---
title: "Days Until Calculator - Count Days to Any Date"
date: 2025-05-16
description: "Calculate how many days until any date. Count days between two dates. Includes business days, weekends, and weeks calculation."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "days-until-calculator"
ShowToc: false
cover:
  image: "/images/covers/days-until-calculator.png"
  alt: "Days Until Calculator"
---

<div id="duc-app">
<style>
#duc-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1a1a2e;
}
#duc-app * { box-sizing: border-box; }
#duc-app h2 {
font-size: 1.25rem;
font-weight: 700;
margin: 0 0 1rem 0;
color: #1a1a2e;
}
#duc-app .duc-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 1.5rem;
}
#duc-app .duc-tab {
padding: 0.6rem 1.1rem;
font-size: 0.9rem;
font-weight: 600;
color: #64748b;
background: none;
border: none;
border-bottom: 3px solid transparent;
cursor: pointer;
transition: all 0.2s;
margin-bottom: -2px;
}
#duc-app .duc-tab:hover { color: #3b82f6; }
#duc-app .duc-tab.active {
color: #3b82f6;
border-bottom-color: #3b82f6;
}
#duc-app .duc-panel { display: none; }
#duc-app .duc-panel.active { display: block; }
#duc-app .duc-card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 1.5rem;
margin-bottom: 1rem;
}
#duc-app label {
display: block;
font-size: 0.85rem;
font-weight: 600;
color: #374151;
margin-bottom: 0.4rem;
}
#duc-app input[type="date"],
#duc-app input[type="number"],
#duc-app select {
width: 100%;
padding: 0.6rem 0.85rem;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 0.95rem;
color: #1a1a2e;
background: #fff;
transition: border-color 0.2s;
}
#duc-app input[type="date"]:focus,
#duc-app input[type="number"]:focus,
#duc-app select:focus {
outline: none;
border-color: #3b82f6;
}
#duc-app .duc-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
margin-bottom: 1rem;
}
@media (max-width: 520px) {
#duc-app .duc-row { grid-template-columns: 1fr; }
}
#duc-app .duc-field { margin-bottom: 1rem; }
#duc-app .duc-check-row {
display: flex;
align-items: center;
gap: 0.5rem;
margin-bottom: 1rem;
}
#duc-app .duc-check-row input[type="checkbox"] {
width: 16px;
height: 16px;
cursor: pointer;
}
#duc-app .duc-check-row label {
margin: 0;
font-size: 0.88rem;
cursor: pointer;
}
#duc-app .duc-btn {
display: inline-block;
padding: 0.65rem 1.6rem;
background: #3b82f6;
color: #fff;
font-size: 0.95rem;
font-weight: 700;
border: none;
border-radius: 8px;
cursor: pointer;
transition: background 0.2s;
}
#duc-app .duc-btn:hover { background: #2563eb; }
#duc-app .duc-results {
display: none;
margin-top: 1.25rem;
}
#duc-app .duc-results.show { display: block; }
#duc-app .duc-result-grid {
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 0.75rem;
margin-bottom: 1rem;
}
@media (max-width: 520px) {
#duc-app .duc-result-grid { grid-template-columns: 1fr; }
}
#duc-app .duc-result-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 1rem;
text-align: center;
}
#duc-app .duc-result-box.highlight {
background: linear-gradient(135deg, #3b82f6 0%, #6366f1 100%);
border-color: transparent;
color: #fff;
}
#duc-app .duc-result-box .rval {
font-size: 2rem;
font-weight: 800;
line-height: 1.1;
}
#duc-app .duc-result-box.highlight .rval { color: #fff; }
#duc-app .duc-result-box .rlabel {
font-size: 0.78rem;
font-weight: 600;
color: #64748b;
margin-top: 0.2rem;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#duc-app .duc-result-box.highlight .rlabel { color: rgba(255,255,255,0.85); }
#duc-app .duc-progress-wrap {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-bottom: 0.75rem;
}
#duc-app .duc-progress-label {
display: flex;
justify-content: space-between;
font-size: 0.82rem;
font-weight: 600;
color: #64748b;
margin-bottom: 0.5rem;
}
#duc-app .duc-progress-bar {
height: 10px;
background: #e2e8f0;
border-radius: 99px;
overflow: hidden;
}
#duc-app .duc-progress-fill {
height: 100%;
background: linear-gradient(90deg, #3b82f6, #6366f1);
border-radius: 99px;
transition: width 0.6s ease;
}
#duc-app .duc-message {
background: #eff6ff;
border: 1px solid #bfdbfe;
border-radius: 8px;
padding: 0.75rem 1rem;
font-size: 0.9rem;
color: #1e40af;
margin-top: 0.5rem;
}
#duc-app .duc-presets {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-bottom: 1rem;
}
#duc-app .duc-preset-btn {
padding: 0.35rem 0.85rem;
font-size: 0.8rem;
font-weight: 600;
background: #fff;
border: 1.5px solid #d1d5db;
border-radius: 20px;
cursor: pointer;
color: #374151;
transition: all 0.2s;
}
#duc-app .duc-preset-btn:hover {
background: #3b82f6;
border-color: #3b82f6;
color: #fff;
}
#duc-app .duc-error {
color: #dc2626;
font-size: 0.85rem;
margin-top: 0.5rem;
display: none;
}
#duc-app .duc-error.show { display: block; }
#duc-app .duc-related {
margin-top: 2rem;
padding-top: 1.5rem;
border-top: 1px solid #e2e8f0;
}
#duc-app .duc-related h3 {
font-size: 1rem;
font-weight: 700;
margin: 0 0 0.75rem 0;
color: #374151;
}
#duc-app .duc-related-links {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
}
#duc-app .duc-related-links a {
display: inline-block;
padding: 0.4rem 0.9rem;
background: #f1f5f9;
border: 1px solid #e2e8f0;
border-radius: 6px;
font-size: 0.85rem;
color: #3b82f6;
text-decoration: none;
transition: all 0.2s;
}
#duc-app .duc-related-links a:hover {
background: #3b82f6;
color: #fff;
border-color: #3b82f6;
}
#duc-app .duc-add-result {
display: none;
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-top: 1rem;
font-size: 0.95rem;
}
#duc-app .duc-add-result.show { display: block; }
#duc-app .duc-add-result .big-date {
font-size: 1.4rem;
font-weight: 800;
color: #3b82f6;
margin-top: 0.3rem;
}
</style>

**Free tool** — instantly calculate days until any date, business days, and more.

<div class="duc-tabs">
<button class="duc-tab active" onclick="ducSwitchTab('countdown')">Days Until</button>
<button class="duc-tab" onclick="ducSwitchTab('between')">Days Between</button>
<button class="duc-tab" onclick="ducSwitchTab('addsubtract')">Add / Subtract Days</button>
</div>

<!-- PANEL 1: Days Until -->
<div class="duc-panel active" id="duc-panel-countdown">
<div class="duc-card">
<h2>How Many Days Until...?</h2>
<div style="margin-bottom:0.75rem;font-size:0.85rem;color:#64748b;">Quick presets:</div>
<div class="duc-presets">
<button class="duc-preset-btn" onclick="ducPreset('christmas')">Christmas</button>
<button class="duc-preset-btn" onclick="ducPreset('newyear')">New Year's Day</button>
<button class="duc-preset-btn" onclick="ducPreset('halloween')">Halloween</button>
<button class="duc-preset-btn" onclick="ducPreset('valentines')">Valentine's Day</button>
<button class="duc-preset-btn" onclick="ducPreset('thanksgiving')">Thanksgiving</button>
<button class="duc-preset-btn" onclick="ducPreset('july4')">July 4th</button>
<button class="duc-preset-btn" onclick="ducPreset('nextbday')">My Birthday</button>
</div>
<div class="duc-field">
<label for="duc-target-date">Target Date</label>
<input type="date" id="duc-target-date" />
</div>
<div class="duc-check-row">
<input type="checkbox" id="duc-excl-weekends" />
<label for="duc-excl-weekends">Count business days only (exclude Sat & Sun)</label>
</div>
<div class="duc-error" id="duc-cd-error">Please select a target date.</div>
<button class="duc-btn" onclick="ducCalcCountdown()">Calculate</button>
<div class="duc-results" id="duc-cd-results">
<div class="duc-result-grid">
<div class="duc-result-box highlight">
<div class="rval" id="duc-cd-days">—</div>
<div class="rlabel" id="duc-cd-days-label">Days Until</div>
</div>
<div class="duc-result-box">
<div class="rval" id="duc-cd-weeks">—</div>
<div class="rlabel">Weeks</div>
</div>
<div class="duc-result-box">
<div class="rval" id="duc-cd-months">—</div>
<div class="rlabel">Months (approx.)</div>
</div>
<div class="duc-result-box">
<div class="rval" id="duc-cd-bizdays">—</div>
<div class="rlabel">Business Days</div>
</div>
</div>
<div class="duc-progress-wrap">
<div class="duc-progress-label">
<span>Year Progress</span>
<span id="duc-year-pct">0%</span>
</div>
<div class="duc-progress-bar">
<div class="duc-progress-fill" id="duc-year-fill" style="width:0%"></div>
</div>
</div>
<div class="duc-message" id="duc-cd-message"></div>
</div>
</div>
</div>

<!-- PANEL 2: Days Between -->
<div class="duc-panel" id="duc-panel-between">
<div class="duc-card">
<h2>Days Between Two Dates</h2>
<div class="duc-row">
<div>
<label for="duc-from-date">From Date</label>
<input type="date" id="duc-from-date" />
</div>
<div>
<label for="duc-to-date">To Date</label>
<input type="date" id="duc-to-date" />
</div>
</div>
<div class="duc-check-row">
<input type="checkbox" id="duc-btw-excl" />
<label for="duc-btw-excl">Exclude weekends</label>
</div>
<div class="duc-error" id="duc-btw-error">Please select both dates.</div>
<button class="duc-btn" onclick="ducCalcBetween()">Calculate</button>
<div class="duc-results" id="duc-btw-results">
<div class="duc-result-grid">
<div class="duc-result-box highlight">
<div class="rval" id="duc-btw-days">—</div>
<div class="rlabel" id="duc-btw-days-label">Total Days</div>
</div>
<div class="duc-result-box">
<div class="rval" id="duc-btw-weeks">—</div>
<div class="rlabel">Weeks</div>
</div>
<div class="duc-result-box">
<div class="rval" id="duc-btw-months">—</div>
<div class="rlabel">Months (approx.)</div>
</div>
<div class="duc-result-box">
<div class="rval" id="duc-btw-bizdays">—</div>
<div class="rlabel">Business Days</div>
</div>
</div>
<div class="duc-message" id="duc-btw-message"></div>
</div>
</div>
</div>

<!-- PANEL 3: Add / Subtract -->
<div class="duc-panel" id="duc-panel-addsubtract">
<div class="duc-card">
<h2>Add or Subtract Days from a Date</h2>
<div class="duc-row">
<div>
<label for="duc-base-date">Start Date</label>
<input type="date" id="duc-base-date" />
</div>
<div>
<label for="duc-add-num">Number of Days</label>
<input type="number" id="duc-add-num" placeholder="e.g. 30" min="0" max="9999" />
</div>
</div>
<div class="duc-field">
<label for="duc-add-op">Operation</label>
<select id="duc-add-op">
<option value="add">Add days (future date)</option>
<option value="sub">Subtract days (past date)</option>
</select>
</div>
<div class="duc-check-row">
<input type="checkbox" id="duc-add-excl" />
<label for="duc-add-excl">Skip weekends (business days only)</label>
</div>
<div class="duc-error" id="duc-add-error">Please fill in the start date and number of days.</div>
<button class="duc-btn" onclick="ducCalcAdd()">Calculate</button>
<div class="duc-add-result" id="duc-add-result">
<div style="font-size:0.85rem;color:#64748b;font-weight:600;">Result Date</div>
<div class="big-date" id="duc-add-result-date">—</div>
<div style="font-size:0.85rem;color:#64748b;margin-top:0.5rem;" id="duc-add-result-note"></div>
</div>
</div>
</div>

<div class="duc-related">
<h3>Related Tools</h3>
<div class="duc-related-links">
<a href="/tools/timezone-converter/">Time Zone Converter</a>
<a href="/tools/age-calculator/">Age Calculator</a>
<a href="/tools/hourly-to-salary-calculator/">Work Hours Calculator</a>
<a href="/tools/date-calculator/">Deadline Calculator</a>
<a href="/tools/date-calculator/">Week Number Calculator</a>
</div>
</div>

<script>
(function() {
// Tab switching
window.ducSwitchTab = function(tab) {
document.querySelectorAll('#duc-app .duc-tab').forEach(function(t, i) {
t.classList.toggle('active', ['countdown','between','addsubtract'][i] === tab);
});
document.querySelectorAll('#duc-app .duc-panel').forEach(function(p) {
p.classList.remove('active');
});
document.getElementById('duc-panel-' + tab).classList.add('active');
};

// Initialize today's date defaults
var today = new Date();
var todayStr = today.toISOString().slice(0,10);
document.getElementById('duc-from-date').value = todayStr;
document.getElementById('duc-base-date').value = todayStr;

// Presets
window.ducPreset = function(key) {
var now = new Date();
var y = now.getFullYear();
var d;
switch(key) {
case 'christmas':    d = new Date(y, 11, 25); break;
case 'newyear':      d = new Date(y + 1, 0, 1); break;
case 'halloween':    d = new Date(y, 9, 31); break;
case 'valentines':   d = new Date(now.getMonth() >= 1 && now.getDate() > 14 ? y+1 : y, 1, 14); break;
case 'thanksgiving': {
// 4th Thursday of November
var nov1 = new Date(y, 10, 1);
var day1 = nov1.getDay();
var thu = 4;
var first = (thu - day1 + 7) % 7 + 1;
d = new Date(y, 10, first + 21);
break;
}
case 'july4':        d = new Date(y, 6, 4); break;
case 'nextbday': {
var bStr = localStorage.getItem('duc_bday');
var month, dayN;
if (bStr) {
var parts = bStr.split('-');
month = parseInt(parts[0]) - 1;
dayN  = parseInt(parts[1]);
} else {
var input = prompt('Enter your birthday (MM-DD), e.g. 08-15:');
if (!input) return;
var p = input.replace('/','-').split('-');
month = parseInt(p[0]) - 1;
dayN  = parseInt(p[1]);
localStorage.setItem('duc_bday', (month+1) + '-' + dayN);
}
d = new Date(y, month, dayN);
if (d <= now) d = new Date(y + 1, month, dayN);
break;
}
default: return;
}
// If the date has passed this year, move to next year for relevant ones
if (['christmas','halloween','july4','thanksgiving'].indexOf(key) !== -1 && d < now) {
d.setFullYear(y + 1);
}
document.getElementById('duc-target-date').value = d.toISOString().slice(0,10);
ducCalcCountdown();
};

// Business days between two Date objects
function bizDaysBetween(a, b) {
var start = new Date(Math.min(a,b));
var end   = new Date(Math.max(a,b));
var count = 0;
var cur   = new Date(start);
cur.setDate(cur.getDate() + 1);
while (cur <= end) {
var wd = cur.getDay();
if (wd !== 0 && wd !== 6) count++;
cur.setDate(cur.getDate() + 1);
}
return count;
}

function daysDiff(a, b) {
return Math.round((b - a) / 86400000);
}

function fmtDate(d) {
return d.toLocaleDateString('en-US', { weekday:'long', year:'numeric', month:'long', day:'numeric' });
}

function yearProgress() {
var now = new Date();
var start = new Date(now.getFullYear(), 0, 1);
var end   = new Date(now.getFullYear() + 1, 0, 1);
return Math.round(((now - start) / (end - start)) * 100);
}

function getMessage(days) {
if (days < 0)  return 'That date has already passed (' + Math.abs(days) + ' days ago).';
if (days === 0) return 'That date is TODAY!';
if (days === 1) return 'Tomorrow!';
if (days <= 7)  return 'Less than a week away — almost there!';
if (days <= 30) return 'Coming up this month. Stay on track!';
if (days <= 90) return 'A few months away. Good time to plan ahead.';
if (days <= 365) return 'Less than a year to go. Set your milestones!';
return 'More than a year away. Break it into smaller goals.';
}

// Panel 1: Countdown
window.ducCalcCountdown = function() {
var targetVal = document.getElementById('duc-target-date').value;
var err = document.getElementById('duc-cd-error');
if (!targetVal) { err.classList.add('show'); return; }
err.classList.remove('show');

var target = new Date(targetVal + 'T00:00:00');
var now    = new Date(); now.setHours(0,0,0,0);
var totalDays = daysDiff(now, target);
var exclWknd  = document.getElementById('duc-excl-weekends').checked;
var displayDays = exclWknd ? bizDaysBetween(now, target) * (totalDays < 0 ? -1 : 1) : totalDays;

document.getElementById('duc-cd-days').textContent   = Math.abs(displayDays).toLocaleString();
document.getElementById('duc-cd-days-label').textContent = totalDays < 0 ? (exclWknd ? 'Business Days Ago' : 'Days Ago') : (exclWknd ? 'Business Days Until' : 'Days Until');
document.getElementById('duc-cd-weeks').textContent  = Math.abs(Math.floor(totalDays / 7)).toLocaleString();
document.getElementById('duc-cd-months').textContent = Math.abs(Math.floor(totalDays / 30.44)).toLocaleString();
document.getElementById('duc-cd-bizdays').textContent = bizDaysBetween(now, target).toLocaleString();

var pct = yearProgress();
document.getElementById('duc-year-pct').textContent = pct + '%';
document.getElementById('duc-year-fill').style.width = pct + '%';
document.getElementById('duc-cd-message').textContent = getMessage(totalDays);

document.getElementById('duc-cd-results').classList.add('show');
};

// Panel 2: Between
window.ducCalcBetween = function() {
var fromVal = document.getElementById('duc-from-date').value;
var toVal   = document.getElementById('duc-to-date').value;
var err = document.getElementById('duc-btw-error');
if (!fromVal || !toVal) { err.classList.add('show'); return; }
err.classList.remove('show');

var from = new Date(fromVal + 'T00:00:00');
var to   = new Date(toVal   + 'T00:00:00');
var totalDays = Math.abs(daysDiff(from, to));
var exclWknd  = document.getElementById('duc-btw-excl').checked;
var displayDays = exclWknd ? bizDaysBetween(from, to) : totalDays;
var earlier = from <= to ? fmtDate(from) : fmtDate(to);
var later   = from <= to ? fmtDate(to)   : fmtDate(from);

document.getElementById('duc-btw-days').textContent  = displayDays.toLocaleString();
document.getElementById('duc-btw-days-label').textContent = exclWknd ? 'Business Days' : 'Total Days';
document.getElementById('duc-btw-weeks').textContent  = Math.floor(totalDays / 7).toLocaleString();
document.getElementById('duc-btw-months').textContent = Math.floor(totalDays / 30.44).toLocaleString();
document.getElementById('duc-btw-bizdays').textContent = bizDaysBetween(from, to).toLocaleString();
document.getElementById('duc-btw-message').textContent =
'From ' + earlier + ' to ' + later + '.';

document.getElementById('duc-btw-results').classList.add('show');
};

// Panel 3: Add/Subtract
window.ducCalcAdd = function() {
var baseVal = document.getElementById('duc-base-date').value;
var numVal  = document.getElementById('duc-add-num').value;
var err = document.getElementById('duc-add-error');
if (!baseVal || numVal === '') { err.classList.add('show'); return; }
err.classList.remove('show');

var base    = new Date(baseVal + 'T00:00:00');
var num     = parseInt(numVal, 10);
var op      = document.getElementById('duc-add-op').value;
var skipWknd = document.getElementById('duc-add-excl').checked;
var result  = new Date(base);
var direction = op === 'add' ? 1 : -1;

if (skipWknd) {
var remaining = num;
while (remaining > 0) {
result.setDate(result.getDate() + direction);
var wd = result.getDay();
if (wd !== 0 && wd !== 6) remaining--;
}
} else {
result.setDate(result.getDate() + direction * num);
}

document.getElementById('duc-add-result-date').textContent = fmtDate(result);
document.getElementById('duc-add-result-note').textContent =
(op === 'add' ? 'Adding ' : 'Subtracting ') + num +
(skipWknd ? ' business days' : ' calendar days') +
(op === 'add' ? ' from ' : ' before ') + fmtDate(base) + '.';
document.getElementById('duc-add-result').classList.add('show');
};

// Enter on inputs triggers calc
['duc-target-date'].forEach(function(id) {
var el = document.getElementById(id);
if (el) el.addEventListener('change', ducCalcCountdown);
});
document.getElementById('duc-to-date').addEventListener('change', ducCalcBetween);
})();
</script>
</div>

---

## Related Tools

> [Age Calculator](/tools/age-calculator/)
> [Countdown Timer](/tools/countdown-timer/)
> [Date Calculator](/tools/date-calculator/)

