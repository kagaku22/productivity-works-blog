---
title: "Electricity Cost Calculator"
date: 2025-05-16
description: "Free online electricity cost calculator. Estimate your power consumption costs for any appliance — daily, monthly, and yearly with rate comparison."
categories: ["Free Tools"]
slug: "electricity-calculator"
ShowToc: false
cover:
  image: "/images/covers/electricity-calculator.png"
  alt: "Electricity Cost Calculator"
---

<div id="ec-app">
<style>
#ec-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #e2e8f0;
}

#ec-app * {
  box-sizing: border-box;
}

#ec-app h2 {
  font-size: 1.25rem;
  font-weight: 700;
  color: #f1f5f9;
  margin: 0 0 1rem 0;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #334155;
}

#ec-app h3 {
  font-size: 1rem;
  font-weight: 600;
  color: #cbd5e1;
  margin: 0 0 0.75rem 0;
}

/* Tabs */
#ec-app .ec-tabs {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

#ec-app .ec-tab {
  padding: 0.5rem 1.25rem;
  border-radius: 6px;
  border: 1px solid #334155;
  background: #1e293b;
  color: #94a3b8;
  cursor: pointer;
  font-size: 0.875rem;
  font-weight: 500;
  transition: all 0.15s ease;
}

#ec-app .ec-tab:hover {
  border-color: #475569;
  color: #cbd5e1;
}

#ec-app .ec-tab.active {
  background: #3b82f6;
  border-color: #3b82f6;
  color: #fff;
}

/* Panels */
#ec-app .ec-panel {
  display: none;
}

#ec-app .ec-panel.active {
  display: block;
}

/* Cards */
#ec-app .ec-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1.25rem;
}

/* Form grid */
#ec-app .ec-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 1rem;
}

#ec-app .ec-field {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

#ec-app .ec-field label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

#ec-app .ec-field input,
#ec-app .ec-field select {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 6px;
  color: #f1f5f9;
  padding: 0.55rem 0.75rem;
  font-size: 0.95rem;
  width: 100%;
  outline: none;
  transition: border-color 0.15s ease;
  -moz-appearance: textfield;
}

#ec-app .ec-field input::-webkit-inner-spin-button,
#ec-app .ec-field input::-webkit-outer-spin-button {
  opacity: 1;
}

#ec-app .ec-field input:focus,
#ec-app .ec-field select:focus {
  border-color: #3b82f6;
}

#ec-app .ec-field select option {
  background: #1e293b;
}

/* Buttons */
#ec-app .ec-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.55rem 1.1rem;
  border-radius: 6px;
  border: none;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s ease;
}

#ec-app .ec-btn-primary {
  background: #3b82f6;
  color: #fff;
}

#ec-app .ec-btn-primary:hover {
  background: #2563eb;
}

#ec-app .ec-btn-success {
  background: #10b981;
  color: #fff;
}

#ec-app .ec-btn-success:hover {
  background: #059669;
}

#ec-app .ec-btn-danger {
  background: transparent;
  border: 1px solid #ef4444;
  color: #ef4444;
  padding: 0.35rem 0.7rem;
  font-size: 0.8rem;
}

#ec-app .ec-btn-danger:hover {
  background: #ef4444;
  color: #fff;
}

#ec-app .ec-btn-ghost {
  background: transparent;
  border: 1px solid #334155;
  color: #94a3b8;
}

#ec-app .ec-btn-ghost:hover {
  border-color: #475569;
  color: #cbd5e1;
}

/* Results row */
#ec-app .ec-results {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1rem;
  margin-bottom: 1.25rem;
}

#ec-app .ec-result-card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

#ec-app .ec-result-card .label {
  font-size: 0.75rem;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.4rem;
}

#ec-app .ec-result-card .value {
  font-size: 1.5rem;
  font-weight: 700;
  color: #38bdf8;
  line-height: 1.2;
}

#ec-app .ec-result-card .sub {
  font-size: 0.75rem;
  color: #475569;
  margin-top: 0.25rem;
}

#ec-app .ec-result-card.highlight .value {
  color: #34d399;
}

/* Presets */
#ec-app .ec-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

#ec-app .ec-preset-btn {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 6px;
  color: #94a3b8;
  font-size: 0.8rem;
  padding: 0.35rem 0.75rem;
  cursor: pointer;
  transition: all 0.15s ease;
}

#ec-app .ec-preset-btn:hover {
  border-color: #3b82f6;
  color: #3b82f6;
}

/* Multi-appliance list */
#ec-app .ec-appliance-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-bottom: 1rem;
}

#ec-app .ec-appliance-row {
  display: grid;
  grid-template-columns: 1fr 90px 80px 80px auto;
  gap: 0.6rem;
  align-items: center;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 0.75rem;
}

@media (max-width: 600px) {
  #ec-app .ec-appliance-row {
    grid-template-columns: 1fr 1fr;
    row-gap: 0.5rem;
  }
  #ec-app .ec-appliance-row .ec-row-delete {
    grid-column: 1 / -1;
    justify-self: end;
  }
}

#ec-app .ec-appliance-row input {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 5px;
  color: #f1f5f9;
  padding: 0.4rem 0.6rem;
  font-size: 0.875rem;
  width: 100%;
  outline: none;
  -moz-appearance: textfield;
}

#ec-app .ec-appliance-row input:focus {
  border-color: #3b82f6;
}

#ec-app .ec-appliance-row .ec-row-label {
  font-size: 0.72rem;
  color: #64748b;
  display: block;
  margin-bottom: 2px;
}

/* Canvas chart */
#ec-app .ec-chart-wrap {
  position: relative;
  width: 100%;
  overflow-x: auto;
}

#ec-app #ec-chart {
  display: block;
  border-radius: 8px;
}

/* Tips */
#ec-app .ec-tips {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 0.75rem;
}

#ec-app .ec-tips li {
  background: #0f172a;
  border: 1px solid #334155;
  border-left: 3px solid #3b82f6;
  border-radius: 6px;
  padding: 0.75rem 1rem;
  font-size: 0.875rem;
  color: #cbd5e1;
  line-height: 1.5;
}

#ec-app .ec-tips li strong {
  color: #f1f5f9;
  display: block;
  margin-bottom: 0.2rem;
}

/* Total bar */
#ec-app .ec-total-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #0f172a;
  border: 1px solid #3b82f6;
  border-radius: 8px;
  padding: 0.75rem 1.25rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
  gap: 0.5rem;
}

#ec-app .ec-total-bar .tot-label {
  font-size: 0.875rem;
  font-weight: 600;
  color: #94a3b8;
}

#ec-app .ec-total-bar .tot-values {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
}

#ec-app .ec-total-bar .tot-item {
  text-align: center;
}

#ec-app .ec-total-bar .tot-item .tv {
  font-size: 1.1rem;
  font-weight: 700;
  color: #34d399;
}

#ec-app .ec-total-bar .tot-item .tl {
  font-size: 0.72rem;
  color: #475569;
}

/* Cross-links */
#ec-app .ec-crosslinks {
  margin-top: 2rem;
  border-top: 1px solid #1e293b;
  padding-top: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

#ec-app .ec-crosslinks a {
  color: #38bdf8;
  text-decoration: none;
  font-size: 0.875rem;
}

#ec-app .ec-crosslinks a:hover {
  text-decoration: underline;
  color: #7dd3fc;
}

#ec-app .ec-crosslinks span {
  color: #475569;
  margin-right: 0.25rem;
}

/* Divider */
#ec-app .ec-row-actions {
  display: flex;
  gap: 0.6rem;
  align-items: center;
  flex-wrap: wrap;
  margin-top: 0.75rem;
}

/* Reset notice */
#ec-app .ec-notice {
  font-size: 0.8rem;
  color: #64748b;
  margin-top: 0.5rem;
}
</style>

<!-- ====== APP MARKUP ====== -->
<div class="ec-tabs">
  <button class="ec-tab active" onclick="ecSwitchTab('single', this)">Single Appliance</button>
  <button class="ec-tab" onclick="ecSwitchTab('multi', this)">Multi-Appliance</button>
</div>

<!-- ========== SINGLE PANEL ========== -->
<div id="ec-panel-single" class="ec-panel active">
  <div class="ec-card">
    <h2>Single Appliance Calculator</h2>

    <h3>Quick Presets</h3>
    <div class="ec-presets">
      <button class="ec-preset-btn" onclick="ecApplyPreset(65,  'Laptop')">Laptop (65W)</button>
      <button class="ec-preset-btn" onclick="ecApplyPreset(300, 'Desktop PC')">Desktop (300W)</button>
      <button class="ec-preset-btn" onclick="ecApplyPreset(100, 'LED TV')">LED TV (100W)</button>
      <button class="ec-preset-btn" onclick="ecApplyPreset(150, 'Refrigerator')">Fridge (150W)</button>
      <button class="ec-preset-btn" onclick="ecApplyPreset(1500,'Air Conditioner')">AC (1500W)</button>
      <button class="ec-preset-btn" onclick="ecApplyPreset(500, 'Washer')">Washer (500W)</button>
      <button class="ec-preset-btn" onclick="ecApplyPreset(1000,'Microwave')">Microwave (1000W)</button>
    </div>

    <div class="ec-grid">
      <div class="ec-field">
        <label>Appliance Name</label>
        <input type="text" id="ec-name" value="My Appliance" />
      </div>
      <div class="ec-field">
        <label>Wattage (W)</label>
        <input type="number" id="ec-watts" value="65" min="1" oninput="ecCalcSingle()" />
      </div>
      <div class="ec-field">
        <label>Hours Used / Day</label>
        <input type="number" id="ec-hours" value="8" min="0" max="24" step="0.5" oninput="ecCalcSingle()" />
      </div>
      <div class="ec-field">
        <label>Electricity Rate ($/kWh)</label>
        <input type="number" id="ec-rate" value="0.13" min="0.01" step="0.01" oninput="ecCalcSingle()" />
      </div>
      <div class="ec-field">
        <label>Days / Month</label>
        <input type="number" id="ec-days" value="30" min="1" max="31" oninput="ecCalcSingle()" />
      </div>
    </div>
  </div>

  <!-- Results -->
  <div class="ec-results" id="ec-single-results">
    <div class="ec-result-card">
      <div class="label">Daily Cost</div>
      <div class="value" id="ec-r-daily">$0.00</div>
      <div class="sub" id="ec-r-daily-kwh">0.00 kWh/day</div>
    </div>
    <div class="ec-result-card">
      <div class="label">Monthly Cost</div>
      <div class="value" id="ec-r-monthly">$0.00</div>
      <div class="sub" id="ec-r-monthly-kwh">0.00 kWh/month</div>
    </div>
    <div class="ec-result-card highlight">
      <div class="label">Yearly Cost</div>
      <div class="value" id="ec-r-yearly">$0.00</div>
      <div class="sub" id="ec-r-yearly-kwh">0.00 kWh/year</div>
    </div>
  </div>

  <!-- Chart -->
  <div class="ec-card">
    <h2>Cost Comparison Chart</h2>
    <div class="ec-chart-wrap">
      <canvas id="ec-chart" height="220"></canvas>
    </div>
  </div>
</div>

<!-- ========== MULTI PANEL ========== -->
<div id="ec-panel-multi" class="ec-panel">
  <div class="ec-card">
    <h2>Multi-Appliance Calculator</h2>

    <h3>Quick Add Presets</h3>
    <div class="ec-presets">
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(65,  'Laptop')">+ Laptop (65W)</button>
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(300, 'Desktop PC')">+ Desktop (300W)</button>
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(100, 'LED TV')">+ LED TV (100W)</button>
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(150, 'Refrigerator')">+ Fridge (150W)</button>
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(1500,'Air Conditioner')">+ AC (1500W)</button>
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(500, 'Washer')">+ Washer (500W)</button>
      <button class="ec-preset-btn" onclick="ecMultiAddPreset(1000,'Microwave')">+ Microwave (1000W)</button>
    </div>

    <div class="ec-field" style="max-width:260px; margin-bottom:1rem;">
      <label>Electricity Rate ($/kWh)</label>
      <input type="number" id="ec-multi-rate" value="0.13" min="0.01" step="0.01" oninput="ecCalcMulti()" />
    </div>

    <div id="ec-appliance-list" class="ec-appliance-list"></div>

    <div class="ec-row-actions">
      <button class="ec-btn ec-btn-success" onclick="ecMultiAddRow()">+ Add Appliance</button>
      <span class="ec-notice">Each row: name, watts, hours/day, days/month</span>
    </div>
  </div>

  <!-- Multi totals -->
  <div class="ec-total-bar" id="ec-multi-total-bar">
    <span class="tot-label">Total (all appliances)</span>
    <div class="tot-values">
      <div class="tot-item"><div class="tv" id="ec-mt-daily">$0.00</div><div class="tl">Daily</div></div>
      <div class="tot-item"><div class="tv" id="ec-mt-monthly">$0.00</div><div class="tl">Monthly</div></div>
      <div class="tot-item"><div class="tv" id="ec-mt-yearly">$0.00</div><div class="tl">Yearly</div></div>
      <div class="tot-item"><div class="tv" id="ec-mt-kwh">0.00</div><div class="tl">kWh/mo</div></div>
    </div>
  </div>

  <!-- Multi chart -->
  <div class="ec-card">
    <h2>Appliance Cost Breakdown</h2>
    <div class="ec-chart-wrap">
      <canvas id="ec-multi-chart" height="260"></canvas>
    </div>
  </div>
</div>

<!-- ========== ENERGY TIPS ========== -->
<div class="ec-card" style="margin-top:1.25rem;">
  <h2>Energy Saving Tips</h2>
  <ul class="ec-tips">
    <li><strong>Unplug Standby Devices</strong>Idle electronics can draw 5–10% of your total electricity. Unplug chargers and TVs when not in use.</li>
    <li><strong>Switch to LED Bulbs</strong>LEDs use up to 80% less energy than incandescent bulbs and last 25x longer.</li>
    <li><strong>Optimize AC Usage</strong>Every 1°C increase in AC setpoint saves ~3% on cooling costs. Use ceiling fans to feel cooler.</li>
    <li><strong>Run Full Loads</strong>Washers and dishwashers use similar energy regardless of load size. Always run full loads.</li>
    <li><strong>Smart Power Strips</strong>Use smart strips to automatically cut power to peripherals when your main device turns off.</li>
    <li><strong>Off-Peak Hours</strong>Some utilities offer time-of-use rates. Shift heavy loads (laundry, dishwasher) to off-peak hours.</li>
  </ul>
</div>

<!-- ========== CROSS-LINKS ========== -->
<div class="ec-crosslinks">
  <div><span>&#8594;</span>Calculate ROI <a href="/tools/roi-calculator/">ROI Calculator</a></div>
  <div><span>&#8594;</span>Plan your budget <a href="/tools/budget-planner/">50/30/20 Budget Calculator</a></div>
  <div><span>&#8594;</span>Calculate loan payments <a href="/tools/loan-emi-calculator/">Loan EMI Calculator</a></div>
</div>

<!-- ====== JAVASCRIPT ====== -->
<script>
(function () {
  'use strict';

  /* ── Utility ── */
  function fmt(n) { return '$' + n.toFixed(2); }
  function fmtKwh(n) { return n.toFixed(2) + ' kWh'; }

  /* ══════════════════════════════════
     TAB SWITCHER
  ══════════════════════════════════ */
  window.ecSwitchTab = function (tab, btn) {
    document.querySelectorAll('#ec-app .ec-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('#ec-app .ec-tab').forEach(b => b.classList.remove('active'));
    document.getElementById('ec-panel-' + tab).classList.add('active');
    btn.classList.add('active');
    if (tab === 'multi') { ecCalcMulti(); ecDrawMultiChart(); }
    else { ecCalcSingle(); }
  };

  /* ══════════════════════════════════
     SINGLE CALCULATOR
  ══════════════════════════════════ */
  function val(id) { return parseFloat(document.getElementById(id).value) || 0; }

  window.ecApplyPreset = function (watts, name) {
    document.getElementById('ec-watts').value = watts;
    document.getElementById('ec-name').value  = name;
    ecCalcSingle();
  };

  window.ecCalcSingle = function () {
    var w     = val('ec-watts');
    var h     = val('ec-hours');
    var rate  = val('ec-rate');
    var days  = val('ec-days');

    var kwhDay   = (w * h) / 1000;
    var kwhMonth = kwhDay * days;
    var kwhYear  = kwhDay * 365;

    var costDay   = kwhDay   * rate;
    var costMonth = kwhMonth * rate;
    var costYear  = kwhYear  * rate;

    document.getElementById('ec-r-daily').textContent       = fmt(costDay);
    document.getElementById('ec-r-daily-kwh').textContent   = fmtKwh(kwhDay)   + '/day';
    document.getElementById('ec-r-monthly').textContent     = fmt(costMonth);
    document.getElementById('ec-r-monthly-kwh').textContent = fmtKwh(kwhMonth) + '/month';
    document.getElementById('ec-r-yearly').textContent      = fmt(costYear);
    document.getElementById('ec-r-yearly-kwh').textContent  = fmtKwh(kwhYear)  + '/year';

    ecDrawSingleChart(costDay, costMonth, costYear);
  };

  /* ── Single Chart ── */
  function ecDrawSingleChart(daily, monthly, yearly) {
    var canvas = document.getElementById('ec-chart');
    if (!canvas) return;
    var dpr = window.devicePixelRatio || 1;
    var W   = canvas.parentElement.clientWidth || 700;
    canvas.width  = W * dpr;
    canvas.height = 220 * dpr;
    canvas.style.width  = W + 'px';
    canvas.style.height = '220px';

    var ctx = canvas.getContext('2d');
    ctx.scale(dpr, dpr);
    ctx.clearRect(0, 0, W, 220);

    var labels = ['Daily', 'Monthly', 'Yearly'];
    var values = [daily, monthly, yearly];
    var colors = ['#38bdf8', '#818cf8', '#34d399'];
    var maxVal = Math.max.apply(null, values) || 1;

    var padL = 56, padR = 20, padT = 20, padB = 48;
    var chartW = W - padL - padR;
    var chartH = 220 - padT - padB;
    var barW   = Math.min(80, (chartW / labels.length) * 0.5);
    var gap    = chartW / labels.length;

    /* grid lines */
    ctx.strokeStyle = '#1e293b';
    ctx.lineWidth   = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = padT + chartH - (chartH * g / 4);
      ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(padL + chartW, gy); ctx.stroke();
      ctx.fillStyle   = '#475569';
      ctx.font        = '11px sans-serif';
      ctx.textAlign   = 'right';
      var gv = (maxVal * g / 4);
      ctx.fillText('$' + gv.toFixed(gv < 1 ? 2 : 0), padL - 4, gy + 4);
    }

    /* bars */
    labels.forEach(function (lbl, i) {
      var barH = (values[i] / maxVal) * chartH;
      var bx   = padL + gap * i + (gap - barW) / 2;
      var by   = padT + chartH - barH;

      /* bar */
      ctx.fillStyle = colors[i];
      ctx.beginPath();
      ctx.roundRect ? ctx.roundRect(bx, by, barW, barH, [4, 4, 0, 0])
                    : ctx.rect(bx, by, barW, barH);
      ctx.fill();

      /* value label on top */
      ctx.fillStyle   = '#f1f5f9';
      ctx.font        = 'bold 12px sans-serif';
      ctx.textAlign   = 'center';
      ctx.fillText('$' + values[i].toFixed(2), bx + barW / 2, by - 5);

      /* x-axis label */
      ctx.fillStyle = '#94a3b8';
      ctx.font      = '12px sans-serif';
      ctx.fillText(lbl, bx + barW / 2, padT + chartH + 20);
    });
  }

  /* ══════════════════════════════════
     MULTI-APPLIANCE CALCULATOR
  ══════════════════════════════════ */
  var ecRows = [];
  var ecRowId = 0;

  window.ecMultiAddPreset = function (watts, name) {
    ecMultiAddRow(name, watts);
  };

  window.ecMultiAddRow = function (name, watts) {
    var id = ++ecRowId;
    ecRows.push({ id: id, name: name || '', watts: watts || 100, hours: 8, days: 30 });
    ecRenderList();
    ecCalcMulti();
  };

  window.ecMultiRemoveRow = function (id) {
    ecRows = ecRows.filter(function (r) { return r.id !== id; });
    ecRenderList();
    ecCalcMulti();
  };

  function ecRenderList() {
    var list = document.getElementById('ec-appliance-list');
    list.innerHTML = '';

    if (ecRows.length === 0) {
      list.innerHTML = '<p style="color:#475569;font-size:0.875rem;">No appliances added yet. Use presets or click "+ Add Appliance".</p>';
      return;
    }

    ecRows.forEach(function (row) {
      var div = document.createElement('div');
      div.className = 'ec-appliance-row';
      div.innerHTML =
        '<div>' +
          '<span class="ec-row-label">Name</span>' +
          '<input type="text" value="' + ecEsc(row.name) + '" placeholder="Appliance name" oninput="ecMultiUpdate(' + row.id + ',\'name\',this.value)" />' +
        '</div>' +
        '<div>' +
          '<span class="ec-row-label">Watts (W)</span>' +
          '<input type="number" value="' + row.watts + '" min="1" oninput="ecMultiUpdate(' + row.id + ',\'watts\',this.value)" />' +
        '</div>' +
        '<div>' +
          '<span class="ec-row-label">Hours/Day</span>' +
          '<input type="number" value="' + row.hours + '" min="0" max="24" step="0.5" oninput="ecMultiUpdate(' + row.id + ',\'hours\',this.value)" />' +
        '</div>' +
        '<div>' +
          '<span class="ec-row-label">Days/Month</span>' +
          '<input type="number" value="' + row.days + '" min="1" max="31" oninput="ecMultiUpdate(' + row.id + ',\'days\',this.value)" />' +
        '</div>' +
        '<div class="ec-row-delete">' +
          '<button class="ec-btn ec-btn-danger" onclick="ecMultiRemoveRow(' + row.id + ')">Remove</button>' +
        '</div>';
      list.appendChild(div);
    });
  }

  window.ecMultiUpdate = function (id, field, value) {
    ecRows.forEach(function (r) {
      if (r.id === id) r[field] = (field === 'name') ? value : (parseFloat(value) || 0);
    });
    ecCalcMulti();
  };

  function ecEsc(str) {
    return String(str || '').replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  window.ecCalcMulti = function () {
    var rate = parseFloat(document.getElementById('ec-multi-rate').value) || 0.13;
    var totDaily = 0, totMonthly = 0, totYearly = 0, totKwh = 0;

    ecRows.forEach(function (r) {
      var kwhDay   = (r.watts * r.hours) / 1000;
      var kwhMonth = kwhDay * r.days;
      var kwhYear  = kwhDay * 365;
      totDaily   += kwhDay   * rate;
      totMonthly += kwhMonth * rate;
      totYearly  += kwhYear  * rate;
      totKwh     += kwhMonth;
    });

    document.getElementById('ec-mt-daily').textContent   = fmt(totDaily);
    document.getElementById('ec-mt-monthly').textContent = fmt(totMonthly);
    document.getElementById('ec-mt-yearly').textContent  = fmt(totYearly);
    document.getElementById('ec-mt-kwh').textContent     = totKwh.toFixed(2);

    ecDrawMultiChart(rate);
  };

  /* ── Multi Chart ── */
  window.ecDrawMultiChart = function (rate) {
    rate = rate || parseFloat(document.getElementById('ec-multi-rate').value) || 0.13;
    var canvas = document.getElementById('ec-multi-chart');
    if (!canvas) return;

    if (ecRows.length === 0) {
      var ctx0 = canvas.getContext('2d');
      canvas.width = 400; canvas.height = 260;
      ctx0.clearRect(0, 0, 400, 260);
      ctx0.fillStyle = '#475569';
      ctx0.font = '14px sans-serif';
      ctx0.textAlign = 'center';
      ctx0.fillText('Add appliances to see chart', 200, 130);
      return;
    }

    var dpr    = window.devicePixelRatio || 1;
    var W      = canvas.parentElement.clientWidth || 700;
    var H      = 260;
    canvas.width  = W * dpr;
    canvas.height = H * dpr;
    canvas.style.width  = W + 'px';
    canvas.style.height = H + 'px';

    var ctx = canvas.getContext('2d');
    ctx.scale(dpr, dpr);
    ctx.clearRect(0, 0, W, H);

    var palette = ['#38bdf8','#818cf8','#34d399','#fb923c','#f472b6','#facc15','#a78bfa','#4ade80'];
    var values  = ecRows.map(function (r) { return ((r.watts * r.hours) / 1000) * r.days * rate; });
    var labels  = ecRows.map(function (r) { return r.name || ('Item ' + r.id); });
    var maxVal  = Math.max.apply(null, values) || 1;

    var padL = 60, padR = 20, padT = 20, padB = 60;
    var chartW = W - padL - padR;
    var chartH = H - padT - padB;
    var n      = labels.length;
    var barW   = Math.min(60, (chartW / n) * 0.55);
    var gap    = chartW / n;

    /* grid */
    ctx.strokeStyle = '#1e293b';
    ctx.lineWidth   = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = padT + chartH - (chartH * g / 4);
      ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(padL + chartW, gy); ctx.stroke();
      ctx.fillStyle = '#475569'; ctx.font = '11px sans-serif'; ctx.textAlign = 'right';
      var gv = (maxVal * g / 4);
      ctx.fillText('$' + gv.toFixed(gv < 1 ? 2 : 0), padL - 4, gy + 4);
    }

    labels.forEach(function (lbl, i) {
      var barH = (values[i] / maxVal) * chartH;
      var bx   = padL + gap * i + (gap - barW) / 2;
      var by   = padT + chartH - barH;
      var col  = palette[i % palette.length];

      ctx.fillStyle = col;
      ctx.beginPath();
      ctx.roundRect ? ctx.roundRect(bx, by, barW, barH, [4, 4, 0, 0])
                    : ctx.rect(bx, by, barW, barH);
      ctx.fill();

      /* top label */
      ctx.fillStyle = '#f1f5f9'; ctx.font = 'bold 11px sans-serif'; ctx.textAlign = 'center';
      ctx.fillText('$' + values[i].toFixed(2), bx + barW / 2, Math.max(by - 4, padT + 12));

      /* x label — truncate if needed */
      var maxLblW = gap - 4;
      ctx.fillStyle = '#94a3b8'; ctx.font = '11px sans-serif';
      var short = lbl.length > 12 ? lbl.slice(0, 11) + '…' : lbl;
      ctx.fillText(short, bx + barW / 2, padT + chartH + 18);

      /* watts sub-label */
      ctx.fillStyle = '#475569'; ctx.font = '10px sans-serif';
      ctx.fillText(ecRows[i].watts + 'W', bx + barW / 2, padT + chartH + 32);
    });
  };

  /* ══════════════════════════════════
     INIT
  ══════════════════════════════════ */
  function init() {
    ecCalcSingle();
    /* seed multi with a couple of defaults */
    ecMultiAddRow('Laptop', 65);
    ecMultiAddRow('LED TV', 100);
    ecMultiAddRow('Refrigerator', 150);

    /* redraw charts on resize */
    var resizeTimer;
    window.addEventListener('resize', function () {
      clearTimeout(resizeTimer);
      resizeTimer = setTimeout(function () {
        ecCalcSingle();
        var multiPanel = document.getElementById('ec-panel-multi');
        if (multiPanel && multiPanel.classList.contains('active')) {
          ecDrawMultiChart();
        }
      }, 150);
    });
  }

  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', init);
  } else {
    init();
  }
})();
</script>
</div>
