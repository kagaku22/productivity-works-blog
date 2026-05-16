---
title: "CSS Gradient Generator - Free Online Tool for Linear, Radial & Conic Gradients"
date: 2025-05-16
description: "Create beautiful CSS gradients online. Supports linear, radial, and conic gradient types with up to 5 color stops, 12+ presets, angle control, and instant CSS code output. Free, no login required."
categories: ["Free Tools"]
tags: ["css gradient", "gradient generator", "linear gradient", "radial gradient", "css tool", "web design"]
slug: "css-gradient-generator"
aliases: ["/tools/gradient-maker/", "/tools/gradient-generator/"]
cover:
  image: "/images/covers/css-gradient-generator.png"
  alt: "CSS Gradient Generator"
ShowToc: false
---

<div id="grad-app">

<style>
#grad-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 0 48px 0;
  color: #374151;
}

#grad-app * {
  box-sizing: border-box;
}

/* Preview */
.ga-preview-wrap {
  border-radius: 16px;
  overflow: hidden;
  margin-bottom: 20px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.15);
  position: relative;
}

.ga-preview {
  width: 100%;
  height: 320px;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  transition: background 0.2s;
}

.ga-preview-label {
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
.ga-card {
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 2px 16px rgba(0,0,0,0.07);
  padding: 22px 24px;
  margin-bottom: 16px;
}

.ga-card-title {
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
.ga-type-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.ga-type-btn {
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

.ga-type-btn:hover {
  border-color: #9ca3af;
  background: #f3f4f6;
}

.ga-type-btn.ga-active {
  border-color: #374151;
  background: #374151;
  color: #fff;
}

/* Linear angle */
.ga-angle-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-top: 14px;
}

.ga-angle-label {
  font-size: 13px;
  font-weight: 600;
  color: #6b7280;
  white-space: nowrap;
  width: 110px;
  flex-shrink: 0;
}

.ga-angle-slider {
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

.ga-angle-slider::-webkit-slider-thumb {
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

.ga-angle-slider::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #374151;
  border: 3px solid #fff;
  box-shadow: 0 1px 6px rgba(0,0,0,0.25);
  cursor: pointer;
}

.ga-angle-num {
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

.ga-angle-num:focus {
  outline: none;
  border-color: #374151;
}

/* Radial options */
.ga-radial-row {
  display: flex;
  gap: 16px;
  margin-top: 14px;
  flex-wrap: wrap;
  align-items: flex-start;
}

.ga-radial-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.ga-field-label {
  font-size: 12px;
  font-weight: 700;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.ga-select {
  padding: 8px 12px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  font-size: 13px;
  color: #374151;
  background: #fff;
  cursor: pointer;
  font-weight: 600;
}

.ga-select:focus {
  outline: none;
  border-color: #374151;
}

/* Position grid */
.ga-pos-grid {
  display: grid;
  grid-template-columns: repeat(3, 32px);
  gap: 4px;
}

.ga-pos-dot {
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

.ga-pos-dot:hover {
  border-color: #9ca3af;
  background: #f3f4f6;
}

.ga-pos-dot.ga-pos-active {
  border-color: #374151;
  background: #374151;
  color: #fff;
}

/* Color stops */
.ga-stops-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 14px;
}

.ga-stop-row {
  display: flex;
  align-items: center;
  gap: 10px;
}

.ga-stop-swatch {
  width: 38px;
  height: 38px;
  border-radius: 10px;
  border: 2px solid #e5e7eb;
  cursor: pointer;
  padding: 2px;
  flex-shrink: 0;
}

.ga-stop-hex {
  flex: 1;
  min-width: 0;
  padding: 8px 10px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  font-size: 13px;
  font-family: 'Courier New', monospace;
  color: #374151;
  max-width: 100px;
}

.ga-stop-hex:focus {
  outline: none;
  border-color: #374151;
}

.ga-stop-pos-wrap {
  display: flex;
  align-items: center;
  gap: 6px;
  flex: 1;
  min-width: 0;
}

.ga-stop-pos-label {
  font-size: 12px;
  color: #6b7280;
  font-weight: 600;
  white-space: nowrap;
  width: 26px;
  flex-shrink: 0;
}

.ga-stop-pos-slider {
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

.ga-stop-pos-slider::-webkit-slider-thumb {
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

.ga-stop-pos-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #374151;
  border: 2px solid #fff;
  box-shadow: 0 1px 4px rgba(0,0,0,0.2);
  cursor: pointer;
}

.ga-stop-pos-num {
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

.ga-stop-pos-num:focus {
  outline: none;
  border-color: #374151;
}

.ga-stop-remove {
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

.ga-stop-remove:hover {
  border-color: #ef4444;
  color: #ef4444;
  background: #fef2f2;
}

/* Gradient bar */
.ga-gradient-bar {
  height: 18px;
  border-radius: 9px;
  margin-bottom: 14px;
  box-shadow: inset 0 1px 4px rgba(0,0,0,0.12);
}

/* Add stop button */
.ga-add-stop-btn {
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

.ga-add-stop-btn:hover {
  border-color: #374151;
  color: #374151;
  background: #f3f4f6;
}

/* Presets */
.ga-presets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
  gap: 10px;
}

.ga-preset-item {
  border-radius: 12px;
  overflow: hidden;
  cursor: pointer;
  border: 2px solid transparent;
  transition: all 0.18s;
  box-shadow: 0 1px 6px rgba(0,0,0,0.1);
}

.ga-preset-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(0,0,0,0.18);
}

.ga-preset-item.ga-preset-active {
  border-color: #374151;
}

.ga-preset-swatch {
  height: 52px;
  width: 100%;
}

.ga-preset-name {
  background: #fff;
  padding: 5px 8px;
  font-size: 11px;
  font-weight: 600;
  color: #374151;
  text-align: center;
  border-top: 1px solid #f3f4f6;
}

/* Action buttons */
.ga-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

.ga-btn {
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.18s;
  letter-spacing: 0.02em;
}

.ga-btn-primary {
  background: #374151;
  color: #fff;
}

.ga-btn-primary:hover {
  background: #1f2937;
}

.ga-btn-secondary {
  background: #f3f4f6;
  color: #374151;
  border: 2px solid #e5e7eb;
}

.ga-btn-secondary:hover {
  background: #e5e7eb;
}

/* CSS output */
.ga-css-output {
  background: #1a1b2e;
  border-radius: 12px;
  padding: 20px 22px;
  position: relative;
  font-family: 'Courier New', monospace;
  font-size: 13px;
  line-height: 1.9;
  color: #a5b4fc;
}

.ga-css-prop { color: #7dd3fc; }
.ga-css-val  { color: #fde68a; }
.ga-css-semi { color: #94a3b8; }

.ga-css-copy-btn {
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

.ga-css-copy-btn:hover {
  background: rgba(255,255,255,0.16);
}

.ga-css-copy-btn.ga-copied {
  background: rgba(52,211,153,0.2);
  color: #6ee7b7;
  border-color: rgba(52,211,153,0.3);
}

/* Responsive */
@media (max-width: 600px) {
  .ga-preview { height: 220px; }
  .ga-card { padding: 16px 14px; }
  .ga-presets-grid { grid-template-columns: repeat(auto-fill, minmax(90px, 1fr)); }
  .ga-stop-row { flex-wrap: wrap; }
  .ga-stop-hex { max-width: 90px; }
  .ga-angle-label { width: 80px; font-size: 12px; }
  .ga-actions { flex-direction: column; }
  .ga-btn { text-align: center; }
}
</style>

<!-- Preview -->
<div class="ga-preview-wrap">
  <div class="ga-preview" id="ga-preview"></div>
  <div class="ga-preview-label" id="ga-preview-label">linear-gradient(135deg, ...)</div>
</div>

<!-- Actions -->
<div class="ga-actions">
  <button class="ga-btn ga-btn-primary" id="ga-random-btn">Random Gradient</button>
  <button class="ga-btn ga-btn-secondary" id="ga-copy-css-main-btn">Copy CSS</button>
</div>

<!-- Gradient Type -->
<div class="ga-card">
  <div class="ga-card-title">Gradient Type</div>
  <div class="ga-type-row">
    <button class="ga-type-btn ga-active" data-type="linear">Linear</button>
    <button class="ga-type-btn" data-type="radial">Radial</button>
    <button class="ga-type-btn" data-type="conic">Conic</button>
  </div>

  <!-- Linear controls -->
  <div id="ga-linear-controls">
    <div class="ga-angle-row">
      <span class="ga-angle-label">Angle</span>
      <input type="range" class="ga-angle-slider" id="ga-angle-slider" min="0" max="360" value="135">
      <input type="number" class="ga-angle-num" id="ga-angle-num" min="0" max="360" value="135"> °
    </div>
  </div>

  <!-- Radial controls -->
  <div id="ga-radial-controls" style="display:none;">
    <div class="ga-radial-row">
      <div class="ga-radial-field">
        <span class="ga-field-label">Shape</span>
        <select class="ga-select" id="ga-radial-shape">
          <option value="circle">Circle</option>
          <option value="ellipse" selected>Ellipse</option>
        </select>
      </div>
      <div class="ga-radial-field">
        <span class="ga-field-label">Position</span>
        <div class="ga-pos-grid" id="ga-pos-grid">
          <div class="ga-pos-dot" data-pos="left top" title="top left">↖</div>
          <div class="ga-pos-dot" data-pos="center top" title="top">↑</div>
          <div class="ga-pos-dot" data-pos="right top" title="top right">↗</div>
          <div class="ga-pos-dot" data-pos="left center" title="left">←</div>
          <div class="ga-pos-dot ga-pos-active" data-pos="center center" title="center">·</div>
          <div class="ga-pos-dot" data-pos="right center" title="right">→</div>
          <div class="ga-pos-dot" data-pos="left bottom" title="bottom left">↙</div>
          <div class="ga-pos-dot" data-pos="center bottom" title="bottom">↓</div>
          <div class="ga-pos-dot" data-pos="right bottom" title="bottom right">↘</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Conic controls -->
  <div id="ga-conic-controls" style="display:none;">
    <div class="ga-angle-row">
      <span class="ga-angle-label">From Angle</span>
      <input type="range" class="ga-angle-slider" id="ga-conic-angle-slider" min="0" max="360" value="0">
      <input type="number" class="ga-angle-num" id="ga-conic-angle-num" min="0" max="360" value="0"> °
    </div>
  </div>
</div>

<!-- Color Stops -->
<div class="ga-card">
  <div class="ga-card-title">Color Stops</div>
  <div class="ga-gradient-bar" id="ga-gradient-bar"></div>
  <div class="ga-stops-list" id="ga-stops-list"></div>
  <button class="ga-add-stop-btn" id="ga-add-stop-btn">+ Add Color Stop</button>
</div>

<!-- Presets -->
<div class="ga-card">
  <div class="ga-card-title">Presets</div>
  <div class="ga-presets-grid" id="ga-presets-grid"></div>
</div>

<!-- CSS Output -->
<div class="ga-card">
  <div class="ga-card-title">CSS Code</div>
  <div class="ga-css-output" id="ga-css-output">
    <button class="ga-css-copy-btn" id="ga-css-copy-btn">Copy</button>
    <div id="ga-css-code"></div>
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
      { color: '#f093fb', pos: 0 },
      { color: '#f5576c', pos: 100 }
    ]
  };

  var activePreset = null;

  // ---- Presets ----
  var PRESETS = [
    { name: 'Sunset',       type: 'linear', angle: 135, stops: [{ color: '#f093fb', pos: 0 }, { color: '#f5576c', pos: 100 }] },
    { name: 'Ocean',        type: 'linear', angle: 160, stops: [{ color: '#2980b9', pos: 0 }, { color: '#6dd5fa', pos: 50 }, { color: '#ffffff', pos: 100 }] },
    { name: 'Forest',       type: 'linear', angle: 120, stops: [{ color: '#11998e', pos: 0 }, { color: '#38ef7d', pos: 100 }] },
    { name: 'Neon',         type: 'linear', angle: 90,  stops: [{ color: '#f7971e', pos: 0 }, { color: '#ffd200', pos: 50 }, { color: '#21d4fd', pos: 100 }] },
    { name: 'Aurora',       type: 'linear', angle: 135, stops: [{ color: '#a8edea', pos: 0 }, { color: '#fed6e3', pos: 100 }] },
    { name: 'Midnight',     type: 'linear', angle: 180, stops: [{ color: '#0f0c29', pos: 0 }, { color: '#302b63', pos: 50 }, { color: '#24243e', pos: 100 }] },
    { name: 'Peach',        type: 'linear', angle: 45,  stops: [{ color: '#ffecd2', pos: 0 }, { color: '#fcb69f', pos: 100 }] },
    { name: 'Lavender',     type: 'linear', angle: 135, stops: [{ color: '#e0c3fc', pos: 0 }, { color: '#8ec5fc', pos: 100 }] },
    { name: 'Fire',         type: 'linear', angle: 90,  stops: [{ color: '#f83600', pos: 0 }, { color: '#f9d423', pos: 100 }] },
    { name: 'Cotton Candy', type: 'radial', shape: 'ellipse', pos: 'center center', stops: [{ color: '#fddb92', pos: 0 }, { color: '#d1fdff', pos: 100 }] },
    { name: 'Cosmic',       type: 'conic',  conicAngle: 0, stops: [{ color: '#6a3093', pos: 0 }, { color: '#a044ff', pos: 33 }, { color: '#6a3093', pos: 66 }, { color: '#a044ff', pos: 100 }] },
    { name: 'Mango',        type: 'linear', angle: 135, stops: [{ color: '#ffe259', pos: 0 }, { color: '#ffa751', pos: 100 }] }
  ];

  // ---- DOM refs ----
  var previewEl       = document.getElementById('ga-preview');
  var previewLabel    = document.getElementById('ga-preview-label');
  var gradientBar     = document.getElementById('ga-gradient-bar');
  var stopsList       = document.getElementById('ga-stops-list');
  var addStopBtn      = document.getElementById('ga-add-stop-btn');
  var presetsGrid     = document.getElementById('ga-presets-grid');
  var cssCode         = document.getElementById('ga-css-code');
  var cssCopyBtn      = document.getElementById('ga-css-copy-btn');
  var copyCssMainBtn  = document.getElementById('ga-copy-css-main-btn');
  var randomBtn       = document.getElementById('ga-random-btn');
  var angleSlider     = document.getElementById('ga-angle-slider');
  var angleNum        = document.getElementById('ga-angle-num');
  var conicSlider     = document.getElementById('ga-conic-angle-slider');
  var conicNum        = document.getElementById('ga-conic-angle-num');
  var radialShape     = document.getElementById('ga-radial-shape');
  var linearControls  = document.getElementById('ga-linear-controls');
  var radialControls  = document.getElementById('ga-radial-controls');
  var conicControls   = document.getElementById('ga-conic-controls');

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
      '<span class="ga-css-prop">background</span><span class="ga-css-semi">: </span>' +
      '<span class="ga-css-val">-webkit-' + escHtml(grad) + '</span><span class="ga-css-semi">;</span>\n' +
      '<span class="ga-css-prop">background</span><span class="ga-css-semi">: </span>' +
      '<span class="ga-css-val">' + escHtml(grad) + '</span><span class="ga-css-semi">;</span>';
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function renderStops() {
    stopsList.innerHTML = '';
    state.stops.forEach(function(stop, idx) {
      var row = document.createElement('div');
      row.className = 'ga-stop-row';

      // Color swatch (native color input)
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
      hexField.className = 'ga-stop-hex';
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

      // Position slider + num
      var posWrap = document.createElement('div');
      posWrap.className = 'ga-stop-pos-wrap';

      var posLabel = document.createElement('span');
      posLabel.className = 'ga-stop-pos-label';
      posLabel.textContent = 'Pos';

      var posSlider = document.createElement('input');
      posSlider.type = 'range';
      posSlider.className = 'ga-stop-pos-slider';
      posSlider.min = 0;
      posSlider.max = 100;
      posSlider.value = stop.pos;

      var posNum = document.createElement('input');
      posNum.type = 'number';
      posNum.className = 'ga-stop-pos-num';
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
      removeBtn.className = 'ga-stop-remove';
      removeBtn.textContent = '×';
      removeBtn.title = 'Remove stop';
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
      item.className = 'ga-preset-item';
      item.dataset.idx = idx;

      var swatch = document.createElement('div');
      swatch.className = 'ga-preset-swatch';

      // Build gradient for swatch
      var stops = preset.stops.map(function(s) { return s.color + ' ' + s.pos + '%'; }).join(', ');
      var grad;
      if (preset.type === 'radial') {
        grad = 'radial-gradient(ellipse at center center, ' + stops + ')';
      } else if (preset.type === 'conic') {
        grad = 'linear-gradient(135deg, ' + stops + ')'; // approximate for thumbnail
      } else {
        grad = 'linear-gradient(' + preset.angle + 'deg, ' + stops + ')';
      }
      swatch.style.background = grad;

      var nameEl = document.createElement('div');
      nameEl.className = 'ga-preset-name';
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

    // Type buttons
    document.querySelectorAll('#grad-app .ga-type-btn').forEach(function(btn) {
      btn.classList.toggle('ga-active', btn.dataset.type === state.type);
    });
    showTypeControls(state.type);

    // Preset active highlight
    document.querySelectorAll('#grad-app .ga-preset-item').forEach(function(el, i) {
      el.classList.toggle('ga-preset-active', i === idx);
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
    document.querySelectorAll('#ga-pos-grid .ga-pos-dot').forEach(function(dot) {
      dot.classList.toggle('ga-pos-active', dot.dataset.pos === pos);
    });
  }

  // ---- Random gradient ----
  var RANDOM_COLORS = [
    '#f093fb','#f5576c','#4facfe','#00f2fe','#43e97b','#38f9d7',
    '#fa709a','#fee140','#a18cd1','#fbc2eb','#ffecd2','#fcb69f',
    '#a1c4fd','#c2e9fb','#d4fc79','#96e6a1','#f7971e','#ffd200',
    '#e0c3fc','#8ec5fc','#fddb92','#d1fdff','#0f0c29','#24243e',
    '#11998e','#38ef7d','#6a3093','#a044ff'
  ];

  function randomColor() {
    return RANDOM_COLORS[Math.floor(Math.random() * RANDOM_COLORS.length)];
  }

  function randomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  randomBtn.addEventListener('click', function() {
    var count = randomInt(2, 4);
    var positions = [];
    positions.push(0);
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

    document.querySelectorAll('#grad-app .ga-type-btn').forEach(function(btn) {
      btn.classList.toggle('ga-active', btn.dataset.type === state.type);
    });
    showTypeControls(state.type);
    document.querySelectorAll('#grad-app .ga-preset-item').forEach(function(el) {
      el.classList.remove('ga-preset-active');
    });
    activePreset = null;
    render();
  });

  // ---- Type buttons ----
  document.querySelectorAll('#grad-app .ga-type-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      state.type = btn.dataset.type;
      document.querySelectorAll('#grad-app .ga-type-btn').forEach(function(b) {
        b.classList.remove('ga-active');
      });
      btn.classList.add('ga-active');
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

  document.querySelectorAll('#ga-pos-grid .ga-pos-dot').forEach(function(dot) {
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
    btn.classList.add('ga-copied');
    btn.textContent = 'Copied!';
    setTimeout(function() {
      btn.classList.remove('ga-copied');
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

## How to Use the CSS Gradient Generator

**Choose a gradient type** at the top: Linear gradients flow along a straight line at your chosen angle. Radial gradients expand outward from a center point in a circle or ellipse shape. Conic gradients sweep around a center point like a color wheel.

**Control the angle** with the slider (0–360°) or type a value directly. 0° is top-to-bottom, 90° is left-to-right, 135° is diagonal.

**Add color stops** using the color swatches (click to open the native color picker) or type a HEX code directly. Drag the position slider or type a percentage to set where each color starts. You can add up to 5 stops and remove any stop with the × button.

**Apply a preset** from the grid to get started instantly. Presets include Sunset, Ocean, Forest, Neon, Lavender, and more.

**Hit Random** for an instant surprise gradient — great for inspiration.

**Copy the CSS** with the Copy button. The output includes both the standard `background` property and the `-webkit-` prefixed version for maximum browser compatibility.

## CSS Gradient Syntax Reference

A **linear gradient** uses `linear-gradient(angle, color1 pos1, color2 pos2, ...)`. The angle is in degrees: `0deg` goes bottom to top, `90deg` goes left to right, `180deg` goes top to bottom.

A **radial gradient** uses `radial-gradient(shape size at position, colors...)`. Shape is `circle` or `ellipse`. Position can be keywords like `center`, `top left`, or percentage values.

A **conic gradient** uses `conic-gradient(from angle, colors...)`. Colors sweep around a point like a pie chart rather than radiating outward. Browser support is now excellent across modern browsers.

For smooth gradients, avoid placing two color stops at the same position unless you want a hard color edge. Spreading stops evenly (0%, 50%, 100%) creates the smoothest transitions.

---

Related: Pick perfect colors with our [Color Picker](/tools/color-picker/)
