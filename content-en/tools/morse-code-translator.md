---
title: "Morse Code Translator - Free Online Tool"
date: 2025-05-16
description: "Translate text to Morse code and Morse code to text instantly. Play audio beeps, control speed, and view the full Morse alphabet chart. Free online Morse code translator."
categories: ["Free Tools"]
tags: ["morse code", "morse translator", "morse decoder", "audio morse", "encoder"]
slug: "morse-code-translator"
aliases: ["/tools/morse-code/", "/tools/morse-code-translator/"]
cover:
  image: "/images/covers/morse-code-translator.png"
  alt: "Morse Code Translator"
ShowToc: false
---

<div id="morse-app">

<style>
#morse-app {
font-family: 'Courier New', 'Lucida Console', monospace;
background: #1a1a2e;
color: #e2e8f0;
border-radius: 14px;
padding: 28px;
max-width: 860px;
margin: 0 auto;
box-sizing: border-box;
}
#morse-app * { box-sizing: border-box; }

#morse-app h2 {
color: #22c55e;
font-size: 1.2rem;
margin: 0 0 6px 0;
letter-spacing: 0.08em;
text-transform: uppercase;
}

.morse-subtitle {
color: #4ade80;
font-size: 0.78rem;
margin: 0 0 22px 0;
letter-spacing: 0.04em;
opacity: 0.75;
}

/* Mode selector */
.morse-mode-bar {
display: flex;
gap: 8px;
margin-bottom: 20px;
flex-wrap: wrap;
}
.morse-mode-btn {
background: #16213e;
border: 1px solid #22c55e44;
color: #94a3b8;
padding: 7px 18px;
border-radius: 6px;
cursor: pointer;
font-family: inherit;
font-size: 0.82rem;
letter-spacing: 0.04em;
transition: all 0.18s;
}
.morse-mode-btn:hover { border-color: #22c55e; color: #22c55e; }
.morse-mode-btn.active {
background: #22c55e;
border-color: #22c55e;
color: #1a1a2e;
font-weight: 700;
}

/* Panels */
.morse-panels {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-bottom: 16px;
}
@media (max-width: 640px) {
.morse-panels { grid-template-columns: 1fr; }
}

.morse-panel {
background: #16213e;
border: 1px solid #22c55e33;
border-radius: 10px;
padding: 16px;
}
.morse-panel-label {
font-size: 0.7rem;
color: #22c55e;
letter-spacing: 0.1em;
text-transform: uppercase;
margin-bottom: 10px;
display: flex;
justify-content: space-between;
align-items: center;
}

.morse-textarea {
width: 100%;
min-height: 140px;
background: #0f172a;
border: 1px solid #22c55e22;
border-radius: 6px;
color: #e2e8f0;
font-family: 'Courier New', monospace;
font-size: 1rem;
padding: 12px;
resize: vertical;
outline: none;
transition: border-color 0.2s;
line-height: 1.6;
}
.morse-textarea:focus { border-color: #22c55e; }
.morse-textarea[readonly] {
color: #4ade80;
font-size: 1.1rem;
letter-spacing: 0.06em;
}

/* Morse visual display */
.morse-visual {
min-height: 60px;
background: #0f172a;
border: 1px solid #22c55e22;
border-radius: 6px;
padding: 12px;
display: flex;
flex-wrap: wrap;
gap: 4px;
align-items: center;
margin-top: 10px;
}
.morse-dot {
display: inline-block;
width: 8px;
height: 8px;
background: #22c55e;
border-radius: 50%;
box-shadow: 0 0 6px #22c55e88;
}
.morse-dash {
display: inline-block;
width: 24px;
height: 8px;
background: #22c55e;
border-radius: 4px;
box-shadow: 0 0 6px #22c55e88;
}
.morse-letter-gap {
display: inline-block;
width: 12px;
}
.morse-word-gap {
display: inline-block;
width: 28px;
border-left: 2px solid #22c55e22;
height: 20px;
}

/* Controls */
.morse-controls {
display: flex;
gap: 12px;
margin-bottom: 16px;
flex-wrap: wrap;
align-items: center;
}
.morse-btn {
background: #22c55e;
border: none;
color: #1a1a2e;
padding: 9px 20px;
border-radius: 6px;
cursor: pointer;
font-family: inherit;
font-size: 0.85rem;
font-weight: 700;
letter-spacing: 0.06em;
transition: all 0.18s;
display: flex;
align-items: center;
gap: 6px;
}
.morse-btn:hover { background: #4ade80; transform: translateY(-1px); }
.morse-btn:active { transform: translateY(0); }
.morse-btn.secondary {
background: #16213e;
border: 1px solid #22c55e55;
color: #22c55e;
}
.morse-btn.secondary:hover { background: #22c55e22; border-color: #22c55e; }
.morse-btn:disabled {
opacity: 0.5;
cursor: not-allowed;
transform: none;
}

.morse-wpm-group {
display: flex;
align-items: center;
gap: 8px;
margin-left: auto;
}
.morse-wpm-label {
font-size: 0.75rem;
color: #64748b;
letter-spacing: 0.04em;
}
.morse-wpm-val {
color: #22c55e;
font-weight: 700;
min-width: 32px;
}
.morse-wpm-slider {
-webkit-appearance: none;
appearance: none;
width: 120px;
height: 4px;
background: #22c55e33;
border-radius: 2px;
outline: none;
}
.morse-wpm-slider::-webkit-slider-thumb {
-webkit-appearance: none;
width: 16px;
height: 16px;
background: #22c55e;
border-radius: 50%;
cursor: pointer;
box-shadow: 0 0 6px #22c55e88;
}

/* Status bar */
.morse-status {
font-size: 0.75rem;
color: #4ade80;
min-height: 18px;
margin-bottom: 8px;
letter-spacing: 0.04em;
}

/* Reference chart */
.morse-ref-toggle {
background: none;
border: 1px solid #22c55e33;
color: #64748b;
padding: 6px 14px;
border-radius: 6px;
cursor: pointer;
font-family: inherit;
font-size: 0.75rem;
letter-spacing: 0.05em;
transition: all 0.18s;
margin-bottom: 14px;
}
.morse-ref-toggle:hover { border-color: #22c55e; color: #22c55e; }

.morse-ref {
display: none;
background: #16213e;
border: 1px solid #22c55e22;
border-radius: 10px;
padding: 20px;
margin-bottom: 10px;
}
.morse-ref.open { display: block; }

.morse-ref h3 {
color: #22c55e;
font-size: 0.8rem;
letter-spacing: 0.1em;
text-transform: uppercase;
margin: 0 0 14px 0;
}
.morse-ref-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
gap: 6px;
}
.morse-ref-item {
background: #0f172a;
border: 1px solid #22c55e22;
border-radius: 6px;
padding: 7px 10px;
display: flex;
justify-content: space-between;
align-items: center;
font-size: 0.82rem;
}
.morse-ref-char {
color: #e2e8f0;
font-weight: 700;
font-size: 0.95rem;
}
.morse-ref-code {
color: #22c55e;
letter-spacing: 0.08em;
}
.morse-ref-section {
color: #64748b;
font-size: 0.7rem;
letter-spacing: 0.08em;
text-transform: uppercase;
margin: 14px 0 8px 0;
}

/* Copy toast */
.morse-toast {
position: fixed;
bottom: 30px;
right: 30px;
background: #22c55e;
color: #1a1a2e;
padding: 10px 22px;
border-radius: 8px;
font-weight: 700;
font-size: 0.85rem;
opacity: 0;
pointer-events: none;
transition: opacity 0.3s;
z-index: 9999;
font-family: 'Courier New', monospace;
}
.morse-toast.show { opacity: 1; }

/* Playing indicator */
.morse-playing-bar {
height: 4px;
background: #22c55e22;
border-radius: 2px;
margin-bottom: 14px;
overflow: hidden;
display: none;
}
.morse-playing-bar.active { display: block; }
.morse-playing-fill {
height: 100%;
background: #22c55e;
width: 0%;
transition: width 0.1s linear;
box-shadow: 0 0 8px #22c55e;
}
</style>

<h2>// MORSE CODE TRANSLATOR</h2>
<p class="morse-subtitle">Text &lt;--&gt; Morse Code &nbsp;|&nbsp; Web Audio Playback &nbsp;|&nbsp; Auto-Detect Mode</p>

<!-- Mode buttons -->
<div class="morse-mode-bar">
<button class="morse-mode-btn active" onclick="morseSwitchMode('auto')" id="btn-auto">Auto-Detect</button>
<button class="morse-mode-btn" onclick="morseSwitchMode('text2morse')" id="btn-t2m">Text → Morse</button>
<button class="morse-mode-btn" onclick="morseSwitchMode('morse2text')" id="btn-m2t">Morse → Text</button>
</div>

<div class="morse-status" id="morse-status">Ready. Type in either box — Auto-Detect will figure out the direction.</div>

<!-- Progress bar -->
<div class="morse-playing-bar" id="morse-playing-bar">
<div class="morse-playing-fill" id="morse-playing-fill"></div>
</div>

<!-- I/O panels -->
<div class="morse-panels">
<div class="morse-panel">
<div class="morse-panel-label">
<span id="lbl-input">INPUT</span>
<span id="input-count" style="color:#64748b;font-size:0.7rem;letter-spacing:0;text-transform:none"></span>
</div>
<textarea class="morse-textarea" id="morse-input" placeholder="Type text or Morse code here..." oninput="morseAutoTranslate()"></textarea>
</div>
<div class="morse-panel">
<div class="morse-panel-label">
<span id="lbl-output">OUTPUT</span>
</div>
<textarea class="morse-textarea" id="morse-output" placeholder="Translation appears here..." readonly></textarea>
</div>
</div>

<!-- Visual display -->
<div class="morse-panel" style="margin-bottom:16px;">
<div class="morse-panel-label">VISUAL DISPLAY</div>
<div class="morse-visual" id="morse-visual"><span style="color:#22c55e33;font-size:0.8rem;">dots and dashes will appear here...</span></div>
</div>

<!-- Controls -->
<div class="morse-controls">
<button class="morse-btn" id="play-btn" onclick="morsePlay()">&#9654; Play Audio</button>
<button class="morse-btn secondary" id="stop-btn" onclick="morseStop()" disabled>&#9632; Stop</button>
<button class="morse-btn secondary" onclick="morseCopyOutput()">&#10064; Copy Output</button>
<button class="morse-btn secondary" onclick="morseClear()">&#10005; Clear</button>
<div class="morse-wpm-group">
<span class="morse-wpm-label">SPEED</span>
<input type="range" class="morse-wpm-slider" id="wpm-slider" min="5" max="40" value="15" oninput="morseUpdateWPM()">
<span class="morse-wpm-val"><span id="wpm-display">15</span> WPM</span>
</div>
</div>

<!-- Reference chart toggle -->
<button class="morse-ref-toggle" onclick="morseToggleRef()">+ Show Morse Reference Chart</button>

<div class="morse-ref" id="morse-ref">
<h3>Morse Code Reference</h3>
<div class="morse-ref-section">Letters</div>
<div class="morse-ref-grid" id="ref-letters"></div>
<div class="morse-ref-section">Numbers</div>
<div class="morse-ref-grid" id="ref-numbers"></div>
<div class="morse-ref-section">Punctuation</div>
<div class="morse-ref-grid" id="ref-punct"></div>
</div>

<div class="morse-toast" id="morse-toast">Copied!</div>

<script>
(function() {
// --- Morse tables ---
const TEXT_TO_MORSE = {
'A':'.-','B':'-...','C':'-.-.','D':'-..','E':'.','F':'..-.','G':'--.','H':'....','I':'..','J':'.---',
'K':'-.-','L':'.-..','M':'--','N':'-.','O':'---','P':'.--.','Q':'--.-','R':'.-.','S':'...','T':'-',
'U':'..-','V':'...-','W':'.--','X':'-..-','Y':'-.--','Z':'--..',
'0':'-----','1':'.----','2':'..---','3':'...--','4':'....-','5':'.....','6':'-....','7':'--...','8':'---..','9':'----.',
'.':'.-.-.-',',':'--..--','?':'..--..','!':'-.-.--','/':'-..-.','(':'-.--.',')'':'-.--.-',
'&':'.-...', ':':'---...',';':'-.-.-.','=':'-...-','+':'.-.-.', '-':'-....-','_':'..--.-',
'"':'.-..-.','$':'...-..-','@':'.--.-.', "'":'.----.'
};

const MORSE_TO_TEXT = {};
for (const [k,v] of Object.entries(TEXT_TO_MORSE)) MORSE_TO_TEXT[v] = k;

// --- State ---
let currentMode = 'auto';
let audioCtx = null;
let playing = false;
let stopFlag = false;
let playQueue = [];

// --- Mode switching ---
window.morseSwitchMode = function(mode) {
currentMode = mode;
['auto','text2morse','morse2text'].forEach(m => {
document.getElementById('btn-' + (m === 'text2morse' ? 't2m' : m === 'morse2text' ? 'm2t' : 'auto'))
.classList.toggle('active', m === mode);
});
morseAutoTranslate();
};

// --- Auto-detect ---
function isMorseInput(text) {
const trimmed = text.trim();
if (!trimmed) return false;
// Morse only contains dots, dashes, spaces, and /
return /^[.\- /\n]+$/.test(trimmed) && (trimmed.includes('.') || trimmed.includes('-'));
}

// --- Translation ---
function textToMorse(text) {
return text.toUpperCase().split('').map(ch => {
if (ch === ' ') return '/';
return TEXT_TO_MORSE[ch] || '?';
}).join(' ');
}

function morseToText(morse) {
return morse.trim().split(' / ').map(word =>
word.trim().split(' ').map(code => {
if (!code) return '';
return MORSE_TO_TEXT[code] || '?';
}).join('')
).join(' ');
}

window.morseAutoTranslate = function() {
const inp = document.getElementById('morse-input').value;
const count = inp.length;
document.getElementById('input-count').textContent = count ? count + ' chars' : '';

let direction;
if (currentMode === 'auto') {
direction = isMorseInput(inp) ? 'morse2text' : 'text2morse';
} else {
direction = currentMode;
}

let output = '';
if (!inp.trim()) {
output = '';
document.getElementById('morse-status').textContent = 'Ready. Type in either box.';
} else if (direction === 'text2morse') {
output = textToMorse(inp);
document.getElementById('lbl-input').textContent = 'TEXT INPUT';
document.getElementById('lbl-output').textContent = 'MORSE OUTPUT';
document.getElementById('morse-status').textContent = 'Mode: Text → Morse  |  ' + output.split(' ').filter(s=>s&&s!=='/').length + ' symbols';
} else {
output = morseToText(inp);
document.getElementById('lbl-input').textContent = 'MORSE INPUT';
document.getElementById('lbl-output').textContent = 'TEXT OUTPUT';
document.getElementById('morse-status').textContent = 'Mode: Morse → Text  |  ' + output.replace(/\s+/g,' ').trim().length + ' chars decoded';
}

document.getElementById('morse-output').value = output;
renderVisual(direction === 'text2morse' ? output : inp);
};

// --- Visual render ---
function renderVisual(morseStr) {
const container = document.getElementById('morse-visual');
container.innerHTML = '';
if (!morseStr || !morseStr.trim()) {
container.innerHTML = '<span style="color:#22c55e33;font-size:0.8rem;">dots and dashes will appear here...</span>';
return;
}
const words = morseStr.trim().split(' / ');
words.forEach((word, wi) => {
if (wi > 0) {
const gap = document.createElement('span');
gap.className = 'morse-word-gap';
container.appendChild(gap);
}
const letters = word.trim().split(' ');
letters.forEach((letter, li) => {
if (li > 0) {
const lg = document.createElement('span');
lg.className = 'morse-letter-gap';
container.appendChild(lg);
}
for (const ch of letter) {
if (ch === '.') {
const dot = document.createElement('span');
dot.className = 'morse-dot';
container.appendChild(dot);
} else if (ch === '-') {
const dash = document.createElement('span');
dash.className = 'morse-dash';
container.appendChild(dash);
}
}
});
});
}

// --- Audio ---
function getAudioCtx() {
if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
return audioCtx;
}

function wpmToDurations(wpm) {
// PARIS standard: 1 WPM = 1200ms per dit
const dit = 1200 / wpm;
return { dit, dah: dit * 3, gap: dit, letterGap: dit * 3, wordGap: dit * 7 };
}

async function beep(ctx, duration, startTime, freq) {
const osc = ctx.createOscillator();
const gain = ctx.createGain();
osc.connect(gain);
gain.connect(ctx.destination);
osc.frequency.value = freq || 600;
osc.type = 'sine';
gain.gain.setValueAtTime(0, startTime);
gain.gain.linearRampToValueAtTime(0.5, startTime + 0.005);
gain.gain.setValueAtTime(0.5, startTime + duration - 0.005);
gain.gain.linearRampToValueAtTime(0, startTime + duration);
osc.start(startTime);
osc.stop(startTime + duration);
}

window.morsePlay = function() {
if (playing) return;
const inp = document.getElementById('morse-input').value;
const outEl = document.getElementById('morse-output').value;
// Get the morse string (may be input or output depending on direction)
let morseStr;
if (isMorseInput(inp) && currentMode !== 'text2morse') {
morseStr = inp;
} else {
morseStr = outEl;
}
// Only play if morseStr looks like morse
if (!morseStr || !isMorseInput(morseStr)) {
document.getElementById('morse-status').textContent = 'No Morse code to play. Translate some text first.';
return;
}

playing = true;
stopFlag = false;
document.getElementById('play-btn').disabled = true;
document.getElementById('stop-btn').disabled = false;
document.getElementById('morse-playing-bar').classList.add('active');

const wpm = parseInt(document.getElementById('wpm-slider').value);
const d = wpmToDurations(wpm);
const ctx = getAudioCtx();
let t = ctx.currentTime + 0.05;

// Build schedule
const words = morseStr.trim().split(' / ');
let totalDuration = 0;
const events = [];

words.forEach((word, wi) => {
if (wi > 0) { t += d.wordGap / 1000; totalDuration += d.wordGap; }
const letters = word.trim().split(' ');
letters.forEach((letter, li) => {
if (li > 0) { t += d.letterGap / 1000; totalDuration += d.letterGap; }
for (let i = 0; i < letter.length; i++) {
if (i > 0) { t += d.gap / 1000; totalDuration += d.gap; }
const ch = letter[i];
const dur = ch === '.' ? d.dit : d.dah;
events.push({ t, dur });
t += dur / 1000;
totalDuration += dur;
}
});
});

// Schedule all beeps
events.forEach(ev => beep(ctx, ev.dur / 1000, ev.t, 600));

// Progress bar animation
const startReal = performance.now();
const progInterval = setInterval(() => {
if (stopFlag) { clearInterval(progInterval); return; }
const elapsed = performance.now() - startReal;
const pct = Math.min(100, (elapsed / totalDuration) * 100);
document.getElementById('morse-playing-fill').style.width = pct + '%';
}, 80);

// Done callback
setTimeout(() => {
clearInterval(progInterval);
document.getElementById('morse-playing-fill').style.width = '100%';
setTimeout(() => {
playing = false;
document.getElementById('play-btn').disabled = false;
document.getElementById('stop-btn').disabled = true;
document.getElementById('morse-playing-bar').classList.remove('active');
document.getElementById('morse-playing-fill').style.width = '0%';
document.getElementById('morse-status').textContent = 'Playback complete.';
}, 300);
}, totalDuration + 100);
};

window.morseStop = function() {
stopFlag = true;
playing = false;
if (audioCtx) {
audioCtx.close();
audioCtx = null;
}
document.getElementById('play-btn').disabled = false;
document.getElementById('stop-btn').disabled = true;
document.getElementById('morse-playing-bar').classList.remove('active');
document.getElementById('morse-playing-fill').style.width = '0%';
document.getElementById('morse-status').textContent = 'Playback stopped.';
};

window.morseUpdateWPM = function() {
document.getElementById('wpm-display').textContent = document.getElementById('wpm-slider').value;
};

window.morseCopyOutput = function() {
const out = document.getElementById('morse-output').value;
if (!out) return;
navigator.clipboard.writeText(out).then(() => {
const t = document.getElementById('morse-toast');
t.classList.add('show');
setTimeout(() => t.classList.remove('show'), 2000);
});
};

window.morseClear = function() {
morseStop();
document.getElementById('morse-input').value = '';
document.getElementById('morse-output').value = '';
document.getElementById('morse-visual').innerHTML = '<span style="color:#22c55e33;font-size:0.8rem;">dots and dashes will appear here...</span>';
document.getElementById('morse-status').textContent = 'Ready. Type in either box.';
document.getElementById('input-count').textContent = '';
};

// --- Reference chart toggle ---
window.morseToggleRef = function() {
const ref = document.getElementById('morse-ref');
const btn = document.querySelector('.morse-ref-toggle');
ref.classList.toggle('open');
btn.textContent = ref.classList.contains('open') ? '- Hide Morse Reference Chart' : '+ Show Morse Reference Chart';
};

// --- Build reference chart ---
const LETTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
const NUMBERS = '0123456789'.split('');
const PUNCTS  = ['.',',','?','!','/','&',':',';','=','+','-','_','"','@',"'"];

function buildRefGrid(containerId, chars) {
const grid = document.getElementById(containerId);
chars.forEach(ch => {
const code = TEXT_TO_MORSE[ch];
if (!code) return;
const item = document.createElement('div');
item.className = 'morse-ref-item';
item.innerHTML = '<span class="morse-ref-char">' + ch + '</span><span class="morse-ref-code">' + code + '</span>';
grid.appendChild(item);
});
}

buildRefGrid('ref-letters', LETTERS);
buildRefGrid('ref-numbers', NUMBERS);
buildRefGrid('ref-punct', PUNCTS);

})();
</script>

</div>

---

**Related:** Encode text with [Base64 Encoder](/tools/base64-encoder/)
