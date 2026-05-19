---
title: "Pension Simulator"
date: 2025-05-16
description: "Free online pension calculator. Estimate your retirement savings, monthly pension income, and required contributions — with interactive charts, no sign-up needed."
categories: ["Free Tools"]
slug: "pension-simulator"
ShowToc: false
cover:
  image: "/images/covers/pension-simulator.png"
  alt: "Pension Simulator"
---

Plan your retirement with confidence. Enter your details below to estimate your savings at retirement, monthly income, and whether you're on track to meet your goals — no account required.

<div id="ps-app">
<style>
#ps-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1e293b;
max-width: 860px;
margin: 0 auto;
padding: 0 0 2rem 0;
}
#ps-app * {
box-sizing: border-box;
}
#ps-app .ps-section-title {
font-size: 1rem;
font-weight: 700;
color: #475569;
text-transform: uppercase;
letter-spacing: 0.07em;
margin: 1.8rem 0 0.8rem 0;
}
#ps-app .ps-presets {
display: flex;
gap: 0.5rem;
margin-bottom: 1.4rem;
flex-wrap: wrap;
}
#ps-app .ps-preset-btn {
padding: 0.4rem 1.1rem;
border-radius: 999px;
border: 1.5px solid #cbd5e1;
background: #f8fafc;
color: #475569;
font-size: 0.875rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}
#ps-app .ps-preset-btn:hover,
#ps-app .ps-preset-btn.active {
background: #1e293b;
border-color: #1e293b;
color: #f8fafc;
}
#ps-app .ps-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem 1.5rem;
}
@media (max-width: 560px) {
#ps-app .ps-grid {
grid-template-columns: 1fr;
}
}
#ps-app .ps-field {
display: flex;
flex-direction: column;
gap: 0.3rem;
}
#ps-app .ps-field label {
font-size: 0.85rem;
font-weight: 600;
color: #475569;
}
#ps-app .ps-field input {
padding: 0.5rem 0.75rem;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 1rem;
color: #1e293b;
background: #f8fafc;
outline: none;
transition: border-color 0.15s;
width: 100%;
}
#ps-app .ps-field input:focus {
border-color: #475569;
background: #fff;
}
#ps-app .ps-field .ps-hint {
font-size: 0.75rem;
color: #94a3b8;
}
#ps-app .ps-calc-btn {
margin-top: 1.4rem;
width: 100%;
padding: 0.85rem;
border: none;
border-radius: 10px;
background: #1e293b;
color: #f8fafc;
font-size: 1.05rem;
font-weight: 700;
cursor: pointer;
letter-spacing: 0.02em;
transition: background 0.15s;
}
#ps-app .ps-calc-btn:hover {
background: #475569;
}
#ps-app .ps-results {
margin-top: 2rem;
display: none;
}
#ps-app .ps-results.visible {
display: block;
}
#ps-app .ps-cards {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 0.85rem;
margin-bottom: 1.4rem;
}
@media (max-width: 640px) {
#ps-app .ps-cards {
grid-template-columns: 1fr 1fr;
}
}
@media (max-width: 380px) {
#ps-app .ps-cards {
grid-template-columns: 1fr;
}
}
#ps-app .ps-card {
background: #f8fafc;
border: 1.5px solid #cbd5e1;
border-radius: 12px;
padding: 1rem 1.1rem;
display: flex;
flex-direction: column;
gap: 0.25rem;
}
#ps-app .ps-card .ps-card-label {
font-size: 0.75rem;
font-weight: 700;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#ps-app .ps-card .ps-card-value {
font-size: 1.35rem;
font-weight: 800;
color: #1e293b;
word-break: break-all;
}
#ps-app .ps-card .ps-card-sub {
font-size: 0.78rem;
color: #64748b;
}
#ps-app .ps-status-bar {
border-radius: 10px;
padding: 0.85rem 1.1rem;
font-size: 0.95rem;
font-weight: 600;
margin-bottom: 1.4rem;
}
#ps-app .ps-status-bar.green {
background: #dcfce7;
color: #166534;
border: 1.5px solid #86efac;
}
#ps-app .ps-status-bar.orange {
background: #fff7ed;
color: #9a3412;
border: 1.5px solid #fed7aa;
}
#ps-app .ps-status-bar.red {
background: #fef2f2;
color: #991b1b;
border: 1.5px solid #fecaca;
}
#ps-app .ps-chart-wrap {
background: #f8fafc;
border: 1.5px solid #cbd5e1;
border-radius: 12px;
padding: 1.2rem 1.2rem 0.8rem 1.2rem;
margin-bottom: 1.2rem;
}
#ps-app .ps-chart-title {
font-size: 0.85rem;
font-weight: 700;
color: #475569;
margin-bottom: 0.8rem;
}
#ps-app canvas#ps-chart {
width: 100%;
display: block;
}
#ps-app .ps-extra-cards {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 0.85rem;
margin-bottom: 0.5rem;
}
@media (max-width: 480px) {
#ps-app .ps-extra-cards {
grid-template-columns: 1fr;
}
}
#ps-app .ps-card.highlight {
border-color: #1e293b;
background: #1e293b;
}
#ps-app .ps-card.highlight .ps-card-label,
#ps-app .ps-card.highlight .ps-card-sub {
color: #94a3b8;
}
#ps-app .ps-card.highlight .ps-card-value {
color: #f8fafc;
}
</style>

<div class="ps-section-title">Scenario Preset</div>
<div class="ps-presets">
<button class="ps-preset-btn" id="ps-preset-conservative" onclick="psSetPreset('conservative')">Conservative</button>
<button class="ps-preset-btn active" id="ps-preset-moderate" onclick="psSetPreset('moderate')">Moderate</button>
<button class="ps-preset-btn" id="ps-preset-aggressive" onclick="psSetPreset('aggressive')">Aggressive</button>
</div>

<div class="ps-section-title">Your Details</div>
<div class="ps-grid">
<div class="ps-field">
<label for="ps-current-age">Current Age</label>
<input type="number" id="ps-current-age" value="30" min="16" max="99" />
</div>
<div class="ps-field">
<label for="ps-retire-age">Retirement Age</label>
<input type="number" id="ps-retire-age" value="65" min="40" max="99" />
</div>
<div class="ps-field">
<label for="ps-savings">Current Savings ($)</label>
<input type="number" id="ps-savings" value="50000" min="0" />
<span class="ps-hint">Total already saved for retirement</span>
</div>
<div class="ps-field">
<label for="ps-monthly-contrib">Monthly Contribution ($)</label>
<input type="number" id="ps-monthly-contrib" value="500" min="0" />
</div>
<div class="ps-field">
<label for="ps-return">Expected Annual Return (%)</label>
<input type="number" id="ps-return" value="7" min="0" max="30" step="0.1" />
</div>
<div class="ps-field">
<label for="ps-inflation">Expected Inflation Rate (%)</label>
<input type="number" id="ps-inflation" value="2.5" min="0" max="20" step="0.1" />
</div>
<div class="ps-field">
<label for="ps-desired-income">Desired Monthly Income in Retirement ($)</label>
<input type="number" id="ps-desired-income" value="3000" min="0" />
</div>
<div class="ps-field">
<label for="ps-life-exp">Life Expectancy</label>
<input type="number" id="ps-life-exp" value="90" min="60" max="120" />
</div>
</div>

<button class="ps-calc-btn" onclick="psCalculate()">Calculate</button>

<div class="ps-results" id="ps-results">
<div class="ps-section-title">Results</div>

<div id="ps-status-bar" class="ps-status-bar green"></div>

<div class="ps-cards" id="ps-cards-main">
<div class="ps-card">
<div class="ps-card-label">Savings at Retirement</div>
<div class="ps-card-value" id="ps-r-total"></div>
<div class="ps-card-sub">Nominal (before inflation)</div>
</div>
<div class="ps-card">
<div class="ps-card-label">Real Savings (today's $)</div>
<div class="ps-card-value" id="ps-r-real"></div>
<div class="ps-card-sub">Inflation-adjusted</div>
</div>
<div class="ps-card">
<div class="ps-card-label">Monthly Pension Income</div>
<div class="ps-card-value" id="ps-r-monthly"></div>
<div class="ps-card-sub">From savings (real terms)</div>
</div>
</div>

<div class="ps-chart-wrap">
<div class="ps-chart-title">Savings Growth by Decade</div>
<canvas id="ps-chart" height="220"></canvas>
</div>

<div class="ps-extra-cards">
<div class="ps-card">
<div class="ps-card-label">Monthly Shortfall / Surplus</div>
<div class="ps-card-value" id="ps-r-gap"></div>
<div class="ps-card-sub">vs. desired monthly income</div>
</div>
<div class="ps-card">
<div class="ps-card-label">Required Monthly Contribution</div>
<div class="ps-card-value" id="ps-r-required"></div>
<div class="ps-card-sub">To meet desired income</div>
</div>
<div class="ps-card">
<div class="ps-card-label">Years Savings Will Last</div>
<div class="ps-card-value" id="ps-r-years"></div>
<div class="ps-card-sub">At desired withdrawal rate</div>
</div>
<div class="ps-card highlight">
<div class="ps-card-label">Retirement Duration</div>
<div class="ps-card-value" id="ps-r-duration"></div>
<div class="ps-card-sub">Years in retirement (target)</div>
</div>
</div>
</div>

<script>
(function () {
var PS = {};

var presets = {
conservative: { ret: 4.5, inf: 2.0 },
moderate:     { ret: 7.0, inf: 2.5 },
aggressive:   { ret: 10.0, inf: 3.0 }
};

window.psSetPreset = function (name) {
var p = presets[name];
if (!p) return;
document.getElementById('ps-return').value = p.ret;
document.getElementById('ps-inflation').value = p.inf;
['conservative', 'moderate', 'aggressive'].forEach(function (k) {
var btn = document.getElementById('ps-preset-' + k);
if (btn) btn.classList.toggle('active', k === name);
});
};

function fmt(n, decimals) {
if (decimals === undefined) decimals = 0;
return '$' + n.toFixed(decimals).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}

function fmtPlain(n, decimals) {
if (decimals === undefined) decimals = 1;
return n.toFixed(decimals).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}

function val(id) {
return parseFloat(document.getElementById(id).value) || 0;
}

window.psCalculate = function () {
var currentAge   = val('ps-current-age');
var retireAge    = val('ps-retire-age');
var savings      = val('ps-savings');
var monthly      = val('ps-monthly-contrib');
var annualReturn = val('ps-return') / 100;
var inflation    = val('ps-inflation') / 100;
var desiredIncome= val('ps-desired-income');
var lifeExp      = val('ps-life-exp');

if (retireAge <= currentAge) {
alert('Retirement age must be greater than current age.');
return;
}
if (lifeExp <= retireAge) {
alert('Life expectancy must be greater than retirement age.');
return;
}

var yearsToRetire  = retireAge - currentAge;
var yearsInRetire  = lifeExp - retireAge;
var monthlyRate    = annualReturn / 12;
var months         = yearsToRetire * 12;

// Future value of lump sum
var fvLump = savings * Math.pow(1 + annualReturn, yearsToRetire);

// Future value of monthly contributions (annuity)
var fvContrib = 0;
if (monthlyRate > 0) {
fvContrib = monthly * ((Math.pow(1 + monthlyRate, months) - 1) / monthlyRate);
} else {
fvContrib = monthly * months;
}

var totalNominal = fvLump + fvContrib;

// Real (inflation-adjusted) value
var totalReal = totalNominal / Math.pow(1 + inflation, yearsToRetire);

// Monthly pension income using annuity formula (real terms, using real rate)
var realRate = (1 + annualReturn) / (1 + inflation) - 1;
var monthlyRealRate = realRate / 12;
var retireMonths = yearsInRetire * 12;
var monthlyIncome;
if (monthlyRealRate > 0) {
monthlyIncome = totalReal * (monthlyRealRate * Math.pow(1 + monthlyRealRate, retireMonths))
/ (Math.pow(1 + monthlyRealRate, retireMonths) - 1);
} else {
monthlyIncome = totalReal / retireMonths;
}

// Gap
var gap = monthlyIncome - desiredIncome;

// Required monthly contribution to meet desired income
// Work backwards: needed total real = PV of annuity at desiredIncome
var neededReal;
if (monthlyRealRate > 0) {
neededReal = desiredIncome * (1 - Math.pow(1 + monthlyRealRate, -retireMonths)) / monthlyRealRate;
} else {
neededReal = desiredIncome * retireMonths;
}
var neededNominal = neededReal * Math.pow(1 + inflation, yearsToRetire);
var neededFromContrib = neededNominal - fvLump;
var requiredMonthly;
if (neededFromContrib <= 0) {
requiredMonthly = 0;
} else if (monthlyRate > 0) {
requiredMonthly = neededFromContrib * monthlyRate / (Math.pow(1 + monthlyRate, months) - 1);
} else {
requiredMonthly = neededFromContrib / months;
}

// Years savings will last at desired withdrawal rate (real terms)
var yearsSavingsLast;
var monthlyDesiredReal = desiredIncome;
if (monthlyRealRate > 0 && monthlyDesiredReal > 0) {
// n = -ln(1 - P*r/PMT) / ln(1+r)   where P=totalReal, r=monthlyRealRate, PMT=monthlyDesiredReal
var ratio = totalReal * monthlyRealRate / monthlyDesiredReal;
if (ratio >= 1) {
yearsSavingsLast = Infinity;
} else {
var nMonths = -Math.log(1 - ratio) / Math.log(1 + monthlyRealRate);
yearsSavingsLast = nMonths / 12;
}
} else if (monthlyDesiredReal > 0) {
yearsSavingsLast = totalReal / (monthlyDesiredReal * 12);
} else {
yearsSavingsLast = Infinity;
}

// Status
var statusEl = document.getElementById('ps-status-bar');
statusEl.className = 'ps-status-bar';
var statusMsg;
if (gap >= 0) {
statusEl.classList.add('green');
statusMsg = 'You are ON TRACK. Your projected monthly income exceeds your desired retirement income.';
} else if (gap >= -desiredIncome * 0.2) {
statusEl.classList.add('orange');
statusMsg = 'You are CLOSE. Your projected income falls slightly short — a small increase in contributions can close the gap.';
} else {
statusEl.classList.add('red');
statusMsg = 'SHORTFALL DETECTED. Your projected income is significantly below your desired amount. See the required contribution below.';
}
statusEl.textContent = statusMsg;

// Populate cards
document.getElementById('ps-r-total').textContent   = fmt(totalNominal);
document.getElementById('ps-r-real').textContent    = fmt(totalReal);
document.getElementById('ps-r-monthly').textContent = fmt(monthlyIncome);

var gapText = (gap >= 0 ? '+' : '') + fmt(gap);
document.getElementById('ps-r-gap').textContent      = gapText;
document.getElementById('ps-r-gap').style.color      = gap >= 0 ? '#166534' : '#991b1b';
document.getElementById('ps-r-required').textContent = fmt(requiredMonthly);
document.getElementById('ps-r-duration').textContent = yearsInRetire + ' yrs';

if (!isFinite(yearsSavingsLast)) {
document.getElementById('ps-r-years').textContent = 'Forever';
} else {
document.getElementById('ps-r-years').textContent = fmtPlain(yearsSavingsLast, 1) + ' yrs';
}

// Show results
document.getElementById('ps-results').classList.add('visible');

// Draw chart
drawChart(currentAge, retireAge, savings, monthly, monthlyRate, annualReturn, inflation);
};

function drawChart(currentAge, retireAge, savings, monthly, monthlyRate, annualReturn, inflation) {
var canvas = document.getElementById('ps-chart');
var dpr = window.devicePixelRatio || 1;
var cssWidth = canvas.parentElement.clientWidth - 48;
canvas.style.width = cssWidth + 'px';
canvas.style.height = '220px';
canvas.width  = cssWidth * dpr;
canvas.height = 220 * dpr;
var ctx = canvas.getContext('2d');
ctx.scale(dpr, dpr);

var W = cssWidth;
var H = 220;
ctx.clearRect(0, 0, W, H);

// Build decade data points
var points = [];
var startAge = currentAge;
var endAge = retireAge;

// Collect ages at each decade boundary + retirement
var ages = [];
var firstDecade = Math.ceil(startAge / 10) * 10;
for (var a = firstDecade; a <= endAge; a += 10) {
ages.push(a);
}
if (ages.length === 0 || ages[ages.length - 1] !== endAge) {
ages.push(endAge);
}

ages.forEach(function (age) {
var years = age - startAge;
var months = years * 12;
var fvL = savings * Math.pow(1 + annualReturn, years);
var fvC;
if (monthlyRate > 0) {
fvC = monthly * ((Math.pow(1 + monthlyRate, months) - 1) / monthlyRate);
} else {
fvC = monthly * months;
}
var nominal = fvL + fvC;
var real = nominal / Math.pow(1 + inflation, years);
points.push({ age: age, nominal: nominal, real: real });
});

if (points.length === 0) return;

var maxVal = Math.max.apply(null, points.map(function (p) { return p.nominal; }));
if (maxVal === 0) return;

var padLeft = 70, padRight = 16, padTop = 16, padBottom = 48;
var chartW = W - padLeft - padRight;
var chartH = H - padTop - padBottom;
var n = points.length;
var groupW = chartW / n;
var barW = Math.max(groupW * 0.35, 6);

// Axes
ctx.strokeStyle = '#cbd5e1';
ctx.lineWidth = 1;
ctx.beginPath();
ctx.moveTo(padLeft, padTop);
ctx.lineTo(padLeft, padTop + chartH);
ctx.lineTo(padLeft + chartW, padTop + chartH);
ctx.stroke();

// Y gridlines + labels
var steps = 4;
ctx.textAlign = 'right';
ctx.font = '11px system-ui, sans-serif';
ctx.fillStyle = '#94a3b8';
for (var i = 0; i <= steps; i++) {
var yVal = (maxVal / steps) * i;
var yPx  = padTop + chartH - (yVal / maxVal) * chartH;
ctx.strokeStyle = '#e2e8f0';
ctx.lineWidth = 0.5;
ctx.beginPath();
ctx.moveTo(padLeft, yPx);
ctx.lineTo(padLeft + chartW, yPx);
ctx.stroke();
var label = yVal >= 1e6 ? (yVal / 1e6).toFixed(1) + 'M' : yVal >= 1e3 ? (yVal / 1e3).toFixed(0) + 'K' : yVal.toFixed(0);
ctx.fillStyle = '#94a3b8';
ctx.fillText('$' + label, padLeft - 6, yPx + 4);
}

// Bars
points.forEach(function (p, idx) {
var cx = padLeft + groupW * idx + groupW / 2;
var nomH = (p.nominal / maxVal) * chartH;
var realH = (p.real / maxVal) * chartH;

// Nominal bar
ctx.fillStyle = '#1e293b';
ctx.beginPath();
ctx.roundRect
? ctx.roundRect(cx - barW - 2, padTop + chartH - nomH, barW, nomH, [3, 3, 0, 0])
: ctx.rect(cx - barW - 2, padTop + chartH - nomH, barW, nomH);
ctx.fill();

// Real bar
ctx.fillStyle = '#94a3b8';
ctx.beginPath();
ctx.roundRect
? ctx.roundRect(cx + 2, padTop + chartH - realH, barW, realH, [3, 3, 0, 0])
: ctx.rect(cx + 2, padTop + chartH - realH, barW, realH);
ctx.fill();

// Age label
ctx.textAlign = 'center';
ctx.fillStyle = '#64748b';
ctx.font = '11px system-ui, sans-serif';
ctx.fillText('Age ' + p.age, cx, padTop + chartH + 16);
});

// Legend
var lx = padLeft + chartW - 180;
var ly = padTop + 4;
ctx.fillStyle = '#1e293b';
ctx.fillRect(lx, ly, 14, 10);
ctx.fillStyle = '#64748b';
ctx.textAlign = 'left';
ctx.font = '11px system-ui, sans-serif';
ctx.fillText('Nominal', lx + 18, ly + 9);

ctx.fillStyle = '#94a3b8';
ctx.fillRect(lx + 80, ly, 14, 10);
ctx.fillStyle = '#64748b';
ctx.fillText('Real (today\'s $)', lx + 98, ly + 9);
}
})();
</script>

</div>

---

> Calculate take-home pay → [Salary Calculator](/tools/salary-calculator/)
> Plan your budget → [50/30/20 Budget Calculator](/tools/budget-planner/)
> Track compound growth → [Compound Interest Calculator](/tools/compound-interest-calculator/)

## Related Articles

- [Retirement Planning in Japan for Foreign Residents: What the Pension System Won't Cover](/posts/retirement-planning-japan-foreign-resident/)
