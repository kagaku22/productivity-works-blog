---
title: "年金シミュレーター｜将来の受給額を簡単計算"
date: 2026-05-15
draft: false
slug: "nenkin-simulator"
description: "現在の年収と加入期間から、将来受け取れる老齢基礎年金・厚生年金の月額・年額を簡単シミュレーション。繰上げ・繰下げ受給の影響も一目でわかります。"
categories: ["無料ツール"]
tags: ["年金", "シミュレーター", "老後資金", "厚生年金", "国民年金"]
author: "Productivity Works編集部"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/nenkin-simulator.png"
  alt: "年金シミュレーター"
  relative: true
---

※本ページにはアフィリエイト広告が含まれています。

<style>
.nenkin-wrap {
  max-width: 680px;
  margin: 0 auto;
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", sans-serif;
}
.nenkin-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.06);
}
.nenkin-card h2 {
  font-size: 16px;
  font-weight: 700;
  color: #1e293b;
  margin: 0 0 20px 0;
  padding-bottom: 10px;
  border-bottom: 2px solid #4a9eff;
}
.input-group {
  margin-bottom: 22px;
}
.input-label {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 8px;
}
.input-label span:first-child {
  font-size: 14px;
  font-weight: 600;
  color: #334155;
}
.input-value {
  font-size: 20px;
  font-weight: 700;
  color: #4a9eff;
}
.slider-wrap {
  position: relative;
}
input[type="range"] {
  -webkit-appearance: none;
  width: 100%;
  height: 6px;
  border-radius: 3px;
  background: #e2e8f0;
  outline: none;
  cursor: pointer;
}
input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #4a9eff;
  box-shadow: 0 2px 6px rgba(74,158,255,0.4);
  cursor: pointer;
}
input[type="range"]::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #4a9eff;
  box-shadow: 0 2px 6px rgba(74,158,255,0.4);
  cursor: pointer;
  border: none;
}
.slider-limits {
  display: flex;
  justify-content: space-between;
  font-size: 11px;
  color: #94a3b8;
  margin-top: 4px;
}
select.nenkin-select {
  width: 100%;
  padding: 10px 14px;
  font-size: 16px;
  font-weight: 600;
  color: #1e293b;
  background: #f8fafc;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  cursor: pointer;
  outline: none;
}
select.nenkin-select:focus {
  border-color: #4a9eff;
  box-shadow: 0 0 0 3px rgba(74,158,255,0.15);
}
.result-hero {
  background: linear-gradient(135deg, #2563eb 0%, #4a9eff 100%);
  border-radius: 12px;
  padding: 28px 24px;
  text-align: center;
  color: #fff;
  margin-bottom: 16px;
}
.result-hero .hero-label {
  font-size: 14px;
  opacity: 0.88;
  margin-bottom: 6px;
}
.result-hero .hero-monthly {
  font-size: 44px;
  font-weight: 800;
  letter-spacing: -1px;
  line-height: 1;
}
.result-hero .hero-unit {
  font-size: 18px;
  font-weight: 400;
  margin-left: 4px;
}
.result-hero .hero-annual {
  font-size: 15px;
  opacity: 0.88;
  margin-top: 8px;
}
.result-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 16px;
}
.result-sub {
  border-radius: 10px;
  padding: 16px;
  text-align: center;
}
.result-sub.kiso {
  background: #eff6ff;
  border: 1px solid #bfdbfe;
}
.result-sub.kousei {
  background: #f0fdf4;
  border: 1px solid #bbf7d0;
}
.result-sub .sub-label {
  font-size: 12px;
  color: #64748b;
  margin-bottom: 6px;
}
.result-sub .sub-annual {
  font-size: 18px;
  font-weight: 700;
}
.result-sub.kiso .sub-annual { color: #1d4ed8; }
.result-sub.kousei .sub-annual { color: #15803d; }
.result-sub .sub-monthly {
  font-size: 12px;
  color: #64748b;
  margin-top: 4px;
}
.adjust-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 16px;
}
.adjust-card .adj-title {
  font-size: 13px;
  font-weight: 700;
  color: #475569;
  margin-bottom: 12px;
}
.adj-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
  border-bottom: 1px solid #e2e8f0;
  font-size: 14px;
}
.adj-row:last-child { border-bottom: none; }
.adj-row .adj-age { color: #475569; font-weight: 600; }
.adj-row .adj-amount { font-weight: 700; }
.adj-row .adj-rate {
  font-size: 12px;
  padding: 2px 8px;
  border-radius: 20px;
  font-weight: 600;
}
.rate-down { background: #fee2e2; color: #dc2626; }
.rate-base { background: #dbeafe; color: #2563eb; }
.rate-up { background: #dcfce7; color: #16a34a; }
.adj-row.selected { background: #eff6ff; border-radius: 6px; padding: 8px 6px; margin: 0 -6px; }
.compare-box {
  background: #fff7ed;
  border: 1.5px solid #fed7aa;
  border-radius: 10px;
  padding: 14px 16px;
  margin-bottom: 16px;
  text-align: center;
}
.compare-box .cmp-label { font-size: 12px; color: #92400e; margin-bottom: 4px; }
.compare-box .cmp-value { font-size: 18px; font-weight: 700; }
.cmp-plus { color: #16a34a; }
.cmp-minus { color: #dc2626; }
.cmp-zero { color: #2563eb; }
.notice-box {
  background: #f1f5f9;
  border-radius: 8px;
  padding: 12px 14px;
  font-size: 12px;
  color: #64748b;
  line-height: 1.7;
}
.affiliate-section {
  margin-top: 32px;
  padding-top: 24px;
  border-top: 1px solid #e2e8f0;
}
.affiliate-section h3 {
  font-size: 15px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 14px;
}
.aff-btn {
  display: block;
  background: linear-gradient(135deg, #4a9eff, #2563eb);
  color: #fff !important;
  text-decoration: none !important;
  text-align: center;
  padding: 14px 20px;
  border-radius: 8px;
  font-weight: 700;
  font-size: 15px;
  margin-bottom: 10px;
  transition: opacity 0.2s;
}
.aff-btn:hover { opacity: 0.88; }
.aff-btn-sub {
  display: block;
  background: #fff;
  color: #2563eb !important;
  text-decoration: none !important;
  text-align: center;
  padding: 12px 20px;
  border-radius: 8px;
  font-weight: 700;
  font-size: 14px;
  border: 1.5px solid #4a9eff;
  margin-bottom: 10px;
  transition: background 0.2s;
}
.aff-btn-sub:hover { background: #eff6ff; }
.related-tools {
  margin-top: 32px;
}
.related-tools h3 {
  font-size: 15px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 12px;
}
.tool-links {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}
.tool-link {
  display: block;
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  padding: 12px 14px;
  text-decoration: none !important;
  color: #1e293b !important;
  font-size: 13px;
  font-weight: 600;
  transition: border-color 0.2s, background 0.2s;
}
.tool-link:hover {
  border-color: #4a9eff;
  background: #eff6ff;
  color: #2563eb !important;
}
@media (max-width: 480px) {
  .result-grid { grid-template-columns: 1fr; }
  .tool-links { grid-template-columns: 1fr; }
  .result-hero .hero-monthly { font-size: 36px; }
}
</style>

<div class="nenkin-wrap">

<div class="nenkin-card">
<h2>入力項目</h2>

<div class="input-group">
  <div class="input-label">
    <span>現在の年齢</span>
    <span class="input-value"><span id="v-age">30</span>歳</span>
  </div>
  <input type="range" id="s-age" min="20" max="64" step="1" value="30" oninput="nenkinCalc()">
  <div class="slider-limits"><span>20歳</span><span>64歳</span></div>
</div>

<div class="input-group">
  <div class="input-label">
    <span>年収（万円）</span>
    <span class="input-value"><span id="v-income">400</span>万円</span>
  </div>
  <input type="range" id="s-income" min="100" max="2000" step="10" value="400" oninput="nenkinCalc()">
  <div class="slider-limits"><span>100万円</span><span>2,000万円</span></div>
</div>

<div class="input-group">
  <div class="input-label">
    <span>国民年金加入期間（年）</span>
    <span class="input-value"><span id="v-kokumin">40</span>年</span>
  </div>
  <input type="range" id="s-kokumin" min="0" max="40" step="1" value="40" oninput="nenkinCalc()">
  <div class="slider-limits"><span>0年</span><span>40年</span></div>
</div>

<div class="input-group">
  <div class="input-label">
    <span>厚生年金加入期間（年）</span>
    <span class="input-value"><span id="v-kousei">38</span>年</span>
  </div>
  <input type="range" id="s-kousei" min="0" max="40" step="1" value="38" oninput="nenkinCalc()">
  <div class="slider-limits"><span>0年</span><span>40年</span></div>
</div>

<div class="input-group" style="margin-bottom:0;">
  <div class="input-label" style="margin-bottom:8px;">
    <span>受給開始年齢</span>
  </div>
  <select id="s-start" class="nenkin-select" onchange="nenkinCalc()">
    <option value="60">60歳（繰上げ受給）</option>
    <option value="61">61歳（繰上げ受給）</option>
    <option value="62">62歳（繰上げ受給）</option>
    <option value="63">63歳（繰上げ受給）</option>
    <option value="64">64歳（繰上げ受給）</option>
    <option value="65" selected>65歳（通常受給）</option>
    <option value="66">66歳（繰下げ受給）</option>
    <option value="67">67歳（繰下げ受給）</option>
    <option value="68">68歳（繰下げ受給）</option>
    <option value="69">69歳（繰下げ受給）</option>
    <option value="70">70歳（繰下げ受給）</option>
    <option value="75">75歳（繰下げ受給）</option>
  </select>
</div>

</div><!-- .nenkin-card -->

<div id="result-area">

<div class="result-hero">
  <div class="hero-label">月額受給見込み</div>
  <div class="hero-monthly"><span id="r-monthly">---</span><span class="hero-unit">円</span></div>
  <div class="hero-annual">年額：<span id="r-annual">---</span>円</div>
</div>

<div class="result-grid">
  <div class="result-sub kiso">
    <div class="sub-label">老齢基礎年金</div>
    <div class="sub-annual"><span id="r-kiso-annual">---</span>円／年</div>
    <div class="sub-monthly">月額 <span id="r-kiso-monthly">---</span>円</div>
  </div>
  <div class="result-sub kousei">
    <div class="sub-label">老齢厚生年金</div>
    <div class="sub-annual"><span id="r-kousei-annual">---</span>円／年</div>
    <div class="sub-monthly">月額 <span id="r-kousei-monthly">---</span>円</div>
  </div>
</div>

<div class="compare-box">
  <div class="cmp-label">65歳受給（基準）と比較した増減</div>
  <div class="cmp-value" id="r-diff-rate">---</div>
  <div style="font-size:12px;color:#92400e;margin-top:4px;">月額 <span id="r-diff-amount">---</span>円の<span id="r-diff-sign">---</span></div>
</div>

<div class="adjust-card">
  <div class="adj-title">受給開始年齢別の月額一覧（65歳基準で比較）</div>
  <div class="adj-row" id="row-60">
    <span class="adj-age">60歳</span>
    <span class="adj-amount" id="t-60">---円</span>
    <span class="adj-rate rate-down">-24.0%</span>
  </div>
  <div class="adj-row" id="row-65">
    <span class="adj-age">65歳（基準）</span>
    <span class="adj-amount" id="t-65">---円</span>
    <span class="adj-rate rate-base">±0%</span>
  </div>
  <div class="adj-row" id="row-70">
    <span class="adj-age">70歳</span>
    <span class="adj-amount" id="t-70">---円</span>
    <span class="adj-rate rate-up">+42.0%</span>
  </div>
  <div class="adj-row" id="row-75">
    <span class="adj-age">75歳</span>
    <span class="adj-amount" id="t-75">---円</span>
    <span class="adj-rate rate-up">+84.0%</span>
  </div>
</div>

<div class="notice-box">
  <strong>計算方法：</strong>
  老齢基礎年金 = 816,000円 × (国民年金加入月数 ÷ 480)（2024年度満額）。
  老齢厚生年金 = 平均標準報酬月額（上限650,000円）× 5.481 ÷ 1000 × 厚生年金加入月数。
  繰上げ：65歳未満は1ヶ月あたり0.4%減額。繰下げ：66歳以上は1ヶ月あたり0.7%増額。
  実際の受給額は加入履歴や標準報酬月額の実績により異なります。
</div>

</div><!-- #result-area -->

<div class="affiliate-section">
<h3>老後資金を今すぐ対策する</h3>
<a href="https://hb.afl.rakuten.co.jp/hsc/41ab8a31.8f450617.41ab8a32.86e006c4/?link_type=hybrid_url&ut=eyJwYWdlIjoic2hvcCIsInR5cGUiOiJoeWJyaWRfdXJsIiwiY29sIjoxLCJjYXQiOiIxIiwiYmFuIjoiMTI0NjkzOSIsImFtcCI6ZmFsc2V9" target="_blank" rel="nofollow" class="aff-btn">楽天証券でiDeCo口座を開設する</a>
<a href="https://px.a8.net/svt/ejp?a8mat=3ZD3R9+DNEO+4PA2+5YJRM" rel="nofollow" class="aff-btn-sub">freee会計を無料で試す</a><img border="0" width="1" height="1" src="https://www14.a8.net/0.gif?a8mat=3ZD3R9+DNEO+4PA2+5YJRM" alt="">
</div>

<div class="related-tools">
<h3>関連ツール</h3>
<div class="tool-links">
  <a href="/ja/tools/fire-simulator/" class="tool-link">FIREシミュレーター</a>
  <a href="/ja/tools/ideco-simulator/" class="tool-link">iDeCoシミュレーター</a>
  <a href="/ja/tools/nisa-simulator/" class="tool-link">NISAシミュレーター</a>
  <a href="/ja/tools/salary-tedori-calculator/" class="tool-link">手取り計算機</a>
  <a href="/ja/tools/kakeibo-generator/" class="tool-link">家計簿ツール</a>
  <a href="/ja/tools/fukugyou-tax-calculator/" class="tool-link">副業税金計算</a>
  <a href="/ja/tools/kyouikuhi-simulator/" class="tool-link">教育費シミュレーター</a>
</div>
</div>

</div><!-- .nenkin-wrap -->

<script>
function fmt(n) {
  return Math.round(n).toLocaleString('ja-JP');
}

function nenkinCalc() {
  var age      = parseInt(document.getElementById('s-age').value, 10);
  var income   = parseInt(document.getElementById('s-income').value, 10);
  var kokumin  = parseInt(document.getElementById('s-kokumin').value, 10);
  var kousei   = parseInt(document.getElementById('s-kousei').value, 10);
  var startAge = parseInt(document.getElementById('s-start').value, 10);

  // Update slider display values
  document.getElementById('v-age').textContent     = age;
  document.getElementById('v-income').textContent  = income.toLocaleString('ja-JP');
  document.getElementById('v-kokumin').textContent = kokumin;
  document.getElementById('v-kousei').textContent  = kousei;

  // --- 老齢基礎年金 ---
  // 2024年度満額: 816,000円/年 (40年=480ヶ月加入時)
  var kisoFull      = 816000;
  var kokuminMonths = Math.min(kokumin * 12, 480);
  var kisoAnnual    = kisoFull * (kokuminMonths / 480);
  var kisoMonthly   = kisoAnnual / 12;

  // --- 老齢厚生年金 ---
  // 平均標準報酬月額 = 年収/12 、上限 650,000円
  var avgMonthlyWage = Math.min((income * 10000) / 12, 650000);
  var kouseiMonths   = kousei * 12;
  var kouseiAnnual   = avgMonthlyWage * (5.481 / 1000) * kouseiMonths;
  var kouseiMonthly  = kouseiAnnual / 12;

  // --- 65歳時点の合計 ---
  var base65Monthly = kisoMonthly + kouseiMonthly;

  // --- 繰上げ/繰下げ調整 ---
  var adjMonths = (startAge - 65) * 12;
  var adjRate;
  if (startAge < 65) {
    // 繰上げ: 1ヶ月あたり 0.4% 減額
    adjRate = 1 + adjMonths * 0.004; // adjMonths is negative here
  } else if (startAge > 65) {
    // 繰下げ: 1ヶ月あたり 0.7% 増額
    adjRate = 1 + adjMonths * 0.007;
  } else {
    adjRate = 1.0;
  }

  var selectedMonthly = base65Monthly * adjRate;
  var selectedAnnual  = selectedMonthly * 12;

  // Adjusted kiso / kousei proportional split
  var kisoAdj   = kisoMonthly   * adjRate;
  var kouseiAdj = kouseiMonthly * adjRate;

  // --- 比較 ---
  var diffMonthly = selectedMonthly - base65Monthly;
  var diffRate    = ((adjRate - 1) * 100);

  // --- Update result display ---
  document.getElementById('r-monthly').textContent       = fmt(selectedMonthly);
  document.getElementById('r-annual').textContent        = fmt(selectedAnnual);
  document.getElementById('r-kiso-annual').textContent   = fmt(kisoAdj * 12);
  document.getElementById('r-kiso-monthly').textContent  = fmt(kisoAdj);
  document.getElementById('r-kousei-annual').textContent  = fmt(kouseiAdj * 12);
  document.getElementById('r-kousei-monthly').textContent = fmt(kouseiAdj);

  // Diff display
  var rateEl  = document.getElementById('r-diff-rate');
  var amtEl   = document.getElementById('r-diff-amount');
  var signEl  = document.getElementById('r-diff-sign');
  rateEl.className = 'cmp-value';
  if (startAge === 65) {
    rateEl.textContent  = '±0%（65歳通常受給）';
    rateEl.classList.add('cmp-zero');
    amtEl.textContent   = '0';
    signEl.textContent  = '変化なし';
  } else if (diffRate < 0) {
    rateEl.textContent  = diffRate.toFixed(1) + '%（繰上げ減額）';
    rateEl.classList.add('cmp-minus');
    amtEl.textContent   = fmt(Math.abs(diffMonthly));
    signEl.textContent  = '減少';
  } else {
    rateEl.textContent  = '+' + diffRate.toFixed(1) + '%（繰下げ増額）';
    rateEl.classList.add('cmp-plus');
    amtEl.textContent   = fmt(diffMonthly);
    signEl.textContent  = '増加';
  }

  // --- 年齢別一覧 ---
  var ages = [60, 65, 70, 75];
  ages.forEach(function(a) {
    var m = (a - 65) * 12;
    var r;
    if (a < 65)       r = 1 + m * 0.004;
    else if (a > 65)  r = 1 + m * 0.007;
    else              r = 1.0;
    var val = base65Monthly * r;
    document.getElementById('t-' + a).textContent = fmt(val) + '円';
  });

  // Highlight selected row
  ['60','65','70','75'].forEach(function(a) {
    var row = document.getElementById('row-' + a);
    row.classList.remove('selected');
  });
  if ([60,65,70,75].indexOf(startAge) !== -1) {
    document.getElementById('row-' + startAge).classList.add('selected');
  }
}

// Initial calculation on load
nenkinCalc();
</script>

---

## 関連ツール

> 副業税金計算 → [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/)
> ふるさと納税シミュレーター → [ふるさと納税シミュレーターツール](/ja/tools/furusato-nozei-simulator/)
> iDeCo シミュレーター → [iDeCo シミュレーターツール](/ja/tools/ideco-simulator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [iDeCo おすすめ証券会社ランキング【2026年最新版】手数料・商品数を徹底比較](/ja/posts/ideco-osusume-shouken/)
- [iDeCo節税シミュレーション｜年収別に実際いくら得するか計算](/ja/posts/ideco-tax-saving-simulation/)
- [老後2000万円問題を自分で検証｜退職金なしの会社員がとるべき行動](/ja/posts/rougo-2000man-taisaku/)
