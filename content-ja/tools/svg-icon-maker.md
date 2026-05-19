---
title: "SVGアイコン作成ツール - カスタムSVGアイコンを簡単作成"
date: 2025-07-13
description: "ブラウザだけで使えるSVGアイコン作成ツール。24×24グリッドで円・四角・線・パスを自由に描き、SVGコードを即エクスポート。無料・インストール不要。"
categories: ["無料ツール"]
slug: "svg-icon-maker"
ShowToc: false
cover:
  image: "/images/covers/svg-icon-maker.png"
  alt: "SVGアイコン作成ツール"
---

<div id="sim-app">
<style>
#sim-app *,#sim-app *::before,#sim-app *::after{box-sizing:border-box;margin:0;padding:0}
#sim-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans','Yu Gothic UI','Meiryo',sans-serif;color:#1f2937;background:#f9fafb;min-height:100vh;padding:24px 16px}
#sim-app h1{font-size:1.6rem;font-weight:700;margin-bottom:6px;color:#111827}
#sim-app .subtitle{color:#6b7280;font-size:.95rem;margin-bottom:20px}
#sim-app .layout{display:grid;grid-template-columns:220px 1fr 260px;gap:16px;align-items:start}
@media(max-width:900px){#sim-app .layout{grid-template-columns:1fr}}
#sim-app .panel{background:#fff;border:1px solid #e5e7eb;border-radius:10px;padding:14px}
#sim-app .panel h3{font-size:.8rem;font-weight:700;text-transform:uppercase;letter-spacing:.04em;color:#6b7280;margin-bottom:10px}
#sim-app label{display:block;font-size:.82rem;color:#374151;margin-bottom:3px;margin-top:8px}
#sim-app label:first-of-type{margin-top:0}
#sim-app select,#sim-app input[type=number],#sim-app input[type=range]{width:100%;padding:5px 8px;border:1px solid #d1d5db;border-radius:6px;font-size:.85rem;color:#1f2937;background:#fff}
#sim-app input[type=color]{width:100%;height:32px;border:1px solid #d1d5db;border-radius:6px;padding:2px;cursor:pointer;background:#fff}
#sim-app .btn{display:inline-flex;align-items:center;justify-content:center;gap:6px;padding:8px 14px;border-radius:7px;font-size:.85rem;font-weight:600;cursor:pointer;border:none;transition:all .15s}
#sim-app .btn-primary{background:#4f46e5;color:#fff}
#sim-app .btn-primary:hover{background:#4338ca}
#sim-app .btn-secondary{background:#f3f4f6;color:#374151;border:1px solid #d1d5db}
#sim-app .btn-secondary:hover{background:#e5e7eb}
#sim-app .btn-danger{background:#fee2e2;color:#dc2626;border:1px solid #fca5a5}
#sim-app .btn-danger:hover{background:#fecaca}
#sim-app .btn-sm{padding:5px 10px;font-size:.78rem}
#sim-app .canvas-wrap{position:relative;display:flex;flex-direction:column;align-items:center;gap:12px}
#sim-app #drawing-svg{border:2px solid #6366f1;border-radius:8px;cursor:crosshair;background:#fff;display:block;box-shadow:0 2px 8px rgba(99,102,241,.1)}
#sim-app .canvas-controls{display:flex;gap:8px;flex-wrap:wrap;justify-content:center}
#sim-app .tool-btn{padding:6px 12px;border-radius:6px;font-size:.82rem;font-weight:600;border:2px solid #e5e7eb;background:#fff;cursor:pointer;transition:all .15s;color:#374151}
#sim-app .tool-btn.active{border-color:#4f46e5;background:#eef2ff;color:#4f46e5}
#sim-app .tool-btn:hover:not(.active){border-color:#c7d2fe;background:#f5f3ff}
#sim-app .preset-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:6px;margin-bottom:10px}
#sim-app .preset-btn{display:flex;flex-direction:column;align-items:center;gap:3px;padding:6px 4px;border:1px solid #e5e7eb;border-radius:6px;background:#f9fafb;cursor:pointer;font-size:.7rem;color:#6b7280;transition:all .15s}
#sim-app .preset-btn:hover{border-color:#6366f1;background:#eef2ff;color:#4f46e5}
#sim-app .preset-btn svg{width:20px;height:20px}
#sim-app .output-box{font-family:'Fira Mono','Consolas',monospace;font-size:.72rem;background:#0f172a;color:#a5f3fc;padding:12px;border-radius:8px;white-space:pre-wrap;word-break:break-all;max-height:220px;overflow-y:auto;line-height:1.5;border:1px solid #1e293b}
#sim-app .btn-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
#sim-app .shape-list{max-height:180px;overflow-y:auto;margin-top:4px}
#sim-app .shape-item{display:flex;align-items:center;justify-content:space-between;padding:5px 8px;border-radius:5px;font-size:.78rem;color:#374151;cursor:pointer;transition:background .1s}
#sim-app .shape-item:hover{background:#f3f4f6}
#sim-app .shape-item.selected{background:#eef2ff;color:#4338ca;font-weight:600}
#sim-app .shape-dot{width:10px;height:10px;border-radius:50%;border:1px solid #9ca3af;margin-right:6px;flex-shrink:0}
#sim-app .shape-item-left{display:flex;align-items:center}
#sim-app .del-btn{background:none;border:none;color:#ef4444;cursor:pointer;font-size:.85rem;padding:1px 4px;border-radius:3px}
#sim-app .del-btn:hover{background:#fee2e2}
#sim-app .grid-toggle{display:flex;align-items:center;gap:6px;font-size:.82rem;color:#6b7280;cursor:pointer;user-select:none}
#sim-app .grid-toggle input{margin:0}
#sim-app .size-preview{display:flex;align-items:center;gap:8px;font-size:.8rem;color:#6b7280;margin-top:4px}
#sim-app .size-preview canvas{border:1px solid #e5e7eb;border-radius:3px}
#sim-app .alert-ok{background:#d1fae5;color:#065f46;border:1px solid #6ee7b7;border-radius:6px;padding:6px 12px;font-size:.82rem;display:none}
#sim-app .section-sep{border:none;border-top:1px solid #f3f4f6;margin:10px 0}
#sim-app .freee-cta{background:linear-gradient(135deg,#e0f2fe,#f0fdf4);border:1px solid #7dd3fc;border-radius:10px;padding:14px 16px;margin-top:20px;font-size:.9rem}
#sim-app .freee-cta strong{color:#0369a1;display:block;margin-bottom:4px;font-size:.95rem}
#sim-app .freee-cta a{color:#0369a1;font-weight:700;text-decoration:underline}
</style>

<h1>SVGアイコン作成ツール</h1>
<p class="subtitle">24×24グリッドでSVGアイコンをブラウザ上で自由に描画。SVGコードをすぐにコピー・ダウンロードできます。</p>

<div class="layout">
<!-- 左: ツール設定 -->
<div>
<div class="panel" style="margin-bottom:12px">
<h3>プリセットアイコン</h3>
<div class="preset-grid" id="preset-grid"></div>
</div>

<div class="panel" style="margin-bottom:12px">
<h3>描画ツール</h3>
<div style="display:flex;flex-direction:column;gap:6px" id="tool-buttons"></div>

<hr class="section-sep">

<label>塗りつぶし色</label>
<input type="color" id="fill-color" value="#4f46e5">
<label style="margin-top:6px">
<input type="checkbox" id="no-fill" style="width:auto;margin-right:4px"> 塗りなし
</label>

<label>線の色（ストローク）</label>
<input type="color" id="stroke-color" value="#4f46e5">

<label>線の太さ</label>
<input type="range" id="stroke-width" min="0" max="4" step="0.5" value="1.5">
<div style="font-size:.78rem;color:#6b7280;text-align:right" id="stroke-val">1.5</div>

<label>塗りつぶし不透明度</label>
<input type="range" id="fill-opacity" min="0" max="1" step="0.05" value="1">
<div style="font-size:.78rem;color:#6b7280;text-align:right" id="opacity-val">1.0</div>
</div>

<div class="panel">
<h3>シェイプ一覧（<span id="shape-count">0</span>件）</h3>
<div class="shape-list" id="shape-list"></div>
<div style="margin-top:8px;display:flex;gap:6px">
<button class="btn btn-danger btn-sm" id="del-selected-btn">削除</button>
<button class="btn btn-secondary btn-sm" id="clear-btn">全消去</button>
</div>
</div>
</div>

<!-- 中央: キャンバス -->
<div class="canvas-wrap">
<div class="canvas-controls" id="canvas-controls">
<label class="grid-toggle">
<input type="checkbox" id="show-grid" checked> グリッド表示
</label>
<label class="grid-toggle">
<input type="checkbox" id="snap-grid" checked> スナップ
</label>
</div>
<svg id="drawing-svg" width="480" height="480" viewBox="0 0 24 24"
xmlns="http://www.w3.org/2000/svg"
style="touch-action:none">
<defs>
<pattern id="grid-pat" width="1" height="1" patternUnits="userSpaceOnUse">
<path d="M 1 0 L 0 0 0 1" fill="none" stroke="#e0e7ff" stroke-width="0.04"/>
</pattern>
</defs>
<rect id="grid-rect" width="24" height="24" fill="url(#grid-pat)"/>
<g id="shapes-layer"></g>
<g id="preview-layer"></g>
</svg>
<div class="size-preview">
<span>プレビュー:</span>
<canvas id="prev-16" width="16" height="16" title="16px"></canvas> 16px
<canvas id="prev-32" width="32" height="32" title="32px"></canvas> 32px
<canvas id="prev-64" width="64" height="64" title="64px"></canvas> 64px
</div>
<div style="font-size:.78rem;color:#9ca3af;text-align:center">
クリック＆ドラッグで描画。シェイプをクリックで選択。
</div>
</div>

<!-- 右: 出力 -->
<div>
<div class="panel">
<h3>SVGコード出力</h3>
<div class="output-box" id="svg-output">&lt;!-- キャンバスに描画するとSVGが生成されます --&gt;</div>
<div class="btn-row">
<button class="btn btn-primary btn-sm" id="copy-btn">コピー</button>
<button class="btn btn-secondary btn-sm" id="download-btn">.svgダウンロード</button>
</div>
<div class="alert-ok" id="copy-ok">クリップボードにコピーしました！</div>

<hr class="section-sep">
<h3 style="margin-top:0">エクスポートサイズ</h3>
<label>viewBoxサイズ</label>
<select id="viewbox-size">
<option value="24">24×24（標準）</option>
<option value="16">16×16</option>
<option value="32">32×32</option>
<option value="48">48×48</option>
<option value="64">64×64</option>
</select>

<hr class="section-sep">
<h3 style="margin-top:0">最適化</h3>
<label class="grid-toggle" style="margin-top:4px">
<input type="checkbox" id="round-coords" checked> 座標を丸める（小数点2桁）
</label>
</div>
</div>
</div>

<script>
(function(){
const SVG_NS = 'http://www.w3.org/2000/svg';
const svgEl = document.getElementById('drawing-svg');
const shapesLayer = document.getElementById('shapes-layer');
const previewLayer = document.getElementById('preview-layer');
const outputEl = document.getElementById('svg-output');
const shapeListEl = document.getElementById('shape-list');
const shapeCountEl = document.getElementById('shape-count');
const strokeValEl = document.getElementById('stroke-val');
const opacityValEl = document.getElementById('opacity-val');
const copyOkEl = document.getElementById('copy-ok');

let currentTool = 'circle';
let shapes = [];
let selectedId = null;
let drawing = false;
let startPt = null;
let previewEl = null;
let idCounter = 0;

const TOOLS = [
{id:'circle',  label:'円'},
{id:'rect',    label:'四角形'},
{id:'line',    label:'直線'},
{id:'path',    label:'パス（フリーハンド）'},
];

const PRESETS = [
{label:'矢印', d:'M4 12h16M13 5l7 7-7 7', name:'arrow'},
{label:'チェック', d:'M5 13l4 4L19 7', name:'check'},
{label:'×', d:'M18 6L6 18M6 6l12 12', name:'x'},
{label:'星', d:'M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z', name:'star'},
{label:'ハート', d:'M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z', name:'heart'},
];

// ツールボタン生成
const toolBtns = document.getElementById('tool-buttons');
TOOLS.forEach(t => {
const btn = document.createElement('button');
btn.className = 'tool-btn' + (t.id === currentTool ? ' active' : '');
btn.textContent = t.label;
btn.dataset.tool = t.id;
btn.addEventListener('click', () => {
currentTool = t.id;
document.querySelectorAll('#sim-app .tool-btn').forEach(b => b.classList.toggle('active', b.dataset.tool === currentTool));
});
toolBtns.appendChild(btn);
});

// プリセット生成
const presetGrid = document.getElementById('preset-grid');
PRESETS.forEach(p => {
const btn = document.createElement('button');
btn.className = 'preset-btn';
const svgStr = `<svg viewBox="0 0 24 24" fill="none" stroke="#4f46e5" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="${p.d}"/></svg>`;
btn.innerHTML = svgStr + `<span>${p.label}</span>`;
btn.addEventListener('click', () => addPreset(p));
presetGrid.appendChild(btn);
});

function addPreset(p) {
const id = ++idCounter;
const fill = document.getElementById('no-fill').checked ? 'none' : document.getElementById('fill-color').value;
const stroke = document.getElementById('stroke-color').value;
const sw = parseFloat(document.getElementById('stroke-width').value);
const op = parseFloat(document.getElementById('fill-opacity').value);
shapes.push({id, type:'path', d:p.d, fill, stroke, strokeWidth:sw, opacity:op, label:`パス（${p.label}）`});
renderShapes();
selectShape(id);
updateOutput();
updateShapeList();
}

function getSVGPoint(e) {
const rect = svgEl.getBoundingClientRect();
const raw = {
x: (e.clientX ?? e.touches[0].clientX) - rect.left,
y: (e.clientY ?? e.touches[0].clientY) - rect.top
};
const scale = 24 / rect.width;
let px = raw.x * scale;
let py = raw.y * scale;
if (document.getElementById('snap-grid').checked) {
px = Math.round(px * 2) / 2;
py = Math.round(py * 2) / 2;
}
return {x: Math.max(0, Math.min(24, px)), y: Math.max(0, Math.min(24, py))};
}

function r(n) {
return document.getElementById('round-coords').checked ? Math.round(n * 100) / 100 : n;
}

let pathPoints = [];

svgEl.addEventListener('mousedown', startDraw);
svgEl.addEventListener('mousemove', moveDraw);
svgEl.addEventListener('mouseup', endDraw);
svgEl.addEventListener('mouseleave', endDraw);

function startDraw(e) {
if (e.target !== svgEl && e.target !== document.getElementById('grid-rect')) return;
drawing = true;
startPt = getSVGPoint(e);
if (currentTool === 'path') pathPoints = [startPt];
createPreview(startPt, startPt);
}

function moveDraw(e) {
if (!drawing) return;
const pt = getSVGPoint(e);
if (currentTool === 'path') pathPoints.push(pt);
updatePreview(startPt, pt);
}

function endDraw(e) {
if (!drawing) return;
drawing = false;
if (!startPt) return;
const endPt = getSVGPoint(e);
if (previewEl) { previewEl.remove(); previewEl = null; }

const fill = document.getElementById('no-fill').checked ? 'none' : document.getElementById('fill-color').value;
const stroke = document.getElementById('stroke-color').value;
const sw = parseFloat(document.getElementById('stroke-width').value);
const op = parseFloat(document.getElementById('fill-opacity').value);
const id = ++idCounter;

let shape = null;
if (currentTool === 'circle') {
const dx = endPt.x - startPt.x, dy = endPt.y - startPt.y;
const rad = Math.max(0.5, Math.sqrt(dx*dx + dy*dy));
shape = {id, type:'circle', cx:r(startPt.x), cy:r(startPt.y), r:r(rad), fill, stroke, strokeWidth:sw, opacity:op, label:'円'};
} else if (currentTool === 'rect') {
const x = r(Math.min(startPt.x, endPt.x));
const y = r(Math.min(startPt.y, endPt.y));
const w = r(Math.abs(endPt.x - startPt.x));
const h = r(Math.abs(endPt.y - startPt.y));
if (w < 0.5 || h < 0.5) return;
shape = {id, type:'rect', x, y, width:w, height:h, fill, stroke, strokeWidth:sw, opacity:op, label:'四角形'};
} else if (currentTool === 'line') {
shape = {id, type:'line', x1:r(startPt.x), y1:r(startPt.y), x2:r(endPt.x), y2:r(endPt.y), fill:'none', stroke, strokeWidth:sw, opacity:op, label:'直線'};
} else if (currentTool === 'path') {
if (pathPoints.length < 2) return;
const d = pathPoints.map((p,i) => `${i===0?'M':'L'}${r(p.x)},${r(p.y)}`).join(' ');
shape = {id, type:'path', d, fill:'none', stroke, strokeWidth:sw, opacity:op, label:'パス'};
pathPoints = [];
}

if (shape) {
shapes.push(shape);
renderShapes();
selectShape(id);
updateOutput();
updateShapeList();
}
startPt = null;
}

function createPreview(a, b) {
if (previewEl) previewEl.remove();
previewEl = makeShapeEl({id:'preview', type:currentTool==='path'?'path':currentTool, ...shapeAttrs(a,b)}, true);
if (previewEl) { previewEl.style.opacity = '0.5'; previewLayer.appendChild(previewEl); }
}

function updatePreview(a, b) {
if (!previewEl) return createPreview(a, b);
const attrs = shapeAttrs(a, b);
Object.entries(attrs).forEach(([k,v]) => previewEl.setAttribute(k, v));
}

function shapeAttrs(a, b) {
const fill = document.getElementById('no-fill').checked ? 'none' : document.getElementById('fill-color').value;
const stroke = document.getElementById('stroke-color').value;
const sw = document.getElementById('stroke-width').value;
if (currentTool === 'circle') {
const dx = b.x-a.x, dy = b.y-a.y;
const rad = Math.max(0.2, Math.sqrt(dx*dx+dy*dy));
return {cx:a.x, cy:a.y, r:rad, fill, stroke, 'stroke-width':sw};
} else if (currentTool === 'rect') {
return {x:Math.min(a.x,b.x), y:Math.min(a.y,b.y), width:Math.abs(b.x-a.x)||0.1, height:Math.abs(b.y-a.y)||0.1, fill, stroke, 'stroke-width':sw};
} else if (currentTool === 'line') {
return {x1:a.x, y1:a.y, x2:b.x, y2:b.y, fill:'none', stroke, 'stroke-width':sw};
} else if (currentTool === 'path') {
const d = pathPoints.length>1 ? pathPoints.map((p,i)=>`${i===0?'M':'L'}${p.x},${p.y}`).join(' ') : `M${a.x},${a.y} L${b.x},${b.y}`;
return {d, fill:'none', stroke, 'stroke-width':sw};
}
return {};
}

function makeShapeEl(shape, isPreview) {
let el;
if (shape.type === 'circle') {
el = document.createElementNS(SVG_NS, 'circle');
el.setAttribute('cx', shape.cx); el.setAttribute('cy', shape.cy); el.setAttribute('r', shape.r);
} else if (shape.type === 'rect') {
el = document.createElementNS(SVG_NS, 'rect');
el.setAttribute('x', shape.x); el.setAttribute('y', shape.y);
el.setAttribute('width', shape.width); el.setAttribute('height', shape.height);
} else if (shape.type === 'line') {
el = document.createElementNS(SVG_NS, 'line');
el.setAttribute('x1', shape.x1); el.setAttribute('y1', shape.y1);
el.setAttribute('x2', shape.x2); el.setAttribute('y2', shape.y2);
} else if (shape.type === 'path') {
el = document.createElementNS(SVG_NS, 'path');
el.setAttribute('d', shape.d);
}
if (!el) return null;
el.setAttribute('fill', shape.fill ?? 'none');
el.setAttribute('stroke', shape.stroke ?? 'none');
el.setAttribute('stroke-width', shape.strokeWidth ?? 1.5);
el.setAttribute('fill-opacity', shape.opacity ?? 1);
el.setAttribute('stroke-linecap', 'round');
el.setAttribute('stroke-linejoin', 'round');
if (!isPreview) {
el.dataset.shapeId = shape.id;
el.style.cursor = 'pointer';
el.addEventListener('click', (ev) => { ev.stopPropagation(); selectShape(shape.id); });
}
return el;
}

function renderShapes() {
shapesLayer.innerHTML = '';
shapes.forEach(s => {
const el = makeShapeEl(s, false);
if (el) {
if (s.id === selectedId) el.setAttribute('filter', 'drop-shadow(0 0 1px #6366f1)');
shapesLayer.appendChild(el);
}
});
updatePreviews();
}

function selectShape(id) {
selectedId = id;
renderShapes();
updateShapeList();
}

svgEl.addEventListener('click', (e) => {
if (e.target === svgEl || e.target === document.getElementById('grid-rect')) {
selectedId = null;
renderShapes();
updateShapeList();
}
});

function updateShapeList() {
shapeListEl.innerHTML = '';
shapeCountEl.textContent = shapes.length;
if (shapes.length === 0) {
shapeListEl.innerHTML = '<div style="font-size:.78rem;color:#9ca3af;padding:6px">キャンバスに描画するとシェイプが追加されます</div>';
return;
}
shapes.forEach((s, i) => {
const div = document.createElement('div');
div.className = 'shape-item' + (s.id === selectedId ? ' selected' : '');
const dot = document.createElement('span');
dot.className = 'shape-dot';
dot.style.background = s.stroke !== 'none' ? s.stroke : s.fill;
const left = document.createElement('span');
left.className = 'shape-item-left';
left.appendChild(dot);
left.appendChild(document.createTextNode(`${i+1}. ${s.label}`));
const del = document.createElement('button');
del.className = 'del-btn';
del.textContent = '✕';
del.title = 'シェイプを削除';
del.addEventListener('click', (e) => { e.stopPropagation(); shapes.splice(i,1); if(selectedId===s.id) selectedId=null; renderShapes(); updateOutput(); updateShapeList(); });
div.appendChild(left);
div.appendChild(del);
div.addEventListener('click', () => selectShape(s.id));
shapeListEl.appendChild(div);
});
}

function generateSVG() {
const vbSize = parseInt(document.getElementById('viewbox-size').value) || 24;
const scale = vbSize / 24;
let inner = shapes.map(s => {
let attrs = `fill="${s.fill}" stroke="${s.stroke}" stroke-width="${s.strokeWidth}" fill-opacity="${s.opacity}" stroke-linecap="round" stroke-linejoin="round"`;
if (s.type === 'circle') return `  <circle cx="${r(s.cx*scale)}" cy="${r(s.cy*scale)}" r="${r(s.r*scale)}" ${attrs}/>`;
if (s.type === 'rect') return `  <rect x="${r(s.x*scale)}" y="${r(s.y*scale)}" width="${r(s.width*scale)}" height="${r(s.height*scale)}" ${attrs}/>`;
if (s.type === 'line') return `  <line x1="${r(s.x1*scale)}" y1="${r(s.y1*scale)}" x2="${r(s.x2*scale)}" y2="${r(s.y2*scale)}" ${attrs}/>`;
if (s.type === 'path') {
let d = s.d;
if (scale !== 1) {
d = d.replace(/([ML])(-?\d+\.?\d*),(-?\d+\.?\d*)/g, (_, cmd, x, y) => `${cmd}${r(parseFloat(x)*scale)},${r(parseFloat(y)*scale)}`);
}
return `  <path d="${d}" ${attrs}/>`;
}
return '';
}).filter(Boolean).join('\n');
return `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 ${vbSize} ${vbSize}" width="${vbSize}" height="${vbSize}">\n${inner || '  <!-- empty -->'}\n</svg>`;
}

function updateOutput() {
outputEl.textContent = generateSVG();
}

function updatePreviews() {
[16,32,64].forEach(sz => {
const canvas = document.getElementById(`prev-${sz}`);
const ctx = canvas.getContext('2d');
ctx.clearRect(0,0,sz,sz);
const svgStr = generateSVG().replace(`width="24" height="24"`, `width="${sz}" height="${sz}"`);
const blob = new Blob([svgStr], {type:'image/svg+xml'});
const url = URL.createObjectURL(blob);
const img = new Image();
img.onload = () => { ctx.drawImage(img, 0, 0, sz, sz); URL.revokeObjectURL(url); };
img.src = url;
});
}

document.getElementById('show-grid').addEventListener('change', (e) => {
document.getElementById('grid-rect').style.display = e.target.checked ? '' : 'none';
});

document.getElementById('stroke-width').addEventListener('input', (e) => {
strokeValEl.textContent = e.target.value;
});

document.getElementById('fill-opacity').addEventListener('input', (e) => {
opacityValEl.textContent = parseFloat(e.target.value).toFixed(2);
});

document.getElementById('copy-btn').addEventListener('click', () => {
navigator.clipboard.writeText(generateSVG()).then(() => {
copyOkEl.style.display = 'block';
setTimeout(() => copyOkEl.style.display = 'none', 2000);
});
});

document.getElementById('download-btn').addEventListener('click', () => {
const blob = new Blob([generateSVG()], {type:'image/svg+xml'});
const url = URL.createObjectURL(blob);
const a = document.createElement('a');
a.href = url; a.download = 'icon.svg'; a.click();
setTimeout(() => URL.revokeObjectURL(url), 1000);
});

document.getElementById('del-selected-btn').addEventListener('click', () => {
if (selectedId == null) return;
shapes = shapes.filter(s => s.id !== selectedId);
selectedId = null;
renderShapes(); updateOutput(); updateShapeList();
});

document.getElementById('clear-btn').addEventListener('click', () => {
if (!shapes.length || confirm('すべてのシェイプを消去しますか？')) {
shapes = []; selectedId = null;
renderShapes(); updateOutput(); updateShapeList();
}
});

document.getElementById('viewbox-size').addEventListener('change', updateOutput);
document.getElementById('round-coords').addEventListener('change', () => { renderShapes(); updateOutput(); });

updateShapeList();
updateOutput();
})();
</script>

---

> デザイン業務を効率化 → [freee会計でクリエイティブ業務に集中](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

<div class="freee-cta">
<strong>クリエイティブ業務の請求・経費管理もラクに</strong>
デザインやコーディングの案件管理・請求書発行・確定申告まで、freee会計で一元管理できます。<br>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計を無料で試す →</a>
</div>

</div>

---

## 関連ツール

> Favicon Generator → [Favicon Generatorツール](/ja/tools/favicon-generator/)
> Image Color Picker → [Image Color Pickerツール](/ja/tools/image-color-picker/)
> 画像圧縮 → [画像圧縮ツール](/ja/tools/image-compressor/)

