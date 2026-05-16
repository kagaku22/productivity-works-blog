---
title: "画像リサイザー｜無料でオンライン画像サイズ変更・圧縮ツール"
date: 2025-05-16
description: "画像を無料でオンラインリサイズ。カスタムサイズ指定・アスペクト比ロック・SNSプリセット対応。JPEG・PNG・WebP形式でダウンロード。アップロード不要、ブラウザ完結。"
categories: ["無料ツール"]
tags: ["画像リサイズ", "画像圧縮", "サイズ変更", "SNS画像", "無料ツール"]
slug: "image-resizer"
aliases: ["/ja/tools/image-compressor/", "/ja/tools/resize-image/"]
cover:
  image: "/images/covers/image-resizer-ja.png"
  alt: "画像リサイザー"
ShowToc: false
---

<div id="resize-app">

<style>
#resize-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', Roboto, sans-serif;
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
  font-size: 22px;
  font-weight: 800;
}

.ra-hero p {
  margin: 0;
  font-size: 14px;
  opacity: 0.88;
  line-height: 1.7;
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

#ra-file-input-ja {
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
  letter-spacing: 0.04em;
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
  letter-spacing: 0.02em;
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
  grid-template-columns: repeat(auto-fill, minmax(176px, 1fr));
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
  letter-spacing: 0.02em;
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

/* Size comparison */
.ra-size-comparison {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

.ra-size-box {
  flex: 1;
  min-width: 130px;
  background: #f9fafb;
  border-radius: 10px;
  padding: 14px 16px;
  text-align: center;
  border: 1px solid #e5e7eb;
}

.ra-size-box-label {
  font-size: 11px;
  font-weight: 700;
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

.ra-size-box.original .ra-size-box-value { color: #374151; }
.ra-size-box.output .ra-size-box-value   { color: #059669; }
.ra-size-box.savings .ra-size-box-value  { color: #dc2626; }

/* Download */
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

.ra-download-btn:hover:not(:disabled) { opacity: 0.92; }
.ra-download-btn:active:not(:disabled) { transform: scale(0.98); }
.ra-download-btn:disabled { background: #9ca3af; cursor: not-allowed; }

/* Hidden canvas */
#ra-canvas-ja { display: none; }

/* Placeholder */
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
  .ra-hero { padding: 22px 16px; }
  .ra-hero h2 { font-size: 18px; }
  .ra-card { padding: 16px 14px; }
  .ra-dim-row { gap: 8px; }
  .ra-preset-grid { grid-template-columns: 1fr 1fr; }
  .ra-settings-row { flex-direction: column; gap: 16px; }
  .ra-size-comparison { gap: 8px; }
}
</style>

<!-- Hero -->
<div class="ra-hero">
  <h2>無料画像リサイザー</h2>
  <p>画像のサイズ変更・圧縮をブラウザ上で完結。アップロード不要、アカウント不要。Canvas APIを使い、データはすべてあなたのデバイス内で処理されます。</p>
</div>

<!-- Drop Zone -->
<div class="ra-dropzone" id="ra-dropzone-ja">
  <span class="ra-dropzone-icon">🖼️</span>
  <div class="ra-dropzone-title">ここに画像をドラッグ＆ドロップ</div>
  <div class="ra-dropzone-sub">JPG・PNG・WebP・GIF・BMP対応 · 最大20MB</div>
  <button class="ra-browse-btn" onclick="document.getElementById('ra-file-input-ja').click()">ファイルを選択</button>
  <input type="file" id="ra-file-input-ja" accept="image/*">
</div>

<!-- Preview -->
<div class="ra-card">
  <h3>プレビュー</h3>
  <div id="ra-preview-area-ja">
    <div class="ra-placeholder">
      <span class="ra-placeholder-icon">📂</span>
      画像をアップロードするとプレビューが表示されます
    </div>
  </div>
</div>

<!-- Dimensions -->
<div class="ra-card">
  <h3>サイズ指定</h3>
  <div class="ra-dim-row">
    <div class="ra-dim-field">
      <label for="ra-width-ja">幅（px）</label>
      <input type="number" class="ra-dim-input" id="ra-width-ja" min="1" max="8000" placeholder="例：1200">
    </div>
    <button class="ra-lock-btn locked" id="ra-lock-btn-ja" title="アスペクト比ロック切替">🔒</button>
    <div class="ra-dim-field">
      <label for="ra-height-ja">高さ（px）</label>
      <input type="number" class="ra-dim-input" id="ra-height-ja" min="1" max="8000" placeholder="例：630">
    </div>
  </div>
</div>

<!-- Presets -->
<div class="ra-card">
  <h3>プリセットサイズ</h3>
  <div class="ra-preset-grid" id="ra-preset-grid-ja">
    <button class="ra-preset-btn" data-w="1200" data-h="630">
      <span class="ra-preset-name">SNSヘッダー / OG画像</span>
      <span class="ra-preset-size">1200 × 630 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1080" data-h="1080">
      <span class="ra-preset-name">Instagramスクエア</span>
      <span class="ra-preset-size">1080 × 1080 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1280" data-h="720">
      <span class="ra-preset-name">YouTubeサムネイル</span>
      <span class="ra-preset-size">1280 × 720 px</span>
    </button>
    <button class="ra-preset-btn" data-w="400" data-h="400">
      <span class="ra-preset-name">プロフィール画像</span>
      <span class="ra-preset-size">400 × 400 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1080" data-h="1920">
      <span class="ra-preset-name">Instagramストーリー</span>
      <span class="ra-preset-size">1080 × 1920 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1500" data-h="500">
      <span class="ra-preset-name">Twitterヘッダー</span>
      <span class="ra-preset-size">1500 × 500 px</span>
    </button>
    <button class="ra-preset-btn" data-w="800" data-h="800">
      <span class="ra-preset-name">ブログサムネイル</span>
      <span class="ra-preset-size">800 × 800 px</span>
    </button>
    <button class="ra-preset-btn" data-w="1920" data-h="1080">
      <span class="ra-preset-name">フルHD</span>
      <span class="ra-preset-size">1920 × 1080 px</span>
    </button>
  </div>
</div>

<!-- Quality & Format -->
<div class="ra-card">
  <h3>出力設定</h3>
  <div class="ra-settings-row">
    <div class="ra-setting-group">
      <label>画質（JPEG / WebP）</label>
      <div class="ra-quality-wrap">
        <input type="range" class="ra-quality-slider" id="ra-quality-ja" min="10" max="100" value="85">
        <span class="ra-quality-val" id="ra-quality-val-ja">85%</span>
      </div>
    </div>
    <div class="ra-setting-group">
      <label>出力フォーマット</label>
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
  <h3>ファイルサイズ比較</h3>
  <div class="ra-size-comparison">
    <div class="ra-size-box original">
      <div class="ra-size-box-label">元のサイズ</div>
      <div class="ra-size-box-value" id="ra-orig-size-ja">—</div>
      <div class="ra-size-box-sub" id="ra-orig-dim-ja">画像をアップロード</div>
    </div>
    <div class="ra-size-box output">
      <div class="ra-size-box-label">出力サイズ（推定）</div>
      <div class="ra-size-box-value" id="ra-out-size-ja">—</div>
      <div class="ra-size-box-sub" id="ra-out-dim-ja">—</div>
    </div>
    <div class="ra-size-box savings">
      <div class="ra-size-box-label">削減サイズ</div>
      <div class="ra-size-box-value" id="ra-savings-ja">—</div>
      <div class="ra-size-box-sub" id="ra-savings-pct-ja">—</div>
    </div>
  </div>
</div>

<!-- Download -->
<div class="ra-card">
  <button class="ra-download-btn" id="ra-download-btn-ja" disabled>リサイズした画像をダウンロード</button>
</div>

<canvas id="ra-canvas-ja"></canvas>

<script>
(function() {
  var img = null;
  var origFile = null;
  var origWidth = 0, origHeight = 0;
  var aspectRatio = 1;
  var locked = true;
  var fmt = 'image/jpeg';
  var updatingDim = false;

  var dropzone     = document.getElementById('ra-dropzone-ja');
  var fileInput    = document.getElementById('ra-file-input-ja');
  var previewArea  = document.getElementById('ra-preview-area-ja');
  var widthInput   = document.getElementById('ra-width-ja');
  var heightInput  = document.getElementById('ra-height-ja');
  var lockBtn      = document.getElementById('ra-lock-btn-ja');
  var qualitySlider= document.getElementById('ra-quality-ja');
  var qualityVal   = document.getElementById('ra-quality-val-ja');
  var origSizeEl   = document.getElementById('ra-orig-size-ja');
  var origDimEl    = document.getElementById('ra-orig-dim-ja');
  var outSizeEl    = document.getElementById('ra-out-size-ja');
  var outDimEl     = document.getElementById('ra-out-dim-ja');
  var savingsEl    = document.getElementById('ra-savings-ja');
  var savingsPctEl = document.getElementById('ra-savings-pct-ja');
  var downloadBtn  = document.getElementById('ra-download-btn-ja');
  var canvas       = document.getElementById('ra-canvas-ja');
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

  function loadFile(file) {
    if (file.size > 20 * 1024 * 1024) {
      alert('ファイルが大きすぎます。20MB以下の画像を使用してください。');
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

  function renderPreview() {
    var w = parseInt(widthInput.value) || origWidth;
    var h = parseInt(heightInput.value) || origHeight;

    canvas.width  = w;
    canvas.height = h;
    ctx.clearRect(0, 0, w, h);
    if (img) ctx.drawImage(img, 0, 0, w, h);

    var origSrc = img.src;
    var outSrc  = canvas.toDataURL(fmt, parseInt(qualitySlider.value) / 100);

    previewArea.innerHTML =
      '<div class="ra-preview-wrap">' +
        '<div class="ra-preview-box">' +
          '<div class="ra-preview-label">変換前（' + origWidth + ' x ' + origHeight + '）</div>' +
          '<div class="ra-preview-img-wrap"><img src="' + origSrc + '" alt="元画像"></div>' +
          '<div class="ra-preview-info">' + formatBytes(origFile ? origFile.size : 0) + '</div>' +
        '</div>' +
        '<div class="ra-preview-box">' +
          '<div class="ra-preview-label">変換後（' + w + ' x ' + h + '）</div>' +
          '<div class="ra-preview-img-wrap"><img src="' + outSrc + '" alt="リサイズ後"></div>' +
          '<div class="ra-preview-info">' + formatBytes(estimateSize(outSrc)) + '</div>' +
        '</div>' +
      '</div>';
  }

  function estimateSize(dataUrl) {
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
    var outUrl   = canvas.toDataURL(fmt, q);
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
      savingsPctEl.textContent = pct + '% 削減';
      savingsEl.style.color    = '#dc2626';
    } else {
      savingsEl.textContent    = '+' + formatBytes(Math.abs(saved));
      savingsPctEl.textContent = Math.abs(pct) + '% 増加';
      savingsEl.style.color    = '#059669';
    }
  }

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

  lockBtn.addEventListener('click', function() {
    locked = !locked;
    lockBtn.textContent = locked ? '🔒' : '🔓';
    lockBtn.classList.toggle('locked', locked);
    if (locked && img) {
      aspectRatio = (parseInt(widthInput.value) || origWidth) / (parseInt(heightInput.value) || origHeight);
    }
  });

  document.getElementById('ra-preset-grid-ja').addEventListener('click', function(e) {
    var btn = e.target.closest('.ra-preset-btn');
    if (!btn) return;
    var w = parseInt(btn.getAttribute('data-w'));
    var h = parseInt(btn.getAttribute('data-h'));
    widthInput.value  = w;
    heightInput.value = h;
    aspectRatio = w / h;
    if (img) { renderPreview(); updateSizes(); }
  });

  qualitySlider.addEventListener('input', function() {
    qualityVal.textContent = qualitySlider.value + '%';
    if (img) { renderPreview(); updateSizes(); }
  });

  document.querySelectorAll('.ra-format-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      document.querySelectorAll('.ra-format-btn').forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      fmt = btn.getAttribute('data-fmt');
      if (img) { renderPreview(); updateSizes(); }
    });
  });

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

## 使い方

**STEP 1 — 画像をアップロード**: ドラッグ＆ドロップするか、「ファイルを選択」から画像を選びます。JPG・PNG・WebP・GIF・BMP（最大20MB）に対応しています。

**STEP 2 — サイズを指定**: 幅・高さをピクセルで入力します。🔒アイコンをクリックするとアスペクト比ロックのON/OFFを切り替えられます。プリセットボタンをクリックすれば、よく使うサイズに一発変換。

**STEP 3 — 出力設定**: JPEG・PNG・WebPから出力フォーマットを選び、画質スライダー（10〜100%）で圧縮率を調整します。PNGは可逆圧縮のため画質設定はJPEG・WebPのみ有効です。

**STEP 4 — サイズ確認**: 変換前後のファイルサイズと削減量を確認できます。プレビューで視覚的に品質を確かめてからダウンロードしましょう。

**STEP 5 — ダウンロード**: 「リサイズした画像をダウンロード」をクリックして保存します。

## SNS別・推奨画像サイズ（2025年版）

| プラットフォーム | 推奨サイズ |
|---|---|
| OGP / Facebook シェア画像 | 1200 × 630 px |
| Instagram スクエア投稿 | 1080 × 1080 px |
| Instagram / TikTok ストーリー | 1080 × 1920 px |
| YouTube サムネイル | 1280 × 720 px |
| Twitter / X ヘッダー | 1500 × 500 px |
| プロフィール・アイコン | 400 × 400 px |

上記はすべてプリセットとして登録済みです。ボタンをクリックするだけで即座に適用できます。

## フォーマットの選び方

**JPEG** は写真や複雑な色のある画像に最適。ファイルサイズが小さく、Web表示に向いています。画質80〜85%が品質とサイズのバランス点です。

**PNG** はスクリーンショット、ロゴ、テキスト入り画像、透過画像に最適。可逆圧縮のため劣化なし。ただしJPEGよりファイルサイズは大きくなります。

**WebP** はGoogleが開発した次世代フォーマット。同等品質でJPEGより30〜40%小さいことが多く、主要ブラウザすべてで対応済み。Web用途に最も推奨されます。

---

## 関連ツール

> QRコードを生成してマーケティング素材やURLを共有 → [QRコードジェネレーター](/ja/tools/qr-code-generator/)

> 画面の解像度・ビューポートサイズを確認 → [画面解像度チェッカー](/ja/tools/screen-resolution/)

> デザインに使う色を選択・変換 → [カラーピッカー](/ja/tools/color-picker/)

---

**画像管理もfreeeで効率化**
ブログやSNSの画像を編集している方、経費管理もfreeeで一括管理しませんか？
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
