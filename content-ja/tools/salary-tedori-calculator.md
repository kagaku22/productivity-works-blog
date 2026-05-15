---
title: "手取り計算シミュレーター｜年収から手取りを自動計算【2026年版】"
date: 2026-05-14
draft: false
slug: "salary-tedori-calculator"
description: "年収・月収から手取り額を自動計算。所得税・住民税・社会保険料の内訳も表示。転職・副業の年収比較に便利な無料ツール。"
author: "Productivity Works編集部"
categories:
  - "マネー・個人金融"
tags:
  - "手取り"
  - "年収"
  - "計算ツール"
  - "税金"
  - "社会保険料"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/salary-tedori-calculator.png"
  alt: "手取り計算シミュレーター｜年収から手取りを自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 手取り計算シミュレーター【2026年版】

年収（額面）を入力するだけで、**手取り額**・**税金**・**社会保険料**の内訳を自動計算します。

<div id="tedori-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">年収（額面・万円）</label>
<input type="range" id="income" min="200" max="2000" step="10" value="500" oninput="calcTedori()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>200万円</span><span id="incomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">500万円</span><span>2,000万円</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">扶養人数</label>
<select id="dependents" onchange="calcTedori()" style="width:100%;padding:8px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="0">0人（独身・扶養なし）</option>
<option value="1">1人</option>
<option value="2">2人</option>
<option value="3">3人</option>
</select>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">年間手取り額（概算）</div>
<div id="tedoriYear" style="font-size:36px;font-weight:bold;">3,940,000円</div>
<div style="font-size:14px;margin-top:8px;">月額手取り: <span id="tedoriMonth" style="font-weight:bold;">328,333円</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#fee2e2;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">所得税（年額）</div>
<div id="incomeTax" style="font-size:16px;font-weight:bold;color:#dc2626;">139,500円</div>
</div>
<div style="background:#fef3c7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">住民税（年額）</div>
<div id="residentTax" style="font-size:16px;font-weight:bold;color:#d97706;">247,000円</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">社会保険料（年額）</div>
<div id="socialIns" style="font-size:16px;font-weight:bold;color:#0369a1;">735,000円</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">手取り率</div>
<div id="tedoriRate" style="font-size:16px;font-weight:bold;color:#15803d;">78.8%</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>計算条件:</strong> 会社員（給与所得者）、40歳未満、東京都在住を想定した概算値です。実際の金額は勤務先・居住地・年齢により異なります。
</div>

</div>

<script>
function calcTedori(){
  var inc=parseInt(document.getElementById('income').value);
  var dep=parseInt(document.getElementById('dependents').value);
  var annual=inc*10000;

  // 給与所得控除
  var deduction;
  if(annual<=1625000) deduction=550000;
  else if(annual<=1800000) deduction=annual*0.4-100000;
  else if(annual<=3600000) deduction=annual*0.3+80000;
  else if(annual<=6600000) deduction=annual*0.2+440000;
  else if(annual<=8500000) deduction=annual*0.1+1100000;
  else deduction=1950000;

  // 所得
  var shotoku=annual-deduction;

  // 基礎控除48万 + 社会保険料控除（概算15%）+ 扶養控除
  var socialRate=0.147;
  var socialIns=Math.floor(annual*socialRate);
  var basicDeduction=480000;
  var dependentDeduction=dep*380000;
  var totalDeduction=basicDeduction+socialIns+dependentDeduction;

  // 課税所得
  var taxable=Math.max(shotoku-totalDeduction,0);

  // 所得税（累進課税）
  var incomeTax;
  if(taxable<=1950000) incomeTax=taxable*0.05;
  else if(taxable<=3300000) incomeTax=taxable*0.1-97500;
  else if(taxable<=6950000) incomeTax=taxable*0.2-427500;
  else if(taxable<=9000000) incomeTax=taxable*0.23-636000;
  else if(taxable<=18000000) incomeTax=taxable*0.33-1536000;
  else if(taxable<=40000000) incomeTax=taxable*0.40-2796000;
  else incomeTax=taxable*0.45-4796000;
  incomeTax=Math.floor(incomeTax*1.021); // 復興特別所得税

  // 住民税（課税所得×10%+均等割5000円）
  var residentTax=Math.floor(taxable*0.1)+5000;

  // 手取り
  var tedori=annual-incomeTax-residentTax-socialIns;
  var tedoriMonthly=Math.floor(tedori/12);
  var rate=(tedori/annual*100).toFixed(1);

  document.getElementById('incomeVal').textContent=inc.toLocaleString()+'万円';
  document.getElementById('tedoriYear').textContent=tedori.toLocaleString()+'円';
  document.getElementById('tedoriMonth').textContent=tedoriMonthly.toLocaleString()+'円';
  document.getElementById('incomeTax').textContent=incomeTax.toLocaleString()+'円';
  document.getElementById('residentTax').textContent=residentTax.toLocaleString()+'円';
  document.getElementById('socialIns').textContent=socialIns.toLocaleString()+'円';
  document.getElementById('tedoriRate').textContent=rate+'%';
}
calcTedori();
</script>

---

## 年収別の手取り目安表

| 年収（額面） | 手取り（概算） | 手取り率 |
|------------|------------|---------|
| 300万円 | 約240万円 | 約80% |
| 400万円 | 約315万円 | 約79% |
| 500万円 | 約394万円 | 約79% |
| 600万円 | 約467万円 | 約78% |
| 700万円 | 約535万円 | 約76% |
| 800万円 | 約600万円 | 約75% |
| 1,000万円 | 約722万円 | 約72% |
| 1,500万円 | 約1,020万円 | 約68% |

※独身・扶養なし・40歳未満の概算値

---

## 手取りを増やす方法

手取りを増やすには、**収入を上げる**か**控除を増やす**のが基本です。

- **iDeCoで節税** → 掛金が全額所得控除。会社員なら月23,000円で年間約55,000円の節税効果 → [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/)で節税額を計算
- **ふるさと納税** → 実質2,000円で返礼品がもらえる節税制度
- **副業で収入UP** → 副業収入は給与所得とは別計算 → [副業の始め方ガイド](/ja/posts/副業-始め方-初心者-2026/)
- **転職で年収UP** → 年収交渉のコツを知る → [転職サイトおすすめ](/ja/posts/tenshoku-site-osusume-2026/)

---

## よくある質問

**Q. ボーナスは含まれていますか？**
年収（額面）にボーナスを含めた金額を入力してください。計算結果はボーナス込みの年間手取りになります。

**Q. 40歳以上の場合は？**
40歳以上は介護保険料（約0.8%）が追加されるため、手取りがやや減少します。上記の計算は40歳未満を前提としています。

**Q. 副業収入がある場合は？**
副業所得は別途確定申告が必要です → [副業の確定申告やり方](/ja/posts/fukugyou-kakuteishinkoku-yarikata-2026/)

---

## おすすめサービス

手取り額がわかったら、次のアクションに進みましょう。

- **貯蓄を投資で増やす** → 毎月3万円を年利5%で20年運用すると約1,233万円に。[つみたてNISAシミュレーター](/ja/tools/nisa-simulator/)で将来の資産額を計算
- **老後資金を確認する** → 年金だけで足りる？[年金シミュレーター](/ja/tools/nenkin-simulator/)で将来の受給額をチェック
- **確定申告を楽にする** → [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)なら銀行口座と自動連携で記帳が自動化
- **家計を最適化する** → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)で理想の支出配分を計算

---

## 関連ツール・記事

- [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/) — iDeCoの節税額と将来受取額を計算
- [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) — 将来の資産額を計算
- [年金シミュレーター](/ja/tools/nenkin-simulator/) — 将来の年金受給額を確認
- [家計簿シミュレーター](/ja/tools/kakeibo-generator/) — 理想の支出配分を計算
- [副業の税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/) — 副業収入の税金を確認
- [FX利益計算シミュレーター](/ja/tools/fx-profit-calculator/) — 投資の損益を計算
- [フリーランス確定申告ガイド](/ja/posts/フリーランス-確定申告-やり方/)
- [会計ソフトおすすめ比較](/ja/posts/kaikei-soft-osusume-2026/)
