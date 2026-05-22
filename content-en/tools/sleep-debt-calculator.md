---
title: "Sleep Debt Calculator - Track Your Sleep Deficit"
date: 2025-05-16
description: "Calculate your accumulated sleep debt. Enter your weekly sleep hours and find out how much sleep you're missing. Recovery plan included."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "sleep-debt-calculator"
ShowToc: false
cover:
  image: "/images/covers/sleep-debt-calculator.png"
  alt: "Sleep Debt Calculator"
---

<div id="sd-app">

<style>
#sd-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1a1a2e;
}
#sd-app h2 {
font-size: 1.4rem;
font-weight: 700;
margin: 1.6rem 0 0.8rem;
color: #1a1a2e;
}
#sd-app .sd-intro {
background: #eef2ff;
border-left: 4px solid #4f46e5;
border-radius: 6px;
padding: 1rem 1.2rem;
margin-bottom: 1.6rem;
font-size: 0.95rem;
color: #3730a3;
}
#sd-app .sd-card {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 12px;
padding: 1.4rem 1.6rem;
margin-bottom: 1.2rem;
box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#sd-app label {
display: block;
font-size: 0.88rem;
font-weight: 600;
color: #374151;
margin-bottom: 0.3rem;
}
#sd-app .sd-ideal-row {
display: flex;
align-items: center;
gap: 1rem;
}
#sd-app .sd-ideal-row input[type=range] {
flex: 1;
accent-color: #4f46e5;
}
#sd-app .sd-ideal-val {
font-size: 1.3rem;
font-weight: 700;
color: #4f46e5;
min-width: 3.5rem;
text-align: center;
}
#sd-app .sd-days-grid {
display: grid;
grid-template-columns: repeat(7, 1fr);
gap: 0.6rem;
}
@media (max-width: 540px) {
#sd-app .sd-days-grid {
grid-template-columns: repeat(4, 1fr);
}
}
#sd-app .sd-day-cell {
display: flex;
flex-direction: column;
align-items: center;
gap: 0.3rem;
}
#sd-app .sd-day-cell span {
font-size: 0.78rem;
font-weight: 600;
color: #6b7280;
}
#sd-app .sd-day-cell input[type=number] {
width: 100%;
padding: 0.4rem 0.2rem;
border: 1px solid #d1d5db;
border-radius: 6px;
font-size: 1rem;
text-align: center;
outline: none;
transition: border-color 0.2s;
}
#sd-app .sd-day-cell input[type=number]:focus {
border-color: #4f46e5;
box-shadow: 0 0 0 2px rgba(79,70,229,0.15);
}
#sd-app .sd-btn {
display: block;
width: 100%;
padding: 0.85rem;
background: #4f46e5;
color: #fff;
border: none;
border-radius: 8px;
font-size: 1.05rem;
font-weight: 700;
cursor: pointer;
margin-top: 1rem;
transition: background 0.2s;
}
#sd-app .sd-btn:hover { background: #4338ca; }
#sd-app .sd-result {
display: none;
}
#sd-app .sd-result.visible { display: block; }
#sd-app .sd-summary-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
gap: 0.8rem;
margin-bottom: 1.2rem;
}
#sd-app .sd-stat {
background: #f9fafb;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 0.9rem 1rem;
text-align: center;
}
#sd-app .sd-stat .sd-stat-val {
font-size: 1.8rem;
font-weight: 800;
color: #4f46e5;
line-height: 1.1;
}
#sd-app .sd-stat .sd-stat-lbl {
font-size: 0.78rem;
color: #6b7280;
margin-top: 0.3rem;
}
#sd-app .sd-badge {
display: inline-block;
padding: 0.35rem 0.9rem;
border-radius: 999px;
font-size: 0.9rem;
font-weight: 700;
margin-bottom: 1rem;
}
#sd-app .sd-badge.none    { background: #d1fae5; color: #065f46; }
#sd-app .sd-badge.mild    { background: #fef3c7; color: #92400e; }
#sd-app .sd-badge.moderate{ background: #ffe4e6; color: #9f1239; }
#sd-app .sd-badge.severe  { background: #fce7f3; color: #831843; }
#sd-app .sd-chart-wrap {
overflow-x: auto;
margin-bottom: 1.2rem;
}
#sd-app .sd-chart {
display: flex;
align-items: flex-end;
gap: 0.5rem;
height: 160px;
padding: 0.5rem 0.2rem 0;
min-width: 320px;
}
#sd-app .sd-bar-group {
flex: 1;
display: flex;
flex-direction: column;
align-items: center;
gap: 2px;
height: 100%;
justify-content: flex-end;
}
#sd-app .sd-bars {
display: flex;
align-items: flex-end;
gap: 3px;
width: 100%;
height: 130px;
}
#sd-app .sd-bar {
flex: 1;
border-radius: 4px 4px 0 0;
min-height: 4px;
transition: height 0.4s ease;
}
#sd-app .sd-bar.ideal  { background: #c7d2fe; }
#sd-app .sd-bar.actual { background: #4f46e5; }
#sd-app .sd-bar-lbl {
font-size: 0.7rem;
color: #6b7280;
margin-top: 4px;
}
#sd-app .sd-legend {
display: flex;
gap: 1rem;
font-size: 0.8rem;
color: #374151;
margin-bottom: 0.8rem;
}
#sd-app .sd-legend-dot {
width: 12px; height: 12px;
border-radius: 3px;
display: inline-block;
margin-right: 4px;
vertical-align: middle;
}
#sd-app .sd-recovery {
background: #f0fdf4;
border: 1px solid #bbf7d0;
border-radius: 10px;
padding: 1rem 1.2rem;
margin-bottom: 1.2rem;
}
#sd-app .sd-recovery h3 {
font-size: 1rem;
font-weight: 700;
color: #166534;
margin: 0 0 0.4rem;
}
#sd-app .sd-recovery p {
font-size: 0.9rem;
color: #166534;
margin: 0;
}
#sd-app .sd-tips { list-style: none; padding: 0; margin: 0; }
#sd-app .sd-tips li {
padding: 0.5rem 0;
border-bottom: 1px solid #f3f4f6;
font-size: 0.9rem;
color: #374151;
padding-left: 1.4rem;
position: relative;
}
#sd-app .sd-tips li:last-child { border-bottom: none; }
#sd-app .sd-tips li::before {
content: "•";
color: #4f46e5;
font-weight: 700;
position: absolute;
left: 0.3rem;
}
#sd-app .sd-related {
background: #f9fafb;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 1rem 1.2rem;
margin-top: 1.6rem;
}
#sd-app .sd-related h3 {
font-size: 0.95rem;
font-weight: 700;
color: #374151;
margin: 0 0 0.5rem;
}
#sd-app .sd-related ul {
list-style: none;
padding: 0; margin: 0;
}
#sd-app .sd-related ul li {
padding: 0.3rem 0;
font-size: 0.88rem;
}
#sd-app .sd-related ul li a {
color: #4f46e5;
text-decoration: none;
}
#sd-app .sd-related ul li a:hover { text-decoration: underline; }
</style>

<div class="sd-intro">
Enter your ideal sleep hours and how much you actually slept each night this week. The calculator will show your accumulated sleep debt and how long recovery will take.
</div>

<!-- Ideal Sleep -->
<div class="sd-card">
<h2 style="margin-top:0">Step 1: Your Ideal Sleep</h2>
<label for="sd-ideal">Ideal hours of sleep per night</label>
<div class="sd-ideal-row">
<input type="range" id="sd-ideal" min="6" max="10" step="0.5" value="8" oninput="sdUpdateIdeal(this.value)">
<div class="sd-ideal-val" id="sd-ideal-display">8.0 hrs</div>
</div>
<p style="font-size:0.8rem;color:#6b7280;margin:0.5rem 0 0">Most adults need 7–9 hours. Adults over 65 often need 7–8 hours.</p>
</div>

<!-- 7-day log -->
<div class="sd-card">
<h2 style="margin-top:0">Step 2: This Week's Sleep Log</h2>
<p style="font-size:0.85rem;color:#6b7280;margin:0 0 1rem">Enter hours slept (decimals OK, e.g. 6.5)</p>
<div class="sd-days-grid">
<div class="sd-day-cell"><span>Mon</span><input type="number" id="sd-day0" min="0" max="24" step="0.5" value="7" placeholder="0"></div>
<div class="sd-day-cell"><span>Tue</span><input type="number" id="sd-day1" min="0" max="24" step="0.5" value="6" placeholder="0"></div>
<div class="sd-day-cell"><span>Wed</span><input type="number" id="sd-day2" min="0" max="24" step="0.5" value="6.5" placeholder="0"></div>
<div class="sd-day-cell"><span>Thu</span><input type="number" id="sd-day3" min="0" max="24" step="0.5" value="5.5" placeholder="0"></div>
<div class="sd-day-cell"><span>Fri</span><input type="number" id="sd-day4" min="0" max="24" step="0.5" value="7" placeholder="0"></div>
<div class="sd-day-cell"><span>Sat</span><input type="number" id="sd-day5" min="0" max="24" step="0.5" value="8.5" placeholder="0"></div>
<div class="sd-day-cell"><span>Sun</span><input type="number" id="sd-day6" min="0" max="24" step="0.5" value="7.5" placeholder="0"></div>
</div>
<button class="sd-btn" onclick="sdCalculate()">Calculate My Sleep Debt</button>
</div>

<!-- Results -->
<div class="sd-result" id="sd-result">

<div class="sd-card">
<h2 style="margin-top:0">Your Results</h2>
<div id="sd-badge-wrap"></div>

<div class="sd-summary-grid">
<div class="sd-stat">
<div class="sd-stat-val" id="sd-total-debt">0.0</div>
<div class="sd-stat-lbl">Weekly Sleep Debt (hrs)</div>
</div>
<div class="sd-stat">
<div class="sd-stat-val" id="sd-avg-actual">0.0</div>
<div class="sd-stat-lbl">Avg Actual Sleep (hrs/night)</div>
</div>
<div class="sd-stat">
<div class="sd-stat-val" id="sd-monthly-debt">0.0</div>
<div class="sd-stat-lbl">Projected Monthly Debt (hrs)</div>
</div>
<div class="sd-stat">
<div class="sd-stat-val" id="sd-recovery-days">0</div>
<div class="sd-stat-lbl">Recovery Days Needed</div>
</div>
</div>

<!-- Bar chart -->
<h3 style="font-size:0.95rem;font-weight:700;color:#374151;margin:0 0 0.5rem">Ideal vs. Actual Sleep per Night</h3>
<div class="sd-legend">
<span><span class="sd-legend-dot" style="background:#c7d2fe"></span>Ideal</span>
<span><span class="sd-legend-dot" style="background:#4f46e5"></span>Actual</span>
</div>
<div class="sd-chart-wrap">
<div class="sd-chart" id="sd-chart"></div>
</div>
</div>

<!-- Recovery plan -->
<div class="sd-recovery" id="sd-recovery-box">
<h3>Recovery Plan</h3>
<p id="sd-recovery-text"></p>
</div>

<!-- Tips -->
<div class="sd-card">
<h2 style="margin-top:0">Tips to Reduce Sleep Debt</h2>
<ul class="sd-tips" id="sd-tips-list"></ul>
</div>

</div>

<!-- Related tools -->
<div class="sd-related">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/pomodoro-timer/">Pomodoro Timer - Focus in 25-minute blocks</a></li>
<li><a href="/tools/daily-planner/">Deep Work Planner - Schedule your peak focus hours</a></li>
<li><a href="/tools/habit-tracker/">Energy Level Tracker - Map your daily energy curve</a></li>
</ul>
</div>

<script>
(function() {
var DAYS = ['Mon','Tue','Wed','Thu','Fri','Sat','Sun'];
var TIPS_ALL = [
'Go to bed and wake up at the same time every day — even weekends.',
'Avoid screens (phone, TV, laptop) for at least 30 minutes before bed.',
'Keep your bedroom cool (65–68°F / 18–20°C) and dark.',
'Cut off caffeine at least 6 hours before your bedtime.',
'A short nap (10–20 min) before 3 PM can reduce acute debt without affecting nighttime sleep.',
'Get bright light exposure within 30 minutes of waking to anchor your circadian rhythm.',
'Avoid alcohol close to bedtime — it fragments sleep quality.',
'Add 30–60 extra minutes per night on recovery days rather than sleeping in for hours at once.',
'Use a wind-down routine: dim lights, light reading, or breathing exercises.',
'Track your sleep for two weeks to spot the exact days your debt accumulates.'
];

window.sdUpdateIdeal = function(val) {
document.getElementById('sd-ideal-display').textContent = parseFloat(val).toFixed(1) + ' hrs';
};

window.sdCalculate = function() {
var ideal = parseFloat(document.getElementById('sd-ideal').value);
var actuals = [];
for (var i = 0; i < 7; i++) {
var v = parseFloat(document.getElementById('sd-day' + i).value);
actuals.push(isNaN(v) || v < 0 ? 0 : Math.min(v, 24));
}

var totalDebt = 0;
for (var i = 0; i < 7; i++) {
totalDebt += Math.max(0, ideal - actuals[i]);
}
var avgActual = actuals.reduce(function(a,b){return a+b;},0) / 7;
var monthlyDebt = totalDebt * (30/7);
// Recovery: sleep 1 extra hour per night until debt repaid
var recoveryDays = totalDebt <= 0 ? 0 : Math.ceil(totalDebt / 1);

// Category
var cat, catLabel;
if (totalDebt <= 0) { cat = 'none'; catLabel = 'No Sleep Debt'; }
else if (totalDebt < 3) { cat = 'mild'; catLabel = 'Mild Sleep Debt'; }
else if (totalDebt < 7) { cat = 'moderate'; catLabel = 'Moderate Sleep Debt'; }
else { cat = 'severe'; catLabel = 'Severe Sleep Debt'; }

// Update stats
document.getElementById('sd-total-debt').textContent = totalDebt.toFixed(1);
document.getElementById('sd-avg-actual').textContent = avgActual.toFixed(1);
document.getElementById('sd-monthly-debt').textContent = monthlyDebt.toFixed(1);
document.getElementById('sd-recovery-days').textContent = recoveryDays;

// Badge
document.getElementById('sd-badge-wrap').innerHTML =
'<span class="sd-badge ' + cat + '">' + catLabel + '</span>';

// Chart
var maxH = Math.max(ideal, Math.max.apply(null, actuals));
var chartH = 130;
var html = '';
for (var i = 0; i < 7; i++) {
var ih = Math.round((ideal / maxH) * chartH);
var ah = Math.round((actuals[i] / maxH) * chartH);
html += '<div class="sd-bar-group">' +
'<div class="sd-bars">' +
'<div class="sd-bar ideal" style="height:' + ih + 'px" title="Ideal: ' + ideal + 'h"></div>' +
'<div class="sd-bar actual" style="height:' + ah + 'px" title="Actual: ' + actuals[i] + 'h"></div>' +
'</div>' +
'<div class="sd-bar-lbl">' + DAYS[i] + '</div>' +
'</div>';
}
document.getElementById('sd-chart').innerHTML = html;

// Recovery text
var recText;
if (totalDebt <= 0) {
recText = 'Great work — you have no sleep debt this week! Keep maintaining your consistent sleep schedule.';
} else {
recText = 'You have accumulated ' + totalDebt.toFixed(1) + ' hours of sleep debt this week. ' +
'To recover, aim to sleep 1 extra hour per night for the next ' + recoveryDays + ' night' + (recoveryDays !== 1 ? 's' : '') + '. ' +
'At this rate, your monthly deficit will reach ' + monthlyDebt.toFixed(1) + ' hours — prioritize recovery now.';
}
document.getElementById('sd-recovery-text').textContent = recText;

// Tips — pick 5 relevant ones
var tips = TIPS_ALL.slice(0, 10);
if (cat === 'none') tips = [TIPS_ALL[0], TIPS_ALL[5], TIPS_ALL[2], TIPS_ALL[6], TIPS_ALL[8]];
else if (cat === 'mild') tips = [TIPS_ALL[0], TIPS_ALL[1], TIPS_ALL[3], TIPS_ALL[7], TIPS_ALL[8]];
else if (cat === 'moderate') tips = [TIPS_ALL[4], TIPS_ALL[0], TIPS_ALL[1], TIPS_ALL[3], TIPS_ALL[7]];
else tips = [TIPS_ALL[7], TIPS_ALL[4], TIPS_ALL[0], TIPS_ALL[3], TIPS_ALL[9]];

var thtml = '';
tips.forEach(function(t){ thtml += '<li>' + t + '</li>'; });
document.getElementById('sd-tips-list').innerHTML = thtml;

// Show results
var res = document.getElementById('sd-result');
res.classList.add('visible');
setTimeout(function(){ res.scrollIntoView({behavior:'smooth', block:'start'}); }, 100);
};
})();
</script>

</div>

---

## Related Tools

> [Pomodoro Timer](/tools/pomodoro-timer/)
> [Sleep Calculator](/tools/sleep-calculator/)

