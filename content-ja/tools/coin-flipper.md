---
title: "コイントスシミュレーター"
description: "無料のオンラインコイントスツール。リアルな3Dアニメーション付きコイン投げ。複数枚同時・カスタムラベル・履歴・確率統計機能搭載。意思決定に最適。"
slug: coin-flipper
date: 2025-06-16
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/coin-flipper-ja.png
  alt: "コイントスシミュレーター"
---

<div id="cf-app">
<style>
#cf-app *,#cf-app *::before,#cf-app *::after{box-sizing:border-box;margin:0;padding:0}
#cf-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI','Hiragino Kaku Gothic ProN',Meiryo,sans-serif;max-width:700px;margin:0 auto;padding:16px;color:#1e293b}
#cf-app h2{font-size:1.1rem;font-weight:700;color:#0f172a;margin-bottom:14px}
#cf-app .cf-section{background:#fff;border:1px solid #e2e8f0;border-radius:12px;padding:20px;margin-bottom:16px}

/* Coin */
#cf-app .cf-coin-wrap{display:flex;justify-content:center;align-items:center;margin:8px 0 20px;perspective:600px}
#cf-app .cf-coin{width:130px;height:130px;position:relative;transform-style:preserve-3d;transition:transform 0.05s;cursor:pointer;user-select:none}
#cf-app .cf-coin.spinning{animation:cfSpin 0.8s ease-out forwards}
#cf-app .cf-coin-face{position:absolute;width:100%;height:100%;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:2.6rem;font-weight:900;backface-visibility:hidden;box-shadow:0 4px 18px rgba(0,0,0,0.18)}
#cf-app .cf-heads{background:linear-gradient(145deg,#f5c842,#e6a817);color:#7a4800;border:4px solid #c8860a}
#cf-app .cf-tails{background:linear-gradient(145deg,#d4d4d4,#a0a0a0);color:#3a3a3a;border:4px solid #888;transform:rotateY(180deg)}
@keyframes cfSpin{0%{transform:rotateY(0deg)}60%{transform:rotateY(900deg)}80%{transform:rotateY(1050deg)}90%{transform:rotateY(980deg)}100%{transform:rotateY(var(--cf-end-rot,1080deg))}}

/* Result badge */
#cf-app .cf-result{text-align:center;font-size:1.5rem;font-weight:800;margin-bottom:6px;min-height:36px;transition:color 0.3s}
#cf-app .cf-result.heads{color:#b45309}
#cf-app .cf-result.tails{color:#475569}
#cf-app .cf-result-label{text-align:center;font-size:0.85rem;color:#64748b;margin-bottom:16px;min-height:20px}

/* Buttons */
#cf-app .cf-btn{display:inline-flex;align-items:center;justify-content:center;gap:6px;padding:11px 22px;border:none;border-radius:8px;font-size:1rem;font-weight:700;cursor:pointer;transition:background 0.18s,transform 0.1s}
#cf-app .cf-btn:active{transform:scale(0.97)}
#cf-app .cf-btn-primary{background:#2563eb;color:#fff;font-size:1.15rem;padding:14px 36px;border-radius:10px;width:100%;margin-bottom:10px;min-height:54px}
#cf-app .cf-btn-primary:hover{background:#1d4ed8}
#cf-app .cf-btn-primary:disabled{background:#93c5fd;cursor:not-allowed;transform:none}
#cf-app .cf-btn-sm{background:#f1f5f9;color:#334155;font-size:0.85rem;padding:7px 14px;border-radius:7px;border:1px solid #e2e8f0}
#cf-app .cf-btn-sm:hover{background:#e2e8f0}
#cf-app .cf-btn-danger{background:#fee2e2;color:#b91c1c;border:1px solid #fecaca}
#cf-app .cf-btn-danger:hover{background:#fecaca}

/* Controls row */
#cf-app .cf-controls{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-bottom:12px}
#cf-app .cf-label{font-size:0.82rem;font-weight:600;color:#64748b;margin-bottom:4px;display:block}
#cf-app .cf-input{border:1px solid #cbd5e1;border-radius:7px;padding:7px 10px;font-size:0.9rem;color:#1e293b !important;color-scheme:light;background:#f8fafc;width:100%}
#cf-app .cf-input:focus{outline:2px solid #2563eb;border-color:#2563eb;background:#fff}
#cf-app .cf-select{border:1px solid #cbd5e1;border-radius:7px;padding:7px 10px;font-size:0.9rem;color:#1e293b !important;color-scheme:light;background:#f8fafc;cursor:pointer}

/* Stats */
#cf-app .cf-stats-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
#cf-app .cf-stat-card{background:#f8fafc;border:1px solid #e2e8f0;border-radius:9px;padding:12px;text-align:center}
#cf-app .cf-stat-num{font-size:1.6rem;font-weight:800;color:#2563eb;line-height:1}
#cf-app .cf-stat-label{font-size:0.75rem;color:#64748b;margin-top:4px}
#cf-app .cf-progress{height:8px;background:#e2e8f0;border-radius:4px;overflow:hidden;margin-top:10px}
#cf-app .cf-progress-bar{height:100%;background:linear-gradient(90deg,#f59e0b,#2563eb);border-radius:4px;transition:width 0.4s}

/* History */
#cf-app .cf-history-list{display:flex;flex-wrap:wrap;gap:6px;max-height:140px;overflow-y:auto;padding:4px 0}
#cf-app .cf-chip{padding:4px 10px;border-radius:20px;font-size:0.78rem;font-weight:600}
#cf-app .cf-chip.heads{background:#fef3c7;color:#92400e;border:1px solid #fde68a}
#cf-app .cf-chip.tails{background:#f1f5f9;color:#475569;border:1px solid #e2e8f0}

/* Multi flip */
#cf-app .cf-multi-results{display:flex;flex-wrap:wrap;gap:5px;margin-top:10px;max-height:120px;overflow-y:auto}
#cf-app .cf-mini-coin{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;font-weight:700}
#cf-app .cf-mini-coin.heads{background:#f5c842;color:#7a4800;border:2px solid #c8860a}
#cf-app .cf-mini-coin.tails{background:#d4d4d4;color:#3a3a3a;border:2px solid #888}

/* Best of N */
#cf-app .cf-bon-score{display:flex;gap:20px;justify-content:center;margin:12px 0;font-size:1rem;font-weight:700}
#cf-app .cf-bon-h{color:#b45309}
#cf-app .cf-bon-t{color:#475569}
#cf-app .cf-bon-win{text-align:center;padding:12px;background:#dcfce7;border:1px solid #86efac;border-radius:8px;color:#166534;font-weight:700;font-size:1rem;display:none}

/* Sound */
#cf-app .cf-top-bar{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}
#cf-app .cf-toggle{display:flex;align-items:center;gap:6px;font-size:0.82rem;color:#64748b;cursor:pointer;user-select:none}
#cf-app .cf-toggle input[type=checkbox]{width:16px;height:16px;cursor:pointer;accent-color:#2563eb}

/* freee CTA */
#cf-app .cf-freee-cta{margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px}

@media(max-width:480px){
#cf-app .cf-stats-grid{grid-template-columns:1fr 1fr}
#cf-app .cf-coin{width:110px;height:110px}
#cf-app .cf-coin-face{font-size:2.1rem}
}
</style>

<!-- メインフリップセクション -->
<div class="cf-section">
<div class="cf-top-bar">
<h2>コイントスシミュレーター</h2>
<label class="cf-toggle"><input type="checkbox" id="cf-sound" checked> 音</label>
</div>

<div class="cf-coin-wrap">
<div class="cf-coin" id="cf-coin">
<div class="cf-coin-face cf-heads" id="cf-face-h">表</div>
<div class="cf-coin-face cf-tails" id="cf-face-t">裏</div>
</div>
</div>

<div class="cf-result" id="cf-result">—</div>
<div class="cf-result-label" id="cf-result-label">クリックしてコインを投げる</div>

<button class="cf-btn cf-btn-primary" id="cf-flip-btn">コインを投げる</button>

<div class="cf-controls">
<div style="flex:1;min-width:120px">
<span class="cf-label">表のラベル</span>
<input class="cf-input" id="cf-label-h" value="表" maxlength="20">
</div>
<div style="flex:1;min-width:120px">
<span class="cf-label">裏のラベル</span>
<input class="cf-input" id="cf-label-t" value="裏" maxlength="20">
</div>
</div>

<div class="cf-freee-cta">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">ビジネスの意思決定をデータで</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、経営判断に必要な財務データをリアルタイムで把握。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>
</div>

<!-- 統計 -->
<div class="cf-section">
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
<h2>統計</h2>
<button class="cf-btn cf-btn-sm cf-btn-danger" id="cf-reset-btn">リセット</button>
</div>
<div class="cf-stats-grid">
<div class="cf-stat-card">
<div class="cf-stat-num" id="cf-stat-h">0</div>
<div class="cf-stat-label">表の回数</div>
</div>
<div class="cf-stat-card">
<div class="cf-stat-num" id="cf-stat-t">0</div>
<div class="cf-stat-label">裏の回数</div>
</div>
<div class="cf-stat-card">
<div class="cf-stat-num" id="cf-stat-pct">—</div>
<div class="cf-stat-label">表の割合</div>
</div>
<div class="cf-stat-card">
<div class="cf-stat-num" id="cf-stat-streak">0</div>
<div class="cf-stat-label">最長連続記録</div>
</div>
</div>
<div class="cf-progress" style="margin-top:12px"><div class="cf-progress-bar" id="cf-prog" style="width:50%"></div></div>
</div>

<!-- 履歴 -->
<div class="cf-section">
<h2 style="margin-bottom:12px">投げた履歴 <span style="font-weight:400;font-size:0.82rem;color:#94a3b8">（直近50回）</span></h2>
<div class="cf-history-list" id="cf-history"><span style="color:#94a3b8;font-size:0.85rem">まだ投げていません</span></div>
</div>

<!-- 複数枚 -->
<div class="cf-section">
<h2 style="margin-bottom:12px">複数枚を同時に投げる</h2>
<div style="display:flex;gap:10px;align-items:flex-end;flex-wrap:wrap">
<div style="flex:1;min-width:100px">
<span class="cf-label">枚数（1〜100）</span>
<input class="cf-input" id="cf-multi-n" type="number" min="1" max="100" value="10">
</div>
<button class="cf-btn cf-btn-primary" id="cf-multi-btn" style="width:auto;padding:11px 22px;font-size:0.95rem;margin-bottom:0">一斉に投げる</button>
</div>
<div id="cf-multi-summary" style="margin-top:10px;font-size:0.88rem;color:#475569"></div>
<div class="cf-multi-results" id="cf-multi-results"></div>
</div>

<!-- ベストオブN -->
<div class="cf-section">
<h2 style="margin-bottom:12px">ベストオブN（勝負）</h2>
<div class="cf-controls">
<div>
<span class="cf-label">シリーズ</span>
<select class="cf-select" id="cf-bon-select">
<option value="3">ベストオブ3</option>
<option value="5">ベストオブ5</option>
<option value="7">ベストオブ7</option>
</select>
</div>
<button class="cf-btn cf-btn-sm" id="cf-bon-reset-btn">新しいシリーズ</button>
</div>
<div class="cf-bon-score">
<span>表: <span class="cf-bon-h" id="cf-bon-h">0</span></span>
<span>裏: <span class="cf-bon-t" id="cf-bon-t">0</span></span>
</div>
<div id="cf-bon-history" style="font-size:0.82rem;color:#64748b;margin-bottom:10px;min-height:20px"></div>
<button class="cf-btn cf-btn-primary" id="cf-bon-flip-btn">ベストオブNで投げる</button>
<div class="cf-bon-win" id="cf-bon-win"></div>
</div>

<div style="margin-top:20px;padding:14px 16px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;font-size:0.87rem;color:#475569">
<strong>他のランダムツール：</strong><br>
サイコロを振る → <a href="/ja/tools/dice-roller/">サイコロシミュレーター</a><br>
乱数を生成 → <a href="/ja/tools/random-number-generator/">乱数ジェネレーター</a>
</div>

<script>
(function(){
var state = {
heads: 0, tails: 0,
history: [],
maxStreak: 0, currentStreak: 0, currentSide: null,
bonH: 0, bonT: 0, bonDone: false
};

var coin = document.getElementById('cf-coin');
var faceH = document.getElementById('cf-face-h');
var faceT = document.getElementById('cf-face-t');
var resultEl = document.getElementById('cf-result');
var resultLabel = document.getElementById('cf-result-label');
var flipBtn = document.getElementById('cf-flip-btn');
var resetBtn = document.getElementById('cf-reset-btn');
var labelH = document.getElementById('cf-label-h');
var labelT = document.getElementById('cf-label-t');
var statH = document.getElementById('cf-stat-h');
var statT = document.getElementById('cf-stat-t');
var statPct = document.getElementById('cf-stat-pct');
var statStreak = document.getElementById('cf-stat-streak');
var prog = document.getElementById('cf-prog');
var histEl = document.getElementById('cf-history');
var soundChk = document.getElementById('cf-sound');
var multiN = document.getElementById('cf-multi-n');
var multiBtn = document.getElementById('cf-multi-btn');
var multiSummary = document.getElementById('cf-multi-summary');
var multiResults = document.getElementById('cf-multi-results');
var bonSelect = document.getElementById('cf-bon-select');
var bonFlipBtn = document.getElementById('cf-bon-flip-btn');
var bonResetBtn = document.getElementById('cf-bon-reset-btn');
var bonHEl = document.getElementById('cf-bon-h');
var bonTEl = document.getElementById('cf-bon-t');
var bonHistEl = document.getElementById('cf-bon-history');
var bonWin = document.getElementById('cf-bon-win');

var flipping = false;

function playFlipSound() {
if (!soundChk.checked) return;
try {
var ctx = new (window.AudioContext || window.webkitAudioContext)();
var o = ctx.createOscillator();
var g = ctx.createGain();
o.connect(g); g.connect(ctx.destination);
o.type = 'triangle';
o.frequency.setValueAtTime(880, ctx.currentTime);
o.frequency.exponentialRampToValueAtTime(220, ctx.currentTime + 0.25);
g.gain.setValueAtTime(0.3, ctx.currentTime);
g.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.3);
o.start(ctx.currentTime);
o.stop(ctx.currentTime + 0.3);
} catch(e){}
}

function getLabel(side) {
return side === 'heads' ? (labelH.value || '表') : (labelT.value || '裏');
}

function updateStats() {
var total = state.heads + state.tails;
statH.textContent = state.heads;
statT.textContent = state.tails;
statPct.textContent = total ? (state.heads / total * 100).toFixed(1) + '%' : '—';
statStreak.textContent = state.maxStreak;
var pct = total ? (state.heads / total * 100) : 50;
prog.style.width = pct + '%';
}

function updateHistory() {
if (state.history.length === 0) {
histEl.innerHTML = '<span style="color:#94a3b8;font-size:0.85rem">まだ投げていません</span>';
return;
}
histEl.innerHTML = state.history.slice().reverse().map(function(s,i){
return '<span class="cf-chip ' + s + '">' + (i+1) + '. ' + getLabel(s) + '</span>';
}).join('');
}

function doFlip(callback) {
var isHeads = Math.random() < 0.5;
var side = isHeads ? 'heads' : 'tails';
var endRot = isHeads ? 1080 : 900;

faceH.textContent = labelH.value || '表';
faceT.textContent = labelT.value || '裏';

coin.style.setProperty('--cf-end-rot', endRot + 'deg');
coin.classList.remove('spinning');
void coin.offsetWidth;
coin.classList.add('spinning');
playFlipSound();

setTimeout(function(){
coin.classList.remove('spinning');
coin.style.transform = isHeads ? 'rotateY(0deg)' : 'rotateY(180deg)';
if (callback) callback(side);
}, 800);

return side;
}

function recordFlip(side) {
if (side === 'heads') state.heads++;
else state.tails++;

if (state.currentSide === side) {
state.currentStreak++;
} else {
state.currentSide = side;
state.currentStreak = 1;
}
if (state.currentStreak > state.maxStreak) state.maxStreak = state.currentStreak;

state.history.push(side);
if (state.history.length > 50) state.history.shift();
}

flipBtn.addEventListener('click', function(){
if (flipping) return;
flipping = true;
flipBtn.disabled = true;
resultEl.textContent = '…';
resultEl.className = 'cf-result';
resultLabel.textContent = 'コインを投げています…';

doFlip(function(side){
recordFlip(side);
resultEl.textContent = getLabel(side);
resultEl.className = 'cf-result ' + side;
resultLabel.textContent = side === 'heads' ? '表が出ました！' : '裏が出ました！';
updateStats();
updateHistory();
flipBtn.disabled = false;
flipping = false;
});
});

coin.addEventListener('click', function(){ if (!flipping) flipBtn.click(); });

resetBtn.addEventListener('click', function(){
state.heads = 0; state.tails = 0;
state.history = [];
state.maxStreak = 0; state.currentStreak = 0; state.currentSide = null;
resultEl.textContent = '—';
resultEl.className = 'cf-result';
resultLabel.textContent = 'クリックしてコインを投げる';
coin.style.transform = '';
updateStats();
updateHistory();
});

multiBtn.addEventListener('click', function(){
var n = Math.min(100, Math.max(1, parseInt(multiN.value) || 10));
var h = 0, t = 0;
var icons = [];
for (var i = 0; i < n; i++) {
var s = Math.random() < 0.5 ? 'heads' : 'tails';
if (s === 'heads') h++; else t++;
icons.push('<div class="cf-mini-coin ' + s + '">' + (s === 'heads' ? (labelH.value||'表')[0] : (labelT.value||'裏')[0]) + '</div>');
}
multiSummary.textContent = n + '枚: 表 ' + h + '回 (' + (h/n*100).toFixed(1) + '%)、裏 ' + t + '回 (' + (t/n*100).toFixed(1) + '%)';
multiResults.innerHTML = icons.join('');
});

function bonNeeded() { return Math.ceil(parseInt(bonSelect.value) / 2); }

function updateBon() {
bonHEl.textContent = state.bonH;
bonTEl.textContent = state.bonT;
var needed = bonNeeded();
var hist = [];
for (var i = 0; i < state.bonH; i++) hist.push('<span style="color:#b45309">表</span>');
for (var j = 0; j < state.bonT; j++) hist.push('<span style="color:#475569">裏</span>');
bonHistEl.innerHTML = hist.join(' · ');

if (state.bonH >= needed || state.bonT >= needed) {
state.bonDone = true;
var winner = state.bonH >= needed ? '表' : '裏';
bonWin.textContent = winner + ' がシリーズを制しました！';
bonWin.style.display = 'block';
bonFlipBtn.disabled = true;
}
}

bonFlipBtn.addEventListener('click', function(){
if (state.bonDone || flipping) return;
flipping = true;
bonFlipBtn.disabled = true;
doFlip(function(side){
if (side === 'heads') state.bonH++; else state.bonT++;
updateBon();
flipping = false;
if (!state.bonDone) bonFlipBtn.disabled = false;
});
});

bonResetBtn.addEventListener('click', function(){
state.bonH = 0; state.bonT = 0; state.bonDone = false;
bonWin.style.display = 'none';
bonFlipBtn.disabled = false;
updateBon();
});

bonSelect.addEventListener('change', function(){ bonResetBtn.click(); });

faceH.textContent = '表';
faceT.textContent = '裏';
updateStats();
updateBon();
})();
</script>
</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

## 関連ツール

> Dice Roller → [Dice Rollerツール](/ja/tools/dice-roller/)
> パスワード生成 → [パスワード生成ツール](/ja/tools/password-generator/)
> Random Number Generator → [Random Number Generatorツール](/ja/tools/random-number-generator/)

