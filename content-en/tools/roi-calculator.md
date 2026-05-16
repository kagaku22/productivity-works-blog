---
title: "ROI Calculator"
date: 2025-05-16
description: "Free online ROI calculator. Calculate return on investment, annualized ROI, and break-even point for any investment — with visual charts, no sign-up required."
categories: ["Free Tools"]
slug: "roi-calculator"
ShowToc: false
cover:
  image: "/images/covers/roi-calculator.png"
  alt: "ROI Calculator"
---

Enter your investment figures below to instantly calculate ROI, annualized return, NPV, IRR, and payback period — no account or sign-up needed.

<div id="roi-app">
<style>
#roi-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: #1e293b;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 0 2rem;
}
#roi-app *, #roi-app *::before, #roi-app *::after {
  box-sizing: border-box;
}

/* Tabs */
#roi-app .tab-bar {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #cbd5e1;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}
#roi-app .tab-btn {
  padding: 0.6rem 1.2rem;
  background: none;
  border: none;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  cursor: pointer;
  font-size: 0.95rem;
  font-weight: 600;
  color: #64748b;
  transition: color 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#roi-app .tab-btn:hover { color: #334155; }
#roi-app .tab-btn.active {
  color: #0f172a;
  border-bottom-color: #3b82f6;
}
#roi-app .tab-panel { display: none; }
#roi-app .tab-panel.active { display: block; }

/* Form grid */
#roi-app .form-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 560px) {
  #roi-app .form-grid { grid-template-columns: 1fr; }
}
#roi-app .field {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}
#roi-app .field.full { grid-column: 1 / -1; }
#roi-app label {
  font-size: 0.85rem;
  font-weight: 600;
  color: #475569;
}
#roi-app input[type="number"],
#roi-app select {
  padding: 0.5rem 0.75rem;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.95rem;
  color: #1e293b;
  background: #f8fafc;
  transition: border-color 0.15s;
  width: 100%;
}
#roi-app input[type="number"]:focus,
#roi-app select:focus {
  outline: none;
  border-color: #3b82f6;
  background: #fff;
}
#roi-app .radio-group {
  display: flex;
  gap: 1rem;
  align-items: center;
  flex-wrap: wrap;
}
#roi-app .radio-group label {
  font-weight: 400;
  display: flex;
  align-items: center;
  gap: 0.3rem;
  cursor: pointer;
  color: #334155;
}

/* Toggle gain/final value */
#roi-app .toggle-note {
  font-size: 0.8rem;
  color: #94a3b8;
  margin-top: 0.15rem;
}

/* Buttons */
#roi-app .btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.55rem 1.4rem;
  border-radius: 7px;
  border: none;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.08s;
}
#roi-app .btn:active { transform: scale(0.98); }
#roi-app .btn-primary {
  background: #3b82f6;
  color: #fff;
}
#roi-app .btn-primary:hover { background: #2563eb; }
#roi-app .btn-secondary {
  background: #e2e8f0;
  color: #334155;
}
#roi-app .btn-secondary:hover { background: #cbd5e1; }
#roi-app .btn-danger {
  background: #fee2e2;
  color: #b91c1c;
  padding: 0.35rem 0.75rem;
  font-size: 0.82rem;
}
#roi-app .btn-danger:hover { background: #fecaca; }
#roi-app .btn-small {
  background: #f1f5f9;
  color: #475569;
  padding: 0.35rem 0.9rem;
  font-size: 0.82rem;
  border: 1.5px solid #cbd5e1;
}
#roi-app .btn-small:hover { background: #e2e8f0; }
#roi-app .action-row {
  display: flex;
  gap: 0.75rem;
  align-items: center;
  margin-top: 1.25rem;
  flex-wrap: wrap;
}

/* Result cards */
#roi-app .result-area {
  margin-top: 1.5rem;
}
#roi-app .result-cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
  gap: 0.85rem;
  margin-bottom: 1.5rem;
}
#roi-app .card {
  border-radius: 10px;
  padding: 1rem 1.1rem;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}
#roi-app .card-neutral { background: #f1f5f9; border: 1.5px solid #e2e8f0; }
#roi-app .card-positive { background: #f0fdf4; border: 1.5px solid #86efac; }
#roi-app .card-negative { background: #fef2f2; border: 1.5px solid #fca5a5; }
#roi-app .card-info { background: #eff6ff; border: 1.5px solid #93c5fd; }
#roi-app .card-label {
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: #64748b;
}
#roi-app .card-value {
  font-size: 1.5rem;
  font-weight: 800;
  color: #0f172a;
  line-height: 1.1;
}
#roi-app .card-positive .card-value { color: #15803d; }
#roi-app .card-negative .card-value { color: #b91c1c; }
#roi-app .card-info .card-value { color: #1d4ed8; }
#roi-app .card-sub {
  font-size: 0.78rem;
  color: #94a3b8;
}

/* Break-even bar */
#roi-app .breakeven-bar-wrap {
  margin-bottom: 1.5rem;
}
#roi-app .breakeven-label {
  font-size: 0.82rem;
  font-weight: 600;
  color: #475569;
  margin-bottom: 0.4rem;
}
#roi-app .breakeven-track {
  position: relative;
  height: 22px;
  background: #e2e8f0;
  border-radius: 99px;
  overflow: hidden;
}
#roi-app .breakeven-fill {
  height: 100%;
  border-radius: 99px;
  transition: width 0.4s ease;
}
#roi-app .breakeven-fill-good { background: linear-gradient(90deg, #34d399, #10b981); }
#roi-app .breakeven-fill-bad  { background: linear-gradient(90deg, #f87171, #ef4444); }
#roi-app .breakeven-marker {
  font-size: 0.75rem;
  color: #475569;
  margin-top: 0.3rem;
}

/* Chart */
#roi-app .chart-wrap {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem;
  margin-bottom: 1.5rem;
}
#roi-app .chart-title {
  font-size: 0.82rem;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.75rem;
}
#roi-app canvas { display: block; width: 100%; }

/* Cost rows (Advanced) */
#roi-app .cost-rows { display: flex; flex-direction: column; gap: 0.5rem; }
#roi-app .cost-row {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}
#roi-app .cost-row input { flex: 1; }
#roi-app .cost-row input.cost-label-input { flex: 1.4; }

/* Comparison */
#roi-app .comp-investments {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 1rem;
}
#roi-app .comp-investment {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem;
}
#roi-app .comp-investment-title {
  font-size: 0.85rem;
  font-weight: 700;
  color: #475569;
  margin-bottom: 0.75rem;
}
#roi-app .comp-table-wrap { overflow-x: auto; }
#roi-app .comp-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#roi-app .comp-table th, #roi-app .comp-table td {
  padding: 0.55rem 0.85rem;
  border-bottom: 1px solid #e2e8f0;
  text-align: right;
}
#roi-app .comp-table th:first-child,
#roi-app .comp-table td:first-child { text-align: left; }
#roi-app .comp-table th {
  background: #f1f5f9;
  font-weight: 700;
  color: #475569;
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}
#roi-app .comp-table tr:last-child td { border-bottom: none; }
#roi-app .best-cell { color: #15803d; font-weight: 700; }

/* Section title */
#roi-app .section-title {
  font-size: 0.85rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #94a3b8;
  margin: 1.25rem 0 0.75rem;
}
#roi-app hr.divider {
  border: none;
  border-top: 1.5px solid #e2e8f0;
  margin: 1.5rem 0;
}

/* Cross-links */
#roi-app .crosslinks {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 2rem;
}
#roi-app .crosslinks p {
  margin: 0.3rem 0;
  font-size: 0.9rem;
  color: #475569;
}
#roi-app .crosslinks a { color: #2563eb; text-decoration: none; }
#roi-app .crosslinks a:hover { text-decoration: underline; }

/* Error */
#roi-app .error-msg {
  background: #fef2f2;
  border: 1.5px solid #fca5a5;
  border-radius: 7px;
  padding: 0.6rem 1rem;
  color: #b91c1c;
  font-size: 0.88rem;
  margin-top: 0.75rem;
}

/* Hidden */
#roi-app .hidden { display: none !important; }
</style>

<!-- TAB BAR -->
<div class="tab-bar">
  <button class="tab-btn active" onclick="roiShowTab('simple', this)">Simple ROI</button>
  <button class="tab-btn" onclick="roiShowTab('advanced', this)">Advanced ROI</button>
  <button class="tab-btn" onclick="roiShowTab('compare', this)">Comparison</button>
</div>

<!-- ===== TAB: SIMPLE ===== -->
<div id="roi-tab-simple" class="tab-panel active">
  <div class="form-grid">
    <div class="field">
      <label for="s-initial">Initial Investment ($)</label>
      <input type="number" id="s-initial" placeholder="10000" min="0" step="any">
    </div>
    <div class="field">
      <label>Value Type</label>
      <div class="radio-group" style="margin-top:0.4rem;">
        <label><input type="radio" name="s-type" value="final" checked onchange="roiSimpleTypeChange()"> Final Value ($)</label>
        <label><input type="radio" name="s-type" value="gain" onchange="roiSimpleTypeChange()"> Gain / Loss ($)</label>
      </div>
    </div>
    <div class="field" id="s-final-field">
      <label for="s-final">Final Value ($)</label>
      <input type="number" id="s-final" placeholder="13000" step="any">
      <span class="toggle-note">Total value at end of period</span>
    </div>
    <div class="field hidden" id="s-gain-field">
      <label for="s-gain">Gain / Loss ($)</label>
      <input type="number" id="s-gain" placeholder="3000" step="any">
      <span class="toggle-note">Positive = profit, negative = loss</span>
    </div>
    <div class="field">
      <label for="s-period">Investment Period</label>
      <input type="number" id="s-period" placeholder="3" min="0" step="any">
    </div>
    <div class="field">
      <label for="s-period-unit">Period Unit</label>
      <select id="s-period-unit">
        <option value="years">Years</option>
        <option value="months">Months</option>
      </select>
    </div>
  </div>
  <div class="action-row">
    <button class="btn btn-primary" onclick="roiCalcSimple()">Calculate</button>
    <button class="btn btn-secondary" onclick="roiResetSimple()">Reset</button>
  </div>
  <div id="s-error" class="error-msg hidden"></div>

  <div id="s-results" class="result-area hidden">
    <div class="section-title">Results</div>
    <div class="result-cards" id="s-cards"></div>
    <div class="breakeven-bar-wrap" id="s-breakeven-wrap">
      <div class="breakeven-label" id="s-breakeven-label">Break-even Progress</div>
      <div class="breakeven-track">
        <div class="breakeven-fill" id="s-breakeven-fill" style="width:0%"></div>
      </div>
      <div class="breakeven-marker" id="s-breakeven-marker"></div>
    </div>
    <div class="chart-wrap">
      <div class="chart-title">Investment vs. Returns</div>
      <canvas id="s-chart" height="220"></canvas>
    </div>
  </div>
</div>

<!-- ===== TAB: ADVANCED ===== -->
<div id="roi-tab-advanced" class="tab-panel">
  <div class="form-grid">
    <div class="field">
      <label for="a-initial">Initial Investment ($)</label>
      <input type="number" id="a-initial" placeholder="50000" min="0" step="any">
    </div>
    <div class="field">
      <label for="a-revenue">Annual Revenue ($)</label>
      <input type="number" id="a-revenue" placeholder="20000" min="0" step="any">
    </div>
    <div class="field">
      <label for="a-period">Investment Period (years)</label>
      <input type="number" id="a-period" placeholder="5" min="1" max="50" step="1">
    </div>
    <div class="field">
      <label for="a-discount">Discount Rate (% per year)</label>
      <input type="number" id="a-discount" placeholder="8" min="0" step="any">
    </div>
  </div>

  <div class="section-title" style="margin-top:1.25rem;">Annual Costs</div>
  <div class="cost-rows" id="a-cost-rows">
    <div class="cost-row">
      <input type="text" class="cost-label-input" placeholder="e.g. Operating costs" style="padding:0.5rem 0.75rem;border:1.5px solid #cbd5e1;border-radius:6px;font-size:0.95rem;background:#f8fafc;">
      <input type="number" class="cost-amount-input" placeholder="5000" min="0" step="any" style="padding:0.5rem 0.75rem;border:1.5px solid #cbd5e1;border-radius:6px;font-size:0.95rem;background:#f8fafc;flex:1;">
      <button class="btn btn-danger" onclick="roiRemoveCostRow(this)">Remove</button>
    </div>
  </div>
  <div style="margin-top:0.6rem;">
    <button class="btn btn-small" onclick="roiAddCostRow()">+ Add Cost</button>
  </div>

  <div class="action-row">
    <button class="btn btn-primary" onclick="roiCalcAdvanced()">Calculate</button>
    <button class="btn btn-secondary" onclick="roiResetAdvanced()">Reset</button>
  </div>
  <div id="a-error" class="error-msg hidden"></div>

  <div id="a-results" class="result-area hidden">
    <div class="section-title">Results</div>
    <div class="result-cards" id="a-cards"></div>
    <div class="breakeven-bar-wrap" id="a-breakeven-wrap">
      <div class="breakeven-label">Break-even Progress</div>
      <div class="breakeven-track">
        <div class="breakeven-fill" id="a-breakeven-fill" style="width:0%"></div>
      </div>
      <div class="breakeven-marker" id="a-breakeven-marker"></div>
    </div>
    <div class="chart-wrap">
      <div class="chart-title">Cumulative Cash Flow by Year</div>
      <canvas id="a-chart" height="260"></canvas>
    </div>
  </div>
</div>

<!-- ===== TAB: COMPARISON ===== -->
<div id="roi-tab-compare" class="tab-panel">
  <p style="font-size:0.9rem;color:#64748b;margin:0 0 1rem;">Enter 2–3 investments to compare side by side.</p>
  <div class="comp-investments" id="comp-investments">
    <!-- Investments injected by JS -->
  </div>
  <div style="display:flex;gap:0.75rem;flex-wrap:wrap;margin-bottom:1rem;">
    <button class="btn btn-small" id="comp-add-btn" onclick="roiCompAddInvestment()">+ Add Investment</button>
    <button class="btn btn-primary" onclick="roiCalcCompare()">Compare</button>
    <button class="btn btn-secondary" onclick="roiResetCompare()">Reset</button>
  </div>
  <div id="comp-error" class="error-msg hidden"></div>
  <div id="comp-results" class="result-area hidden">
    <div class="section-title">Comparison Table</div>
    <div class="comp-table-wrap">
      <table class="comp-table" id="comp-table"></table>
    </div>
    <div class="chart-wrap" style="margin-top:1.25rem;">
      <div class="chart-title">ROI % Comparison</div>
      <canvas id="comp-chart" height="220"></canvas>
    </div>
  </div>
</div>

<!-- CROSS-LINKS -->
<div class="crosslinks">
  <p>> Calculate compound interest &rarr; <a href="/tools/compound-interest-calculator/">Compound Interest Calculator</a></p>
  <p>> Plan your retirement &rarr; <a href="/tools/pension-simulator/">Pension Simulator</a></p>
  <p>> Manage your budget &rarr; <a href="/tools/budget-planner/">50/30/20 Budget Calculator</a></p>
</div>

<script>
(function() {
  /* ===== UTILS ===== */
  function fmt(n, dec) {
    if (!isFinite(n)) return "N/A";
    dec = dec === undefined ? 2 : dec;
    return n.toLocaleString(undefined, { minimumFractionDigits: dec, maximumFractionDigits: dec });
  }
  function fmtUSD(n) {
    if (!isFinite(n)) return "N/A";
    return "$" + fmt(n, 2);
  }
  function fmtPct(n) {
    if (!isFinite(n)) return "N/A";
    return fmt(n, 2) + "%";
  }
  function cardClass(val) {
    if (val > 0) return "card card-positive";
    if (val < 0) return "card card-negative";
    return "card card-neutral";
  }
  function makeCard(label, value, sub, cls) {
    return '<div class="' + (cls || "card card-neutral") + '">' +
      '<div class="card-label">' + label + '</div>' +
      '<div class="card-value">' + value + '</div>' +
      (sub ? '<div class="card-sub">' + sub + '</div>' : '') +
      '</div>';
  }

  /* ===== TAB SWITCHER ===== */
  window.roiShowTab = function(tab, btn) {
    document.querySelectorAll("#roi-app .tab-panel").forEach(function(p) { p.classList.remove("active"); });
    document.querySelectorAll("#roi-app .tab-btn").forEach(function(b) { b.classList.remove("active"); });
    document.getElementById("roi-tab-" + tab).classList.add("active");
    btn.classList.add("active");
  };

  /* ===== SIMPLE ROI ===== */
  window.roiSimpleTypeChange = function() {
    var type = document.querySelector('input[name="s-type"]:checked').value;
    document.getElementById("s-final-field").classList.toggle("hidden", type !== "final");
    document.getElementById("s-gain-field").classList.toggle("hidden", type !== "gain");
  };

  window.roiResetSimple = function() {
    ["s-initial","s-final","s-gain","s-period"].forEach(function(id) {
      document.getElementById(id).value = "";
    });
    document.getElementById("s-period-unit").value = "years";
    document.querySelector('input[name="s-type"][value="final"]').checked = true;
    roiSimpleTypeChange();
    document.getElementById("s-results").classList.add("hidden");
    document.getElementById("s-error").classList.add("hidden");
  };

  window.roiCalcSimple = function() {
    var errEl = document.getElementById("s-error");
    errEl.classList.add("hidden");

    var initial = parseFloat(document.getElementById("s-initial").value);
    var period  = parseFloat(document.getElementById("s-period").value);
    var unit    = document.getElementById("s-period-unit").value;
    var type    = document.querySelector('input[name="s-type"]:checked').value;

    if (isNaN(initial) || initial < 0) { roiErr(errEl, "Please enter a valid initial investment."); return; }
    if (isNaN(period) || period <= 0)  { roiErr(errEl, "Please enter a valid investment period."); return; }

    var gain, finalVal;
    if (type === "final") {
      finalVal = parseFloat(document.getElementById("s-final").value);
      if (isNaN(finalVal)) { roiErr(errEl, "Please enter a final value."); return; }
      gain = finalVal - initial;
    } else {
      gain = parseFloat(document.getElementById("s-gain").value);
      if (isNaN(gain)) { roiErr(errEl, "Please enter a gain or loss."); return; }
      finalVal = initial + gain;
    }

    var periodYears = unit === "months" ? period / 12 : period;
    var roi = initial === 0 ? NaN : (gain / initial) * 100;
    var annRoi = (initial <= 0 || !isFinite(roi)) ? NaN : (Math.pow(finalVal / initial, 1 / periodYears) - 1) * 100;

    // Cards
    var cards = "";
    cards += makeCard("ROI", fmtPct(roi), null, cardClass(roi) + " card");
    cards += makeCard("Annualized ROI", fmtPct(annRoi), "per year", (isFinite(annRoi) ? cardClass(annRoi) : "card card-neutral") + " card");
    cards += makeCard("Net Profit", fmtUSD(gain), null, cardClass(gain) + " card");
    cards += makeCard("Final Value", fmtUSD(finalVal), null, "card card-neutral");
    cards += makeCard("Period", fmt(period, 0) + " " + unit, null, "card card-neutral");
    document.getElementById("s-cards").innerHTML = cards;

    // Break-even
    var beEl = document.getElementById("s-breakeven-fill");
    var beMk = document.getElementById("s-breakeven-marker");
    if (initial > 0) {
      var pct = Math.min(100, Math.max(0, (finalVal / initial) * 100));
      beEl.style.width = pct + "%";
      beEl.className = "breakeven-fill " + (finalVal >= initial ? "breakeven-fill-good" : "breakeven-fill-bad");
      beMk.textContent = finalVal >= initial
        ? "Break-even reached — investment recovered"
        : "Break-even not yet reached (" + fmtPct(100 - pct) + " remaining)";
    }

    // Chart
    drawSimpleChart(initial, gain, period, unit);

    document.getElementById("s-results").classList.remove("hidden");
  };

  function drawSimpleChart(initial, gain, period, unit) {
    var canvas = document.getElementById("s-chart");
    var ctx = canvas.getContext("2d");
    var dpr = window.devicePixelRatio || 1;
    var W = canvas.parentElement.clientWidth - 32;
    var H = 220;
    canvas.width  = W * dpr;
    canvas.height = H * dpr;
    canvas.style.width  = W + "px";
    canvas.style.height = H + "px";
    ctx.scale(dpr, dpr);
    ctx.clearRect(0, 0, W, H);

    var totalYears = unit === "months" ? period / 12 : period;
    var steps = Math.max(2, Math.min(10, Math.ceil(totalYears)));
    var labels = [];
    var invVals = [];
    var retVals = [];
    for (var i = 1; i <= steps; i++) {
      var frac = i / steps;
      labels.push((unit === "months" ? fmt(period * frac, 0) + "mo" : fmt(totalYears * frac, 1) + "yr"));
      invVals.push(initial);
      retVals.push(initial + gain * frac);
    }
    drawBarChart(ctx, W, H, labels, [
      { label: "Initial Investment", values: invVals, color: "#94a3b8" },
      { label: "Portfolio Value",    values: retVals, color: gain >= 0 ? "#34d399" : "#f87171" }
    ]);
  }

  /* ===== ADVANCED ROI ===== */
  window.roiAddCostRow = function() {
    var row = document.createElement("div");
    row.className = "cost-row";
    row.innerHTML =
      '<input type="text" class="cost-label-input" placeholder="Cost description" style="padding:0.5rem 0.75rem;border:1.5px solid #cbd5e1;border-radius:6px;font-size:0.95rem;background:#f8fafc;flex:1.4;">' +
      '<input type="number" class="cost-amount-input" placeholder="0" min="0" step="any" style="padding:0.5rem 0.75rem;border:1.5px solid #cbd5e1;border-radius:6px;font-size:0.95rem;background:#f8fafc;flex:1;">' +
      '<button class="btn btn-danger" onclick="roiRemoveCostRow(this)">Remove</button>';
    document.getElementById("a-cost-rows").appendChild(row);
  };

  window.roiRemoveCostRow = function(btn) {
    var rows = document.querySelectorAll("#a-cost-rows .cost-row");
    if (rows.length > 1) btn.parentElement.remove();
  };

  window.roiResetAdvanced = function() {
    ["a-initial","a-revenue","a-period","a-discount"].forEach(function(id) {
      document.getElementById(id).value = "";
    });
    var container = document.getElementById("a-cost-rows");
    container.innerHTML =
      '<div class="cost-row">' +
      '<input type="text" class="cost-label-input" placeholder="e.g. Operating costs" style="padding:0.5rem 0.75rem;border:1.5px solid #cbd5e1;border-radius:6px;font-size:0.95rem;background:#f8fafc;">' +
      '<input type="number" class="cost-amount-input" placeholder="5000" min="0" step="any" style="padding:0.5rem 0.75rem;border:1.5px solid #cbd5e1;border-radius:6px;font-size:0.95rem;background:#f8fafc;flex:1;">' +
      '<button class="btn btn-danger" onclick="roiRemoveCostRow(this)">Remove</button>' +
      '</div>';
    document.getElementById("a-results").classList.add("hidden");
    document.getElementById("a-error").classList.add("hidden");
  };

  function calcIRR(cashflows) {
    // Iterative Newton-Raphson
    var rate = 0.1;
    for (var iter = 0; iter < 200; iter++) {
      var f = 0, df = 0;
      for (var t = 0; t < cashflows.length; t++) {
        var denom = Math.pow(1 + rate, t);
        f  += cashflows[t] / denom;
        df -= t * cashflows[t] / (denom * (1 + rate));
      }
      if (Math.abs(df) < 1e-12) break;
      var newRate = rate - f / df;
      if (Math.abs(newRate - rate) < 1e-9) { rate = newRate; break; }
      rate = newRate;
      if (rate < -0.999) rate = -0.999;
    }
    return isFinite(rate) ? rate * 100 : NaN;
  }

  window.roiCalcAdvanced = function() {
    var errEl = document.getElementById("a-error");
    errEl.classList.add("hidden");

    var initial  = parseFloat(document.getElementById("a-initial").value);
    var revenue  = parseFloat(document.getElementById("a-revenue").value);
    var period   = parseInt(document.getElementById("a-period").value, 10);
    var discount = parseFloat(document.getElementById("a-discount").value) / 100;

    if (isNaN(initial) || initial < 0)  { roiErr(errEl, "Please enter a valid initial investment."); return; }
    if (isNaN(revenue) || revenue < 0)  { roiErr(errEl, "Please enter a valid annual revenue."); return; }
    if (isNaN(period) || period < 1)    { roiErr(errEl, "Please enter a valid period (min 1 year)."); return; }
    if (isNaN(discount) || discount < 0){ roiErr(errEl, "Please enter a valid discount rate."); return; }

    // Total annual costs
    var totalCost = 0;
    document.querySelectorAll("#a-cost-rows .cost-amount-input").forEach(function(inp) {
      var v = parseFloat(inp.value);
      if (!isNaN(v) && v >= 0) totalCost += v;
    });

    var annualNet = revenue - totalCost;
    var totalNet  = annualNet * period;
    var roi       = initial === 0 ? NaN : (totalNet / initial) * 100;

    // NPV
    var npv = -initial;
    for (var t = 1; t <= period; t++) {
      npv += annualNet / Math.pow(1 + discount, t);
    }

    // IRR: cashflows[0] = -initial, [1..n] = annualNet
    var cfs = [-initial];
    for (var i = 0; i < period; i++) cfs.push(annualNet);
    var irr = calcIRR(cfs);

    // Payback
    var payback = NaN;
    if (annualNet > 0) payback = initial / annualNet;

    // Cumulative cash flow per year
    var cumCF = [];
    var running = -initial;
    for (var y = 1; y <= period; y++) {
      running += annualNet;
      cumCF.push(running);
    }

    // Cards
    var cards = "";
    cards += makeCard("Total ROI", fmtPct(roi), "over " + period + " yrs", cardClass(roi) + " card");
    cards += makeCard("NPV", fmtUSD(npv), "at " + fmt(discount*100,1) + "% discount", (isFinite(npv) ? cardClass(npv) : "card card-neutral") + " card");
    cards += makeCard("IRR", fmtPct(irr), "internal rate of return", "card card-info");
    cards += makeCard("Payback Period", isFinite(payback) ? fmt(payback, 1) + " yrs" : "N/A", null, isFinite(payback) && payback <= period ? "card card-positive" : "card card-negative");
    cards += makeCard("Annual Net", fmtUSD(annualNet), "revenue − costs", cardClass(annualNet) + " card");
    cards += makeCard("Total Net", fmtUSD(totalNet), period + " yrs total", cardClass(totalNet) + " card");
    document.getElementById("a-cards").innerHTML = cards;

    // Break-even bar
    var beEl = document.getElementById("a-breakeven-fill");
    var beMk = document.getElementById("a-breakeven-marker");
    if (isFinite(payback) && period > 0) {
      var bePct = Math.min(100, (payback / period) * 100);
      beEl.style.width = bePct + "%";
      beEl.className = "breakeven-fill " + (payback <= period ? "breakeven-fill-good" : "breakeven-fill-bad");
      beMk.textContent = payback <= period
        ? "Break-even at " + fmt(payback, 1) + " years (within the " + period + "-year period)"
        : "Break-even at " + fmt(payback, 1) + " years (exceeds period)";
    } else {
      beEl.style.width = "0%";
      beMk.textContent = annualNet <= 0 ? "No break-even: annual net is non-positive" : "";
    }

    // Chart
    drawAdvancedChart(initial, period, cumCF);

    document.getElementById("a-results").classList.remove("hidden");
  };

  function drawAdvancedChart(initial, period, cumCF) {
    var canvas = document.getElementById("a-chart");
    var ctx = canvas.getContext("2d");
    var dpr = window.devicePixelRatio || 1;
    var W = canvas.parentElement.clientWidth - 32;
    var H = 260;
    canvas.width  = W * dpr;
    canvas.height = H * dpr;
    canvas.style.width  = W + "px";
    canvas.style.height = H + "px";
    ctx.scale(dpr, dpr);
    ctx.clearRect(0, 0, W, H);

    // Draw line chart of cumulative CF
    var labels = [];
    for (var y = 1; y <= period; y++) labels.push("Yr " + y);

    var allVals = [-initial].concat(cumCF);
    var minV = Math.min.apply(null, allVals);
    var maxV = Math.max.apply(null, allVals);
    var pad = 40;
    var chartH = H - pad - 20;
    var chartW = W - pad - 16;
    var range = maxV - minV || 1;

    function xPos(i) { return pad + (i / (cumCF.length - 1 || 1)) * chartW; }
    function yPos(v) { return pad + (1 - (v - minV) / range) * chartH; }

    // Zero line
    var zeroY = yPos(0);
    ctx.strokeStyle = "#cbd5e1";
    ctx.lineWidth = 1;
    ctx.setLineDash([4, 3]);
    ctx.beginPath();
    ctx.moveTo(pad, zeroY);
    ctx.lineTo(pad + chartW, zeroY);
    ctx.stroke();
    ctx.setLineDash([]);

    // Line
    ctx.beginPath();
    for (var i = 0; i < cumCF.length; i++) {
      var x = xPos(i);
      var y = yPos(cumCF[i]);
      if (i === 0) ctx.moveTo(x, y); else ctx.lineTo(x, y);
    }
    ctx.strokeStyle = "#3b82f6";
    ctx.lineWidth = 2.5;
    ctx.stroke();

    // Points
    for (var j = 0; j < cumCF.length; j++) {
      var px = xPos(j), py = yPos(cumCF[j]);
      ctx.beginPath();
      ctx.arc(px, py, 4, 0, Math.PI * 2);
      ctx.fillStyle = cumCF[j] >= 0 ? "#34d399" : "#f87171";
      ctx.fill();
      ctx.strokeStyle = "#fff";
      ctx.lineWidth = 1.5;
      ctx.stroke();
    }

    // X labels
    ctx.fillStyle = "#64748b";
    ctx.font = "11px system-ui";
    ctx.textAlign = "center";
    for (var k = 0; k < labels.length; k++) {
      ctx.fillText(labels[k], xPos(k), H - 6);
    }

    // Y axis min/max
    ctx.textAlign = "right";
    ctx.fillText("$" + fmt(maxV, 0), pad - 4, pad + 4);
    ctx.fillText("$" + fmt(minV, 0), pad - 4, pad + chartH + 4);
    ctx.fillText("$0", pad - 4, zeroY + 4);
  }

  /* ===== COMPARISON ===== */
  var compCount = 2;

  function buildCompInvestmentHtml(n) {
    return '<div class="comp-investment" id="comp-inv-' + n + '">' +
      '<div class="comp-investment-title">Investment ' + n + '</div>' +
      '<div class="form-grid" style="grid-template-columns:1fr 1fr 1fr;">' +
        '<div class="field"><label>Initial ($)</label><input type="number" class="comp-initial" placeholder="10000" min="0" step="any"></div>' +
        '<div class="field"><label>Final Value ($)</label><input type="number" class="comp-final" placeholder="13000" step="any"></div>' +
        '<div class="field"><label>Period (years)</label><input type="number" class="comp-period" placeholder="3" min="0" step="any"></div>' +
      '</div>' +
    '</div>';
  }

  function initCompare() {
    var container = document.getElementById("comp-investments");
    container.innerHTML = "";
    for (var i = 1; i <= 2; i++) {
      container.insertAdjacentHTML("beforeend", buildCompInvestmentHtml(i));
    }
    compCount = 2;
    document.getElementById("comp-add-btn").style.display = "";
  }
  initCompare();

  window.roiCompAddInvestment = function() {
    if (compCount >= 3) return;
    compCount++;
    document.getElementById("comp-investments").insertAdjacentHTML("beforeend", buildCompInvestmentHtml(compCount));
    if (compCount >= 3) document.getElementById("comp-add-btn").style.display = "none";
  };

  window.roiResetCompare = function() {
    initCompare();
    document.getElementById("comp-results").classList.add("hidden");
    document.getElementById("comp-error").classList.add("hidden");
    document.getElementById("comp-add-btn").style.display = "";
  };

  window.roiCalcCompare = function() {
    var errEl = document.getElementById("comp-error");
    errEl.classList.add("hidden");

    var investments = [];
    var invEls = document.querySelectorAll("#comp-investments .comp-investment");
    for (var i = 0; i < invEls.length; i++) {
      var initial = parseFloat(invEls[i].querySelector(".comp-initial").value);
      var final_  = parseFloat(invEls[i].querySelector(".comp-final").value);
      var period  = parseFloat(invEls[i].querySelector(".comp-period").value);
      if (isNaN(initial) || isNaN(final_) || isNaN(period) || initial < 0 || period <= 0) {
        roiErr(errEl, "Please fill in all fields for Investment " + (i + 1) + ".");
        return;
      }
      var gain = final_ - initial;
      var roi  = initial === 0 ? NaN : (gain / initial) * 100;
      var annR = (initial <= 0 || !isFinite(roi)) ? NaN : (Math.pow(final_ / initial, 1 / period) - 1) * 100;
      investments.push({ n: i + 1, initial: initial, final: final_, period: period, gain: gain, roi: roi, annRoi: annR });
    }

    // Find best ROI
    var bestRoi = -Infinity, bestIdx = 0;
    investments.forEach(function(inv, idx) { if (isFinite(inv.roi) && inv.roi > bestRoi) { bestRoi = inv.roi; bestIdx = idx; } });

    // Build table
    var metrics = [
      { key: "initial",  label: "Initial Investment", fmt: fmtUSD,  higherBetter: false },
      { key: "final",    label: "Final Value",         fmt: fmtUSD,  higherBetter: true  },
      { key: "gain",     label: "Net Profit",          fmt: fmtUSD,  higherBetter: true  },
      { key: "roi",      label: "ROI %",               fmt: fmtPct,  higherBetter: true  },
      { key: "annRoi",   label: "Annualized ROI %",    fmt: fmtPct,  higherBetter: true  },
      { key: "period",   label: "Period (yrs)",        fmt: function(v){ return fmt(v,1)+"yr"; }, higherBetter: false }
    ];

    var thead = "<thead><tr><th>Metric</th>";
    investments.forEach(function(inv) { thead += "<th>Investment " + inv.n + "</th>"; });
    thead += "</tr></thead>";

    var tbody = "<tbody>";
    metrics.forEach(function(m) {
      tbody += "<tr><td>" + m.label + "</td>";
      var vals = investments.map(function(inv) { return inv[m.key]; });
      var best = m.higherBetter
        ? Math.max.apply(null, vals.filter(isFinite))
        : Math.min.apply(null, vals.filter(isFinite));
      investments.forEach(function(inv) {
        var v = inv[m.key];
        var isBest = isFinite(v) && v === best && vals.filter(function(x){ return x === best; }).length < vals.length;
        tbody += '<td class="' + (isBest ? "best-cell" : "") + '">' + m.fmt(v) + (isBest ? " ★" : "") + '</td>';
      });
      tbody += "</tr>";
    });
    tbody += "</tbody>";

    document.getElementById("comp-table").innerHTML = thead + tbody;

    // Chart
    drawCompChart(investments);

    document.getElementById("comp-results").classList.remove("hidden");
  };

  function drawCompChart(investments) {
    var canvas = document.getElementById("comp-chart");
    var ctx = canvas.getContext("2d");
    var dpr = window.devicePixelRatio || 1;
    var W = canvas.parentElement.clientWidth - 32;
    var H = 220;
    canvas.width  = W * dpr;
    canvas.height = H * dpr;
    canvas.style.width  = W + "px";
    canvas.style.height = H + "px";
    ctx.scale(dpr, dpr);
    ctx.clearRect(0, 0, W, H);

    var labels  = investments.map(function(inv) { return "Inv " + inv.n; });
    var rois    = investments.map(function(inv) { return isFinite(inv.roi) ? inv.roi : 0; });
    var annRois = investments.map(function(inv) { return isFinite(inv.annRoi) ? inv.annRoi : 0; });

    drawBarChart(ctx, W, H, labels, [
      { label: "ROI %",          values: rois,    color: "#3b82f6" },
      { label: "Annualized ROI%",values: annRois, color: "#34d399" }
    ]);
  }

  /* ===== SHARED BAR CHART ===== */
  function drawBarChart(ctx, W, H, labels, datasets) {
    var padL = 52, padR = 12, padT = 20, padB = 36;
    var chartW = W - padL - padR;
    var chartH = H - padT - padB;
    var n = labels.length;
    var m = datasets.length;
    var allVals = [];
    datasets.forEach(function(ds) { ds.values.forEach(function(v) { allVals.push(v); }); });
    allVals.push(0);
    var maxV = Math.max.apply(null, allVals);
    var minV = Math.min.apply(null, allVals);
    var range = maxV - minV || 1;

    function yPos(v) { return padT + (1 - (v - minV) / range) * chartH; }
    var zeroY = yPos(0);

    // Grid
    var gridLines = 5;
    ctx.strokeStyle = "#e2e8f0";
    ctx.lineWidth = 1;
    ctx.setLineDash([3, 3]);
    for (var g = 0; g <= gridLines; g++) {
      var gy = padT + (g / gridLines) * chartH;
      ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(padL + chartW, gy); ctx.stroke();
    }
    ctx.setLineDash([]);

    // Zero line
    if (minV < 0) {
      ctx.strokeStyle = "#94a3b8";
      ctx.lineWidth = 1.5;
      ctx.beginPath(); ctx.moveTo(padL, zeroY); ctx.lineTo(padL + chartW, zeroY); ctx.stroke();
    }

    // Bars
    var groupW = chartW / n;
    var barPad = groupW * 0.15;
    var barW   = (groupW - barPad * 2) / m;

    datasets.forEach(function(ds, di) {
      ctx.fillStyle = ds.color;
      for (var i = 0; i < n; i++) {
        var v = ds.values[i];
        var x = padL + i * groupW + barPad + di * barW;
        var top  = yPos(Math.max(v, 0));
        var bot  = yPos(Math.min(v, 0));
        var h    = Math.abs(bot - top) || 2;
        ctx.fillRect(x, top, barW - 2, h);
      }
    });

    // X labels
    ctx.fillStyle = "#64748b";
    ctx.font = "11px system-ui";
    ctx.textAlign = "center";
    for (var i = 0; i < n; i++) {
      ctx.fillText(labels[i], padL + i * groupW + groupW / 2, H - 6);
    }

    // Y labels
    ctx.textAlign = "right";
    for (var g2 = 0; g2 <= gridLines; g2++) {
      var val = minV + ((gridLines - g2) / gridLines) * range;
      var gy2 = padT + (g2 / gridLines) * chartH;
      ctx.fillText(fmt(val, 0), padL - 4, gy2 + 4);
    }

    // Legend
    if (datasets.length > 1) {
      var lx = padL;
      datasets.forEach(function(ds) {
        ctx.fillStyle = ds.color;
        ctx.fillRect(lx, padT - 14, 10, 10);
        ctx.fillStyle = "#475569";
        ctx.textAlign = "left";
        ctx.font = "10px system-ui";
        ctx.fillText(ds.label, lx + 13, padT - 5);
        lx += ctx.measureText(ds.label).width + 30;
      });
    }
  }

  /* ===== ERROR HELPER ===== */
  function roiErr(el, msg) {
    el.textContent = msg;
    el.classList.remove("hidden");
  }
})();
</script>
</div>

> Calculate compound interest → [Compound Interest Calculator](/tools/compound-interest-calculator/)
> Plan your retirement → [Pension Simulator](/tools/pension-simulator/)
> Manage your budget → [50/30/20 Budget Calculator](/tools/budget-planner/)

## Related Articles

- [Real Estate Investment in Japan for Salaried Workers: How It Compares to NISA and iDeCo](/posts/real-estate-investment-japan-salaried-worker/)
- [RENOSY Review for Expats: Is Real Estate Investment in Japan Worth It? (2026)](/posts/renosy-real-estate-investment-review-expat-japan/)
- [How to Make Money With AI in 2026: 15 Realistic Ways That Work](/posts/how-to-make-money-with-ai-2026/)
