---
title: "Universal Encoder/Decoder — Multi-Format Tool"
date: 2025-05-16
description: "Encode and decode text in multiple formats: Base64, URL, HTML entities, hex, binary, Unicode, and more. Bidirectional conversion with auto-detection. Free, client-side only."
categories: ["Free Tools"]
slug: "encoder-decoder"
ShowToc: false
aliases:
  - "/tools/encoder-decoder/"
  - "/tools/encoder-decoder/"
cover:
  image: "/images/covers/encoder-decoder.png"
  alt: "Universal Encoder/Decoder"
---

<div id="enc-app">

<style>
#enc-app {
font-family: ui-sans-serif, system-ui, -apple-system, sans-serif;
color: #e2e8f0;
max-width: 880px;
margin: 0 auto;
padding: 0;
}

#enc-app * {
box-sizing: border-box;
}

.enc-card {
background: #1e293b;
border: 1px solid #334155;
border-radius: 12px;
padding: 22px 24px;
margin-bottom: 14px;
}

.enc-section-title {
font-size: 15px;
font-weight: 700;
color: #cbd5e1;
margin-bottom: 14px;
display: flex;
align-items: center;
gap: 8px;
}

.enc-section-title::before {
content: '';
display: block;
width: 3px;
height: 16px;
background: #06b6d4;
border-radius: 2px;
flex-shrink: 0;
}

/* Mode selector row */
.enc-mode-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
align-items: center;
margin-bottom: 16px;
}

.enc-mode-label {
font-size: 13px;
font-weight: 600;
color: #94a3b8;
white-space: nowrap;
}

.enc-select {
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
color: #e2e8f0;
font-size: 14px;
padding: 8px 12px;
cursor: pointer;
outline: none;
transition: border-color 0.2s;
min-width: 220px;
}

.enc-select:focus {
border-color: #06b6d4;
}

.enc-auto-badge {
display: inline-block;
background: #164e63;
color: #67e8f9;
font-size: 11px;
font-weight: 700;
padding: 2px 9px;
border-radius: 10px;
letter-spacing: 0.03em;
margin-left: 4px;
vertical-align: middle;
}

/* Chain row */
.enc-chain-row {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 14px;
padding: 10px 14px;
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
}

.enc-chain-label {
font-size: 13px;
font-weight: 600;
color: #94a3b8;
white-space: nowrap;
}

.enc-chain-select {
background: #1e293b;
border: 1px solid #334155;
border-radius: 6px;
color: #e2e8f0;
font-size: 13px;
padding: 6px 10px;
cursor: pointer;
outline: none;
transition: border-color 0.2s;
}

.enc-chain-select:focus {
border-color: #06b6d4;
}

.enc-chain-arrow {
color: #475569;
font-size: 16px;
font-weight: 700;
}

/* Textarea area */
.enc-textarea-label {
font-size: 13px;
font-weight: 600;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 7px;
display: flex;
justify-content: space-between;
align-items: center;
}

.enc-char-count {
font-size: 12px;
font-weight: 400;
color: #64748b;
text-transform: none;
letter-spacing: 0;
}

.enc-textarea {
width: 100%;
min-height: 140px;
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
color: #e2e8f0;
font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
font-size: 14px;
line-height: 1.6;
padding: 12px;
resize: vertical;
transition: border-color 0.2s;
outline: none;
}

.enc-textarea:focus {
border-color: #06b6d4;
}

.enc-textarea.enc-error-border {
border-color: #f87171;
}

.enc-textarea::placeholder {
color: #475569;
}

/* Button rows */
.enc-btn-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin: 14px 0 0;
align-items: center;
}

.enc-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 9px 20px;
border-radius: 8px;
font-size: 14px;
font-weight: 600;
cursor: pointer;
border: none;
transition: background 0.15s, transform 0.1s, opacity 0.15s;
white-space: nowrap;
outline: none;
}

.enc-btn:active {
transform: scale(0.97);
}

.enc-btn-primary {
background: #06b6d4;
color: #0f172a;
}

.enc-btn-primary:hover {
background: #22d3ee;
}

.enc-btn-violet {
background: #7c3aed;
color: #fff;
}

.enc-btn-violet:hover {
background: #8b5cf6;
}

.enc-btn-secondary {
background: #475569;
color: #e2e8f0;
}

.enc-btn-secondary:hover {
background: #64748b;
}

.enc-btn-ghost {
background: transparent;
color: #94a3b8;
border: 1px solid #334155;
}

.enc-btn-ghost:hover {
background: #1e293b;
color: #e2e8f0;
border-color: #475569;
}

.enc-btn-success {
background: #10b981 !important;
color: #fff !important;
}

/* Swap row */
.enc-swap-row {
display: flex;
align-items: center;
justify-content: center;
margin: 4px 0;
}

.enc-swap-btn {
display: flex;
align-items: center;
gap: 6px;
padding: 7px 16px;
background: #1e293b;
border: 1px solid #334155;
border-radius: 20px;
color: #94a3b8;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}

.enc-swap-btn:hover {
background: #334155;
color: #e2e8f0;
border-color: #475569;
}

/* Error */
.enc-error {
background: #450a0a;
border: 1px solid #f87171;
border-radius: 8px;
color: #fca5a5;
font-size: 13px;
padding: 10px 14px;
margin-top: 10px;
display: none;
}

.enc-error.visible {
display: block;
}

/* History */
.enc-history-list {
list-style: none;
margin: 0;
padding: 0;
display: flex;
flex-direction: column;
gap: 8px;
}

.enc-history-item {
background: #0f172a;
border: 1px solid #1e293b;
border-radius: 8px;
padding: 10px 14px;
font-size: 13px;
cursor: pointer;
transition: border-color 0.15s, background 0.15s;
display: flex;
flex-direction: column;
gap: 3px;
}

.enc-history-item:hover {
border-color: #334155;
background: #1e293b;
}

.enc-history-meta {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
}

.enc-history-mode-badge {
display: inline-block;
background: #1e3a5f;
color: #7dd3fc;
font-size: 11px;
font-weight: 700;
padding: 2px 8px;
border-radius: 6px;
}

.enc-history-dir-badge {
display: inline-block;
font-size: 11px;
font-weight: 700;
padding: 2px 7px;
border-radius: 6px;
}

.enc-history-dir-badge.enc {
background: #14532d;
color: #86efac;
}

.enc-history-dir-badge.dec {
background: #3b1f6e;
color: #c4b5fd;
}

.enc-history-text {
color: #94a3b8;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
font-family: ui-monospace, Menlo, monospace;
font-size: 12px;
}

.enc-history-empty {
color: #475569;
font-size: 13px;
font-style: italic;
}

/* Auto-detect toggle */
.enc-toggle-row {
display: flex;
flex-wrap: wrap;
gap: 14px;
align-items: center;
padding-top: 12px;
border-top: 1px solid #1e293b;
margin-top: 14px;
}

.enc-toggle-item {
display: flex;
align-items: center;
gap: 8px;
cursor: pointer;
user-select: none;
}

.enc-toggle-item input[type="checkbox"] {
appearance: none;
-webkit-appearance: none;
width: 36px;
height: 20px;
background: #334155;
border-radius: 10px;
position: relative;
cursor: pointer;
transition: background 0.2s;
flex-shrink: 0;
}

.enc-toggle-item input[type="checkbox"]:checked {
background: #06b6d4;
}

.enc-toggle-item input[type="checkbox"]::after {
content: '';
position: absolute;
width: 14px;
height: 14px;
background: #fff;
border-radius: 50%;
top: 3px;
left: 3px;
transition: left 0.2s;
}

.enc-toggle-item input[type="checkbox"]:checked::after {
left: 19px;
}

.enc-toggle-label-text {
font-size: 13px;
color: #94a3b8;
}

@media (max-width: 600px) {
.enc-card {
padding: 16px;
}
.enc-btn {
padding: 8px 14px;
font-size: 13px;
}
.enc-textarea {
min-height: 110px;
font-size: 13px;
}
.enc-btn-row {
gap: 8px;
}
.enc-select {
min-width: 0;
width: 100%;
}
.enc-mode-row {
flex-direction: column;
align-items: flex-start;
}
}
</style>

<!-- MODE SELECTOR + AUTO-DETECT -->
<div class="enc-card">
<div class="enc-section-title">Encoding Format</div>

<div class="enc-mode-row">
<span class="enc-mode-label">Format:</span>
<select class="enc-select" id="enc-mode">
<option value="base64">Base64</option>
<option value="url">URL Encode</option>
<option value="html">HTML Entities</option>
<option value="hex">Hex</option>
<option value="binary">Binary</option>
<option value="octal">Octal</option>
<option value="ascii">ASCII Codes</option>
<option value="unicode">Unicode Escape (\uXXXX)</option>
<option value="jwt">JWT Decode (header.payload)</option>
</select>
</div>

<!-- Chain encoding -->
<div class="enc-chain-row">
<span class="enc-chain-label">Chain:</span>
<select class="enc-chain-select" id="enc-chain-1">
<option value="none">— Step 1 —</option>
<option value="base64">Base64</option>
<option value="url">URL Encode</option>
<option value="html">HTML Entities</option>
<option value="hex">Hex</option>
<option value="binary">Binary</option>
<option value="unicode">Unicode Escape</option>
</select>
<span class="enc-chain-arrow">&#8594;</span>
<select class="enc-chain-select" id="enc-chain-2">
<option value="none">— Step 2 —</option>
<option value="base64">Base64</option>
<option value="url">URL Encode</option>
<option value="html">HTML Entities</option>
<option value="hex">Hex</option>
<option value="binary">Binary</option>
<option value="unicode">Unicode Escape</option>
</select>
<button class="enc-btn enc-btn-violet" id="enc-chain-run-btn">Run Chain</button>
</div>

<div class="enc-toggle-row">
<label class="enc-toggle-item">
<input type="checkbox" id="enc-auto-detect">
<span class="enc-toggle-label-text">Auto-detect format <span class="enc-auto-badge" id="enc-auto-indicator" style="display:none;">AUTO</span></span>
</label>
</div>
</div>

<!-- INPUT -->
<div class="enc-card">
<div class="enc-textarea-label">
<span>Input</span>
<span class="enc-char-count" id="enc-input-count">0 chars</span>
</div>
<textarea
class="enc-textarea"
id="enc-input"
placeholder="Type or paste text here..."
spellcheck="false"
></textarea>

<div class="enc-btn-row">
<button class="enc-btn enc-btn-primary" id="enc-encode-btn">Encode</button>
<button class="enc-btn enc-btn-primary" id="enc-decode-btn">Decode</button>
<button class="enc-btn enc-btn-ghost" id="enc-clear-btn">Clear</button>
</div>
</div>

<!-- SWAP -->
<div class="enc-swap-row">
<button class="enc-swap-btn" id="enc-swap-btn">&#8645; Swap Input / Output</button>
</div>

<!-- OUTPUT -->
<div class="enc-card">
<div class="enc-textarea-label">
<span>Output</span>
<span class="enc-char-count" id="enc-output-count">0 chars</span>
</div>
<textarea
class="enc-textarea"
id="enc-output"
placeholder="Result will appear here..."
spellcheck="false"
readonly
></textarea>

<div class="enc-error" id="enc-error-msg"></div>

<div class="enc-btn-row">
<button class="enc-btn enc-btn-secondary" id="enc-copy-btn">Copy Output</button>
</div>
</div>

<!-- HISTORY -->
<div class="enc-card">
<div class="enc-section-title">Recent Conversions (Last 5)</div>
<ul class="enc-history-list" id="enc-history-list">
<li class="enc-history-empty">No conversions yet.</li>
</ul>
</div>

<script>
(function () {
'use strict';

/* ── DOM refs ── */
var inputEl     = document.getElementById('enc-input');
var outputEl    = document.getElementById('enc-output');
var inputCnt    = document.getElementById('enc-input-count');
var outputCnt   = document.getElementById('enc-output-count');
var errorEl     = document.getElementById('enc-error-msg');
var modeSelect  = document.getElementById('enc-mode');
var encodeBtn   = document.getElementById('enc-encode-btn');
var decodeBtn   = document.getElementById('enc-decode-btn');
var clearBtn    = document.getElementById('enc-clear-btn');
var swapBtn     = document.getElementById('enc-swap-btn');
var copyBtn     = document.getElementById('enc-copy-btn');
var autoDetect  = document.getElementById('enc-auto-detect');
var autoInd     = document.getElementById('enc-auto-indicator');
var chain1      = document.getElementById('enc-chain-1');
var chain2      = document.getElementById('enc-chain-2');
var chainRunBtn = document.getElementById('enc-chain-run-btn');
var historyList = document.getElementById('enc-history-list');

/* ── History ── */
var history = [];

function addHistory(mode, direction, input, output) {
history.unshift({ mode: mode, dir: direction, input: input, output: output });
if (history.length > 5) history = history.slice(0, 5);
renderHistory();
}

function renderHistory() {
if (history.length === 0) {
historyList.innerHTML = '<li class="enc-history-empty">No conversions yet.</li>';
return;
}
historyList.innerHTML = history.map(function (h, i) {
var dirCls  = h.dir === 'encode' ? 'enc' : 'dec';
var dirText = h.dir === 'encode' ? 'ENC' : 'DEC';
var preview = (h.input || '').substring(0, 60) + (h.input.length > 60 ? '…' : '');
return '<li class="enc-history-item" data-idx="' + i + '">' +
'<div class="enc-history-meta">' +
'<span class="enc-history-mode-badge">' + h.mode.toUpperCase() + '</span>' +
'<span class="enc-history-dir-badge ' + dirCls + '">' + dirText + '</span>' +
'</div>' +
'<div class="enc-history-text">' + escapeHtml(preview) + '</div>' +
'</li>';
}).join('');

historyList.querySelectorAll('.enc-history-item').forEach(function (el) {
el.addEventListener('click', function () {
var idx = parseInt(this.getAttribute('data-idx'), 10);
var h = history[idx];
if (h) {
inputEl.value  = h.input;
outputEl.value = h.output;
modeSelect.value = h.mode;
updateCounts();
clearError();
}
});
});
}

function escapeHtml(str) {
return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

/* ── Counts ── */
function updateCounts() {
inputCnt.textContent  = inputEl.value.length.toLocaleString() + ' chars';
outputCnt.textContent = outputEl.value.length.toLocaleString() + ' chars';
}

/* ── Error ── */
function showError(msg) {
errorEl.textContent = msg;
errorEl.classList.add('visible');
outputEl.classList.add('enc-error-border');
}

function clearError() {
errorEl.textContent = '';
errorEl.classList.remove('visible');
outputEl.classList.remove('enc-error-border');
}

function setOutput(val) {
outputEl.value = val;
updateCounts();
}

/* ══════════════════════════════════════════
ENCODING FUNCTIONS
══════════════════════════════════════════ */

function encodeBase64(str) {
return btoa(unescape(encodeURIComponent(str)));
}

function decodeBase64(str) {
var raw = str.trim().replace(/^data:[^;]+;base64,/, '');
raw = raw.replace(/-/g, '+').replace(/_/g, '/');
while (raw.length % 4 !== 0) raw += '=';
return decodeURIComponent(escape(atob(raw)));
}

function encodeUrl(str) {
return encodeURIComponent(str);
}

function decodeUrl(str) {
return decodeURIComponent(str.replace(/\+/g, ' '));
}

function encodeHtml(str) {
return str
.replace(/&/g, '&amp;')
.replace(/</g, '&lt;')
.replace(/>/g, '&gt;')
.replace(/"/g, '&quot;')
.replace(/'/g, '&#39;')
.replace(/\//g, '&#47;');
}

function decodeHtml(str) {
var txt = document.createElement('textarea');
txt.innerHTML = str;
return txt.value;
}

function encodeHex(str) {
var result = '';
for (var i = 0; i < str.length; i++) {
var code = str.charCodeAt(i);
result += (code < 256 ? '' : '\\u') + code.toString(16).padStart(code < 256 ? 2 : 4, '0') + ' ';
}
return result.trim();
}

function decodeHex(str) {
return str.trim().split(/\s+/).map(function (token) {
var code = parseInt(token.replace(/^\\u/, ''), 16);
if (isNaN(code)) throw new Error('Invalid hex token: ' + token);
return String.fromCharCode(code);
}).join('');
}

function encodeBinary(str) {
var result = [];
for (var i = 0; i < str.length; i++) {
result.push(str.charCodeAt(i).toString(2).padStart(8, '0'));
}
return result.join(' ');
}

function decodeBinary(str) {
return str.trim().split(/\s+/).map(function (b) {
var code = parseInt(b, 2);
if (isNaN(code)) throw new Error('Invalid binary sequence: ' + b);
return String.fromCharCode(code);
}).join('');
}

function encodeOctal(str) {
var result = [];
for (var i = 0; i < str.length; i++) {
result.push('\\' + str.charCodeAt(i).toString(8).padStart(3, '0'));
}
return result.join(' ');
}

function decodeOctal(str) {
return str.trim().split(/\s+/).map(function (o) {
var clean = o.replace(/^\\/, '');
var code = parseInt(clean, 8);
if (isNaN(code)) throw new Error('Invalid octal token: ' + o);
return String.fromCharCode(code);
}).join('');
}

function encodeAscii(str) {
var result = [];
for (var i = 0; i < str.length; i++) {
result.push(str.charCodeAt(i));
}
return result.join(' ');
}

function decodeAscii(str) {
return str.trim().split(/\s+/).map(function (n) {
var code = parseInt(n, 10);
if (isNaN(code)) throw new Error('Invalid ASCII code: ' + n);
return String.fromCharCode(code);
}).join('');
}

function encodeUnicode(str) {
var result = '';
for (var i = 0; i < str.length; i++) {
var code = str.charCodeAt(i);
if (code > 127) {
result += '\\u' + code.toString(16).toUpperCase().padStart(4, '0');
} else {
result += str[i];
}
}
return result;
}

function decodeUnicode(str) {
return str.replace(/\\u([0-9a-fA-F]{4})/g, function (_, hex) {
return String.fromCharCode(parseInt(hex, 16));
});
}

function decodeJwt(str) {
var parts = str.trim().split('.');
if (parts.length < 2) throw new Error('Not a valid JWT: expected at least two dot-separated parts.');
function decodeSegment(seg) {
seg = seg.replace(/-/g, '+').replace(/_/g, '/');
while (seg.length % 4 !== 0) seg += '=';
return JSON.parse(decodeURIComponent(escape(atob(seg))));
}
var header  = decodeSegment(parts[0]);
var payload = decodeSegment(parts[1]);
return JSON.stringify({ header: header, payload: payload }, null, 2);
}

/* ── Dispatch encode/decode by mode ── */
function runEncode(text, mode) {
switch (mode) {
case 'base64':  return encodeBase64(text);
case 'url':     return encodeUrl(text);
case 'html':    return encodeHtml(text);
case 'hex':     return encodeHex(text);
case 'binary':  return encodeBinary(text);
case 'octal':   return encodeOctal(text);
case 'ascii':   return encodeAscii(text);
case 'unicode': return encodeUnicode(text);
case 'jwt':     throw new Error('JWT is decode-only. Switch to another format for encoding.');
default: throw new Error('Unknown mode: ' + mode);
}
}

function runDecode(text, mode) {
switch (mode) {
case 'base64':  return decodeBase64(text);
case 'url':     return decodeUrl(text);
case 'html':    return decodeHtml(text);
case 'hex':     return decodeHex(text);
case 'binary':  return decodeBinary(text);
case 'octal':   return decodeOctal(text);
case 'ascii':   return decodeAscii(text);
case 'unicode': return decodeUnicode(text);
case 'jwt':     return decodeJwt(text);
default: throw new Error('Unknown mode: ' + mode);
}
}

/* ── Auto-detect ── */
function detectMode(str) {
var s = str.trim();
if (/^[A-Za-z0-9\-_]+\.[A-Za-z0-9\-_]+\.[A-Za-z0-9\-_]*$/.test(s)) return 'jwt';
if (/^[A-Za-z0-9+/\-_]+=*$/.test(s) && s.length % 4 === 0 && s.length > 3) return 'base64';
if (/%[0-9A-Fa-f]{2}/.test(s)) return 'url';
if (/&(amp|lt|gt|quot|#\d+|#x[0-9a-fA-F]+);/.test(s)) return 'html';
if (/^([01]{8}\s*)+$/.test(s)) return 'binary';
if (/^(\\[0-7]{3}\s*)+$/.test(s)) return 'octal';
if (/^([0-9a-fA-F]{2}\s*)+$/.test(s)) return 'hex';
if (/^(\d{1,3}\s*)+$/.test(s) && s.trim().split(/\s+/).every(function(n){var v=parseInt(n,10);return !isNaN(v)&&v>=0&&v<=127;})) return 'ascii';
if (/\\u[0-9a-fA-F]{4}/.test(s)) return 'unicode';
return null;
}

/* ── Main actions ── */
function doEncode() {
clearError();
var text = inputEl.value;
var mode = modeSelect.value;
if (!text) { setOutput(''); return; }
try {
var result = runEncode(text, mode);
setOutput(result);
addHistory(mode, 'encode', text, result);
} catch (e) {
showError('Encode error: ' + e.message);
setOutput('');
}
}

function doDecode() {
clearError();
var text = inputEl.value;
var mode = modeSelect.value;
if (!text) { setOutput(''); return; }
try {
var result = runDecode(text, mode);
setOutput(result);
addHistory(mode, 'decode', text, result);
} catch (e) {
showError('Decode error: ' + e.message);
setOutput('');
}
}

/* ── Chain encoding ── */
function doChain() {
clearError();
var text = inputEl.value;
if (!text) { setOutput(''); return; }
var steps = [chain1.value, chain2.value].filter(function(v){ return v !== 'none'; });
if (steps.length === 0) {
showError('Select at least one step in the chain.');
return;
}
try {
var current = text;
steps.forEach(function (step) {
current = runEncode(current, step);
});
setOutput(current);
addHistory(steps.join('+'), 'encode', text, current);
} catch (e) {
showError('Chain error: ' + e.message);
setOutput('');
}
}

/* ── Auto-detect handler ── */
function runAutoDetect() {
var text = inputEl.value.trim();
if (!text) return;
var detected = detectMode(text);
if (detected) {
modeSelect.value = detected;
doDecode();
}
}

/* ── Copy ── */
function doCopy() {
var val = outputEl.value;
if (!val) return;
navigator.clipboard.writeText(val).then(function () {
flashCopy();
}).catch(function () {
var ta = document.createElement('textarea');
ta.value = val;
ta.style.position = 'fixed';
ta.style.opacity  = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
flashCopy();
});
}

function flashCopy() {
var orig = copyBtn.textContent;
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('enc-btn-success');
setTimeout(function () {
copyBtn.textContent = orig;
copyBtn.classList.remove('enc-btn-success');
}, 1800);
}

/* ── Event listeners ── */
encodeBtn.addEventListener('click', doEncode);
decodeBtn.addEventListener('click', doDecode);
chainRunBtn.addEventListener('click', doChain);

clearBtn.addEventListener('click', function () {
inputEl.value  = '';
setOutput('');
clearError();
});

swapBtn.addEventListener('click', function () {
var tmp = inputEl.value;
inputEl.value  = outputEl.value;
outputEl.value = tmp;
clearError();
updateCounts();
});

copyBtn.addEventListener('click', doCopy);

autoDetect.addEventListener('change', function () {
autoInd.style.display = this.checked ? 'inline-block' : 'none';
if (this.checked) runAutoDetect();
});

inputEl.addEventListener('input', function () {
updateCounts();
clearError();
if (autoDetect.checked) runAutoDetect();
});

renderHistory();
updateCounts();
})();
</script>

</div>

---

## What is an Encoder/Decoder?

Encoding transforms text or binary data into a different representation so it can be safely transported, stored, or embedded in a target medium. Decoding reverses the process to recover the original content. Unlike encryption, encoding is not a security mechanism — the transformation is entirely reversible and publicly defined. Common uses include transmitting binary data over text-based protocols, embedding special characters safely in HTML or URLs, and inspecting authentication tokens.

## Supported Formats

| Format | Encode example | Use case |
|--------|---------------|----------|
| **Base64** | `Hello` → `SGVsbG8=` | Email attachments, data URIs, JWT |
| **URL Encode** | `a b` → `a%20b` | Query strings, form data |
| **HTML Entities** | `<b>` → `&lt;b&gt;` | Safe HTML output |
| **Hex** | `A` → `41` | Debugging, binary inspection |
| **Binary** | `A` → `01000001` | Low-level analysis |
| **Octal** | `A` → `\101` | Unix file permissions, C escape sequences |
| **ASCII Codes** | `Hi` → `72 105` | Protocol debugging |
| **Unicode Escape** | `©` → `\u00A9` | JavaScript source, JSON |
| **JWT Decode** | `eyJ…` → header + payload JSON | Inspect tokens without a library |

## Chain Encoding

The chain feature applies two encoding steps in sequence. For example, selecting **Hex → Base64** first converts each character to its hex code, then Base64-encodes the result. This is useful for simulating multi-layer encoding found in obfuscated payloads or CTF challenges.

---

### Related Tools

> Encode Base64 → [Base64 Encoder](/tools/base64-encoder/)

> Encode URLs → [URL Encoder](/tools/url-encoder/)

> Encode HTML entities → [HTML Entity Encoder](/tools/html-entity-encoder/)
