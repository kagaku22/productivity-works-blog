---
title: "Typing Speed Test — Free WPM Tester"
description: "Test your typing speed and accuracy online. No sign-up, no downloads. Get your WPM score instantly with real-time feedback."
date: 2025-05-16
categories: ["Free Tools"]
slug: "typing-speed-test"
ShowToc: false
aliases: ["/tools/typing-test/", "/tools/wpm-test/"]
cover:
  image: "/images/covers/typing-speed-test.png"
  alt: "Typing Speed Test"
---

<div id="type-app">

<style>
  #type-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    max-width: 800px;
    margin: 0 auto;
    color: #e2e8f0;
  }
  #type-app * { box-sizing: border-box; }

  #type-app .ta-card {
    background: #1e293b;
    border: 1px solid #334155;
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 20px;
  }

  #type-app .ta-controls {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    align-items: center;
    margin-bottom: 0;
  }

  #type-app .ta-control-group {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  #type-app .ta-label {
    font-size: 13px;
    color: #94a3b8;
    font-weight: 500;
    white-space: nowrap;
  }

  #type-app .ta-btn-group {
    display: flex;
    gap: 4px;
  }

  #type-app .ta-btn {
    background: #0f172a;
    border: 1px solid #334155;
    color: #94a3b8;
    padding: 6px 14px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 13px;
    font-weight: 500;
    transition: all 0.15s;
  }
  #type-app .ta-btn:hover {
    border-color: #2563eb;
    color: #60a5fa;
  }
  #type-app .ta-btn.active {
    background: #2563eb;
    border-color: #2563eb;
    color: #fff;
  }

  #type-app .ta-start-btn {
    background: #2563eb;
    border: none;
    color: #fff;
    padding: 8px 22px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    transition: background 0.15s;
    margin-left: auto;
  }
  #type-app .ta-start-btn:hover { background: #1d4ed8; }
  #type-app .ta-start-btn:disabled { background: #475569; cursor: not-allowed; }

  #type-app .ta-progress-bar {
    height: 6px;
    background: #0f172a;
    border-radius: 3px;
    overflow: hidden;
    margin-bottom: 20px;
  }
  #type-app .ta-progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #2563eb, #60a5fa);
    border-radius: 3px;
    transition: width 0.25s linear;
    width: 0%;
  }

  #type-app .ta-passage {
    font-size: 20px;
    line-height: 1.8;
    letter-spacing: 0.02em;
    background: #0f172a;
    border-radius: 10px;
    padding: 20px;
    margin-bottom: 16px;
    min-height: 100px;
    user-select: none;
    word-break: break-word;
  }

  #type-app .ta-char { color: #475569; }
  #type-app .ta-char.correct { color: #4ade80; }
  #type-app .ta-char.incorrect { color: #f87171; background: rgba(248,113,113,0.12); border-radius: 2px; }
  #type-app .ta-char.cursor {
    border-left: 2px solid #60a5fa;
    margin-left: -1px;
    padding-left: 1px;
    animation: ta-blink 1s step-end infinite;
  }
  @keyframes ta-blink { 0%,100%{opacity:1} 50%{opacity:0} }

  #type-app .ta-input {
    width: 100%;
    background: #0f172a;
    border: 2px solid #334155;
    border-radius: 8px;
    color: #e2e8f0;
    font-size: 16px;
    padding: 12px 16px;
    outline: none;
    transition: border-color 0.15s;
    resize: none;
    font-family: inherit;
    caret-color: #60a5fa;
  }
  #type-app .ta-input:focus { border-color: #2563eb; }
  #type-app .ta-input:disabled { opacity: 0.5; cursor: not-allowed; }

  #type-app .ta-timer-display {
    text-align: center;
    font-size: 48px;
    font-weight: 700;
    color: #60a5fa;
    font-variant-numeric: tabular-nums;
    margin: 4px 0;
  }
  #type-app .ta-timer-label {
    text-align: center;
    font-size: 12px;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }

  #type-app .ta-stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin-top: 4px;
  }
  @media (max-width: 600px) {
    #type-app .ta-stats-grid { grid-template-columns: repeat(2, 1fr); }
  }

  #type-app .ta-stat {
    background: #0f172a;
    border-radius: 10px;
    padding: 14px;
    text-align: center;
  }
  #type-app .ta-stat-val {
    font-size: 28px;
    font-weight: 700;
    color: #60a5fa;
    font-variant-numeric: tabular-nums;
  }
  #type-app .ta-stat-lbl {
    font-size: 11px;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-top: 2px;
  }

  #type-app .ta-result-card {
    background: #1e293b;
    border: 1px solid #2563eb44;
    border-radius: 12px;
    padding: 28px;
    text-align: center;
    display: none;
  }
  #type-app .ta-result-card.visible { display: block; }
  #type-app .ta-result-title {
    font-size: 22px;
    font-weight: 700;
    color: #e2e8f0;
    margin-bottom: 20px;
  }
  #type-app .ta-result-wpm {
    font-size: 64px;
    font-weight: 800;
    color: #60a5fa;
    line-height: 1;
  }
  #type-app .ta-result-wpm-lbl {
    font-size: 14px;
    color: #94a3b8;
    margin-bottom: 20px;
    margin-top: 4px;
  }
  #type-app .ta-result-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    margin-bottom: 24px;
  }
  @media (max-width: 500px) {
    #type-app .ta-result-grid { grid-template-columns: repeat(1, 1fr); }
  }

  #type-app .ta-retry-btn {
    background: #2563eb;
    border: none;
    color: #fff;
    padding: 10px 32px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 15px;
    font-weight: 600;
    transition: background 0.15s;
  }
  #type-app .ta-retry-btn:hover { background: #1d4ed8; }

  #type-app .ta-history {
    margin-top: 4px;
  }
  #type-app .ta-history-title {
    font-size: 14px;
    font-weight: 600;
    color: #94a3b8;
    margin-bottom: 10px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }
  #type-app .ta-history-empty {
    color: #475569;
    font-size: 13px;
    text-align: center;
    padding: 16px;
  }
  #type-app .ta-history-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  #type-app .ta-history-table th {
    color: #64748b;
    font-weight: 500;
    text-align: left;
    padding: 6px 10px;
    border-bottom: 1px solid #1e293b;
  }
  #type-app .ta-history-table td {
    padding: 8px 10px;
    color: #cbd5e1;
    border-bottom: 1px solid #1e293b22;
  }
  #type-app .ta-history-table tr:last-child td { border-bottom: none; }
  #type-app .ta-history-clear {
    background: none;
    border: 1px solid #334155;
    color: #64748b;
    padding: 4px 10px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 12px;
    float: right;
    transition: all 0.15s;
  }
  #type-app .ta-history-clear:hover { border-color: #f87171; color: #f87171; }

  #type-app .ta-msg {
    font-size: 13px;
    color: #64748b;
    text-align: center;
    padding: 8px 0 0;
  }
</style>

<!-- Controls -->
<div class="ta-card">
  <div class="ta-controls">
    <div class="ta-control-group">
      <span class="ta-label">Duration</span>
      <div class="ta-btn-group" id="ta-dur-group">
        <button class="ta-btn" data-dur="30">30s</button>
        <button class="ta-btn active" data-dur="60">60s</button>
        <button class="ta-btn" data-dur="120">120s</button>
      </div>
    </div>
    <div class="ta-control-group">
      <span class="ta-label">Difficulty</span>
      <div class="ta-btn-group" id="ta-diff-group">
        <button class="ta-btn active" data-diff="easy">Easy</button>
        <button class="ta-btn" data-diff="medium">Medium</button>
        <button class="ta-btn" data-diff="hard">Hard</button>
      </div>
    </div>
    <button class="ta-start-btn" id="ta-reset-btn">Reset</button>
  </div>
</div>

<!-- Timer + Progress -->
<div class="ta-card" style="padding:16px 24px;">
  <div class="ta-timer-label">Time Remaining</div>
  <div class="ta-timer-display" id="ta-timer">60</div>
  <div class="ta-progress-bar">
    <div class="ta-progress-fill" id="ta-progress"></div>
  </div>
  <div class="ta-stats-grid">
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-wpm-live">0</div>
      <div class="ta-stat-lbl">WPM</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-acc-live">—</div>
      <div class="ta-stat-lbl">Accuracy</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-chars-live">0</div>
      <div class="ta-stat-lbl">Characters</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-errors-live">0</div>
      <div class="ta-stat-lbl">Errors</div>
    </div>
  </div>
</div>

<!-- Passage + Input -->
<div class="ta-card">
  <div class="ta-passage" id="ta-passage" aria-label="Text to type"></div>
  <textarea
    class="ta-input"
    id="ta-input"
    rows="3"
    placeholder="Click here and start typing to begin the test…"
    autocomplete="off"
    autocorrect="off"
    autocapitalize="off"
    spellcheck="false"
  ></textarea>
  <p class="ta-msg" id="ta-msg">Timer starts on your first keystroke.</p>
</div>

<!-- Result -->
<div class="ta-result-card" id="ta-result">
  <div class="ta-result-title">Test Complete!</div>
  <div class="ta-result-wpm" id="ta-res-wpm">0</div>
  <div class="ta-result-wpm-lbl">Words Per Minute</div>
  <div class="ta-result-grid">
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-res-acc">0%</div>
      <div class="ta-stat-lbl">Accuracy</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-res-time">0s</div>
      <div class="ta-stat-lbl">Time Taken</div>
    </div>
    <div class="ta-stat">
      <div class="ta-stat-val" id="ta-res-chars">0</div>
      <div class="ta-stat-lbl">Characters</div>
    </div>
  </div>
  <button class="ta-retry-btn" id="ta-retry-btn">Try Again</button>
</div>

<!-- History -->
<div class="ta-card ta-history" id="ta-history-card">
  <div class="ta-history-title">
    Past Results
    <button class="ta-history-clear" id="ta-clear-hist">Clear</button>
  </div>
  <div id="ta-history-body"></div>
</div>

<script>
(function(){
  // ─── Passages ───────────────────────────────────────────────────────────────
  const PASSAGES = {
    easy: [
      "the quick brown fox jumps over the lazy dog and runs away into the forest where it finds a warm and cozy den to rest for the night after a long day of play",
      "she sells sea shells by the sea shore and the shells she sells are the finest you can find anywhere along the coast from here to the distant lighthouse",
      "all that glitters is not gold and not all those who wander are lost in the woods they may simply be exploring new paths and finding beauty in the unknown",
      "a friend in need is a friend indeed and those who stand by you through thick and thin are the ones worth keeping close to your heart for all your life",
      "the sun rises in the east and sets in the west and every day brings a new chance to do better to be kinder and to find joy in the small things around us",
      "good things come to those who wait but better things come to those who work hard every single day and never give up on the dreams that keep them going forward",
      "it was a bright cold day in april and the clocks were striking thirteen as the people walked through the wide grey streets under a pale and cloudy sky",
      "to be or not to be that is the question and whether it is nobler in the mind to suffer the slings and arrows of outrageous fortune or to take arms against them",
      "life is what happens when you are busy making other plans so be sure to look up once in a while and enjoy the world that is right in front of you today",
      "in the middle of every difficulty lies opportunity and if you look hard enough and stay patient you will always find a way through to the other side",
    ],
    medium: [
      "Productivity is not about doing more things faster. It is about doing the right things with full attention, eliminating distractions, and recovering well so you can show up fully each day.",
      "The best time to plant a tree was twenty years ago. The second best time is now. Stop waiting for perfect conditions and start building the habits that will define your future self.",
      "Deep work requires protecting large blocks of uninterrupted time. Checking email constantly and attending too many meetings are the silent killers of meaningful cognitive progress.",
      "Typing speed improves with deliberate practice, not just repetition. Focus on accuracy first; speed will follow naturally as your muscle memory builds over weeks of consistent effort.",
      "A morning routine anchors the rest of your day. Wake at a consistent time, avoid screens for the first thirty minutes, and do your most important creative work before checking messages.",
      "Flow state occurs when challenge and skill are balanced. Work that is too easy leads to boredom; work that is too hard leads to anxiety. The sweet spot is just beyond your comfort zone.",
      "Reading widely outside your domain builds unexpected connections between ideas. The best innovations often come from people who borrow frameworks from one field and apply them to another.",
      "Every system is perfectly designed to get the results it gets. If you want different outcomes, you must redesign the inputs, the process, and the feedback loops driving your behavior.",
      "Writing clarifies thinking. If you cannot explain an idea simply in writing, you probably do not understand it as well as you think. The act of writing forces precision and exposes gaps.",
      "Rest is not a reward for finishing work. It is a prerequisite for doing good work. Sleep, breaks, and leisure are investments that compound into sharper focus and better decisions.",
    ],
    hard: [
      "Asymmetric cryptography relies on the computational intractability of factoring large semiprime integers, forming the mathematical foundation for RSA encryption used in TLS handshakes across the web.",
      "Gradient descent optimization iteratively adjusts model parameters by computing the partial derivative of the loss function with respect to each weight, moving opposite to the gradient direction.",
      "Kubernetes orchestrates containerized workloads across a cluster by abstracting infrastructure into declarative manifests, enabling horizontal pod autoscaling, rolling deployments, and self-healing capabilities.",
      "Transformer architectures leverage multi-head self-attention mechanisms to compute contextualized token representations, enabling parallelization that recurrent networks cannot achieve due to sequential dependencies.",
      "Zero-knowledge proofs allow one party to convince another that a statement is true without revealing any information beyond the validity of the assertion itself, enabling privacy-preserving verification.",
      "Distributed consensus protocols such as Raft achieve fault tolerance by electing a leader node responsible for log replication, ensuring linearizability even when a minority of nodes fail arbitrarily.",
      "Compilers perform lexical analysis, syntactic parsing, semantic analysis, intermediate representation generation, optimization passes, and target code emission as distinct phases in the translation pipeline.",
      "Quantum entanglement produces correlations between particles that violate Bell inequalities, demonstrating that no local hidden-variable theory can reproduce the predictions of standard quantum mechanics.",
      "Differential privacy adds calibrated Laplace or Gaussian noise to query outputs, providing a mathematically rigorous guarantee that individual records cannot be inferred from aggregate statistical releases.",
      "Microservice architectures decompose monolithic applications into independently deployable services communicating via APIs, enabling autonomous team ownership but introducing distributed systems complexity such as network partitioning.",
    ],
  };

  // ─── State ──────────────────────────────────────────────────────────────────
  let duration = 60;
  let difficulty = "easy";
  let passage = "";
  let charIndex = 0;
  let totalTyped = 0;
  let totalErrors = 0;
  let startTime = null;
  let timerInterval = null;
  let running = false;
  let finished = false;

  // ─── Elements ───────────────────────────────────────────────────────────────
  const elPassage    = document.getElementById("ta-passage");
  const elInput      = document.getElementById("ta-input");
  const elTimer      = document.getElementById("ta-timer");
  const elProgress   = document.getElementById("ta-progress");
  const elWpmLive    = document.getElementById("ta-wpm-live");
  const elAccLive    = document.getElementById("ta-acc-live");
  const elCharsLive  = document.getElementById("ta-chars-live");
  const elErrorsLive = document.getElementById("ta-errors-live");
  const elResult     = document.getElementById("ta-result");
  const elResWpm     = document.getElementById("ta-res-wpm");
  const elResAcc     = document.getElementById("ta-res-acc");
  const elResTime    = document.getElementById("ta-res-time");
  const elResChars   = document.getElementById("ta-res-chars");
  const elMsg        = document.getElementById("ta-msg");
  const elRetryBtn   = document.getElementById("ta-retry-btn");
  const elResetBtn   = document.getElementById("ta-reset-btn");
  const elHistBody   = document.getElementById("ta-history-body");
  const elClearHist  = document.getElementById("ta-clear-hist");

  // ─── Helpers ────────────────────────────────────────────────────────────────
  function pickPassage() {
    const pool = PASSAGES[difficulty];
    return pool[Math.floor(Math.random() * pool.length)];
  }

  function renderPassage() {
    elPassage.innerHTML = passage.split("").map((ch, i) => {
      let cls = "ta-char";
      if (i < charIndex) cls += " correct"; // will be updated per input
      if (i === charIndex) cls += " cursor";
      return `<span class="${cls}" data-i="${i}">${ch === " " ? "&nbsp;" : ch}</span>`;
    }).join("");
  }

  function updatePassageDisplay(typed) {
    const spans = elPassage.querySelectorAll(".ta-char");
    spans.forEach((s, i) => {
      s.className = "ta-char";
      if (i < typed.length) {
        s.classList.add(typed[i] === passage[i] ? "correct" : "incorrect");
      }
      if (i === typed.length) s.classList.add("cursor");
    });
  }

  function calcWpm(elapsed) {
    // gross WPM: (chars typed / 5) / minutes
    const minutes = elapsed / 60000;
    if (minutes === 0) return 0;
    return Math.round((totalTyped / 5) / minutes);
  }

  function calcAcc() {
    if (totalTyped === 0) return null;
    return Math.round(((totalTyped - totalErrors) / totalTyped) * 100);
  }

  function updateLiveStats() {
    const elapsed = Date.now() - startTime;
    elWpmLive.textContent = calcWpm(elapsed);
    const acc = calcAcc();
    elAccLive.textContent = acc !== null ? acc + "%" : "—";
    elCharsLive.textContent = totalTyped;
    elErrorsLive.textContent = totalErrors;
  }

  function startTimer() {
    startTime = Date.now();
    running = true;
    elMsg.textContent = "Test in progress…";

    timerInterval = setInterval(() => {
      const elapsed = Date.now() - startTime;
      const remaining = Math.max(0, duration * 1000 - elapsed);
      const secs = Math.ceil(remaining / 1000);
      elTimer.textContent = secs;
      elProgress.style.width = ((1 - remaining / (duration * 1000)) * 100) + "%";
      updateLiveStats();

      if (remaining <= 0) {
        clearInterval(timerInterval);
        finishTest();
      }
    }, 100);
  }

  function finishTest() {
    running = false;
    finished = true;
    elInput.disabled = true;
    const elapsed = startTime ? Date.now() - startTime : duration * 1000;
    const actualSecs = Math.min(Math.round(elapsed / 1000), duration);
    const wpm = calcWpm(Math.min(elapsed, duration * 1000));
    const acc = calcAcc();

    elResWpm.textContent = wpm;
    elResAcc.textContent = (acc !== null ? acc : 0) + "%";
    elResTime.textContent = actualSecs + "s";
    elResChars.textContent = totalTyped;
    elResult.classList.add("visible");
    elMsg.textContent = "Test complete!";

    saveHistory({ wpm, acc: acc ?? 0, time: actualSecs, chars: totalTyped, diff: difficulty, dur: duration });
    renderHistory();
  }

  function reset() {
    clearInterval(timerInterval);
    running = false;
    finished = false;
    charIndex = 0;
    totalTyped = 0;
    totalErrors = 0;
    startTime = null;
    passage = pickPassage();
    elInput.value = "";
    elInput.disabled = false;
    elInput.focus();
    elTimer.textContent = duration;
    elProgress.style.width = "0%";
    elWpmLive.textContent = "0";
    elAccLive.textContent = "—";
    elCharsLive.textContent = "0";
    elErrorsLive.textContent = "0";
    elResult.classList.remove("visible");
    elMsg.textContent = "Timer starts on your first keystroke.";
    renderPassage();
  }

  // ─── Input handling ──────────────────────────────────────────────────────────
  elInput.addEventListener("input", function() {
    if (finished) return;
    const typed = this.value;

    if (!running && typed.length > 0) startTimer();
    if (!running && typed.length === 0) return;

    // Advance if passage needs extension (longer than current passage)
    // Clamp to passage length
    const clamped = typed.slice(0, passage.length);

    totalTyped = clamped.length;
    totalErrors = 0;
    for (let i = 0; i < clamped.length; i++) {
      if (clamped[i] !== passage[i]) totalErrors++;
    }

    updatePassageDisplay(clamped);
    updateLiveStats();

    // Auto-advance to next passage if completed
    if (clamped.length === passage.length && running) {
      passage = pickPassage();
      this.value = "";
      renderPassage();
    }
  });

  // Prevent paste
  elInput.addEventListener("paste", e => e.preventDefault());

  // ─── Controls ───────────────────────────────────────────────────────────────
  document.getElementById("ta-dur-group").addEventListener("click", e => {
    const btn = e.target.closest("[data-dur]");
    if (!btn) return;
    document.querySelectorAll("#ta-dur-group .ta-btn").forEach(b => b.classList.remove("active"));
    btn.classList.add("active");
    duration = parseInt(btn.dataset.dur);
    reset();
  });

  document.getElementById("ta-diff-group").addEventListener("click", e => {
    const btn = e.target.closest("[data-diff]");
    if (!btn) return;
    document.querySelectorAll("#ta-diff-group .ta-btn").forEach(b => b.classList.remove("active"));
    btn.classList.add("active");
    difficulty = btn.dataset.diff;
    reset();
  });

  elResetBtn.addEventListener("click", reset);
  elRetryBtn.addEventListener("click", reset);

  // ─── History ────────────────────────────────────────────────────────────────
  const HIST_KEY = "ta_history_en";

  function saveHistory(entry) {
    const hist = getHistory();
    hist.unshift({ ...entry, date: new Date().toLocaleDateString() });
    if (hist.length > 15) hist.length = 15;
    localStorage.setItem(HIST_KEY, JSON.stringify(hist));
  }

  function getHistory() {
    try { return JSON.parse(localStorage.getItem(HIST_KEY)) || []; }
    catch { return []; }
  }

  function renderHistory() {
    const hist = getHistory();
    if (hist.length === 0) {
      elHistBody.innerHTML = '<div class="ta-history-empty">No results yet. Complete a test to see your history.</div>';
      return;
    }
    elHistBody.innerHTML = `<table class="ta-history-table">
      <thead><tr>
        <th>#</th><th>WPM</th><th>Accuracy</th><th>Time</th><th>Chars</th><th>Difficulty</th><th>Date</th>
      </tr></thead>
      <tbody>${hist.map((r, i) => `<tr>
        <td>${i + 1}</td>
        <td><strong style="color:#60a5fa">${r.wpm}</strong></td>
        <td>${r.acc}%</td>
        <td>${r.time}s / ${r.dur}s</td>
        <td>${r.chars}</td>
        <td style="text-transform:capitalize">${r.diff}</td>
        <td>${r.date}</td>
      </tr>`).join("")}</tbody>
    </table>`;
  }

  elClearHist.addEventListener("click", () => {
    localStorage.removeItem(HIST_KEY);
    renderHistory();
  });

  // ─── Init ────────────────────────────────────────────────────────────────────
  reset();
  renderHistory();
})();
</script>

</div>

---

**Related:** Time yourself — [Stopwatch](/tools/stopwatch/)
