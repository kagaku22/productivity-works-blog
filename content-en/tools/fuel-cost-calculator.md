---
title: "Fuel Cost Calculator"
date: 2025-05-16
description: "Free fuel cost calculator. Calculate trip fuel costs based on distance, fuel efficiency, and gas price. Compare vehicles, estimate annual fuel expenses."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "fuel-cost-calculator"
ShowToc: false
cover:
  image: "/images/covers/fuel-cost-calculator.png"
  alt: "Fuel Cost Calculator"
---

<div id="fc-app">
<style>
#fc-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #e2e8f0;
}
#fc-app * { box-sizing: border-box; }

#fc-app h2 {
font-size: 1.2rem;
font-weight: 700;
color: #f1f5f9;
margin: 0 0 1rem 0;
padding-bottom: 0.5rem;
border-bottom: 2px solid #334155;
}
#fc-app h3 {
font-size: 0.95rem;
font-weight: 600;
color: #cbd5e1;
margin: 0 0 0.75rem 0;
}

/* Tabs */
#fc-app .fc-tabs {
display: flex;
gap: 0.5rem;
margin-bottom: 1.5rem;
flex-wrap: wrap;
}
#fc-app .fc-tab {
padding: 0.5rem 1.25rem;
border-radius: 6px;
border: 1px solid #334155;
background: #1e293b;
color: #94a3b8;
cursor: pointer;
font-size: 0.875rem;
font-weight: 500;
transition: all 0.15s ease;
}
#fc-app .fc-tab:hover { border-color: #475569; color: #cbd5e1; }
#fc-app .fc-tab.active { background: #10b981; border-color: #10b981; color: #fff; }

/* Panels */
#fc-app .fc-panel { display: none; }
#fc-app .fc-panel.active { display: block; }

/* Card */
#fc-app .fc-card {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 1.25rem;
margin-bottom: 1rem;
}

/* Grid */
#fc-app .fc-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 1rem;
margin-bottom: 1rem;
}
#fc-app .fc-field { display: flex; flex-direction: column; gap: 0.3rem; }
#fc-app .fc-field label {
font-size: 0.75rem;
font-weight: 600;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#fc-app .fc-field input,
#fc-app .fc-field select {
padding: 0.55rem 0.75rem;
background: #0f172a;
border: 1.5px solid #334155;
border-radius: 7px;
color: #e2e8f0;
font-size: 0.9rem;
outline: none;
width: 100%;
transition: border-color 0.15s;
}
#fc-app .fc-field input:focus,
#fc-app .fc-field select:focus { border-color: #10b981; }

/* Toggle row */
#fc-app .fc-toggles {
display: flex;
flex-wrap: wrap;
gap: 0.75rem;
margin-bottom: 1rem;
align-items: center;
}
#fc-app .fc-toggle-label {
display: flex;
align-items: center;
gap: 0.4rem;
cursor: pointer;
color: #cbd5e1;
font-size: 0.875rem;
user-select: none;
}
#fc-app .fc-toggle-label input[type="checkbox"] {
width: 1rem;
height: 1rem;
accent-color: #10b981;
cursor: pointer;
}

/* Button */
#fc-app .fc-btn {
padding: 0.6rem 1.4rem;
border: none;
border-radius: 7px;
background: #10b981;
color: #fff;
font-size: 0.9rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
}
#fc-app .fc-btn:hover { background: #059669; }
#fc-app .fc-btn-outline {
background: transparent;
border: 1.5px solid #10b981;
color: #10b981;
}
#fc-app .fc-btn-outline:hover { background: #10b981; color: #fff; }

/* Results bar */
#fc-app .fc-result-bar {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
gap: 0.75rem;
background: #0f172a;
border: 1px solid #1e3a5f;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-top: 1rem;
}
#fc-app .fc-result-item { text-align: center; }
#fc-app .fc-result-val {
font-size: 1.5rem;
font-weight: 800;
color: #10b981;
line-height: 1.2;
}
#fc-app .fc-result-lbl {
font-size: 0.72rem;
color: #64748b;
margin-top: 0.2rem;
text-transform: uppercase;
letter-spacing: 0.03em;
}

/* Compare card */
#fc-app .fc-compare-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
margin-bottom: 1rem;
}
@media (max-width: 540px) {
#fc-app .fc-compare-grid { grid-template-columns: 1fr; }
}
#fc-app .fc-vehicle-card {
background: #0f172a;
border: 1.5px solid #334155;
border-radius: 8px;
padding: 1rem;
}
#fc-app .fc-vehicle-card h3 {
font-size: 0.85rem;
color: #10b981;
margin: 0 0 0.75rem 0;
}
#fc-app .fc-vehicle-card .fc-field { margin-bottom: 0.6rem; }

/* Compare results table */
#fc-app .fc-cmp-table { width: 100%; border-collapse: collapse; font-size: 0.875rem; }
#fc-app .fc-cmp-table th {
background: #1e293b;
color: #94a3b8;
padding: 0.5rem 0.75rem;
text-align: left;
font-weight: 600;
font-size: 0.75rem;
text-transform: uppercase;
letter-spacing: 0.03em;
}
#fc-app .fc-cmp-table td {
padding: 0.5rem 0.75rem;
border-bottom: 1px solid #1e293b;
color: #e2e8f0;
}
#fc-app .fc-cmp-table tr:last-child td { border-bottom: none; }
#fc-app .fc-cmp-table .winner { color: #10b981; font-weight: 700; }
#fc-app .fc-cmp-table .loser  { color: #94a3b8; }

/* Annual panel */
#fc-app .fc-annual-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
gap: 0.75rem;
margin-bottom: 1rem;
}
#fc-app .fc-annual-stat {
background: #0f172a;
border: 1px solid #1e3a5f;
border-radius: 8px;
padding: 0.85rem 1rem;
text-align: center;
}
#fc-app .fc-annual-stat .val { font-size: 1.3rem; font-weight: 800; color: #10b981; }
#fc-app .fc-annual-stat .lbl { font-size: 0.72rem; color: #64748b; margin-top: 0.2rem; text-transform: uppercase; }

/* Chart */
#fc-app .fc-chart-wrap { position: relative; width: 100%; }
#fc-app canvas { display: block; width: 100%; border-radius: 6px; }

/* Cross-links */
#fc-app .fc-crosslinks {
margin-top: 1.5rem;
padding: 1rem 1.25rem;
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
display: flex;
flex-direction: column;
gap: 0.5rem;
}
#fc-app .fc-crosslinks a { color: #38bdf8; text-decoration: none; }
#fc-app .fc-crosslinks a:hover { text-decoration: underline; }
#fc-app .fc-crosslinks span { color: #475569; margin-right: 0.4rem; }
#fc-app .fc-crosslinks div { font-size: 0.875rem; color: #cbd5e1; }

/* Tip */
#fc-app .fc-tip {
background: #0f2a1f;
border-left: 3px solid #10b981;
border-radius: 0 6px 6px 0;
padding: 0.65rem 1rem;
font-size: 0.8rem;
color: #6ee7b7;
margin-top: 0.75rem;
}
</style>

<!-- TABS -->
<div class="fc-tabs">
<button class="fc-tab active" onclick="fcSwitchTab('trip')">Trip Calculator</button>
<button class="fc-tab" onclick="fcSwitchTab('compare')">Compare Vehicles</button>
<button class="fc-tab" onclick="fcSwitchTab('annual')">Annual Estimator</button>
</div>

<!-- ==============================
PANEL: TRIP
============================== -->
<div id="fc-panel-trip" class="fc-panel active">
<div class="fc-card">
<h2>Trip Fuel Cost</h2>

<!-- Unit toggle -->
<div class="fc-toggles">
<label class="fc-toggle-label">
<input type="checkbox" id="fc-imperial" onchange="fcCalcTrip()"> Imperial (miles / MPG / gallon)
</label>
<label class="fc-toggle-label">
<input type="checkbox" id="fc-roundtrip" onchange="fcCalcTrip()"> Round Trip
</label>
</div>

<div class="fc-grid">
<div class="fc-field">
<label id="fc-dist-lbl">Distance (km)</label>
<input type="number" id="fc-distance" value="100" min="0" step="1" oninput="fcCalcTrip()">
</div>
<div class="fc-field">
<label id="fc-eff-lbl">Fuel Efficiency (L/100km)</label>
<select id="fc-eff-mode" onchange="fcCalcTrip()">
<option value="l100km">L / 100 km</option>
<option value="kml">km / L</option>
<option value="mpg">MPG</option>
</select>
</div>
<div class="fc-field">
<label id="fc-eff-val-lbl">Efficiency Value</label>
<input type="number" id="fc-efficiency" value="8" min="0.1" step="0.1" oninput="fcCalcTrip()">
</div>
<div class="fc-field">
<label id="fc-price-lbl">Fuel Price (per liter)</label>
<input type="number" id="fc-price" value="1.60" min="0.01" step="0.01" oninput="fcCalcTrip()">
</div>
</div>

<button class="fc-btn" onclick="fcCalcTrip()">Calculate</button>

<div class="fc-result-bar" id="fc-trip-results">
<div class="fc-result-item">
<div class="fc-result-val" id="fc-r-fuel">—</div>
<div class="fc-result-lbl">Fuel Needed</div>
</div>
<div class="fc-result-item">
<div class="fc-result-val" id="fc-r-cost">—</div>
<div class="fc-result-lbl">Total Cost</div>
</div>
<div class="fc-result-item">
<div class="fc-result-val" id="fc-r-dist">—</div>
<div class="fc-result-lbl">Distance</div>
</div>
<div class="fc-result-item">
<div class="fc-result-val" id="fc-r-perkm">—</div>
<div class="fc-result-lbl" id="fc-r-perkm-lbl">Cost / km</div>
</div>
</div>

<div class="fc-tip" id="fc-trip-tip"></div>
</div>
</div>

<!-- ==============================
PANEL: COMPARE
============================== -->
<div id="fc-panel-compare" class="fc-panel">
<div class="fc-card">
<h2>Compare Two Vehicles</h2>

<div class="fc-grid" style="margin-bottom:1rem;">
<div class="fc-field">
<label>Distance (km)</label>
<input type="number" id="fc-cmp-dist" value="200" min="1" step="1" oninput="fcCalcCompare()">
</div>
<div class="fc-field">
<label>Fuel Price (per liter)</label>
<input type="number" id="fc-cmp-price" value="1.60" min="0.01" step="0.01" oninput="fcCalcCompare()">
</div>
</div>

<div class="fc-compare-grid">
<div class="fc-vehicle-card">
<h3>Vehicle A</h3>
<div class="fc-field">
<label>Name</label>
<input type="text" id="fc-va-name" value="Current Car" oninput="fcCalcCompare()">
</div>
<div class="fc-field">
<label>Fuel Mode</label>
<select id="fc-va-mode" onchange="fcCalcCompare()">
<option value="l100km">L / 100 km</option>
<option value="kml">km / L</option>
<option value="mpg">MPG</option>
</select>
</div>
<div class="fc-field">
<label>Efficiency Value</label>
<input type="number" id="fc-va-eff" value="9" min="0.1" step="0.1" oninput="fcCalcCompare()">
</div>
</div>

<div class="fc-vehicle-card">
<h3>Vehicle B</h3>
<div class="fc-field">
<label>Name</label>
<input type="text" id="fc-vb-name" value="New Car" oninput="fcCalcCompare()">
</div>
<div class="fc-field">
<label>Fuel Mode</label>
<select id="fc-vb-mode" onchange="fcCalcCompare()">
<option value="l100km">L / 100 km</option>
<option value="kml">km / L</option>
<option value="mpg">MPG</option>
</select>
</div>
<div class="fc-field">
<label>Efficiency Value</label>
<input type="number" id="fc-vb-eff" value="6" min="0.1" step="0.1" oninput="fcCalcCompare()">
</div>
</div>
</div>

<div id="fc-cmp-output">
<table class="fc-cmp-table" id="fc-cmp-table">
<thead>
<tr>
<th>Metric</th>
<th id="fc-cmp-th-a">Vehicle A</th>
<th id="fc-cmp-th-b">Vehicle B</th>
</tr>
</thead>
<tbody id="fc-cmp-tbody"></tbody>
</table>
</div>

<div class="fc-chart-wrap" style="margin-top:1rem;">
<canvas id="fc-cmp-chart" height="240"></canvas>
</div>
</div>
</div>

<!-- ==============================
PANEL: ANNUAL
============================== -->
<div id="fc-panel-annual" class="fc-panel">
<div class="fc-card">
<h2>Annual Fuel Cost Estimator</h2>

<div class="fc-grid">
<div class="fc-field">
<label>Daily Commute (km one-way)</label>
<input type="number" id="fc-ann-commute" value="25" min="0" step="1" oninput="fcCalcAnnual()">
</div>
<div class="fc-field">
<label>Work Days / Week</label>
<input type="number" id="fc-ann-workdays" value="5" min="1" max="7" step="1" oninput="fcCalcAnnual()">
</div>
<div class="fc-field">
<label>Fuel Mode</label>
<select id="fc-ann-mode" onchange="fcCalcAnnual()">
<option value="l100km">L / 100 km</option>
<option value="kml">km / L</option>
<option value="mpg">MPG</option>
</select>
</div>
<div class="fc-field">
<label>Efficiency Value</label>
<input type="number" id="fc-ann-eff" value="8" min="0.1" step="0.1" oninput="fcCalcAnnual()">
</div>
<div class="fc-field">
<label>Fuel Price (per liter)</label>
<input type="number" id="fc-ann-price" value="1.60" min="0.01" step="0.01" oninput="fcCalcAnnual()">
</div>
<div class="fc-field">
<label>Extra km / week (errands, etc.)</label>
<input type="number" id="fc-ann-extra" value="50" min="0" step="10" oninput="fcCalcAnnual()">
</div>
</div>

<div class="fc-annual-grid" id="fc-ann-stats">
<div class="fc-annual-stat"><div class="val" id="fc-an-weekly">—</div><div class="lbl">Weekly</div></div>
<div class="fc-annual-stat"><div class="val" id="fc-an-monthly">—</div><div class="lbl">Monthly</div></div>
<div class="fc-annual-stat"><div class="val" id="fc-an-yearly">—</div><div class="lbl">Yearly</div></div>
<div class="fc-annual-stat"><div class="val" id="fc-an-liters">—</div><div class="lbl">Liters/Year</div></div>
<div class="fc-annual-stat"><div class="val" id="fc-an-km">—</div><div class="lbl">km/Year</div></div>
<div class="fc-annual-stat"><div class="val" id="fc-an-perday">—</div><div class="lbl">Daily Cost</div></div>
</div>

<div class="fc-chart-wrap">
<canvas id="fc-ann-chart" height="240"></canvas>
</div>
</div>
</div>

<!-- Cross-links -->
<div class="fc-crosslinks">
<div><span>&#8594;</span>Track your monthly spending <a href="/tools/budget-planner/">Budget Planner</a></div>
<div><span>&#8594;</span>Estimate your home electricity costs <a href="/tools/electricity-calculator/">Electricity Cost Calculator</a></div>
</div>

</div><!-- /#fc-app -->

<script>
(function () {
'use strict';

/* ── helpers ── */
function num(id) {
var v = parseFloat(document.getElementById(id).value);
return isNaN(v) ? 0 : v;
}
function val(id) { return document.getElementById(id).value; }
function set(id, t) { document.getElementById(id).textContent = t; }
function fmtCurrency(n) { return '$' + n.toFixed(2); }
function fmtLiters(n) { return n.toFixed(1) + ' L'; }
function fmtGal(n) { return n.toFixed(1) + ' gal'; }

/* Convert any efficiency mode to L/100km */
function toLper100km(mode, val) {
if (val <= 0) return 0;
if (mode === 'l100km') return val;
if (mode === 'kml') return 100 / val;
if (mode === 'mpg') return 235.214 / val;
return val;
}

/* Fuel needed (liters) for distance (km) given L/100km */
function fuelLiters(distKm, lPer100) {
if (lPer100 <= 0) return 0;
return distKm * lPer100 / 100;
}

/* ── TAB SWITCHER ── */
window.fcSwitchTab = function (name) {
document.querySelectorAll('#fc-app .fc-tab').forEach(function (b) { b.classList.remove('active'); });
document.querySelectorAll('#fc-app .fc-panel').forEach(function (p) { p.classList.remove('active'); });
var btn = document.querySelector('#fc-app .fc-tab[onclick*="' + name + '"]');
if (btn) btn.classList.add('active');
var panel = document.getElementById('fc-panel-' + name);
if (panel) panel.classList.add('active');
if (name === 'compare') { fcCalcCompare(); }
if (name === 'annual')  { fcCalcAnnual();  }
};

/* ── TRIP CALCULATOR ── */
window.fcCalcTrip = function () {
var imperial = document.getElementById('fc-imperial').checked;
var roundtrip = document.getElementById('fc-roundtrip').checked;
var mode = val('fc-eff-mode');

/* update labels */
document.getElementById('fc-dist-lbl').textContent = imperial ? 'Distance (miles)' : 'Distance (km)';
var modeLabels = {
'l100km': 'L / 100 km',
'kml': 'km / L',
'mpg': 'MPG'
};
document.getElementById('fc-eff-lbl').textContent = 'Fuel Efficiency (' + modeLabels[mode] + ')';
document.getElementById('fc-price-lbl').textContent = imperial ? 'Fuel Price (per gallon)' : 'Fuel Price (per liter)';

var rawDist = num('fc-distance');
var effVal  = num('fc-efficiency');
var price   = num('fc-price');

/* normalize to metric */
var distKm = imperial ? rawDist * 1.60934 : rawDist;
if (roundtrip) distKm *= 2;

/* if imperial override mode to mpg */
var calcMode = (imperial && mode !== 'mpg') ? 'mpg' : mode;
var lPer100 = toLper100km(calcMode, effVal);
var liters  = fuelLiters(distKm, lPer100);

/* cost */
var cost;
if (imperial) {
var gallons = liters * 0.264172;
cost = gallons * price;
set('fc-r-fuel', fmtGal(gallons));
set('fc-r-perkm-lbl', 'Cost / mile');
var displayDist = rawDist * (roundtrip ? 2 : 1);
set('fc-r-dist', displayDist.toFixed(0) + ' mi');
set('fc-r-perkm', displayDist > 0 ? fmtCurrency(cost / displayDist) : '—');
} else {
cost = liters * price;
set('fc-r-fuel', fmtLiters(liters));
set('fc-r-perkm-lbl', 'Cost / km');
var displayDistKm = rawDist * (roundtrip ? 2 : 1);
set('fc-r-dist', displayDistKm.toFixed(0) + ' km');
set('fc-r-perkm', displayDistKm > 0 ? fmtCurrency(cost / displayDistKm) : '—');
}

set('fc-r-cost', fmtCurrency(cost));

/* tip */
var tip = '';
if (lPer100 > 12) tip = 'Your vehicle uses over 12 L/100km — consider smooth acceleration and proper tire pressure to improve fuel economy.';
else if (lPer100 < 5) tip = 'Great fuel efficiency! Maintaining regular oil changes and clean air filters helps sustain this performance.';
else tip = 'Tip: reducing highway speed from 120 km/h to 100 km/h can cut fuel use by up to 20%.';
document.getElementById('fc-trip-tip').textContent = tip;
};

/* ── COMPARE VEHICLES ── */
window.fcCalcCompare = function () {
var dist  = num('fc-cmp-dist');
var price = num('fc-cmp-price');
var aName = document.getElementById('fc-va-name').value || 'Vehicle A';
var bName = document.getElementById('fc-vb-name').value || 'Vehicle B';

var aMode = val('fc-va-mode');
var bMode = val('fc-vb-mode');
var aEff  = num('fc-va-eff');
var bEff  = num('fc-vb-eff');

var aL100 = toLper100km(aMode, aEff);
var bL100 = toLper100km(bMode, bEff);

var aFuel = fuelLiters(dist, aL100);
var bFuel = fuelLiters(dist, bL100);
var aCost = aFuel * price;
var bCost = bFuel * price;

var aAnn = aCost * 365;
var bAnn = bCost * 365;
var saving = Math.abs(aAnn - bAnn);
var winner = aCost <= bCost ? 'a' : 'b';

set('fc-cmp-th-a', aName);
set('fc-cmp-th-b', bName);

var rows = [
['L / 100 km', aL100.toFixed(2) + ' L', bL100.toFixed(2) + ' L', aL100 <= bL100 ? 'a' : 'b'],
['Fuel for ' + dist + ' km', fmtLiters(aFuel), fmtLiters(bFuel), aFuel <= bFuel ? 'a' : 'b'],
['Trip Cost', fmtCurrency(aCost), fmtCurrency(bCost), winner],
['Daily Cost (same route)', fmtCurrency(aCost), fmtCurrency(bCost), winner],
['Annual Cost', fmtCurrency(aAnn), fmtCurrency(bAnn), aCost <= bCost ? 'a' : 'b'],
['Annual Saving vs Other', '—', '—', 'none'],
];

if (saving > 0) {
var cheaperName = aCost <= bCost ? aName : bName;
rows[5] = ['Annual Saving', aCost <= bCost ? fmtCurrency(saving) : '—', bCost < aCost ? fmtCurrency(saving) : '—', winner];
}

var tbody = document.getElementById('fc-cmp-tbody');
tbody.innerHTML = '';
rows.forEach(function (r) {
var tr = document.createElement('tr');
var metric = r[0], av = r[1], bv = r[2], w = r[3];
tr.innerHTML =
'<td>' + metric + '</td>' +
'<td class="' + (w === 'a' ? 'winner' : (w === 'none' ? '' : 'loser')) + '">' + av + '</td>' +
'<td class="' + (w === 'b' ? 'winner' : (w === 'none' ? '' : 'loser')) + '">' + bv + '</td>';
tbody.appendChild(tr);
});

/* draw bar chart */
fcDrawCompareChart(aName, bName, aCost, bCost, aFuel, bFuel);
};

function fcDrawCompareChart(aName, bName, aCost, bCost, aFuel, bFuel) {
var canvas = document.getElementById('fc-cmp-chart');
if (!canvas) return;
var W = canvas.offsetWidth || 600;
canvas.width  = W * window.devicePixelRatio;
canvas.height = 240 * window.devicePixelRatio;
canvas.style.height = '240px';
var ctx = canvas.getContext('2d');
ctx.scale(window.devicePixelRatio, window.devicePixelRatio);

var groups = [
{ label: 'Trip Cost ($)', a: aCost, b: bCost },
{ label: 'Fuel (L)',       a: aFuel, b: bFuel },
];

var padL = 50, padR = 20, padT = 20, padB = 50;
var chartW = W - padL - padR;
var chartH = 240 - padT - padB;
var maxVal = Math.max(aCost, bCost, aFuel, bFuel) * 1.2 || 1;

ctx.fillStyle = '#0f172a';
ctx.fillRect(0, 0, W, 240);

/* grid lines */
ctx.strokeStyle = '#1e293b'; ctx.lineWidth = 1;
for (var g = 0; g <= 4; g++) {
var gy = padT + chartH - (g / 4) * chartH;
ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(W - padR, gy); ctx.stroke();
ctx.fillStyle = '#475569'; ctx.font = '10px sans-serif'; ctx.textAlign = 'right';
ctx.fillText((maxVal * g / 4).toFixed(1), padL - 5, gy + 4);
}

/* bars */
var groupW = chartW / groups.length;
var barW = groupW * 0.3;
var colors = { a: '#10b981', b: '#3b82f6' };

groups.forEach(function (grp, gi) {
var gx = padL + gi * groupW;
['a', 'b'].forEach(function (key, ki) {
var v = grp[key];
var bx = gx + ki * (barW + 6) + (groupW - 2 * barW - 6) / 2;
var bh = (v / maxVal) * chartH;
var by = padT + chartH - bh;
ctx.fillStyle = colors[key];
ctx.beginPath();
ctx.roundRect ? ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]) : ctx.rect(bx, by, barW, bh);
ctx.fill();
ctx.fillStyle = '#f1f5f9'; ctx.font = 'bold 10px sans-serif'; ctx.textAlign = 'center';
ctx.fillText(v.toFixed(1), bx + barW / 2, Math.max(by - 4, padT + 12));
});
ctx.fillStyle = '#94a3b8'; ctx.font = '11px sans-serif'; ctx.textAlign = 'center';
ctx.fillText(grp.label, gx + groupW / 2, padT + chartH + 16);
});

/* legend */
var lx = padL;
[{ key: 'a', name: aName }, { key: 'b', name: bName }].forEach(function (item) {
ctx.fillStyle = colors[item.key];
ctx.fillRect(lx, padT + chartH + 28, 10, 10);
ctx.fillStyle = '#cbd5e1'; ctx.font = '11px sans-serif'; ctx.textAlign = 'left';
ctx.fillText(item.name.length > 14 ? item.name.slice(0, 13) + '…' : item.name, lx + 14, padT + chartH + 38);
lx += 160;
});
}

/* ── ANNUAL ESTIMATOR ── */
window.fcCalcAnnual = function () {
var commute  = num('fc-ann-commute');   /* one-way km */
var workdays = Math.min(7, Math.max(1, num('fc-ann-workdays')));
var mode     = val('fc-ann-mode');
var effVal   = num('fc-ann-eff');
var price    = num('fc-ann-price');
var extra    = num('fc-ann-extra');

var lPer100 = toLper100km(mode, effVal);

var dailyCommute = commute * 2; /* round trip */
var weeklyKm  = dailyCommute * workdays + extra;
var yearlyKm  = weeklyKm * 52;
var yearlyL   = fuelLiters(yearlyKm, lPer100);
var yearlyCost = yearlyL * price;
var monthlyCost = yearlyCost / 12;
var weeklyCost  = yearlyCost / 52;
var dailyCost   = yearlyCost / 365;

set('fc-an-weekly',  fmtCurrency(weeklyCost));
set('fc-an-monthly', fmtCurrency(monthlyCost));
set('fc-an-yearly',  fmtCurrency(yearlyCost));
set('fc-an-liters',  yearlyL.toFixed(0) + ' L');
set('fc-an-km',      Math.round(yearlyKm).toLocaleString() + ' km');
set('fc-an-perday',  fmtCurrency(dailyCost));

fcDrawAnnualChart(weeklyCost, monthlyCost, yearlyCost);
};

function fcDrawAnnualChart(weekly, monthly, yearly) {
var canvas = document.getElementById('fc-ann-chart');
if (!canvas) return;
var W = canvas.offsetWidth || 600;
canvas.width  = W * window.devicePixelRatio;
canvas.height = 240 * window.devicePixelRatio;
canvas.style.height = '240px';
var ctx = canvas.getContext('2d');
ctx.scale(window.devicePixelRatio, window.devicePixelRatio);

var labels = ['Weekly', 'Monthly', 'Yearly'];
var values = [weekly, monthly, yearly];
var clrs   = ['#10b981', '#3b82f6', '#f59e0b'];

var padL = 60, padR = 20, padT = 20, padB = 40;
var chartW = W - padL - padR;
var chartH = 240 - padT - padB;
var maxVal = Math.max.apply(null, values) * 1.2 || 1;
var barW = Math.min(80, (chartW / labels.length) * 0.55);
var gap   = chartW / labels.length;

ctx.fillStyle = '#0f172a';
ctx.fillRect(0, 0, W, 240);

/* grid */
ctx.strokeStyle = '#1e293b'; ctx.lineWidth = 1;
for (var g = 0; g <= 4; g++) {
var gy = padT + chartH - (g / 4) * chartH;
ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(W - padR, gy); ctx.stroke();
ctx.fillStyle = '#475569'; ctx.font = '10px sans-serif'; ctx.textAlign = 'right';
ctx.fillText('$' + (maxVal * g / 4).toFixed(0), padL - 5, gy + 4);
}

/* bars */
values.forEach(function (v, i) {
var bx = padL + i * gap + (gap - barW) / 2;
var bh = (v / maxVal) * chartH;
var by = padT + chartH - bh;
ctx.fillStyle = clrs[i];
ctx.beginPath();
ctx.roundRect ? ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]) : ctx.rect(bx, by, barW, bh);
ctx.fill();
ctx.fillStyle = '#f1f5f9'; ctx.font = 'bold 11px sans-serif'; ctx.textAlign = 'center';
ctx.fillText('$' + v.toFixed(0), bx + barW / 2, Math.max(by - 5, padT + 12));
ctx.fillStyle = '#94a3b8'; ctx.font = '12px sans-serif';
ctx.fillText(labels[i], bx + barW / 2, padT + chartH + 18);
});
}

/* ── RESIZE ── */
var resizeTimer;
window.addEventListener('resize', function () {
clearTimeout(resizeTimer);
resizeTimer = setTimeout(function () {
var activePanel = document.querySelector('#fc-app .fc-panel.active');
if (!activePanel) return;
if (activePanel.id === 'fc-panel-compare') fcCalcCompare();
if (activePanel.id === 'fc-panel-annual')  fcCalcAnnual();
}, 150);
});

/* ── INIT ── */
fcCalcTrip();
fcCalcCompare();
fcCalcAnnual();
})();
</script>
</div>

---

## Related Tools

> [Carbon Footprint Calculator](/tools/carbon-footprint-calculator/)
> [Cooking Unit Converter](/tools/cooking-unit-converter/)
> [Electricity Cost Calculator](/tools/electricity-cost-calculator/)

