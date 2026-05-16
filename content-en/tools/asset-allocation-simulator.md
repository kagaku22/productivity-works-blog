---
title: "Asset Allocation Simulator | Calculate Total Assets & Net Worth Automatically [2026]"
date: 2026-05-16
draft: false
slug: "asset-allocation-simulator"
description: "Asset allocation simulator. Enter your cash, investments, real estate, and other assets alongside your mortgage, loans, and other liabilities to instantly calculate your net worth. Compare against age-group averages."
categories: ["Free Tools"]
tags: ["asset management", "net worth", "simulator", "budgeting", "calculator"]
author: "Productivity Works Editorial Team"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/asset-allocation-simulator.png"
  alt: "Asset Allocation Simulator | Calculate Total Assets & Net Worth Automatically"
  relative: false
---

*This article contains affiliate links.*

# Asset Allocation Simulator

Enter your **assets** (cash, investments, real estate, etc.) and **liabilities** (loans, debt, etc.) to instantly calculate your **net worth**. Compare against age-group averages and set a personal goal.

<div id="ss-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;color:#1e293b;">

<!-- Assets section -->
<div style="padding:24px;border:2px solid #059669;border-radius:12px;background:#f0fdf4;margin-bottom:20px;">
<h2 style="margin:0 0 20px 0;font-size:20px;color:#059669;">Assets</h2>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Cash & Deposits <span style="font-weight:normal;color:#64748b;">(checking, savings, CDs, emergency fund)</span></label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssCash" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Investment Assets <span style="font-weight:normal;color:#64748b;">(stocks, funds, NISA, iDeCo, crypto)</span></label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssInvest" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Real Estate <span style="font-weight:normal;color:#64748b;">(primary residence value, investment properties)</span></label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssRealty" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Other <span style="font-weight:normal;color:#64748b;">(vehicles, precious metals, insurance cash value, business assets)</span></label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssOtherAsset" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="padding:16px;background:#dcfce7;border-radius:8px;display:flex;justify-content:space-between;align-items:center;">
<span style="font-weight:bold;font-size:16px;color:#059669;">Total Assets</span>
<span id="ssTotalAsset" style="font-size:28px;font-weight:bold;color:#059669;">¥0</span>
</div>
</div>

<!-- Liabilities section -->
<div style="padding:24px;border:2px solid #dc2626;border-radius:12px;background:#fef2f2;margin-bottom:20px;">
<h2 style="margin:0 0 20px 0;font-size:20px;color:#dc2626;">Liabilities</h2>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Mortgage Balance</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssHomeLoan" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Auto Loan</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssCarLoan" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Student Loan / Education Debt</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssEduLoan" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Credit Card Balance</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssCreditCard" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:14px;">Other Debt</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssOtherDebt" min="0" step="1" value="0" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="padding:16px;background:#fee2e2;border-radius:8px;display:flex;justify-content:space-between;align-items:center;">
<span style="font-weight:bold;font-size:16px;color:#dc2626;">Total Liabilities</span>
<span id="ssTotalDebt" style="font-size:28px;font-weight:bold;color:#dc2626;">¥0</span>
</div>
</div>

<!-- Results panel -->
<div id="ssResults" style="padding:24px;border-radius:12px;background:#eef2ff;border:2px solid #4f46e5;margin-bottom:20px;">

<div style="text-align:center;margin-bottom:24px;">
<div style="font-size:14px;color:#64748b;margin-bottom:4px;">Net Worth (Total Assets − Total Liabilities)</div>
<div id="ssNetWorth" style="font-size:48px;font-weight:bold;color:#4f46e5;line-height:1.1;">¥0</div>
<div id="ssDebtRatio" style="font-size:14px;color:#64748b;margin-top:8px;">Debt ratio: 0%</div>
</div>

<!-- Asset breakdown bar -->
<div style="margin-bottom:20px;">
<div style="font-weight:bold;font-size:14px;margin-bottom:8px;">Asset Breakdown</div>
<div style="height:28px;background:#e2e8f0;border-radius:14px;overflow:hidden;display:flex;">
<div id="ssBarCash" style="background:#059669;height:100%;transition:width 0.3s;width:0%;" title="Cash & Deposits"></div>
<div id="ssBarInvest" style="background:#10b981;height:100%;transition:width 0.3s;width:0%;" title="Investment Assets"></div>
<div id="ssBarRealty" style="background:#34d399;height:100%;transition:width 0.3s;width:0%;" title="Real Estate"></div>
<div id="ssBarOtherAsset" style="background:#6ee7b7;height:100%;transition:width 0.3s;width:0%;" title="Other"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#059669;border-radius:2px;"></span> Cash & Deposits</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#10b981;border-radius:2px;"></span> Investments</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#34d399;border-radius:2px;"></span> Real Estate</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#6ee7b7;border-radius:2px;"></span> Other</span>
</div>
</div>

<!-- Debt breakdown bar -->
<div id="ssDebtBreakdownWrap">
<div style="font-weight:bold;font-size:14px;margin-bottom:8px;">Liability Breakdown</div>
<div style="height:28px;background:#e2e8f0;border-radius:14px;overflow:hidden;display:flex;">
<div id="ssBarHomeLoan" style="background:#dc2626;height:100%;transition:width 0.3s;width:0%;" title="Mortgage"></div>
<div id="ssBarCarLoan" style="background:#ef4444;height:100%;transition:width 0.3s;width:0%;" title="Auto Loan"></div>
<div id="ssBarEduLoan" style="background:#f87171;height:100%;transition:width 0.3s;width:0%;" title="Student Loan"></div>
<div id="ssBarCredit" style="background:#fca5a5;height:100%;transition:width 0.3s;width:0%;" title="Credit Card"></div>
<div id="ssBarOtherDebt" style="background:#fecaca;height:100%;transition:width 0.3s;width:0%;" title="Other Debt"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#dc2626;border-radius:2px;"></span> Mortgage</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#ef4444;border-radius:2px;"></span> Auto</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#f87171;border-radius:2px;"></span> Student</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#fca5a5;border-radius:2px;"></span> Credit Card</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#fecaca;border-radius:2px;"></span> Other</span>
</div>
</div>

</div>

<!-- Age comparison -->
<div style="padding:24px;border-radius:12px;background:#f8fafc;border:1px solid #e2e8f0;margin-bottom:20px;">
<h3 style="margin:0 0 16px 0;font-size:18px;">Compare Against Age-Group Averages</h3>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Your Age Group</label>
<select id="ssAge" onchange="calcSS()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="">Select your age group</option>
<option value="20">20s</option>
<option value="30">30s</option>
<option value="40">40s</option>
<option value="50">50s</option>
<option value="60">60s</option>
<option value="70">70+</option>
</select>
</div>

<table style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#4f46e5;color:white;">
<th style="padding:10px 12px;text-align:left;border-radius:8px 0 0 0;">Age Group</th>
<th style="padding:10px 12px;text-align:right;">Median Net Worth (2+ person HH)</th>
<th style="padding:10px 12px;text-align:center;border-radius:0 8px 0 0;">vs. You</th>
</tr>
</thead>
<tbody id="ssAgeTable">
<tr style="background:white;"><td style="padding:10px 12px;border-bottom:1px solid #e2e8f0;">20s</td><td style="padding:10px 12px;text-align:right;border-bottom:1px solid #e2e8f0;">¥1,650,000</td><td style="padding:10px 12px;text-align:center;border-bottom:1px solid #e2e8f0;" id="ssCmp20">—</td></tr>
<tr style="background:#f8fafc;"><td style="padding:10px 12px;border-bottom:1px solid #e2e8f0;">30s</td><td style="padding:10px 12px;text-align:right;border-bottom:1px solid #e2e8f0;">¥5,260,000</td><td style="padding:10px 12px;text-align:center;border-bottom:1px solid #e2e8f0;" id="ssCmp30">—</td></tr>
<tr style="background:white;"><td style="padding:10px 12px;border-bottom:1px solid #e2e8f0;">40s</td><td style="padding:10px 12px;text-align:right;border-bottom:1px solid #e2e8f0;">¥8,250,000</td><td style="padding:10px 12px;text-align:center;border-bottom:1px solid #e2e8f0;" id="ssCmp40">—</td></tr>
<tr style="background:#f8fafc;"><td style="padding:10px 12px;border-bottom:1px solid #e2e8f0;">50s</td><td style="padding:10px 12px;text-align:right;border-bottom:1px solid #e2e8f0;">¥12,530,000</td><td style="padding:10px 12px;text-align:center;border-bottom:1px solid #e2e8f0;" id="ssCmp50">—</td></tr>
<tr style="background:white;"><td style="padding:10px 12px;border-bottom:1px solid #e2e8f0;">60s</td><td style="padding:10px 12px;text-align:right;border-bottom:1px solid #e2e8f0;">¥18,190,000</td><td style="padding:10px 12px;text-align:center;border-bottom:1px solid #e2e8f0;" id="ssCmp60">—</td></tr>
<tr style="background:#f8fafc;"><td style="padding:10px 12px;">70+</td><td style="padding:10px 12px;text-align:right;">¥19,050,000</td><td style="padding:10px 12px;text-align:center;" id="ssCmp70">—</td></tr>
</tbody>
</table>
<div id="ssAgeComment" style="margin-top:12px;padding:12px;border-radius:8px;font-size:14px;display:none;"></div>
<p style="font-size:12px;color:#94a3b8;margin-top:8px;margin-bottom:0;">Source: Survey on Household Financial Behavior (Central Council for Financial Services Information, Japan). Values shown in JPY.</p>
</div>

<!-- Goal setting -->
<div style="padding:24px;border-radius:12px;background:#fffbeb;border:1px solid #fde68a;margin-bottom:20px;">
<h3 style="margin:0 0 16px 0;font-size:18px;">Set a Net Worth Goal</h3>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Target Net Worth (¥10K units)</label>
<div style="display:flex;align-items:center;gap:8px;">
<input type="number" id="ssGoal" min="1" step="100" value="3000" oninput="calcSS()" style="flex:1;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
<span style="color:#64748b;white-space:nowrap;">万円 (¥10K units)</span>
</div>
</div>

<div style="margin-bottom:8px;display:flex;justify-content:space-between;font-size:14px;">
<span>Goal Progress</span>
<span id="ssGoalPct" style="font-weight:bold;color:#4f46e5;">0%</span>
</div>
<div style="height:20px;background:#e2e8f0;border-radius:10px;overflow:hidden;">
<div id="ssGoalBar" style="background:#4f46e5;height:100%;width:0%;transition:width 0.4s;border-radius:10px;"></div>
</div>
<div id="ssGoalComment" style="margin-top:10px;font-size:14px;color:#64748b;"></div>
</div>

</div>

<script>
(function(){
  var ageBenchmarks = {20:165, 30:526, 40:825, 50:1253, 60:1819, 70:1905};
  var ageCmpIds = {20:'ssCmp20', 30:'ssCmp30', 40:'ssCmp40', 50:'ssCmp50', 60:'ssCmp60', 70:'ssCmp70'};

  function fmtMan(v) {
    return '¥' + (v * 10000).toLocaleString();
  }

  function calcSS() {
    var cash = parseFloat(document.getElementById('ssCash').value) || 0;
    var invest = parseFloat(document.getElementById('ssInvest').value) || 0;
    var realty = parseFloat(document.getElementById('ssRealty').value) || 0;
    var otherAsset = parseFloat(document.getElementById('ssOtherAsset').value) || 0;

    var homeLoan = parseFloat(document.getElementById('ssHomeLoan').value) || 0;
    var carLoan = parseFloat(document.getElementById('ssCarLoan').value) || 0;
    var eduLoan = parseFloat(document.getElementById('ssEduLoan').value) || 0;
    var creditCard = parseFloat(document.getElementById('ssCreditCard').value) || 0;
    var otherDebt = parseFloat(document.getElementById('ssOtherDebt').value) || 0;

    var totalAsset = cash + invest + realty + otherAsset;
    var totalDebt = homeLoan + carLoan + eduLoan + creditCard + otherDebt;
    var netWorth = totalAsset - totalDebt;
    var debtRatio = totalAsset > 0 ? ((totalDebt / totalAsset) * 100).toFixed(1) : 0;

    document.getElementById('ssTotalAsset').textContent = fmtMan(totalAsset);
    document.getElementById('ssTotalDebt').textContent = fmtMan(totalDebt);

    var nwEl = document.getElementById('ssNetWorth');
    nwEl.textContent = (netWorth >= 0 ? '' : '-') + fmtMan(Math.abs(netWorth));
    nwEl.style.color = netWorth >= 0 ? '#4f46e5' : '#dc2626';

    document.getElementById('ssDebtRatio').textContent = 'Debt ratio: ' + debtRatio + '%';

    if (totalAsset > 0) {
      document.getElementById('ssBarCash').style.width = ((cash / totalAsset) * 100) + '%';
      document.getElementById('ssBarInvest').style.width = ((invest / totalAsset) * 100) + '%';
      document.getElementById('ssBarRealty').style.width = ((realty / totalAsset) * 100) + '%';
      document.getElementById('ssBarOtherAsset').style.width = ((otherAsset / totalAsset) * 100) + '%';
    } else {
      ['ssBarCash','ssBarInvest','ssBarRealty','ssBarOtherAsset'].forEach(function(id){
        document.getElementById(id).style.width = '0%';
      });
    }

    if (totalDebt > 0) {
      document.getElementById('ssBarHomeLoan').style.width = ((homeLoan / totalDebt) * 100) + '%';
      document.getElementById('ssBarCarLoan').style.width = ((carLoan / totalDebt) * 100) + '%';
      document.getElementById('ssBarEduLoan').style.width = ((eduLoan / totalDebt) * 100) + '%';
      document.getElementById('ssBarCredit').style.width = ((creditCard / totalDebt) * 100) + '%';
      document.getElementById('ssBarOtherDebt').style.width = ((otherDebt / totalDebt) * 100) + '%';
    } else {
      ['ssBarHomeLoan','ssBarCarLoan','ssBarEduLoan','ssBarCredit','ssBarOtherDebt'].forEach(function(id){
        document.getElementById(id).style.width = '0%';
      });
    }

    var selectedAge = document.getElementById('ssAge').value;
    var ageKeys = [20, 30, 40, 50, 60, 70];
    ageKeys.forEach(function(age) {
      var cell = document.getElementById(ageCmpIds[age]);
      var row = cell.closest('tr');
      if (selectedAge && parseInt(selectedAge) === age) {
        row.style.background = '#eef2ff';
        row.style.fontWeight = 'bold';
        var bench = ageBenchmarks[age];
        var diff = netWorth - bench;
        if (diff >= 0) {
          cell.innerHTML = '<span style="color:#059669;">+' + fmtMan(diff) + '</span>';
        } else {
          cell.innerHTML = '<span style="color:#dc2626;">' + fmtMan(diff) + '</span>';
        }
      } else {
        row.style.background = (age === 30 || age === 50 || age === 70) ? '#f8fafc' : 'white';
        row.style.fontWeight = 'normal';
        cell.innerHTML = '—';
      }
    });

    var ageComment = document.getElementById('ssAgeComment');
    if (selectedAge) {
      var age = parseInt(selectedAge);
      var bench = ageBenchmarks[age];
      var diff = netWorth - bench;
      ageComment.style.display = 'block';
      if (diff >= 0) {
        ageComment.style.background = '#dcfce7';
        ageComment.style.color = '#166534';
        ageComment.textContent = 'You are ' + fmtMan(diff) + ' above the median net worth for your age group (' + fmtMan(bench) + '). Keep it up!';
      } else {
        ageComment.style.background = '#fef2f2';
        ageComment.style.color = '#991b1b';
        ageComment.textContent = 'You are ' + fmtMan(Math.abs(diff)) + ' below the median net worth for your age group (' + fmtMan(bench) + '). Growing income or cutting expenses can help close the gap.';
      }
    } else {
      ageComment.style.display = 'none';
    }

    var goal = parseFloat(document.getElementById('ssGoal').value) || 3000;
    var pct = goal > 0 ? Math.min(Math.round((netWorth / goal) * 100), 100) : 0;
    var pctDisplay = netWorth < 0 ? 0 : pct;
    document.getElementById('ssGoalPct').textContent = pctDisplay + '%';
    document.getElementById('ssGoalBar').style.width = pctDisplay + '%';

    var goalComment = document.getElementById('ssGoalComment');
    if (netWorth < 0) {
      goalComment.textContent = 'Your net worth is negative. Prioritize paying down high-interest debt first.';
      goalComment.style.color = '#dc2626';
    } else if (pct >= 100) {
      goalComment.textContent = 'Goal achieved! Consider setting a higher target.';
      goalComment.style.color = '#059669';
    } else {
      var remaining = goal - netWorth;
      goalComment.textContent = fmtMan(remaining) + ' remaining to reach your goal. Keep building steadily.';
      goalComment.style.color = '#64748b';
    }
  }

  window.calcSS = calcSS;
  calcSS();
})();
</script>

---

## What Is Net Worth and Why Does It Matter?

**Net worth** is the value of everything you own minus everything you owe.

> Net Worth = Total Assets − Total Liabilities

Income and salary measure *flow* (what comes in each period), while net worth measures *stock* (what you have accumulated). Knowing your net worth helps you understand:

- **Financial resilience** — A higher net worth means greater ability to weather income disruptions
- **Retirement readiness** — How much wealth you have beyond future pension payments
- **Borrowing capacity** — Lenders assess net worth when approving mortgages and business loans
- **Progress tracking** — Measuring annually shows whether your wealth-building is on track

If your debt ratio (total liabilities ÷ total assets) exceeds 50%, consider prioritizing repayment of high-interest debt.

---

## 5 Ways to Grow Your Net Worth

### 1. Increase income
Side work, skill development, job changes, or negotiating a raise are the most direct levers. Channel extra income straight into assets.

### 2. Reduce expenses
Auditing fixed costs (rent, phone, insurance, subscriptions) can free tens of thousands of yen per year — often faster than a pay raise.

### 3. Pay off high-interest debt first
Credit card revolving debt (15–18% p.a.) erodes wealth faster than almost any investment can grow it. Eliminate these balances before investing aggressively.

### 4. Start investing
Cash alone loses purchasing power to inflation. Use NISA or iDeCo to invest in index funds for long-term, diversified, low-cost growth. Even 3–5% annual returns compound dramatically over decades.

### 5. Refinance or renegotiate fixed costs
Refinancing a mortgage, switching to a budget phone plan, or canceling unused insurance can permanently reduce monthly outflows.

---

## Related Tools

- [Savings Goal Calculator](/en/tools/savings-goal-calculator/) — Calculate how long to reach any savings target
- [iDeCo Simulator](/en/tools/ideco-simulator/) — Model iDeCo tax savings and projected payout
- [Dividend Growth Simulator](/en/tools/dividend-growth-simulator/) — Project dividend income from your investment portfolio

</div>
