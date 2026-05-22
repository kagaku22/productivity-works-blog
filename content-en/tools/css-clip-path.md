---
title: "CSS Clip-Path Maker"
date: 2025-05-16
description: "Free visual CSS clip-path generator. Create custom shapes with draggable points, choose from presets, and copy the CSS code instantly."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "css-clip-path"
ShowToc: false
cover:
  image: "/images/covers/css-clip-path.png"
  alt: "CSS Clip-Path Maker"
---

<div id="cp-app">

<style>
#cp-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 48px 0;
color: #374151;
}
#cp-app * { box-sizing: border-box; }

.cp-layout {
display: grid;
grid-template-columns: 1fr 320px;
gap: 20px;
align-items: start;
}
@media (max-width: 720px) {
.cp-layout { grid-template-columns: 1fr; }
}

/* Canvas area */
.cp-canvas-wrap {
position: relative;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 14px;
overflow: hidden;
}
.cp-canvas-inner {
position: relative;
width: 100%;
aspect-ratio: 1 / 1;
max-height: 480px;
overflow: hidden;
}
#cp-canvas {
display: block;
width: 100%;
height: 100%;
touch-action: none;
cursor: crosshair;
}
.cp-canvas-label {
position: absolute;
bottom: 10px;
left: 50%;
transform: translateX(-50%);
background: rgba(0,0,0,0.5);
color: #fff;
font-size: 11px;
padding: 3px 10px;
border-radius: 20px;
pointer-events: none;
white-space: nowrap;
}

/* Controls panel */
.cp-panel {
display: flex;
flex-direction: column;
gap: 14px;
}

.cp-card {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 16px;
}
.cp-card h3 {
margin: 0 0 10px 0;
font-size: 13px;
font-weight: 700;
color: #1e293b;
text-transform: uppercase;
letter-spacing: 0.05em;
}

/* Presets */
.cp-presets {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 7px;
}
.cp-preset-btn {
display: flex;
flex-direction: column;
align-items: center;
gap: 5px;
padding: 8px 4px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
cursor: pointer;
font-size: 11px;
color: #475569;
font-weight: 600;
transition: all 0.15s;
}
.cp-preset-btn:hover {
border-color: #6366f1;
color: #4f46e5;
background: #eef2ff;
}
.cp-preset-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4f46e5;
}
.cp-preset-icon {
width: 36px;
height: 36px;
background: #6366f1;
}

/* Background controls */
.cp-bg-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 8px;
}
.cp-bg-row label {
font-size: 13px;
color: #374151;
font-weight: 500;
min-width: 80px;
}
.cp-color-input {
width: 40px;
height: 32px;
border: 1.5px solid #e2e8f0;
border-radius: 6px;
padding: 2px;
cursor: pointer;
background: none;
}
.cp-img-btn {
flex: 1;
padding: 6px 10px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
font-size: 12px;
cursor: pointer;
color: #475569;
font-weight: 600;
transition: all 0.15s;
}
.cp-img-btn:hover {
border-color: #6366f1;
color: #4f46e5;
}

/* CSS Output */
.cp-output-box {
background: #1e293b;
border-radius: 10px;
padding: 14px 16px;
font-family: 'SFMono-Regular', Consolas, monospace;
font-size: 12.5px;
color: #a5f3fc;
line-height: 1.6;
word-break: break-all;
min-height: 56px;
}
.cp-copy-btn {
width: 100%;
margin-top: 10px;
padding: 11px;
background: linear-gradient(135deg, #6366f1, #8b5cf6);
color: #fff;
border: none;
border-radius: 9px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.15s;
}
.cp-copy-btn:hover { opacity: 0.9; }
.cp-copy-btn.copied {
background: linear-gradient(135deg, #10b981, #059669);
}

/* Point info */
.cp-point-info {
font-size: 12px;
color: #64748b;
margin-top: 6px;
text-align: center;
}

/* Shape info */
.cp-shape-info {
font-size: 12px;
color: #6366f1;
font-weight: 600;
background: #eef2ff;
border-radius: 6px;
padding: 6px 10px;
text-align: center;
}

/* Reset btn */
.cp-reset-btn {
width: 100%;
padding: 9px;
background: #f1f5f9;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
color: #475569;
cursor: pointer;
transition: all 0.15s;
}
.cp-reset-btn:hover {
border-color: #cbd5e1;
background: #e2e8f0;
}
</style>

<div class="cp-layout">
<!-- Left: Canvas -->
<div>
<div class="cp-canvas-wrap">
<div class="cp-canvas-inner">
<canvas id="cp-canvas"></canvas>
</div>
<div class="cp-canvas-label">Drag points to reshape</div>
</div>
<div class="cp-point-info" id="cp-point-info">Click on the shape edge to add a point. Right-click a point to delete it.</div>
</div>

<!-- Right: Panel -->
<div class="cp-panel">
<!-- Presets -->
<div class="cp-card">
<h3>Presets</h3>
<div class="cp-presets" id="cp-presets"></div>
</div>

<!-- Background -->
<div class="cp-card">
<h3>Preview</h3>
<div class="cp-bg-row">
<label>Shape color</label>
<input type="color" class="cp-color-input" id="cp-shape-color" value="#6366f1">
</div>
<div class="cp-bg-row">
<label>BG color</label>
<input type="color" class="cp-color-input" id="cp-bg-color" value="#e2e8f0">
</div>
<div class="cp-bg-row">
<label>Image</label>
<button class="cp-img-btn" id="cp-upload-btn">Upload Image</button>
<input type="file" id="cp-file-input" accept="image/*" style="display:none">
</div>
<button class="cp-reset-btn" id="cp-clear-img" style="display:none">Remove Image</button>
</div>

<!-- Output -->
<div class="cp-card">
<h3>CSS Output</h3>
<div class="cp-output-box" id="cp-output">clip-path: polygon(...);</div>
<button class="cp-copy-btn" id="cp-copy-btn">Copy CSS</button>
</div>

<!-- Shape info -->
<div class="cp-shape-info" id="cp-shape-info">polygon · 0 points</div>
<button class="cp-reset-btn" id="cp-reset-btn">Reset to Preset</button>
</div>
</div>

<script>
(function() {
const PRESETS = {
circle: {
label: 'Circle',
icon: (ctx, w, h) => { ctx.arc(w/2, h/2, Math.min(w,h)*0.42, 0, Math.PI*2); },
type: 'circle',
css: () => 'clip-path: circle(50% at 50% 50%);'
},
ellipse: {
label: 'Ellipse',
icon: (ctx, w, h) => { ctx.ellipse(w/2, h/2, w*0.42, h*0.28, 0, 0, Math.PI*2); },
type: 'ellipse',
css: () => 'clip-path: ellipse(55% 35% at 50% 50%);'
},
triangle: {
label: 'Triangle',
points: [[50,5],[95,95],[5,95]]
},
diamond: {
label: 'Diamond',
points: [[50,5],[95,50],[50,95],[5,50]]
},
pentagon: {
label: 'Pentagon',
points: (function() {
var pts = [];
for (var i = 0; i < 5; i++) {
var a = (i * 72 - 90) * Math.PI / 180;
pts.push([50 + 45 * Math.cos(a), 50 + 45 * Math.sin(a)]);
}
return pts;
})()
},
hexagon: {
label: 'Hexagon',
points: (function() {
var pts = [];
for (var i = 0; i < 6; i++) {
var a = (i * 60 - 30) * Math.PI / 180;
pts.push([50 + 47 * Math.cos(a), 50 + 47 * Math.sin(a)]);
}
return pts;
})()
},
star: {
label: 'Star',
points: (function() {
var pts = [];
for (var i = 0; i < 10; i++) {
var a = (i * 36 - 90) * Math.PI / 180;
var r = i % 2 === 0 ? 47 : 20;
pts.push([50 + r * Math.cos(a), 50 + r * Math.sin(a)]);
}
return pts;
})()
},
arrow: {
label: 'Arrow',
points: [[0,35],[60,35],[60,15],[100,50],[60,85],[60,65],[0,65]]
},
cross: {
label: 'Cross',
points: [[33,0],[67,0],[67,33],[100,33],[100,67],[67,67],[67,100],[33,100],[33,67],[0,67],[0,33],[33,33]]
}
};

const canvas = document.getElementById('cp-canvas');
const ctx = canvas.getContext('2d');
const outputEl = document.getElementById('cp-output');
const copyBtn = document.getElementById('cp-copy-btn');
const resetBtn = document.getElementById('cp-reset-btn');
const shapeInfoEl = document.getElementById('cp-shape-info');
const pointInfoEl = document.getElementById('cp-point-info');
const shapeColorInput = document.getElementById('cp-shape-color');
const bgColorInput = document.getElementById('cp-bg-color');
const uploadBtn = document.getElementById('cp-upload-btn');
const fileInput = document.getElementById('cp-file-input');
const clearImgBtn = document.getElementById('cp-clear-img');

let points = []; // percentage [x, y]
let activePreset = 'triangle';
let dragIndex = -1;
let shapeColor = '#6366f1';
let bgColor = '#e2e8f0';
let uploadedImage = null;
let currentType = 'polygon'; // 'polygon', 'circle', 'ellipse'

// Resize canvas to match display size
function resizeCanvas() {
const rect = canvas.parentElement.getBoundingClientRect();
const size = Math.min(rect.width, 480);
canvas.width = size;
canvas.height = size;
draw();
}

// Convert percentage to canvas px
function toCanvasPx(px, py) {
return [px / 100 * canvas.width, py / 100 * canvas.height];
}

function toPercent(cx, cy) {
return [cx / canvas.width * 100, cy / canvas.height * 100];
}

function fmt(n) { return Math.round(n * 10) / 10; }

function buildCSS() {
if (currentType === 'circle') {
return 'clip-path: circle(50% at 50% 50%);';
} else if (currentType === 'ellipse') {
return 'clip-path: ellipse(55% 35% at 50% 50%);';
}
if (points.length < 3) return 'clip-path: polygon(/* add points */);';
const pts = points.map(p => fmt(p[0]) + '% ' + fmt(p[1]) + '%').join(', ');
return 'clip-path: polygon(' + pts + ');';
}

function updateOutput() {
const css = buildCSS();
outputEl.textContent = css;
const count = currentType === 'polygon' ? points.length + ' points' : '';
shapeInfoEl.textContent = currentType + (count ? ' · ' + count : '');
}

function draw() {
const w = canvas.width, h = canvas.height;
ctx.clearRect(0, 0, w, h);

// Background
ctx.fillStyle = bgColor;
ctx.fillRect(0, 0, w, h);

// Draw checkerboard pattern hint
const cs = 20;
for (let r = 0; r < h / cs; r++) {
for (let c = 0; c < w / cs; c++) {
if ((r + c) % 2 === 0) {
ctx.fillStyle = 'rgba(0,0,0,0.04)';
ctx.fillRect(c * cs, r * cs, cs, cs);
}
}
}

// Shape with clip
ctx.save();
if (currentType === 'circle') {
ctx.beginPath();
ctx.arc(w / 2, h / 2, Math.min(w, h) * 0.47, 0, Math.PI * 2);
ctx.clip();
} else if (currentType === 'ellipse') {
ctx.beginPath();
ctx.ellipse(w / 2, h / 2, w * 0.52, h * 0.34, 0, 0, Math.PI * 2);
ctx.clip();
} else if (points.length >= 3) {
ctx.beginPath();
const [x0, y0] = toCanvasPx(points[0][0], points[0][1]);
ctx.moveTo(x0, y0);
for (let i = 1; i < points.length; i++) {
const [xi, yi] = toCanvasPx(points[i][0], points[i][1]);
ctx.lineTo(xi, yi);
}
ctx.closePath();
ctx.clip();
}

if (uploadedImage) {
// Draw image fitted
const ar = uploadedImage.width / uploadedImage.height;
let dw = w, dh = h;
if (ar > 1) { dh = w / ar; } else { dw = h * ar; }
const dx = (w - dw) / 2, dy = (h - dh) / 2;
ctx.drawImage(uploadedImage, dx, dy, dw, dh);
} else {
ctx.fillStyle = shapeColor;
ctx.fillRect(0, 0, w, h);
}
ctx.restore();

// Draw outline and control points for polygon only
if (currentType === 'polygon' && points.length >= 2) {
ctx.beginPath();
const [x0, y0] = toCanvasPx(points[0][0], points[0][1]);
ctx.moveTo(x0, y0);
for (let i = 1; i < points.length; i++) {
const [xi, yi] = toCanvasPx(points[i][0], points[i][1]);
ctx.lineTo(xi, yi);
}
ctx.closePath();
ctx.strokeStyle = 'rgba(255,255,255,0.9)';
ctx.lineWidth = 1.5;
ctx.setLineDash([5, 4]);
ctx.stroke();
ctx.setLineDash([]);

// Draw points
points.forEach(([px, py], i) => {
const [cx, cy] = toCanvasPx(px, py);
ctx.beginPath();
ctx.arc(cx, cy, dragIndex === i ? 10 : 7, 0, Math.PI * 2);
ctx.fillStyle = dragIndex === i ? '#f59e0b' : '#fff';
ctx.fill();
ctx.strokeStyle = dragIndex === i ? '#d97706' : '#6366f1';
ctx.lineWidth = 2;
ctx.stroke();
});
}

updateOutput();
}

function loadPreset(name) {
const preset = PRESETS[name];
if (!preset) return;
activePreset = name;
if (preset.type === 'circle' || preset.type === 'ellipse') {
currentType = preset.type;
points = [];
} else {
currentType = 'polygon';
points = preset.points.map(p => [...p]);
}
document.querySelectorAll('.cp-preset-btn').forEach(b => {
b.classList.toggle('active', b.dataset.preset === name);
});
pointInfoEl.textContent = currentType === 'polygon'
? 'Drag points to reshape. Right-click a point to delete it.'
: 'This shape uses a fixed CSS function. Switch to a polygon preset to edit points.';
draw();
}

// Build preset buttons
const presetsEl = document.getElementById('cp-presets');
Object.keys(PRESETS).forEach(name => {
const btn = document.createElement('button');
btn.className = 'cp-preset-btn';
btn.dataset.preset = name;
// Mini SVG icon for each shape
const svg = buildPresetSVG(name);
btn.innerHTML = svg + '<span>' + PRESETS[name].label + '</span>';
btn.addEventListener('click', () => loadPreset(name));
presetsEl.appendChild(btn);
});

function buildPresetSVG(name) {
const size = 36;
const preset = PRESETS[name];
let path = '';

if (name === 'circle') {
return `<svg width="${size}" height="${size}" viewBox="0 0 100 100"><circle cx="50" cy="50" r="45" fill="#6366f1"/></svg>`;
}
if (name === 'ellipse') {
return `<svg width="${size}" height="${size}" viewBox="0 0 100 100"><ellipse cx="50" cy="50" rx="48" ry="30" fill="#6366f1"/></svg>`;
}
const pts = preset.points;
if (pts) {
path = pts.map((p, i) => (i === 0 ? 'M' : 'L') + p[0] + ',' + p[1]).join(' ') + 'Z';
return `<svg width="${size}" height="${size}" viewBox="0 0 100 100"><path d="${path}" fill="#6366f1"/></svg>`;
}
return `<svg width="${size}" height="${size}" viewBox="0 0 100 100"><rect width="100" height="100" fill="#6366f1"/></svg>`;
}

// Pointer events
function getCanvasPos(e) {
const rect = canvas.getBoundingClientRect();
const scaleX = canvas.width / rect.width;
const scaleY = canvas.height / rect.height;
const clientX = e.touches ? e.touches[0].clientX : e.clientX;
const clientY = e.touches ? e.touches[0].clientY : e.clientY;
return [(clientX - rect.left) * scaleX, (clientY - rect.top) * scaleY];
}

function hitTest(cx, cy) {
const radius = 14;
for (let i = points.length - 1; i >= 0; i--) {
const [px, py] = toCanvasPx(points[i][0], points[i][1]);
if (Math.hypot(cx - px, cy - py) < radius) return i;
}
return -1;
}

canvas.addEventListener('mousedown', onPointerDown);
canvas.addEventListener('touchstart', onPointerDown, {passive: false});

function onPointerDown(e) {
if (currentType !== 'polygon') return;
e.preventDefault();
const [cx, cy] = getCanvasPos(e);
const hit = hitTest(cx, cy);
if (hit >= 0) {
dragIndex = hit;
}
draw();
}

canvas.addEventListener('mousemove', onPointerMove);
canvas.addEventListener('touchmove', onPointerMove, {passive: false});

function onPointerMove(e) {
if (currentType !== 'polygon' || dragIndex < 0) return;
e.preventDefault();
const [cx, cy] = getCanvasPos(e);
const px = Math.max(0, Math.min(100, cx / canvas.width * 100));
const py = Math.max(0, Math.min(100, cy / canvas.height * 100));
points[dragIndex] = [px, py];
draw();
}

canvas.addEventListener('mouseup', onPointerUp);
canvas.addEventListener('touchend', onPointerUp);

function onPointerUp(e) {
dragIndex = -1;
draw();
}

canvas.addEventListener('contextmenu', (e) => {
if (currentType !== 'polygon') return;
e.preventDefault();
const [cx, cy] = getCanvasPos(e);
const hit = hitTest(cx, cy);
if (hit >= 0 && points.length > 3) {
points.splice(hit, 1);
draw();
}
});

// Double-click to add point
canvas.addEventListener('dblclick', (e) => {
if (currentType !== 'polygon') return;
const [cx, cy] = getCanvasPos(e);
const hit = hitTest(cx, cy);
if (hit >= 0) return; // don't add on existing point

// Find nearest edge to insert
const px = cx / canvas.width * 100;
const py = cy / canvas.height * 100;
let bestEdge = 0, bestDist = Infinity;
for (let i = 0; i < points.length; i++) {
const j = (i + 1) % points.length;
const [ax, ay] = points[i];
const [bx, by] = points[j];
const mx = (ax + bx) / 2, my = (ay + by) / 2;
const d = Math.hypot(px - mx, py - my);
if (d < bestDist) { bestDist = d; bestEdge = j; }
}
points.splice(bestEdge, 0, [px, py]);
draw();
});

// Colors
shapeColorInput.addEventListener('input', (e) => { shapeColor = e.target.value; draw(); });
bgColorInput.addEventListener('input', (e) => { bgColor = e.target.value; draw(); });

// Image upload
uploadBtn.addEventListener('click', () => fileInput.click());
fileInput.addEventListener('change', (e) => {
const file = e.target.files[0];
if (!file) return;
const reader = new FileReader();
reader.onload = (ev) => {
const img = new Image();
img.onload = () => {
uploadedImage = img;
clearImgBtn.style.display = 'block';
draw();
};
img.src = ev.target.result;
};
reader.readAsDataURL(file);
});
clearImgBtn.addEventListener('click', () => {
uploadedImage = null;
fileInput.value = '';
clearImgBtn.style.display = 'none';
draw();
});

// Copy CSS
copyBtn.addEventListener('click', () => {
const css = buildCSS();
navigator.clipboard.writeText(css).then(() => {
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('copied');
setTimeout(() => {
copyBtn.textContent = 'Copy CSS';
copyBtn.classList.remove('copied');
}, 2000);
});
});

// Reset
resetBtn.addEventListener('click', () => loadPreset(activePreset));

// Init
window.addEventListener('resize', resizeCanvas);
resizeCanvas();
loadPreset('triangle');
})();
</script>

---

## How to Use the CSS Clip-Path Maker

1. **Choose a preset** from the shape gallery — triangle, star, hexagon, and more.
2. **Drag the white control points** to reshape the polygon to your liking.
3. **Double-click** on the canvas to add new points along the nearest edge.
4. **Right-click** a point to remove it (minimum 3 points).
5. **Customize** the shape color and background color in the Preview panel.
6. **Upload an image** to see how your clip-path looks on a real photo.
7. **Copy the CSS** and paste it directly into your stylesheet.

## Understanding clip-path

The `clip-path` CSS property lets you define a visible region for an element — everything outside is hidden. The most flexible value is `polygon()`, which takes a list of percentage coordinates:

```css
/* Triangle */
clip-path: polygon(50% 0%, 0% 100%, 100% 100%);

/* Hexagon */
clip-path: polygon(25% 6%, 75% 6%, 100% 50%, 75% 94%, 25% 94%, 0% 50%);

/* Star */
clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
```

Other clip-path functions include `circle()`, `ellipse()`, and `inset()`.

## Browser Support

`clip-path` with `polygon()` is supported in all modern browsers (Chrome, Firefox, Safari, Edge). No vendor prefix needed as of 2025.

---

**Related Tools**

> Generate gradients → [Gradient Gallery](/tools/gradient-gallery/)

> CSS specificity → [CSS Specificity Calculator](/tools/css-specificity-calculator/)

</div>
