---
title: "CSS Border Radius Generator — Free Visual Tool"
date: 2025-05-16
description: "Generate CSS border-radius with visual controls. Individual corners, elliptical values, and shape presets. Copy border-radius CSS code instantly."
categories: ["Free Tools"]
slug: "border-radius-generator"
ShowToc: false
aliases:
  - "/tools/border-radius-generator/"
  - "/tools/border-radius-generator/"
cover:
  image: "/images/covers/border-radius-generator.png"
  alt: "CSS Border Radius Generator"
---

Visually design any CSS border-radius shape — from simple rounded corners to pills, circles, blobs, and organic forms. Adjust individual corners, toggle elliptical (horizontal/vertical) values, and copy the ready-to-use CSS in one click.

<div id="br-app">

<style>
/* ── Reset & Base ─────────────────────────────────────────── */
#br-app *,
#br-app *::before,
#br-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#br-app {
font-family: system-ui, -apple-system, sans-serif;
font-size: 14px;
color: #1a1a2e;
line-height: 1.5;
}

/* ── Layout ───────────────────────────────────────────────── */
#br-app .br-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 24px;
margin-top: 24px;
}
@media (max-width: 720px) {
#br-app .br-layout {
grid-template-columns: 1fr;
}
}

/* ── Panel ────────────────────────────────────────────────── */
#br-app .br-panel {
background: #f8f9fc;
border: 1px solid #e2e6f0;
border-radius: 12px;
padding: 20px;
}
#br-app .br-panel h3 {
font-size: 13px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .06em;
color: #6b7280;
margin-bottom: 16px;
}

/* ── Preview ──────────────────────────────────────────────── */
#br-app .br-preview-wrap {
display: flex;
align-items: center;
justify-content: center;
min-height: 260px;
background: repeating-conic-gradient(#e5e7eb 0% 25%, #f9fafb 0% 50%) 0 0 / 20px 20px;
border-radius: 8px;
padding: 20px;
margin-bottom: 16px;
}
#br-app #br-preview-box {
width: 160px;
height: 160px;
background: #6366f1;
transition: border-radius .15s ease, width .15s ease, height .15s ease, background .15s ease;
}

/* ── Preview Controls ─────────────────────────────────────── */
#br-app .br-preview-controls {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
gap: 10px;
align-items: end;
}
#br-app .br-preview-controls label {
font-size: 12px;
color: #6b7280;
display: block;
margin-bottom: 4px;
}
#br-app .br-preview-controls input[type="number"] {
width: 100%;
padding: 6px 8px;
border: 1px solid #d1d5db;
border-radius: 6px;
font-size: 13px;
background: #fff;
}
#br-app .br-preview-controls input[type="color"] {
width: 100%;
height: 34px;
padding: 2px 4px;
border: 1px solid #d1d5db;
border-radius: 6px;
cursor: pointer;
background: #fff;
}

/* ── Presets ──────────────────────────────────────────────── */
#br-app .br-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 0;
}
#br-app .br-preset-btn {
padding: 6px 14px;
border: 1px solid #d1d5db;
border-radius: 6px;
background: #fff;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: background .12s, border-color .12s, color .12s;
}
#br-app .br-preset-btn:hover,
#br-app .br-preset-btn.active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}

/* ── Unit Toggle ──────────────────────────────────────────── */
#br-app .br-unit-toggle {
display: flex;
gap: 0;
border: 1px solid #d1d5db;
border-radius: 6px;
overflow: hidden;
width: fit-content;
margin-bottom: 16px;
}
#br-app .br-unit-btn {
padding: 5px 16px;
border: none;
background: #fff;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background .12s, color .12s;
}
#br-app .br-unit-btn.active {
background: #6366f1;
color: #fff;
}

/* ── Corner Grid ──────────────────────────────────────────── */
#br-app .br-corner-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-bottom: 16px;
}
#br-app .br-corner-block {
background: #fff;
border: 1px solid #e2e6f0;
border-radius: 8px;
padding: 12px;
}
#br-app .br-corner-block label {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .05em;
color: #6366f1;
display: block;
margin-bottom: 8px;
}
#br-app .br-slider-row {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 6px;
}
#br-app .br-slider-row span {
font-size: 11px;
color: #9ca3af;
width: 10px;
flex-shrink: 0;
}
#br-app .br-slider-row input[type="range"] {
flex: 1;
accent-color: #6366f1;
cursor: pointer;
}
#br-app .br-slider-row input[type="number"] {
width: 52px;
padding: 3px 6px;
border: 1px solid #d1d5db;
border-radius: 5px;
font-size: 12px;
text-align: right;
}
#br-app .br-elliptic-toggle {
font-size: 11px;
color: #6b7280;
cursor: pointer;
display: flex;
align-items: center;
gap: 4px;
margin-top: 4px;
user-select: none;
}
#br-app .br-elliptic-toggle input { accent-color: #6366f1; cursor: pointer; }

/* ── Link Toggle ──────────────────────────────────────────── */
#br-app .br-link-row {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 16px;
}
#br-app .br-link-btn {
padding: 6px 14px;
border: 1px solid #d1d5db;
border-radius: 6px;
background: #fff;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: background .12s, border-color .12s, color .12s;
display: flex;
align-items: center;
gap: 6px;
}
#br-app .br-link-btn.active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}
#br-app .br-link-btn svg {
width: 14px; height: 14px; fill: currentColor;
}

/* ── Output ───────────────────────────────────────────────── */
#br-app .br-output-box {
background: #1a1a2e;
border-radius: 8px;
padding: 16px;
margin-top: 8px;
position: relative;
}
#br-app .br-output-code {
font-family: 'Fira Mono', 'Cascadia Code', monospace;
font-size: 13px;
color: #a5f3fc;
word-break: break-all;
white-space: pre-wrap;
line-height: 1.7;
}
#br-app .br-copy-btn {
position: absolute;
top: 10px;
right: 10px;
padding: 5px 12px;
background: #6366f1;
color: #fff;
border: none;
border-radius: 5px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: background .12s;
}
#br-app .br-copy-btn:hover { background: #4f46e5; }
#br-app .br-copy-btn.copied { background: #10b981; }
</style>

<!-- ── Presets ── -->
<div class="br-panel" style="margin-top:24px;">
<h3>Presets</h3>
<div class="br-presets">
<button class="br-preset-btn" data-preset="none">None</button>
<button class="br-preset-btn" data-preset="pill">Pill</button>
<button class="br-preset-btn" data-preset="circle">Circle</button>
<button class="br-preset-btn" data-preset="blob">Blob</button>
<button class="br-preset-btn" data-preset="squircle">Squircle</button>
<button class="br-preset-btn" data-preset="leaf">Leaf</button>
<button class="br-preset-btn" data-preset="drop">Drop</button>
<button class="br-preset-btn" data-preset="triangle">Triangle-ish</button>
</div>
</div>

<div class="br-layout">
<!-- Left: Preview -->
<div>
<div class="br-panel">
<h3>Preview</h3>
<div class="br-preview-wrap">
<div id="br-preview-box"></div>
</div>
<div class="br-preview-controls">
<div>
<label for="br-pw">Width (px)</label>
<input type="number" id="br-pw" value="160" min="40" max="400" step="4">
</div>
<div>
<label for="br-ph">Height (px)</label>
<input type="number" id="br-ph" value="160" min="40" max="400" step="4">
</div>
<div>
<label for="br-pbg">Color</label>
<input type="color" id="br-pbg" value="#6366f1">
</div>
</div>
</div>
</div>

<!-- Right: Controls -->
<div>
<div class="br-panel">
<h3>Controls</h3>

<!-- Unit toggle -->
<div class="br-unit-toggle">
<button class="br-unit-btn active" data-unit="px">px</button>
<button class="br-unit-btn" data-unit="%">%</button>
</div>

<!-- Link toggle -->
<div class="br-link-row">
<button class="br-link-btn active" id="br-link-btn">
<svg viewBox="0 0 20 20"><path d="M10.293 3.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 9H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414zM3 14a1 1 0 100 2h14a1 1 0 100-2H3z"/></svg>
Link corners
</button>
<span id="br-link-label" style="font-size:12px;color:#6b7280;">All corners move together</span>
</div>

<!-- Corner sliders -->
<div class="br-corner-grid" id="br-corner-grid">

<!-- Top-Left -->
<div class="br-corner-block" id="br-block-tl">
<label>Top-Left</label>
<div class="br-slider-row">
<span>H</span>
<input type="range" id="br-tl-h" min="0" max="200" value="0">
<input type="number" id="br-tl-h-n" min="0" max="200" value="0">
</div>
<div class="br-slider-row" id="br-tl-v-row" style="display:none;">
<span>V</span>
<input type="range" id="br-tl-v" min="0" max="200" value="0">
<input type="number" id="br-tl-v-n" min="0" max="200" value="0">
</div>
<label class="br-elliptic-toggle"><input type="checkbox" id="br-tl-ell"> Elliptical</label>
</div>

<!-- Top-Right -->
<div class="br-corner-block" id="br-block-tr">
<label>Top-Right</label>
<div class="br-slider-row">
<span>H</span>
<input type="range" id="br-tr-h" min="0" max="200" value="0">
<input type="number" id="br-tr-h-n" min="0" max="200" value="0">
</div>
<div class="br-slider-row" id="br-tr-v-row" style="display:none;">
<span>V</span>
<input type="range" id="br-tr-v" min="0" max="200" value="0">
<input type="number" id="br-tr-v-n" min="0" max="200" value="0">
</div>
<label class="br-elliptic-toggle"><input type="checkbox" id="br-tr-ell"> Elliptical</label>
</div>

<!-- Bottom-Right -->
<div class="br-corner-block" id="br-block-br">
<label>Bottom-Right</label>
<div class="br-slider-row">
<span>H</span>
<input type="range" id="br-br-h" min="0" max="200" value="0">
<input type="number" id="br-br-h-n" min="0" max="200" value="0">
</div>
<div class="br-slider-row" id="br-br-v-row" style="display:none;">
<span>V</span>
<input type="range" id="br-br-v" min="0" max="200" value="0">
<input type="number" id="br-br-v-n" min="0" max="200" value="0">
</div>
<label class="br-elliptic-toggle"><input type="checkbox" id="br-br-ell"> Elliptical</label>
</div>

<!-- Bottom-Left -->
<div class="br-corner-block" id="br-block-bl">
<label>Bottom-Left</label>
<div class="br-slider-row">
<span>H</span>
<input type="range" id="br-bl-h" min="0" max="200" value="0">
<input type="number" id="br-bl-h-n" min="0" max="200" value="0">
</div>
<div class="br-slider-row" id="br-bl-v-row" style="display:none;">
<span>V</span>
<input type="range" id="br-bl-v" min="0" max="200" value="0">
<input type="number" id="br-bl-v-n" min="0" max="200" value="0">
</div>
<label class="br-elliptic-toggle"><input type="checkbox" id="br-bl-ell"> Elliptical</label>
</div>

</div><!-- /.br-corner-grid -->
</div><!-- /.br-panel -->
</div>
</div><!-- /.br-layout -->

<!-- Output -->
<div class="br-panel" style="margin-top:0;">
<h3>Generated CSS</h3>
<div class="br-output-box">
<button class="br-copy-btn" id="br-copy-btn">Copy</button>
<pre class="br-output-code" id="br-output-code">border-radius: 0;</pre>
</div>
</div>

<script>
(function () {
'use strict';

/* ── State ── */
var unit = 'px';
var linked = true;

var corners = {
tl: { h: 0, v: 0, elliptic: false },
tr: { h: 0, v: 0, elliptic: false },
br: { h: 0, v: 0, elliptic: false },
bl: { h: 0, v: 0, elliptic: false }
};

/* ── Presets (px-based; % presets use special flag) ── */
var PRESETS = {
none:     { tl:{h:0,v:0,e:false}, tr:{h:0,v:0,e:false}, br:{h:0,v:0,e:false}, bl:{h:0,v:0,e:false}, unit:'px' },
pill:     { tl:{h:999,v:999,e:false}, tr:{h:999,v:999,e:false}, br:{h:999,v:999,e:false}, bl:{h:999,v:999,e:false}, unit:'px' },
circle:   { tl:{h:50,v:50,e:false}, tr:{h:50,v:50,e:false}, br:{h:50,v:50,e:false}, bl:{h:50,v:50,e:false}, unit:'%' },
blob:     { tl:{h:60,v:40,e:true}, tr:{h:40,v:70,e:true}, br:{h:70,v:50,e:true}, bl:{h:50,v:60,e:true}, unit:'%' },
squircle: { tl:{h:30,v:30,e:false}, tr:{h:30,v:30,e:false}, br:{h:30,v:30,e:false}, bl:{h:30,v:30,e:false}, unit:'%' },
leaf:     { tl:{h:0,v:0,e:false}, tr:{h:50,v:50,e:false}, br:{h:0,v:0,e:false}, bl:{h:50,v:50,e:false}, unit:'%' },
drop:     { tl:{h:50,v:50,e:false}, tr:{h:50,v:50,e:false}, br:{h:50,v:50,e:false}, bl:{h:0,v:0,e:false}, unit:'%' },
triangle: { tl:{h:0,v:0,e:false}, tr:{h:100,v:0,e:true}, br:{h:100,v:100,e:true}, bl:{h:0,v:100,e:true}, unit:'%' }
};

/* ── DOM refs ── */
var preview   = document.getElementById('br-preview-box');
var outputEl  = document.getElementById('br-output-code');
var copyBtn   = document.getElementById('br-copy-btn');
var linkBtn   = document.getElementById('br-link-btn');
var linkLabel = document.getElementById('br-link-label');
var pwInput   = document.getElementById('br-pw');
var phInput   = document.getElementById('br-ph');
var pbgInput  = document.getElementById('br-pbg');

var cornerKeys = ['tl','tr','br','bl'];

function el(id) { return document.getElementById(id); }

/* ── Build CSS value ── */
function cornerVal(c) {
var u = unit;
var hv = Math.min(c.h, u === '%' ? 50 : 200);
if (c.elliptic) {
var vv = Math.min(c.v, u === '%' ? 50 : 200);
return hv + u + ' / ' + vv + u;
}
return hv + u;
}

function buildCSS() {
var c = corners;
var vals = [cornerVal(c.tl), cornerVal(c.tr), cornerVal(c.br), cornerVal(c.bl)];

// Check if any corner is elliptic
var anyElliptic = cornerKeys.some(function(k){ return corners[k].elliptic; });

var css;
if (anyElliptic) {
// Full 4-value horizontal / 4-value vertical syntax
var hParts = cornerKeys.map(function(k){
return Math.min(corners[k].h, unit === '%' ? 50 : 200) + unit;
});
var vParts = cornerKeys.map(function(k){
return Math.min(corners[k].v, unit === '%' ? 50 : 200) + unit;
});
css = 'border-radius: ' + hParts.join(' ') + ' / ' + vParts.join(' ') + ';';
} else {
// Compact shorthand
var tl = Math.min(corners.tl.h, unit === '%' ? 50 : 200) + unit;
var tr = Math.min(corners.tr.h, unit === '%' ? 50 : 200) + unit;
var brv= Math.min(corners.br.h, unit === '%' ? 50 : 200) + unit;
var bl = Math.min(corners.bl.h, unit === '%' ? 50 : 200) + unit;
// Collapse shorthand when possible
if (tl === tr && tr === brv && brv === bl) {
css = 'border-radius: ' + tl + ';';
} else if (tl === brv && tr === bl) {
css = 'border-radius: ' + tl + ' ' + tr + ';';
} else if (tr === bl) {
css = 'border-radius: ' + tl + ' ' + tr + ' ' + brv + ';';
} else {
css = 'border-radius: ' + tl + ' ' + tr + ' ' + brv + ' ' + bl + ';';
}
}
return css;
}

function applyPreview() {
var css = buildCSS();
// Apply border-radius to preview box
var hParts = cornerKeys.map(function(k){
return Math.min(corners[k].h, unit === '%' ? 50 : 200) + unit;
});
var vParts = cornerKeys.map(function(k){
return Math.min(corners[k].v, unit === '%' ? 50 : 200) + unit;
});
preview.style.borderRadius = hParts.join(' ') + ' / ' + vParts.join(' ');
outputEl.textContent = css;
}

function syncInputs() {
cornerKeys.forEach(function(k) {
var c = corners[k];
var maxVal = unit === '%' ? 50 : 200;
el('br-' + k + '-h').max = maxVal;
el('br-' + k + '-h-n').max = maxVal;
el('br-' + k + '-v').max = maxVal;
el('br-' + k + '-v-n').max = maxVal;
el('br-' + k + '-h').value = Math.min(c.h, maxVal);
el('br-' + k + '-h-n').value = Math.min(c.h, maxVal);
el('br-' + k + '-v').value = Math.min(c.v, maxVal);
el('br-' + k + '-v-n').value = Math.min(c.v, maxVal);
el('br-' + k + '-ell').checked = c.elliptic;
el('br-' + k + '-v-row').style.display = c.elliptic ? 'flex' : 'none';
});
}

/* ── Wire slider ↔ number input ── */
function wireCorner(k, axis) {
var sliderEl = el('br-' + k + '-' + axis);
var numEl    = el('br-' + k + '-' + axis + '-n');

function onChange(val) {
val = Math.max(0, Math.min(parseInt(val) || 0, unit === '%' ? 50 : 200));
corners[k][axis] = val;

if (linked && axis === 'h') {
cornerKeys.forEach(function(ck) {
corners[ck].h = val;
if (!corners[ck].elliptic) corners[ck].v = val;
});
syncInputs();
} else {
sliderEl.value = val;
numEl.value = val;
}
applyPreview();
}

sliderEl.addEventListener('input', function() { onChange(this.value); });
numEl.addEventListener('input', function() { onChange(this.value); });
}

cornerKeys.forEach(function(k) {
wireCorner(k, 'h');
wireCorner(k, 'v');

// Elliptic toggle
el('br-' + k + '-ell').addEventListener('change', function() {
corners[k].elliptic = this.checked;
el('br-' + k + '-v-row').style.display = this.checked ? 'flex' : 'none';
applyPreview();
});
});

/* ── Link button ── */
linkBtn.addEventListener('click', function() {
linked = !linked;
linkBtn.classList.toggle('active', linked);
linkLabel.textContent = linked ? 'All corners move together' : 'Corners are independent';
});

/* ── Unit buttons ── */
document.querySelectorAll('#br-app .br-unit-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#br-app .br-unit-btn').forEach(function(b){ b.classList.remove('active'); });
this.classList.add('active');
unit = this.dataset.unit;
// Scale values when switching unit
var maxVal = unit === '%' ? 50 : 200;
cornerKeys.forEach(function(k) {
corners[k].h = Math.min(corners[k].h, maxVal);
corners[k].v = Math.min(corners[k].v, maxVal);
});
syncInputs();
applyPreview();
});
});

/* ── Preset buttons ── */
document.querySelectorAll('#br-app .br-preset-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#br-app .br-preset-btn').forEach(function(b){ b.classList.remove('active'); });
this.classList.add('active');

var p = PRESETS[this.dataset.preset];
if (!p) return;

// Switch unit
unit = p.unit;
document.querySelectorAll('#br-app .br-unit-btn').forEach(function(b){
b.classList.toggle('active', b.dataset.unit === unit);
});

// Apply corner values
var maxVal = unit === '%' ? 50 : 200;
cornerKeys.forEach(function(k) {
corners[k].h = Math.min(p[k].h, maxVal);
corners[k].v = Math.min(p[k].v, maxVal);
corners[k].elliptic = p[k].e;
});

// Pill uses px 999 — clamp displayed but let CSS do the work
if (this.dataset.preset === 'pill') {
cornerKeys.forEach(function(k) { corners[k].h = 200; });
}

linked = false;
linkBtn.classList.remove('active');
linkLabel.textContent = 'Corners are independent';

syncInputs();
applyPreview();
});
});

/* ── Preview box size / color ── */
pwInput.addEventListener('input', function() {
preview.style.width = Math.max(40, parseInt(this.value) || 160) + 'px';
});
phInput.addEventListener('input', function() {
preview.style.height = Math.max(40, parseInt(this.value) || 160) + 'px';
});
pbgInput.addEventListener('input', function() {
preview.style.background = this.value;
});

/* ── Copy button ── */
copyBtn.addEventListener('click', function() {
var text = outputEl.textContent;
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(function() { flash(); });
} else {
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
flash();
}
function flash() {
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'Copy';
copyBtn.classList.remove('copied');
}, 1800);
}
});

/* ── Init ── */
syncInputs();
applyPreview();

})();
</script>

</div>

---

### How to Use

1. **Choose a preset** to start from a known shape, or drag the sliders to build from scratch.
2. **Toggle px / %** — percentage values are relative to the element's dimensions; pixels are absolute.
3. **Unlink corners** to set each corner independently.
4. **Enable Elliptical** on any corner to separate horizontal and vertical radii for organic shapes.
5. **Resize the preview** box to see how your radius looks at different aspect ratios.
6. **Copy the CSS** and paste it directly into your stylesheet.

### Quick Reference: border-radius Syntax

| Value | Meaning |
|---|---|
| `border-radius: 8px` | All corners equal |
| `border-radius: 8px 16px` | TL+BR / TR+BL |
| `border-radius: 8px 16px 24px 32px` | TL TR BR BL (clockwise) |
| `border-radius: 40% 60% / 60% 40%` | Elliptical (H / V) |

---

### Related Tools
> Generate box shadows → [CSS Box Shadow Generator](/tools/box-shadow-generator/)
> Build gradients → [CSS Gradient Generator](/tools/css-gradient-generator/)
> Create Flexbox layouts → [CSS Flexbox Generator](/tools/flexbox-generator/)
