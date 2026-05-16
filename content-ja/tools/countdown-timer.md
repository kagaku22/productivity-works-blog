---
title: "カウントダウンタイマー - 無料イベント日数カウントダウン"
date: 2025-05-16
description: "任意の日付までのカウントダウンを作成。日・時間・分・秒をリアルタイム表示。祝日プリセット・複数イベント同時管理。無料オンラインツール。"
categories: ["無料ツール"]
tags: ["カウントダウン", "タイマー", "日数計算", "イベント", "あと何日"]
slug: "countdown-timer"
aliases: ["/ja/tools/date-countdown/", "/ja/tools/event-timer/"]
cover:
  image: "/images/covers/countdown-timer-ja.png"
  alt: "カウントダウンタイマー"
ShowToc: false
---

<div id="countdown-app">

<style>
  #countdown-app {
    font-family: 'Segoe UI', 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
    max-width: 860px;
    margin: 0 auto;
    color: #1e1b4b;
  }

  #countdown-app * {
    box-sizing: border-box;
  }

  /* ---- Input Panel ---- */
  .cd-panel {
    background: linear-gradient(135deg, #6d28d9 0%, #4c1d95 100%);
    border-radius: 16px;
    padding: 28px 24px;
    color: #fff;
    margin-bottom: 24px;
    box-shadow: 0 8px 32px rgba(109,40,217,0.25);
  }

  .cd-panel h2 {
    margin: 0 0 20px 0;
    font-size: 1.25rem;
    font-weight: 700;
    letter-spacing: 0.03em;
    color: #fef3c7;
  }

  .cd-form-row {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 14px;
  }

  .cd-form-group {
    display: flex;
    flex-direction: column;
    flex: 1 1 180px;
  }

  .cd-form-group label {
    font-size: 0.78rem;
    font-weight: 600;
    margin-bottom: 5px;
    color: #ddd6fe;
    letter-spacing: 0.04em;
  }

  .cd-form-group input[type="text"],
  .cd-form-group input[type="date"],
  .cd-form-group input[type="time"] {
    padding: 9px 12px;
    border: none;
    border-radius: 8px;
    font-size: 0.95rem;
    background: rgba(255,255,255,0.15);
    color: #fff;
    outline: none;
    transition: background 0.2s;
  }

  .cd-form-group input[type="text"]::placeholder {
    color: rgba(255,255,255,0.55);
  }

  .cd-form-group input[type="date"]::-webkit-calendar-picker-indicator,
  .cd-form-group input[type="time"]::-webkit-calendar-picker-indicator {
    filter: invert(1);
    cursor: pointer;
  }

  .cd-form-group input:focus {
    background: rgba(255,255,255,0.25);
  }

  .cd-mode-toggle {
    display: flex;
    gap: 10px;
    margin-bottom: 14px;
    flex-wrap: wrap;
  }

  .cd-mode-btn {
    padding: 7px 18px;
    border-radius: 20px;
    border: 2px solid rgba(255,255,255,0.4);
    background: transparent;
    color: #fff;
    font-size: 0.85rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
  }

  .cd-mode-btn.active {
    background: #fbbf24;
    border-color: #fbbf24;
    color: #1e1b4b;
  }

  .cd-btn-row {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 4px;
  }

  .cd-start-btn {
    padding: 11px 28px;
    background: #fbbf24;
    color: #1e1b4b;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s, transform 0.1s;
    letter-spacing: 0.03em;
  }

  .cd-start-btn:hover {
    background: #f59e0b;
    transform: translateY(-1px);
  }

  .cd-add-btn {
    padding: 11px 20px;
    background: rgba(255,255,255,0.15);
    color: #fff;
    border: 2px solid rgba(255,255,255,0.4);
    border-radius: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s;
  }

  .cd-add-btn:hover {
    background: rgba(255,255,255,0.25);
  }

  /* ---- Presets ---- */
  .cd-presets {
    margin-top: 18px;
  }

  .cd-presets-label {
    font-size: 0.78rem;
    font-weight: 600;
    color: #ddd6fe;
    margin-bottom: 8px;
    display: block;
    letter-spacing: 0.04em;
  }

  .cd-preset-list {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .cd-preset-chip {
    padding: 6px 14px;
    background: rgba(255,255,255,0.12);
    border: 1px solid rgba(255,255,255,0.3);
    border-radius: 20px;
    color: #fff;
    font-size: 0.82rem;
    cursor: pointer;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .cd-preset-chip:hover {
    background: rgba(251,191,36,0.3);
    border-color: #fbbf24;
    color: #fef3c7;
  }

  /* ---- Main Display ---- */
  .cd-display-card {
    background: #fff;
    border-radius: 16px;
    box-shadow: 0 4px 24px rgba(109,40,217,0.12);
    padding: 28px 20px 20px;
    margin-bottom: 20px;
    border: 2px solid #ede9fe;
    position: relative;
    overflow: hidden;
  }

  .cd-event-name {
    text-align: center;
    font-size: 1.15rem;
    font-weight: 700;
    color: #5b21b6;
    margin-bottom: 20px;
    letter-spacing: 0.03em;
  }

  .cd-units {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 20px;
  }

  .cd-unit-card {
    background: linear-gradient(135deg, #6d28d9 0%, #4c1d95 100%);
    border-radius: 14px;
    min-width: 80px;
    padding: 16px 10px 12px;
    text-align: center;
    box-shadow: 0 4px 14px rgba(109,40,217,0.22);
    transition: transform 0.15s;
    flex: 1 1 70px;
    max-width: 120px;
  }

  .cd-unit-card:hover {
    transform: translateY(-2px);
  }

  .cd-unit-value {
    font-size: 2.6rem;
    font-weight: 900;
    color: #fbbf24;
    line-height: 1;
    font-variant-numeric: tabular-nums;
    letter-spacing: -0.02em;
  }

  .cd-unit-label {
    font-size: 0.72rem;
    font-weight: 700;
    color: #ddd6fe;
    margin-top: 6px;
    letter-spacing: 0.08em;
  }

  .cd-separator {
    font-size: 2rem;
    font-weight: 900;
    color: #7c3aed;
    align-self: center;
    margin-top: -10px;
    flex: 0 0 auto;
  }

  /* ---- Progress Bar ---- */
  .cd-progress-wrap {
    margin: 4px 0 14px;
  }

  .cd-progress-labels {
    display: flex;
    justify-content: space-between;
    font-size: 0.72rem;
    color: #7c3aed;
    font-weight: 600;
    margin-bottom: 4px;
  }

  .cd-progress-bar {
    width: 100%;
    height: 8px;
    background: #ede9fe;
    border-radius: 4px;
    overflow: hidden;
  }

  .cd-progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #6d28d9, #fbbf24);
    border-radius: 4px;
    transition: width 0.5s ease;
  }

  /* ---- Trivia ---- */
  .cd-trivia {
    background: #faf5ff;
    border-radius: 10px;
    padding: 12px 16px;
    font-size: 0.83rem;
    color: #5b21b6;
    margin-bottom: 14px;
    border-left: 4px solid #7c3aed;
    line-height: 1.6;
  }

  .cd-trivia span {
    font-weight: 700;
    color: #6d28d9;
  }

  /* ---- Elapsed Mode Badge ---- */
  .cd-mode-badge {
    display: inline-block;
    background: #7c3aed;
    color: #fff;
    font-size: 0.72rem;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 12px;
    margin-bottom: 12px;
    letter-spacing: 0.06em;
  }

  /* ---- Multi-card controls ---- */
  .cd-card-controls {
    display: flex;
    justify-content: flex-end;
    gap: 8px;
    margin-top: 4px;
  }

  .cd-del-btn {
    background: none;
    border: 1px solid #d1d5db;
    color: #6b7280;
    border-radius: 7px;
    padding: 4px 12px;
    font-size: 0.78rem;
    cursor: pointer;
    transition: all 0.2s;
  }

  .cd-del-btn:hover {
    background: #fee2e2;
    border-color: #fca5a5;
    color: #dc2626;
  }

  /* ---- Celebration Overlay ---- */
  .cd-celebrate {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, rgba(109,40,217,0.92) 0%, rgba(76,29,149,0.92) 100%);
    border-radius: 14px;
    z-index: 10;
    animation: cdFadeIn 0.4s ease;
  }

  @keyframes cdFadeIn {
    from { opacity: 0; transform: scale(0.95); }
    to   { opacity: 1; transform: scale(1); }
  }

  .cd-celebrate-emoji {
    font-size: 3.5rem;
    animation: cdBounce 0.6s infinite alternate;
  }

  @keyframes cdBounce {
    from { transform: translateY(0); }
    to   { transform: translateY(-12px); }
  }

  .cd-celebrate-text {
    color: #fbbf24;
    font-size: 1.5rem;
    font-weight: 900;
    margin-top: 12px;
    letter-spacing: 0.04em;
    text-align: center;
    padding: 0 16px;
  }

  .cd-celebrate-sub {
    color: #ddd6fe;
    font-size: 0.9rem;
    margin-top: 6px;
  }

  .cd-dismiss-btn {
    margin-top: 20px;
    padding: 9px 24px;
    background: #fbbf24;
    color: #1e1b4b;
    border: none;
    border-radius: 8px;
    font-weight: 700;
    font-size: 0.9rem;
    cursor: pointer;
  }

  /* ---- Confetti canvas ---- */
  #cd-confetti-canvas {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 9999;
  }

  /* ---- Multi-list ---- */
  .cd-list-section {
    margin-top: 8px;
  }

  .cd-list-title {
    font-size: 0.9rem;
    font-weight: 700;
    color: #5b21b6;
    margin-bottom: 12px;
    letter-spacing: 0.03em;
  }

  /* ---- Empty state ---- */
  .cd-empty {
    text-align: center;
    padding: 40px 20px;
    color: #9ca3af;
    font-size: 0.95rem;
  }

  .cd-empty-icon {
    font-size: 3rem;
    margin-bottom: 10px;
  }

  /* ---- Responsive ---- */
  @media (max-width: 540px) {
    .cd-unit-value { font-size: 1.9rem; }
    .cd-unit-card  { min-width: 58px; padding: 12px 6px 10px; }
    .cd-separator  { font-size: 1.4rem; }
    .cd-panel      { padding: 20px 16px; }
    .cd-display-card { padding: 20px 14px 16px; }
  }
</style>

<!-- Confetti canvas (fixed overlay) -->
<canvas id="cd-confetti-canvas"></canvas>

<!-- ========== INPUT PANEL ========== -->
<div class="cd-panel">
  <h2>カウントダウンタイマー</h2>

  <!-- Mode toggle -->
  <div class="cd-mode-toggle">
    <button class="cd-mode-btn active" id="cd-mode-countdown" onclick="cdSetMode('countdown')">カウントダウン</button>
    <button class="cd-mode-btn" id="cd-mode-elapsed" onclick="cdSetMode('elapsed')">経過時間</button>
  </div>

  <!-- Form -->
  <div class="cd-form-row">
    <div class="cd-form-group" style="flex: 2 1 220px;">
      <label>イベント名（任意）</label>
      <input type="text" id="cd-name-input" placeholder="例: 夏休み旅行" maxlength="40">
    </div>
    <div class="cd-form-group">
      <label>目標日付</label>
      <input type="date" id="cd-date-input">
    </div>
    <div class="cd-form-group">
      <label>時刻（任意）</label>
      <input type="time" id="cd-time-input" value="00:00">
    </div>
  </div>

  <div class="cd-btn-row">
    <button class="cd-start-btn" onclick="cdStart()">スタート</button>
    <button class="cd-add-btn" onclick="cdAddToList()">+ リストに追加</button>
  </div>

  <!-- Presets -->
  <div class="cd-presets">
    <span class="cd-presets-label">プリセット</span>
    <div class="cd-preset-list">
      <button class="cd-preset-chip" onclick="cdPreset('2027年お正月', '2027-01-01', '00:00')">2027年お正月</button>
      <button class="cd-preset-chip" onclick="cdPreset('クリスマス2026', '2026-12-25', '00:00')">クリスマス2026</button>
      <button class="cd-preset-chip" onclick="cdPreset('お盆2026', '2026-08-13', '00:00')">お盆2026</button>
      <button class="cd-preset-chip" onclick="cdPreset('大晦日2026', '2026-12-31', '23:59')">大晦日2026</button>
      <button class="cd-preset-chip" onclick="cdPreset('ゴールデンウィーク2026', '2026-04-29', '00:00')">GW2026</button>
      <button class="cd-preset-chip" onclick="cdPreset('夏休み2026', '2026-07-20', '00:00')">夏休み2026</button>
    </div>
  </div>
</div>

<!-- ========== MAIN DISPLAY ========== -->
<div id="cd-main-display">
  <div class="cd-empty">
    <div class="cd-empty-icon">⏱</div>
    <div>日付を設定してカウントダウンを開始しましょう</div>
  </div>
</div>

<!-- ========== MULTI-LIST ========== -->
<div class="cd-list-section" id="cd-list-section" style="display:none;">
  <div class="cd-list-title">登録済みイベント一覧</div>
  <div id="cd-list-container"></div>
</div>

<script>
(function() {
  /* ===== State ===== */
  var cdMode = 'countdown';
  var cdMainTimer = null;
  var cdMainData = null;
  var cdItems = [];   /* { id, name, targetMs, mode, startMs } */
  var cdItemTimers = {};
  var cdNextId = 1;
  var cdConfettiParts = [];
  var cdConfettiAnim = null;
  var cdCelebrated = {};

  /* ===== Helpers ===== */
  function cdPad(n) { return String(Math.floor(n)).padStart(2, '0'); }

  function cdGetTargetMs() {
    var dateVal = document.getElementById('cd-date-input').value;
    var timeVal = document.getElementById('cd-time-input').value || '00:00';
    if (!dateVal) return null;
    return new Date(dateVal + 'T' + timeVal + ':00').getTime();
  }

  function cdCalcDiff(targetMs, mode) {
    var now = Date.now();
    var diff = mode === 'elapsed' ? now - targetMs : targetMs - now;
    if (diff < 0) diff = 0;
    var total = Math.floor(diff / 1000);
    var days    = Math.floor(total / 86400);
    var hours   = Math.floor((total % 86400) / 3600);
    var minutes = Math.floor((total % 3600) / 60);
    var seconds = total % 60;
    return { days: days, hours: hours, minutes: minutes, seconds: seconds, total: total, diff: diff };
  }

  function cdTrivia(d) {
    var weeks = Math.floor(d.days / 7);
    var remDays = d.days % 7;
    var totalHours = d.days * 24 + d.hours;
    var totalMins  = totalHours * 60 + d.minutes;
    var parts = [];
    if (weeks > 0) parts.push('<span>' + weeks + '週間</span>' + (remDays > 0 ? remDays + '日' : ''));
    parts.push('<span>' + totalHours.toLocaleString() + '時間</span>');
    parts.push('<span>' + totalMins.toLocaleString() + '分</span>');
    return parts.join(' = ');
  }

  /* ===== Mode ===== */
  window.cdSetMode = function(m) {
    cdMode = m;
    document.getElementById('cd-mode-countdown').classList.toggle('active', m === 'countdown');
    document.getElementById('cd-mode-elapsed').classList.toggle('active', m === 'elapsed');
  };

  /* ===== Preset ===== */
  window.cdPreset = function(name, date, time) {
    document.getElementById('cd-name-input').value = name;
    document.getElementById('cd-date-input').value = date;
    document.getElementById('cd-time-input').value = time;
    cdSetMode('countdown');
    cdStart();
  };

  /* ===== Start main ===== */
  window.cdStart = function() {
    var targetMs = cdGetTargetMs();
    if (!targetMs) { alert('日付を入力してください。'); return; }
    var name = document.getElementById('cd-name-input').value.trim() || 'イベント';
    cdMainData = { name: name, targetMs: targetMs, mode: cdMode, startMs: Date.now() };
    if (cdMainTimer) clearInterval(cdMainTimer);
    cdCelebrated['main'] = false;
    cdRenderMain();
    cdMainTimer = setInterval(cdRenderMain, 1000);
  };

  function cdRenderMain() {
    if (!cdMainData) return;
    var d = cdCalcDiff(cdMainData.targetMs, cdMainData.mode);
    var finished = (cdMainData.mode === 'countdown') && (Date.now() >= cdMainData.targetMs);

    /* Progress: elapsed fraction from startMs → targetMs */
    var pct = 0;
    if (cdMainData.mode === 'countdown') {
      var total = cdMainData.targetMs - cdMainData.startMs;
      var elapsed = Date.now() - cdMainData.startMs;
      pct = total > 0 ? Math.min(100, Math.max(0, (elapsed / total) * 100)) : 100;
    } else {
      pct = Math.min(100, (d.days / 365) * 100);
    }

    var html = '<div class="cd-display-card" id="cd-main-card">';
    if (cdMainData.mode === 'elapsed') {
      html += '<div style="text-align:center;margin-bottom:10px;"><span class="cd-mode-badge">経過時間モード</span></div>';
    }
    html += '<div class="cd-event-name">' + cdEscape(cdMainData.name) + ' まで</div>';
    html += '<div class="cd-units">';
    html += cdUnitCard(d.days, '日');
    html += '<div class="cd-separator">:</div>';
    html += cdUnitCard(d.hours, '時間');
    html += '<div class="cd-separator">:</div>';
    html += cdUnitCard(d.minutes, '分');
    html += '<div class="cd-separator">:</div>';
    html += cdUnitCard(d.seconds, '秒');
    html += '</div>';

    /* Progress bar */
    html += '<div class="cd-progress-wrap">';
    html += '<div class="cd-progress-labels"><span>開始</span><span>' + Math.round(pct) + '%経過</span><span>目標</span></div>';
    html += '<div class="cd-progress-bar"><div class="cd-progress-fill" style="width:' + pct + '%"></div></div>';
    html += '</div>';

    /* Trivia */
    html += '<div class="cd-trivia">あと ' + cdTrivia(d) + '</div>';
    html += '</div>';

    document.getElementById('cd-main-display').innerHTML = html;

    if (finished && !cdCelebrated['main']) {
      cdCelebrated['main'] = true;
      cdShowCelebration('cd-main-card', cdMainData.name);
      cdFireConfetti();
    }
  }

  function cdUnitCard(val, label) {
    return '<div class="cd-unit-card"><div class="cd-unit-value">' + cdPad(val) + '</div><div class="cd-unit-label">' + label + '</div></div>';
  }

  /* ===== Add to list ===== */
  window.cdAddToList = function() {
    var targetMs = cdGetTargetMs();
    if (!targetMs) { alert('日付を入力してください。'); return; }
    var name = document.getElementById('cd-name-input').value.trim() || 'イベント';
    var id = cdNextId++;
    cdItems.push({ id: id, name: name, targetMs: targetMs, mode: cdMode, startMs: Date.now() });
    cdCelebrated['item_' + id] = false;
    cdRenderList();
    if (!cdItemTimers['main']) {
      cdItemTimers['main'] = setInterval(cdRenderList, 1000);
    }
  };

  function cdRenderList() {
    if (cdItems.length === 0) {
      document.getElementById('cd-list-section').style.display = 'none';
      return;
    }
    document.getElementById('cd-list-section').style.display = 'block';
    var html = '';
    cdItems.forEach(function(item) {
      var d = cdCalcDiff(item.targetMs, item.mode);
      var finished = (item.mode === 'countdown') && (Date.now() >= item.targetMs);
      var pct = 0;
      if (item.mode === 'countdown') {
        var tot = item.targetMs - item.startMs;
        pct = tot > 0 ? Math.min(100, Math.max(0, ((Date.now() - item.startMs) / tot) * 100)) : 100;
      } else {
        pct = Math.min(100, (d.days / 365) * 100);
      }
      html += '<div class="cd-display-card" id="cd-item-' + item.id + '" style="margin-bottom:16px;">';
      if (item.mode === 'elapsed') {
        html += '<div style="text-align:center;margin-bottom:6px;"><span class="cd-mode-badge">経過時間</span></div>';
      }
      html += '<div class="cd-event-name">' + cdEscape(item.name) + ' まで</div>';
      html += '<div class="cd-units">';
      html += cdUnitCard(d.days, '日');
      html += '<div class="cd-separator">:</div>';
      html += cdUnitCard(d.hours, '時間');
      html += '<div class="cd-separator">:</div>';
      html += cdUnitCard(d.minutes, '分');
      html += '<div class="cd-separator">:</div>';
      html += cdUnitCard(d.seconds, '秒');
      html += '</div>';
      html += '<div class="cd-progress-wrap">';
      html += '<div class="cd-progress-bar"><div class="cd-progress-fill" style="width:' + pct + '%"></div></div>';
      html += '</div>';
      html += '<div class="cd-trivia" style="margin-top:10px;">あと ' + cdTrivia(d) + '</div>';
      html += '<div class="cd-card-controls"><button class="cd-del-btn" onclick="cdDeleteItem(' + item.id + ')">削除</button></div>';
      html += '</div>';

      if (finished && !cdCelebrated['item_' + item.id]) {
        cdCelebrated['item_' + item.id] = true;
        setTimeout(function(iid, iname) {
          cdShowCelebration('cd-item-' + iid, iname);
          cdFireConfetti();
        }.bind(null, item.id, item.name), 100);
      }
    });
    document.getElementById('cd-list-container').innerHTML = html;
  }

  window.cdDeleteItem = function(id) {
    cdItems = cdItems.filter(function(i) { return i.id !== id; });
    if (cdItems.length === 0) {
      clearInterval(cdItemTimers['main']);
      delete cdItemTimers['main'];
    }
    cdRenderList();
  };

  /* ===== Celebration ===== */
  function cdShowCelebration(cardId, name) {
    var card = document.getElementById(cardId);
    if (!card) return;
    var cel = document.createElement('div');
    cel.className = 'cd-celebrate';
    cel.innerHTML =
      '<div class="cd-celebrate-emoji">🎉</div>' +
      '<div class="cd-celebrate-text">おめでとうございます！</div>' +
      '<div class="cd-celebrate-sub">「' + cdEscape(name) + '」の日が来ました</div>' +
      '<button class="cd-dismiss-btn" onclick="this.parentNode.remove()">閉じる</button>';
    card.appendChild(cel);
  }

  /* ===== Confetti ===== */
  function cdFireConfetti() {
    var canvas = document.getElementById('cd-confetti-canvas');
    var ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    var colors = ['#6d28d9','#fbbf24','#10b981','#f472b6','#60a5fa','#fff'];
    cdConfettiParts = [];
    for (var i = 0; i < 120; i++) {
      cdConfettiParts.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height - canvas.height,
        r: Math.random() * 7 + 3,
        color: colors[Math.floor(Math.random() * colors.length)],
        vy: Math.random() * 3 + 2,
        vx: (Math.random() - 0.5) * 2,
        angle: Math.random() * 360,
        spin: (Math.random() - 0.5) * 6
      });
    }
    if (cdConfettiAnim) cancelAnimationFrame(cdConfettiAnim);
    var frames = 0;
    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      cdConfettiParts.forEach(function(p) {
        ctx.save();
        ctx.translate(p.x, p.y);
        ctx.rotate(p.angle * Math.PI / 180);
        ctx.fillStyle = p.color;
        ctx.fillRect(-p.r / 2, -p.r / 2, p.r, p.r * 0.5);
        ctx.restore();
        p.y += p.vy;
        p.x += p.vx;
        p.angle += p.spin;
      });
      frames++;
      if (frames < 180) {
        cdConfettiAnim = requestAnimationFrame(animate);
      } else {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
      }
    }
    animate();
  }

  /* ===== Escape ===== */
  function cdEscape(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  /* ===== Init: set today's date as default ===== */
  (function init() {
    var today = new Date();
    var yyyy  = today.getFullYear();
    var mm    = String(today.getMonth() + 1).padStart(2, '0');
    var dd    = String(today.getDate()).padStart(2, '0');
    document.getElementById('cd-date-input').value = yyyy + '-' + mm + '-' + dd;
  })();
})();
</script>

</div>

---

## カウントダウンタイマーの使い方

1. **日付を入力する** — 「目標日付」フィールドにカウントダウンしたい日付を入力します。時刻も設定すると秒単位で精度が上がります。
2. **イベント名を付ける** — 「旅行」「資格試験」など目的を入力するとわかりやすくなります（省略可）。
3. **スタートを押す** — リアルタイムで日・時間・分・秒が表示されます。
4. **プリセットを使う** — よく使う日本の祝日・イベントをワンクリックで設定できます。
5. **複数管理** — 「リストに追加」を使うと複数のカウントダウンを同時に管理できます。
6. **経過時間モード** — 過去の日付（記念日・入社日など）からの経過時間を表示したい場合は「経過時間」モードに切り替えます。

---

## 人気のカウントダウンイベント

日本でよくカウントダウンされるイベントの例です。

| イベント | 特徴 |
|---|---|
| お正月 | 新年まであと何日？家族や友人と共有しよう |
| クリスマス | プレゼントの準備もカウントダウンで管理 |
| ゴールデンウィーク | 連休を楽しみに仕事を乗り切る |
| お盆 | 帰省や旅行の計画立てに |
| 大晦日 | 年越しまでの秒読み |
| 試験・受験 | 試験日まで逆算して計画的に学習 |
| 結婚記念日・誕生日 | 大切な人の記念日を忘れずに |
| 旅行出発日 | 旅行への期待感をリアルタイムで楽しむ |

---

## 関連ツール

> 正確な年齢を計算 → [年齢計算ツール](/ja/tools/age-calculator/)

> ポモドーロテクニックで集中 → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)

> 時間の単位を変換 → [単位変換ツール](/ja/tools/unit-converter/)

> 海外チームと時間を合わせる → [タイムゾーン変換ツール](/ja/tools/timezone-converter/) — 世界中の都市間で時刻を即変換

---

**年末の確定申告に向けて準備を**

確定申告の期限までカウントダウン！クラウド会計ソフト「freee」なら、日々の経費入力から確定申告書の作成まで、すべてスマホで完結します。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
