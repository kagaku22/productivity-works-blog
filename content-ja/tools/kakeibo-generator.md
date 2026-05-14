---
title: "家計簿シミュレーター｜月収から理想の支出配分を自動計算"
date: 2026-05-14
draft: false
slug: "kakeibo-generator"
description: "月収を入力するだけで理想の家計配分を自動計算。住居費・食費・貯蓄の目安がわかる無料シミュレーター。家計の見直しに最適です。"
author: "Productivity Works編集部"
categories:
  - "マネー・個人金融"
tags:
  - "家計簿"
  - "節約"
  - "計算ツール"
  - "貯蓄"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/kakeibo-generator.png"
  alt: "家計簿シミュレーター｜月収から理想の支出配分を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 家計簿シミュレーター｜理想の支出配分を自動計算

手取り月収を入力するだけで、**理想的な支出配分**を自動計算します。FP（ファイナンシャルプランナー）推奨の配分比率をベースにしています。

<div id="kakeibo-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">手取り月収（万円）</label>
<input type="range" id="monthlyIncome" min="10" max="100" step="1" value="25" oninput="calcBudget()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>10万円</span><span id="incomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">25万円</span><span>100万円</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">世帯タイプ</label>
<select id="household" onchange="calcBudget()" style="width:100%;padding:8px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="single">一人暮らし</option>
<option value="couple">二人暮らし（共働き）</option>
<option value="family">ファミリー（子どもあり）</option>
</select>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">毎月の貯蓄・投資目標額</div>
<div id="savingsTarget" style="font-size:36px;font-weight:bold;">50,000円</div>
<div style="font-size:13px;margin-top:4px;">年間: <span id="savingsYearly">600,000円</span></div>
</div>

<div id="budgetBreakdown" style="margin-bottom:16px;"></div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>配分基準:</strong> FP推奨の支出比率をベースに計算。実際の家計は個人の状況により異なります。あくまで目安としてご活用ください。
</div>

</div>

<script>
function calcBudget(){
  var income=parseInt(document.getElementById('monthlyIncome').value)*10000;
  var type=document.getElementById('household').value;

  var ratios;
  if(type==='single'){
    ratios=[
      {name:'住居費',rate:0.28,color:'#ef4444'},
      {name:'食費',rate:0.15,color:'#f97316'},
      {name:'水道光熱費',rate:0.05,color:'#eab308'},
      {name:'通信費',rate:0.05,color:'#22c55e'},
      {name:'日用品・衣服',rate:0.05,color:'#06b6d4'},
      {name:'交際費・娯楽',rate:0.08,color:'#8b5cf6'},
      {name:'交通費',rate:0.04,color:'#ec4899'},
      {name:'保険・医療',rate:0.03,color:'#6366f1'},
      {name:'自己投資',rate:0.05,color:'#14b8a6'},
      {name:'予備費',rate:0.02,color:'#94a3b8'},
      {name:'貯蓄・投資',rate:0.20,color:'#2563eb'}
    ];
  } else if(type==='couple'){
    ratios=[
      {name:'住居費',rate:0.25,color:'#ef4444'},
      {name:'食費',rate:0.15,color:'#f97316'},
      {name:'水道光熱費',rate:0.05,color:'#eab308'},
      {name:'通信費',rate:0.05,color:'#22c55e'},
      {name:'日用品・衣服',rate:0.05,color:'#06b6d4'},
      {name:'交際費・娯楽',rate:0.07,color:'#8b5cf6'},
      {name:'交通費',rate:0.04,color:'#ec4899'},
      {name:'保険・医療',rate:0.04,color:'#6366f1'},
      {name:'自己投資',rate:0.03,color:'#14b8a6'},
      {name:'予備費',rate:0.02,color:'#94a3b8'},
      {name:'貯蓄・投資',rate:0.25,color:'#2563eb'}
    ];
  } else {
    ratios=[
      {name:'住居費',rate:0.25,color:'#ef4444'},
      {name:'食費',rate:0.18,color:'#f97316'},
      {name:'水道光熱費',rate:0.06,color:'#eab308'},
      {name:'通信費',rate:0.04,color:'#22c55e'},
      {name:'日用品・衣服',rate:0.06,color:'#06b6d4'},
      {name:'教育費',rate:0.08,color:'#8b5cf6'},
      {name:'交通費',rate:0.04,color:'#ec4899'},
      {name:'保険・医療',rate:0.06,color:'#6366f1'},
      {name:'娯楽・交際',rate:0.05,color:'#14b8a6'},
      {name:'予備費',rate:0.03,color:'#94a3b8'},
      {name:'貯蓄・投資',rate:0.15,color:'#2563eb'}
    ];
  }

  var savings=0;
  var html='';
  for(var i=0;i<ratios.length;i++){
    var amt=Math.floor(income*ratios[i].rate);
    var pct=Math.round(ratios[i].rate*100);
    if(ratios[i].name==='貯蓄・投資') savings=amt;
    html+='<div style="display:flex;align-items:center;padding:8px 0;border-bottom:1px solid #e2e8f0;">';
    html+='<div style="width:12px;height:12px;border-radius:50%;background:'+ratios[i].color+';margin-right:10px;flex-shrink:0;"></div>';
    html+='<div style="flex:1;font-size:14px;">'+ratios[i].name+' <span style="color:#94a3b8;">('+pct+'%)</span></div>';
    html+='<div style="font-weight:bold;font-size:15px;">'+amt.toLocaleString()+'円</div>';
    html+='</div>';
  }

  document.getElementById('incomeVal').textContent=(income/10000)+'万円';
  document.getElementById('savingsTarget').textContent=savings.toLocaleString()+'円';
  document.getElementById('savingsYearly').textContent=(savings*12).toLocaleString()+'円';
  document.getElementById('budgetBreakdown').innerHTML=html;
}
calcBudget();
</script>

---

## 貯蓄を増やすためのアクション

シミュレーション結果をもとに、貯蓄を効率よく増やしましょう。

- **固定費を見直す** → 通信費・保険料・サブスクの見直しで月1〜2万円削減できることも
- **貯蓄分はNISAで運用** → 銀行預金より高いリターンが期待できる → [新NISAの始め方](/ja/posts/新nisa-始め方-手順/)
- **副業で収入を増やす** → 月3〜5万円の副収入で貯蓄ペースが倍に → [副業の始め方ガイド](/ja/posts/副業-始め方-初心者-2026/)
- **会計ソフトで管理** → [freee](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)なら銀行口座と自動連携で家計管理が楽に

---

## よくある質問

**Q. 住居費は手取りの何%が目安ですか？**
一般的には手取りの25〜30%が目安です。一人暮らしなら28%程度、ファミリーなら25%以下を目指しましょう。

**Q. 貯蓄率20%は現実的ですか？**
一人暮らしの場合、手取り25万円なら月5万円の貯蓄です。固定費の見直しと先取り貯蓄を組み合わせれば十分に達成可能です。

**Q. ボーナスはどう扱えばいいですか？**
ボーナスの50%以上を貯蓄・投資に回すのが理想です。毎月の家計とは別に管理しましょう。

---

## 関連ツール・記事

- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 年収から手取りを計算
- [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) — 将来の資産額を計算
- [NISAとiDeCo、どっちを先に？](/ja/posts/nisa-ideco-docchi-saki/)
- [クレジットカードおすすめ](/ja/posts/credit-card-osusume-2026/)
