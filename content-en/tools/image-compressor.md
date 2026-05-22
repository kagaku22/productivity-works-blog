---
title: "Image Compressor"
date: 2025-05-16
description: "Free online image compressor. Reduce image file size while maintaining quality. Supports JPEG and PNG. Adjust quality, see before/after comparison."
categories: ["Free Tools"]
tags: ["Image Tools", "Design", "Free Tools"]
slug: "image-compressor"
ShowToc: false
cover:
  image: "/images/covers/image-compressor.png"
  alt: "Image Compressor"
---

Free online image compressor — no upload to server, all processing in your browser. Adjust quality, pick output format, and download instantly.

<div id="ic-app">
<style>
#ic-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 780px;
margin: 0 auto;
color: #1a1a1a;
}
#ic-app * { box-sizing: border-box; }

#ic-drop-zone {
border: 2px dashed #ccc;
border-radius: 12px;
padding: 48px 24px;
text-align: center;
cursor: pointer;
transition: border-color 0.2s, background 0.2s;
background: #fafafa;
margin-bottom: 24px;
}
#ic-drop-zone:hover, #ic-drop-zone.ic-dragover {
border-color: #4f8ef7;
background: #f0f5ff;
}
#ic-drop-zone svg { display: block; margin: 0 auto 12px; }
#ic-drop-zone p { margin: 0; color: #555; font-size: 0.97rem; }
#ic-drop-zone strong { color: #333; }
#ic-file-input { display: none; }

#ic-controls {
display: none;
background: #f5f7fa;
border-radius: 12px;
padding: 20px 24px;
margin-bottom: 24px;
}
#ic-controls.ic-visible { display: block; }

.ic-control-row {
display: flex;
align-items: center;
gap: 16px;
margin-bottom: 16px;
flex-wrap: wrap;
}
.ic-control-row:last-child { margin-bottom: 0; }
.ic-label {
font-size: 0.88rem;
font-weight: 600;
color: #444;
min-width: 110px;
}
#ic-quality-slider {
flex: 1;
min-width: 140px;
accent-color: #4f8ef7;
}
#ic-quality-val {
font-size: 0.95rem;
font-weight: 700;
color: #4f8ef7;
min-width: 38px;
text-align: right;
}
#ic-format-select {
border: 1px solid #d0d5dd;
border-radius: 6px;
padding: 6px 10px;
font-size: 0.93rem;
background: #fff;
color: #333;
cursor: pointer;
}

#ic-stats {
display: none;
margin-bottom: 24px;
}
#ic-stats.ic-visible { display: flex; gap: 12px; flex-wrap: wrap; }

.ic-stat-card {
flex: 1;
min-width: 140px;
background: #fff;
border: 1px solid #e4e7ec;
border-radius: 10px;
padding: 14px 18px;
text-align: center;
}
.ic-stat-card .ic-stat-label {
font-size: 0.78rem;
color: #888;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 4px;
}
.ic-stat-card .ic-stat-value {
font-size: 1.22rem;
font-weight: 700;
color: #1a1a1a;
}
.ic-stat-card.ic-reduction .ic-stat-value { color: #16a34a; }

#ic-preview-wrap {
display: none;
margin-bottom: 24px;
}
#ic-preview-wrap.ic-visible { display: block; }
.ic-preview-header {
display: flex;
gap: 0;
margin-bottom: 8px;
}
.ic-preview-header span {
flex: 1;
text-align: center;
font-size: 0.82rem;
font-weight: 600;
color: #666;
text-transform: uppercase;
letter-spacing: 0.05em;
padding: 4px 0;
background: #f0f0f0;
border-radius: 4px 0 0 4px;
}
.ic-preview-header span:last-child { border-radius: 0 4px 4px 0; }
.ic-previews {
display: flex;
gap: 8px;
}
.ic-previews canvas, .ic-previews img {
width: 50%;
border-radius: 8px;
border: 1px solid #e4e7ec;
display: block;
object-fit: contain;
max-height: 320px;
background: #f7f7f7;
}

#ic-compress-btn {
display: none;
width: 100%;
padding: 13px;
background: #4f8ef7;
color: #fff;
border: none;
border-radius: 8px;
font-size: 1rem;
font-weight: 600;
cursor: pointer;
margin-bottom: 12px;
transition: background 0.2s;
}
#ic-compress-btn:hover { background: #2d6fe0; }
#ic-compress-btn.ic-visible { display: block; }

#ic-download-btn {
display: none;
width: 100%;
padding: 13px;
background: #16a34a;
color: #fff;
border: none;
border-radius: 8px;
font-size: 1rem;
font-weight: 600;
cursor: pointer;
margin-bottom: 24px;
transition: background 0.2s;
text-decoration: none;
text-align: center;
}
#ic-download-btn:hover { background: #15803d; }
#ic-download-btn.ic-visible { display: block; }

#ic-reset-btn {
display: none;
width: 100%;
padding: 10px;
background: #fff;
color: #555;
border: 1px solid #d0d5dd;
border-radius: 8px;
font-size: 0.93rem;
cursor: pointer;
margin-bottom: 24px;
transition: background 0.2s;
}
#ic-reset-btn:hover { background: #f5f5f5; }
#ic-reset-btn.ic-visible { display: block; }

#ic-error {
display: none;
color: #b91c1c;
background: #fef2f2;
border: 1px solid #fecaca;
border-radius: 8px;
padding: 10px 14px;
font-size: 0.93rem;
margin-bottom: 16px;
}
#ic-error.ic-visible { display: block; }

#ic-canvas-orig, #ic-canvas-comp { display: none; }

@media (max-width: 520px) {
#ic-controls { padding: 14px 12px; }
.ic-control-row { gap: 8px; }
.ic-label { min-width: 80px; font-size: 0.82rem; }
.ic-stat-card { min-width: 100px; padding: 10px 10px; }
.ic-stat-card .ic-stat-value { font-size: 1rem; }
}
</style>

<div id="ic-drop-zone" role="button" tabindex="0" aria-label="Upload image">
<svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="#aab" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
<rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/>
<polyline points="21 15 16 10 5 21"/>
</svg>
<p><strong>Click or drag & drop</strong> an image here</p>
<p style="margin-top:6px;font-size:0.83rem;color:#aaa;">JPEG · PNG · WebP · GIF · BMP</p>
<input type="file" id="ic-file-input" accept="image/*">
</div>

<div id="ic-error"></div>

<div id="ic-controls">
<div class="ic-control-row">
<span class="ic-label">Quality</span>
<input type="range" id="ic-quality-slider" min="1" max="100" value="80">
<span id="ic-quality-val">80%</span>
</div>
<div class="ic-control-row">
<span class="ic-label">Output Format</span>
<select id="ic-format-select">
<option value="image/jpeg">JPEG</option>
<option value="image/png">PNG</option>
<option value="image/webp">WebP</option>
</select>
</div>
</div>

<button id="ic-compress-btn">Compress Image</button>

<div id="ic-stats">
<div class="ic-stat-card">
<div class="ic-stat-label">Original Size</div>
<div class="ic-stat-value" id="ic-orig-size">—</div>
</div>
<div class="ic-stat-card">
<div class="ic-stat-label">Compressed Size</div>
<div class="ic-stat-value" id="ic-comp-size">—</div>
</div>
<div class="ic-stat-card ic-reduction">
<div class="ic-stat-label">Reduction</div>
<div class="ic-stat-value" id="ic-reduction">—</div>
</div>
</div>

<div id="ic-preview-wrap">
<div class="ic-preview-header">
<span>Original</span>
<span style="border-radius:0 4px 4px 0;">Compressed</span>
</div>
<div class="ic-previews">
<img id="ic-img-orig" alt="Original">
<canvas id="ic-canvas-comp-preview"></canvas>
</div>
</div>

<a id="ic-download-btn" download="compressed-image">Download Compressed Image</a>
<button id="ic-reset-btn">Reset / Upload Another</button>

<canvas id="ic-canvas-orig"></canvas>
<canvas id="ic-canvas-comp"></canvas>

<script>
(function() {
var dropZone   = document.getElementById('ic-drop-zone');
var fileInput  = document.getElementById('ic-file-input');
var controls   = document.getElementById('ic-controls');
var slider     = document.getElementById('ic-quality-slider');
var qualVal    = document.getElementById('ic-quality-val');
var fmtSelect  = document.getElementById('ic-format-select');
var compBtn    = document.getElementById('ic-compress-btn');
var dlBtn      = document.getElementById('ic-download-btn');
var resetBtn   = document.getElementById('ic-reset-btn');
var stats      = document.getElementById('ic-stats');
var origSizeEl = document.getElementById('ic-orig-size');
var compSizeEl = document.getElementById('ic-comp-size');
var reductEl   = document.getElementById('ic-reduction');
var previewWrap= document.getElementById('ic-preview-wrap');
var imgOrig    = document.getElementById('ic-img-orig');
var canvasComp = document.getElementById('ic-canvas-comp');
var canvasCompPrev = document.getElementById('ic-canvas-comp-preview');
var errorEl    = document.getElementById('ic-error');

var origFile = null;
var origImg  = null;

function fmtBytes(b) {
if (b < 1024) return b + ' B';
if (b < 1048576) return (b / 1024).toFixed(1) + ' KB';
return (b / 1048576).toFixed(2) + ' MB';
}

function showError(msg) {
errorEl.textContent = msg;
errorEl.classList.add('ic-visible');
}
function hideError() {
errorEl.classList.remove('ic-visible');
}

function loadFile(file) {
if (!file || !file.type.startsWith('image/')) {
showError('Please select a valid image file.');
return;
}
hideError();
origFile = file;
var reader = new FileReader();
reader.onload = function(e) {
var img = new Image();
img.onload = function() {
origImg = img;
imgOrig.src = e.target.result;
controls.classList.add('ic-visible');
compBtn.classList.add('ic-visible');
dropZone.style.display = 'none';
};
img.onerror = function() { showError('Could not load image.'); };
img.src = e.target.result;
};
reader.readAsDataURL(file);
}

slider.addEventListener('input', function() {
qualVal.textContent = slider.value + '%';
});

compBtn.addEventListener('click', function() {
if (!origImg) return;
hideError();

var fmt   = fmtSelect.value;
var qual  = parseInt(slider.value, 10) / 100;
var w = origImg.naturalWidth;
var h = origImg.naturalHeight;

canvasComp.width  = w;
canvasComp.height = h;
var ctx = canvasComp.getContext('2d');
ctx.drawImage(origImg, 0, 0, w, h);

canvasComp.toBlob(function(blob) {
if (!blob) { showError('Compression failed. Try a different format.'); return; }

var origBytes = origFile.size;
var compBytes = blob.size;
var pct = origBytes > 0 ? ((1 - compBytes / origBytes) * 100) : 0;

origSizeEl.textContent = fmtBytes(origBytes);
compSizeEl.textContent = fmtBytes(compBytes);
reductEl.textContent   = (pct > 0 ? '-' : '+') + Math.abs(pct).toFixed(1) + '%';

stats.classList.add('ic-visible');

// Side-by-side preview canvas
canvasCompPrev.width  = w;
canvasCompPrev.height = h;
canvasCompPrev.getContext('2d').drawImage(canvasComp, 0, 0);

// Inline style for responsive sizing
canvasCompPrev.style.width  = '50%';
canvasCompPrev.style.height = 'auto';

previewWrap.classList.add('ic-visible');

// Download link
var url = URL.createObjectURL(blob);
var ext = fmt === 'image/jpeg' ? 'jpg' : fmt === 'image/png' ? 'png' : 'webp';
dlBtn.href = url;
dlBtn.download = 'compressed-image.' + ext;
dlBtn.classList.add('ic-visible');
resetBtn.classList.add('ic-visible');
compBtn.textContent = 'Re-compress';
}, fmt, qual);
});

resetBtn.addEventListener('click', function() {
origFile = null;
origImg  = null;
fileInput.value = '';
controls.classList.remove('ic-visible');
compBtn.classList.remove('ic-visible');
dlBtn.classList.remove('ic-visible');
resetBtn.classList.remove('ic-visible');
stats.classList.remove('ic-visible');
previewWrap.classList.remove('ic-visible');
dropZone.style.display = '';
compBtn.textContent = 'Compress Image';
hideError();
});

dropZone.addEventListener('click', function() { fileInput.click(); });
dropZone.addEventListener('keydown', function(e) { if (e.key === 'Enter' || e.key === ' ') fileInput.click(); });
fileInput.addEventListener('change', function() { if (fileInput.files[0]) loadFile(fileInput.files[0]); });

dropZone.addEventListener('dragover', function(e) { e.preventDefault(); dropZone.classList.add('ic-dragover'); });
dropZone.addEventListener('dragleave', function() { dropZone.classList.remove('ic-dragover'); });
dropZone.addEventListener('drop', function(e) {
e.preventDefault();
dropZone.classList.remove('ic-dragover');
var f = e.dataTransfer.files[0];
if (f) loadFile(f);
});
})();
</script>
</div>

---

**How it works:** Your image never leaves your device. The browser draws it onto an HTML5 Canvas and re-encodes it at the quality level you choose using `canvas.toBlob()`. Choose a lower quality for smaller files, or keep it high for near-lossless results.

**Tips:**
- JPEG gives the smallest files for photos; PNG preserves transparency; WebP often beats both.
- Quality around 75–85% is usually indistinguishable from the original for photos.
- Compressing a PNG as JPEG will remove transparency — use PNG or WebP if you need it.

---

**Related tools**

> Resize images → [Image Resizer](/tools/image-resizer/)

> Crop images → [Image Cropper](/tools/image-cropper/)

## Related Articles

- [Best AI Image Generators Free 2026](/posts/best-ai-image-generators-free-2026/)
