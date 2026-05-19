---
title: "フラッシュカードメーカー"
date: 2025-08-23
description: "無料のフラッシュカード作成ツール。単語帳をブラウザで作成・学習・復習。間隔反復学習・CSV取込対応、会員登録不要。"
categories: ["無料ツール"]
slug: "flashcard-maker"
ShowToc: false
cover:
  image: "/images/covers/flashcard-maker-ja.png"
  alt: "フラッシュカードメーカー"
---

<div id="fc-app">
<style>
#fc-app {
font-family: 'Helvetica Neue', Arial, 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', Meiryo, sans-serif;
max-width: 720px;
margin: 0 auto;
color: #1e293b;
}
#fc-app * {
box-sizing: border-box;
}
#fc-app h2 {
font-size: 1.25rem;
font-weight: 700;
margin: 0 0 16px 0;
color: #0f172a;
}
#fc-app .fc-tabs {
display: flex;
gap: 4px;
margin-bottom: 20px;
background: #f1f5f9;
border-radius: 10px;
padding: 4px;
}
#fc-app .fc-tab {
flex: 1;
padding: 10px 8px;
border: none;
background: transparent;
border-radius: 7px;
font-size: 14px;
font-weight: 600;
color: #64748b;
cursor: pointer;
transition: all 0.18s;
}
#fc-app .fc-tab.active {
background: #fff;
color: #0f172a;
box-shadow: 0 1px 4px rgba(0,0,0,0.10);
}
#fc-app .fc-tab:hover:not(.active) {
color: #334155;
background: rgba(255,255,255,0.5);
}
#fc-app .fc-panel {
display: none;
}
#fc-app .fc-panel.active {
display: block;
}

/* --- 作成モード --- */
#fc-app .fc-form {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 18px;
margin-bottom: 18px;
}
#fc-app .fc-form-row {
display: flex;
gap: 10px;
margin-bottom: 10px;
}
#fc-app .fc-form-row label {
display: block;
font-size: 12px;
font-weight: 700;
color: #475569;
margin-bottom: 4px;
letter-spacing: 0.03em;
}
#fc-app .fc-form-row .fc-field {
flex: 1;
}
#fc-app .fc-input {
width: 100%;
padding: 10px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 15px;
color: #0f172a;
background: #fff;
transition: border-color 0.15s;
resize: vertical;
min-height: 42px;
}
#fc-app .fc-input:focus {
outline: none;
border-color: #3b82f6;
box-shadow: 0 0 0 3px rgba(59,130,246,0.12);
}
#fc-app .fc-btn {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 10px 18px;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: all 0.15s;
white-space: nowrap;
}
#fc-app .fc-btn-primary {
background: #3b82f6;
color: #fff;
}
#fc-app .fc-btn-primary:hover {
background: #2563eb;
}
#fc-app .fc-btn-secondary {
background: #e2e8f0;
color: #334155;
}
#fc-app .fc-btn-secondary:hover {
background: #cbd5e1;
}
#fc-app .fc-btn-danger {
background: #fee2e2;
color: #dc2626;
}
#fc-app .fc-btn-danger:hover {
background: #fecaca;
}
#fc-app .fc-btn-success {
background: #dcfce7;
color: #16a34a;
}
#fc-app .fc-btn-success:hover {
background: #bbf7d0;
}
#fc-app .fc-btn-sm {
padding: 5px 11px;
font-size: 12px;
border-radius: 6px;
}
#fc-app .fc-form-actions {
display: flex;
gap: 8px;
flex-wrap: wrap;
}
#fc-app .fc-csv-row {
margin-top: 10px;
padding-top: 10px;
border-top: 1px solid #e2e8f0;
display: flex;
gap: 8px;
align-items: center;
flex-wrap: wrap;
}
#fc-app .fc-csv-label {
font-size: 12px;
color: #64748b;
font-weight: 600;
}
#fc-app .fc-file-input {
display: none;
}
#fc-app .fc-card-list {
display: flex;
flex-direction: column;
gap: 8px;
}
#fc-app .fc-card-item {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 12px 14px;
display: flex;
gap: 12px;
align-items: flex-start;
}
#fc-app .fc-card-item.editing {
border-color: #3b82f6;
background: #eff6ff;
}
#fc-app .fc-card-idx {
font-size: 12px;
font-weight: 700;
color: #94a3b8;
min-width: 22px;
padding-top: 2px;
}
#fc-app .fc-card-content {
flex: 1;
}
#fc-app .fc-card-front {
font-size: 14px;
font-weight: 700;
color: #1e293b;
}
#fc-app .fc-card-back {
font-size: 13px;
color: #475569;
margin-top: 3px;
}
#fc-app .fc-card-actions {
display: flex;
gap: 5px;
flex-shrink: 0;
}
#fc-app .fc-empty {
text-align: center;
color: #94a3b8;
font-size: 14px;
padding: 32px 0;
}

/* --- 学習モード --- */
#fc-app .fc-study-info {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 12px;
flex-wrap: wrap;
gap: 8px;
}
#fc-app .fc-study-count {
font-size: 13px;
color: #64748b;
font-weight: 600;
}
#fc-app .fc-progress-bar {
width: 100%;
height: 6px;
background: #e2e8f0;
border-radius: 99px;
margin-bottom: 18px;
overflow: hidden;
}
#fc-app .fc-progress-fill {
height: 100%;
background: linear-gradient(90deg, #3b82f6, #06b6d4);
border-radius: 99px;
transition: width 0.35s ease;
}
#fc-app .fc-flipcard-wrap {
perspective: 1000px;
width: 100%;
height: 220px;
margin-bottom: 18px;
cursor: pointer;
}
#fc-app .fc-flipcard {
width: 100%;
height: 100%;
position: relative;
transform-style: preserve-3d;
transition: transform 0.5s cubic-bezier(0.4,0,0.2,1);
}
#fc-app .fc-flipcard.flipped {
transform: rotateY(180deg);
}
#fc-app .fc-card-face {
position: absolute;
width: 100%;
height: 100%;
backface-visibility: hidden;
-webkit-backface-visibility: hidden;
border-radius: 14px;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
padding: 24px;
text-align: center;
}
#fc-app .fc-card-face-front {
background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
border: 2px solid #475569;
}
#fc-app .fc-card-face-back {
background: linear-gradient(135deg, #0f4c81 0%, #1e40af 100%);
border: 2px solid #3b82f6;
transform: rotateY(180deg);
}
#fc-app .fc-face-label {
font-size: 11px;
font-weight: 700;
letter-spacing: 0.1em;
margin-bottom: 12px;
text-transform: uppercase;
}
#fc-app .fc-card-face-front .fc-face-label {
color: #94a3b8;
}
#fc-app .fc-card-face-back .fc-face-label {
color: #93c5fd;
}
#fc-app .fc-face-text {
font-size: 1.5rem;
font-weight: 700;
line-height: 1.4;
}
#fc-app .fc-card-face-front .fc-face-text {
color: #f1f5f9;
}
#fc-app .fc-card-face-back .fc-face-text {
color: #dbeafe;
}
#fc-app .fc-flip-hint {
font-size: 12px;
color: #94a3b8;
margin-top: 12px;
text-align: center;
}
#fc-app .fc-study-buttons {
display: flex;
gap: 10px;
justify-content: center;
flex-wrap: wrap;
margin-bottom: 18px;
}
#fc-app .fc-btn-remembered {
background: #16a34a;
color: #fff;
font-size: 15px;
padding: 12px 28px;
border-radius: 10px;
}
#fc-app .fc-btn-remembered:hover {
background: #15803d;
}
#fc-app .fc-btn-retry {
background: #dc2626;
color: #fff;
font-size: 15px;
padding: 12px 28px;
border-radius: 10px;
}
#fc-app .fc-btn-retry:hover {
background: #b91c1c;
}
#fc-app .fc-study-empty {
text-align: center;
padding: 40px 0;
}
#fc-app .fc-session-summary {
background: #f0fdf4;
border: 1.5px solid #86efac;
border-radius: 12px;
padding: 24px;
text-align: center;
}
#fc-app .fc-session-summary h3 {
font-size: 1.1rem;
font-weight: 700;
color: #15803d;
margin: 0 0 12px 0;
}
#fc-app .fc-summary-stats {
display: flex;
justify-content: center;
gap: 24px;
margin-bottom: 16px;
flex-wrap: wrap;
}
#fc-app .fc-summary-stat {
text-align: center;
}
#fc-app .fc-summary-num {
font-size: 1.8rem;
font-weight: 800;
color: #166534;
}
#fc-app .fc-summary-label {
font-size: 12px;
color: #4ade80;
font-weight: 600;
}

/* --- 統計 --- */
#fc-app .fc-stats-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
gap: 12px;
margin-bottom: 20px;
}
#fc-app .fc-stat-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 16px;
text-align: center;
}
#fc-app .fc-stat-num {
font-size: 2rem;
font-weight: 800;
color: #3b82f6;
}
#fc-app .fc-stat-label {
font-size: 12px;
color: #64748b;
font-weight: 600;
margin-top: 2px;
}
#fc-app .fc-stats-actions {
display: flex;
gap: 8px;
flex-wrap: wrap;
}
#fc-app .fc-alert {
padding: 10px 14px;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
margin-bottom: 12px;
}
#fc-app .fc-alert-info {
background: #eff6ff;
color: #1d4ed8;
border: 1px solid #bfdbfe;
}
#fc-app .fc-alert-success {
background: #f0fdf4;
color: #15803d;
border: 1px solid #86efac;
}

@media (max-width: 480px) {
#fc-app .fc-form-row {
flex-direction: column;
}
#fc-app .fc-flipcard-wrap {
height: 180px;
}
#fc-app .fc-face-text {
font-size: 1.2rem;
}
#fc-app .fc-tabs {
gap: 2px;
}
#fc-app .fc-tab {
font-size: 12px;
padding: 8px 4px;
}
}
</style>

<!-- タブ -->
<div class="fc-tabs" role="tablist">
<button class="fc-tab active" onclick="fcSwitchTab('create')" role="tab">作成</button>
<button class="fc-tab" onclick="fcSwitchTab('study')" role="tab">学習</button>
<button class="fc-tab" onclick="fcSwitchTab('stats')" role="tab">統計</button>
</div>

<!-- 作成パネル -->
<div id="fc-panel-create" class="fc-panel active">
<h2>カードを作成</h2>
<div class="fc-form">
<div class="fc-form-row">
<div class="fc-field">
<label>表面（質問・単語）</label>
<textarea id="fc-front-input" class="fc-input" rows="2" placeholder="例: capital of Japan"></textarea>
</div>
<div class="fc-field">
<label>裏面（答え・訳）</label>
<textarea id="fc-back-input" class="fc-input" rows="2" placeholder="例: 東京（Tokyo）"></textarea>
</div>
</div>
<div class="fc-form-actions">
<button class="fc-btn fc-btn-primary" onclick="fcAddCard()">＋ 追加</button>
<button class="fc-btn fc-btn-secondary" onclick="fcClearForm()">クリア</button>
</div>
<div class="fc-csv-row">
<span class="fc-csv-label">CSV一括取込：</span>
<button class="fc-btn fc-btn-secondary fc-btn-sm" onclick="document.getElementById('fc-csv-file').click()">CSVを選択</button>
<input type="file" id="fc-csv-file" class="fc-file-input" accept=".csv,text/csv" onchange="fcImportCSV(event)">
<span style="font-size:11px;color:#94a3b8;">形式: 表面,裏面（1行1枚）</span>
</div>
</div>
<div id="fc-card-list" class="fc-card-list">
<div class="fc-empty">カードがまだありません。上のフォームから追加してください。</div>
</div>
</div>

<!-- 学習パネル -->
<div id="fc-panel-study" class="fc-panel">
<div id="fc-study-main">
<div class="fc-study-empty">
<p style="color:#94a3b8;font-size:15px;">カードがありません。<br>「作成」タブでカードを追加してください。</p>
</div>
</div>
</div>

<!-- 統計パネル -->
<div id="fc-panel-stats" class="fc-panel">
<h2>学習統計</h2>
<div class="fc-stats-grid">
<div class="fc-stat-card">
<div class="fc-stat-num" id="fc-stat-total">0</div>
<div class="fc-stat-label">合計カード</div>
</div>
<div class="fc-stat-card">
<div class="fc-stat-num" style="color:#16a34a;" id="fc-stat-mastered">0</div>
<div class="fc-stat-label">マスター済</div>
</div>
<div class="fc-stat-card">
<div class="fc-stat-num" style="color:#f59e0b;" id="fc-stat-learning">0</div>
<div class="fc-stat-label">学習中</div>
</div>
<div class="fc-stat-card">
<div class="fc-stat-num" style="color:#8b5cf6;" id="fc-stat-streak">0</div>
<div class="fc-stat-label">連続正解数</div>
</div>
</div>
<div class="fc-stats-actions">
<button class="fc-btn fc-btn-primary" onclick="fcExportJSON()">JSONで書き出し</button>
<button class="fc-btn fc-btn-secondary" onclick="document.getElementById('fc-json-import').click()">JSONを取込</button>
<input type="file" id="fc-json-import" class="fc-file-input" accept=".json,application/json" onchange="fcImportJSON(event)">
<button class="fc-btn fc-btn-danger" onclick="fcResetAll()">全データ削除</button>
</div>
<div style="margin-top:14px;" id="fc-stats-msg"></div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function() {
// --- State ---
var FC = {
cards: [],          // {id, front, back, level, nextReview, correctCount, incorrectCount}
session: {
queue: [],        // card ids for current session
current: 0,
remembered: 0,
retry: 0,
flipped: false,
},
streak: 0,
editingId: null,
STORAGE_KEY: 'fc_deck_v1',
STREAK_KEY: 'fc_streak_v1',
};

// --- Persistence ---
function fcSave() {
try {
localStorage.setItem(FC.STORAGE_KEY, JSON.stringify(FC.cards));
localStorage.setItem(FC.STREAK_KEY, String(FC.streak));
} catch(e) {}
}
function fcLoad() {
try {
var d = localStorage.getItem(FC.STORAGE_KEY);
if (d) FC.cards = JSON.parse(d);
var s = localStorage.getItem(FC.STREAK_KEY);
if (s) FC.streak = parseInt(s, 10) || 0;
} catch(e) {}
}

// --- Tab switching ---
window.fcSwitchTab = function(tab) {
['create','study','stats'].forEach(function(t) {
document.getElementById('fc-panel-' + t).classList.toggle('active', t === tab);
var tabs = document.querySelectorAll('#fc-app .fc-tab');
tabs.forEach(function(el, i) {
el.classList.toggle('active', ['create','study','stats'][i] === tab);
});
});
if (tab === 'study') fcRenderStudy();
if (tab === 'stats') fcRenderStats();
};

// --- Generate ID ---
function fcGenId() {
return 'c' + Date.now() + Math.random().toString(36).slice(2, 7);
}

// --- Spaced repetition: next review interval (days) by level ---
function fcNextInterval(level) {
var intervals = [0, 1, 3, 7, 14, 30];
return (intervals[Math.min(level, intervals.length - 1)] || 30) * 86400000;
}

// --- Add card ---
window.fcAddCard = function() {
var front = document.getElementById('fc-front-input').value.trim();
var back = document.getElementById('fc-back-input').value.trim();
if (!front || !back) {
alert('表面と裏面を両方入力してください。');
return;
}
if (FC.editingId) {
var idx = FC.cards.findIndex(function(c){ return c.id === FC.editingId; });
if (idx >= 0) {
FC.cards[idx].front = front;
FC.cards[idx].back = back;
}
FC.editingId = null;
document.querySelector('#fc-app .fc-btn-primary').textContent = '＋ 追加';
} else {
FC.cards.push({
id: fcGenId(),
front: front,
back: back,
level: 0,
nextReview: Date.now(),
correctCount: 0,
incorrectCount: 0,
});
}
fcSave();
fcClearForm();
fcRenderList();
};

window.fcClearForm = function() {
document.getElementById('fc-front-input').value = '';
document.getElementById('fc-back-input').value = '';
FC.editingId = null;
document.querySelector('#fc-app .fc-btn-primary').textContent = '＋ 追加';
document.querySelectorAll('#fc-app .fc-card-item').forEach(function(el) {
el.classList.remove('editing');
});
};

// --- Edit / Delete ---
window.fcEditCard = function(id) {
var card = FC.cards.find(function(c){ return c.id === id; });
if (!card) return;
FC.editingId = id;
document.getElementById('fc-front-input').value = card.front;
document.getElementById('fc-back-input').value = card.back;
document.querySelector('#fc-app .fc-btn-primary').textContent = '保存';
document.querySelectorAll('#fc-app .fc-card-item').forEach(function(el) {
el.classList.toggle('editing', el.dataset.id === id);
});
document.getElementById('fc-front-input').focus();
};

window.fcDeleteCard = function(id) {
if (!confirm('このカードを削除しますか？')) return;
FC.cards = FC.cards.filter(function(c){ return c.id !== id; });
fcSave();
fcRenderList();
};

// --- Render card list ---
function fcRenderList() {
var el = document.getElementById('fc-card-list');
if (FC.cards.length === 0) {
el.innerHTML = '<div class="fc-empty">カードがまだありません。上のフォームから追加してください。</div>';
return;
}
el.innerHTML = FC.cards.map(function(card, i) {
var levelLabel = ['未学習','Lv1','Lv2','Lv3','Lv4','マスター'][Math.min(card.level, 5)];
var levelColor = ['#94a3b8','#60a5fa','#34d399','#fbbf24','#f97316','#8b5cf6'][Math.min(card.level, 5)];
return '<div class="fc-card-item" data-id="' + card.id + '">' +
'<div class="fc-card-idx">' + (i+1) + '</div>' +
'<div class="fc-card-content">' +
'<div class="fc-card-front">' + fcEscape(card.front) + '</div>' +
'<div class="fc-card-back">' + fcEscape(card.back) + '</div>' +
'<div style="margin-top:5px;"><span style="font-size:11px;font-weight:700;color:' + levelColor + ';">' + levelLabel + '</span>' +
' <span style="font-size:11px;color:#94a3b8;">正解:' + card.correctCount + ' 間違い:' + card.incorrectCount + '</span></div>' +
'</div>' +
'<div class="fc-card-actions">' +
'<button class="fc-btn fc-btn-secondary fc-btn-sm" onclick="fcEditCard(\'' + card.id + '\')">編集</button>' +
'<button class="fc-btn fc-btn-danger fc-btn-sm" onclick="fcDeleteCard(\'' + card.id + '\')">削除</button>' +
'</div>' +
'</div>';
}).join('');
}

function fcEscape(str) {
return String(str).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

// --- CSV import ---
window.fcImportCSV = function(e) {
var file = e.target.files[0];
if (!file) return;
var reader = new FileReader();
reader.onload = function(ev) {
var lines = ev.target.result.split(/\r?\n/);
var added = 0;
lines.forEach(function(line) {
if (!line.trim()) return;
var parts = line.split(',');
if (parts.length < 2) return;
var front = parts[0].trim().replace(/^"|"$/g,'');
var back = parts.slice(1).join(',').trim().replace(/^"|"$/g,'');
if (!front || !back) return;
FC.cards.push({
id: fcGenId(), front: front, back: back,
level: 0, nextReview: Date.now(), correctCount: 0, incorrectCount: 0,
});
added++;
});
fcSave();
fcRenderList();
alert(added + '枚のカードを取り込みました。');
};
reader.readAsText(file, 'UTF-8');
e.target.value = '';
};

// --- Study mode ---
function fcBuildQueue() {
var now = Date.now();
// Due cards first (level < 5), then unreviewed
var due = FC.cards.filter(function(c){ return c.level < 5 && c.nextReview <= now; });
var later = FC.cards.filter(function(c){ return c.level < 5 && c.nextReview > now; });
// Shuffle due
due = fcShuffle(due);
return due.concat(later).map(function(c){ return c.id; });
}

function fcShuffle(arr) {
var a = arr.slice();
for (var i = a.length - 1; i > 0; i--) {
var j = Math.floor(Math.random() * (i + 1));
var tmp = a[i]; a[i] = a[j]; a[j] = tmp;
}
return a;
}

function fcRenderStudy() {
var el = document.getElementById('fc-study-main');
if (FC.cards.length === 0) {
el.innerHTML = '<div class="fc-study-empty"><p style="color:#94a3b8;font-size:15px;">カードがありません。<br>「作成」タブでカードを追加してください。</p></div>';
return;
}
// Build queue if empty or not started
var sess = FC.session;
if (!sess.queue || sess.queue.length === 0) {
sess.queue = fcBuildQueue();
sess.current = 0;
sess.remembered = 0;
sess.retry = 0;
sess.flipped = false;
}
fcRenderCard();
}

function fcRenderCard() {
var el = document.getElementById('fc-study-main');
var sess = FC.session;
var studyableCount = FC.cards.filter(function(c){ return c.level < 5; }).length;

if (sess.current >= sess.queue.length) {
// Session complete
var total = sess.remembered + sess.retry;
var pct = total > 0 ? Math.round(sess.remembered / total * 100) : 0;
el.innerHTML =
'<div class="fc-session-summary">' +
'<h3>セッション完了！</h3>' +
'<div class="fc-summary-stats">' +
'<div class="fc-summary-stat"><div class="fc-summary-num">' + sess.remembered + '</div><div class="fc-summary-label">覚えた</div></div>' +
'<div class="fc-summary-stat"><div class="fc-summary-num" style="color:#f87171;">' + sess.retry + '</div><div class="fc-summary-label">もう一度</div></div>' +
'<div class="fc-summary-stat"><div class="fc-summary-num" style="color:#60a5fa;">' + pct + '%</div><div class="fc-summary-label">正解率</div></div>' +
'</div>' +
'<button class="fc-btn fc-btn-primary" style="margin-right:8px;" onclick="fcRestartSession()">もう一度学習</button>' +
'<button class="fc-btn fc-btn-secondary" onclick="fcSwitchTab(\'stats\')">統計を見る</button>' +
'</div>';
fcRenderStats();
return;
}

var cardId = sess.queue[sess.current];
var card = FC.cards.find(function(c){ return c.id === cardId; });
if (!card) { sess.current++; fcRenderCard(); return; }

var progress = sess.queue.length > 0 ? (sess.current / sess.queue.length * 100) : 0;
var countText = (sess.current + 1) + ' / ' + sess.queue.length;

el.innerHTML =
'<div class="fc-study-info">' +
'<span class="fc-study-count">' + countText + '</span>' +
'<span style="font-size:12px;color:#64748b;">連続正解: <strong>' + FC.streak + '</strong></span>' +
'</div>' +
'<div class="fc-progress-bar"><div class="fc-progress-fill" style="width:' + progress + '%"></div></div>' +
'<div class="fc-flipcard-wrap" onclick="fcFlipCard()">' +
'<div class="fc-flipcard" id="fc-flipcard">' +
'<div class="fc-card-face fc-card-face-front">' +
'<div class="fc-face-label">表面</div>' +
'<div class="fc-face-text">' + fcEscape(card.front) + '</div>' +
'</div>' +
'<div class="fc-card-face fc-card-face-back">' +
'<div class="fc-face-label">裏面</div>' +
'<div class="fc-face-text">' + fcEscape(card.back) + '</div>' +
'</div>' +
'</div>' +
'</div>' +
'<p class="fc-flip-hint" id="fc-flip-hint">クリックしてカードを裏返す</p>' +
'<div class="fc-study-buttons" id="fc-study-buttons" style="display:none;">' +
'<button class="fc-btn fc-btn-retry" onclick="fcAnswer(false)">もう一度 ✗</button>' +
'<button class="fc-btn fc-btn-remembered" onclick="fcAnswer(true)">覚えた ✓</button>' +
'</div>';

sess.flipped = false;
}

window.fcFlipCard = function() {
var flipcard = document.getElementById('fc-flipcard');
if (!flipcard) return;
flipcard.classList.toggle('flipped');
FC.session.flipped = !FC.session.flipped;
var btns = document.getElementById('fc-study-buttons');
var hint = document.getElementById('fc-flip-hint');
if (FC.session.flipped) {
if (btns) btns.style.display = 'flex';
if (hint) hint.style.display = 'none';
}
};

window.fcAnswer = function(remembered) {
var sess = FC.session;
var cardId = sess.queue[sess.current];
var card = FC.cards.find(function(c){ return c.id === cardId; });
if (!card) { sess.current++; fcRenderCard(); return; }

if (remembered) {
card.level = Math.min(card.level + 1, 5);
card.correctCount++;
card.nextReview = Date.now() + fcNextInterval(card.level);
sess.remembered++;
FC.streak++;
} else {
card.level = Math.max(card.level - 1, 0);
card.incorrectCount++;
card.nextReview = Date.now();
sess.retry++;
FC.streak = 0;
// Re-add to end of queue for retry
sess.queue.push(cardId);
}
fcSave();
sess.current++;
fcRenderCard();
};

window.fcRestartSession = function() {
FC.session.queue = fcBuildQueue();
FC.session.current = 0;
FC.session.remembered = 0;
FC.session.retry = 0;
FC.session.flipped = false;
fcRenderCard();
};

// --- Stats ---
function fcRenderStats() {
var total = FC.cards.length;
var mastered = FC.cards.filter(function(c){ return c.level >= 5; }).length;
var learning = FC.cards.filter(function(c){ return c.level > 0 && c.level < 5; }).length;
document.getElementById('fc-stat-total').textContent = total;
document.getElementById('fc-stat-mastered').textContent = mastered;
document.getElementById('fc-stat-learning').textContent = learning;
document.getElementById('fc-stat-streak').textContent = FC.streak;
}

// --- JSON export/import ---
window.fcExportJSON = function() {
var data = JSON.stringify({ cards: FC.cards, streak: FC.streak, exportedAt: new Date().toISOString() }, null, 2);
var blob = new Blob([data], { type: 'application/json' });
var url = URL.createObjectURL(blob);
var a = document.createElement('a');
a.href = url;
a.download = 'flashcard-deck-' + new Date().toISOString().slice(0,10) + '.json';
a.click();
URL.revokeObjectURL(url);
};

window.fcImportJSON = function(e) {
var file = e.target.files[0];
if (!file) return;
var reader = new FileReader();
reader.onload = function(ev) {
try {
var data = JSON.parse(ev.target.result);
if (!data.cards || !Array.isArray(data.cards)) throw new Error('invalid');
if (!confirm('現在のデッキをインポートしたデータで上書きしますか？')) return;
FC.cards = data.cards;
FC.streak = data.streak || 0;
fcSave();
fcRenderList();
fcRenderStats();
var msg = document.getElementById('fc-stats-msg');
msg.innerHTML = '<div class="fc-alert fc-alert-success">' + FC.cards.length + '枚のカードを取り込みました。</div>';
setTimeout(function(){ msg.innerHTML = ''; }, 3000);
} catch(err) {
alert('JSONファイルの読み込みに失敗しました。正しいフォーマットか確認してください。');
}
};
reader.readAsText(file, 'UTF-8');
e.target.value = '';
};

// --- Reset all ---
window.fcResetAll = function() {
if (!confirm('全てのカードと学習データを削除しますか？この操作は取り消せません。')) return;
FC.cards = [];
FC.streak = 0;
FC.session = { queue: [], current: 0, remembered: 0, retry: 0, flipped: false };
fcSave();
fcRenderList();
fcRenderStats();
var msg = document.getElementById('fc-stats-msg');
msg.innerHTML = '<div class="fc-alert fc-alert-info">全データを削除しました。</div>';
setTimeout(function(){ msg.innerHTML = ''; }, 3000);
};

// --- Init ---
fcLoad();
fcRenderList();
})();
</script>
</div>

---

> 読書速度を測定 → [読書速度テスト](/ja/tools/reading-speed-calculator/)
> ポモドーロで集中 → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)
> タイピング速度を測定 → [タイピング速度テスト](/ja/tools/typing-speed-test/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
