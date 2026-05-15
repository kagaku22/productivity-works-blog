---
title: "iDeCoシミュレーター｜節税額・将来資産を自動計算【2026年版】"
date: 2026-05-14
draft: false
slug: "ideco-simulator"
description: "iDeCo（個人型確定拠出年金）の節税額と将来の受取額を自動計算。年収・掛金・運用利回りを入力するだけ。所得税・住民税の節税効果が一目でわかる無料ツール。"
author: "Productivity Works編集部"
categories:
  - "マネー・個人金融"
tags:
  - "iDeCo"
  - "節税"
  - "年金"
  - "計算ツール"
  - "資産運用"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/ideco-simulator.png"
  alt: "iDeCoシミュレーター｜節税額・将来資産を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# iDeCo節税シミュレーター【2026年版】

年収・職業・毎月の掛金を入力するだけで、**節税額**と**将来の受取額**を自動計算します。

<div id="ideco-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">年収（額面・万円）</label>
<input type="range" id="income" min="200" max="1500" step="10" value="500" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>200万円</span><span id="incomeVal" style="font-weight:bold;font-size:18px;color:#2563eb;">500万円</span><span>1,500万円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">職業（掛金上限が変わります）</label>
<select id="jobType" onchange="calcIdeco()" style="width:100%;padding:8px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="employee">会社員（企業年金なし）— 上限23,000円/月</option>
<option value="employee_dc">会社員（企業型DCあり）— 上限20,000円/月</option>
<option value="employee_db">会社員（DB・厚生年金基金あり）— 上限12,000円/月</option>
<option value="civil">公務員 — 上限12,000円/月</option>
<option value="self">自営業・フリーランス — 上限68,000円/月</option>
<option value="homemaker">専業主婦(夫) — 上限23,000円/月</option>
</select>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">毎月の掛金（円）</label>
<input type="range" id="contribution" min="5000" max="68000" step="1000" value="23000" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>5,000円</span><span id="contribVal" style="font-weight:bold;font-size:18px;color:#2563eb;">23,000円</span><span id="contribMax">68,000円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">想定年利回り（%）</label>
<input type="range" id="rate" min="1" max="8" step="0.5" value="4" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1%</span><span id="rateVal" style="font-weight:bold;font-size:18px;color:#2563eb;">4.0%</span><span>8%</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">運用年数（60歳まで）</label>
<input type="range" id="years" min="1" max="35" step="1" value="25" oninput="calcIdeco()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1年</span><span id="yearsVal" style="font-weight:bold;font-size:18px;color:#2563eb;">25年</span><span>35年</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">60歳時点の受取額（税引前）</div>
<div id="totalAsset" style="font-size:36px;font-weight:bold;">11,896,000円</div>
<div style="font-size:13px;margin-top:4px;">うち運用益: <span id="profitAmt" style="font-weight:bold;">4,996,000円</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
<div style="background:#dcfce7;border-radius:8px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#64748b;">年間の節税額</div>
<div id="taxSaveYear" style="font-size:22px;font-weight:bold;color:#15803d;">55,200円</div>
</div>
<div style="background:#fef9c3;border-radius:8px;padding:16px;text-align:center;">
<div style="font-size:12px;color:#64748b;">累計の節税額</div>
<div id="taxSaveTotal" style="font-size:22px;font-weight:bold;color:#a16207;">1,380,000円</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">掛金合計（元本）</div>
<div id="principal" style="font-size:16px;font-weight:bold;color:#0369a1;">6,900,000円</div>
</div>
<div style="background:#f3e8ff;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">節税込み実質リターン</div>
<div id="realReturn" style="font-size:16px;font-weight:bold;color:#7c3aed;">+78.2%</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>計算条件:</strong> 給与所得控除・基礎控除・社会保険料控除（14.7%概算）を適用した簡易計算です。実際の節税額は個人の状況により異なります。iDeCoの掛金は全額所得控除の対象です。
</div>

</div>

<script>
function calcIdeco(){
  var inc=parseInt(document.getElementById('income').value);
  var job=document.getElementById('jobType').value;
  var contrib=parseInt(document.getElementById('contribution').value);
  var r=parseFloat(document.getElementById('rate').value)/100;
  var y=parseInt(document.getElementById('years').value);

  // 職業別の掛金上限
  var maxContrib;
  if(job==='self') maxContrib=68000;
  else if(job==='employee') maxContrib=23000;
  else if(job==='employee_dc') maxContrib=20000;
  else if(job==='employee_db'||job==='civil') maxContrib=12000;
  else maxContrib=23000; // homemaker

  // 掛金を上限に制限
  if(contrib>maxContrib) contrib=maxContrib;
  var slider=document.getElementById('contribution');
  slider.max=maxContrib;
  if(parseInt(slider.value)>maxContrib) slider.value=maxContrib;

  var annual=inc*10000;
  var annualContrib=contrib*12;

  // 給与所得控除
  var deduction;
  if(annual<=1625000) deduction=550000;
  else if(annual<=1800000) deduction=annual*0.4-100000;
  else if(annual<=3600000) deduction=annual*0.3+80000;
  else if(annual<=6600000) deduction=annual*0.2+440000;
  else if(annual<=8500000) deduction=annual*0.1+1100000;
  else deduction=1950000;

  // 自営業の場合は給与所得控除なし
  if(job==='self') deduction=0;

  var shotoku=annual-deduction;

  // 基礎控除48万 + 社会保険料（14.7%概算）
  var socialIns=Math.floor(annual*0.147);
  if(job==='self') socialIns=Math.floor(annual*0.10); // 国保は低め
  var basicDeduction=480000;
  var totalDeduction=basicDeduction+socialIns;

  // iDeCoなしの課税所得
  var taxableWithout=Math.max(shotoku-totalDeduction,0);
  // iDeCoありの課税所得
  var taxableWith=Math.max(shotoku-totalDeduction-annualContrib,0);

  // 所得税率を求める
  function getIncomeTax(taxable){
    if(taxable<=1950000) return taxable*0.05;
    else if(taxable<=3300000) return taxable*0.1-97500;
    else if(taxable<=6950000) return taxable*0.2-427500;
    else if(taxable<=9000000) return taxable*0.23-636000;
    else if(taxable<=18000000) return taxable*0.33-1536000;
    else if(taxable<=40000000) return taxable*0.40-2796000;
    else return taxable*0.45-4796000;
  }

  var taxWithout=Math.floor(getIncomeTax(taxableWithout)*1.021)+Math.floor(taxableWithout*0.1)+5000;
  var taxWith=Math.floor(getIncomeTax(taxableWith)*1.021)+Math.floor(taxableWith*0.1)+5000;

  var taxSaveYear=Math.max(taxWithout-taxWith,0);
  var taxSaveTotal=taxSaveYear*y;

  // 将来の資産額
  var mr=r/12;
  var n=y*12;
  var fv=contrib*((Math.pow(1+mr,n)-1)/mr);
  var p=contrib*n;
  var profit=fv-p;

  // 節税込み実質リターン
  var realRet=((fv+taxSaveTotal-p)/p*100);

  document.getElementById('incomeVal').textContent=inc.toLocaleString()+'万円';
  document.getElementById('contribVal').textContent=contrib.toLocaleString()+'円';
  document.getElementById('contribMax').textContent=maxContrib.toLocaleString()+'円';
  document.getElementById('rateVal').textContent=(r*100).toFixed(1)+'%';
  document.getElementById('yearsVal').textContent=y+'年';
  document.getElementById('totalAsset').textContent=Math.floor(fv).toLocaleString()+'円';
  document.getElementById('profitAmt').textContent=Math.floor(profit).toLocaleString()+'円';
  document.getElementById('taxSaveYear').textContent=taxSaveYear.toLocaleString()+'円';
  document.getElementById('taxSaveTotal').textContent=taxSaveTotal.toLocaleString()+'円';
  document.getElementById('principal').textContent=p.toLocaleString()+'円';
  document.getElementById('realReturn').textContent='+'+realRet.toFixed(1)+'%';
}
calcIdeco();
</script>

---

## iDeCoの3つの節税メリット

iDeCoは**3段階**で節税できる、最強の節税制度です。

| タイミング | 節税内容 | 効果 |
|-----------|---------|------|
| 掛金拠出時 | 全額所得控除 | 所得税・住民税が毎年減る |
| 運用中 | 運用益が非課税 | 通常20.315%の税金がゼロ |
| 受取時 | 退職所得控除・公的年金等控除 | 一時金 or 年金で受取時も優遇 |

---

## iDeCoを始める手順

1. **証券口座を選ぶ** — 手数料と商品ラインナップで選ぶのがポイント
2. **掛金を決める** — 上限額は職業で異なる（上のシミュレーターで確認）
3. **運用商品を選ぶ** — インデックスファンドが初心者にはおすすめ
4. **毎月自動引き落とし** — 一度設定すれば放置でOK

**おすすめの証券会社:** [楽天証券でiDeCo口座を開設する]()（手数料最安水準、商品数豊富）

---

## 年収別の節税効果まとめ

| 年収 | 掛金（会社員） | 年間節税額 | 30年累計節税 |
|------|-------------|-----------|------------|
| 300万円 | 23,000円/月 | 約41,400円 | 約124万円 |
| 500万円 | 23,000円/月 | 約55,200円 | 約166万円 |
| 700万円 | 23,000円/月 | 約55,200円 | 約166万円 |
| 1,000万円 | 23,000円/月 | 約82,800円 | 約248万円 |

※会社員（企業年金なし）、独身・扶養なしの概算

---

## よくある質問

**Q. iDeCoとNISA、どちらを先に始めるべき？**
一般的にはNISAが先。iDeCoは60歳まで引き出せないため、まずはNISAで流動性を確保してからiDeCoを追加するのがおすすめです。 → [NISAとiDeCo、どっちを先に？](/ja/posts/nisa-ideco-docchi-saki/)

**Q. 自営業者はiDeCoの掛金が多いのはなぜ？**
自営業者は厚生年金がないため、老後の備えが少なくなります。その分、iDeCoの掛金上限が月68,000円（年81.6万円）と高く設定されています。

**Q. 途中で掛金を変更できますか？**
はい、年1回変更できます。掛金を0円にして運用のみ継続する「運用指図者」になることも可能です。

**Q. 受取時に税金はかかりますか？**
一時金で受け取る場合は退職所得控除、年金で受け取る場合は公的年金等控除が適用されます。全額課税されるわけではありません。

---

## おすすめサービス

iDeCoの節税効果がわかったら、次のアクションに進みましょう。

- **iDeCo口座を開設する** → [楽天証券]()なら手数料最安水準＆商品数豊富
- **NISAも併用する** → [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/)でNISA分の資産額も計算
- **老後資金の全体像を確認** → [年金シミュレーター](/ja/tools/nenkin-simulator/)で将来の年金受給額をチェック
- **確定申告を楽にする** → [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)なら控除申請も自動化

---

## 関連ツール・記事

- [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) — 将来の資産額を計算
- [年金シミュレーター](/ja/tools/nenkin-simulator/) — 将来の年金受給額を確認
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 年収から手取りを計算
- [家計簿シミュレーター](/ja/tools/kakeibo-generator/) — 理想の支出配分を計算
- [副業の税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/) — 副業収入の税金を確認
- [NISAとiDeCo、どっちを先に？](/ja/posts/nisa-ideco-docchi-saki/)
- [iDeCoおすすめ証券会社](/ja/posts/ideco-osusume-shouken/)
