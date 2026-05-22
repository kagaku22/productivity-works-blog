---
title: "Pixel Ruler / Screen Measurement Tool — Free Online"
date: 2025-05-16
description: "On-screen pixel ruler with drag measurement in px, cm, and inches. Crosshair coordinate tracker, DPI detection, configurable length and color. No install needed."
categories: ["Free Tools"]
tags: ["Image Tools", "Design", "Free Tools"]
slug: "pixel-ruler"
ShowToc: false
aliases:
  - "/tools/pixel-ruler/"
  - "/tools/pixel-ruler/"
cover:
  image: "/images/covers/pixel-ruler.png"
  alt: "Pixel Ruler Screen Measurement Tool"
---

Measure distances and positions directly on your screen. Drag the ruler to set a measurement, track your cursor's exact pixel coordinates, detect your screen's DPI, and customize the ruler's color and length — all without installing anything.

<div id="pr-app">

<style>
/* ── Reset ──────────────────────────────────────────────────── */
#pr-app *, #pr-app *::before, #pr-app *::after {
box-sizing: border-box; margin: 0; padding: 0;
}
#pr-app {
font-family: system-ui, -apple-system, sans-serif;
font-size: 14px;
color: #1a1a2e;
line-height: 1.5;
user-select: none;
}

/* ── Controls bar ───────────────────────────────────────────── */
#pr-app .pr-controls {
display: flex;
flex-wrap: wrap;
gap: 12px;
align-items: center;
background: #f8f9fc;
border: 1px solid #e2e6f0;
border-radius: 12px;
padding: 14px 16px;
margin-bottom: 16px;
}
#pr-app .pr-ctrl-group {
display: flex;
align-items: center;
gap: 8px;
font-size: 13px;
color: #374151;
}
#pr-app .pr-ctrl-group label {
font-weight: 600;
white-space: nowrap;
}
#pr-app .pr-ctrl-group input[type="range"] {
width: 100px;
accent-color: #6366f1;
}
#pr-app .pr-ctrl-group input[type="color"] {
width: 34px;
height: 30px;
border: 1.5px solid #d1d5db;
border-radius: 6px;
cursor: pointer;
padding: 2px;
background: #fff;
}
#pr-app .pr-ctrl-group select {
border: 1px solid #d1d5db;
border-radius: 6px;
padding: 5px 8px;
font-size: 13px;
background: #fff;
cursor: pointer;
outline: none;
}
#pr-app .pr-ctrl-group select:focus { border-color: #6366f1; }
#pr-app .pr-sep {
width: 1px;
height: 28px;
background: #e2e6f0;
}

/* ── DPI info ───────────────────────────────────────────────── */
#pr-app .pr-dpi-badge {
font-size: 12px;
background: #eef2ff;
color: #4338ca;
padding: 3px 10px;
border-radius: 20px;
font-weight: 600;
border: 1px solid #c7d2fe;
}

/* ── Canvas area ────────────────────────────────────────────── */
#pr-app .pr-canvas-wrap {
position: relative;
background: #fff;
border: 1px solid #e2e6f0;
border-radius: 12px;
overflow: hidden;
height: 380px;
cursor: crosshair;
}

/* ── Coordinate display ─────────────────────────────────────── */
#pr-app .pr-coords {
position: absolute;
top: 10px;
right: 14px;
background: rgba(15,23,42,.82);
color: #f8fafc;
font-size: 12px;
font-family: monospace;
padding: 6px 12px;
border-radius: 6px;
pointer-events: none;
z-index: 10;
white-space: nowrap;
}

/* ── Measurement label ──────────────────────────────────────── */
#pr-app .pr-measure-label {
position: absolute;
background: rgba(15,23,42,.82);
color: #f8fafc;
font-size: 12px;
font-family: monospace;
padding: 4px 10px;
border-radius: 6px;
pointer-events: none;
z-index: 10;
white-space: nowrap;
}

/* ── Canvas ─────────────────────────────────────────────────── */
#pr-app canvas {
display: block;
width: 100%;
height: 100%;
}

/* ── Info row ───────────────────────────────────────────────── */
#pr-app .pr-info-row {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin-top: 14px;
}
#pr-app .pr-info-card {
flex: 1;
min-width: 140px;
background: #f8f9fc;
border: 1px solid #e2e6f0;
border-radius: 10px;
padding: 14px 16px;
}
#pr-app .pr-info-card .pr-ic-label {
font-size: 11px;
color: #6b7280;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .07em;
margin-bottom: 4px;
}
#pr-app .pr-info-card .pr-ic-val {
font-size: 20px;
font-weight: 800;
color: #1a1a2e;
font-family: monospace;
}
#pr-app .pr-info-card .pr-ic-sub {
font-size: 11px;
color: #6b7280;
margin-top: 2px;
}

/* ── Instructions ───────────────────────────────────────────── */
#pr-app .pr-hint {
font-size: 12px;
color: #6b7280;
margin-top: 10px;
padding: 10px 14px;
background: #f8f9fc;
border-radius: 8px;
border-left: 3px solid #6366f1;
}

/* ── Buttons ────────────────────────────────────────────────── */
#pr-app .pr-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 7px 14px;
border-radius: 7px;
border: 1.5px solid #d1d5db;
background: #fff;
font-size: 12px;
font-weight: 600;
cursor: pointer;
color: #374151;
transition: background .15s;
}
#pr-app .pr-btn:hover { background: #f3f4f6; }
#pr-app .pr-btn-primary {
background: #6366f1;
color: #fff;
border-color: #6366f1;
}
#pr-app .pr-btn-primary:hover { background: #4f46e5; }
</style>

<!-- Controls -->
<div class="pr-controls">
<div class="pr-ctrl-group">
<label>Orientation:</label>
<select id="pr-orient">
<option value="h">Horizontal</option>
<option value="v">Vertical</option>
<option value="both">Both</option>
</select>
</div>
<div class="pr-sep"></div>
<div class="pr-ctrl-group">
<label>Length:</label>
<input type="range" id="pr-length" min="100" max="900" value="500">
<span id="pr-length-lbl">500 px</span>
</div>
<div class="pr-sep"></div>
<div class="pr-ctrl-group">
<label>Color:</label>
<input type="color" id="pr-color" value="#6366f1">
</div>
<div class="pr-sep"></div>
<div class="pr-ctrl-group">
<label>Units:</label>
<select id="pr-unit">
<option value="px">px</option>
<option value="cm">cm</option>
<option value="in">in</option>
</select>
</div>
<div class="pr-sep"></div>
<span class="pr-dpi-badge" id="pr-dpi-badge">DPI: detecting…</span>
<button class="pr-btn pr-btn-primary" id="pr-reset-btn">Reset</button>
</div>

<!-- Canvas area -->
<div class="pr-canvas-wrap" id="pr-canvas-wrap">
<canvas id="pr-canvas"></canvas>
<div class="pr-coords" id="pr-coords">x: 0 &nbsp; y: 0</div>
<div class="pr-measure-label" id="pr-meas-label" style="display:none;"></div>
</div>

<!-- Info cards -->
<div class="pr-info-row">
<div class="pr-info-card">
<div class="pr-ic-label">Measurement</div>
<div class="pr-ic-val" id="pr-val-px">—</div>
<div class="pr-ic-sub">pixels</div>
</div>
<div class="pr-info-card">
<div class="pr-ic-label">Centimeters</div>
<div class="pr-ic-val" id="pr-val-cm">—</div>
<div class="pr-ic-sub">cm</div>
</div>
<div class="pr-info-card">
<div class="pr-ic-label">Inches</div>
<div class="pr-ic-val" id="pr-val-in">—</div>
<div class="pr-ic-sub">in</div>
</div>
<div class="pr-info-card">
<div class="pr-ic-label">Screen DPI</div>
<div class="pr-ic-val" id="pr-val-dpi">—</div>
<div class="pr-ic-sub">dots per inch</div>
</div>
</div>

<p class="pr-hint">
<strong>How to use:</strong> Hover to track cursor position. Click and drag inside the ruler area to measure a distance. The ruler snaps to the selected orientation. Adjust length, color, and unit above.
</p>

<script>
(function () {
'use strict';

/* ── DPI detection ───────────────────────────────────────── */
function detectDPI() {
var dpi = 96;
// Use matchMedia to probe DPI
var queries = [72,96,120,144,160,192,216,240,288,320];
for (var i = queries.length - 1; i >= 0; i--) {
if (window.matchMedia('(min-resolution: ' + queries[i] + 'dpi)').matches) {
dpi = queries[i];
break;
}
}
// Also check devicePixelRatio as a hint
if (window.devicePixelRatio) {
var ratioDpi = Math.round(96 * window.devicePixelRatio);
// Use the higher of the two as a better estimate
dpi = Math.max(dpi, ratioDpi);
}
return dpi;
}

var DPI = detectDPI();
document.getElementById('pr-dpi-badge').textContent = 'DPI: ' + DPI;
document.getElementById('pr-val-dpi').textContent = DPI;

/* ── State ───────────────────────────────────────────────── */
var rulerColor   = '#6366f1';
var rulerLength  = 500;
var orientation  = 'h';  // h, v, both
var unit         = 'px';
var mouseX       = 0;
var mouseY       = 0;
var dragStart    = null;  // {x, y}
var dragEnd      = null;  // {x, y}
var isDragging   = false;
// Ruler position (draggable)
var rulerX       = 40;
var rulerY       = 40;
var draggingRuler = false;
var rulerDragOff  = {x:0, y:0};

/* ── DOM ─────────────────────────────────────────────────── */
var wrap       = document.getElementById('pr-canvas-wrap');
var canvas     = document.getElementById('pr-canvas');
var ctx        = canvas.getContext('2d');
var elCoords   = document.getElementById('pr-coords');
var elMeasLbl  = document.getElementById('pr-meas-label');
var elValPx    = document.getElementById('pr-val-px');
var elValCm    = document.getElementById('pr-val-cm');
var elValIn    = document.getElementById('pr-val-in');
var elOrient   = document.getElementById('pr-orient');
var elLength   = document.getElementById('pr-length');
var elLenLbl   = document.getElementById('pr-length-lbl');
var elColor    = document.getElementById('pr-color');
var elUnit     = document.getElementById('pr-unit');
var elResetBtn = document.getElementById('pr-reset-btn');

/* ── Resize canvas ───────────────────────────────────────── */
function resizeCanvas() {
canvas.width  = wrap.clientWidth;
canvas.height = wrap.clientHeight;
draw();
}

/* ── Convert px to display unit ──────────────────────────── */
function pxTo(px, u) {
if (u === 'cm') return (px / DPI * 2.54).toFixed(2);
if (u === 'in') return (px / DPI).toFixed(3);
return Math.round(px);
}

/* ── Draw ruler ──────────────────────────────────────────── */
function drawRuler(x, y, len, isHoriz) {
ctx.save();
ctx.strokeStyle = rulerColor;
ctx.fillStyle   = rulerColor;
ctx.lineWidth   = 2;
ctx.font        = '10px monospace';
ctx.textAlign   = 'center';

// Main line
ctx.beginPath();
if (isHoriz) {
ctx.moveTo(x, y);
ctx.lineTo(x + len, y);
} else {
ctx.moveTo(x, y);
ctx.lineTo(x, y + len);
}
ctx.stroke();

// Tick marks every 10px, larger every 50px, labels every 100px
for (var i = 0; i <= len; i++) {
var tickLen;
if (i % 100 === 0) tickLen = 16;
else if (i % 50 === 0) tickLen = 10;
else if (i % 10 === 0) tickLen = 6;
else continue;

ctx.beginPath();
if (isHoriz) {
ctx.moveTo(x + i, y - tickLen);
ctx.lineTo(x + i, y + tickLen);
} else {
ctx.moveTo(x - tickLen, y + i);
ctx.lineTo(x + tickLen, y + i);
}
ctx.stroke();

// Labels at 100px intervals
if (i % 100 === 0 && i > 0) {
var labelTxt = pxTo(i, unit).toString();
ctx.save();
if (isHoriz) {
ctx.fillText(labelTxt, x + i, y - 20);
} else {
ctx.save();
ctx.translate(x - 22, y + i);
ctx.rotate(-Math.PI / 2);
ctx.fillText(labelTxt, 0, 0);
ctx.restore();
}
ctx.restore();
}
}

// End caps
ctx.beginPath();
if (isHoriz) {
ctx.moveTo(x, y - 16); ctx.lineTo(x, y + 16);
ctx.moveTo(x + len, y - 16); ctx.lineTo(x + len, y + 16);
} else {
ctx.moveTo(x - 16, y); ctx.lineTo(x + 16, y);
ctx.moveTo(x - 16, y + len); ctx.lineTo(x + 16, y + len);
}
ctx.stroke();

ctx.restore();
}

/* ── Draw crosshair ──────────────────────────────────────── */
function drawCrosshair(x, y) {
ctx.save();
ctx.strokeStyle = 'rgba(99,102,241,0.5)';
ctx.lineWidth = 1;
ctx.setLineDash([4, 4]);
ctx.beginPath();
ctx.moveTo(x, 0); ctx.lineTo(x, canvas.height);
ctx.moveTo(0, y); ctx.lineTo(canvas.width, y);
ctx.stroke();
ctx.restore();
}

/* ── Draw measurement line ───────────────────────────────── */
function drawMeasurement() {
if (!dragStart || !dragEnd) return;
var x1 = dragStart.x, y1 = dragStart.y;
var x2 = dragEnd.x,   y2 = dragEnd.y;

ctx.save();
ctx.strokeStyle = '#ef4444';
ctx.lineWidth = 2;
ctx.setLineDash([]);

// Line
ctx.beginPath();
ctx.moveTo(x1, y1);
ctx.lineTo(x2, y2);
ctx.stroke();

// End dots
[dragStart, dragEnd].forEach(function (pt) {
ctx.beginPath();
ctx.arc(pt.x, pt.y, 5, 0, Math.PI * 2);
ctx.fillStyle = '#ef4444';
ctx.fill();
});

// Distance
var dx = x2 - x1, dy = y2 - y1;
var dist = Math.sqrt(dx*dx + dy*dy);
var midX = (x1 + x2) / 2;
var midY = (y1 + y2) / 2;

// Update cards
var distPx = Math.round(dist);
elValPx.textContent = distPx + ' px';
elValCm.textContent = (distPx / DPI * 2.54).toFixed(2) + ' cm';
elValIn.textContent = (distPx / DPI).toFixed(3) + ' in';

// Floating label
var labelTxt = pxTo(dist, unit) + (unit === 'px' ? ' px' : unit === 'cm' ? ' cm' : ' in');
elMeasLbl.style.display = 'block';
elMeasLbl.textContent = labelTxt;
elMeasLbl.style.left = (midX + 8) + 'px';
elMeasLbl.style.top  = (midY - 14) + 'px';

ctx.restore();
}

/* ── Main draw ───────────────────────────────────────────── */
function draw() {
ctx.clearRect(0, 0, canvas.width, canvas.height);

// Background grid (subtle)
ctx.save();
ctx.strokeStyle = 'rgba(226,230,240,0.6)';
ctx.lineWidth = 1;
for (var gx = 0; gx < canvas.width; gx += 50) {
ctx.beginPath(); ctx.moveTo(gx, 0); ctx.lineTo(gx, canvas.height); ctx.stroke();
}
for (var gy = 0; gy < canvas.height; gy += 50) {
ctx.beginPath(); ctx.moveTo(0, gy); ctx.lineTo(canvas.width, gy); ctx.stroke();
}
ctx.restore();

// Ruler(s)
if (orientation === 'h' || orientation === 'both') {
drawRuler(rulerX, rulerY, rulerLength, true);
}
if (orientation === 'v' || orientation === 'both') {
var vy = orientation === 'both' ? rulerY : rulerY;
var vx = orientation === 'both' ? rulerX + rulerLength + 30 : rulerX;
if (orientation === 'v') vx = rulerX;
drawRuler(vx, vy, rulerLength, false);
}

// Crosshair
drawCrosshair(mouseX, mouseY);

// Measurement
drawMeasurement();
}

/* ── Pointer position in canvas ──────────────────────────── */
function canvasPos(e) {
var r = canvas.getBoundingClientRect();
var cx = e.clientX - r.left;
var cy = e.clientY - r.top;
return {
x: cx * (canvas.width / r.width),
y: cy * (canvas.height / r.height)
};
}

/* ── Mouse events ────────────────────────────────────────── */
wrap.addEventListener('mousemove', function (e) {
var pos = canvasPos(e);
mouseX = pos.x;
mouseY = pos.y;

elCoords.textContent = 'x: ' + Math.round(mouseX) + '   y: ' + Math.round(mouseY);

if (isDragging) {
dragEnd = pos;
}

if (draggingRuler) {
rulerX = pos.x - rulerDragOff.x;
rulerY = pos.y - rulerDragOff.y;
}

draw();
});

wrap.addEventListener('mousedown', function (e) {
var pos = canvasPos(e);

// Check if clicking near ruler line (for drag)
var onRuler = false;
if (orientation === 'h' || orientation === 'both') {
if (Math.abs(pos.y - rulerY) < 20 && pos.x >= rulerX - 10 && pos.x <= rulerX + rulerLength + 10) {
onRuler = true;
}
}
if (orientation === 'v' || orientation === 'both') {
var vx2 = orientation === 'both' ? rulerX + rulerLength + 30 : rulerX;
if (Math.abs(pos.x - vx2) < 20 && pos.y >= rulerY - 10 && pos.y <= rulerY + rulerLength + 10) {
onRuler = true;
vx2 = vx2;
}
}

if (onRuler && e.altKey) {
draggingRuler = true;
rulerDragOff = { x: pos.x - rulerX, y: pos.y - rulerY };
} else {
isDragging = true;
dragStart = pos;
dragEnd   = pos;
elMeasLbl.style.display = 'none';
}
e.preventDefault();
});

wrap.addEventListener('mouseup', function () {
isDragging   = false;
draggingRuler = false;
});

wrap.addEventListener('mouseleave', function () {
isDragging   = false;
draggingRuler = false;
});

/* ── Touch support ───────────────────────────────────────── */
function touchPos(e) {
return canvasPos(e.touches[0] || e.changedTouches[0]);
}

wrap.addEventListener('touchstart', function (e) {
var pos = touchPos(e);
isDragging = true;
dragStart = pos;
dragEnd   = pos;
e.preventDefault();
}, {passive: false});

wrap.addEventListener('touchmove', function (e) {
var pos = touchPos(e);
mouseX = pos.x; mouseY = pos.y;
if (isDragging) dragEnd = pos;
elCoords.textContent = 'x: ' + Math.round(mouseX) + '   y: ' + Math.round(mouseY);
draw();
e.preventDefault();
}, {passive: false});

wrap.addEventListener('touchend', function () { isDragging = false; });

/* ── Controls ────────────────────────────────────────────── */
elOrient.addEventListener('change', function () {
orientation = elOrient.value;
draw();
});

elLength.addEventListener('input', function () {
rulerLength = parseInt(elLength.value, 10);
elLenLbl.textContent = rulerLength + ' px';
draw();
});

elColor.addEventListener('input', function () {
rulerColor = elColor.value;
draw();
});

elUnit.addEventListener('change', function () {
unit = elUnit.value;
draw();
});

elResetBtn.addEventListener('click', function () {
rulerX = 40; rulerY = 40;
rulerLength = 500;
rulerColor = '#6366f1';
orientation = 'h';
unit = 'px';
dragStart = null; dragEnd = null;
elOrient.value = 'h';
elLength.value = 500;
elLenLbl.textContent = '500 px';
elColor.value = '#6366f1';
elUnit.value = 'px';
elMeasLbl.style.display = 'none';
elValPx.textContent = '—';
elValCm.textContent = '—';
elValIn.textContent = '—';
draw();
});

/* ── Init ────────────────────────────────────────────────── */
resizeCanvas();
window.addEventListener('resize', resizeCanvas);
draw();
})();
</script>

</div>

---

> Check screen resolution → [Screen Resolution](/tools/screen-resolution/)
