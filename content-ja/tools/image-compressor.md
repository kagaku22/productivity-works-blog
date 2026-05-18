---
title: "画像圧縮ツール"
date: 2025-12-30
description: "無料の画像圧縮ツール。画質を維持しながらファイルサイズを削減。JPEG・PNG対応。品質調整・ビフォーアフター比較。"
categories: ["無料ツール"]
slug: "image-compressor"
ShowToc: false
cover:
  image: "/images/covers/image-compressor-ja.png"
  alt: "画像圧縮ツール"
---

無料のブラウザ完結型画像圧縮ツール — 画像はサーバーにアップロードされません。品質・フォーマットを調整してすぐにダウンロードできます。

<div id="ic-app">
<style>
#ic-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
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

<div id="ic-drop-zone" role="button" tabindex="0" aria-label="画像をアップロード">
  <svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="#aab" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
    <rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/>
    <polyline points="21 15 16 10 5 21"/>
  </svg>
  <p><strong>クリックまたはドラッグ＆ドロップ</strong>で画像を追加</p>
  <p style="margin-top:6px;font-size:0.83rem;color:#aaa;">JPEG · PNG · WebP · GIF · BMP 対応</p>
  <input type="file" id="ic-file-input" accept="image/*">
</div>

<div id="ic-error"></div>

<div id="ic-controls">
  <div class="ic-control-row">
    <span class="ic-label">品質</span>
    <input type="range" id="ic-quality-slider" min="1" max="100" value="80">
    <span id="ic-quality-val">80%</span>
  </div>
  <div class="ic-control-row">
    <span class="ic-label">出力フォーマット</span>
    <select id="ic-format-select">
      <option value="image/jpeg">JPEG</option>
      <option value="image/png">PNG</option>
      <option value="image/webp">WebP</option>
    </select>
  </div>
</div>

<button id="ic-compress-btn">画像を圧縮する</button>

<div id="ic-stats">
  <div class="ic-stat-card">
    <div class="ic-stat-label">元のサイズ</div>
    <div class="ic-stat-value" id="ic-orig-size">—</div>
  </div>
  <div class="ic-stat-card">
    <div class="ic-stat-label">圧縮後のサイズ</div>
    <div class="ic-stat-value" id="ic-comp-size">—</div>
  </div>
  <div class="ic-stat-card ic-reduction">
    <div class="ic-stat-label">削減率</div>
    <div class="ic-stat-value" id="ic-reduction">—</div>
  </div>
</div>

<div id="ic-preview-wrap">
  <div class="ic-preview-header">
    <span>圧縮前</span>
    <span style="border-radius:0 4px 4px 0;">圧縮後</span>
  </div>
  <div class="ic-previews">
    <img id="ic-img-orig" alt="圧縮前">
    <canvas id="ic-canvas-comp-preview"></canvas>
  </div>
</div>

<a id="ic-download-btn" download="compressed-image">圧縮画像をダウンロード</a>
<button id="ic-reset-btn">リセット / 別の画像をアップロード</button>

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
      showError('有効な画像ファイルを選択してください。');
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
      img.onerror = function() { showError('画像の読み込みに失敗しました。'); };
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
      if (!blob) { showError('圧縮に失敗しました。別のフォーマットをお試しください。'); return; }

      var origBytes = origFile.size;
      var compBytes = blob.size;
      var pct = origBytes > 0 ? ((1 - compBytes / origBytes) * 100) : 0;

      origSizeEl.textContent = fmtBytes(origBytes);
      compSizeEl.textContent = fmtBytes(compBytes);
      reductEl.textContent   = (pct > 0 ? '-' : '+') + Math.abs(pct).toFixed(1) + '%';

      stats.classList.add('ic-visible');

      canvasCompPrev.width  = w;
      canvasCompPrev.height = h;
      canvasCompPrev.getContext('2d').drawImage(canvasComp, 0, 0);
      canvasCompPrev.style.width  = '50%';
      canvasCompPrev.style.height = 'auto';

      previewWrap.classList.add('ic-visible');

      var url = URL.createObjectURL(blob);
      var ext = fmt === 'image/jpeg' ? 'jpg' : fmt === 'image/png' ? 'png' : 'webp';
      dlBtn.href = url;
      dlBtn.download = 'compressed-image.' + ext;
      dlBtn.classList.add('ic-visible');
      resetBtn.classList.add('ic-visible');
      compBtn.textContent = '再圧縮する';
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
    compBtn.textContent = '画像を圧縮する';
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

**仕組み：** 画像はお使いのデバイス内で処理され、サーバーには送信されません。ブラウザがHTML5 Canvasに画像を描画し、選択した品質レベルで`canvas.toBlob()`を使って再エンコードします。

**使い方のヒント：**
- 写真にはJPEGが最もファイルサイズを小さくできます。透過が必要な場合はPNGまたはWebPを選択してください。
- 品質75〜85%程度なら、多くの場合オリジナルと見分けがつきません。
- WebPはJPEGやPNGより高い圧縮率を実現できる場合があります。

---

**関連ツール**

> 画像リサイズ → [画像リサイズツール](/ja/tools/image-resizer/)

> 画像切り抜き → [画像クロッパー](/ja/tools/image-cropper/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

## 関連記事

- [無料AI画像生成ツール比較2026年版【目的別おすすめランキング】](/ja/posts/ai-画像生成-無料/)
- [AI画像生成おすすめツール比較2026年版【無料・有料・日本語対応】](/ja/posts/ai-gazou-seisei-tool-hikaku-2026/)
