---
title: "Loan Calculator - Free Payment & Amortization Tool"
date: 2025-05-16
description: "Calculate monthly loan payments, total interest, and payoff timeline. Compare loans, see amortization schedules. Works for personal, auto, and student loans."
categories: ["Free Tools"]
tags: ["loan calculator", "debt payoff", "amortization", "interest", "personal finance"]
slug: "loan-calculator"
aliases: ["/tools/debt-payoff-calculator/", "/tools/loan-calculator/", "/tools/loan-repayment-calculator/"]
cover:
  image: "/images/covers/loan-calculator.png"
  alt: "Loan Calculator"
ShowToc: false
---

<div id="loan-app">

<style>
#loan-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 960px;
  margin: 0 auto;
  color: #1f2937;
}

#loan-app * {
  box-sizing: border-box;
}

/* Tabs */
.loan-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 24px;
  flex-wrap: wrap;
}

.loan-tab {
  padding: 10px 20px;
  border: 2px solid #d1fae5;
  border-radius: 8px;
  background: #fff;
  color: #059669;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.loan-tab:hover {
  background: #f0fdf4;
}

.loan-tab.active {
  background: #059669;
  color: #fff;
  border-color: #059669;
}

/* Panels */
.loan-panel {
  display: none;
}

.loan-panel.active {
  display: block;
}

/* Input Group */
.input-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}

@media (max-width: 600px) {
  .input-grid {
    grid-template-columns: 1fr;
  }
}

.input-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.input-group label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
}

.input-row {
  display: flex;
  align-items: center;
  border: 2px solid #d1fae5;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
  transition: border-color 0.2s;
}

.input-row:focus-within {
  border-color: #059669;
}

.input-prefix, .input-suffix {
  padding: 10px 12px;
  background: #f0fdf4;
  color: #059669;
  font-weight: 700;
  font-size: 15px;
  border: none;
  white-space: nowrap;
}

.input-row input[type="number"],
.input-row input[type="text"] {
  flex: 1;
  border: none;
  outline: none;
  padding: 10px 12px;
  font-size: 16px;
  color: #1f2937;
  background: transparent;
  min-width: 0;
}

/* Term toggle */
.term-row {
  display: flex;
  align-items: center;
  border: 2px solid #d1fae5;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
  transition: border-color 0.2s;
}

.term-row:focus-within {
  border-color: #059669;
}

.term-row input[type="number"] {
  flex: 1;
  border: none;
  outline: none;
  padding: 10px 12px;
  font-size: 16px;
  color: #1f2937;
  background: transparent;
  min-width: 0;
}

.term-toggle {
  display: flex;
}

.term-toggle button {
  padding: 10px 12px;
  border: none;
  background: #f0fdf4;
  color: #6b7280;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.term-toggle button.active {
  background: #059669;
  color: #fff;
}

/* Calculate Button */
.calc-btn {
  width: 100%;
  padding: 14px;
  background: #059669;
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 17px;
  font-weight: 700;
  cursor: pointer;
  margin: 16px 0;
  transition: background 0.2s;
  letter-spacing: 0.3px;
}

.calc-btn:hover {
  background: #047857;
}

/* Result Card */
.result-hero {
  background: linear-gradient(135deg, #059669, #047857);
  border-radius: 14px;
  padding: 28px;
  text-align: center;
  color: #fff;
  margin-bottom: 20px;
}

.result-hero .label {
  font-size: 14px;
  opacity: 0.85;
  margin-bottom: 6px;
  font-weight: 500;
}

.result-hero .amount {
  font-size: 52px;
  font-weight: 800;
  letter-spacing: -1px;
  line-height: 1;
}

.result-hero .sublabel {
  font-size: 13px;
  opacity: 0.75;
  margin-top: 6px;
}

/* Summary Grid */
.summary-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-bottom: 20px;
}

@media (max-width: 600px) {
  .summary-grid {
    grid-template-columns: 1fr;
  }
}

.summary-card {
  background: #f0fdf4;
  border: 1px solid #d1fae5;
  border-radius: 10px;
  padding: 16px;
  text-align: center;
}

.summary-card .s-label {
  font-size: 12px;
  color: #6b7280;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  margin-bottom: 6px;
}

.summary-card .s-value {
  font-size: 22px;
  font-weight: 700;
  color: #059669;
}

.summary-card .s-sub {
  font-size: 12px;
  color: #6b7280;
  margin-top: 3px;
}

/* Pie Chart (CSS only) */
.chart-section {
  display: flex;
  align-items: center;
  gap: 32px;
  background: #f9fafb;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 20px;
  flex-wrap: wrap;
  justify-content: center;
}

.pie-wrap {
  position: relative;
  width: 140px;
  height: 140px;
  flex-shrink: 0;
}

.pie-chart {
  width: 140px;
  height: 140px;
  border-radius: 50%;
  background: conic-gradient(#059669 0deg 0deg, #6ee7b7 0deg 360deg);
  transition: background 0.5s;
}

.pie-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  font-size: 11px;
  font-weight: 700;
  color: #374151;
  pointer-events: none;
}

.pie-legend {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 10px;
}

.legend-dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  flex-shrink: 0;
}

.legend-dot.principal { background: #059669; }
.legend-dot.interest  { background: #6ee7b7; }

.legend-text .lt {
  font-size: 13px;
  color: #6b7280;
  font-weight: 500;
}

.legend-text .lv {
  font-size: 16px;
  font-weight: 700;
  color: #1f2937;
}

/* Payoff Timeline Bar */
.timeline-section {
  margin-bottom: 20px;
}

.timeline-title {
  font-size: 14px;
  font-weight: 600;
  color: #374151;
  margin-bottom: 8px;
}

.timeline-bar-wrap {
  background: #e5e7eb;
  border-radius: 99px;
  height: 22px;
  overflow: hidden;
  position: relative;
}

.timeline-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #059669, #34d399);
  border-radius: 99px;
  transition: width 0.6s ease;
  min-width: 4px;
}

.timeline-labels {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  color: #6b7280;
  margin-top: 5px;
}

/* Extra Payment Section */
.section-card {
  background: #fff;
  border: 2px solid #d1fae5;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
}

.section-card h3 {
  margin: 0 0 16px 0;
  font-size: 16px;
  color: #059669;
  font-weight: 700;
}

.extra-input-row {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 14px;
}

.extra-input-row .input-group {
  flex: 1;
  min-width: 180px;
}

.extra-impact {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

@media (max-width: 500px) {
  .extra-impact {
    grid-template-columns: 1fr;
  }
}

.impact-box {
  background: #f0fdf4;
  border: 1px solid #a7f3d0;
  border-radius: 8px;
  padding: 14px;
  text-align: center;
}

.impact-box .ib-label {
  font-size: 12px;
  color: #6b7280;
  font-weight: 600;
  margin-bottom: 4px;
}

.impact-box .ib-value {
  font-size: 20px;
  font-weight: 800;
  color: #059669;
}

/* Amortization Table */
.amort-section {
  margin-bottom: 20px;
}

.amort-section h3 {
  font-size: 16px;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 12px;
}

.table-wrap {
  overflow-x: auto;
  border-radius: 10px;
  border: 1px solid #e5e7eb;
}

.amort-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}

.amort-table th {
  background: #059669;
  color: #fff;
  padding: 10px 12px;
  text-align: right;
  font-weight: 600;
  white-space: nowrap;
}

.amort-table th:first-child {
  text-align: left;
}

.amort-table td {
  padding: 9px 12px;
  text-align: right;
  border-bottom: 1px solid #f3f4f6;
  color: #374151;
  white-space: nowrap;
}

.amort-table td:first-child {
  text-align: left;
  font-weight: 600;
  color: #1f2937;
}

.amort-table tr:nth-child(even) td {
  background: #f9fafb;
}

.amort-table tr:last-child td {
  background: #f0fdf4;
  font-weight: 700;
  color: #059669;
  border-bottom: none;
}

.amort-table tr:hover td {
  background: #ecfdf5;
}

.amort-toggle-btn {
  margin-top: 10px;
  padding: 8px 18px;
  background: #fff;
  border: 2px solid #059669;
  border-radius: 8px;
  color: #059669;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.amort-toggle-btn:hover {
  background: #f0fdf4;
}

/* Comparison Panel */
.compare-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 20px;
}

@media (max-width: 640px) {
  .compare-grid {
    grid-template-columns: 1fr;
  }
}

.compare-card {
  border: 2px solid #d1fae5;
  border-radius: 12px;
  padding: 18px;
  background: #fff;
}

.compare-card h3 {
  font-size: 15px;
  font-weight: 700;
  color: #059669;
  margin: 0 0 14px 0;
}

.compare-result {
  background: #f0fdf4;
  border: 1px solid #a7f3d0;
  border-radius: 10px;
  padding: 16px;
  text-align: center;
  margin-top: 12px;
}

.compare-result .cr-label {
  font-size: 12px;
  color: #6b7280;
  font-weight: 600;
  margin-bottom: 4px;
}

.compare-result .cr-value {
  font-size: 26px;
  font-weight: 800;
  color: #059669;
}

.compare-result .cr-sub {
  font-size: 12px;
  color: #6b7280;
  margin-top: 6px;
}

.compare-winner {
  border-color: #059669;
  background: linear-gradient(135deg, #f0fdf4, #d1fae5);
}

.winner-badge {
  display: inline-block;
  background: #059669;
  color: #fff;
  font-size: 11px;
  font-weight: 700;
  padding: 3px 10px;
  border-radius: 99px;
  margin-bottom: 6px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.compare-summary-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 16px;
  font-size: 13px;
}

.compare-summary-table th {
  background: #059669;
  color: #fff;
  padding: 9px 14px;
  text-align: center;
}

.compare-summary-table td {
  padding: 9px 14px;
  text-align: center;
  border-bottom: 1px solid #f3f4f6;
}

.compare-summary-table tr:nth-child(even) td {
  background: #f9fafb;
}

.compare-summary-table .best {
  color: #059669;
  font-weight: 700;
}

/* Hidden */
.hidden { display: none !important; }

/* Alert / info */
.info-box {
  background: #f0fdf4;
  border-left: 4px solid #059669;
  padding: 12px 16px;
  border-radius: 0 8px 8px 0;
  font-size: 13px;
  color: #374151;
  margin-bottom: 16px;
}
</style>

<div class="loan-tabs">
  <button class="loan-tab active" onclick="switchTab('basic')">Basic Calculator</button>
  <button class="loan-tab" onclick="switchTab('extra')">Extra Payments</button>
  <button class="loan-tab" onclick="switchTab('compare')">Compare Loans</button>
</div>

<!-- ===== BASIC PANEL ===== -->
<div id="panel-basic" class="loan-panel active">
  <div class="input-grid">
    <div class="input-group">
      <label>Loan Amount</label>
      <div class="input-row">
        <span class="input-prefix">$</span>
        <input type="number" id="b-amount" value="20000" min="0" step="100" placeholder="20000">
      </div>
    </div>
    <div class="input-group">
      <label>Annual Interest Rate</label>
      <div class="input-row">
        <input type="number" id="b-rate" value="6.5" min="0" step="0.01" placeholder="6.5">
        <span class="input-suffix">%</span>
      </div>
    </div>
    <div class="input-group">
      <label>Loan Term</label>
      <div class="term-row">
        <input type="number" id="b-term" value="5" min="1" step="1" placeholder="5">
        <div class="term-toggle">
          <button id="b-term-yr" class="active" onclick="setTermUnit('years')">Yrs</button>
          <button id="b-term-mo" onclick="setTermUnit('months')">Mo</button>
        </div>
      </div>
    </div>
    <div class="input-group">
      <label>Start Date (optional)</label>
      <div class="input-row">
        <input type="month" id="b-start" style="padding:10px 12px;border:none;outline:none;font-size:15px;color:#1f2937;background:transparent;flex:1;min-width:0;">
      </div>
    </div>
  </div>

  <button class="calc-btn" onclick="calcBasic()">Calculate Monthly Payment</button>

  <div id="basic-results" class="hidden">
    <div class="result-hero">
      <div class="label">Monthly Payment</div>
      <div class="amount" id="r-monthly">$0.00</div>
      <div class="sublabel" id="r-sublabel"></div>
    </div>

    <div class="summary-grid">
      <div class="summary-card">
        <div class="s-label">Total Payment</div>
        <div class="s-value" id="r-total">$0</div>
        <div class="s-sub">principal + interest</div>
      </div>
      <div class="summary-card">
        <div class="s-label">Total Interest</div>
        <div class="s-value" id="r-interest">$0</div>
        <div class="s-sub" id="r-interest-pct">0% of loan</div>
      </div>
      <div class="summary-card">
        <div class="s-label">Payoff Date</div>
        <div class="s-value" id="r-payoff" style="font-size:16px;margin-top:4px;">—</div>
        <div class="s-sub" id="r-payoff-sub"></div>
      </div>
    </div>

    <!-- Pie Chart -->
    <div class="chart-section">
      <div class="pie-wrap">
        <div class="pie-chart" id="pie-chart"></div>
        <div class="pie-center" id="pie-center"></div>
      </div>
      <div class="pie-legend">
        <div class="legend-item">
          <div class="legend-dot principal"></div>
          <div class="legend-text">
            <div class="lt">Principal</div>
            <div class="lv" id="legend-principal">$0</div>
          </div>
        </div>
        <div class="legend-item">
          <div class="legend-dot interest"></div>
          <div class="legend-text">
            <div class="lt">Total Interest</div>
            <div class="lv" id="legend-interest">$0</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Timeline Bar -->
    <div class="timeline-section">
      <div class="timeline-title" id="timeline-title">Payoff Progress</div>
      <div class="timeline-bar-wrap">
        <div class="timeline-bar-fill" id="timeline-bar" style="width:0%"></div>
      </div>
      <div class="timeline-labels">
        <span>Today</span>
        <span id="timeline-mid"></span>
        <span id="timeline-end">Payoff</span>
      </div>
    </div>

    <!-- Amortization Table -->
    <div class="amort-section">
      <h3>Amortization Schedule</h3>
      <div class="table-wrap">
        <table class="amort-table">
          <thead>
            <tr>
              <th>Month</th>
              <th>Payment</th>
              <th>Principal</th>
              <th>Interest</th>
              <th>Balance</th>
            </tr>
          </thead>
          <tbody id="amort-body"></tbody>
        </table>
      </div>
      <button class="amort-toggle-btn" id="amort-toggle" onclick="toggleAmort()">Show Full Schedule</button>
    </div>
  </div>
</div>

<!-- ===== EXTRA PAYMENTS PANEL ===== -->
<div id="panel-extra" class="loan-panel">
  <div class="info-box">
    See how extra payments reduce your total interest and payoff time.
  </div>

  <div class="input-grid">
    <div class="input-group">
      <label>Loan Amount</label>
      <div class="input-row">
        <span class="input-prefix">$</span>
        <input type="number" id="e-amount" value="20000" min="0" step="100">
      </div>
    </div>
    <div class="input-group">
      <label>Annual Interest Rate</label>
      <div class="input-row">
        <input type="number" id="e-rate" value="6.5" min="0" step="0.01">
        <span class="input-suffix">%</span>
      </div>
    </div>
    <div class="input-group">
      <label>Loan Term (years)</label>
      <div class="input-row">
        <input type="number" id="e-term" value="5" min="1" step="1">
        <span class="input-suffix">yrs</span>
      </div>
    </div>
  </div>

  <div class="section-card">
    <h3>Extra Payments</h3>
    <div class="extra-input-row">
      <div class="input-group">
        <label>Extra Monthly Payment</label>
        <div class="input-row">
          <span class="input-prefix">$</span>
          <input type="number" id="e-monthly-extra" value="100" min="0" step="10" placeholder="0">
        </div>
      </div>
      <div class="input-group">
        <label>One-Time Extra Payment</label>
        <div class="input-row">
          <span class="input-prefix">$</span>
          <input type="number" id="e-onetime" value="0" min="0" step="100" placeholder="0">
        </div>
      </div>
      <div class="input-group">
        <label>One-Time Payment at Month #</label>
        <div class="input-row">
          <input type="number" id="e-onetime-month" value="1" min="1" step="1" placeholder="1">
        </div>
      </div>
    </div>
  </div>

  <button class="calc-btn" onclick="calcExtra()">Calculate Impact</button>

  <div id="extra-results" class="hidden">
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:20px;">
      <div class="result-hero" style="margin-bottom:0">
        <div class="label">Original Monthly</div>
        <div class="amount" id="e-orig-monthly" style="font-size:36px">$0</div>
        <div class="sublabel" id="e-orig-term"></div>
      </div>
      <div class="result-hero" style="margin-bottom:0;background:linear-gradient(135deg,#047857,#065f46)">
        <div class="label">New Monthly</div>
        <div class="amount" id="e-new-monthly" style="font-size:36px">$0</div>
        <div class="sublabel" id="e-new-term"></div>
      </div>
    </div>

    <div class="extra-impact">
      <div class="impact-box">
        <div class="ib-label">Time Saved</div>
        <div class="ib-value" id="e-time-saved">0 months</div>
      </div>
      <div class="impact-box">
        <div class="ib-label">Interest Saved</div>
        <div class="ib-value" id="e-interest-saved">$0</div>
      </div>
      <div class="impact-box">
        <div class="ib-label">Original Total Interest</div>
        <div class="ib-value" id="e-orig-interest">$0</div>
      </div>
      <div class="impact-box">
        <div class="ib-label">New Total Interest</div>
        <div class="ib-value" id="e-new-interest">$0</div>
      </div>
    </div>
  </div>
</div>

<!-- ===== COMPARE PANEL ===== -->
<div id="panel-compare" class="loan-panel">
  <div class="info-box">
    Enter two loan options to compare total cost, monthly payment, and interest side by side.
  </div>

  <div class="compare-grid">
    <!-- Loan A -->
    <div class="compare-card">
      <h3>Loan A</h3>
      <div class="input-group" style="margin-bottom:12px">
        <label>Loan Amount</label>
        <div class="input-row">
          <span class="input-prefix">$</span>
          <input type="number" id="ca-amount" value="20000" min="0" step="100">
        </div>
      </div>
      <div class="input-group" style="margin-bottom:12px">
        <label>Annual Interest Rate</label>
        <div class="input-row">
          <input type="number" id="ca-rate" value="6.5" min="0" step="0.01">
          <span class="input-suffix">%</span>
        </div>
      </div>
      <div class="input-group" style="margin-bottom:12px">
        <label>Loan Term (years)</label>
        <div class="input-row">
          <input type="number" id="ca-term" value="5" min="1" step="1">
          <span class="input-suffix">yrs</span>
        </div>
      </div>
      <div class="compare-result" id="ca-result" style="display:none">
        <div class="cr-label">Monthly Payment</div>
        <div class="cr-value" id="ca-monthly">$0</div>
        <div class="cr-sub" id="ca-sub"></div>
      </div>
    </div>

    <!-- Loan B -->
    <div class="compare-card">
      <h3>Loan B</h3>
      <div class="input-group" style="margin-bottom:12px">
        <label>Loan Amount</label>
        <div class="input-row">
          <span class="input-prefix">$</span>
          <input type="number" id="cb-amount" value="20000" min="0" step="100">
        </div>
      </div>
      <div class="input-group" style="margin-bottom:12px">
        <label>Annual Interest Rate</label>
        <div class="input-row">
          <input type="number" id="cb-rate" value="8.0" min="0" step="0.01">
          <span class="input-suffix">%</span>
        </div>
      </div>
      <div class="input-group" style="margin-bottom:12px">
        <label>Loan Term (years)</label>
        <div class="input-row">
          <input type="number" id="cb-term" value="5" min="1" step="1">
          <span class="input-suffix">yrs</span>
        </div>
      </div>
      <div class="compare-result" id="cb-result" style="display:none">
        <div class="cr-label">Monthly Payment</div>
        <div class="cr-value" id="cb-monthly">$0</div>
        <div class="cr-sub" id="cb-sub"></div>
      </div>
    </div>
  </div>

  <button class="calc-btn" onclick="calcCompare()">Compare Loans</button>

  <div id="compare-results" class="hidden">
    <div class="table-wrap">
      <table class="compare-summary-table">
        <thead>
          <tr>
            <th>Metric</th>
            <th>Loan A</th>
            <th>Loan B</th>
          </tr>
        </thead>
        <tbody id="compare-body"></tbody>
      </table>
    </div>
  </div>
</div>

<script>
(function() {

/* ---- State ---- */
var termUnit = 'years'; // 'years' or 'months'
var amortExpanded = false;
var lastAmortData = [];

/* ---- Tabs ---- */
window.switchTab = function(name) {
  document.querySelectorAll('.loan-panel').forEach(function(p){ p.classList.remove('active'); });
  document.querySelectorAll('.loan-tab').forEach(function(t){ t.classList.remove('active'); });
  document.getElementById('panel-' + name).classList.add('active');
  var tabs = document.querySelectorAll('.loan-tab');
  var map = {basic:0, extra:1, compare:2};
  tabs[map[name]].classList.add('active');
};

/* ---- Term unit toggle ---- */
window.setTermUnit = function(unit) {
  termUnit = unit;
  document.getElementById('b-term-yr').classList.toggle('active', unit === 'years');
  document.getElementById('b-term-mo').classList.toggle('active', unit === 'months');
};

/* ---- Formatters ---- */
function fmt(n) {
  return '$' + n.toLocaleString('en-US', {minimumFractionDigits:2, maximumFractionDigits:2});
}
function fmtShort(n) {
  if (n >= 1000000) return '$' + (n/1000000).toFixed(2) + 'M';
  if (n >= 1000) return '$' + (n/1000).toFixed(1) + 'K';
  return '$' + n.toFixed(0);
}

/* ---- Monthly payment formula ---- */
function calcPayment(principal, annualRate, months) {
  if (annualRate === 0) return principal / months;
  var r = annualRate / 100 / 12;
  return principal * r * Math.pow(1+r, months) / (Math.pow(1+r, months) - 1);
}

/* ---- Build amortization schedule ---- */
function buildAmort(principal, annualRate, months, extraMonthly, oneTime, oneTimeMonth) {
  var r = annualRate / 100 / 12;
  var payment = calcPayment(principal, annualRate, months);
  var schedule = [];
  var balance = principal;
  var totalInterest = 0;

  for (var m = 1; m <= months && balance > 0.005; m++) {
    var interestDue = balance * r;
    var extra = (extraMonthly || 0);
    if (m === (oneTimeMonth || 1)) extra += (oneTime || 0);
    var principalPaid = Math.min(balance, payment - interestDue + extra);
    if (principalPaid < 0) principalPaid = 0;
    var actualPayment = interestDue + principalPaid;
    balance -= principalPaid;
    if (balance < 0.005) balance = 0;
    totalInterest += interestDue;
    schedule.push({
      month: m,
      payment: actualPayment,
      principal: principalPaid,
      interest: interestDue,
      balance: balance
    });
    if (balance === 0) break;
  }
  return schedule;
}

/* ---- Payoff date string ---- */
function payoffDateStr(months) {
  var startEl = document.getElementById('b-start');
  var base;
  if (startEl && startEl.value) {
    var parts = startEl.value.split('-');
    base = new Date(parseInt(parts[0]), parseInt(parts[1])-1, 1);
  } else {
    base = new Date();
  }
  base.setMonth(base.getMonth() + months);
  return base.toLocaleDateString('en-US', {month:'long', year:'numeric'});
}

/* ---- BASIC CALC ---- */
window.calcBasic = function() {
  var amount = parseFloat(document.getElementById('b-amount').value) || 0;
  var rate   = parseFloat(document.getElementById('b-rate').value)  || 0;
  var term   = parseInt(document.getElementById('b-term').value)    || 0;
  var months = termUnit === 'years' ? term * 12 : term;

  if (amount <= 0 || months <= 0) return;

  var monthly   = calcPayment(amount, rate, months);
  var schedule  = buildAmort(amount, rate, months, 0, 0, 0);
  var totalInt  = schedule.reduce(function(s,r){ return s+r.interest; }, 0);
  var totalPay  = schedule.reduce(function(s,r){ return s+r.payment;  }, 0);
  var actualMo  = schedule.length;

  // Hero
  document.getElementById('r-monthly').textContent = fmt(monthly);
  document.getElementById('r-sublabel').textContent = 'for ' + actualMo + ' months';

  // Summary
  document.getElementById('r-total').textContent      = fmtShort(totalPay);
  document.getElementById('r-interest').textContent   = fmtShort(totalInt);
  document.getElementById('r-interest-pct').textContent = (totalInt/amount*100).toFixed(1) + '% of principal';
  document.getElementById('r-payoff').textContent     = payoffDateStr(actualMo);
  document.getElementById('r-payoff-sub').textContent = actualMo + ' months from now';

  // Pie chart
  var principalDeg = Math.round(amount / totalPay * 360);
  document.getElementById('pie-chart').style.background =
    'conic-gradient(#059669 0deg ' + principalDeg + 'deg, #6ee7b7 ' + principalDeg + 'deg 360deg)';
  document.getElementById('pie-center').textContent = Math.round(amount/totalPay*100) + '%\nprincipal';
  document.getElementById('legend-principal').textContent = fmtShort(amount);
  document.getElementById('legend-interest').textContent  = fmtShort(totalInt);

  // Timeline bar — show 50% for full term (visual metaphor: you're at start)
  document.getElementById('timeline-bar').style.width = '4%';
  document.getElementById('timeline-title').textContent = 'Payoff Timeline — ' + actualMo + ' months';
  document.getElementById('timeline-mid').textContent = Math.round(actualMo/2) + ' months';
  document.getElementById('timeline-end').textContent  = payoffDateStr(actualMo);

  // Amortization
  lastAmortData = schedule;
  amortExpanded = false;
  renderAmort(false);

  document.getElementById('basic-results').classList.remove('hidden');
};

function renderAmort(full) {
  var data = full ? lastAmortData : lastAmortData.slice(0, 12);
  var body = document.getElementById('amort-body');
  body.innerHTML = '';

  data.forEach(function(row) {
    var tr = document.createElement('tr');
    tr.innerHTML = '<td>Month ' + row.month + '</td>' +
      '<td>' + fmt(row.payment) + '</td>' +
      '<td>' + fmt(row.principal) + '</td>' +
      '<td>' + fmt(row.interest) + '</td>' +
      '<td>' + fmt(row.balance) + '</td>';
    body.appendChild(tr);
  });

  // Totals row
  var totPay  = lastAmortData.reduce(function(s,r){return s+r.payment;},0);
  var totPrin = lastAmortData.reduce(function(s,r){return s+r.principal;},0);
  var totInt  = lastAmortData.reduce(function(s,r){return s+r.interest;},0);
  var tr = document.createElement('tr');
  tr.innerHTML = '<td>Total</td>' +
    '<td>' + fmt(totPay) + '</td>' +
    '<td>' + fmt(totPrin) + '</td>' +
    '<td>' + fmt(totInt) + '</td>' +
    '<td>$0.00</td>';
  body.appendChild(tr);

  var btn = document.getElementById('amort-toggle');
  if (lastAmortData.length <= 12) {
    btn.style.display = 'none';
  } else {
    btn.style.display = '';
    btn.textContent = full ? 'Show First 12 Months' : 'Show Full Schedule (' + lastAmortData.length + ' months)';
  }
}

window.toggleAmort = function() {
  amortExpanded = !amortExpanded;
  renderAmort(amortExpanded);
};

/* ---- EXTRA PAYMENT CALC ---- */
window.calcExtra = function() {
  var amount   = parseFloat(document.getElementById('e-amount').value) || 0;
  var rate     = parseFloat(document.getElementById('e-rate').value)   || 0;
  var term     = parseInt(document.getElementById('e-term').value)     || 0;
  var extraMo  = parseFloat(document.getElementById('e-monthly-extra').value) || 0;
  var oneTime  = parseFloat(document.getElementById('e-onetime').value)       || 0;
  var otMonth  = parseInt(document.getElementById('e-onetime-month').value)   || 1;
  var months   = term * 12;

  if (amount <= 0 || months <= 0) return;

  var origSchedule = buildAmort(amount, rate, months, 0, 0, 0);
  var newSchedule  = buildAmort(amount, rate, months, extraMo, oneTime, otMonth);

  var origInt  = origSchedule.reduce(function(s,r){return s+r.interest;},0);
  var newInt   = newSchedule.reduce(function(s,r){return s+r.interest;},0);
  var origPay  = calcPayment(amount, rate, months);
  var newPay   = origPay + extraMo;

  var timeSaved = origSchedule.length - newSchedule.length;
  var intSaved  = origInt - newInt;

  document.getElementById('e-orig-monthly').textContent = fmt(origPay);
  document.getElementById('e-orig-term').textContent    = origSchedule.length + ' months';
  document.getElementById('e-new-monthly').textContent  = fmt(newPay);
  document.getElementById('e-new-term').textContent     = newSchedule.length + ' months';

  document.getElementById('e-time-saved').textContent = timeSaved > 0
    ? timeSaved + ' month' + (timeSaved !== 1 ? 's' : '')
    : '0 months';
  document.getElementById('e-interest-saved').textContent = fmtShort(intSaved > 0 ? intSaved : 0);
  document.getElementById('e-orig-interest').textContent  = fmtShort(origInt);
  document.getElementById('e-new-interest').textContent   = fmtShort(newInt);

  document.getElementById('extra-results').classList.remove('hidden');
};

/* ---- COMPARE CALC ---- */
window.calcCompare = function() {
  var aAmt  = parseFloat(document.getElementById('ca-amount').value) || 0;
  var aRate = parseFloat(document.getElementById('ca-rate').value)   || 0;
  var aTerm = parseInt(document.getElementById('ca-term').value)     || 0;
  var bAmt  = parseFloat(document.getElementById('cb-amount').value) || 0;
  var bRate = parseFloat(document.getElementById('cb-rate').value)   || 0;
  var bTerm = parseInt(document.getElementById('cb-term').value)     || 0;

  if (aAmt <= 0 || aTerm <= 0 || bAmt <= 0 || bTerm <= 0) return;

  var aMo    = aTerm * 12;
  var bMo    = bTerm * 12;
  var aPayMo = calcPayment(aAmt, aRate, aMo);
  var bPayMo = calcPayment(bAmt, bRate, bMo);

  var aSched  = buildAmort(aAmt, aRate, aMo, 0, 0, 0);
  var bSched  = buildAmort(bAmt, bRate, bMo, 0, 0, 0);
  var aInt    = aSched.reduce(function(s,r){return s+r.interest;},0);
  var bInt    = bSched.reduce(function(s,r){return s+r.interest;},0);
  var aTot    = aPayMo * aMo;
  var bTot    = bPayMo * bMo;

  // Update mini result cards
  document.getElementById('ca-monthly').textContent = fmt(aPayMo);
  document.getElementById('ca-sub').textContent     = 'Total: ' + fmtShort(aTot) + ' | Interest: ' + fmtShort(aInt);
  document.getElementById('ca-result').style.display = '';

  document.getElementById('cb-monthly').textContent = fmt(bPayMo);
  document.getElementById('cb-sub').textContent     = 'Total: ' + fmtShort(bTot) + ' | Interest: ' + fmtShort(bInt);
  document.getElementById('cb-result').style.display = '';

  // Winner highlight
  var aCard = document.querySelector('.compare-card:first-of-type');
  var bCard = document.querySelector('.compare-card:last-of-type');
  var aWin  = aInt < bInt;
  aCard.classList.toggle('compare-winner', aWin);
  bCard.classList.toggle('compare-winner', !aWin);

  // Comparison table
  function better(a, b, lowerIsBetter) {
    if (lowerIsBetter) return a < b ? 'A' : (b < a ? 'B' : '-');
    return a > b ? 'A' : (b > a ? 'B' : '-');
  }

  var rows = [
    ['Loan Amount',    fmt(aAmt),          fmt(bAmt),          null],
    ['Interest Rate',  aRate+'%',          bRate+'%',          better(aRate,bRate,true)],
    ['Loan Term',      aTerm+' yrs',       bTerm+' yrs',       null],
    ['Monthly Payment',fmt(aPayMo),        fmt(bPayMo),        better(aPayMo,bPayMo,true)],
    ['Total Payment',  fmtShort(aTot),     fmtShort(bTot),     better(aTot,bTot,true)],
    ['Total Interest', fmtShort(aInt),     fmtShort(bInt),     better(aInt,bInt,true)],
    ['Interest %',     (aInt/aAmt*100).toFixed(1)+'%', (bInt/bAmt*100).toFixed(1)+'%', better(aInt/aAmt,bInt/bAmt,true)],
  ];

  var tbody = document.getElementById('compare-body');
  tbody.innerHTML = '';
  rows.forEach(function(row) {
    var tr = document.createElement('tr');
    var winner = row[3];
    tr.innerHTML = '<td style="text-align:left;font-weight:600">' + row[0] + '</td>' +
      '<td class="' + (winner==='A'?'best':'') + '">' + row[1] + (winner==='A'?' ★':'') + '</td>' +
      '<td class="' + (winner==='B'?'best':'') + '">' + row[2] + (winner==='B'?' ★':'') + '</td>';
    tbody.appendChild(tr);
  });

  document.getElementById('compare-results').classList.remove('hidden');
};

/* Auto-run on load */
calcBasic();

})();
</script>

</div>

---

## How to Use This Loan Calculator

1. **Enter your loan details** — input the loan amount, annual interest rate, and term in years or months.
2. **Click Calculate** — your monthly payment appears instantly, along with total interest and payoff date.
3. **Review the amortization schedule** — see exactly how each payment splits between principal and interest month by month.
4. **Try extra payments** — switch to the Extra Payments tab and enter an additional monthly or one-time payment to see how much time and money you save.
5. **Compare two loans** — use the Compare Loans tab to evaluate different rate or term options side by side before signing.

---

## Tips for Paying Off Loans Faster

- **Add even a small extra monthly payment.** An extra $50–$100/month on a 5-year loan can shave months off your payoff and save hundreds in interest.
- **Make one extra payment per year.** Apply a tax refund, bonus, or side income directly to your principal — this alone can cut a 30-year mortgage by several years.
- **Choose the shortest term you can comfortably afford.** A 3-year auto loan costs far less in total interest than a 6-year loan, even at the same rate.
- **Refinance when rates drop.** If your credit improves or market rates fall, refinancing at a lower rate reduces both your monthly payment and lifetime interest.

---

## Related Tools

> Calculate percentages and discounts → [Percentage Calculator](/tools/percentage-calculator/)

> See how inflation affects your money → [Inflation Calculator](/tools/inflation-calculator/)

> Track your subscription costs → [Subscription Cost Calculator](/tools/subscription-cost-calculator/)

## Related Articles

- [How to Pay Off Debt Fast: Best Strategies 2026](/posts/how-to-pay-off-debt-fast-strategies/)
