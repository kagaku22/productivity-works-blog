---
title: "万能エンコーダー/デコーダー — マルチフォーマット変換"
date: 2025-09-04
description: "複数形式でテキストをエンコード・デコード。Base64・URL・HTMLエンティティ・16進数・2進数・Unicode等。双方向変換・自動検出。無料・クライアントサイド処理。"
categories: ["無料ツール"]
tags: ["開発ツール", "コード変換", "無料ツール"]
slug: "encoder-decoder"
ShowToc: false
aliases:
  - "/ja/tools/encoder-decoder/"
  - "/ja/tools/encoder-decoder/"
cover:
  image: "/images/covers/encoder-decoder-ja.png"
  alt: "万能エンコーダー/デコーダー"
---

<div id="enc-app">

<style>
#enc-app {
font-family: 'Hiragino Sans', 'Yu Gothic UI', 'Meiryo', ui-sans-serif, system-ui, sans-serif;
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

/* モード選択行 */
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
min-width: 240px;
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

/* チェーン行 */
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

/* テキストエリア */
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
font-family: ui-monospace, 'Courier New', Consolas, monospace;
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

/* ボタン */
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
transition: background 0.15s, transform 0.1s;
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

/* スワップ */
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

/* エラー */
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

/* 履歴 */
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

/* トグル */
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
.enc-chain-row {
flex-direction: column;
align-items: flex-start;
}
}
</style>

<!-- フォーマット選択 -->
<div class="enc-card">
<div class="enc-section-title">エンコード形式の選択</div>

<div class="enc-mode-row">
<span class="enc-mode-label">形式：</span>
<select class="enc-select" id="enc-mode">
<option value="base64">Base64</option>
<option value="url">URLエンコード</option>
<option value="html">HTMLエンティティ</option>
<option value="hex">16進数（Hex）</option>
<option value="binary">2進数（Binary）</option>
<option value="octal">8進数（Octal）</option>
<option value="ascii">ASCIIコード</option>
<option value="unicode">Unicodeエスケープ（\uXXXX）</option>
<option value="jwt">JWTデコード（ヘッダー＋ペイロード）</option>
</select>
</div>

<!-- チェーンエンコード -->
<div class="enc-chain-row">
<span class="enc-chain-label">チェーン：</span>
<select class="enc-chain-select" id="enc-chain-1">
<option value="none">— ステップ1 —</option>
<option value="base64">Base64</option>
<option value="url">URLエンコード</option>
<option value="html">HTMLエンティティ</option>
<option value="hex">16進数</option>
<option value="binary">2進数</option>
<option value="unicode">Unicodeエスケープ</option>
</select>
<span class="enc-chain-arrow">&#8594;</span>
<select class="enc-chain-select" id="enc-chain-2">
<option value="none">— ステップ2 —</option>
<option value="base64">Base64</option>
<option value="url">URLエンコード</option>
<option value="html">HTMLエンティティ</option>
<option value="hex">16進数</option>
<option value="binary">2進数</option>
<option value="unicode">Unicodeエスケープ</option>
</select>
<button class="enc-btn enc-btn-violet" id="enc-chain-run-btn">チェーン実行</button>
</div>

<div class="enc-toggle-row">
<label class="enc-toggle-item">
<input type="checkbox" id="enc-auto-detect">
<span class="enc-toggle-label-text">形式を自動検出 <span class="enc-auto-badge" id="enc-auto-indicator" style="display:none;">AUTO</span></span>
</label>
</div>
</div>

<!-- 入力エリア -->
<div class="enc-card">
<div class="enc-textarea-label">
<span>入力</span>
<span class="enc-char-count" id="enc-input-count">0 文字</span>
</div>
<textarea
class="enc-textarea"
id="enc-input"
placeholder="ここにテキストを入力または貼り付けてください..."
spellcheck="false"
></textarea>

<div class="enc-btn-row">
<button class="enc-btn enc-btn-primary" id="enc-encode-btn">エンコード</button>
<button class="enc-btn enc-btn-primary" id="enc-decode-btn">デコード</button>
<button class="enc-btn enc-btn-ghost" id="enc-clear-btn">クリア</button>
</div>
</div>

<!-- スワップ -->
<div class="enc-swap-row">
<button class="enc-swap-btn" id="enc-swap-btn">&#8645; 入力と出力を入れ替え</button>
</div>

<!-- 出力エリア -->
<div class="enc-card">
<div class="enc-textarea-label">
<span>出力</span>
<span class="enc-char-count" id="enc-output-count">0 文字</span>
</div>
<textarea
class="enc-textarea"
id="enc-output"
placeholder="変換結果がここに表示されます..."
spellcheck="false"
readonly
></textarea>

<div class="enc-error" id="enc-error-msg"></div>

<div class="enc-btn-row">
<button class="enc-btn enc-btn-secondary" id="enc-copy-btn">出力をコピー</button>
</div>
</div>

<!-- 変換履歴 -->
<div class="enc-card">
<div class="enc-section-title">最近の変換履歴（最大5件）</div>
<ul class="enc-history-list" id="enc-history-list">
<li class="enc-history-empty">まだ変換履歴がありません。</li>
</ul>
</div>

<script>
(function () {
'use strict';

/* ── DOM参照 ── */
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

/* ── 履歴管理 ── */
var history = [];

function addHistory(mode, direction, input, output) {
history.unshift({ mode: mode, dir: direction, input: input, output: output });
if (history.length > 5) history = history.slice(0, 5);
renderHistory();
}

function renderHistory() {
if (history.length === 0) {
historyList.innerHTML = '<li class="enc-history-empty">まだ変換履歴がありません。</li>';
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

/* ── 文字数カウント ── */
function updateCounts() {
inputCnt.textContent  = inputEl.value.length.toLocaleString('ja-JP') + ' 文字';
outputCnt.textContent = outputEl.value.length.toLocaleString('ja-JP') + ' 文字';
}

/* ── エラー表示 ── */
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
各形式のエンコード/デコード関数
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
if (isNaN(code)) throw new Error('無効な16進数トークン: ' + token);
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
if (isNaN(code)) throw new Error('無効な2進数: ' + b);
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
if (isNaN(code)) throw new Error('無効な8進数トークン: ' + o);
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
if (isNaN(code)) throw new Error('無効なASCIIコード: ' + n);
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
if (parts.length < 2) throw new Error('有効なJWTではありません。ドット区切りの形式（header.payload.signature）を入力してください。');
function decodeSegment(seg) {
seg = seg.replace(/-/g, '+').replace(/_/g, '/');
while (seg.length % 4 !== 0) seg += '=';
return JSON.parse(decodeURIComponent(escape(atob(seg))));
}
var header  = decodeSegment(parts[0]);
var payload = decodeSegment(parts[1]);
return JSON.stringify({ header: header, payload: payload }, null, 2);
}

/* ── モード別ディスパッチ ── */
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
case 'jwt':     throw new Error('JWTはデコード専用です。エンコードには別の形式を選択してください。');
default: throw new Error('不明な形式: ' + mode);
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
default: throw new Error('不明な形式: ' + mode);
}
}

/* ── 自動検出 ── */
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

/* ── メイン処理 ── */
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
showError('エンコードエラー: ' + e.message);
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
showError('デコードエラー: ' + e.message);
setOutput('');
}
}

/* ── チェーンエンコード ── */
function doChain() {
clearError();
var text = inputEl.value;
if (!text) { setOutput(''); return; }
var steps = [chain1.value, chain2.value].filter(function(v){ return v !== 'none'; });
if (steps.length === 0) {
showError('チェーンのステップを少なくとも1つ選択してください。');
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
showError('チェーンエラー: ' + e.message);
setOutput('');
}
}

/* ── 自動検出実行 ── */
function runAutoDetect() {
var text = inputEl.value.trim();
if (!text) return;
var detected = detectMode(text);
if (detected) {
modeSelect.value = detected;
doDecode();
}
}

/* ── コピー ── */
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
copyBtn.textContent = 'コピーしました!';
copyBtn.classList.add('enc-btn-success');
setTimeout(function () {
copyBtn.textContent = orig;
copyBtn.classList.remove('enc-btn-success');
}, 1800);
}

/* ── イベント登録 ── */
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

## エンコーダー/デコーダーとは

エンコードとは、テキストやバイナリデータを別の表現形式に変換することで、安全に転送・保存・埋め込みができるようにする処理です。デコードはその逆で、元のデータを復元します。暗号化とは異なり、エンコードはセキュリティ機構ではなく、変換手順は公開されており完全に可逆です。テキストベースのプロトコルでバイナリデータを送信する、HTMLやURLに特殊文字を安全に埋め込む、認証トークンを検査するといった場面で広く使われます。

## 対応形式一覧

| 形式 | エンコード例 | 主な用途 |
|------|------------|---------|
| **Base64** | `Hello` → `SGVsbG8=` | メール添付・データURI・JWT |
| **URLエンコード** | `a b` → `a%20b` | クエリ文字列・フォームデータ |
| **HTMLエンティティ** | `<b>` → `&lt;b&gt;` | HTML安全出力 |
| **16進数（Hex）** | `A` → `41` | デバッグ・バイナリ解析 |
| **2進数（Binary）** | `A` → `01000001` | 低レベル解析 |
| **8進数（Octal）** | `A` → `\101` | Unixパーミッション・Cエスケープ |
| **ASCIIコード** | `Hi` → `72 105` | プロトコルデバッグ |
| **Unicodeエスケープ** | `©` → `\u00A9` | JavaScriptソース・JSON |
| **JWTデコード** | `eyJ…` → header＋payload JSON | ライブラリ不要のトークン検査 |

## チェーンエンコードの使い方

チェーン機能を使うと、2段階のエンコードを連続して適用できます。たとえば「16進数 → Base64」を選ぶと、各文字を16進数コードに変換してからBase64エンコードします。難読化されたペイロードの解析やCTF（セキュリティコンテスト）などで役立ちます。

---

### 関連ツール

> Base64エンコード → [Base64エンコーダー](/ja/tools/base64-encoder/)

> URLエンコード → [URLエンコーダー](/ja/tools/url-encoder/)

> HTMLエンティティ変換 → [HTMLエンティティエンコーダー](/ja/tools/html-entity-encoder/)

---

**エンジニアの確定申告を、もっとラクに**

コードは書けても、帳簿はちょっと…というエンジニアの方へ。クラウド会計ソフト「freee」なら、銀行口座・クレジットカードと自動連携して経費を自動分類。確定申告書の作成もガイドに沿うだけで完結します。副業・フリーランス収入がある方にも対応。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す（30日間）</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
