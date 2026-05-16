---
title: "住宅ローン計算ツール - 月々返済額シミュレーション"
date: 2025-05-16
description: "無料の住宅ローン計算ツール。借入額・金利・返済期間から月々の返済額・総支払額・利息総額を即座に計算。返済予定表付き。"
categories: ["無料ツール"]
slug: "mortgage-calculator"
ShowToc: false
aliases:
  - "/ja/tools/home-loan-calculator/"
  - "/ja/tools/jutaku-loan/"
cover:
  image: "/images/covers/mortgage-calculator-ja.png"
  alt: "住宅ローン計算ツール"
---

<div id="mc-app">
<style>
#mc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}
#mc-app * { box-sizing: border-box; }
#mc-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1.2rem;
  color: #1a1a2e;
  border-left: 4px solid #4f8ef7;
  padding-left: 0.7rem;
}
#mc-app .mc-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.6rem;
  margin-bottom: 1.4rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
#mc-app .mc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}
#mc-app label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #4a5568;
  margin-bottom: 0.35rem;
  letter-spacing: 0.02em;
}
#mc-app input[type=number], #mc-app select {
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
#mc-app input[type=number]:focus, #mc-app select:focus {
  border-color: #4f8ef7;
  background: #fff;
}
#mc-app .mc-btn {
  display: inline-block;
  padding: 0.7rem 2rem;
  background: linear-gradient(135deg, #4f8ef7, #3b6fd4);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 0.5rem;
  transition: opacity 0.2s;
}
#mc-app .mc-btn:hover { opacity: 0.88; }
#mc-app .mc-results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1rem;
  margin-bottom: 1.2rem;
}
#mc-app .mc-stat {
  background: #f0f5ff;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  text-align: center;
}
#mc-app .mc-stat .mc-stat-label {
  font-size: 0.75rem;
  font-weight: 600;
  color: #667eea;
  margin-bottom: 0.3rem;
}
#mc-app .mc-stat .mc-stat-value {
  font-size: 1.45rem;
  font-weight: 800;
  color: #1a1a2e;
}
#mc-app .mc-chart-row {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}
#mc-app .mc-legend {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
#mc-app .mc-legend-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.9rem;
}
#mc-app .mc-legend-dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  flex-shrink: 0;
}
#mc-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#mc-app thead th {
  background: #f0f5ff;
  color: #4f8ef7;
  font-weight: 700;
  padding: 0.6rem 0.8rem;
  text-align: right;
  border-bottom: 2px solid #e2e8f0;
}
#mc-app thead th:first-child { text-align: center; }
#mc-app tbody td {
  padding: 0.5rem 0.8rem;
  text-align: right;
  border-bottom: 1px solid #f0f0f0;
  color: #2d3748;
}
#mc-app tbody td:first-child { text-align: center; font-weight: 600; color: #667eea; }
#mc-app tbody tr:hover { background: #fafbff; }
#mc-app .mc-toggle-btn {
  display: block;
  width: 100%;
  text-align: center;
  padding: 0.55rem;
  background: #f0f5ff;
  border: 1.5px solid #4f8ef7;
  color: #4f8ef7;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  margin-top: 1rem;
  transition: background 0.2s;
}
#mc-app .mc-toggle-btn:hover { background: #e0eaff; }
#mc-app .mc-hidden { display: none; }
#mc-app .mc-note {
  font-size: 0.78rem;
  color: #888;
  margin-top: 1rem;
  line-height: 1.7;
}
#mc-app .mc-cta {
  background: linear-gradient(135deg, #f0f5ff, #e8f4fd);
  border: 1.5px solid #4f8ef7;
  border-radius: 12px;
  padding: 1.4rem 1.6rem;
  margin-top: 1.4rem;
  text-align: center;
}
#mc-app .mc-cta p {
  margin: 0 0 0.8rem;
  font-size: 0.95rem;
  color: #2d3748;
  line-height: 1.7;
}
#mc-app .mc-cta a {
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
#mc-app .mc-cta a:hover { opacity: 0.85; }
</style>

<div class="mc-card">
  <h2>ローン条件の入力</h2>
  <div class="mc-grid">
    <div>
      <label for="mc-price">物件価格（円）</label>
      <input type="number" id="mc-price" value="40000000" min="0" step="100000">
    </div>
    <div>
      <label for="mc-down">頭金（円）</label>
      <input type="number" id="mc-down" value="8000000" min="0" step="100000">
    </div>
    <div>
      <label for="mc-rate">年利（%）</label>
      <input type="number" id="mc-rate" value="1.5" min="0" max="20" step="0.01">
    </div>
    <div>
      <label for="mc-term">返済期間（年）</label>
      <select id="mc-term">
        <option value="10">10年</option>
        <option value="15">15年</option>
        <option value="20">20年</option>
        <option value="25">25年</option>
        <option value="30">30年</option>
        <option value="35" selected>35年</option>
      </select>
    </div>
  </div>
  <button class="mc-btn" onclick="mcCalculate()">計算する</button>
</div>

<div class="mc-card mc-hidden" id="mc-results">
  <h2>計算結果</h2>
  <div class="mc-results-grid">
    <div class="mc-stat">
      <div class="mc-stat-label">月々の返済額</div>
      <div class="mc-stat-value" id="mc-monthly">—</div>
    </div>
    <div class="mc-stat">
      <div class="mc-stat-label">借入金額</div>
      <div class="mc-stat-value" id="mc-principal">—</div>
    </div>
    <div class="mc-stat">
      <div class="mc-stat-label">総返済額</div>
      <div class="mc-stat-value" id="mc-total">—</div>
    </div>
    <div class="mc-stat">
      <div class="mc-stat-label">利息総額</div>
      <div class="mc-stat-value" id="mc-interest">—</div>
    </div>
  </div>
  <div class="mc-chart-row">
    <canvas id="mc-pie" width="200" height="200"></canvas>
    <div class="mc-legend">
      <div class="mc-legend-item">
        <div class="mc-legend-dot" style="background:#4f8ef7"></div>
        <span id="mc-legend-principal">元金</span>
      </div>
      <div class="mc-legend-item">
        <div class="mc-legend-dot" style="background:#f97b4f"></div>
        <span id="mc-legend-interest">利息</span>
      </div>
    </div>
  </div>
</div>

<div class="mc-card mc-hidden" id="mc-amort-card">
  <h2>返済予定表</h2>
  <div style="overflow-x:auto">
    <table>
      <thead>
        <tr>
          <th>回</th>
          <th>返済額</th>
          <th>元金分</th>
          <th>利息分</th>
          <th>残高</th>
        </tr>
      </thead>
      <tbody id="mc-amort-body"></tbody>
    </table>
  </div>
  <button class="mc-toggle-btn" id="mc-toggle-btn" onclick="mcToggleAll()">全期間を表示</button>
  <p class="mc-note">※ 元利均等返済方式による計算です。管理費・固定資産税・火災保険料等は含まれません。あくまで参考値としてご利用ください。実際のローン条件は金融機関にご確認ください。</p>
</div>

<div class="mc-cta">
  <p><strong>確定申告・会計をもっとラクに？</strong><br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow" target="_blank">freee会計</a> なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。</p>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow" target="_blank">freee会計を無料で試す</a>
</div>

<script>
(function(){
  var mcAllRows = [];
  var mcShowAll = false;

  function fmt(n) {
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }
  function fmtM(n) {
    if (n >= 100000000) return (n/100000000).toFixed(2) + '億円';
    if (n >= 10000) return (n/10000).toFixed(1) + '万円';
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }

  window.mcCalculate = function() {
    var price = parseFloat(document.getElementById('mc-price').value) || 0;
    var down  = parseFloat(document.getElementById('mc-down').value)  || 0;
    var rate  = parseFloat(document.getElementById('mc-rate').value)  || 0;
    var term  = parseInt(document.getElementById('mc-term').value)    || 35;

    var P = price - down;
    if (P <= 0) { alert('借入金額は0より大きい値を入力してください。'); return; }

    var r = rate / 100 / 12;
    var n = term * 12;
    var M;

    if (r === 0) {
      M = P / n;
    } else {
      var rn = Math.pow(1 + r, n);
      M = P * r * rn / (rn - 1);
    }

    var totalPay = M * n;
    var totalInt = totalPay - P;

    document.getElementById('mc-monthly').textContent   = fmtM(M);
    document.getElementById('mc-principal').textContent = fmtM(P);
    document.getElementById('mc-total').textContent     = fmtM(totalPay);
    document.getElementById('mc-interest').textContent  = fmtM(totalInt);
    document.getElementById('mc-legend-principal').textContent = '元金（' + fmtM(P) + '）';
    document.getElementById('mc-legend-interest').textContent  = '利息（' + fmtM(totalInt) + '）';

    document.getElementById('mc-results').classList.remove('mc-hidden');
    document.getElementById('mc-amort-card').classList.remove('mc-hidden');

    mcDrawPie(P, totalInt);
    mcBuildAmort(P, r, M, n);
  };

  function mcDrawPie(principal, interest) {
    var canvas = document.getElementById('mc-pie');
    var ctx = canvas.getContext('2d');
    var total = principal + interest;
    var cx = 100, cy = 100, R = 85;
    ctx.clearRect(0, 0, 200, 200);

    var slices = [
      { val: principal, color: '#4f8ef7' },
      { val: interest,  color: '#f97b4f' }
    ];
    var start = -Math.PI / 2;
    slices.forEach(function(s) {
      var angle = (s.val / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, R, start, start + angle);
      ctx.closePath();
      ctx.fillStyle = s.color;
      ctx.fill();
      start += angle;
    });
    ctx.beginPath();
    ctx.arc(cx, cy, 48, 0, 2 * Math.PI);
    ctx.fillStyle = '#fff';
    ctx.fill();
    ctx.fillStyle = '#1a1a2e';
    ctx.font = 'bold 13px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    var pct = ((principal / total) * 100).toFixed(1) + '%';
    ctx.fillText('元金割合', cx, cy - 9);
    ctx.fillText(pct, cx, cy + 9);
  }

  function mcBuildAmort(P, r, M, n) {
    var balance = P;
    mcAllRows = [];
    for (var i = 1; i <= n; i++) {
      var intPay  = r === 0 ? 0 : balance * r;
      var prinPay = M - intPay;
      balance -= prinPay;
      if (balance < 0) balance = 0;
      mcAllRows.push({ month: i, pay: M, prin: prinPay, int: intPay, bal: balance });
    }
    mcShowAll = false;
    document.getElementById('mc-toggle-btn').textContent = '全' + n + '回を表示';
    mcRenderAmort();
  }

  function mcRenderAmort() {
    var rows = mcShowAll ? mcAllRows : mcAllRows.slice(0, 12);
    var tbody = document.getElementById('mc-amort-body');
    tbody.innerHTML = rows.map(function(r) {
      return '<tr><td>' + r.month + '</td><td>' + fmt(r.pay) + '</td><td>' + fmt(r.prin) + '</td><td>' + fmt(r.int) + '</td><td>' + fmt(r.bal) + '</td></tr>';
    }).join('');
  }

  window.mcToggleAll = function() {
    mcShowAll = !mcShowAll;
    var btn = document.getElementById('mc-toggle-btn');
    btn.textContent = mcShowAll ? '最初の12回のみ表示' : '全' + mcAllRows.length + '回を表示';
    mcRenderAmort();
  };

  window.addEventListener('DOMContentLoaded', function(){ mcCalculate(); });
  if (document.readyState !== 'loading') { mcCalculate(); }
})();
</script>
</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

## 関連ツール

> 借金返済計算 → [借金返済計算ツール](/ja/tools/debt-payoff-calculator/)
> ローン比較 → [ローン比較ツール](/ja/tools/loan-comparison/)
> 住宅ローン借入可能額 → [住宅ローン借入可能額ツール](/ja/tools/mortgage-affordability-calculator/)

