---
title: "CSS clip-pathメーカー"
date: 2025-09-12
description: "無料のCSS clip-pathビジュアルエディター。ドラッグ操作でカスタムシェイプを作成、プリセットから選択、CSSコードを即コピー。"
categories: ["無料ツール"]
tags: ["CSS", "Webデザイン", "無料ツール"]
slug: "css-clip-path"
ShowToc: false
cover:
  image: "/images/covers/css-clip-path-ja.png"
  alt: "CSS clip-pathメーカー"
---

<div id="cp-app">

<style>
#cp-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 0 0 48px 0;
color: #374151;
}
#cp-app * { box-sizing: border-box; }

.cp-layout {
display: grid;
grid-template-columns: 1fr 320px;
gap: 20px;
align-items: start;
}
@media (max-width: 720px) {
.cp-layout { grid-template-columns: 1fr; }
}

/* キャンバスエリア */
.cp-canvas-wrap {
position: relative;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 14px;
overflow: hidden;
}
.cp-canvas-inner {
position: relative;
width: 100%;
aspect-ratio: 1 / 1;
max-height: 480px;
overflow: hidden;
}
#cp-canvas {
display: block;
width: 100%;
height: 100%;
touch-action: none;
cursor: crosshair;
}
.cp-canvas-label {
position: absolute;
bottom: 10px;
left: 50%;
transform: translateX(-50%);
background: rgba(0,0,0,0.5);
color: #fff;
font-size: 11px;
padding: 3px 10px;
border-radius: 20px;
pointer-events: none;
white-space: nowrap;
}

/* コントロールパネル */
.cp-panel {
display: flex;
flex-direction: column;
gap: 14px;
}

.cp-card {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 16px;
}
.cp-card h3 {
margin: 0 0 10px 0;
font-size: 13px;
font-weight: 700;
color: #1e293b;
text-transform: uppercase;
letter-spacing: 0.05em;
}

/* プリセット */
.cp-presets {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 7px;
}
.cp-preset-btn {
display: flex;
flex-direction: column;
align-items: center;
gap: 5px;
padding: 8px 4px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
cursor: pointer;
font-size: 11px;
color: #475569;
font-weight: 600;
transition: all 0.15s;
}
.cp-preset-btn:hover {
border-color: #6366f1;
color: #4f46e5;
background: #eef2ff;
}
.cp-preset-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4f46e5;
}

/* 背景コントロール */
.cp-bg-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 8px;
}
.cp-bg-row label {
font-size: 13px;
color: #374151;
font-weight: 500;
min-width: 80px;
}
.cp-color-input {
width: 40px;
height: 32px;
border: 1.5px solid #e2e8f0;
border-radius: 6px;
padding: 2px;
cursor: pointer;
background: none;
}
.cp-img-btn {
flex: 1;
padding: 6px 10px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
font-size: 12px;
cursor: pointer;
color: #475569;
font-weight: 600;
transition: all 0.15s;
}
.cp-img-btn:hover {
border-color: #6366f1;
color: #4f46e5;
}

/* CSS出力 */
.cp-output-box {
background: #1e293b;
border-radius: 10px;
padding: 14px 16px;
font-family: 'SFMono-Regular', Consolas, monospace;
font-size: 12.5px;
color: #a5f3fc;
line-height: 1.6;
word-break: break-all;
min-height: 56px;
}
.cp-copy-btn {
width: 100%;
margin-top: 10px;
padding: 11px;
background: linear-gradient(135deg, #6366f1, #8b5cf6);
color: #fff;
border: none;
border-radius: 9px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.15s;
}
.cp-copy-btn:hover { opacity: 0.9; }
.cp-copy-btn.copied {
background: linear-gradient(135deg, #10b981, #059669);
}

/* ポイント情報 */
.cp-point-info {
font-size: 12px;
color: #64748b;
margin-top: 6px;
text-align: center;
}

/* シェイプ情報 */
.cp-shape-info {
font-size: 12px;
color: #6366f1;
font-weight: 600;
background: #eef2ff;
border-radius: 6px;
padding: 6px 10px;
text-align: center;
}

/* リセットボタン */
.cp-reset-btn {
width: 100%;
padding: 9px;
background: #f1f5f9;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
color: #475569;
cursor: pointer;
transition: all 0.15s;
}
.cp-reset-btn:hover {
border-color: #cbd5e1;
background: #e2e8f0;
}
</style>

<div class="cp-layout">
<!-- 左: キャンバス -->
<div>
<div class="cp-canvas-wrap">
<div class="cp-canvas-inner">
<canvas id="cp-canvas"></canvas>
</div>
<div class="cp-canvas-label">ポイントをドラッグして形を変える</div>
</div>
<div class="cp-point-info" id="cp-point-info">シェイプの頂点をドラッグして変形。右クリックで頂点を削除。ダブルクリックで頂点を追加。</div>
</div>

<!-- 右: パネル -->
<div class="cp-panel">
<!-- プリセット -->
<div class="cp-card">
<h3>プリセット</h3>
<div class="cp-presets" id="cp-presets"></div>
</div>

<!-- プレビュー設定 -->
<div class="cp-card">
<h3>プレビュー設定</h3>
<div class="cp-bg-row">
<label>シェイプ色</label>
<input type="color" class="cp-color-input" id="cp-shape-color" value="#6366f1">
</div>
<div class="cp-bg-row">
<label>背景色</label>
<input type="color" class="cp-color-input" id="cp-bg-color" value="#e2e8f0">
</div>
<div class="cp-bg-row">
<label>画像</label>
<button class="cp-img-btn" id="cp-upload-btn">画像をアップロード</button>
<input type="file" id="cp-file-input" accept="image/*" style="display:none">
</div>
<button class="cp-reset-btn" id="cp-clear-img" style="display:none">画像を削除</button>
</div>

<!-- CSS出力 -->
<div class="cp-card">
<h3>CSS出力</h3>
<div class="cp-output-box" id="cp-output">clip-path: polygon(...);</div>
<button class="cp-copy-btn" id="cp-copy-btn">CSSをコピー</button>
</div>

<!-- シェイプ情報 -->
<div class="cp-shape-info" id="cp-shape-info">polygon · 0点</div>
<button class="cp-reset-btn" id="cp-reset-btn">プリセットに戻す</button>
</div>
</div>

<script>
(function() {
var PRESETS = {
circle: {
label: '円',
type: 'circle'
},
ellipse: {
label: '楕円',
type: 'ellipse'
},
triangle: {
label: '三角形',
points: [[50,5],[95,95],[5,95]]
},
diamond: {
label: 'ダイヤ',
points: [[50,5],[95,50],[50,95],[5,50]]
},
pentagon: {
label: '五角形',
points: (function() {
var pts = [];
for (var i = 0; i < 5; i++) {
var a = (i * 72 - 90) * Math.PI / 180;
pts.push([50 + 45 * Math.cos(a), 50 + 45 * Math.sin(a)]);
}
return pts;
})()
},
hexagon: {
label: '六角形',
points: (function() {
var pts = [];
for (var i = 0; i < 6; i++) {
var a = (i * 60 - 30) * Math.PI / 180;
pts.push([50 + 47 * Math.cos(a), 50 + 47 * Math.sin(a)]);
}
return pts;
})()
},
star: {
label: '星',
points: (function() {
var pts = [];
for (var i = 0; i < 10; i++) {
var a = (i * 36 - 90) * Math.PI / 180;
var r = i % 2 === 0 ? 47 : 20;
pts.push([50 + r * Math.cos(a), 50 + r * Math.sin(a)]);
}
return pts;
})()
},
arrow: {
label: '矢印',
points: [[0,35],[60,35],[60,15],[100,50],[60,85],[60,65],[0,65]]
},
cross: {
label: '十字',
points: [[33,0],[67,0],[67,33],[100,33],[100,67],[67,67],[67,100],[33,100],[33,67],[0,67],[0,33],[33,33]]
}
};

var canvas = document.getElementById('cp-canvas');
var ctx = canvas.getContext('2d');
var outputEl = document.getElementById('cp-output');
var copyBtn = document.getElementById('cp-copy-btn');
var resetBtn = document.getElementById('cp-reset-btn');
var shapeInfoEl = document.getElementById('cp-shape-info');
var pointInfoEl = document.getElementById('cp-point-info');
var shapeColorInput = document.getElementById('cp-shape-color');
var bgColorInput = document.getElementById('cp-bg-color');
var uploadBtn = document.getElementById('cp-upload-btn');
var fileInput = document.getElementById('cp-file-input');
var clearImgBtn = document.getElementById('cp-clear-img');

var points = [];
var activePreset = 'triangle';
var dragIndex = -1;
var shapeColor = '#6366f1';
var bgColor = '#e2e8f0';
var uploadedImage = null;
var currentType = 'polygon';

function resizeCanvas() {
var rect = canvas.parentElement.getBoundingClientRect();
var size = Math.min(rect.width, 480);
canvas.width = size;
canvas.height = size;
draw();
}

function toCanvasPx(px, py) {
return [px / 100 * canvas.width, py / 100 * canvas.height];
}

function fmt(n) { return Math.round(n * 10) / 10; }

function buildCSS() {
if (currentType === 'circle') return 'clip-path: circle(50% at 50% 50%);';
if (currentType === 'ellipse') return 'clip-path: ellipse(55% 35% at 50% 50%);';
if (points.length < 3) return 'clip-path: polygon(/* ポイントを追加 */);';
var pts = points.map(function(p) { return fmt(p[0]) + '% ' + fmt(p[1]) + '%'; }).join(', ');
return 'clip-path: polygon(' + pts + ');';
}

function updateOutput() {
var css = buildCSS();
outputEl.textContent = css;
var count = currentType === 'polygon' ? points.length + '点' : '';
shapeInfoEl.textContent = currentType + (count ? ' · ' + count : '');
}

function draw() {
var w = canvas.width, h = canvas.height;
ctx.clearRect(0, 0, w, h);

ctx.fillStyle = bgColor;
ctx.fillRect(0, 0, w, h);

var cs = 20;
for (var r = 0; r < h / cs; r++) {
for (var c = 0; c < w / cs; c++) {
if ((r + c) % 2 === 0) {
ctx.fillStyle = 'rgba(0,0,0,0.04)';
ctx.fillRect(c * cs, r * cs, cs, cs);
}
}
}

ctx.save();
if (currentType === 'circle') {
ctx.beginPath();
ctx.arc(w / 2, h / 2, Math.min(w, h) * 0.47, 0, Math.PI * 2);
ctx.clip();
} else if (currentType === 'ellipse') {
ctx.beginPath();
ctx.ellipse(w / 2, h / 2, w * 0.52, h * 0.34, 0, 0, Math.PI * 2);
ctx.clip();
} else if (points.length >= 3) {
ctx.beginPath();
var p0 = toCanvasPx(points[0][0], points[0][1]);
ctx.moveTo(p0[0], p0[1]);
for (var i = 1; i < points.length; i++) {
var pi = toCanvasPx(points[i][0], points[i][1]);
ctx.lineTo(pi[0], pi[1]);
}
ctx.closePath();
ctx.clip();
}

if (uploadedImage) {
var ar = uploadedImage.width / uploadedImage.height;
var dw = w, dh = h;
if (ar > 1) { dh = w / ar; } else { dw = h * ar; }
var dx = (w - dw) / 2, dy = (h - dh) / 2;
ctx.drawImage(uploadedImage, dx, dy, dw, dh);
} else {
ctx.fillStyle = shapeColor;
ctx.fillRect(0, 0, w, h);
}
ctx.restore();

if (currentType === 'polygon' && points.length >= 2) {
ctx.beginPath();
var q0 = toCanvasPx(points[0][0], points[0][1]);
ctx.moveTo(q0[0], q0[1]);
for (var j = 1; j < points.length; j++) {
var qj = toCanvasPx(points[j][0], points[j][1]);
ctx.lineTo(qj[0], qj[1]);
}
ctx.closePath();
ctx.strokeStyle = 'rgba(255,255,255,0.9)';
ctx.lineWidth = 1.5;
ctx.setLineDash([5, 4]);
ctx.stroke();
ctx.setLineDash([]);

for (var k = 0; k < points.length; k++) {
var cp = toCanvasPx(points[k][0], points[k][1]);
ctx.beginPath();
ctx.arc(cp[0], cp[1], dragIndex === k ? 10 : 7, 0, Math.PI * 2);
ctx.fillStyle = dragIndex === k ? '#f59e0b' : '#fff';
ctx.fill();
ctx.strokeStyle = dragIndex === k ? '#d97706' : '#6366f1';
ctx.lineWidth = 2;
ctx.stroke();
}
}

updateOutput();
}

function loadPreset(name) {
var preset = PRESETS[name];
if (!preset) return;
activePreset = name;
if (preset.type === 'circle' || preset.type === 'ellipse') {
currentType = preset.type;
points = [];
} else {
currentType = 'polygon';
points = preset.points.map(function(p) { return [p[0], p[1]]; });
}
document.querySelectorAll('.cp-preset-btn').forEach(function(b) {
b.classList.toggle('active', b.dataset.preset === name);
});
pointInfoEl.textContent = currentType === 'polygon'
? 'ポイントをドラッグして変形。右クリックで削除。ダブルクリックで追加。'
: 'この形は固定CSS関数を使用します。ポリゴン系プリセットを選ぶと頂点を編集できます。';
draw();
}

var presetsEl = document.getElementById('cp-presets');
Object.keys(PRESETS).forEach(function(name) {
var btn = document.createElement('button');
btn.className = 'cp-preset-btn';
btn.dataset.preset = name;
var svg = buildPresetSVG(name);
btn.innerHTML = svg + '<span>' + PRESETS[name].label + '</span>';
btn.addEventListener('click', function() { loadPreset(name); });
presetsEl.appendChild(btn);
});

function buildPresetSVG(name) {
var size = 36;
var preset = PRESETS[name];
if (name === 'circle') {
return '<svg width="' + size + '" height="' + size + '" viewBox="0 0 100 100"><circle cx="50" cy="50" r="45" fill="#6366f1"/></svg>';
}
if (name === 'ellipse') {
return '<svg width="' + size + '" height="' + size + '" viewBox="0 0 100 100"><ellipse cx="50" cy="50" rx="48" ry="30" fill="#6366f1"/></svg>';
}
var pts = preset.points;
if (pts) {
var path = pts.map(function(p, i) { return (i === 0 ? 'M' : 'L') + p[0] + ',' + p[1]; }).join(' ') + 'Z';
return '<svg width="' + size + '" height="' + size + '" viewBox="0 0 100 100"><path d="' + path + '" fill="#6366f1"/></svg>';
}
return '<svg width="' + size + '" height="' + size + '" viewBox="0 0 100 100"><rect width="100" height="100" fill="#6366f1"/></svg>';
}

function getCanvasPos(e) {
var rect = canvas.getBoundingClientRect();
var scaleX = canvas.width / rect.width;
var scaleY = canvas.height / rect.height;
var clientX = e.touches ? e.touches[0].clientX : e.clientX;
var clientY = e.touches ? e.touches[0].clientY : e.clientY;
return [(clientX - rect.left) * scaleX, (clientY - rect.top) * scaleY];
}

function hitTest(cx, cy) {
var radius = 14;
for (var i = points.length - 1; i >= 0; i--) {
var cp = toCanvasPx(points[i][0], points[i][1]);
if (Math.hypot(cx - cp[0], cy - cp[1]) < radius) return i;
}
return -1;
}

canvas.addEventListener('mousedown', function(e) {
if (currentType !== 'polygon') return;
e.preventDefault();
var pos = getCanvasPos(e);
var hit = hitTest(pos[0], pos[1]);
if (hit >= 0) dragIndex = hit;
draw();
});
canvas.addEventListener('touchstart', function(e) {
if (currentType !== 'polygon') return;
e.preventDefault();
var pos = getCanvasPos(e);
var hit = hitTest(pos[0], pos[1]);
if (hit >= 0) dragIndex = hit;
draw();
}, {passive: false});

canvas.addEventListener('mousemove', function(e) {
if (currentType !== 'polygon' || dragIndex < 0) return;
e.preventDefault();
var pos = getCanvasPos(e);
var px = Math.max(0, Math.min(100, pos[0] / canvas.width * 100));
var py = Math.max(0, Math.min(100, pos[1] / canvas.height * 100));
points[dragIndex] = [px, py];
draw();
});
canvas.addEventListener('touchmove', function(e) {
if (currentType !== 'polygon' || dragIndex < 0) return;
e.preventDefault();
var pos = getCanvasPos(e);
var px = Math.max(0, Math.min(100, pos[0] / canvas.width * 100));
var py = Math.max(0, Math.min(100, pos[1] / canvas.height * 100));
points[dragIndex] = [px, py];
draw();
}, {passive: false});

canvas.addEventListener('mouseup', function() { dragIndex = -1; draw(); });
canvas.addEventListener('touchend', function() { dragIndex = -1; draw(); });

canvas.addEventListener('contextmenu', function(e) {
if (currentType !== 'polygon') return;
e.preventDefault();
var pos = getCanvasPos(e);
var hit = hitTest(pos[0], pos[1]);
if (hit >= 0 && points.length > 3) {
points.splice(hit, 1);
draw();
}
});

canvas.addEventListener('dblclick', function(e) {
if (currentType !== 'polygon') return;
var pos = getCanvasPos(e);
var hit = hitTest(pos[0], pos[1]);
if (hit >= 0) return;
var px = pos[0] / canvas.width * 100;
var py = pos[1] / canvas.height * 100;
var bestEdge = 0, bestDist = Infinity;
for (var i = 0; i < points.length; i++) {
var j = (i + 1) % points.length;
var mx = (points[i][0] + points[j][0]) / 2;
var my = (points[i][1] + points[j][1]) / 2;
var d = Math.hypot(px - mx, py - my);
if (d < bestDist) { bestDist = d; bestEdge = j; }
}
points.splice(bestEdge, 0, [px, py]);
draw();
});

shapeColorInput.addEventListener('input', function(e) { shapeColor = e.target.value; draw(); });
bgColorInput.addEventListener('input', function(e) { bgColor = e.target.value; draw(); });

uploadBtn.addEventListener('click', function() { fileInput.click(); });
fileInput.addEventListener('change', function(e) {
var file = e.target.files[0];
if (!file) return;
var reader = new FileReader();
reader.onload = function(ev) {
var img = new Image();
img.onload = function() {
uploadedImage = img;
clearImgBtn.style.display = 'block';
draw();
};
img.src = ev.target.result;
};
reader.readAsDataURL(file);
});
clearImgBtn.addEventListener('click', function() {
uploadedImage = null;
fileInput.value = '';
clearImgBtn.style.display = 'none';
draw();
});

copyBtn.addEventListener('click', function() {
var css = buildCSS();
navigator.clipboard.writeText(css).then(function() {
copyBtn.textContent = 'コピーしました！';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'CSSをコピー';
copyBtn.classList.remove('copied');
}, 2000);
});
});

resetBtn.addEventListener('click', function() { loadPreset(activePreset); });

window.addEventListener('resize', resizeCanvas);
resizeCanvas();
loadPreset('triangle');
})();
</script>

---

## 使い方

1. **プリセットを選択** — 三角形・星・六角形など9種類から選べます。
2. **白いコントロールポイントをドラッグ** してシェイプを自由に変形。
3. **ダブルクリック** でキャンバス上に新しいポイントを追加。
4. **右クリック** でポイントを削除（最小3点）。
5. **シェイプ色・背景色** を自由にカスタマイズ。
6. **画像をアップロード** して実際の写真でclip-pathを確認。
7. **CSSをコピー** して、スタイルシートにそのまま貼り付け。

## clip-pathとは

`clip-path`はCSSプロパティで、要素の表示領域を多角形や円などの形に切り抜く機能です。最も柔軟な値は`polygon()`で、パーセンテージ座標のリストを指定します。

```css
/* 三角形 */
clip-path: polygon(50% 0%, 0% 100%, 100% 100%);

/* 六角形 */
clip-path: polygon(25% 6%, 75% 6%, 100% 50%, 75% 94%, 25% 94%, 0% 50%);

/* 星 */
clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
```

他にも`circle()`、`ellipse()`、`inset()`などの関数があります。

## ブラウザ対応

`clip-path`のpolygon値はChrome・Firefox・Safari・Edgeすべての最新ブラウザで対応済みです（2025年時点でベンダープレフィックス不要）。

---

**関連ツール**

> グラデーション → [グラデーションギャラリー](/ja/tools/gradient-gallery/)

> CSS詳細度 → [CSS詳細度計算](/ja/tools/css-specificity-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

<div class="cp-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>
