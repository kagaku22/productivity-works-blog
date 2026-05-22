---
title: "所得税計算機 2026 | 日本の税率・税額シミュレーター（無料）"
date: 2025-10-03
draft: false
slug: "tax-bracket-calculator"
description: "2026年版・日本の所得税計算機。課税所得と申告区分を入力して、税率・実効税率・税額を即座に表示。各税率段階ごとの内訳グラフつき。"
categories: ["無料ツール"]
tags: ["税金計算機", "所得税", "税率", "確定申告", "計算機"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/tax-bracket-calculator.png"
  alt: "所得税計算機 2026"
  relative: false
---

*本ページにはアフィリエイトリンクが含まれます。*

# 所得税計算機 2026

課税所得と申告区分を入力して、**税率・実効税率・税額**をビジュアルで確認しましょう。

<div id="tb-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b !important;color-scheme:light;">

<div style="padding:24px;border:2px solid #dc2626;border-radius:12px;background:#fef2f2;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">年間課税所得（円）</label>
<input type="number" id="tbIncome" min="0" max="500000000" step="100000" value="5000000" oninput="calcTB()" style="width:100%;padding:12px;border:1px solid #cbd5e1;border-radius:8px;font-size:18px;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">申告区分</label>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-single">
<input type="radio" name="tbStatus" value="single" checked onchange="calcTB()" style="margin-right:8px;"> 単身（一般）
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-mfj">
<input type="radio" name="tbStatus" value="mfj" onchange="calcTB()" style="margin-right:8px;"> 配偶者控除あり
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-mfs">
<input type="radio" name="tbStatus" value="mfs" onchange="calcTB()" style="margin-right:8px;"> 老人扶養控除あり
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-hoh">
<input type="radio" name="tbStatus" value="hoh" onchange="calcTB()" style="margin-right:8px;"> ひとり親控除あり
</label>
</div>
</div>

<div style="margin-bottom:8px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">基礎控除</label>
<div style="display:flex;gap:12px;align-items:center;">
<label style="display:flex;align-items:center;cursor:pointer;">
<input type="checkbox" id="tbDeduction" checked onchange="calcTB()" style="margin-right:6px;width:18px;height:18px;"> 基礎控除を適用する
</label>
<span id="tbDeductionAmt" style="color:#64748b;font-size:14px;">（48万円）</span>
</div>
</div>

</div>

<!-- 結果 -->
<div id="tbResults" style="margin-top:24px;">

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;text-align:center;">
<div style="padding:20px;background:#fef2f2;border-radius:12px;border:1px solid #fecaca;">
<div style="font-size:12px;color:#64748b;">最高限界税率</div>
<div id="tbBracket" style="font-size:36px;font-weight:bold;color:#dc2626;">23%</div>
</div>
<div style="padding:20px;background:#f0fdf4;border-radius:12px;border:1px solid #bbf7d0;">
<div style="font-size:12px;color:#64748b;">実効税率</div>
<div id="tbEffective" style="font-size:36px;font-weight:bold;color:#16a34a;">0.0%</div>
</div>
<div style="padding:20px;background:#f8fafc;border-radius:12px;border:1px solid #e2e8f0;">
<div style="font-size:12px;color:#64748b;">所得税額合計</div>
<div id="tbTotal" style="font-size:28px;font-weight:bold;color:#1e293b !important;color-scheme:light;">¥0</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:12px;text-align:center;">
<div style="padding:16px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:12px;color:#64748b;">税引後所得</div>
<div id="tbAfterTax" style="font-size:22px;font-weight:bold;color:#1e293b !important;color-scheme:light;">¥0</div>
</div>
<div style="padding:16px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:12px;color:#64748b;">月換算手取り（所得税のみ）</div>
<div id="tbMonthly" style="font-size:22px;font-weight:bold;color:#1e293b !important;color-scheme:light;">¥0</div>
</div>
</div>

<!-- 税率段階バー -->
<div style="margin-top:24px;padding:20px;background:#f8fafc;border-radius:12px;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 12px 0;font-size:16px;">各税率段階での課税内訳</h3>
<div id="tbBar" style="height:32px;border-radius:8px;overflow:hidden;display:flex;margin-bottom:8px;"></div>
<div id="tbLegend" style="display:flex;flex-wrap:wrap;gap:8px;font-size:12px;"></div>
</div>

<!-- 税率テーブル -->
<div style="margin-top:20px;padding:20px;background:white;border-radius:12px;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 12px 0;font-size:16px;">2026年度 所得税の速算表</h3>
<div style="overflow-x:auto;">
<table id="tbTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#dc2626;color:white;">
<th style="padding:8px;text-align:left;">税率</th>
<th style="padding:8px;text-align:right;">課税所得の範囲</th>
<th style="padding:8px;text-align:right;">この段階の税額</th>
<th style="padding:8px;text-align:right;">累計税額</th>
</tr>
</thead>
<tbody id="tbTableBody"></tbody>
</table>
</div>
</div>

<!-- シナリオ比較 -->
<div style="margin-top:20px;padding:20px;background:#fffbeb;border-radius:12px;border:1px solid #fde68a;">
<h3 style="margin:0 0 12px 0;font-size:16px;">収入が増えたら？</h3>
<div id="tbScenarios" style="display:grid;gap:8px;"></div>
</div>

</div>

</div>

<script>
// 日本の所得税速算表（2026年度）
const BRACKETS={
  single:[
[0,1950000,0.05,0],
[1950000,3300000,0.10,97500],
[3300000,6950000,0.20,427500],
[6950000,9000000,0.23,636000],
[9000000,18000000,0.33,1536000],
[18000000,40000000,0.40,2796000],
[40000000,Infinity,0.45,4796000]
  ],
  mfj:[
[0,1950000,0.05,0],
[1950000,3300000,0.10,97500],
[3300000,6950000,0.20,427500],
[6950000,9000000,0.23,636000],
[9000000,18000000,0.33,1536000],
[18000000,40000000,0.40,2796000],
[40000000,Infinity,0.45,4796000]
  ],
  mfs:[
[0,1950000,0.05,0],
[1950000,3300000,0.10,97500],
[3300000,6950000,0.20,427500],
[6950000,9000000,0.23,636000],
[9000000,18000000,0.33,1536000],
[18000000,40000000,0.40,2796000],
[40000000,Infinity,0.45,4796000]
  ],
  hoh:[
[0,1950000,0.05,0],
[1950000,3300000,0.10,97500],
[3300000,6950000,0.20,427500],
[6950000,9000000,0.23,636000],
[9000000,18000000,0.33,1536000],
[18000000,40000000,0.40,2796000],
[40000000,Infinity,0.45,4796000]
  ]
};
// 各区分の追加控除（基礎控除48万は別途）
const EXTRA_DED={single:0,mfj:380000,mfs:480000,hoh:350000};
const BASE_DED=480000;
const COLORS=['#dbeafe','#bfdbfe','#93c5fd','#60a5fa','#3b82f6','#2563eb','#1d4ed8'];

function getStatus(){
  return document.querySelector('input[name="tbStatus"]:checked').value;
}

function computeTax(income,status){
  const brackets=BRACKETS[status];
  let tax=0;const details=[];
  for(const[lo,hi,rate,ded]of brackets){
if(income<=lo)break;
const taxable=Math.min(income,hi)-lo;
const t=taxable*rate;
tax+=t;
details.push({lo,hi:Math.min(income,hi),rate,taxable,tax:t,cumTax:tax});
  }
  // 復興特別所得税 2.1%
  const finalTax=tax*1.021;
  return{tax:finalTax,details};
}

function calcTB(){
  const grossIncome=parseFloat(document.getElementById('tbIncome').value)||0;
  const status=getStatus();
  const useDeduction=document.getElementById('tbDeduction').checked;
  const deduction=useDeduction?(BASE_DED+EXTRA_DED[status]):0;
  const taxableIncome=Math.max(0,grossIncome-deduction);

  document.getElementById('tbDeductionAmt').textContent='\uff08'+deduction.toLocaleString('ja-JP')+'\u5186\uff09';

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
  document.getElementById('tbTotal').textContent='\u00a5'+Math.round(tax).toLocaleString('ja-JP');
  document.getElementById('tbAfterTax').textContent='\u00a5'+Math.round(afterTax).toLocaleString('ja-JP');
  document.getElementById('tbMonthly').textContent='\u00a5'+Math.round(afterTax/12).toLocaleString('ja-JP');

  let barHTML='';let legendHTML='';
  if(taxableIncome>0){
details.forEach((d,i)=>{
const pct=(d.taxable/taxableIncome)*100;
if(pct>0){
barHTML+='<div style="width:'+pct+'%;background:'+COLORS[i%COLORS.length]+';height:100%;" title="'+Math.round(d.rate*100)+'%: \u00a5'+d.taxable.toLocaleString('ja-JP')+'"></div>';
legendHTML+='<span><span style="display:inline-block;width:10px;height:10px;background:'+COLORS[i%COLORS.length]+';border-radius:2px;"></span> '+Math.round(d.rate*100)+'%</span>';
}
});
  }
  document.getElementById('tbBar').innerHTML=barHTML;
  document.getElementById('tbLegend').innerHTML=legendHTML;

  const allBrackets=BRACKETS[status];
  let tbody='';let cumTax=0;
  allBrackets.forEach((b,i)=>{
const[lo,hi,rate,ded]=b;
const taxable=taxableIncome>lo?Math.min(taxableIncome,hi)-lo:0;
const t=taxable*rate*1.021;
cumTax+=t;
const active=taxableIncome>lo;
const current=taxableIncome>lo&&(hi===Infinity||taxableIncome<=hi);
const bg=current?'#fef2f2':i%2===0?'#f8fafc':'white';
const hiStr=hi===Infinity?'\u8d85':''+hi.toLocaleString('ja-JP')+'\u5186';
const arrow=current?' \u2190':'';
tbody+='<tr style="background:'+bg+';'+(current?'font-weight:bold;':'')+'">';
tbody+='<td style="padding:8px;">'+Math.round(rate*100)+'%'+arrow+'</td>';
tbody+='<td style="padding:8px;text-align:right;">\u00a5'+lo.toLocaleString('ja-JP')+' \uff5e '+hiStr+'</td>';
tbody+='<td style="padding:8px;text-align:right;'+(active?'':'color:#94a3b8;')+'">\u00a5'+Math.round(t).toLocaleString('ja-JP')+'</td>';
tbody+='<td style="padding:8px;text-align:right;'+(active?'':'color:#94a3b8;')+'">\u00a5'+Math.round(cumTax).toLocaleString('ja-JP')+'</td>';
tbody+='</tr>';
  });
  document.getElementById('tbTableBody').innerHTML=tbody;

  const changes=[500000,1000000,2000000];
  let sHTML='';
  changes.forEach(c=>{
const newGross=grossIncome+c;
const newTaxable=Math.max(0,newGross-deduction);
const r=computeTax(newTaxable,status);
const diff=r.tax-tax;
const newEff=newGross>0?(r.tax/newGross)*100:0;
sHTML+='<div style="display:flex;justify-content:space-between;align-items:center;padding:12px;background:white;border-radius:8px;border:1px solid #e2e8f0;">';
sHTML+='<div><strong>\u00a5'+newGross.toLocaleString('ja-JP')+'</strong> <span style="color:#64748b;font-size:13px;">(+\u00a5'+c.toLocaleString('ja-JP')+')</span></div>';
sHTML+='<div style="text-align:right;font-size:14px;">\u7a0e\u984d: \u00a5'+Math.round(r.tax).toLocaleString('ja-JP')+' <span style="color:#dc2626;">(+\u00a5'+Math.round(diff).toLocaleString('ja-JP')+')</span> | \u5b9f\u52b9: '+newEff.toFixed(1)+'%</div>';
sHTML+='</div>';
  });
  document.getElementById('tbScenarios').innerHTML=sHTML;
}

calcTB();
</script>

---

## 日本の所得税の仕組み

日本は**超過累進課税制度**を採用しています。所得を段階ごとに分割し、それぞれの部分に異なる税率を適用します。高い税率が適用されるのは**その段階を超えた部分だけ**です。

**よくある誤解：** 「収入が増えて上の税率に入ったら、全部の所得に高い税率がかかる」— これは**誤り**です。超えた部分だけが高い税率で課税されます。

---

## 2026年度 所得税速算表

| 税率 | 課税所得の範囲 | 控除額 |
|------|--------------|--------|
| 5% | 195万円以下 | — |
| 10% | 195万円超〜330万円以下 | 9.75万円 |
| 20% | 330万円超〜695万円以下 | 42.75万円 |
| 23% | 695万円超〜900万円以下 | 63.6万円 |
| 33% | 900万円超〜1,800万円以下 | 153.6万円 |
| 40% | 1,800万円超〜4,000万円以下 | 279.6万円 |
| 45% | 4,000万円超 | 479.6万円 |

※復興特別所得税（2.1%加算）を含めて計算しています。基礎控除48万円は別途適用。

---

## 税負担を減らす方法

### 1. iDeCo・企業型DCで節税

iDeCoの掛金は全額所得控除。年間最大81.6万円（自営業者）の拠出が可能で、高い税率段階の方ほど節税効果が大きくなります。

### 2. 基礎控除・各種控除を活用

配偶者控除・扶養控除・医療費控除・生命保険料控除など、忘れずに申告しましょう。

### 3. NISAで運用益を非課税に

NISA口座内の利益・配当は非課税。税率20%分を丸ごと節税できます。

### 4. 損益通算・繰越控除

株式・投資信託の売却損は他の譲渡益と通算でき、最大3年間繰り越すことができます。

---

## 関連ツール

> 副業にかかる税金を計算 → [副業税金計算機](/tools/side-hustle-tax-calculator/)
> 老後資産をシミュレーション → [老後資産計算機](/tools/retirement-calculator/)
> 毎月の予算を最適化 → [予算プランナー](/tools/budget-planner/)

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)
