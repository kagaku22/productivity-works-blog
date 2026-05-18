---
title: "世界時計 - タイムゾーン比較ツール"
description: "無料の世界時計ツール。30以上の主要都市の現在時刻をリアルタイム表示。昼夜表示・ミーティングプランナー・時差計算機能付き。海外取引先との時間調整に最適。"
slug: world-clock
date: 2025-12-25
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/world-clock-ja.png
  alt: "世界時計 - タイムゾーン比較ツール"
---

<div id="wc-app">
<style>
#wc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
  max-width: 1100px;
  margin: 0 auto;
  color: #1e293b;
}
#wc-app * { box-sizing: border-box; }
#wc-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 0 0 14px 0;
  color: #0f172a;
}
#wc-app .wc-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 20px;
  align-items: center;
}
#wc-app .wc-search {
  flex: 1;
  min-width: 200px;
  padding: 9px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  outline: none;
  transition: border-color 0.2s;
}
#wc-app .wc-search:focus { border-color: #3b82f6; }
#wc-app .wc-city-select {
  flex: 1;
  min-width: 200px;
  padding: 9px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  outline: none;
  cursor: pointer;
}
#wc-app .wc-btn {
  padding: 9px 18px;
  background: #3b82f6;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  white-space: nowrap;
}
#wc-app .wc-btn:hover { background: #2563eb; }
#wc-app .wc-btn-secondary {
  background: #f1f5f9;
  color: #334155;
  border: 1.5px solid #cbd5e1;
}
#wc-app .wc-btn-secondary:hover { background: #e2e8f0; }
#wc-app .wc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 16px;
  margin-bottom: 28px;
}
#wc-app .wc-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 16px 18px;
  position: relative;
  transition: box-shadow 0.2s;
}
#wc-app .wc-card:hover { box-shadow: 0 4px 16px rgba(0,0,0,0.08); }
#wc-app .wc-card.day { border-top: 3px solid #f59e0b; }
#wc-app .wc-card.night { border-top: 3px solid #6366f1; background: #f8f7ff; }
#wc-app .wc-card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 8px;
}
#wc-app .wc-city-name {
  font-size: 15px;
  font-weight: 700;
  color: #0f172a;
}
#wc-app .wc-day-night {
  font-size: 20px;
  line-height: 1;
}
#wc-app .wc-tz-label {
  font-size: 11px;
  color: #94a3b8;
  margin-bottom: 4px;
}
#wc-app .wc-time {
  font-size: 28px;
  font-weight: 800;
  color: #0f172a;
  letter-spacing: -0.5px;
  font-variant-numeric: tabular-nums;
}
#wc-app .wc-date {
  font-size: 12px;
  color: #64748b;
  margin-top: 2px;
}
#wc-app .wc-diff {
  font-size: 12px;
  color: #3b82f6;
  margin-top: 4px;
  font-weight: 600;
}
#wc-app .wc-remove-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: none;
  border: none;
  color: #94a3b8;
  cursor: pointer;
  font-size: 16px;
  padding: 2px 5px;
  border-radius: 4px;
  line-height: 1;
  transition: color 0.2s, background 0.2s;
}
#wc-app .wc-remove-btn:hover { color: #ef4444; background: #fee2e2; }
#wc-app .wc-canvas-wrap {
  display: flex;
  justify-content: center;
  margin-top: 8px;
}
#wc-app canvas.wc-analog { display: block; }
#wc-app .wc-section {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 22px;
  margin-bottom: 24px;
}
#wc-app .wc-planner-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  margin-bottom: 16px;
}
#wc-app .wc-planner-select,
#wc-app .wc-planner-input {
  padding: 8px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  outline: none;
}
#wc-app .wc-planner-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
#wc-app .wc-planner-table th {
  text-align: left;
  padding: 6px 10px;
  background: #e2e8f0;
  color: #475569;
  font-weight: 600;
  border-radius: 4px;
}
#wc-app .wc-planner-table td {
  padding: 7px 10px;
  border-bottom: 1px solid #f1f5f9;
  color: #334155;
}
#wc-app .wc-planner-table tr:last-child td { border-bottom: none; }
#wc-app .wc-toggle-row {
  display: flex;
  gap: 10px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}
#wc-app .wc-toggle-btn {
  padding: 6px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 20px;
  background: #fff;
  font-size: 13px;
  cursor: pointer;
  transition: all 0.2s;
  color: #475569;
}
#wc-app .wc-toggle-btn.active {
  background: #3b82f6;
  border-color: #3b82f6;
  color: #fff;
}
#wc-app .wc-crosslinks {
  font-size: 13px;
  color: #64748b;
  margin-top: 10px;
  padding-top: 10px;
  border-top: 1px solid #e2e8f0;
}
#wc-app .wc-crosslinks a { color: #3b82f6; text-decoration: none; }
#wc-app .wc-crosslinks a:hover { text-decoration: underline; }
@media (max-width: 600px) {
  #wc-app .wc-grid { grid-template-columns: 1fr 1fr; gap: 10px; }
  #wc-app .wc-time { font-size: 22px; }
  #wc-app .wc-controls { flex-direction: column; }
}
@media (max-width: 380px) {
  #wc-app .wc-grid { grid-template-columns: 1fr; }
}
</style>

<div class="wc-controls">
  <input type="text" id="wc-search" class="wc-search" placeholder="都市名を検索..." />
  <select id="wc-city-select" class="wc-city-select">
    <option value="">— 都市を選んで追加 —</option>
  </select>
  <button id="wc-add-btn" class="wc-btn">+ 追加</button>
  <button id="wc-reset-btn" class="wc-btn wc-btn-secondary">リセット</button>
</div>

<div class="wc-toggle-row">
  <button class="wc-toggle-btn active" data-view="digital">デジタル時計</button>
  <button class="wc-toggle-btn" data-view="analog">アナログ時計</button>
</div>

<div id="wc-grid" class="wc-grid"></div>

<div class="wc-section">
  <h2>ミーティングプランナー</h2>
  <div class="wc-planner-row">
    <label style="font-size:14px;color:#475569;font-weight:600;">基準タイムゾーン：</label>
    <select id="wc-planner-tz" class="wc-planner-select"></select>
    <input type="time" id="wc-planner-time" class="wc-planner-input" value="09:00" />
    <button id="wc-planner-calc" class="wc-btn">比較する</button>
  </div>
  <div id="wc-planner-result"></div>
</div>

<div class="wc-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">海外取引の会計管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、外貨取引の仕訳・経費精算もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div class="wc-crosslinks">
  タイムスタンプ変換 → <a href="/ja/tools/timestamp-converter/">タイムスタンプ変換ツール</a> &nbsp;|&nbsp;
  タイムゾーン変換 → <a href="/ja/tools/timezone-converter/">タイムゾーン変換ツール</a>
</div>

<script>
(function () {
  'use strict';

  var CITIES = [
    { name: '東京', tz: 'Asia/Tokyo', flag: '🇯🇵' },
    { name: 'ソウル', tz: 'Asia/Seoul', flag: '🇰🇷' },
    { name: '北京', tz: 'Asia/Shanghai', flag: '🇨🇳' },
    { name: '上海', tz: 'Asia/Shanghai', flag: '🇨🇳' },
    { name: '香港', tz: 'Asia/Hong_Kong', flag: '🇭🇰' },
    { name: 'シンガポール', tz: 'Asia/Singapore', flag: '🇸🇬' },
    { name: 'バンコク', tz: 'Asia/Bangkok', flag: '🇹🇭' },
    { name: 'コルカタ', tz: 'Asia/Kolkata', flag: '🇮🇳' },
    { name: 'ムンバイ', tz: 'Asia/Kolkata', flag: '🇮🇳' },
    { name: 'ドバイ', tz: 'Asia/Dubai', flag: '🇦🇪' },
    { name: 'イスタンブール', tz: 'Europe/Istanbul', flag: '🇹🇷' },
    { name: 'モスクワ', tz: 'Europe/Moscow', flag: '🇷🇺' },
    { name: 'ナイロビ', tz: 'Africa/Nairobi', flag: '🇰🇪' },
    { name: 'カイロ', tz: 'Africa/Cairo', flag: '🇪🇬' },
    { name: 'ヨハネスブルグ', tz: 'Africa/Johannesburg', flag: '🇿🇦' },
    { name: 'フランクフルト', tz: 'Europe/Berlin', flag: '🇩🇪' },
    { name: 'ベルリン', tz: 'Europe/Berlin', flag: '🇩🇪' },
    { name: 'パリ', tz: 'Europe/Paris', flag: '🇫🇷' },
    { name: 'アムステルダム', tz: 'Europe/Amsterdam', flag: '🇳🇱' },
    { name: 'チューリッヒ', tz: 'Europe/Zurich', flag: '🇨🇭' },
    { name: 'ロンドン', tz: 'Europe/London', flag: '🇬🇧' },
    { name: 'リスボン', tz: 'Europe/Lisbon', flag: '🇵🇹' },
    { name: 'レイキャビク', tz: 'Atlantic/Reykjavik', flag: '🇮🇸' },
    { name: 'ニューヨーク', tz: 'America/New_York', flag: '🇺🇸' },
    { name: 'ワシントンDC', tz: 'America/New_York', flag: '🇺🇸' },
    { name: 'シカゴ', tz: 'America/Chicago', flag: '🇺🇸' },
    { name: 'デンバー', tz: 'America/Denver', flag: '🇺🇸' },
    { name: 'ロサンゼルス', tz: 'America/Los_Angeles', flag: '🇺🇸' },
    { name: 'サンフランシスコ', tz: 'America/Los_Angeles', flag: '🇺🇸' },
    { name: 'トロント', tz: 'America/Toronto', flag: '🇨🇦' },
    { name: 'バンクーバー', tz: 'America/Vancouver', flag: '🇨🇦' },
    { name: 'メキシコシティ', tz: 'America/Mexico_City', flag: '🇲🇽' },
    { name: 'サンパウロ', tz: 'America/Sao_Paulo', flag: '🇧🇷' },
    { name: 'ブエノスアイレス', tz: 'America/Argentina/Buenos_Aires', flag: '🇦🇷' },
    { name: 'シドニー', tz: 'Australia/Sydney', flag: '🇦🇺' },
    { name: 'メルボルン', tz: 'Australia/Melbourne', flag: '🇦🇺' },
    { name: 'オークランド', tz: 'Pacific/Auckland', flag: '🇳🇿' },
    { name: 'ホノルル', tz: 'Pacific/Honolulu', flag: '🇺🇸' },
    { name: 'アンカレジ', tz: 'America/Anchorage', flag: '🇺🇸' },
    { name: 'UTC', tz: 'UTC', flag: '🌐' },
  ];

  var DEFAULT_CITIES = ['東京', 'ニューヨーク', 'ロンドン', 'シドニー', 'ドバイ', 'ロサンゼルス'];
  var STORAGE_KEY = 'wc_ja_selected_cities';
  var VIEW_KEY = 'wc_ja_view_mode';

  var viewMode = localStorage.getItem(VIEW_KEY) || 'digital';
  var selectedCities = [];
  var tickInterval = null;

  function loadCities() {
    try {
      var stored = JSON.parse(localStorage.getItem(STORAGE_KEY));
      if (Array.isArray(stored) && stored.length > 0) return stored;
    } catch (e) {}
    return DEFAULT_CITIES.slice();
  }

  function saveCities() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(selectedCities));
  }

  function getLocalHour(tz) {
    try {
      var d = new Date();
      var h = parseInt(new Intl.DateTimeFormat('ja-JP', { hour: 'numeric', hour12: false, timeZone: tz }).format(d), 10);
      return h;
    } catch (e) { return 12; }
  }

  function isDay(tz) {
    var h = getLocalHour(tz);
    return h >= 6 && h < 20;
  }

  function getTimeInTz(tz) {
    var d = new Date();
    var opts = { hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false, timeZone: tz };
    return new Intl.DateTimeFormat('ja-JP', opts).format(d);
  }

  function getDateInTz(tz) {
    var d = new Date();
    var opts = { weekday: 'short', month: 'long', day: 'numeric', timeZone: tz };
    return new Intl.DateTimeFormat('ja-JP', opts).format(d);
  }

  function getTzLabel(tz) {
    try {
      var d = new Date();
      var parts = new Intl.DateTimeFormat('en-US', { timeZoneName: 'short', timeZone: tz }).formatToParts(d);
      var p = parts.find(function (x) { return x.type === 'timeZoneName'; });
      return p ? p.value : tz;
    } catch (e) { return tz; }
  }

  function getOffsetDiff(tz) {
    try {
      var d = new Date();
      var localOffset = -d.getTimezoneOffset();
      var tzStr = new Intl.DateTimeFormat('en-US', { timeZone: tz, timeZoneName: 'longOffset' })
        .formatToParts(d).find(function (p) { return p.type === 'timeZoneName'; });
      if (!tzStr) return '';
      var m = tzStr.value.match(/GMT([+-])(\d{2}):(\d{2})/);
      if (!m) return tz === 'UTC' ? 'UTC±0' : '';
      var sign = m[1] === '+' ? 1 : -1;
      var tzOffset = sign * (parseInt(m[2], 10) * 60 + parseInt(m[3], 10));
      var diff = tzOffset - localOffset;
      if (diff === 0) return '現地時刻と同じ';
      var h = Math.floor(Math.abs(diff) / 60);
      var min = Math.abs(diff) % 60;
      var str = diff > 0 ? '+' : '-';
      str += h + (min ? ':' + String(min).padStart(2, '0') : '') + '時間（現地比）';
      return str;
    } catch (e) { return ''; }
  }

  function drawAnalog(canvas, tz) {
    var ctx = canvas.getContext('2d');
    var size = canvas.width;
    var cx = size / 2, cy = size / 2, r = size / 2 - 4;
    ctx.clearRect(0, 0, size, size);

    ctx.beginPath();
    ctx.arc(cx, cy, r, 0, Math.PI * 2);
    ctx.fillStyle = '#f8fafc';
    ctx.fill();
    ctx.strokeStyle = '#cbd5e1';
    ctx.lineWidth = 2;
    ctx.stroke();

    for (var i = 0; i < 12; i++) {
      var ang = (i / 12) * Math.PI * 2 - Math.PI / 2;
      var x1 = cx + Math.cos(ang) * (r - 6);
      var y1 = cy + Math.sin(ang) * (r - 6);
      var x2 = cx + Math.cos(ang) * (r - 14);
      var y2 = cy + Math.sin(ang) * (r - 14);
      ctx.beginPath();
      ctx.moveTo(x1, y1);
      ctx.lineTo(x2, y2);
      ctx.strokeStyle = '#94a3b8';
      ctx.lineWidth = i % 3 === 0 ? 2.5 : 1.5;
      ctx.stroke();
    }

    var d = new Date();
    var parts = new Intl.DateTimeFormat('en-US', {
      hour: '2-digit', minute: '2-digit', second: '2-digit',
      hour12: false, timeZone: tz
    }).formatToParts(d);
    var hh = 0, mm = 0, ss = 0;
    parts.forEach(function (p) {
      if (p.type === 'hour') hh = parseInt(p.value, 10) % 12;
      if (p.type === 'minute') mm = parseInt(p.value, 10);
      if (p.type === 'second') ss = parseInt(p.value, 10);
    });

    function drawHand(angle, length, width, color) {
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.lineTo(cx + Math.cos(angle) * length, cy + Math.sin(angle) * length);
      ctx.strokeStyle = color;
      ctx.lineWidth = width;
      ctx.lineCap = 'round';
      ctx.stroke();
    }

    var hourAng = ((hh + mm / 60 + ss / 3600) / 12) * Math.PI * 2 - Math.PI / 2;
    var minAng = ((mm + ss / 60) / 60) * Math.PI * 2 - Math.PI / 2;
    var secAng = (ss / 60) * Math.PI * 2 - Math.PI / 2;

    drawHand(hourAng, r * 0.5, 4, '#0f172a');
    drawHand(minAng, r * 0.72, 3, '#334155');
    drawHand(secAng, r * 0.82, 1.5, '#ef4444');

    ctx.beginPath();
    ctx.arc(cx, cy, 4, 0, Math.PI * 2);
    ctx.fillStyle = '#0f172a';
    ctx.fill();
  }

  function renderCard(cityName) {
    var city = CITIES.find(function (c) { return c.name === cityName; });
    if (!city) return '';
    var day = isDay(city.tz);
    var canvasId = 'wc-canvas-' + cityName.replace(/[\s\u3000]+/g, '-');
    return '<div class="wc-card ' + (day ? 'day' : 'night') + '" data-city="' + cityName + '">' +
      '<button class="wc-remove-btn" data-remove="' + cityName + '" title="削除">×</button>' +
      '<div class="wc-card-header">' +
        '<div>' +
          '<div class="wc-city-name">' + city.flag + ' ' + cityName + '</div>' +
          '<div class="wc-tz-label">' + getTzLabel(city.tz) + '</div>' +
        '</div>' +
        '<div class="wc-day-night">' + (day ? '☀️' : '🌙') + '</div>' +
      '</div>' +
      '<div class="wc-time" id="wc-time-' + cityName.replace(/[\s\u3000]+/g, '-') + '">' + getTimeInTz(city.tz) + '</div>' +
      '<div class="wc-date" id="wc-date-' + cityName.replace(/[\s\u3000]+/g, '-') + '">' + getDateInTz(city.tz) + '</div>' +
      '<div class="wc-diff">' + getOffsetDiff(city.tz) + '</div>' +
      (viewMode === 'analog' ? '<div class="wc-canvas-wrap"><canvas class="wc-analog" id="' + canvasId + '" width="90" height="90"></canvas></div>' : '') +
    '</div>';
  }

  function renderGrid() {
    var grid = document.getElementById('wc-grid');
    grid.innerHTML = selectedCities.map(renderCard).join('');
    if (viewMode === 'analog') {
      selectedCities.forEach(function (cityName) {
        var city = CITIES.find(function (c) { return c.name === cityName; });
        if (!city) return;
        var canvasId = 'wc-canvas-' + cityName.replace(/[\s\u3000]+/g, '-');
        var canvas = document.getElementById(canvasId);
        if (canvas) drawAnalog(canvas, city.tz);
      });
    }
  }

  function tick() {
    selectedCities.forEach(function (cityName) {
      var city = CITIES.find(function (c) { return c.name === cityName; });
      if (!city) return;
      var key = cityName.replace(/[\s\u3000]+/g, '-');
      var timeEl = document.getElementById('wc-time-' + key);
      var dateEl = document.getElementById('wc-date-' + key);
      if (timeEl) timeEl.textContent = getTimeInTz(city.tz);
      if (dateEl) dateEl.textContent = getDateInTz(city.tz);
      if (viewMode === 'analog') {
        var canvas = document.getElementById('wc-canvas-' + key);
        if (canvas) drawAnalog(canvas, city.tz);
      }
    });
  }

  function startTick() {
    if (tickInterval) clearInterval(tickInterval);
    tickInterval = setInterval(tick, 1000);
  }

  function populateSelect(filter) {
    var sel = document.getElementById('wc-city-select');
    var val = sel.value;
    var opts = CITIES.filter(function (c) {
      if (filter && !c.name.includes(filter)) return false;
      return !selectedCities.includes(c.name);
    });
    sel.innerHTML = '<option value="">— 都市を選んで追加 —</option>' +
      opts.map(function (c) { return '<option value="' + c.name + '">' + c.flag + ' ' + c.name + '</option>'; }).join('');
    if (val) sel.value = val;
  }

  function populatePlannerTz() {
    var sel = document.getElementById('wc-planner-tz');
    sel.innerHTML = CITIES.map(function (c) {
      return '<option value="' + c.tz + '">' + c.flag + ' ' + c.name + ' (' + getTzLabel(c.tz) + ')</option>';
    }).join('');
    sel.value = 'Asia/Tokyo';
  }

  function runPlanner() {
    var tz = document.getElementById('wc-planner-tz').value;
    var timeVal = document.getElementById('wc-planner-time').value;
    if (!timeVal) return;
    var parts = timeVal.split(':');
    var hh = parseInt(parts[0], 10);
    var mm = parseInt(parts[1], 10);

    var now = new Date();
    var srcFormatter = new Intl.DateTimeFormat('en-US', {
      timeZone: tz, timeZoneName: 'longOffset'
    });
    var srcParts = srcFormatter.formatToParts(now);
    var srcTzName = (srcParts.find(function (p) { return p.type === 'timeZoneName'; }) || {}).value || '';
    var m2 = srcTzName.match(/GMT([+-])(\d{2}):(\d{2})/);
    var srcOffsetMin = 0;
    if (m2) {
      var s2 = m2[1] === '+' ? 1 : -1;
      srcOffsetMin = s2 * (parseInt(m2[2], 10) * 60 + parseInt(m2[3], 10));
    }

    var utcMs = Date.UTC(now.getUTCFullYear(), now.getUTCMonth(), now.getUTCDate(), hh - srcOffsetMin / 60 | 0, mm - (srcOffsetMin % 60), 0);
    var utcDate = new Date(utcMs);

    var rows = CITIES.map(function (city) {
      var opts2 = { hour: '2-digit', minute: '2-digit', hour12: false, timeZone: city.tz };
      var t = new Intl.DateTimeFormat('ja-JP', opts2).format(utcDate);
      var hCity = parseInt(t.split(':')[0], 10);
      var isWorkHour = hCity >= 9 && hCity < 18;
      return '<tr><td>' + city.flag + ' ' + city.name + '</td><td>' + t + ' ' + getTzLabel(city.tz) +
        '</td><td style="color:' + (isWorkHour ? '#16a34a' : '#dc2626') + ';font-weight:600;">' +
        (isWorkHour ? '✓ 営業時間内' : '✗ 営業時間外') + '</td></tr>';
    });

    document.getElementById('wc-planner-result').innerHTML =
      '<table class="wc-planner-table"><thead><tr><th>都市</th><th>現地時刻</th><th>ステータス</th></tr></thead><tbody>' +
      rows.join('') + '</tbody></table>';
  }

  function init() {
    selectedCities = loadCities();
    populateSelect('');
    populatePlannerTz();
    renderGrid();
    startTick();

    document.getElementById('wc-search').addEventListener('input', function () {
      populateSelect(this.value);
    });

    document.getElementById('wc-add-btn').addEventListener('click', function () {
      var sel = document.getElementById('wc-city-select');
      var name = sel.value;
      if (!name) return;
      if (!selectedCities.includes(name)) {
        selectedCities.push(name);
        saveCities();
        populateSelect(document.getElementById('wc-search').value);
        renderGrid();
        startTick();
      }
    });

    document.getElementById('wc-reset-btn').addEventListener('click', function () {
      selectedCities = DEFAULT_CITIES.slice();
      saveCities();
      populateSelect(document.getElementById('wc-search').value);
      renderGrid();
      startTick();
    });

    document.getElementById('wc-grid').addEventListener('click', function (e) {
      var btn = e.target.closest('[data-remove]');
      if (!btn) return;
      var name = btn.getAttribute('data-remove');
      selectedCities = selectedCities.filter(function (c) { return c !== name; });
      saveCities();
      populateSelect(document.getElementById('wc-search').value);
      renderGrid();
      startTick();
    });

    document.querySelectorAll('#wc-app .wc-toggle-btn').forEach(function (btn) {
      btn.addEventListener('click', function () {
        document.querySelectorAll('#wc-app .wc-toggle-btn').forEach(function (b) { b.classList.remove('active'); });
        btn.classList.add('active');
        viewMode = btn.getAttribute('data-view');
        localStorage.setItem(VIEW_KEY, viewMode);
        renderGrid();
        startTick();
      });
    });

    document.getElementById('wc-planner-calc').addEventListener('click', runPlanner);
    document.getElementById('wc-planner-time').addEventListener('change', runPlanner);
    document.getElementById('wc-planner-tz').addEventListener('change', runPlanner);
    runPlanner();
  }

  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', init);
  } else {
    init();
  }
})();
</script>
</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
