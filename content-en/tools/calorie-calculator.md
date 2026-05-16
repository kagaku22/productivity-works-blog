---
title: "Calorie Calculator"
date: 2025-05-16
description: "Free online calorie calculator. Estimate your daily caloric needs based on age, weight, height, and activity level — with macro breakdown and weight goal planning."
categories: ["Free Tools"]
slug: "calorie-calculator"
ShowToc: false
cover:
  image: "/images/covers/calorie-calculator.png"
  alt: "Calorie Calculator"
---

Find out how many calories your body needs each day — then plan smarter with macro breakdowns and weight goal targets tailored to your lifestyle.

<div id="cc-app">
<style>
#cc-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 760px;
  margin: 0 auto;
  color: #1e293b;
  font-size: 15px;
  line-height: 1.6;
}
#cc-app * {
  box-sizing: border-box;
}
#cc-app h2 {
  font-size: 1.15rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid #e2e8f0;
}
#cc-app .cc-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1.25rem;
}
#cc-app .cc-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 540px) {
  #cc-app .cc-grid {
    grid-template-columns: 1fr;
  }
}
#cc-app .cc-field {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}
#cc-app .cc-field label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#cc-app input[type="number"],
#cc-app select {
  width: 100%;
  padding: 0.55rem 0.75rem;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  background: #fff;
  color: #1e293b;
  font-size: 0.95rem;
  font-family: inherit;
  transition: border-color 0.15s;
  -moz-appearance: textfield;
}
#cc-app input[type="number"]::-webkit-inner-spin-button,
#cc-app input[type="number"]::-webkit-outer-spin-button {
  opacity: 1;
}
#cc-app input[type="number"]:focus,
#cc-app select:focus {
  outline: none;
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#cc-app .cc-radio-group {
  display: flex;
  gap: 0.75rem;
}
#cc-app .cc-radio-btn {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
  padding: 0.5rem 0.75rem;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: 500;
  color: #475569;
  transition: all 0.15s;
  user-select: none;
}
#cc-app .cc-radio-btn input[type="radio"] {
  display: none;
}
#cc-app .cc-radio-btn.active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#cc-app .cc-toggle-row {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 0.5rem;
}
#cc-app .cc-toggle-label {
  font-size: 0.78rem;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#cc-app .cc-toggle {
  display: flex;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  overflow: hidden;
  background: #fff;
}
#cc-app .cc-toggle button {
  padding: 0.25rem 0.65rem;
  border: none;
  background: transparent;
  font-size: 0.78rem;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  transition: all 0.15s;
  font-family: inherit;
}
#cc-app .cc-toggle button.active {
  background: #6366f1;
  color: #fff;
}
#cc-app .cc-height-inputs {
  display: flex;
  gap: 0.5rem;
}
#cc-app .cc-height-inputs input {
  flex: 1;
}
#cc-app .cc-height-inputs .cc-unit-hint {
  display: flex;
  align-items: center;
  font-size: 0.8rem;
  color: #94a3b8;
  white-space: nowrap;
  padding: 0 0.2rem;
}
#cc-app .cc-formula-row {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}
#cc-app .cc-formula-btn {
  padding: 0.4rem 0.9rem;
  border: 1px solid #cbd5e1;
  border-radius: 20px;
  background: #fff;
  font-size: 0.8rem;
  font-weight: 600;
  color: #475569;
  cursor: pointer;
  transition: all 0.15s;
  font-family: inherit;
}
#cc-app .cc-formula-btn.active {
  background: #0f172a;
  border-color: #0f172a;
  color: #fff;
}
#cc-app .cc-btn-calc {
  width: 100%;
  padding: 0.75rem 1.5rem;
  background: linear-gradient(135deg, #6366f1, #4f46e5);
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  font-family: inherit;
  letter-spacing: 0.02em;
  transition: opacity 0.15s, transform 0.1s;
  box-shadow: 0 2px 8px rgba(99,102,241,0.3);
}
#cc-app .cc-btn-calc:hover {
  opacity: 0.93;
  transform: translateY(-1px);
}
#cc-app .cc-btn-calc:active {
  transform: translateY(0);
}
#cc-app .cc-results {
  display: none;
}
#cc-app .cc-results.visible {
  display: block;
}
#cc-app .cc-summary-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1.25rem;
}
@media (max-width: 480px) {
  #cc-app .cc-summary-grid {
    grid-template-columns: 1fr;
  }
}
#cc-app .cc-stat-box {
  border-radius: 10px;
  padding: 1rem 1.2rem;
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
}
#cc-app .cc-stat-box .cc-stat-label {
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  opacity: 0.75;
}
#cc-app .cc-stat-box .cc-stat-value {
  font-size: 1.8rem;
  font-weight: 800;
  line-height: 1.1;
}
#cc-app .cc-stat-box .cc-stat-sub {
  font-size: 0.78rem;
  opacity: 0.7;
}
#cc-app .cc-stat-bmr {
  background: #ede9fe;
  color: #4c1d95;
}
#cc-app .cc-stat-tdee {
  background: #dbeafe;
  color: #1e3a8a;
}
#cc-app .cc-goals-section h2 {
  margin-top: 0.25rem;
}
#cc-app .cc-goal-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#cc-app .cc-goal-table th {
  text-align: left;
  padding: 0.5rem 0.75rem;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: #64748b;
  background: #f1f5f9;
  border-bottom: 1px solid #e2e8f0;
}
#cc-app .cc-goal-table th:not(:first-child) {
  text-align: right;
}
#cc-app .cc-goal-table td {
  padding: 0.6rem 0.75rem;
  border-bottom: 1px solid #f1f5f9;
  color: #334155;
  vertical-align: middle;
}
#cc-app .cc-goal-table td:not(:first-child) {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
#cc-app .cc-goal-table tr:last-child td {
  border-bottom: none;
}
#cc-app .cc-badge {
  display: inline-block;
  padding: 0.15rem 0.55rem;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 700;
}
#cc-app .cc-badge-loss { background: #fef2f2; color: #991b1b; }
#cc-app .cc-badge-maintain { background: #f0fdf4; color: #166534; }
#cc-app .cc-badge-gain { background: #eff6ff; color: #1d4ed8; }
#cc-app .cc-macro-section {
  margin-top: 1.25rem;
}
#cc-app .cc-macro-layout {
  display: flex;
  gap: 1.5rem;
  align-items: center;
  flex-wrap: wrap;
}
#cc-app .cc-macro-chart-wrap {
  flex: 0 0 140px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
}
#cc-app .cc-macro-chart-wrap canvas {
  display: block;
}
#cc-app .cc-macro-chart-label {
  font-size: 0.75rem;
  color: #64748b;
  text-align: center;
}
#cc-app .cc-macro-details {
  flex: 1;
  min-width: 200px;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
#cc-app .cc-macro-row {
  display: flex;
  align-items: center;
  gap: 0.65rem;
}
#cc-app .cc-macro-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  flex-shrink: 0;
}
#cc-app .cc-macro-name {
  flex: 1;
  font-size: 0.88rem;
  font-weight: 600;
  color: #334155;
}
#cc-app .cc-macro-val {
  font-size: 0.88rem;
  font-weight: 700;
  color: #1e293b;
  font-variant-numeric: tabular-nums;
}
#cc-app .cc-macro-pct {
  font-size: 0.78rem;
  color: #94a3b8;
  width: 2.5rem;
  text-align: right;
}
#cc-app .cc-macro-goal-select {
  margin-bottom: 0.9rem;
  display: flex;
  align-items: center;
  gap: 0.65rem;
  flex-wrap: wrap;
}
#cc-app .cc-macro-goal-select label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#cc-app .cc-macro-goal-select select {
  padding: 0.35rem 0.65rem;
  font-size: 0.88rem;
  border-radius: 7px;
  width: auto;
}
#cc-app .cc-error {
  background: #fef2f2;
  border: 1px solid #fca5a5;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  color: #991b1b;
  font-size: 0.88rem;
  margin-bottom: 1rem;
  display: none;
}
#cc-app .cc-error.visible {
  display: block;
}
#cc-app .cc-crosslinks {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1.5rem;
  font-size: 0.88rem;
  color: #475569;
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
#cc-app .cc-crosslinks a {
  color: #6366f1;
  text-decoration: none;
  font-weight: 600;
}
#cc-app .cc-crosslinks a:hover {
  text-decoration: underline;
}
#cc-app .cc-divider {
  height: 1px;
  background: #e2e8f0;
  margin: 1.25rem 0;
}
#cc-app .cc-formula-note {
  font-size: 0.78rem;
  color: #94a3b8;
  margin-top: 0.5rem;
}
</style>

<!-- INPUTS -->
<div class="cc-card">
  <h2>Your Details</h2>
  <div class="cc-grid" style="margin-bottom:1rem;">
    <div class="cc-field">
      <label>Gender</label>
      <div class="cc-radio-group">
        <label class="cc-radio-btn active" id="cc-lbl-male">
          <input type="radio" name="cc-gender" value="male" checked> Male
        </label>
        <label class="cc-radio-btn" id="cc-lbl-female">
          <input type="radio" name="cc-gender" value="female"> Female
        </label>
      </div>
    </div>
    <div class="cc-field">
      <label>Age</label>
      <input type="number" id="cc-age" min="10" max="120" placeholder="e.g. 30">
    </div>
  </div>

  <div class="cc-grid" style="margin-bottom:1rem;">
    <div class="cc-field">
      <div class="cc-toggle-row">
        <span class="cc-toggle-label">Height</span>
        <div class="cc-toggle" id="cc-height-toggle">
          <button class="active" data-unit="cm" onclick="ccSetHeightUnit('cm')">cm</button>
          <button data-unit="ftin" onclick="ccSetHeightUnit('ftin')">ft/in</button>
        </div>
      </div>
      <div id="cc-height-cm-wrap" class="cc-height-inputs">
        <input type="number" id="cc-height-cm" min="50" max="280" placeholder="e.g. 170">
        <span class="cc-unit-hint">cm</span>
      </div>
      <div id="cc-height-ftin-wrap" class="cc-height-inputs" style="display:none;">
        <input type="number" id="cc-height-ft" min="1" max="9" placeholder="5">
        <span class="cc-unit-hint">ft</span>
        <input type="number" id="cc-height-in" min="0" max="11" placeholder="7">
        <span class="cc-unit-hint">in</span>
      </div>
    </div>
    <div class="cc-field">
      <div class="cc-toggle-row">
        <span class="cc-toggle-label">Weight</span>
        <div class="cc-toggle" id="cc-weight-toggle">
          <button class="active" data-unit="kg" onclick="ccSetWeightUnit('kg')">kg</button>
          <button data-unit="lbs" onclick="ccSetWeightUnit('lbs')">lbs</button>
        </div>
      </div>
      <div class="cc-height-inputs">
        <input type="number" id="cc-weight" min="1" max="1000" placeholder="e.g. 70">
        <span class="cc-unit-hint" id="cc-weight-hint">kg</span>
      </div>
    </div>
  </div>

  <div class="cc-field" style="margin-bottom:1rem;">
    <label>Activity Level</label>
    <select id="cc-activity">
      <option value="1.2">Sedentary (little or no exercise)</option>
      <option value="1.375">Lightly Active (1–3 days/week)</option>
      <option value="1.55" selected>Moderately Active (3–5 days/week)</option>
      <option value="1.725">Very Active (6–7 days/week)</option>
      <option value="1.9">Extra Active (hard exercise + physical job)</option>
    </select>
  </div>

  <div class="cc-field" style="margin-bottom:0.25rem;">
    <label>Formula</label>
    <div class="cc-formula-row">
      <button class="cc-formula-btn active" id="cc-formula-mifflin" onclick="ccSetFormula('mifflin')">Mifflin-St Jeor (recommended)</button>
      <button class="cc-formula-btn" id="cc-formula-harris" onclick="ccSetFormula('harris')">Harris-Benedict</button>
    </div>
    <p class="cc-formula-note">Mifflin-St Jeor is considered the most accurate for most adults.</p>
  </div>
</div>

<div class="cc-error" id="cc-error">Please fill in all fields with valid values.</div>

<button class="cc-btn-calc" onclick="ccCalculate()">Calculate My Calories</button>

<!-- RESULTS -->
<div class="cc-results" id="cc-results">
  <div class="cc-divider"></div>

  <div class="cc-summary-grid">
    <div class="cc-stat-box cc-stat-bmr">
      <span class="cc-stat-label">BMR — Basal Metabolic Rate</span>
      <span class="cc-stat-value" id="cc-out-bmr">—</span>
      <span class="cc-stat-sub">kcal/day at complete rest</span>
    </div>
    <div class="cc-stat-box cc-stat-tdee">
      <span class="cc-stat-label">TDEE — Daily Caloric Need</span>
      <span class="cc-stat-value" id="cc-out-tdee">—</span>
      <span class="cc-stat-sub">kcal/day to maintain weight</span>
    </div>
  </div>

  <!-- Goal table -->
  <div class="cc-card cc-goals-section">
    <h2>Calorie Targets by Goal</h2>
    <table class="cc-goal-table" id="cc-goal-table">
      <thead>
        <tr>
          <th>Goal</th>
          <th>Calories/day</th>
          <th>Weekly Change</th>
        </tr>
      </thead>
      <tbody id="cc-goal-tbody"></tbody>
    </table>
  </div>

  <!-- Macro breakdown -->
  <div class="cc-card cc-macro-section">
    <h2>Macro Breakdown</h2>
    <div class="cc-macro-goal-select">
      <label for="cc-macro-goal-sel">Show macros for:</label>
      <select id="cc-macro-goal-sel" onchange="ccUpdateMacros()"></select>
    </div>
    <div class="cc-macro-layout">
      <div class="cc-macro-chart-wrap">
        <canvas id="cc-donut" width="130" height="130"></canvas>
        <span class="cc-macro-chart-label">Macro Split</span>
      </div>
      <div class="cc-macro-details" id="cc-macro-details"></div>
    </div>
  </div>
</div>

<!-- Cross-links -->
<div class="cc-crosslinks">
  <span>Check your BMI &rarr; <a href="/tools/bmi-calculator/">BMI Calculator</a></span>
  <span>Plan your budget &rarr; <a href="/tools/budget-calculator/">50/30/20 Budget Calculator</a></span>
  <span>Track your investments &rarr; <a href="/tools/roi-calculator/">ROI Calculator</a></span>
</div>

<script>
(function () {
  "use strict";

  // State
  var ccState = {
    heightUnit: "cm",
    weightUnit: "kg",
    formula: "mifflin",
    bmr: 0,
    tdee: 0,
    goals: []
  };

  // Unit toggles
  window.ccSetHeightUnit = function (unit) {
    ccState.heightUnit = unit;
    var toggle = document.getElementById("cc-height-toggle");
    toggle.querySelectorAll("button").forEach(function (btn) {
      btn.classList.toggle("active", btn.dataset.unit === unit);
    });
    document.getElementById("cc-height-cm-wrap").style.display = unit === "cm" ? "" : "none";
    document.getElementById("cc-height-ftin-wrap").style.display = unit === "ftin" ? "" : "none";
  };

  window.ccSetWeightUnit = function (unit) {
    ccState.weightUnit = unit;
    var toggle = document.getElementById("cc-weight-toggle");
    toggle.querySelectorAll("button").forEach(function (btn) {
      btn.classList.toggle("active", btn.dataset.unit === unit);
    });
    document.getElementById("cc-weight-hint").textContent = unit;
  };

  window.ccSetFormula = function (formula) {
    ccState.formula = formula;
    document.getElementById("cc-formula-mifflin").classList.toggle("active", formula === "mifflin");
    document.getElementById("cc-formula-harris").classList.toggle("active", formula === "harris");
  };

  // Gender radio
  document.querySelectorAll("input[name='cc-gender']").forEach(function (radio) {
    radio.addEventListener("change", function () {
      document.getElementById("cc-lbl-male").classList.toggle("active", this.value === "male");
      document.getElementById("cc-lbl-female").classList.toggle("active", this.value === "female");
    });
  });

  // Get gender
  function getGender() {
    var radios = document.querySelectorAll("input[name='cc-gender']");
    for (var i = 0; i < radios.length; i++) {
      if (radios[i].checked) return radios[i].value;
    }
    return "male";
  }

  // Height → cm
  function getHeightCm() {
    if (ccState.heightUnit === "cm") {
      return parseFloat(document.getElementById("cc-height-cm").value);
    } else {
      var ft = parseFloat(document.getElementById("cc-height-ft").value) || 0;
      var inch = parseFloat(document.getElementById("cc-height-in").value) || 0;
      return (ft * 12 + inch) * 2.54;
    }
  }

  // Weight → kg
  function getWeightKg() {
    var w = parseFloat(document.getElementById("cc-weight").value);
    if (ccState.weightUnit === "lbs") return w * 0.453592;
    return w;
  }

  // Mifflin-St Jeor
  function calcMifflin(gender, weightKg, heightCm, age) {
    var base = 10 * weightKg + 6.25 * heightCm - 5 * age;
    return gender === "male" ? base + 5 : base - 161;
  }

  // Harris-Benedict
  function calcHarris(gender, weightKg, heightCm, age) {
    if (gender === "male") {
      return 88.362 + 13.397 * weightKg + 4.799 * heightCm - 5.677 * age;
    } else {
      return 447.593 + 9.247 * weightKg + 3.098 * heightCm - 4.330 * age;
    }
  }

  // Goals definition
  var GOALS = [
    { key: "loss-1kg",    label: "Lose 1 kg/week",    delta: -7700, badge: "loss" },
    { key: "loss-0.5kg",  label: "Lose 0.5 kg/week",  delta: -3850, badge: "loss" },
    { key: "loss-0.25kg", label: "Lose 0.25 kg/week", delta: -1925, badge: "loss" },
    { key: "maintain",    label: "Maintain Weight",    delta: 0,     badge: "maintain" },
    { key: "gain-0.25kg", label: "Gain 0.25 kg/week", delta: 1925,  badge: "gain" },
    { key: "gain-0.5kg",  label: "Gain 0.5 kg/week",  delta: 3850,  badge: "gain" }
  ];

  // Macro ratios per goal type (protein%, carb%, fat%)
  function getMacroRatios(badge) {
    if (badge === "loss")     return { p: 0.35, c: 0.40, f: 0.25 };
    if (badge === "gain")     return { p: 0.30, c: 0.45, f: 0.25 };
    return                           { p: 0.30, c: 0.40, f: 0.30 };
  }

  // Compute macros in grams (protein=4kcal/g, carb=4kcal/g, fat=9kcal/g)
  function computeMacros(kcal, badge) {
    var r = getMacroRatios(badge);
    return {
      protein: Math.round(kcal * r.p / 4),
      carbs:   Math.round(kcal * r.c / 4),
      fat:     Math.round(kcal * r.f / 9),
      pPct: Math.round(r.p * 100),
      cPct: Math.round(r.c * 100),
      fPct: Math.round(r.f * 100)
    };
  }

  function fmt(n) { return Math.round(n).toLocaleString(); }

  window.ccCalculate = function () {
    var errEl = document.getElementById("cc-error");
    errEl.classList.remove("visible");

    var gender = getGender();
    var age = parseFloat(document.getElementById("cc-age").value);
    var weightKg = getWeightKg();
    var heightCm = getHeightCm();
    var activity = parseFloat(document.getElementById("cc-activity").value);

    // Validation
    if (!age || age < 10 || age > 120 ||
        !weightKg || weightKg < 1 || weightKg > 500 ||
        !heightCm || heightCm < 50 || heightCm > 280) {
      errEl.classList.add("visible");
      return;
    }

    // BMR
    var bmr = ccState.formula === "harris"
      ? calcHarris(gender, weightKg, heightCm, age)
      : calcMifflin(gender, weightKg, heightCm, age);

    var tdee = bmr * activity;
    ccState.bmr = bmr;
    ccState.tdee = tdee;

    document.getElementById("cc-out-bmr").textContent = fmt(bmr) + " kcal";
    document.getElementById("cc-out-tdee").textContent = fmt(tdee) + " kcal";

    // Goal table
    var tbody = document.getElementById("cc-goal-tbody");
    tbody.innerHTML = "";
    ccState.goals = [];

    GOALS.forEach(function (g) {
      var dailyDelta = Math.round(g.delta / 7);
      var targetKcal = Math.max(1000, Math.round(tdee + dailyDelta));
      ccState.goals.push({ key: g.key, label: g.label, badge: g.badge, kcal: targetKcal });

      var tr = document.createElement("tr");
      var changeLabel = g.delta === 0 ? "—" :
        (g.delta > 0 ? "+" : "") + Math.round(dailyDelta) + " kcal/day";

      tr.innerHTML =
        '<td><span class="cc-badge cc-badge-' + g.badge + '">' + g.label + '</span></td>' +
        '<td><strong>' + fmt(targetKcal) + '</strong> kcal</td>' +
        '<td>' + changeLabel + '</td>';
      tbody.appendChild(tr);
    });

    // Populate macro goal selector
    var sel = document.getElementById("cc-macro-goal-sel");
    sel.innerHTML = "";
    ccState.goals.forEach(function (g) {
      var opt = document.createElement("option");
      opt.value = g.key;
      opt.textContent = g.label + " (" + fmt(g.kcal) + " kcal)";
      if (g.key === "maintain") opt.selected = true;
      sel.appendChild(opt);
    });

    ccUpdateMacros();

    var resultsEl = document.getElementById("cc-results");
    resultsEl.classList.add("visible");
    resultsEl.scrollIntoView({ behavior: "smooth", block: "start" });
  };

  window.ccUpdateMacros = function () {
    var sel = document.getElementById("cc-macro-goal-sel");
    var key = sel.value;
    var goal = ccState.goals.find(function (g) { return g.key === key; });
    if (!goal) return;

    var m = computeMacros(goal.kcal, goal.badge);
    var colors = { protein: "#6366f1", carbs: "#0ea5e9", fat: "#f59e0b" };

    var details = document.getElementById("cc-macro-details");
    details.innerHTML = [
      { name: "Protein", val: m.protein, pct: m.pPct, color: colors.protein },
      { name: "Carbs",   val: m.carbs,   pct: m.cPct, color: colors.carbs },
      { name: "Fat",     val: m.fat,     pct: m.fPct, color: colors.fat }
    ].map(function (row) {
      return '<div class="cc-macro-row">' +
        '<span class="cc-macro-dot" style="background:' + row.color + ';"></span>' +
        '<span class="cc-macro-name">' + row.name + '</span>' +
        '<span class="cc-macro-val">' + row.val + 'g</span>' +
        '<span class="cc-macro-pct">' + row.pct + '%</span>' +
        '</div>';
    }).join("");

    drawDonut([m.pPct, m.cPct, m.fPct], [colors.protein, colors.carbs, colors.fat]);
  };

  // Canvas donut chart
  function drawDonut(slices, colors) {
    var canvas = document.getElementById("cc-donut");
    var ctx = canvas.getContext("2d");
    var W = canvas.width, H = canvas.height;
    var cx = W / 2, cy = H / 2;
    var outer = Math.min(W, H) / 2 - 4;
    var inner = outer * 0.58;

    ctx.clearRect(0, 0, W, H);

    var total = slices.reduce(function (a, b) { return a + b; }, 0);
    var start = -Math.PI / 2;
    var gap = 0.025;

    slices.forEach(function (slice, i) {
      var angle = (slice / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, outer, start + gap / 2, start + angle - gap / 2);
      ctx.closePath();
      ctx.fillStyle = colors[i];
      ctx.fill();

      // Cutout
      ctx.beginPath();
      ctx.arc(cx, cy, inner, 0, 2 * Math.PI);
      ctx.fillStyle = "#fff";
      ctx.fill();

      start += angle;
    });

    // Center label
    ctx.fillStyle = "#1e293b";
    ctx.font = "bold 11px system-ui, sans-serif";
    ctx.textAlign = "center";
    ctx.textBaseline = "middle";
    ctx.fillText("Macros", cx, cy);
  }
})();
</script>
</div>
