---
title: "Mortgage Calculator 2026 | Monthly Payment, Amortization & More"
date: 2026-05-16
draft: false
slug: "mortgage-calculator"
description: "Free mortgage calculator 2026. Calculate your monthly payment including P&I, property tax, insurance, and PMI. See full amortization schedule and rate comparisons."
author: "Productivity Works Editorial"
categories:
  - "Free Tools"
tags:
  - "mortgage calculator"
  - "calculator"
  - "home buying"
  - "personal finance"
  - "tools"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/mortgage-calculator.png"
  alt: "Mortgage Calculator 2026 | Monthly Payment, Amortization & More"
  relative: false
---

*This article contains affiliate links. We may earn a commission at no extra cost to you.*

# Mortgage Calculator 2026

Enter your home price, down payment, and loan details to calculate your **full monthly payment** — including principal & interest, property taxes, insurance, and PMI.

<div id="mort-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b !important;color-scheme:light;">

<!-- Inputs -->
<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Home Price ($)</label>
<input type="number" id="homePrice" min="50000" max="5000000" step="1000" value="350000" oninput="calcMort()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;box-sizing:border-box;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Down Payment: <span id="dpPct" style="color:#2563eb;">20%</span> &nbsp;<span id="dpAmt" style="color:#64748b;font-size:14px;font-weight:normal;">($70,000)</span></label>
<input type="range" id="downPct" min="0" max="30" step="1" value="20" oninput="calcMort()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span>30%</span></div>
</div>

<div style="margin-bottom:20px;padding:12px;background:#e0f2fe;border-radius:8px;">
<div style="font-size:13px;color:#64748b;">Loan Amount</div>
<div id="loanAmtDisplay" style="font-size:22px;font-weight:bold;color:#0369a1;">$280,000</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Interest Rate: <span id="ratePct" style="color:#2563eb;">6.5%</span></label>
<input type="range" id="intRate" min="2" max="10" step="0.125" value="6.5" oninput="calcMort()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>2%</span><span>10%</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:10px;">Loan Term</label>
<div style="display:flex;gap:12px;">
<label style="flex:1;text-align:center;padding:10px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;font-weight:bold;" id="term15label">
<input type="radio" name="loanTerm" value="15" onchange="calcMort()" style="display:none;"> 15 Years
</label>
<label style="flex:1;text-align:center;padding:10px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;font-weight:bold;" id="term20label">
<input type="radio" name="loanTerm" value="20" onchange="calcMort()" style="display:none;"> 20 Years
</label>
<label style="flex:1;text-align:center;padding:10px;border:2px solid #2563eb;border-radius:8px;cursor:pointer;font-weight:bold;background:#eff6ff;color:#2563eb;" id="term30label">
<input type="radio" name="loanTerm" value="30" checked onchange="calcMort()" style="display:none;"> 30 Years
</label>
</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Property Tax Rate: <span id="taxPct" style="color:#2563eb;">1.2%</span> &nbsp;<span id="taxAmt" style="color:#64748b;font-size:14px;font-weight:normal;">($350/mo)</span></label>
<input type="range" id="propTax" min="0" max="3" step="0.1" value="1.2" oninput="calcMort()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span>3%</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Home Insurance ($/year)</label>
<input type="number" id="insurance" min="0" max="20000" step="100" value="1200" oninput="calcMort()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;box-sizing:border-box;">
</div>

<div id="pmiRow" style="margin-bottom:4px;padding:10px 12px;background:#fef3c7;border:1px solid #fcd34d;border-radius:8px;font-size:14px;color:#92400e;display:none;">
PMI automatically added — down payment is below 20%. PMI is removed once equity reaches 20%.
</div>

</div>

<!-- Results -->
<div style="margin-top:24px;padding:24px;border-radius:12px;background:#1e40af;color:white;text-align:center;">
<div style="font-size:15px;opacity:0.85;margin-bottom:4px;">Total Monthly Payment</div>
<div id="totalMonthly" style="font-size:52px;font-weight:bold;line-height:1.1;">$2,212</div>
<div style="font-size:14px;opacity:0.75;margin-top:6px;">Principal &amp; Interest + Tax + Insurance</div>
</div>

<div style="margin-top:16px;display:grid;grid-template-columns:1fr 1fr;gap:12px;">
<div style="padding:16px;background:#e0f2fe;border-radius:10px;text-align:center;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">Principal &amp; Interest</div>
<div id="piPayment" style="font-size:22px;font-weight:bold;color:#0369a1;">$1,770</div>
</div>
<div style="padding:16px;background:#fef3c7;border-radius:10px;text-align:center;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">Property Tax</div>
<div id="taxPayment" style="font-size:22px;font-weight:bold;color:#d97706;">$350</div>
</div>
<div style="padding:16px;background:#f0fdf4;border-radius:10px;text-align:center;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">Home Insurance</div>
<div id="insPayment" style="font-size:22px;font-weight:bold;color:#059669;">$100</div>
</div>
<div id="pmiCell" style="padding:16px;background:#fef2f2;border-radius:10px;text-align:center;display:none;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">PMI</div>
<div id="pmiPayment" style="font-size:22px;font-weight:bold;color:#dc2626;">$0</div>
</div>
</div>

<div style="margin-top:16px;display:grid;grid-template-columns:1fr 1fr;gap:12px;">
<div style="padding:16px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;text-align:center;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">Total Payment Over Loan Life</div>
<div id="totalLifetime" style="font-size:20px;font-weight:bold;color:#1e293b !important;color-scheme:light;">$637,320</div>
</div>
<div style="padding:16px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;text-align:center;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">Total Interest Paid</div>
<div id="totalInterest" style="font-size:20px;font-weight:bold;color:#dc2626;">$357,320</div>
</div>
</div>

<!-- Stacked bar -->
<div style="margin-top:20px;">
<div style="font-size:13px;font-weight:bold;margin-bottom:8px;color:#475569;">Monthly Payment Breakdown</div>
<div style="height:28px;border-radius:8px;overflow:hidden;display:flex;">
<div id="barPI"  style="background:#2563eb;height:100%;transition:width 0.3s;" title="Principal &amp; Interest"></div>
<div id="barTax" style="background:#f59e0b;height:100%;transition:width 0.3s;" title="Property Tax"></div>
<div id="barIns" style="background:#10b981;height:100%;transition:width 0.3s;" title="Insurance"></div>
<div id="barPMI" style="background:#ef4444;height:100%;transition:width 0.3s;" title="PMI"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#2563eb;border-radius:2px;margin-right:4px;"></span>P&amp;I</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#f59e0b;border-radius:2px;margin-right:4px;"></span>Property Tax</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#10b981;border-radius:2px;margin-right:4px;"></span>Insurance</span>
<span id="pmiLegend" style="display:none;"><span style="display:inline-block;width:10px;height:10px;background:#ef4444;border-radius:2px;margin-right:4px;"></span>PMI</span>
</div>
</div>

<!-- Amortization table -->
<div style="margin-top:24px;">
<div style="font-size:16px;font-weight:bold;margin-bottom:12px;color:#1e293b !important;color-scheme:light;">Amortization Schedule</div>

<div style="overflow-x:auto;">
<table style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#2563eb;color:white;">
<th style="padding:10px 8px;text-align:left;">Year</th>
<th style="padding:10px 8px;text-align:right;">Payment</th>
<th style="padding:10px 8px;text-align:right;">Principal</th>
<th style="padding:10px 8px;text-align:right;">Interest</th>
<th style="padding:10px 8px;text-align:right;">Balance</th>
</tr>
</thead>
<tbody id="amortFirst5"></tbody>
</table>
</div>

<details id="amortDetails" style="margin-top:0;">
<summary style="cursor:pointer;font-weight:bold;color:#2563eb;font-size:14px;padding:10px 8px;background:#eff6ff;border-radius:0 0 8px 8px;">Show remaining years</summary>
<div style="overflow-x:auto;">
<table style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#2563eb;color:white;">
<th style="padding:10px 8px;text-align:left;">Year</th>
<th style="padding:10px 8px;text-align:right;">Payment</th>
<th style="padding:10px 8px;text-align:right;">Principal</th>
<th style="padding:10px 8px;text-align:right;">Interest</th>
<th style="padding:10px 8px;text-align:right;">Balance</th>
</tr>
</thead>
<tbody id="amortRest"></tbody>
</table>
</div>
</details>
</div>

<!-- Rate comparison -->
<div style="margin-top:24px;padding:20px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;">
<div style="font-size:16px;font-weight:bold;margin-bottom:14px;color:#1e293b !important;color-scheme:light;">Rate Comparison</div>
<div id="rateComparison" style="display:grid;gap:8px;"></div>
</div>

</div>

<script>
function fmt(n){return '$'+Math.round(n).toLocaleString();}
function fmtR(n){return n.toFixed(3)+'%';}

function getTermYears(){
var radios=document.getElementsByName('loanTerm');
for(var i=0;i<radios.length;i++){if(radios[i].checked)return parseInt(radios[i].value);}
return 30;
}

function updateTermLabels(selected){
var terms=[15,20,30];
terms.forEach(function(t){
var el=document.getElementById('term'+t+'label');
if(t===selected){
el.style.borderColor='#2563eb';
el.style.background='#eff6ff';
el.style.color='#2563eb';
} else {
el.style.borderColor='#e2e8f0';
el.style.background='white';
el.style.color='#1e293b';
}
});
}

function calcPI(principal, annualRate, years){
var r=annualRate/100/12;
var n=years*12;
if(r===0) return principal/n;
return principal*(r*Math.pow(1+r,n))/(Math.pow(1+r,n)-1);
}

function buildAmort(principal, annualRate, years){
var r=annualRate/100/12;
var n=years*12;
var payment=calcPI(principal,annualRate,years);
var balance=principal;
var rows=[];
for(var y=1;y<=years;y++){
var yearPrincipal=0;
var yearInterest=0;
var yearPayment=0;
for(var m=0;m<12;m++){
var interest=balance*r;
var princ=payment-interest;
if(princ>balance) princ=balance;
balance-=princ;
yearInterest+=interest;
yearPrincipal+=princ;
yearPayment+=payment;
if(balance<0.01){balance=0;break;}
}
rows.push({year:y,payment:yearPayment,principal:yearPrincipal,interest:yearInterest,balance:Math.max(0,balance)});
if(balance===0) break;
}
return rows;
}

function amortRow(r,bg){
return '<tr style="background:'+bg+'">'+
'<td style="padding:8px;">Year '+r.year+'</td>'+
'<td style="padding:8px;text-align:right;">'+fmt(r.payment)+'</td>'+
'<td style="padding:8px;text-align:right;color:#0369a1;">'+fmt(r.principal)+'</td>'+
'<td style="padding:8px;text-align:right;color:#dc2626;">'+fmt(r.interest)+'</td>'+
'<td style="padding:8px;text-align:right;font-weight:bold;">'+fmt(r.balance)+'</td>'+
'</tr>';
}

function calcMort(){
var homePrice=parseFloat(document.getElementById('homePrice').value)||350000;
var dpPct=parseFloat(document.getElementById('downPct').value)||0;
var rate=parseFloat(document.getElementById('intRate').value)||6.5;
var years=getTermYears();
var taxRate=parseFloat(document.getElementById('propTax').value)||0;
var insAnnual=parseFloat(document.getElementById('insurance').value)||0;

updateTermLabels(years);

var downAmt=homePrice*(dpPct/100);
var loanAmt=homePrice-downAmt;

document.getElementById('dpPct').textContent=dpPct+'%';
document.getElementById('dpAmt').textContent='('+fmt(downAmt)+')';
document.getElementById('loanAmtDisplay').textContent=fmt(loanAmt);
document.getElementById('ratePct').textContent=rate.toFixed(3).replace(/\.?0+$/,'')+'%';
var taxMonthly=(homePrice*taxRate/100)/12;
document.getElementById('taxPct').textContent=taxRate.toFixed(1)+'%';
document.getElementById('taxAmt').textContent='('+fmt(taxMonthly)+'/mo)';

var hasPMI=dpPct<20;
var pmiMonthly=hasPMI?(loanAmt*0.005/12):0;

document.getElementById('pmiRow').style.display=hasPMI?'block':'none';
document.getElementById('pmiCell').style.display=hasPMI?'block':'none';
document.getElementById('pmiLegend').style.display=hasPMI?'inline':'none';

var pi=calcPI(loanAmt,rate,years);
var insMonthly=insAnnual/12;
var total=pi+taxMonthly+insMonthly+pmiMonthly;

document.getElementById('totalMonthly').textContent=fmt(total);
document.getElementById('piPayment').textContent=fmt(pi);
document.getElementById('taxPayment').textContent=fmt(taxMonthly);
document.getElementById('insPayment').textContent=fmt(insMonthly);
document.getElementById('pmiPayment').textContent=fmt(pmiMonthly);

// Total over loan life (P&I only for interest calc, full payment for lifetime)
var totalPI=pi*years*12;
var totalInterest=totalPI-loanAmt;
var totalLifetime=total*years*12;
document.getElementById('totalLifetime').textContent=fmt(totalLifetime);
document.getElementById('totalInterest').textContent=fmt(totalInterest);

// Bar
var piPct=(pi/total)*100;
var taxPct=(taxMonthly/total)*100;
var insPct=(insMonthly/total)*100;
var pmiPct=(pmiMonthly/total)*100;
document.getElementById('barPI').style.width=piPct+'%';
document.getElementById('barTax').style.width=taxPct+'%';
document.getElementById('barIns').style.width=insPct+'%';
document.getElementById('barPMI').style.width=pmiPct+'%';

// Amortization
var rows=buildAmort(loanAmt,rate,years);
var first5='';
var rest='';
rows.forEach(function(r,i){
var bg=i%2===0?'white':'#f8fafc';
if(i<5) first5+=amortRow(r,bg);
else rest+=amortRow(r,bg);
});
document.getElementById('amortFirst5').innerHTML=first5;
document.getElementById('amortRest').innerHTML=rest;
document.getElementById('amortDetails').style.display=rows.length>5?'block':'none';

// Rate comparison
var offsets=[-1.0,-0.5,0,0.5,1.0];
var compHTML='';
offsets.forEach(function(offset){
var r2=Math.max(0.125,rate+offset);
var pi2=calcPI(loanAmt,r2,years);
var total2=pi2+taxMonthly+insMonthly+pmiMonthly;
var diff=total2-total;
var isBase=offset===0;
var bg=isBase?'#eff6ff':'white';
var border=isBase?'2px solid #2563eb':'1px solid #e2e8f0';
var diffStr=isBase?'<span style="color:#2563eb;font-size:12px;">current rate</span>'
:(diff>0?'<span style="color:#dc2626;font-size:12px;">+'+fmt(diff)+'/mo</span>'
:'<span style="color:#059669;font-size:12px;">'+fmt(diff)+'/mo</span>');
compHTML+='<div style="display:flex;justify-content:space-between;align-items:center;padding:12px;background:'+bg+';border:'+border+';border-radius:8px;">';
compHTML+='<div><strong>'+r2.toFixed(3).replace(/0+$/,'').replace(/\.$/,'')+'%</strong>'+(offset!==0?' <span style="font-size:12px;color:#64748b;">('+( offset>0?'+':'')+offset.toFixed(1)+'%)</span>':'')+'</div>';
compHTML+='<div style="text-align:right;"><span style="font-size:18px;font-weight:bold;">'+fmt(total2)+'/mo</span> '+diffStr+'</div>';
compHTML+='</div>';
});
document.getElementById('rateComparison').innerHTML=compHTML;
}

// Attach term radio change to also update labels
document.getElementsByName('loanTerm').forEach(function(r){
r.addEventListener('change',function(){calcMort();});
});

// Attach term label clicks
[15,20,30].forEach(function(t){
document.getElementById('term'+t+'label').addEventListener('click',function(){
document.querySelector('input[name="loanTerm"][value="'+t+'"]').checked=true;
calcMort();
});
});

calcMort();
</script>

---

## How to Use This Calculator

1. **Enter your home price** — the purchase price or estimated value of the home you're buying
2. **Set your down payment** — drag the slider to your planned down payment percentage; 20% avoids PMI
3. **Choose your interest rate** — use your pre-approval rate or current market rates; adjust the slider in 0.125% increments
4. **Select a loan term** — 15 years means higher monthly payments but far less total interest; 30 years lowers your payment
5. **Add property tax rate** — check your county assessor's website for the local rate (national average is ~1.1%)
6. **Enter annual home insurance** — get quotes from insurers or use $1,000–$2,000 as a starting estimate

All results update instantly as you adjust inputs. No sign-up or data sharing required.

---

## Understanding Your Mortgage Payment

Most homeowners are surprised that their mortgage payment covers far more than just repaying the loan. Here is what makes up your total monthly obligation:

### Principal & Interest (P&I)

This is the core loan repayment calculated using standard amortization. Early payments are mostly interest; later payments shift toward principal. Your P&I payment stays fixed for the life of a fixed-rate mortgage — one of its key advantages over renting or adjustable-rate loans.

### Property Tax

Collected by local governments and typically rolled into your monthly payment through an escrow account. Rates vary widely — from under 0.5% in states like Hawaii to over 2% in New Jersey and Illinois. The national average is approximately 1.1% of home value per year.

### Home Insurance (Homeowner's Insurance)

Required by virtually all mortgage lenders. It covers damage from fire, storms, theft, and liability claims. Annual premiums typically run $1,000–$2,500 depending on your home's value, location, and coverage level. Shop at least 3 insurers to compare.

### PMI (Private Mortgage Insurance)

Required when your down payment is below 20% of the home price. PMI protects the lender — not you — in case of default. This calculator uses a standard rate of 0.5% of the loan amount annually, split into monthly installments. Once your equity reaches 20% (through payments or appreciation), you can request PMI removal from your lender. PMI typically cancels automatically at 22% equity under the Homeowners Protection Act.

---

## Tips to Get a Better Mortgage Rate

### 1. Improve your credit score before applying

Lenders offer their best rates to borrowers with scores above 740. Even a 20-point improvement can drop your rate by 0.125%–0.25%, saving tens of thousands over the life of the loan. Pay down credit card balances, dispute any errors, and avoid opening new accounts in the 6 months before applying.

### 2. Compare at least 3–5 lenders

Rates vary more than most buyers realize. Credit unions, regional banks, online lenders, and mortgage brokers all price risk differently. Shopping multiple lenders within a 14-day window counts as only one credit inquiry under FICO scoring rules.

### 3. Consider paying points to buy down your rate

One discount point costs 1% of the loan amount and typically reduces your rate by 0.25%. Use the rate comparison table above to estimate how much a lower rate saves you per month — then divide the cost of points by the monthly savings to find your break-even period. If you plan to stay in the home longer than the break-even, buying points usually makes sense.

### 4. Time your lock strategically

Mortgage rates move daily with bond markets. Once you find a rate you are comfortable with, lock it in writing — most locks are free for 30–60 days. Floating (not locking) only makes sense if you have strong conviction rates will fall before closing.

---

## Related Tools

> Calculate your monthly budget after housing costs → [Budget Planner](/tools/budget-planner/)
> Find out how long to save your down payment → [Savings Goal Calculator](/tools/savings-goal-calculator/)
> Compare mortgage payoff with debt avalanche → [Debt Payoff Calculator](/tools/debt-payoff-calculator/)
> Calculate your net take-home pay → [Salary Calculator](/tools/salary-calculator/)
> See how investments grow alongside home equity → [Compound Interest Calculator](/tools/compound-interest-calculator/)

---

## Related Articles

- [How Much House Can I Afford in 2026?](/posts/how-much-house-can-i-afford-2026/)
- [30-Year vs 15-Year Mortgage: Which Is Right for You?](/posts/30-year-vs-15-year-mortgage/)
- [Best Mortgage Lenders 2026: Rates, Fees & Reviews](/posts/best-mortgage-lenders-2026/)
- [How to Improve Your Credit Score Before Buying a Home](/posts/improve-credit-score-before-buying-home/)
- [First-Time Homebuyer Guide: From Pre-Approval to Closing](/posts/first-time-homebuyer-guide-2026/)

---

## Productivity Works Free Tools

All our financial calculators are **100% free**, run entirely in your browser, and never store your data.

[Browse all free tools](/tools/)

*This article contains affiliate links. We may earn a commission at no extra cost to you.*
