---
title: "Meeting Cost Calculator"
date: 2025-05-16
description: "Free online meeting cost calculator. See the real-time cost of your meetings based on attendees and salaries — make every minute count."
categories: ["Free Tools"]
slug: "meeting-cost-calculator"
ShowToc: false
cover:
  image: "/images/covers/meeting-cost-calculator.png"
  alt: "Meeting Cost Calculator"
---

<div id="mc-app">

<style>
#mc-app {
--bg: #0f172a;
--surface: #1e293b;
--surface2: #334155;
--border: #475569;
--accent: #38bdf8;
--accent-dark: #0284c7;
--accent-hover: #7dd3fc;
--success: #34d399;
--warning: #fbbf24;
--danger: #f87171;
--text: #f1f5f9;
--text-muted: #94a3b8;
--text-dim: #64748b;
--radius: 10px;
--radius-sm: 6px;
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
background: var(--bg);
color: var(--text);
padding: 1.5rem 1rem;
border-radius: 16px;
max-width: 820px;
margin: 0 auto;
box-sizing: border-box;
}
#mc-app *, #mc-app *::before, #mc-app *::after { box-sizing: border-box; }

/* Typography */
#mc-app h2 {
font-size: 1.1rem;
font-weight: 700;
color: var(--accent);
margin: 0 0 1rem 0;
letter-spacing: 0.04em;
text-transform: uppercase;
display: flex;
align-items: center;
gap: 0.5rem;
}
#mc-app h2 .icon { font-size: 1.1em; }

/* Cards */
#mc-app .mc-card {
background: var(--surface);
border: 1px solid var(--border);
border-radius: var(--radius);
padding: 1.25rem 1.25rem;
margin-bottom: 1.25rem;
}

/* Grid */
#mc-app .mc-grid-2 {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1.25rem;
}
@media (max-width: 600px) {
#mc-app .mc-grid-2 { grid-template-columns: 1fr; }
}

/* Buttons */
#mc-app button {
cursor: pointer;
border: none;
border-radius: var(--radius-sm);
font-size: 0.875rem;
font-weight: 600;
padding: 0.45rem 0.9rem;
transition: background 0.15s, transform 0.1s, opacity 0.15s;
}
#mc-app button:active { transform: scale(0.97); }
#mc-app button:disabled { opacity: 0.45; cursor: not-allowed; transform: none; }

#mc-app .btn-primary {
background: var(--accent-dark);
color: #fff;
}
#mc-app .btn-primary:hover:not(:disabled) { background: var(--accent); color: #0f172a; }

#mc-app .btn-success {
background: #065f46;
color: var(--success);
border: 1px solid var(--success);
}
#mc-app .btn-success:hover:not(:disabled) { background: var(--success); color: #022c22; }

#mc-app .btn-warning {
background: #78350f;
color: var(--warning);
border: 1px solid var(--warning);
}
#mc-app .btn-warning:hover:not(:disabled) { background: var(--warning); color: #1c0a00; }

#mc-app .btn-danger {
background: #450a0a;
color: var(--danger);
border: 1px solid var(--danger);
}
#mc-app .btn-danger:hover:not(:disabled) { background: var(--danger); color: #1c0000; }

#mc-app .btn-ghost {
background: transparent;
color: var(--text-muted);
border: 1px solid var(--border);
}
#mc-app .btn-ghost:hover:not(:disabled) { background: var(--surface2); color: var(--text); }

#mc-app .btn-sm {
font-size: 0.78rem;
padding: 0.3rem 0.65rem;
}

/* Form inputs */
#mc-app input[type="text"],
#mc-app input[type="number"] {
background: var(--bg);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
color: var(--text);
font-size: 0.9rem;
padding: 0.45rem 0.7rem;
width: 100%;
outline: none;
transition: border-color 0.15s;
}
#mc-app input[type="text"]:focus,
#mc-app input[type="number"]:focus {
border-color: var(--accent);
}
#mc-app input[type="radio"] { accent-color: var(--accent); }

#mc-app label {
font-size: 0.82rem;
color: var(--text-muted);
display: block;
margin-bottom: 0.3rem;
}

/* Presets */
#mc-app .mc-presets {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-bottom: 1rem;
}
#mc-app .mc-preset-btn {
background: var(--surface2);
color: var(--text);
border: 1px solid var(--border);
border-radius: 20px;
font-size: 0.8rem;
padding: 0.3rem 0.75rem;
cursor: pointer;
transition: background 0.15s, border-color 0.15s;
}
#mc-app .mc-preset-btn:hover { background: var(--accent-dark); border-color: var(--accent); color: #fff; }

/* Attendee add form */
#mc-app .mc-add-form {
display: grid;
grid-template-columns: 1fr auto auto auto;
gap: 0.6rem;
align-items: end;
margin-bottom: 1rem;
}
@media (max-width: 560px) {
#mc-app .mc-add-form {
grid-template-columns: 1fr 1fr;
}
#mc-app .mc-add-form .mc-add-btn { grid-column: 1 / -1; }
}

#mc-app .mc-rate-toggle {
display: flex;
gap: 0.4rem;
align-items: center;
font-size: 0.8rem;
color: var(--text-muted);
white-space: nowrap;
}

/* Attendee list */
#mc-app .mc-attendee-list {
display: flex;
flex-direction: column;
gap: 0.5rem;
}
#mc-app .mc-attendee-item {
display: grid;
grid-template-columns: 1fr auto auto auto;
align-items: center;
gap: 0.6rem;
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
padding: 0.5rem 0.75rem;
}
@media (max-width: 480px) {
#mc-app .mc-attendee-item {
grid-template-columns: 1fr auto auto;
}
}
#mc-app .mc-attendee-name {
font-weight: 600;
font-size: 0.9rem;
}
#mc-app .mc-attendee-rate {
font-size: 0.82rem;
color: var(--text-muted);
white-space: nowrap;
}
#mc-app .mc-attendee-count {
display: flex;
align-items: center;
gap: 0.3rem;
}
#mc-app .mc-attendee-count button {
background: var(--bg);
border: 1px solid var(--border);
color: var(--text);
border-radius: 4px;
width: 26px;
height: 26px;
padding: 0;
font-size: 1rem;
line-height: 1;
display: flex;
align-items: center;
justify-content: center;
}
#mc-app .mc-attendee-count button:hover { background: var(--surface2); border-color: var(--accent); }
#mc-app .mc-count-val {
min-width: 20px;
text-align: center;
font-weight: 700;
font-size: 0.9rem;
}
#mc-app .mc-remove-btn {
background: transparent;
border: none;
color: var(--text-dim);
font-size: 1.1rem;
padding: 0 0.2rem;
cursor: pointer;
transition: color 0.15s;
}
#mc-app .mc-remove-btn:hover { color: var(--danger); }

#mc-app .mc-empty-msg {
text-align: center;
color: var(--text-dim);
font-size: 0.88rem;
padding: 1rem 0;
}

/* Summary bar */
#mc-app .mc-summary-bar {
display: flex;
flex-wrap: wrap;
gap: 1rem;
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
padding: 0.75rem 1rem;
margin-top: 0.75rem;
font-size: 0.88rem;
color: var(--text-muted);
}
#mc-app .mc-summary-bar strong {
color: var(--accent);
font-size: 1rem;
}

/* Timer display */
#mc-app .mc-timer-display {
text-align: center;
margin: 0.5rem 0 1.25rem;
}
#mc-app .mc-timer-time {
font-size: 3.5rem;
font-weight: 800;
letter-spacing: 0.08em;
color: var(--text);
font-variant-numeric: tabular-nums;
line-height: 1;
}
#mc-app .mc-timer-cost {
font-size: 2.2rem;
font-weight: 700;
color: var(--accent);
margin-top: 0.4rem;
font-variant-numeric: tabular-nums;
}
#mc-app .mc-timer-label {
font-size: 0.82rem;
color: var(--text-dim);
margin-top: 0.2rem;
}
#mc-app .mc-timer-running .mc-timer-cost { color: var(--warning); }

#mc-app .mc-timer-buttons {
display: flex;
justify-content: center;
gap: 0.75rem;
flex-wrap: wrap;
}
#mc-app .mc-timer-buttons button {
min-width: 90px;
padding: 0.6rem 1.2rem;
font-size: 0.95rem;
}

/* Status badge */
#mc-app .mc-status {
display: inline-flex;
align-items: center;
gap: 0.35rem;
font-size: 0.78rem;
font-weight: 600;
padding: 0.2rem 0.65rem;
border-radius: 20px;
margin-left: 0.5rem;
vertical-align: middle;
}
#mc-app .mc-status.idle { background: var(--surface2); color: var(--text-dim); }
#mc-app .mc-status.running { background: #065f46; color: var(--success); }
#mc-app .mc-status.paused { background: #78350f; color: var(--warning); }

/* Estimate section */
#mc-app .mc-estimate-row {
display: flex;
align-items: flex-end;
gap: 0.75rem;
flex-wrap: wrap;
}
#mc-app .mc-estimate-row > div { flex: 1; min-width: 120px; }
#mc-app .mc-estimate-result {
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
padding: 0.75rem 1rem;
margin-top: 0.75rem;
font-size: 0.9rem;
color: var(--text-muted);
}
#mc-app .mc-estimate-result .mc-big-num {
font-size: 1.8rem;
font-weight: 800;
color: var(--accent);
}

/* Results section */
#mc-app .mc-results {
display: none;
}
#mc-app .mc-results.visible { display: block; }
#mc-app .mc-results-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 0.75rem;
margin-bottom: 1rem;
}
@media (max-width: 500px) {
#mc-app .mc-results-grid { grid-template-columns: 1fr 1fr; }
}
#mc-app .mc-result-box {
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
padding: 0.85rem 0.75rem;
text-align: center;
}
#mc-app .mc-result-box .mc-result-val {
font-size: 1.5rem;
font-weight: 800;
color: var(--accent);
}
#mc-app .mc-result-box .mc-result-lbl {
font-size: 0.75rem;
color: var(--text-dim);
margin-top: 0.2rem;
}

/* Fun comparisons */
#mc-app .mc-comparisons {
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
padding: 1rem;
}
#mc-app .mc-comparisons h3 {
font-size: 0.88rem;
font-weight: 700;
color: var(--text-muted);
text-transform: uppercase;
letter-spacing: 0.05em;
margin: 0 0 0.75rem 0;
}
#mc-app .mc-comp-list {
display: flex;
flex-direction: column;
gap: 0.45rem;
}
#mc-app .mc-comp-item {
display: flex;
align-items: center;
gap: 0.6rem;
font-size: 0.9rem;
}
#mc-app .mc-comp-icon { font-size: 1.2em; width: 1.4em; text-align: center; }
#mc-app .mc-comp-text { color: var(--text); }
#mc-app .mc-comp-text strong { color: var(--accent-hover); }

/* Cross-links */
#mc-app .mc-crosslinks {
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius-sm);
padding: 0.85rem 1rem;
margin-top: 1.25rem;
font-size: 0.88rem;
color: var(--text-muted);
display: flex;
flex-wrap: wrap;
gap: 0.5rem 1.5rem;
}
#mc-app .mc-crosslinks a {
color: var(--accent);
text-decoration: none;
font-weight: 500;
}
#mc-app .mc-crosslinks a:hover { text-decoration: underline; color: var(--accent-hover); }
#mc-app .mc-crosslinks span { white-space: nowrap; }

/* Divider */
#mc-app .mc-divider {
height: 1px;
background: var(--border);
margin: 1rem 0;
}

/* Pulse animation for running cost */
@keyframes mc-pulse {
0%   { opacity: 1; }
50%  { opacity: 0.7; }
100% { opacity: 1; }
}
#mc-app .mc-timer-running .mc-timer-cost {
animation: mc-pulse 1s infinite;
}
</style>

<!-- ===== SECTION 1: ATTENDEES ===== -->
<div class="mc-card">
<h2><span class="icon">👥</span> Attendees</h2>

<div class="mc-presets" id="mc-presets"></div>

<div class="mc-add-form" id="mc-add-form">
<div>
<label for="mc-role-name">Role / Name</label>
<input type="text" id="mc-role-name" placeholder="e.g. Product Manager" />
</div>
<div>
<label id="mc-rate-label" for="mc-rate-value">Hourly Rate ($)</label>
<input type="number" id="mc-rate-value" min="0" step="1" placeholder="e.g. 80" style="max-width:110px;" />
</div>
<div>
<label style="white-space:nowrap;">Input type</label>
<div class="mc-rate-toggle">
<label style="display:inline-flex;align-items:center;gap:0.3rem;color:var(--text);font-size:0.82rem;">
<input type="radio" name="mc-rate-type" value="hourly" checked /> Hourly
</label>
<label style="display:inline-flex;align-items:center;gap:0.3rem;color:var(--text);font-size:0.82rem;">
<input type="radio" name="mc-rate-type" value="annual" /> Annual
</label>
</div>
</div>
<div class="mc-add-btn">
<label style="visibility:hidden;">Add</label>
<button class="btn-primary" onclick="mcAddAttendee()">+ Add</button>
</div>
</div>

<div class="mc-attendee-list" id="mc-attendee-list">
<div class="mc-empty-msg" id="mc-empty-msg">No attendees yet. Add roles above or use a preset.</div>
</div>

<div class="mc-summary-bar" id="mc-summary-bar" style="display:none;">
<span>Total Attendees: <strong id="mc-total-attendees">0</strong></span>
<span>Combined Rate: <strong id="mc-total-rate">$0.00</strong>/hr</span>
<span>Per Minute: <strong id="mc-per-minute">$0.00</strong>/min</span>
</div>
</div>

<!-- ===== SECTION 2: ESTIMATE ===== -->
<div class="mc-card">
<h2><span class="icon">📋</span> Pre-Meeting Estimate</h2>
<div class="mc-estimate-row">
<div>
<label for="mc-planned-mins">Planned Duration (minutes)</label>
<input type="number" id="mc-planned-mins" min="1" step="1" placeholder="e.g. 60" oninput="mcUpdateEstimate()" />
</div>
</div>
<div class="mc-estimate-result" id="mc-estimate-result" style="display:none;">
<div>Estimated cost for this meeting:</div>
<div class="mc-big-num" id="mc-estimate-val">$0.00</div>
<div style="font-size:0.8rem;color:var(--text-dim);margin-top:0.25rem;" id="mc-estimate-detail"></div>
</div>
</div>

<!-- ===== SECTION 3: TIMER ===== -->
<div class="mc-card">
<h2>
<span class="icon">⏱</span> Meeting Timer
<span class="mc-status idle" id="mc-status-badge">Idle</span>
</h2>

<div class="mc-timer-display" id="mc-timer-display">
<div class="mc-timer-time" id="mc-timer-time">00:00</div>
<div class="mc-timer-cost" id="mc-timer-cost">$0.00</div>
<div class="mc-timer-label">real-time cost</div>
</div>

<div class="mc-timer-buttons">
<button class="btn-success" id="mc-btn-start" onclick="mcTimerStart()">&#9654; Start</button>
<button class="btn-warning" id="mc-btn-pause" onclick="mcTimerPause()" disabled>&#9646;&#9646; Pause</button>
<button class="btn-danger" id="mc-btn-stop" onclick="mcTimerStop()" disabled>&#9632; Stop &amp; Report</button>
<button class="btn-ghost" id="mc-btn-reset" onclick="mcTimerReset()">&#8635; Reset</button>
</div>
</div>

<!-- ===== SECTION 4: RESULTS ===== -->
<div class="mc-card mc-results" id="mc-results">
<h2><span class="icon">📊</span> Meeting Report</h2>

<div class="mc-results-grid">
<div class="mc-result-box">
<div class="mc-result-val" id="mc-res-total">$0.00</div>
<div class="mc-result-lbl">Total Cost</div>
</div>
<div class="mc-result-box">
<div class="mc-result-val" id="mc-res-per-min">$0.00</div>
<div class="mc-result-lbl">Cost / Minute</div>
</div>
<div class="mc-result-box">
<div class="mc-result-val" id="mc-res-per-person">$0.00</div>
<div class="mc-result-lbl">Cost / Attendee</div>
</div>
</div>

<div class="mc-comparisons">
<h3>What else could this buy?</h3>
<div class="mc-comp-list" id="mc-comp-list"></div>
</div>
</div>

<!-- ===== CROSS-LINKS ===== -->
<div class="mc-crosslinks">
<span>Focus with Pomodoro &rarr; <a href="/tools/pomodoro-timer/">Pomodoro Timer</a></span>
<span>Calculate salary &rarr; <a href="/tools/salary-calculator/">Salary Calculator</a></span>
<span>Track ROI &rarr; <a href="/tools/roi-calculator/">ROI Calculator</a></span>
</div>

<script>
(function() {
/* ---- State ---- */
var attendees = [];
var timerInterval = null;
var timerStartTs = null;
var timerElapsed = 0; // ms accumulated before current start
var timerRunning = false;
var timerStopped = false;

/* ---- Presets ---- */
var PRESETS = [
{ label: "Junior", rate: 30 },
{ label: "Mid",    rate: 50 },
{ label: "Senior", rate: 80 },
{ label: "Manager",rate: 100 },
{ label: "Exec",   rate: 150 },
];

function buildPresets() {
var el = document.getElementById("mc-presets");
el.innerHTML = "";
PRESETS.forEach(function(p) {
var btn = document.createElement("button");
btn.className = "mc-preset-btn";
btn.textContent = p.label + " ($" + p.rate + "/hr)";
btn.onclick = function() { applyPreset(p); };
el.appendChild(btn);
});
}

function applyPreset(p) {
document.getElementById("mc-role-name").value = p.label;
document.getElementById("mc-rate-value").value = p.rate;
// set to hourly
document.querySelector('input[name="mc-rate-type"][value="hourly"]').checked = true;
updateRateLabel();
mcAddAttendee();
}

/* ---- Rate type toggle ---- */
document.querySelectorAll('input[name="mc-rate-type"]').forEach(function(r) {
r.addEventListener("change", updateRateLabel);
});
function updateRateLabel() {
var type = document.querySelector('input[name="mc-rate-type"]:checked').value;
var lbl = document.getElementById("mc-rate-label");
var inp = document.getElementById("mc-rate-value");
if (type === "annual") {
lbl.textContent = "Annual Salary ($)";
inp.placeholder = "e.g. 80000";
inp.step = "1000";
} else {
lbl.textContent = "Hourly Rate ($)";
inp.placeholder = "e.g. 80";
inp.step = "1";
}
}

/* ---- Add Attendee ---- */
window.mcAddAttendee = function() {
var name = document.getElementById("mc-role-name").value.trim();
var rateRaw = parseFloat(document.getElementById("mc-rate-value").value);
var type = document.querySelector('input[name="mc-rate-type"]:checked').value;

if (!name) { document.getElementById("mc-role-name").focus(); return; }
if (isNaN(rateRaw) || rateRaw <= 0) { document.getElementById("mc-rate-value").focus(); return; }

var hourlyRate = (type === "annual") ? rateRaw / 2080 : rateRaw;

// Check if role already exists — increment count
var existing = attendees.find(function(a) { return a.name.toLowerCase() === name.toLowerCase(); });
if (existing) {
existing.count++;
} else {
attendees.push({ id: Date.now(), name: name, hourlyRate: hourlyRate, annualEquiv: hourlyRate * 2080, count: 1 });
}

document.getElementById("mc-role-name").value = "";
document.getElementById("mc-rate-value").value = "";
renderAttendees();
mcUpdateEstimate();
};

/* ---- Render Attendees ---- */
function renderAttendees() {
var list = document.getElementById("mc-attendee-list");
var empty = document.getElementById("mc-empty-msg");
var summaryBar = document.getElementById("mc-summary-bar");

if (attendees.length === 0) {
list.innerHTML = "";
list.appendChild(empty);
empty.style.display = "block";
summaryBar.style.display = "none";
return;
}
empty.style.display = "none";
list.innerHTML = "";

attendees.forEach(function(a) {
var item = document.createElement("div");
item.className = "mc-attendee-item";
item.innerHTML =
'<div>' +
'<div class="mc-attendee-name">' + escHtml(a.name) + '</div>' +
'<div class="mc-attendee-rate">$' + a.hourlyRate.toFixed(2) + '/hr &middot; ~$' + Math.round(a.annualEquiv).toLocaleString() + '/yr</div>' +
'</div>' +
'<div class="mc-attendee-count">' +
'<button onclick="mcChangeCount(' + a.id + ',-1)" title="Remove one">&#8722;</button>' +
'<span class="mc-count-val">' + a.count + '</span>' +
'<button onclick="mcChangeCount(' + a.id + ',1)" title="Add one">+</button>' +
'</div>' +
'<div class="mc-attendee-rate" style="white-space:nowrap;">Subtotal: $' + (a.hourlyRate * a.count).toFixed(2) + '/hr</div>' +
'<button class="mc-remove-btn" onclick="mcRemoveAttendee(' + a.id + ')" title="Remove">&times;</button>';
list.appendChild(item);
});

// Summary
var totalPeople = attendees.reduce(function(s, a) { return s + a.count; }, 0);
var totalRate = attendees.reduce(function(s, a) { return s + a.hourlyRate * a.count; }, 0);
document.getElementById("mc-total-attendees").textContent = totalPeople;
document.getElementById("mc-total-rate").textContent = "$" + totalRate.toFixed(2);
document.getElementById("mc-per-minute").textContent = "$" + (totalRate / 60).toFixed(3);
summaryBar.style.display = "flex";
}

window.mcChangeCount = function(id, delta) {
var a = attendees.find(function(x) { return x.id === id; });
if (!a) return;
a.count = Math.max(1, a.count + delta);
renderAttendees();
mcUpdateEstimate();
};

window.mcRemoveAttendee = function(id) {
attendees = attendees.filter(function(a) { return a.id !== id; });
renderAttendees();
mcUpdateEstimate();
};

/* ---- Helpers ---- */
function getTotalHourlyRate() {
return attendees.reduce(function(s, a) { return s + a.hourlyRate * a.count; }, 0);
}
function getTotalAttendees() {
return attendees.reduce(function(s, a) { return s + a.count; }, 0);
}
function formatMoney(n) {
if (n >= 10000) return "$" + Math.round(n).toLocaleString();
if (n >= 100)   return "$" + n.toFixed(0);
return "$" + n.toFixed(2);
}
function formatTime(ms) {
var totalSec = Math.floor(ms / 1000);
var min = Math.floor(totalSec / 60);
var sec = totalSec % 60;
return pad2(min) + ":" + pad2(sec);
}
function pad2(n) { return n < 10 ? "0" + n : "" + n; }
function escHtml(s) {
return s.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");
}

/* ---- Estimate ---- */
window.mcUpdateEstimate = function() {
var mins = parseFloat(document.getElementById("mc-planned-mins").value);
var resultEl = document.getElementById("mc-estimate-result");
var valEl = document.getElementById("mc-estimate-val");
var detailEl = document.getElementById("mc-estimate-detail");
var rate = getTotalHourlyRate();

if (!mins || mins <= 0 || rate <= 0) {
resultEl.style.display = "none";
return;
}
var cost = rate * (mins / 60);
valEl.textContent = formatMoney(cost);
detailEl.textContent =
getTotalAttendees() + " attendees \u00d7 " +
mins.toFixed(0) + " min \u00d7 $" + rate.toFixed(2) + "/hr combined";
resultEl.style.display = "block";
};

/* ---- Timer ---- */
function getElapsedMs() {
if (timerRunning && timerStartTs) {
return timerElapsed + (Date.now() - timerStartTs);
}
return timerElapsed;
}

function updateTimerDisplay() {
var ms = getElapsedMs();
var rate = getTotalHourlyRate();
var cost = rate * (ms / 3600000);
document.getElementById("mc-timer-time").textContent = formatTime(ms);
document.getElementById("mc-timer-cost").textContent = formatMoney(cost);
}

window.mcTimerStart = function() {
if (timerRunning) return;
if (attendees.length === 0) {
alert("Please add at least one attendee before starting the timer.");
return;
}
timerRunning = true;
timerStopped = false;
timerStartTs = Date.now();
timerInterval = setInterval(updateTimerDisplay, 1000);

document.getElementById("mc-btn-start").disabled = true;
document.getElementById("mc-btn-pause").disabled = false;
document.getElementById("mc-btn-stop").disabled = false;
document.getElementById("mc-timer-display").classList.add("mc-timer-running");
setStatusBadge("running");

// Hide previous results
document.getElementById("mc-results").classList.remove("visible");
};

window.mcTimerPause = function() {
if (!timerRunning) return;
timerElapsed = getElapsedMs();
timerRunning = false;
timerStartTs = null;
clearInterval(timerInterval);
timerInterval = null;

document.getElementById("mc-btn-start").disabled = false;
document.getElementById("mc-btn-start").textContent = "\u25b6 Resume";
document.getElementById("mc-btn-pause").disabled = true;
document.getElementById("mc-timer-display").classList.remove("mc-timer-running");
setStatusBadge("paused");
};

window.mcTimerStop = function() {
if (!timerRunning && timerElapsed === 0) return;
// capture final
if (timerRunning) {
timerElapsed = getElapsedMs();
timerRunning = false;
clearInterval(timerInterval);
timerInterval = null;
}
timerStopped = true;
updateTimerDisplay();

document.getElementById("mc-btn-start").disabled = true;
document.getElementById("mc-btn-pause").disabled = true;
document.getElementById("mc-btn-stop").disabled = true;
document.getElementById("mc-timer-display").classList.remove("mc-timer-running");
setStatusBadge("idle");

showResults();
};

window.mcTimerReset = function() {
timerRunning = false;
timerStopped = false;
timerElapsed = 0;
timerStartTs = null;
clearInterval(timerInterval);
timerInterval = null;

document.getElementById("mc-timer-time").textContent = "00:00";
document.getElementById("mc-timer-cost").textContent = "$0.00";
document.getElementById("mc-btn-start").disabled = false;
document.getElementById("mc-btn-start").textContent = "\u25b6 Start";
document.getElementById("mc-btn-pause").disabled = true;
document.getElementById("mc-btn-stop").disabled = true;
document.getElementById("mc-timer-display").classList.remove("mc-timer-running");
setStatusBadge("idle");
document.getElementById("mc-results").classList.remove("visible");
};

function setStatusBadge(state) {
var badge = document.getElementById("mc-status-badge");
badge.className = "mc-status " + state;
badge.textContent = state.charAt(0).toUpperCase() + state.slice(1);
}

/* ---- Results ---- */
var COMPARISONS = [
{ icon: "\u2615", name: "cups of coffee", price: 5 },
{ icon: "\ud83c\udfac", name: "months of Netflix", price: 15.49 },
{ icon: "\ud83c\udf55", name: "large pizzas", price: 18 },
{ icon: "\ud83d\udcda", name: "business books", price: 20 },
{ icon: "\ud83c\udfce\ufe0f", name: "Uber rides", price: 22 },
{ icon: "\ud83c\udfb5", name: "Spotify months", price: 10.99 },
{ icon: "\ud83e\udd50", name: "Starbucks lattes", price: 6.5 },
{ icon: "\ud83c\udf89", name: "board game nights (rental)", price: 12 },
];

function showResults() {
var ms = timerElapsed;
var rate = getTotalHourlyRate();
var totalPeople = getTotalAttendees();
var totalMins = ms / 60000;
var totalCost = rate * (ms / 3600000);

document.getElementById("mc-res-total").textContent = formatMoney(totalCost);
document.getElementById("mc-res-per-min").textContent = totalMins > 0 ? formatMoney(totalCost / totalMins) : "$0.00";
document.getElementById("mc-res-per-person").textContent = (totalPeople > 0 && totalCost > 0) ? formatMoney(totalCost / totalPeople) : "$0.00";

// Comparisons
var compList = document.getElementById("mc-comp-list");
compList.innerHTML = "";
COMPARISONS.forEach(function(c) {
var qty = Math.floor(totalCost / c.price);
if (qty < 1) return;
var item = document.createElement("div");
item.className = "mc-comp-item";
item.innerHTML =
'<span class="mc-comp-icon">' + c.icon + '</span>' +
'<span class="mc-comp-text">That\'s <strong>' + qty.toLocaleString() + ' ' + c.name + '</strong>' +
' ($' + c.price + ' each)</span>';
compList.appendChild(item);
});
if (compList.children.length === 0) {
compList.innerHTML = '<span style="color:var(--text-dim);font-size:0.88rem;">Run the meeting for a little longer to see comparisons!</span>';
}

document.getElementById("mc-results").classList.add("visible");
document.getElementById("mc-results").scrollIntoView({ behavior: "smooth", block: "nearest" });
}

/* ---- Init ---- */
buildPresets();
renderAttendees();
})();
</script>

</div>

## Related Articles

- [Best Remote Work Tools in 2026: The Complete Stack](/posts/best-remote-work-tools-2026/)
