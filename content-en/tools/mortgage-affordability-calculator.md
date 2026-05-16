---
title: "Mortgage Affordability Calculator - How Much House Can You Afford?"
date: 2025-05-16
categories: ["Free Tools"]
slug: "mortgage-affordability-calculator"
ShowToc: false
cover:
  image: "/images/covers/mortgage-affordability-calculator.png"
---

<div id="ma-app">

<style>
#ma-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a202c;
  line-height: 1.6;
}
#ma-app h2 {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0 0 1.25rem 0;
  color: #1a202c;
}
#ma-app h3 {
  font-size: 1.1rem;
  font-weight: 600;
  margin: 0 0 1rem 0;
  color: #2d3748;
}
#ma-app .ma-intro {
  background: #f0f7ff;
  border-left: 4px solid #3182ce;
  padding: 1rem 1.25rem;
  border-radius: 0 8px 8px 0;
  margin-bottom: 2rem;
  font-size: 0.95rem;
  color: #2c5282;
}
#ma-app .ma-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.75rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ma-app .ma-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
}
@media (max-width: 600px) {
  #ma-app .ma-grid { grid-template-columns: 1fr; }
}
#ma-app .ma-field {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
#ma-app .ma-field label {
  font-size: 0.85rem;
  font-weight: 600;
  color: #4a5568;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#ma-app .ma-field .ma-hint {
  font-size: 0.78rem;
  color: #718096;
  margin-top: -0.2rem;
}
#ma-app .ma-input-wrap {
  position: relative;
  display: flex;
  align-items: center;
}
#ma-app .ma-input-wrap .ma-prefix,
#ma-app .ma-input-wrap .ma-suffix {
  position: absolute;
  color: #718096;
  font-size: 0.95rem;
  font-weight: 500;
  pointer-events: none;
}
#ma-app .ma-input-wrap .ma-prefix { left: 0.75rem; }
#ma-app .ma-input-wrap .ma-suffix { right: 0.75rem; }
#ma-app .ma-input-wrap input,
#ma-app .ma-input-wrap select {
  width: 100%;
  border: 1.5px solid #cbd5e0;
  border-radius: 8px;
  padding: 0.6rem 0.85rem;
  font-size: 1rem;
  background: #fff;
  color: #1a202c;
  outline: none;
  transition: border-color 0.2s;
  box-sizing: border-box;
}
#ma-app .ma-input-wrap input:focus,
#ma-app .ma-input-wrap select:focus {
  border-color: #3182ce;
  box-shadow: 0 0 0 3px rgba(49,130,206,0.15);
}
#ma-app .ma-input-wrap.has-prefix input { padding-left: 1.8rem; }
#ma-app .ma-input-wrap.has-suffix input { padding-right: 2.2rem; }
#ma-app .ma-dti-row {
  display: flex;
  gap: 1rem;
  margin-top: 0.5rem;
}
#ma-app .ma-dti-chip {
  flex: 1;
  background: #ebf8ff;
  border: 1px solid #bee3f8;
  border-radius: 8px;
  padding: 0.6rem 0.9rem;
  text-align: center;
}
#ma-app .ma-dti-chip .ma-dti-label {
  font-size: 0.75rem;
  color: #2b6cb0;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#ma-app .ma-dti-chip .ma-dti-val {
  font-size: 1.2rem;
  font-weight: 700;
  color: #2c5282;
}
#ma-app .ma-dti-chip.warn .ma-dti-val { color: #c05621; }
#ma-app .ma-dti-chip.danger .ma-dti-val { color: #c53030; }
#ma-app .ma-btn {
  display: block;
  width: 100%;
  padding: 0.85rem 1.5rem;
  background: linear-gradient(135deg, #3182ce, #2b6cb0);
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.1s;
  letter-spacing: 0.02em;
}
#ma-app .ma-btn:hover { opacity: 0.92; transform: translateY(-1px); }
#ma-app .ma-btn:active { transform: translateY(0); }
#ma-app .ma-results {
  display: none;
}
#ma-app .ma-results.visible {
  display: block;
}
#ma-app .ma-result-hero {
  background: linear-gradient(135deg, #2b6cb0, #2c5282);
  border-radius: 12px;
  padding: 2rem;
  text-align: center;
  color: #fff;
  margin-bottom: 1.5rem;
}
#ma-app .ma-result-hero .ma-hero-label {
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  opacity: 0.85;
  margin-bottom: 0.4rem;
}
#ma-app .ma-result-hero .ma-hero-price {
  font-size: 2.8rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 0.75rem;
}
#ma-app .ma-result-hero .ma-hero-sub {
  font-size: 1rem;
  opacity: 0.9;
}
#ma-app .ma-stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-bottom: 1.5rem;
}
@media (max-width: 600px) {
  #ma-app .ma-stats-grid { grid-template-columns: 1fr 1fr; }
}
#ma-app .ma-stat {
  background: #f7fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
#ma-app .ma-stat .ma-stat-label {
  font-size: 0.75rem;
  color: #718096;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.3rem;
}
#ma-app .ma-stat .ma-stat-value {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2d3748;
}
#ma-app .ma-stat .ma-stat-value.green { color: #276749; }
#ma-app .ma-stat .ma-stat-value.orange { color: #c05621; }
#ma-app .ma-chart-wrap {
  display: flex;
  gap: 2rem;
  align-items: center;
  flex-wrap: wrap;
}
#ma-app canvas#ma-pie {
  width: 180px !important;
  height: 180px !important;
  flex-shrink: 0;
}
#ma-app .ma-legend {
  flex: 1;
  min-width: 180px;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
#ma-app .ma-legend-item {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  font-size: 0.9rem;
}
#ma-app .ma-legend-dot {
  width: 14px;
  height: 14px;
  border-radius: 3px;
  flex-shrink: 0;
}
#ma-app .ma-legend-name { color: #4a5568; flex: 1; }
#ma-app .ma-legend-amt { font-weight: 700; color: #2d3748; }
#ma-app .ma-alert {
  border-radius: 8px;
  padding: 0.85rem 1.1rem;
  font-size: 0.88rem;
  margin-top: 1rem;
  display: flex;
  align-items: flex-start;
  gap: 0.6rem;
}
#ma-app .ma-alert.success { background: #f0fff4; border: 1px solid #9ae6b4; color: #276749; }
#ma-app .ma-alert.warn { background: #fffbeb; border: 1px solid #fbd38d; color: #744210; }
#ma-app .ma-alert.danger { background: #fff5f5; border: 1px solid #feb2b2; color: #742a2a; }
#ma-app .ma-related {
  background: #f7fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.5rem;
  margin-top: 2rem;
}
#ma-app .ma-related h3 { margin-bottom: 0.75rem; }
#ma-app .ma-related ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
#ma-app .ma-related ul li a {
  color: #3182ce;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
}
#ma-app .ma-related ul li a:hover { text-decoration: underline; }
#ma-app .ma-disclaimer {
  font-size: 0.78rem;
  color: #a0aec0;
  margin-top: 1.5rem;
  text-align: center;
  line-height: 1.5;
}
</style>

<div class="ma-intro">
  Enter your financial details below to instantly find out the maximum home price you can afford, based on standard DTI (Debt-to-Income) lending guidelines used by most U.S. lenders.
</div>

<div class="ma-card">
  <h2>Your Financial Information</h2>
  <div class="ma-grid">
    <div class="ma-field">
      <label>Annual Gross Income</label>
      <span class="ma-hint">Before taxes, all sources</span>
      <div class="ma-input-wrap has-prefix">
        <span class="ma-prefix">$</span>
        <input type="number" id="ma-income" value="90000" min="0" step="1000" />
      </div>
    </div>
    <div class="ma-field">
      <label>Total Monthly Debts</label>
      <span class="ma-hint">Car, student loans, credit cards</span>
      <div class="ma-input-wrap has-prefix">
        <span class="ma-prefix">$</span>
        <input type="number" id="ma-debts" value="500" min="0" step="50" />
      </div>
    </div>
    <div class="ma-field">
      <label>Down Payment</label>
      <span class="ma-hint">Dollar amount</span>
      <div class="ma-input-wrap has-prefix">
        <span class="ma-prefix">$</span>
        <input type="number" id="ma-downpayment" value="60000" min="0" step="1000" />
      </div>
    </div>
    <div class="ma-field">
      <label>Down Payment %</label>
      <span class="ma-hint">Auto-syncs with amount above</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-downpct" value="" min="0" max="100" step="0.5" placeholder="e.g. 20" />
        <span class="ma-suffix">%</span>
      </div>
    </div>
    <div class="ma-field">
      <label>Annual Interest Rate</label>
      <span class="ma-hint">Current 30-yr avg ~6.8%</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-rate" value="6.8" min="0.1" max="20" step="0.05" />
        <span class="ma-suffix">%</span>
      </div>
    </div>
    <div class="ma-field">
      <label>Loan Term</label>
      <span class="ma-hint">Years</span>
      <div class="ma-input-wrap">
        <select id="ma-term">
          <option value="15">15 years</option>
          <option value="20">20 years</option>
          <option value="25">25 years</option>
          <option value="30" selected>30 years</option>
        </select>
      </div>
    </div>
    <div class="ma-field">
      <label>Annual Property Tax Rate</label>
      <span class="ma-hint">U.S. avg ~1.1%</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-tax" value="1.1" min="0" max="5" step="0.05" />
        <span class="ma-suffix">%</span>
      </div>
    </div>
    <div class="ma-field">
      <label>Monthly Home Insurance</label>
      <span class="ma-hint">Typical $100–$200/mo</span>
      <div class="ma-input-wrap has-prefix">
        <span class="ma-prefix">$</span>
        <input type="number" id="ma-insurance" value="150" min="0" step="10" />
      </div>
    </div>
  </div>

  <div style="margin-top:1.25rem;">
    <div style="font-size:0.85rem;font-weight:600;color:#4a5568;text-transform:uppercase;letter-spacing:0.04em;margin-bottom:0.5rem;">DTI Limit Guidelines</div>
    <div class="ma-dti-row">
      <div class="ma-dti-chip" id="ma-frontend-chip">
        <div class="ma-dti-label">Front-End DTI (Housing)</div>
        <div class="ma-dti-val" id="ma-frontend-val">—</div>
        <div style="font-size:0.72rem;color:#4a5568;">Limit: 28%</div>
      </div>
      <div class="ma-dti-chip" id="ma-backend-chip">
        <div class="ma-dti-label">Back-End DTI (All Debts)</div>
        <div class="ma-dti-val" id="ma-backend-val">—</div>
        <div style="font-size:0.72rem;color:#4a5568;">Limit: 36%</div>
      </div>
    </div>
  </div>

  <button class="ma-btn" id="ma-calc-btn" style="margin-top:1.5rem;" onclick="maCalculate()">
    Calculate My Affordability
  </button>
</div>

<div class="ma-results" id="ma-results">
  <div class="ma-result-hero">
    <div class="ma-hero-label">Maximum Home Price You Can Afford</div>
    <div class="ma-hero-price" id="ma-max-price">$0</div>
    <div class="ma-hero-sub" id="ma-hero-sub">Based on DTI lending guidelines</div>
  </div>

  <div class="ma-stats-grid">
    <div class="ma-stat">
      <div class="ma-stat-label">Max Monthly Payment</div>
      <div class="ma-stat-value" id="ma-max-payment">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">Loan Amount</div>
      <div class="ma-stat-value" id="ma-loan-amt">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">Down Payment</div>
      <div class="ma-stat-value green" id="ma-dp-display">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">Total Interest Paid</div>
      <div class="ma-stat-value orange" id="ma-total-interest">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">Total Cost of Loan</div>
      <div class="ma-stat-value" id="ma-total-cost">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">Interest Rate</div>
      <div class="ma-stat-value" id="ma-rate-display">—</div>
    </div>
  </div>

  <div class="ma-card">
    <h3>Monthly Payment Breakdown</h3>
    <div class="ma-chart-wrap">
      <canvas id="ma-pie" width="180" height="180"></canvas>
      <div class="ma-legend" id="ma-legend"></div>
    </div>
    <div id="ma-dti-alert" class="ma-alert" style="display:none;"></div>
  </div>

  <div class="ma-related">
    <h3>Related Free Tools</h3>
    <ul>
      <li><a href="/tools/compound-interest-calculator/">Compound Interest Calculator</a></li>
      <li><a href="/tools/budget-calculator/">Monthly Budget Calculator</a></li>
      <li><a href="/tools/net-worth-calculator/">Net Worth Calculator</a></li>
      <li><a href="/tools/savings-goal-calculator/">Savings Goal Calculator</a></li>
      <li><a href="/tools/loan-payoff-calculator/">Loan Payoff Calculator</a></li>
    </ul>
  </div>
</div>

<p class="ma-disclaimer">
  This calculator is for educational purposes only and does not constitute financial advice.<br>
  Actual loan approval depends on credit score, lender criteria, and other factors. Consult a licensed mortgage professional.
</p>

<script>
(function() {
  var COLORS = ['#3182ce', '#f6ad55', '#68d391', '#fc8181'];
  var pieChart = null;

  function fmt(n) {
    return '$' + Math.round(n).toLocaleString('en-US');
  }
  function fmtPct(n) {
    return n.toFixed(1) + '%';
  }

  // Sync down payment amount <-> percentage
  var incomeEl = document.getElementById('ma-income');
  var dpAmtEl = document.getElementById('ma-downpayment');
  var dpPctEl = document.getElementById('ma-downpct');
  var lastEdited = 'amt';

  dpAmtEl.addEventListener('input', function() {
    lastEdited = 'amt';
    dpPctEl.value = '';
  });
  dpPctEl.addEventListener('input', function() {
    lastEdited = 'pct';
    dpAmtEl.value = '';
  });

  window.maCalculate = function() {
    var income = parseFloat(document.getElementById('ma-income').value) || 0;
    var debts = parseFloat(document.getElementById('ma-debts').value) || 0;
    var rate = parseFloat(document.getElementById('ma-rate').value) / 100 / 12;
    var term = parseInt(document.getElementById('ma-term').value) * 12;
    var taxRate = parseFloat(document.getElementById('ma-tax').value) / 100;
    var insurance = parseFloat(document.getElementById('ma-insurance').value) || 0;

    var monthlyIncome = income / 12;

    // Front-end limit: 28% of gross monthly income (PITI)
    var maxPITI = monthlyIncome * 0.28;
    // Back-end limit: 36% of gross monthly income minus existing debts
    var maxPITIBackend = monthlyIncome * 0.36 - debts;
    // Use the more restrictive
    var maxHousingPayment = Math.min(maxPITI, maxPITIBackend);

    // Determine down payment
    var dpAmt = parseFloat(dpAmtEl.value) || 0;
    var dpPct = parseFloat(dpPctEl.value);

    // We iterate: home price -> dp -> loan -> PI payment
    // Max PI = maxHousingPayment - tax&ins (tax depends on home price)
    // tax per month = homePrice * taxRate / 12
    // So: PI = maxHousingPayment - homePrice*taxRate/12 - insurance
    // PI = PMT(rate, term, loanAmt)
    // loanAmt = homePrice - dpAmt (if amt) or homePrice*(1 - dpPct/100) (if pct)

    var maxHomePrice;
    var usePct = (dpPctEl.value !== '' && lastEdited === 'pct');

    if (rate === 0) {
      // Edge case: 0% interest
      if (usePct) {
        var ltvFrac = 1 - dpPct / 100;
        // PI = loan/term, loan = price*ltvFrac
        // price*ltvFrac/term + price*taxRate/12 + insurance = maxHousing
        maxHomePrice = (maxHousingPayment - insurance) / (ltvFrac / term + taxRate / 12);
      } else {
        // loan = price - dpAmt
        // (price-dpAmt)/term + price*taxRate/12 + insurance = maxHousing
        maxHomePrice = (maxHousingPayment - insurance + dpAmt / term) / (1 / term + taxRate / 12);
      }
    } else {
      // Monthly PI factor per dollar of loan: rate*(1+rate)^n / ((1+rate)^n - 1)
      var piFactor = rate * Math.pow(1 + rate, term) / (Math.pow(1 + rate, term) - 1);

      if (usePct) {
        var ltvFrac = 1 - dpPct / 100;
        // PI = price * ltvFrac * piFactor
        // tax = price * taxRate / 12
        // price*(ltvFrac*piFactor + taxRate/12) + insurance = maxHousing
        maxHomePrice = (maxHousingPayment - insurance) / (ltvFrac * piFactor + taxRate / 12);
        dpAmt = maxHomePrice * dpPct / 100;
      } else {
        // PI = (price - dpAmt) * piFactor
        // tax = price * taxRate / 12
        // price*piFactor - dpAmt*piFactor + price*taxRate/12 + insurance = maxHousing
        // price*(piFactor + taxRate/12) = maxHousing - insurance + dpAmt*piFactor
        maxHomePrice = (maxHousingPayment - insurance + dpAmt * piFactor) / (piFactor + taxRate / 12);
      }
    }

    if (maxHomePrice < 0) maxHomePrice = 0;

    var loanAmt = Math.max(0, maxHomePrice - dpAmt);
    var monthlyPI, totalPaid, totalInterest;

    if (rate === 0) {
      monthlyPI = loanAmt / term;
      totalPaid = loanAmt;
      totalInterest = 0;
    } else {
      monthlyPI = loanAmt * rate * Math.pow(1 + rate, term) / (Math.pow(1 + rate, term) - 1);
      totalPaid = monthlyPI * term;
      totalInterest = totalPaid - loanAmt;
    }

    var monthlyTax = maxHomePrice * taxRate / 12;
    var totalMonthly = monthlyPI + monthlyTax + insurance;

    // Actual DTI
    var frontEndDTI = (totalMonthly / monthlyIncome) * 100;
    var backEndDTI = ((totalMonthly + debts) / monthlyIncome) * 100;

    // Update hero
    document.getElementById('ma-max-price').textContent = fmt(maxHomePrice);
    document.getElementById('ma-hero-sub').textContent =
      'With ' + fmt(dpAmt) + ' down · ' + document.getElementById('ma-term').value + '-year term at ' +
      document.getElementById('ma-rate').value + '%';

    // Stats
    document.getElementById('ma-max-payment').textContent = fmt(totalMonthly) + '/mo';
    document.getElementById('ma-loan-amt').textContent = fmt(loanAmt);
    document.getElementById('ma-dp-display').textContent = fmt(dpAmt);
    document.getElementById('ma-total-interest').textContent = fmt(totalInterest);
    document.getElementById('ma-total-cost').textContent = fmt(totalPaid + dpAmt);
    document.getElementById('ma-rate-display').textContent = document.getElementById('ma-rate').value + '%';

    // DTI chips
    updateDTIChip('ma-frontend-chip', 'ma-frontend-val', frontEndDTI, 28);
    updateDTIChip('ma-backend-chip', 'ma-backend-val', backEndDTI, 36);

    // Pie chart
    var breakdown = [
      { label: 'Principal & Interest', value: monthlyPI, color: COLORS[0] },
      { label: 'Property Tax', value: monthlyTax, color: COLORS[1] },
      { label: 'Home Insurance', value: insurance, color: COLORS[2] },
    ];
    drawPie(breakdown, totalMonthly);

    // Alert
    var alertEl = document.getElementById('ma-dti-alert');
    if (maxHomePrice <= 0) {
      alertEl.style.display = 'flex';
      alertEl.className = 'ma-alert danger';
      alertEl.innerHTML = '<strong>&#9888; Your current debts exceed the DTI limit.</strong> Consider paying down existing debts or increasing income before applying for a mortgage.';
    } else if (backEndDTI > 36 || frontEndDTI > 28) {
      alertEl.style.display = 'flex';
      alertEl.className = 'ma-alert warn';
      alertEl.innerHTML = '<strong>&#9888; DTI is near or above limits.</strong> Some lenders may require a larger down payment or lower loan amount.';
    } else {
      alertEl.style.display = 'flex';
      alertEl.className = 'ma-alert success';
      alertEl.innerHTML = '<strong>&#10003; You are within standard DTI guidelines.</strong> Most conventional lenders should be able to approve a loan at this price point.';
    }

    document.getElementById('ma-results').classList.add('visible');
    document.getElementById('ma-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function updateDTIChip(chipId, valId, val, limit) {
    var chip = document.getElementById(chipId);
    var valEl = document.getElementById(valId);
    valEl.textContent = fmtPct(val);
    chip.className = 'ma-dti-chip';
    if (val > limit) chip.classList.add('danger');
    else if (val > limit * 0.9) chip.classList.add('warn');
  }

  function drawPie(data, total) {
    var canvas = document.getElementById('ma-pie');
    var ctx = canvas.getContext('2d');
    var dpr = window.devicePixelRatio || 1;
    canvas.width = 180 * dpr;
    canvas.height = 180 * dpr;
    canvas.style.width = '180px';
    canvas.style.height = '180px';
    ctx.scale(dpr, dpr);

    var cx = 90, cy = 90, r = 80;
    ctx.clearRect(0, 0, 180, 180);

    var start = -Math.PI / 2;
    data.forEach(function(seg) {
      var slice = (seg.value / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, start, start + slice);
      ctx.closePath();
      ctx.fillStyle = seg.color;
      ctx.fill();
      start += slice;
    });

    // Donut hole
    ctx.beginPath();
    ctx.arc(cx, cy, r * 0.52, 0, 2 * Math.PI);
    ctx.fillStyle = '#fff';
    ctx.fill();

    // Center text
    ctx.fillStyle = '#2d3748';
    ctx.font = 'bold 13px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText('Total/mo', cx, cy - 10);
    ctx.font = 'bold 15px sans-serif';
    ctx.fillStyle = '#2b6cb0';
    ctx.fillText(fmt(total), cx, cy + 10);

    // Legend
    var legendEl = document.getElementById('ma-legend');
    legendEl.innerHTML = '';
    data.forEach(function(seg) {
      var pct = total > 0 ? ((seg.value / total) * 100).toFixed(1) : '0.0';
      legendEl.innerHTML +=
        '<div class="ma-legend-item">' +
        '<div class="ma-legend-dot" style="background:' + seg.color + ';"></div>' +
        '<span class="ma-legend-name">' + seg.label + '<br><span style="font-size:0.75rem;color:#a0aec0;">' + pct + '%</span></span>' +
        '<span class="ma-legend-amt">' + fmt(seg.value) + '</span>' +
        '</div>';
    });
  }

  // Trigger on Enter key
  document.addEventListener('keydown', function(e) {
    if (e.key === 'Enter' && document.activeElement && document.activeElement.closest && document.activeElement.closest('#ma-app')) {
      maCalculate();
    }
  });
})();
</script>

</div>
