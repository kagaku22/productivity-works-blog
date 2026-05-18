---
title: "フリーランス単価計算ツール | 適正時給を無料で診断"
date: 2025-06-29
draft: false
slug: "freelance-rate-calculator"
description: "収入目標・経費・税率・利益率をもとに、フリーランスの適正時給を計算します。フリーランサーやコンサルタント向けの無料インタラクティブ計算ツール。"
categories:
  - "無料ツール"
tags:
  - "フリーランス単価"
  - "時給計算"
  - "フリーランス料金設定"
  - "計算ツール"
  - "副業"
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/freelance-rate-calculator.png"
  alt: "フリーランス単価計算ツール | 適正時給を無料で診断"
  relative: false
---

*本記事にはアフィリエイトリンクが含まれています。*

# フリーランス単価計算ツール

収入目標と稼働時間を入力して、請求すべき**最低時給**と、持続可能な事業運営のための**推奨時給**を算出しましょう。

<style>
.fr-wrap {
  max-width: 720px;
  margin: 0 auto;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: #1e293b;
}
.fr-card {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 14px;
  padding: 28px;
  margin-bottom: 20px;
  box-shadow: 0 2px 8px rgba(13,148,136,0.07);
}
.fr-section-title {
  font-size: 15px;
  font-weight: 700;
  color: #0d9488;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin: 0 0 18px 0;
}
.fr-field {
  margin-bottom: 18px;
}
.fr-label {
  display: block;
  font-size: 14px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 8px;
}
.fr-range-row {
  display: flex;
  align-items: center;
  gap: 12px;
}
.fr-range-row input[type="range"] {
  flex: 1;
  accent-color: #0d9488;
  height: 6px;
  cursor: pointer;
}
.fr-range-val {
  min-width: 80px;
  text-align: right;
  font-weight: 700;
  font-size: 15px;
  color: #0d9488;
}
.fr-input {
  width: 100%;
  padding: 10px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 15px;
  color: #1e293b;
  box-sizing: border-box;
  transition: border-color 0.2s;
}
.fr-input:focus {
  outline: none;
  border-color: #0d9488;
}
.fr-results-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 20px;
}
.fr-result-box {
  background: #f0fdfa;
  border: 2px solid #0d9488;
  border-radius: 12px;
  padding: 18px;
  text-align: center;
}
.fr-result-box.primary {
  background: #0d9488;
  color: #fff;
}
.fr-result-label {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #134e4a;
  margin-bottom: 6px;
}
.fr-result-box.primary .fr-result-label {
  color: #ccfbf1;
}
.fr-result-value {
  font-size: 32px;
  font-weight: 800;
  color: #0d9488;
  line-height: 1;
}
.fr-result-box.primary .fr-result-value {
  color: #fff;
  font-size: 38px;
}
.fr-result-sub {
  font-size: 12px;
  color: #5eead4;
  margin-top: 4px;
}
.fr-stat-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #e2e8f0;
  font-size: 14px;
}
.fr-stat-row:last-child { border-bottom: none; }
.fr-stat-label { color: #64748b; }
.fr-stat-val { font-weight: 700; color: #0d9488; }
.fr-bar-wrap {
  margin-top: 10px;
}
.fr-bar-track {
  display: flex;
  height: 28px;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 12px;
}
.fr-bar-seg {
  transition: width 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 11px;
  font-weight: 700;
  color: #fff;
  overflow: hidden;
  white-space: nowrap;
}
.fr-legend {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
}
.fr-legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
}
.fr-legend-dot {
  width: 12px;
  height: 12px;
  border-radius: 3px;
  flex-shrink: 0;
}
.fr-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}
.fr-table th {
  background: #0d9488;
  color: #fff;
  padding: 10px 12px;
  text-align: left;
  font-weight: 600;
}
.fr-table td {
  padding: 10px 12px;
  border-bottom: 1px solid #e2e8f0;
}
.fr-table tr.highlighted td {
  background: #f0fdfa;
  font-weight: 700;
  color: #0d9488;
}
.fr-table tr:hover td { background: #f8fafc; }
.fr-toggle-btn {
  display: flex;
  align-items: center;
  gap: 12px;
  cursor: pointer;
  padding: 12px 16px;
  background: #f0fdfa;
  border: 2px solid #0d9488;
  border-radius: 10px;
  font-weight: 700;
  font-size: 14px;
  color: #134e4a;
  margin-bottom: 16px;
  user-select: none;
  transition: background 0.2s;
}
.fr-toggle-btn:hover { background: #ccfbf1; }
.fr-toggle-switch {
  width: 40px;
  height: 22px;
  background: #cbd5e1;
  border-radius: 11px;
  position: relative;
  transition: background 0.2s;
  flex-shrink: 0;
}
.fr-toggle-switch.on { background: #0d9488; }
.fr-toggle-switch::after {
  content: '';
  position: absolute;
  width: 16px;
  height: 16px;
  background: #fff;
  border-radius: 50%;
  top: 3px;
  left: 3px;
  transition: left 0.2s;
}
.fr-toggle-switch.on::after { left: 21px; }
.fr-project-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}
.fr-project-box {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 14px;
  text-align: center;
}
.fr-project-hours {
  font-size: 12px;
  color: #64748b;
  margin-bottom: 4px;
}
.fr-project-price {
  font-size: 22px;
  font-weight: 800;
  color: #0d9488;
}
.fr-project-label {
  font-size: 11px;
  color: #94a3b8;
  margin-top: 2px;
}
@media (max-width: 520px) {
  .fr-results-grid { grid-template-columns: 1fr; }
  .fr-project-grid { grid-template-columns: 1fr; }
  .fr-legend { grid-template-columns: 1fr; }
}
</style>

<div class="fr-wrap">

<!-- 入力エリア -->
<div class="fr-card">
<div class="fr-section-title">収入目標</div>

<div class="fr-field">
  <label class="fr-label" for="frAnnualIncome">目標年収（円）</label>
  <input type="number" id="frAnnualIncome" class="fr-input" value="80000" min="10000" max="500000" step="1000" oninput="calcFR()">
</div>

<div class="fr-field">
  <label class="fr-label">週あたり請求可能時間: <span id="frHoursVal" style="color:#0d9488;">30</span> 時間</label>
  <div class="fr-range-row">
    <span style="font-size:12px;color:#94a3b8;">20</span>
    <input type="range" id="frHours" min="20" max="40" step="1" value="30" oninput="calcFR()">
    <span style="font-size:12px;color:#94a3b8;">40</span>
  </div>
  <div style="font-size:12px;color:#94a3b8;margin-top:4px;">実際にクライアントに請求できる時間のみカウント</div>
</div>

<div class="fr-field">
  <label class="fr-label">年間稼働週数: <span id="frWeeksVal" style="color:#0d9488;">48</span> 週</label>
  <div class="fr-range-row">
    <span style="font-size:12px;color:#94a3b8;">40</span>
    <input type="range" id="frWeeks" min="40" max="52" step="1" value="48" oninput="calcFR()">
    <span style="font-size:12px;color:#94a3b8;">52</span>
  </div>
  <div style="font-size:12px;color:#94a3b8;margin-top:4px;">休暇・病欠・祝日を差し引いてください</div>
</div>

<div class="fr-field">
  <label class="fr-label" for="frExpenses">年間事業経費（円）</label>
  <input type="number" id="frExpenses" class="fr-input" value="5000" min="0" max="200000" step="500" oninput="calcFR()">
  <div style="font-size:12px;color:#94a3b8;margin-top:4px;">ソフトウェア・機材・保険・マーケティング・会計費用など</div>
</div>

<div class="fr-field">
  <label class="fr-label">税率（個人事業主）: <span id="frTaxVal" style="color:#0d9488;">25</span>%</label>
  <div class="fr-range-row">
    <span style="font-size:12px;color:#94a3b8;">10%</span>
    <input type="range" id="frTax" min="10" max="35" step="1" value="25" oninput="calcFR()">
    <span style="font-size:12px;color:#94a3b8;">35%</span>
  </div>
  <div style="font-size:12px;color:#94a3b8;margin-top:4px;">所得税・住民税・個人事業税などを含む合計税率</div>
</div>

<div class="fr-field">
  <label class="fr-label">利益率: <span id="frMarginVal" style="color:#0d9488;">15</span>%</label>
  <div class="fr-range-row">
    <span style="font-size:12px;color:#94a3b8;">0%</span>
    <input type="range" id="frMargin" min="0" max="30" step="1" value="15" oninput="calcFR()">
    <span style="font-size:12px;color:#94a3b8;">30%</span>
  </div>
  <div style="font-size:12px;color:#94a3b8;margin-top:4px;">閑散期の備え・事業成長・再投資のためのバッファ</div>
</div>
</div>

<!-- 計算結果 -->
<div id="frResultsCard" class="fr-card">
<div class="fr-section-title">あなたのフリーランス単価</div>
<div class="fr-results-grid" id="frRatesGrid"></div>
<div id="frStatsGrid"></div>
</div>

<!-- 収入目標別比較表 -->
<div class="fr-card">
<div class="fr-section-title">収入目標別 単価比較</div>
<div style="font-size:13px;color:#64748b;margin-bottom:14px;">現在の時間・週・税率設定に基づく試算。あなたの目標に最も近い行をハイライト表示しています。</div>
<div style="overflow-x:auto;">
<table class="fr-table" id="frCompTable">
<thead>
<tr>
  <th>収入目標</th>
  <th>最低時給</th>
  <th>推奨時給</th>
  <th>必要年間売上</th>
</tr>
</thead>
<tbody id="frCompBody"></tbody>
</table>
</div>
</div>

<!-- 収入の内訳 -->
<div class="fr-card">
<div class="fr-section-title">実際の手取り内訳</div>
<div class="fr-bar-wrap">
  <div class="fr-bar-track" id="frBarTrack"></div>
  <div class="fr-legend" id="frLegend"></div>
</div>
</div>

<!-- プロジェクト料金 -->
<div class="fr-card">
<div class="fr-section-title">料金設定戦略</div>
<div class="fr-toggle-btn" onclick="toggleProjectView()" id="frToggleBtn">
  <div class="fr-toggle-switch" id="frToggleSwitch"></div>
  時給提示より案件単価で見積もる — プロジェクト料金を表示
</div>
<div id="frProjectPanel" style="display:none;">
  <div style="font-size:13px;color:#64748b;margin-bottom:14px;">推奨時給をもとにしたプロジェクト料金目安。時間ではなく成果物の価値で提示しましょう。</div>
  <div class="fr-project-grid" id="frProjectGrid"></div>
</div>
</div>

</div><!-- end fr-wrap -->

<script>
var frProjectsOn = false;

function fmtD(n) {
  return '$' + Math.round(n).toLocaleString('en-US');
}
function fmtR(n) {
  return '$' + n.toFixed(2);
}

function calcFRRate(income, hours, weeks, expenses, taxRate, margin) {
  var totalHours = hours * weeks;
  var revenueNeeded = income + expenses;
  var revenueWithTax = revenueNeeded / (1 - taxRate / 100);
  var minRate = revenueWithTax / totalHours;
  var recRate = minRate / (1 - margin / 100);
  return { minRate: minRate, recRate: recRate, revenueWithTax: revenueWithTax, totalHours: totalHours };
}

function calcFR() {
  var income = parseFloat(document.getElementById('frAnnualIncome').value) || 80000;
  var hours = parseInt(document.getElementById('frHours').value);
  var weeks = parseInt(document.getElementById('frWeeks').value);
  var expenses = parseFloat(document.getElementById('frExpenses').value) || 0;
  var taxRate = parseInt(document.getElementById('frTax').value);
  var margin = parseInt(document.getElementById('frMargin').value);

  document.getElementById('frHoursVal').textContent = hours;
  document.getElementById('frWeeksVal').textContent = weeks;
  document.getElementById('frTaxVal').textContent = taxRate;
  document.getElementById('frMarginVal').textContent = margin;

  var r = calcFRRate(income, hours, weeks, expenses, taxRate, margin);
  var totalHours = r.totalHours;
  var minRate = r.minRate;
  var recRate = r.recRate;
  var annualRevenue = recRate * totalHours;
  var monthlyRevenue = annualRevenue / 12;
  var dailyRate = recRate * 8;
  var halfDayRate = recRate * 4;

  var rg = document.getElementById('frRatesGrid');
  rg.innerHTML =
    '<div class="fr-result-box">' +
      '<div class="fr-result-label">最低時給</div>' +
      '<div class="fr-result-value">' + fmtR(minRate) + '</div>' +
      '<div style="font-size:12px;color:#134e4a;margin-top:6px;">収入＋経費＋税金をカバー</div>' +
    '</div>' +
    '<div class="fr-result-box primary">' +
      '<div class="fr-result-label">推奨時給</div>' +
      '<div class="fr-result-value">' + fmtR(recRate) + '</div>' +
      '<div class="fr-result-sub">利益率 ' + margin + '% 込み</div>' +
    '</div>';

  var sg = document.getElementById('frStatsGrid');
  var stats = [
    ['必要年間売上', fmtD(annualRevenue)],
    ['必要月間売上', fmtD(monthlyRevenue)],
    ['実効日当（8時間）', fmtD(dailyRate)],
    ['半日料金（4時間）', fmtD(halfDayRate)],
    ['年間請求可能時間合計', totalHours.toLocaleString('en-US') + ' 時間']
  ];
  var sh = '';
  for (var i = 0; i < stats.length; i++) {
    sh += '<div class="fr-stat-row"><span class="fr-stat-label">' + stats[i][0] + '</span><span class="fr-stat-val">' + stats[i][1] + '</span></div>';
  }
  sg.innerHTML = sh;

  var targets = [50000, 60000, 80000, 100000, 120000, 150000];
  var closestIdx = 0;
  var closestDiff = Math.abs(income - targets[0]);
  for (var j = 1; j < targets.length; j++) {
    var diff = Math.abs(income - targets[j]);
    if (diff < closestDiff) { closestDiff = diff; closestIdx = j; }
  }
  var cb = document.getElementById('frCompBody');
  var ch = '';
  for (var k = 0; k < targets.length; k++) {
    var tr = calcFRRate(targets[k], hours, weeks, expenses, taxRate, margin);
    var hl = k === closestIdx ? ' class="highlighted"' : '';
    var star = k === closestIdx ? ' ★' : '';
    ch += '<tr' + hl + '>' +
      '<td>' + fmtD(targets[k]) + star + '</td>' +
      '<td>' + fmtR(tr.minRate) + '/時</td>' +
      '<td>' + fmtR(tr.recRate) + '/時</td>' +
      '<td>' + fmtD(tr.recRate * tr.totalHours) + '</td>' +
    '</tr>';
  }
  cb.innerHTML = ch;

  var taxAmt = annualRevenue * (taxRate / 100);
  var expAmt = expenses;
  var profitAmt = annualRevenue * (margin / 100);
  var takeHome = annualRevenue - taxAmt - expAmt - profitAmt;
  if (takeHome < 0) takeHome = 0;
  var total = taxAmt + expAmt + profitAmt + takeHome;

  function pct(v) { return total > 0 ? (v / total * 100).toFixed(1) : '0'; }

  var segs = [
    { label: '手取り', val: takeHome, color: '#0d9488' },
    { label: '税金', val: taxAmt, color: '#ef4444' },
    { label: '経費', val: expAmt, color: '#f59e0b' },
    { label: '利益バッファ', val: profitAmt, color: '#8b5cf6' }
  ];

  var barH = '';
  var legH = '';
  for (var s = 0; s < segs.length; s++) {
    var p = pct(segs[s].val);
    barH += '<div class="fr-bar-seg" style="width:' + p + '%;background:' + segs[s].color + ';">' +
      (parseFloat(p) > 8 ? p + '%' : '') + '</div>';
    legH += '<div class="fr-legend-item">' +
      '<div class="fr-legend-dot" style="background:' + segs[s].color + ';"></div>' +
      '<span><strong>' + segs[s].label + '</strong>: ' + fmtD(segs[s].val) + ' (' + p + '%)</span>' +
    '</div>';
  }
  document.getElementById('frBarTrack').innerHTML = barH;
  document.getElementById('frLegend').innerHTML = legH;

  var projectHours = [2, 5, 10, 20, 40];
  var projectLabels = ['スポット対応（2時間）', '半日案件（5時間）', '1日案件（10時間）', '2日案件（20時間）', '週次案件（40時間）'];
  var pg = document.getElementById('frProjectGrid');
  var ph = '';
  for (var p2 = 0; p2 < projectHours.length; p2++) {
    var price = recRate * projectHours[p2];
    ph += '<div class="fr-project-box">' +
      '<div class="fr-project-hours">' + projectLabels[p2] + '</div>' +
      '<div class="fr-project-price">' + fmtD(price) + '</div>' +
      '<div class="fr-project-label">推奨時給 ' + fmtR(recRate) + '/時 基準</div>' +
    '</div>';
  }
  pg.innerHTML = ph;
}

function toggleProjectView() {
  frProjectsOn = !frProjectsOn;
  var sw = document.getElementById('frToggleSwitch');
  var panel = document.getElementById('frProjectPanel');
  if (frProjectsOn) {
    sw.classList.add('on');
    panel.style.display = 'block';
  } else {
    sw.classList.remove('on');
    panel.style.display = 'none';
  }
}

document.addEventListener('DOMContentLoaded', function() { calcFR(); });
calcFR();
</script>

---

## このツールの使い方

1. **目標年収を入力** — 税引き後に手元に残したい金額を入力します。
2. **請求可能時間を設定** — 現実的に見積もりましょう。多くのフリーランサーは週25〜35時間が請求可能で、残りは管理業務・営業・クライアント対応に充てられます。
3. **稼働週数を調整** — 休暇・祝日・病欠を差し引きます。48週が一般的な目安です。
4. **事業経費を追加** — サブスクリプション・機材・保険・研修費・会計費用などを含めます。
5. **税率を設定** — 所得税・住民税・個人事業税を合算した実効税率を設定します。
6. **利益率を選択** — 閑散期の備えや事業成長のためのバッファです。

**最低時給**は最低限の収支を維持するための水準です。**推奨時給**が実際に請求すべき金額です。

---

## フリーランス単価の設定方法

### 1. 市場相場を調査する

単価を設定する前に、同じ職種・地域・業界の相場を調べましょう。クラウドワークス・ランサーズ・LinkedInなどのプラットフォームや業界団体の調査を参照してください。あなたの単価は競争力があるものでなければなりませんが、最安値を目指す必要はありません。

### 2. 非請求時間を考慮する

メール対応・提案書作成・請求書処理・営業・自己研鑽に費やす時間はすべて、クライアントに請求できない時間です。週40時間働いても請求できるのが25時間なら、事業のコストは40時間ベースで考える必要があります。このツールの「請求可能時間」スライダーはこの現実を反映しています。

### 3. 価値ベース料金設定へ移行する

時給制は収入に上限を生みます。専門性が高まったら、時間ではなく成果物や価値で料金設定することを検討しましょう。3時間で作ったロゴがクライアントのブランド混乱を解消して大きな価値を生むなら、それは時給×3時間をはるかに超える価値があります。「案件単価で見積もる」トグルで推奨時給ベースのプロジェクト料金目安を確認できます。

---

## フリーランス単価の参考相場（日本市場）

| 職種 | 初級 | 中級 | 上級 |
|---|---|---|---|
| ライター | 1,500〜3,000円/時 | 3,000〜6,000円/時 | 6,000〜15,000円/時 |
| グラフィックデザイナー | 2,000〜4,000円/時 | 4,000〜8,000円/時 | 8,000〜20,000円/時 |
| Webエンジニア | 3,000〜5,000円/時 | 5,000〜10,000円/時 | 10,000〜30,000円/時 |
| マーケティングコンサルタント | 3,000〜6,000円/時 | 6,000〜12,000円/時 | 12,000〜30,000円/時 |
| 経営コンサルタント | 5,000〜10,000円/時 | 10,000〜20,000円/時 | 20,000〜50,000円/時 |
| UX/UIデザイナー | 3,000〜6,000円/時 | 6,000〜12,000円/時 | 12,000〜25,000円/時 |
| コピーライター | 2,000〜5,000円/時 | 5,000〜10,000円/時 | 10,000〜20,000円/時 |

*単価は案件・クライアント・専門領域によって大きく異なります。あくまで参考値です。*

---

## 関連ツール

> 時給を年収に換算する → [時給・年収換算計算ツール](/tools/hourly-to-salary-calculator/)

> ローン返済を計算する → [ローン返済計算ツール](/tools/loan-repayment-calculator/)

> 月次予算を立てる → [予算プランナー](/tools/budget-planner/)

---

*免責事項：本ツールは教育・参考目的の概算を提供するものであり、税務・法務・財務アドバイスを構成するものではありません。税率は収入・申告状況・居住地・控除によって異なります。詳細は税理士または専門家にご相談ください。*

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

## 関連記事

- [フリーランスエンジニアの開業届と青色申告｜初年度にやるべき手続き全リスト](/ja/posts/freelance-engineer-kaigyou-aoiro-shinkoku/)
- [AIを使った副業の始め方完全ガイド【2026年版・月3万〜10万円を目指す】](/ja/posts/ai-副業-始め方/)
- [AI副業で稼ぐ方法2026年最新完全ガイド](/ja/posts/ai-副業-稼ぐ-方法-2026/)
