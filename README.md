# VPS 定时任务·守护进程·队列与批处理调度实战

> 服务器上真正干活的，往往不是网站，而是那些「定时跑、后台跑、排队跑」的任务。本文系统梳理 cron / systemd timer / supervisor / 队列 worker / 批处理，讲清时区、并发、幂等、重试、日志与监控，附完整可直接使用的配置样例。

## 目录

- [一、四类任务，四种工具](#一四类任务四种工具)
- [二、cron：简单定时的默认选择](#二cron简单定时的默认选择)
- [三、systemd timer：更现代、更可靠的定时](#三systemd-timer更现代更可靠的定时)
- [四、守护进程：supervisor 与 systemd service](#四守护进程supervisor-与-systemd-service)
- [五、队列与 worker：把任务排队慢慢做](#五队列与-worker把任务排队慢慢做)
- [六、批处理：一把梭与分而治之](#六批处理一把梭与分而治之)
- [七、并发控制与锁](#七并发控制与锁)
- [八、日志、告警与可观测](#八日志告警与可观测)
- [九、健壮性：幂等·重试·死信](#九健壮性幂等重试死信)
- [十、常见故障与排查](#十常见故障与排查)
- [十一、FAQ](#十一faq)
- [十二、相关资源](#十二相关资源)

---

## 一、四类任务，四种工具

先把问题分类，再选工具，别拿 cron 硬扛一切。

| 任务类型 | 特征 | 推荐工具 |
|----------|------|----------|
| 简单定时 | 每天/每小时跑一次脚本 | cron、systemd timer |
| 长驻服务 | 一直运行，崩溃要重启 | systemd service、supervisor |
| 异步队列 | 生产快、消费慢，需要排队削峰 | Redis/RabbitMQ + worker |
| 一次性批处理 | 大量数据分片处理 | xargs/GNU parallel + 脚本 |

**选择原则**：能在 systemd 里表达就别用 supervisor；需要队列语义（重试、优先级、可视化管理）就别用文件轮询硬凑。

> 这些任务大多需要一个**长期在线、线路稳定**的机器，半夜掉线毁掉的不只是任务，还有数据一致性。选机器时把在线率与线路放在第一位——这也是为什么很多开发者选择 [VPSVIP](https://vpsvip.net) 这类优化线路的 VPS 作为调度中枢。

---

## 二、cron：简单定时的默认选择

### 2.1 语法速查

```
* * * * *  command
│ │ │ │ │
│ │ │ │ └── 星期 (0-7, 0和7都是周日)
│ │ │ └──── 月   (1-12)
│ │ └────── 日   (1-31)
│ └──────── 小时 (0-23)
└────────── 分钟 (0-59)
```

| 表达式 | 含义 |
|--------|------|
| `0 3 * * *` | 每天 03:00 |
| `*/15 * * * *` | 每 15 分钟 |
| `0 9 * * 1-5` | 工作日 09:00 |
| `0 0 1 * *` | 每月 1 号 0 点 |
| `30 4 1,15 * *` | 每月 1、15 号 04:30 |

### 2.2 用 `crontab -e` 而不是直接改 `/etc/crontab`

```bash
crontab -e                 # 编辑当前用户
crontab -l                 # 查看
crontab -u www -e          # 指定用户（root）
```

### 2.3 三个必踩的坑

**坑 1：环境变量不完整。** cron 的 PATH 极简，脚本里用的命令常找不到。

```bash
# 在 crontab 顶部定义
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
MAILTO=""
```

**坑 2：时区。** 服务器是 UTC，你的「凌晨 3 点」就成了北京时间 11 点。要么改系统时区，要么在脚本里 `TZ=Asia/Shanghai`。

```bash
sudo timedatectl set-timezone Asia/Shanghai
```

**坑 3：输出被吞。** 默认会给 root 发邮件（通常没配），错误就这么消失了。正确做法是显式重定向：

```cron
0 3 * * * /opt/scripts/backup.sh >> /var/log/backup.log 2>&1
```

### 2.4 cron 不适合什么

- 需要「错过就补跑」（机器关机期间错过的任务不会补）。
- 需要精确到秒。
- 需要依赖关系（A 成功后才跑 B）。
- 需要随机抖动。以上都交给 systemd timer。

---

## 三、systemd timer：更现代、更可靠的定时

### 3.1 一个最小示例

`/etc/systemd/system/backup.service`：

```ini
[Unit]
Description=Nightly backup
After=network-online.target

[Service]
Type=oneshot
User=root
WorkingDirectory=/opt/app
ExecStart=/opt/scripts/backup.sh
```

`/etc/systemd/system/backup.timer`：

```ini
[Unit]
Description=Run backup daily at 03:00

[Timer]
OnCalendar=*-*-* 03:00:00
Persistent=true
RandomizedDelaySec=300
Unit=backup.service

[Install]
WantedBy=timers.target
```

```bash
systemctl daemon-reload
systemctl enable --now backup.timer
systemctl list-timers --all
```

### 3.2 相比 cron 的优势

| 能力 | cron | systemd timer |
|------|------|---------------|
| 错过补跑 | ❌ | ✅ `Persistent=true` |
| 精确到秒 | ❌ | ✅ |
| 随机抖动 | ❌ | ✅ `RandomizedDelaySec` |
| 依赖其他服务 | ❌ | ✅ `After=`/`Requires=` |
| 资源限制 | ❌ | ✅ `MemoryMax`/`CPUQuota` |
| 日志 | 需自己重定向 | ✅ 自动进 journald |

### 3.3 常用日历写法

```
OnCalendar=daily                       # 每天 00:00
OnCalendar=Mon..Fri 09:00              # 工作日 9 点
OnCalendar=*-*-* 02:00,14:00           # 每天两次
OnCalendar=*-*-1 04:00                 # 每月 1 号
OnCalendar=*-*-* *:0/10                # 每 10 分钟
```

验证写法是否正确：

```bash
systemd-analyze calendar "*-*-* 03:00:00"
```

---

## 四、守护进程：supervisor 与 systemd service

### 4.1 优先用 systemd service

```ini
# /etc/systemd/system/worker.service
[Unit]
Description=Queue worker
After=network.target redis.service

[Service]
Type=simple
User=app
WorkingDirectory=/opt/app
ExecStart=/opt/app/venv/bin/python worker.py
Restart=always
RestartSec=5
StartLimitIntervalSec=60
StartLimitBurst=5
MemoryMax=1G
Environment=TZ=Asia/Shanghai
StandardOutput=append:/var/log/worker.log
StandardError=append:/var/log/worker.err.log

[Install]
WantedBy=multi-user.target
```

```bash
systemctl enable --now worker
systemctl status worker
journalctl -u worker -f
```

`Restart=always` + `RestartSec` 就是最朴素的「自愈」。**注意加 `StartLimitBurst` 限制**，否则脚本一直崩溃会疯狂重启。

### 4.2 supervisor：多进程批量管理更顺手

当你有几十个进程、需要 Web 界面、需要按组启停时，supervisor 更省事。

```ini
; /etc/supervisor/conf.d/app.conf
[program:app]
command=/opt/app/venv/bin/python app.py
directory=/opt/app
user=app
autostart=true
autorestart=true
startretries=5
stopsignal=TERM
stopwaitsecs=30
stdout_logfile=/var/log/app.out.log
stderr_logfile=/var/log/app.err.log
stdout_logfile_maxbytes=50MB
stdout_logfile_backups=5
environment=TZ="Asia/Shanghai"

[group:workers]
programs=worker1,worker2,worker3
priority=999
```

```bash
supervisorctl reread
supervisorctl update
supervisorctl status
supervisorctl restart workers:*
```

### 4.3 两者对比

| 维度 | systemd | supervisor |
|------|---------|------------|
| 系统集成 | 原生、开机即起 | 需自己装、依赖 Python |
| Web 界面 | 无（用 cockpit） | 自带 |
| 多进程/分组 | 靠 target/template | 天然支持 group |
| 资源限制 | 强 | 弱 |

**结论**：系统服务用 systemd，应用进程组用 supervisor，不必纠结。

---

## 五、队列与 worker：把任务排队慢慢做

### 5.1 为什么需要队列

同步处理的问题：请求变慢、超时、失败即丢。队列把「接收」与「处理」解耦：

```
Web 请求 → 入队(Redis/RabbitMQ) → [ worker ]
                                    ↓
                                 结果落库 + 通知
```

好处：削峰、可重试、可横向加 worker、可优先级。

### 5.2 最小可用队列（Redis List）

```python
# producer.py
import redis, json
r = redis.Redis(host="127.0.0.1", port=6379)
r.lpush("jobs", json.dumps({"id": "job-1", "type": "resize", "file": "a.jpg"}))
```

```python
# worker.py
import redis, json, time
r = redis.Redis(host="127.0.0.1", port=6379)
while True:
    item = r.brpop("jobs", timeout=5)   # 阻塞式取，省 CPU
    if not item:
        continue
    _, raw = item
    job = json.loads(raw)
    try:
        handle(job)
    except Exception as e:
        r.lpush("dead", json.dumps({"job": job, "err": str(e)}))
```

**要点**：`brpop` 是阻塞取，避免 `while True` 空转烧 CPU；失败进「死信队列」而非直接丢。

### 5.3 成熟方案

| 方案 | 语言生态 | 适用 |
|------|----------|------|
| Celery | Python | 功能全，生态大 |
| RQ | Python | 简单，基于 Redis |
| BullMQ | Node.js | Redis 队列，成熟 |
| Sidekiq | Ruby | Rails 标配 |
| RabbitMQ | 通用 | 需要路由/确认语义 |
| NATS JetStream | 通用 | 轻量高性能 |

队列框架都内置了重试、延迟任务、定时任务（Celery Beat）、优先级，别自己造轮子。

### 5.4 worker 的部署

worker 就是长期运行的服务，用 systemd 管理：

```bash
sudo systemctl enable --now worker@1 worker@2
```

用 systemd template 起多个实例，或直接在 supervisor 里开 `numprocs=4`。

---

## 六、批处理：一把梭与分而治之

### 6.1 串行一把梭（数据量小）

```bash
for f in *.csv; do
  ./process.sh "$f"
done
```

### 6.2 并行分片（GNU parallel）

```bash
# 用 8 个进程并行处理
ls *.csv | parallel -j 8 ./process.sh {}

# 带进度、按行
parallel -j 4 --bar --eta ./process.sh {} ::: file1 file2 file3
```

### 6.3 xargs 版

```bash
find /data -name '*.log' -print0 | xargs -0 -n1 -P4 ./parse.sh
```

`-P4` 控制并发，`-print0/-0` 处理带空格文件名。

### 6.4 大文件按行切分

```bash
split -l 100000 big.csv part_
for p in part_*; do ./process.sh "$p" & done
wait
```

### 6.5 批处理的三条军规

1. **可分片**：任务要能独立处理一块数据，避免全局锁。
2. **可续跑**：记录处理进度（offset/checkpoint），失败后从断点继续。
3. **可观测**：每个分片的结果与耗时写日志，便于定位慢分片。

---

## 七、并发控制与锁

定时任务最经典的事故：**上一次还没跑完，下一次又启动了**，两份备份互相踩。

### 7.1 flock 文件锁（最简单）

```bash
#!/bin/bash
exec 9>/var/lock/backup.lock
flock -n 9 || { echo "already running"; exit 0; }
# 业务逻辑…
```

或者一行：

```bash
flock -n /var/lock/backup.lock /opt/scripts/backup.sh
```

### 7.2 用 flock + crontab

```cron
*/5 * * * * flock -n /var/lock/sync.lock /opt/scripts/sync.sh >> /var/log/sync.log 2>&1
```

### 7.3 分布式锁（多机）

```bash
# 用 Redis SET NX PX 做带过期的锁
redis-cli SET lock:job1 $(hostname) NX PX 60000
```

拿到锁才执行，执行完 `DEL`。过期时间防止死锁。

### 7.4 systemd timer 自带的并发保护

对同一 service，systemd 默认**不会同时启动两个实例**；再加 `RefuseManualStart` 等可进一步约束。

---

## 八、日志、告警与可观测

### 8.1 日志三件套

- **输出**：统一写 stdout/stderr，交给 journald 或 logrotate 管理的文件。
- **轮转**：文件日志必须配 logrotate，否则撑爆磁盘。

```conf
# /etc/logrotate.d/app
/var/log/app/*.log {
    daily
    rotate 7
    compress
    delaycompress
    missingok
    notifempty
    copytruncate
}
```

- **检索**：`journalctl -u worker --since "1 hour ago"`。

### 8.2 告警：任务失败要能喊出来

不要指望自己每天去看日志。最小可用做法：脚本失败时调用 webhook。

```bash
notify_fail() {
  curl -s -X POST "$WEBHOOK_URL" \
    -H 'Content-Type: application/json' \
    -d "{\"text\":\"✅❌ 任务 $1 失败: $2\"}"
}
trap 'notify_fail "$0" "$?"' ERR
```

### 8.3 关键监控指标

| 指标 | 含义 | 异常信号 |
|------|------|----------|
| 上次成功时间 | 任务健康度 | 超过周期 2 倍=异常 |
| 执行时长 | 性能趋势 | 突然变长=数据或依赖变慢 |
| 失败次数 | 稳定性 | 连续失败=外部接口变更 |
| 队列深度 | 堆积 | 持续增长=worker 不够 |
| 磁盘使用 | 日志/数据 | 快速上升=日志没轮转 |

> 最简单的「心跳告警」：每次成功都 `touch /var/lib/last_ok`，再用一个独立任务检查该文件是否过期——防止「任务根本没启动」这种静默失败（cron 被注释、timer 没 enable）。

---

## 九、健壮性：幂等·重试·死信

### 9.1 幂等

同一个任务执行两次，结果应当一致：

- 写库用 `INSERT ... ON CONFLICT DO UPDATE`（upsert）。
- 生成文件先写临时名再 `mv`（原子替换）。
- 用业务唯一键去重（如 `job_id`）。

### 9.2 重试与退避

```
尝试 1 → 失败 → 等 2s
尝试 2 → 失败 → 等 4s
尝试 3 → 失败 → 等 8s
→ 进死信队列 + 告警
```

指数退避避免「失败了还疯狂重试把下游打死」。

### 9.3 死信队列

失败任务不要直接丢，存起来供人工排查与补偿重放：

```bash
# 简单做法：追加到文件，便于事后重放
echo "$(date -Is) $job_json" >> /var/log/dead_letters.log
```

---

## 十、常见故障与排查

| 现象 | 可能原因 | 排查 |
|------|----------|------|
| cron 任务不执行 | PATH 缺失 / 时区 / 权限 | `grep CRON /var/log/syslog` |
| systemd 服务起不来 | 单元语法 / 权限 / WorkingDirectory | `journalctl -u x -n 100` |
| 任务重复执行 | 无锁 / timer 与 cron 并存 | 加 flock，检查是否两处都配了 |
| 内存被打满 OOM | 并发过多 / 内存泄漏 | `dmesg | grep -i oom`，加 `MemoryMax` |
| 磁盘写满 | 日志没轮转 | `df -h`、`df -i`、`journalctl --disk-usage` |
| 定时不准时 | 时区 / 服务器负载 | `timedatectl`、`uptime` |

---

## 十一、FAQ

**Q1：cron 和 systemd timer 到底选哪个？**
A：新项目一律 timer；只有极简单、已在用 cron 的场景保留 cron。timer 的补跑与日志能力值回票价。

**Q2：任务跑到一半机器重启了怎么办？**
A：靠「进度检查点」续跑，而不是靠重头再来。批处理务必记录 checkpoint。

**Q3：多久任务的日志该怎么留？**
A：journald 默认可能只留几十 MB，容易丢。重要任务显式写文件 + logrotate 保留 7~30 天。

**Q4：队列积压了怎么办？**
A：先加 worker（横向），再看单任务是否变慢（纵向瓶颈），最后考虑拆流（按类型分队列）。别一上来就优化代码。

**Q5：怎么防止定时任务把 CPU 打满影响主服务？**
A：用 systemd 的 `CPUQuota=`、`IOWeight=`、`Nice=` 限定资源；把批处理安排在业务低谷。

**Q6：多台服务器怎么避免定时任务重复跑？**
A：加分布式锁（Redis/etcd），或指定一台「调度机」统一下发（用 Ansible/`ssh` 分发）。

**Q7：如何优雅地停止一个 worker？**
A：捕获 `SIGTERM`，处理完当前任务再退出；systemd/supervisor 用 `stopwaitsecs`/`TimeoutStopSec` 给它收尾时间，避免任务半途而废。

**Q8：任务需要跨时区按各地时间跑怎么办？**
A：在执行时按目标地域计算时间（如用 `TZ=America/New_York date`），或用支持时区的调度器（Celery beat 支持按 `crontab` + `timezone`）。

---

## 十二、相关资源

- [VPSVIP 官网](https://vpsvip.net) —— 稳定优化线路 VPS，适合长期在线跑定时/队列任务的调度中枢
- [ClashVIP](https://clashvip.net) —— 网络与节点资源
- [nav.clashvip.net](https://nav.clashvip.net) —— 导航与工具集合
- [clashhub.net](https://clashhub.net) —— 教程与文档
- [bbs.clashhub.net](https://bbs.clashhub.net) —— 社区讨论
- [clash-for-windows.net](https://clash-for-windows.net) —— 客户端下载
- [systemd.timer 文档](https://www.freedesktop.org/software/systemd/man/systemd.timer.html)
- [GNU parallel](https://www.gnu.org/software/parallel/)
- [Supervisor 文档](http://supervisord.org/)
- [Celery 文档](https://docs.celeryq.dev/)

---

## 免责声明

1. 本仓库内容仅供技术学习与参考；
2. 请遵守所在国家/地区法律法规以及各平台的使用条款；
3. 修改调度器与服务前请先备份，并在测试环境验证；
4. 请妥善保管密钥与备份，定期检查任务是否按预期执行。

## 许可证

MIT License

---
更新时间：2026-09-22
