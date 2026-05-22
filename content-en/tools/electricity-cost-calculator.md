---
title: "Electricity Cost Calculator - Estimate Your Power Bill"
date: 2025-05-16
description: "Free online electricity cost calculator. Add your appliances, set your rate, and instantly see monthly and yearly power bills with a visual cost breakdown chart."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "electricity-cost-calculator"
ShowToc: false
cover:
  image: "/images/covers/electricity-cost-calculator.png"
  alt: "Electricity Cost Calculator"
---

<style>
#ec-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a1a2e;
}
#ec-app * { box-sizing: border-box; }
#ec-app h2 {
font-size: 1.35rem;
font-weight: 700;
margin: 1.5rem 0 0.75rem;
color: #1a1a2e;
}
#ec-app .ec-intro {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: #fff;
border-radius: 12px;
padding: 1.25rem 1.5rem;
margin-bottom: 1.5rem;
font-size: 0.97rem;
line-height: 1.6;
}
#ec-app .ec-rate-row {
display: flex;
align-items: center;
gap: 0.75rem;
background: #f0f4ff;
border: 1.5px solid #c7d2fe;
border-radius: 10px;
padding: 0.85rem 1.1rem;
margin-bottom: 1.25rem;
flex-wrap: wrap;
}
#ec-app .ec-rate-row label {
font-weight: 600;
font-size: 0.95rem;
color: #3730a3;
white-space: nowrap;
}
#ec-app .ec-rate-row input {
width: 110px;
padding: 0.45rem 0.65rem;
border: 1.5px solid #a5b4fc;
border-radius: 7px;
font-size: 1rem;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.2s;
}
#ec-app .ec-rate-row input:focus { border-color: #6366f1; }
#ec-app .ec-rate-row span { font-size: 0.9rem; color: #6366f1; font-weight: 500; }

/* Presets */
#ec-app .ec-presets {
margin-bottom: 1.25rem;
}
#ec-app .ec-presets-title {
font-size: 0.88rem;
font-weight: 600;
color: #6b7280;
margin-bottom: 0.5rem;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#ec-app .ec-preset-grid {
display: flex;
flex-wrap: wrap;
gap: 0.45rem;
}
#ec-app .ec-preset-btn {
background: #fff;
border: 1.5px solid #e0e7ff;
border-radius: 20px;
padding: 0.35rem 0.85rem;
font-size: 0.85rem;
cursor: pointer;
color: #4f46e5;
font-weight: 500;
transition: background 0.15s, border-color 0.15s;
}
#ec-app .ec-preset-btn:hover {
background: #eef2ff;
border-color: #6366f1;
}

/* Add form */
#ec-app .ec-add-form {
background: #f9fafb;
border: 1.5px solid #e5e7eb;
border-radius: 12px;
padding: 1.1rem 1.25rem;
margin-bottom: 1.25rem;
}
#ec-app .ec-add-form .ec-form-grid {
display: grid;
grid-template-columns: 2fr 1fr 1fr 1fr;
gap: 0.6rem;
align-items: end;
}
@media (max-width: 600px) {
#ec-app .ec-add-form .ec-form-grid {
grid-template-columns: 1fr 1fr;
}
}
#ec-app .ec-form-group { display: flex; flex-direction: column; gap: 0.3rem; }
#ec-app .ec-form-group label {
font-size: 0.8rem;
font-weight: 600;
color: #6b7280;
text-transform: uppercase;
letter-spacing: 0.03em;
}
#ec-app .ec-form-group input {
padding: 0.5rem 0.7rem;
border: 1.5px solid #d1d5db;
border-radius: 7px;
font-size: 0.97rem;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.2s;
}
#ec-app .ec-form-group input:focus { border-color: #6366f1; }
#ec-app .ec-add-btn {
background: linear-gradient(135deg, #6366f1, #8b5cf6);
color: #fff;
border: none;
border-radius: 8px;
padding: 0.55rem 1.2rem;
font-size: 0.97rem;
font-weight: 600;
cursor: pointer;
transition: opacity 0.2s;
white-space: nowrap;
margin-top: 0.6rem;
}
#ec-app .ec-add-btn:hover { opacity: 0.88; }

/* Table */
#ec-app .ec-table-wrap {
overflow-x: auto;
border-radius: 10px;
border: 1.5px solid #e5e7eb;
margin-bottom: 1.5rem;
}
#ec-app .ec-table {
width: 100%;
border-collapse: collapse;
font-size: 0.93rem;
}
#ec-app .ec-table th {
background: #f3f4f6;
padding: 0.65rem 0.9rem;
text-align: left;
font-size: 0.8rem;
font-weight: 700;
color: #6b7280;
text-transform: uppercase;
letter-spacing: 0.03em;
white-space: nowrap;
}
#ec-app .ec-table td {
padding: 0.6rem 0.9rem;
border-top: 1px solid #f0f0f0;
vertical-align: middle;
}
#ec-app .ec-table tr:hover td { background: #f9fafb; }
#ec-app .ec-table .ec-color-dot {
display: inline-block;
width: 10px;
height: 10px;
border-radius: 50%;
margin-right: 6px;
vertical-align: middle;
}
#ec-app .ec-del-btn {
background: none;
border: none;
color: #ef4444;
cursor: pointer;
font-size: 1.1rem;
padding: 0.1rem 0.4rem;
border-radius: 5px;
transition: background 0.15s;
}
#ec-app .ec-del-btn:hover { background: #fee2e2; }
#ec-app .ec-empty {
text-align: center;
color: #9ca3af;
padding: 2rem;
font-size: 0.95rem;
}

/* Summary */
#ec-app .ec-summary {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
gap: 1rem;
margin-bottom: 1.5rem;
}
#ec-app .ec-summary-card {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: #fff;
border-radius: 12px;
padding: 1.1rem 1.25rem;
text-align: center;
}
#ec-app .ec-summary-card.green {
background: linear-gradient(135deg, #11998e, #38ef7d);
}
#ec-app .ec-summary-card.orange {
background: linear-gradient(135deg, #f7971e, #ffd200);
color: #1a1a2e;
}
#ec-app .ec-summary-card .ec-card-label {
font-size: 0.82rem;
font-weight: 600;
opacity: 0.85;
margin-bottom: 0.35rem;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#ec-app .ec-summary-card .ec-card-value {
font-size: 1.7rem;
font-weight: 800;
line-height: 1.1;
}
#ec-app .ec-summary-card .ec-card-sub {
font-size: 0.78rem;
opacity: 0.75;
margin-top: 0.2rem;
}

/* Chart */
#ec-app .ec-chart-section {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1.5rem;
align-items: start;
margin-bottom: 1.5rem;
}
@media (max-width: 600px) {
#ec-app .ec-chart-section { grid-template-columns: 1fr; }
}
#ec-app canvas {
display: block;
max-width: 100%;
}
#ec-app .ec-legend { list-style: none; padding: 0; margin: 0; }
#ec-app .ec-legend li {
display: flex;
align-items: center;
gap: 0.5rem;
font-size: 0.9rem;
margin-bottom: 0.45rem;
color: #374151;
}
#ec-app .ec-legend-dot {
width: 12px;
height: 12px;
border-radius: 3px;
flex-shrink: 0;
}
#ec-app .ec-legend-pct {
margin-left: auto;
font-weight: 700;
color: #4f46e5;
}

/* Tips */
#ec-app .ec-tips {
background: #f0fdf4;
border: 1.5px solid #bbf7d0;
border-radius: 12px;
padding: 1.1rem 1.25rem;
margin-bottom: 1.5rem;
}
#ec-app .ec-tips h3 {
margin: 0 0 0.7rem;
font-size: 1rem;
font-weight: 700;
color: #15803d;
}
#ec-app .ec-tips ul {
margin: 0;
padding-left: 1.25rem;
}
#ec-app .ec-tips li {
font-size: 0.92rem;
color: #166534;
margin-bottom: 0.35rem;
line-height: 1.5;
}

/* Related tools */
#ec-app .ec-related {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 1.1rem 1.25rem;
}
#ec-app .ec-related h3 {
margin: 0 0 0.7rem;
font-size: 1rem;
font-weight: 700;
color: #1e293b;
}
#ec-app .ec-related ul {
margin: 0;
padding: 0;
list-style: none;
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
}
#ec-app .ec-related li a {
display: inline-block;
background: #fff;
border: 1.5px solid #cbd5e1;
border-radius: 20px;
padding: 0.35rem 0.85rem;
font-size: 0.88rem;
color: #4f46e5;
text-decoration: none;
font-weight: 500;
transition: border-color 0.15s, background 0.15s;
}
#ec-app .ec-related li a:hover {
border-color: #6366f1;
background: #eef2ff;
}
</style>

<div id="ec-app">

<div class="ec-intro">
Enter your appliances below, set your electricity rate, and instantly see your estimated monthly and yearly power bill — with a visual breakdown by appliance.
</div>

<h2>Electricity Rate</h2>
<div class="ec-rate-row">
<label for="ec-rate">Rate per kWh:</label>
<input type="number" id="ec-rate" value="0.13" min="0.01" step="0.01">
<span>$/kWh &nbsp;(check your utility bill for the exact rate)</span>
</div>

<h2>Add Appliance</h2>
<div class="ec-presets">
<div class="ec-presets-title">Quick presets</div>
<div class="ec-preset-grid" id="ec-preset-grid"></div>
</div>

<div class="ec-add-form">
<div class="ec-form-grid">
<div class="ec-form-group">
<label for="ec-name">Appliance Name</label>
<input type="text" id="ec-name" placeholder="e.g. Living Room TV">
</div>
<div class="ec-form-group">
<label for="ec-watts">Watts (W)</label>
<input type="number" id="ec-watts" placeholder="e.g. 100" min="0" step="1">
</div>
<div class="ec-form-group">
<label for="ec-hours">Hours/Day</label>
<input type="number" id="ec-hours" placeholder="e.g. 4" min="0" max="24" step="0.5">
</div>
<div class="ec-form-group">
<label for="ec-days">Days/Month</label>
<input type="number" id="ec-days" placeholder="e.g. 30" min="1" max="31" step="1" value="30">
</div>
</div>
<button class="ec-add-btn" onclick="ecAddAppliance()">+ Add Appliance</button>
</div>

<h2>Your Appliances</h2>
<div class="ec-table-wrap">
<table class="ec-table">
<thead>
<tr>
<th>Appliance</th>
<th>Watts</th>
<th>Hrs/Day</th>
<th>Days/Mo</th>
<th>kWh/Mo</th>
<th>Cost/Mo</th>
<th>Cost/Yr</th>
<th></th>
</tr>
</thead>
<tbody id="ec-tbody">
<tr><td colspan="8" class="ec-empty">No appliances added yet. Use presets above or enter your own.</td></tr>
</tbody>
</table>
</div>

<div class="ec-summary" id="ec-summary">
<div class="ec-summary-card">
<div class="ec-card-label">Total kWh / Month</div>
<div class="ec-card-value" id="ec-total-kwh">0</div>
<div class="ec-card-sub">kilowatt-hours</div>
</div>
<div class="ec-summary-card green">
<div class="ec-card-label">Monthly Cost</div>
<div class="ec-card-value" id="ec-total-monthly">$0.00</div>
<div class="ec-card-sub">estimated</div>
</div>
<div class="ec-summary-card orange">
<div class="ec-card-label">Yearly Cost</div>
<div class="ec-card-value" id="ec-total-yearly">$0.00</div>
<div class="ec-card-sub">projected annual</div>
</div>
</div>

<h2>Cost Breakdown</h2>
<div class="ec-chart-section">
<canvas id="ec-pie" width="260" height="260"></canvas>
<ul class="ec-legend" id="ec-legend">
<li style="color:#9ca3af">Add appliances to see breakdown</li>
</ul>
</div>

<div class="ec-tips">
<h3>Tips to Reduce Your Electricity Bill</h3>
<ul>
<li><strong>Unplug standby devices</strong> — chargers, TVs on standby, and game consoles can draw 5–20W continuously even when "off".</li>
<li><strong>Switch to LED bulbs</strong> — LED bulbs use up to 80% less energy than incandescent, lasting 15–25x longer.</li>
<li><strong>Use smart power strips</strong> — automatically cut power to devices when the main device (e.g. TV) turns off.</li>
<li><strong>Optimize your air conditioner</strong> — set to 78°F (26°C) in summer; each degree lower adds ~3% to cooling costs.</li>
<li><strong>Run laundry in cold water</strong> — about 90% of a washing machine's energy goes to heating water.</li>
<li><strong>Check your refrigerator seals</strong> — worn gaskets force the compressor to work harder; replace if they fail the "paper test".</li>
<li><strong>Use time-of-use rates</strong> — if your utility offers TOU pricing, run dishwashers and dryers during off-peak hours.</li>
</ul>
</div>

<div class="ec-related">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/hourly-to-salary-calculator/">Hourly Rate Calculator</a></li>
<li><a href="/tools/savings-goal-calculator/">Savings Goal Calculator</a></li>
<li><a href="/tools/pomodoro-timer/">Pomodoro Timer</a></li>
<li><a href="/tools/bmi-calculator/">BMI Calculator</a></li>
<li><a href="/tools/unit-converter/">Unit Converter</a></li>
</ul>
</div>

<script>
(function() {
var COLORS = [
'#6366f1','#8b5cf6','#ec4899','#f59e0b','#10b981',
'#3b82f6','#ef4444','#14b8a6','#f97316','#84cc16',
'#06b6d4','#a855f7','#eab308','#22c55e','#e11d48'
];

var PRESETS = [
{ name: "Refrigerator", watts: 150, hours: 24, days: 30 },
{ name: "Central AC", watts: 3500, hours: 8, days: 22 },
{ name: "Window AC", watts: 900, hours: 8, days: 22 },
{ name: "Electric Heater", watts: 1500, hours: 6, days: 20 },
{ name: "Clothes Dryer", watts: 5000, hours: 0.75, days: 12 },
{ name: "Washing Machine", watts: 500, hours: 0.75, days: 12 },
{ name: "Dishwasher", watts: 1200, hours: 1, days: 15 },
{ name: "TV (50\")", watts: 100, hours: 4, days: 30 },
{ name: "Desktop PC", watts: 200, hours: 8, days: 22 },
{ name: "Laptop", watts: 50, hours: 8, days: 22 },
{ name: "LED Light Bulb", watts: 10, hours: 5, days: 30 },
{ name: "Microwave", watts: 1000, hours: 0.25, days: 30 },
{ name: "Electric Oven", watts: 2400, hours: 1, days: 15 },
{ name: "Water Heater", watts: 4000, hours: 3, days: 30 },
{ name: "EV Charger (L2)", watts: 7200, hours: 2, days: 15 }
];

var appliances = [];

function init() {
var grid = document.getElementById('ec-preset-grid');
PRESETS.forEach(function(p, i) {
var btn = document.createElement('button');
btn.className = 'ec-preset-btn';
btn.textContent = p.name;
btn.onclick = function() { ecFillPreset(p); };
grid.appendChild(btn);
});
render();
}

window.ecFillPreset = function(p) {
document.getElementById('ec-name').value = p.name;
document.getElementById('ec-watts').value = p.watts;
document.getElementById('ec-hours').value = p.hours;
document.getElementById('ec-days').value = p.days;
};

window.ecAddAppliance = function() {
var name = document.getElementById('ec-name').value.trim();
var watts = parseFloat(document.getElementById('ec-watts').value);
var hours = parseFloat(document.getElementById('ec-hours').value);
var days = parseFloat(document.getElementById('ec-days').value);
if (!name) { alert('Please enter an appliance name.'); return; }
if (isNaN(watts) || watts < 0) { alert('Please enter valid wattage.'); return; }
if (isNaN(hours) || hours < 0) { alert('Please enter valid hours/day.'); return; }
if (isNaN(days) || days < 1) { alert('Please enter valid days/month.'); return; }
appliances.push({ name: name, watts: watts, hours: hours, days: days, color: COLORS[appliances.length % COLORS.length] });
document.getElementById('ec-name').value = '';
document.getElementById('ec-watts').value = '';
document.getElementById('ec-hours').value = '';
document.getElementById('ec-days').value = '30';
render();
};

window.ecRemove = function(i) {
appliances.splice(i, 1);
appliances.forEach(function(a, idx) { a.color = COLORS[idx % COLORS.length]; });
render();
};

function getRate() {
return parseFloat(document.getElementById('ec-rate').value) || 0.13;
}

function calcKwh(a) {
return (a.watts / 1000) * a.hours * a.days;
}

function fmt(n) { return '$' + n.toFixed(2); }

function render() {
var rate = getRate();
var tbody = document.getElementById('ec-tbody');

if (appliances.length === 0) {
tbody.innerHTML = '<tr><td colspan="8" class="ec-empty">No appliances added yet. Use presets above or enter your own.</td></tr>';
document.getElementById('ec-total-kwh').textContent = '0';
document.getElementById('ec-total-monthly').textContent = '$0.00';
document.getElementById('ec-total-yearly').textContent = '$0.00';
document.getElementById('ec-legend').innerHTML = '<li style="color:#9ca3af">Add appliances to see breakdown</li>';
drawPie([]);
return;
}

var totalKwh = 0, totalMonth = 0;
var rows = appliances.map(function(a, i) {
var kwh = calcKwh(a);
var costM = kwh * rate;
var costY = costM * 12;
totalKwh += kwh;
totalMonth += costM;
return '<tr>' +
'<td><span class="ec-color-dot" style="background:' + a.color + '"></span>' + escHtml(a.name) + '</td>' +
'<td>' + a.watts + '</td>' +
'<td>' + a.hours + '</td>' +
'<td>' + a.days + '</td>' +
'<td>' + kwh.toFixed(1) + '</td>' +
'<td>' + fmt(costM) + '</td>' +
'<td>' + fmt(costY) + '</td>' +
'<td><button class="ec-del-btn" onclick="ecRemove(' + i + ')" title="Remove">&#10005;</button></td>' +
'</tr>';
});

tbody.innerHTML = rows.join('');
document.getElementById('ec-total-kwh').textContent = totalKwh.toFixed(1);
document.getElementById('ec-total-monthly').textContent = fmt(totalMonth);
document.getElementById('ec-total-yearly').textContent = fmt(totalMonth * 12);

var legend = document.getElementById('ec-legend');
legend.innerHTML = appliances.map(function(a) {
var kwh = calcKwh(a);
var pct = totalKwh > 0 ? (kwh / totalKwh * 100).toFixed(1) : '0.0';
return '<li>' +
'<span class="ec-legend-dot" style="background:' + a.color + '"></span>' +
escHtml(a.name) +
'<span class="ec-legend-pct">' + pct + '%</span>' +
'</li>';
}).join('');

drawPie(appliances.map(function(a) { return { label: a.name, value: calcKwh(a), color: a.color }; }));
}

function drawPie(data) {
var canvas = document.getElementById('ec-pie');
var ctx = canvas.getContext('2d');
var W = canvas.width, H = canvas.height;
ctx.clearRect(0, 0, W, H);

var total = data.reduce(function(s, d) { return s + d.value; }, 0);
if (total === 0 || data.length === 0) {
ctx.beginPath();
ctx.arc(W/2, H/2, W/2 - 10, 0, Math.PI*2);
ctx.fillStyle = '#f3f4f6';
ctx.fill();
ctx.fillStyle = '#9ca3af';
ctx.font = '14px sans-serif';
ctx.textAlign = 'center';
ctx.fillText('No data yet', W/2, H/2 + 5);
return;
}

var startAngle = -Math.PI / 2;
var cx = W/2, cy = H/2, r = W/2 - 10;
data.forEach(function(d) {
var slice = (d.value / total) * Math.PI * 2;
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, startAngle, startAngle + slice);
ctx.closePath();
ctx.fillStyle = d.color;
ctx.fill();
ctx.strokeStyle = '#fff';
ctx.lineWidth = 2;
ctx.stroke();
startAngle += slice;
});

// Center hole
ctx.beginPath();
ctx.arc(cx, cy, r * 0.42, 0, Math.PI*2);
ctx.fillStyle = '#fff';
ctx.fill();
ctx.fillStyle = '#374151';
ctx.font = 'bold 13px sans-serif';
ctx.textAlign = 'center';
ctx.fillText('kWh/Mo', cx, cy - 6);
ctx.font = 'bold 16px sans-serif';
ctx.fillStyle = '#4f46e5';
var totalKwh = data.reduce(function(s,d){return s+d.value;},0);
ctx.fillText(totalKwh.toFixed(1), cx, cy + 14);
}

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

document.getElementById('ec-rate').addEventListener('input', render);

init();
})();
</script>

</div>

---

## Related Tools

> [Carbon Footprint Calculator](/tools/carbon-footprint-calculator/)
> [Cooking Unit Converter](/tools/cooking-unit-converter/)
> [Fuel Cost Calculator](/tools/fuel-cost-calculator/)

