---
title: "Tax Withholding Calculator - Estimate Paycheck Deductions"
description: "Calculate federal and state tax withholding from your paycheck. Estimate your take-home pay after taxes."
date: 2025-05-16
categories: ["Free Tools"]
slug: "tax-withholding-calculator"
ShowToc: false
cover:
  image: "/images/covers/tax-withholding-calculator.png"
---

<div id="tw-app">

<style>
#tw-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
}
#tw-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
  color: #1a1a2e;
}
#tw-app .tw-intro {
  background: #f0f4ff;
  border-left: 4px solid #4361ee;
  padding: 0.85rem 1.1rem;
  border-radius: 0 6px 6px 0;
  margin-bottom: 1.5rem;
  font-size: 0.92rem;
  color: #444;
}
#tw-app .tw-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1.5rem;
  margin-bottom: 1.2rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.04);
}
#tw-app .tw-row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}
#tw-app .tw-field {
  flex: 1;
  min-width: 200px;
}
#tw-app .tw-field label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #555;
  margin-bottom: 0.35rem;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}
#tw-app .tw-field input,
#tw-app .tw-field select {
  width: 100%;
  padding: 0.6rem 0.85rem;
  border: 1.5px solid #d1d5db;
  border-radius: 6px;
  font-size: 1rem;
  color: #1a1a2e;
  background: #fafafa;
  box-sizing: border-box;
  transition: border-color 0.2s;
  -webkit-appearance: none;
}
#tw-app .tw-field input:focus,
#tw-app .tw-field select:focus {
  outline: none;
  border-color: #4361ee;
  background: #fff;
}
#tw-app .tw-field .tw-hint {
  font-size: 0.76rem;
  color: #888;
  margin-top: 0.25rem;
}
#tw-app .tw-btn {
  display: block;
  width: 100%;
  padding: 0.85rem;
  background: #4361ee;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  letter-spacing: 0.02em;
}
#tw-app .tw-btn:hover {
  background: #3451d1;
  transform: translateY(-1px);
}
#tw-app .tw-btn:active {
  transform: translateY(0);
}
#tw-app .tw-results {
  display: none;
}
#tw-app .tw-results.visible {
  display: block;
}
#tw-app .tw-summary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 0.9rem;
  margin-bottom: 1.2rem;
}
#tw-app .tw-stat {
  background: #f8faff;
  border: 1px solid #dce5ff;
  border-radius: 8px;
  padding: 0.85rem 1rem;
  text-align: center;
}
#tw-app .tw-stat .tw-stat-label {
  font-size: 0.75rem;
  color: #666;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.3rem;
}
#tw-app .tw-stat .tw-stat-value {
  font-size: 1.35rem;
  font-weight: 800;
  color: #4361ee;
}
#tw-app .tw-stat.net .tw-stat-value {
  color: #2d8a4e;
}
#tw-app .tw-stat.deduct .tw-stat-value {
  color: #c0392b;
}
#tw-app .tw-breakdown table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.9rem;
}
#tw-app .tw-breakdown th {
  background: #f0f4ff;
  padding: 0.55rem 0.8rem;
  text-align: left;
  font-size: 0.78rem;
  font-weight: 700;
  color: #4361ee;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#tw-app .tw-breakdown td {
  padding: 0.55rem 0.8rem;
  border-bottom: 1px solid #f0f0f0;
  color: #333;
}
#tw-app .tw-breakdown tr:last-child td {
  border-bottom: none;
}
#tw-app .tw-breakdown tr.total-row td {
  font-weight: 700;
  background: #fffbeb;
  border-top: 2px solid #f0d060;
}
#tw-app .tw-breakdown tr.net-row td {
  font-weight: 800;
  background: #edfff4;
  color: #2d8a4e;
  border-top: 2px solid #6fcf97;
  font-size: 1rem;
}
#tw-app .tw-period-tabs {
  display: flex;
  gap: 0.4rem;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}
#tw-app .tw-period-tab {
  padding: 0.35rem 0.9rem;
  border: 1.5px solid #4361ee;
  border-radius: 20px;
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  background: #fff;
  color: #4361ee;
  transition: all 0.15s;
}
#tw-app .tw-period-tab.active,
#tw-app .tw-period-tab:hover {
  background: #4361ee;
  color: #fff;
}
#tw-app .tw-disclaimer {
  font-size: 0.77rem;
  color: #888;
  background: #fafafa;
  border: 1px solid #eee;
  border-radius: 6px;
  padding: 0.75rem 1rem;
  margin-top: 1rem;
}
#tw-app .tw-related {
  margin-top: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid #eee;
}
#tw-app .tw-related h3 {
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 0.6rem;
  color: #333;
}
#tw-app .tw-related ul {
  margin: 0;
  padding-left: 1.2rem;
}
#tw-app .tw-related li {
  margin-bottom: 0.3rem;
  font-size: 0.88rem;
}
#tw-app .tw-related a {
  color: #4361ee;
  text-decoration: none;
}
#tw-app .tw-related a:hover {
  text-decoration: underline;
}
@media (max-width: 480px) {
  #tw-app .tw-card { padding: 1rem; }
  #tw-app .tw-stat .tw-stat-value { font-size: 1.1rem; }
}
</style>

<div class="tw-intro">
Estimate your paycheck deductions in seconds. Enter your gross pay and filing details below to see federal income tax, FICA (Social Security + Medicare), and estimated state tax withheld — plus a full pay-period breakdown.
</div>

<div class="tw-card">
  <h2>Your Pay Information</h2>
  <div class="tw-row">
    <div class="tw-field">
      <label for="tw-gross">Gross Pay Amount</label>
      <input type="number" id="tw-gross" placeholder="e.g. 75000" min="0" step="0.01" />
      <div class="tw-hint">Enter the amount for the pay period selected below.</div>
    </div>
    <div class="tw-field">
      <label for="tw-period">Pay Period</label>
      <select id="tw-period">
        <option value="annual">Annual</option>
        <option value="monthly">Monthly</option>
        <option value="biweekly" selected>Biweekly (every 2 weeks)</option>
        <option value="weekly">Weekly</option>
      </select>
    </div>
  </div>
  <div class="tw-row">
    <div class="tw-field">
      <label for="tw-status">Filing Status</label>
      <select id="tw-status">
        <option value="single">Single</option>
        <option value="married">Married Filing Jointly</option>
        <option value="hoh">Head of Household</option>
      </select>
    </div>
    <div class="tw-field">
      <label for="tw-dependents">Dependents / Allowances</label>
      <input type="number" id="tw-dependents" value="0" min="0" max="20" step="1" />
      <div class="tw-hint">Each dependent reduces withholding (~$500/yr credit equivalent).</div>
    </div>
  </div>
  <div class="tw-row">
    <div class="tw-field">
      <label for="tw-extra">Additional Withholding ($/paycheck)</label>
      <input type="number" id="tw-extra" value="0" min="0" step="0.01" />
      <div class="tw-hint">Optional extra amount withheld each pay period.</div>
    </div>
    <div class="tw-field">
      <label for="tw-state">State</label>
      <select id="tw-state">
        <option value="0">No state income tax</option>
        <option value="0.0495">Illinois (~4.95%)</option>
        <option value="0.0525">Massachusetts (~5.25%)</option>
        <option value="0.055">Michigan (~5.5%)</option>
        <option value="0.06">Georgia / Virginia (~6%)</option>
        <option value="0.065">Wisconsin (~6.5%)</option>
        <option value="0.07">South Carolina (~7%)</option>
        <option value="0.0725">Maryland (~7.25%)</option>
        <option value="0.075">Minnesota / New Jersey (~7.5%)</option>
        <option value="0.08">Oregon / Vermont (~8%)</option>
        <option value="0.085">New York (~8.5%)</option>
        <option value="0.093">California (~9.3%)</option>
        <option value="custom">Custom rate...</option>
      </select>
    </div>
  </div>
  <div class="tw-row" id="tw-custom-state-row" style="display:none;">
    <div class="tw-field">
      <label for="tw-custom-rate">Custom State Tax Rate (%)</label>
      <input type="number" id="tw-custom-rate" value="5" min="0" max="20" step="0.01" />
    </div>
  </div>
  <button class="tw-btn" onclick="twCalculate()">Calculate My Withholding</button>
</div>

<div class="tw-card tw-results" id="tw-results">
  <h2>Results — <span id="tw-result-period-label">Per Paycheck</span></h2>
  <div class="tw-period-tabs">
    <button class="tw-period-tab active" onclick="twShowPeriod('paycheck', this)">Per Paycheck</button>
    <button class="tw-period-tab" onclick="twShowPeriod('monthly', this)">Monthly</button>
    <button class="tw-period-tab" onclick="twShowPeriod('annual', this)">Annual</button>
  </div>
  <div class="tw-summary-grid">
    <div class="tw-stat net">
      <div class="tw-stat-label">Net Pay (Take-Home)</div>
      <div class="tw-stat-value" id="tw-net-pay">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">Federal Income Tax</div>
      <div class="tw-stat-value" id="tw-fed-tax">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">Social Security</div>
      <div class="tw-stat-value" id="tw-ss">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">Medicare</div>
      <div class="tw-stat-value" id="tw-medicare">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">State Tax</div>
      <div class="tw-stat-value" id="tw-state-tax">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">Total Withheld</div>
      <div class="tw-stat-value" id="tw-total-withheld">--</div>
    </div>
  </div>

  <div class="tw-breakdown">
    <h2>Full Pay Period Breakdown</h2>
    <table>
      <thead>
        <tr>
          <th>Component</th>
          <th>Weekly</th>
          <th>Biweekly</th>
          <th>Monthly</th>
          <th>Annual</th>
        </tr>
      </thead>
      <tbody id="tw-table-body">
      </tbody>
    </table>
  </div>

  <div class="tw-disclaimer">
    <strong>Disclaimer:</strong> This calculator provides estimates based on 2025 federal tax brackets and simplified FICA rates. Actual withholding may differ based on W-4 elections, pre-tax deductions (401k, health insurance), local taxes, and other factors. Consult a tax professional for precise advice. State tax figures are flat-rate approximations only.
  </div>
</div>

<div class="tw-related">
  <h3>Related Free Tools</h3>
  <ul>
    <li><a href="/tools/salary-to-hourly-calculator/">Salary to Hourly Calculator</a></li>
    <li><a href="/tools/overtime-pay-calculator/">Overtime Pay Calculator</a></li>
    <li><a href="/tools/budget-calculator/">Monthly Budget Calculator</a></li>
    <li><a href="/tools/retirement-savings-calculator/">Retirement Savings Calculator</a></li>
  </ul>
</div>

<script>
(function() {
  // 2025 Federal income tax brackets (marginal rates)
  var BRACKETS = {
    single: [
      [11925, 0.10],
      [48475, 0.12],
      [103350, 0.22],
      [197300, 0.24],
      [250525, 0.32],
      [626350, 0.35],
      [Infinity, 0.37]
    ],
    married: [
      [23850, 0.10],
      [96950, 0.12],
      [206700, 0.22],
      [394600, 0.24],
      [501050, 0.32],
      [751600, 0.35],
      [Infinity, 0.37]
    ],
    hoh: [
      [17000, 0.10],
      [64850, 0.12],
      [103350, 0.22],
      [197300, 0.24],
      [250500, 0.32],
      [626350, 0.35],
      [Infinity, 0.37]
    ]
  };

  var STANDARD_DEDUCTION = {
    single: 15000,
    married: 30000,
    hoh: 22500
  };

  // SS wage base 2025
  var SS_WAGE_BASE = 176100;
  var SS_RATE = 0.062;
  var MEDICARE_RATE = 0.0145;
  var ADDITIONAL_MEDICARE_RATE = 0.009;
  var ADDITIONAL_MEDICARE_THRESHOLD = { single: 200000, married: 250000, hoh: 200000 };

  var twData = null;
  var twCurrentPeriodView = 'paycheck';

  document.getElementById('tw-state').addEventListener('change', function() {
    document.getElementById('tw-custom-state-row').style.display =
      this.value === 'custom' ? 'flex' : 'none';
  });

  function calcFederalTax(annualGross, status, dependents) {
    var depCredit = dependents * 500;
    var taxable = Math.max(0, annualGross - STANDARD_DEDUCTION[status] - depCredit);
    var brackets = BRACKETS[status];
    var tax = 0;
    var prev = 0;
    for (var i = 0; i < brackets.length; i++) {
      var limit = brackets[i][0];
      var rate = brackets[i][1];
      if (taxable <= prev) break;
      var chunk = Math.min(taxable, limit) - prev;
      tax += chunk * rate;
      prev = limit;
    }
    return Math.max(0, tax);
  }

  function fmt(n) {
    return '$' + n.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
  }

  function toAnnual(amount, period) {
    if (period === 'annual') return amount;
    if (period === 'monthly') return amount * 12;
    if (period === 'biweekly') return amount * 26;
    if (period === 'weekly') return amount * 52;
    return amount;
  }

  function fromAnnual(annualAmt, period) {
    if (period === 'annual') return annualAmt;
    if (period === 'monthly') return annualAmt / 12;
    if (period === 'biweekly') return annualAmt / 26;
    if (period === 'weekly') return annualAmt / 52;
    return annualAmt;
  }

  window.twCalculate = function() {
    var grossInput = parseFloat(document.getElementById('tw-gross').value) || 0;
    var period = document.getElementById('tw-period').value;
    var status = document.getElementById('tw-status').value;
    var dependents = parseInt(document.getElementById('tw-dependents').value) || 0;
    var extraPerPaycheck = parseFloat(document.getElementById('tw-extra').value) || 0;
    var stateEl = document.getElementById('tw-state');
    var stateRate = stateEl.value === 'custom'
      ? (parseFloat(document.getElementById('tw-custom-rate').value) || 0) / 100
      : parseFloat(stateEl.value) || 0;

    var annualGross = toAnnual(grossInput, period);

    // Federal income tax (annual)
    var annualFedTax = calcFederalTax(annualGross, status, dependents);

    // SS (capped at wage base)
    var ssTaxable = Math.min(annualGross, SS_WAGE_BASE);
    var annualSS = ssTaxable * SS_RATE;

    // Medicare (with additional Medicare tax)
    var annualMedicare = annualGross * MEDICARE_RATE;
    var threshold = ADDITIONAL_MEDICARE_THRESHOLD[status];
    if (annualGross > threshold) {
      annualMedicare += (annualGross - threshold) * ADDITIONAL_MEDICARE_RATE;
    }

    // State
    var annualStateTax = annualGross * stateRate;

    // Extra withholding (annualize from paycheck amount)
    var annualExtra = 0;
    if (period === 'biweekly') annualExtra = extraPerPaycheck * 26;
    else if (period === 'weekly') annualExtra = extraPerPaycheck * 52;
    else if (period === 'monthly') annualExtra = extraPerPaycheck * 12;
    else annualExtra = extraPerPaycheck; // if annual, treat as annual extra

    var annualTotal = annualFedTax + annualSS + annualMedicare + annualStateTax + annualExtra;
    var annualNet = annualGross - annualTotal;

    twData = {
      annualGross: annualGross,
      annualFedTax: annualFedTax,
      annualSS: annualSS,
      annualMedicare: annualMedicare,
      annualStateTax: annualStateTax,
      annualExtra: annualExtra,
      annualTotal: annualTotal,
      annualNet: annualNet,
      inputPeriod: period,
      extraPerPaycheck: extraPerPaycheck
    };

    twCurrentPeriodView = 'paycheck';
    document.querySelectorAll('#tw-app .tw-period-tab').forEach(function(t) { t.classList.remove('active'); });
    document.querySelectorAll('#tw-app .tw-period-tab')[0].classList.add('active');

    twRenderResults();

    var resultsEl = document.getElementById('tw-results');
    resultsEl.classList.add('visible');
    resultsEl.scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function getPaycheckDivisor(inputPeriod) {
    if (inputPeriod === 'weekly') return 52;
    if (inputPeriod === 'monthly') return 12;
    if (inputPeriod === 'annual') return 1;
    return 26; // biweekly default
  }

  window.twShowPeriod = function(viewPeriod, btn) {
    twCurrentPeriodView = viewPeriod;
    document.querySelectorAll('#tw-app .tw-period-tab').forEach(function(t) { t.classList.remove('active'); });
    btn.classList.add('active');
    twRenderResults();
  };

  function twRenderResults() {
    if (!twData) return;
    var d = twData;

    var divisors = { paycheck: getPaycheckDivisor(d.inputPeriod), monthly: 12, annual: 1 };
    var div = divisors[twCurrentPeriodView];
    var labels = { paycheck: 'Per Paycheck', monthly: 'Monthly', annual: 'Annual' };

    document.getElementById('tw-result-period-label').textContent = labels[twCurrentPeriodView];

    document.getElementById('tw-net-pay').textContent = fmt(d.annualNet / div);
    document.getElementById('tw-fed-tax').textContent = fmt(d.annualFedTax / div);
    document.getElementById('tw-ss').textContent = fmt(d.annualSS / div);
    document.getElementById('tw-medicare').textContent = fmt(d.annualMedicare / div);
    document.getElementById('tw-state-tax').textContent = fmt(d.annualStateTax / div);
    document.getElementById('tw-total-withheld').textContent = fmt(d.annualTotal / div);

    // Build breakdown table
    var rows = [
      ['Gross Pay', d.annualGross],
      ['Federal Income Tax', d.annualFedTax],
      ['Social Security (6.2%)', d.annualSS],
      ['Medicare (1.45%+)', d.annualMedicare],
      ['State Income Tax', d.annualStateTax],
    ];
    if (d.annualExtra > 0) rows.push(['Additional Withholding', d.annualExtra]);
    rows.push(null); // separator → total
    rows.push(['_total', d.annualTotal]);
    rows.push(['_net', d.annualNet]);

    var tbody = document.getElementById('tw-table-body');
    tbody.innerHTML = '';
    rows.forEach(function(row) {
      if (!row) return;
      var tr = document.createElement('tr');
      var isTotal = row[0] === '_total';
      var isNet = row[0] === '_net';
      if (isTotal) tr.className = 'total-row';
      if (isNet) tr.className = 'net-row';
      var label = isTotal ? 'Total Withheld' : isNet ? 'Net Take-Home Pay' : row[0];
      var annual = row[1];
      tr.innerHTML =
        '<td>' + label + '</td>' +
        '<td>' + fmt(annual / 52) + '</td>' +
        '<td>' + fmt(annual / 26) + '</td>' +
        '<td>' + fmt(annual / 12) + '</td>' +
        '<td>' + fmt(annual) + '</td>';
      tbody.appendChild(tr);
    });
  }
})();
</script>

</div>

---

## Related Tools

> [Freelance Rate Calculator](/tools/freelance-rate-calculator/)
> [Hourly To Salary Calculator](/tools/hourly-to-salary-calculator/)
> [Pension Simulator](/tools/pension-simulator/)

