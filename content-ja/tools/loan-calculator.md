---
title: "ローン計算ツール - 返済額・利息シミュレーション"
date: 2025-05-16
description: "ローンの毎月返済額・総利息・返済期間を即座に計算。繰上返済の効果シミュレーション、返済スケジュール表付き。住宅ローン・自動車ローン・教育ローン対応。"
categories: ["無料ツール"]
tags: ["ローン計算", "返済シミュレーション", "利息計算", "繰上返済", "住宅ローン"]
slug: "loan-calculator"
aliases: ["/ja/tools/debt-payoff-calculator/", "/ja/tools/debt-payoff-calculator/"]
cover:
  image: "/images/covers/loan-calculator-ja.png"
  alt: "ローン計算ツール"
ShowToc: false
---

<div id="loan-app">

<style>
#loan-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a1a;
}
#loan-app * { box-sizing: border-box; }

/* preset buttons */
.preset-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}
.preset-btn {
  background: #f0fdf4;
  border: 1.5px solid #059669;
  color: #059669;
  border-radius: 20px;
  padding: 6px 16px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
.preset-btn:hover, .preset-btn.active {
  background: #059669;
  color: #fff;
}

/* tab */
.tab-bar {
  display: flex;
  border-bottom: 2px solid #d1fae5;
  margin-bottom: 24px;
  gap: 4px;
}
.tab-btn {
  background: none;
  border: none;
  padding: 10px 20px;
  font-size: 14px;
  font-weight: 600;
  color: #6b7280;
  cursor: pointer;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  border-radius: 6px 6px 0 0;
  transition: color 0.15s;
}
.tab-btn.active {
  color: #059669;
  border-bottom-color: #059669;
  background: #f0fdf4;
}

/* input card */
.input-card {
  background: #f0fdf4;
  border: 1px solid #a7f3d0;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 24px;
}
.input-card h3 {
  margin: 0 0 16px;
  font-size: 15px;
  color: #059669;
  font-weight: 700;
}
.field-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 14px;
  flex-wrap: wrap;
}
.field-label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  min-width: 130px;
}
.field-input {
  flex: 1;
  min-width: 100px;
  padding: 9px 12px;
  border: 1.5px solid #a7f3d0;
  border-radius: 8px;
  font-size: 15px;
  color: #1a1a1a;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
}
.field-input:focus { border-color: #059669; }
.unit-toggle {
  display: flex;
  border: 1.5px solid #a7f3d0;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
}
.unit-btn {
  padding: 9px 14px;
  background: none;
  border: none;
  font-size: 13px;
  font-weight: 600;
  color: #6b7280;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
.unit-btn.active {
  background: #059669;
  color: #fff;
}
.calc-btn {
  width: 100%;
  background: #059669;
  color: #fff;
  border: none;
  border-radius: 10px;
  padding: 14px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  margin-top: 8px;
  transition: background 0.15s;
}
.calc-btn:hover { background: #047857; }

/* result */
.result-hero {
  background: linear-gradient(135deg, #059669 0%, #047857 100%);
  color: #fff;
  border-radius: 14px;
  padding: 28px 24px;
  text-align: center;
  margin-bottom: 20px;
}
.result-hero .label { font-size: 14px; opacity: 0.85; margin-bottom: 6px; }
.result-hero .amount { font-size: 42px; font-weight: 800; letter-spacing: -1px; }
.result-hero .sub { font-size: 18px; font-weight: 600; opacity: 0.9; margin-top: 2px; }

.summary-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-bottom: 24px;
}
.summary-card {
  background: #fff;
  border: 1px solid #d1fae5;
  border-radius: 10px;
  padding: 16px;
  text-align: center;
}
.summary-card .s-label { font-size: 12px; color: #6b7280; margin-bottom: 6px; font-weight: 600; }
.summary-card .s-value { font-size: 20px; font-weight: 800; color: #059669; }
.summary-card .s-sub { font-size: 11px; color: #9ca3af; margin-top: 2px; }

/* pie chart */
.pie-section {
  display: flex;
  align-items: center;
  gap: 32px;
  background: #fff;
  border: 1px solid #d1fae5;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 24px;
  flex-wrap: wrap;
}
.pie-title { font-size: 14px; font-weight: 700; color: #374151; margin-bottom: 14px; }
.pie-wrap { position: relative; width: 110px; height: 110px; flex-shrink: 0; }
.pie-chart {
  width: 110px;
  height: 110px;
  border-radius: 50%;
  background: conic-gradient(#059669 0deg var(--principal-deg), #fbbf24 var(--principal-deg) 360deg);
}
.pie-inner {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  width: 54px; height: 54px;
  background: #fff;
  border-radius: 50%;
}
.pie-legend { flex: 1; min-width: 160px; }
.legend-item {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
  font-size: 13px;
}
.legend-dot {
  width: 12px; height: 12px;
  border-radius: 3px;
  flex-shrink: 0;
}
.legend-dot.principal { background: #059669; }
.legend-dot.interest { background: #fbbf24; }
.legend-info { line-height: 1.3; }
.legend-name { font-weight: 600; color: #374151; }
.legend-pct { color: #6b7280; font-size: 12px; }

/* prepayment */
.prepay-card {
  background: #fffbeb;
  border: 1px solid #fde68a;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 24px;
}
.prepay-card h3 { margin: 0 0 14px; font-size: 15px; color: #d97706; font-weight: 700; }
.prepay-result {
  display: flex;
  gap: 12px;
  margin-top: 14px;
  flex-wrap: wrap;
}
.prepay-box {
  flex: 1;
  min-width: 120px;
  background: #fff;
  border: 1px solid #fde68a;
  border-radius: 8px;
  padding: 12px;
  text-align: center;
}
.prepay-box .p-label { font-size: 11px; color: #92400e; font-weight: 600; margin-bottom: 4px; }
.prepay-box .p-value { font-size: 18px; font-weight: 800; color: #d97706; }

/* schedule table */
.schedule-section { margin-bottom: 24px; }
.schedule-section h3 { font-size: 15px; font-weight: 700; color: #374151; margin-bottom: 12px; }
.table-wrap {
  overflow-x: auto;
  border: 1px solid #d1fae5;
  border-radius: 10px;
}
table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
thead th {
  background: #059669;
  color: #fff;
  padding: 10px 12px;
  text-align: right;
  font-weight: 700;
  white-space: nowrap;
}
thead th:first-child { text-align: left; }
tbody tr:nth-child(even) { background: #f0fdf4; }
tbody td {
  padding: 8px 12px;
  text-align: right;
  border-bottom: 1px solid #d1fae5;
  white-space: nowrap;
}
tbody td:first-child { text-align: left; color: #6b7280; font-size: 12px; }
.show-more-btn {
  display: block;
  width: 100%;
  margin-top: 10px;
  padding: 10px;
  background: #fff;
  border: 1.5px solid #059669;
  color: #059669;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
.show-more-btn:hover { background: #f0fdf4; }

/* compare mode */
.compare-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 20px;
}
.compare-col { }
.compare-vs {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  font-weight: 800;
  color: #9ca3af;
  padding-top: 40px;
}
.compare-result-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 20px;
}
.compare-result-card {
  background: #f0fdf4;
  border: 1px solid #a7f3d0;
  border-radius: 10px;
  padding: 16px;
}
.compare-result-card h4 { margin: 0 0 12px; font-size: 14px; color: #059669; font-weight: 700; }
.compare-row { display: flex; justify-content: space-between; font-size: 13px; margin-bottom: 6px; }
.compare-row .cr-label { color: #6b7280; }
.compare-row .cr-value { font-weight: 700; color: #1a1a1a; }

.hidden { display: none !important; }
.section-divider { border: none; border-top: 1px solid #d1fae5; margin: 24px 0; }

@media (max-width: 600px) {
  .summary-grid { grid-template-columns: 1fr 1fr; }
  .result-hero .amount { font-size: 32px; }
  .compare-grid { grid-template-columns: 1fr; }
  .compare-result-grid { grid-template-columns: 1fr; }
  .field-label { min-width: 100px; }
  .tab-btn { padding: 8px 12px; font-size: 13px; }
}
</style>

<!-- TAB BAR -->
<div class="tab-bar">
  <button class="tab-btn active" onclick="switchTab('single')">通常計算</button>
  <button class="tab-btn" onclick="switchTab('compare')">ローン比較</button>
</div>

<!-- ===== SINGLE MODE ===== -->
<div id="tab-single">

  <!-- Preset -->
  <div class="preset-bar">
    <span style="font-size:13px;font-weight:600;color:#6b7280;align-self:center;">プリセット：</span>
    <button class="preset-btn" onclick="applyPreset('housing')">住宅ローン</button>
    <button class="preset-btn" onclick="applyPreset('car')">自動車ローン</button>
    <button class="preset-btn" onclick="applyPreset('edu')">教育ローン</button>
  </div>

  <!-- Input -->
  <div class="input-card">
    <h3>ローン情報を入力</h3>

    <div class="field-row">
      <span class="field-label">借入金額</span>
      <input class="field-input" id="loanAmount" type="number" value="3000" min="1" step="1" placeholder="3000">
      <div class="unit-toggle">
        <button class="unit-btn active" id="unitMan" onclick="setAmountUnit('man')">万円</button>
        <button class="unit-btn" id="unitYen" onclick="setAmountUnit('yen')">円</button>
      </div>
    </div>

    <div class="field-row">
      <span class="field-label">年利（%）</span>
      <input class="field-input" id="annualRate" type="number" value="1.5" min="0" step="0.01" placeholder="1.5">
      <span style="font-size:13px;color:#6b7280;">%</span>
    </div>

    <div class="field-row">
      <span class="field-label">借入期間</span>
      <input class="field-input" id="loanTerm" type="number" value="35" min="1" step="1" placeholder="35">
      <div class="unit-toggle">
        <button class="unit-btn active" id="termYear" onclick="setTermUnit('year')">年</button>
        <button class="unit-btn" id="termMonth" onclick="setTermUnit('month')">ヶ月</button>
      </div>
    </div>

    <button class="calc-btn" onclick="calculate()">計算する</button>
  </div>

  <!-- Result hero -->
  <div class="result-hero" id="resultHero" style="display:none;">
    <div class="label">毎月の返済額</div>
    <div class="amount" id="monthlyPaymentDisplay">-</div>
    <div class="sub" id="monthlyPaymentSub"></div>
  </div>

  <!-- Summary -->
  <div class="summary-grid" id="summaryGrid" style="display:none;">
    <div class="summary-card">
      <div class="s-label">総返済額</div>
      <div class="s-value" id="totalPayment">-</div>
      <div class="s-sub" id="totalPaymentSub"></div>
    </div>
    <div class="summary-card">
      <div class="s-label">総利息</div>
      <div class="s-value" id="totalInterest">-</div>
      <div class="s-sub" id="totalInterestSub"></div>
    </div>
    <div class="summary-card">
      <div class="s-label">返済終了</div>
      <div class="s-value" id="endDate">-</div>
      <div class="s-sub" id="endDateSub"></div>
    </div>
  </div>

  <!-- Pie chart -->
  <div class="pie-section" id="pieSection" style="display:none;">
    <div>
      <div class="pie-title">元金 vs 利息の内訳</div>
      <div class="pie-wrap">
        <div class="pie-chart" id="pieChart"></div>
        <div class="pie-inner"></div>
      </div>
    </div>
    <div class="pie-legend">
      <div class="legend-item">
        <div class="legend-dot principal"></div>
        <div class="legend-info">
          <div class="legend-name">元金</div>
          <div class="legend-pct" id="principalPct">-</div>
        </div>
      </div>
      <div class="legend-item">
        <div class="legend-dot interest"></div>
        <div class="legend-info">
          <div class="legend-name">利息</div>
          <div class="legend-pct" id="interestPct">-</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Prepayment -->
  <div class="prepay-card" id="prepayCard" style="display:none;">
    <h3>繰上返済シミュレーション</h3>
    <div class="field-row">
      <span class="field-label">毎月追加返済額</span>
      <input class="field-input" id="extraMonthly" type="number" value="0" min="0" step="1000" placeholder="0">
      <span style="font-size:13px;color:#6b7280;">円</span>
    </div>
    <div class="field-row">
      <span class="field-label">一括繰上返済額</span>
      <input class="field-input" id="lumpSum" type="number" value="0" min="0" step="10000" placeholder="0">
      <span style="font-size:13px;color:#6b7280;">円</span>
    </div>
    <button class="calc-btn" style="background:#d97706;" onclick="calcPrepay()">繰上返済効果を計算</button>
    <div class="prepay-result" id="prepayResult" style="display:none;">
      <div class="prepay-box">
        <div class="p-label">短縮期間</div>
        <div class="p-value" id="savedMonths">-</div>
      </div>
      <div class="prepay-box">
        <div class="p-label">節約利息額</div>
        <div class="p-value" id="savedInterest">-</div>
      </div>
      <div class="prepay-box">
        <div class="p-label">新・毎月返済額</div>
        <div class="p-value" id="newMonthly">-</div>
      </div>
    </div>
  </div>

  <!-- Schedule table -->
  <div class="schedule-section" id="scheduleSection" style="display:none;">
    <h3>返済スケジュール表</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th style="text-align:left;">年月</th>
            <th>返済額</th>
            <th>元金</th>
            <th>利息</th>
            <th>残高</th>
          </tr>
        </thead>
        <tbody id="scheduleBody"></tbody>
      </table>
    </div>
    <button class="show-more-btn" id="showMoreBtn" onclick="toggleSchedule()">全期間を表示する ▼</button>
  </div>

</div><!-- /tab-single -->

<!-- ===== COMPARE MODE ===== -->
<div id="tab-compare" class="hidden">
  <div class="compare-grid">
    <div class="compare-col">
      <div class="input-card">
        <h3>ローン A</h3>
        <div class="field-row">
          <span class="field-label">借入金額</span>
          <input class="field-input" id="cA_amount" type="number" value="3000" placeholder="3000">
          <span style="font-size:13px;color:#6b7280;">万円</span>
        </div>
        <div class="field-row">
          <span class="field-label">年利（%）</span>
          <input class="field-input" id="cA_rate" type="number" value="0.5" step="0.01" placeholder="0.5">
        </div>
        <div class="field-row">
          <span class="field-label">期間（年）</span>
          <input class="field-input" id="cA_term" type="number" value="35" placeholder="35">
        </div>
      </div>
    </div>

    <div class="compare-col">
      <div class="input-card" style="border-color:#fde68a;background:#fffbeb;">
        <h3 style="color:#d97706;">ローン B</h3>
        <div class="field-row">
          <span class="field-label">借入金額</span>
          <input class="field-input" id="cB_amount" type="number" value="3000" placeholder="3000">
          <span style="font-size:13px;color:#6b7280;">万円</span>
        </div>
        <div class="field-row">
          <span class="field-label">年利（%）</span>
          <input class="field-input" id="cB_rate" type="number" value="1.5" step="0.01" placeholder="1.5">
        </div>
        <div class="field-row">
          <span class="field-label">期間（年）</span>
          <input class="field-input" id="cB_term" type="number" value="35" placeholder="35">
        </div>
      </div>
    </div>
  </div>

  <button class="calc-btn" onclick="calcCompare()">2つを比較する</button>

  <div id="compareResult" style="display:none;margin-top:20px;">
    <div class="compare-result-grid">
      <div class="compare-result-card">
        <h4>ローン A</h4>
        <div class="compare-row"><span class="cr-label">毎月返済額</span><span class="cr-value" id="cA_monthly">-</span></div>
        <div class="compare-row"><span class="cr-label">総返済額</span><span class="cr-value" id="cA_total">-</span></div>
        <div class="compare-row"><span class="cr-label">総利息</span><span class="cr-value" id="cA_interest">-</span></div>
        <div class="compare-row"><span class="cr-label">年利</span><span class="cr-value" id="cA_rateDisplay">-</span></div>
        <div class="compare-row"><span class="cr-label">期間</span><span class="cr-value" id="cA_termDisplay">-</span></div>
      </div>
      <div class="compare-result-card" style="border-color:#fde68a;background:#fffbeb;">
        <h4 style="color:#d97706;">ローン B</h4>
        <div class="compare-row"><span class="cr-label">毎月返済額</span><span class="cr-value" id="cB_monthly">-</span></div>
        <div class="compare-row"><span class="cr-label">総返済額</span><span class="cr-value" id="cB_total">-</span></div>
        <div class="compare-row"><span class="cr-label">総利息</span><span class="cr-value" id="cB_interest">-</span></div>
        <div class="compare-row"><span class="cr-label">年利</span><span class="cr-value" id="cB_rateDisplay">-</span></div>
        <div class="compare-row"><span class="cr-label">期間</span><span class="cr-value" id="cB_termDisplay">-</span></div>
      </div>
    </div>
    <div id="compareDiff" style="background:#f0fdf4;border:1px solid #a7f3d0;border-radius:10px;padding:16px;font-size:14px;line-height:1.8;"></div>
  </div>
</div><!-- /tab-compare -->

<script>
(function() {
  // --- State ---
  var amountUnit = 'man'; // 'man' | 'yen'
  var termUnit   = 'year'; // 'year' | 'month'
  var scheduleData = [];
  var scheduleExpanded = false;
  var PREVIEW_ROWS = 12;

  // --- Unit toggles ---
  window.setAmountUnit = function(u) {
    amountUnit = u;
    document.getElementById('unitMan').classList.toggle('active', u === 'man');
    document.getElementById('unitYen').classList.toggle('active', u === 'yen');
  };
  window.setTermUnit = function(u) {
    termUnit = u;
    document.getElementById('termYear').classList.toggle('active', u === 'year');
    document.getElementById('termMonth').classList.toggle('active', u === 'month');
  };

  // --- Presets ---
  window.applyPreset = function(type) {
    document.querySelectorAll('.preset-btn').forEach(function(b){ b.classList.remove('active'); });
    event.target.classList.add('active');
    setAmountUnit('man');
    setTermUnit('year');
    if (type === 'housing') {
      document.getElementById('loanAmount').value = 3000;
      document.getElementById('annualRate').value  = 0.5;
      document.getElementById('loanTerm').value    = 35;
    } else if (type === 'car') {
      document.getElementById('loanAmount').value = 300;
      document.getElementById('annualRate').value  = 2.5;
      document.getElementById('loanTerm').value    = 5;
    } else if (type === 'edu') {
      document.getElementById('loanAmount').value = 300;
      document.getElementById('annualRate').value  = 3.0;
      document.getElementById('loanTerm').value    = 10;
    }
    calculate();
  };

  // --- Tab ---
  window.switchTab = function(tab) {
    document.querySelectorAll('.tab-btn').forEach(function(b, i){
      b.classList.toggle('active', (i === 0 && tab === 'single') || (i === 1 && tab === 'compare'));
    });
    document.getElementById('tab-single').classList.toggle('hidden', tab !== 'single');
    document.getElementById('tab-compare').classList.toggle('hidden', tab !== 'compare');
  };

  // --- Core calc ---
  function calcLoan(principal, annualRatePct, months) {
    var r = annualRatePct / 100 / 12;
    var n = months;
    var monthly;
    if (r === 0) {
      monthly = principal / n;
    } else {
      monthly = principal * r * Math.pow(1 + r, n) / (Math.pow(1 + r, n) - 1);
    }
    return monthly;
  }

  function buildSchedule(principal, annualRatePct, months, extraMonthly, lumpSumAt1) {
    var r = annualRatePct / 100 / 12;
    var rows = [];
    var balance = principal;
    var now = new Date(2025, 4, 1); // May 2025
    for (var i = 1; i <= months; i++) {
      if (balance <= 0) break;
      var interest = balance * r;
      var basePayment = calcLoan(principal, annualRatePct, months);
      var principalPart = basePayment - interest;
      if (principalPart < 0) principalPart = 0;
      var payment = basePayment + extraMonthly;
      if (i === 1 && lumpSumAt1 > 0) {
        balance -= lumpSumAt1;
        if (balance < 0) balance = 0;
      }
      var actualPrincipal = principalPart + extraMonthly;
      if (actualPrincipal > balance) actualPrincipal = balance;
      var actualPayment = actualPrincipal + interest;
      balance -= actualPrincipal;
      if (balance < 0) balance = 0;
      var d = new Date(now.getFullYear(), now.getMonth() + i - 1, 1);
      rows.push({
        label: d.getFullYear() + '年' + (d.getMonth() + 1) + '月',
        payment: actualPayment,
        principal: actualPrincipal,
        interest: interest,
        balance: balance
      });
      if (balance <= 0) break;
    }
    return rows;
  }

  function fmt(n) {
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }
  function fmtMan(n) {
    var man = n / 10000;
    if (man >= 1) {
      return man.toFixed(1) + '万円';
    }
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }

  window.calculate = function() {
    var amountRaw = parseFloat(document.getElementById('loanAmount').value) || 0;
    var principal = amountUnit === 'man' ? amountRaw * 10000 : amountRaw;
    var rate      = parseFloat(document.getElementById('annualRate').value) || 0;
    var termRaw   = parseFloat(document.getElementById('loanTerm').value)   || 0;
    var months    = termUnit === 'year' ? Math.round(termRaw * 12) : Math.round(termRaw);

    if (principal <= 0 || months <= 0) return;

    var monthly    = calcLoan(principal, rate, months);
    var total      = monthly * months;
    var totalInt   = total - principal;

    // Hero
    document.getElementById('resultHero').style.display = 'block';
    document.getElementById('monthlyPaymentDisplay').textContent = fmt(monthly);
    document.getElementById('monthlyPaymentSub').textContent = fmtMan(monthly) + ' / 月';

    // Summary
    var endDate = new Date(2025, 4 + months, 1);
    document.getElementById('summaryGrid').style.display = 'grid';
    document.getElementById('totalPayment').textContent  = fmtMan(total);
    document.getElementById('totalPaymentSub').textContent = fmt(total);
    document.getElementById('totalInterest').textContent = fmtMan(totalInt);
    document.getElementById('totalInterestSub').textContent = fmt(totalInt);
    document.getElementById('endDate').textContent       = endDate.getFullYear() + '年' + (endDate.getMonth() + 1) + '月';
    document.getElementById('endDateSub').textContent    = termUnit === 'year' ? termRaw + '年間' : termRaw + 'ヶ月間';

    // Pie
    document.getElementById('pieSection').style.display = 'flex';
    var principalPct = principal / total * 100;
    var interestPct  = 100 - principalPct;
    var deg = principalPct / 100 * 360;
    document.getElementById('pieChart').style.setProperty('--principal-deg', deg + 'deg');
    document.getElementById('principalPct').textContent = principalPct.toFixed(1) + '% （' + fmtMan(principal) + '）';
    document.getElementById('interestPct').textContent  = interestPct.toFixed(1) + '% （' + fmtMan(totalInt) + '）';

    // Prepay card
    document.getElementById('prepayCard').style.display = 'block';
    document.getElementById('prepayResult').style.display = 'none';

    // Schedule
    scheduleData = buildSchedule(principal, rate, months, 0, 0);
    scheduleExpanded = false;
    renderSchedule();
    document.getElementById('scheduleSection').style.display = 'block';
  };

  function renderSchedule() {
    var rows = scheduleExpanded ? scheduleData : scheduleData.slice(0, PREVIEW_ROWS);
    var html = '';
    rows.forEach(function(r) {
      html += '<tr>' +
        '<td>' + r.label + '</td>' +
        '<td>' + Math.round(r.payment).toLocaleString() + '円</td>' +
        '<td>' + Math.round(r.principal).toLocaleString() + '円</td>' +
        '<td>' + Math.round(r.interest).toLocaleString() + '円</td>' +
        '<td>' + Math.round(r.balance).toLocaleString() + '円</td>' +
        '</tr>';
    });
    document.getElementById('scheduleBody').innerHTML = html;
    var btn = document.getElementById('showMoreBtn');
    if (scheduleData.length <= PREVIEW_ROWS) {
      btn.style.display = 'none';
    } else {
      btn.style.display = 'block';
      btn.textContent = scheduleExpanded
        ? '表示を縮小する ▲'
        : '全' + scheduleData.length + 'ヶ月を表示する ▼';
    }
  }

  window.toggleSchedule = function() {
    scheduleExpanded = !scheduleExpanded;
    renderSchedule();
  };

  // --- Prepayment ---
  window.calcPrepay = function() {
    var amountRaw = parseFloat(document.getElementById('loanAmount').value) || 0;
    var principal = amountUnit === 'man' ? amountRaw * 10000 : amountRaw;
    var rate      = parseFloat(document.getElementById('annualRate').value) || 0;
    var termRaw   = parseFloat(document.getElementById('loanTerm').value)   || 0;
    var months    = termUnit === 'year' ? Math.round(termRaw * 12) : Math.round(termRaw);
    var extra     = parseFloat(document.getElementById('extraMonthly').value) || 0;
    var lump      = parseFloat(document.getElementById('lumpSum').value)      || 0;

    if (principal <= 0 || months <= 0) return;

    // Original total interest
    var origMonthly = calcLoan(principal, rate, months);
    var origTotal   = origMonthly * months;
    var origInt     = origTotal - principal;

    // New schedule
    var newSchedule = buildSchedule(principal, rate, months, extra, lump);
    var newMonths   = newSchedule.length;
    var newTotal    = newSchedule.reduce(function(s, r) { return s + r.payment; }, 0);
    var newInt      = newTotal - (principal - lump);

    var savedM   = months - newMonths;
    var savedInt = origInt - newInt;

    // New effective monthly (last full payment)
    var newMonthlyAmt = extra > 0 ? (origMonthly + extra) : origMonthly;

    document.getElementById('savedMonths').textContent   = savedM > 0 ? savedM + 'ヶ月短縮' : '変化なし';
    document.getElementById('savedInterest').textContent = savedInt > 0 ? fmtMan(savedInt) + '節約' : '変化なし';
    document.getElementById('newMonthly').textContent    = extra > 0 ? fmt(newMonthlyAmt) : fmt(origMonthly);
    document.getElementById('prepayResult').style.display = 'flex';
  };

  // --- Compare ---
  window.calcCompare = function() {
    function getInputs(prefix) {
      var amount  = (parseFloat(document.getElementById(prefix + '_amount').value) || 0) * 10000;
      var rate    = parseFloat(document.getElementById(prefix + '_rate').value)   || 0;
      var termYr  = parseFloat(document.getElementById(prefix + '_term').value)   || 0;
      var months  = Math.round(termYr * 12);
      var monthly = calcLoan(amount, rate, months);
      var total   = monthly * months;
      var interest = total - amount;
      return { amount: amount, rate: rate, months: months, monthly: monthly, total: total, interest: interest, termYr: termYr };
    }
    var A = getInputs('cA');
    var B = getInputs('cB');

    function fill(prefix, data) {
      document.getElementById(prefix + '_monthly').textContent     = fmt(data.monthly);
      document.getElementById(prefix + '_total').textContent       = fmtMan(data.total);
      document.getElementById(prefix + '_interest').textContent    = fmtMan(data.interest);
      document.getElementById(prefix + '_rateDisplay').textContent = data.rate + '%';
      document.getElementById(prefix + '_termDisplay').textContent = data.termYr + '年';
    }
    fill('cA', A);
    fill('cB', B);

    // Diff summary
    var diffMonthly  = B.monthly - A.monthly;
    var diffTotal    = B.total   - A.total;
    var diffInterest = B.interest - A.interest;
    var lines = [];
    lines.push('毎月の返済額の差：<strong>' + (diffMonthly >= 0 ? 'B が ' + fmt(Math.abs(diffMonthly)) + ' 高い' : 'A が ' + fmt(Math.abs(diffMonthly)) + ' 高い') + '</strong>');
    lines.push('総返済額の差：<strong>' + (diffTotal >= 0 ? 'B が ' + fmtMan(Math.abs(diffTotal)) + ' 多い' : 'A が ' + fmtMan(Math.abs(diffTotal)) + ' 多い') + '</strong>');
    lines.push('総利息の差：<strong>' + (diffInterest >= 0 ? 'B が ' + fmtMan(Math.abs(diffInterest)) + ' 多い' : 'A が ' + fmtMan(Math.abs(diffInterest)) + ' 多い') + '</strong>');
    document.getElementById('compareDiff').innerHTML = lines.join('<br>');
    document.getElementById('compareResult').style.display = 'block';
  };

  // Initial calculation
  calculate();
})();
</script>

</div><!-- /loan-app -->

---

## ローン計算ツールの使い方

このツールは3ステップで使えます。

1. **借入金額・金利・期間を入力する** — 万円・円の単位は切り替え可能です。住宅ローン・自動車ローン・教育ローンのプリセットボタンを使えば、代表的な金利が自動入力されます。
2. **「計算する」を押す** — 毎月返済額が大きく表示され、総返済額・総利息・返済終了月のサマリーと、元金・利息の割合を示す円グラフが表示されます。
3. **繰上返済や比較も試す** — 毎月の追加返済額や一括繰上返済を入力すると、何ヶ月短縮できるか・利息をいくら節約できるかがわかります。「ローン比較」タブでは2つのローン条件を並べて比較できます。

---

## ローンを早く返すコツ

**毎月少額でも繰上返済を続ける**
元金が減ると次月以降の利息も減るため、複利効果が逆方向に働きます。月1万円の上乗せでも、35年ローンなら数年短縮できることがあります。

**ボーナス時に一括繰上返済する**
残高が多い初期ほど利息削減効果が大きくなります。ローン開始から5年以内の一括返済は特に効率的です。

**金利の低いローンへの借換えを検討する**
変動金利が上昇傾向にある場合や、固定期間終了時には借換えで総返済額を大幅に下げられることがあります。手数料と節約額を必ず比較してください。

**返済期間を短く設定し直す**
借換えや条件変更の際に期間を短縮すると、金利コストを抑えながら完済を早められます。毎月の返済額が増える点は、このツールの比較モードで事前に確認しましょう。

---

## 関連ツール

> 割合・割引・変化率をすぐ計算 → [パーセント計算ツール](/ja/tools/percent-calculator/)

> インフレが資産に与える影響を確認 → [インフレ計算ツール](/ja/tools/inflation-calculator/)

> サブスクの年間コストを把握 → [サブスク管理計算ツール](/ja/tools/subscription-cost-calculator/)

---

**住宅ローン控除の確定申告をもっと簡単に**

住宅ローン控除の初年度は確定申告が必要です。クラウド会計ソフト「freee」なら、必要書類をガイドに沿って入力するだけで申告書が完成します。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
