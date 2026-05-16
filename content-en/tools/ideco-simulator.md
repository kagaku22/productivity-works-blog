---
title: "iDeCo Simulator | Calculate Tax Savings & Future Assets Automatically [2026]"
date: 2026-05-14
draft: false
slug: "ideco-simulator"
description: "Calculate your iDeCo (individual defined contribution pension) tax savings and future payout automatically. Just enter your income, monthly contribution, and expected return. Free tool to see your income tax and resident tax savings at a glance."
author: "Productivity Works Editorial Team"
categories:
  - "Free Tools"
tags:
  - "iDeCo"
  - "tax savings"
  - "pension"
  - "calculator"
  - "investing"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/ideco-simulator.png"
  alt: "iDeCo Simulator | Calculate Tax Savings & Future Assets Automatically"
  relative: false
---

*This article contains affiliate links.*

# iDeCo Tax Savings Simulator [2026]

Just enter your income, occupation, and monthly contribution to automatically calculate your **tax savings** and **projected payout at age 60**.

<div id="ideco-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Annual Income (gross, in 10,000s JPY)</label>
<input type="range" id="income" min="200" max="1500" step="10" value="500" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>¥2M</span><span id="incomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">¥5,000,000</span><span>¥15M</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Occupation (affects contribution limit)</label>
<select id="jobType" onchange="calcIdeco()" style="width:100%;padding:8px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="employee">Company employee (no corporate pension) — limit ¥23,000/mo</option>
<option value="employee_dc">Company employee (with corporate DC plan) — limit ¥20,000/mo</option>
<option value="employee_db">Company employee (with DB / welfare pension fund) — limit ¥12,000/mo</option>
<option value="civil">Public servant — limit ¥12,000/mo</option>
<option value="self">Self-employed / Freelancer — limit ¥68,000/mo</option>
<option value="homemaker">Homemaker (non-working spouse) — limit ¥23,000/mo</option>
</select>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Monthly Contribution (JPY)</label>
<input type="range" id="contribution" min="5000" max="68000" step="1000" value="23000" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>¥5,000</span><span id="contribVal" style="font-weight:bold;font-size:18px;color:#2563eb;">¥23,000</span><span id="contribMax">¥68,000</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Expected Annual Return (%)</label>
<input type="range" id="rate" min="1" max="8" step="0.5" value="4" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1%</span><span id="rateVal" style="font-weight:bold;font-size:18px;color:#2563eb;">4.0%</span><span>8%</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Investment Period (until age 60)</label>
<input type="range" id="years" min="1" max="35" step="1" value="25" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1 yr</span><span id="yearsVal" style="font-weight:bold;font-size:18px;color:#2563eb;">25 years</span><span>35 yrs</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">Projected Payout at Age 60 (pre-tax)</div>
<div id="totalAsset" style="font-size:36px;font-weight:bold;">¥11,896,000</div>
<div style="font-size:13px;margin-top:4px;">of which investment gains: <span id="profitAmt" style="font-weight:bold;">¥4,996,000</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#dcfce7;border-radius:8px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Annual Tax Savings</div>
<div id="taxSaveYear" style="font-size:22px;font-weight:bold;color:#15803d;">¥55,200</div>
</div>
<div style="background:#fef9c3;border-radius:8px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Cumulative Tax Savings</div>
<div id="taxSaveTotal" style="font-size:22px;font-weight:bold;color:#a16207;">¥1,380,000</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Total Contributions (principal)</div>
<div id="principal" style="font-size:16px;font-weight:bold;color:#0369a1;">¥6,900,000</div>
</div>
<div style="background:#f3e8ff;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Effective Return (incl. tax savings)</div>
<div id="realReturn" style="font-size:16px;font-weight:bold;color:#7c3aed;">+78.2%</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>Calculation notes:</strong> Uses a simplified model applying employment income deduction, basic deduction, and estimated social insurance premiums (~14.7%). Actual tax savings vary by individual circumstances. iDeCo contributions are fully deductible from taxable income.
</div>

</div>

<script>
function calcIdeco(){
  var inc=parseInt(document.getElementById('income').value);
  var job=document.getElementById('jobType').value;
  var contrib=parseInt(document.getElementById('contribution').value);
  var r=parseFloat(document.getElementById('rate').value)/100;
  var y=parseInt(document.getElementById('years').value);

  var maxContrib;
  if(job==='self') maxContrib=68000;
  else if(job==='employee') maxContrib=23000;
  else if(job==='employee_dc') maxContrib=20000;
  else if(job==='employee_db'||job==='civil') maxContrib=12000;
  else maxContrib=23000;

  if(contrib>maxContrib) contrib=maxContrib;
  var slider=document.getElementById('contribution');
  slider.max=maxContrib;
  if(parseInt(slider.value)>maxContrib) slider.value=maxContrib;

  var annual=inc*10000;
  var annualContrib=contrib*12;

  var deduction;
  if(annual<=1625000) deduction=550000;
  else if(annual<=1800000) deduction=annual*0.4-100000;
  else if(annual<=3600000) deduction=annual*0.3+80000;
  else if(annual<=6600000) deduction=annual*0.2+440000;
  else if(annual<=8500000) deduction=annual*0.1+1100000;
  else deduction=1950000;

  if(job==='self') deduction=0;

  var shotoku=annual-deduction;

  var socialIns=Math.floor(annual*0.147);
  if(job==='self') socialIns=Math.floor(annual*0.10);
  var basicDeduction=480000;
  var totalDeduction=basicDeduction+socialIns;

  var taxableWithout=Math.max(shotoku-totalDeduction,0);
  var taxableWith=Math.max(shotoku-totalDeduction-annualContrib,0);

  function getIncomeTax(taxable){
    if(taxable<=1950000) return taxable*0.05;
    else if(taxable<=3300000) return taxable*0.1-97500;
    else if(taxable<=6950000) return taxable*0.2-427500;
    else if(taxable<=9000000) return taxable*0.23-636000;
    else if(taxable<=18000000) return taxable*0.33-1536000;
    else if(taxable<=40000000) return taxable*0.40-2796000;
    else return taxable*0.45-4796000;
  }

  var taxWithout=Math.floor(getIncomeTax(taxableWithout)*1.021)+Math.floor(taxableWithout*0.1)+5000;
  var taxWith=Math.floor(getIncomeTax(taxableWith)*1.021)+Math.floor(taxableWith*0.1)+5000;

  var taxSaveYear=Math.max(taxWithout-taxWith,0);
  var taxSaveTotal=taxSaveYear*y;

  var mr=r/12;
  var n=y*12;
  var fv=contrib*((Math.pow(1+mr,n)-1)/mr);
  var p=contrib*n;
  var profit=fv-p;

  var realRet=((fv+taxSaveTotal-p)/p*100);

  document.getElementById('incomeVal').textContent='¥'+( inc*10000).toLocaleString();
  document.getElementById('contribVal').textContent='¥'+contrib.toLocaleString();
  document.getElementById('contribMax').textContent='¥'+maxContrib.toLocaleString();
  document.getElementById('rateVal').textContent=(r*100).toFixed(1)+'%';
  document.getElementById('yearsVal').textContent=y+' years';
  document.getElementById('totalAsset').textContent='¥'+Math.floor(fv).toLocaleString();
  document.getElementById('profitAmt').textContent='¥'+Math.floor(profit).toLocaleString();
  document.getElementById('taxSaveYear').textContent='¥'+taxSaveYear.toLocaleString();
  document.getElementById('taxSaveTotal').textContent='¥'+taxSaveTotal.toLocaleString();
  document.getElementById('principal').textContent='¥'+p.toLocaleString();
  document.getElementById('realReturn').textContent='+'+realRet.toFixed(1)+'%';
}
calcIdeco();
</script>

---

## iDeCo's 3 Tax Benefits

iDeCo offers tax advantages at **3 stages**, making it one of the most powerful tax-saving vehicles available.

| Stage | Tax Benefit | Effect |
|-------|------------|--------|
| Contribution | Full income deduction | Reduces income & resident tax every year |
| Growth phase | Tax-free investment gains | Eliminates the usual 20.315% tax on gains |
| Withdrawal | Retirement income deduction / public pension deduction | Favorable treatment whether taken as lump sum or annuity |

---

## How to Start iDeCo

1. **Choose a brokerage** — Compare fees and fund lineup
2. **Set your monthly contribution** — Limit depends on your occupation (use the simulator above)
3. **Select investment products** — Index funds are recommended for beginners
4. **Set up auto-deduction** — Once configured, contributions run on autopilot

---

## Tax Savings by Income Level

| Annual Income | Contribution (employee) | Annual Tax Savings | 30-Year Total Savings |
|--------------|------------------------|-------------------|-----------------------|
| ¥3,000,000   | ¥23,000/mo             | ~¥41,400          | ~¥1,242,000           |
| ¥5,000,000   | ¥23,000/mo             | ~¥55,200          | ~¥1,656,000           |
| ¥7,000,000   | ¥23,000/mo             | ~¥55,200          | ~¥1,656,000           |
| ¥10,000,000  | ¥23,000/mo             | ~¥82,800          | ~¥2,484,000           |

*Estimates for single employee with no dependents and no corporate pension.*

---

## Frequently Asked Questions

**Q. Should I start with iDeCo or NISA first?**
Generally NISA first. Because iDeCo funds are locked until age 60, it is recommended to secure liquidity with NISA before adding iDeCo contributions.

**Q. Why do self-employed people have a higher iDeCo limit?**
Self-employed individuals are not covered by the corporate pension system, so they have less retirement security. To compensate, their iDeCo contribution ceiling is ¥68,000/month (¥816,000/year).

**Q. Can I change my contribution amount later?**
Yes, once per year. You can also set contributions to ¥0 and continue managing investments as a "non-contributing member."

**Q. Are withdrawals taxed?**
Lump-sum withdrawals qualify for the retirement income deduction; annuity withdrawals qualify for the public pension deduction. Not the full amount is taxed.

---

## Related Tools

- [Savings Goal Calculator](/en/tools/savings-goal-calculator/) — Calculate how long to reach any savings target
- [Asset Allocation Simulator](/en/tools/asset-allocation-simulator/) — Track your total net worth
- [Dividend Growth Simulator](/en/tools/dividend-growth-simulator/) — Model dividend income and reinvestment

</div>
