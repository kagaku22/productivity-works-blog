---
title: "Pomodoro Timer"
date: 2025-05-16
description: "Free online Pomodoro timer. Boost your productivity with customizable work/break intervals, session tracking, and audio notifications — no sign-up required."
categories: ["Free Tools"]
slug: "pomodoro-timer"
ShowToc: false
cover:
  image: "/images/covers/pomodoro-timer.png"
  alt: "Pomodoro Timer"
---

Stay focused and accomplish more with this free browser-based Pomodoro timer — no downloads or sign-ups needed. Customize your work and break intervals, track your daily focus sessions, and receive audio notifications when each phase ends.

<div id="pm-app">
<style>
  #pm-app {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    max-width: 640px;
    margin: 0 auto;
    padding: 1rem;
    color: #1e293b;
  }

  /* Preset buttons */
  #pm-app .pm-presets {
    display: flex;
    gap: 0.5rem;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 1.5rem;
  }
  #pm-app .pm-preset-btn {
    background: #f1f5f9;
    border: 1.5px solid #cbd5e1;
    border-radius: 999px;
    padding: 0.35rem 1rem;
    font-size: 0.85rem;
    font-weight: 500;
    color: #475569;
    cursor: pointer;
    transition: background 0.15s, border-color 0.15s, color 0.15s;
  }
  #pm-app .pm-preset-btn:hover,
  #pm-app .pm-preset-btn.pm-preset-active {
    background: #0f172a;
    border-color: #0f172a;
    color: #f8fafc;
  }

  /* Timer ring */
  #pm-app .pm-ring-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 1.5rem;
    position: relative;
  }
  #pm-app .pm-svg {
    width: 220px;
    height: 220px;
    transform: rotate(-90deg);
  }
  #pm-app .pm-ring-bg {
    fill: none;
    stroke: #e2e8f0;
    stroke-width: 12;
  }
  #pm-app .pm-ring-progress {
    fill: none;
    stroke: #334155;
    stroke-width: 12;
    stroke-linecap: round;
    transition: stroke-dashoffset 0.5s linear, stroke 0.4s;
  }
  #pm-app .pm-ring-progress.pm-break {
    stroke: #0ea5e9;
  }
  #pm-app .pm-ring-progress.pm-long {
    stroke: #8b5cf6;
  }
  #pm-app .pm-timer-label {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    pointer-events: none;
  }
  #pm-app .pm-time-display {
    font-size: 3rem;
    font-weight: 700;
    letter-spacing: -1px;
    color: #0f172a;
    line-height: 1;
  }
  #pm-app .pm-phase-label {
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: #64748b;
    margin-top: 0.35rem;
  }

  /* Controls */
  #pm-app .pm-controls {
    display: flex;
    gap: 0.625rem;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 1.5rem;
  }
  #pm-app .pm-btn {
    border: none;
    border-radius: 0.5rem;
    padding: 0.6rem 1.4rem;
    font-size: 0.95rem;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s, transform 0.1s;
  }
  #pm-app .pm-btn:active { transform: scale(0.97); }
  #pm-app .pm-btn-primary {
    background: #0f172a;
    color: #f8fafc;
  }
  #pm-app .pm-btn-primary:hover { background: #1e293b; }
  #pm-app .pm-btn-secondary {
    background: #f1f5f9;
    color: #334155;
    border: 1.5px solid #cbd5e1;
  }
  #pm-app .pm-btn-secondary:hover { background: #e2e8f0; }
  #pm-app .pm-btn-skip {
    background: #f1f5f9;
    color: #64748b;
    border: 1.5px solid #cbd5e1;
    font-size: 0.85rem;
  }
  #pm-app .pm-btn-skip:hover { background: #e2e8f0; }

  /* Session tracker */
  #pm-app .pm-session-tracker {
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 0.75rem;
    padding: 1rem 1.25rem;
    margin-bottom: 1.25rem;
  }
  #pm-app .pm-session-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.75rem;
  }
  #pm-app .pm-session-title {
    font-size: 0.8rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.07em;
    color: #64748b;
  }
  #pm-app .pm-focus-total {
    font-size: 0.8rem;
    color: #64748b;
  }
  #pm-app .pm-focus-total span {
    font-weight: 700;
    color: #0f172a;
  }
  #pm-app .pm-dots {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    align-items: center;
  }
  #pm-app .pm-dot {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    border: 2px solid #cbd5e1;
    background: transparent;
    transition: background 0.2s, border-color 0.2s;
  }
  #pm-app .pm-dot.pm-dot-done {
    background: #334155;
    border-color: #334155;
  }
  #pm-app .pm-dot.pm-dot-current {
    border-color: #0f172a;
    box-shadow: 0 0 0 2px #94a3b8;
    background: #e2e8f0;
  }
  #pm-app .pm-session-count {
    font-size: 0.82rem;
    color: #64748b;
    margin-top: 0.5rem;
  }
  #pm-app .pm-session-count strong { color: #0f172a; }

  /* Settings */
  #pm-app .pm-settings-wrap {
    border: 1px solid #e2e8f0;
    border-radius: 0.75rem;
    overflow: hidden;
  }
  #pm-app .pm-settings-toggle {
    width: 100%;
    background: #f8fafc;
    border: none;
    padding: 0.75rem 1.25rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.9rem;
    font-weight: 600;
    color: #334155;
    cursor: pointer;
    text-align: left;
  }
  #pm-app .pm-settings-toggle:hover { background: #f1f5f9; }
  #pm-app .pm-chevron {
    transition: transform 0.2s;
    font-size: 0.75rem;
    color: #94a3b8;
  }
  #pm-app .pm-chevron.pm-open { transform: rotate(180deg); }
  #pm-app .pm-settings-body {
    display: none;
    padding: 1rem 1.25rem 1.25rem;
    background: #ffffff;
    border-top: 1px solid #e2e8f0;
  }
  #pm-app .pm-settings-body.pm-visible { display: block; }
  #pm-app .pm-setting-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 0.875rem;
    gap: 1rem;
  }
  #pm-app .pm-setting-row:last-child { margin-bottom: 0; }
  #pm-app .pm-setting-label {
    font-size: 0.88rem;
    color: #475569;
    flex: 1;
  }
  #pm-app .pm-setting-input {
    width: 70px;
    padding: 0.3rem 0.5rem;
    border: 1.5px solid #cbd5e1;
    border-radius: 0.4rem;
    font-size: 0.9rem;
    font-weight: 600;
    color: #0f172a;
    text-align: center;
    background: #f8fafc;
    outline: none;
  }
  #pm-app .pm-setting-input:focus { border-color: #334155; background: #fff; }
  #pm-app .pm-toggle-switch {
    position: relative;
    width: 42px;
    height: 24px;
    flex-shrink: 0;
  }
  #pm-app .pm-toggle-switch input {
    opacity: 0;
    width: 0;
    height: 0;
    position: absolute;
  }
  #pm-app .pm-slider {
    position: absolute;
    inset: 0;
    background: #cbd5e1;
    border-radius: 999px;
    cursor: pointer;
    transition: background 0.2s;
  }
  #pm-app .pm-slider::before {
    content: "";
    position: absolute;
    width: 18px;
    height: 18px;
    left: 3px;
    top: 3px;
    background: #fff;
    border-radius: 50%;
    transition: transform 0.2s;
  }
  #pm-app .pm-toggle-switch input:checked + .pm-slider { background: #334155; }
  #pm-app .pm-toggle-switch input:checked + .pm-slider::before { transform: translateX(18px); }
  #pm-app .pm-settings-note {
    font-size: 0.78rem;
    color: #94a3b8;
    margin-top: 0.75rem;
  }

  /* Cross-links */
  #pm-app .pm-links {
    margin-top: 1.5rem;
    padding-top: 1rem;
    border-top: 1px solid #e2e8f0;
    font-size: 0.875rem;
    color: #64748b;
    line-height: 1.9;
  }
  #pm-app .pm-links a {
    color: #334155;
    font-weight: 600;
    text-decoration: underline;
    text-underline-offset: 2px;
  }
  #pm-app .pm-links a:hover { color: #0f172a; }

  @media (max-width: 400px) {
    #pm-app .pm-time-display { font-size: 2.4rem; }
    #pm-app .pm-svg { width: 190px; height: 190px; }
    #pm-app .pm-btn { padding: 0.55rem 1rem; font-size: 0.88rem; }
  }
</style>

<!-- Preset buttons -->
<div class="pm-presets">
  <button class="pm-preset-btn pm-preset-active" data-preset="classic">Classic (25/5)</button>
  <button class="pm-preset-btn" data-preset="deep">Deep Work (50/10)</button>
  <button class="pm-preset-btn" data-preset="sprint">Sprint (15/3)</button>
</div>

<!-- Timer ring -->
<div class="pm-ring-wrap">
  <svg class="pm-svg" viewBox="0 0 220 220" aria-hidden="true">
    <circle class="pm-ring-bg" cx="110" cy="110" r="96"/>
    <circle class="pm-ring-progress" id="pm-ring" cx="110" cy="110" r="96"/>
  </svg>
  <div class="pm-timer-label">
    <div class="pm-time-display" id="pm-time">25:00</div>
    <div class="pm-phase-label" id="pm-phase">Work</div>
  </div>
</div>

<!-- Controls -->
<div class="pm-controls">
  <button class="pm-btn pm-btn-primary" id="pm-start">Start</button>
  <button class="pm-btn pm-btn-secondary" id="pm-reset">Reset</button>
  <button class="pm-btn pm-btn-skip" id="pm-skip">Skip &#x276F;</button>
</div>

<!-- Session tracker -->
<div class="pm-session-tracker">
  <div class="pm-session-header">
    <div class="pm-session-title">Sessions</div>
    <div class="pm-focus-total">Focus today: <span id="pm-focus-today">0 min</span></div>
  </div>
  <div class="pm-dots" id="pm-dots"></div>
  <div class="pm-session-count">Session <strong id="pm-cur-session">1</strong> of <strong id="pm-total-sessions">4</strong> before long break</div>
</div>

<!-- Settings -->
<div class="pm-settings-wrap">
  <button class="pm-settings-toggle" id="pm-settings-toggle" aria-expanded="false">
    Settings
    <span class="pm-chevron" id="pm-chevron">&#9660;</span>
  </button>
  <div class="pm-settings-body" id="pm-settings-body">
    <div class="pm-setting-row">
      <label class="pm-setting-label" for="pm-s-work">Work duration (min)</label>
      <input class="pm-setting-input" type="number" id="pm-s-work" min="1" max="60" value="25">
    </div>
    <div class="pm-setting-row">
      <label class="pm-setting-label" for="pm-s-short">Short break (min)</label>
      <input class="pm-setting-input" type="number" id="pm-s-short" min="1" max="30" value="5">
    </div>
    <div class="pm-setting-row">
      <label class="pm-setting-label" for="pm-s-long">Long break (min)</label>
      <input class="pm-setting-input" type="number" id="pm-s-long" min="1" max="60" value="15">
    </div>
    <div class="pm-setting-row">
      <label class="pm-setting-label" for="pm-s-sessions">Sessions before long break</label>
      <input class="pm-setting-input" type="number" id="pm-s-sessions" min="2" max="8" value="4">
    </div>
    <div class="pm-setting-row">
      <label class="pm-setting-label" for="pm-s-autobreak">Auto-start breaks</label>
      <label class="pm-toggle-switch">
        <input type="checkbox" id="pm-s-autobreak">
        <span class="pm-slider"></span>
      </label>
    </div>
    <div class="pm-setting-row">
      <label class="pm-setting-label" for="pm-s-autowork">Auto-start work</label>
      <label class="pm-toggle-switch">
        <input type="checkbox" id="pm-s-autowork">
        <span class="pm-slider"></span>
      </label>
    </div>
    <p class="pm-settings-note">Changes apply when the current session ends or after a reset.</p>
  </div>
</div>

<!-- Cross-links -->
<div class="pm-links">
  &rsaquo; Test your typing speed &rarr; <a href="/tools/typing-speed-test/">Typing Speed Test</a><br>
  &rsaquo; Plan your budget &rarr; <a href="/tools/budget-calculator/">50/30/20 Budget Calculator</a><br>
  &rsaquo; Track time zones &rarr; <a href="/tools/timezone-converter/">Time Zone Converter</a>
</div>

<script>
(function () {
  "use strict";

  // Constants
  var RADIUS = 96;
  var CIRCUMFERENCE = 2 * Math.PI * RADIUS;

  var PRESETS = {
    classic: { work: 25, short: 5,  long: 15, sessions: 4 },
    deep:    { work: 50, short: 10, long: 20, sessions: 4 },
    sprint:  { work: 15, short: 3,  long: 10, sessions: 4 }
  };

  // State
  var cfg = { work: 25, short: 5, long: 15, sessions: 4, autoBreak: false, autoWork: false };
  var phase = "work";        // "work" | "short" | "long"
  var sessionsDone = 0;      // completed work sessions in current cycle
  var totalWorkMin = 0;      // total focus minutes accumulated today
  var timeLeft = cfg.work * 60;
  var totalTime = cfg.work * 60;
  var running = false;
  var ticker = null;

  // DOM refs
  var timeEl       = document.getElementById("pm-time");
  var phaseEl      = document.getElementById("pm-phase");
  var ring         = document.getElementById("pm-ring");
  var startBtn     = document.getElementById("pm-start");
  var resetBtn     = document.getElementById("pm-reset");
  var skipBtn      = document.getElementById("pm-skip");
  var dotsEl       = document.getElementById("pm-dots");
  var curSessEl    = document.getElementById("pm-cur-session");
  var totalSessEl  = document.getElementById("pm-total-sessions");
  var focusEl      = document.getElementById("pm-focus-today");
  var settingsBtn  = document.getElementById("pm-settings-toggle");
  var settingsBody = document.getElementById("pm-settings-body");
  var chevron      = document.getElementById("pm-chevron");
  var inWork       = document.getElementById("pm-s-work");
  var inShort      = document.getElementById("pm-s-short");
  var inLong       = document.getElementById("pm-s-long");
  var inSess       = document.getElementById("pm-s-sessions");
  var inAutoBreak  = document.getElementById("pm-s-autobreak");
  var inAutoWork   = document.getElementById("pm-s-autowork");
  var presetBtns   = document.querySelectorAll("#pm-app .pm-preset-btn");

  // Ring initialisation
  ring.style.strokeDasharray  = CIRCUMFERENCE;
  ring.style.strokeDashoffset = 0;

  // Helpers
  function fmt(sec) {
    var m = Math.floor(sec / 60);
    var s = sec % 60;
    return (m < 10 ? "0" : "") + m + ":" + (s < 10 ? "0" : "") + s;
  }

  function phaseLabel(p) {
    return p === "work" ? "Work" : p === "short" ? "Short Break" : "Long Break";
  }

  function updateRing() {
    var ratio = totalTime > 0 ? timeLeft / totalTime : 0;
    ring.style.strokeDashoffset = CIRCUMFERENCE * (1 - ratio);
    ring.className = "pm-ring-progress" +
      (phase === "short" ? " pm-break" : phase === "long" ? " pm-long" : "");
  }

  function buildDots() {
    dotsEl.innerHTML = "";
    for (var i = 0; i < cfg.sessions; i++) {
      var d = document.createElement("div");
      d.className = "pm-dot" +
        (i < sessionsDone ? " pm-dot-done" :
         (i === sessionsDone && phase === "work") ? " pm-dot-current" : "");
      dotsEl.appendChild(d);
    }
  }

  function updateDisplay() {
    timeEl.textContent = fmt(timeLeft);
    phaseEl.textContent = phaseLabel(phase);
    document.title = fmt(timeLeft) + " - " + phaseLabel(phase) + " | Pomodoro";
    updateRing();
    buildDots();
    curSessEl.textContent   = Math.min(sessionsDone + 1, cfg.sessions);
    totalSessEl.textContent = cfg.sessions;
    focusEl.textContent     = totalWorkMin + " min";
  }

  // Audio — Web Audio API chime (no external files)
  function playChime() {
    try {
      var ctx = new (window.AudioContext || window.webkitAudioContext)();
      var notes = [523.25, 659.25, 783.99, 1046.5]; // C5 E5 G5 C6
      notes.forEach(function (freq, i) {
        var osc  = ctx.createOscillator();
        var gain = ctx.createGain();
        osc.connect(gain);
        gain.connect(ctx.destination);
        osc.type = "sine";
        osc.frequency.value = freq;
        var t = ctx.currentTime + i * 0.18;
        gain.gain.setValueAtTime(0, t);
        gain.gain.linearRampToValueAtTime(0.25, t + 0.05);
        gain.gain.exponentialRampToValueAtTime(0.001, t + 0.5);
        osc.start(t);
        osc.stop(t + 0.55);
      });
    } catch (e) {
      // AudioContext unavailable — silent fallback
    }
  }

  // Timer engine
  function tick() {
    if (!running) return;
    timeLeft--;
    if (timeLeft <= 0) {
      timeLeft = 0;
      updateDisplay();
      clearInterval(ticker);
      running = false;
      onPhaseEnd();
      return;
    }
    updateDisplay();
  }

  function onPhaseEnd() {
    playChime();
    startBtn.textContent = "Start";

    if (phase === "work") {
      sessionsDone++;
      totalWorkMin += cfg.work;
      if (sessionsDone >= cfg.sessions) {
        sessionsDone = 0;
        setPhase("long");
        if (cfg.autoBreak) startTimer();
      } else {
        setPhase("short");
        if (cfg.autoBreak) startTimer();
      }
    } else {
      setPhase("work");
      if (cfg.autoWork) startTimer();
    }
  }

  function setPhase(p) {
    phase = p;
    var dur = p === "work" ? cfg.work : p === "short" ? cfg.short : cfg.long;
    timeLeft  = dur * 60;
    totalTime = dur * 60;
    updateDisplay();
  }

  function startTimer() {
    if (running) return;
    running = true;
    startBtn.textContent = "Pause";
    ticker = setInterval(tick, 1000);
  }

  function pauseTimer() {
    running = false;
    clearInterval(ticker);
    startBtn.textContent = "Start";
  }

  function resetTimer() {
    pauseTimer();
    sessionsDone = 0;
    setPhase("work");
  }

  function skipPhase() {
    pauseTimer();
    // Credit partial work time on skip
    if (phase === "work" && timeLeft < cfg.work * 60) {
      var elapsed = Math.floor((cfg.work * 60 - timeLeft) / 60);
      totalWorkMin += elapsed;
      sessionsDone++;
      if (sessionsDone >= cfg.sessions) sessionsDone = 0;
    }
    if (phase === "work") {
      setPhase(sessionsDone >= cfg.sessions ? "long" : "short");
      if (sessionsDone >= cfg.sessions) sessionsDone = 0;
    } else {
      setPhase("work");
    }
  }

  // Settings
  function applySettings() {
    cfg.work      = Math.min(60, Math.max(1, parseInt(inWork.value,  10) || 25));
    cfg.short     = Math.min(30, Math.max(1, parseInt(inShort.value, 10) || 5));
    cfg.long      = Math.min(60, Math.max(1, parseInt(inLong.value,  10) || 15));
    cfg.sessions  = Math.min(8,  Math.max(2, parseInt(inSess.value,  10) || 4));
    cfg.autoBreak = inAutoBreak.checked;
    cfg.autoWork  = inAutoWork.checked;
    // Clamp displayed values
    inWork.value  = cfg.work;
    inShort.value = cfg.short;
    inLong.value  = cfg.long;
    inSess.value  = cfg.sessions;
    totalSessEl.textContent = cfg.sessions;
  }

  function applyPreset(key) {
    var p = PRESETS[key];
    if (!p) return;
    inWork.value  = p.work;
    inShort.value = p.short;
    inLong.value  = p.long;
    inSess.value  = p.sessions;
    applySettings();
    resetTimer();
    presetBtns.forEach(function (b) {
      b.classList.toggle("pm-preset-active", b.dataset.preset === key);
    });
  }

  // Event listeners
  startBtn.addEventListener("click", function () {
    if (running) pauseTimer(); else startTimer();
  });

  resetBtn.addEventListener("click", function () {
    applySettings();
    resetTimer();
  });

  skipBtn.addEventListener("click", skipPhase);

  settingsBtn.addEventListener("click", function () {
    var open = settingsBody.classList.toggle("pm-visible");
    chevron.classList.toggle("pm-open", open);
    settingsBtn.setAttribute("aria-expanded", String(open));
  });

  [inWork, inShort, inLong, inSess].forEach(function (el) {
    el.addEventListener("change", function () {
      applySettings();
      if (!running) setPhase(phase);
    });
  });

  [inAutoBreak, inAutoWork].forEach(function (el) {
    el.addEventListener("change", applySettings);
  });

  presetBtns.forEach(function (btn) {
    btn.addEventListener("click", function () {
      applyPreset(btn.dataset.preset);
    });
  });

  // Reset tab title on page leave
  window.addEventListener("beforeunload", function () {
    document.title = "Pomodoro Timer";
  });

  // Init
  applySettings();
  setPhase("work");
})();
</script>
</div>

---

## Related Tools

> [Age Calculator](/tools/age-calculator/)
> [Countdown Timer](/tools/countdown-timer/)
> [Date Calculator](/tools/date-calculator/)

