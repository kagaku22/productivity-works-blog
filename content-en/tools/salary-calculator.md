---
title: "US Salary Calculator | Take-Home Pay After Taxes"
date: 2026-05-14
draft: false
slug: "salary-calculator"
description: "Calculate your US take-home pay after federal tax, state tax, Social Security, and Medicare. Enter your annual salary to see your actual paycheck amount."
author: "Productivity Works"
categories:
  - "Personal Finance"
tags:
  - "Salary"
  - "Calculator"
  - "Tax"
  - "Take-Home Pay"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/salary-calculator.png"
  alt: "US Salary Calculator | Take-Home Pay After Taxes"
  relative: false
---

# US Salary Calculator — Take-Home Pay 2026

Enter your annual salary and filing status to instantly calculate your **take-home pay** after federal tax, state tax, Social Security, and Medicare.

<div id="salary-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Annual Gross Salary ($)</label>
<input type="range" id="salary" min="20000" max="300000" step="1000" value="75000" oninput="salCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>$20K</span><span id="salaryVal" style="font-weight:bold;font-size:18px;color:#2563eb;">$75,000</span><span>$300K</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Filing Status</label>
<select id="filing" onchange="salCalc()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="single">Single</option>
<option value="married">Married Filing Jointly</option>
<option value="head">Head of Household</option>
</select>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">State</label>
<select id="state" onchange="salCalc()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="0" data-name="No State Tax (TX, FL, WA, NV, etc.)">No State Tax (TX, FL, WA, NV, etc.)</option>
<option value="3.0">Low (3% — e.g. PA, IN)</option>
<option value="5.0" selected>Medium (5% — e.g. OH, VA, CO)</option>
<option value="7.0">High (7% — e.g. MN, OR)</option>
<option value="9.3">Very High (9.3% — e.g. CA)</option>
<option value="10.9">Highest (10.9% — e.g. NY+NYC)</option>
</select>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">Annual Take-Home Pay</div>
<div id="takeHome" style="font-size:36px;font-weight:bold;">$56,138</div>
<div style="font-size:14px;margin-top:8px;">Monthly: <span id="monthly" style="font-weight:bold;">$4,678</span> | Biweekly: <span id="biweekly" style="font-weight:bold;">$2,159</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#fee2e2;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Federal Income Tax</div>
<div id="fedTax" style="font-size:16px;font-weight:bold;color:#dc2626;">$8,932</div>
</div>
<div style="background:#fef3c7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">State Income Tax</div>
<div id="stateTax" style="font-size:16px;font-weight:bold;color:#d97706;">$3,180</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Social Security (6.2%)</div>
<div id="ssTax" style="font-size:16px;font-weight:bold;color:#0369a1;">$4,650</div>
</div>
<div style="background:#f3e8ff;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Medicare (1.45%)</div>
<div id="medTax" style="font-size:16px;font-weight:bold;color:#7c3aed;">$1,088</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Effective Tax Rate</div>
<div id="effRate" style="font-size:18px;font-weight:bold;color:#15803d;">25.2%</div>
</div>
<div style="background:#fce7f3;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Total Deductions</div>
<div id="totalDed" style="font-size:18px;font-weight:bold;color:#be185d;">$17,850</div>
</div>
</div>

<!-- Tax Breakdown Bar -->
<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;margin-bottom:6px;">Paycheck Breakdown</div>
<div style="display:flex;height:24px;border-radius:6px;overflow:hidden;">
<div id="barTake" style="background:#16a34a;height:100%;" title="Take-home"></div>
<div id="barFed" style="background:#dc2626;height:100%;" title="Federal Tax"></div>
<div id="barState" style="background:#d97706;height:100%;" title="State Tax"></div>
<div id="barSS" style="background:#0369a1;height:100%;" title="Social Security"></div>
<div id="barMed" style="background:#7c3aed;height:100%;" title="Medicare"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:8px;margin-top:6px;font-size:11px;">
<span style="color:#16a34a;">&#9632; Take-home</span>
<span style="color:#dc2626;">&#9632; Federal</span>
<span style="color:#d97706;">&#9632; State</span>
<span style="color:#0369a1;">&#9632; SS</span>
<span style="color:#7c3aed;">&#9632; Medicare</span>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>Note:</strong> Uses 2026 federal tax brackets with standard deduction ($15,000 single / $30,000 married / $22,500 HoH). State tax is a simplified flat rate. Does not include local taxes, 401(k), HSA, or other pre-tax deductions. Social Security wage base: $168,600.
</div>

</div>

<script>
function salCalc(){
  var gross=parseInt(document.getElementById('salary').value);
  var filing=document.getElementById('filing').value;
  var stateRate=parseFloat(document.getElementById('state').value)/100;

  // Standard deduction 2026 (approximate)
  var stdDed;
  if(filing==='married') stdDed=30000;
  else if(filing==='head') stdDed=22500;
  else stdDed=15000;

  var taxableIncome=Math.max(gross-stdDed,0);

  // Federal tax brackets 2026 (approximate)
  var fedTax;
  if(filing==='married'){
    if(taxableIncome<=23200) fedTax=taxableIncome*0.10;
    else if(taxableIncome<=94300) fedTax=2320+(taxableIncome-23200)*0.12;
    else if(taxableIncome<=201050) fedTax=10852+(taxableIncome-94300)*0.22;
    else if(taxableIncome<=383900) fedTax=34337+(taxableIncome-201050)*0.24;
    else if(taxableIncome<=487450) fedTax=78221+(taxableIncome-383900)*0.32;
    else if(taxableIncome<=731200) fedTax=111357+(taxableIncome-487450)*0.35;
    else fedTax=196670+(taxableIncome-731200)*0.37;
  } else if(filing==='head'){
    if(taxableIncome<=16550) fedTax=taxableIncome*0.10;
    else if(taxableIncome<=63100) fedTax=1655+(taxableIncome-16550)*0.12;
    else if(taxableIncome<=100500) fedTax=7241+(taxableIncome-63100)*0.22;
    else if(taxableIncome<=191950) fedTax=15469+(taxableIncome-100500)*0.24;
    else if(taxableIncome<=243725) fedTax=37417+(taxableIncome-191950)*0.32;
    else if(taxableIncome<=609350) fedTax=53985+(taxableIncome-243725)*0.35;
    else fedTax=181954+(taxableIncome-609350)*0.37;
  } else {
    if(taxableIncome<=11600) fedTax=taxableIncome*0.10;
    else if(taxableIncome<=47150) fedTax=1160+(taxableIncome-11600)*0.12;
    else if(taxableIncome<=100525) fedTax=5426+(taxableIncome-47150)*0.22;
    else if(taxableIncome<=191950) fedTax=17169+(taxableIncome-100525)*0.24;
    else if(taxableIncome<=243725) fedTax=39110+(taxableIncome-191950)*0.32;
    else if(taxableIncome<=609350) fedTax=55679+(taxableIncome-243725)*0.35;
    else fedTax=183647+(taxableIncome-609350)*0.37;
  }
  fedTax=Math.round(fedTax);

  // State tax (simplified flat rate)
  var stateTaxAmt=Math.round(taxableIncome*stateRate);

  // FICA
  var ssWageBase=168600;
  var ssAmt=Math.round(Math.min(gross,ssWageBase)*0.062);
  var medAmt=Math.round(gross*0.0145);
  if(gross>200000) medAmt+=Math.round((gross-200000)*0.009); // Additional Medicare

  var totalDed=fedTax+stateTaxAmt+ssAmt+medAmt;
  var takeHome=gross-totalDed;
  var effRate=(totalDed/gross*100);

  // Update display
  document.getElementById('salaryVal').textContent='$'+gross.toLocaleString();
  document.getElementById('takeHome').textContent='$'+takeHome.toLocaleString();
  document.getElementById('monthly').textContent='$'+Math.round(takeHome/12).toLocaleString();
  document.getElementById('biweekly').textContent='$'+Math.round(takeHome/26).toLocaleString();
  document.getElementById('fedTax').textContent='$'+fedTax.toLocaleString();
  document.getElementById('stateTax').textContent='$'+stateTaxAmt.toLocaleString();
  document.getElementById('ssTax').textContent='$'+ssAmt.toLocaleString();
  document.getElementById('medTax').textContent='$'+medAmt.toLocaleString();
  document.getElementById('effRate').textContent=effRate.toFixed(1)+'%';
  document.getElementById('totalDed').textContent='$'+totalDed.toLocaleString();

  // Update bar chart
  var tp=takeHome/gross*100;
  var fp=fedTax/gross*100;
  var sp=stateTaxAmt/gross*100;
  var ssp=ssAmt/gross*100;
  var mp=medAmt/gross*100;
  document.getElementById('barTake').style.width=tp+'%';
  document.getElementById('barFed').style.width=fp+'%';
  document.getElementById('barState').style.width=sp+'%';
  document.getElementById('barSS').style.width=ssp+'%';
  document.getElementById('barMed').style.width=mp+'%';
}
salCalc();
</script>

---

## How to Increase Your Take-Home Pay

### 1. Maximize Pre-Tax Contributions

Contributions to a 401(k) or 403(b) reduce your taxable income. In 2026, you can contribute up to **$23,500** (plus $7,500 catch-up if over 50).

### 2. Use an HSA (Health Savings Account)

If you have a high-deductible health plan, an HSA offers triple tax benefits: tax-deductible contributions, tax-free growth, and tax-free withdrawals for medical expenses.

### 3. Consider Your State

States like **Texas, Florida, Washington, Nevada, and Wyoming** have no state income tax. If you work remotely, this can significantly boost your take-home pay.

### 4. Track Your Expenses and Budget

Knowing where your take-home pay goes is just as important as maximizing it. Use our [Budget Planner](/tools/budget-planner/) to optimize your spending.

---

## Understanding Your Paycheck Deductions

| Deduction | Rate | 2026 Limit |
|-----------|------|-----------|
| Social Security | 6.2% | $168,600 wage base |
| Medicare | 1.45% | No limit (+0.9% over $200K) |
| Federal Income Tax | 10-37% | Progressive brackets |
| State Income Tax | 0-13.3% | Varies by state |

---

## FAQ

**Q: Why is my actual paycheck different from this calculator?**
This calculator uses the standard deduction and doesn't account for 401(k) contributions, HSA, insurance premiums, or other pre-tax deductions that reduce your taxable income.

**Q: What's the difference between marginal and effective tax rate?**
Your marginal rate is the tax on your next dollar of income. Your effective rate (shown above) is the total tax divided by your gross income — it's always lower than your marginal rate.

**Q: How can I lower my federal tax?**
Maximize pre-tax retirement contributions (401k, IRA), use an HSA, claim all eligible deductions, and consider tax-loss harvesting on investments.

---

## Related Tools

- [Budget Planner](/tools/budget-planner/) — Optimize your monthly spending
- [Compound Interest Calculator](/tools/compound-interest-calculator/) — See how investing your savings grows
- [Loan Repayment Calculator](/tools/loan-repayment-calculator/) — Plan your debt payoff
- [Forex Profit Calculator](/tools/forex-profit-calculator/) — Calculate trading profits
