---
title: "Countdown Timer - Free Event Countdown & Date Calculator"
date: 2025-05-16
description: "Create a countdown to any date or event. See days, hours, minutes, and seconds remaining. Built-in holidays, custom events, and shareable countdowns."
categories: ["Free Tools"]
tags: ["countdown", "timer", "date calculator", "event countdown", "days until"]
slug: "countdown-timer"
aliases: ["/tools/event-countdown/", "/tools/event-countdown/", "/tools/days-until-calculator/"]
cover:
  image: "/images/covers/countdown-timer.png"
  alt: "Countdown Timer"
ShowToc: false
---

<div id="countdown-app">

<style>
/* =============================================
   COUNTDOWN TIMER - Deep Purple + Gold Theme
   ============================================= */

#countdown-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1e1b4b;
}

/* --- Input Panel --- */
.cd-panel {
  background: linear-gradient(135deg, #6d28d9 0%, #4c1d95 100%);
  border-radius: 16px;
  padding: 28px 28px 24px;
  color: #fff;
  margin-bottom: 24px;
  box-shadow: 0 8px 32px rgba(109,40,217,0.28);
}

.cd-panel h2 {
  margin: 0 0 20px;
  font-size: 1.3rem;
  font-weight: 700;
  letter-spacing: .02em;
  display: flex;
  align-items: center;
  gap: 8px;
}

.cd-form-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: flex-end;
}

.cd-form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
  flex: 1;
  min-width: 160px;
}

.cd-form-group label {
  font-size: .78rem;
  font-weight: 600;
  letter-spacing: .06em;
  text-transform: uppercase;
  opacity: .85;
}

.cd-form-group input[type="text"],
.cd-form-group input[type="date"],
.cd-form-group input[type="time"] {
  background: rgba(255,255,255,0.15);
  border: 1.5px solid rgba(255,255,255,0.35);
  border-radius: 8px;
  padding: 9px 13px;
  color: #fff;
  font-size: .97rem;
  outline: none;
  transition: border-color .2s, background .2s;
  width: 100%;
  box-sizing: border-box;
}

.cd-form-group input[type="text"]::placeholder {
  color: rgba(255,255,255,0.55);
}

.cd-form-group input:focus {
  border-color: #fbbf24;
  background: rgba(255,255,255,0.22);
}

.cd-form-group input[type="date"]::-webkit-calendar-picker-indicator,
.cd-form-group input[type="time"]::-webkit-calendar-picker-indicator {
  filter: invert(1);
  opacity: .7;
  cursor: pointer;
}

.cd-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 16px;
  align-items: center;
}

.cd-btn {
  padding: 9px 20px;
  border-radius: 8px;
  border: none;
  font-size: .9rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform .12s, box-shadow .12s, background .2s;
}

.cd-btn:active { transform: scale(.97); }

.cd-btn-primary {
  background: #fbbf24;
  color: #1e1b4b;
  box-shadow: 0 3px 10px rgba(251,191,36,.35);
}

.cd-btn-primary:hover { background: #f59e0b; box-shadow: 0 4px 14px rgba(251,191,36,.5); }

.cd-btn-secondary {
  background: rgba(255,255,255,0.15);
  color: #fff;
  border: 1.5px solid rgba(255,255,255,0.3);
}

.cd-btn-secondary:hover { background: rgba(255,255,255,0.25); }

/* Mode toggle */
.cd-mode-toggle {
  display: flex;
  gap: 0;
  background: rgba(0,0,0,0.2);
  border-radius: 8px;
  padding: 3px;
  margin-bottom: 16px;
  width: fit-content;
}

.cd-mode-btn {
  padding: 6px 16px;
  border: none;
  border-radius: 6px;
  font-size: .85rem;
  font-weight: 600;
  cursor: pointer;
  background: transparent;
  color: rgba(255,255,255,0.65);
  transition: background .2s, color .2s;
}

.cd-mode-btn.active {
  background: #fbbf24;
  color: #1e1b4b;
}

/* --- Presets --- */
.cd-presets {
  margin-top: 16px;
  border-top: 1px solid rgba(255,255,255,0.15);
  padding-top: 16px;
}

.cd-presets-label {
  font-size: .75rem;
  font-weight: 600;
  letter-spacing: .07em;
  text-transform: uppercase;
  opacity: .7;
  margin-bottom: 10px;
}

.cd-preset-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.cd-chip {
  padding: 5px 13px;
  border-radius: 20px;
  border: 1.5px solid rgba(255,255,255,0.35);
  background: rgba(255,255,255,0.1);
  color: #fff;
  font-size: .82rem;
  font-weight: 500;
  cursor: pointer;
  transition: background .2s, border-color .2s;
}

.cd-chip:hover {
  background: rgba(251,191,36,0.25);
  border-color: #fbbf24;
}

/* --- Main Countdown Display --- */
.cd-display {
  background: #fff;
  border-radius: 16px;
  padding: 32px 24px 28px;
  box-shadow: 0 4px 20px rgba(109,40,217,0.10);
  border: 1.5px solid #ede9fe;
  margin-bottom: 20px;
  text-align: center;
}

.cd-event-label {
  font-size: 1.05rem;
  color: #6d28d9;
  font-weight: 700;
  margin-bottom: 6px;
  letter-spacing: .01em;
  min-height: 1.4em;
}

.cd-mode-label {
  font-size: .8rem;
  color: #9ca3af;
  margin-bottom: 22px;
  text-transform: uppercase;
  letter-spacing: .08em;
}

/* Flip card numbers */
.cd-units {
  display: flex;
  justify-content: center;
  gap: 16px;
  flex-wrap: wrap;
  margin-bottom: 24px;
}

.cd-unit {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}

.cd-flip-card {
  width: 90px;
  height: 90px;
  position: relative;
  perspective: 400px;
}

@media (max-width: 500px) {
  .cd-flip-card { width: 68px; height: 68px; }
  .cd-num { font-size: 2.1rem !important; }
}

.cd-num {
  width: 100%;
  height: 100%;
  background: linear-gradient(160deg, #6d28d9 0%, #4c1d95 100%);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2.8rem;
  font-weight: 800;
  color: #fff;
  box-shadow: 0 4px 16px rgba(109,40,217,0.30);
  position: relative;
  overflow: hidden;
  transition: transform .1s;
  letter-spacing: -.02em;
  line-height: 1;
}

.cd-num::after {
  content: '';
  position: absolute;
  left: 0; right: 0;
  top: 50%;
  height: 1.5px;
  background: rgba(0,0,0,0.18);
}

.cd-num.flip-anim {
  animation: cdFlip .3s ease-in-out;
}

@keyframes cdFlip {
  0%   { transform: rotateX(0deg); }
  40%  { transform: rotateX(-25deg); }
  100% { transform: rotateX(0deg); }
}

.cd-unit-label {
  font-size: .72rem;
  font-weight: 700;
  letter-spacing: .1em;
  text-transform: uppercase;
  color: #7c3aed;
}

/* Separator */
.cd-sep {
  display: flex;
  align-items: center;
  padding-bottom: 32px;
  font-size: 2rem;
  font-weight: 800;
  color: #c4b5fd;
  line-height: 1;
}

/* Progress bar */
.cd-progress-wrap {
  margin: 0 auto 18px;
  max-width: 520px;
}

.cd-progress-label {
  display: flex;
  justify-content: space-between;
  font-size: .78rem;
  color: #9ca3af;
  margin-bottom: 6px;
}

.cd-progress-track {
  background: #ede9fe;
  border-radius: 99px;
  height: 8px;
  overflow: hidden;
}

.cd-progress-bar {
  height: 100%;
  border-radius: 99px;
  background: linear-gradient(90deg, #6d28d9, #fbbf24);
  transition: width .6s ease;
}

/* Fun facts */
.cd-facts {
  background: #faf5ff;
  border-radius: 10px;
  padding: 14px 18px;
  font-size: .87rem;
  color: #5b21b6;
  line-height: 1.7;
  max-width: 520px;
  margin: 0 auto;
  text-align: left;
}

.cd-facts strong { color: #6d28d9; }

/* --- Finished state --- */
.cd-finished {
  display: none;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  padding: 20px 0;
}

.cd-finished.show { display: flex; }

.cd-finished-emoji {
  font-size: 3.5rem;
  animation: cdBounce .6s ease infinite alternate;
}

@keyframes cdBounce {
  from { transform: translateY(0); }
  to   { transform: translateY(-12px); }
}

.cd-finished-msg {
  font-size: 1.4rem;
  font-weight: 800;
  color: #6d28d9;
}

/* Confetti canvas */
#cd-confetti {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  pointer-events: none;
  z-index: 9999;
  display: none;
}

/* --- Multiple Countdowns --- */
.cd-list-section {
  background: #fff;
  border-radius: 16px;
  padding: 22px 24px;
  box-shadow: 0 4px 20px rgba(109,40,217,0.08);
  border: 1.5px solid #ede9fe;
  margin-bottom: 20px;
}

.cd-list-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.cd-list-title {
  font-size: 1rem;
  font-weight: 700;
  color: #4c1d95;
}

.cd-list-empty {
  text-align: center;
  color: #a78bfa;
  font-size: .9rem;
  padding: 16px 0;
}

.cd-event-cards {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.cd-event-card {
  background: linear-gradient(90deg, #faf5ff 0%, #f5f3ff 100%);
  border: 1.5px solid #ddd6fe;
  border-radius: 10px;
  padding: 13px 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  flex-wrap: wrap;
}

.cd-event-card-name {
  font-weight: 700;
  color: #5b21b6;
  font-size: .95rem;
  flex: 1;
  min-width: 120px;
}

.cd-event-card-date {
  font-size: .8rem;
  color: #9ca3af;
}

.cd-event-card-time {
  font-size: 1.1rem;
  font-weight: 800;
  color: #6d28d9;
  white-space: nowrap;
}

.cd-event-card-remove {
  background: none;
  border: none;
  color: #c4b5fd;
  font-size: 1.1rem;
  cursor: pointer;
  padding: 2px 6px;
  border-radius: 5px;
  transition: color .2s, background .2s;
  line-height: 1;
}

.cd-event-card-remove:hover { color: #ef4444; background: #fef2f2; }

/* --- Responsive --- */
@media (max-width: 600px) {
  .cd-panel { padding: 20px 16px 18px; }
  .cd-display { padding: 22px 12px 20px; }
  .cd-units { gap: 6px; }
  .cd-sep { padding-bottom: 24px; font-size: 1.5rem; }
  .cd-list-section { padding: 18px 14px; }
}
</style>

<!-- Confetti Canvas -->
<canvas id="cd-confetti"></canvas>

<!-- Input Panel -->
<div class="cd-panel">
  <h2>&#8987; Countdown Timer</h2>

  <div class="cd-mode-toggle">
    <button class="cd-mode-btn active" id="cd-mode-countdown" onclick="setMode('countdown')">Countdown</button>
    <button class="cd-mode-btn" id="cd-mode-timesince" onclick="setMode('timesince')">Time Since</button>
  </div>

  <div class="cd-form-row">
    <div class="cd-form-group" style="flex:2;min-width:180px;">
      <label>Event Name (optional)</label>
      <input type="text" id="cd-event-name" placeholder="e.g. My Birthday, Product Launch..." />
    </div>
    <div class="cd-form-group">
      <label>Date</label>
      <input type="date" id="cd-date" />
    </div>
    <div class="cd-form-group" style="max-width:130px;">
      <label>Time</label>
      <input type="time" id="cd-time" value="00:00" />
    </div>
  </div>

  <div class="cd-btn-row">
    <button class="cd-btn cd-btn-primary" onclick="startCountdown()">Start Countdown</button>
    <button class="cd-btn cd-btn-secondary" onclick="addToList()">+ Add to List</button>
    <button class="cd-btn cd-btn-secondary" onclick="resetAll()">Reset</button>
  </div>

  <div class="cd-presets">
    <div class="cd-presets-label">Quick Presets</div>
    <div class="cd-preset-chips">
      <button class="cd-chip" onclick="setPreset('New Year 2027','2027-01-01','00:00')">&#127881; New Year 2027</button>
      <button class="cd-chip" onclick="setPreset('Christmas 2026','2026-12-25','00:00')">&#127876; Christmas 2026</button>
      <button class="cd-chip" onclick="setPreset('Summer Solstice','2026-06-21','00:00')">&#9728;&#65039; Summer 2026</button>
      <button class="cd-chip" onclick="setPreset('Halloween','2026-10-31','00:00')">&#127875; Halloween 2026</button>
      <button class="cd-chip" onclick="setPreset("Valentine's Day",'2027-02-14','00:00')">&#10084;&#65039; Valentine 2027</button>
    </div>
  </div>
</div>

<!-- Main Countdown Display -->
<div class="cd-display" id="cd-main-display">
  <div class="cd-event-label" id="cd-display-name">Set a date above to start your countdown</div>
  <div class="cd-mode-label" id="cd-display-mode">-- select a date --</div>

  <!-- Countdown units -->
  <div id="cd-countdown-units">
    <div class="cd-units">
      <div class="cd-unit">
        <div class="cd-flip-card"><div class="cd-num" id="cd-days">--</div></div>
        <div class="cd-unit-label">Days</div>
      </div>
      <div class="cd-sep">:</div>
      <div class="cd-unit">
        <div class="cd-flip-card"><div class="cd-num" id="cd-hours">--</div></div>
        <div class="cd-unit-label">Hours</div>
      </div>
      <div class="cd-sep">:</div>
      <div class="cd-unit">
        <div class="cd-flip-card"><div class="cd-num" id="cd-minutes">--</div></div>
        <div class="cd-unit-label">Minutes</div>
      </div>
      <div class="cd-sep">:</div>
      <div class="cd-unit">
        <div class="cd-flip-card"><div class="cd-num" id="cd-seconds">--</div></div>
        <div class="cd-unit-label">Seconds</div>
      </div>
    </div>

    <!-- Progress bar -->
    <div class="cd-progress-wrap" id="cd-progress-wrap" style="display:none;">
      <div class="cd-progress-label">
        <span id="cd-prog-start">Start</span>
        <span id="cd-prog-pct">0%</span>
        <span id="cd-prog-end">Target</span>
      </div>
      <div class="cd-progress-track">
        <div class="cd-progress-bar" id="cd-prog-bar" style="width:0%;"></div>
      </div>
    </div>

    <!-- Fun facts -->
    <div class="cd-facts" id="cd-facts" style="display:none;"></div>
  </div>

  <!-- Finished state -->
  <div class="cd-finished" id="cd-finished">
    <div class="cd-finished-emoji">&#127881;</div>
    <div class="cd-finished-msg" id="cd-finished-msg">The moment has arrived!</div>
    <div style="color:#7c3aed;font-size:.9rem;" id="cd-finished-sub"></div>
  </div>
</div>

<!-- Multiple Countdowns List -->
<div class="cd-list-section">
  <div class="cd-list-header">
    <div class="cd-list-title">&#128197; My Countdowns</div>
    <button class="cd-btn cd-btn-secondary" style="font-size:.8rem;padding:5px 12px;" onclick="clearList()">Clear All</button>
  </div>
  <div id="cd-event-cards">
    <div class="cd-list-empty" id="cd-list-empty">No events added yet. Use "+ Add to List" to track multiple countdowns.</div>
  </div>
</div>

<script>
(function() {
  'use strict';

  /* =========================================================
     STATE
  ========================================================= */
  let targetDate   = null;
  let startDate    = null; // when countdown was started (for progress)
  let currentMode  = 'countdown'; // 'countdown' | 'timesince'
  let timerInterval = null;
  let savedEvents  = []; // [{name, iso, mode}]
  let listInterval = null;
  let prevVals     = { d:'', h:'', m:'', s:'' };
  let confettiShown = false;

  /* =========================================================
     MODE
  ========================================================= */
  window.setMode = function(mode) {
    currentMode = mode;
    document.getElementById('cd-mode-countdown').classList.toggle('active', mode === 'countdown');
    document.getElementById('cd-mode-timesince').classList.toggle('active', mode === 'timesince');
  };

  /* =========================================================
     PRESETS
  ========================================================= */
  window.setPreset = function(name, date, time) {
    document.getElementById('cd-event-name').value = name;
    document.getElementById('cd-date').value = date;
    document.getElementById('cd-time').value = time;
    // auto-detect mode
    const d = new Date(date + 'T' + time);
    setMode(d < new Date() ? 'timesince' : 'countdown');
    startCountdown();
  };

  /* =========================================================
     START / RESET
  ========================================================= */
  window.startCountdown = function() {
    const dateVal = document.getElementById('cd-date').value;
    const timeVal = document.getElementById('cd-time').value || '00:00';
    if (!dateVal) { alert('Please select a date first.'); return; }

    targetDate = new Date(dateVal + 'T' + timeVal + ':00');
    startDate  = new Date(); // now = start of progress

    const nameRaw = document.getElementById('cd-event-name').value.trim();
    const name = nameRaw || formatDateLabel(targetDate);

    document.getElementById('cd-display-name').textContent = name;
    confettiShown = false;

    clearInterval(timerInterval);
    showCountdownUnits();
    tick();
    timerInterval = setInterval(tick, 1000);
  };

  window.resetAll = function() {
    clearInterval(timerInterval);
    targetDate = null;
    startDate  = null;
    confettiShown = false;
    document.getElementById('cd-display-name').textContent = 'Set a date above to start your countdown';
    document.getElementById('cd-display-mode').textContent = '-- select a date --';
    ['cd-days','cd-hours','cd-minutes','cd-seconds'].forEach(id => {
      document.getElementById(id).textContent = '--';
    });
    document.getElementById('cd-facts').style.display = 'none';
    document.getElementById('cd-progress-wrap').style.display = 'none';
    showCountdownUnits();
  };

  /* =========================================================
     TICK
  ========================================================= */
  function tick() {
    if (!targetDate) return;
    const now  = new Date();
    const diff = targetDate - now; // ms, can be negative

    if (currentMode === 'countdown') {
      if (diff <= 0) {
        showFinished();
        return;
      }
      renderDiff(diff, 'countdown');
    } else {
      // time since — diff is negative if past
      const absDiff = Math.abs(diff);
      renderDiff(absDiff, 'timesince');
    }
  }

  function renderDiff(diffMs, mode) {
    const totalSec = Math.floor(diffMs / 1000);
    const d = Math.floor(totalSec / 86400);
    const h = Math.floor((totalSec % 86400) / 3600);
    const m = Math.floor((totalSec % 3600) / 60);
    const s = totalSec % 60;

    setNum('cd-days',    pad(d),    'd');
    setNum('cd-hours',   pad(h),    'h');
    setNum('cd-minutes', pad(m),    'm');
    setNum('cd-seconds', pad(s),    's');

    const modeText = mode === 'countdown'
      ? 'until ' + formatDateLabel(targetDate)
      : 'since '  + formatDateLabel(targetDate);
    document.getElementById('cd-display-mode').textContent = modeText;

    // Progress bar
    updateProgress(diffMs, mode);

    // Fun facts
    updateFacts(totalSec, mode);
  }

  function setNum(id, val, key) {
    const el = document.getElementById(id);
    if (el.textContent !== val) {
      el.textContent = val;
      if (prevVals[key] !== val) {
        el.classList.remove('flip-anim');
        void el.offsetWidth; // reflow
        el.classList.add('flip-anim');
      }
      prevVals[key] = val;
    }
  }

  /* =========================================================
     PROGRESS BAR
  ========================================================= */
  function updateProgress(remainingMs, mode) {
    const wrap = document.getElementById('cd-progress-wrap');
    if (!startDate || !targetDate) { wrap.style.display = 'none'; return; }
    wrap.style.display = 'block';

    if (mode === 'countdown') {
      const totalSpan = targetDate - startDate;
      const elapsed   = totalSpan - remainingMs;
      const pct = Math.min(100, Math.max(0, (elapsed / totalSpan) * 100));
      document.getElementById('cd-prog-bar').style.width = pct.toFixed(1) + '%';
      document.getElementById('cd-prog-pct').textContent  = pct.toFixed(1) + '% elapsed';
      document.getElementById('cd-prog-start').textContent = 'Started';
      document.getElementById('cd-prog-end').textContent   = formatDateLabel(targetDate);
    } else {
      // timesince: progress = how far into the day since event
      const dayMs = 86400000;
      const pct = Math.min(100, (remainingMs % dayMs) / dayMs * 100);
      document.getElementById('cd-prog-bar').style.width = pct.toFixed(1) + '%';
      document.getElementById('cd-prog-pct').textContent  = 'Time since event';
      document.getElementById('cd-prog-start').textContent = formatDateLabel(targetDate);
      document.getElementById('cd-prog-end').textContent   = 'Now';
    }
  }

  /* =========================================================
     FUN FACTS
  ========================================================= */
  function updateFacts(totalSec, mode) {
    const factsEl = document.getElementById('cd-facts');
    if (totalSec < 1) { factsEl.style.display = 'none'; return; }
    factsEl.style.display = 'block';

    const weeks   = (totalSec / 604800).toFixed(1);
    const hours   = Math.floor(totalSec / 3600).toLocaleString();
    const minutes = Math.floor(totalSec / 60).toLocaleString();
    const months  = (totalSec / 2592000).toFixed(1);
    const label   = mode === 'countdown' ? 'remaining' : 'ago';

    factsEl.innerHTML =
      `<strong>Fun Facts:</strong><br>` +
      `That's <strong>${weeks}</strong> weeks ${label}, or <strong>${hours}</strong> hours, ` +
      `or <strong>${minutes}</strong> minutes, or <strong>${months}</strong> months.`;
  }

  /* =========================================================
     FINISHED
  ========================================================= */
  function showFinished() {
    clearInterval(timerInterval);
    document.getElementById('cd-countdown-units').style.display = 'none';
    const fin = document.getElementById('cd-finished');
    fin.classList.add('show');

    const name = document.getElementById('cd-display-name').textContent;
    document.getElementById('cd-finished-msg').textContent = name + ' has arrived!';
    document.getElementById('cd-finished-sub').textContent = 'The countdown is complete.';
    document.getElementById('cd-display-mode').textContent = '';

    if (!confettiShown) {
      confettiShown = true;
      launchConfetti();
    }
  }

  function showCountdownUnits() {
    document.getElementById('cd-countdown-units').style.display = 'block';
    const fin = document.getElementById('cd-finished');
    fin.classList.remove('show');
  }

  /* =========================================================
     CONFETTI
  ========================================================= */
  function launchConfetti() {
    const canvas = document.getElementById('cd-confetti');
    canvas.style.display = 'block';
    const ctx = canvas.getContext('2d');
    canvas.width  = window.innerWidth;
    canvas.height = window.innerHeight;

    const colors = ['#6d28d9','#fbbf24','#34d399','#f87171','#60a5fa','#f472b6','#a78bfa'];
    const pieces = Array.from({length: 120}, () => ({
      x:  Math.random() * canvas.width,
      y:  Math.random() * -canvas.height,
      w:  6 + Math.random() * 8,
      h:  10 + Math.random() * 6,
      r:  Math.random() * Math.PI * 2,
      dr: (Math.random() - .5) * .15,
      vx: (Math.random() - .5) * 3,
      vy: 2.5 + Math.random() * 3,
      color: colors[Math.floor(Math.random() * colors.length)],
    }));

    let frame = 0;
    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      pieces.forEach(p => {
        ctx.save();
        ctx.translate(p.x + p.w/2, p.y + p.h/2);
        ctx.rotate(p.r);
        ctx.fillStyle = p.color;
        ctx.globalAlpha = .88;
        ctx.fillRect(-p.w/2, -p.h/2, p.w, p.h);
        ctx.restore();
        p.x  += p.vx;
        p.y  += p.vy;
        p.r  += p.dr;
        p.vy += .04; // gravity
        if (p.y > canvas.height) {
          p.y  = -20;
          p.x  = Math.random() * canvas.width;
          p.vy = 2.5 + Math.random() * 2;
        }
      });
      frame++;
      if (frame < 220) requestAnimationFrame(draw);
      else { ctx.clearRect(0,0,canvas.width,canvas.height); canvas.style.display='none'; }
    }
    draw();
  }

  /* =========================================================
     MULTIPLE COUNTDOWNS LIST
  ========================================================= */
  window.addToList = function() {
    const dateVal = document.getElementById('cd-date').value;
    const timeVal = document.getElementById('cd-time').value || '00:00';
    if (!dateVal) { alert('Please select a date first.'); return; }

    const nameRaw = document.getElementById('cd-event-name').value.trim();
    const iso = dateVal + 'T' + timeVal + ':00';
    const name = nameRaw || formatDateLabel(new Date(iso));

    // avoid duplicates
    if (savedEvents.find(e => e.iso === iso && e.name === name)) return;

    savedEvents.push({ name, iso, mode: currentMode });
    renderList();

    // start list update interval if not running
    if (!listInterval) listInterval = setInterval(renderList, 1000);
  };

  window.removeEvent = function(idx) {
    savedEvents.splice(idx, 1);
    renderList();
    if (savedEvents.length === 0) { clearInterval(listInterval); listInterval = null; }
  };

  window.clearList = function() {
    savedEvents = [];
    clearInterval(listInterval);
    listInterval = null;
    renderList();
  };

  function renderList() {
    const container = document.getElementById('cd-event-cards');
    const emptyEl   = document.getElementById('cd-list-empty');
    if (savedEvents.length === 0) {
      container.innerHTML = '';
      container.appendChild(emptyEl);
      emptyEl.style.display = 'block';
      return;
    }
    emptyEl.style.display = 'none';

    // Build all cards HTML
    let html = '';
    savedEvents.forEach((ev, i) => {
      const target = new Date(ev.iso);
      const now    = new Date();
      const diffMs = target - now;
      let timeStr;

      if (ev.mode === 'countdown') {
        if (diffMs <= 0) {
          timeStr = '&#127881; Now!';
        } else {
          const totalSec = Math.floor(diffMs / 1000);
          const d = Math.floor(totalSec / 86400);
          const h = Math.floor((totalSec % 86400) / 3600);
          const m = Math.floor((totalSec % 3600) / 60);
          const s = totalSec % 60;
          timeStr = d > 0
            ? `${d}d ${pad(h)}h ${pad(m)}m ${pad(s)}s`
            : `${pad(h)}h ${pad(m)}m ${pad(s)}s`;
        }
      } else {
        const absSec = Math.floor(Math.abs(diffMs) / 1000);
        const d = Math.floor(absSec / 86400);
        const h = Math.floor((absSec % 86400) / 3600);
        timeStr = d > 0 ? `${d}d ${pad(h)}h ago` : `${pad(h)}h ago`;
      }

      const dateLabel = target.toLocaleDateString('en-US', {month:'short', day:'numeric', year:'numeric'});
      html += `
        <div class="cd-event-card">
          <div>
            <div class="cd-event-card-name">${escHtml(ev.name)}</div>
            <div class="cd-event-card-date">${dateLabel} &middot; ${ev.mode === 'timesince' ? 'Time since' : 'Countdown'}</div>
          </div>
          <div class="cd-event-card-time">${timeStr}</div>
          <button class="cd-event-card-remove" onclick="removeEvent(${i})" title="Remove">&#10005;</button>
        </div>`;
    });
    container.innerHTML = html;
  }

  /* =========================================================
     HELPERS
  ========================================================= */
  function pad(n) { return String(n).padStart(2, '0'); }

  function formatDateLabel(d) {
    return d.toLocaleDateString('en-US', { weekday:'short', month:'short', day:'numeric', year:'numeric' });
  }

  function escHtml(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  /* =========================================================
     INIT — set default date to tomorrow
  ========================================================= */
  (function init() {
    const tomorrow = new Date();
    tomorrow.setDate(tomorrow.getDate() + 1);
    const y = tomorrow.getFullYear();
    const mo = String(tomorrow.getMonth() + 1).padStart(2, '0');
    const da = String(tomorrow.getDate()).padStart(2, '0');
    document.getElementById('cd-date').value = `${y}-${mo}-${da}`;
    document.getElementById('cd-date').min   = new Date().toISOString().split('T')[0];
  })();

})();
</script>

</div>

---

## How to Use the Countdown Timer

1. **Enter a date** — Pick any future or past date using the date picker. Add an optional time for precision down to the second.
2. **Name your event** — Type a label like "Product Launch" or "Summer Vacation" in the Event Name field. This is optional but keeps things organized.
3. **Choose a mode** — Use **Countdown** for future dates (days until) or **Time Since** for past dates (how long ago).
4. **Hit Start** — The large display begins updating every second with days, hours, minutes, and seconds.
5. **Use presets** — Click any quick-preset chip (New Year, Christmas, Halloween, etc.) to instantly load a popular event.
6. **Track multiple events** — After configuring an event, click **+ Add to List** to pin it to the live multi-event panel below the main display.
7. **Celebrate** — When a countdown hits zero, a confetti animation fires automatically.

---

## Popular Events to Count Down To

| Event | Typical Date |
|---|---|
| New Year's Day | January 1 |
| Valentine's Day | February 14 |
| Summer Solstice | June 21 |
| Halloween | October 31 |
| Thanksgiving (US) | 4th Thursday, November |
| Christmas | December 25 |
| New Year's Eve | December 31 |

Beyond holidays, countdowns work great for personal milestones — project deadlines, exam dates, anniversaries, travel departures, product launches, and sports events.

---

## Related Tools

> Calculate your exact age → [Age Calculator](/tools/age-calculator/)

> Stay focused with Pomodoro → [Pomodoro Timer](/tools/pomodoro-timer/)

> Convert between time units → [Unit Converter](/tools/unit-converter/)

> Working across time zones? → [Timezone Converter](/tools/timezone-converter/) — convert times between any cities instantly
