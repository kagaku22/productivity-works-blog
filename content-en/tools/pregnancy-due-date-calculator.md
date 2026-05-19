---
title: "Pregnancy Due Date Calculator - Estimate Your Baby's Arrival"
date: 2025-05-16
description: "Calculate your estimated due date based on last menstrual period or conception date. Week-by-week pregnancy timeline."
categories: ["Free Tools"]
slug: "pregnancy-due-date-calculator"
ShowToc: false
cover:
  image: "/images/covers/pregnancy-due-date-calculator.png"
  alt: "Pregnancy Due Date Calculator"
---

<div id="pdd-app">

<style>
#pdd-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #2d2d2d;
line-height: 1.6;
}

#pdd-app h2 {
font-size: 1.5rem;
font-weight: 700;
color: #c2185b;
margin: 0 0 1rem 0;
}

#pdd-app h3 {
font-size: 1.1rem;
font-weight: 600;
margin: 0 0 0.75rem 0;
color: #2d2d2d;
}

#pdd-app .pdd-intro {
background: #fce4ec;
border-left: 4px solid #e91e63;
border-radius: 0 8px 8px 0;
padding: 1rem 1.25rem;
margin-bottom: 1.5rem;
font-size: 0.95rem;
color: #555;
}

#pdd-app .pdd-card {
background: #fff;
border: 1px solid #f0c0d0;
border-radius: 12px;
padding: 1.5rem;
margin-bottom: 1.5rem;
box-shadow: 0 2px 8px rgba(194,24,91,0.06);
}

#pdd-app .pdd-input-group {
margin-bottom: 1.25rem;
}

#pdd-app .pdd-input-group label {
display: block;
font-weight: 600;
margin-bottom: 0.4rem;
font-size: 0.9rem;
color: #444;
}

#pdd-app .pdd-input-group input[type="date"] {
width: 100%;
padding: 0.65rem 0.9rem;
border: 2px solid #f0c0d0;
border-radius: 8px;
font-size: 1rem;
color: #2d2d2d;
background: #fff;
box-sizing: border-box;
transition: border-color 0.2s;
outline: none;
}

#pdd-app .pdd-input-group input[type="date"]:focus {
border-color: #e91e63;
}

#pdd-app .pdd-divider {
display: flex;
align-items: center;
gap: 0.75rem;
margin: 1rem 0;
color: #aaa;
font-size: 0.85rem;
font-weight: 600;
}

#pdd-app .pdd-divider::before,
#pdd-app .pdd-divider::after {
content: '';
flex: 1;
height: 1px;
background: #f0c0d0;
}

#pdd-app .pdd-btn {
display: inline-block;
background: #e91e63;
color: #fff;
border: none;
border-radius: 8px;
padding: 0.75rem 2rem;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
width: 100%;
margin-top: 0.5rem;
}

#pdd-app .pdd-btn:hover {
background: #c2185b;
transform: translateY(-1px);
}

#pdd-app .pdd-btn:active {
transform: translateY(0);
}

#pdd-app .pdd-result {
display: none;
}

#pdd-app .pdd-result.visible {
display: block;
}

#pdd-app .pdd-due-date-box {
background: linear-gradient(135deg, #e91e63 0%, #c2185b 100%);
color: #fff;
border-radius: 12px;
padding: 1.5rem;
text-align: center;
margin-bottom: 1.5rem;
}

#pdd-app .pdd-due-date-box .pdd-due-label {
font-size: 0.9rem;
opacity: 0.85;
margin-bottom: 0.4rem;
font-weight: 500;
}

#pdd-app .pdd-due-date-box .pdd-due-value {
font-size: 2rem;
font-weight: 800;
letter-spacing: 0.02em;
margin-bottom: 0.5rem;
}

#pdd-app .pdd-due-date-box .pdd-due-sub {
font-size: 0.9rem;
opacity: 0.85;
}

#pdd-app .pdd-stats-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 1rem;
margin-bottom: 1.5rem;
}

@media (max-width: 520px) {
#pdd-app .pdd-stats-grid {
grid-template-columns: 1fr 1fr;
}
}

#pdd-app .pdd-stat-box {
background: #fce4ec;
border-radius: 10px;
padding: 0.9rem 0.75rem;
text-align: center;
}

#pdd-app .pdd-stat-box .pdd-stat-label {
font-size: 0.75rem;
color: #888;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 0.3rem;
}

#pdd-app .pdd-stat-box .pdd-stat-value {
font-size: 1.4rem;
font-weight: 800;
color: #c2185b;
line-height: 1.1;
}

#pdd-app .pdd-stat-box .pdd-stat-unit {
font-size: 0.75rem;
color: #c2185b;
font-weight: 500;
}

#pdd-app .pdd-trimester-bar {
background: #fce4ec;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-bottom: 1.5rem;
}

#pdd-app .pdd-trimester-bar h3 {
margin-bottom: 0.75rem;
font-size: 0.95rem;
color: #888;
text-transform: uppercase;
letter-spacing: 0.04em;
}

#pdd-app .pdd-progress-wrap {
background: #f8bbd0;
border-radius: 999px;
height: 14px;
position: relative;
overflow: hidden;
margin-bottom: 0.4rem;
}

#pdd-app .pdd-progress-fill {
height: 100%;
background: linear-gradient(90deg, #e91e63, #c2185b);
border-radius: 999px;
transition: width 0.6s ease;
}

#pdd-app .pdd-trimester-labels {
display: flex;
justify-content: space-between;
font-size: 0.72rem;
color: #aaa;
font-weight: 500;
}

#pdd-app .pdd-trimester-badge {
display: inline-block;
background: #e91e63;
color: #fff;
border-radius: 999px;
padding: 0.2rem 0.9rem;
font-size: 0.82rem;
font-weight: 700;
margin-top: 0.6rem;
}

#pdd-app .pdd-milestones {
margin-bottom: 1.5rem;
}

#pdd-app .pdd-milestone-item {
display: flex;
align-items: flex-start;
gap: 0.9rem;
padding: 0.8rem 0;
border-bottom: 1px solid #fce4ec;
}

#pdd-app .pdd-milestone-item:last-child {
border-bottom: none;
}

#pdd-app .pdd-milestone-icon {
width: 36px;
height: 36px;
border-radius: 50%;
display: flex;
align-items: center;
justify-content: center;
font-size: 1rem;
flex-shrink: 0;
background: #fce4ec;
}

#pdd-app .pdd-milestone-icon.past {
background: #e0e0e0;
}

#pdd-app .pdd-milestone-icon.current {
background: #e91e63;
}

#pdd-app .pdd-milestone-body {
flex: 1;
}

#pdd-app .pdd-milestone-body .pdd-ms-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 0.2rem;
}

#pdd-app .pdd-milestone-body .pdd-ms-name {
font-weight: 700;
font-size: 0.92rem;
color: #2d2d2d;
}

#pdd-app .pdd-milestone-body .pdd-ms-date {
font-size: 0.8rem;
color: #e91e63;
font-weight: 600;
}

#pdd-app .pdd-milestone-body .pdd-ms-desc {
font-size: 0.82rem;
color: #777;
}

#pdd-app .pdd-dev-section {
margin-bottom: 1.5rem;
}

#pdd-app .pdd-dev-card {
background: #fff9fb;
border: 1px solid #f8bbd0;
border-radius: 10px;
padding: 1rem 1.1rem;
margin-bottom: 0.75rem;
}

#pdd-app .pdd-dev-card .pdd-dev-week {
font-weight: 800;
color: #e91e63;
font-size: 0.85rem;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 0.2rem;
}

#pdd-app .pdd-dev-card .pdd-dev-title {
font-weight: 700;
font-size: 0.95rem;
margin-bottom: 0.25rem;
}

#pdd-app .pdd-dev-card .pdd-dev-desc {
font-size: 0.85rem;
color: #666;
}

#pdd-app .pdd-related {
background: #f9f9f9;
border-radius: 10px;
padding: 1.1rem 1.25rem;
margin-top: 1.5rem;
}

#pdd-app .pdd-related h3 {
font-size: 0.95rem;
color: #888;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 0.75rem;
}

#pdd-app .pdd-related ul {
list-style: none;
margin: 0;
padding: 0;
}

#pdd-app .pdd-related ul li {
margin-bottom: 0.5rem;
}

#pdd-app .pdd-related ul li a {
color: #e91e63;
text-decoration: none;
font-size: 0.9rem;
font-weight: 500;
}

#pdd-app .pdd-related ul li a:hover {
text-decoration: underline;
}

#pdd-app .pdd-error {
display: none;
color: #c2185b;
background: #fce4ec;
border-radius: 8px;
padding: 0.65rem 1rem;
font-size: 0.88rem;
font-weight: 600;
margin-top: 0.5rem;
}

#pdd-app .pdd-error.visible {
display: block;
}
</style>

<div class="pdd-intro">
Enter your <strong>last menstrual period (LMP)</strong> date or your <strong>conception date</strong> to instantly calculate your estimated due date, current pregnancy week, trimester, and key upcoming milestones.
</div>

<div class="pdd-card">
<h2>Pregnancy Due Date Calculator</h2>

<div class="pdd-input-group">
<label for="pdd-lmp">Last Menstrual Period (LMP) Date</label>
<input type="date" id="pdd-lmp" />
</div>

<div class="pdd-divider">OR</div>

<div class="pdd-input-group">
<label for="pdd-conception">Conception / Ovulation Date</label>
<input type="date" id="pdd-conception" />
</div>

<div class="pdd-error" id="pdd-error">Please enter either an LMP date or a conception date to continue.</div>

<button class="pdd-btn" onclick="pddCalculate()">Calculate My Due Date</button>
</div>

<div class="pdd-result" id="pdd-result">

<div class="pdd-due-date-box">
<div class="pdd-due-label">Estimated Due Date (EDD)</div>
<div class="pdd-due-value" id="pdd-edd-display"></div>
<div class="pdd-due-sub" id="pdd-days-remaining"></div>
</div>

<div class="pdd-stats-grid">
<div class="pdd-stat-box">
<div class="pdd-stat-label">Current Week</div>
<div class="pdd-stat-value" id="pdd-week-num">—</div>
<div class="pdd-stat-unit">weeks</div>
</div>
<div class="pdd-stat-box">
<div class="pdd-stat-label">Day in Week</div>
<div class="pdd-stat-value" id="pdd-day-num">—</div>
<div class="pdd-stat-unit">days</div>
</div>
<div class="pdd-stat-box">
<div class="pdd-stat-label">Trimester</div>
<div class="pdd-stat-value" id="pdd-trimester-num">—</div>
<div class="pdd-stat-unit">trimester</div>
</div>
</div>

<div class="pdd-card pdd-trimester-bar">
<h3>Pregnancy Progress</h3>
<div class="pdd-progress-wrap">
<div class="pdd-progress-fill" id="pdd-progress-fill" style="width:0%"></div>
</div>
<div class="pdd-trimester-labels">
<span>Week 1</span>
<span>1st Tri (W1–13)</span>
<span>2nd Tri (W14–27)</span>
<span>3rd Tri (W28+)</span>
<span>Week 40</span>
</div>
<div id="pdd-trimester-badge" class="pdd-trimester-badge"></div>
</div>

<div class="pdd-card pdd-milestones">
<h2>Key Milestones</h2>
<div id="pdd-milestones-list"></div>
</div>

<div class="pdd-card pdd-dev-section">
<h2>Week-by-Week Development Highlights</h2>
<div class="pdd-dev-card">
<div class="pdd-dev-week">Weeks 8–10</div>
<div class="pdd-dev-title">All Major Organs Forming</div>
<div class="pdd-dev-desc">The embryo transitions to a fetus. Tiny fingers and toes appear. The heart beats at ~170 bpm. Facial features are becoming distinct.</div>
</div>
<div class="pdd-dev-card">
<div class="pdd-dev-week">Weeks 18–22</div>
<div class="pdd-dev-title">First Movements & Anatomy Scan</div>
<div class="pdd-dev-desc">You may feel the first kicks ("quickening"). The 20-week anatomy scan checks organ development and can often reveal the baby's sex.</div>
</div>
<div class="pdd-dev-card">
<div class="pdd-dev-week">Weeks 28–32</div>
<div class="pdd-dev-title">Rapid Brain Growth</div>
<div class="pdd-dev-desc">The brain develops rapidly with characteristic grooves and folds. The baby can open and close its eyes. Lungs are maturing in preparation for birth.</div>
</div>
<div class="pdd-dev-card">
<div class="pdd-dev-week">Weeks 37–40</div>
<div class="pdd-dev-title">Full Term — Ready for Birth</div>
<div class="pdd-dev-desc">At 37 weeks, the baby is considered full term. The baby continues gaining weight and the immune system receives antibodies. Birth can happen any day.</div>
</div>
</div>

</div>

<div class="pdd-related">
<h3>Related Tools</h3>
<ul>
<li><a href="/tools/date-calculator/">Ovulation & Fertile Window Calculator</a></li>
<li><a href="/tools/bmi-calculator/">BMI Calculator</a></li>
<li><a href="/tools/calorie-calculator/">Daily Calorie Calculator</a></li>
<li><a href="/tools/age-calculator/">Age Calculator</a></li>
</ul>
</div>

<script>
(function () {
var MONTHS = [
'January','February','March','April','May','June',
'July','August','September','October','November','December'
];

function formatDate(d) {
return MONTHS[d.getMonth()] + ' ' + d.getDate() + ', ' + d.getFullYear();
}

function addDays(date, days) {
var d = new Date(date.getTime());
d.setDate(d.getDate() + days);
return d;
}

function daysBetween(a, b) {
return Math.round((b.getTime() - a.getTime()) / 86400000);
}

function getTrimesterInfo(weeks) {
if (weeks < 1) return { num: '1st', label: '1st Trimester', color: '#e91e63' };
if (weeks <= 13) return { num: '1st', label: '1st Trimester (Weeks 1–13)', color: '#e91e63' };
if (weeks <= 27) return { num: '2nd', label: '2nd Trimester (Weeks 14–27)', color: '#ad1457' };
return { num: '3rd', label: '3rd Trimester (Weeks 28–40)', color: '#880e4f' };
}

window.pddCalculate = function () {
var lmpInput = document.getElementById('pdd-lmp').value;
var conceptionInput = document.getElementById('pdd-conception').value;
var errorEl = document.getElementById('pdd-error');
var resultEl = document.getElementById('pdd-result');

errorEl.classList.remove('visible');

var lmpDate;

if (lmpInput) {
lmpDate = new Date(lmpInput + 'T12:00:00');
} else if (conceptionInput) {
var conceptionDate = new Date(conceptionInput + 'T12:00:00');
// conception is ~14 days after LMP
lmpDate = addDays(conceptionDate, -14);
} else {
errorEl.classList.add('visible');
resultEl.classList.remove('visible');
return;
}

var edd = addDays(lmpDate, 280);
var today = new Date();
today.setHours(12, 0, 0, 0);

var daysPregnant = daysBetween(lmpDate, today);
var weeksPregnant = Math.floor(daysPregnant / 7);
var dayInWeek = daysPregnant % 7;
var daysRemaining = daysBetween(today, edd);
var progressPct = Math.min(100, Math.max(0, (daysPregnant / 280) * 100));

var trimInfo = getTrimesterInfo(weeksPregnant);

// EDD display
document.getElementById('pdd-edd-display').textContent = formatDate(edd);

if (daysRemaining > 0) {
document.getElementById('pdd-days-remaining').textContent =
daysRemaining + ' days remaining until your estimated due date';
} else if (daysRemaining === 0) {
document.getElementById('pdd-days-remaining').textContent = 'Today is your estimated due date!';
} else {
document.getElementById('pdd-days-remaining').textContent =
'Your estimated due date was ' + Math.abs(daysRemaining) + ' days ago';
}

// Stats
document.getElementById('pdd-week-num').textContent =
daysPregnant >= 0 ? weeksPregnant : '—';
document.getElementById('pdd-day-num').textContent =
daysPregnant >= 0 ? dayInWeek : '—';
document.getElementById('pdd-trimester-num').textContent =
daysPregnant >= 0 ? trimInfo.num : '—';

// Progress
document.getElementById('pdd-progress-fill').style.width = progressPct.toFixed(1) + '%';
var badge = document.getElementById('pdd-trimester-badge');
badge.textContent = trimInfo.label;
badge.style.background = trimInfo.color;

// Milestones
var milestones = [
{
week: 8,
icon: '🩺',
name: 'First Prenatal Visit',
desc: 'Confirmation scan, blood tests, and medical history review.'
},
{
week: 12,
icon: '📷',
name: '12-Week Nuchal Scan',
desc: 'Checks for chromosomal conditions. First clear image of your baby.'
},
{
week: 20,
icon: '🔬',
name: '20-Week Anatomy Scan',
desc: 'Detailed check of baby\'s organs, position, and growth. Sex can often be seen.'
},
{
week: 28,
icon: '🌟',
name: 'Third Trimester Begins',
desc: 'Glucose screening test. Increased prenatal visit frequency.'
},
{
week: 37,
icon: '✅',
name: 'Full Term',
desc: 'Baby is considered full term. Birth can safely occur any time now.'
},
{
week: 40,
icon: '👶',
name: 'Estimated Due Date',
desc: 'Your estimated arrival date. Only ~5% of babies arrive exactly on this day.'
}
];

var listEl = document.getElementById('pdd-milestones-list');
listEl.innerHTML = '';

milestones.forEach(function (ms) {
var msDate = addDays(lmpDate, ms.week * 7);
var msDaysFromToday = daysBetween(today, msDate);
var isPast = msDaysFromToday < 0;
var isCurrent = Math.abs(weeksPregnant - ms.week) <= 1 && !isPast;

var iconClass = isPast ? 'past' : (isCurrent ? 'current' : '');

var dateStr = formatDate(msDate);
var whenStr = isPast
? 'Passed'
: (msDaysFromToday === 0 ? 'Today!' : 'In ' + msDaysFromToday + ' days (' + dateStr + ')');

var item = document.createElement('div');
item.className = 'pdd-milestone-item';
item.innerHTML =
'<div class="pdd-milestone-icon ' + iconClass + '">' + ms.icon + '</div>' +
'<div class="pdd-milestone-body">' +
'<div class="pdd-ms-header">' +
'<span class="pdd-ms-name">Week ' + ms.week + ' — ' + ms.name + '</span>' +
'<span class="pdd-ms-date">' + whenStr + '</span>' +
'</div>' +
'<div class="pdd-ms-desc">' + ms.desc + '</div>' +
'</div>';
listEl.appendChild(item);
});

resultEl.classList.add('visible');
resultEl.scrollIntoView({ behavior: 'smooth', block: 'start' });
};

// Mutual exclusivity: clearing one input clears the other
document.getElementById('pdd-lmp').addEventListener('input', function () {
if (this.value) document.getElementById('pdd-conception').value = '';
});
document.getElementById('pdd-conception').addEventListener('input', function () {
if (this.value) document.getElementById('pdd-lmp').value = '';
});
})();
</script>

</div>

---

## Related Tools

> [Age Calculator](/tools/age-calculator/)
> [Dog Age Calculator](/tools/dog-age-calculator/)

