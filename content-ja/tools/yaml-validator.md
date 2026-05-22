---
title: "YAMLバリデーター＆変換ツール"
description: "YAMLファイルをオンラインで検証・整形。構文エラーのチェックとYAML⇔JSON変換。"
date: 2025-09-26
slug: "yaml-validator"
categories: ["無料ツール"]
tags: ["開発ツール", "コード変換", "無料ツール"]
ShowToc: false
cover:
  image: "/images/covers/yaml-validator-ja.png"
  alt: "YAMLバリデーター"
aliases:
  - "/ja/tools/yaml-json-converter/"
  - "/ja/tools/yaml-validator/"
---

<div id="ym-app">

<style>
#ym-app *,
#ym-app *::before,
#ym-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#ym-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", Meiryo, sans-serif;
font-size: 15px;
color: #1e293b;
line-height: 1.6;
max-width: 860px;
}
#ym-app h2 {
font-size: 1.15rem;
font-weight: 700;
color: #1e293b;
margin-bottom: 10px;
}
#ym-app .ym-desc {
font-size: 14px;
color: #475569;
margin-bottom: 18px;
}
#ym-app .ym-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 18px;
}
@media (max-width: 640px) {
#ym-app .ym-grid {
grid-template-columns: 1fr;
}
}
#ym-app .ym-panel {
display: flex;
flex-direction: column;
gap: 8px;
}
#ym-app .ym-panel-label {
font-size: 13px;
font-weight: 600;
color: #334155;
}
#ym-app textarea {
width: 100%;
height: 280px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
padding: 12px;
resize: vertical;
color: #1e293b;
background: #f8fafc;
line-height: 1.55;
outline: none;
transition: border-color 0.15s;
}
#ym-app textarea:focus {
border-color: #6366f1;
background: #fff;
}
#ym-app .ym-output-wrap {
position: relative;
}
#ym-app .ym-output {
width: 100%;
min-height: 280px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
padding: 12px;
background: #0f172a;
color: #e2e8f0;
line-height: 1.55;
white-space: pre-wrap;
word-break: break-all;
overflow: auto;
}
#ym-app .ym-copy-btn {
position: absolute;
top: 8px;
right: 8px;
padding: 4px 10px;
font-size: 12px;
font-weight: 600;
background: #334155;
color: #e2e8f0;
border: none;
border-radius: 5px;
cursor: pointer;
transition: background 0.15s;
}
#ym-app .ym-copy-btn:hover {
background: #475569;
}
#ym-app .ym-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin: 14px 0;
align-items: center;
}
#ym-app .ym-btn {
padding: 8px 16px;
font-size: 13px;
font-weight: 600;
border: none;
border-radius: 7px;
cursor: pointer;
transition: background 0.15s, transform 0.08s;
}
#ym-app .ym-btn:active {
transform: scale(0.97);
}
#ym-app .ym-btn-primary {
background: #6366f1;
color: #fff;
}
#ym-app .ym-btn-primary:hover {
background: #4f46e5;
}
#ym-app .ym-btn-green {
background: #10b981;
color: #fff;
}
#ym-app .ym-btn-green:hover {
background: #059669;
}
#ym-app .ym-btn-amber {
background: #f59e0b;
color: #fff;
}
#ym-app .ym-btn-amber:hover {
background: #d97706;
}
#ym-app .ym-btn-slate {
background: #64748b;
color: #fff;
}
#ym-app .ym-btn-slate:hover {
background: #475569;
}
#ym-app .ym-btn-red {
background: #ef4444;
color: #fff;
}
#ym-app .ym-btn-red:hover {
background: #dc2626;
}
#ym-app .ym-upload-label {
display: inline-block;
padding: 8px 16px;
font-size: 13px;
font-weight: 600;
background: #e2e8f0;
color: #334155;
border-radius: 7px;
cursor: pointer;
transition: background 0.15s;
}
#ym-app .ym-upload-label:hover {
background: #cbd5e1;
}
#ym-app #ym-file-input {
display: none;
}
#ym-app .ym-status {
display: flex;
align-items: center;
gap: 8px;
font-size: 13px;
font-weight: 600;
padding: 10px 14px;
border-radius: 8px;
min-height: 40px;
}
#ym-app .ym-status.ok {
background: #dcfce7;
color: #166534;
border: 1px solid #bbf7d0;
}
#ym-app .ym-status.err {
background: #fee2e2;
color: #991b1b;
border: 1px solid #fecaca;
}
#ym-app .ym-status.info {
background: #eff6ff;
color: #1e40af;
border: 1px solid #bfdbfe;
}
#ym-app .ym-status.hidden {
display: none;
}
/* Syntax highlight tokens */
#ym-app .yt-key    { color: #a78bfa; }  /* 紫 */
#ym-app .yt-str    { color: #4ade80; }  /* 緑 */
#ym-app .yt-num    { color: #60a5fa; }  /* 青 */
#ym-app .yt-bool   { color: #fb923c; }  /* オレンジ */
#ym-app .yt-null   { color: #94a3b8; }  /* スレート */
#ym-app .yt-punct  { color: #e2e8f0; }
#ym-app .yt-cmt    { color: #64748b; font-style: italic; }
#ym-app .yt-dash   { color: #f472b6; }
#ym-app .ym-mode-row {
display: flex;
gap: 8px;
align-items: center;
flex-wrap: wrap;
margin-bottom: 6px;
}
#ym-app .ym-mode-label {
font-size: 12px;
font-weight: 600;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#ym-app .ym-sep {
height: 1px;
background: #e2e8f0;
margin: 20px 0;
}
</style>

<p class="ym-desc">YAMLまたはJSONを貼り付けて、バリデーション・変換・整形をすぐに実行できます。データはブラウザ外に送信されません。</p>

<div class="ym-mode-row">
<span class="ym-mode-label">入力形式:</span>
<label style="font-size:13px;cursor:pointer;"><input type="radio" name="ym-mode" value="yaml" checked style="accent-color:#6366f1;"> YAML</label>
<label style="font-size:13px;cursor:pointer;"><input type="radio" name="ym-mode" value="json" style="accent-color:#6366f1;"> JSON</label>
<label class="ym-upload-label" title=".yaml/.yml/.jsonファイルをアップロード">
ファイルを開く
<input type="file" id="ym-file-input" accept=".yaml,.yml,.json,.txt">
</label>
<button class="ym-btn ym-btn-red" id="ym-clear-btn" style="padding:6px 12px;font-size:12px;">クリア</button>
</div>

<div class="ym-grid">
<div class="ym-panel">
<div class="ym-panel-label">入力</div>
<textarea id="ym-input" spellcheck="false" placeholder="YAMLまたはJSONをここに貼り付けてください…"></textarea>
</div>
<div class="ym-panel">
<div class="ym-panel-label">出力</div>
<div class="ym-output-wrap">
<div class="ym-output" id="ym-output" aria-label="出力"></div>
<button class="ym-copy-btn" id="ym-copy-btn">コピー</button>
</div>
</div>
</div>

<div class="ym-toolbar">
<button class="ym-btn ym-btn-primary" id="ym-validate-btn">バリデーション</button>
<button class="ym-btn ym-btn-green"   id="ym-to-json-btn">YAML → JSON</button>
<button class="ym-btn ym-btn-amber"   id="ym-to-yaml-btn">JSON → YAML</button>
<button class="ym-btn ym-btn-slate"   id="ym-format-btn">整形 / 正規化</button>
</div>

<div class="ym-status hidden" id="ym-status"></div>

<script>
(function(){
"use strict";

/* ─────────────────────────────────────────────
Mini YAML パーサー
対応機能:
- key: value ペア
- ネストされたオブジェクト（インデントベース）
- 配列（- item）
- クォートあり/なし文字列
- 数値、真偽値、null
- 複数行文字列（| と >）
- コメント（#）
───────────────────────────────────────────── */

function parseYAML(text) {
var lines = text.split(/\r?\n/);
while (lines.length && lines[lines.length-1].trim() === '') lines.pop();
var pos = {i: 0};
return parseBlock(lines, pos, 0);
}

function getIndent(line) {
var m = line.match(/^( *)/);
return m ? m[1].length : 0;
}

function isComment(line) {
return line.trim().startsWith('#') || line.trim() === '';
}

function stripComment(s) {
var inQ = false, q = '', i;
for (i = 0; i < s.length; i++) {
var c = s[i];
if (!inQ && (c === '"' || c === "'")) { inQ = true; q = c; }
else if (inQ && c === q) { inQ = false; }
else if (!inQ && c === '#') { return s.slice(0, i).trimEnd(); }
}
return s;
}

function parseScalar(s) {
s = s.trim();
if (s === '' || s === 'null' || s === '~') return null;
if (s === 'true' || s === 'yes' || s === 'on') return true;
if (s === 'false' || s === 'no' || s === 'off') return false;
if ((s.startsWith('"') && s.endsWith('"')) ||
(s.startsWith("'") && s.endsWith("'"))) {
return s.slice(1, -1)
.replace(/\\n/g, '\n').replace(/\\t/g, '\t')
.replace(/\\"/g, '"').replace(/\\\\/g, '\\');
}
if (/^-?(\d+\.?\d*|\.\d+)([eE][+-]?\d+)?$/.test(s)) return Number(s);
if (/^0x[0-9a-fA-F]+$/.test(s)) return parseInt(s, 16);
if (/^0o[0-7]+$/.test(s)) return parseInt(s.slice(2), 8);
return s;
}

function collectMultiline(lines, pos, indent, style) {
var result = [];
while (pos.i < lines.length) {
var raw = lines[pos.i];
if (raw.trim() === '') { result.push(''); pos.i++; continue; }
var ind = getIndent(raw);
if (ind < indent + 1) break;
result.push(raw.slice(indent + 1));
pos.i++;
}
while (result.length && result[result.length-1] === '') result.pop();
if (style === '|') return result.join('\n') + '\n';
var out = '', prev = '';
for (var i = 0; i < result.length; i++) {
var l = result[i];
if (l === '') { out += '\n'; prev = ''; }
else if (prev !== '') { out += ' ' + l; prev = l; }
else { out += l; prev = l; }
}
return out + '\n';
}

function parseBlock(lines, pos, indent) {
while (pos.i < lines.length && isComment(lines[pos.i])) pos.i++;
if (pos.i >= lines.length) return null;
var firstLine = lines[pos.i];
var firstTrim = firstLine.trim();
if (firstTrim.startsWith('- ') || firstTrim === '-') {
return parseSequence(lines, pos, indent);
}
if (firstTrim.includes(':') || firstTrim.endsWith(':')) {
return parseMapping(lines, pos, indent);
}
pos.i++;
return parseScalar(stripComment(firstTrim));
}

function parseSequence(lines, pos, indent) {
var arr = [];
while (pos.i < lines.length) {
var raw = lines[pos.i];
if (raw.trim() === '' || raw.trim().startsWith('#')) { pos.i++; continue; }
var ind = getIndent(raw);
if (ind < indent) break;
var trimmed = raw.trim();
if (!trimmed.startsWith('-')) break;
pos.i++;
var afterDash = trimmed.slice(1);
if (afterDash.trim() === '') {
while (pos.i < lines.length && (lines[pos.i].trim() === '' || lines[pos.i].trim().startsWith('#'))) pos.i++;
if (pos.i < lines.length && getIndent(lines[pos.i]) > ind) {
arr.push(parseBlock(lines, pos, getIndent(lines[pos.i])));
} else {
arr.push(null);
}
} else {
var content = afterDash.trim();
if (content.includes(':') && !isQuotedString(content)) {
var synLines = [raw.replace(/^(\s*)-\s*/, '$1  ')].concat(
collectSubLines(lines, pos, ind + 1)
);
var synPos = {i: 0};
arr.push(parseMapping(synLines, synPos, ind + 1));
} else {
arr.push(parseScalar(stripComment(content)));
}
}
}
return arr;
}

function collectSubLines(lines, pos, minIndent) {
var collected = [];
while (pos.i < lines.length) {
var raw = lines[pos.i];
if (raw.trim() === '' || raw.trim().startsWith('#')) { collected.push(raw); pos.i++; continue; }
if (getIndent(raw) < minIndent) break;
collected.push(raw); pos.i++;
}
return collected;
}

function isQuotedString(s) {
s = s.trim();
return (s.startsWith('"') || s.startsWith("'"));
}

function parseMapping(lines, pos, indent) {
var obj = {};
while (pos.i < lines.length) {
var raw = lines[pos.i];
if (raw.trim() === '' || raw.trim().startsWith('#')) { pos.i++; continue; }
var ind = getIndent(raw);
if (ind < indent) break;
var trimmed = raw.trim();
var colonIdx = findKeyColon(trimmed);
if (colonIdx === -1) break;
var key = trimmed.slice(0, colonIdx).trim();
if ((key.startsWith('"') && key.endsWith('"')) ||
(key.startsWith("'") && key.endsWith("'"))) {
key = key.slice(1, -1);
}
var rest = trimmed.slice(colonIdx + 1).trim();
pos.i++;
if (rest === '|' || rest === '|-' || rest === '|+' ||
rest === '>' || rest === '>-' || rest === '>+') {
var style = rest[0];
var subInd = ind + 2;
while (pos.i < lines.length && lines[pos.i].trim() === '') pos.i++;
if (pos.i < lines.length) subInd = getIndent(lines[pos.i]);
obj[key] = collectMultiline(lines, pos, subInd - 1, style);
} else if (rest === '' || rest === null) {
while (pos.i < lines.length && (lines[pos.i].trim() === '' || lines[pos.i].trim().startsWith('#'))) pos.i++;
if (pos.i < lines.length) {
var nextInd = getIndent(lines[pos.i]);
if (nextInd > ind) {
obj[key] = parseBlock(lines, pos, nextInd);
} else {
obj[key] = null;
}
} else {
obj[key] = null;
}
} else {
if (rest.startsWith('[') || rest.startsWith('{')) {
obj[key] = parseFlow(rest);
} else {
obj[key] = parseScalar(stripComment(rest));
}
}
}
return obj;
}

function findKeyColon(s) {
var inQ = false, q = '', i;
for (i = 0; i < s.length; i++) {
var c = s[i];
if (!inQ && (c === '"' || c === "'")) { inQ = true; q = c; }
else if (inQ && c === q) { inQ = false; }
else if (!inQ && c === ':') {
if (i === s.length - 1 || s[i+1] === ' ' || s[i+1] === '\t') return i;
}
}
return -1;
}

function parseFlow(s) {
s = s.trim();
try {
var normalised = s
.replace(/'/g, '"')
.replace(/([{,]\s*)([a-zA-Z_][\w-]*)(\s*:)/g, '$1"$2"$3');
return JSON.parse(normalised);
} catch(e) {
return s;
}
}

/* ─────────────────────────────────────────────
YAML エミッター（JSオブジェクト → YAML文字列）
───────────────────────────────────────────── */

function dumpYAML(val, indent) {
indent = indent || 0;
var pad = '  '.repeat(indent);
if (val === null || val === undefined) return 'null';
if (typeof val === 'boolean') return val ? 'true' : 'false';
if (typeof val === 'number') return String(val);
if (typeof val === 'string') return dumpString(val, indent);
if (Array.isArray(val)) {
if (val.length === 0) return '[]';
var lines = val.map(function(item) {
var dumped = dumpYAML(item, indent + 1);
if (typeof item === 'object' && item !== null) {
var subLines = dumped.split('\n');
return pad + '- ' + subLines[0] + (subLines.length > 1 ? '\n' + subLines.slice(1).join('\n') : '');
}
return pad + '- ' + dumped;
});
return lines.join('\n');
}
if (typeof val === 'object') {
var keys = Object.keys(val);
if (keys.length === 0) return '{}';
var out = keys.map(function(k) {
var v = val[k];
var keyStr = needsQuoting(k) ? '"' + k + '"' : k;
if (v === null || v === undefined) return pad + keyStr + ': null';
if (typeof v === 'object') {
var dumped = dumpYAML(v, indent + 1);
if (Array.isArray(v) && v.length === 0) return pad + keyStr + ': []';
if (!Array.isArray(v) && Object.keys(v).length === 0) return pad + keyStr + ': {}';
return pad + keyStr + ':\n' + dumped;
}
return pad + keyStr + ': ' + dumpYAML(v, indent + 1);
});
return out.join('\n');
}
return String(val);
}

function needsQuoting(s) {
return /[:#\[\]{},&*!|>'"%@`]/.test(s) || /^[\s]|[\s]$/.test(s);
}

function dumpString(s, indent) {
if (/\n/.test(s)) {
var pad = '  '.repeat(indent + 1);
return '|\n' + s.split('\n').map(function(l){ return pad + l; }).join('\n');
}
if (/[:#\[\]{},&*!|>'"%@`?]/.test(s) || s.trim() !== s ||
s === '' || /^(true|false|null|yes|no|on|off|\d.*)$/i.test(s)) {
return '"' + s.replace(/\\/g, '\\\\').replace(/"/g, '\\"').replace(/\n/g, '\\n') + '"';
}
return s;
}

/* ─────────────────────────────────────────────
シンタックスハイライター
───────────────────────────────────────────── */

function highlightYAML(text) {
return text.split('\n').map(function(line) {
if (/^\s*#/.test(line)) return '<span class="yt-cmt">' + esc(line) + '</span>';
var m = line.match(/^(\s*)(-\s+)?([^:#\n]+?)(\s*:\s*)(.*)$/);
if (m) {
var ws   = esc(m[1]);
var dash = m[2] ? '<span class="yt-dash">' + esc(m[2]) + '</span>' : '';
var key  = '<span class="yt-key">' + esc(m[3]) + '</span>';
var col  = '<span class="yt-punct">' + esc(m[4]) + '</span>';
var val  = highlightValue(m[5]);
return ws + dash + key + col + val;
}
var dm = line.match(/^(\s*)(- )(.*)$/);
if (dm) {
return esc(dm[1]) + '<span class="yt-dash">' + esc(dm[2]) + '</span>' + highlightValue(dm[3]);
}
return esc(line);
}).join('\n');
}

function highlightJSON(text) {
return text.replace(/("(?:[^"\\]|\\.)*")\s*:/g, '<span class="yt-key">$1</span>:')
.replace(/:\s*("(?:[^"\\]|\\.)*")/g, ': <span class="yt-str">$1</span>')
.replace(/:\s*(-?\d+\.?\d*(?:[eE][+-]?\d+)?)/g, ': <span class="yt-num">$1</span>')
.replace(/:\s*(true|false)/g, ': <span class="yt-bool">$1</span>')
.replace(/:\s*(null)/g, ': <span class="yt-null">$1</span>');
}

function highlightValue(v) {
if (!v) return '';
var t = v.trim();
if (t.startsWith('#')) return '<span class="yt-cmt">' + esc(v) + '</span>';
if (t === 'true' || t === 'false' || t === 'yes' || t === 'no' || t === 'on' || t === 'off')
return '<span class="yt-bool">' + esc(v) + '</span>';
if (t === 'null' || t === '~')
return '<span class="yt-null">' + esc(v) + '</span>';
if (/^-?[\d.]+([eE][+-]?\d+)?$/.test(t))
return '<span class="yt-num">' + esc(v) + '</span>';
if (t.startsWith('"') || t.startsWith("'"))
return '<span class="yt-str">' + esc(v) + '</span>';
if (t === '|' || t === '>' || t === '|-' || t === '>-')
return '<span class="yt-punct">' + esc(v) + '</span>';
if (t.startsWith('[') || t.startsWith('{'))
return '<span class="yt-str">' + esc(v) + '</span>';
return '<span class="yt-str">' + esc(v) + '</span>';
}

function esc(s) {
return (s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

/* ─────────────────────────────────────────────
バリデーションヘルパー
───────────────────────────────────────────── */

function validateYAML(text) {
try {
parseYAML(text);
return {ok: true};
} catch(e) {
return {ok: false, msg: e.message};
}
}

function validateJSON(text) {
try {
JSON.parse(text);
return {ok: true};
} catch(e) {
return {ok: false, msg: e.message};
}
}

/* ─────────────────────────────────────────────
UI 設定
───────────────────────────────────────────── */

var input   = document.getElementById('ym-input');
var output  = document.getElementById('ym-output');
var status  = document.getElementById('ym-status');
var copyBtn = document.getElementById('ym-copy-btn');
var fileInput = document.getElementById('ym-file-input');

function getMode() {
return document.querySelector('input[name="ym-mode"]:checked').value;
}

function setStatus(type, msg) {
status.className = 'ym-status ' + type;
status.textContent = msg;
}

function clearStatus() {
status.className = 'ym-status hidden';
status.textContent = '';
}

function setOutput(text, lang) {
if (!text) { output.innerHTML = ''; return; }
if (lang === 'yaml') output.innerHTML = highlightYAML(text);
else if (lang === 'json') output.innerHTML = highlightJSON(esc(text));
else output.innerHTML = esc(text);
output.dataset.raw = text;
}

// バリデーション
document.getElementById('ym-validate-btn').addEventListener('click', function() {
var text = input.value.trim();
if (!text) { setStatus('info', '入力欄にYAMLまたはJSONを貼り付けてください。'); return; }
var mode = getMode();
var result;
if (mode === 'yaml') result = validateYAML(text);
else result = validateJSON(text);
if (result.ok) {
setStatus('ok', mode.toUpperCase() + ' の構文は正しいです！');
setOutput(text, mode);
} else {
setStatus('err', mode.toUpperCase() + ' エラー: ' + result.msg);
setOutput('', 'plain');
}
});

// YAML → JSON
document.getElementById('ym-to-json-btn').addEventListener('click', function() {
var text = input.value.trim();
if (!text) { setStatus('info', 'YAMLを入力欄に貼り付けてください。'); return; }
try {
var parsed = parseYAML(text);
var json = JSON.stringify(parsed, null, 2);
setOutput(json, 'json');
setStatus('ok', 'JSONへの変換が完了しました。');
} catch(e) {
setStatus('err', 'YAMLパースエラー: ' + e.message);
setOutput('', 'plain');
}
});

// JSON → YAML
document.getElementById('ym-to-yaml-btn').addEventListener('click', function() {
var text = input.value.trim();
if (!text) { setStatus('info', 'JSONを入力欄に貼り付けてください。'); return; }
try {
var parsed = JSON.parse(text);
var yaml = dumpYAML(parsed, 0);
setOutput(yaml, 'yaml');
setStatus('ok', 'YAMLへの変換が完了しました。');
} catch(e) {
setStatus('err', 'JSONパースエラー: ' + e.message);
setOutput('', 'plain');
}
});

// 整形 / 正規化
document.getElementById('ym-format-btn').addEventListener('click', function() {
var text = input.value.trim();
if (!text) { setStatus('info', 'YAMLを入力欄に貼り付けてください。'); return; }
try {
var parsed = parseYAML(text);
var pretty = dumpYAML(parsed, 0);
setOutput(pretty, 'yaml');
setStatus('ok', 'インデント2スペースで整形しました。');
input.value = pretty;
} catch(e) {
setStatus('err', 'YAMLパースエラー: ' + e.message);
setOutput('', 'plain');
}
});

// コピー
copyBtn.addEventListener('click', function() {
var raw = output.dataset.raw || output.textContent;
if (!raw) return;
navigator.clipboard.writeText(raw).then(function() {
var old = copyBtn.textContent;
copyBtn.textContent = 'コピー完了！';
setTimeout(function(){ copyBtn.textContent = old; }, 1500);
}).catch(function() {
var ta = document.createElement('textarea');
ta.value = raw;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
copyBtn.textContent = 'コピー完了！';
setTimeout(function(){ copyBtn.textContent = 'コピー'; }, 1500);
});
});

// ファイルアップロード
fileInput.addEventListener('change', function() {
var file = fileInput.files[0];
if (!file) return;
var ext = file.name.split('.').pop().toLowerCase();
if (ext === 'json') {
document.querySelector('input[name="ym-mode"][value="json"]').checked = true;
} else {
document.querySelector('input[name="ym-mode"][value="yaml"]').checked = true;
}
var reader = new FileReader();
reader.onload = function(e) {
input.value = e.target.result;
clearStatus();
setOutput('', 'plain');
};
reader.readAsText(file);
fileInput.value = '';
});

// クリア
document.getElementById('ym-clear-btn').addEventListener('click', function() {
input.value = '';
output.innerHTML = '';
output.dataset.raw = '';
clearStatus();
});

// サンプルYAMLを初期表示
input.value = [
'# サンプルYAML',
'アプリ名: 私のアプリケーション',
'バージョン: 2.1.0',
'デバッグ: false',
'ポート: 8080',
'',
'データベース:',
'  ホスト: localhost',
'  ポート: 5432',
'  DB名: mydb',
'  SSL: true',
'',
'機能:',
'  - 認証',
'  - レート制限',
'  - キャッシュ',
'',
'ログ:',
'  レベル: info',
'  形式: json',
'  出力先: stdout',
].join('\n');

})();
</script>

<div class="ym-sep"></div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div class="ym-sep"></div>

### 関連ツール
> JSONを検証 → [JSONバリデーター](/ja/tools/json-validator/)
> HTMLを整形 → [HTML整形ツール](/ja/tools/html-beautifier/)

---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
