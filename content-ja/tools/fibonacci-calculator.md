---
title: "フィボナッチ数列計算ツール"
date: 2025-07-21
description: "無料フィボナッチ数列計算ツール。BigIntでN=1000まで正確に計算。数列生成・フィボナッチ判定・黄金比収束・螺旋ビジュアライズ対応。"
categories: ["無料ツール"]
slug: "fibonacci-calculator"
ShowToc: false
aliases: ["/ja/tools/fibonacci-calculator/", "/ja/tools/fibonacci-calculator/"]
cover:
  image: "/images/covers/fibonacci-calculator-ja.png"
  alt: "フィボナッチ数列計算ツール"
---

<div id="fib-app">

<style>
#fib-app *, #fib-app *::before, #fib-app *::after { box-sizing: border-box; margin: 0; padding: 0; }
#fib-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', sans-serif;
max-width: 740px;
margin: 0 auto;
padding: 12px;
color: #1e293b;
}
#fib-app h2.fib-title {
font-size: 18px;
font-weight: 700;
color: #0f172a;
margin-bottom: 14px;
letter-spacing: -0.3px;
}
#fib-app .fib-tabs {
display: flex;
gap: 6px;
flex-wrap: wrap;
margin-bottom: 16px;
}
#fib-app .fib-tab-btn {
padding: 7px 16px;
border: 1.5px solid #e2e8f0;
border-radius: 20px;
background: #f8fafc;
color: #475569;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#fib-app .fib-tab-btn:hover { background: #f1f5f9; border-color: #cbd5e1; }
#fib-app .fib-tab-btn.fib-active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}
#fib-app .fib-panel { display: none; }
#fib-app .fib-panel.fib-visible { display: block; }
#fib-app .fib-card {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 18px;
margin-bottom: 14px;
box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#fib-app label.fib-label {
display: block;
font-size: 12px;
font-weight: 600;
color: #64748b;
margin-bottom: 5px;
text-transform: uppercase;
letter-spacing: 0.4px;
}
#fib-app input[type="number"], #fib-app input[type="text"] {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
font-size: 15px;
color: #1e293b;
background: #f8fafc;
outline: none;
transition: border-color 0.15s;
}
#fib-app input[type="number"]:focus, #fib-app input[type="text"]:focus {
border-color: #7c3aed;
background: #fff;
}
#fib-app .fib-btn {
display: inline-block;
padding: 9px 22px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
margin-top: 10px;
}
#fib-app .fib-btn:hover { background: #6d28d9; }
#fib-app .fib-btn-sm {
display: inline-block;
padding: 6px 14px;
background: #f1f5f9;
color: #475569;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#fib-app .fib-btn-sm:hover { background: #e2e8f0; }
#fib-app .fib-btn-sm.fib-copied { background: #dcfce7; border-color: #86efac; color: #16a34a; }
#fib-app .fib-result-box {
margin-top: 12px;
padding: 14px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
word-break: break-all;
}
#fib-app .fib-result-label {
font-size: 11px;
font-weight: 700;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.5px;
margin-bottom: 5px;
}
#fib-app .fib-result-val {
font-size: 15px;
font-weight: 700;
color: #7c3aed;
word-break: break-all;
line-height: 1.5;
}
#fib-app .fib-result-sub {
font-size: 12px;
color: #64748b;
margin-top: 4px;
}
#fib-app .fib-seq-wrap {
margin-top: 10px;
max-height: 180px;
overflow-y: auto;
padding: 10px 12px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
font-size: 13px;
color: #334155;
line-height: 1.8;
word-break: break-all;
}
#fib-app .fib-seq-actions {
display: flex;
gap: 8px;
margin-top: 8px;
flex-wrap: wrap;
align-items: center;
}
#fib-app .fib-ratio-table {
width: 100%;
border-collapse: collapse;
margin-top: 10px;
font-size: 13px;
}
#fib-app .fib-ratio-table th {
background: #f1f5f9;
padding: 7px 10px;
text-align: left;
font-size: 11px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.4px;
border-bottom: 1.5px solid #e2e8f0;
}
#fib-app .fib-ratio-table td {
padding: 7px 10px;
border-bottom: 1px solid #f1f5f9;
color: #334155;
vertical-align: top;
}
#fib-app .fib-ratio-table tr:last-child td { border-bottom: none; }
#fib-app .fib-ratio-val { font-weight: 700; color: #7c3aed; font-size: 12px; }
#fib-app .fib-phi-highlight { color: #d97706; font-weight: 700; }
#fib-app .fib-check-badge {
display: inline-block;
padding: 4px 12px;
border-radius: 20px;
font-size: 13px;
font-weight: 700;
margin-top: 8px;
}
#fib-app .fib-check-yes { background: #dcfce7; color: #16a34a; }
#fib-app .fib-check-no  { background: #fee2e2; color: #dc2626; }
#fib-app canvas#fib-canvas {
display: block;
margin: 12px auto 0;
border-radius: 10px;
border: 1.5px solid #e2e8f0;
max-width: 100%;
}
#fib-app .fib-spiral-ctrl {
display: flex;
gap: 8px;
align-items: center;
margin-top: 10px;
flex-wrap: wrap;
}
#fib-app .fib-spiral-ctrl label { font-size: 12px; color: #64748b; font-weight: 600; }
#fib-app .fib-spiral-ctrl input[type="range"] { flex: 1; min-width: 80px; accent-color: #7c3aed; }
#fib-app .fib-err {
color: #dc2626;
font-size: 13px;
margin-top: 8px;
font-weight: 600;
}
#fib-app .fib-info-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-top: 10px;
}
#fib-app .fib-info-chip {
background: #ede9fe;
color: #5b21b6;
border-radius: 8px;
padding: 5px 12px;
font-size: 12px;
font-weight: 600;
}
@media (max-width: 500px) {
#fib-app .fib-ratio-table { font-size: 11px; }
#fib-app .fib-ratio-table td, #fib-app .fib-ratio-table th { padding: 5px 6px; }
}
</style>

<h2 class="fib-title">フィボナッチ数列計算ツール</h2>

<div class="fib-tabs">
<button class="fib-tab-btn fib-active" onclick="fibSwitchTab('nth',this)">第N項の計算</button>
<button class="fib-tab-btn" onclick="fibSwitchTab('seq',this)">数列生成</button>
<button class="fib-tab-btn" onclick="fibSwitchTab('check',this)">判定</button>
<button class="fib-tab-btn" onclick="fibSwitchTab('ratio',this)">黄金比</button>
<button class="fib-tab-btn" onclick="fibSwitchTab('spiral',this)">螺旋</button>
</div>

<!-- パネル：第N項 -->
<div id="fib-panel-nth" class="fib-panel fib-visible">
<div class="fib-card">
<label class="fib-label">N（1 〜 1000）</label>
<input type="number" id="fib-nth-input" min="1" max="1000" value="10" oninput="fibCalcNth()">
<div id="fib-nth-err" class="fib-err"></div>
<div id="fib-nth-result" class="fib-result-box" style="display:none;">
<div class="fib-result-label">F(N)</div>
<div class="fib-result-val" id="fib-nth-val"></div>
<div class="fib-result-sub" id="fib-nth-sub"></div>
<div class="fib-info-row" id="fib-nth-chips"></div>
</div>
</div>
</div>

<!-- パネル：数列生成 -->
<div id="fib-panel-seq" class="fib-panel">
<div class="fib-card">
<label class="fib-label">項数（1 〜 100）</label>
<input type="number" id="fib-seq-input" min="1" max="100" value="15" oninput="fibGenSeq()">
<div id="fib-seq-err" class="fib-err"></div>
<div id="fib-seq-wrap" class="fib-seq-wrap" style="display:none;"></div>
<div class="fib-seq-actions" id="fib-seq-actions" style="display:none;">
<button class="fib-btn-sm" id="fib-copy-btn" onclick="fibCopySeq()">コピー</button>
<span id="fib-seq-count" style="font-size:12px;color:#94a3b8;"></span>
</div>
</div>
</div>

<!-- パネル：フィボナッチ判定 -->
<div id="fib-panel-check" class="fib-panel">
<div class="fib-card">
<label class="fib-label">数値を入力</label>
<input type="text" id="fib-check-input" placeholder="例：89" oninput="fibCheckNum()">
<div id="fib-check-err" class="fib-err"></div>
<div id="fib-check-result" style="margin-top:10px;display:none;">
<div id="fib-check-badge"></div>
<div class="fib-result-sub" id="fib-check-sub" style="margin-top:6px;"></div>
</div>
</div>
</div>

<!-- パネル：黄金比 -->
<div id="fib-panel-ratio" class="fib-panel">
<div class="fib-card">
<p style="font-size:13px;color:#64748b;margin-bottom:10px;">Nが大きくなるにつれ、F(N)/F(N-1) は黄金比 &phi;（ファイ）&asymp; 1.6180339887&hellip; に収束します。</p>
<div style="overflow-x:auto;">
<table class="fib-ratio-table" id="fib-ratio-table">
<thead><tr><th>N</th><th>F(N)</th><th>F(N)/F(N-1)</th><th>&phi; との差</th></tr></thead>
<tbody id="fib-ratio-body"></tbody>
</table>
</div>
<div style="margin-top:10px;font-size:12px;color:#64748b;">&phi; = <span class="fib-phi-highlight">1.6180339887498948482&hellip;</span></div>
</div>
</div>

<!-- パネル：螺旋 -->
<div id="fib-panel-spiral" class="fib-panel">
<div class="fib-card">
<p style="font-size:13px;color:#64748b;margin-bottom:6px;">フィボナッチ正方形で構成された黄金螺旋。</p>
<div class="fib-spiral-ctrl">
<label>ステップ数: <span id="fib-steps-val">10</span></label>
<input type="range" id="fib-steps-range" min="3" max="14" value="10" oninput="fibDrawSpiral(this.value)">
</div>
<canvas id="fib-canvas" width="480" height="320"></canvas>
</div>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function(){
'use strict';

// --- BigInt フィボナッチ（メモ化） ---
var fibCache = [BigInt(0), BigInt(1)];
function fibN(n) {
if (n < 0 || n > 1000) return null;
if (fibCache[n] !== undefined) return fibCache[n];
for (var i = fibCache.length; i <= n; i++) {
fibCache[i] = fibCache[i-1] + fibCache[i-2];
}
return fibCache[n];
}
for (var _i = 0; _i <= 1000; _i++) fibN(_i);

var PHI = (1 + Math.sqrt(5)) / 2;

// --- タブ切替 ---
window.fibSwitchTab = function(name, el) {
document.querySelectorAll('#fib-app .fib-panel').forEach(function(p){ p.classList.remove('fib-visible'); });
document.querySelectorAll('#fib-app .fib-tab-btn').forEach(function(b){ b.classList.remove('fib-active'); });
document.getElementById('fib-panel-' + name).classList.add('fib-visible');
el.classList.add('fib-active');
if (name === 'ratio') fibBuildRatioTable();
if (name === 'spiral') fibDrawSpiral(document.getElementById('fib-steps-range').value);
if (name === 'seq') fibGenSeq();
if (name === 'nth') fibCalcNth();
};

// --- 第N項の計算 ---
window.fibCalcNth = function() {
var input = document.getElementById('fib-nth-input');
var errEl = document.getElementById('fib-nth-err');
var resBox = document.getElementById('fib-nth-result');
var valEl  = document.getElementById('fib-nth-val');
var subEl  = document.getElementById('fib-nth-sub');
var chips  = document.getElementById('fib-nth-chips');

errEl.textContent = '';
var n = parseInt(input.value, 10);
if (isNaN(n) || n < 1 || n > 1000) {
errEl.textContent = '1〜1000の整数を入力してください。';
resBox.style.display = 'none';
return;
}
var val = fibN(n);
var valStr = val.toString();
resBox.style.display = 'block';
valEl.textContent = valStr;
subEl.textContent = 'F(' + n + ') は ' + valStr.length + ' 桁の数値です。';
chips.innerHTML = '';
if (n >= 2) {
var ratio = Number(fibN(n)) / Number(fibN(n-1));
chips.innerHTML = '<span class="fib-info-chip">F(' + n + ')/F(' + (n-1) + ') &asymp; ' + ratio.toFixed(10) + '</span>';
}
};

// --- 数列生成 ---
var fibSeqData = [];
window.fibGenSeq = function() {
var input = document.getElementById('fib-seq-input');
var errEl = document.getElementById('fib-seq-err');
var wrap  = document.getElementById('fib-seq-wrap');
var acts  = document.getElementById('fib-seq-actions');
var cnt   = document.getElementById('fib-seq-count');

errEl.textContent = '';
var n = parseInt(input.value, 10);
if (isNaN(n) || n < 1 || n > 100) {
errEl.textContent = '1〜100の整数を入力してください。';
wrap.style.display = 'none';
acts.style.display = 'none';
return;
}
fibSeqData = [];
for (var i = 1; i <= n; i++) fibSeqData.push(fibN(i).toString());
wrap.style.display = 'block';
acts.style.display = 'flex';
wrap.textContent = fibSeqData.join(', ');
cnt.textContent = n + ' 項';
document.getElementById('fib-copy-btn').classList.remove('fib-copied');
document.getElementById('fib-copy-btn').textContent = 'コピー';
};

window.fibCopySeq = function() {
var btn = document.getElementById('fib-copy-btn');
if (!fibSeqData.length) return;
var text = fibSeqData.join(', ');
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function(){
btn.textContent = 'コピーしました！';
btn.classList.add('fib-copied');
setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('fib-copied'); }, 1500);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta); ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
btn.textContent = 'コピーしました！';
btn.classList.add('fib-copied');
setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('fib-copied'); }, 1500);
}
};

// --- フィボナッチ判定 ---
function isPerfectSquare(n) {
if (n < BigInt(0)) return false;
var s = BigInt(Math.round(Math.sqrt(Number(n))));
while (s * s > n) s--;
while ((s+BigInt(1))*(s+BigInt(1)) <= n) s++;
return s * s === n;
}
function isFibonacci(x) {
if (x < BigInt(0)) return false;
var x5 = BigInt(5) * x * x;
return isPerfectSquare(x5 + BigInt(4)) || isPerfectSquare(x5 - BigInt(4));
}
function findFibIndex(x) {
for (var i = 0; i <= 1000; i++) {
if (fibCache[i] === x) return i;
if (fibCache[i] > x) return -1;
}
return -1;
}

window.fibCheckNum = function() {
var input  = document.getElementById('fib-check-input');
var errEl  = document.getElementById('fib-check-err');
var resDiv = document.getElementById('fib-check-result');
var badge  = document.getElementById('fib-check-badge');
var sub    = document.getElementById('fib-check-sub');

errEl.textContent = '';
resDiv.style.display = 'none';
var raw = input.value.trim().replace(/,/g, '');
if (!raw) return;
if (!/^\d+$/.test(raw)) {
errEl.textContent = '0以上の整数を入力してください。';
return;
}
var x;
try { x = BigInt(raw); } catch(e) { errEl.textContent = '無効な数値です。'; return; }

resDiv.style.display = 'block';
if (isFibonacci(x)) {
badge.innerHTML = '<span class="fib-check-badge fib-check-yes">フィボナッチ数です</span>';
var idx = findFibIndex(x);
if (idx >= 0) {
sub.textContent = raw + ' = F(' + idx + ')';
} else {
sub.textContent = raw + ' はフィボナッチ数です（インデックス > 1000）。';
}
} else {
badge.innerHTML = '<span class="fib-check-badge fib-check-no">フィボナッチ数ではありません</span>';
var lo = BigInt(0), hi = BigInt(0);
for (var i = 0; i <= 1000; i++) {
if (fibCache[i] <= x) lo = fibCache[i];
if (fibCache[i] > x) { hi = fibCache[i]; break; }
}
sub.textContent = '直近のフィボナッチ数: ' + lo.toString() + '（以下）と ' + hi.toString() + '（以上）';
}
};

// --- 黄金比テーブル ---
function fibBuildRatioTable() {
var rows = [2,3,4,5,6,7,8,9,10,12,15,20,25,30,40,50];
var tbody = document.getElementById('fib-ratio-body');
tbody.innerHTML = '';
rows.forEach(function(n){
var fn  = Number(fibN(n));
var fn1 = Number(fibN(n-1));
if (fn1 === 0) return;
var ratio = fn / fn1;
var diff  = Math.abs(ratio - PHI);
var tr = document.createElement('tr');
tr.innerHTML =
'<td>' + n + '</td>' +
'<td>' + fibN(n).toString() + '</td>' +
'<td class="fib-ratio-val">' + ratio.toFixed(15) + '</td>' +
'<td style="color:#94a3b8;font-size:11px;">' + diff.toExponential(4) + '</td>';
tbody.appendChild(tr);
});
}

// --- 螺旋 ---
window.fibDrawSpiral = function(steps) {
steps = parseInt(steps, 10);
document.getElementById('fib-steps-val').textContent = steps;
var canvas = document.getElementById('fib-canvas');
var ctx = canvas.getContext('2d');
var W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);

var seq = [];
for (var i = 1; i <= steps; i++) seq.push(Number(fibN(i)));

var colors = ['#7c3aed','#a78bfa','#c4b5fd','#ddd6fe','#ede9fe',
'#6d28d9','#8b5cf6','#b197fc','#d8b4fe','#f3e8ff',
'#5b21b6','#7c3aed','#9333ea','#c026d3'];

var rects = [];
var spx = 0, spy = 0;
for (var i2 = 0; i2 < steps; i2++) {
var sz = seq[i2];
var rect = {x: spx, y: spy, s: sz};
rects.push(rect);
var nd = i2 % 4;
if (nd === 0) { spx += sz; }
else if (nd === 1) { spy += sz; spx -= seq[i2 > 0 ? i2-1 : 0]; }
else if (nd === 2) { spx -= sz; spy -= sz + (i2 > 0 ? seq[i2-1] : 0); }
else { spy -= seq[i2]; spx += sz; }
}

var minX = Infinity, minY = Infinity, maxX = -Infinity, maxY = -Infinity;
rects.forEach(function(r){
minX = Math.min(minX, r.x); minY = Math.min(minY, r.y);
maxX = Math.max(maxX, r.x + r.s); maxY = Math.max(maxY, r.y + r.s);
});
var bbW = maxX - minX, bbH = maxY - minY;
var sc = Math.min((W - 24) / bbW, (H - 24) / bbH);
var offX = (W - bbW * sc) / 2 - minX * sc;
var offY = (H - bbH * sc) / 2 - minY * sc;

rects.forEach(function(r, i){
var px2 = r.x * sc + offX, py2 = r.y * sc + offY, ps = r.s * sc;
ctx.fillStyle = colors[i % colors.length] + '22';
ctx.fillRect(px2, py2, ps, ps);
ctx.strokeStyle = colors[i % colors.length];
ctx.lineWidth = 1.5;
ctx.strokeRect(px2, py2, ps, ps);
if (ps > 20) {
ctx.fillStyle = colors[i % colors.length];
ctx.font = 'bold ' + Math.min(12, ps * 0.3) + 'px sans-serif';
ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
ctx.fillText(seq[i].toString(), px2 + ps/2, py2 + ps/2);
}
});

ctx.beginPath();
ctx.strokeStyle = '#d97706';
ctx.lineWidth = 2;
rects.forEach(function(r, i){
var px2 = r.x * sc + offX, py2 = r.y * sc + offY, ps = r.s * sc;
var nd2 = i % 4;
var startA, endA, arcX, arcY;
if (nd2 === 0)      { arcX = px2;      arcY = py2 + ps; startA = -Math.PI/2; endA = 0; }
else if (nd2 === 1) { arcX = px2;      arcY = py2;      startA = 0;          endA = Math.PI/2; }
else if (nd2 === 2) { arcX = px2 + ps; arcY = py2;      startA = Math.PI/2;  endA = Math.PI; }
else                { arcX = px2 + ps; arcY = py2 + ps; startA = Math.PI;    endA = 3*Math.PI/2; }
ctx.moveTo(arcX + ps * Math.cos(startA), arcY + ps * Math.sin(startA));
ctx.arc(arcX, arcY, ps, startA, endA, false);
});
ctx.stroke();
};

// --- 初期化 ---
fibCalcNth();
fibGenSeq();
fibDrawSpiral(10);

})();
</script>

---

### 関連ツール
> 進数変換 &rarr; [進数変換ツール](/ja/tools/number-base-converter/)
> パーセント計算 &rarr; [パーセント計算ツール](/ja/tools/percentage-calculator/)

---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
