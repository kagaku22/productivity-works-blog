---
title: "所得税計算ツール - 税額シミュレーション"
date: 2025-05-16
description: "無料の所得税計算ツール。給与所得から所得税額を即座に計算。累進税率・控除額・実効税率を表示。確定申告の参考に。"
categories: ["無料ツール"]
slug: "tax-calculator"
ShowToc: false
aliases:
  - "/ja/tools/tax-estimator/"
  - "/ja/tools/shotokuzei/"
cover:
  image: "/images/covers/tax-calculator-ja.png"
  alt: "所得税計算ツール"
---

<div id="tc-app">
<style>
#tc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}
#tc-app * { box-sizing: border-box; }
#tc-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1.2rem;
  color: #1a1a2e;
  border-left: 4px solid #22c55e;
  padding-left: 0.7rem;
}
#tc-app .tc-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.6rem;
  margin-bottom: 1.4rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
#tc-app .tc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
}
#tc-app label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #4a5568;
  margin-bottom: 0.35rem;
  letter-spacing: 0.02em;
}
#tc-app input[type=number] {
  width: 100%;
  padding: 0.6rem 0.9rem;
  border: 1.5px solid #cbd5e0;
  border-radius: 8px;
  font-size: 1rem;
  color: #1a1a2e;
  background: #f8fafc;
  transition: border-color 0.2s;
  outline: none;
}
#tc-app input[type=number]:focus {
  border-color: #22c55e;
  background: #fff;
}
#tc-app .tc-btn {
  display: inline-block;
  padding: 0.7rem 2rem;
  background: linear-gradient(135deg, #22c55e, #16a34a);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 1rem;
  transition: opacity 0.2s;
}
#tc-app .tc-btn:hover { opacity: 0.88; }
#tc-app .tc-info-box {
  background: #f0fdf4;
  border-left: 3px solid #22c55e;
  border-radius: 6px;
  padding: 0.7rem 1rem;
  margin-top: 1rem;
  font-size: 0.83rem;
  color: #2d3748;
  line-height: 1.7;
}
#tc-app .tc-results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1rem;
  margin-bottom: 1.4rem;
}
#tc-app .tc-stat {
  background: #f0fdf4;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  text-align: center;
}
#tc-app .tc-stat .tc-stat-label {
  font-size: 0.75rem;
  font-weight: 600;
  color: #16a34a;
  margin-bottom: 0.3rem;
}
#tc-app .tc-stat .tc-stat-value {
  font-size: 1.3rem;
  font-weight: 800;
  color: #1a1a2e;
}
#tc-app .tc-stat.tc-highlight {
  background: linear-gradient(135deg, #dcfce7, #bbf7d0);
  border: 1.5px solid #22c55e;
}
#tc-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.87rem;
}
#tc-app thead th {
  background: #f0fdf4;
  color: #16a34a;
  font-weight: 700;
  padding: 0.6rem 0.8rem;
  text-align: right;
  border-bottom: 2px solid #e2e8f0;
}
#tc-app thead th:first-child { text-align: left; }
#tc-app tbody td {
  padding: 0.5rem 0.8rem;
  text-align: right;
  border-bottom: 1px solid #f0f0f0;
  color: #2d3748;
}
#tc-app tbody td:first-child { text-align: left; }
#tc-app tbody tr:hover { background: #f0fdf4; }
#tc-app tbody tr.tc-active-row { background: #dcfce7; font-weight: 600; }
#tc-app .tc-bar-wrap {
  background: #f0f0f0;
  border-radius: 4px;
  height: 10px;
  display: inline-block;
  width: 60px;
  vertical-align: middle;
  margin-left: 6px;
  overflow: hidden;
}
#tc-app .tc-bar-fill {
  height: 100%;
  border-radius: 4px;
  background: linear-gradient(90deg, #22c55e, #16a34a);
}
#tc-app .tc-hidden { display: none; }
#tc-app .tc-note {
  font-size: 0.78rem;
  color: #888;
  margin-top: 1rem;
  line-height: 1.7;
}
#tc-app .tc-cta {
  background: linear-gradient(135deg, #f0f5ff, #e8f4fd);
  border: 1.5px solid #4f8ef7;
  border-radius: 12px;
  padding: 1.4rem 1.6rem;
  margin-top: 1.4rem;
  text-align: center;
}
#tc-app .tc-cta p {
  margin: 0 0 0.8rem;
  font-size: 0.95rem;
  color: #2d3748;
  line-height: 1.7;
}
#tc-app .tc-cta a.tc-cta-btn {
  display: inline-block;
  background: linear-gradient(135deg, #4f8ef7, #3b6fd4);
  color: #fff;
  padding: 0.65rem 1.8rem;
  border-radius: 8px;
  font-weight: 700;
  font-size: 0.95rem;
  text-decoration: none;
  transition: opacity 0.2s;
}
#tc-app .tc-cta a.tc-cta-btn:hover { opacity: 0.85; }
#tc-app canvas { display: block; margin: 0 auto 1rem; }
</style>

<div class="tc-card">
  <h2>収入の入力</h2>
  <div class="tc-grid">
    <div>
      <label for="tc-income">給与収入（年収・円）</label>
      <input type="number" id="tc-income" value="5000000" min="0" step="10000">
    </div>
  </div>
  <div class="tc-info-box" id="tc-info-box">
    ここに入力した給与収入をもとに、給与所得控除・基礎控除・社会保険料控除を自動計算します。
  </div>
  <button class="tc-btn" onclick="tcCalculate()">計算する</button>
</div>

<div class="tc-card tc-hidden" id="tc-results">
  <h2>計算結果</h2>
  <div class="tc-results-grid">
    <div class="tc-stat">
      <div class="tc-stat-label">給与収入</div>
      <div class="tc-stat-value" id="tc-gross-out">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">給与所得</div>
      <div class="tc-stat-value" id="tc-kyuyo-shotoku">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">各種控除合計</div>
      <div class="tc-stat-value" id="tc-total-ded">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">課税所得</div>
      <div class="tc-stat-value" id="tc-taxable-out">—</div>
    </div>
    <div class="tc-stat tc-highlight">
      <div class="tc-stat-label">所得税額（概算）</div>
      <div class="tc-stat-value" id="tc-tax-out">—</div>
    </div>
    <div class="tc-stat">
      <div class="tc-stat-label">実効税率</div>
      <div class="tc-stat-value" id="tc-eff-out">—</div>
    </div>
  </div>
  <canvas id="tc-chart" width="700" height="200"></canvas>
</div>

<div class="tc-card tc-hidden" id="tc-bracket-card">
  <h2>税率区分内訳</h2>
  <div style="overflow-x:auto">
    <table>
      <thead>
        <tr>
          <th>課税所得の範囲</th>
          <th>税率</th>
          <th>控除額</th>
          <th>この区分の課税所得</th>
          <th>この区分の税額</th>
        </tr>
      </thead>
      <tbody id="tc-bracket-body"></tbody>
    </table>
  </div>
  <p class="tc-note">※ 2024年（令和6年）分の所得税の税率表を使用しています。住民税・復興特別所得税（2.1%）・各種控除（医療費控除・生命保険料控除等）は含まれていません。実際の税額は確定申告や源泉徴収によって異なる場合があります。本ツールは参考情報の提供を目的とし、税務上の助言を構成するものではありません。</p>
</div>

<div class="tc-cta">
  <p><strong>確定申告・会計をもっとラクに？</strong><br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow" target="_blank">freee会計</a> なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。</p>
  <a class="tc-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow" target="_blank">freee会計を無料で試す</a>
</div>

<script>
(function(){
  // 給与所得控除 schedule (2024)
  function calcKyuyoKojyo(income) {
    if (income <= 550999)   return income;            // 所得0
    if (income <= 1619000)  return 550000;
    if (income <= 1619999)  return income - 1069000;
    if (income <= 1621999)  return 550000;
    if (income <= 1623999)  return 552000;
    if (income <= 1627999)  return 556000;
    if (income <= 1800000)  return Math.floor(income / 4) * 4 * 0.4 - (Math.floor(income / 4) * 4 * 0.4 % 1);
    // simpler schedule from 1,800,001+
    if (income <= 3600000)  return Math.floor(income * 0.3) + 108000;
    if (income <= 6600000)  return Math.floor(income * 0.2) + 468000;
    if (income <= 8500000)  return Math.floor(income * 0.1) + 1128000;
    return 1950000; // cap
  }

  // Simplified but accurate for salary:
  function calcKyuyoShotoku(income) {
    var deduction;
    if (income <= 550999)   return 0;
    if (income <= 1619000)  deduction = 550000;
    else if (income <= 1619999) deduction = income - 1069000;
    else if (income <= 1621999) deduction = 550000;
    else if (income <= 1623999) deduction = 552000;
    else if (income <= 1627999) deduction = 556000;
    else if (income <= 1800000) {
      var base = Math.floor(income / 4) * 4;
      deduction = base * 0.4;
    }
    else if (income <= 3600000) deduction = income * 0.3 + 108000;
    else if (income <= 6600000) deduction = income * 0.2 + 468000;
    else if (income <= 8500000) deduction = income * 0.1 + 1128000;
    else deduction = 1950000;
    return Math.max(0, income - deduction);
  }

  // JP brackets 2024: [min, max, rate, deduction_yen]
  var JP_BRACKETS = [
    { min: 0,        max: 1950000,  rate: 0.05, ded: 0 },
    { min: 1950000,  max: 3300000,  rate: 0.10, ded: 97500 },
    { min: 3300000,  max: 6950000,  rate: 0.20, ded: 427500 },
    { min: 6950000,  max: 9000000,  rate: 0.23, ded: 636000 },
    { min: 9000000,  max: 18000000, rate: 0.33, ded: 1536000 },
    { min: 18000000, max: 40000000, rate: 0.40, ded: 2796000 },
    { min: 40000000, max: Infinity, rate: 0.45, ded: 4796000 }
  ];

  var BRACKET_COLORS = ['#dcfce7','#bbf7d0','#86efac','#4ade80','#22c55e','#16a34a','#15803d'];

  function fmt(n) {
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }
  function fmtM(n) {
    if (n >= 100000000) return (n/100000000).toFixed(2) + '億円';
    if (n >= 10000) return Math.round(n/10000) + '万円';
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }

  window.tcCalculate = function() {
    var income = parseFloat(document.getElementById('tc-income').value) || 0;

    // 給与所得
    var kyuyoShotoku = calcKyuyoShotoku(income);

    // 基礎控除
    var kiso = 480000;
    if (income > 25000000) kiso = 0;
    else if (income > 24000000) kiso = 160000;
    else if (income > 23000000) kiso = 320000;

    // 社会保険料控除（概算：給与収入の約14.5%）
    var shakai = Math.round(income * 0.145);

    var totalDed = kiso + shakai;
    var taxable = Math.max(0, kyuyoShotoku - totalDed);

    // 課税所得を1,000円未満切り捨て
    taxable = Math.floor(taxable / 1000) * 1000;

    // 計算方式: 課税所得 × 税率 - 控除額
    var totalTax = 0;
    var breakdown = [];
    var marginalRate = 0.05;

    JP_BRACKETS.forEach(function(b, i) {
      if (taxable <= b.min) {
        breakdown.push({ rate: b.rate, ded: b.ded, label: formatLabel(b), income: 0, tax: 0, active: false });
        return;
      }
      var incomeInBracket = Math.min(taxable, b.max === Infinity ? taxable : b.max) - b.min;
      if (incomeInBracket < 0) incomeInBracket = 0;
      if (incomeInBracket > 0) marginalRate = b.rate;
      breakdown.push({ rate: b.rate, ded: b.ded, label: formatLabel(b), income: incomeInBracket, tax: incomeInBracket * b.rate, active: incomeInBracket > 0 });
    });

    // Use the standard calculation: taxable * rate - deduction for the applicable bracket
    var applicableBracket = JP_BRACKETS[0];
    JP_BRACKETS.forEach(function(b) {
      if (taxable >= b.min) applicableBracket = b;
    });
    totalTax = Math.max(0, taxable * applicableBracket.rate - applicableBracket.ded);

    var effectiveRate = income > 0 ? (totalTax / income * 100) : 0;

    document.getElementById('tc-gross-out').textContent     = fmtM(income);
    document.getElementById('tc-kyuyo-shotoku').textContent = fmtM(kyuyoShotoku);
    document.getElementById('tc-total-ded').textContent     = fmtM(totalDed);
    document.getElementById('tc-taxable-out').textContent   = fmtM(taxable);
    document.getElementById('tc-tax-out').textContent       = fmtM(totalTax);
    document.getElementById('tc-eff-out').textContent       = effectiveRate.toFixed(2) + '%';

    // Update info box
    document.getElementById('tc-info-box').innerHTML =
      '<strong>控除の内訳（概算）</strong><br>' +
      '給与所得控除: ' + fmtM(income - kyuyoShotoku) + '　／　' +
      '基礎控除: ' + fmtM(kiso) + '　／　' +
      '社会保険料控除（概算）: ' + fmtM(shakai);

    document.getElementById('tc-results').classList.remove('tc-hidden');
    document.getElementById('tc-bracket-card').classList.remove('tc-hidden');

    tcRenderBrackets(breakdown, taxable);
    tcDrawChart(breakdown);
  };

  function formatLabel(b) {
    var min = (b.min / 10000).toFixed(0) + '万円';
    var max = b.max === Infinity ? '超' : '〜' + (b.max / 10000).toFixed(0) + '万円';
    return min + max;
  }

  function tcRenderBrackets(breakdown, taxable) {
    var maxIncome = Math.max.apply(null, breakdown.map(function(b){ return b.income; }));
    var tbody = document.getElementById('tc-bracket-body');
    tbody.innerHTML = breakdown.map(function(b, i) {
      var barPct = maxIncome > 0 ? Math.round((b.income / maxIncome) * 100) : 0;
      var rowClass = b.active ? ' class="tc-active-row"' : '';
      var bar = '<span class="tc-bar-wrap"><span class="tc-bar-fill" style="width:' + barPct + '%"></span></span>';
      var dedStr = b.ded > 0 ? (b.ded / 10000).toFixed(1) + '万円' : '—';
      return '<tr' + rowClass + '>' +
        '<td>' + b.label + '</td>' +
        '<td>' + (b.rate * 100).toFixed(0) + '%</td>' +
        '<td>' + dedStr + '</td>' +
        '<td>' + (b.income > 0 ? fmtM(b.income) : '—') + '</td>' +
        '<td>' + (b.income > 0 ? fmtM(b.income * b.rate) : '—') + bar + '</td>' +
        '</tr>';
    }).join('');
  }

  function tcDrawChart(breakdown) {
    var canvas = document.getElementById('tc-chart');
    var ctx = canvas.getContext('2d');
    var W = canvas.width, H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    var active = breakdown.filter(function(b){ return b.income > 0; });
    if (active.length === 0) return;

    var maxIncome = Math.max.apply(null, active.map(function(b){ return b.income; }));
    var pad = { top: 24, right: 20, bottom: 50, left: 80 };
    var chartW = W - pad.left - pad.right;
    var chartH = H - pad.top - pad.bottom;
    var barW = Math.floor(chartW / active.length) - 10;

    ctx.fillStyle = '#f8fafc';
    ctx.fillRect(0, 0, W, H);

    ctx.strokeStyle = '#e2e8f0';
    ctx.lineWidth = 1;
    [0, 0.25, 0.5, 0.75, 1].forEach(function(f) {
      var y = pad.top + chartH * (1 - f);
      ctx.beginPath();
      ctx.moveTo(pad.left, y);
      ctx.lineTo(pad.left + chartW, y);
      ctx.stroke();
      var val = maxIncome * f;
      var label = val >= 10000 ? Math.round(val / 10000) + '万' : Math.round(val) + '';
      ctx.fillStyle = '#999';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'right';
      ctx.textBaseline = 'middle';
      ctx.fillText(label, pad.left - 4, y);
    });

    active.forEach(function(b, i) {
      var x = pad.left + i * (chartW / active.length) + 5;
      var barH = chartH * (b.income / maxIncome);
      var y = pad.top + chartH - barH;

      var grad = ctx.createLinearGradient(0, y, 0, y + barH);
      grad.addColorStop(0, BRACKET_COLORS[Math.min(i, BRACKET_COLORS.length - 1)]);
      grad.addColorStop(1, '#16a34a');
      ctx.fillStyle = grad;
      ctx.beginPath();
      if (ctx.roundRect) ctx.roundRect(x, y, barW, barH, [4,4,0,0]);
      else ctx.rect(x, y, barW, barH);
      ctx.fill();

      ctx.fillStyle = '#1a1a2e';
      ctx.font = 'bold 11px sans-serif';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'top';
      ctx.fillText((b.rate * 100).toFixed(0) + '%', x + barW / 2, pad.top + chartH + 8);

      ctx.fillStyle = '#16a34a';
      ctx.font = 'bold 10px sans-serif';
      ctx.textBaseline = 'bottom';
      var label = b.income >= 10000 ? Math.round(b.income / 10000) + '万' : Math.round(b.income) + '円';
      ctx.fillText(label, x + barW / 2, y - 2);
    });

    ctx.fillStyle = '#4a5568';
    ctx.font = '12px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'bottom';
    ctx.fillText('税率区分別の課税所得', W / 2, H);
  }

  var BRACKET_COLORS = ['#dcfce7','#bbf7d0','#86efac','#4ade80','#22c55e','#16a34a','#15803d'];
})();
</script>
</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [FXの損失は3年繰り越せる？繰越控除の申告手順を図解で解説](/ja/posts/fx-sonshitsu-kurikoshi-koujo/)
