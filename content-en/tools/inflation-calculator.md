---
title: "Inflation Calculator | See How Prices Change Over Time"
date: 2026-05-16
draft: false
slug: "inflation-calculator"
description: "Calculate how inflation affects your purchasing power over time. See what today's money will be worth in the future, or what past prices equal in today's dollars."
categories: ["Free Tools"]
tags: ["inflation", "purchasing power", "calculator", "cost of living", "money"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/inflation-calculator.png"
  alt: "Inflation Calculator | See How Prices Change Over Time"
  relative: false
---

*Disclosure: Some links on this page may be affiliate links. We may earn a commission at no extra cost to you if you make a purchase through these links. We only recommend tools and resources we genuinely believe in.*

# Inflation Calculator

Inflation silently erodes the value of your money every year. Whether you want to see what a sum of money will be worth in the future, or understand what a price from the past equals in today's dollars, this calculator gives you a clear, honest picture of purchasing power over time.

<div id="inflation-calc-root" style="font-family: system-ui, -apple-system, sans-serif; max-width: 760px; margin: 2rem auto; color: #1c1917;">

  <!-- Mode Toggle -->
  <div style="display: flex; background: #fef3c7; border-radius: 10px; padding: 4px; margin-bottom: 1.5rem; gap: 4px;">
    <button id="btn-future" onclick="setMode('future')"
      style="flex:1; padding: 10px 16px; border: none; border-radius: 7px; cursor: pointer; font-size: 0.95rem; font-weight: 600; background: #d97706; color: #fff; transition: all 0.2s;">
      Future Value
    </button>
    <button id="btn-past" onclick="setMode('past')"
      style="flex:1; padding: 10px 16px; border: none; border-radius: 7px; cursor: pointer; font-size: 0.95rem; font-weight: 600; background: transparent; color: #92400e; transition: all 0.2s;">
      Past Value (Historical CPI)
    </button>
  </div>

  <!-- Mode 1: Future Value -->
  <div id="panel-future">
    <div style="background: #fffbeb; border: 1.5px solid #fde68a; border-radius: 12px; padding: 1.5rem; margin-bottom: 1.5rem;">
      <h2 style="margin: 0 0 1.25rem; font-size: 1.1rem; color: #92400e;">Future Value Settings</h2>

      <div style="margin-bottom: 1.25rem;">
        <label style="display:block; font-weight:600; margin-bottom:6px; color:#44403c;">
          Current Amount
        </label>
        <div style="display:flex; align-items:center; gap:8px;">
          <span style="font-size:1.2rem; color:#d97706; font-weight:700;">$</span>
          <input id="fv-amount" type="number" value="1000" min="1" max="10000000" step="1"
            oninput="calcFuture()"
            style="width:160px; padding:8px 12px; border:1.5px solid #fcd34d; border-radius:7px; font-size:1rem; background:#fff; color:#1c1917; outline:none;">
        </div>
      </div>

      <div style="margin-bottom: 1.25rem;">
        <label style="display:flex; justify-content:space-between; font-weight:600; margin-bottom:6px; color:#44403c;">
          <span>Annual Inflation Rate</span>
          <span id="fv-rate-display" style="color:#d97706;">3.0%</span>
        </label>
        <input id="fv-rate" type="range" min="1" max="10" step="0.5" value="3"
          oninput="document.getElementById('fv-rate-display').textContent=parseFloat(this.value).toFixed(1)+'%'; calcFuture();"
          style="width:100%; accent-color:#d97706; cursor:pointer;">
        <div style="display:flex; justify-content:space-between; font-size:0.75rem; color:#a8a29e; margin-top:3px;">
          <span>1%</span><span>5%</span><span>10%</span>
        </div>
      </div>

      <div>
        <label style="display:flex; justify-content:space-between; font-weight:600; margin-bottom:6px; color:#44403c;">
          <span>Time Period</span>
          <span id="fv-years-display" style="color:#d97706;">10 years</span>
        </label>
        <input id="fv-years" type="range" min="1" max="40" step="1" value="10"
          oninput="document.getElementById('fv-years-display').textContent=this.value+' year'+(this.value==1?'':'s'); calcFuture();"
          style="width:100%; accent-color:#d97706; cursor:pointer;">
        <div style="display:flex; justify-content:space-between; font-size:0.75rem; color:#a8a29e; margin-top:3px;">
          <span>1 yr</span><span>20 yrs</span><span>40 yrs</span>
        </div>
      </div>
    </div>

    <!-- Future Results -->
    <div id="fv-results" style="background:#fff; border:1.5px solid #fde68a; border-radius:12px; padding:1.5rem; margin-bottom:1.5rem;">
      <h2 style="margin:0 0 1rem; font-size:1.05rem; color:#92400e;">Results</h2>
      <div style="display:grid; grid-template-columns:repeat(auto-fit,minmax(190px,1fr)); gap:1rem; margin-bottom:1.25rem;">
        <div style="background:#fffbeb; border-radius:9px; padding:1rem; text-align:center;">
          <div style="font-size:0.8rem; color:#a8a29e; margin-bottom:4px;">Future Equivalent Price</div>
          <div id="fv-future-price" style="font-size:1.6rem; font-weight:700; color:#d97706;">$1,344</div>
        </div>
        <div style="background:#fffbeb; border-radius:9px; padding:1rem; text-align:center;">
          <div style="font-size:0.8rem; color:#a8a29e; margin-bottom:4px;">Purchasing Power Lost</div>
          <div id="fv-power-lost" style="font-size:1.6rem; font-weight:700; color:#dc2626;">25.6%</div>
        </div>
        <div style="background:#fffbeb; border-radius:9px; padding:1rem; text-align:center;">
          <div style="font-size:0.8rem; color:#a8a29e; margin-bottom:4px;">Needed to Maintain Power</div>
          <div id="fv-maintain" style="font-size:1.6rem; font-weight:700; color:#16a34a;">$1,344</div>
        </div>
      </div>

      <!-- Visual Bar -->
      <div style="margin-bottom:0.5rem;">
        <div style="display:flex; justify-content:space-between; font-size:0.8rem; color:#78716c; margin-bottom:6px;">
          <span>Today's $1,000</span>
          <span id="fv-bar-label">Future purchasing power</span>
        </div>
        <div style="background:#e5e7eb; border-radius:99px; height:22px; overflow:hidden; position:relative;">
          <div id="fv-bar-fill" style="height:100%; background:linear-gradient(90deg,#d97706,#f59e0b); border-radius:99px; transition:width 0.4s; width:74.4%; display:flex; align-items:center; padding-left:10px;">
            <span id="fv-bar-pct" style="font-size:0.75rem; font-weight:700; color:#fff;">74.4%</span>
          </div>
        </div>
        <div style="font-size:0.75rem; color:#a8a29e; margin-top:4px;">
          Your money retains <span id="fv-retain-pct" style="color:#d97706; font-weight:600;">74.4%</span> of today's purchasing power after <span id="fv-retain-years">10</span> years at <span id="fv-retain-rate">3.0%</span> inflation.
        </div>
      </div>
    </div>
  </div>

  <!-- Mode 2: Past Value -->
  <div id="panel-past" style="display:none;">
    <div style="background:#fffbeb; border:1.5px solid #fde68a; border-radius:12px; padding:1.5rem; margin-bottom:1.5rem;">
      <h2 style="margin:0 0 1.25rem; font-size:1.1rem; color:#92400e;">Historical CPI Settings</h2>

      <div style="margin-bottom:1.25rem;">
        <label style="display:block; font-weight:600; margin-bottom:6px; color:#44403c;">
          Amount in Past Year
        </label>
        <div style="display:flex; align-items:center; gap:8px;">
          <span style="font-size:1.2rem; color:#d97706; font-weight:700;">$</span>
          <input id="pv-amount" type="number" value="1000" min="1" max="10000000" step="1"
            oninput="calcPast()"
            style="width:160px; padding:8px 12px; border:1.5px solid #fcd34d; border-radius:7px; font-size:1rem; background:#fff; color:#1c1917; outline:none;">
        </div>
      </div>

      <div>
        <label style="display:flex; justify-content:space-between; font-weight:600; margin-bottom:6px; color:#44403c;">
          <span>Year</span>
          <span id="pv-year-display" style="color:#d97706;">1990</span>
        </label>
        <input id="pv-year" type="range" min="1960" max="2025" step="1" value="1990"
          oninput="document.getElementById('pv-year-display').textContent=this.value; calcPast();"
          style="width:100%; accent-color:#d97706; cursor:pointer;">
        <div style="display:flex; justify-content:space-between; font-size:0.75rem; color:#a8a29e; margin-top:3px;">
          <span>1960</span><span>1990</span><span>2025</span>
        </div>
      </div>
    </div>

    <!-- Past Results -->
    <div id="pv-results" style="background:#fff; border:1.5px solid #fde68a; border-radius:12px; padding:1.5rem; margin-bottom:1.5rem;">
      <h2 style="margin:0 0 1rem; font-size:1.05rem; color:#92400e;">Results</h2>
      <div style="display:grid; grid-template-columns:repeat(auto-fit,minmax(190px,1fr)); gap:1rem; margin-bottom:1.25rem;">
        <div style="background:#fffbeb; border-radius:9px; padding:1rem; text-align:center;">
          <div style="font-size:0.8rem; color:#a8a29e; margin-bottom:4px;">Equivalent in Today's Dollars</div>
          <div id="pv-today-value" style="font-size:1.6rem; font-weight:700; color:#d97706;">$2,131</div>
        </div>
        <div style="background:#fffbeb; border-radius:9px; padding:1rem; text-align:center;">
          <div style="font-size:0.8rem; color:#a8a29e; margin-bottom:4px;">Total Inflation Since <span id="pv-since-year-label">1990</span></div>
          <div id="pv-total-inflation" style="font-size:1.6rem; font-weight:700; color:#dc2626;">113.1%</div>
        </div>
        <div style="background:#fffbeb; border-radius:9px; padding:1rem; text-align:center;">
          <div style="font-size:0.8rem; color:#a8a29e; margin-bottom:4px;">Avg Annual Rate</div>
          <div id="pv-avg-rate" style="font-size:1.6rem; font-weight:700; color:#78716c;">3.2%</div>
        </div>
      </div>
      <div style="font-size:0.9rem; color:#78716c; background:#fffbeb; border-radius:8px; padding:0.75rem 1rem;">
        <strong style="color:#92400e;">Note:</strong> Based on approximate US CPI data. Values are estimates for educational purposes.
      </div>
    </div>
  </div>

  <!-- Year-by-Year Table (shared) -->
  <div style="background:#fff; border:1.5px solid #fde68a; border-radius:12px; padding:1.5rem; margin-bottom:1.5rem;">
    <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:1rem; flex-wrap:wrap; gap:8px;">
      <h2 style="margin:0; font-size:1.05rem; color:#92400e;">Year-by-Year Value Erosion</h2>
      <button id="expand-btn" onclick="toggleTable()"
        style="padding:6px 14px; background:#d97706; color:#fff; border:none; border-radius:6px; cursor:pointer; font-size:0.85rem; font-weight:600;">
        Show All Years
      </button>
    </div>
    <div style="overflow-x:auto;">
      <table id="yby-table" style="width:100%; border-collapse:collapse; font-size:0.875rem;">
        <thead>
          <tr style="background:#fef3c7;">
            <th style="padding:8px 12px; text-align:left; color:#92400e; font-weight:700; border-bottom:2px solid #fde68a;">Year</th>
            <th style="padding:8px 12px; text-align:right; color:#92400e; font-weight:700; border-bottom:2px solid #fde68a;">Value of Original $</th>
            <th style="padding:8px 12px; text-align:right; color:#92400e; font-weight:700; border-bottom:2px solid #fde68a;">Purchasing Power</th>
            <th style="padding:8px 12px; text-align:right; color:#92400e; font-weight:700; border-bottom:2px solid #fde68a;">Power Lost</th>
          </tr>
        </thead>
        <tbody id="yby-body">
        </tbody>
      </table>
    </div>
  </div>

  <!-- Beat Inflation Panel -->
  <div style="background:linear-gradient(135deg,#fffbeb 0%,#fef3c7 100%); border:2px solid #f59e0b; border-radius:12px; padding:1.5rem; margin-bottom:1.5rem;">
    <h2 style="margin:0 0 0.75rem; font-size:1.05rem; color:#92400e;">Beat Inflation: Required Investment Return</h2>
    <p style="margin:0 0 1rem; font-size:0.9rem; color:#78716c;">
      To maintain your purchasing power, your investments need to earn at least as much as the inflation rate. To actually grow your wealth in real terms, you need to exceed it.
    </p>
    <div style="display:grid; grid-template-columns:repeat(auto-fit,minmax(160px,1fr)); gap:1rem; margin-bottom:1rem;">
      <div style="background:#fff; border-radius:9px; padding:1rem; text-align:center; border:1px solid #fde68a;">
        <div style="font-size:0.78rem; color:#a8a29e; margin-bottom:4px;">Break Even (keep up)</div>
        <div id="beat-breakeven" style="font-size:1.4rem; font-weight:700; color:#d97706;">3.0%</div>
        <div style="font-size:0.72rem; color:#a8a29e;">annual return</div>
      </div>
      <div style="background:#fff; border-radius:9px; padding:1rem; text-align:center; border:1px solid #fde68a;">
        <div style="font-size:0.78rem; color:#a8a29e; margin-bottom:4px;">Modest Growth (+2%)</div>
        <div id="beat-modest" style="font-size:1.4rem; font-weight:700; color:#16a34a;">5.0%</div>
        <div style="font-size:0.72rem; color:#a8a29e;">annual return</div>
      </div>
      <div style="background:#fff; border-radius:9px; padding:1rem; text-align:center; border:1px solid #fde68a;">
        <div style="font-size:0.78rem; color:#a8a29e; margin-bottom:4px;">Strong Growth (+5%)</div>
        <div id="beat-strong" style="font-size:1.4rem; font-weight:700; color:#0284c7;">8.0%</div>
        <div style="font-size:0.72rem; color:#a8a29e;">annual return</div>
      </div>
    </div>
    <p style="margin:0; font-size:0.875rem; color:#78716c;">
      Want to see how compound growth can outpace inflation?
      <a href="/tools/compound-interest-calculator/" style="color:#d97706; font-weight:600; text-decoration:underline;">Try the Compound Interest Calculator &rarr;</a>
    </p>
  </div>

</div>

<script>
(function() {

  // --- Historical US CPI data (approximate, base = index value) ---
  // Source: approximate BLS CPI-U annual average values
  var CPI = {
    1960: 29.6, 1961: 29.9, 1962: 30.2, 1963: 30.6, 1964: 31.0,
    1965: 31.5, 1966: 32.5, 1967: 33.4, 1968: 34.8, 1969: 36.7,
    1970: 38.8, 1971: 40.5, 1972: 41.8, 1973: 44.4, 1974: 49.3,
    1975: 53.8, 1976: 56.9, 1977: 60.6, 1978: 65.2, 1979: 72.6,
    1980: 82.4, 1981: 90.9, 1982: 96.5, 1983: 99.6, 1984: 103.9,
    1985: 107.6, 1986: 109.6, 1987: 113.6, 1988: 118.3, 1989: 124.0,
    1990: 130.7, 1991: 136.2, 1992: 140.3, 1993: 144.5, 1994: 148.2,
    1995: 152.4, 1996: 156.9, 1997: 160.5, 1998: 163.0, 1999: 166.6,
    2000: 172.2, 2001: 177.1, 2002: 179.9, 2003: 184.0, 2004: 188.9,
    2005: 195.3, 2006: 201.6, 2007: 207.3, 2008: 215.3, 2009: 214.5,
    2010: 218.1, 2011: 224.9, 2012: 229.6, 2013: 233.0, 2014: 236.7,
    2015: 237.0, 2016: 240.0, 2017: 245.1, 2018: 251.1, 2019: 255.7,
    2020: 258.8, 2021: 270.9, 2022: 292.7, 2023: 304.7, 2024: 314.2,
    2025: 320.0
  };

  var currentMode = 'future';
  var tableExpanded = false;

  window.setMode = function(mode) {
    currentMode = mode;
    var isFuture = mode === 'future';
    document.getElementById('panel-future').style.display = isFuture ? '' : 'none';
    document.getElementById('panel-past').style.display = isFuture ? 'none' : '';
    document.getElementById('btn-future').style.background = isFuture ? '#d97706' : 'transparent';
    document.getElementById('btn-future').style.color = isFuture ? '#fff' : '#92400e';
    document.getElementById('btn-past').style.background = isFuture ? 'transparent' : '#d97706';
    document.getElementById('btn-past').style.color = isFuture ? '#92400e' : '#fff';
    tableExpanded = false;
    document.getElementById('expand-btn').textContent = 'Show All Years';
    if (isFuture) {
      calcFuture();
    } else {
      calcPast();
    }
  };

  function fmt(n) {
    return '$' + n.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
  }

  function fmtPct(n) {
    return (n >= 0 ? '+' : '') + n.toFixed(1) + '%';
  }

  window.calcFuture = function() {
    var amount = parseFloat(document.getElementById('fv-amount').value) || 1000;
    var rate = parseFloat(document.getElementById('fv-rate').value) / 100;
    var years = parseInt(document.getElementById('fv-years').value);

    var futurePrice = amount * Math.pow(1 + rate, years);
    var powerRetained = (amount / futurePrice) * 100;
    var powerLost = 100 - powerRetained;

    document.getElementById('fv-future-price').textContent = fmt(futurePrice);
    document.getElementById('fv-power-lost').textContent = powerLost.toFixed(1) + '%';
    document.getElementById('fv-maintain').textContent = fmt(futurePrice);

    // Bar
    var pct = Math.max(0, Math.min(100, powerRetained));
    document.getElementById('fv-bar-fill').style.width = pct.toFixed(1) + '%';
    document.getElementById('fv-bar-pct').textContent = pct.toFixed(1) + '%';
    document.getElementById('fv-bar-label').textContent = 'Future purchasing power';
    document.getElementById('fv-retain-pct').textContent = pct.toFixed(1) + '%';
    document.getElementById('fv-retain-years').textContent = years;
    document.getElementById('fv-retain-rate').textContent = (rate * 100).toFixed(1) + '%';

    // Beat inflation
    var rateDisplay = (rate * 100).toFixed(1) + '%';
    document.getElementById('beat-breakeven').textContent = (rate * 100).toFixed(1) + '%';
    document.getElementById('beat-modest').textContent = (rate * 100 + 2).toFixed(1) + '%';
    document.getElementById('beat-strong').textContent = (rate * 100 + 5).toFixed(1) + '%';

    // Table
    buildTable(amount, rate, years, null, null);
  };

  window.calcPast = function() {
    var amount = parseFloat(document.getElementById('pv-amount').value) || 1000;
    var pastYear = parseInt(document.getElementById('pv-year').value);
    var currentYear = 2025;

    document.getElementById('pv-since-year-label').textContent = pastYear;
    document.getElementById('pv-year-display').textContent = pastYear;

    var cpiPast = CPI[pastYear] || CPI[1990];
    var cpiNow = CPI[currentYear];
    var factor = cpiNow / cpiPast;
    var todayValue = amount * factor;
    var totalInflation = (factor - 1) * 100;
    var numYears = currentYear - pastYear;
    var avgRate = numYears > 0 ? (Math.pow(factor, 1 / numYears) - 1) * 100 : 0;

    document.getElementById('pv-today-value').textContent = fmt(todayValue);
    document.getElementById('pv-total-inflation').textContent = totalInflation.toFixed(1) + '%';
    document.getElementById('pv-avg-rate').textContent = avgRate.toFixed(1) + '%';

    // Beat inflation
    document.getElementById('beat-breakeven').textContent = avgRate.toFixed(1) + '%';
    document.getElementById('beat-modest').textContent = (avgRate + 2).toFixed(1) + '%';
    document.getElementById('beat-strong').textContent = (avgRate + 5).toFixed(1) + '%';

    // Table: show year-by-year from pastYear to 2025 using CPI
    buildTableCPI(amount, pastYear, cpiPast);
  };

  function buildTable(amount, rate, totalYears, pastYear, cpiBase) {
    var rows = [];
    for (var y = 1; y <= totalYears; y++) {
      var val = amount / Math.pow(1 + rate, y);
      var pctRetained = (val / amount) * 100;
      var pctLost = 100 - pctRetained;
      rows.push({ year: 'Year ' + y, value: val, retained: pctRetained, lost: pctLost });
    }
    renderTable(rows, amount);
  }

  function buildTableCPI(amount, startYear, cpiBase) {
    var rows = [];
    var endYear = 2025;
    for (var y = startYear + 1; y <= endYear; y++) {
      var cpiY = CPI[y] || CPI[endYear];
      var factor = cpiBase / cpiY;
      var val = amount * factor;
      var pctRetained = (val / amount) * 100;
      var pctLost = 100 - pctRetained;
      rows.push({ year: String(y), value: val, retained: pctRetained, lost: pctLost });
    }
    renderTable(rows, amount);
  }

  function renderTable(rows, amount) {
    var tbody = document.getElementById('yby-body');
    tbody.innerHTML = '';
    var limit = tableExpanded ? rows.length : Math.min(10, rows.length);
    for (var i = 0; i < limit; i++) {
      var r = rows[i];
      var tr = document.createElement('tr');
      tr.style.borderBottom = '1px solid #fef3c7';
      if (i % 2 === 0) tr.style.background = '#fffbeb';
      var barW = Math.max(0, Math.min(100, r.retained));
      tr.innerHTML =
        '<td style="padding:8px 12px; color:#44403c; font-weight:500;">' + r.year + '</td>' +
        '<td style="padding:8px 12px; text-align:right; font-family:monospace; color:#44403c;">' + fmt(r.value) + '</td>' +
        '<td style="padding:8px 12px; text-align:right;">' +
          '<div style="display:flex; align-items:center; gap:6px; justify-content:flex-end;">' +
            '<div style="width:80px; background:#e5e7eb; border-radius:99px; height:8px; overflow:hidden;">' +
              '<div style="width:' + barW.toFixed(1) + '%; height:100%; background:#d97706; border-radius:99px;"></div>' +
            '</div>' +
            '<span style="font-size:0.85rem; color:#78716c; width:42px; text-align:right;">' + r.retained.toFixed(1) + '%</span>' +
          '</div>' +
        '</td>' +
        '<td style="padding:8px 12px; text-align:right; color:#dc2626; font-weight:600;">' + r.lost.toFixed(1) + '%</td>';
      tbody.appendChild(tr);
    }
    var expandBtn = document.getElementById('expand-btn');
    if (rows.length <= 10) {
      expandBtn.style.display = 'none';
    } else {
      expandBtn.style.display = '';
      expandBtn.textContent = tableExpanded ? 'Show Less' : 'Show All ' + rows.length + ' Years';
    }
    // Store rows for toggle
    tbody._allRows = rows;
    tbody._amount = amount;
  }

  window.toggleTable = function() {
    tableExpanded = !tableExpanded;
    var tbody = document.getElementById('yby-body');
    renderTable(tbody._allRows, tbody._amount);
  };

  // Init
  calcFuture();

})();
</script>

## How to Protect Against Inflation

Inflation is a permanent feature of modern economies. Here are four evidence-based strategies to protect your purchasing power:

**1. Invest in assets that historically outpace inflation.**
Broad stock market index funds have historically returned around 7–10% annually before inflation adjustments — well above the long-run US inflation rate of roughly 3%. Holding cash long-term is a guaranteed losing strategy in real terms.

**2. Consider I Bonds and TIPS.**
US Treasury Inflation-Protected Securities (TIPS) and Series I Savings Bonds are explicitly designed to rise with inflation. They won't make you rich, but they preserve purchasing power with low risk — especially useful for emergency funds or short-term savings.

**3. Real assets provide a natural hedge.**
Real estate, commodities, and infrastructure tend to rise in nominal value alongside inflation, though they carry their own risks and illiquidity. REITs (Real Estate Investment Trusts) offer exposure without direct ownership.

**4. Avoid holding large amounts in low-yield savings accounts.**
Even a high-yield savings account at 4–5% barely keeps pace with moderate inflation. Money that won't be needed for 5+ years should generally be invested, not saved. Review your allocation regularly as interest rates change.

## Related Tools

- Calculate compound interest: [Compound Interest Calculator](/tools/compound-interest-calculator/)
- Plan for retirement: [Retirement Calculator](/tools/retirement-calculator/)
- Plan for early retirement: [FIRE Calculator](/tools/fire-calculator/)
- Calculate your net worth: [Net Worth Calculator](/tools/net-worth-calculator/)
