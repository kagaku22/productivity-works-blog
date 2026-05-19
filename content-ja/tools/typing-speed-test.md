---
title: "タイピング速度テスト"
date: 2025-09-27
description: "無料のタイピング速度テスト。WPM・正確率・キーストロークをリアルタイム測定。難易度別のテキストで練習可能、会員登録不要。"
categories: ["無料ツール"]
slug: "typing-speed-test"
ShowToc: false
cover:
  image: "/images/covers/typing-speed-test-ja.png"
  alt: "タイピング速度テスト"
---

自分のタイピング速度を計測してみましょう。難易度を選んでテキストを入力するだけで、WPM・正確率・ミス数をリアルタイムで確認できます。会員登録不要、完全無料です。

<div id="tt-app">

<style>
#tt-app *,
#tt-app *::before,
#tt-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#tt-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
max-width: 760px;
margin: 0 auto;
color: #1e293b;
}

#tt-app h2 {
font-size: 18px;
font-weight: 700;
color: #0f172a;
margin-bottom: 16px;
display: flex;
align-items: center;
gap: 8px;
}

/* Controls */
#tt-controls {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin-bottom: 18px;
align-items: center;
}

#tt-controls label {
font-size: 13px;
font-weight: 600;
color: #475569;
margin-right: 4px;
}

#tt-controls select {
font-size: 13px;
padding: 6px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
background: #fff;
color: #1e293b;
cursor: pointer;
outline: none;
transition: border-color 0.15s;
}

#tt-controls select:focus {
border-color: #3b82f6;
}

#tt-btn-start {
padding: 7px 20px;
font-size: 13px;
font-weight: 700;
border: none;
border-radius: 6px;
cursor: pointer;
background: #3b82f6;
color: #fff;
transition: background 0.15s, transform 0.1s;
}

#tt-btn-start:hover {
background: #2563eb;
}

#tt-btn-start:active {
transform: scale(0.97);
}

#tt-btn-reset {
padding: 7px 16px;
font-size: 13px;
font-weight: 600;
border: 1.5px solid #94a3b8;
border-radius: 6px;
cursor: pointer;
background: #fff;
color: #475569;
transition: background 0.15s, border-color 0.15s;
}

#tt-btn-reset:hover {
background: #f1f5f9;
border-color: #64748b;
}

/* Timer */
#tt-timer-bar {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 14px;
}

#tt-timer-display {
font-size: 28px;
font-weight: 800;
color: #0f172a;
min-width: 56px;
text-align: center;
font-variant-numeric: tabular-nums;
}

#tt-timer-display.tt-warning {
color: #ef4444;
}

#tt-progress-track {
flex: 1;
height: 6px;
background: #e2e8f0;
border-radius: 99px;
overflow: hidden;
}

#tt-progress-fill {
height: 100%;
background: #3b82f6;
border-radius: 99px;
transition: width 0.5s linear, background 0.3s;
width: 100%;
}

#tt-progress-fill.tt-warning {
background: #ef4444;
}

/* Text display */
#tt-text-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
padding: 16px 18px;
font-size: 17px;
line-height: 1.9;
letter-spacing: 0.01em;
margin-bottom: 14px;
min-height: 88px;
word-break: break-all;
user-select: none;
cursor: text;
transition: border-color 0.15s;
}

#tt-text-box.tt-active {
border-color: #93c5fd;
box-shadow: 0 0 0 3px rgba(59,130,246,0.1);
}

#tt-text-box .char-pending {
color: #94a3b8;
}

#tt-text-box .char-current {
color: #1e40af;
background: #dbeafe;
border-radius: 3px;
padding: 0 1px;
animation: tt-blink 1s step-end infinite;
}

@keyframes tt-blink {
50% { background: #bfdbfe; }
}

#tt-text-box .char-correct {
color: #16a34a;
}

#tt-text-box .char-wrong {
color: #dc2626;
text-decoration: line-through;
text-decoration-color: #dc2626;
}

/* Input */
#tt-input {
width: 100%;
padding: 10px 14px;
font-size: 15px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
outline: none;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
margin-bottom: 16px;
font-family: inherit;
}

#tt-input:focus {
border-color: #3b82f6;
box-shadow: 0 0 0 3px rgba(59,130,246,0.1);
}

#tt-input:disabled {
background: #f1f5f9;
color: #94a3b8;
cursor: not-allowed;
}

/* Stats */
#tt-stats {
display: grid;
grid-template-columns: repeat(5, 1fr);
gap: 10px;
margin-bottom: 18px;
}

@media (max-width: 560px) {
#tt-stats {
grid-template-columns: repeat(3, 1fr);
}
}

@media (max-width: 380px) {
#tt-stats {
grid-template-columns: repeat(2, 1fr);
}
}

.tt-stat-card {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
padding: 10px 8px;
text-align: center;
}

.tt-stat-label {
font-size: 11px;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 4px;
}

.tt-stat-value {
font-size: 22px;
font-weight: 800;
color: #0f172a;
font-variant-numeric: tabular-nums;
line-height: 1;
}

.tt-stat-value.tt-wpm {
color: #2563eb;
}

.tt-stat-value.tt-acc {
color: #16a34a;
}

/* Result */
#tt-result {
display: none;
background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
border: 1.5px solid #bae6fd;
border-radius: 10px;
padding: 22px 20px;
margin-bottom: 18px;
text-align: center;
}

#tt-result h3 {
font-size: 17px;
font-weight: 700;
color: #0369a1;
margin-bottom: 14px;
}

#tt-result-level {
font-size: 26px;
font-weight: 800;
color: #0f172a;
margin-bottom: 10px;
}

#tt-result-stats {
display: flex;
justify-content: center;
gap: 24px;
flex-wrap: wrap;
margin-bottom: 16px;
}

.tt-res-item {
text-align: center;
}

.tt-res-item .rval {
font-size: 28px;
font-weight: 800;
color: #0c4a6e;
font-variant-numeric: tabular-nums;
display: block;
line-height: 1.1;
}

.tt-res-item .rlbl {
font-size: 12px;
color: #0369a1;
font-weight: 600;
}

#tt-result-comment {
font-size: 13px;
color: #334155;
margin-bottom: 14px;
}

#tt-btn-retry {
padding: 9px 24px;
font-size: 14px;
font-weight: 700;
border: none;
border-radius: 7px;
cursor: pointer;
background: #0284c7;
color: #fff;
transition: background 0.15s;
}

#tt-btn-retry:hover {
background: #0369a1;
}

/* Status message */
#tt-status {
font-size: 13px;
color: #64748b;
text-align: center;
margin-bottom: 10px;
min-height: 18px;
}
</style>

<h2>&#9000; タイピング速度テスト</h2>

<div id="tt-controls">
<div>
<label for="tt-select-diff">難易度：</label>
<select id="tt-select-diff">
<option value="easy">初級</option>
<option value="medium" selected>中級</option>
<option value="hard">上級</option>
</select>
</div>
<div>
<label for="tt-select-time">制限時間：</label>
<select id="tt-select-time">
<option value="30">30秒</option>
<option value="60" selected>60秒</option>
<option value="120">120秒</option>
</select>
</div>
<button id="tt-btn-start">スタート</button>
<button id="tt-btn-reset">リセット</button>
</div>

<div id="tt-timer-bar">
<div id="tt-timer-display">60</div>
<div id="tt-progress-track">
<div id="tt-progress-fill"></div>
</div>
</div>

<div id="tt-text-box" aria-label="タイピングテキスト"></div>

<p id="tt-status">難易度と制限時間を選んで「スタート」を押すか、入力欄に最初の文字を入力してください。</p>

<input
type="text"
id="tt-input"
placeholder="ここに入力してください（入力開始で自動スタート）"
autocomplete="off"
autocorrect="off"
autocapitalize="off"
spellcheck="false"
disabled
/>

<div id="tt-stats">
<div class="tt-stat-card">
<div class="tt-stat-label">WPM</div>
<div class="tt-stat-value tt-wpm" id="tt-s-wpm">0</div>
</div>
<div class="tt-stat-card">
<div class="tt-stat-label">正確率</div>
<div class="tt-stat-value tt-acc" id="tt-s-acc">100%</div>
</div>
<div class="tt-stat-card">
<div class="tt-stat-label">文字数</div>
<div class="tt-stat-value" id="tt-s-chars">0</div>
</div>
<div class="tt-stat-card">
<div class="tt-stat-label">ミス</div>
<div class="tt-stat-value" id="tt-s-errors">0</div>
</div>
<div class="tt-stat-card">
<div class="tt-stat-label">経過時間</div>
<div class="tt-stat-value" id="tt-s-elapsed">0s</div>
</div>
</div>

<div id="tt-result">
<h3>テスト結果</h3>
<div id="tt-result-level"></div>
<div id="tt-result-stats">
<div class="tt-res-item">
<span class="rval" id="tt-r-wpm">0</span>
<span class="rlbl">WPM</span>
</div>
<div class="tt-res-item">
<span class="rval" id="tt-r-acc">0%</span>
<span class="rlbl">正確率</span>
</div>
<div class="tt-res-item">
<span class="rval" id="tt-r-chars">0</span>
<span class="rlbl">総文字数</span>
</div>
<div class="tt-res-item">
<span class="rval" id="tt-r-errors">0</span>
<span class="rlbl">ミス数</span>
</div>
</div>
<p id="tt-result-comment"></p>
<button id="tt-btn-retry">もう一度挑戦</button>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function () {
"use strict";

/* ── Sample texts (English, romaji-input friendly) ── */
var TEXTS = {
easy: [
"the cat sat on the mat and looked at the dog by the big red barn near the old oak tree",
"she has a big blue ball and two small red cars for her little dog to play with every day",
"my dog runs fast and likes to jump over the fence in the yard on hot sunny days in june",
"he can see the sun and the moon at the same time on a clear cold night in the open field",
"we like to eat cake and drink milk at the table with our family on friday night each week",
"the old man has a hat and a bag and he walks to the shop every day to buy bread and eggs"
],
medium: [
"practice makes perfect and consistent effort over time leads to remarkable improvements in skill",
"the quick brown fox jumps over the lazy dog while the sun sets slowly beyond the distant hills",
"reading books every day is one of the most effective ways to expand your vocabulary and knowledge",
"good communication skills are essential in any workplace and help teams collaborate more effectively",
"regular exercise improves both physical and mental health and can increase productivity during work",
"learning to type faster requires daily practice and focus on accuracy before increasing your speed"
],
hard: [
"asynchronous programming paradigms allow developers to write non-blocking code that improves application throughput significantly",
"the implementation of machine learning algorithms requires careful consideration of data preprocessing normalization and feature engineering",
"distributed systems must handle network partitions gracefully while maintaining consistency availability and partition tolerance trade-offs",
"containerization with docker and orchestration via kubernetes enables scalable microservice deployments across heterogeneous cloud infrastructure",
"the cryptographic hash function produces a fixed-length digest from arbitrary input data ensuring integrity verification in blockchain protocols",
"functional programming emphasizes immutability pure functions and declarative composition enabling more predictable and testable software architectures"
]
};

/* ── State ── */
var state = {
phase: "idle",
text: "",
typed: [],
currentIndex: 0,
totalChars: 0,
errors: 0,
startTime: null,
elapsed: 0,
limitSec: 60,
timerInterval: null,
statsInterval: null,
textPoolIndex: 0
};

/* ── DOM refs ── */
function ge(id) { return document.getElementById(id); }
var elTextBox    = ge("tt-text-box");
var elInput      = ge("tt-input");
var elBtnStart   = ge("tt-btn-start");
var elBtnReset   = ge("tt-btn-reset");
var elBtnRetry   = ge("tt-btn-retry");
var elSelectDiff = ge("tt-select-diff");
var elSelectTime = ge("tt-select-time");
var elTimer      = ge("tt-timer-display");
var elFill       = ge("tt-progress-fill");
var elStatus     = ge("tt-status");
var elResult     = ge("tt-result");
var elSWpm       = ge("tt-s-wpm");
var elSAcc       = ge("tt-s-acc");
var elSChars     = ge("tt-s-chars");
var elSErrors    = ge("tt-s-errors");
var elSElapsed   = ge("tt-s-elapsed");
var elRWpm       = ge("tt-r-wpm");
var elRAcc       = ge("tt-r-acc");
var elRChars     = ge("tt-r-chars");
var elRErrors    = ge("tt-r-errors");
var elRLevel     = ge("tt-result-level");
var elRComment   = ge("tt-result-comment");

/* ── Helpers ── */
function pickText(diff) {
var pool = TEXTS[diff];
var idx = state.textPoolIndex % pool.length;
state.textPoolIndex++;
return pool[idx];
}

function calcWpm(chars, elapsedMs) {
if (elapsedMs < 500) return 0;
var minutes = elapsedMs / 60000;
return Math.round((chars / 5) / minutes);
}

function calcAcc(totalTyped, errors) {
if (totalTyped === 0) return 100;
return Math.max(0, Math.round(((totalTyped - errors) / totalTyped) * 100));
}

function levelInfo(wpm) {
if (wpm < 30)  return { label: "初心者",     comment: "焦らず正確さを意識しましょう。毎日練習すれば必ず上達します！" };
if (wpm < 50)  return { label: "一般レベル", comment: "平均的な速さです。正確率を維持しながら速度アップを目指しましょう。" };
if (wpm < 70)  return { label: "上手",       comment: "なかなかの速さです！あと少しでプロレベルに届きます。" };
if (wpm < 100) return { label: "プロレベル", comment: "素晴らしいタイピング力です。多くのプロと同等以上の速さです！" };
return            { label: "エリート",       comment: "驚異的なスピード！トップクラスのタイピスト水準です。" };
}

/* ── Render text display ── */
function renderText() {
var text = state.text;
var html = "";
for (var i = 0; i < text.length; i++) {
var ch = text[i] === " " ? "\u00a0" : text[i];
ch = ch.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;");
if (i < state.currentIndex) {
var t = state.typed[i];
if (t && t.correct) {
html += '<span class="char-correct">' + ch + '</span>';
} else {
html += '<span class="char-wrong">' + ch + '</span>';
}
} else if (i === state.currentIndex) {
html += '<span class="char-current">' + ch + '</span>';
} else {
html += '<span class="char-pending">' + ch + '</span>';
}
}
elTextBox.innerHTML = html;
}

/* ── Update live stats ── */
function updateStats() {
var now = Date.now();
var elapsed = state.startTime ? now - state.startTime : 0;
state.elapsed = elapsed;
var wpm = calcWpm(state.totalChars, elapsed);
var acc = calcAcc(state.totalChars, state.errors);
elSWpm.textContent     = wpm;
elSAcc.textContent     = acc + "%";
elSChars.textContent   = state.totalChars;
elSErrors.textContent  = state.errors;
elSElapsed.textContent = Math.floor(elapsed / 1000) + "s";
}

/* ── Timer tick ── */
function timerTick() {
var now = Date.now();
var elapsed = now - state.startTime;
var remaining = Math.max(0, state.limitSec * 1000 - elapsed);
var remainSec = Math.ceil(remaining / 1000);
var pct = (remaining / (state.limitSec * 1000)) * 100;

elTimer.textContent = remainSec;
elFill.style.width  = pct + "%";

var warn = remainSec <= 10;
if (warn) {
elTimer.classList.add("tt-warning");
elFill.classList.add("tt-warning");
} else {
elTimer.classList.remove("tt-warning");
elFill.classList.remove("tt-warning");
}

if (remaining <= 0) {
finishTest();
}
}

/* ── Initialize / ready state ── */
function initReady() {
var diff = elSelectDiff.value;
state.limitSec     = parseInt(elSelectTime.value, 10);
state.text         = pickText(diff);
state.typed        = [];
state.currentIndex = 0;
state.totalChars   = 0;
state.errors       = 0;
state.startTime    = null;
state.elapsed      = 0;
state.phase        = "ready";

clearInterval(state.timerInterval);
clearInterval(state.statsInterval);

elInput.value       = "";
elInput.disabled    = false;
elInput.placeholder = "ここに入力してください（入力開始で自動スタート）";
elResult.style.display = "none";
elTimer.textContent = state.limitSec;
elTimer.classList.remove("tt-warning");
elFill.style.width  = "100%";
elFill.classList.remove("tt-warning");
elBtnStart.textContent = "スタート";

elSWpm.textContent     = "0";
elSAcc.textContent     = "100%";
elSChars.textContent   = "0";
elSErrors.textContent  = "0";
elSElapsed.textContent = "0s";

elTextBox.classList.add("tt-active");
elStatus.textContent = "入力を開始するとタイマーがスタートします。";
renderText();
elInput.focus();
}

/* ── Start running ── */
function startRunning() {
state.phase     = "running";
state.startTime = Date.now();
elStatus.textContent   = "入力中...";
elBtnStart.textContent = "進行中";

state.timerInterval = setInterval(timerTick, 200);
state.statsInterval = setInterval(updateStats, 300);
}

/* ── Finish ── */
function finishTest() {
if (state.phase === "finished") return;
state.phase = "finished";

clearInterval(state.timerInterval);
clearInterval(state.statsInterval);

elInput.disabled = true;
elTextBox.classList.remove("tt-active");
elTimer.textContent = "0";
elFill.style.width  = "0%";
elStatus.textContent = "テスト終了！";

var elapsed = state.elapsed || (Date.now() - (state.startTime || Date.now()));
var wpm  = calcWpm(state.totalChars, elapsed);
var acc  = calcAcc(state.totalChars, state.errors);
var info = levelInfo(wpm);

elRWpm.textContent    = wpm;
elRAcc.textContent    = acc + "%";
elRChars.textContent  = state.totalChars;
elRErrors.textContent = state.errors;
elRLevel.textContent  = "レベル判定：" + info.label;
elRComment.textContent = info.comment;

elResult.style.display = "block";
elResult.scrollIntoView({ behavior: "smooth", block: "nearest" });

updateStats();
}

/* ── Input handler ── */
elInput.addEventListener("input", function () {
if (state.phase === "idle" || state.phase === "finished") return;

var val = this.value;

/* Auto-start on first keystroke */
if (state.phase === "ready" && val.length > 0) {
startRunning();
}

if (state.phase !== "running") return;

var expected = state.text[state.currentIndex];
if (expected === undefined) return;

var lastChar = val[val.length - 1];

if (lastChar !== undefined) {
var correct = lastChar === expected;
state.typed[state.currentIndex] = { char: lastChar, correct: correct };
state.currentIndex++;
state.totalChars++;
if (!correct) state.errors++;
}

/* Clear input to keep processing char-by-char */
this.value = "";

renderText();
updateStats();

/* If all text consumed, load next passage */
if (state.currentIndex >= state.text.length) {
var diff = elSelectDiff.value;
state.text         = pickText(diff);
state.typed        = [];
state.currentIndex = 0;
renderText();
elStatus.textContent = "次のテキストに進みました。続けて入力してください。";
}
});

/* Prevent paste */
elInput.addEventListener("paste", function (e) {
e.preventDefault();
});

/* ── Button handlers ── */
elBtnStart.addEventListener("click", function () {
initReady();
});

elBtnReset.addEventListener("click", function () {
clearInterval(state.timerInterval);
clearInterval(state.statsInterval);
state.phase = "idle";

elInput.disabled    = true;
elInput.value       = "";
elInput.placeholder = "ここに入力してください（入力開始で自動スタート）";
elResult.style.display = "none";
elTextBox.classList.remove("tt-active");
elTextBox.innerHTML = "";

var limitSec = parseInt(elSelectTime.value, 10);
elTimer.textContent = limitSec;
elTimer.classList.remove("tt-warning");
elFill.style.width  = "100%";
elFill.classList.remove("tt-warning");

elSWpm.textContent     = "0";
elSAcc.textContent     = "100%";
elSChars.textContent   = "0";
elSErrors.textContent  = "0";
elSElapsed.textContent = "0s";
elBtnStart.textContent = "スタート";
elStatus.textContent   = "難易度と制限時間を選んで「スタート」を押すか、入力欄に最初の文字を入力してください。";
});

elBtnRetry.addEventListener("click", function () {
initReady();
});

/* Update timer display when time selector changes in idle/ready */
elSelectTime.addEventListener("change", function () {
if (state.phase === "idle" || state.phase === "ready") {
elTimer.textContent = this.value;
state.limitSec = parseInt(this.value, 10);
}
});

/* ── Init display ── */
elTimer.textContent  = elSelectTime.value;
elStatus.textContent = "難易度と制限時間を選んで「スタート」を押すか、入力欄に最初の文字を入力してください。";

})();
</script>

</div>

---

> コード行数をカウント → [行数カウンター](/ja/tools/line-counter/)
> コードを整形 → [コード圧縮ツール](/ja/tools/code-minifier/)
> テキストの差分を確認 → [テキスト差分比較ツール](/ja/tools/text-diff-checker/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [AI英語学習おすすめアプリ2026年版【比較ランキング・無料あり】](/ja/posts/ai-eigo-gakushu-osusume-app-2026/)
- [AI活用の英語学習法おすすめ5選【2026年版・独学で話せるようになる方法】](/ja/posts/ai-英語学習-おすすめ/)
