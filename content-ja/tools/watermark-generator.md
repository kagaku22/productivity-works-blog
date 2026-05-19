---
title: "ウォーターマークジェネレーター"
date: 2025-05-08
description: "無料の透かし画像作成ツール。写真にテキスト透かしを追加。フォント・サイズ・色・透明度・位置をカスタマイズ。PNGダウンロード対応。著作権保護に。"
categories: ["無料ツール"]
tags: ["ウォーターマーク", "透かし画像", "著作権保護", "画像加工", "無料ツール"]
slug: "watermark-generator"
cover:
  image: "/images/covers/watermark-generator-ja.png"
  alt: "ウォーターマークジェネレーター"
ShowToc: false
---

<div id="wm-app">

<style>
#wm-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 48px 0;
color: #1a202c;
}

#wm-app * {
box-sizing: border-box;
}

/* Hero */
.wm-hero {
background: linear-gradient(135deg, #0369a1 0%, #0284c7 50%, #0ea5e9 100%);
border-radius: 16px;
padding: 32px 28px;
margin-bottom: 24px;
color: #fff;
}

.wm-hero h2 {
margin: 0 0 6px 0;
font-size: 22px;
font-weight: 800;
}

.wm-hero p {
margin: 0;
font-size: 14px;
opacity: 0.88;
line-height: 1.7;
}

/* Drop Zone */
.wm-dropzone {
border: 3px dashed #0369a1;
border-radius: 14px;
padding: 48px 24px;
text-align: center;
background: #f0f9ff;
cursor: pointer;
transition: background 0.2s, border-color 0.2s;
margin-bottom: 24px;
}

.wm-dropzone:hover,
.wm-dropzone.wm-drag-over {
background: #e0f2fe;
border-color: #0284c7;
}

.wm-dropzone-icon {
font-size: 48px;
margin-bottom: 12px;
}

.wm-dropzone h3 {
margin: 0 0 6px 0;
font-size: 17px;
font-weight: 700;
color: #0c4a6e;
}

.wm-dropzone p {
margin: 0;
font-size: 13px;
color: #0369a1;
}

/* Editor layout */
.wm-editor {
display: none;
}

.wm-editor.wm-visible {
display: block;
}

.wm-canvas-wrap {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 14px;
padding: 16px;
margin-bottom: 20px;
text-align: center;
overflow: auto;
}

#wm-canvas {
max-width: 100%;
border-radius: 8px;
box-shadow: 0 4px 20px rgba(0,0,0,0.12);
display: block;
margin: 0 auto;
}

/* Controls panel */
.wm-panel {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 14px;
padding: 24px;
margin-bottom: 20px;
}

.wm-panel h3 {
margin: 0 0 16px 0;
font-size: 15px;
font-weight: 700;
color: #0c4a6e;
border-bottom: 2px solid #e0f2fe;
padding-bottom: 8px;
}

.wm-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 14px;
}

@media (max-width: 600px) {
.wm-grid {
grid-template-columns: 1fr;
}
}

.wm-field {
display: flex;
flex-direction: column;
gap: 5px;
}

.wm-field.wm-full {
grid-column: 1 / -1;
}

.wm-field label {
font-size: 12px;
font-weight: 600;
color: #374151;
letter-spacing: 0.02em;
}

.wm-field input[type="text"],
.wm-field input[type="number"],
.wm-field select {
padding: 8px 10px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 14px;
color: #1a202c;
background: #fff;
transition: border-color 0.2s;
width: 100%;
font-family: inherit;
}

.wm-field input[type="text"]:focus,
.wm-field input[type="number"]:focus,
.wm-field select:focus {
outline: none;
border-color: #0369a1;
}

.wm-range-row {
display: flex;
align-items: center;
gap: 10px;
}

.wm-range-row input[type="range"] {
flex: 1;
accent-color: #0369a1;
}

.wm-range-val {
font-size: 13px;
font-weight: 700;
color: #0369a1;
min-width: 40px;
text-align: right;
}

.wm-color-row {
display: flex;
align-items: center;
gap: 10px;
}

.wm-color-row input[type="color"] {
width: 42px;
height: 36px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
padding: 2px;
cursor: pointer;
background: #fff;
}

.wm-color-row input[type="text"] {
flex: 1;
padding: 8px 10px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 14px;
color: #1a202c;
}

/* Position grid */
.wm-pos-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 6px;
}

.wm-pos-btn {
padding: 8px 4px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
background: #fff;
font-size: 11px;
color: #374151;
cursor: pointer;
transition: all 0.15s;
text-align: center;
font-weight: 600;
font-family: inherit;
}

.wm-pos-btn:hover {
border-color: #0369a1;
background: #f0f9ff;
color: #0369a1;
}

.wm-pos-btn.wm-pos-active {
border-color: #0369a1;
background: #0369a1;
color: #fff;
}

/* Toggle */
.wm-toggle-row {
display: flex;
align-items: center;
gap: 10px;
}

.wm-toggle {
position: relative;
width: 44px;
height: 24px;
flex-shrink: 0;
}

.wm-toggle input {
opacity: 0;
width: 0;
height: 0;
}

.wm-toggle-slider {
position: absolute;
inset: 0;
background: #d1d5db;
border-radius: 24px;
cursor: pointer;
transition: background 0.2s;
}

.wm-toggle-slider::before {
content: '';
position: absolute;
width: 18px;
height: 18px;
left: 3px;
top: 3px;
background: #fff;
border-radius: 50%;
transition: transform 0.2s;
}

.wm-toggle input:checked + .wm-toggle-slider {
background: #0369a1;
}

.wm-toggle input:checked + .wm-toggle-slider::before {
transform: translateX(20px);
}

.wm-toggle-label {
font-size: 13px;
color: #374151;
font-weight: 600;
}

/* Actions */
.wm-actions {
display: flex;
gap: 12px;
flex-wrap: wrap;
}

.wm-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 11px 22px;
border-radius: 10px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
border: none;
transition: all 0.18s;
text-decoration: none;
font-family: inherit;
}

.wm-btn-primary {
background: #0369a1;
color: #fff;
}

.wm-btn-primary:hover {
background: #0284c7;
transform: translateY(-1px);
box-shadow: 0 4px 12px rgba(3,105,161,0.3);
}

.wm-btn-secondary {
background: #f1f5f9;
color: #374151;
border: 1.5px solid #d1d5db;
}

.wm-btn-secondary:hover {
background: #e2e8f0;
}
</style>

<div class="wm-hero">
<h2>ウォーターマークジェネレーター</h2>
<p>画像をアップロードし、テキスト透かし（フォント・サイズ・色・透明度・位置・角度）をカスタマイズしてPNGでダウンロード。登録不要・サーバー送信なし。ブラウザ完結で安心。</p>
</div>

<!-- Drop Zone -->
<div class="wm-dropzone" id="wm-dropzone">
<div class="wm-dropzone-icon">🖼️</div>
<h3>画像をここにドロップ</h3>
<p>またはクリックして選択 &mdash; JPG / PNG / GIF / WebP 対応</p>
<input type="file" id="wm-file-input" accept="image/*" style="display:none">
</div>

<!-- Editor -->
<div class="wm-editor" id="wm-editor">

<!-- Canvas Preview -->
<div class="wm-canvas-wrap">
<canvas id="wm-canvas"></canvas>
</div>

<!-- Watermark Text -->
<div class="wm-panel">
<h3>透かしテキスト設定</h3>
<div class="wm-grid">
<div class="wm-field wm-full">
<label>透かしテキスト</label>
<input type="text" id="wm-text" value="© あなたの名前" placeholder="透かしに表示するテキスト">
</div>
<div class="wm-field">
<label>フォントサイズ (px)</label>
<div class="wm-range-row">
<input type="range" id="wm-fontsize" min="8" max="200" value="36">
<span class="wm-range-val" id="wm-fontsize-val">36</span>
</div>
</div>
<div class="wm-field">
<label>フォント</label>
<select id="wm-font">
<option value="Arial">Arial</option>
<option value="Georgia">Georgia</option>
<option value="Times New Roman">Times New Roman</option>
<option value="Courier New">Courier New</option>
<option value="Verdana">Verdana</option>
<option value="Impact">Impact</option>
<option value="Trebuchet MS">Trebuchet MS</option>
<option value="Palatino">Palatino</option>
</select>
</div>
<div class="wm-field">
<label>テキストカラー</label>
<div class="wm-color-row">
<input type="color" id="wm-color-picker" value="#ffffff">
<input type="text" id="wm-color-hex" value="#ffffff" placeholder="#ffffff">
</div>
</div>
<div class="wm-field">
<label>不透明度 (%)</label>
<div class="wm-range-row">
<input type="range" id="wm-opacity" min="0" max="100" value="50">
<span class="wm-range-val" id="wm-opacity-val">50%</span>
</div>
</div>
<div class="wm-field">
<label>回転角度 (deg)</label>
<div class="wm-range-row">
<input type="range" id="wm-rotation" min="-180" max="180" value="-30">
<span class="wm-range-val" id="wm-rotation-val">-30°</span>
</div>
</div>
</div>
</div>

<!-- Position & Repeat -->
<div class="wm-panel">
<h3>位置・タイル設定</h3>
<div class="wm-grid">
<div class="wm-field">
<label>表示位置（単体）</label>
<div class="wm-pos-grid" id="wm-pos-grid">
<button class="wm-pos-btn" data-pos="top-left">左上</button>
<button class="wm-pos-btn" data-pos="top-center">上中央</button>
<button class="wm-pos-btn" data-pos="top-right">右上</button>
<button class="wm-pos-btn" data-pos="middle-left">左中</button>
<button class="wm-pos-btn wm-pos-active" data-pos="center">中央</button>
<button class="wm-pos-btn" data-pos="middle-right">右中</button>
<button class="wm-pos-btn" data-pos="bottom-left">左下</button>
<button class="wm-pos-btn" data-pos="bottom-center">下中央</button>
<button class="wm-pos-btn" data-pos="bottom-right">右下</button>
</div>
</div>
<div class="wm-field">
<label>繰り返し（タイル）</label>
<div class="wm-toggle-row" style="margin-bottom:14px">
<label class="wm-toggle">
<input type="checkbox" id="wm-repeat">
<span class="wm-toggle-slider"></span>
</label>
<span class="wm-toggle-label">画像全体にタイル表示</span>
</div>
<label>タイル間隔 (px)</label>
<div class="wm-range-row" style="margin-top:6px">
<input type="range" id="wm-spacing" min="20" max="400" value="150">
<span class="wm-range-val" id="wm-spacing-val">150</span>
</div>
</div>
</div>
</div>

<!-- Actions -->
<div class="wm-actions">
<button class="wm-btn wm-btn-primary" id="wm-download">&#8595; PNGでダウンロード</button>
<button class="wm-btn wm-btn-secondary" id="wm-new">別の画像を使う</button>
</div>

</div>

<script>
(function () {
'use strict';

var dropzone = document.getElementById('wm-dropzone');
var fileInput = document.getElementById('wm-file-input');
var editor = document.getElementById('wm-editor');
var canvas = document.getElementById('wm-canvas');
var ctx = canvas.getContext('2d');

var textInput = document.getElementById('wm-text');
var fontsizeInput = document.getElementById('wm-fontsize');
var fontsizeVal = document.getElementById('wm-fontsize-val');
var fontSelect = document.getElementById('wm-font');
var colorPicker = document.getElementById('wm-color-picker');
var colorHex = document.getElementById('wm-color-hex');
var opacityInput = document.getElementById('wm-opacity');
var opacityVal = document.getElementById('wm-opacity-val');
var rotationInput = document.getElementById('wm-rotation');
var rotationVal = document.getElementById('wm-rotation-val');
var repeatChk = document.getElementById('wm-repeat');
var spacingInput = document.getElementById('wm-spacing');
var spacingVal = document.getElementById('wm-spacing-val');
var posGrid = document.getElementById('wm-pos-grid');
var downloadBtn = document.getElementById('wm-download');
var newBtn = document.getElementById('wm-new');

var sourceImg = null;
var currentPos = 'center';

// Drag & drop
dropzone.addEventListener('dragover', function (e) {
e.preventDefault();
dropzone.classList.add('wm-drag-over');
});

dropzone.addEventListener('dragleave', function () {
dropzone.classList.remove('wm-drag-over');
});

dropzone.addEventListener('drop', function (e) {
e.preventDefault();
dropzone.classList.remove('wm-drag-over');
var file = e.dataTransfer.files[0];
if (file && file.type.startsWith('image/')) loadFile(file);
});

dropzone.addEventListener('click', function () {
fileInput.click();
});

fileInput.addEventListener('change', function () {
if (fileInput.files[0]) loadFile(fileInput.files[0]);
});

function loadFile(file) {
var reader = new FileReader();
reader.onload = function (e) {
var img = new Image();
img.onload = function () {
sourceImg = img;
canvas.width = img.naturalWidth;
canvas.height = img.naturalHeight;
dropzone.style.display = 'none';
editor.classList.add('wm-visible');
render();
};
img.src = e.target.result;
};
reader.readAsDataURL(file);
}

// Position buttons
posGrid.querySelectorAll('.wm-pos-btn').forEach(function (btn) {
btn.addEventListener('click', function () {
posGrid.querySelectorAll('.wm-pos-btn').forEach(function (b) {
b.classList.remove('wm-pos-active');
});
btn.classList.add('wm-pos-active');
currentPos = btn.dataset.pos;
render();
});
});

// Live controls
[textInput, fontSelect, repeatChk].forEach(function (el) {
el.addEventListener('input', render);
el.addEventListener('change', render);
});

function bindRange(input, display, suffix) {
input.addEventListener('input', function () {
display.textContent = input.value + (suffix || '');
render();
});
}

bindRange(fontsizeInput, fontsizeVal, '');
bindRange(opacityInput, opacityVal, '%');
bindRange(rotationInput, rotationVal, '°');
bindRange(spacingInput, spacingVal, '');

colorPicker.addEventListener('input', function () {
colorHex.value = colorPicker.value;
render();
});

colorHex.addEventListener('input', function () {
var hex = colorHex.value.trim();
if (/^#[0-9a-fA-F]{6}$/.test(hex)) {
colorPicker.value = hex;
}
render();
});

function hexToRgb(hex) {
var r = parseInt(hex.slice(1, 3), 16);
var g = parseInt(hex.slice(3, 5), 16);
var b = parseInt(hex.slice(5, 7), 16);
return { r: r, g: g, b: b };
}

function getPosition(pos, cw, ch, tw, th) {
var padding = 20;
var x, y;
switch (pos) {
case 'top-left':     x = padding;          y = padding + th; break;
case 'top-center':   x = cw / 2;           y = padding + th; break;
case 'top-right':    x = cw - padding;     y = padding + th; break;
case 'middle-left':  x = padding;          y = ch / 2; break;
case 'center':       x = cw / 2;           y = ch / 2; break;
case 'middle-right': x = cw - padding;     y = ch / 2; break;
case 'bottom-left':  x = padding;          y = ch - padding; break;
case 'bottom-center':x = cw / 2;           y = ch - padding; break;
case 'bottom-right': x = cw - padding;     y = ch - padding; break;
default:             x = cw / 2;           y = ch / 2;
}
return { x: x, y: y };
}

function render() {
if (!sourceImg) return;

var cw = canvas.width;
var ch = canvas.height;

ctx.clearRect(0, 0, cw, ch);
ctx.drawImage(sourceImg, 0, 0, cw, ch);

var text = textInput.value || '© ウォーターマーク';
var fontSize = parseInt(fontsizeInput.value, 10);
var font = fontSelect.value;
var opacity = parseInt(opacityInput.value, 10) / 100;
var rotation = parseInt(rotationInput.value, 10) * Math.PI / 180;
var tileRepeat = repeatChk.checked;
var spacing = parseInt(spacingInput.value, 10);

var hex = colorHex.value.trim();
if (!/^#[0-9a-fA-F]{6}$/.test(hex)) hex = '#ffffff';
var rgb = hexToRgb(hex);

ctx.font = 'bold ' + fontSize + 'px ' + font;
ctx.fillStyle = 'rgba(' + rgb.r + ',' + rgb.g + ',' + rgb.b + ',' + opacity + ')';
ctx.textBaseline = 'middle';

if (tileRepeat) {
var step = spacing;
for (var ty = -ch; ty < ch * 2; ty += step) {
for (var tx = -cw; tx < cw * 2; tx += step) {
ctx.save();
ctx.translate(tx, ty);
ctx.rotate(rotation);
ctx.fillText(text, 0, 0);
ctx.restore();
}
}
} else {
var metrics = ctx.measureText(text);
var tw = metrics.width;
var th = fontSize;
var pos = getPosition(currentPos, cw, ch, tw, th);
ctx.save();
ctx.translate(pos.x, pos.y);
ctx.rotate(rotation);
if (currentPos.indexOf('left') !== -1) {
ctx.textAlign = 'left';
} else if (currentPos.indexOf('right') !== -1) {
ctx.textAlign = 'right';
} else {
ctx.textAlign = 'center';
}
ctx.fillText(text, 0, 0);
ctx.restore();
}
}

// Download
downloadBtn.addEventListener('click', function () {
if (!canvas) return;
var link = document.createElement('a');
link.download = 'watermarked-image.png';
link.href = canvas.toDataURL('image/png');
link.click();
});

// New image
newBtn.addEventListener('click', function () {
editor.classList.remove('wm-visible');
dropzone.style.display = '';
fileInput.value = '';
sourceImg = null;
});

})();
</script>

---

## 関連ツール

> 画像を指定サイズにリサイズ → [画像リサイザー](/ja/tools/image-resizer/)

> Instagram風フィルターを適用 → [写真フィルター](/ja/tools/photo-filter/)

> プレースホルダー画像を生成 → [プレースホルダー画像](/ja/tools/placeholder-image/)

---

**個人事業主・フリーランスの会計をもっとかんたんに**

写真・デザイン素材の販売や制作を仕事にされている方。freee会計で帳簿・確定申告をまるっと効率化しませんか？

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">

</div>
