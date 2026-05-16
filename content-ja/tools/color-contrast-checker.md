---
title: "カラーコントラストチェッカー — WCAGアクセシビリティツール"
date: 2025-05-16
description: "WCAG 2.1準拠のカラーコントラスト比チェック。AA・AAAレベルをライブプレビューで判定。色覚シミュレーション・アクセシブルな色提案機能付き。"
categories: ["無料ツール"]
slug: "color-contrast-checker"
ShowToc: false
aliases:
  - "/ja/tools/contrast-checker/"
  - "/ja/tools/contrast-checker/"
cover:
  image: "/images/covers/color-contrast-checker-ja.png"
  alt: "カラーコントラストチェッカー"
---

<div id="cc-app">

<style>
#cc-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', 'Segoe UI', Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 0 40px 0;
  color: #1a1a2e;
}

#cc-app * {
  box-sizing: border-box;
}

/* ── Hero ── */
.cc-hero {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  border-radius: 16px;
  padding: 28px 24px;
  margin-bottom: 24px;
  color: #fff;
}

.cc-hero-title {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0 0 4px;
}

.cc-hero-sub {
  font-size: 0.9rem;
  opacity: 0.75;
  margin: 0;
}

/* ── Layout ── */
.cc-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}

@media (max-width: 600px) {
  .cc-grid { grid-template-columns: 1fr; }
}

.cc-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
}

.cc-card-title {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #64748b;
  margin: 0 0 14px;
}

/* ── Color pickers ── */
.cc-color-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 12px;
}

.cc-swatch-btn {
  width: 48px;
  height: 48px;
  border-radius: 10px;
  border: 3px solid #e2e8f0;
  cursor: pointer;
  position: relative;
  flex-shrink: 0;
  overflow: hidden;
  padding: 0;
  background: transparent;
}

.cc-swatch-btn input[type="color"] {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  cursor: pointer;
  border: none;
  padding: 0;
}

.cc-swatch-inner {
  display: block;
  width: 100%;
  height: 100%;
  border-radius: 7px;
  pointer-events: none;
}

.cc-inputs {
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex: 1;
}

.cc-mode-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 4px;
}

.cc-mode-tab {
  padding: 2px 8px;
  border-radius: 6px;
  border: 1px solid #e2e8f0;
  background: #f8fafc;
  font-size: 0.7rem;
  font-weight: 600;
  cursor: pointer;
  color: #64748b;
  transition: all 0.15s;
}

.cc-mode-tab.active {
  background: #0f3460;
  border-color: #0f3460;
  color: #fff;
}

.cc-text-input {
  width: 100%;
  padding: 7px 10px;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  font-size: 0.85rem;
  font-family: 'Courier New', monospace;
  color: #1a1a2e;
  background: #f8fafc;
  outline: none;
  transition: border-color 0.15s;
}

.cc-text-input:focus {
  border-color: #0f3460;
  background: #fff;
}

.cc-text-input.invalid {
  border-color: #ef4444;
  background: #fef2f2;
}

/* ── Swap / action buttons ── */
.cc-action-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 24px;
}

.cc-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 9px 18px;
  border-radius: 9px;
  border: none;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}

.cc-btn-primary {
  background: #0f3460;
  color: #fff;
}

.cc-btn-primary:hover {
  background: #1a4a80;
  transform: translateY(-1px);
}

.cc-btn-swap {
  background: #f8fafc;
  color: #334155;
  border: 1px solid #e2e8f0;
  border-radius: 50px;
  padding: 8px 20px;
  font-size: 0.85rem;
  font-weight: 600;
}

.cc-btn-swap:hover { background: #e2e8f0; }

/* ── Ratio + badges ── */
.cc-ratio-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 16px;
  display: flex;
  align-items: center;
  gap: 24px;
  flex-wrap: wrap;
}

.cc-ratio-number {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1;
  color: #1a1a2e;
  letter-spacing: -0.03em;
}

.cc-ratio-label {
  font-size: 0.8rem;
  color: #64748b;
  margin-top: 2px;
}

.cc-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  flex: 1;
}

.cc-badge {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px 14px;
  border-radius: 10px;
  min-width: 80px;
  text-align: center;
}

.cc-badge-label {
  font-size: 0.68rem;
  font-weight: 700;
  letter-spacing: 0.04em;
  margin-bottom: 4px;
}

.cc-badge-result {
  font-size: 0.95rem;
  font-weight: 800;
}

.cc-badge.pass {
  background: #dcfce7;
  color: #15803d;
}

.cc-badge.fail {
  background: #fee2e2;
  color: #dc2626;
}

/* ── Live Preview ── */
.cc-preview-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
}

.cc-preview-stage {
  border-radius: 10px;
  padding: 24px;
  transition: background-color 0.2s;
}

.cc-preview-heading {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0 0 8px;
  line-height: 1.3;
}

.cc-preview-large {
  font-size: 1.125rem;
  font-weight: 400;
  margin: 0 0 10px;
  line-height: 1.6;
}

.cc-preview-normal {
  font-size: 0.9375rem;
  font-weight: 400;
  margin: 0;
  line-height: 1.7;
}

/* ── Suggestions ── */
.cc-suggestions {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
}

.cc-suggestions-title {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  color: #64748b;
  margin: 0 0 14px;
}

.cc-suggest-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.cc-suggest-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 12px;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
  cursor: pointer;
  background: #f8fafc;
  transition: all 0.15s;
  font-size: 0.8rem;
}

.cc-suggest-item:hover {
  border-color: #0f3460;
  background: #eff6ff;
}

.cc-suggest-swatch {
  width: 24px;
  height: 24px;
  border-radius: 6px;
  border: 1px solid rgba(0,0,0,0.1);
  flex-shrink: 0;
}

.cc-suggest-info {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.cc-suggest-hex {
  font-family: 'Courier New', monospace;
  font-size: 0.78rem;
  font-weight: 600;
  color: #1a1a2e;
}

.cc-suggest-ratio {
  font-size: 0.72rem;
  color: #64748b;
}

/* ── Color blindness simulation ── */
.cc-cbsim {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
}

.cc-cbsim-title {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  color: #64748b;
  margin: 0 0 14px;
}

.cc-cbsim-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 10px;
}

.cc-cbsim-item {
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid #e2e8f0;
}

.cc-cbsim-label {
  font-size: 0.7rem;
  font-weight: 600;
  padding: 5px 10px;
  background: #f8fafc;
  color: #64748b;
  border-bottom: 1px solid #e2e8f0;
  text-align: center;
}

.cc-cbsim-stage {
  padding: 14px;
  font-size: 0.875rem;
  font-weight: 500;
  text-align: center;
  line-height: 1.5;
  min-height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* ── Hidden ── */
.cc-hidden { display: none; }
</style>

<!-- Hero -->
<div class="cc-hero">
  <div class="cc-hero-title">カラーコントラストチェッカー</div>
  <p class="cc-hero-sub">WCAG 2.1 — AA・AAA準拠チェック、ライブプレビュー、色覚シミュレーション付き</p>
</div>

<!-- Color pickers -->
<div class="cc-grid">

  <!-- 前景色 -->
  <div class="cc-card">
    <p class="cc-card-title">前景色（テキスト）</p>
    <div class="cc-color-row">
      <button class="cc-swatch-btn" id="cc-fg-swatch-btn" title="前景色を選択" aria-label="前景色を選択">
        <span class="cc-swatch-inner" id="cc-fg-swatch-inner"></span>
        <input type="color" id="cc-fg-native" value="#1a1a2e" tabindex="-1" aria-hidden="true">
      </button>
      <div class="cc-inputs">
        <div class="cc-mode-tabs">
          <button class="cc-mode-tab active" data-target="fg" data-mode="hex">HEX</button>
          <button class="cc-mode-tab" data-target="fg" data-mode="rgb">RGB</button>
          <button class="cc-mode-tab" data-target="fg" data-mode="hsl">HSL</button>
        </div>
        <input class="cc-text-input" id="cc-fg-hex" value="#1a1a2e" placeholder="#000000" aria-label="前景色HEX">
        <input class="cc-text-input cc-hidden" id="cc-fg-rgb" value="rgb(26, 26, 46)" placeholder="rgb(0,0,0)" aria-label="前景色RGB">
        <input class="cc-text-input cc-hidden" id="cc-fg-hsl" value="hsl(240, 28%, 14%)" placeholder="hsl(0,0%,0%)" aria-label="前景色HSL">
      </div>
    </div>
  </div>

  <!-- 背景色 -->
  <div class="cc-card">
    <p class="cc-card-title">背景色</p>
    <div class="cc-color-row">
      <button class="cc-swatch-btn" id="cc-bg-swatch-btn" title="背景色を選択" aria-label="背景色を選択">
        <span class="cc-swatch-inner" id="cc-bg-swatch-inner"></span>
        <input type="color" id="cc-bg-native" value="#ffffff" tabindex="-1" aria-hidden="true">
      </button>
      <div class="cc-inputs">
        <div class="cc-mode-tabs">
          <button class="cc-mode-tab active" data-target="bg" data-mode="hex">HEX</button>
          <button class="cc-mode-tab" data-target="bg" data-mode="rgb">RGB</button>
          <button class="cc-mode-tab" data-target="bg" data-mode="hsl">HSL</button>
        </div>
        <input class="cc-text-input" id="cc-bg-hex" value="#ffffff" placeholder="#ffffff" aria-label="背景色HEX">
        <input class="cc-text-input cc-hidden" id="cc-bg-rgb" value="rgb(255, 255, 255)" placeholder="rgb(255,255,255)" aria-label="背景色RGB">
        <input class="cc-text-input cc-hidden" id="cc-bg-hsl" value="hsl(0, 0%, 100%)" placeholder="hsl(0,0%,100%)" aria-label="背景色HSL">
      </div>
    </div>
  </div>

</div>

<!-- アクションボタン -->
<div class="cc-action-row">
  <button class="cc-btn cc-btn-swap" id="cc-swap-btn">&#8645; 前景・背景を入れ替え</button>
  <button class="cc-btn cc-btn-primary" id="cc-random-btn">&#10022; アクセシブルな配色をランダム生成</button>
</div>

<!-- コントラスト比 + バッジ -->
<div class="cc-ratio-card">
  <div>
    <div class="cc-ratio-number" id="cc-ratio-display">14.69</div>
    <div class="cc-ratio-label">コントラスト比</div>
  </div>
  <div class="cc-badges">
    <div class="cc-badge pass" id="cc-badge-aa-normal">
      <span class="cc-badge-label">AA 通常文字</span>
      <span class="cc-badge-result">合格</span>
    </div>
    <div class="cc-badge pass" id="cc-badge-aa-large">
      <span class="cc-badge-label">AA 大きい文字</span>
      <span class="cc-badge-result">合格</span>
    </div>
    <div class="cc-badge pass" id="cc-badge-aaa-normal">
      <span class="cc-badge-label">AAA 通常文字</span>
      <span class="cc-badge-result">合格</span>
    </div>
    <div class="cc-badge pass" id="cc-badge-aaa-large">
      <span class="cc-badge-label">AAA 大きい文字</span>
      <span class="cc-badge-result">合格</span>
    </div>
  </div>
</div>

<!-- ライブプレビュー -->
<div class="cc-preview-card">
  <p class="cc-card-title">ライブプレビュー</p>
  <div class="cc-preview-stage" id="cc-preview-stage">
    <p class="cc-preview-heading" id="cc-preview-heading">見出しテキスト（24px ボールド）</p>
    <p class="cc-preview-large" id="cc-preview-large">大きいテキストのサンプル — 18px 通常ウェイト。WCAG 2.1では「大きい文字」に分類されます。</p>
    <p class="cc-preview-normal" id="cc-preview-normal">通常の本文テキスト（15px）。このサイズではWCAG AA基準（4.5:1以上）、AAA基準（7:1以上）のコントラスト比が必要です。低視力や色覚多様性を持つユーザーにも読みやすい配色を選びましょう。</p>
  </div>
</div>

<!-- 改善候補 -->
<div class="cc-suggestions" id="cc-suggestions-section">
  <p class="cc-suggestions-title">アクセシブルな代替色の提案</p>
  <div class="cc-suggest-grid" id="cc-suggest-grid"></div>
</div>

<!-- 色覚シミュレーション -->
<div class="cc-cbsim">
  <p class="cc-cbsim-title">色覚シミュレーション</p>
  <div class="cc-cbsim-grid" id="cc-cbsim-grid">
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">通常の色覚</div>
      <div class="cc-cbsim-stage" id="cc-cb-normal">サンプルテキスト</div>
    </div>
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">1型色覚（赤色弱）</div>
      <div class="cc-cbsim-stage" id="cc-cb-prot">サンプルテキスト</div>
    </div>
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">2型色覚（緑色弱）</div>
      <div class="cc-cbsim-stage" id="cc-cb-deut">サンプルテキスト</div>
    </div>
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">3型色覚（青色弱）</div>
      <div class="cc-cbsim-stage" id="cc-cb-trit">サンプルテキスト</div>
    </div>
  </div>
</div>

<script>
(function () {
  'use strict';

  // ── 状態 ──
  var fg = [26, 26, 46];
  var bg = [255, 255, 255];

  // ── 色計算ユーティリティ ──
  function clamp(v, lo, hi) { return Math.max(lo, Math.min(hi, v)); }

  function hexToRgb(hex) {
    hex = hex.replace(/^\s*#?\s*/, '').trim();
    if (hex.length === 3) hex = hex[0]+hex[0]+hex[1]+hex[1]+hex[2]+hex[2];
    if (hex.length !== 6 || !/^[0-9a-fA-F]{6}$/.test(hex)) return null;
    return [parseInt(hex.slice(0,2),16), parseInt(hex.slice(2,4),16), parseInt(hex.slice(4,6),16)];
  }

  function rgbToHex(r, g, b) {
    return '#' + [r,g,b].map(function(v){ return ('0'+Math.round(v).toString(16)).slice(-2); }).join('');
  }

  function parseRgbStr(str) {
    var m = str.match(/rgba?\s*\(\s*(\d+)\s*,\s*(\d+)\s*,\s*(\d+)/i);
    if (!m) return null;
    return [+m[1], +m[2], +m[3]];
  }

  function parseHslStr(str) {
    var m = str.match(/hsla?\s*\(\s*([\d.]+)\s*,\s*([\d.]+)%?\s*,\s*([\d.]+)%?/i);
    if (!m) return null;
    return hslToRgb(+m[1], +m[2], +m[3]);
  }

  function rgbToHsl(r, g, b) {
    r /= 255; g /= 255; b /= 255;
    var max = Math.max(r, g, b), min = Math.min(r, g, b);
    var h, s, l = (max + min) / 2;
    if (max === min) { h = s = 0; }
    else {
      var d = max - min;
      s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
      switch(max) {
        case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
        case g: h = ((b - r) / d + 2) / 6; break;
        default: h = ((r - g) / d + 4) / 6;
      }
    }
    return [Math.round(h*360), Math.round(s*100), Math.round(l*100)];
  }

  function hslToRgb(h, s, l) {
    h = h % 360; s /= 100; l /= 100;
    var c = (1 - Math.abs(2*l - 1)) * s;
    var x = c * (1 - Math.abs((h/60)%2 - 1));
    var m = l - c/2;
    var r=0, g=0, b=0;
    if      (h<60)  { r=c; g=x; b=0; }
    else if (h<120) { r=x; g=c; b=0; }
    else if (h<180) { r=0; g=c; b=x; }
    else if (h<240) { r=0; g=x; b=c; }
    else if (h<300) { r=x; g=0; b=c; }
    else            { r=c; g=0; b=x; }
    return [Math.round((r+m)*255), Math.round((g+m)*255), Math.round((b+m)*255)];
  }

  function luminance(r, g, b) {
    var c = [r, g, b].map(function(v) {
      v /= 255;
      return v <= 0.03928 ? v/12.92 : Math.pow((v+0.055)/1.055, 2.4);
    });
    return 0.2126*c[0] + 0.7152*c[1] + 0.0722*c[2];
  }

  function contrastRatio(c1, c2) {
    var l1 = luminance(c1[0], c1[1], c1[2]);
    var l2 = luminance(c2[0], c2[1], c2[2]);
    var lighter = Math.max(l1, l2), darker = Math.min(l1, l2);
    return (lighter + 0.05) / (darker + 0.05);
  }

  // ── 色覚シミュレーション（Machado et al. 2009 行列） ──
  var CB_MATRICES = {
    prot: [
      [0.567, 0.433, 0.000],
      [0.558, 0.442, 0.000],
      [0.000, 0.242, 0.758]
    ],
    deut: [
      [0.625, 0.375, 0.000],
      [0.700, 0.300, 0.000],
      [0.000, 0.300, 0.700]
    ],
    trit: [
      [0.950, 0.050, 0.000],
      [0.000, 0.433, 0.567],
      [0.000, 0.475, 0.525]
    ]
  };

  function simCB(rgb, type) {
    var m = CB_MATRICES[type];
    var r = rgb[0]/255, g = rgb[1]/255, b = rgb[2]/255;
    return [
      clamp(Math.round((m[0][0]*r + m[0][1]*g + m[0][2]*b)*255), 0, 255),
      clamp(Math.round((m[1][0]*r + m[1][1]*g + m[1][2]*b)*255), 0, 255),
      clamp(Math.round((m[2][0]*r + m[2][1]*g + m[2][2]*b)*255), 0, 255)
    ];
  }

  // ── DOM参照 ──
  var fgNative   = document.getElementById('cc-fg-native');
  var bgNative   = document.getElementById('cc-bg-native');
  var fgSwatchIn = document.getElementById('cc-fg-swatch-inner');
  var bgSwatchIn = document.getElementById('cc-bg-swatch-inner');
  var fgHex = document.getElementById('cc-fg-hex');
  var fgRgb = document.getElementById('cc-fg-rgb');
  var fgHsl = document.getElementById('cc-fg-hsl');
  var bgHex = document.getElementById('cc-bg-hex');
  var bgRgb = document.getElementById('cc-bg-rgb');
  var bgHsl = document.getElementById('cc-bg-hsl');

  var ratioDisplay = document.getElementById('cc-ratio-display');
  var badgeAaN    = document.getElementById('cc-badge-aa-normal');
  var badgeAaL    = document.getElementById('cc-badge-aa-large');
  var badgeAaaN   = document.getElementById('cc-badge-aaa-normal');
  var badgeAaaL   = document.getElementById('cc-badge-aaa-large');

  var previewStage   = document.getElementById('cc-preview-stage');
  var previewHeading = document.getElementById('cc-preview-heading');
  var previewLarge   = document.getElementById('cc-preview-large');
  var previewNormal  = document.getElementById('cc-preview-normal');

  var suggestGrid    = document.getElementById('cc-suggest-grid');
  var suggestSection = document.getElementById('cc-suggestions-section');

  var cbNormal = document.getElementById('cc-cb-normal');
  var cbProt   = document.getElementById('cc-cb-prot');
  var cbDeut   = document.getElementById('cc-cb-deut');
  var cbTrit   = document.getElementById('cc-cb-trit');

  // ── モード管理 ──
  var fgMode = 'hex', bgMode = 'hex';

  // ── バッジ更新 ──
  function setBadge(el, pass) {
    el.classList.toggle('pass', pass);
    el.classList.toggle('fail', !pass);
    el.querySelector('.cc-badge-result').textContent = pass ? '合格' : '不合格';
  }

  // ── 全体レンダリング ──
  function render() {
    var ratio = contrastRatio(fg, bg);
    var ratioStr = ratio.toFixed(2) + ':1';
    ratioDisplay.textContent = ratioStr;

    setBadge(badgeAaN,  ratio >= 4.5);
    setBadge(badgeAaL,  ratio >= 3.0);
    setBadge(badgeAaaN, ratio >= 7.0);
    setBadge(badgeAaaL, ratio >= 4.5);

    // プレビュー
    var fgCss = rgbToHex(fg[0],fg[1],fg[2]);
    var bgCss = rgbToHex(bg[0],bg[1],bg[2]);
    previewStage.style.backgroundColor = bgCss;
    [previewHeading, previewLarge, previewNormal].forEach(function(el){ el.style.color = fgCss; });

    // 色覚シミュレーション
    function setCB(el, fgSim, bgSim) {
      el.style.color = rgbToHex(fgSim[0],fgSim[1],fgSim[2]);
      el.style.backgroundColor = rgbToHex(bgSim[0],bgSim[1],bgSim[2]);
    }
    setCB(cbNormal, fg, bg);
    setCB(cbProt,   simCB(fg,'prot'), simCB(bg,'prot'));
    setCB(cbDeut,   simCB(fg,'deut'), simCB(bg,'deut'));
    setCB(cbTrit,   simCB(fg,'trit'), simCB(bg,'trit'));

    // 改善提案（AA通常未達時のみ）
    if (ratio < 4.5) {
      suggestSection.style.display = '';
      renderSuggestions();
    } else {
      suggestSection.style.display = 'none';
    }

    // 入力値同期
    syncInputs(fg, 'fg');
    syncInputs(bg, 'bg');

    // スウォッチ更新
    fgSwatchIn.style.backgroundColor = fgCss;
    bgSwatchIn.style.backgroundColor = bgCss;
    fgNative.value = fgCss;
    bgNative.value = bgCss;
  }

  function syncInputs(rgb, target) {
    var hex = rgbToHex(rgb[0],rgb[1],rgb[2]);
    var hsl = rgbToHsl(rgb[0],rgb[1],rgb[2]);
    if (target === 'fg') {
      fgHex.value = hex;
      fgRgb.value = 'rgb(' + rgb[0]+', '+rgb[1]+', '+rgb[2]+')';
      fgHsl.value = 'hsl(' + hsl[0]+', '+hsl[1]+'%, '+hsl[2]+'%)';
    } else {
      bgHex.value = hex;
      bgRgb.value = 'rgb(' + rgb[0]+', '+rgb[1]+', '+rgb[2]+')';
      bgHsl.value = 'hsl(' + hsl[0]+', '+hsl[1]+'%, '+hsl[2]+'%)';
    }
  }

  // ── 改善提案 ──
  function renderSuggestions() {
    var candidates = [];

    // 前景色を暗くする
    var hslFg = rgbToHsl(fg[0], fg[1], fg[2]);
    for (var l = hslFg[2]; l >= 0; l -= 5) {
      var candidate = hslToRgb(hslFg[0], hslFg[1], l);
      var r = contrastRatio(candidate, bg);
      if (r >= 4.5) { candidates.push({ rgb: candidate, ratio: r, label: '前景を暗く', isFg: true }); break; }
    }

    // 前景色を明るくする
    for (var l2 = hslFg[2]; l2 <= 100; l2 += 5) {
      var candidate2 = hslToRgb(hslFg[0], hslFg[1], l2);
      var r2 = contrastRatio(candidate2, bg);
      if (r2 >= 4.5) { candidates.push({ rgb: candidate2, ratio: r2, label: '前景を明るく', isFg: true }); break; }
    }

    // 背景色を明るくする
    var hslBg = rgbToHsl(bg[0], bg[1], bg[2]);
    for (var l3 = hslBg[2]; l3 <= 100; l3 += 5) {
      var candidateBg = hslToRgb(hslBg[0], hslBg[1], l3);
      var r3 = contrastRatio(fg, candidateBg);
      if (r3 >= 4.5) { candidates.push({ rgb: candidateBg, ratio: r3, label: '背景を明るく', isFg: false }); break; }
    }

    // 背景色を暗くする
    for (var l4 = hslBg[2]; l4 >= 0; l4 -= 5) {
      var candidateBg2 = hslToRgb(hslBg[0], hslBg[1], l4);
      var r4 = contrastRatio(fg, candidateBg2);
      if (r4 >= 4.5) { candidates.push({ rgb: candidateBg2, ratio: r4, label: '背景を暗く', isFg: false }); break; }
    }

    suggestGrid.innerHTML = '';
    candidates.forEach(function(c) {
      var hex = rgbToHex(c.rgb[0],c.rgb[1],c.rgb[2]);
      var div = document.createElement('div');
      div.className = 'cc-suggest-item';
      div.innerHTML =
        '<span class="cc-suggest-swatch" style="background:' + hex + '"></span>' +
        '<span class="cc-suggest-info">' +
          '<span class="cc-suggest-hex">' + hex + '</span>' +
          '<span class="cc-suggest-ratio">' + c.label + ' &bull; ' + c.ratio.toFixed(2) + ':1</span>' +
        '</span>';
      var isFg = c.isFg;
      var rgb = c.rgb;
      div.addEventListener('click', function() {
        if (isFg) { fg = rgb.slice(); } else { bg = rgb.slice(); }
        render();
      });
      suggestGrid.appendChild(div);
    });
  }

  // ── テキスト入力パース ──
  function parseInput(str, mode) {
    str = str.trim();
    if (mode === 'hex') return hexToRgb(str);
    if (mode === 'rgb') return parseRgbStr(str);
    if (mode === 'hsl') return parseHslStr(str);
    return null;
  }

  function handleInput(inputEl, mode, isFg) {
    var parsed = parseInput(inputEl.value, mode);
    if (parsed) {
      inputEl.classList.remove('invalid');
      if (isFg) fg = parsed; else bg = parsed;
      render();
    } else {
      inputEl.classList.add('invalid');
    }
  }

  // ── モードタブ ──
  document.querySelectorAll('.cc-mode-tab').forEach(function(tab) {
    tab.addEventListener('click', function() {
      var target = tab.dataset.target;
      var mode   = tab.dataset.mode;
      var isFg   = target === 'fg';
      if (isFg) fgMode = mode; else bgMode = mode;

      document.querySelectorAll('.cc-mode-tab[data-target="'+target+'"]').forEach(function(t){
        t.classList.toggle('active', t.dataset.mode === mode);
      });

      var ids = isFg
        ? { hex: fgHex, rgb: fgRgb, hsl: fgHsl }
        : { hex: bgHex, rgb: bgRgb, hsl: bgHsl };
      Object.keys(ids).forEach(function(m) {
        ids[m].classList.toggle('cc-hidden', m !== mode);
      });
    });
  });

  // ── テキスト入力イベント ──
  fgHex.addEventListener('input', function(){ handleInput(fgHex, 'hex', true); });
  fgRgb.addEventListener('input', function(){ handleInput(fgRgb, 'rgb', true); });
  fgHsl.addEventListener('input', function(){ handleInput(fgHsl, 'hsl', true); });
  bgHex.addEventListener('input', function(){ handleInput(bgHex, 'hex', false); });
  bgRgb.addEventListener('input', function(){ handleInput(bgRgb, 'rgb', false); });
  bgHsl.addEventListener('input', function(){ handleInput(bgHsl, 'hsl', false); });

  // ── ネイティブカラーピッカー ──
  fgNative.addEventListener('input', function() {
    var parsed = hexToRgb(fgNative.value);
    if (parsed) { fg = parsed; render(); }
  });
  bgNative.addEventListener('input', function() {
    var parsed = hexToRgb(bgNative.value);
    if (parsed) { bg = parsed; render(); }
  });

  // ── 入れ替え ──
  document.getElementById('cc-swap-btn').addEventListener('click', function() {
    var tmp = fg; fg = bg; bg = tmp;
    render();
  });

  // ── ランダムアクセシブルペア ──
  var ACCESSIBLE_PAIRS = [
    [[255,255,255],[0,0,0]],
    [[0,0,0],[255,255,0]],
    [[255,255,255],[0,70,127]],
    [[0,0,0],[255,204,0]],
    [[255,255,255],[31,73,125]],
    [[0,0,0],[0,168,107]],
    [[255,255,255],[155,17,30]],
    [[0,0,0],[100,149,237]],
    [[255,255,255],[75,0,130]],
    [[255,255,255],[34,85,34]],
    [[0,0,0],[255,127,80]],
    [[255,255,255],[20,20,20]],
    [[0,0,0],[200,200,200]],
    [[255,255,255],[100,40,130]],
    [[0,0,0],[64,224,208]],
    [[255,255,255],[139,0,0]],
    [[0,0,0],[255,165,0]],
    [[255,255,255],[0,100,0]]
  ];

  document.getElementById('cc-random-btn').addEventListener('click', function() {
    var pair = ACCESSIBLE_PAIRS[Math.floor(Math.random() * ACCESSIBLE_PAIRS.length)];
    fg = pair[0].slice();
    bg = pair[1].slice();
    render();
  });

  // ── 初期化 ──
  render();

})();
</script>

</div>

---

## カラーコントラストチェッカーの使い方

**色の選択** — カラースウォッチをクリックするとブラウザ標準のカラーピッカーが開きます。HEX欄に直接入力することも可能です。HEX・RGB・HSLのタブで入力形式を切り替えられ、値は常に同期されます。

**コントラスト比の確認** — 大きな数値がリアルタイムで更新されます。AA通常文字（4.5:1以上）、AA大きい文字（3:1以上）、AAA通常文字（7:1以上）、AAA大きい文字（4.5:1以上）の4基準に対して合格・不合格を表示します。

**ライブプレビューの活用** — 見出し・大きいテキスト・通常本文の3サイズで実際の表示を確認できます。公開前にここで視認性を確かめましょう。

**改善提案の適用** — AA基準を満たしていない場合、前景色または背景色を明るく・暗くした代替案が自動生成されます。候補をクリックすると即座に適用されます。

**色覚シミュレーション** — 通常の色覚、1型（赤色弱）、2型（緑色弱）、3型（青色弱）の4パターンで見え方を確認できます。コントラスト比が高くても色覚多様性によって識別しにくい組み合わせがあるため、実際の見え方の確認が重要です。

**入れ替えボタン** — 前景色と背景色を一瞬で交換します。ライトテーマとダークテーマを素早く比較できます。

**ランダム生成** — WCAG AA基準を満たす配色ペアをランダムに提案します。デザインのアイデア出しにご活用ください。

---

## WCAG 2.1 コントラスト基準について

WCAG（Web Content Accessibility Guidelines）は、W3C（World Wide Web Consortium）が策定するWebアクセシビリティの国際標準です。コントラスト比は2つの色の「相対輝度」の比率として計算され、数値が大きいほどコントラストが強くなります。

**AA基準（最低限の要件）** は、通常テキスト（18px未満、または14px未満のボールド）で **4.5:1以上**、大きいテキスト（18px以上、または14px以上のボールド）で **3:1以上** が必要です。日本の「JIS X 8341-3:2016」やEU・米国の法律でも参照される実質的な国際標準であり、Webサイト公開時の最低ラインと言えます。

**AAA基準（より高い水準）** は、通常テキストで **7:1以上**、大きいテキストで **4.5:1以上** が求められます。医療・行政・金融など、情報の正確な伝達が特に重要な場面での適用が推奨されます。

**色覚多様性への配慮** も欠かせません。日本人男性の約5%、女性の約0.2%が色覚多様性を持つとされています。最も多いのは2型色覚（緑色弱）で、赤と緑の区別が難しい方が多くいます。色だけで情報を伝えることを避け、十分なコントラスト比と形・ラベルの組み合わせによる設計が重要です。

---

## 関連ツール

> カラーピッカー → [カラーピッカー](/ja/tools/color-picker/)

> 配色パレット生成 → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)

> グラデーション作成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)

---

**デザイナー・Web制作者の経理を効率化**

クリエイティブな制作業務に集中したいのに、請求書作成・経費管理・確定申告の準備に時間を取られていませんか？クラウド会計ソフト「freee」なら、バックオフィス業務を大幅に削減できます。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
