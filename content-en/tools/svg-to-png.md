---
title: "SVG to PNG Converter"
date: 2025-05-16
description: "Convert SVG to PNG online for free. Upload or paste SVG code, set scale and background, then download high-resolution PNG. No upload to server — 100% client-side."
categories: ["Free Tools"]
slug: "svg-to-png"
ShowToc: false
cover:
  image: "/images/covers/svg-to-png.png"
  alt: "SVG to PNG Converter"
---

<div id="sp-app">

<style>
#sp-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 48px 0;
color: #1a202c;
}

#sp-app * {
box-sizing: border-box;
}

/* Hero */
.sp-hero {
background: linear-gradient(135deg, #7c3aed 0%, #6d28d9 50%, #4c1d95 100%);
border-radius: 16px;
padding: 32px 28px;
margin-bottom: 24px;
color: #fff;
}

.sp-hero h2 {
margin: 0 0 6px 0;
font-size: 24px;
font-weight: 800;
}

.sp-hero p {
margin: 0;
font-size: 14px;
opacity: 0.88;
line-height: 1.6;
}

/* Layout */
.sp-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
margin-bottom: 20px;
}

@media (max-width: 640px) {
.sp-layout {
grid-template-columns: 1fr;
}
}

/* Panels */
.sp-panel {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
}

.sp-panel-title {
font-size: 13px;
font-weight: 700;
color: #6d28d9;
text-transform: uppercase;
letter-spacing: 0.06em;
margin: 0 0 14px 0;
}

/* Drop Zone */
.sp-dropzone {
border: 3px dashed #7c3aed;
border-radius: 12px;
padding: 36px 20px;
text-align: center;
background: #faf5ff;
cursor: pointer;
transition: background 0.2s, border-color 0.2s;
margin-bottom: 14px;
}

.sp-dropzone:hover,
.sp-dropzone.sp-drag-over {
background: #ede9fe;
border-color: #6d28d9;
}

.sp-dropzone-icon {
font-size: 36px;
margin-bottom: 10px;
}

.sp-dropzone-text {
font-size: 15px;
font-weight: 600;
color: #4c1d95;
margin: 0 0 4px 0;
}

.sp-dropzone-sub {
font-size: 12px;
color: #7c3aed;
margin: 0;
}

/* Textarea */
.sp-textarea {
width: 100%;
min-height: 140px;
border: 1.5px solid #d8b4fe;
border-radius: 8px;
padding: 10px 12px;
font-family: 'Menlo', 'Monaco', 'Courier New', monospace;
font-size: 12px;
color: #1a202c;
background: #fdfbff;
resize: vertical;
outline: none;
transition: border-color 0.2s;
}

.sp-textarea:focus {
border-color: #7c3aed;
}

/* Controls */
.sp-controls {
display: flex;
flex-direction: column;
gap: 14px;
}

.sp-field {
display: flex;
flex-direction: column;
gap: 5px;
}

.sp-label {
font-size: 12px;
font-weight: 600;
color: #374151;
}

.sp-select,
.sp-input {
border: 1.5px solid #d1d5db;
border-radius: 7px;
padding: 8px 10px;
font-size: 13px;
color: #1a202c;
background: #fff;
outline: none;
transition: border-color 0.2s;
width: 100%;
}

.sp-select:focus,
.sp-input:focus {
border-color: #7c3aed;
}

.sp-dim-row {
display: flex;
gap: 8px;
align-items: center;
}

.sp-dim-row .sp-input {
flex: 1;
}

.sp-lock-btn {
background: #ede9fe;
border: 1.5px solid #c4b5fd;
border-radius: 7px;
width: 34px;
height: 34px;
cursor: pointer;
font-size: 16px;
display: flex;
align-items: center;
justify-content: center;
flex-shrink: 0;
transition: background 0.15s;
}

.sp-lock-btn:hover {
background: #ddd6fe;
}

.sp-lock-btn.locked {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

.sp-color-row {
display: flex;
gap: 8px;
align-items: center;
}

.sp-color-input {
width: 40px;
height: 34px;
padding: 2px 3px;
border: 1.5px solid #d1d5db;
border-radius: 7px;
cursor: pointer;
flex-shrink: 0;
}

.sp-transparent-btn {
padding: 6px 12px;
font-size: 12px;
font-weight: 600;
border: 1.5px solid #d1d5db;
border-radius: 7px;
background: #fff;
cursor: pointer;
color: #374151;
transition: all 0.15s;
}

.sp-transparent-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

/* Scale pills */
.sp-scale-row {
display: flex;
gap: 6px;
}

.sp-scale-btn {
flex: 1;
padding: 7px 0;
border: 1.5px solid #d1d5db;
border-radius: 7px;
background: #fff;
font-size: 12px;
font-weight: 700;
color: #374151;
cursor: pointer;
transition: all 0.15s;
text-align: center;
}

.sp-scale-btn:hover {
border-color: #7c3aed;
color: #7c3aed;
}

.sp-scale-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

/* Preview */
.sp-preview-wrap {
background: repeating-conic-gradient(#e5e7eb 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
min-height: 200px;
display: flex;
align-items: center;
justify-content: center;
overflow: hidden;
margin-bottom: 16px;
position: relative;
}

.sp-preview-wrap img {
max-width: 100%;
max-height: 300px;
display: block;
}

.sp-preview-placeholder {
text-align: center;
color: #9ca3af;
padding: 40px 20px;
}

.sp-preview-placeholder svg {
opacity: 0.3;
margin-bottom: 10px;
}

.sp-preview-placeholder p {
margin: 0;
font-size: 13px;
}

/* Info bar */
.sp-info-bar {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 16px;
}

.sp-info-chip {
background: #f3f4f6;
border-radius: 6px;
padding: 4px 10px;
font-size: 12px;
color: #374151;
font-weight: 500;
}

.sp-info-chip span {
color: #7c3aed;
font-weight: 700;
}

/* Buttons */
.sp-btn-primary {
display: block;
width: 100%;
padding: 13px;
background: linear-gradient(135deg, #7c3aed 0%, #6d28d9 100%);
color: #fff;
font-size: 15px;
font-weight: 700;
border: none;
border-radius: 10px;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
text-align: center;
}

.sp-btn-primary:hover {
opacity: 0.9;
}

.sp-btn-primary:active {
transform: scale(0.98);
}

.sp-btn-primary:disabled {
background: #9ca3af;
cursor: not-allowed;
transform: none;
}

.sp-btn-secondary {
display: block;
width: 100%;
padding: 10px;
background: #fff;
color: #7c3aed;
font-size: 13px;
font-weight: 600;
border: 1.5px solid #7c3aed;
border-radius: 10px;
cursor: pointer;
transition: background 0.15s;
text-align: center;
margin-top: 8px;
}

.sp-btn-secondary:hover {
background: #faf5ff;
}

/* Error */
.sp-error {
background: #fef2f2;
border: 1.5px solid #fca5a5;
border-radius: 8px;
padding: 10px 14px;
font-size: 13px;
color: #dc2626;
margin-bottom: 14px;
display: none;
}

/* File name */
.sp-filename {
font-size: 12px;
color: #6b7280;
text-align: center;
margin-bottom: 8px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
}

/* Canvas (hidden) */
#sp-canvas {
display: none;
}

/* How it works */
.sp-how {
background: #faf5ff;
border: 1.5px solid #e9d5ff;
border-radius: 12px;
padding: 20px 24px;
margin-top: 24px;
}

.sp-how h3 {
margin: 0 0 12px 0;
font-size: 15px;
font-weight: 700;
color: #4c1d95;
}

.sp-how ol {
margin: 0;
padding-left: 20px;
}

.sp-how li {
font-size: 13px;
color: #374151;
line-height: 1.7;
}
</style>

<div class="sp-hero">
<h2>SVG to PNG Converter</h2>
<p>Upload or paste SVG code, set your scale and background, and download a high-resolution PNG — entirely in your browser. No files are ever sent to a server.</p>
</div>

<div id="sp-error" class="sp-error"></div>

<div class="sp-layout">
<!-- Left: Input -->
<div class="sp-panel">
<p class="sp-panel-title">Input SVG</p>

<div class="sp-dropzone" id="sp-dropzone">
<div class="sp-dropzone-icon">&#9653;</div>
<p class="sp-dropzone-text">Drop SVG file here</p>
<p class="sp-dropzone-sub">or click to browse</p>
</div>
<input type="file" id="sp-file-input" accept=".svg,image/svg+xml" style="display:none;">

<div class="sp-field">
<label class="sp-label" for="sp-code">Or paste SVG code</label>
<textarea id="sp-code" class="sp-textarea" placeholder="<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; ...>&#10;  ...&#10;</svg>"></textarea>
</div>

<button class="sp-btn-secondary" id="sp-load-sample" style="margin-top:10px;">Load sample SVG</button>
</div>

<!-- Right: Settings -->
<div class="sp-panel">
<p class="sp-panel-title">Settings</p>
<div class="sp-controls">

<div class="sp-field">
<label class="sp-label">Scale (retina-ready)</label>
<div class="sp-scale-row">
<button class="sp-scale-btn active" data-scale="1">1x</button>
<button class="sp-scale-btn" data-scale="2">2x</button>
<button class="sp-scale-btn" data-scale="3">3x</button>
<button class="sp-scale-btn" data-scale="4">4x</button>
</div>
</div>

<div class="sp-field">
<label class="sp-label">Output Dimensions (px)</label>
<div class="sp-dim-row">
<input type="number" id="sp-width" class="sp-input" placeholder="Width" min="1" max="8000">
<button class="sp-lock-btn locked" id="sp-lock-btn" title="Lock aspect ratio">&#128274;</button>
<input type="number" id="sp-height" class="sp-input" placeholder="Height" min="1" max="8000">
</div>
<p style="font-size:11px;color:#9ca3af;margin:2px 0 0 0;">Leave blank to use SVG's natural size × scale</p>
</div>

<div class="sp-field">
<label class="sp-label">Background</label>
<div class="sp-color-row">
<input type="color" id="sp-bg-color" class="sp-color-input" value="#ffffff" title="Background color">
<button class="sp-transparent-btn active" id="sp-transparent-btn">Transparent</button>
<span style="font-size:12px;color:#6b7280;flex:1;" id="sp-bg-label">Transparent PNG</span>
</div>
</div>

</div>
</div>
</div>

<!-- Preview + Download -->
<div class="sp-panel">
<p class="sp-panel-title">Preview &amp; Download</p>
<div class="sp-preview-wrap" id="sp-preview-wrap">
<div class="sp-preview-placeholder" id="sp-preview-placeholder">
<svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="3"/><path d="M3 9l4-4 4 4 4-6 4 6"/><circle cx="8.5" cy="13.5" r="1.5"/></svg>
<p>Your SVG preview will appear here</p>
</div>
<img id="sp-preview-img" style="display:none;" alt="SVG preview">
</div>

<div class="sp-info-bar" id="sp-info-bar" style="display:none;">
<div class="sp-info-chip">Output: <span id="sp-out-w">—</span> &times; <span id="sp-out-h">—</span> px</div>
<div class="sp-info-chip">Est. size: <span id="sp-out-size">—</span></div>
<div class="sp-info-chip">Scale: <span id="sp-out-scale">1</span>x</div>
</div>

<p class="sp-filename" id="sp-filename" style="display:none;"></p>

<button class="sp-btn-primary" id="sp-convert-btn" disabled>Convert &amp; Download PNG</button>
</div>

<canvas id="sp-canvas"></canvas>

<div class="sp-how">
<h3>How it works</h3>
<ol>
<li>Upload an SVG file or paste SVG code into the text area.</li>
<li>Choose a scale multiplier (2x/3x for retina-sharp exports).</li>
<li>Optionally set custom width/height — the aspect ratio lock keeps proportions intact.</li>
<li>Pick a background color or leave it transparent.</li>
<li>Click <strong>Convert &amp; Download PNG</strong> — the SVG is rendered on an HTML Canvas and saved as PNG.</li>
</ol>
</div>

<script>
(function () {
'use strict';

/* ── State ── */
var svgSrc = '';
var scale = 1;
var aspectLocked = true;
var naturalW = 0, naturalH = 0;
var bgTransparent = true;
var currentFilename = 'image';

/* ── DOM ── */
var dropzone     = document.getElementById('sp-dropzone');
var fileInput    = document.getElementById('sp-file-input');
var codeArea     = document.getElementById('sp-code');
var widthInput   = document.getElementById('sp-width');
var heightInput  = document.getElementById('sp-height');
var lockBtn      = document.getElementById('sp-lock-btn');
var bgColor      = document.getElementById('sp-bg-color');
var transpBtn    = document.getElementById('sp-transparent-btn');
var bgLabel      = document.getElementById('sp-bg-label');
var convertBtn   = document.getElementById('sp-convert-btn');
var previewImg   = document.getElementById('sp-preview-img');
var placeholder  = document.getElementById('sp-preview-placeholder');
var infoBar      = document.getElementById('sp-info-bar');
var outW         = document.getElementById('sp-out-w');
var outH         = document.getElementById('sp-out-h');
var outSize      = document.getElementById('sp-out-size');
var outScale     = document.getElementById('sp-out-scale');
var errorBox     = document.getElementById('sp-error');
var canvas       = document.getElementById('sp-canvas');
var filenameEl   = document.getElementById('sp-filename');
var sampleBtn    = document.getElementById('sp-load-sample');
var scaleBtns    = document.querySelectorAll('.sp-scale-btn');

/* ── Sample SVG ── */
var SAMPLE = '<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200" viewBox="0 0 200 200">\n  <defs>\n    <linearGradient id="g1" x1="0%" y1="0%" x2="100%" y2="100%">\n      <stop offset="0%" stop-color="#7c3aed"/>\n      <stop offset="100%" stop-color="#db2777"/>\n    </linearGradient>\n  </defs>\n  <circle cx="100" cy="100" r="90" fill="url(#g1)"/>\n  <text x="100" y="115" text-anchor="middle" font-family="sans-serif" font-size="60" fill="white">&#9830;</text>\n</svg>';

/* ── Helpers ── */
function showError(msg) {
errorBox.textContent = msg;
errorBox.style.display = 'block';
}
function clearError() {
errorBox.style.display = 'none';
}

function estimateFileSize(w, h, transparent) {
// rough estimate: ~3-4 bytes per pixel (PNG compression ~50%)
var bytes = w * h * (transparent ? 4 : 3) * 0.5;
if (bytes < 1024) return bytes.toFixed(0) + ' B';
if (bytes < 1048576) return (bytes / 1024).toFixed(1) + ' KB';
return (bytes / 1048576).toFixed(1) + ' MB';
}

function updateInfoBar(w, h) {
outW.textContent = w;
outH.textContent = h;
outScale.textContent = scale;
outSize.textContent = estimateFileSize(w, h, bgTransparent);
infoBar.style.display = 'flex';
}

function getSVGDimensions(svgText) {
var parser = new DOMParser();
var doc = parser.parseFromString(svgText, 'image/svg+xml');
var svgEl = doc.querySelector('svg');
if (!svgEl) return { w: 0, h: 0 };

var vb = svgEl.getAttribute('viewBox');
var w = parseFloat(svgEl.getAttribute('width')) || 0;
var h = parseFloat(svgEl.getAttribute('height')) || 0;

if ((!w || !h) && vb) {
var parts = vb.trim().split(/[\s,]+/);
if (parts.length >= 4) {
w = w || parseFloat(parts[2]);
h = h || parseFloat(parts[3]);
}
}
return { w: w || 300, h: h || 150 };
}

function loadSVG(text, filename) {
clearError();
if (!text || !text.trim().startsWith('<')) {
showError('The input does not appear to be valid SVG.');
return;
}
svgSrc = text;
currentFilename = filename || 'image';
filenameEl.textContent = currentFilename + '.svg';
filenameEl.style.display = 'block';

var dims = getSVGDimensions(text);
naturalW = dims.w;
naturalH = dims.h;

// Reset dimension fields
widthInput.value = '';
heightInput.value = '';

renderPreview();
convertBtn.disabled = false;
}

function getOutputDimensions() {
var w = parseInt(widthInput.value, 10) || 0;
var h = parseInt(heightInput.value, 10) || 0;
var baseW = naturalW * scale;
var baseH = naturalH * scale;

if (!w && !h) return { w: Math.round(baseW), h: Math.round(baseH) };
if (w && !h) return { w: w, h: Math.round(w * (naturalH / naturalW)) };
if (!w && h) return { w: Math.round(h * (naturalW / naturalH)), h: h };
return { w: w, h: h };
}

function renderPreview() {
if (!svgSrc) return;
var dims = getOutputDimensions();
updateInfoBar(dims.w, dims.h);

// Build a data URL for preview
var blob = new Blob([svgSrc], { type: 'image/svg+xml' });
var url = URL.createObjectURL(blob);
previewImg.onload = function () {
URL.revokeObjectURL(url);
};
previewImg.src = url;
previewImg.style.display = 'block';
placeholder.style.display = 'none';
}

function convertAndDownload() {
if (!svgSrc) return;
clearError();

var dims = getOutputDimensions();
var W = dims.w;
var H = dims.h;

canvas.width  = W;
canvas.height = H;
var ctx = canvas.getContext('2d');
ctx.clearRect(0, 0, W, H);

if (!bgTransparent) {
ctx.fillStyle = bgColor.value;
ctx.fillRect(0, 0, W, H);
}

var img = new Image();
var svgBlob = new Blob([svgSrc], { type: 'image/svg+xml;charset=utf-8' });
var url = URL.createObjectURL(svgBlob);

img.onload = function () {
ctx.drawImage(img, 0, 0, W, H);
URL.revokeObjectURL(url);

try {
var dataURL = canvas.toDataURL('image/png');
var link = document.createElement('a');
link.download = currentFilename + '_' + W + 'x' + H + '.png';
link.href = dataURL;
link.click();
} catch (e) {
showError('Export failed. If your SVG contains external resources, they may be blocked by the browser for security reasons.');
}
};

img.onerror = function () {
URL.revokeObjectURL(url);
showError('Failed to render SVG. Please check that your SVG is valid.');
};

img.src = url;
}

/* ── Event: Dropzone ── */
dropzone.addEventListener('click', function () { fileInput.click(); });

dropzone.addEventListener('dragover', function (e) {
e.preventDefault();
dropzone.classList.add('sp-drag-over');
});
dropzone.addEventListener('dragleave', function () {
dropzone.classList.remove('sp-drag-over');
});
dropzone.addEventListener('drop', function (e) {
e.preventDefault();
dropzone.classList.remove('sp-drag-over');
var file = e.dataTransfer.files[0];
if (file) readFile(file);
});

fileInput.addEventListener('change', function () {
if (fileInput.files[0]) readFile(fileInput.files[0]);
});

function readFile(file) {
if (!file.name.match(/\.svg$/i) && file.type !== 'image/svg+xml') {
showError('Please select an SVG file.');
return;
}
var reader = new FileReader();
reader.onload = function (e) {
codeArea.value = e.target.result;
loadSVG(e.target.result, file.name.replace(/\.svg$/i, ''));
};
reader.readAsText(file);
}

/* ── Event: Paste SVG code ── */
codeArea.addEventListener('input', function () {
if (codeArea.value.trim()) {
loadSVG(codeArea.value, 'svg-export');
}
});

/* ── Event: Scale buttons ── */
scaleBtns.forEach(function (btn) {
btn.addEventListener('click', function () {
scaleBtns.forEach(function (b) { b.classList.remove('active'); });
btn.classList.add('active');
scale = parseInt(btn.dataset.scale, 10);
if (svgSrc) renderPreview();
});
});

/* ── Event: Dimension inputs ── */
var aspectRatio = 1;

widthInput.addEventListener('input', function () {
if (!aspectLocked) { if (svgSrc) renderPreview(); return; }
var w = parseInt(widthInput.value, 10);
if (w && naturalH && naturalW) {
heightInput.value = Math.round(w * (naturalH / naturalW));
}
if (svgSrc) renderPreview();
});

heightInput.addEventListener('input', function () {
if (!aspectLocked) { if (svgSrc) renderPreview(); return; }
var h = parseInt(heightInput.value, 10);
if (h && naturalW && naturalH) {
widthInput.value = Math.round(h * (naturalW / naturalH));
}
if (svgSrc) renderPreview();
});

/* ── Event: Lock button ── */
lockBtn.addEventListener('click', function () {
aspectLocked = !aspectLocked;
lockBtn.classList.toggle('locked', aspectLocked);
lockBtn.textContent = aspectLocked ? '\uD83D\uDD12' : '\uD83D\uDD13';
});

/* ── Event: Background ── */
transpBtn.addEventListener('click', function () {
bgTransparent = !bgTransparent;
transpBtn.classList.toggle('active', bgTransparent);
bgLabel.textContent = bgTransparent ? 'Transparent PNG' : bgColor.value;
if (svgSrc) renderPreview();
});

bgColor.addEventListener('input', function () {
bgTransparent = false;
transpBtn.classList.remove('active');
bgLabel.textContent = bgColor.value;
if (svgSrc) renderPreview();
});

/* ── Event: Convert ── */
convertBtn.addEventListener('click', convertAndDownload);

/* ── Event: Sample ── */
sampleBtn.addEventListener('click', function () {
codeArea.value = SAMPLE;
loadSVG(SAMPLE, 'sample');
});

})();
</script>

> Generate placeholder images → [Placeholder Image Generator](/tools/placeholder-image/)

> Resize images → [Image Resizer](/tools/image-resizer/)

</div>
