---
title: "Side Hustle Tax Calculator | Estimate Self-Employment & Income Tax"
date: 2026-05-16
draft: false
slug: "side-hustle-tax-calculator"
description: "Calculate taxes on your side hustle income. Estimate self-employment tax, federal income tax, and take-home pay from freelance or gig work. Free interactive calculator."
author: "Productivity Works Editorial"
categories:
  - "Personal Finance"
tags:
  - "side hustle"
  - "tax calculator"
  - "self-employment tax"
  - "freelance"
  - "1099"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/side-hustle-tax-calculator.png"
  alt: "Side Hustle Tax Calculator | Estimate Self-Employment & Income Tax"
  relative: false
---

*This article contains affiliate links. We may earn a commission at no extra cost to you.*

# Side Hustle Tax Calculator

Enter your W-2 salary and side hustle income to estimate your **total tax burden**, **self-employment tax**, and **actual take-home** from your side gig.

<div id="sh-calc" style="max-width:680px;margin:0 auto;font-family:Inter,sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
<div>
<h3 style="margin:0 0 12px;color:#64748b;font-size:14px;text-align:center;">W-2 Salary</h3>
<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">Annual Salary ($)</label>
<input type="range" id="w2Salary" min="0" max="250000" step="5000" value="65000" oninput="calcSH()" style="width:100%;">
<div style="text-align:center;font-weight:bold;font-size:20px;color:#64748b;" id="w2Val">$65,000</div>
</div>
</div>
<div>
<h3 style="margin:0 0 12px;color:#2563eb;font-size:14px;text-align:center;">Side Hustle</h3>
<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">Gross Revenue ($)</label>
<input type="range" id="shRevenue" min="0" max="100000" step="1000" value="15000" oninput="calcSH()" style="width:100%;">
<div style="text-align:center;font-weight:bold;font-size:20px;color:#2563eb;" id="shRevVal">$15,000</div>
</div>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">Business Expenses ($)</label>
<input type="range" id="shExpenses" min="0" max="50000" step="500" value="3000" oninput="calcSH()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>$0</span><span id="shExpVal" style="font-weight:bold;font-size:16px;color:#ef4444;">$3,000</span><span>$50,000</span></div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">Filing Status</label>
<select id="shFiling" onchange="calcSH()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="single">Single</option>
<option value="married">Married Filing Jointly</option>
<option value="hoh">Head of Household</option>
</select>
</div>

<div id="shResult" style="margin-top:20px;"></div>

</div>

<div id="shBreakdown" style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;"></div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">Quarterly Estimated Tax Payments</h3>
<div id="shQuarterly"></div>
</div>

</div>

<script>
function fmt(n){return Math.round(n).toLocaleString('en-US');}

function calcFedTax(taxable,filing){
  var brackets;
  if(filing==='married'){
    brackets=[[23200,0.10],[94300,0.12],[201050,0.22],[383900,0.24],[487450,0.32],[731200,0.35],[Infinity,0.37]];
  } else if(filing==='hoh'){
    brackets=[[16550,0.10],[63100,0.12],[100500,0.22],[191950,0.24],[243725,0.32],[609350,0.35],[Infinity,0.37]];
  } else {
    brackets=[[11600,0.10],[47150,0.12],[100525,0.22],[191950,0.24],[243725,0.32],[609350,0.35],[Infinity,0.37]];
  }
  var tax=0,prev=0;
  for(var i=0;i<brackets.length;i++){
    var upper=brackets[i][0],rate=brackets[i][1];
    var amt=Math.min(taxable,upper)-prev;
    if(amt<=0) break;
    tax+=amt*rate;
    prev=upper;
  }
  return Math.max(0,tax);
}

function getStdDeduction(filing){
  if(filing==='married') return 29200;
  if(filing==='hoh') return 21900;
  return 14600;
}

function calcSH(){
  var w2=+document.getElementById('w2Salary').value;
  var rev=+document.getElementById('shRevenue').value;
  var exp=+document.getElementById('shExpenses').value;
  var filing=document.getElementById('shFiling').value;

  document.getElementById('w2Val').textContent='$'+fmt(w2);
  document.getElementById('shRevVal').textContent='$'+fmt(rev);
  document.getElementById('shExpVal').textContent='$'+fmt(exp);

  var netProfit=Math.max(0,rev-exp);

  // Self-employment tax (15.3% on 92.35% of net profit)
  var seTaxBase=netProfit*0.9235;
  var ssWageBase=168600; // 2025 SS wage base
  var ssFromW2=Math.min(w2,ssWageBase);
  var ssFromSE=Math.min(Math.max(0,ssWageBase-ssFromW2),seTaxBase);
  var ssTax=ssFromSE*0.124;
  var medicareTax=seTaxBase*0.029;
  var seTax=ssTax+medicareTax;

  // SE tax deduction (half of SE tax)
  var seDeduction=seTax/2;

  // Federal income tax
  var stdDed=getStdDeduction(filing);
  var totalIncome=w2+netProfit;
  var agi=totalIncome-seDeduction;
  var taxable=Math.max(0,agi-stdDed);
  var fedTax=calcFedTax(taxable,filing);

  // Tax WITHOUT side hustle (for comparison)
  var taxableNoSH=Math.max(0,w2-stdDed);
  var fedTaxNoSH=calcFedTax(taxableNoSH,filing);

  // Additional tax from side hustle
  var additionalFed=fedTax-fedTaxNoSH;
  var totalSHTax=seTax+additionalFed;
  var effectiveRate=netProfit>0?(totalSHTax/netProfit*100):0;
  var takeHome=netProfit-totalSHTax;

  // Result summary
  var color=takeHome>=0?'#10b981':'#ef4444';
  var html='<div style="text-align:center;padding:16px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">Side Hustle Take-Home</div>';
  html+='<div style="font-size:36px;font-weight:bold;color:'+color+';">$'+fmt(takeHome)+'</div>';
  html+='<div style="font-size:14px;color:#64748b;margin-top:4px;">out of $'+fmt(netProfit)+' net profit</div>';
  html+='<div style="font-size:13px;color:#64748b;margin-top:8px;">Effective tax rate on side income: <strong style="color:#ef4444;">'+effectiveRate.toFixed(1)+'%</strong></div>';
  html+='</div>';
  document.getElementById('shResult').innerHTML=html;

  // Breakdown table
  var bhtml='<h3 style="margin:0 0 12px;color:#166534;font-size:16px;">Tax Breakdown</h3>';
  bhtml+='<table style="width:100%;border-collapse:collapse;font-size:14px;">';
  bhtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:8px;">Item</th><th style="text-align:right;padding:8px;">Amount</th></tr>';

  var rows=[
    ['Side hustle gross revenue','$'+fmt(rev)],
    ['Business expenses','-$'+fmt(exp)],
    ['Net profit (Schedule C)','$'+fmt(netProfit)],
    ['',''],
    ['Self-employment tax (15.3%)','$'+fmt(Math.round(seTax))],
    ['  Social Security (12.4%)','$'+fmt(Math.round(ssTax))],
    ['  Medicare (2.9%)','$'+fmt(Math.round(medicareTax))],
    ['',''],
    ['Additional federal income tax','$'+fmt(Math.round(additionalFed))],
    ['SE tax deduction (above-the-line)','-$'+fmt(Math.round(seDeduction))],
    ['',''],
    ['Total tax on side income','$'+fmt(Math.round(totalSHTax))],
    ['Take-home from side hustle','$'+fmt(Math.round(takeHome))]
  ];

  for(var i=0;i<rows.length;i++){
    if(rows[i][0]===''){bhtml+='<tr><td colspan="2" style="padding:4px;"></td></tr>';continue;}
    var bg=i%2===0?'#fff':'#f0fdf4';
    var bold=(i===rows.length-1||i===rows.length-2)?'font-weight:bold;':'';
    var indent=rows[i][0].startsWith('  ')?'padding-left:24px;':'';
    bhtml+='<tr style="background:'+bg+';'+bold+'">';
    bhtml+='<td style="padding:8px;'+indent+'">'+rows[i][0].trim()+'</td>';
    bhtml+='<td style="padding:8px;text-align:right;">'+rows[i][1]+'</td>';
    bhtml+='</tr>';
  }
  bhtml+='</table>';
  document.getElementById('shBreakdown').innerHTML=bhtml;

  // Quarterly estimates
  var quarterly=Math.round(totalSHTax/4);
  var qhtml='<div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:8px;text-align:center;">';
  var dates=['Apr 15','Jun 15','Sep 15','Jan 15'];
  for(var i=0;i<4;i++){
    qhtml+='<div style="padding:12px;background:#fff;border-radius:8px;">';
    qhtml+='<div style="font-size:11px;color:#64748b;">Q'+(i+1)+' ('+dates[i]+')</div>';
    qhtml+='<div style="font-size:18px;font-weight:bold;color:#92400e;">$'+fmt(quarterly)+'</div>';
    qhtml+='</div>';
  }
  qhtml+='</div>';
  qhtml+='<div style="margin-top:12px;font-size:12px;color:#92400e;text-align:center;">Pay quarterly estimated taxes to avoid underpayment penalties. Use IRS Form 1040-ES.</div>';
  document.getElementById('shQuarterly').innerHTML=qhtml;
}

document.addEventListener('DOMContentLoaded',function(){calcSH();});
calcSH();
</script>

---

## How Side Hustle Income Is Taxed

When you earn money from a side hustle — freelancing, gig work, selling online, consulting — the IRS treats it as **self-employment income**. This means you pay two types of tax:

### 1. Self-Employment Tax (15.3%)

This is the Social Security (12.4%) and Medicare (2.9%) tax that employers normally split with you. As a self-employed person, you pay both halves. The good news: you can deduct half of this tax from your adjusted gross income.

### 2. Federal Income Tax

Your side hustle profit is added to your W-2 income, so it's taxed at your **marginal tax rate** — the rate for the next dollar you earn. This is often higher than your average tax rate.

### Reducing Your Tax Bill

1. **Track all business expenses** — home office, equipment, software, mileage, supplies
2. **Open a Solo 401(k) or SEP-IRA** — contribute pre-tax dollars from self-employment income
3. **Deduct health insurance premiums** if you're self-employed and not covered by an employer plan
4. **Use accounting software** to categorize expenses and generate Schedule C reports

### When to Pay

If you expect to owe $1,000+ in taxes, make **quarterly estimated payments** using Form 1040-ES. Missing these deadlines can result in underpayment penalties.

---

> Want to see your full salary picture? Try our [US Salary Calculator](/tools/salary-calculator/) for W-2 take-home pay.

> Building your emergency fund from side hustle profits? Our [Emergency Fund Calculator](/tools/emergency-fund-calculator/) shows how long it takes.

---

**Related Tools**
- [US Salary Calculator](/tools/salary-calculator/)
- [Budget Planner](/tools/budget-planner/)
- [Debt Payoff Calculator](/tools/debt-payoff-calculator/)
- [Compound Interest Calculator](/tools/compound-interest-calculator/)
