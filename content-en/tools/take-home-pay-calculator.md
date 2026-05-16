---
title: "Take-Home Pay Calculator | Instantly Calculate Net Pay from Gross Salary [2026]"
date: 2026-05-14
draft: false
slug: "take-home-pay-calculator"
description: "Enter your gross salary and instantly see your take-home pay, income tax, state tax, and social insurance breakdown. Free tool for comparing salaries after a job change or raise."
author: "Productivity Works Editorial Team"
categories:
  - "Free Tools"
tags:
  - "take-home pay"
  - "salary"
  - "calculator"
  - "taxes"
  - "social security"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/take-home-pay-calculator.png"
  alt: "Take-Home Pay Calculator | Instantly Calculate Net Pay from Gross Salary"
  relative: false
---

*This article contains affiliate links.*

# Take-Home Pay Calculator [2026]

Enter your gross annual salary and instantly get your **take-home pay**, **taxes**, and **social insurance** breakdown.

<div id="tedori-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Gross Annual Salary ($)</label>
<input type="range" id="income" min="20000" max="300000" step="1000" value="70000" oninput="calcTedori()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>$20,000</span><span id="incomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">$70,000</span><span>$300,000</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Dependents</label>
<select id="dependents" onchange="calcTedori()" style="width:100%;padding:8px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="0">0 (Single, no dependents)</option>
<option value="1">1 dependent</option>
<option value="2">2 dependents</option>
<option value="3">3 dependents</option>
</select>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">Annual Take-Home Pay (Estimate)</div>
<div id="tedoriYear" style="font-size:36px;font-weight:bold;">$52,000</div>
<div style="font-size:14px;margin-top:8px;">Monthly: <span id="tedoriMonth" style="font-weight:bold;">$4,333</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#fee2e2;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Federal Income Tax (Annual)</div>
<div id="incomeTax" style="font-size:16px;font-weight:bold;color:#dc2626;">$0</div>
</div>
<div style="background:#fef3c7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">State Income Tax (Annual)</div>
<div id="residentTax" style="font-size:16px;font-weight:bold;color:#d97706;">$0</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">FICA / Social Insurance (Annual)</div>
<div id="socialIns" style="font-size:16px;font-weight:bold;color:#0369a1;">$0</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">Take-Home Rate</div>
<div id="tedoriRate" style="font-size:16px;font-weight:bold;color:#15803d;">—%</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>Assumptions:</strong> Single W-2 employee, standard deduction applied, average state tax ~5%, FICA at 7.65%. Actual amounts vary by filing status, state, age, and employer benefits.
</div>

</div>

<script>
function calcTedori(){
  var inc=parseInt(document.getElementById('income').value);
  var dep=parseInt(document.getElementById('dependents').value);
  var annual=inc;

  // Standard deduction (2026 approximate)
  var standardDeduction=14600+dep*4300;
  var taxableIncome=Math.max(0,annual-standardDeduction);

  // Federal income tax (2026 single brackets, approximate)
  var incomeTax=0;
  if(taxableIncome<=11600) incomeTax=taxableIncome*0.10;
  else if(taxableIncome<=47150) incomeTax=1160+(taxableIncome-11600)*0.12;
  else if(taxableIncome<=100525) incomeTax=5426+(taxableIncome-47150)*0.22;
  else if(taxableIncome<=191950) incomeTax=17169+(taxableIncome-100525)*0.24;
  else if(taxableIncome<=243725) incomeTax=39111+(taxableIncome-191950)*0.32;
  else if(taxableIncome<=609350) incomeTax=55679+(taxableIncome-243725)*0.35;
  else incomeTax=183647+(taxableIncome-609350)*0.37;
  incomeTax=Math.floor(incomeTax);

  // State tax (approximate 5% average)
  var residentTax=Math.floor(Math.max(0,taxableIncome)*0.05);

  // FICA: Social Security (6.2% up to $168,600) + Medicare (1.45%)
  var socialIns=Math.floor(Math.min(annual,168600)*0.062+annual*0.0145);

  var tedori=annual-incomeTax-residentTax-socialIns;
  var tedoriMonthly=Math.floor(tedori/12);
  var rate=(tedori/annual*100).toFixed(1);

  document.getElementById('incomeVal').textContent='$'+inc.toLocaleString();
  document.getElementById('tedoriYear').textContent='$'+Math.max(0,tedori).toLocaleString();
  document.getElementById('tedoriMonth').textContent='$'+Math.max(0,tedoriMonthly).toLocaleString();
  document.getElementById('incomeTax').textContent='$'+Math.max(0,incomeTax).toLocaleString();
  document.getElementById('residentTax').textContent='$'+Math.max(0,residentTax).toLocaleString();
  document.getElementById('socialIns').textContent='$'+socialIns.toLocaleString();
  document.getElementById('tedoriRate').textContent=rate+'%';
}
calcTedori();
</script>

---

## Take-Home Pay Reference Table by Salary

| Gross Salary | Estimated Take-Home | Take-Home Rate |
|---|---|---|
| $30,000 | ~$25,500 | ~85% |
| $50,000 | ~$41,000 | ~82% |
| $70,000 | ~$55,500 | ~79% |
| $90,000 | ~$69,500 | ~77% |
| $120,000 | ~$89,000 | ~74% |
| $150,000 | ~$107,000 | ~71% |
| $200,000 | ~$136,000 | ~68% |
| $300,000 | ~$192,000 | ~64% |

*Estimates for single filer, no dependents, average state tax.*

---

## How to Increase Your Take-Home Pay

The two key levers are **increasing income** or **increasing deductions**.

- **Maximize 401(k) / IRA contributions** — Pre-tax contributions directly reduce your taxable income
- **Use an HSA** — Health Savings Accounts offer a triple tax advantage
- **Claim all eligible deductions** — Don't overlook student loan interest, home office, and business expenses
- **Negotiate a raise or change jobs** — Often the fastest route to a higher paycheck

---

## Frequently Asked Questions

**Q. Does this include bonus income?**
Yes — enter your total gross compensation including bonuses. The result will be your estimated annual take-home including all pay.

**Q. What about 401(k) contributions?**
Pre-tax 401(k) contributions reduce your taxable income. For a more precise number, subtract your annual contribution from gross salary before entering it above.

**Q. I have side income — how does that affect things?**
Side income (freelance, gig work, etc.) is generally taxed as self-employment income at a different rate. See the [Income Tax Simulator](/en/tools/income-tax-simulator/) for a freelancer-specific calculation.

---

## Related Tools

- [Income Tax Simulator](/en/tools/income-tax-simulator/) — Detailed breakdown of income tax, state tax, and deductions
- [Job Change Salary Simulator](/en/tools/job-change-salary-simulator/) — Compare take-home pay before and after a job change
- [FIRE Retirement Simulator](/en/tools/fire-retirement-simulator/) — Calculate years to financial independence based on your income and expenses
</div>
