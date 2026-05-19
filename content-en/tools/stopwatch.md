---
title: "Stopwatch - Free Online Stopwatch with Lap Timer"
date: 2025-05-16
description: "Free online stopwatch with lap timer, countdown mode, and fullscreen support. Track hours, minutes, seconds, and milliseconds. Best/worst lap highlighting, keyboard shortcuts included."
categories: ["Free Tools"]
tags: ["stopwatch", "lap timer", "countdown", "time tracking", "productivity"]
slug: "stopwatch"
aliases: ["/tools/stopwatch-timer/", "/tools/countdown-timer/"]
cover:
  image: "/images/covers/stopwatch.png"
  alt: "Free Online Stopwatch with Lap Timer"
ShowToc: false
---

<div id="sw-app">

<style>
#sw-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
max-width: 720px;
margin: 0 auto;
padding: 16px;
color: #1a2e2a;
}

/* Mode tabs */
#sw-app .sw-mode-tabs {
display: flex;
justify-content: center;
gap: 8px;
margin-bottom: 32px;
flex-wrap: wrap;
}
#sw-app .sw-mode-tab {
padding: 8px 24px;
border: 2px solid #10b981;
border-radius: 24px;
background: transparent;
color: #10b981;
font-size: 14px;
font-weight: 600;
cursor: pointer;
transition: all 0.2s;
}
#sw-app .sw-mode-tab:hover {
background: #d1fae5;
}
#sw-app .sw-mode-tab.active {
background: #10b981;
color: #fff;
}

/* Display */
#sw-app .sw-display-wrap {
text-align: center;
margin-bottom: 32px;
}
#sw-app .sw-display {
font-size: clamp(48px, 10vw, 96px);
font-variant-numeric: tabular-nums;
font-weight: 700;
letter-spacing: 2px;
color: #065f46;
line-height: 1;
font-family: 'Courier New', 'Roboto Mono', monospace;
}
#sw-app .sw-display .sw-ms {
font-size: 0.45em;
color: #10b981;
vertical-align: baseline;
}

/* Countdown input */
#sw-app .sw-countdown-setup {
display: flex;
justify-content: center;
align-items: center;
gap: 8px;
margin-bottom: 24px;
flex-wrap: wrap;
}
#sw-app .sw-countdown-setup label {
font-size: 13px;
color: #6b7280;
font-weight: 500;
}
#sw-app .sw-countdown-setup .sw-cd-field {
display: flex;
align-items: center;
gap: 4px;
}
#sw-app .sw-cd-input {
width: 64px;
padding: 8px 10px;
border: 2px solid #10b981;
border-radius: 8px;
font-size: 18px;
font-weight: 700;
text-align: center;
color: #065f46;
outline: none;
font-family: monospace;
}
#sw-app .sw-cd-input:focus {
border-color: #059669;
box-shadow: 0 0 0 3px rgba(16,185,129,0.15);
}
#sw-app .sw-cd-sep {
font-size: 22px;
font-weight: 700;
color: #10b981;
}

/* Buttons */
#sw-app .sw-buttons {
display: flex;
justify-content: center;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 28px;
}
#sw-app .sw-btn {
padding: 13px 32px;
border: none;
border-radius: 12px;
font-size: 16px;
font-weight: 700;
cursor: pointer;
transition: transform 0.1s, box-shadow 0.1s;
box-shadow: 0 2px 8px rgba(0,0,0,0.12);
letter-spacing: 0.5px;
}
#sw-app .sw-btn:active {
transform: scale(0.96);
box-shadow: 0 1px 4px rgba(0,0,0,0.1);
}
#sw-app .sw-btn-start {
background: #10b981;
color: #fff;
min-width: 120px;
}
#sw-app .sw-btn-start:hover {
background: #059669;
}
#sw-app .sw-btn-stop {
background: #ef4444;
color: #fff;
min-width: 120px;
}
#sw-app .sw-btn-stop:hover {
background: #dc2626;
}
#sw-app .sw-btn-lap {
background: #f0fdf4;
color: #065f46;
border: 2px solid #10b981;
}
#sw-app .sw-btn-lap:hover {
background: #d1fae5;
}
#sw-app .sw-btn-reset {
background: #f3f4f6;
color: #374151;
border: 2px solid #d1d5db;
}
#sw-app .sw-btn-reset:hover {
background: #e5e7eb;
}
#sw-app .sw-btn-fs {
background: #f0fdf4;
color: #065f46;
border: 2px solid #10b981;
padding: 13px 18px;
font-size: 18px;
}
#sw-app .sw-btn-fs:hover {
background: #d1fae5;
}
#sw-app .sw-btn:disabled {
opacity: 0.4;
cursor: not-allowed;
transform: none;
}

/* Keyboard shortcuts hint */
#sw-app .sw-shortcuts {
text-align: center;
font-size: 12px;
color: #9ca3af;
margin-bottom: 28px;
}
#sw-app .sw-shortcuts kbd {
display: inline-block;
padding: 2px 6px;
background: #f3f4f6;
border: 1px solid #d1d5db;
border-radius: 4px;
font-family: monospace;
font-size: 11px;
color: #374151;
}

/* Lap table */
#sw-app .sw-lap-section {
margin-top: 8px;
}
#sw-app .sw-lap-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 10px;
}
#sw-app .sw-lap-title {
font-size: 15px;
font-weight: 700;
color: #065f46;
}
#sw-app .sw-lap-clear {
font-size: 12px;
color: #10b981;
background: none;
border: none;
cursor: pointer;
padding: 4px 8px;
border-radius: 6px;
transition: background 0.15s;
}
#sw-app .sw-lap-clear:hover {
background: #d1fae5;
}
#sw-app .sw-lap-table {
width: 100%;
border-collapse: collapse;
font-size: 14px;
}
#sw-app .sw-lap-table thead th {
padding: 10px 12px;
background: #ecfdf5;
color: #065f46;
font-weight: 700;
text-align: left;
border-bottom: 2px solid #10b981;
font-size: 12px;
text-transform: uppercase;
letter-spacing: 0.5px;
}
#sw-app .sw-lap-table tbody tr {
border-bottom: 1px solid #f0fdf4;
transition: background 0.12s;
}
#sw-app .sw-lap-table tbody tr:hover {
background: #f0fdf4;
}
#sw-app .sw-lap-table td {
padding: 10px 12px;
font-variant-numeric: tabular-nums;
font-family: monospace;
font-size: 14px;
}
#sw-app .sw-lap-table td:first-child {
font-family: inherit;
font-weight: 600;
color: #374151;
font-size: 13px;
}
#sw-app .sw-lap-best {
background: #dcfce7 !important;
color: #166534;
font-weight: 700;
}
#sw-app .sw-lap-worst {
background: #fee2e2 !important;
color: #991b1b;
font-weight: 700;
}
#sw-app .sw-lap-best td,
#sw-app .sw-lap-worst td {
font-weight: 700;
}
#sw-app .sw-lap-badge {
display: inline-block;
padding: 1px 7px;
border-radius: 10px;
font-size: 10px;
font-family: sans-serif;
letter-spacing: 0.5px;
text-transform: uppercase;
vertical-align: middle;
margin-left: 6px;
}
#sw-app .sw-badge-best {
background: #10b981;
color: #fff;
}
#sw-app .sw-badge-worst {
background: #ef4444;
color: #fff;
}

/* Countdown finished state */
#sw-app .sw-cd-done {
color: #ef4444 !important;
animation: sw-pulse 0.6s ease-in-out infinite alternate;
}
@keyframes sw-pulse {
from { opacity: 1; }
to { opacity: 0.5; }
}

/* Fullscreen overlay */
#sw-app.sw-fullscreen {
position: fixed;
inset: 0;
z-index: 99999;
max-width: 100%;
background: #fff;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
padding: 32px;
overflow-y: auto;
}
#sw-app.sw-fullscreen .sw-display {
font-size: clamp(72px, 18vw, 160px);
}
#sw-app.sw-fullscreen .sw-lap-section {
width: 100%;
max-width: 700px;
}

/* Responsive */
@media (max-width: 480px) {
#sw-app .sw-btn {
padding: 11px 20px;
font-size: 14px;
}
#sw-app .sw-lap-table {
font-size: 12px;
}
}
</style>

<!-- Mode tabs -->
<div class="sw-mode-tabs">
<button class="sw-mode-tab active" data-mode="stopwatch" onclick="swSetMode('stopwatch')">Stopwatch</button>
<button class="sw-mode-tab" data-mode="countdown" onclick="swSetMode('countdown')">Countdown</button>
</div>

<!-- Countdown setup (hidden in stopwatch mode) -->
<div class="sw-countdown-setup" id="sw-cd-setup" style="display:none;">
<span class="sw-cd-field">
<input class="sw-cd-input" id="sw-cd-h" type="number" min="0" max="99" value="0" placeholder="hh">
<span class="sw-cd-sep">h</span>
</span>
<span class="sw-cd-field">
<input class="sw-cd-input" id="sw-cd-m" type="number" min="0" max="59" value="5" placeholder="mm">
<span class="sw-cd-sep">m</span>
</span>
<span class="sw-cd-field">
<input class="sw-cd-input" id="sw-cd-s" type="number" min="0" max="59" value="0" placeholder="ss">
<span class="sw-cd-sep">s</span>
</span>
</div>

<!-- Main display -->
<div class="sw-display-wrap">
<div class="sw-display" id="sw-display">
<span id="sw-hms">00:00:00</span><span class="sw-ms">.<span id="sw-ms">000</span></span>
</div>
</div>

<!-- Buttons -->
<div class="sw-buttons">
<button class="sw-btn sw-btn-start" id="sw-btn-startstop" onclick="swToggle()">Start</button>
<button class="sw-btn sw-btn-lap" id="sw-btn-lap" onclick="swLap()" disabled>Lap</button>
<button class="sw-btn sw-btn-reset" onclick="swReset()">Reset</button>
<button class="sw-btn sw-btn-fs" id="sw-btn-fs" onclick="swToggleFs()" title="Fullscreen">&#x26F6;</button>
</div>

<!-- Keyboard shortcuts -->
<div class="sw-shortcuts">
<kbd>Space</kbd> Start / Stop &nbsp;&nbsp;
<kbd>L</kbd> Lap &nbsp;&nbsp;
<kbd>R</kbd> Reset &nbsp;&nbsp;
<kbd>F</kbd> Fullscreen
</div>

<!-- Lap section -->
<div class="sw-lap-section" id="sw-lap-section" style="display:none;">
<div class="sw-lap-header">
<span class="sw-lap-title">Lap Times</span>
<button class="sw-lap-clear" onclick="swClearLaps()">Clear</button>
</div>
<table class="sw-lap-table">
<thead>
<tr>
<th>Lap</th>
<th>Lap Time</th>
<th>Total Time</th>
</tr>
</thead>
<tbody id="sw-lap-tbody"></tbody>
</table>
</div>

<script>
(function() {
// State
var SW = {
mode: 'stopwatch',      // 'stopwatch' | 'countdown'
running: false,
startTime: 0,           // performance.now() reference
elapsed: 0,             // ms accumulated before last pause
lapOffset: 0,           // elapsed at start of current lap
laps: [],               // [{lap, total}] in ms
cdTotal: 0,             // countdown total ms
cdDone: false,
raf: null,
fs: false
};

// Elements
var elHMS   = document.getElementById('sw-hms');
var elMS    = document.getElementById('sw-ms');
var elDisp  = document.getElementById('sw-display');
var elBtn   = document.getElementById('sw-btn-startstop');
var elLapBtn= document.getElementById('sw-btn-lap');
var elLapSec= document.getElementById('sw-lap-section');
var elTbody = document.getElementById('sw-lap-tbody');
var elCdSet = document.getElementById('sw-cd-setup');
var elApp   = document.getElementById('sw-app');
var elCdH   = document.getElementById('sw-cd-h');
var elCdM   = document.getElementById('sw-cd-m');
var elCdS   = document.getElementById('sw-cd-s');

// Format helpers
function pad2(n) { return n < 10 ? '0' + n : '' + n; }
function pad3(n) { return n < 10 ? '00' + n : n < 100 ? '0' + n : '' + n; }

function msToDisplay(ms) {
ms = Math.max(0, Math.floor(ms));
var mil = ms % 1000;
var s   = Math.floor(ms / 1000) % 60;
var m   = Math.floor(ms / 60000) % 60;
var h   = Math.floor(ms / 3600000);
return { hms: pad2(h) + ':' + pad2(m) + ':' + pad2(s), ms: pad3(mil) };
}

function msToString(ms) {
var d = msToDisplay(ms);
return d.hms + '.' + d.ms;
}

// Render current time
function render() {
var now = SW.running ? (performance.now() - SW.startTime + SW.elapsed) : SW.elapsed;
if (SW.mode === 'countdown') {
var remaining = SW.cdTotal - now;
if (remaining <= 0) {
remaining = 0;
if (!SW.cdDone) {
SW.cdDone = true;
swStop();
elDisp.classList.add('sw-cd-done');
// Browser beep via oscillator
try {
var ctx = new (window.AudioContext || window.webkitAudioContext)();
for (var i = 0; i < 3; i++) {
(function(delay) {
var osc = ctx.createOscillator();
var gain = ctx.createGain();
osc.connect(gain); gain.connect(ctx.destination);
osc.frequency.value = 880;
osc.type = 'sine';
gain.gain.setValueAtTime(0.5, ctx.currentTime + delay);
gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + delay + 0.3);
osc.start(ctx.currentTime + delay);
osc.stop(ctx.currentTime + delay + 0.35);
})(i * 0.4);
}
} catch(e) {}
}
}
var d = msToDisplay(remaining);
elHMS.textContent = d.hms;
elMS.textContent  = d.ms;
} else {
var d2 = msToDisplay(now);
elHMS.textContent = d2.hms;
elMS.textContent  = d2.ms;
}
}

function loop() {
render();
SW.raf = requestAnimationFrame(loop);
}

// Controls
function swStart() {
if (SW.mode === 'countdown' && !SW.running && SW.elapsed === 0) {
// Load countdown value
var h = parseInt(elCdH.value) || 0;
var m = parseInt(elCdM.value) || 0;
var s = parseInt(elCdS.value) || 0;
SW.cdTotal = (h * 3600 + m * 60 + s) * 1000;
if (SW.cdTotal <= 0) return;
SW.cdDone = false;
elDisp.classList.remove('sw-cd-done');
}
SW.running = true;
SW.startTime = performance.now();
elBtn.textContent = 'Stop';
elBtn.className = 'sw-btn sw-btn-stop';
elLapBtn.disabled = (SW.mode === 'countdown');
SW.raf = requestAnimationFrame(loop);
}

function swStop() {
if (!SW.running) return;
SW.elapsed += performance.now() - SW.startTime;
SW.running = false;
cancelAnimationFrame(SW.raf);
render();
elBtn.textContent = 'Start';
elBtn.className = 'sw-btn sw-btn-start';
elLapBtn.disabled = true;
}

window.swToggle = function() {
if (SW.running) swStop(); else swStart();
};

window.swLap = function() {
if (!SW.running || SW.mode === 'countdown') return;
var total = SW.elapsed + (performance.now() - SW.startTime);
var lap   = total - SW.lapOffset;
SW.lapOffset = total;
SW.laps.unshift({ lap: lap, total: total, num: SW.laps.length + 1 });
renderLaps();
elLapSec.style.display = '';
};

window.swReset = function() {
swStop();
SW.elapsed   = 0;
SW.lapOffset = 0;
SW.laps      = [];
SW.cdDone    = false;
elDisp.classList.remove('sw-cd-done');
elBtn.textContent = 'Start';
elBtn.className = 'sw-btn sw-btn-start';
elLapBtn.disabled = true;
render();
elTbody.innerHTML = '';
elLapSec.style.display = 'none';
};

window.swClearLaps = function() {
SW.laps = [];
SW.lapOffset = SW.elapsed + (SW.running ? (performance.now() - SW.startTime) : 0);
elTbody.innerHTML = '';
elLapSec.style.display = 'none';
};

window.swSetMode = function(mode) {
swReset();
SW.mode = mode;
document.querySelectorAll('#sw-app .sw-mode-tab').forEach(function(t) {
t.classList.toggle('active', t.dataset.mode === mode);
});
elCdSet.style.display = mode === 'countdown' ? 'flex' : 'none';
// Lap button: only show in stopwatch
elLapBtn.style.display = mode === 'countdown' ? 'none' : '';
elLapSec.style.display = 'none';
render();
};

window.swToggleFs = function() {
SW.fs = !SW.fs;
elApp.classList.toggle('sw-fullscreen', SW.fs);
document.getElementById('sw-btn-fs').title = SW.fs ? 'Exit Fullscreen' : 'Fullscreen';
document.getElementById('sw-btn-fs').innerHTML = SW.fs ? '&#x2715;' : '&#x26F6;';
};

// Render lap table
function renderLaps() {
if (SW.laps.length === 0) return;
// Find best and worst by lap time
var lapTimes = SW.laps.map(function(l){ return l.lap; });
var minLap = Math.min.apply(null, lapTimes);
var maxLap = Math.max.apply(null, lapTimes);
var onlyOne = SW.laps.length === 1;

elTbody.innerHTML = SW.laps.map(function(l, i) {
var isBest  = !onlyOne && l.lap === minLap;
var isWorst = !onlyOne && l.lap === maxLap;
var rowCls  = isBest ? 'sw-lap-best' : isWorst ? 'sw-lap-worst' : '';
var badge   = isBest
? '<span class="sw-lap-badge sw-badge-best">Best</span>'
: isWorst
? '<span class="sw-lap-badge sw-badge-worst">Worst</span>'
: '';
var lapNum  = SW.laps.length - i;
return '<tr class="' + rowCls + '">'
+ '<td>Lap ' + lapNum + badge + '</td>'
+ '<td>' + msToString(l.lap) + '</td>'
+ '<td>' + msToString(l.total) + '</td>'
+ '</tr>';
}).join('');
}

// Keyboard shortcuts
document.addEventListener('keydown', function(e) {
// Ignore if focus is on an input field
if (document.activeElement && (document.activeElement.tagName === 'INPUT' || document.activeElement.tagName === 'TEXTAREA')) return;
// Check the stopwatch app is present on the page
if (!document.getElementById('sw-app')) return;
if (e.code === 'Space' || e.key === ' ') {
e.preventDefault();
swToggle();
} else if (e.key === 'l' || e.key === 'L') {
swLap();
} else if (e.key === 'r' || e.key === 'R') {
swReset();
} else if (e.key === 'f' || e.key === 'F') {
swToggleFs();
}
});

// Escape exits fullscreen
document.addEventListener('keydown', function(e) {
if ((e.key === 'Escape') && SW.fs) swToggleFs();
});

// Init render
render();
})();
</script>

</div>

---

## Related Tools

> Boost focus with the Pomodoro Technique → [Pomodoro Timer](/tools/pomodoro-timer/)

> Count down to a deadline or event → [Countdown Timer](/tools/countdown-timer/)

> Generate random numbers for games or decisions → [Random Number Generator](/tools/random-number-generator/)
