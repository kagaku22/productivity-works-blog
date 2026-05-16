---
title: "Social Media Image Resizer"
date: 2025-05-16
description: "Free social media image resizer. Resize images for Instagram, Facebook, Twitter/X, LinkedIn, YouTube, and Pinterest. Crop and download optimized images instantly."
categories: ["Free Tools"]
tags: ["social media image resizer", "instagram image size", "facebook image size", "twitter image size", "image crop", "canvas crop"]
slug: "social-media-image-resizer"
cover:
  image: "/images/covers/social-media-image-resizer.png"
  alt: "Social Media Image Resizer"
ShowToc: false
---

<div id="sr-app">

<style>
#sr-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 0 48px 0;
  color: #1a202c;
}

#sr-app * {
  box-sizing: border-box;
}

/* Hero */
.sr-hero {
  background: linear-gradient(135deg, #7c3aed 0%, #5b21b6 50%, #4c1d95 100%);
  border-radius: 16px;
  padding: 32px 28px;
  margin-bottom: 24px;
  color: #fff;
}

.sr-hero h2 {
  margin: 0 0 6px 0;
  font-size: 24px;
  font-weight: 800;
}

.sr-hero p {
  margin: 0;
  font-size: 14px;
  opacity: 0.88;
  line-height: 1.6;
}

/* Upload area */
.sr-upload {
  border: 3px dashed #7c3aed;
  border-radius: 14px;
  padding: 40px 24px;
  text-align: center;
  background: #f5f3ff;
  cursor: pointer;
  transition: background 0.2s, border-color 0.2s;
  margin-bottom: 20px;
  position: relative;
}

.sr-upload:hover, .sr-upload.drag-over {
  background: #ede9fe;
  border-color: #5b21b6;
}

.sr-upload-icon {
  font-size: 48px;
  line-height: 1;
  margin-bottom: 10px;
  display: block;
}

.sr-upload-title {
  font-size: 17px;
  font-weight: 700;
  color: #4c1d95;
  margin-bottom: 4px;
}

.sr-upload-sub {
  font-size: 13px;
  color: #6b7280;
}

#sr-file-input {
  position: absolute;
  inset: 0;
  opacity: 0;
  cursor: pointer;
  width: 100%;
  height: 100%;
}

/* Platform tabs */
.sr-platforms {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 16px;
}

.sr-platform-btn {
  padding: 8px 14px;
  border-radius: 8px;
  border: 2px solid #e5e7eb;
  background: #fff;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
  color: #374151;
}

.sr-platform-btn:hover {
  border-color: #7c3aed;
  color: #7c3aed;
}

.sr-platform-btn.active {
  border-color: #7c3aed;
  background: #7c3aed;
  color: #fff;
}

/* Presets grid */
.sr-presets {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
  gap: 8px;
  margin-bottom: 20px;
}

.sr-preset-btn {
  padding: 10px 12px;
  border-radius: 10px;
  border: 2px solid #e5e7eb;
  background: #fff;
  cursor: pointer;
  text-align: left;
  transition: all 0.15s;
}

.sr-preset-btn:hover {
  border-color: #7c3aed;
  background: #f5f3ff;
}

.sr-preset-btn.active {
  border-color: #7c3aed;
  background: #ede9fe;
}

.sr-preset-name {
  font-size: 12px;
  font-weight: 700;
  color: #1a202c;
  display: block;
  margin-bottom: 2px;
}

.sr-preset-dim {
  font-size: 11px;
  color: #6b7280;
}

/* Controls row */
.sr-controls {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 20px;
}

@media (max-width: 540px) {
  .sr-controls { grid-template-columns: 1fr; }
}

.sr-control-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.sr-label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
}

.sr-select, .sr-color-input {
  padding: 8px 12px;
  border-radius: 8px;
  border: 2px solid #e5e7eb;
  font-size: 14px;
  background: #fff;
  color: #1a202c;
  transition: border-color 0.15s;
  width: 100%;
}

.sr-select:focus, .sr-color-input:focus {
  outline: none;
  border-color: #7c3aed;
}

.sr-color-row {
  display: flex;
  align-items: center;
  gap: 8px;
}

.sr-color-swatch {
  width: 36px;
  height: 36px;
  border-radius: 8px;
  border: 2px solid #e5e7eb;
  cursor: pointer;
  padding: 2px;
}

/* Canvas preview */
.sr-preview-wrap {
  margin-bottom: 20px;
  background: #f9fafb;
  border-radius: 14px;
  padding: 16px;
  display: none;
}

.sr-preview-wrap.visible { display: block; }

.sr-preview-label {
  font-size: 13px;
  font-weight: 600;
  color: #6b7280;
  margin-bottom: 10px;
}

.sr-canvas-container {
  position: relative;
  display: inline-block;
  cursor: move;
  border-radius: 8px;
  overflow: hidden;
  max-width: 100%;
  border: 2px solid #e5e7eb;
  background: #fff;
  touch-action: none;
}

#sr-canvas {
  display: block;
  max-width: 100%;
  height: auto;
}

/* Info bar */
.sr-info-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  margin-bottom: 20px;
  font-size: 13px;
  color: #6b7280;
}

.sr-info-badge {
  background: #f3f4f6;
  border-radius: 6px;
  padding: 4px 10px;
  font-weight: 600;
  color: #374151;
}

/* Download buttons */
.sr-dl-row {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: center;
}

.sr-dl-btn {
  padding: 12px 24px;
  border-radius: 10px;
  border: none;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.15s;
  display: inline-flex;
  align-items: center;
  gap: 6px;
}

.sr-dl-btn.primary {
  background: #7c3aed;
  color: #fff;
}

.sr-dl-btn.primary:hover {
  background: #5b21b6;
}

.sr-dl-btn.primary:disabled {
  background: #c4b5fd;
  cursor: not-allowed;
}

.sr-dl-btn.secondary {
  background: #f3f4f6;
  color: #374151;
  font-size: 13px;
  padding: 10px 16px;
}

.sr-dl-btn.secondary:hover {
  background: #e5e7eb;
}

.sr-fmt-toggle {
  display: flex;
  gap: 6px;
  margin-left: auto;
}

.sr-fmt-btn {
  padding: 8px 14px;
  border-radius: 8px;
  border: 2px solid #e5e7eb;
  background: #fff;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  color: #374151;
  transition: all 0.15s;
}

.sr-fmt-btn.active {
  border-color: #7c3aed;
  background: #7c3aed;
  color: #fff;
}

/* Section heading */
.sr-section-title {
  font-size: 14px;
  font-weight: 700;
  color: #374151;
  margin: 0 0 10px 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* Hint */
.sr-hint {
  font-size: 12px;
  color: #9ca3af;
  margin-top: 8px;
  line-height: 1.5;
}

/* Drag hint overlay */
.sr-drag-hint {
  position: absolute;
  bottom: 8px;
  right: 8px;
  background: rgba(0,0,0,0.55);
  color: #fff;
  font-size: 11px;
  padding: 3px 8px;
  border-radius: 6px;
  pointer-events: none;
}
</style>

<div class="sr-hero">
  <h2>Social Media Image Resizer</h2>
  <p>Resize and crop images for any platform — Instagram, Facebook, Twitter/X, LinkedIn, YouTube, Pinterest. Pick a preset, drag to reposition, and download. No upload to servers. All processing happens in your browser.</p>
</div>

<!-- Upload -->
<div class="sr-upload" id="sr-upload-zone">
  <input type="file" id="sr-file-input" accept="image/*">
  <span class="sr-upload-icon">🖼️</span>
  <div class="sr-upload-title">Drop an image here or click to upload</div>
  <div class="sr-upload-sub">JPG, PNG, WebP, GIF, BMP — up to 30 MB</div>
</div>

<!-- Platform selector -->
<p class="sr-section-title">Platform</p>
<div class="sr-platforms" id="sr-platforms">
  <button class="sr-platform-btn active" data-platform="instagram">Instagram</button>
  <button class="sr-platform-btn" data-platform="facebook">Facebook</button>
  <button class="sr-platform-btn" data-platform="twitter">Twitter / X</button>
  <button class="sr-platform-btn" data-platform="linkedin">LinkedIn</button>
  <button class="sr-platform-btn" data-platform="youtube">YouTube</button>
  <button class="sr-platform-btn" data-platform="pinterest">Pinterest</button>
</div>

<!-- Preset grid -->
<div class="sr-presets" id="sr-preset-grid"></div>

<!-- Controls -->
<div class="sr-controls">
  <div class="sr-control-group">
    <label class="sr-label" for="sr-fit-mode">Fit Mode</label>
    <select class="sr-select" id="sr-fit-mode">
      <option value="cover">Cover (crop to fill)</option>
      <option value="contain">Contain (letterbox)</option>
      <option value="stretch">Stretch (distort)</option>
    </select>
    <span class="sr-hint">Cover crops the image to exactly fill the frame. Contain adds padding bars. Stretch distorts to fit.</span>
  </div>
  <div class="sr-control-group">
    <label class="sr-label">Background Color (for Contain mode)</label>
    <div class="sr-color-row">
      <input type="color" class="sr-color-swatch" id="sr-bg-color" value="#ffffff">
      <input type="text" class="sr-select" id="sr-bg-hex" value="#ffffff" maxlength="7" placeholder="#ffffff">
    </div>
    <span class="sr-hint">Used only when Contain mode leaves empty areas.</span>
  </div>
</div>

<!-- Preview -->
<div class="sr-preview-wrap" id="sr-preview-wrap">
  <div class="sr-preview-label" id="sr-preview-label">Preview — drag to reposition</div>
  <div class="sr-canvas-container" id="sr-canvas-container">
    <canvas id="sr-canvas"></canvas>
    <span class="sr-drag-hint">drag to reposition</span>
  </div>
</div>

<!-- Info bar -->
<div class="sr-info-bar" id="sr-info-bar" style="display:none;">
  <span id="sr-info-dim" class="sr-info-badge">—</span>
  <span id="sr-info-size" class="sr-info-badge">— KB</span>
  <span id="sr-info-orig" style="margin-left:auto; font-size:12px;"></span>
</div>

<!-- Download row -->
<div class="sr-dl-row">
  <button class="sr-dl-btn primary" id="sr-dl-btn" disabled>⬇ Download Image</button>
  <div class="sr-fmt-toggle">
    <button class="sr-fmt-btn active" data-fmt="image/png">PNG</button>
    <button class="sr-fmt-btn" data-fmt="image/jpeg">JPEG</button>
  </div>
</div>

<script>
(function() {
  'use strict';

  var PRESETS = {
    instagram: [
      { name: 'Post',    w: 1080, h: 1080 },
      { name: 'Story',   w: 1080, h: 1920 },
      { name: 'Reel',    w: 1080, h: 1920 },
      { name: 'Profile', w: 320,  h: 320  }
    ],
    facebook: [
      { name: 'Post',    w: 1200, h: 630  },
      { name: 'Cover',   w: 820,  h: 312  },
      { name: 'Profile', w: 170,  h: 170  },
      { name: 'Story',   w: 1080, h: 1920 }
    ],
    twitter: [
      { name: 'Post',    w: 1600, h: 900  },
      { name: 'Header',  w: 1500, h: 500  },
      { name: 'Profile', w: 400,  h: 400  }
    ],
    linkedin: [
      { name: 'Post',    w: 1200, h: 627  },
      { name: 'Cover',   w: 1584, h: 396  },
      { name: 'Profile', w: 400,  h: 400  }
    ],
    youtube: [
      { name: 'Thumbnail',    w: 1280, h: 720  },
      { name: 'Channel Art',  w: 2560, h: 1440 }
    ],
    pinterest: [
      { name: 'Pin', w: 1000, h: 1500 }
    ]
  };

  var state = {
    img: null,
    origW: 0,
    origH: 0,
    platform: 'instagram',
    preset: PRESETS['instagram'][0],
    fitMode: 'cover',
    bgColor: '#ffffff',
    fmt: 'image/png',
    // drag offset in image pixels (for cover mode)
    offsetX: 0,
    offsetY: 0,
    dragging: false,
    dragStartX: 0,
    dragStartY: 0,
    dragOffsetStartX: 0,
    dragOffsetStartY: 0
  };

  var canvas = document.getElementById('sr-canvas');
  var ctx = canvas.getContext('2d');
  var previewWrap = document.getElementById('sr-preview-wrap');
  var previewLabel = document.getElementById('sr-preview-label');
  var infoBar = document.getElementById('sr-info-bar');
  var infoSize = document.getElementById('sr-info-size');
  var infoDim = document.getElementById('sr-info-dim');
  var infoOrig = document.getElementById('sr-info-orig');
  var dlBtn = document.getElementById('sr-dl-btn');
  var fitSel = document.getElementById('sr-fit-mode');
  var bgColorPicker = document.getElementById('sr-bg-color');
  var bgHexInput = document.getElementById('sr-bg-hex');
  var container = document.getElementById('sr-canvas-container');

  // Build preset grid
  function buildPresets() {
    var grid = document.getElementById('sr-preset-grid');
    grid.innerHTML = '';
    var list = PRESETS[state.platform];
    list.forEach(function(p, i) {
      var btn = document.createElement('button');
      btn.className = 'sr-preset-btn' + (i === 0 ? ' active' : '');
      btn.innerHTML = '<span class="sr-preset-name">' + p.name + '</span><span class="sr-preset-dim">' + p.w + ' × ' + p.h + '</span>';
      btn.addEventListener('click', function() {
        document.querySelectorAll('.sr-preset-btn').forEach(function(b) { b.classList.remove('active'); });
        btn.classList.add('active');
        state.preset = p;
        state.offsetX = 0;
        state.offsetY = 0;
        render();
      });
      grid.appendChild(btn);
    });
    state.preset = list[0];
  }

  // Render onto canvas
  function render() {
    if (!state.img) return;
    var tw = state.preset.w;
    var th = state.preset.h;
    canvas.width = tw;
    canvas.height = th;

    var scaleX = tw / state.origW;
    var scaleY = th / state.origH;

    ctx.fillStyle = state.bgColor;
    ctx.fillRect(0, 0, tw, th);

    if (state.fitMode === 'stretch') {
      ctx.drawImage(state.img, 0, 0, tw, th);
    } else if (state.fitMode === 'contain') {
      var scale = Math.min(scaleX, scaleY);
      var dw = state.origW * scale;
      var dh = state.origH * scale;
      var dx = (tw - dw) / 2;
      var dy = (th - dh) / 2;
      ctx.drawImage(state.img, dx, dy, dw, dh);
    } else {
      // cover: crop
      var scale = Math.max(scaleX, scaleY);
      var dw = state.origW * scale;
      var dh = state.origH * scale;
      // offset is in output pixels, clamped
      var maxOx = (dw - tw) / 2;
      var maxOy = (dh - th) / 2;
      var ox = Math.max(-maxOx, Math.min(maxOx, state.offsetX));
      var oy = Math.max(-maxOy, Math.min(maxOy, state.offsetY));
      state.offsetX = ox;
      state.offsetY = oy;
      ctx.drawImage(state.img, (tw - dw) / 2 + ox, (th - dh) / 2 + oy, dw, dh);
    }

    updateInfo();
    previewWrap.classList.add('visible');
    infoBar.style.display = 'flex';
    dlBtn.disabled = false;

    // update preview label
    previewLabel.textContent = 'Preview — ' + tw + ' × ' + th + (state.fitMode === 'cover' ? ' (drag to reposition)' : '');
  }

  function estimateSize() {
    var dataUrl = canvas.toDataURL(state.fmt, 0.9);
    var base64 = dataUrl.split(',')[1] || '';
    return Math.round(base64.length * 0.75 / 1024);
  }

  function updateInfo() {
    var p = state.preset;
    infoDim.textContent = p.w + ' × ' + p.h + ' px';
    var kb = estimateSize();
    infoSize.textContent = kb >= 1024 ? (kb / 1024).toFixed(1) + ' MB (est.)' : kb + ' KB (est.)';
    infoOrig.textContent = 'Original: ' + state.origW + ' × ' + state.origH + ' px';
  }

  // File input
  var uploadZone = document.getElementById('sr-upload-zone');
  var fileInput = document.getElementById('sr-file-input');

  function loadFile(file) {
    if (!file || !file.type.startsWith('image/')) return;
    var reader = new FileReader();
    reader.onload = function(e) {
      var img = new Image();
      img.onload = function() {
        state.img = img;
        state.origW = img.naturalWidth;
        state.origH = img.naturalHeight;
        state.offsetX = 0;
        state.offsetY = 0;
        render();
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }

  fileInput.addEventListener('change', function() {
    if (fileInput.files[0]) loadFile(fileInput.files[0]);
  });

  uploadZone.addEventListener('dragover', function(e) {
    e.preventDefault();
    uploadZone.classList.add('drag-over');
  });
  uploadZone.addEventListener('dragleave', function() {
    uploadZone.classList.remove('drag-over');
  });
  uploadZone.addEventListener('drop', function(e) {
    e.preventDefault();
    uploadZone.classList.remove('drag-over');
    if (e.dataTransfer.files[0]) loadFile(e.dataTransfer.files[0]);
  });

  // Platform tabs
  document.getElementById('sr-platforms').addEventListener('click', function(e) {
    var btn = e.target.closest('.sr-platform-btn');
    if (!btn) return;
    document.querySelectorAll('.sr-platform-btn').forEach(function(b) { b.classList.remove('active'); });
    btn.classList.add('active');
    state.platform = btn.getAttribute('data-platform');
    state.offsetX = 0;
    state.offsetY = 0;
    buildPresets();
    render();
  });

  // Fit mode
  fitSel.addEventListener('change', function() {
    state.fitMode = fitSel.value;
    state.offsetX = 0;
    state.offsetY = 0;
    render();
  });

  // Background color
  bgColorPicker.addEventListener('input', function() {
    state.bgColor = bgColorPicker.value;
    bgHexInput.value = bgColorPicker.value;
    render();
  });

  bgHexInput.addEventListener('input', function() {
    var val = bgHexInput.value.trim();
    if (/^#[0-9a-fA-F]{6}$/.test(val)) {
      state.bgColor = val;
      bgColorPicker.value = val;
      render();
    }
  });

  // Format toggle
  document.querySelectorAll('.sr-fmt-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      document.querySelectorAll('.sr-fmt-btn').forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      state.fmt = btn.getAttribute('data-fmt');
      if (state.img) updateInfo();
    });
  });

  // Drag to reposition (cover mode)
  function getPos(e) {
    var src = e.touches ? e.touches[0] : e;
    return { x: src.clientX, y: src.clientY };
  }

  function onDragStart(e) {
    if (state.fitMode !== 'cover' || !state.img) return;
    e.preventDefault();
    state.dragging = true;
    var pos = getPos(e);
    state.dragStartX = pos.x;
    state.dragStartY = pos.y;
    state.dragOffsetStartX = state.offsetX;
    state.dragOffsetStartY = state.offsetY;
  }

  function onDragMove(e) {
    if (!state.dragging) return;
    e.preventDefault();
    var pos = getPos(e);
    var dx = pos.x - state.dragStartX;
    var dy = pos.y - state.dragStartY;
    // canvas is displayed at reduced size; compute scale factor
    var displayW = canvas.offsetWidth || canvas.width;
    var canvasW = canvas.width || 1;
    var scaleFactor = canvasW / displayW;
    state.offsetX = state.dragOffsetStartX + dx * scaleFactor;
    state.offsetY = state.dragOffsetStartY + dy * scaleFactor;
    render();
  }

  function onDragEnd() {
    state.dragging = false;
  }

  container.addEventListener('mousedown', onDragStart);
  window.addEventListener('mousemove', onDragMove);
  window.addEventListener('mouseup', onDragEnd);
  container.addEventListener('touchstart', onDragStart, { passive: false });
  window.addEventListener('touchmove', onDragMove, { passive: false });
  window.addEventListener('touchend', onDragEnd);

  // Download
  dlBtn.addEventListener('click', function() {
    if (!state.img) return;
    // render at full resolution
    var tw = state.preset.w;
    var th = state.preset.h;
    var offscreen = document.createElement('canvas');
    offscreen.width = tw;
    offscreen.height = th;
    var octx = offscreen.getContext('2d');
    octx.fillStyle = state.bgColor;
    octx.fillRect(0, 0, tw, th);

    var scaleX = tw / state.origW;
    var scaleY = th / state.origH;

    if (state.fitMode === 'stretch') {
      octx.drawImage(state.img, 0, 0, tw, th);
    } else if (state.fitMode === 'contain') {
      var scale = Math.min(scaleX, scaleY);
      var dw = state.origW * scale;
      var dh = state.origH * scale;
      var dx = (tw - dw) / 2;
      var dy = (th - dh) / 2;
      octx.drawImage(state.img, dx, dy, dw, dh);
    } else {
      var scale = Math.max(scaleX, scaleY);
      var dw = state.origW * scale;
      var dh = state.origH * scale;
      var maxOx = (dw - tw) / 2;
      var maxOy = (dh - th) / 2;
      var ox = Math.max(-maxOx, Math.min(maxOx, state.offsetX));
      var oy = Math.max(-maxOy, Math.min(maxOy, state.offsetY));
      octx.drawImage(state.img, (tw - dw) / 2 + ox, (th - dh) / 2 + oy, dw, dh);
    }

    var q = state.fmt === 'image/png' ? 1.0 : 0.92;
    var ext = state.fmt === 'image/png' ? 'png' : 'jpg';
    var dataUrl = offscreen.toDataURL(state.fmt, q);
    var a = document.createElement('a');
    a.href = dataUrl;
    a.download = state.platform + '-' + state.preset.name.toLowerCase().replace(/\s+/g, '-') + '-' + tw + 'x' + th + '.' + ext;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  });

  // Init
  buildPresets();

})();
</script>

</div>

## How to Use

**STEP 1 — Upload your image**: Drag and drop any image onto the upload area, or click to browse. JPG, PNG, WebP, GIF, and BMP up to 30 MB are supported.

**STEP 2 — Choose a platform**: Click a platform tab (Instagram, Facebook, Twitter/X, LinkedIn, YouTube, Pinterest) and then select the specific format from the preset grid.

**STEP 3 — Pick a fit mode**: Cover crops the image to fill the frame exactly — drag the preview to reposition. Contain adds letterbox bars using your chosen background color. Stretch distorts the image to fill the frame.

**STEP 4 — Adjust background color**: In Contain mode, select the bar color using the color picker or by typing a hex value.

**STEP 5 — Download**: Choose PNG or JPEG, then click Download Image. The file is named automatically with the platform, format name, and dimensions.

## Platform Image Size Reference (2025)

| Platform | Format | Size |
|---|---|---|
| Instagram | Post | 1080 × 1080 |
| Instagram | Story / Reel | 1080 × 1920 |
| Instagram | Profile | 320 × 320 |
| Facebook | Post | 1200 × 630 |
| Facebook | Cover | 820 × 312 |
| Facebook | Story | 1080 × 1920 |
| Twitter / X | Post | 1600 × 900 |
| Twitter / X | Header | 1500 × 500 |
| LinkedIn | Post | 1200 × 627 |
| LinkedIn | Cover | 1584 × 396 |
| YouTube | Thumbnail | 1280 × 720 |
| YouTube | Channel Art | 2560 × 1440 |
| Pinterest | Pin | 1000 × 1500 |

## Fit Mode Explained

**Cover** scales the image up so that both dimensions meet or exceed the target size, then crops the overflow. You can drag the preview to control which part is kept. This is the best choice for most social media images.

**Contain** scales the image down so it fits entirely within the target frame, adding bars (in your chosen background color) to fill the remaining space. Use this when you need the full image visible with no cropping.

**Stretch** forces the image to exactly match the target dimensions, which may distort the proportions. Useful when your source image is already close in shape to the target.

---

## Related Tools

> Resize images to any custom dimension → [Image Resizer](/tools/image-resizer/)

> Generate placeholder images at exact sizes → [Placeholder Image Generator](/tools/placeholder-image/)
