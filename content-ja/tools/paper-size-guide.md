---
title: "用紙サイズガイド - A判・B判・レターサイズ一覧"
date: 2025-05-15
description: "用紙サイズの完全リファレンス。A0〜A10、B0〜B10（ISO・JIS両対応）、レター・リーガル・タブロイドをmm・cm・インチで比較。ビジュアル確認付き。"
categories: ["無料ツール"]
slug: "paper-size-guide"
ShowToc: false
cover:
  image: "/images/covers/paper-size-guide.png"
  alt: "用紙サイズガイド"
---

<div id="ps-app">
<style>
#ps-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Yu Gothic", Meiryo, sans-serif;
max-width: 960px;
margin: 0 auto;
color: #1a1a2e;
}
#ps-app h2 {
font-size: 1.4rem;
font-weight: 700;
margin: 1.5rem 0 0.75rem;
color: #16213e;
border-left: 4px solid #0f3460;
padding-left: 0.6rem;
}
#ps-app .ps-intro {
background: #f0f4ff;
border-radius: 8px;
padding: 1rem 1.2rem;
margin-bottom: 1.2rem;
font-size: 0.95rem;
color: #333;
line-height: 1.7;
}
#ps-app .ps-controls {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
align-items: center;
margin-bottom: 1rem;
}
#ps-app .ps-controls label {
font-size: 0.88rem;
font-weight: 600;
color: #555;
margin-right: 0.25rem;
}
#ps-app .ps-unit-btn {
padding: 0.35rem 0.9rem;
border: 2px solid #0f3460;
background: #fff;
color: #0f3460;
border-radius: 20px;
cursor: pointer;
font-size: 0.85rem;
font-weight: 600;
transition: all 0.18s;
}
#ps-app .ps-unit-btn.active {
background: #0f3460;
color: #fff;
}
#ps-app .ps-unit-btn:hover:not(.active) {
background: #e8edf7;
}
#ps-app .ps-filter-btn {
padding: 0.3rem 0.8rem;
border: 1px solid #bbb;
background: #fff;
color: #444;
border-radius: 20px;
cursor: pointer;
font-size: 0.82rem;
transition: all 0.18s;
margin-left: 0.5rem;
}
#ps-app .ps-filter-btn.active {
background: #0f3460;
color: #fff;
border-color: #0f3460;
}
#ps-app .ps-table-wrap {
overflow-x: auto;
border-radius: 8px;
box-shadow: 0 1px 6px rgba(0,0,0,0.08);
margin-bottom: 1.5rem;
}
#ps-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
background: #fff;
}
#ps-app thead th {
background: #0f3460;
color: #fff;
padding: 0.6rem 0.75rem;
text-align: left;
font-weight: 600;
white-space: nowrap;
}
#ps-app tbody tr {
border-bottom: 1px solid #e8ecf0;
cursor: pointer;
transition: background 0.15s;
}
#ps-app tbody tr:hover {
background: #f0f4ff;
}
#ps-app tbody tr.highlighted {
background: #dce8ff;
font-weight: 600;
}
#ps-app tbody td {
padding: 0.5rem 0.75rem;
white-space: nowrap;
}
#ps-app tbody td:first-child {
font-weight: 700;
color: #0f3460;
}
#ps-app .ps-badge {
display: inline-block;
font-size: 0.72rem;
padding: 0.1rem 0.45rem;
border-radius: 10px;
font-weight: 600;
vertical-align: middle;
margin-left: 0.3rem;
}
#ps-app .badge-iso  { background: #d4edda; color: #155724; }
#ps-app .badge-jis  { background: #cce5ff; color: #004085; }
#ps-app .badge-us   { background: #fff3cd; color: #856404; }
#ps-app .ps-canvas-wrap {
background: #f8f9fc;
border: 1px solid #dde3ee;
border-radius: 8px;
padding: 1rem;
margin-bottom: 1.5rem;
text-align: center;
}
#ps-app .ps-canvas-wrap canvas {
max-width: 100%;
border-radius: 4px;
}
#ps-app .ps-canvas-label {
font-size: 0.82rem;
color: #666;
margin-top: 0.5rem;
}
#ps-app .ps-detail-panel {
background: #fff;
border: 1px solid #c8d6f0;
border-radius: 8px;
padding: 1rem 1.2rem;
margin-bottom: 1.5rem;
display: none;
}
#ps-app .ps-detail-panel.visible {
display: block;
}
#ps-app .ps-detail-panel h3 {
margin: 0 0 0.6rem;
font-size: 1.15rem;
color: #0f3460;
}
#ps-app .ps-detail-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
gap: 0.6rem;
}
#ps-app .ps-detail-item {
background: #f0f4ff;
border-radius: 6px;
padding: 0.5rem 0.75rem;
}
#ps-app .ps-detail-item .di-label {
font-size: 0.75rem;
color: #666;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#ps-app .ps-detail-item .di-value {
font-size: 1rem;
font-weight: 700;
color: #0f3460;
}
#ps-app .ps-usage {
font-size: 0.88rem;
color: #444;
margin-top: 0.6rem;
background: #fffbe6;
border-left: 3px solid #f0b429;
padding: 0.4rem 0.7rem;
border-radius: 0 4px 4px 0;
}
#ps-app .ps-cta {
background: linear-gradient(135deg, #e8f4fd 0%, #f0f8e8 100%);
border: 1px solid #b8d8f0;
border-radius: 8px;
padding: 1rem 1.2rem;
margin: 1.5rem 0;
font-size: 0.92rem;
}
#ps-app .ps-cta a {
color: #0f3460;
font-weight: 700;
text-decoration: underline;
}
#ps-app .ps-section-sep {
border: none;
border-top: 2px solid #e8ecf0;
margin: 1.5rem 0;
}
#ps-app .ps-note {
font-size: 0.82rem;
color: #777;
background: #f8f8f8;
border-radius: 6px;
padding: 0.6rem 0.9rem;
margin-bottom: 1rem;
line-height: 1.6;
}
</style>

<div class="ps-intro">
<strong>用紙サイズ早見表</strong> — ISO A判・ISO B判・JIS B判・US判のサイズを一覧表示。mm・cm・インチに切り替えてすぐ確認。行をクリックするとビジュアル比較と詳細が表示されます。
</div>

<div class="ps-note">
<strong>JIS B判について：</strong>JIS（日本産業規格）のB判はISO B判と異なります。日本国内ではJIS B判が主に流通しており、B5ノートやB4コピー用紙はJIS規格です。ISO B判は国際規格です。
</div>

<div class="ps-controls">
<label>単位：</label>
<button class="ps-unit-btn active" onclick="psSetUnit('mm')">mm</button>
<button class="ps-unit-btn" onclick="psSetUnit('cm')">cm</button>
<button class="ps-unit-btn" onclick="psSetUnit('in')">インチ</button>
<span style="display:inline-block;width:1rem;"></span>
<label>シリーズ：</label>
<button class="ps-filter-btn active" onclick="psSetFilter('all')">すべて</button>
<button class="ps-filter-btn" onclick="psSetFilter('A')">ISO A判</button>
<button class="ps-filter-btn" onclick="psSetFilter('ISOB')">ISO B判</button>
<button class="ps-filter-btn" onclick="psSetFilter('JISB')">JIS B判</button>
<button class="ps-filter-btn" onclick="psSetFilter('US')">US判</button>
</div>

<div id="ps-detail" class="ps-detail-panel">
<h3 id="ps-detail-name"></h3>
<div class="ps-detail-grid" id="ps-detail-grid"></div>
<div class="ps-usage" id="ps-detail-usage"></div>
</div>

<div class="ps-canvas-wrap">
<canvas id="ps-canvas" width="780" height="240"></canvas>
<div class="ps-canvas-label" id="ps-canvas-label">行をクリックするとビジュアル比較でそのサイズをハイライト表示します</div>
</div>

<div class="ps-table-wrap">
<table id="ps-table">
<thead>
<tr>
<th>サイズ</th>
<th>規格</th>
<th>横幅</th>
<th>縦幅</th>
<th>面積</th>
<th>縦横比</th>
<th>主な用途</th>
</tr>
</thead>
<tbody id="ps-tbody"></tbody>
</table>
</div>

<hr class="ps-section-sep">

<div class="ps-cta">
書類管理を効率化 &rarr; <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で帳票を自動作成</a>
</div>

<h2>用紙サイズの基礎知識</h2>
<div class="ps-intro" style="background:#fff;border:1px solid #dde3ee;">
<p><strong>ISO A判</strong>：世界で最も広く使われる規格。A0の面積はちょうど1m²で、縦横比は1:√2（≈1:1.414）。A1はA0の半分、A2はA1の半分、と続く。A4が世界標準の書類サイズ。</p>
<p><strong>JIS B判（日本のB判）</strong>：日本独自の規格。ISO B判とは寸法が異なる。B0=1030×1456mm。B5ノート・B4コピー用紙など日本国内で広く流通。面積はA判の1.5倍に設定されている。</p>
<p><strong>ISO B判</strong>：国際規格のB判。B0=1000×1414mm。パスポート（B7）やポスターなどに使用。日本国内ではJIS B判の方が一般的。</p>
<p><strong>US判（レター等）</strong>：レター（8.5×11インチ）は米国・カナダの標準書類サイズ。リーガルは法律文書用に縦が長い。タブロイドは新聞・大判印刷に使用。</p>
</div>

<script>
(function() {
var PS_DATA = [
// ISO A series (mm)
{ name:"A0",  series:"A",    seriesLabel:"ISO A判", w:841,  h:1189, badge:"iso", use:"大型ポスター、建築図面、設計図" },
{ name:"A1",  series:"A",    seriesLabel:"ISO A判", w:594,  h:841,  badge:"iso", use:"ポスター、フリップチャート、設計図" },
{ name:"A2",  series:"A",    seriesLabel:"ISO A判", w:420,  h:594,  badge:"iso", use:"大型ポスター、アートプリント" },
{ name:"A3",  series:"A",    seriesLabel:"ISO A判", w:297,  h:420,  badge:"iso", use:"新聞、スプレッドシート、ポスター、プレゼン資料" },
{ name:"A4",  series:"A",    seriesLabel:"ISO A判", w:210,  h:297,  badge:"iso", use:"標準書類・レポート・フォーム（世界標準）" },
{ name:"A5",  series:"A",    seriesLabel:"ISO A判", w:148,  h:210,  badge:"iso", use:"ノート、小冊子、チラシ" },
{ name:"A6",  series:"A",    seriesLabel:"ISO A判", w:105,  h:148,  badge:"iso", use:"ポストカード、文庫本、メモ帳" },
{ name:"A7",  series:"A",    seriesLabel:"ISO A判", w:74,   h:105,  badge:"iso", use:"名刺（一部地域）、小型カード" },
{ name:"A8",  series:"A",    seriesLabel:"ISO A判", w:52,   h:74,   badge:"iso", use:"ラベル、小型カード" },
{ name:"A9",  series:"A",    seriesLabel:"ISO A判", w:37,   h:52,   badge:"iso", use:"切手サイズ" },
{ name:"A10", series:"A",    seriesLabel:"ISO A判", w:26,   h:37,   badge:"iso", use:"極小ラベル・スタンプ用途" },
// JIS B series (mm) — Japanese standard
{ name:"B0（JIS）", series:"JISB", seriesLabel:"JIS B判", w:1030, h:1456, badge:"jis", use:"大型ポスター、横断幕" },
{ name:"B1（JIS）", series:"JISB", seriesLabel:"JIS B判", w:728,  h:1030, badge:"jis", use:"大型ポスター、地図" },
{ name:"B2（JIS）", series:"JISB", seriesLabel:"JIS B判", w:515,  h:728,  badge:"jis", use:"ポスター、アートプリント" },
{ name:"B3（JIS）", series:"JISB", seriesLabel:"JIS B判", w:364,  h:515,  badge:"jis", use:"ポスター" },
{ name:"B4（JIS）", series:"JISB", seriesLabel:"JIS B判", w:257,  h:364,  badge:"jis", use:"コピー用紙、印刷物、新聞" },
{ name:"B5（JIS）", series:"JISB", seriesLabel:"JIS B判", w:182,  h:257,  badge:"jis", use:"ノート、教科書、週刊誌（日本で最も一般的なB5）" },
{ name:"B6（JIS）", series:"JISB", seriesLabel:"JIS B判", w:128,  h:182,  badge:"jis", use:"単行本、手帳" },
{ name:"B7（JIS）", series:"JISB", seriesLabel:"JIS B判", w:91,   h:128,  badge:"jis", use:"手帳、小型ノート" },
{ name:"B8（JIS）", series:"JISB", seriesLabel:"JIS B判", w:64,   h:91,   badge:"jis", use:"カード類" },
{ name:"B9（JIS）", series:"JISB", seriesLabel:"JIS B判", w:45,   h:64,   badge:"jis", use:"小型ラベル" },
{ name:"B10（JIS）",series:"JISB", seriesLabel:"JIS B判", w:32,   h:45,   badge:"jis", use:"切手サイズ用途" },
// ISO B series (mm)
{ name:"B0（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:1000, h:1414, badge:"iso", use:"大型ポスター、バナー" },
{ name:"B1（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:707,  h:1000, badge:"iso", use:"大型ポスター、地図" },
{ name:"B2（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:500,  h:707,  badge:"iso", use:"ポスター、アートプリント" },
{ name:"B3（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:353,  h:500,  badge:"iso", use:"ポスター" },
{ name:"B4（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:250,  h:353,  badge:"iso", use:"雑誌、新聞" },
{ name:"B5（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:176,  h:250,  badge:"iso", use:"書籍（国際ISO規格）" },
{ name:"B6（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:125,  h:176,  badge:"iso", use:"書籍、ポケットサイズ" },
{ name:"B7（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:88,   h:125,  badge:"iso", use:"パスポートサイズ" },
{ name:"B8（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:62,   h:88,   badge:"iso", use:"カード類" },
{ name:"B9（ISO）", series:"ISOB", seriesLabel:"ISO B判", w:44,   h:62,   badge:"iso", use:"小型ラベル" },
{ name:"B10（ISO）",series:"ISOB", seriesLabel:"ISO B判", w:31,   h:44,   badge:"iso", use:"切手サイズ用途" },
// US sizes (mm)
{ name:"レター（Letter）",    series:"US", seriesLabel:"US判", w:216, h:279,  badge:"us", use:"米国・カナダの標準書類サイズ（A4相当）" },
{ name:"リーガル（Legal）",   series:"US", seriesLabel:"US判", w:216, h:356,  badge:"us", use:"米国の法律文書、契約書" },
{ name:"タブロイド（Tabloid）",series:"US",seriesLabel:"US判", w:279, h:432,  badge:"us", use:"新聞、大判印刷（横向き=レジャー）" },
{ name:"エグゼクティブ",      series:"US", seriesLabel:"US判", w:184, h:267,  badge:"us", use:"ビジネスレター、個人用便箋" },
{ name:"ハーフレター",        series:"US", seriesLabel:"US判", w:140, h:216,  badge:"us", use:"メモ帳、小冊子" },
];

var currentUnit = 'mm';
var currentFilter = 'all';
var highlightedName = null;

function round2(n) { return Math.round(n * 100) / 100; }

function convertW(mmVal) {
if (currentUnit === 'cm') return round2(mmVal / 10);
if (currentUnit === 'in') return round2(mmVal / 25.4);
return mmVal;
}
function unitLabel() {
return currentUnit === 'in' ? 'インチ' : ' ' + currentUnit;
}
function areaLabel(w, h) {
var a;
if (currentUnit === 'mm') a = round2(w * h / 1000) + ' cm²';
else if (currentUnit === 'cm') a = round2(w / 10 * h / 10) + ' cm²';
else a = round2(w / 25.4 * h / 25.4) + ' in²';
return a;
}
function aspectRatio(w, h) {
return '1 : ' + round2(h / w);
}

function badgeHtml(badge) {
if (badge === 'jis') return '<span class="ps-badge badge-jis">JIS</span>';
if (badge === 'us')  return '<span class="ps-badge badge-us">US</span>';
return '<span class="ps-badge badge-iso">ISO</span>';
}

function getFilteredData() {
if (currentFilter === 'all') return PS_DATA;
if (currentFilter === 'A')    return PS_DATA.filter(function(d) { return d.series === 'A'; });
if (currentFilter === 'ISOB') return PS_DATA.filter(function(d) { return d.series === 'ISOB'; });
if (currentFilter === 'JISB') return PS_DATA.filter(function(d) { return d.series === 'JISB'; });
if (currentFilter === 'US')   return PS_DATA.filter(function(d) { return d.series === 'US'; });
return PS_DATA;
}

function renderTable() {
var data = getFilteredData();
var tbody = document.getElementById('ps-tbody');
tbody.innerHTML = '';
data.forEach(function(row) {
var tr = document.createElement('tr');
if (row.name === highlightedName) tr.classList.add('highlighted');
tr.innerHTML =
'<td>' + row.name + '</td>' +
'<td>' + row.seriesLabel + badgeHtml(row.badge) + '</td>' +
'<td>' + convertW(row.w) + unitLabel() + '</td>' +
'<td>' + convertW(row.h) + unitLabel() + '</td>' +
'<td>' + areaLabel(row.w, row.h) + '</td>' +
'<td>' + aspectRatio(row.w, row.h) + '</td>' +
'<td style="white-space:normal;min-width:180px;font-size:0.82rem;color:#555;">' + row.use + '</td>';
tr.addEventListener('click', function() { psSelectRow(row, tr); });
tbody.appendChild(tr);
});
}

function psSelectRow(row, tr) {
var prev = document.querySelectorAll('#ps-tbody tr.highlighted');
prev.forEach(function(r) { r.classList.remove('highlighted'); });
if (highlightedName === row.name) {
highlightedName = null;
document.getElementById('ps-detail').classList.remove('visible');
renderCanvas(null);
return;
}
highlightedName = row.name;
tr.classList.add('highlighted');
showDetail(row);
renderCanvas(row);
}

function showDetail(row) {
var panel = document.getElementById('ps-detail');
panel.classList.add('visible');
document.getElementById('ps-detail-name').textContent = row.name + ' の詳細';
var grid = document.getElementById('ps-detail-grid');
grid.innerHTML =
'<div class="ps-detail-item"><div class="di-label">横幅</div><div class="di-value">' + convertW(row.w) + unitLabel() + '</div></div>' +
'<div class="ps-detail-item"><div class="di-label">縦幅</div><div class="di-value">' + convertW(row.h) + unitLabel() + '</div></div>' +
'<div class="ps-detail-item"><div class="di-label">横幅 (mm)</div><div class="di-value">' + row.w + ' mm</div></div>' +
'<div class="ps-detail-item"><div class="di-label">縦幅 (mm)</div><div class="di-value">' + row.h + ' mm</div></div>' +
'<div class="ps-detail-item"><div class="di-label">横幅 (インチ)</div><div class="di-value">' + round2(row.w/25.4) + '"</div></div>' +
'<div class="ps-detail-item"><div class="di-label">縦幅 (インチ)</div><div class="di-value">' + round2(row.h/25.4) + '"</div></div>' +
'<div class="ps-detail-item"><div class="di-label">面積</div><div class="di-value">' + areaLabel(row.w, row.h) + '</div></div>' +
'<div class="ps-detail-item"><div class="di-label">縦横比</div><div class="di-value">' + aspectRatio(row.w, row.h) + '</div></div>';
document.getElementById('ps-detail-usage').textContent = '主な用途：' + row.use;
}

function renderCanvas(highlighted) {
var canvas = document.getElementById('ps-canvas');
var ctx = canvas.getContext('2d');
var W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);

var displaySizes = [
{ name:'A0',       w:841,  h:1189 },
{ name:'A1',       w:594,  h:841  },
{ name:'A2',       w:420,  h:594  },
{ name:'A3',       w:297,  h:420  },
{ name:'A4',       w:210,  h:297  },
{ name:'A5',       w:148,  h:210  },
{ name:'B5（JIS）', w:182,  h:257  },
{ name:'B4（JIS）', w:257,  h:364  },
{ name:'レター',   w:216,  h:279  },
];

if (highlighted) {
var found = displaySizes.some(function(s) { return s.name === highlighted.name; });
if (!found) displaySizes.push({ name: highlighted.name, w: highlighted.w, h: highlighted.h });
}

var maxH = Math.max.apply(null, displaySizes.map(function(s) { return s.h; }));
var padding = 10;
var labelH = 20;
var drawH = H - padding * 2 - labelH;
var scale = drawH / maxH;

var totalW = displaySizes.reduce(function(acc, s) { return acc + s.w * scale + 6; }, 0);
var x = (W - totalW) / 2;

displaySizes.forEach(function(s) {
var sw = s.w * scale;
var sh = s.h * scale;
var y = padding + (drawH - sh);
var isHL = highlighted && s.name === highlighted.name;

ctx.save();
if (isHL) {
ctx.fillStyle = '#2563eb22';
ctx.strokeStyle = '#2563eb';
ctx.lineWidth = 2.5;
} else {
ctx.fillStyle = '#e8edf722';
ctx.strokeStyle = '#9aaac8';
ctx.lineWidth = 1.2;
}
ctx.fillRect(x, y, sw, sh);
ctx.strokeRect(x, y, sw, sh);

ctx.fillStyle = isHL ? '#2563eb' : '#555';
ctx.font = (isHL ? 'bold ' : '') + '10px sans-serif';
ctx.textAlign = 'center';
// Truncate long names for canvas
var label = s.name.replace('（JIS）','').replace('（ISO）','');
ctx.fillText(label, x + sw / 2, H - padding + 4);

if (sw > 28 && sh > 22) {
ctx.fillStyle = isHL ? '#1e40af' : '#888';
ctx.font = '9px sans-serif';
ctx.fillText(s.w + 'x' + s.h, x + sw / 2, y + sh / 2);
}
ctx.restore();
x += sw + 6;
});

var labelText = highlighted
? 'ビジュアル比較 — ' + highlighted.name + ' をハイライト中（' + highlighted.w + ' x ' + highlighted.h + ' mm）'
: '行をクリックするとビジュアル比較でそのサイズをハイライト表示します';
document.getElementById('ps-canvas-label').textContent = labelText;
}

window.psSetUnit = function(u) {
currentUnit = u;
document.querySelectorAll('#ps-app .ps-unit-btn').forEach(function(b) {
var map = { 'mm':'mm', 'cm':'cm', 'in':'インチ' };
b.classList.toggle('active', b.textContent === map[u]);
});
if (highlightedName) {
var row = PS_DATA.find(function(r) { return r.name === highlightedName; });
if (row) showDetail(row);
}
renderTable();
};

window.psSetFilter = function(f) {
currentFilter = f;
var labelMap = { 'all':'すべて', 'A':'ISO A判', 'ISOB':'ISO B判', 'JISB':'JIS B判', 'US':'US判' };
document.querySelectorAll('#ps-app .ps-filter-btn').forEach(function(b) {
b.classList.toggle('active', b.textContent === labelMap[f]);
});
renderTable();
};

// Init
renderTable();
renderCanvas(null);
})();
</script>

</div>
