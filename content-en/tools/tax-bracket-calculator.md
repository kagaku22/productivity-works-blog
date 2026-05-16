---
title: "US Tax Bracket Calculator 2026 | Federal Income Tax Estimator"
date: 2026-05-16
draft: false
slug: "tax-bracket-calculator"
description: "Free 2026 US federal income tax bracket calculator. Enter your income and filing status to see your tax bracket, effective tax rate, and total tax owed. Supports Single, Married Filing Jointly, Head of Household."
categories: ["Free Tools"]
tags: ["tax calculator", "tax bracket", "federal income tax", "2026 tax", "calculator"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/tax-bracket-calculator.png"
  alt: "US Tax Bracket Calculator 2026"
  relative: false
---

*This article contains affiliate links. We may earn a commission at no extra cost to you.*

# US Tax Bracket Calculator 2026

Enter your taxable income and filing status to see your **federal tax bracket, effective tax rate, and total tax owed** — with a visual breakdown of how each dollar is taxed.

<div id="tb-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;">

<div style="padding:24px;border:2px solid #dc2626;border-radius:12px;background:#fef2f2;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Annual Taxable Income ($)</label>
<input type="number" id="tbIncome" min="0" max="50000000" step="1000" value="75000" oninput="calcTB()" style="width:100%;padding:12px;border:1px solid #cbd5e1;border-radius:8px;font-size:18px;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Filing Status</label>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-single">
<input type="radio" name="tbStatus" value="single" checked onchange="calcTB()" style="margin-right:8px;"> Single
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-mfj">
<input type="radio" name="tbStatus" value="mfj" onchange="calcTB()" style="margin-right:8px;"> Married Filing Jointly
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-mfs">
<input type="radio" name="tbStatus" value="mfs" onchange="calcTB()" style="margin-right:8px;"> Married Filing Separately
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-hoh">
<input type="radio" name="tbStatus" value="hoh" onchange="calcTB()" style="margin-right:8px;"> Head of Household
</label>
</div>
</div>

<div style="margin-bottom:8px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Standard Deduction</label>
<div style="display:flex;gap:12px;align-items:center;">
<label style="display:flex;align-items:center;cursor:pointer;">
<input type="checkbox" id="tbDeduction" checked onchange="calcTB()" style="margin-right:6px;width:18px;height:18px;"> Apply standard deduction
</label>
<span id="tbDeductionAmt" style="color:#64748b;font-size:14px;">($15,000)</span>
</div>
</div>

</div>

<!-- Results -->
<div id="tbResults" style="margin-top:24px;">

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;text-align:center;">
<div style="padding:20px;background:#fef2f2;border-radius:12px;border:1px solid #fecaca;">
<div style="font-size:12px;color:#64748b;">Marginal Tax Bracket</div>
<div id="tbBracket" style="font-size:36px;font-weight:bold;color:#dc2626;">22%</div>
</div>
<div style="padding:20px;background:#f0fdf4;border-radius:12px;border:1px solid #bbf7d0;">
<div style="font-size:12px;color:#64748b;">Effective Tax Rate</div>
<div id="tbEffective" style="font-size:36px;font-weight:bold;color:#16a34a;">14.3%</div>
</div>
<div style="padding:20px;background:#f8fafc;border-radius:12px;border:1px solid #e2e8f0;">
<div style="font-size:12px;color:#64748b;">Total Federal Tax</div>
<div id="tbTotal" style="font-size:28px;font-weight:bold;color:#1e293b;">$10,725</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:12px;text-align:center;">
<div style="padding:16px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:12px;color:#64748b;">After-Tax Income</div>
<div id="tbAfterTax" style="font-size:22px;font-weight:bold;color:#1e293b;">$64,275</div>
</div>
<div style="padding:16px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:12px;color:#64748b;">Monthly Take-Home (Federal Only)</div>
<div id="tbMonthly" style="font-size:22px;font-weight:bold;color:#1e293b;">$5,356</div>
</div>
</div>

<!-- Bracket breakdown bar -->
<div style="margin-top:24px;padding:20px;background:#f8fafc;border-radius:12px;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 12px 0;font-size:16px;">How your income is taxed</h3>
<div id="tbBar" style="height:32px;border-radius:8px;overflow:hidden;display:flex;margin-bottom:8px;"></div>
<div id="tbLegend" style="display:flex;flex-wrap:wrap;gap:8px;font-size:12px;"></div>
</div>

<!-- Bracket table -->
<div style="margin-top:20px;padding:20px;background:white;border-radius:12px;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 12px 0;font-size:16px;">2026 Federal Tax Brackets</h3>
<div style="overflow-x:auto;">
<table id="tbTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#dc2626;color:white;">
<th style="padding:8px;text-align:left;">Rate</th>
<th style="padding:8px;text-align:right;">Income Range</th>
<th style="padding:8px;text-align:right;">Tax in Bracket</th>
<th style="padding:8px;text-align:right;">Cumulative Tax</th>
</tr>
</thead>
<tbody id="tbTableBody"></tbody>
</table>
</div>
</div>

<!-- Comparison -->
<div style="margin-top:20px;padding:20px;background:#fffbeb;border-radius:12px;border:1px solid #fde68a;">
<h3 style="margin:0 0 12px 0;font-size:16px;">What if your income changed?</h3>
<div id="tbScenarios" style="display:grid;gap:8px;"></div>
</div>

</div>

</div>

<script>
const BRACKETS={
  single:[
    [0,11925,0.10],[11925,48475,0.12],[48475,103350,0.22],
    [103350,197300,0.24],[197300,250525,0.32],[250525,626350,0.35],[626350,Infinity,0.37]
  ],
  mfj:[
    [0,23850,0.10],[23850,96950,0.12],[96950,206700,0.22],
    [206700,394600,0.24],[394600,501050,0.32],[501050,751600,0.35],[751600,Infinity,0.37]
  ],
  mfs:[
    [0,11925,0.10],[11925,48475,0.12],[48475,103350,0.22],
    [103350,197300,0.24],[197300,250525,0.32],[250525,375800,0.35],[375800,Infinity,0.37]
  ],
  hoh:[
    [0,17000,0.10],[17000,64850,0.12],[64850,103350,0.22],
    [103350,197300,0.24],[197300,250500,0.32],[250500,626350,0.35],[626350,Infinity,0.37]
  ]
};
const STD_DED={single:15000,mfj:30000,mfs:15000,hoh:22500};
const COLORS=['#dbeafe','#bfdbfe','#93c5fd','#60a5fa','#3b82f6','#2563eb','#1d4ed8'];

function getStatus(){
  return document.querySelector('input[name="tbStatus"]:checked').value;
}

function computeTax(income,status){
  const brackets=BRACKETS[status];
  let tax=0;const details=[];
  for(const[lo,hi,rate]of brackets){
    if(income<=lo)break;
    const taxable=Math.min(income,hi)-lo;
    const t=taxable*rate;
    tax+=t;
    details.push({lo,hi:Math.min(income,hi),rate,taxable,tax:t,cumTax:tax});
  }
  return{tax,details};
}

function calcTB(){
  const grossIncome=parseFloat(document.getElementById('tbIncome').value)||0;
  const status=getStatus();
  const useDeduction=document.getElementById('tbDeduction').checked;
  const deduction=useDeduction?STD_DED[status]:0;
  const taxableIncome=Math.max(0,grossIncome-deduction);

  document.getElementById('tbDeductionAmt').textContent='($'+deduction.toLocaleString()+')';

  // Highlight selected radio
  ['single','mfj','mfs','hoh'].forEach(s=>{
    document.getElementById('lbl-'+s).style.borderColor=s===status?'#dc2626':'#e2e8f0';
    document.getElementById('lbl-'+s).style.background=s===status?'#fef2f2':'white';
  });

  const{tax,details}=computeTax(taxableIncome,status);
  const marginalRate=details.length>0?details[details.length-1].rate:0;
  const effectiveRate=grossIncome>0?(tax/grossIncome)*100:0;
  const afterTax=grossIncome-tax;

  document.getElementById('tbBracket').textContent=Math.round(marginalRate*100)+'%';
  document.getElementById('tbEffective').textContent=effectiveRate.toFixed(1)+'%';
  document.getElementById('tbTotal').textContent='$'+Math.round(tax).toLocaleString();
  document.getElementById('tbAfterTax').textContent='$'+Math.round(afterTax).toLocaleString();
  document.getElementById('tbMonthly').textContent='$'+Math.round(afterTax/12).toLocaleString();

  // Bar
  let barHTML='';let legendHTML='';
  if(taxableIncome>0){
    details.forEach((d,i)=>{
      const pct=(d.taxable/taxableIncome)*100;
      if(pct>0){
        barHTML+='<div style="width:'+pct+'%;background:'+COLORS[i%COLORS.length]+';height:100%;" title="'+Math.round(d.rate*100)+'%: $'+d.taxable.toLocaleString()+'"></div>';
        legendHTML+='<span><span style="display:inline-block;width:10px;height:10px;background:'+COLORS[i%COLORS.length]+';border-radius:2px;"></span> '+Math.round(d.rate*100)+'%</span>';
      }
    });
  }
  document.getElementById('tbBar').innerHTML=barHTML;
  document.getElementById('tbLegend').innerHTML=legendHTML;

  // Table
  const allBrackets=BRACKETS[status];
  let tbody='';let cumTax=0;
  allBrackets.forEach((b,i)=>{
    const[lo,hi,rate]=b;
    const taxable=taxableIncome>lo?Math.min(taxableIncome,hi)-lo:0;
    const t=taxable*rate;
    cumTax+=t;
    const active=taxableIncome>lo;
    const current=taxableIncome>lo&&(hi===Infinity||taxableIncome<=hi);
    const bg=current?'#fef2f2':i%2===0?'#f8fafc':'white';
    const hiStr=hi===Infinity?'+':'$'+hi.toLocaleString();
    const arrow=current?' ←':'';
    tbody+='<tr style="background:'+bg+';'+(current?'font-weight:bold;':'')+'">';
    tbody+='<td style="padding:8px;">'+Math.round(rate*100)+'%'+arrow+'</td>';
    tbody+='<td style="padding:8px;text-align:right;">$'+lo.toLocaleString()+' – '+hiStr+'</td>';
    tbody+='<td style="padding:8px;text-align:right;'+(active?'':'color:#94a3b8;')+'">$'+Math.round(t).toLocaleString()+'</td>';
    tbody+='<td style="padding:8px;text-align:right;'+(active?'':'color:#94a3b8;')+'">$'+Math.round(cumTax).toLocaleString()+'</td>';
    tbody+='</tr>';
  });
  document.getElementById('tbTableBody').innerHTML=tbody;

  // Scenarios
  const changes=[10000,25000,50000];
  let sHTML='';
  changes.forEach(c=>{
    const newGross=grossIncome+c;
    const newTaxable=Math.max(0,newGross-deduction);
    const r=computeTax(newTaxable,status);
    const diff=r.tax-tax;
    const newEff=newGross>0?(r.tax/newGross)*100:0;
    sHTML+='<div style="display:flex;justify-content:space-between;align-items:center;padding:12px;background:white;border-radius:8px;border:1px solid #e2e8f0;">';
    sHTML+='<div><strong>$'+newGross.toLocaleString()+'</strong> <span style="color:#64748b;font-size:13px;">(+$'+c.toLocaleString()+')</span></div>';
    sHTML+='<div style="text-align:right;font-size:14px;">Tax: $'+Math.round(r.tax).toLocaleString()+' <span style="color:#dc2626;">(+$'+Math.round(diff).toLocaleString()+')</span> | Eff: '+newEff.toFixed(1)+'%</div>';
    sHTML+='</div>';
  });
  document.getElementById('tbScenarios').innerHTML=sHTML;
}

calcTB();
</script>

---

## How US Tax Brackets Work

The US uses a **progressive tax system** — your income is split into portions ("brackets"), and each portion is taxed at a different rate. Only the income **within** each bracket is taxed at that bracket's rate.

**Common misconception:** "If I earn $1 more and move into a higher bracket, all my income gets taxed at the higher rate." This is **false**. Only the additional dollar is taxed at the higher rate. Your overall (effective) tax rate always stays lower than your marginal bracket.

---

## 2026 Federal Tax Brackets (Single Filer)

| Rate | Taxable Income |
|---|---|
| 10% | $0 – $11,925 |
| 12% | $11,925 – $48,475 |
| 22% | $48,475 – $103,350 |
| 24% | $103,350 – $197,300 |
| 32% | $197,300 – $250,525 |
| 35% | $250,525 – $626,350 |
| 37% | $626,350+ |

*Standard deduction for 2026: $15,000 (Single), $30,000 (Married Filing Jointly), $22,500 (Head of Household).*

---

## Ways to Lower Your Tax Bracket

### 1. Maximize retirement contributions

401(k) contributions (up to $23,500 in 2026) reduce your taxable income dollar-for-dollar. If you're in the 22% bracket, a $10,000 contribution saves $2,200 in federal taxes.

### 2. Use the standard deduction or itemize

Most filers benefit from the standard deduction. If your mortgage interest, state taxes, and charitable donations exceed the standard deduction, itemizing saves more.

### 3. Contribute to an HSA

Health Savings Account contributions ($4,300 individual / $8,550 family in 2026) are tax-deductible, grow tax-free, and can be withdrawn tax-free for medical expenses.

### 4. Harvest investment losses

Capital losses offset capital gains dollar-for-dollar, plus up to $3,000 of ordinary income per year.

---

## Related Tools

> Calculate your full take-home pay after all taxes → [Salary Calculator](/tools/salary-calculator/)
> See how savings grow with compound interest → [Compound Interest Calculator](/tools/compound-interest-calculator/)
> Calculate how long to reach any savings target → [Savings Goal Calculator](/tools/savings-goal-calculator/)
> Plan your monthly budget after taxes → [Budget Planner](/tools/budget-planner/)
> Estimate freelance/side hustle taxes → [Side Hustle Tax Calculator](/tools/side-hustle-tax-calculator/)

---

## Related Articles

- [Freelance Tax Guide 2026](/posts/freelance-tax-guide-2026/)
- [401(k) vs IRA Differences Explained](/posts/401k-vs-ira-differences-explained/)
- [Roth IRA vs Traditional IRA](/posts/roth-ira-vs-traditional-ira-which-is-better/)
- [Best Budgeting Apps 2026](/posts/best-budgeting-apps-2026/)
- [How to Start Freelancing 2026](/posts/how-to-start-freelancing-2026/)

---

## Productivity Works Free Tools

All our financial calculators are **100% free**, run entirely in your browser, and never store your data.

[Browse all free tools](/tools/)

*This article contains affiliate links. We may earn a commission at no extra cost to you.*
