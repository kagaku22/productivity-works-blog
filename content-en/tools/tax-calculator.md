---
title: "Income Tax Calculator - Tax Bracket Estimator"
date: 2025-05-16
description: "Free income tax calculator. Estimate your federal income tax based on filing status and taxable income. See your effective tax rate, marginal rate, and tax bracket breakdown."
categories: ["Free Tools"]
slug: "tax-calculator"
ShowToc: false
aliases:
  - "/tools/tax-calculator/"
cover:
  image: "/images/covers/tax-calculator.png"
  alt: "Income Tax Calculator"
---

<div id="tc-app">
<style>
#tc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}
#tc-app * { box-sizing: border-box; }
#tc-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1.2rem;
  color: #1a1a2e;
  border-left: 4px solid #22c55e;
  padding-left: 0.7rem;
}
#tc-app .tc-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.6rem;
  margin-bottom: 1.4rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
#tc-app .tc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
  margin-bottom: 1rem;
}
#tc-app label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #4a5568;
  margin-bottom: 0.35rem;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#tc-app input[type=number], #tc-app select {
  width: 100%;
  padding: 0.6rem 0.9rem;
  border: 1.5px solid #cbd5e0;
  border-radius: 8px;
  font-size: 1rem;
  color: #1a1a2e;
  background: #f8fafc;
  transition: border-color 0.2s;
  outline: none;
}
#tc-app input[type=number]:focus, #tc-app select:focus {
  border-color: #22c55e;
  background: #fff;
}
#tc-app .tc-checkbox-row {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: 0.2rem;
}
#tc-app .tc-checkbox-row input[type=checkbox] {
  width: 18px;
  height: 18px;
  accent-color: #22c55e;
  cursor: pointer;
}
#tc-app .tc-checkbox-row label {
  font-size: 0.9rem;
  text-transform: none;
  letter-spacing: 0;
  cursor: pointer;
  margin: 0;
  color: #2d3748;
}
#tc-app .tc-btn {
  display: inline-block;
  padding: 0.7rem 2rem;
  background: linear-gradient(135deg, #22c55e, #16a34a);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  margin-top: 0.5rem;
  transition: opacity 0.2s;
}
#tc-app .tc-btn:hover { opacity: 0.88; }
#tc-app .tc-results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1rem;
  margin-bottom: 1.4rem;
}
#tc-app .tc-stat {
  background: #f0fdf4;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  text-align: center;
}
#tc-app .tc-stat .tc-stat-label {
  font-size: 0.75rem;
  font-weight: 600;
  color: #16a34a;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.3rem;
}
#tc-app .tc-stat .tc-stat-value {
  font-size: 1.35rem;
  font-weight: 800;
  color: #1a1a2e;
}
#tc-app .tc-stat.tc-highlight {
  background: linear-gradient(135deg, #dcfce7, #bbf7d0);
  border: 1.5px solid #22c55e;
}
#tc-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#tc-app thead th {
  background: #f0fdf4;
  color: #16a34a;
  font-weight: 700;
  padding: 0.6rem 0.9rem;
  text-align: right;
  border-bottom: 2px solid #e2e8f0;
}
#tc-app thead th:first-child { text-align: left; }
#tc-app tbody td {
  padding: 0.5rem 0.9rem;
  text-align: right;
  border-bottom: 1px solid #f0f0f0;
  color: #2d3748;
}
#tc-app tbody td:first-child { text-align: left; }
#tc-app tbody tr:hover { background: #f0fdf4; }
#tc-app tbody tr.tc-active-row {
  background: #dcfce7;
  font-weight: 600;
}
#tc-app .tc-bar-wrap {
  background: #f0f0f0;
  border-radius: 4px;
  height: 10px;
  display: inline-block;
  width: 60px;
  vertical-align: middle;
  margin-left: 6px;
  overflow: hidden;
}
#tc-app .tc-bar-fill {
  height: 100%;
  border-radius: 4px;
  background: linear-gradient(90deg, #22c55e, #16a34a);
}
#tc-app .tc-hidden { display: none; }
#tc-app .tc-note {
  font-size: 0.78rem;
  color: #888;
  margin-top: 1rem;
  line-height: 1.6;
}
#tc-app .tc-deduction-note {
  font-size: 0.82rem;
  color: #667;
  margin-top: 0.5rem;
  padding: 0.5rem 0.8rem;
  background: #f8fafc;
  border-radius: 6px;
  border-left: 3px solid #22c55e;
}
#tc-app canvas { display: block; margin: 0 auto 1rem; }
</style>

<div class="tc-card">
  <h2>Income Details</h2>
  <div class="tc-grid">
    <div>
      <label for="tc-income">Gross Annual Income ($)</label>
      <input type="number" id="tc-income" value="75000" min="0" step="1000">
    </div>
    <div>
      <label for="tc-status">Filing Status</label>
      <select id="tc-status" onchange="tcUpdateDeduction()">
        <option value="single">Single</option>
        <option value="mfj">Married Filing Jointly</option>
        <option value="hoh">Head of Household</option>
      </select>
    </div>
  </div>
  <div class="tc-checkbox-row">
    <input type="checkbox" id="tc-std-ded" checked onchange="tcUpdateDeduction()">
    <label for="tc-std-ded">Apply Standard Deduction</label>
  </div>
  <div class="tc-deduction-note" id="tc-ded-note">2024 Standard Deduction: $14,600 (Single)</div>
  <br>
  <button class="tc-btn" onclick="tcCalculate()">Calculate Tax</button>
</div>

<div class="tc-card tc-hidden" id="tc-results">
  <h2>Tax Summary</h2>
  <div class="tc-results-grid">
    <div class="tc-stat">
      <div class="tc-stat-label">Gross Income</div>
      <div class="tc-stat-value" id="tc-gross-out">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">Deduction</div>
      <div class="tc-stat-value" id="tc-ded-out">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">Taxable Income</div>
      <div class="tc-stat-value" id="tc-taxable-out">—</div>
    </div>
    <div class="tc-stat tc-highlight">
      <div class="tc-stat-label">Total Federal Tax</div>
      <div class="tc-stat-value" id="tc-tax-out">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">Effective Rate</div>
      <div class="tc-stat-value" id="tc-eff-out">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">Marginal Rate</div>
      <div class="tc-stat-value" id="tc-marginal-out">—</div>
    </div>
  </div>

  <canvas id="tc-chart" width="700" height="200"></canvas>
</div>

<div class="tc-card tc-hidden" id="tc-bracket-card">
  <h2>Tax Bracket Breakdown</h2>
  <div style="overflow-x:auto">
    <table>
      <thead>
        <tr>
          <th>Bracket</th>
          <th>Rate</th>
          <th>Income in Bracket</th>
          <th>Tax in Bracket</th>
          <th></th>
        </tr>
      </thead>
      <tbody id="tc-bracket-body"></tbody>
    </table>
  </div>
  <p class="tc-note">* 2024 US federal income tax brackets. State taxes, FICA (Social Security & Medicare), AMT, and tax credits are not included. For general estimation only — consult a tax professional for your specific situation.</p>
</div>

<script>
(function(){
  var TC_BRACKETS = {
    single: [
      { rate: 0.10, min: 0,       max: 11600 },
      { rate: 0.12, min: 11600,   max: 47150 },
      { rate: 0.22, min: 47150,   max: 100525 },
      { rate: 0.24, min: 100525,  max: 191950 },
      { rate: 0.32, min: 191950,  max: 243725 },
      { rate: 0.35, min: 243725,  max: 609350 },
      { rate: 0.37, min: 609350,  max: Infinity }
    ],
    mfj: [
      { rate: 0.10, min: 0,       max: 23200 },
      { rate: 0.12, min: 23200,   max: 94300 },
      { rate: 0.22, min: 94300,   max: 201050 },
      { rate: 0.24, min: 201050,  max: 383900 },
      { rate: 0.32, min: 383900,  max: 487450 },
      { rate: 0.35, min: 487450,  max: 731200 },
      { rate: 0.37, min: 731200,  max: Infinity }
    ],
    hoh: [
      { rate: 0.10, min: 0,       max: 16550 },
      { rate: 0.12, min: 16550,   max: 63100 },
      { rate: 0.22, min: 63100,   max: 100500 },
      { rate: 0.24, min: 100500,  max: 191950 },
      { rate: 0.32, min: 191950,  max: 243700 },
      { rate: 0.35, min: 243700,  max: 609350 },
      { rate: 0.37, min: 609350,  max: Infinity }
    ]
  };

  var STD_DED = { single: 14600, mfj: 29200, hoh: 21900 };
  var STD_LABEL = { single: 'Single', mfj: 'Married Filing Jointly', hoh: 'Head of Household' };

  var BRACKET_COLORS = ['#dcfce7','#bbf7d0','#86efac','#4ade80','#22c55e','#16a34a','#15803d'];

  window.tcUpdateDeduction = function() {
    var status = document.getElementById('tc-status').value;
    var useStd = document.getElementById('tc-std-ded').checked;
    var ded = STD_DED[status];
    var note = document.getElementById('tc-ded-note');
    if (useStd) {
      note.textContent = '2024 Standard Deduction: $' + ded.toLocaleString() + ' (' + STD_LABEL[status] + ')';
      note.style.display = 'block';
    } else {
      note.textContent = 'No deduction applied. Enter your itemized deductions separately.';
      note.style.display = 'block';
    }
  };

  function fmt(n) {
    return '$' + Math.round(n).toLocaleString('en-US');
  }

  window.tcCalculate = function() {
    var gross = parseFloat(document.getElementById('tc-income').value) || 0;
    var status = document.getElementById('tc-status').value;
    var useStd = document.getElementById('tc-std-ded').checked;

    var ded = useStd ? STD_DED[status] : 0;
    var taxable = Math.max(0, gross - ded);
    var brackets = TC_BRACKETS[status];

    var totalTax = 0;
    var breakdown = [];
    var marginal = 0.10;

    brackets.forEach(function(b, i) {
      if (taxable <= b.min) {
        breakdown.push({ rate: b.rate, label: formatBracketLabel(b, i, brackets), income: 0, tax: 0, active: false });
        return;
      }
      var incomeInBracket = Math.min(taxable, b.max === Infinity ? taxable : b.max) - b.min;
      if (incomeInBracket < 0) incomeInBracket = 0;
      var taxInBracket = incomeInBracket * b.rate;
      if (incomeInBracket > 0) marginal = b.rate;
      totalTax += taxInBracket;
      breakdown.push({ rate: b.rate, label: formatBracketLabel(b, i, brackets), income: incomeInBracket, tax: taxInBracket, active: incomeInBracket > 0 });
    });

    var effectiveRate = gross > 0 ? (totalTax / gross * 100) : 0;

    document.getElementById('tc-gross-out').textContent    = fmt(gross);
    document.getElementById('tc-ded-out').textContent      = fmt(ded);
    document.getElementById('tc-taxable-out').textContent  = fmt(taxable);
    document.getElementById('tc-tax-out').textContent      = fmt(totalTax);
    document.getElementById('tc-eff-out').textContent      = effectiveRate.toFixed(2) + '%';
    document.getElementById('tc-marginal-out').textContent = (marginal * 100).toFixed(0) + '%';

    document.getElementById('tc-results').classList.remove('tc-hidden');
    document.getElementById('tc-bracket-card').classList.remove('tc-hidden');

    tcRenderBrackets(breakdown, taxable);
    tcDrawChart(breakdown);
  };

  function formatBracketLabel(b, i, brackets) {
    var min = '$' + b.min.toLocaleString();
    var max = b.max === Infinity ? '+' : ' – $' + b.max.toLocaleString();
    return min + (b.max === Infinity ? '+' : ' – $' + b.max.toLocaleString());
  }

  function tcRenderBrackets(breakdown, taxable) {
    var maxTax = Math.max.apply(null, breakdown.map(function(b){ return b.tax; }));
    var tbody = document.getElementById('tc-bracket-body');
    tbody.innerHTML = breakdown.map(function(b, i) {
      var barPct = maxTax > 0 ? Math.round((b.tax / maxTax) * 100) : 0;
      var rowClass = b.active ? ' class="tc-active-row"' : '';
      var bar = '<span class="tc-bar-wrap"><span class="tc-bar-fill" style="width:' + barPct + '%"></span></span>';
      return '<tr' + rowClass + '>' +
        '<td>' + b.label + '</td>' +
        '<td>' + (b.rate * 100).toFixed(0) + '%</td>' +
        '<td>' + (b.income > 0 ? fmt(b.income) : '—') + '</td>' +
        '<td>' + (b.tax > 0 ? fmt(b.tax) : '—') + bar + '</td>' +
        '<td>' + (b.active ? '<span style="color:#22c55e;font-weight:700">&#10003;</span>' : '') + '</td>' +
        '</tr>';
    }).join('');
  }

  function tcDrawChart(breakdown) {
    var canvas = document.getElementById('tc-chart');
    var ctx = canvas.getContext('2d');
    var W = canvas.width, H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    var active = breakdown.filter(function(b){ return b.income > 0; });
    if (active.length === 0) return;

    var maxIncome = Math.max.apply(null, active.map(function(b){ return b.income; }));
    var pad = { top: 20, right: 20, bottom: 50, left: 70 };
    var chartW = W - pad.left - pad.right;
    var chartH = H - pad.top - pad.bottom;
    var barW = Math.floor(chartW / active.length) - 8;

    ctx.fillStyle = '#f8fafc';
    ctx.fillRect(0, 0, W, H);

    ctx.strokeStyle = '#e2e8f0';
    ctx.lineWidth = 1;
    [0, 0.25, 0.5, 0.75, 1].forEach(function(f) {
      var y = pad.top + chartH * (1 - f);
      ctx.beginPath();
      ctx.moveTo(pad.left, y);
      ctx.lineTo(pad.left + chartW, y);
      ctx.stroke();
      var label = '$' + Math.round(maxIncome * f / 1000) + 'K';
      ctx.fillStyle = '#999';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'right';
      ctx.textBaseline = 'middle';
      ctx.fillText(label, pad.left - 6, y);
    });

    active.forEach(function(b, i) {
      var x = pad.left + i * (chartW / active.length) + 4;
      var barH = chartH * (b.income / maxIncome);
      var y = pad.top + chartH - barH;

      var grad = ctx.createLinearGradient(0, y, 0, y + barH);
      grad.addColorStop(0, BRACKET_COLORS[Math.min(i, BRACKET_COLORS.length - 1)]);
      grad.addColorStop(1, '#16a34a');
      ctx.fillStyle = grad;
      ctx.beginPath();
      ctx.roundRect ? ctx.roundRect(x, y, barW, barH, [4,4,0,0]) : ctx.rect(x, y, barW, barH);
      ctx.fill();

      ctx.fillStyle = '#1a1a2e';
      ctx.font = 'bold 11px sans-serif';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'top';
      ctx.fillText((b.rate * 100).toFixed(0) + '%', x + barW / 2, pad.top + chartH + 8);

      ctx.fillStyle = '#16a34a';
      ctx.font = 'bold 10px sans-serif';
      ctx.textBaseline = 'bottom';
      ctx.fillText('$' + Math.round(b.income / 1000) + 'K', x + barW / 2, y - 2);
    });

    ctx.fillStyle = '#4a5568';
    ctx.font = '12px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'bottom';
    ctx.fillText('Income by Tax Bracket', W / 2, H);
  }

  window.addEventListener('DOMContentLoaded', function(){ tcUpdateDeduction(); });
  if (document.readyState !== 'loading') { tcUpdateDeduction(); }

  var BRACKET_COLORS = ['#dcfce7','#bbf7d0','#86efac','#4ade80','#22c55e','#16a34a','#15803d'];
})();
</script>
</div>

## Related Articles

- [How Much Tax Do You Pay on FX Profits in Japan? A Salary Worker's Guide](/posts/fx-tax-japan-salary-worker/)
- [FX Trading and Japan Tax Filing: Can You Carry Forward Losses for 3 Years?](/posts/fx-loss-carryforward-japan-tax/)
- [How to File a Kakuteishinkoku for FX Income in Japan: 2026 Guide](/posts/kakuteishinkoku-fx-income-guide/)
