---
title: "Furusato Nozei (Hometown Tax) Simulator | Calculate Your Deduction Limit & Savings [2026]"
date: 2026-05-16
draft: false
slug: "furusato-tax-simulator"
description: "Enter your annual income and family situation to automatically calculate your Furusato Nozei deduction ceiling. See your net out-of-pocket cost, estimated gift return value, and a reference table by income bracket."
author: "Productivity Works Editorial"
categories:
  - "Free Tools"
tags:
  - "furusato nozei"
  - "hometown tax"
  - "Japan tax"
  - "simulation"
  - "tax deduction"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/furusato-tax-simulator.png"
  alt: "Furusato Nozei Simulator | Calculate Your Deduction Limit & Savings"
  relative: false
---

*This article contains affiliate links.*

# Furusato Nozei (Hometown Tax) Simulator [2026]

Enter your annual income and household situation to automatically calculate your **Furusato Nozei deduction ceiling** and **net tax savings**.

<div id="fn-calc" style="max-width:680px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Annual Income (gross, in 10,000 JPY)</label>
<input type="range" id="fnIncome" min="200" max="2500" step="10" value="500" oninput="calcFN()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>2M JPY</span><span id="fnIncVal" style="font-weight:bold;font-size:20px;color:#2563eb;">5M JPY</span><span>25M JPY</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Household Situation</label>
<select id="fnFamily" onchange="calcFN()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="single">Single or dual-income couple (no spousal deduction)</option>
<option value="couple">Married couple (spousal deduction applies)</option>
<option value="couple1">Married + 1 child (high school age)</option>
<option value="couple2">Married + 2 children (university + high school)</option>
</select>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Housing Loan Tax Credit (Jutaku Loan Kojo)</label>
<select id="fnLoan" onchange="calcFN()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="0">None</option>
<option value="100000">Yes (100,000 JPY/yr)</option>
<option value="200000">Yes (200,000 JPY/yr)</option>
<option value="300000">Yes (300,000 JPY/yr)</option>
</select>
</div>

<div id="fnResult" style="margin-top:24px;"></div>

</div>

<div style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;">
<h3 style="margin:0 0 16px;color:#166534;font-size:16px;">Deduction Ceiling by Income Bracket</h3>
<div id="fnTable"></div>
</div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">Gift Return Value Estimates</h3>
<div id="fnReturn"></div>
</div>

</div>

<script>
function fmt(n){return Math.round(n).toLocaleString();}

function calcFurusatoLimit(income,familyType,loanDeduction){
  var annual=income*10000;
  // Salary income deduction
  var deduction;
  if(annual<=1625000) deduction=550000;
  else if(annual<=1800000) deduction=annual*0.4-100000;
  else if(annual<=3600000) deduction=annual*0.3+80000;
  else if(annual<=6600000) deduction=annual*0.2+440000;
  else if(annual<=8500000) deduction=annual*0.1+1100000;
  else deduction=1950000;

  var netIncome=annual-deduction;

  // Personal deductions
  var kiso=480000;
  var shakai=annual*0.15; // approx. 15% for social insurance
  var haigusha=0,fuyou=0;
  if(familyType==='couple') haigusha=380000;
  else if(familyType==='couple1'){haigusha=380000;fuyou=380000;}
  else if(familyType==='couple2'){haigusha=380000;fuyou=380000+630000;}

  var totalDeduction=kiso+shakai+haigusha+fuyou;
  var taxableIncome=Math.max(0,netIncome-totalDeduction);

  // Income tax rate
  var taxRate;
  if(taxableIncome<=1950000) taxRate=0.05;
  else if(taxableIncome<=3300000) taxRate=0.10;
  else if(taxableIncome<=6950000) taxRate=0.20;
  else if(taxableIncome<=9000000) taxRate=0.23;
  else if(taxableIncome<=18000000) taxRate=0.33;
  else if(taxableIncome<=40000000) taxRate=0.40;
  else taxRate=0.45;

  // Resident tax (approx.)
  var juminTax=taxableIncome*0.10;

  // Furusato Nozei ceiling formula
  var denominator=1-taxRate*1.021-0.10;
  if(denominator<=0) denominator=0.01;
  var limit=juminTax*0.20/denominator+2000;

  // Housing loan credit impact
  if(loanDeduction>0){
var reduction=Math.min(loanDeduction*0.15,limit*0.15);
limit=Math.max(limit-reduction,2000);
  }

  return{
limit:Math.floor(limit),
taxRate:taxRate,
taxableIncome:taxableIncome,
juminTax:juminTax
  };
}

function calcFN(){
  var income=+document.getElementById('fnIncome').value;
  var family=document.getElementById('fnFamily').value;
  var loan=+document.getElementById('fnLoan').value;

  document.getElementById('fnIncVal').textContent=fmt(income*10000)+' JPY';

  var r=calcFurusatoLimit(income,family,loan);
  var returnValue=Math.floor(r.limit*0.3);

  var html='<div style="text-align:center;padding:20px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">Furusato Nozei Deduction Ceiling (estimate)</div>';
  html+='<div style="font-size:40px;font-weight:bold;color:#2563eb;">'+fmt(r.limit)+'<span style="font-size:16px;"> JPY</span></div>';
  html+='</div>';

  html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-top:16px;text-align:center;">';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">Your out-of-pocket cost</div><div style="font-size:20px;font-weight:bold;color:#ef4444;">2,000<span style="font-size:12px;"> JPY</span></div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">Gift return value (~30%)</div><div style="font-size:20px;font-weight:bold;color:#10b981;">'+fmt(returnValue)+'<span style="font-size:12px;"> JPY</span></div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">Net benefit</div><div style="font-size:20px;font-weight:bold;color:#f59e0b;">'+fmt(returnValue-2000)+'<span style="font-size:12px;"> JPY</span></div></div>';
  html+='</div>';

  html+='<div style="margin-top:12px;font-size:12px;color:#64748b;text-align:center;">* Calculated at income tax rate '+Math.round(r.taxRate*100)+'% (including surtax). Actual ceiling varies depending on your individual deductions.</div>';

  document.getElementById('fnResult').innerHTML=html;

  // Reference table
  var incomes=[300,400,500,600,700,800,900,1000,1200,1500,2000];
  var thtml='<table style="width:100%;border-collapse:collapse;font-size:13px;">';
  thtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:6px;">Income</th><th style="text-align:right;padding:6px;">Single</th><th style="text-align:right;padding:6px;">Married</th><th style="text-align:right;padding:6px;">Married+1</th></tr>';
  for(var i=0;i<incomes.length;i++){
var s=calcFurusatoLimit(incomes[i],'single',0);
var c=calcFurusatoLimit(incomes[i],'couple',0);
var c1=calcFurusatoLimit(incomes[i],'couple1',0);
var bg=incomes[i]===income?'#dcfce7':i%2===0?'#fff':'#f0fdf4';
var bold=incomes[i]===income?'font-weight:bold;':'';
thtml+='<tr style="background:'+bg+';'+bold+'">';
thtml+='<td style="padding:6px;">'+fmt(incomes[i]*10000)+' JPY</td>';
thtml+='<td style="padding:6px;text-align:right;">'+fmt(s.limit)+' JPY</td>';
thtml+='<td style="padding:6px;text-align:right;">'+fmt(c.limit)+' JPY</td>';
thtml+='<td style="padding:6px;text-align:right;">'+fmt(c1.limit)+' JPY</td>';
thtml+='</tr>';
  }
  thtml+='</table>';
  thtml+='<div style="margin-top:8px;font-size:11px;color:#64748b;">* Estimates only. Medical expense deductions, life insurance deductions, etc. may alter your actual ceiling.</div>';
  document.getElementById('fnTable').innerHTML=thtml;

  // Gift return goods
  var rhtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;">';
  var goods=[
{name:'Rice 20kg (domestic)',price:20000,value:8000},
{name:'Japanese Wagyu Beef 1kg',price:15000,value:5000},
{name:'Scallops 1kg (Hokkaido)',price:12000,value:4000},
{name:'Shine Muscat Grapes',price:10000,value:3500}
  ];
  for(var i=0;i<goods.length;i++){
var canAfford=r.limit>=goods[i].price?'#10b981':'#94a3b8';
var badge=r.limit>=goods[i].price?'Within limit':'Exceeds limit';
var badgeBg=r.limit>=goods[i].price?'#dcfce7':'#f1f5f9';
rhtml+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
rhtml+='<div style="font-size:13px;font-weight:bold;color:#1e293b !important;color-scheme:light;">'+goods[i].name+'</div>';
rhtml+='<div style="font-size:12px;color:#64748b;">Donation: '+fmt(goods[i].price)+' JPY</div>';
rhtml+='<div style="font-size:12px;color:#64748b;">Market value: ~'+fmt(goods[i].value)+' JPY</div>';
rhtml+='<span style="display:inline-block;margin-top:4px;padding:2px 8px;font-size:11px;font-weight:bold;background:'+badgeBg+';color:'+canAfford+';border-radius:4px;">'+badge+'</span>';
rhtml+='</div>';
  }
  rhtml+='</div>';
  rhtml+='<div style="margin-top:12px;font-size:12px;color:#92400e;text-align:center;">* Gift return rates are typical estimates as of 2026. Actual values vary by municipality and time of year.</div>';
  document.getElementById('fnReturn').innerHTML=rhtml;
}

document.addEventListener('DOMContentLoaded',function(){calcFN();});
calcFN();
</script>

---

## How Furusato Nozei Works

Furusato Nozei (literally "hometown tax donation") lets you donate to any Japanese municipality of your choice. The donated amount minus 2,000 JPY is deducted from your income tax and resident tax. On top of that, you receive a local gift (return item) worth roughly 30% of your donation — making it a highly efficient way to reduce taxes while supporting regional communities.

### Staying Within Your Deduction Ceiling

Any donation above your ceiling is not deductible and becomes a pure out-of-pocket expense. Use this simulator to confirm your ceiling before making any donations.

### The Process Step by Step

1. **Choose a municipality** — typically done by browsing gift catalogues on Furusato Nozei portals
2. **Complete the donation** — apply through a dedicated platform for convenience
3. **Receive your gift and receipt** — the municipality sends both
4. **Claim the deduction** — via your annual tax return, or via the One-Stop Special Exception (for up to 5 municipalities, no tax return needed)

---

## Related Tools

- [NISA Investment Simulator](/en/tools/nisa-investment-simulator/) — Simulate tax-free NISA growth
- [Compound Interest Calculator](/en/tools/compound-interest-calculator/) — See the long-term power of compounding
- [Percentage Calculator](/en/tools/percentage-calculator/) — Calculate tax rates and discount amounts
