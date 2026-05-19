---
title: "Screen Recorder"
date: 2025-05-16
description: "Free online screen recorder. Record your screen, camera, or both using the browser's MediaRecorder API — download as WebM, no sign-up or install required."
categories: ["Free Tools"]
slug: "screen-recorder"
ShowToc: false
cover:
  image: "/images/covers/screen-recorder.png"
  alt: "Screen Recorder"
---

<div id="sr-app">

<style>
#sr-app {
font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
max-width: 800px;
margin: 0 auto;
color: #e2e8f0;
}

#sr-app * {
box-sizing: border-box;
}

#sr-app .sr-card {
background: #1e293b;
border: 1px solid #334155;
border-radius: 12px;
padding: 20px 24px;
margin-bottom: 16px;
}

#sr-app .sr-section-title {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #94a3b8;
margin: 0 0 14px 0;
}

/* Mode & Audio options */
#sr-app .sr-options {
display: flex;
flex-wrap: wrap;
gap: 10px;
}

#sr-app .sr-radio-label,
#sr-app .sr-check-label {
display: flex;
align-items: center;
gap: 8px;
cursor: pointer;
padding: 8px 14px;
border-radius: 8px;
border: 1px solid #334155;
background: #0f172a;
font-size: 0.875rem;
color: #cbd5e1;
transition: border-color 0.15s, background 0.15s;
user-select: none;
}

#sr-app .sr-radio-label:hover,
#sr-app .sr-check-label:hover {
border-color: #64748b;
background: #1e293b;
}

#sr-app .sr-radio-label input,
#sr-app .sr-check-label input {
accent-color: #6366f1;
width: 15px;
height: 15px;
cursor: pointer;
}

#sr-app .sr-radio-label.sr-selected {
border-color: #6366f1;
background: #1e1b4b;
color: #c7d2fe;
}

/* Controls row */
#sr-app .sr-controls {
display: flex;
flex-wrap: wrap;
align-items: center;
gap: 10px;
}

#sr-app .sr-btn {
padding: 10px 20px;
border: none;
border-radius: 8px;
font-size: 0.875rem;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
line-height: 1;
}

#sr-app .sr-btn:active {
transform: scale(0.97);
}

#sr-app .sr-btn:disabled {
opacity: 0.35;
cursor: not-allowed;
transform: none;
}

#sr-app .sr-btn-start {
background: #6366f1;
color: #fff;
}

#sr-app .sr-btn-start:hover:not(:disabled) {
background: #4f46e5;
}

#sr-app .sr-btn-stop {
background: #ef4444;
color: #fff;
}

#sr-app .sr-btn-stop:hover:not(:disabled) {
background: #dc2626;
}

#sr-app .sr-btn-pause {
background: #f59e0b;
color: #1c1917;
}

#sr-app .sr-btn-pause:hover:not(:disabled) {
background: #d97706;
}

#sr-app .sr-btn-download {
background: #10b981;
color: #fff;
}

#sr-app .sr-btn-download:hover:not(:disabled) {
background: #059669;
}

/* Timer & indicator */
#sr-app .sr-timer-wrap {
display: flex;
align-items: center;
gap: 10px;
margin-left: auto;
}

#sr-app .sr-dot {
width: 12px;
height: 12px;
border-radius: 50%;
background: #ef4444;
flex-shrink: 0;
opacity: 0;
}

#sr-app .sr-dot.sr-active {
opacity: 1;
animation: sr-blink 1s step-start infinite;
}

#sr-app .sr-dot.sr-paused {
opacity: 1;
animation: none;
background: #f59e0b;
}

@keyframes sr-blink {
0%, 100% { opacity: 1; }
50% { opacity: 0; }
}

#sr-app .sr-timer {
font-size: 1.25rem;
font-weight: 700;
font-variant-numeric: tabular-nums;
color: #f1f5f9;
letter-spacing: 0.05em;
min-width: 64px;
}

/* Video area */
#sr-app .sr-video-wrap {
position: relative;
background: #0f172a;
border-radius: 10px;
overflow: hidden;
aspect-ratio: 16 / 9;
border: 1px solid #334155;
}

#sr-app .sr-video-placeholder {
position: absolute;
inset: 0;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
gap: 10px;
color: #475569;
font-size: 0.875rem;
}

#sr-app .sr-video-placeholder svg {
opacity: 0.4;
}

#sr-app #sr-preview,
#sr-app #sr-playback {
width: 100%;
height: 100%;
object-fit: contain;
display: none;
background: #000;
}

#sr-app #sr-preview.sr-visible,
#sr-app #sr-playback.sr-visible {
display: block;
}

/* PiP camera overlay */
#sr-app #sr-cam-overlay {
position: absolute;
bottom: 12px;
right: 12px;
width: 22%;
aspect-ratio: 4/3;
border-radius: 8px;
overflow: hidden;
border: 2px solid #6366f1;
background: #000;
display: none;
}

#sr-app #sr-cam-overlay.sr-visible {
display: block;
}

#sr-app #sr-cam-overlay video {
width: 100%;
height: 100%;
object-fit: cover;
}

/* Download info */
#sr-app .sr-dl-info {
display: flex;
align-items: center;
gap: 14px;
flex-wrap: wrap;
}

#sr-app .sr-filesize {
font-size: 0.8rem;
color: #94a3b8;
}

/* Status message */
#sr-app .sr-status {
border-radius: 8px;
padding: 10px 14px;
font-size: 0.85rem;
line-height: 1.5;
display: none;
}

#sr-app .sr-status.sr-visible {
display: block;
}

#sr-app .sr-status.sr-info {
background: #1e3a5f;
border: 1px solid #2563eb;
color: #93c5fd;
}

#sr-app .sr-status.sr-error {
background: #3b1515;
border: 1px solid #ef4444;
color: #fca5a5;
}

#sr-app .sr-status.sr-success {
background: #052e16;
border: 1px solid #10b981;
color: #6ee7b7;
}

/* Cross-links */
#sr-app .sr-links {
border-top: 1px solid #334155;
padding-top: 16px;
font-size: 0.85rem;
color: #94a3b8;
line-height: 2;
}

#sr-app .sr-links a {
color: #818cf8;
text-decoration: none;
}

#sr-app .sr-links a:hover {
text-decoration: underline;
color: #a5b4fc;
}

@media (max-width: 520px) {
#sr-app .sr-timer-wrap {
margin-left: 0;
width: 100%;
justify-content: flex-end;
}

#sr-app .sr-btn {
flex: 1 1 auto;
text-align: center;
}
}
</style>

<!-- Mode selection -->
<div class="sr-card">
<p class="sr-section-title">Recording Mode</p>
<div class="sr-options" id="sr-mode-options">
<label class="sr-radio-label sr-selected" id="sr-lbl-screen">
<input type="radio" name="sr-mode" value="screen" checked> Screen only
</label>
<label class="sr-radio-label" id="sr-lbl-camera">
<input type="radio" name="sr-mode" value="camera"> Camera only
</label>
<label class="sr-radio-label" id="sr-lbl-both">
<input type="radio" name="sr-mode" value="both"> Screen + Camera (PiP)
</label>
</div>
</div>

<!-- Audio options -->
<div class="sr-card">
<p class="sr-section-title">Audio</p>
<div class="sr-options">
<label class="sr-check-label" id="sr-lbl-sysaudio">
<input type="checkbox" id="sr-sys-audio"> System audio (if supported)
</label>
<label class="sr-check-label" id="sr-lbl-mic">
<input type="checkbox" id="sr-mic"> Microphone
</label>
</div>
</div>

<!-- Controls -->
<div class="sr-card">
<div class="sr-controls">
<button class="sr-btn sr-btn-start" id="sr-btn-start">&#9679; Start Recording</button>
<button class="sr-btn sr-btn-stop" id="sr-btn-stop" disabled>&#9632; Stop</button>
<button class="sr-btn sr-btn-pause" id="sr-btn-pause" disabled>&#10074;&#10074; Pause</button>
<div class="sr-timer-wrap">
<span class="sr-dot" id="sr-dot"></span>
<span class="sr-timer" id="sr-timer">00:00</span>
</div>
</div>
</div>

<!-- Status -->
<div class="sr-status sr-info" id="sr-status"></div>

<!-- Video preview / playback -->
<div class="sr-card" style="padding: 0; overflow: hidden;">
<div class="sr-video-wrap" id="sr-video-wrap">
<div class="sr-video-placeholder" id="sr-placeholder">
<svg width="56" height="56" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round">
<rect x="2" y="7" width="15" height="10" rx="2"/>
<polygon points="22 12 17 7 17 17"/>
</svg>
<span>Preview will appear here when recording starts</span>
</div>
<video id="sr-preview" autoplay muted playsinline></video>
<video id="sr-playback" controls playsinline></video>
<div id="sr-cam-overlay">
<video id="sr-cam-pip" autoplay muted playsinline></video>
</div>
</div>
</div>

<!-- Download -->
<div class="sr-card" id="sr-dl-card" style="display:none;">
<p class="sr-section-title">Download Recording</p>
<div class="sr-dl-info">
<button class="sr-btn sr-btn-download" id="sr-btn-download">&#8595; Download WebM</button>
<span class="sr-filesize" id="sr-filesize"></span>
</div>
</div>

<!-- Cross-links -->
<div class="sr-card">
<div class="sr-links">
&gt; Draw on whiteboard &rarr; <a href="/tools/whiteboard-drawing/">Whiteboard Drawing Tool</a><br>
&gt; Create pixel art &rarr; <a href="/tools/pixel-art-editor/">Pixel Art Editor</a><br>
&gt; Generate placeholder images &rarr; <a href="/tools/placeholder-image/">Placeholder Image Generator</a>
</div>
</div>

<script>
(function () {
'use strict';

/* ── State ── */
var state = {
mode: 'screen',
recorder: null,
chunks: [],
screenStream: null,
cameraStream: null,
micStream: null,
combinedStream: null,
blobUrl: null,
blob: null,
timerInterval: null,
elapsed: 0,
recording: false,
paused: false,
};

/* ── Element refs ── */
var $ = function (id) { return document.getElementById(id); };
var btnStart   = $('sr-btn-start');
var btnStop    = $('sr-btn-stop');
var btnPause   = $('sr-btn-pause');
var btnDl      = $('sr-btn-download');
var dlCard     = $('sr-dl-card');
var timerEl    = $('sr-timer');
var dot        = $('sr-dot');
var status     = $('sr-status');
var preview    = $('sr-preview');
var playback   = $('sr-playback');
var placeholder = $('sr-placeholder');
var camOverlay = $('sr-cam-overlay');
var camPip     = $('sr-cam-pip');
var fileSizeEl = $('sr-filesize');
var modeLabels = {
screen: $('sr-lbl-screen'),
camera: $('sr-lbl-camera'),
both:   $('sr-lbl-both'),
};

/* ── Mode radio highlight ── */
var radios = document.querySelectorAll('#sr-mode-options input[type=radio]');
radios.forEach(function (r) {
r.addEventListener('change', function () {
state.mode = r.value;
Object.keys(modeLabels).forEach(function (k) {
modeLabels[k].classList.toggle('sr-selected', k === state.mode);
});
});
});

/* ── Helpers ── */
function padZ(n) { return String(n).padStart(2, '0'); }

function formatTime(secs) {
var m = Math.floor(secs / 60);
var s = secs % 60;
return padZ(m) + ':' + padZ(s);
}

function showStatus(msg, type) {
status.textContent = msg;
status.className = 'sr-status sr-visible ' + (type || 'sr-info');
}

function hideStatus() {
status.className = 'sr-status';
}

function formatBytes(bytes) {
if (bytes < 1024) return bytes + ' B';
if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + ' KB';
return (bytes / (1024 * 1024)).toFixed(2) + ' MB';
}

function startTimer() {
state.elapsed = 0;
timerEl.textContent = '00:00';
state.timerInterval = setInterval(function () {
if (!state.paused) {
state.elapsed++;
timerEl.textContent = formatTime(state.elapsed);
}
}, 1000);
}

function stopTimer() {
clearInterval(state.timerInterval);
state.timerInterval = null;
}

function resetStreams() {
if (state.screenStream) { state.screenStream.getTracks().forEach(function (t) { t.stop(); }); state.screenStream = null; }
if (state.cameraStream) { state.cameraStream.getTracks().forEach(function (t) { t.stop(); }); state.cameraStream = null; }
if (state.micStream) { state.micStream.getTracks().forEach(function (t) { t.stop(); }); state.micStream = null; }
state.combinedStream = null;
}

function setControlsRecording(active) {
btnStart.disabled = active;
btnStop.disabled  = !active;
btnPause.disabled = !active;
radios.forEach(function (r) { r.disabled = active; });
$('sr-sys-audio').disabled = active;
$('sr-mic').disabled       = active;
}

function showPreview(stream) {
placeholder.style.display = 'none';
playback.classList.remove('sr-visible');
preview.srcObject = stream;
preview.classList.add('sr-visible');
}

function showPlayback(url) {
preview.classList.remove('sr-visible');
preview.srcObject = null;
camOverlay.classList.remove('sr-visible');
playback.src = url;
playback.classList.add('sr-visible');
}

/* ── Best supported MIME type ── */
function getBestMime() {
var types = [
'video/webm;codecs=vp9,opus',
'video/webm;codecs=vp8,opus',
'video/webm;codecs=vp9',
'video/webm;codecs=vp8',
'video/webm',
];
for (var i = 0; i < types.length; i++) {
if (MediaRecorder.isTypeSupported(types[i])) return types[i];
}
return '';
}

/* ── Start Recording ── */
btnStart.addEventListener('click', async function () {
if (!navigator.mediaDevices || !navigator.mediaDevices.getDisplayMedia && state.mode !== 'camera') {
showStatus('Your browser does not support the required MediaDevices API. Please use Chrome, Edge, or Firefox.', 'sr-error');
return;
}
if (typeof MediaRecorder === 'undefined') {
showStatus('MediaRecorder API is not supported in this browser.', 'sr-error');
return;
}

hideStatus();
dlCard.style.display = 'none';
if (state.blobUrl) { URL.revokeObjectURL(state.blobUrl); state.blobUrl = null; }
state.chunks = [];
state.blob = null;
resetStreams();

var sysAudio = $('sr-sys-audio').checked;
var useMic   = $('sr-mic').checked;
var mode     = state.mode;

try {
/* Acquire streams based on mode */
if (mode === 'screen' || mode === 'both') {
if (!navigator.mediaDevices.getDisplayMedia) {
showStatus('getDisplayMedia is not supported in this browser. Try Chrome or Edge.', 'sr-error');
return;
}
state.screenStream = await navigator.mediaDevices.getDisplayMedia({
video: { cursor: 'always' },
audio: sysAudio ? true : false,
});
}

if (mode === 'camera' || mode === 'both') {
state.cameraStream = await navigator.mediaDevices.getUserMedia({
video: true,
audio: false,
});
}

if (useMic) {
state.micStream = await navigator.mediaDevices.getUserMedia({
audio: true,
video: false,
});
}

/* Build combined stream */
var tracks = [];

if (mode === 'screen') {
state.screenStream.getVideoTracks().forEach(function (t) { tracks.push(t); });
if (sysAudio) state.screenStream.getAudioTracks().forEach(function (t) { tracks.push(t); });
} else if (mode === 'camera') {
state.cameraStream.getVideoTracks().forEach(function (t) { tracks.push(t); });
} else if (mode === 'both') {
/* Screen video */
state.screenStream.getVideoTracks().forEach(function (t) { tracks.push(t); });
if (sysAudio) state.screenStream.getAudioTracks().forEach(function (t) { tracks.push(t); });
/* Camera shown in PiP overlay (separate video element) */
camPip.srcObject = state.cameraStream;
camOverlay.classList.add('sr-visible');
}

/* Mic audio */
if (useMic && state.micStream) {
state.micStream.getAudioTracks().forEach(function (t) { tracks.push(t); });
}

if (tracks.length === 0) {
showStatus('No media tracks were acquired. Please allow permissions.', 'sr-error');
resetStreams();
return;
}

state.combinedStream = new MediaStream(tracks);

/* Show preview */
var previewStream = state.screenStream || state.cameraStream;
showPreview(previewStream);

/* MediaRecorder */
var mime = getBestMime();
var recOpts = mime ? { mimeType: mime } : {};
state.recorder = new MediaRecorder(state.combinedStream, recOpts);

state.recorder.ondataavailable = function (e) {
if (e.data && e.data.size > 0) state.chunks.push(e.data);
};

state.recorder.onstop = function () {
var mimeType = mime || 'video/webm';
state.blob = new Blob(state.chunks, { type: mimeType });
state.blobUrl = URL.createObjectURL(state.blob);
showPlayback(state.blobUrl);
fileSizeEl.textContent = 'File size: ' + formatBytes(state.blob.size);
dlCard.style.display = 'block';
showStatus('Recording complete. Preview below — download when ready.', 'sr-success');
dot.className = 'sr-dot';
stopTimer();
setControlsRecording(false);
resetStreams();
state.recording = false;
state.paused = false;
btnPause.textContent = '\u23f8 Pause';
};

/* Handle user stopping share via browser UI */
state.screenStream && state.screenStream.getVideoTracks()[0] && (state.screenStream.getVideoTracks()[0].onended = function () {
if (state.recorder && state.recorder.state !== 'inactive') {
state.recorder.stop();
}
});

state.recorder.start(500); /* collect every 500ms */
state.recording = true;
state.paused = false;
setControlsRecording(true);
dot.className = 'sr-dot sr-active';
startTimer();
showStatus('Recording\u2026 Click Stop when done.', 'sr-info');

} catch (err) {
resetStreams();
var msg = err.message || String(err);
if (err.name === 'NotAllowedError' || err.name === 'PermissionDeniedError') {
showStatus('Permission denied. Please allow screen/camera access and try again.', 'sr-error');
} else if (err.name === 'NotFoundError') {
showStatus('No camera or microphone found on this device.', 'sr-error');
} else if (err.name === 'NotSupportedError') {
showStatus('This recording mode is not supported in your browser.', 'sr-error');
} else if (err.name === 'AbortError' || msg.toLowerCase().includes('cancel')) {
showStatus('Screen selection was cancelled.', 'sr-info');
} else {
showStatus('Error: ' + msg, 'sr-error');
}
}
});

/* ── Stop Recording ── */
btnStop.addEventListener('click', function () {
if (state.recorder && state.recorder.state !== 'inactive') {
state.recorder.stop();
}
});

/* ── Pause / Resume ── */
btnPause.addEventListener('click', function () {
if (!state.recorder) return;
if (state.recorder.state === 'recording') {
state.recorder.pause();
state.paused = true;
btnPause.textContent = '\u25b6 Resume';
dot.className = 'sr-dot sr-paused';
showStatus('Paused. Click Resume to continue.', 'sr-info');
} else if (state.recorder.state === 'paused') {
state.recorder.resume();
state.paused = false;
btnPause.textContent = '\u23f8 Pause';
dot.className = 'sr-dot sr-active';
showStatus('Recording\u2026 Click Stop when done.', 'sr-info');
}
});

/* ── Download ── */
btnDl.addEventListener('click', function () {
if (!state.blobUrl) return;
var a = document.createElement('a');
a.href = state.blobUrl;
var ts = new Date().toISOString().replace(/[:.]/g, '-').slice(0, 19);
a.download = 'recording-' + ts + '.webm';
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
});

/* ── Keyboard shortcut: Space to pause/resume while recording ── */
document.addEventListener('keydown', function (e) {
if (e.code === 'Space' && e.target === document.body && state.recording) {
e.preventDefault();
btnPause.click();
}
});

})();
</script>

</div>
