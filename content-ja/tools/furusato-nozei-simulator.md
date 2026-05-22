---
title: "ふるさと納税シミュレーター｜控除上限額・自己負担・節税効果を自動計算【2026年版】"
date: 2025-11-06
draft: false
slug: "furusato-nozei-simulator"
description: "年収・家族構成を入力してふるさと納税の控除上限額を自動計算。自己負担2,000円で寄付できる上限額、節税効果、おすすめ返礼品の還元率も確認できる無料シミュレーター。"
author: "Productivity Works編集部"
categories:
  - "節税・税金"
tags:
  - "ふるさと納税"
  - "シミュレーション"
  - "控除上限額"
  - "節税"
  - "計算ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/furusato-nozei-simulator.png"
  alt: "ふるさと納税シミュレーター｜控除上限額・自己負担・節税効果を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# ふるさと納税シミュレーター【2026年版】

年収と家族構成を入力して、**ふるさと納税の控除上限額**と**実質的な節税効果**を自動計算します。

<div id="fn-calc" style="max-width:680px;margin:0 auto;font-family:'Noto Sans JP',sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">年収（額面）</label>
<input type="range" id="fnIncome" min="200" max="2500" step="10" value="500" oninput="calcFN()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>200万円</span><span id="fnIncVal" style="font-weight:bold;font-size:20px;color:#2563eb;">500万円</span><span>2,500万円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">家族構成</label>
<select id="fnFamily" onchange="calcFN()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b !important;background:#fff !important;">
<option value="single">独身または共働き（配偶者控除なし）</option>
<option value="couple">夫婦（配偶者控除あり）</option>
<option value="couple1">夫婦+子1人（高校生）</option>
<option value="couple2">夫婦+子2人（大学生+高校生）</option>
</select>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">住宅ローン控除</label>
<select id="fnLoan" onchange="calcFN()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b !important;background:#fff !important;">
<option value="0">なし</option>
<option value="100000">あり（年10万円）</option>
<option value="200000">あり（年20万円）</option>
<option value="300000">あり（年30万円）</option>
</select>
</div>

<div id="fnResult" style="margin-top:24px;"></div>

</div>

<div style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;">
<h3 style="margin:0 0 16px;color:#166534;font-size:16px;">控除上限額の目安表</h3>
<div id="fnTable"></div>
</div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">返礼品の実質還元率</h3>
<div id="fnReturn"></div>
</div>

</div>

<script>
function fmt(n){return Math.round(n).toLocaleString('ja-JP');}

function calcFurusatoLimit(income,familyType,loanDeduction){
  var annual=income*10000;
  // 給与所得控除
  var deduction;
  if(annual<=1625000) deduction=550000;
  else if(annual<=1800000) deduction=annual*0.4-100000;
  else if(annual<=3600000) deduction=annual*0.3+80000;
  else if(annual<=6600000) deduction=annual*0.2+440000;
  else if(annual<=8500000) deduction=annual*0.1+1100000;
  else deduction=1950000;

  var shotokuKin額=annual-deduction;

  // 所得控除
  var kiso=480000; // 基礎控除
  var shakai=annual*0.15; // 社会保険料（概算15%）
  var haigusha=0,fuyou=0;
  if(familyType==='couple') haigusha=380000;
  else if(familyType==='couple1'){haigusha=380000;fuyou=380000;}
  else if(familyType==='couple2'){haigusha=380000;fuyou=380000+630000;}

  var totalDeduction=kiso+shakai+haigusha+fuyou;
  var taxableIncome=Math.max(0,shotokuKin額-totalDeduction);

  // 所得税率
  var taxRate;
  if(taxableIncome<=1950000) taxRate=0.05;
  else if(taxableIncome<=3300000) taxRate=0.10;
  else if(taxableIncome<=6950000) taxRate=0.20;
  else if(taxableIncome<=9000000) taxRate=0.23;
  else if(taxableIncome<=18000000) taxRate=0.33;
  else if(taxableIncome<=40000000) taxRate=0.40;
  else taxRate=0.45;

  // 住民税所得割額（概算）
  var juminTaxable=taxableIncome;
  var juminTax=juminTaxable*0.10;

  // ふるさと納税上限額の計算
  // 上限 = 住民税所得割額 × 20% ÷ (1 - 所得税率×1.021 - 住民税率10%) + 2000
  // 簡易計算
  var denominator=1-taxRate*1.021-0.10;
  if(denominator<=0) denominator=0.01;
  var limit=juminTax*0.20/denominator+2000;

  // 住宅ローン控除の影響（控除分だけ上限が下がる可能性）
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

  document.getElementById('fnIncVal').textContent=fmt(income)+'万円';

  var r=calcFurusatoLimit(income,family,loan);
  var limitMan=Math.floor(r.limit/10000);
  var returnValue=Math.floor(r.limit*0.3); // 返礼品還元率30%

  var html='<div style="text-align:center;padding:20px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
  html+='<div style="font-size:13px;color:#64748b;">ふるさと納税 控除上限額（目安）</div>';
  html+='<div style="font-size:40px;font-weight:bold;color:#2563eb;">'+fmt(r.limit)+'<span style="font-size:16px;">円</span></div>';
  html+='<div style="font-size:14px;color:#64748b;margin-top:4px;">（約'+fmt(limitMan)+'万円）</div>';
  html+='</div>';

  html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-top:16px;text-align:center;">';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">自己負担</div><div style="font-size:20px;font-weight:bold;color:#ef4444;">2,000<span style="font-size:12px;">円</span></div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">返礼品の価値（約30%）</div><div style="font-size:20px;font-weight:bold;color:#10b981;">'+fmt(returnValue)+'<span style="font-size:12px;">円</span></div></div>';
  html+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"><div style="font-size:11px;color:#64748b;">実質お得額</div><div style="font-size:20px;font-weight:bold;color:#f59e0b;">'+fmt(returnValue-2000)+'<span style="font-size:12px;">円</span></div></div>';
  html+='</div>';

  html+='<div style="margin-top:12px;font-size:12px;color:#64748b;text-align:center;">※所得税率 '+Math.round(r.taxRate*100)+'%（復興特別所得税含む）で計算。実際の上限額は個人の控除状況により異なります。</div>';

  document.getElementById('fnResult').innerHTML=html;

  // Reference table
  var incomes=[300,400,500,600,700,800,900,1000,1200,1500,2000];
  var thtml='<table style="width:100%;border-collapse:collapse;font-size:13px;">';
  thtml+='<tr style="border-bottom:2px solid #10b981;"><th style="text-align:left;padding:6px;">年収</th><th style="text-align:right;padding:6px;">独身</th><th style="text-align:right;padding:6px;">夫婦</th><th style="text-align:right;padding:6px;">夫婦+子1</th></tr>';
  for(var i=0;i<incomes.length;i++){
var s=calcFurusatoLimit(incomes[i],'single',0);
var c=calcFurusatoLimit(incomes[i],'couple',0);
var c1=calcFurusatoLimit(incomes[i],'couple1',0);
var bg=incomes[i]===income?'#dcfce7':i%2===0?'#fff':'#f0fdf4';
var bold=incomes[i]===income?'font-weight:bold;':'';
thtml+='<tr style="background:'+bg+';'+bold+'">';
thtml+='<td style="padding:6px;">'+fmt(incomes[i])+'万円</td>';
thtml+='<td style="padding:6px;text-align:right;">'+fmt(s.limit)+'円</td>';
thtml+='<td style="padding:6px;text-align:right;">'+fmt(c.limit)+'円</td>';
thtml+='<td style="padding:6px;text-align:right;">'+fmt(c1.limit)+'円</td>';
thtml+='</tr>';
  }
  thtml+='</table>';
  thtml+='<div style="margin-top:8px;font-size:11px;color:#64748b;">※概算値です。医療費控除・生命保険料控除等がある場合は上限額が変わります。</div>';
  document.getElementById('fnTable').innerHTML=thtml;

  // Return goods section
  var rhtml='<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;">';
  var goods=[
{name:'お米 20kg',price:20000,value:8000},
{name:'国産牛 1kg',price:15000,value:5000},
{name:'ホタテ 1kg',price:12000,value:4000},
{name:'シャインマスカット',price:10000,value:3500}
  ];
  for(var i=0;i<goods.length;i++){
var canAfford=r.limit>=goods[i].price?'#10b981':'#94a3b8';
var badge=r.limit>=goods[i].price?'申込OK':'上限超過';
var badgeBg=r.limit>=goods[i].price?'#dcfce7':'#f1f5f9';
rhtml+='<div style="padding:12px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;">';
rhtml+='<div style="font-size:13px;font-weight:bold;color:#1e293b;">'+goods[i].name+'</div>';
rhtml+='<div style="font-size:12px;color:#64748b;">寄付額: '+fmt(goods[i].price)+'円</div>';
rhtml+='<div style="font-size:12px;color:#64748b;">市場価値: 約'+fmt(goods[i].value)+'円</div>';
rhtml+='<span style="display:inline-block;margin-top:4px;padding:2px 8px;font-size:11px;font-weight:bold;background:'+badgeBg+';color:'+canAfford+';border-radius:4px;">'+badge+'</span>';
rhtml+='</div>';
  }
  rhtml+='</div>';
  rhtml+='<div style="margin-top:12px;font-size:12px;color:#92400e;text-align:center;">※返礼品の還元率は2026年時点の一般的な目安です。自治体・時期により変動します。</div>';
  document.getElementById('fnReturn').innerHTML=rhtml;
}

document.addEventListener('DOMContentLoaded',function(){calcFN();});
calcFN();
</script>

---

## ふるさと納税の仕組み

ふるさと納税は、好きな自治体に寄付をすると**寄付額−2,000円**が所得税・住民税から控除される制度です。さらに返礼品（寄付額の約30%相当）がもらえるため、**実質2,000円の自己負担で各地の特産品を受け取れる**お得な仕組みです。

### 控除上限額を超えないことが大切

控除上限額を超えた分は純粋な寄付（自己負担）になります。このシミュレーターで上限額を確認してから寄付しましょう。

### ふるさと納税の手続き

1. **寄付先を選ぶ** — 返礼品から選ぶのが一般的
2. **寄付を申し込む** — ふるさと納税サイト経由が便利
3. **返礼品と寄付金受領証明書を受け取る**
4. **確定申告またはワンストップ特例制度で控除申請**

ワンストップ特例制度を使えば、確定申告不要で控除を受けられます（寄付先5自治体まで）。

---

> ふるさと納税の確定申告が必要な方は、[freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)を使えばガイドに沿って簡単に完了できます。

> 投資と節税を組み合わせるなら、iDeCoの併用もおすすめです。「[iDeCo節税シミュレーター](/ja/tools/ideco-simulator/)」で節税効果を確認してみてください。

---

**関連記事**
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)
- [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/)
- [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/)
- [転職年収シミュレーター](/ja/tools/tenshoku-nenshu-simulator/)

## 関連記事

- [ふるさと納税 やり方 完全ガイド【2026年版・初心者向け】](/ja/posts/furusato-nozei-yarikata-2026/)
