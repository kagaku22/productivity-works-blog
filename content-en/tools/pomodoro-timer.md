---
title: "Pomodoro Timer - Free Online Focus Timer"
date: 2025-05-16
description: "Free online Pomodoro timer with customizable work/break intervals. Boost productivity with the Pomodoro Technique. Track sessions, set goals, and stay focused."
categories: ["Free Tools"]
tags: ["pomodoro", "timer", "productivity", "focus", "time management"]
slug: "pomodoro-timer"
aliases: ["/tools/focus-timer/", "/tools/productivity-timer/"]
cover:
  image: "/images/covers/pomodoro-timer.png"
  alt: "Pomodoro Timer"
ShowToc: false
---

<div id="pomodoro-app">

<style>
  #pomodoro-app {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
    max-width: 680px;
    margin: 0 auto;
    padding: 16px;
    color: #2c3e50;
  }

  /* Mode tabs */
  #pomodoro-app .pom-tabs {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin-bottom: 28px;
    flex-wrap: wrap;
  }
  #pomodoro-app .pom-tab {
    padding: 8px 20px;
    border: 2px solid #e74c3c;
    border-radius: 24px;
    background: transparent;
    color: #e74c3c;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
  }
  #pomodoro-app .pom-tab:hover {
    background: #fdecea;
  }
  #pomodoro-app .pom-tab.active {
    background: #e74c3c;
    color: #fff;
  }

  /* Circular timer */
  #pomodoro-app .pom-ring-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 28px;
  }
  #pomodoro-app .pom-svg {
    transform: rotate(-90deg);
    filter: drop-shadow(0 4px 16px rgba(231,76,60,0.18));
  }
  #pomodoro-app .pom-ring-bg {
    fill: none;
    stroke: #f5c6c2;
    stroke-width: 10;
  }
  #pomodoro-app .pom-ring-prog {
    fill: none;
    stroke: #e74c3c;
    stroke-width: 10;
    stroke-linecap: round;
    transition: stroke-dashoffset 1s linear, stroke 0.4s;
  }
  #pomodoro-app .pom-ring-break {
    stroke: #27ae60;
  }
  #pomodoro-app .pom-time-label {
    font-size: clamp(44px, 12vw, 72px);
    font-weight: 700;
    letter-spacing: 2px;
    color: #e74c3c;
    margin-top: -8px;
    font-variant-numeric: tabular-nums;
    transition: color 0.4s;
  }
  #pomodoro-app .pom-time-label.break-mode {
    color: #27ae60;
  }
  #pomodoro-app .pom-mode-label {
    font-size: 15px;
    font-weight: 600;
    color: #7f8c8d;
    margin-top: 4px;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* Buttons */
  #pomodoro-app .pom-controls {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin-bottom: 24px;
    flex-wrap: wrap;
  }
  #pomodoro-app .pom-btn {
    padding: 12px 28px;
    border-radius: 8px;
    border: none;
    font-size: 15px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.18s;
    letter-spacing: 0.5px;
  }
  #pomodoro-app .pom-btn-start {
    background: #e74c3c;
    color: #fff;
    min-width: 120px;
  }
  #pomodoro-app .pom-btn-start:hover {
    background: #c0392b;
    transform: translateY(-1px);
  }
  #pomodoro-app .pom-btn-start.pause {
    background: #e67e22;
  }
  #pomodoro-app .pom-btn-start.pause:hover {
    background: #ca6f1e;
  }
  #pomodoro-app .pom-btn-reset {
    background: #ecf0f1;
    color: #555;
  }
  #pomodoro-app .pom-btn-reset:hover {
    background: #dde1e2;
  }
  #pomodoro-app .pom-btn-skip {
    background: #ecf0f1;
    color: #555;
  }
  #pomodoro-app .pom-btn-skip:hover {
    background: #dde1e2;
  }

  /* Session counter */
  #pomodoro-app .pom-counter {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 16px;
    margin-bottom: 24px;
  }
  #pomodoro-app .pom-tomato-row {
    display: flex;
    gap: 6px;
    align-items: center;
  }
  #pomodoro-app .pom-tomato {
    font-size: 22px;
    opacity: 0.25;
    transition: opacity 0.3s;
  }
  #pomodoro-app .pom-tomato.done {
    opacity: 1;
  }
  #pomodoro-app .pom-counter-label {
    font-size: 13px;
    color: #7f8c8d;
    font-weight: 600;
  }

  /* Settings panel */
  #pomodoro-app .pom-settings-toggle {
    display: block;
    margin: 0 auto 12px;
    background: none;
    border: none;
    color: #7f8c8d;
    font-size: 13px;
    cursor: pointer;
    text-decoration: underline;
    padding: 4px 8px;
  }
  #pomodoro-app .pom-settings-toggle:hover {
    color: #e74c3c;
  }
  #pomodoro-app .pom-settings {
    background: #fafafa;
    border: 1px solid #eee;
    border-radius: 10px;
    padding: 18px 20px;
    margin-bottom: 20px;
    display: none;
  }
  #pomodoro-app .pom-settings.open {
    display: block;
  }
  #pomodoro-app .pom-settings-title {
    font-size: 13px;
    font-weight: 700;
    color: #888;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 14px;
  }
  #pomodoro-app .pom-settings-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 14px;
    margin-bottom: 14px;
  }
  #pomodoro-app .pom-setting-item label {
    display: block;
    font-size: 12px;
    color: #7f8c8d;
    margin-bottom: 4px;
    font-weight: 600;
  }
  #pomodoro-app .pom-setting-item input[type="number"] {
    width: 100%;
    padding: 7px 10px;
    border: 1px solid #ddd;
    border-radius: 6px;
    font-size: 15px;
    font-weight: 600;
    color: #2c3e50;
    box-sizing: border-box;
    outline: none;
  }
  #pomodoro-app .pom-setting-item input[type="number"]:focus {
    border-color: #e74c3c;
  }
  #pomodoro-app .pom-settings-apply {
    display: block;
    width: 100%;
    padding: 9px;
    background: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 6px;
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.18s;
  }
  #pomodoro-app .pom-settings-apply:hover {
    background: #c0392b;
  }

  /* Suggestion banner */
  #pomodoro-app .pom-suggestion {
    background: #eafaf1;
    border: 1px solid #a9dfbf;
    border-radius: 8px;
    padding: 12px 16px;
    margin-bottom: 18px;
    font-size: 14px;
    color: #1e8449;
    display: none;
    align-items: center;
    gap: 10px;
  }
  #pomodoro-app .pom-suggestion.show {
    display: flex;
  }
  #pomodoro-app .pom-suggestion button {
    margin-left: auto;
    padding: 5px 14px;
    background: #27ae60;
    color: #fff;
    border: none;
    border-radius: 5px;
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
  }
  #pomodoro-app .pom-suggestion button:hover {
    background: #1e8449;
  }

  /* Session history */
  #pomodoro-app .pom-history {
    margin-top: 8px;
  }
  #pomodoro-app .pom-history-title {
    font-size: 13px;
    font-weight: 700;
    color: #888;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 10px;
  }
  #pomodoro-app .pom-history-list {
    list-style: none;
    padding: 0;
    margin: 0;
    max-height: 200px;
    overflow-y: auto;
    border: 1px solid #eee;
    border-radius: 8px;
    background: #fafafa;
  }
  #pomodoro-app .pom-history-list:empty::after {
    content: "No sessions yet. Start your first Pomodoro!";
    display: block;
    padding: 16px;
    color: #aaa;
    font-size: 13px;
    text-align: center;
  }
  #pomodoro-app .pom-history-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 9px 14px;
    border-bottom: 1px solid #f0f0f0;
    font-size: 13px;
  }
  #pomodoro-app .pom-history-item:last-child {
    border-bottom: none;
  }
  #pomodoro-app .pom-history-dot {
    width: 9px;
    height: 9px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  #pomodoro-app .pom-history-dot.work { background: #e74c3c; }
  #pomodoro-app .pom-history-dot.short { background: #3498db; }
  #pomodoro-app .pom-history-dot.long { background: #27ae60; }
  #pomodoro-app .pom-history-text {
    flex: 1;
    color: #2c3e50;
    font-weight: 500;
  }
  #pomodoro-app .pom-history-time {
    color: #aaa;
    font-size: 12px;
    white-space: nowrap;
  }

  /* Responsive tweaks */
  @media (max-width: 480px) {
    #pomodoro-app .pom-btn {
      padding: 11px 18px;
      font-size: 14px;
    }
    #pomodoro-app .pom-settings-grid {
      grid-template-columns: 1fr 1fr;
    }
  }
</style>

<!-- Mode Tabs -->
<div class="pom-tabs">
  <button class="pom-tab active" data-mode="work">Work</button>
  <button class="pom-tab" data-mode="short">Short Break</button>
  <button class="pom-tab" data-mode="long">Long Break</button>
</div>

<!-- Circular Timer -->
<div class="pom-ring-wrap">
  <svg class="pom-svg" width="220" height="220" viewBox="0 0 220 220">
    <circle class="pom-ring-bg" cx="110" cy="110" r="96"/>
    <circle class="pom-ring-prog" id="pom-ring" cx="110" cy="110" r="96"
      stroke-dasharray="603.2" stroke-dashoffset="0"/>
    <!-- Embed time label in SVG via foreignObject for centering -->
  </svg>
  <div class="pom-time-label" id="pom-display">25:00</div>
  <div class="pom-mode-label" id="pom-mode-label">Focus Time</div>
</div>

<!-- Controls -->
<div class="pom-controls">
  <button class="pom-btn pom-btn-start" id="pom-start-btn">Start</button>
  <button class="pom-btn pom-btn-reset" id="pom-reset-btn">Reset</button>
  <button class="pom-btn pom-btn-skip" id="pom-skip-btn">Skip</button>
</div>

<!-- Session Counter (tomatoes) -->
<div class="pom-counter">
  <div class="pom-tomato-row" id="pom-tomatoes">
    <span class="pom-tomato" id="t0">&#127813;</span>
    <span class="pom-tomato" id="t1">&#127813;</span>
    <span class="pom-tomato" id="t2">&#127813;</span>
    <span class="pom-tomato" id="t3">&#127813;</span>
  </div>
  <span class="pom-counter-label" id="pom-counter-text">0 / 4 pomodoros</span>
</div>

<!-- Long Break Suggestion Banner -->
<div class="pom-suggestion" id="pom-suggestion">
  <span>&#127881; You completed 4 pomodoros! Time for a long break.</span>
  <button id="pom-take-long-break">Take Long Break</button>
</div>

<!-- Settings -->
<button class="pom-settings-toggle" id="pom-settings-toggle">&#9881; Customize Durations</button>
<div class="pom-settings" id="pom-settings-panel">
  <div class="pom-settings-title">Timer Settings</div>
  <div class="pom-settings-grid">
    <div class="pom-setting-item">
      <label for="set-work">Work (min)</label>
      <input type="number" id="set-work" value="25" min="1" max="90"/>
    </div>
    <div class="pom-setting-item">
      <label for="set-short">Short Break (min)</label>
      <input type="number" id="set-short" value="5" min="1" max="30"/>
    </div>
    <div class="pom-setting-item">
      <label for="set-long">Long Break (min)</label>
      <input type="number" id="set-long" value="15" min="1" max="60"/>
    </div>
  </div>
  <button class="pom-settings-apply" id="pom-apply-settings">Apply Settings</button>
</div>

<!-- Session History -->
<div class="pom-history">
  <div class="pom-history-title">Session History</div>
  <ul class="pom-history-list" id="pom-history-list"></ul>
</div>

</div><!-- /#pomodoro-app -->

<script>
(function() {
  // --- State ---
  var CIRCUMFERENCE = 2 * Math.PI * 96; // ~603.2
  var durations = { work: 25, short: 5, long: 15 };
  var mode = 'work';
  var totalSeconds = durations.work * 60;
  var secondsLeft = totalSeconds;
  var running = false;
  var intervalId = null;
  var completedPomodoros = 0;
  var sessionInCycle = 0; // resets every 4 work sessions

  // --- DOM refs ---
  var display      = document.getElementById('pom-display');
  var modeLabel    = document.getElementById('pom-mode-label');
  var ring         = document.getElementById('pom-ring');
  var startBtn     = document.getElementById('pom-start-btn');
  var resetBtn     = document.getElementById('pom-reset-btn');
  var skipBtn      = document.getElementById('pom-skip-btn');
  var counterText  = document.getElementById('pom-counter-text');
  var tomatoes     = [0,1,2,3].map(function(i){ return document.getElementById('t'+i); });
  var suggestion   = document.getElementById('pom-suggestion');
  var takeLBBtn    = document.getElementById('pom-take-long-break');
  var settingsToggle = document.getElementById('pom-settings-toggle');
  var settingsPanel  = document.getElementById('pom-settings-panel');
  var applyBtn       = document.getElementById('pom-apply-settings');
  var historyList    = document.getElementById('pom-history-list');
  var tabs           = document.querySelectorAll('#pomodoro-app .pom-tab');

  var MODE_LABELS = { work: 'Focus Time', short: 'Short Break', long: 'Long Break' };

  // --- Audio (Web Audio API bell) ---
  function playBell() {
    try {
      var ctx = new (window.AudioContext || window.webkitAudioContext)();
      function tone(freq, startTime, duration, vol) {
        var osc = ctx.createOscillator();
        var gain = ctx.createGain();
        osc.connect(gain);
        gain.connect(ctx.destination);
        osc.type = 'sine';
        osc.frequency.setValueAtTime(freq, startTime);
        gain.gain.setValueAtTime(vol, startTime);
        gain.gain.exponentialRampToValueAtTime(0.001, startTime + duration);
        osc.start(startTime);
        osc.stop(startTime + duration);
      }
      var t = ctx.currentTime;
      tone(880, t,        0.8, 0.5);
      tone(1100, t + 0.3, 0.7, 0.4);
      tone(880, t + 0.6,  0.9, 0.45);
    } catch(e) {}
  }

  // --- Helpers ---
  function pad(n) { return n < 10 ? '0' + n : '' + n; }

  function formatTime(secs) {
    var m = Math.floor(secs / 60);
    var s = secs % 60;
    return pad(m) + ':' + pad(s);
  }

  function setRing(secondsLeft, total) {
    var ratio = total > 0 ? secondsLeft / total : 0;
    var offset = CIRCUMFERENCE * (1 - ratio);
    ring.style.strokeDashoffset = offset;
  }

  function updateDisplay() {
    display.textContent = formatTime(secondsLeft);
    setRing(secondsLeft, totalSeconds);
    // color
    var isBreak = (mode === 'short' || mode === 'long');
    display.className = 'pom-time-label' + (isBreak ? ' break-mode' : '');
    ring.className.baseVal = 'pom-ring-prog' + (isBreak ? ' pom-ring-break' : '');
  }

  function updateTomatoes() {
    tomatoes.forEach(function(el, i) {
      el.classList.toggle('done', i < (sessionInCycle % 4 === 0 && sessionInCycle > 0 ? 4 : sessionInCycle % 4));
    });
    counterText.textContent = completedPomodoros + ' pomodoro' + (completedPomodoros !== 1 ? 's' : '') + ' completed';
  }

  function setMode(m) {
    mode = m;
    totalSeconds = durations[mode] * 60;
    secondsLeft = totalSeconds;
    running = false;
    clearInterval(intervalId);
    intervalId = null;
    startBtn.textContent = 'Start';
    startBtn.className = 'pom-btn pom-btn-start';
    modeLabel.textContent = MODE_LABELS[mode];
    tabs.forEach(function(tab) {
      tab.classList.toggle('active', tab.dataset.mode === mode);
    });
    suggestion.classList.remove('show');
    updateDisplay();
  }

  function addHistory(label, type) {
    var now = new Date();
    var timeStr = pad(now.getHours()) + ':' + pad(now.getMinutes());
    var li = document.createElement('li');
    li.className = 'pom-history-item';
    li.innerHTML =
      '<span class="pom-history-dot ' + type + '"></span>' +
      '<span class="pom-history-text">' + label + '</span>' +
      '<span class="pom-history-time">' + timeStr + '</span>';
    historyList.insertBefore(li, historyList.firstChild);
  }

  function onTimerEnd() {
    running = false;
    clearInterval(intervalId);
    intervalId = null;
    startBtn.textContent = 'Start';
    startBtn.className = 'pom-btn pom-btn-start';
    playBell();

    if (mode === 'work') {
      completedPomodoros++;
      sessionInCycle++;
      addHistory('Work Session #' + completedPomodoros + ' (' + durations.work + ' min)', 'work');
      updateTomatoes();
      if (sessionInCycle % 4 === 0) {
        suggestion.classList.add('show');
      }
    } else if (mode === 'short') {
      addHistory('Short Break (' + durations.short + ' min)', 'short');
    } else {
      addHistory('Long Break (' + durations.long + ' min)', 'long');
    }
  }

  function tick() {
    if (secondsLeft <= 0) {
      secondsLeft = 0;
      updateDisplay();
      onTimerEnd();
      return;
    }
    secondsLeft--;
    updateDisplay();
  }

  // --- Event Listeners ---
  startBtn.addEventListener('click', function() {
    if (running) {
      // Pause
      running = false;
      clearInterval(intervalId);
      intervalId = null;
      startBtn.textContent = 'Resume';
      startBtn.className = 'pom-btn pom-btn-start';
    } else {
      // Start / Resume
      running = true;
      startBtn.textContent = 'Pause';
      startBtn.className = 'pom-btn pom-btn-start pause';
      intervalId = setInterval(tick, 1000);
    }
  });

  resetBtn.addEventListener('click', function() {
    clearInterval(intervalId);
    intervalId = null;
    running = false;
    secondsLeft = totalSeconds;
    startBtn.textContent = 'Start';
    startBtn.className = 'pom-btn pom-btn-start';
    updateDisplay();
  });

  skipBtn.addEventListener('click', function() {
    clearInterval(intervalId);
    intervalId = null;
    running = false;
    // Move to next logical mode
    if (mode === 'work') {
      if (sessionInCycle > 0 && sessionInCycle % 4 === 0) {
        setMode('long');
      } else {
        setMode('short');
      }
    } else {
      setMode('work');
    }
  });

  tabs.forEach(function(tab) {
    tab.addEventListener('click', function() {
      setMode(tab.dataset.mode);
    });
  });

  takeLBBtn.addEventListener('click', function() {
    suggestion.classList.remove('show');
    setMode('long');
  });

  settingsToggle.addEventListener('click', function() {
    settingsPanel.classList.toggle('open');
  });

  applyBtn.addEventListener('click', function() {
    var w = parseInt(document.getElementById('set-work').value, 10);
    var s = parseInt(document.getElementById('set-short').value, 10);
    var l = parseInt(document.getElementById('set-long').value, 10);
    if (w > 0) durations.work = w;
    if (s > 0) durations.short = s;
    if (l > 0) durations.long = l;
    settingsPanel.classList.remove('open');
    setMode(mode); // reset current mode with new duration
  });

  // --- Init ---
  ring.style.strokeDasharray = CIRCUMFERENCE;
  ring.style.strokeDashoffset = 0;
  updateDisplay();
  updateTomatoes();

})();
</script>

---

## How to Use the Pomodoro Technique

The Pomodoro Technique is a time management method developed by Francesco Cirillo in the late 1980s. Named after the tomato-shaped kitchen timer he used as a university student ("pomodoro" is Italian for tomato), the method breaks your workday into short, focused intervals — traditionally 25 minutes — separated by brief breaks. Each interval is called a pomodoro, and the structure helps you work with time rather than against it.

The technique follows five simple steps. First, choose a task you want to work on. Second, set the timer for 25 minutes and commit fully to that task. Third, work until the timer rings — avoid switching tasks or checking notifications. Fourth, take a 5-minute short break to rest your mind. Fifth, after every four pomodoros, take a longer break of 15 to 30 minutes to recharge. This cycle repeats throughout your workday, creating a reliable rhythm of effort and recovery.

The benefits for productivity are well-documented. By limiting your focus to one task per session, the technique reduces the mental overhead of constant decision-making. The built-in breaks prevent mental fatigue and keep your concentration sharp over long periods. Many people also find that the time pressure of a countdown timer helps them overcome procrastination — starting feels easier when you are only committing to 25 minutes.

If you are new to the technique, start simple. Do not try to optimize every session immediately. Use the timer above, pick one meaningful task, and see how many pomodoros it actually takes. Over time you will build an accurate sense of how long your work really takes, which makes planning and estimation much easier. Some people prefer 50-minute work sessions with 10-minute breaks — use the settings panel above to customize the durations to fit your personal working style.

## Why the Pomodoro Technique Works

The core mechanism behind the Pomodoro Technique is the management of attention rather than time. Research in cognitive psychology consistently shows that the human brain is not built for sustained, uninterrupted focus for hours at a stretch. Attentional resources deplete with use, a phenomenon sometimes called ego depletion or directed-attention fatigue. The regular breaks built into the Pomodoro cycle allow these attentional resources to partially recover, meaning you return to work sharper rather than grinding through diminishing returns.

The technique also leverages the psychological effect of a commitment device. When you set the timer and declare that you will work on a specific task, you create a small but real social contract with yourself. This reduces the likelihood of task-switching and the productivity costs that come with it. Studies on context switching suggest that returning to a task after an interruption can take more than 20 minutes to reach the same depth of focus — the Pomodoro structure minimizes those interruptions by design.

Finally, the visible progress created by counting completed sessions provides consistent positive reinforcement. Each tomato icon filled in the counter above is a small reward signal. Tracking completed pomodoros across a day or week also creates useful data about your actual working capacity, helping you plan realistic workloads and notice patterns in your most productive hours.

## Related Tools

> Track your subscriptions and save money → [Subscription Cost Calculator](/tools/subscription-cost-calculator/)

> Calculate your freelance hourly rate → [Freelance Rate Calculator](/tools/freelance-rate-calculator/)

> Convert between hourly and annual salary → [Hourly to Salary Calculator](/tools/hourly-to-salary-calculator/)

> Working across time zones? → [Timezone Converter](/tools/timezone-converter/) — convert times between any cities instantly
