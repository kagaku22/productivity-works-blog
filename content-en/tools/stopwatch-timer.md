---
title: "Stopwatch & Timer"
date: 2025-05-16
description: "Free online stopwatch and countdown timer. Lap timing, alarm sound, keyboard shortcuts, and millisecond precision. No sign-up required."
categories: ["Free Tools"]
slug: "stopwatch-timer"
ShowToc: false
cover:
  image: "/images/covers/stopwatch-timer.png"
  alt: "Stopwatch & Timer"
---

<div id="sw-app">

<style>
#sw-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 16px;
  box-sizing: border-box;
}
#sw-app * {
  box-sizing: border-box;
}
#sw-app .sw-card {
  background: var(--sw-bg, #1a1a2e);
  border-radius: 16px;
  padding: 24px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.18);
  transition: background 0.3s;
}
#sw-app.sw-light .sw-card {
  background: #f8fafc;
  box-shadow: 0 4px 24px rgba(0,0,0,0.10);
}
#sw-app .sw-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
#sw-app .sw-mode-tabs {
  display: flex;
  background: rgba(255,255,255,0.08);
  border-radius: 10px;
  padding: 3px;
  gap: 2px;
}
#sw-app.sw-light .sw-mode-tabs {
  background: #e2e8f0;
}
#sw-app .sw-tab {
  padding: 7px 20px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  background: transparent;
  color: rgba(255,255,255,0.55);
  transition: all 0.2s;
}
#sw-app.sw-light .sw-tab {
  color: #64748b;
}
#sw-app .sw-tab.active {
  background: #6366f1;
  color: #fff;
}
#sw-app .sw-theme-btn {
  background: rgba(255,255,255,0.1);
  border: none;
  border-radius: 8px;
  padding: 7px 12px;
  color: #fff;
  cursor: pointer;
  font-size: 18px;
  transition: background 0.2s;
}
#sw-app.sw-light .sw-theme-btn {
  background: #e2e8f0;
  color: #334155;
}
#sw-app .sw-theme-btn:hover {
  background: rgba(255,255,255,0.2);
}
#sw-app.sw-light .sw-theme-btn:hover {
  background: #cbd5e1;
}
#sw-app .sw-display {
  text-align: center;
  margin: 20px 0 24px;
}
#sw-app .sw-time {
  font-size: clamp(48px, 12vw, 72px);
  font-weight: 700;
  font-variant-numeric: tabular-nums;
  letter-spacing: 2px;
  color: #e2e8f0;
  line-height: 1.1;
  transition: color 0.3s;
}
#sw-app.sw-light .sw-time {
  color: #1e293b;
}
#sw-app .sw-ms {
  font-size: clamp(24px, 6vw, 36px);
  color: #6366f1;
  font-weight: 700;
  font-variant-numeric: tabular-nums;
}
#sw-app .sw-time-alarm {
  animation: sw-pulse 0.5s ease infinite alternate;
}
@keyframes sw-pulse {
  from { color: #e2e8f0; }
  to { color: #f43f5e; }
}
#sw-app.sw-light .sw-time-alarm {
  animation: sw-pulse-light 0.5s ease infinite alternate;
}
@keyframes sw-pulse-light {
  from { color: #1e293b; }
  to { color: #e11d48; }
}
#sw-app .sw-timer-inputs {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 4px;
  margin-bottom: 20px;
}
#sw-app .sw-time-input-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
}
#sw-app .sw-time-input-label {
  font-size: 11px;
  color: rgba(255,255,255,0.45);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
}
#sw-app.sw-light .sw-time-input-label {
  color: #94a3b8;
}
#sw-app .sw-time-input {
  width: 72px;
  text-align: center;
  font-size: 32px;
  font-weight: 700;
  font-variant-numeric: tabular-nums;
  background: rgba(255,255,255,0.08);
  border: 2px solid rgba(255,255,255,0.12);
  border-radius: 10px;
  color: #e2e8f0;
  padding: 8px 4px;
  outline: none;
  transition: border-color 0.2s;
  -moz-appearance: textfield;
}
#sw-app .sw-time-input::-webkit-outer-spin-button,
#sw-app .sw-time-input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
#sw-app.sw-light .sw-time-input {
  background: #fff;
  border-color: #cbd5e1;
  color: #1e293b;
}
#sw-app .sw-time-input:focus {
  border-color: #6366f1;
}
#sw-app .sw-time-sep {
  font-size: 32px;
  font-weight: 700;
  color: rgba(255,255,255,0.4);
  padding-bottom: 18px;
}
#sw-app.sw-light .sw-time-sep {
  color: #94a3b8;
}
#sw-app .sw-controls {
  display: flex;
  justify-content: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}
#sw-app .sw-btn {
  padding: 12px 28px;
  border: none;
  border-radius: 50px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: transform 0.1s, opacity 0.2s, box-shadow 0.2s;
  outline: none;
}
#sw-app .sw-btn:active {
  transform: scale(0.96);
}
#sw-app .sw-btn-start {
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  color: #fff;
  box-shadow: 0 4px 14px rgba(99,102,241,0.4);
  min-width: 120px;
}
#sw-app .sw-btn-stop {
  background: linear-gradient(135deg, #f43f5e, #e11d48);
  color: #fff;
  box-shadow: 0 4px 14px rgba(244,63,94,0.4);
  min-width: 120px;
}
#sw-app .sw-btn-lap {
  background: rgba(255,255,255,0.1);
  color: #e2e8f0;
}
#sw-app.sw-light .sw-btn-lap {
  background: #e2e8f0;
  color: #334155;
}
#sw-app .sw-btn-reset {
  background: rgba(255,255,255,0.07);
  color: rgba(255,255,255,0.7);
}
#sw-app.sw-light .sw-btn-reset {
  background: #f1f5f9;
  color: #64748b;
}
#sw-app .sw-btn:disabled {
  opacity: 0.35;
  cursor: not-allowed;
}
#sw-app .sw-shortcuts {
  text-align: center;
  font-size: 12px;
  color: rgba(255,255,255,0.3);
  margin-bottom: 16px;
  letter-spacing: 0.5px;
}
#sw-app.sw-light .sw-shortcuts {
  color: #94a3b8;
}
#sw-app .sw-shortcuts kbd {
  background: rgba(255,255,255,0.1);
  border-radius: 4px;
  padding: 1px 5px;
  font-family: monospace;
  font-size: 11px;
}
#sw-app.sw-light .sw-shortcuts kbd {
  background: #e2e8f0;
}
#sw-app .sw-laps {
  margin-top: 8px;
}
#sw-app .sw-laps-title {
  font-size: 13px;
  font-weight: 700;
  color: rgba(255,255,255,0.5);
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 10px;
}
#sw-app.sw-light .sw-laps-title {
  color: #94a3b8;
}
#sw-app .sw-laps-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}
#sw-app .sw-laps-table th {
  text-align: left;
  padding: 6px 10px;
  color: rgba(255,255,255,0.35);
  font-weight: 600;
  font-size: 12px;
  border-bottom: 1px solid rgba(255,255,255,0.07);
}
#sw-app.sw-light .sw-laps-table th {
  color: #94a3b8;
  border-bottom-color: #e2e8f0;
}
#sw-app .sw-laps-table td {
  padding: 8px 10px;
  color: #e2e8f0;
  border-bottom: 1px solid rgba(255,255,255,0.05);
  font-variant-numeric: tabular-nums;
}
#sw-app.sw-light .sw-laps-table td {
  color: #334155;
  border-bottom-color: #f1f5f9;
}
#sw-app .sw-laps-table tr:last-child td {
  border-bottom: none;
}
#sw-app .sw-laps-table .sw-lap-fastest {
  color: #34d399;
}
#sw-app .sw-laps-table .sw-lap-slowest {
  color: #f87171;
}
#sw-app .sw-laps-empty {
  text-align: center;
  color: rgba(255,255,255,0.2);
  font-size: 13px;
  padding: 18px 0;
}
#sw-app.sw-light .sw-laps-empty {
  color: #cbd5e1;
}
#sw-app .sw-alarm-banner {
  display: none;
  background: linear-gradient(135deg, #f43f5e, #e11d48);
  color: #fff;
  text-align: center;
  padding: 12px 16px;
  border-radius: 10px;
  font-size: 15px;
  font-weight: 700;
  margin-bottom: 16px;
  cursor: pointer;
  animation: sw-banner-in 0.3s ease;
}
@keyframes sw-banner-in {
  from { opacity: 0; transform: translateY(-10px); }
  to { opacity: 1; transform: translateY(0); }
}
#sw-app .sw-alarm-banner.show {
  display: block;
}
#sw-app .sw-progress-ring {
  display: flex;
  justify-content: center;
  margin-bottom: 8px;
}
#sw-app .sw-progress-ring svg {
  transform: rotate(-90deg);
}
#sw-app .sw-progress-track {
  fill: none;
  stroke: rgba(255,255,255,0.08);
  stroke-width: 6;
}
#sw-app.sw-light .sw-progress-track {
  stroke: #e2e8f0;
}
#sw-app .sw-progress-fill {
  fill: none;
  stroke: #6366f1;
  stroke-width: 6;
  stroke-linecap: round;
  transition: stroke-dashoffset 0.1s linear;
}
@media (max-width: 480px) {
  #sw-app .sw-btn {
    padding: 11px 18px;
    font-size: 14px;
  }
  #sw-app .sw-time-input {
    width: 60px;
    font-size: 26px;
  }
}
</style>

<div class="sw-card">
  <div class="sw-header">
    <div class="sw-mode-tabs">
      <button class="sw-tab active" id="sw-tab-stopwatch">Stopwatch</button>
      <button class="sw-tab" id="sw-tab-timer">Timer</button>
    </div>
    <button class="sw-theme-btn" id="sw-theme-btn" title="Toggle theme">🌙</button>
  </div>

  <div id="sw-alarm-banner" class="sw-alarm-banner">
    ⏰ Time's up! Click to dismiss.
  </div>

  <!-- Stopwatch panel -->
  <div id="sw-stopwatch-panel">
    <div class="sw-display">
      <div class="sw-time" id="sw-sw-display">
        <span id="sw-sw-hms">00:00:00</span><span class="sw-ms">.<span id="sw-sw-ms">00</span></span>
      </div>
    </div>
    <div class="sw-controls">
      <button class="sw-btn sw-btn-start" id="sw-sw-startstop">Start</button>
      <button class="sw-btn sw-btn-lap" id="sw-sw-lap" disabled>Lap</button>
      <button class="sw-btn sw-btn-reset" id="sw-sw-reset">Reset</button>
    </div>
    <div class="sw-shortcuts">
      <kbd>Space</kbd> Start/Stop &nbsp; <kbd>L</kbd> Lap &nbsp; <kbd>R</kbd> Reset
    </div>
    <div class="sw-laps" id="sw-laps-section">
      <div class="sw-laps-title">Lap Times</div>
      <table class="sw-laps-table" id="sw-laps-table">
        <thead><tr><th>#</th><th>Lap Time</th><th>Total</th></tr></thead>
        <tbody id="sw-laps-body">
          <tr><td colspan="3" class="sw-laps-empty">No laps yet</td></tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- Timer panel -->
  <div id="sw-timer-panel" style="display:none;">
    <div id="sw-timer-inputs-wrap">
      <div class="sw-timer-inputs">
        <div class="sw-time-input-wrap">
          <span class="sw-time-input-label">Hours</span>
          <input type="number" class="sw-time-input" id="sw-t-h" value="0" min="0" max="99">
        </div>
        <div class="sw-time-sep">:</div>
        <div class="sw-time-input-wrap">
          <span class="sw-time-input-label">Min</span>
          <input type="number" class="sw-time-input" id="sw-t-m" value="5" min="0" max="59">
        </div>
        <div class="sw-time-sep">:</div>
        <div class="sw-time-input-wrap">
          <span class="sw-time-input-label">Sec</span>
          <input type="number" class="sw-time-input" id="sw-t-s" value="0" min="0" max="59">
        </div>
      </div>
    </div>
    <div class="sw-progress-ring" id="sw-progress-ring" style="display:none;">
      <svg width="160" height="160" viewBox="0 0 160 160">
        <circle class="sw-progress-track" cx="80" cy="80" r="70"/>
        <circle class="sw-progress-fill" cx="80" cy="80" r="70" id="sw-progress-fill"
          stroke-dasharray="439.82"
          stroke-dashoffset="0"/>
      </svg>
    </div>
    <div class="sw-display" id="sw-timer-display-wrap" style="display:none;">
      <div class="sw-time" id="sw-t-display">
        <span id="sw-t-hms">00:05:00</span><span class="sw-ms">.<span id="sw-t-ms">00</span></span>
      </div>
    </div>
    <div class="sw-controls">
      <button class="sw-btn sw-btn-start" id="sw-t-startstop">Start</button>
      <button class="sw-btn sw-btn-reset" id="sw-t-reset">Reset</button>
    </div>
    <div class="sw-shortcuts">
      <kbd>Space</kbd> Start/Stop &nbsp; <kbd>R</kbd> Reset
    </div>
  </div>
</div>

<script>
(function() {
  var app = document.getElementById('sw-app');

  // --- Theme ---
  var themeBtn = document.getElementById('sw-theme-btn');
  var isLight = false;
  themeBtn.addEventListener('click', function() {
    isLight = !isLight;
    app.classList.toggle('sw-light', isLight);
    themeBtn.textContent = isLight ? '🌙' : '☀️';
  });

  // --- Tab switching ---
  var tabSW = document.getElementById('sw-tab-stopwatch');
  var tabTimer = document.getElementById('sw-tab-timer');
  var panelSW = document.getElementById('sw-stopwatch-panel');
  var panelTimer = document.getElementById('sw-timer-panel');
  var currentMode = 'stopwatch';

  tabSW.addEventListener('click', function() {
    if (currentMode === 'stopwatch') return;
    currentMode = 'stopwatch';
    tabSW.classList.add('active');
    tabTimer.classList.remove('active');
    panelSW.style.display = '';
    panelTimer.style.display = 'none';
  });
  tabTimer.addEventListener('click', function() {
    if (currentMode === 'timer') return;
    currentMode = 'timer';
    tabTimer.classList.add('active');
    tabSW.classList.remove('active');
    panelSW.style.display = 'none';
    panelTimer.style.display = '';
  });

  // ============================================================
  // STOPWATCH
  // ============================================================
  var swRunning = false;
  var swStartTime = 0;
  var swElapsed = 0;
  var swLapStart = 0;
  var swLaps = [];
  var swRaf = null;

  var swDisplay = document.getElementById('sw-sw-hms');
  var swMs = document.getElementById('sw-sw-ms');
  var swDisplayWrap = document.getElementById('sw-sw-display');
  var swBtnSS = document.getElementById('sw-sw-startstop');
  var swBtnLap = document.getElementById('sw-sw-lap');
  var swBtnReset = document.getElementById('sw-sw-reset');
  var swLapsBody = document.getElementById('sw-laps-body');

  function pad2(n) { return String(Math.floor(n)).padStart(2, '0'); }

  function formatTime(ms) {
    var totalSec = Math.floor(ms / 1000);
    var h = Math.floor(totalSec / 3600);
    var m = Math.floor((totalSec % 3600) / 60);
    var s = totalSec % 60;
    return pad2(h) + ':' + pad2(m) + ':' + pad2(s);
  }

  function formatMs(ms) {
    return pad2((ms % 1000) / 10);
  }

  function swTick() {
    var now = performance.now();
    var total = swElapsed + (now - swStartTime);
    swDisplay.textContent = formatTime(total);
    swMs.textContent = formatMs(total);
    swRaf = requestAnimationFrame(swTick);
  }

  swBtnSS.addEventListener('click', swToggle);
  swBtnLap.addEventListener('click', swLap);
  swBtnReset.addEventListener('click', swReset);

  function swToggle() {
    if (swRunning) {
      swRunning = false;
      swElapsed += performance.now() - swStartTime;
      cancelAnimationFrame(swRaf);
      swBtnSS.textContent = 'Start';
      swBtnSS.className = 'sw-btn sw-btn-start';
    } else {
      swRunning = true;
      swStartTime = performance.now();
      if (swLaps.length === 0) swLapStart = 0;
      swRaf = requestAnimationFrame(swTick);
      swBtnSS.textContent = 'Stop';
      swBtnSS.className = 'sw-btn sw-btn-stop';
      swBtnLap.disabled = false;
    }
  }

  function swLap() {
    if (!swRunning) return;
    var now = performance.now();
    var total = swElapsed + (now - swStartTime);
    var lapTime = total - swLapStart;
    swLapStart = total;
    swLaps.push({ lap: lapTime, total: total });
    swRenderLaps();
  }

  function swReset() {
    swRunning = false;
    cancelAnimationFrame(swRaf);
    swElapsed = 0;
    swLapStart = 0;
    swLaps = [];
    swDisplay.textContent = '00:00:00';
    swMs.textContent = '00';
    swBtnSS.textContent = 'Start';
    swBtnSS.className = 'sw-btn sw-btn-start';
    swBtnLap.disabled = true;
    swRenderLaps();
  }

  function swRenderLaps() {
    if (swLaps.length === 0) {
      swLapsBody.innerHTML = '<tr><td colspan="3" class="sw-laps-empty">No laps yet</td></tr>';
      return;
    }
    var lapTimes = swLaps.map(function(l) { return l.lap; });
    var minLap = Math.min.apply(null, lapTimes);
    var maxLap = Math.max.apply(null, lapTimes);
    var html = '';
    for (var i = swLaps.length - 1; i >= 0; i--) {
      var cls = '';
      if (swLaps.length > 1) {
        if (swLaps[i].lap === minLap) cls = ' class="sw-lap-fastest"';
        else if (swLaps[i].lap === maxLap) cls = ' class="sw-lap-slowest"';
      }
      html += '<tr' + cls + '><td>' + (i + 1) + '</td><td>' +
        formatTime(swLaps[i].lap) + '.' + formatMs(swLaps[i].lap) +
        '</td><td>' +
        formatTime(swLaps[i].total) + '.' + formatMs(swLaps[i].total) +
        '</td></tr>';
    }
    swLapsBody.innerHTML = html;
  }

  // ============================================================
  // TIMER
  // ============================================================
  var tRunning = false;
  var tStartTime = 0;
  var tTotalMs = 0;
  var tRemaining = 0;
  var tRaf = null;
  var tFinished = false;
  var tAudioCtx = null;
  var tAlarmInterval = null;

  var tH = document.getElementById('sw-t-h');
  var tM = document.getElementById('sw-t-m');
  var tS = document.getElementById('sw-t-s');
  var tDisplay = document.getElementById('sw-t-hms');
  var tDisplayMs = document.getElementById('sw-t-ms');
  var tDisplayWrap = document.getElementById('sw-t-display');
  var tDisplaySection = document.getElementById('sw-timer-display-wrap');
  var tInputsWrap = document.getElementById('sw-timer-inputs-wrap');
  var tProgressRing = document.getElementById('sw-progress-ring');
  var tProgressFill = document.getElementById('sw-progress-fill');
  var tBtnSS = document.getElementById('sw-t-startstop');
  var tBtnReset = document.getElementById('sw-t-reset');
  var alarmBanner = document.getElementById('sw-alarm-banner');
  var CIRCUMFERENCE = 2 * Math.PI * 70; // 439.82

  tBtnSS.addEventListener('click', tToggle);
  tBtnReset.addEventListener('click', tReset);
  alarmBanner.addEventListener('click', tDismissAlarm);

  function tGetInputMs() {
    var h = parseInt(tH.value) || 0;
    var m = parseInt(tM.value) || 0;
    var s = parseInt(tS.value) || 0;
    return (h * 3600 + m * 60 + s) * 1000;
  }

  function tToggle() {
    if (tFinished) { tReset(); return; }
    if (tRunning) {
      tRunning = false;
      tRemaining -= performance.now() - tStartTime;
      if (tRemaining < 0) tRemaining = 0;
      cancelAnimationFrame(tRaf);
      tBtnSS.textContent = 'Resume';
      tBtnSS.className = 'sw-btn sw-btn-start';
    } else {
      if (tRemaining === 0 && !tFinished) {
        tTotalMs = tGetInputMs();
        if (tTotalMs <= 0) return;
        tRemaining = tTotalMs;
        tInputsWrap.style.display = 'none';
        tProgressRing.style.display = 'flex';
        tDisplaySection.style.display = '';
      }
      tRunning = true;
      tStartTime = performance.now();
      tRaf = requestAnimationFrame(tTick);
      tBtnSS.textContent = 'Pause';
      tBtnSS.className = 'sw-btn sw-btn-stop';
    }
  }

  function tTick() {
    var now = performance.now();
    var elapsed = now - tStartTime;
    var left = tRemaining - elapsed;
    if (left <= 0) {
      left = 0;
      tRunning = false;
      tFinished = true;
      cancelAnimationFrame(tRaf);
      tRenderTimer(0);
      tFireAlarm();
      return;
    }
    tRenderTimer(left);
    tRaf = requestAnimationFrame(tTick);
  }

  function tRenderTimer(ms) {
    tDisplay.textContent = formatTime(ms);
    tDisplayMs.textContent = formatMs(ms);
    var fraction = tTotalMs > 0 ? ms / tTotalMs : 0;
    var offset = CIRCUMFERENCE * (1 - fraction);
    tProgressFill.setAttribute('stroke-dashoffset', offset.toFixed(2));
  }

  function tReset() {
    tRunning = false;
    tFinished = false;
    cancelAnimationFrame(tRaf);
    tDismissAlarm();
    tRemaining = 0;
    tInputsWrap.style.display = '';
    tProgressRing.style.display = 'none';
    tDisplaySection.style.display = 'none';
    tBtnSS.textContent = 'Start';
    tBtnSS.className = 'sw-btn sw-btn-start';
    tProgressFill.setAttribute('stroke-dashoffset', '0');
    document.getElementById('sw-t-display').classList.remove('sw-time-alarm');
  }

  function tFireAlarm() {
    alarmBanner.classList.add('show');
    document.getElementById('sw-t-display').classList.add('sw-time-alarm');
    tBtnSS.textContent = 'Reset';
    tBtnSS.className = 'sw-btn sw-btn-reset';
    tPlayAlarmSound();
    tAlarmInterval = setInterval(tPlayAlarmSound, 2000);
  }

  function tDismissAlarm() {
    alarmBanner.classList.remove('show');
    clearInterval(tAlarmInterval);
    tAlarmInterval = null;
  }

  function tPlayAlarmSound() {
    try {
      var AudioContext = window.AudioContext || window.webkitAudioContext;
      if (!AudioContext) return;
      var ctx = new AudioContext();
      function beep(freq, start, dur) {
        var osc = ctx.createOscillator();
        var gain = ctx.createGain();
        osc.connect(gain);
        gain.connect(ctx.destination);
        osc.type = 'sine';
        osc.frequency.value = freq;
        gain.gain.setValueAtTime(0.4, ctx.currentTime + start);
        gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + start + dur);
        osc.start(ctx.currentTime + start);
        osc.stop(ctx.currentTime + start + dur + 0.05);
      }
      beep(880, 0, 0.15);
      beep(1100, 0.18, 0.15);
      beep(1320, 0.36, 0.3);
    } catch(e) {}
  }

  // ============================================================
  // KEYBOARD SHORTCUTS
  // ============================================================
  document.addEventListener('keydown', function(e) {
    var tag = e.target.tagName;
    if (tag === 'INPUT' || tag === 'TEXTAREA') return;
    if (e.key === ' ' || e.code === 'Space') {
      e.preventDefault();
      if (currentMode === 'stopwatch') swToggle();
      else tToggle();
    } else if (e.key === 'l' || e.key === 'L') {
      if (currentMode === 'stopwatch') swLap();
    } else if (e.key === 'r' || e.key === 'R') {
      if (currentMode === 'stopwatch') swReset();
      else tReset();
    }
  });

  // Clamp timer inputs
  [tH, tM, tS].forEach(function(inp) {
    inp.addEventListener('change', function() {
      var max = inp === tH ? 99 : 59;
      var val = parseInt(inp.value) || 0;
      if (val < 0) val = 0;
      if (val > max) val = max;
      inp.value = val;
    });
  });

})();
</script>

</div>

> Plan your day → [Daily Planner](/tools/daily-planner/)

> Event countdown → [Event Countdown](/tools/event-countdown/)
