---
title: "写真フィルター・画像エフェクトツール"
date: 2026-01-21
description: "無料の写真フィルターツール。Instagram風フィルターの適用、明るさ・コントラスト・彩度などの調整をブラウザで完結。PNGダウンロード対応。"
categories: ["無料ツール"]
tags: ["写真フィルター", "画像エフェクト", "インスタフィルター", "画像編集", "無料ツール"]
slug: "photo-filter"
cover:
  image: "/images/covers/photo-filter-ja.png"
  alt: "写真フィルター・画像エフェクトツール"
ShowToc: false
---

<div id="pf-app">

<style>
#pf-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 0 48px 0;
  color: #1a202c;
}

#pf-app * {
  box-sizing: border-box;
}

/* Hero */
.pf-hero {
  background: linear-gradient(135deg, #7c3aed 0%, #6d28d9 50%, #4c1d95 100%);
  border-radius: 16px;
  padding: 32px 28px;
  margin-bottom: 24px;
  color: #fff;
}

.pf-hero h2 {
  margin: 0 0 6px 0;
  font-size: 22px;
  font-weight: 800;
}

.pf-hero p {
  margin: 0;
  font-size: 14px;
  opacity: 0.88;
  line-height: 1.7;
}

/* Drop Zone */
.pf-dropzone {
  border: 3px dashed #7c3aed;
  border-radius: 14px;
  padding: 48px 24px;
  text-align: center;
  background: #f5f3ff;
  cursor: pointer;
  transition: background 0.2s, border-color 0.2s;
  margin-bottom: 24px;
}

.pf-dropzone:hover,
.pf-dropzone.pf-drag-over {
  background: #ede9fe;
  border-color: #6d28d9;
}

.pf-dropzone-icon {
  font-size: 48px;
  margin-bottom: 12px;
}

.pf-dropzone h3 {
  margin: 0 0 6px 0;
  font-size: 17px;
  font-weight: 700;
  color: #4c1d95;
}

.pf-dropzone p {
  margin: 0 0 16px 0;
  font-size: 13px;
  color: #6b7280;
}

.pf-btn-upload {
  display: inline-block;
  padding: 10px 24px;
  background: #7c3aed;
  color: #fff;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: background 0.2s;
}

.pf-btn-upload:hover {
  background: #6d28d9;
}

/* Main Editor */
.pf-editor {
  display: none;
  gap: 24px;
}

.pf-editor.pf-visible {
  display: grid;
  grid-template-columns: 1fr 320px;
}

@media (max-width: 700px) {
  .pf-editor.pf-visible {
    grid-template-columns: 1fr;
  }
}

/* Canvas Area */
.pf-canvas-wrap {
  background: #0f172a;
  border-radius: 14px;
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  min-height: 300px;
}

.pf-canvas-label {
  color: #94a3b8;
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  text-align: center;
}

.pf-canvas-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

#pf-canvas {
  max-width: 100%;
  max-height: 480px;
  border-radius: 8px;
  display: block;
}

.pf-comparison-wrap {
  display: flex;
  gap: 8px;
}

.pf-comparison-wrap .pf-canvas-container {
  flex: 1;
  flex-direction: column;
  gap: 4px;
}

/* Controls Panel */
.pf-panel {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.pf-card {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 16px;
}

.pf-card-title {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #7c3aed;
  margin: 0 0 12px 0;
}

/* Preset Filters */
.pf-presets {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px;
}

.pf-preset-btn {
  position: relative;
  border: 2px solid transparent;
  border-radius: 8px;
  padding: 0;
  background: #f3f4f6;
  cursor: pointer;
  overflow: hidden;
  transition: border-color 0.15s, transform 0.1s;
  aspect-ratio: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
}

.pf-preset-btn:hover {
  transform: scale(1.04);
}

.pf-preset-btn.pf-active {
  border-color: #7c3aed;
}

.pf-preset-swatch {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  border-radius: 6px;
}

.pf-preset-label {
  position: relative;
  z-index: 1;
  font-size: 10px;
  font-weight: 700;
  color: #fff;
  text-shadow: 0 1px 3px rgba(0,0,0,0.7);
  padding: 4px 2px;
  width: 100%;
  text-align: center;
  background: linear-gradient(transparent, rgba(0,0,0,0.55));
}

/* Sliders */
.pf-slider-row {
  margin-bottom: 10px;
}

.pf-slider-row:last-child {
  margin-bottom: 0;
}

.pf-slider-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 4px;
}

.pf-slider-name {
  font-size: 12px;
  font-weight: 600;
  color: #374151;
}

.pf-slider-val {
  font-size: 12px;
  color: #7c3aed;
  font-weight: 700;
  min-width: 36px;
  text-align: right;
}

.pf-slider-row input[type="range"] {
  width: 100%;
  height: 4px;
  -webkit-appearance: none;
  appearance: none;
  background: #e5e7eb;
  border-radius: 2px;
  outline: none;
  cursor: pointer;
}

.pf-slider-row input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #7c3aed;
  cursor: pointer;
  box-shadow: 0 1px 4px rgba(124,58,237,0.4);
}

.pf-slider-row input[type="range"]::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #7c3aed;
  cursor: pointer;
  border: none;
}

/* Action Buttons */
.pf-actions {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.pf-btn {
  width: 100%;
  padding: 11px 16px;
  border: none;
  border-radius: 9px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.15s;
}

.pf-btn-primary {
  background: #7c3aed;
  color: #fff;
}

.pf-btn-primary:hover {
  background: #6d28d9;
}

.pf-btn-secondary {
  background: #f3f4f6;
  color: #374151;
}

.pf-btn-secondary:hover {
  background: #e5e7eb;
}

.pf-btn-danger {
  background: #fef2f2;
  color: #dc2626;
}

.pf-btn-danger:hover {
  background: #fee2e2;
}

/* Toggle Compare */
.pf-compare-toggle {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 12px;
  color: #6b7280;
  cursor: pointer;
  user-select: none;
  padding: 6px 0;
}

.pf-compare-toggle input[type="checkbox"] {
  accent-color: #7c3aed;
  width: 14px;
  height: 14px;
  cursor: pointer;
}

/* File info */
.pf-file-info {
  font-size: 11px;
  color: #9ca3af;
  text-align: center;
  padding: 4px 0;
}

/* Related tools */
.pf-related {
  margin-top: 32px;
  padding: 20px;
  background: #f9fafb;
  border-radius: 12px;
  border: 1px solid #e5e7eb;
}

.pf-related h3 {
  margin: 0 0 12px 0;
  font-size: 14px;
  font-weight: 700;
  color: #374151;
}

.pf-related-links {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.pf-related-links a {
  display: inline-block;
  padding: 6px 14px;
  background: #fff;
  border: 1px solid #d1d5db;
  border-radius: 20px;
  font-size: 13px;
  color: #7c3aed;
  text-decoration: none;
  transition: all 0.15s;
  font-weight: 500;
}

.pf-related-links a:hover {
  background: #f5f3ff;
  border-color: #7c3aed;
}
</style>

<!-- Drop Zone -->
<div class="pf-dropzone" id="pf-dropzone">
  <div class="pf-dropzone-icon">🖼️</div>
  <h3>写真をここにドロップ</h3>
  <p>JPEG・PNG・WebP・GIF対応。アップロード不要、ブラウザ完結</p>
  <button class="pf-btn-upload" id="pf-upload-btn">画像を選択</button>
  <input type="file" id="pf-file-input" accept="image/*" style="display:none">
</div>

<!-- Editor -->
<div class="pf-editor" id="pf-editor">

  <!-- Canvas -->
  <div class="pf-canvas-wrap" id="pf-canvas-wrap">
    <div class="pf-canvas-label" id="pf-canvas-label">フィルター適用後</div>
    <div class="pf-canvas-container" id="pf-canvas-container">
      <canvas id="pf-canvas"></canvas>
    </div>
    <div class="pf-file-info" id="pf-file-info"></div>
  </div>

  <!-- Controls -->
  <div class="pf-panel">

    <!-- Preset Filters -->
    <div class="pf-card">
      <div class="pf-card-title">プリセットフィルター</div>
      <div class="pf-presets" id="pf-presets"></div>
    </div>

    <!-- Adjustments -->
    <div class="pf-card">
      <div class="pf-card-title">詳細調整</div>
      <div id="pf-sliders"></div>
    </div>

    <!-- Actions -->
    <div class="pf-card">
      <div class="pf-card-title">操作</div>
      <div class="pf-actions">
        <label class="pf-compare-toggle">
          <input type="checkbox" id="pf-compare-chk"> Before / After 比較表示
        </label>
        <button class="pf-btn pf-btn-primary" id="pf-download-btn">PNGでダウンロード</button>
        <button class="pf-btn pf-btn-secondary" id="pf-new-btn">別の画像を読み込む</button>
        <button class="pf-btn pf-btn-danger" id="pf-reset-btn">フィルターをリセット</button>
      </div>
    </div>

  </div>
</div>

<script>
(function() {
  'use strict';

  // ── Preset definitions ─────────────────────────────────────────────────────
  const PRESETS = [
    { name: 'ノーマル',    brightness:100, contrast:100, saturate:100, sepia:0,   grayscale:0,  hueRotate:0,   blur:0,  invert:0, swatch:'#a78bfa' },
    { name: 'ヴィンテージ', brightness:105, contrast:95,  saturate:75,  sepia:35,  grayscale:0,  hueRotate:0,   blur:0,  invert:0, swatch:'#d97706' },
    { name: 'モノクロ',    brightness:100, contrast:110, saturate:0,   sepia:0,   grayscale:100,hueRotate:0,   blur:0,  invert:0, swatch:'#374151' },
    { name: '温かみ',      brightness:108, contrast:100, saturate:120, sepia:20,  grayscale:0,  hueRotate:10,  blur:0,  invert:0, swatch:'#f59e0b' },
    { name: 'クール',      brightness:100, contrast:105, saturate:110, sepia:0,   grayscale:0,  hueRotate:200, blur:0,  invert:0, swatch:'#3b82f6' },
    { name: 'ドラマチック', brightness:95,  contrast:140, saturate:90,  sepia:0,   grayscale:0,  hueRotate:0,   blur:0,  invert:0, swatch:'#1e1b4b' },
    { name: 'フェード',    brightness:115, contrast:80,  saturate:70,  sepia:10,  grayscale:0,  hueRotate:0,   blur:0,  invert:0, swatch:'#e9d5ff' },
    { name: 'ビビッド',    brightness:105, contrast:115, saturate:165, sepia:0,   grayscale:0,  hueRotate:0,   blur:0,  invert:0, swatch:'#ec4899' },
    { name: 'マット',      brightness:110, contrast:90,  saturate:80,  sepia:15,  grayscale:5,  hueRotate:0,   blur:0,  invert:0, swatch:'#6b7280' },
    { name: 'サンセット',  brightness:108, contrast:108, saturate:130, sepia:25,  grayscale:0,  hueRotate:340, blur:0,  invert:0, swatch:'#f97316' },
    { name: 'フォレスト',  brightness:100, contrast:105, saturate:120, sepia:0,   grayscale:0,  hueRotate:85,  blur:0,  invert:0, swatch:'#15803d' },
    { name: 'ソフトブラー', brightness:100, contrast:100, saturate:100, sepia:0,   grayscale:0,  hueRotate:0,   blur:1.5,invert:0, swatch:'#c4b5fd' },
  ];

  // ── Slider config ──────────────────────────────────────────────────────────
  const SLIDERS = [
    { key:'brightness', label:'明るさ',    min:0,   max:200, default:100, unit:'%' },
    { key:'contrast',   label:'コントラスト', min:0,  max:200, default:100, unit:'%' },
    { key:'saturate',   label:'彩度',      min:0,   max:200, default:100, unit:'%' },
    { key:'sepia',      label:'セピア',    min:0,   max:100, default:0,   unit:'%' },
    { key:'grayscale',  label:'グレースケール', min:0, max:100, default:0, unit:'%' },
    { key:'hueRotate',  label:'色相回転',  min:0,   max:360, default:0,   unit:'°' },
    { key:'blur',       label:'ブラー',    min:0,   max:10,  default:0,   unit:'px', step:0.1 },
    { key:'invert',     label:'階調反転',  min:0,   max:100, default:0,   unit:'%' },
  ];

  // ── State ──────────────────────────────────────────────────────────────────
  let state = {};
  let imgEl = null;
  let origCanvas = null;
  let comparing = false;
  let activePreset = 'ノーマル';

  function defaultState() {
    const s = {};
    SLIDERS.forEach(sl => { s[sl.key] = sl.default; });
    return s;
  }

  // ── DOM refs ───────────────────────────────────────────────────────────────
  const dropzone    = document.getElementById('pf-dropzone');
  const fileInput   = document.getElementById('pf-file-input');
  const uploadBtn   = document.getElementById('pf-upload-btn');
  const editor      = document.getElementById('pf-editor');
  const canvas      = document.getElementById('pf-canvas');
  const ctx         = canvas.getContext('2d');
  const canvasWrap  = document.getElementById('pf-canvas-wrap');
  const canvasLabel = document.getElementById('pf-canvas-label');
  const canvasCont  = document.getElementById('pf-canvas-container');
  const fileInfo    = document.getElementById('pf-file-info');
  const presetsEl   = document.getElementById('pf-presets');
  const slidersEl   = document.getElementById('pf-sliders');
  const dlBtn       = document.getElementById('pf-download-btn');
  const newBtn      = document.getElementById('pf-new-btn');
  const resetBtn    = document.getElementById('pf-reset-btn');
  const compareChk  = document.getElementById('pf-compare-chk');

  // ── Build Presets UI ───────────────────────────────────────────────────────
  PRESETS.forEach(p => {
    const btn = document.createElement('button');
    btn.className = 'pf-preset-btn' + (p.name === 'ノーマル' ? ' pf-active' : '');
    btn.dataset.name = p.name;
    btn.innerHTML = `
      <div class="pf-preset-swatch" style="background:${p.swatch}"></div>
      <span class="pf-preset-label">${p.name}</span>
    `;
    btn.addEventListener('click', () => applyPreset(p));
    presetsEl.appendChild(btn);
  });

  // ── Build Sliders UI ──────────────────────────────────────────────────────
  SLIDERS.forEach(sl => {
    const row = document.createElement('div');
    row.className = 'pf-slider-row';
    row.innerHTML = `
      <div class="pf-slider-header">
        <span class="pf-slider-name">${sl.label}</span>
        <span class="pf-slider-val" id="pf-val-${sl.key}">${sl.default}${sl.unit}</span>
      </div>
      <input type="range" id="pf-sl-${sl.key}"
        min="${sl.min}" max="${sl.max}"
        step="${sl.step || 1}" value="${sl.default}">
    `;
    slidersEl.appendChild(row);

    row.querySelector('input').addEventListener('input', (e) => {
      state[sl.key] = parseFloat(e.target.value);
      document.getElementById(`pf-val-${sl.key}`).textContent = state[sl.key] + sl.unit;
      activePreset = '';
      updateActivePresetUI();
      render();
    });
  });

  // ── Filter string builder ──────────────────────────────────────────────────
  function buildFilter(s) {
    return [
      `brightness(${s.brightness}%)`,
      `contrast(${s.contrast}%)`,
      `saturate(${s.saturate}%)`,
      `sepia(${s.sepia}%)`,
      `grayscale(${s.grayscale}%)`,
      `hue-rotate(${s.hueRotate}deg)`,
      `blur(${s.blur}px)`,
      `invert(${s.invert}%)`,
    ].join(' ');
  }

  // ── Render filtered image to canvas ───────────────────────────────────────
  function render() {
    if (!imgEl) return;
    ctx.filter = buildFilter(state);
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.drawImage(imgEl, 0, 0, canvas.width, canvas.height);
    ctx.filter = 'none';
  }

  // ── Apply preset ──────────────────────────────────────────────────────────
  function applyPreset(p) {
    activePreset = p.name;
    SLIDERS.forEach(sl => {
      state[sl.key] = p[sl.key] !== undefined ? p[sl.key] : sl.default;
      const input = document.getElementById(`pf-sl-${sl.key}`);
      const valEl = document.getElementById(`pf-val-${sl.key}`);
      if (input) input.value = state[sl.key];
      if (valEl) valEl.textContent = state[sl.key] + sl.unit;
    });
    updateActivePresetUI();
    render();
  }

  function updateActivePresetUI() {
    document.querySelectorAll('.pf-preset-btn').forEach(btn => {
      btn.classList.toggle('pf-active', btn.dataset.name === activePreset);
    });
  }

  // ── Load image ────────────────────────────────────────────────────────────
  function loadImage(file) {
    if (!file || !file.type.startsWith('image/')) return;
    const url = URL.createObjectURL(file);
    const img = new Image();
    img.onload = function() {
      imgEl = img;
      const maxW = 800, maxH = 600;
      let w = img.naturalWidth, h = img.naturalHeight;
      if (w > maxW) { h = Math.round(h * maxW / w); w = maxW; }
      if (h > maxH) { w = Math.round(w * maxH / h); h = maxH; }
      canvas.width = w;
      canvas.height = h;

      origCanvas = document.createElement('canvas');
      origCanvas.width = w;
      origCanvas.height = h;
      origCanvas.getContext('2d').drawImage(img, 0, 0, w, h);

      state = defaultState();
      activePreset = 'ノーマル';
      syncSliders();
      updateActivePresetUI();
      render();

      dropzone.style.display = 'none';
      editor.classList.add('pf-visible');
      fileInfo.textContent = `${file.name} — ${img.naturalWidth}×${img.naturalHeight}px`;
      URL.revokeObjectURL(url);
    };
    img.src = url;
  }

  function syncSliders() {
    SLIDERS.forEach(sl => {
      const input = document.getElementById(`pf-sl-${sl.key}`);
      const valEl = document.getElementById(`pf-val-${sl.key}`);
      if (input) input.value = state[sl.key];
      if (valEl) valEl.textContent = state[sl.key] + sl.unit;
    });
  }

  // ── Before/After comparison ───────────────────────────────────────────────
  function setCompareMode(on) {
    comparing = on;
    if (on) {
      canvasLabel.style.display = 'none';
      canvasCont.innerHTML = '';
      const wrap = document.createElement('div');
      wrap.className = 'pf-comparison-wrap';
      wrap.id = 'pf-cmp-wrap';

      const beforeDiv = document.createElement('div');
      beforeDiv.className = 'pf-canvas-container';
      const beforeLabel = document.createElement('div');
      beforeLabel.className = 'pf-canvas-label';
      beforeLabel.textContent = '変更前';
      beforeDiv.appendChild(beforeLabel);
      const beforeImg = document.createElement('canvas');
      beforeImg.width = origCanvas.width;
      beforeImg.height = origCanvas.height;
      beforeImg.style.maxWidth = '100%';
      beforeImg.style.borderRadius = '6px';
      beforeImg.getContext('2d').drawImage(origCanvas, 0, 0);
      beforeDiv.appendChild(beforeImg);

      const afterDiv = document.createElement('div');
      afterDiv.className = 'pf-canvas-container';
      const afterLabel = document.createElement('div');
      afterLabel.className = 'pf-canvas-label';
      afterLabel.textContent = '変更後';
      afterDiv.appendChild(afterLabel);
      canvas.style.maxWidth = '100%';
      canvas.style.borderRadius = '6px';
      afterDiv.appendChild(canvas);

      wrap.appendChild(beforeDiv);
      wrap.appendChild(afterDiv);
      canvasCont.appendChild(wrap);
    } else {
      canvasLabel.style.display = '';
      const cmpWrap = document.getElementById('pf-cmp-wrap');
      if (cmpWrap) {
        canvasCont.innerHTML = '';
        canvasCont.appendChild(canvas);
      }
      canvas.style.maxWidth = '';
      canvas.style.borderRadius = '';
    }
    render();
  }

  // ── Event listeners ───────────────────────────────────────────────────────
  uploadBtn.addEventListener('click', () => fileInput.click());
  fileInput.addEventListener('change', () => loadImage(fileInput.files[0]));

  dropzone.addEventListener('dragover', (e) => { e.preventDefault(); dropzone.classList.add('pf-drag-over'); });
  dropzone.addEventListener('dragleave', () => dropzone.classList.remove('pf-drag-over'));
  dropzone.addEventListener('drop', (e) => {
    e.preventDefault();
    dropzone.classList.remove('pf-drag-over');
    loadImage(e.dataTransfer.files[0]);
  });

  compareChk.addEventListener('change', () => setCompareMode(compareChk.checked));

  dlBtn.addEventListener('click', () => {
    const oc = document.createElement('canvas');
    oc.width = imgEl.naturalWidth;
    oc.height = imgEl.naturalHeight;
    const oc2d = oc.getContext('2d');
    oc2d.filter = buildFilter(state);
    oc2d.drawImage(imgEl, 0, 0, oc.width, oc.height);
    oc2d.filter = 'none';
    const a = document.createElement('a');
    a.download = 'photo-filter.png';
    a.href = oc.toDataURL('image/png');
    a.click();
  });

  resetBtn.addEventListener('click', () => {
    applyPreset(PRESETS[0]);
    compareChk.checked = false;
    if (comparing) setCompareMode(false);
  });

  newBtn.addEventListener('click', () => {
    editor.classList.remove('pf-visible');
    dropzone.style.display = '';
    fileInput.value = '';
    compareChk.checked = false;
    comparing = false;
    imgEl = null;
  });

})();
</script>

---

## 関連ツール

> 画像を指定サイズに変更 → [画像リサイザー](/ja/tools/image-resizer/)

> カラーコードの確認・変換 → [カラーピッカー](/ja/tools/color-picker/)

---

**個人事業主・フリーランスの会計をもっとかんたんに**

写真素材やデザイン制作を仕事にされている方。freee会計で帳簿・確定申告をまるっと効率化しませんか？

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">

</div>
