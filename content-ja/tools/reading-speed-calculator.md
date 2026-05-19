---
title: "読書速度テスト"
date: 2025-11-01
description: "無料の読書速度テスト＆計算ツール。WPMを測定、本や記事の読了時間を推定。理解度チェック付き、会員登録不要。"
categories: ["無料ツール"]
slug: "reading-speed-calculator"
ShowToc: false
cover:
  image: "/images/covers/reading-speed-calculator-ja.png"
  alt: "読書速度テスト"
---

<div id="rs-app">
<style>
#rs-app {
font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
max-width: 720px;
margin: 0 auto;
color: #1e293b;
line-height: 1.6;
}
#rs-app * { box-sizing: border-box; }

/* Tabs */
#rs-app .rs-tabs {
display: flex;
gap: 4px;
margin-bottom: 24px;
border-bottom: 2px solid #cbd5e1;
}
#rs-app .rs-tab-btn {
padding: 10px 20px;
border: none;
background: none;
font-size: 15px;
font-weight: 600;
color: #64748b;
cursor: pointer;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
border-radius: 6px 6px 0 0;
transition: color 0.18s, border-color 0.18s, background 0.18s;
}
#rs-app .rs-tab-btn:hover {
color: #0f172a;
background: #f1f5f9;
}
#rs-app .rs-tab-btn.active {
color: #0284c7;
border-bottom-color: #0284c7;
background: #f0f9ff;
}

/* Tab panels */
#rs-app .rs-panel { display: none; }
#rs-app .rs-panel.active { display: block; }

/* Cards */
#rs-app .rs-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 20px 22px;
margin-bottom: 18px;
}

/* Passage selector */
#rs-app .rs-passage-select-wrap {
margin-bottom: 14px;
display: flex;
align-items: center;
gap: 10px;
flex-wrap: wrap;
}
#rs-app .rs-passage-select-wrap label {
font-size: 14px;
font-weight: 600;
color: #475569;
}
#rs-app .rs-select {
padding: 7px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
background: #fff;
color: #1e293b;
cursor: pointer;
}
#rs-app .rs-select:focus { outline: 2px solid #0284c7; border-color: #0284c7; }

/* Passage box */
#rs-app .rs-passage-box {
background: #fff;
border: 1.5px solid #cbd5e1;
border-radius: 9px;
padding: 18px 20px;
font-size: 15px;
line-height: 1.85;
color: #334155;
margin-bottom: 16px;
min-height: 120px;
user-select: none;
position: relative;
filter: blur(4px);
pointer-events: none;
transition: filter 0.3s;
}
#rs-app .rs-passage-box.revealed {
filter: none;
pointer-events: auto;
user-select: text;
}
#rs-app .rs-passage-overlay {
position: absolute;
inset: 0;
display: flex;
align-items: center;
justify-content: center;
background: rgba(248,250,252,0.55);
border-radius: 9px;
font-size: 14px;
color: #64748b;
font-weight: 600;
pointer-events: none;
}

/* Timer */
#rs-app .rs-timer-row {
display: flex;
align-items: center;
gap: 14px;
flex-wrap: wrap;
margin-bottom: 12px;
}
#rs-app .rs-timer-display {
font-size: 28px;
font-weight: 700;
font-variant-numeric: tabular-nums;
color: #0f172a;
min-width: 90px;
}
#rs-app .rs-badge {
display: inline-block;
padding: 3px 10px;
border-radius: 20px;
font-size: 12px;
font-weight: 700;
background: #e2e8f0;
color: #475569;
}
#rs-app .rs-badge.running { background: #dcfce7; color: #15803d; }

/* Buttons */
#rs-app .rs-btn {
padding: 10px 22px;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: background 0.18s, transform 0.1s, box-shadow 0.18s;
}
#rs-app .rs-btn:active { transform: scale(0.97); }
#rs-app .rs-btn-primary {
background: #0284c7;
color: #fff;
}
#rs-app .rs-btn-primary:hover { background: #0369a1; box-shadow: 0 2px 8px rgba(2,132,199,0.18); }
#rs-app .rs-btn-primary:disabled { background: #94a3b8; cursor: not-allowed; }
#rs-app .rs-btn-success {
background: #16a34a;
color: #fff;
}
#rs-app .rs-btn-success:hover { background: #15803d; }
#rs-app .rs-btn-success:disabled { background: #94a3b8; cursor: not-allowed; }
#rs-app .rs-btn-ghost {
background: #f1f5f9;
color: #475569;
border: 1.5px solid #cbd5e1;
}
#rs-app .rs-btn-ghost:hover { background: #e2e8f0; }

/* Result box */
#rs-app .rs-result-box {
background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
border: 1.5px solid #bae6fd;
border-radius: 10px;
padding: 16px 20px;
margin-bottom: 16px;
display: none;
}
#rs-app .rs-result-box.visible { display: block; }
#rs-app .rs-result-grid {
display: flex;
gap: 20px;
flex-wrap: wrap;
}
#rs-app .rs-result-item {
text-align: center;
min-width: 100px;
}
#rs-app .rs-result-num {
font-size: 32px;
font-weight: 800;
color: #0284c7;
}
#rs-app .rs-result-label {
font-size: 12px;
color: #475569;
margin-top: 2px;
}
#rs-app .rs-wpm-comment {
margin-top: 10px;
font-size: 14px;
color: #0c4a6e;
font-weight: 500;
}

/* Quiz */
#rs-app .rs-quiz-section { display: none; }
#rs-app .rs-quiz-section.visible { display: block; }
#rs-app .rs-quiz-title {
font-size: 15px;
font-weight: 700;
color: #1e293b;
margin-bottom: 12px;
}
#rs-app .rs-question {
margin-bottom: 16px;
}
#rs-app .rs-question p {
font-size: 14px;
font-weight: 600;
color: #334155;
margin-bottom: 8px;
}
#rs-app .rs-options {
display: flex;
flex-direction: column;
gap: 7px;
}
#rs-app .rs-option-label {
display: flex;
align-items: center;
gap: 9px;
padding: 9px 14px;
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
cursor: pointer;
font-size: 14px;
color: #334155;
transition: border-color 0.15s, background 0.15s;
}
#rs-app .rs-option-label:hover { border-color: #0284c7; background: #f0f9ff; }
#rs-app .rs-option-label input { accent-color: #0284c7; }
#rs-app .rs-option-label.correct { border-color: #16a34a; background: #f0fdf4; color: #15803d; }
#rs-app .rs-option-label.incorrect { border-color: #dc2626; background: #fef2f2; color: #b91c1c; }

/* Tab 2 - Reading time calculator */
#rs-app .rs-input-group {
margin-bottom: 16px;
}
#rs-app .rs-input-group label {
display: block;
font-size: 13px;
font-weight: 600;
color: #475569;
margin-bottom: 6px;
}
#rs-app .rs-input {
width: 100%;
padding: 9px 13px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 14px;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
}
#rs-app .rs-input:focus { outline: 2px solid #0284c7; border-color: #0284c7; }
#rs-app textarea.rs-input {
min-height: 110px;
resize: vertical;
font-family: inherit;
}
#rs-app .rs-or-divider {
text-align: center;
font-size: 13px;
color: #94a3b8;
font-weight: 600;
margin: 10px 0;
}
#rs-app .rs-preset-row {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 8px;
}
#rs-app .rs-preset-btn {
padding: 6px 13px;
background: #f1f5f9;
border: 1.5px solid #cbd5e1;
border-radius: 20px;
font-size: 13px;
color: #475569;
cursor: pointer;
font-weight: 600;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}
#rs-app .rs-preset-btn:hover {
background: #e0f2fe;
border-color: #7dd3fc;
color: #0284c7;
}
#rs-app .rs-wpm-row {
display: flex;
align-items: center;
gap: 12px;
flex-wrap: wrap;
}
#rs-app .rs-wpm-row input[type=range] {
flex: 1;
min-width: 120px;
accent-color: #0284c7;
}
#rs-app .rs-wpm-val {
font-size: 16px;
font-weight: 700;
color: #0284c7;
min-width: 48px;
}
#rs-app .rs-time-result {
background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
border: 1.5px solid #bae6fd;
border-radius: 10px;
padding: 18px 22px;
text-align: center;
display: none;
}
#rs-app .rs-time-result.visible { display: block; }
#rs-app .rs-time-big {
font-size: 40px;
font-weight: 800;
color: #0284c7;
}
#rs-app .rs-time-sub {
font-size: 14px;
color: #475569;
margin-top: 4px;
}

/* Chart section */
#rs-app .rs-chart-section {
margin-top: 10px;
}
#rs-app .rs-chart-title {
font-size: 15px;
font-weight: 700;
color: #1e293b;
margin-bottom: 12px;
}
#rs-app canvas#rs-bar-chart {
width: 100% !important;
display: block;
}

/* Cross-links */
#rs-app .rs-crosslinks {
margin-top: 28px;
padding: 16px 18px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
font-size: 14px;
color: #475569;
}
#rs-app .rs-crosslinks p { margin: 5px 0; }
#rs-app .rs-crosslinks a { color: #0284c7; text-decoration: none; font-weight: 600; }
#rs-app .rs-crosslinks a:hover { text-decoration: underline; }
</style>

<!-- ========== TABS ========== -->
<div class="rs-tabs" role="tablist">
<button class="rs-tab-btn active" data-tab="test" role="tab" aria-selected="true" onclick="rsShowTab('test',this)">読書速度テスト</button>
<button class="rs-tab-btn" data-tab="calc" role="tab" aria-selected="false" onclick="rsShowTab('calc',this)">読了時間計算</button>
</div>

<!-- ========== TAB 1: 読書速度テスト ========== -->
<div id="rs-panel-test" class="rs-panel active">

<div class="rs-card">
<div class="rs-passage-select-wrap">
<label for="rs-difficulty">難易度：</label>
<select id="rs-difficulty" class="rs-select" onchange="rsLoadPassage()">
<option value="easy">やさしい</option>
<option value="normal" selected>ふつう</option>
<option value="hard">むずかしい</option>
</select>
<span id="rs-word-count-label" style="font-size:13px;color:#94a3b8;"></span>
</div>

<div style="position:relative;">
<div id="rs-passage-box" class="rs-passage-box">
<!-- text injected by JS -->
</div>
<div id="rs-passage-overlay" class="rs-passage-overlay">「読み始める」を押すとテキストが表示されます</div>
</div>

<div class="rs-timer-row">
<div class="rs-timer-display" id="rs-timer-display">0:00.0</div>
<span class="rs-badge" id="rs-status-badge">待機中</span>
</div>
<div style="display:flex;gap:10px;flex-wrap:wrap;">
<button class="rs-btn rs-btn-primary" id="rs-start-btn" onclick="rsStart()">読み始める</button>
<button class="rs-btn rs-btn-success" id="rs-done-btn" onclick="rsDone()" disabled>読了</button>
<button class="rs-btn rs-btn-ghost" onclick="rsReset()">リセット</button>
</div>
</div>

<!-- Result -->
<div class="rs-result-box" id="rs-result-box">
<div class="rs-result-grid">
<div class="rs-result-item">
<div class="rs-result-num" id="rs-wpm-val">—</div>
<div class="rs-result-label">WPM（1分あたりの語数）</div>
</div>
<div class="rs-result-item">
<div class="rs-result-num" id="rs-time-val">—</div>
<div class="rs-result-label">読書時間（秒）</div>
</div>
<div class="rs-result-item">
<div class="rs-result-num" id="rs-comp-val">—</div>
<div class="rs-result-label">理解度</div>
</div>
</div>
<div class="rs-wpm-comment" id="rs-wpm-comment"></div>
</div>

<!-- Quiz -->
<div class="rs-quiz-section" id="rs-quiz-section">
<div class="rs-card">
<div class="rs-quiz-title">理解度テスト（3問）</div>
<div id="rs-quiz-questions"></div>
<button class="rs-btn rs-btn-primary" onclick="rsCheckAnswers()" id="rs-check-btn" style="margin-top:8px;">答え合わせ</button>
</div>
</div>

<!-- Speed comparison chart -->
<div class="rs-card rs-chart-section" id="rs-chart-section" style="display:none;">
<div class="rs-chart-title">あなたの速度 vs 平均的な読者</div>
<canvas id="rs-bar-chart" height="160"></canvas>
</div>
</div>

<!-- ========== TAB 2: 読了時間計算 ========== -->
<div id="rs-panel-calc" class="rs-panel">

<div class="rs-card">
<div class="rs-input-group">
<label for="rs-char-count">文字数を入力</label>
<input type="number" id="rs-char-count" class="rs-input" placeholder="例: 80000" min="1" oninput="rsCalcTime()" />
</div>

<div class="rs-input-group">
<label>プリセット</label>
<div class="rs-preset-row">
<button class="rs-preset-btn" onclick="rsSetPreset(80000,'小説（8万字）')">小説（8万字）</button>
<button class="rs-preset-btn" onclick="rsSetPreset(1500,'ブログ記事（1,500字）')">ブログ記事（1,500字）</button>
<button class="rs-preset-btn" onclick="rsSetPreset(8000,'論文（8,000字）')">論文（8,000字）</button>
<button class="rs-preset-btn" onclick="rsSetPreset(5000,'教科書章（5,000字）')">教科書章（5,000字）</button>
</div>
</div>

<div class="rs-or-divider">— または —</div>

<div class="rs-input-group">
<label for="rs-paste-text">テキストを貼り付け（自動カウント）</label>
<textarea id="rs-paste-text" class="rs-input" placeholder="ここにテキストを貼り付けると文字数を自動カウントします..." oninput="rsCountPaste()"></textarea>
<div style="font-size:12px;color:#94a3b8;margin-top:4px;" id="rs-paste-count"></div>
</div>

<div class="rs-input-group">
<label>読書速度（WPM）</label>
<div class="rs-wpm-row">
<input type="range" id="rs-wpm-slider" min="100" max="800" value="250" oninput="rsUpdateWpm();rsCalcTime();" />
<div class="rs-wpm-val"><span id="rs-wpm-display">250</span> WPM</div>
</div>
<div style="display:flex;justify-content:space-between;font-size:11px;color:#94a3b8;margin-top:2px;">
<span>100（遅い）</span><span>250（平均）</span><span>400（速い）</span><span>800（速読）</span>
</div>
</div>

<button class="rs-btn rs-btn-primary" onclick="rsCalcTime()" style="width:100%;margin-top:4px;">読了時間を計算</button>
</div>

<div class="rs-time-result" id="rs-time-result">
<div style="font-size:13px;color:#475569;margin-bottom:4px;" id="rs-time-label">読了時間（推定）</div>
<div class="rs-time-big" id="rs-time-display">—</div>
<div class="rs-time-sub" id="rs-time-detail"></div>
</div>

<!-- Chart in tab 2 always visible -->
<div class="rs-card" style="margin-top:18px;">
<div class="rs-chart-title">読書速度の目安（WPM比較）</div>
<canvas id="rs-bar-chart-2" height="180"></canvas>
</div>
</div>

<!-- ========== freee CTA ========== -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<!-- ========== Cross-links ========== -->
<div class="rs-crosslinks">
<p>タイピング速度を測定 → <a href="/ja/tools/typing-speed-test/">タイピング速度テスト</a></p>
<p>テキスト行数をカウント → <a href="/ja/tools/line-counter/">行数カウンター</a></p>
<p>ダミーテキストを生成 → <a href="/ja/tools/lorem-ipsum-generator/">Lorem Ipsumジェネレーター</a></p>
</div>

<!-- ========== JAVASCRIPT ========== -->
<script>
(function() {
'use strict';

/* ---- Passages ---- */
var PASSAGES = {
easy: {
label: 'やさしい',
text: "Reading every day is one of the best habits you can build. It helps you learn new ideas, improve your vocabulary, and reduce stress. Even fifteen minutes of reading before bed can make a big difference over time. Many successful people read for at least an hour each day. Books allow you to explore different worlds, understand other people's experiences, and grow as a person. Whether you enjoy fiction, history, or self-help, there is always a book that can teach you something new. Start small, stay consistent, and you will be surprised how much you can learn in just one year of regular reading.",
words: 105,
questions: [
{
q: "毎日の読書のメリットとして挙げられていないものはどれですか？",
options: ["語彙を増やす", "ストレスを減らす", "体力を高める", "新しいアイデアを学ぶ"],
answer: 2
},
{
q: "多くの成功者は1日何時間読書をすると述べられていますか？",
options: ["30分", "少なくとも1時間", "2時間以上", "就寝前15分"],
answer: 1
},
{
q: "本を読むことで何を理解できると述べられていますか？",
options: ["最新のニュース", "コンピュータのプログラミング", "他の人々の経験", "自分の夢"],
answer: 2
}
]
},
normal: {
label: 'ふつう',
text: "Productivity is not about doing more things in less time — it is about doing the right things efficiently. Research suggests that the human brain can sustain deep focus for approximately 90 minutes before it needs a recovery period. This is why techniques like the Pomodoro method, which breaks work into focused intervals with short breaks, can be highly effective. Another key factor is eliminating distractions: studies have shown that it takes an average of 23 minutes to fully regain concentration after being interrupted. Prioritizing tasks using frameworks such as the Eisenhower Matrix — which categorizes work by urgency and importance — helps ensure that your energy is directed toward high-impact activities rather than urgent but trivial ones. Combining focused work sessions with intentional rest is the foundation of sustainable high performance.",
words: 128,
questions: [
{
q: "人間の脳が深い集中を維持できるのはおよそどのくらいですか？",
options: ["30分", "60分", "90分", "120分"],
answer: 2
},
{
q: "中断後に完全に集中力を取り戻すまで平均何分かかると述べられていますか？",
options: ["5分", "10分", "15分", "23分"],
answer: 3
},
{
q: "アイゼンハワーマトリックスはタスクを何で分類しますか？",
options: ["難易度と所要時間", "緊急性と重要性", "コストと効果", "担当者と期限"],
answer: 1
}
]
},
hard: {
label: 'むずかしい',
text: "Cognitive load theory, originally proposed by John Sweller in the late 1980s, posits that the human working memory has a finite capacity and that instructional design must account for this limitation to optimize learning outcomes. The theory distinguishes between three types of cognitive load: intrinsic load, which arises from the inherent complexity of the material itself; extraneous load, which is imposed by poorly designed instruction or irrelevant information; and germane load, which refers to the mental effort directed toward schema formation and automation. Effective learning environments seek to minimize extraneous load while managing intrinsic load through techniques such as segmentation and sequencing, thereby freeing cognitive resources for germane processing. Recent extensions of the theory have integrated findings from neuroscience, particularly regarding the role of long-term memory in augmenting working memory capacity through the retrieval of well-established schemas, suggesting that expertise fundamentally alters the architecture of cognitive processing.",
words: 148,
questions: [
{
q: "認知負荷理論を提唱したのは誰ですか？",
options: ["Noam Chomsky", "John Sweller", "Albert Bandura", "Jean Piaget"],
answer: 1
},
{
q: "「外在的負荷（Extraneous load）」とは何を指しますか？",
options: ["素材固有の複雑さから生じる負荷", "スキーマ形成に向けられた精神的努力", "不適切な教授設計や無関係な情報による負荷", "長期記憶の検索コスト"],
answer: 2
},
{
q: "最近の理論拡張で長期記憶はどのような役割を果たすと述べられていますか？",
options: ["外在的負荷を増加させる", "作業記憶容量を補完する", "内在的負荷を排除する", "スキーマの自動化を妨げる"],
answer: 1
}
]
}
};

var currentPassage = PASSAGES.normal;
var startTime = null;
var endTime = null;
var timerInterval = null;
var timerRunning = false;
var finalWPM = 0;

/* ---- Init ---- */
rsLoadPassage();
rsDrawComparisonChart('rs-bar-chart-2', null);

function rsLoadPassage() {
var diff = document.getElementById('rs-difficulty').value;
currentPassage = PASSAGES[diff];
var box = document.getElementById('rs-passage-box');
box.textContent = currentPassage.text;
box.classList.remove('revealed');
document.getElementById('rs-passage-overlay').style.display = 'flex';
document.getElementById('rs-word-count-label').textContent = '(' + currentPassage.words + ' 語)';
rsReset();
}
window.rsLoadPassage = rsLoadPassage;

function rsStart() {
if (timerRunning) return;
timerRunning = true;
startTime = performance.now();
document.getElementById('rs-start-btn').disabled = true;
document.getElementById('rs-done-btn').disabled = false;
document.getElementById('rs-status-badge').textContent = '計測中';
document.getElementById('rs-status-badge').className = 'rs-badge running';
// Reveal passage
document.getElementById('rs-passage-box').classList.add('revealed');
document.getElementById('rs-passage-overlay').style.display = 'none';
timerInterval = setInterval(updateTimer, 100);
}
window.rsStart = rsStart;

function updateTimer() {
var elapsed = (performance.now() - startTime) / 1000;
var mins = Math.floor(elapsed / 60);
var secs = (elapsed % 60).toFixed(1);
if (secs < 10) secs = '0' + secs;
document.getElementById('rs-timer-display').textContent = mins + ':' + secs;
}

function rsDone() {
if (!timerRunning) return;
endTime = performance.now();
clearInterval(timerInterval);
timerRunning = false;
document.getElementById('rs-done-btn').disabled = true;
document.getElementById('rs-status-badge').textContent = '完了';
document.getElementById('rs-status-badge').className = 'rs-badge';

var elapsedSec = (endTime - startTime) / 1000;
finalWPM = Math.round((currentPassage.words / elapsedSec) * 60);

document.getElementById('rs-wpm-val').textContent = finalWPM;
document.getElementById('rs-time-val').textContent = elapsedSec.toFixed(1) + '秒';
document.getElementById('rs-comp-val').textContent = '採点中...';
document.getElementById('rs-result-box').className = 'rs-result-box visible';
document.getElementById('rs-wpm-comment').textContent = wpmComment(finalWPM);

buildQuiz();
document.getElementById('rs-quiz-section').className = 'rs-quiz-section visible';
document.getElementById('rs-chart-section').style.display = 'none';
}
window.rsDone = rsDone;

function rsReset() {
clearInterval(timerInterval);
timerRunning = false;
startTime = null;
endTime = null;
finalWPM = 0;
document.getElementById('rs-timer-display').textContent = '0:00.0';
document.getElementById('rs-status-badge').textContent = '待機中';
document.getElementById('rs-status-badge').className = 'rs-badge';
document.getElementById('rs-start-btn').disabled = false;
document.getElementById('rs-done-btn').disabled = true;
document.getElementById('rs-result-box').className = 'rs-result-box';
document.getElementById('rs-quiz-section').className = 'rs-quiz-section';
document.getElementById('rs-chart-section').style.display = 'none';
document.getElementById('rs-quiz-questions').innerHTML = '';
document.getElementById('rs-passage-box').classList.remove('revealed');
document.getElementById('rs-passage-overlay').style.display = 'flex';
}
window.rsReset = rsReset;

function wpmComment(wpm) {
if (wpm < 150) return '読書速度：ゆっくり（平均以下）。音読せず、目で文字を追う練習をしましょう。';
if (wpm < 250) return '読書速度：やや遅い（平均的）。毎日の読書習慣でさらに速くなれます。';
if (wpm < 350) return '読書速度：標準（一般的な成人の平均レベル）。良いペースです！';
if (wpm < 500) return '読書速度：速い！上位20%の読者です。続けて練習しましょう。';
return '読書速度：非常に速い！速読レベルです。理解度も高く維持できていますか？';
}

/* ---- Quiz ---- */
function buildQuiz() {
var qs = currentPassage.questions;
var html = '';
qs.forEach(function(q, i) {
html += '<div class="rs-question" id="rs-q' + i + '">';
html += '<p>Q' + (i+1) + '. ' + q.q + '</p>';
html += '<div class="rs-options">';
q.options.forEach(function(opt, j) {
html += '<label class="rs-option-label" id="rs-opt-' + i + '-' + j + '">';
html += '<input type="radio" name="rsq' + i + '" value="' + j + '"> ' + opt;
html += '</label>';
});
html += '</div></div>';
});
document.getElementById('rs-quiz-questions').innerHTML = html;
document.getElementById('rs-check-btn').style.display = 'inline-block';
}

function rsCheckAnswers() {
var qs = currentPassage.questions;
var correct = 0;
qs.forEach(function(q, i) {
var sel = document.querySelector('input[name="rsq' + i + '"]:checked');
var chosen = sel ? parseInt(sel.value) : -1;
q.options.forEach(function(_, j) {
var lbl = document.getElementById('rs-opt-' + i + '-' + j);
lbl.classList.remove('correct','incorrect');
if (j === q.answer) lbl.classList.add('correct');
else if (j === chosen && chosen !== q.answer) lbl.classList.add('incorrect');
});
if (chosen === q.answer) correct++;
// disable radios
document.querySelectorAll('input[name="rsq' + i + '"]').forEach(function(r){ r.disabled = true; });
});
var pct = Math.round((correct / qs.length) * 100);
document.getElementById('rs-comp-val').textContent = pct + '%（' + correct + '/' + qs.length + '問）';
document.getElementById('rs-check-btn').style.display = 'none';
// Show chart
document.getElementById('rs-chart-section').style.display = 'block';
rsDrawComparisonChart('rs-bar-chart', finalWPM);
}
window.rsCheckAnswers = rsCheckAnswers;

/* ---- Canvas Bar Chart ---- */
function rsDrawComparisonChart(canvasId, userWpm) {
var canvas = document.getElementById(canvasId);
if (!canvas) return;
var ctx = canvas.getContext('2d');
var dpr = window.devicePixelRatio || 1;
var W = canvas.parentElement.clientWidth || 600;
var H = parseInt(canvas.getAttribute('height')) || 160;
canvas.width = W * dpr;
canvas.height = H * dpr;
canvas.style.width = W + 'px';
canvas.style.height = H + 'px';
ctx.scale(dpr, dpr);

var bars = [
{ label: 'ゆっくり', wpm: 120, color: '#94a3b8' },
{ label: '平均', wpm: 250, color: '#60a5fa' },
{ label: '速い', wpm: 400, color: '#34d399' },
{ label: '速読', wpm: 700, color: '#a78bfa' }
];
if (userWpm && userWpm > 0) {
bars.push({ label: 'あなた', wpm: userWpm, color: '#f97316', highlight: true });
}

var maxWpm = Math.max(800, userWpm ? userWpm + 100 : 800);
var paddingLeft = 70;
var paddingRight = 20;
var paddingTop = 16;
var paddingBottom = 14;
var barAreaH = H - paddingTop - paddingBottom;
var barH = Math.min(28, Math.floor(barAreaH / bars.length) - 6);
var gap = Math.floor(barAreaH / bars.length);

ctx.clearRect(0, 0, W, H);
ctx.font = '12px sans-serif';

bars.forEach(function(bar, i) {
var y = paddingTop + i * gap + (gap - barH) / 2;
var barW = ((bar.wpm / maxWpm) * (W - paddingLeft - paddingRight));

// label
ctx.fillStyle = '#475569';
ctx.textAlign = 'right';
ctx.fillText(bar.label, paddingLeft - 6, y + barH / 2 + 4);

// bar bg
ctx.fillStyle = '#f1f5f9';
ctx.beginPath();
ctx.roundRect(paddingLeft, y, W - paddingLeft - paddingRight, barH, 4);
ctx.fill();

// bar fill
ctx.fillStyle = bar.highlight ? bar.color : bar.color;
if (bar.highlight) {
ctx.shadowColor = bar.color;
ctx.shadowBlur = 6;
}
ctx.beginPath();
ctx.roundRect(paddingLeft, y, barW, barH, 4);
ctx.fill();
ctx.shadowBlur = 0;

// wpm label
ctx.fillStyle = bar.highlight ? '#c2410c' : '#1e293b';
ctx.textAlign = 'left';
ctx.font = bar.highlight ? 'bold 12px sans-serif' : '12px sans-serif';
ctx.fillText(bar.wpm + ' WPM', paddingLeft + barW + 5, y + barH / 2 + 4);
});
}

/* ---- Tab switching ---- */
window.rsShowTab = function(tab, btn) {
document.querySelectorAll('#rs-app .rs-tab-btn').forEach(function(b){ b.classList.remove('active'); b.setAttribute('aria-selected','false'); });
document.querySelectorAll('#rs-app .rs-panel').forEach(function(p){ p.classList.remove('active'); });
btn.classList.add('active');
btn.setAttribute('aria-selected','true');
document.getElementById('rs-panel-' + tab).classList.add('active');
if (tab === 'calc') {
setTimeout(function(){ rsDrawComparisonChart('rs-bar-chart-2', null); }, 50);
}
};

/* ---- Tab 2: Reading time calculator ---- */
window.rsUpdateWpm = function() {
document.getElementById('rs-wpm-display').textContent = document.getElementById('rs-wpm-slider').value;
};

window.rsSetPreset = function(chars, label) {
document.getElementById('rs-char-count').value = chars;
document.getElementById('rs-paste-text').value = '';
document.getElementById('rs-paste-count').textContent = '';
rsCalcTime(label);
};

window.rsCountPaste = function() {
var text = document.getElementById('rs-paste-text').value;
var count = text.length;
document.getElementById('rs-paste-count').textContent = count > 0 ? count + ' 文字' : '';
document.getElementById('rs-char-count').value = count > 0 ? count : '';
if (count > 0) rsCalcTime();
};

window.rsCalcTime = function(presetLabel) {
var chars = parseInt(document.getElementById('rs-char-count').value);
var wpm = parseInt(document.getElementById('rs-wpm-slider').value);
if (!chars || chars <= 0 || !wpm || wpm <= 0) {
document.getElementById('rs-time-result').className = 'rs-time-result';
return;
}
// Japanese: approx 1 word ≈ 2 chars (reading speed in chars/min = wpm * 2 for JP)
// Use chars-based: minutes = chars / (wpm * 2)
var totalMinutes = chars / (wpm * 2);
var hours = Math.floor(totalMinutes / 60);
var mins = Math.round(totalMinutes % 60);
var display = '';
if (hours > 0) display = hours + '時間 ' + mins + '分';
else if (mins < 1) display = Math.round(totalMinutes * 60) + '秒';
else display = mins + '分';

var labelEl = document.getElementById('rs-time-label');
labelEl.textContent = presetLabel ? presetLabel + ' の読了時間（推定）' : chars.toLocaleString() + '文字 の読了時間（推定）';
document.getElementById('rs-time-display').textContent = display;
var detail = '文字数: ' + chars.toLocaleString() + '　読書速度: ' + wpm + ' WPM';
document.getElementById('rs-time-detail').textContent = detail;
document.getElementById('rs-time-result').className = 'rs-time-result visible';
};

// Fix roundRect for older browsers
if (!CanvasRenderingContext2D.prototype.roundRect) {
CanvasRenderingContext2D.prototype.roundRect = function(x, y, w, h, r) {
if (w < 2*r) r = w/2;
if (h < 2*r) r = h/2;
this.beginPath();
this.moveTo(x+r, y);
this.arcTo(x+w, y, x+w, y+h, r);
this.arcTo(x+w, y+h, x, y+h, r);
this.arcTo(x, y+h, x, y, r);
this.arcTo(x, y, x+w, y, r);
this.closePath();
return this;
};
}

// Redraw chart on resize
window.addEventListener('resize', function() {
var active = document.querySelector('#rs-app .rs-panel.active');
if (!active) return;
if (active.id === 'rs-panel-test' && document.getElementById('rs-chart-section').style.display !== 'none') {
rsDrawComparisonChart('rs-bar-chart', finalWPM);
}
if (active.id === 'rs-panel-calc') {
rsDrawComparisonChart('rs-bar-chart-2', null);
}
});

})();
</script>
</div>

> タイピング速度を測定 → [タイピング速度テスト](/ja/tools/typing-speed-test/)
> テキスト行数をカウント → [行数カウンター](/ja/tools/line-counter/)
> ダミーテキストを生成 → [Lorem Ipsumジェネレーター](/ja/tools/lorem-ipsum-generator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [AI英語学習おすすめアプリ2026年版【比較ランキング・無料あり】](/ja/posts/ai-eigo-gakushu-osusume-app-2026/)
- [AI活用の英語学習法おすすめ5選【2026年版・独学で話せるようになる方法】](/ja/posts/ai-英語学習-おすすめ/)
- [オンライン英会話 おすすめ2026年版！料金・講師・教材で比較](/ja/posts/online-eikaiwa-osusume-2026/)
