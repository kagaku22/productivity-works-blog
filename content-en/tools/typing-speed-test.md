---
title: "Typing Speed Test"
date: 2025-05-16
description: "Free online typing speed test. Measure your WPM, accuracy, and keystrokes in real time — with multiple text samples and difficulty levels. No sign-up required."
categories: ["Free Tools"]
slug: "typing-speed-test"
ShowToc: false
cover:
  image: "/images/covers/typing-speed-test.png"
  alt: "Typing Speed Test"
---

Find out how fast you really type — just start typing to begin, and get your WPM, accuracy, and error count updated live. No account needed, works entirely in your browser.

<div id="tt-app">
<style>
#tt-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1e293b;
}
#tt-app * { box-sizing: border-box; }

#tt-app .tt-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: flex-end;
  margin-bottom: 18px;
}
#tt-app .tt-control-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
#tt-app .tt-control-group label {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
}
#tt-app select {
  background: #f1f5f9;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  padding: 7px 30px 7px 12px;
  font-size: 14px;
  color: #1e293b;
  cursor: pointer;
  font-family: inherit;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%2364748b' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 10px center;
}
#tt-app select:focus { outline: 2px solid #3b82f6; outline-offset: 1px; }

#tt-app .tt-btn {
  padding: 8px 20px;
  border-radius: 6px;
  border: none;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.15s, transform 0.1s;
}
#tt-app .tt-btn:active { transform: scale(0.97); }
#tt-app .tt-btn-primary { background: #2563eb; color: #fff; }
#tt-app .tt-btn-primary:hover { background: #3b82f6; }

#tt-app .tt-timer-row {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 12px;
}
#tt-app .tt-timer {
  font-size: 26px;
  font-weight: 700;
  font-variant-numeric: tabular-nums;
  color: #1e293b;
  min-width: 56px;
}
#tt-app .tt-timer.tt-warn { color: #ef4444; }

#tt-app .tt-badge {
  font-size: 12px;
  font-weight: 600;
  padding: 3px 10px;
  border-radius: 20px;
  background: #e2e8f0;
  color: #475569;
}
#tt-app .tt-badge.tt-running { background: #dcfce7; color: #15803d; }
#tt-app .tt-badge.tt-waiting { background: #fef9c3; color: #a16207; }

#tt-app .tt-text-box {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 20px 22px;
  font-size: 18px;
  line-height: 1.75;
  letter-spacing: 0.01em;
  min-height: 110px;
  user-select: none;
  margin-bottom: 14px;
  word-break: break-word;
  position: relative;
  cursor: text;
}
#tt-app .tt-text-box:focus-within {
  outline: 2px solid #3b82f6;
  outline-offset: 2px;
}

#tt-app .tt-ch-ok   { color: #16a34a; }
#tt-app .tt-ch-err  { color: #ef4444; text-decoration: line-through; }
#tt-app .tt-ch-cur  { color: #2563eb; background: #dbeafe; border-radius: 2px; }
#tt-app .tt-ch-rem  { color: #94a3b8; }

#tt-app .tt-cursor-bar {
  display: inline-block;
  width: 2px;
  height: 1.1em;
  background: #3b82f6;
  vertical-align: middle;
  animation: tt-blink 1s step-end infinite;
}
@keyframes tt-blink { 0%,100%{opacity:1} 50%{opacity:0} }

#tt-app .tt-ghost-input {
  position: absolute;
  top: 0; left: 0;
  width: 1px; height: 1px;
  opacity: 0;
  pointer-events: none;
}

#tt-app .tt-stats {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 18px;
}
#tt-app .tt-stat {
  flex: 1 1 100px;
  background: #f1f5f9;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 12px 14px;
  text-align: center;
}
#tt-app .tt-sv {
  font-size: 24px;
  font-weight: 700;
  font-variant-numeric: tabular-nums;
  color: #1e293b;
  line-height: 1.2;
}
#tt-app .tt-sl {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #64748b;
  margin-top: 3px;
}

#tt-app .tt-results {
  display: none;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 28px 24px;
  text-align: center;
  margin-bottom: 18px;
}
#tt-app .tt-results.tt-show { display: block; }
#tt-app .tt-res-title {
  font-size: 20px;
  font-weight: 700;
  color: #1e293b;
  margin: 0 0 6px;
}
#tt-app .tt-rating {
  display: inline-block;
  font-size: 15px;
  font-weight: 700;
  padding: 4px 16px;
  border-radius: 20px;
  margin-bottom: 20px;
}
#tt-app .r-beginner { background: #f1f5f9; color: #475569; }
#tt-app .r-average  { background: #fef9c3; color: #854d0e; }
#tt-app .r-good     { background: #dcfce7; color: #15803d; }
#tt-app .r-pro      { background: #dbeafe; color: #1d4ed8; }
#tt-app .r-elite    { background: #f3e8ff; color: #7e22ce; }

#tt-app .tt-res-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 14px;
  margin-bottom: 20px;
}
#tt-app .tt-rs { min-width: 110px; }
#tt-app .tt-rs-v {
  font-size: 32px;
  font-weight: 800;
  color: #0f172a;
  font-variant-numeric: tabular-nums;
}
#tt-app .tt-rs-l {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #64748b;
}

#tt-app .tt-hint {
  font-size: 13px;
  color: #94a3b8;
  margin-top: 4px;
  text-align: center;
}

@media (max-width: 520px) {
  #tt-app .tt-text-box { font-size: 15px; padding: 14px; }
  #tt-app .tt-sv { font-size: 20px; }
  #tt-app .tt-rs-v { font-size: 26px; }
}
</style>

<!-- Controls -->
<div class="tt-controls">
  <div class="tt-control-group">
    <label for="tt-sel-diff">Difficulty</label>
    <select id="tt-sel-diff">
      <option value="easy">Easy</option>
      <option value="medium" selected>Medium</option>
      <option value="hard">Hard</option>
    </select>
  </div>
  <div class="tt-control-group">
    <label for="tt-sel-dur">Duration</label>
    <select id="tt-sel-dur">
      <option value="30">30 seconds</option>
      <option value="60" selected>60 seconds</option>
      <option value="120">120 seconds</option>
    </select>
  </div>
  <div class="tt-control-group">
    <label>&nbsp;</label>
    <button class="tt-btn tt-btn-primary" id="tt-reset-btn">Reset</button>
  </div>
</div>

<!-- Timer row -->
<div class="tt-timer-row">
  <div class="tt-timer" id="tt-timer">60s</div>
  <div class="tt-badge tt-waiting" id="tt-badge">Press any key to start</div>
</div>

<!-- Text display -->
<div class="tt-text-box" id="tt-box" tabindex="0" role="textbox" aria-label="Typing area — click here and start typing">
  <span id="tt-chars"></span>
  <input
    class="tt-ghost-input"
    id="tt-input"
    type="text"
    autocomplete="off"
    autocorrect="off"
    autocapitalize="off"
    spellcheck="false"
    aria-hidden="true"
    tabindex="-1"
  >
</div>
<p class="tt-hint" id="tt-hint">Click the text area above and start typing — the timer starts on your first keystroke.</p>

<!-- Live stats -->
<div class="tt-stats">
  <div class="tt-stat"><div class="tt-sv" id="tt-s-wpm">0</div><div class="tt-sl">WPM</div></div>
  <div class="tt-stat"><div class="tt-sv" id="tt-s-acc">100%</div><div class="tt-sl">Accuracy</div></div>
  <div class="tt-stat"><div class="tt-sv" id="tt-s-chars">0</div><div class="tt-sl">Characters</div></div>
  <div class="tt-stat"><div class="tt-sv" id="tt-s-errs">0</div><div class="tt-sl">Errors</div></div>
  <div class="tt-stat"><div class="tt-sv" id="tt-s-time">0s</div><div class="tt-sl">Elapsed</div></div>
</div>

<!-- Results -->
<div class="tt-results" id="tt-results">
  <p class="tt-res-title">Time's Up!</p>
  <div class="tt-rating" id="tt-rating"></div>
  <div class="tt-res-grid">
    <div class="tt-rs"><div class="tt-rs-v" id="tt-r-wpm">0</div><div class="tt-rs-l">WPM</div></div>
    <div class="tt-rs"><div class="tt-rs-v" id="tt-r-acc">0%</div><div class="tt-rs-l">Accuracy</div></div>
    <div class="tt-rs"><div class="tt-rs-v" id="tt-r-chars">0</div><div class="tt-rs-l">Characters</div></div>
  </div>
  <button class="tt-btn tt-btn-primary" id="tt-retry-btn">Try Again</button>
</div>

<script>
(function () {
  // ── Sample texts ──────────────────────────────────────────────────────────
  var TEXTS = {
    easy: [
      "The cat sat on the mat and looked at the big red ball. It was a fun day for all.",
      "She can run fast. He can jump high. We all like to play in the park on sunny days.",
      "My dog loves to eat and sleep. He runs to the door when he hears the bell ring.",
      "The sun is bright today. The sky is blue and the clouds are soft and white above us.",
      "Tom went to the shop to buy some bread and milk. He also got a cake for his mom.",
      "Birds sing in the trees each morning. The sound fills the air and wakes the whole street."
    ],
    medium: [
      "Productivity is not about working more hours but about making every hour count with focused effort and clear priorities.",
      "Learning to type faster can save you hours each week, especially if you spend most of your day writing emails and documents.",
      "The best way to improve your workflow is to identify bottlenecks and address them one at a time rather than changing everything at once.",
      "Effective communication is the foundation of any successful team. Being clear and concise saves time and reduces misunderstandings.",
      "Good habits are built through consistent repetition over time. Small daily improvements compound into remarkable long-term results.",
      "Time management is less about controlling the clock and more about controlling your attention and the choices you make each day."
    ],
    hard: [
      "Asynchronous programming paradigms, including promises and async/await syntax, have fundamentally altered how JavaScript developers architect non-blocking I/O operations.",
      "Cognitive load theory posits that working memory has finite capacity; instructional designers must therefore scaffold complexity to prevent extraneous overload during acquisition.",
      "Distributed systems must address the CAP theorem's trilemma: consistency, availability, and partition tolerance cannot all be simultaneously guaranteed across network boundaries.",
      "Epigenetic mechanisms, such as DNA methylation and histone acetylation, regulate gene expression without altering the underlying nucleotide sequence of the genome.",
      "Quantitative easing, a non-conventional monetary policy instrument, involves central bank asset purchases to inject liquidity, thereby compressing long-duration yield spreads.",
      "Phenomenological inquiry, as articulated by Husserl and later Heidegger, brackets presuppositions to examine the structure of lived experience in its primordial givenness."
    ]
  };

  // ── State ─────────────────────────────────────────────────────────────────
  var s = {
    diff: "medium",
    dur: 60,
    text: "",
    typed: "",
    cumChars: 0,
    cumErrors: 0,
    errors: 0,
    elapsed: 0,
    running: false,
    done: false,
    tid: null,
    t0: null,
    used: { easy: [], medium: [], hard: [] }
  };

  // ── Elements ──────────────────────────────────────────────────────────────
  var eBox     = document.getElementById("tt-box");
  var eChars   = document.getElementById("tt-chars");
  var eInput   = document.getElementById("tt-input");
  var eTimer   = document.getElementById("tt-timer");
  var eBadge   = document.getElementById("tt-badge");
  var eHint    = document.getElementById("tt-hint");
  var eSWpm    = document.getElementById("tt-s-wpm");
  var eSAcc    = document.getElementById("tt-s-acc");
  var eSChars  = document.getElementById("tt-s-chars");
  var eSErrs   = document.getElementById("tt-s-errs");
  var eSTime   = document.getElementById("tt-s-time");
  var eResults = document.getElementById("tt-results");
  var eRating  = document.getElementById("tt-rating");
  var eRWpm    = document.getElementById("tt-r-wpm");
  var eRAcc    = document.getElementById("tt-r-acc");
  var eRChars  = document.getElementById("tt-r-chars");
  var eDiff    = document.getElementById("tt-sel-diff");
  var eDur     = document.getElementById("tt-sel-dur");
  var eBtnRst  = document.getElementById("tt-reset-btn");
  var eBtnRet  = document.getElementById("tt-retry-btn");

  // ── Helpers ───────────────────────────────────────────────────────────────
  function pick(diff) {
    var pool = TEXTS[diff];
    var used = s.used[diff];
    if (used.length >= pool.length) used.length = 0;
    var avail = [];
    for (var i = 0; i < pool.length; i++) {
      if (used.indexOf(i) === -1) avail.push(i);
    }
    var idx = avail[Math.floor(Math.random() * avail.length)];
    used.push(idx);
    return pool[idx];
  }

  function esc(c) {
    if (c === " ") return "&nbsp;";
    return c.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;");
  }

  function wpm(chars, secs) {
    if (secs < 1) return 0;
    return Math.round((chars / 5) / (secs / 60));
  }

  function acc(typed, errs) {
    if (typed === 0) return 100;
    return Math.max(0, Math.round(((typed - errs) / typed) * 100));
  }

  function rating(w) {
    if (w < 30)  return { label: "Beginner", cls: "r-beginner" };
    if (w < 50)  return { label: "Average",  cls: "r-average"  };
    if (w < 70)  return { label: "Good",     cls: "r-good"     };
    if (w < 100) return { label: "Pro",      cls: "r-pro"      };
    return             { label: "Elite",    cls: "r-elite"    };
  }

  // ── Render ────────────────────────────────────────────────────────────────
  function renderText() {
    var text = s.text;
    var typed = s.typed;
    var html = "";
    for (var i = 0; i < text.length; i++) {
      var ch = esc(text[i]);
      if (i < typed.length) {
        var cls = typed[i] === text[i] ? "tt-ch-ok" : "tt-ch-err";
        html += '<span class="' + cls + '">' + ch + "</span>";
      } else if (i === typed.length) {
        html += '<span class="tt-ch-cur">' + ch + "</span>";
      } else {
        html += '<span class="tt-ch-rem">' + ch + "</span>";
      }
    }
    if (typed.length >= text.length && text.length > 0) {
      html += '<span class="tt-cursor-bar"></span>';
    }
    eChars.innerHTML = html;
  }

  function updateStats() {
    var totalChars = s.cumChars + s.typed.length;
    var totalErrs  = s.cumErrors + s.errors;
    var w = wpm(totalChars, s.elapsed);
    var a = acc(totalChars, totalErrs);
    eSWpm.textContent   = w;
    eSAcc.textContent   = a + "%";
    eSChars.textContent = totalChars;
    eSErrs.textContent  = totalErrs;
    eSTime.textContent  = s.elapsed + "s";
  }

  // ── Timer ─────────────────────────────────────────────────────────────────
  function updateTimerDisplay() {
    var rem = s.dur - s.elapsed;
    eTimer.textContent = rem + "s";
    if (rem <= 10) eTimer.classList.add("tt-warn");
    else           eTimer.classList.remove("tt-warn");
  }

  function startTimer() {
    s.t0      = Date.now();
    s.running = true;
    eBadge.textContent  = "Running";
    eBadge.className    = "tt-badge tt-running";
    eHint.style.display = "none";
    updateTimerDisplay();
    s.tid = setInterval(function () {
      s.elapsed = Math.min(s.dur, Math.round((Date.now() - s.t0) / 1000));
      updateTimerDisplay();
      updateStats();
      if (s.elapsed >= s.dur) finish();
    }, 200);
  }

  function stopTimer() {
    if (s.tid) { clearInterval(s.tid); s.tid = null; }
  }

  // ── Finish ────────────────────────────────────────────────────────────────
  function finish() {
    stopTimer();
    s.running = false;
    s.done    = true;
    eInput.blur();
    eBadge.textContent = "Finished";
    eBadge.className   = "tt-badge";

    var totalChars = s.cumChars + s.typed.length;
    var totalErrs  = s.cumErrors + s.errors;
    var w = wpm(totalChars, s.elapsed);
    var a = acc(totalChars, totalErrs);
    var r = rating(w);

    eRWpm.textContent   = w;
    eRAcc.textContent   = a + "%";
    eRChars.textContent = totalChars;
    eRating.textContent = r.label;
    eRating.className   = "tt-rating " + r.cls;
    eResults.classList.add("tt-show");
  }

  // ── Reset ─────────────────────────────────────────────────────────────────
  function reset() {
    stopTimer();
    s.diff      = eDiff.value;
    s.dur       = parseInt(eDur.value, 10);
    s.text      = pick(s.diff);
    s.typed     = "";
    s.cumChars  = 0;
    s.cumErrors = 0;
    s.errors    = 0;
    s.elapsed   = 0;
    s.running   = false;
    s.done      = false;
    s.t0        = null;

    eTimer.textContent  = s.dur + "s";
    eTimer.classList.remove("tt-warn");
    eBadge.textContent  = "Press any key to start";
    eBadge.className    = "tt-badge tt-waiting";
    eHint.style.display = "";
    eInput.value        = "";
    eResults.classList.remove("tt-show");
    updateStats();
    renderText();
  }

  // ── Input events ──────────────────────────────────────────────────────────
  eBox.addEventListener("click", function () {
    if (!s.done) eInput.focus();
  });

  eBox.addEventListener("keydown", function (e) {
    if (!s.done && e.key.length === 1) eInput.focus();
  });

  eInput.addEventListener("input", function () {
    if (s.done) return;
    var val = eInput.value;
    if (!s.running && val.length > 0) startTimer();
    if (!s.running) return;

    // Clamp to text length
    if (val.length > s.text.length) {
      val = val.slice(0, s.text.length);
      eInput.value = val;
    }

    // Count per-character errors
    var errs = 0;
    for (var i = 0; i < val.length; i++) {
      if (val[i] !== s.text[i]) errs++;
    }
    s.typed  = val;
    s.errors = errs;

    renderText();
    updateStats();

    // Auto-advance when sample is fully typed
    if (s.typed.length === s.text.length) {
      s.cumChars  += s.typed.length;
      s.cumErrors += s.errors;
      s.text       = pick(s.diff);
      s.typed      = "";
      s.errors     = 0;
      eInput.value = "";
      renderText();
    }
  });

  eInput.addEventListener("paste", function (e) { e.preventDefault(); });
  eInput.addEventListener("cut",   function (e) { e.preventDefault(); });

  // ── Control events ────────────────────────────────────────────────────────
  eBtnRst.addEventListener("click", function () { reset(); eInput.focus(); });
  eBtnRet.addEventListener("click", function () { reset(); eInput.focus(); });
  eDiff.addEventListener("change",  function () { reset(); });
  eDur.addEventListener("change",   function () { reset(); });

  // ── Init ──────────────────────────────────────────────────────────────────
  reset();
})();
</script>
</div>

---

> Count lines of code → [Line Counter](/tools/line-counter/)
> Format your code → [Code Minifier & Beautifier](/tools/code-minifier/)
> Check text differences → [Text Diff Checker](/tools/text-diff-checker/)

## Related Articles

- [Best Language Learning Apps 2026: Actually Become Conversational](/posts/best-online-language-learning-apps-2026/)
