---
title: "Date Calculator"
slug: "date-calculator"
description: "Free date calculator. Find the difference between two dates, add or subtract days from a date, and calculate business days."
categories: ["Free Tools"]
date: 2025-05-16
ShowToc: false
cover:
  image: "/images/covers/date-calculator.png"
---

Free online date calculator with three modes: find the difference between two dates, add or subtract time from a date, and calculate business days. No sign-up required.

<div id="dt-app">
<style>
#dt-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 700px;
margin: 0 auto;
color: #1a1a2e;
}
#dt-app * {
box-sizing: border-box;
}
#dt-app .dt-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e0e0e0;
margin-bottom: 24px;
}
#dt-app .dt-tab {
flex: 1;
padding: 12px 8px;
background: none;
border: none;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
font-size: 14px;
font-weight: 600;
color: #777;
cursor: pointer;
transition: all 0.2s;
text-align: center;
}
#dt-app .dt-tab:hover {
color: #4f46e5;
background: #f5f3ff;
}
#dt-app .dt-tab.active {
color: #4f46e5;
border-bottom-color: #4f46e5;
background: none;
}
#dt-app .dt-panel {
display: none;
}
#dt-app .dt-panel.active {
display: block;
}
#dt-app .dt-card {
background: #f9f9ff;
border: 1px solid #e8e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
}
#dt-app .dt-row {
display: flex;
gap: 16px;
flex-wrap: wrap;
margin-bottom: 16px;
align-items: flex-end;
}
#dt-app .dt-field {
display: flex;
flex-direction: column;
gap: 6px;
flex: 1;
min-width: 160px;
}
#dt-app .dt-field label {
font-size: 13px;
font-weight: 600;
color: #555;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#dt-app .dt-field input,
#dt-app .dt-field select {
padding: 10px 12px;
border: 1.5px solid #d0d0e0;
border-radius: 8px;
font-size: 15px;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.2s;
width: 100%;
}
#dt-app .dt-field input:focus,
#dt-app .dt-field select:focus {
border-color: #4f46e5;
}
#dt-app .dt-btn {
display: inline-block;
padding: 11px 28px;
background: #4f46e5;
color: #fff;
border: none;
border-radius: 8px;
font-size: 15px;
font-weight: 600;
cursor: pointer;
transition: background 0.2s;
}
#dt-app .dt-btn:hover {
background: #4338ca;
}
#dt-app .dt-result {
background: #fff;
border: 1.5px solid #4f46e5;
border-radius: 10px;
padding: 20px 24px;
margin-top: 16px;
display: none;
}
#dt-app .dt-result.show {
display: block;
}
#dt-app .dt-result-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
gap: 12px;
margin-bottom: 12px;
}
#dt-app .dt-result-item {
background: #f5f3ff;
border-radius: 8px;
padding: 14px 12px;
text-align: center;
}
#dt-app .dt-result-item .val {
font-size: 26px;
font-weight: 800;
color: #4f46e5;
line-height: 1.1;
}
#dt-app .dt-result-item .lbl {
font-size: 12px;
color: #666;
margin-top: 4px;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#dt-app .dt-result-main {
font-size: 17px;
font-weight: 700;
color: #1a1a2e;
margin-bottom: 8px;
}
#dt-app .dt-result-sub {
font-size: 14px;
color: #555;
line-height: 1.6;
}
#dt-app .dt-dow-badge {
display: inline-block;
background: #e0f2fe;
color: #0369a1;
border-radius: 6px;
padding: 3px 10px;
font-size: 13px;
font-weight: 700;
margin-left: 6px;
}
#dt-app .dt-error {
color: #dc2626;
font-size: 14px;
margin-top: 10px;
display: none;
}
#dt-app .dt-error.show {
display: block;
}
#dt-app .dt-op-toggle {
display: flex;
gap: 0;
border: 1.5px solid #d0d0e0;
border-radius: 8px;
overflow: hidden;
background: #fff;
}
#dt-app .dt-op-btn {
flex: 1;
padding: 10px;
background: none;
border: none;
font-size: 14px;
font-weight: 600;
color: #777;
cursor: pointer;
transition: all 0.2s;
}
#dt-app .dt-op-btn.active {
background: #4f46e5;
color: #fff;
}
#dt-app .dt-related {
margin-top: 32px;
padding-top: 24px;
border-top: 1px solid #e0e0e0;
}
#dt-app .dt-related h3 {
font-size: 16px;
font-weight: 700;
margin: 0 0 14px;
color: #1a1a2e;
}
#dt-app .dt-related-links {
display: flex;
gap: 12px;
flex-wrap: wrap;
}
#dt-app .dt-related-link {
display: inline-block;
padding: 9px 18px;
background: #f5f3ff;
border: 1.5px solid #c7d2fe;
border-radius: 8px;
color: #4f46e5;
font-size: 14px;
font-weight: 600;
text-decoration: none;
transition: background 0.2s;
}
#dt-app .dt-related-link:hover {
background: #ede9fe;
}
#dt-app .dt-hint {
font-size: 13px;
color: #888;
margin-top: 10px;
}
@media (max-width: 500px) {
#dt-app .dt-tab { font-size: 12px; padding: 10px 4px; }
#dt-app .dt-result-item .val { font-size: 20px; }
}
</style>

<!-- Tab navigation -->
<div class="dt-tabs">
<button class="dt-tab active" onclick="dtSwitchTab(0, this)">Date Difference</button>
<button class="dt-tab" onclick="dtSwitchTab(1, this)">Add / Subtract</button>
<button class="dt-tab" onclick="dtSwitchTab(2, this)">Business Days</button>
</div>

<!-- Panel 0: Date Difference -->
<div class="dt-panel active" id="dt-panel-0">
<div class="dt-card">
<div class="dt-row">
<div class="dt-field">
<label>Start Date</label>
<input type="date" id="dd-start" />
</div>
<div class="dt-field">
<label>End Date</label>
<input type="date" id="dd-end" />
</div>
</div>
<button class="dt-btn" onclick="dtCalcDiff()">Calculate Difference</button>
<div class="dt-error" id="dd-error">Please enter both dates.</div>
</div>
<div class="dt-result" id="dd-result">
<div class="dt-result-main" id="dd-main"></div>
<div class="dt-result-grid" id="dd-grid"></div>
<div class="dt-result-sub" id="dd-sub"></div>
</div>
</div>

<!-- Panel 1: Add / Subtract -->
<div class="dt-panel" id="dt-panel-1">
<div class="dt-card">
<div class="dt-row">
<div class="dt-field">
<label>Base Date</label>
<input type="date" id="as-date" />
</div>
</div>
<div class="dt-row">
<div class="dt-field" style="max-width:100px;">
<label>Amount</label>
<input type="number" id="as-amount" value="30" min="0" max="9999" />
</div>
<div class="dt-field" style="max-width:160px;">
<label>Unit</label>
<select id="as-unit">
<option value="days">Days</option>
<option value="weeks">Weeks</option>
<option value="months">Months</option>
<option value="years">Years</option>
</select>
</div>
<div class="dt-field" style="max-width:180px;">
<label>Operation</label>
<div class="dt-op-toggle">
<button class="dt-op-btn active" id="as-add-btn" onclick="dtSetOp('add')">+ Add</button>
<button class="dt-op-btn" id="as-sub-btn" onclick="dtSetOp('sub')">− Subtract</button>
</div>
</div>
</div>
<button class="dt-btn" onclick="dtCalcAddSub()">Calculate Date</button>
<div class="dt-error" id="as-error">Please enter a base date and amount.</div>
</div>
<div class="dt-result" id="as-result">
<div class="dt-result-main" id="as-main"></div>
<div class="dt-result-sub" id="as-sub"></div>
</div>
</div>

<!-- Panel 2: Business Days -->
<div class="dt-panel" id="dt-panel-2">
<div class="dt-card">
<div class="dt-row">
<div class="dt-field">
<label>Start Date</label>
<input type="date" id="bd-start" />
</div>
<div class="dt-field">
<label>End Date</label>
<input type="date" id="bd-end" />
</div>
</div>
<p class="dt-hint">Weekends (Saturday &amp; Sunday) are excluded. Public holidays are not automatically excluded.</p>
<button class="dt-btn" onclick="dtCalcBiz()">Calculate Business Days</button>
<div class="dt-error" id="bd-error">Please enter both dates.</div>
</div>
<div class="dt-result" id="bd-result">
<div class="dt-result-main" id="bd-main"></div>
<div class="dt-result-grid" id="bd-grid"></div>
<div class="dt-result-sub" id="bd-sub"></div>
</div>
</div>

<!-- Related tools -->
<div class="dt-related">
<h3>Related Free Tools</h3>
<div class="dt-related-links">
<a class="dt-related-link" href="/tools/age-calculator/">Age Calculator</a>
<a class="dt-related-link" href="/tools/calendar-generator/">Calendar Generator</a>
</div>
</div>

<script>
(function() {
var _op = 'add';
var DAYS = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
var MONTHS_SHORT = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];

// Set today as default for all date inputs
var today = new Date();
var todayStr = dtFmtISO(today);
document.getElementById('dd-start').value = todayStr;
document.getElementById('dd-end').value = todayStr;
document.getElementById('as-date').value = todayStr;
document.getElementById('bd-start').value = todayStr;
document.getElementById('bd-end').value = todayStr;

function dtFmtISO(d) {
var y = d.getFullYear();
var m = String(d.getMonth()+1).padStart(2,'0');
var day = String(d.getDate()).padStart(2,'0');
return y+'-'+m+'-'+day;
}

function dtFmtDisplay(d) {
return DAYS[d.getDay()]+', '+MONTHS_SHORT[d.getMonth()]+' '+d.getDate()+', '+d.getFullYear();
}

function dtParseDate(str) {
if (!str) return null;
var p = str.split('-');
if (p.length !== 3) return null;
return new Date(+p[0], +p[1]-1, +p[2]);
}

window.dtSwitchTab = function(idx, btn) {
var tabs = document.querySelectorAll('#dt-app .dt-tab');
var panels = document.querySelectorAll('#dt-app .dt-panel');
tabs.forEach(function(t){ t.classList.remove('active'); });
panels.forEach(function(p){ p.classList.remove('active'); });
btn.classList.add('active');
document.getElementById('dt-panel-'+idx).classList.add('active');
};

window.dtSetOp = function(op) {
_op = op;
document.getElementById('as-add-btn').classList.toggle('active', op==='add');
document.getElementById('as-sub-btn').classList.toggle('active', op==='sub');
};

window.dtCalcDiff = function() {
var err = document.getElementById('dd-error');
var res = document.getElementById('dd-result');
err.classList.remove('show');
res.classList.remove('show');

var s = dtParseDate(document.getElementById('dd-start').value);
var e = dtParseDate(document.getElementById('dd-end').value);
if (!s || !e) { err.classList.add('show'); return; }

var sign = 1;
if (e < s) { sign = -1; var tmp = s; s = e; e = tmp; }

var msPerDay = 86400000;
var totalDays = Math.round((e - s) / msPerDay);
var totalHours = totalDays * 24;
var totalWeeks = (totalDays / 7).toFixed(2);

// Years/months/days breakdown
var y = e.getFullYear() - s.getFullYear();
var mo = e.getMonth() - s.getMonth();
var da = e.getDate() - s.getDate();
if (da < 0) {
mo--;
var prev = new Date(e.getFullYear(), e.getMonth(), 0);
da += prev.getDate();
}
if (mo < 0) { y--; mo += 12; }

var mainTxt = sign >= 0
? dtFmtDisplay(s)+' &rarr; '+dtFmtDisplay(e)
: dtFmtDisplay(e)+' &rarr; '+dtFmtDisplay(s)+' <span style="color:#dc2626;font-size:13px;">(end is before start)</span>';

document.getElementById('dd-main').innerHTML = mainTxt;

var grid = document.getElementById('dd-grid');
grid.innerHTML = [
{v: y, l: 'Years'},
{v: mo, l: 'Months'},
{v: da, l: 'Days (rem.)'},
{v: totalDays, l: 'Total Days'},
{v: totalWeeks, l: 'Total Weeks'},
{v: totalHours.toLocaleString(), l: 'Total Hours'}
].map(function(i){
return '<div class="dt-result-item"><div class="val">'+i.v+'</div><div class="lbl">'+i.l+'</div></div>';
}).join('');

var s0 = dtParseDate(document.getElementById('dd-start').value);
var e0 = dtParseDate(document.getElementById('dd-end').value);
document.getElementById('dd-sub').innerHTML =
'Start: <strong>'+dtFmtDisplay(s0)+'</strong><br>'+
'End: <strong>'+dtFmtDisplay(e0)+'</strong>';

res.classList.add('show');
};

window.dtCalcAddSub = function() {
var err = document.getElementById('as-error');
var res = document.getElementById('as-result');
err.classList.remove('show');
res.classList.remove('show');

var base = dtParseDate(document.getElementById('as-date').value);
var amt = parseInt(document.getElementById('as-amount').value, 10);
var unit = document.getElementById('as-unit').value;
if (!base || isNaN(amt) || amt < 0) { err.classList.add('show'); return; }

var mul = _op === 'add' ? 1 : -1;
var result = new Date(base);

if (unit === 'days') {
result.setDate(result.getDate() + mul * amt);
} else if (unit === 'weeks') {
result.setDate(result.getDate() + mul * amt * 7);
} else if (unit === 'months') {
result.setMonth(result.getMonth() + mul * amt);
} else if (unit === 'years') {
result.setFullYear(result.getFullYear() + mul * amt);
}

var opLabel = _op === 'add' ? '+' : '−';
var unitLabel = amt === 1 ? unit.replace(/s$/, '') : unit;

document.getElementById('as-main').innerHTML =
dtFmtDisplay(base)+' <span style="color:#4f46e5;">'+opLabel+' '+amt+' '+unitLabel+'</span>';
document.getElementById('as-sub').innerHTML =
'Result: <strong style="font-size:20px;">'+dtFmtDisplay(result)+'</strong>' +
'<span class="dt-dow-badge">'+DAYS[result.getDay()]+'</span>';

res.classList.add('show');
};

window.dtCalcBiz = function() {
var err = document.getElementById('bd-error');
var res = document.getElementById('bd-result');
err.classList.remove('show');
res.classList.remove('show');

var s = dtParseDate(document.getElementById('bd-start').value);
var e = dtParseDate(document.getElementById('bd-end').value);
if (!s || !e) { err.classList.add('show'); return; }

var sign = 1;
if (e < s) { sign = -1; var tmp = s; s = e; e = tmp; }

var msPerDay = 86400000;
var totalDays = Math.round((e - s) / msPerDay) + 1; // inclusive
var bizDays = 0, weekendDays = 0;
var cur = new Date(s);
for (var i = 0; i < totalDays; i++) {
var dow = cur.getDay();
if (dow === 0 || dow === 6) weekendDays++;
else bizDays++;
cur.setDate(cur.getDate() + 1);
}

var s0 = dtParseDate(document.getElementById('bd-start').value);
var e0 = dtParseDate(document.getElementById('bd-end').value);

document.getElementById('bd-main').innerHTML =
dtFmtDisplay(s0)+' &rarr; '+dtFmtDisplay(e0);

var grid = document.getElementById('bd-grid');
grid.innerHTML = [
{v: bizDays, l: 'Business Days'},
{v: weekendDays, l: 'Weekend Days'},
{v: totalDays, l: 'Total Days (incl.)'}
].map(function(i){
return '<div class="dt-result-item"><div class="val">'+i.v+'</div><div class="lbl">'+i.l+'</div></div>';
}).join('');

var wks = Math.floor(bizDays / 5);
var rem = bizDays % 5;
document.getElementById('bd-sub').innerHTML =
'That is approximately <strong>'+wks+' week'+(wks!==1?'s':'')+
(rem ? ' and '+rem+' day'+(rem!==1?'s':'') : '')+'</strong> of business time.<br>'+
'<span style="font-size:13px;color:#888;">Weekends excluded. Public holidays not included.</span>';

res.classList.add('show');
};
})();
</script>
</div>

## How to Use the Date Calculator

**Mode 1 — Date Difference:** Enter a start date and an end date, then click "Calculate Difference." The tool returns the gap in years, months, days, total days, weeks, and hours.

**Mode 2 — Add / Subtract:** Pick a base date, choose an amount and unit (days, weeks, months, or years), select Add or Subtract, and click "Calculate Date." The resulting date and day of week are displayed instantly.

**Mode 3 — Business Days:** Enter two dates to count how many working days (Monday–Friday) fall between them, excluding weekends. Public holidays must be excluded manually.

### Frequently Asked Questions

**How is the date difference calculated?**
The calculator uses the exact calendar difference. Years and months are counted by calendar position; remaining days are counted precisely including leap years.

**Are public holidays excluded in Business Days mode?**
No. The tool automatically removes Saturdays and Sundays. If you need to exclude local public holidays, subtract them from the business-day count manually.

**Can I subtract dates across different years?**
Yes. The calculator handles multi-year spans, leap years, and month-length differences automatically.

**What is the day of week used for?**
Every result shows the day of the week (e.g., Monday) for quick reference — useful for scheduling meetings or deadlines.

---

*Related: [Age Calculator](/tools/age-calculator/) · [Calendar Generator](/tools/calendar-generator/)*
