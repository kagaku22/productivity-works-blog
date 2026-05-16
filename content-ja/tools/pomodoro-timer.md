---
title: "ポモドーロタイマー"
date: 2025-05-16
description: "無料のポモドーロタイマー。作業・休憩のインターバルをカスタマイズして集中力をアップ。セッション管理・音声通知付き、会員登録不要。"
categories: ["無料ツール"]
slug: "pomodoro-timer"
ShowToc: false
cover:
  image: "/images/covers/pomodoro-timer-ja.png"
  alt: "ポモドーロタイマー"
---

25分の集中と5分の休憩を繰り返す「ポモドーロ・テクニック」を、ブラウザだけで手軽に実践できるタイマーです。作業時間・休憩時間のカスタマイズ、音声通知、セッション記録に対応し、会員登録なしで今すぐ使えます。

<div id="pm-app">

<style>
#pm-app {
  font-family: system-ui, -apple-system, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  color: #1e293b;
}

#pm-app * {
  box-sizing: border-box;
}

/* Preset buttons */
#pm-app .pm-presets {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 24px;
}

#pm-app .pm-preset-btn {
  padding: 6px 14px;
  border: 1.5px solid #94a3b8;
  border-radius: 20px;
  background: #fff;
  color: #475569;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all .18s;
}

#pm-app .pm-preset-btn:hover,
#pm-app .pm-preset-btn.active {
  background: #1e293b;
  border-color: #1e293b;
  color: #fff;
}

/* Phase tabs */
#pm-app .pm-phase-tabs {
  display: flex;
  gap: 6px;
  justify-content: center;
  margin-bottom: 20px;
}

#pm-app .pm-phase-tab {
  padding: 5px 16px;
  border-radius: 20px;
  border: none;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  background: #e2e8f0;
  color: #64748b;
  transition: all .18s;
}

#pm-app .pm-phase-tab.active {
  background: #0f172a;
  color: #fff;
}

/* Circular timer */
#pm-app .pm-timer-wrap {
  position: relative;
  width: 240px;
  height: 240px;
  margin: 0 auto 24px;
}

#pm-app .pm-ring-svg {
  width: 240px;
  height: 240px;
  transform: rotate(-90deg);
}

#pm-app .pm-ring-bg {
  fill: none;
  stroke: #e2e8f0;
  stroke-width: 10;
}

#pm-app .pm-ring-progress {
  fill: none;
  stroke: #0ea5e9;
  stroke-width: 10;
  stroke-linecap: round;
  transition: stroke-dashoffset .8s linear, stroke .4s;
}

#pm-app .pm-timer-center {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

#pm-app .pm-time-display {
  font-size: 54px;
  font-weight: 700;
  letter-spacing: -2px;
  color: #0f172a;
  line-height: 1;
}

#pm-app .pm-phase-label {
  font-size: 14px;
  font-weight: 600;
  color: #64748b;
  margin-top: 6px;
}

/* Controls */
#pm-app .pm-controls {
  display: flex;
  gap: 12px;
  justify-content: center;
  margin-bottom: 24px;
  flex-wrap: wrap;
}

#pm-app .pm-btn {
  padding: 10px 22px;
  border-radius: 8px;
  border: none;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: all .18s;
}

#pm-app .pm-btn-primary {
  background: #0ea5e9;
  color: #fff;
  min-width: 110px;
}

#pm-app .pm-btn-primary:hover {
  background: #0284c7;
}

#pm-app .pm-btn-secondary {
  background: #e2e8f0;
  color: #475569;
}

#pm-app .pm-btn-secondary:hover {
  background: #cbd5e1;
}

#pm-app .pm-btn-skip {
  background: #f1f5f9;
  color: #64748b;
  font-size: 13px;
  padding: 10px 16px;
}

#pm-app .pm-btn-skip:hover {
  background: #e2e8f0;
}

/* Session dots */
#pm-app .pm-sessions {
  text-align: center;
  margin-bottom: 20px;
}

#pm-app .pm-session-dots {
  font-size: 22px;
  letter-spacing: 4px;
  margin-bottom: 4px;
}

#pm-app .pm-session-info {
  font-size: 13px;
  color: #64748b;
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

#pm-app .pm-session-info span {
  font-weight: 600;
  color: #334155;
}

/* Settings */
#pm-app .pm-settings-toggle {
  display: flex;
  align-items: center;
  gap: 8px;
  background: none;
  border: none;
  font-size: 14px;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  margin: 0 auto 12px;
  padding: 6px 12px;
  border-radius: 6px;
  transition: background .18s;
}

#pm-app .pm-settings-toggle:hover {
  background: #f1f5f9;
}

#pm-app .pm-settings-toggle .pm-chevron {
  transition: transform .25s;
}

#pm-app .pm-settings-toggle.open .pm-chevron {
  transform: rotate(180deg);
}

#pm-app .pm-settings-panel {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 20px;
  display: none;
}

#pm-app .pm-settings-panel.open {
  display: block;
}

#pm-app .pm-settings-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
}

@media (max-width: 420px) {
  #pm-app .pm-settings-grid {
    grid-template-columns: 1fr;
  }
  #pm-app .pm-timer-wrap,
  #pm-app .pm-ring-svg {
    width: 200px;
    height: 200px;
  }
  #pm-app .pm-time-display {
    font-size: 44px;
  }
}

#pm-app .pm-field {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

#pm-app .pm-field label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: .5px;
}

#pm-app .pm-field input[type="number"] {
  padding: 8px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  font-weight: 600;
  color: #1e293b;
  background: #fff;
  width: 100%;
  outline: none;
  transition: border-color .18s;
}

#pm-app .pm-field input[type="number"]:focus {
  border-color: #0ea5e9;
}

#pm-app .pm-field-full {
  grid-column: 1 / -1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

#pm-app .pm-toggle-label {
  font-size: 13px;
  font-weight: 600;
  color: #334155;
}

#pm-app .pm-toggle {
  position: relative;
  width: 40px;
  height: 22px;
  flex-shrink: 0;
}

#pm-app .pm-toggle input {
  opacity: 0;
  width: 0;
  height: 0;
}

#pm-app .pm-toggle-slider {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  background: #cbd5e1;
  border-radius: 11px;
  cursor: pointer;
  transition: background .2s;
}

#pm-app .pm-toggle-slider::before {
  content: '';
  position: absolute;
  width: 16px;
  height: 16px;
  left: 3px;
  top: 3px;
  background: #fff;
  border-radius: 50%;
  transition: transform .2s;
}

#pm-app .pm-toggle input:checked + .pm-toggle-slider {
  background: #0ea5e9;
}

#pm-app .pm-toggle input:checked + .pm-toggle-slider::before {
  transform: translateX(18px);
}

#pm-app .pm-apply-btn {
  margin-top: 14px;
  width: 100%;
  padding: 9px;
  background: #0f172a;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background .18s;
}

#pm-app .pm-apply-btn:hover {
  background: #1e293b;
}
</style>

<!-- Preset buttons -->
<div class="pm-presets">
  <button class="pm-preset-btn active" data-work="25" data-short="5" data-long="15" data-sessions="4">クラシック（25/5）</button>
  <button class="pm-preset-btn" data-work="50" data-short="10" data-long="30" data-sessions="4">ディープワーク（50/10）</button>
  <button class="pm-preset-btn" data-work="15" data-short="3" data-long="15" data-sessions="4">スプリント（15/3）</button>
</div>

<!-- Phase indicator tabs -->
<div class="pm-phase-tabs">
  <button class="pm-phase-tab active" id="pm-tab-work">作業</button>
  <button class="pm-phase-tab" id="pm-tab-short">小休憩</button>
  <button class="pm-phase-tab" id="pm-tab-long">大休憩</button>
</div>

<!-- Circular timer -->
<div class="pm-timer-wrap">
  <svg class="pm-ring-svg" viewBox="0 0 240 240">
    <circle class="pm-ring-bg" cx="120" cy="120" r="108"/>
    <circle class="pm-ring-progress" id="pm-ring" cx="120" cy="120" r="108"/>
  </svg>
  <div class="pm-timer-center">
    <div class="pm-time-display" id="pm-display">25:00</div>
    <div class="pm-phase-label" id="pm-phase-text">作業中</div>
  </div>
</div>

<!-- Controls -->
<div class="pm-controls">
  <button class="pm-btn pm-btn-primary" id="pm-start-btn">スタート</button>
  <button class="pm-btn pm-btn-secondary" id="pm-reset-btn">リセット</button>
  <button class="pm-btn pm-btn-skip" id="pm-skip-btn">次へ &#8594;</button>
</div>

<!-- Session tracker -->
<div class="pm-sessions">
  <div class="pm-session-dots" id="pm-dots">○○○○</div>
  <div class="pm-session-info">
    <div>セッション: <span id="pm-session-num">1 / 4</span></div>
    <div>本日の集中時間: <span id="pm-focus-total">0分</span></div>
  </div>
</div>

<!-- Settings toggle -->
<button class="pm-settings-toggle" id="pm-settings-btn">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <circle cx="12" cy="12" r="3"/>
    <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 2.83-2.83l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/>
  </svg>
  設定
  <svg class="pm-chevron" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
    <polyline points="6 9 12 15 18 9"/>
  </svg>
</button>

<!-- Settings panel -->
<div class="pm-settings-panel" id="pm-settings-panel">
  <div class="pm-settings-grid">
    <div class="pm-field">
      <label>作業時間（分）</label>
      <input type="number" id="pm-set-work" min="1" max="120" value="25">
    </div>
    <div class="pm-field">
      <label>小休憩（分）</label>
      <input type="number" id="pm-set-short" min="1" max="60" value="5">
    </div>
    <div class="pm-field">
      <label>大休憩（分）</label>
      <input type="number" id="pm-set-long" min="1" max="60" value="15">
    </div>
    <div class="pm-field">
      <label>大休憩までのセッション数</label>
      <input type="number" id="pm-set-sessions" min="1" max="10" value="4">
    </div>
    <div class="pm-field-full">
      <span class="pm-toggle-label">フェーズ終了後に自動スタート</span>
      <label class="pm-toggle">
        <input type="checkbox" id="pm-set-auto">
        <span class="pm-toggle-slider"></span>
      </label>
    </div>
  </div>
  <button class="pm-apply-btn" id="pm-apply-btn">設定を適用</button>
</div>

<script>
(function() {
  // --- Config & State ---
  var cfg = { work: 25, short: 5, long: 15, sessions: 4, auto: false };

  var phaseNames   = { work: '作業中', short: '小休憩', long: '大休憩' };
  var phaseColors  = { work: '#0ea5e9', short: '#10b981', long: '#8b5cf6' };

  var state = {
    phase: 'work',
    sessionsDone: 0,
    secondsLeft: cfg.work * 60,
    totalSeconds: cfg.work * 60,
    running: false,
    timer: null,
    focusMinutesToday: 0
  };

  // SVG ring geometry
  var R    = 108;
  var CIRC = 2 * Math.PI * R;

  // --- DOM refs ---
  var display       = document.getElementById('pm-display');
  var phaseText     = document.getElementById('pm-phase-text');
  var ring          = document.getElementById('pm-ring');
  var startBtn      = document.getElementById('pm-start-btn');
  var resetBtn      = document.getElementById('pm-reset-btn');
  var skipBtn       = document.getElementById('pm-skip-btn');
  var dotsEl        = document.getElementById('pm-dots');
  var sessionNumEl  = document.getElementById('pm-session-num');
  var focusTotalEl  = document.getElementById('pm-focus-total');
  var settingsBtn   = document.getElementById('pm-settings-btn');
  var settingsPanel = document.getElementById('pm-settings-panel');
  var applyBtn      = document.getElementById('pm-apply-btn');
  var tabWork       = document.getElementById('pm-tab-work');
  var tabShort      = document.getElementById('pm-tab-short');
  var tabLong       = document.getElementById('pm-tab-long');

  // Init ring
  ring.style.strokeDasharray  = CIRC;
  ring.style.strokeDashoffset = 0;

  // --- Audio (Web Audio API) ---
  function beep(type) {
    try {
      var ctx  = new (window.AudioContext || window.webkitAudioContext)();
      var osc  = ctx.createOscillator();
      var gain = ctx.createGain();
      osc.connect(gain);
      gain.connect(ctx.destination);
      if (type === 'work') {
        // Two-tone descending: session starting
        osc.frequency.setValueAtTime(880, ctx.currentTime);
        osc.frequency.setValueAtTime(660, ctx.currentTime + 0.15);
        gain.gain.setValueAtTime(0.3, ctx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.5);
        osc.start(ctx.currentTime);
        osc.stop(ctx.currentTime + 0.5);
      } else {
        // Three-tone ascending: break starting
        osc.frequency.setValueAtTime(440, ctx.currentTime);
        osc.frequency.setValueAtTime(550, ctx.currentTime + 0.2);
        osc.frequency.setValueAtTime(660, ctx.currentTime + 0.4);
        gain.gain.setValueAtTime(0.25, ctx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.7);
        osc.start(ctx.currentTime);
        osc.stop(ctx.currentTime + 0.7);
      }
    } catch(e) {}
  }

  // --- Helpers ---
  function pad(n) { return n < 10 ? '0' + n : '' + n; }

  // --- Render ---
  function render() {
    var m = Math.floor(state.secondsLeft / 60);
    var s = state.secondsLeft % 60;
    var timeStr = pad(m) + ':' + pad(s);

    display.textContent   = timeStr;
    phaseText.textContent = phaseNames[state.phase];
    document.title        = timeStr + ' | ポモドーロタイマー';

    // Ring progress
    var progress = state.totalSeconds > 0 ? state.secondsLeft / state.totalSeconds : 0;
    ring.style.strokeDashoffset = CIRC * (1 - progress);
    ring.style.stroke           = phaseColors[state.phase];

    // Start/pause button label
    startBtn.textContent = state.running ? '一時停止' : 'スタート';

    // Phase tabs
    tabWork.classList.toggle('active',  state.phase === 'work');
    tabShort.classList.toggle('active', state.phase === 'short');
    tabLong.classList.toggle('active',  state.phase === 'long');

    // Session dots (●○)
    var total = cfg.sessions;
    var done  = state.sessionsDone;
    var dots  = '';
    for (var i = 0; i < total; i++) {
      dots += i < done ? '●' : '○';
    }
    dotsEl.textContent = dots;

    // Session number label
    var cur = state.phase === 'work'
      ? (state.sessionsDone + 1)
      : state.sessionsDone;
    sessionNumEl.textContent = Math.min(cur, cfg.sessions) + ' / ' + cfg.sessions;

    // Today's focus time
    focusTotalEl.textContent = state.focusMinutesToday + '分';
  }

  // --- Phase transition ---
  function goNextPhase(skipForward) {
    clearInterval(state.timer);
    state.running = false;

    var prev = state.phase;

    // Count the completed work session (only when not manually skipping from idle)
    if (prev === 'work' && !skipForward) {
      state.sessionsDone = Math.min(state.sessionsDone + 1, cfg.sessions);
      state.focusMinutesToday += cfg.work;
    }

    // Determine next phase
    if (prev === 'work') {
      if (state.sessionsDone >= cfg.sessions) {
        state.phase        = 'long';
        state.sessionsDone = 0;
      } else {
        state.phase = 'short';
      }
    } else {
      state.phase = 'work';
    }

    // Set new duration
    var dur = cfg[state.phase === 'work' ? 'work' : state.phase === 'short' ? 'short' : 'long'];
    state.secondsLeft  = dur * 60;
    state.totalSeconds = dur * 60;

    // Sound
    if (!skipForward) {
      beep(state.phase === 'work' ? 'work' : 'break');
    }

    if (cfg.auto) {
      startTimer();
    } else {
      render();
    }
  }

  // --- Timer controls ---
  function startTimer() {
    if (state.running) return;
    state.running = true;
    render();
    state.timer = setInterval(function() {
      state.secondsLeft--;
      if (state.secondsLeft <= 0) {
        state.secondsLeft = 0;
        render();
        goNextPhase(false);
        return;
      }
      render();
    }, 1000);
  }

  function pauseTimer() {
    clearInterval(state.timer);
    state.running = false;
    render();
  }

  function resetTimer() {
    clearInterval(state.timer);
    state.running      = false;
    state.phase        = 'work';
    state.sessionsDone = 0;
    state.secondsLeft  = cfg.work * 60;
    state.totalSeconds = cfg.work * 60;
    render();
  }

  // --- Button listeners ---
  startBtn.addEventListener('click', function() {
    if (state.running) { pauseTimer(); } else { startTimer(); }
  });

  resetBtn.addEventListener('click', resetTimer);

  skipBtn.addEventListener('click', function() { goNextPhase(true); });

  // Phase tabs (manual switch when paused)
  tabWork.addEventListener('click', function() {
    if (state.running) return;
    state.phase        = 'work';
    state.secondsLeft  = cfg.work * 60;
    state.totalSeconds = cfg.work * 60;
    render();
  });

  tabShort.addEventListener('click', function() {
    if (state.running) return;
    state.phase        = 'short';
    state.secondsLeft  = cfg.short * 60;
    state.totalSeconds = cfg.short * 60;
    render();
  });

  tabLong.addEventListener('click', function() {
    if (state.running) return;
    state.phase        = 'long';
    state.secondsLeft  = cfg.long * 60;
    state.totalSeconds = cfg.long * 60;
    render();
  });

  // --- Settings panel ---
  settingsBtn.addEventListener('click', function() {
    settingsBtn.classList.toggle('open');
    settingsPanel.classList.toggle('open');
  });

  applyBtn.addEventListener('click', function() {
    var w  = parseInt(document.getElementById('pm-set-work').value,     10);
    var sh = parseInt(document.getElementById('pm-set-short').value,    10);
    var lo = parseInt(document.getElementById('pm-set-long').value,     10);
    var se = parseInt(document.getElementById('pm-set-sessions').value, 10);
    var au = document.getElementById('pm-set-auto').checked;

    cfg.work     = w  > 0 ? w  : 25;
    cfg.short    = sh > 0 ? sh : 5;
    cfg.long     = lo > 0 ? lo : 15;
    cfg.sessions = se > 0 ? se : 4;
    cfg.auto     = au;

    resetTimer();
    settingsBtn.classList.remove('open');
    settingsPanel.classList.remove('open');
  });

  // --- Presets ---
  var presetBtns = document.querySelectorAll('#pm-app .pm-preset-btn');
  for (var pi = 0; pi < presetBtns.length; pi++) {
    (function(btn) {
      btn.addEventListener('click', function() {
        for (var i = 0; i < presetBtns.length; i++) {
          presetBtns[i].classList.remove('active');
        }
        btn.classList.add('active');

        cfg.work     = parseInt(btn.getAttribute('data-work'),     10);
        cfg.short    = parseInt(btn.getAttribute('data-short'),    10);
        cfg.long     = parseInt(btn.getAttribute('data-long'),     10);
        cfg.sessions = parseInt(btn.getAttribute('data-sessions'), 10);

        document.getElementById('pm-set-work').value     = cfg.work;
        document.getElementById('pm-set-short').value    = cfg.short;
        document.getElementById('pm-set-long').value     = cfg.long;
        document.getElementById('pm-set-sessions').value = cfg.sessions;

        resetTimer();
      });
    })(presetBtns[pi]);
  }

  // --- Init ---
  render();
})();
</script>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

</div>

---

> タイピング速度を測定 → [タイピング速度テスト](/ja/tools/typing-speed-test/)
> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-calculator/)
> 時差を計算 → [タイムゾーン変換ツール](/ja/tools/timezone-converter/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
