---
title: "Body Fat Calculator - Estimate Your Body Fat Percentage"
date: 2025-05-16
description: "Calculate body fat percentage using US Navy and BMI methods. Get personalized fitness category and health insights."
categories: ["Free Tools"]
slug: "body-fat-calculator"
ShowToc: false
cover:
  image: "/images/covers/body-fat-calculator.png"
  alt: "Body Fat Calculator"
---

<div id="bf-app">

<style>
#bf-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 720px;
margin: 0 auto;
color: #1a1a2e;
}
#bf-app * { box-sizing: border-box; }
#bf-app h2 {
font-size: 1.4rem;
font-weight: 700;
margin: 1.5rem 0 0.75rem;
color: #0f3460;
border-left: 4px solid #e94560;
padding-left: 0.6rem;
}
#bf-app .gender-row {
display: flex;
gap: 12px;
margin-bottom: 1.2rem;
}
#bf-app .gender-btn {
flex: 1;
padding: 12px;
border: 2px solid #dde3f0;
border-radius: 10px;
background: #f8faff;
cursor: pointer;
font-size: 1rem;
font-weight: 600;
color: #555;
transition: all 0.2s;
}
#bf-app .gender-btn.active {
border-color: #e94560;
background: #fff0f3;
color: #e94560;
}
#bf-app .input-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 14px;
margin-bottom: 1.2rem;
}
#bf-app .input-group {
display: flex;
flex-direction: column;
gap: 4px;
}
#bf-app .input-group label {
font-size: 0.82rem;
font-weight: 600;
color: #555;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#bf-app .input-group .input-wrap {
position: relative;
}
#bf-app .input-group input {
width: 100%;
padding: 10px 42px 10px 12px;
border: 2px solid #dde3f0;
border-radius: 8px;
font-size: 1rem;
background: #f8faff;
transition: border-color 0.2s;
outline: none;
}
#bf-app .input-group input:focus {
border-color: #0f3460;
background: #fff;
}
#bf-app .input-group .unit {
position: absolute;
right: 10px;
top: 50%;
transform: translateY(-50%);
font-size: 0.8rem;
color: #888;
font-weight: 600;
pointer-events: none;
}
#bf-app .calc-btn {
width: 100%;
padding: 14px;
background: linear-gradient(135deg, #0f3460, #e94560);
color: #fff;
border: none;
border-radius: 10px;
font-size: 1.1rem;
font-weight: 700;
cursor: pointer;
transition: opacity 0.2s;
margin-bottom: 1.5rem;
}
#bf-app .calc-btn:hover { opacity: 0.9; }
#bf-app .results {
display: none;
animation: bfFadeIn 0.4s ease;
}
@keyframes bfFadeIn {
from { opacity: 0; transform: translateY(12px); }
to   { opacity: 1; transform: translateY(0); }
}
#bf-app .result-hero {
text-align: center;
background: linear-gradient(135deg, #0f3460 0%, #16213e 100%);
border-radius: 14px;
padding: 2rem 1rem 1.5rem;
color: #fff;
margin-bottom: 1.2rem;
}
#bf-app .result-hero .pct {
font-size: 3.5rem;
font-weight: 800;
line-height: 1;
margin-bottom: 0.3rem;
}
#bf-app .result-hero .cat-badge {
display: inline-block;
padding: 4px 18px;
border-radius: 20px;
font-size: 0.95rem;
font-weight: 700;
margin-bottom: 1rem;
}
#bf-app .gauge-container {
margin: 0.8rem auto 0;
max-width: 420px;
}
#bf-app .gauge-bar {
height: 18px;
border-radius: 9px;
background: linear-gradient(to right, #4caf50, #8bc34a, #ffeb3b, #ff9800, #f44336);
position: relative;
overflow: visible;
}
#bf-app .gauge-needle {
position: absolute;
top: -6px;
width: 4px;
height: 30px;
background: #fff;
border-radius: 2px;
transform: translateX(-50%);
box-shadow: 0 0 0 2px rgba(0,0,0,0.4);
transition: left 0.6s cubic-bezier(0.34,1.56,0.64,1);
}
#bf-app .gauge-labels {
display: flex;
justify-content: space-between;
margin-top: 6px;
font-size: 0.68rem;
color: rgba(255,255,255,0.7);
}
#bf-app .stats-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
margin-bottom: 1.2rem;
}
#bf-app .stat-card {
background: #f8faff;
border: 2px solid #dde3f0;
border-radius: 12px;
padding: 1rem;
text-align: center;
}
#bf-app .stat-card .stat-val {
font-size: 1.8rem;
font-weight: 800;
color: #0f3460;
}
#bf-app .stat-card .stat-lbl {
font-size: 0.78rem;
color: #777;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.03em;
}
#bf-app .chart-wrap {
display: flex;
align-items: center;
gap: 1.5rem;
background: #f8faff;
border: 2px solid #dde3f0;
border-radius: 12px;
padding: 1.2rem 1.5rem;
margin-bottom: 1.2rem;
}
#bf-app canvas#bfPie {
flex-shrink: 0;
}
#bf-app .legend {
flex: 1;
}
#bf-app .legend-item {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 10px;
font-size: 0.9rem;
}
#bf-app .legend-dot {
width: 14px;
height: 14px;
border-radius: 4px;
flex-shrink: 0;
}
#bf-app .legend-val {
font-weight: 700;
font-size: 1rem;
color: #0f3460;
}
#bf-app .methods-note {
background: #fffbf0;
border: 1px solid #ffe082;
border-radius: 10px;
padding: 1rem 1.2rem;
font-size: 0.84rem;
color: #7a6000;
line-height: 1.6;
margin-bottom: 1.2rem;
}
#bf-app .category-table {
width: 100%;
border-collapse: collapse;
font-size: 0.85rem;
margin-bottom: 1.5rem;
}
#bf-app .category-table th {
background: #0f3460;
color: #fff;
padding: 8px 12px;
text-align: left;
font-weight: 600;
}
#bf-app .category-table td {
padding: 7px 12px;
border-bottom: 1px solid #eee;
}
#bf-app .category-table tr:nth-child(even) td { background: #f8faff; }
#bf-app .category-table tr.highlight td {
background: #fff0f3 !important;
font-weight: 700;
color: #e94560;
}
#bf-app .related-tools {
background: #f0f4ff;
border-radius: 12px;
padding: 1.2rem 1.5rem;
margin-top: 1.5rem;
}
#bf-app .related-tools h3 {
margin: 0 0 0.8rem;
font-size: 1rem;
color: #0f3460;
font-weight: 700;
}
#bf-app .related-tools ul {
margin: 0;
padding-left: 1.2rem;
}
#bf-app .related-tools li {
margin-bottom: 6px;
font-size: 0.9rem;
}
#bf-app .related-tools a {
color: #0f3460;
text-decoration: none;
font-weight: 600;
}
#bf-app .related-tools a:hover { color: #e94560; text-decoration: underline; }
#bf-app .error-msg {
color: #e94560;
font-size: 0.88rem;
font-weight: 600;
margin-bottom: 0.8rem;
display: none;
padding: 8px 12px;
background: #fff0f3;
border-radius: 8px;
border: 1px solid #ffc0cb;
}
@media (max-width: 500px) {
#bf-app .input-grid { grid-template-columns: 1fr; }
#bf-app .stats-grid { grid-template-columns: 1fr 1fr; }
#bf-app .chart-wrap { flex-direction: column; }
}
</style>

<h2>Body Fat Calculator</h2>

<div class="gender-row">
<button class="gender-btn active" id="btnMale" onclick="bfSetGender('male')">Male</button>
<button class="gender-btn" id="btnFemale" onclick="bfSetGender('female')">Female</button>
</div>

<div class="input-grid">
<div class="input-group">
<label>Height</label>
<div class="input-wrap">
<input type="number" id="bfHeight" placeholder="175" min="100" max="250" value="">
<span class="unit">cm</span>
</div>
</div>
<div class="input-group">
<label>Weight</label>
<div class="input-wrap">
<input type="number" id="bfWeight" placeholder="75" min="30" max="300" value="">
<span class="unit">kg</span>
</div>
</div>
<div class="input-group">
<label>Waist</label>
<div class="input-wrap">
<input type="number" id="bfWaist" placeholder="85" min="40" max="200" value="">
<span class="unit">cm</span>
</div>
</div>
<div class="input-group">
<label>Neck</label>
<div class="input-wrap">
<input type="number" id="bfNeck" placeholder="38" min="20" max="80" value="">
<span class="unit">cm</span>
</div>
</div>
<div class="input-group" id="hipGroup" style="display:none;">
<label>Hip</label>
<div class="input-wrap">
<input type="number" id="bfHip" placeholder="95" min="50" max="200" value="">
<span class="unit">cm</span>
</div>
</div>
<div class="input-group">
<label>Age</label>
<div class="input-wrap">
<input type="number" id="bfAge" placeholder="30" min="10" max="120" value="">
<span class="unit">yrs</span>
</div>
</div>
</div>

<div class="error-msg" id="bfError"></div>

<button class="calc-btn" onclick="bfCalculate()">Calculate Body Fat</button>

<div class="results" id="bfResults">
<div class="result-hero">
<div class="pct" id="bfPctDisplay">--%</div>
<div class="cat-badge" id="bfCatBadge">--</div>
<div class="gauge-container">
<div class="gauge-bar">
<div class="gauge-needle" id="bfNeedle" style="left:0%"></div>
</div>
<div class="gauge-labels">
<span>Essential</span>
<span>Athletic</span>
<span>Fitness</span>
<span>Average</span>
<span>Obese</span>
</div>
</div>
</div>

<div class="stats-grid">
<div class="stat-card">
<div class="stat-val" id="bfNavyVal">--%</div>
<div class="stat-lbl">US Navy Method</div>
</div>
<div class="stat-card">
<div class="stat-val" id="bfBmiVal">--%</div>
<div class="stat-lbl">BMI Method</div>
</div>
<div class="stat-card">
<div class="stat-val" id="bfLeanVal">-- kg</div>
<div class="stat-lbl">Lean Mass</div>
</div>
<div class="stat-card">
<div class="stat-val" id="bfFatVal">-- kg</div>
<div class="stat-lbl">Fat Mass</div>
</div>
</div>

<div class="chart-wrap">
<canvas id="bfPie" width="140" height="140"></canvas>
<div class="legend">
<div class="legend-item">
<div class="legend-dot" style="background:#e94560;"></div>
<div>
<div class="legend-val" id="lgFatPct">--%</div>
<div style="color:#777;font-size:0.8rem;">Body Fat</div>
</div>
</div>
<div class="legend-item">
<div class="legend-dot" style="background:#0f3460;"></div>
<div>
<div class="legend-val" id="lgLeanPct">--%</div>
<div style="color:#777;font-size:0.8rem;">Lean Mass (muscle, bone, water)</div>
</div>
</div>
</div>
</div>

<div class="methods-note">
<strong>How it works:</strong> The <strong>US Navy method</strong> uses circumference measurements (waist, neck, hip for women) with a logarithmic formula validated by the US military. The <strong>BMI-based method</strong> uses the Deurenberg formula: BF% = (1.20 × BMI) + (0.23 × Age) − (10.8 × sex) − 5.4. Results are averaged for the displayed figure. These are estimates — DEXA scan is the gold standard.
</div>

<h2>Body Fat Categories</h2>
<table class="category-table" id="bfCatTable">
<thead>
<tr><th>Category</th><th>Men</th><th>Women</th></tr>
</thead>
<tbody>
<tr id="catEssential"><td>Essential Fat</td><td>2–5%</td><td>10–13%</td></tr>
<tr id="catAthletes"><td>Athletes</td><td>6–13%</td><td>14–20%</td></tr>
<tr id="catFitness"><td>Fitness</td><td>14–17%</td><td>21–24%</td></tr>
<tr id="catAverage"><td>Average</td><td>18–24%</td><td>25–31%</td></tr>
<tr id="catObese"><td>Obese</td><td>25%+</td><td>32%+</td></tr>
</tbody>
</table>

<div class="related-tools">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/bmi-calculator/">BMI Calculator</a> — Check your body mass index</li>
<li><a href="/tools/calorie-calculator/">Calorie Calculator</a> — Daily calorie needs based on your stats</li>
<li><a href="/tools/calorie-calculator/">TDEE Calculator</a> — Total daily energy expenditure</li>
<li><a href="/tools/bmi-calculator/">Ideal Weight Calculator</a> — Find your target weight range</li>
</ul>
</div>
</div>

<script>
(function() {
var bfGender = 'male';

window.bfSetGender = function(g) {
bfGender = g;
document.getElementById('btnMale').classList.toggle('active', g === 'male');
document.getElementById('btnFemale').classList.toggle('active', g === 'female');
document.getElementById('hipGroup').style.display = g === 'female' ? '' : 'none';
};

function bfNavy(gender, height, waist, neck, hip) {
if (gender === 'male') {
return 495 / (1.0324 - 0.19077 * Math.log10(waist - neck) + 0.15456 * Math.log10(height)) - 450;
} else {
return 495 / (1.29579 - 0.35004 * Math.log10(waist + hip - neck) + 0.22100 * Math.log10(height)) - 450;
}
}

function bfBmi(bmi, age, gender) {
var sex = gender === 'male' ? 1 : 0;
return (1.20 * bmi) + (0.23 * age) - (10.8 * sex) - 5.4;
}

function getCategory(bf, gender) {
if (gender === 'male') {
if (bf < 6)  return { name: 'Essential Fat', color: '#4caf50', row: 'catEssential', pos: 5 };
if (bf < 14) return { name: 'Athletes',      color: '#8bc34a', row: 'catAthletes',  pos: 22 };
if (bf < 18) return { name: 'Fitness',       color: '#ffeb3b', row: 'catFitness',   pos: 43 };
if (bf < 25) return { name: 'Average',       color: '#ff9800', row: 'catAverage',   pos: 65 };
return               { name: 'Obese',         color: '#f44336', row: 'catObese',    pos: 88 };
} else {
if (bf < 14) return { name: 'Essential Fat', color: '#4caf50', row: 'catEssential', pos: 5 };
if (bf < 21) return { name: 'Athletes',      color: '#8bc34a', row: 'catAthletes',  pos: 22 };
if (bf < 25) return { name: 'Fitness',       color: '#ffeb3b', row: 'catFitness',   pos: 43 };
if (bf < 32) return { name: 'Average',       color: '#ff9800', row: 'catAverage',   pos: 65 };
return               { name: 'Obese',         color: '#f44336', row: 'catObese',    pos: 88 };
}
}

function drawPie(fatPct) {
var canvas = document.getElementById('bfPie');
if (!canvas) return;
var ctx = canvas.getContext('2d');
var cx = 70, cy = 70, r = 58;
ctx.clearRect(0, 0, 140, 140);
var fatAngle = (fatPct / 100) * Math.PI * 2;
// Fat slice
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, -Math.PI/2, -Math.PI/2 + fatAngle);
ctx.closePath();
ctx.fillStyle = '#e94560';
ctx.fill();
// Lean slice
ctx.beginPath();
ctx.moveTo(cx, cy);
ctx.arc(cx, cy, r, -Math.PI/2 + fatAngle, -Math.PI/2 + Math.PI*2);
ctx.closePath();
ctx.fillStyle = '#0f3460';
ctx.fill();
// Center hole
ctx.beginPath();
ctx.arc(cx, cy, r * 0.52, 0, Math.PI * 2);
ctx.fillStyle = '#f8faff';
ctx.fill();
// Center label
ctx.fillStyle = '#0f3460';
ctx.font = 'bold 16px sans-serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
ctx.fillText(fatPct.toFixed(1) + '%', cx, cy);
}

window.bfCalculate = function() {
var errEl = document.getElementById('bfError');
errEl.style.display = 'none';

var h = parseFloat(document.getElementById('bfHeight').value);
var w = parseFloat(document.getElementById('bfWeight').value);
var waist = parseFloat(document.getElementById('bfWaist').value);
var neck  = parseFloat(document.getElementById('bfNeck').value);
var age   = parseFloat(document.getElementById('bfAge').value);
var hip   = parseFloat(document.getElementById('bfHip').value);

if (!h || !w || !waist || !neck || !age) {
errEl.textContent = 'Please fill in all required fields (height, weight, waist, neck, age).';
errEl.style.display = 'block';
return;
}
if (bfGender === 'female' && !hip) {
errEl.textContent = 'Hip measurement is required for women.';
errEl.style.display = 'block';
return;
}
if (waist <= neck) {
errEl.textContent = 'Waist must be larger than neck measurement.';
errEl.style.display = 'block';
return;
}

var navy = bfNavy(bfGender, h, waist, neck, hip || 0);
var bmi  = w / ((h/100) * (h/100));
var bmiMethod = bfBmi(bmi, age, bfGender);

// Clamp to reasonable range
navy     = Math.max(2, Math.min(70, navy));
bmiMethod = Math.max(2, Math.min(70, bmiMethod));

var avg = (navy + bmiMethod) / 2;
var fatMass = (avg / 100) * w;
var leanMass = w - fatMass;

var cat = getCategory(avg, bfGender);

// Update hero
document.getElementById('bfPctDisplay').textContent = avg.toFixed(1) + '%';
var badge = document.getElementById('bfCatBadge');
badge.textContent = cat.name;
badge.style.background = cat.color + '33';
badge.style.color = cat.color;
badge.style.border = '1.5px solid ' + cat.color;

// Gauge needle
document.getElementById('bfNeedle').style.left = cat.pos + '%';

// Stats
document.getElementById('bfNavyVal').textContent = navy.toFixed(1) + '%';
document.getElementById('bfBmiVal').textContent  = bmiMethod.toFixed(1) + '%';
document.getElementById('bfLeanVal').textContent = leanMass.toFixed(1) + ' kg';
document.getElementById('bfFatVal').textContent  = fatMass.toFixed(1) + ' kg';

// Legend
document.getElementById('lgFatPct').textContent  = avg.toFixed(1) + '%';
document.getElementById('lgLeanPct').textContent = (100 - avg).toFixed(1) + '%';

// Pie
drawPie(avg);

// Highlight table row
['catEssential','catAthletes','catFitness','catAverage','catObese'].forEach(function(id) {
document.getElementById(id).classList.remove('highlight');
});
document.getElementById(cat.row).classList.add('highlight');

// Show results
var res = document.getElementById('bfResults');
res.style.display = 'block';
res.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
};

// Allow Enter key
document.addEventListener('keydown', function(e) {
if (e.key === 'Enter' && document.activeElement && document.activeElement.closest('#bf-app')) {
bfCalculate();
}
});
})();
</script>

</div>

---

## Related Tools

> [Bmi Calculator](/tools/bmi-calculator/)
> [Calorie Calculator](/tools/calorie-calculator/)
> [Water Intake Calculator](/tools/water-intake-calculator/)

