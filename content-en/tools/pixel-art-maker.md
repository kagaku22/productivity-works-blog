---
title: "Pixel Art Maker - Draw Pixel Art Online"
description: "Create pixel art with an interactive grid editor. Export as PNG. Free online pixel art drawing tool."
date: 2025-05-16
slug: "pixel-art-maker"
categories: ["Free Tools"]
tags: ["Image Tools", "Design", "Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/pixel-art-maker.png"
---

<div id="pam-app">

<style>
#pam-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 16px;
color: #222;
}
#pam-app h1 {
font-size: 1.6rem;
margin-bottom: 4px;
}
#pam-app p.pam-desc {
color: #555;
margin-top: 0;
margin-bottom: 16px;
}
#pam-app .pam-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 12px;
background: #f5f5f5;
border: 1px solid #ddd;
border-radius: 8px;
padding: 10px 12px;
}
#pam-app .pam-toolbar label {
font-size: 0.82rem;
color: #444;
margin-right: 2px;
}
#pam-app select, #pam-app button {
font-size: 0.85rem;
border: 1px solid #ccc;
border-radius: 5px;
padding: 4px 9px;
background: #fff;
cursor: pointer;
transition: background 0.15s;
}
#pam-app button:hover { background: #e8e8e8; }
#pam-app button.pam-active {
background: #3b82f6;
color: #fff;
border-color: #2563eb;
}
#pam-app .pam-color-wrap {
display: flex;
align-items: center;
gap: 6px;
}
#pam-app input[type=color] {
width: 34px;
height: 30px;
border: 1px solid #ccc;
border-radius: 5px;
padding: 1px;
cursor: pointer;
background: none;
}
#pam-app .pam-recent-colors {
display: flex;
gap: 4px;
align-items: center;
}
#pam-app .pam-recent-swatch {
width: 20px;
height: 20px;
border-radius: 3px;
border: 1px solid #aaa;
cursor: pointer;
flex-shrink: 0;
transition: transform 0.1s;
}
#pam-app .pam-recent-swatch:hover { transform: scale(1.2); }
#pam-app .pam-canvas-wrap {
display: flex;
justify-content: center;
margin-bottom: 12px;
overflow: auto;
}
#pam-app #pam-canvas {
display: block;
cursor: crosshair;
border: 2px solid #555;
image-rendering: pixelated;
image-rendering: crisp-edges;
}
#pam-app .pam-status {
font-size: 0.8rem;
color: #666;
text-align: center;
margin-bottom: 14px;
min-height: 18px;
}
#pam-app .pam-actions {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 20px;
}
#pam-app .pam-actions button {
padding: 6px 14px;
}
#pam-app .pam-related {
border-top: 1px solid #e0e0e0;
padding-top: 14px;
margin-top: 8px;
}
#pam-app .pam-related h3 {
font-size: 1rem;
margin-bottom: 8px;
color: #333;
}
#pam-app .pam-related ul {
list-style: disc;
padding-left: 20px;
font-size: 0.9rem;
line-height: 1.9;
}
#pam-app .pam-sep {
width: 1px;
height: 24px;
background: #ccc;
margin: 0 2px;
}
</style>

<p class="pam-desc">Draw pixel art in your browser — no sign-up, no install. Choose your grid size, pick colors, and download your creation as a PNG.</p>

<div class="pam-toolbar">
<label>Grid:</label>
<select id="pam-size-select">
<option value="16">16×16</option>
<option value="32" selected>32×32</option>
<option value="64">64×64</option>
</select>
<div class="pam-sep"></div>
<label>Color:</label>
<div class="pam-color-wrap">
<input type="color" id="pam-color" value="#3b82f6">
<div class="pam-recent-colors" id="pam-recent-colors"></div>
</div>
<div class="pam-sep"></div>
<button id="pam-tool-pencil" class="pam-active" title="Pencil">Pencil</button>
<button id="pam-tool-eraser" title="Eraser">Eraser</button>
<button id="pam-tool-fill" title="Fill Bucket">Fill</button>
<button id="pam-tool-eyedropper" title="Eyedropper">Eyedropper</button>
<div class="pam-sep"></div>
<button id="pam-grid-toggle">Hide Grid</button>
</div>

<div class="pam-canvas-wrap">
<canvas id="pam-canvas"></canvas>
</div>

<div class="pam-status" id="pam-status">Ready — click or drag to draw</div>

<div class="pam-actions">
<button id="pam-undo">Undo</button>
<button id="pam-redo">Redo</button>
<button id="pam-clear">Clear Canvas</button>
<button id="pam-download">Download PNG</button>
</div>

<script>
(function() {
var CANVAS_PX = 512;
var gridSize = 32;
var showGrid = true;
var currentTool = 'pencil';
var isDrawing = false;
var currentColor = '#3b82f6';
var recentColors = [];
var history = [];
var historyIndex = -1;
var MAX_HISTORY = 50;

var canvas = document.getElementById('pam-canvas');
var ctx = canvas.getContext('2d');
var colorInput = document.getElementById('pam-color');
var sizeSelect = document.getElementById('pam-size-select');
var statusEl = document.getElementById('pam-status');
var recentColorsEl = document.getElementById('pam-recent-colors');

var pixels = [];

function initPixels() {
pixels = [];
for (var i = 0; i < gridSize * gridSize; i++) {
pixels.push(null);
}
}

function cellSize() { return CANVAS_PX / gridSize; }

function setupCanvas() {
canvas.width = CANVAS_PX;
canvas.height = CANVAS_PX;
canvas.style.width = CANVAS_PX + 'px';
canvas.style.height = CANVAS_PX + 'px';
}

function hexToRgb(hex) {
var r = parseInt(hex.slice(1, 3), 16);
var g = parseInt(hex.slice(3, 5), 16);
var b = parseInt(hex.slice(5, 7), 16);
return [r, g, b, 255];
}

function rgbToHex(r, g, b) {
return '#' + [r, g, b].map(function(v) {
return ('0' + v.toString(16)).slice(-2);
}).join('');
}

function drawAll() {
var cs = cellSize();
ctx.clearRect(0, 0, CANVAS_PX, CANVAS_PX);
ctx.fillStyle = '#ffffff';
ctx.fillRect(0, 0, CANVAS_PX, CANVAS_PX);

for (var i = 0; i < gridSize; i++) {
for (var j = 0; j < gridSize; j++) {
var idx = i * gridSize + j;
if (pixels[idx]) {
ctx.fillStyle = pixels[idx];
ctx.fillRect(j * cs, i * cs, cs, cs);
}
}
}

if (showGrid) {
ctx.strokeStyle = 'rgba(180,180,180,0.5)';
ctx.lineWidth = 0.5;
for (var x = 0; x <= gridSize; x++) {
ctx.beginPath();
ctx.moveTo(x * cs, 0);
ctx.lineTo(x * cs, CANVAS_PX);
ctx.stroke();
}
for (var y = 0; y <= gridSize; y++) {
ctx.beginPath();
ctx.moveTo(0, y * cs);
ctx.lineTo(CANVAS_PX, y * cs);
ctx.stroke();
}
}
}

function getCell(e) {
var rect = canvas.getBoundingClientRect();
var scaleX = CANVAS_PX / rect.width;
var scaleY = CANVAS_PX / rect.height;
var x = Math.floor(((e.clientX - rect.left) * scaleX) / cellSize());
var y = Math.floor(((e.clientY - rect.top) * scaleY) / cellSize());
if (x < 0 || x >= gridSize || y < 0 || y >= gridSize) return null;
return { x: x, y: y };
}

function pushHistory() {
history.splice(historyIndex + 1);
history.push(pixels.slice());
if (history.length > MAX_HISTORY) history.shift();
historyIndex = history.length - 1;
}

function applyTool(cell, saveHist) {
if (!cell) return;
var idx = cell.y * gridSize + cell.x;
if (currentTool === 'pencil') {
pixels[idx] = currentColor;
drawAll();
} else if (currentTool === 'eraser') {
pixels[idx] = null;
drawAll();
} else if (currentTool === 'fill') {
var targetColor = pixels[idx];
if (targetColor === currentColor) return;
floodFill(cell.x, cell.y, targetColor, currentColor);
drawAll();
if (saveHist) pushHistory();
addRecentColor(currentColor);
return;
} else if (currentTool === 'eyedropper') {
var picked = pixels[idx] || '#ffffff';
currentColor = picked;
colorInput.value = picked;
setTool('pencil');
setStatus('Color picked: ' + picked);
return;
}
if (saveHist) pushHistory();
if (currentTool === 'pencil') addRecentColor(currentColor);
}

function floodFill(startX, startY, targetColor, fillColor) {
var stack = [[startX, startY]];
var visited = new Set();
while (stack.length > 0) {
var pos = stack.pop();
var x = pos[0], y = pos[1];
if (x < 0 || x >= gridSize || y < 0 || y >= gridSize) continue;
var key = y * gridSize + x;
if (visited.has(key)) continue;
if (pixels[key] !== targetColor) continue;
visited.add(key);
pixels[key] = fillColor;
stack.push([x + 1, y], [x - 1, y], [x, y + 1], [x, y - 1]);
}
}

function addRecentColor(hex) {
recentColors = recentColors.filter(function(c) { return c !== hex; });
recentColors.unshift(hex);
if (recentColors.length > 10) recentColors.length = 10;
renderRecentColors();
}

function renderRecentColors() {
recentColorsEl.innerHTML = '';
recentColors.forEach(function(c) {
var sw = document.createElement('div');
sw.className = 'pam-recent-swatch';
sw.style.background = c;
sw.title = c;
sw.addEventListener('click', function() {
currentColor = c;
colorInput.value = c;
});
recentColorsEl.appendChild(sw);
});
}

function setTool(tool) {
currentTool = tool;
['pencil','eraser','fill','eyedropper'].forEach(function(t) {
var btn = document.getElementById('pam-tool-' + t);
if (btn) btn.classList.toggle('pam-active', t === tool);
});
var cursors = { pencil: 'crosshair', eraser: 'cell', fill: 'copy', eyedropper: 'zoom-in' };
canvas.style.cursor = cursors[tool] || 'crosshair';
}

function setStatus(msg) {
statusEl.textContent = msg;
}

// Events
canvas.addEventListener('mousedown', function(e) {
e.preventDefault();
var cell = getCell(e);
if (!cell) return;
isDrawing = true;
if (currentTool === 'fill' || currentTool === 'eyedropper') {
applyTool(cell, true);
} else {
pushHistory();
applyTool(cell, false);
}
});

canvas.addEventListener('mousemove', function(e) {
var cell = getCell(e);
if (cell) setStatus('x: ' + cell.x + ', y: ' + cell.y);
if (!isDrawing) return;
if (currentTool === 'pencil' || currentTool === 'eraser') {
applyTool(cell, false);
}
});

canvas.addEventListener('mouseup', function() { isDrawing = false; });
canvas.addEventListener('mouseleave', function() { isDrawing = false; });

// Touch support
canvas.addEventListener('touchstart', function(e) {
e.preventDefault();
var touch = e.touches[0];
var cell = getCell(touch);
if (!cell) return;
isDrawing = true;
if (currentTool === 'fill' || currentTool === 'eyedropper') {
applyTool(cell, true);
} else {
pushHistory();
applyTool(cell, false);
}
}, { passive: false });

canvas.addEventListener('touchmove', function(e) {
e.preventDefault();
if (!isDrawing) return;
var touch = e.touches[0];
var cell = getCell(touch);
if (currentTool === 'pencil' || currentTool === 'eraser') {
applyTool(cell, false);
}
}, { passive: false });

canvas.addEventListener('touchend', function() { isDrawing = false; });

colorInput.addEventListener('input', function() {
currentColor = colorInput.value;
});

sizeSelect.addEventListener('change', function() {
if (!confirm('Changing grid size will clear the canvas. Continue?')) {
sizeSelect.value = String(gridSize);
return;
}
gridSize = parseInt(sizeSelect.value);
initPixels();
history = [];
historyIndex = -1;
drawAll();
setStatus('Grid changed to ' + gridSize + 'x' + gridSize);
});

document.getElementById('pam-tool-pencil').addEventListener('click', function() { setTool('pencil'); });
document.getElementById('pam-tool-eraser').addEventListener('click', function() { setTool('eraser'); });
document.getElementById('pam-tool-fill').addEventListener('click', function() { setTool('fill'); });
document.getElementById('pam-tool-eyedropper').addEventListener('click', function() { setTool('eyedropper'); });

document.getElementById('pam-grid-toggle').addEventListener('click', function() {
showGrid = !showGrid;
this.textContent = showGrid ? 'Hide Grid' : 'Show Grid';
drawAll();
});

document.getElementById('pam-undo').addEventListener('click', function() {
if (historyIndex <= 0) { setStatus('Nothing to undo'); return; }
historyIndex--;
pixels = history[historyIndex].slice();
drawAll();
setStatus('Undo');
});

document.getElementById('pam-redo').addEventListener('click', function() {
if (historyIndex >= history.length - 1) { setStatus('Nothing to redo'); return; }
historyIndex++;
pixels = history[historyIndex].slice();
drawAll();
setStatus('Redo');
});

document.getElementById('pam-clear').addEventListener('click', function() {
if (!confirm('Clear the entire canvas?')) return;
pushHistory();
initPixels();
drawAll();
setStatus('Canvas cleared');
});

document.getElementById('pam-download').addEventListener('click', function() {
var scale = gridSize <= 16 ? 16 : gridSize <= 32 ? 8 : 4;
var out = document.createElement('canvas');
out.width = gridSize * scale;
out.height = gridSize * scale;
var octx = out.getContext('2d');
octx.fillStyle = '#ffffff';
octx.fillRect(0, 0, out.width, out.height);
for (var i = 0; i < gridSize; i++) {
for (var j = 0; j < gridSize; j++) {
var c = pixels[i * gridSize + j];
if (c) {
octx.fillStyle = c;
octx.fillRect(j * scale, i * scale, scale, scale);
}
}
}
var link = document.createElement('a');
link.download = 'pixel-art-' + gridSize + 'x' + gridSize + '.png';
link.href = out.toDataURL('image/png');
link.click();
setStatus('Downloaded as PNG (' + (gridSize * scale) + 'x' + (gridSize * scale) + 'px)');
});

// Keyboard shortcuts
document.addEventListener('keydown', function(e) {
if (e.target.tagName === 'INPUT' || e.target.tagName === 'SELECT') return;
if (e.key === 'p' || e.key === 'P') setTool('pencil');
if (e.key === 'e' || e.key === 'E') setTool('eraser');
if (e.key === 'f' || e.key === 'F') setTool('fill');
if (e.key === 'i' || e.key === 'I') setTool('eyedropper');
if ((e.ctrlKey || e.metaKey) && e.key === 'z') {
e.preventDefault();
document.getElementById('pam-undo').click();
}
if ((e.ctrlKey || e.metaKey) && e.key === 'y') {
e.preventDefault();
document.getElementById('pam-redo').click();
}
});

// Init
setupCanvas();
initPixels();
pushHistory();
drawAll();
setStatus('Ready — click or drag to draw | Shortcuts: P=Pencil E=Eraser F=Fill I=Eyedropper Ctrl+Z=Undo');
})();
</script>

---

### Related Tools

<div class="pam-related">
<h3>Other Free Tools</h3>
<ul>
<li><a href="/tools/pomodoro-timer/">Pomodoro Timer — stay focused with timed work sessions</a></li>
<li><a href="/tools/character-counter/">Text Counter — count characters, words, and lines instantly</a></li>
<li><a href="/tools/color-palette-generator/">Color Palette Generator — create harmonious color schemes</a></li>
<li><a href="/tools/image-resizer/">Image Resizer — resize images in your browser without uploading</a></li>
</ul>
</div>

</div>
