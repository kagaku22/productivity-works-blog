---
title: "Color Vision Test - Check Your Color Perception"
description: "Test your color vision with an interactive Ishihara-style color blindness screening tool. Free online color perception test."
date: 2025-05-16
slug: "color-vision-test"
categories: ["Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/color-vision-test.png"
---

<div id="cvt-app">

<style>
#cvt-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 720px;
margin: 0 auto;
padding: 16px;
color: #1a1a2e;
}
#cvt-app h2 {
font-size: 1.5rem;
margin-bottom: 8px;
color: #1a1a2e;
}
#cvt-app p {
margin: 0 0 12px;
line-height: 1.6;
}
#cvt-app .cvt-disclaimer {
background: #fff8e1;
border-left: 4px solid #f9a825;
padding: 10px 14px;
border-radius: 4px;
font-size: 0.85rem;
margin-bottom: 20px;
color: #5d4037;
}
#cvt-app .cvt-plate-area {
display: flex;
flex-direction: column;
align-items: center;
gap: 16px;
margin-bottom: 20px;
}
#cvt-app .cvt-progress {
font-size: 0.9rem;
color: #555;
}
#cvt-app canvas#cvt-canvas {
border-radius: 50%;
border: 3px solid #ddd;
display: block;
max-width: 100%;
}
#cvt-app .cvt-question {
font-size: 1.05rem;
font-weight: 600;
text-align: center;
}
#cvt-app .cvt-input-row {
display: flex;
gap: 8px;
align-items: center;
flex-wrap: wrap;
justify-content: center;
}
#cvt-app input#cvt-answer {
border: 2px solid #ccc;
border-radius: 8px;
padding: 10px 14px;
font-size: 1.1rem;
width: 120px;
text-align: center;
outline: none;
transition: border-color 0.2s;
}
#cvt-app input#cvt-answer:focus {
border-color: #5c6bc0;
}
#cvt-app button.cvt-btn {
background: #5c6bc0;
color: #fff;
border: none;
border-radius: 8px;
padding: 10px 22px;
font-size: 1rem;
cursor: pointer;
transition: background 0.2s;
}
#cvt-app button.cvt-btn:hover {
background: #3949ab;
}
#cvt-app button.cvt-btn:disabled {
background: #aaa;
cursor: default;
}
#cvt-app .cvt-feedback {
font-size: 0.95rem;
min-height: 22px;
text-align: center;
font-weight: 600;
}
#cvt-app .cvt-feedback.correct { color: #2e7d32; }
#cvt-app .cvt-feedback.wrong   { color: #c62828; }
#cvt-app .cvt-result {
background: #f3f4ff;
border: 2px solid #5c6bc0;
border-radius: 12px;
padding: 24px;
text-align: center;
}
#cvt-app .cvt-result h3 {
margin: 0 0 10px;
font-size: 1.3rem;
color: #1a1a2e;
}
#cvt-app .cvt-score-num {
font-size: 2.8rem;
font-weight: 700;
color: #5c6bc0;
line-height: 1;
margin: 10px 0;
}
#cvt-app .cvt-interp {
margin: 12px 0;
padding: 12px;
border-radius: 8px;
background: #e8eaf6;
font-size: 0.97rem;
line-height: 1.6;
}
#cvt-app .cvt-detail-list {
text-align: left;
font-size: 0.9rem;
margin: 12px 0;
padding: 0 0 0 18px;
color: #333;
}
#cvt-app .cvt-detail-list li {
margin-bottom: 4px;
}
#cvt-app button#cvt-restart {
margin-top: 14px;
background: #5c6bc0;
color: #fff;
border: none;
border-radius: 8px;
padding: 10px 28px;
font-size: 1rem;
cursor: pointer;
transition: background 0.2s;
}
#cvt-app button#cvt-restart:hover {
background: #3949ab;
}
#cvt-app .cvt-related {
margin-top: 28px;
padding-top: 18px;
border-top: 1px solid #ddd;
font-size: 0.95rem;
}
#cvt-app .cvt-related h4 {
margin: 0 0 8px;
color: #333;
}
#cvt-app .cvt-related ul {
padding-left: 18px;
margin: 0;
}
#cvt-app .cvt-related ul li {
margin-bottom: 5px;
}
#cvt-app .cvt-hidden { display: none; }
</style>

<h2>Color Vision Test</h2>
<p>This Ishihara-style screening test checks how well you distinguish colors. Look at each plate and enter the number you see hidden in the pattern.</p>

<div class="cvt-disclaimer">
<strong>Disclaimer:</strong> This is a screening tool only. Results are not a medical diagnosis. Consult a qualified eye care professional for a formal evaluation.
</div>

<div id="cvt-test-area">
<div class="cvt-plate-area">
<div class="cvt-progress" id="cvt-progress">Plate 1 of 5</div>
<canvas id="cvt-canvas" width="300" height="300"></canvas>
<div class="cvt-question" id="cvt-question">What number do you see?</div>
<div class="cvt-input-row">
<input type="text" id="cvt-answer" maxlength="2" placeholder="0–99" autocomplete="off" />
<button class="cvt-btn" id="cvt-submit">Submit</button>
</div>
<div class="cvt-feedback" id="cvt-feedback"></div>
</div>
</div>

<div id="cvt-result-area" class="cvt-result cvt-hidden">
<h3>Your Results</h3>
<div class="cvt-score-num" id="cvt-score-display"></div>
<div style="font-size:1rem;color:#555;">out of 5 correct</div>
<div class="cvt-interp" id="cvt-interp"></div>
<ul class="cvt-detail-list" id="cvt-detail-list"></ul>
<div class="cvt-disclaimer" style="margin-top:14px;">
<strong>Reminder:</strong> This is a screening tool only. Consult an eye care professional for diagnosis.
</div>
<button id="cvt-restart">Take the Test Again</button>
</div>

<div class="cvt-related">
<h4>Related Free Tools</h4>
<ul>
<li><a href="/tools/typing-speed-test/">Reaction Time Test – Measure your reflexes</a></li>
<li><a href="/tools/reading-speed-calculator/">Reading Speed Test – Words per minute calculator</a></li>
<li><a href="/tools/pomodoro-timer/">Focus Timer – Pomodoro-style productivity timer</a></li>
</ul>
</div>

<script>
(function() {
// ── Plate definitions ──────────────────────────────────────────────
// Each plate: { number, fgColor, bgColor, deficiency, description }
// deficiency: what the plate tests for (informational)
var plates = [
{
number: 12,
fgColor: '#d44',   // red-ish
bgColor: '#8a6',   // green-ish
deficiency: 'protanopia/deuteranopia',
desc: 'Red-green (number visible to normal vision)'
},
{
number: 8,
fgColor: '#c84',   // orange-tan
bgColor: '#5a8',   // medium green
deficiency: 'deuteranopia',
desc: 'Red-green (orange vs green)'
},
{
number: 29,
fgColor: '#b55',   // muted red
bgColor: '#6a9',   // teal-green
deficiency: 'protanopia',
desc: 'Red vs teal'
},
{
number: 5,
fgColor: '#55b',   // blue-violet
bgColor: '#ba5',   // yellow-green
deficiency: 'tritanopia',
desc: 'Blue-yellow'
},
{
number: 74,
fgColor: '#c66',   // salmon
bgColor: '#7a5',   // olive green
deficiency: 'protanopia/deuteranopia',
desc: 'Red vs olive'
}
];

var current = 0;
var answers = [];   // { plate, userAnswer, correct }
var answered = false;

var canvas   = document.getElementById('cvt-canvas');
var ctx      = canvas.getContext('2d');
var progress = document.getElementById('cvt-progress');
var question = document.getElementById('cvt-question');
var input    = document.getElementById('cvt-answer');
var submitBtn= document.getElementById('cvt-submit');
var feedback = document.getElementById('cvt-feedback');
var testArea = document.getElementById('cvt-test-area');
var resultArea = document.getElementById('cvt-result-area');
var scoreDisplay = document.getElementById('cvt-score-display');
var interpEl   = document.getElementById('cvt-interp');
var detailList = document.getElementById('cvt-detail-list');
var restartBtn = document.getElementById('cvt-restart');

// ── Canvas plate generator ─────────────────────────────────────────
function hexToRgb(hex) {
var r = parseInt(hex.slice(1,3),16);
var g = parseInt(hex.slice(3,5),16);
var b = parseInt(hex.slice(5,7),16);
return [r,g,b];
}

function lerpColor(c1, c2, t) {
return [
Math.round(c1[0]*(1-t) + c2[0]*t),
Math.round(c1[1]*(1-t) + c2[1]*t),
Math.round(c1[2]*(1-t) + c2[2]*t)
];
}

function rgbStr(c) {
return 'rgb('+c[0]+','+c[1]+','+c[2]+')';
}

// Simple deterministic pseudo-random seeded by plate index
function seededRand(seed) {
var s = seed;
return function() {
s = (s * 1664525 + 1013904223) & 0xffffffff;
return (s >>> 0) / 0xffffffff;
};
}

// Draw a digit using a simple 5x7 pixel font bitmask
var FONT5x7 = {
'0': [0x1f,0x11,0x11,0x11,0x11,0x11,0x1f],
'1': [0x04,0x0c,0x04,0x04,0x04,0x04,0x0e],
'2': [0x1f,0x01,0x01,0x1f,0x10,0x10,0x1f],
'3': [0x1f,0x01,0x01,0x0f,0x01,0x01,0x1f],
'4': [0x11,0x11,0x11,0x1f,0x01,0x01,0x01],
'5': [0x1f,0x10,0x10,0x1f,0x01,0x01,0x1f],
'6': [0x1f,0x10,0x10,0x1f,0x11,0x11,0x1f],
'7': [0x1f,0x01,0x02,0x04,0x08,0x08,0x08],
'8': [0x1f,0x11,0x11,0x1f,0x11,0x11,0x1f],
'9': [0x1f,0x11,0x11,0x1f,0x01,0x01,0x1f]
};

function getDigitMask(numStr, W, H) {
// Returns a set of {x,y} pixel coords (normalized 0..1) that belong to digits
var digits = String(numStr);
var cellW = 5, cellH = 7;
var gap = 1;
var totalW = digits.length * cellW + (digits.length-1) * gap;
var startX = (W - totalW) / 2;
var startY = (H - cellH) / 2;
var pixels = new Set();
for (var di = 0; di < digits.length; di++) {
var rows = FONT5x7[digits[di]];
if (!rows) continue;
for (var row = 0; row < 7; row++) {
for (var col = 0; col < 5; col++) {
if (rows[row] & (0x10 >> col)) {
var px = startX + di*(cellW+gap) + col;
var py = startY + row;
pixels.add(px+'_'+py);
}
}
}
}
return { pixels: pixels, startX: startX, startY: startY, totalW: totalW, cellH: cellH };
}

function drawPlate(plate, plateIndex) {
var W = canvas.width, H = canvas.height;
var R = W / 2;
ctx.clearRect(0,0,W,H);

var rand = seededRand(plateIndex * 7919 + 13);

var fgRgb = hexToRgb(plate.fgColor);
var bgRgb = hexToRgb(plate.bgColor);

// Grid resolution for digit mask
var GRID = 9; // pixel-grid cell size in canvas px
var cols = Math.floor(W / GRID);
var rows = Math.floor(H / GRID);
var maskInfo = getDigitMask(plate.number, cols, rows);

// Draw filled circles
var numCircles = 900;
for (var i = 0; i < numCircles; i++) {
var angle = rand() * Math.PI * 2;
var dist  = Math.sqrt(rand()) * (R - 8);
var cx    = R + Math.cos(angle) * dist;
var cy    = R + Math.sin(angle) * dist;
var cr    = 4 + rand() * 9;

// Determine if circle center falls in digit region (grid coords)
var gx = Math.floor(cx / GRID);
var gy = Math.floor(cy / GRID);
var inDigit = maskInfo.pixels.has(gx+'_'+gy);

// Pick color: fg for digit, bg for background, with slight noise
var base = inDigit ? fgRgb : bgRgb;
var noise = rand() * 0.22 - 0.11;
var noiseRgb = [
Math.min(255,Math.max(0, base[0] + Math.round(noise*60))),
Math.min(255,Math.max(0, base[1] + Math.round(noise*60))),
Math.min(255,Math.max(0, base[2] + Math.round(noise*60)))
];

ctx.beginPath();
ctx.arc(cx, cy, cr, 0, Math.PI*2);
ctx.fillStyle = rgbStr(noiseRgb);
ctx.fill();
}

// Clip to circle
ctx.save();
ctx.globalCompositeOperation = 'destination-in';
ctx.beginPath();
ctx.arc(R, R, R-2, 0, Math.PI*2);
ctx.fillStyle = '#000';
ctx.fill();
ctx.restore();
}

// ── Test flow ──────────────────────────────────────────────────────
function loadPlate(idx) {
answered = false;
var plate = plates[idx];
progress.textContent = 'Plate ' + (idx+1) + ' of ' + plates.length;
question.textContent = 'What number do you see? (Enter 0 if you see nothing)';
input.value = '';
feedback.textContent = '';
feedback.className = 'cvt-feedback';
submitBtn.disabled = false;
input.disabled = false;
input.focus();
drawPlate(plate, idx);
}

function submitAnswer() {
if (answered) return;
var val = input.value.trim();
if (val === '') { feedback.textContent = 'Please enter a number (or 0).'; feedback.className='cvt-feedback wrong'; return; }
answered = true;
submitBtn.disabled = true;
input.disabled = true;

var plate = plates[current];
var correct = parseInt(val, 10) === plate.number;
answers.push({ plate: plate, userAnswer: val, correct: correct });

if (correct) {
feedback.textContent = 'Correct!';
feedback.className = 'cvt-feedback correct';
} else {
feedback.textContent = 'The number was ' + plate.number + '.';
feedback.className = 'cvt-feedback wrong';
}

setTimeout(function() {
current++;
if (current < plates.length) {
loadPlate(current);
} else {
showResult();
}
}, 1100);
}

function showResult() {
testArea.style.display = 'none';
resultArea.classList.remove('cvt-hidden');

var score = answers.filter(function(a){ return a.correct; }).length;
scoreDisplay.textContent = score + ' / ' + plates.length;

var interp;
if (score === 5) {
interp = 'Excellent! You identified all plates correctly. Your color vision appears to be functioning well in this screening.';
} else if (score >= 3) {
interp = 'You missed ' + (5-score) + ' plate(s). This may indicate mild difficulty distinguishing certain color combinations. Consider a professional evaluation.';
} else {
interp = 'You missed ' + (5-score) + ' plates. This suggests possible color vision deficiency. We strongly recommend consulting an eye care professional for a full assessment.';
}
interpEl.textContent = interp;

detailList.innerHTML = '';
answers.forEach(function(a, i) {
var li = document.createElement('li');
var icon = a.correct ? '✓' : '✗';
li.textContent = icon + ' Plate ' + (i+1) + ' (' + a.plate.desc + '): you said "' + a.userAnswer + '", answer was ' + a.plate.number;
li.style.color = a.correct ? '#2e7d32' : '#c62828';
detailList.appendChild(li);
});
}

function restart() {
current = 0;
answers = [];
answered = false;
resultArea.classList.add('cvt-hidden');
testArea.style.display = '';
loadPlate(0);
}

// ── Event listeners ────────────────────────────────────────────────
submitBtn.addEventListener('click', submitAnswer);
input.addEventListener('keydown', function(e) {
if (e.key === 'Enter') submitAnswer();
});
restartBtn.addEventListener('click', restart);

// Start
loadPlate(0);
})();
</script>

</div>

---

## Related Tools

> [Color Blindness Simulator](/tools/color-blindness-simulator/)
> [Color Contrast Checker](/tools/color-contrast-checker/)
> [Color Converter](/tools/color-converter/)

