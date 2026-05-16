---
title: "CSS Filter Generator — Image Effects Tool"
date: 2025-05-16
description: "Create CSS filter effects with live preview. Adjust blur, brightness, contrast, and more. Presets for vintage, noir, and dramatic effects. Copy CSS filter code instantly."
categories: ["Free Tools"]
slug: "css-filter-generator"
ShowToc: false
aliases:
  - "/tools/css-filter/"
  - "/tools/image-filter/"
cover:
  image: "/images/covers/css-filter-generator.png"
  alt: "CSS Filter Generator"
---

<div id="cf-app">

<style>
#cf-app *,
#cf-app *::before,
#cf-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#cf-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 15px;
  color: #1a1a2e;
  line-height: 1.5;
}

/* Layout */
#cf-app .cf-layout {
  display: grid;
  grid-template-columns: 1fr 340px;
  gap: 24px;
  align-items: start;
}

@media (max-width: 900px) {
  #cf-app .cf-layout {
    grid-template-columns: 1fr;
  }
}

/* Preview Panel */
#cf-app .cf-preview-panel {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  overflow: hidden;
}

#cf-app .cf-preview-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 16px;
  background: #f8fafc;
  border-bottom: 1px solid #e2e8f0;
  flex-wrap: wrap;
  gap: 8px;
}

#cf-app .cf-preview-header h3 {
  font-size: 14px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

#cf-app .cf-preview-actions {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

#cf-app .cf-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 6px 12px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  background: #fff;
  color: #374151;
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.15s ease;
  white-space: nowrap;
}

#cf-app .cf-btn:hover {
  background: #f1f5f9;
  border-color: #94a3b8;
}

#cf-app .cf-btn-primary {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}

#cf-app .cf-btn-primary:hover {
  background: #4f46e5;
  border-color: #4f46e5;
}

#cf-app .cf-btn-success {
  background: #10b981;
  border-color: #10b981;
  color: #fff;
}

#cf-app .cf-btn-danger {
  background: #ef4444;
  border-color: #ef4444;
  color: #fff;
  font-size: 12px;
  padding: 4px 8px;
}

#cf-app .cf-btn-sm {
  padding: 4px 8px;
  font-size: 12px;
}

/* Image Wrapper */
#cf-app .cf-image-wrapper {
  position: relative;
  overflow: hidden;
  background: #0f172a;
  min-height: 260px;
  display: flex;
  align-items: center;
  justify-content: center;
}

#cf-app .cf-preview-img {
  display: block;
  max-width: 100%;
  max-height: 400px;
  width: auto;
  height: auto;
  object-fit: contain;
  transition: filter 0.2s ease;
  user-select: none;
}

#cf-app .cf-before-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  object-fit: cover;
  clip-path: inset(0 50% 0 0);
  filter: none !important;
  display: none;
  max-width: none;
  max-height: none;
}

#cf-app.cf-compare-mode .cf-before-img {
  display: block;
}

#cf-app.cf-compare-mode .cf-preview-img {
  width: 100%;
  max-height: 400px;
  object-fit: cover;
}

#cf-app .cf-compare-label {
  position: absolute;
  top: 8px;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  padding: 3px 8px;
  border-radius: 4px;
  display: none;
}

#cf-app.cf-compare-mode .cf-compare-label {
  display: block;
}

#cf-app .cf-label-before {
  left: 8px;
  background: rgba(0,0,0,0.6);
  color: #fff;
}

#cf-app .cf-label-after {
  right: 8px;
  background: rgba(99,102,241,0.85);
  color: #fff;
}

#cf-app .cf-divider-line {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: #6366f1;
  display: none;
}

#cf-app.cf-compare-mode .cf-divider-line {
  display: block;
}

/* Drop zone overlay */
#cf-app .cf-drop-overlay {
  position: absolute;
  inset: 0;
  background: rgba(99,102,241,0.85);
  color: #fff;
  font-size: 18px;
  font-weight: 600;
  display: none;
  align-items: center;
  justify-content: center;
  border-radius: 0;
  pointer-events: none;
}

#cf-app .cf-image-wrapper.cf-drag-over .cf-drop-overlay {
  display: flex;
}

/* Image upload bar */
#cf-app .cf-upload-bar {
  display: flex;
  gap: 8px;
  padding: 10px 14px;
  background: #f8fafc;
  border-top: 1px solid #e2e8f0;
  align-items: center;
  flex-wrap: wrap;
}

#cf-app .cf-url-input {
  flex: 1;
  min-width: 120px;
  padding: 6px 10px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  outline: none;
  transition: border-color 0.15s;
}

#cf-app .cf-url-input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}

/* CSS Output */
#cf-app .cf-output-panel {
  background: #0f172a;
  color: #e2e8f0;
  padding: 14px 16px;
  border-top: 1px solid #e2e8f0;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 13px;
  line-height: 1.6;
  display: flex;
  align-items: flex-start;
  gap: 10px;
  justify-content: space-between;
}

#cf-app .cf-css-code {
  flex: 1;
  white-space: pre-wrap;
  word-break: break-all;
  color: #a5b4fc;
}

#cf-app .cf-css-prop {
  color: #67e8f9;
}

#cf-app .cf-css-val {
  color: #fde68a;
}

#cf-app .cf-copy-btn {
  flex-shrink: 0;
  padding: 5px 10px;
  border: 1px solid #334155;
  border-radius: 6px;
  background: #1e293b;
  color: #94a3b8;
  font-size: 12px;
  cursor: pointer;
  transition: all 0.15s;
  font-family: inherit;
}

#cf-app .cf-copy-btn:hover {
  background: #334155;
  color: #e2e8f0;
}

#cf-app .cf-copy-btn.cf-copied {
  background: #10b981;
  border-color: #10b981;
  color: #fff;
}

/* Controls Panel */
#cf-app .cf-controls-panel {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  overflow: hidden;
}

#cf-app .cf-controls-header {
  padding: 12px 16px;
  background: #f8fafc;
  border-bottom: 1px solid #e2e8f0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#cf-app .cf-controls-header h3 {
  font-size: 14px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

#cf-app .cf-filter-list {
  padding: 12px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-height: 520px;
  overflow-y: auto;
}

#cf-app .cf-filter-item {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 10px 12px;
}

#cf-app .cf-filter-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 6px;
}

#cf-app .cf-filter-name {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
}

#cf-app .cf-filter-val {
  font-size: 12px;
  font-weight: 600;
  color: #6366f1;
  min-width: 48px;
  text-align: right;
}

#cf-app .cf-filter-row {
  display: flex;
  align-items: center;
  gap: 8px;
}

#cf-app .cf-slider {
  -webkit-appearance: none;
  flex: 1;
  height: 4px;
  border-radius: 2px;
  background: #e2e8f0;
  outline: none;
  cursor: pointer;
  transition: background 0.15s;
}

#cf-app .cf-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #6366f1;
  cursor: pointer;
  border: 2px solid #fff;
  box-shadow: 0 0 0 1px #6366f1;
  transition: transform 0.1s;
}

#cf-app .cf-slider::-webkit-slider-thumb:hover {
  transform: scale(1.2);
}

#cf-app .cf-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #6366f1;
  cursor: pointer;
  border: 2px solid #fff;
  box-shadow: 0 0 0 1px #6366f1;
}

#cf-app .cf-reset-single {
  background: none;
  border: none;
  color: #94a3b8;
  font-size: 15px;
  cursor: pointer;
  padding: 0 2px;
  line-height: 1;
  transition: color 0.15s;
  flex-shrink: 0;
}

#cf-app .cf-reset-single:hover {
  color: #ef4444;
}

/* Drop shadow sub-controls */
#cf-app .cf-shadow-sub {
  margin-top: 8px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6px;
}

#cf-app .cf-shadow-sub label {
  font-size: 11px;
  color: #64748b;
  display: block;
  margin-bottom: 2px;
}

#cf-app .cf-shadow-color-row {
  grid-column: span 2;
  display: flex;
  align-items: center;
  gap: 8px;
}

#cf-app .cf-color-input {
  width: 36px;
  height: 28px;
  border: 1px solid #cbd5e1;
  border-radius: 4px;
  cursor: pointer;
  padding: 1px;
  background: none;
}

/* Presets */
#cf-app .cf-presets-section {
  padding: 12px;
  border-top: 1px solid #e2e8f0;
}

#cf-app .cf-presets-label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 8px;
}

#cf-app .cf-presets-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 6px;
}

#cf-app .cf-preset-btn {
  padding: 7px 6px;
  border: 1px solid #e2e8f0;
  border-radius: 6px;
  background: #f8fafc;
  color: #374151;
  font-size: 12px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.15s;
  text-align: center;
}

#cf-app .cf-preset-btn:hover {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}

#cf-app .cf-preset-btn.cf-active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}

/* Notification */
#cf-app .cf-toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background: #1e293b;
  color: #fff;
  padding: 10px 18px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  opacity: 0;
  transform: translateY(8px);
  transition: opacity 0.2s, transform 0.2s;
  pointer-events: none;
  z-index: 9999;
  box-shadow: 0 4px 16px rgba(0,0,0,0.25);
}

#cf-app .cf-toast.cf-show {
  opacity: 1;
  transform: translateY(0);
}

/* Section label */
#cf-app .cf-section-title {
  font-size: 22px;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 6px;
}

#cf-app .cf-section-sub {
  font-size: 14px;
  color: #64748b;
  margin-bottom: 20px;
}
</style>

<p class="cf-section-title">CSS Filter Generator</p>
<p class="cf-section-sub">Adjust sliders to create filter effects and copy the CSS instantly. Drag & drop an image or paste a URL to use your own photo.</p>

<div class="cf-layout">
  <!-- Preview Panel -->
  <div class="cf-preview-panel">
    <div class="cf-preview-header">
      <h3>Live Preview</h3>
      <div class="cf-preview-actions">
        <button class="cf-btn cf-btn-sm" id="cf-compare-btn">&#9654; Before / After</button>
        <button class="cf-btn cf-btn-sm cf-btn-primary" id="cf-copy-main-btn">Copy CSS</button>
      </div>
    </div>

    <div class="cf-image-wrapper" id="cf-image-wrapper">
      <canvas id="cf-default-canvas" style="display:none;"></canvas>
      <img id="cf-preview-img" class="cf-preview-img" alt="Preview" />
      <img id="cf-before-img" class="cf-before-img" alt="Before" />
      <div class="cf-compare-label cf-label-before">Before</div>
      <div class="cf-compare-label cf-label-after">After</div>
      <div class="cf-divider-line"></div>
      <div class="cf-drop-overlay">Drop image here</div>
    </div>

    <div class="cf-upload-bar">
      <input type="text" class="cf-url-input" id="cf-url-input" placeholder="Paste image URL and press Enter…" />
      <button class="cf-btn cf-btn-sm" id="cf-load-url-btn">Load</button>
      <label class="cf-btn cf-btn-sm" style="cursor:pointer;">
        Upload
        <input type="file" id="cf-file-input" accept="image/*" style="display:none;" />
      </label>
    </div>

    <div class="cf-output-panel">
      <span class="cf-css-code" id="cf-css-output"><span class="cf-css-prop">filter</span>: <span class="cf-css-val" id="cf-css-val-span">none</span>;</span>
      <button class="cf-copy-btn" id="cf-copy-output-btn">Copy</button>
    </div>
  </div>

  <!-- Controls Panel -->
  <div class="cf-controls-panel">
    <div class="cf-controls-header">
      <h3>Filter Controls</h3>
      <button class="cf-btn cf-btn-sm cf-btn-danger" id="cf-reset-all-btn">Reset All</button>
    </div>

    <div class="cf-filter-list" id="cf-filter-list">
      <!-- Filters rendered by JS -->
    </div>

    <div class="cf-presets-section">
      <div class="cf-presets-label">Presets</div>
      <div class="cf-presets-grid" id="cf-presets-grid">
        <!-- Presets rendered by JS -->
      </div>
    </div>
  </div>
</div>

<div class="cf-toast" id="cf-toast"></div>

<script>
(function() {
  'use strict';

  /* ── Filter definitions ── */
  const FILTERS = [
    { id: 'blur',       label: 'Blur',        min: 0,   max: 20,  step: 0.1, def: 0,   unit: 'px',  fmt: v => v === 0 ? null : `blur(${v}px)` },
    { id: 'brightness', label: 'Brightness',  min: 0,   max: 3,   step: 0.01,def: 1,   unit: '',    fmt: v => v === 1 ? null : `brightness(${v})` },
    { id: 'contrast',   label: 'Contrast',    min: 0,   max: 3,   step: 0.01,def: 1,   unit: '',    fmt: v => v === 1 ? null : `contrast(${v})` },
    { id: 'grayscale',  label: 'Grayscale',   min: 0,   max: 100, step: 1,   def: 0,   unit: '%',   fmt: v => v === 0 ? null : `grayscale(${v}%)` },
    { id: 'hue-rotate', label: 'Hue Rotate',  min: 0,   max: 360, step: 1,   def: 0,   unit: 'deg', fmt: v => v === 0 ? null : `hue-rotate(${v}deg)` },
    { id: 'invert',     label: 'Invert',      min: 0,   max: 100, step: 1,   def: 0,   unit: '%',   fmt: v => v === 0 ? null : `invert(${v}%)` },
    { id: 'opacity',    label: 'Opacity',     min: 0,   max: 1,   step: 0.01,def: 1,   unit: '',    fmt: v => v === 1 ? null : `opacity(${v})` },
    { id: 'saturate',   label: 'Saturate',    min: 0,   max: 5,   step: 0.01,def: 1,   unit: '',    fmt: v => v === 1 ? null : `saturate(${v})` },
    { id: 'sepia',      label: 'Sepia',       min: 0,   max: 100, step: 1,   def: 0,   unit: '%',   fmt: v => v === 0 ? null : `sepia(${v}%)` },
  ];

  /* Drop-shadow handled separately */
  const SHADOW_DEF = { x: 0, y: 0, blur: 0, color: '#000000' };

  /* ── Presets ── */
  const PRESETS = {
    'Vintage':        { blur:0, brightness:1.05, contrast:1.1, grayscale:10, 'hue-rotate':15, invert:0, opacity:1, saturate:0.85, sepia:30, shadow:{ x:0,y:0,blur:0,color:'#000000' } },
    'Noir':           { blur:0, brightness:0.9,  contrast:1.4, grayscale:100,'hue-rotate':0,  invert:0, opacity:1, saturate:0,    sepia:0,  shadow:{ x:0,y:0,blur:0,color:'#000000' } },
    'Warm':           { blur:0, brightness:1.1,  contrast:1.05,grayscale:0, 'hue-rotate':20,  invert:0, opacity:1, saturate:1.3,  sepia:15, shadow:{ x:0,y:0,blur:0,color:'#000000' } },
    'Cool':           { blur:0, brightness:1.05, contrast:1.05,grayscale:0, 'hue-rotate':200, invert:0, opacity:1, saturate:1.2,  sepia:0,  shadow:{ x:0,y:0,blur:0,color:'#000000' } },
    'High Contrast':  { blur:0, brightness:1.0,  contrast:2.0, grayscale:0, 'hue-rotate':0,   invert:0, opacity:1, saturate:1.2,  sepia:0,  shadow:{ x:0,y:0,blur:0,color:'#000000' } },
    'Faded':          { blur:0, brightness:1.15, contrast:0.75,grayscale:10,'hue-rotate':0,   invert:0, opacity:0.9,saturate:0.7, sepia:10, shadow:{ x:0,y:0,blur:0,color:'#000000' } },
    'Dramatic':       { blur:0, brightness:0.85, contrast:1.6, grayscale:0, 'hue-rotate':0,   invert:0, opacity:1, saturate:1.4,  sepia:0,  shadow:{ x:2,y:2,blur:8,color:'#000000' } },
    'Sepia Classic':  { blur:0, brightness:1.05, contrast:1.1, grayscale:0, 'hue-rotate':0,   invert:0, opacity:1, saturate:0.9,  sepia:80, shadow:{ x:0,y:0,blur:0,color:'#000000' } },
  };

  /* ── State ── */
  let values = {};
  let shadow = { ...SHADOW_DEF };
  let compareMode = false;
  let activePreset = null;

  FILTERS.forEach(f => { values[f.id] = f.def; });

  /* ── DOM refs ── */
  const app          = document.getElementById('cf-app');
  const previewImg   = document.getElementById('cf-preview-img');
  const beforeImg    = document.getElementById('cf-before-img');
  const filterList   = document.getElementById('cf-filter-list');
  const presetsGrid  = document.getElementById('cf-presets-grid');
  const cssValSpan   = document.getElementById('cf-css-val-span');
  const compareBtn   = document.getElementById('cf-compare-btn');
  const resetAllBtn  = document.getElementById('cf-reset-all-btn');
  const copyMainBtn  = document.getElementById('cf-copy-main-btn');
  const copyOutBtn   = document.getElementById('cf-copy-output-btn');
  const urlInput     = document.getElementById('cf-url-input');
  const loadUrlBtn   = document.getElementById('cf-load-url-btn');
  const fileInput    = document.getElementById('cf-file-input');
  const imageWrapper = document.getElementById('cf-image-wrapper');
  const toast        = document.getElementById('cf-toast');
  const canvas       = document.getElementById('cf-default-canvas');

  /* ── Generate default canvas image ── */
  function generateDefaultImage() {
    canvas.width  = 600;
    canvas.height = 400;
    const ctx = canvas.getContext('2d');

    /* Sky gradient */
    const sky = ctx.createLinearGradient(0, 0, 0, 260);
    sky.addColorStop(0, '#1e3a8a');
    sky.addColorStop(0.5, '#3b82f6');
    sky.addColorStop(1, '#93c5fd');
    ctx.fillStyle = sky;
    ctx.fillRect(0, 0, 600, 260);

    /* Sun */
    const sunGrad = ctx.createRadialGradient(480, 80, 0, 480, 80, 80);
    sunGrad.addColorStop(0, '#fef08a');
    sunGrad.addColorStop(0.4, '#fbbf24');
    sunGrad.addColorStop(1, 'rgba(251,191,36,0)');
    ctx.fillStyle = sunGrad;
    ctx.beginPath();
    ctx.arc(480, 80, 80, 0, Math.PI * 2);
    ctx.fill();

    /* Clouds */
    function cloud(cx, cy, s) {
      ctx.fillStyle = 'rgba(255,255,255,0.85)';
      ctx.beginPath(); ctx.arc(cx, cy, s*1.0, 0, Math.PI*2); ctx.fill();
      ctx.beginPath(); ctx.arc(cx+s*1.2, cy+s*0.2, s*0.8, 0, Math.PI*2); ctx.fill();
      ctx.beginPath(); ctx.arc(cx-s*1.0, cy+s*0.3, s*0.7, 0, Math.PI*2); ctx.fill();
      ctx.beginPath(); ctx.arc(cx+s*0.3, cy-s*0.5, s*0.65, 0, Math.PI*2); ctx.fill();
    }
    cloud(120, 70, 28);
    cloud(300, 50, 22);

    /* Ground */
    const ground = ctx.createLinearGradient(0, 255, 0, 400);
    ground.addColorStop(0, '#22c55e');
    ground.addColorStop(0.4, '#16a34a');
    ground.addColorStop(1, '#14532d');
    ctx.fillStyle = ground;
    ctx.fillRect(0, 255, 600, 145);

    /* Path */
    ctx.fillStyle = '#d97706';
    ctx.beginPath();
    ctx.moveTo(250, 400); ctx.lineTo(350, 400);
    ctx.lineTo(320, 260); ctx.lineTo(280, 260);
    ctx.closePath(); ctx.fill();

    /* Mountains */
    function mountain(x, h, w, color) {
      ctx.fillStyle = color;
      ctx.beginPath();
      ctx.moveTo(x - w/2, 260);
      ctx.lineTo(x, 260 - h);
      ctx.lineTo(x + w/2, 260);
      ctx.closePath();
      ctx.fill();
    }
    mountain(100, 120, 200, '#6b7280');
    mountain(220, 100, 180, '#9ca3af');
    mountain(400, 140, 220, '#4b5563');
    mountain(520, 90,  170, '#374151');

    /* Snow caps */
    ctx.fillStyle = '#f1f5f9';
    [[100,140],[220,120],[400,160],[520,110]].forEach(([x,h]) => {
      ctx.beginPath();
      ctx.moveTo(x, 260-h);
      ctx.lineTo(x-28, 260-h+40);
      ctx.lineTo(x+28, 260-h+40);
      ctx.closePath();
      ctx.fill();
    });

    /* Trees */
    function tree(x, y, s) {
      ctx.fillStyle = '#15803d';
      ctx.beginPath(); ctx.moveTo(x,y-s*2); ctx.lineTo(x-s,y); ctx.lineTo(x+s,y); ctx.closePath(); ctx.fill();
      ctx.beginPath(); ctx.moveTo(x,y-s*3.2); ctx.lineTo(x-s*0.7,y-s*1.6); ctx.lineTo(x+s*0.7,y-s*1.6); ctx.closePath(); ctx.fill();
      ctx.fillStyle = '#92400e';
      ctx.fillRect(x-s*0.18, y, s*0.36, s*0.8);
    }
    [50,160,185,410,460,490,540].forEach((tx,i) => tree(tx, 340-i%3*6, 14+i%2*4));

    /* Flowers */
    const flowerColors = ['#f43f5e','#a855f7','#f97316','#facc15'];
    for(let i=0;i<25;i++) {
      const fx = 30 + Math.random()*540;
      const fy = 270 + Math.random()*110;
      ctx.fillStyle = flowerColors[i%4];
      ctx.beginPath();
      ctx.arc(fx, fy, 4, 0, Math.PI*2);
      ctx.fill();
      ctx.fillStyle = '#fef9c3';
      ctx.beginPath();
      ctx.arc(fx, fy, 2, 0, Math.PI*2);
      ctx.fill();
    }

    /* Water reflection */
    const water = ctx.createLinearGradient(200, 310, 200, 380);
    water.addColorStop(0, 'rgba(59,130,246,0.55)');
    water.addColorStop(1, 'rgba(30,64,175,0.35)');
    ctx.fillStyle = water;
    ctx.beginPath();
    ctx.ellipse(300, 355, 90, 32, 0, 0, Math.PI*2);
    ctx.fill();
    /* Shimmer */
    ctx.strokeStyle = 'rgba(255,255,255,0.4)';
    ctx.lineWidth = 1.5;
    for(let i=0;i<5;i++) {
      ctx.beginPath();
      ctx.moveTo(230+i*14, 350+i%2*4);
      ctx.lineTo(255+i*14, 350+i%2*4);
      ctx.stroke();
    }

    return canvas.toDataURL('image/png');
  }

  /* ── Init image ── */
  const defaultDataUrl = generateDefaultImage();
  previewImg.src  = defaultDataUrl;
  beforeImg.src   = defaultDataUrl;

  /* ── Build filter controls ── */
  function buildControls() {
    filterList.innerHTML = '';
    FILTERS.forEach(f => {
      const item = document.createElement('div');
      item.className = 'cf-filter-item';

      const top = document.createElement('div');
      top.className = 'cf-filter-top';

      const name = document.createElement('span');
      name.className = 'cf-filter-name';
      name.textContent = f.label;

      const val = document.createElement('span');
      val.className = 'cf-filter-val';
      val.id = `cf-val-${f.id}`;
      val.textContent = formatDisplay(f, values[f.id]);

      top.appendChild(name);
      top.appendChild(val);

      const row = document.createElement('div');
      row.className = 'cf-filter-row';

      const slider = document.createElement('input');
      slider.type      = 'range';
      slider.className = 'cf-slider';
      slider.id        = `cf-slider-${f.id}`;
      slider.min       = f.min;
      slider.max       = f.max;
      slider.step      = f.step;
      slider.value     = values[f.id];

      slider.addEventListener('input', () => {
        values[f.id] = parseFloat(slider.value);
        val.textContent = formatDisplay(f, values[f.id]);
        activePreset = null;
        updatePresetButtons();
        applyFilter();
      });

      const resetBtn = document.createElement('button');
      resetBtn.className = 'cf-reset-single';
      resetBtn.title = 'Reset';
      resetBtn.textContent = '↺';
      resetBtn.addEventListener('click', () => {
        values[f.id] = f.def;
        slider.value = f.def;
        val.textContent = formatDisplay(f, f.def);
        activePreset = null;
        updatePresetButtons();
        applyFilter();
      });

      row.appendChild(slider);
      row.appendChild(resetBtn);
      item.appendChild(top);
      item.appendChild(row);
      filterList.appendChild(item);
    });

    /* Drop-shadow item */
    const shadowItem = document.createElement('div');
    shadowItem.className = 'cf-filter-item';
    shadowItem.innerHTML = `
      <div class="cf-filter-top">
        <span class="cf-filter-name">Drop Shadow</span>
        <button class="cf-reset-single" id="cf-reset-shadow" title="Reset">↺</button>
      </div>
      <div class="cf-shadow-sub">
        <div>
          <label>X offset (px)</label>
          <input type="range" class="cf-slider" id="cf-shadow-x" min="-30" max="30" step="1" value="0" />
          <span class="cf-filter-val" id="cf-shadow-x-val">0px</span>
        </div>
        <div>
          <label>Y offset (px)</label>
          <input type="range" class="cf-slider" id="cf-shadow-y" min="-30" max="30" step="1" value="0" />
          <span class="cf-filter-val" id="cf-shadow-y-val">0px</span>
        </div>
        <div>
          <label>Blur (px)</label>
          <input type="range" class="cf-slider" id="cf-shadow-blur" min="0" max="30" step="1" value="0" />
          <span class="cf-filter-val" id="cf-shadow-blur-val">0px</span>
        </div>
        <div class="cf-shadow-color-row">
          <label>Color</label>
          <input type="color" class="cf-color-input" id="cf-shadow-color" value="#000000" />
          <span id="cf-shadow-color-val" style="font-size:12px;color:#64748b;">#000000</span>
        </div>
      </div>
    `;
    filterList.appendChild(shadowItem);

    /* Shadow events */
    ['x','y','blur'].forEach(k => {
      const sl  = document.getElementById(`cf-shadow-${k}`);
      const lbl = document.getElementById(`cf-shadow-${k}-val`);
      sl.addEventListener('input', () => {
        shadow[k] = parseInt(sl.value);
        lbl.textContent = sl.value + 'px';
        applyFilter();
      });
    });
    document.getElementById('cf-shadow-color').addEventListener('input', function() {
      shadow.color = this.value;
      document.getElementById('cf-shadow-color-val').textContent = this.value;
      applyFilter();
    });
    document.getElementById('cf-reset-shadow').addEventListener('click', () => {
      shadow = { ...SHADOW_DEF };
      document.getElementById('cf-shadow-x').value    = 0;
      document.getElementById('cf-shadow-y').value    = 0;
      document.getElementById('cf-shadow-blur').value = 0;
      document.getElementById('cf-shadow-color').value = '#000000';
      document.getElementById('cf-shadow-x-val').textContent    = '0px';
      document.getElementById('cf-shadow-y-val').textContent    = '0px';
      document.getElementById('cf-shadow-blur-val').textContent = '0px';
      document.getElementById('cf-shadow-color-val').textContent = '#000000';
      applyFilter();
    });
  }

  function formatDisplay(f, v) {
    if (f.unit === '%')   return v + '%';
    if (f.unit === 'px')  return v + 'px';
    if (f.unit === 'deg') return v + '°';
    return v;
  }

  /* ── Build presets ── */
  function buildPresets() {
    presetsGrid.innerHTML = '';
    Object.keys(PRESETS).forEach(name => {
      const btn = document.createElement('button');
      btn.className = 'cf-preset-btn';
      btn.textContent = name;
      btn.dataset.preset = name;
      btn.addEventListener('click', () => applyPreset(name));
      presetsGrid.appendChild(btn);
    });
  }

  function applyPreset(name) {
    const p = PRESETS[name];
    FILTERS.forEach(f => {
      values[f.id] = p[f.id];
      const sl  = document.getElementById(`cf-slider-${f.id}`);
      const val = document.getElementById(`cf-val-${f.id}`);
      if (sl)  sl.value       = values[f.id];
      if (val) val.textContent = formatDisplay(f, values[f.id]);
    });
    shadow = { ...p.shadow };
    document.getElementById('cf-shadow-x').value     = shadow.x;
    document.getElementById('cf-shadow-y').value     = shadow.y;
    document.getElementById('cf-shadow-blur').value  = shadow.blur;
    document.getElementById('cf-shadow-color').value = shadow.color;
    document.getElementById('cf-shadow-x-val').textContent    = shadow.x + 'px';
    document.getElementById('cf-shadow-y-val').textContent    = shadow.y + 'px';
    document.getElementById('cf-shadow-blur-val').textContent = shadow.blur + 'px';
    document.getElementById('cf-shadow-color-val').textContent = shadow.color;
    activePreset = name;
    updatePresetButtons();
    applyFilter();
  }

  function updatePresetButtons() {
    document.querySelectorAll('#cf-presets-grid .cf-preset-btn').forEach(btn => {
      btn.classList.toggle('cf-active', btn.dataset.preset === activePreset);
    });
  }

  /* ── Apply filter ── */
  function buildFilterString() {
    const parts = [];
    FILTERS.forEach(f => {
      const v = values[f.id];
      const s = f.fmt(v);
      if (s) parts.push(s);
    });
    if (shadow.x !== 0 || shadow.y !== 0 || shadow.blur !== 0) {
      parts.push(`drop-shadow(${shadow.x}px ${shadow.y}px ${shadow.blur}px ${shadow.color})`);
    }
    return parts.length ? parts.join(' ') : 'none';
  }

  function applyFilter() {
    const fs = buildFilterString();
    previewImg.style.filter = fs === 'none' ? '' : fs;
    cssValSpan.textContent  = fs;
  }

  /* ── Compare mode ── */
  compareBtn.addEventListener('click', () => {
    compareMode = !compareMode;
    app.classList.toggle('cf-compare-mode', compareMode);
    compareBtn.textContent = compareMode ? '✕ Exit Compare' : '▶ Before / After';
  });

  /* ── Reset all ── */
  resetAllBtn.addEventListener('click', () => {
    FILTERS.forEach(f => {
      values[f.id] = f.def;
      const sl  = document.getElementById(`cf-slider-${f.id}`);
      const val = document.getElementById(`cf-val-${f.id}`);
      if (sl)  sl.value        = f.def;
      if (val) val.textContent = formatDisplay(f, f.def);
    });
    shadow = { ...SHADOW_DEF };
    document.getElementById('cf-shadow-x').value     = 0;
    document.getElementById('cf-shadow-y').value     = 0;
    document.getElementById('cf-shadow-blur').value  = 0;
    document.getElementById('cf-shadow-color').value = '#000000';
    document.getElementById('cf-shadow-x-val').textContent    = '0px';
    document.getElementById('cf-shadow-y-val').textContent    = '0px';
    document.getElementById('cf-shadow-blur-val').textContent = '0px';
    document.getElementById('cf-shadow-color-val').textContent = '#000000';
    activePreset = null;
    updatePresetButtons();
    applyFilter();
  });

  /* ── Copy CSS ── */
  function copyToClipboard(text, btnEl) {
    navigator.clipboard.writeText(text).then(() => {
      btnEl.classList.add('cf-copied');
      btnEl.textContent = 'Copied!';
      setTimeout(() => {
        btnEl.classList.remove('cf-copied');
        btnEl.textContent = btnEl === copyOutBtn ? 'Copy' : 'Copy CSS';
      }, 1800);
      showToast('CSS copied to clipboard!');
    }).catch(() => {
      showToast('Copy failed — please select manually.');
    });
  }

  copyMainBtn.addEventListener('click', () => {
    copyToClipboard(`filter: ${buildFilterString()};`, copyMainBtn);
  });
  copyOutBtn.addEventListener('click', () => {
    copyToClipboard(`filter: ${buildFilterString()};`, copyOutBtn);
  });

  /* ── Toast ── */
  function showToast(msg) {
    toast.textContent = msg;
    toast.classList.add('cf-show');
    setTimeout(() => toast.classList.remove('cf-show'), 2200);
  }

  /* ── Load image from URL ── */
  function loadImageUrl(url) {
    if (!url.trim()) return;
    previewImg.src = url.trim();
    beforeImg.src  = url.trim();
    applyFilter();
  }

  loadUrlBtn.addEventListener('click', () => loadImageUrl(urlInput.value));
  urlInput.addEventListener('keydown', e => { if (e.key === 'Enter') loadImageUrl(urlInput.value); });

  /* ── File upload ── */
  fileInput.addEventListener('change', () => {
    const file = fileInput.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = e => {
      previewImg.src = e.target.result;
      beforeImg.src  = e.target.result;
      applyFilter();
    };
    reader.readAsDataURL(file);
  });

  /* ── Drag & drop ── */
  imageWrapper.addEventListener('dragover', e => {
    e.preventDefault();
    imageWrapper.classList.add('cf-drag-over');
  });
  imageWrapper.addEventListener('dragleave', () => {
    imageWrapper.classList.remove('cf-drag-over');
  });
  imageWrapper.addEventListener('drop', e => {
    e.preventDefault();
    imageWrapper.classList.remove('cf-drag-over');
    const file = e.dataTransfer.files[0];
    if (file && file.type.startsWith('image/')) {
      const reader = new FileReader();
      reader.onload = ev => {
        previewImg.src = ev.target.result;
        beforeImg.src  = ev.target.result;
        applyFilter();
      };
      reader.readAsDataURL(file);
    } else {
      const url = e.dataTransfer.getData('text/plain');
      if (url) loadImageUrl(url);
    }
  });

  /* ── Paste image ── */
  document.addEventListener('paste', e => {
    const items = e.clipboardData && e.clipboardData.items;
    if (!items) return;
    for (let i = 0; i < items.length; i++) {
      if (items[i].type.startsWith('image/')) {
        const blob = items[i].getAsFile();
        const reader = new FileReader();
        reader.onload = ev => {
          previewImg.src = ev.target.result;
          beforeImg.src  = ev.target.result;
          applyFilter();
          showToast('Image pasted!');
        };
        reader.readAsDataURL(blob);
        break;
      }
    }
  });

  /* ── Init ── */
  buildControls();
  buildPresets();
  applyFilter();

})();
</script>

---

### Related Tools
> Generate gradients → [CSS Gradient Generator](/tools/css-gradient-generator/)
> Check color contrast → [Color Contrast Checker](/tools/color-contrast-checker/)
> Resize images → [Image Resizer](/tools/image-resizer/)

</div>
