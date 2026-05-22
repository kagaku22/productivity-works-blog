---
title: "Loan EMI Calculator"
date: 2025-05-16
description: "Free online loan EMI calculator. Calculate monthly payments, total interest, and amortization schedule for any loan — mortgage, car, personal, or student loans."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "loan-emi-calculator"
ShowToc: false
cover:
  image: "/images/covers/loan-emi-calculator.png"
  alt: "Loan EMI Calculator"
---

Enter your loan details below to instantly calculate your monthly EMI, total interest paid, and a full amortization schedule — no sign-up required, everything runs in your browser.

<div id="emi-app">
<style>
#emi-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1e293b;
max-width: 960px;
margin: 0 auto;
padding: 0;
}
#emi-app *, #emi-app *::before, #emi-app *::after {
box-sizing: border-box;
}

/* ── Tabs ── */
#emi-app .tab-bar {
display: flex;
gap: 4px;
margin-bottom: 24px;
border-bottom: 2px solid #e2e8f0;
}
#emi-app .tab-btn {
background: none;
border: none;
padding: 10px 20px;
font-size: 0.9rem;
font-weight: 600;
color: #64748b;
cursor: pointer;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
}
#emi-app .tab-btn.active {
color: #0f172a;
border-bottom-color: #3b82f6;
}
#emi-app .tab-panel { display: none; }
#emi-app .tab-panel.active { display: block; }

/* ── Card ── */
#emi-app .card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 24px;
}
#emi-app .card-title {
font-size: 1rem;
font-weight: 700;
color: #0f172a;
margin: 0 0 18px 0;
}

/* ── Form ── */
#emi-app .form-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 600px) {
#emi-app .form-grid { grid-template-columns: 1fr; }
}
#emi-app .form-group {
display: flex;
flex-direction: column;
gap: 6px;
}
#emi-app .form-group.full { grid-column: 1 / -1; }
#emi-app label {
font-size: 0.8rem;
font-weight: 600;
color: #475569;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#emi-app input[type="number"],
#emi-app input[type="text"],
#emi-app select {
padding: 10px 12px;
border: 1px solid #cbd5e1;
border-radius: 8px;
font-size: 1rem;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color 0.15s, box-shadow 0.15s;
width: 100%;
}
#emi-app input[type="number"]:focus,
#emi-app input[type="text"]:focus,
#emi-app select:focus {
border-color: #3b82f6;
box-shadow: 0 0 0 3px rgba(59,130,246,0.15);
}
#emi-app .input-row {
display: flex;
gap: 8px;
}
#emi-app .input-row input { flex: 1; }
#emi-app .input-row select { width: auto; flex-shrink: 0; }

/* ── Toggle (years/months) ── */
#emi-app .toggle-group {
display: flex;
border: 1px solid #cbd5e1;
border-radius: 8px;
overflow: hidden;
background: #fff;
}
#emi-app .toggle-group button {
flex: 1;
padding: 10px;
border: none;
background: none;
font-size: 0.9rem;
font-weight: 600;
color: #64748b;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#emi-app .toggle-group button.active {
background: #3b82f6;
color: #fff;
}

/* ── Primary button ── */
#emi-app .btn-primary {
background: #3b82f6;
color: #fff;
border: none;
border-radius: 8px;
padding: 12px 28px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
width: 100%;
margin-top: 8px;
}
#emi-app .btn-primary:hover { background: #2563eb; }

/* ── Summary cards ── */
#emi-app .summary-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 16px;
margin-bottom: 24px;
}
@media (max-width: 640px) {
#emi-app .summary-grid { grid-template-columns: 1fr; }
}
#emi-app .summary-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
text-align: center;
}
#emi-app .summary-card .sc-label {
font-size: 0.75rem;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 8px;
}
#emi-app .summary-card .sc-value {
font-size: 1.6rem;
font-weight: 800;
color: #0f172a;
line-height: 1.1;
}
#emi-app .summary-card.highlight { border-color: #3b82f6; background: #eff6ff; }
#emi-app .summary-card.highlight .sc-value { color: #2563eb; }
#emi-app .summary-card .sc-sub {
font-size: 0.75rem;
color: #94a3b8;
margin-top: 4px;
}

/* ── Charts ── */
#emi-app .charts-row {
display: grid;
grid-template-columns: 1fr 2fr;
gap: 20px;
margin-bottom: 24px;
}
@media (max-width: 680px) {
#emi-app .charts-row { grid-template-columns: 1fr; }
}
#emi-app .chart-box {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
display: flex;
flex-direction: column;
align-items: center;
}
#emi-app .chart-box h3 {
font-size: 0.85rem;
font-weight: 700;
color: #475569;
text-transform: uppercase;
letter-spacing: 0.04em;
margin: 0 0 12px 0;
align-self: flex-start;
}
#emi-app canvas { display: block; max-width: 100%; }
#emi-app .donut-legend {
display: flex;
gap: 16px;
margin-top: 12px;
flex-wrap: wrap;
justify-content: center;
}
#emi-app .donut-legend span {
display: flex;
align-items: center;
gap: 6px;
font-size: 0.8rem;
color: #475569;
font-weight: 600;
}
#emi-app .legend-dot {
width: 12px;
height: 12px;
border-radius: 50%;
display: inline-block;
}

/* ── Ratio bar ── */
#emi-app .ratio-bar-wrap { margin-bottom: 20px; }
#emi-app .ratio-label {
display: flex;
justify-content: space-between;
font-size: 0.78rem;
font-weight: 600;
color: #64748b;
margin-bottom: 6px;
}
#emi-app .ratio-bar {
height: 10px;
border-radius: 99px;
background: #e2e8f0;
overflow: hidden;
}
#emi-app .ratio-bar-fill {
height: 100%;
background: linear-gradient(90deg, #3b82f6, #0ea5e9);
border-radius: 99px;
transition: width 0.5s ease;
}

/* ── Table ── */
#emi-app .table-section { margin-bottom: 24px; }
#emi-app .table-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 12px;
flex-wrap: wrap;
gap: 8px;
}
#emi-app .table-header h3 {
font-size: 1rem;
font-weight: 700;
color: #0f172a;
margin: 0;
}
#emi-app .view-toggle {
display: flex;
border: 1px solid #cbd5e1;
border-radius: 6px;
overflow: hidden;
}
#emi-app .view-toggle button {
padding: 6px 14px;
border: none;
background: none;
font-size: 0.8rem;
font-weight: 600;
color: #64748b;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#emi-app .view-toggle button.active {
background: #3b82f6;
color: #fff;
}
#emi-app .table-scroll {
max-height: 340px;
overflow-y: auto;
border: 1px solid #e2e8f0;
border-radius: 10px;
}
#emi-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.82rem;
}
#emi-app thead th {
background: #f1f5f9;
padding: 10px 12px;
text-align: right;
font-weight: 700;
color: #475569;
text-transform: uppercase;
font-size: 0.72rem;
letter-spacing: 0.04em;
position: sticky;
top: 0;
z-index: 1;
}
#emi-app thead th:first-child { text-align: left; }
#emi-app tbody tr:nth-child(even) td { background: #f8fafc; }
#emi-app tbody tr:hover td { background: #eff6ff; }
#emi-app tbody td {
padding: 9px 12px;
text-align: right;
color: #334155;
border-top: 1px solid #f1f5f9;
}
#emi-app tbody td:first-child { text-align: left; font-weight: 600; color: #1e293b; }
#emi-app tbody tr.yearly-row td {
background: #1e293b !important;
color: #e2e8f0;
font-weight: 700;
}
#emi-app tbody tr.yearly-row td:first-child { color: #fff; }

/* ── Comparison ── */
#emi-app .cmp-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
margin-bottom: 20px;
}
@media (max-width: 600px) {
#emi-app .cmp-grid { grid-template-columns: 1fr; }
}
#emi-app .cmp-result {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
}
#emi-app .cmp-result h4 {
font-size: 0.9rem;
font-weight: 700;
color: #0f172a;
margin: 0 0 16px 0;
padding-bottom: 10px;
border-bottom: 1px solid #f1f5f9;
}
#emi-app .cmp-row {
display: flex;
justify-content: space-between;
align-items: baseline;
padding: 6px 0;
font-size: 0.88rem;
border-bottom: 1px solid #f8fafc;
}
#emi-app .cmp-row .cml { color: #64748b; }
#emi-app .cmp-row .cmv { font-weight: 700; color: #1e293b; }
#emi-app .savings-banner {
background: #f0fdf4;
border: 1px solid #86efac;
border-radius: 10px;
padding: 16px 20px;
display: flex;
justify-content: space-between;
align-items: center;
flex-wrap: wrap;
gap: 12px;
}
#emi-app .savings-banner .sb-label {
font-size: 0.85rem;
font-weight: 600;
color: #166534;
}
#emi-app .savings-banner .sb-value {
font-size: 1.4rem;
font-weight: 800;
color: #15803d;
}
#emi-app .winner-badge {
display: inline-block;
background: #22c55e;
color: #fff;
font-size: 0.7rem;
font-weight: 700;
padding: 3px 8px;
border-radius: 99px;
margin-left: 6px;
vertical-align: middle;
}

/* ── Error / hidden ── */
#emi-app .error-msg {
color: #ef4444;
font-size: 0.82rem;
margin-top: 4px;
display: none;
}
#emi-app .result-section { display: none; }
#emi-app .result-section.visible { display: block; }

/* ── Cross-links ── */
#emi-app .crosslinks {
background: #f1f5f9;
border-radius: 10px;
padding: 16px 20px;
margin-top: 8px;
font-size: 0.85rem;
color: #475569;
line-height: 2;
}
#emi-app .crosslinks a {
color: #2563eb;
text-decoration: none;
font-weight: 600;
}
#emi-app .crosslinks a:hover { text-decoration: underline; }
</style>

<!-- ═══════════════ MAIN CALCULATOR TAB ═══════════════ -->
<div class="tab-bar">
<button class="tab-btn active" onclick="emiShowTab('tab-calc', this)">Calculator</button>
<button class="tab-btn" onclick="emiShowTab('tab-compare', this)">Compare Loans</button>
</div>

<!-- ── CALCULATOR PANEL ── -->
<div id="tab-calc" class="tab-panel active">

<!-- Inputs -->
<div class="card">
<p class="card-title">Loan Details</p>
<div class="form-grid">

<div class="form-group">
<label for="emi-amount">Loan Amount ($)</label>
<input type="number" id="emi-amount" placeholder="e.g. 250000" min="1" step="1">
</div>

<div class="form-group">
<label for="emi-rate">Annual Interest Rate (%)</label>
<input type="number" id="emi-rate" placeholder="e.g. 6.5" min="0.01" step="0.01">
</div>

<div class="form-group">
<label>Loan Term</label>
<div class="input-row">
<input type="number" id="emi-term" placeholder="e.g. 30" min="1" step="1">
<div class="toggle-group" style="flex-shrink:0;">
<button id="emi-term-years" class="active" onclick="emiSetTermUnit('years')">Yrs</button>
<button id="emi-term-months" onclick="emiSetTermUnit('months')">Mo</button>
</div>
</div>
</div>

<div class="form-group">
<label for="emi-start">Start Date</label>
<input type="month" id="emi-start">
</div>

</div>
<div class="error-msg" id="emi-error">Please fill in all fields with valid values.</div>
<button class="btn-primary" onclick="emiCalculate()">Calculate EMI</button>
</div>

<!-- Results -->
<div class="result-section" id="emi-results">

<!-- Summary cards -->
<div class="summary-grid">
<div class="summary-card highlight">
<div class="sc-label">Monthly EMI</div>
<div class="sc-value" id="res-emi">—</div>
<div class="sc-sub">per month</div>
</div>
<div class="summary-card">
<div class="sc-label">Total Interest</div>
<div class="sc-value" id="res-interest">—</div>
<div class="sc-sub" id="res-interest-pct">—</div>
</div>
<div class="summary-card">
<div class="sc-label">Total Payment</div>
<div class="sc-value" id="res-total">—</div>
<div class="sc-sub" id="res-months-label">—</div>
</div>
</div>

<!-- Principal vs Interest ratio bar -->
<div class="ratio-bar-wrap">
<div class="ratio-label">
<span id="ratio-principal-label">Principal</span>
<span id="ratio-interest-label">Interest</span>
</div>
<div class="ratio-bar"><div class="ratio-bar-fill" id="ratio-bar-fill" style="width:50%"></div></div>
</div>

<!-- Charts -->
<div class="charts-row">
<div class="chart-box">
<h3>Breakdown</h3>
<canvas id="donut-canvas" width="180" height="180"></canvas>
<div class="donut-legend">
<span><span class="legend-dot" style="background:#3b82f6"></span>Principal</span>
<span><span class="legend-dot" style="background:#f97316"></span>Interest</span>
</div>
</div>
<div class="chart-box">
<h3>Balance Over Time</h3>
<canvas id="line-canvas" width="460" height="220"></canvas>
</div>
</div>

<!-- Amortization table -->
<div class="table-section">
<div class="table-header">
<h3>Amortization Schedule</h3>
<div class="view-toggle">
<button class="active" id="view-monthly-btn" onclick="emiShowView('monthly')">Monthly</button>
<button id="view-yearly-btn" onclick="emiShowView('yearly')">Yearly</button>
</div>
</div>
<div class="table-scroll">
<table>
<thead>
<tr>
<th>Period</th>
<th>Payment</th>
<th>Principal</th>
<th>Interest</th>
<th>Balance</th>
</tr>
</thead>
<tbody id="amort-tbody"></tbody>
</table>
</div>
</div>

</div><!-- /result-section -->
</div><!-- /tab-calc -->

<!-- ── COMPARE PANEL ── -->
<div id="tab-compare" class="tab-panel">
<div class="cmp-grid">
<!-- Loan A -->
<div class="card" style="margin-bottom:0">
<p class="card-title">Loan A</p>
<div class="form-group" style="margin-bottom:12px">
<label for="cmp-a-amount">Loan Amount ($)</label>
<input type="number" id="cmp-a-amount" placeholder="e.g. 200000" min="1">
</div>
<div class="form-group" style="margin-bottom:12px">
<label for="cmp-a-rate">Annual Rate (%)</label>
<input type="number" id="cmp-a-rate" placeholder="e.g. 6.0" min="0.01" step="0.01">
</div>
<div class="form-group">
<label for="cmp-a-term">Term (years)</label>
<input type="number" id="cmp-a-term" placeholder="e.g. 30" min="1">
</div>
</div>
<!-- Loan B -->
<div class="card" style="margin-bottom:0">
<p class="card-title">Loan B</p>
<div class="form-group" style="margin-bottom:12px">
<label for="cmp-b-amount">Loan Amount ($)</label>
<input type="number" id="cmp-b-amount" placeholder="e.g. 200000" min="1">
</div>
<div class="form-group" style="margin-bottom:12px">
<label for="cmp-b-rate">Annual Rate (%)</label>
<input type="number" id="cmp-b-rate" placeholder="e.g. 7.0" min="0.01" step="0.01">
</div>
<div class="form-group">
<label for="cmp-b-term">Term (years)</label>
<input type="number" id="cmp-b-term" placeholder="e.g. 25" min="1">
</div>
</div>
</div>
<button class="btn-primary" style="margin-top:16px;margin-bottom:24px" onclick="emiCompare()">Compare Loans</button>
<div id="cmp-error" class="error-msg">Please fill in all fields for both loans.</div>

<div class="result-section" id="cmp-results">
<div class="cmp-grid" id="cmp-cards"></div>
<div class="savings-banner" id="cmp-savings"></div>
</div>
</div><!-- /tab-compare -->

<!-- Cross-links -->
<div class="crosslinks">
<strong>Related Tools</strong><br>
&rsaquo; Calculate compound interest &rarr; <a href="/tools/compound-interest-calculator/">Compound Interest Calculator</a><br>
&rsaquo; Track ROI &rarr; <a href="/tools/roi-calculator/">ROI Calculator</a><br>
&rsaquo; Plan retirement &rarr; <a href="/tools/pension-simulator/">Pension Simulator</a>
</div>

<!-- ═══════════════ JAVASCRIPT ═══════════════ -->
<script>
(function() {
'use strict';

/* ── State ── */
let termUnit = 'years';      // 'years' | 'months'
let tableView = 'monthly';   // 'monthly' | 'yearly'
let scheduleData = [];       // full monthly schedule

/* ── Helpers ── */
const $ = id => document.getElementById(id);
const fmt = (n, dec=2) => '$' + n.toFixed(dec).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
const fmtN = (n, dec=2) => n.toFixed(dec).replace(/\B(?=(\d{3})+(?!\d))/g, ',');

/* ── Tabs ── */
window.emiShowTab = function(panelId, btn) {
document.querySelectorAll('#emi-app .tab-panel').forEach(p => p.classList.remove('active'));
document.querySelectorAll('#emi-app .tab-btn').forEach(b => b.classList.remove('active'));
$(panelId).classList.add('active');
btn.classList.add('active');
};

/* ── Term unit toggle ── */
window.emiSetTermUnit = function(unit) {
termUnit = unit;
$('emi-term-years').classList.toggle('active', unit === 'years');
$('emi-term-months').classList.toggle('active', unit === 'months');
};

/* ── View toggle ── */
window.emiShowView = function(view) {
tableView = view;
$('view-monthly-btn').classList.toggle('active', view === 'monthly');
$('view-yearly-btn').classList.toggle('active', view === 'yearly');
renderTable(scheduleData);
};

/* Set default start date to current month */
(function setDefaultDate() {
const now = new Date();
const y = now.getFullYear();
const m = String(now.getMonth() + 1).padStart(2, '0');
$('emi-start').value = y + '-' + m;
})();

/* ── Core EMI calc ── */
function calcEMI(P, annualRate, months) {
if (annualRate === 0) return P / months;
const r = annualRate / 100 / 12;
const pow = Math.pow(1 + r, months);
return P * r * pow / (pow - 1);
}

function buildSchedule(P, annualRate, months, startYear, startMonth) {
const emi = calcEMI(P, annualRate, months);
const r = annualRate / 100 / 12;
let balance = P;
const rows = [];
let y = startYear, mo = startMonth;
for (let i = 1; i <= months; i++) {
const interest = balance * r;
const principal = Math.min(emi - interest, balance);
balance = Math.max(balance - principal, 0);
const moName = new Date(y, mo - 1).toLocaleString('en', {month:'short', year:'numeric'});
rows.push({ n: i, label: moName, payment: emi, principal, interest, balance, year: y });
mo++;
if (mo > 12) { mo = 1; y++; }
}
// fix last row rounding
if (rows.length) rows[rows.length - 1].balance = 0;
return { emi, rows };
}

/* ── Main calculate ── */
window.emiCalculate = function() {
const P = parseFloat($('emi-amount').value);
const rate = parseFloat($('emi-rate').value);
const termVal = parseFloat($('emi-term').value);
const startRaw = $('emi-start').value || '';

const errEl = $('emi-error');
if (!P || P <= 0 || !rate || rate <= 0 || !termVal || termVal <= 0) {
errEl.style.display = 'block';
return;
}
errEl.style.display = 'none';

const months = termUnit === 'years' ? Math.round(termVal * 12) : Math.round(termVal);
const [startYear, startMonth] = startRaw ? startRaw.split('-').map(Number) : [new Date().getFullYear(), new Date().getMonth()+1];

const { emi, rows } = buildSchedule(P, rate, months, startYear, startMonth);
scheduleData = rows;

const totalPayment = emi * months;
const totalInterest = totalPayment - P;
const principalPct = (P / totalPayment * 100).toFixed(1);
const interestPct = (totalInterest / totalPayment * 100).toFixed(1);

/* Summary cards */
$('res-emi').textContent = fmt(emi);
$('res-interest').textContent = fmt(totalInterest);
$('res-interest-pct').textContent = interestPct + '% of total payment';
$('res-total').textContent = fmt(totalPayment);
$('res-months-label').textContent = months + ' payments';

/* Ratio bar */
$('ratio-principal-label').textContent = 'Principal ' + principalPct + '%';
$('ratio-interest-label').textContent = 'Interest ' + interestPct + '%';
$('ratio-bar-fill').style.width = principalPct + '%';

/* Show result section */
$('emi-results').classList.add('visible');

/* Charts */
requestAnimationFrame(() => {
drawDonut($('donut-canvas'), P, totalInterest);
drawLine($('line-canvas'), rows);
renderTable(rows);
});
};

/* ── Donut chart ── */
function drawDonut(canvas, principal, interest) {
const ctx = canvas.getContext('2d');
const W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);
const cx = W / 2, cy = H / 2, r = Math.min(W, H) * 0.42;
const inner = r * 0.55;
const total = principal + interest;
const pAngle = (principal / total) * 2 * Math.PI;
const colors = ['#3b82f6', '#f97316'];
const angles = [pAngle, 2 * Math.PI - pAngle];
let start = -Math.PI / 2;
angles.forEach((a, i) => {
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, start, start + a);
ctx.closePath();
ctx.fillStyle = colors[i];
ctx.fill();
start += a;
});
// inner hole
ctx.beginPath();
ctx.arc(cx, cy, inner, 0, 2 * Math.PI);
ctx.fillStyle = '#fff';
ctx.fill();
// center text
ctx.fillStyle = '#1e293b';
ctx.font = 'bold 13px system-ui,sans-serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
ctx.fillText((principal / total * 100).toFixed(0) + '%', cx, cy - 8);
ctx.fillStyle = '#64748b';
ctx.font = '10px system-ui,sans-serif';
ctx.fillText('Principal', cx, cy + 10);
}

/* ── Line chart ── */
function drawLine(canvas, rows) {
const ctx = canvas.getContext('2d');
const W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);

const pad = { top: 16, right: 16, bottom: 36, left: 64 };
const cW = W - pad.left - pad.right;
const cH = H - pad.top - pad.bottom;

// Downsample for readability (max 120 points)
const step = Math.max(1, Math.floor(rows.length / 120));
const pts = rows.filter((_, i) => i % step === 0 || i === rows.length - 1);

const maxBalance = rows[0].balance + rows[0].principal + rows[0].interest;
const minBal = 0;

/* Grid lines */
ctx.strokeStyle = '#f1f5f9';
ctx.lineWidth = 1;
for (let i = 0; i <= 4; i++) {
const y = pad.top + (cH / 4) * i;
ctx.beginPath();
ctx.moveTo(pad.left, y);
ctx.lineTo(pad.left + cW, y);
ctx.stroke();
const val = maxBalance * (1 - i / 4);
ctx.fillStyle = '#94a3b8';
ctx.font = '10px system-ui,sans-serif';
ctx.textAlign = 'right';
ctx.textBaseline = 'middle';
ctx.fillText('$' + (val >= 1000 ? (val/1000).toFixed(0)+'k' : val.toFixed(0)), pad.left - 6, y);
}

/* X axis labels */
const labelStep = Math.max(1, Math.floor(pts.length / 5));
ctx.fillStyle = '#94a3b8';
ctx.font = '10px system-ui,sans-serif';
ctx.textAlign = 'center';
pts.forEach((d, i) => {
if (i % labelStep !== 0 && i !== pts.length - 1) return;
const x = pad.left + (i / (pts.length - 1)) * cW;
ctx.fillText(d.year, x, H - pad.bottom + 14);
});

/* Helper to map a point */
const px = i => pad.left + (i / (pts.length - 1)) * cW;
const py = v => pad.top + cH - ((v - minBal) / (maxBalance - minBal)) * cH;

/* Filled area – balance */
ctx.beginPath();
pts.forEach((d, i) => {
const x = px(i), y = py(d.balance);
i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
});
ctx.lineTo(px(pts.length - 1), pad.top + cH);
ctx.lineTo(px(0), pad.top + cH);
ctx.closePath();
const grad = ctx.createLinearGradient(0, pad.top, 0, pad.top + cH);
grad.addColorStop(0, 'rgba(59,130,246,0.25)');
grad.addColorStop(1, 'rgba(59,130,246,0.02)');
ctx.fillStyle = grad;
ctx.fill();

/* Line – balance */
ctx.beginPath();
pts.forEach((d, i) => {
const x = px(i), y = py(d.balance);
i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
});
ctx.strokeStyle = '#3b82f6';
ctx.lineWidth = 2.5;
ctx.lineJoin = 'round';
ctx.stroke();

/* Line – cumulative interest */
let cumInt = 0;
const intPts = pts.map(d => { cumInt += d.interest; return cumInt; });
const maxInt = intPts[intPts.length - 1];
// scale cumInt to same axis as balance for comparison
ctx.beginPath();
intPts.forEach((v, i) => {
const x = px(i);
const y = py(Math.min(v, maxBalance));
i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
});
ctx.strokeStyle = '#f97316';
ctx.lineWidth = 2;
ctx.setLineDash([5, 3]);
ctx.stroke();
ctx.setLineDash([]);

/* Legend */
ctx.font = 'bold 10px system-ui,sans-serif';
ctx.textAlign = 'left';
ctx.fillStyle = '#3b82f6';
ctx.fillRect(pad.left, H - 10, 24, 3);
ctx.fillStyle = '#475569';
ctx.fillText('Balance', pad.left + 28, H - 8);

ctx.fillStyle = '#f97316';
const dx = pad.left + 110;
ctx.setLineDash([5, 3]);
ctx.beginPath();
ctx.moveTo(dx, H - 9);
ctx.lineTo(dx + 24, H - 9);
ctx.strokeStyle = '#f97316';
ctx.lineWidth = 2;
ctx.stroke();
ctx.setLineDash([]);
ctx.fillStyle = '#475569';
ctx.fillText('Cumulative Interest', dx + 28, H - 8);
}

/* ── Amortization table ── */
function renderTable(rows) {
const tbody = $('amort-tbody');
tbody.innerHTML = '';

if (tableView === 'monthly') {
rows.forEach(r => {
const tr = document.createElement('tr');
tr.innerHTML = `<td>${r.label}</td><td>${fmt(r.payment)}</td><td>${fmt(r.principal)}</td><td>${fmt(r.interest)}</td><td>${fmt(r.balance)}</td>`;
tbody.appendChild(tr);
});
} else {
// Group by year
const years = {};
rows.forEach(r => {
if (!years[r.year]) years[r.year] = { payment:0, principal:0, interest:0, balance:0 };
years[r.year].payment += r.payment;
years[r.year].principal += r.principal;
years[r.year].interest += r.interest;
years[r.year].balance = r.balance;
});
Object.entries(years).forEach(([yr, d]) => {
const tr = document.createElement('tr');
tr.classList.add('yearly-row');
tr.innerHTML = `<td>Year ${yr}</td><td>${fmt(d.payment)}</td><td>${fmt(d.principal)}</td><td>${fmt(d.interest)}</td><td>${fmt(d.balance)}</td>`;
tbody.appendChild(tr);
});
}
}

/* ── Loan comparison ── */
window.emiCompare = function() {
const fields = ['cmp-a-amount','cmp-a-rate','cmp-a-term','cmp-b-amount','cmp-b-rate','cmp-b-term'];
const vals = fields.map(id => parseFloat($(id).value));
const errEl = $('cmp-error');
if (vals.some(v => !v || v <= 0)) { errEl.style.display = 'block'; return; }
errEl.style.display = 'none';

const [aP, aRate, aTerm, bP, bRate, bTerm] = vals;
const aMo = Math.round(aTerm * 12), bMo = Math.round(bTerm * 12);
const aEMI = calcEMI(aP, aRate, aMo);
const bEMI = calcEMI(bP, bRate, bMo);
const aTotal = aEMI * aMo, bTotal = bEMI * bMo;
const aInt = aTotal - aP, bInt = bTotal - bP;

const winner = aTotal < bTotal ? 'A' : 'B';
const savings = Math.abs(aTotal - bTotal);

const cmpCards = $('cmp-cards');
const makeCard = (label, P, rate, term, emi, total, interest, isWinner) => `
<div class="cmp-result">
<h4>Loan ${label}${isWinner ? '<span class="winner-badge">Cheaper</span>' : ''}</h4>
<div class="cmp-row"><span class="cml">Principal</span><span class="cmv">${fmt(P)}</span></div>
<div class="cmp-row"><span class="cml">Interest Rate</span><span class="cmv">${fmtN(rate)}%</span></div>
<div class="cmp-row"><span class="cml">Term</span><span class="cmv">${term} years</span></div>
<div class="cmp-row"><span class="cml">Monthly EMI</span><span class="cmv">${fmt(emi)}</span></div>
<div class="cmp-row"><span class="cml">Total Interest</span><span class="cmv">${fmt(interest)}</span></div>
<div class="cmp-row"><span class="cml">Total Payment</span><span class="cmv">${fmt(total)}</span></div>
</div>`;
cmpCards.innerHTML = makeCard('A', aP, aRate, aTerm, aEMI, aTotal, aInt, winner==='A')
+ makeCard('B', bP, bRate, bTerm, bEMI, bTotal, bInt, winner==='B');

$('cmp-savings').innerHTML = `
<div>
<div class="sb-label">Total Savings with Loan ${winner}</div>
<div style="font-size:0.78rem;color:#166534;margin-top:2px">Over the full loan term</div>
</div>
<div class="sb-value">${fmt(savings)}</div>`;

$('cmp-results').classList.add('visible');
};

})();
</script>
</div>
