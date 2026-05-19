---
title: "Color Picker & Converter - Free Online Color Tool"
date: 2025-05-16
description: "Pick colors visually and convert between HEX, RGB, HSL, and HSV. Generate color palettes, check contrast ratios. Free online color tool for designers and developers."
categories: ["Free Tools"]
tags: ["color picker", "hex converter", "rgb", "hsl", "design tool"]
slug: "color-picker"
aliases: ["/tools/rgb-hex-converter/", "/tools/color-converter/", "/tools/rgb-hex-converter/"]
cover:
  image: "/images/covers/color-picker.png"
  alt: "Color Picker"
ShowToc: false
---

<div id="color-app">

<style>
#color-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 40px 0;
}

#color-app * {
box-sizing: border-box;
}

.ca-hero {
background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
border-radius: 16px;
padding: 32px 24px;
margin-bottom: 24px;
display: flex;
align-items: center;
gap: 24px;
flex-wrap: wrap;
}

.ca-preview-wrap {
display: flex;
flex-direction: column;
align-items: center;
gap: 12px;
}

.ca-preview {
width: 140px;
height: 140px;
border-radius: 16px;
border: 4px solid rgba(255,255,255,0.5);
box-shadow: 0 8px 32px rgba(0,0,0,0.25);
background: #3498db;
transition: background 0.15s;
}

.ca-native-input {
width: 60px;
height: 36px;
border: none;
border-radius: 8px;
cursor: pointer;
padding: 2px;
background: rgba(255,255,255,0.2);
}

.ca-native-label {
color: rgba(255,255,255,0.85);
font-size: 12px;
text-align: center;
}

.ca-hero-title {
color: #fff;
}

.ca-hero-title h2 {
margin: 0 0 6px 0;
font-size: 22px;
font-weight: 700;
}

.ca-hero-title p {
margin: 0;
font-size: 14px;
opacity: 0.85;
}

.ca-card {
background: #fff;
border-radius: 14px;
box-shadow: 0 2px 16px rgba(0,0,0,0.08);
padding: 22px 24px;
margin-bottom: 18px;
}

.ca-card h3 {
margin: 0 0 18px 0;
font-size: 15px;
font-weight: 700;
color: #2d3748;
text-transform: uppercase;
letter-spacing: 0.05em;
border-bottom: 2px solid #f0f0f0;
padding-bottom: 10px;
}

/* Formats */
.ca-format-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 14px;
}

.ca-format-label {
width: 44px;
font-size: 13px;
font-weight: 700;
color: #555;
flex-shrink: 0;
}

.ca-format-input {
flex: 1;
padding: 8px 12px;
border: 2px solid #e2e8f0;
border-radius: 8px;
font-size: 14px;
font-family: 'Courier New', monospace;
color: #2d3748;
transition: border-color 0.2s;
min-width: 0;
}

.ca-format-input:focus {
outline: none;
border-color: #667eea;
}

.ca-format-input.invalid {
border-color: #fc5c65;
background: #fff5f5;
}

.ca-copy-btn {
padding: 8px 14px;
background: linear-gradient(135deg, #667eea, #764ba2);
color: #fff;
border: none;
border-radius: 8px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
white-space: nowrap;
transition: opacity 0.2s, transform 0.1s;
flex-shrink: 0;
}

.ca-copy-btn:hover {
opacity: 0.9;
}

.ca-copy-btn:active {
transform: scale(0.96);
}

.ca-copy-btn.copied {
background: linear-gradient(135deg, #48bb78, #38a169);
}

/* Sliders */
.ca-slider-group {
margin-bottom: 16px;
}

.ca-slider-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 8px;
}

.ca-slider-label {
width: 20px;
font-size: 13px;
font-weight: 700;
color: #555;
flex-shrink: 0;
text-align: center;
}

.ca-slider {
flex: 1;
height: 6px;
border-radius: 3px;
-webkit-appearance: none;
appearance: none;
outline: none;
cursor: pointer;
min-width: 0;
}

.ca-slider::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 18px;
height: 18px;
border-radius: 50%;
background: #fff;
border: 2px solid #667eea;
box-shadow: 0 1px 4px rgba(0,0,0,0.2);
cursor: pointer;
}

.ca-slider::-moz-range-thumb {
width: 18px;
height: 18px;
border-radius: 50%;
background: #fff;
border: 2px solid #667eea;
box-shadow: 0 1px 4px rgba(0,0,0,0.2);
cursor: pointer;
}

.ca-slider-num {
width: 54px;
padding: 6px 8px;
border: 2px solid #e2e8f0;
border-radius: 8px;
font-size: 13px;
text-align: center;
color: #2d3748;
font-family: 'Courier New', monospace;
flex-shrink: 0;
}

.ca-slider-num:focus {
outline: none;
border-color: #667eea;
}

/* Slider track colors */
#ca-r-slider { background: linear-gradient(to right, #000, #f00); }
#ca-g-slider { background: linear-gradient(to right, #000, #0f0); }
#ca-b-slider { background: linear-gradient(to right, #000, #00f); }
#ca-h-slider { background: linear-gradient(to right, #f00, #ff0, #0f0, #0ff, #00f, #f0f, #f00); }
#ca-s-slider { background: linear-gradient(to right, #888, #f00); }
#ca-l-slider { background: linear-gradient(to right, #000, #888, #fff); }

/* Palette */
.ca-palette-controls {
display: flex;
gap: 8px;
flex-wrap: wrap;
margin-bottom: 16px;
}

.ca-palette-btn {
padding: 7px 14px;
border: 2px solid #e2e8f0;
border-radius: 20px;
background: #fff;
font-size: 12px;
font-weight: 600;
color: #555;
cursor: pointer;
transition: all 0.2s;
}

.ca-palette-btn:hover,
.ca-palette-btn.active {
border-color: #667eea;
background: #667eea;
color: #fff;
}

.ca-palette-swatches {
display: flex;
gap: 10px;
flex-wrap: wrap;
}

.ca-swatch {
display: flex;
flex-direction: column;
align-items: center;
gap: 5px;
cursor: pointer;
}

.ca-swatch-color {
width: 56px;
height: 56px;
border-radius: 12px;
border: 2px solid rgba(0,0,0,0.08);
box-shadow: 0 2px 8px rgba(0,0,0,0.12);
transition: transform 0.15s;
}

.ca-swatch:hover .ca-swatch-color {
transform: scale(1.08);
}

.ca-swatch-hex {
font-size: 10px;
font-family: 'Courier New', monospace;
color: #666;
}

/* Contrast checker */
.ca-contrast-inputs {
display: flex;
gap: 16px;
margin-bottom: 16px;
flex-wrap: wrap;
}

.ca-contrast-field {
flex: 1;
min-width: 180px;
}

.ca-contrast-field label {
display: block;
font-size: 12px;
font-weight: 700;
color: #555;
margin-bottom: 6px;
text-transform: uppercase;
letter-spacing: 0.04em;
}

.ca-contrast-field input[type="color"] {
width: 100%;
height: 44px;
border: 2px solid #e2e8f0;
border-radius: 10px;
cursor: pointer;
padding: 2px 4px;
}

.ca-contrast-preview {
padding: 16px 20px;
border-radius: 12px;
margin-bottom: 14px;
font-size: 16px;
font-weight: 600;
text-align: center;
transition: all 0.2s;
}

.ca-contrast-results {
display: flex;
gap: 10px;
flex-wrap: wrap;
}

.ca-contrast-badge {
padding: 8px 16px;
border-radius: 20px;
font-size: 13px;
font-weight: 700;
}

.ca-badge-pass {
background: #c6f6d5;
color: #276749;
}

.ca-badge-fail {
background: #fed7d7;
color: #9b2c2c;
}

.ca-contrast-ratio {
font-size: 20px;
font-weight: 800;
color: #2d3748;
margin-bottom: 10px;
}

/* History */
.ca-history-swatches {
display: flex;
gap: 8px;
flex-wrap: wrap;
}

.ca-history-swatch {
width: 40px;
height: 40px;
border-radius: 10px;
border: 2px solid rgba(0,0,0,0.1);
cursor: pointer;
transition: transform 0.15s;
box-shadow: 0 1px 4px rgba(0,0,0,0.1);
}

.ca-history-swatch:hover {
transform: scale(1.12);
}

/* CSS output */
.ca-css-output {
background: #1e1e3f;
border-radius: 10px;
padding: 16px 18px;
font-family: 'Courier New', monospace;
font-size: 13px;
color: #a8b5e8;
line-height: 1.8;
position: relative;
}

.ca-css-comment { color: #636da6; }
.ca-css-prop { color: #7aa0e8; }
.ca-css-value { color: #e8c57a; }

.ca-css-copy-btn {
position: absolute;
top: 10px;
right: 12px;
padding: 5px 12px;
background: rgba(255,255,255,0.1);
color: #a8b5e8;
border: 1px solid rgba(255,255,255,0.15);
border-radius: 6px;
font-size: 11px;
cursor: pointer;
transition: background 0.2s;
}

.ca-css-copy-btn:hover {
background: rgba(255,255,255,0.18);
}

.ca-empty-history {
color: #aaa;
font-size: 13px;
font-style: italic;
}

@media (max-width: 600px) {
.ca-hero {
padding: 22px 16px;
gap: 16px;
}
.ca-preview {
width: 100px;
height: 100px;
}
.ca-card {
padding: 18px 16px;
}
.ca-format-row {
flex-wrap: wrap;
}
.ca-format-input {
width: 100%;
}
.ca-swatch-color {
width: 46px;
height: 46px;
}
.ca-slider-row {
flex-wrap: wrap;
}
}
</style>

<!-- Hero: Preview + Native Picker -->
<div class="ca-hero">
<div class="ca-preview-wrap">
<div class="ca-preview" id="ca-preview"></div>
<input type="color" class="ca-native-input" id="ca-native" value="#3498db" title="Click to open color picker">
<span class="ca-native-label">Click to pick color</span>
</div>
<div class="ca-hero-title">
<h2>Color Picker & Converter</h2>
<p>Pick any color and convert between HEX, RGB, and HSL instantly.<br>Generate palettes, check contrast, and copy CSS code.</p>
</div>
</div>

<!-- Format Inputs -->
<div class="ca-card">
<h3>Color Values</h3>

<div class="ca-format-row">
<span class="ca-format-label">HEX</span>
<input type="text" class="ca-format-input" id="ca-hex" value="#3498db" maxlength="7" spellcheck="false" placeholder="#RRGGBB">
<button class="ca-copy-btn" data-copy="hex">Copy</button>
</div>

<div class="ca-format-row">
<span class="ca-format-label">RGB</span>
<input type="text" class="ca-format-input" id="ca-rgb-text" value="rgb(52, 152, 219)" readonly spellcheck="false">
<button class="ca-copy-btn" data-copy="rgb">Copy</button>
</div>

<div class="ca-format-row">
<span class="ca-format-label">HSL</span>
<input type="text" class="ca-format-input" id="ca-hsl-text" value="hsl(204, 70%, 53%)" readonly spellcheck="false">
<button class="ca-copy-btn" data-copy="hsl">Copy</button>
</div>
</div>

<!-- RGB Sliders -->
<div class="ca-card">
<h3>RGB Sliders</h3>
<div class="ca-slider-group">
<div class="ca-slider-row">
<span class="ca-slider-label" style="color:#e53e3e;">R</span>
<input type="range" class="ca-slider" id="ca-r-slider" min="0" max="255" value="52">
<input type="number" class="ca-slider-num" id="ca-r-num" min="0" max="255" value="52">
</div>
<div class="ca-slider-row">
<span class="ca-slider-label" style="color:#38a169;">G</span>
<input type="range" class="ca-slider" id="ca-g-slider" min="0" max="255" value="152">
<input type="number" class="ca-slider-num" id="ca-g-num" min="0" max="255" value="152">
</div>
<div class="ca-slider-row">
<span class="ca-slider-label" style="color:#3182ce;">B</span>
<input type="range" class="ca-slider" id="ca-b-slider" min="0" max="255" value="219">
<input type="number" class="ca-slider-num" id="ca-b-num" min="0" max="255" value="219">
</div>
</div>
</div>

<!-- HSL Sliders -->
<div class="ca-card">
<h3>HSL Sliders</h3>
<div class="ca-slider-group">
<div class="ca-slider-row">
<span class="ca-slider-label">H</span>
<input type="range" class="ca-slider" id="ca-h-slider" min="0" max="360" value="204">
<input type="number" class="ca-slider-num" id="ca-h-num" min="0" max="360" value="204">
</div>
<div class="ca-slider-row">
<span class="ca-slider-label">S</span>
<input type="range" class="ca-slider" id="ca-s-slider" min="0" max="100" value="70">
<input type="number" class="ca-slider-num" id="ca-s-num" min="0" max="100" value="70">
</div>
<div class="ca-slider-row">
<span class="ca-slider-label">L</span>
<input type="range" class="ca-slider" id="ca-l-slider" min="0" max="100" value="53">
<input type="number" class="ca-slider-num" id="ca-l-num" min="0" max="100" value="53">
</div>
</div>
</div>

<!-- Palette Generator -->
<div class="ca-card">
<h3>Palette Generator</h3>
<div class="ca-palette-controls">
<button class="ca-palette-btn active" data-palette="complementary">Complementary</button>
<button class="ca-palette-btn" data-palette="analogous">Analogous</button>
<button class="ca-palette-btn" data-palette="triadic">Triadic</button>
<button class="ca-palette-btn" data-palette="split">Split-Complementary</button>
</div>
<div class="ca-palette-swatches" id="ca-palette-swatches"></div>
</div>

<!-- Contrast Checker -->
<div class="ca-card">
<h3>Contrast Checker (WCAG)</h3>
<div class="ca-contrast-inputs">
<div class="ca-contrast-field">
<label>Text Color</label>
<input type="color" id="ca-contrast-text-color" value="#ffffff">
</div>
<div class="ca-contrast-field">
<label>Background Color</label>
<input type="color" id="ca-contrast-bg-color" value="#3498db">
</div>
</div>
<div class="ca-contrast-preview" id="ca-contrast-preview">The quick brown fox jumps over the lazy dog</div>
<div class="ca-contrast-ratio" id="ca-contrast-ratio"></div>
<div class="ca-contrast-results" id="ca-contrast-results"></div>
</div>

<!-- Color History -->
<div class="ca-card">
<h3>Color History</h3>
<div class="ca-history-swatches" id="ca-history-swatches">
<span class="ca-empty-history">No colors picked yet.</span>
</div>
</div>

<!-- CSS Output -->
<div class="ca-card">
<h3>CSS Code</h3>
<div class="ca-css-output" id="ca-css-output">
<button class="ca-css-copy-btn" id="ca-css-copy-btn">Copy CSS</button>
<div id="ca-css-code"></div>
</div>
</div>

<script>
(function() {
// --- State ---
var state = { r: 52, g: 152, b: 219 };
var history = [];
var activePalette = 'complementary';
var updating = false;

// --- DOM refs ---
var preview      = document.getElementById('ca-preview');
var nativeInput  = document.getElementById('ca-native');
var hexInput     = document.getElementById('ca-hex');
var rgbText      = document.getElementById('ca-rgb-text');
var hslText      = document.getElementById('ca-hsl-text');
var rSlider      = document.getElementById('ca-r-slider');
var gSlider      = document.getElementById('ca-g-slider');
var bSlider      = document.getElementById('ca-b-slider');
var rNum         = document.getElementById('ca-r-num');
var gNum         = document.getElementById('ca-g-num');
var bNum         = document.getElementById('ca-b-num');
var hSlider      = document.getElementById('ca-h-slider');
var sSlider      = document.getElementById('ca-s-slider');
var lSlider      = document.getElementById('ca-l-slider');
var hNum         = document.getElementById('ca-h-num');
var sNum         = document.getElementById('ca-s-num');
var lNum         = document.getElementById('ca-l-num');
var paletteSwatches = document.getElementById('ca-palette-swatches');
var historySwatches = document.getElementById('ca-history-swatches');
var contrastTextColor = document.getElementById('ca-contrast-text-color');
var contrastBgColor   = document.getElementById('ca-contrast-bg-color');
var contrastPreview   = document.getElementById('ca-contrast-preview');
var contrastRatio     = document.getElementById('ca-contrast-ratio');
var contrastResults   = document.getElementById('ca-contrast-results');
var cssCode           = document.getElementById('ca-css-code');
var cssCopyBtn        = document.getElementById('ca-css-copy-btn');

// --- Color Conversions ---
function clamp(v, mn, mx) { return Math.max(mn, Math.min(mx, v)); }

function rgbToHex(r, g, b) {
return '#' + [r, g, b].map(function(v) {
return ('0' + Math.round(v).toString(16)).slice(-2);
}).join('');
}

function hexToRgb(hex) {
hex = hex.replace(/^#/, '');
if (hex.length === 3) hex = hex.split('').map(function(c) { return c+c; }).join('');
if (hex.length !== 6) return null;
var n = parseInt(hex, 16);
if (isNaN(n)) return null;
return { r: (n >> 16) & 255, g: (n >> 8) & 255, b: n & 255 };
}

function rgbToHsl(r, g, b) {
r /= 255; g /= 255; b /= 255;
var max = Math.max(r, g, b), min = Math.min(r, g, b);
var h, s, l = (max + min) / 2;
if (max === min) {
h = s = 0;
} else {
var d = max - min;
s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
switch (max) {
case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
case g: h = ((b - r) / d + 2) / 6; break;
case b: h = ((r - g) / d + 4) / 6; break;
}
}
return { h: Math.round(h * 360), s: Math.round(s * 100), l: Math.round(l * 100) };
}

function hslToRgb(h, s, l) {
s /= 100; l /= 100;
var c = (1 - Math.abs(2 * l - 1)) * s;
var x = c * (1 - Math.abs((h / 60) % 2 - 1));
var m = l - c / 2;
var r1, g1, b1;
if      (h < 60)  { r1=c; g1=x; b1=0; }
else if (h < 120) { r1=x; g1=c; b1=0; }
else if (h < 180) { r1=0; g1=c; b1=x; }
else if (h < 240) { r1=0; g1=x; b1=c; }
else if (h < 300) { r1=x; g1=0; b1=c; }
else              { r1=c; g1=0; b1=x; }
return {
r: Math.round((r1 + m) * 255),
g: Math.round((g1 + m) * 255),
b: Math.round((b1 + m) * 255)
};
}

function hslStringFromRgb(r, g, b) {
var hsl = rgbToHsl(r, g, b);
return 'hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%)';
}

// --- Update all UI from state ---
function updateAll(source) {
if (updating) return;
updating = true;

var r = state.r, g = state.g, b = state.b;
var hex = rgbToHex(r, g, b);
var hsl = rgbToHsl(r, g, b);

// Preview
preview.style.background = hex;

// Native
if (source !== 'native') nativeInput.value = hex;

// HEX field
if (source !== 'hex') {
hexInput.value = hex;
hexInput.classList.remove('invalid');
}

// RGB text
rgbText.value = 'rgb(' + r + ', ' + g + ', ' + b + ')';

// HSL text
hslText.value = 'hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%)';

// RGB sliders + nums
if (source !== 'rgb') {
rSlider.value = r; rNum.value = r;
gSlider.value = g; gNum.value = g;
bSlider.value = b; bNum.value = b;
}

// HSL sliders + nums
if (source !== 'hsl') {
hSlider.value = hsl.h; hNum.value = hsl.h;
sSlider.value = hsl.s; sNum.value = hsl.s;
lSlider.value = hsl.l; lNum.value = hsl.l;
}

// Update HSL slider track colors based on current values
sSlider.style.background = 'linear-gradient(to right, hsl(' + hsl.h + ',0%,' + hsl.l + '%), hsl(' + hsl.h + ',100%,' + hsl.l + '%))';
lSlider.style.background = 'linear-gradient(to right, hsl(' + hsl.h + ',' + hsl.s + '%,0%), hsl(' + hsl.h + ',' + hsl.s + '%,50%), hsl(' + hsl.h + ',' + hsl.s + '%,100%))';

// CSS output
cssCode.innerHTML =
'<span class="ca-css-comment">/* Current color */</span>\n' +
'<span class="ca-css-prop">color</span>: <span class="ca-css-value">' + hex + '</span>;\n' +
'<span class="ca-css-prop">background-color</span>: <span class="ca-css-value">rgb(' + r + ', ' + g + ', ' + b + ')</span>;\n' +
'<span class="ca-css-prop">border-color</span>: <span class="ca-css-value">hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%)</span>;';

// Palette
renderPalette();

// Sync contrast bg to current color on native/hex change
if (source === 'native' || source === 'hex') {
contrastBgColor.value = hex;
updateContrast();
}

updating = false;
}

// --- Palette Generator ---
function hslSwatchHex(h, s, l) {
h = ((h % 360) + 360) % 360;
var rgb = hslToRgb(h, s, l);
return rgbToHex(rgb.r, rgb.g, rgb.b);
}

function renderPalette() {
var hsl = rgbToHsl(state.r, state.g, state.b);
var h = hsl.h, s = hsl.s, l = hsl.l;
var colors = [];

switch (activePalette) {
case 'complementary':
colors = [
hslSwatchHex(h, s, l),
hslSwatchHex(h + 30, s, l),
hslSwatchHex(h + 180, s, l),
hslSwatchHex(h + 180, Math.max(s-15,0), l + 10 > 90 ? l : l + 10),
hslSwatchHex(h + 150, s, l)
];
break;
case 'analogous':
colors = [
hslSwatchHex(h - 40, s, l),
hslSwatchHex(h - 20, s, l),
hslSwatchHex(h, s, l),
hslSwatchHex(h + 20, s, l),
hslSwatchHex(h + 40, s, l)
];
break;
case 'triadic':
colors = [
hslSwatchHex(h, s, l),
hslSwatchHex(h + 60, s, l),
hslSwatchHex(h + 120, s, l),
hslSwatchHex(h + 180, s, l),
hslSwatchHex(h + 240, s, l)
];
break;
case 'split':
colors = [
hslSwatchHex(h, s, l),
hslSwatchHex(h + 150, s, l),
hslSwatchHex(h + 180, s, l),
hslSwatchHex(h + 210, s, l),
hslSwatchHex(h + 90, s, Math.min(l + 15, 90))
];
break;
}

paletteSwatches.innerHTML = '';
colors.forEach(function(hex) {
var swatch = document.createElement('div');
swatch.className = 'ca-swatch';
swatch.title = hex + ' — click to select';
swatch.innerHTML =
'<div class="ca-swatch-color" style="background:' + hex + '"></div>' +
'<span class="ca-swatch-hex">' + hex.toUpperCase() + '</span>';
swatch.addEventListener('click', function() {
var rgb = hexToRgb(hex);
if (rgb) { state.r = rgb.r; state.g = rgb.g; state.b = rgb.b; addHistory(hex); updateAll('hex'); }
});
paletteSwatches.appendChild(swatch);
});
}

// --- Contrast Checker ---
function luminance(r, g, b) {
var vals = [r, g, b].map(function(v) {
v /= 255;
return v <= 0.03928 ? v / 12.92 : Math.pow((v + 0.055) / 1.055, 2.4);
});
return 0.2126 * vals[0] + 0.7152 * vals[1] + 0.0722 * vals[2];
}

function contrastRatioFn(r1, g1, b1, r2, g2, b2) {
var l1 = luminance(r1, g1, b1);
var l2 = luminance(r2, g2, b2);
var bright = Math.max(l1, l2);
var dark   = Math.min(l1, l2);
return (bright + 0.05) / (dark + 0.05);
}

function updateContrast() {
var tc = hexToRgb(contrastTextColor.value);
var bc = hexToRgb(contrastBgColor.value);
if (!tc || !bc) return;

contrastPreview.style.color = contrastTextColor.value;
contrastPreview.style.background = contrastBgColor.value;

var ratio = contrastRatioFn(tc.r, tc.g, tc.b, bc.r, bc.g, bc.b);
var ratioStr = ratio.toFixed(2);

contrastRatio.textContent = 'Contrast Ratio: ' + ratioStr + ':1';

var aaLarge  = ratio >= 3;
var aaSmall  = ratio >= 4.5;
var aaaLarge = ratio >= 4.5;
var aaaSmall = ratio >= 7;

contrastResults.innerHTML =
badge('AA Normal Text',   aaSmall) +
badge('AA Large Text',    aaLarge) +
badge('AAA Normal Text',  aaaSmall) +
badge('AAA Large Text',   aaaLarge);
}

function badge(label, pass) {
return '<span class="ca-contrast-badge ' + (pass ? 'ca-badge-pass' : 'ca-badge-fail') + '">' +
label + ': ' + (pass ? 'PASS' : 'FAIL') + '</span>';
}

contrastTextColor.addEventListener('input', updateContrast);
contrastBgColor.addEventListener('input', updateContrast);

// --- Color History ---
function addHistory(hex) {
hex = hex.toLowerCase();
history = history.filter(function(h) { return h !== hex; });
history.unshift(hex);
if (history.length > 10) history.pop();
renderHistory();
}

function renderHistory() {
if (history.length === 0) {
historySwatches.innerHTML = '<span class="ca-empty-history">No colors picked yet.</span>';
return;
}
historySwatches.innerHTML = '';
history.forEach(function(hex) {
var sw = document.createElement('div');
sw.className = 'ca-history-swatch';
sw.style.background = hex;
sw.title = hex.toUpperCase();
sw.addEventListener('click', function() {
var rgb = hexToRgb(hex);
if (rgb) { state.r = rgb.r; state.g = rgb.g; state.b = rgb.b; updateAll('hex'); }
});
historySwatches.appendChild(sw);
});
}

// --- Copy buttons ---
document.querySelectorAll('.ca-copy-btn[data-copy]').forEach(function(btn) {
btn.addEventListener('click', function() {
var type = btn.getAttribute('data-copy');
var text = '';
if (type === 'hex') text = hexInput.value;
if (type === 'rgb') text = rgbText.value;
if (type === 'hsl') text = hslText.value;
copyText(text, btn);
});
});

cssCopyBtn.addEventListener('click', function() {
var r = state.r, g = state.g, b = state.b;
var hsl = rgbToHsl(r, g, b);
var text =
'color: ' + rgbToHex(r,g,b) + ';\n' +
'background-color: rgb(' + r + ', ' + g + ', ' + b + ');\n' +
'border-color: hsl(' + hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%);';
copyText(text, cssCopyBtn);
});

function copyText(text, btn) {
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() { flashCopied(btn); });
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
flashCopied(btn);
}
}

function flashCopied(btn) {
var orig = btn.textContent;
btn.classList.add('copied');
btn.textContent = 'Copied!';
setTimeout(function() {
btn.classList.remove('copied');
btn.textContent = orig;
}, 1500);
}

// --- Input event listeners ---

// Native color picker
nativeInput.addEventListener('input', function() {
var rgb = hexToRgb(nativeInput.value);
if (rgb) {
state.r = rgb.r; state.g = rgb.g; state.b = rgb.b;
addHistory(nativeInput.value);
updateAll('native');
}
});

// HEX text input
hexInput.addEventListener('input', function() {
var val = hexInput.value.trim();
if (!val.startsWith('#')) val = '#' + val;
var rgb = hexToRgb(val);
if (rgb) {
state.r = rgb.r; state.g = rgb.g; state.b = rgb.b;
hexInput.classList.remove('invalid');
updateAll('hex');
} else {
hexInput.classList.add('invalid');
}
});

hexInput.addEventListener('blur', function() {
addHistory(rgbToHex(state.r, state.g, state.b));
});

// RGB sliders
function bindRgbSlider(slider, num, channel) {
slider.addEventListener('input', function() {
state[channel] = clamp(parseInt(slider.value) || 0, 0, 255);
num.value = state[channel];
updateAll('rgb');
});
num.addEventListener('input', function() {
state[channel] = clamp(parseInt(num.value) || 0, 0, 255);
slider.value = state[channel];
updateAll('rgb');
});
num.addEventListener('blur', function() {
addHistory(rgbToHex(state.r, state.g, state.b));
});
}

bindRgbSlider(rSlider, rNum, 'r');
bindRgbSlider(gSlider, gNum, 'g');
bindRgbSlider(bSlider, bNum, 'b');

// HSL sliders
function bindHslSlider(slider, num, channel, max) {
function apply() {
var hsl = rgbToHsl(state.r, state.g, state.b);
hsl[channel] = clamp(parseInt(slider.value) || 0, 0, max);
var rgb = hslToRgb(hsl.h, hsl.s, hsl.l);
state.r = rgb.r; state.g = rgb.g; state.b = rgb.b;
updateAll('hsl');
}
slider.addEventListener('input', function() { num.value = slider.value; apply(); });
num.addEventListener('input', function() { slider.value = num.value; apply(); });
num.addEventListener('blur', function() { addHistory(rgbToHex(state.r, state.g, state.b)); });
}

bindHslSlider(hSlider, hNum, 'h', 360);
bindHslSlider(sSlider, sNum, 's', 100);
bindHslSlider(lSlider, lNum, 'l', 100);

// Palette buttons
document.querySelectorAll('.ca-palette-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('.ca-palette-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
activePalette = btn.getAttribute('data-palette');
renderPalette();
});
});

// --- Init ---
updateAll('init');
updateContrast();

})();
</script>

</div>

## How to Use This Color Picker

**Pick a color** by clicking the color swatch in the top panel to open your browser's native color picker, or type a HEX code directly into the HEX field. All other values update instantly.

**Adjust with sliders**: Use the RGB or HSL sliders to fine-tune your color. RGB sliders control Red, Green, and Blue channels (0–255 each). HSL sliders control Hue (0–360°), Saturation (0–100%), and Lightness (0–100%).

**Copy values**: Click the Copy button next to HEX, RGB, or HSL to copy that format to your clipboard. Use the Copy CSS button at the bottom to grab ready-to-paste CSS declarations.

**Generate a palette**: Select a harmony type — Complementary, Analogous, Triadic, or Split-Complementary — and click any swatch to switch your active color to that palette entry.

**Check contrast**: Enter a text color and background color in the Contrast Checker. The tool calculates the contrast ratio and shows WCAG AA and AAA pass/fail results for normal and large text.

**Color history**: The last 10 colors you've picked appear as clickable swatches. Click any swatch to return to that color instantly.

## Color Theory Basics

Color harmony is the principle of arranging colors that are pleasing to the eye based on their relationships on the color wheel. Complementary colors sit directly opposite each other (e.g., blue and orange) and create high visual tension, making them ideal for call-to-action buttons and bold design accents. Analogous colors sit adjacent on the wheel and create a cohesive, low-contrast palette suited for backgrounds and subtle UI themes. Triadic schemes use three colors equally spaced at 120° apart, offering balanced contrast with more variety. Split-complementary is a softer alternative to the true complementary pairing, using one base color and two colors flanking its complement.

Contrast and accessibility go hand in hand. WCAG (Web Content Accessibility Guidelines) defines minimum contrast ratios to ensure readable text for people with low vision or color blindness. A ratio of 4.5:1 is required for normal-sized text (Level AA), while 7:1 meets the stricter Level AAA standard. Large text (18pt+ or 14pt bold) has a more lenient threshold of 3:1 for AA. Using the contrast checker built into this tool before publishing your designs helps ensure your color choices are inclusive and meet modern accessibility standards.

## Related Tools

> Format and validate JSON data → [JSON Formatter](/tools/json-formatter/)

> Count words and characters → [Word Counter](/tools/word-counter/)

> Generate secure passwords → [Password Generator](/tools/password-generator/)

> Design with gradients → [CSS Gradient Generator](/tools/css-gradient-generator/) — create beautiful CSS gradients visually

> Need placeholder text? → [Lorem Ipsum Generator](/tools/lorem-ipsum-generator/) — generate filler content for mockups
