---
title: "カラーピッカー｜HEX・RGB・HSL変換＆パレット作成【無料】"
date: 2025-12-24
description: "色を視覚的に選んでHEX・RGB・HSLを相互変換。配色パレット生成、コントラスト比チェック機能付き。デザイナー・開発者向け無料カラーツール。"
categories: ["無料ツール"]
tags: ["カラーピッカー", "HEX変換", "RGB", "HSL", "デザインツール"]
slug: "color-picker"
aliases: ["/ja/tools/rgb-hex-converter/", "/ja/tools/color-converter/"]
cover:
  image: "/images/covers/color-picker-ja.png"
  alt: "カラーピッカー"
ShowToc: false
---

<div id="color-app">

<style>
#color-app {
font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a1a2e;
}
#color-app * { box-sizing: border-box; }

/* Layout */
.ca-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
}
@media (max-width: 640px) {
.ca-grid { grid-template-columns: 1fr; }
}

/* Card */
.ca-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
margin-bottom: 20px;
}
.ca-card h3 {
margin: 0 0 14px;
font-size: 15px;
font-weight: 700;
color: #2d3748;
border-bottom: 2px solid #f0f0f0;
padding-bottom: 8px;
}

/* Preview panel */
.ca-preview {
width: 100%;
aspect-ratio: 1 / 1;
border-radius: 12px;
border: 1px solid #e2e8f0;
transition: background 0.15s;
cursor: pointer;
min-height: 160px;
}
.ca-preview-label {
text-align: center;
font-size: 13px;
color: #718096;
margin-top: 6px;
}

/* Native color input */
.ca-native-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 16px;
}
.ca-native-input {
width: 56px;
height: 56px;
border: none;
border-radius: 8px;
cursor: pointer;
padding: 2px;
background: none;
}
.ca-native-label {
font-size: 14px;
color: #4a5568;
}

/* HEX field */
.ca-hex-row {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 18px;
}
.ca-hex-input {
flex: 1;
padding: 9px 12px;
border: 1.5px solid #cbd5e0;
border-radius: 8px;
font-size: 16px;
font-family: 'Courier New', monospace;
letter-spacing: 1px;
text-transform: uppercase;
outline: none;
transition: border-color 0.2s;
}
.ca-hex-input:focus { border-color: #667eea; }
.ca-hex-input.invalid { border-color: #e53e3e; background: #fff5f5; }

/* Copy button */
.ca-copy-btn {
padding: 8px 14px;
border: 1.5px solid #cbd5e0;
border-radius: 8px;
background: #f7fafc;
font-size: 13px;
cursor: pointer;
transition: all 0.15s;
white-space: nowrap;
color: #4a5568;
}
.ca-copy-btn:hover { background: #667eea; color: #fff; border-color: #667eea; }
.ca-copy-btn.copied { background: #38a169; color: #fff; border-color: #38a169; }

/* Sliders section */
.ca-slider-group { margin-bottom: 16px; }
.ca-slider-label-row {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 4px;
}
.ca-slider-label { font-size: 13px; font-weight: 600; color: #4a5568; }
.ca-slider-num {
width: 54px;
padding: 3px 6px;
border: 1.5px solid #cbd5e0;
border-radius: 6px;
font-size: 13px;
text-align: center;
outline: none;
}
.ca-slider-num:focus { border-color: #667eea; }
.ca-slider {
width: 100%;
height: 8px;
border-radius: 4px;
outline: none;
cursor: pointer;
-webkit-appearance: none;
appearance: none;
}
.ca-slider::-webkit-slider-thumb {
-webkit-appearance: none;
width: 18px; height: 18px;
border-radius: 50%;
background: #fff;
border: 2px solid #667eea;
cursor: pointer;
box-shadow: 0 1px 4px rgba(0,0,0,0.2);
}
.ca-slider::-moz-range-thumb {
width: 18px; height: 18px;
border-radius: 50%;
background: #fff;
border: 2px solid #667eea;
cursor: pointer;
}

/* RGB slider tracks */
#ca-r-slider { background: linear-gradient(to right, #000, #f00); }
#ca-g-slider { background: linear-gradient(to right, #000, #0f0); }
#ca-b-slider { background: linear-gradient(to right, #000, #00f); }
#ca-h-slider { background: linear-gradient(to right, hsl(0,100%,50%), hsl(30,100%,50%), hsl(60,100%,50%), hsl(90,100%,50%), hsl(120,100%,50%), hsl(150,100%,50%), hsl(180,100%,50%), hsl(210,100%,50%), hsl(240,100%,50%), hsl(270,100%,50%), hsl(300,100%,50%), hsl(330,100%,50%), hsl(360,100%,50%)); }
#ca-s-slider { background: linear-gradient(to right, #808080, #f00); }
#ca-l-slider { background: linear-gradient(to right, #000, #808080, #fff); }

/* Format output rows */
.ca-format-row {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 10px;
}
.ca-format-label {
font-size: 12px;
font-weight: 700;
color: #667eea;
width: 36px;
flex-shrink: 0;
}
.ca-format-value {
flex: 1;
padding: 7px 10px;
background: #f7fafc;
border: 1px solid #e2e8f0;
border-radius: 7px;
font-size: 13px;
font-family: 'Courier New', monospace;
color: #2d3748;
user-select: all;
}

/* Palette */
.ca-palette-grid {
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 12px;
}
.ca-palette-item { }
.ca-palette-title {
font-size: 12px;
font-weight: 600;
color: #718096;
margin-bottom: 6px;
}
.ca-palette-swatches {
display: flex;
gap: 6px;
flex-wrap: wrap;
}
.ca-swatch {
width: 36px;
height: 36px;
border-radius: 8px;
border: 1px solid rgba(0,0,0,0.1);
cursor: pointer;
transition: transform 0.15s;
position: relative;
}
.ca-swatch:hover { transform: scale(1.15); }
.ca-swatch-hex {
font-size: 10px;
color: #718096;
margin-top: 2px;
font-family: monospace;
}
@media (max-width: 640px) {
.ca-palette-grid { grid-template-columns: 1fr; }
}

/* Contrast checker */
.ca-contrast-section { }
.ca-contrast-pair {
display: flex;
gap: 10px;
margin-bottom: 12px;
align-items: center;
}
.ca-contrast-pair label { font-size: 13px; color: #4a5568; width: 70px; flex-shrink: 0; }
.ca-contrast-color-input {
width: 44px; height: 44px;
border: none; border-radius: 8px;
padding: 2px; background: none; cursor: pointer;
}
.ca-contrast-preview {
flex: 1;
padding: 10px 14px;
border-radius: 8px;
font-size: 14px;
font-weight: 600;
border: 1px solid #e2e8f0;
text-align: center;
}
.ca-contrast-result {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
gap: 8px;
margin-top: 10px;
}
.ca-contrast-badge {
padding: 8px 4px;
border-radius: 8px;
text-align: center;
font-size: 12px;
font-weight: 700;
}
.ca-contrast-badge .ratio { font-size: 16px; display: block; margin-bottom: 2px; }
.ca-badge-pass { background: #c6f6d5; color: #276749; }
.ca-badge-fail { background: #fed7d7; color: #9b2c2c; }

/* History */
.ca-history-row {
display: flex;
flex-wrap: wrap;
gap: 8px;
}
.ca-hist-swatch {
width: 38px;
height: 38px;
border-radius: 8px;
border: 1px solid rgba(0,0,0,0.12);
cursor: pointer;
transition: transform 0.15s;
position: relative;
}
.ca-hist-swatch:hover { transform: scale(1.15); }
.ca-hist-empty { font-size: 13px; color: #a0aec0; }

/* CSS output */
.ca-css-output {
background: #1a1a2e;
color: #e2e8f0;
border-radius: 8px;
padding: 14px;
font-size: 12px;
font-family: 'Courier New', monospace;
white-space: pre-wrap;
line-height: 1.7;
overflow-x: auto;
}
</style>

<!-- ===== APP HTML ===== -->

<div class="ca-card">
<div class="ca-grid">
<!-- Left: Preview + Native -->
<div>
<div id="ca-preview" class="ca-preview" title="クリックでコピー"></div>
<p class="ca-preview-label">カラープレビュー（クリックでHEXコピー）</p>
<div class="ca-native-row" style="margin-top:14px;">
<input type="color" id="ca-native" class="ca-native-input" value="#667eea" title="クリックして色を選択">
<span class="ca-native-label">クリックして色を選択</span>
</div>
</div>
<!-- Right: HEX + Format outputs -->
<div>
<h3>HEX 入力</h3>
<div class="ca-hex-row">
<input type="text" id="ca-hex" class="ca-hex-input" value="#667EEA" maxlength="7" spellcheck="false" placeholder="#000000">
<button class="ca-copy-btn" onclick="caCopyFormat('hex')">コピー</button>
</div>
<h3>カラー値</h3>
<div class="ca-format-row">
<span class="ca-format-label">HEX</span>
<span class="ca-format-value" id="ca-out-hex">#667EEA</span>
<button class="ca-copy-btn" onclick="caCopyFormat('hex')">コピー</button>
</div>
<div class="ca-format-row">
<span class="ca-format-label">RGB</span>
<span class="ca-format-value" id="ca-out-rgb">rgb(102, 126, 234)</span>
<button class="ca-copy-btn" onclick="caCopyFormat('rgb')">コピー</button>
</div>
<div class="ca-format-row">
<span class="ca-format-label">HSL</span>
<span class="ca-format-value" id="ca-out-hsl">hsl(231, 77%, 66%)</span>
<button class="ca-copy-btn" onclick="caCopyFormat('hsl')">コピー</button>
</div>
</div>
</div>
</div>

<!-- RGB Sliders -->
<div class="ca-card">
<h3>RGB スライダー</h3>
<div class="ca-slider-group">
<div class="ca-slider-label-row">
<span class="ca-slider-label">R（赤）</span>
<input type="number" id="ca-r-num" class="ca-slider-num" min="0" max="255" value="102">
</div>
<input type="range" id="ca-r-slider" class="ca-slider" min="0" max="255" value="102">
</div>
<div class="ca-slider-group">
<div class="ca-slider-label-row">
<span class="ca-slider-label">G（緑）</span>
<input type="number" id="ca-g-num" class="ca-slider-num" min="0" max="255" value="126">
</div>
<input type="range" id="ca-g-slider" class="ca-slider" min="0" max="255" value="126">
</div>
<div class="ca-slider-group">
<div class="ca-slider-label-row">
<span class="ca-slider-label">B（青）</span>
<input type="number" id="ca-b-num" class="ca-slider-num" min="0" max="255" value="234">
</div>
<input type="range" id="ca-b-slider" class="ca-slider" min="0" max="255" value="234">
</div>
</div>

<!-- HSL Sliders -->
<div class="ca-card">
<h3>HSL スライダー</h3>
<div class="ca-slider-group">
<div class="ca-slider-label-row">
<span class="ca-slider-label">H（色相）</span>
<input type="number" id="ca-h-num" class="ca-slider-num" min="0" max="360" value="231">
</div>
<input type="range" id="ca-h-slider" class="ca-slider" min="0" max="360" value="231">
</div>
<div class="ca-slider-group">
<div class="ca-slider-label-row">
<span class="ca-slider-label">S（彩度）%</span>
<input type="number" id="ca-s-num" class="ca-slider-num" min="0" max="100" value="77">
</div>
<input type="range" id="ca-s-slider" class="ca-slider" min="0" max="100" value="77">
</div>
<div class="ca-slider-group">
<div class="ca-slider-label-row">
<span class="ca-slider-label">L（明度）%</span>
<input type="number" id="ca-l-num" class="ca-slider-num" min="0" max="100" value="66">
</div>
<input type="range" id="ca-l-slider" class="ca-slider" min="0" max="100" value="66">
</div>
</div>

<!-- Palette -->
<div class="ca-card">
<h3>配色パレット生成</h3>
<div class="ca-palette-grid">
<div class="ca-palette-item">
<div class="ca-palette-title">補色（コンプリメンタリー）</div>
<div class="ca-palette-swatches" id="ca-pal-comp"></div>
</div>
<div class="ca-palette-item">
<div class="ca-palette-title">類似色（アナログ）</div>
<div class="ca-palette-swatches" id="ca-pal-analog"></div>
</div>
<div class="ca-palette-item">
<div class="ca-palette-title">トライアド（3色）</div>
<div class="ca-palette-swatches" id="ca-pal-triad"></div>
</div>
<div class="ca-palette-item">
<div class="ca-palette-title">分割補色</div>
<div class="ca-palette-swatches" id="ca-pal-split"></div>
</div>
</div>
</div>

<!-- Contrast Checker -->
<div class="ca-card">
<h3>コントラストチェッカー（WCAG 2.1）</h3>
<div class="ca-contrast-pair">
<label>前景色</label>
<input type="color" id="ca-fg-color" class="ca-contrast-color-input" value="#ffffff">
<div class="ca-contrast-preview" id="ca-contrast-preview">サンプルテキスト Aa</div>
<input type="color" id="ca-bg-color" class="ca-contrast-color-input" value="#667eea">
<label>背景色</label>
</div>
<div class="ca-contrast-result" id="ca-contrast-result">
<div class="ca-contrast-badge" id="ca-badge-ratio"><span class="ratio" id="ca-ratio-val">--</span>コントラスト比</div>
<div class="ca-contrast-badge" id="ca-badge-aa">AA</div>
<div class="ca-contrast-badge" id="ca-badge-aaa">AAA</div>
</div>
</div>

<!-- History -->
<div class="ca-card">
<h3>カラー履歴（直近10色）</h3>
<div class="ca-history-row" id="ca-history">
<span class="ca-hist-empty">まだ色を選択していません</span>
</div>
</div>

<!-- CSS Output -->
<div class="ca-card">
<h3>CSS コード出力 <button class="ca-copy-btn" style="float:right;margin-top:-4px;" onclick="caCopyCss()">CSSをコピー</button></h3>
<pre class="ca-css-output" id="ca-css-out"></pre>
</div>

<script>
(function() {
'use strict';

// ===== State =====
let caR = 102, caG = 126, caB = 234;
let caHistory = [];
let caLock = false;

// ===== Helpers =====
function caHexToRgb(hex) {
hex = hex.replace(/^#/, '');
if (hex.length === 3) hex = hex.split('').map(c => c+c).join('');
if (hex.length !== 6) return null;
const n = parseInt(hex, 16);
if (isNaN(n)) return null;
return { r: (n >> 16) & 255, g: (n >> 8) & 255, b: n & 255 };
}

function caRgbToHex(r, g, b) {
return '#' + [r, g, b].map(v => v.toString(16).padStart(2, '0')).join('').toUpperCase();
}

function caRgbToHsl(r, g, b) {
r /= 255; g /= 255; b /= 255;
const max = Math.max(r, g, b), min = Math.min(r, g, b);
let h, s, l = (max + min) / 2;
if (max === min) { h = s = 0; }
else {
const d = max - min;
s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
switch (max) {
case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
case g: h = ((b - r) / d + 2) / 6; break;
case b: h = ((r - g) / d + 4) / 6; break;
}
}
return { h: Math.round(h * 360), s: Math.round(s * 100), l: Math.round(l * 100) };
}

function caHslToRgb(h, s, l) {
s /= 100; l /= 100;
const k = n => (n + h / 30) % 12;
const a = s * Math.min(l, 1 - l);
const f = n => l - a * Math.max(-1, Math.min(k(n) - 3, Math.min(9 - k(n), 1)));
return {
r: Math.round(f(0) * 255),
g: Math.round(f(8) * 255),
b: Math.round(f(4) * 255)
};
}

function caClamp(v, min, max) { return Math.min(max, Math.max(min, Math.round(v))); }

function caRelativeLuminance(r, g, b) {
const toLinear = c => { c /= 255; return c <= 0.03928 ? c / 12.92 : Math.pow((c + 0.055) / 1.055, 2.4); };
return 0.2126 * toLinear(r) + 0.7152 * toLinear(g) + 0.0722 * toLinear(b);
}

function caContrastRatio(r1, g1, b1, r2, g2, b2) {
const l1 = caRelativeLuminance(r1, g1, b1);
const l2 = caRelativeLuminance(r2, g2, b2);
const lighter = Math.max(l1, l2), darker = Math.min(l1, l2);
return (lighter + 0.05) / (darker + 0.05);
}

function caHslColor(h, s, l) {
h = ((h % 360) + 360) % 360;
s = caClamp(s, 0, 100);
l = caClamp(l, 0, 100);
const rgb = caHslToRgb(h, s, l);
return caRgbToHex(rgb.r, rgb.g, rgb.b);
}

// ===== Update all UI from caR, caG, caB =====
function caUpdate(source) {
if (caLock) return;
caLock = true;

const hex = caRgbToHex(caR, caG, caB);
const hsl = caRgbToHsl(caR, caG, caB);

// Preview
document.getElementById('ca-preview').style.background = hex;

// Native
if (source !== 'native') document.getElementById('ca-native').value = hex;

// HEX input
if (source !== 'hex') {
const hexEl = document.getElementById('ca-hex');
hexEl.value = hex;
hexEl.classList.remove('invalid');
}

// Output labels
document.getElementById('ca-out-hex').textContent = hex;
document.getElementById('ca-out-rgb').textContent = 'rgb(' + caR + ', ' + caG + ', ' + caB + ')';
document.getElementById('ca-out-hsl').textContent = 'hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%)';

// RGB sliders
if (source !== 'rgb') {
document.getElementById('ca-r-slider').value = caR;
document.getElementById('ca-g-slider').value = caG;
document.getElementById('ca-b-slider').value = caB;
document.getElementById('ca-r-num').value = caR;
document.getElementById('ca-g-num').value = caG;
document.getElementById('ca-b-num').value = caB;
}

// HSL sliders
if (source !== 'hsl') {
document.getElementById('ca-h-slider').value = hsl.h;
document.getElementById('ca-s-slider').value = hsl.s;
document.getElementById('ca-l-slider').value = hsl.l;
document.getElementById('ca-h-num').value = hsl.h;
document.getElementById('ca-s-num').value = hsl.s;
document.getElementById('ca-l-num').value = hsl.l;
}

// Update HSL slider tracks dynamically
document.getElementById('ca-s-slider').style.background =
'linear-gradient(to right, hsl(' + hsl.h + ',0%,50%), hsl(' + hsl.h + ',100%,50%))';
document.getElementById('ca-l-slider').style.background =
'linear-gradient(to right, #000, hsl(' + hsl.h + ',' + hsl.s + '%,50%), #fff)';

// Palette
caUpdatePalette(hsl);

// CSS output
document.getElementById('ca-css-out').textContent =
':root {\n  --color-primary: ' + hex + ';\n  --color-primary-rgb: ' + caR + ', ' + caG + ', ' + caB + ';\n  --color-primary-hsl: ' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%;\n}\n\n.element {\n  color: ' + hex + ';\n  color: rgb(' + caR + ', ' + caG + ', ' + caB + ');\n  color: hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%);\n  background-color: ' + hex + ';\n}';

// Sync bg of contrast checker
document.getElementById('ca-bg-color').value = hex.toLowerCase();
caUpdateContrast();

// Add to history (debounced via source check)
if (source !== 'history') caAddHistory(hex);

caLock = false;
}

// ===== Palette =====
function caUpdatePalette(hsl) {
const h = hsl.h, s = hsl.s, l = hsl.l;
const palettes = {
'ca-pal-comp':  [caHslColor(h, s, l), caHslColor(h + 180, s, l)],
'ca-pal-analog': [caHslColor(h - 30, s, l), caHslColor(h, s, l), caHslColor(h + 30, s, l)],
'ca-pal-triad':  [caHslColor(h, s, l), caHslColor(h + 120, s, l), caHslColor(h + 240, s, l)],
'ca-pal-split':  [caHslColor(h, s, l), caHslColor(h + 150, s, l), caHslColor(h + 210, s, l)]
};
for (const [id, colors] of Object.entries(palettes)) {
const el = document.getElementById(id);
el.innerHTML = '';
colors.forEach(c => {
const wrap = document.createElement('div');
const sw = document.createElement('div');
sw.className = 'ca-swatch';
sw.style.background = c;
sw.title = c;
sw.addEventListener('click', () => caApplyHex(c));
const label = document.createElement('div');
label.className = 'ca-swatch-hex';
label.textContent = c;
wrap.appendChild(sw);
wrap.appendChild(label);
el.appendChild(wrap);
});
}
}

// ===== Contrast =====
function caUpdateContrast() {
const fgVal = document.getElementById('ca-fg-color').value;
const bgVal = document.getElementById('ca-bg-color').value;
const fg = caHexToRgb(fgVal);
const bg = caHexToRgb(bgVal);
if (!fg || !bg) return;

const preview = document.getElementById('ca-contrast-preview');
preview.style.color = fgVal;
preview.style.background = bgVal;

const ratio = caContrastRatio(fg.r, fg.g, fg.b, bg.r, bg.g, bg.b);
const ratioStr = ratio.toFixed(2) + ':1';
document.getElementById('ca-ratio-val').textContent = ratioStr;
document.getElementById('ca-badge-ratio').className = 'ca-contrast-badge ca-badge-pass';

const aa = ratio >= 4.5;
const aaa = ratio >= 7;
const badgeAa = document.getElementById('ca-badge-aa');
const badgeAaa = document.getElementById('ca-badge-aaa');
badgeAa.textContent = 'AA ' + (aa ? '合格' : '不合格');
badgeAa.className = 'ca-contrast-badge ' + (aa ? 'ca-badge-pass' : 'ca-badge-fail');
badgeAaa.textContent = 'AAA ' + (aaa ? '合格' : '不合格');
badgeAaa.className = 'ca-contrast-badge ' + (aaa ? 'ca-badge-pass' : 'ca-badge-fail');
}

// ===== History =====
function caAddHistory(hex) {
if (caHistory[0] === hex) return;
caHistory = caHistory.filter(c => c !== hex);
caHistory.unshift(hex);
if (caHistory.length > 10) caHistory.pop();
caRenderHistory();
}

function caRenderHistory() {
const el = document.getElementById('ca-history');
if (caHistory.length === 0) {
el.innerHTML = '<span class="ca-hist-empty">まだ色を選択していません</span>';
return;
}
el.innerHTML = '';
caHistory.forEach(c => {
const sw = document.createElement('div');
sw.className = 'ca-hist-swatch';
sw.style.background = c;
sw.title = c;
sw.addEventListener('click', () => caApplyHex(c));
el.appendChild(sw);
});
}

// ===== Apply from HEX =====
function caApplyHex(hex) {
const rgb = caHexToRgb(hex);
if (!rgb) return;
caR = rgb.r; caG = rgb.g; caB = rgb.b;
caUpdate('hex');
}

// ===== Copy helpers =====
window.caCopyFormat = function(fmt) {
let text = '';
if (fmt === 'hex') text = document.getElementById('ca-out-hex').textContent;
else if (fmt === 'rgb') text = document.getElementById('ca-out-rgb').textContent;
else if (fmt === 'hsl') text = document.getElementById('ca-out-hsl').textContent;
caCopyText(text, event.target);
};

window.caCopyCss = function() {
caCopyText(document.getElementById('ca-css-out').textContent, event.target);
};

function caCopyText(text, btn) {
navigator.clipboard.writeText(text).then(() => {
if (btn) {
const orig = btn.textContent;
btn.textContent = 'コピー済み!';
btn.classList.add('copied');
setTimeout(() => { btn.textContent = orig; btn.classList.remove('copied'); }, 1500);
}
}).catch(() => {
const ta = document.createElement('textarea');
ta.value = text; ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta); ta.select(); document.execCommand('copy');
document.body.removeChild(ta);
if (btn) {
const orig = btn.textContent;
btn.textContent = 'コピー済み!';
btn.classList.add('copied');
setTimeout(() => { btn.textContent = orig; btn.classList.remove('copied'); }, 1500);
}
});
}

// ===== Event Listeners =====

// Preview click => copy HEX
document.getElementById('ca-preview').addEventListener('click', function() {
caCopyText(document.getElementById('ca-out-hex').textContent, null);
this.style.outline = '3px solid #38a169';
setTimeout(() => { this.style.outline = ''; }, 600);
});

// Native color input
document.getElementById('ca-native').addEventListener('input', function() {
const rgb = caHexToRgb(this.value);
if (!rgb) return;
caR = rgb.r; caG = rgb.g; caB = rgb.b;
caUpdate('native');
});

// HEX text input
document.getElementById('ca-hex').addEventListener('input', function() {
const val = this.value.trim();
const hex = val.startsWith('#') ? val : '#' + val;
const rgb = caHexToRgb(hex);
if (rgb) {
this.classList.remove('invalid');
caR = rgb.r; caG = rgb.g; caB = rgb.b;
caUpdate('hex');
} else {
this.classList.add('invalid');
}
});

// RGB sliders + number inputs
['r', 'g', 'b'].forEach(ch => {
const slider = document.getElementById('ca-' + ch + '-slider');
const num = document.getElementById('ca-' + ch + '-num');
const apply = (v) => {
v = caClamp(parseInt(v) || 0, 0, 255);
if (ch === 'r') caR = v;
else if (ch === 'g') caG = v;
else caB = v;
slider.value = v;
num.value = v;
caUpdate('rgb');
};
slider.addEventListener('input', () => apply(slider.value));
num.addEventListener('input', () => apply(num.value));
});

// HSL sliders + number inputs
['h', 's', 'l'].forEach(ch => {
const slider = document.getElementById('ca-' + ch + '-slider');
const num = document.getElementById('ca-' + ch + '-num');
const apply = () => {
const h = caClamp(parseInt(document.getElementById('ca-h-num').value) || 0, 0, 360);
const s = caClamp(parseInt(document.getElementById('ca-s-num').value) || 0, 0, 100);
const l = caClamp(parseInt(document.getElementById('ca-l-num').value) || 0, 0, 100);
const rgb = caHslToRgb(h, s, l);
caR = rgb.r; caG = rgb.g; caB = rgb.b;
slider.value = (ch === 'h') ? h : (ch === 's') ? s : l;
num.value = (ch === 'h') ? h : (ch === 's') ? s : l;
caUpdate('hsl');
};
slider.addEventListener('input', () => { num.value = slider.value; apply(); });
num.addEventListener('input', () => { slider.value = num.value; apply(); });
});

// Contrast inputs
document.getElementById('ca-fg-color').addEventListener('input', caUpdateContrast);
document.getElementById('ca-bg-color').addEventListener('input', caUpdateContrast);

// ===== Init =====
caUpdate('init');

})();
</script>

</div>

---

## カラーピッカーの使い方

**簡単なガイド**

1. **色を選ぶ** — カラープレビューの下にあるカラー入力ボタンをクリックして色を選択するか、HEXコードを直接入力してください。
2. **スライダーで微調整** — RGBまたはHSLスライダーをドラッグして色を細かく調整できます。数値入力欄への直接入力も可能です。
3. **コードをコピー** — 使用したい形式（HEX / RGB / HSL）の「コピー」ボタンをクリックすれば、クリップボードにコピーされます。
4. **配色パレット** — 補色・類似色・トライアド・分割補色のスウォッチをクリックすると、その色に切り替えられます。
5. **コントラスト確認** — 前景色と背景色を選択して、WCAG AA / AAAの合否を即座に確認しましょう。

---

## 配色の基礎知識

**補色とコントラストの重要性**

補色とは色相環で正反対に位置する色の組み合わせです。例えば青とオレンジ、赤と緑などが代表例で、互いを引き立て合う視覚的な緊張感を生み出します。デザインにおいてアクセントカラーを選ぶ際には補色関係を活用することで、情報が自然と目に飛び込んでくるビジュアルを作ることができます。類似色（アナログカラー）は調和のとれた穏やかな印象を与えるため、背景やグラデーションに適しています。

**アクセシビリティと色のコントラスト**

Webデザインにおいてコントラスト比はアクセシビリティの根幹です。WCAG 2.1ガイドラインでは、通常テキストに対してAA基準（4.5:1以上）、より高いAAA基準（7:1以上）が定められています。特に視覚障害や色覚多様性を持つユーザーにとって、十分なコントラストは可読性を大きく左右します。フォントサイズが18px以上（または太字14px以上）の大きなテキストはAA基準が3:1に緩和されますが、デザイン全体を通して適切なコントラスト比を保つことがユーザー体験の向上につながります。

---

## 関連ツール

> JSONデータを即座に整形・検証 → [JSONフォーマッター](/ja/tools/json-formatter/)

> 文字数・単語数をリアルタイムでカウント → [文字数カウンター](/ja/tools/moji-counter/)

> 安全なパスワードを即座に生成 → [パスワード生成ツール](/ja/tools/password-generator/)

> グラデーションをビジュアルで作成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/) — 美しいCSSグラデーションを視覚的に生成

> ダミーテキストを生成 → [ダミーテキスト生成ツール](/ja/tools/lorem-ipsum-generator/) — レイアウト確認用のプレースホルダーを即作成

---

**デザイナー・クリエイターの経理を効率化**

クリエイティブな仕事に集中したいのに、請求書作成や経費管理に時間を取られていませんか？クラウド会計ソフト「freee」なら、バックオフィス業務を大幅に削減できます。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
