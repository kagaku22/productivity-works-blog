---
title: "配当収入計算ツール | 年間・月間の配当収入を試算"
date: 2026-05-16
draft: false
slug: "dividend-income-calculator"
description: "株式・ETFからの配当収入を計算。年間・月間収入の試算、配当再投資（DRIP）の複利効果、人気高配当ETFの比較が無料でできるインタラクティブ計算ツール。"
author: "Productivity Works Editorial"
categories:
  - "無料ツール"
tags:
  - "配当"
  - "計算ツール"
  - "不労所得"
  - "投資"
  - "DRIP"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/dividend-income-calculator.png"
  alt: "配当収入計算ツール | 年間・月間の配当収入を試算"
  relative: false
---

*本記事にはアフィリエイトリンクが含まれています。紹介料が発生する場合がありますが、読者の追加費用はありません。*

# 配当収入計算ツール

投資金額と配当利回りを入力して、**年間・月間の配当収入**を試算しましょう。**配当再投資（DRIP）**の複利効果も確認できます。

<div id="dc-calc" style="max-width:700px;margin:0 auto;font-family:Inter,sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">投資金額（円）</label>
<input type="range" id="dcAmount" min="100000" max="100000000" step="100000" value="5000000" oninput="calcDC()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>10万円</span><span id="dcAmtVal" style="font-weight:bold;font-size:20px;color:#2563eb;">500万円</span><span>1億円</span></div>
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">配当利回り（%）</label>
<input type="range" id="dcYield" min="0.5" max="10" step="0.1" value="3.0" oninput="calcDC()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>0.5%</span><span id="dcYldVal" style="font-weight:bold;font-size:20px;color:#10b981;">3.0%</span><span>10%</span></div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:16px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">配当再投資（DRIP）</label>
<select id="dcDRIP" onchange="calcDC()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="yes">あり（複利で増やす）</option>
<option value="no">なし（現金で受け取る）</option>
</select>
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">配当課税率</label>
<select id="dcTax" onchange="calcDC()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="0">0%（非課税口座・NISA等）</option>
<option value="20" selected>20.315%（国内源泉徴収）</option>
<option value="15">15%（外国税額控除適用後）</option>
<option value="30">30%（総合課税・高所得者）</option>
</select>
</div>
</div>

<div style="margin-top:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">投資期間（年）</label>
<input type="range" id="dcYears" min="1" max="30" step="1" value="10" oninput="calcDC()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>1年</span><span id="dcYrsVal" style="font-weight:bold;font-size:18px;color:#f59e0b;">10年</span><span>30年</span></div>
</div>

<div id="dcResult" style="margin-top:24px;"></div>

</div>

<div id="dcTimeline" style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;"></div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">人気の高配当ETF（参考）</h3>
<div id="dcETF"></div>
</div>

</div>

<script>
function fmtJP(n){
  if(n>=100000000) return (n/100000000).toFixed(2)+'億円';
  if(n>=10000) return Math.round(n/10000).toLocaleString('ja-JP')+'万円';
  return Math.round(n).toLocaleString('ja-JP')+'円';
}
function fmtD(n){return Math.round(n).toLocaleString('ja-JP');}

function calcDC(){
  var amount=+document.getElementById('dcAmount').value;
  var yieldRate=+document.getElementById('dcYield').value;
  var drip=document.getElementById('dcDRIP').value;
  var taxPct=+document.getElementById('dcTax').value;
  var years=+document.getElementById('dcYears').value;

  document.getElementById('dcAmtVal').textContent=fmtJP(amount);
  document.getElementById('dcYldVal').textContent=yieldRate.toFixed(1)+'%';
  document.getElementById('dcYrsVal').textContent=years+'年';

  var rate=yieldRate/100;
  var taxRate=taxPct/100;

  var annualDiv=amount*rate;
  var annualNet=annualDiv*(1-taxRate);
  var monthlyNet=annualNet/12;

  // Result summary
  var html='<div style="text-align:center;padding:20px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">年間配当収入（税引後）</div>';
  html+='<div style="font-size:40px;font-weight:bold;color:#10b981;">'+fmtJP(annualNet)+'</div>';
  html+='<div style="font-size:14px;color:#64748b;margin-top:4px;">月額: <strong style="color:#2563eb;">'+fmtJP(monthlyNet)+'</strong></div>';
  html+='</div>';

  html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-top:16px;text-align:center;">';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">配当総額（税前）</div><div style="font-size:18px;font-weight:bold;color:#1e293b;">'+fmtJP(annualDiv)+'<span style="font-size:11px;">/年</span></div></div>';
  var taxAmt=annualDiv*taxRate;
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">源泉徴収税額</div><div style="font-size:18px;font-weight:bold;color:'+(taxRate>0?'#ef4444':'#10b981')+';">'+fmtJP(taxAmt)+'<span style="font-size:11px;">/年</span></div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">実質利回り</div><div style="font-size:18px;font-weight:bold;color:#f59e0b;">'+(yieldRate*(1-taxRate)).toFixed(2)+'<span style="font-size:11px;">%</span></div></div>';
  html+='</div>';

  document.getElementById('dcResult').innerHTML=html;

  // Timeline
  var thtml='<h3 style="margin:0 0 12px;color:#166534;font-size:16px;">'+years+'年間の配当収入推移</h3>';
  thtml+='<table style="width:100%;border-collapse:collapse;font-size:13px;">';
  thtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:6px;">年</th><th style="text-align:right;padding:6px;">ポートフォリオ</th><th style="text-align:right;padding:6px;">年間配当</th><th style="text-align:right;padding:6px;">累計配当</th></tr>';

  var balance=amount;
  var totalDiv=0;
  var showYears=[];
  if(years<=10){for(var i=1;i<=years;i++) showYears.push(i);}
  else{showYears=[1,2,3,5];for(var i=10;i<=years;i+=5) showYears.push(i);if(showYears[showYears.length-1]!==years) showYears.push(years);}

  var yearData=[];
  for(var y=1;y<=years;y++){
    var div=balance*rate;
    var divNet=div*(1-taxRate);
    totalDiv+=divNet;
    if(drip==='yes') balance+=divNet;
    yearData.push({year:y,balance:balance,div:divNet,total:totalDiv});
  }

  for(var i=0;i<showYears.length;i++){
    var d=yearData[showYears[i]-1];
    var bg=i%2===0?'#fff':'#f0fdf4';
    var bold=showYears[i]===years?'font-weight:bold;':'';
    thtml+='<tr style="background:'+bg+';'+bold+'">';
    thtml+='<td style="padding:6px;">'+d.year+'年目</td>';
    thtml+='<td style="padding:6px;text-align:right;">'+fmtJP(d.balance)+'</td>';
    thtml+='<td style="padding:6px;text-align:right;">'+fmtJP(d.div)+'</td>';
    thtml+='<td style="padding:6px;text-align:right;color:#10b981;">'+fmtJP(d.total)+'</td>';
    thtml+='</tr>';
  }
  thtml+='</table>';

  var finalData=yearData[years-1];
  thtml+='<div style="margin-top:12px;padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;text-align:center;">';
  thtml+='<span style="font-size:13px;color:#64748b;">'+years+'年後のポートフォリオ: </span>';
  thtml+='<span style="font-size:20px;font-weight:bold;color:#166534;">'+fmtJP(drip==='yes'?finalData.balance:amount)+'</span>';
  if(drip==='no'){
    thtml+='<span style="font-size:13px;color:#64748b;"> + 累計配当: </span>';
    thtml+='<span style="font-size:20px;font-weight:bold;color:#10b981;">'+fmtJP(finalData.total)+'</span>';
  }
  thtml+='</div>';

  if(drip==='yes'){
    var noReinvest=amount*rate*(1-taxRate)*years;
    var diff=finalData.total-noReinvest;
    thtml+='<div style="margin-top:8px;font-size:12px;color:#166534;text-align:center;">DRIP複利ボーナス: <strong>+'+fmtJP(diff)+'</strong>（現金受取との比較）</div>';
  }

  document.getElementById('dcTimeline').innerHTML=thtml;

  // ETF comparison (Japan-focused)
  var etfs=[
    {name:'VYM',desc:'バンガード高配当利回りETF',yield:2.8,expense:0.06},
    {name:'HDV',desc:'iShares コア高配当ETF',yield:3.5,expense:0.08},
    {name:'SPYD',desc:'SPDR S&P500高配当ETF',yield:4.5,expense:0.07},
    {name:'SCHD',desc:'シュワブ米国配当株式ETF',yield:3.4,expense:0.06},
    {name:'VIG',desc:'バンガード増配株式ETF',yield:1.8,expense:0.06},
    {name:'JEPI',desc:'JPモルガン・プレミアム・インカムETF',yield:7.5,expense:0.35}
  ];

  var ehtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;">';
  for(var i=0;i<etfs.length;i++){
    var annDivE=amount*etfs[i].yield/100*(1-taxRate);
    ehtml+='<div style="padding:10px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
    ehtml+='<div style="display:flex;justify-content:space-between;align-items:center;">';
    ehtml+='<span style="font-weight:bold;font-size:14px;color:#1e293b;">'+etfs[i].name+'</span>';
    ehtml+='<span style="font-size:14px;font-weight:bold;color:#10b981;">'+etfs[i].yield+'%</span>';
    ehtml+='</div>';
    ehtml+='<div style="font-size:11px;color:#64748b;">'+etfs[i].desc+'（経費率: '+etfs[i].expense+'%）</div>';
    ehtml+='<div style="font-size:12px;margin-top:4px;color:#2563eb;">年間収入: <strong>'+fmtJP(annDivE)+'</strong>（税引後）</div>';
    ehtml+='</div>';
  }
  ehtml+='</div>';
  ehtml+='<div style="margin-top:8px;font-size:11px;color:#92400e;text-align:center;">利回りは2026年5月時点の概算値。実際の配当は変動します。過去の実績は将来の成果を保証しません。</div>';
  document.getElementById('dcETF').innerHTML=ehtml;
}

document.addEventListener('DOMContentLoaded',function(){calcDC();});
calcDC();
</script>

---

## 配当投資の仕組み

### 配当とは？

配当とは、企業が利益の一部を株主に現金で還元するものです。配当株・配当ETFを保有することで、株を持っているだけで定期的（通常は年2〜4回）に収入を得られます。

### 配当利回りの計算式

```
配当利回り（%）= 1株あたり年間配当金 ÷ 株価 × 100
```

株価1,000円の株が年間35円の配当を出す場合、配当利回りは3.5%です。

### DRIP（配当再投資）の威力

配当を再投資して株数を増やすことで**複利効果**が生まれます。配当がさらに配当を生む仕組みです。長期間継続すると、現金受取に比べて総リターンが大幅に向上します。

### 税金の考慮

- **国内株の配当**：通常20.315%が源泉徴収（申告分離課税）
- **NISA口座**：配当・売却益が非課税（積立NISAは年間120万円まで）
- **外国株の配当**：現地課税＋国内課税の二重課税（外国税額控除で一部還付可能）

---

> 投資ポートフォリオ全体の成長を確認したい方は → [複利計算ツール](/ja/tools/compound-interest-calculator/)

> 配当を活用した早期退職計画は → [FIREシミュレーター](/ja/tools/fire-calculator/)

---

**関連ツール**
- [予算プランナー](/ja/tools/budget-planner/)
- [緊急資金計算ツール](/ja/tools/emergency-fund-calculator/)
- [FIREシミュレーター](/ja/tools/fire-calculator/)

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)
