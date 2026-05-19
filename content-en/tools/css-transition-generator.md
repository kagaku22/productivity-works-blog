---
title: "CSS Transition Generator"
slug: "css-transition-generator"
date: 2025-05-16
description: "Free CSS transition generator. Build smooth transitions with custom properties, duration, timing functions, and delay — copy CSS instantly."
categories: ["Free Tools"]
tags: ["CSS", "transition", "generator", "web design", "frontend"]
cover:
  image: "/images/covers/css-transition-generator.png"
  alt: "CSS Transition Generator tool screenshot"
ShowToc: false
---

<div id="tr-app">

<style>
#tr-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1e293b;
line-height: 1.6;
}
#tr-app *, #tr-app *::before, #tr-app *::after {
box-sizing: border-box;
}
#tr-app .tr-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 24px;
margin-top: 24px;
}
@media (max-width: 768px) {
#tr-app .tr-layout {
grid-template-columns: 1fr;
}
}
#tr-app .tr-panel {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
}
#tr-app .tr-panel h3 {
margin: 0 0 16px 0;
font-size: 14px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #64748b;
}
#tr-app .tr-full-panel {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
margin-top: 24px;
}
#tr-app .tr-full-panel h3 {
margin: 0 0 16px 0;
font-size: 14px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #64748b;
}
#tr-app label {
display: block;
font-size: 13px;
font-weight: 600;
color: #475569;
margin-bottom: 6px;
}
#tr-app select {
width: 100%;
padding: 8px 12px;
border: 1px solid #cbd5e1;
border-radius: 8px;
background: #fff;
font-size: 14px;
color: #1e293b;
cursor: pointer;
outline: none;
margin-bottom: 16px;
appearance: none;
background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2364748b' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
background-repeat: no-repeat;
background-position: right 12px center;
padding-right: 36px;
}
#tr-app select:focus {
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#tr-app .tr-slider-row {
margin-bottom: 16px;
}
#tr-app .tr-slider-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 6px;
}
#tr-app .tr-slider-header label {
margin-bottom: 0;
}
#tr-app .tr-slider-val {
font-size: 13px;
font-weight: 700;
color: #6366f1;
min-width: 48px;
text-align: right;
}
#tr-app input[type="range"] {
width: 100%;
accent-color: #6366f1;
height: 4px;
cursor: pointer;
}
#tr-app .tr-bezier-section {
margin-top: 4px;
}
#tr-app .tr-bezier-inputs {
display: grid;
grid-template-columns: 1fr 1fr 1fr 1fr;
gap: 8px;
margin-bottom: 12px;
}
#tr-app .tr-bezier-inputs input[type="number"] {
width: 100%;
padding: 6px 8px;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
text-align: center;
color: #1e293b;
outline: none;
}
#tr-app .tr-bezier-inputs input[type="number"]:focus {
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#tr-app .tr-bezier-labels {
display: grid;
grid-template-columns: 1fr 1fr 1fr 1fr;
gap: 8px;
margin-bottom: 8px;
}
#tr-app .tr-bezier-labels span {
font-size: 11px;
color: #94a3b8;
text-align: center;
}
#tr-app canvas {
display: block;
border: 1px solid #e2e8f0;
border-radius: 8px;
background: #fff;
margin: 0 auto;
}
#tr-app .tr-transitions-list {
display: flex;
flex-direction: column;
gap: 8px;
margin-bottom: 12px;
max-height: 240px;
overflow-y: auto;
}
#tr-app .tr-transition-item {
display: flex;
align-items: center;
gap: 8px;
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 8px 12px;
font-size: 13px;
}
#tr-app .tr-transition-item span {
flex: 1;
color: #334155;
font-family: "Courier New", monospace;
font-size: 12px;
word-break: break-all;
}
#tr-app .tr-btn-remove {
background: none;
border: none;
color: #ef4444;
cursor: pointer;
font-size: 16px;
line-height: 1;
padding: 0 4px;
flex-shrink: 0;
}
#tr-app .tr-btn-remove:hover {
color: #b91c1c;
}
#tr-app .tr-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 9px 18px;
border-radius: 8px;
font-size: 14px;
font-weight: 600;
border: none;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
}
#tr-app .tr-btn:active {
transform: scale(0.97);
}
#tr-app .tr-btn-primary {
background: #6366f1;
color: #fff;
}
#tr-app .tr-btn-primary:hover {
background: #4f46e5;
}
#tr-app .tr-btn-secondary {
background: #e2e8f0;
color: #475569;
}
#tr-app .tr-btn-secondary:hover {
background: #cbd5e1;
}
#tr-app .tr-btn-row {
display: flex;
gap: 8px;
flex-wrap: wrap;
}
#tr-app .tr-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 0;
}
#tr-app .tr-preset-btn {
padding: 6px 14px;
border-radius: 20px;
border: 1.5px solid #6366f1;
background: #fff;
color: #6366f1;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#tr-app .tr-preset-btn:hover {
background: #6366f1;
color: #fff;
}
#tr-app .tr-preview-box {
display: flex;
align-items: center;
justify-content: center;
height: 140px;
background: linear-gradient(135deg, #e0e7ff 0%, #f0fdf4 100%);
border-radius: 10px;
margin-bottom: 12px;
position: relative;
overflow: hidden;
}
#tr-app .tr-preview-el {
width: 80px;
height: 80px;
border-radius: 12px;
background: #6366f1;
display: flex;
align-items: center;
justify-content: center;
color: #fff;
font-size: 12px;
font-weight: 700;
cursor: pointer;
user-select: none;
}
#tr-app .tr-preview-hint {
position: absolute;
bottom: 8px;
right: 12px;
font-size: 11px;
color: #94a3b8;
}
#tr-app .tr-output-block {
position: relative;
background: #0f172a;
border-radius: 10px;
padding: 20px;
font-family: "Courier New", monospace;
font-size: 13px;
line-height: 1.8;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
margin-bottom: 12px;
min-height: 80px;
}
#tr-app .tr-copy-btn {
position: absolute;
top: 12px;
right: 12px;
background: #334155;
border: none;
border-radius: 6px;
color: #94a3b8;
padding: 5px 12px;
font-size: 12px;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#tr-app .tr-copy-btn:hover {
background: #475569;
color: #fff;
}
#tr-app .tr-copy-btn.tr-copied {
background: #22c55e;
color: #fff;
}
#tr-app .tr-syntax-prop { color: #93c5fd; }
#tr-app .tr-syntax-colon { color: #94a3b8; }
#tr-app .tr-syntax-val { color: #86efac; }
#tr-app .tr-syntax-semi { color: #94a3b8; }
#tr-app .tr-info-bar {
background: #eff6ff;
border: 1px solid #bfdbfe;
border-radius: 8px;
padding: 12px 16px;
font-size: 13px;
color: #1d4ed8;
margin-bottom: 16px;
}
#tr-app .tr-divider {
border: none;
border-top: 1px solid #e2e8f0;
margin: 16px 0;
}
</style>

**Build smooth CSS transitions visually.** Select properties, set duration and easing, add multiple transitions, and copy the generated CSS — no coding required.

<div class="tr-info-bar">
Hover over the preview element to see your transition in action. Add multiple properties and use presets to get started quickly.
</div>

<div class="tr-full-panel">
<h3>Presets</h3>
<div class="tr-presets">
<button class="tr-preset-btn" onclick="trLoadPreset('fade')">Fade</button>
<button class="tr-preset-btn" onclick="trLoadPreset('slide')">Slide</button>
<button class="tr-preset-btn" onclick="trLoadPreset('scale')">Scale</button>
<button class="tr-preset-btn" onclick="trLoadPreset('color')">Color Change</button>
<button class="tr-preset-btn" onclick="trLoadPreset('combined')">Combined</button>
</div>
</div>

<div class="tr-layout">
<!-- LEFT: Controls -->
<div>
<div class="tr-panel">
<h3>Transition Settings</h3>

<label for="tr-property">Property</label>
<select id="tr-property">
<option value="all">all</option>
<option value="opacity" selected>opacity</option>
<option value="transform">transform</option>
<option value="background-color">background-color</option>
<option value="color">color</option>
<option value="width">width</option>
<option value="height">height</option>
<option value="border-radius">border-radius</option>
<option value="box-shadow">box-shadow</option>
<option value="padding">padding</option>
<option value="margin">margin</option>
<option value="font-size">font-size</option>
<option value="letter-spacing">letter-spacing</option>
<option value="border-color">border-color</option>
<option value="outline">outline</option>
<option value="filter">filter</option>
<option value="left">left</option>
<option value="top">top</option>
</select>

<div class="tr-slider-row">
<div class="tr-slider-header">
<label for="tr-duration">Duration</label>
<span class="tr-slider-val" id="tr-duration-val">0.3s</span>
</div>
<input type="range" id="tr-duration" min="0" max="300" value="30" oninput="trUpdateDuration(this.value)">
</div>

<div class="tr-slider-row">
<div class="tr-slider-header">
<label for="tr-delay">Delay</label>
<span class="tr-slider-val" id="tr-delay-val">0s</span>
</div>
<input type="range" id="tr-delay" min="0" max="200" value="0" oninput="trUpdateDelay(this.value)">
</div>

<label for="tr-timing">Timing Function</label>
<select id="tr-timing" onchange="trTimingChanged()">
<option value="ease" selected>ease</option>
<option value="linear">linear</option>
<option value="ease-in">ease-in</option>
<option value="ease-out">ease-out</option>
<option value="ease-in-out">ease-in-out</option>
<option value="step-start">step-start</option>
<option value="step-end">step-end</option>
<option value="cubic-bezier">cubic-bezier (custom)</option>
</select>

<div class="tr-bezier-section" id="tr-bezier-section" style="display:none">
<div class="tr-bezier-labels">
<span>x1</span><span>y1</span><span>x2</span><span>y2</span>
</div>
<div class="tr-bezier-inputs">
<input type="number" id="tr-bz-x1" value="0.25" min="0" max="1" step="0.01" oninput="trUpdateBezier()">
<input type="number" id="tr-bz-y1" value="0.1" min="-2" max="3" step="0.01" oninput="trUpdateBezier()">
<input type="number" id="tr-bz-x2" value="0.25" min="0" max="1" step="0.01" oninput="trUpdateBezier()">
<input type="number" id="tr-bz-y2" value="1" min="-2" max="3" step="0.01" oninput="trUpdateBezier()">
</div>
<canvas id="tr-bezier-canvas" width="200" height="160"></canvas>
</div>

<hr class="tr-divider">

<div class="tr-btn-row">
<button class="tr-btn tr-btn-primary" onclick="trAddTransition()">+ Add Transition</button>
<button class="tr-btn tr-btn-secondary" onclick="trClearAll()">Clear All</button>
</div>
</div>

<div class="tr-panel" style="margin-top:16px;">
<h3>Transition List</h3>
<div class="tr-transitions-list" id="tr-list">
<!-- populated by JS -->
</div>
<div style="font-size:12px;color:#94a3b8;" id="tr-list-empty">No transitions added yet. Configure and click "Add Transition".</div>
</div>
</div>

<!-- RIGHT: Preview + Output -->
<div>
<div class="tr-panel">
<h3>Live Preview</h3>
<div class="tr-preview-box">
<div class="tr-preview-el" id="tr-preview-el">Hover me</div>
<span class="tr-preview-hint">hover to trigger</span>
</div>
<div style="font-size:12px;color:#64748b;text-align:center;">The element above uses your generated transitions.</div>
</div>

<div class="tr-panel" style="margin-top:16px;">
<h3>Generated CSS</h3>
<div class="tr-output-block" id="tr-output">
<button class="tr-copy-btn" id="tr-copy-btn" onclick="trCopyCSS()">Copy</button>
<span id="tr-output-content"></span>
</div>
<div style="font-size:12px;color:#64748b;">Paste this into your stylesheet. Apply to the element that should animate.</div>
</div>
</div>
</div>

<script>
(function() {
// State
var trState = {
transitions: [],
duration: 0.3,
delay: 0,
timing: 'ease',
bezier: { x1: 0.25, y1: 0.1, x2: 0.25, y2: 1 }
};

// Presets
var TR_PRESETS = {
fade: [
{ property: 'opacity', duration: 0.4, delay: 0, timing: 'ease' }
],
slide: [
{ property: 'transform', duration: 0.35, delay: 0, timing: 'ease-out' },
{ property: 'opacity', duration: 0.35, delay: 0, timing: 'ease-out' }
],
scale: [
{ property: 'transform', duration: 0.25, delay: 0, timing: 'cubic-bezier(0.34,1.56,0.64,1)' }
],
color: [
{ property: 'background-color', duration: 0.3, delay: 0, timing: 'ease' },
{ property: 'color', duration: 0.3, delay: 0, timing: 'ease' }
],
combined: [
{ property: 'opacity', duration: 0.5, delay: 0, timing: 'ease' },
{ property: 'transform', duration: 0.5, delay: 0, timing: 'ease-in-out' },
{ property: 'background-color', duration: 0.3, delay: 0.1, timing: 'ease' }
]
};

// Hover states for preview
var TR_HOVER_STYLES = {
opacity: { normal: { opacity: 1 }, hover: { opacity: 0.3 } },
transform: { normal: { transform: 'none' }, hover: { transform: 'translateX(20px)' } },
'background-color': { normal: { backgroundColor: '#6366f1' }, hover: { backgroundColor: '#22c55e' } },
color: { normal: { color: '#fff' }, hover: { color: '#fef08a' } },
width: { normal: { width: '80px' }, hover: { width: '120px' } },
height: { normal: { height: '80px' }, hover: { height: '120px' } },
'border-radius': { normal: { borderRadius: '12px' }, hover: { borderRadius: '50%' } },
'box-shadow': { normal: { boxShadow: 'none' }, hover: { boxShadow: '0 8px 32px rgba(99,102,241,0.5)' } },
padding: { normal: { padding: '0px' }, hover: { padding: '16px' } },
'font-size': { normal: { fontSize: '12px' }, hover: { fontSize: '18px' } },
filter: { normal: { filter: 'none' }, hover: { filter: 'hue-rotate(90deg)' } },
all: { normal: { opacity: 1, transform: 'none' }, hover: { opacity: 0.6, transform: 'scale(1.15)' } }
};

function trGetTimingValue() {
var sel = document.getElementById('tr-timing').value;
if (sel === 'cubic-bezier') {
var x1 = parseFloat(document.getElementById('tr-bz-x1').value);
var y1 = parseFloat(document.getElementById('tr-bz-y1').value);
var x2 = parseFloat(document.getElementById('tr-bz-x2').value);
var y2 = parseFloat(document.getElementById('tr-bz-y2').value);
return 'cubic-bezier(' + x1 + ',' + y1 + ',' + x2 + ',' + y2 + ')';
}
return sel;
}

function trFormatDuration(v) {
return parseFloat(v).toFixed(2).replace(/\.?0+$/, '') || '0';
}

window.trUpdateDuration = function(v) {
var sec = (parseInt(v) / 100).toFixed(2);
trState.duration = parseFloat(sec);
document.getElementById('tr-duration-val').textContent = trFormatDuration(sec) + 's';
};

window.trUpdateDelay = function(v) {
var sec = (parseInt(v) / 100).toFixed(2);
trState.delay = parseFloat(sec);
document.getElementById('tr-delay-val').textContent = trFormatDuration(sec) + 's';
};

window.trTimingChanged = function() {
var val = document.getElementById('tr-timing').value;
var bzsec = document.getElementById('tr-bezier-section');
bzsec.style.display = (val === 'cubic-bezier') ? 'block' : 'none';
if (val === 'cubic-bezier') trDrawBezier();
};

window.trUpdateBezier = function() {
trState.bezier.x1 = parseFloat(document.getElementById('tr-bz-x1').value) || 0;
trState.bezier.y1 = parseFloat(document.getElementById('tr-bz-y1').value) || 0;
trState.bezier.x2 = parseFloat(document.getElementById('tr-bz-x2').value) || 0;
trState.bezier.y2 = parseFloat(document.getElementById('tr-bz-y2').value) || 0;
trDrawBezier();
};

function trDrawBezier() {
var canvas = document.getElementById('tr-bezier-canvas');
if (!canvas) return;
var ctx = canvas.getContext('2d');
var W = canvas.width, H = canvas.height;
var pad = 24;
var x1 = trState.bezier.x1, y1 = trState.bezier.y1;
var x2 = trState.bezier.x2, y2 = trState.bezier.y2;

ctx.clearRect(0, 0, W, H);

// Grid
ctx.strokeStyle = '#f1f5f9';
ctx.lineWidth = 1;
for (var i = 0; i <= 4; i++) {
var gx = pad + (i / 4) * (W - pad * 2);
var gy = pad + (i / 4) * (H - pad * 2);
ctx.beginPath(); ctx.moveTo(gx, pad); ctx.lineTo(gx, H - pad); ctx.stroke();
ctx.beginPath(); ctx.moveTo(pad, gy); ctx.lineTo(W - pad, gy); ctx.stroke();
}

// Axes
ctx.strokeStyle = '#cbd5e1';
ctx.lineWidth = 1.5;
ctx.beginPath();
ctx.moveTo(pad, H - pad);
ctx.lineTo(W - pad, H - pad);
ctx.stroke();
ctx.beginPath();
ctx.moveTo(pad, H - pad);
ctx.lineTo(pad, pad);
ctx.stroke();

// Map curve coords to canvas
function mapX(t) { return pad + t * (W - pad * 2); }
function mapY(t) { return (H - pad) - t * (H - pad * 2); }

// Control point handles
var p0x = mapX(0), p0y = mapY(0);
var p3x = mapX(1), p3y = mapY(1);
var c1x = mapX(x1), c1y = mapY(y1);
var c2x = mapX(x2), c2y = mapY(y2);

ctx.strokeStyle = '#c7d2fe';
ctx.lineWidth = 1;
ctx.setLineDash([4, 3]);
ctx.beginPath(); ctx.moveTo(p0x, p0y); ctx.lineTo(c1x, c1y); ctx.stroke();
ctx.beginPath(); ctx.moveTo(p3x, p3y); ctx.lineTo(c2x, c2y); ctx.stroke();
ctx.setLineDash([]);

// Bezier curve
ctx.strokeStyle = '#6366f1';
ctx.lineWidth = 2.5;
ctx.beginPath();
ctx.moveTo(p0x, p0y);
ctx.bezierCurveTo(c1x, c1y, c2x, c2y, p3x, p3y);
ctx.stroke();

// Control points
[{ x: c1x, y: c1y }, { x: c2x, y: c2y }].forEach(function(pt) {
ctx.beginPath();
ctx.arc(pt.x, pt.y, 5, 0, Math.PI * 2);
ctx.fillStyle = '#6366f1';
ctx.fill();
ctx.strokeStyle = '#fff';
ctx.lineWidth = 2;
ctx.stroke();
});

// Endpoints
[{ x: p0x, y: p0y }, { x: p3x, y: p3y }].forEach(function(pt) {
ctx.beginPath();
ctx.arc(pt.x, pt.y, 4, 0, Math.PI * 2);
ctx.fillStyle = '#64748b';
ctx.fill();
});
}

window.trAddTransition = function() {
var prop = document.getElementById('tr-property').value;
var dur = trState.duration;
var del = trState.delay;
var timing = trGetTimingValue();
trState.transitions.push({ property: prop, duration: dur, delay: del, timing: timing });
trRender();
};

window.trRemoveTransition = function(idx) {
trState.transitions.splice(idx, 1);
trRender();
};

window.trClearAll = function() {
trState.transitions = [];
trRender();
};

window.trLoadPreset = function(name) {
var preset = TR_PRESETS[name];
if (!preset) return;
trState.transitions = preset.map(function(p) { return Object.assign({}, p); });
trRender();
};

function trBuildCSSValue() {
if (trState.transitions.length === 0) {
return 'transition: none;';
}
var parts = trState.transitions.map(function(t) {
var dur = trFormatDuration(t.duration) + 's';
var del = t.delay ? ' ' + trFormatDuration(t.delay) + 's' : '';
return t.property + ' ' + dur + ' ' + t.timing + del;
});
return 'transition: ' + parts.join(',\n            ') + ';';
}

function trBuildSyntaxHTML() {
if (trState.transitions.length === 0) {
return '<span class="tr-syntax-prop">transition</span><span class="tr-syntax-colon">: </span><span class="tr-syntax-val">none</span><span class="tr-syntax-semi">;</span>';
}
var parts = trState.transitions.map(function(t, i) {
var dur = trFormatDuration(t.duration) + 's';
var del = t.delay ? ' ' + trFormatDuration(t.delay) + 's' : '';
var val = t.property + ' ' + dur + ' ' + t.timing + del;
var comma = i < trState.transitions.length - 1 ? ',' : '';
var indent = i === 0 ? '' : '            ';
return indent + '<span class="tr-syntax-val">' + val + '</span>' + comma;
});
return '<span class="tr-syntax-prop">transition</span><span class="tr-syntax-colon">: </span>' + parts.join('\n') + '<span class="tr-syntax-semi">;</span>';
}

function trApplyPreviewTransition() {
var el = document.getElementById('tr-preview-el');
if (!el) return;
if (trState.transitions.length === 0) {
el.style.transition = 'none';
return;
}
var parts = trState.transitions.map(function(t) {
var dur = trFormatDuration(t.duration) + 's';
var del = t.delay ? ' ' + trFormatDuration(t.delay) + 's' : '';
return t.property + ' ' + dur + ' ' + t.timing + del;
});
el.style.transition = parts.join(', ');
}

function trGetHoverStyles() {
var normal = {
opacity: '1',
transform: 'none',
backgroundColor: '#6366f1',
color: '#fff',
width: '80px',
height: '80px',
borderRadius: '12px',
boxShadow: 'none',
padding: '0px',
fontSize: '12px',
filter: 'none'
};
var hover = Object.assign({}, normal);

trState.transitions.forEach(function(t) {
var prop = t.property;
var hs = TR_HOVER_STYLES[prop] || TR_HOVER_STYLES['all'];
if (hs) {
Object.assign(hover, hs.hover);
}
});
return { normal: normal, hover: hover };
}

function trSetupPreviewHover() {
var el = document.getElementById('tr-preview-el');
if (!el) return;

// Remove old listeners by replacing element
var newEl = el.cloneNode(true);
el.parentNode.replaceChild(newEl, el);
el = newEl;

var styles = trGetHoverStyles();
Object.assign(el.style, styles.normal);

el.addEventListener('mouseenter', function() {
Object.assign(el.style, styles.hover);
});
el.addEventListener('mouseleave', function() {
Object.assign(el.style, styles.normal);
});
}

function trRender() {
// List
var listEl = document.getElementById('tr-list');
var emptyEl = document.getElementById('tr-list-empty');
listEl.innerHTML = '';
if (trState.transitions.length === 0) {
emptyEl.style.display = 'block';
} else {
emptyEl.style.display = 'none';
trState.transitions.forEach(function(t, idx) {
var item = document.createElement('div');
item.className = 'tr-transition-item';
var dur = trFormatDuration(t.duration) + 's';
var del = t.delay ? ' ' + trFormatDuration(t.delay) + 's' : '';
item.innerHTML = '<span>' + t.property + ' ' + dur + ' ' + t.timing + del + '</span>' +
'<button class="tr-btn-remove" onclick="trRemoveTransition(' + idx + ')" title="Remove">&#x2715;</button>';
listEl.appendChild(item);
});
}

// Output
document.getElementById('tr-output-content').innerHTML = trBuildSyntaxHTML();

// Preview
trApplyPreviewTransition();
trSetupPreviewHover();
}

window.trCopyCSS = function() {
var text = trBuildCSSValue();
navigator.clipboard.writeText(text).then(function() {
var btn = document.getElementById('tr-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('tr-copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('tr-copied');
}, 2000);
}).catch(function() {
// Fallback
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
});
};

// Init
trRender();
trDrawBezier();
})();
</script>

---

## How to Use

1. **Select a property** — choose which CSS property to animate (opacity, transform, etc.)
2. **Set duration** — drag the slider from 0 to 3 seconds
3. **Set delay** — optionally delay when the transition starts (0–2 seconds)
4. **Choose a timing function** — pick a preset easing or draw a custom cubic-bezier curve
5. **Click "Add Transition"** — adds it to the list below
6. **Repeat** for additional properties
7. **Hover the preview** to see all transitions in action
8. **Copy the CSS** and paste it into your stylesheet

---

## Tips & Common Patterns

### Staggering multiple transitions
Add different delays to each property to create a cascading effect:
```css
transition: opacity 0.3s ease 0s,
transform 0.3s ease 0.1s,
background-color 0.3s ease 0.2s;
```

### Smooth button hover
```css
transition: background-color 0.2s ease, box-shadow 0.2s ease, transform 0.15s ease;
```

### Performance tip
Prefer `transform` and `opacity` for transitions — they run on the compositor thread and avoid layout recalculations, giving you 60fps animations without jank.

### Custom easing with cubic-bezier
The cubic-bezier editor lets you fine-tune your easing curve. Classic values:
- **ease-in**: `cubic-bezier(0.42, 0, 1, 1)`
- **ease-out**: `cubic-bezier(0, 0, 0.58, 1)`
- **spring**: `cubic-bezier(0.34, 1.56, 0.64, 1)`
- **sharp**: `cubic-bezier(0.4, 0, 0.6, 1)`

---

## Related Tools

- [CSS Animation Generator](/tools/css-animation-generator/) — build full keyframe animations with `@keyframes`
- [CSS Transform Generator](/tools/css-transform-generator/) — visually construct `transform` values (rotate, scale, skew, translate)

</div>
