---
title: "Reading Speed Calculator"
date: 2025-05-16
description: "Free online reading speed test and calculator. Measure your WPM, estimate reading time for books and articles, and track your comprehension — no sign-up required."
categories: ["Free Tools"]
slug: "reading-speed-calculator"
ShowToc: false
cover:
  image: "/images/covers/reading-speed-calculator.png"
  alt: "Reading Speed Calculator"
---

<div id="rs-app">
<style>
#rs-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 800px;
margin: 0 auto;
color: #e2e8f0;
background: #0f172a;
border-radius: 12px;
overflow: hidden;
box-shadow: 0 4px 24px rgba(0,0,0,0.4);
}
#rs-app * { box-sizing: border-box; }

/* Tabs */
#rs-app .rs-tabs {
display: flex;
background: #1e293b;
border-bottom: 2px solid #334155;
}
#rs-app .rs-tab-btn {
flex: 1;
padding: 14px 8px;
border: none;
background: transparent;
color: #94a3b8;
font-size: 14px;
font-weight: 600;
cursor: pointer;
transition: color 0.2s, border-bottom 0.2s;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
letter-spacing: 0.02em;
}
#rs-app .rs-tab-btn:hover { color: #e2e8f0; }
#rs-app .rs-tab-btn.active {
color: #38bdf8;
border-bottom: 2px solid #38bdf8;
}

/* Panels */
#rs-app .rs-panel {
display: none;
padding: 24px;
}
#rs-app .rs-panel.active { display: block; }

/* Section titles */
#rs-app h2 {
font-size: 18px;
font-weight: 700;
margin: 0 0 6px 0;
color: #f1f5f9;
}
#rs-app .rs-subtitle {
font-size: 13px;
color: #64748b;
margin: 0 0 20px 0;
}

/* Passage selector */
#rs-app .rs-passage-selector {
display: flex;
gap: 8px;
margin-bottom: 16px;
flex-wrap: wrap;
}
#rs-app .rs-pill {
padding: 6px 14px;
border-radius: 9999px;
border: 1px solid #334155;
background: #1e293b;
color: #94a3b8;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: all 0.2s;
}
#rs-app .rs-pill:hover { border-color: #38bdf8; color: #e2e8f0; }
#rs-app .rs-pill.active {
background: #0369a1;
border-color: #38bdf8;
color: #f0f9ff;
}

/* Passage box */
#rs-app .rs-passage-box {
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
padding: 20px;
font-size: 15px;
line-height: 1.75;
color: #cbd5e1;
min-height: 160px;
margin-bottom: 16px;
position: relative;
user-select: none;
}
#rs-app .rs-passage-box.blurred { filter: blur(4px); pointer-events: none; }
#rs-app .rs-blur-overlay {
display: none;
position: absolute;
inset: 0;
align-items: center;
justify-content: center;
background: rgba(15,23,42,0.7);
border-radius: 8px;
font-size: 14px;
color: #94a3b8;
}
#rs-app .rs-passage-box.blurred + .rs-blur-overlay { display: flex; }

/* Timer display */
#rs-app .rs-timer {
font-size: 40px;
font-weight: 800;
font-variant-numeric: tabular-nums;
color: #38bdf8;
text-align: center;
margin: 16px 0;
letter-spacing: -1px;
}
#rs-app .rs-timer span { font-size: 18px; color: #64748b; margin-left: 4px; }

/* Buttons */
#rs-app .rs-btn {
display: inline-flex;
align-items: center;
justify-content: center;
gap: 6px;
padding: 10px 22px;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: all 0.2s;
letter-spacing: 0.02em;
}
#rs-app .rs-btn:disabled { opacity: 0.4; cursor: not-allowed; }
#rs-app .rs-btn-primary { background: #0369a1; color: #f0f9ff; }
#rs-app .rs-btn-primary:hover:not(:disabled) { background: #0284c7; }
#rs-app .rs-btn-success { background: #15803d; color: #f0fdf4; }
#rs-app .rs-btn-success:hover:not(:disabled) { background: #16a34a; }
#rs-app .rs-btn-ghost {
background: transparent;
border: 1px solid #334155;
color: #94a3b8;
}
#rs-app .rs-btn-ghost:hover:not(:disabled) { border-color: #94a3b8; color: #e2e8f0; }
#rs-app .rs-btn-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 20px;
}

/* Result card */
#rs-app .rs-result-card {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 20px;
margin-bottom: 20px;
}
#rs-app .rs-result-card h3 {
font-size: 13px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.08em;
margin: 0 0 12px 0;
}
#rs-app .rs-result-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
gap: 16px;
}
#rs-app .rs-stat {
text-align: center;
}
#rs-app .rs-stat-value {
font-size: 32px;
font-weight: 800;
color: #38bdf8;
display: block;
line-height: 1.1;
}
#rs-app .rs-stat-label {
font-size: 12px;
color: #64748b;
margin-top: 4px;
}

/* Quiz */
#rs-app .rs-quiz { margin-top: 8px; }
#rs-app .rs-question { margin-bottom: 18px; }
#rs-app .rs-question p {
font-size: 14px;
font-weight: 600;
color: #e2e8f0;
margin: 0 0 10px 0;
}
#rs-app .rs-options { display: flex; flex-direction: column; gap: 8px; }
#rs-app .rs-option {
display: flex;
align-items: center;
gap: 10px;
padding: 10px 14px;
border-radius: 7px;
border: 1px solid #334155;
background: #1e293b;
cursor: pointer;
font-size: 14px;
color: #cbd5e1;
transition: all 0.15s;
}
#rs-app .rs-option:hover { border-color: #38bdf8; color: #f1f5f9; }
#rs-app .rs-option.correct { border-color: #22c55e; background: #14532d; color: #bbf7d0; }
#rs-app .rs-option.incorrect { border-color: #ef4444; background: #450a0a; color: #fecaca; }
#rs-app .rs-option.disabled { pointer-events: none; }
#rs-app .rs-option-letter {
width: 24px;
height: 24px;
border-radius: 50%;
border: 1px solid #475569;
display: flex;
align-items: center;
justify-content: center;
font-size: 12px;
font-weight: 700;
flex-shrink: 0;
}

/* Divider */
#rs-app .rs-divider {
border: none;
border-top: 1px solid #334155;
margin: 20px 0;
}

/* Estimator */
#rs-app .rs-form-group { margin-bottom: 16px; }
#rs-app .rs-label {
display: block;
font-size: 13px;
font-weight: 600;
color: #94a3b8;
margin-bottom: 6px;
letter-spacing: 0.02em;
}
#rs-app .rs-input {
width: 100%;
padding: 10px 14px;
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
color: #e2e8f0;
font-size: 14px;
outline: none;
transition: border-color 0.2s;
font-family: inherit;
}
#rs-app .rs-input:focus { border-color: #38bdf8; }
#rs-app .rs-input::placeholder { color: #475569; }
#rs-app textarea.rs-input { resize: vertical; min-height: 90px; }

#rs-app .rs-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 480px) {
#rs-app .rs-row { grid-template-columns: 1fr; }
}

#rs-app .rs-presets {
display: flex;
gap: 8px;
flex-wrap: wrap;
margin-bottom: 16px;
}
#rs-app .rs-preset-chip {
padding: 5px 12px;
border-radius: 6px;
background: #1e293b;
border: 1px solid #334155;
color: #94a3b8;
font-size: 12px;
cursor: pointer;
transition: all 0.15s;
}
#rs-app .rs-preset-chip:hover { border-color: #38bdf8; color: #e2e8f0; }

#rs-app .rs-estimate-result {
background: linear-gradient(135deg, #0c1a2e 0%, #0f2942 100%);
border: 1px solid #1d4ed8;
border-radius: 10px;
padding: 24px;
text-align: center;
margin-top: 16px;
}
#rs-app .rs-estimate-time {
font-size: 48px;
font-weight: 800;
color: #38bdf8;
line-height: 1;
margin-bottom: 6px;
}
#rs-app .rs-estimate-label {
font-size: 13px;
color: #64748b;
}
#rs-app .rs-estimate-detail {
font-size: 13px;
color: #94a3b8;
margin-top: 10px;
}

/* Speed chart */
#rs-app .rs-chart-wrap {
margin-top: 24px;
}
#rs-app .rs-chart-title {
font-size: 13px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.08em;
margin: 0 0 14px 0;
}
#rs-app canvas#rs-chart {
width: 100%;
border-radius: 8px;
}

/* Cross-links */
#rs-app .rs-crosslinks {
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
padding: 14px 18px;
margin-top: 24px;
font-size: 13px;
color: #64748b;
line-height: 2;
}
#rs-app .rs-crosslinks a {
color: #38bdf8;
text-decoration: none;
font-weight: 600;
}
#rs-app .rs-crosslinks a:hover { text-decoration: underline; }
#rs-app .rs-crosslinks p { margin: 0; }

/* Utility */
#rs-app .rs-hidden { display: none !important; }
#rs-app .rs-badge {
display: inline-block;
padding: 2px 10px;
border-radius: 9999px;
font-size: 11px;
font-weight: 700;
margin-left: 8px;
vertical-align: middle;
}
#rs-app .rs-wpm-tag { background: #0369a1; color: #f0f9ff; }
</style>

<!-- Tab navigation -->
<div class="rs-tabs">
<button class="rs-tab-btn active" data-tab="test">Reading Speed Test</button>
<button class="rs-tab-btn" data-tab="estimator">Reading Time Estimator</button>
</div>

<!-- ==================== TAB 1: SPEED TEST ==================== -->
<div id="rs-panel-test" class="rs-panel active">
<h2>Reading Speed Test</h2>
<p class="rs-subtitle">Choose a passage, press Start, and read at your normal pace. Press Done when finished.</p>

<!-- Passage selector -->
<div class="rs-passage-selector">
<button class="rs-pill active" data-passage="easy">Easy</button>
<button class="rs-pill" data-passage="medium">Medium</button>
<button class="rs-pill" data-passage="hard">Hard</button>
</div>

<!-- Passage display -->
<div style="position:relative;">
<div id="rs-passage-text" class="rs-passage-box blurred"></div>
<div class="rs-blur-overlay">Press <strong style="margin:0 4px;">Start Reading</strong> to reveal the passage</div>
</div>

<!-- Timer -->
<div class="rs-timer" id="rs-timer-display">0:00 <span>sec</span></div>

<!-- Controls -->
<div class="rs-btn-row">
<button class="rs-btn rs-btn-primary" id="rs-btn-start">&#9654; Start Reading</button>
<button class="rs-btn rs-btn-success" id="rs-btn-done" disabled>&#10003; Done Reading</button>
<button class="rs-btn rs-btn-ghost" id="rs-btn-reset">&#8635; Reset</button>
</div>

<!-- Result section (hidden until done) -->
<div id="rs-test-result" class="rs-hidden">
<div class="rs-result-card">
<h3>Your Results</h3>
<div class="rs-result-grid">
<div class="rs-stat">
<span class="rs-stat-value" id="rs-wpm-val">—</span>
<div class="rs-stat-label">Words per Minute</div>
</div>
<div class="rs-stat">
<span class="rs-stat-value" id="rs-time-val">—</span>
<div class="rs-stat-label">Reading Time (sec)</div>
</div>
<div class="rs-stat">
<span class="rs-stat-value" id="rs-comp-val">—</span>
<div class="rs-stat-label">Comprehension</div>
</div>
</div>
</div>

<!-- Speed chart embedded in result -->
<div class="rs-chart-wrap">
<p class="rs-chart-title">How you compare</p>
<canvas id="rs-chart" height="180"></canvas>
</div>

<hr class="rs-divider">

<!-- Comprehension quiz -->
<h2 id="rs-quiz-heading">Comprehension Quiz</h2>
<p class="rs-subtitle">Answer to calculate your comprehension score.</p>
<div id="rs-quiz" class="rs-quiz"></div>
<div class="rs-btn-row">
<button class="rs-btn rs-btn-primary" id="rs-btn-submit-quiz">Submit Quiz</button>
</div>
<div id="rs-quiz-result" class="rs-hidden"></div>
</div>

<!-- Speed chart (shown before test if user already has a WPM saved) -->
<div id="rs-chart-pre" class="rs-chart-wrap rs-hidden">
<p class="rs-chart-title">Speed comparison</p>
<canvas id="rs-chart-pre-canvas" height="180"></canvas>
</div>
</div>

<!-- ==================== TAB 2: ESTIMATOR ==================== -->
<div id="rs-panel-estimator" class="rs-panel">
<h2>Reading Time Estimator</h2>
<p class="rs-subtitle">Enter a word count or paste your text to estimate how long it will take to read.</p>

<div class="rs-row">
<div class="rs-form-group">
<label class="rs-label" for="rs-wordcount-input">Word Count</label>
<input class="rs-input" type="number" id="rs-wordcount-input" placeholder="e.g. 5000" min="1">
</div>
<div class="rs-form-group">
<label class="rs-label" for="rs-wpm-input">Your Reading Speed (WPM)</label>
<input class="rs-input" type="number" id="rs-wpm-input" placeholder="250" min="1" value="250">
</div>
</div>

<div class="rs-form-group">
<label class="rs-label" for="rs-paste-input">Or paste text here (word count auto-calculated)</label>
<textarea class="rs-input" id="rs-paste-input" placeholder="Paste your article, chapter, or document here..."></textarea>
</div>

<p class="rs-label" style="margin-bottom:8px;">Quick presets</p>
<div class="rs-presets">
<button class="rs-preset-chip" data-words="80000">Novel (80k words)</button>
<button class="rs-preset-chip" data-words="1500">Blog Post (1.5k)</button>
<button class="rs-preset-chip" data-words="8000">Research Paper (8k)</button>
<button class="rs-preset-chip" data-words="5000">Textbook Chapter (5k)</button>
</div>

<div class="rs-btn-row">
<button class="rs-btn rs-btn-primary" id="rs-btn-estimate">Calculate Reading Time</button>
</div>

<div id="rs-estimate-output" class="rs-hidden">
<div class="rs-estimate-result">
<div class="rs-estimate-time" id="rs-est-time-display">—</div>
<div class="rs-estimate-label">estimated reading time</div>
<div class="rs-estimate-detail" id="rs-est-detail"></div>
</div>

<div class="rs-chart-wrap">
<p class="rs-chart-title">Speed comparison</p>
<canvas id="rs-chart-est" height="180"></canvas>
</div>
</div>
</div>

<!-- Cross-links (always visible at bottom) -->
<div class="rs-crosslinks" style="margin:0;border-radius:0;">
<p>&#8250; Test your typing speed &#8594; <a href="/tools/typing-speed-test/">Typing Speed Test</a></p>
<p>&#8250; Count text lines &#8594; <a href="/tools/line-counter/">Line Counter</a></p>
<p>&#8250; Generate lorem ipsum &#8594; <a href="/tools/lorem-ipsum-generator/">Lorem Ipsum Generator</a></p>
</div>

<script>
(function () {
'use strict';

/* ===================== DATA ===================== */
var passages = {
easy: {
text: "Reading is one of the most powerful habits you can develop. It expands your vocabulary, sharpens your thinking, and exposes you to ideas and perspectives you might never encounter otherwise. Whether you prefer fiction or nonfiction, the act of reading regularly trains your brain to focus and absorb information more efficiently. Many successful people credit daily reading as a cornerstone of their growth. Even fifteen minutes a day adds up to nearly a hundred hours of reading per year. The key is consistency. Pick topics you genuinely enjoy, and the habit will sustain itself naturally over time. Start small, stay curious, and let books do the rest.",
wordCount: 112,
questions: [
{
q: "According to the passage, what is the key to sustaining a reading habit?",
options: ["Reading for at least an hour daily", "Choosing topics you genuinely enjoy", "Focusing only on nonfiction books", "Reading before bedtime"],
answer: 1
},
{
q: "How many hours of reading does fifteen minutes a day approximately add up to per year?",
options: ["About 50 hours", "About 75 hours", "Nearly a hundred hours", "Over 200 hours"],
answer: 2
},
{
q: "What benefit of reading is NOT mentioned in the passage?",
options: ["Expanding vocabulary", "Improving memory retention", "Sharpening thinking", "Exposing you to new perspectives"],
answer: 1
}
]
},
medium: {
text: "Cognitive load theory, developed by John Sweller in the 1980s, proposes that our working memory has a limited capacity and that learning is most effective when instructional design respects this constraint. The theory distinguishes between three types of cognitive load: intrinsic load, which arises from the inherent complexity of the material; extraneous load, which is caused by poor instructional design that adds unnecessary mental effort; and germane load, which reflects the mental effort invested in building new schemas. Effective educators and instructional designers aim to minimize extraneous load while managing intrinsic load, allowing learners to channel more of their cognitive resources toward germane load—the productive processing that leads to lasting understanding. Modern e-learning platforms increasingly apply these principles through techniques such as segmenting content into smaller chunks, using worked examples, and reducing redundant information across modalities.",
wordCount: 132,
questions: [
{
q: "Which type of cognitive load is associated with poor instructional design?",
options: ["Intrinsic load", "Germane load", "Extraneous load", "Implicit load"],
answer: 2
},
{
q: "What is the primary goal of effective instructional designers according to the passage?",
options: ["Maximize germane load and intrinsic load", "Eliminate all forms of cognitive load", "Minimize extraneous load and maximize germane load", "Increase working memory capacity"],
answer: 2
},
{
q: "When was cognitive load theory developed?",
options: ["The 1960s", "The 1970s", "The 1980s", "The 1990s"],
answer: 2
}
]
},
hard: {
text: "Epistemological antirealism, in its strongest formulations, contends that the entities posited by mature scientific theories—quarks, dark matter, neural correlates of consciousness—are instrumental fictions whose predictive utility does not warrant ontological commitment. This contrasts sharply with scientific realism, which holds that the empirical success of a theory constitutes abductive grounds for believing in the approximate truth of its theoretical claims. The no-miracles argument, attributed to Hilary Putnam, crystallizes the realist intuition: the predictive success of science would be a miracle unless our theories are at least approximately tracking mind-independent reality. Antirealists, notably Bas van Fraassen through constructive empiricism, counter that empirical adequacy—a theory's agreement with observable phenomena—is the appropriate epistemic goal, and that positing unobservable entities exceeds what the evidence can rationally compel. The underdetermination thesis further complicates the realist position, suggesting that any finite body of observational data is logically consistent with infinitely many mutually incompatible theoretical descriptions, undermining the inference from empirical success to unique truth.",
wordCount: 153,
questions: [
{
q: "What does van Fraassen's constructive empiricism hold as the appropriate epistemic goal of science?",
options: ["Ontological commitment to unobservable entities", "Approximate truth of theoretical claims", "Empirical adequacy with observable phenomena", "Elimination of all theoretical posits"],
answer: 2
},
{
q: "The no-miracles argument is primarily a defense of which position?",
options: ["Epistemological antirealism", "Scientific realism", "Constructive empiricism", "Underdetermination thesis"],
answer: 1
},
{
q: "What does the underdetermination thesis suggest?",
options: ["Observations uniquely determine true theories", "Finite observational data is consistent with infinitely many incompatible theories", "Mature scientific theories should be rejected", "Empirical success implies ontological commitment"],
answer: 1
}
]
}
};

var speedBenchmarks = [
{ label: "Slow Reader", wpm: 150, color: "#ef4444" },
{ label: "Average Reader", wpm: 250, color: "#f59e0b" },
{ label: "Fast Reader", wpm: 400, color: "#22c55e" },
{ label: "Speed Reader", wpm: 700, color: "#a78bfa" }
];

/* ===================== STATE ===================== */
var state = {
activeTab: "test",
activePassage: "easy",
timerRunning: false,
timerStart: null,
timerInterval: null,
elapsedMs: 0,
testDone: false,
userWpm: null,
quizAnswers: {},
quizSubmitted: false
};

/* ===================== ELEMENTS ===================== */
var $ = function (id) { return document.getElementById(id); };

/* ===================== TABS ===================== */
document.querySelectorAll('#rs-app .rs-tab-btn').forEach(function (btn) {
btn.addEventListener('click', function () {
document.querySelectorAll('#rs-app .rs-tab-btn').forEach(function (b) { b.classList.remove('active'); });
btn.classList.add('active');
var tab = btn.dataset.tab;
document.querySelectorAll('#rs-app .rs-panel').forEach(function (p) { p.classList.remove('active'); });
$('rs-panel-' + tab).classList.add('active');
state.activeTab = tab;
if (tab === 'estimator' && state.userWpm) {
$('rs-wpm-input').value = state.userWpm;
}
});
});

/* ===================== PASSAGE SELECTOR ===================== */
document.querySelectorAll('#rs-app .rs-pill[data-passage]').forEach(function (pill) {
pill.addEventListener('click', function () {
if (state.timerRunning) return;
document.querySelectorAll('#rs-app .rs-pill[data-passage]').forEach(function (p) { p.classList.remove('active'); });
pill.classList.add('active');
state.activePassage = pill.dataset.passage;
resetTest();
});
});

/* ===================== PASSAGE RENDERING ===================== */
function renderPassage() {
var p = passages[state.activePassage];
$('rs-passage-text').textContent = p.text;
}
renderPassage();

/* ===================== TIMER ===================== */
function formatTime(ms) {
var s = Math.floor(ms / 1000);
var m = Math.floor(s / 60);
var sec = s % 60;
return m + ':' + (sec < 10 ? '0' : '') + sec;
}

function updateTimerDisplay() {
var elapsed = state.timerRunning ? (Date.now() - state.timerStart) : state.elapsedMs;
var s = Math.floor(elapsed / 1000);
$('rs-timer-display').innerHTML = formatTime(elapsed) + ' <span>elapsed</span>';
}

/* ===================== START ===================== */
$('rs-btn-start').addEventListener('click', function () {
if (state.testDone) return;
// Reveal passage
$('rs-passage-text').classList.remove('blurred');
state.timerRunning = true;
state.timerStart = Date.now();
state.timerInterval = setInterval(updateTimerDisplay, 100);
$('rs-btn-start').disabled = true;
$('rs-btn-done').disabled = false;
document.querySelectorAll('#rs-app .rs-pill[data-passage]').forEach(function (p) { p.style.pointerEvents = 'none'; });
});

/* ===================== DONE ===================== */
$('rs-btn-done').addEventListener('click', function () {
if (!state.timerRunning) return;
clearInterval(state.timerInterval);
state.elapsedMs = Date.now() - state.timerStart;
state.timerRunning = false;
updateTimerDisplay();

var p = passages[state.activePassage];
var minutes = state.elapsedMs / 60000;
var wpm = Math.round(p.wordCount / minutes);
state.userWpm = wpm;

$('rs-wpm-val').textContent = wpm;
$('rs-time-val').textContent = (state.elapsedMs / 1000).toFixed(1);
$('rs-comp-val').textContent = '—';

$('rs-test-result').classList.remove('rs-hidden');
state.testDone = true;
$('rs-btn-done').disabled = true;

renderQuiz();
drawChart('rs-chart', wpm);

// Scroll to result
$('rs-test-result').scrollIntoView({ behavior: 'smooth', block: 'start' });
});

/* ===================== RESET ===================== */
$('rs-btn-reset').addEventListener('click', resetTest);

function resetTest() {
clearInterval(state.timerInterval);
state.timerRunning = false;
state.timerStart = null;
state.elapsedMs = 0;
state.testDone = false;
state.quizAnswers = {};
state.quizSubmitted = false;

$('rs-timer-display').innerHTML = '0:00 <span>sec</span>';
$('rs-passage-text').classList.add('blurred');
$('rs-btn-start').disabled = false;
$('rs-btn-done').disabled = true;
$('rs-test-result').classList.add('rs-hidden');
$('rs-quiz').innerHTML = '';
$('rs-quiz-result').classList.add('rs-hidden');
document.querySelectorAll('#rs-app .rs-pill[data-passage]').forEach(function (p) { p.style.pointerEvents = ''; });
renderPassage();
}

/* ===================== QUIZ ===================== */
function renderQuiz() {
var p = passages[state.activePassage];
var html = '';
var letters = ['A', 'B', 'C', 'D'];
p.questions.forEach(function (q, qi) {
html += '<div class="rs-question"><p>' + (qi + 1) + '. ' + q.q + '</p><div class="rs-options">';
q.options.forEach(function (opt, oi) {
html += '<div class="rs-option" data-qi="' + qi + '" data-oi="' + oi + '">';
html += '<span class="rs-option-letter">' + letters[oi] + '</span>' + opt + '</div>';
});
html += '</div></div>';
});
$('rs-quiz').innerHTML = html;

document.querySelectorAll('#rs-app #rs-quiz .rs-option').forEach(function (el) {
el.addEventListener('click', function () {
if (state.quizSubmitted) return;
var qi = parseInt(el.dataset.qi);
var oi = parseInt(el.dataset.oi);
// Deselect siblings
document.querySelectorAll('#rs-app #rs-quiz .rs-option[data-qi="' + qi + '"]').forEach(function (s) {
s.style.borderColor = '';
s.style.background = '';
s.style.color = '';
});
el.style.borderColor = '#38bdf8';
el.style.background = '#0c2d48';
el.style.color = '#f0f9ff';
state.quizAnswers[qi] = oi;
});
});
}

$('rs-btn-submit-quiz').addEventListener('click', function () {
if (state.quizSubmitted) return;
var p = passages[state.activePassage];
var total = p.questions.length;
var correct = 0;

p.questions.forEach(function (q, qi) {
var selected = state.quizAnswers[qi];
var options = document.querySelectorAll('#rs-app #rs-quiz .rs-option[data-qi="' + qi + '"]');
options.forEach(function (opt) {
opt.classList.add('disabled');
opt.style.borderColor = '';
opt.style.background = '';
opt.style.color = '';
});
if (selected === undefined) {
// No answer — mark correct one
options[q.answer].classList.add('correct');
} else {
if (selected === q.answer) {
correct++;
options[selected].classList.add('correct');
} else {
options[selected].classList.add('incorrect');
options[q.answer].classList.add('correct');
}
}
});

state.quizSubmitted = true;
var pct = Math.round((correct / total) * 100);
$('rs-comp-val').textContent = pct + '%';

var grade = pct === 100 ? 'Excellent!' : pct >= 67 ? 'Good' : pct >= 33 ? 'Fair' : 'Needs review';
$('rs-quiz-result').innerHTML =
'<div class="rs-result-card" style="margin-top:16px;">' +
'<h3>Quiz Score</h3>' +
'<div class="rs-result-grid">' +
'<div class="rs-stat"><span class="rs-stat-value">' + correct + '/' + total + '</span><div class="rs-stat-label">Correct Answers</div></div>' +
'<div class="rs-stat"><span class="rs-stat-value">' + pct + '%</span><div class="rs-stat-label">Comprehension</div></div>' +
'<div class="rs-stat"><span class="rs-stat-value" style="font-size:22px;">' + grade + '</span><div class="rs-stat-label">Rating</div></div>' +
'</div></div>';
$('rs-quiz-result').classList.remove('rs-hidden');
$('rs-btn-submit-quiz').disabled = true;
});

/* ===================== CHART ===================== */
function drawChart(canvasId, userWpm) {
var canvas = $(canvasId);
if (!canvas) return;
var dpr = window.devicePixelRatio || 1;
var cssW = canvas.offsetWidth || 700;
var cssH = 180;
canvas.width = cssW * dpr;
canvas.height = cssH * dpr;
canvas.style.width = cssW + 'px';
canvas.style.height = cssH + 'px';

var ctx = canvas.getContext('2d');
ctx.scale(dpr, dpr);

var padding = { top: 10, left: 130, right: 60, bottom: 10 };
var barH = 22;
var gap = 16;
var rows = speedBenchmarks.length + (userWpm ? 1 : 0);
var maxWpm = Math.max(userWpm || 0, 800);

ctx.clearRect(0, 0, cssW, cssH);

var allBars = speedBenchmarks.slice();
if (userWpm) {
allBars.push({ label: "You", wpm: userWpm, color: "#38bdf8", isUser: true });
}

allBars.forEach(function (bar, i) {
var y = padding.top + i * (barH + gap);
var availW = cssW - padding.left - padding.right;
var barW = Math.max(4, (bar.wpm / maxWpm) * availW);

// Label
ctx.fillStyle = bar.isUser ? '#38bdf8' : '#94a3b8';
ctx.font = (bar.isUser ? 'bold ' : '') + '12px -apple-system, sans-serif';
ctx.textAlign = 'right';
ctx.textBaseline = 'middle';
ctx.fillText(bar.label, padding.left - 8, y + barH / 2);

// Bar background
ctx.fillStyle = '#1e293b';
ctx.beginPath();
ctx.roundRect ? ctx.roundRect(padding.left, y, availW, barH, 4) : ctx.rect(padding.left, y, availW, barH);
ctx.fill();

// Bar fill
ctx.fillStyle = bar.color;
ctx.globalAlpha = bar.isUser ? 1 : 0.75;
ctx.beginPath();
ctx.roundRect ? ctx.roundRect(padding.left, y, barW, barH, 4) : ctx.rect(padding.left, y, barW, barH);
ctx.fill();
ctx.globalAlpha = 1;

// WPM label
ctx.fillStyle = '#e2e8f0';
ctx.font = 'bold 11px -apple-system, sans-serif';
ctx.textAlign = 'left';
var labelX = padding.left + barW + 6;
if (labelX + 40 > cssW - 4) labelX = padding.left + barW - 42;
ctx.fillText(bar.wpm + ' WPM', labelX, y + barH / 2);
});
}

/* ===================== ESTIMATOR ===================== */
// Paste text → auto word count
$('rs-paste-input').addEventListener('input', function () {
var text = this.value.trim();
if (!text) { $('rs-wordcount-input').value = ''; return; }
var words = text.split(/\s+/).filter(function (w) { return w.length > 0; }).length;
$('rs-wordcount-input').value = words;
});

// Presets
document.querySelectorAll('#rs-app .rs-preset-chip').forEach(function (chip) {
chip.addEventListener('click', function () {
$('rs-wordcount-input').value = chip.dataset.words;
$('rs-paste-input').value = '';
});
});

// Calculate
$('rs-btn-estimate').addEventListener('click', function () {
var words = parseInt($('rs-wordcount-input').value);
var wpm = parseInt($('rs-wpm-input').value) || 250;
if (!words || words < 1) {
$('rs-wordcount-input').focus();
$('rs-wordcount-input').style.borderColor = '#ef4444';
setTimeout(function () { $('rs-wordcount-input').style.borderColor = ''; }, 1500);
return;
}
var totalMinutes = words / wpm;
var hours = Math.floor(totalMinutes / 60);
var mins = Math.round(totalMinutes % 60);

var timeStr;
if (hours === 0) {
timeStr = mins + ' min' + (mins !== 1 ? 's' : '');
} else {
timeStr = hours + 'h ' + (mins > 0 ? mins + 'm' : '');
}

$('rs-est-time-display').textContent = timeStr;
$('rs-est-detail').textContent =
words.toLocaleString() + ' words at ' + wpm + ' WPM — approximately ' + Math.ceil(totalMinutes) + ' minutes total';

$('rs-estimate-output').classList.remove('rs-hidden');
drawChart('rs-chart-est', wpm);
$('rs-estimate-output').scrollIntoView({ behavior: 'smooth', block: 'start' });
});

// Pre-fill WPM from test if available
if (state.userWpm) {
$('rs-wpm-input').value = state.userWpm;
}

})();
</script>
</div>

## Related Articles

- [How to Use ChatGPT for Studying: The Complete Student Guide 2026](/posts/how-to-use-chatgpt-for-studying-guide-2026/)
- [How to Build a Notion Book Tracker: Complete Template Guide (2026)](/posts/notion-book-tracker-template-guide-2026/)
- [Best Language Learning Apps 2026: Actually Become Conversational](/posts/best-online-language-learning-apps-2026/)
