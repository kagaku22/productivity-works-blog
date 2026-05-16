---
title: "電気代計算ツール｜家電の消費電力から月額料金を自動計算【無料】"
date: 2025-05-16
description: "無料の電気代計算ツール。家電ごとの消費電力から日額・月額・年額の電気代を計算。複数機器対応、省エネ比較機能付き。"
categories: ["無料ツール"]
slug: "electricity-calculator"
ShowToc: false
cover:
  image: "/images/covers/electricity-calculator-ja.png"
  alt: "電気代計算ツール"
---

<div id="ec-app">

<style>
#ec-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1e293b;
}
#ec-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  color: #0f172a;
  margin: 28px 0 14px;
  padding-bottom: 6px;
  border-bottom: 2px solid #e2e8f0;
}
#ec-app .ec-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 16px;
}
#ec-app .ec-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: flex-end;
  margin-bottom: 10px;
}
#ec-app .ec-field {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex: 1 1 140px;
}
#ec-app .ec-field label {
  font-size: 12px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}
#ec-app .ec-field input,
#ec-app .ec-field select {
  padding: 9px 11px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  color: #1e293b;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
  width: 100%;
  box-sizing: border-box;
}
#ec-app .ec-field input:focus,
#ec-app .ec-field select:focus {
  border-color: #0284c7;
}
#ec-app .ec-btn {
  padding: 9px 16px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#ec-app .ec-btn:active { transform: scale(0.97); }
#ec-app .ec-btn-primary {
  background: #0284c7;
  color: #fff;
}
#ec-app .ec-btn-primary:hover { background: #0369a1; }
#ec-app .ec-btn-danger {
  background: #fee2e2;
  color: #b91c1c;
}
#ec-app .ec-btn-danger:hover { background: #fecaca; }
#ec-app .ec-btn-secondary {
  background: #e2e8f0;
  color: #334155;
}
#ec-app .ec-btn-secondary:hover { background: #cbd5e1; }
#ec-app .ec-device-list {
  margin: 0 0 14px;
  padding: 0;
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
#ec-app .ec-device-item {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 10px;
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 10px 14px;
}
#ec-app .ec-device-item span.ec-device-name {
  font-weight: 600;
  font-size: 14px;
  flex: 1 1 120px;
  color: #0f172a;
}
#ec-app .ec-device-item span.ec-device-detail {
  font-size: 13px;
  color: #64748b;
  flex: 2 1 180px;
}
#ec-app .ec-device-item span.ec-device-cost {
  font-size: 14px;
  font-weight: 700;
  color: #0284c7;
  flex: 1 1 90px;
  text-align: right;
}
#ec-app .ec-results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 12px;
  margin-bottom: 18px;
}
#ec-app .ec-result-box {
  background: #fff;
  border: 1.5px solid #bae6fd;
  border-radius: 10px;
  padding: 16px;
  text-align: center;
}
#ec-app .ec-result-box .ec-result-label {
  font-size: 12px;
  color: #64748b;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 6px;
}
#ec-app .ec-result-box .ec-result-value {
  font-size: 1.6rem;
  font-weight: 800;
  color: #0369a1;
  line-height: 1.1;
}
#ec-app .ec-result-box .ec-result-unit {
  font-size: 13px;
  color: #94a3b8;
  margin-top: 2px;
}
#ec-app .ec-chart-wrap {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 18px;
}
#ec-app canvas#ec-chart {
  width: 100% !important;
  height: 220px !important;
  display: block;
}
#ec-app .ec-tips {
  background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
  border: 1.5px solid #bbf7d0;
  border-radius: 10px;
  padding: 16px 20px;
  margin-bottom: 18px;
}
#ec-app .ec-tips h3 {
  font-size: 14px;
  font-weight: 700;
  color: #15803d;
  margin: 0 0 10px;
}
#ec-app .ec-tips ul {
  margin: 0;
  padding-left: 18px;
  font-size: 13px;
  color: #166534;
  line-height: 1.8;
}
#ec-app .ec-preset-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 14px;
}
#ec-app .ec-preset-btn {
  padding: 6px 13px;
  border: 1.5px solid #cbd5e1;
  border-radius: 20px;
  background: #fff;
  font-size: 12px;
  font-weight: 600;
  color: #334155;
  cursor: pointer;
  transition: all 0.15s;
  white-space: nowrap;
}
#ec-app .ec-preset-btn:hover {
  border-color: #0284c7;
  color: #0284c7;
  background: #f0f9ff;
}
#ec-app .ec-rate-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 18px;
  flex-wrap: wrap;
}
#ec-app .ec-rate-row label {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  white-space: nowrap;
}
#ec-app .ec-rate-row input {
  padding: 8px 11px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  width: 100px;
  outline: none;
  color: #1e293b;
  background: #fff;
  transition: border-color 0.15s;
}
#ec-app .ec-rate-row input:focus { border-color: #0284c7; }
#ec-app .ec-rate-row span { font-size: 13px; color: #64748b; }
#ec-app .ec-empty {
  text-align: center;
  padding: 24px;
  color: #94a3b8;
  font-size: 14px;
}
#ec-app .ec-total-bar {
  background: linear-gradient(90deg, #0284c7 0%, #0369a1 100%);
  color: #fff;
  border-radius: 10px;
  padding: 14px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 18px;
}
#ec-app .ec-total-bar .ec-total-label {
  font-size: 14px;
  font-weight: 700;
  opacity: 0.9;
}
#ec-app .ec-total-bar .ec-total-value {
  font-size: 1.5rem;
  font-weight: 800;
}
@media (max-width: 520px) {
  #ec-app .ec-result-box .ec-result-value { font-size: 1.3rem; }
  #ec-app .ec-total-bar .ec-total-value { font-size: 1.2rem; }
}
</style>

<h2>電気代計算ツール</h2>
<p style="font-size:14px;color:#64748b;margin-bottom:20px;">家電の消費電力・使用時間を入力して、日額・月額・年額の電気代を計算できます。複数機器をまとめて管理。</p>

<!-- 電力単価設定 -->
<div class="ec-card">
  <div style="font-size:14px;font-weight:700;color:#0f172a;margin-bottom:12px;">電力単価の設定</div>
  <div class="ec-rate-row">
    <label for="ec-rate">電力単価：</label>
    <input type="number" id="ec-rate" value="31" min="1" max="999" step="0.1">
    <span>円 / kWh（目安：全国平均 約31円）</span>
  </div>
</div>

<!-- 機器追加フォーム -->
<div class="ec-card">
  <div style="font-size:14px;font-weight:700;color:#0f172a;margin-bottom:10px;">家電・機器を追加</div>

  <div style="font-size:12px;color:#64748b;margin-bottom:8px;font-weight:600;">よく使われる機器をワンクリックで追加：</div>
  <div class="ec-preset-row" id="ec-presets"></div>

  <div class="ec-row">
    <div class="ec-field" style="flex:2 1 160px;">
      <label for="ec-name">機器名</label>
      <input type="text" id="ec-name" placeholder="例：エアコン（リビング）">
    </div>
    <div class="ec-field">
      <label for="ec-watts">消費電力（W）</label>
      <input type="number" id="ec-watts" placeholder="例：1500" min="0" step="0.1">
    </div>
    <div class="ec-field">
      <label for="ec-hours">1日の使用時間（時間）</label>
      <input type="number" id="ec-hours" placeholder="例：8" min="0" max="24" step="0.1">
    </div>
    <div style="flex:0 0 auto;">
      <button class="ec-btn ec-btn-primary" onclick="ecAddDevice()">追加</button>
    </div>
  </div>
  <div id="ec-form-error" style="color:#b91c1c;font-size:13px;min-height:18px;"></div>
</div>

<!-- 機器リスト -->
<h2>登録した機器一覧</h2>
<ul class="ec-device-list" id="ec-device-list">
  <li class="ec-empty" id="ec-empty-msg">まだ機器が追加されていません。上のフォームから追加してください。</li>
</ul>

<!-- 合計 -->
<div id="ec-total-section" style="display:none;">
  <div class="ec-total-bar">
    <span class="ec-total-label">月額電気代（合計）</span>
    <span class="ec-total-value" id="ec-total-monthly">¥0</span>
  </div>

  <!-- 結果グリッド -->
  <div class="ec-results-grid">
    <div class="ec-result-box">
      <div class="ec-result-label">日額</div>
      <div class="ec-result-value" id="ec-res-daily">¥0</div>
      <div class="ec-result-unit">円 / 日</div>
    </div>
    <div class="ec-result-box">
      <div class="ec-result-label">月額（30日）</div>
      <div class="ec-result-value" id="ec-res-monthly">¥0</div>
      <div class="ec-result-unit">円 / 月</div>
    </div>
    <div class="ec-result-box">
      <div class="ec-result-label">年額</div>
      <div class="ec-result-value" id="ec-res-yearly">¥0</div>
      <div class="ec-result-unit">円 / 年</div>
    </div>
    <div class="ec-result-box">
      <div class="ec-result-label">消費電力合計</div>
      <div class="ec-result-value" id="ec-res-kwh">0.0</div>
      <div class="ec-result-unit">kWh / 日</div>
    </div>
  </div>

  <!-- 機器別グラフ -->
  <div class="ec-chart-wrap">
    <div style="font-size:13px;font-weight:700;color:#0f172a;margin-bottom:10px;">機器別 月額電気代（円）</div>
    <canvas id="ec-chart"></canvas>
  </div>

  <!-- 省エネtips -->
  <div class="ec-tips" id="ec-tips-box">
    <h3>省エネのヒント</h3>
    <ul id="ec-tips-list"></ul>
  </div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の経費・光熱費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<!-- クロスリンク -->
<div style="margin-top:24px;padding:16px 20px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;font-size:13px;color:#475569;line-height:2;">

> 投資利益率を計算 → <a href="/ja/tools/roi-calculator/">ROI計算ツール</a><br>
> 家計を見直す → <a href="/ja/tools/budget-calculator/">50/30/20 家計バランス計算</a><br>
> ローン返済を計算 → <a href="/ja/tools/loan-emi-calculator/">ローン返済シミュレーター</a>

</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

<script>
(function() {
  'use strict';

  // ---- State ----
  var devices = [];
  var nextId = 1;

  var PRESETS = [
    { name: 'ノートPC', watts: 65 },
    { name: 'デスクトップPC', watts: 300 },
    { name: 'テレビ', watts: 100 },
    { name: '冷蔵庫', watts: 150 },
    { name: 'エアコン', watts: 1500 },
    { name: '電子レンジ', watts: 1000 },
    { name: '洗濯機', watts: 500 },
    { name: '食洗機', watts: 800 },
    { name: 'LED照明', watts: 10 },
    { name: '掃除機', watts: 1000 },
  ];

  var TIPS_RULES = [
    {
      check: function(d) { return d.watts >= 1000 && d.hours >= 4; },
      tip: function(d) { return '「' + d.name + '」の使用時間を1時間減らすと月約' + fmt(d.watts / 1000 * 1 * 30 * getRate()) + '円の節約になります。'; }
    },
    {
      check: function(d) { return d.name.indexOf('エアコン') !== -1; },
      tip: function() { return 'エアコンは設定温度を1℃変えるだけで約10%の節電効果があります。'; }
    },
    {
      check: function(d) { return d.name.indexOf('冷蔵庫') !== -1; },
      tip: function() { return '冷蔵庫は壁から適切な距離を保ち、詰めすぎないことで効率が上がります。'; }
    },
    {
      check: function(d) { return d.name.indexOf('テレビ') !== -1 && d.hours >= 6; },
      tip: function() { return 'テレビの輝度を下げると消費電力を最大30%削減できます。'; }
    },
    {
      check: function(d) { return d.watts >= 500 && d.name.indexOf('照明') === -1; },
      tip: function(d) { return '「' + d.name + '」はスマートプラグで自動オフにすると待機電力を削減できます。'; }
    },
  ];

  function getRate() {
    var v = parseFloat(document.getElementById('ec-rate').value);
    return isNaN(v) || v <= 0 ? 31 : v;
  }

  function fmt(n) {
    return Math.round(n).toLocaleString('ja-JP');
  }

  function calcDevice(d) {
    var kwhDay = d.watts / 1000 * d.hours;
    var rate = getRate();
    return {
      kwhDay: kwhDay,
      costDay: kwhDay * rate,
      costMonth: kwhDay * rate * 30,
      costYear: kwhDay * rate * 365,
    };
  }

  // ---- Render presets ----
  function renderPresets() {
    var wrap = document.getElementById('ec-presets');
    wrap.innerHTML = '';
    PRESETS.forEach(function(p) {
      var btn = document.createElement('button');
      btn.className = 'ec-preset-btn';
      btn.textContent = p.name + ' ' + p.watts + 'W';
      btn.onclick = function() {
        document.getElementById('ec-name').value = p.name;
        document.getElementById('ec-watts').value = p.watts;
        document.getElementById('ec-hours').focus();
      };
      wrap.appendChild(btn);
    });
  }

  // ---- Add device ----
  window.ecAddDevice = function() {
    var name = document.getElementById('ec-name').value.trim();
    var watts = parseFloat(document.getElementById('ec-watts').value);
    var hours = parseFloat(document.getElementById('ec-hours').value);
    var err = document.getElementById('ec-form-error');

    if (!name) { err.textContent = '機器名を入力してください。'; return; }
    if (isNaN(watts) || watts < 0) { err.textContent = '消費電力（W）を正しく入力してください。'; return; }
    if (isNaN(hours) || hours < 0 || hours > 24) { err.textContent = '使用時間は0〜24時間で入力してください。'; return; }
    err.textContent = '';

    devices.push({ id: nextId++, name: name, watts: watts, hours: hours });
    document.getElementById('ec-name').value = '';
    document.getElementById('ec-watts').value = '';
    document.getElementById('ec-hours').value = '';
    render();
  };

  // ---- Remove device ----
  window.ecRemoveDevice = function(id) {
    devices = devices.filter(function(d) { return d.id !== id; });
    render();
  };

  // ---- Render device list ----
  function renderList() {
    var ul = document.getElementById('ec-device-list');
    var emptyMsg = document.getElementById('ec-empty-msg');

    if (devices.length === 0) {
      ul.innerHTML = '';
      ul.appendChild(emptyMsg);
      emptyMsg.style.display = '';
      return;
    }
    emptyMsg.style.display = 'none';
    ul.innerHTML = '';

    devices.forEach(function(d) {
      var c = calcDevice(d);
      var li = document.createElement('li');
      li.className = 'ec-device-item';
      li.innerHTML =
        '<span class="ec-device-name">' + esc(d.name) + '</span>' +
        '<span class="ec-device-detail">' + d.watts + 'W &times; ' + d.hours + '時間/日</span>' +
        '<span class="ec-device-cost">月: ¥' + fmt(c.costMonth) + '</span>' +
        '<button class="ec-btn ec-btn-danger" onclick="ecRemoveDevice(' + d.id + ')" style="flex:0 0 auto;padding:6px 12px;font-size:12px;">削除</button>';
      ul.appendChild(li);
    });
  }

  // ---- Render results ----
  function renderResults() {
    var section = document.getElementById('ec-total-section');
    if (devices.length === 0) {
      section.style.display = 'none';
      return;
    }
    section.style.display = '';

    var totalKwh = 0, totalDay = 0, totalMonth = 0, totalYear = 0;
    devices.forEach(function(d) {
      var c = calcDevice(d);
      totalKwh += c.kwhDay;
      totalDay += c.costDay;
      totalMonth += c.costMonth;
      totalYear += c.costYear;
    });

    document.getElementById('ec-total-monthly').textContent = '¥' + fmt(totalMonth);
    document.getElementById('ec-res-daily').textContent = '¥' + fmt(totalDay);
    document.getElementById('ec-res-monthly').textContent = '¥' + fmt(totalMonth);
    document.getElementById('ec-res-yearly').textContent = '¥' + fmt(totalYear);
    document.getElementById('ec-res-kwh').textContent = totalKwh.toFixed(2);
  }

  // ---- Canvas bar chart ----
  var chartDrawn = false;
  function renderChart() {
    if (devices.length === 0) return;
    var canvas = document.getElementById('ec-chart');
    var ctx = canvas.getContext('2d');

    // HiDPI
    var dpr = window.devicePixelRatio || 1;
    var displayW = canvas.offsetWidth || canvas.parentElement.clientWidth || 700;
    var displayH = 220;
    canvas.width = displayW * dpr;
    canvas.height = displayH * dpr;
    canvas.style.width = displayW + 'px';
    canvas.style.height = displayH + 'px';
    ctx.scale(dpr, dpr);

    var W = displayW;
    var H = displayH;
    ctx.clearRect(0, 0, W, H);

    var costs = devices.map(function(d) { return calcDevice(d).costMonth; });
    var maxCost = Math.max.apply(null, costs) || 1;

    var padL = 16, padR = 16, padTop = 24, padBot = 48;
    var chartW = W - padL - padR;
    var chartH = H - padTop - padBot;
    var n = devices.length;
    var barW = Math.min(60, (chartW / n) * 0.55);
    var gap = chartW / n;

    var COLORS = ['#0284c7','#0369a1','#38bdf8','#7dd3fc','#bae6fd','#0ea5e9','#0c4a6e','#075985'];

    devices.forEach(function(d, i) {
      var c = costs[i];
      var barH = (c / maxCost) * chartH;
      var x = padL + gap * i + (gap - barW) / 2;
      var y = padTop + chartH - barH;

      // Bar
      ctx.fillStyle = COLORS[i % COLORS.length];
      ctx.beginPath();
      var radius = 4;
      ctx.moveTo(x + radius, y);
      ctx.lineTo(x + barW - radius, y);
      ctx.quadraticCurveTo(x + barW, y, x + barW, y + radius);
      ctx.lineTo(x + barW, y + barH);
      ctx.lineTo(x, y + barH);
      ctx.lineTo(x, y + radius);
      ctx.quadraticCurveTo(x, y, x + radius, y);
      ctx.closePath();
      ctx.fill();

      // Value label
      ctx.fillStyle = '#0369a1';
      ctx.font = 'bold 11px sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText('¥' + fmt(c), x + barW / 2, y - 5);

      // Name label (truncated)
      var label = d.name.length > 6 ? d.name.slice(0, 5) + '…' : d.name;
      ctx.fillStyle = '#475569';
      ctx.font = '11px sans-serif';
      ctx.fillText(label, x + barW / 2, padTop + chartH + 16);
    });

    // Baseline
    ctx.strokeStyle = '#e2e8f0';
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(padL, padTop + chartH);
    ctx.lineTo(W - padR, padTop + chartH);
    ctx.stroke();
  }

  // ---- Tips ----
  function renderTips() {
    if (devices.length === 0) return;
    var ul = document.getElementById('ec-tips-list');
    ul.innerHTML = '';
    var shown = {};
    var count = 0;

    devices.forEach(function(d) {
      TIPS_RULES.forEach(function(rule) {
        if (count >= 5) return;
        var key = rule.tip(d);
        if (rule.check(d) && !shown[key]) {
          shown[key] = true;
          var li = document.createElement('li');
          li.textContent = key;
          ul.appendChild(li);
          count++;
        }
      });
    });

    // Generic tip
    if (count === 0) {
      var li = document.createElement('li');
      li.textContent = '省エネ家電（省エネラベルA以上）への買い替えで年間数千円の節約効果が見込めます。';
      ul.appendChild(li);
    }
  }

  // ---- Main render ----
  function render() {
    renderList();
    renderResults();
    if (devices.length > 0) {
      setTimeout(renderChart, 0);
      renderTips();
    }
  }

  // ---- Rate change ----
  document.getElementById('ec-rate').addEventListener('input', function() {
    if (devices.length > 0) render();
  });

  // ---- Enter key on form ----
  ['ec-name','ec-watts','ec-hours'].forEach(function(id) {
    document.getElementById(id).addEventListener('keydown', function(e) {
      if (e.key === 'Enter') window.ecAddDevice();
    });
  });

  // ---- Resize chart ----
  var resizeTimer;
  window.addEventListener('resize', function() {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(function() {
      if (devices.length > 0) renderChart();
    }, 150);
  });

  function esc(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  // ---- Init ----
  renderPresets();
  render();
})();
</script>

</div>
