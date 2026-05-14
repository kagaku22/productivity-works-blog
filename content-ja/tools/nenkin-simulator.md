---
title: "年金シミュレーター｜将来の年金受給額を無料で計算【2026年版】"
date: 2026-05-14
draft: false
slug: "nenkin-simulator"
description: "年齢・年収・加入期間を入力するだけで、将来の年金受給額を自動計算。老齢基礎年金と老齢厚生年金の内訳、繰上げ・繰下げ受給の差額もわかる無料シミュレーター。"
author: "Productivity Works編集部"
categories:
  - "投資・資産運用"
tags:
  - "年金"
  - "シミュレーター"
  - "老後"
  - "計算ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/nenkin-simulator.png"
  alt: "年金シミュレーター｜将来の年金受給額を無料で計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 年金受給額シミュレーター【2026年版】

年齢・平均年収・加入期間を入力するだけで、**将来の年金受給額**（老齢基礎年金＋老齢厚生年金）を自動計算します。

<div id="nenkin-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">現在の年齢</label>
<input type="range" id="age" min="20" max="64" step="1" value="35" oninput="nenkinCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>20歳</span><span id="ageVal" style="font-weight:bold;font-size:18px;color:#2563eb;">35歳</span><span>64歳</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">平均年収（額面・万円）</label>
<input type="range" id="income" min="200" max="1500" step="10" value="500" oninput="nenkinCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>200万円</span><span id="incomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">500万円</span><span>1,500万円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">厚生年金の加入期間（年）</label>
<input type="range" id="kousei" min="0" max="44" step="1" value="38" oninput="nenkinCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0年</span><span id="kouseiVal" style="font-weight:bold;font-size:18px;color:#2563eb;">38年</span><span>44年</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">国民年金の加入期間（年）※厚生年金期間含む</label>
<input type="range" id="kokumin" min="0" max="40" step="1" value="40" oninput="nenkinCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0年</span><span id="kokuminVal" style="font-weight:bold;font-size:18px;color:#2563eb;">40年</span><span>40年</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">65歳からの年金受給額（年額）</div>
<div id="totalNenkin" style="font-size:36px;font-weight:bold;">1,844,800円</div>
<div style="font-size:14px;margin-top:4px;">月額: <span id="monthlyNenkin" style="font-weight:bold;">153,733円</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">老齢基礎年金（年額）</div>
<div id="kisonen" style="font-size:16px;font-weight:bold;color:#0369a1;">816,000円</div>
<div style="font-size:11px;color:#64748b;">月額 <span id="kisoMonth">68,000</span>円</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">老齢厚生年金（年額）</div>
<div id="kouseinen" style="font-size:16px;font-weight:bold;color:#15803d;">1,028,800円</div>
<div style="font-size:11px;color:#64748b;">月額 <span id="kouseiMonth">85,733</span>円</div>
</div>
</div>

<!-- 繰上げ・繰下げ比較 -->
<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:14px;margin-bottom:8px;">受給開始年齢別の年金額</div>
<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;">
<div style="background:#fee2e2;border-radius:8px;padding:10px;text-align:center;">
<div style="font-size:12px;color:#dc2626;font-weight:bold;">60歳（繰上げ）</div>
<div id="age60" style="font-size:14px;font-weight:bold;">月額 107,613円</div>
<div style="font-size:11px;color:#dc2626;">-30%</div>
</div>
<div style="background:#e0f2fe;border-radius:8px;padding:10px;text-align:center;">
<div style="font-size:12px;color:#2563eb;font-weight:bold;">65歳（通常）</div>
<div id="age65" style="font-size:14px;font-weight:bold;">月額 153,733円</div>
<div style="font-size:11px;color:#2563eb;">基準</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:10px;text-align:center;">
<div style="font-size:12px;color:#15803d;font-weight:bold;">70歳（繰下げ）</div>
<div id="age70" style="font-size:14px;font-weight:bold;">月額 218,302円</div>
<div style="font-size:11px;color:#15803d;">+42%</div>
</div>
</div>
</div>

<div style="background:#fef9c3;border-radius:8px;padding:12px;text-align:center;margin-bottom:16px;">
<div style="font-size:12px;color:#92400e;">年金だけでは不足する月額（ゆとりある老後に月35万円必要とした場合）</div>
<div id="shortage" style="font-size:20px;font-weight:bold;color:#dc2626;">月額 196,267円 不足</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>計算条件:</strong> 老齢基礎年金は2026年度満額816,000円/年（40年加入時）で按分。老齢厚生年金は平均標準報酬額×5.481/1000×加入月数で概算。繰上げは1月あたり0.5%減額、繰下げは1月あたり0.7%増額。実際の受給額は加入履歴・報酬月額により異なります。
</div>

</div>

<script>
function nenkinCalc(){
  var age=parseInt(document.getElementById('age').value);
  var income=parseInt(document.getElementById('income').value)*10000;
  var kouseiYears=parseInt(document.getElementById('kousei').value);
  var kokuminYears=parseInt(document.getElementById('kokumin').value);

  // 老齢基礎年金（2026年度満額 816,000円/年、40年加入で満額）
  var kisoFull=816000;
  var kisoNenkin=Math.round(kisoFull*(Math.min(kokuminYears,40)/40));

  // 老齢厚生年金
  // 平均標準報酬額（上限あり: 65万円/月 = 780万円/年）
  var avgMonthly=Math.min(income/12,650000);
  // 厚生年金計算: 平均標準報酬額 × 5.481/1000 × 加入月数
  var kouseiNenkin=Math.round(avgMonthly*5.481/1000*kouseiYears*12);

  var totalNenkin=kisoNenkin+kouseiNenkin;
  var monthlyTotal=Math.round(totalNenkin/12);

  // 繰上げ（60歳: -0.5%×60ヶ月=-30%）
  var age60=Math.round(monthlyTotal*0.70);
  // 繰下げ（70歳: +0.7%×60ヶ月=+42%）
  var age70=Math.round(monthlyTotal*1.42);

  // 不足額（ゆとりある老後: 月35万円）
  var shortage=350000-monthlyTotal;

  // Update display
  document.getElementById('ageVal').textContent=age+'歳';
  document.getElementById('incomeVal').textContent=(income/10000).toLocaleString()+'万円';
  document.getElementById('kouseiVal').textContent=kouseiYears+'年';
  document.getElementById('kokuminVal').textContent=kokuminYears+'年';

  document.getElementById('totalNenkin').textContent=totalNenkin.toLocaleString()+'円';
  document.getElementById('monthlyNenkin').textContent=monthlyTotal.toLocaleString()+'円';
  document.getElementById('kisonen').textContent=kisoNenkin.toLocaleString()+'円';
  document.getElementById('kisoMonth').textContent=Math.round(kisoNenkin/12).toLocaleString();
  document.getElementById('kouseinen').textContent=kouseiNenkin.toLocaleString()+'円';
  document.getElementById('kouseiMonth').textContent=Math.round(kouseiNenkin/12).toLocaleString();

  document.getElementById('age60').textContent='月額 '+age60.toLocaleString()+'円';
  document.getElementById('age65').textContent='月額 '+monthlyTotal.toLocaleString()+'円';
  document.getElementById('age70').textContent='月額 '+age70.toLocaleString()+'円';

  if(shortage>0){
    document.getElementById('shortage').textContent='月額 '+shortage.toLocaleString()+'円 不足';
    document.getElementById('shortage').style.color='#dc2626';
  } else {
    document.getElementById('shortage').textContent='年金のみで月35万円を達成！';
    document.getElementById('shortage').style.color='#15803d';
  }
}
nenkinCalc();
</script>

---

## 年金の不足分を補う方法

シミュレーション結果を見て、「年金だけでは足りない」と感じた方へ。不足分を補うための3つの方法を紹介します。

### 1. iDeCo（個人型確定拠出年金）で老後資金を増やす

iDeCoの掛金は**全額所得控除**。年収500万円で月2.3万円拠出すると、年間約5.5万円の節税効果。運用益も非課税です。

→ [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/) で節税額を計算
→ [iDeCoおすすめ証券会社の選び方](/ja/posts/ideco-osusume-shouken/)

### 2. つみたてNISAで資産を育てる

毎月3万円を年利5%で20年間積み立てると、約**1,233万円**に。NISAなら運用益が非課税です。

→ [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) で将来の資産額を計算

### 3. 副業で収入を増やす

副業の収入を投資に回せば、老後資金を大幅に増やせます。まずは月5万円の副業収入を目指しましょう。

→ [副業の税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/) で手取りを確認
→ [freeeで確定申告を簡単に](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

---

## 年金の基礎知識

### 老齢基礎年金

- 対象: 国民年金に加入した全員（20〜60歳の40年間）
- 満額: 年816,000円（2026年度）= **月68,000円**
- 加入期間が40年未満なら、その分減額

### 老齢厚生年金

- 対象: 会社員・公務員（厚生年金加入者）
- 計算式: 平均標準報酬額 × 5.481/1000 × 加入月数
- 年収が高いほど、加入期間が長いほど多くなる

### 繰上げ・繰下げ受給

| 受給開始 | 増減率 | 65歳で月15万円の場合 |
|---------|--------|-------------------|
| 60歳 | -30%（0.5%×60月） | 月105,000円 |
| 63歳 | -14.4% | 月128,400円 |
| 65歳 | 基準 | 月150,000円 |
| 68歳 | +25.2% | 月187,800円 |
| 70歳 | +42% | 月213,000円 |
| 75歳 | +84% | 月276,000円 |

---

## よくある質問

**Q. 年金は何歳からもらえますか？**
原則65歳から。繰上げ受給で最短60歳から（減額あり）、繰下げで最長75歳まで遅らせる（増額あり）ことができます。

**Q. 年金だけで生活できますか？**
生命保険文化センターの調査では「ゆとりある老後生活費」は月約35万円。平均的な年金受給額は月約15万円なので、月20万円の不足が生じます。

**Q. フリーランスの年金はどうなりますか？**
フリーランスは国民年金のみで、老齢基礎年金（満額で月68,000円）しか受給できません。iDeCoや国民年金基金での上乗せが必須です。

---

## 関連ツール・記事

- [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/) — iDeCoの節税額と将来受取額を計算
- [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) — 資産運用で老後資金を増やす
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 現在の手取り額を確認
- [家計簿シミュレーター](/ja/tools/kakeibo-generator/) — 月々の貯蓄額を最適化
- [FX利益計算シミュレーター](/ja/tools/fx-profit-calculator/) — 投資の損益を計算
- [副業の税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/) — 副業収入の税金を確認
