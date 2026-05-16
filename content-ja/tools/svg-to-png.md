---
title: "SVG→PNG変換ツール"
date: 2025-05-16
description: "SVGをPNGに無料変換。SVGファイルをアップロードまたはコード貼り付けで高解像度PNGをダウンロード。サーバー不要・完全ブラウザ処理。"
categories: ["無料ツール"]
slug: "svg-to-png"
ShowToc: false
cover:
  image: "/images/covers/svg-to-png-ja.png"
  alt: "SVG→PNG変換ツール"
---

<div id="sp-app">

<style>
#sp-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', Meiryo, sans-serif;
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
  line-height: 1.7;
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
  letter-spacing: 0.05em;
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
  line-height: 1.8;
}
</style>

<div class="sp-hero">
  <h2>SVG&#x2192;PNG 変換ツール</h2>
  <p>SVGファイルをアップロードするか、SVGコードを貼り付けて、スケールや背景を設定し、高解像度のPNGをダウンロードできます。すべてブラウザ上で処理されるため、ファイルがサーバーに送信されることはありません。</p>
</div>

<div id="sp-error" class="sp-error"></div>

<div class="sp-layout">
  <!-- 左: 入力 -->
  <div class="sp-panel">
    <p class="sp-panel-title">SVGを入力</p>

    <div class="sp-dropzone" id="sp-dropzone">
      <div class="sp-dropzone-icon">&#9653;</div>
      <p class="sp-dropzone-text">SVGファイルをドロップ</p>
      <p class="sp-dropzone-sub">またはクリックして選択</p>
    </div>
    <input type="file" id="sp-file-input" accept=".svg,image/svg+xml" style="display:none;">

    <div class="sp-field">
      <label class="sp-label" for="sp-code">またはSVGコードを貼り付け</label>
      <textarea id="sp-code" class="sp-textarea" placeholder="<svg xmlns=&quot;http://www.w3.org/2000/svg&quot; ...>&#10;  ...&#10;</svg>"></textarea>
    </div>

    <button class="sp-btn-secondary" id="sp-load-sample" style="margin-top:10px;">サンプルSVGを読み込む</button>
  </div>

  <!-- 右: 設定 -->
  <div class="sp-panel">
    <p class="sp-panel-title">設定</p>
    <div class="sp-controls">

      <div class="sp-field">
        <label class="sp-label">スケール（Retina対応）</label>
        <div class="sp-scale-row">
          <button class="sp-scale-btn active" data-scale="1">1x</button>
          <button class="sp-scale-btn" data-scale="2">2x</button>
          <button class="sp-scale-btn" data-scale="3">3x</button>
          <button class="sp-scale-btn" data-scale="4">4x</button>
        </div>
      </div>

      <div class="sp-field">
        <label class="sp-label">出力サイズ（px）</label>
        <div class="sp-dim-row">
          <input type="number" id="sp-width" class="sp-input" placeholder="幅" min="1" max="8000">
          <button class="sp-lock-btn locked" id="sp-lock-btn" title="アスペクト比を固定">&#128274;</button>
          <input type="number" id="sp-height" class="sp-input" placeholder="高さ" min="1" max="8000">
        </div>
        <p style="font-size:11px;color:#9ca3af;margin:2px 0 0 0;">空欄の場合はSVGの元サイズ×スケールで出力</p>
      </div>

      <div class="sp-field">
        <label class="sp-label">背景</label>
        <div class="sp-color-row">
          <input type="color" id="sp-bg-color" class="sp-color-input" value="#ffffff" title="背景色">
          <button class="sp-transparent-btn active" id="sp-transparent-btn">透明</button>
          <span style="font-size:12px;color:#6b7280;flex:1;" id="sp-bg-label">透明PNG</span>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- プレビュー + ダウンロード -->
<div class="sp-panel">
  <p class="sp-panel-title">プレビュー &amp; ダウンロード</p>
  <div class="sp-preview-wrap" id="sp-preview-wrap">
    <div class="sp-preview-placeholder" id="sp-preview-placeholder">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="3"/><path d="M3 9l4-4 4 4 4-6 4 6"/><circle cx="8.5" cy="13.5" r="1.5"/></svg>
      <p>ここにSVGのプレビューが表示されます</p>
    </div>
    <img id="sp-preview-img" style="display:none;" alt="SVGプレビュー">
  </div>

  <div class="sp-info-bar" id="sp-info-bar" style="display:none;">
    <div class="sp-info-chip">出力サイズ: <span id="sp-out-w">—</span> &times; <span id="sp-out-h">—</span> px</div>
    <div class="sp-info-chip">推定ファイルサイズ: <span id="sp-out-size">—</span></div>
    <div class="sp-info-chip">スケール: <span id="sp-out-scale">1</span>x</div>
  </div>

  <p class="sp-filename" id="sp-filename" style="display:none;"></p>

  <button class="sp-btn-primary" id="sp-convert-btn" disabled>変換してPNGをダウンロード</button>
</div>

<canvas id="sp-canvas"></canvas>

<div class="sp-how">
  <h3>使い方</h3>
  <ol>
    <li>SVGファイルをアップロードするか、SVGコードをテキストエリアに貼り付けます。</li>
    <li>スケール倍率を選択します（高解像度出力には2x・3xがおすすめです）。</li>
    <li>必要に応じて幅・高さを指定できます。鍵マークでアスペクト比を固定できます。</li>
    <li>背景色を指定するか、「透明」のままにします。</li>
    <li>「変換してPNGをダウンロード」をクリックすると、CanvasでSVGをレンダリングしてPNG保存します。</li>
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

  /* ── サンプルSVG ── */
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
      showError('有効なSVGではないようです。SVGコードを確認してください。');
      return;
    }
    svgSrc = text;
    currentFilename = filename || 'image';
    filenameEl.textContent = currentFilename + '.svg';
    filenameEl.style.display = 'block';

    var dims = getSVGDimensions(text);
    naturalW = dims.w;
    naturalH = dims.h;

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
        showError('エクスポートに失敗しました。SVGに外部リソースが含まれている場合、ブラウザのセキュリティポリシーによりブロックされることがあります。');
      }
    };

    img.onerror = function () {
      URL.revokeObjectURL(url);
      showError('SVGのレンダリングに失敗しました。SVGが正しい形式か確認してください。');
    };

    img.src = url;
  }

  /* ── ドロップゾーン ── */
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
      showError('SVGファイルを選択してください。');
      return;
    }
    var reader = new FileReader();
    reader.onload = function (e) {
      codeArea.value = e.target.result;
      loadSVG(e.target.result, file.name.replace(/\.svg$/i, ''));
    };
    reader.readAsText(file);
  }

  /* ── SVGコード入力 ── */
  codeArea.addEventListener('input', function () {
    if (codeArea.value.trim()) {
      loadSVG(codeArea.value, 'svg-export');
    }
  });

  /* ── スケールボタン ── */
  scaleBtns.forEach(function (btn) {
    btn.addEventListener('click', function () {
      scaleBtns.forEach(function (b) { b.classList.remove('active'); });
      btn.classList.add('active');
      scale = parseInt(btn.dataset.scale, 10);
      if (svgSrc) renderPreview();
    });
  });

  /* ── サイズ入力 ── */
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

  /* ── アスペクト比ロック ── */
  lockBtn.addEventListener('click', function () {
    aspectLocked = !aspectLocked;
    lockBtn.classList.toggle('locked', aspectLocked);
    lockBtn.textContent = aspectLocked ? '\uD83D\uDD12' : '\uD83D\uDD13';
  });

  /* ── 背景 ── */
  transpBtn.addEventListener('click', function () {
    bgTransparent = !bgTransparent;
    transpBtn.classList.toggle('active', bgTransparent);
    bgLabel.textContent = bgTransparent ? '透明PNG' : bgColor.value;
    if (svgSrc) renderPreview();
  });

  bgColor.addEventListener('input', function () {
    bgTransparent = false;
    transpBtn.classList.remove('active');
    bgLabel.textContent = bgColor.value;
    if (svgSrc) renderPreview();
  });

  /* ── 変換ボタン ── */
  convertBtn.addEventListener('click', convertAndDownload);

  /* ── サンプルボタン ── */
  sampleBtn.addEventListener('click', function () {
    codeArea.value = SAMPLE;
    loadSVG(SAMPLE, 'sample');
  });

})();
</script>

<div class="sp-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

> プレースホルダー画像 → [プレースホルダー画像生成](/ja/tools/placeholder-image/)

> 画像リサイズ → [画像リサイズツール](/ja/tools/image-resizer/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
