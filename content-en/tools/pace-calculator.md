---
title: "Pace Calculator - Running & Cycling"
date: 2025-05-16
description: "Free pace calculator for runners and cyclists. Calculate pace, speed, distance, or time. Convert between min/km, min/mile, km/h, and mph. Race time predictions included."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: pace-calculator
ShowToc: false
cover:
  image: /images/covers/pace-calculator.png
  alt: "Pace Calculator - Running & Cycling"
---

Enter your distance and time to instantly get your pace, speed, and projected race finish times — or work backwards from a target pace.

<div id="pc-app">
<style>
#pc-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
max-width: 720px;
margin: 0 auto;
color: #1e293b;
font-size: 15px;
line-height: 1.6;
}
#pc-app * {
box-sizing: border-box;
}
#pc-app h2 {
font-size: 1.05rem;
font-weight: 700;
color: #0f172a;
margin: 0 0 1rem;
padding-bottom: 0.4rem;
border-bottom: 2px solid #e2e8f0;
}
#pc-app .pc-card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 1.25rem 1.5rem;
margin-bottom: 1.25rem;
}
#pc-app .pc-tabs {
display: flex;
gap: 0.5rem;
margin-bottom: 1.25rem;
flex-wrap: wrap;
}
#pc-app .pc-tab {
flex: 1;
min-width: 150px;
padding: 0.55rem 0.75rem;
background: #f1f5f9;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
font-size: 0.82rem;
font-weight: 600;
color: #64748b;
cursor: pointer;
text-align: center;
transition: all 0.15s;
}
#pc-app .pc-tab.active {
background: #1e293b;
border-color: #1e293b;
color: #fff;
}
#pc-app .pc-tab:hover:not(.active) {
background: #e2e8f0;
color: #334155;
}
#pc-app .pc-unit-toggle {
display: flex;
align-items: center;
gap: 0.5rem;
margin-bottom: 1.25rem;
font-size: 0.82rem;
font-weight: 600;
color: #64748b;
}
#pc-app .pc-toggle-btn {
display: flex;
background: #f1f5f9;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
overflow: hidden;
font-size: 0.82rem;
}
#pc-app .pc-toggle-btn span {
padding: 0.35rem 0.9rem;
cursor: pointer;
font-weight: 600;
color: #64748b;
transition: all 0.15s;
}
#pc-app .pc-toggle-btn span.active {
background: #1e293b;
color: #fff;
}
#pc-app .pc-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
}
@media (max-width: 520px) {
#pc-app .pc-grid {
grid-template-columns: 1fr;
}
#pc-app .pc-tab {
min-width: 100%;
}
}
#pc-app .pc-field {
display: flex;
flex-direction: column;
gap: 0.3rem;
}
#pc-app .pc-field label {
font-size: 0.78rem;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#pc-app .pc-field input,
#pc-app .pc-field select {
padding: 0.5rem 0.75rem;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 0.95rem;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color 0.15s;
width: 100%;
}
#pc-app .pc-field input:focus,
#pc-app .pc-field select:focus {
border-color: #334155;
}
#pc-app .pc-time-row {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
gap: 0.5rem;
}
#pc-app .pc-time-label {
font-size: 0.7rem;
color: #94a3b8;
text-align: center;
margin-top: 0.15rem;
}
#pc-app .pc-btn {
width: 100%;
padding: 0.75rem;
background: #1e293b;
color: #fff;
border: none;
border-radius: 10px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
margin-top: 1rem;
transition: background 0.15s;
}
#pc-app .pc-btn:hover {
background: #334155;
}
#pc-app .pc-results {
display: none;
}
#pc-app .pc-results.visible {
display: block;
}
#pc-app .pc-result-grid {
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 0.75rem;
margin-bottom: 1rem;
}
@media (max-width: 400px) {
#pc-app .pc-result-grid {
grid-template-columns: 1fr;
}
}
#pc-app .pc-result-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 0.9rem 1rem;
text-align: center;
}
#pc-app .pc-result-box.highlight {
border-color: #334155;
background: #1e293b;
color: #fff;
}
#pc-app .pc-result-label {
font-size: 0.72rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.05em;
color: #94a3b8;
margin-bottom: 0.3rem;
}
#pc-app .pc-result-box.highlight .pc-result-label {
color: #94a3b8;
}
#pc-app .pc-result-val {
font-size: 1.6rem;
font-weight: 800;
line-height: 1.1;
color: #1e293b;
}
#pc-app .pc-result-box.highlight .pc-result-val {
color: #fff;
}
#pc-app .pc-result-unit {
font-size: 0.78rem;
color: #64748b;
margin-top: 0.15rem;
}
#pc-app .pc-result-box.highlight .pc-result-unit {
color: #cbd5e1;
}
#pc-app .pc-race-table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
}
#pc-app .pc-race-table th {
background: #1e293b;
color: #fff;
padding: 0.5rem 0.75rem;
text-align: left;
font-weight: 600;
font-size: 0.78rem;
}
#pc-app .pc-race-table td {
padding: 0.5rem 0.75rem;
border-bottom: 1px solid #f1f5f9;
}
#pc-app .pc-race-table tr:last-child td {
border-bottom: none;
}
#pc-app .pc-race-table tr:nth-child(even) td {
background: #f8fafc;
}
#pc-app .pc-split-table {
width: 100%;
border-collapse: collapse;
font-size: 0.85rem;
}
#pc-app .pc-split-table th {
background: #334155;
color: #fff;
padding: 0.45rem 0.75rem;
text-align: right;
font-weight: 600;
font-size: 0.76rem;
}
#pc-app .pc-split-table th:first-child {
text-align: left;
}
#pc-app .pc-split-table td {
padding: 0.45rem 0.75rem;
border-bottom: 1px solid #f1f5f9;
text-align: right;
}
#pc-app .pc-split-table td:first-child {
text-align: left;
font-weight: 600;
}
#pc-app .pc-split-table tr:nth-child(even) td {
background: #f8fafc;
}
#pc-app .pc-error {
color: #dc2626;
font-size: 0.85rem;
font-weight: 600;
padding: 0.5rem 0.75rem;
background: #fef2f2;
border: 1px solid #fecaca;
border-radius: 8px;
margin-bottom: 0.75rem;
display: none;
}
#pc-app .pc-error.visible {
display: block;
}
#pc-app .pc-mode-panel {
display: none;
}
#pc-app .pc-mode-panel.active {
display: block;
}
#pc-app .pc-reset-btn {
background: none;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
color: #64748b;
padding: 0.45rem 1rem;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
margin-top: 0.5rem;
transition: all 0.15s;
}
#pc-app .pc-reset-btn:hover {
background: #f1f5f9;
}
</style>

<!-- Unit Toggle -->
<div class="pc-unit-toggle">
<span>Units:</span>
<div class="pc-toggle-btn">
<span id="pc-unit-km" class="active" onclick="pcSetUnit('km')">Metric (km)</span>
<span id="pc-unit-mi" onclick="pcSetUnit('mi')">Imperial (mi)</span>
</div>
</div>

<!-- Mode Tabs -->
<div class="pc-tabs">
<div class="pc-tab active" id="pc-tab-pace" onclick="pcSetMode('pace')">Pace from Distance + Time</div>
<div class="pc-tab" id="pc-tab-time" onclick="pcSetMode('time')">Time from Distance + Pace</div>
<div class="pc-tab" id="pc-tab-dist" onclick="pcSetMode('dist')">Distance from Pace + Time</div>
</div>

<!-- MODE 1: Calc Pace from Distance + Time -->
<div class="pc-mode-panel active" id="pc-panel-pace">
<div class="pc-card">
<h2>Calculate Pace</h2>
<div class="pc-grid" style="margin-bottom:1rem;">
<div class="pc-field">
<label id="pc-dist-label-1">Distance (km)</label>
<input type="number" id="pc-dist-1" min="0.01" step="0.01" placeholder="e.g. 10">
</div>
<div class="pc-field">
<label>Preset Distance</label>
<select id="pc-dist-preset-1" onchange="pcApplyPreset(1)">
<option value="">— select —</option>
<option value="5">5K</option>
<option value="10">10K</option>
<option value="21.0975">Half Marathon</option>
<option value="42.195">Marathon</option>
</select>
</div>
</div>
<div class="pc-field" style="margin-bottom:1rem;">
<label>Time (h : min : sec)</label>
<div class="pc-time-row">
<div>
<input type="number" id="pc-h-1" min="0" max="99" placeholder="0">
<div class="pc-time-label">Hours</div>
</div>
<div>
<input type="number" id="pc-m-1" min="0" max="59" placeholder="0">
<div class="pc-time-label">Minutes</div>
</div>
<div>
<input type="number" id="pc-s-1" min="0" max="59" placeholder="0">
<div class="pc-time-label">Seconds</div>
</div>
</div>
</div>
<div class="pc-error" id="pc-err-1"></div>
<button class="pc-btn" onclick="pcCalcPace()">Calculate Pace</button>
</div>
</div>

<!-- MODE 2: Calc Time from Distance + Pace -->
<div class="pc-mode-panel" id="pc-panel-time">
<div class="pc-card">
<h2>Calculate Finish Time</h2>
<div class="pc-grid" style="margin-bottom:1rem;">
<div class="pc-field">
<label id="pc-dist-label-2">Distance (km)</label>
<input type="number" id="pc-dist-2" min="0.01" step="0.01" placeholder="e.g. 42.195">
</div>
<div class="pc-field">
<label>Preset Distance</label>
<select id="pc-dist-preset-2" onchange="pcApplyPreset(2)">
<option value="">— select —</option>
<option value="5">5K</option>
<option value="10">10K</option>
<option value="21.0975">Half Marathon</option>
<option value="42.195">Marathon</option>
</select>
</div>
</div>
<div class="pc-field" style="margin-bottom:1rem;">
<label id="pc-pace-label-2">Pace (min : sec / km)</label>
<div class="pc-time-row" style="grid-template-columns:1fr 1fr;">
<div>
<input type="number" id="pc-pm-2" min="0" max="59" placeholder="5">
<div class="pc-time-label">Min</div>
</div>
<div>
<input type="number" id="pc-ps-2" min="0" max="59" placeholder="30">
<div class="pc-time-label">Sec</div>
</div>
</div>
</div>
<div class="pc-error" id="pc-err-2"></div>
<button class="pc-btn" onclick="pcCalcTime()">Calculate Time</button>
</div>
</div>

<!-- MODE 3: Calc Distance from Pace + Time -->
<div class="pc-mode-panel" id="pc-panel-dist">
<div class="pc-card">
<h2>Calculate Distance</h2>
<div class="pc-field" style="margin-bottom:1rem;">
<label id="pc-pace-label-3">Pace (min : sec / km)</label>
<div class="pc-time-row" style="grid-template-columns:1fr 1fr;">
<div>
<input type="number" id="pc-pm-3" min="0" max="59" placeholder="5">
<div class="pc-time-label">Min</div>
</div>
<div>
<input type="number" id="pc-ps-3" min="0" max="59" placeholder="30">
<div class="pc-time-label">Sec</div>
</div>
</div>
</div>
<div class="pc-field" style="margin-bottom:1rem;">
<label>Duration (h : min : sec)</label>
<div class="pc-time-row">
<div>
<input type="number" id="pc-h-3" min="0" max="99" placeholder="1">
<div class="pc-time-label">Hours</div>
</div>
<div>
<input type="number" id="pc-m-3" min="0" max="59" placeholder="0">
<div class="pc-time-label">Minutes</div>
</div>
<div>
<input type="number" id="pc-s-3" min="0" max="59" placeholder="0">
<div class="pc-time-label">Seconds</div>
</div>
</div>
</div>
<div class="pc-error" id="pc-err-3"></div>
<button class="pc-btn" onclick="pcCalcDist()">Calculate Distance</button>
</div>
</div>

<!-- Results -->
<div class="pc-results" id="pc-results">
<div class="pc-card">
<h2>Results</h2>
<div class="pc-result-grid" id="pc-result-grid"></div>
<button class="pc-reset-btn" onclick="pcReset()">Clear / Reset</button>
</div>

<div class="pc-card" id="pc-race-section">
<h2>Race Time Predictions</h2>
<table class="pc-race-table">
<thead>
<tr>
<th>Race</th>
<th>Distance</th>
<th>Predicted Time</th>
<th id="pc-race-pace-header">Pace</th>
</tr>
</thead>
<tbody id="pc-race-body"></tbody>
</table>
<p style="font-size:0.75rem;color:#94a3b8;margin-top:0.6rem;">Predictions assume constant pace. Actual race performance varies with terrain, weather, and fatigue.</p>
</div>

<div class="pc-card" id="pc-split-section">
<h2>Split Table</h2>
<div style="font-size:0.82rem;color:#64748b;margin-bottom:0.75rem;" id="pc-split-label"></div>
<div style="overflow-x:auto;">
<table class="pc-split-table">
<thead id="pc-split-head"></thead>
<tbody id="pc-split-body"></tbody>
</table>
</div>
</div>
</div>

<script>
(function () {
'use strict';

var pcUnit = 'km';   // 'km' | 'mi'
var pcMode = 'pace'; // 'pace' | 'time' | 'dist'
var pcLastPaceSec = 0;   // pace in sec/km (always metric internally)
var pcLastDistKm = 0;
var pcLastTimeSec = 0;

var KM_TO_MI = 0.621371;
var MI_TO_KM = 1.60934;

// ─── Unit toggle ───────────────────────────────────────────────
window.pcSetUnit = function (u) {
pcUnit = u;
document.getElementById('pc-unit-km').classList.toggle('active', u === 'km');
document.getElementById('pc-unit-mi').classList.toggle('active', u === 'mi');

var distLabel = u === 'km' ? 'Distance (km)' : 'Distance (mi)';
var paceLabel = u === 'km' ? 'Pace (min : sec / km)' : 'Pace (min : sec / mile)';

document.getElementById('pc-dist-label-1').textContent = distLabel;
document.getElementById('pc-dist-label-2').textContent = distLabel;
document.getElementById('pc-pace-label-2').textContent = paceLabel;
document.getElementById('pc-pace-label-3').textContent = paceLabel;

// Update preset values if miles
var presets1 = document.getElementById('pc-dist-preset-1');
var presets2 = document.getElementById('pc-dist-preset-2');
[presets1, presets2].forEach(function (sel) {
sel.options[1].value = u === 'km' ? '5'       : (5 * KM_TO_MI).toFixed(4);
sel.options[2].value = u === 'km' ? '10'      : (10 * KM_TO_MI).toFixed(4);
sel.options[3].value = u === 'km' ? '21.0975' : (21.0975 * KM_TO_MI).toFixed(4);
sel.options[4].value = u === 'km' ? '42.195'  : (42.195 * KM_TO_MI).toFixed(4);
});
};

// ─── Mode switch ───────────────────────────────────────────────
window.pcSetMode = function (m) {
pcMode = m;
['pace','time','dist'].forEach(function (id) {
document.getElementById('pc-tab-' + id).classList.toggle('active', id === m);
document.getElementById('pc-panel-' + id).classList.toggle('active', id === m);
});
document.getElementById('pc-results').classList.remove('visible');
};

// ─── Preset apply ──────────────────────────────────────────────
window.pcApplyPreset = function (panel) {
var sel = document.getElementById('pc-dist-preset-' + panel);
var val = sel.value;
if (!val) return;
document.getElementById('pc-dist-' + panel).value = parseFloat(val).toFixed(
pcUnit === 'km' ? 3 : 3
);
};

// ─── Helpers ───────────────────────────────────────────────────
function fmtTime(totalSec) {
totalSec = Math.round(totalSec);
var h = Math.floor(totalSec / 3600);
var m = Math.floor((totalSec % 3600) / 60);
var s = totalSec % 60;
if (h > 0) {
return h + ':' + pad(m) + ':' + pad(s);
}
return m + ':' + pad(s);
}

function fmtPace(secPerKm) {
var m = Math.floor(secPerKm / 60);
var s = Math.round(secPerKm % 60);
if (s === 60) { m += 1; s = 0; }
return m + ':' + pad(s);
}

function pad(n) { return n < 10 ? '0' + n : '' + n; }

function getVal(id) {
var v = parseFloat(document.getElementById(id).value);
return isNaN(v) ? 0 : v;
}

function showErr(id, msg) {
var el = document.getElementById(id);
el.textContent = msg;
el.classList.add('visible');
}

function clearErr(id) {
document.getElementById(id).classList.remove('visible');
}

function resultBox(label, val, unit, highlight) {
return '<div class="pc-result-box' + (highlight ? ' highlight' : '') + '">' +
'<div class="pc-result-label">' + label + '</div>' +
'<div class="pc-result-val">' + val + '</div>' +
'<div class="pc-result-unit">' + unit + '</div>' +
'</div>';
}

function showResults(html) {
document.getElementById('pc-result-grid').innerHTML = html;
document.getElementById('pc-results').classList.add('visible');
document.getElementById('pc-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
}

// ─── Race predictions ──────────────────────────────────────────
function buildRacePredictions(paceSec) {
// paceSec = sec per km
var races = [
{ name: '5K',           distKm: 5 },
{ name: '10K',          distKm: 10 },
{ name: 'Half Marathon', distKm: 21.0975 },
{ name: 'Marathon',     distKm: 42.195 }
];
var hdr = document.getElementById('pc-race-pace-header');
hdr.textContent = pcUnit === 'km' ? 'Pace (min/km)' : 'Pace (min/mi)';

var rows = races.map(function (r) {
var timeSec = paceSec * r.distKm;
var dispDist = pcUnit === 'km'
? r.distKm.toFixed(r.distKm % 1 === 0 ? 0 : 3) + ' km'
: (r.distKm * KM_TO_MI).toFixed(2) + ' mi';
var dispPace = pcUnit === 'km'
? fmtPace(paceSec) + ' /km'
: fmtPace(paceSec / KM_TO_MI) + ' /mi';
return '<tr><td><strong>' + r.name + '</strong></td><td>' + dispDist + '</td><td>' + fmtTime(timeSec) + '</td><td>' + dispPace + '</td></tr>';
});
document.getElementById('pc-race-body').innerHTML = rows.join('');
}

// ─── Split table ───────────────────────────────────────────────
function buildSplitTable(paceSec, distKm) {
var unit = pcUnit;
var splitDistKm = unit === 'km' ? 1 : MI_TO_KM;  // 1 km or 1 mile splits
var splitLabel  = unit === 'km' ? 'km' : 'mi';
var totalDist   = unit === 'km' ? distKm : distKm * KM_TO_MI;
var pacePerSplit = unit === 'km' ? paceSec : paceSec / KM_TO_MI; // sec per display unit

var count = Math.floor(totalDist);
if (count < 1) count = 1;
if (count > 50) count = 50;

document.getElementById('pc-split-label').textContent =
'Splits every 1 ' + splitLabel + ' for ' + totalDist.toFixed(unit === 'km' ? 3 : 2) + ' ' + splitLabel;

var head = '<tr><th>' + splitLabel + '</th><th>Split Time</th><th>Elapsed</th></tr>';
document.getElementById('pc-split-head').innerHTML = head;

var rows = '';
for (var i = 1; i <= count; i++) {
var elapsed = pacePerSplit * i;
rows += '<tr><td>' + i + '</td><td>' + fmtTime(pacePerSplit) + '</td><td>' + fmtTime(elapsed) + '</td></tr>';
}
// Final partial split if needed
var remainder = totalDist - count;
if (remainder > 0.01) {
var partialSec = pacePerSplit * remainder;
var totalElapsed = pacePerSplit * count + partialSec;
rows += '<tr><td>' + totalDist.toFixed(2) + ' (' + splitLabel + ')</td><td>' + fmtTime(partialSec) + '</td><td>' + fmtTime(totalElapsed) + '</td></tr>';
}
document.getElementById('pc-split-body').innerHTML = rows;
}

// ─── MODE 1: Calc pace ─────────────────────────────────────────
window.pcCalcPace = function () {
clearErr('pc-err-1');
var distInput = getVal('pc-dist-1');
var h = getVal('pc-h-1');
var m = getVal('pc-m-1');
var s = getVal('pc-s-1');
var totalTimeSec = h * 3600 + m * 60 + s;

if (!distInput || distInput <= 0) { showErr('pc-err-1', 'Please enter a valid distance.'); return; }
if (totalTimeSec <= 0) { showErr('pc-err-1', 'Please enter a valid time.'); return; }

var distKm = pcUnit === 'km' ? distInput : distInput * MI_TO_KM;
var paceSec = totalTimeSec / distKm;          // sec/km
var speedKmh = distKm / (totalTimeSec / 3600);
var speedMph = speedKmh * KM_TO_MI;
var pacePerMi = paceSec / KM_TO_MI;           // sec/mile

pcLastPaceSec = paceSec;
pcLastDistKm  = distKm;
pcLastTimeSec = totalTimeSec;

var html = '';
html += resultBox('Pace', fmtPace(paceSec), 'min:sec / km', true);
html += resultBox('Pace', fmtPace(pacePerMi), 'min:sec / mile', false);
html += resultBox('Speed', speedKmh.toFixed(2), 'km/h', false);
html += resultBox('Speed', speedMph.toFixed(2), 'mph', false);

showResults(html);
buildRacePredictions(paceSec);
buildSplitTable(paceSec, distKm);
};

// ─── MODE 2: Calc time ─────────────────────────────────────────
window.pcCalcTime = function () {
clearErr('pc-err-2');
var distInput = getVal('pc-dist-2');
var pm = getVal('pc-pm-2');
var ps = getVal('pc-ps-2');
var paceSec = pcUnit === 'km'
? pm * 60 + ps
: (pm * 60 + ps) * KM_TO_MI; // convert min/mi to sec/km

if (!distInput || distInput <= 0) { showErr('pc-err-2', 'Please enter a valid distance.'); return; }
if (paceSec <= 0) { showErr('pc-err-2', 'Please enter a valid pace.'); return; }

var distKm = pcUnit === 'km' ? distInput : distInput * MI_TO_KM;
var totalTimeSec = paceSec * distKm;
var speedKmh = distKm / (totalTimeSec / 3600);
var speedMph = speedKmh * KM_TO_MI;
var pacePerMi = paceSec / KM_TO_MI;

pcLastPaceSec = paceSec;
pcLastDistKm  = distKm;
pcLastTimeSec = totalTimeSec;

var html = '';
html += resultBox('Finish Time', fmtTime(totalTimeSec), 'h:min:sec', true);
html += resultBox('Pace', fmtPace(paceSec), 'min:sec / km', false);
html += resultBox('Speed', speedKmh.toFixed(2), 'km/h', false);
html += resultBox('Speed', speedMph.toFixed(2), 'mph', false);

showResults(html);
buildRacePredictions(paceSec);
buildSplitTable(paceSec, distKm);
};

// ─── MODE 3: Calc distance ─────────────────────────────────────
window.pcCalcDist = function () {
clearErr('pc-err-3');
var pm = getVal('pc-pm-3');
var ps = getVal('pc-ps-3');
var h  = getVal('pc-h-3');
var m  = getVal('pc-m-3');
var s  = getVal('pc-s-3');

var paceSec = pcUnit === 'km'
? pm * 60 + ps
: (pm * 60 + ps) * KM_TO_MI;
var totalTimeSec = h * 3600 + m * 60 + s;

if (paceSec <= 0) { showErr('pc-err-3', 'Please enter a valid pace.'); return; }
if (totalTimeSec <= 0) { showErr('pc-err-3', 'Please enter a valid duration.'); return; }

var distKm = totalTimeSec / paceSec;
var distMi = distKm * KM_TO_MI;
var speedKmh = distKm / (totalTimeSec / 3600);
var speedMph = speedKmh * KM_TO_MI;

pcLastPaceSec = paceSec;
pcLastDistKm  = distKm;
pcLastTimeSec = totalTimeSec;

var html = '';
if (pcUnit === 'km') {
html += resultBox('Distance', distKm.toFixed(2), 'km', true);
html += resultBox('Distance', distMi.toFixed(2), 'miles', false);
} else {
html += resultBox('Distance', distMi.toFixed(2), 'miles', true);
html += resultBox('Distance', distKm.toFixed(2), 'km', false);
}
html += resultBox('Speed', speedKmh.toFixed(2), 'km/h', false);
html += resultBox('Speed', speedMph.toFixed(2), 'mph', false);

showResults(html);
buildRacePredictions(paceSec);
buildSplitTable(paceSec, distKm);
};

// ─── Reset ─────────────────────────────────────────────────────
window.pcReset = function () {
document.getElementById('pc-results').classList.remove('visible');
['pc-dist-1','pc-h-1','pc-m-1','pc-s-1',
'pc-dist-2','pc-pm-2','pc-ps-2',
'pc-pm-3','pc-ps-3','pc-h-3','pc-m-3','pc-s-3'].forEach(function (id) {
var el = document.getElementById(id);
if (el) el.value = '';
});
['pc-dist-preset-1','pc-dist-preset-2'].forEach(function (id) {
var el = document.getElementById(id);
if (el) el.selectedIndex = 0;
});
clearErr('pc-err-1'); clearErr('pc-err-2'); clearErr('pc-err-3');
};
})();
</script>
</div>

---

## Related Tools

- Track your fitness calories → [Calorie Calculator](/tools/calorie-calculator/)
- Check your body weight range → [BMI Calculator](/tools/bmi-calculator/)
