# VPS 缃戠珯鎬ц兘璇婃柇涓?Core Web Vitals 鍏ㄩ潰浼樺寲瀹炴垬

**鍒嗙被**锛歏PS 鎬ц兘宸ョ▼ | **鏇存柊鏃ユ湡**锛?026-09-24 | **缁存姢浜?*锛歝lashforwindows-net

---

## 馃摉 鐩綍

- [涓€銆丆ore Web Vitals 鏍稿績鎸囨爣瑙ｈ](#涓€core-web-vitals-鏍稿績鎸囨爣瑙ｈ)
- [浜屻€佹€ц兘鐩戞帶浣撶郴鎼缓](#浜屾€ц兘鐩戞帶浣撶郴鎼缓)
- [涓夈€丩CP 浼樺寲瀹炴垬锛堟渶澶у唴瀹圭粯鍒讹級](#涓塴cp-浼樺寲瀹炴垬鏈€澶у唴瀹圭粯鍒?
- [鍥涖€丆LS 浼樺寲瀹炴垬锛堢疮绉竷灞€鍋忕Щ锛塢(#鍥沜ls-浼樺寲瀹炴垬绱Н甯冨眬鍋忕Щ)
- [浜斻€丗ID/INP 浼樺寲瀹炴垬锛堜氦浜掑欢杩燂級](#浜攆idinp-浼樺寲瀹炴垬浜や簰寤惰繜)
- [鍏€乀TFB 涓?DNS/TCP 浼樺寲](#鍏璽tfb-涓?dnstcp-浼樺寲)
- [涓冦€丣avaScript 鎬ц兘浼樺寲](#涓僯avascript-鎬ц兘浼樺寲)
- [鍏€丆SS 娓叉煋浼樺寲](#鍏玞ss-娓叉煋浼樺寲)
- [涔濄€佸浘鐗囦笌濯掍綋浼樺寲](#涔濆浘鐗囦笌濯掍綋浼樺寲)
- [鍗併€佽嚜鍔ㄥ寲鎬ц兘娴嬭瘯涓庢寔缁泦鎴怾(#鍗佽嚜鍔ㄥ寲鎬ц兘娴嬭瘯涓庢寔缁泦鎴?
- [鍗佷竴銆佺敓浜х幆澧冩€ц兘闂鎺掓煡鎵嬪唽](#鍗佷竴鐢熶骇鐜鎬ц兘闂鎺掓煡鎵嬪唽)

---

## 涓€銆丆ore Web Vitals 鏍稿績鎸囨爣瑙ｈ

### 1.1 Google Web Vitals 涓夊ぇ鎸囨爣

Core Web Vitals 鏄?Google 鐢ㄤ簬琛￠噺鐢ㄦ埛浣撻獙鐨勬牳蹇冩寚鏍囷紝鐩存帴褰卞搷鎼滅储鎺掑悕锛?
| 鎸囨爣 | 鍏ㄧО | 鍚箟 | 杈炬爣闃堝€?| 浼樼闃堝€?|
|------|------|------|---------|---------|
| **LCP** | Largest Contentful Paint | 鏈€澶у唴瀹圭粯鍒舵椂闂?| 鈮?2.5s | 鈮?1.2s |
| **INP** | Interaction to Next Paint | 涓嬩竴甯т氦浜掑欢杩燂紙鏇夸唬 FID锛?| 鈮?200ms | 鈮?100ms |
| **CLS** | Cumulative Layout Shift | 绱Н甯冨眬鍋忕Щ閲?| 鈮?0.1 | 鈮?0.05 |

### 1.2 鍚勬寚鏍囨繁搴﹁В鏋?
**LCP锛堟渶澶у唴瀹圭粯鍒讹級**锛?- 琛￠噺椤甸潰涓昏鍐呭鍔犺浇閫熷害
- 閫氬父鏄?hero 鍥剧墖銆侀灞忔枃瀛楁垨瑙嗛棣栧抚
- 鍏抽敭鏃堕棿鐐癸細鐢ㄦ埛鍙戣捣璇锋眰 鈫?LCP 鍏冪礌娓叉煋瀹屾垚
- 甯歌 LCP 鍏冪礌锛歚<img>`銆乣<video>`锛堝皝闈㈠浘锛夈€侀€氳繃 `url()` 鍔犺浇鐨?CSS 鑳屾櫙鍥俱€佸潡绾ф枃鏈厓绱?
**INP锛堜氦浜掑欢杩燂級**锛?- 娴嬮噺浠庣敤鎴蜂氦浜掞紙鐐瑰嚮/杈撳叆锛夊埌涓嬩竴甯ф覆鏌撶殑鏃堕棿
- 閲囨牱鎵€鏈変氦浜掍簨浠讹紝鍙栨渶闀跨殑涓€娆★紙P98锛?- INP > 200ms 鏃剁敤鎴蜂細鎰熺煡鍒版槑鏄惧崱椤?
**CLS锛堝竷灞€鍋忕Щ锛?*锛?- 琛￠噺瑙嗚绋冲畾鎬э紝鍒嗘暟瓒婇珮瓒婁笉绋冲畾
- 鍙戠敓鍦ㄥ彲瑙佸厓绱犱綅缃剰澶栫Щ鍔ㄦ椂
- 鍏稿瀷鍦烘櫙锛氬浘鐗囧姞杞芥椂鏃犲昂瀵搞€佸姩鎬佹敞鍏ュ箍鍛娿€佹棤棰勫姞杞藉瓧浣?
### 1.3 鎬ц兘棰勭畻鍙傝€?
| 璧勬簮绫诲瀷 | 鎬ц兘棰勭畻 | 璇存槑 |
|---------|---------|------|
| HTML | < 15 KB | 棣栧睆 HTML 鍘嬬缉鍚庡ぇ灏?|
| CSS | < 10 KB | 鍏抽敭 CSS锛堝唴鑱旓級+ 闈炲叧閿?CSS 寤惰繜鍔犺浇 |
| JavaScript | < 50 KB | 棣栧睆 JS 鎬诲ぇ灏忥紙鍘嬬缉鍚庯級 |
| 鍥剧墖 | < 100 KB/寮?| 棣栧睆 LCP 鍥剧墖 |
| TTFB | < 200ms | Time to First Byte |
| TTI | < 3.5s | 鍙氦浜掓椂闂达紙4G 缃戠粶锛?|

---

## 浜屻€佹€ц兘鐩戞帶浣撶郴鎼缓

### 2.1 鐪熷疄鐢ㄦ埛鐩戞帶锛圧UM锛夐儴缃?
```javascript
// web-vitals-rum.js - 閲囬泦鐪熷疄鐢ㄦ埛 Core Web Vitals 鏁版嵁
// 閮ㄧ讲鍦ㄧ綉绔?footer 鎴栦綔涓虹嫭绔嬭剼鏈姞杞?
(function() {
    'use strict';

    const ANALYTICS_ENDPOINT = 'https://analytics.example.com/vitals';
    const REPORTING_THRESHOLD = 0.1; // 浠呬笂鎶ュ亸绂荤洰鏍囩殑鎸囨爣

    // Web Vitals 搴擄紙Google 瀹樻柟锛?    var script = document.createElement('script');
    script.src = 'https://unpkg.com/web-vitals@4.0.0/dist/web-vitals.attribution.iife.js';
    script.onload = function() {
        // 纭繚鑴氭湰鍔犺浇瀹屾垚鍚庡啀閲囬泦
        if (window.webVitals) {
            initWebVitals();
        }
    };
    document.head.appendChild(script);

    function initWebVitals() {
        // LCP 閲囬泦
        onLCP(function(metric) {
            sendToAnalytics('LCP', metric);
            console.debug('[WebVitals] LCP:', metric.value, 'ms');
        });

        // INP 閲囬泦
        onINP(function(metric) {
            sendToAnalytics('INP', metric);
            console.debug('[WebVitals] INP:', metric.value, 'ms');
        });

        // CLS 閲囬泦
        onCLS(function(metric) {
            sendToAnalytics('CLS', metric);
            console.debug('[WebVitals] CLS:', metric.value);
        });

        // TTFB 閲囬泦
        onTTFB(function(metric) {
            sendToAnalytics('TTFB', metric);
            console.debug('[WebVitals] TTFB:', metric.value, 'ms');
        });

        // FCP 閲囬泦
        onFCP(function(metric) {
            sendToAnalytics('FCP', metric);
            console.debug('[WebVitals] FCP:', metric.value, 'ms');
        });
    }

    function sendToAnalytics(name, metric) {
        // 杩囨护寮傚父鍊硷紙鍙兘鏄祴璇?鏈哄櫒浜猴級
        if (metric.value === 0) return;

        var payload = {
            name: name,
            value: metric.value,
            rating: metric.rating, // 'good' | 'needs-improvement' | 'poor'
            delta: metric.delta,
            id: metric.id,
            entries: metric.entries ? metric.entries.length : 0,
            navigationType: metric.navigationType || 'navigate',
            url: window.location.href,
            userAgent: navigator.userAgent,
            connectionType: navigator.connection?.effectiveType || 'unknown',
            deviceMemory: navigator.deviceMemory || 'unknown',
            timestamp: Date.now(),
            viewport: {
                width: window.innerWidth,
                height: window.innerHeight
            },
            // 褰掑洜鏁版嵁锛堢敤浜庤皟璇曪級
            attribution: metric.attribution ? {
                element: metric.attribution.element?.tagName || 'unknown',
                url: metric.attribution.url || '',
                timeToFirstByte: metric.attribution.timeToFirstByte || 0,
                resourceLoadDelay: metric.attribution.resourceLoadDelay || 0,
                resourceLoadDuration: metric.attribution.resourceLoadDuration || 0,
                elementRenderDelay: metric.attribution.elementRenderDelay || 0
            } : null
        };

        // 鎵归噺涓婃姤锛堝噺灏戣姹傛暟锛?        batchSend(payload);
    }

    // 鎵归噺鍙戦€佺紦鍐插尯
    var sendBuffer = [];
    var flushTimer = null;

    function batchSend(payload) {
        sendBuffer.push(payload);

        // 绔嬪嵆鍙戦€侊紙杈惧埌闃堝€兼椂锛?        if (sendBuffer.length >= 5) {
            flushBuffer();
            return;
        }

        // 瀹氭椂鍙戦€?        if (!flushTimer) {
            flushTimer = setTimeout(flushBuffer, 5000);
        }
    }

    function flushBuffer() {
        if (sendBuffer.length === 0) return;
        clearTimeout(flushTimer);
        flushTimer = null;

        var data = JSON.stringify(sendBuffer);
        sendBuffer = [];

        // 浣跨敤 sendBeacon 纭繚椤甸潰鍗歌浇鏃朵篃鑳藉彂閫?        if (navigator.sendBeacon) {
            navigator.sendBeacon(ANALYTICS_ENDPOINT + '/batch', data);
        } else {
            fetch(ANALYTICS_ENDPOINT + '/batch', {
                method: 'POST',
                body: data,
                keepalive: true,
                headers: { 'Content-Type': 'application/json' }
            }).catch(function() {});
        }
    }
})();
```

### 2.2 鎬ц兘鐩戞帶鍚庣鏈嶅姟

```python
#!/usr/bin/env python3
"""
performance-backend.py - Web Vitals 鏁版嵁鏀堕泦涓庡垎鏋愬悗绔?Flask + SQLite 杞婚噺绾у疄鐜?"""
from flask import Flask, request, jsonify
from datetime import datetime, timedelta
from collections import defaultdict
import sqlite3
import json

app = Flask(__name__)
DB_PATH = '/opt/performance/vitals.db'

def init_db():
    conn = sqlite3.connect(DB_PATH)
    conn.execute('''
        CREATE TABLE IF NOT EXISTS vitals (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT, value REAL, rating TEXT,
            url TEXT, device_memory TEXT,
            connection_type TEXT, viewport_w TEXT,
            user_agent TEXT, timestamp INTEGER
        )
    ''')
    conn.execute('''
        CREATE INDEX IF NOT EXISTS idx_timestamp ON vitals(timestamp)
    ''')
    conn.execute('''
        CREATE INDEX IF NOT EXISTS idx_name ON vitals(name)
    ''')
    conn.commit()
    conn.close()

@app.route('/vitals/batch', methods=['POST'])
def receive_batch():
    """鎺ユ敹鎵归噺 Web Vitals 鏁版嵁"""
    try:
        items = request.get_json()
        if not isinstance(items, list):
            items = [items]

        conn = sqlite3.connect(DB_PATH)
        cur = conn.cursor()

        for item in items:
            cur.execute('''
                INSERT INTO vitals (name, value, rating, url,
                    device_memory, connection_type, viewport_w,
                    user_agent, timestamp)
                VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)
            ''', (
                item.get('name'),
                item.get('value'),
                item.get('rating'),
                item.get('url'),
                item.get('deviceMemory', 'unknown'),
                item.get('connectionType', 'unknown'),
                item.get('viewport', {}).get('width', 0),
                item.get('userAgent', ''),
                item.get('timestamp', 0)
            ))

        conn.commit()
        conn.close()
        return jsonify({'status': 'ok', 'count': len(items)})
    except Exception as e:
        return jsonify({'status': 'error', 'message': str(e)}), 500

@app.route('/vitals/stats', methods=['GET'])
def get_stats():
    """鑾峰彇鎬ц兘缁熻"""
    metric = request.args.get('metric', 'LCP')
    hours = int(request.args.get('hours', 24))

    since = int((datetime.now() - timedelta(hours=hours)).timestamp() * 1000)

    conn = sqlite3.connect(DB_PATH)
    cur = conn.cursor()
    cur.execute('''
        SELECT
            COUNT(*) as count,
            AVG(value) as avg_value,
            MIN(value) as min_value,
            MAX(value) as max_value,
            AVG(CASE WHEN rating='good' THEN 1 ELSE 0 END) * 100 as good_pct,
            AVG(CASE WHEN rating='needs-improvement' THEN 1 ELSE 0 END) * 100 as needs_pct,
            AVG(CASE WHEN rating='poor' THEN 1 ELSE 0 END) * 100 as poor_pct
        FROM vitals
        WHERE name=? AND timestamp>?
    ''', (metric, since))

    row = cur.fetchone()
    conn.close()

    if not row or row[0] == 0:
        return jsonify({'error': 'no data'}), 404

    return jsonify({
        'metric': metric,
        'period_hours': hours,
        'sample_count': row[0],
        'avg_value': round(row[1], 2),
        'min_value': round(row[2], 2),
        'max_value': round(row[3], 2),
        'good_pct': round(row[4], 1),
        'needs_improvement_pct': round(row[5], 1),
        'poor_pct': round(row[6], 1),
        'good_threshold': {'LCP': 2500, 'INP': 200, 'CLS': 0.1, 'TTFB': 200, 'FCP': 1800}.get(metric, 0)
    })

if __name__ == '__main__':
    init_db()
    app.run(host='0.0.0.0', port=5000)
```

### 2.3 Prometheus 鎸囨爣鏆撮湶绔偣

```python
"""
prometheus-exporter.py - 灏?Web Vitals 鏁版嵁鏆撮湶涓?Prometheus 鏍煎紡
"""
from flask import Response

@app.route('/metrics')
def metrics():
    """Prometheus 鎶撳彇绔偣"""
    conn = sqlite3.connect(DB_PATH)
    cur = conn.cursor()

    since_1h = int((datetime.now() - timedelta(hours=1)).timestamp() * 1000)
    since_24h = int((datetime.now() - timedelta(hours=24)).timestamp() * 1000)

    output = ['# HELP webvitals_samples_total Total Web Vitals samples',
              '# TYPE webvitals_samples_total counter']

    for metric in ['LCP', 'INP', 'CLS', 'TTFB', 'FCP']:
        for period, since in [('1h', since_1h), ('24h', since_24h)]:
            cur.execute('SELECT COUNT(*) FROM vitals WHERE name=? AND timestamp>?',
                       (metric, since))
            count = cur.fetchone()[0]

            cur.execute('SELECT AVG(value) FROM vitals WHERE name=? AND timestamp>?',
                       (metric, since))
            avg = cur.fetchone()[0] or 0

            cur.execute('''SELECT AVG(CASE WHEN rating='good' THEN 1 ELSE 0 END) * 100
                          FROM vitals WHERE name=? AND timestamp>?''',
                       (metric, since))
            good_pct = cur.fetchone()[0] or 0

            output.append(f'webvitals_samples_total{{metric="{metric}",period="{period}"}} {count}')
            output.append(f'webvitals_avg_value{{metric="{metric}",period="{period}"}} {avg:.2f}')
            output.append(f'webvitals_good_pct{{metric="{metric}",period="{period}"}} {good_pct:.2f}')

    conn.close()
    return Response('\n'.join(output), mimetype='text/plain')
```

---

## 涓夈€丩CP 浼樺寲瀹炴垬锛堟渶澶у唴瀹圭粯鍒讹級

### 3.1 LCP 鏃堕棿绾垮垎鏋愭鏋?
```
LCP 鎬绘椂闂?= TTFB + 璧勬簮鑾峰彇寤惰繜 + 璧勬簮鑾峰彇鏃堕棿 + 鍏冪礌娓叉煋寤惰繜
           鈫?         鈫?              鈫?             鈫?        鏈嶅姟鍣ㄥ搷搴?  娴忚鍣ㄥ鐞嗗搷搴?  涓嬭浇鍥剧墖/瀛椾綋   GPU 娓叉煋

鍏抽敭浼樺寲鐐癸細
1. TTFB锛欳DN 缂撳瓨銆丯ginx 缂撳瓨銆佹暟鎹簱鏌ヨ浼樺寲
2. 璧勬簮鑾峰彇寤惰繜锛欴NS 棰勮В鏋愩€乀CP 棰勮繛鎺ャ€丠TTP/2 Server Push
3. 璧勬簮鑾峰彇鏃堕棿锛氬浘鐗囧帇缂┿€乄ebP/AVIF銆丆DN 鍒嗗彂
4. 鍏冪礌娓叉煋寤惰繜锛氭湇鍔″櫒绔覆鏌撱€佸叧閿祫婧愪紭鍏堢骇
```

### 3.2 棰勫姞杞?LCP 鍥剧墖

```html
<!-- 鍦?<head> 涓鍔犺浇 LCP 鍥剧墖 -->
<head>
    <!-- 棰勮繛鎺ュ叧閿煙鍚?-->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

    <!-- 棰勫姞杞?LCP 鍥剧墖锛堟渶閲嶈锛佹牴鎹疄闄?LCP 鍏冪礌 URL 淇敼锛?-->
    <link rel="preload" as="image"
          href="/images/hero.webp"
          imagesrcset="/images/hero-480.webp 480w, /images/hero-960.webp 960w, /images/hero-1440.webp 1440w"
          imagesizes="100vw"
          fetchpriority="high">

    <!-- 濡傛灉 LCP 鏄枃瀛楋紝浼樺厛绾ф洿浣?-->
    <link rel="preload" as="font" href="/fonts/hero-font.woff2" crossorigin>

    <!-- 棰勫姞杞藉叧閿?CSS -->
    <link rel="preload" href="/css/critical.css" as="style">
    <link rel="stylesheet" href="/css/critical.css" media="print" onload="this.media='all'">

    <!-- 鍏抽敭 JS 棰勫姞杞?-->
    <link rel="modulepreload" href="/js/app.js">
</head>
```

### 3.3 鍥剧墖 LCP 浼樺寲瀹屾暣鏂规

```html
<!-- 鏈€浣?LCP 鍥剧墖瀹炶返锛氬悓鏃舵敮鎸佸绉嶆牸寮忓拰灏哄 -->
<picture>
    <!-- AVIF锛堟渶楂樺帇缂╃巼锛岀幇浠ｆ祻瑙堝櫒锛?-->
    <source
        type="image/avif"
        srcset="/images/hero-480.avif 480w,
                /images/hero-960.avif 960w,
                /images/hero-1440.avif 1440w"
        sizes="(max-width: 600px) 480px,
               (max-width: 1200px) 960px,
               100vw">

    <!-- WebP锛堥€氱敤鐜颁唬鏍煎紡锛?-->
    <source
        type="image/webp"
        srcset="/images/hero-480.webp 480w,
                /images/hero-960.webp 960w,
                /images/hero-1440.webp 1440w"
        sizes="(max-width: 600px) 480px,
               (max-width: 1200px) 960px,
               100vw">

    <!-- JPEG锛堥檷绾у吋瀹癸級 -->
    <img
        src="/images/hero-960.jpg"
        srcset="/images/hero-480.jpg 480w,
                /images/hero-960.jpg 960w,
                /images/hero-1440.jpg 1440w"
        sizes="(max-width: 600px) 480px,
               (max-width: 1200px) 960px,
               100vw"
        alt="Hero image with optimized formats"
        width="1440"
        height="810"
        loading="eager"
        fetchpriority="high"
        decoding="async">
</picture>
```

---

## 鍥涖€丆LS 浼樺寲瀹炴垬锛堢疮绉竷灞€鍋忕Щ锛?
### 4.1 甯冨眬鍋忕Щ鐨勪簲澶ф牴婧?
| 鏍规簮 | 鐥囩姸 | 瑙ｅ喅鏂规 |
|------|------|---------|
| **鏃犲昂瀵稿浘鐗?* | 鍥剧墖鍔犺浇鍚庝笅鏂瑰唴瀹硅鎺ㄤ笅 | 鍥哄畾 `width`/`height` 鎴?`aspect-ratio` |
| **鍔ㄦ€佹敞鍏ュ唴瀹?* | 骞垮憡/Banner 绐佺劧鎻掑叆 | 棰勭暀鍥哄畾绌洪棿 |
| **瀛椾綋鍔犺浇闂儊锛團OIT/FOUT锛?* | 瀛椾綋鍒囨崲瀵艰嚧鏂囧瓧澶у皬鍙樺寲 | `font-display: optional` + 瀛椾綋棰勫姞杞?|
| **鏃犲昂瀵歌棰?iframe** | 宓屽叆鍐呭瀵艰嚧甯冨眬鎶栧姩 | 璁剧疆鍥哄畾瀹介珮姣?|
| **CSS 鍔ㄧ敾浣嶇疆鍙樺寲** | 鍔ㄧ敾瀵艰嚧鍏冪礌绉诲姩 | 浣跨敤 `transform` 鑰岄潪 `top/left` |

### 4.2 闃叉甯冨眬鍋忕Щ鐨?HTML 鏈€浣冲疄璺?
```html
<!-- 鍥剧墖蹇呴』璁剧疆瀹介珮锛堟帹鑽?aspect-ratio 鐜颁唬鏂规锛?-->
<style>
    /* 鐜颁唬瀹介珮姣旀柟妗?*/
    .hero-image {
        aspect-ratio: 16 / 9;
        width: 100%;
        max-width: 1440px;
        /* 鍗犱綅鑳屾櫙鑹诧紝闃叉绌虹櫧闂儊 */
        background-color: #f0f0f0;
    }

    /* 鏃х増鍏煎鏂规锛坧adding-bottom hack锛?*/
    .video-container {
        position: relative;
        width: 100%;
        padding-bottom: 56.25%; /* 16:9 */
        height: 0;
        overflow: hidden;
    }

    .video-container iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

    /* 骞垮憡浣嶅繀椤婚鐣欑┖闂?*/
    .ad-slot {
        min-height: 250px; /* 鏈€灏忛珮搴﹂槻姝㈢獊鐒跺嚭鐜?*/
        contain: layout;
    }

    /* 瀛椾綋鍔犺浇闃叉姈鍔?*/
    @font-face {
        font-family: 'Inter';
        src: url('/fonts/Inter.woff2') format('woff2');
        font-display: optional; /* 棣栭€夌郴缁熷瓧浣擄紝瀹屽叏涓嶆姈鍔?*/
        /* 椋庨櫓鏈€浣庯紝浣嗗彲鑳芥棤娉曚娇鐢ㄨ嚜瀹氫箟瀛椾綋 */
    }

    /* 鎶樹腑鏂规锛氬瓧浣撳垏鎹㈡椂缂╁皬杩囨浮 */
    @font-face {
        font-family: 'Inter';
        src: url('/fonts/Inter.woff2') format('woff2');
        font-display: swap;
        size-adjust: 103%; /* 璋冩暣澶у皬浣垮叾鎺ヨ繎绯荤粺瀛椾綋 */
        ascent-override: 90%;
        descent-override: 25%;
    }
</style>

<!-- 鍥剧墖蹇呴』璁剧疆瀹介珮 -->
<img src="/images/logo.png" alt="Logo" width="200" height="50" style="aspect-ratio: 200/50;">

<!-- 鍔ㄦ€佸唴瀹逛娇鐢ㄩ鏋跺睆 -->
<div class="skeleton" aria-hidden="true">
    <div class="skeleton-image"></div>
    <div class="skeleton-title"></div>
    <div class="skeleton-text"></div>
</div>

<style>
    .skeleton { opacity: 0.7; }
    .skeleton-image {
        width: 100%;
        aspect-ratio: 16/9;
        background: linear-gradient(90deg, #eee 25%, #ddd 50%, #eee 75%);
        background-size: 200% 100%;
        animation: shimmer 1.5s infinite;
    }
    @keyframes shimmer {
        0% { background-position: 200% 0; }
        100% { background-position: -200% 0; }
    }
</style>
```

---

## 浜斻€丗ID/INP 浼樺寲瀹炴垬锛堜氦浜掑欢杩燂級

### 5.1 闀夸换鍔★紙Long Task锛夎瘑鍒?
```javascript
// longtask-detector.js - 妫€娴嬮樆濉炰富绾跨▼鐨勯暱浠诲姟
const longTaskObserver = new PerformanceObserver((list) => {
    for (const entry of list.getEntries()) {
        console.warn('[Long Task]', {
            duration: entry.duration.toFixed(2) + 'ms',
            startTime: entry.startTime.toFixed(2) + 'ms',
            attribution: entry.attribution ? [{
                name: entry.attribution[0]?.name,
                type: entry.attribution[0]?.type,
                containerType: entry.attribution[0]?.containerType
            }] : []
        });

        // 鍙戦€佸憡璀?        if (entry.duration > 100) {
            sendAlert('Long Task', entry.duration);
        }
    }
});

longTaskObserver.observe({ type: 'longtask', buffered: true });
```

### 5.2 JavaScript 鎵ц浼樺寲

```javascript
// performance-utils.js - 瀹炵敤鐨勬€ц兘浼樺寲宸ュ叿搴?
/**
 * 寤惰繜鍔犺浇闈炲叧閿?JS
 */
function loadScriptDeferred(src, integrity = '') {
    return new Promise((resolve, reject) => {
        const script = document.createElement('script');
        script.src = src;
        if (integrity) script.integrity = integrity;
        script.async = true;      // 涓嶉樆濉?HTML 瑙ｆ瀽
        script.defer = true;      // DOM 瑙ｆ瀽瀹屾垚鍚庢墽琛?        script.onload = resolve;
        script.onerror = reject;
        document.head.appendChild(script);
    });
}

/**
 * 鎳掑姞杞芥ā鍧楋紙Code Splitting锛? */
const loadFeature = async (featureName) => {
    const modules = {
        'comments': () => import('./comments.module.js'),
        'analytics': () => import('./analytics.module.js'),
        'chat': () => import('./chat.module.js')
    };
    if (modules[featureName]) {
        await modules[featureName]();
        console.log(`[Perf] Loaded: ${featureName}`);
    }
};

/**
 * 绌洪棽鏃舵墽琛岄潪绱ф€ヤ换鍔? */
function runWhenIdle(callback, timeout = 2000) {
    if ('requestIdleCallback' in window) {
        requestIdleCallback(() => callback(), { timeout });
    } else {
        setTimeout(callback, 1);
    }
}

/**
 * 闃叉姈 + 鑺傛祦缁勫悎锛堟粴鍔?杈撳叆浼樺寲锛? */
function createOptimizedHandler(fn, options = {}) {
    let lastRun = 0;
    let timeoutId = null;
    const { debounceMs = 250, throttleMs = 100 } = options;

    return function(...args) {
        const now = Date.now();
        const timeSinceLast = now - lastRun;

        // 鑺傛祦锛氶檺鍒舵墽琛岄鐜?        if (timeSinceLast >= throttleMs) {
            lastRun = now;
            fn.apply(this, args);
        } else {
            // 闃叉姈锛氭渶鍚庝竴娆¤Е鍙戝悗寤惰繜鎵ц
            clearTimeout(timeoutId);
            timeoutId = setTimeout(() => {
                lastRun = Date.now();
                fn.apply(this, args);
            }, debounceMs);
        }
    };
}

/**
 * 浜嬩欢濮旀墭锛堝噺灏戠洃鍚櫒鏁伴噺锛? */
document.addEventListener('click', createOptimizedHandler((e) => {
    // 浜嬩欢濮旀墭锛氬彧缁戝畾涓€涓洃鍚櫒澶勭悊鎵€鏈夌偣鍑?    const target = e.target.closest('[data-action]');
    if (!target) return;

    const action = target.dataset.action;
    switch (action) {
        case 'toggle-menu': toggleMenu(); break;
        case 'load-comments': loadFeature('comments'); break;
        case 'open-modal': openModal(target.dataset.modal); break;
    }
}), { throttleMs: 200 });
```

### 5.3 CSS 娓叉煋鎬ц兘

```css
/* 娓叉煋鎬ц兘鏈€浣冲疄璺?*/

/* 1. 寮哄埗 GPU 鍔犻€燂紙鎱庣敤锛屼粎蹇呰鏃讹級 */
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}
.animated-element {
    /* 浣跨敤 transform 鍜?opacity锛岃繖涓や釜灞炴€т笉瑙﹀彂閲嶆帓 */
    will-change: transform, opacity;
    animation: fadeIn 0.3s ease-out;
}

/* 2. 閬垮厤寮哄埗鍚屾甯冨眬锛圠ayout Thrashing锛?*/
.card {
    /* 浣跨敤 contain 闅旂娓叉煋鑼冨洿 */
    contain: content; /* layout style paint */
}

/* 3. 鍑忓皯閲嶆帓/閲嶇粯 */
.bad {
    element.style.left = x + 'px';     /* 瑙﹀彂閲嶆帓 */
    element.style.top = y + 'px';      /* 鍐嶆瑙﹀彂閲嶆帓 */
}
.good {
    element.style.transform = `translate(${x}px, ${y}px)`; /* 鍗曟 composite */
}

/* 4. 瀛椾綋鍔犺浇浼樺寲 */
@font-face {
    font-family: 'Inter';
    src: url('/fonts/Inter.woff2') format('woff2');
    font-display: swap; /* 鏂囧瓧鍏堟樉绀虹郴缁熷瓧浣擄紝鍐嶅垏鎹?*/
    unicode-range: U+0000-00FF; /* 浠呭姞杞介渶瑕佺殑瀛楃闆?*/
}

/* 5. 鍑忓皯 paint 鍖哄煙 */
.badge {
    contain: paint; /* 浠呯粯鍒惰嚜韬尯鍩?*/
}
```

---

## 鍏€乀TFB 涓?DNS/TCP 浼樺寲

### 6.1 TTFB 浼樺寲閾捐矾

TTFB锛堥瀛楄妭鏃堕棿锛夋槸鏈嶅姟鍣ㄥ搷搴旂涓€涓瓧鑺傚埌杈剧殑鏃堕棿锛屾槸鎵€鏈夋€ц兘鎸囨爣鐨勫湴鍩猴細

```
TTFB = 缃戠粶寤惰繜 + 鏈嶅姟鍣ㄥ鐞嗘椂闂?+ 鍝嶅簲鐢熸垚鏃堕棿

鐩爣锛? 200ms锛堝ソ锛? < 100ms锛堜紭绉€锛?
浼樺寲绛栫暐锛?鈹溾攢鈹€ 1. 缃戠粶灞傦細CDN 灏辫繎鍒嗗彂銆丏NS 鏅鸿兘瑙ｆ瀽銆丅GP 浼樺寲
鈹溾攢鈹€ 2. 缂撳瓨灞傦細Nginx 闈欐€佺紦瀛樸€丷edis 椤甸潰缂撳瓨銆丒dge Cache
鈹溾攢鈹€ 3. 搴旂敤灞傦細鏁版嵁搴撴煡璇紭鍖栥€佽繛鎺ユ睜銆侀缂栬瘧妯℃澘
鈹斺攢鈹€ 4. 鍗忚灞傦細HTTP/2銆?-RTT銆乀LS 1.3
```

### 6.2 Nginx 鍏ㄧ紦瀛橀厤缃?
```nginx
# /etc/nginx/conf.d/edge-cache.conf

# 闈欐€佽祫婧愯竟缂樼紦瀛橈紙缂撳瓨瑙勫垯鎸?URL 璺緞锛?proxy_cache_path /var/cache/nginx/static
    levels=1:2
    keys_zone=static_cache:10m
    max_size=1g
    inactive=7d
    use_temp_path=off;

# 鍔ㄦ€侀〉闈㈢紦瀛橈紙HTML 椤甸潰锛?proxy_cache_path /var/cache/nginx/pages
    levels=1:2
    keys_zone=page_cache:50m
    max_size=500m
    inactive=1h
    use_temp_path=off
    loader_threshold=300
    loader_files=200;

# HTML 缂撳瓨閰嶇疆
server {
    # ... SSL 鍜屽叾浠栭厤缃?...

    # 涓?HTML 椤甸潰璁剧疆缂撳瓨
    location ~ \.(html|htm)$ {
        proxy_pass http://127.0.0.1:3000;
        proxy_cache page_cache;
        proxy_cache_valid 200 10m;      # 200 鍝嶅簲缂撳瓨 10 鍒嗛挓
        proxy_cache_valid 404 1m;
        proxy_cache_use_stale error timeout http_500 http_502 http_503;
        proxy_cache_lock on;            # 闃叉缂撳瓨鍑荤┛
        proxy_cache_key "$scheme$request_method$host$request_uri";
        add_header X-Cache-Status $upstream_cache_status;

        # 蹇界暐娴忚鍣?no-cache 澶达紙纭繚 CDN 缂撳瓨鏈夋晥锛?        proxy_ignore_headers Cache-Control Expires Set-Cookie;
    }

    # 闈欐€佽祫婧愰暱鏈熺紦瀛?    location ~* \.(js|css|woff2|png|jpg|webp)$ {
        proxy_pass http://127.0.0.1:3000;
        proxy_cache static_cache;
        proxy_cache_valid 200 30d;
        proxy_cache_valid 404 10m;
        add_header Cache-Control "public, max-age=2592000, immutable";
        add_header X-Cache-Status $upstream_cache_status;

        # 寮€鍚?HTTP/2 Server Push锛堝彲閫夛級
        http2_push_preload on;
    }

    # 娓呴櫎缂撳瓨鎺ュ彛锛堜娇鐢?Nginx Cache Purge 妯″潡锛?    location ~ /purge(/.*) {
        proxy_cache_purge static_cache "$scheme$request_method$host$1";
        proxy_cache_purge page_cache "$scheme$request_method$host$1";
    }
}
```

### 6.3 DNS 棰勮В鏋愪笌杩炴帴棰勫缓

```html
<head>
    <!-- DNS 棰勮В鏋愶紙鎻愬墠瑙ｆ瀽澶栭儴璧勬簮鍩熷悕锛?-->
    <link rel="dns-prefetch" href="//fonts.googleapis.com">
    <link rel="dns-prefetch" href="//fonts.gstatic.com">
    <link rel="dns-prefetch" href="//cdn.example.com">
    <link rel="dns-prefetch" href="//analytics.example.com">

    <!-- 棰勮繛鎺ワ紙寤虹珛 TCP + TLS 杩炴帴锛屾彁鍓嶅畬鎴愶級 -->
    <link rel="preconnect" href="https://fonts.googleapis.com" crossorigin>
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

    <!-- 棰勫姞杞藉叧閿祫婧?-->
    <link rel="preload" href="/fonts/Inter.woff2" as="font" type="font/woff2" crossorigin>
</head>
```

---

## 涓冦€丣avaScript 鎬ц兘浼樺寲

### 7.1 鏋勫缓浜х墿鍒嗘瀽涓庝紭鍖?
```javascript
// rollup-plugin-visualizer.js 閰嶇疆绀轰緥锛圴ite/Rollup锛?// vite.config.js
import { visualizer } from 'rollup-plugin-visualizer';

export default defineConfig({
    build: {
        rollupOptions: {
            plugins: [
                visualizer({
                    filename: 'stats.html',
                    open: false,
                    gzipSize: true,
                    brotliSize: true,
                    // 鍒嗘瀽瓒呰繃 5KB 鐨勬ā鍧?                    threshold: 5120,
                    // 鏄剧ず Treemap 渚夸簬瀹氫綅澶ф枃浠?                    chart: 'treemap'
                })
            ]
        },
        // 鍒嗗寘绛栫暐锛氬垎绂荤涓夋柟搴擄紙闀挎湡缂撳瓨锛?        rollupOptions: {
            output: {
                manualChunks: {
                    'vendor-react': ['react', 'react-dom'],
                    'vendor-utils': ['lodash', 'axios', 'dayjs']
                }
            }
        },
        // 鍘嬬缉閰嶇疆
        minify: 'terser',
        terserOptions: {
            compress: {
                drop_console: true,    // 鐢熶骇鐜绉婚櫎 console
                drop_debugger: true,
                pure_funcs: ['console.log', 'console.info']
            }
        }
    }
});
```

### 7.2 React/Vue 鎬ц兘浼樺寲

```jsx
// React 鎬ц兘浼樺寲瀹炶返

// 1. 浣跨敤 React.memo 閬垮厤涓嶅繀瑕佺殑閲嶆覆鏌?const ExpensiveCard = React.memo(({ title, data }) => {
    // 浠呭綋 title 鎴?data 瀹為檯鍙樺寲鏃堕噸娓叉煋
    return (
        <div className="card">
            <h2>{title}</h2>
            <Chart data={data} />
        </div>
    );
}, (prev, next) => {
    // 鑷畾涔夋瘮杈冨嚱鏁帮紙娣卞害姣旇緝澶參鏃朵娇鐢級
    return prev.title === next.title &&
           prev.data.length === next.data.length;
});

// 2. useMemo 缂撳瓨璁＄畻缁撴灉
function DataTable({ dataset, filter }) {
    const filtered = useMemo(() => {
        return dataset.filter(item =>
            item.name.toLowerCase().includes(filter.toLowerCase())
        );
    }, [dataset, filter]); // 浠呭綋杩欎袱涓緷璧栧彉鍖栨椂閲嶆柊璁＄畻

    return <Table data={filtered} />;
}

// 3. useCallback 绋冲畾鍥炶皟寮曠敤
const handleClick = useCallback((id) => {
    dispatch({ type: 'SELECT', id });
}, [dispatch]); // 浠呭綋 dispatch 鍙樺寲鏃跺垱寤烘柊鍑芥暟

// 4. 铏氭嫙鍒楄〃锛堝鐞嗛暱鍒楄〃锛?import { FixedSizeList } from 'react-window';

function VirtualList({ items }) {
    return (
        <FixedSizeList
            height={400}
            itemCount={items.length}
            itemSize={50}
            width="100%"
        >
            {({ index, style }) => (
                <div style={style}>
                    <Item data={items[index]} />
                </div>
            )}
        </FixedSizeList>
    );
}
```

---

## 鍏€丆SS 娓叉煋浼樺寲

### 8.1 鍏抽敭 CSS 鎻愬彇涓庡唴鑱?
```bash
#!/bin/bash
# critical-css.sh - 鑷姩鎻愬彇骞跺唴鑱斿叧閿?CSS

# 浣跨敤 Penthouse锛圢ode.js锛夋彁鍙栭灞忓叧閿?CSS
npm install -g penthouse

INPUT_CSS="dist/styles.css"
OUTPUT_CSS="dist/critical.css"
URL="https://example.com/"

# 鎻愬彇棣栧睆鍏抽敭 CSS锛堣鍙?1280x800锛?penthouse \
    --url "$URL" \
    --css "$INPUT_CSS" \
    --output "$OUTPUT_CSS" \
    --width 1280 \
    --height 800 \
    --strict:false \
    --timeout 30000

# 鍐呰仈鍒?HTML 妯℃澘
CRITICAL_CSS=$(cat "$OUTPUT_CSS")
sed -i "s|<head>|<head><style>${CRITICAL_CSS}</style>|" index.html
echo "[OK] Critical CSS 宸插唴鑱?
```

### 8.2 CSS 鐢熶骇浼樺寲

```css
/* 浣跨敤 CSS Layers 閬垮厤鏍峰紡鍐茬獊鍜岃绠楀紑閿€锛堢幇浠ｆ祻瑙堝櫒锛?*/
@layer reset, base, components, utilities;

/* 鍚勫眰鏍峰紡浜掍笉骞叉壈锛屽噺灏戞牱寮忚绠楀鏉傚害 */
@layer reset {
    * { margin: 0; padding: 0; box-sizing: border-box; }
}

@layer base {
    body { font-family: system-ui, sans-serif; }
}

@layer components {
    .card { padding: 1rem; border-radius: 8px; }
}

@layer utilities {
    .text-center { text-align: center; }
}

/* 鍑忓皯閫夋嫨鍣ㄥ鏉傚害 */
.bad { /* 閬垮厤澶氬眰宓屽 */
    #app > .main-container > .content > .card > .title { }
}

.good { /* 浣跨敤 BEM 鎴栫被閫夋嫨鍣?*/
    .card__title { font-size: 1.25rem; }
}
```

---

## 涔濄€佸浘鐗囦笌濯掍綋浼樺寲

### 9.1 鍥剧墖鏍煎紡瀵规瘮

| 鏍煎紡 | 浼樼偣 | 缂虹偣 | 鏈€浣崇敤閫?|
|------|------|------|---------|
| **AVIF** | 鏈€楂樺帇缂╃巼锛堟瘮 WebP 灏?50%锛?| 娴忚鍣ㄦ敮鎸佽緝鏂?| 鐓х墖銆丅anner |
| **WebP** | 浼樼鐨勫帇缂╃巼 + Alpha | 鏃ф祻瑙堝櫒涓嶆敮鎸?| 閫氱敤鍥剧墖 |
| **JPEG** | 鍏煎鎵€鏈夋祻瑙堝櫒 | 鏈夋崯鍘嬬缉 | 闄嶇骇鍏煎 |
| **SVG** | 鐭㈤噺锛屾棤闄愭竻鏅?| 涓嶉€傚悎澶嶆潅鍥惧儚 | 鍥炬爣銆丩ogo |
| **PNG** | 鏃犳崯銆侀€忔槑搴?| 浣撶Н澶?| 鎴浘銆佸惈閫忔槑鍥?|
| **GIF** | 鍔ㄧ敾鏀寔 | 鑹插僵鏈夐檺 | 绠€鍗曞姩鐢?|

### 9.2 Python 鍥剧墖鎵归噺浼樺寲鑴氭湰

```python
#!/usr/bin/env python3
"""
image-optimizer.py - 鍏ㄨ嚜鍔ㄥ浘鐗囦紭鍖栨祦姘寸嚎
鏀寔 WebP/AVIF 杞崲銆佸昂瀵稿帇缂┿€佽川閲忎紭鍖?"""
import os
import sys
import subprocess
from pathlib import Path
from PIL import Image

# 閰嶇疆
QUALITY = {
    'webp': 85,
    'avif': 80,
    'jpeg': 85,
    'png': 85
}

SIZES = [320, 640, 960, 1280, 1920]

def optimize_image(src_path: str, output_dir: Path) -> list:
    """浼樺寲鍗曞紶鍥剧墖锛岀敓鎴愬灏哄 + 澶氭牸寮忚緭鍑?""
    path = Path(src_path)
    results = []

    try:
        with Image.open(src_path) as img:
            # 鑷姩鏃嬭浆锛堟牴鎹?EXIF锛?            img = img.convert('RGB')  # 杞负 RGB锛堝幓闄?Alpha锛?
            for size in SIZES:
                # 璁＄畻缂╂斁灏哄锛堜繚鎸佸楂樻瘮锛?                w, h = img.size
                if w <= size:
                    resized = img
                else:
                    new_h = int(h * size / w)
                    resized = img.resize((size, new_h), Image.Resampling.LANCZOS)

                base_name = f'{path.stem}-{size}'

                # 鐢熸垚 WebP
                webp_path = output_dir / f'{base_name}.webp'
                resized.save(webp_path, 'WEBP', quality=QUALITY['webp'], method=6)
                results.append(str(webp_path))

                # 鐢熸垚 AVIF锛堝鏋滃彲鐢級
                try:
                    avif_path = output_dir / f'{base_name}.avif'
                    resized.save(avif_path, 'AVIF', quality=QUALITY['avif'])
                    results.append(str(avif_path))
                except Exception:
                    pass  # PIL AVIF 鍙兘涓嶅彲鐢?
                # 鍘熷鏍煎紡锛堝鏋滃ぇ浜庣洰鏍囧昂瀵稿垯鍘嬬缉锛?                if w > size:
                    orig_path = output_dir / f'{base_name}{path.suffix}'
                    if path.suffix.lower() in ['.jpg', '.jpeg']:
                        resized.save(orig_path, 'JPEG', quality=QUALITY['jpeg'])
                    results.append(str(orig_path))

    except Exception as e:
        print(f"[ERROR] {src_path}: {e}")

    return results

def main():
    src_dir = Path(sys.argv[1] if len(sys.argv) > 1 else './src/images')
    out_dir = Path(sys.argv[2] if len(sys.argv) > 2 else './dist/images')
    out_dir.mkdir(parents=True, exist_ok=True)

    for img_path in src_dir.rglob('*.{jpg,jpeg,png,webp}'):
        print(f"Processing: {img_path}")
        results = optimize_image(img_path, out_dir)
        for r in results:
            size_kb = Path(r).stat().st_size // 1024
            print(f"  -> {Path(r).name} ({size_kb} KB)")

if __name__ == '__main__':
    main()
```

---

## 鍗併€佽嚜鍔ㄥ寲鎬ц兘娴嬭瘯涓庢寔缁泦鎴?
### 10.1 Lighthouse CI 閰嶇疆

```yaml
# lighthouserc.js
module.exports = {
    ci: {
        collect: {
            // 鎷夊彇璇锋眰鏃朵娇鐢ㄦā鎷熺Щ鍔ㄨ澶?            url: [
                'http://localhost:4000/',
                'http://localhost:4000/blog/',
                'http://localhost:4000/about/'
            ],
            startServerCommand: 'npm run preview',
            startServerReadyPattern: 'Local.*http://',
            startServerReadyTimeout: 30000,
            numberOfRuns: 3,
            settings: {
                preset: 'desktop',
                throttling: {
                    rttMs: 40,
                    throughputKbps: 10240,
                    cpuSlowdownMultiplier: 1
                }
            }
        },
        assert: {
            assertions: {
                // 鎬ц兘
                'categories:performance': ['error', { minScore: 0.9 }],
                'first-contentful-paint': ['error', { maxNumericValue: 1800 }],
                'largest-contentful-paint': ['error', { maxNumericValue: 2500 }],
                'cumulative-layout-shift': ['error', { maxNumericValue: 0.1 }],
                'interactive': ['error', { maxNumericValue: 3500 }],
                'speed-index': ['warn', { maxNumericValue: 3400 }],
                'total-blocking-time': ['error', { maxNumericValue: 300 }],
                'render-blocking-resources': ['error', { maxNumericValue: 1 }],
                // 鍙闂€?                'categories:accessibility': ['error', { minScore: 0.9 }],
                'color-contrast': 'error',
                'document-title': 'warn',
                // SEO
                'categories:seo': ['warn', { minScore: 0.9 }],
                // PWA
                'service-worker': 'warn',
                'installable-manifest': 'warn'
            }
        },
        upload: {
            target: 'temporary-public-storage' // 涓婁紶鍒颁复鏃跺叕寮€瀛樺偍
        }
    }
};
```

### 10.2 鎬ц兘鍥炲綊娴嬭瘯 GitHub Actions

```yaml
# .github/workflows/performance.yml
name: Performance Regression

on:
  pull_request:
    paths:
      - 'src/**'
      - 'public/**'
      - 'package.json'

jobs:
  lighthouse:
    runs-on: ubuntu-latest
    steps:
        - uses: actions/checkout@v4

        - name: Build Site
          run: hugo --gc --minify

        - name: Run Lighthouse CI
          uses: treosh/lighthouse-ci-action@v11
          with:
              configPath: './lighthouserc.js'
              uploadArtifacts: true
              temporaryPublicStorage: true

        - name: Upload Lighthouse Report
          uses: actions/upload-artifact@v4
          with:
              name: lighthouse-report
              path: '.lighthouseci/'

        - name: Comment on PR
          uses: actions/github-script@v7
          with:
              script: |
                  const fs = require('fs');
                  const lhr = JSON.parse(
                      fs.readFileSync('.lighthouseci/lhr-0.json', 'utf8')
                  );
                  const { categories } = lhr;
                  const comment = `
                      ## 鈿?Lighthouse 鎬ц兘鎶ュ憡
                      | 鎸囨爣 | 鍒嗘暟 | 鐘舵€?|
                      |------|------|------|
                      | Performance | ${Math.round(categories.performance.score * 100)} | ${categories.performance.score >= 0.9 ? '鉁? : '鈿狅笍'} |
                      | Accessibility | ${Math.round(categories.accessibility.score * 100)} | ${categories.accessibility.score >= 0.9 ? '鉁? : '鈿狅笍'} |
                      | Best Practices | ${Math.round(categories['best-practices'].score * 100)} | 鉁?|
                      | SEO | ${Math.round(categories.seo.score * 100)} | 鉁?|
                  `;
                  github.rest.issues.createComment({
                      issue_number: context.issue.number,
                      owner: context.repo.owner,
                      repo: context.repo.repo,
                      body: comment
                  });
```

---

## 鍗佷竴銆佺敓浜х幆澧冩€ц兘闂鎺掓煡鎵嬪唽

### 11.1 鎬ц兘闂璇婃柇娴佺▼鍥?
```
鐢ㄦ埛鎶ュ憡椤甸潰鎱?       鈹?       鈻?Step 1: 纭鏄?TTFB 闂杩樻槸娓叉煋闂锛?  鈹溾攢 TTFB 楂?鈫?妫€鏌?CDN 缂撳瓨 / 鏈嶅姟鍣ㄦ棩蹇?/ 鏁版嵁搴撴煡璇?  鈹斺攢 TTFB 姝ｅ父 鈫?缁х画 Step 2
       鈹?       鈻?Step 2: LCP 鏄惁杈炬爣锛?  鈹溾攢 LCP > 2.5s 鈫?妫€鏌ュ浘鐗囦紭鍖?/ 璧勬簮鍔犺浇浼樺厛绾?  鈹斺攢 LCP < 2.5s 鈫?缁х画 Step 3
       鈹?       鈻?Step 3: CLS 鏄惁杈炬爣锛?  鈹溾攢 CLS > 0.1 鈫?妫€鏌ュ浘鐗囧昂瀵?/ 鍔ㄦ€佸唴瀹?/ 瀛椾綋鍔犺浇
  鈹斺攢 CLS < 0.1 鈫?缁х画 Step 4
       鈹?       鈻?Step 4: INP 鏄惁杈炬爣锛?  鈹溾攢 INP > 200ms 鈫?妫€鏌?JS 鎵ц / 闀夸换鍔?/ 浜嬩欢澶勭悊
  鈹斺攢 鍏ㄩ儴杈炬爣 鈫?闂鍙兘鍦ㄧ綉缁滃眰鎴栫敤鎴风幆澧?```

### 11.2 涓€閿€ц兘璇婃柇鑴氭湰

```bash
#!/bin/bash
# diagnose-performance.sh - 蹇€熻瘖鏂綉绔欐€ц兘闂
TARGET="${1:-https://example.com}"

echo "=== Web Vitals 蹇€熻瘖鏂?==="
echo "鐩爣: $TARGET"
echo ""

# 1. TTFB 娴嬭瘯
echo "--- TTFB ---"
TTFB=$(curl -o /dev/null -s -w "%{time_starttransfer}" "$TARGET" 2>/dev/null)
echo "棣栧瓧鑺傛椂闂? $(echo "$TTFB * 1000" | bc)ms"
if (( $(echo "$TTFB > 0.5" | bc -l) )); then
    echo "[WARN] TTFB > 500ms锛屽缓璁鏌?CDN 缂撳瓨"
fi

# 2. 妫€鏌?HTTPS 鍜屽帇缂?echo ""
echo "--- HTTPS & Compression ---"
HTTP_CODE=$(curl -sI "$TARGET" | grep -i "HTTP/")
echo "HTTP 鐘舵€? $HTTP_CODE"
GZIP=$(curl -sI -H "Accept-Encoding: gzip" "$TARGET" | grep -i "content-encoding")
echo "鍘嬬缉: ${GZIP:-鏈惎鐢▆"

# 3. 妫€鏌ュ叧閿祫婧?echo ""
echo "--- 鍏抽敭璧勬簮 ---"
curl -s "$TARGET" | grep -E "(<link rel=[\"']preload|<link rel=[\"']preconnect|<img.*loading=[\"']eager)" | head -5

# 4. Lighthouse 蹇€熸祴璇曪紙Node.js锛?echo ""
echo "--- Lighthouse 鍒嗘暟 ---"
if command -v npx &> /dev/null; then
    npx lighthouse "$TARGET" --only-categories=performance --quiet --no-envelope \
        --chrome-flags="--headless --no-sandbox" 2>/dev/null | grep -E "(Performance|LCP|CLS|FID)" | head -10 || \
        echo "Lighthouse 鏈畨瑁咃紝璺宠繃"
fi

echo ""
echo "璇婃柇瀹屾垚銆傚缓璁娇鐢?Chrome DevTools Performance 闈㈡澘杩涜娣卞害鍒嗘瀽銆?
```

### 11.3 Nginx 鎬ц兘鏃ュ織鍒嗘瀽

```bash
#!/bin/bash
# analyze-slow-requests.sh - 鍒嗘瀽 Nginx 鏃ュ織涓殑鎱㈣姹?
LOG_FILE="/var/log/nginx/access.log"
THRESHOLD_MS=1000

echo "=== 鎱㈣姹傚垎鏋愶紙>${THRESHOLD_MS}ms锛?=="
echo ""

# 鎸夎矾寰勮仛鍚堟參璇锋眰
awk -v threshold=$THRESHOLD_MS '
$10 ~ /^[0-9.]+$/ && $10 * 1000 > threshold {
    # 鎻愬彇璇锋眰璺緞
    split($7, parts, "?")
    path = parts[1]
    ms = int($10 * 1000)
    count[path]++
    total_ms[path] += ms
    max_ms[path] = (ms > max_ms[path] ? ms : max_ms[path])
}
END {
    for (path in count) {
        avg = int(total_ms[path] / count[path])
        printf "%8d娆?| 骞冲潎:%6dms | 鏈€澶?%6dms | %s\n", count[path], avg, max_ms[path], path
    }
}' "$LOG_FILE" | sort -rn | head -20

echo ""
echo "--- 閿欒璇锋眰缁熻 ---"
awk '{ if ($9 >= 400) errors[$9" "$7]++ } END {
    for (e in errors) print e, errors[e] }' "$LOG_FILE" | sort -rn | head -10
```

---

## 馃敆 鎺ㄥ箍鍏ュ彛

**銆怌lashVIP 鏈哄満鎺ㄨ崘銆?*锛歔https://nav.clashvip.net](https://nav.clashvip.net) | [https://clashvip.net](https://clashvip.net)  
**銆怴PS 浼樻儬鎺ㄨ崘銆?*锛歔https://vpsvip.net](https://vpsvip.net)  
**銆怌lash for Windows 瀹㈡埛绔€?*锛歔https://clash-for-windows.net](https://clash-for-windows.net)  
**銆怌lashHub 绀惧尯銆?*锛歔https://bbs.clashhub.net](https://bbs.clashhub.net) | [https://clashhub.net](https://clashhub.net)

---

> 馃搮 鏈€鍚庢洿鏂帮細2026-09-24 | 瑙夊緱鏈夌敤锛熻缁欎粨搴撲竴涓?猸? 
> 鈿欙笍 鏈粨搴撴兜鐩?Web 鎬ц兘璇婃柇鏂规硶璁恒€丆ore Web Vitals 浼樺寲瀹炴垬涓?VPS 鎬ц兘宸ョ▼鍏ㄩ摼璺€?