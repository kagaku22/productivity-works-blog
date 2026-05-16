---
title: "Color Contrast Checker — WCAG Accessibility Tool"
date: 2025-05-16
description: "Check color contrast ratios for WCAG 2.1 compliance. Test AA and AAA levels with live preview, color blindness simulation, and accessible color suggestions."
categories: ["Free Tools"]
slug: "color-contrast-checker"
ShowToc: false
aliases:
  - "/tools/contrast-checker/"
  - "/tools/wcag-checker/"
cover:
  image: "/images/covers/color-contrast-checker.png"
  alt: "Color Contrast Checker"
---

<div id="cc-app">

<style>
#cc-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
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
  letter-spacing: 0.08em;
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

/* ── Swap button ── */
.cc-swap-row {
  display: flex;
  justify-content: center;
  margin-bottom: 16px;
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

.cc-btn-secondary {
  background: #f1f5f9;
  color: #334155;
  border: 1px solid #e2e8f0;
}

.cc-btn-secondary:hover {
  background: #e2e8f0;
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

.cc-btn-swap:hover {
  background: #e2e8f0;
}

.cc-action-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 24px;
}

/* ── Ratio display ── */
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
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
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
  line-height: 1.5;
}

.cc-preview-normal {
  font-size: 0.9375rem;
  font-weight: 400;
  margin: 0;
  line-height: 1.6;
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
  letter-spacing: 0.08em;
  text-transform: uppercase;
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

/* ── Color Blindness Simulation ── */
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
  letter-spacing: 0.08em;
  text-transform: uppercase;
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
  line-height: 1.4;
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
  <div class="cc-hero-title">Color Contrast Checker</div>
  <p class="cc-hero-sub">WCAG 2.1 — AA &amp; AAA compliance checker with live preview and color blindness simulation</p>
</div>

<!-- Color pickers -->
<div class="cc-grid">

  <!-- Foreground -->
  <div class="cc-card">
    <p class="cc-card-title">Foreground (Text)</p>
    <div class="cc-color-row">
      <button class="cc-swatch-btn" id="cc-fg-swatch-btn" title="Pick foreground color" aria-label="Pick foreground color">
        <span class="cc-swatch-inner" id="cc-fg-swatch-inner"></span>
        <input type="color" id="cc-fg-native" value="#1a1a2e" tabindex="-1" aria-hidden="true">
      </button>
      <div class="cc-inputs">
        <div class="cc-mode-tabs">
          <button class="cc-mode-tab active" data-target="fg" data-mode="hex">HEX</button>
          <button class="cc-mode-tab" data-target="fg" data-mode="rgb">RGB</button>
          <button class="cc-mode-tab" data-target="fg" data-mode="hsl">HSL</button>
        </div>
        <input class="cc-text-input" id="cc-fg-hex" value="#1a1a2e" placeholder="#000000" aria-label="Foreground hex color">
        <input class="cc-text-input cc-hidden" id="cc-fg-rgb" value="rgb(26, 26, 46)" placeholder="rgb(0,0,0)" aria-label="Foreground rgb color">
        <input class="cc-text-input cc-hidden" id="cc-fg-hsl" value="hsl(240, 28%, 14%)" placeholder="hsl(0,0%,0%)" aria-label="Foreground hsl color">
      </div>
    </div>
  </div>

  <!-- Background -->
  <div class="cc-card">
    <p class="cc-card-title">Background</p>
    <div class="cc-color-row">
      <button class="cc-swatch-btn" id="cc-bg-swatch-btn" title="Pick background color" aria-label="Pick background color">
        <span class="cc-swatch-inner" id="cc-bg-swatch-inner"></span>
        <input type="color" id="cc-bg-native" value="#ffffff" tabindex="-1" aria-hidden="true">
      </button>
      <div class="cc-inputs">
        <div class="cc-mode-tabs">
          <button class="cc-mode-tab active" data-target="bg" data-mode="hex">HEX</button>
          <button class="cc-mode-tab" data-target="bg" data-mode="rgb">RGB</button>
          <button class="cc-mode-tab" data-target="bg" data-mode="hsl">HSL</button>
        </div>
        <input class="cc-text-input" id="cc-bg-hex" value="#ffffff" placeholder="#ffffff" aria-label="Background hex color">
        <input class="cc-text-input cc-hidden" id="cc-bg-rgb" value="rgb(255, 255, 255)" placeholder="rgb(255,255,255)" aria-label="Background rgb color">
        <input class="cc-text-input cc-hidden" id="cc-bg-hsl" value="hsl(0, 0%, 100%)" placeholder="hsl(0,0%,100%)" aria-label="Background hsl color">
      </div>
    </div>
  </div>

</div>

<!-- Action buttons -->
<div class="cc-action-row">
  <button class="cc-btn cc-btn-swap" id="cc-swap-btn">&#8645; Swap Colors</button>
  <button class="cc-btn cc-btn-primary" id="cc-random-btn">&#10022; Random Accessible Pair</button>
</div>

<!-- Ratio + badges -->
<div class="cc-ratio-card">
  <div>
    <div class="cc-ratio-number" id="cc-ratio-display">14.69</div>
    <div class="cc-ratio-label">contrast ratio</div>
  </div>
  <div class="cc-badges">
    <div class="cc-badge pass" id="cc-badge-aa-normal">
      <span class="cc-badge-label">AA Normal</span>
      <span class="cc-badge-result">PASS</span>
    </div>
    <div class="cc-badge pass" id="cc-badge-aa-large">
      <span class="cc-badge-label">AA Large</span>
      <span class="cc-badge-result">PASS</span>
    </div>
    <div class="cc-badge pass" id="cc-badge-aaa-normal">
      <span class="cc-badge-label">AAA Normal</span>
      <span class="cc-badge-result">PASS</span>
    </div>
    <div class="cc-badge pass" id="cc-badge-aaa-large">
      <span class="cc-badge-label">AAA Large</span>
      <span class="cc-badge-result">PASS</span>
    </div>
  </div>
</div>

<!-- Live preview -->
<div class="cc-preview-card">
  <p class="cc-card-title">Live Preview</p>
  <div class="cc-preview-stage" id="cc-preview-stage">
    <p class="cc-preview-heading" id="cc-preview-heading">Heading Text (24px bold)</p>
    <p class="cc-preview-large" id="cc-preview-large">Large text sample — 18px regular weight, qualifying as "large text" under WCAG 2.1.</p>
    <p class="cc-preview-normal" id="cc-preview-normal">Normal body text at 15px. This size requires a contrast ratio of at least 4.5:1 for WCAG AA compliance and 7:1 for AAA. Make sure your color combinations are readable for all users, including those with low vision or color blindness.</p>
  </div>
</div>

<!-- Suggested fixes -->
<div class="cc-suggestions" id="cc-suggestions-section">
  <p class="cc-suggestions-title">Suggested Accessible Alternatives</p>
  <div class="cc-suggest-grid" id="cc-suggest-grid"></div>
</div>

<!-- Color blindness simulation -->
<div class="cc-cbsim">
  <p class="cc-cbsim-title">Color Blindness Simulation</p>
  <div class="cc-cbsim-grid" id="cc-cbsim-grid">
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">Normal Vision</div>
      <div class="cc-cbsim-stage" id="cc-cb-normal">Sample Text</div>
    </div>
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">Protanopia (red-blind)</div>
      <div class="cc-cbsim-stage" id="cc-cb-prot">Sample Text</div>
    </div>
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">Deuteranopia (green-blind)</div>
      <div class="cc-cbsim-stage" id="cc-cb-deut">Sample Text</div>
    </div>
    <div class="cc-cbsim-item">
      <div class="cc-cbsim-label">Tritanopia (blue-blind)</div>
      <div class="cc-cbsim-stage" id="cc-cb-trit">Sample Text</div>
    </div>
  </div>
</div>

<script>
(function () {
  'use strict';

  // ── State ──
  var fg = [26, 26, 46];
  var bg = [255, 255, 255];

  // ── Colour math ──
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

  // ── Color-blindness simulation (Machado et al. 2009 matrices) ──
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

  // ── DOM ──
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

  // ── Mode tracking ──
  var fgMode = 'hex', bgMode = 'hex';

  // ── Set badge ──
  function setBadge(el, pass) {
    el.classList.toggle('pass', pass);
    el.classList.toggle('fail', !pass);
    el.querySelector('.cc-badge-result').textContent = pass ? 'PASS' : 'FAIL';
  }

  // ── Render all ──
  function render() {
    var ratio = contrastRatio(fg, bg);
    var ratioStr = ratio.toFixed(2) + ':1';
    ratioDisplay.textContent = ratioStr;

    setBadge(badgeAaN,  ratio >= 4.5);
    setBadge(badgeAaL,  ratio >= 3.0);
    setBadge(badgeAaaN, ratio >= 7.0);
    setBadge(badgeAaaL, ratio >= 4.5);

    // Preview
    var fgCss = rgbToHex(fg[0],fg[1],fg[2]);
    var bgCss = rgbToHex(bg[0],bg[1],bg[2]);
    previewStage.style.backgroundColor = bgCss;
    [previewHeading, previewLarge, previewNormal].forEach(function(el){ el.style.color = fgCss; });

    // Color blindness
    function setCB(el, fgSim, bgSim) {
      el.style.color = rgbToHex(fgSim[0],fgSim[1],fgSim[2]);
      el.style.backgroundColor = rgbToHex(bgSim[0],bgSim[1],bgSim[2]);
    }
    setCB(cbNormal, fg, bg);
    setCB(cbProt,   simCB(fg,'prot'), simCB(bg,'prot'));
    setCB(cbDeut,   simCB(fg,'deut'), simCB(bg,'deut'));
    setCB(cbTrit,   simCB(fg,'trit'), simCB(bg,'trit'));

    // Suggestions (only if failing AA Normal)
    if (ratio < 4.5) {
      suggestSection.style.display = '';
      renderSuggestions();
    } else {
      suggestSection.style.display = 'none';
    }

    // Sync inputs
    syncInputs(fg, 'fg');
    syncInputs(bg, 'bg');

    // Swatches
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

  // ── Suggestions ──
  function renderSuggestions() {
    var candidates = [];

    // Try darkening foreground
    var hslFg = rgbToHsl(fg[0], fg[1], fg[2]);
    for (var l = hslFg[2]; l >= 0; l -= 5) {
      var candidate = hslToRgb(hslFg[0], hslFg[1], l);
      var r = contrastRatio(candidate, bg);
      if (r >= 4.5) {
        candidates.push({ rgb: candidate, ratio: r, label: 'Darker FG' });
        break;
      }
    }

    // Try lightening foreground
    for (var l2 = hslFg[2]; l2 <= 100; l2 += 5) {
      var candidate2 = hslToRgb(hslFg[0], hslFg[1], l2);
      var r2 = contrastRatio(candidate2, bg);
      if (r2 >= 4.5) {
        candidates.push({ rgb: candidate2, ratio: r2, label: 'Lighter FG' });
        break;
      }
    }

    // Try lightening background
    var hslBg = rgbToHsl(bg[0], bg[1], bg[2]);
    for (var l3 = hslBg[2]; l3 <= 100; l3 += 5) {
      var candidateBg = hslToRgb(hslBg[0], hslBg[1], l3);
      var r3 = contrastRatio(fg, candidateBg);
      if (r3 >= 4.5) {
        candidates.push({ rgb: candidateBg, ratio: r3, label: 'Lighter BG' });
        break;
      }
    }

    // Try darkening background
    for (var l4 = hslBg[2]; l4 >= 0; l4 -= 5) {
      var candidateBg2 = hslToRgb(hslBg[0], hslBg[1], l4);
      var r4 = contrastRatio(fg, candidateBg2);
      if (r4 >= 4.5) {
        candidates.push({ rgb: candidateBg2, ratio: r4, label: 'Darker BG' });
        break;
      }
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
      var isFgSuggestion = c.label.indexOf('FG') !== -1;
      div.addEventListener('click', function() {
        if (isFgSuggestion) { fg = c.rgb.slice(); }
        else { bg = c.rgb.slice(); }
        render();
      });
      suggestGrid.appendChild(div);
    });
  }

  // ── Parse user input ──
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

  // ── Mode tab switching ──
  document.querySelectorAll('.cc-mode-tab').forEach(function(tab) {
    tab.addEventListener('click', function() {
      var target = tab.dataset.target;
      var mode   = tab.dataset.mode;
      var isFg   = target === 'fg';
      if (isFg) fgMode = mode; else bgMode = mode;

      // Update active tab UI
      document.querySelectorAll('.cc-mode-tab[data-target="'+target+'"]').forEach(function(t){
        t.classList.toggle('active', t.dataset.mode === mode);
      });

      // Show/hide inputs
      var ids = isFg
        ? { hex: fgHex, rgb: fgRgb, hsl: fgHsl }
        : { hex: bgHex, rgb: bgRgb, hsl: bgHsl };
      Object.keys(ids).forEach(function(m) {
        ids[m].classList.toggle('cc-hidden', m !== mode);
      });
    });
  });

  // ── Text input events ──
  fgHex.addEventListener('input', function(){ handleInput(fgHex, 'hex', true); });
  fgRgb.addEventListener('input', function(){ handleInput(fgRgb, 'rgb', true); });
  fgHsl.addEventListener('input', function(){ handleInput(fgHsl, 'hsl', true); });
  bgHex.addEventListener('input', function(){ handleInput(bgHex, 'hex', false); });
  bgRgb.addEventListener('input', function(){ handleInput(bgRgb, 'rgb', false); });
  bgHsl.addEventListener('input', function(){ handleInput(bgHsl, 'hsl', false); });

  // ── Native color pickers ──
  fgNative.addEventListener('input', function() {
    var parsed = hexToRgb(fgNative.value);
    if (parsed) { fg = parsed; render(); }
  });
  bgNative.addEventListener('input', function() {
    var parsed = hexToRgb(bgNative.value);
    if (parsed) { bg = parsed; render(); }
  });

  // ── Swap ──
  document.getElementById('cc-swap-btn').addEventListener('click', function() {
    var tmp = fg; fg = bg; bg = tmp;
    render();
  });

  // ── Random accessible pair ──
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

  // ── Init ──
  render();

})();
</script>

</div>

## How to Use This Contrast Checker

**Pick your colors** by clicking the color swatch to open the native color picker, or type directly into the HEX field. Switch between HEX, RGB, and HSL formats using the tabs above the input — all formats stay in sync automatically.

**Read the ratio** in the large number displayed below the pickers. A higher ratio means more contrast. The four badges (AA Normal, AA Large, AAA Normal, AAA Large) each show PASS or FAIL based on WCAG 2.1 thresholds.

**Use the live preview** to see exactly how your text will look at heading, large, and normal body sizes — all rendered in real time with your chosen colors.

**Check suggested fixes** when your ratio falls below AA. The tool calculates the nearest accessible alternative by incrementally adjusting lightness, and each suggestion is clickable to instantly apply it.

**Simulate color blindness** in the bottom grid. The four panels show how your color pair appears under normal vision, protanopia (red-blind), deuteranopia (green-blind), and tritanopia (blue-blind).

**Swap colors** at any time to flip foreground and background — useful for checking both light-on-dark and dark-on-light variants of the same palette.

**Generate a random accessible pair** to explore color combinations that already meet WCAG AA requirements.

## Understanding WCAG Contrast Requirements

WCAG 2.1 (Web Content Accessibility Guidelines) defines contrast ratio thresholds that ensure text remains readable for users with low vision or color blindness. Contrast ratio is calculated using the relative luminance of two colors — a value derived from the linear RGB channels — and expressed as a ratio such as 4.5:1 or 7:1.

**Level AA** is the standard legal and industry baseline. It requires a contrast ratio of at least **4.5:1** for normal text (below 18pt, or below 14pt bold) and **3:1** for large text (18pt or larger, or 14pt bold or larger). Most web accessibility laws worldwide — including WCAG referenced by the EU Web Accessibility Directive, Section 508 in the US, and JIS X 8341-3 in Japan — require Level AA compliance.

**Level AAA** is the enhanced standard. It requires **7:1** for normal text and **4.5:1** for large text. AAA is recommended for critical interfaces such as healthcare portals, government services, and financial applications where text legibility is essential.

**Color blindness** affects approximately 8% of males and 0.5% of females worldwide. The most common forms are protanopia (reduced red sensitivity), deuteranopia (reduced green sensitivity), and tritanopia (reduced blue sensitivity). Because color blindness changes how colors are perceived — not just their brightness — it is possible to have a passing contrast ratio under normal vision but poor readability under color-blind simulation. Always check both.

---

### Related Tools

> Pick colors → [Color Picker](/tools/color-picker/)

> Generate palettes → [Color Palette Generator](/tools/color-palette-generator/)

> Create gradients → [CSS Gradient Generator](/tools/css-gradient-generator/)
