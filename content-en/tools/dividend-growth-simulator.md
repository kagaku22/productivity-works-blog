---
title: "Dividend Growth Simulator | Calculate Annual Dividend Income from Investment Amount & Yield [2026]"
date: 2026-05-16
draft: false
slug: "dividend-growth-simulator"
description: "Enter your investment amount and dividend yield to automatically calculate annual and monthly dividend income. Model NISA tax-free benefits, dividend reinvestment compounding, and compare popular high-yield ETFs. Free dividend calculator."
author: "Productivity Works Editorial Team"
categories:
  - "Free Tools"
tags:
  - "dividends"
  - "simulation"
  - "high yield"
  - "NISA"
  - "calculator"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/dividend-growth-simulator.png"
  alt: "Dividend Growth Simulator | Calculate Annual Dividend Income from Investment Amount & Yield"
  relative: false
---

*This article contains affiliate links.*

# Dividend Growth Simulator [2026]

Enter your investment amount and dividend yield to automatically calculate your **annual and monthly dividend income**, the **NISA tax-free benefit**, and the **compounding effect of reinvesting dividends**.

<div id="div-calc" style="max-width:700px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Investment Amount (¥10K units)</label>
<input type="range" id="divAmount" min="10" max="5000" step="10" value="500" oninput="calcDiv()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>¥100K</span><span id="divAmtVal" style="font-weight:bold;font-size:20px;color:#2563eb;">¥5,000,000</span><span>¥50M</span></div>
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Dividend Yield (annual)</label>
<input type="range" id="divYield" min="0.5" max="10" step="0.1" value="3.5" oninput="calcDiv()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>0.5%</span><span id="divYldVal" style="font-weight:bold;font-size:20px;color:#10b981;">3.5%</span><span>10%</span></div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:16px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Account Type</label>
<select id="divAccount" onchange="calcDiv()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="nisa">NISA (tax-free)</option>
<option value="tokutei">Taxable account (20.315% tax)</option>
</select>
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Dividend Reinvestment</label>
<select id="divReinvest" onchange="calcDiv()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="yes">Yes (compound growth)</option>
<option value="no">No (receive dividends as cash)</option>
</select>
</div>
</div>

<div style="margin-top:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">Investment Period</label>
<input type="range" id="divYears" min="1" max="30" step="1" value="10" oninput="calcDiv()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>1 yr</span><span id="divYrsVal" style="font-weight:bold;font-size:18px;color:#f59e0b;">10 years</span><span>30 yrs</span></div>
</div>

<div id="divResult" style="margin-top:24px;"></div>

</div>

<div id="divTimeline" style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;"></div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">Popular High-Yield ETF & Stock Comparison</h3>
<div id="divETF"></div>
</div>

<div style="margin-top:24px;padding:24px;border:2px solid #8b5cf6;border-radius:12px;background:#f5f3ff;">
<h3 style="margin:0 0 12px;color:#6d28d9;font-size:16px;">NISA vs. Taxable Account: Dividend Take-Home Comparison</h3>
<div id="divNISA"></div>
</div>

</div>

<script>
function fmt(n){return Math.round(n).toLocaleString();}

function calcDiv(){
  var amount=+document.getElementById('divAmount').value;
  var yieldRate=+document.getElementById('divYield').value;
  var account=document.getElementById('divAccount').value;
  var reinvest=document.getElementById('divReinvest').value;
  var years=+document.getElementById('divYears').value;

  document.getElementById('divAmtVal').textContent='¥'+fmt(amount*10000);
  document.getElementById('divYldVal').textContent=yieldRate.toFixed(1)+'%';
  document.getElementById('divYrsVal').textContent=years+' year'+(years>1?'s':'');

  var principal=amount*10000;
  var rate=yieldRate/100;
  var taxRate=account==='nisa'?0:0.20315;

  var annualDiv=principal*rate;
  var annualAfterTax=annualDiv*(1-taxRate);
  var monthlyAfterTax=annualAfterTax/12;

  var html='<div style="text-align:center;padding:20px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">Annual Dividend Income (after tax)</div>';
  html+='<div style="font-size:40px;font-weight:bold;color:#10b981;">¥'+fmt(annualAfterTax)+'</div>';
  html+='<div style="font-size:14px;color:#64748b;margin-top:4px;">Monthly approx. <strong style="color:#2563eb;">¥'+fmt(monthlyAfterTax)+'</strong></div>';
  html+='</div>';

  html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-top:16px;text-align:center;">';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">Pre-tax dividend</div><div style="font-size:18px;font-weight:bold;color:#1e293b !important;color-scheme:light;">¥'+fmt(annualDiv)+'/yr</div></div>';
  var taxAmount=annualDiv*taxRate;
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">Tax withheld</div><div style="font-size:18px;font-weight:bold;color:'+(taxRate>0?'#ef4444':'#10b981')+';">¥'+fmt(taxAmount)+'/yr</div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">Effective yield (after tax)</div><div style="font-size:18px;font-weight:bold;color:#f59e0b;">'+(yieldRate*(1-taxRate)).toFixed(2)+'%</div></div>';
  html+='</div>';

  if(account==='nisa'){
html+='<div style="margin-top:8px;text-align:center;font-size:12px;color:#10b981;font-weight:bold;">NISA account: dividends are tax-free! Annual tax saving of ¥'+fmt(annualDiv*0.20315)+'</div>';
  }

  document.getElementById('divResult').innerHTML=html;

  var thtml='<h3 style="margin:0 0 12px;color:#166534;font-size:16px;">Dividend Income Over Time ('+years+' year'+(years>1?'s':'')+')</h3>';
  thtml+='<table style="width:100%;border-collapse:collapse;font-size:13px;">';
  thtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:6px;">Year</th><th style="text-align:right;padding:6px;">Principal</th><th style="text-align:right;padding:6px;">Annual Dividend</th><th style="text-align:right;padding:6px;">Cumulative Dividends</th></tr>';

  var balance=principal;
  var totalDiv=0;
  var showYears=[];
  if(years<=10){for(var i=1;i<=years;i++) showYears.push(i);}
  else{showYears=[1,2,3,5];for(var i=10;i<=years;i+=5) showYears.push(i);if(showYears[showYears.length-1]!==years) showYears.push(years);}

  var yearData=[];
  for(var y=1;y<=years;y++){
var div=balance*rate;
var divNet=div*(1-taxRate);
totalDiv+=divNet;
if(reinvest==='yes') balance+=divNet;
yearData.push({year:y,balance:balance,div:divNet,total:totalDiv});
  }

  for(var i=0;i<showYears.length;i++){
var d=yearData[showYears[i]-1];
var bg=i%2===0?'#fff':'#f0fdf4';
var bold=showYears[i]===years?'font-weight:bold;':'';
thtml+='<tr style="background:'+bg+';'+bold+'">';
thtml+='<td style="padding:6px;">Year '+d.year+'</td>';
thtml+='<td style="padding:6px;text-align:right;">¥'+fmt(d.balance)+'</td>';
thtml+='<td style="padding:6px;text-align:right;">¥'+fmt(d.div)+'</td>';
thtml+='<td style="padding:6px;text-align:right;color:#10b981;">¥'+fmt(d.total)+'</td>';
thtml+='</tr>';
  }
  thtml+='</table>';

  var finalData=yearData[years-1];
  thtml+='<div style="margin-top:12px;padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;text-align:center;">';
  thtml+='<span style="font-size:13px;color:#64748b;">Portfolio value after '+years+' year'+(years>1?'s':'')+': </span>';
  thtml+='<span style="font-size:20px;font-weight:bold;color:#166534;">¥'+fmt(reinvest==='yes'?finalData.balance:principal)+'</span>';
  if(reinvest==='yes'){
thtml+='<span style="font-size:13px;color:#64748b;"> + cumulative dividends: </span>';
thtml+='<span style="font-size:13px;font-weight:bold;color:#10b981;">reinvested</span>';
  } else {
thtml+='<span style="font-size:13px;color:#64748b;"> + cumulative dividends received: </span>';
thtml+='<span style="font-size:20px;font-weight:bold;color:#10b981;">¥'+fmt(finalData.total)+'</span>';
  }
  thtml+='</div>';

  if(reinvest==='yes'){
var noReinvestTotal=principal*rate*(1-taxRate)*years;
var diff=finalData.total-noReinvestTotal;
thtml+='<div style="margin-top:8px;font-size:12px;color:#166534;text-align:center;">Reinvestment compounding bonus: <strong>+¥'+fmt(diff)+'</strong> (vs. no reinvestment)</div>';
  }

  document.getElementById('divTimeline').innerHTML=thtml;

  var etfs=[
{name:'VYM',desc:'Vanguard High Dividend Yield ETF',yield:2.8,type:'US ETF'},
{name:'HDV',desc:'iShares Core High Dividend ETF',yield:3.5,type:'US ETF'},
{name:'SPYD',desc:'SPDR Portfolio S&P 500 High Dividend ETF',yield:4.5,type:'US ETF'},
{name:'1489',desc:'Nikkei High Dividend 50 ETF',yield:3.2,type:'JP ETF'},
{name:'2914',desc:'Japan Tobacco (JT)',yield:4.8,type:'JP Stock'},
{name:'8593',desc:'Mitsubishi HC Capital',yield:3.8,type:'JP Stock'}
  ];

  var ehtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;">';
  for(var i=0;i<etfs.length;i++){
var annDiv=principal*etfs[i].yield/100*(account==='nisa'?1:0.79685);
ehtml+='<div style="padding:10px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
ehtml+='<div style="display:flex;justify-content:space-between;align-items:center;">';
ehtml+='<div><span style="font-weight:bold;font-size:14px;color:#1e293b !important;color-scheme:light;">'+etfs[i].name+'</span><span style="font-size:11px;color:#64748b;margin-left:4px;">'+etfs[i].type+'</span></div>';
ehtml+='<span style="font-size:14px;font-weight:bold;color:#10b981;">'+etfs[i].yield+'%</span>';
ehtml+='</div>';
ehtml+='<div style="font-size:11px;color:#64748b;">'+etfs[i].desc+'</div>';
ehtml+='<div style="font-size:12px;margin-top:4px;color:#2563eb;">Annual dividend: <strong>¥'+fmt(annDiv)+'</strong> (after tax)</div>';
ehtml+='</div>';
  }
  ehtml+='</div>';
  ehtml+='<div style="margin-top:8px;font-size:11px;color:#92400e;text-align:center;">*Dividend yields are reference values as of May 2026. Actual dividends fluctuate.</div>';
  document.getElementById('divETF').innerHTML=ehtml;

  var nisaDiv=principal*rate;
  var tokuteiDiv=nisaDiv*0.79685;
  var diff10=nisaDiv*10-tokuteiDiv*10;
  var nhtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;text-align:center;">';
  nhtml+='<div style="padding:16px;background:#fff;border-radius:8px;border:2px solid #10b981;">';
  nhtml+='<div style="font-size:12px;color:#166534;font-weight:bold;">NISA (tax-free)</div>';
  nhtml+='<div style="font-size:24px;font-weight:bold;color:#10b981;">¥'+fmt(nisaDiv)+'/yr</div>';
  nhtml+='<div style="font-size:12px;color:#64748b;">10-year total: ¥'+fmt(nisaDiv*10)+'</div>';
  nhtml+='</div>';
  nhtml+='<div style="padding:16px;background:#fff;border-radius:8px;border:2px solid #94a3b8;">';
  nhtml+='<div style="font-size:12px;color:#64748b;font-weight:bold;">Taxable account</div>';
  nhtml+='<div style="font-size:24px;font-weight:bold;color:#64748b;">¥'+fmt(tokuteiDiv)+'/yr</div>';
  nhtml+='<div style="font-size:12px;color:#64748b;">10-year total: ¥'+fmt(tokuteiDiv*10)+'</div>';
  nhtml+='</div>';
  nhtml+='</div>';
  nhtml+='<div style="margin-top:12px;text-align:center;padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  nhtml+='<div style="font-size:13px;color:#64748b;">With NISA, over 10 years you keep an extra</div>';
  nhtml+='<div style="font-size:28px;font-weight:bold;color:#10b981;">+¥'+fmt(diff10)+'</div>';
  nhtml+='<div style="font-size:13px;color:#64748b;">in dividend income</div>';
  nhtml+='</div>';
  document.getElementById('divNISA').innerHTML=nhtml;
}

document.addEventListener('DOMContentLoaded',function(){calcDiv();});
calcDiv();
</script>

---

## Dividend Investing Basics

### What are dividends?
Dividends are cash payments a company distributes to shareholders from its profits. Simply holding qualifying stocks or ETFs earns you payouts one to four times per year.

### How is dividend yield calculated?

```
Dividend Yield (%) = Annual Dividend Per Share / Share Price × 100
```

Example: A stock priced at ¥1,000 paying ¥40/year has a 4.0% yield.

### High-yield investing: pros and cons

| Pros | Cons |
|------|------|
| Regular passive income | Share price can fall |
| Dividend reinvestment compounds returns | Dividends can be cut or suspended |
| NISA makes dividends tax-free | May underperform growth stocks |
| Psychologically easier to hold | High yield alone can signal risk |

### Starting dividend investing with NISA
The NISA growth investment quota (¥2,400,000/year) lets you receive dividends **tax-free**. On a 3.5% yield position, eliminating the usual 20.315% withholding effectively adds ~0.7 percentage points to your take-home yield.

---

## Related Tools

- [iDeCo Simulator](/en/tools/ideco-simulator/) — Model tax-deferred pension contributions alongside dividend income
- [Savings Goal Calculator](/en/tools/savings-goal-calculator/) — Calculate how long to build your target investment principal
- [Asset Allocation Simulator](/en/tools/asset-allocation-simulator/) — Track dividend-generating investments as part of your overall net worth

</div>
