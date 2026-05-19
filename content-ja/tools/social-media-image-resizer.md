---
title: "SNS画像リサイズツール"
date: 2025-04-20
description: "無料のSNS画像リサイズツール。Instagram・Facebook・X(Twitter)・LinkedIn・YouTube・Pinterest用に画像を最適サイズにリサイズ。トリミング・ダウンロード対応。"
categories: ["無料ツール"]
tags: ["SNS画像リサイズ", "インスタグラム画像サイズ", "フェイスブック画像", "X画像サイズ", "画像トリミング", "無料ツール"]
slug: "social-media-image-resizer"
cover:
  image: "/images/covers/social-media-image-resizer-ja.png"
  alt: "SNS画像リサイズツール"
ShowToc: false
---

<div id="sr-app">

<style>
#sr-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', Roboto, sans-serif;
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
font-size: 22px;
font-weight: 800;
}

.sr-hero p {
margin: 0;
font-size: 14px;
opacity: 0.88;
line-height: 1.7;
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

#sr-file-input-ja {
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

#sr-canvas-ja {
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

/* freee CTA */
.sr-freee-cta {
background: linear-gradient(135deg, #e8f4fd 0%, #dbeafe 100%);
border: 2px solid #93c5fd;
border-radius: 14px;
padding: 20px 22px;
margin: 28px 0 8px 0;
display: flex;
align-items: flex-start;
gap: 14px;
}

.sr-freee-cta-icon {
font-size: 32px;
flex-shrink: 0;
margin-top: 2px;
}

.sr-freee-cta-body h3 {
margin: 0 0 6px 0;
font-size: 15px;
font-weight: 800;
color: #1e40af;
}

.sr-freee-cta-body p {
margin: 0 0 10px 0;
font-size: 13px;
color: #1e3a5f;
line-height: 1.6;
}

.sr-freee-link {
display: inline-block;
background: #2563eb;
color: #fff;
font-size: 13px;
font-weight: 700;
padding: 8px 18px;
border-radius: 8px;
text-decoration: none;
transition: background 0.15s;
}

.sr-freee-link:hover {
background: #1d4ed8;
color: #fff;
}
</style>

<div class="sr-hero">
<h2>SNS画像リサイズツール</h2>
<p>Instagram・Facebook・X(Twitter)・LinkedIn・YouTube・Pinterest の各サイズにワンクリック対応。プリセットを選んでドラッグでトリミング位置を調整、そのままダウンロード。画像はサーバーに送信されず、ブラウザ内で完結します。</p>
</div>

<!-- Upload -->
<div class="sr-upload" id="sr-upload-zone-ja">
<input type="file" id="sr-file-input-ja" accept="image/*">
<span class="sr-upload-icon">🖼️</span>
<div class="sr-upload-title">画像をドロップ、またはクリックして選択</div>
<div class="sr-upload-sub">JPG・PNG・WebP・GIF・BMP（最大30MB）</div>
</div>

<!-- Platform selector -->
<p class="sr-section-title">プラットフォーム</p>
<div class="sr-platforms" id="sr-platforms-ja">
<button class="sr-platform-btn active" data-platform="instagram">Instagram</button>
<button class="sr-platform-btn" data-platform="facebook">Facebook</button>
<button class="sr-platform-btn" data-platform="twitter">X (Twitter)</button>
<button class="sr-platform-btn" data-platform="linkedin">LinkedIn</button>
<button class="sr-platform-btn" data-platform="youtube">YouTube</button>
<button class="sr-platform-btn" data-platform="pinterest">Pinterest</button>
</div>

<!-- Preset grid -->
<div class="sr-presets" id="sr-preset-grid-ja"></div>

<!-- Controls -->
<div class="sr-controls">
<div class="sr-control-group">
<label class="sr-label" for="sr-fit-mode-ja">フィットモード</label>
<select class="sr-select" id="sr-fit-mode-ja">
<option value="cover">カバー（はみ出しトリミング）</option>
<option value="contain">コンテイン（レターボックス）</option>
<option value="stretch">ストレッチ（変形して全体表示）</option>
</select>
<span class="sr-hint">カバーは画像を拡大してフレームを埋めます。コンテインは余白をバーで補完。ストレッチは縦横比を無視します。</span>
</div>
<div class="sr-control-group">
<label class="sr-label">背景色（コンテインモード用）</label>
<div class="sr-color-row">
<input type="color" class="sr-color-swatch" id="sr-bg-color-ja" value="#ffffff">
<input type="text" class="sr-select" id="sr-bg-hex-ja" value="#ffffff" maxlength="7" placeholder="#ffffff">
</div>
<span class="sr-hint">コンテインモードで余白が生じる場合に使われる色です。</span>
</div>
</div>

<!-- Preview -->
<div class="sr-preview-wrap" id="sr-preview-wrap-ja">
<div class="sr-preview-label" id="sr-preview-label-ja">プレビュー — ドラッグで位置調整</div>
<div class="sr-canvas-container" id="sr-canvas-container-ja">
<canvas id="sr-canvas-ja"></canvas>
<span class="sr-drag-hint">ドラッグで位置調整</span>
</div>
</div>

<!-- Info bar -->
<div class="sr-info-bar" id="sr-info-bar-ja" style="display:none;">
<span id="sr-info-dim-ja" class="sr-info-badge">—</span>
<span id="sr-info-size-ja" class="sr-info-badge">— KB</span>
<span id="sr-info-orig-ja" style="margin-left:auto; font-size:12px;"></span>
</div>

<!-- Download row -->
<div class="sr-dl-row">
<button class="sr-dl-btn primary" id="sr-dl-btn-ja" disabled>⬇ 画像をダウンロード</button>
<div class="sr-fmt-toggle">
<button class="sr-fmt-btn active" data-fmt="image/png">PNG</button>
<button class="sr-fmt-btn" data-fmt="image/jpeg">JPEG</button>
</div>
</div>

<!-- freee CTA -->
<div class="sr-freee-cta">
<span class="sr-freee-cta-icon">💼</span>
<div class="sr-freee-cta-body">
<h3>SNS運用の経費管理はfreeeで</h3>
<p>広告費・素材費・外注費など、SNS運用にかかる費用をfreee会計でまとめて管理。確定申告や法人決算もスムーズに。</p>
<a class="sr-freee-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
</div>
</div>

<script>
(function() {
'use strict';

var PRESETS = {
instagram: [
{ name: '投稿（スクエア）', w: 1080, h: 1080 },
{ name: 'ストーリー',       w: 1080, h: 1920 },
{ name: 'リール',           w: 1080, h: 1920 },
{ name: 'プロフィール',     w: 320,  h: 320  }
],
facebook: [
{ name: '投稿',             w: 1200, h: 630  },
{ name: 'カバー',           w: 820,  h: 312  },
{ name: 'プロフィール',     w: 170,  h: 170  },
{ name: 'ストーリー',       w: 1080, h: 1920 }
],
twitter: [
{ name: '投稿',             w: 1600, h: 900  },
{ name: 'ヘッダー',         w: 1500, h: 500  },
{ name: 'プロフィール',     w: 400,  h: 400  }
],
linkedin: [
{ name: '投稿',             w: 1200, h: 627  },
{ name: 'カバー',           w: 1584, h: 396  },
{ name: 'プロフィール',     w: 400,  h: 400  }
],
youtube: [
{ name: 'サムネイル',       w: 1280, h: 720  },
{ name: 'チャンネルアート', w: 2560, h: 1440 }
],
pinterest: [
{ name: 'ピン',             w: 1000, h: 1500 }
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
offsetX: 0,
offsetY: 0,
dragging: false,
dragStartX: 0,
dragStartY: 0,
dragOffsetStartX: 0,
dragOffsetStartY: 0
};

var canvas = document.getElementById('sr-canvas-ja');
var ctx = canvas.getContext('2d');
var previewWrap = document.getElementById('sr-preview-wrap-ja');
var previewLabel = document.getElementById('sr-preview-label-ja');
var infoBar = document.getElementById('sr-info-bar-ja');
var infoSize = document.getElementById('sr-info-size-ja');
var infoDim = document.getElementById('sr-info-dim-ja');
var infoOrig = document.getElementById('sr-info-orig-ja');
var dlBtn = document.getElementById('sr-dl-btn-ja');
var fitSel = document.getElementById('sr-fit-mode-ja');
var bgColorPicker = document.getElementById('sr-bg-color-ja');
var bgHexInput = document.getElementById('sr-bg-hex-ja');
var container = document.getElementById('sr-canvas-container-ja');

function buildPresets() {
var grid = document.getElementById('sr-preset-grid-ja');
grid.innerHTML = '';
var list = PRESETS[state.platform];
list.forEach(function(p, i) {
var btn = document.createElement('button');
btn.className = 'sr-preset-btn' + (i === 0 ? ' active' : '');
btn.innerHTML = '<span class="sr-preset-name">' + p.name + '</span><span class="sr-preset-dim">' + p.w + ' × ' + p.h + '</span>';
btn.addEventListener('click', function() {
document.querySelectorAll('#sr-preset-grid-ja .sr-preset-btn').forEach(function(b) { b.classList.remove('active'); });
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
var scale = Math.max(scaleX, scaleY);
var dw = state.origW * scale;
var dh = state.origH * scale;
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
previewLabel.textContent = 'プレビュー — ' + tw + ' × ' + th + (state.fitMode === 'cover' ? '（ドラッグで位置調整）' : '');
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
infoSize.textContent = kb >= 1024 ? (kb / 1024).toFixed(1) + ' MB（推定）' : kb + ' KB（推定）';
infoOrig.textContent = '元画像: ' + state.origW + ' × ' + state.origH + ' px';
}

var uploadZone = document.getElementById('sr-upload-zone-ja');
var fileInput = document.getElementById('sr-file-input-ja');

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

document.getElementById('sr-platforms-ja').addEventListener('click', function(e) {
var btn = e.target.closest('.sr-platform-btn');
if (!btn) return;
document.querySelectorAll('#sr-platforms-ja .sr-platform-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
state.platform = btn.getAttribute('data-platform');
state.offsetX = 0;
state.offsetY = 0;
buildPresets();
render();
});

fitSel.addEventListener('change', function() {
state.fitMode = fitSel.value;
state.offsetX = 0;
state.offsetY = 0;
render();
});

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

document.querySelectorAll('#sr-app .sr-fmt-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#sr-app .sr-fmt-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
state.fmt = btn.getAttribute('data-fmt');
if (state.img) updateInfo();
});
});

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

dlBtn.addEventListener('click', function() {
if (!state.img) return;
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
a.download = state.platform + '-' + state.preset.name + '-' + tw + 'x' + th + '.' + ext;
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
});

buildPresets();

})();
</script>

</div>

## 使い方

**STEP 1 — 画像をアップロード**: ドラッグ＆ドロップ、またはクリックしてファイルを選択します。JPG・PNG・WebP・GIF・BMP（最大30MB）に対応しています。

**STEP 2 — プラットフォームを選ぶ**: 上部のタブからプラットフォームを選択し、フォーマットプリセットをクリックします。

**STEP 3 — フィットモードを選ぶ**: カバーは画像を拡大してフレームに収め、プレビューをドラッグして切り取り位置を調整できます。コンテインは画像全体を表示し余白を背景色で補完します。ストレッチは縦横比を無視して引き伸ばします。

**STEP 4 — 背景色を調整**: コンテインモードで余白が生じる場合は、カラーピッカーまたは16進数コードで色を指定します。

**STEP 5 — ダウンロード**: PNG またはJPEGを選択し「画像をダウンロード」をクリックします。ファイル名にはプラットフォーム名・フォーマット名・解像度が自動で付与されます。

## SNS別・推奨画像サイズ一覧（2025年版）

| プラットフォーム | フォーマット | サイズ |
|---|---|---|
| Instagram | 投稿（スクエア） | 1080 × 1080 |
| Instagram | ストーリー / リール | 1080 × 1920 |
| Instagram | プロフィール | 320 × 320 |
| Facebook | 投稿 | 1200 × 630 |
| Facebook | カバー | 820 × 312 |
| Facebook | ストーリー | 1080 × 1920 |
| X (Twitter) | 投稿 | 1600 × 900 |
| X (Twitter) | ヘッダー | 1500 × 500 |
| LinkedIn | 投稿 | 1200 × 627 |
| LinkedIn | カバー | 1584 × 396 |
| YouTube | サムネイル | 1280 × 720 |
| YouTube | チャンネルアート | 2560 × 1440 |
| Pinterest | ピン | 1000 × 1500 |

## フィットモードの使い分け

**カバー**は画像を拡大してフレームをぴったり埋め、はみ出た部分をトリミングします。プレビューをドラッグすることで、どの部分を切り取るか調整できます。SNS投稿の大半はこのモードが最適です。

**コンテイン**は画像全体がフレーム内に収まるよう縮小し、余白を指定した背景色で補完します。画像の全体を見せたい場合や、ロゴ・テキスト入り画像に適しています。

**ストレッチ**は縦横比を無視して画像を強制的に指定サイズに変形します。元画像が目標サイズと近い縦横比の場合は気になりにくいですが、一般的には非推奨です。

---

## 関連ツール

> 画像を任意のサイズにリサイズ → [画像リサイザー](/ja/tools/image-resizer/)

> 指定サイズのプレースホルダー画像を生成 → [プレースホルダー画像ジェネレーター](/ja/tools/placeholder-image/)

---

**画像管理もfreeeで効率化**
ブログやSNSの画像を編集している方、経費管理もfreeeで一括管理しませんか？
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
