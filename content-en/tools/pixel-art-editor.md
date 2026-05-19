---
title: "Pixel Art Editor"
date: 2025-05-16
description: "Free online pixel art editor. Draw pixel art on a customizable grid with color palette, tools, and PNG export — no sign-up required, fully client-side."
categories: ["Free Tools"]
slug: "pixel-art-editor"
ShowToc: false
cover:
  image: "/images/covers/pixel-art-editor.png"
  alt: "Pixel Art Editor"
---

<div id="px-app">

<style>
#px-app {
font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
background: #0f172a;
color: #e2e8f0;
padding: 16px;
border-radius: 12px;
user-select: none;
-webkit-user-select: none;
}

#px-app * {
box-sizing: border-box;
}

#px-app .px-header {
text-align: center;
margin-bottom: 14px;
}

#px-app .px-header h2 {
margin: 0 0 4px;
font-size: 1.3rem;
color: #f1f5f9;
font-weight: 700;
}

#px-app .px-header p {
margin: 0;
font-size: 0.8rem;
color: #94a3b8;
}

#px-app .px-layout {
display: flex;
gap: 14px;
align-items: flex-start;
flex-wrap: wrap;
justify-content: center;
}

/* ---- Sidebar ---- */
#px-app .px-sidebar {
display: flex;
flex-direction: column;
gap: 12px;
min-width: 180px;
max-width: 200px;
flex-shrink: 0;
}

#px-app .px-panel {
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
padding: 10px;
}

#px-app .px-panel-label {
font-size: 0.68rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #64748b;
margin-bottom: 8px;
}

/* ---- Tools ---- */
#px-app .px-tools {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 6px;
}

#px-app .px-tool-btn {
background: #0f172a;
border: 1px solid #334155;
color: #cbd5e1;
border-radius: 6px;
padding: 7px 4px;
cursor: pointer;
font-size: 0.72rem;
font-weight: 600;
text-align: center;
transition: background 0.15s, border-color 0.15s, color 0.15s;
display: flex;
flex-direction: column;
align-items: center;
gap: 3px;
}

#px-app .px-tool-btn:hover {
background: #1e3a5f;
border-color: #3b82f6;
color: #f1f5f9;
}

#px-app .px-tool-btn.active {
background: #1d4ed8;
border-color: #60a5fa;
color: #fff;
}

#px-app .px-tool-icon {
font-size: 1.1rem;
line-height: 1;
}

/* ---- Color palette ---- */
#px-app .px-palette-grid {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 4px;
margin-bottom: 8px;
}

#px-app .px-swatch {
width: 100%;
aspect-ratio: 1;
border-radius: 4px;
cursor: pointer;
border: 2px solid transparent;
transition: transform 0.1s, border-color 0.1s;
}

#px-app .px-swatch:hover {
transform: scale(1.15);
}

#px-app .px-swatch.selected {
border-color: #f1f5f9;
outline: 1px solid #1d4ed8;
}

#px-app .px-color-row {
display: flex;
align-items: center;
gap: 8px;
margin-top: 6px;
}

#px-app .px-current-color {
width: 32px;
height: 32px;
border-radius: 6px;
border: 2px solid #475569;
flex-shrink: 0;
}

#px-app .px-color-label {
font-size: 0.72rem;
color: #94a3b8;
flex: 1;
}

#px-app .px-custom-color {
width: 32px;
height: 32px;
padding: 0;
border: none;
border-radius: 6px;
cursor: pointer;
background: none;
overflow: hidden;
flex-shrink: 0;
}

#px-app .px-custom-color input[type="color"] {
width: 40px;
height: 40px;
margin: -4px 0 0 -4px;
cursor: pointer;
border: none;
padding: 0;
}

/* ---- Grid size ---- */
#px-app .px-size-btns {
display: flex;
gap: 4px;
flex-wrap: wrap;
}

#px-app .px-size-btn {
flex: 1;
min-width: 38px;
background: #0f172a;
border: 1px solid #334155;
color: #94a3b8;
border-radius: 5px;
padding: 5px 2px;
cursor: pointer;
font-size: 0.65rem;
font-weight: 600;
text-align: center;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}

#px-app .px-size-btn:hover {
background: #1e3a5f;
border-color: #3b82f6;
color: #f1f5f9;
}

#px-app .px-size-btn.active {
background: #155e75;
border-color: #22d3ee;
color: #fff;
}

/* ---- Action buttons ---- */
#px-app .px-actions {
display: flex;
flex-direction: column;
gap: 6px;
}

#px-app .px-btn {
background: #0f172a;
border: 1px solid #334155;
color: #cbd5e1;
border-radius: 6px;
padding: 7px 10px;
cursor: pointer;
font-size: 0.75rem;
font-weight: 600;
text-align: center;
width: 100%;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}

#px-app .px-btn:hover {
background: #1e3a5f;
border-color: #3b82f6;
color: #f1f5f9;
}

#px-app .px-btn:disabled {
opacity: 0.35;
cursor: default;
}

#px-app .px-btn.danger:hover {
background: #7f1d1d;
border-color: #f87171;
color: #fff;
}

#px-app .px-btn.success {
background: #14532d;
border-color: #4ade80;
color: #bbf7d0;
}

#px-app .px-btn.success:hover {
background: #166534;
border-color: #86efac;
color: #fff;
}

#px-app .px-btn-row {
display: flex;
gap: 6px;
}

#px-app .px-btn-row .px-btn {
flex: 1;
}

/* ---- Zoom ---- */
#px-app .px-zoom-row {
display: flex;
align-items: center;
gap: 6px;
}

#px-app .px-zoom-btn {
background: #0f172a;
border: 1px solid #334155;
color: #cbd5e1;
border-radius: 5px;
width: 28px;
height: 28px;
cursor: pointer;
font-size: 1rem;
font-weight: 700;
line-height: 1;
display: flex;
align-items: center;
justify-content: center;
transition: background 0.15s, border-color 0.15s;
flex-shrink: 0;
}

#px-app .px-zoom-btn:hover {
background: #1e3a5f;
border-color: #3b82f6;
}

#px-app .px-zoom-label {
flex: 1;
text-align: center;
font-size: 0.75rem;
color: #94a3b8;
font-weight: 600;
}

/* ---- Toggle ---- */
#px-app .px-toggle-row {
display: flex;
align-items: center;
gap: 8px;
}

#px-app .px-toggle {
position: relative;
width: 36px;
height: 20px;
flex-shrink: 0;
}

#px-app .px-toggle input {
opacity: 0;
width: 0;
height: 0;
position: absolute;
}

#px-app .px-toggle-slider {
position: absolute;
inset: 0;
background: #334155;
border-radius: 20px;
cursor: pointer;
transition: background 0.2s;
}

#px-app .px-toggle-slider::before {
content: '';
position: absolute;
width: 14px;
height: 14px;
background: #94a3b8;
border-radius: 50%;
top: 3px;
left: 3px;
transition: transform 0.2s, background 0.2s;
}

#px-app .px-toggle input:checked + .px-toggle-slider {
background: #1d4ed8;
}

#px-app .px-toggle input:checked + .px-toggle-slider::before {
transform: translateX(16px);
background: #fff;
}

#px-app .px-toggle-label {
font-size: 0.75rem;
color: #94a3b8;
}

/* ---- Canvas area ---- */
#px-app .px-canvas-wrap {
flex: 1;
min-width: 280px;
display: flex;
flex-direction: column;
align-items: center;
gap: 10px;
}

#px-app .px-canvas-scroll {
overflow: auto;
max-width: 100%;
border-radius: 8px;
background: #1e293b;
border: 1px solid #334155;
padding: 8px;
}

#px-app #px-canvas {
display: block;
cursor: crosshair;
image-rendering: pixelated;
image-rendering: crisp-edges;
}

#px-app .px-status {
font-size: 0.7rem;
color: #475569;
text-align: center;
}

/* ---- Responsive ---- */
@media (max-width: 600px) {
#px-app .px-layout {
flex-direction: column;
align-items: center;
}

#px-app .px-sidebar {
flex-direction: row;
flex-wrap: wrap;
max-width: 100%;
width: 100%;
min-width: unset;
}

#px-app .px-panel {
flex: 1;
min-width: 140px;
}
}
</style>

<div class="px-header">
<h2>Pixel Art Editor</h2>
<p>Draw on a grid, choose colors, export PNG — fully offline, no sign-up.</p>
</div>

<div class="px-layout">

<!-- Sidebar -->
<div class="px-sidebar">

<!-- Tools -->
<div class="px-panel">
<div class="px-panel-label">Tool</div>
<div class="px-tools">
<button class="px-tool-btn active" id="px-tool-pen" title="Pen (P)">
<span class="px-tool-icon">&#9998;</span>Pen
</button>
<button class="px-tool-btn" id="px-tool-eraser" title="Eraser (E)">
<span class="px-tool-icon">&#9641;</span>Eraser
</button>
<button class="px-tool-btn" id="px-tool-fill" title="Fill (F)">
<span class="px-tool-icon">&#9724;</span>Fill
</button>
<button class="px-tool-btn" id="px-tool-picker" title="Eyedropper (I)">
<span class="px-tool-icon">&#128451;</span>Pick
</button>
</div>
</div>

<!-- Color -->
<div class="px-panel">
<div class="px-panel-label">Color</div>
<div class="px-palette-grid" id="px-palette"></div>
<div class="px-color-row">
<div class="px-current-color" id="px-current-color-swatch"></div>
<span class="px-color-label" id="px-current-color-hex">#000000</span>
<label class="px-custom-color" title="Custom color">
<input type="color" id="px-custom-color-input" value="#000000">
</label>
</div>
</div>

<!-- Grid size -->
<div class="px-panel">
<div class="px-panel-label">Grid Size</div>
<div class="px-size-btns">
<button class="px-size-btn" data-size="8">8x8</button>
<button class="px-size-btn active" data-size="16">16x16</button>
<button class="px-size-btn" data-size="32">32x32</button>
<button class="px-size-btn" data-size="64">64x64</button>
</div>
</div>

<!-- View -->
<div class="px-panel">
<div class="px-panel-label">View</div>
<div class="px-zoom-row" style="margin-bottom:8px;">
<button class="px-zoom-btn" id="px-zoom-out">&#8722;</button>
<span class="px-zoom-label" id="px-zoom-label">1x</span>
<button class="px-zoom-btn" id="px-zoom-in">&#43;</button>
</div>
<div class="px-toggle-row">
<label class="px-toggle">
<input type="checkbox" id="px-grid-toggle" checked>
<span class="px-toggle-slider"></span>
</label>
<span class="px-toggle-label">Show grid</span>
</div>
</div>

<!-- Actions -->
<div class="px-panel">
<div class="px-panel-label">Actions</div>
<div class="px-actions">
<div class="px-btn-row">
<button class="px-btn" id="px-undo" title="Undo (Ctrl+Z)" disabled>&#8592; Undo</button>
<button class="px-btn" id="px-redo" title="Redo (Ctrl+Y)" disabled>Redo &#8594;</button>
</div>
<button class="px-btn danger" id="px-clear">Clear Canvas</button>
<button class="px-btn success" id="px-export">&#8595; Export PNG</button>
</div>
</div>

</div><!-- /sidebar -->

<!-- Canvas -->
<div class="px-canvas-wrap">
<div class="px-canvas-scroll">
<canvas id="px-canvas"></canvas>
</div>
<div class="px-status" id="px-status">16 &times; 16 &mdash; hover over canvas to begin drawing</div>
</div>

</div><!-- /layout -->

<script>
(function () {
'use strict';

// ---- State ----
var GRID_SIZES = [8, 16, 32, 64];
var ZOOM_LEVELS = [1, 2, 4, 6, 8, 12, 16, 20];
var MAX_HISTORY = 20;
var EXPORT_SCALE = 512; // exported PNG will be EXPORT_SCALE px on each side

var PALETTE = [
'#1e293b','#334155','#64748b','#e2e8f0',
'#ef4444','#f97316','#eab308','#22c55e',
'#14b8a6','#3b82f6','#8b5cf6','#ec4899',
'#fef9c3','#d1fae5','#dbeafe','#ffffff'
];

var state = {
gridSize: 16,
zoomIdx: 2,        // index into ZOOM_LEVELS (default 4x)
tool: 'pen',
color: '#3b82f6',
showGrid: true,
pixels: [],        // flat array [row * gridSize + col] = color string or null
history: [],       // array of snapshots
historyIdx: -1,
isDrawing: false,
lastCell: null,    // {r, c} — avoid redrawing same cell on drag
paletteSelectedIdx: 5,  // index of selected preset swatch (matches #3b82f6)
};

// ---- DOM refs ----
var canvas = document.getElementById('px-canvas');
var ctx = canvas.getContext('2d');
var paletteEl = document.getElementById('px-palette');
var currentColorSwatch = document.getElementById('px-current-color-swatch');
var currentColorHex = document.getElementById('px-current-color-hex');
var customColorInput = document.getElementById('px-custom-color-input');
var zoomLabel = document.getElementById('px-zoom-label');
var statusEl = document.getElementById('px-status');
var undoBtn = document.getElementById('px-undo');
var redoBtn = document.getElementById('px-redo');

// ---- Helpers ----
function cellSize() {
return ZOOM_LEVELS[state.zoomIdx];
}

function canvasSize() {
return state.gridSize * cellSize();
}

function initPixels(size) {
state.pixels = new Array(size * size).fill(null);
}

function pixelIndex(r, c) {
return r * state.gridSize + c;
}

// ---- History ----
function snapshot() {
// Trim forward history
state.history = state.history.slice(0, state.historyIdx + 1);
state.history.push(state.pixels.slice());
if (state.history.length > MAX_HISTORY) {
state.history.shift();
}
state.historyIdx = state.history.length - 1;
updateUndoRedo();
}

function undo() {
if (state.historyIdx <= 0) return;
state.historyIdx--;
state.pixels = state.history[state.historyIdx].slice();
render();
updateUndoRedo();
}

function redo() {
if (state.historyIdx >= state.history.length - 1) return;
state.historyIdx++;
state.pixels = state.history[state.historyIdx].slice();
render();
updateUndoRedo();
}

function updateUndoRedo() {
undoBtn.disabled = state.historyIdx <= 0;
redoBtn.disabled = state.historyIdx >= state.history.length - 1;
}

// ---- Render ----
function applyCanvasSize() {
var sz = canvasSize();
canvas.width = sz;
canvas.height = sz;
canvas.style.width = sz + 'px';
canvas.style.height = sz + 'px';
}

function render() {
var cs = cellSize();
var gs = state.gridSize;
var sz = canvasSize();

ctx.clearRect(0, 0, sz, sz);

// Background (transparent checkerboard feel)
ctx.fillStyle = '#0f172a';
ctx.fillRect(0, 0, sz, sz);

// Draw pixels
for (var i = 0; i < state.pixels.length; i++) {
var color = state.pixels[i];
if (!color) continue;
var r = Math.floor(i / gs);
var c = i % gs;
ctx.fillStyle = color;
ctx.fillRect(c * cs, r * cs, cs, cs);
}

// Grid lines
if (state.showGrid && cs >= 2) {
ctx.strokeStyle = 'rgba(148,163,184,0.2)';
ctx.lineWidth = 1;
ctx.beginPath();
for (var col = 0; col <= gs; col++) {
ctx.moveTo(col * cs + 0.5, 0);
ctx.lineTo(col * cs + 0.5, sz);
}
for (var row = 0; row <= gs; row++) {
ctx.moveTo(0, row * cs + 0.5);
ctx.lineTo(sz, row * cs + 0.5);
}
ctx.stroke();
}
}

// ---- Flood fill ----
function floodFill(startR, startC, fillColor) {
var gs = state.gridSize;
var targetColor = state.pixels[pixelIndex(startR, startC)];
if (targetColor === fillColor) return false;

var stack = [[startR, startC]];
var visited = new Uint8Array(gs * gs);

while (stack.length) {
var cell = stack.pop();
var r = cell[0], c = cell[1];
if (r < 0 || r >= gs || c < 0 || c >= gs) continue;
var idx = pixelIndex(r, c);
if (visited[idx]) continue;
visited[idx] = 1;
if (state.pixels[idx] !== targetColor) continue;
state.pixels[idx] = fillColor;
stack.push([r + 1, c], [r - 1, c], [r, c + 1], [r, c - 1]);
}
return true;
}

// ---- Cell from event ----
function cellFromEvent(e) {
var rect = canvas.getBoundingClientRect();
var scaleX = canvas.width / rect.width;
var scaleY = canvas.height / rect.height;
var cs = cellSize();
var x = (e.clientX - rect.left) * scaleX;
var y = (e.clientY - rect.top) * scaleY;
var c = Math.floor(x / cs);
var r = Math.floor(y / cs);
var gs = state.gridSize;
if (r < 0 || r >= gs || c < 0 || c >= gs) return null;
return { r: r, c: c };
}

function cellKey(cell) {
return cell.r + ',' + cell.c;
}

// ---- Paint ----
function paintCell(cell, colorOverride) {
var color = colorOverride !== undefined ? colorOverride : state.color;
var idx = pixelIndex(cell.r, cell.c);
if (state.pixels[idx] === color) return;
state.pixels[idx] = color;
// Fast partial redraw: just redraw the cell
var cs = cellSize();
if (color) {
ctx.fillStyle = color;
ctx.fillRect(cell.c * cs, cell.r * cs, cs, cs);
} else {
ctx.fillStyle = '#0f172a';
ctx.fillRect(cell.c * cs, cell.r * cs, cs, cs);
}
// Redraw grid lines over this cell if needed
if (state.showGrid && cs >= 2) {
ctx.strokeStyle = 'rgba(148,163,184,0.2)';
ctx.lineWidth = 1;
ctx.strokeRect(cell.c * cs + 0.5, cell.r * cs + 0.5, cs - 1, cs - 1);
}
}

function handleDraw(e, isNew) {
var cell = cellFromEvent(e);
if (!cell) return;
if (!isNew && state.lastCell && cellKey(cell) === cellKey(state.lastCell)) return;
state.lastCell = cell;

if (state.tool === 'pen') {
paintCell(cell, state.color);
} else if (state.tool === 'eraser') {
paintCell(cell, null);
} else if (state.tool === 'fill' && isNew) {
var changed = floodFill(cell.r, cell.c, state.color);
if (changed) render();
} else if (state.tool === 'picker' && isNew) {
var picked = state.pixels[pixelIndex(cell.r, cell.c)];
if (picked) {
setColor(picked);
setTool('pen');
}
}

updateStatus(cell);
}

// ---- Color ----
function setColor(hex) {
state.color = hex;
currentColorSwatch.style.background = hex;
currentColorHex.textContent = hex;
customColorInput.value = hex;
// Update palette selection
var idx = PALETTE.indexOf(hex);
updatePaletteSelection(idx);
}

function updatePaletteSelection(idx) {
state.paletteSelectedIdx = idx;
var swatches = paletteEl.querySelectorAll('.px-swatch');
swatches.forEach(function (sw, i) {
sw.classList.toggle('selected', i === idx);
});
}

// ---- Tool ----
function setTool(name) {
state.tool = name;
var toolBtns = ['pen','eraser','fill','picker'];
toolBtns.forEach(function (t) {
var el = document.getElementById('px-tool-' + t);
if (el) el.classList.toggle('active', t === name);
});
canvas.style.cursor = name === 'picker' ? 'crosshair' : 'crosshair';
}

// ---- Grid size ----
function setGridSize(size) {
if (state.gridSize === size) return;
// Confirm if canvas not empty
var hasContent = state.pixels.some(function (p) { return p !== null; });
if (hasContent && !confirm('Changing grid size will clear the canvas. Continue?')) return;
state.gridSize = size;
initPixels(size);
state.history = [];
state.historyIdx = -1;
updateUndoRedo();
applyCanvasSize();
snapshot();
render();
updateSizeButtons();
updateStatusDefault();
}

function updateSizeButtons() {
document.querySelectorAll('#px-app .px-size-btn').forEach(function (btn) {
btn.classList.toggle('active', parseInt(btn.dataset.size) === state.gridSize);
});
}

// ---- Zoom ----
function setZoom(idx) {
state.zoomIdx = Math.max(0, Math.min(ZOOM_LEVELS.length - 1, idx));
zoomLabel.textContent = ZOOM_LEVELS[state.zoomIdx] + 'x';
applyCanvasSize();
render();
}

// ---- Status ----
function updateStatus(cell) {
statusEl.textContent = state.gridSize + ' \u00d7 ' + state.gridSize +
' \u2014 (' + cell.c + ', ' + cell.r + ')';
}

function updateStatusDefault() {
statusEl.textContent = state.gridSize + ' \u00d7 ' + state.gridSize +
' \u2014 hover over canvas to begin drawing';
}

// ---- Build palette ----
function buildPalette() {
paletteEl.innerHTML = '';
PALETTE.forEach(function (hex, i) {
var sw = document.createElement('div');
sw.className = 'px-swatch';
sw.style.background = hex;
sw.title = hex;
if (i === state.paletteSelectedIdx) sw.classList.add('selected');
sw.addEventListener('click', function () {
setColor(hex);
});
paletteEl.appendChild(sw);
});
}

// ---- Export PNG ----
function exportPNG() {
var gs = state.gridSize;
var scale = Math.ceil(EXPORT_SCALE / gs);
var offscreen = document.createElement('canvas');
offscreen.width = gs * scale;
offscreen.height = gs * scale;
var octx = offscreen.getContext('2d');
octx.imageSmoothingEnabled = false;

// Background
octx.fillStyle = '#0f172a';
octx.fillRect(0, 0, offscreen.width, offscreen.height);

for (var i = 0; i < state.pixels.length; i++) {
var color = state.pixels[i];
if (!color) continue;
var r = Math.floor(i / gs);
var c = i % gs;
octx.fillStyle = color;
octx.fillRect(c * scale, r * scale, scale, scale);
}

var link = document.createElement('a');
link.download = 'pixel-art-' + gs + 'x' + gs + '.png';
link.href = offscreen.toDataURL('image/png');
link.click();
}

// ---- Event listeners ----

// Canvas mouse
canvas.addEventListener('mousedown', function (e) {
e.preventDefault();
if (e.button === 2) {
// Right-click = erase
var prevTool = state.tool;
state.tool = 'eraser';
state.isDrawing = true;
state.lastCell = null;
snapshot();
handleDraw(e, true);
state.tool = prevTool;
state._rightErase = true;
} else {
state.isDrawing = true;
state.lastCell = null;
if (state.tool !== 'fill' && state.tool !== 'picker') snapshot();
handleDraw(e, true);
}
});

canvas.addEventListener('mousemove', function (e) {
if (!state.isDrawing) return;
if (state._rightErase) {
var prevTool = state.tool;
state.tool = 'eraser';
handleDraw(e, false);
state.tool = prevTool;
} else {
handleDraw(e, false);
}
});

window.addEventListener('mouseup', function () {
if (state.isDrawing && (state.tool === 'fill' || state.tool === 'picker')) {
snapshot();
}
state.isDrawing = false;
state._rightErase = false;
});

canvas.addEventListener('contextmenu', function (e) {
e.preventDefault();
});

// Touch support
canvas.addEventListener('touchstart', function (e) {
e.preventDefault();
state.isDrawing = true;
state.lastCell = null;
if (state.tool !== 'fill' && state.tool !== 'picker') snapshot();
handleDraw(e.touches[0], true);
}, { passive: false });

canvas.addEventListener('touchmove', function (e) {
e.preventDefault();
if (!state.isDrawing) return;
handleDraw(e.touches[0], false);
}, { passive: false });

canvas.addEventListener('touchend', function () {
if (state.isDrawing && (state.tool === 'fill' || state.tool === 'picker')) {
snapshot();
}
state.isDrawing = false;
});

// Tool buttons
['pen','eraser','fill','picker'].forEach(function (t) {
var el = document.getElementById('px-tool-' + t);
if (el) el.addEventListener('click', function () { setTool(t); });
});

// Grid size buttons
document.querySelectorAll('#px-app .px-size-btn').forEach(function (btn) {
btn.addEventListener('click', function () {
setGridSize(parseInt(btn.dataset.size));
});
});

// Zoom
document.getElementById('px-zoom-in').addEventListener('click', function () {
setZoom(state.zoomIdx + 1);
});
document.getElementById('px-zoom-out').addEventListener('click', function () {
setZoom(state.zoomIdx - 1);
});

// Grid toggle
document.getElementById('px-grid-toggle').addEventListener('change', function (e) {
state.showGrid = e.target.checked;
render();
});

// Custom color
customColorInput.addEventListener('input', function (e) {
setColor(e.target.value);
});

// Undo / Redo
undoBtn.addEventListener('click', undo);
redoBtn.addEventListener('click', redo);

// Clear
document.getElementById('px-clear').addEventListener('click', function () {
if (!confirm('Clear the entire canvas?')) return;
initPixels(state.gridSize);
snapshot();
render();
});

// Export
document.getElementById('px-export').addEventListener('click', exportPNG);

// Keyboard shortcuts
document.addEventListener('keydown', function (e) {
// Only if focus is not in an input
if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') return;
if ((e.ctrlKey || e.metaKey) && e.key === 'z') { e.preventDefault(); undo(); return; }
if ((e.ctrlKey || e.metaKey) && (e.key === 'y' || (e.shiftKey && e.key === 'z'))) { e.preventDefault(); redo(); return; }
switch (e.key.toLowerCase()) {
case 'p': setTool('pen'); break;
case 'e': setTool('eraser'); break;
case 'f': setTool('fill'); break;
case 'i': setTool('picker'); break;
case '+': case '=': setZoom(state.zoomIdx + 1); break;
case '-': setZoom(state.zoomIdx - 1); break;
}
});

// ---- Init ----
function init() {
initPixels(state.gridSize);
buildPalette();
setColor(state.color);
setZoom(state.zoomIdx);
applyCanvasSize();
snapshot();
render();
updateStatusDefault();
}

init();

})();
</script>

</div>

---

**Keyboard Shortcuts**

| Key | Action |
|-----|--------|
| P | Pen tool |
| E | Eraser tool |
| F | Fill tool |
| I | Color picker (eyedropper) |
| Ctrl + Z | Undo |
| Ctrl + Y | Redo |
| + / - | Zoom in / out |

**Tips**

- Right-click (or right-drag) on the canvas to erase pixels quickly.
- Use Fill (F) to flood-fill a region with the current color.
- Exported PNG is scaled up to 512 px for crisp results — safe to use in projects.
- Switch to 64x64 grid for detailed sprites; 8x8 for retro icons.

---

> Generate ASCII art from text → [ASCII Art Generator](/tools/ascii-art-generator/)

> Pick colors from images → [Image Color Picker](/tools/image-color-picker/)

> Create placeholder images → [Placeholder Image Generator](/tools/placeholder-image/)
