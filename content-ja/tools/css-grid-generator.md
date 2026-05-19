---
title: "CSS Gridジェネレーター — ビジュアルレイアウトビルダー"
date: 2025-08-18
description: "無料のCSS Gridジェネレーター。ドラッグ操作でグリッドレイアウトを構築、セル結合、エリア設定、CSSコード生成。ダッシュボード・ギャラリー等のプリセット。"
categories: ["無料ツール"]
slug: "css-grid-generator"
ShowToc: false
aliases:
  - "/ja/tools/css-grid-generator/"
  - "/ja/tools/css-grid-generator/"
cover:
  image: "/images/covers/css-grid-generator-ja.png"
  alt: "CSS Gridジェネレーター"
---

<div id="grid-app">
<style>
#grid-app *,
#grid-app *::before,
#grid-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#grid-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Meiryo", "Segoe UI", sans-serif;
font-size: 14px;
color: #1a1a2e;
background: #f8f9ff;
border-radius: 12px;
padding: 24px;
max-width: 100%;
overflow: hidden;
}

#grid-app h2.ga-title {
font-size: 1.4rem;
font-weight: 700;
margin-bottom: 4px;
color: #1a1a2e;
}

#grid-app p.ga-subtitle {
color: #666;
margin-bottom: 20px;
font-size: 0.9rem;
}

/* Presets */
#grid-app .ga-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 20px;
}

#grid-app .ga-preset-btn {
background: #fff;
border: 2px solid #d0d7ff;
border-radius: 8px;
padding: 6px 14px;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
color: #3a3aff;
transition: all 0.15s;
}

#grid-app .ga-preset-btn:hover {
background: #3a3aff;
color: #fff;
border-color: #3a3aff;
}

/* Controls panel */
#grid-app .ga-controls {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 12px;
margin-bottom: 20px;
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
}

#grid-app .ga-ctrl-group {
display: flex;
flex-direction: column;
gap: 4px;
}

#grid-app .ga-ctrl-group label {
font-size: 0.78rem;
font-weight: 600;
color: #555;
text-transform: uppercase;
letter-spacing: 0.04em;
}

#grid-app .ga-ctrl-group input[type="number"],
#grid-app .ga-ctrl-group input[type="text"],
#grid-app .ga-ctrl-group select {
border: 1.5px solid #d0d7ff;
border-radius: 6px;
padding: 6px 10px;
font-size: 0.9rem;
outline: none;
transition: border-color 0.15s;
background: #f8f9ff;
color: #1a1a2e;
width: 100%;
}

#grid-app .ga-ctrl-group input:focus,
#grid-app .ga-ctrl-group select:focus {
border-color: #3a3aff;
background: #fff;
}

/* Column / Row definition rows */
#grid-app .ga-track-section {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
}

#grid-app .ga-track-section h3 {
font-size: 0.9rem;
font-weight: 700;
margin-bottom: 10px;
color: #3a3aff;
}

#grid-app .ga-track-list {
display: flex;
flex-direction: column;
gap: 6px;
}

#grid-app .ga-track-row {
display: flex;
align-items: center;
gap: 8px;
font-size: 0.85rem;
}

#grid-app .ga-track-row span.ga-track-label {
width: 70px;
color: #888;
flex-shrink: 0;
}

#grid-app .ga-track-row input.ga-track-val {
flex: 1;
border: 1.5px solid #d0d7ff;
border-radius: 6px;
padding: 4px 8px;
font-size: 0.85rem;
outline: none;
background: #f8f9ff;
color: #1a1a2e;
min-width: 0;
}

#grid-app .ga-track-row input.ga-track-val:focus {
border-color: #3a3aff;
background: #fff;
}

#grid-app .ga-track-row select.ga-track-unit {
border: 1.5px solid #d0d7ff;
border-radius: 6px;
padding: 4px 6px;
font-size: 0.82rem;
outline: none;
background: #f8f9ff;
color: #1a1a2e;
cursor: pointer;
}

/* Preview area */
#grid-app .ga-preview-label {
font-size: 0.82rem;
font-weight: 700;
color: #555;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 8px;
}

#grid-app .ga-preview-wrap {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
overflow: auto;
}

#grid-app #ga-preview-grid {
display: grid;
min-height: 200px;
gap: 8px;
width: 100%;
}

#grid-app .ga-cell {
border-radius: 6px;
display: flex;
align-items: center;
justify-content: center;
font-size: 0.75rem;
font-weight: 700;
color: rgba(255,255,255,0.9);
cursor: pointer;
min-height: 48px;
transition: filter 0.15s, transform 0.1s;
user-select: none;
position: relative;
border: 2px solid transparent;
}

#grid-app .ga-cell:hover {
filter: brightness(1.1);
transform: scale(1.02);
z-index: 2;
}

#grid-app .ga-cell.ga-selected {
border-color: #fff;
box-shadow: 0 0 0 3px #3a3aff;
}

/* Items panel */
#grid-app .ga-items-section {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
}

#grid-app .ga-items-section h3 {
font-size: 0.9rem;
font-weight: 700;
margin-bottom: 10px;
color: #3a3aff;
}

#grid-app .ga-items-list {
display: flex;
flex-direction: column;
gap: 8px;
max-height: 300px;
overflow-y: auto;
}

#grid-app .ga-item-row {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
padding: 8px;
border-radius: 8px;
border: 1.5px solid #e0e4ff;
background: #f8f9ff;
}

#grid-app .ga-item-row .ga-item-swatch {
width: 20px;
height: 20px;
border-radius: 4px;
flex-shrink: 0;
}

#grid-app .ga-item-row label {
font-size: 0.78rem;
font-weight: 600;
color: #555;
}

#grid-app .ga-item-row input[type="number"] {
width: 52px;
border: 1.5px solid #d0d7ff;
border-radius: 5px;
padding: 3px 6px;
font-size: 0.82rem;
outline: none;
background: #fff;
color: #1a1a2e;
}

#grid-app .ga-item-row input[type="text"] {
flex: 1;
min-width: 80px;
border: 1.5px solid #d0d7ff;
border-radius: 5px;
padding: 3px 6px;
font-size: 0.82rem;
outline: none;
background: #fff;
color: #1a1a2e;
}

#grid-app .ga-item-row input:focus {
border-color: #3a3aff;
}

#grid-app .ga-item-btn {
background: #f0f0ff;
border: 1.5px solid #d0d7ff;
border-radius: 5px;
padding: 3px 8px;
font-size: 0.78rem;
cursor: pointer;
color: #3a3aff;
font-weight: 600;
}

#grid-app .ga-item-btn:hover {
background: #3a3aff;
color: #fff;
border-color: #3a3aff;
}

#grid-app .ga-add-item-btn {
margin-top: 8px;
background: #3a3aff;
color: #fff;
border: none;
border-radius: 7px;
padding: 7px 16px;
font-size: 0.85rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
}

#grid-app .ga-add-item-btn:hover {
background: #2020cc;
}

/* Named areas */
#grid-app .ga-areas-section {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
}

#grid-app .ga-areas-section h3 {
font-size: 0.9rem;
font-weight: 700;
margin-bottom: 6px;
color: #3a3aff;
}

#grid-app .ga-areas-section p.ga-hint {
font-size: 0.78rem;
color: #888;
margin-bottom: 8px;
}

#grid-app #ga-areas-input {
width: 100%;
min-height: 80px;
font-family: "Courier New", monospace;
font-size: 0.85rem;
border: 1.5px solid #d0d7ff;
border-radius: 7px;
padding: 8px 10px;
resize: vertical;
outline: none;
background: #f8f9ff;
color: #1a1a2e;
}

#grid-app #ga-areas-input:focus {
border-color: #3a3aff;
background: #fff;
}

/* Output */
#grid-app .ga-output-section {
background: #1a1a2e;
border-radius: 10px;
padding: 16px;
margin-bottom: 20px;
position: relative;
}

#grid-app .ga-output-section h3 {
font-size: 0.88rem;
font-weight: 700;
color: #a0a8ff;
margin-bottom: 10px;
text-transform: uppercase;
letter-spacing: 0.05em;
}

#grid-app #ga-css-output {
font-family: "Courier New", monospace;
font-size: 0.82rem;
color: #c9d1ff;
white-space: pre;
overflow-x: auto;
line-height: 1.6;
max-height: 320px;
overflow-y: auto;
}

#grid-app #ga-css-output .ga-prop { color: #79b8ff; }
#grid-app #ga-css-output .ga-val  { color: #b5f5a0; }
#grid-app #ga-css-output .ga-sel  { color: #ffcc66; }
#grid-app #ga-css-output .ga-brace { color: #ff9eee; }

#grid-app .ga-copy-btn {
position: absolute;
top: 14px;
right: 14px;
background: #3a3aff;
color: #fff;
border: none;
border-radius: 6px;
padding: 5px 14px;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
}

#grid-app .ga-copy-btn:hover { background: #2020cc; }
#grid-app .ga-copy-btn.ga-copied { background: #22aa66; }

#grid-app .ga-shorthand-section {
background: #111127;
border-radius: 10px;
padding: 14px 16px;
margin-bottom: 20px;
position: relative;
}

#grid-app .ga-shorthand-section h3 {
font-size: 0.88rem;
font-weight: 700;
color: #a0a8ff;
margin-bottom: 8px;
text-transform: uppercase;
letter-spacing: 0.05em;
}

#grid-app #ga-shorthand-output {
font-family: "Courier New", monospace;
font-size: 0.82rem;
color: #b5f5a0;
white-space: pre-wrap;
word-break: break-all;
}

#grid-app .ga-copy-sh-btn {
position: absolute;
top: 14px;
right: 14px;
background: #22aa66;
color: #fff;
border: none;
border-radius: 6px;
padding: 5px 14px;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
}

#grid-app .ga-copy-sh-btn:hover { background: #178850; }
#grid-app .ga-copy-sh-btn.ga-copied { background: #0e5c38; }

/* Responsive */
@media (max-width: 600px) {
#grid-app { padding: 14px; }
#grid-app .ga-controls { grid-template-columns: 1fr 1fr; }
#grid-app .ga-item-row { gap: 5px; }
#grid-app .ga-presets { gap: 5px; }
}
</style>

<h2 class="ga-title">CSS Gridジェネレーター</h2>
<p class="ga-subtitle">グリッドレイアウトをビジュアルで構築。トラック設定・セル結合・エリア名指定後、CSSをコピーするだけ。</p>

<!-- プリセット -->
<div class="ga-presets">
<button class="ga-preset-btn" onclick="gaLoadPreset('dashboard')">ダッシュボード</button>
<button class="ga-preset-btn" onclick="gaLoadPreset('gallery')">フォトギャラリー</button>
<button class="ga-preset-btn" onclick="gaLoadPreset('magazine')">マガジンレイアウト</button>
<button class="ga-preset-btn" onclick="gaLoadPreset('holygrail')">Holy Grail</button>
<button class="ga-preset-btn" onclick="gaLoadPreset('cards')">レスポンシブカード</button>
<button class="ga-preset-btn" onclick="gaLoadPreset('reset')">リセット</button>
</div>

<!-- コントロール -->
<div class="ga-controls">
<div class="ga-ctrl-group">
<label>列数（Columns）</label>
<input type="number" id="ga-cols" min="1" max="12" value="3" oninput="gaUpdate()">
</div>
<div class="ga-ctrl-group">
<label>行数（Rows）</label>
<input type="number" id="ga-rows" min="1" max="12" value="3" oninput="gaUpdate()">
</div>
<div class="ga-ctrl-group">
<label>列の間隔（Column Gap）</label>
<input type="text" id="ga-col-gap" value="16px" oninput="gaUpdate()">
</div>
<div class="ga-ctrl-group">
<label>行の間隔（Row Gap）</label>
<input type="text" id="ga-row-gap" value="16px" oninput="gaUpdate()">
</div>
<div class="ga-ctrl-group">
<label>横位置（Justify Items）</label>
<select id="ga-justify-items" onchange="gaUpdate()">
<option value="stretch">stretch（引き伸ばし）</option>
<option value="start">start（左寄せ）</option>
<option value="end">end（右寄せ）</option>
<option value="center">center（中央）</option>
</select>
</div>
<div class="ga-ctrl-group">
<label>縦位置（Align Items）</label>
<select id="ga-align-items" onchange="gaUpdate()">
<option value="stretch">stretch（引き伸ばし）</option>
<option value="start">start（上寄せ）</option>
<option value="end">end（下寄せ）</option>
<option value="center">center（中央）</option>
</select>
</div>
</div>

<!-- 列トラック設定 -->
<div class="ga-track-section">
<h3>列サイズ（grid-template-columns）</h3>
<div class="ga-track-list" id="ga-col-tracks"></div>
</div>

<!-- 行トラック設定 -->
<div class="ga-track-section">
<h3>行サイズ（grid-template-rows）</h3>
<div class="ga-track-list" id="ga-row-tracks"></div>
</div>

<!-- 名前付きグリッドエリア -->
<div class="ga-areas-section">
<h3>名前付きグリッドエリア（任意）</h3>
<p class="ga-hint">1行に1行分のエリア名をスペース区切りで入力してください。空セルには <code>.</code> を使用。</p>
<textarea id="ga-areas-input" placeholder='例：&#10;"header header header"&#10;"sidebar main aside"&#10;"footer footer footer"' oninput="gaUpdate()"></textarea>
</div>

<!-- ライブプレビュー -->
<div class="ga-preview-label">ライブプレビュー — セルをクリックして選択</div>
<div class="ga-preview-wrap">
<div id="ga-preview-grid"></div>
</div>

<!-- グリッドアイテム -->
<div class="ga-items-section">
<h3>グリッドアイテム</h3>
<div class="ga-items-list" id="ga-items-list"></div>
<button class="ga-add-item-btn" onclick="gaAddItem()">+ アイテムを追加</button>
</div>

<!-- CSS出力 -->
<div class="ga-output-section">
<h3>生成されたCSS</h3>
<button class="ga-copy-btn" id="ga-copy-btn" onclick="gaCopyCss()">CSSをコピー</button>
<div id="ga-css-output"></div>
</div>

<!-- 短縮記法 -->
<div class="ga-shorthand-section">
<h3>ショートハンド値</h3>
<button class="ga-copy-sh-btn" id="ga-copy-sh-btn" onclick="gaCopyShorthand()">コピー</button>
<div id="ga-shorthand-output"></div>
</div>

<script>
(function() {
var COLORS = [
'#6366f1','#f59e0b','#10b981','#ef4444','#8b5cf6',
'#06b6d4','#f97316','#84cc16','#ec4899','#14b8a6',
'#a855f7','#eab308'
];

var gaState = {
cols: 3,
rows: 3,
colGap: '16px',
rowGap: '16px',
justifyItems: 'stretch',
alignItems: 'stretch',
colTracks: [],
rowTracks: [],
areas: '',
items: []
};

function gaDefaultTracks(n, type) {
var arr = [];
for (var i = 0; i < n; i++) {
arr.push({ value: '1', unit: 'fr' });
}
return arr;
}

function gaTrackStr(track) {
if (track.unit === 'minmax') {
return 'minmax(' + track.value + ')';
}
if (track.unit === 'auto') return 'auto';
return track.value + track.unit;
}

function gaGetColTracks() {
var rows = document.querySelectorAll('#ga-col-tracks .ga-track-row');
var arr = [];
rows.forEach(function(r) {
arr.push({
value: r.querySelector('.ga-track-val').value || '1',
unit: r.querySelector('.ga-track-unit').value
});
});
return arr;
}

function gaGetRowTracks() {
var rows = document.querySelectorAll('#ga-row-tracks .ga-track-row');
var arr = [];
rows.forEach(function(r) {
arr.push({
value: r.querySelector('.ga-track-val').value || '1',
unit: r.querySelector('.ga-track-unit').value
});
});
return arr;
}

function gaRenderTrackInputs(containerId, tracks, type) {
var el = document.getElementById(containerId);
el.innerHTML = '';
tracks.forEach(function(t, i) {
var row = document.createElement('div');
row.className = 'ga-track-row';
var label = document.createElement('span');
label.className = 'ga-track-label';
label.textContent = (type === 'col' ? '列 ' : '行 ') + (i + 1);
var valInput = document.createElement('input');
valInput.type = 'text';
valInput.className = 'ga-track-val';
valInput.value = t.value;
valInput.oninput = gaUpdate;
var unitSel = document.createElement('select');
unitSel.className = 'ga-track-unit';
['fr','px','%','em','rem','auto','minmax'].forEach(function(u) {
var opt = document.createElement('option');
opt.value = u;
opt.textContent = u;
if (u === t.unit) opt.selected = true;
unitSel.appendChild(opt);
});
unitSel.onchange = gaUpdate;
row.appendChild(label);
row.appendChild(valInput);
row.appendChild(unitSel);
el.appendChild(row);
});
}

function gaReadState() {
gaState.cols = Math.max(1, Math.min(12, parseInt(document.getElementById('ga-cols').value) || 3));
gaState.rows = Math.max(1, Math.min(12, parseInt(document.getElementById('ga-rows').value) || 3));
gaState.colGap = document.getElementById('ga-col-gap').value || '0px';
gaState.rowGap = document.getElementById('ga-row-gap').value || '0px';
gaState.justifyItems = document.getElementById('ga-justify-items').value;
gaState.alignItems = document.getElementById('ga-align-items').value;
gaState.areas = document.getElementById('ga-areas-input').value.trim();
}

function gaSyncTracks() {
var curCols = gaGetColTracks();
var curRows = gaGetRowTracks();
while (curCols.length < gaState.cols) curCols.push({ value: '1', unit: 'fr' });
curCols = curCols.slice(0, gaState.cols);
while (curRows.length < gaState.rows) curRows.push({ value: '100px', unit: '' });
curRows = curRows.slice(0, gaState.rows);
gaState.colTracks = curCols;
gaState.rowTracks = curRows;
gaRenderTrackInputs('ga-col-tracks', curCols, 'col');
gaRenderTrackInputs('ga-row-tracks', curRows, 'row');
}

function gaRenderPreview() {
var grid = document.getElementById('ga-preview-grid');
var colTracks = gaGetColTracks();
var rowTracks = gaGetRowTracks();
var colStr = colTracks.map(gaTrackStr).join(' ');
var rowStr = rowTracks.map(gaTrackStr).join(' ');
grid.style.gridTemplateColumns = colStr;
grid.style.gridTemplateRows = rowStr;
grid.style.columnGap = gaState.colGap;
grid.style.rowGap = gaState.rowGap;
grid.style.justifyItems = gaState.justifyItems;
grid.style.alignItems = gaState.alignItems;
grid.innerHTML = '';

var areasVal = gaState.areas;
if (areasVal) {
try { grid.style.gridTemplateAreas = areasVal; } catch(e) {}
} else {
grid.style.gridTemplateAreas = '';
}

var total = gaState.rows * gaState.cols;
for (var idx = 0; idx < Math.max(total, gaState.items.length); idx++) {
var cell = document.createElement('div');
cell.className = 'ga-cell';
var item = gaState.items[idx];
if (item) {
cell.style.background = item.color;
cell.textContent = item.label || ('アイテム ' + (idx + 1));
if (item.colStart && item.colEnd) {
cell.style.gridColumn = item.colStart + ' / ' + item.colEnd;
}
if (item.rowStart && item.rowEnd) {
cell.style.gridRow = item.rowStart + ' / ' + item.rowEnd;
}
if (item.area) {
cell.style.gridArea = item.area;
}
} else {
cell.style.background = COLORS[idx % COLORS.length];
cell.textContent = 'アイテム ' + (idx + 1);
}
(function(i) {
cell.addEventListener('click', function() {
document.querySelectorAll('#ga-preview-grid .ga-cell').forEach(function(c) { c.classList.remove('ga-selected'); });
cell.classList.add('ga-selected');
});
})(idx);
grid.appendChild(cell);
}
}

function gaRenderItems() {
var list = document.getElementById('ga-items-list');
list.innerHTML = '';
gaState.items.forEach(function(item, i) {
var row = document.createElement('div');
row.className = 'ga-item-row';

var swatch = document.createElement('div');
swatch.className = 'ga-item-swatch';
swatch.style.background = item.color;
row.appendChild(swatch);

function addField(labelText, inputEl) {
var lbl = document.createElement('label');
lbl.textContent = labelText;
row.appendChild(lbl);
row.appendChild(inputEl);
}

var labelInput = document.createElement('input');
labelInput.type = 'text';
labelInput.value = item.label;
labelInput.placeholder = 'ラベル';
labelInput.oninput = (function(idx) { return function() { gaState.items[idx].label = this.value; gaRenderPreview(); gaBuildCss(); }; })(i);
addField('ラベル:', labelInput);

var csInput = document.createElement('input');
csInput.type = 'number';
csInput.value = item.colStart || '';
csInput.placeholder = '開始列';
csInput.min = 1;
csInput.oninput = (function(idx) { return function() { gaState.items[idx].colStart = this.value; gaRenderPreview(); gaBuildCss(); }; })(i);
addField('col-start:', csInput);

var ceInput = document.createElement('input');
ceInput.type = 'number';
ceInput.value = item.colEnd || '';
ceInput.placeholder = '終了列';
ceInput.min = 1;
ceInput.oninput = (function(idx) { return function() { gaState.items[idx].colEnd = this.value; gaRenderPreview(); gaBuildCss(); }; })(i);
addField('col-end:', ceInput);

var rsInput = document.createElement('input');
rsInput.type = 'number';
rsInput.value = item.rowStart || '';
rsInput.placeholder = '開始行';
rsInput.min = 1;
rsInput.oninput = (function(idx) { return function() { gaState.items[idx].rowStart = this.value; gaRenderPreview(); gaBuildCss(); }; })(i);
addField('row-start:', rsInput);

var reInput = document.createElement('input');
reInput.type = 'number';
reInput.value = item.rowEnd || '';
reInput.placeholder = '終了行';
reInput.min = 1;
reInput.oninput = (function(idx) { return function() { gaState.items[idx].rowEnd = this.value; gaRenderPreview(); gaBuildCss(); }; })(i);
addField('row-end:', reInput);

var areaInput = document.createElement('input');
areaInput.type = 'text';
areaInput.value = item.area || '';
areaInput.placeholder = 'grid-area名';
areaInput.oninput = (function(idx) { return function() { gaState.items[idx].area = this.value; gaRenderPreview(); gaBuildCss(); }; })(i);
addField('エリア名:', areaInput);

var delBtn = document.createElement('button');
delBtn.className = 'ga-item-btn';
delBtn.textContent = '削除';
delBtn.onclick = (function(idx) { return function() { gaState.items.splice(idx, 1); gaRenderItems(); gaRenderPreview(); gaBuildCss(); }; })(i);
row.appendChild(delBtn);

list.appendChild(row);
});
}

function gaAddItem() {
var n = gaState.items.length;
gaState.items.push({
label: 'アイテム ' + (n + 1),
color: COLORS[n % COLORS.length],
colStart: '', colEnd: '',
rowStart: '', rowEnd: '',
area: ''
});
gaRenderItems();
gaRenderPreview();
gaBuildCss();
}

function gaEsc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function gaHl(prop, val) {
return '<span class="ga-prop">' + gaEsc(prop) + '</span>: <span class="ga-val">' + gaEsc(val) + '</span>;';
}

function gaBuildCss() {
var colTracks = gaGetColTracks();
var rowTracks = gaGetRowTracks();
var colStr = colTracks.map(gaTrackStr).join(' ');
var rowStr = rowTracks.map(gaTrackStr).join(' ');

var lines = [];
lines.push('<span class="ga-sel">.grid-container</span> <span class="ga-brace">{</span>');
lines.push('  ' + gaHl('display', 'grid'));
lines.push('  ' + gaHl('grid-template-columns', colStr));
lines.push('  ' + gaHl('grid-template-rows', rowStr));
if (gaState.colGap && gaState.colGap !== '0') lines.push('  ' + gaHl('column-gap', gaState.colGap));
if (gaState.rowGap && gaState.rowGap !== '0') lines.push('  ' + gaHl('row-gap', gaState.rowGap));
if (gaState.justifyItems !== 'stretch') lines.push('  ' + gaHl('justify-items', gaState.justifyItems));
if (gaState.alignItems !== 'stretch') lines.push('  ' + gaHl('align-items', gaState.alignItems));
if (gaState.areas) {
var areaLines = gaState.areas.split('\n').map(function(l){ return l.trim(); }).filter(Boolean);
lines.push('  ' + gaHl('grid-template-areas', areaLines.join('\n    ')));
}
lines.push('<span class="ga-brace">}</span>');

gaState.items.forEach(function(item, i) {
var hasProps = (item.colStart && item.colEnd) || (item.rowStart && item.rowEnd) || item.area;
if (!hasProps) return;
lines.push('');
lines.push('<span class="ga-sel">.grid-item-' + (i+1) + '</span> <span class="ga-brace">{</span>');
if (item.area) {
lines.push('  ' + gaHl('grid-area', item.area));
} else {
if (item.colStart && item.colEnd) lines.push('  ' + gaHl('grid-column', item.colStart + ' / ' + item.colEnd));
if (item.rowStart && item.rowEnd) lines.push('  ' + gaHl('grid-row', item.rowStart + ' / ' + item.rowEnd));
}
lines.push('<span class="ga-brace">}</span>');
});

document.getElementById('ga-css-output').innerHTML = lines.join('\n');

// ショートハンド
var sh = 'grid-template-columns: ' + colStr + ';\n';
sh += 'grid-template-rows: ' + rowStr + ';\n';
if (gaState.colGap === gaState.rowGap) {
sh += 'gap: ' + gaState.rowGap + ';';
} else {
sh += 'gap: ' + gaState.rowGap + ' ' + gaState.colGap + ';';
}
document.getElementById('ga-shorthand-output').textContent = sh;
}

function gaUpdate() {
gaReadState();
gaSyncTracks();
gaRenderPreview();
gaRenderItems();
gaBuildCss();
}

window.gaAddItem = gaAddItem;

window.gaLoadPreset = function(name) {
var presets = {
dashboard: {
cols: 4, rows: 3,
colTracks: [{value:'1',unit:'fr'},{value:'1',unit:'fr'},{value:'1',unit:'fr'},{value:'300px',unit:''}],
rowTracks: [{value:'80px',unit:''},{value:'1',unit:'fr'},{value:'60px',unit:''}],
colGap: '16px', rowGap: '16px',
areas: '"header header header header"\n"sidebar main main aside"\n"footer footer footer footer"',
items: [
{label:'ヘッダー',color:'#6366f1',area:'header'},
{label:'サイドバー',color:'#f59e0b',area:'sidebar'},
{label:'メイン',color:'#10b981',area:'main'},
{label:'アサイド',color:'#8b5cf6',area:'aside'},
{label:'フッター',color:'#ef4444',area:'footer'}
]
},
gallery: {
cols: 3, rows: 3,
colTracks: [{value:'1',unit:'fr'},{value:'1',unit:'fr'},{value:'1',unit:'fr'}],
rowTracks: [{value:'200px',unit:''},{value:'200px',unit:''},{value:'200px',unit:''}],
colGap: '8px', rowGap: '8px',
areas: '',
items: []
},
magazine: {
cols: 3, rows: 4,
colTracks: [{value:'2',unit:'fr'},{value:'1',unit:'fr'},{value:'1',unit:'fr'}],
rowTracks: [{value:'60px',unit:''},{value:'300px',unit:''},{value:'200px',unit:''},{value:'60px',unit:''}],
colGap: '20px', rowGap: '16px',
areas: '"nav nav nav"\n"hero hero sidebar"\n"article1 article2 sidebar"\n"footer footer footer"',
items: [
{label:'ナビ',color:'#1a1a2e',area:'nav'},
{label:'ヒーロー',color:'#6366f1',area:'hero'},
{label:'サイドバー',color:'#f59e0b',area:'sidebar'},
{label:'記事1',color:'#10b981',area:'article1'},
{label:'記事2',color:'#06b6d4',area:'article2'},
{label:'フッター',color:'#ef4444',area:'footer'}
]
},
holygrail: {
cols: 3, rows: 3,
colTracks: [{value:'200px',unit:''},{value:'1',unit:'fr'},{value:'200px',unit:''}],
rowTracks: [{value:'60px',unit:''},{value:'1',unit:'fr'},{value:'60px',unit:''}],
colGap: '0px', rowGap: '0px',
areas: '"header header header"\n"nav main aside"\n"footer footer footer"',
items: [
{label:'ヘッダー',color:'#6366f1',area:'header'},
{label:'ナビ',color:'#f59e0b',area:'nav'},
{label:'メイン',color:'#10b981',area:'main'},
{label:'アサイド',color:'#8b5cf6',area:'aside'},
{label:'フッター',color:'#ef4444',area:'footer'}
]
},
cards: {
cols: 3, rows: 2,
colTracks: [{value:'repeat(auto-fill, minmax(200px, 1fr))',unit:''}],
rowTracks: [{value:'auto',unit:''},{value:'auto',unit:''}],
colGap: '16px', rowGap: '16px',
areas: '',
items: []
},
reset: {
cols: 3, rows: 3,
colTracks: null, rowTracks: null,
colGap: '16px', rowGap: '16px',
areas: '',
items: []
}
};
var p = presets[name];
if (!p) return;
document.getElementById('ga-cols').value = p.cols;
document.getElementById('ga-rows').value = p.rows;
document.getElementById('ga-col-gap').value = p.colGap;
document.getElementById('ga-row-gap').value = p.rowGap;
document.getElementById('ga-areas-input').value = p.areas || '';
gaState.cols = p.cols;
gaState.rows = p.rows;
gaState.colGap = p.colGap;
gaState.rowGap = p.rowGap;
gaState.areas = p.areas || '';
gaState.items = (p.items || []).map(function(it) {
return Object.assign({colStart:'',colEnd:'',rowStart:'',rowEnd:''}, it);
});
if (p.colTracks) {
gaState.colTracks = p.colTracks;
gaRenderTrackInputs('ga-col-tracks', p.colTracks, 'col');
} else {
var def = gaDefaultTracks(p.cols, 'col');
gaState.colTracks = def;
gaRenderTrackInputs('ga-col-tracks', def, 'col');
}
if (p.rowTracks) {
gaState.rowTracks = p.rowTracks;
gaRenderTrackInputs('ga-row-tracks', p.rowTracks, 'row');
} else {
var defr = gaDefaultTracks(p.rows, 'row');
gaState.rowTracks = defr;
gaRenderTrackInputs('ga-row-tracks', defr, 'row');
}
gaRenderPreview();
gaRenderItems();
gaBuildCss();
};

window.gaCopyCss = function() {
var el = document.getElementById('ga-css-output');
var text = el.innerText || el.textContent;
navigator.clipboard.writeText(text).then(function() {
var btn = document.getElementById('ga-copy-btn');
btn.textContent = 'コピーしました!';
btn.classList.add('ga-copied');
setTimeout(function() { btn.textContent = 'CSSをコピー'; btn.classList.remove('ga-copied'); }, 1800);
});
};

window.gaCopyShorthand = function() {
var text = document.getElementById('ga-shorthand-output').textContent;
navigator.clipboard.writeText(text).then(function() {
var btn = document.getElementById('ga-copy-sh-btn');
btn.textContent = 'コピーしました!';
btn.classList.add('ga-copied');
setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('ga-copied'); }, 1800);
});
};

// 初期化
gaState.colTracks = gaDefaultTracks(3, 'col');
gaState.rowTracks = [{value:'120px',unit:''},{value:'120px',unit:''},{value:'120px',unit:''}];
gaRenderTrackInputs('ga-col-tracks', gaState.colTracks, 'col');
gaRenderTrackInputs('ga-row-tracks', gaState.rowTracks, 'row');
gaReadState();
gaRenderPreview();
gaRenderItems();
gaBuildCss();
})();
</script>
</div>

---

### 関連ツール

> Flexboxレイアウトを構築 → [CSS Flexboxジェネレーター](/ja/tools/flexbox-generator/)

> ボックスシャドウを生成 → [CSSボックスシャドウジェネレーター](/ja/tools/box-shadow-generator/)

> グラデーションを作成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
