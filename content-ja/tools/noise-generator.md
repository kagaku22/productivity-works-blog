---
title: "ホワイトノイズジェネレーター"
date: 2026-01-04
description: "無料のホワイトノイズ生成ツール。ホワイト・ピンク・ブラウンノイズ＆雨音で集中・リラックス・睡眠をサポート。Web Audio API搭載、会員登録不要。"
categories: ["無料ツール"]
slug: "noise-generator"
ShowToc: false
cover:
  image: "/images/covers/noise-generator-ja.png"
  alt: "ホワイトノイズジェネレーター"
---

ブラウザだけで使えるホワイトノイズジェネレーターです。ホワイト・ピンク・ブラウンノイズと雨音を自由にミックスして、集中・リラックス・睡眠をサポートします。インストール不要・会員登録不要で今すぐ使えます。

<div id="ng-app">
<style>
#ng-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
max-width: 640px;
margin: 0 auto;
padding: 0;
color: #1e293b;
box-sizing: border-box;
}
#ng-app *, #ng-app *::before, #ng-app *::after {
box-sizing: inherit;
}
#ng-app .ng-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 14px;
padding: 22px 20px;
margin-bottom: 16px;
}
#ng-app .ng-title {
font-size: 18px;
font-weight: 700;
color: #0f172a;
margin: 0 0 18px 0;
letter-spacing: -0.3px;
}
#ng-app .ng-section-label {
font-size: 13px;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.5px;
margin-bottom: 14px;
}
#ng-app .ng-noise-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 14px;
padding: 12px 14px;
background: #ffffff;
border: 1px solid #e2e8f0;
border-radius: 10px;
transition: border-color 0.2s, box-shadow 0.2s;
}
#ng-app .ng-noise-row.active {
border-color: #7dd3fc;
box-shadow: 0 0 0 3px rgba(125, 211, 252, 0.15);
}
#ng-app .ng-noise-toggle {
appearance: none;
-webkit-appearance: none;
width: 40px;
height: 22px;
background: #cbd5e1;
border-radius: 11px;
position: relative;
cursor: pointer;
flex-shrink: 0;
transition: background 0.2s;
border: none;
outline: none;
}
#ng-app .ng-noise-toggle::after {
content: "";
position: absolute;
width: 16px;
height: 16px;
background: #fff;
border-radius: 50%;
top: 3px;
left: 3px;
transition: transform 0.2s;
box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
#ng-app .ng-noise-toggle:checked {
background: #0ea5e9;
}
#ng-app .ng-noise-toggle:checked::after {
transform: translateX(18px);
}
#ng-app .ng-noise-name {
font-size: 14px;
font-weight: 600;
color: #334155;
min-width: 110px;
flex-shrink: 0;
}
#ng-app .ng-noise-name small {
display: block;
font-size: 11px;
font-weight: 400;
color: #94a3b8;
margin-top: 1px;
}
#ng-app .ng-vol-slider {
flex: 1;
-webkit-appearance: none;
appearance: none;
height: 5px;
border-radius: 3px;
background: linear-gradient(to right, #0ea5e9 var(--val, 50%), #e2e8f0 var(--val, 50%));
outline: none;
cursor: pointer;
}
#ng-app .ng-vol-slider::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 17px;
height: 17px;
border-radius: 50%;
background: #0284c7;
cursor: pointer;
box-shadow: 0 1px 4px rgba(2,132,199,0.35);
transition: transform 0.15s;
}
#ng-app .ng-vol-slider::-webkit-slider-thumb:hover {
transform: scale(1.2);
}
#ng-app .ng-vol-slider::-moz-range-thumb {
width: 17px;
height: 17px;
border-radius: 50%;
background: #0284c7;
cursor: pointer;
border: none;
box-shadow: 0 1px 4px rgba(2,132,199,0.35);
}
#ng-app .ng-vol-value {
font-size: 12px;
color: #64748b;
min-width: 34px;
text-align: right;
flex-shrink: 0;
}
#ng-app .ng-master-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 14px;
}
#ng-app .ng-master-label {
font-size: 13px;
font-weight: 600;
color: #475569;
min-width: 90px;
flex-shrink: 0;
}
#ng-app .ng-play-btn {
display: flex;
align-items: center;
justify-content: center;
gap: 8px;
width: 100%;
padding: 13px 0;
background: #0284c7;
color: #fff;
border: none;
border-radius: 10px;
font-size: 16px;
font-weight: 700;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
margin-bottom: 14px;
letter-spacing: 0.2px;
}
#ng-app .ng-play-btn:hover {
background: #0369a1;
}
#ng-app .ng-play-btn:active {
transform: scale(0.98);
}
#ng-app .ng-play-btn.playing {
background: #64748b;
}
#ng-app .ng-play-btn.playing:hover {
background: #475569;
}
#ng-app .ng-timer-row {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
}
#ng-app .ng-timer-label {
font-size: 13px;
font-weight: 600;
color: #475569;
flex-shrink: 0;
}
#ng-app .ng-timer-btn {
padding: 6px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 20px;
background: #fff;
color: #475569;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#ng-app .ng-timer-btn:hover {
border-color: #7dd3fc;
color: #0369a1;
background: #f0f9ff;
}
#ng-app .ng-timer-btn.selected {
background: #0ea5e9;
border-color: #0ea5e9;
color: #fff;
}
#ng-app .ng-timer-display {
font-size: 13px;
font-weight: 700;
color: #0369a1;
margin-left: auto;
flex-shrink: 0;
}
#ng-app .ng-canvas-wrap {
background: #0f172a;
border-radius: 10px;
overflow: hidden;
margin-bottom: 0;
}
#ng-app canvas {
display: block;
width: 100%;
height: 80px;
}
#ng-app .ng-status {
text-align: center;
font-size: 12px;
color: #94a3b8;
margin-top: 10px;
}
@media (max-width: 480px) {
#ng-app .ng-noise-name {
min-width: 80px;
}
#ng-app .ng-play-btn {
font-size: 15px;
padding: 12px 0;
}
}
</style>

<div class="ng-card">
<div class="ng-title">ホワイトノイズジェネレーター</div>

<div class="ng-section-label">ノイズタイプ（個別音量・ON/OFF）</div>

<!-- White -->
<div class="ng-noise-row" id="ng-row-white">
<input type="checkbox" class="ng-noise-toggle" id="ng-tog-white" checked>
<div class="ng-noise-name">ホワイトノイズ<small>フラットスペクトル</small></div>
<input type="range" class="ng-vol-slider" id="ng-vol-white" min="0" max="100" value="50">
<div class="ng-vol-value" id="ng-vv-white">50%</div>
</div>

<!-- Pink -->
<div class="ng-noise-row" id="ng-row-pink">
<input type="checkbox" class="ng-noise-toggle" id="ng-tog-pink">
<div class="ng-noise-name">ピンクノイズ<small>1/f スペクトル</small></div>
<input type="range" class="ng-vol-slider" id="ng-vol-pink" min="0" max="100" value="50">
<div class="ng-vol-value" id="ng-vv-pink">50%</div>
</div>

<!-- Brown -->
<div class="ng-noise-row" id="ng-row-brown">
<input type="checkbox" class="ng-noise-toggle" id="ng-tog-brown">
<div class="ng-noise-name">ブラウンノイズ<small>1/f² スペクトル</small></div>
<input type="range" class="ng-vol-slider" id="ng-vol-brown" min="0" max="100" value="50">
<div class="ng-vol-value" id="ng-vv-brown">50%</div>
</div>

<!-- Rain -->
<div class="ng-noise-row" id="ng-row-rain">
<input type="checkbox" class="ng-noise-toggle" id="ng-tog-rain">
<div class="ng-noise-name">雨音<small>バンドパスフィルター</small></div>
<input type="range" class="ng-vol-slider" id="ng-vol-rain" min="0" max="100" value="50">
<div class="ng-vol-value" id="ng-vv-rain">50%</div>
</div>

<div class="ng-section-label" style="margin-top:8px;">マスターコントロール</div>

<!-- Master volume -->
<div class="ng-master-row">
<div class="ng-master-label">マスター音量</div>
<input type="range" class="ng-vol-slider" id="ng-master-vol" min="0" max="100" value="70">
<div class="ng-vol-value" id="ng-vv-master">70%</div>
</div>

<!-- Play button -->
<button class="ng-play-btn" id="ng-play-btn">
<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><polygon points="5,3 19,12 5,21"/></svg>
再生する
</button>

<!-- Timer -->
<div class="ng-timer-row">
<div class="ng-timer-label">タイマー:</div>
<button class="ng-timer-btn selected" data-min="0">OFF</button>
<button class="ng-timer-btn" data-min="15">15分</button>
<button class="ng-timer-btn" data-min="30">30分</button>
<button class="ng-timer-btn" data-min="60">60分</button>
<button class="ng-timer-btn" data-min="120">2時間</button>
<div class="ng-timer-display" id="ng-timer-display"></div>
</div>
</div>

<!-- Visualizer -->
<div class="ng-card" style="padding:14px 14px 14px;">
<div class="ng-section-label" style="margin-bottom:10px;">波形ビジュアライゼーション</div>
<div class="ng-canvas-wrap">
<canvas id="ng-canvas" height="80"></canvas>
</div>
<div class="ng-status" id="ng-status">再生ボタンを押してスタート</div>
</div>

<script>
(function() {
"use strict";

// --- State ---
var ctx = null;
var masterGain = null;
var analyser = null;
var animFrame = null;
var isPlaying = false;
var timerMinutes = 0;
var timerEndTime = null;
var timerInterval = null;

var noiseTypes = ["white", "pink", "brown", "rain"];
var nodes = {}; // per noise type: { processor, gainNode }

// Pink noise state (Voss-McCartney)
var pinkState = { b0:0, b1:0, b2:0, b3:0, b4:0, b5:0, b6:0 };
// Brown noise state
var brownState = { last: 0 };
// Rain filter state (ScriptProcessorNode + BiquadFilter)
var rainFilter = null;

// --- DOM refs ---
var playBtn = document.getElementById("ng-play-btn");
var masterSlider = document.getElementById("ng-master-vol");
var masterDisplay = document.getElementById("ng-vv-master");
var timerDisplay = document.getElementById("ng-timer-display");
var statusEl = document.getElementById("ng-status");
var canvas = document.getElementById("ng-canvas");
var canvasCtx = canvas.getContext("2d");

// --- Slider fill helper ---
function updateSliderFill(slider) {
var pct = ((slider.value - slider.min) / (slider.max - slider.min) * 100).toFixed(1) + "%";
slider.style.setProperty("--val", pct);
}

// --- Volume slider wiring ---
noiseTypes.forEach(function(type) {
var slider = document.getElementById("ng-vol-" + type);
var display = document.getElementById("ng-vv-" + type);
var toggle = document.getElementById("ng-tog-" + type);
var row = document.getElementById("ng-row-" + type);

updateSliderFill(slider);

slider.addEventListener("input", function() {
display.textContent = slider.value + "%";
updateSliderFill(slider);
if (nodes[type] && nodes[type].gainNode) {
nodes[type].gainNode.gain.setTargetAtTime(
parseFloat(slider.value) / 100 * (toggle.checked ? 1 : 0),
ctx.currentTime, 0.02
);
}
});

toggle.addEventListener("change", function() {
row.classList.toggle("active", toggle.checked);
if (nodes[type] && nodes[type].gainNode) {
var vol = parseFloat(slider.value) / 100;
nodes[type].gainNode.gain.setTargetAtTime(
toggle.checked ? vol : 0,
ctx.currentTime, 0.05
);
}
});

// Init active state
if (toggle.checked) row.classList.add("active");
});

masterSlider.addEventListener("input", function() {
masterDisplay.textContent = masterSlider.value + "%";
updateSliderFill(masterSlider);
if (masterGain) {
masterGain.gain.setTargetAtTime(
parseFloat(masterSlider.value) / 100,
ctx.currentTime, 0.02
);
}
});
updateSliderFill(masterSlider);

// --- Audio init ---
function initAudio() {
if (ctx) return;
ctx = new (window.AudioContext || window.webkitAudioContext)();
masterGain = ctx.createGain();
masterGain.gain.value = parseFloat(masterSlider.value) / 100;
masterGain.connect(ctx.destination);

analyser = ctx.createAnalyser();
analyser.fftSize = 1024;
analyser.smoothingTimeConstant = 0.8;
masterGain.connect(analyser);

createNoiseNodes();
}

function bufferSize() { return 4096; }

function createNoiseNodes() {
// White
nodes.white = createScriptNode(function(buf) {
for (var i = 0; i < buf.length; i++) {
buf[i] = Math.random() * 2 - 1;
}
}, "white");

// Pink (Voss-McCartney)
nodes.pink = createScriptNode(function(buf) {
var b0 = pinkState.b0, b1 = pinkState.b1, b2 = pinkState.b2,
b3 = pinkState.b3, b4 = pinkState.b4, b5 = pinkState.b5, b6 = pinkState.b6;
for (var i = 0; i < buf.length; i++) {
var white = Math.random() * 2 - 1;
b0 = 0.99886 * b0 + white * 0.0555179;
b1 = 0.99332 * b1 + white * 0.0750759;
b2 = 0.96900 * b2 + white * 0.1538520;
b3 = 0.86650 * b3 + white * 0.3104856;
b4 = 0.55000 * b4 + white * 0.5329522;
b5 = -0.7616 * b5 - white * 0.0168980;
var pink = b0 + b1 + b2 + b3 + b4 + b5 + b6 + white * 0.5362;
b6 = white * 0.115926;
buf[i] = pink * 0.11;
}
pinkState.b0 = b0; pinkState.b1 = b1; pinkState.b2 = b2;
pinkState.b3 = b3; pinkState.b4 = b4; pinkState.b5 = b5; pinkState.b6 = b6;
}, "pink");

// Brown (leaky integrator)
nodes.brown = createScriptNode(function(buf) {
var last = brownState.last;
for (var i = 0; i < buf.length; i++) {
var white = Math.random() * 2 - 1;
last = (last + 0.02 * white) / 1.02;
buf[i] = last * 3.5;
}
brownState.last = last;
}, "brown");

// Rain (bandpass filtered white noise)
var bpFilter = ctx.createBiquadFilter();
bpFilter.type = "bandpass";
bpFilter.frequency.value = 600;
bpFilter.Q.value = 0.8;
var bpFilter2 = ctx.createBiquadFilter();
bpFilter2.type = "bandpass";
bpFilter2.frequency.value = 1800;
bpFilter2.Q.value = 1.2;

var rainGainNode = ctx.createGain();
var rainVol = parseFloat(document.getElementById("ng-vol-rain").value) / 100;
var rainToggle = document.getElementById("ng-tog-rain");
rainGainNode.gain.value = rainToggle.checked ? rainVol : 0;
rainGainNode.connect(masterGain);

// Split signal to both bandpass filters
var rainMerge = ctx.createGain();
rainMerge.gain.value = 0.5;
bpFilter.connect(rainMerge);
bpFilter2.connect(rainMerge);
rainMerge.connect(rainGainNode);

var rainProc = ctx.createScriptProcessor(bufferSize(), 1, 1);
rainProc.onaudioprocess = function(e) {
if (!isPlaying) return;
var out = e.outputBuffer.getChannelData(0);
for (var i = 0; i < out.length; i++) {
out[i] = Math.random() * 2 - 1;
}
};
rainProc.connect(bpFilter);
rainProc.connect(bpFilter2);

nodes.rain = { processor: rainProc, gainNode: rainGainNode, filter: [bpFilter, bpFilter2], merge: rainMerge };
}

function createScriptNode(fillFn, type) {
var toggle = document.getElementById("ng-tog-" + type);
var volSlider = document.getElementById("ng-vol-" + type);
var gainNode = ctx.createGain();
gainNode.gain.value = toggle.checked ? parseFloat(volSlider.value) / 100 : 0;
gainNode.connect(masterGain);

var proc = ctx.createScriptProcessor(bufferSize(), 1, 1);
proc.onaudioprocess = function(e) {
if (!isPlaying) return;
var out = e.outputBuffer.getChannelData(0);
fillFn(out);
};
proc.connect(gainNode);
return { processor: proc, gainNode: gainNode };
}

// --- Play / Pause ---
playBtn.addEventListener("click", function() {
if (!isPlaying) {
startPlay();
} else {
stopPlay();
}
});

function startPlay() {
initAudio();
if (ctx.state === "suspended") ctx.resume();
isPlaying = true;
playBtn.classList.add("playing");
playBtn.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><rect x="6" y="4" width="4" height="16"/><rect x="14" y="4" width="4" height="16"/></svg> 一時停止';
statusEl.textContent = "再生中...";
drawWave();
startTimer();
}

function stopPlay() {
isPlaying = false;
playBtn.classList.remove("playing");
playBtn.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><polygon points="5,3 19,12 5,21"/></svg> 再生する';
statusEl.textContent = "一時停止中";
if (animFrame) { cancelAnimationFrame(animFrame); animFrame = null; }
clearInterval(timerInterval);
timerInterval = null;
timerEndTime = null;
timerDisplay.textContent = "";
// Clear canvas
canvasCtx.fillStyle = "#0f172a";
canvasCtx.fillRect(0, 0, canvas.width, canvas.height);
}

// --- Canvas wave ---
function drawWave() {
if (!isPlaying) return;
animFrame = requestAnimationFrame(drawWave);
var W = canvas.offsetWidth;
var H = canvas.offsetHeight;
if (canvas.width !== W) canvas.width = W;
if (canvas.height !== H || canvas.height < 1) canvas.height = 80;

var bufLen = analyser.frequencyBinCount;
var data = new Uint8Array(bufLen);
analyser.getByteTimeDomainData(data);

canvasCtx.fillStyle = "#0f172a";
canvasCtx.fillRect(0, 0, W, canvas.height);

canvasCtx.lineWidth = 2;
canvasCtx.strokeStyle = "#38bdf8";
canvasCtx.beginPath();
var sliceWidth = W / bufLen;
var x = 0;
for (var i = 0; i < bufLen; i++) {
var v = data[i] / 128.0;
var y = (v * canvas.height) / 2;
if (i === 0) canvasCtx.moveTo(x, y);
else canvasCtx.lineTo(x, y);
x += sliceWidth;
}
canvasCtx.lineTo(W, canvas.height / 2);
canvasCtx.stroke();
}

// --- Timer ---
document.querySelectorAll("#ng-app .ng-timer-btn").forEach(function(btn) {
btn.addEventListener("click", function() {
document.querySelectorAll("#ng-app .ng-timer-btn").forEach(function(b){ b.classList.remove("selected"); });
btn.classList.add("selected");
timerMinutes = parseInt(btn.dataset.min, 10);
if (isPlaying) {
clearInterval(timerInterval);
timerInterval = null;
timerEndTime = null;
timerDisplay.textContent = "";
startTimer();
}
});
});

function startTimer() {
clearInterval(timerInterval);
timerDisplay.textContent = "";
if (timerMinutes <= 0) return;
timerEndTime = Date.now() + timerMinutes * 60 * 1000;
updateTimerDisplay();
timerInterval = setInterval(function() {
var remaining = timerEndTime - Date.now();
if (remaining <= 0) {
stopPlay();
timerDisplay.textContent = "";
statusEl.textContent = "タイマー終了";
return;
}
updateTimerDisplay();
}, 1000);
}

function updateTimerDisplay() {
if (!timerEndTime) { timerDisplay.textContent = ""; return; }
var remaining = Math.max(0, timerEndTime - Date.now());
var h = Math.floor(remaining / 3600000);
var m = Math.floor((remaining % 3600000) / 60000);
var s = Math.floor((remaining % 60000) / 1000);
var parts = [];
if (h > 0) parts.push(h + "時間");
parts.push(pad(m) + "分");
parts.push(pad(s) + "秒");
timerDisplay.textContent = "残り " + parts.join("");
}

function pad(n) { return n < 10 ? "0" + n : "" + n; }

// Init canvas background
(function() {
canvas.width = canvas.offsetWidth || 600;
canvas.height = 80;
canvasCtx.fillStyle = "#0f172a";
canvasCtx.fillRect(0, 0, canvas.width, canvas.height);
// Draw idle center line
canvasCtx.strokeStyle = "#1e3a4a";
canvasCtx.lineWidth = 1;
canvasCtx.beginPath();
canvasCtx.moveTo(0, 40);
canvasCtx.lineTo(canvas.width, 40);
canvasCtx.stroke();
})();
})();
</script>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

</div>

> ポモドーロで集中 → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)
> タイピング速度を測定 → [タイピング速度テスト](/ja/tools/typing-speed-test/)
> ダミーテキストを生成 → [Lorem Ipsumジェネレーター](/ja/tools/lorem-ipsum-generator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
