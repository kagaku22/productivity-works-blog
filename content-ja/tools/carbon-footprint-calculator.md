---
title: "カーボンフットプリント計算ツール - あなたのCO2排出量を推定"
date: 2025-05-16
categories: ["無料ツール"]
slug: "carbon-footprint-calculator"
ShowToc: false
cover:
  image: "/images/covers/carbon-footprint-calculator.png"
---

<div id="cf-app">
<style>
#cf-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 24px 16px;
  color: #1a1a2e;
  box-sizing: border-box;
}
#cf-app *, #cf-app *::before, #cf-app *::after {
  box-sizing: inherit;
}
#cf-app h1 {
  font-size: 1.7rem;
  font-weight: 700;
  text-align: center;
  margin: 0 0 6px 0;
  color: #1a1a2e;
}
#cf-app .cf-subtitle {
  text-align: center;
  color: #555;
  margin: 0 0 32px 0;
  font-size: 0.95rem;
}
#cf-app .cf-sections {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 18px;
  margin-bottom: 28px;
}
@media (max-width: 640px) {
  #cf-app .cf-sections { grid-template-columns: 1fr; }
  #cf-app h1 { font-size: 1.25rem; }
}
#cf-app .cf-card {
  background: #fff;
  border: 1.5px solid #e0e7ff;
  border-radius: 14px;
  padding: 20px 18px;
  box-shadow: 0 2px 10px rgba(99,102,241,0.06);
}
#cf-app .cf-card-title {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 1.0rem;
  font-weight: 700;
  margin-bottom: 16px;
  color: #3730a3;
}
#cf-app .cf-card-title .cf-icon {
  font-size: 1.4rem;
}
#cf-app .cf-field {
  margin-bottom: 14px;
}
#cf-app .cf-field label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #444;
  margin-bottom: 5px;
}
#cf-app .cf-field input[type="number"] {
  width: 100%;
  padding: 8px 11px;
  border: 1.5px solid #c7d2fe;
  border-radius: 8px;
  font-size: 0.95rem;
  color: #1a1a2e;
  background: #f8f9ff;
  outline: none;
  transition: border-color 0.2s;
}
#cf-app .cf-field input[type="number"]:focus {
  border-color: #6366f1;
  background: #fff;
}
#cf-app .cf-field .cf-hint {
  font-size: 0.73rem;
  color: #888;
  margin-top: 3px;
}
#cf-app .cf-btn {
  display: block;
  width: 100%;
  padding: 14px;
  background: linear-gradient(135deg, #6366f1 0%, #22d3ee 100%);
  color: #fff;
  font-size: 1.05rem;
  font-weight: 700;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  margin: 8px 0 32px 0;
  letter-spacing: 0.04em;
  transition: opacity 0.2s, transform 0.1s;
  box-shadow: 0 4px 14px rgba(99,102,241,0.25);
}
#cf-app .cf-btn:hover { opacity: 0.92; transform: translateY(-1px); }
#cf-app .cf-btn:active { transform: translateY(0); }
#cf-app .cf-results {
  display: none;
}
#cf-app .cf-results.visible {
  display: block;
}
#cf-app .cf-total-box {
  background: linear-gradient(135deg, #1a1a2e 0%, #3730a3 100%);
  border-radius: 16px;
  padding: 28px 24px;
  text-align: center;
  color: #fff;
  margin-bottom: 24px;
  box-shadow: 0 6px 24px rgba(55,48,163,0.18);
}
#cf-app .cf-total-box .cf-total-label {
  font-size: 0.88rem;
  opacity: 0.8;
  margin-bottom: 6px;
  letter-spacing: 0.04em;
}
#cf-app .cf-total-box .cf-total-value {
  font-size: 3.2rem;
  font-weight: 800;
  line-height: 1;
  margin-bottom: 4px;
}
#cf-app .cf-total-box .cf-total-unit {
  font-size: 1.0rem;
  opacity: 0.75;
}
#cf-app .cf-total-box .cf-tree-line {
  margin-top: 14px;
  font-size: 0.87rem;
  background: rgba(255,255,255,0.12);
  border-radius: 8px;
  padding: 8px 12px;
  display: inline-block;
}
#cf-app .cf-charts-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px;
  margin-bottom: 24px;
}
@media (max-width: 600px) {
  #cf-app .cf-charts-row { grid-template-columns: 1fr; }
}
#cf-app .cf-chart-box {
  background: #fff;
  border: 1.5px solid #e0e7ff;
  border-radius: 14px;
  padding: 18px 16px;
  box-shadow: 0 2px 10px rgba(99,102,241,0.06);
}
#cf-app .cf-chart-box h3 {
  font-size: 0.85rem;
  font-weight: 700;
  color: #3730a3;
  margin: 0 0 12px 0;
  letter-spacing: 0.02em;
}
#cf-app canvas {
  width: 100% !important;
  height: auto;
}
#cf-app .cf-breakdown {
  background: #fff;
  border: 1.5px solid #e0e7ff;
  border-radius: 14px;
  padding: 20px 18px;
  margin-bottom: 24px;
  box-shadow: 0 2px 10px rgba(99,102,241,0.06);
}
#cf-app .cf-breakdown h3 {
  font-size: 0.88rem;
  font-weight: 700;
  color: #3730a3;
  margin: 0 0 14px 0;
  letter-spacing: 0.02em;
}
#cf-app .cf-bar-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}
#cf-app .cf-bar-label {
  width: 90px;
  font-size: 0.82rem;
  font-weight: 600;
  color: #444;
  flex-shrink: 0;
}
#cf-app .cf-bar-track {
  flex: 1;
  background: #f0f4ff;
  border-radius: 999px;
  height: 14px;
  overflow: hidden;
}
#cf-app .cf-bar-fill {
  height: 100%;
  border-radius: 999px;
  transition: width 0.6s ease;
}
#cf-app .cf-bar-val {
  width: 60px;
  font-size: 0.82rem;
  font-weight: 700;
  color: #1a1a2e;
  text-align: right;
  flex-shrink: 0;
}
#cf-app .cf-tips {
  background: #f0fdf4;
  border: 1.5px solid #86efac;
  border-radius: 14px;
  padding: 20px 18px;
  margin-bottom: 24px;
}
#cf-app .cf-tips h3 {
  font-size: 0.88rem;
  font-weight: 700;
  color: #15803d;
  margin: 0 0 12px 0;
  letter-spacing: 0.02em;
}
#cf-app .cf-tips ul {
  margin: 0;
  padding-left: 18px;
}
#cf-app .cf-tips ul li {
  margin-bottom: 6px;
  font-size: 0.92rem;
  color: #166534;
  line-height: 1.6;
}
#cf-app .cf-cta {
  background: #fffbeb;
  border: 1.5px solid #fbbf24;
  border-radius: 14px;
  padding: 20px 18px;
  margin-bottom: 24px;
}
#cf-app .cf-cta p {
  margin: 0;
  font-size: 0.93rem;
  color: #92400e;
  line-height: 1.6;
}
#cf-app .cf-cta a {
  color: #d97706;
  font-weight: 700;
  text-decoration: none;
}
#cf-app .cf-cta a:hover { text-decoration: underline; }
#cf-app .cf-badge-row {
  display: flex;
  gap: 10px;
  justify-content: center;
  flex-wrap: wrap;
  margin-top: 16px;
}
#cf-app .cf-badge {
  padding: 5px 12px;
  border-radius: 999px;
  font-size: 0.8rem;
  font-weight: 700;
}
#cf-app .cf-badge-you { background: #818cf8; color: #fff; }
#cf-app .cf-badge-us { background: #f87171; color: #fff; }
#cf-app .cf-badge-world { background: #fb923c; color: #fff; }
#cf-app .cf-badge-target { background: #4ade80; color: #166534; }
</style>

<h1>カーボンフットプリント計算ツール</h1>
<p class="cf-subtitle">移動・家庭エネルギー・食事の3カテゴリから、あなたの年間CO2排出量を推定します。</p>

<div class="cf-sections">
  <!-- 移動 -->
  <div class="cf-card">
    <div class="cf-card-title"><span class="cf-icon">🚗</span> 移動</div>
    <div class="cf-field">
      <label for="cf-car-km">自動車走行距離（km/年）</label>
      <input type="number" id="cf-car-km" value="8000" min="0" step="100">
      <div class="cf-hint">平均的な乗用車: 約0.21 kg CO2/km</div>
    </div>
    <div class="cf-field">
      <label for="cf-flights">飛行機の搭乗回数（回/年）</label>
      <input type="number" id="cf-flights" value="2" min="0" step="1">
      <div class="cf-hint">1フライト平均: 約0.9 t CO2</div>
    </div>
  </div>

  <!-- 家庭エネルギー -->
  <div class="cf-card">
    <div class="cf-card-title"><span class="cf-icon">🏠</span> 家庭エネルギー</div>
    <div class="cf-field">
      <label for="cf-electricity">電力使用量（kWh/年）</label>
      <input type="number" id="cf-electricity" value="3500" min="0" step="100">
      <div class="cf-hint">日本平均世帯: 約4,300 kWh</div>
    </div>
    <div class="cf-field">
      <label for="cf-gas">都市ガス使用量（kWh換算/年）</label>
      <input type="number" id="cf-gas" value="5000" min="0" step="100">
      <div class="cf-hint">日本平均世帯: 約6,500 kWh相当</div>
    </div>
  </div>

  <!-- 食事 -->
  <div class="cf-card">
    <div class="cf-card-title"><span class="cf-icon">🍽️</span> 食事</div>
    <div class="cf-field">
      <label for="cf-meat">肉類を含む食事（回/週）</label>
      <input type="number" id="cf-meat" value="7" min="0" max="21" step="1">
      <div class="cf-hint">1食あたり: 約2.5 kg CO2</div>
    </div>
    <div class="cf-field">
      <label for="cf-dairy">乳製品の摂取（回/週）</label>
      <input type="number" id="cf-dairy" value="7" min="0" max="35" step="1">
      <div class="cf-hint">1回あたり: 約0.6 kg CO2</div>
    </div>
  </div>
</div>

<button class="cf-btn" id="cf-calculate-btn" onclick="cfCalculateJA()">CO2排出量を計算する</button>

<div class="cf-results" id="cf-results">

  <div class="cf-total-box">
    <div class="cf-total-label">あなたの推定年間カーボンフットプリント</div>
    <div class="cf-total-value" id="cf-total-value">0.0</div>
    <div class="cf-total-unit">トン CO2 / 年</div>
    <div class="cf-badge-row">
      <span class="cf-badge cf-badge-you" id="cf-badge-you">あなた: 0t</span>
      <span class="cf-badge cf-badge-us">米国平均: 16t</span>
      <span class="cf-badge cf-badge-world">世界平均: 4t</span>
      <span class="cf-badge cf-badge-target">目標: 2t</span>
    </div>
    <div class="cf-tree-line" id="cf-tree-line"></div>
  </div>

  <div class="cf-charts-row">
    <div class="cf-chart-box">
      <h3>あなたの排出量 vs. 各平均値</h3>
      <canvas id="cf-bar-chart" width="360" height="240"></canvas>
    </div>
    <div class="cf-chart-box">
      <h3>カテゴリ別内訳</h3>
      <canvas id="cf-pie-chart" width="360" height="240"></canvas>
    </div>
  </div>

  <div class="cf-breakdown">
    <h3>カテゴリ別内訳</h3>
    <div class="cf-bar-row">
      <div class="cf-bar-label">移動</div>
      <div class="cf-bar-track"><div class="cf-bar-fill" id="cf-bar-transport" style="background:#6366f1; width:0%"></div></div>
      <div class="cf-bar-val" id="cf-val-transport">0 t</div>
    </div>
    <div class="cf-bar-row">
      <div class="cf-bar-label">家庭エネルギー</div>
      <div class="cf-bar-track"><div class="cf-bar-fill" id="cf-bar-home" style="background:#22d3ee; width:0%"></div></div>
      <div class="cf-bar-val" id="cf-val-home">0 t</div>
    </div>
    <div class="cf-bar-row">
      <div class="cf-bar-label">食事</div>
      <div class="cf-bar-track"><div class="cf-bar-fill" id="cf-bar-food" style="background:#f59e0b; width:0%"></div></div>
      <div class="cf-bar-val" id="cf-val-food">0 t</div>
    </div>
  </div>

  <div class="cf-tips" id="cf-tips-box">
    <h3 id="cf-tips-title">削減のヒント</h3>
    <ul id="cf-tips-list"></ul>
  </div>

  <div class="cf-cta">
    <p>環境経営を推進 &rarr; <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計でサステナビリティレポートを効率化</a></p>
  </div>

</div>

<script>
(function() {
  var EF = {
    car: 0.00021,
    flight: 0.9,
    electricity: 0.000486,
    gas: 0.000203,
    meat: 0.0025,
    dairy: 0.0006
  };

  var TIPS = {
    transport: [
      "電気自動車やハイブリッド車への切り替えで、自動車のCO2排出量を最大70%削減できます。",
      "移動をまとめ、可能な場合は公共交通機関を利用しましょう。",
      "短距離フライトを新幹線などの鉄道に変えると、排出量を約90%削減できます。",
      "出張をビデオ会議に置き換えることを検討しましょう。",
      "カープールやライドシェアを日常の通勤に取り入れましょう。"
    ],
    home: [
      "再生可能エネルギーのプランに切り替えるか、太陽光パネルの設置を検討しましょう。",
      "断熱材の強化で冷暖房のエネルギー消費を大幅に削減できます。",
      "ガス器具をヒートポンプ式エアコンやIHクッキングヒーターに変えましょう。",
      "スマートサーモスタットで、不在時の無駄な冷暖房を自動的に抑制しましょう。",
      "古い家電を省エネ型（★★★以上）の製品に買い替えましょう。"
    ],
    food: [
      "週2〜3回の肉なし食事デーを設けるだけで、年間約0.5 t CO2を削減できます。",
      "牛肉・羊肉よりも鶏肉・魚を選ぶと排出量を大幅に減らせます。",
      "食品ロスを減らしましょう。食品関連排出量の約30%はロスが原因です。",
      "地元産・旬の食材を選ぶことで、輸送に伴う排出量を削減できます。",
      "週数回、植物性ミルクなどの代替乳製品を試してみましょう。"
    ]
  };

  window.cfCalculateJA = function() {
    var carKm = parseFloat(document.getElementById('cf-car-km').value) || 0;
    var flights = parseFloat(document.getElementById('cf-flights').value) || 0;
    var electricity = parseFloat(document.getElementById('cf-electricity').value) || 0;
    var gas = parseFloat(document.getElementById('cf-gas').value) || 0;
    var meat = parseFloat(document.getElementById('cf-meat').value) || 0;
    var dairy = parseFloat(document.getElementById('cf-dairy').value) || 0;

    var tTransport = (carKm * EF.car) + (flights * EF.flight);
    var tHome = (electricity * EF.electricity) + (gas * EF.gas);
    var tFood = (meat * 52 * EF.meat) + (dairy * 52 * EF.dairy);
    var tTotal = tTransport + tHome + tFood;

    document.getElementById('cf-total-value').textContent = tTotal.toFixed(1);
    document.getElementById('cf-badge-you').textContent = 'あなた: ' + tTotal.toFixed(1) + 't';

    var trees = Math.ceil(tTotal / 0.021);
    document.getElementById('cf-tree-line').textContent =
      'このCO2を相殺するには、約 ' + trees.toLocaleString('ja-JP') + ' 本の木を1年間植林する必要があります。';

    var maxVal = Math.max(tTransport, tHome, tFood, 0.01);
    document.getElementById('cf-bar-transport').style.width = (tTransport / maxVal * 100).toFixed(1) + '%';
    document.getElementById('cf-bar-home').style.width = (tHome / maxVal * 100).toFixed(1) + '%';
    document.getElementById('cf-bar-food').style.width = (tFood / maxVal * 100).toFixed(1) + '%';
    document.getElementById('cf-val-transport').textContent = tTransport.toFixed(2) + ' t';
    document.getElementById('cf-val-home').textContent = tHome.toFixed(2) + ' t';
    document.getElementById('cf-val-food').textContent = tFood.toFixed(2) + ' t';

    drawBarChartJA(tTotal);
    drawPieChartJA(tTransport, tHome, tFood);

    var categories = [
      { key: 'transport', val: tTransport },
      { key: 'home', val: tHome },
      { key: 'food', val: tFood }
    ];
    categories.sort(function(a, b) { return b.val - a.val; });
    var topKey = categories[0].key;
    var titleMap = { transport: '移動', home: '家庭エネルギー', food: '食事' };
    document.getElementById('cf-tips-title').textContent =
      '削減のヒント: ' + titleMap[topKey] + '（最大排出カテゴリ）';
    var tipsList = document.getElementById('cf-tips-list');
    tipsList.innerHTML = '';
    TIPS[topKey].forEach(function(tip) {
      var li = document.createElement('li');
      li.textContent = tip;
      tipsList.appendChild(li);
    });

    document.getElementById('cf-results').classList.add('visible');
    document.getElementById('cf-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function drawBarChartJA(userTotal) {
    var canvas = document.getElementById('cf-bar-chart');
    var ctx = canvas.getContext('2d');
    var W = canvas.width;
    var H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    var data = [
      { label: 'あなた', value: userTotal, color: '#6366f1' },
      { label: '米国平均', value: 16, color: '#f87171' },
      { label: '世界平均', value: 4, color: '#fb923c' },
      { label: '目標値', value: 2, color: '#4ade80' }
    ];

    var maxVal = Math.max(userTotal, 16, 0.1);
    var padL = 14, padR = 14, padT = 18, padB = 44;
    var chartW = W - padL - padR;
    var chartH = H - padT - padB;
    var barW = Math.floor(chartW / data.length * 0.55);
    var gap = Math.floor(chartW / data.length);

    ctx.fillStyle = '#f8f9ff';
    ctx.fillRect(0, 0, W, H);

    ctx.strokeStyle = '#e0e7ff';
    ctx.lineWidth = 1;
    for (var i = 0; i <= 4; i++) {
      var y = padT + chartH - (chartH * i / 4);
      ctx.beginPath();
      ctx.moveTo(padL, y);
      ctx.lineTo(W - padR, y);
      ctx.stroke();
      ctx.fillStyle = '#94a3b8';
      ctx.font = '10px sans-serif';
      ctx.textAlign = 'right';
      ctx.fillText((maxVal * i / 4).toFixed(1), padL - 2, y + 4);
    }

    data.forEach(function(d, i) {
      var barH = Math.max((d.value / maxVal) * chartH, 2);
      var x = padL + i * gap + (gap - barW) / 2;
      var y = padT + chartH - barH;

      ctx.fillStyle = d.color;
      ctx.beginPath();
      ctx.roundRect ? ctx.roundRect(x, y, barW, barH, 4) : ctx.rect(x, y, barW, barH);
      ctx.fill();

      ctx.fillStyle = '#1a1a2e';
      ctx.font = 'bold 11px sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText(d.value.toFixed(1) + 't', x + barW / 2, y - 5);

      ctx.fillStyle = '#555';
      ctx.font = '10px sans-serif';
      var labelLines = d.label.length > 4 ? [d.label.slice(0,4), d.label.slice(4)] : [d.label];
      labelLines.forEach(function(line, li) {
        ctx.fillText(line, x + barW / 2, padT + chartH + 16 + li * 13);
      });
    });
  }

  function drawPieChartJA(transport, home, food) {
    var canvas = document.getElementById('cf-pie-chart');
    var ctx = canvas.getContext('2d');
    var W = canvas.width;
    var H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    ctx.fillStyle = '#f8f9ff';
    ctx.fillRect(0, 0, W, H);

    var total = transport + home + food;
    if (total <= 0) return;

    var slices = [
      { label: '移動', value: transport, color: '#6366f1' },
      { label: 'エネルギー', value: home, color: '#22d3ee' },
      { label: '食事', value: food, color: '#f59e0b' }
    ];

    var cx = W / 2;
    var cy = H / 2 - 18;
    var r = Math.min(W, H) * 0.33;
    var startAngle = -Math.PI / 2;

    slices.forEach(function(s) {
      var sliceAngle = (s.value / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, startAngle, startAngle + sliceAngle);
      ctx.closePath();
      ctx.fillStyle = s.color;
      ctx.fill();
      ctx.strokeStyle = '#fff';
      ctx.lineWidth = 2;
      ctx.stroke();

      if (s.value / total > 0.08) {
        var midAngle = startAngle + sliceAngle / 2;
        var lx = cx + Math.cos(midAngle) * r * 0.62;
        var ly = cy + Math.sin(midAngle) * r * 0.62;
        ctx.fillStyle = '#fff';
        ctx.font = 'bold 12px sans-serif';
        ctx.textAlign = 'center';
        ctx.textBaseline = 'middle';
        ctx.fillText(Math.round(s.value / total * 100) + '%', lx, ly);
      }
      startAngle += sliceAngle;
    });

    var legendY = cy + r + 14;
    var legendStartX = cx - 110;
    slices.forEach(function(s, i) {
      var lx = legendStartX + i * 74;
      ctx.fillStyle = s.color;
      ctx.fillRect(lx, legendY, 12, 12);
      ctx.fillStyle = '#444';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'left';
      ctx.textBaseline = 'top';
      ctx.fillText(s.label, lx + 15, legendY);
    });
  }
})();
</script>

</div>
