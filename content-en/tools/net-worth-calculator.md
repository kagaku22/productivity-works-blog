---
title: "Net Worth Calculator | Track Your Financial Health"
date: 2026-05-16
draft: false
slug: "net-worth-calculator"
description: "Free net worth calculator. Enter your assets and liabilities to instantly calculate your net worth, debt-to-asset ratio, and see how you compare to US benchmarks by age."
categories: ["Free Tools"]
tags: ["net worth calculator", "net worth", "personal finance", "financial health", "calculator", "assets", "liabilities"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/net-worth-calculator.png"
  alt: "Net Worth Calculator"
  relative: false
---

*This article contains affiliate links. We may earn a commission at no extra cost to you.*

# Net Worth Calculator

Enter your assets and liabilities below to instantly calculate your **net worth** and see how your financial health stacks up.

<div id="nw-calc" style="max-width:760px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;">

<!-- ASSETS SECTION -->
<div style="padding:24px;border:2px solid #059669;border-radius:12px;background:#f0fdf4;margin-bottom:20px;">

<h2 style="margin:0 0 20px 0;font-size:20px;color:#059669;">Assets</h2>

<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">Cash &amp; Savings</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Checking account</label><input type="number" id="aCash" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Savings account</label><input type="number" id="aSavings" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Emergency fund</label><input type="number" id="aEmergency" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">Investments</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">401(k) / 403(b)</label><input type="number" id="a401k" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">IRA / Roth IRA</label><input type="number" id="aIRA" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Brokerage account</label><input type="number" id="aBrokerage" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Crypto</label><input type="number" id="aCrypto" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">Property</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Home value</label><input type="number" id="aHome" min="0" step="1000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Other real estate</label><input type="number" id="aRealEstate" min="0" step="1000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="margin-bottom:20px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">Other Assets</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Vehicles</label><input type="number" id="aVehicles" min="0" step="500" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Valuables (jewelry, art, collectibles)</label><input type="number" id="aValuables" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Business equity</label><input type="number" id="aBusiness" min="0" step="1000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="padding:16px;background:#059669;border-radius:8px;display:flex;justify-content:space-between;align-items:center;">
<span style="color:white;font-weight:bold;font-size:16px;">Total Assets</span>
<span id="totalAssets" style="color:white;font-weight:bold;font-size:24px;">$0</span>
</div>

</div>

<!-- LIABILITIES SECTION -->
<div style="padding:24px;border:2px solid #dc2626;border-radius:12px;background:#fef2f2;margin-bottom:20px;">

<h2 style="margin:0 0 20px 0;font-size:20px;color:#dc2626;">Liabilities</h2>

<div style="display:grid;gap:10px;margin-bottom:20px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Mortgage balance</label><input type="number" id="lMortgage" min="0" step="1000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Student loans</label><input type="number" id="lStudent" min="0" step="500" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Auto loans</label><input type="number" id="lAuto" min="0" step="500" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Credit card debt</label><input type="number" id="lCredit" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">$</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">Other debt</label><input type="number" id="lOther" min="0" step="100" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>

<div style="padding:16px;background:#dc2626;border-radius:8px;display:flex;justify-content:space-between;align-items:center;">
<span style="color:white;font-weight:bold;font-size:16px;">Total Liabilities</span>
<span id="totalLiabilities" style="color:white;font-weight:bold;font-size:24px;">$0</span>
</div>

</div>

<!-- RESULTS PANEL -->
<div id="nwResults" style="padding:28px;border-radius:12px;background:#eef2ff;border:2px solid #4f46e5;margin-bottom:20px;">

<div style="text-align:center;margin-bottom:24px;">
<div style="font-size:14px;color:#64748b;text-transform:uppercase;letter-spacing:0.08em;margin-bottom:6px;">Your Net Worth</div>
<div id="netWorthDisplay" style="font-size:52px;font-weight:bold;color:#4f46e5;line-height:1.1;">$0</div>
<div id="debtRatioDisplay" style="font-size:14px;color:#64748b;margin-top:8px;">Debt-to-Asset Ratio: —</div>
</div>

<!-- Asset allocation breakdown -->
<div style="margin-bottom:20px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:8px;">Asset Allocation</div>
<div id="assetBar" style="height:28px;border-radius:8px;overflow:hidden;display:flex;background:#e2e8f0;">
<div id="barCash" style="background:#059669;height:100%;transition:width 0.3s;" title="Cash &amp; Savings"></div>
<div id="barInvest" style="background:#10b981;height:100%;transition:width 0.3s;" title="Investments"></div>
<div id="barProperty" style="background:#34d399;height:100%;transition:width 0.3s;" title="Property"></div>
<div id="barOther" style="background:#6ee7b7;height:100%;transition:width 0.3s;" title="Other"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#059669;border-radius:2px;margin-right:4px;"></span>Cash &amp; Savings <span id="pctCash" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#10b981;border-radius:2px;margin-right:4px;"></span>Investments <span id="pctInvest" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#34d399;border-radius:2px;margin-right:4px;"></span>Property <span id="pctProperty" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#6ee7b7;border-radius:2px;margin-right:4px;"></span>Other <span id="pctOther" style="font-weight:bold;">0%</span></span>
</div>
</div>

<!-- Liability breakdown -->
<div id="liabBreakdownWrap" style="display:none;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:8px;">Liability Breakdown</div>
<div id="liabBar" style="height:28px;border-radius:8px;overflow:hidden;display:flex;background:#e2e8f0;">
<div id="lbarMortgage" style="background:#dc2626;height:100%;transition:width 0.3s;" title="Mortgage"></div>
<div id="lbarStudent" style="background:#ef4444;height:100%;transition:width 0.3s;" title="Student Loans"></div>
<div id="lbarAuto" style="background:#f87171;height:100%;transition:width 0.3s;" title="Auto Loans"></div>
<div id="lbarCredit" style="background:#fca5a5;height:100%;transition:width 0.3s;" title="Credit Cards"></div>
<div id="lbarOther" style="background:#fecaca;height:100%;transition:width 0.3s;" title="Other"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#dc2626;border-radius:2px;margin-right:4px;"></span>Mortgage <span id="lpctMortgage" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#ef4444;border-radius:2px;margin-right:4px;"></span>Student <span id="lpctStudent" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#f87171;border-radius:2px;margin-right:4px;"></span>Auto <span id="lpctAuto" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#fca5a5;border-radius:2px;margin-right:4px;"></span>Credit Cards <span id="lpctCredit" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#fecaca;border-radius:2px;margin-right:4px;"></span>Other <span id="lpctOther" style="font-weight:bold;">0%</span></span>
</div>
</div>

</div>

<!-- BENCHMARK SECTION -->
<div style="padding:24px;border-radius:12px;background:#f8fafc;border:1px solid #e2e8f0;margin-bottom:20px;">

<h3 style="margin:0 0 16px 0;font-size:18px;color:#1e293b;">How Do You Compare?</h3>
<p style="font-size:13px;color:#64748b;margin:0 0 16px 0;">Median net worth by age group in the United States (Federal Reserve data).</p>

<div style="overflow-x:auto;">
<table id="benchmarkTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#4f46e5;color:white;">
<th style="padding:10px 14px;text-align:left;border-radius:0;">Age Group</th>
<th style="padding:10px 14px;text-align:right;">Median Net Worth (US)</th>
<th style="padding:10px 14px;text-align:center;">Your Position</th>
</tr>
</thead>
<tbody id="benchmarkBody"></tbody>
</table>
</div>

<div style="margin-top:12px;font-size:12px;color:#64748b;">Select your age group above or scroll to see all benchmarks. Data sourced from Federal Reserve Survey of Consumer Finances.</div>

<div style="margin-top:16px;">
<label style="display:block;font-size:13px;font-weight:bold;color:#64748b;margin-bottom:6px;">Your Age Group</label>
<select id="ageGroup" onchange="calcNW()" style="padding:9px 12px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;background:white;">
<option value="">— Select age group —</option>
<option value="0">Under 35</option>
<option value="1">35–44</option>
<option value="2">45–54</option>
<option value="3">55–64</option>
<option value="4">65–74</option>
<option value="5">75+</option>
</select>
</div>

</div>

<!-- GOAL TRACKER -->
<div style="padding:24px;border-radius:12px;background:#f8fafc;border:1px solid #e2e8f0;margin-bottom:8px;">

<h3 style="margin:0 0 16px 0;font-size:18px;color:#1e293b;">Goal Tracker</h3>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Net Worth Goal ($)</label>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;">$</span>
<input type="number" id="nwGoal" min="0" step="10000" value="1000000" oninput="calcNW()" style="flex:1;padding:9px 12px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;box-sizing:border-box;">
</div>
</div>

<div style="margin-bottom:10px;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;margin-bottom:6px;">
<span>Progress toward goal</span>
<span id="goalPctLabel" style="font-weight:bold;color:#4f46e5;">0%</span>
</div>
<div style="height:20px;background:#e2e8f0;border-radius:10px;overflow:hidden;">
<div id="goalBar" style="height:100%;background:#4f46e5;border-radius:10px;transition:width 0.4s;width:0%;"></div>
</div>
</div>

<div id="goalMessage" style="font-size:14px;color:#4f46e5;font-weight:bold;margin-top:8px;">You're 0% of the way there.</div>

</div>

</div>

<script>
var NW_BENCHMARKS=[
  {label:'Under 35',median:39000},
  {label:'35\u201344',median:135600},
  {label:'45\u201354',median:247200},
  {label:'55\u201364',median:364500},
  {label:'65\u201374',median:409900},
  {label:'75+',median:335600}
];

function v(id){return parseFloat(document.getElementById(id).value)||0;}

function fmt(n){
  var abs=Math.abs(n);
  var s='$'+abs.toLocaleString('en-US',{minimumFractionDigits:0,maximumFractionDigits:0});
  return n<0?'-'+s:s;
}

function pct(part,total){
  if(total<=0) return 0;
  return Math.round((part/total)*100);
}

function calcNW(){
  // Assets
  var cash=v('aCash')+v('aSavings')+v('aEmergency');
  var invest=v('a401k')+v('aIRA')+v('aBrokerage')+v('aCrypto');
  var property=v('aHome')+v('aRealEstate');
  var other=v('aVehicles')+v('aValuables')+v('aBusiness');
  var totalAssets=cash+invest+property+other;

  // Liabilities
  var lMortgage=v('lMortgage');
  var lStudent=v('lStudent');
  var lAuto=v('lAuto');
  var lCredit=v('lCredit');
  var lOther=v('lOther');
  var totalLiabilities=lMortgage+lStudent+lAuto+lCredit+lOther;

  var netWorth=totalAssets-totalLiabilities;

  // Update totals
  document.getElementById('totalAssets').textContent=fmt(totalAssets);
  document.getElementById('totalLiabilities').textContent=fmt(totalLiabilities);

  // Net worth display
  var nwEl=document.getElementById('netWorthDisplay');
  nwEl.textContent=fmt(netWorth);
  nwEl.style.color=netWorth>=0?'#4f46e5':'#dc2626';

  // Debt-to-asset ratio
  var dtaEl=document.getElementById('debtRatioDisplay');
  if(totalAssets>0){
var dta=((totalLiabilities/totalAssets)*100).toFixed(1);
dtaEl.textContent='Debt-to-Asset Ratio: '+dta+'%';
  } else {
dtaEl.textContent='Debt-to-Asset Ratio: —';
  }

  // Asset allocation bar
  var pCash=pct(cash,totalAssets);
  var pInvest=pct(invest,totalAssets);
  var pProperty=pct(property,totalAssets);
  var pOther=pct(other,totalAssets);
  // Adjust so bars sum to 100 when totalAssets>0
  var remainder=totalAssets>0?Math.max(0,100-pCash-pInvest-pProperty-pOther):0;
  pOther+=remainder;

  document.getElementById('barCash').style.width=pCash+'%';
  document.getElementById('barInvest').style.width=pInvest+'%';
  document.getElementById('barProperty').style.width=pProperty+'%';
  document.getElementById('barOther').style.width=pOther+'%';
  document.getElementById('pctCash').textContent=pCash+'%';
  document.getElementById('pctInvest').textContent=pInvest+'%';
  document.getElementById('pctProperty').textContent=pProperty+'%';
  document.getElementById('pctOther').textContent=pOther+'%';

  // Liability breakdown bar
  var liabWrap=document.getElementById('liabBreakdownWrap');
  if(totalLiabilities>0){
liabWrap.style.display='block';
var lpM=pct(lMortgage,totalLiabilities);
var lpS=pct(lStudent,totalLiabilities);
var lpA=pct(lAuto,totalLiabilities);
var lpC=pct(lCredit,totalLiabilities);
var lpO=pct(lOther,totalLiabilities);
var lRemainder=Math.max(0,100-lpM-lpS-lpA-lpC-lpO);
lpO+=lRemainder;
document.getElementById('lbarMortgage').style.width=lpM+'%';
document.getElementById('lbarStudent').style.width=lpS+'%';
document.getElementById('lbarAuto').style.width=lpA+'%';
document.getElementById('lbarCredit').style.width=lpC+'%';
document.getElementById('lbarOther').style.width=lpO+'%';
document.getElementById('lpctMortgage').textContent=lpM+'%';
document.getElementById('lpctStudent').textContent=lpS+'%';
document.getElementById('lpctAuto').textContent=lpA+'%';
document.getElementById('lpctCredit').textContent=lpC+'%';
document.getElementById('lpctOther').textContent=lpO+'%';
  } else {
liabWrap.style.display='none';
  }

  // Benchmark table
  var ageIdx=document.getElementById('ageGroup').value;
  var tbody='';
  NW_BENCHMARKS.forEach(function(b,i){
var isSelected=(ageIdx!=='' && parseInt(ageIdx)===i);
var bg=isSelected?'#eef2ff':(i%2===0?'white':'#f8fafc');
var border=isSelected?'2px solid #4f46e5':'1px solid transparent';
var position='';
if(isSelected){
if(netWorth>=b.median){
var abovePct=Math.round(((netWorth-b.median)/b.median)*100);
position='<span style="color:#059669;font-weight:bold;">Above median (+'+abovePct+'%)</span>';
} else {
var belowPct=Math.round(((b.median-netWorth)/b.median)*100);
position='<span style="color:#dc2626;font-weight:bold;">Below median (-'+belowPct+'%)</span>';
}
} else {
position='<span style="color:#94a3b8;">—</span>';
}
tbody+='<tr style="background:'+bg+';border:'+border+';">';
tbody+='<td style="padding:10px 14px;font-weight:'+(isSelected?'bold':'normal')+';">'+b.label+'</td>';
tbody+='<td style="padding:10px 14px;text-align:right;">$'+b.median.toLocaleString('en-US')+'</td>';
tbody+='<td style="padding:10px 14px;text-align:center;">'+position+'</td>';
tbody+='</tr>';
  });
  document.getElementById('benchmarkBody').innerHTML=tbody;

  // Goal tracker
  var goal=v('nwGoal');
  var goalPct=goal>0?Math.min(100,Math.max(0,Math.round((netWorth/goal)*100))):0;
  document.getElementById('goalBar').style.width=goalPct+'%';
  document.getElementById('goalPctLabel').textContent=goalPct+'%';
  var goalMsg=document.getElementById('goalMessage');
  if(netWorth<=0){
goalMsg.textContent="Build your assets and reduce debt to start making progress toward your goal.";
goalMsg.style.color='#dc2626';
  } else if(goalPct>=100){
goalMsg.textContent="Congratulations — you've reached your net worth goal!";
goalMsg.style.color='#059669';
  } else {
var remaining=goal-netWorth;
goalMsg.textContent="You're "+goalPct+"% of the way there. "+fmt(remaining)+" to go.";
goalMsg.style.color='#4f46e5';
  }
}

calcNW();
</script>

---

## How to Use This Calculator

1. **Enter your assets** — fill in what you own: bank balances, investment accounts, property values, and other valuables. Use current market values, not purchase prices.
2. **Enter your liabilities** — list every debt: mortgage balance, student loans, car loans, and credit card balances.
3. **Select your age group** — see how your net worth compares to US median benchmarks.
4. **Set a goal** — enter a target net worth to track your progress.

The calculator updates instantly as you type. Your data never leaves your browser.

---

## What Is Net Worth and Why Does It Matter?

Net worth is the single most important number in personal finance. It is simply what you own (assets) minus what you owe (liabilities). A positive net worth means your assets exceed your debts; a negative net worth — common for young adults with student loans — means you owe more than you own. Tracking this number over time is the best way to measure whether you are genuinely building wealth or just keeping up with payments.

Net worth matters because income alone does not tell the full story. Someone earning $200,000 per year but spending $210,000 is losing ground, while someone earning $60,000 and investing consistently builds real wealth. By calculating your net worth regularly — once a quarter or once a year — you get an honest snapshot of your financial progress that no single paycheck or bank balance can provide.

---

## How to Increase Your Net Worth

### 1. Earn more

Every dollar of additional income that you do not spend goes directly toward building net worth. Negotiate your salary, develop a marketable skill, or start a side hustle. Even an extra $300 per month invested over 20 years at 7% becomes over $175,000.

### 2. Spend less

Reducing expenses is often faster than increasing income. Audit your subscriptions, refinance high-rate debt, and distinguish wants from needs. The goal is not deprivation — it is ensuring your spending is intentional and aligned with your values.

### 3. Pay off high-interest debt

Credit card balances at 20%+ APR destroy net worth faster than almost anything else. Prioritize eliminating high-interest debt using the avalanche method (highest rate first) before aggressively investing. Every dollar paid off high-interest debt is a guaranteed return equal to that interest rate.

### 4. Invest consistently

Wealth is built through ownership — of index funds, real estate, a business, or other appreciating assets. Automate contributions to your 401(k) and IRA every month, and let compound growth do the heavy lifting over time. Time in the market consistently outperforms trying to time the market.

---

## Related Tools

> Plan your monthly spending to free up more to invest — [Budget Planner](/tools/budget-planner/)
> Calculate how long to reach a savings target — [Savings Goal Calculator](/tools/savings-goal-calculator/)
> See your fastest path to becoming debt-free — [Debt Payoff Calculator](/tools/debt-payoff-calculator/)
> Project your retirement nest egg — [Retirement Calculator](/tools/retirement-calculator/)
> See how compound growth builds wealth over time — [Compound Interest Calculator](/tools/compound-interest-calculator/)
> Estimate your monthly mortgage payment — [Mortgage Calculator](/tools/mortgage-calculator/)
> Plan your path to financial independence → [FIRE Calculator](/tools/fire-calculator/)

---

## Related Articles

- [How to Start Investing With $100](/posts/how-to-start-investing-with-100/)
- [How to Build an Emergency Fund Fast](/posts/how-to-build-an-emergency-fund-fast/)
- [How to Pay Off Debt Fast](/posts/how-to-pay-off-debt-fast/)
- [Best Budgeting Apps 2026](/posts/best-budgeting-apps-2026/)
- [Best High-Yield Savings Accounts 2026](/posts/best-high-yield-savings-accounts-2026/)

---

## Productivity Works Free Tools

All our financial calculators are **100% free**, run entirely in your browser, and never store your data.

[Browse all free tools](/tools/)

*This article contains affiliate links. We may earn a commission at no extra cost to you.*
