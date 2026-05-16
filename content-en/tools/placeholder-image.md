---
title: "Placeholder Image Generator"
date: 2025-05-16
description: "Free online placeholder image generator. Create custom dummy images with any size, color, and text — download as PNG or JPEG instantly, no sign-up required."
categories: ["Free Tools"]
slug: "placeholder-image"
ShowToc: false
aliases:
  - "/tools/dummy-image/"
  - "/tools/placeholder-generator/"
cover:
  image: "/images/covers/placeholder-image.png"
  alt: "Placeholder Image Generator"
---

Generate placeholder images instantly in your browser. Set width, height, background color, text color, and custom label — then download as PNG or JPEG. No uploads, no sign-up, fully client-side.

<div id="ph-app">
<style>
#ph-app {
  font-family: system-ui, -apple-system, sans-serif;
  color: #1e293b;
  max-width: 780px;
  margin: 0 auto;
}
#ph-app .ph-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 16px;
}
#ph-app .ph-field {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
#ph-app .ph-field label {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
}
#ph-app .ph-field input[type="number"],
#ph-app .ph-field input[type="text"],
#ph-app .ph-field select {
  padding: 8px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  color: #1e293b;
  background: #f8fafc;
  outline: none;
  transition: border-color 0.15s;
  width: 100%;
  box-sizing: border-box;
}
#ph-app .ph-field input:focus,
#ph-app .ph-field select:focus {
  border-color: #64748b;
  background: #fff;
}
#ph-app .ph-color-row {
  display: flex;
  align-items: center;
  gap: 8px;
}
#ph-app .ph-color-row input[type="color"] {
  width: 42px;
  height: 36px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  padding: 2px 3px;
  background: #f8fafc;
  cursor: pointer;
}
#ph-app .ph-color-row input[type="text"] {
  flex: 1;
}
#ph-app .ph-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 16px;
}
#ph-app .ph-presets button {
  padding: 6px 13px;
  border: 1.5px solid #cbd5e1;
  border-radius: 20px;
  background: #f1f5f9;
  font-size: 12px;
  font-weight: 600;
  color: #475569;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s, color 0.15s;
}
#ph-app .ph-presets button:hover {
  background: #64748b;
  color: #fff;
  border-color: #64748b;
}
#ph-app .ph-font-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 16px;
}
#ph-app .ph-font-row label {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  white-space: nowrap;
}
#ph-app .ph-font-row input[type="checkbox"] {
  width: 16px;
  height: 16px;
  cursor: pointer;
}
#ph-app .ph-font-row input[type="number"] {
  width: 80px;
  padding: 7px 9px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  color: #1e293b;
  background: #f8fafc;
  outline: none;
}
#ph-app .ph-actions {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}
#ph-app .ph-actions select {
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 600;
  color: #1e293b;
  background: #f8fafc;
  outline: none;
  cursor: pointer;
}
#ph-app .ph-btn-generate {
  padding: 9px 22px;
  background: #64748b;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#ph-app .ph-btn-generate:hover {
  background: #475569;
}
#ph-app .ph-btn-download {
  padding: 9px 22px;
  background: #0f172a;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#ph-app .ph-btn-download:hover {
  background: #1e293b;
}
#ph-app .ph-preview-wrap {
  border: 2px dashed #cbd5e1;
  border-radius: 10px;
  padding: 16px;
  background: #f8fafc;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  min-height: 160px;
  justify-content: center;
}
#ph-app canvas#ph-canvas {
  max-width: 100%;
  height: auto;
  border-radius: 6px;
  display: block;
  box-shadow: 0 2px 8px rgba(0,0,0,0.10);
}
#ph-app .ph-info {
  font-size: 12px;
  color: #94a3b8;
}
#ph-app .ph-section-title {
  font-size: 13px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin: 0 0 8px;
}
#ph-app .ph-divider {
  border: none;
  border-top: 1.5px solid #e2e8f0;
  margin: 16px 0;
}
@media (max-width: 520px) {
  #ph-app .ph-grid {
    grid-template-columns: 1fr;
  }
}
</style>

<p class="ph-section-title">Preset Sizes</p>
<div class="ph-presets">
  <button onclick="phSetPreset(728,90)">Web Banner (728×90)</button>
  <button onclick="phSetPreset(1200,630)">OG / Social (1200×630)</button>
  <button onclick="phSetPreset(1080,1080)">Instagram Square (1080×1080)</button>
  <button onclick="phSetPreset(375,667)">Mobile (375×667)</button>
</div>

<hr class="ph-divider">

<p class="ph-section-title">Settings</p>
<div class="ph-grid">
  <div class="ph-field">
    <label for="ph-width">Width (px)</label>
    <input type="number" id="ph-width" value="800" min="1" max="4096">
  </div>
  <div class="ph-field">
    <label for="ph-height">Height (px)</label>
    <input type="number" id="ph-height" value="600" min="1" max="4096">
  </div>
  <div class="ph-field">
    <label>Background Color</label>
    <div class="ph-color-row">
      <input type="color" id="ph-bg-picker" value="#94a3b8" oninput="phSyncColor('bg')">
      <input type="text" id="ph-bg-hex" value="#94a3b8" maxlength="7" oninput="phSyncColorFromHex('bg')" placeholder="#94a3b8">
    </div>
  </div>
  <div class="ph-field">
    <label>Text Color</label>
    <div class="ph-color-row">
      <input type="color" id="ph-text-picker" value="#ffffff" oninput="phSyncColor('text')">
      <input type="text" id="ph-text-hex" value="#ffffff" maxlength="7" oninput="phSyncColorFromHex('text')" placeholder="#ffffff">
    </div>
  </div>
  <div class="ph-field" style="grid-column: 1 / -1;">
    <label for="ph-label">Label Text <span style="font-weight:400;color:#94a3b8;">(leave blank to show dimensions)</span></label>
    <input type="text" id="ph-label" placeholder="e.g. Hero Image" value="">
  </div>
</div>

<div class="ph-font-row">
  <label>Font Size:</label>
  <label style="display:flex;align-items:center;gap:5px;cursor:pointer;">
    <input type="checkbox" id="ph-auto-font" checked onchange="phToggleAutoFont()"> Auto
  </label>
  <input type="number" id="ph-font-size" value="48" min="8" max="512" disabled style="opacity:0.5;">
  <span style="font-size:13px;color:#94a3b8;">px</span>
</div>

<hr class="ph-divider">

<div class="ph-actions">
  <select id="ph-format">
    <option value="png">PNG</option>
    <option value="jpeg">JPEG</option>
  </select>
  <button class="ph-btn-generate" onclick="phRender()">Preview</button>
  <button class="ph-btn-download" onclick="phDownload()">Download</button>
</div>

<div class="ph-preview-wrap">
  <canvas id="ph-canvas"></canvas>
  <p class="ph-info" id="ph-info-text">Click "Preview" to generate.</p>
</div>

<script>
(function() {
  function phGetVal(id) { return document.getElementById(id).value; }

  window.phSetPreset = function(w, h) {
    document.getElementById('ph-width').value = w;
    document.getElementById('ph-height').value = h;
    phRender();
  };

  window.phSyncColor = function(type) {
    var picker = document.getElementById('ph-' + type + '-picker');
    var hex = document.getElementById('ph-' + type + '-hex');
    hex.value = picker.value;
  };

  window.phSyncColorFromHex = function(type) {
    var hex = document.getElementById('ph-' + type + '-hex').value.trim();
    if (/^#[0-9a-fA-F]{6}$/.test(hex)) {
      document.getElementById('ph-' + type + '-picker').value = hex;
    }
  };

  window.phToggleAutoFont = function() {
    var auto = document.getElementById('ph-auto-font').checked;
    var fs = document.getElementById('ph-font-size');
    fs.disabled = auto;
    fs.style.opacity = auto ? '0.5' : '1';
  };

  function phCalcFontSize(w, h, text) {
    var shorter = Math.min(w, h);
    var base = Math.max(12, Math.round(shorter / (text.length > 8 ? 8 : 5)));
    return Math.min(base, Math.round(shorter / 3));
  }

  window.phRender = function() {
    var w = Math.max(1, Math.min(4096, parseInt(phGetVal('ph-width')) || 800));
    var h = Math.max(1, Math.min(4096, parseInt(phGetVal('ph-height')) || 600));
    var bg = phGetVal('ph-bg-hex') || '#94a3b8';
    var tc = phGetVal('ph-text-hex') || '#ffffff';
    var label = phGetVal('ph-label').trim() || (w + ' x ' + h);
    var autoFont = document.getElementById('ph-auto-font').checked;
    var fontSize = autoFont ? phCalcFontSize(w, h, label) : (parseInt(phGetVal('ph-font-size')) || 48);

    var canvas = document.getElementById('ph-canvas');
    canvas.width = w;
    canvas.height = h;
    var ctx = canvas.getContext('2d');

    ctx.fillStyle = /^#[0-9a-fA-F]{6}$/.test(bg) ? bg : '#94a3b8';
    ctx.fillRect(0, 0, w, h);

    ctx.fillStyle = /^#[0-9a-fA-F]{6}$/.test(tc) ? tc : '#ffffff';
    ctx.font = 'bold ' + fontSize + 'px system-ui, sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(label, w / 2, h / 2);

    document.getElementById('ph-info-text').textContent = w + ' x ' + h + ' px  |  Font: ' + fontSize + 'px';
    return canvas;
  };

  window.phDownload = function() {
    var canvas = phRender();
    var fmt = phGetVal('ph-format');
    var mime = fmt === 'jpeg' ? 'image/jpeg' : 'image/png';
    var ext = fmt === 'jpeg' ? 'jpg' : 'png';
    var w = canvas.width;
    var h = canvas.height;
    var link = document.createElement('a');
    link.download = 'placeholder-' + w + 'x' + h + '.' + ext;
    link.href = canvas.toDataURL(mime, 0.92);
    link.click();
  };

  // Auto-render on load
  document.addEventListener('DOMContentLoaded', function() { phRender(); });
  // Also try immediately in case DOM is already ready
  if (document.readyState !== 'loading') { setTimeout(phRender, 50); }
})();
</script>
</div>

---

### Related Tools

> Resize real images → [Image Resizer](/tools/image-resizer/)

> Generate favicons → [Favicon Generator](/tools/favicon-generator/)

> Build color palettes → [Color Palette Generator](/tools/color-palette-generator/)
