---
title: "結婚式費用シミュレーター - 結婚式の予算を簡単計算"
description: "カテゴリ別の内訳と費用見積もりで結婚式の予算を計画。無料ウェディング費用プランナー。"
date: 2025-10-19
slug: "wedding-budget-calculator"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: "/images/covers/wedding-budget-calculator.png"
---

<div id="wb-app">
<style>
#wb-app {
font-family: 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', 'Meiryo', sans-serif;
max-width: 880px;
margin: 0 auto;
color: #2d2d2d;
padding: 0 8px;
}
#wb-app h2 {
font-size: 1.3rem;
font-weight: 700;
color: #1a1a1a;
margin: 1.5rem 0 0.5rem;
border-bottom: 2px solid #f0c4d4;
padding-bottom: 0.3rem;
}
#wb-app .wb-intro {
background: linear-gradient(135deg, #fff5f8 0%, #fdf0f5 100%);
border: 1px solid #f0c4d4;
border-radius: 10px;
padding: 1.2rem 1.4rem;
margin-bottom: 1.5rem;
font-size: 0.95rem;
color: #555;
line-height: 1.7;
}
#wb-app .wb-top-row {
display: flex;
gap: 14px;
flex-wrap: wrap;
margin-bottom: 1.4rem;
}
#wb-app .wb-top-card {
flex: 1 1 180px;
background: #fff;
border: 1px solid #e8d0d8;
border-radius: 10px;
padding: 1rem 1.2rem;
}
#wb-app .wb-top-card label {
display: block;
font-size: 0.8rem;
font-weight: 700;
color: #999;
margin-bottom: 0.4rem;
}
#wb-app .wb-top-card input {
width: 100%;
border: 1.5px solid #e0c8d0;
border-radius: 6px;
padding: 0.45rem 0.7rem;
font-size: 1.05rem;
font-weight: 700;
color: #c0396b;
background: #fffafb;
box-sizing: border-box;
outline: none;
transition: border-color 0.2s;
}
#wb-app .wb-top-card input:focus {
border-color: #c0396b;
background: #fff;
}
#wb-app .wb-goshugi-card {
background: linear-gradient(135deg, #fffbf0 0%, #fff8e8 100%);
border: 1.5px solid #f5d08c;
border-radius: 10px;
padding: 1rem 1.2rem;
flex: 1 1 180px;
}
#wb-app .wb-goshugi-card label {
display: block;
font-size: 0.8rem;
font-weight: 700;
color: #b8860b;
margin-bottom: 0.4rem;
}
#wb-app .wb-goshugi-card input {
width: 100%;
border: 1.5px solid #f5d08c;
border-radius: 6px;
padding: 0.45rem 0.7rem;
font-size: 1.05rem;
font-weight: 700;
color: #b8860b;
background: #fffef8;
box-sizing: border-box;
outline: none;
transition: border-color 0.2s;
}
#wb-app .wb-goshugi-card input:focus {
border-color: #b8860b;
background: #fff;
}
#wb-app .wb-status-bar {
background: #fff;
border: 2px solid #e8d0d8;
border-radius: 10px;
padding: 1rem 1.4rem;
margin-bottom: 1rem;
display: flex;
align-items: center;
gap: 16px;
flex-wrap: wrap;
}
#wb-app .wb-status-label {
font-size: 0.78rem;
color: #999;
font-weight: 700;
margin-bottom: 2px;
}
#wb-app .wb-status-amount {
font-size: 1.35rem;
font-weight: 800;
color: #c0396b;
}
#wb-app .wb-status-diff {
font-size: 0.92rem;
font-weight: 700;
padding: 0.28rem 0.75rem;
border-radius: 20px;
}
#wb-app .wb-status-diff.under {
background: #e8f5e9;
color: #2e7d32;
}
#wb-app .wb-status-diff.over {
background: #fdecea;
color: #c62828;
}
#wb-app .wb-status-diff.exact {
background: #e8eaf6;
color: #3949ab;
}
#wb-app .wb-goshugi-banner {
background: linear-gradient(135deg, #fffbf0, #fff8e8);
border: 1.5px solid #f5d08c;
border-radius: 10px;
padding: 0.9rem 1.2rem;
margin-bottom: 1.2rem;
display: flex;
align-items: center;
gap: 18px;
flex-wrap: wrap;
}
#wb-app .wb-goshugi-banner .wb-status-label {
color: #b8860b;
}
#wb-app .wb-goshugi-banner .wb-status-amount {
color: #b8860b;
}
#wb-app .wb-jishutankin {
font-size: 0.88rem;
color: #888;
margin-top: 2px;
}
#wb-app .wb-jishutankin strong {
color: #c0396b;
font-size: 1.05rem;
}
#wb-app .wb-progress-wrap {
flex: 1 1 160px;
min-width: 100px;
}
#wb-app .wb-progress-track {
background: #f0e0e8;
border-radius: 6px;
height: 10px;
overflow: hidden;
}
#wb-app .wb-progress-fill {
height: 100%;
border-radius: 6px;
transition: width 0.4s, background 0.4s;
}
#wb-app .wb-main {
display: flex;
gap: 22px;
flex-wrap: wrap;
}
#wb-app .wb-categories {
flex: 1 1 340px;
}
#wb-app .wb-chart-col {
flex: 0 0 230px;
display: flex;
flex-direction: column;
align-items: center;
}
#wb-app .wb-category-row {
background: #fff;
border: 1px solid #ecdde4;
border-radius: 8px;
padding: 0.7rem 0.9rem;
margin-bottom: 0.6rem;
}
#wb-app .wb-cat-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 0.3rem;
}
#wb-app .wb-cat-name {
font-weight: 700;
font-size: 0.9rem;
color: #333;
}
#wb-app .wb-cat-amounts {
font-size: 0.8rem;
color: #aaa;
text-align: right;
}
#wb-app .wb-cat-pct {
font-size: 0.78rem;
font-weight: 800;
color: #c0396b;
min-width: 34px;
text-align: right;
}
#wb-app .wb-cat-input-row {
display: flex;
align-items: center;
gap: 10px;
}
#wb-app .wb-cat-slider {
-webkit-appearance: none;
appearance: none;
flex: 1;
height: 5px;
border-radius: 3px;
background: #f0c4d4;
outline: none;
cursor: pointer;
}
#wb-app .wb-cat-slider::-webkit-slider-thumb {
-webkit-appearance: none;
width: 15px;
height: 15px;
border-radius: 50%;
background: #c0396b;
cursor: pointer;
box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
#wb-app .wb-cat-slider::-moz-range-thumb {
width: 15px;
height: 15px;
border-radius: 50%;
background: #c0396b;
cursor: pointer;
border: none;
}
#wb-app .wb-warning {
font-size: 0.8rem;
color: #e65100;
background: #fff3e0;
border: 1px solid #ffcc80;
border-radius: 6px;
padding: 0.4rem 0.7rem;
margin-bottom: 0.8rem;
display: none;
}
#wb-app .wb-chart-title {
font-size: 0.82rem;
font-weight: 700;
color: #999;
margin-bottom: 0.6rem;
text-align: center;
}
#wb-app canvas#wb-pie {
border-radius: 50%;
box-shadow: 0 2px 12px rgba(192,57,107,0.10);
}
#wb-app .wb-legend {
margin-top: 0.9rem;
width: 100%;
}
#wb-app .wb-legend-item {
display: flex;
align-items: center;
gap: 7px;
font-size: 0.76rem;
color: #555;
margin-bottom: 0.28rem;
}
#wb-app .wb-legend-dot {
width: 10px;
height: 10px;
border-radius: 3px;
flex-shrink: 0;
}
#wb-app .wb-per-person {
background: #fff5f8;
border: 1px solid #f0c4d4;
border-radius: 8px;
padding: 0.75rem 0.9rem;
margin-top: 0.9rem;
font-size: 0.85rem;
color: #555;
text-align: center;
line-height: 1.6;
}
#wb-app .wb-per-person strong {
font-size: 1.05rem;
color: #c0396b;
}
#wb-app .wb-cta {
margin-top: 2rem;
background: linear-gradient(135deg, #fffbf0, #fff8e8);
border: 1.5px solid #f5d08c;
border-radius: 10px;
padding: 1rem 1.3rem;
font-size: 0.92rem;
color: #555;
line-height: 1.7;
}
#wb-app .wb-cta a {
color: #b8860b;
font-weight: 700;
text-decoration: none;
}
#wb-app .wb-cta a:hover {
text-decoration: underline;
}
@media (max-width: 620px) {
#wb-app .wb-chart-col {
flex: 1 1 100%;
align-items: center;
}
#wb-app .wb-status-bar {
gap: 10px;
}
#wb-app .wb-goshugi-banner {
gap: 10px;
}
}
</style>

<div class="wb-intro">
総予算・ゲスト人数・ご祝儀収入を入力するだけで、結婚式の費用内訳が一目でわかります。スライダーで各項目の割合を自由に調整しながら、自己負担額をリアルタイムで確認できます。
</div>

<div class="wb-top-row">
<div class="wb-top-card">
<label for="wb-total-budget">総予算（円）</label>
<input type="number" id="wb-total-budget" value="3000000" min="0" step="10000" placeholder="3000000">
</div>
<div class="wb-top-card">
<label for="wb-guest-count">招待ゲスト人数（名）</label>
<input type="number" id="wb-guest-count" value="80" min="1" step="1" placeholder="80">
</div>
<div class="wb-goshugi-card">
<label for="wb-goshugi">ご祝儀収入見込（円）</label>
<input type="number" id="wb-goshugi" value="2000000" min="0" step="10000" placeholder="2000000">
</div>
</div>

<div class="wb-status-bar">
<div>
<div class="wb-status-label">総予算</div>
<div class="wb-status-amount" id="wb-disp-budget">300万円</div>
</div>
<div>
<div class="wb-status-label">配分合計</div>
<div class="wb-status-amount" id="wb-disp-allocated">300万円</div>
</div>
<div id="wb-disp-diff" class="wb-status-diff exact">過不足なし</div>
<div class="wb-progress-wrap">
<div class="wb-status-label" style="margin-bottom:0.3rem;">配分率</div>
<div class="wb-progress-track">
<div class="wb-progress-fill" id="wb-progress-fill" style="width:100%;background:#c0396b;"></div>
</div>
<div style="font-size:0.76rem;color:#bbb;margin-top:3px;" id="wb-pct-total-label">合計 100%</div>
</div>
</div>

<div class="wb-goshugi-banner">
<div>
<div class="wb-status-label">ご祝儀収入見込</div>
<div class="wb-status-amount" id="wb-disp-goshugi">200万円</div>
</div>
<div>
<div class="wb-status-label">自己負担額（予測）</div>
<div class="wb-status-amount" id="wb-disp-jifutan">100万円</div>
</div>
<div>
<div class="wb-jishutankin">お一人あたりのご祝儀目安：<strong id="wb-per-goshugi">2.5万円</strong></div>
</div>
</div>

<div id="wb-pct-warning" class="wb-warning"></div>

<div class="wb-main">
<div class="wb-categories" id="wb-categories-list">
<!-- Rows injected by JS -->
</div>
<div class="wb-chart-col">
<div class="wb-chart-title">費用内訳グラフ</div>
<canvas id="wb-pie" width="220" height="220"></canvas>
<div class="wb-legend" id="wb-legend"></div>
<div class="wb-per-person" id="wb-per-person">
ゲスト1人あたりの費用<br>
<strong id="wb-per-person-val">3.75万円</strong>
</div>
</div>
</div>

<div class="wb-cta">

> 結婚資金の管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

</div>

<script>
(function() {
'use strict';

const CATEGORIES = [
{ name: '会場費',       pct: 40, color: '#c0396b' },
{ name: '料理・飲物',   pct: 25, color: '#e05c8a' },
{ name: '写真・映像',   pct: 10, color: '#f4a0b5' },
{ name: '花・装花',     pct:  5, color: '#f7c5d5' },
{ name: '音楽・演出',   pct:  5, color: '#a0c4ff' },
{ name: '衣裳・美容',   pct:  5, color: '#b5ead7' },
{ name: '招待状・印刷', pct:  3, color: '#ffd6a5' },
{ name: '引き出物',     pct:  2, color: '#caffbf' },
{ name: 'その他',       pct:  5, color: '#c9c9ff' },
];

let state = {
budget: 3000000,
guests: 80,
goshugi: 2000000,
pcts: CATEGORIES.map(c => c.pct),
};

function fmtJpy(n) {
if (n >= 10000) {
const man = n / 10000;
if (Number.isInteger(man)) return man + '万円';
return man.toFixed(1).replace(/\.0$/, '') + '万円';
}
return n.toLocaleString('ja-JP') + '円';
}
function fmtJpyFull(n) {
return n.toLocaleString('ja-JP') + '円';
}

// Build category rows
const list = document.getElementById('wb-categories-list');
CATEGORIES.forEach((cat, i) => {
const row = document.createElement('div');
row.className = 'wb-category-row';
row.innerHTML = `
<div class="wb-cat-header">
<span class="wb-cat-name">${cat.name}</span>
<div style="text-align:right">
<span class="wb-cat-amounts" id="wb-amt-${i}"></span>
<span class="wb-cat-pct" id="wb-pct-${i}">${cat.pct}%</span>
</div>
</div>
<div class="wb-cat-input-row">
<input type="range" class="wb-cat-slider" id="wb-slider-${i}"
min="0" max="60" step="1" value="${cat.pct}"
aria-label="${cat.name}の割合">
</div>
`;
list.appendChild(row);

document.getElementById(`wb-slider-${i}`).addEventListener('input', function() {
state.pcts[i] = parseInt(this.value, 10);
render();
});
});

document.getElementById('wb-total-budget').addEventListener('input', function() {
const v = parseFloat(this.value);
state.budget = isNaN(v) ? 0 : v;
render();
});
document.getElementById('wb-guest-count').addEventListener('input', function() {
const v = parseInt(this.value, 10);
state.guests = isNaN(v) || v < 1 ? 1 : v;
render();
});
document.getElementById('wb-goshugi').addEventListener('input', function() {
const v = parseFloat(this.value);
state.goshugi = isNaN(v) ? 0 : v;
render();
});

function drawPie(data, colors) {
const canvas = document.getElementById('wb-pie');
const ctx = canvas.getContext('2d');
const W = canvas.width, H = canvas.height;
const cx = W / 2, cy = H / 2, r = Math.min(cx, cy) - 6;
ctx.clearRect(0, 0, W, H);

const total = data.reduce((a, b) => a + b, 0);
if (total === 0) return;

let startAngle = -Math.PI / 2;
data.forEach((val, i) => {
if (val <= 0) return;
const slice = (val / total) * 2 * Math.PI;
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, startAngle, startAngle + slice);
ctx.closePath();
ctx.fillStyle = colors[i];
ctx.fill();
ctx.strokeStyle = '#fff';
ctx.lineWidth = 2;
ctx.stroke();
startAngle += slice;
});

// donut hole
ctx.beginPath();
ctx.arc(cx, cy, r * 0.44, 0, 2 * Math.PI);
ctx.fillStyle = '#fff';
ctx.fill();
}

function buildLegend(amounts) {
const leg = document.getElementById('wb-legend');
leg.innerHTML = '';
CATEGORIES.forEach((cat, i) => {
if (amounts[i] <= 0) return;
const item = document.createElement('div');
item.className = 'wb-legend-item';
item.innerHTML = `
<span class="wb-legend-dot" style="background:${cat.color}"></span>
<span>${cat.name}：${fmtJpy(amounts[i])}</span>
`;
leg.appendChild(item);
});
}

function render() {
const budget = state.budget;
const guests = state.guests;
const goshugi = state.goshugi;
const pctTotal = state.pcts.reduce((a, b) => a + b, 0);
const amounts = state.pcts.map(p => budget * p / 100);
const allocated = amounts.reduce((a, b) => a + b, 0);
const jifutan = allocated - goshugi;

// Update slider labels
CATEGORIES.forEach((cat, i) => {
document.getElementById(`wb-pct-${i}`).textContent = state.pcts[i] + '%';
document.getElementById(`wb-slider-${i}`).value = state.pcts[i];
document.getElementById(`wb-amt-${i}`).textContent = fmtJpy(amounts[i]);
});

// Status bar
document.getElementById('wb-disp-budget').textContent = fmtJpy(budget);
document.getElementById('wb-disp-allocated').textContent = fmtJpy(allocated);

const diff = budget - allocated;
const diffEl = document.getElementById('wb-disp-diff');
if (Math.abs(diff) < 100) {
diffEl.textContent = '過不足なし';
diffEl.className = 'wb-status-diff exact';
} else if (diff > 0) {
diffEl.textContent = fmtJpy(diff) + ' 余剰';
diffEl.className = 'wb-status-diff under';
} else {
diffEl.textContent = fmtJpy(Math.abs(diff)) + ' 超過';
diffEl.className = 'wb-status-diff over';
}

// Progress bar
const pf = document.getElementById('wb-progress-fill');
const pPct = budget > 0 ? Math.min((allocated / budget) * 100, 120) : 0;
pf.style.width = Math.min(pPct, 100) + '%';
pf.style.background = pPct > 100 ? '#c62828' : pPct > 90 ? '#e65100' : '#c0396b';
document.getElementById('wb-pct-total-label').textContent = '合計 ' + pctTotal + '%';

// Warning
const warn = document.getElementById('wb-pct-warning');
warn.style.display = (pctTotal !== 100) ? 'block' : 'none';
if (pctTotal > 100) {
warn.textContent = `注意：各項目の合計が ${pctTotal}%（${pctTotal - 100}% 超過）になっています。スライダーを調整してください。`;
} else {
warn.textContent = `注意：各項目の合計が ${pctTotal}%（${100 - pctTotal}% 未配分）です。スライダーを調整してください。`;
}

// Goshugi banner
document.getElementById('wb-disp-goshugi').textContent = fmtJpy(goshugi);
const jifutanEl = document.getElementById('wb-disp-jifutan');
jifutanEl.textContent = jifutan >= 0 ? fmtJpy(jifutan) : '▲' + fmtJpy(Math.abs(jifutan));
jifutanEl.style.color = jifutan > 0 ? '#c0396b' : jifutan < 0 ? '#2e7d32' : '#3949ab';

const perGoshugi = guests > 0 ? goshugi / guests : 0;
document.getElementById('wb-per-goshugi').textContent = fmtJpy(Math.round(perGoshugi / 1000) * 1000);

// Per guest
document.getElementById('wb-per-person-val').textContent = guests > 0
? fmtJpy(Math.round(allocated / guests / 100) * 100)
: '—';

// Pie
drawPie(amounts, CATEGORIES.map(c => c.color));
buildLegend(amounts);
}

render();
})();
</script>

</div>
