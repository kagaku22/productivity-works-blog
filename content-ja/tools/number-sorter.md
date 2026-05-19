---
title: "数値ソートツール - 数字を昇順・降順に並べ替え 無料オンライン"
date: 2025-06-28
description: "数字を昇順・降順にワンクリックで並べ替え。重複削除、件数・最小値・最大値・平均・中央値・合計を即時表示。テキストのアルファベット順ソートにも対応。無料、登録不要。"
categories: ["無料ツール"]
tags: ["数値ソート", "並べ替え", "昇順", "降順", "重複削除", "統計", "無料ツール"]
slug: "number-sorter"
aliases: ["/ja/tools/number-sorter/"]
cover:
  image: "/images/covers/number-sorter-ja.png"
  alt: "数値ソートツール"
ShowToc: false
---

<div id="ns-app">

<style>
#ns-app {
font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Noto Sans JP', 'Meiryo', system-ui, sans-serif;
background: #0f0f13;
color: #e2e8f0;
border-radius: 12px;
padding: 24px;
margin: 0 auto;
max-width: 900px;
box-sizing: border-box;
}

#ns-app * {
box-sizing: border-box;
}

#ns-app h2 {
font-size: 1.05rem;
font-weight: 600;
color: #f1f5f9;
margin: 0 0 10px 0;
}

#ns-app .ns-row {
display: flex;
gap: 16px;
margin-bottom: 20px;
}

@media (max-width: 640px) {
#ns-app .ns-row {
flex-direction: column;
}
}

#ns-app .ns-col {
flex: 1;
display: flex;
flex-direction: column;
}

#ns-app textarea {
width: 100%;
flex: 1;
min-height: 200px;
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
color: #e2e8f0;
font-size: 0.95rem;
padding: 12px 14px;
resize: vertical;
font-family: 'Fira Mono', 'Consolas', monospace;
transition: border-color 0.2s;
outline: none;
line-height: 1.6;
}

#ns-app textarea:focus {
border-color: #6366f1;
}

#ns-app .ns-label {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #6366f1;
margin-bottom: 6px;
}

#ns-app .ns-controls {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 16px;
align-items: center;
}

#ns-app .ns-btn {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 6px;
color: #cbd5e1;
font-size: 0.82rem;
padding: 6px 14px;
cursor: pointer;
transition: all 0.18s;
font-family: inherit;
font-weight: 500;
}

#ns-app .ns-btn:hover {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}

#ns-app .ns-btn.active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}

#ns-app .ns-btn.success {
background: #16a34a;
border-color: #16a34a;
color: #fff;
}

#ns-app .ns-separator {
width: 1px;
height: 28px;
background: #2d2d3d;
margin: 0 2px;
}

#ns-app .ns-toggle {
display: flex;
align-items: center;
gap: 6px;
font-size: 0.82rem;
color: #94a3b8;
cursor: pointer;
user-select: none;
padding: 6px 10px;
border: 1px solid #2d2d3d;
border-radius: 6px;
background: #1a1a24;
transition: all 0.18s;
}

#ns-app .ns-toggle:hover {
border-color: #6366f1;
color: #e2e8f0;
}

#ns-app .ns-toggle input[type="checkbox"] {
accent-color: #6366f1;
width: 14px;
height: 14px;
cursor: pointer;
}

#ns-app .ns-stats {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(110px, 1fr));
gap: 8px;
margin-bottom: 16px;
}

#ns-app .ns-stat-card {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 10px 14px;
text-align: center;
}

#ns-app .ns-stat-label {
font-size: 0.7rem;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #64748b;
margin-bottom: 4px;
}

#ns-app .ns-stat-val {
font-size: 1.05rem;
font-weight: 700;
color: #6366f1;
font-family: 'Fira Mono', 'Consolas', monospace;
word-break: break-all;
}

#ns-app .ns-output-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 6px;
}

#ns-app .ns-mode-badge {
font-size: 0.7rem;
background: #1e1e2e;
border: 1px solid #2d2d3d;
border-radius: 4px;
padding: 2px 8px;
color: #64748b;
font-weight: 600;
letter-spacing: 0.04em;
}

#ns-app .ns-error {
color: #f87171;
font-size: 0.82rem;
margin-top: 6px;
min-height: 1.2em;
}
</style>

<div class="ns-controls">
<button class="ns-btn active" id="ns-asc" onclick="nsSetOrder('asc')">昇順 ↑</button>
<button class="ns-btn" id="ns-desc" onclick="nsSetOrder('desc')">降順 ↓</button>
<div class="ns-separator"></div>
<button class="ns-btn" id="ns-mode-btn" onclick="nsToggleMode()">テキストモードに切り替え</button>
<div class="ns-separator"></div>
<label class="ns-toggle">
<input type="checkbox" id="ns-dedup" onchange="nsProcess()"> 重複を削除
</label>
</div>

<div class="ns-row">
<div class="ns-col">
<div class="ns-label">入力 — 1行に1つ、またはカンマ区切り</div>
<textarea id="ns-input" placeholder="数値を入力してください&#10;例：&#10;42&#10;7&#10;3.14&#10;-5&#10;100&#10;&#10;カンマ区切りも可: 5, 2, 8, 1, 9" oninput="nsProcess()"></textarea>
<div class="ns-error" id="ns-error"></div>
</div>
<div class="ns-col">
<div class="ns-output-header">
<div class="ns-label">ソート結果</div>
<div style="display:flex;gap:6px;align-items:center;">
<span class="ns-mode-badge" id="ns-mode-badge">数値モード</span>
<button class="ns-btn" id="ns-copy-btn" onclick="nsCopy()">コピー</button>
</div>
</div>
<textarea id="ns-output" readonly placeholder="ソート結果がここに表示されます..."></textarea>
</div>
</div>

<div class="ns-stats" id="ns-stats" style="display:none;">
<div class="ns-stat-card">
<div class="ns-stat-label">件数</div>
<div class="ns-stat-val" id="ns-s-count">—</div>
</div>
<div class="ns-stat-card">
<div class="ns-stat-label">最小値</div>
<div class="ns-stat-val" id="ns-s-min">—</div>
</div>
<div class="ns-stat-card">
<div class="ns-stat-label">最大値</div>
<div class="ns-stat-val" id="ns-s-max">—</div>
</div>
<div class="ns-stat-card">
<div class="ns-stat-label">合計</div>
<div class="ns-stat-val" id="ns-s-sum">—</div>
</div>
<div class="ns-stat-card">
<div class="ns-stat-label">平均</div>
<div class="ns-stat-val" id="ns-s-avg">—</div>
</div>
<div class="ns-stat-card">
<div class="ns-stat-label">中央値</div>
<div class="ns-stat-val" id="ns-s-med">—</div>
</div>
</div>

<script>
(function() {
var nsMode = 'number';
var nsOrder = 'asc';

function nsGetItems() {
var raw = document.getElementById('ns-input').value;
if (!raw.trim()) return [];
var parts;
if (raw.indexOf(',') !== -1) {
parts = raw.split(',');
} else {
parts = raw.split('\n');
}
return parts.map(function(p) { return p.trim(); }).filter(function(p) { return p !== ''; });
}

function nsFmt(n) {
var s = String(n);
if (s.indexOf('.') !== -1) {
s = parseFloat(n.toFixed(10)).toString();
}
return s;
}

window.nsSetOrder = function(order) {
nsOrder = order;
document.getElementById('ns-asc').classList.toggle('active', order === 'asc');
document.getElementById('ns-desc').classList.toggle('active', order === 'desc');
nsProcess();
};

window.nsToggleMode = function() {
nsMode = nsMode === 'number' ? 'text' : 'number';
document.getElementById('ns-mode-btn').textContent = nsMode === 'number' ? 'テキストモードに切り替え' : '数値モードに切り替え';
document.getElementById('ns-mode-badge').textContent = nsMode === 'number' ? '数値モード' : 'テキストモード';
document.getElementById('ns-error').textContent = '';
nsProcess();
};

window.nsProcess = function() {
var items = nsGetItems();
var dedup = document.getElementById('ns-dedup').checked;
var errorEl = document.getElementById('ns-error');
var statsEl = document.getElementById('ns-stats');
var outputEl = document.getElementById('ns-output');

errorEl.textContent = '';

if (!items.length) {
outputEl.value = '';
statsEl.style.display = 'none';
return;
}

if (nsMode === 'number') {
var nums = [];
var bad = [];
items.forEach(function(item) {
var n = Number(item);
if (item === '' || isNaN(n)) {
bad.push(item);
} else {
nums.push(n);
}
});

if (bad.length) {
errorEl.textContent = '数値以外は無視されました: ' + bad.slice(0, 5).join(', ') + (bad.length > 5 ? '...' : '');
}

if (dedup) {
nums = nums.filter(function(v, i, a) { return a.indexOf(v) === i; });
}

nums.sort(function(a, b) { return nsOrder === 'asc' ? a - b : b - a; });

outputEl.value = nums.map(nsFmt).join('\n');

if (nums.length) {
var sum = nums.reduce(function(a, b) { return a + b; }, 0);
var avg = sum / nums.length;
var sorted = nums.slice().sort(function(a, b) { return a - b; });
var mid = Math.floor(sorted.length / 2);
var median = sorted.length % 2 === 0
? (sorted[mid - 1] + sorted[mid]) / 2
: sorted[mid];

document.getElementById('ns-s-count').textContent = nums.length;
document.getElementById('ns-s-min').textContent = nsFmt(nums[nsOrder === 'asc' ? 0 : nums.length - 1]);
document.getElementById('ns-s-max').textContent = nsFmt(nums[nsOrder === 'asc' ? nums.length - 1 : 0]);
document.getElementById('ns-s-sum').textContent = nsFmt(sum);
document.getElementById('ns-s-avg').textContent = nsFmt(Math.round(avg * 1e10) / 1e10);
document.getElementById('ns-s-med').textContent = nsFmt(median);
statsEl.style.display = 'grid';
} else {
statsEl.style.display = 'none';
}

} else {
var texts = items.slice();
if (dedup) {
texts = texts.filter(function(v, i, a) { return a.indexOf(v) === i; });
}
texts.sort(function(a, b) {
var cmp = a.localeCompare(b, 'ja');
return nsOrder === 'asc' ? cmp : -cmp;
});
outputEl.value = texts.join('\n');

document.getElementById('ns-s-count').textContent = texts.length;
document.getElementById('ns-s-min').textContent = texts[0] || '—';
document.getElementById('ns-s-max').textContent = texts[texts.length - 1] || '—';
document.getElementById('ns-s-sum').textContent = '—';
document.getElementById('ns-s-avg').textContent = '—';
document.getElementById('ns-s-med').textContent = '—';
statsEl.style.display = 'grid';
}
};

window.nsCopy = function() {
var text = document.getElementById('ns-output').value;
if (!text) return;
var btn = document.getElementById('ns-copy-btn');
var done = function() {
btn.textContent = 'コピー済み!';
btn.classList.add('success');
setTimeout(function() {
btn.textContent = 'コピー';
btn.classList.remove('success');
}, 1800);
};
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(done).catch(function() { fallbackCopy(text, done); });
} else {
fallbackCopy(text, done);
}
};

function fallbackCopy(text, cb) {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
cb();
}
})();
</script>

</div>

---

## 関連ツール

> 乱数生成 → [乱数生成ツール](/ja/tools/random-number-generator/)

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
