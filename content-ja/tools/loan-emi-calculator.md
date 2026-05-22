---
title: "ローン返済シミュレーター"
date: 2026-01-26
description: "無料のローン返済計算ツール。毎月の返済額・総支払利息・返済スケジュールをシミュレーション。住宅ローン・自動車ローン・教育ローン対応、会員登録不要。"
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
slug: "loan-emi-calculator"
ShowToc: false
cover:
  image: "/images/covers/loan-emi-calculator-ja.png"
  alt: "ローン返済シミュレーター"
---

借入額・年利・返済期間を入力するだけで、毎月の返済額・総支払利息・返済スケジュールをすぐに計算できます。住宅ローン・自動車ローン・教育ローンなど、さまざまなローンに対応した無料シミュレーターです。

<div id="emi-app">
<style>
#emi-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1e293b;
max-width: 900px;
margin: 0 auto;
padding: 0;
box-sizing: border-box;
}
#emi-app *, #emi-app *::before, #emi-app *::after {
box-sizing: border-box;
}
#emi-app h2 {
font-size: 18px;
font-weight: 700;
color: #0f172a;
margin: 0 0 16px 0;
padding-bottom: 8px;
border-bottom: 2px solid #e2e8f0;
}
#emi-app .emi-section {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#emi-app .emi-grid-2 {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 600px) {
#emi-app .emi-grid-2 {
grid-template-columns: 1fr;
}
}
#emi-app .emi-field {
display: flex;
flex-direction: column;
gap: 6px;
}
#emi-app .emi-field label {
font-size: 13px;
font-weight: 600;
color: #475569;
}
#emi-app .emi-field input,
#emi-app .emi-field select {
padding: 10px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 15px;
color: #1e293b;
background: #f8fafc;
transition: border-color 0.2s;
width: 100%;
}
#emi-app .emi-field input:focus,
#emi-app .emi-field select:focus {
outline: none;
border-color: #3b82f6;
background: #fff;
}
#emi-app .emi-period-row {
display: flex;
gap: 8px;
align-items: center;
}
#emi-app .emi-period-row input {
flex: 1;
}
#emi-app .emi-period-row select {
width: 80px;
flex-shrink: 0;
}
#emi-app .emi-radio-group {
display: flex;
gap: 12px;
flex-wrap: wrap;
}
#emi-app .emi-radio-label {
display: flex;
align-items: center;
gap: 6px;
font-size: 14px;
color: #334155;
cursor: pointer;
padding: 8px 14px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
background: #f8fafc;
transition: all 0.2s;
}
#emi-app .emi-radio-label:hover {
border-color: #3b82f6;
background: #eff6ff;
}
#emi-app .emi-radio-label input[type="radio"] {
accent-color: #3b82f6;
width: 15px;
height: 15px;
}
#emi-app .emi-btn {
display: inline-flex;
align-items: center;
justify-content: center;
gap: 6px;
padding: 12px 28px;
background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
color: #fff;
border: none;
border-radius: 9px;
font-size: 15px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.2s, transform 0.1s;
width: 100%;
margin-top: 8px;
}
#emi-app .emi-btn:hover {
opacity: 0.92;
transform: translateY(-1px);
}
#emi-app .emi-btn:active {
transform: translateY(0);
}
#emi-app .emi-summary-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
gap: 14px;
margin-bottom: 20px;
}
#emi-app .emi-card {
background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
border: 1px solid #bae6fd;
border-radius: 10px;
padding: 16px 18px;
text-align: center;
}
#emi-app .emi-card.accent-green {
background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
border-color: #bbf7d0;
}
#emi-app .emi-card.accent-red {
background: linear-gradient(135deg, #fff1f2 0%, #ffe4e6 100%);
border-color: #fecdd3;
}
#emi-app .emi-card.accent-purple {
background: linear-gradient(135deg, #faf5ff 0%, #f3e8ff 100%);
border-color: #e9d5ff;
}
#emi-app .emi-card-label {
font-size: 12px;
color: #64748b;
font-weight: 600;
margin-bottom: 4px;
}
#emi-app .emi-card-value {
font-size: 22px;
font-weight: 800;
color: #0f172a;
line-height: 1.2;
}
#emi-app .emi-card-unit {
font-size: 13px;
color: #64748b;
margin-top: 2px;
}
#emi-app .emi-charts-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
margin-bottom: 20px;
}
@media (max-width: 600px) {
#emi-app .emi-charts-row {
grid-template-columns: 1fr;
}
}
#emi-app .emi-chart-box {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#emi-app .emi-chart-title {
font-size: 14px;
font-weight: 700;
color: #475569;
margin-bottom: 12px;
text-align: center;
}
#emi-app canvas {
max-width: 100%;
display: block;
margin: 0 auto;
}
#emi-app .emi-pie-legend {
display: flex;
justify-content: center;
gap: 16px;
margin-top: 10px;
flex-wrap: wrap;
}
#emi-app .emi-legend-item {
display: flex;
align-items: center;
gap: 5px;
font-size: 12px;
color: #475569;
}
#emi-app .emi-legend-dot {
width: 12px;
height: 12px;
border-radius: 3px;
}
#emi-app .emi-schedule-wrap {
overflow-x: auto;
}
#emi-app table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
}
#emi-app table th {
background: #1e293b;
color: #f1f5f9;
padding: 10px 12px;
text-align: right;
font-weight: 600;
white-space: nowrap;
}
#emi-app table th:first-child {
text-align: left;
border-radius: 6px 0 0 0;
}
#emi-app table th:last-child {
border-radius: 0 6px 0 0;
}
#emi-app table td {
padding: 8px 12px;
text-align: right;
border-bottom: 1px solid #f1f5f9;
color: #334155;
}
#emi-app table td:first-child {
text-align: left;
color: #64748b;
font-weight: 500;
}
#emi-app table tr:nth-child(even) td {
background: #f8fafc;
}
#emi-app table tr.emi-year-row td {
background: #dbeafe;
font-weight: 700;
color: #1e40af;
font-size: 12px;
}
#emi-app .emi-compare-section {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#emi-app .emi-compare-cols {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 600px) {
#emi-app .emi-compare-cols {
grid-template-columns: 1fr;
}
}
#emi-app .emi-compare-loan {
border: 1.5px solid #cbd5e1;
border-radius: 10px;
padding: 16px;
background: #f8fafc;
}
#emi-app .emi-compare-loan h3 {
font-size: 14px;
font-weight: 700;
color: #0f172a;
margin: 0 0 12px 0;
}
#emi-app .emi-compare-result {
margin-top: 14px;
padding: 12px;
border-radius: 8px;
background: #fff;
border: 1px solid #e2e8f0;
font-size: 13px;
color: #334155;
display: none;
}
#emi-app .emi-compare-result .emi-cr-row {
display: flex;
justify-content: space-between;
padding: 3px 0;
border-bottom: 1px solid #f1f5f9;
}
#emi-app .emi-compare-result .emi-cr-row:last-child {
border-bottom: none;
font-weight: 700;
color: #1e293b;
}
#emi-app .emi-hidden {
display: none;
}
#emi-app .emi-result-area {
display: none;
}
#emi-app .emi-error {
color: #dc2626;
font-size: 13px;
margin-top: 6px;
display: none;
}
#emi-app .emi-show-more-wrap {
text-align: center;
margin-top: 12px;
}
#emi-app .emi-show-more-btn {
padding: 8px 20px;
background: #f1f5f9;
border: 1px solid #cbd5e1;
border-radius: 7px;
font-size: 13px;
color: #475569;
cursor: pointer;
font-weight: 600;
transition: background 0.2s;
}
#emi-app .emi-show-more-btn:hover {
background: #e2e8f0;
}
</style>

<!-- ===== 入力フォーム ===== -->
<div class="emi-section">
<h2>ローン条件を入力</h2>
<div class="emi-grid-2">
<div class="emi-field">
<label for="emi-principal">借入額（万円）</label>
<input type="number" id="emi-principal" placeholder="例: 3000" min="1" step="0.1" value="3000">
</div>
<div class="emi-field">
<label for="emi-rate">年利（%）</label>
<input type="number" id="emi-rate" placeholder="例: 1.5" min="0" step="0.01" value="1.5">
</div>
<div class="emi-field">
<label>返済期間</label>
<div class="emi-period-row">
<input type="number" id="emi-period" placeholder="例: 35" min="1" step="1" value="35">
<select id="emi-period-unit">
<option value="year">年</option>
<option value="month">ヶ月</option>
</select>
</div>
</div>
<div class="emi-field">
<label for="emi-start">返済開始年月</label>
<input type="month" id="emi-start" value="2025-06">
</div>
</div>
<div class="emi-field" style="margin-top:16px;">
<label>返済方式</label>
<div class="emi-radio-group">
<label class="emi-radio-label">
<input type="radio" name="emi-method" value="equal-payment" checked> 元利均等（毎月同額）
</label>
<label class="emi-radio-label">
<input type="radio" name="emi-method" value="equal-principal"> 元金均等（元金一定）
</label>
</div>
</div>
<div id="emi-error" class="emi-error">入力値を確認してください。</div>
<button class="emi-btn" onclick="emiCalculate()">計算する</button>
</div>

<!-- ===== 結果エリア ===== -->
<div id="emi-result-area" class="emi-result-area">

<!-- サマリーカード -->
<div class="emi-section">
<h2>計算結果サマリー</h2>
<div class="emi-summary-grid">
<div class="emi-card">
<div class="emi-card-label">毎月の返済額（初回）</div>
<div class="emi-card-value" id="res-monthly">—</div>
<div class="emi-card-unit">万円</div>
</div>
<div class="emi-card accent-green">
<div class="emi-card-label">総支払額</div>
<div class="emi-card-value" id="res-total">—</div>
<div class="emi-card-unit">万円</div>
</div>
<div class="emi-card accent-red">
<div class="emi-card-label">総利息額</div>
<div class="emi-card-value" id="res-interest">—</div>
<div class="emi-card-unit">万円</div>
</div>
<div class="emi-card accent-purple">
<div class="emi-card-label">利息割合</div>
<div class="emi-card-value" id="res-ratio">—</div>
<div class="emi-card-unit">%</div>
</div>
</div>
</div>

<!-- グラフ -->
<div class="emi-charts-row">
<div class="emi-chart-box">
<div class="emi-chart-title">元金 vs 利息（円グラフ）</div>
<canvas id="emi-pie" width="220" height="220"></canvas>
<div class="emi-pie-legend">
<div class="emi-legend-item"><div class="emi-legend-dot" style="background:#3b82f6;"></div>元金</div>
<div class="emi-legend-item"><div class="emi-legend-dot" style="background:#f97316;"></div>利息</div>
</div>
</div>
<div class="emi-chart-box">
<div class="emi-chart-title">元金・利息の推移（年次）</div>
<canvas id="emi-line" width="340" height="220"></canvas>
<div class="emi-pie-legend">
<div class="emi-legend-item"><div class="emi-legend-dot" style="background:#3b82f6;"></div>元金返済累計</div>
<div class="emi-legend-item"><div class="emi-legend-dot" style="background:#f97316;"></div>利息支払累計</div>
</div>
</div>
</div>

<!-- 返済スケジュール表 -->
<div class="emi-section">
<h2>返済スケジュール表</h2>
<div class="emi-schedule-wrap">
<table id="emi-table">
<thead>
<tr>
<th>月</th>
<th>返済額（円）</th>
<th>元金（円）</th>
<th>利息（円）</th>
<th>残高（円）</th>
</tr>
</thead>
<tbody id="emi-tbody"></tbody>
</table>
</div>
<div class="emi-show-more-wrap">
<button class="emi-show-more-btn" id="emi-show-more-btn" onclick="emiToggleFullSchedule()">全期間を表示</button>
</div>
</div>

</div><!-- /result-area -->

<!-- ===== ローン比較 ===== -->
<div class="emi-compare-section">
<h2>ローン比較（2件並列）</h2>
<div class="emi-compare-cols">
<!-- ローンA -->
<div class="emi-compare-loan">
<h3>ローン A</h3>
<div class="emi-field" style="margin-bottom:10px;">
<label>借入額（万円）</label>
<input type="number" id="cmp-a-p" placeholder="例: 3000" value="3000" min="1">
</div>
<div class="emi-field" style="margin-bottom:10px;">
<label>年利（%）</label>
<input type="number" id="cmp-a-r" placeholder="例: 1.0" value="1.0" step="0.01">
</div>
<div class="emi-field" style="margin-bottom:10px;">
<label>返済期間（年）</label>
<input type="number" id="cmp-a-t" placeholder="例: 30" value="30" min="1">
</div>
<div class="emi-field" style="margin-bottom:10px;">
<label>返済方式</label>
<select id="cmp-a-m">
<option value="equal-payment">元利均等</option>
<option value="equal-principal">元金均等</option>
</select>
</div>
<div class="emi-compare-result" id="cmp-a-result"></div>
</div>
<!-- ローンB -->
<div class="emi-compare-loan">
<h3>ローン B</h3>
<div class="emi-field" style="margin-bottom:10px;">
<label>借入額（万円）</label>
<input type="number" id="cmp-b-p" placeholder="例: 3000" value="3000" min="1">
</div>
<div class="emi-field" style="margin-bottom:10px;">
<label>年利（%）</label>
<input type="number" id="cmp-b-r" placeholder="例: 1.5" value="1.5" step="0.01">
</div>
<div class="emi-field" style="margin-bottom:10px;">
<label>返済期間（年）</label>
<input type="number" id="cmp-b-t" placeholder="例: 35" value="35" min="1">
</div>
<div class="emi-field" style="margin-bottom:10px;">
<label>返済方式</label>
<select id="cmp-b-m">
<option value="equal-payment">元利均等</option>
<option value="equal-principal">元金均等</option>
</select>
</div>
<div class="emi-compare-result" id="cmp-b-result"></div>
</div>
</div>
<button class="emi-btn" style="margin-top:16px;" onclick="emiCompare()">比較する</button>
</div>

<!-- ===== freee CTA ===== -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の経費・資金管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、経費精算・資金繰り・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function() {
// ===== ユーティリティ =====
function fmt(yen) {
return Math.round(yen).toLocaleString('ja-JP');
}
function fmtMan(yen) {
return (yen / 10000).toFixed(2);
}
function addMonths(yyyymm, n) {
var y = parseInt(yyyymm.slice(0,4));
var m = parseInt(yyyymm.slice(5,7)) - 1 + n;
y += Math.floor(m / 12);
m = m % 12;
return y + '-' + String(m + 1).padStart(2, '0');
}
function formatYM(yyyymm) {
var y = yyyymm.slice(0,4);
var m = parseInt(yyyymm.slice(5,7));
return y + '年' + m + '月';
}

// ===== 元利均等計算 =====
function calcEqualPayment(principal, annualRate, months) {
var r = annualRate / 100 / 12;
var monthly;
if (r === 0) {
monthly = principal / months;
} else {
monthly = principal * r * Math.pow(1 + r, months) / (Math.pow(1 + r, months) - 1);
}
var schedule = [];
var balance = principal;
for (var i = 0; i < months; i++) {
var interest = balance * r;
var principalPart = monthly - interest;
if (i === months - 1) {
principalPart = balance;
monthly = principalPart + interest;
}
balance -= principalPart;
if (balance < 0.01) balance = 0;
schedule.push({ payment: principalPart + interest, principal: principalPart, interest: interest, balance: balance });
}
return { monthly: schedule[0].payment, schedule: schedule };
}

// ===== 元金均等計算 =====
function calcEqualPrincipal(principal, annualRate, months) {
var r = annualRate / 100 / 12;
var principalPart = principal / months;
var schedule = [];
var balance = principal;
for (var i = 0; i < months; i++) {
var interest = balance * r;
var payment = principalPart + interest;
balance -= principalPart;
if (i === months - 1) balance = 0;
if (balance < 0) balance = 0;
schedule.push({ payment: payment, principal: principalPart, interest: interest, balance: balance });
}
return { monthly: schedule[0].payment, schedule: schedule };
}

function calcLoan(principal, annualRate, months, method) {
if (method === 'equal-principal') return calcEqualPrincipal(principal, annualRate, months);
return calcEqualPayment(principal, annualRate, months);
}

// ===== メイン計算 =====
var _schedule = [];
var _showFull = false;
var _startYM = '2025-06';

window.emiCalculate = function() {
var errEl = document.getElementById('emi-error');
errEl.style.display = 'none';
var p = parseFloat(document.getElementById('emi-principal').value);
var rr = parseFloat(document.getElementById('emi-rate').value);
var t = parseFloat(document.getElementById('emi-period').value);
var unit = document.getElementById('emi-period-unit').value;
var start = document.getElementById('emi-start').value || '2025-06';
var method = document.querySelector('input[name="emi-method"]:checked').value;

if (!p || p <= 0 || isNaN(rr) || rr < 0 || !t || t <= 0) {
errEl.style.display = 'block';
errEl.textContent = '入力値を確認してください（借入額・年利・返済期間は必須です）。';
return;
}
var principal = p * 10000;
var months = unit === 'year' ? Math.round(t * 12) : Math.round(t);
if (months < 1 || months > 600) {
errEl.style.display = 'block';
errEl.textContent = '返済期間が範囲外です（最大50年 / 600ヶ月）。';
return;
}

var result = calcLoan(principal, rr, months, method);
_schedule = result.schedule;
_startYM = start;
_showFull = false;

var totalPayment = _schedule.reduce(function(s, r) { return s + r.payment; }, 0);
var totalInterest = _schedule.reduce(function(s, r) { return s + r.interest; }, 0);
var ratio = totalPayment > 0 ? (totalInterest / totalPayment * 100) : 0;

document.getElementById('res-monthly').textContent = fmtMan(result.monthly);
document.getElementById('res-total').textContent = fmtMan(totalPayment);
document.getElementById('res-interest').textContent = fmtMan(totalInterest);
document.getElementById('res-ratio').textContent = ratio.toFixed(1);

document.getElementById('emi-result-area').style.display = 'block';

drawPie(principal, totalInterest);
drawLine(_schedule, _startYM);
renderTable(_schedule, _startYM, _showFull);
};

// ===== テーブル描画 =====
function renderTable(schedule, startYM, showFull) {
var tbody = document.getElementById('emi-tbody');
tbody.innerHTML = '';
var limit = showFull ? schedule.length : Math.min(24, schedule.length);
var yearPrincipal = 0, yearInterest = 0, yearPayment = 0;
var currentYear = null;

for (var i = 0; i < limit; i++) {
var row = schedule[i];
var ym = addMonths(startYM, i);
var yr = ym.slice(0, 4);
if (currentYear === null) currentYear = yr;

// 年が変わったら年間サマリー行を挿入（前年分）
if (yr !== currentYear) {
var sumRow = document.createElement('tr');
sumRow.className = 'emi-year-row';
sumRow.innerHTML = '<td>' + currentYear + '年 合計</td><td>' + fmt(yearPayment) + '</td><td>' + fmt(yearPrincipal) + '</td><td>' + fmt(yearInterest) + '</td><td>—</td>';
tbody.appendChild(sumRow);
yearPrincipal = 0; yearInterest = 0; yearPayment = 0;
currentYear = yr;
}

yearPrincipal += row.principal;
yearInterest += row.interest;
yearPayment += row.payment;

var tr = document.createElement('tr');
tr.innerHTML = '<td>' + formatYM(ym) + '</td><td>' + fmt(row.payment) + '</td><td>' + fmt(row.principal) + '</td><td>' + fmt(row.interest) + '</td><td>' + fmt(row.balance) + '</td>';
tbody.appendChild(tr);
}
// 最後の年サマリー
if (currentYear && limit === schedule.length) {
var lastSumRow = document.createElement('tr');
lastSumRow.className = 'emi-year-row';
lastSumRow.innerHTML = '<td>' + currentYear + '年 合計</td><td>' + fmt(yearPayment) + '</td><td>' + fmt(yearPrincipal) + '</td><td>' + fmt(yearInterest) + '</td><td>—</td>';
tbody.appendChild(lastSumRow);
}

var btn = document.getElementById('emi-show-more-btn');
if (schedule.length <= 24) {
btn.style.display = 'none';
} else {
btn.style.display = 'inline-block';
btn.textContent = showFull ? '最初の24ヶ月を表示' : '全期間を表示（' + schedule.length + 'ヶ月）';
}
}

window.emiToggleFullSchedule = function() {
_showFull = !_showFull;
renderTable(_schedule, _startYM, _showFull);
};

// ===== 円グラフ =====
function drawPie(principal, interest) {
var canvas = document.getElementById('emi-pie');
var ctx = canvas.getContext('2d');
var W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);
var total = principal + interest;
if (total <= 0) return;
var pRatio = principal / total;
var iRatio = interest / total;
var cx = W / 2, cy = H / 2, r = Math.min(W, H) / 2 - 16;
var start = -Math.PI / 2;

// 元金
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, start, start + 2 * Math.PI * pRatio);
ctx.closePath();
ctx.fillStyle = '#3b82f6';
ctx.fill();

// 利息
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, start + 2 * Math.PI * pRatio, start + 2 * Math.PI);
ctx.closePath();
ctx.fillStyle = '#f97316';
ctx.fill();

// 中央テキスト
ctx.fillStyle = '#fff';
ctx.font = 'bold 13px system-ui, sans-serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
if (pRatio > 0.1) {
var pAngle = start + Math.PI * pRatio;
ctx.fillText(Math.round(pRatio * 100) + '%', cx + Math.cos(pAngle) * r * 0.6, cy + Math.sin(pAngle) * r * 0.6);
}
if (iRatio > 0.1) {
var iAngle = start + 2 * Math.PI * pRatio + Math.PI * iRatio;
ctx.fillText(Math.round(iRatio * 100) + '%', cx + Math.cos(iAngle) * r * 0.6, cy + Math.sin(iAngle) * r * 0.6);
}
}

// ===== 折れ線グラフ =====
function drawLine(schedule, startYM) {
var canvas = document.getElementById('emi-line');
var ctx = canvas.getContext('2d');
var W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);

// 年次データを集計
var years = [];
var yearData = {};
for (var i = 0; i < schedule.length; i++) {
var ym = addMonths(startYM, i);
var yr = ym.slice(0, 4);
if (!yearData[yr]) { yearData[yr] = { principal: 0, interest: 0 }; years.push(yr); }
yearData[yr].principal += schedule[i].principal;
yearData[yr].interest += schedule[i].interest;
}
var pCumul = [], iCumul = [], pSum = 0, iSum = 0;
for (var j = 0; j < years.length; j++) {
pSum += yearData[years[j]].principal;
iSum += yearData[years[j]].interest;
pCumul.push(pSum);
iCumul.push(iSum);
}

var padL = 52, padR = 16, padT = 16, padB = 32;
var w = W - padL - padR, h = H - padT - padB;
var maxVal = Math.max(pCumul[pCumul.length - 1], iCumul[iCumul.length - 1]);
if (maxVal <= 0) return;

function xPos(i) { return padL + (years.length <= 1 ? w / 2 : i / (years.length - 1) * w); }
function yPos(v) { return padT + h - (v / maxVal * h); }

// Grid lines
ctx.strokeStyle = '#e2e8f0';
ctx.lineWidth = 1;
for (var g = 0; g <= 4; g++) {
var gy = padT + h * g / 4;
ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(padL + w, gy); ctx.stroke();
ctx.fillStyle = '#94a3b8';
ctx.font = '10px system-ui, sans-serif';
ctx.textAlign = 'right';
ctx.textBaseline = 'middle';
ctx.fillText(Math.round(maxVal * (4 - g) / 4 / 10000) + '万', padL - 4, gy);
}

// 元金折れ線
ctx.beginPath();
ctx.strokeStyle = '#3b82f6';
ctx.lineWidth = 2.5;
ctx.lineJoin = 'round';
for (var k = 0; k < years.length; k++) {
if (k === 0) ctx.moveTo(xPos(k), yPos(pCumul[k]));
else ctx.lineTo(xPos(k), yPos(pCumul[k]));
}
ctx.stroke();

// 利息折れ線
ctx.beginPath();
ctx.strokeStyle = '#f97316';
ctx.lineWidth = 2.5;
ctx.lineJoin = 'round';
for (var l = 0; l < years.length; l++) {
if (l === 0) ctx.moveTo(xPos(l), yPos(iCumul[l]));
else ctx.lineTo(xPos(l), yPos(iCumul[l]));
}
ctx.stroke();

// X軸ラベル（最大6件）
ctx.fillStyle = '#64748b';
ctx.font = '10px system-ui, sans-serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'top';
var step = Math.max(1, Math.floor(years.length / 6));
for (var m = 0; m < years.length; m += step) {
ctx.fillText(years[m], xPos(m), padT + h + 4);
}
ctx.fillText(years[years.length - 1], xPos(years.length - 1), padT + h + 4);
}

// ===== ローン比較 =====
window.emiCompare = function() {
['a', 'b'].forEach(function(id) {
var p = parseFloat(document.getElementById('cmp-' + id + '-p').value);
var r = parseFloat(document.getElementById('cmp-' + id + '-r').value);
var t = parseFloat(document.getElementById('cmp-' + id + '-t').value);
var m = document.getElementById('cmp-' + id + '-m').value;
var resEl = document.getElementById('cmp-' + id + '-result');
if (!p || p <= 0 || isNaN(r) || r < 0 || !t || t <= 0) {
resEl.style.display = 'block';
resEl.innerHTML = '<div style="color:#dc2626;font-size:13px;">入力値を確認してください。</div>';
return;
}
var principal = p * 10000;
var months = Math.round(t * 12);
var result = calcLoan(principal, r, months, m);
var totalP = result.schedule.reduce(function(s, x) { return s + x.payment; }, 0);
var totalI = result.schedule.reduce(function(s, x) { return s + x.interest; }, 0);
resEl.style.display = 'block';
resEl.innerHTML =
'<div class="emi-cr-row"><span>毎月の返済額（初回）</span><span>' + fmt(result.monthly) + ' 円</span></div>' +
'<div class="emi-cr-row"><span>総支払額</span><span>' + fmtMan(totalP) + ' 万円</span></div>' +
'<div class="emi-cr-row"><span>総利息額</span><span>' + fmtMan(totalI) + ' 万円</span></div>' +
'<div class="emi-cr-row"><span>利息割合</span><span>' + (totalP > 0 ? (totalI / totalP * 100).toFixed(1) : '0.0') + ' %</span></div>';
});
};
})();
</script>

</div><!-- /#emi-app -->

---

> 複利を計算 → [複利計算ツール](/ja/tools/compound-interest-calculator/)
> 投資利益率を計算 → [ROI計算ツール](/ja/tools/roi-calculator/)
> 年金をシミュレーション → [年金シミュレーター](/ja/tools/pension-simulator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
