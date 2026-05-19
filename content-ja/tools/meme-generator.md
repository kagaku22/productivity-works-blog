---
title: "ミーム画像ジェネレーター"
date: 2025-04-25
description: "無料のミーム画像作成ツール。画像をアップロードして上下にテキストを追加。フォントサイズ・色・縁取りをカスタマイズしてPNGでダウンロード。会員登録不要。"
categories: ["無料ツール"]
tags: ["ミームジェネレーター", "ミーム作成", "画像テキスト合成", "ミーム画像", "無料ツール"]
slug: "meme-generator"
cover:
  image: "/images/covers/meme-generator-ja.png"
  alt: "ミーム画像ジェネレーター"
ShowToc: false
---

<div id="mg-app">

<style>
#mg-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', Roboto, sans-serif;
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

#mg-file-input-ja {
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

#mg-canvas-ja {
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
<h2>無料ミーム画像ジェネレーター</h2>
<p>画像をアップロードして上下にテキストを追加するだけ。フォントサイズ・色・縁取りを自由にカスタマイズしてPNGでダウンロード。すべてブラウザ内で完結、アカウント不要。</p>
</div>

<!-- Drop Zone -->
<div class="mg-dropzone" id="mg-dropzone-ja">
<span class="mg-dropzone-icon">🖼️</span>
<div class="mg-dropzone-title">ここに画像をドラッグ＆ドロップ</div>
<div class="mg-dropzone-sub">JPG・PNG・GIF・WebP対応 · 最大20MB</div>
<button class="mg-browse-btn" onclick="document.getElementById('mg-file-input-ja').click()">ファイルを選択</button>
<input type="file" id="mg-file-input-ja" accept="image/*">
</div>

<!-- Canvas Preview -->
<div class="mg-card">
<h3>プレビュー</h3>
<div class="mg-canvas-wrap" id="mg-canvas-wrap-ja">
<div class="mg-placeholder" id="mg-placeholder-ja">
<span class="mg-placeholder-icon">🎭</span>
画像をアップロードするとプレビューが表示されます
</div>
<canvas id="mg-canvas-ja" style="display:none;"></canvas>
</div>
</div>

<!-- Text Inputs -->
<div class="mg-card">
<h3>ミームテキスト</h3>
<div class="mg-input-group">
<label for="mg-top-text-ja">上部テキスト</label>
<input type="text" class="mg-text-input" id="mg-top-text-ja" placeholder="上のテキストを入力" maxlength="120">
</div>
<div class="mg-input-group">
<label for="mg-bottom-text-ja">下部テキスト</label>
<input type="text" class="mg-text-input" id="mg-bottom-text-ja" placeholder="下のテキストを入力" maxlength="120">
</div>
</div>

<!-- Style Controls -->
<div class="mg-card">
<h3>スタイル設定</h3>
<div class="mg-controls-row">
<div class="mg-control-group">
<label for="mg-font-size-ja">フォントサイズ</label>
<div class="mg-slider-wrap">
<input type="range" class="mg-slider" id="mg-font-size-ja" min="16" max="120" value="52">
<span class="mg-slider-val" id="mg-font-size-val-ja">52px</span>
</div>
</div>
<div class="mg-control-group">
<label for="mg-outline-width-ja">縁取りの太さ</label>
<div class="mg-slider-wrap">
<input type="range" class="mg-slider" id="mg-outline-width-ja" min="0" max="20" value="4">
<span class="mg-slider-val" id="mg-outline-width-val-ja">4px</span>
</div>
</div>
</div>
<div class="mg-controls-row" style="margin-top:14px;">
<div class="mg-control-group">
<label>文字色</label>
<div class="mg-color-wrap">
<input type="color" class="mg-color-swatch" id="mg-text-color-ja" value="#ffffff">
<span class="mg-color-label-val" id="mg-text-color-val-ja">#ffffff</span>
</div>
</div>
<div class="mg-control-group">
<label>縁取り色</label>
<div class="mg-color-wrap">
<input type="color" class="mg-color-swatch" id="mg-outline-color-ja" value="#000000">
<span class="mg-color-label-val" id="mg-outline-color-val-ja">#000000</span>
</div>
</div>
<div class="mg-control-group">
<label>文字揃え</label>
<div class="mg-align-btns" id="mg-align-btns-ja">
<button class="mg-align-btn" data-align="left" title="左揃え">&#9664;</button>
<button class="mg-align-btn active" data-align="center" title="中央揃え">&#9632;</button>
<button class="mg-align-btn" data-align="right" title="右揃え">&#9654;</button>
</div>
</div>
</div>
</div>

<!-- Actions -->
<div class="mg-card">
<div class="mg-actions">
<button class="mg-download-btn" id="mg-download-btn-ja" disabled>PNGでダウンロード</button>
<button class="mg-reset-btn" id="mg-reset-btn-ja">リセット</button>
</div>
</div>

<script>
(function() {
var img = null;
var alignment = 'center';

var dropzone     = document.getElementById('mg-dropzone-ja');
var fileInput    = document.getElementById('mg-file-input-ja');
var canvas       = document.getElementById('mg-canvas-ja');
var placeholder  = document.getElementById('mg-placeholder-ja');
var ctx          = canvas.getContext('2d');
var topTextEl    = document.getElementById('mg-top-text-ja');
var botTextEl    = document.getElementById('mg-bottom-text-ja');
var fontSizeEl   = document.getElementById('mg-font-size-ja');
var fontSizeVal  = document.getElementById('mg-font-size-val-ja');
var outlineWEl   = document.getElementById('mg-outline-width-ja');
var outlineWVal  = document.getElementById('mg-outline-width-val-ja');
var textColorEl  = document.getElementById('mg-text-color-ja');
var textColorVal = document.getElementById('mg-text-color-val-ja');
var outColorEl   = document.getElementById('mg-outline-color-ja');
var outColorVal  = document.getElementById('mg-outline-color-val-ja');
var downloadBtn  = document.getElementById('mg-download-btn-ja');
var resetBtn     = document.getElementById('mg-reset-btn-ja');
var alignBtns    = document.getElementById('mg-align-btns-ja');

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
alert('ファイルが大きすぎます。20MB以下の画像を使用してください。');
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

var fontSize     = parseInt(fontSizeEl.value);
var outlineW     = parseInt(outlineWEl.value);
var textColor    = textColorEl.value;
var outlineColor = outColorEl.value;
var topText      = topTextEl.value;
var botText      = botTextEl.value;

var cw      = canvas.width;
var ch      = canvas.height;
var padding = Math.round(cw * 0.04);

ctx.font         = 'bold ' + fontSize + 'px Impact, "Arial Black", sans-serif';
ctx.textBaseline = 'top';
ctx.lineJoin     = 'round';
ctx.miterLimit   = 2;

var xPos;
if (alignment === 'left')       { ctx.textAlign = 'left';   xPos = padding; }
else if (alignment === 'right') { ctx.textAlign = 'right';  xPos = cw - padding; }
else                            { ctx.textAlign = 'center'; xPos = cw / 2; }

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
var words   = text.split(' ');
var lines   = [];
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

alignBtns.addEventListener('click', function(e) {
var btn = e.target.closest('.mg-align-btn');
if (!btn) return;
alignBtns.querySelectorAll('.mg-align-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
alignment = btn.getAttribute('data-align');
drawMeme();
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
alignBtns.querySelectorAll('.mg-align-btn').forEach(function(b) { b.classList.remove('active'); });
alignBtns.querySelector('.mg-align-btn[data-align="center"]').classList.add('active');
downloadBtn.disabled = true;
fileInput.value = '';
});

})();
</script>

</div>

## 使い方

**STEP 1 — 画像をアップロード**: ドラッグ＆ドロップ、または「ファイルを選択」から画像を選びます。JPG・PNG・GIF・WebP（最大20MB）に対応しています。

**STEP 2 — テキストを入力**: 上部・下部テキストフィールドに文字を入力します。入力と同時にプレビューがリアルタイムで更新されます。長いテキストは自動で折り返されます。

**STEP 3 — スタイルを調整**: フォントサイズ（16〜120px）、文字色、縁取り色、縁取りの太さをスライダーやカラーピッカーで設定します。定番のミームスタイルは「白文字＋黒縁取り」のデフォルト設定です。

**STEP 4 — 文字揃えを選択**: 左・中央（デフォルト）・右揃えを切り替えられます。上部テキスト・下部テキストの両方に適用されます。

**STEP 5 — ダウンロード**: 「PNGでダウンロード」をクリックして保存します。元画像のフル解像度でレンダリングされます。

## ミームを上手に作るコツ

**テキストは短く。** 定番ミームは1行3〜6単語程度のシンプルなフレーズが基本です。長すぎると読みにくくなります。

**縁取りを活用する。** 縁取り幅3〜6pxが多くの画像でバランスよく機能します。背景が暗い・複雑な場合は太めに、明るく単色な背景では細めに設定しましょう。

**フォントはImpact相当。** このツールはImpact（定番ミームフォント）を優先し、環境によってArial Blackにフォールバックします。

**フル解像度で出力。** ダウンロードされるPNGは元画像のピクセルサイズ通りに生成されるため、大きな画面でも鮮明です。

---

## 関連ツール

> テキスト追加前に画像サイズを調整 → [画像リサイザー](/ja/tools/image-resizer/)

> モックアップ用のダミー画像を即座に生成 → [プレースホルダー画像ジェネレーター](/ja/tools/placeholder-image/)

---

**ミーム作成もfreeeで経費管理もスマートに**
クリエイター・フリーランスの方へ。制作活動の経費管理はfreeeで自動化しませんか？
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
