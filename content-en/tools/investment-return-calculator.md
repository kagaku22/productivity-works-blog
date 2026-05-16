---
title: "Investment Return Calculator - CAGR & Total Growth"
description: "Calculate your investment returns with compound growth, dividends, and fees. Free ROI and portfolio growth calculator."
date: 2025-05-16
categories: ["Free Tools"]
slug: "investment-return-calculator"
ShowToc: false
cover:
  image: "/images/covers/investment-return-calculator.png"
---

<div id="ir-app">
<style>
#ir-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
}
#ir-app * { box-sizing: border-box; }
#ir-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  color: #1a1a2e;
  border-left: 4px solid #2563eb;
  padding-left: 0.6rem;
}
#ir-app .ir-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1rem;
}
@media (max-width: 600px) {
  #ir-app .ir-grid { grid-template-columns: 1fr; }
}
#ir-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.3rem;
}
#ir-app input[type="number"] {
  width: 100%;
  padding: 0.6rem 0.75rem;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.2s;
  background: #fff;
}
#ir-app input[type="number"]:focus {
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37,99,235,0.1);
}
#ir-app .ir-hint {
  font-size: 0.75rem;
  color: #6b7280;
  margin-top: 0.25rem;
}
#ir-app .ir-btn {
  display: inline-block;
  padding: 0.7rem 2rem;
  background: linear-gradient(135deg, #2563eb, #1d4ed8);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: transform 0.1s, box-shadow 0.1s;
  margin-top: 0.5rem;
}
#ir-app .ir-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 14px rgba(37,99,235,0.35);
}
#ir-app .ir-btn:active { transform: translateY(0); }
#ir-app .ir-results {
  display: none;
}
#ir-app .ir-cards {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.75rem;
  margin: 1.25rem 0;
}
@media (max-width: 700px) {
  #ir-app .ir-cards { grid-template-columns: repeat(2, 1fr); }
}
#ir-app .ir-card {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem 0.75rem;
  text-align: center;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ir-app .ir-card .ir-card-label {
  font-size: 0.75rem;
  color: #6b7280;
  margin-bottom: 0.35rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#ir-app .ir-card .ir-card-val {
  font-size: 1.3rem;
  font-weight: 800;
  color: #1a1a2e;
}
#ir-app .ir-card.ir-highlight .ir-card-val { color: #2563eb; }
#ir-app .ir-card.ir-green .ir-card-val { color: #059669; }
#ir-app .ir-chart-wrap {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem;
  margin-bottom: 1.25rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ir-app canvas { display: block; width: 100% !important; }
#ir-app .ir-table-wrap {
  overflow-x: auto;
  border-radius: 12px;
  border: 1.5px solid #e5e7eb;
  margin-bottom: 1.5rem;
}
#ir-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#ir-app thead th {
  background: #1e3a8a;
  color: #fff;
  padding: 0.65rem 0.85rem;
  text-align: right;
  font-weight: 700;
  white-space: nowrap;
}
#ir-app thead th:first-child { text-align: center; }
#ir-app tbody tr:nth-child(even) { background: #f0f4ff; }
#ir-app tbody tr:hover { background: #dbeafe; }
#ir-app tbody td {
  padding: 0.55rem 0.85rem;
  text-align: right;
  border-bottom: 1px solid #e5e7eb;
  white-space: nowrap;
}
#ir-app tbody td:first-child { text-align: center; font-weight: 700; }
#ir-app .ir-scenario {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem 1.25rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ir-app .ir-scenario h3 {
  font-size: 1rem;
  font-weight: 700;
  margin: 0 0 0.75rem;
  color: #374151;
}
#ir-app .ir-scenario-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.75rem;
}
@media (max-width: 600px) {
  #ir-app .ir-scenario-grid { grid-template-columns: 1fr; }
}
#ir-app .ir-s-card {
  border-radius: 10px;
  padding: 0.85rem 0.75rem;
  text-align: center;
}
#ir-app .ir-s-card.conservative { background: #f0fdf4; border: 1.5px solid #86efac; }
#ir-app .ir-s-card.moderate    { background: #eff6ff; border: 1.5px solid #93c5fd; }
#ir-app .ir-s-card.aggressive  { background: #fef3c7; border: 1.5px solid #fcd34d; }
#ir-app .ir-s-card .ir-s-label {
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.3rem;
}
#ir-app .ir-s-card.conservative .ir-s-label { color: #059669; }
#ir-app .ir-s-card.moderate    .ir-s-label { color: #2563eb; }
#ir-app .ir-s-card.aggressive  .ir-s-label { color: #d97706; }
#ir-app .ir-s-card .ir-s-rate {
  font-size: 0.8rem;
  color: #6b7280;
  margin-bottom: 0.5rem;
}
#ir-app .ir-s-card .ir-s-val {
  font-size: 1.2rem;
  font-weight: 800;
  color: #1a1a2e;
}
#ir-app .ir-related {
  background: #f8fafc;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem 1.25rem;
  margin-top: 1rem;
}
#ir-app .ir-related h3 {
  font-size: 0.95rem;
  font-weight: 700;
  margin: 0 0 0.6rem;
  color: #374151;
}
#ir-app .ir-related ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
#ir-app .ir-related ul li {
  padding: 0.25rem 0;
  font-size: 0.9rem;
}
#ir-app .ir-related ul li a { color: #2563eb; text-decoration: none; }
#ir-app .ir-related ul li a:hover { text-decoration: underline; }
#ir-app .ir-input-section {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
</style>

<h2>Investment Return Calculator</h2>
<p style="color:#6b7280;font-size:0.92rem;margin-bottom:1rem;">Enter your investment details to calculate ending balance, total growth, CAGR, and a year-by-year breakdown. Compare conservative, moderate, and aggressive return scenarios.</p>

<div class="ir-input-section">
  <div class="ir-grid">
    <div>
      <label for="ir-initial">Initial Investment ($)</label>
      <input type="number" id="ir-initial" value="10000" min="0" step="100">
      <div class="ir-hint">The amount you invest at the start</div>
    </div>
    <div>
      <label for="ir-monthly">Monthly Contribution ($)</label>
      <input type="number" id="ir-monthly" value="500" min="0" step="50">
      <div class="ir-hint">Regular monthly addition to investment</div>
    </div>
    <div>
      <label for="ir-rate">Expected Annual Return (%)</label>
      <input type="number" id="ir-rate" value="7" min="0" max="100" step="0.1">
      <div class="ir-hint">Historical S&amp;P 500 avg ≈ 7% (inflation-adjusted)</div>
    </div>
    <div>
      <label for="ir-years">Investment Period (Years)</label>
      <input type="number" id="ir-years" value="20" min="1" max="50" step="1">
      <div class="ir-hint">How long you plan to stay invested</div>
    </div>
  </div>
  <button class="ir-btn" onclick="irCalculate()">Calculate Returns</button>
</div>

<div class="ir-results" id="ir-results">
  <h2>Results</h2>
  <div class="ir-cards">
    <div class="ir-card ir-highlight">
      <div class="ir-card-label">Ending Balance</div>
      <div class="ir-card-val" id="ir-ending">-</div>
    </div>
    <div class="ir-card">
      <div class="ir-card-label">Total Contributions</div>
      <div class="ir-card-val" id="ir-contrib">-</div>
    </div>
    <div class="ir-card ir-green">
      <div class="ir-card-label">Total Growth</div>
      <div class="ir-card-val" id="ir-growth">-</div>
    </div>
    <div class="ir-card">
      <div class="ir-card-label">CAGR</div>
      <div class="ir-card-val" id="ir-cagr">-</div>
    </div>
  </div>

  <h2>Growth Chart</h2>
  <div class="ir-chart-wrap">
    <canvas id="ir-canvas" height="300"></canvas>
  </div>

  <h2>Year-by-Year Breakdown</h2>
  <div class="ir-table-wrap">
    <table>
      <thead>
        <tr>
          <th>Year</th>
          <th>Balance</th>
          <th>Contributions</th>
          <th>Growth</th>
          <th>Growth %</th>
        </tr>
      </thead>
      <tbody id="ir-tbody"></tbody>
    </table>
  </div>

  <div class="ir-scenario">
    <h3>Scenario Comparison</h3>
    <p style="font-size:0.82rem;color:#6b7280;margin:0 0 0.75rem;">Same initial investment &amp; contributions — different return assumptions.</p>
    <div class="ir-scenario-grid">
      <div class="ir-s-card conservative">
        <div class="ir-s-label">Conservative</div>
        <div class="ir-s-rate">4% annual return</div>
        <div class="ir-s-val" id="ir-s-conservative">-</div>
      </div>
      <div class="ir-s-card moderate">
        <div class="ir-s-label">Moderate</div>
        <div class="ir-s-rate">7% annual return</div>
        <div class="ir-s-val" id="ir-s-moderate">-</div>
      </div>
      <div class="ir-s-card aggressive">
        <div class="ir-s-label">Aggressive</div>
        <div class="ir-s-rate">12% annual return</div>
        <div class="ir-s-val" id="ir-s-aggressive">-</div>
      </div>
    </div>
  </div>
</div>

<div class="ir-related">
  <h3>Related Free Tools</h3>
  <ul>
    <li><a href="/tools/compound-interest-calculator/">Compound Interest Calculator</a> — See how interest compounds over time</li>
    <li><a href="/tools/savings-goal-calculator/">Savings Goal Calculator</a> — How much to save monthly to hit your target</li>
    <li><a href="/tools/net-worth-tracker/">Net Worth Tracker</a> — Track assets vs liabilities over time</li>
    <li><a href="/tools/retirement-calculator/">Retirement Calculator</a> — Plan your retirement nest egg</li>
  </ul>
</div>

<script>
(function() {
  function fmt(n) {
    if (Math.abs(n) >= 1e6) return '$' + (n / 1e6).toFixed(2) + 'M';
    if (Math.abs(n) >= 1e3) return '$' + (n / 1e3).toFixed(1) + 'K';
    return '$' + n.toFixed(0);
  }
  function fmtFull(n) {
    return '$' + Math.round(n).toLocaleString('en-US');
  }

  function calcFutureValue(initial, monthly, annualRate, years) {
    var monthlyRate = annualRate / 100 / 12;
    var months = years * 12;
    var fv;
    if (monthlyRate === 0) {
      fv = initial + monthly * months;
    } else {
      fv = initial * Math.pow(1 + monthlyRate, months)
         + monthly * (Math.pow(1 + monthlyRate, months) - 1) / monthlyRate;
    }
    return fv;
  }

  function buildYearData(initial, monthly, annualRate, years) {
    var rows = [];
    var monthlyRate = annualRate / 100 / 12;
    var balance = initial;
    var totalContrib = initial;
    for (var y = 1; y <= years; y++) {
      for (var m = 0; m < 12; m++) {
        balance = balance * (1 + monthlyRate) + monthly;
        totalContrib += monthly;
      }
      rows.push({
        year: y,
        balance: balance,
        contributions: totalContrib,
        growth: balance - totalContrib,
        growthPct: totalContrib > 0 ? ((balance - totalContrib) / totalContrib * 100) : 0
      });
    }
    return rows;
  }

  function calcCAGR(initial, monthly, finalBalance, years) {
    var totalContrib = initial + monthly * 12 * years;
    if (totalContrib <= 0 || years <= 0) return 0;
    return (Math.pow(finalBalance / totalContrib, 1 / years) - 1) * 100;
  }

  var chartInstance = null;

  function drawChart(rows, years) {
    var canvas = document.getElementById('ir-canvas');
    var ctx = canvas.getContext('2d');
    var dpr = window.devicePixelRatio || 1;
    var w = canvas.parentElement.clientWidth - 32;
    var h = 300;
    canvas.width = w * dpr;
    canvas.height = h * dpr;
    canvas.style.width = w + 'px';
    canvas.style.height = h + 'px';
    ctx.scale(dpr, dpr);

    var pad = { top: 20, right: 20, bottom: 40, left: 70 };
    var plotW = w - pad.left - pad.right;
    var plotH = h - pad.top - pad.bottom;

    var maxVal = rows[rows.length - 1].balance;
    var labels = rows.map(function(r) { return 'Y' + r.year; });

    ctx.clearRect(0, 0, w, h);

    // Grid lines
    ctx.strokeStyle = '#e5e7eb';
    ctx.lineWidth = 1;
    for (var i = 0; i <= 5; i++) {
      var y = pad.top + plotH - (i / 5) * plotH;
      ctx.beginPath();
      ctx.moveTo(pad.left, y);
      ctx.lineTo(pad.left + plotW, y);
      ctx.stroke();
      ctx.fillStyle = '#9ca3af';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'right';
      ctx.fillText(fmt((i / 5) * maxVal), pad.left - 6, y + 4);
    }

    // X labels (show every N years)
    var step = Math.ceil(years / 10);
    ctx.fillStyle = '#6b7280';
    ctx.font = '11px sans-serif';
    ctx.textAlign = 'center';
    rows.forEach(function(r, i) {
      if (r.year % step === 0 || r.year === 1) {
        var x = pad.left + (i / (rows.length - 1)) * plotW;
        ctx.fillText('Y' + r.year, x, h - pad.bottom + 16);
      }
    });

    function dataX(i) { return pad.left + (i / (rows.length - 1)) * plotW; }
    function dataY(val) { return pad.top + plotH - (val / maxVal) * plotH; }

    // Contribution area
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i);
      var y = dataY(r.contributions);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.lineTo(dataX(rows.length - 1), pad.top + plotH);
    ctx.lineTo(dataX(0), pad.top + plotH);
    ctx.closePath();
    ctx.fillStyle = 'rgba(219,234,254,0.7)';
    ctx.fill();

    // Balance area
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i);
      var y = dataY(r.balance);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.lineTo(dataX(rows.length - 1), pad.top + plotH);
    ctx.lineTo(dataX(0), pad.top + plotH);
    ctx.closePath();
    ctx.fillStyle = 'rgba(37,99,235,0.15)';
    ctx.fill();

    // Balance line
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i);
      var y = dataY(r.balance);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.strokeStyle = '#2563eb';
    ctx.lineWidth = 2.5;
    ctx.stroke();

    // Contribution line
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i);
      var y = dataY(r.contributions);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.strokeStyle = '#93c5fd';
    ctx.lineWidth = 1.5;
    ctx.setLineDash([5, 4]);
    ctx.stroke();
    ctx.setLineDash([]);

    // Legend
    var lx = pad.left + 10;
    var ly = pad.top + 10;
    ctx.fillStyle = '#2563eb'; ctx.fillRect(lx, ly, 16, 3);
    ctx.fillStyle = '#374151'; ctx.font = '11px sans-serif'; ctx.textAlign = 'left';
    ctx.fillText('Balance', lx + 20, ly + 4);
    ctx.fillStyle = '#93c5fd'; ctx.fillRect(lx + 80, ly, 16, 3);
    ctx.fillStyle = '#374151';
    ctx.fillText('Contributions', lx + 100, ly + 4);
  }

  function fillTable(rows) {
    var tbody = document.getElementById('ir-tbody');
    tbody.innerHTML = '';
    rows.forEach(function(r) {
      var tr = document.createElement('tr');
      tr.innerHTML = '<td>' + r.year + '</td>'
        + '<td>' + fmtFull(r.balance) + '</td>'
        + '<td>' + fmtFull(r.contributions) + '</td>'
        + '<td>' + fmtFull(r.growth) + '</td>'
        + '<td>' + (r.growthPct >= 0 ? '+' : '') + r.growthPct.toFixed(1) + '%</td>';
      tbody.appendChild(tr);
    });
  }

  window.irCalculate = function() {
    var initial = parseFloat(document.getElementById('ir-initial').value) || 0;
    var monthly = parseFloat(document.getElementById('ir-monthly').value) || 0;
    var rate    = parseFloat(document.getElementById('ir-rate').value)    || 0;
    var years   = parseInt(document.getElementById('ir-years').value)     || 1;

    var rows = buildYearData(initial, monthly, rate, years);
    var finalBal = rows[rows.length - 1].balance;
    var totalContrib = rows[rows.length - 1].contributions;
    var totalGrowth  = finalBal - totalContrib;
    var cagr = calcCAGR(initial, monthly, finalBal, years);

    document.getElementById('ir-ending').textContent = fmtFull(finalBal);
    document.getElementById('ir-contrib').textContent = fmtFull(totalContrib);
    document.getElementById('ir-growth').textContent  = fmtFull(totalGrowth);
    document.getElementById('ir-cagr').textContent    = cagr.toFixed(2) + '%';

    // Scenarios
    var sRates = { conservative: 4, moderate: 7, aggressive: 12 };
    Object.keys(sRates).forEach(function(key) {
      var fv = calcFutureValue(initial, monthly, sRates[key], years);
      document.getElementById('ir-s-' + key).textContent = fmtFull(fv);
    });

    fillTable(rows);
    document.getElementById('ir-results').style.display = 'block';
    setTimeout(function() { drawChart(rows, years); }, 50);
  };

  // Auto-calculate on load
  window.addEventListener('DOMContentLoaded', function() { irCalculate(); });
  if (document.readyState !== 'loading') { irCalculate(); }
})();
</script>

</div>

---

## Related Tools

> [Compound Interest Calculator](/tools/compound-interest-calculator/)
> [Fire Calculator](/tools/fire-calculator/)
> [Ideco Simulator](/tools/ideco-simulator/)

## Related Articles

- [Beginner Investing Guide 2026: How to Start Building Wealth Today](/posts/beginner-investing-guide-2026/)
- [Best Index Funds for Beginners 2026](/posts/best-index-funds-for-beginners-2026/)
- [Best Investment Account for Beginners in Japan: NISA vs. iDeCo vs. Regular Brokerage](/posts/best-investment-account-japan-nisa-ideco/)
