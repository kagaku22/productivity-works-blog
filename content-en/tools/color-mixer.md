---
title: "Color Mixer - Blend Colors Online"
date: 2025-05-16
description: "Free online color mixer. Blend two or more colors together with adjustable ratios. See the mixed result in real-time with HEX, RGB, and HSL values. Perfect for design."
categories: ["Free Tools"]
tags: ["color mixer", "blend colors", "color tool", "hex", "rgb", "hsl", "design tool"]
slug: "color-mixer"
cover:
  image: "/images/covers/color-mixer.png"
  alt: "Color Mixer - Blend Colors Online"
ShowToc: false
---

<div id="cm-app">

<style>
#cm-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 40px 0;
color: #1a1a2e;
}
#cm-app * { box-sizing: border-box; }

/* Card */
.cm-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 14px;
padding: 22px 24px;
margin-bottom: 20px;
}
.cm-card h3 {
margin: 0 0 16px;
font-size: 15px;
font-weight: 700;
color: #2d3748;
border-bottom: 2px solid #f0f4f8;
padding-bottom: 8px;
}

/* Result hero */
.cm-result-hero {
border-radius: 14px;
padding: 24px;
margin-bottom: 20px;
display: flex;
align-items: center;
gap: 24px;
flex-wrap: wrap;
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
.cm-result-swatch {
width: 120px;
height: 120px;
border-radius: 14px;
border: 4px solid rgba(255,255,255,0.5);
box-shadow: 0 8px 32px rgba(0,0,0,0.25);
flex-shrink: 0;
transition: background 0.2s;
}
.cm-result-info { flex: 1; min-width: 220px; }
.cm-result-label {
color: rgba(255,255,255,0.85);
font-size: 13px;
font-weight: 600;
letter-spacing: .04em;
text-transform: uppercase;
margin-bottom: 6px;
}
.cm-result-hex {
color: #fff;
font-size: 32px;
font-weight: 800;
letter-spacing: .02em;
margin-bottom: 12px;
font-family: 'Courier New', monospace;
}
.cm-codes { display: flex; flex-wrap: wrap; gap: 8px; }
.cm-code-badge {
background: rgba(255,255,255,0.18);
border: 1px solid rgba(255,255,255,0.35);
border-radius: 8px;
padding: 6px 12px;
color: #fff;
font-size: 12px;
font-family: 'Courier New', monospace;
cursor: pointer;
transition: background 0.15s;
display: flex;
align-items: center;
gap: 6px;
}
.cm-code-badge:hover { background: rgba(255,255,255,0.3); }
.cm-copy-icon { font-size: 11px; opacity: 0.8; }
.cm-copied { background: rgba(72,199,142,0.5) !important; }

/* Color inputs */
.cm-colors-grid {
display: flex;
flex-direction: column;
gap: 14px;
}
.cm-color-row {
display: flex;
align-items: center;
gap: 12px;
flex-wrap: wrap;
padding: 14px;
background: #f8fafc;
border-radius: 10px;
border: 1px solid #e8edf2;
position: relative;
}
.cm-color-row.cm-removing {
opacity: 0;
transition: opacity 0.2s;
}
.cm-color-swatch-wrap {
display: flex;
align-items: center;
gap: 8px;
}
.cm-native-picker {
width: 48px;
height: 48px;
border: none;
border-radius: 10px;
padding: 2px;
cursor: pointer;
background: none;
flex-shrink: 0;
}
.cm-hex-input {
width: 100px;
padding: 8px 10px;
border: 1px solid #cbd5e0;
border-radius: 8px;
font-size: 13px;
font-family: 'Courier New', monospace;
color: #2d3748;
background: #fff;
transition: border-color 0.15s;
}
.cm-hex-input:focus { outline: none; border-color: #667eea; }
.cm-hex-input.cm-invalid { border-color: #fc8181; background: #fff5f5; }

/* Ratio */
.cm-ratio-wrap {
flex: 1;
min-width: 160px;
display: flex;
align-items: center;
gap: 8px;
}
.cm-ratio-label {
font-size: 12px;
color: #718096;
white-space: nowrap;
}
.cm-ratio-slider {
flex: 1;
accent-color: #667eea;
height: 4px;
cursor: pointer;
}
.cm-ratio-num {
width: 44px;
padding: 4px 6px;
border: 1px solid #cbd5e0;
border-radius: 6px;
font-size: 12px;
text-align: center;
color: #2d3748;
background: #fff;
}
.cm-ratio-num:focus { outline: none; border-color: #667eea; }

/* Remove button */
.cm-remove-btn {
width: 28px;
height: 28px;
border-radius: 50%;
border: 1px solid #e2e8f0;
background: #fff;
color: #a0aec0;
cursor: pointer;
font-size: 16px;
display: flex;
align-items: center;
justify-content: center;
flex-shrink: 0;
transition: background 0.15s, color 0.15s;
line-height: 1;
padding: 0;
}
.cm-remove-btn:hover { background: #fed7d7; color: #e53e3e; border-color: #fc8181; }

/* Add button */
.cm-add-btn {
display: flex;
align-items: center;
gap: 8px;
padding: 10px 18px;
background: #fff;
border: 2px dashed #cbd5e0;
border-radius: 10px;
color: #667eea;
font-size: 14px;
font-weight: 600;
cursor: pointer;
transition: border-color 0.15s, background 0.15s;
width: 100%;
justify-content: center;
}
.cm-add-btn:hover { border-color: #667eea; background: #f0f0ff; }
.cm-add-btn:disabled { opacity: 0.4; cursor: not-allowed; }

/* Ratio bar */
.cm-ratio-bar {
display: flex;
height: 12px;
border-radius: 8px;
overflow: hidden;
margin-bottom: 6px;
border: 1px solid #e2e8f0;
}
.cm-ratio-bar-seg {
transition: width 0.2s, background 0.2s;
height: 100%;
}
.cm-ratio-total {
font-size: 12px;
color: #a0aec0;
text-align: right;
}
.cm-ratio-total.cm-over { color: #e53e3e; font-weight: 700; }

/* Tint/Shade */
.cm-ts-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 560px) { .cm-ts-grid { grid-template-columns: 1fr; } }
.cm-ts-label {
font-size: 13px;
font-weight: 600;
color: #4a5568;
margin-bottom: 8px;
}
.cm-ts-swatches {
display: flex;
gap: 4px;
flex-wrap: wrap;
}
.cm-ts-swatch {
width: 36px;
height: 36px;
border-radius: 6px;
cursor: pointer;
border: 2px solid transparent;
transition: transform 0.1s, border-color 0.15s;
flex-shrink: 0;
position: relative;
}
.cm-ts-swatch:hover { transform: scale(1.12); border-color: #667eea; }
.cm-ts-swatch[title]:hover::after {
content: attr(title);
position: absolute;
bottom: calc(100% + 4px);
left: 50%;
transform: translateX(-50%);
background: #2d3748;
color: #fff;
font-size: 10px;
padding: 2px 6px;
border-radius: 4px;
white-space: nowrap;
pointer-events: none;
z-index: 10;
}

/* Complementary */
.cm-comp-row {
display: flex;
align-items: center;
gap: 14px;
flex-wrap: wrap;
}
.cm-comp-swatch {
width: 56px;
height: 56px;
border-radius: 10px;
cursor: pointer;
border: 2px solid #e2e8f0;
transition: transform 0.1s, border-color 0.15s;
flex-shrink: 0;
}
.cm-comp-swatch:hover { transform: scale(1.08); border-color: #667eea; }
.cm-comp-info { flex: 1; }
.cm-comp-hex {
font-family: 'Courier New', monospace;
font-size: 14px;
font-weight: 700;
color: #2d3748;
}
.cm-comp-desc { font-size: 12px; color: #718096; margin-top: 2px; }

/* History */
.cm-history-row {
display: flex;
gap: 8px;
flex-wrap: wrap;
align-items: center;
}
.cm-history-swatch {
width: 36px;
height: 36px;
border-radius: 8px;
cursor: pointer;
border: 2px solid transparent;
transition: transform 0.1s, border-color 0.15s;
flex-shrink: 0;
position: relative;
}
.cm-history-swatch:hover { transform: scale(1.15); border-color: #667eea; }
.cm-history-empty { font-size: 13px; color: #a0aec0; }

/* Buttons row */
.cm-btn-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-top: 10px;
}
.cm-btn {
padding: 9px 18px;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
border: 1px solid transparent;
transition: background 0.15s, color 0.15s;
}
.cm-btn-primary {
background: #667eea;
color: #fff;
border-color: #667eea;
}
.cm-btn-primary:hover { background: #5a67d8; }
.cm-btn-secondary {
background: #fff;
color: #4a5568;
border-color: #cbd5e0;
}
.cm-btn-secondary:hover { background: #f7fafc; }

@media (max-width: 480px) {
.cm-result-hex { font-size: 24px; }
.cm-result-swatch { width: 80px; height: 80px; }
}
</style>

<!-- Result Hero -->
<div class="cm-result-hero" id="cm-hero">
<div class="cm-result-swatch" id="cm-result-swatch"></div>
<div class="cm-result-info">
<div class="cm-result-label">Mixed Color</div>
<div class="cm-result-hex" id="cm-result-hex">#7B6FBD</div>
<div class="cm-codes">
<span class="cm-code-badge" id="cm-badge-hex" title="Click to copy HEX"><span id="cm-val-hex">#7B6FBD</span><span class="cm-copy-icon">&#x2398;</span></span>
<span class="cm-code-badge" id="cm-badge-rgb" title="Click to copy RGB"><span id="cm-val-rgb">rgb(123, 111, 189)</span><span class="cm-copy-icon">&#x2398;</span></span>
<span class="cm-code-badge" id="cm-badge-hsl" title="Click to copy HSL"><span id="cm-val-hsl">hsl(248, 35%, 59%)</span><span class="cm-copy-icon">&#x2398;</span></span>
</div>
</div>
</div>

<!-- Color Inputs -->
<div class="cm-card">
<h3>Colors to Mix</h3>
<div class="cm-colors-grid" id="cm-colors-grid"></div>
<div style="margin-top:12px;">
<button class="cm-add-btn" id="cm-add-btn">&#43; Add Another Color (up to 5)</button>
</div>
<div style="margin-top:16px;">
<div class="cm-ratio-bar" id="cm-ratio-bar"></div>
<div class="cm-ratio-total" id="cm-ratio-total">Total: 100%</div>
</div>
</div>

<!-- Tint & Shade -->
<div class="cm-card">
<h3>Tints &amp; Shades</h3>
<div class="cm-ts-grid">
<div>
<div class="cm-ts-label">Tints (+ White)</div>
<div class="cm-ts-swatches" id="cm-tints"></div>
</div>
<div>
<div class="cm-ts-label">Shades (+ Black)</div>
<div class="cm-ts-swatches" id="cm-shades"></div>
</div>
</div>
</div>

<!-- Complementary -->
<div class="cm-card">
<h3>Complementary Color</h3>
<div class="cm-comp-row">
<div class="cm-comp-swatch" id="cm-comp-swatch"></div>
<div class="cm-comp-info">
<div class="cm-comp-hex" id="cm-comp-hex">#8D7F3B</div>
<div class="cm-comp-desc">Opposite on the color wheel — great for contrast &amp; accents</div>
</div>
<div>
<button class="cm-btn cm-btn-secondary" id="cm-use-comp">Use as Color 1</button>
</div>
</div>
</div>

<!-- History -->
<div class="cm-card">
<h3>Color History</h3>
<div class="cm-history-row" id="cm-history-row">
<span class="cm-history-empty">Mix colors to build history...</span>
</div>
<div class="cm-btn-row">
<button class="cm-btn cm-btn-secondary" id="cm-clear-history">Clear History</button>
</div>
</div>

<script>
(function() {
'use strict';

// ===== State =====
var colors = [
{ hex: '#667eea', ratio: 50 },
{ hex: '#f093fb', ratio: 50 }
];
var history = [];
var MAX_COLORS = 5;
var MAX_HISTORY = 12;

// ===== Utilities =====
function hexToRgb(hex) {
var h = hex.replace('#', '');
if (h.length === 3) h = h[0]+h[0]+h[1]+h[1]+h[2]+h[2];
if (h.length !== 6) return null;
var n = parseInt(h, 16);
if (isNaN(n)) return null;
return { r: (n >> 16) & 255, g: (n >> 8) & 255, b: n & 255 };
}

function rgbToHex(r, g, b) {
return '#' + [r,g,b].map(function(v) {
return Math.round(v).toString(16).padStart(2,'0');
}).join('').toUpperCase();
}

function rgbToHsl(r, g, b) {
r /= 255; g /= 255; b /= 255;
var max = Math.max(r,g,b), min = Math.min(r,g,b);
var h, s, l = (max+min)/2;
if (max === min) { h = s = 0; }
else {
var d = max - min;
s = l > 0.5 ? d/(2-max-min) : d/(max+min);
switch(max) {
case r: h = ((g-b)/d + (g<b?6:0))/6; break;
case g: h = ((b-r)/d + 2)/6; break;
default: h = ((r-g)/d + 4)/6;
}
}
return { h: Math.round(h*360), s: Math.round(s*100), l: Math.round(l*100) };
}

function clamp(v, lo, hi) { return Math.max(lo, Math.min(hi, v)); }

function isValidHex(s) { return /^#?[0-9A-Fa-f]{6}$/.test(s.trim()); }

function normalizeHex(s) {
s = s.trim().replace(/^#/,'');
if (s.length === 3) s = s[0]+s[0]+s[1]+s[1]+s[2]+s[2];
return '#' + s.toUpperCase();
}

function mixColors(colorsArr) {
var total = colorsArr.reduce(function(a,c){ return a+c.ratio; }, 0);
if (total === 0) return { r:128, g:128, b:128 };
var r=0, g=0, b=0;
colorsArr.forEach(function(c) {
var rgb = hexToRgb(c.hex);
if (!rgb) return;
var w = c.ratio / total;
r += rgb.r * w;
g += rgb.g * w;
b += rgb.b * w;
});
return { r: Math.round(r), g: Math.round(g), b: Math.round(b) };
}

function complementaryHex(hex) {
var rgb = hexToRgb(hex);
if (!rgb) return '#888888';
var hsl = rgbToHsl(rgb.r, rgb.g, rgb.b);
var ch = (hsl.h + 180) % 360;
return hslToHex(ch, hsl.s, hsl.l);
}

function hslToHex(h, s, l) {
s /= 100; l /= 100;
var c = (1 - Math.abs(2*l-1)) * s;
var x = c * (1 - Math.abs((h/60) % 2 - 1));
var m = l - c/2;
var r,g,b;
if (h<60){r=c;g=x;b=0;}
else if(h<120){r=x;g=c;b=0;}
else if(h<180){r=0;g=c;b=x;}
else if(h<240){r=0;g=x;b=c;}
else if(h<300){r=x;g=0;b=c;}
else{r=c;g=0;b=x;}
return rgbToHex(Math.round((r+m)*255), Math.round((g+m)*255), Math.round((b+m)*255));
}

function blendWithWhite(hex, t) {
var rgb = hexToRgb(hex);
if (!rgb) return '#ffffff';
return rgbToHex(
Math.round(rgb.r + (255-rgb.r)*t),
Math.round(rgb.g + (255-rgb.g)*t),
Math.round(rgb.b + (255-rgb.b)*t)
);
}

function blendWithBlack(hex, t) {
var rgb = hexToRgb(hex);
if (!rgb) return '#000000';
return rgbToHex(
Math.round(rgb.r*(1-t)),
Math.round(rgb.g*(1-t)),
Math.round(rgb.b*(1-t))
);
}

function copyText(text, badge) {
navigator.clipboard.writeText(text).then(function() {
badge.classList.add('cm-copied');
setTimeout(function(){ badge.classList.remove('cm-copied'); }, 1200);
}).catch(function() {
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
badge.classList.add('cm-copied');
setTimeout(function(){ badge.classList.remove('cm-copied'); }, 1200);
});
}

// ===== Render color rows =====
function renderColorRows() {
var grid = document.getElementById('cm-colors-grid');
grid.innerHTML = '';
colors.forEach(function(c, i) {
var row = document.createElement('div');
row.className = 'cm-color-row';
row.setAttribute('data-index', i);

// Native picker
var picker = document.createElement('input');
picker.type = 'color';
picker.className = 'cm-native-picker';
picker.value = c.hex.toUpperCase();
picker.title = 'Pick color ' + (i+1);

// Hex input
var hexInput = document.createElement('input');
hexInput.type = 'text';
hexInput.className = 'cm-hex-input';
hexInput.value = c.hex.toUpperCase();
hexInput.maxLength = 7;
hexInput.placeholder = '#RRGGBB';

// Sync picker -> hex
picker.addEventListener('input', function() {
colors[i].hex = picker.value.toUpperCase();
hexInput.value = picker.value.toUpperCase();
hexInput.classList.remove('cm-invalid');
update();
});

// Sync hex -> picker
hexInput.addEventListener('input', function() {
var v = hexInput.value.trim();
if (!v.startsWith('#')) v = '#' + v;
if (isValidHex(v)) {
colors[i].hex = normalizeHex(v);
picker.value = normalizeHex(v).toLowerCase();
hexInput.classList.remove('cm-invalid');
update();
} else {
hexInput.classList.add('cm-invalid');
}
});

var swatchWrap = document.createElement('div');
swatchWrap.className = 'cm-color-swatch-wrap';
swatchWrap.appendChild(picker);
swatchWrap.appendChild(hexInput);

// Ratio controls
var ratioWrap = document.createElement('div');
ratioWrap.className = 'cm-ratio-wrap';

var ratioLabel = document.createElement('span');
ratioLabel.className = 'cm-ratio-label';
ratioLabel.textContent = 'Ratio:';

var ratioSlider = document.createElement('input');
ratioSlider.type = 'range';
ratioSlider.className = 'cm-ratio-slider';
ratioSlider.min = 0;
ratioSlider.max = 100;
ratioSlider.value = c.ratio;

var ratioNum = document.createElement('input');
ratioNum.type = 'number';
ratioNum.className = 'cm-ratio-num';
ratioNum.min = 0;
ratioNum.max = 100;
ratioNum.value = c.ratio;

ratioSlider.addEventListener('input', function() {
colors[i].ratio = parseInt(ratioSlider.value) || 0;
ratioNum.value = colors[i].ratio;
update();
});
ratioNum.addEventListener('input', function() {
colors[i].ratio = clamp(parseInt(ratioNum.value) || 0, 0, 100);
ratioSlider.value = colors[i].ratio;
update();
});

ratioWrap.appendChild(ratioLabel);
ratioWrap.appendChild(ratioSlider);
ratioWrap.appendChild(ratioNum);

row.appendChild(swatchWrap);
row.appendChild(ratioWrap);

// Remove button (only if > 2 colors)
if (colors.length > 2) {
var removeBtn = document.createElement('button');
removeBtn.className = 'cm-remove-btn';
removeBtn.title = 'Remove color';
removeBtn.innerHTML = '&times;';
removeBtn.addEventListener('click', function() {
colors.splice(i, 1);
renderColorRows();
update();
});
row.appendChild(removeBtn);
}

grid.appendChild(row);
});

// Add button state
var addBtn = document.getElementById('cm-add-btn');
addBtn.disabled = colors.length >= MAX_COLORS;
}

// ===== Render ratio bar =====
function renderRatioBar() {
var bar = document.getElementById('cm-ratio-bar');
var totalEl = document.getElementById('cm-ratio-total');
var total = colors.reduce(function(a,c){ return a+c.ratio; }, 0);
bar.innerHTML = '';
colors.forEach(function(c) {
var seg = document.createElement('div');
seg.className = 'cm-ratio-bar-seg';
seg.style.width = (total > 0 ? (c.ratio/total*100) : (100/colors.length)) + '%';
seg.style.background = c.hex;
bar.appendChild(seg);
});
totalEl.textContent = 'Total: ' + total + '%';
totalEl.className = 'cm-ratio-total' + (total !== 100 ? ' cm-over' : '');
}

// ===== Render tints & shades =====
function renderTintsShades(resultHex) {
var steps = [0.1, 0.2, 0.35, 0.5, 0.65, 0.8];
var tintsEl = document.getElementById('cm-tints');
var shadesEl = document.getElementById('cm-shades');
tintsEl.innerHTML = '';
shadesEl.innerHTML = '';

steps.forEach(function(t) {
var tintHex = blendWithWhite(resultHex, t);
var ts = document.createElement('div');
ts.className = 'cm-ts-swatch';
ts.style.background = tintHex;
ts.title = tintHex;
ts.addEventListener('click', function() {
addToHistory(resultHex);
colors[0].hex = tintHex;
colors[0].ratio = 100;
if (colors.length > 1) {
colors = colors.slice(0,1);
colors.push({ hex: '#ffffff', ratio: 0 });
}
renderColorRows();
update();
});
tintsEl.appendChild(ts);
});

steps.forEach(function(t) {
var shadeHex = blendWithBlack(resultHex, t);
var ss = document.createElement('div');
ss.className = 'cm-ts-swatch';
ss.style.background = shadeHex;
ss.title = shadeHex;
ss.addEventListener('click', function() {
addToHistory(resultHex);
colors[0].hex = shadeHex;
renderColorRows();
update();
});
shadesEl.appendChild(ss);
});
}

// ===== Render complementary =====
function renderComplementary(resultHex) {
var compHex = complementaryHex(resultHex);
document.getElementById('cm-comp-swatch').style.background = compHex;
document.getElementById('cm-comp-hex').textContent = compHex;
document.getElementById('cm-use-comp').onclick = function() {
colors[0].hex = compHex;
document.querySelector('[data-index="0"] input[type="color"]') && (document.querySelector('[data-index="0"] input[type="color"]').value = compHex.toLowerCase());
renderColorRows();
update();
};
}

// ===== History =====
function addToHistory(hex) {
if (history.length && history[0] === hex) return;
history = history.filter(function(h){ return h !== hex; });
history.unshift(hex);
if (history.length > MAX_HISTORY) history = history.slice(0, MAX_HISTORY);
renderHistory();
}

function renderHistory() {
var row = document.getElementById('cm-history-row');
row.innerHTML = '';
if (!history.length) {
var empty = document.createElement('span');
empty.className = 'cm-history-empty';
empty.textContent = 'Mix colors to build history...';
row.appendChild(empty);
return;
}
history.forEach(function(hex) {
var sw = document.createElement('div');
sw.className = 'cm-history-swatch';
sw.style.background = hex;
sw.title = hex;
sw.addEventListener('click', function() {
colors[0].hex = hex;
renderColorRows();
update();
});
row.appendChild(sw);
});
}

// ===== Main update =====
var lastResultHex = '';
function update() {
var validColors = colors.filter(function(c){ return hexToRgb(c.hex); });
var rgb = mixColors(validColors.length ? validColors : colors);
var hex = rgbToHex(rgb.r, rgb.g, rgb.b);
var hsl = rgbToHsl(rgb.r, rgb.g, rgb.b);

// Result hero
document.getElementById('cm-result-swatch').style.background = hex;
document.getElementById('cm-result-hex').textContent = hex;
document.getElementById('cm-val-hex').textContent = hex;
document.getElementById('cm-val-rgb').textContent = 'rgb(' + rgb.r + ', ' + rgb.g + ', ' + rgb.b + ')';
document.getElementById('cm-val-hsl').textContent = 'hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%)';

// Hero gradient follows mix
var heroColors = colors.map(function(c){ return c.hex; });
document.getElementById('cm-hero').style.background =
'linear-gradient(135deg, ' + heroColors.join(', ') + ')';

renderRatioBar();
renderTintsShades(hex);
renderComplementary(hex);

// History: add when result changes
if (hex !== lastResultHex) {
addToHistory(hex);
lastResultHex = hex;
}
}

// ===== Copy badges =====
document.getElementById('cm-badge-hex').addEventListener('click', function() {
copyText(document.getElementById('cm-val-hex').textContent, this);
});
document.getElementById('cm-badge-rgb').addEventListener('click', function() {
copyText(document.getElementById('cm-val-rgb').textContent, this);
});
document.getElementById('cm-badge-hsl').addEventListener('click', function() {
copyText(document.getElementById('cm-val-hsl').textContent, this);
});

// ===== Add color =====
document.getElementById('cm-add-btn').addEventListener('click', function() {
if (colors.length >= MAX_COLORS) return;
colors.push({ hex: '#' + Math.floor(Math.random()*0xffffff).toString(16).padStart(6,'0').toUpperCase(), ratio: 20 });
renderColorRows();
update();
});

// ===== Clear history =====
document.getElementById('cm-clear-history').addEventListener('click', function() {
history = [];
renderHistory();
});

// ===== Init =====
renderColorRows();
update();

})();
</script>

</div>

## How to Use the Color Mixer

**Select colors**: Click the color swatch (left of each row) to open the browser's native color picker, or type a HEX code directly into the input field. Up to 5 colors can be mixed simultaneously.

**Adjust ratios**: Drag the slider or type a number for each color's ratio. The ratio bar at the bottom gives a visual breakdown. Ratios don't have to add to 100 — the tool normalizes them automatically to calculate the weighted mix.

**Add more colors**: Click **+ Add Another Color** to add a third, fourth, or fifth color to the mix.

**Copy values**: Click any of the HEX, RGB, or HSL badges in the result panel to copy that color value to your clipboard.

**Tints & Shades**: The Tints panel shows the mixed color blended with white (lighter versions); the Shades panel shows it blended with black (darker versions). Click any swatch to use it.

**Complementary color**: The tool automatically calculates the color directly opposite on the color wheel. Click **Use as Color 1** to swap it into the mix.

**Color history**: Every unique mixed result is saved automatically. Click any history swatch to reload it as your first color input.

## Color Mixing Tips

**Why ratios matter**: A 90/10 mix produces a very different result from 60/40. Use the ratio bar to see proportions at a glance — small ratio changes near one extreme shift the result color dramatically.

**Start with two, then add**: Build complex mixes gradually. Start with your two dominant colors, confirm the mid-tone, then add a third color at a low ratio (10–20%) to add warmth or coolness without overpowering the blend.

**Complementary for contrast**: If your mixed color will appear alongside text or UI elements, the complementary suggestion gives you a mathematically opposite hue — ideal for accent buttons, borders, and highlights.

**Tints for UI states**: Design systems often use the same hue at multiple lightness levels for hover, focus, and disabled states. Use the tint generator to instantly derive those variants from your mixed base color.

## Related Tools

> Pick and convert colors visually → [Color Picker](/tools/color-picker/)

> Generate full color palettes → [Color Palette Generator](/tools/color-palette-generator/)

> Check color contrast ratios → [Color Contrast Checker](/tools/color-contrast-checker/)
