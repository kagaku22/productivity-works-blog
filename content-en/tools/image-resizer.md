---
title: "Image Resizer - Free Online Tool to Resize & Compress Images"
date: 2025-05-16
description: "Resize images online for free. Set custom dimensions, lock aspect ratio, pick preset sizes for social media, and export as JPEG, PNG, or WebP. No upload required — works entirely in your browser."
categories: ["Free Tools"]
tags: ["image resizer", "resize image", "image compressor", "photo resize", "canvas api"]
slug: "image-resizer"
aliases: ["/tools/image-compressor/", "/tools/image-resizer/"]
cover:
  image: "/images/covers/image-resizer.png"
  alt: "Image Resizer"
ShowToc: false
---

<div id="resize-app">

<style>
#resize-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 0 48px 0;
  color: #1a202c;
}

#resize-app * {
  box-sizing: border-box;
}

/* Hero */
.ra-hero {
  background: linear-gradient(135deg, #059669 0%, #047857 50%, #065f46 100%);
  border-radius: 16px;
  padding: 32px 28px;
  margin-bottom: 24px;
  color: #fff;
}

.ra-hero h2 {
  margin: 0 0 6px 0;
  font-size: 24px;
  font-weight: 800;
}

.ra-hero p {
  margin: 0;
  font-size: 14px;
  opacity: 0.88;
  line-height: 1.6;
}

/* Drop Zone */
.ra-dropzone {
  border: 3px dashed #059669;
  border-radius: 14px;
  padding: 44px 24px;
  text-align: center;
  background: #f0fdf4;
  cursor: pointer;
  transition: background 0.2s, border-color 0.2s;
  margin-bottom: 20px;
  position: relative;
}

.ra-dropzone.drag-over {
  background: #d1fae5;
  border-color: #047857;
}

.ra-dropzone-icon {
  font-size: 48px;
  line-height: 1;
  margin-bottom: 12px;
  display: block;
}

.ra-dropzone-title {
  font-size: 17px;
  font-weight: 700;
  color: #065f46;
  margin-bottom: 6px;
}

.ra-dropzone-sub {
  font-size: 13px;
  color: #6b7280;
  margin-bottom: 16px;
}

.ra-browse-btn {
  display: inline-block;
  padding: 10px 24px;
  background: #059669;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}

.ra-browse-btn:hover {
  background: #047857;
}

#ra-file-input {
  display: none;
}

/* Card */
.ra-card {
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 2px 16px rgba(0,0,0,0.08);
  padding: 22px 24px;
  margin-bottom: 18px;
}

.ra-card h3 {
  margin: 0 0 18px 0;
  font-size: 13px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  border-bottom: 2px solid #f0fdf4;
  padding-bottom: 10px;
}

/* Preview */
.ra-preview-wrap {
  display: flex;
  gap: 20px;
  align-items: flex-start;
  flex-wrap: wrap;
}

.ra-preview-box {
  flex: 1;
  min-width: 200px;
  text-align: center;
}

.ra-preview-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #6b7280;
  margin-bottom: 8px;
}

.ra-preview-img-wrap {
  border-radius: 10px;
  overflow: hidden;
  background: repeating-conic-gradient(#e5e7eb 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
  border: 1px solid #e5e7eb;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 120px;
  max-height: 300px;
}

.ra-preview-img-wrap img {
  max-width: 100%;
  max-height: 280px;
  display: block;
  object-fit: contain;
}

.ra-preview-info {
  margin-top: 8px;
  font-size: 12px;
  color: #6b7280;
}

/* Dimension inputs */
.ra-dim-row {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

.ra-dim-field {
  display: flex;
  flex-direction: column;
  gap: 5px;
  flex: 1;
  min-width: 110px;
}

.ra-dim-field label {
  font-size: 12px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.ra-dim-input {
  padding: 9px 12px;
  border: 2px solid #d1fae5;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 600;
  color: #1a202c;
  transition: border-color 0.2s;
  width: 100%;
}

.ra-dim-input:focus {
  outline: none;
  border-color: #059669;
}

.ra-lock-btn {
  margin-top: 20px;
  padding: 9px 16px;
  border: 2px solid #d1fae5;
  border-radius: 8px;
  background: #fff;
  font-size: 18px;
  cursor: pointer;
  transition: background 0.2s, border-color 0.2s;
  flex-shrink: 0;
  title: "Toggle aspect ratio lock";
}

.ra-lock-btn.locked {
  background: #d1fae5;
  border-color: #059669;
}

.ra-lock-btn:hover {
  background: #ecfdf5;
}

/* Presets */
.ra-preset-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 10px;
}

.ra-preset-btn {
  padding: 10px 14px;
  border: 2px solid #e5e7eb;
  border-radius: 10px;
  background: #fff;
  text-align: left;
  cursor: pointer;
  transition: all 0.18s;
}

.ra-preset-btn:hover {
  border-color: #059669;
  background: #f0fdf4;
}

.ra-preset-name {
  font-size: 13px;
  font-weight: 700;
  color: #1a202c;
  display: block;
  margin-bottom: 2px;
}

.ra-preset-size {
  font-size: 11px;
  color: #6b7280;
}

/* Quality + Format */
.ra-settings-row {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  align-items: flex-start;
}

.ra-setting-group {
  flex: 1;
  min-width: 180px;
}

.ra-setting-group label {
  display: block;
  font-size: 12px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 8px;
}

.ra-quality-wrap {
  display: flex;
  align-items: center;
  gap: 10px;
}

.ra-quality-slider {
  flex: 1;
  height: 6px;
  border-radius: 3px;
  background: linear-gradient(to right, #d1fae5, #059669);
  -webkit-appearance: none;
  appearance: none;
  outline: none;
  cursor: pointer;
}

.ra-quality-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid #059669;
  box-shadow: 0 1px 4px rgba(0,0,0,0.15);
  cursor: pointer;
}

.ra-quality-slider::-moz-range-thumb {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid #059669;
  box-shadow: 0 1px 4px rgba(0,0,0,0.15);
  cursor: pointer;
}

.ra-quality-val {
  font-size: 15px;
  font-weight: 800;
  color: #059669;
  width: 42px;
  text-align: right;
}

.ra-format-btns {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.ra-format-btn {
  padding: 8px 18px;
  border: 2px solid #e5e7eb;
  border-radius: 20px;
  background: #fff;
  font-size: 13px;
  font-weight: 700;
  color: #374151;
  cursor: pointer;
  transition: all 0.18s;
}

.ra-format-btn:hover {
  border-color: #059669;
  color: #059669;
}

.ra-format-btn.active {
  border-color: #059669;
  background: #059669;
  color: #fff;
}

/* Size estimate + comparison */
.ra-size-comparison {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.ra-size-box {
  flex: 1;
  min-width: 140px;
  background: #f9fafb;
  border-radius: 10px;
  padding: 14px 16px;
  text-align: center;
  border: 1px solid #e5e7eb;
}

.ra-size-box-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #6b7280;
  margin-bottom: 6px;
}

.ra-size-box-value {
  font-size: 20px;
  font-weight: 800;
  color: #1a202c;
}

.ra-size-box-sub {
  font-size: 11px;
  color: #9ca3af;
  margin-top: 3px;
}

.ra-size-box.original .ra-size-box-value {
  color: #374151;
}

.ra-size-box.output .ra-size-box-value {
  color: #059669;
}

.ra-size-box.savings .ra-size-box-value {
  color: #dc2626;
}

/* Download button */
.ra-download-btn {
  display: block;
  width: 100%;
  padding: 14px 24px;
  background: linear-gradient(135deg, #059669, #047857);
  color: #fff;
  border: none;
  border-radius: 12px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.1s;
  text-align: center;
  margin-top: 4px;
}

.ra-download-btn:hover:not(:disabled) {
  opacity: 0.92;
}

.ra-download-btn:active:not(:disabled) {
  transform: scale(0.98);
}

.ra-download-btn:disabled {
  background: #9ca3af;
  cursor: not-allowed;
}

/* Hidden canvas */
#ra-canvas {
  display: none;
}

/* Placeholder state */
.ra-placeholder {
  text-align: center;
  padding: 32px 16px;
  color: #9ca3af;
  font-size: 14px;
}

.ra-placeholder-icon {
  font-size: 40px;
  display: block;
  margin-bottom: 8px;
}

/* Responsive */
@media (max-width: 600px) {
  .ra-hero {
    padding: 24px 18px;
  }
  .ra-hero h2 {
    font-size: 20px;
  }
  .ra-card {
    padding: 18px 16px;
  }
  .ra-dim-row {
    gap: 8px;
  }
  .ra-preset-grid {
    grid-template-columns: 1fr 1fr;
  }
  .ra-settings-row {
    flex-direction: column;
    gap: 16px;
  }
  .ra-size-comparison {
    gap: 10px;
  }
}
</style>

<!-- Hero -->
<div class="ra-hero">
  <h2>Free Image Resizer</h2>
  <p>Resize and compress images instantly — no upload, no account. Everything runs in your browser using the Canvas API.</p>
</div>

<!-- Drop Zone -->
<div class="ra-dropzone" id="ra-dropzone">
  <span class="ra-dropzone-icon">🖼️</span>
  <div class="ra-dropzone-title">Drop your image here</div>
  <div class="ra-dropzone-sub">Supports JPG, PNG, WebP, GIF, BMP · Max 20 MB</div>
  <button class="ra-browse-btn" onclick="document.getElementById('ra-file-input').click()">Choose File</button>
  <input type="file" id="ra-file-input" accept="image/*">
</div>

<!-- Preview -->
<div class="ra-card" id="ra-preview-card">
  <h3>Preview</h3>
  <div id="ra-preview-area">
    <div class="ra-placeholder">
      <span class="ra-placeholder-icon">📂</span>
      Upload an image to see the preview
    </div>
  </div>
</div>

<!-- Dimensions -->
<div class="ra-card">
  <h3>Dimensions</h3>
  <div class="ra-dim-row">
    <div class="ra-dim-field">
      <label for="ra-width">Width (px)</label>
      <input type="number" class="ra-dim-input" id="ra-width" min="1" max="8000" placeholder="e.g. 1200">
    </div>
    <button class="ra-lock-btn locked" id="ra-lock-btn" title="Lock/unlock aspect ratio">🔒</button>
    <div class="ra-dim-field">
      <label for="ra-height">Height (px)</label>
      <input type="number" class="ra-dim-input" id="ra-height" min="1" max="8000" placeholder="e.g. 630">
    </div>
  </div>
</div>

<!-- Presets -->
<div class="ra-card">
  <h3>Preset Sizes</h3>
  <div class="ra-preset-grid" id="ra-preset-grid">
    <button class="ra-preset-btn" data-w="1200" data-h="630">
      <span class="ra-preset-name">OG / Facebook</span>
      <span class="ra-preset-size">1200 × 630 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1080" data-h="1080">
      <span class="ra-preset-name">Instagram Square</span>
      <span class="ra-preset-size">1080 × 1080 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1280" data-h="720">
      <span class="ra-preset-name">YouTube Thumbnail</span>
      <span class="ra-preset-size">1280 × 720 px</span>
    </button>
    <button class="ra-preset-btn" data-w="400" data-h="400">
      <span class="ra-preset-name">Avatar / Profile</span>
      <span class="ra-preset-size">400 × 400 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1080" data-h="1920">
      <span class="ra-preset-name">Instagram Story</span>
      <span class="ra-preset-size">1080 × 1920 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1500" data-h="500">
      <span class="ra-preset-name">Twitter Header</span>
      <span class="ra-preset-size">1500 × 500 px</span>
    </button>
    <button class="ra-preset-btn" data-w="800" data-h="800">
      <span class="ra-preset-name">Blog Thumbnail</span>
      <span class="ra-preset-size">800 × 800 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1920" data-h="1080">
      <span class="ra-preset-name">Full HD</span>
      <span class="ra-preset-size">1920 × 1080 px</span>
    </button>
  </div>
</div>

<!-- Quality & Format -->
<div class="ra-card">
  <h3>Output Settings</h3>
  <div class="ra-settings-row">
    <div class="ra-setting-group">
      <label>Quality (JPEG / WebP)</label>
      <div class="ra-quality-wrap">
        <input type="range" class="ra-quality-slider" id="ra-quality" min="10" max="100" value="85">
        <span class="ra-quality-val" id="ra-quality-val">85%</span>
      </div>
    </div>
    <div class="ra-setting-group">
      <label>Output Format</label>
      <div class="ra-format-btns">
        <button class="ra-format-btn active" data-fmt="image/jpeg">JPEG</button>
        <button class="ra-format-btn" data-fmt="image/png">PNG</button>
        <button class="ra-format-btn" data-fmt="image/webp">WebP</button>
      </div>
    </div>
  </div>
</div>

<!-- Size Comparison -->
<div class="ra-card">
  <h3>File Size Estimate</h3>
  <div class="ra-size-comparison">
    <div class="ra-size-box original">
      <div class="ra-size-box-label">Original Size</div>
      <div class="ra-size-box-value" id="ra-orig-size">—</div>
      <div class="ra-size-box-sub" id="ra-orig-dim">Upload an image</div>
    </div>
    <div class="ra-size-box output">
      <div class="ra-size-box-label">Output Size (est.)</div>
      <div class="ra-size-box-value" id="ra-out-size">—</div>
      <div class="ra-size-box-sub" id="ra-out-dim">—</div>
    </div>
    <div class="ra-size-box savings">
      <div class="ra-size-box-label">Size Reduction</div>
      <div class="ra-size-box-value" id="ra-savings">—</div>
      <div class="ra-size-box-sub" id="ra-savings-pct">—</div>
    </div>
  </div>
</div>

<!-- Download -->
<div class="ra-card">
  <button class="ra-download-btn" id="ra-download-btn" disabled>Download Resized Image</button>
</div>

<canvas id="ra-canvas"></canvas>

<script>
(function() {
  var img = null;
  var origFile = null;
  var origWidth = 0, origHeight = 0;
  var aspectRatio = 1;
  var locked = true;
  var fmt = 'image/jpeg';
  var updatingDim = false;

  // DOM refs
  var dropzone     = document.getElementById('ra-dropzone');
  var fileInput    = document.getElementById('ra-file-input');
  var previewArea  = document.getElementById('ra-preview-area');
  var widthInput   = document.getElementById('ra-width');
  var heightInput  = document.getElementById('ra-height');
  var lockBtn      = document.getElementById('ra-lock-btn');
  var qualitySlider= document.getElementById('ra-quality');
  var qualityVal   = document.getElementById('ra-quality-val');
  var origSizeEl   = document.getElementById('ra-orig-size');
  var origDimEl    = document.getElementById('ra-orig-dim');
  var outSizeEl    = document.getElementById('ra-out-size');
  var outDimEl     = document.getElementById('ra-out-dim');
  var savingsEl    = document.getElementById('ra-savings');
  var savingsPctEl = document.getElementById('ra-savings-pct');
  var downloadBtn  = document.getElementById('ra-download-btn');
  var canvas       = document.getElementById('ra-canvas');
  var ctx          = canvas.getContext('2d');

  // --- Drag & Drop ---
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
    var file = e.dataTransfer.files[0];
    if (file && file.type.startsWith('image/')) loadFile(file);
  });

  fileInput.addEventListener('change', function() {
    if (fileInput.files[0]) loadFile(fileInput.files[0]);
  });

  // --- Load File ---
  function loadFile(file) {
    if (file.size > 20 * 1024 * 1024) {
      alert('File too large. Please use an image under 20 MB.');
      return;
    }
    origFile = file;
    var reader = new FileReader();
    reader.onload = function(e) {
      img = new Image();
      img.onload = function() {
        origWidth  = img.naturalWidth;
        origHeight = img.naturalHeight;
        aspectRatio = origWidth / origHeight;
        widthInput.value  = origWidth;
        heightInput.value = origHeight;
        renderPreview();
        updateSizes();
        downloadBtn.disabled = false;
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }

  // --- Preview ---
  function renderPreview() {
    var w = parseInt(widthInput.value) || origWidth;
    var h = parseInt(heightInput.value) || origHeight;

    // Draw to canvas for output
    canvas.width  = w;
    canvas.height = h;
    ctx.clearRect(0, 0, w, h);
    if (img) ctx.drawImage(img, 0, 0, w, h);

    // Build before/after HTML
    var origSrc = img.src;
    var outSrc  = canvas.toDataURL(fmt, parseInt(qualitySlider.value) / 100);

    previewArea.innerHTML =
      '<div class="ra-preview-wrap">' +
        '<div class="ra-preview-box">' +
          '<div class="ra-preview-label">Original (' + origWidth + ' x ' + origHeight + ')</div>' +
          '<div class="ra-preview-img-wrap"><img src="' + origSrc + '" alt="Original"></div>' +
          '<div class="ra-preview-info">' + formatBytes(origFile ? origFile.size : 0) + '</div>' +
        '</div>' +
        '<div class="ra-preview-box">' +
          '<div class="ra-preview-label">Output (' + w + ' x ' + h + ')</div>' +
          '<div class="ra-preview-img-wrap"><img src="' + outSrc + '" alt="Resized"></div>' +
          '<div class="ra-preview-info">' + formatBytes(estimateSize(outSrc)) + '</div>' +
        '</div>' +
      '</div>';
  }

  // --- Size estimate ---
  function estimateSize(dataUrl) {
    // dataUrl length * 3/4 - padding
    var base64 = dataUrl.split(',')[1] || '';
    var padding = (base64.endsWith('==') ? 2 : base64.endsWith('=') ? 1 : 0);
    return Math.floor(base64.length * 3 / 4) - padding;
  }

  function formatBytes(bytes) {
    if (!bytes || bytes === 0) return '0 B';
    if (bytes < 1024) return bytes + ' B';
    if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + ' KB';
    return (bytes / (1024 * 1024)).toFixed(2) + ' MB';
  }

  function updateSizes() {
    if (!img) return;
    var w = parseInt(widthInput.value) || origWidth;
    var h = parseInt(heightInput.value) || origHeight;
    var q = parseInt(qualitySlider.value) / 100;

    canvas.width  = w;
    canvas.height = h;
    ctx.clearRect(0, 0, w, h);
    ctx.drawImage(img, 0, 0, w, h);
    var outUrl  = canvas.toDataURL(fmt, q);
    var outBytes = estimateSize(outUrl);
    var origBytes = origFile ? origFile.size : 0;
    var saved = origBytes - outBytes;
    var pct = origBytes > 0 ? Math.round((saved / origBytes) * 100) : 0;

    origSizeEl.textContent = formatBytes(origBytes);
    origDimEl.textContent  = origWidth + ' x ' + origHeight + ' px';
    outSizeEl.textContent  = formatBytes(outBytes);
    outDimEl.textContent   = w + ' x ' + h + ' px';

    if (saved > 0) {
      savingsEl.textContent    = formatBytes(saved);
      savingsPctEl.textContent = pct + '% smaller';
    } else {
      savingsEl.textContent    = '+' + formatBytes(Math.abs(saved));
      savingsPctEl.textContent = Math.abs(pct) + '% larger';
      savingsEl.style.color    = '#059669';
    }
  }

  // --- Dimension inputs with aspect lock ---
  widthInput.addEventListener('input', function() {
    if (updatingDim || !locked || !img) return;
    var w = parseInt(widthInput.value);
    if (w > 0) {
      updatingDim = true;
      heightInput.value = Math.round(w / aspectRatio);
      updatingDim = false;
    }
    if (img) { renderPreview(); updateSizes(); }
  });

  heightInput.addEventListener('input', function() {
    if (updatingDim || !locked || !img) return;
    var h = parseInt(heightInput.value);
    if (h > 0) {
      updatingDim = true;
      widthInput.value = Math.round(h * aspectRatio);
      updatingDim = false;
    }
    if (img) { renderPreview(); updateSizes(); }
  });

  // --- Lock button ---
  lockBtn.addEventListener('click', function() {
    locked = !locked;
    lockBtn.textContent = locked ? '🔒' : '🔓';
    lockBtn.classList.toggle('locked', locked);
    if (locked && img) {
      aspectRatio = (parseInt(widthInput.value) || origWidth) / (parseInt(heightInput.value) || origHeight);
    }
  });

  // --- Preset buttons ---
  document.getElementById('ra-preset-grid').addEventListener('click', function(e) {
    var btn = e.target.closest('.ra-preset-btn');
    if (!btn) return;
    var w = parseInt(btn.getAttribute('data-w'));
    var h = parseInt(btn.getAttribute('data-h'));
    widthInput.value  = w;
    heightInput.value = h;
    aspectRatio = w / h;
    if (img) { renderPreview(); updateSizes(); }
  });

  // --- Quality slider ---
  qualitySlider.addEventListener('input', function() {
    qualityVal.textContent = qualitySlider.value + '%';
    if (img) { renderPreview(); updateSizes(); }
  });

  // --- Format buttons ---
  document.querySelectorAll('.ra-format-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      document.querySelectorAll('.ra-format-btn').forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      fmt = btn.getAttribute('data-fmt');
      if (img) { renderPreview(); updateSizes(); }
    });
  });

  // --- Download ---
  downloadBtn.addEventListener('click', function() {
    if (!img) return;
    var w = parseInt(widthInput.value) || origWidth;
    var h = parseInt(heightInput.value) || origHeight;
    var q = parseInt(qualitySlider.value) / 100;

    canvas.width  = w;
    canvas.height = h;
    ctx.clearRect(0, 0, w, h);
    ctx.drawImage(img, 0, 0, w, h);

    var ext = fmt === 'image/jpeg' ? 'jpg' : fmt === 'image/png' ? 'png' : 'webp';
    var dataUrl = canvas.toDataURL(fmt, q);

    var a = document.createElement('a');
    a.href = dataUrl;
    a.download = 'resized-' + w + 'x' + h + '.' + ext;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  });

})();
</script>

</div>

## How to Use This Image Resizer

**Step 1 — Upload**: Drag and drop your image onto the upload area, or click "Choose File". Supported formats include JPG, PNG, WebP, GIF, and BMP up to 20 MB.

**Step 2 — Set dimensions**: Enter a custom width and height in pixels. The lock icon keeps the aspect ratio intact — click it to unlock for freeform resizing. Or click a preset button to snap to a common size instantly.

**Step 3 — Choose format and quality**: Select JPEG, PNG, or WebP as the output format. Use the quality slider (10–100%) to balance file size against image clarity. PNG is lossless, so quality only affects JPEG and WebP.

**Step 4 — Check sizes**: The size panel shows the original file size, estimated output size, and how much space you save. The before/after preview lets you visually compare the result before downloading.

**Step 5 — Download**: Click "Download Resized Image" to save the result directly to your device.

## Choosing the Right Format

**JPEG** is best for photographs and complex images. It uses lossy compression, so quality settings below 80% may introduce visible artifacts. For web use, 75–85% gives a good balance.

**PNG** is ideal for screenshots, graphics with text, logos, and images with transparency. It is lossless — no quality degradation — but produces larger files than JPEG.

**WebP** is Google's modern format offering superior compression compared to both JPEG and PNG at equivalent quality. Supported by all major browsers, it is an excellent choice for web images.

## Social Media Image Sizes (2025)

| Platform | Recommended Size |
|---|---|
| Open Graph / Facebook | 1200 × 630 px |
| Instagram Square | 1080 × 1080 px |
| Instagram Story / Reel | 1080 × 1920 px |
| YouTube Thumbnail | 1280 × 720 px |
| Twitter / X Header | 1500 × 500 px |
| Profile / Avatar | 400 × 400 px |

All presets above are built into the tool — just click the button and resize in one step.

---

## Related Tools

> Pick colors for your image designs → [Color Picker](/tools/color-picker/)

> Generate a QR code to link to your image or portfolio → [QR Code Generator](/tools/qr-code-generator/)

> Check what screen resolution your visitors use → [Screen Resolution Checker](/tools/screen-resolution/)

## Related Articles

- [Best AI Image Generators Free 2026](/posts/best-ai-image-generators-free-2026/)
