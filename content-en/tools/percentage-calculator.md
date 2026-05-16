---
title: "Percentage Calculator | Calculate Any Percentage Instantly"
date: 2026-05-16
draft: false
slug: "percentage-calculator"
aliases: ["/tools/percentage-calculator/", "/tools/percentage-calculator/"]
description: "Free percentage calculator with 5 modes: find percentage of a number, what percent one number is of another, percentage increase/decrease, tip calculator, and discount calculator."
categories: ["Free Tools"]
tags: ["percentage", "calculator", "math", "discount", "tip calculator"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/percentage-calculator.png"
  alt: "Percentage Calculator | Calculate Any Percentage Instantly"
  relative: false
---

*Disclosure: This page may contain affiliate links. If you make a purchase through these links, we may earn a commission at no extra cost to you. We only recommend tools and services we genuinely find useful.*

# Percentage Calculator

Whether you're figuring out a restaurant tip, calculating a sale discount, or tracking how much your expenses changed month over month, percentages come up constantly in everyday life. This free calculator gives you five dedicated modes so you always get the right answer — no mental math required.

<style>
  .pct-wrap {
    font-family: system-ui, -apple-system, sans-serif;
    max-width: 680px;
    margin: 2rem auto;
    color: #1e1b4b;
  }
  .pct-tabs {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 0;
    padding: 0;
    list-style: none;
  }
  .pct-tabs button {
    background: #e0e7ff;
    border: 2px solid transparent;
    border-radius: 8px 8px 0 0;
    color: #4338ca;
    cursor: pointer;
    font-size: 0.82rem;
    font-weight: 600;
    padding: 8px 14px;
    transition: background 0.15s, color 0.15s, border-color 0.15s;
    white-space: nowrap;
  }
  .pct-tabs button:hover {
    background: #c7d2fe;
  }
  .pct-tabs button.active {
    background: #4f46e5;
    color: #fff;
    border-color: #4f46e5;
  }
  .pct-panel-wrap {
    background: #f5f3ff;
    border: 2px solid #4f46e5;
    border-radius: 0 8px 8px 8px;
    padding: 1.5rem;
  }
  .pct-panel { display: none; }
  .pct-panel.active { display: block; }
  .pct-panel h3 {
    color: #4f46e5;
    font-size: 1rem;
    margin: 0 0 1rem;
  }
  .pct-row {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 1rem;
  }
  .pct-row label {
    font-size: 0.9rem;
    font-weight: 600;
    min-width: 130px;
    color: #312e81;
  }
  .pct-row input[type="number"] {
    border: 2px solid #a5b4fc;
    border-radius: 6px;
    font-size: 1rem;
    padding: 7px 10px;
    width: 140px;
    outline: none;
    background: #fff;
    color: #1e1b4b;
    transition: border-color 0.15s;
  }
  .pct-row input[type="number"]:focus {
    border-color: #4f46e5;
  }
  .pct-row span.unit {
    font-size: 0.95rem;
    color: #6366f1;
    font-weight: 700;
  }
  .pct-btn {
    background: #4f46e5;
    border: none;
    border-radius: 8px;
    color: #fff;
    cursor: pointer;
    font-size: 0.95rem;
    font-weight: 700;
    padding: 10px 28px;
    margin-top: 0.5rem;
    transition: background 0.15s;
  }
  .pct-btn:hover { background: #4338ca; }
  .pct-result {
    margin-top: 1.2rem;
    background: #4f46e5;
    border-radius: 10px;
    color: #fff;
    padding: 1rem 1.2rem;
    display: none;
  }
  .pct-result.visible { display: block; }
  .pct-result .res-main {
    font-size: 1.6rem;
    font-weight: 800;
    letter-spacing: -0.5px;
  }
  .pct-result .res-formula {
    font-size: 0.82rem;
    opacity: 0.8;
    margin-top: 4px;
  }
  /* Slider shared */
  .pct-slider-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 1rem;
    flex-wrap: wrap;
  }
  .pct-slider-row label {
    font-size: 0.9rem;
    font-weight: 600;
    min-width: 130px;
    color: #312e81;
  }
  .pct-slider-row input[type="range"] {
    accent-color: #4f46e5;
    width: 180px;
    cursor: pointer;
  }
  .pct-slider-row .slider-val {
    background: #4f46e5;
    color: #fff;
    border-radius: 6px;
    font-size: 0.9rem;
    font-weight: 700;
    min-width: 52px;
    padding: 4px 8px;
    text-align: center;
  }
  /* Tip / Discount multi-result */
  .pct-multi-result {
    margin-top: 1.2rem;
    display: none;
    gap: 10px;
    flex-wrap: wrap;
  }
  .pct-multi-result.visible { display: flex; }
  .pct-card {
    background: #4f46e5;
    border-radius: 10px;
    color: #fff;
    padding: 0.9rem 1.1rem;
    flex: 1 1 140px;
    min-width: 130px;
  }
  .pct-card.highlight {
    background: #7c3aed;
  }
  .pct-card .card-label {
    font-size: 0.75rem;
    opacity: 0.85;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    margin-bottom: 4px;
  }
  .pct-card .card-val {
    font-size: 1.4rem;
    font-weight: 800;
  }
  /* % change colors */
  .res-increase { background: #16a34a !important; }
  .res-decrease { background: #dc2626 !important; }
  .res-zero     { background: #6b7280 !important; }
  /* Quick ref table */
  .pct-table-wrap {
    margin-top: 2.5rem;
    overflow-x: auto;
  }
  .pct-table-wrap h2 {
    color: #4f46e5;
    font-size: 1.1rem;
    margin-bottom: 0.8rem;
  }
  .pct-table {
    border-collapse: collapse;
    width: 100%;
    font-size: 0.88rem;
  }
  .pct-table th {
    background: #4f46e5;
    color: #fff;
    padding: 8px 12px;
    text-align: right;
  }
  .pct-table th:first-child { text-align: left; border-radius: 6px 0 0 0; }
  .pct-table th:last-child  { border-radius: 0 6px 0 0; }
  .pct-table td {
    border: 1px solid #c7d2fe;
    padding: 7px 12px;
    text-align: right;
    color: #312e81;
  }
  .pct-table td:first-child { text-align: left; font-weight: 700; color: #4f46e5; }
  .pct-table tr:nth-child(even) td { background: #ede9fe; }
  .pct-table tr:nth-child(odd)  td { background: #f5f3ff; }
</style>

<div class="pct-wrap">

  <!-- TAB BUTTONS -->
  <div style="overflow-x:auto;">
    <ul class="pct-tabs" role="tablist">
      <li><button class="active" role="tab" onclick="pctTab(event,'t1')">X% of Y</button></li>
      <li><button role="tab" onclick="pctTab(event,'t2')">X is ?% of Y</button></li>
      <li><button role="tab" onclick="pctTab(event,'t3')">% Change</button></li>
      <li><button role="tab" onclick="pctTab(event,'t4')">Tip Calculator</button></li>
      <li><button role="tab" onclick="pctTab(event,'t5')">Discount Calculator</button></li>
    </ul>
  </div>

  <!-- PANEL WRAP -->
  <div class="pct-panel-wrap">

    <!-- TAB 1: What is X% of Y? -->
    <div id="t1" class="pct-panel active">
      <h3>What is X% of Y?</h3>
      <div class="pct-row">
        <label>Percentage (%)</label>
        <input type="number" id="t1-pct" placeholder="e.g. 15" min="0" step="any">
        <span class="unit">%</span>
      </div>
      <div class="pct-row">
        <label>of Number</label>
        <input type="number" id="t1-num" placeholder="e.g. 200" step="any">
      </div>
      <button class="pct-btn" onclick="calcT1()">Calculate</button>
      <div class="pct-result" id="t1-result">
        <div class="res-main" id="t1-main"></div>
        <div class="res-formula" id="t1-formula"></div>
      </div>
    </div>

    <!-- TAB 2: X is what % of Y? -->
    <div id="t2" class="pct-panel">
      <h3>X is what % of Y?</h3>
      <div class="pct-row">
        <label>Number X</label>
        <input type="number" id="t2-x" placeholder="e.g. 30" step="any">
      </div>
      <div class="pct-row">
        <label>Number Y</label>
        <input type="number" id="t2-y" placeholder="e.g. 200" step="any">
      </div>
      <button class="pct-btn" onclick="calcT2()">Calculate</button>
      <div class="pct-result" id="t2-result">
        <div class="res-main" id="t2-main"></div>
        <div class="res-formula" id="t2-formula"></div>
      </div>
    </div>

    <!-- TAB 3: % Change -->
    <div id="t3" class="pct-panel">
      <h3>Percentage Change</h3>
      <div class="pct-row">
        <label>Original Value</label>
        <input type="number" id="t3-orig" placeholder="e.g. 80" step="any">
      </div>
      <div class="pct-row">
        <label>New Value</label>
        <input type="number" id="t3-new" placeholder="e.g. 100" step="any">
      </div>
      <button class="pct-btn" onclick="calcT3()">Calculate</button>
      <div class="pct-result" id="t3-result">
        <div class="res-main" id="t3-main"></div>
        <div class="res-formula" id="t3-formula"></div>
      </div>
    </div>

    <!-- TAB 4: Tip Calculator -->
    <div id="t4" class="pct-panel">
      <h3>Tip Calculator</h3>
      <div class="pct-row">
        <label>Bill Amount ($)</label>
        <input type="number" id="t4-bill" placeholder="e.g. 85.00" min="0" step="0.01" oninput="calcT4()">
        <span class="unit">$</span>
      </div>
      <div class="pct-slider-row">
        <label>Tip Percentage</label>
        <input type="range" id="t4-tip-slider" min="0" max="30" value="18" step="1" oninput="t4SliderUpdate()">
        <span class="slider-val" id="t4-tip-display">18%</span>
      </div>
      <div class="pct-slider-row">
        <label>Split Between</label>
        <input type="range" id="t4-people-slider" min="1" max="20" value="1" step="1" oninput="t4PeopleUpdate()">
        <span class="slider-val" id="t4-people-display">1 person</span>
      </div>
      <button class="pct-btn" onclick="calcT4()">Calculate</button>
      <div class="pct-multi-result" id="t4-result">
        <div class="pct-card">
          <div class="card-label">Tip Amount</div>
          <div class="card-val" id="t4-tip-amt">—</div>
        </div>
        <div class="pct-card">
          <div class="card-label">Total Bill</div>
          <div class="card-val" id="t4-total">—</div>
        </div>
        <div class="pct-card highlight">
          <div class="card-label">Per Person</div>
          <div class="card-val" id="t4-per-person">—</div>
        </div>
      </div>
    </div>

    <!-- TAB 5: Discount Calculator -->
    <div id="t5" class="pct-panel">
      <h3>Discount Calculator</h3>
      <div class="pct-row">
        <label>Original Price ($)</label>
        <input type="number" id="t5-price" placeholder="e.g. 120.00" min="0" step="0.01" oninput="calcT5()">
        <span class="unit">$</span>
      </div>
      <div class="pct-slider-row">
        <label>Discount</label>
        <input type="range" id="t5-disc-slider" min="5" max="90" value="20" step="1" oninput="t5SliderUpdate()">
        <span class="slider-val" id="t5-disc-display">20%</span>
      </div>
      <button class="pct-btn" onclick="calcT5()">Calculate</button>
      <div class="pct-multi-result" id="t5-result">
        <div class="pct-card">
          <div class="card-label">Discount Amount</div>
          <div class="card-val" id="t5-disc-amt">—</div>
        </div>
        <div class="pct-card">
          <div class="card-label">Final Price</div>
          <div class="card-val" id="t5-final">—</div>
        </div>
        <div class="pct-card highlight">
          <div class="card-label">You Save</div>
          <div class="card-val" id="t5-save">—</div>
        </div>
      </div>
    </div>

  </div><!-- /panel-wrap -->

  <!-- QUICK REFERENCE TABLE -->
  <div class="pct-table-wrap">
    <h2>Quick Percentage Reference</h2>
    <table class="pct-table">
      <thead>
        <tr>
          <th>% of amount</th>
          <th>$50</th>
          <th>$100</th>
          <th>$500</th>
          <th>$1,000</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>10%</td><td>$5.00</td><td>$10.00</td><td>$50.00</td><td>$100.00</td></tr>
        <tr><td>15%</td><td>$7.50</td><td>$15.00</td><td>$75.00</td><td>$150.00</td></tr>
        <tr><td>20%</td><td>$10.00</td><td>$20.00</td><td>$100.00</td><td>$200.00</td></tr>
        <tr><td>25%</td><td>$12.50</td><td>$25.00</td><td>$125.00</td><td>$250.00</td></tr>
        <tr><td>33%</td><td>$16.50</td><td>$33.00</td><td>$165.00</td><td>$330.00</td></tr>
        <tr><td>50%</td><td>$25.00</td><td>$50.00</td><td>$250.00</td><td>$500.00</td></tr>
        <tr><td>75%</td><td>$37.50</td><td>$75.00</td><td>$375.00</td><td>$750.00</td></tr>
      </tbody>
    </table>
  </div>

</div><!-- /pct-wrap -->

<script>
/* ---- Tab switching ---- */
function pctTab(e, id) {
  document.querySelectorAll('.pct-panel').forEach(function(p){ p.classList.remove('active'); });
  document.querySelectorAll('.pct-tabs button').forEach(function(b){ b.classList.remove('active'); });
  document.getElementById(id).classList.add('active');
  e.currentTarget.classList.add('active');
}

/* ---- Helpers ---- */
function fmt(n, decimals) {
  if (decimals === undefined) decimals = 2;
  return Number(n).toLocaleString('en-US', { minimumFractionDigits: decimals, maximumFractionDigits: decimals });
}
function showResult(el) { el.classList.add('visible'); }

/* ---- Tab 1: What is X% of Y? ---- */
function calcT1() {
  var pct = parseFloat(document.getElementById('t1-pct').value);
  var num = parseFloat(document.getElementById('t1-num').value);
  var res = document.getElementById('t1-result');
  if (isNaN(pct) || isNaN(num)) { alert('Please enter both a percentage and a number.'); return; }
  var answer = (pct / 100) * num;
  document.getElementById('t1-main').textContent = pct + '% of ' + fmt(num) + ' = ' + fmt(answer);
  document.getElementById('t1-formula').textContent = 'Formula: (' + pct + ' \u00F7 100) \u00D7 ' + num + ' = ' + fmt(answer);
  res.classList.remove('res-increase','res-decrease','res-zero');
  showResult(res);
}

/* ---- Tab 2: X is what % of Y? ---- */
function calcT2() {
  var x = parseFloat(document.getElementById('t2-x').value);
  var y = parseFloat(document.getElementById('t2-y').value);
  var res = document.getElementById('t2-result');
  if (isNaN(x) || isNaN(y)) { alert('Please enter both numbers.'); return; }
  if (y === 0) { alert('Y cannot be zero.'); return; }
  var answer = (x / y) * 100;
  document.getElementById('t2-main').textContent = fmt(x) + ' is ' + fmt(answer) + '% of ' + fmt(y);
  document.getElementById('t2-formula').textContent = 'Formula: (' + x + ' \u00F7 ' + y + ') \u00D7 100 = ' + fmt(answer) + '%';
  res.classList.remove('res-increase','res-decrease','res-zero');
  showResult(res);
}

/* ---- Tab 3: % Change ---- */
function calcT3() {
  var orig = parseFloat(document.getElementById('t3-orig').value);
  var nv   = parseFloat(document.getElementById('t3-new').value);
  var res  = document.getElementById('t3-result');
  if (isNaN(orig) || isNaN(nv)) { alert('Please enter both values.'); return; }
  if (orig === 0) { alert('Original value cannot be zero.'); return; }
  var change = ((nv - orig) / Math.abs(orig)) * 100;
  var direction = change > 0 ? 'Increase' : change < 0 ? 'Decrease' : 'No Change';
  document.getElementById('t3-main').textContent = direction + ': ' + fmt(Math.abs(change)) + '%';
  document.getElementById('t3-formula').textContent = 'Formula: ((' + nv + ' \u2212 ' + orig + ') \u00F7 |' + orig + '|) \u00D7 100 = ' + (change >= 0 ? '+' : '') + fmt(change) + '%';
  res.classList.remove('res-increase','res-decrease','res-zero');
  if (change > 0)      res.classList.add('res-increase');
  else if (change < 0) res.classList.add('res-decrease');
  else                 res.classList.add('res-zero');
  showResult(res);
}

/* ---- Tab 4: Tip Calculator ---- */
function t4SliderUpdate() {
  var v = document.getElementById('t4-tip-slider').value;
  document.getElementById('t4-tip-display').textContent = v + '%';
  calcT4();
}
function t4PeopleUpdate() {
  var v = parseInt(document.getElementById('t4-people-slider').value);
  document.getElementById('t4-people-display').textContent = v === 1 ? '1 person' : v + ' people';
  calcT4();
}
function calcT4() {
  var bill   = parseFloat(document.getElementById('t4-bill').value);
  var tipPct = parseFloat(document.getElementById('t4-tip-slider').value);
  var people = parseInt(document.getElementById('t4-people-slider').value);
  var res    = document.getElementById('t4-result');
  if (isNaN(bill) || bill <= 0) { res.classList.remove('visible'); return; }
  var tipAmt   = bill * (tipPct / 100);
  var total    = bill + tipAmt;
  var perPerson = total / people;
  document.getElementById('t4-tip-amt').textContent    = '$' + fmt(tipAmt);
  document.getElementById('t4-total').textContent      = '$' + fmt(total);
  document.getElementById('t4-per-person').textContent = '$' + fmt(perPerson);
  res.classList.add('visible');
}

/* ---- Tab 5: Discount Calculator ---- */
function t5SliderUpdate() {
  var v = document.getElementById('t5-disc-slider').value;
  document.getElementById('t5-disc-display').textContent = v + '%';
  calcT5();
}
function calcT5() {
  var price   = parseFloat(document.getElementById('t5-price').value);
  var discPct = parseFloat(document.getElementById('t5-disc-slider').value);
  var res     = document.getElementById('t5-result');
  if (isNaN(price) || price <= 0) { res.classList.remove('visible'); return; }
  var discAmt  = price * (discPct / 100);
  var final    = price - discAmt;
  document.getElementById('t5-disc-amt').textContent = '$' + fmt(discAmt);
  document.getElementById('t5-final').textContent    = '$' + fmt(final);
  document.getElementById('t5-save').textContent     = '$' + fmt(discAmt);
  res.classList.add('visible');
}
</script>

## Related Tools

- Create a monthly budget → [Budget Planner](/tools/budget-planner/)
- Calculate compound interest → [Compound Interest Calculator](/tools/compound-interest-calculator/)
- Estimate your tax bracket → [Tax Bracket Calculator](/tools/tax-bracket-calculator/)

## Related Articles

- [Best Credit Cards 2026: Complete Comparison Guide by Category](/posts/best-credit-cards-2026/)
- [How to Use ChatGPT for Data Analysis 2026](/posts/how-to-use-chatgpt-for-data-analysis-2026/)
- [Excel Skills That Will Double Your Salary](/posts/excel-skills-double-salary/)
