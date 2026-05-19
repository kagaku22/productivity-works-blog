---
title: "Age Calculator - Free Online Age & Birthday Tool"
date: 2025-05-16
description: "Calculate your exact age in years, months, days, hours, and minutes. Find days until next birthday, day of the week you were born, and more."
categories: ["Free Tools"]
tags: ["age calculator", "birthday", "date calculator", "how old am I", "days between dates"]
slug: "age-calculator"
aliases: ["/tools/age-calculator/", "/tools/date-calculator/"]
cover:
  image: "/images/covers/age-calculator.png"
  alt: "Age Calculator"
ShowToc: false
---

<div id="age-app">

<style>
#age-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1f2937;
}

/* Mode Tabs */
#age-app .mode-tabs {
display: flex;
gap: 0;
margin-bottom: 24px;
border-radius: 10px;
overflow: hidden;
border: 2px solid #f59e0b;
}
#age-app .mode-tab {
flex: 1;
padding: 12px 8px;
background: #fff;
border: none;
cursor: pointer;
font-size: 0.95rem;
font-weight: 600;
color: #92400e;
transition: background 0.2s, color 0.2s;
text-align: center;
}
#age-app .mode-tab.active {
background: #f59e0b;
color: #fff;
}
#age-app .mode-tab:hover:not(.active) {
background: #fef3c7;
}

/* Input card */
#age-app .input-card {
background: #fffbeb;
border: 1px solid #fde68a;
border-radius: 14px;
padding: 28px 24px;
margin-bottom: 24px;
}
#age-app .input-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
align-items: end;
}
#age-app .input-group {
display: flex;
flex-direction: column;
gap: 6px;
}
#age-app .input-group label {
font-size: 0.85rem;
font-weight: 600;
color: #92400e;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#age-app .input-group input[type="date"] {
padding: 10px 14px;
border: 2px solid #fcd34d;
border-radius: 8px;
font-size: 1rem;
background: #fff;
color: #1f2937;
outline: none;
width: 100%;
box-sizing: border-box;
transition: border-color 0.2s;
}
#age-app .input-group input[type="date"]:focus {
border-color: #f59e0b;
}
#age-app .calc-btn {
padding: 12px 28px;
background: #f59e0b;
color: #fff;
border: none;
border-radius: 8px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
white-space: nowrap;
}
#age-app .calc-btn:hover {
background: #d97706;
transform: translateY(-1px);
}
#age-app .calc-btn:active {
transform: translateY(0);
}
#age-app .reset-link {
font-size: 0.85rem;
color: #b45309;
cursor: pointer;
text-decoration: underline;
margin-top: 4px;
display: inline-block;
}

/* Results */
#age-app .results-section {
display: none;
}
#age-app .results-section.visible {
display: block;
}

/* Hero age display */
#age-app .hero-age {
background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
border-radius: 14px;
padding: 28px 24px;
text-align: center;
color: #fff;
margin-bottom: 20px;
}
#age-app .hero-age .age-main {
font-size: 3rem;
font-weight: 800;
line-height: 1.1;
margin-bottom: 4px;
}
#age-app .hero-age .age-sub {
font-size: 1.1rem;
opacity: 0.9;
}

/* Stat cards grid */
#age-app .stats-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 14px;
margin-bottom: 20px;
}
#age-app .stat-card {
background: #fff;
border: 1px solid #fde68a;
border-radius: 12px;
padding: 18px 14px;
text-align: center;
transition: box-shadow 0.2s;
}
#age-app .stat-card:hover {
box-shadow: 0 4px 16px rgba(245,158,11,0.15);
}
#age-app .stat-card .stat-value {
font-size: 1.5rem;
font-weight: 800;
color: #d97706;
word-break: break-all;
line-height: 1.2;
}
#age-app .stat-card .stat-label {
font-size: 0.8rem;
color: #6b7280;
margin-top: 4px;
font-weight: 500;
}

/* Info cards (birthday facts, zodiac, etc.) */
#age-app .info-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 14px;
margin-bottom: 20px;
}
#age-app .info-card {
background: #fff;
border: 1px solid #fde68a;
border-radius: 12px;
padding: 18px 16px;
}
#age-app .info-card .info-icon {
font-size: 1.6rem;
margin-bottom: 8px;
}
#age-app .info-card .info-title {
font-size: 0.78rem;
font-weight: 700;
color: #92400e;
text-transform: uppercase;
letter-spacing: 0.06em;
margin-bottom: 4px;
}
#age-app .info-card .info-value {
font-size: 1.05rem;
font-weight: 700;
color: #1f2937;
}
#age-app .info-card .info-sub {
font-size: 0.82rem;
color: #6b7280;
margin-top: 2px;
}

/* Birthday countdown */
#age-app .countdown-card {
background: linear-gradient(135deg, #fffbeb 0%, #fef3c7 100%);
border: 2px solid #fcd34d;
border-radius: 12px;
padding: 18px 16px;
display: flex;
align-items: center;
gap: 16px;
margin-bottom: 20px;
}
#age-app .countdown-card .cd-icon {
font-size: 2.2rem;
flex-shrink: 0;
}
#age-app .countdown-card .cd-text .cd-title {
font-size: 0.82rem;
font-weight: 700;
color: #92400e;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#age-app .countdown-card .cd-text .cd-value {
font-size: 1.3rem;
font-weight: 800;
color: #b45309;
}
#age-app .countdown-card .cd-text .cd-sub {
font-size: 0.82rem;
color: #78716c;
}

/* Milestones */
#age-app .milestones-section {
background: #fff;
border: 1px solid #fde68a;
border-radius: 14px;
padding: 22px 20px;
margin-bottom: 20px;
}
#age-app .milestones-section h3 {
font-size: 1rem;
font-weight: 700;
color: #92400e;
margin: 0 0 16px 0;
display: flex;
align-items: center;
gap: 8px;
}
#age-app .milestone-list {
display: flex;
flex-direction: column;
gap: 10px;
}
#age-app .milestone-item {
display: flex;
align-items: center;
gap: 12px;
padding: 10px 14px;
border-radius: 8px;
font-size: 0.9rem;
}
#age-app .milestone-item.passed {
background: #f0fdf4;
border: 1px solid #bbf7d0;
}
#age-app .milestone-item.upcoming {
background: #fffbeb;
border: 1px solid #fde68a;
}
#age-app .milestone-item .ms-badge {
font-size: 1.2rem;
flex-shrink: 0;
}
#age-app .milestone-item .ms-body {
flex: 1;
}
#age-app .milestone-item .ms-label {
font-weight: 700;
color: #1f2937;
}
#age-app .milestone-item .ms-date {
font-size: 0.78rem;
color: #6b7280;
}
#age-app .milestone-item .ms-status {
font-size: 0.78rem;
font-weight: 700;
flex-shrink: 0;
}
#age-app .milestone-item.passed .ms-status { color: #16a34a; }
#age-app .milestone-item.upcoming .ms-status { color: #d97706; }

/* Date diff mode */
#age-app .diff-result {
background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
border-radius: 14px;
padding: 28px 24px;
text-align: center;
color: #fff;
margin-bottom: 20px;
}
#age-app .diff-result .diff-main {
font-size: 2.4rem;
font-weight: 800;
line-height: 1.1;
margin-bottom: 6px;
}
#age-app .diff-result .diff-sub {
font-size: 1rem;
opacity: 0.9;
}
#age-app .diff-stats-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 14px;
margin-bottom: 20px;
}

/* Error */
#age-app .error-msg {
background: #fef2f2;
border: 1px solid #fecaca;
border-radius: 8px;
padding: 12px 16px;
color: #dc2626;
font-size: 0.9rem;
margin-top: 12px;
display: none;
}
#age-app .error-msg.visible {
display: block;
}

/* Responsive */
@media (max-width: 600px) {
#age-app .input-grid {
grid-template-columns: 1fr;
}
#age-app .stats-grid {
grid-template-columns: repeat(2, 1fr);
}
#age-app .info-grid {
grid-template-columns: 1fr;
}
#age-app .diff-stats-grid {
grid-template-columns: repeat(2, 1fr);
}
#age-app .hero-age .age-main {
font-size: 2.2rem;
}
}
@media (max-width: 400px) {
#age-app .stats-grid {
grid-template-columns: 1fr 1fr;
}
#age-app .input-card {
padding: 18px 14px;
}
}
</style>

<!-- Mode Tabs -->
<div class="mode-tabs">
<button class="mode-tab active" onclick="ageTool.setMode('age')" id="tab-age">Age Calculator</button>
<button class="mode-tab" onclick="ageTool.setMode('diff')" id="tab-diff">Date Difference</button>
</div>

<!-- AGE CALCULATOR MODE -->
<div id="mode-age">
<div class="input-card">
<div class="input-grid">
<div class="input-group">
<label for="dob-input">Date of Birth</label>
<input type="date" id="dob-input" max="" />
</div>
<div class="input-group">
<label for="asof-input">Calculate As Of</label>
<input type="date" id="asof-input" />
</div>
<div class="input-group" style="align-self:end;">
<button class="calc-btn" onclick="ageTool.calcAge()">Calculate Age</button>
<span class="reset-link" onclick="ageTool.resetAge()">Reset</span>
</div>
</div>
<div class="error-msg" id="age-error"></div>
</div>

<div class="results-section" id="age-results">
<!-- Hero -->
<div class="hero-age">
<div class="age-main" id="res-hero-age"></div>
<div class="age-sub" id="res-hero-sub"></div>
</div>

<!-- Stat Cards -->
<div class="stats-grid">
<div class="stat-card">
<div class="stat-value" id="res-months"></div>
<div class="stat-label">Total Months</div>
</div>
<div class="stat-card">
<div class="stat-value" id="res-weeks"></div>
<div class="stat-label">Total Weeks</div>
</div>
<div class="stat-card">
<div class="stat-value" id="res-days"></div>
<div class="stat-label">Total Days</div>
</div>
<div class="stat-card">
<div class="stat-value" id="res-hours"></div>
<div class="stat-label">Total Hours</div>
</div>
<div class="stat-card">
<div class="stat-value" id="res-minutes"></div>
<div class="stat-label">Total Minutes</div>
</div>
<div class="stat-card">
<div class="stat-value" id="res-seconds"></div>
<div class="stat-label">Total Seconds</div>
</div>
</div>

<!-- Info Cards Row 1 -->
<div class="info-grid">
<div class="info-card">
<div class="info-icon">📅</div>
<div class="info-title">Day of Week Born</div>
<div class="info-value" id="res-dow"></div>
<div class="info-sub" id="res-dob-fmt"></div>
</div>
<div class="info-card">
<div class="info-icon">♈</div>
<div class="info-title">Western Zodiac</div>
<div class="info-value" id="res-zodiac"></div>
<div class="info-sub" id="res-zodiac-dates"></div>
</div>
<div class="info-card">
<div class="info-icon">🐉</div>
<div class="info-title">Chinese Zodiac</div>
<div class="info-value" id="res-chinese"></div>
<div class="info-sub" id="res-chinese-year"></div>
</div>
<div class="info-card">
<div class="info-icon">👥</div>
<div class="info-title">Generation</div>
<div class="info-value" id="res-gen"></div>
<div class="info-sub" id="res-gen-range"></div>
</div>
</div>

<!-- Birthday Countdown -->
<div class="countdown-card">
<div class="cd-icon">🎂</div>
<div class="cd-text">
<div class="cd-title">Next Birthday</div>
<div class="cd-value" id="res-countdown"></div>
<div class="cd-sub" id="res-next-bday"></div>
</div>
</div>

<!-- Milestones -->
<div class="milestones-section">
<h3>🏁 Life Milestones</h3>
<div class="milestone-list" id="res-milestones"></div>
</div>
</div>
</div>

<!-- DATE DIFFERENCE MODE -->
<div id="mode-diff" style="display:none;">
<div class="input-card">
<div class="input-grid">
<div class="input-group">
<label for="diff-start">Start Date</label>
<input type="date" id="diff-start" />
</div>
<div class="input-group">
<label for="diff-end">End Date</label>
<input type="date" id="diff-end" />
</div>
<div class="input-group" style="align-self:end;">
<button class="calc-btn" onclick="ageTool.calcDiff()">Calculate Difference</button>
<span class="reset-link" onclick="ageTool.resetDiff()">Reset</span>
</div>
</div>
<div class="error-msg" id="diff-error"></div>
</div>

<div class="results-section" id="diff-results">
<div class="diff-result">
<div class="diff-main" id="diff-hero"></div>
<div class="diff-sub" id="diff-hero-sub"></div>
</div>
<div class="diff-stats-grid">
<div class="stat-card">
<div class="stat-value" id="diff-months"></div>
<div class="stat-label">Total Months</div>
</div>
<div class="stat-card">
<div class="stat-value" id="diff-weeks"></div>
<div class="stat-label">Total Weeks</div>
</div>
<div class="stat-card">
<div class="stat-value" id="diff-hours"></div>
<div class="stat-label">Total Hours</div>
</div>
<div class="stat-card">
<div class="stat-value" id="diff-minutes"></div>
<div class="stat-label">Total Minutes</div>
</div>
<div class="stat-card">
<div class="stat-value" id="diff-seconds"></div>
<div class="stat-label">Total Seconds</div>
</div>
<div class="stat-card">
<div class="stat-value" id="diff-workdays"></div>
<div class="stat-label">Weekdays</div>
</div>
</div>
</div>
</div>

<script>
(function() {
var ageTool = window.ageTool = {};

// ---- Helpers ----
function parseDate(str) {
if (!str) return null;
var p = str.split('-');
return new Date(+p[0], +p[1]-1, +p[2]);
}
function fmtNum(n) {
return n.toLocaleString();
}
function pad2(n) { return n < 10 ? '0'+n : ''+n; }
function toDateStr(d) {
return d.getFullYear() + '-' + pad2(d.getMonth()+1) + '-' + pad2(d.getDate());
}

var DAYS = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
var MONTHS_LONG = ['January','February','March','April','May','June','July','August','September','October','November','December'];

function fmtDateLong(d) {
return MONTHS_LONG[d.getMonth()] + ' ' + d.getDate() + ', ' + d.getFullYear();
}

// ---- Zodiac ----
var ZODIAC = [
{ name: 'Capricorn', symbol: '♑', start: [1,1],  end: [1,19],  dates: 'Dec 22 – Jan 19' },
{ name: 'Aquarius',  symbol: '♒', start: [1,20], end: [2,18],  dates: 'Jan 20 – Feb 18' },
{ name: 'Pisces',    symbol: '♓', start: [2,19], end: [3,20],  dates: 'Feb 19 – Mar 20' },
{ name: 'Aries',     symbol: '♈', start: [3,21], end: [4,19],  dates: 'Mar 21 – Apr 19' },
{ name: 'Taurus',    symbol: '♉', start: [4,20], end: [5,20],  dates: 'Apr 20 – May 20' },
{ name: 'Gemini',    symbol: '♊', start: [5,21], end: [6,20],  dates: 'May 21 – Jun 20' },
{ name: 'Cancer',    symbol: '♋', start: [6,21], end: [7,22],  dates: 'Jun 21 – Jul 22' },
{ name: 'Leo',       symbol: '♌', start: [7,23], end: [8,22],  dates: 'Jul 23 – Aug 22' },
{ name: 'Virgo',     symbol: '♍', start: [8,23], end: [9,22],  dates: 'Aug 23 – Sep 22' },
{ name: 'Libra',     symbol: '♎', start: [9,23], end: [10,22], dates: 'Sep 23 – Oct 22' },
{ name: 'Scorpio',   symbol: '♏', start: [10,23],end: [11,21], dates: 'Oct 23 – Nov 21' },
{ name: 'Sagittarius',symbol:'♐', start: [11,22],end: [12,21], dates: 'Nov 22 – Dec 21' },
{ name: 'Capricorn', symbol: '♑', start: [12,22],end: [12,31], dates: 'Dec 22 – Jan 19' }
];
function getZodiac(d) {
var m = d.getMonth()+1, day = d.getDate();
for (var i=0; i<ZODIAC.length; i++) {
var z = ZODIAC[i];
if ((m === z.start[0] && day >= z.start[1]) || (m === z.end[0] && day <= z.end[1])) {
return z;
}
}
return ZODIAC[0];
}

// ---- Chinese Zodiac ----
var CZ_ANIMALS = ['Rat','Ox','Tiger','Rabbit','Dragon','Snake','Horse','Goat','Monkey','Rooster','Dog','Pig'];
var CZ_EMOJI   = ['🐀','🐂','🐅','🐇','🐉','🐍','🐎','🐑','🐒','🐓','🐕','🐖'];
function getChineseZodiac(year) {
var idx = (year - 1900) % 12;
if (idx < 0) idx += 12;
return { animal: CZ_ANIMALS[idx], emoji: CZ_EMOJI[idx] };
}

// ---- Generation ----
var GENERATIONS = [
{ name: 'Generation Alpha', range: '2013–present', min: 2013, max: 2030 },
{ name: 'Generation Z',     range: '1997–2012',    min: 1997, max: 2012 },
{ name: 'Millennial',       range: '1981–1996',    min: 1981, max: 1996 },
{ name: 'Generation X',     range: '1965–1980',    min: 1965, max: 1980 },
{ name: 'Baby Boomer',      range: '1946–1964',    min: 1946, max: 1964 },
{ name: 'Silent Generation',range: '1928–1945',    min: 1928, max: 1945 },
{ name: 'Greatest Generation',range:'1901–1927',   min: 1901, max: 1927 }
];
function getGeneration(year) {
for (var i=0; i<GENERATIONS.length; i++) {
if (year >= GENERATIONS[i].min && year <= GENERATIONS[i].max) return GENERATIONS[i];
}
return { name: 'Unknown', range: '' };
}

// ---- Milestones ----
function getMilestones(dob, asof) {
var items = [
{ label: '1,000 days old',       days: 1000 },
{ label: '10,000 hours lived',    days: Math.ceil(10000/24) },
{ label: '10,000 days old',       days: 10000 },
{ label: '100,000,000 seconds',   days: Math.ceil(100000000/86400) },
{ label: '1 billion seconds',     days: Math.ceil(1000000000/86400) },
{ label: '2 billion seconds',     days: Math.ceil(2000000000/86400) },
{ label: '3 billion seconds',     days: Math.ceil(3000000000/86400) },
{ label: '100 months old',        days: Math.ceil(100*30.4375) },
{ label: '20,000 days old',       days: 20000 },
{ label: '500 months old',        days: Math.ceil(500*30.4375) },
{ label: '30,000 days old',       days: 30000 },
];
var result = [];
items.forEach(function(m) {
var mDate = new Date(dob.getTime() + m.days * 86400000);
var passed = mDate <= asof;
var diffDays = Math.round(Math.abs(mDate - asof) / 86400000);
result.push({
label: m.label,
date: mDate,
passed: passed,
diffDays: diffDays
});
});
// Sort: passed desc by date, upcoming asc
var passed = result.filter(function(x){ return x.passed; }).sort(function(a,b){ return b.date-a.date; });
var upcoming = result.filter(function(x){ return !x.passed; }).sort(function(a,b){ return a.date-b.date; });
return passed.concat(upcoming);
}

// ---- Diff between two dates (years/months/days) ----
function calcYMD(from, to) {
var y = to.getFullYear() - from.getFullYear();
var m = to.getMonth() - from.getMonth();
var d = to.getDate() - from.getDate();
if (d < 0) { m--; var prevMonth = new Date(to.getFullYear(), to.getMonth(), 0); d += prevMonth.getDate(); }
if (m < 0) { y--; m += 12; }
return { years: y, months: m, days: d };
}

// ---- Count weekdays ----
function countWeekdays(from, to) {
var start = new Date(Math.min(from, to));
var end   = new Date(Math.max(from, to));
var count = 0;
var cur = new Date(start);
while (cur <= end) {
var dow = cur.getDay();
if (dow !== 0 && dow !== 6) count++;
cur.setDate(cur.getDate() + 1);
}
return count;
}

// ---- UI helpers ----
function showError(id, msg) {
var el = document.getElementById(id);
el.textContent = msg;
el.classList.add('visible');
}
function hideError(id) {
var el = document.getElementById(id);
el.textContent = '';
el.classList.remove('visible');
}
function setText(id, val) {
var el = document.getElementById(id);
if (el) el.textContent = val;
}

// ---- Mode switching ----
ageTool.setMode = function(mode) {
document.getElementById('mode-age').style.display = mode === 'age' ? '' : 'none';
document.getElementById('mode-diff').style.display = mode === 'diff' ? '' : 'none';
document.getElementById('tab-age').classList.toggle('active', mode === 'age');
document.getElementById('tab-diff').classList.toggle('active', mode === 'diff');
};

// ---- Age Calculator ----
ageTool.calcAge = function() {
hideError('age-error');
var dobStr = document.getElementById('dob-input').value;
var asofStr = document.getElementById('asof-input').value;
if (!dobStr) { showError('age-error', 'Please enter your date of birth.'); return; }
if (!asofStr) { showError('age-error', 'Please enter the "as of" date.'); return; }

var dob = parseDate(dobStr);
var asof = parseDate(asofStr);

if (dob > asof) { showError('age-error', 'Date of birth cannot be after the "Calculate As Of" date.'); return; }

var ymd = calcYMD(dob, asof);
var totalDays = Math.floor((asof - dob) / 86400000);
var totalWeeks = Math.floor(totalDays / 7);
var totalMonths = ymd.years * 12 + ymd.months;
var totalHours = totalDays * 24;
var totalMinutes = totalHours * 60;
var totalSeconds = totalMinutes * 60;

// Hero
var heroText = ymd.years + ' years, ' + ymd.months + ' months & ' + ymd.days + ' days';
setText('res-hero-age', heroText);
setText('res-hero-sub', 'Born ' + fmtDateLong(dob) + ' — As of ' + fmtDateLong(asof));

// Stats
setText('res-months',  fmtNum(totalMonths));
setText('res-weeks',   fmtNum(totalWeeks));
setText('res-days',    fmtNum(totalDays));
setText('res-hours',   fmtNum(totalHours));
setText('res-minutes', fmtNum(totalMinutes));
setText('res-seconds', fmtNum(totalSeconds));

// Day of week
setText('res-dow',     'You were born on a ' + DAYS[dob.getDay()]);
setText('res-dob-fmt', fmtDateLong(dob));

// Zodiac
var z = getZodiac(dob);
setText('res-zodiac',       z.symbol + ' ' + z.name);
setText('res-zodiac-dates', z.dates);

// Chinese zodiac
var cz = getChineseZodiac(dob.getFullYear());
setText('res-chinese',      cz.emoji + ' ' + cz.animal);
setText('res-chinese-year', 'Year of the ' + cz.animal + ' (' + dob.getFullYear() + ')');

// Generation
var gen = getGeneration(dob.getFullYear());
setText('res-gen',       gen.name);
setText('res-gen-range', 'Born ' + gen.range);

// Next birthday countdown
var nextBday = new Date(asof.getFullYear(), dob.getMonth(), dob.getDate());
if (nextBday <= asof) nextBday.setFullYear(nextBday.getFullYear() + 1);
var daysUntil = Math.ceil((nextBday - asof) / 86400000);
if (daysUntil === 0) {
setText('res-countdown', 'Today is your birthday!');
setText('res-next-bday', 'Happy Birthday!');
} else {
setText('res-countdown', daysUntil + (daysUntil === 1 ? ' day' : ' days') + ' until your birthday');
setText('res-next-bday', 'Next birthday: ' + fmtDateLong(nextBday));
}

// Milestones
var ms = getMilestones(dob, asof);
var msHtml = '';
ms.forEach(function(m) {
var cls = m.passed ? 'passed' : 'upcoming';
var badge = m.passed ? '✅' : '⏳';
var statusText = m.passed
? (m.diffDays === 0 ? 'Today!' : m.diffDays + ' days ago')
: 'in ' + fmtNum(m.diffDays) + ' days';
msHtml += '<div class="milestone-item ' + cls + '">' +
'<span class="ms-badge">' + badge + '</span>' +
'<div class="ms-body">' +
'<div class="ms-label">' + m.label + '</div>' +
'<div class="ms-date">' + fmtDateLong(m.date) + '</div>' +
'</div>' +
'<span class="ms-status">' + statusText + '</span>' +
'</div>';
});
document.getElementById('res-milestones').innerHTML = msHtml;

document.getElementById('age-results').classList.add('visible');
};

ageTool.resetAge = function() {
document.getElementById('dob-input').value = '';
document.getElementById('asof-input').value = '';
document.getElementById('age-results').classList.remove('visible');
hideError('age-error');
};

// ---- Date Difference Calculator ----
ageTool.calcDiff = function() {
hideError('diff-error');
var startStr = document.getElementById('diff-start').value;
var endStr   = document.getElementById('diff-end').value;
if (!startStr) { showError('diff-error', 'Please select a start date.'); return; }
if (!endStr)   { showError('diff-error', 'Please select an end date.'); return; }

var start = parseDate(startStr);
var end   = parseDate(endStr);

var earlier = start <= end ? start : end;
var later   = start <= end ? end   : start;
var direction = start <= end ? '' : '(reversed) ';

var totalDays = Math.floor((later - earlier) / 86400000);
var totalWeeks = Math.floor(totalDays / 7);
var remainDays = totalDays % 7;
var ymd = calcYMD(earlier, later);
var totalMonths = ymd.years * 12 + ymd.months;
var totalHours   = totalDays * 24;
var totalMinutes = totalHours * 60;
var totalSeconds = totalMinutes * 60;
var weekdays = countWeekdays(earlier, later);

// Hero
var heroParts = [];
if (ymd.years > 0)   heroParts.push(ymd.years + (ymd.years === 1 ? ' year' : ' years'));
if (ymd.months > 0)  heroParts.push(ymd.months + (ymd.months === 1 ? ' month' : ' months'));
if (ymd.days > 0)    heroParts.push(ymd.days + (ymd.days === 1 ? ' day' : ' days'));
if (heroParts.length === 0) heroParts.push('Same day');

setText('diff-hero', heroParts.join(', '));
setText('diff-hero-sub', direction + fmtDateLong(earlier) + '  →  ' + fmtDateLong(later));

setText('diff-months',   fmtNum(totalMonths));
setText('diff-weeks',    fmtNum(totalWeeks) + (remainDays > 0 ? ' w ' + remainDays + 'd' : ''));
setText('diff-hours',    fmtNum(totalHours));
setText('diff-minutes',  fmtNum(totalMinutes));
setText('diff-seconds',  fmtNum(totalSeconds));
setText('diff-workdays', fmtNum(weekdays));

document.getElementById('diff-results').classList.add('visible');
};

ageTool.resetDiff = function() {
document.getElementById('diff-start').value = '';
document.getElementById('diff-end').value = '';
document.getElementById('diff-results').classList.remove('visible');
hideError('diff-error');
};

// ---- Init: set default dates ----
(function init() {
var today = new Date();
var todayStr = toDateStr(today);
var maxEl = document.getElementById('dob-input');
if (maxEl) maxEl.setAttribute('max', todayStr);
var asofEl = document.getElementById('asof-input');
if (asofEl) asofEl.value = todayStr;
var diffEnd = document.getElementById('diff-end');
if (diffEnd) diffEnd.value = todayStr;
})();
})();
</script>

</div>

---

## How Old Am I Exactly?

Most people know their age in whole years, but your exact age is far more precise than that. Between your last birthday and today, days, hours, and even minutes have accumulated into a meaningful slice of your life. Knowing your exact age down to days and hours matters more than you might think — from legal eligibility thresholds (such as voting, retirement, or pension calculations) to health screenings that are recommended at specific age milestones. Insurance actuaries, medical researchers, and demographers all work with exact ages rather than rounded figures because the difference of even a few months can change which category you fall into.

Beyond practicality, there is something quietly profound about seeing your life expressed in total days or seconds. 10,000 days is a milestone fewer than 30% of people have consciously noticed passing; one billion seconds occurs around age 31 years and 8 months, and almost nobody celebrates it — even though it is a far rarer number than a simple birthday. Expressing age in multiple units makes time feel tangible in a new way, transforming an abstract number of years into a vivid accumulation of lived moments.

---

## Fun Birthday Facts

- **The most common birthday** in the United States is September 9th, likely because it falls about nine months after the winter holiday season.
- **February 29th birthdays** (leap day) occur only once every four years, meaning leap-day babies technically have a calendar birthday just once every four years — though they usually celebrate on February 28th or March 1st.
- **You share your birthday** with roughly 20 million other people alive today, based on a global population of around 8 billion spread over 365 days.
- **The oldest verified human ever** was Jeanne Calment of France, who lived to 122 years and 164 days — that is over 44,700 days of life.
- **One billion seconds** is approximately 31.69 years. If you are in your early 30s, your "billion-second birthday" may be right around the corner.
- **Saturday is the most common day of the week** to be born in many Western countries, simply because hospitals historically had more planned deliveries scheduled on weekdays — though the distribution has become more even in recent decades.

---

## Related Tools

> Check your BMI and healthy weight range → [BMI Calculator](/tools/bmi-calculator/)

> Calculate percentages instantly → [Percentage Calculator](/tools/percentage-calculator/)

> Convert between units of measurement → [Unit Converter](/tools/unit-converter/)

> Working across time zones? → [Timezone Converter](/tools/timezone-converter/) — convert times between any cities instantly
