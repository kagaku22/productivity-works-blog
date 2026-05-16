---
title: "画面解像度チェッカー — ディスプレイ情報を即確認"
date: 2025-05-16
description: "画面解像度・ビューポートサイズ・デバイスピクセル比・色深度・向き・アクティブCSSブレークポイントをリアルタイムで確認。インストール不要の無料ツール。"
categories: ["無料ツール"]
slug: "screen-resolution"
tags: ["画面解像度", "ディスプレイ情報", "ビューポート", "ピクセル比", "レスポンシブ"]
cover:
  image: "/images/covers/screen-resolution-ja.png"
  alt: "画面解像度チェッカー"
ShowToc: false
aliases:
  - "/ja/tools/screen-size/"
  - "/ja/tools/display-info/"
---

画面解像度・ビューポートサイズ・ピクセル比・アクティブなCSSブレークポイントをリアルタイム表示。ウィンドウをリサイズすると数値が即時更新されます。

<div id="screen-app">

<style>
#screen-app {
  font-family: system-ui, -apple-system, sans-serif;
  color: #1e293b;
  max-width: 860px;
  margin: 0 auto;
}
#screen-app * { box-sizing: border-box; }

#screen-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  color: #0891b2;
  margin: 1.6rem 0 0.6rem;
  border-left: 4px solid #0891b2;
  padding-left: 0.6rem;
}

#screen-app .sa-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 0.75rem;
  margin-bottom: 1rem;
}

#screen-app .sa-card {
  background: #f0f9ff;
  border: 1px solid #bae6fd;
  border-radius: 10px;
  padding: 0.9rem 1rem;
}
#screen-app .sa-card .sa-label {
  font-size: 0.72rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #0e7490;
  margin-bottom: 0.25rem;
}
#screen-app .sa-card .sa-value {
  font-size: 1.35rem;
  font-weight: 700;
  color: #0891b2;
}
#screen-app .sa-card .sa-unit {
  font-size: 0.8rem;
  color: #64748b;
  margin-left: 2px;
}

/* Visual area */
#screen-app .sa-visual-wrap {
  background: #0f172a;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 200px;
  position: relative;
}
#screen-app .sa-screen-rect {
  position: relative;
  background: #1e293b;
  border: 2px solid #0891b2;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
}
#screen-app .sa-screen-label {
  position: absolute;
  top: -20px;
  left: 0;
  font-size: 0.7rem;
  color: #0891b2;
  white-space: nowrap;
}
#screen-app .sa-viewport-rect {
  position: absolute;
  background: rgba(8, 145, 178, 0.25);
  border: 2px dashed #06b6d4;
  border-radius: 3px;
  display: flex;
  align-items: center;
  justify-content: center;
}
#screen-app .sa-viewport-label {
  font-size: 0.65rem;
  color: #67e8f9;
  text-align: center;
  pointer-events: none;
}

/* Breakpoints */
#screen-app .sa-bp-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
#screen-app .sa-bp-tag {
  padding: 0.3rem 0.75rem;
  border-radius: 999px;
  font-size: 0.78rem;
  font-weight: 600;
  background: #e2e8f0;
  color: #64748b;
  border: 2px solid transparent;
  transition: all 0.2s;
}
#screen-app .sa-bp-tag.active {
  background: #0891b2;
  color: #fff;
  border-color: #0891b2;
}

/* Resolution comparison */
#screen-app .sa-res-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.85rem;
  margin-bottom: 1rem;
}
#screen-app .sa-res-table th {
  background: #0891b2;
  color: #fff;
  padding: 0.5rem 0.75rem;
  text-align: left;
  font-weight: 600;
}
#screen-app .sa-res-table td {
  padding: 0.45rem 0.75rem;
  border-bottom: 1px solid #e2e8f0;
}
#screen-app .sa-res-table tr:nth-child(even) td {
  background: #f8fafc;
}
#screen-app .sa-res-table tr.sa-res-match td {
  background: #ecfeff;
  font-weight: 700;
  color: #0891b2;
}
#screen-app .sa-res-table tr.sa-res-match td:first-child::before {
  content: "► ";
}

/* Browser/OS */
#screen-app .sa-info-box {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 0.9rem 1rem;
  font-size: 0.84rem;
  line-height: 1.7;
  margin-bottom: 1rem;
}
#screen-app .sa-info-box strong {
  color: #0891b2;
}

/* Copy button */
#screen-app .sa-copy-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  background: #0891b2;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0.6rem 1.2rem;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  margin-bottom: 1rem;
}
#screen-app .sa-copy-btn:hover { background: #0e7490; }
#screen-app .sa-copy-btn.copied { background: #059669; }

#screen-app .sa-live-badge {
  display: inline-block;
  background: #0891b2;
  color: #fff;
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  border-radius: 999px;
  padding: 0.1rem 0.5rem;
  vertical-align: middle;
  margin-left: 0.4rem;
  animation: sa-pulse 2s infinite;
}
@keyframes sa-pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

/* freee CTA */
#screen-app .sa-freee-cta {
  background: linear-gradient(135deg, #ecfeff 0%, #f0f9ff 100%);
  border: 1px solid #a5f3fc;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  margin-top: 1.5rem;
  font-size: 0.88rem;
  line-height: 1.6;
}
#screen-app .sa-freee-cta strong {
  display: block;
  color: #0891b2;
  font-size: 0.95rem;
  margin-bottom: 0.4rem;
}
#screen-app .sa-freee-cta a {
  display: inline-block;
  margin-top: 0.4rem;
  background: #0891b2;
  color: #fff;
  text-decoration: none;
  border-radius: 6px;
  padding: 0.45rem 1rem;
  font-weight: 700;
  font-size: 0.88rem;
  transition: background 0.2s;
}
#screen-app .sa-freee-cta a:hover { background: #0e7490; }
</style>

<h2>あなたのディスプレイ情報 <span class="sa-live-badge">LIVE</span></h2>

<div class="sa-grid" id="sa-metrics"></div>

<h2>画面とビューポートの比較（視覚）</h2>
<div class="sa-visual-wrap" id="sa-visual">
  <div class="sa-screen-rect" id="sa-screen-rect">
    <span class="sa-screen-label" id="sa-screen-rect-label"></span>
    <div class="sa-viewport-rect" id="sa-viewport-rect">
      <span class="sa-viewport-label" id="sa-vp-label"></span>
    </div>
  </div>
</div>

<h2>アクティブなCSSブレークポイント</h2>
<div class="sa-bp-list" id="sa-breakpoints"></div>

<h2>主要解像度との比較</h2>
<table class="sa-res-table">
  <thead>
    <tr><th>名称</th><th>横幅</th><th>高さ</th><th>比率</th></tr>
  </thead>
  <tbody id="sa-res-tbody"></tbody>
</table>

<h2>ブラウザ・OS情報</h2>
<div class="sa-info-box" id="sa-browser-info"></div>

<button class="sa-copy-btn" id="sa-copy-btn" onclick="saCopyAll()">
  &#128203; 情報をコピー
</button>

<script>
(function() {
  var RESOLUTIONS = [
    { name: "nHD",             w: 640,  h: 360  },
    { name: "HD (720p)",       w: 1280, h: 720  },
    { name: "フルHD (1080p)",  w: 1920, h: 1080 },
    { name: "QHD (1440p)",     w: 2560, h: 1440 },
    { name: "4K UHD",          w: 3840, h: 2160 },
    { name: "5K",              w: 5120, h: 2880 },
    { name: "8K UHD",          w: 7680, h: 4320 },
  ];

  var BREAKPOINTS = [
    { label: "sm (≥640px)",  mq: "(min-width: 640px)"  },
    { label: "md (≥768px)",  mq: "(min-width: 768px)"  },
    { label: "lg (≥1024px)", mq: "(min-width: 1024px)" },
    { label: "xl (≥1280px)", mq: "(min-width: 1280px)" },
    { label: "2xl (≥1536px)",mq: "(min-width: 1536px)" },
  ];

  function gcd(a, b) { return b === 0 ? a : gcd(b, a % b); }
  function aspectRatio(w, h) {
    var d = gcd(w, h);
    return (w / d) + ":" + (h / d);
  }

  function detectBrowser(ua) {
    if (/Edg\//.test(ua))       return "Microsoft Edge";
    if (/OPR\/|Opera/.test(ua)) return "Opera";
    if (/Chrome\//.test(ua))    return "Google Chrome";
    if (/Firefox\//.test(ua))   return "Mozilla Firefox";
    if (/Safari\//.test(ua))    return "Apple Safari";
    return "不明";
  }
  function detectOS(ua) {
    if (/Windows NT 10/.test(ua)) return "Windows 10/11";
    if (/Windows NT/.test(ua))    return "Windows";
    if (/Mac OS X/.test(ua))      return "macOS";
    if (/Android/.test(ua))       return "Android";
    if (/iPhone|iPad/.test(ua))   return "iOS";
    if (/Linux/.test(ua))         return "Linux";
    return "不明";
  }
  function detectDevice(ua) {
    if (/Mobile|Android|iPhone/.test(ua)) return "モバイル";
    if (/iPad|Tablet/.test(ua))           return "タブレット";
    return "デスクトップ";
  }

  function getData() {
    var sw = window.screen.width;
    var sh = window.screen.height;
    var vw = window.innerWidth;
    var vh = window.innerHeight;
    var dpr = window.devicePixelRatio || 1;
    var cd = window.screen.colorDepth || 24;
    var orient = (sw > sh) ? "横向き" : "縦向き";
    if (window.screen.orientation && window.screen.orientation.type) {
      orient = /landscape/.test(window.screen.orientation.type) ? "横向き" : "縦向き";
    }
    return { sw: sw, sh: sh, vw: vw, vh: vh, dpr: dpr, cd: cd, orient: orient };
  }

  function renderMetrics(d) {
    var cards = [
      { label: "画面の横幅",        value: d.sw, unit: "px" },
      { label: "画面の高さ",        value: d.sh, unit: "px" },
      { label: "画面のアスペクト比", value: aspectRatio(d.sw, d.sh), unit: "" },
      { label: "ビューポート横幅",   value: d.vw, unit: "px" },
      { label: "ビューポート高さ",   value: d.vh, unit: "px" },
      { label: "ビューポート比",     value: aspectRatio(d.vw, d.vh), unit: "" },
      { label: "デバイスピクセル比", value: d.dpr.toFixed(2), unit: "x" },
      { label: "色深度",            value: d.cd, unit: "bit" },
      { label: "向き",              value: d.orient, unit: "" },
    ];
    var el = document.getElementById("sa-metrics");
    el.innerHTML = cards.map(function(c) {
      return '<div class="sa-card">' +
        '<div class="sa-label">' + c.label + '</div>' +
        '<div class="sa-value">' + c.value + '<span class="sa-unit">' + c.unit + '</span></div>' +
        '</div>';
    }).join("");
  }

  function renderVisual(d) {
    var container = document.getElementById("sa-visual");
    var cw = container.offsetWidth - 48;
    var ch = Math.max(160, container.offsetHeight - 48);
    var scaleX = cw / d.sw;
    var scaleY = ch / d.sh;
    var scale = Math.min(scaleX, scaleY, 1);

    var srW = Math.round(d.sw * scale);
    var srH = Math.round(d.sh * scale);
    var vpW = Math.round(d.vw * scale);
    var vpH = Math.round(d.vh * scale);

    var sr = document.getElementById("sa-screen-rect");
    sr.style.width  = srW + "px";
    sr.style.height = srH + "px";

    document.getElementById("sa-screen-rect-label").textContent =
      "画面: " + d.sw + " x " + d.sh;

    var vp = document.getElementById("sa-viewport-rect");
    vp.style.width  = Math.min(vpW, srW) + "px";
    vp.style.height = Math.min(vpH, srH) + "px";

    document.getElementById("sa-vp-label").textContent =
      "ビューポート\n" + d.vw + "x" + d.vh;
  }

  function renderBreakpoints() {
    var el = document.getElementById("sa-breakpoints");
    el.innerHTML = BREAKPOINTS.map(function(bp) {
      var active = window.matchMedia(bp.mq).matches;
      return '<span class="sa-bp-tag' + (active ? " active" : "") + '">' + bp.label + '</span>';
    }).join("");
  }

  function renderResTable(d) {
    var tbody = document.getElementById("sa-res-tbody");
    var match = -1;
    var minDiff = Infinity;
    RESOLUTIONS.forEach(function(r, i) {
      var diff = Math.abs(r.w - d.sw) + Math.abs(r.h - d.sh);
      if (diff < minDiff) { minDiff = diff; match = i; }
    });
    tbody.innerHTML = RESOLUTIONS.map(function(r, i) {
      var cls = (i === match && minDiff < 300) ? ' class="sa-res-match"' : '';
      return '<tr' + cls + '><td>' + r.name + '</td><td>' + r.w + 'px</td><td>' + r.h + 'px</td><td>' + aspectRatio(r.w, r.h) + '</td></tr>';
    }).join("");
  }

  function renderBrowser() {
    var ua = navigator.userAgent;
    var el = document.getElementById("sa-browser-info");
    el.innerHTML =
      '<strong>ブラウザ:</strong> ' + detectBrowser(ua) + '<br>' +
      '<strong>OS:</strong> ' + detectOS(ua) + '<br>' +
      '<strong>デバイス種別:</strong> ' + detectDevice(ua) + '<br>' +
      '<strong>タッチ対応:</strong> ' + ('ontouchstart' in window ? 'あり' : 'なし') + '<br>' +
      '<strong>ユーザーエージェント:</strong> <span style="word-break:break-all;color:#334155">' + ua + '</span>';
  }

  function renderAll() {
    var d = getData();
    renderMetrics(d);
    renderVisual(d);
    renderBreakpoints();
    renderResTable(d);
  }

  window.saCopyAll = function() {
    var d = getData();
    var ua = navigator.userAgent;
    var lines = [
      "=== 画面解像度情報 ===",
      "画面: " + d.sw + " x " + d.sh + " (" + aspectRatio(d.sw, d.sh) + ")",
      "ビューポート: " + d.vw + " x " + d.vh + " (" + aspectRatio(d.vw, d.vh) + ")",
      "デバイスピクセル比: " + d.dpr.toFixed(2) + "x",
      "色深度: " + d.cd + " bit",
      "向き: " + d.orient,
      "ブラウザ: " + detectBrowser(ua),
      "OS: " + detectOS(ua),
      "デバイス: " + detectDevice(ua),
      "ユーザーエージェント: " + ua,
    ];
    var bp = BREAKPOINTS.filter(function(b) { return window.matchMedia(b.mq).matches; });
    lines.push("アクティブブレークポイント: " + (bp.length ? bp.map(function(b){return b.label;}).join(", ") : "なし"));
    lines.push("取得日時: " + new Date().toLocaleString("ja-JP"));

    navigator.clipboard.writeText(lines.join("\n")).then(function() {
      var btn = document.getElementById("sa-copy-btn");
      btn.textContent = "コピーしました!";
      btn.classList.add("copied");
      setTimeout(function() {
        btn.textContent = "\uD83D\uDCCB 情報をコピー";
        btn.classList.remove("copied");
      }, 2000);
    }).catch(function() {
      alert(lines.join("\n"));
    });
  };

  renderAll();
  renderBrowser();

  var resizeTimer;
  window.addEventListener("resize", function() {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(renderAll, 80);
  });

  window.addEventListener("orientationchange", function() {
    setTimeout(renderAll, 300);
  });
})();
</script>

<div class="sa-freee-cta">
  <strong>デバイス管理もfreeeで効率化</strong>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
</div>

</div>

---

**デバイス管理もfreeeで効率化**
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
