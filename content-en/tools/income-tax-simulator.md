---
title: "Income Tax Simulator | Calculate Federal Tax, State Tax & Take-Home Pay Free"
date: 2026-05-16
draft: false
slug: "income-tax-simulator"
description: "Income tax simulator. Enter your gross income to calculate federal income tax, state tax, social insurance, and take-home pay for free. Supports both W-2 employee and freelance/self-employed calculations with 2026 tax brackets."
categories: ["Free Tools"]
tags: ["income tax", "simulator", "tax filing", "tax calculator", "calculator"]
author: "Productivity Works Editorial Team"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/income-tax-simulator.png"
  alt: "Income Tax Simulator"
  relative: false
---

*This article contains affiliate links.*

# Income Tax Simulator

Enter your income to instantly calculate your **federal income tax, state tax, social insurance, and take-home pay** all at once. The progressive tax bracket breakdown is shown clearly so you can understand exactly where your money goes.

<div id="st-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;color:#1e293b;">

<div style="padding:24px;border:2px solid #b91c1c;border-radius:12px;background:#fef2f2;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Gross Annual Income ($)</label>
<input type="number" id="stIncome" min="0" max="10000000" step="1000" value="80000" oninput="calcST()" style="width:100%;padding:12px;border:1px solid #cbd5e1;border-radius:8px;font-size:18px;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Employment Type</label>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<label style="display:flex;align-items:center;padding:12px;border:2px solid #b91c1c;border-radius:8px;cursor:pointer;background:#fef2f2;" id="lbl-employee">
<input type="radio" name="stType" value="employee" checked onchange="calcST()" style="margin-right:8px;"> W-2 Employee
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-freelance">
<input type="radio" name="stType" value="freelance" onchange="calcST()" style="margin-right:8px;"> Freelance / Self-Employed
</label>
</div>
</div>

<div id="stFreelanceOpts" style="display:none;margin-bottom:20px;padding:16px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="margin-bottom:12px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Business Expense Rate (%)</label>
<input type="range" id="stExpenseRate" min="0" max="80" step="5" value="30" oninput="calcST()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span id="stExpenseVal" style="font-weight:bold;color:#b91c1c;">30%</span><span>80%</span></div>
</div>
<div>
<label style="display:flex;align-items:center;cursor:pointer;font-size:14px;">
<input type="checkbox" id="stBlueReturn" checked onchange="calcST()" style="margin-right:6px;width:16px;height:16px;"> Home Office / QBI Deduction (~$6,500 equivalent)
</label>
</div>
</div>

<div style="margin-bottom:8px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Filing Status / Dependents</label>
<select id="stDependents" onchange="calcST()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="0">Single, no dependents</option>
<option value="1">Married filing jointly (no children)</option>
<option value="2">Married + 1 child</option>
<option value="3">Married + 2 children</option>
</select>
</div>

</div>

<!-- Results -->
<div id="stResults" style="margin-top:24px;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;text-align:center;">
<div style="padding:20px;background:#fef2f2;border-radius:12px;border:1px solid #fecaca;">
<div style="font-size:12px;color:#64748b;">Marginal Tax Rate</div>
<div id="stRate" style="font-size:36px;font-weight:bold;color:#b91c1c;">22%</div>
</div>
<div style="padding:20px;background:#f0fdf4;border-radius:12px;border:1px solid #bbf7d0;">
<div style="font-size:12px;color:#64748b;">Effective Tax Rate (All Taxes / Income)</div>
<div id="stEffective" style="font-size:36px;font-weight:bold;color:#16a34a;">—%</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:8px;margin-top:12px;text-align:center;">
<div style="padding:14px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:11px;color:#64748b;">Federal Tax</div>
<div id="stTax" style="font-size:18px;font-weight:bold;color:#b91c1c;">—</div>
</div>
<div style="padding:14px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:11px;color:#64748b;">State Tax</div>
<div id="stResident" style="font-size:18px;font-weight:bold;color:#ea580c;">—</div>
</div>
<div style="padding:14px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:11px;color:#64748b;">FICA / Social Ins.</div>
<div id="stSocial" style="font-size:18px;font-weight:bold;color:#7c3aed;">—</div>
</div>
<div style="padding:14px;background:#f0fdf4;border-radius:8px;border:2px solid #16a34a;">
<div style="font-size:11px;color:#64748b;">Take-Home</div>
<div id="stTakeHome" style="font-size:18px;font-weight:bold;color:#16a34a;">—</div>
</div>
</div>

<div style="margin-top:12px;text-align:center;padding:12px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<span style="font-size:13px;color:#64748b;">Monthly Take-Home: </span>
<span id="stMonthly" style="font-size:20px;font-weight:bold;color:#16a34a;">—</span>
</div>

<!-- Breakdown Bar -->
<div style="margin-top:20px;padding:20px;background:#f8fafc;border-radius:12px;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 12px 0;font-size:16px;">Income Breakdown</h3>
<div id="stBar" style="height:32px;border-radius:8px;overflow:hidden;display:flex;margin-bottom:8px;"></div>
<div style="display:flex;flex-wrap:wrap;gap:10px;font-size:12px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#16a34a;border-radius:2px;"></span> Take-Home</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#b91c1c;border-radius:2px;"></span> Federal Tax</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#ea580c;border-radius:2px;"></span> State Tax</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#7c3aed;border-radius:2px;"></span> FICA / Social Insurance</span>
</div>
</div>

<!-- Tax Bracket Table -->
<details style="margin-top:20px;">
<summary style="cursor:pointer;font-weight:bold;color:#b91c1c;font-size:15px;">Show Federal Income Tax Brackets</summary>
<div style="overflow-x:auto;margin-top:12px;">
<table id="stTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#b91c1c;color:white;">
<th style="padding:8px;text-align:left;">Rate</th>
<th style="padding:8px;text-align:right;">Taxable Income Range</th>
<th style="padding:8px;text-align:right;">Deduction Offset</th>
<th style="padding:8px;text-align:right;">Tax in This Bracket</th>
</tr>
</thead>
<tbody id="stTableBody"></tbody>
</table>
</div>
</details>

<!-- Income Comparison -->
<div style="margin-top:20px;padding:20px;background:#fffbeb;border-radius:12px;border:1px solid #fde68a;">
<h3 style="margin:0 0 12px 0;font-size:16px;">Take-Home Pay at Different Income Levels</h3>
<div id="stScenarios" style="display:grid;gap:8px;"></div>
</div>

</div>

</div>

<script>
const US_BRACKETS=[
  [0,11600,0.10,0],
  [11600,47150,0.12,232],
  [47150,100525,0.22,3479],
  [100525,191950,0.24,5579],
  [191950,243725,0.32,20725],
  [243725,609350,0.35,28001],
  [609350,Infinity,0.37,29211]
];

function getType(){return document.querySelector('input[name="stType"]:checked').value;}

function calcEmployeeDeduction(income){
  // Standard deduction 2026
  return 14600;
}

function calcSocialInsurance(income,type){
  if(type==='employee'){
// Employee share: SS 6.2% up to $168,600 + Medicare 1.45%
return Math.round(Math.min(income,168600)*0.062+income*0.0145);
  } else {
// Self-employed: full 15.3% (SS+Medicare), deduct half
return Math.round(Math.min(income,168600)*0.124+income*0.029);
  }
}

function calcFederalTax(taxableIncome){
  if(taxableIncome<=0) return{tax:0,rate:0,details:[]};
  let tax=0;let topRate=0;const details=[];
  for(const[lo,hi,rate,deduction] of US_BRACKETS){
if(taxableIncome<=lo) break;
topRate=rate;
const portion=Math.min(taxableIncome,hi)-lo;
const t=portion*rate;
details.push({lo,hi:Math.min(taxableIncome,hi),rate,portion,tax:t});
  }
  const bracket=US_BRACKETS.find(b=>b[2]===topRate);
  tax=Math.floor(taxableIncome*topRate-(bracket?bracket[3]:0));
  return{tax:Math.max(0,tax),rate:topRate,details};
}

function calcStateTax(taxableIncome){
  if(taxableIncome<=0) return 0;
  return Math.round(taxableIncome*0.05);
}

function calcST(){
  const incomeRaw=parseFloat(document.getElementById('stIncome').value)||0;
  const income=incomeRaw;
  const type=getType();
  const deps=parseInt(document.getElementById('stDependents').value);

  ['employee','freelance'].forEach(t=>{
document.getElementById('lbl-'+t).style.borderColor=t===type?'#b91c1c':'#e2e8f0';
document.getElementById('lbl-'+t).style.background=t===type?'#fef2f2':'white';
  });
  document.getElementById('stFreelanceOpts').style.display=type==='freelance'?'block':'none';

  // Deductions
  let deduction=0;
  if(type==='employee'){
deduction=calcEmployeeDeduction(income);
  }else{
const expRate=parseFloat(document.getElementById('stExpenseRate').value)/100;
document.getElementById('stExpenseVal').textContent=Math.round(expRate*100)+'%';
deduction=income*expRate;
if(document.getElementById('stBlueReturn').checked) deduction+=6500;
  }

  // Additional deductions for dependents
  if(deps>=1) deduction+=14600; // married filing jointly additional
  if(deps>=2) deduction+=2000;  // child tax credit equivalent
  if(deps>=3) deduction+=2000;

  const earnedIncome=Math.max(0,income-deduction);
  const social=calcSocialInsurance(income,type);

  // For self-employed, deduct half of SE tax
  let seDeduction=type==='freelance'?Math.round(social/2):0;
  const taxableIncome=Math.max(0,earnedIncome-seDeduction);

  const{tax:federalTax,rate:topRate,details}=calcFederalTax(taxableIncome);
  const stateTax=calcStateTax(taxableIncome);

  const totalTax=federalTax+stateTax+social;
  const takeHome=income-totalTax;
  const effectiveRate=income>0?(totalTax/income)*100:0;

  const fmt=v=>'$'+Math.round(v).toLocaleString();

  document.getElementById('stRate').textContent=Math.round(topRate*100)+'%';
  document.getElementById('stEffective').textContent=effectiveRate.toFixed(1)+'%';
  document.getElementById('stTax').textContent=fmt(federalTax);
  document.getElementById('stResident').textContent=fmt(stateTax);
  document.getElementById('stSocial').textContent=fmt(social);
  document.getElementById('stTakeHome').textContent=fmt(Math.max(0,takeHome));
  document.getElementById('stMonthly').textContent=fmt(Math.max(0,takeHome/12));

  // Breakdown bar
  if(income>0){
const pTH=((Math.max(0,takeHome)/income)*100).toFixed(1);
const pIT=((federalTax/income)*100).toFixed(1);
const pRT=((stateTax/income)*100).toFixed(1);
const pSI=((social/income)*100).toFixed(1);
document.getElementById('stBar').innerHTML=
'<div style="width:'+pTH+'%;background:#16a34a;height:100%;" title="Take-Home"></div>'+
'<div style="width:'+pIT+'%;background:#b91c1c;height:100%;" title="Federal Tax"></div>'+
'<div style="width:'+pRT+'%;background:#ea580c;height:100%;" title="State Tax"></div>'+
'<div style="width:'+pSI+'%;background:#7c3aed;height:100%;" title="FICA"></div>';
  }

  // Bracket table
  let tbody='';
  US_BRACKETS.forEach((b,i)=>{
const[lo,hi,rate,ded]=b;
const active=taxableIncome>lo;
const current=taxableIncome>lo&&(hi===Infinity||taxableIncome<=hi);
const portion=active?Math.min(taxableIncome,hi)-lo:0;
const t=portion*rate;
const bg=current?'#fef2f2':i%2===0?'#f8fafc':'white';
const hiStr=hi===Infinity?'+':'–$'+Math.round(hi).toLocaleString();
const arrow=current?' &larr;':'';
tbody+='<tr style="background:'+bg+';'+(current?'font-weight:bold;':'')+'">';
tbody+='<td style="padding:8px;">'+Math.round(rate*100)+'%'+arrow+'</td>';
tbody+='<td style="padding:8px;text-align:right;">$'+Math.round(lo).toLocaleString()+hiStr+'</td>';
tbody+='<td style="padding:8px;text-align:right;">$'+Math.round(ded).toLocaleString()+'</td>';
tbody+='<td style="padding:8px;text-align:right;'+(active?'':'color:#94a3b8;')+'">$'+Math.round(t).toLocaleString()+'</td>';
tbody+='</tr>';
  });
  document.getElementById('stTableBody').innerHTML=tbody;

  // Income comparison scenarios
  const scenarios=[30000,50000,70000,90000,120000,150000,200000,300000];
  let sHTML='';
  const expRate=type==='freelance'?(parseFloat(document.getElementById('stExpenseRate').value)/100):0;
  const blueReturn=type==='freelance'&&document.getElementById('stBlueReturn').checked;
  scenarios.forEach(s=>{
const sDed=type==='employee'?calcEmployeeDeduction(s):s*expRate+(blueReturn?6500:0);
const depDed=(deps>=1?14600:0)+(deps>=2?2000:0)+(deps>=3?2000:0);
const sEarned=Math.max(0,s-sDed-depDed);
const sSocial=calcSocialInsurance(s,type);
const sSEDed=type==='freelance'?Math.round(sSocial/2):0;
const sTaxable=Math.max(0,sEarned-sSEDed);
const sFederal=calcFederalTax(sTaxable).tax;
const sState=calcStateTax(sTaxable);
const sTH=s-sFederal-sState-sSocial;
const current=s===income;
sHTML+='<div style="display:flex;justify-content:space-between;align-items:center;padding:10px 12px;background:'+(current?'#fef2f2':'white')+';border-radius:8px;border:'+(current?'2px solid #b91c1c':'1px solid #e2e8f0')+';font-size:14px;">';
sHTML+='<div><strong>$'+s.toLocaleString()+'</strong></div>';
sHTML+='<div style="text-align:right;">Take-Home <strong style="color:#16a34a;">$'+Math.max(0,Math.round(sTH)).toLocaleString()+'</strong> ('+((Math.max(0,sTH)/s)*100).toFixed(0)+'%)</div>';
sHTML+='</div>';
  });
  document.getElementById('stScenarios').innerHTML=sHTML;
}

calcST();
</script>

---

## How to Use This Tool

1. **Enter your gross income** — Use your total annual compensation before any deductions
2. **Select employment type** — W-2 employees get the standard deduction automatically; freelancers can enter business expense rates
3. **Select filing status** — Married filing jointly and dependents increase your deductions and reduce taxable income

---

## US Federal Income Tax Brackets (2026)

| Taxable Income | Rate | Notes |
|---|---|---|
| $0 – $11,600 | 10% | Lowest bracket |
| $11,600 – $47,150 | 12% | |
| $47,150 – $100,525 | 22% | Most middle-class filers |
| $100,525 – $191,950 | 24% | |
| $191,950 – $243,725 | 32% | |
| $243,725 – $609,350 | 35% | |
| $609,350+ | 37% | Top bracket |

*State income taxes vary. An average of ~5% is used in this simulator. FICA = 6.2% Social Security + 1.45% Medicare for employees.*

---

## How to Reduce Your Tax Bill

### 1. Maximize 401(k) and IRA Contributions

Traditional 401(k) and IRA contributions are pre-tax, directly reducing your taxable income. In 2026, the 401(k) limit is $23,500 (under 50) — maxing this can drop you into a lower bracket.

### 2. Use an HSA (Health Savings Account)

HSAs offer a triple tax advantage: contributions are pre-tax, growth is tax-free, and withdrawals for medical expenses are tax-free.

### 3. Claim All Eligible Deductions

Don't miss student loan interest, mortgage interest, charitable contributions, or medical expenses above 7.5% of AGI.

### 4. Freelancers: File as S-Corp When Income Is High Enough

Above ~$60,000 in net self-employment income, electing S-Corp status can significantly reduce self-employment tax liability.

---

## Related Tools

- [Take-Home Pay Calculator](/en/tools/take-home-pay-calculator/) — Quick net pay calculation from gross salary
- [Job Change Salary Simulator](/en/tools/job-change-salary-simulator/) — Compare taxes and take-home before and after a job change
- [Budget Journal Generator](/en/tools/budget-journal-generator/) — Allocate your take-home pay across spending categories

---

## All Productivity Works Free Tools

All calculators on this site are **completely free**, run in your browser, and store no data whatsoever.

*This article contains affiliate links. No additional cost to you.*
</div>
