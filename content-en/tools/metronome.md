---
title: "Online Metronome - Free BPM Timer"
date: 2025-05-16
description: "Free online metronome with adjustable BPM, time signatures, and accent patterns. Practice music with a precise beat."
categories: ["Free Tools"]
tags: ["Utility", "Free Tools"]
slug: "metronome"
ShowToc: false
cover:
  image: "/images/covers/metronome.png"
  alt: "Online Metronome"
---

<div id="met-app">

<style>
#met-app {
font-family: 'Segoe UI', system-ui, sans-serif;
max-width: 540px;
margin: 0 auto;
padding: 24px 20px;
color: #1a1a2e;
}
#met-app * { box-sizing: border-box; }

#met-app h2 {
text-align: center;
font-size: 1.4rem;
margin: 0 0 24px;
color: #16213e;
}

/* BPM Display */
#met-app .bpm-display {
text-align: center;
margin-bottom: 20px;
}
#met-app .bpm-number {
font-size: 5rem;
font-weight: 800;
line-height: 1;
color: #0f3460;
letter-spacing: -2px;
}
#met-app .bpm-label {
font-size: 0.85rem;
letter-spacing: 3px;
text-transform: uppercase;
color: #888;
margin-top: 4px;
}

/* Tempo marking */
#met-app .tempo-marking {
text-align: center;
font-size: 1.05rem;
font-style: italic;
color: #e94560;
margin-bottom: 20px;
min-height: 1.5em;
}

/* Beat indicator */
#met-app .beat-row {
display: flex;
justify-content: center;
gap: 10px;
margin-bottom: 24px;
}
#met-app .beat-dot {
width: 36px;
height: 36px;
border-radius: 50%;
background: #dde3f0;
transition: background 0.05s, transform 0.05s;
}
#met-app .beat-dot.accent {
background: #c0c8e0;
}
#met-app .beat-dot.active {
background: #e94560;
transform: scale(1.18);
box-shadow: 0 0 12px rgba(233,69,96,0.5);
}
#met-app .beat-dot.accent.active {
background: #c0392b;
box-shadow: 0 0 16px rgba(192,57,43,0.6);
}

/* Slider */
#met-app .slider-wrap {
margin-bottom: 20px;
}
#met-app .slider-wrap label {
display: block;
font-size: 0.8rem;
font-weight: 600;
letter-spacing: 1px;
text-transform: uppercase;
color: #555;
margin-bottom: 8px;
}
#met-app input[type="range"] {
width: 100%;
height: 6px;
accent-color: #0f3460;
cursor: pointer;
}

/* Buttons */
#met-app .btn-row {
display: flex;
gap: 12px;
margin-bottom: 20px;
}
#met-app .btn {
flex: 1;
padding: 14px;
border: none;
border-radius: 10px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
#met-app .btn:active { transform: scale(0.97); }
#met-app .btn-start {
background: #0f3460;
color: #fff;
}
#met-app .btn-start.running {
background: #e94560;
}
#met-app .btn-tap {
background: #f0f3fa;
color: #0f3460;
border: 2px solid #ccd3e8;
}
#met-app .btn-tap:active {
background: #dde3f0;
}

/* Time signature */
#met-app .timesig-wrap {
margin-bottom: 20px;
}
#met-app .timesig-wrap label {
display: block;
font-size: 0.8rem;
font-weight: 600;
letter-spacing: 1px;
text-transform: uppercase;
color: #555;
margin-bottom: 8px;
}
#met-app .timesig-grid {
display: flex;
gap: 8px;
}
#met-app .timesig-btn {
flex: 1;
padding: 10px 4px;
border: 2px solid #ccd3e8;
border-radius: 8px;
background: #f0f3fa;
color: #333;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
text-align: center;
transition: all 0.15s;
}
#met-app .timesig-btn.selected {
border-color: #0f3460;
background: #0f3460;
color: #fff;
}

/* Volume */
#met-app .vol-wrap {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 24px;
}
#met-app .vol-wrap label {
font-size: 0.8rem;
font-weight: 600;
letter-spacing: 1px;
text-transform: uppercase;
color: #555;
white-space: nowrap;
}
#met-app .vol-wrap input[type="range"] {
flex: 1;
}
#met-app .vol-pct {
font-size: 0.85rem;
color: #555;
width: 36px;
text-align: right;
}

/* Tempo reference */
#met-app .tempo-ref {
background: #f7f9ff;
border: 1px solid #dde3f0;
border-radius: 10px;
padding: 16px;
margin-bottom: 24px;
}
#met-app .tempo-ref h3 {
font-size: 0.8rem;
font-weight: 700;
letter-spacing: 1px;
text-transform: uppercase;
color: #888;
margin: 0 0 12px;
}
#met-app .tempo-ref table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
}
#met-app .tempo-ref td {
padding: 5px 8px;
color: #333;
}
#met-app .tempo-ref td:first-child {
font-style: italic;
font-weight: 600;
color: #0f3460;
width: 38%;
}
#met-app .tempo-ref tr:nth-child(even) td {
background: #eef1fa;
}
#met-app .tempo-ref .current-row td {
background: #ffeef1;
color: #c0392b;
font-weight: 700;
}

/* Related tools */
#met-app .related {
border-top: 1px solid #dde3f0;
padding-top: 20px;
}
#met-app .related h3 {
font-size: 0.8rem;
font-weight: 700;
letter-spacing: 1px;
text-transform: uppercase;
color: #888;
margin: 0 0 10px;
}
#met-app .related ul {
list-style: none;
padding: 0;
margin: 0;
display: flex;
flex-wrap: wrap;
gap: 8px;
}
#met-app .related a {
display: inline-block;
padding: 6px 14px;
background: #f0f3fa;
border: 1px solid #ccd3e8;
border-radius: 20px;
font-size: 0.85rem;
color: #0f3460;
text-decoration: none;
transition: background 0.15s;
}
#met-app .related a:hover {
background: #dde3f0;
}
</style>

<h2>Online Metronome</h2>

<!-- Beat dots -->
<div class="beat-row" id="met-beat-row"></div>

<!-- BPM display -->
<div class="bpm-display">
<div class="bpm-number" id="met-bpm-num">120</div>
<div class="bpm-label">BPM</div>
</div>

<!-- Tempo marking -->
<div class="tempo-marking" id="met-tempo-name">Moderato</div>

<!-- BPM slider -->
<div class="slider-wrap">
<label for="met-bpm-slider">Tempo</label>
<input type="range" id="met-bpm-slider" min="40" max="220" value="120">
</div>

<!-- Start / Tap -->
<div class="btn-row">
<button class="btn btn-start" id="met-start-btn">Start</button>
<button class="btn btn-tap" id="met-tap-btn">Tap Tempo</button>
</div>

<!-- Time signature -->
<div class="timesig-wrap">
<label>Time Signature</label>
<div class="timesig-grid" id="met-timesig-grid">
<button class="timesig-btn" data-beats="2" data-label="2/4">2/4</button>
<button class="timesig-btn selected" data-beats="4" data-label="4/4">4/4</button>
<button class="timesig-btn" data-beats="3" data-label="3/4">3/4</button>
<button class="timesig-btn" data-beats="6" data-label="6/8">6/8</button>
</div>
</div>

<!-- Volume -->
<div class="vol-wrap">
<label for="met-vol">Volume</label>
<input type="range" id="met-vol" min="0" max="100" value="80">
<span class="vol-pct" id="met-vol-pct">80%</span>
</div>

<!-- Tempo reference table -->
<div class="tempo-ref">
<h3>Tempo Reference</h3>
<table id="met-tempo-table">
<tr data-min="40" data-max="59"><td>Largo</td><td>40 – 59 BPM</td><td>Very slow, broad</td></tr>
<tr data-min="60" data-max="85"><td>Andante</td><td>60 – 85 BPM</td><td>Walking pace</td></tr>
<tr data-min="86" data-max="140"><td>Moderato</td><td>86 – 140 BPM</td><td>Moderate</td></tr>
<tr data-min="141" data-max="180"><td>Allegro</td><td>141 – 180 BPM</td><td>Fast, lively</td></tr>
<tr data-min="181" data-max="220"><td>Presto</td><td>181 – 220 BPM</td><td>Very fast</td></tr>
</table>
</div>

<!-- Related tools -->
<div class="related">
<h3>Related Tools</h3>
<ul>
<li><a href="/tools/pomodoro-timer/">Pomodoro Timer</a></li>
<li><a href="/tools/stopwatch/">Stopwatch</a></li>
<li><a href="/tools/countdown-timer/">Countdown Timer</a></li>
<li><a href="/tools/noise-generator/">Focus Noise Generator</a></li>
</ul>
</div>

<script>
(function() {
'use strict';

// --- State ---
var bpm = 120;
var beatsPerMeasure = 4;
var currentBeat = -1;
var isRunning = false;
var volume = 0.8;
var audioCtx = null;
var nextBeatTime = 0;
var scheduleAheadTime = 0.1;
var lookahead = 25.0;
var schedulerTimer = null;

// Tap tempo state
var tapTimes = [];

// Tempo markings
var tempoMarkings = [
{ name: 'Largo',    min: 40,  max: 59  },
{ name: 'Andante',  min: 60,  max: 85  },
{ name: 'Moderato', min: 86,  max: 140 },
{ name: 'Allegro',  min: 141, max: 180 },
{ name: 'Presto',   min: 181, max: 220 }
];

// --- DOM refs ---
var bpmSlider  = document.getElementById('met-bpm-slider');
var bpmNumEl   = document.getElementById('met-bpm-num');
var tempoName  = document.getElementById('met-tempo-name');
var startBtn   = document.getElementById('met-start-btn');
var tapBtn     = document.getElementById('met-tap-btn');
var beatRow    = document.getElementById('met-beat-row');
var timesigGrid= document.getElementById('met-timesig-grid');
var volSlider  = document.getElementById('met-vol');
var volPct     = document.getElementById('met-vol-pct');
var tempoTable = document.getElementById('met-tempo-table');

// --- Audio ---
function getAudioCtx() {
if (!audioCtx) {
audioCtx = new (window.AudioContext || window.webkitAudioContext)();
}
return audioCtx;
}

function scheduleClick(time, isAccent) {
var ctx = getAudioCtx();
var osc = ctx.createOscillator();
var env = ctx.createGain();

osc.connect(env);
env.connect(ctx.destination);

if (isAccent) {
osc.frequency.value = 1100;
env.gain.setValueAtTime(volume, time);
env.gain.exponentialRampToValueAtTime(0.001, time + 0.06);
} else {
osc.frequency.value = 880;
env.gain.setValueAtTime(volume * 0.65, time);
env.gain.exponentialRampToValueAtTime(0.001, time + 0.04);
}

osc.start(time);
osc.stop(time + 0.08);
}

// --- Beat dots ---
function renderBeatDots() {
beatRow.innerHTML = '';
for (var i = 0; i < beatsPerMeasure; i++) {
var d = document.createElement('div');
d.className = 'beat-dot' + (i === 0 ? ' accent' : '');
d.id = 'met-dot-' + i;
beatRow.appendChild(d);
}
}

function flashBeat(beatIndex) {
for (var i = 0; i < beatsPerMeasure; i++) {
var d = document.getElementById('met-dot-' + i);
if (d) d.classList.remove('active');
}
var active = document.getElementById('met-dot-' + beatIndex);
if (active) active.classList.add('active');
}

function clearBeats() {
for (var i = 0; i < beatsPerMeasure; i++) {
var d = document.getElementById('met-dot-' + i);
if (d) d.classList.remove('active');
}
}

// --- Scheduler ---
var pendingFlashes = [];

function scheduler() {
var ctx = getAudioCtx();
while (nextBeatTime < ctx.currentTime + scheduleAheadTime) {
var isAccent = (currentBeat === 0);
scheduleClick(nextBeatTime, isAccent);

// Schedule visual flash
var beatToFlash = currentBeat;
var flashAt = nextBeatTime;
pendingFlashes.push({ beat: beatToFlash, time: flashAt });

currentBeat = (currentBeat + 1) % beatsPerMeasure;
nextBeatTime += 60.0 / bpm;
}
}

function visualLoop() {
if (!isRunning) return;
var ctx = getAudioCtx();
var now = ctx.currentTime;
while (pendingFlashes.length && pendingFlashes[0].time <= now + 0.015) {
flashBeat(pendingFlashes.shift().beat);
}
requestAnimationFrame(visualLoop);
}

function startMetronome() {
var ctx = getAudioCtx();
if (ctx.state === 'suspended') ctx.resume();
currentBeat = 0;
pendingFlashes = [];
nextBeatTime = ctx.currentTime + 0.05;
schedulerTimer = setInterval(scheduler, lookahead);
visualLoop();
}

function stopMetronome() {
clearInterval(schedulerTimer);
schedulerTimer = null;
pendingFlashes = [];
clearBeats();
}

// --- BPM helpers ---
function getTempoName(b) {
for (var i = 0; i < tempoMarkings.length; i++) {
if (b >= tempoMarkings[i].min && b <= tempoMarkings[i].max) return tempoMarkings[i].name;
}
return '';
}

function updateBPM(val) {
bpm = Math.min(220, Math.max(40, val));
bpmSlider.value = bpm;
bpmNumEl.textContent = bpm;
tempoName.textContent = getTempoName(bpm);
highlightTempoRow(bpm);
}

function highlightTempoRow(b) {
var rows = tempoTable.querySelectorAll('tr');
rows.forEach(function(row) {
var mn = parseInt(row.getAttribute('data-min'));
var mx = parseInt(row.getAttribute('data-max'));
if (b >= mn && b <= mx) {
row.classList.add('current-row');
} else {
row.classList.remove('current-row');
}
});
}

// --- Events ---
bpmSlider.addEventListener('input', function() {
updateBPM(parseInt(this.value));
});

startBtn.addEventListener('click', function() {
isRunning = !isRunning;
if (isRunning) {
startBtn.textContent = 'Stop';
startBtn.classList.add('running');
startMetronome();
} else {
startBtn.textContent = 'Start';
startBtn.classList.remove('running');
stopMetronome();
}
});

// Tap tempo
tapBtn.addEventListener('click', function() {
var now = Date.now();
tapTimes.push(now);
// Keep only taps within last 3 seconds
tapTimes = tapTimes.filter(function(t) { return now - t < 3000; });
if (tapTimes.length >= 2) {
var intervals = [];
for (var i = 1; i < tapTimes.length; i++) {
intervals.push(tapTimes[i] - tapTimes[i-1]);
}
var avg = intervals.reduce(function(a,b){return a+b;},0) / intervals.length;
var tappedBPM = Math.round(60000 / avg);
updateBPM(tappedBPM);
// Restart if running to apply new BPM immediately
if (isRunning) {
stopMetronome();
startMetronome();
}
}
// Visual feedback
tapBtn.style.background = '#0f3460';
tapBtn.style.color = '#fff';
setTimeout(function() {
tapBtn.style.background = '';
tapBtn.style.color = '';
}, 100);
});

// Time signature buttons
timesigGrid.querySelectorAll('.timesig-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
timesigGrid.querySelectorAll('.timesig-btn').forEach(function(b){ b.classList.remove('selected'); });
this.classList.add('selected');
beatsPerMeasure = parseInt(this.getAttribute('data-beats'));
currentBeat = 0;
pendingFlashes = [];
renderBeatDots();
if (!isRunning) clearBeats();
});
});

// Volume
volSlider.addEventListener('input', function() {
volume = parseInt(this.value) / 100;
volPct.textContent = this.value + '%';
});

// BPM input via click on number
bpmNumEl.style.cursor = 'pointer';
bpmNumEl.title = 'Click to type BPM';
bpmNumEl.addEventListener('click', function() {
var val = prompt('Enter BPM (40–220):', bpm);
if (val !== null) {
var n = parseInt(val);
if (!isNaN(n)) updateBPM(n);
}
});

// --- Init ---
renderBeatDots();
updateBPM(120);
})();
</script>

</div>

---

## Related Tools

> [Noise Generator](/tools/noise-generator/)

