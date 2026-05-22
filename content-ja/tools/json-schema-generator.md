---
title: "JSONスキーマジェネレーター — 無料オンラインツール"
date: 2025-07-16
description: "サンプルJSONからJSONスキーマを自動生成。型・ネストオブジェクト・配列を自動検出。プロパティ編集・必須フィールド設定・バリデーション対応。"
categories: ["無料ツール"]
tags: ["開発ツール", "コード変換", "無料ツール"]
slug: "json-schema-generator"
ShowToc: false
aliases:
  - "/ja/tools/json-schema-generator/"
  - "/ja/tools/json-schema-generator/"
cover:
  image: "/images/covers/json-schema-generator-ja.png"
  alt: "JSONスキーマジェネレーター"
---

<div id="jsg-app">

<style>
#jsg-app {
font-family: 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', system-ui, sans-serif;
background: #1e1e2e;
color: #cdd6f4;
border-radius: 12px;
padding: 20px;
margin: 0 auto;
max-width: 1200px;
box-sizing: border-box;
}

#jsg-app * {
box-sizing: border-box;
}

/* ── ツールバー ── */
#jsg-app .jsg-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 16px;
}

#jsg-app .jsg-toolbar-group {
display: flex;
align-items: center;
gap: 6px;
flex-wrap: wrap;
}

#jsg-app .jsg-sep {
width: 1px;
height: 26px;
background: #45475a;
margin: 0 4px;
}

#jsg-app .jsg-label {
font-size: 12px;
color: #a6adc8;
white-space: nowrap;
}

#jsg-app .jsg-btn {
padding: 7px 15px;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
outline: none;
white-space: nowrap;
}
#jsg-app .jsg-btn:active { transform: scale(0.97); }
#jsg-app .jsg-btn:hover  { opacity: 0.88; }

#jsg-app .jsg-btn-generate { background: #89b4fa; color: #1e1e2e; }
#jsg-app .jsg-btn-validate { background: #a6e3a1; color: #1e1e2e; }
#jsg-app .jsg-btn-copy     { background: #cba6f7; color: #1e1e2e; }
#jsg-app .jsg-btn-clear    { background: #45475a; color: #cdd6f4; }

#jsg-app .jsg-select {
background: #313244;
color: #cdd6f4;
border: 1px solid #45475a;
border-radius: 6px;
padding: 6px 10px;
font-size: 13px;
cursor: pointer;
outline: none;
}
#jsg-app .jsg-select:focus { border-color: #89b4fa; }

#jsg-app .jsg-version-toggle {
display: flex;
gap: 0;
border-radius: 7px;
overflow: hidden;
border: 1px solid #45475a;
}

#jsg-app .jsg-version-btn {
padding: 6px 13px;
background: #313244;
color: #a6adc8;
border: none;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
outline: none;
}
#jsg-app .jsg-version-btn.active {
background: #89b4fa;
color: #1e1e2e;
}

/* ── メインレイアウト ── */
#jsg-app .jsg-main {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}

@media (max-width: 750px) {
#jsg-app .jsg-main { grid-template-columns: 1fr; }
#jsg-app .jsg-sep  { display: none; }
}

#jsg-app .jsg-pane {
display: flex;
flex-direction: column;
gap: 8px;
}

#jsg-app .jsg-pane-label {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #a6adc8;
}

#jsg-app .jsg-textarea {
width: 100%;
min-height: 320px;
background: #11111b;
color: #cdd6f4;
border: 2px solid #313244;
border-radius: 9px;
padding: 14px;
font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
font-size: 13px;
line-height: 1.65;
resize: vertical;
outline: none;
transition: border-color 0.2s;
tab-size: 2;
}
#jsg-app .jsg-textarea:focus { border-color: #89b4fa; }
#jsg-app .jsg-textarea.jsg-error { border-color: #f38ba8; }
#jsg-app .jsg-textarea.jsg-valid { border-color: #a6e3a1; }

#jsg-app .jsg-output-box {
width: 100%;
min-height: 320px;
background: #11111b;
border: 2px solid #313244;
border-radius: 9px;
padding: 14px;
font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
font-size: 13px;
line-height: 1.65;
overflow: auto;
white-space: pre-wrap;
word-break: break-all;
transition: border-color 0.2s;
}
#jsg-app .jsg-output-box.jsg-valid { border-color: #a6e3a1; }
#jsg-app .jsg-output-box.jsg-error { border-color: #f38ba8; }

/* ── ステータス・エラー ── */
#jsg-app .jsg-status-bar {
display: flex;
flex-wrap: wrap;
gap: 12px;
font-size: 12px;
color: #6c7086;
margin-top: 2px;
}
#jsg-app .jsg-ok   { color: #a6e3a1; font-weight: 600; }
#jsg-app .jsg-err  { color: #f38ba8; font-weight: 600; }
#jsg-app .jsg-info { color: #89b4fa; }

#jsg-app .jsg-error-box {
background: #1a0a0a;
border: 1px solid #f38ba8;
border-radius: 7px;
color: #f38ba8;
font-size: 13px;
padding: 10px 14px;
display: none;
font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
}
#jsg-app .jsg-error-box.visible { display: block; }

/* ── プロパティエディター ── */
#jsg-app .jsg-editor-section {
margin-top: 18px;
background: #181825;
border: 1px solid #313244;
border-radius: 10px;
padding: 14px;
}

#jsg-app .jsg-editor-title {
font-size: 12px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #a6adc8;
margin-bottom: 12px;
}

#jsg-app .jsg-prop-table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
}

#jsg-app .jsg-prop-table th {
text-align: left;
color: #6c7086;
font-weight: 600;
font-size: 11px;
text-transform: uppercase;
letter-spacing: 0.06em;
padding: 4px 8px 8px 8px;
border-bottom: 1px solid #313244;
}

#jsg-app .jsg-prop-table td {
padding: 6px 8px;
vertical-align: middle;
border-bottom: 1px solid #1e1e2e;
}
#jsg-app .jsg-prop-table tr:last-child td { border-bottom: none; }

#jsg-app .jsg-prop-key {
color: #89b4fa;
font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
white-space: nowrap;
}

#jsg-app .jsg-prop-type {
color: #fab387;
font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
font-size: 12px;
}

#jsg-app .jsg-prop-desc-input {
background: #11111b;
color: #cdd6f4;
border: 1px solid #313244;
border-radius: 5px;
padding: 4px 8px;
font-size: 12px;
width: 100%;
outline: none;
transition: border-color 0.15s;
}
#jsg-app .jsg-prop-desc-input:focus { border-color: #89b4fa; }

#jsg-app .jsg-prop-req-chk {
accent-color: #89b4fa;
width: 16px;
height: 16px;
cursor: pointer;
}

#jsg-app .jsg-apply-btn {
margin-top: 12px;
padding: 7px 18px;
background: #89b4fa;
color: #1e1e2e;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.15s;
}
#jsg-app .jsg-apply-btn:hover { opacity: 0.85; }

/* ── シンタックスハイライト ── */
#jsg-app .jst-key    { color: #89b4fa; }
#jsg-app .jst-str    { color: #a6e3a1; }
#jsg-app .jst-num    { color: #fab387; }
#jsg-app .jst-bool   { color: #cba6f7; }
#jsg-app .jst-null   { color: #f38ba8; }
#jsg-app .jst-punc   { color: #6c7086; }

/* ── トースト通知 ── */
#jsg-app .jsg-toast {
position: fixed;
bottom: 32px;
right: 32px;
background: #a6e3a1;
color: #1e1e2e;
font-weight: 700;
font-size: 14px;
padding: 10px 22px;
border-radius: 8px;
box-shadow: 0 4px 24px rgba(0,0,0,0.4);
opacity: 0;
pointer-events: none;
transition: opacity 0.25s;
z-index: 9999;
}
#jsg-app .jsg-toast.show { opacity: 1; }
</style>

<!-- ツールバー -->
<div class="jsg-toolbar">
<div class="jsg-toolbar-group">
<button class="jsg-btn jsg-btn-generate" onclick="jsgGenerate()">スキーマ生成</button>
<button class="jsg-btn jsg-btn-validate" onclick="jsgValidate()">JSONを検証</button>
</div>
<div class="jsg-sep"></div>
<div class="jsg-toolbar-group">
<span class="jsg-label">スキーマバージョン:</span>
<div class="jsg-version-toggle">
<button class="jsg-version-btn active" id="jsg-v07" onclick="jsgSetVersion('draft-07')">Draft-07</button>
<button class="jsg-version-btn" id="jsg-v20" onclick="jsgSetVersion('2020-12')">2020-12</button>
</div>
</div>
<div class="jsg-sep"></div>
<div class="jsg-toolbar-group">
<span class="jsg-label">サンプル:</span>
<select class="jsg-select" id="jsg-sample-select" onchange="jsgLoadSample(this.value)">
<option value="">— プリセットを選択 —</option>
<option value="user">ユーザーオブジェクト</option>
<option value="product">商品カタログ</option>
<option value="api">APIレスポンス</option>
</select>
</div>
<div class="jsg-sep"></div>
<div class="jsg-toolbar-group">
<button class="jsg-btn jsg-btn-copy"  onclick="jsgCopy()">スキーマをコピー</button>
<button class="jsg-btn jsg-btn-clear" onclick="jsgClear()">クリア</button>
</div>
</div>

<!-- メインペイン -->
<div class="jsg-main">

<!-- 左: JSON入力 -->
<div class="jsg-pane">
<div class="jsg-pane-label">入力 JSON</div>
<textarea
id="jsg-input"
class="jsg-textarea"
placeholder='サンプルJSONを貼り付けてください…&#10;&#10;{"name": "田中太郎", "age": 30, "email": "tanaka@example.com"}'
oninput="jsgOnInput()"
spellcheck="false"
></textarea>
<div class="jsg-status-bar">
<span id="jsg-in-chars">文字数: 0</span>
<span id="jsg-in-lines">行数: 1</span>
</div>
<div id="jsg-error-box" class="jsg-error-box"></div>
</div>

<!-- 右: スキーマ出力 -->
<div class="jsg-pane">
<div class="jsg-pane-label">生成済み JSON スキーマ</div>
<div id="jsg-output" class="jsg-output-box"><span style="color:#45475a">// 左にJSONを貼り付けて「スキーマ生成」をクリックするとここに表示されます</span></div>
<div class="jsg-status-bar" id="jsg-out-status"></div>
</div>

</div>

<!-- プロパティエディター（スキーマ生成後に表示） -->
<div class="jsg-editor-section" id="jsg-editor-section" style="display:none;">
<div class="jsg-editor-title">スキーマプロパティを編集</div>
<table class="jsg-prop-table" id="jsg-prop-table">
<thead>
<tr>
<th>プロパティ名</th>
<th>型</th>
<th>説明（description）</th>
<th>必須</th>
</tr>
</thead>
<tbody id="jsg-prop-tbody"></tbody>
</table>
<button class="jsg-apply-btn" onclick="jsgApplyEdits()">編集を適用して再生成</button>
</div>

<div class="jsg-toast" id="jsg-toast">コピーしました！</div>

<script>
(function () {
'use strict';

/* ────────────────────────────────────────
状態管理
──────────────────────────────────────── */
var schemaVersion = 'draft-07';
var lastSchema = null;
var lastInput  = null;
var propMeta   = {};

/* ────────────────────────────────────────
ユーティリティ
──────────────────────────────────────── */
function esc(s) {
return String(s)
.replace(/&/g, '&amp;')
.replace(/</g, '&lt;')
.replace(/>/g, '&gt;')
.replace(/"/g, '&quot;');
}

function syntaxHL(json) {
return esc(json).replace(
/("(\\u[a-fA-F0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+\-]?\d+)?|[{}\[\],:])/g,
function (m) {
var cls = 'jst-num';
if (/^"/.test(m))              cls = /:$/.test(m) ? 'jst-key' : 'jst-str';
else if (/true|false/.test(m)) cls = 'jst-bool';
else if (/null/.test(m))       cls = 'jst-null';
else if (/[{}\[\],:]/.test(m)) cls = 'jst-punc';
return '<span class="' + cls + '">' + m + '</span>';
}
);
}

function showToast(msg) {
var t = document.getElementById('jsg-toast');
t.textContent = msg || 'コピーしました！';
t.classList.add('show');
setTimeout(function () { t.classList.remove('show'); }, 1800);
}

function setError(msg) {
var el = document.getElementById('jsg-error-box');
if (msg) { el.textContent = msg; el.classList.add('visible'); }
else      { el.textContent = ''; el.classList.remove('visible'); }
}

function setInputState(state) {
var el = document.getElementById('jsg-input');
el.className = 'jsg-textarea' + (state ? ' jsg-' + state : '');
}

function setOutputState(state) {
var el = document.getElementById('jsg-output');
el.className = 'jsg-output-box' + (state ? ' jsg-' + state : '');
}

function setOutputHTML(html) {
document.getElementById('jsg-output').innerHTML = html;
}

function updateInputStats() {
var v = document.getElementById('jsg-input').value;
document.getElementById('jsg-in-chars').textContent = '文字数: ' + v.length;
document.getElementById('jsg-in-lines').textContent = '行数: ' + (v ? v.split('\n').length : 1);
}

function setOutStatus(html) {
document.getElementById('jsg-out-status').innerHTML = html;
}

function parseInput() {
var raw = document.getElementById('jsg-input').value.trim();
if (!raw) return null;
try {
return { ok: true, value: JSON.parse(raw) };
} catch (e) {
var msg = e.message || String(e);
var pm = msg.match(/position (\d+)/i);
var line = null;
if (pm) {
var pos = parseInt(pm[1], 10);
line = raw.slice(0, pos).split('\n').length;
}
return { ok: false, error: msg, line: line };
}
}

/* ────────────────────────────────────────
フォーマット検出
──────────────────────────────────────── */
var RE_DATETIME = /^\d{4}-\d{2}-\d{2}(T\d{2}:\d{2}:\d{2}(\.\d+)?(Z|[+-]\d{2}:\d{2})?)?$/;
var RE_EMAIL    = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
var RE_URI      = /^https?:\/\/.+/;
var RE_UUID     = /^[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}$/i;

function detectStringFormat(val) {
if (RE_DATETIME.test(val)) return 'date-time';
if (RE_EMAIL.test(val))    return 'email';
if (RE_URI.test(val))      return 'uri';
if (RE_UUID.test(val))     return 'uuid';
return null;
}

function isInteger(n) {
return Number.isFinite(n) && Math.floor(n) === n;
}

/* ────────────────────────────────────────
スキーマ生成（再帰）
──────────────────────────────────────── */
function inferSchema(val) {
if (val === null)              return { type: 'null' };
if (typeof val === 'boolean')  return { type: 'boolean' };
if (typeof val === 'number')   return { type: isInteger(val) ? 'integer' : 'number' };

if (typeof val === 'string') {
var fmt = detectStringFormat(val);
var s = { type: 'string' };
if (fmt) s.format = fmt;
return s;
}

if (Array.isArray(val)) {
var schema = { type: 'array' };
if (val.length > 0) schema.items = inferSchema(val[0]);
return schema;
}

if (typeof val === 'object') {
var props  = {};
var reqArr = [];
var keys   = Object.keys(val);
for (var i = 0; i < keys.length; i++) {
var k = keys[i];
props[k] = inferSchema(val[k]);
reqArr.push(k);
}
return { type: 'object', properties: props, required: reqArr };
}

return {};
}

function buildRootSchema(parsed) {
var $schema = schemaVersion === '2020-12'
? 'https://json-schema.org/draft/2020-12/schema'
: 'http://json-schema.org/draft-07/schema#';

var inner = inferSchema(parsed);
var root  = Object.assign({ $schema: $schema }, inner);

if (root.properties) {
var keys    = Object.keys(root.properties);
var hasMeta = Object.keys(propMeta).length > 0;

for (var i = 0; i < keys.length; i++) {
var k    = keys[i];
var meta = propMeta[k] || {};
if (meta.description) root.properties[k].description = meta.description;
}

if (hasMeta) {
var newReq = [];
for (var j = 0; j < keys.length; j++) {
var kk = keys[j];
var m  = propMeta[kk];
if (!m || m.required !== false) newReq.push(kk);
}
root.required = newReq;
}
}

return root;
}

/* ────────────────────────────────────────
プロパティエディター描画
──────────────────────────────────────── */
function renderEditor(schema) {
var section = document.getElementById('jsg-editor-section');
var tbody   = document.getElementById('jsg-prop-tbody');

if (!schema || schema.type !== 'object' || !schema.properties) {
section.style.display = 'none';
return;
}

var keys   = Object.keys(schema.properties);
var reqSet = {};
if (schema.required) {
for (var i = 0; i < schema.required.length; i++) reqSet[schema.required[i]] = true;
}

tbody.innerHTML = '';
for (var j = 0; j < keys.length; j++) {
var k      = keys[j];
var prop   = schema.properties[k];
var meta   = propMeta[k] || {};
var typeStr = prop.type || '?';
if (prop.format) typeStr += ' (' + prop.format + ')';
var isReq  = propMeta[k] ? propMeta[k].required !== false : (reqSet[k] || false);
var descVal = meta.description || prop.description || '';

var tr = document.createElement('tr');
tr.innerHTML =
'<td class="jsg-prop-key">' + esc(k) + '</td>' +
'<td class="jsg-prop-type">' + esc(typeStr) + '</td>' +
'<td><input class="jsg-prop-desc-input" type="text" data-key="' + esc(k) + '" placeholder="説明を追加…" value="' + esc(descVal) + '"></td>' +
'<td style="text-align:center;"><input class="jsg-prop-req-chk" type="checkbox" data-key="' + esc(k) + '"' + (isReq ? ' checked' : '') + '></td>';
tbody.appendChild(tr);
}
section.style.display = 'block';
}

/* ────────────────────────────────────────
公開アクション
──────────────────────────────────────── */
window.jsgOnInput = function () {
updateInputStats();
setInputState('');
setError('');
};

window.jsgSetVersion = function (v) {
schemaVersion = v;
document.getElementById('jsg-v07').classList.toggle('active', v === 'draft-07');
document.getElementById('jsg-v20').classList.toggle('active', v === '2020-12');
if (lastInput !== null) jsgGenerate();
};

window.jsgGenerate = function () {
var r = parseInput();
if (!r) {
setOutputHTML('<span style="color:#45475a">// 左にJSONを貼り付けて「スキーマ生成」をクリックしてください</span>');
setOutputState('');
setOutStatus('');
document.getElementById('jsg-editor-section').style.display = 'none';
return;
}
if (!r.ok) {
setInputState('error');
setError('解析エラー' + (r.line ? '（' + r.line + '行目付近）' : '') + ': ' + r.error);
setOutputState('error');
setOutputHTML('<span style="color:#45475a">// JSONエラーを修正してください</span>');
setOutStatus('<span class="jsg-err">無効なJSON — スキーマを生成できません</span>');
document.getElementById('jsg-editor-section').style.display = 'none';
return;
}

setInputState('valid');
setError('');
lastInput = r.value;
propMeta  = {};

lastSchema = buildRootSchema(lastInput);
var pretty = JSON.stringify(lastSchema, null, 2);
setOutputHTML(syntaxHL(pretty));
setOutputState('valid');

var propCount = lastSchema.properties ? Object.keys(lastSchema.properties).length : 0;
setOutStatus(
'<span class="jsg-ok">スキーマ生成完了</span>' +
'<span class="jsg-info">' + schemaVersion + '</span>' +
'<span>プロパティ数: ' + propCount + '</span>' +
'<span>文字数: ' + pretty.length + '</span>'
);

renderEditor(lastSchema);
};

window.jsgApplyEdits = function () {
if (!lastInput) return;

var descInputs = document.querySelectorAll('#jsg-prop-tbody .jsg-prop-desc-input');
var reqChecks  = document.querySelectorAll('#jsg-prop-tbody .jsg-prop-req-chk');

propMeta = {};
for (var i = 0; i < descInputs.length; i++) {
var k = descInputs[i].getAttribute('data-key');
propMeta[k] = propMeta[k] || {};
propMeta[k].description = descInputs[i].value.trim();
}
for (var j = 0; j < reqChecks.length; j++) {
var kk = reqChecks[j].getAttribute('data-key');
propMeta[kk] = propMeta[kk] || {};
propMeta[kk].required = reqChecks[j].checked;
}

lastSchema = buildRootSchema(lastInput);
var pretty = JSON.stringify(lastSchema, null, 2);
setOutputHTML(syntaxHL(pretty));
setOutputState('valid');

var propCount = lastSchema.properties ? Object.keys(lastSchema.properties).length : 0;
setOutStatus(
'<span class="jsg-ok">スキーマ更新完了</span>' +
'<span class="jsg-info">' + schemaVersion + '</span>' +
'<span>プロパティ数: ' + propCount + '</span>' +
'<span>文字数: ' + pretty.length + '</span>'
);
showToast('スキーマを更新しました！');
};

window.jsgValidate = function () {
var r = parseInput();
if (!r) {
setError('検証するJSONを入力してください。');
return;
}
if (!r.ok) {
setInputState('error');
setError('解析エラー' + (r.line ? '（' + r.line + '行目付近）' : '') + ': ' + r.error);
setOutputState('error');
setOutputHTML('<span class="jsg-err" style="font-size:15px;font-weight:700;">無効なJSON</span>');
setOutStatus('<span class="jsg-err">JSONの構文が正しくありません</span>');
return;
}

if (!lastSchema) {
setInputState('valid');
setError('');
setOutputHTML('<span class="jsg-ok" style="font-size:14px;font-weight:700;">有効なJSON</span>\n\n<span style="color:#6c7086">// まずスキーマを生成してから検証してください。</span>');
setOutputState('valid');
setOutStatus('<span class="jsg-ok">JSONの構文は正しいです</span>');
return;
}

var errs = validateAgainstSchema(r.value, lastSchema, '$');
if (errs.length === 0) {
setInputState('valid');
setError('');
setOutputHTML('<span class="jsg-ok" style="font-size:15px;font-weight:700;">検証成功</span>\n\n<span style="color:#6c7086">// JSONは生成済みスキーマに準拠しています。</span>');
setOutputState('valid');
setOutStatus('<span class="jsg-ok">すべてのスキーマチェックを通過しました</span>');
} else {
setInputState('error');
setError('');
var errLines = errs.map(function (e) { return '  ' + e; }).join('\n');
setOutputHTML('<span class="jsg-err" style="font-size:15px;font-weight:700;">検証失敗</span>\n\n<span style="color:#f38ba8">' + esc(errLines) + '</span>');
setOutputState('error');
setOutStatus('<span class="jsg-err">' + errs.length + ' 件のエラーが見つかりました</span>');
}
};

/* ────────────────────────────────────────
構造バリデーター
──────────────────────────────────────── */
function validateAgainstSchema(val, schema, path) {
var errors = [];
if (!schema) return errors;

if (schema.type) {
var types      = Array.isArray(schema.type) ? schema.type : [schema.type];
var actualType = getType(val);
var matched    = false;
for (var i = 0; i < types.length; i++) {
if (types[i] === actualType) { matched = true; break; }
if (types[i] === 'integer' && actualType === 'number' && isInteger(val)) { matched = true; break; }
}
if (!matched) {
errors.push(path + ': ' + types.join('|') + ' が期待されましたが ' + actualType + ' でした');
}
}

if (schema.required && typeof val === 'object' && val !== null && !Array.isArray(val)) {
for (var r = 0; r < schema.required.length; r++) {
if (!Object.prototype.hasOwnProperty.call(val, schema.required[r])) {
errors.push(path + ': 必須プロパティ "' + schema.required[r] + '" がありません');
}
}
}

if (schema.properties && typeof val === 'object' && val !== null && !Array.isArray(val)) {
var pkeys = Object.keys(schema.properties);
for (var p = 0; p < pkeys.length; p++) {
var pk = pkeys[p];
if (Object.prototype.hasOwnProperty.call(val, pk)) {
var subErrs = validateAgainstSchema(val[pk], schema.properties[pk], path + '.' + pk);
errors = errors.concat(subErrs);
}
}
}

if (schema.items && Array.isArray(val)) {
for (var ai = 0; ai < val.length; ai++) {
var aErrs = validateAgainstSchema(val[ai], schema.items, path + '[' + ai + ']');
errors = errors.concat(aErrs);
}
}

return errors;
}

function getType(val) {
if (val === null)              return 'null';
if (typeof val === 'boolean')  return 'boolean';
if (typeof val === 'number')   return 'number';
if (typeof val === 'string')   return 'string';
if (Array.isArray(val))        return 'array';
if (typeof val === 'object')   return 'object';
return 'unknown';
}

/* ────────────────────────────────────────
コピー
──────────────────────────────────────── */
window.jsgCopy = function () {
var el   = document.getElementById('jsg-output');
var text = el.innerText || el.textContent;
if (!text || text.trim().startsWith('//')) return;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function () { showToast('コピーしました！'); });
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.cssText = 'position:fixed;opacity:0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
showToast('コピーしました！');
}
};

/* ────────────────────────────────────────
クリア
──────────────────────────────────────── */
window.jsgClear = function () {
document.getElementById('jsg-input').value = '';
setInputState('');
setError('');
updateInputStats();
setOutputHTML('<span style="color:#45475a">// 左にJSONを貼り付けて「スキーマ生成」をクリックするとここに表示されます</span>');
setOutputState('');
setOutStatus('');
lastSchema = null;
lastInput  = null;
propMeta   = {};
document.getElementById('jsg-editor-section').style.display = 'none';
document.getElementById('jsg-sample-select').value = '';
};

/* ────────────────────────────────────────
サンプルプリセット
──────────────────────────────────────── */
var SAMPLES = {
user: {
"id": "a3f8c2d1-4b7e-4f9a-8c1d-2e3f4a5b6c7d",
"username": "tanaka_taro",
"email": "tanaka@example.co.jp",
"age": 32,
"isPremium": true,
"score": 95.5,
"registeredAt": "2024-04-01T09:00:00Z",
"address": {
"prefecture": "東京都",
"city": "渋谷区",
"postalCode": "150-0001"
},
"roles": ["user", "editor"],
"deletedAt": null
},
product: {
"sku": "ITEM-00732",
"name": "ワイヤレスイヤホン Pro",
"description": "ノイズキャンセリング機能付き完全ワイヤレスイヤホン",
"price": 19800,
"currency": "JPY",
"inStock": true,
"quantity": 128,
"rating": 4.6,
"categories": ["電子機器", "オーディオ", "イヤホン"],
"images": [
{
"url": "https://example.com/images/earphone-main.jpg",
"alt": "正面から見た画像",
"isPrimary": true
}
],
"createdAt": "2024-01-10T00:00:00Z",
"updatedAt": "2025-03-20T14:30:00Z"
},
api: {
"status": "success",
"code": 200,
"message": "リクエストが正常に完了しました",
"data": {
"totalCount": 350,
"page": 1,
"pageSize": 20,
"hasNextPage": true,
"items": [
{
"id": 1,
"title": "サンプルアイテム",
"active": true,
"score": 0.88
}
]
},
"meta": {
"requestId": "req_7a3b2c1d",
"timestamp": "2025-05-16T10:00:00Z",
"version": "v3"
},
"errors": null
}
};

window.jsgLoadSample = function (key) {
if (!key || !SAMPLES[key]) return;
document.getElementById('jsg-input').value = JSON.stringify(SAMPLES[key], null, 2);
updateInputStats();
setInputState('');
setError('');
propMeta = {};
jsgGenerate();
};

updateInputStats();

})();
</script>

</div>

---

## JSONスキーマとは

JSONスキーマ（JSON Schema）は、JSONデータの構造を記述・検証するための仕様です。「このオブジェクトはどのようなプロパティを持つか」「各フィールドの型は何か」「どのフィールドが必須か」「文字列のフォーマットはどうあるべきか」といった制約を機械可読な形式で定義できます。APIの設計・ドキュメント生成・コード自動生成・入力バリデーションなど、様々な場面で活用されています。

広く使われているバージョンは **Draft-07**（ほぼすべての言語のバリデーションライブラリが対応）と、現行の安定仕様である **Draft 2020-12** です。このツールはボタン一つで両バージョンを切り替えられます。

---

## このJSONスキーマジェネレーターの使い方

**スキーマ生成** — 左の入力欄にJSONを貼り付けて「スキーマ生成」をクリックします。ツールは各値を再帰的に検査し、`true`/`false` を `boolean`、整数を `integer`、小数を `number`、`null` を `null`、配列・オブジェクトをそれぞれの型にマッピングします。文字列は日時（date-time）・メールアドレス（email）・URL（uri）・UUID のパターンを自動検出し、`format` キーワードを付加します。

**スキーマバージョン切替** — 「Draft-07」または「2020-12」ボタンで `$schema` URIを切り替えます。入力済みの場合は即座に再生成されます。

**プロパティ編集** — スキーマ生成後、下部に「スキーマプロパティを編集」テーブルが表示されます。各プロパティに `description`（説明文）を追加し、「必須」チェックボックスで `required` 配列を制御できます。「編集を適用して再生成」をクリックすると反映されます。

**JSONを検証** — 「JSONを検証」をクリックすると、入力JSONを生成済みスキーマと照合します。型の不一致・必須フィールドの欠落・ネスト構造のエラーをJSONパスとともに報告します。

**サンプルプリセット** — 「サンプル」ドロップダウンから3種類の例を読み込めます。**ユーザーオブジェクト**（UUID・メール・日時・ネスト住所・ロール配列）、**商品カタログ**（価格・評価・画像配列）、**APIレスポンス**（ページネーション・ネストデータ・メタ情報）。

**スキーマをコピー** — 「スキーマをコピー」ボタンで生成済みスキーマをクリップボードに一発コピーできます。

---

### 関連ツール

> JSONを整形 → [JSONフォーマッター](/ja/tools/json-formatter/)

> JSONをCSVに変換 → [JSON to CSV](/ja/tools/json-to-csv/)

> YAML ↔ JSON を相互変換 → [YAML↔JSONコンバーター](/ja/tools/yaml-json-converter/)

---

**エンジニア・フリーランスの確定申告を自動化**

開発に集中したいのに、経理業務に時間を取られていませんか？クラウド会計ソフト「freee」なら、銀行口座・クレジットカードと自動連携。確定申告もワンクリック。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
