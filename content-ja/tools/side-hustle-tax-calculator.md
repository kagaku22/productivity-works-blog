---
title: "副業税金計算機 | 所得税・住民税の簡単シミュレーター（無料）"
date: 2025-11-24
draft: false
slug: "side-hustle-tax-calculator"
description: "副業収入にかかる税金を簡単計算。給与収入と副業収入を入力するだけで、所得税・住民税の概算と手取り額を瞬時に表示。無料インタラクティブ計算機。"
author: "Productivity Works Editorial"
categories:
  - "無料ツール"
tags:
  - "副業"
  - "税金計算機"
  - "所得税"
  - "フリーランス"
  - "確定申告"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/side-hustle-tax-calculator.png"
  alt: "副業税金計算機 | 所得税・住民税シミュレーター"
  relative: false
---

*本ページにはアフィリエイトリンクが含まれます。*

# 副業税金計算機

給与収入と副業収入を入力して、**税負担の合計**・**副業の手取り額**を概算します。

<div id="sh-calc" style="max-width:680px;margin:0 auto;font-family:Inter,sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
<div>
<h3 style="margin:0 0 12px;color:#64748b;font-size:14px;text-align:center;">給与収入</h3>
<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">年間給与（円）</label>
<input type="range" id="w2Salary" min="0" max="20000000" step="100000" value="5000000" oninput="calcSH()" style="width:100%;">
<div style="text-align:center;font-weight:bold;font-size:20px;color:#64748b;" id="w2Val">500万円</div>
</div>
</div>
<div>
<h3 style="margin:0 0 12px;color:#2563eb;font-size:14px;text-align:center;">副業収入</h3>
<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">副業の総収入（円）</label>
<input type="range" id="shRevenue" min="0" max="5000000" step="50000" value="500000" oninput="calcSH()" style="width:100%;">
<div style="text-align:center;font-weight:bold;font-size:20px;color:#2563eb;" id="shRevVal">50万円</div>
</div>
</div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">事業経費（円）</label>
<input type="range" id="shExpenses" min="0" max="2000000" step="10000" value="100000" oninput="calcSH()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0円</span><span id="shExpVal" style="font-weight:bold;font-size:16px;color:#ef4444;">10万円</span><span>200万円</span></div>
</div>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:4px;font-size:13px;">申告区分</label>
<select id="shFiling" onchange="calcSH()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b;background:#fff;">
<option value="single">単身（一般）</option>
<option value="married">配偶者控除あり</option>
<option value="hoh">ひとり親控除あり</option>
</select>
</div>

<div id="shResult" style="margin-top:20px;"></div>

</div>

<div id="shBreakdown" style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;"></div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">予定納税・確定申告の目安</h3>
<div id="shQuarterly"></div>
</div>

</div>

<script>
function fmtJP(n){return Math.round(n).toLocaleString('ja-JP');}

function calcJPIncomeTax(taxable){
  // 日本の所得税速算表（2026年度・概算）
  var brackets=[
[1950000,0.05,0],
[3300000,0.10,97500],
[6950000,0.20,427500],
[9000000,0.23,636000],
[18000000,0.33,1536000],
[40000000,0.40,2796000],
[Infinity,0.45,4796000]
  ];
  var tax=0;
  for(var i=0;i<brackets.length;i++){
if(taxable<=brackets[i][0]){
tax=taxable*brackets[i][1]-brackets[i][2];
break;
}
  }
  return Math.max(0,tax);
}

function getSalariedDeduction(salary){
  // 給与所得控除（簡易版）
  if(salary<=1625000) return 550000;
  if(salary<=1800000) return salary*0.4-100000;
  if(salary<=3600000) return salary*0.3+80000;
  if(salary<=6600000) return salary*0.2+440000;
  if(salary<=8500000) return salary*0.1+1100000;
  return 1950000;
}

function getBasicDeduction(){return 480000;}

function calcSH(){
  var w2=+document.getElementById('w2Salary').value;
  var rev=+document.getElementById('shRevenue').value;
  var exp=+document.getElementById('shExpenses').value;
  var filing=document.getElementById('shFiling').value;

  document.getElementById('w2Val').textContent=fmtJP(w2)+'\u5186';
  document.getElementById('shRevVal').textContent=fmtJP(rev)+'\u5186';
  document.getElementById('shExpVal').textContent=fmtJP(exp)+'\u5186';

  var netProfit=Math.max(0,rev-exp);

  // 給与所得
  var salaryIncome=Math.max(0,w2-getSalariedDeduction(w2));
  // 事業所得（副業）
  var businessIncome=netProfit;

  // 基礎控除
  var basicDed=getBasicDeduction();
  // 配偶者控除（簡易）
  var spouseDed=filing==='married'?380000:0;
  // ひとり親控除
  var hohDed=filing==='hoh'?350000:0;

  // 副業なしの課税所得
  var taxableNoSH=Math.max(0,salaryIncome-basicDed-spouseDed-hohDed);
  var taxNoSH=calcJPIncomeTax(taxableNoSH);
  // 復興特別所得税2.1%
  var taxNoSHTotal=taxNoSH*1.021;

  // 副業ありの課税所得
  var taxableWithSH=Math.max(0,salaryIncome+businessIncome-basicDed-spouseDed-hohDed);
  var taxWithSH=calcJPIncomeTax(taxableWithSH);
  var taxWithSHTotal=taxWithSH*1.021;

  // 副業分の追加所得税
  var additionalIncomeTax=taxWithSHTotal-taxNoSHTotal;

  // 住民税（概算10%）
  var juminzeiBase=Math.max(0,salaryIncome+businessIncome-basicDed-spouseDed-hohDed);
  var juminzeiBaseNoSH=Math.max(0,salaryIncome-basicDed-spouseDed-hohDed);
  var additionalJuminzei=(juminzeiBase-juminzeiBaseNoSH)*0.10;

  var totalSHTax=additionalIncomeTax+additionalJuminzei;
  var effectiveRate=netProfit>0?(totalSHTax/netProfit*100):0;
  var takeHome=netProfit-totalSHTax;

  var color=takeHome>=0?'#10b981':'#ef4444';
  var html='<div style="text-align:center;padding:16px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">\u526f\u696d\u306e\u624b\u53d6\u308a\u984d</div>';
  html+='<div style="font-size:36px;font-weight:bold;color:'+color+';">\u00a5'+fmtJP(takeHome)+'</div>';
  html+='<div style="font-size:14px;color:#64748b;margin-top:4px;">\u4e8b\u696d\u6240\u5f97\uff08\u7d14\u5229\u76ca\uff09\u00a5'+fmtJP(netProfit)+'\u306e\u3046\u3061</div>';
  html+='<div style="font-size:13px;color:#64748b;margin-top:8px;">\u526f\u696d\u6240\u5f97\u306b\u304b\u304b\u308b\u5b9f\u8cea\u7a0e\u7387: <strong style="color:#ef4444;">'+effectiveRate.toFixed(1)+'%</strong></div>';
  html+='</div>';
  document.getElementById('shResult').innerHTML=html;

  var bhtml='<h3 style="margin:0 0 12px;color:#166534;font-size:16px;">\u7a0e\u91d1\u5185\u8a33</h3>';
  bhtml+='<table style="width:100%;border-collapse:collapse;font-size:14px;">';
  bhtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:8px;">\u9805\u76ee</th><th style="text-align:right;padding:8px;">\u91d1\u984d</th></tr>';

  var rows=[
['\u526f\u696d\u306e\u7dcf\u53ce\u5165','\u00a5'+fmtJP(rev)],
['\u4e8b\u696d\u7d4c\u8cbb','-\u00a5'+fmtJP(exp)],
['\u4e8b\u696d\u6240\u5f97\uff08\u7d14\u5229\u76ca\uff09','\u00a5'+fmtJP(netProfit)],
['',''],
['\u8ffd\u52a0\u6240\u5f97\u7a0e\uff08\u5fa9\u8208\u7279\u5225\u6240\u5f97\u7a0e\u542b\uff09','\u00a5'+fmtJP(Math.round(additionalIncomeTax))],
['\u8ffd\u52a0\u4f4f\u6c11\u7a0e\uff08\u6982\u7b97\uff09','\u00a5'+fmtJP(Math.round(additionalJuminzei))],
['',''],
['\u526f\u696d\u5206\u306e\u7a0e\u8ca0\u62c5\u5408\u8a08','\u00a5'+fmtJP(Math.round(totalSHTax))],
['\u526f\u696d\u306e\u624b\u53d6\u308a\u984d','\u00a5'+fmtJP(Math.round(takeHome))]
  ];

  for(var i=0;i<rows.length;i++){
if(rows[i][0]===''){bhtml+='<tr><td colspan="2" style="padding:4px;"></td></tr>';continue;}
var bg=i%2===0?'#fff':'#f0fdf4';
var bold=(i===rows.length-1||i===rows.length-2)?'font-weight:bold;':'';
bhtml+='<tr style="background:'+bg+';'+bold+'">';
bhtml+='<td style="padding:8px;">'+rows[i][0]+'</td>';
bhtml+='<td style="padding:8px;text-align:right;">'+rows[i][1]+'</td>';
bhtml+='</tr>';
  }
  bhtml+='</table>';
  document.getElementById('shBreakdown').innerHTML=bhtml;

  // 確定申告・予定納税目安
  var quarterly=Math.round(totalSHTax/4);
  var qhtml='<div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:8px;text-align:center;">';
  var periods=['\u7b2c1\u671f\uff087\u6708\uff09','\u7b2c2\u671f\uff0811\u6708\uff09','\u78ba\u5b9a\u7533\u544a\uff083\u6708\uff09','\u4f59\u5104\uff083\u6708\uff09'];
  for(var i=0;i<4;i++){
qhtml+='<div style="padding:12px;background:#fff;border-radius:8px;">';
qhtml+='<div style="font-size:11px;color:#64748b;">'+periods[i]+'</div>';
qhtml+='<div style="font-size:18px;font-weight:bold;color:#92400e;">\u00a5'+fmtJP(quarterly)+'</div>';
qhtml+='</div>';
  }
  qhtml+='</div>';
  qhtml+='<div style="margin-top:12px;font-size:12px;color:#92400e;text-align:center;">\u526f\u696d\u6240\u5f97\u304c20\u4e07\u5186\u8d85\u306e\u5834\u5408\u306f\u78ba\u5b9a\u7533\u544a\u304c\u5fc5\u8981\u3067\u3059\u3002\u4e88\u5b9a\u7d0d\u7a0e\u306f\u524d\u5e74\u5ea6\u7a0e\u984d\u304c15\u4e07\u5186\u4ee5\u4e0a\u306e\u5834\u5408\u306b\u767a\u751f\u3057\u307e\u3059\u3002</div>';
  document.getElementById('shQuarterly').innerHTML=qhtml;
}

document.addEventListener('DOMContentLoaded',function(){calcSH();});
calcSH();
</script>

---

## 副業収入の課税の仕組み

フリーランス・ギグワーク・ネット販売・コンサルティングなどで得た収入は**事業所得または雑所得**として扱われます。課税される税金は主に2種類です。

### 1. 所得税（累進課税）

副業の純利益は給与所得と合算され、**所得税の速算表**に基づいて課税されます。税率は5%〜45%（復興特別所得税2.1%加算）。

### 2. 住民税（一律10%程度）

所得税とは別に、翌年6月から住民税（都道府県民税＋市区町村民税 合計約10%）が追加でかかります。

### 税負担を減らす方法

1. **経費を正確に記録する** — 自宅の一部（家事按分）・通信費・書籍代・機材費など
2. **青色申告を活用する** — 複式帳簿で最大65万円の青色申告特別控除
3. **iDeCo・小規模企業共済** — 自営業者向けの節税積み立て制度を活用
4. **会計ソフトを使う** — 自動仕訳と確定申告書の作成を効率化

### 確定申告が必要なケース

給与収入以外の所得が**年間20万円を超える**場合、翌年2月16日〜3月15日に確定申告が必要です。

---

> 副業の帳簿管理を自動化したい方へ → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

---

**関連ツール**
- [純資産計算機](/tools/net-worth-calculator/)
- [老後資産計算機](/tools/retirement-calculator/)
- [債務返済計算機](/tools/debt-payoff-calculator/)
- [複利計算機](/tools/compound-interest-calculator/)
