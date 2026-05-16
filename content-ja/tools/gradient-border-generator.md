---
title: "CSSグラデーションボーダージェネレーター"
date: 2025-05-16
description: "無料のCSSグラデーションボーダー作成ツール。色・幅・角丸・方向をカスタマイズして美しいグラデーション枠線のCSSコードを即生成。"
categories: ["無料ツール"]
tags: ["cssグラデーションボーダー", "ボーダージェネレーター", "css枠線", "cssツール", "ウェブデザイン"]
slug: "gradient-border-generator"
cover:
  image: "/images/covers/gradient-border-generator-ja.png"
  alt: "CSSグラデーションボーダージェネレーター"
ShowToc: false
---

グラデーションボーダーを数秒で作成。色・方向・幅・角丸を自由にカスタマイズして、すぐに使えるCSSコードをコピーできます。外部ライブラリ不要・登録不要。

<div id="gb-app">

<style>
#gb-app *,
#gb-app *::before,
#gb-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#gb-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
  max-width: 880px;
  margin: 0 auto;
  padding: 0 0 56px;
  color: #1f2937;
}

/* ── Preview ────────────────────────────────────────── */
.gb-preview-wrap {
  background: repeating-conic-gradient(#e5e7eb 0% 25%, #fff 0% 50%) 0 0 / 20px 20px;
  border-radius: 16px;
  padding: 48px 32px;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 220px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.10);
}
.gb-preview-box {
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 15px;
  color: #6b7280;
  font-weight: 500;
  min-width: 200px;
  min-height: 100px;
  transition: all 0.2s;
  word-break: break-all;
}

/* ── Cards ──────────────────────────────────────────── */
.gb-card {
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 2px 16px rgba(0,0,0,0.07);
  padding: 22px 24px;
  margin-bottom: 16px;
}
.gb-card-title {
  font-size: 12px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  border-bottom: 2px solid #f3f4f6;
  padding-bottom: 10px;
  margin-bottom: 18px;
}

/* ── Color Stops ─────────────────────────────────────── */
.gb-stops-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 14px;
}
.gb-stop-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
.gb-color-swatch {
  width: 38px;
  height: 38px;
  border-radius: 8px;
  border: 2px solid #e5e7eb;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  flex-shrink: 0;
}
.gb-color-swatch input[type="color"] {
  position: absolute;
  inset: -4px;
  width: calc(100% + 8px);
  height: calc(100% + 8px);
  opacity: 0;
  cursor: pointer;
}
.gb-color-hex {
  width: 88px;
  padding: 7px 10px;
  border: 1.5px solid #e5e7eb;
  border-radius: 8px;
  font-size: 13px;
  font-family: 'Menlo', 'Consolas', monospace;
  color: #374151;
  outline: none;
  transition: border-color 0.15s;
}
.gb-color-hex:focus { border-color: #6366f1; }
.gb-stop-label {
  font-size: 12px;
  color: #9ca3af;
  width: 32px;
  text-align: center;
  flex-shrink: 0;
}
.gb-stop-percent {
  flex: 1;
  accent-color: #6366f1;
}
.gb-stop-pct-val {
  font-size: 12px;
  color: #6b7280;
  width: 34px;
  text-align: right;
  flex-shrink: 0;
}
.gb-stop-remove {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  border: none;
  background: #fee2e2;
  color: #ef4444;
  font-size: 16px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  transition: background 0.15s;
  line-height: 1;
}
.gb-stop-remove:hover { background: #fecaca; }
.gb-stop-remove:disabled { opacity: 0.3; cursor: default; }
.gb-add-stop-btn {
  padding: 8px 18px;
  border-radius: 8px;
  border: 1.5px dashed #c7d2fe;
  background: #eef2ff;
  color: #6366f1;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
.gb-add-stop-btn:hover { background: #e0e7ff; }
.gb-add-stop-btn:disabled { opacity: 0.4; cursor: default; }

/* ── Direction ───────────────────────────────────────── */
.gb-dir-row {
  display: flex;
  align-items: center;
  gap: 14px;
  flex-wrap: wrap;
}
.gb-dir-presets {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}
.gb-dir-btn {
  padding: 6px 12px;
  border-radius: 7px;
  border: 1.5px solid #e5e7eb;
  background: #f9fafb;
  color: #374151;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
.gb-dir-btn:hover { border-color: #a5b4fc; background: #eef2ff; }
.gb-dir-btn.gb-active { border-color: #6366f1; background: #eef2ff; color: #4f46e5; }
.gb-angle-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 14px;
}
.gb-angle-label { font-size: 13px; color: #6b7280; flex-shrink: 0; }
.gb-angle-slider { flex: 1; accent-color: #6366f1; }
.gb-angle-num {
  width: 60px;
  padding: 6px 8px;
  border: 1.5px solid #e5e7eb;
  border-radius: 7px;
  font-size: 13px;
  text-align: center;
  outline: none;
}
.gb-angle-num:focus { border-color: #6366f1; }
.gb-angle-deg { font-size: 13px; color: #9ca3af; }

/* ── Sliders ─────────────────────────────────────────── */
.gb-slider-row {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 14px;
}
.gb-slider-row:last-child { margin-bottom: 0; }
.gb-slider-label {
  font-size: 13px;
  color: #374151;
  width: 110px;
  flex-shrink: 0;
}
.gb-slider {
  flex: 1;
  accent-color: #6366f1;
}
.gb-slider-val {
  font-size: 13px;
  color: #6b7280;
  width: 44px;
  text-align: right;
  flex-shrink: 0;
  font-variant-numeric: tabular-nums;
}

/* ── Technique Toggle ────────────────────────────────── */
.gb-tech-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}
.gb-tech-btn {
  padding: 7px 16px;
  border-radius: 8px;
  border: 1.5px solid #e5e7eb;
  background: #f9fafb;
  color: #374151;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
.gb-tech-btn:hover { border-color: #a5b4fc; }
.gb-tech-btn.gb-active { border-color: #6366f1; background: #eef2ff; color: #4f46e5; }
.gb-tech-note {
  font-size: 12px;
  color: #9ca3af;
  margin-top: 10px;
  line-height: 1.5;
}

/* ── Presets ─────────────────────────────────────────── */
.gb-presets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
  gap: 10px;
}
.gb-preset-item {
  border-radius: 10px;
  height: 52px;
  cursor: pointer;
  border: 3px solid transparent;
  transition: all 0.15s;
  position: relative;
  overflow: hidden;
}
.gb-preset-item:hover { transform: scale(1.06); box-shadow: 0 4px 12px rgba(0,0,0,0.15); }
.gb-preset-item.gb-active { border-color: #6366f1; }
.gb-preset-label {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  background: rgba(0,0,0,0.45);
  color: #fff;
  font-size: 9px;
  text-align: center;
  padding: 2px 4px;
}

/* ── CSS Output ──────────────────────────────────────── */
.gb-output-wrap {
  position: relative;
}
.gb-output-code {
  display: block;
  background: #1e1e2e;
  color: #cdd6f4;
  border-radius: 10px;
  padding: 18px 20px;
  font-family: 'Menlo', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.7;
  white-space: pre-wrap;
  word-break: break-all;
  min-height: 80px;
  user-select: all;
}
.gb-copy-btn {
  margin-top: 12px;
  padding: 11px 28px;
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  color: #fff;
  border: none;
  border-radius: 9px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  width: 100%;
}
.gb-copy-btn:hover { opacity: 0.9; transform: translateY(-1px); }
.gb-copy-btn.gb-copied { background: linear-gradient(135deg, #10b981, #059669); }

/* ── Related Links ───────────────────────────────────── */
.gb-related {
  margin-top: 28px;
  padding-top: 22px;
  border-top: 2px solid #f3f4f6;
}
.gb-related-title {
  font-size: 13px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin-bottom: 12px;
}
.gb-related-links {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}
.gb-related-links a {
  padding: 7px 14px;
  background: #f3f4f6;
  border-radius: 7px;
  font-size: 13px;
  color: #4f46e5;
  text-decoration: none;
  font-weight: 500;
  transition: background 0.15s;
}
.gb-related-links a:hover { background: #e0e7ff; }
</style>

<!-- Preview -->
<div class="gb-preview-wrap">
  <div class="gb-preview-box" id="gb-preview">プレビュー</div>
</div>

<!-- Color Stops -->
<div class="gb-card">
  <div class="gb-card-title">カラーストップ</div>
  <div class="gb-stops-list" id="gb-stops-list"></div>
  <button class="gb-add-stop-btn" id="gb-add-stop">＋ カラーストップを追加</button>
</div>

<!-- Direction -->
<div class="gb-card">
  <div class="gb-card-title">グラデーションの方向</div>
  <div class="gb-dir-row">
    <div class="gb-dir-presets" id="gb-dir-presets">
      <button class="gb-dir-btn" data-angle="0">↑ 0°</button>
      <button class="gb-dir-btn" data-angle="45">↗ 45°</button>
      <button class="gb-dir-btn gb-active" data-angle="90">→ 90°</button>
      <button class="gb-dir-btn" data-angle="135">↘ 135°</button>
      <button class="gb-dir-btn" data-angle="180">↓ 180°</button>
      <button class="gb-dir-btn" data-angle="225">↙ 225°</button>
      <button class="gb-dir-btn" data-angle="270">← 270°</button>
      <button class="gb-dir-btn" data-angle="315">↖ 315°</button>
    </div>
  </div>
  <div class="gb-angle-row">
    <span class="gb-angle-label">カスタム角度</span>
    <input type="range" class="gb-angle-slider" id="gb-angle-slider" min="0" max="360" value="90">
    <input type="number" class="gb-angle-num" id="gb-angle-num" min="0" max="360" value="90">
    <span class="gb-angle-deg">°</span>
  </div>
</div>

<!-- Border Controls -->
<div class="gb-card">
  <div class="gb-card-title">ボーダー設定</div>
  <div class="gb-slider-row">
    <span class="gb-slider-label">ボーダー幅</span>
    <input type="range" class="gb-slider" id="gb-border-width" min="1" max="10" value="3">
    <span class="gb-slider-val" id="gb-border-width-val">3px</span>
  </div>
  <div class="gb-slider-row">
    <span class="gb-slider-label">角丸（radius）</span>
    <input type="range" class="gb-slider" id="gb-border-radius" min="0" max="50" value="12">
    <span class="gb-slider-val" id="gb-border-radius-val">12px</span>
  </div>
  <div class="gb-slider-row">
    <span class="gb-slider-label">パディング</span>
    <input type="range" class="gb-slider" id="gb-padding" min="8" max="48" value="20">
    <span class="gb-slider-val" id="gb-padding-val">20px</span>
  </div>
</div>

<!-- Technique -->
<div class="gb-card">
  <div class="gb-card-title">CSSの実装方法</div>
  <div class="gb-tech-row" id="gb-tech-row">
    <button class="gb-tech-btn gb-active" data-tech="background-clip">background-clip（推奨）</button>
    <button class="gb-tech-btn" data-tech="border-image">border-image</button>
  </div>
  <p class="gb-tech-note" id="gb-tech-note"><code>background-clip: padding-box</code> を使用。角丸（border-radius）対応で全ブラウザで動作します。</p>
</div>

<!-- Presets -->
<div class="gb-card">
  <div class="gb-card-title">プリセット</div>
  <div class="gb-presets-grid" id="gb-presets-grid"></div>
</div>

<!-- CSS Output -->
<div class="gb-card">
  <div class="gb-card-title">生成されたCSS</div>
  <div class="gb-output-wrap">
    <code class="gb-output-code" id="gb-output-code"></code>
  </div>
  <button class="gb-copy-btn" id="gb-copy-btn">CSSをコピー</button>
</div>

<!-- Related -->
<div class="gb-related">
  <div class="gb-related-title">関連ツール</div>
  <div class="gb-related-links">
    <a href="/ja/tools/css-gradient-generator/">CSSグラデーションジェネレーター</a>
    <a href="/ja/tools/border-radius-generator/">ボーダーラジアスジェネレーター</a>
    <a href="/ja/tools/css-animation-generator/">CSSアニメーションジェネレーター</a>
  </div>
</div>

<script>
(function() {
  'use strict';

  // ── State ──────────────────────────────────────────────
  var state = {
    stops: [
      { color: '#6366f1', pct: 0 },
      { color: '#ec4899', pct: 100 }
    ],
    angle: 90,
    borderWidth: 3,
    borderRadius: 12,
    padding: 20,
    technique: 'background-clip'
  };

  var PRESETS = [
    { name: 'インディゴ', stops: [{ color: '#6366f1', pct: 0 }, { color: '#ec4899', pct: 100 }], angle: 90 },
    { name: '夕焼け', stops: [{ color: '#f97316', pct: 0 }, { color: '#ef4444', pct: 50 }, { color: '#a855f7', pct: 100 }], angle: 135 },
    { name: '海', stops: [{ color: '#06b6d4', pct: 0 }, { color: '#3b82f6', pct: 100 }], angle: 180 },
    { name: 'オーロラ', stops: [{ color: '#10b981', pct: 0 }, { color: '#6366f1', pct: 50 }, { color: '#ec4899', pct: 100 }], angle: 45 },
    { name: 'ゴールド', stops: [{ color: '#f59e0b', pct: 0 }, { color: '#fbbf24', pct: 50 }, { color: '#d97706', pct: 100 }], angle: 90 },
    { name: 'ネオン', stops: [{ color: '#22d3ee', pct: 0 }, { color: '#a855f7', pct: 100 }], angle: 270 },
    { name: 'ローズ', stops: [{ color: '#fb7185', pct: 0 }, { color: '#f43f5e', pct: 100 }], angle: 135 },
    { name: 'ミント', stops: [{ color: '#34d399', pct: 0 }, { color: '#059669', pct: 100 }], angle: 90 },
    { name: 'ピーチ', stops: [{ color: '#fed7aa', pct: 0 }, { color: '#fb923c', pct: 100 }], angle: 180 },
    { name: '桜', stops: [{ color: '#f9a8d4', pct: 0 }, { color: '#c084fc', pct: 50 }, { color: '#818cf8', pct: 100 }], angle: 45 },
    { name: '夜空', stops: [{ color: '#1e1b4b', pct: 0 }, { color: '#312e81', pct: 50 }, { color: '#4338ca', pct: 100 }], angle: 135 },
    { name: '炎', stops: [{ color: '#fde68a', pct: 0 }, { color: '#f97316', pct: 50 }, { color: '#b91c1c', pct: 100 }], angle: 90 }
  ];

  var TECH_NOTES = {
    'background-clip': '<code>background-clip: padding-box</code> を使用。角丸（border-radius）対応で全ブラウザで動作します。',
    'border-image': '<code>border-image</code> を使用。シンプルな実装ですが <strong>border-radiusは非対応</strong>です。角丸が必要な場合はbackground-clipを使用してください。'
  };

  // ── DOM refs ───────────────────────────────────────────
  var stopsList    = document.getElementById('gb-stops-list');
  var addStopBtn   = document.getElementById('gb-add-stop');
  var dirPresets   = document.getElementById('gb-dir-presets');
  var angleSlider  = document.getElementById('gb-angle-slider');
  var angleNum     = document.getElementById('gb-angle-num');
  var bwSlider     = document.getElementById('gb-border-width');
  var bwVal        = document.getElementById('gb-border-width-val');
  var brSlider     = document.getElementById('gb-border-radius');
  var brVal        = document.getElementById('gb-border-radius-val');
  var padSlider    = document.getElementById('gb-padding');
  var padVal       = document.getElementById('gb-padding-val');
  var techRow      = document.getElementById('gb-tech-row');
  var techNote     = document.getElementById('gb-tech-note');
  var presetsGrid  = document.getElementById('gb-presets-grid');
  var outputCode   = document.getElementById('gb-output-code');
  var copyBtn      = document.getElementById('gb-copy-btn');
  var preview      = document.getElementById('gb-preview');

  // ── Helpers ────────────────────────────────────────────
  function gradientCSS() {
    var stops = state.stops.map(function(s) { return s.color + ' ' + s.pct + '%'; }).join(', ');
    return 'linear-gradient(' + state.angle + 'deg, ' + stops + ')';
  }

  function buildBackgroundClipCSS() {
    var grad = gradientCSS();
    var bw   = state.borderWidth;
    var br   = state.borderRadius;
    var pad  = state.padding;
    return [
      '.gradient-border {',
      '  padding: ' + pad + 'px;',
      '  background: ' + grad + ';',
      '  border-radius: ' + br + 'px;',
      '}',
      '',
      '.gradient-border-inner {',
      '  background: #fff;',
      '  border-radius: ' + Math.max(0, br - bw) + 'px;',
      '  padding: ' + bw + 'px;',
      '}'
    ].join('\n');
  }

  function buildBorderImageCSS() {
    var grad = gradientCSS();
    var bw   = state.borderWidth;
    var pad  = state.padding;
    return [
      '.gradient-border {',
      '  padding: ' + pad + 'px;',
      '  border: ' + bw + 'px solid transparent;',
      '  border-image: ' + grad + ' 1;',
      '}'
    ].join('\n');
  }

  function buildFullCSS() {
    if (state.technique === 'background-clip') return buildBackgroundClipCSS();
    return buildBorderImageCSS();
  }

  // ── Apply preview ──────────────────────────────────────
  function applyPreview() {
    var grad = gradientCSS();
    var bw   = state.borderWidth;
    var br   = state.borderRadius;
    var pad  = state.padding;

    if (state.technique === 'background-clip') {
      preview.style.cssText = [
        'padding:' + pad + 'px',
        'background:' + grad,
        'border-radius:' + br + 'px',
        'border:none',
        'display:flex',
        'align-items:center',
        'justify-content:center',
        'min-width:200px',
        'min-height:100px',
        'transition:all 0.2s'
      ].join(';');
      preview.innerHTML = '<div style="background:#fff;border-radius:' + Math.max(0, br - bw) + 'px;padding:' + bw + 'px;font-size:15px;color:#6b7280;font-weight:500;min-width:' + (160 - pad * 2) + 'px;min-height:' + (60 - pad * 2) + 'px;display:flex;align-items:center;justify-content:center;">プレビュー</div>';
    } else {
      preview.style.cssText = [
        'padding:' + pad + 'px',
        'border:' + bw + 'px solid transparent',
        'border-image:' + grad + ' 1',
        'border-radius:0',
        'background:#fff',
        'display:flex',
        'align-items:center',
        'justify-content:center',
        'min-width:200px',
        'min-height:100px',
        'font-size:15px',
        'color:#6b7280',
        'font-weight:500',
        'transition:all 0.2s'
      ].join(';');
      preview.textContent = 'プレビュー';
    }
  }

  // ── Render ─────────────────────────────────────────────
  function render() {
    renderStops();
    applyPreview();
    outputCode.textContent = buildFullCSS();
  }

  function renderStops() {
    stopsList.innerHTML = '';
    state.stops.forEach(function(stop, i) {
      var row = document.createElement('div');
      row.className = 'gb-stop-row';

      // Swatch
      var swatch = document.createElement('div');
      swatch.className = 'gb-color-swatch';
      swatch.style.background = stop.color;
      var picker = document.createElement('input');
      picker.type = 'color';
      picker.value = stop.color;
      picker.addEventListener('input', (function(idx) {
        return function() {
          state.stops[idx].color = this.value;
          hexInput.value = this.value;
          swatch.style.background = this.value;
          render();
        };
      })(i));
      swatch.appendChild(picker);

      // Hex input
      var hexInput = document.createElement('input');
      hexInput.type = 'text';
      hexInput.className = 'gb-color-hex';
      hexInput.value = stop.color;
      hexInput.maxLength = 7;
      hexInput.addEventListener('change', (function(idx) {
        return function() {
          var val = this.value.trim();
          if (!val.startsWith('#')) val = '#' + val;
          if (/^#[0-9a-fA-F]{6}$/.test(val)) {
            state.stops[idx].color = val;
            picker.value = val;
            swatch.style.background = val;
            render();
          }
        };
      })(i));

      // Position
      var label = document.createElement('span');
      label.className = 'gb-stop-label';
      label.textContent = '位置';

      var pctSlider = document.createElement('input');
      pctSlider.type = 'range';
      pctSlider.className = 'gb-stop-percent';
      pctSlider.min = 0;
      pctSlider.max = 100;
      pctSlider.value = stop.pct;
      pctSlider.addEventListener('input', (function(idx) {
        return function() {
          state.stops[idx].pct = parseInt(this.value);
          pctValSpan.textContent = this.value + '%';
          render();
        };
      })(i));

      var pctValSpan = document.createElement('span');
      pctValSpan.className = 'gb-stop-pct-val';
      pctValSpan.textContent = stop.pct + '%';

      // Remove
      var removeBtn = document.createElement('button');
      removeBtn.className = 'gb-stop-remove';
      removeBtn.innerHTML = '&times;';
      removeBtn.title = '削除';
      removeBtn.disabled = state.stops.length <= 2;
      removeBtn.addEventListener('click', (function(idx) {
        return function() {
          if (state.stops.length > 2) {
            state.stops.splice(idx, 1);
            render();
          }
        };
      })(i));

      row.appendChild(swatch);
      row.appendChild(hexInput);
      row.appendChild(label);
      row.appendChild(pctSlider);
      row.appendChild(pctValSpan);
      row.appendChild(removeBtn);
      stopsList.appendChild(row);
    });

    addStopBtn.disabled = state.stops.length >= 5;
  }

  // ── Presets grid ───────────────────────────────────────
  function renderPresets() {
    presetsGrid.innerHTML = '';
    PRESETS.forEach(function(p) {
      var stops = p.stops.map(function(s) { return s.color + ' ' + s.pct + '%'; }).join(', ');
      var grad  = 'linear-gradient(' + p.angle + 'deg, ' + stops + ')';
      var item  = document.createElement('div');
      item.className = 'gb-preset-item';
      item.style.background = grad;
      var lbl   = document.createElement('div');
      lbl.className = 'gb-preset-label';
      lbl.textContent = p.name;
      item.appendChild(lbl);
      item.addEventListener('click', function() {
        state.stops = p.stops.map(function(s) { return { color: s.color, pct: s.pct }; });
        state.angle = p.angle;
        angleSlider.value = p.angle;
        angleNum.value = p.angle;
        syncDirBtns();
        render();
      });
      presetsGrid.appendChild(item);
    });
  }

  // ── Direction buttons ──────────────────────────────────
  function syncDirBtns() {
    dirPresets.querySelectorAll('.gb-dir-btn').forEach(function(btn) {
      btn.classList.toggle('gb-active', parseInt(btn.dataset.angle) === state.angle);
    });
  }

  dirPresets.addEventListener('click', function(e) {
    var btn = e.target.closest('.gb-dir-btn');
    if (!btn) return;
    state.angle = parseInt(btn.dataset.angle);
    angleSlider.value = state.angle;
    angleNum.value = state.angle;
    syncDirBtns();
    render();
  });

  angleSlider.addEventListener('input', function() {
    state.angle = parseInt(this.value);
    angleNum.value = state.angle;
    syncDirBtns();
    render();
  });

  angleNum.addEventListener('change', function() {
    var v = Math.min(360, Math.max(0, parseInt(this.value) || 0));
    state.angle = v;
    this.value = v;
    angleSlider.value = v;
    syncDirBtns();
    render();
  });

  // ── Border controls ────────────────────────────────────
  bwSlider.addEventListener('input', function() {
    state.borderWidth = parseInt(this.value);
    bwVal.textContent = state.borderWidth + 'px';
    render();
  });

  brSlider.addEventListener('input', function() {
    state.borderRadius = parseInt(this.value);
    brVal.textContent = state.borderRadius + 'px';
    render();
  });

  padSlider.addEventListener('input', function() {
    state.padding = parseInt(this.value);
    padVal.textContent = state.padding + 'px';
    render();
  });

  // ── Technique toggle ───────────────────────────────────
  techRow.addEventListener('click', function(e) {
    var btn = e.target.closest('.gb-tech-btn');
    if (!btn) return;
    state.technique = btn.dataset.tech;
    techRow.querySelectorAll('.gb-tech-btn').forEach(function(b) {
      b.classList.toggle('gb-active', b.dataset.tech === state.technique);
    });
    techNote.innerHTML = TECH_NOTES[state.technique];
    render();
  });

  // ── Add stop ───────────────────────────────────────────
  addStopBtn.addEventListener('click', function() {
    if (state.stops.length >= 5) return;
    var colors = ['#a855f7', '#f59e0b', '#10b981', '#f43f5e', '#06b6d4'];
    var nextColor = colors[state.stops.length % colors.length];
    var lastPct = state.stops[state.stops.length - 1].pct;
    var newPct  = Math.min(100, lastPct + Math.round((100 - lastPct) / 2));
    state.stops.push({ color: nextColor, pct: newPct });
    render();
  });

  // ── Copy ───────────────────────────────────────────────
  copyBtn.addEventListener('click', function() {
    var text = buildFullCSS();
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() { flashCopied(); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.cssText = 'position:fixed;opacity:0;';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      flashCopied();
    }
  });

  function flashCopied() {
    copyBtn.classList.add('gb-copied');
    copyBtn.textContent = 'コピーしました！';
    setTimeout(function() {
      copyBtn.classList.remove('gb-copied');
      copyBtn.textContent = 'CSSをコピー';
    }, 1800);
  }

  // ── Init ───────────────────────────────────────────────
  renderPresets();
  syncDirBtns();
  render();

})();
</script>

</div>

## 使い方

**色を選ぶ** — カラースウォッチをクリックしてカラーピッカーを開くか、HEXコードを直接入力します。「＋ カラーストップを追加」ボタンで最大5色まで追加でき、×ボタンで削除できます（最低2色は必須）。

**位置を調整する** — 各カラーストップの横にあるスライダーで、グラデーション内での色の開始位置（0〜100%）を指定します。

**方向を決める** — 8方向のプリセットボタン（0°・45°・90°など）から選ぶか、カスタム角度スライダーで0〜360°を自由に設定します。

**ボーダーを設定する** — スライダーでボーダー幅（1〜10px）・角丸（0〜50px）・パディングを調整します。

**CSSの実装方法を選ぶ** — 2種類の実装方法から選択できます：
- **background-clip（推奨）**：外側の要素にグラデーション背景を設定し、内側の要素で白背景を重ねる手法。角丸対応で全ブラウザで動作します。
- **border-image**：1要素のみのシンプルな実装ですが、border-radiusには非対応です。

**プリセットを適用する** — プリセットギャラリーのタイルをクリックするだけで即適用されます。夕焼け・海・桜・炎など日本語名のカラーセットを12種収録。

**CSSをコピーする** — 「CSSをコピー」ボタンを押してクリップボードにコピーし、スタイルシートに貼り付けるだけです。

## CSSグラデーションボーダーの実装方法

### background-clip を使う方法（推奨）

角丸にも対応した最も汎用性の高いアプローチです。外側の要素にグラデーション背景と border-radius を設定し、内側の要素で白（または任意の色）背景を重ねます：

```css
.gradient-border {
  padding: 20px;
  background: linear-gradient(90deg, #6366f1 0%, #ec4899 100%);
  border-radius: 12px;
}

.gradient-border-inner {
  background: #fff;
  border-radius: 9px;
  padding: 3px;
}
```

### border-image を使う方法

HTMLが1要素で済むシンプルな手法ですが、border-radius は機能しません：

```css
.gradient-border {
  border: 3px solid transparent;
  border-image: linear-gradient(90deg, #6366f1 0%, #ec4899 100%) 1;
}
```

ダークモードや透過背景が必要な場合は、`::before` 擬似要素を使って `background-clip: padding-box` と組み合わせる手法もよく使われます。

---

**デザイン業務の会計管理にはfreee**
フリーランスのデザイナーやエンジニアの方、経費精算・請求書発行もfreeeでまとめて管理しませんか？
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す →</a>

<small>※本ページには広告リンクが含まれています。</small>
