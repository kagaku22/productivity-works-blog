---
title: "カロリー計算ツール｜1日の必要摂取カロリー・消費量を自動算出【無料】"
date: 2025-12-03
description: "無料のカロリー計算ツール。年齢・体重・身長・活動レベルから1日の必要カロリーを計算。マクロ栄養素の内訳・減量/増量プランも表示、会員登録不要。"
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
slug: "calorie-calculator"
ShowToc: false
cover:
  image: "/images/covers/calorie-calculator-ja.png"
  alt: "カロリー計算ツール"
---

年齢・身長・体重・活動レベルを入力するだけで、あなたの基礎代謝量（BMR）と1日の総消費カロリー（TDEE）を瞬時に計算。減量・増量プランやマクロ栄養素の内訳もまとめて確認できます。

<div id="cc-app">
<style>
#cc-app *,
#cc-app *::before,
#cc-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#cc-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1e293b;
max-width: 680px;
margin: 0 auto;
padding: 8px 0;
}
#cc-app h2 {
font-size: 20px;
font-weight: 700;
color: #0f172a;
margin-bottom: 18px;
}
#cc-app .cc-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
}
#cc-app .cc-section-title {
font-size: 15px;
font-weight: 700;
color: #334155;
margin-bottom: 16px;
padding-bottom: 8px;
border-bottom: 2px solid #e2e8f0;
}
#cc-app .cc-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 14px;
}
@media (max-width: 520px) {
#cc-app .cc-grid {
grid-template-columns: 1fr;
}
}
#cc-app .cc-field {
display: flex;
flex-direction: column;
gap: 5px;
}
#cc-app .cc-field.cc-full {
grid-column: 1 / -1;
}
#cc-app label {
font-size: 13px;
font-weight: 600;
color: #475569;
}
#cc-app input[type="number"],
#cc-app select {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 15px;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
appearance: none;
-webkit-appearance: none;
}
#cc-app input[type="number"]:focus,
#cc-app select:focus {
outline: none;
border-color: #64748b;
box-shadow: 0 0 0 3px rgba(100,116,139,0.12);
}
#cc-app .cc-gender-row {
display: flex;
gap: 10px;
}
#cc-app .cc-gender-btn {
flex: 1;
padding: 10px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
background: #fff;
font-size: 14px;
font-weight: 600;
color: #64748b;
cursor: pointer;
transition: all 0.15s;
text-align: center;
}
#cc-app .cc-gender-btn.active {
background: #334155;
border-color: #334155;
color: #fff;
}
#cc-app .cc-formula-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
}
#cc-app .cc-formula-btn {
flex: 1;
min-width: 140px;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
background: #fff;
font-size: 13px;
font-weight: 600;
color: #64748b;
cursor: pointer;
transition: all 0.15s;
text-align: center;
}
#cc-app .cc-formula-btn.active {
background: #334155;
border-color: #334155;
color: #fff;
}
#cc-app .cc-btn-primary {
width: 100%;
padding: 14px;
background: #334155;
color: #fff;
border: none;
border-radius: 10px;
font-size: 16px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
margin-top: 4px;
}
#cc-app .cc-btn-primary:hover {
background: #1e293b;
}
#cc-app .cc-results {
display: none;
}
#cc-app .cc-results.visible {
display: block;
}
#cc-app .cc-stat-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 14px;
margin-bottom: 20px;
}
@media (max-width: 400px) {
#cc-app .cc-stat-grid {
grid-template-columns: 1fr;
}
}
#cc-app .cc-stat-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 16px;
text-align: center;
}
#cc-app .cc-stat-box.highlight {
background: #0f172a;
border-color: #0f172a;
color: #fff;
}
#cc-app .cc-stat-label {
font-size: 12px;
font-weight: 600;
color: #64748b;
margin-bottom: 6px;
letter-spacing: 0.02em;
}
#cc-app .cc-stat-box.highlight .cc-stat-label {
color: #94a3b8;
}
#cc-app .cc-stat-value {
font-size: 28px;
font-weight: 800;
color: #0f172a;
line-height: 1;
}
#cc-app .cc-stat-box.highlight .cc-stat-value {
color: #fff;
}
#cc-app .cc-stat-unit {
font-size: 13px;
font-weight: 600;
color: #475569;
margin-top: 2px;
}
#cc-app .cc-stat-box.highlight .cc-stat-unit {
color: #94a3b8;
}
#cc-app .cc-plan-table {
width: 100%;
border-collapse: collapse;
font-size: 14px;
margin-bottom: 4px;
}
#cc-app .cc-plan-table th {
background: #f1f5f9;
color: #334155;
font-weight: 700;
padding: 10px 12px;
text-align: left;
font-size: 13px;
}
#cc-app .cc-plan-table th:last-child,
#cc-app .cc-plan-table td:last-child {
text-align: right;
}
#cc-app .cc-plan-table td {
padding: 10px 12px;
border-bottom: 1px solid #f1f5f9;
color: #1e293b;
}
#cc-app .cc-plan-table tr:last-child td {
border-bottom: none;
}
#cc-app .cc-badge-loss {
display: inline-block;
padding: 2px 8px;
border-radius: 20px;
font-size: 11px;
font-weight: 700;
background: #fef2f2;
color: #b91c1c;
margin-right: 4px;
}
#cc-app .cc-badge-gain {
display: inline-block;
padding: 2px 8px;
border-radius: 20px;
font-size: 11px;
font-weight: 700;
background: #f0fdf4;
color: #15803d;
margin-right: 4px;
}
#cc-app .cc-macro-row {
display: flex;
align-items: center;
gap: 20px;
flex-wrap: wrap;
}
#cc-app .cc-canvas-wrap {
flex-shrink: 0;
display: flex;
align-items: center;
justify-content: center;
}
#cc-app canvas {
display: block;
}
#cc-app .cc-macro-legend {
flex: 1;
min-width: 160px;
display: flex;
flex-direction: column;
gap: 10px;
}
#cc-app .cc-legend-item {
display: flex;
align-items: center;
gap: 10px;
}
#cc-app .cc-legend-dot {
width: 14px;
height: 14px;
border-radius: 50%;
flex-shrink: 0;
}
#cc-app .cc-legend-text {
font-size: 13px;
color: #334155;
flex: 1;
}
#cc-app .cc-legend-val {
font-size: 14px;
font-weight: 700;
color: #0f172a;
}
#cc-app .cc-note {
font-size: 12px;
color: #94a3b8;
margin-top: 14px;
line-height: 1.6;
}
#cc-app .cc-error {
color: #b91c1c;
font-size: 13px;
font-weight: 600;
padding: 10px 14px;
background: #fef2f2;
border: 1px solid #fecaca;
border-radius: 8px;
display: none;
margin-top: 10px;
}
#cc-app .cc-error.visible {
display: block;
}
</style>

<!-- Input Card -->
<div class="cc-card">
<div class="cc-section-title">基本情報を入力</div>
<div class="cc-grid">

<!-- Gender -->
<div class="cc-field cc-full">
<label>性別</label>
<div class="cc-gender-row">
<button class="cc-gender-btn active" id="cc-male" onclick="ccSetGender('male')">男性</button>
<button class="cc-gender-btn" id="cc-female" onclick="ccSetGender('female')">女性</button>
</div>
</div>

<!-- Age -->
<div class="cc-field">
<label for="cc-age">年齢（歳）</label>
<input type="number" id="cc-age" min="10" max="100" placeholder="例: 35">
</div>

<!-- Height -->
<div class="cc-field">
<label for="cc-height">身長（cm）</label>
<input type="number" id="cc-height" min="100" max="250" step="0.1" placeholder="例: 168">
</div>

<!-- Weight -->
<div class="cc-field">
<label for="cc-weight">体重（kg）</label>
<input type="number" id="cc-weight" min="20" max="300" step="0.1" placeholder="例: 65">
</div>

<!-- Activity Level -->
<div class="cc-field">
<label for="cc-activity">活動レベル</label>
<select id="cc-activity">
<option value="1.2">座り仕事（ほぼ運動なし）</option>
<option value="1.375">軽い運動（週1〜3回）</option>
<option value="1.55" selected>中程度の運動（週3〜5回）</option>
<option value="1.725">激しい運動（週6〜7回）</option>
<option value="1.9">非常に激しい運動（1日2回など）</option>
</select>
</div>

<!-- Formula -->
<div class="cc-field cc-full">
<label>計算式</label>
<div class="cc-formula-row">
<button class="cc-formula-btn active" id="cc-mifflin" onclick="ccSetFormula('mifflin')">Mifflin-St Jeor（推奨）</button>
<button class="cc-formula-btn" id="cc-harris" onclick="ccSetFormula('harris')">Harris-Benedict</button>
</div>
</div>

</div>

<div style="margin-top:18px;">
<button class="cc-btn-primary" onclick="ccCalculate()">カロリーを計算する</button>
</div>
<div class="cc-error" id="cc-error">入力内容を確認してください。年齢・身長・体重はすべて正の数で入力してください。</div>
</div>

<!-- Results -->
<div class="cc-results" id="cc-results">

<!-- BMR + TDEE -->
<div class="cc-card">
<div class="cc-section-title">計算結果</div>
<div class="cc-stat-grid">
<div class="cc-stat-box">
<div class="cc-stat-label">基礎代謝量（BMR）</div>
<div class="cc-stat-value" id="cc-bmr-val">—</div>
<div class="cc-stat-unit">kcal/日</div>
</div>
<div class="cc-stat-box highlight">
<div class="cc-stat-label">1日の総消費カロリー（TDEE）</div>
<div class="cc-stat-value" id="cc-tdee-val">—</div>
<div class="cc-stat-unit">kcal/日</div>
</div>
</div>
<p class="cc-note">※ BMR（Basal Metabolic Rate）は安静時に消費するカロリー。TDEEは活動レベルを加味した1日の総消費カロリーです。個人差・体組成によって実際の値は異なります。</p>
</div>

<!-- Weight Goals -->
<div class="cc-card">
<div class="cc-section-title">目標別カロリー摂取量</div>
<table class="cc-plan-table">
<thead>
<tr>
<th>目標</th>
<th>目安摂取カロリー</th>
</tr>
</thead>
<tbody>
<tr>
<td><span class="cc-badge-loss">減量</span> −0.25 kg/週</td>
<td id="cc-loss-025">—</td>
</tr>
<tr>
<td><span class="cc-badge-loss">減量</span> −0.5 kg/週</td>
<td id="cc-loss-05">—</td>
</tr>
<tr>
<td><span class="cc-badge-loss">減量</span> −1 kg/週</td>
<td id="cc-loss-1">—</td>
</tr>
<tr>
<td>現状維持</td>
<td id="cc-maintain">—</td>
</tr>
<tr>
<td><span class="cc-badge-gain">増量</span> +0.25 kg/週</td>
<td id="cc-gain-025">—</td>
</tr>
<tr>
<td><span class="cc-badge-gain">増量</span> +0.5 kg/週</td>
<td id="cc-gain-05">—</td>
</tr>
</tbody>
</table>
<p class="cc-note">※ 1 kg の体脂肪 ≈ 7,200 kcal として算出。極端なカロリー制限は健康に悪影響を与える場合があります。</p>
</div>

<!-- Macros -->
<div class="cc-card">
<div class="cc-section-title">マクロ栄養素バランス（TDEE基準）</div>
<div class="cc-macro-row">
<div class="cc-canvas-wrap">
<canvas id="cc-chart" width="150" height="150"></canvas>
</div>
<div class="cc-macro-legend">
<div class="cc-legend-item">
<div class="cc-legend-dot" style="background:#334155;"></div>
<div class="cc-legend-text">タンパク質（25%）</div>
<div class="cc-legend-val" id="cc-protein">—</div>
</div>
<div class="cc-legend-item">
<div class="cc-legend-dot" style="background:#64748b;"></div>
<div class="cc-legend-text">炭水化物（50%）</div>
<div class="cc-legend-val" id="cc-carb">—</div>
</div>
<div class="cc-legend-item">
<div class="cc-legend-dot" style="background:#94a3b8;"></div>
<div class="cc-legend-text">脂質（25%）</div>
<div class="cc-legend-val" id="cc-fat">—</div>
</div>
</div>
</div>
<p class="cc-note">※ タンパク質・炭水化物は 4 kcal/g、脂質は 9 kcal/g として換算。比率は一般的な目安（P:25% / C:50% / F:25%）です。</p>
</div>

</div><!-- /.cc-results -->

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function () {
var ccGender = 'male';
var ccFormula = 'mifflin';

window.ccSetGender = function (g) {
ccGender = g;
document.getElementById('cc-male').classList.toggle('active', g === 'male');
document.getElementById('cc-female').classList.toggle('active', g === 'female');
};

window.ccSetFormula = function (f) {
ccFormula = f;
document.getElementById('cc-mifflin').classList.toggle('active', f === 'mifflin');
document.getElementById('cc-harris').classList.toggle('active', f === 'harris');
};

window.ccCalculate = function () {
var errorEl = document.getElementById('cc-error');
var resultsEl = document.getElementById('cc-results');
errorEl.classList.remove('visible');
resultsEl.classList.remove('visible');

var age = parseFloat(document.getElementById('cc-age').value);
var height = parseFloat(document.getElementById('cc-height').value);
var weight = parseFloat(document.getElementById('cc-weight').value);
var activity = parseFloat(document.getElementById('cc-activity').value);

if (!age || !height || !weight || age <= 0 || height <= 0 || weight <= 0) {
errorEl.classList.add('visible');
return;
}

var bmr;
if (ccFormula === 'mifflin') {
// Mifflin-St Jeor
if (ccGender === 'male') {
bmr = 10 * weight + 6.25 * height - 5 * age + 5;
} else {
bmr = 10 * weight + 6.25 * height - 5 * age - 161;
}
} else {
// Harris-Benedict (revised Roza & Shizgal 1984)
if (ccGender === 'male') {
bmr = 88.362 + 13.397 * weight + 4.799 * height - 5.677 * age;
} else {
bmr = 447.593 + 9.247 * weight + 3.098 * height - 4.330 * age;
}
}

var tdee = bmr * activity;

// Plans: 1 kg fat ≈ 7200 kcal => 0.25 kg/week = 257 kcal/day deficit, etc.
var loss025 = tdee - 257;
var loss05  = tdee - 500;
var loss1   = tdee - 1000;
var gain025 = tdee + 257;
var gain05  = tdee + 500;

// Macros: P 25%, C 50%, F 25%
var proteinKcal = tdee * 0.25;
var carbKcal    = tdee * 0.50;
var fatKcal     = tdee * 0.25;
var proteinG    = proteinKcal / 4;
var carbG       = carbKcal / 4;
var fatG        = fatKcal / 9;

// Set values
document.getElementById('cc-bmr-val').textContent  = Math.round(bmr).toLocaleString();
document.getElementById('cc-tdee-val').textContent = Math.round(tdee).toLocaleString();
document.getElementById('cc-loss-025').textContent = Math.round(loss025).toLocaleString() + ' kcal/日';
document.getElementById('cc-loss-05').textContent  = Math.round(loss05).toLocaleString()  + ' kcal/日';
document.getElementById('cc-loss-1').textContent   = Math.round(loss1).toLocaleString()   + ' kcal/日';
document.getElementById('cc-maintain').textContent = Math.round(tdee).toLocaleString()    + ' kcal/日';
document.getElementById('cc-gain-025').textContent = Math.round(gain025).toLocaleString() + ' kcal/日';
document.getElementById('cc-gain-05').textContent  = Math.round(gain05).toLocaleString()  + ' kcal/日';

document.getElementById('cc-protein').textContent = Math.round(proteinG) + ' g';
document.getElementById('cc-carb').textContent    = Math.round(carbG)    + ' g';
document.getElementById('cc-fat').textContent     = Math.round(fatG)     + ' g';

// Draw donut chart
ccDrawChart();

resultsEl.classList.add('visible');
resultsEl.scrollIntoView({ behavior: 'smooth', block: 'start' });
};

function ccDrawChart() {
var canvas = document.getElementById('cc-chart');
if (!canvas || !canvas.getContext) return;
var ctx = canvas.getContext('2d');
var W = canvas.width;
var H = canvas.height;
var cx = W / 2;
var cy = H / 2;
var r = 60;
var ri = 36;

ctx.clearRect(0, 0, W, H);

var slices = [
{ ratio: 0.25, color: '#334155' },
{ ratio: 0.50, color: '#64748b' },
{ ratio: 0.25, color: '#94a3b8' }
];

var start = -Math.PI / 2;
for (var i = 0; i < slices.length; i++) {
var end = start + slices[i].ratio * 2 * Math.PI;
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, start, end);
ctx.closePath();
ctx.fillStyle = slices[i].color;
ctx.fill();
start = end;
}

// Donut hole
ctx.beginPath();
ctx.arc(cx, cy, ri, 0, 2 * Math.PI);
ctx.fillStyle = '#f8fafc';
ctx.fill();

// Center label
ctx.fillStyle = '#334155';
ctx.font = 'bold 11px system-ui, sans-serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
ctx.fillText('P/C/F', cx, cy - 7);
ctx.font = '10px system-ui, sans-serif';
ctx.fillStyle = '#64748b';
ctx.fillText('25/50/25', cx, cy + 7);
}
})();
</script>
</div>

---

> BMIを計算 → [BMI計算ツール](/ja/tools/bmi-calculator/)
> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-planner/)
> 投資利益率を計算 → [ROI計算ツール](/ja/tools/roi-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
