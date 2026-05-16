---
title: "BMI Calculator | Check Your Body Mass Index Instantly"
date: 2026-05-16
draft: false
slug: "bmi-calculator"
aliases: ["/tools/bmi-calculator/"]
description: "Free BMI calculator. Enter your height and weight to instantly calculate your Body Mass Index, see your BMI category, and get a healthy weight range for your height."
categories: ["Free Tools"]
tags: ["BMI", "body mass index", "health calculator", "weight", "fitness"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/bmi-calculator.png"
  alt: "BMI Calculator | Check Your Body Mass Index Instantly"
  relative: false
---

*This page contains affiliate links. We may earn a commission at no extra cost to you if you make a purchase through these links. Our editorial opinions remain independent.*

# BMI Calculator

Your **Body Mass Index (BMI)** is a simple number derived from your height and weight that helps gauge whether you are in a healthy weight range. Use this free calculator to find your BMI instantly — no sign-up required. Toggle between Imperial (lb/ft) and Metric (kg/cm), and get a color-coded result along with your healthy weight range and a personalized goal panel.

<style>
  #bmi-tool *,#bmi-tool *::before,#bmi-tool *::after{box-sizing:border-box;margin:0;padding:0}
  #bmi-tool{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;max-width:680px;margin:2rem auto;color:#1f2937}
  .bmi-card{background:#fff;border:1px solid #e5e7eb;border-radius:12px;padding:1.75rem;margin-bottom:1.25rem;box-shadow:0 1px 3px rgba(0,0,0,.07)}
  .bmi-toggle-row{display:flex;gap:.5rem;margin-bottom:1.5rem}
  .bmi-toggle-btn{flex:1;padding:.6rem 1rem;border:2px solid #d1fae5;border-radius:8px;background:#f0fdf4;color:#065f46;font-size:.95rem;font-weight:600;cursor:pointer;transition:all .2s}
  .bmi-toggle-btn.active{background:#10b981;border-color:#10b981;color:#fff}
  .bmi-toggle-btn:hover:not(.active){background:#d1fae5}
  .bmi-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
  @media(max-width:500px){.bmi-grid{grid-template-columns:1fr}}
  .bmi-field{display:flex;flex-direction:column;gap:.35rem}
  .bmi-field label{font-size:.85rem;font-weight:600;color:#374151;text-transform:uppercase;letter-spacing:.04em}
  .bmi-field input[type=number]{width:100%;padding:.6rem .75rem;border:2px solid #e5e7eb;border-radius:8px;font-size:1rem;color:#111827;transition:border-color .2s;-moz-appearance:textfield}
  .bmi-field input[type=number]::-webkit-outer-spin-button,
  .bmi-field input[type=number]::-webkit-inner-spin-button{-webkit-appearance:none}
  .bmi-field input[type=number]:focus{outline:none;border-color:#10b981}
  .bmi-height-imperial{display:flex;gap:.5rem}
  .bmi-height-imperial input{flex:1}
  .bmi-height-imperial span{align-self:center;font-size:.85rem;color:#6b7280;white-space:nowrap}
  .bmi-gender-row{display:flex;gap:1rem;margin-top:.25rem}
  .bmi-gender-row label{display:flex;align-items:center;gap:.4rem;font-size:.95rem;font-weight:500;cursor:pointer;color:#374151}
  .bmi-gender-row input[type=radio]{accent-color:#10b981;width:1.1rem;height:1.1rem;cursor:pointer}
  .bmi-calc-btn{width:100%;margin-top:1.25rem;padding:.85rem;background:#10b981;color:#fff;border:none;border-radius:10px;font-size:1.05rem;font-weight:700;cursor:pointer;transition:background .2s,transform .1s;letter-spacing:.02em}
  .bmi-calc-btn:hover{background:#059669}
  .bmi-calc-btn:active{transform:scale(.98)}
  .bmi-result-hidden{display:none}
  .bmi-result-number-wrap{text-align:center;padding:1.5rem 1rem;border-radius:10px;margin-bottom:1.25rem;transition:background .4s}
  .bmi-result-number{font-size:4rem;font-weight:800;line-height:1;color:#fff}
  .bmi-result-label{font-size:1.1rem;font-weight:600;color:#fff;margin-top:.4rem;opacity:.92}
  .bmi-scale-wrap{margin-bottom:1.25rem}
  .bmi-scale-label{font-size:.8rem;font-weight:600;color:#6b7280;text-transform:uppercase;letter-spacing:.05em;margin-bottom:.5rem}
  .bmi-scale-track{position:relative;height:18px;border-radius:9px;background:linear-gradient(to right,#3b82f6 0%,#3b82f6 22.9%,#10b981 22.9%,#10b981 48.4%,#f59e0b 48.4%,#f59e0b 65.4%,#ef4444 65.4%,#ef4444 100%);overflow:visible}
  .bmi-scale-pointer{position:absolute;top:-6px;width:6px;height:30px;background:#1f2937;border-radius:3px;transform:translateX(-50%);transition:left .5s cubic-bezier(.4,0,.2,1)}
  .bmi-scale-ticks{display:flex;justify-content:space-between;margin-top:.35rem;padding:0 .1rem}
  .bmi-scale-ticks span{font-size:.72rem;color:#9ca3af}
  .bmi-info-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1.25rem}
  @media(max-width:480px){.bmi-info-grid{grid-template-columns:1fr}}
  .bmi-info-box{background:#f9fafb;border:1px solid #e5e7eb;border-radius:8px;padding:1rem}
  .bmi-info-box-title{font-size:.75rem;font-weight:700;color:#6b7280;text-transform:uppercase;letter-spacing:.05em;margin-bottom:.35rem}
  .bmi-info-box-value{font-size:1.05rem;font-weight:700;color:#111827}
  .bmi-goal-panel{border-radius:8px;padding:1rem 1.25rem;margin-bottom:1rem}
  .bmi-goal-panel.bmi-on-track{background:#d1fae5;border:1px solid #6ee7b7}
  .bmi-goal-panel.bmi-adjust{background:#fef3c7;border:1px solid #fcd34d}
  .bmi-goal-panel.bmi-adjust-red{background:#fee2e2;border:1px solid #fca5a5}
  .bmi-goal-title{font-size:.85rem;font-weight:700;text-transform:uppercase;letter-spacing:.04em;margin-bottom:.3rem}
  .bmi-goal-text{font-size:.95rem;font-weight:500;color:#1f2937}
  .bmi-chart-title{font-size:1rem;font-weight:700;color:#111827;margin-bottom:.75rem}
  .bmi-chart-table{width:100%;border-collapse:collapse;font-size:.9rem}
  .bmi-chart-table th{text-align:left;padding:.5rem .75rem;background:#f0fdf4;color:#065f46;font-weight:700;border-bottom:2px solid #a7f3d0}
  .bmi-chart-table td{padding:.5rem .75rem;border-bottom:1px solid #e5e7eb;color:#374151}
  .bmi-chart-table tr:last-child td{border-bottom:none}
  .bmi-chart-table tr.bmi-row-active td{font-weight:700;color:#111827}
</style>

<div id="bmi-tool">

  <!-- Unit Toggle -->
  <div class="bmi-card">
    <div class="bmi-toggle-row">
      <button class="bmi-toggle-btn active" id="btn-imperial" onclick="bmiSetUnit('imperial')">Imperial (lb / ft-in)</button>
      <button class="bmi-toggle-btn" id="btn-metric" onclick="bmiSetUnit('metric')">Metric (kg / cm)</button>
    </div>

    <!-- Imperial Inputs -->
    <div id="bmi-imperial-inputs">
      <div class="bmi-grid">
        <div class="bmi-field">
          <label>Height</label>
          <div class="bmi-height-imperial">
            <input type="number" id="imp-ft" placeholder="5" min="1" max="8" inputmode="decimal">
            <span>ft</span>
            <input type="number" id="imp-in" placeholder="7" min="0" max="11" inputmode="decimal">
            <span>in</span>
          </div>
        </div>
        <div class="bmi-field">
          <label>Weight (lbs)</label>
          <input type="number" id="imp-lbs" placeholder="154" min="1" max="1000" inputmode="decimal">
        </div>
        <div class="bmi-field">
          <label>Age (optional)</label>
          <input type="number" id="imp-age" placeholder="30" min="2" max="120" inputmode="decimal">
        </div>
        <div class="bmi-field">
          <label>Gender</label>
          <div class="bmi-gender-row">
            <label><input type="radio" name="bmi-gender-imp" value="male" checked> Male</label>
            <label><input type="radio" name="bmi-gender-imp" value="female"> Female</label>
          </div>
        </div>
      </div>
    </div>

    <!-- Metric Inputs -->
    <div id="bmi-metric-inputs" style="display:none">
      <div class="bmi-grid">
        <div class="bmi-field">
          <label>Height (cm)</label>
          <input type="number" id="met-cm" placeholder="170" min="50" max="300" inputmode="decimal">
        </div>
        <div class="bmi-field">
          <label>Weight (kg)</label>
          <input type="number" id="met-kg" placeholder="70" min="1" max="500" inputmode="decimal">
        </div>
        <div class="bmi-field">
          <label>Age (optional)</label>
          <input type="number" id="met-age" placeholder="30" min="2" max="120" inputmode="decimal">
        </div>
        <div class="bmi-field">
          <label>Gender</label>
          <div class="bmi-gender-row">
            <label><input type="radio" name="bmi-gender-met" value="male" checked> Male</label>
            <label><input type="radio" name="bmi-gender-met" value="female"> Female</label>
          </div>
        </div>
      </div>
    </div>

    <button class="bmi-calc-btn" onclick="bmiCalculate()">Calculate My BMI</button>
  </div>

  <!-- Results -->
  <div id="bmi-results" class="bmi-result-hidden">

    <!-- Big Number -->
    <div class="bmi-card" style="padding:0;overflow:hidden">
      <div id="bmi-number-wrap" class="bmi-result-number-wrap" style="margin:0;border-radius:0">
        <div id="bmi-number" class="bmi-result-number">--</div>
        <div id="bmi-cat-text" class="bmi-result-label">--</div>
      </div>

      <div style="padding:1.25rem">
        <!-- Scale Bar -->
        <div class="bmi-scale-wrap">
          <div class="bmi-scale-label">BMI Scale</div>
          <div class="bmi-scale-track">
            <div id="bmi-pointer" class="bmi-scale-pointer" style="left:0%"></div>
          </div>
          <div class="bmi-scale-ticks">
            <span>10</span>
            <span>18.5</span>
            <span>25</span>
            <span>30</span>
            <span>40+</span>
          </div>
        </div>

        <!-- Info Boxes -->
        <div class="bmi-info-grid">
          <div class="bmi-info-box">
            <div class="bmi-info-box-title">Your BMI</div>
            <div class="bmi-info-box-value" id="bmi-info-number">--</div>
          </div>
          <div class="bmi-info-box">
            <div class="bmi-info-box-title">Category</div>
            <div class="bmi-info-box-value" id="bmi-info-cat">--</div>
          </div>
          <div class="bmi-info-box">
            <div class="bmi-info-box-title">Healthy Weight Range</div>
            <div class="bmi-info-box-value" id="bmi-info-range">--</div>
          </div>
          <div class="bmi-info-box">
            <div class="bmi-info-box-title">Your Weight</div>
            <div class="bmi-info-box-value" id="bmi-info-weight">--</div>
          </div>
        </div>

        <!-- Goal Panel -->
        <div id="bmi-goal-panel" class="bmi-goal-panel bmi-on-track">
          <div class="bmi-goal-title" id="bmi-goal-title">Status</div>
          <div class="bmi-goal-text" id="bmi-goal-text"></div>
        </div>
      </div>
    </div>

    <!-- Chart Reference -->
    <div class="bmi-card">
      <div class="bmi-chart-title">BMI Category Reference Chart</div>
      <table class="bmi-chart-table">
        <thead>
          <tr><th>Category</th><th>BMI Range</th></tr>
        </thead>
        <tbody id="bmi-chart-body">
          <tr data-cat="underweight"><td>Underweight</td><td>&lt; 18.5</td></tr>
          <tr data-cat="normal"><td>Normal</td><td>18.5 – 24.9</td></tr>
          <tr data-cat="overweight"><td>Overweight</td><td>25.0 – 29.9</td></tr>
          <tr data-cat="obese1"><td>Obese Class I</td><td>30.0 – 34.9</td></tr>
          <tr data-cat="obese2"><td>Obese Class II</td><td>35.0 – 39.9</td></tr>
          <tr data-cat="obese3"><td>Obese Class III</td><td>&#8805; 40.0</td></tr>
        </tbody>
      </table>
    </div>

  </div><!-- /results -->

</div><!-- /bmi-tool -->

<script>
(function(){
  var _unit = 'imperial';

  window.bmiSetUnit = function(u){
    _unit = u;
    document.getElementById('bmi-imperial-inputs').style.display = u==='imperial'?'':'none';
    document.getElementById('bmi-metric-inputs').style.display  = u==='metric'?'':'none';
    document.getElementById('btn-imperial').classList.toggle('active', u==='imperial');
    document.getElementById('btn-metric').classList.toggle('active', u==='metric');
    document.getElementById('bmi-results').className = 'bmi-result-hidden';
  };

  window.bmiCalculate = function(){
    var heightM, weightKg, weightLbs, heightCm;

    if(_unit==='imperial'){
      var ft  = parseFloat(document.getElementById('imp-ft').value)  || 0;
      var ins = parseFloat(document.getElementById('imp-in').value)  || 0;
      var lbs = parseFloat(document.getElementById('imp-lbs').value) || 0;
      if(!ft && !ins){ alert('Please enter your height.'); return; }
      if(!lbs){ alert('Please enter your weight.'); return; }
      heightM   = (ft * 12 + ins) * 0.0254;
      weightKg  = lbs * 0.45359237;
      weightLbs = lbs;
      heightCm  = heightM * 100;
    } else {
      heightCm = parseFloat(document.getElementById('met-cm').value) || 0;
      weightKg = parseFloat(document.getElementById('met-kg').value) || 0;
      if(!heightCm){ alert('Please enter your height.'); return; }
      if(!weightKg){ alert('Please enter your weight.'); return; }
      heightM   = heightCm / 100;
      weightLbs = weightKg / 0.45359237;
    }

    if(heightM < 0.5 || heightM > 2.7){ alert('Please enter a valid height.'); return; }
    if(weightKg < 1 || weightKg > 500){ alert('Please enter a valid weight.'); return; }

    var bmi = weightKg / (heightM * heightM);
    bmi = Math.round(bmi * 10) / 10;

    // Category
    var cat, catKey, color;
    if(bmi < 18.5){
      cat='Underweight'; catKey='underweight'; color='#3b82f6';
    } else if(bmi < 25){
      cat='Normal Weight'; catKey='normal'; color='#10b981';
    } else if(bmi < 30){
      cat='Overweight'; catKey='overweight'; color='#f59e0b';
    } else if(bmi < 35){
      cat='Obese Class I'; catKey='obese1'; color='#ef4444';
    } else if(bmi < 40){
      cat='Obese Class II'; catKey='obese2'; color='#ef4444';
    } else {
      cat='Obese Class III'; catKey='obese3'; color='#ef4444';
    }

    // Healthy weight range for this height
    var minHealthyKg = 18.5 * heightM * heightM;
    var maxHealthyKg = 24.9 * heightM * heightM;
    var minHealthyLbs = minHealthyKg / 0.45359237;
    var maxHealthyLbs = maxHealthyKg / 0.45359237;

    var rangeStr, yourWeightStr;
    if(_unit==='imperial'){
      rangeStr     = round1(minHealthyLbs)+' – '+round1(maxHealthyLbs)+' lbs';
      yourWeightStr = round1(weightLbs)+' lbs';
    } else {
      rangeStr     = round1(minHealthyKg)+' – '+round1(maxHealthyKg)+' kg';
      yourWeightStr = round1(weightKg)+' kg';
    }

    // Scale pointer (range 10–45, clamped)
    var scaleMin=10, scaleMax=45;
    var pct = Math.min(100, Math.max(0, (bmi-scaleMin)/(scaleMax-scaleMin)*100));

    // Goal panel
    var goalTitle, goalText, goalClass;
    var diff, diffLbs;
    if(catKey==='normal'){
      goalClass='bmi-on-track';
      goalTitle='You are in the Normal range';
      goalText='Great work! Maintain your current lifestyle with balanced nutrition and regular activity.';
    } else if(catKey==='underweight'){
      var gainKg  = minHealthyKg - weightKg;
      var gainLbs = minHealthyLbs - weightLbs;
      goalClass='bmi-adjust';
      goalTitle='To reach Normal BMI';
      if(_unit==='imperial'){
        goalText='Consider gaining approximately '+round1(gainLbs)+' lbs to reach the lower end of the healthy range.';
      } else {
        goalText='Consider gaining approximately '+round1(gainKg)+' kg to reach the lower end of the healthy range.';
      }
    } else {
      var loseKg  = weightKg - maxHealthyKg;
      var loseLbs = weightLbs - maxHealthyLbs;
      goalClass='bmi-adjust-red';
      goalTitle='To reach Normal BMI';
      if(_unit==='imperial'){
        goalText='Consider losing approximately '+round1(loseLbs)+' lbs to reach the upper end of the healthy range.';
      } else {
        goalText='Consider losing approximately '+round1(loseKg)+' kg to reach the upper end of the healthy range.';
      }
    }

    // --- Render ---
    document.getElementById('bmi-results').className = '';

    document.getElementById('bmi-number-wrap').style.background = color;
    document.getElementById('bmi-number').textContent  = bmi.toFixed(1);
    document.getElementById('bmi-cat-text').textContent = cat;

    document.getElementById('bmi-info-number').textContent = bmi.toFixed(1);
    document.getElementById('bmi-info-cat').textContent    = cat;
    document.getElementById('bmi-info-range').textContent  = rangeStr;
    document.getElementById('bmi-info-weight').textContent = yourWeightStr;

    document.getElementById('bmi-pointer').style.left = pct+'%';

    var gp = document.getElementById('bmi-goal-panel');
    gp.className = 'bmi-goal-panel '+goalClass;
    document.getElementById('bmi-goal-title').textContent = goalTitle;
    document.getElementById('bmi-goal-text').textContent  = goalText;

    // Highlight chart row
    var rows = document.querySelectorAll('#bmi-chart-body tr');
    rows.forEach(function(r){
      r.classList.toggle('bmi-row-active', r.getAttribute('data-cat')===catKey);
    });

    // Scroll to results
    document.getElementById('bmi-results').scrollIntoView({behavior:'smooth', block:'start'});
  };

  function round1(n){ return Math.round(n*10)/10; }

  // Allow Enter key to trigger calculation
  document.addEventListener('keydown', function(e){
    if(e.key==='Enter' && document.activeElement &&
       document.activeElement.closest && document.activeElement.closest('#bmi-tool')){
      bmiCalculate();
    }
  });
})();
</script>

---

> **BMI is a screening tool, not a diagnostic measure.** It does not account for muscle mass, bone density, or fat distribution. Consult a qualified healthcare professional for personalized health and weight advice.

## Related Tools

- Create a monthly budget → [Budget Planner](/tools/budget-planner/)
- Calculate any percentage → [Percentage Calculator](/tools/percentage-calculator/)
