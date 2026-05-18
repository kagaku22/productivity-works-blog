---
title: "配当金シミュレーター｜投資額・利回りから年間配当収入を自動計算【2026年版】"
date: 2025-11-15
draft: false
slug: "haitoukin-simulator"
description: "投資額と配当利回りを入力して年間・月間の配当収入を自動計算。NISA非課税効果、配当再投資の複利シミュレーション、高配当ETF比較も。無料の配当金計算ツール。"
author: "Productivity Works編集部"
categories:
  - "投資・資産運用"
tags:
  - "配当金"
  - "シミュレーション"
  - "高配当"
  - "NISA"
  - "計算ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/haitoukin-simulator.png"
  alt: "配当金シミュレーター｜投資額・利回りから年間配当収入を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 配当金シミュレーター【2026年版】

投資額と配当利回りを入力して、**年間・月間の配当収入**と**NISA非課税効果**を自動計算します。配当再投資による複利効果も確認できます。

<div id="div-calc" style="max-width:700px;margin:0 auto;font-family:'Noto Sans JP',sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">投資額（万円）</label>
<input type="range" id="divAmount" min="10" max="5000" step="10" value="500" oninput="calcDiv()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>10万</span><span id="divAmtVal" style="font-weight:bold;font-size:20px;color:#2563eb;">500万円</span><span>5,000万</span></div>
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">配当利回り（年率）</label>
<input type="range" id="divYield" min="0.5" max="10" step="0.1" value="3.5" oninput="calcDiv()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>0.5%</span><span id="divYldVal" style="font-weight:bold;font-size:20px;color:#10b981;">3.5%</span><span>10%</span></div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:16px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">口座タイプ</label>
<select id="divAccount" onchange="calcDiv()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b;background:#fff;">
<option value="nisa">新NISA（非課税）</option>
<option value="tokutei">特定口座（課税20.315%）</option>
</select>
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">配当再投資</label>
<select id="divReinvest" onchange="calcDiv()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b;background:#fff;">
<option value="yes">する（複利効果あり）</option>
<option value="no">しない（配当受取）</option>
</select>
</div>
</div>

<div style="margin-top:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">運用期間</label>
<input type="range" id="divYears" min="1" max="30" step="1" value="10" oninput="calcDiv()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;"><span>1年</span><span id="divYrsVal" style="font-weight:bold;font-size:18px;color:#f59e0b;">10年</span><span>30年</span></div>
</div>

<div id="divResult" style="margin-top:24px;"></div>

</div>

<div id="divTimeline" style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;"></div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">人気の高配当ETF・銘柄比較</h3>
<div id="divETF"></div>
</div>

<div style="margin-top:24px;padding:24px;border:2px solid #8b5cf6;border-radius:12px;background:#f5f3ff;">
<h3 style="margin:0 0 12px;color:#6d28d9;font-size:16px;">NISA vs 特定口座：配当手取り比較</h3>
<div id="divNISA"></div>
</div>

</div>

<script>
function fmt(n){return Math.round(n).toLocaleString('ja-JP');}

function calcDiv(){
  var amount=+document.getElementById('divAmount').value;
  var yieldRate=+document.getElementById('divYield').value;
  var account=document.getElementById('divAccount').value;
  var reinvest=document.getElementById('divReinvest').value;
  var years=+document.getElementById('divYears').value;

  document.getElementById('divAmtVal').textContent=fmt(amount)+'万円';
  document.getElementById('divYldVal').textContent=yieldRate.toFixed(1)+'%';
  document.getElementById('divYrsVal').textContent=years+'年';

  var principal=amount*10000;
  var rate=yieldRate/100;
  var taxRate=account==='nisa'?0:0.20315;

  // Annual dividend (year 1)
  var annualDiv=principal*rate;
  var annualAfterTax=annualDiv*(1-taxRate);
  var monthlyAfterTax=annualAfterTax/12;

  // Result summary
  var html='<div style="text-align:center;padding:20px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">年間配当収入（税引後）</div>';
  html+='<div style="font-size:40px;font-weight:bold;color:#10b981;">'+fmt(annualAfterTax)+'<span style="font-size:16px;">円</span></div>';
  html+='<div style="font-size:14px;color:#64748b;margin-top:4px;">月額 約 <strong style="color:#2563eb;">'+fmt(monthlyAfterTax)+'円</strong></div>';
  html+='</div>';

  html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-top:16px;text-align:center;">';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">税引前配当</div><div style="font-size:18px;font-weight:bold;color:#1e293b;">'+fmt(annualDiv)+'<span style="font-size:11px;">円/年</span></div></div>';
  var taxAmount=annualDiv*taxRate;
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">税金</div><div style="font-size:18px;font-weight:bold;color:'+(taxRate>0?'#ef4444':'#10b981')+';">'+fmt(taxAmount)+'<span style="font-size:11px;">円/年</span></div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">配当利回り（税引後）</div><div style="font-size:18px;font-weight:bold;color:#f59e0b;">'+(yieldRate*(1-taxRate)).toFixed(2)+'<span style="font-size:11px;">%</span></div></div>';
  html+='</div>';

  if(account==='nisa'){
    html+='<div style="margin-top:8px;text-align:center;font-size:12px;color:#10b981;font-weight:bold;">NISA口座なら配当金が非課税！年間 '+fmt(annualDiv*0.20315)+' 円の節税効果</div>';
  }

  document.getElementById('divResult').innerHTML=html;

  // Timeline table
  var thtml='<h3 style="margin:0 0 12px;color:#166534;font-size:16px;">配当収入の推移（'+years+'年間）</h3>';
  thtml+='<table style="width:100%;border-collapse:collapse;font-size:13px;">';
  thtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:6px;">年</th><th style="text-align:right;padding:6px;">投資元本</th><th style="text-align:right;padding:6px;">年間配当</th><th style="text-align:right;padding:6px;">累計配当</th></tr>';

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
    thtml+='<td style="padding:6px;">'+d.year+'年目</td>';
    thtml+='<td style="padding:6px;text-align:right;">'+fmt(d.balance)+'円</td>';
    thtml+='<td style="padding:6px;text-align:right;">'+fmt(d.div)+'円</td>';
    thtml+='<td style="padding:6px;text-align:right;color:#10b981;">'+fmt(d.total)+'円</td>';
    thtml+='</tr>';
  }
  thtml+='</table>';

  var finalData=yearData[years-1];
  var gain=finalData.balance-principal+finalData.total*(reinvest==='yes'?0:1);
  thtml+='<div style="margin-top:12px;padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;text-align:center;">';
  thtml+='<span style="font-size:13px;color:#64748b;">'+years+'年後の資産総額: </span>';
  thtml+='<span style="font-size:20px;font-weight:bold;color:#166534;">'+fmt(reinvest==='yes'?finalData.balance:principal)+'円</span>';
  if(reinvest==='yes'){
    thtml+='<span style="font-size:13px;color:#64748b;"> + 受取配当累計: </span>';
    thtml+='<span style="font-size:13px;font-weight:bold;color:#10b981;">再投資済み</span>';
  } else {
    thtml+='<span style="font-size:13px;color:#64748b;"> + 受取配当累計: </span>';
    thtml+='<span style="font-size:20px;font-weight:bold;color:#10b981;">'+fmt(finalData.total)+'円</span>';
  }
  thtml+='</div>';

  if(reinvest==='yes'){
    var noReinvestTotal=principal*rate*(1-taxRate)*years;
    var diff=finalData.total-noReinvestTotal;
    thtml+='<div style="margin-top:8px;font-size:12px;color:#166534;text-align:center;">配当再投資の複利効果: <strong>+'+fmt(diff)+'円</strong>（再投資なしと比較）</div>';
  }

  document.getElementById('divTimeline').innerHTML=thtml;

  // ETF comparison
  var etfs=[
    {name:'VYM',desc:'バンガード米国高配当',yield:2.8,type:'米国ETF'},
    {name:'HDV',desc:'iシェアーズ高配当',yield:3.5,type:'米国ETF'},
    {name:'SPYD',desc:'S&P500高配当',yield:4.5,type:'米国ETF'},
    {name:'1489',desc:'日経高配当50',yield:3.2,type:'国内ETF'},
    {name:'2914',desc:'日本たばこ産業(JT)',yield:4.8,type:'個別株'},
    {name:'8593',desc:'三菱HCキャピタル',yield:3.8,type:'個別株'}
  ];

  var ehtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;">';
  for(var i=0;i<etfs.length;i++){
    var annDiv=principal*etfs[i].yield/100*(account==='nisa'?1:0.79685);
    ehtml+='<div style="padding:10px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
    ehtml+='<div style="display:flex;justify-content:space-between;align-items:center;">';
    ehtml+='<div><span style="font-weight:bold;font-size:14px;color:#1e293b;">'+etfs[i].name+'</span><span style="font-size:11px;color:#64748b;margin-left:4px;">'+etfs[i].type+'</span></div>';
    ehtml+='<span style="font-size:14px;font-weight:bold;color:#10b981;">'+etfs[i].yield+'%</span>';
    ehtml+='</div>';
    ehtml+='<div style="font-size:11px;color:#64748b;">'+etfs[i].desc+'</div>';
    ehtml+='<div style="font-size:12px;margin-top:4px;color:#2563eb;">年間配当: <strong>'+fmt(annDiv)+'円</strong>（税引後）</div>';
    ehtml+='</div>';
  }
  ehtml+='</div>';
  ehtml+='<div style="margin-top:8px;font-size:11px;color:#92400e;text-align:center;">※配当利回りは2026年5月時点の参考値です。実際の配当は変動します。</div>';
  document.getElementById('divETF').innerHTML=ehtml;

  // NISA vs Tokutei comparison
  var nisaDiv=principal*rate;
  var tokuteiDiv=nisaDiv*0.79685;
  var diff10=nisaDiv*10-tokuteiDiv*10;
  var nhtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;text-align:center;">';
  nhtml+='<div style="padding:16px;background:#fff;border-radius:8px;border:2px solid #10b981;">';
  nhtml+='<div style="font-size:12px;color:#166534;font-weight:bold;">新NISA（非課税）</div>';
  nhtml+='<div style="font-size:24px;font-weight:bold;color:#10b981;">'+fmt(nisaDiv)+'<span style="font-size:12px;">円/年</span></div>';
  nhtml+='<div style="font-size:12px;color:#64748b;">10年累計: '+fmt(nisaDiv*10)+'円</div>';
  nhtml+='</div>';
  nhtml+='<div style="padding:16px;background:#fff;border-radius:8px;border:2px solid #94a3b8;">';
  nhtml+='<div style="font-size:12px;color:#64748b;font-weight:bold;">特定口座（課税）</div>';
  nhtml+='<div style="font-size:24px;font-weight:bold;color:#64748b;">'+fmt(tokuteiDiv)+'<span style="font-size:12px;">円/年</span></div>';
  nhtml+='<div style="font-size:12px;color:#64748b;">10年累計: '+fmt(tokuteiDiv*10)+'円</div>';
  nhtml+='</div>';
  nhtml+='</div>';
  nhtml+='<div style="margin-top:12px;text-align:center;padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  nhtml+='<div style="font-size:13px;color:#64748b;">NISAなら10年間で</div>';
  nhtml+='<div style="font-size:28px;font-weight:bold;color:#10b981;">+'+fmt(diff10)+'<span style="font-size:14px;">円</span></div>';
  nhtml+='<div style="font-size:13px;color:#64748b;">多く受け取れます</div>';
  nhtml+='</div>';
  document.getElementById('divNISA').innerHTML=nhtml;
}

document.addEventListener('DOMContentLoaded',function(){calcDiv();});
calcDiv();
</script>

---

## 配当投資の基礎知識

### 配当金とは

配当金は、企業が稼いだ利益の一部を株主に還元するお金です。株式やETFを保有しているだけで、年に1〜4回配当金を受け取れます。

### 配当利回りの計算方法

```
配当利回り（%） = 年間配当金 ÷ 株価 × 100
```

例：株価1,000円の銘柄が年間40円の配当を出す場合、配当利回りは4.0%です。

### 高配当投資のメリット・デメリット

| メリット | デメリット |
|---|---|
| 定期的なインカム収入 | 株価下落リスクあり |
| 再投資で複利効果 | 減配・無配のリスク |
| NISAなら非課税 | 成長株と比べリターンが劣る場合も |
| 精神的に安定しやすい | 配当利回りだけで判断は危険 |

### 新NISAで配当投資を始める

新NISAの成長投資枠（年間240万円）を使えば、配当金が**非課税**で受け取れます。通常は20.315%の税金がかかるため、利回り3.5%の銘柄なら実質利回りが約0.7%向上します。

---

> 配当投資を始めるなら、NISA口座の開設が第一歩です。<a href="https://hb.afl.rakuten.co.jp/hsc/41ab8a31.8f450617.41ab8a32.86e006c4/?link_type=hybrid_url&ut=eyJwYWdlIjoic2hvcCIsInR5cGUiOiJoeWJyaWRfdXJsIiwiY29sIjoxLCJjYXQiOiIxIiwiYmFuIjoiMTI0NjkzOSIsImFtcCI6ZmFsc2V9" target="_blank" rel="nofollow">楽天証券でNISA口座を開設</a>すれば、国内株・米国ETFの配当金が非課税になります。

> 積立投資と配当投資を組み合わせるなら、[新NISAシミュレーター](/ja/tools/nisa-simulator/)で積立枠の運用も確認してみてください。

---

**関連記事**
- [新NISAシミュレーター](/ja/tools/nisa-simulator/)
- [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/)
- [複利計算シミュレーター](/ja/tools/fukuri-keisan/)
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [新NISA おすすめ銘柄 初心者向け完全ガイド【2026年最新版】](/ja/posts/nisa-osusume-meigara-2026/)
- [SBI証券 楽天証券 比較 2026年版！どちらを選ぶべきか徹底解説](/ja/posts/sbi-rakuten-hikaku-2026/)
- [株の始め方 初心者ガイド！必要な金額と最初の一歩を完全解説【2026年版】](/ja/posts/株-始め方-初心者-必要な金額/)
