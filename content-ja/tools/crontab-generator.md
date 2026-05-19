---
title: "Crontab生成ツール"
date: 2026-01-12
description: "無料のCrontab生成ツール。ドロップダウンでcron式をビジュアル作成。プリセット・人間語での説明・次回5回の実行時刻・コピー・既存cron式の検証まで対応。"
categories: ["無料ツール"]
slug: "crontab-generator"
ShowToc: false
aliases:
  - "/ja/tools/cron-generator/"
cover:
  image: "/images/covers/crontab-generator-ja.png"
  alt: "Crontab生成ツール"
---

<div id="cg-app">

<style>
#cg-app {
font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Noto Sans JP', 'Meiryo', system-ui, sans-serif;
background: #0f0f13;
color: #e2e8f0;
border-radius: 12px;
padding: 24px;
margin: 0 auto;
max-width: 900px;
box-sizing: border-box;
}
#cg-app * { box-sizing: border-box; }

#cg-app h2 {
font-size: 1.05rem;
font-weight: 700;
color: #f1f5f9;
margin: 0 0 14px 0;
}
#cg-app h3 {
font-size: 0.82rem;
font-weight: 700;
color: #94a3b8;
margin: 0 0 12px 0;
text-transform: uppercase;
letter-spacing: 0.04em;
}

.cg-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 22px;
}
.cg-preset-btn {
padding: 6px 14px;
border-radius: 20px;
border: 1px solid #2d2d4d;
background: #1a1a24;
color: #a5b4fc;
font-size: 0.82rem;
font-weight: 700;
cursor: pointer;
font-family: inherit;
transition: background 0.15s, border-color 0.15s;
}
.cg-preset-btn:hover { background: #22224a; border-color: #6366f1; color: #c7d2fe; }
.cg-preset-btn.active { background: #3730a3; border-color: #6366f1; color: #fff; }

.cg-builder {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 10px;
padding: 18px;
margin-bottom: 18px;
}
.cg-fields {
display: grid;
grid-template-columns: repeat(5, 1fr);
gap: 12px;
}
.cg-field-label {
font-size: 0.72rem;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 6px;
display: block;
}
.cg-field-select {
width: 100%;
background: #0f0f18;
border: 1px solid #2d2d3d;
border-radius: 6px;
color: #e2e8f0;
font-size: 0.84rem;
padding: 7px 10px;
outline: none;
font-family: inherit;
cursor: pointer;
transition: border-color 0.2s;
appearance: none;
-webkit-appearance: none;
background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2364748b' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
background-repeat: no-repeat;
background-position: right 8px center;
padding-right: 26px;
}
.cg-field-select:focus { border-color: #6366f1; }

.cg-expr-wrap {
background: #12192e;
border: 1px solid #1e2a4a;
border-radius: 8px;
padding: 14px 16px;
margin-bottom: 16px;
display: flex;
align-items: center;
gap: 12px;
flex-wrap: wrap;
}
.cg-expr-code {
font-family: 'Courier New', 'Consolas', monospace;
font-size: 1.4rem;
font-weight: 700;
color: #7dd3fc;
letter-spacing: 0.06em;
flex: 1;
min-width: 200px;
}
.cg-btn {
padding: 7px 16px;
border-radius: 6px;
border: none;
font-size: 0.84rem;
font-weight: 700;
cursor: pointer;
font-family: inherit;
transition: background 0.15s, transform 0.1s;
white-space: nowrap;
}
.cg-btn:active { transform: scale(0.97); }
.cg-btn-copy { background: #1a1a24; color: #a5b4fc; border: 1px solid #2d2d4d; }
.cg-btn-copy:hover { background: #22224a; }
.cg-btn-primary { background: #6366f1; color: #fff; }
.cg-btn-primary:hover { background: #4f46e5; }
.cg-btn-danger { background: #1a1a24; color: #f87171; border: 1px solid #3d2020; }
.cg-btn-danger:hover { background: #2d1a1a; }

.cg-desc-wrap {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 14px 16px;
margin-bottom: 18px;
}
.cg-desc-text {
font-size: 0.95rem;
color: #c7d2fe;
font-weight: 500;
line-height: 1.6;
}

.cg-runs-wrap {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 14px 16px;
margin-bottom: 18px;
}
.cg-run-list {
list-style: none;
margin: 0;
padding: 0;
}
.cg-run-item {
display: flex;
align-items: center;
gap: 10px;
padding: 6px 0;
border-bottom: 1px solid #1e1e2c;
font-size: 0.88rem;
}
.cg-run-item:last-child { border-bottom: none; }
.cg-run-num {
font-size: 0.72rem;
color: #475569;
width: 20px;
text-align: right;
flex-shrink: 0;
}
.cg-run-time {
font-family: 'Courier New', monospace;
color: #7dd3fc;
font-weight: 600;
}
.cg-run-rel {
color: #64748b;
font-size: 0.78rem;
}

.cg-validate-wrap {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 14px 16px;
margin-bottom: 20px;
}
.cg-validate-row {
display: flex;
gap: 8px;
align-items: center;
flex-wrap: wrap;
}
.cg-validate-input {
flex: 1;
min-width: 200px;
background: #0f0f18;
border: 1px solid #2d2d3d;
border-radius: 6px;
color: #e2e8f0;
font-size: 0.9rem;
font-family: 'Courier New', monospace;
padding: 8px 12px;
outline: none;
transition: border-color 0.2s;
}
.cg-validate-input:focus { border-color: #6366f1; }
.cg-validate-input::placeholder { color: #3a3a5a; font-family: inherit; }
.cg-validate-result {
margin-top: 10px;
font-size: 0.88rem;
min-height: 1.2em;
line-height: 1.5;
}
.cg-valid { color: #4ade80; }
.cg-invalid { color: #f87171; }

@media (max-width: 640px) {
#cg-app { padding: 16px 12px; }
.cg-fields { grid-template-columns: repeat(3, 1fr); }
.cg-expr-code { font-size: 1.1rem; }
}
@media (max-width: 400px) {
.cg-fields { grid-template-columns: repeat(2, 1fr); }
}
</style>

<h2>Cron式をビジュアル作成</h2>

<!-- プリセット -->
<div class="cg-presets" id="cg-presets">
<button class="cg-preset-btn" data-expr="* * * * *" onclick="cgApplyPreset(this)">毎分</button>
<button class="cg-preset-btn" data-expr="0 * * * *" onclick="cgApplyPreset(this)">毎時00分</button>
<button class="cg-preset-btn" data-expr="0 0 * * *" onclick="cgApplyPreset(this)">毎日深夜0時</button>
<button class="cg-preset-btn" data-expr="0 9 * * *" onclick="cgApplyPreset(this)">毎日9時</button>
<button class="cg-preset-btn" data-expr="0 0 * * 0" onclick="cgApplyPreset(this)">毎週日曜深夜</button>
<button class="cg-preset-btn" data-expr="0 0 1 * *" onclick="cgApplyPreset(this)">毎月1日深夜</button>
<button class="cg-preset-btn" data-expr="0 9 * * 1-5" onclick="cgApplyPreset(this)">平日9時</button>
<button class="cg-preset-btn" data-expr="*/5 * * * *" onclick="cgApplyPreset(this)">5分ごと</button>
<button class="cg-preset-btn" data-expr="*/15 * * * *" onclick="cgApplyPreset(this)">15分ごと</button>
<button class="cg-preset-btn" data-expr="0 0 1 1 *" onclick="cgApplyPreset(this)">元日深夜（年次）</button>
</div>

<!-- フィールドビルダー -->
<div class="cg-builder">
<div class="cg-fields">
<div class="cg-field-wrap">
<label class="cg-field-label" for="cg-min">分（Minute）</label>
<select class="cg-field-select" id="cg-min" onchange="cgUpdate()"></select>
</div>
<div class="cg-field-wrap">
<label class="cg-field-label" for="cg-hr">時（Hour）</label>
<select class="cg-field-select" id="cg-hr" onchange="cgUpdate()"></select>
</div>
<div class="cg-field-wrap">
<label class="cg-field-label" for="cg-dom">日（Month）</label>
<select class="cg-field-select" id="cg-dom" onchange="cgUpdate()"></select>
</div>
<div class="cg-field-wrap">
<label class="cg-field-label" for="cg-mon">月（Month）</label>
<select class="cg-field-select" id="cg-mon" onchange="cgUpdate()"></select>
</div>
<div class="cg-field-wrap">
<label class="cg-field-label" for="cg-dow">曜日（Week）</label>
<select class="cg-field-select" id="cg-dow" onchange="cgUpdate()"></select>
</div>
</div>
</div>

<!-- Cron式出力 -->
<div class="cg-expr-wrap">
<span class="cg-expr-code" id="cg-expr">* * * * *</span>
<button class="cg-btn cg-btn-copy" id="cg-copy-btn" onclick="cgCopyExpr()">コピー</button>
</div>

<!-- 日本語説明 -->
<div class="cg-desc-wrap">
<h3>日本語での説明</h3>
<div class="cg-desc-text" id="cg-desc">毎分実行</div>
</div>

<!-- 次回5回の実行時刻 -->
<div class="cg-runs-wrap">
<h3>次回5回の実行予定時刻</h3>
<ul class="cg-run-list" id="cg-run-list"></ul>
</div>

<!-- バリデーター -->
<div class="cg-validate-wrap">
<h3>既存のCron式を検証</h3>
<div class="cg-validate-row">
<input class="cg-validate-input" id="cg-val-input" placeholder="例: 0 9 * * 1-5" />
<button class="cg-btn cg-btn-primary" onclick="cgValidate()">検証</button>
<button class="cg-btn cg-btn-danger" onclick="cgClearValidate()">クリア</button>
</div>
<div class="cg-validate-result" id="cg-val-result"></div>
</div>

<script>
(function(){

var FIELDS = {
min: {
el: null,
options: (function(){
var o = [{ v: '*', l: '毎分 (*)' }];
for (var i = 0; i <= 59; i++) o.push({ v: String(i), l: i + '分' });
o.push({ v: '*/2', l: '2分ごと (*/2)' });
o.push({ v: '*/5', l: '5分ごと (*/5)' });
o.push({ v: '*/10', l: '10分ごと (*/10)' });
o.push({ v: '*/15', l: '15分ごと (*/15)' });
o.push({ v: '*/30', l: '30分ごと (*/30)' });
return o;
})()
},
hr: {
el: null,
options: (function(){
var o = [{ v: '*', l: '毎時 (*)' }];
for (var i = 0; i <= 23; i++) o.push({ v: String(i), l: i + '時' });
o.push({ v: '*/2', l: '2時間ごと (*/2)' });
o.push({ v: '*/3', l: '3時間ごと (*/3)' });
o.push({ v: '*/6', l: '6時間ごと (*/6)' });
o.push({ v: '*/12', l: '12時間ごと (*/12)' });
return o;
})()
},
dom: {
el: null,
options: (function(){
var o = [{ v: '*', l: '毎日 (*)' }];
for (var i = 1; i <= 31; i++) o.push({ v: String(i), l: i + '日' });
o.push({ v: '*/2', l: '2日ごと' });
o.push({ v: '1,15', l: '1日と15日' });
o.push({ v: 'L', l: '月末日' });
return o;
})()
},
mon: {
el: null,
options: [
{ v: '*', l: '毎月 (*)' },
{ v: '1', l: '1月' }, { v: '2', l: '2月' }, { v: '3', l: '3月' },
{ v: '4', l: '4月' }, { v: '5', l: '5月' }, { v: '6', l: '6月' },
{ v: '7', l: '7月' }, { v: '8', l: '8月' }, { v: '9', l: '9月' },
{ v: '10', l: '10月' }, { v: '11', l: '11月' }, { v: '12', l: '12月' },
{ v: '1-3', l: '第1四半期（1〜3月）' }, { v: '4-6', l: '第2四半期（4〜6月）' },
{ v: '7-9', l: '第3四半期（7〜9月）' }, { v: '10-12', l: '第4四半期（10〜12月）' }
]
},
dow: {
el: null,
options: [
{ v: '*', l: '毎日（曜日問わず）(*)' },
{ v: '0', l: '日曜日 (0)' }, { v: '1', l: '月曜日 (1)' }, { v: '2', l: '火曜日 (2)' },
{ v: '3', l: '水曜日 (3)' }, { v: '4', l: '木曜日 (4)' }, { v: '5', l: '金曜日 (5)' },
{ v: '6', l: '土曜日 (6)' },
{ v: '1-5', l: '平日（月〜金）' }, { v: '0,6', l: '週末（土・日）' },
{ v: '1,3,5', l: '月・水・金' }, { v: '2,4', l: '火・木' }
]
}
};

var MONTHS_JA = ['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
var DAYS_JA = ['日曜','月曜','火曜','水曜','木曜','金曜','土曜'];
var DAYS_SHORT_JA = ['日','月','火','水','木','金','土'];

function buildSelects() {
['min','hr','dom','mon','dow'].forEach(function(key) {
var sel = document.getElementById('cg-' + key);
FIELDS[key].el = sel;
FIELDS[key].options.forEach(function(opt) {
var o = document.createElement('option');
o.value = opt.v; o.textContent = opt.l;
sel.appendChild(o);
});
});
}

function getExpr() {
return ['min','hr','dom','mon','dow'].map(function(k){ return FIELDS[k].el.value; }).join(' ');
}

function describe(expr) {
var parts = expr.trim().split(/\s+/);
if (parts.length !== 5) return '無効なcron式です';
var min = parts[0], hr = parts[1], dom = parts[2], mon = parts[3], dow = parts[4];

if (expr === '* * * * *') return '毎分実行';
if (expr === '0 * * * *') return '毎時0分に実行';
if (expr === '0 0 * * *') return '毎日深夜0時（0:00）に実行';
if (expr === '0 0 * * 0') return '毎週日曜日の深夜0時に実行';
if (expr === '0 0 1 * *') return '毎月1日の深夜0時に実行';
if (expr === '0 0 1 1 *') return '毎年1月1日の深夜0時に実行';
if (expr === '0 9 * * 1-5') return '平日（月〜金）の毎朝9時に実行';

var desc_parts = [];

if (min === '*') desc_parts.push('毎分');
else if (min.startsWith('*/')) desc_parts.push(min.slice(2) + '分ごと');
else desc_parts.push(min + '分に');

if (hr === '*') { /* omit */ }
else if (hr.startsWith('*/')) desc_parts.push(hr.slice(2) + '時間ごと');
else desc_parts.push(hr + '時');

if (dom !== '*' && dom !== '*/1') {
if (dom === 'L') desc_parts.push('月末日');
else if (dom.includes('-')) desc_parts.push(dom + '日の間');
else if (dom.includes(',')) desc_parts.push(dom.replace(/,/g,'日・') + '日');
else if (dom.startsWith('*/')) desc_parts.push(dom.slice(2) + '日ごと');
else desc_parts.push(dom + '日に');
}

if (mon !== '*') {
if (mon.includes('-')) {
var sp = mon.split('-');
desc_parts.push((MONTHS_JA[parseInt(sp[0])-1]||sp[0]+'月') + '〜' + (MONTHS_JA[parseInt(sp[1])-1]||sp[1]+'月'));
} else if (mon.includes(',')) {
var ms = mon.split(',').map(function(m){ return MONTHS_JA[parseInt(m)-1]||m+'月'; });
desc_parts.push(ms.join('・'));
} else {
desc_parts.push(MONTHS_JA[parseInt(mon)-1] || mon + '月');
}
}

if (dow !== '*') {
if (dow === '1-5') desc_parts.push('平日（月〜金）');
else if (dow === '0,6' || dow === '6,0') desc_parts.push('週末（土・日）');
else if (dow.includes('-')) {
var sp2 = dow.split('-');
desc_parts.push((DAYS_SHORT_JA[parseInt(sp2[0])]||sp2[0]) + '〜' + (DAYS_SHORT_JA[parseInt(sp2[1])]||sp2[1]) + '曜日');
} else if (dow.includes(',')) {
var ds = dow.split(',').map(function(d){ return (DAYS_SHORT_JA[parseInt(d)]||d) + '曜'; });
desc_parts.push(ds.join('・'));
} else {
desc_parts.push(DAYS_JA[parseInt(dow)] || '曜日' + dow);
}
}

return desc_parts.length ? desc_parts.join(' ') + 'に実行' : 'カスタムスケジュール';
}

function nextRuns(expr, count) {
var parts = expr.trim().split(/\s+/);
if (parts.length !== 5) return [];

function parseField(str, min, max) {
var values = [];
if (str === '*') {
for (var i = min; i <= max; i++) values.push(i);
return values;
}
var segments = str.split(',');
segments.forEach(function(seg) {
seg = seg.trim();
if (seg === '*') {
for (var i = min; i <= max; i++) values.push(i);
} else if (seg.startsWith('*/')) {
var step = parseInt(seg.slice(2));
for (var i = min; i <= max; i += step) values.push(i);
} else if (seg.includes('-')) {
var rng = seg.split('-');
var from = parseInt(rng[0]), to = parseInt(rng[1]);
for (var i = from; i <= to; i++) values.push(i);
} else {
var n = parseInt(seg);
if (!isNaN(n)) values.push(n);
}
});
return values.filter(function(v,i,a){ return a.indexOf(v)===i; }).sort(function(a,b){return a-b;});
}

try {
var mins = parseField(parts[0], 0, 59);
var hrs  = parseField(parts[1], 0, 23);
var doms = parts[2] === '*' ? null : parseField(parts[2], 1, 31);
var mons = parseField(parts[3], 1, 12);
var dows = parts[4] === '*' ? null : parseField(parts[4], 0, 6);

var runs = [];
var cur = new Date();
cur = new Date(cur.getFullYear(), cur.getMonth(), cur.getDate(), cur.getHours(), cur.getMinutes() + 1, 0);
var limit = 50000;

while (runs.length < count && limit-- > 0) {
var m = cur.getMonth() + 1;
var dom = cur.getDate();
var dow = cur.getDay();
var h = cur.getHours();
var mi = cur.getMinutes();

if (mons.indexOf(m) >= 0
&& (doms === null || doms.indexOf(dom) >= 0)
&& (dows === null || dows.indexOf(dow) >= 0)
&& hrs.indexOf(h) >= 0
&& mins.indexOf(mi) >= 0) {
runs.push(new Date(cur));
}
cur = new Date(cur.getTime() + 60000);
}
return runs;
} catch(e) {
return [];
}
}

function relTimeJa(d) {
var diff = Math.round((d - Date.now()) / 1000);
if (diff < 60) return diff + '秒後';
if (diff < 3600) return Math.round(diff/60) + '分後';
if (diff < 86400) return Math.round(diff/3600) + '時間後';
return Math.round(diff/86400) + '日後';
}

function padZ(n) { return n < 10 ? '0' + n : String(n); }

function fmtDate(d) {
var wd = ['日','月','火','水','木','金','土'];
return d.getFullYear() + '/' + padZ(d.getMonth()+1) + '/' + padZ(d.getDate())
+ '(' + wd[d.getDay()] + ') '
+ padZ(d.getHours()) + ':' + padZ(d.getMinutes());
}

function renderRuns(expr) {
var list = document.getElementById('cg-run-list');
var runs = nextRuns(expr, 5);
if (!runs.length) {
list.innerHTML = '<li class="cg-run-item"><span style="color:#64748b;">この式では次回実行時刻を計算できませんでした。</span></li>';
return;
}
list.innerHTML = runs.map(function(d, i) {
return '<li class="cg-run-item">'
+ '<span class="cg-run-num">' + (i+1) + '</span>'
+ '<span class="cg-run-time">' + fmtDate(d) + '</span>'
+ '<span class="cg-run-rel">' + relTimeJa(d) + '</span>'
+ '</li>';
}).join('');
}

function cgUpdate() {
var expr = getExpr();
document.getElementById('cg-expr').textContent = expr;
document.getElementById('cg-desc').textContent = describe(expr);
renderRuns(expr);
document.querySelectorAll('.cg-preset-btn').forEach(function(b){
b.classList.toggle('active', b.getAttribute('data-expr') === expr);
});
}

window.cgApplyPreset = function(btn) {
var expr = btn.getAttribute('data-expr');
var parts = expr.split(' ');
var keys = ['min','hr','dom','mon','dow'];
keys.forEach(function(k, i) {
var sel = FIELDS[k].el;
var found = false;
for (var j = 0; j < sel.options.length; j++) {
if (sel.options[j].value === parts[i]) { sel.selectedIndex = j; found = true; break; }
}
if (!found) sel.selectedIndex = 0;
});
cgUpdate();
};

window.cgCopyExpr = function() {
var expr = getExpr();
var btn = document.getElementById('cg-copy-btn');
try {
if (navigator.clipboard) {
navigator.clipboard.writeText(expr).then(function(){
btn.textContent = 'コピー完了!';
setTimeout(function(){ btn.textContent = 'コピー'; }, 1600);
});
} else {
var ta = document.createElement('textarea');
ta.value = expr;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
btn.textContent = 'コピー完了!';
setTimeout(function(){ btn.textContent = 'コピー'; }, 1600);
}
} catch(e) {}
};

function validateExpr(expr) {
var parts = expr.trim().split(/\s+/);
if (parts.length !== 5) return { ok: false, msg: 'cron式はスペース区切りの5フィールド（分 時 日 月 曜日）で入力してください。' };
var ranges = [[0,59],[0,23],[1,31],[1,12],[0,7]];
var names  = ['分','時','日','月','曜日'];
for (var i = 0; i < 5; i++) {
var f = parts[i];
if (f === '*') continue;
if (/^\*\/\d+$/.test(f)) {
var step = parseInt(f.slice(2));
if (step < 1) return { ok: false, msg: '"' + names[i] + '" フィールド: ステップ値は1以上にしてください。' };
continue;
}
var segs = f.split(',');
for (var j = 0; j < segs.length; j++) {
var seg = segs[j].trim();
if (/^\d+$/.test(seg)) {
var n = parseInt(seg);
if (n < ranges[i][0] || n > ranges[i][1]) {
return { ok: false, msg: '"' + names[i] + '" フィールド: 値 ' + n + ' は範囲外です（' + ranges[i][0] + '〜' + ranges[i][1] + '）。' };
}
} else if (/^\d+-\d+$/.test(seg)) {
var rp = seg.split('-').map(Number);
if (rp[0] > rp[1]) return { ok: false, msg: '"' + names[i] + '" フィールド: 範囲の開始値は終了値以下にしてください。' };
if (rp[0] < ranges[i][0] || rp[1] > ranges[i][1]) {
return { ok: false, msg: '"' + names[i] + '" フィールド: 範囲 ' + seg + ' は許容範囲外です（' + ranges[i][0] + '〜' + ranges[i][1] + '）。' };
}
} else if (/^\d+-\d+\/\d+$/.test(seg)) {
continue;
} else if (seg === 'L' && i === 2) {
continue;
} else {
return { ok: false, msg: '"' + names[i] + '" フィールド: 認識できない値 "' + seg + '"。' };
}
}
}
return { ok: true, msg: '有効なcron式です: ' + describe(parts.join(' ')) };
}

window.cgValidate = function() {
var val = document.getElementById('cg-val-input').value.trim();
var res = document.getElementById('cg-val-result');
if (!val) { res.textContent = '検証するcron式を入力してください。'; res.className = 'cg-validate-result'; return; }
var r = validateExpr(val);
res.textContent = r.msg;
res.className = 'cg-validate-result ' + (r.ok ? 'cg-valid' : 'cg-invalid');
if (r.ok) {
var parts = val.trim().split(/\s+/);
var keys = ['min','hr','dom','mon','dow'];
keys.forEach(function(k, i) {
var sel = FIELDS[k].el;
for (var j = 0; j < sel.options.length; j++) {
if (sel.options[j].value === parts[i]) { sel.selectedIndex = j; break; }
}
});
cgUpdate();
}
};

window.cgClearValidate = function() {
document.getElementById('cg-val-input').value = '';
document.getElementById('cg-val-result').textContent = '';
document.getElementById('cg-val-result').className = 'cg-validate-result';
};

buildSelects();
cgUpdate();

document.getElementById('cg-val-input').addEventListener('keydown', function(e){
if (e.key === 'Enter') cgValidate();
});

})();
</script>

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

> Cron式 → [Cron式ビルダー](/ja/tools/cron-expression-builder/)

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

</div>
