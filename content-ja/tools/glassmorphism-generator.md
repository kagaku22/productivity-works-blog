---
title: "グラスモーフィズム ジェネレーター"
date: 2025-05-16
description: "無料のCSSグラスモーフィズムジェネレーター。すりガラス風エフェクトをbackdrop-filterで作成し、CSSコードを即コピー。登録不要。"
categories: ["無料ツール"]
slug: "glassmorphism-generator"
ShowToc: false
cover:
  image: "/images/covers/glassmorphism-generator-ja.png"
  alt: "グラスモーフィズム ジェネレーター"
---

ブラー・透明度・ボーダー半径などを調整するだけで、すりガラス風CSSが即生成されます。コピーしてそのまま使えます。

<div id="gm-app">
<style>
  #gm-app *,
  #gm-app *::before,
  #gm-app *::after {
    box-sizing: border-box;
  }
  #gm-app {
    font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Meiryo", "Segoe UI", sans-serif;
    font-size: 14px;
    color: #1e293b;
    line-height: 1.5;
  }
  #gm-app .gm-layout {
    display: grid;
    grid-template-columns: 320px 1fr;
    gap: 24px;
    align-items: start;
    margin-top: 20px;
  }
  @media (max-width: 700px) {
    #gm-app .gm-layout {
      grid-template-columns: 1fr;
    }
  }

  /* Controls Panel */
  #gm-app .gm-panel {
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  #gm-app .gm-panel-title {
    font-size: 13px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: #64748b;
    margin: 0 0 2px 0;
  }
  #gm-app .gm-section-divider {
    border: none;
    border-top: 1px solid #e2e8f0;
    margin: 0;
  }
  #gm-app .gm-field {
    display: flex;
    flex-direction: column;
    gap: 6px;
  }
  #gm-app .gm-label {
    font-size: 13px;
    font-weight: 600;
    color: #374151;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  #gm-app .gm-label span {
    font-weight: 400;
    color: #6366f1;
    font-size: 12px;
    font-family: monospace;
    background: #eef2ff;
    padding: 1px 6px;
    border-radius: 4px;
  }
  #gm-app input[type="range"] {
    width: 100%;
    height: 4px;
    accent-color: #6366f1;
    cursor: pointer;
  }
  #gm-app input[type="color"] {
    width: 36px;
    height: 30px;
    border: 1px solid #cbd5e1;
    border-radius: 6px;
    cursor: pointer;
    padding: 2px;
    background: #fff;
  }
  #gm-app .gm-color-row {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  #gm-app .gm-color-label {
    font-size: 12px;
    color: #64748b;
    flex: 1;
  }

  /* Presets */
  #gm-app .gm-presets {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  #gm-app .gm-preset-btn {
    padding: 5px 12px;
    font-size: 12px;
    font-weight: 600;
    border: 1.5px solid #e2e8f0;
    border-radius: 20px;
    cursor: pointer;
    background: #fff;
    color: #374151;
    transition: all 0.15s;
  }
  #gm-app .gm-preset-btn:hover,
  #gm-app .gm-preset-btn.active {
    border-color: #6366f1;
    color: #6366f1;
    background: #eef2ff;
  }

  /* Toggle */
  #gm-app .gm-toggle-row {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  #gm-app .gm-toggle {
    position: relative;
    display: inline-block;
    width: 38px;
    height: 22px;
    flex-shrink: 0;
  }
  #gm-app .gm-toggle input {
    opacity: 0;
    width: 0;
    height: 0;
  }
  #gm-app .gm-toggle-slider {
    position: absolute;
    inset: 0;
    background: #cbd5e1;
    border-radius: 22px;
    cursor: pointer;
    transition: 0.2s;
  }
  #gm-app .gm-toggle-slider::before {
    content: "";
    position: absolute;
    width: 16px;
    height: 16px;
    left: 3px;
    top: 3px;
    background: #fff;
    border-radius: 50%;
    transition: 0.2s;
  }
  #gm-app .gm-toggle input:checked + .gm-toggle-slider {
    background: #6366f1;
  }
  #gm-app .gm-toggle input:checked + .gm-toggle-slider::before {
    transform: translateX(16px);
  }
  #gm-app .gm-toggle-text {
    font-size: 13px;
    color: #374151;
  }

  /* Preview Area */
  #gm-app .gm-preview-col {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  #gm-app .gm-preview-area {
    position: relative;
    width: 100%;
    min-height: 340px;
    border-radius: 16px;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.3s;
  }
  #gm-app .gm-backdrop-shapes {
    position: absolute;
    inset: 0;
    overflow: hidden;
    pointer-events: none;
  }
  #gm-app .gm-shape {
    position: absolute;
    border-radius: 50%;
    opacity: 0.7;
  }
  #gm-app .gm-shape-1 {
    width: 200px;
    height: 200px;
    top: -40px;
    left: -40px;
  }
  #gm-app .gm-shape-2 {
    width: 160px;
    height: 160px;
    bottom: -30px;
    right: -20px;
  }
  #gm-app .gm-shape-3 {
    width: 100px;
    height: 100px;
    top: 50%;
    left: 60%;
    transform: translate(-50%, -50%);
    opacity: 0.5;
  }
  #gm-app .gm-glass-card {
    position: relative;
    z-index: 2;
    width: 260px;
    padding: 32px 28px;
    text-align: center;
    border-style: solid;
    transition: all 0.2s;
  }
  #gm-app .gm-card-inner-title {
    font-size: 18px;
    font-weight: 700;
    margin: 0 0 6px 0;
    color: inherit;
  }
  #gm-app .gm-card-inner-sub {
    font-size: 13px;
    opacity: 0.8;
    margin: 0 0 20px 0;
  }
  #gm-app .gm-card-btn {
    display: inline-block;
    padding: 8px 22px;
    background: rgba(255,255,255,0.3);
    border: 1px solid rgba(255,255,255,0.5);
    border-radius: 50px;
    font-size: 13px;
    font-weight: 600;
    color: inherit;
    cursor: default;
  }

  /* Browser support badge */
  #gm-app .gm-support-bar {
    background: #f0fdf4;
    border: 1px solid #bbf7d0;
    border-radius: 8px;
    padding: 10px 14px;
    font-size: 12px;
    color: #166534;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  #gm-app .gm-support-dot {
    width: 8px;
    height: 8px;
    background: #22c55e;
    border-radius: 50%;
    flex-shrink: 0;
  }

  /* Code Output */
  #gm-app .gm-code-block {
    background: #0f172a;
    border-radius: 12px;
    overflow: hidden;
  }
  #gm-app .gm-code-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 16px;
    background: #1e293b;
  }
  #gm-app .gm-code-label {
    font-size: 12px;
    color: #94a3b8;
    font-family: monospace;
  }
  #gm-app .gm-copy-btn {
    padding: 5px 14px;
    font-size: 12px;
    font-weight: 700;
    background: #6366f1;
    color: #fff;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    transition: background 0.15s;
  }
  #gm-app .gm-copy-btn:hover { background: #4f46e5; }
  #gm-app .gm-copy-btn.copied { background: #22c55e; }
  #gm-app pre#gm-css-output {
    margin: 0;
    padding: 16px;
    font-size: 12px;
    line-height: 1.7;
    font-family: "Fira Code", "Cascadia Code", monospace;
    overflow-x: auto;
    color: #e2e8f0;
    white-space: pre;
  }
  /* Syntax highlight tokens */
  #gm-app .tok-prop { color: #7dd3fc; }
  #gm-app .tok-val  { color: #a5f3fc; }
  #gm-app .tok-num  { color: #fde68a; }
  #gm-app .tok-unit { color: #fbbf24; }
  #gm-app .tok-fn   { color: #c4b5fd; }
  #gm-app .tok-comment { color: #64748b; font-style: italic; }
  #gm-app .tok-sel  { color: #f9a8d4; }
  #gm-app .tok-brace { color: #94a3b8; }
</style>

<div class="gm-layout">
  <!-- LEFT: Controls -->
  <div class="gm-panel">
    <div>
      <p class="gm-panel-title">プリセット</p>
      <div class="gm-presets">
        <button class="gm-preset-btn active" data-preset="frost">フロスト</button>
        <button class="gm-preset-btn" data-preset="ocean">オーシャン</button>
        <button class="gm-preset-btn" data-preset="sunset">サンセット</button>
        <button class="gm-preset-btn" data-preset="midnight">ミッドナイト</button>
        <button class="gm-preset-btn" data-preset="forest">フォレスト</button>
      </div>
    </div>

    <hr class="gm-section-divider">

    <div>
      <p class="gm-panel-title">ガラスエフェクト</p>
      <div class="gm-field">
        <div class="gm-label">ブラー強度 <span id="gm-blur-val">12px</span></div>
        <input type="range" id="gm-blur" min="0" max="30" value="12">
      </div>
      <div class="gm-field" style="margin-top:12px;">
        <div class="gm-label">透明度 <span id="gm-alpha-val">0.15</span></div>
        <input type="range" id="gm-alpha" min="0" max="100" value="15">
      </div>
      <div class="gm-field" style="margin-top:12px;">
        <div class="gm-label">角丸（ボーダー半径） <span id="gm-radius-val">16px</span></div>
        <input type="range" id="gm-radius" min="0" max="48" value="16">
      </div>
      <div class="gm-field" style="margin-top:12px;">
        <div class="gm-label">ボーダー幅 <span id="gm-bw-val">1px</span></div>
        <input type="range" id="gm-bw" min="0" max="6" value="1">
      </div>
      <div class="gm-field" style="margin-top:12px;">
        <div class="gm-label">ボーダー透明度 <span id="gm-bopacity-val">0.30</span></div>
        <input type="range" id="gm-bopacity" min="0" max="100" value="30">
      </div>
    </div>

    <hr class="gm-section-divider">

    <div>
      <p class="gm-panel-title">カラー</p>
      <div class="gm-color-row">
        <span class="gm-color-label">カードの基本色</span>
        <input type="color" id="gm-card-color" value="#ffffff">
      </div>
      <div class="gm-color-row" style="margin-top:10px;">
        <span class="gm-color-label">テキスト色</span>
        <input type="color" id="gm-text-color" value="#ffffff">
      </div>
    </div>

    <hr class="gm-section-divider">

    <div>
      <p class="gm-panel-title">背景グラデーション</p>
      <div class="gm-color-row">
        <span class="gm-color-label">カラー1</span>
        <input type="color" id="gm-bg1" value="#6366f1">
      </div>
      <div class="gm-color-row" style="margin-top:10px;">
        <span class="gm-color-label">カラー2</span>
        <input type="color" id="gm-bg2" value="#8b5cf6">
      </div>
    </div>

    <hr class="gm-section-divider">

    <div class="gm-toggle-row">
      <label class="gm-toggle">
        <input type="checkbox" id="gm-dark-toggle">
        <span class="gm-toggle-slider"></span>
      </label>
      <span class="gm-toggle-text">ダーク背景でプレビュー</span>
    </div>
  </div>

  <!-- RIGHT: Preview + Code -->
  <div class="gm-preview-col">
    <!-- Browser support -->
    <div class="gm-support-bar">
      <div class="gm-support-dot"></div>
      <div><strong>backdrop-filter</strong> は Chrome 76+・Firefox 103+・Safari 9+・Edge 17+ で対応。古いSafari向けに <code style="background:#dcfce7;padding:1px 5px;border-radius:3px;font-size:11px;">-webkit-backdrop-filter</code> も自動出力されます。</div>
    </div>

    <!-- Preview -->
    <div class="gm-preview-area" id="gm-preview-area">
      <div class="gm-backdrop-shapes">
        <div class="gm-shape gm-shape-1" id="gm-shape1"></div>
        <div class="gm-shape gm-shape-2" id="gm-shape2"></div>
        <div class="gm-shape gm-shape-3" id="gm-shape3"></div>
      </div>
      <div class="gm-glass-card" id="gm-glass-card">
        <p class="gm-card-inner-title" id="gm-card-title">ガラスカード</p>
        <p class="gm-card-inner-sub" id="gm-card-sub">すりガラスエフェクト</p>
        <span class="gm-card-btn" id="gm-card-btn">もっと見る</span>
      </div>
    </div>

    <!-- Code -->
    <div class="gm-code-block">
      <div class="gm-code-header">
        <span class="gm-code-label">CSS</span>
        <button class="gm-copy-btn" id="gm-copy-btn" onclick="gmCopyCSS()">CSSをコピー</button>
      </div>
      <pre id="gm-css-output"></pre>
    </div>
  </div>
</div>

<script>
(function() {
  var PRESETS = {
    frost:    { blur:12, alpha:15, radius:16, bw:1, bopacity:30, cardColor:"#ffffff", textColor:"#ffffff", bg1:"#6366f1", bg2:"#8b5cf6" },
    ocean:    { blur:18, alpha:20, radius:20, bw:1, bopacity:25, cardColor:"#0ea5e9", textColor:"#ffffff", bg1:"#0284c7", bg2:"#06b6d4" },
    sunset:   { blur:14, alpha:18, radius:12, bw:2, bopacity:35, cardColor:"#f97316", textColor:"#ffffff", bg1:"#ef4444", bg2:"#f97316" },
    midnight: { blur:20, alpha:10, radius:24, bw:1, bopacity:15, cardColor:"#1e293b", textColor:"#e2e8f0", bg1:"#0f172a", bg2:"#1e1b4b" },
    forest:   { blur:10, alpha:22, radius:10, bw:1, bopacity:40, cardColor:"#16a34a", textColor:"#ffffff", bg1:"#14532d", bg2:"#166534" }
  };

  function hexToRgb(hex) {
    var r = parseInt(hex.slice(1,3),16);
    var g = parseInt(hex.slice(3,5),16);
    var b = parseInt(hex.slice(5,7),16);
    return { r:r, g:g, b:b };
  }

  function getValues() {
    return {
      blur:     parseInt(document.getElementById("gm-blur").value),
      alpha:    parseInt(document.getElementById("gm-alpha").value) / 100,
      radius:   parseInt(document.getElementById("gm-radius").value),
      bw:       parseInt(document.getElementById("gm-bw").value),
      bopacity: parseInt(document.getElementById("gm-bopacity").value) / 100,
      cardColor: document.getElementById("gm-card-color").value,
      textColor: document.getElementById("gm-text-color").value,
      bg1:      document.getElementById("gm-bg1").value,
      bg2:      document.getElementById("gm-bg2").value,
      dark:     document.getElementById("gm-dark-toggle").checked
    };
  }

  function applyPreset(name) {
    var p = PRESETS[name];
    document.getElementById("gm-blur").value      = p.blur;
    document.getElementById("gm-alpha").value     = p.alpha;
    document.getElementById("gm-radius").value    = p.radius;
    document.getElementById("gm-bw").value        = p.bw;
    document.getElementById("gm-bopacity").value  = p.bopacity;
    document.getElementById("gm-card-color").value = p.cardColor;
    document.getElementById("gm-text-color").value = p.textColor;
    document.getElementById("gm-bg1").value       = p.bg1;
    document.getElementById("gm-bg2").value       = p.bg2;
    updateAll();
  }

  function updateLabels(v) {
    document.getElementById("gm-blur-val").textContent     = v.blur + "px";
    document.getElementById("gm-alpha-val").textContent    = v.alpha.toFixed(2);
    document.getElementById("gm-radius-val").textContent   = v.radius + "px";
    document.getElementById("gm-bw-val").textContent       = v.bw + "px";
    document.getElementById("gm-bopacity-val").textContent = v.bopacity.toFixed(2);
  }

  function updatePreview(v) {
    var area  = document.getElementById("gm-preview-area");
    var card  = document.getElementById("gm-glass-card");
    var s1    = document.getElementById("gm-shape1");
    var s2    = document.getElementById("gm-shape2");
    var s3    = document.getElementById("gm-shape3");

    var grad = "linear-gradient(135deg, " + v.bg1 + " 0%, " + v.bg2 + " 100%)";
    area.style.background = v.dark ? "#0f172a" : grad;

    var rgb1 = hexToRgb(v.bg1);
    var rgb2 = hexToRgb(v.bg2);
    s1.style.background = "rgba(" + rgb1.r + "," + rgb1.g + "," + rgb1.b + ",0.9)";
    s2.style.background = "rgba(" + rgb2.r + "," + rgb2.g + "," + rgb2.b + ",0.9)";
    s3.style.background = "rgba(255,255,255,0.3)";

    var cRgb = hexToRgb(v.cardColor);
    var bgColor = "rgba(" + cRgb.r + "," + cRgb.g + "," + cRgb.b + "," + v.alpha.toFixed(2) + ")";
    var borderColor = "rgba(255,255,255," + v.bopacity.toFixed(2) + ")";

    card.style.background           = bgColor;
    card.style.backdropFilter       = "blur(" + v.blur + "px)";
    card.style.webkitBackdropFilter = "blur(" + v.blur + "px)";
    card.style.borderRadius         = v.radius + "px";
    card.style.borderWidth          = v.bw + "px";
    card.style.borderColor          = borderColor;
    card.style.color                = v.textColor;

    document.getElementById("gm-card-title").style.color = v.textColor;
    document.getElementById("gm-card-sub").style.color   = v.textColor;
    document.getElementById("gm-card-btn").style.color   = v.textColor;
    document.getElementById("gm-card-btn").style.borderColor = borderColor;
  }

  function buildRawCSS(v) {
    var cRgb = hexToRgb(v.cardColor);
    var bgColor = "rgba(" + cRgb.r + "," + cRgb.g + "," + cRgb.b + "," + v.alpha.toFixed(2) + ")";
    var borderColor = "rgba(255, 255, 255, " + v.bopacity.toFixed(2) + ")";
    return [
      ".glass-card {",
      "  background: " + bgColor + ";",
      "  backdrop-filter: blur(" + v.blur + "px);",
      "  -webkit-backdrop-filter: blur(" + v.blur + "px);",
      "  border-radius: " + v.radius + "px;",
      "  border: " + v.bw + "px solid " + borderColor + ";",
      "  color: " + v.textColor + ";",
      "}"
    ].join("\n");
  }

  function tokenize(css) {
    return css
      .replace(/\/\*.*?\*\//g, '<span class="tok-comment">$&</span>')
      .replace(/(\.[\w-]+)\s*\{/g, '<span class="tok-sel">$1</span> <span class="tok-brace">{</span>')
      .replace(/\}/g, '<span class="tok-brace">}</span>')
      .replace(/([\w-]+)(\s*:\s*)/g, '<span class="tok-prop">$1</span>$2')
      .replace(/(\d+\.?\d*)(px|%|em|rem|deg)?(?=[;,\s)])/g, function(m, num, unit) {
        return '<span class="tok-num">' + num + '</span>' + (unit ? '<span class="tok-unit">' + unit + '</span>' : '');
      })
      .replace(/(rgba?|hsla?|blur|linear-gradient)\(/g, '<span class="tok-fn">$1</span>(')
      .replace(/(#[0-9a-fA-F]{3,8})/g, '<span class="tok-val">$1</span>');
  }

  function updateCode(v) {
    var raw = buildRawCSS(v);
    document.getElementById("gm-css-output").innerHTML = tokenize(raw);
  }

  function updateAll() {
    var v = getValues();
    updateLabels(v);
    updatePreview(v);
    updateCode(v);
  }

  var inputs = ["gm-blur","gm-alpha","gm-radius","gm-bw","gm-bopacity",
                "gm-card-color","gm-text-color","gm-bg1","gm-bg2","gm-dark-toggle"];
  inputs.forEach(function(id) {
    var el = document.getElementById(id);
    if (el) el.addEventListener("input", updateAll);
  });

  document.querySelectorAll("#gm-app .gm-preset-btn").forEach(function(btn) {
    btn.addEventListener("click", function() {
      document.querySelectorAll("#gm-app .gm-preset-btn").forEach(function(b){ b.classList.remove("active"); });
      btn.classList.add("active");
      applyPreset(btn.dataset.preset);
    });
  });

  updateAll();

  window.gmCopyCSS = function() {
    var v = getValues();
    var raw = buildRawCSS(v);
    navigator.clipboard.writeText(raw).then(function() {
      var btn = document.getElementById("gm-copy-btn");
      btn.textContent = "コピーしました！";
      btn.classList.add("copied");
      setTimeout(function() {
        btn.textContent = "CSSをコピー";
        btn.classList.remove("copied");
      }, 1800);
    }).catch(function() {
      var ta = document.createElement("textarea");
      ta.value = raw;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand("copy");
      document.body.removeChild(ta);
      var btn = document.getElementById("gm-copy-btn");
      btn.textContent = "コピーしました！";
      btn.classList.add("copied");
      setTimeout(function() {
        btn.textContent = "CSSをコピー";
        btn.classList.remove("copied");
      }, 1800);
    });
  };
})();
</script>
</div>

---

<div class="gm-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">Web制作の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、デザインツール・サーバー費用の経費精算もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

> ボックスシャドウを生成 → [CSSボックスシャドウジェネレーター](/ja/tools/box-shadow-generator/)
> グラデーションを作成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)
> ボタンをデザイン → [CSSボタンジェネレーター](/ja/tools/css-button-generator/)
