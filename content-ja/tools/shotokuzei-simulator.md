---
title: "所得税シミュレーター｜年収から所得税・住民税・手取りを無料計算"
date: 2025-04-28
draft: false
slug: "shotokuzei-simulator"
aliases:
  - /ja/tools/shotokuzei-simulator/
description: "所得税シミュレーター。年収・給与所得を入力して、所得税・住民税・社会保険料・手取り額を無料で計算。2026年最新の税率表で正確にシミュレーションできます。"
categories: ["無料ツール"]
tags: ["所得税", "シミュレーター", "確定申告", "税金計算", "計算ツール"]
author: "Productivity Works編集部"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/shotokuzei-simulator.png"
  alt: "所得税シミュレーター"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 所得税シミュレーター

年収を入力するだけで、**所得税・住民税・社会保険料・手取り額**を一括計算します。累進課税の仕組みも一目で確認できます。

<div id="st-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI','Hiragino Sans',sans-serif;color:#1e293b;">

<div style="padding:24px;border:2px solid #b91c1c;border-radius:12px;background:#fef2f2;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">年収（額面・万円）</label>
<input type="number" id="stIncome" min="0" max="100000" step="10" value="500" oninput="calcST()" style="width:100%;padding:12px;border:1px solid #cbd5e1;border-radius:8px;font-size:18px;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">働き方</label>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<label style="display:flex;align-items:center;padding:12px;border:2px solid #b91c1c;border-radius:8px;cursor:pointer;background:#fef2f2;" id="lbl-employee">
<input type="radio" name="stType" value="employee" checked onchange="calcST()" style="margin-right:8px;"> 会社員
</label>
<label style="display:flex;align-items:center;padding:12px;border:2px solid #e2e8f0;border-radius:8px;cursor:pointer;background:white;" id="lbl-freelance">
<input type="radio" name="stType" value="freelance" onchange="calcST()" style="margin-right:8px;"> フリーランス
</label>
</div>
</div>

<div id="stFreelanceOpts" style="display:none;margin-bottom:20px;padding:16px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="margin-bottom:12px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">経費率（%）</label>
<input type="range" id="stExpenseRate" min="0" max="80" step="5" value="30" oninput="calcST()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span id="stExpenseVal" style="font-weight:bold;color:#b91c1c;">30%</span><span>80%</span></div>
</div>
<div>
<label style="display:flex;align-items:center;cursor:pointer;font-size:14px;">
<input type="checkbox" id="stBlueReturn" checked onchange="calcST()" style="margin-right:6px;width:16px;height:16px;"> 青色申告特別控除（65万円）
</label>
</div>
</div>

<div style="margin-bottom:8px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">扶養家族</label>
<select id="stDependents" onchange="calcST()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b;background:#fff;">
<option value="0">なし（独身・共働き）</option>
<option value="1">配偶者控除あり</option>
<option value="2">配偶者+子1人</option>
<option value="3">配偶者+子2人</option>
</select>
</div>

</div>

<!-- 結果 -->
<div id="stResults" style="margin-top:24px;">

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;text-align:center;">
<div style="padding:20px;background:#fef2f2;border-radius:12px;border:1px solid #fecaca;">
<div style="font-size:12px;color:#64748b;">所得税率（最高税率）</div>
<div id="stRate" style="font-size:36px;font-weight:bold;color:#b91c1c;">20%</div>
</div>
<div style="padding:20px;background:#f0fdf4;border-radius:12px;border:1px solid #bbf7d0;">
<div style="font-size:12px;color:#64748b;">実効税率（税金合計/年収）</div>
<div id="stEffective" style="font-size:36px;font-weight:bold;color:#16a34a;">21.5%</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:8px;margin-top:12px;text-align:center;">
<div style="padding:14px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:11px;color:#64748b;">所得税</div>
<div id="stTax" style="font-size:18px;font-weight:bold;color:#b91c1c;">21万円</div>
</div>
<div style="padding:14px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:11px;color:#64748b;">住民税</div>
<div id="stResident" style="font-size:18px;font-weight:bold;color:#ea580c;">24万円</div>
</div>
<div style="padding:14px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<div style="font-size:11px;color:#64748b;">社会保険料</div>
<div id="stSocial" style="font-size:18px;font-weight:bold;color:#7c3aed;">72万円</div>
</div>
<div style="padding:14px;background:#f0fdf4;border-radius:8px;border:2px solid #16a34a;">
<div style="font-size:11px;color:#64748b;">手取り</div>
<div id="stTakeHome" style="font-size:18px;font-weight:bold;color:#16a34a;">383万円</div>
</div>
</div>

<div style="margin-top:12px;text-align:center;padding:12px;background:white;border-radius:8px;border:1px solid #e2e8f0;">
<span style="font-size:13px;color:#64748b;">月額手取り: </span>
<span id="stMonthly" style="font-size:20px;font-weight:bold;color:#16a34a;">31.9万円</span>
</div>

<!-- 内訳バー -->
<div style="margin-top:20px;padding:20px;background:#f8fafc;border-radius:12px;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 12px 0;font-size:16px;">年収の内訳</h3>
<div id="stBar" style="height:32px;border-radius:8px;overflow:hidden;display:flex;margin-bottom:8px;"></div>
<div style="display:flex;flex-wrap:wrap;gap:10px;font-size:12px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#16a34a;border-radius:2px;"></span> 手取り</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#b91c1c;border-radius:2px;"></span> 所得税</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#ea580c;border-radius:2px;"></span> 住民税</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#7c3aed;border-radius:2px;"></span> 社会保険料</span>
</div>
</div>

<!-- 所得税ブラケット表 -->
<details style="margin-top:20px;">
<summary style="cursor:pointer;font-weight:bold;color:#b91c1c;font-size:15px;">所得税の累進課税ブラケットを表示</summary>
<div style="overflow-x:auto;margin-top:12px;">
<table id="stTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#b91c1c;color:white;">
<th style="padding:8px;text-align:left;">税率</th>
<th style="padding:8px;text-align:right;">課税所得</th>
<th style="padding:8px;text-align:right;">控除額</th>
<th style="padding:8px;text-align:right;">この区分の税額</th>
</tr>
</thead>
<tbody id="stTableBody"></tbody>
</table>
</div>
</details>

<!-- 年収別比較 -->
<div style="margin-top:20px;padding:20px;background:#fffbeb;border-radius:12px;border:1px solid #fde68a;">
<h3 style="margin:0 0 12px 0;font-size:16px;">年収別の手取り比較</h3>
<div id="stScenarios" style="display:grid;gap:8px;"></div>
</div>

</div>

</div>

<script>
const JP_BRACKETS=[
  [0,1950000,0.05,0],
  [1950000,3300000,0.10,97500],
  [3300000,6950000,0.20,427500],
  [6950000,9000000,0.23,636000],
  [9000000,18000000,0.33,1536000],
  [18000000,40000000,0.40,2796000],
  [40000000,Infinity,0.45,4796000]
];

function getType(){return document.querySelector('input[name="stType"]:checked').value;}

function calcEmployeeDeduction(income){
  if(income<=1625000) return 550000;
  if(income<=1800000) return income*0.4-100000;
  if(income<=3600000) return income*0.3+80000;
  if(income<=6600000) return income*0.2+440000;
  if(income<=8500000) return income*0.1+1100000;
  return 1950000;
}

function calcSocialInsurance(income,type){
  if(type==='employee') return Math.round(income*0.1497);
  return Math.round(Math.min(income,10200000)*0.145+income*0.05);
}

function calcIncomeTax(taxableIncome){
  if(taxableIncome<=0) return{tax:0,rate:0,details:[]};
  let tax=0;let topRate=0;const details=[];
  for(const[lo,hi,rate,deduction] of JP_BRACKETS){
if(taxableIncome<=lo) break;
topRate=rate;
const portion=Math.min(taxableIncome,hi)-lo;
const t=portion*rate;
details.push({lo,hi:Math.min(taxableIncome,hi),rate,portion,tax:t});
  }
  tax=Math.floor(taxableIncome*topRate-JP_BRACKETS.find(b=>b[2]===topRate)[3]);
  const recoveryTax=Math.floor(tax*0.021);
  return{tax:tax+recoveryTax,rate:topRate,details};
}

function calcResidentTax(taxableIncome){
  if(taxableIncome<=0) return 0;
  return Math.round(taxableIncome*0.10)+5000;
}

function calcST(){
  const incomeMan=parseFloat(document.getElementById('stIncome').value)||0;
  const income=incomeMan*10000;
  const type=getType();
  const deps=parseInt(document.getElementById('stDependents').value);

  ['employee','freelance'].forEach(t=>{
document.getElementById('lbl-'+t).style.borderColor=t===type?'#b91c1c':'#e2e8f0';
document.getElementById('lbl-'+t).style.background=t===type?'#fef2f2':'white';
  });
  document.getElementById('stFreelanceOpts').style.display=type==='freelance'?'block':'none';

  // 給与所得控除 or 経費
  let deduction=0;
  if(type==='employee'){
deduction=calcEmployeeDeduction(income);
  }else{
const expRate=parseFloat(document.getElementById('stExpenseRate').value)/100;
document.getElementById('stExpenseVal').textContent=Math.round(expRate*100)+'%';
deduction=income*expRate;
if(document.getElementById('stBlueReturn').checked) deduction+=650000;
  }

  const earnedIncome=Math.max(0,income-deduction);

  // 所得控除
  let personalDeduction=480000; // 基礎控除
  const social=calcSocialInsurance(income,type);
  personalDeduction+=social; // 社会保険料控除
  if(deps>=1) personalDeduction+=380000; // 配偶者控除
  if(deps>=2) personalDeduction+=380000; // 扶養控除(子1)
  if(deps>=3) personalDeduction+=380000; // 扶養控除(子2)

  const taxableIncome=Math.max(0,earnedIncome-personalDeduction);
  const{tax:incomeTax,rate:topRate,details}=calcIncomeTax(taxableIncome);
  const residentTax=calcResidentTax(Math.max(0,earnedIncome-personalDeduction+social-social));
  // 住民税は所得控除が若干異なるが簡易計算
  const residentTaxable=Math.max(0,earnedIncome-(personalDeduction-social)-330000-social);
  const residentTaxCalc=calcResidentTax(Math.max(0,earnedIncome-personalDeduction+50000));

  const totalTax=incomeTax+residentTaxCalc+social;
  const takeHome=income-totalTax;
  const effectiveRate=income>0?(totalTax/income)*100:0;

  document.getElementById('stRate').textContent=Math.round(topRate*100)+'%';
  document.getElementById('stEffective').textContent=effectiveRate.toFixed(1)+'%';
  document.getElementById('stTax').textContent=Math.round(incomeTax/10000)+'万円';
  document.getElementById('stResident').textContent=Math.round(residentTaxCalc/10000)+'万円';
  document.getElementById('stSocial').textContent=Math.round(social/10000)+'万円';
  document.getElementById('stTakeHome').textContent=Math.round(takeHome/10000)+'万円';
  document.getElementById('stMonthly').textContent=(takeHome/120000).toFixed(1)+'万円';

  // バー
  if(income>0){
const pTH=((takeHome/income)*100).toFixed(1);
const pIT=((incomeTax/income)*100).toFixed(1);
const pRT=((residentTaxCalc/income)*100).toFixed(1);
const pSI=((social/income)*100).toFixed(1);
document.getElementById('stBar').innerHTML=
'<div style="width:'+pTH+'%;background:#16a34a;height:100%;" title="手取り"></div>'+
'<div style="width:'+pIT+'%;background:#b91c1c;height:100%;" title="所得税"></div>'+
'<div style="width:'+pRT+'%;background:#ea580c;height:100%;" title="住民税"></div>'+
'<div style="width:'+pSI+'%;background:#7c3aed;height:100%;" title="社会保険料"></div>';
  }

  // ブラケット表
  let tbody='';
  JP_BRACKETS.forEach((b,i)=>{
const[lo,hi,rate,ded]=b;
const active=taxableIncome>lo;
const current=taxableIncome>lo&&(hi===Infinity||taxableIncome<=hi);
const portion=active?Math.min(taxableIncome,hi)-lo:0;
const t=portion*rate;
const bg=current?'#fef2f2':i%2===0?'#f8fafc':'white';
const hiStr=hi===Infinity?'〜':'〜'+Math.round(hi/10000)+'万円';
const arrow=current?' ←':'';
tbody+='<tr style="background:'+bg+';'+(current?'font-weight:bold;':'')+'">';
tbody+='<td style="padding:8px;">'+Math.round(rate*100)+'%'+arrow+'</td>';
tbody+='<td style="padding:8px;text-align:right;">'+Math.round(lo/10000)+'万円'+hiStr+'</td>';
tbody+='<td style="padding:8px;text-align:right;">'+Math.round(ded/10000)+'万円</td>';
tbody+='<td style="padding:8px;text-align:right;'+(active?'':'color:#94a3b8;')+'">'+Math.round(t/10000)+'万円</td>';
tbody+='</tr>';
  });
  document.getElementById('stTableBody').innerHTML=tbody;

  // 年収別比較
  const scenarios=[300,400,500,600,700,800,1000,1500];
  let sHTML='';
  scenarios.forEach(s=>{
const sInc=s*10000;
const sDed=type==='employee'?calcEmployeeDeduction(sInc):sInc*(parseFloat(document.getElementById('stExpenseRate').value)/100)+(type==='freelance'&&document.getElementById('stBlueReturn').checked?650000:0);
const sEarned=Math.max(0,sInc-sDed);
const sSocial=calcSocialInsurance(sInc,type);
let sPD=480000+sSocial;
if(deps>=1)sPD+=380000;if(deps>=2)sPD+=380000;if(deps>=3)sPD+=380000;
const sTaxable=Math.max(0,sEarned-sPD);
const sIT=calcIncomeTax(sTaxable).tax;
const sRT=calcResidentTax(Math.max(0,sEarned-sPD+50000));
const sTH=sInc-sIT-sRT-sSocial;
const current=s===incomeMan;
sHTML+='<div style="display:flex;justify-content:space-between;align-items:center;padding:10px 12px;background:'+(current?'#fef2f2':'white')+';border-radius:8px;border:'+(current?'2px solid #b91c1c':'1px solid #e2e8f0')+';font-size:14px;">';
sHTML+='<div><strong>'+s+'万円</strong></div>';
sHTML+='<div style="text-align:right;">手取り <strong style="color:#16a34a;">'+Math.round(sTH/10000)+'万円</strong> ('+((sTH/sInc)*100).toFixed(0)+'%)</div>';
sHTML+='</div>';
  });
  document.getElementById('stScenarios').innerHTML=sHTML;
}

calcST();
</script>

---

## 使い方

1. **年収（額面）を入力** — 源泉徴収票の「支払金額」欄の数字
2. **働き方を選択** — 会社員は給与所得控除が自動適用、フリーランスは経費率・青色申告を設定
3. **扶養家族を選択** — 配偶者控除・扶養控除が反映されます

---

## 日本の所得税率表（2026年）

| 課税所得 | 税率 | 控除額 |
|---|---|---|
| 〜195万円 | 5% | 0円 |
| 195〜330万円 | 10% | 9.75万円 |
| 330〜695万円 | 20% | 42.75万円 |
| 695〜900万円 | 23% | 63.6万円 |
| 900〜1,800万円 | 33% | 153.6万円 |
| 1,800〜4,000万円 | 40% | 279.6万円 |
| 4,000万円〜 | 45% | 479.6万円 |

*復興特別所得税（2.1%）が加算されます。住民税は一律10%+均等割5,000円。*

---

## 手取りを増やす方法

### 1. iDeCo・小規模企業共済を活用する

掛金が全額所得控除になるため、課税所得を直接減らせます。年収500万円で月2.3万円のiDeCoなら、年間約5.5万円の節税効果。

### 2. ふるさと納税を活用する

実質2,000円の負担で各地の返礼品がもらえます。控除上限額は年収と家族構成で変わります。

### 3. 医療費控除を忘れずに申告する

年間医療費が10万円を超えた場合、確定申告で控除が受けられます。

### 4. フリーランスは青色申告を必ず選択する

青色申告特別控除65万円は非常に大きな節税効果があります。年収500万円（経費30%）の場合、白色申告より約13万円の節税になります。

---

## 関連ツール

> 年収から手取りを詳細計算 → [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)
> 副業収入の税金を計算 → [副業税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/)
> iDeCoの節税効果を計算 → [iDeCoシミュレーター](/ja/tools/ideco-simulator/)
> ふるさと納税の控除上限額を計算 → [ふるさと納税シミュレーター](/ja/tools/furusato-nozei-simulator/)
> 月収から理想の支出配分を計算 → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)

---

## 関連記事

- [フリーランス確定申告のやり方](/ja/posts/フリーランス-確定申告-やり方/)
- [副業確定申告20万以下のやり方](/ja/posts/副業-確定申告-20万以下-やり方/)
- [freee青色申告65万円控除](/ja/posts/freee-aoiro-shinkoku-65man/)
- [確定拠出年金と確定給付年金の違い](/ja/posts/kakutei-kyoshutsu-nenkin-chigai/)

---

## Productivity Worksの無料ツール

当サイトの計算ツールはすべて**完全無料**、ブラウザ上で動作し、データは一切保存されません。

[全ツール一覧はこちら](/ja/tools/)

> 確定申告を簡単に済ませたいなら、<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freee会計</a>がおすすめです。銀行口座・クレジットカードと連携して仕訳を自動化し、青色申告書類もガイドに沿って作成できます。

*本記事にはアフィリエイトリンクが含まれています。読者の皆様に追加費用は発生しません。*
