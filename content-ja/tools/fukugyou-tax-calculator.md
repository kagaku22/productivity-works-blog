---
title: "副業の税金計算シミュレーター｜確定申告が必要か自動判定【2026年版】"
date: 2026-05-14
draft: false
slug: "fukugyou-tax-calculator"
description: "副業の税金を自動計算。本業年収と副業収入を入力するだけで、追加税額・確定申告の要否・手取り額がわかる無料シミュレーター。"
author: "Productivity Works編集部"
categories:
  - "副業・フリーランス"
tags:
  - "副業"
  - "税金"
  - "確定申告"
  - "計算ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/fukugyou-tax-calculator.png"
  alt: "副業の税金計算シミュレーター｜確定申告が必要か自動判定"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 副業の税金計算シミュレーター【2026年版】

本業の年収と副業の収入・経費を入力するだけで、**追加で支払う税金**と**確定申告の要否**を自動判定します。

<div id="tax-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">本業の年収（額面・万円）</label>
<input type="range" id="mainIncome" min="200" max="1500" step="10" value="500" oninput="calcSideTax()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>200万円</span><span id="mainIncomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">500万円</span><span>1,500万円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">副業の年間収入（万円）</label>
<input type="range" id="sideRevenue" min="0" max="500" step="5" value="100" oninput="calcSideTax()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0万円</span><span id="sideRevenueVal" style="font-weight:bold;font-size:18px;color:#2563eb;">100万円</span><span>500万円</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">副業の年間経費（万円）</label>
<input type="range" id="sideExpense" min="0" max="200" step="5" value="20" oninput="calcSideTax()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0万円</span><span id="sideExpenseVal" style="font-weight:bold;font-size:18px;color:#2563eb;">20万円</span><span>200万円</span></div>
</div>

<div id="filingAlert" style="background:#dc2626;color:white;border-radius:8px;padding:16px;text-align:center;margin-bottom:16px;font-weight:bold;font-size:18px;">
確定申告が必要です
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">副業にかかる追加税額（概算）</div>
<div id="additionalTax" style="font-size:36px;font-weight:bold;">162,000円</div>
<div style="font-size:13px;margin-top:4px;">副業の手取り: <span id="sideTedori" style="font-weight:bold;">638,000円</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">副業所得（収入-経費）</div>
<div id="sideIncome" style="font-size:16px;font-weight:bold;color:#0369a1;">800,000円</div>
</div>
<div style="background:#fee2e2;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">適用される税率</div>
<div id="taxRate" style="font-size:16px;font-weight:bold;color:#dc2626;">所得税20%+住民税10%</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#fef3c7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">追加所得税</div>
<div id="addIncomeTax" style="font-size:16px;font-weight:bold;color:#d97706;">82,000円</div>
</div>
<div style="background:#fce7f3;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">追加住民税</div>
<div id="addResidentTax" style="font-size:16px;font-weight:bold;color:#be185d;">80,000円</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>計算条件:</strong> 会社員（給与所得者）、青色申告なし（雑所得扱い）の概算値。青色申告を適用すると最大65万円の追加控除が受けられます。実際の税額は個人の控除状況により異なります。
</div>

</div>

<script>
function calcSideTax(){
  var mainAnnual=parseInt(document.getElementById('mainIncome').value)*10000;
  var sideRev=parseInt(document.getElementById('sideRevenue').value)*10000;
  var sideExp=parseInt(document.getElementById('sideExpense').value)*10000;
  var sideShotoku=Math.max(sideRev-sideExp,0);

  // 本業の給与所得控除
  var mainDed;
  if(mainAnnual<=1625000) mainDed=550000;
  else if(mainAnnual<=1800000) mainDed=mainAnnual*0.4-100000;
  else if(mainAnnual<=3600000) mainDed=mainAnnual*0.3+80000;
  else if(mainAnnual<=6600000) mainDed=mainAnnual*0.2+440000;
  else if(mainAnnual<=8500000) mainDed=mainAnnual*0.1+1100000;
  else mainDed=1950000;

  var mainShotoku=mainAnnual-mainDed;
  var socialIns=Math.floor(mainAnnual*0.147);
  var basicDed=480000;

  // 本業のみの課税所得
  var mainTaxable=Math.max(mainShotoku-basicDed-socialIns,0);

  // 本業+副業の課税所得
  var totalTaxable=Math.max(mainShotoku+sideShotoku-basicDed-socialIns,0);

  // 所得税計算関数
  function incomeTax(t){
    var tax;
    if(t<=1950000) tax=t*0.05;
    else if(t<=3300000) tax=t*0.1-97500;
    else if(t<=6950000) tax=t*0.2-427500;
    else if(t<=9000000) tax=t*0.23-636000;
    else if(t<=18000000) tax=t*0.33-1536000;
    else if(t<=40000000) tax=t*0.40-2796000;
    else tax=t*0.45-4796000;
    return Math.floor(tax*1.021);
  }

  var mainTax=incomeTax(mainTaxable);
  var totalTax=incomeTax(totalTaxable);
  var addIncomeTax=totalTax-mainTax;

  // 住民税（副業所得×10%）
  var addResidentTax=Math.floor(sideShotoku*0.1);

  var totalAddTax=addIncomeTax+addResidentTax;
  var sideTedori=sideShotoku-totalAddTax;

  // 適用税率の表示
  var marginalRate;
  if(totalTaxable<=1950000) marginalRate='5%';
  else if(totalTaxable<=3300000) marginalRate='10%';
  else if(totalTaxable<=6950000) marginalRate='20%';
  else if(totalTaxable<=9000000) marginalRate='23%';
  else if(totalTaxable<=18000000) marginalRate='33%';
  else marginalRate='40%+';

  // 確定申告判定
  var needFiling=sideShotoku>200000;
  var alertEl=document.getElementById('filingAlert');
  if(sideShotoku===0){
    alertEl.style.background='#94a3b8';
    alertEl.textContent='副業所得0円：申告不要';
  } else if(needFiling){
    alertEl.style.background='#dc2626';
    alertEl.textContent='確定申告が必要です（所得20万円超）';
  } else {
    alertEl.style.background='#16a34a';
    alertEl.textContent='確定申告は不要です（所得20万円以下）';
  }

  document.getElementById('mainIncomeVal').textContent=(mainAnnual/10000).toLocaleString()+'万円';
  document.getElementById('sideRevenueVal').textContent=(sideRev/10000).toLocaleString()+'万円';
  document.getElementById('sideExpenseVal').textContent=(sideExp/10000).toLocaleString()+'万円';
  document.getElementById('additionalTax').textContent=Math.max(totalAddTax,0).toLocaleString()+'円';
  document.getElementById('sideTedori').textContent=Math.max(sideTedori,0).toLocaleString()+'円';
  document.getElementById('sideIncome').textContent=sideShotoku.toLocaleString()+'円';
  document.getElementById('taxRate').textContent='所得税'+marginalRate+'+住民税10%';
  document.getElementById('addIncomeTax').textContent=Math.max(addIncomeTax,0).toLocaleString()+'円';
  document.getElementById('addResidentTax').textContent=Math.max(addResidentTax,0).toLocaleString()+'円';
}
calcSideTax();
</script>

---

## 副業の税金を減らす方法

### 1. 経費を漏れなく計上する

副業に関連する支出はすべて経費にできます。

| 経費項目 | 具体例 |
|---------|-------|
| 通信費 | インターネット代（副業割合で按分） |
| PC・機材 | パソコン、カメラ、ソフトウェア |
| 書籍・研修 | 専門書、オンライン講座 |
| 交通費 | 打ち合わせの交通費 |
| 家賃按分 | 自宅作業スペース分 |

### 2. 青色申告で65万円控除

開業届を出して青色申告にすれば、最大65万円の追加控除が受けられます。副業所得100万円の場合、約13万円の節税効果です。

会計ソフトを使えば複式簿記も自動化できます → **[freeeで無料トライアル開始](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)**

### 3. iDeCoで節税

iDeCoの掛金は全額所得控除。副業で増えた税負担をiDeCoで相殺できます → [iDeCoおすすめ証券会社](/ja/posts/ideco-osusume-shouken/)

---

## よくある質問

**Q. 副業所得20万円以下なら本当に申告不要ですか？**
所得税は不要ですが、住民税の申告が別途必要な場合があります。お住まいの市区町村に確認してください。

**Q. 会社にバレない方法はありますか？**
確定申告書で住民税を「自分で納付（普通徴収）」にすれば、会社の給与から天引きされません → [副業がバレない方法](/ja/posts/副業-バレない-方法-住民税/)

**Q. 副業の種類で税金は変わりますか？**
雑所得（アフィリエイト・ライティング等）と事業所得（開業届あり）で控除額が異なります。継続的な副業なら開業届を出して事業所得にするのが有利です。

---

## 関連ツール・記事

- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 本業の手取りを計算
- [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) — 副業収入を投資に回した場合の試算
- [家計簿シミュレーター](/ja/tools/kakeibo-generator/) — 理想の支出配分を計算
- [副業の確定申告やり方](/ja/posts/fukugyou-kakuteishinkoku-yarikata-2026/)
- [フリーランス確定申告ガイド](/ja/posts/フリーランス-確定申告-やり方/)
