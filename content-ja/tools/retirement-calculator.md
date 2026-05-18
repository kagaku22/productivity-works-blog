---
title: "老後資産計算機 | iDeCo・NISA積立シミュレーター（無料）"
date: 2025-09-01
draft: false
slug: "retirement-calculator"
description: "無料の老後資産計算機。現在の年齢・毎月の積立額・期待利回りを入力して、退職時の想定資産額をシミュレーション。iDeCo・NISA対応。"
author: "Productivity Works Editorial"
categories:
  - "無料ツール"
tags:
  - "計算機"
  - "老後資産"
  - "iDeCo"
  - "NISA"
  - "資産運用"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/retirement-calculator.png"
  alt: "老後資産計算機 | iDeCo・NISA積立シミュレーター"
  relative: false
---

*本ページにはアフィリエイトリンクが含まれます。*

# 老後資産計算機

現在の年齢・毎月の積立額・期待利回りを入力して、退職時の**老後資産**を見積もりましょう。

<div id="retire-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">現在の年齢</label>
<input type="range" id="age" min="18" max="60" step="1" value="30" oninput="calcRetire()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>18歳</span><span id="ageVal" style="font-weight:bold;font-size:18px;color:#2563eb;">30</span><span>60歳</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">毎月の積立額（円）</label>
<input type="range" id="contrib" min="5000" max="100000" step="1000" value="30000" oninput="calcRetire()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>5,000円</span><span id="contribVal" style="font-weight:bold;font-size:18px;color:#2563eb;">30,000円</span><span>100,000円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">雇用主マッチング率（%）</label>
<input type="range" id="match" min="0" max="100" step="10" value="0" oninput="calcRetire()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span id="matchVal" style="font-weight:bold;font-size:18px;color:#2563eb;">0%</span><span>100%</span></div>
<div style="font-size:12px;color:#94a3b8;margin-top:2px;">企業型DCなどで会社が上乗せしてくれる割合</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">年間期待利回り（%）</label>
<input type="range" id="rate" min="1" max="10" step="0.5" value="5" oninput="calcRetire()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1%</span><span id="rateVal" style="font-weight:bold;font-size:18px;color:#2563eb;">5.0%</span><span>10%</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">退職年齢</label>
<input type="range" id="retireAge" min="55" max="70" step="1" value="65" oninput="calcRetire()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>55歳</span><span id="retireAgeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">65</span><span>70歳</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">退職時の想定資産額</div>
<div id="totalSavings" style="font-size:36px;font-weight:bold;">¥0</div>
<div style="font-size:13px;margin-top:4px;">退職まであと <span id="yearsLeft" style="font-weight:bold;">35</span> 年</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">自分の積立額</div>
<div id="yourContrib" style="font-size:16px;font-weight:bold;color:#0369a1;">¥0</div>
</div>
<div style="background:#f3e8ff;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">会社マッチング</div>
<div id="employerContrib" style="font-size:16px;font-weight:bold;color:#7c3aed;">¥0</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">運用益</div>
<div id="growthAmt" style="font-size:16px;font-weight:bold;color:#15803d;">¥0</div>
</div>
</div>

<div style="background:#fef9c3;border-radius:8px;padding:16px;margin-bottom:16px;">
<div style="font-size:13px;color:#a16207;margin-bottom:4px;"><strong>退職後の月間引出額（4%ルール）：</strong></div>
<div id="monthlyIncome" style="font-size:22px;font-weight:bold;color:#a16207;text-align:center;">¥0/月</div>
<div style="font-size:12px;color:#a16207;text-align:center;margin-top:4px;">資産の4%を毎年取り崩す場合の目安</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>前提条件：</strong> 毎月積立・複利計算（月次）。4%ルールは持続可能な年間取崩率の目安。実際の運用成績は異なります。インフレや税金は考慮していません。
</div>

</div>

<script>
function calcRetire(){
  var age=parseInt(document.getElementById('age').value);
  var contrib=parseInt(document.getElementById('contrib').value);
  var matchPct=parseInt(document.getElementById('match').value)/100;
  var r=parseFloat(document.getElementById('rate').value)/100;
  var retireAge=parseInt(document.getElementById('retireAge').value);

  if(retireAge<=age) retireAge=age+1;

  var years=retireAge-age;
  var mr=r/12;
  var n=years*12;
  var totalMonthly=contrib+contrib*matchPct;
  var fv=totalMonthly*((Math.pow(1+mr,n)-1)/mr);
  var yourTotal=contrib*n;
  var employerTotal=Math.floor(contrib*matchPct)*n;
  var growth=fv-yourTotal-employerTotal;
  var monthlyIncome=Math.floor(fv*0.04/12);

  document.getElementById('ageVal').textContent=age;
  document.getElementById('contribVal').textContent=contrib.toLocaleString('ja-JP')+'\u5186';
  document.getElementById('matchVal').textContent=Math.round(matchPct*100)+'%';
  document.getElementById('rateVal').textContent=(r*100).toFixed(1)+'%';
  document.getElementById('retireAgeVal').textContent=retireAge;
  document.getElementById('totalSavings').textContent='\u00a5'+Math.floor(fv).toLocaleString('ja-JP');
  document.getElementById('yearsLeft').textContent=years;
  document.getElementById('yourContrib').textContent='\u00a5'+yourTotal.toLocaleString('ja-JP');
  document.getElementById('employerContrib').textContent='\u00a5'+employerTotal.toLocaleString('ja-JP');
  document.getElementById('growthAmt').textContent='\u00a5'+Math.floor(growth).toLocaleString('ja-JP');
  document.getElementById('monthlyIncome').textContent='\u00a5'+monthlyIncome.toLocaleString('ja-JP')+'/\u6708';
}
calcRetire();
</script>

---

## 老後資産を最大化するには

- **会社マッチングをフル活用** — 企業型DCがある場合、マッチング上限まで積み立てないと「もらえるお金を捨てている」のと同じです
- **非課税枠を使い切る** — 2026年のNISA年間投資枠：つみたて投資枠120万円、成長投資枠240万円
- **低コストインデックスファンドを選ぶ** — 信託報酬の差は複利で何百万円もの違いになります
- **毎年積立額を増やす** — 昇給のたびに積立額を1〜2%引き上げると、苦痛なく資産を積み上げられます

---

## iDeCo・NISA・企業型DCの比較

| 項目 | iDeCo | つみたてNISA枠 | 成長投資枠 |
|------|-------|--------------|----------|
| 年間上限 | 〜81.6万円（属性による） | 120万円 | 240万円 |
| 掛金の税優遇 | 全額所得控除 | なし（税引後） | なし（税引後） |
| 運用益・引出 | 引出時課税 | 非課税 | 非課税 |
| 受取開始 | 60〜75歳 | いつでも | いつでも |
| 向いている人 | 節税重視・長期 | 積立投資初心者 | 個別株・ETF投資 |

---

## よくある質問

**Q: 4%ルールとは何ですか？**
退職1年目に資産の4%を引き出し、以降はインフレに合わせて調整する戦略です。研究では30年間の退職生活を支えられるとされています。

**Q: 期待利回りはどのくらいに設定すればよいですか？**
全世界株式インデックスは過去30年で年平均7〜10%程度のリターンを上げています。インフレや手数料を差し引いた実質ベースでは5%が保守的な目安です。

**Q: いつから始めるべきですか？**
できるだけ早く。25歳と35歳から同額を積み立てた場合、退職時の資産額は約2倍近く変わります（複利の力）。

---

## 関連ツール

- [複利計算機](/tools/compound-interest-calculator/) — 投資の成長をシミュレーション
- [予算プランナー](/tools/budget-planner/) — 毎月の積立余力を確認
- [純資産計算機](/tools/net-worth-calculator/) — 資産と負債の全体像を把握

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)
