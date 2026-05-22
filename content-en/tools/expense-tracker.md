---
title: "Expense Tracker"
date: 2025-05-16
description: "Free online expense tracker. Log income and expenses by category, view monthly summaries with charts. Data saved locally in your browser. No sign-up required."
categories: ["Free Tools"]
tags: ["Utility", "Free Tools"]
slug: "expense-tracker"
ShowToc: false
cover:
  image: "/images/covers/expense-tracker.png"
  alt: "Expense Tracker"
---

<div id="et-app">

<style>
#et-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1e293b;
box-sizing: border-box;
}
#et-app *, #et-app *::before, #et-app *::after {
box-sizing: border-box;
}
#et-app h2 {
font-size: 1.05rem;
font-weight: 700;
color: #334155;
margin: 24px 0 10px;
padding-bottom: 6px;
border-bottom: 2px solid #e2e8f0;
}
#et-app .et-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 18px 20px;
margin-bottom: 16px;
}
#et-app label {
display: block;
font-size: 12px;
font-weight: 600;
color: #64748b;
margin-bottom: 4px;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#et-app input, #et-app select, #et-app textarea {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color 0.15s;
}
#et-app input:focus, #et-app select:focus {
border-color: #3b82f6;
}
#et-app .et-grid {
display: grid;
gap: 12px;
}
#et-app .et-grid-2 { grid-template-columns: 1fr 1fr; }
#et-app .et-grid-3 { grid-template-columns: 1fr 1fr 1fr; }
#et-app .et-grid-4 { grid-template-columns: 1fr 1fr 1fr 1fr; }
@media (max-width: 560px) {
#et-app .et-grid-2,
#et-app .et-grid-3,
#et-app .et-grid-4 { grid-template-columns: 1fr; }
}
#et-app .et-type-toggle {
display: flex;
gap: 0;
border-radius: 8px;
overflow: hidden;
border: 1.5px solid #cbd5e1;
width: 100%;
}
#et-app .et-type-toggle button {
flex: 1;
padding: 9px;
border: none;
background: #fff;
font-size: 14px;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
color: #64748b;
}
#et-app .et-type-toggle button.active-income {
background: #22c55e;
color: #fff;
}
#et-app .et-type-toggle button.active-expense {
background: #ef4444;
color: #fff;
}
#et-app .et-btn {
display: inline-block;
padding: 10px 22px;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.15s;
}
#et-app .et-btn:hover { opacity: 0.85; }
#et-app .et-btn-primary { background: #3b82f6; color: #fff; }
#et-app .et-btn-sm {
padding: 5px 12px;
font-size: 12px;
border-radius: 6px;
font-weight: 600;
border: none;
cursor: pointer;
}
#et-app .et-btn-delete { background: #fee2e2; color: #dc2626; }
#et-app .et-btn-edit { background: #eff6ff; color: #2563eb; }
#et-app .et-btn-export { background: #f0fdf4; color: #16a34a; border: 1.5px solid #bbf7d0; }

/* Summary bar */
#et-app .et-summary-bar {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
gap: 12px;
margin-bottom: 16px;
}
#et-app .et-summary-card {
border-radius: 10px;
padding: 14px 16px;
text-align: center;
}
#et-app .et-summary-card .et-s-label {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 4px;
}
#et-app .et-summary-card .et-s-value {
font-size: 1.35rem;
font-weight: 800;
}
#et-app .et-income-card { background: #f0fdf4; border: 1.5px solid #bbf7d0; }
#et-app .et-income-card .et-s-label { color: #16a34a; }
#et-app .et-income-card .et-s-value { color: #15803d; }
#et-app .et-expense-card { background: #fef2f2; border: 1.5px solid #fecaca; }
#et-app .et-expense-card .et-s-label { color: #dc2626; }
#et-app .et-expense-card .et-s-value { color: #b91c1c; }
#et-app .et-balance-card { background: #eff6ff; border: 1.5px solid #bfdbfe; }
#et-app .et-balance-card .et-s-label { color: #2563eb; }
#et-app .et-balance-card .et-s-value { color: #1d4ed8; }
#et-app .et-balance-neg { background: #fef9c3; border-color: #fde68a; }
#et-app .et-balance-neg .et-s-label { color: #b45309; }
#et-app .et-balance-neg .et-s-value { color: #92400e; }

/* Filter row */
#et-app .et-filter-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
align-items: flex-end;
margin-bottom: 14px;
}
#et-app .et-filter-row > div { flex: 1; min-width: 130px; }

/* Table */
#et-app .et-table-wrap { overflow-x: auto; }
#et-app table {
width: 100%;
border-collapse: collapse;
font-size: 13.5px;
}
#et-app thead th {
background: #f1f5f9;
padding: 9px 12px;
text-align: left;
font-size: 11px;
text-transform: uppercase;
letter-spacing: 0.04em;
color: #64748b;
font-weight: 700;
white-space: nowrap;
}
#et-app tbody tr {
border-bottom: 1px solid #f1f5f9;
transition: background 0.1s;
}
#et-app tbody tr:hover { background: #f8fafc; }
#et-app tbody td { padding: 9px 12px; vertical-align: middle; }
#et-app .et-badge {
display: inline-block;
padding: 2px 9px;
border-radius: 99px;
font-size: 11px;
font-weight: 700;
}
#et-app .et-badge-income { background: #dcfce7; color: #16a34a; }
#et-app .et-badge-expense { background: #fee2e2; color: #dc2626; }
#et-app .et-amount-income { color: #16a34a; font-weight: 700; }
#et-app .et-amount-expense { color: #dc2626; font-weight: 700; }
#et-app .et-empty {
text-align: center;
padding: 32px;
color: #94a3b8;
font-size: 14px;
}

/* Chart */
#et-app .et-chart-wrap {
display: flex;
gap: 24px;
align-items: center;
flex-wrap: wrap;
}
#et-app canvas { display: block; }
#et-app .et-legend { flex: 1; min-width: 180px; }
#et-app .et-legend-item {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 7px;
font-size: 13px;
}
#et-app .et-legend-dot {
width: 12px;
height: 12px;
border-radius: 3px;
flex-shrink: 0;
}
#et-app .et-legend-label { flex: 1; color: #475569; }
#et-app .et-legend-val { font-weight: 700; color: #1e293b; }

/* Category breakdown */
#et-app .et-cat-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 8px;
}
#et-app .et-cat-bar-bg {
flex: 1;
height: 8px;
background: #e2e8f0;
border-radius: 99px;
overflow: hidden;
}
#et-app .et-cat-bar-fill {
height: 100%;
border-radius: 99px;
transition: width 0.3s;
}
#et-app .et-cat-name { font-size: 13px; color: #475569; min-width: 90px; }
#et-app .et-cat-amt { font-size: 13px; font-weight: 700; color: #1e293b; min-width: 70px; text-align: right; }

/* Edit modal */
#et-app .et-modal-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(0,0,0,0.4);
z-index: 9999;
align-items: center;
justify-content: center;
}
#et-app .et-modal-overlay.open { display: flex; }
#et-app .et-modal {
background: #fff;
border-radius: 12px;
padding: 24px;
width: 100%;
max-width: 460px;
margin: 16px;
box-shadow: 0 20px 60px rgba(0,0,0,0.2);
}
#et-app .et-modal h3 { margin: 0 0 16px; font-size: 1.1rem; color: #1e293b; }
#et-app .et-modal-actions { display: flex; gap: 10px; justify-content: flex-end; margin-top: 16px; }
#et-app .et-btn-secondary { background: #f1f5f9; color: #475569; }
</style>

<h2>Add Transaction</h2>
<div class="et-card">
<div class="et-grid et-grid-2" style="margin-bottom:12px;">
<div>
<label>Date</label>
<input type="date" id="et-date">
</div>
<div>
<label>Type</label>
<div class="et-type-toggle">
<button id="et-btn-income" class="active-income" onclick="etSetType('income')">+ Income</button>
<button id="et-btn-expense" onclick="etSetType('expense')">- Expense</button>
</div>
</div>
</div>
<div class="et-grid et-grid-3" style="margin-bottom:12px;">
<div style="grid-column:span 2;">
<label>Description</label>
<input type="text" id="et-desc" placeholder="e.g. Grocery run">
</div>
<div>
<label>Amount ($)</label>
<input type="number" id="et-amount" placeholder="0.00" min="0" step="0.01">
</div>
</div>
<div class="et-grid et-grid-2" style="margin-bottom:14px;">
<div>
<label>Category</label>
<select id="et-category">
<option value="Food">Food</option>
<option value="Transport">Transport</option>
<option value="Housing">Housing</option>
<option value="Entertainment">Entertainment</option>
<option value="Health">Health</option>
<option value="Education">Education</option>
<option value="Other">Other</option>
</select>
</div>
<div style="display:flex;align-items:flex-end;">
<button class="et-btn et-btn-primary" onclick="etAddTransaction()" style="width:100%;">Add Transaction</button>
</div>
</div>
</div>

<h2>Monthly Overview</h2>
<div class="et-summary-bar">
<div class="et-summary-card et-income-card">
<div class="et-s-label">Income</div>
<div class="et-s-value" id="et-total-income">$0.00</div>
</div>
<div class="et-summary-card et-expense-card">
<div class="et-s-label">Expenses</div>
<div class="et-s-value" id="et-total-expense">$0.00</div>
</div>
<div class="et-summary-card et-balance-card" id="et-balance-card">
<div class="et-s-label">Balance</div>
<div class="et-s-value" id="et-balance">$0.00</div>
</div>
</div>

<div class="et-card" id="et-chart-section" style="display:none;">
<div class="et-chart-wrap">
<canvas id="et-donut" width="160" height="160"></canvas>
<div class="et-legend" id="et-legend"></div>
</div>
<div style="margin-top:18px;" id="et-cat-breakdown"></div>
</div>

<h2>Transactions</h2>
<div class="et-filter-row">
<div>
<label>Month</label>
<input type="month" id="et-filter-month">
</div>
<div>
<label>Category</label>
<select id="et-filter-cat">
<option value="">All Categories</option>
<option value="Food">Food</option>
<option value="Transport">Transport</option>
<option value="Housing">Housing</option>
<option value="Entertainment">Entertainment</option>
<option value="Health">Health</option>
<option value="Education">Education</option>
<option value="Other">Other</option>
</select>
</div>
<div>
<label>Type</label>
<select id="et-filter-type">
<option value="">All</option>
<option value="income">Income</option>
<option value="expense">Expense</option>
</select>
</div>
<div style="display:flex;align-items:flex-end;gap:8px;">
<button class="et-btn et-btn-sm et-btn-export" onclick="etExportCSV()">Export CSV</button>
</div>
</div>

<div class="et-table-wrap et-card" style="padding:0;overflow:hidden;">
<table>
<thead>
<tr>
<th>Date</th>
<th>Description</th>
<th>Category</th>
<th>Type</th>
<th style="text-align:right;">Amount</th>
<th></th>
</tr>
</thead>
<tbody id="et-tbody"></tbody>
</table>
</div>

<!-- Edit Modal -->
<div class="et-modal-overlay" id="et-modal">
<div class="et-modal">
<h3>Edit Transaction</h3>
<div class="et-grid et-grid-2" style="margin-bottom:12px;">
<div>
<label>Date</label>
<input type="date" id="et-edit-date">
</div>
<div>
<label>Type</label>
<div class="et-type-toggle">
<button id="et-edit-btn-income" class="active-income" onclick="etEditSetType('income')">+ Income</button>
<button id="et-edit-btn-expense" onclick="etEditSetType('expense')">- Expense</button>
</div>
</div>
</div>
<div class="et-grid et-grid-2" style="margin-bottom:12px;">
<div style="grid-column:span 2;">
<label>Description</label>
<input type="text" id="et-edit-desc">
</div>
</div>
<div class="et-grid et-grid-2" style="margin-bottom:12px;">
<div>
<label>Amount ($)</label>
<input type="number" id="et-edit-amount" min="0" step="0.01">
</div>
<div>
<label>Category</label>
<select id="et-edit-category">
<option value="Food">Food</option>
<option value="Transport">Transport</option>
<option value="Housing">Housing</option>
<option value="Entertainment">Entertainment</option>
<option value="Health">Health</option>
<option value="Education">Education</option>
<option value="Other">Other</option>
</select>
</div>
</div>
<div class="et-modal-actions">
<button class="et-btn et-btn-sm et-btn-secondary" onclick="etCloseModal()">Cancel</button>
<button class="et-btn et-btn-sm et-btn-primary" onclick="etSaveEdit()">Save Changes</button>
</div>
</div>
</div>

<script>
(function () {
'use strict';

var STORAGE_KEY = 'et_transactions_v1';
var COLORS = {
Food:          '#f97316',
Transport:     '#3b82f6',
Housing:       '#8b5cf6',
Entertainment: '#ec4899',
Health:        '#10b981',
Education:     '#f59e0b',
Other:         '#94a3b8'
};

var transactions = [];
var currentType = 'expense';
var editId = null;
var editType = 'expense';

// Init
(function init() {
var stored = localStorage.getItem(STORAGE_KEY);
if (stored) {
try { transactions = JSON.parse(stored); } catch (e) { transactions = []; }
}
// Default date to today
var today = new Date().toISOString().slice(0, 10);
document.getElementById('et-date').value = today;
// Default filter to current month
document.getElementById('et-filter-month').value = today.slice(0, 7);

// Listeners
document.getElementById('et-filter-month').addEventListener('change', etRender);
document.getElementById('et-filter-cat').addEventListener('change', etRender);
document.getElementById('et-filter-type').addEventListener('change', etRender);

etRender();
})();

function etSave() {
localStorage.setItem(STORAGE_KEY, JSON.stringify(transactions));
}

function etSetType(type) {
currentType = type;
document.getElementById('et-btn-income').className = type === 'income' ? 'active-income' : '';
document.getElementById('et-btn-expense').className = type === 'expense' ? 'active-expense' : '';
}

function etEditSetType(type) {
editType = type;
document.getElementById('et-edit-btn-income').className = type === 'income' ? 'active-income' : '';
document.getElementById('et-edit-btn-expense').className = type === 'expense' ? 'active-expense' : '';
}

function etAddTransaction() {
var date = document.getElementById('et-date').value;
var desc = document.getElementById('et-desc').value.trim();
var amount = parseFloat(document.getElementById('et-amount').value);
var category = document.getElementById('et-category').value;

if (!date) { alert('Please select a date.'); return; }
if (!desc) { alert('Please enter a description.'); return; }
if (isNaN(amount) || amount <= 0) { alert('Please enter a valid amount greater than 0.'); return; }

transactions.push({
id: Date.now() + Math.random(),
date: date,
desc: desc,
amount: amount,
category: category,
type: currentType
});

etSave();

// Reset form
document.getElementById('et-desc').value = '';
document.getElementById('et-amount').value = '';

etRender();
}

function etDeleteTransaction(id) {
transactions = transactions.filter(function (t) { return t.id !== id; });
etSave();
etRender();
}

function etOpenEdit(id) {
var t = transactions.find(function (x) { return x.id === id; });
if (!t) return;
editId = id;
document.getElementById('et-edit-date').value = t.date;
document.getElementById('et-edit-desc').value = t.desc;
document.getElementById('et-edit-amount').value = t.amount;
document.getElementById('et-edit-category').value = t.category;
etEditSetType(t.type);
document.getElementById('et-modal').classList.add('open');
}

function etCloseModal() {
document.getElementById('et-modal').classList.remove('open');
editId = null;
}

function etSaveEdit() {
if (editId === null) return;
var date = document.getElementById('et-edit-date').value;
var desc = document.getElementById('et-edit-desc').value.trim();
var amount = parseFloat(document.getElementById('et-edit-amount').value);
var category = document.getElementById('et-edit-category').value;

if (!date || !desc || isNaN(amount) || amount <= 0) { alert('Please fill in all fields correctly.'); return; }

transactions = transactions.map(function (t) {
if (t.id === editId) {
return { id: t.id, date: date, desc: desc, amount: amount, category: category, type: editType };
}
return t;
});
etSave();
etCloseModal();
etRender();
}

function etGetFiltered() {
var month = document.getElementById('et-filter-month').value;
var cat = document.getElementById('et-filter-cat').value;
var type = document.getElementById('et-filter-type').value;

return transactions.filter(function (t) {
if (month && t.date.slice(0, 7) !== month) return false;
if (cat && t.category !== cat) return false;
if (type && t.type !== type) return false;
return true;
}).sort(function (a, b) { return b.date.localeCompare(a.date); });
}

function fmt(n) {
return '$' + n.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}

function etRender() {
var filtered = etGetFiltered();

// Summary (based on filtered month, all types/cats)
var month = document.getElementById('et-filter-month').value;
var monthTxns = month
? transactions.filter(function (t) { return t.date.slice(0, 7) === month; })
: transactions;

var totalIncome = monthTxns.filter(function (t) { return t.type === 'income'; })
.reduce(function (s, t) { return s + t.amount; }, 0);
var totalExpense = monthTxns.filter(function (t) { return t.type === 'expense'; })
.reduce(function (s, t) { return s + t.amount; }, 0);
var balance = totalIncome - totalExpense;

document.getElementById('et-total-income').textContent = fmt(totalIncome);
document.getElementById('et-total-expense').textContent = fmt(totalExpense);
document.getElementById('et-balance').textContent = fmt(balance);

var balCard = document.getElementById('et-balance-card');
balCard.className = 'et-summary-card ' + (balance < 0 ? 'et-balance-neg' : 'et-balance-card');

// Chart & breakdown (expenses by category in current month filter)
var expenseTxns = monthTxns.filter(function (t) { return t.type === 'expense'; });
etRenderChart(expenseTxns);

// Table
var tbody = document.getElementById('et-tbody');
if (filtered.length === 0) {
tbody.innerHTML = '<tr><td colspan="6" class="et-empty">No transactions found. Add one above!</td></tr>';
return;
}

var html = '';
filtered.forEach(function (t) {
html += '<tr>';
html += '<td>' + t.date + '</td>';
html += '<td>' + escHtml(t.desc) + '</td>';
html += '<td><span class="et-badge" style="background:' + hexBg(COLORS[t.category] || '#94a3b8') + ';color:' + (COLORS[t.category] || '#94a3b8') + ';">' + t.category + '</span></td>';
html += '<td><span class="et-badge ' + (t.type === 'income' ? 'et-badge-income' : 'et-badge-expense') + '">' + (t.type === 'income' ? 'Income' : 'Expense') + '</span></td>';
html += '<td style="text-align:right;" class="' + (t.type === 'income' ? 'et-amount-income' : 'et-amount-expense') + '">' + (t.type === 'income' ? '+' : '-') + fmt(t.amount) + '</td>';
html += '<td style="white-space:nowrap;text-align:right;">';
html += '<button class="et-btn et-btn-sm et-btn-edit" onclick="etOpenEdit(' + t.id + ')" style="margin-right:4px;">Edit</button>';
html += '<button class="et-btn et-btn-sm et-btn-delete" onclick="etDeleteTransaction(' + t.id + ')">Delete</button>';
html += '</td>';
html += '</tr>';
});
tbody.innerHTML = html;
}

function hexBg(hex) {
// Return light version of color for badge background
var map = {
'#f97316': '#fff7ed',
'#3b82f6': '#eff6ff',
'#8b5cf6': '#f5f3ff',
'#ec4899': '#fdf2f8',
'#10b981': '#ecfdf5',
'#f59e0b': '#fffbeb',
'#94a3b8': '#f1f5f9'
};
return map[hex] || '#f1f5f9';
}

function etRenderChart(expenseTxns) {
var section = document.getElementById('et-chart-section');
if (expenseTxns.length === 0) { section.style.display = 'none'; return; }
section.style.display = '';

// Aggregate by category
var catMap = {};
expenseTxns.forEach(function (t) {
catMap[t.category] = (catMap[t.category] || 0) + t.amount;
});
var total = Object.values(catMap).reduce(function (s, v) { return s + v; }, 0);
var entries = Object.entries(catMap).sort(function (a, b) { return b[1] - a[1]; });

// Draw donut
var canvas = document.getElementById('et-donut');
var ctx = canvas.getContext('2d');
var cx = 80, cy = 80, r = 68, innerR = 44;
ctx.clearRect(0, 0, 160, 160);

var startAngle = -Math.PI / 2;
entries.forEach(function (entry) {
var slice = (entry[1] / total) * 2 * Math.PI;
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, startAngle, startAngle + slice);
ctx.closePath();
ctx.fillStyle = COLORS[entry[0]] || '#94a3b8';
ctx.fill();
startAngle += slice;
});

// Inner circle (hole)
ctx.beginPath();
ctx.arc(cx, cy, innerR, 0, 2 * Math.PI);
ctx.fillStyle = '#fff';
ctx.fill();

// Center text
ctx.fillStyle = '#1e293b';
ctx.font = 'bold 13px system-ui';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
ctx.fillText(fmt(total), cx, cy);

// Legend
var legendHtml = '';
entries.forEach(function (entry) {
var pct = ((entry[1] / total) * 100).toFixed(1);
legendHtml += '<div class="et-legend-item">';
legendHtml += '<div class="et-legend-dot" style="background:' + (COLORS[entry[0]] || '#94a3b8') + ';"></div>';
legendHtml += '<span class="et-legend-label">' + entry[0] + ' <span style="color:#94a3b8;font-size:11px;">(' + pct + '%)</span></span>';
legendHtml += '<span class="et-legend-val">' + fmt(entry[1]) + '</span>';
legendHtml += '</div>';
});
document.getElementById('et-legend').innerHTML = legendHtml;

// Category bar breakdown
var breakHtml = '<div style="font-size:12px;font-weight:700;text-transform:uppercase;letter-spacing:0.04em;color:#64748b;margin-bottom:10px;">Breakdown by Category</div>';
entries.forEach(function (entry) {
var pct = (entry[1] / total) * 100;
breakHtml += '<div class="et-cat-row">';
breakHtml += '<span class="et-cat-name">' + entry[0] + '</span>';
breakHtml += '<div class="et-cat-bar-bg"><div class="et-cat-bar-fill" style="width:' + pct.toFixed(1) + '%;background:' + (COLORS[entry[0]] || '#94a3b8') + ';"></div></div>';
breakHtml += '<span class="et-cat-amt">' + fmt(entry[1]) + '</span>';
breakHtml += '</div>';
});
document.getElementById('et-cat-breakdown').innerHTML = breakHtml;
}

function etExportCSV() {
var filtered = etGetFiltered();
if (filtered.length === 0) { alert('No transactions to export.'); return; }
var rows = [['Date', 'Description', 'Category', 'Type', 'Amount']];
filtered.forEach(function (t) {
rows.push([t.date, '"' + t.desc.replace(/"/g, '""') + '"', t.category, t.type, t.amount.toFixed(2)]);
});
var csv = rows.map(function (r) { return r.join(','); }).join('\n');
var blob = new Blob([csv], { type: 'text/csv' });
var url = URL.createObjectURL(blob);
var a = document.createElement('a');
a.href = url;
a.download = 'expenses.csv';
a.click();
URL.revokeObjectURL(url);
}

function escHtml(str) {
return String(str)
.replace(/&/g, '&amp;')
.replace(/</g, '&lt;')
.replace(/>/g, '&gt;')
.replace(/"/g, '&quot;');
}

// Expose to global scope for inline onclick handlers
window.etSetType = etSetType;
window.etEditSetType = etEditSetType;
window.etAddTransaction = etAddTransaction;
window.etDeleteTransaction = etDeleteTransaction;
window.etOpenEdit = etOpenEdit;
window.etCloseModal = etCloseModal;
window.etSaveEdit = etSaveEdit;
window.etExportCSV = etExportCSV;
})();
</script>

</div>

---

## Related Tools

- [Budget Planner](/tools/budget-planner/) — Plan your monthly budget with the 50/30/20 rule
- [Split Bill Calculator](/tools/split-bill-calculator/) — Split costs fairly among a group

## Related Articles

- [7 Best Budgeting Apps in 2026 (Free & Paid Compared)](/posts/best-budgeting-apps-2026/)
- [Best Budgeting Apps 2026: Full Comparison](/posts/best-budgeting-apps-2026-comparison/)
- [10 Ways ChatGPT Can Save You $500/Month](/posts/chatgpt-save-money/)
