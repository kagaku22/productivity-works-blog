---
title: "Meme Generator - Custom Meme Maker"
date: 2025-05-16
description: "Free online meme generator. Upload any image, add top and bottom text with classic meme font styling. Customize font size, color, and stroke. Download as PNG."
categories: ["Free Tools"]
tags: ["meme generator", "meme maker", "custom meme", "image text overlay", "canvas tool"]
slug: "meme-generator"
cover:
  image: "/images/covers/meme-generator.png"
  alt: "Meme Generator"
ShowToc: false
---

<div id="mg-app">

<style>
#mg-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 0 48px 0;
  color: #1a202c;
}

#mg-app * {
  box-sizing: border-box;
}

/* Hero */
.mg-hero {
  background: linear-gradient(135deg, #7c3aed 0%, #5b21b6 50%, #4c1d95 100%);
  border-radius: 16px;
  padding: 32px 28px;
  margin-bottom: 24px;
  color: #fff;
}

.mg-hero h2 {
  margin: 0 0 6px 0;
  font-size: 22px;
  font-weight: 800;
}

.mg-hero p {
  margin: 0;
  font-size: 14px;
  opacity: 0.88;
  line-height: 1.7;
}

/* Drop Zone */
.mg-dropzone {
  border: 3px dashed #7c3aed;
  border-radius: 14px;
  padding: 44px 24px;
  text-align: center;
  background: #f5f3ff;
  cursor: pointer;
  transition: background 0.2s, border-color 0.2s;
  margin-bottom: 20px;
}

.mg-dropzone.drag-over {
  background: #ede9fe;
  border-color: #5b21b6;
}

.mg-dropzone-icon {
  font-size: 48px;
  line-height: 1;
  margin-bottom: 12px;
  display: block;
}

.mg-dropzone-title {
  font-size: 17px;
  font-weight: 700;
  color: #4c1d95;
  margin-bottom: 6px;
}

.mg-dropzone-sub {
  font-size: 13px;
  color: #6b7280;
  margin-bottom: 16px;
}

.mg-browse-btn {
  display: inline-block;
  padding: 10px 24px;
  background: #7c3aed;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}

.mg-browse-btn:hover {
  background: #5b21b6;
}

#mg-file-input {
  display: none;
}

/* Card */
.mg-card {
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 2px 16px rgba(0,0,0,0.08);
  padding: 22px 24px;
  margin-bottom: 18px;
}

.mg-card h3 {
  margin: 0 0 18px 0;
  font-size: 13px;
  font-weight: 700;
  color: #374151;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  border-bottom: 2px solid #f5f3ff;
  padding-bottom: 10px;
}

/* Canvas wrapper */
.mg-canvas-wrap {
  width: 100%;
  overflow: hidden;
  border-radius: 10px;
  background: repeating-conic-gradient(#e5e7eb 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
  border: 1px solid #e5e7eb;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 200px;
}

#mg-canvas {
  max-width: 100%;
  max-height: 500px;
  display: block;
  object-fit: contain;
}

/* Text inputs */
.mg-input-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
  margin-bottom: 14px;
}

.mg-input-group label {
  font-size: 12px;
  font-weight: 700;
  color: #374151;
  letter-spacing: 0.02em;
}

.mg-text-input {
  padding: 10px 14px;
  border: 2px solid #e9d5ff;
  border-radius: 8px;
  font-size: 15px;
  color: #1a202c;
  transition: border-color 0.2s;
  width: 100%;
}

.mg-text-input:focus {
  outline: none;
  border-color: #7c3aed;
}

/* Controls row */
.mg-controls-row {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  align-items: flex-start;
}

.mg-control-group {
  flex: 1;
  min-width: 140px;
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.mg-control-group label {
  font-size: 12px;
  font-weight: 700;
  color: #374151;
  letter-spacing: 0.02em;
}

.mg-control-input {
  padding: 8px 12px;
  border: 2px solid #e9d5ff;
  border-radius: 8px;
  font-size: 14px;
  color: #1a202c;
  width: 100%;
  transition: border-color 0.2s;
}

.mg-control-input:focus {
  outline: none;
  border-color: #7c3aed;
}

/* Color picker inline */
.mg-color-wrap {
  display: flex;
  align-items: center;
  gap: 8px;
}

.mg-color-swatch {
  width: 36px;
  height: 36px;
  border-radius: 6px;
  border: 2px solid #e9d5ff;
  padding: 2px;
  cursor: pointer;
  background: none;
}

.mg-color-label-val {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  font-family: monospace;
}

/* Alignment buttons */
.mg-align-btns {
  display: flex;
  gap: 8px;
}

.mg-align-btn {
  flex: 1;
  padding: 8px 10px;
  border: 2px solid #e9d5ff;
  border-radius: 8px;
  background: #fff;
  font-size: 16px;
  cursor: pointer;
  transition: all 0.18s;
  text-align: center;
}

.mg-align-btn:hover {
  border-color: #7c3aed;
  background: #f5f3ff;
}

.mg-align-btn.active {
  border-color: #7c3aed;
  background: #7c3aed;
  color: #fff;
}

/* Slider */
.mg-slider-wrap {
  display: flex;
  align-items: center;
  gap: 10px;
}

.mg-slider {
  flex: 1;
  height: 6px;
  border-radius: 3px;
  background: linear-gradient(to right, #e9d5ff, #7c3aed);
  -webkit-appearance: none;
  appearance: none;
  outline: none;
  cursor: pointer;
}

.mg-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid #7c3aed;
  box-shadow: 0 1px 4px rgba(0,0,0,0.15);
  cursor: pointer;
}

.mg-slider::-moz-range-thumb {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid #7c3aed;
  box-shadow: 0 1px 4px rgba(0,0,0,0.15);
  cursor: pointer;
}

.mg-slider-val {
  font-size: 14px;
  font-weight: 700;
  color: #7c3aed;
  min-width: 36px;
  text-align: right;
}

/* Action buttons */
.mg-actions {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.mg-download-btn {
  flex: 1;
  min-width: 160px;
  padding: 14px 24px;
  background: linear-gradient(135deg, #7c3aed, #5b21b6);
  color: #fff;
  border: none;
  border-radius: 12px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.1s;
  text-align: center;
}

.mg-download-btn:hover:not(:disabled) { opacity: 0.92; }
.mg-download-btn:active:not(:disabled) { transform: scale(0.98); }
.mg-download-btn:disabled { background: #9ca3af; cursor: not-allowed; }

.mg-reset-btn {
  padding: 14px 24px;
  background: #fff;
  color: #7c3aed;
  border: 2px solid #7c3aed;
  border-radius: 12px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.18s;
}

.mg-reset-btn:hover {
  background: #f5f3ff;
}

/* Placeholder */
.mg-placeholder {
  text-align: center;
  padding: 32px 16px;
  color: #9ca3af;
  font-size: 14px;
}

.mg-placeholder-icon {
  font-size: 40px;
  display: block;
  margin-bottom: 8px;
}

/* Responsive */
@media (max-width: 600px) {
  .mg-hero { padding: 22px 16px; }
  .mg-hero h2 { font-size: 18px; }
  .mg-card { padding: 16px 14px; }
  .mg-controls-row { gap: 10px; }
  .mg-actions { flex-direction: column; }
  .mg-reset-btn { width: 100%; text-align: center; }
}
</style>

<!-- Hero -->
<div class="mg-hero">
  <h2>Free Meme Generator</h2>
  <p>Upload any image, add top and bottom text in classic meme style. Customize font, color, and outline. All processing happens in your browser — no uploads, no sign-up.</p>
</div>

<!-- Drop Zone -->
<div class="mg-dropzone" id="mg-dropzone">
  <span class="mg-dropzone-icon">🖼️</span>
  <div class="mg-dropzone-title">Drag & drop an image here</div>
  <div class="mg-dropzone-sub">JPG, PNG, GIF, WebP — up to 20 MB</div>
  <button class="mg-browse-btn" onclick="document.getElementById('mg-file-input').click()">Choose File</button>
  <input type="file" id="mg-file-input" accept="image/*">
</div>

<!-- Canvas Preview -->
<div class="mg-card">
  <h3>Preview</h3>
  <div class="mg-canvas-wrap" id="mg-canvas-wrap">
    <div class="mg-placeholder" id="mg-placeholder">
      <span class="mg-placeholder-icon">🎭</span>
      Upload an image to start creating your meme
    </div>
    <canvas id="mg-canvas" style="display:none;"></canvas>
  </div>
</div>

<!-- Text Inputs -->
<div class="mg-card">
  <h3>Meme Text</h3>
  <div class="mg-input-group">
    <label for="mg-top-text">Top Text</label>
    <input type="text" class="mg-text-input" id="mg-top-text" placeholder="TOP TEXT" maxlength="120">
  </div>
  <div class="mg-input-group">
    <label for="mg-bottom-text">Bottom Text</label>
    <input type="text" class="mg-text-input" id="mg-bottom-text" placeholder="BOTTOM TEXT" maxlength="120">
  </div>
</div>

<!-- Style Controls -->
<div class="mg-card">
  <h3>Style</h3>
  <div class="mg-controls-row">
    <div class="mg-control-group">
      <label for="mg-font-size">Font Size</label>
      <div class="mg-slider-wrap">
        <input type="range" class="mg-slider" id="mg-font-size" min="16" max="120" value="52">
        <span class="mg-slider-val" id="mg-font-size-val">52px</span>
      </div>
    </div>
    <div class="mg-control-group">
      <label for="mg-outline-width">Outline Width</label>
      <div class="mg-slider-wrap">
        <input type="range" class="mg-slider" id="mg-outline-width" min="0" max="20" value="4">
        <span class="mg-slider-val" id="mg-outline-width-val">4px</span>
      </div>
    </div>
  </div>
  <div class="mg-controls-row" style="margin-top:14px;">
    <div class="mg-control-group">
      <label>Text Color</label>
      <div class="mg-color-wrap">
        <input type="color" class="mg-color-swatch" id="mg-text-color" value="#ffffff">
        <span class="mg-color-label-val" id="mg-text-color-val">#ffffff</span>
      </div>
    </div>
    <div class="mg-control-group">
      <label>Outline Color</label>
      <div class="mg-color-wrap">
        <input type="color" class="mg-color-swatch" id="mg-outline-color" value="#000000">
        <span class="mg-color-label-val" id="mg-outline-color-val">#000000</span>
      </div>
    </div>
    <div class="mg-control-group">
      <label>Alignment</label>
      <div class="mg-align-btns">
        <button class="mg-align-btn" data-align="left" title="Left">&#9664;</button>
        <button class="mg-align-btn active" data-align="center" title="Center">&#9632;</button>
        <button class="mg-align-btn" data-align="right" title="Right">&#9654;</button>
      </div>
    </div>
  </div>
</div>

<!-- Actions -->
<div class="mg-card">
  <div class="mg-actions">
    <button class="mg-download-btn" id="mg-download-btn" disabled>Download as PNG</button>
    <button class="mg-reset-btn" id="mg-reset-btn">Reset</button>
  </div>
</div>

<script>
(function() {
  var img = null;
  var alignment = 'center';

  var dropzone     = document.getElementById('mg-dropzone');
  var fileInput    = document.getElementById('mg-file-input');
  var canvas       = document.getElementById('mg-canvas');
  var placeholder  = document.getElementById('mg-placeholder');
  var ctx          = canvas.getContext('2d');
  var topTextEl    = document.getElementById('mg-top-text');
  var botTextEl    = document.getElementById('mg-bottom-text');
  var fontSizeEl   = document.getElementById('mg-font-size');
  var fontSizeVal  = document.getElementById('mg-font-size-val');
  var outlineWEl   = document.getElementById('mg-outline-width');
  var outlineWVal  = document.getElementById('mg-outline-width-val');
  var textColorEl  = document.getElementById('mg-text-color');
  var textColorVal = document.getElementById('mg-text-color-val');
  var outColorEl   = document.getElementById('mg-outline-color');
  var outColorVal  = document.getElementById('mg-outline-color-val');
  var downloadBtn  = document.getElementById('mg-download-btn');
  var resetBtn     = document.getElementById('mg-reset-btn');

  // Drag & Drop
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

  function loadFile(file) {
    if (file.size > 20 * 1024 * 1024) {
      alert('File too large. Please use an image under 20 MB.');
      return;
    }
    var reader = new FileReader();
    reader.onload = function(e) {
      var newImg = new Image();
      newImg.onload = function() {
        img = newImg;
        canvas.width  = img.naturalWidth;
        canvas.height = img.naturalHeight;
        placeholder.style.display = 'none';
        canvas.style.display = 'block';
        drawMeme();
        downloadBtn.disabled = false;
      };
      newImg.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }

  function drawMeme() {
    if (!img) return;

    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.drawImage(img, 0, 0);

    var fontSize    = parseInt(fontSizeEl.value);
    var outlineW    = parseInt(outlineWEl.value);
    var textColor   = textColorEl.value;
    var outlineColor= outColorEl.value;
    var topText     = topTextEl.value.toUpperCase();
    var botText     = botTextEl.value.toUpperCase();

    var cw = canvas.width;
    var ch = canvas.height;
    var padding = Math.round(cw * 0.04);

    ctx.font         = 'bold ' + fontSize + 'px Impact, Arial Black, sans-serif';
    ctx.textBaseline = 'top';
    ctx.lineJoin     = 'round';
    ctx.miterLimit   = 2;

    var xPos;
    if (alignment === 'left')        { ctx.textAlign = 'left';   xPos = padding; }
    else if (alignment === 'right')  { ctx.textAlign = 'right';  xPos = cw - padding; }
    else                             { ctx.textAlign = 'center'; xPos = cw / 2; }

    // Top text
    if (topText) {
      var topLines = wrapText(ctx, topText, cw - padding * 2, fontSize);
      topLines.forEach(function(line, i) {
        var y = padding + i * (fontSize + 4);
        if (outlineW > 0) {
          ctx.strokeStyle = outlineColor;
          ctx.lineWidth   = outlineW * 2;
          ctx.strokeText(line, xPos, y);
        }
        ctx.fillStyle = textColor;
        ctx.fillText(line, xPos, y);
      });
    }

    // Bottom text
    if (botText) {
      ctx.textBaseline = 'bottom';
      var botLines = wrapText(ctx, botText, cw - padding * 2, fontSize);
      botLines.reverse();
      botLines.forEach(function(line, i) {
        var y = ch - padding - i * (fontSize + 4);
        if (outlineW > 0) {
          ctx.strokeStyle = outlineColor;
          ctx.lineWidth   = outlineW * 2;
          ctx.strokeText(line, xPos, y);
        }
        ctx.fillStyle = textColor;
        ctx.fillText(line, xPos, y);
      });
    }
  }

  function wrapText(ctx, text, maxWidth, lineHeight) {
    var words = text.split(' ');
    var lines  = [];
    var current = '';

    for (var i = 0; i < words.length; i++) {
      var test = current ? current + ' ' + words[i] : words[i];
      if (ctx.measureText(test).width > maxWidth && current) {
        lines.push(current);
        current = words[i];
      } else {
        current = test;
      }
    }
    if (current) lines.push(current);
    return lines;
  }

  // Live update listeners
  [topTextEl, botTextEl].forEach(function(el) {
    el.addEventListener('input', drawMeme);
  });

  fontSizeEl.addEventListener('input', function() {
    fontSizeVal.textContent = fontSizeEl.value + 'px';
    drawMeme();
  });

  outlineWEl.addEventListener('input', function() {
    outlineWVal.textContent = outlineWEl.value + 'px';
    drawMeme();
  });

  textColorEl.addEventListener('input', function() {
    textColorVal.textContent = textColorEl.value;
    drawMeme();
  });

  outColorEl.addEventListener('input', function() {
    outColorVal.textContent = outColorEl.value;
    drawMeme();
  });

  document.querySelectorAll('.mg-align-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      document.querySelectorAll('.mg-align-btn').forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      alignment = btn.getAttribute('data-align');
      drawMeme();
    });
  });

  // Download
  downloadBtn.addEventListener('click', function() {
    if (!img) return;
    var a = document.createElement('a');
    a.href = canvas.toDataURL('image/png');
    a.download = 'meme.png';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  });

  // Reset
  resetBtn.addEventListener('click', function() {
    img = null;
    canvas.style.display = 'none';
    placeholder.style.display = '';
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    topTextEl.value = '';
    botTextEl.value = '';
    fontSizeEl.value = 52;
    fontSizeVal.textContent = '52px';
    outlineWEl.value = 4;
    outlineWVal.textContent = '4px';
    textColorEl.value = '#ffffff';
    textColorVal.textContent = '#ffffff';
    outColorEl.value = '#000000';
    outColorVal.textContent = '#000000';
    alignment = 'center';
    document.querySelectorAll('.mg-align-btn').forEach(function(b) { b.classList.remove('active'); });
    document.querySelector('.mg-align-btn[data-align="center"]').classList.add('active');
    downloadBtn.disabled = true;
    fileInput.value = '';
  });

})();
</script>

</div>

## How to Use

**STEP 1 — Upload an image**: Drag and drop any image onto the drop zone, or click "Choose File." JPG, PNG, GIF, and WebP files up to 20 MB are supported.

**STEP 2 — Add text**: Type your top and bottom text. Text is automatically uppercased to match classic meme style. It wraps automatically if it's too long to fit.

**STEP 3 — Customize style**: Adjust font size (16–120 px), text color, outline color, and outline width. Classic meme style uses white text with a black outline — the defaults reflect this.

**STEP 4 — Choose alignment**: Toggle between left, center (default), and right alignment for both text blocks.

**STEP 5 — Download**: Click "Download as PNG" to save your meme. The canvas renders at full original image resolution.

## Tips for Great Memes

**Keep text short.** Classic memes use punchy phrases of 3–6 words per line. The generator wraps long text automatically, but shorter is almost always better.

**Use Impact font.** The tool prioritizes Impact (the traditional meme font) and falls back to Arial Black. These wide, bold letterforms with a black outline are what define the classic meme aesthetic.

**Outline width matters.** An outline width of 3–6 px works well for most images. Increase it for busy or dark backgrounds; decrease for light, clean backgrounds.

**Full resolution output.** The PNG download is rendered at the original image's pixel dimensions, so your meme stays sharp even on large displays.

---

## Related Tools

> Resize or compress any image before adding text → [Image Resizer](/tools/image-resizer/)

> Generate placeholder images for mockups or testing → [Placeholder Image Generator](/tools/placeholder-image/)
