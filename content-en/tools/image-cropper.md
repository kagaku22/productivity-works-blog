---
title: "Image Cropper - Free Online Crop Tool"
date: 2025-05-16
description: "Free online image cropper. Upload any image and crop it with a draggable selection box. Fixed aspect ratio options, rotate, and download as PNG or JPEG."
categories: ["Free Tools"]
tags: ["image cropper", "crop image", "online crop tool", "image editor", "canvas api", "free tool"]
slug: "image-cropper"
cover:
  image: "/images/covers/image-cropper.png"
  alt: "Image Cropper - Free Online Crop Tool"
ShowToc: false
---

<div id="ic-app">

<style>
#ic-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 48px 0;
color: #1a202c;
}

#ic-app * {
box-sizing: border-box;
}

/* Hero */
#ic-app .ic-hero {
background: linear-gradient(135deg, #7c3aed 0%, #6d28d9 50%, #4c1d95 100%);
border-radius: 16px;
padding: 32px 28px;
margin-bottom: 24px;
color: #fff;
}

#ic-app .ic-hero h2 {
margin: 0 0 6px 0;
font-size: 24px;
font-weight: 800;
}

#ic-app .ic-hero p {
margin: 0;
font-size: 14px;
opacity: 0.88;
line-height: 1.6;
}

/* Drop Zone */
#ic-app .ic-dropzone {
border: 3px dashed #7c3aed;
border-radius: 14px;
padding: 44px 24px;
text-align: center;
background: #f5f3ff;
cursor: pointer;
transition: background 0.2s, border-color 0.2s;
margin-bottom: 20px;
position: relative;
}

#ic-app .ic-dropzone.drag-over {
background: #ede9fe;
border-color: #6d28d9;
}

#ic-app .ic-dropzone-icon {
font-size: 48px;
line-height: 1;
margin-bottom: 12px;
display: block;
}

#ic-app .ic-dropzone-title {
font-size: 17px;
font-weight: 700;
color: #4c1d95;
margin-bottom: 6px;
}

#ic-app .ic-dropzone-sub {
font-size: 13px;
color: #6b7280;
}

#ic-app .ic-dropzone input[type="file"] {
position: absolute;
inset: 0;
opacity: 0;
cursor: pointer;
width: 100%;
height: 100%;
}

/* Main layout */
#ic-app .ic-main {
display: none;
gap: 20px;
flex-direction: column;
}

#ic-app .ic-main.visible {
display: flex;
}

/* Toolbar */
#ic-app .ic-toolbar {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 12px;
padding: 16px 18px;
display: flex;
flex-wrap: wrap;
gap: 12px;
align-items: center;
}

#ic-app .ic-toolbar-group {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
}

#ic-app .ic-toolbar-label {
font-size: 12px;
font-weight: 700;
color: #6b7280;
text-transform: uppercase;
letter-spacing: 0.04em;
white-space: nowrap;
}

#ic-app .ic-toolbar-sep {
width: 1px;
height: 28px;
background: #e5e7eb;
}

#ic-app .ic-ratio-btn {
padding: 5px 12px;
border: 1.5px solid #d1d5db;
border-radius: 7px;
background: #fff;
font-size: 13px;
font-weight: 600;
color: #374151;
cursor: pointer;
transition: all 0.15s;
white-space: nowrap;
}

#ic-app .ic-ratio-btn:hover {
border-color: #7c3aed;
color: #7c3aed;
}

#ic-app .ic-ratio-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

#ic-app .ic-tool-btn {
padding: 6px 14px;
border: 1.5px solid #d1d5db;
border-radius: 7px;
background: #fff;
font-size: 13px;
font-weight: 600;
color: #374151;
cursor: pointer;
transition: all 0.15s;
display: flex;
align-items: center;
gap: 5px;
white-space: nowrap;
}

#ic-app .ic-tool-btn:hover {
border-color: #7c3aed;
color: #7c3aed;
}

/* Zoom */
#ic-app .ic-zoom-wrap {
display: flex;
align-items: center;
gap: 8px;
}

#ic-app .ic-zoom-slider {
-webkit-appearance: none;
appearance: none;
width: 100px;
height: 4px;
border-radius: 2px;
background: #e5e7eb;
outline: none;
cursor: pointer;
}

#ic-app .ic-zoom-slider::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 16px;
height: 16px;
border-radius: 50%;
background: #7c3aed;
cursor: pointer;
}

#ic-app .ic-zoom-val {
font-size: 12px;
font-weight: 700;
color: #374151;
min-width: 36px;
text-align: right;
}

/* Canvas wrapper */
#ic-app .ic-canvas-wrap {
background: #111827;
border-radius: 12px;
overflow: hidden;
position: relative;
display: flex;
align-items: center;
justify-content: center;
min-height: 300px;
max-height: 560px;
}

#ic-app #ic-canvas {
display: block;
cursor: crosshair;
max-width: 100%;
max-height: 560px;
user-select: none;
-webkit-user-select: none;
}

/* File info */
#ic-app .ic-info-bar {
display: flex;
flex-wrap: wrap;
gap: 10px;
font-size: 12px;
color: #6b7280;
padding: 0 2px;
}

#ic-app .ic-info-item {
background: #f3f4f6;
border-radius: 6px;
padding: 4px 10px;
font-weight: 600;
}

#ic-app .ic-info-item span {
color: #374151;
}

/* Preview + Download */
#ic-app .ic-bottom {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
}

@media (max-width: 600px) {
#ic-app .ic-bottom {
grid-template-columns: 1fr;
}
}

#ic-app .ic-preview-box {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 12px;
padding: 16px;
}

#ic-app .ic-preview-title {
font-size: 13px;
font-weight: 700;
color: #374151;
margin-bottom: 10px;
}

#ic-app .ic-preview-canvas-wrap {
background: repeating-conic-gradient(#e5e7eb 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
border-radius: 8px;
min-height: 100px;
display: flex;
align-items: center;
justify-content: center;
overflow: hidden;
}

#ic-app #ic-preview-canvas {
display: block;
max-width: 100%;
max-height: 220px;
border-radius: 4px;
}

#ic-app .ic-preview-dims {
font-size: 11px;
color: #9ca3af;
margin-top: 8px;
text-align: center;
}

/* Download panel */
#ic-app .ic-dl-box {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 12px;
padding: 16px;
display: flex;
flex-direction: column;
gap: 12px;
}

#ic-app .ic-dl-title {
font-size: 13px;
font-weight: 700;
color: #374151;
}

#ic-app .ic-fmt-row {
display: flex;
gap: 8px;
}

#ic-app .ic-fmt-btn {
flex: 1;
padding: 7px 0;
border: 1.5px solid #d1d5db;
border-radius: 7px;
background: #fff;
font-size: 13px;
font-weight: 700;
color: #374151;
cursor: pointer;
transition: all 0.15s;
text-align: center;
}

#ic-app .ic-fmt-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

#ic-app .ic-fmt-btn:hover:not(.active) {
border-color: #7c3aed;
color: #7c3aed;
}

#ic-app .ic-quality-row {
display: flex;
flex-direction: column;
gap: 6px;
}

#ic-app .ic-quality-label {
font-size: 12px;
font-weight: 600;
color: #6b7280;
display: flex;
justify-content: space-between;
}

#ic-app .ic-quality-slider {
-webkit-appearance: none;
appearance: none;
width: 100%;
height: 4px;
border-radius: 2px;
background: #e5e7eb;
outline: none;
cursor: pointer;
}

#ic-app .ic-quality-slider::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 16px;
height: 16px;
border-radius: 50%;
background: #7c3aed;
cursor: pointer;
}

#ic-app .ic-dl-btn {
display: block;
width: 100%;
padding: 13px 0;
background: linear-gradient(135deg, #7c3aed, #6d28d9);
color: #fff;
border: none;
border-radius: 10px;
font-size: 15px;
font-weight: 800;
cursor: pointer;
transition: opacity 0.15s;
text-align: center;
}

#ic-app .ic-dl-btn:hover {
opacity: 0.88;
}

#ic-app .ic-dl-btn:disabled {
opacity: 0.4;
cursor: not-allowed;
}

/* Selection info */
#ic-app .ic-sel-info {
font-size: 12px;
color: #6b7280;
text-align: center;
padding: 6px 0 0;
}

#ic-app .ic-sel-info span {
font-weight: 700;
color: #4c1d95;
}

/* Hint */
#ic-app .ic-hint {
background: #f5f3ff;
border-left: 4px solid #7c3aed;
border-radius: 0 8px 8px 0;
padding: 10px 14px;
font-size: 13px;
color: #4c1d95;
line-height: 1.6;
}
</style>

<!-- Hero -->
<div class="ic-hero">
<h2>✂️ Image Cropper</h2>
<p>Upload an image, drag the selection box to choose your crop area, then download as PNG or JPEG. Works entirely in your browser — nothing is uploaded to any server.</p>
</div>

<!-- Drop Zone -->
<div class="ic-dropzone" id="ic-dropzone">
<input type="file" id="ic-file-input" accept="image/*">
<span class="ic-dropzone-icon">🖼️</span>
<div class="ic-dropzone-title">Drop an image here or click to browse</div>
<div class="ic-dropzone-sub">Supports JPG, PNG, WebP, GIF, BMP &mdash; up to 20 MB</div>
</div>

<!-- Main (hidden until image loaded) -->
<div class="ic-main" id="ic-main">

<!-- Toolbar -->
<div class="ic-toolbar">
<div class="ic-toolbar-group">
<span class="ic-toolbar-label">Ratio</span>
<button class="ic-ratio-btn active" data-ratio="free">Free</button>
<button class="ic-ratio-btn" data-ratio="1">1:1</button>
<button class="ic-ratio-btn" data-ratio="1.3333">4:3</button>
<button class="ic-ratio-btn" data-ratio="1.7778">16:9</button>
<button class="ic-ratio-btn" data-ratio="1.5">3:2</button>
</div>
<div class="ic-toolbar-sep"></div>
<div class="ic-toolbar-group">
<span class="ic-toolbar-label">Transform</span>
<button class="ic-tool-btn" id="ic-rotate-btn">↻ Rotate 90°</button>
<button class="ic-tool-btn" id="ic-flip-h-btn">↔ Flip H</button>
<button class="ic-tool-btn" id="ic-flip-v-btn">↕ Flip V</button>
</div>
<div class="ic-toolbar-sep"></div>
<div class="ic-toolbar-group">
<span class="ic-toolbar-label">Zoom</span>
<div class="ic-zoom-wrap">
<input type="range" class="ic-zoom-slider" id="ic-zoom-slider" min="10" max="300" value="100">
<span class="ic-zoom-val" id="ic-zoom-val">100%</span>
</div>
</div>
<div class="ic-toolbar-sep"></div>
<div class="ic-toolbar-group">
<button class="ic-tool-btn" id="ic-reset-btn">🔄 New Image</button>
</div>
</div>

<!-- File info -->
<div class="ic-info-bar" id="ic-info-bar">
<div class="ic-info-item">File: <span id="ic-fname">—</span></div>
<div class="ic-info-item">Size: <span id="ic-fsize">—</span></div>
<div class="ic-info-item">Original: <span id="ic-fdims">—</span></div>
</div>

<!-- Canvas -->
<div class="ic-canvas-wrap" id="ic-canvas-wrap">
<canvas id="ic-canvas"></canvas>
</div>

<!-- Selection info -->
<div class="ic-sel-info" id="ic-sel-info">
Drag on the image to select crop area &mdash; selection: <span id="ic-sel-dims">none</span>
</div>

<!-- Preview + Download -->
<div class="ic-bottom">
<div class="ic-preview-box">
<div class="ic-preview-title">Crop Preview</div>
<div class="ic-preview-canvas-wrap">
<canvas id="ic-preview-canvas"></canvas>
</div>
<div class="ic-preview-dims" id="ic-preview-dims">Select an area above to preview</div>
</div>

<div class="ic-dl-box">
<div class="ic-dl-title">Download</div>
<div>
<div style="font-size:12px;font-weight:600;color:#6b7280;margin-bottom:6px;">Format</div>
<div class="ic-fmt-row">
<button class="ic-fmt-btn active" data-fmt="image/png">PNG</button>
<button class="ic-fmt-btn" data-fmt="image/jpeg">JPEG</button>
</div>
</div>
<div class="ic-quality-row" id="ic-quality-row">
<div class="ic-quality-label">
<span>Quality (JPEG)</span>
<span id="ic-quality-val">90%</span>
</div>
<input type="range" class="ic-quality-slider" id="ic-quality-slider" min="10" max="100" value="90">
</div>
<button class="ic-dl-btn" id="ic-dl-btn" disabled>Download Cropped Image</button>
</div>
</div>

<div class="ic-hint">
💡 <strong>Tips:</strong> Drag anywhere on the canvas to draw a crop selection. Drag the selection edges or corners to resize it. Use aspect ratio buttons to lock proportions. Rotate or flip the image before cropping if needed.
</div>

</div>

<script>
(function() {
'use strict';

// --- State ---
var sourceImg = null;      // original HTMLImageElement
var rotationDeg = 0;       // 0, 90, 180, 270
var flipH = false;
var flipV = false;
var zoom = 1;
var aspectRatio = 'free';  // 'free' | number

// Selection (in canvas display coordinates)
var sel = { active: false, x: 0, y: 0, w: 0, h: 0 };
var drag = { down: false, startX: 0, startY: 0, mode: 'draw', handleIdx: -1 };
var HANDLE_SIZE = 8;

// Output format
var outFmt = 'image/png';
var outQuality = 0.9;

// --- DOM refs ---
var dropzone    = document.getElementById('ic-dropzone');
var fileInput   = document.getElementById('ic-file-input');
var mainEl      = document.getElementById('ic-main');
var canvas      = document.getElementById('ic-canvas');
var ctx         = canvas.getContext('2d');
var previewCanvas = document.getElementById('ic-preview-canvas');
var pCtx        = previewCanvas.getContext('2d');
var zoomSlider  = document.getElementById('ic-zoom-slider');
var zoomVal     = document.getElementById('ic-zoom-val');
var selDimsEl   = document.getElementById('ic-sel-dims');
var previewDims = document.getElementById('ic-preview-dims');
var dlBtn       = document.getElementById('ic-dl-btn');
var qualityRow  = document.getElementById('ic-quality-row');
var qualitySlider = document.getElementById('ic-quality-slider');
var qualityValEl  = document.getElementById('ic-quality-val');
var fnameEl     = document.getElementById('ic-fname');
var fsizeEl     = document.getElementById('ic-fsize');
var fdimsEl     = document.getElementById('ic-fdims');

// --- Helpers ---
function fmtBytes(b) {
if (b < 1024) return b + ' B';
if (b < 1048576) return (b / 1024).toFixed(1) + ' KB';
return (b / 1048576).toFixed(2) + ' MB';
}

// Get the transformed image dimensions (after rotation)
function getTransformedDims() {
if (!sourceImg) return { w: 0, h: 0 };
var sw = sourceImg.naturalWidth;
var sh = sourceImg.naturalHeight;
if (rotationDeg === 90 || rotationDeg === 270) return { w: sh, h: sw };
return { w: sw, h: sh };
}

// Draw the transformed image onto a temp offscreen canvas, return it
function buildTransformedCanvas() {
var dims = getTransformedDims();
var oc = document.createElement('canvas');
oc.width  = dims.w;
oc.height = dims.h;
var oc_ctx = oc.getContext('2d');
oc_ctx.save();
oc_ctx.translate(dims.w / 2, dims.h / 2);
oc_ctx.rotate(rotationDeg * Math.PI / 180);
var sx = flipH ? -1 : 1;
var sy = flipV ? -1 : 1;
oc_ctx.scale(sx, sy);
oc_ctx.drawImage(sourceImg, -sourceImg.naturalWidth / 2, -sourceImg.naturalHeight / 2);
oc_ctx.restore();
return oc;
}

// Render the main canvas
function render() {
if (!sourceImg) return;

var dims = getTransformedDims();
var dispW = Math.round(dims.w * zoom);
var dispH = Math.round(dims.h * zoom);
canvas.width  = dispW;
canvas.height = dispH;

var tc = buildTransformedCanvas();
ctx.drawImage(tc, 0, 0, dispW, dispH);

// Draw selection overlay
if (sel.active && sel.w !== 0 && sel.h !== 0) {
var sx = Math.min(sel.x, sel.x + sel.w);
var sy = Math.min(sel.y, sel.y + sel.h);
var sw = Math.abs(sel.w);
var sh = Math.abs(sel.h);

// Darken outside
ctx.save();
ctx.fillStyle = 'rgba(0,0,0,0.48)';
ctx.fillRect(0, 0, dispW, dispH);
ctx.clearRect(sx, sy, sw, sh);
// Re-draw image in clear area
ctx.drawImage(tc, sx, sy, sw, sh, sx, sy, sw, sh);
ctx.restore();

// Border
ctx.save();
ctx.strokeStyle = '#a78bfa';
ctx.lineWidth = 2;
ctx.setLineDash([6, 3]);
ctx.strokeRect(sx, sy, sw, sh);
ctx.setLineDash([]);
ctx.restore();

// Rule of thirds grid
ctx.save();
ctx.strokeStyle = 'rgba(167,139,250,0.4)';
ctx.lineWidth = 1;
for (var i = 1; i < 3; i++) {
ctx.beginPath();
ctx.moveTo(sx + sw * i / 3, sy);
ctx.lineTo(sx + sw * i / 3, sy + sh);
ctx.stroke();
ctx.beginPath();
ctx.moveTo(sx, sy + sh * i / 3);
ctx.lineTo(sx + sw, sy + sh * i / 3);
ctx.stroke();
}
ctx.restore();

// Handles
var handles = getHandles(sx, sy, sw, sh);
ctx.save();
ctx.fillStyle = '#fff';
ctx.strokeStyle = '#7c3aed';
ctx.lineWidth = 2;
handles.forEach(function(h) {
ctx.fillRect(h.x - HANDLE_SIZE/2, h.y - HANDLE_SIZE/2, HANDLE_SIZE, HANDLE_SIZE);
ctx.strokeRect(h.x - HANDLE_SIZE/2, h.y - HANDLE_SIZE/2, HANDLE_SIZE, HANDLE_SIZE);
});
ctx.restore();

// Update selection dims display
var realW = Math.round(sw / zoom);
var realH = Math.round(sh / zoom);
selDimsEl.innerHTML = '<span>' + realW + ' &times; ' + realH + ' px</span>';
dlBtn.disabled = false;
updatePreview(tc, sx, sy, sw, sh);
} else {
selDimsEl.innerHTML = 'none';
dlBtn.disabled = true;
previewDims.textContent = 'Select an area above to preview';
previewCanvas.width = 1;
previewCanvas.height = 1;
}
}

function getHandles(sx, sy, sw, sh) {
return [
{ x: sx,      y: sy },
{ x: sx+sw/2, y: sy },
{ x: sx+sw,   y: sy },
{ x: sx+sw,   y: sy+sh/2 },
{ x: sx+sw,   y: sy+sh },
{ x: sx+sw/2, y: sy+sh },
{ x: sx,      y: sy+sh },
{ x: sx,      y: sy+sh/2 }
];
}

function updatePreview(tc, sx, sy, sw, sh) {
var realW = Math.round(sw / zoom);
var realH = Math.round(sh / zoom);
var maxPreview = 220;
var scale = Math.min(maxPreview / realW, maxPreview / realH, 1);
var pw = Math.round(realW * scale);
var ph = Math.round(realH * scale);
previewCanvas.width  = pw;
previewCanvas.height = ph;
pCtx.drawImage(tc,
sx / zoom, sy / zoom, realW, realH,
0, 0, pw, ph
);
previewDims.textContent = realW + ' \u00d7 ' + realH + ' px';
}

// --- Drag / selection ---
function getCanvasXY(e) {
var rect = canvas.getBoundingClientRect();
var clientX = e.touches ? e.touches[0].clientX : e.clientX;
var clientY = e.touches ? e.touches[0].clientY : e.clientY;
var scaleX = canvas.width  / rect.width;
var scaleY = canvas.height / rect.height;
return {
x: (clientX - rect.left) * scaleX,
y: (clientY - rect.top)  * scaleY
};
}

function hitHandle(px, py) {
if (!sel.active) return -1;
var sx = Math.min(sel.x, sel.x + sel.w);
var sy = Math.min(sel.y, sel.y + sel.h);
var sw = Math.abs(sel.w);
var sh = Math.abs(sel.h);
var handles = getHandles(sx, sy, sw, sh);
var ht = HANDLE_SIZE + 4;
for (var i = 0; i < handles.length; i++) {
if (Math.abs(px - handles[i].x) <= ht/2 && Math.abs(py - handles[i].y) <= ht/2) {
return i;
}
}
return -1;
}

function hitSelection(px, py) {
if (!sel.active) return false;
var sx = Math.min(sel.x, sel.x + sel.w);
var sy = Math.min(sel.y, sel.y + sel.h);
var sw = Math.abs(sel.w);
var sh = Math.abs(sel.h);
return px >= sx && px <= sx + sw && py >= sy && py <= sy + sh;
}

function clampSel() {
var cw = canvas.width;
var ch = canvas.height;
sel.x = Math.max(0, Math.min(sel.x, cw));
sel.y = Math.max(0, Math.min(sel.y, ch));
sel.w = Math.max(-(sel.x), Math.min(sel.w, cw - sel.x));
sel.h = Math.max(-(sel.y), Math.min(sel.h, ch - sel.y));
}

function applyAspectRatio() {
if (aspectRatio === 'free') return;
var ar = parseFloat(aspectRatio);
if (!ar) return;
var absW = Math.abs(sel.w);
var absH = Math.abs(sel.h);
// Keep the larger dimension
if (absW / ar > absH) {
sel.h = (sel.w >= 0 ? 1 : -1) * Math.abs(sel.w) / ar;
} else {
sel.w = (sel.h >= 0 ? 1 : -1) * Math.abs(sel.h) * ar;
}
}

canvas.addEventListener('mousedown', onDown);
canvas.addEventListener('touchstart', onDown, { passive: false });

function onDown(e) {
e.preventDefault();
var pos = getCanvasXY(e);
var hIdx = hitHandle(pos.x, pos.y);
if (hIdx !== -1) {
drag.down = true;
drag.mode = 'handle';
drag.handleIdx = hIdx;
drag.startX = pos.x;
drag.startY = pos.y;
} else if (hitSelection(pos.x, pos.y)) {
drag.down = true;
drag.mode = 'move';
drag.startX = pos.x - Math.min(sel.x, sel.x + sel.w);
drag.startY = pos.y - Math.min(sel.y, sel.y + sel.h);
} else {
drag.down = true;
drag.mode = 'draw';
drag.startX = pos.x;
drag.startY = pos.y;
sel.active = true;
sel.x = pos.x;
sel.y = pos.y;
sel.w = 0;
sel.h = 0;
}
}

document.addEventListener('mousemove', onMove);
document.addEventListener('touchmove', onMove, { passive: false });

function onMove(e) {
if (!drag.down) return;
e.preventDefault();
var pos = getCanvasXY(e);

if (drag.mode === 'draw') {
sel.w = pos.x - drag.startX;
sel.h = pos.y - drag.startY;
applyAspectRatio();
} else if (drag.mode === 'move') {
var normX = Math.min(sel.x, sel.x + sel.w);
var normY = Math.min(sel.y, sel.y + sel.h);
var sw = Math.abs(sel.w);
var sh = Math.abs(sel.h);
sel.x = pos.x - drag.startX;
sel.y = pos.y - drag.startY;
sel.w = sw;
sel.h = sh;
// Clamp move
sel.x = Math.max(0, Math.min(sel.x, canvas.width  - sw));
sel.y = Math.max(0, Math.min(sel.y, canvas.height - sh));
} else if (drag.mode === 'handle') {
var sx = Math.min(sel.x, sel.x + sel.w);
var sy = Math.min(sel.y, sel.y + sel.h);
var sw2 = Math.abs(sel.w);
var sh2 = Math.abs(sel.h);
var ex = sx + sw2;
var ey = sy + sh2;
switch (drag.handleIdx) {
case 0: sx = pos.x; sy = pos.y; break;
case 1: sy = pos.y; break;
case 2: ex = pos.x; sy = pos.y; break;
case 3: ex = pos.x; break;
case 4: ex = pos.x; ey = pos.y; break;
case 5: ey = pos.y; break;
case 6: sx = pos.x; ey = pos.y; break;
case 7: sx = pos.x; break;
}
sel.x = sx;
sel.y = sy;
sel.w = ex - sx;
sel.h = ey - sy;
applyAspectRatio();
}

clampSel();
render();
}

document.addEventListener('mouseup', onUp);
document.addEventListener('touchend', onUp);

function onUp() {
drag.down = false;
if (sel.active && Math.abs(sel.w) < 4 && Math.abs(sel.h) < 4) {
sel.active = false;
}
render();
}

// --- File loading ---
function loadFile(file) {
if (!file || !file.type.startsWith('image/')) return;
if (file.size > 20 * 1024 * 1024) {
alert('File is too large. Maximum 20 MB.');
return;
}
var reader = new FileReader();
reader.onload = function(ev) {
var img = new Image();
img.onload = function() {
sourceImg = img;
rotationDeg = 0;
flipH = false;
flipV = false;
zoom = 1;
zoomSlider.value = 100;
zoomVal.textContent = '100%';
sel = { active: false, x: 0, y: 0, w: 0, h: 0 };
dlBtn.disabled = true;

fnameEl.textContent = file.name;
fsizeEl.textContent = fmtBytes(file.size);
fdimsEl.textContent = img.naturalWidth + ' \u00d7 ' + img.naturalHeight + ' px';

mainEl.classList.add('visible');
dropzone.style.display = 'none';
render();
};
img.src = ev.target.result;
};
reader.readAsDataURL(file);
}

// Drop zone
dropzone.addEventListener('dragover', function(e) {
e.preventDefault();
dropzone.classList.add('drag-over');
});
dropzone.addEventListener('dragleave', function() {
dropzone.classList.remove('drag-over');
});
dropzone.addEventListener('drop', function(e) {
e.preventDefault();
dropzone.classList.remove('drag-over');
loadFile(e.dataTransfer.files[0]);
});
fileInput.addEventListener('change', function() {
loadFile(fileInput.files[0]);
});

// Reset
document.getElementById('ic-reset-btn').addEventListener('click', function() {
sourceImg = null;
mainEl.classList.remove('visible');
dropzone.style.display = '';
fileInput.value = '';
});

// Rotate
document.getElementById('ic-rotate-btn').addEventListener('click', function() {
rotationDeg = (rotationDeg + 90) % 360;
sel = { active: false, x: 0, y: 0, w: 0, h: 0 };
autoZoom();
render();
});

// Flip H
document.getElementById('ic-flip-h-btn').addEventListener('click', function() {
flipH = !flipH;
render();
});

// Flip V
document.getElementById('ic-flip-v-btn').addEventListener('click', function() {
flipV = !flipV;
render();
});

// Auto-zoom to fit container
function autoZoom() {
var dims = getTransformedDims();
var wrap = document.getElementById('ic-canvas-wrap');
var maxW = wrap.clientWidth || 860;
var maxH = 560;
var z = Math.min(maxW / dims.w, maxH / dims.h, 1);
zoom = Math.round(z * 100) / 100;
zoomSlider.value = Math.round(zoom * 100);
zoomVal.textContent = Math.round(zoom * 100) + '%';
}

// Zoom slider
zoomSlider.addEventListener('input', function() {
zoom = parseInt(zoomSlider.value) / 100;
zoomVal.textContent = zoomSlider.value + '%';
sel = { active: false, x: 0, y: 0, w: 0, h: 0 };
render();
});

// Aspect ratio buttons
document.querySelectorAll('#ic-app .ic-ratio-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#ic-app .ic-ratio-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
aspectRatio = btn.getAttribute('data-ratio');
});
});

// Format buttons
document.querySelectorAll('#ic-app .ic-fmt-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#ic-app .ic-fmt-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
outFmt = btn.getAttribute('data-fmt');
qualityRow.style.opacity = outFmt === 'image/png' ? '0.4' : '1';
qualityRow.style.pointerEvents = outFmt === 'image/png' ? 'none' : '';
});
});

// Quality slider
qualitySlider.addEventListener('input', function() {
outQuality = parseInt(qualitySlider.value) / 100;
qualityValEl.textContent = qualitySlider.value + '%';
});
// PNG: disable quality row initially
qualityRow.style.opacity = '0.4';
qualityRow.style.pointerEvents = 'none';
// Switch to PNG by default — show quality only for JPEG
document.querySelectorAll('#ic-app .ic-fmt-btn').forEach(function(btn) {
if (btn.getAttribute('data-fmt') === 'image/png') btn.classList.add('active');
else btn.classList.remove('active');
});

// Download
dlBtn.addEventListener('click', function() {
if (!sourceImg || !sel.active) return;
var sx = Math.min(sel.x, sel.x + sel.w) / zoom;
var sy = Math.min(sel.y, sel.y + sel.h) / zoom;
var sw = Math.abs(sel.w) / zoom;
var sh = Math.abs(sel.h) / zoom;
if (sw < 1 || sh < 1) return;

var tc = buildTransformedCanvas();
var outCanvas = document.createElement('canvas');
outCanvas.width  = Math.round(sw);
outCanvas.height = Math.round(sh);
var outCtx = outCanvas.getContext('2d');
outCtx.drawImage(tc, sx, sy, sw, sh, 0, 0, outCanvas.width, outCanvas.height);

var ext = outFmt === 'image/jpeg' ? 'jpg' : 'png';
var dataUrl = outCanvas.toDataURL(outFmt, outQuality);
var a = document.createElement('a');
a.href = dataUrl;
a.download = 'cropped-' + outCanvas.width + 'x' + outCanvas.height + '.' + ext;
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
});

})();
</script>

</div>

## How to Use the Image Cropper

**Step 1 — Upload**: Drop your image onto the upload area or click to browse. JPG, PNG, WebP, GIF, and BMP files up to 20 MB are supported.

**Step 2 — Draw a selection**: Click and drag on the canvas to draw a crop rectangle. The selection is shown with a dashed purple border and a rule-of-thirds grid overlay.

**Step 3 — Resize the selection**: Drag any of the eight white handles (corners and midpoints) to resize the crop area. Drag inside the selection to move it.

**Step 4 — Lock an aspect ratio (optional)**: Click a ratio button (1:1, 4:3, 16:9, 3:2) to snap the selection to a fixed proportion as you drag.

**Step 5 — Rotate or flip (optional)**: Click "Rotate 90°" to rotate the image before cropping. Use "Flip H" or "Flip V" to mirror it.

**Step 6 — Preview and download**: The right-side preview shows the cropped area in real time. Choose PNG or JPEG format, set JPEG quality if needed, then click "Download Cropped Image".

## Aspect Ratio Guide

| Ratio | Best for |
|---|---|
| Free | Any custom crop, no constraints |
| 1:1 | Instagram square posts, profile pictures |
| 4:3 | Standard photos, presentations |
| 16:9 | YouTube thumbnails, widescreen video |
| 3:2 | Classic camera photos, prints |

## Why Crop in the Browser?

This tool runs entirely client-side using the HTML5 Canvas API. Your image never leaves your device — there is no server upload, no account required, and no file size limit beyond your browser memory. It works on any modern desktop or mobile browser without installing anything.

---

## Related Tools

> Resize an image to exact pixel dimensions &rarr; [Image Resizer](/tools/image-resizer/)

> Apply filters and effects to photos &rarr; [Photo Filter](/tools/photo-filter/)

> Resize images to social media sizes &rarr; [Social Media Image Resizer](/tools/social-media-image-resizer/)
