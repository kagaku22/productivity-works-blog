---
title: "Wedding Budget Calculator - Plan Your Wedding Expenses"
description: "Plan your wedding budget with category breakdowns and cost estimates. Free wedding expense planner."
date: 2025-05-16
slug: "wedding-budget-calculator"
categories: ["Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/wedding-budget-calculator.png"
---

<div id="wb-app">
<style>
#wb-app {
  font-family: 'Segoe UI', Arial, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #2d2d2d;
  padding: 0 8px;
}
#wb-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  color: #1a1a1a;
  margin: 1.5rem 0 0.5rem;
  border-bottom: 2px solid #f0c4d4;
  padding-bottom: 0.3rem;
}
#wb-app .wb-intro {
  background: linear-gradient(135deg, #fff5f8 0%, #fdf0f5 100%);
  border: 1px solid #f0c4d4;
  border-radius: 10px;
  padding: 1.2rem 1.4rem;
  margin-bottom: 1.5rem;
  font-size: 0.97rem;
  color: #555;
}
#wb-app .wb-top-row {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  margin-bottom: 1.4rem;
}
#wb-app .wb-top-card {
  flex: 1 1 200px;
  background: #fff;
  border: 1px solid #e8d0d8;
  border-radius: 10px;
  padding: 1rem 1.2rem;
}
#wb-app .wb-top-card label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #888;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.4rem;
}
#wb-app .wb-top-card input {
  width: 100%;
  border: 1.5px solid #e0c8d0;
  border-radius: 6px;
  padding: 0.45rem 0.7rem;
  font-size: 1.1rem;
  font-weight: 600;
  color: #c0396b;
  background: #fffafb;
  box-sizing: border-box;
  outline: none;
  transition: border-color 0.2s;
}
#wb-app .wb-top-card input:focus {
  border-color: #c0396b;
  background: #fff;
}
#wb-app .wb-status-bar {
  background: #fff;
  border: 2px solid #e8d0d8;
  border-radius: 10px;
  padding: 1rem 1.4rem;
  margin-bottom: 1.4rem;
  display: flex;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
}
#wb-app .wb-status-label {
  font-size: 0.85rem;
  color: #888;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#wb-app .wb-status-amount {
  font-size: 1.5rem;
  font-weight: 800;
  color: #c0396b;
}
#wb-app .wb-status-diff {
  font-size: 1rem;
  font-weight: 700;
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
}
#wb-app .wb-status-diff.under {
  background: #e8f5e9;
  color: #2e7d32;
}
#wb-app .wb-status-diff.over {
  background: #fdecea;
  color: #c62828;
}
#wb-app .wb-status-diff.exact {
  background: #e8eaf6;
  color: #3949ab;
}
#wb-app .wb-progress-wrap {
  flex: 1 1 200px;
  min-width: 120px;
}
#wb-app .wb-progress-track {
  background: #f0e0e8;
  border-radius: 6px;
  height: 12px;
  overflow: hidden;
}
#wb-app .wb-progress-fill {
  height: 100%;
  border-radius: 6px;
  transition: width 0.4s, background 0.4s;
}
#wb-app .wb-main {
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
}
#wb-app .wb-categories {
  flex: 1 1 340px;
}
#wb-app .wb-chart-col {
  flex: 0 0 240px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
#wb-app .wb-category-row {
  background: #fff;
  border: 1px solid #ecdde4;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  margin-bottom: 0.7rem;
}
#wb-app .wb-cat-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 0.3rem;
}
#wb-app .wb-cat-name {
  font-weight: 600;
  font-size: 0.95rem;
  color: #333;
}
#wb-app .wb-cat-amounts {
  font-size: 0.82rem;
  color: #888;
  text-align: right;
}
#wb-app .wb-cat-pct {
  font-size: 0.8rem;
  font-weight: 700;
  color: #c0396b;
  min-width: 36px;
  text-align: right;
}
#wb-app .wb-cat-input-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#wb-app .wb-cat-slider {
  -webkit-appearance: none;
  appearance: none;
  flex: 1;
  height: 5px;
  border-radius: 3px;
  background: #f0c4d4;
  outline: none;
  cursor: pointer;
}
#wb-app .wb-cat-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #c0396b;
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
#wb-app .wb-cat-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #c0396b;
  cursor: pointer;
  border: none;
}
#wb-app .wb-warning {
  font-size: 0.8rem;
  color: #e65100;
  background: #fff3e0;
  border: 1px solid #ffcc80;
  border-radius: 6px;
  padding: 0.4rem 0.7rem;
  margin-bottom: 0.8rem;
  display: none;
}
#wb-app .wb-chart-title {
  font-size: 0.85rem;
  font-weight: 600;
  color: #888;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.6rem;
  text-align: center;
}
#wb-app canvas#wb-pie {
  border-radius: 50%;
  box-shadow: 0 2px 12px rgba(192,57,107,0.10);
}
#wb-app .wb-legend {
  margin-top: 1rem;
  width: 100%;
}
#wb-app .wb-legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.78rem;
  color: #555;
  margin-bottom: 0.3rem;
}
#wb-app .wb-legend-dot {
  width: 11px;
  height: 11px;
  border-radius: 3px;
  flex-shrink: 0;
}
#wb-app .wb-per-person {
  background: #fff5f8;
  border: 1px solid #f0c4d4;
  border-radius: 8px;
  padding: 0.8rem 1rem;
  margin-top: 1rem;
  font-size: 0.88rem;
  color: #555;
  text-align: center;
}
#wb-app .wb-per-person strong {
  font-size: 1.1rem;
  color: #c0396b;
}
#wb-app .wb-related {
  margin-top: 2rem;
  background: #f8f9fa;
  border: 1px solid #e0e0e0;
  border-radius: 10px;
  padding: 1rem 1.3rem;
}
#wb-app .wb-related h3 {
  font-size: 0.95rem;
  font-weight: 700;
  color: #444;
  margin: 0 0 0.6rem;
}
#wb-app .wb-related ul {
  margin: 0;
  padding-left: 1.2rem;
  font-size: 0.88rem;
  color: #555;
}
#wb-app .wb-related ul li {
  margin-bottom: 0.3rem;
}
#wb-app .wb-related a {
  color: #c0396b;
  text-decoration: none;
}
#wb-app .wb-related a:hover {
  text-decoration: underline;
}
@media (max-width: 600px) {
  #wb-app .wb-chart-col {
    flex: 1 1 100%;
    align-items: center;
  }
  #wb-app .wb-status-bar {
    gap: 10px;
  }
}
</style>

<div class="wb-intro">
  Plan your perfect wedding without the financial stress. Enter your total budget, adjust each category with sliders, and see your full breakdown instantly — including a live pie chart and per-guest cost.
</div>

<div class="wb-top-row">
  <div class="wb-top-card">
    <label for="wb-total-budget">Total Wedding Budget ($)</label>
    <input type="number" id="wb-total-budget" value="30000" min="0" step="500" placeholder="30000">
  </div>
  <div class="wb-top-card">
    <label for="wb-guest-count">Guest Count</label>
    <input type="number" id="wb-guest-count" value="100" min="1" step="1" placeholder="100">
  </div>
</div>

<div class="wb-status-bar">
  <div>
    <div class="wb-status-label">Budget</div>
    <div class="wb-status-amount" id="wb-disp-budget">$30,000</div>
  </div>
  <div>
    <div class="wb-status-label">Allocated</div>
    <div class="wb-status-amount" id="wb-disp-allocated">$30,000</div>
  </div>
  <div id="wb-disp-diff" class="wb-status-diff exact">Balanced</div>
  <div class="wb-progress-wrap">
    <div class="wb-status-label" style="margin-bottom:0.3rem;">Allocation</div>
    <div class="wb-progress-track">
      <div class="wb-progress-fill" id="wb-progress-fill" style="width:100%;background:#c0396b;"></div>
    </div>
    <div style="font-size:0.78rem;color:#aaa;margin-top:3px;" id="wb-pct-total-label">100% of budget</div>
  </div>
</div>

<div id="wb-pct-warning" class="wb-warning">
  Warning: category percentages add up to more or less than 100%. Adjust sliders to balance.
</div>

<div class="wb-main">
  <div class="wb-categories" id="wb-categories-list">
    <!-- Rows injected by JS -->
  </div>
  <div class="wb-chart-col">
    <div class="wb-chart-title">Breakdown</div>
    <canvas id="wb-pie" width="220" height="220"></canvas>
    <div class="wb-legend" id="wb-legend"></div>
    <div class="wb-per-person" id="wb-per-person">
      Per-guest cost:<br><strong id="wb-per-person-val">$300.00</strong>
    </div>
  </div>
</div>

<div class="wb-related">
  <h3>Related Free Tools</h3>
  <ul>
    <li><a href="/tools/budget-planner/">Monthly Budget Calculator</a></li>
    <li><a href="/tools/savings-goal-calculator/">Savings Goal Calculator</a></li>
    <li><a href="/tools/debt-payoff-calculator/">Debt Payoff Calculator</a></li>
    <li><a href="/tools/net-worth-calculator/">Net Worth Calculator</a></li>
  </ul>
</div>

<script>
(function() {
  'use strict';

  const CATEGORIES = [
    { name: 'Venue',         pct: 40, color: '#c0396b' },
    { name: 'Catering',      pct: 25, color: '#e05c8a' },
    { name: 'Photography',   pct: 10, color: '#f4a0b5' },
    { name: 'Flowers',       pct:  5, color: '#f7c5d5' },
    { name: 'Music',         pct:  5, color: '#a0c4ff' },
    { name: 'Attire',        pct:  5, color: '#b5ead7' },
    { name: 'Invitations',   pct:  3, color: '#ffd6a5' },
    { name: 'Favors',        pct:  2, color: '#caffbf' },
    { name: 'Other',         pct:  5, color: '#c9c9ff' },
  ];

  let state = {
    budget: 30000,
    guests: 100,
    pcts: CATEGORIES.map(c => c.pct),
  };

  function fmt(n) {
    return '$' + n.toLocaleString('en-US', { minimumFractionDigits: 0, maximumFractionDigits: 0 });
  }
  function fmtDec(n) {
    return '$' + n.toLocaleString('en-US', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
  }

  // Build category rows
  const list = document.getElementById('wb-categories-list');
  CATEGORIES.forEach((cat, i) => {
    const row = document.createElement('div');
    row.className = 'wb-category-row';
    row.innerHTML = `
      <div class="wb-cat-header">
        <span class="wb-cat-name">${cat.name}</span>
        <div style="text-align:right">
          <span class="wb-cat-amounts" id="wb-amt-${i}"></span>
          <span class="wb-cat-pct" id="wb-pct-${i}">${cat.pct}%</span>
        </div>
      </div>
      <div class="wb-cat-input-row">
        <input type="range" class="wb-cat-slider" id="wb-slider-${i}"
          min="0" max="60" step="1" value="${cat.pct}"
          aria-label="${cat.name} percentage">
      </div>
    `;
    list.appendChild(row);

    document.getElementById(`wb-slider-${i}`).addEventListener('input', function() {
      state.pcts[i] = parseInt(this.value, 10);
      render();
    });
  });

  document.getElementById('wb-total-budget').addEventListener('input', function() {
    const v = parseFloat(this.value);
    state.budget = isNaN(v) ? 0 : v;
    render();
  });
  document.getElementById('wb-guest-count').addEventListener('input', function() {
    const v = parseInt(this.value, 10);
    state.guests = isNaN(v) || v < 1 ? 1 : v;
    render();
  });

  function drawPie(data, colors) {
    const canvas = document.getElementById('wb-pie');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const cx = W / 2, cy = H / 2, r = Math.min(cx, cy) - 6;
    ctx.clearRect(0, 0, W, H);

    const total = data.reduce((a, b) => a + b, 0);
    if (total === 0) return;

    let startAngle = -Math.PI / 2;
    data.forEach((val, i) => {
      if (val <= 0) return;
      const slice = (val / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, startAngle, startAngle + slice);
      ctx.closePath();
      ctx.fillStyle = colors[i];
      ctx.fill();
      ctx.strokeStyle = '#fff';
      ctx.lineWidth = 2;
      ctx.stroke();
      startAngle += slice;
    });

    // center circle (donut)
    ctx.beginPath();
    ctx.arc(cx, cy, r * 0.44, 0, 2 * Math.PI);
    ctx.fillStyle = '#fff';
    ctx.fill();
  }

  function buildLegend(amounts) {
    const leg = document.getElementById('wb-legend');
    leg.innerHTML = '';
    CATEGORIES.forEach((cat, i) => {
      if (amounts[i] <= 0) return;
      const item = document.createElement('div');
      item.className = 'wb-legend-item';
      item.innerHTML = `
        <span class="wb-legend-dot" style="background:${cat.color}"></span>
        <span>${cat.name}: ${fmt(amounts[i])}</span>
      `;
      leg.appendChild(item);
    });
  }

  function render() {
    const budget = state.budget;
    const guests = state.guests;
    const pctTotal = state.pcts.reduce((a, b) => a + b, 0);
    const amounts = state.pcts.map(p => budget * p / 100);
    const allocated = amounts.reduce((a, b) => a + b, 0);

    // Update slider labels
    CATEGORIES.forEach((cat, i) => {
      document.getElementById(`wb-pct-${i}`).textContent = state.pcts[i] + '%';
      document.getElementById(`wb-slider-${i}`).value = state.pcts[i];
      document.getElementById(`wb-amt-${i}`).textContent = fmt(amounts[i]);
    });

    // Status bar
    document.getElementById('wb-disp-budget').textContent = fmt(budget);
    document.getElementById('wb-disp-allocated').textContent = fmt(allocated);

    const diff = budget - allocated;
    const diffEl = document.getElementById('wb-disp-diff');
    if (Math.abs(diff) < 1) {
      diffEl.textContent = 'Balanced';
      diffEl.className = 'wb-status-diff exact';
    } else if (diff > 0) {
      diffEl.textContent = fmt(diff) + ' under budget';
      diffEl.className = 'wb-status-diff under';
    } else {
      diffEl.textContent = fmt(Math.abs(diff)) + ' over budget';
      diffEl.className = 'wb-status-diff over';
    }

    // Progress bar
    const pf = document.getElementById('wb-progress-fill');
    const pPct = budget > 0 ? Math.min((allocated / budget) * 100, 120) : 0;
    pf.style.width = Math.min(pPct, 100) + '%';
    pf.style.background = pPct > 100 ? '#c62828' : pPct > 90 ? '#e65100' : '#c0396b';
    document.getElementById('wb-pct-total-label').textContent = pctTotal + '% of budget';

    // Warning
    const warn = document.getElementById('wb-pct-warning');
    warn.style.display = (pctTotal !== 100) ? 'block' : 'none';
    warn.textContent = pctTotal > 100
      ? `Warning: category percentages add up to ${pctTotal}% (${pctTotal - 100}% over 100%). Adjust sliders to balance.`
      : `Note: category percentages add up to ${pctTotal}% (${100 - pctTotal}% unallocated). Adjust sliders to balance.`;

    // Per guest
    document.getElementById('wb-per-person-val').textContent = guests > 0
      ? fmtDec(allocated / guests)
      : '$0.00';

    // Pie chart
    drawPie(amounts, CATEGORIES.map(c => c.color));
    buildLegend(amounts);
  }

  render();
})();
</script>

</div>
