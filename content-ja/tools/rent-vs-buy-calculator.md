---
title: "賃貸vs購入シミュレーター - 賃貸と持ち家どちらがお得？"
date: 2025-09-22
description: "賃貸と持ち家の総コストを長期で比較。損益分岐点を可視化して、あなたの状況に合った最適な選択を見つけましょう。"
categories: ["無料ツール"]
slug: "rent-vs-buy-calculator"
ShowToc: false
cover:
  image: "/images/covers/rent-vs-buy-calculator.png"
  alt: "賃貸vs購入シミュレーター"
---

<div id="rvb-app">
<style>
#rvb-app {
font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, -apple-system, BlinkMacSystemFont, sans-serif;
max-width: 900px;
margin: 0 auto;
color: #1a1a2e;
background: #f8f9ff;
border-radius: 16px;
overflow: hidden;
box-shadow: 0 4px 24px rgba(0,0,0,0.08);
}
#rvb-app h2 {
margin: 0;
font-size: 1.05rem;
font-weight: 700;
letter-spacing: 0.02em;
}
#rvb-app .rvb-header {
background: linear-gradient(135deg, #16213e 0%, #0f3460 100%);
color: #fff;
padding: 28px 32px;
text-align: center;
}
#rvb-app .rvb-header h1 {
margin: 0 0 8px;
font-size: 1.5rem;
font-weight: 800;
}
#rvb-app .rvb-header p {
margin: 0;
opacity: 0.8;
font-size: 0.93rem;
}
#rvb-app .rvb-body {
padding: 28px 32px;
}
#rvb-app .rvb-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
margin-bottom: 20px;
}
@media (max-width: 620px) {
#rvb-app .rvb-grid { grid-template-columns: 1fr; }
#rvb-app .rvb-body { padding: 20px 16px; }
}
#rvb-app .rvb-card {
background: #fff;
border-radius: 12px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
}
#rvb-app .rvb-card.rent-card { border-top: 4px solid #3498db; }
#rvb-app .rvb-card.buy-card  { border-top: 4px solid #e67e22; }
#rvb-app .rvb-card h2 { margin-bottom: 16px; }
#rvb-app .rvb-card.rent-card h2 { color: #3498db; }
#rvb-app .rvb-card.buy-card h2  { color: #e67e22; }
#rvb-app .rvb-field {
margin-bottom: 14px;
}
#rvb-app .rvb-field label {
display: block;
font-size: 0.8rem;
font-weight: 600;
color: #555;
margin-bottom: 5px;
letter-spacing: 0.03em;
}
#rvb-app .rvb-field input[type="number"],
#rvb-app .rvb-field input[type="range"] {
width: 100%;
box-sizing: border-box;
}
#rvb-app .rvb-field input[type="number"] {
padding: 8px 12px;
border: 1.5px solid #dde1f0;
border-radius: 8px;
font-size: 0.97rem;
color: #1a1a2e;
background: #f8f9ff;
transition: border-color 0.2s;
-moz-appearance: textfield;
}
#rvb-app .rvb-field input[type="number"]::-webkit-outer-spin-button,
#rvb-app .rvb-field input[type="number"]::-webkit-inner-spin-button { -webkit-appearance: none; }
#rvb-app .rvb-field input[type="number"]:focus {
outline: none;
border-color: #0f3460;
background: #fff;
}
#rvb-app .rvb-shared-card {
background: #fff;
border-radius: 12px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
margin-bottom: 20px;
border-top: 4px solid #6c5ce7;
}
#rvb-app .rvb-shared-card h2 { color: #6c5ce7; margin-bottom: 16px; }
#rvb-app .rvb-shared-inner {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 14px;
}
@media (max-width: 620px) {
#rvb-app .rvb-shared-inner { grid-template-columns: 1fr 1fr; }
}
#rvb-app .rvb-timeline-card {
background: #fff;
border-radius: 12px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
margin-bottom: 20px;
}
#rvb-app .rvb-timeline-card label {
display: flex;
justify-content: space-between;
align-items: center;
font-weight: 700;
font-size: 1rem;
margin-bottom: 10px;
}
#rvb-app .rvb-timeline-card label span {
background: #0f3460;
color: #fff;
padding: 3px 12px;
border-radius: 20px;
font-size: 0.93rem;
}
#rvb-app input[type="range"] {
-webkit-appearance: none;
height: 6px;
border-radius: 3px;
background: #dde1f0;
cursor: pointer;
}
#rvb-app input[type="range"]::-webkit-slider-thumb {
-webkit-appearance: none;
width: 20px;
height: 20px;
border-radius: 50%;
background: #0f3460;
cursor: pointer;
box-shadow: 0 2px 6px rgba(15,52,96,0.3);
}
#rvb-app .rvb-chart-card {
background: #fff;
border-radius: 12px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
margin-bottom: 20px;
}
#rvb-app .rvb-chart-card h2 { margin-bottom: 16px; color: #1a1a2e; }
#rvb-app canvas {
width: 100% !important;
max-width: 100%;
border-radius: 8px;
}
#rvb-app .rvb-legend {
display: flex;
gap: 20px;
margin-top: 10px;
flex-wrap: wrap;
}
#rvb-app .rvb-legend-item {
display: flex;
align-items: center;
gap: 7px;
font-size: 0.85rem;
font-weight: 600;
}
#rvb-app .rvb-legend-dot {
width: 14px;
height: 14px;
border-radius: 3px;
flex-shrink: 0;
}
#rvb-app .rvb-result-card {
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
text-align: center;
}
#rvb-app .rvb-result-card.rent-wins {
background: linear-gradient(135deg, #e8f4fd, #d0eaf9);
border: 2px solid #3498db;
}
#rvb-app .rvb-result-card.buy-wins {
background: linear-gradient(135deg, #fef3e8, #fde8cc);
border: 2px solid #e67e22;
}
#rvb-app .rvb-result-card.tie {
background: linear-gradient(135deg, #f3f0ff, #e8e3ff);
border: 2px solid #6c5ce7;
}
#rvb-app .rvb-result-title {
font-size: 1.25rem;
font-weight: 800;
margin-bottom: 8px;
}
#rvb-app .rvb-result-subtitle {
font-size: 0.9rem;
opacity: 0.8;
margin-bottom: 16px;
}
#rvb-app .rvb-stats-row {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 12px;
margin-top: 8px;
}
@media (max-width: 540px) {
#rvb-app .rvb-stats-row { grid-template-columns: 1fr; }
}
#rvb-app .rvb-stat-box {
background: #fff;
border-radius: 10px;
padding: 14px 10px;
box-shadow: 0 1px 4px rgba(0,0,0,0.07);
}
#rvb-app .rvb-stat-label {
font-size: 0.72rem;
font-weight: 600;
letter-spacing: 0.03em;
color: #777;
margin-bottom: 4px;
}
#rvb-app .rvb-stat-value {
font-size: 1.05rem;
font-weight: 800;
color: #1a1a2e;
}
#rvb-app .rvb-breakeven {
background: #fff;
border-radius: 12px;
padding: 18px 20px;
margin-bottom: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
display: flex;
align-items: center;
gap: 14px;
}
#rvb-app .rvb-breakeven-icon {
font-size: 1.8rem;
flex-shrink: 0;
}
#rvb-app .rvb-breakeven-text strong {
display: block;
font-size: 0.97rem;
font-weight: 700;
margin-bottom: 2px;
}
#rvb-app .rvb-breakeven-text span {
font-size: 0.85rem;
color: #555;
}
#rvb-app .rvb-cta {
background: linear-gradient(135deg, #1a3a5c 0%, #0f5c46 100%);
border-radius: 12px;
padding: 22px 24px;
margin-bottom: 20px;
color: #fff;
}
#rvb-app .rvb-cta p {
margin: 0 0 10px;
font-size: 0.92rem;
opacity: 0.92;
line-height: 1.6;
}
#rvb-app .rvb-cta a {
display: inline-block;
background: #fff;
color: #0f3460;
padding: 10px 20px;
border-radius: 8px;
font-weight: 700;
text-decoration: none;
font-size: 0.9rem;
transition: opacity 0.15s;
}
#rvb-app .rvb-cta a:hover { opacity: 0.85; }
</style>

<div class="rvb-header">
<h1>賃貸 vs 購入シミュレーター</h1>
<p>賃貸と持ち家の長期コストを比較して、あなたに最適な選択を見つけよう</p>
</div>

<div class="rvb-body">

<!-- 入力グリッド -->
<div class="rvb-grid">
<!-- 賃貸カード -->
<div class="rvb-card rent-card">
<h2>賃貸の場合</h2>
<div class="rvb-field">
<label>月額家賃（円）</label>
<input type="number" id="rvb-monthly-rent" value="100000" min="0" step="1000">
</div>
<div class="rvb-field">
<label>家賃年間上昇率（%）</label>
<input type="number" id="rvb-rent-increase" value="1" min="0" max="20" step="0.1">
</div>
<div class="rvb-field">
<label>火災保険料（円/月）</label>
<input type="number" id="rvb-renters-insurance" value="1500" min="0" step="100">
</div>
</div>

<!-- 購入カード -->
<div class="rvb-card buy-card">
<h2>購入の場合</h2>
<div class="rvb-field">
<label>物件価格（円）</label>
<input type="number" id="rvb-home-price" value="50000000" min="0" step="100000">
</div>
<div class="rvb-field">
<label>頭金割合（%）</label>
<input type="number" id="rvb-down-pct" value="20" min="0" max="100" step="0.5">
</div>
<div class="rvb-field">
<label>住宅ローン金利（%）</label>
<input type="number" id="rvb-interest-rate" value="1.5" min="0" max="20" step="0.05">
</div>
<div class="rvb-field">
<label>返済期間（年）</label>
<input type="number" id="rvb-loan-term" value="35" min="5" max="50" step="5">
</div>
<div class="rvb-field">
<label>固定資産税（物件価格の %/年）</label>
<input type="number" id="rvb-property-tax" value="0.7" min="0" max="5" step="0.05">
</div>
<div class="rvb-field">
<label>管理費・修繕積立金（円/月）</label>
<input type="number" id="rvb-hoa" value="20000" min="0" step="1000">
</div>
<div class="rvb-field">
<label>維持修繕費（物件価格の %/年）</label>
<input type="number" id="rvb-maintenance" value="0.5" min="0" max="5" step="0.1">
</div>
<div class="rvb-field">
<label>火災・地震保険（円/月）</label>
<input type="number" id="rvb-home-insurance" value="5000" min="0" step="500">
</div>
</div>
</div>

<!-- 共通前提 -->
<div class="rvb-shared-card">
<h2>共通の前提条件</h2>
<div class="rvb-shared-inner">
<div class="rvb-field">
<label>投資収益率（%/年）</label>
<input type="number" id="rvb-invest-return" value="5" min="0" max="30" step="0.5">
</div>
<div class="rvb-field">
<label>不動産価格上昇率（%/年）</label>
<input type="number" id="rvb-home-apprec" value="1" min="-5" max="20" step="0.5">
</div>
<div class="rvb-field">
<label>売却コスト（物件価格の %）</label>
<input type="number" id="rvb-sell-cost" value="5" min="0" max="15" step="0.5">
</div>
</div>
</div>

<!-- タイムラインスライダー -->
<div class="rvb-timeline-card">
<label>
シミュレーション期間
<span id="rvb-timeline-label">15年</span>
</label>
<input type="range" id="rvb-timeline" min="5" max="30" value="15" step="1">
</div>

<!-- チャート -->
<div class="rvb-chart-card">
<h2>累積純コストの推移</h2>
<canvas id="rvb-canvas" height="280"></canvas>
<div class="rvb-legend">
<div class="rvb-legend-item">
<div class="rvb-legend-dot" style="background:#3498db;"></div>
賃貸（純コスト）
</div>
<div class="rvb-legend-item">
<div class="rvb-legend-dot" style="background:#e67e22;"></div>
購入（純コスト）
</div>
</div>
</div>

<!-- 損益分岐点 -->
<div class="rvb-breakeven" id="rvb-breakeven-box">
<div class="rvb-breakeven-icon" id="rvb-breakeven-icon">&#8987;</div>
<div class="rvb-breakeven-text">
<strong id="rvb-breakeven-title">計算中...</strong>
<span id="rvb-breakeven-desc"></span>
</div>
</div>

<!-- 結果サマリー -->
<div class="rvb-result-card" id="rvb-result-card">
<div class="rvb-result-title" id="rvb-result-title"></div>
<div class="rvb-result-subtitle" id="rvb-result-subtitle"></div>
<div class="rvb-stats-row">
<div class="rvb-stat-box">
<div class="rvb-stat-label">賃貸の総純コスト</div>
<div class="rvb-stat-value" id="rvb-stat-rent-cost"></div>
</div>
<div class="rvb-stat-box">
<div class="rvb-stat-label">購入の総純コスト</div>
<div class="rvb-stat-value" id="rvb-stat-buy-cost"></div>
</div>
<div class="rvb-stat-box">
<div class="rvb-stat-label">差額</div>
<div class="rvb-stat-value" id="rvb-stat-diff"></div>
</div>
</div>
</div>

<!-- freee CTA -->
<div class="rvb-cta">
<p>住宅ローン管理を効率化 — 毎月の返済額・資産推移・税務処理をまとめて自動化しましょう。</p>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="nofollow noopener">freee会計で資産管理を自動化</a>
</div>

</div><!-- /.rvb-body -->

<script>
(function() {
'use strict';

function gid(id) { return document.getElementById(id); }
function val(id) { return parseFloat(gid(id).value) || 0; }

var canvas = gid('rvb-canvas');
var ctx = canvas.getContext('2d');

function fmtJPY(n) {
var abs = Math.abs(n);
var sign = n < 0 ? '-' : '';
if (abs >= 1e8) return sign + (abs/1e8).toFixed(2) + '億円';
if (abs >= 1e4) return sign + Math.round(abs/1e4) + '万円';
return sign + Math.round(abs) + '円';
}

function calcMonthlyPayment(principal, annualRate, termYears) {
if (annualRate === 0) return principal / (termYears * 12);
var r = annualRate / 100 / 12;
var n = termYears * 12;
return principal * r * Math.pow(1+r, n) / (Math.pow(1+r, n) - 1);
}

function compute(years) {
var monthlyRent      = val('rvb-monthly-rent');
var rentIncrease     = val('rvb-rent-increase') / 100;
var rentersIns       = val('rvb-renters-insurance');
var homePrice        = val('rvb-home-price');
var downPct          = val('rvb-down-pct') / 100;
var interestRate     = val('rvb-interest-rate');
var loanTerm         = val('rvb-loan-term');
var propTaxPct       = val('rvb-property-tax') / 100;
var hoa              = val('rvb-hoa');
var maintPct         = val('rvb-maintenance') / 100;
var homeIns          = val('rvb-home-insurance');
var investReturn     = val('rvb-invest-return') / 100;
var homeApprec       = val('rvb-home-apprec') / 100;
var sellCostPct      = val('rvb-sell-cost') / 100;

var downPayment = homePrice * downPct;
var loanAmount  = homePrice - downPayment;
var monthlyMortgage = calcMonthlyPayment(loanAmount, interestRate, loanTerm);

var rentData = [];
var buyData  = [];

var rentPortfolio = downPayment;
var totalRentCost = 0;
var currentRent = monthlyRent;

var remainingLoan = loanAmount;
var currentHomeValue = homePrice;
var totalBuyCost = 0;

var monthlyInvestReturn = Math.pow(1 + investReturn, 1/12) - 1;
var monthlyApprec = Math.pow(1 + homeApprec, 1/12) - 1;
var monthlyRate = interestRate / 100 / 12;

var months = years * 12;

for (var m = 1; m <= months; m++) {
if (m > 1 && (m - 1) % 12 === 0) {
currentRent *= (1 + rentIncrease);
}

var rentMonthly = currentRent + rentersIns;
totalRentCost += rentMonthly;

currentHomeValue *= (1 + monthlyApprec);

var interestPaid = remainingLoan * monthlyRate;
var principalPaid = (remainingLoan > 0) ? Math.min(monthlyMortgage - interestPaid, remainingLoan) : 0;
remainingLoan = Math.max(0, remainingLoan - principalPaid);

var propTaxMonthly = (currentHomeValue * propTaxPct) / 12;
var maintMonthly   = (currentHomeValue * maintPct) / 12;
var buyMonthly = (remainingLoan > 0 ? monthlyMortgage : 0) + propTaxMonthly + hoa + maintMonthly + homeIns;
totalBuyCost += buyMonthly;

var diff = buyMonthly - rentMonthly;
rentPortfolio += diff;
rentPortfolio *= (1 + monthlyInvestReturn);

if (m % 12 === 0) {
var yr = m / 12;
var rentNet = totalRentCost - rentPortfolio;
rentData.push({ year: yr, net: rentNet });

var equity = currentHomeValue - remainingLoan;
var sellProceeds = equity - (currentHomeValue * sellCostPct);
var buyNet = totalBuyCost + downPayment - sellProceeds;
buyData.push({ year: yr, net: buyNet });
}
}

return { rentData: rentData, buyData: buyData };
}

function findBreakeven(rentData, buyData) {
for (var i = 0; i < rentData.length; i++) {
if (buyData[i].net < rentData[i].net) {
return rentData[i].year;
}
}
return null;
}

function drawChart(rentData, buyData, years) {
var dpr = window.devicePixelRatio || 1;
var rect = canvas.parentElement.getBoundingClientRect();
var w = rect.width - 40;
var h = 280;
canvas.width  = w * dpr;
canvas.height = h * dpr;
canvas.style.width  = w + 'px';
canvas.style.height = h + 'px';
ctx.scale(dpr, dpr);

var padL = 80, padR = 20, padT = 20, padB = 40;
var chartW = w - padL - padR;
var chartH = h - padT - padB;

ctx.clearRect(0, 0, w, h);

var allVals = rentData.map(function(d){return d.net;}).concat(buyData.map(function(d){return d.net;}));
var minV = Math.min.apply(null, allVals);
var maxV = Math.max.apply(null, allVals);
var padding = (maxV - minV) * 0.1 || 100000;
minV -= padding;
maxV += padding;
var range = maxV - minV;

function xPos(yr) { return padL + ((yr - 1) / (years - 1)) * chartW; }
function yPos(v)  { return padT + (1 - (v - minV) / range) * chartH; }

ctx.strokeStyle = '#eef0f8';
ctx.lineWidth = 1;
for (var g = 0; g <= 5; g++) {
var gy = padT + (g / 5) * chartH;
ctx.beginPath();
ctx.moveTo(padL, gy);
ctx.lineTo(padL + chartW, gy);
ctx.stroke();
var gVal = maxV - (g / 5) * range;
ctx.fillStyle = '#999';
ctx.font = '10px sans-serif';
ctx.textAlign = 'right';
ctx.fillText(fmtJPY(gVal), padL - 5, gy + 4);
}

if (minV < 0 && maxV > 0) {
var zy = yPos(0);
ctx.strokeStyle = '#ccc';
ctx.setLineDash([4, 3]);
ctx.beginPath();
ctx.moveTo(padL, zy);
ctx.lineTo(padL + chartW, zy);
ctx.stroke();
ctx.setLineDash([]);
}

ctx.fillStyle = '#999';
ctx.font = '10px sans-serif';
ctx.textAlign = 'center';
for (var yr = 1; yr <= years; yr++) {
if (yr === 1 || yr % 5 === 0 || yr === years) {
ctx.fillText(yr + '年', xPos(yr), h - padB + 16);
}
}

function drawLine(data, color) {
ctx.strokeStyle = color;
ctx.lineWidth = 2.5;
ctx.lineJoin = 'round';
ctx.lineCap  = 'round';
ctx.beginPath();
for (var i = 0; i < data.length; i++) {
var px = xPos(data[i].year);
var py = yPos(data[i].net);
if (i === 0) ctx.moveTo(px, py);
else ctx.lineTo(px, py);
}
ctx.stroke();
}

drawLine(rentData, '#3498db');
drawLine(buyData,  '#e67e22');

for (var i = 0; i < rentData.length - 1; i++) {
var r0 = rentData[i].net, r1 = rentData[i+1].net;
var b0 = buyData[i].net,  b1 = buyData[i+1].net;
if ((r0 > b0 && r1 <= b1) || (r0 < b0 && r1 >= b1)) {
var bx = xPos(rentData[i].year + 0.5);
var by = yPos((rentData[i].net + buyData[i].net) / 2);
ctx.fillStyle = '#6c5ce7';
ctx.beginPath();
ctx.arc(bx, by, 6, 0, Math.PI * 2);
ctx.fill();
ctx.fillStyle = '#6c5ce7';
ctx.font = 'bold 10px sans-serif';
ctx.textAlign = 'center';
ctx.fillText('損益分岐', bx, by - 12);
break;
}
}
}

function update() {
var years = parseInt(gid('rvb-timeline').value) || 15;
gid('rvb-timeline-label').textContent = years + '年';

var result = compute(years);
var rentData = result.rentData;
var buyData  = result.buyData;

drawChart(rentData, buyData, years);

var lastRent = rentData[rentData.length - 1].net;
var lastBuy  = buyData[buyData.length - 1].net;
var diff = Math.abs(lastRent - lastBuy);
var breakevenYr = findBreakeven(rentData, buyData);

if (breakevenYr !== null) {
gid('rvb-breakeven-icon').textContent = 'X';
gid('rvb-breakeven-title').textContent = '損益分岐点：' + breakevenYr + '年目';
gid('rvb-breakeven-desc').textContent = '購入開始から' + breakevenYr + '年を超えると、購入の方が賃貸よりコストが低くなります。長期居住を計画している場合は購入が有利です。';
} else if (buyData[0].net < rentData[0].net) {
gid('rvb-breakeven-icon').textContent = 'O';
gid('rvb-breakeven-title').textContent = '最初から購入がお得';
gid('rvb-breakeven-desc').textContent = 'この条件では、購入は1年目からコスト的に有利です。';
} else {
gid('rvb-breakeven-icon').textContent = 'X';
gid('rvb-breakeven-title').textContent = breakevenYr === null ? years + '年間、損益分岐点なし' : '損益分岐点：' + breakevenYr + '年目';
gid('rvb-breakeven-desc').textContent = 'この条件では' + years + '年間を通じて賃貸の方がコストが低い状態が続きます。期間を延ばすか、条件を見直してみましょう。';
}

var card = gid('rvb-result-card');
var title = gid('rvb-result-title');
var subtitle = gid('rvb-result-subtitle');
card.className = 'rvb-result-card';

if (diff < Math.max(Math.abs(lastRent), Math.abs(lastBuy)) * 0.02) {
card.classList.add('tie');
title.textContent = years + '年間ではほぼ同コスト';
subtitle.textContent = 'どちらも大きな差がありません。柔軟性・安定性・ライフスタイルなど金銭以外の要素で判断しましょう。';
} else if (lastRent < lastBuy) {
card.classList.add('rent-wins');
title.textContent = years + '年間では賃貸がお得';
subtitle.textContent = 'この期間では、賃貸の方が購入より ' + fmtJPY(diff) + ' コストが低い結果になりました。';
} else {
card.classList.add('buy-wins');
title.textContent = years + '年間では購入がお得';
subtitle.textContent = 'この期間では、購入の方が賃貸より ' + fmtJPY(diff) + ' コストが低い結果になりました。';
}

gid('rvb-stat-rent-cost').textContent = fmtJPY(lastRent);
gid('rvb-stat-buy-cost').textContent  = fmtJPY(lastBuy);
gid('rvb-stat-diff').textContent      = fmtJPY(diff);
}

var inputs = document.querySelectorAll('#rvb-app input');
for (var i = 0; i < inputs.length; i++) {
inputs[i].addEventListener('input', update);
}

update();

var resizeTimer;
window.addEventListener('resize', function() {
clearTimeout(resizeTimer);
resizeTimer = setTimeout(update, 120);
});
})();
</script>

</div>

---

## 関連ツール

> 借金返済計算 → [借金返済計算ツール](/ja/tools/debt-payoff-calculator/)
> ローン比較 → [ローン比較ツール](/ja/tools/loan-comparison/)
> 住宅ローン借入可能額 → [住宅ローン借入可能額ツール](/ja/tools/mortgage-affordability-calculator/)

