---
title: "モールス信号変換ツール"
date: 2025-10-21
description: "無料のモールス信号変換ツール。テキスト↔モールス符号の双方向変換。音声再生・コピー・一覧表付き。登録不要。"
categories: ["無料ツール"]
slug: "morse-code"
ShowToc: false
cover:
  image: "/images/covers/morse-code-ja.png"
  alt: "モールス信号変換ツール"
---

<div id="mc-app">

<style>
#mc-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1e293b;
}
#mc-app * {
box-sizing: border-box;
}
#mc-app h2 {
font-size: 1.1rem;
font-weight: 700;
margin: 0 0 10px 0;
color: #0f172a;
}
#mc-app .mc-mode-bar {
display: flex;
gap: 8px;
margin-bottom: 18px;
}
#mc-app .mc-mode-btn {
padding: 9px 20px;
border: 2px solid #cbd5e1;
border-radius: 8px;
background: #fff;
font-size: 14px;
font-weight: 600;
cursor: pointer;
color: #475569;
transition: all 0.15s;
}
#mc-app .mc-mode-btn.active {
background: #0284c7;
border-color: #0284c7;
color: #fff;
}
#mc-app .mc-mode-btn:hover:not(.active) {
border-color: #0284c7;
color: #0284c7;
}
#mc-app .mc-panels {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-bottom: 16px;
}
@media (max-width: 600px) {
#mc-app .mc-panels {
grid-template-columns: 1fr;
}
}
#mc-app .mc-panel {
display: flex;
flex-direction: column;
gap: 8px;
}
#mc-app .mc-panel label {
font-size: 13px;
font-weight: 600;
color: #475569;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#mc-app .mc-textarea {
width: 100%;
min-height: 140px;
padding: 12px 14px;
border: 1.5px solid #cbd5e1;
border-radius: 10px;
font-size: 15px;
font-family: inherit;
resize: vertical;
color: #1e293b;
background: #f8fafc;
transition: border-color 0.15s;
line-height: 1.6;
}
#mc-app .mc-textarea:focus {
outline: none;
border-color: #0284c7;
background: #fff;
}
#mc-app .mc-output-box {
width: 100%;
min-height: 140px;
padding: 12px 14px;
border: 1.5px solid #cbd5e1;
border-radius: 10px;
font-size: 14px;
font-family: 'Courier New', monospace;
background: #f1f5f9;
color: #334155;
word-break: break-all;
white-space: pre-wrap;
line-height: 1.8;
}
#mc-app .mc-actions {
display: flex;
gap: 8px;
flex-wrap: wrap;
align-items: center;
}
#mc-app .mc-btn {
padding: 8px 16px;
border-radius: 7px;
border: none;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#mc-app .mc-btn-primary {
background: #0284c7;
color: #fff;
}
#mc-app .mc-btn-primary:hover {
background: #0369a1;
}
#mc-app .mc-btn-secondary {
background: #e2e8f0;
color: #334155;
}
#mc-app .mc-btn-secondary:hover {
background: #cbd5e1;
}
#mc-app .mc-btn-danger {
background: #fee2e2;
color: #dc2626;
}
#mc-app .mc-btn-danger:hover {
background: #fecaca;
}
#mc-app .mc-controls {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
margin-bottom: 16px;
display: flex;
align-items: center;
gap: 20px;
flex-wrap: wrap;
}
#mc-app .mc-controls label {
font-size: 13px;
font-weight: 600;
color: #475569;
}
#mc-app .mc-wpm-group {
display: flex;
align-items: center;
gap: 10px;
}
#mc-app .mc-wpm-input {
width: 70px;
padding: 6px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
font-weight: 600;
text-align: center;
color: #1e293b;
}
#mc-app .mc-wpm-input:focus {
outline: none;
border-color: #0284c7;
}
#mc-app .mc-status {
font-size: 12px;
color: #64748b;
margin-left: auto;
}
#mc-app .mc-visual {
display: flex;
flex-wrap: wrap;
gap: 4px;
padding: 12px 14px;
background: #f1f5f9;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
margin-bottom: 16px;
min-height: 52px;
align-items: center;
}
#mc-app .mc-visual-dot {
display: inline-block;
width: 10px;
height: 10px;
border-radius: 50%;
background: #0284c7;
}
#mc-app .mc-visual-dash {
display: inline-block;
width: 28px;
height: 10px;
border-radius: 5px;
background: #0284c7;
}
#mc-app .mc-visual-space {
display: inline-block;
width: 20px;
}
#mc-app .mc-visual-letter-gap {
display: inline-block;
width: 8px;
}
#mc-app .mc-ref {
margin-top: 24px;
}
#mc-app .mc-ref-title {
font-size: 1rem;
font-weight: 700;
color: #0f172a;
margin-bottom: 12px;
}
#mc-app .mc-ref-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
gap: 6px;
}
#mc-app .mc-ref-item {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 8px 10px;
display: flex;
align-items: center;
gap: 8px;
cursor: pointer;
transition: all 0.12s;
}
#mc-app .mc-ref-item:hover {
background: #e0f2fe;
border-color: #7dd3fc;
}
#mc-app .mc-ref-char {
font-size: 16px;
font-weight: 700;
color: #0284c7;
min-width: 20px;
}
#mc-app .mc-ref-morse {
font-size: 12px;
font-family: 'Courier New', monospace;
color: #475569;
}
#mc-app .mc-copy-toast {
display: none;
font-size: 12px;
color: #16a34a;
font-weight: 600;
}
#mc-app .mc-copy-toast.show {
display: inline;
}
#mc-app .mc-error {
color: #dc2626;
font-size: 13px;
margin-top: 4px;
}
#mc-app .mc-freee-cta {
margin-top: 28px;
padding: 18px 20px;
background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
border: 1.5px solid #bae6fd;
border-radius: 10px;
}
</style>

<div class="mc-mode-bar">
<button class="mc-mode-btn active" id="mc-btn-t2m" onclick="mcSetMode('t2m')">テキスト → モールス</button>
<button class="mc-mode-btn" id="mc-btn-m2t" onclick="mcSetMode('m2t')">モールス → テキスト</button>
</div>

<div class="mc-panels">
<div class="mc-panel">
<label id="mc-input-label">入力テキスト</label>
<textarea class="mc-textarea" id="mc-input" placeholder="ここにテキストを入力..." oninput="mcConvert()" autocomplete="off" spellcheck="false"></textarea>
<div class="mc-actions">
<button class="mc-btn mc-btn-danger" onclick="mcClear()">クリア</button>
<span class="mc-error" id="mc-error"></span>
</div>
</div>
<div class="mc-panel">
<label id="mc-output-label">モールス符号</label>
<div class="mc-output-box" id="mc-output"></div>
<div class="mc-actions">
<button class="mc-btn mc-btn-secondary" onclick="mcCopy()">コピー</button>
<span class="mc-copy-toast" id="mc-copy-toast">コピーしました！</span>
<button class="mc-btn mc-btn-primary" id="mc-play-btn" onclick="mcPlay()">&#9654; 音声再生</button>
<button class="mc-btn mc-btn-danger" id="mc-stop-btn" onclick="mcStop()" style="display:none;">&#9646;&#9646; 停止</button>
</div>
</div>
</div>

<div class="mc-controls">
<div class="mc-wpm-group">
<label for="mc-wpm">速度 (WPM)：</label>
<input type="number" class="mc-wpm-input" id="mc-wpm" value="15" min="5" max="40" onchange="mcUpdateWpm()">
</div>
<span class="mc-status" id="mc-status">待機中</span>
</div>

<div id="mc-visual-area">
<h2>ビジュアル表示</h2>
<div class="mc-visual" id="mc-visual"></div>
</div>

<div class="mc-ref">
<div class="mc-ref-title">符号一覧 <span style="font-size:12px;font-weight:400;color:#64748b;">（クリックで入力欄に追加）</span></div>
<div class="mc-ref-grid" id="mc-ref-grid"></div>
</div>

<div class="mc-freee-cta">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>

<script>
(function() {
var CODE = {
'A':'.-','B':'-...','C':'-.-.','D':'-..','E':'.','F':'..-.','G':'--.','H':'....','I':'..','J':'.---',
'K':'-.-','L':'.-..','M':'--','N':'-.','O':'---','P':'.--.','Q':'--.-','R':'.-.','S':'...','T':'-',
'U':'..-','V':'...-','W':'.--','X':'-..-','Y':'-.--','Z':'--..',
'0':'-----','1':'.----','2':'..---','3':'...--','4':'....-','5':'.....','6':'-....','7':'--...','8':'---..','9':'----.',
'.':'.-.-.-',',':'--..--','?':'..--..','!':'-.-.--','/':'-..-.','(':'-.--.',')':'-.--.-',
'&':'.-...',':':'---...',';':'-.-.-.','=':'-...-','+':'.-.-.', '-':'-....-','_':'..--.-',
'"':'.-..-.','$':'...-..-','@':'.--.-.','\'':'.----.'
};
var DECODE = {};
for (var k in CODE) DECODE[CODE[k]] = k;

var mode = 't2m';
var wpm = 15;
var audioCtx = null;
var playing = false;
var stopFlag = false;

function getDotDuration() {
return 1200 / wpm;
}

window.mcSetMode = function(m) {
mode = m;
document.getElementById('mc-btn-t2m').classList.toggle('active', m === 't2m');
document.getElementById('mc-btn-m2t').classList.toggle('active', m === 'm2t');
var inp = document.getElementById('mc-input');
var inpLabel = document.getElementById('mc-input-label');
var outLabel = document.getElementById('mc-output-label');
inp.value = '';
document.getElementById('mc-output').textContent = '';
document.getElementById('mc-visual').innerHTML = '';
document.getElementById('mc-error').textContent = '';
if (m === 't2m') {
inp.placeholder = 'ここにテキストを入力...';
inpLabel.textContent = '入力テキスト';
outLabel.textContent = 'モールス符号';
} else {
inp.placeholder = 'モールス符号を入力（文字間はスペース、単語間は / ）';
inpLabel.textContent = 'モールス符号入力';
outLabel.textContent = 'デコード結果';
}
};

window.mcConvert = function() {
var inp = document.getElementById('mc-input').value;
var out = '';
var errEl = document.getElementById('mc-error');
errEl.textContent = '';

if (mode === 't2m') {
var upper = inp.toUpperCase();
var words = upper.split(' ');
var morseWords = [];
for (var wi = 0; wi < words.length; wi++) {
var word = words[wi];
var letters = [];
for (var li = 0; li < word.length; li++) {
var ch = word[li];
if (CODE[ch]) {
letters.push(CODE[ch]);
}
}
if (letters.length) morseWords.push(letters.join(' '));
}
out = morseWords.join(' / ');
} else {
var trimmed = inp.trim();
if (!trimmed) { document.getElementById('mc-output').textContent = ''; updateVisual(''); return; }
var wordGroups = trimmed.split(/\s*\/\s*/);
var decoded = [];
var errors = [];
for (var wg = 0; wg < wordGroups.length; wg++) {
var wgVal = wordGroups[wg].trim();
if (!wgVal) continue;
var tokens = wgVal.split(/\s+/);
var word = '';
for (var t = 0; t < tokens.length; t++) {
var tok = tokens[t];
if (!tok) continue;
if (DECODE[tok]) {
word += DECODE[tok];
} else {
word += '?';
errors.push(tok);
}
}
decoded.push(word);
}
out = decoded.join(' ');
if (errors.length) {
errEl.textContent = '不明な符号: ' + errors.slice(0,5).join(', ');
}
}

document.getElementById('mc-output').textContent = out;
updateVisual(mode === 't2m' ? out : '');
};

function updateVisual(morseStr) {
var vis = document.getElementById('mc-visual');
vis.innerHTML = '';
if (!morseStr) return;
var words = morseStr.split(' / ');
for (var wi = 0; wi < words.length; wi++) {
if (wi > 0) {
var sp = document.createElement('span');
sp.className = 'mc-visual-space';
vis.appendChild(sp);
}
var letters = words[wi].split(' ');
for (var li = 0; li < letters.length; li++) {
if (li > 0) {
var lg = document.createElement('span');
lg.className = 'mc-visual-letter-gap';
vis.appendChild(lg);
}
var sym = letters[li];
for (var si = 0; si < sym.length; si++) {
var el = document.createElement('span');
if (sym[si] === '.') {
el.className = 'mc-visual-dot';
} else if (sym[si] === '-') {
el.className = 'mc-visual-dash';
}
vis.appendChild(el);
}
}
}
}

window.mcClear = function() {
mcStop();
document.getElementById('mc-input').value = '';
document.getElementById('mc-output').textContent = '';
document.getElementById('mc-visual').innerHTML = '';
document.getElementById('mc-error').textContent = '';
document.getElementById('mc-status').textContent = '待機中';
};

window.mcCopy = function() {
var out = document.getElementById('mc-output').textContent;
if (!out) return;
navigator.clipboard.writeText(out).then(function() {
var t = document.getElementById('mc-copy-toast');
t.classList.add('show');
setTimeout(function() { t.classList.remove('show'); }, 2000);
}).catch(function() {
var ta = document.createElement('textarea');
ta.value = out;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
var t = document.getElementById('mc-copy-toast');
t.classList.add('show');
setTimeout(function() { t.classList.remove('show'); }, 2000);
});
};

window.mcUpdateWpm = function() {
var v = parseInt(document.getElementById('mc-wpm').value, 10);
if (v >= 5 && v <= 40) wpm = v;
};

function getMorseToPlay() {
var out = document.getElementById('mc-output').textContent.trim();
if (mode === 'm2t') {
out = document.getElementById('mc-input').value.trim();
}
return out;
}

window.mcPlay = function() {
if (playing) return;
var morse = getMorseToPlay();
if (!morse) {
document.getElementById('mc-status').textContent = '再生するデータがありません。';
return;
}
stopFlag = false;
playing = true;
document.getElementById('mc-play-btn').style.display = 'none';
document.getElementById('mc-stop-btn').style.display = '';
document.getElementById('mc-status').textContent = '再生中...';

if (!audioCtx) {
audioCtx = new (window.AudioContext || window.webkitAudioContext)();
}

playMorse(morse).then(function() {
playing = false;
stopFlag = false;
document.getElementById('mc-play-btn').style.display = '';
document.getElementById('mc-stop-btn').style.display = 'none';
document.getElementById('mc-status').textContent = '再生完了';
});
};

window.mcStop = function() {
stopFlag = true;
playing = false;
document.getElementById('mc-play-btn').style.display = '';
document.getElementById('mc-stop-btn').style.display = 'none';
document.getElementById('mc-status').textContent = '停止しました';
};

function sleep(ms) {
return new Promise(function(resolve) { setTimeout(resolve, ms); });
}

function beep(freq, duration) {
return new Promise(function(resolve) {
if (!audioCtx) { resolve(); return; }
var osc = audioCtx.createOscillator();
var gain = audioCtx.createGain();
osc.connect(gain);
gain.connect(audioCtx.destination);
osc.frequency.value = freq;
osc.type = 'sine';
gain.gain.setValueAtTime(0, audioCtx.currentTime);
gain.gain.linearRampToValueAtTime(0.4, audioCtx.currentTime + 0.005);
gain.gain.setValueAtTime(0.4, audioCtx.currentTime + duration / 1000 - 0.005);
gain.gain.linearRampToValueAtTime(0, audioCtx.currentTime + duration / 1000);
osc.start(audioCtx.currentTime);
osc.stop(audioCtx.currentTime + duration / 1000);
osc.onended = resolve;
});
}

async function playMorse(morse) {
var dot = getDotDuration();
var dash = dot * 3;
var symGap = dot;
var letterGap = dot * 3;
var wordGap = dot * 7;
var freq = 600;

var words = morse.split(/\s*\/\s*/);
for (var wi = 0; wi < words.length; wi++) {
if (stopFlag) return;
if (wi > 0) await sleep(wordGap);
var letters = words[wi].trim().split(/\s+/);
for (var li = 0; li < letters.length; li++) {
if (stopFlag) return;
if (li > 0) await sleep(letterGap);
var sym = letters[li];
for (var si = 0; si < sym.length; si++) {
if (stopFlag) return;
if (si > 0) await sleep(symGap);
if (sym[si] === '.') {
await beep(freq, dot);
} else if (sym[si] === '-') {
await beep(freq, dash);
}
}
}
}
}

function buildRefGrid() {
var grid = document.getElementById('mc-ref-grid');
var all = Object.keys(CODE);
for (var i = 0; i < all.length; i++) {
var ch = all[i];
var item = document.createElement('div');
item.className = 'mc-ref-item';
item.innerHTML = '<span class="mc-ref-char">' + ch + '</span><span class="mc-ref-morse">' + CODE[ch] + '</span>';
item.setAttribute('data-char', ch);
item.addEventListener('click', (function(c) {
return function() {
var inp = document.getElementById('mc-input');
if (mode === 't2m') {
inp.value += c;
} else {
var cur = inp.value;
var suffix = cur.length > 0 && cur[cur.length-1] !== ' ' ? ' ' : '';
inp.value += suffix + CODE[c];
}
mcConvert();
inp.focus();
};
})(ch));
grid.appendChild(item);
}
}

buildRefGrid();
})();
</script>

---

> テキスト暗号化 → [テキスト暗号化ツール](/ja/tools/text-encryption/)
> バーコード生成 → [バーコードジェネレーター](/ja/tools/barcode-generator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
