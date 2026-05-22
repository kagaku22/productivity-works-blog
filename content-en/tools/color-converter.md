---
title: "Color Converter — HEX RGB HSL CMYK"
date: 2025-05-16
description: "Convert colors between HEX, RGB, HSL, HSV, and CMYK formats instantly. Color picker, shade generator, and complementary color finder. Copy any format with one click."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "color-converter"
ShowToc: false
cover:
  image: "/images/covers/color-converter.png"
  alt: "Color Converter"
---

Convert any color between **HEX, RGB, HSL, HSV/HSB, CMYK**, and CSS named colors instantly. Pick a color, paste a value in any format, and every other format updates live. Generate lighter and darker shades, find the complementary color, and copy any format with one click.

<div id="colconv-app">
<style>
#colconv-app *,
#colconv-app *::before,
#colconv-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#colconv-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f7f8fc;
border-radius: 12px;
padding: 24px;
max-width: 720px;
margin: 0 auto;
}
#colconv-app h2 {
font-size: 1.3rem;
font-weight: 700;
margin-bottom: 16px;
color: #12122a;
}
#colconv-app h3 {
font-size: 1rem;
font-weight: 600;
margin-bottom: 10px;
color: #12122a;
}

/* Input section */
#colconv-input-row {
display: flex;
flex-wrap: wrap;
gap: 12px;
align-items: center;
margin-bottom: 20px;
background: #fff;
border-radius: 10px;
padding: 16px;
box-shadow: 0 1px 4px rgba(0,0,0,0.07);
}
#colconv-picker-wrap {
display: flex;
flex-direction: column;
align-items: center;
gap: 6px;
}
#colconv-picker-wrap label {
font-size: 0.75rem;
color: #666;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#colconv-picker {
width: 56px;
height: 56px;
border: none;
border-radius: 8px;
cursor: pointer;
padding: 2px;
background: none;
}
#colconv-picker::-webkit-color-swatch-wrapper { padding: 0; border-radius: 6px; }
#colconv-picker::-webkit-color-swatch { border: none; border-radius: 6px; }
#colconv-text-input-wrap {
flex: 1;
min-width: 200px;
display: flex;
flex-direction: column;
gap: 4px;
}
#colconv-text-input-wrap label {
font-size: 0.75rem;
color: #666;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#colconv-raw-input {
width: 100%;
padding: 10px 14px;
border: 1.5px solid #d0d4e8;
border-radius: 8px;
font-size: 1rem;
outline: none;
transition: border-color 0.2s;
background: #fafbff;
}
#colconv-raw-input:focus { border-color: #5b6af0; }
#colconv-error {
font-size: 0.8rem;
color: #e53e3e;
min-height: 18px;
}

/* Swatch + complementary */
#colconv-swatches-row {
display: flex;
flex-wrap: wrap;
gap: 14px;
margin-bottom: 20px;
}
.colconv-swatch-card {
flex: 1;
min-width: 140px;
border-radius: 10px;
overflow: hidden;
box-shadow: 0 1px 4px rgba(0,0,0,0.09);
}
.colconv-swatch-block {
height: 80px;
width: 100%;
transition: background-color 0.25s;
}
.colconv-swatch-label {
background: #fff;
padding: 8px 12px;
font-size: 0.78rem;
color: #555;
font-weight: 500;
}
.colconv-swatch-label span {
display: block;
font-size: 0.85rem;
font-weight: 700;
color: #12122a;
margin-bottom: 2px;
}

/* Format outputs */
#colconv-formats {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(290px, 1fr));
gap: 12px;
margin-bottom: 24px;
}
.colconv-format-card {
background: #fff;
border-radius: 10px;
padding: 12px 14px;
box-shadow: 0 1px 4px rgba(0,0,0,0.07);
display: flex;
align-items: center;
gap: 10px;
}
.colconv-format-label {
font-size: 0.72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #5b6af0;
min-width: 46px;
}
.colconv-format-value {
flex: 1;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 0.88rem;
color: #1a1a2e;
word-break: break-all;
}
.colconv-copy-btn {
background: #f0f2ff;
border: none;
border-radius: 6px;
padding: 5px 10px;
font-size: 0.75rem;
font-weight: 600;
color: #5b6af0;
cursor: pointer;
transition: background 0.15s, color 0.15s;
white-space: nowrap;
}
.colconv-copy-btn:hover { background: #5b6af0; color: #fff; }
.colconv-copy-btn.copied { background: #38a169; color: #fff; }

/* Shades */
#colconv-shades-section {
background: #fff;
border-radius: 10px;
padding: 16px;
box-shadow: 0 1px 4px rgba(0,0,0,0.07);
margin-bottom: 20px;
}
#colconv-shades-grid {
display: flex;
flex-wrap: wrap;
gap: 8px;
}
.colconv-shade-cell {
display: flex;
flex-direction: column;
align-items: center;
gap: 4px;
cursor: pointer;
}
.colconv-shade-block {
width: 48px;
height: 48px;
border-radius: 8px;
border: 1.5px solid rgba(0,0,0,0.08);
transition: transform 0.1s;
}
.colconv-shade-block:hover { transform: scale(1.1); }
.colconv-shade-hex {
font-size: 0.62rem;
font-family: "SFMono-Regular", Consolas, monospace;
color: #555;
}
.colconv-shade-tag {
font-size: 0.6rem;
color: #999;
font-style: italic;
}

/* CSS Named */
#colconv-named-badge {
display: inline-block;
background: #ebf8ff;
color: #2b6cb0;
border-radius: 6px;
padding: 3px 10px;
font-size: 0.82rem;
font-weight: 600;
margin-left: 4px;
}

/* Responsive */
@media (max-width: 480px) {
#colconv-app { padding: 14px; }
#colconv-formats { grid-template-columns: 1fr; }
.colconv-shade-block { width: 38px; height: 38px; }
}
</style>

<h2>Color Converter</h2>

<div id="colconv-input-row">
<div id="colconv-picker-wrap">
<label for="colconv-picker">Picker</label>
<input type="color" id="colconv-picker" value="#5b6af0" title="Pick a color">
</div>
<div id="colconv-text-input-wrap">
<label for="colconv-raw-input">Enter any format (HEX, RGB, HSL, HSV, CMYK, CSS name)</label>
<input type="text" id="colconv-raw-input" value="#5b6af0" placeholder="e.g. #ff6600 or rgb(255,102,0) or coral">
<div id="colconv-error"></div>
</div>
</div>

<div id="colconv-swatches-row">
<div class="colconv-swatch-card">
<div class="colconv-swatch-block" id="colconv-main-swatch"></div>
<div class="colconv-swatch-label"><span>Selected Color</span><span id="colconv-main-hex-label"></span></div>
</div>
<div class="colconv-swatch-card">
<div class="colconv-swatch-block" id="colconv-comp-swatch"></div>
<div class="colconv-swatch-label"><span>Complementary</span><span id="colconv-comp-hex-label"></span></div>
</div>
</div>

<div id="colconv-formats">
<div class="colconv-format-card"><span class="colconv-format-label">HEX</span><span class="colconv-format-value" id="colconv-out-hex"></span><button class="colconv-copy-btn" data-target="colconv-out-hex">Copy</button></div>
<div class="colconv-format-card"><span class="colconv-format-label">RGB</span><span class="colconv-format-value" id="colconv-out-rgb"></span><button class="colconv-copy-btn" data-target="colconv-out-rgb">Copy</button></div>
<div class="colconv-format-card"><span class="colconv-format-label">HSL</span><span class="colconv-format-value" id="colconv-out-hsl"></span><button class="colconv-copy-btn" data-target="colconv-out-hsl">Copy</button></div>
<div class="colconv-format-card"><span class="colconv-format-label">HSV</span><span class="colconv-format-value" id="colconv-out-hsv"></span><button class="colconv-copy-btn" data-target="colconv-out-hsv">Copy</button></div>
<div class="colconv-format-card"><span class="colconv-format-label">CMYK</span><span class="colconv-format-value" id="colconv-out-cmyk"></span><button class="colconv-copy-btn" data-target="colconv-out-cmyk">Copy</button></div>
<div class="colconv-format-card"><span class="colconv-format-label">CSS</span><span class="colconv-format-value" id="colconv-out-css">—</span><button class="colconv-copy-btn" data-target="colconv-out-css">Copy</button></div>
</div>

<div id="colconv-shades-section">
<h3>Lighter &amp; Darker Shades <small style="font-weight:400;color:#888;">(click to apply)</small></h3>
<div id="colconv-shades-grid"></div>
</div>

<script>
(function() {
'use strict';

// ── CSS Named Colors (subset, most common) ──────────────────────────────
const CSS_NAMES = {
aliceblue:'#f0f8ff',antiquewhite:'#faebd7',aqua:'#00ffff',aquamarine:'#7fffd4',
azure:'#f0ffff',beige:'#f5f5dc',bisque:'#ffe4c4',black:'#000000',
blanchedalmond:'#ffebcd',blue:'#0000ff',blueviolet:'#8a2be2',brown:'#a52a2a',
burlywood:'#deb887',cadetblue:'#5f9ea0',chartreuse:'#7fff00',chocolate:'#d2691e',
coral:'#ff7f50',cornflowerblue:'#6495ed',cornsilk:'#fff8dc',crimson:'#dc143c',
cyan:'#00ffff',darkblue:'#00008b',darkcyan:'#008b8b',darkgoldenrod:'#b8860b',
darkgray:'#a9a9a9',darkgreen:'#006400',darkkhaki:'#bdb76b',darkmagenta:'#8b008b',
darkolivegreen:'#556b2f',darkorange:'#ff8c00',darkorchid:'#9932cc',darkred:'#8b0000',
darksalmon:'#e9967a',darkseagreen:'#8fbc8f',darkslateblue:'#483d8b',
darkslategray:'#2f4f4f',darkturquoise:'#00ced1',darkviolet:'#9400d3',
deeppink:'#ff1493',deepskyblue:'#00bfff',dimgray:'#696969',dodgerblue:'#1e90ff',
firebrick:'#b22222',floralwhite:'#fffaf0',forestgreen:'#228b22',fuchsia:'#ff00ff',
gainsboro:'#dcdcdc',ghostwhite:'#f8f8ff',gold:'#ffd700',goldenrod:'#daa520',
gray:'#808080',green:'#008000',greenyellow:'#adff2f',honeydew:'#f0fff0',
hotpink:'#ff69b4',indianred:'#cd5c5c',indigo:'#4b0082',ivory:'#fffff0',
khaki:'#f0e68c',lavender:'#e6e6fa',lavenderblush:'#fff0f5',lawngreen:'#7cfc00',
lemonchiffon:'#fffacd',lightblue:'#add8e6',lightcoral:'#f08080',lightcyan:'#e0ffff',
lightgoldenrodyellow:'#fafad2',lightgray:'#d3d3d3',lightgreen:'#90ee90',
lightpink:'#ffb6c1',lightsalmon:'#ffa07a',lightseagreen:'#20b2aa',
lightskyblue:'#87cefa',lightslategray:'#778899',lightsteelblue:'#b0c4de',
lightyellow:'#ffffe0',lime:'#00ff00',limegreen:'#32cd32',linen:'#faf0e6',
magenta:'#ff00ff',maroon:'#800000',mediumaquamarine:'#66cdaa',mediumblue:'#0000cd',
mediumorchid:'#ba55d3',mediumpurple:'#9370db',mediumseagreen:'#3cb371',
mediumslateblue:'#7b68ee',mediumspringgreen:'#00fa9a',mediumturquoise:'#48d1cc',
mediumvioletred:'#c71585',midnightblue:'#191970',mintcream:'#f5fffa',
mistyrose:'#ffe4e1',moccasin:'#ffe4b5',navajowhite:'#ffdead',navy:'#000080',
oldlace:'#fdf5e6',olive:'#808000',olivedrab:'#6b8e23',orange:'#ffa500',
orangered:'#ff4500',orchid:'#da70d6',palegoldenrod:'#eee8aa',palegreen:'#98fb98',
paleturquoise:'#afeeee',palevioletred:'#db7093',papayawhip:'#ffefd5',
peachpuff:'#ffdab9',peru:'#cd853f',pink:'#ffc0cb',plum:'#dda0dd',
powderblue:'#b0e0e6',purple:'#800080',rebeccapurple:'#663399',red:'#ff0000',
rosybrown:'#bc8f8f',royalblue:'#4169e1',saddlebrown:'#8b4513',salmon:'#fa8072',
sandybrown:'#f4a460',seagreen:'#2e8b57',seashell:'#fff5ee',sienna:'#a0522d',
silver:'#c0c0c0',skyblue:'#87ceeb',slateblue:'#6a5acd',slategray:'#708090',
snow:'#fffafa',springgreen:'#00ff7f',steelblue:'#4682b4',tan:'#d2b48c',
teal:'#008080',thistle:'#d8bfd8',tomato:'#ff6347',turquoise:'#40e0d0',
violet:'#ee82ee',wheat:'#f5deb3',white:'#ffffff',whitesmoke:'#f5f5f5',
yellow:'#ffff00',yellowgreen:'#9acd32'
};
const HEX_TO_NAME = {};
for (const [n, h] of Object.entries(CSS_NAMES)) HEX_TO_NAME[h] = n;

// ── Conversion helpers ──────────────────────────────────────────────────
function hexToRgb(hex) {
hex = hex.replace(/^#/, '');
if (hex.length === 3) hex = hex.split('').map(c => c+c).join('');
const n = parseInt(hex, 16);
return { r: (n >> 16) & 255, g: (n >> 8) & 255, b: n & 255 };
}
function rgbToHex({r, g, b}) {
return '#' + [r, g, b].map(v => v.toString(16).padStart(2,'0')).join('');
}
function rgbToHsl({r, g, b}) {
r /= 255; g /= 255; b /= 255;
const max = Math.max(r,g,b), min = Math.min(r,g,b);
let h, s, l = (max + min) / 2;
if (max === min) { h = s = 0; }
else {
const d = max - min;
s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
switch(max) {
case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
case g: h = ((b - r) / d + 2) / 6; break;
case b: h = ((r - g) / d + 4) / 6; break;
}
}
return { h: Math.round(h*360), s: Math.round(s*100), l: Math.round(l*100) };
}
function hslToRgb({h, s, l}) {
s /= 100; l /= 100;
const k = n => (n + h/30) % 12;
const a = s * Math.min(l, 1-l);
const f = n => l - a * Math.max(-1, Math.min(k(n)-3, Math.min(9-k(n), 1)));
return { r: Math.round(f(0)*255), g: Math.round(f(8)*255), b: Math.round(f(4)*255) };
}
function rgbToHsv({r, g, b}) {
r /= 255; g /= 255; b /= 255;
const max = Math.max(r,g,b), min = Math.min(r,g,b), d = max - min;
let h = 0, s = max === 0 ? 0 : d/max, v = max;
if (d !== 0) {
switch(max) {
case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
case g: h = ((b - r) / d + 2) / 6; break;
case b: h = ((r - g) / d + 4) / 6; break;
}
}
return { h: Math.round(h*360), s: Math.round(s*100), v: Math.round(v*100) };
}
function rgbToCmyk({r, g, b}) {
r /= 255; g /= 255; b /= 255;
const k = 1 - Math.max(r, g, b);
if (k === 1) return { c:0, m:0, y:0, k:100 };
return {
c: Math.round((1-r-k)/(1-k)*100),
m: Math.round((1-g-k)/(1-k)*100),
y: Math.round((1-b-k)/(1-k)*100),
k: Math.round(k*100)
};
}
function complementRgb({r, g, b}) {
return { r: 255-r, g: 255-g, b: 255-b };
}
function hslLighten({h, s, l}, amount) {
return { h, s, l: Math.min(100, l + amount) };
}
function hslDarken({h, s, l}, amount) {
return { h, s, l: Math.max(0, l - amount) };
}

// ── Parse any input ─────────────────────────────────────────────────────
function parseInput(raw) {
raw = raw.trim().toLowerCase();
// CSS named
if (CSS_NAMES[raw]) return hexToRgb(CSS_NAMES[raw]);
// HEX
if (/^#?[0-9a-f]{3,6}$/.test(raw)) {
const h = raw.startsWith('#') ? raw : '#' + raw;
return hexToRgb(h);
}
// RGB / RGBA
let m = raw.match(/rgba?\(\s*([\d.]+)\s*,\s*([\d.]+)\s*,\s*([\d.]+)/);
if (m) return { r: +m[1]|0, g: +m[2]|0, b: +m[3]|0 };
// HSL / HSLA
m = raw.match(/hsla?\(\s*([\d.]+)\s*,\s*([\d.]+)%?\s*,\s*([\d.]+)%?/);
if (m) return hslToRgb({ h: +m[1], s: +m[2], l: +m[3] });
// HSV — hsv(h,s%,v%)
m = raw.match(/hsv\(\s*([\d.]+)\s*,\s*([\d.]+)%?\s*,\s*([\d.]+)%?/);
if (m) {
const {h,s,v} = {h:+m[1],s:+m[2],v:+m[3]};
// HSV to RGB
const l = v/100 * (1 - s/200);
const sl = (l===0||l===1) ? 0 : (v/100 - l) / Math.min(l, 1-l);
return hslToRgb({h, s: Math.round(sl*100), l: Math.round(l*100)});
}
// CMYK — cmyk(c%,m%,y%,k%)
m = raw.match(/cmyk\(\s*([\d.]+)%?\s*,\s*([\d.]+)%?\s*,\s*([\d.]+)%?\s*,\s*([\d.]+)%?/);
if (m) {
const c=+m[1]/100, mm=+m[2]/100, y=+m[3]/100, k=+m[4]/100;
return {
r: Math.round(255*(1-c)*(1-k)),
g: Math.round(255*(1-mm)*(1-k)),
b: Math.round(255*(1-y)*(1-k))
};
}
return null;
}

// ── State ───────────────────────────────────────────────────────────────
let currentRgb = hexToRgb('#5b6af0');

// ── DOM refs ────────────────────────────────────────────────────────────
const picker     = document.getElementById('colconv-picker');
const rawInput   = document.getElementById('colconv-raw-input');
const errorEl    = document.getElementById('colconv-error');
const mainSwatch = document.getElementById('colconv-main-swatch');
const compSwatch = document.getElementById('colconv-comp-swatch');
const mainHexLbl = document.getElementById('colconv-main-hex-label');
const compHexLbl = document.getElementById('colconv-comp-hex-label');
const outHex     = document.getElementById('colconv-out-hex');
const outRgb     = document.getElementById('colconv-out-rgb');
const outHsl     = document.getElementById('colconv-out-hsl');
const outHsv     = document.getElementById('colconv-out-hsv');
const outCmyk    = document.getElementById('colconv-out-cmyk');
const outCss     = document.getElementById('colconv-out-css');
const shadesGrid = document.getElementById('colconv-shades-grid');

// ── Render ──────────────────────────────────────────────────────────────
function render(rgb) {
const hex  = rgbToHex(rgb);
const hsl  = rgbToHsl(rgb);
const hsv  = rgbToHsv(rgb);
const cmyk = rgbToCmyk(rgb);
const comp = complementRgb(rgb);
const compHex = rgbToHex(comp);
const cssName = HEX_TO_NAME[hex] || '—';

// Swatches
mainSwatch.style.background = hex;
mainHexLbl.textContent = hex.toUpperCase();
compSwatch.style.background = compHex;
compHexLbl.textContent = compHex.toUpperCase();

// Outputs
outHex.textContent  = hex.toUpperCase();
outRgb.textContent  = `rgb(${rgb.r}, ${rgb.g}, ${rgb.b})`;
outHsl.textContent  = `hsl(${hsl.h}, ${hsl.s}%, ${hsl.l}%)`;
outHsv.textContent  = `hsv(${hsv.h}, ${hsv.s}%, ${hsv.v}%)`;
outCmyk.textContent = `cmyk(${cmyk.c}%, ${cmyk.m}%, ${cmyk.y}%, ${cmyk.k}%)`;
outCss.textContent  = cssName;

// Picker sync
picker.value = hex;

// Shades: 5 lighter + current + 5 darker
const step = 8;
const shadeList = [];
for (let i = 5; i >= 1; i--) shadeList.push({ hsl: hslLighten(hsl, step*i), tag: `+${step*i}%` });
shadeList.push({ hsl, tag: 'base' });
for (let i = 1; i <= 5; i++) shadeList.push({ hsl: hslDarken(hsl, step*i), tag: `-${step*i}%` });

shadesGrid.innerHTML = '';
shadeList.forEach(({hsl: sh, tag}) => {
const shRgb = hslToRgb(sh);
const shHex = rgbToHex(shRgb);
const cell  = document.createElement('div');
cell.className = 'colconv-shade-cell';
cell.title = `${shHex.toUpperCase()} — ${tag}`;
cell.innerHTML = `
<div class="colconv-shade-block" style="background:${shHex}" data-hex="${shHex}"></div>
<div class="colconv-shade-hex">${shHex.toUpperCase()}</div>
<div class="colconv-shade-tag">${tag}</div>`;
cell.querySelector('.colconv-shade-block').addEventListener('click', () => {
applyHex(shHex);
});
shadesGrid.appendChild(cell);
});
}

function applyHex(hex) {
currentRgb = hexToRgb(hex);
rawInput.value = hex.toUpperCase();
errorEl.textContent = '';
render(currentRgb);
}

function applyInput(raw) {
const rgb = parseInput(raw);
if (!rgb) { errorEl.textContent = 'Could not parse color. Try #rrggbb, rgb(), hsl(), or a CSS name.'; return; }
errorEl.textContent = '';
currentRgb = rgb;
render(currentRgb);
}

// ── Events ──────────────────────────────────────────────────────────────
picker.addEventListener('input', () => applyHex(picker.value));

let debounceTimer;
rawInput.addEventListener('input', () => {
clearTimeout(debounceTimer);
debounceTimer = setTimeout(() => applyInput(rawInput.value), 300);
});
rawInput.addEventListener('keydown', e => {
if (e.key === 'Enter') { clearTimeout(debounceTimer); applyInput(rawInput.value); }
});

// Copy buttons
document.getElementById('colconv-formats').addEventListener('click', e => {
const btn = e.target.closest('.colconv-copy-btn');
if (!btn) return;
const val = document.getElementById(btn.dataset.target)?.textContent;
if (!val || val === '—') return;
navigator.clipboard.writeText(val).then(() => {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(() => { btn.textContent = 'Copy'; btn.classList.remove('copied'); }, 1500);
});
});

// Initial render
render(currentRgb);
})();
</script>
</div>

---

## How to Use

1. **Pick** a color using the color picker, or **type** any value into the text box.
2. Supported input formats: `#rrggbb`, `#rgb`, `rgb(r, g, b)`, `hsl(h, s%, l%)`, `hsv(h, s%, v%)`, `cmyk(c%, m%, y%, k%)`, or any CSS named color (e.g. `coral`, `steelblue`).
3. All output formats update instantly.
4. Click any **shade block** in the Lighter/Darker section to jump to that shade.
5. Hit **Copy** next to any format to copy it to your clipboard.

---

## Format Reference

| Format | Example | Use case |
|--------|---------|----------|
| HEX | `#5B6AF0` | Web development, design tools |
| RGB | `rgb(91, 106, 240)` | CSS, canvas, image processing |
| HSL | `hsl(235, 82%, 65%)` | CSS theming, intuitive adjustments |
| HSV/HSB | `hsv(235, 62%, 94%)` | Photoshop, Illustrator color pickers |
| CMYK | `cmyk(62%, 56%, 0%, 6%)` | Print design, press-ready files |
| CSS Name | `cornflowerblue` | Quick CSS shorthand |

---

## Related Tools

- [Color Picker](/tools/color-picker/) — Advanced eyedropper and palette builder
- [Color Palette Generator](/tools/color-palette-generator/) — Generate harmonious color palettes
- [Color Contrast Checker](/tools/color-contrast-checker/) — WCAG accessibility contrast ratio checker
