---
title: "FIRE Retirement Simulator | How Many Years to Financial Independence? [2026]"
date: 2026-05-16
draft: false
slug: "fire-retirement-simulator"
description: "FIRE simulator. Enter your income, annual expenses, and current savings to automatically calculate years to financial independence. Compare Lean FIRE, Fat FIRE, and Coast FIRE scenarios."
categories: ["Free Tools"]
tags: ["FIRE", "financial independence", "early retirement", "simulator", "wealth building", "calculator"]
author: "Productivity Works Editorial Team"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/fire-retirement-simulator.png"
  alt: "FIRE Retirement Simulator | How Many Years to Financial Independence? [2026]"
  relative: false
---

*This article contains affiliate links.*

# FIRE Retirement Simulator [2026]

Enter your income, annual living expenses, and current assets to automatically calculate **years to FIRE** and your **target nest egg**. Lean FIRE, Fat FIRE, and Coast FIRE are all compared in one view.

<div id="fire-calc" style="max-width:680px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;color:#1e293b !important;color-scheme:light;">

<!-- Input Panel -->
<div style="padding:24px;border:2px solid #7c3aed;border-radius:12px;background:#faf5ff;margin-bottom:20px;">
<h2 style="margin:0 0 20px 0;font-size:18px;color:#7c3aed;">Enter Your Information</h2>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px;">

<div>
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Current Age</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="fireAge" min="20" max="70" step="1" value="30" oninput="calcFire()" style="flex:1;padding:10px;border:1px solid #c4b5fd;border-radius:8px;font-size:16px;background:white;">
<span style="color:#64748b;white-space:nowrap;">yrs</span>
</div>
</div>

<div>
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Annual Income ($)</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="fireIncome" min="0" max="1000000" step="1000" value="80000" oninput="calcFire()" style="flex:1;padding:10px;border:1px solid #c4b5fd;border-radius:8px;font-size:16px;background:white;">
<span style="color:#64748b;white-space:nowrap;">$</span>
</div>
</div>

<div>
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Annual Living Expenses ($)</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="fireExpense" min="0" max="500000" step="1000" value="50000" oninput="calcFire()" style="flex:1;padding:10px;border:1px solid #c4b5fd;border-radius:8px;font-size:16px;background:white;">
<span style="color:#64748b;white-space:nowrap;">$</span>
</div>
</div>

<div>
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Current Net Worth ($)</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="fireAsset" min="0" max="10000000" step="1000" value="50000" oninput="calcFire()" style="flex:1;padding:10px;border:1px solid #c4b5fd;border-radius:8px;font-size:16px;background:white;">
<span style="color:#64748b;white-space:nowrap;">$</span>
</div>
</div>

</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Expected Annual Return (%): <span id="fireReturnVal" style="color:#7c3aed;">5.0%</span></label>
<input type="range" id="fireReturn" min="3" max="12" step="0.5" value="5" oninput="calcFire()" style="width:100%;accent-color:#7c3aed;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#94a3b8;"><span>3%</span><span>12%</span></div>
</div>

<div style="margin-bottom:4px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Withdrawal Rate (%): <span id="fireWithdrawVal" style="color:#7c3aed;">4.00%</span></label>
<input type="range" id="fireWithdraw" min="2" max="5" step="0.25" value="4" oninput="calcFire()" style="width:100%;accent-color:#7c3aed;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#94a3b8;"><span>2% (conservative)</span><span>5% (aggressive)</span></div>
</div>

</div>

<!-- Main Results Panel -->
<div style="background:linear-gradient(135deg,#7c3aed,#5b21b6);color:white;border-radius:12px;padding:24px;margin-bottom:16px;text-align:center;">
<div style="font-size:14px;opacity:0.85;margin-bottom:4px;">FIRE Target (Required Nest Egg)</div>
<div id="fireTarget" style="font-size:42px;font-weight:bold;letter-spacing:-1px;">$1,250,000</div>
<div style="font-size:13px;opacity:0.75;margin-top:4px;">Annual Expenses &divide; Withdrawal Rate</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#ede9fe;border-radius:10px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#6b7280;margin-bottom:4px;">Years to FIRE</div>
<div id="fireYears" style="font-size:22px;font-weight:bold;color:#7c3aed;">—</div>
</div>
<div style="background:#ede9fe;border-radius:10px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#6b7280;margin-bottom:4px;">FIRE Age</div>
<div id="fireAgeResult" style="font-size:22px;font-weight:bold;color:#7c3aed;">—</div>
</div>
<div style="background:#ede9fe;border-radius:10px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#6b7280;margin-bottom:4px;">Monthly Savings</div>
<div id="fireMonthlySave" style="font-size:22px;font-weight:bold;color:#7c3aed;">—</div>
</div>
</div>

<div style="background:#f5f3ff;border-radius:10px;padding:16px;margin-bottom:16px;">
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">
<span style="font-size:14px;font-weight:bold;">Savings Rate</span>
<span id="fireSavingsRate" style="font-size:20px;font-weight:bold;color:#7c3aed;">—</span>
</div>
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
<span style="font-size:13px;color:#6b7280;">Progress to FIRE</span>
<span id="fireProgressPct" style="font-size:14px;font-weight:bold;color:#7c3aed;">0%</span>
</div>
<div style="background:#ddd6fe;border-radius:999px;height:12px;overflow:hidden;">
<div id="fireProgressBar" style="height:100%;background:linear-gradient(90deg,#7c3aed,#a78bfa);border-radius:999px;width:0%;transition:width 0.4s;"></div>
</div>
<div style="display:flex;justify-content:space-between;font-size:11px;color:#94a3b8;margin-top:4px;">
<span>Current: <span id="fireCurrentAssetLabel">$0</span></span>
<span>Target: <span id="fireTargetLabel">$0</span></span>
</div>
</div>

<!-- FIRE Type Comparison Panel -->
<div style="margin-bottom:20px;">
<h3 style="font-size:16px;font-weight:bold;margin:0 0 12px 0;color:#4c1d95;">FIRE Type Comparison</h3>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;" id="fireTypeGrid">

<div style="border:1px solid #c4b5fd;border-radius:10px;padding:14px;background:#faf5ff;">
<div style="font-size:13px;font-weight:bold;color:#6b7280;margin-bottom:6px;">Lean FIRE <span style="font-size:11px;font-weight:normal;">(expenses &times; 0.8)</span></div>
<div id="leanTarget" style="font-size:18px;font-weight:bold;color:#7c3aed;margin-bottom:2px;">—</div>
<div id="leanYears" style="font-size:13px;color:#6b7280;">Calculating...</div>
</div>

<div style="border:2px solid #7c3aed;border-radius:10px;padding:14px;background:#ede9fe;position:relative;">
<div style="position:absolute;top:-10px;left:12px;background:#7c3aed;color:white;font-size:11px;padding:2px 8px;border-radius:999px;">Current Setting</div>
<div style="font-size:13px;font-weight:bold;color:#5b21b6;margin-bottom:6px;">Standard FIRE</div>
<div id="normalTarget" style="font-size:18px;font-weight:bold;color:#7c3aed;margin-bottom:2px;">—</div>
<div id="normalYears" style="font-size:13px;color:#5b21b6;font-weight:bold;">Calculating...</div>
</div>

<div style="border:1px solid #c4b5fd;border-radius:10px;padding:14px;background:#faf5ff;">
<div style="font-size:13px;font-weight:bold;color:#6b7280;margin-bottom:6px;">Fat FIRE <span style="font-size:11px;font-weight:normal;">(expenses &times; 1.5)</span></div>
<div id="fatTarget" style="font-size:18px;font-weight:bold;color:#7c3aed;margin-bottom:2px;">—</div>
<div id="fatYears" style="font-size:13px;color:#6b7280;">Calculating...</div>
</div>

<div style="border:1px solid #c4b5fd;border-radius:10px;padding:14px;background:#faf5ff;">
<div style="font-size:13px;font-weight:bold;color:#6b7280;margin-bottom:6px;">Coast FIRE <span style="font-size:11px;font-weight:normal;">(amount needed now to reach target by 65)</span></div>
<div id="coastTarget" style="font-size:18px;font-weight:bold;color:#7c3aed;margin-bottom:2px;">—</div>
<div id="coastStatus" style="font-size:13px;color:#6b7280;">Calculating...</div>
</div>

</div>
</div>

<!-- Year-by-Year Table (collapsible) -->
<details style="margin-bottom:20px;border:1px solid #c4b5fd;border-radius:10px;overflow:hidden;">
<summary style="padding:14px 16px;font-weight:bold;font-size:14px;cursor:pointer;background:#faf5ff;color:#4c1d95;list-style:none;display:flex;align-items:center;gap:8px;">
<span>&#9658; Show Year-by-Year Projection</span>
</summary>
<div style="overflow-x:auto;">
<table id="fireTable" style="width:100%;border-collapse:collapse;font-size:13px;">
<thead>
<tr style="background:#7c3aed;color:white;">
<th style="padding:8px 12px;text-align:right;">Year</th>
<th style="padding:8px 12px;text-align:right;">Age</th>
<th style="padding:8px 12px;text-align:right;">Annual Savings</th>
<th style="padding:8px 12px;text-align:right;">Investment Gains</th>
<th style="padding:8px 12px;text-align:right;">Total Assets</th>
</tr>
</thead>
<tbody id="fireTableBody"></tbody>
</table>
</div>
</details>

<!-- Savings Rate Table -->
<div style="margin-bottom:20px;">
<h3 style="font-size:16px;font-weight:bold;margin:0 0 12px 0;color:#4c1d95;">Years to FIRE by Savings Rate</h3>
<div style="overflow-x:auto;">
<table style="width:100%;border-collapse:collapse;font-size:13px;text-align:center;">
<thead>
<tr style="background:#7c3aed;color:white;">
<th style="padding:8px 10px;">Savings Rate</th>
<th style="padding:8px 10px;">20%</th>
<th style="padding:8px 10px;">30%</th>
<th style="padding:8px 10px;">40%</th>
<th style="padding:8px 10px;">50%</th>
<th style="padding:8px 10px;">60%</th>
<th style="padding:8px 10px;">70%</th>
</tr>
</thead>
<tbody>
<tr id="savingsRateRow" style="background:#f5f3ff;">
<td style="padding:8px 10px;font-weight:bold;color:#4c1d95;">Years to FIRE</td>
<td id="sr20" style="padding:8px 10px;font-weight:bold;"></td>
<td id="sr30" style="padding:8px 10px;font-weight:bold;"></td>
<td id="sr40" style="padding:8px 10px;font-weight:bold;"></td>
<td id="sr50" style="padding:8px 10px;font-weight:bold;"></td>
<td id="sr60" style="padding:8px 10px;font-weight:bold;"></td>
<td id="sr70" style="padding:8px 10px;font-weight:bold;"></td>
</tr>
</tbody>
</table>
</div>
<div style="font-size:11px;color:#94a3b8;margin-top:6px;">* Based on current annual expenses, withdrawal rate, and expected return. Calculated from $0 starting assets.</div>
</div>

<div style="background:#f5f3ff;border-radius:8px;padding:12px;font-size:12px;color:#64748b;">
<strong>Calculation assumptions:</strong> Annual compound interest. Taxes and inflation are not factored in. Actual investment returns vary with market conditions. This simulator is for reference only and does not constitute investment advice.
</div>

</div>

<script>
(function(){

function fmt(v){
  return '$'+Math.round(v).toLocaleString();
}

function calcYearsToFireFractional(currentAsset, annualSave, targetAmount, returnRate){
  var asset = currentAsset;
  var r = returnRate / 100;
  for(var y = 0; y <= 200; y++){
if(asset >= targetAmount) return y;
var nextAsset = asset * (1 + r) + annualSave;
if(nextAsset >= targetAmount){
var frac = (targetAmount - asset) / (nextAsset - asset);
return y + frac;
}
asset = nextAsset;
  }
  return Infinity;
}

function fmtYears(y){
  if(y === Infinity || isNaN(y)) return 'Not achievable';
  if(y < 0) return 'Already achieved!';
  var totalMonths = Math.round(y * 12);
  var yy = Math.floor(totalMonths / 12);
  var mm = totalMonths % 12;
  if(yy === 0) return mm + ' mo';
  if(mm === 0) return yy + ' yr';
  return yy + ' yr ' + mm + ' mo';
}

window.calcFire = function(){
  var age      = parseInt(document.getElementById('fireAge').value)    || 30;
  var income   = parseFloat(document.getElementById('fireIncome').value)  || 0;
  var expense  = parseFloat(document.getElementById('fireExpense').value) || 0;
  var asset    = parseFloat(document.getElementById('fireAsset').value)   || 0;
  var retRate  = parseFloat(document.getElementById('fireReturn').value)  || 5;
  var wdRate   = parseFloat(document.getElementById('fireWithdraw').value) || 4;

  document.getElementById('fireReturnVal').textContent  = retRate.toFixed(1) + '%';
  document.getElementById('fireWithdrawVal').textContent = wdRate.toFixed(2) + '%';

  var annualSave = income - expense;
  var savingsRate = income > 0 ? (annualSave / income * 100) : 0;
  var monthlySave = annualSave / 12;

  // FIRE targets
  var targetNormal = expense / (wdRate / 100);
  var targetLean   = (expense * 0.8) / (wdRate / 100);
  var targetFat    = (expense * 1.5) / (wdRate / 100);

  // Progress
  var progressPct = targetNormal > 0 ? Math.min((asset / targetNormal) * 100, 100) : 0;
  var progressDisplay = asset < 0 ? 0 : progressPct;

  // FIRE years
  var yearsNormal = calcYearsToFireFractional(asset, annualSave, targetNormal, retRate);
  var yearsLean   = calcYearsToFireFractional(asset, annualSave, targetLean,   retRate);
  var yearsFat    = calcYearsToFireFractional(asset, annualSave, targetFat,    retRate);

  // Coast FIRE
  var yearsToRetire = Math.max(65 - age, 0);
  var coastAmount = yearsToRetire > 0
? targetNormal / Math.pow(1 + retRate / 100, yearsToRetire)
: targetNormal;
  var coastAchieved = asset >= coastAmount;

  // Update main results
  document.getElementById('fireTarget').textContent    = fmt(targetNormal);
  document.getElementById('fireTargetLabel').textContent = fmt(targetNormal);
  document.getElementById('fireCurrentAssetLabel').textContent = fmt(asset);
  document.getElementById('fireProgressPct').textContent = progressDisplay.toFixed(1) + '%';
  document.getElementById('fireProgressBar').style.width = progressDisplay + '%';
  document.getElementById('fireSavingsRate').textContent = savingsRate.toFixed(1) + '%';
  document.getElementById('fireMonthlySave').textContent = (monthlySave >= 0 ? '' : '-') + '$' + Math.round(Math.abs(monthlySave)).toLocaleString();

  if(yearsNormal === Infinity){
document.getElementById('fireYears').textContent    = 'Not achievable';
document.getElementById('fireAgeResult').textContent = '—';
  } else if(asset >= targetNormal){
document.getElementById('fireYears').textContent    = 'Already achieved!';
document.getElementById('fireAgeResult').textContent = age + ' yrs';
  } else {
document.getElementById('fireYears').textContent    = fmtYears(yearsNormal);
document.getElementById('fireAgeResult').textContent = Math.floor(age + yearsNormal) + ' yrs';
  }

  // FIRE type cards
  document.getElementById('leanTarget').textContent  = fmt(targetLean);
  document.getElementById('normalTarget').textContent = fmt(targetNormal);
  document.getElementById('fatTarget').textContent   = fmt(targetFat);

  document.getElementById('leanYears').textContent  = asset >= targetLean   ? 'Already achieved!' : (yearsLean   === Infinity ? 'Not achievable' : fmtYears(yearsLean)   + ' to FIRE');
  document.getElementById('normalYears').textContent = asset >= targetNormal ? 'Already achieved!' : (yearsNormal === Infinity ? 'Not achievable' : fmtYears(yearsNormal) + ' to FIRE');
  document.getElementById('fatYears').textContent   = asset >= targetFat    ? 'Already achieved!' : (yearsFat    === Infinity ? 'Not achievable' : fmtYears(yearsFat)    + ' to FIRE');

  document.getElementById('coastTarget').textContent = fmt(coastAmount);
  if(coastAchieved){
document.getElementById('coastStatus').textContent = 'Achieved! No more contributions needed to FIRE at 65';
document.getElementById('coastStatus').style.color = '#059669';
  } else {
var coastShortfall = coastAmount - asset;
document.getElementById('coastStatus').textContent = '$' + Math.round(coastShortfall).toLocaleString() + ' more to achieve Coast FIRE';
document.getElementById('coastStatus').style.color = '#6b7280';
  }

  // Year-by-year table
  var tbody = document.getElementById('fireTableBody');
  tbody.innerHTML = '';
  var a = asset;
  var r = retRate / 100;
  var maxYears = Math.min(
yearsNormal === Infinity ? 50 : Math.ceil(yearsNormal) + 2,
60
  );
  var fireReached = false;
  for(var y = 0; y <= maxYears; y++){
var investment = a * r;
var tr = document.createElement('tr');
var isFireYear = !fireReached && a >= targetNormal;
if(isFireYear){ fireReached = true; }
tr.style.background = isFireYear ? '#ede9fe' : (y % 2 === 0 ? 'white' : '#faf5ff');
tr.style.fontWeight = isFireYear ? 'bold' : 'normal';
var saveCurrent = y === 0 ? 0 : annualSave;
tr.innerHTML =
'<td style="padding:7px 12px;text-align:right;">' + (isFireYear ? '<span style="color:#7c3aed;">&#9733; ' : '') + 'Year ' + y + (isFireYear ? '</span>' : '') + '</td>' +
'<td style="padding:7px 12px;text-align:right;">' + (age + y) + '</td>' +
'<td style="padding:7px 12px;text-align:right;">' + (y === 0 ? '—' : '$' + Math.round(saveCurrent).toLocaleString()) + '</td>' +
'<td style="padding:7px 12px;text-align:right;">$' + Math.round(y === 0 ? 0 : a * r / (1 + r)).toLocaleString() + '</td>' +
'<td style="padding:7px 12px;text-align:right;color:' + (isFireYear ? '#7c3aed' : '#1e293b') + ';">$' + Math.round(a).toLocaleString() + '</td>';
tbody.appendChild(tr);
if(y > 0) a = a * (1 + r) + annualSave;
else a = a * (1 + r) + annualSave;
  }

  // Savings rate table
  var rates = [20, 30, 40, 50, 60, 70];
  rates.forEach(function(sr){
var annSave2 = income * (sr / 100);
var exp2 = income - annSave2;
var target2 = exp2 > 0 ? exp2 / (wdRate / 100) : 0;
var y2 = target2 > 0 ? calcYearsToFireFractional(0, annSave2, target2, retRate) : 0;
var el = document.getElementById('sr' + sr);
if(el){
el.textContent = y2 === Infinity ? 'N/A' : (y2 <= 0 ? 'Now' : fmtYears(y2));
el.style.color = '#7c3aed';
var curSR = Math.round(savingsRate / 10) * 10;
el.style.background = (sr === curSR) ? '#ddd6fe' : '';
}
  });
};

calcFire();
})();
</script>

---

## What Is FIRE?

**FIRE (Financial Independence, Retire Early)** is a lifestyle movement centered on achieving the freedom to stop working for money by accumulating enough investment assets to live off their returns indefinitely. It gained popularity in the US in the 2010s and has since spread worldwide.

The core FIRE formula is simple: **earn more, spend less, invest the difference**. A higher savings rate accelerates FIRE in two ways — you accumulate faster, and your required nest egg shrinks because your lifestyle costs less.

---

## How the 4% Rule Works

The 4% rule originates from the Trinity Study, a landmark research paper showing that a portfolio invested primarily in stocks can sustain annual withdrawals of 4% for 30+ years without being depleted. This means **25x your annual expenses** is the classic FIRE target.

Conservative planners use 3–3.5% withdrawal rates for longer retirements. This simulator lets you adjust the withdrawal rate from 2–5% so you can model any scenario.

---

## FIRE Types Explained

**Lean FIRE** — Achieve financial independence on a minimal budget (expenses &times; 0.8). Lower required assets, but demands frugal living.

**Standard FIRE** — Maintain your current lifestyle in retirement. The classic 25x annual expenses target.

**Fat FIRE** — Retire with a more generous lifestyle (expenses &times; 1.5). Requires a larger portfolio but provides maximum comfort.

**Coast FIRE** — The point at which your current assets will grow on their own to your full FIRE number by age 65, with no further contributions. Once you reach Coast FIRE, you only need to cover living expenses.

**Barista FIRE** — Semi-retire before reaching full FIRE by covering part of living expenses with part-time or passion work.

---

## How to Reach FIRE Faster

1. **Maximize your savings rate** — Going from 20% to 50% savings can cut your timeline by 20+ years
2. **Invest in low-cost index funds** — Broad market ETFs with expense ratios under 0.2% compound powerfully over time
3. **Add income streams** — Side income raises your savings rate without cutting lifestyle
4. **Cut fixed costs first** — Every $100/month in permanent savings = $30,000 less needed (at 4% rule)

---

## Related Tools

- [Take-Home Pay Calculator](/en/tools/take-home-pay-calculator/) — Calculate your net pay after tax
- [Income Tax Simulator](/en/tools/income-tax-simulator/) — See how taxes are calculated at any income level
- [Budget Journal Generator](/en/tools/budget-journal-generator/) — Optimize your monthly spending allocation
</div>
