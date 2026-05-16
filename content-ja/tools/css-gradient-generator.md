---
title: "CSSグラデーションジェネレーター｜無料オンラインツール（リニア・放射・コニック対応）"
date: 2025-05-16
description: "CSSグラデーションをブラウザ上で簡単作成。リニア・放射・コニックの3種類に対応。カラーストップ最大5個、12種以上のプリセット、角度調整、CSSコードをワンクリックでコピー。無料・登録不要。"
categories: ["無料ツール"]
tags: ["cssグラデーション", "グラデーションジェネレーター", "リニアグラデーション", "css ツール", "ウェブデザイン"]
slug: "css-gradient-generator"
aliases: ["/ja/tools/gradient-maker/", "/ja/tools/gradient-generator/"]
cover:
  image: "/images/covers/css-gradient-generator-ja.png"
  alt: "CSSグラデーションジェネレーター"
ShowToc: false
---

<div id="grad-app-ja">

<style>
#grad-app-ja {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 0 48px 0;
  color: #374151;
}

#grad-app-ja * {
  box-sizing: border-box;
}

/* Preview */
.gja-preview-wrap {
  border-radius: 16px;
  overflow: hidden;
  margin-bottom: 20px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.15);
  position: relative;
}

.gja-preview {
  width: 100%;
  height: 320px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  transition: background 0.2s;
}

.gja-preview-label {
  position: absolute;
  bottom: 14px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.45);
  color: #fff;
  font-size: 12px;
  padding: 4px 12px;
  border-radius: 20px;
  white-space: nowrap;
  pointer-events: none;
}

/* Cards */
.gja-card {
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 2px 16px rgba(0,0,0,0.07);
  padding: 22px 24px;
  margin-bottom: 16px;
}

.gja-card-title {
  margin: 0 0 16px 0;
  font-size: 13px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  border-bottom: 2px solid #f3f4f6;
  padding-bottom: 10px;
}

/* Type toggle */
.gja-type-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.gja-type-btn {
  flex: 1;
  min-width: 90px;
  padding: 9px 14px;
  border: 2px solid #e5e7eb;
  border-radius: 10px;
  background: #f9fafb;
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  cursor: pointer;
  transition: all 0.18s;
  text-align: center;
}

.gja-type-btn:hover {
  border-color: #9ca3af;
  background: #f3f4f6;
}

.gja-type-btn.gja-active {
  border-color: #374151;
  background: #374151;
  color: #fff;
}

/* Linear angle */
.gja-angle-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-top: 14px;
}

.gja-angle-label {
  font-size: 13px;
  font-weight: 600;
  color: #6b7280;
  white-space: nowrap;
  width: 80px;
  flex-shrink: 0;
}

.gja-angle-slider {
  flex: 1;
  height: 6px;
  border-radius: 3px;
  -webkit-appearance: none;
  appearance: none;
  background: #e5e7eb;
  outline: none;
  cursor: pointer;
  min-width: 0;
}

.gja-angle-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #374151;
  border: 3px solid #fff;
  box-shadow: 0 1px 6px rgba(0,0,0,0.25);
  cursor: pointer;
}

.gja-angle-slider::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #374151;
  border: 3px solid #fff;
  box-shadow: 0 1px 6px rgba(0,0,0,0.25);
  cursor: pointer;
}

.gja-angle-num {
  width: 64px;
  padding: 7px 10px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  text-align: center;
  color: #374151;
  font-family: 'Courier New', monospace;
  flex-shrink: 0;
}

.gja-angle-num:focus {
  outline: none;
  border-color: #374151;
}

/* Radial options */
.gja-radial-row {
  display: flex;
  gap: 16px;
  margin-top: 14px;
  flex-wrap: wrap;
  align-items: flex-start;
}

.gja-radial-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.gja-field-label {
  font-size: 12px;
  font-weight: 700;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.gja-select {
  padding: 8px 12px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  font-size: 13px;
  color: #374151;
  background: #fff;
  cursor: pointer;
  font-weight: 600;
}

.gja-select:focus {
  outline: none;
  border-color: #374151;
}

/* Position grid */
.gja-pos-grid {
  display: grid;
  grid-template-columns: repeat(3, 32px);
  gap: 4px;
}

.gja-pos-dot {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  border: 2px solid #e5e7eb;
  background: #f9fafb;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  color: #9ca3af;
  transition: all 0.15s;
}

.gja-pos-dot:hover {
  border-color: #9ca3af;
  background: #f3f4f6;
}

.gja-pos-dot.gja-pos-active {
  border-color: #374151;
  background: #374151;
  color: #fff;
}

/* Color stops */
.gja-stops-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 14px;
}

.gja-stop-row {
  display: flex;
  align-items: center;
  gap: 10px;
}

.gja-stop-pos-wrap {
  display: flex;
  align-items: center;
  gap: 6px;
  flex: 1;
  min-width: 0;
}

.gja-stop-pos-label {
  font-size: 12px;
  color: #6b7280;
  font-weight: 600;
  white-space: nowrap;
  width: 26px;
  flex-shrink: 0;
}

.gja-stop-pos-slider {
  flex: 1;
  height: 5px;
  border-radius: 3px;
  -webkit-appearance: none;
  appearance: none;
  background: #e5e7eb;
  outline: none;
  cursor: pointer;
  min-width: 0;
}

.gja-stop-pos-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #374151;
  border: 2px solid #fff;
  box-shadow: 0 1px 4px rgba(0,0,0,0.2);
  cursor: pointer;
}

.gja-stop-pos-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #374151;
  border: 2px solid #fff;
  box-shadow: 0 1px 4px rgba(0,0,0,0.2);
  cursor: pointer;
}

.gja-stop-hex {
  min-width: 0;
  padding: 8px 10px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  font-size: 13px;
  font-family: 'Courier New', monospace;
  color: #374151;
  width: 90px;
  flex-shrink: 0;
}

.gja-stop-hex:focus {
  outline: none;
  border-color: #374151;
}

.gja-stop-pos-num {
  width: 46px;
  padding: 5px 6px;
  border: 2px solid #e5e7eb;
  border-radius: 6px;
  font-size: 12px;
  text-align: center;
  color: #374151;
  font-family: 'Courier New', monospace;
  flex-shrink: 0;
}

.gja-stop-pos-num:focus {
  outline: none;
  border-color: #374151;
}

.gja-stop-remove {
  width: 28px;
  height: 28px;
  border-radius: 7px;
  border: 2px solid #e5e7eb;
  background: #fff;
  color: #9ca3af;
  font-size: 16px;
  line-height: 1;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.15s;
  flex-shrink: 0;
}

.gja-stop-remove:hover {
  border-color: #ef4444;
  color: #ef4444;
  background: #fef2f2;
}

/* Gradient bar */
.gja-gradient-bar {
  height: 18px;
  border-radius: 9px;
  margin-bottom: 14px;
  box-shadow: inset 0 1px 4px rgba(0,0,0,0.12);
}

/* Add stop button */
.gja-add-stop-btn {
  padding: 8px 18px;
  border: 2px dashed #d1d5db;
  border-radius: 10px;
  background: #f9fafb;
  font-size: 13px;
  font-weight: 600;
  color: #6b7280;
  cursor: pointer;
  transition: all 0.18s;
}

.gja-add-stop-btn:hover {
  border-color: #374151;
  color: #374151;
  background: #f3f4f6;
}

/* Presets */
.gja-presets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  gap: 10px;
}

.gja-preset-item {
  border-radius: 12px;
  overflow: hidden;
  cursor: pointer;
  border: 2px solid transparent;
  transition: all 0.18s;
  box-shadow: 0 1px 6px rgba(0,0,0,0.1);
}

.gja-preset-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(0,0,0,0.18);
}

.gja-preset-item.gja-preset-active {
  border-color: #374151;
}

.gja-preset-swatch {
  height: 52px;
  width: 100%;
}

.gja-preset-name {
  background: #fff;
  padding: 5px 8px;
  font-size: 11px;
  font-weight: 600;
  color: #374151;
  text-align: center;
  border-top: 1px solid #f3f4f6;
}

/* Action buttons */
.gja-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

.gja-btn {
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.18s;
  letter-spacing: 0.02em;
}

.gja-btn-primary {
  background: #374151;
  color: #fff;
}

.gja-btn-primary:hover {
  background: #1f2937;
}

.gja-btn-secondary {
  background: #f3f4f6;
  color: #374151;
  border: 2px solid #e5e7eb;
}

.gja-btn-secondary:hover {
  background: #e5e7eb;
}

/* CSS output */
.gja-css-output {
  background: #1a1b2e;
  border-radius: 12px;
  padding: 20px 22px;
  position: relative;
  font-family: 'Courier New', monospace;
  font-size: 13px;
  line-height: 1.9;
  color: #a5b4fc;
}

.gja-css-prop { color: #7dd3fc; }
.gja-css-val  { color: #fde68a; }
.gja-css-semi { color: #94a3b8; }

.gja-css-copy-btn {
  position: absolute;
  top: 12px;
  right: 14px;
  padding: 5px 14px;
  background: rgba(255,255,255,0.08);
  color: #a5b4fc;
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: 6px;
  font-size: 11px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}

.gja-css-copy-btn:hover {
  background: rgba(255,255,255,0.16);
}

.gja-css-copy-btn.gja-copied {
  background: rgba(52,211,153,0.2);
  color: #6ee7b7;
  border-color: rgba(52,211,153,0.3);
}

/* Responsive */
@media (max-width: 600px) {
  .gja-preview { height: 220px; }
  .gja-card { padding: 16px 14px; }
  .gja-presets-grid { grid-template-columns: repeat(auto-fill, minmax(85px, 1fr)); }
  .gja-stop-row { flex-wrap: wrap; }
  .gja-angle-label { width: 60px; font-size: 12px; }
  .gja-actions { flex-direction: column; }
  .gja-btn { text-align: center; }
}
</style>

<!-- Preview -->
<div class="gja-preview-wrap">
  <div class="gja-preview" id="gja-preview"></div>
  <div class="gja-preview-label" id="gja-preview-label">linear-gradient(135deg, ...)</div>
</div>

<!-- Actions -->
<div class="gja-actions">
  <button class="gja-btn gja-btn-primary" id="gja-random-btn">ランダム生成</button>
  <button class="gja-btn gja-btn-secondary" id="gja-copy-css-main-btn">CSSをコピー</button>
</div>

<!-- Gradient Type -->
<div class="gja-card">
  <div class="gja-card-title">グラデーションの種類</div>
  <div class="gja-type-row">
    <button class="gja-type-btn gja-active" data-type="linear">リニア</button>
    <button class="gja-type-btn" data-type="radial">放射状</button>
    <button class="gja-type-btn" data-type="conic">コニック</button>
  </div>

  <!-- Linear controls -->
  <div id="gja-linear-controls">
    <div class="gja-angle-row">
      <span class="gja-angle-label">角度</span>
      <input type="range" class="gja-angle-slider" id="gja-angle-slider" min="0" max="360" value="135">
      <input type="number" class="gja-angle-num" id="gja-angle-num" min="0" max="360" value="135"> °
    </div>
  </div>

  <!-- Radial controls -->
  <div id="gja-radial-controls" style="display:none;">
    <div class="gja-radial-row">
      <div class="gja-radial-field">
        <span class="gja-field-label">形状</span>
        <select class="gja-select" id="gja-radial-shape">
          <option value="circle">円形</option>
          <option value="ellipse" selected>楕円形</option>
        </select>
      </div>
      <div class="gja-radial-field">
        <span class="gja-field-label">中心位置</span>
        <div class="gja-pos-grid" id="gja-pos-grid">
          <div class="gja-pos-dot" data-pos="left top" title="左上">↖</div>
          <div class="gja-pos-dot" data-pos="center top" title="上">↑</div>
          <div class="gja-pos-dot" data-pos="right top" title="右上">↗</div>
          <div class="gja-pos-dot" data-pos="left center" title="左">←</div>
          <div class="gja-pos-dot gja-pos-active" data-pos="center center" title="中央">·</div>
          <div class="gja-pos-dot" data-pos="right center" title="右">→</div>
          <div class="gja-pos-dot" data-pos="left bottom" title="左下">↙</div>
          <div class="gja-pos-dot" data-pos="center bottom" title="下">↓</div>
          <div class="gja-pos-dot" data-pos="right bottom" title="右下">↘</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Conic controls -->
  <div id="gja-conic-controls" style="display:none;">
    <div class="gja-angle-row">
      <span class="gja-angle-label">開始角度</span>
      <input type="range" class="gja-angle-slider" id="gja-conic-angle-slider" min="0" max="360" value="0">
      <input type="number" class="gja-angle-num" id="gja-conic-angle-num" min="0" max="360" value="0"> °
    </div>
  </div>
</div>

<!-- Color Stops -->
<div class="gja-card">
  <div class="gja-card-title">カラーストップ</div>
  <div class="gja-gradient-bar" id="gja-gradient-bar"></div>
  <div class="gja-stops-list" id="gja-stops-list"></div>
  <button class="gja-add-stop-btn" id="gja-add-stop-btn">+ カラーストップを追加</button>
</div>

<!-- Presets -->
<div class="gja-card">
  <div class="gja-card-title">プリセット</div>
  <div class="gja-presets-grid" id="gja-presets-grid"></div>
</div>

<!-- CSS Output -->
<div class="gja-card">
  <div class="gja-card-title">CSSコード</div>
  <div class="gja-css-output" id="gja-css-output">
    <button class="gja-css-copy-btn" id="gja-css-copy-btn">コピー</button>
    <div id="gja-css-code"></div>
  </div>
</div>

<script>
(function() {
  'use strict';

  // ---- State ----
  var state = {
    type: 'linear',
    angle: 135,
    conicAngle: 0,
    radialShape: 'ellipse',
    radialPos: 'center center',
    stops: [
      { color: '#667eea', pos: 0 },
      { color: '#764ba2', pos: 100 }
    ]
  };

  var activePreset = null;

  // ---- Presets (Japanese names) ----
  var PRESETS = [
    { name: '夕焼け',     type: 'linear', angle: 135, stops: [{ color: '#f093fb', pos: 0 }, { color: '#f5576c', pos: 100 }] },
    { name: '海',         type: 'linear', angle: 160, stops: [{ color: '#2980b9', pos: 0 }, { color: '#6dd5fa', pos: 50 }, { color: '#ffffff', pos: 100 }] },
    { name: '森林',       type: 'linear', angle: 120, stops: [{ color: '#11998e', pos: 0 }, { color: '#38ef7d', pos: 100 }] },
    { name: 'ネオン',     type: 'linear', angle: 90,  stops: [{ color: '#f7971e', pos: 0 }, { color: '#ffd200', pos: 50 }, { color: '#21d4fd', pos: 100 }] },
    { name: 'オーロラ',   type: 'linear', angle: 135, stops: [{ color: '#a8edea', pos: 0 }, { color: '#fed6e3', pos: 100 }] },
    { name: '深夜',       type: 'linear', angle: 180, stops: [{ color: '#0f0c29', pos: 0 }, { color: '#302b63', pos: 50 }, { color: '#24243e', pos: 100 }] },
    { name: '桜',         type: 'linear', angle: 135, stops: [{ color: '#ffecd2', pos: 0 }, { color: '#fcb69f', pos: 100 }] },
    { name: '抹茶',       type: 'linear', angle: 120, stops: [{ color: '#d4fc79', pos: 0 }, { color: '#96e6a1', pos: 100 }] },
    { name: '炎',         type: 'linear', angle: 90,  stops: [{ color: '#f83600', pos: 0 }, { color: '#f9d423', pos: 100 }] },
    { name: '藤色',       type: 'linear', angle: 135, stops: [{ color: '#e0c3fc', pos: 0 }, { color: '#8ec5fc', pos: 100 }] },
    { name: '宇宙',       type: 'conic',  conicAngle: 0, stops: [{ color: '#6a3093', pos: 0 }, { color: '#a044ff', pos: 33 }, { color: '#6a3093', pos: 66 }, { color: '#a044ff', pos: 100 }] },
    { name: 'マンゴー',   type: 'linear', angle: 135, stops: [{ color: '#ffe259', pos: 0 }, { color: '#ffa751', pos: 100 }] }
  ];

  // ---- DOM refs ----
  var previewEl       = document.getElementById('gja-preview');
  var previewLabel    = document.getElementById('gja-preview-label');
  var gradientBar     = document.getElementById('gja-gradient-bar');
  var stopsList       = document.getElementById('gja-stops-list');
  var addStopBtn      = document.getElementById('gja-add-stop-btn');
  var presetsGrid     = document.getElementById('gja-presets-grid');
  var cssCode         = document.getElementById('gja-css-code');
  var cssCopyBtn      = document.getElementById('gja-css-copy-btn');
  var copyCssMainBtn  = document.getElementById('gja-copy-css-main-btn');
  var randomBtn       = document.getElementById('gja-random-btn');
  var angleSlider     = document.getElementById('gja-angle-slider');
  var angleNum        = document.getElementById('gja-angle-num');
  var conicSlider     = document.getElementById('gja-conic-angle-slider');
  var conicNum        = document.getElementById('gja-conic-angle-num');
  var radialShape     = document.getElementById('gja-radial-shape');
  var linearControls  = document.getElementById('gja-linear-controls');
  var radialControls  = document.getElementById('gja-radial-controls');
  var conicControls   = document.getElementById('gja-conic-controls');

  // ---- CSS Builder ----
  function buildGradientCSS() {
    var stops = state.stops.map(function(s) {
      return s.color + ' ' + s.pos + '%';
    }).join(', ');

    if (state.type === 'linear') {
      return 'linear-gradient(' + state.angle + 'deg, ' + stops + ')';
    } else if (state.type === 'radial') {
      return 'radial-gradient(' + state.radialShape + ' at ' + state.radialPos + ', ' + stops + ')';
    } else {
      return 'conic-gradient(from ' + state.conicAngle + 'deg, ' + stops + ')';
    }
  }

  function buildFullCSS() {
    var grad = buildGradientCSS();
    return 'background: ' + grad + ';\nbackground: -webkit-' + grad + ';';
  }

  // ---- Render ----
  function render() {
    var grad = buildGradientCSS();
    previewEl.style.background = grad;
    gradientBar.style.background = 'linear-gradient(to right, ' +
      state.stops.map(function(s) { return s.color + ' ' + s.pos + '%'; }).join(', ') + ')';
    previewLabel.textContent = grad.length > 80 ? grad.slice(0, 77) + '...' : grad;
    renderCSS(grad);
    renderStops();
  }

  function renderCSS(grad) {
    cssCode.innerHTML =
      '<span class="gja-css-prop">background</span><span class="gja-css-semi">: </span>' +
      '<span class="gja-css-val">-webkit-' + escHtml(grad) + '</span><span class="gja-css-semi">;</span>\n' +
      '<span class="gja-css-prop">background</span><span class="gja-css-semi">: </span>' +
      '<span class="gja-css-val">' + escHtml(grad) + '</span><span class="gja-css-semi">;</span>';
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function renderStops() {
    stopsList.innerHTML = '';
    state.stops.forEach(function(stop, idx) {
      var row = document.createElement('div');
      row.className = 'gja-stop-row';

      // Color swatch
      var swatchWrap = document.createElement('label');
      swatchWrap.style.cssText = 'position:relative;cursor:pointer;flex-shrink:0;';
      var swatch = document.createElement('div');
      swatch.style.cssText = 'width:38px;height:38px;border-radius:10px;border:2px solid #e5e7eb;background:' + stop.color + ';cursor:pointer;';
      var colorInput = document.createElement('input');
      colorInput.type = 'color';
      colorInput.value = stop.color;
      colorInput.style.cssText = 'position:absolute;opacity:0;width:0;height:0;';
      colorInput.addEventListener('input', (function(i) {
        return function() {
          state.stops[i].color = colorInput.value;
          swatch.style.background = colorInput.value;
          hexField.value = colorInput.value;
          render();
        };
      })(idx));
      swatchWrap.appendChild(swatch);
      swatchWrap.appendChild(colorInput);
      swatchWrap.addEventListener('click', function() { colorInput.click(); });

      // HEX field
      var hexField = document.createElement('input');
      hexField.type = 'text';
      hexField.className = 'gja-stop-hex';
      hexField.value = stop.color;
      hexField.maxLength = 7;
      hexField.spellcheck = false;
      hexField.addEventListener('input', (function(i, sw, ci) {
        return function() {
          var v = hexField.value.trim();
          if (!v.startsWith('#')) v = '#' + v;
          if (/^#[0-9a-fA-F]{6}$/.test(v)) {
            state.stops[i].color = v;
            sw.style.background = v;
            ci.value = v;
            render();
          }
        };
      })(idx, swatch, colorInput));

      // Position
      var posWrap = document.createElement('div');
      posWrap.className = 'gja-stop-pos-wrap';

      var posLabel = document.createElement('span');
      posLabel.className = 'gja-stop-pos-label';
      posLabel.textContent = '位置';

      var posSlider = document.createElement('input');
      posSlider.type = 'range';
      posSlider.className = 'gja-stop-pos-slider';
      posSlider.min = 0;
      posSlider.max = 100;
      posSlider.value = stop.pos;

      var posNum = document.createElement('input');
      posNum.type = 'number';
      posNum.className = 'gja-stop-pos-num';
      posNum.min = 0;
      posNum.max = 100;
      posNum.value = stop.pos;

      posSlider.addEventListener('input', (function(i, pn) {
        return function() {
          state.stops[i].pos = parseInt(posSlider.value);
          pn.value = posSlider.value;
          render();
        };
      })(idx, posNum));

      posNum.addEventListener('input', (function(i, ps) {
        return function() {
          var v = Math.max(0, Math.min(100, parseInt(posNum.value) || 0));
          state.stops[i].pos = v;
          ps.value = v;
          render();
        };
      })(idx, posSlider));

      posWrap.appendChild(posLabel);
      posWrap.appendChild(posSlider);
      posWrap.appendChild(posNum);

      // Remove button
      var removeBtn = document.createElement('button');
      removeBtn.className = 'gja-stop-remove';
      removeBtn.textContent = '×';
      removeBtn.title = '削除';
      removeBtn.addEventListener('click', (function(i) {
        return function() {
          if (state.stops.length <= 2) return;
          state.stops.splice(i, 1);
          render();
        };
      })(idx));

      row.appendChild(swatchWrap);
      row.appendChild(hexField);
      row.appendChild(posWrap);
      row.appendChild(removeBtn);
      stopsList.appendChild(row);
    });
  }

  // ---- Presets ----
  function renderPresets() {
    PRESETS.forEach(function(preset, idx) {
      var item = document.createElement('div');
      item.className = 'gja-preset-item';
      item.dataset.idx = idx;

      var swatch = document.createElement('div');
      swatch.className = 'gja-preset-swatch';

      var stops = preset.stops.map(function(s) { return s.color + ' ' + s.pos + '%'; }).join(', ');
      var grad;
      if (preset.type === 'radial') {
        grad = 'radial-gradient(ellipse at center center, ' + stops + ')';
      } else if (preset.type === 'conic') {
        grad = 'linear-gradient(135deg, ' + stops + ')';
      } else {
        grad = 'linear-gradient(' + preset.angle + 'deg, ' + stops + ')';
      }
      swatch.style.background = grad;

      var nameEl = document.createElement('div');
      nameEl.className = 'gja-preset-name';
      nameEl.textContent = preset.name;

      item.appendChild(swatch);
      item.appendChild(nameEl);

      item.addEventListener('click', function() {
        applyPreset(idx);
      });

      presetsGrid.appendChild(item);
    });
  }

  function applyPreset(idx) {
    var preset = PRESETS[idx];
    state.type = preset.type;
    state.stops = preset.stops.map(function(s) { return { color: s.color, pos: s.pos }; });

    if (preset.type === 'linear') {
      state.angle = preset.angle;
      angleSlider.value = state.angle;
      angleNum.value = state.angle;
    } else if (preset.type === 'radial') {
      state.radialShape = preset.shape || 'ellipse';
      state.radialPos = preset.pos || 'center center';
      radialShape.value = state.radialShape;
      syncPosGrid(state.radialPos);
    } else if (preset.type === 'conic') {
      state.conicAngle = preset.conicAngle || 0;
      conicSlider.value = state.conicAngle;
      conicNum.value = state.conicAngle;
    }

    document.querySelectorAll('#grad-app-ja .gja-type-btn').forEach(function(btn) {
      btn.classList.toggle('gja-active', btn.dataset.type === state.type);
    });
    showTypeControls(state.type);

    document.querySelectorAll('#grad-app-ja .gja-preset-item').forEach(function(el, i) {
      el.classList.toggle('gja-preset-active', i === idx);
    });

    activePreset = idx;
    render();
  }

  function showTypeControls(type) {
    linearControls.style.display = type === 'linear' ? '' : 'none';
    radialControls.style.display = type === 'radial' ? '' : 'none';
    conicControls.style.display  = type === 'conic'  ? '' : 'none';
  }

  function syncPosGrid(pos) {
    document.querySelectorAll('#gja-pos-grid .gja-pos-dot').forEach(function(dot) {
      dot.classList.toggle('gja-pos-active', dot.dataset.pos === pos);
    });
  }

  // ---- Random gradient ----
  var RANDOM_COLORS = [
    '#f093fb','#f5576c','#4facfe','#00f2fe','#43e97b','#38f9d7',
    '#fa709a','#fee140','#a18cd1','#fbc2eb','#ffecd2','#fcb69f',
    '#a1c4fd','#c2e9fb','#d4fc79','#96e6a1','#f7971e','#ffd200',
    '#e0c3fc','#8ec5fc','#fddb92','#d1fdff','#0f0c29','#24243e',
    '#11998e','#38ef7d','#6a3093','#a044ff','#667eea','#764ba2'
  ];

  function randomColor() {
    return RANDOM_COLORS[Math.floor(Math.random() * RANDOM_COLORS.length)];
  }

  function randomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  randomBtn.addEventListener('click', function() {
    var count = randomInt(2, 4);
    var positions = [0];
    for (var i = 1; i < count - 1; i++) {
      positions.push(randomInt(20, 80));
    }
    positions.push(100);
    positions.sort(function(a,b){return a-b;});

    state.stops = positions.map(function(p) {
      return { color: randomColor(), pos: p };
    });

    var types = ['linear', 'radial', 'conic'];
    state.type = types[randomInt(0, 2)];
    state.angle = randomInt(0, 360);
    state.conicAngle = randomInt(0, 360);
    state.radialShape = Math.random() > 0.5 ? 'circle' : 'ellipse';

    angleSlider.value = state.angle;
    angleNum.value = state.angle;
    conicSlider.value = state.conicAngle;
    conicNum.value = state.conicAngle;
    radialShape.value = state.radialShape;

    document.querySelectorAll('#grad-app-ja .gja-type-btn').forEach(function(btn) {
      btn.classList.toggle('gja-active', btn.dataset.type === state.type);
    });
    showTypeControls(state.type);
    document.querySelectorAll('#grad-app-ja .gja-preset-item').forEach(function(el) {
      el.classList.remove('gja-preset-active');
    });
    activePreset = null;
    render();
  });

  // ---- Type buttons ----
  document.querySelectorAll('#grad-app-ja .gja-type-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      state.type = btn.dataset.type;
      document.querySelectorAll('#grad-app-ja .gja-type-btn').forEach(function(b) {
        b.classList.remove('gja-active');
      });
      btn.classList.add('gja-active');
      showTypeControls(state.type);
      render();
    });
  });

  // ---- Angle sliders ----
  angleSlider.addEventListener('input', function() {
    state.angle = parseInt(angleSlider.value);
    angleNum.value = state.angle;
    render();
  });

  angleNum.addEventListener('input', function() {
    state.angle = Math.max(0, Math.min(360, parseInt(angleNum.value) || 0));
    angleSlider.value = state.angle;
    render();
  });

  conicSlider.addEventListener('input', function() {
    state.conicAngle = parseInt(conicSlider.value);
    conicNum.value = state.conicAngle;
    render();
  });

  conicNum.addEventListener('input', function() {
    state.conicAngle = Math.max(0, Math.min(360, parseInt(conicNum.value) || 0));
    conicSlider.value = state.conicAngle;
    render();
  });

  // ---- Radial controls ----
  radialShape.addEventListener('change', function() {
    state.radialShape = radialShape.value;
    render();
  });

  document.querySelectorAll('#gja-pos-grid .gja-pos-dot').forEach(function(dot) {
    dot.addEventListener('click', function() {
      state.radialPos = dot.dataset.pos;
      syncPosGrid(state.radialPos);
      render();
    });
  });

  // ---- Add stop ----
  addStopBtn.addEventListener('click', function() {
    if (state.stops.length >= 5) return;
    var lastPos = state.stops[state.stops.length - 1].pos;
    var newPos = Math.min(100, lastPos + Math.round((100 - lastPos) / 2));
    state.stops.push({ color: randomColor(), pos: newPos });
    render();
  });

  // ---- Copy CSS ----
  function doCopy(text, btn) {
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() { flashCopied(btn); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.cssText = 'position:fixed;opacity:0;';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      flashCopied(btn);
    }
  }

  function flashCopied(btn) {
    var orig = btn.textContent;
    btn.classList.add('gja-copied');
    btn.textContent = 'コピーしました!';
    setTimeout(function() {
      btn.classList.remove('gja-copied');
      btn.textContent = orig;
    }, 1600);
  }

  cssCopyBtn.addEventListener('click', function() {
    doCopy(buildFullCSS(), cssCopyBtn);
  });

  copyCssMainBtn.addEventListener('click', function() {
    doCopy(buildFullCSS(), copyCssMainBtn);
  });

  // ---- Init ----
  renderPresets();
  render();

})();
</script>

</div>

## CSSグラデーションジェネレーターの使い方

**グラデーションの種類を選ぶ** — リニア（直線）・放射状・コニック（扇形）の3種類から選択できます。

**リニアグラデーション**は角度スライダーで方向を指定します。0°は下から上、90°は左から右、135°は斜め方向です。

**放射状グラデーション**は形状（円形・楕円形）と中心位置（9マスのグリッドで選択）を指定します。

**コニックグラデーション**は開始角度を指定します。色が時計回りに扇状に広がります。

**カラーストップ**はカラースウォッチをクリックしてカラーピッカーを開くか、HEXコードを直接入力して設定します。位置スライダーで各色の開始位置（0〜100%）を調整できます。最大5つまで追加可能、×ボタンで削除できます（最低2つは必須）。

**プリセット**をクリックするとすぐに適用されます。夕焼け・海・森林・ネオン・桜・抹茶など12種類以上を収録。

**ランダム生成**ボタンで予想外の美しいグラデーションが生成されます。インスピレーション探しに最適です。

**CSSをコピー**ボタンを押すと、`-webkit-` プレフィックス付きのCSSコードをクリップボードにコピーします。そのままHTMLやCSSファイルに貼り付けるだけで使えます。

## CSSグラデーション構文リファレンス

**リニアグラデーション**の基本構文：
```
background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
```

**放射状グラデーション**の基本構文：
```
background: radial-gradient(ellipse at center, #a8edea 0%, #fed6e3 100%);
```

**コニックグラデーション**の基本構文：
```
background: conic-gradient(from 0deg, #6a3093 0%, #a044ff 50%, #6a3093 100%);
```

複数のカラーストップを使うことで、虹色・三色旗・グラデーションボーダーなど多彩な表現が可能になります。ストップ位置を同じ値に設定すると、ぼかしのない鮮明な色の境界線を作れます。

---

**デザイン業務の会計管理にはfreee**
デザイン制作をしている方、経費精算もfreeeで一括管理しませんか？
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>

---

## 関連ツール

> Box Shadow Generator → [Box Shadow Generatorツール](/ja/tools/box-shadow-generator/)
> Css Animation Generator → [Css Animation Generatorツール](/ja/tools/css-animation-generator/)
> Css Button Generator → [Css Button Generatorツール](/ja/tools/css-button-generator/)

