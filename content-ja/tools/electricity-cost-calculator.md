---
title: "電気代計算シミュレーター - 家電ごとの電気代を簡単計算"
date: 2025-05-16
description: "家電ごとの消費電力・使用時間を入力するだけで月々の電気代を自動計算。円グラフで内訳も一目瞭然。エアコン・冷蔵庫・テレビなどのプリセット付き無料ツール。"
categories: ["無料ツール"]
slug: "electricity-cost-calculator"
ShowToc: false
cover:
  image: "/images/covers/electricity-cost-calculator.png"
  alt: "電気代計算シミュレーター"
---

<style>
#ec-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", "Yu Gothic", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}
#ec-app * { box-sizing: border-box; }
#ec-app h2 {
  font-size: 1.2rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  color: #1a1a2e;
}
#ec-app .ec-intro {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1.5rem;
  font-size: 0.97rem;
  line-height: 1.7;
}
#ec-app .ec-rate-row {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  background: #f0f4ff;
  border: 1.5px solid #c7d2fe;
  border-radius: 10px;
  padding: 0.85rem 1.1rem;
  margin-bottom: 1.25rem;
  flex-wrap: wrap;
}
#ec-app .ec-rate-row label {
  font-weight: 600;
  font-size: 0.95rem;
  color: #3730a3;
  white-space: nowrap;
}
#ec-app .ec-rate-row input {
  width: 110px;
  padding: 0.45rem 0.65rem;
  border: 1.5px solid #a5b4fc;
  border-radius: 7px;
  font-size: 1rem;
  background: #fff;
  color: #1a1a2e;
  outline: none;
  transition: border-color 0.2s;
}
#ec-app .ec-rate-row input:focus { border-color: #6366f1; }
#ec-app .ec-rate-row span { font-size: 0.9rem; color: #6366f1; font-weight: 500; }

#ec-app .ec-presets { margin-bottom: 1.25rem; }
#ec-app .ec-presets-title {
  font-size: 0.85rem;
  font-weight: 600;
  color: #6b7280;
  margin-bottom: 0.5rem;
  letter-spacing: 0.02em;
}
#ec-app .ec-preset-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.45rem;
}
#ec-app .ec-preset-btn {
  background: #fff;
  border: 1.5px solid #e0e7ff;
  border-radius: 20px;
  padding: 0.35rem 0.85rem;
  font-size: 0.85rem;
  cursor: pointer;
  color: #4f46e5;
  font-weight: 500;
  transition: background 0.15s, border-color 0.15s;
}
#ec-app .ec-preset-btn:hover {
  background: #eef2ff;
  border-color: #6366f1;
}

#ec-app .ec-add-form {
  background: #f9fafb;
  border: 1.5px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.1rem 1.25rem;
  margin-bottom: 1.25rem;
}
#ec-app .ec-add-form .ec-form-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 0.6rem;
  align-items: end;
}
@media (max-width: 600px) {
  #ec-app .ec-add-form .ec-form-grid {
    grid-template-columns: 1fr 1fr;
  }
}
#ec-app .ec-form-group { display: flex; flex-direction: column; gap: 0.3rem; }
#ec-app .ec-form-group label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #6b7280;
}
#ec-app .ec-form-group input {
  padding: 0.5rem 0.7rem;
  border: 1.5px solid #d1d5db;
  border-radius: 7px;
  font-size: 0.97rem;
  background: #fff;
  color: #1a1a2e;
  outline: none;
  transition: border-color 0.2s;
}
#ec-app .ec-form-group input:focus { border-color: #6366f1; }
#ec-app .ec-add-btn {
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0.55rem 1.2rem;
  font-size: 0.97rem;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.2s;
  white-space: nowrap;
  margin-top: 0.6rem;
}
#ec-app .ec-add-btn:hover { opacity: 0.88; }

#ec-app .ec-table-wrap {
  overflow-x: auto;
  border-radius: 10px;
  border: 1.5px solid #e5e7eb;
  margin-bottom: 1.5rem;
}
#ec-app .ec-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.93rem;
}
#ec-app .ec-table th {
  background: #f3f4f6;
  padding: 0.65rem 0.9rem;
  text-align: left;
  font-size: 0.8rem;
  font-weight: 700;
  color: #6b7280;
  white-space: nowrap;
}
#ec-app .ec-table td {
  padding: 0.6rem 0.9rem;
  border-top: 1px solid #f0f0f0;
  vertical-align: middle;
}
#ec-app .ec-table tr:hover td { background: #f9fafb; }
#ec-app .ec-table .ec-color-dot {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin-right: 6px;
  vertical-align: middle;
}
#ec-app .ec-del-btn {
  background: none;
  border: none;
  color: #ef4444;
  cursor: pointer;
  font-size: 1.1rem;
  padding: 0.1rem 0.4rem;
  border-radius: 5px;
  transition: background 0.15s;
}
#ec-app .ec-del-btn:hover { background: #fee2e2; }
#ec-app .ec-empty {
  text-align: center;
  color: #9ca3af;
  padding: 2rem;
  font-size: 0.95rem;
}

#ec-app .ec-summary {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
  gap: 1rem;
  margin-bottom: 1.5rem;
}
#ec-app .ec-summary-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  border-radius: 12px;
  padding: 1.1rem 1.25rem;
  text-align: center;
}
#ec-app .ec-summary-card.green {
  background: linear-gradient(135deg, #11998e, #38ef7d);
}
#ec-app .ec-summary-card.orange {
  background: linear-gradient(135deg, #f7971e, #ffd200);
  color: #1a1a2e;
}
#ec-app .ec-summary-card .ec-card-label {
  font-size: 0.82rem;
  font-weight: 600;
  opacity: 0.85;
  margin-bottom: 0.35rem;
}
#ec-app .ec-summary-card .ec-card-value {
  font-size: 1.7rem;
  font-weight: 800;
  line-height: 1.1;
}
#ec-app .ec-summary-card .ec-card-sub {
  font-size: 0.78rem;
  opacity: 0.75;
  margin-top: 0.2rem;
}

#ec-app .ec-chart-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  align-items: start;
  margin-bottom: 1.5rem;
}
@media (max-width: 600px) {
  #ec-app .ec-chart-section { grid-template-columns: 1fr; }
}
#ec-app canvas { display: block; max-width: 100%; }
#ec-app .ec-legend { list-style: none; padding: 0; margin: 0; }
#ec-app .ec-legend li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.9rem;
  margin-bottom: 0.45rem;
  color: #374151;
}
#ec-app .ec-legend-dot {
  width: 12px;
  height: 12px;
  border-radius: 3px;
  flex-shrink: 0;
}
#ec-app .ec-legend-pct {
  margin-left: auto;
  font-weight: 700;
  color: #4f46e5;
}

#ec-app .ec-tips {
  background: #f0fdf4;
  border: 1.5px solid #bbf7d0;
  border-radius: 12px;
  padding: 1.1rem 1.25rem;
  margin-bottom: 1.5rem;
}
#ec-app .ec-tips h3 {
  margin: 0 0 0.7rem;
  font-size: 1rem;
  font-weight: 700;
  color: #15803d;
}
#ec-app .ec-tips ul { margin: 0; padding-left: 1.25rem; }
#ec-app .ec-tips li {
  font-size: 0.92rem;
  color: #166534;
  margin-bottom: 0.35rem;
  line-height: 1.6;
}

#ec-app .ec-cta {
  background: #fffbeb;
  border: 1.5px solid #fde68a;
  border-radius: 12px;
  padding: 1rem 1.25rem;
  font-size: 0.95rem;
  color: #92400e;
  line-height: 1.6;
}
#ec-app .ec-cta a { color: #d97706; font-weight: 600; }
</style>

<div id="ec-app">

<div class="ec-intro">
  家電の消費電力・使用時間・使用日数を入力するだけで、月々の電気代と年間電気代を自動計算します。エアコン・冷蔵庫・テレビなどのプリセットも用意しています。
</div>

<h2>電気料金単価の設定</h2>
<div class="ec-rate-row">
  <label for="ec-rate">1kWhあたりの単価：</label>
  <input type="number" id="ec-rate" value="31" min="1" step="0.5">
  <span>円/kWh &nbsp;（検針票または電力会社のWebで確認できます）</span>
</div>

<h2>家電を追加する</h2>
<div class="ec-presets">
  <div class="ec-presets-title">プリセットから追加</div>
  <div class="ec-preset-grid" id="ec-preset-grid"></div>
</div>

<div class="ec-add-form">
  <div class="ec-form-grid">
    <div class="ec-form-group">
      <label for="ec-name">家電名</label>
      <input type="text" id="ec-name" placeholder="例：リビングのエアコン">
    </div>
    <div class="ec-form-group">
      <label for="ec-watts">消費電力（W）</label>
      <input type="number" id="ec-watts" placeholder="例：900" min="0" step="1">
    </div>
    <div class="ec-form-group">
      <label for="ec-hours">1日の使用時間</label>
      <input type="number" id="ec-hours" placeholder="例：8" min="0" max="24" step="0.5">
    </div>
    <div class="ec-form-group">
      <label for="ec-days">1ヶ月の使用日数</label>
      <input type="number" id="ec-days" placeholder="例：30" min="1" max="31" step="1" value="30">
    </div>
  </div>
  <button class="ec-add-btn" onclick="ecAddAppliance()">＋ 追加する</button>
</div>

<h2>登録した家電一覧</h2>
<div class="ec-table-wrap">
  <table class="ec-table">
    <thead>
      <tr>
        <th>家電名</th>
        <th>消費電力(W)</th>
        <th>時間/日</th>
        <th>日数/月</th>
        <th>kWh/月</th>
        <th>電気代/月</th>
        <th>電気代/年</th>
        <th></th>
      </tr>
    </thead>
    <tbody id="ec-tbody">
      <tr><td colspan="8" class="ec-empty">家電がまだ登録されていません。プリセットまたは手動で追加してください。</td></tr>
    </tbody>
  </table>
</div>

<div class="ec-summary" id="ec-summary">
  <div class="ec-summary-card">
    <div class="ec-card-label">合計使用量（月）</div>
    <div class="ec-card-value" id="ec-total-kwh">0</div>
    <div class="ec-card-sub">kWh / 月</div>
  </div>
  <div class="ec-summary-card green">
    <div class="ec-card-label">月の電気代（概算）</div>
    <div class="ec-card-value" id="ec-total-monthly">¥0</div>
    <div class="ec-card-sub">月額合計</div>
  </div>
  <div class="ec-summary-card orange">
    <div class="ec-card-label">年間電気代（概算）</div>
    <div class="ec-card-value" id="ec-total-yearly">¥0</div>
    <div class="ec-card-sub">年間合計</div>
  </div>
</div>

<h2>家電別コスト内訳</h2>
<div class="ec-chart-section">
  <canvas id="ec-pie" width="260" height="260"></canvas>
  <ul class="ec-legend" id="ec-legend">
    <li style="color:#9ca3af">家電を追加すると内訳が表示されます</li>
  </ul>
</div>

<div class="ec-tips">
  <h3>電気代を節約するためのコツ</h3>
  <ul>
    <li><strong>エアコンの設定温度を見直す</strong> — 冷房は28℃、暖房は20℃を目安に。1℃変えるだけで約10%の節電効果があると言われています。</li>
    <li><strong>冷蔵庫の設定を「中」に</strong> — 季節に合わせて設定温度を調整。詰め込みすぎると効率が下がります。</li>
    <li><strong>待機電力をカット</strong> — テレビやゲーム機などの主電源をオフに。スマートタップを使うと便利です。</li>
    <li><strong>LED照明に切り替える</strong> — 白熱電球と比べて約80%省エネ。寿命も40倍以上。</li>
    <li><strong>洗濯は「まとめ洗い」</strong> — 回数を減らすだけで水道代・電気代の両方を節約できます。</li>
    <li><strong>電力自由化を活用</strong> — 電力会社を比較・乗り換えで年間数千円〜1万円以上の節約ができる場合があります。</li>
    <li><strong>太陽光発電の検討</strong> — 初期費用はかかりますが、自家消費で電気代を大幅に削減できます。</li>
  </ul>
</div>

<div class="ec-cta">
  家計の経費管理を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で家計簿を自動管理</a>
</div>

<script>
(function() {
  var COLORS = [
    '#6366f1','#8b5cf6','#ec4899','#f59e0b','#10b981',
    '#3b82f6','#ef4444','#14b8a6','#f97316','#84cc16',
    '#06b6d4','#a855f7','#eab308','#22c55e','#e11d48'
  ];

  var PRESETS = [
    { name: "エアコン（冷房）", watts: 900, hours: 8, days: 22 },
    { name: "エアコン（暖房）", watts: 1000, hours: 6, days: 20 },
    { name: "冷蔵庫", watts: 40, hours: 24, days: 30 },
    { name: "テレビ（50型）", watts: 100, hours: 4, days: 30 },
    { name: "洗濯機", watts: 500, hours: 1, days: 15 },
    { name: "乾燥機", watts: 1200, hours: 1, days: 12 },
    { name: "電子レンジ", watts: 1000, hours: 0.25, days: 30 },
    { name: "炊飯器", watts: 900, hours: 0.5, days: 30 },
    { name: "食洗機", watts: 1000, hours: 1, days: 20 },
    { name: "デスクトップPC", watts: 200, hours: 8, days: 22 },
    { name: "ノートPC", watts: 45, hours: 8, days: 22 },
    { name: "LED照明（1灯）", watts: 10, hours: 5, days: 30 },
    { name: "電気ケトル", watts: 1300, hours: 0.1, days: 30 },
    { name: "温水洗浄便座", watts: 25, hours: 24, days: 30 },
    { name: "電気温水器", watts: 3000, hours: 2, days: 30 }
  ];

  var appliances = [];

  function init() {
    var grid = document.getElementById('ec-preset-grid');
    PRESETS.forEach(function(p) {
      var btn = document.createElement('button');
      btn.className = 'ec-preset-btn';
      btn.textContent = p.name;
      btn.onclick = function() { ecFillPreset(p); };
      grid.appendChild(btn);
    });
    render();
  }

  window.ecFillPreset = function(p) {
    document.getElementById('ec-name').value = p.name;
    document.getElementById('ec-watts').value = p.watts;
    document.getElementById('ec-hours').value = p.hours;
    document.getElementById('ec-days').value = p.days;
  };

  window.ecAddAppliance = function() {
    var name = document.getElementById('ec-name').value.trim();
    var watts = parseFloat(document.getElementById('ec-watts').value);
    var hours = parseFloat(document.getElementById('ec-hours').value);
    var days = parseFloat(document.getElementById('ec-days').value);
    if (!name) { alert('家電名を入力してください。'); return; }
    if (isNaN(watts) || watts < 0) { alert('消費電力を正しく入力してください。'); return; }
    if (isNaN(hours) || hours < 0) { alert('使用時間を正しく入力してください。'); return; }
    if (isNaN(days) || days < 1) { alert('使用日数を正しく入力してください。'); return; }
    appliances.push({ name: name, watts: watts, hours: hours, days: days, color: COLORS[appliances.length % COLORS.length] });
    document.getElementById('ec-name').value = '';
    document.getElementById('ec-watts').value = '';
    document.getElementById('ec-hours').value = '';
    document.getElementById('ec-days').value = '30';
    render();
  };

  window.ecRemove = function(i) {
    appliances.splice(i, 1);
    appliances.forEach(function(a, idx) { a.color = COLORS[idx % COLORS.length]; });
    render();
  };

  function getRate() {
    return parseFloat(document.getElementById('ec-rate').value) || 31;
  }

  function calcKwh(a) {
    return (a.watts / 1000) * a.hours * a.days;
  }

  function fmtJpy(n) { return '¥' + Math.round(n).toLocaleString('ja-JP'); }

  function render() {
    var rate = getRate();
    var tbody = document.getElementById('ec-tbody');

    if (appliances.length === 0) {
      tbody.innerHTML = '<tr><td colspan="8" class="ec-empty">家電がまだ登録されていません。プリセットまたは手動で追加してください。</td></tr>';
      document.getElementById('ec-total-kwh').textContent = '0';
      document.getElementById('ec-total-monthly').textContent = '¥0';
      document.getElementById('ec-total-yearly').textContent = '¥0';
      document.getElementById('ec-legend').innerHTML = '<li style="color:#9ca3af">家電を追加すると内訳が表示されます</li>';
      drawPie([]);
      return;
    }

    var totalKwh = 0, totalMonth = 0;
    var rows = appliances.map(function(a, i) {
      var kwh = calcKwh(a);
      var costM = kwh * rate;
      var costY = costM * 12;
      totalKwh += kwh;
      totalMonth += costM;
      return '<tr>' +
        '<td><span class="ec-color-dot" style="background:' + a.color + '"></span>' + escHtml(a.name) + '</td>' +
        '<td>' + a.watts + 'W</td>' +
        '<td>' + a.hours + 'h</td>' +
        '<td>' + a.days + '日</td>' +
        '<td>' + kwh.toFixed(1) + '</td>' +
        '<td>' + fmtJpy(costM) + '</td>' +
        '<td>' + fmtJpy(costY) + '</td>' +
        '<td><button class="ec-del-btn" onclick="ecRemove(' + i + ')" title="削除">&#10005;</button></td>' +
        '</tr>';
    });

    tbody.innerHTML = rows.join('');
    document.getElementById('ec-total-kwh').textContent = totalKwh.toFixed(1);
    document.getElementById('ec-total-monthly').textContent = fmtJpy(totalMonth);
    document.getElementById('ec-total-yearly').textContent = fmtJpy(totalMonth * 12);

    var legend = document.getElementById('ec-legend');
    legend.innerHTML = appliances.map(function(a) {
      var kwh = calcKwh(a);
      var pct = totalKwh > 0 ? (kwh / totalKwh * 100).toFixed(1) : '0.0';
      return '<li>' +
        '<span class="ec-legend-dot" style="background:' + a.color + '"></span>' +
        escHtml(a.name) +
        '<span class="ec-legend-pct">' + pct + '%</span>' +
        '</li>';
    }).join('');

    drawPie(appliances.map(function(a) { return { label: a.name, value: calcKwh(a), color: a.color }; }));
  }

  function drawPie(data) {
    var canvas = document.getElementById('ec-pie');
    var ctx = canvas.getContext('2d');
    var W = canvas.width, H = canvas.height;
    ctx.clearRect(0, 0, W, H);

    var total = data.reduce(function(s, d) { return s + d.value; }, 0);
    if (total === 0 || data.length === 0) {
      ctx.beginPath();
      ctx.arc(W/2, H/2, W/2 - 10, 0, Math.PI*2);
      ctx.fillStyle = '#f3f4f6';
      ctx.fill();
      ctx.fillStyle = '#9ca3af';
      ctx.font = '13px sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText('データなし', W/2, H/2 + 5);
      return;
    }

    var startAngle = -Math.PI / 2;
    var cx = W/2, cy = H/2, r = W/2 - 10;
    data.forEach(function(d) {
      var slice = (d.value / total) * Math.PI * 2;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, startAngle, startAngle + slice);
      ctx.closePath();
      ctx.fillStyle = d.color;
      ctx.fill();
      ctx.strokeStyle = '#fff';
      ctx.lineWidth = 2;
      ctx.stroke();
      startAngle += slice;
    });

    ctx.beginPath();
    ctx.arc(cx, cy, r * 0.42, 0, Math.PI*2);
    ctx.fillStyle = '#fff';
    ctx.fill();
    ctx.fillStyle = '#374151';
    ctx.font = 'bold 12px sans-serif';
    ctx.textAlign = 'center';
    ctx.fillText('月間kWh', cx, cy - 6);
    ctx.font = 'bold 16px sans-serif';
    ctx.fillStyle = '#4f46e5';
    var totalKwh = data.reduce(function(s,d){return s+d.value;},0);
    ctx.fillText(totalKwh.toFixed(1), cx, cy + 14);
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  document.getElementById('ec-rate').addEventListener('input', render);

  init();
})();
</script>

</div>
