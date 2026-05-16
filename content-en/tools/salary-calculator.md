---
title: "US Salary Calculator — Take-Home Pay After Taxes"
date: 2026-05-15
draft: false
slug: "salary-calculator"
aliases:
  - /tools/take-home-pay/
description: "Calculate your actual take-home pay after federal tax, state tax, Social Security, Medicare, and 401(k). Supports all 50 states with 2026 tax brackets."
categories: ["Free Tools"]
tags: ["salary calculator", "take-home pay", "income tax", "federal tax", "state tax"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/salary-calculator.png"
  alt: "US Salary Calculator"
  relative: true
---

<style>
.sc-wrap {
  max-width: 720px;
  margin: 0 auto;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: #1e293b;
}
.sc-card {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 14px;
  padding: 28px;
  margin-bottom: 20px;
  box-shadow: 0 2px 8px rgba(74,158,255,0.07);
}
.sc-section-title {
  font-size: 15px;
  font-weight: 700;
  color: #4a9eff;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin: 0 0 18px 0;
}
.sc-field {
  margin-bottom: 18px;
}
.sc-label {
  display: block;
  font-size: 14px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 8px;
}
.sc-range-row {
  display: flex;
  align-items: center;
  gap: 12px;
}
.sc-range-row input[type="range"] {
  flex: 1;
  accent-color: #4a9eff;
  cursor: pointer;
}
.sc-number-input {
  width: 110px;
  padding: 7px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  font-weight: 600;
  color: #1e293b;
  text-align: right;
  transition: border-color .2s;
}
.sc-number-input:focus {
  outline: none;
  border-color: #4a9eff;
  box-shadow: 0 0 0 3px rgba(74,158,255,0.15);
}
.sc-select {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  color: #1e293b;
  background: #fff;
  cursor: pointer;
  transition: border-color .2s;
}
.sc-select:focus {
  outline: none;
  border-color: #4a9eff;
  box-shadow: 0 0 0 3px rgba(74,158,255,0.15);
}
.sc-grid-2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
}
@media (max-width: 500px) {
  .sc-grid-2 { grid-template-columns: 1fr; }
}
.sc-result-hero {
  background: linear-gradient(135deg, #1d4ed8 0%, #4a9eff 100%);
  border-radius: 12px;
  padding: 28px 20px;
  text-align: center;
  color: #fff;
  margin-bottom: 20px;
}
.sc-result-hero .label {
  font-size: 14px;
  opacity: .85;
  margin-bottom: 6px;
  letter-spacing: .04em;
}
.sc-result-hero .amount {
  font-size: 48px;
  font-weight: 800;
  letter-spacing: -1px;
  line-height: 1;
}
.sc-result-hero .sub {
  margin-top: 14px;
  font-size: 15px;
  opacity: .9;
  display: flex;
  justify-content: center;
  gap: 24px;
  flex-wrap: wrap;
}
.sc-result-hero .sub span { font-weight: 700; }
.sc-rate-row {
  display: flex;
  gap: 14px;
  margin-bottom: 20px;
}
.sc-rate-box {
  flex: 1;
  border-radius: 10px;
  padding: 14px 12px;
  text-align: center;
}
.sc-rate-box .rl { font-size: 12px; color: #64748b; margin-bottom: 4px; }
.sc-rate-box .rv { font-size: 20px; font-weight: 700; }
.sc-breakdown-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}
.sc-breakdown-table th {
  text-align: left;
  font-size: 12px;
  font-weight: 700;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: .06em;
  padding: 0 0 8px 0;
  border-bottom: 1px solid #e2e8f0;
}
.sc-breakdown-table th:last-child { text-align: right; }
.sc-breakdown-table td {
  padding: 10px 0;
  border-bottom: 1px solid #f1f5f9;
  color: #334155;
}
.sc-breakdown-table td:last-child {
  text-align: right;
  font-weight: 600;
  color: #dc2626;
}
.sc-breakdown-table tr.total-row td {
  font-weight: 700;
  font-size: 15px;
  color: #1e293b;
  border-bottom: none;
  padding-top: 12px;
}
.sc-breakdown-table tr.total-row td:last-child { color: #dc2626; }
.sc-dot {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin-right: 7px;
  vertical-align: middle;
}
.sc-bar-wrap {
  display: flex;
  height: 20px;
  border-radius: 6px;
  overflow: hidden;
  margin-bottom: 10px;
}
.sc-bar-legend {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  font-size: 12px;
  color: #475569;
}
.sc-other-row {
  display: none;
  margin-top: 10px;
}
.sc-note {
  background: #f8fafc;
  border-left: 3px solid #4a9eff;
  border-radius: 0 8px 8px 0;
  padding: 12px 16px;
  font-size: 13px;
  color: #64748b;
  line-height: 1.6;
  margin-top: 8px;
}
.sc-affiliate {
  background: #fffbeb;
  border: 1px solid #fde68a;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 20px;
}
.sc-affiliate p { margin: 0 0 8px 0; font-size: 14px; font-weight: 600; color: #92400e; }
.sc-affiliate a { color: #b45309; font-weight: 600; }
.sc-crosslinks {
  background: #f0f9ff;
  border: 1px solid #bae6fd;
  border-radius: 10px;
  padding: 18px 20px;
}
.sc-crosslinks p { margin: 0 0 10px 0; font-size: 14px; font-weight: 700; color: #0369a1; }
.sc-crosslinks ul { margin: 0; padding: 0 0 0 18px; }
.sc-crosslinks ul li { margin-bottom: 6px; font-size: 14px; }
.sc-crosslinks ul li a { color: #0284c7; font-weight: 500; }
</style>

<div class="sc-wrap">

<!-- ===== INPUTS ===== -->
<div class="sc-card">
  <div class="sc-section-title">Your Info</div>

  <div class="sc-field">
    <label class="sc-label" for="sc-salary">Annual Gross Salary ($)</label>
    <div class="sc-range-row">
      <input type="range" id="sc-salary-range" min="10000" max="500000" step="1000" value="75000">
      <input type="number" id="sc-salary" class="sc-number-input" min="10000" max="500000" value="75000">
    </div>
  </div>

  <div class="sc-grid-2">
    <div class="sc-field">
      <label class="sc-label" for="sc-filing">Filing Status</label>
      <select id="sc-filing" class="sc-select">
        <option value="single">Single</option>
        <option value="married">Married Filing Jointly</option>
        <option value="head">Head of Household</option>
      </select>
    </div>
    <div class="sc-field">
      <label class="sc-label" for="sc-freq">Pay Frequency</label>
      <select id="sc-freq" class="sc-select">
        <option value="1">Annual</option>
        <option value="12">Monthly</option>
        <option value="26" selected>Bi-weekly</option>
        <option value="52">Weekly</option>
      </select>
    </div>
  </div>

  <div class="sc-field">
    <label class="sc-label" for="sc-state">State</label>
    <select id="sc-state" class="sc-select">
      <option value="CA">California (CA)</option>
      <option value="NY">New York (NY)</option>
      <option value="TX">Texas (TX)</option>
      <option value="FL">Florida (FL)</option>
      <option value="WA">Washington (WA)</option>
      <option value="IL">Illinois (IL)</option>
      <option value="PA">Pennsylvania (PA)</option>
      <option value="OH">Ohio (OH)</option>
      <option value="GA">Georgia (GA)</option>
      <option value="NC">North Carolina (NC)</option>
      <option value="NJ">New Jersey (NJ)</option>
      <option value="VA">Virginia (VA)</option>
      <option value="MA">Massachusetts (MA)</option>
      <option value="AZ">Arizona (AZ)</option>
      <option value="CO">Colorado (CO)</option>
      <option value="AL">Alabama (AL)</option>
      <option value="AK">Alaska (AK)</option>
      <option value="AR">Arkansas (AR)</option>
      <option value="CT">Connecticut (CT)</option>
      <option value="DE">Delaware (DE)</option>
      <option value="HI">Hawaii (HI)</option>
      <option value="ID">Idaho (ID)</option>
      <option value="IN">Indiana (IN)</option>
      <option value="IA">Iowa (IA)</option>
      <option value="KS">Kansas (KS)</option>
      <option value="KY">Kentucky (KY)</option>
      <option value="LA">Louisiana (LA)</option>
      <option value="ME">Maine (ME)</option>
      <option value="MD">Maryland (MD)</option>
      <option value="MI">Michigan (MI)</option>
      <option value="MN">Minnesota (MN)</option>
      <option value="MS">Mississippi (MS)</option>
      <option value="MO">Missouri (MO)</option>
      <option value="MT">Montana (MT)</option>
      <option value="NE">Nebraska (NE)</option>
      <option value="NV">Nevada (NV)</option>
      <option value="NH">New Hampshire (NH)</option>
      <option value="NM">New Mexico (NM)</option>
      <option value="ND">North Dakota (ND)</option>
      <option value="OK">Oklahoma (OK)</option>
      <option value="OR">Oregon (OR)</option>
      <option value="RI">Rhode Island (RI)</option>
      <option value="SC">South Carolina (SC)</option>
      <option value="SD">South Dakota (SD)</option>
      <option value="TN">Tennessee (TN)</option>
      <option value="UT">Utah (UT)</option>
      <option value="VT">Vermont (VT)</option>
      <option value="WV">West Virginia (WV)</option>
      <option value="WI">Wisconsin (WI)</option>
      <option value="WY">Wyoming (WY)</option>
      <option value="DC">Washington D.C. (DC)</option>
      <option value="OTHER">Other (enter rate manually)</option>
    </select>
    <div class="sc-other-row" id="sc-other-row">
      <label class="sc-label" for="sc-other-rate">State Tax Rate (%)</label>
      <input type="number" id="sc-other-rate" class="sc-number-input" min="0" max="20" step="0.1" value="5" style="width:90px;">
    </div>
  </div>

  <div class="sc-grid-2">
    <div class="sc-field">
      <label class="sc-label" for="sc-401k">401(k) Contribution (%)</label>
      <div class="sc-range-row">
        <input type="range" id="sc-401k-range" min="0" max="100" step="1" value="6">
        <input type="number" id="sc-401k" class="sc-number-input" min="0" max="100" value="6" style="width:80px;">
      </div>
    </div>
    <div class="sc-field">
      <label class="sc-label" for="sc-pretax">Additional Pre-tax Deductions ($)</label>
      <input type="number" id="sc-pretax" class="sc-number-input" min="0" value="0" style="width:100%;">
    </div>
  </div>
</div>

<!-- ===== RESULTS ===== -->
<div class="sc-result-hero" id="sc-hero">
  <div class="label">Annual Take-Home Pay</div>
  <div class="amount" id="sc-takehome-annual">—</div>
  <div class="sub">
    <div>Monthly: <span id="sc-monthly">—</span></div>
    <div>Bi-weekly: <span id="sc-biweekly">—</span></div>
    <div>Weekly: <span id="sc-weekly">—</span></div>
  </div>
  <div style="margin-top:14px;font-size:14px;opacity:.85;" id="sc-per-period-label"></div>
</div>

<div class="sc-rate-row">
  <div class="sc-rate-box" style="background:#dcfce7;">
    <div class="rl">Effective Tax Rate</div>
    <div class="rv" style="color:#15803d;" id="sc-eff-rate">—</div>
  </div>
  <div class="sc-rate-box" style="background:#fef3c7;">
    <div class="rl">Marginal Tax Rate</div>
    <div class="rv" style="color:#b45309;" id="sc-marg-rate">—</div>
  </div>
  <div class="sc-rate-box" style="background:#fee2e2;">
    <div class="rl">Total Deductions</div>
    <div class="rv" style="color:#dc2626;" id="sc-total-ded">—</div>
  </div>
</div>

<div class="sc-card">
  <div class="sc-section-title">Tax Breakdown</div>
  <table class="sc-breakdown-table">
    <thead>
      <tr><th>Item</th><th>Annual Amount</th></tr>
    </thead>
    <tbody>
      <tr>
        <td><span class="sc-dot" style="background:#dc2626;"></span>Federal Income Tax</td>
        <td id="sc-fed-tax">—</td>
      </tr>
      <tr>
        <td><span class="sc-dot" style="background:#d97706;"></span>State Income Tax</td>
        <td id="sc-state-tax">—</td>
      </tr>
      <tr>
        <td><span class="sc-dot" style="background:#0369a1;"></span>Social Security (6.2%)</td>
        <td id="sc-ss">—</td>
      </tr>
      <tr>
        <td><span class="sc-dot" style="background:#7c3aed;"></span>Medicare</td>
        <td id="sc-med">—</td>
      </tr>
      <tr>
        <td><span class="sc-dot" style="background:#0891b2;"></span>401(k) Contribution</td>
        <td id="sc-401k-amt">—</td>
      </tr>
      <tr class="total-row">
        <td><strong>Total Deductions</strong></td>
        <td id="sc-total-ded-2">—</td>
      </tr>
    </tbody>
  </table>

  <!-- Stacked bar -->
  <div style="margin-top:20px;">
    <div style="font-size:12px;font-weight:600;color:#94a3b8;margin-bottom:8px;">Paycheck Breakdown</div>
    <div class="sc-bar-wrap">
      <div id="sc-bar-take" style="background:#16a34a;"></div>
      <div id="sc-bar-fed"  style="background:#dc2626;"></div>
      <div id="sc-bar-state" style="background:#d97706;"></div>
      <div id="sc-bar-ss"  style="background:#0369a1;"></div>
      <div id="sc-bar-med"  style="background:#7c3aed;"></div>
      <div id="sc-bar-401k" style="background:#0891b2;"></div>
    </div>
    <div class="sc-bar-legend">
      <span><span class="sc-dot" style="background:#16a34a;"></span>Take-home</span>
      <span><span class="sc-dot" style="background:#dc2626;"></span>Federal</span>
      <span><span class="sc-dot" style="background:#d97706;"></span>State</span>
      <span><span class="sc-dot" style="background:#0369a1;"></span>SS</span>
      <span><span class="sc-dot" style="background:#7c3aed;"></span>Medicare</span>
      <span><span class="sc-dot" style="background:#0891b2;"></span>401(k)</span>
    </div>
  </div>
</div>

<div class="sc-note">
  <strong>2026 tax brackets applied.</strong> Standard deduction: Single $15,200 / MFJ $30,400 / HoH $22,800. Social Security wage base $176,100. 401(k) contribution reduces federal &amp; state taxable income. State rates are simplified effective rates. Does not include local taxes, AMT, credits, or itemized deductions. For official tax advice consult a CPA.
</div>

<!-- ===== AFFILIATE ===== -->
<div class="sc-affiliate" style="margin-top:24px;">
  <p>Sponsored Links</p>
  <div style="margin-bottom:8px;">
    <a href="https://px.a8.net/svt/ejp?a8mat=3ZD3R9+DPXS1E+GDO+C03K1" rel="nofollow">Find higher-paying jobs on doda</a><img border="0" width="1" height="1" src="https://www12.a8.net/0.gif?a8mat=3ZD3R9+DPXS1E+GDO+C03K1" alt="">
  </div>
  <div>
    <a href="https://px.a8.net/svt/ejp?a8mat=3ZD3R9+DNEO+4PA2+5YJRM" rel="nofollow">Try freee for easy tax filing</a><img border="0" width="1" height="1" src="https://www14.a8.net/0.gif?a8mat=3ZD3R9+DNEO+4PA2+5YJRM" alt="">
  </div>
</div>

<!-- ===== CROSS-LINKS ===== -->
<div class="sc-crosslinks">
  <p>Other Free Financial Tools</p>
  <ul>
    <li><a href="/tools/compound-interest-calculator/">Compound Interest Calculator</a></li>
    <li><a href="/tools/budget-planner/">Budget Planner</a></li>
    <li><a href="/tools/loan-repayment-calculator/">Loan Repayment Calculator</a></li>
    <li><a href="/tools/retirement-calculator/">Retirement Calculator</a></li>
    <li><a href="/tools/forex-calculator/">Forex Profit Calculator</a></li>
  </ul>
</div>

</div><!-- /.sc-wrap -->

<script>
(function(){

// ── State tax effective rates (approximate) ───────────────────────────────
var STATE_RATES = {
  CA: 0.093, NY: 0.065, TX: 0,    FL: 0,    WA: 0,    IL: 0.0495,
  PA: 0.0307,OH: 0.04,  GA: 0.055,NC: 0.0475,NJ: 0.063,VA: 0.0575,
  MA: 0.05,  AZ: 0.025, CO: 0.044,AL: 0.05, AK: 0,    AR: 0.055,
  CT: 0.065, DE: 0.066, HI: 0.088,ID: 0.058,IN: 0.0315,IA: 0.06,
  KS: 0.057, KY: 0.045,LA: 0.04, ME: 0.075, MD: 0.055,MI: 0.0425,
  MN: 0.085, MS: 0.05,  MO: 0.054,MT: 0.069,NE: 0.068,NV: 0,
  NH: 0,     NM: 0.059, ND: 0.025,OK: 0.05, OR: 0.096,RI: 0.0599,
  SC: 0.064, SD: 0,     TN: 0,    UT: 0.0485,VT: 0.068,WV: 0.065,
  WI: 0.054, WY: 0,     DC: 0.085, OTHER: null
};

// ── 2026 Federal brackets ─────────────────────────────────────────────────
// Returns { tax, marginalRate }
function calcFederal(taxable, filing) {
  var brackets;
  if (filing === 'married') {
    brackets = [
      [23850,  0.10],
      [96950,  0.12],
      [206700, 0.22],
      [394600, 0.24],
      [501050, 0.32],
      [751600, 0.35],
      [Infinity, 0.37]
    ];
  } else if (filing === 'head') {
    brackets = [
      [17150,  0.10],
      [65150,  0.12],
      [105300, 0.22],
      [197300, 0.24],
      [250500, 0.32],
      [626350, 0.35],
      [Infinity, 0.37]
    ];
  } else { // single
    brackets = [
      [11925,  0.10],
      [48475,  0.12],
      [103350, 0.22],
      [197300, 0.24],
      [250525, 0.32],
      [626350, 0.35],
      [Infinity, 0.37]
    ];
  }

  var tax = 0;
  var prev = 0;
  var marginal = 0.10;
  for (var i = 0; i < brackets.length; i++) {
    var cap   = brackets[i][0];
    var rate  = brackets[i][1];
    if (taxable <= prev) break;
    var chunk = Math.min(taxable, cap) - prev;
    tax += chunk * rate;
    marginal = rate;
    prev = cap;
    if (taxable <= cap) break;
  }
  return { tax: Math.round(tax), marginalRate: marginal };
}

// ── Standard deductions 2026 ──────────────────────────────────────────────
function stdDed(filing) {
  if (filing === 'married') return 30400;
  if (filing === 'head')    return 22800;
  return 15200;
}

// ── Formatting helpers ────────────────────────────────────────────────────
function fmt(n)  { return '$' + Math.round(n).toLocaleString('en-US'); }
function pct(n)  { return (n * 100).toFixed(1) + '%'; }

// ── Frequency label ───────────────────────────────────────────────────────
var FREQ_LABEL = { '1': 'Annual', '12': 'Monthly', '26': 'Bi-weekly', '52': 'Weekly' };

// ── Main calculation ──────────────────────────────────────────────────────
function calculate() {
  var gross    = Math.max(10000, Math.min(500000, parseFloat(document.getElementById('sc-salary').value) || 75000));
  var filing   = document.getElementById('sc-filing').value;
  var stateKey = document.getElementById('sc-state').value;
  var freq     = document.getElementById('sc-freq').value;
  var k401pct  = Math.max(0, Math.min(100, parseFloat(document.getElementById('sc-401k').value) || 0)) / 100;
  var pretax   = Math.max(0, parseFloat(document.getElementById('sc-pretax').value) || 0);

  // State rate
  var stateRate;
  if (stateKey === 'OTHER') {
    stateRate = Math.max(0, parseFloat(document.getElementById('sc-other-rate').value) || 0) / 100;
  } else {
    stateRate = STATE_RATES[stateKey] || 0;
  }

  // Pre-tax deductions reduce taxable income
  var k401amt  = Math.round(gross * k401pct);
  var preTaxTotal = k401amt + pretax;
  var adjustedGross = Math.max(0, gross - preTaxTotal);

  // Federal taxable income
  var ded = stdDed(filing);
  var fedTaxable = Math.max(0, adjustedGross - ded);
  var fedResult  = calcFederal(fedTaxable, filing);
  var fedTax     = fedResult.tax;
  var margRate   = fedResult.marginalRate;

  // State tax (applied to adjusted gross, simplified)
  var stateTax = Math.round(adjustedGross * stateRate);

  // FICA (applied to gross, not reduced by 401k for simplicity — standard IRS rule)
  var ssWageBase = 176100;
  var ssAmt  = Math.round(Math.min(gross, ssWageBase) * 0.062);
  var medAmt = Math.round(gross * 0.0145);
  if (gross > 200000) medAmt += Math.round((gross - 200000) * 0.009);

  var totalTaxDed = fedTax + stateTax + ssAmt + medAmt;
  var totalDed    = totalTaxDed + k401amt; // 401k is a deduction from take-home but pre-tax
  var takeHome    = gross - totalDed - pretax;
  if (takeHome < 0) takeHome = 0;

  var effRate = totalDed / gross; // effective rate on all deductions

  // Per-period breakdown
  var periods = { '1': 1, '12': 12, '26': 26, '52': 52 };
  var p = periods[freq] || 26;

  // ── Update DOM ────────────────────────────────────────────────────────
  document.getElementById('sc-takehome-annual').textContent = fmt(takeHome);
  document.getElementById('sc-monthly').textContent   = fmt(takeHome / 12);
  document.getElementById('sc-biweekly').textContent  = fmt(takeHome / 26);
  document.getElementById('sc-weekly').textContent    = fmt(takeHome / 52);

  var freqLabel = FREQ_LABEL[freq] || 'Bi-weekly';
  document.getElementById('sc-per-period-label').textContent =
    freqLabel + ' Take-Home: ' + fmt(takeHome / p);

  document.getElementById('sc-eff-rate').textContent  = pct(effRate);
  document.getElementById('sc-marg-rate').textContent = (margRate * 100).toFixed(0) + '%';
  document.getElementById('sc-total-ded').textContent = fmt(totalDed + pretax);

  document.getElementById('sc-fed-tax').textContent   = fmt(fedTax);
  document.getElementById('sc-state-tax').textContent = fmt(stateTax);
  document.getElementById('sc-ss').textContent        = fmt(ssAmt);
  document.getElementById('sc-med').textContent       = fmt(medAmt);
  document.getElementById('sc-401k-amt').textContent  = fmt(k401amt);
  document.getElementById('sc-total-ded-2').textContent = fmt(totalDed + pretax);

  // Bar chart
  var total = gross || 1;
  function barW(amt) { return Math.max(0, Math.min(100, amt / total * 100)).toFixed(2) + '%'; }
  document.getElementById('sc-bar-take').style.width  = barW(takeHome);
  document.getElementById('sc-bar-fed').style.width   = barW(fedTax);
  document.getElementById('sc-bar-state').style.width = barW(stateTax);
  document.getElementById('sc-bar-ss').style.width    = barW(ssAmt);
  document.getElementById('sc-bar-med').style.width   = barW(medAmt);
  document.getElementById('sc-bar-401k').style.width  = barW(k401amt);
}

// ── Sync range <-> number inputs ──────────────────────────────────────────
function syncPair(rangeId, numberId, min, max) {
  var range  = document.getElementById(rangeId);
  var number = document.getElementById(numberId);
  range.addEventListener('input', function(){
    number.value = range.value;
    calculate();
  });
  number.addEventListener('input', function(){
    var v = Math.max(min, Math.min(max, parseFloat(this.value) || min));
    range.value = v;
    calculate();
  });
}
syncPair('sc-salary-range', 'sc-salary', 10000, 500000);
syncPair('sc-401k-range',   'sc-401k',   0,     100);

// ── Other selects / inputs ────────────────────────────────────────────────
['sc-filing', 'sc-freq', 'sc-state'].forEach(function(id){
  document.getElementById(id).addEventListener('change', function(){
    if (id === 'sc-state') {
      document.getElementById('sc-other-row').style.display =
        this.value === 'OTHER' ? 'block' : 'none';
    }
    calculate();
  });
});
document.getElementById('sc-pretax').addEventListener('input', calculate);
document.getElementById('sc-other-rate').addEventListener('input', calculate);

// ── Initial run ───────────────────────────────────────────────────────────
calculate();

})();
</script>
