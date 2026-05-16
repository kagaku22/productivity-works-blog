---
title: "ポモドーロタイマー - 無料オンライン集中タイマー"
date: 2025-05-16
description: "無料のポモドーロタイマー。作業・休憩時間をカスタマイズして集中力アップ。セッション記録・目標設定機能付き。"
categories: ["無料ツール"]
tags: ["ポモドーロ", "タイマー", "集中力", "生産性", "時間管理"]
slug: "pomodoro-timer"
aliases: ["/ja/tools/focus-timer/", "/ja/tools/productivity-timer/"]
cover:
  image: "/images/covers/pomodoro-timer-ja.png"
  alt: "ポモドーロタイマー"
ShowToc: false
---

<div id="pomodoro-app">

<style>
#pomodoro-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic", "Meiryo", sans-serif;
  max-width: 700px;
  margin: 0 auto;
  padding: 16px;
  color: #2c3e50;
}

/* Mode tabs */
#pomodoro-app .mode-tabs {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin-bottom: 28px;
  flex-wrap: wrap;
}

#pomodoro-app .mode-btn {
  padding: 8px 20px;
  border: 2px solid #e74c3c;
  background: transparent;
  color: #e74c3c;
  border-radius: 24px;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.2s;
  font-weight: 600;
}

#pomodoro-app .mode-btn.active,
#pomodoro-app .mode-btn:hover {
  background: #e74c3c;
  color: #fff;
}

/* Circular timer */
#pomodoro-app .timer-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 28px;
}

#pomodoro-app .ring-svg {
  width: 220px;
  height: 220px;
  transform: rotate(-90deg);
}

#pomodoro-app .ring-bg {
  fill: none;
  stroke: #f0e0de;
  stroke-width: 12;
}

#pomodoro-app .ring-progress {
  fill: none;
  stroke: #e74c3c;
  stroke-width: 12;
  stroke-linecap: round;
  transition: stroke-dashoffset 0.8s linear, stroke 0.5s;
}

#pomodoro-app .timer-inner {
  position: relative;
  width: 220px;
  height: 220px;
}

#pomodoro-app .timer-text-wrap {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

#pomodoro-app .timer-display {
  font-size: 54px;
  font-weight: 700;
  color: #e74c3c;
  line-height: 1;
  letter-spacing: -2px;
}

#pomodoro-app .timer-mode-label {
  font-size: 13px;
  color: #888;
  margin-top: 4px;
  font-weight: 500;
}

/* Session counter */
#pomodoro-app .session-counter {
  display: flex;
  justify-content: center;
  gap: 6px;
  margin-bottom: 24px;
}

#pomodoro-app .pom-dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  border: 2px solid #e74c3c;
  background: transparent;
  transition: background 0.3s;
}

#pomodoro-app .pom-dot.done {
  background: #e74c3c;
}

/* Control buttons */
#pomodoro-app .controls {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-bottom: 28px;
  flex-wrap: wrap;
}

#pomodoro-app .ctrl-btn {
  padding: 12px 28px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.1s;
}

#pomodoro-app .ctrl-btn:active {
  transform: scale(0.97);
}

#pomodoro-app .btn-start {
  background: #e74c3c;
  color: #fff;
  min-width: 120px;
}

#pomodoro-app .btn-reset {
  background: #ecf0f1;
  color: #555;
}

#pomodoro-app .btn-skip {
  background: #ecf0f1;
  color: #555;
}

#pomodoro-app .ctrl-btn:hover {
  opacity: 0.85;
}

/* Customize settings */
#pomodoro-app .settings-toggle {
  text-align: center;
  margin-bottom: 12px;
}

#pomodoro-app .settings-toggle button {
  background: none;
  border: none;
  color: #e74c3c;
  font-size: 14px;
  cursor: pointer;
  text-decoration: underline;
  font-weight: 500;
}

#pomodoro-app .settings-panel {
  display: none;
  background: #fff8f7;
  border: 1px solid #f5c6c2;
  border-radius: 10px;
  padding: 16px 20px;
  margin-bottom: 20px;
}

#pomodoro-app .settings-panel.open {
  display: block;
}

#pomodoro-app .settings-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

#pomodoro-app .setting-item label {
  display: block;
  font-size: 12px;
  color: #888;
  margin-bottom: 4px;
  font-weight: 500;
}

#pomodoro-app .setting-item input[type="number"] {
  width: 100%;
  padding: 8px 10px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 15px;
  text-align: center;
  box-sizing: border-box;
}

#pomodoro-app .settings-apply-btn {
  display: block;
  width: 100%;
  margin-top: 12px;
  padding: 9px;
  background: #e74c3c;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
}

#pomodoro-app .settings-apply-btn:hover {
  opacity: 0.87;
}

/* Notification banner */
#pomodoro-app .notification-banner {
  display: none;
  background: #e74c3c;
  color: #fff;
  border-radius: 8px;
  padding: 12px 18px;
  text-align: center;
  font-weight: 600;
  margin-bottom: 20px;
  font-size: 15px;
  animation: fadeIn 0.4s;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-8px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Session log */
#pomodoro-app .log-section {
  margin-top: 8px;
}

#pomodoro-app .log-section h3 {
  font-size: 15px;
  color: #555;
  margin-bottom: 10px;
  font-weight: 600;
  border-left: 3px solid #e74c3c;
  padding-left: 8px;
}

#pomodoro-app .log-list {
  list-style: none;
  padding: 0;
  margin: 0;
  max-height: 180px;
  overflow-y: auto;
}

#pomodoro-app .log-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 7px 10px;
  border-radius: 6px;
  font-size: 13px;
  background: #fdf5f4;
  margin-bottom: 5px;
}

#pomodoro-app .log-list li .log-type {
  font-weight: 600;
  color: #e74c3c;
}

#pomodoro-app .log-list li .log-time {
  color: #999;
  font-size: 12px;
}

#pomodoro-app .log-empty {
  color: #bbb;
  font-size: 13px;
  text-align: center;
  padding: 10px 0;
}

#pomodoro-app .log-clear-btn {
  background: none;
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 4px 12px;
  font-size: 12px;
  color: #999;
  cursor: pointer;
  margin-left: 10px;
}

#pomodoro-app .log-clear-btn:hover {
  background: #f5f5f5;
}

#pomodoro-app .log-header {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

#pomodoro-app .log-header h3 {
  margin-bottom: 0;
  flex: 1;
}

/* Long break suggestion */
#pomodoro-app .long-break-banner {
  display: none;
  background: #27ae60;
  color: #fff;
  border-radius: 8px;
  padding: 12px 18px;
  text-align: center;
  font-weight: 600;
  margin-bottom: 20px;
  font-size: 15px;
}

#pomodoro-app .long-break-banner button {
  margin-left: 10px;
  padding: 4px 14px;
  border: 2px solid #fff;
  border-radius: 5px;
  background: transparent;
  color: #fff;
  cursor: pointer;
  font-size: 13px;
  font-weight: 700;
}

/* Responsive */
@media (max-width: 480px) {
  #pomodoro-app .ring-svg,
  #pomodoro-app .timer-inner {
    width: 180px;
    height: 180px;
  }
  #pomodoro-app .timer-display {
    font-size: 42px;
  }
  #pomodoro-app .settings-grid {
    grid-template-columns: 1fr;
  }
  #pomodoro-app .ctrl-btn {
    padding: 10px 18px;
    font-size: 14px;
  }
}
</style>

<!-- Mode selector -->
<div class="mode-tabs">
  <button class="mode-btn active" id="btn-work">作業 (25分)</button>
  <button class="mode-btn" id="btn-short">短い休憩 (5分)</button>
  <button class="mode-btn" id="btn-long">長い休憩 (15分)</button>
</div>

<!-- Long break suggestion banner -->
<div class="long-break-banner" id="long-break-banner">
  4ポモドーロ達成！長い休憩を取りましょう。
  <button id="take-long-break-btn">今すぐ休憩</button>
</div>

<!-- Notification banner -->
<div class="notification-banner" id="notification-banner"></div>

<!-- Circular timer -->
<div class="timer-container">
  <div class="timer-inner">
    <svg class="ring-svg" viewBox="0 0 220 220" xmlns="http://www.w3.org/2000/svg">
      <circle class="ring-bg" cx="110" cy="110" r="95"/>
      <circle class="ring-progress" id="ring-progress" cx="110" cy="110" r="95"/>
    </svg>
    <div class="timer-text-wrap">
      <div class="timer-display" id="timer-display">25:00</div>
      <div class="timer-mode-label" id="timer-mode-label">作業セッション</div>
    </div>
  </div>
</div>

<!-- Session counter (4 dots) -->
<div class="session-counter" id="session-counter">
  <div class="pom-dot" id="dot-0"></div>
  <div class="pom-dot" id="dot-1"></div>
  <div class="pom-dot" id="dot-2"></div>
  <div class="pom-dot" id="dot-3"></div>
</div>

<!-- Controls -->
<div class="controls">
  <button class="ctrl-btn btn-start" id="start-btn">スタート</button>
  <button class="ctrl-btn btn-reset" id="reset-btn">リセット</button>
  <button class="ctrl-btn btn-skip" id="skip-btn">スキップ</button>
</div>

<!-- Settings -->
<div class="settings-toggle">
  <button id="settings-toggle-btn">時間をカスタマイズ ▾</button>
</div>
<div class="settings-panel" id="settings-panel">
  <div class="settings-grid">
    <div class="setting-item">
      <label>作業時間（分）</label>
      <input type="number" id="inp-work" min="1" max="60" value="25">
    </div>
    <div class="setting-item">
      <label>短い休憩（分）</label>
      <input type="number" id="inp-short" min="1" max="30" value="5">
    </div>
    <div class="setting-item">
      <label>長い休憩（分）</label>
      <input type="number" id="inp-long" min="1" max="60" value="15">
    </div>
  </div>
  <button class="settings-apply-btn" id="settings-apply-btn">設定を適用</button>
</div>

<!-- Session log -->
<div class="log-section">
  <div class="log-header">
    <h3>セッション履歴</h3>
    <button class="log-clear-btn" id="log-clear-btn">クリア</button>
  </div>
  <ul class="log-list" id="log-list">
    <li class="log-empty" id="log-empty">まだセッションがありません</li>
  </ul>
</div>

<script>
(function() {
  // --- State ---
  var MODES = {
    work:  { label: '作業セッション', color: '#e74c3c', ringColor: '#e74c3c' },
    short: { label: '短い休憩',       color: '#e67e22', ringColor: '#e67e22' },
    long:  { label: '長い休憩',       color: '#27ae60', ringColor: '#27ae60' }
  };

  var durations = { work: 25, short: 5, long: 15 }; // minutes
  var currentMode = 'work';
  var totalSeconds = durations.work * 60;
  var remainingSeconds = totalSeconds;
  var isRunning = false;
  var timerId = null;
  var completedPomodoros = 0; // in current cycle of 4
  var totalPomodoros = 0;
  var sessionLog = [];

  // Ring circumference
  var RADIUS = 95;
  var CIRCUMFERENCE = 2 * Math.PI * RADIUS;

  // --- DOM ---
  var ringProgress   = document.getElementById('ring-progress');
  var timerDisplay   = document.getElementById('timer-display');
  var timerModeLabel = document.getElementById('timer-mode-label');
  var startBtn       = document.getElementById('start-btn');
  var resetBtn       = document.getElementById('reset-btn');
  var skipBtn        = document.getElementById('skip-btn');
  var notifBanner    = document.getElementById('notification-banner');
  var longBrkBanner  = document.getElementById('long-break-banner');
  var logList        = document.getElementById('log-list');
  var logEmpty       = document.getElementById('log-empty');
  var logClearBtn    = document.getElementById('log-clear-btn');
  var settingsToggle = document.getElementById('settings-toggle-btn');
  var settingsPanel  = document.getElementById('settings-panel');
  var settingsApply  = document.getElementById('settings-apply-btn');
  var inpWork        = document.getElementById('inp-work');
  var inpShort       = document.getElementById('inp-short');
  var inpLong        = document.getElementById('inp-long');
  var btnWork        = document.getElementById('btn-work');
  var btnShort       = document.getElementById('btn-short');
  var btnLong        = document.getElementById('btn-long');
  var takeLongBreak  = document.getElementById('take-long-break-btn');
  var dots           = [
    document.getElementById('dot-0'),
    document.getElementById('dot-1'),
    document.getElementById('dot-2'),
    document.getElementById('dot-3')
  ];

  // --- Ring setup ---
  ringProgress.setAttribute('stroke-dasharray', CIRCUMFERENCE);
  ringProgress.setAttribute('stroke-dashoffset', '0');

  function setRingProgress(fraction) {
    // fraction: 1.0 = full, 0.0 = empty
    var offset = CIRCUMFERENCE * (1 - fraction);
    ringProgress.setAttribute('stroke-dashoffset', offset);
  }

  function updateRingColor(mode) {
    ringProgress.style.stroke = MODES[mode].ringColor;
  }

  // --- Format ---
  function formatTime(secs) {
    var m = Math.floor(secs / 60);
    var s = secs % 60;
    return (m < 10 ? '0' : '') + m + ':' + (s < 10 ? '0' : '') + s;
  }

  // --- Display update ---
  function updateDisplay() {
    timerDisplay.textContent = formatTime(remainingSeconds);
    timerModeLabel.textContent = MODES[currentMode].label;
    var fraction = totalSeconds > 0 ? remainingSeconds / totalSeconds : 1;
    setRingProgress(fraction);
    updateRingColor(currentMode);
  }

  // --- Dots ---
  function updateDots() {
    for (var i = 0; i < 4; i++) {
      if (i < completedPomodoros) {
        dots[i].classList.add('done');
      } else {
        dots[i].classList.remove('done');
      }
    }
  }

  // --- Mode switch ---
  function switchMode(mode) {
    stopTimer();
    currentMode = mode;
    totalSeconds = durations[mode] * 60;
    remainingSeconds = totalSeconds;
    updateDisplay();
    updateDots();
    hideLongBreakBanner();
    hideNotif();
    updateModeButtons();
  }

  function updateModeButtons() {
    btnWork.classList.toggle('active', currentMode === 'work');
    btnShort.classList.toggle('active', currentMode === 'short');
    btnLong.classList.toggle('active', currentMode === 'long');
    // Update button labels with current durations
    btnWork.textContent  = '作業 (' + durations.work + '分)';
    btnShort.textContent = '短い休憩 (' + durations.short + '分)';
    btnLong.textContent  = '長い休憩 (' + durations.long + '分)';
  }

  // --- Timer control ---
  function startTimer() {
    if (isRunning) return;
    isRunning = true;
    startBtn.textContent = '一時停止';
    hideNotif();
    hideLongBreakBanner();
    timerId = setInterval(function() {
      if (remainingSeconds <= 0) {
        onTimerEnd();
        return;
      }
      remainingSeconds--;
      updateDisplay();
    }, 1000);
  }

  function pauseTimer() {
    if (!isRunning) return;
    isRunning = false;
    startBtn.textContent = 'スタート';
    clearInterval(timerId);
    timerId = null;
  }

  function stopTimer() {
    isRunning = false;
    startBtn.textContent = 'スタート';
    clearInterval(timerId);
    timerId = null;
  }

  function resetTimer() {
    stopTimer();
    totalSeconds = durations[currentMode] * 60;
    remainingSeconds = totalSeconds;
    updateDisplay();
    hideNotif();
    hideLongBreakBanner();
  }

  function skipSession() {
    if (isRunning || remainingSeconds < totalSeconds) {
      // Count as complete if work mode and partially done or running
      if (currentMode === 'work') {
        handleWorkComplete(true);
      } else {
        // Just switch to work
        switchMode('work');
      }
    } else {
      // Nothing has started, just skip to next
      if (currentMode === 'work') {
        switchMode('short');
      } else {
        switchMode('work');
      }
    }
  }

  function onTimerEnd() {
    stopTimer();
    remainingSeconds = 0;
    updateDisplay();
    playBell();
    if (currentMode === 'work') {
      handleWorkComplete(false);
    } else {
      // Break ended — prompt to start work
      showNotif('休憩終了！作業セッションを始めましょう。');
      addLog(currentMode === 'short' ? '短い休憩' : '長い休憩', '完了');
      setTimeout(function() {
        switchMode('work');
      }, 1500);
    }
  }

  function handleWorkComplete(skipped) {
    completedPomodoros++;
    totalPomodoros++;
    var label = skipped ? 'スキップ' : '完了';
    addLog('作業セッション #' + totalPomodoros, label);
    updateDots();

    if (completedPomodoros >= 4) {
      completedPomodoros = 0;
      updateDots();
      showLongBreakBanner();
      showNotif('4ポモドーロ達成！長い休憩を取りましょう！');
    } else {
      showNotif('セッション完了！短い休憩を取りましょう。');
      setTimeout(function() {
        switchMode('short');
      }, 1500);
    }
  }

  // --- Notifications ---
  function showNotif(msg) {
    notifBanner.textContent = msg;
    notifBanner.style.display = 'block';
    clearTimeout(notifBanner._hideTimer);
    notifBanner._hideTimer = setTimeout(hideNotif, 5000);
  }

  function hideNotif() {
    notifBanner.style.display = 'none';
  }

  function showLongBreakBanner() {
    longBrkBanner.style.display = 'block';
  }

  function hideLongBreakBanner() {
    longBrkBanner.style.display = 'none';
  }

  // --- Audio bell (Web Audio API) ---
  function playBell() {
    try {
      var ctx = new (window.AudioContext || window.webkitAudioContext)();
      function tone(freq, start, dur, vol) {
        var osc = ctx.createOscillator();
        var gain = ctx.createGain();
        osc.connect(gain);
        gain.connect(ctx.destination);
        osc.type = 'sine';
        osc.frequency.setValueAtTime(freq, ctx.currentTime + start);
        gain.gain.setValueAtTime(vol, ctx.currentTime + start);
        gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + start + dur);
        osc.start(ctx.currentTime + start);
        osc.stop(ctx.currentTime + start + dur);
      }
      tone(880, 0,    0.6, 0.5);
      tone(1046, 0.15, 0.6, 0.4);
      tone(1318, 0.30, 0.8, 0.35);
    } catch(e) {}
  }

  // --- Session log ---
  function addLog(type, status) {
    var now = new Date();
    var hh = now.getHours().toString().padStart(2, '0');
    var mm = now.getMinutes().toString().padStart(2, '0');
    var entry = { type: type, status: status, time: hh + ':' + mm };
    sessionLog.unshift(entry);
    renderLog();
  }

  function renderLog() {
    if (sessionLog.length === 0) {
      logList.innerHTML = '<li class="log-empty" id="log-empty">まだセッションがありません</li>';
      return;
    }
    logList.innerHTML = '';
    sessionLog.forEach(function(e) {
      var li = document.createElement('li');
      li.innerHTML =
        '<span class="log-type">' + e.type + '</span>' +
        '<span>' + e.status + '</span>' +
        '<span class="log-time">' + e.time + '</span>';
      logList.appendChild(li);
    });
  }

  // --- Event listeners ---
  startBtn.addEventListener('click', function() {
    if (isRunning) { pauseTimer(); } else { startTimer(); }
  });

  resetBtn.addEventListener('click', resetTimer);

  skipBtn.addEventListener('click', skipSession);

  btnWork.addEventListener('click', function() { switchMode('work'); });
  btnShort.addEventListener('click', function() { switchMode('short'); });
  btnLong.addEventListener('click', function() { switchMode('long'); });

  takeLongBreak.addEventListener('click', function() {
    hideLongBreakBanner();
    switchMode('long');
    setTimeout(startTimer, 300);
  });

  settingsToggle.addEventListener('click', function() {
    settingsPanel.classList.toggle('open');
    settingsToggle.textContent = settingsPanel.classList.contains('open')
      ? '時間をカスタマイズ ▴'
      : '時間をカスタマイズ ▾';
  });

  settingsApply.addEventListener('click', function() {
    var w = parseInt(inpWork.value, 10) || 25;
    var s = parseInt(inpShort.value, 10) || 5;
    var l = parseInt(inpLong.value, 10) || 15;
    w = Math.min(60, Math.max(1, w));
    s = Math.min(30, Math.max(1, s));
    l = Math.min(60, Math.max(1, l));
    durations.work  = w;
    durations.short = s;
    durations.long  = l;
    inpWork.value  = w;
    inpShort.value = s;
    inpLong.value  = l;
    switchMode(currentMode);
    settingsPanel.classList.remove('open');
    settingsToggle.textContent = '時間をカスタマイズ ▾';
    showNotif('設定を更新しました。');
  });

  logClearBtn.addEventListener('click', function() {
    sessionLog = [];
    renderLog();
  });

  // --- Init ---
  updateDisplay();
  updateDots();
  updateModeButtons();

})();
</script>

</div>

---

## ポモドーロテクニックとは

ポモドーロテクニックは、1980年代後半にイタリアの開発者フランチェスコ・シリロが考案した時間管理術です。「ポモドーロ（pomidoro）」はイタリア語でトマトを意味し、シリロが大学生のころにトマト型のキッチンタイマーを使って実践したことが名前の由来です。基本的なルールはシンプルで、25分間の集中作業（ポモドーロ）と5分間の短い休憩を繰り返し、4回の作業セッションを終えたら15〜30分の長い休憩を取ります。

ポモドーロテクニックの実践は5つのステップで構成されています。まず「やるべきタスクを書き出す」、次に「タイマーを25分にセットする」、そして「タイマーが鳴るまで一つのタスクに集中する」、続いて「5分休憩を取る」、最後に「4セット完了したら長い休憩に入る」というサイクルです。このシンプルな構造が、誰でも今日から実践できる手軽さを実現しています。

ポモドーロテクニックの最大の効果は、「集中→休憩」のリズムを体に覚えさせることで生産性と持続性が同時に高まる点です。作業中に別のことが気になっても「あとで」と記録するだけで安心でき、タスクの先延ばしを防ぐことができます。また、1セッション単位で進捗を実感できるため、モチベーションを維持しやすいという利点もあります。これまで多くのプログラマー、ライター、研究者、学生などが活用し、世界中で広まっています。

始め方のコツとして、最初の数日は「スマートフォンをサイレントモードにする」「ブラウザのタブを最小限にする」「メールやSNSの通知をオフにする」といった環境整備から始めると効果的です。25分が長く感じる場合は、最初は15〜20分から始めて徐々に延ばしていくのも良い方法です。慣れてくると、集中の質が大きく変わることを実感できるでしょう。

## ポモドーロテクニックが効果的な理由

科学的な観点から見ると、ポモドーロテクニックは人間の注意持続時間と深く関係しています。認知心理学の研究によれば、人間が高い集中力を維持できる時間は20〜30分程度とされており、それを超えると注意散漫や疲労が蓄積されやすくなります。ポモドーロの25分という単位は、この認知的な限界に合わせて設計されており、脳への過負荷を防ぎながら効率よく作業を進めることが可能です。また、作業と休憩の明確な区切りが「切り替えコスト（スイッチングコスト）」を下げ、再集中をスムーズにすることも確認されています。

さらに、ポモドーロテクニックはドーパミンの分泌サイクルとも相性が良いとされています。セッションを1つ完了するごとに小さな達成感を得ることで、脳は「もう1回やろう」という動機付けを自然に得やすくなります。この「小さな成功の積み重ね」は、長期プロジェクトや勉強など、ゴールが遠く感じられる作業において特に力を発揮します。時間を可視化し、成果を記録するという行為自体が、自己効力感の向上にもつながっていると言えるでしょう。

## 関連ツール

> サブスクの年間コストを把握しよう → [サブスク管理計算ツール](/ja/tools/subscription-cost-calculator/)

> フリーランスの適正報酬を計算 → [フリーランス報酬計算ツール](/ja/tools/freelance-hoshu-calculator/)

> 時給と年収を相互変換 → [時給換算ツール](/ja/tools/jikyuu-kansan-calculator/)

---

**確定申告・経費管理を自動化しませんか？**

ポモドーロテクニックで作業効率を上げたら、バックオフィス業務も効率化。クラウド会計ソフト「freee」なら、経費精算・確定申告がスマホで完結します。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
