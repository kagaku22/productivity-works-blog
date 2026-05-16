---
title: "投資リターン計算ツール - 年平均成長率(CAGR)＆トータルリターン"
date: 2025-05-16
categories: ["無料ツール"]
slug: "investment-return-calculator"
ShowToc: false
cover:
  image: "/images/covers/investment-return-calculator.png"
---

<div id="ir-app">
<style>
#ir-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Noto Sans JP', sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
}
#ir-app * { box-sizing: border-box; }
#ir-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  color: #1a1a2e;
  border-left: 4px solid #2563eb;
  padding-left: 0.6rem;
}
#ir-app .ir-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1rem;
}
@media (max-width: 600px) {
  #ir-app .ir-grid { grid-template-columns: 1fr; }
}
#ir-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.3rem;
}
#ir-app input[type="number"] {
  width: 100%;
  padding: 0.6rem 0.75rem;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.2s;
  background: #fff;
}
#ir-app input[type="number"]:focus {
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37,99,235,0.1);
}
#ir-app .ir-hint {
  font-size: 0.75rem;
  color: #6b7280;
  margin-top: 0.25rem;
}
#ir-app .ir-btn {
  display: inline-block;
  padding: 0.7rem 2rem;
  background: linear-gradient(135deg, #2563eb, #1d4ed8);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: transform 0.1s, box-shadow 0.1s;
  margin-top: 0.5rem;
}
#ir-app .ir-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 14px rgba(37,99,235,0.35);
}
#ir-app .ir-btn:active { transform: translateY(0); }
#ir-app .ir-results {
  display: none;
}
#ir-app .ir-cards {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.75rem;
  margin: 1.25rem 0;
}
@media (max-width: 700px) {
  #ir-app .ir-cards { grid-template-columns: repeat(2, 1fr); }
}
#ir-app .ir-card {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem 0.75rem;
  text-align: center;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ir-app .ir-card .ir-card-label {
  font-size: 0.75rem;
  color: #6b7280;
  margin-bottom: 0.35rem;
  font-weight: 600;
}
#ir-app .ir-card .ir-card-val {
  font-size: 1.3rem;
  font-weight: 800;
  color: #1a1a2e;
}
#ir-app .ir-card.ir-highlight .ir-card-val { color: #2563eb; }
#ir-app .ir-card.ir-green .ir-card-val { color: #059669; }
#ir-app .ir-chart-wrap {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem;
  margin-bottom: 1.25rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ir-app canvas { display: block; width: 100% !important; }
#ir-app .ir-table-wrap {
  overflow-x: auto;
  border-radius: 12px;
  border: 1.5px solid #e5e7eb;
  margin-bottom: 1.5rem;
}
#ir-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#ir-app thead th {
  background: #1e3a8a;
  color: #fff;
  padding: 0.65rem 0.85rem;
  text-align: right;
  font-weight: 700;
  white-space: nowrap;
}
#ir-app thead th:first-child { text-align: center; }
#ir-app tbody tr:nth-child(even) { background: #f0f4ff; }
#ir-app tbody tr:hover { background: #dbeafe; }
#ir-app tbody td {
  padding: 0.55rem 0.85rem;
  text-align: right;
  border-bottom: 1px solid #e5e7eb;
  white-space: nowrap;
}
#ir-app tbody td:first-child { text-align: center; font-weight: 700; }
#ir-app .ir-scenario {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1rem 1.25rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ir-app .ir-scenario h3 {
  font-size: 1rem;
  font-weight: 700;
  margin: 0 0 0.75rem;
  color: #374151;
}
#ir-app .ir-scenario-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.75rem;
}
@media (max-width: 600px) {
  #ir-app .ir-scenario-grid { grid-template-columns: 1fr; }
}
#ir-app .ir-s-card {
  border-radius: 10px;
  padding: 0.85rem 0.75rem;
  text-align: center;
}
#ir-app .ir-s-card.conservative { background: #f0fdf4; border: 1.5px solid #86efac; }
#ir-app .ir-s-card.moderate    { background: #eff6ff; border: 1.5px solid #93c5fd; }
#ir-app .ir-s-card.aggressive  { background: #fef3c7; border: 1.5px solid #fcd34d; }
#ir-app .ir-s-card .ir-s-label {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.03em;
  margin-bottom: 0.3rem;
}
#ir-app .ir-s-card.conservative .ir-s-label { color: #059669; }
#ir-app .ir-s-card.moderate    .ir-s-label { color: #2563eb; }
#ir-app .ir-s-card.aggressive  .ir-s-label { color: #d97706; }
#ir-app .ir-s-card .ir-s-rate {
  font-size: 0.8rem;
  color: #6b7280;
  margin-bottom: 0.5rem;
}
#ir-app .ir-s-card .ir-s-val {
  font-size: 1.2rem;
  font-weight: 800;
  color: #1a1a2e;
}
#ir-app .ir-cta {
  background: linear-gradient(135deg, #e0f2fe, #dbeafe);
  border: 1.5px solid #93c5fd;
  border-radius: 12px;
  padding: 1rem 1.25rem;
  margin: 1.5rem 0;
  font-size: 0.92rem;
  color: #1e3a8a;
  line-height: 1.7;
}
#ir-app .ir-cta a { color: #1d4ed8; font-weight: 700; }
#ir-app .ir-input-section {
  background: #fff;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
</style>

<h2>投資リターン計算ツール</h2>
<p style="color:#6b7280;font-size:0.92rem;margin-bottom:1rem;">投資情報を入力するだけで、最終残高・総リターン・CAGR（年平均成長率）を計算。年別推移グラフと運用シナリオ比較も確認できます。</p>

<div class="ir-input-section">
  <div class="ir-grid">
    <div>
      <label for="ir-initial">初期投資額（円）</label>
      <input type="number" id="ir-initial" value="1000000" min="0" step="10000">
      <div class="ir-hint">投資開始時の一括投資額</div>
    </div>
    <div>
      <label for="ir-monthly">毎月の積立額（円）</label>
      <input type="number" id="ir-monthly" value="30000" min="0" step="1000">
      <div class="ir-hint">毎月定期的に追加する金額</div>
    </div>
    <div>
      <label for="ir-rate">期待年利回り（%）</label>
      <input type="number" id="ir-rate" value="5" min="0" max="100" step="0.1">
      <div class="ir-hint">全世界株式インデックスの長期平均 ≈ 5〜7%</div>
    </div>
    <div>
      <label for="ir-years">運用期間（年）</label>
      <input type="number" id="ir-years" value="20" min="1" max="50" step="1">
      <div class="ir-hint">投資を継続する予定年数</div>
    </div>
  </div>
  <button class="ir-btn" onclick="irCalculate()">リターンを計算する</button>
</div>

<div class="ir-results" id="ir-results">
  <h2>計算結果</h2>
  <div class="ir-cards">
    <div class="ir-card ir-highlight">
      <div class="ir-card-label">最終残高</div>
      <div class="ir-card-val" id="ir-ending">-</div>
    </div>
    <div class="ir-card">
      <div class="ir-card-label">総投資元本</div>
      <div class="ir-card-val" id="ir-contrib">-</div>
    </div>
    <div class="ir-card ir-green">
      <div class="ir-card-label">運用収益（総額）</div>
      <div class="ir-card-val" id="ir-growth">-</div>
    </div>
    <div class="ir-card">
      <div class="ir-card-label">CAGR（年平均成長率）</div>
      <div class="ir-card-val" id="ir-cagr">-</div>
    </div>
  </div>

  <h2>資産推移グラフ</h2>
  <div class="ir-chart-wrap">
    <canvas id="ir-canvas" height="300"></canvas>
  </div>

  <h2>年別内訳</h2>
  <div class="ir-table-wrap">
    <table>
      <thead>
        <tr>
          <th>年</th>
          <th>残高</th>
          <th>投資元本</th>
          <th>運用収益</th>
          <th>収益率</th>
        </tr>
      </thead>
      <tbody id="ir-tbody"></tbody>
    </table>
  </div>

  <div class="ir-scenario">
    <h3>シナリオ比較</h3>
    <p style="font-size:0.82rem;color:#6b7280;margin:0 0 0.75rem;">同じ元本・積立額で、利回りが違うと最終残高はどう変わる？</p>
    <div class="ir-scenario-grid">
      <div class="ir-s-card conservative">
        <div class="ir-s-label">堅実型</div>
        <div class="ir-s-rate">年利 3%（債券・定期預金）</div>
        <div class="ir-s-val" id="ir-s-conservative">-</div>
      </div>
      <div class="ir-s-card moderate">
        <div class="ir-s-label">標準型</div>
        <div class="ir-s-rate">年利 5%（インデックス投資）</div>
        <div class="ir-s-val" id="ir-s-moderate">-</div>
      </div>
      <div class="ir-s-card aggressive">
        <div class="ir-s-label">積極型</div>
        <div class="ir-s-rate">年利 10%（成長株・海外ETF）</div>
        <div class="ir-s-val" id="ir-s-aggressive">-</div>
      </div>
    </div>
  </div>
</div>

> 投資の確定申告も簡単 → [freee会計で投資収益を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

<div class="ir-cta">
  <strong>投資収益の確定申告、手間がかかっていませんか？</strong><br>
  freee会計なら証券口座との連携・損益通算・申告書作成まで自動化。<br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="nofollow noopener">freee会計で投資収益を自動管理する →</a>
</div>

<script>
(function() {
  function fmt(n) {
    if (Math.abs(n) >= 1e8) return (n / 1e8).toFixed(2) + '億円';
    if (Math.abs(n) >= 1e4) return Math.round(n / 1e4) + '万円';
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }
  function fmtFull(n) {
    if (Math.abs(n) >= 1e8) {
      return (n / 1e8).toFixed(2) + '億円';
    }
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }

  function calcFutureValue(initial, monthly, annualRate, years) {
    var monthlyRate = annualRate / 100 / 12;
    var months = years * 12;
    var fv;
    if (monthlyRate === 0) {
      fv = initial + monthly * months;
    } else {
      fv = initial * Math.pow(1 + monthlyRate, months)
         + monthly * (Math.pow(1 + monthlyRate, months) - 1) / monthlyRate;
    }
    return fv;
  }

  function buildYearData(initial, monthly, annualRate, years) {
    var rows = [];
    var monthlyRate = annualRate / 100 / 12;
    var balance = initial;
    var totalContrib = initial;
    for (var y = 1; y <= years; y++) {
      for (var m = 0; m < 12; m++) {
        balance = balance * (1 + monthlyRate) + monthly;
        totalContrib += monthly;
      }
      rows.push({
        year: y,
        balance: balance,
        contributions: totalContrib,
        growth: balance - totalContrib,
        growthPct: totalContrib > 0 ? ((balance - totalContrib) / totalContrib * 100) : 0
      });
    }
    return rows;
  }

  function calcCAGR(initial, monthly, finalBalance, years) {
    var totalContrib = initial + monthly * 12 * years;
    if (totalContrib <= 0 || years <= 0) return 0;
    return (Math.pow(finalBalance / totalContrib, 1 / years) - 1) * 100;
  }

  function drawChart(rows, years) {
    var canvas = document.getElementById('ir-canvas');
    var ctx = canvas.getContext('2d');
    var dpr = window.devicePixelRatio || 1;
    var w = canvas.parentElement.clientWidth - 32;
    var h = 300;
    canvas.width = w * dpr;
    canvas.height = h * dpr;
    canvas.style.width = w + 'px';
    canvas.style.height = h + 'px';
    ctx.scale(dpr, dpr);

    var pad = { top: 20, right: 20, bottom: 40, left: 80 };
    var plotW = w - pad.left - pad.right;
    var plotH = h - pad.top - pad.bottom;
    var maxVal = rows[rows.length - 1].balance;

    ctx.clearRect(0, 0, w, h);

    // Grid lines
    ctx.strokeStyle = '#e5e7eb';
    ctx.lineWidth = 1;
    for (var i = 0; i <= 5; i++) {
      var y = pad.top + plotH - (i / 5) * plotH;
      ctx.beginPath();
      ctx.moveTo(pad.left, y);
      ctx.lineTo(pad.left + plotW, y);
      ctx.stroke();
      ctx.fillStyle = '#9ca3af';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'right';
      ctx.fillText(fmt((i / 5) * maxVal), pad.left - 6, y + 4);
    }

    // X labels
    var step = Math.ceil(years / 10);
    ctx.fillStyle = '#6b7280';
    ctx.font = '11px sans-serif';
    ctx.textAlign = 'center';
    rows.forEach(function(r, i) {
      if (r.year % step === 0 || r.year === 1) {
        var x = pad.left + (i / (rows.length - 1)) * plotW;
        ctx.fillText(r.year + '年', x, h - pad.bottom + 16);
      }
    });

    function dataX(i) { return pad.left + (i / (rows.length - 1)) * plotW; }
    function dataY(val) { return pad.top + plotH - (val / maxVal) * plotH; }

    // Contribution area
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i); var y = dataY(r.contributions);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.lineTo(dataX(rows.length - 1), pad.top + plotH);
    ctx.lineTo(dataX(0), pad.top + plotH);
    ctx.closePath();
    ctx.fillStyle = 'rgba(219,234,254,0.7)';
    ctx.fill();

    // Balance area
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i); var y = dataY(r.balance);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.lineTo(dataX(rows.length - 1), pad.top + plotH);
    ctx.lineTo(dataX(0), pad.top + plotH);
    ctx.closePath();
    ctx.fillStyle = 'rgba(37,99,235,0.15)';
    ctx.fill();

    // Balance line
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i); var y = dataY(r.balance);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.strokeStyle = '#2563eb'; ctx.lineWidth = 2.5; ctx.stroke();

    // Contribution line
    ctx.beginPath();
    rows.forEach(function(r, i) {
      var x = dataX(i); var y = dataY(r.contributions);
      i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    });
    ctx.strokeStyle = '#93c5fd'; ctx.lineWidth = 1.5;
    ctx.setLineDash([5, 4]); ctx.stroke(); ctx.setLineDash([]);

    // Legend
    var lx = pad.left + 10; var ly = pad.top + 10;
    ctx.fillStyle = '#2563eb'; ctx.fillRect(lx, ly, 16, 3);
    ctx.fillStyle = '#374151'; ctx.font = '11px sans-serif'; ctx.textAlign = 'left';
    ctx.fillText('残高', lx + 20, ly + 4);
    ctx.fillStyle = '#93c5fd'; ctx.fillRect(lx + 60, ly, 16, 3);
    ctx.fillStyle = '#374151';
    ctx.fillText('投資元本', lx + 80, ly + 4);
  }

  function fillTable(rows) {
    var tbody = document.getElementById('ir-tbody');
    tbody.innerHTML = '';
    rows.forEach(function(r) {
      var tr = document.createElement('tr');
      tr.innerHTML = '<td>' + r.year + '年</td>'
        + '<td>' + fmtFull(r.balance) + '</td>'
        + '<td>' + fmtFull(r.contributions) + '</td>'
        + '<td>' + fmtFull(r.growth) + '</td>'
        + '<td>' + (r.growthPct >= 0 ? '+' : '') + r.growthPct.toFixed(1) + '%</td>';
      tbody.appendChild(tr);
    });
  }

  window.irCalculate = function() {
    var initial = parseFloat(document.getElementById('ir-initial').value) || 0;
    var monthly = parseFloat(document.getElementById('ir-monthly').value) || 0;
    var rate    = parseFloat(document.getElementById('ir-rate').value)    || 0;
    var years   = parseInt(document.getElementById('ir-years').value)     || 1;

    var rows = buildYearData(initial, monthly, rate, years);
    var finalBal     = rows[rows.length - 1].balance;
    var totalContrib = rows[rows.length - 1].contributions;
    var totalGrowth  = finalBal - totalContrib;
    var cagr = calcCAGR(initial, monthly, finalBal, years);

    document.getElementById('ir-ending').textContent = fmtFull(finalBal);
    document.getElementById('ir-contrib').textContent = fmtFull(totalContrib);
    document.getElementById('ir-growth').textContent  = fmtFull(totalGrowth);
    document.getElementById('ir-cagr').textContent    = cagr.toFixed(2) + '%';

    // Scenarios (JP rates: 3 / 5 / 10)
    var sRates = { conservative: 3, moderate: 5, aggressive: 10 };
    Object.keys(sRates).forEach(function(key) {
      var fv = calcFutureValue(initial, monthly, sRates[key], years);
      document.getElementById('ir-s-' + key).textContent = fmtFull(fv);
    });

    fillTable(rows);
    document.getElementById('ir-results').style.display = 'block';
    setTimeout(function() { drawChart(rows, years); }, 50);
  };

  window.addEventListener('DOMContentLoaded', function() { irCalculate(); });
  if (document.readyState !== 'loading') { irCalculate(); }
})();
</script>

</div>

---

## 関連ツール

> 貯蓄目標シミュレーター → [貯蓄目標シミュレーターツール](/ja/tools/chochiku-mokuhyo-simulator/)
> 複利計算 → [複利計算ツール](/ja/tools/compound-interest-calculator/)
> FIRE計算 → [FIRE計算ツール](/ja/tools/fire-calculator/)

