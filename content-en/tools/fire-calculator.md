---
title: "FIRE Calculator | When Can You Retire Early?"
date: 2026-05-16
draft: false
slug: "fire-calculator"
description: "Free FIRE calculator. Enter your income, expenses, and savings to find your Financial Independence number, years to early retirement, and savings rate impact."
categories: ["Free Tools"]
tags: ["FIRE calculator", "financial independence", "early retirement", "personal finance", "calculator", "retirement"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/fire-calculator.png"
  alt: "FIRE Calculator | When Can You Retire Early?"
  relative: false
---

*This article contains affiliate links. We may earn a commission at no extra cost to you.*

# FIRE Calculator

Enter your numbers below to find your **Financial Independence number**, years to early retirement, and see exactly how your savings rate affects your timeline.

<div id="fire-calc" style="max-width:760px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;">

<!-- INPUTS -->
<div style="padding:28px;border:2px solid #7c3aed;border-radius:12px;background:#faf5ff;margin-bottom:20px;">

<h2 style="margin:0 0 24px 0;font-size:20px;color:#7c3aed;">Your Financial Details</h2>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:20px;">

<div>
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:6px;text-transform:uppercase;letter-spacing:0.05em;">Current Age</label>
<input type="number" id="fireAge" min="18" max="70" step="1" value="30" oninput="calcFIRE()" style="width:100%;padding:10px 12px;border:1.5px solid #c4b5fd;border-radius:8px;font-size:16px;box-sizing:border-box;background:#fff;color:#1e293b;">
</div>

<div>
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:6px;text-transform:uppercase;letter-spacing:0.05em;">Annual Income ($)</label>
<input type="number" id="fireIncome" min="0" step="1000" value="80000" oninput="calcFIRE()" style="width:100%;padding:10px 12px;border:1.5px solid #c4b5fd;border-radius:8px;font-size:16px;box-sizing:border-box;background:#fff;color:#1e293b;">
</div>

<div>
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:6px;text-transform:uppercase;letter-spacing:0.05em;">Annual Expenses ($)</label>
<input type="number" id="fireExpenses" min="0" step="1000" value="50000" oninput="calcFIRE()" style="width:100%;padding:10px 12px;border:1.5px solid #c4b5fd;border-radius:8px;font-size:16px;box-sizing:border-box;background:#fff;color:#1e293b;">
</div>

<div>
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:6px;text-transform:uppercase;letter-spacing:0.05em;">Current Savings / Investments ($)</label>
<input type="number" id="fireSavings" min="0" step="1000" value="50000" oninput="calcFIRE()" style="width:100%;padding:10px 12px;border:1.5px solid #c4b5fd;border-radius:8px;font-size:16px;box-sizing:border-box;background:#fff;color:#1e293b;">
</div>

</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:8px;text-transform:uppercase;letter-spacing:0.05em;">Expected Annual Return: <span id="fireReturnVal" style="color:#7c3aed;font-size:15px;">7.0%</span></label>
<input type="range" id="fireReturn" min="3" max="12" step="0.5" value="7" oninput="calcFIRE()" style="width:100%;accent-color:#7c3aed;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#94a3b8;margin-top:2px;"><span>3%</span><span>12%</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:8px;text-transform:uppercase;letter-spacing:0.05em;">Safe Withdrawal Rate (SWR): <span id="fireSWRVal" style="color:#7c3aed;font-size:15px;">4.00%</span></label>
<input type="range" id="fireSWR" min="2" max="5" step="0.25" value="4" oninput="calcFIRE()" style="width:100%;accent-color:#7c3aed;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#94a3b8;margin-top:2px;"><span>2% (Conservative)</span><span>5% (Aggressive)</span></div>
<div style="font-size:12px;color:#94a3b8;margin-top:2px;">The 4% rule is the most widely used guideline.</div>
</div>

<div style="margin-bottom:4px;">
<label style="display:block;font-size:13px;font-weight:600;color:#64748b;margin-bottom:8px;text-transform:uppercase;letter-spacing:0.05em;">Annual Savings Increase: <span id="fireSavIncVal" style="color:#7c3aed;font-size:15px;">2.0%</span></label>
<input type="range" id="fireSavInc" min="0" max="5" step="0.5" value="2" oninput="calcFIRE()" style="width:100%;accent-color:#7c3aed;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#94a3b8;margin-top:2px;"><span>0%</span><span>5% (raises + optimization)</span></div>
</div>

</div>

<!-- RESULTS PANEL -->
<div id="fireResults" style="padding:28px;border:2px solid #7c3aed;border-radius:12px;background:linear-gradient(135deg,#7c3aed 0%,#6d28d9 100%);color:white;margin-bottom:20px;">

<div style="text-align:center;margin-bottom:24px;">
<div style="font-size:13px;letter-spacing:0.1em;opacity:0.85;margin-bottom:6px;text-transform:uppercase;">Your FIRE Number</div>
<div id="fireNumber" style="font-size:52px;font-weight:800;letter-spacing:-1px;">$1,250,000</div>
<div style="font-size:13px;opacity:0.75;margin-top:4px;">Annual expenses &divide; Safe withdrawal rate</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:12px;margin-bottom:20px;">
<div style="background:rgba(255,255,255,0.15);border-radius:10px;padding:14px;text-align:center;">
<div style="font-size:11px;opacity:0.8;margin-bottom:4px;text-transform:uppercase;letter-spacing:0.05em;">Years to FIRE</div>
<div id="fireYears" style="font-size:20px;font-weight:700;">14y 3m</div>
</div>
<div style="background:rgba(255,255,255,0.15);border-radius:10px;padding:14px;text-align:center;">
<div style="font-size:11px;opacity:0.8;margin-bottom:4px;text-transform:uppercase;letter-spacing:0.05em;">FIRE Age</div>
<div id="fireAgeResult" style="font-size:20px;font-weight:700;">Age 44</div>
</div>
<div style="background:rgba(255,255,255,0.15);border-radius:10px;padding:14px;text-align:center;">
<div style="font-size:11px;opacity:0.8;margin-bottom:4px;text-transform:uppercase;letter-spacing:0.05em;">Savings Rate</div>
<div id="fireSavRate" style="font-size:20px;font-weight:700;">37.5%</div>
</div>
<div style="background:rgba(255,255,255,0.15);border-radius:10px;padding:14px;text-align:center;">
<div style="font-size:11px;opacity:0.8;margin-bottom:4px;text-transform:uppercase;letter-spacing:0.05em;">Monthly Savings</div>
<div id="fireMonthly" style="font-size:20px;font-weight:700;">$2,500</div>
</div>
</div>

<!-- PROGRESS BAR -->
<div>
<div style="display:flex;justify-content:space-between;font-size:13px;opacity:0.85;margin-bottom:6px;">
<span>Progress to FIRE</span>
<span id="fireProgressPct">4%</span>
</div>
<div style="background:rgba(255,255,255,0.2);border-radius:999px;height:12px;overflow:hidden;">
<div id="fireProgressBar" style="background:#a78bfa;height:100%;border-radius:999px;transition:width 0.4s ease;width:4%;"></div>
</div>
<div style="display:flex;justify-content:space-between;font-size:12px;opacity:0.7;margin-top:5px;">
<span id="fireCurrSavDisplay">$50,000 now</span>
<span id="fireNumDisplay">$1,250,000 goal</span>
</div>
</div>

</div>

<!-- FIRE VARIANTS -->
<div style="padding:24px;border:2px solid #c4b5fd;border-radius:12px;background:#fff;margin-bottom:20px;">
<h3 style="margin:0 0 16px 0;font-size:16px;color:#7c3aed;font-weight:700;">FIRE Variants</h3>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;" id="fireVariants">

<div id="varLean" style="padding:16px;border-radius:10px;border:2px solid #e9d5ff;background:#f5f3ff;">
<div style="font-weight:700;font-size:14px;color:#6d28d9;margin-bottom:4px;">Lean FIRE</div>
<div style="font-size:11px;color:#94a3b8;margin-bottom:8px;">Expenses &times; 0.8</div>
<div id="leanNum" style="font-size:22px;font-weight:800;color:#1e293b;">$1,000,000</div>
<div id="leanYears" style="font-size:13px;color:#64748b;margin-top:4px;">12 years 1 month</div>
</div>

<div id="varRegular" style="padding:16px;border-radius:10px;border:2px solid #7c3aed;background:#ede9fe;">
<div style="display:flex;align-items:center;gap:6px;margin-bottom:4px;">
<div style="font-weight:700;font-size:14px;color:#6d28d9;">Regular FIRE</div>
<span style="background:#7c3aed;color:white;font-size:10px;padding:1px 6px;border-radius:999px;font-weight:600;">YOUR TARGET</span>
</div>
<div style="font-size:11px;color:#94a3b8;margin-bottom:8px;">Your current expenses</div>
<div id="regNum" style="font-size:22px;font-weight:800;color:#1e293b;">$1,250,000</div>
<div id="regYears" style="font-size:13px;color:#64748b;margin-top:4px;">14 years 3 months</div>
</div>

<div id="varFat" style="padding:16px;border-radius:10px;border:2px solid #e9d5ff;background:#f5f3ff;">
<div style="font-weight:700;font-size:14px;color:#6d28d9;margin-bottom:4px;">Fat FIRE</div>
<div style="font-size:11px;color:#94a3b8;margin-bottom:8px;">Expenses &times; 1.5</div>
<div id="fatNum" style="font-size:22px;font-weight:800;color:#1e293b;">$1,875,000</div>
<div id="fatYears" style="font-size:13px;color:#64748b;margin-top:4px;">20 years 8 months</div>
</div>

<div id="varCoast" style="padding:16px;border-radius:10px;border:2px solid #e9d5ff;background:#f5f3ff;">
<div style="font-weight:700;font-size:14px;color:#6d28d9;margin-bottom:4px;">Coast FIRE</div>
<div style="font-size:11px;color:#94a3b8;margin-bottom:8px;">Stop saving, coast to 65</div>
<div id="coastNum" style="font-size:22px;font-weight:800;color:#1e293b;">$182,000</div>
<div id="coastStatus" style="font-size:13px;color:#64748b;margin-top:4px;">Need $132,000 more</div>
</div>

</div>
</div>

<!-- SAVINGS RATE IMPACT TABLE -->
<div style="padding:24px;border:2px solid #c4b5fd;border-radius:12px;background:#fff;margin-bottom:20px;">
<h3 style="margin:0 0 4px 0;font-size:16px;color:#7c3aed;font-weight:700;">Savings Rate Impact</h3>
<p style="margin:0 0 16px 0;font-size:13px;color:#64748b;">Years to FIRE at different savings rates (assuming same return rate)</p>
<div style="overflow-x:auto;">
<table id="savingsRateTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#f5f3ff;">
<th style="padding:10px 14px;text-align:left;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Savings Rate</th>
<th style="padding:10px 14px;text-align:left;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Annual Savings</th>
<th style="padding:10px 14px;text-align:left;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Years to FIRE</th>
<th style="padding:10px 14px;text-align:left;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">FIRE Age</th>
</tr>
</thead>
<tbody id="savingsRateBody"></tbody>
</table>
</div>
</div>

<!-- PROJECTION TABLE -->
<div style="border:2px solid #c4b5fd;border-radius:12px;overflow:hidden;margin-bottom:20px;">
<button onclick="toggleProjection()" style="width:100%;padding:16px 20px;background:#f5f3ff;border:none;text-align:left;font-size:15px;font-weight:700;color:#7c3aed;cursor:pointer;display:flex;justify-content:space-between;align-items:center;">
<span>Year-by-Year Projection</span>
<span id="projToggleIcon" style="font-size:18px;">+</span>
</button>
<div id="projectionTable" style="display:none;overflow-x:auto;">
<table style="width:100%;border-collapse:collapse;font-size:13px;">
<thead>
<tr style="background:#f5f3ff;">
<th style="padding:10px 14px;text-align:left;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Year</th>
<th style="padding:10px 14px;text-align:left;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Age</th>
<th style="padding:10px 14px;text-align:right;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Annual Savings</th>
<th style="padding:10px 14px;text-align:right;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Investment Returns</th>
<th style="padding:10px 14px;text-align:right;color:#6d28d9;font-weight:700;border-bottom:2px solid #c4b5fd;">Total Portfolio</th>
</tr>
</thead>
<tbody id="projectionBody"></tbody>
</table>
</div>
</div>

</div>

<script>
(function() {

function fmt(n) {
  if (n >= 1000000) return '$' + (n / 1000000).toFixed(2) + 'M';
  if (n >= 1000) return '$' + Math.round(n).toLocaleString();
  return '$' + Math.round(n).toLocaleString();
}

function fmtFull(n) {
  return '$' + Math.round(n).toLocaleString();
}

function yearsMonths(totalMonths) {
  if (totalMonths === Infinity || totalMonths > 600) return 'Never (expenses exceed income)';
  var y = Math.floor(totalMonths / 12);
  var m = Math.round(totalMonths % 12);
  if (m === 12) { y++; m = 0; }
  if (y === 0) return m + ' month' + (m !== 1 ? 's' : '');
  if (m === 0) return y + ' year' + (y !== 1 ? 's' : '');
  return y + ' year' + (y !== 1 ? 's' : '') + ' ' + m + ' month' + (m !== 1 ? 's' : '');
}

function simulateMonths(currentSavings, monthlyContrib, monthlyReturn, fireNumber, savIncRate) {
  var savings = currentSavings;
  var contrib = monthlyContrib;
  var monthsPerYear = 12;
  var annualIncrease = savIncRate / 100;
  for (var month = 1; month <= 600; month++) {
    if (month > 1 && (month - 1) % monthsPerYear === 0) {
      contrib *= (1 + annualIncrease);
    }
    savings = savings * (1 + monthlyReturn) + contrib;
    if (savings >= fireNumber) return month;
  }
  return Infinity;
}

function simulateMonthsFixed(currentSavings, monthlyContrib, monthlyReturn, fireNumber) {
  var savings = currentSavings;
  for (var month = 1; month <= 600; month++) {
    savings = savings * (1 + monthlyReturn) + monthlyContrib;
    if (savings >= fireNumber) return month;
  }
  return Infinity;
}

function calcFIRE() {
  var age = parseFloat(document.getElementById('fireAge').value) || 30;
  var income = parseFloat(document.getElementById('fireIncome').value) || 0;
  var expenses = parseFloat(document.getElementById('fireExpenses').value) || 0;
  var currentSavings = parseFloat(document.getElementById('fireSavings').value) || 0;
  var annualReturn = parseFloat(document.getElementById('fireReturn').value) / 100;
  var swr = parseFloat(document.getElementById('fireSWR').value) / 100;
  var savInc = parseFloat(document.getElementById('fireSavInc').value);

  // Update slider labels
  document.getElementById('fireReturnVal').textContent = parseFloat(document.getElementById('fireReturn').value).toFixed(1) + '%';
  document.getElementById('fireSWRVal').textContent = parseFloat(document.getElementById('fireSWR').value).toFixed(2) + '%';
  document.getElementById('fireSavIncVal').textContent = parseFloat(document.getElementById('fireSavInc').value).toFixed(1) + '%';

  var annualSavings = Math.max(0, income - expenses);
  var monthlyContrib = annualSavings / 12;
  var monthlyReturn = annualReturn / 12;
  var savingsRate = income > 0 ? (annualSavings / income * 100) : 0;

  // FIRE number (regular)
  var fireNumber = expenses / swr;

  // Months to FIRE
  var months = simulateMonths(currentSavings, monthlyContrib, monthlyReturn, fireNumber, savInc);
  var fireYearsNum = months === Infinity ? Infinity : months / 12;
  var fireAgeNum = months === Infinity ? null : age + fireYearsNum;

  // Progress
  var pct = fireNumber > 0 ? Math.min(100, (currentSavings / fireNumber) * 100) : 0;

  // Update results
  document.getElementById('fireNumber').textContent = fmt(fireNumber);
  document.getElementById('fireYears').textContent = months === Infinity ? 'N/A' : yearsMonths(months);
  document.getElementById('fireAgeResult').textContent = fireAgeNum === null ? 'N/A' : 'Age ' + Math.round(fireAgeNum);
  document.getElementById('fireSavRate').textContent = savingsRate.toFixed(1) + '%';
  document.getElementById('fireMonthly').textContent = fmtFull(monthlyContrib);
  document.getElementById('fireProgressPct').textContent = pct.toFixed(1) + '%';
  document.getElementById('fireProgressBar').style.width = pct.toFixed(1) + '%';
  document.getElementById('fireCurrSavDisplay').textContent = fmtFull(currentSavings) + ' now';
  document.getElementById('fireNumDisplay').textContent = fmtFull(fireNumber) + ' goal';

  // FIRE Variants
  var leanFireNum = (expenses * 0.8) / swr;
  var fatFireNum = (expenses * 1.5) / swr;

  var leanMonths = simulateMonths(currentSavings, monthlyContrib, monthlyReturn, leanFireNum, savInc);
  var fatMonths = simulateMonths(currentSavings, monthlyContrib, monthlyReturn, fatFireNum, savInc);

  // Coast FIRE: amount needed today so that invested at annual return it grows to fireNumber by age 65, with no more contributions
  var yearsToCoast = Math.max(0, 65 - age);
  var coastFireNum = fireNumber / Math.pow(1 + annualReturn, yearsToCoast);
  var coastDiff = coastFireNum - currentSavings;

  document.getElementById('leanNum').textContent = fmtFull(leanFireNum);
  document.getElementById('leanYears').textContent = leanMonths === Infinity ? 'Not achievable' : yearsMonths(leanMonths);
  document.getElementById('regNum').textContent = fmtFull(fireNumber);
  document.getElementById('regYears').textContent = months === Infinity ? 'Not achievable' : yearsMonths(months);
  document.getElementById('fatNum').textContent = fmtFull(fatFireNum);
  document.getElementById('fatYears').textContent = fatMonths === Infinity ? 'Not achievable' : yearsMonths(fatMonths);
  document.getElementById('coastNum').textContent = fmtFull(coastFireNum);
  if (coastDiff <= 0) {
    document.getElementById('coastStatus').textContent = 'You\'ve already hit Coast FIRE!';
    document.getElementById('coastStatus').style.color = '#16a34a';
  } else {
    document.getElementById('coastStatus').textContent = 'Need ' + fmtFull(coastDiff) + ' more';
    document.getElementById('coastStatus').style.color = '#64748b';
  }

  // Savings Rate Impact Table
  var rates = [20, 30, 40, 50, 60, 70];
  var tbody = document.getElementById('savingsRateBody');
  tbody.innerHTML = '';
  rates.forEach(function(rate) {
    var annSav = income * (rate / 100);
    var mContrib = annSav / 12;
    // Derive implied expenses for this rate
    var impliedExpenses = income - annSav;
    var fn = impliedExpenses / swr;
    var m = simulateMonthsFixed(currentSavings, mContrib, monthlyReturn, fn);
    var fireA = m === Infinity ? null : age + m / 12;
    var isClosest = Math.abs(rate - savingsRate) === Math.min.apply(null, rates.map(function(r) { return Math.abs(r - savingsRate); }));
    var highlight = isClosest ? 'background:#ede9fe;font-weight:700;' : '';
    var tr = document.createElement('tr');
    tr.style.cssText = highlight + 'border-bottom:1px solid #e9d5ff;';
    tr.innerHTML =
      '<td style="padding:9px 14px;' + (isClosest ? 'color:#7c3aed;' : '') + '">' + rate + '%' + (isClosest ? ' &#9664;' : '') + '</td>' +
      '<td style="padding:9px 14px;">' + fmtFull(annSav) + '</td>' +
      '<td style="padding:9px 14px;">' + (m === Infinity ? 'Never' : yearsMonths(m)) + '</td>' +
      '<td style="padding:9px 14px;">' + (fireA === null ? '—' : 'Age ' + Math.round(fireA)) + '</td>';
    tbody.appendChild(tr);
  });

  // Year-by-year projection
  buildProjection(age, currentSavings, annualSavings, annualReturn, fireNumber, savInc, months);
}

function buildProjection(age, currentSavings, annualSavings, annualReturn, fireNumber, savIncRate, fireMonths) {
  var tbody = document.getElementById('projectionBody');
  tbody.innerHTML = '';
  var portfolio = currentSavings;
  var savInc = savIncRate / 100;
  var annSav = annualSavings;
  var fireYear = fireMonths === Infinity ? null : Math.ceil(fireMonths / 12);
  var maxYears = fireYear === null ? 40 : Math.min(fireYear + 2, 50);

  for (var yr = 1; yr <= maxYears; yr++) {
    var returns = portfolio * annualReturn;
    portfolio = portfolio + returns + annSav;
    var isFIREYear = fireYear !== null && yr === fireYear;
    var rowStyle = isFIREYear ? 'background:#d1fae5;font-weight:700;' : (yr % 2 === 0 ? 'background:#faf5ff;' : '');
    var tr = document.createElement('tr');
    tr.style.cssText = rowStyle + 'border-bottom:1px solid #e9d5ff;';
    tr.innerHTML =
      '<td style="padding:8px 14px;">' + yr + (isFIREYear ? ' &#127881;' : '') + '</td>' +
      '<td style="padding:8px 14px;">' + (Math.floor(age) + yr) + '</td>' +
      '<td style="padding:8px 14px;text-align:right;">' + fmtFull(annSav) + '</td>' +
      '<td style="padding:8px 14px;text-align:right;">' + fmtFull(returns) + '</td>' +
      '<td style="padding:8px 14px;text-align:right;">' + fmtFull(portfolio) + '</td>';
    tbody.appendChild(tr);
    annSav *= (1 + savInc);
  }
}

window.toggleProjection = function() {
  var panel = document.getElementById('projectionTable');
  var icon = document.getElementById('projToggleIcon');
  if (panel.style.display === 'none') {
    panel.style.display = 'block';
    icon.textContent = '−';
  } else {
    panel.style.display = 'none';
    icon.textContent = '+';
  }
};

// Run on load
calcFIRE();

})();
</script>

---

## What Is FIRE?

FIRE stands for **Financial Independence, Retire Early** — a movement built around the idea that aggressive saving and investing can allow you to leave traditional employment far ahead of the standard retirement age. Instead of working into your 60s, FIRE practitioners aim to build a portfolio large enough that investment returns alone cover all their living expenses, permanently. The core insight is simple: the less you spend relative to what you earn, the faster your savings compound, and the sooner you reach the crossover point where your money works harder than you do.

The movement gained mainstream traction in the 1990s through Vicki Robin and Joe Dominguez's book *Your Money or Your Life*, and has since grown into a global community of bloggers, podcasters, and practitioners sharing strategies across forums like r/financialindependence. What unites them is a focus on savings rate over raw income — a household earning $60,000 and saving 50% of it will reach FIRE faster than one earning $150,000 and saving just 10%.

---

## The 4% Rule Explained

The **4% rule** is the cornerstone of FIRE withdrawal planning. It originates from the Trinity Study (1998, updated 2011), a landmark paper by three Trinity University professors who analyzed historical stock and bond market data going back to 1926. Their finding: a portfolio invested in a diversified mix of stocks and bonds could sustain annual withdrawals of 4% of its initial value — adjusted for inflation each year — for at least 30 years with a very high probability of success (around 95% for a 75% stock / 25% bond allocation).

In practical terms, the 4% rule means your **FIRE number is 25 times your annual expenses** (since 1 / 4% = 25). If you spend $50,000 per year, you need $1,250,000. If you plan to retire for 40 or 50 years rather than 30, many FIRE practitioners use a more conservative 3% to 3.5% SWR, which implies a FIRE number of 29–33 times annual spending. The rule is a guideline, not a guarantee — sequence-of-returns risk (a market crash early in retirement) remains the primary danger, which is why many FIRE retirees keep 1–2 years of expenses in cash and remain flexible about part-time income.

---

## Types of FIRE

**Lean FIRE** targets a minimalist lifestyle with reduced expenses — typically 20–30% below your current spending. The portfolio required is smaller, making FIRE achievable sooner, but it leaves less cushion for unexpected costs or lifestyle inflation over decades.

**Regular FIRE** is the baseline: retire on your current expenses, funded by a portfolio sized at 25× annual spending using the 4% rule. This is the most common goal and the default in the calculator above.

**Fat FIRE** targets a comfortable, affluent retirement at 1.5× or more of current expenses. You maintain full flexibility — travel, dining out, private schooling — without any lifestyle compromise. The tradeoff is a larger target and a longer accumulation phase.

**Coast FIRE** is a milestone rather than a finish line. Once your invested portfolio is large enough to grow to your full FIRE number by traditional retirement age (65) with no additional contributions, you've "coasted." Many people use Coast FIRE as permission to shift to lower-stress, lower-paying work they enjoy, since they no longer *need* to save aggressively.

**Barista FIRE** is a hybrid: you retire from your primary career before hitting your full number, then cover a portion of expenses through part-time or flexible work (the name comes from working at a coffee shop for health benefits). Your portfolio covers the rest. This approach dramatically shortens the accumulation phase and is popular among people who want to leave corporate life early without needing a fully funded portfolio.

---

## Tips to Reach FIRE Faster

**Increase your savings rate.** The savings rate impact table in the calculator above illustrates this starkly: going from a 20% to a 50% savings rate can cut your timeline roughly in half. Even a 5-percentage-point improvement makes a meaningful difference over a decade.

**Reduce expenses systematically.** Housing and transportation are the two largest budget categories for most households. Downsizing, house hacking (renting part of your home), or eliminating a car payment often moves the needle more than years of cutting discretionary spending. The key is finding cuts that don't reduce your quality of life, which compounds your results indefinitely.

**Increase your income.** Raises, promotions, job-hopping, and side hustles increase the numerator of your savings rate without requiring any lifestyle change. The FIRE community often emphasizes that income growth is underrated compared to frugality — especially early in a career when skills and earning potential are compounding rapidly alongside your portfolio.

**Optimize your investments.** Low-cost index funds (total market or S&P 500) consistently outperform the average actively managed fund after fees. Maximizing tax-advantaged accounts — 401(k), IRA, HSA — reduces your tax drag and keeps more capital compounding. Every basis point of fees you eliminate is permanent, risk-free return improvement.

---

## Related Tools

> See how your investments grow → [Compound Interest Calculator](/tools/compound-interest-calculator/)

> Track your total net worth → [Net Worth Calculator](/tools/net-worth-calculator/)

> Plan your retirement savings → [Retirement Calculator](/tools/retirement-calculator/)

> Calculate your take-home pay → [Salary Calculator](/tools/salary-calculator/)

> Create a monthly budget → [Budget Planner](/tools/budget-planner/)

> Set savings milestones → [Savings Goal Calculator](/tools/savings-goal-calculator/)

---

## Related Articles

- [What Is the FIRE Movement? A Beginner's Guide to Financial Independence](/blog/what-is-fire-movement/)
- [How to Calculate Your FIRE Number and Hit It Faster](/blog/how-to-calculate-fire-number/)
- [The 4% Rule: Is It Still Safe for Early Retirees?](/blog/4-percent-rule-safe-withdrawal-rate/)
- [Lean FIRE vs. Fat FIRE: Which Path Is Right for You?](/blog/lean-fire-vs-fat-fire/)
- [How to Increase Your Savings Rate Without Feeling Deprived](/blog/increase-savings-rate/)

---

*This calculator is provided for educational and informational purposes only. It does not constitute financial advice. Investment returns are not guaranteed, and past market performance does not predict future results. Consult a qualified financial professional before making major financial decisions.*

---

## Related Tools

> [Compound Interest Calculator](/tools/compound-interest-calculator/)
> [Ideco Simulator](/tools/ideco-simulator/)
> [Investment Return Calculator](/tools/investment-return-calculator/)

