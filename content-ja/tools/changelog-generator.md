---
title: "変更履歴ジェネレーター — リリースノート作成ツール"
date: 2025-07-31
description: "Keep a Changelog形式で変更履歴・リリースノートを生成。カテゴリ別にエントリ追加、マークダウンでプレビュー、コピー・ダウンロード。無料・登録不要。"
categories: ["無料ツール"]
tags: ["開発ツール", "ドキュメント", "無料ツール"]
slug: "changelog-generator"
ShowToc: false
aliases:
  - "/ja/tools/changelog-generator/"
  - "/ja/tools/changelog-generator/"
cover:
  image: "/images/covers/changelog-generator-ja.png"
  alt: "変更履歴ジェネレーター"
---

[Keep a Changelog](https://keepachangelog.com/ja/1.0.0/) 形式で変更履歴・リリースノートを作成できます。バージョン情報を入力し、カテゴリ別に変更点を追加して、マークダウン・HTML・プレーンテキストでコピー・ダウンロードできます。無料・登録不要。

<div id="cl-app">
<style>
#cl-app *,
#cl-app *::before,
#cl-app *::after {
box-sizing: border-box;
}
#cl-app {
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, sans-serif;
font-size: 15px;
color: #1a1a2e;
margin: 0 auto;
max-width: 900px;
}
#cl-app h2 {
font-size: 1.05rem;
font-weight: 700;
margin: 0 0 12px 0;
color: #1a1a2e;
}
#cl-app .cl-section {
background: #f8f9fc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 20px;
margin-bottom: 18px;
}
#cl-app .cl-row {
display: flex;
gap: 14px;
flex-wrap: wrap;
}
#cl-app .cl-field {
display: flex;
flex-direction: column;
gap: 5px;
flex: 1;
min-width: 180px;
}
#cl-app label {
font-size: 0.8rem;
font-weight: 700;
color: #4a5568;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#cl-app input[type="text"],
#cl-app input[type="date"],
#cl-app select,
#cl-app textarea {
width: 100%;
padding: 9px 12px;
border: 1px solid #cbd5e0;
border-radius: 7px;
font-size: 0.95rem;
font-family: inherit;
background: #fff;
color: #1a1a2e;
transition: border-color 0.18s;
outline: none;
}
#cl-app input[type="text"]:focus,
#cl-app input[type="date"]:focus,
#cl-app select:focus,
#cl-app textarea:focus {
border-color: #667eea;
box-shadow: 0 0 0 3px rgba(102,126,234,0.12);
}
#cl-app .cl-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
}
#cl-app .cl-preset-btn {
padding: 6px 14px;
border-radius: 20px;
border: 1.5px solid #667eea;
background: #fff;
color: #667eea;
font-size: 0.83rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s, color 0.15s;
font-family: inherit;
}
#cl-app .cl-preset-btn:hover {
background: #667eea;
color: #fff;
}
#cl-app .cl-category {
border: 1px solid #e2e8f0;
border-radius: 9px;
margin-bottom: 12px;
overflow: hidden;
background: #fff;
}
#cl-app .cl-cat-header {
display: flex;
align-items: center;
gap: 10px;
padding: 10px 14px;
cursor: pointer;
user-select: none;
background: #fff;
border-bottom: 1px solid #e2e8f0;
}
#cl-app .cl-cat-header:hover {
background: #f0f4ff;
}
#cl-app .cl-cat-badge {
display: inline-block;
padding: 2px 10px;
border-radius: 12px;
font-size: 0.78rem;
font-weight: 700;
letter-spacing: 0.02em;
}
#cl-app .cl-cat-added     .cl-cat-badge { background: #c6f6d5; color: #22543d; }
#cl-app .cl-cat-changed   .cl-cat-badge { background: #bee3f8; color: #2a4365; }
#cl-app .cl-cat-deprecated .cl-cat-badge { background: #fefcbf; color: #744210; }
#cl-app .cl-cat-removed   .cl-cat-badge { background: #fed7d7; color: #742a2a; }
#cl-app .cl-cat-fixed     .cl-cat-badge { background: #e9d8fd; color: #44337a; }
#cl-app .cl-cat-security  .cl-cat-badge { background: #feebc8; color: #7b341e; }
#cl-app .cl-cat-toggle {
margin-left: auto;
font-size: 0.8rem;
color: #718096;
}
#cl-app .cl-cat-count {
font-size: 0.78rem;
color: #718096;
background: #edf2f7;
border-radius: 10px;
padding: 1px 8px;
}
#cl-app .cl-cat-body {
padding: 12px 14px;
}
#cl-app .cl-entry-row {
display: flex;
gap: 8px;
margin-bottom: 8px;
align-items: center;
}
#cl-app .cl-entry-input {
flex: 1;
}
#cl-app .cl-remove-btn {
background: #fff5f5;
border: 1px solid #feb2b2;
color: #c53030;
border-radius: 6px;
padding: 6px 10px;
cursor: pointer;
font-size: 0.85rem;
font-weight: 700;
transition: background 0.15s;
flex-shrink: 0;
font-family: inherit;
}
#cl-app .cl-remove-btn:hover {
background: #fed7d7;
}
#cl-app .cl-add-btn {
background: #ebf8ff;
border: 1px dashed #90cdf4;
color: #2b6cb0;
border-radius: 7px;
padding: 7px 14px;
cursor: pointer;
font-size: 0.85rem;
font-weight: 600;
width: 100%;
margin-top: 4px;
transition: background 0.15s;
font-family: inherit;
}
#cl-app .cl-add-btn:hover {
background: #bee3f8;
}
#cl-app .cl-format-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 14px;
}
#cl-app .cl-tab {
padding: 8px 20px;
border: none;
background: transparent;
font-size: 0.9rem;
font-weight: 700;
color: #718096;
cursor: pointer;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
font-family: inherit;
}
#cl-app .cl-tab.active {
color: #667eea;
border-bottom-color: #667eea;
}
#cl-app .cl-tab:hover:not(.active) {
color: #4a5568;
}
#cl-app .cl-preview-box {
background: #1a202c;
color: #e2e8f0;
border-radius: 8px;
padding: 18px 20px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.85rem;
line-height: 1.7;
white-space: pre-wrap;
word-break: break-word;
min-height: 180px;
max-height: 420px;
overflow-y: auto;
}
#cl-app .cl-preview-box.html-mode {
background: #fff;
color: #1a1a2e;
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, sans-serif;
font-size: 0.95rem;
border: 1px solid #e2e8f0;
line-height: 1.8;
white-space: normal;
}
#cl-app .cl-action-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 14px;
}
#cl-app .cl-btn {
padding: 9px 20px;
border-radius: 7px;
border: none;
font-size: 0.9rem;
font-weight: 700;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
font-family: inherit;
}
#cl-app .cl-btn:active {
transform: scale(0.97);
}
#cl-app .cl-btn-primary {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: #fff;
}
#cl-app .cl-btn-secondary {
background: #edf2f7;
color: #2d3748;
}
#cl-app .cl-btn-danger {
background: #fff5f5;
border: 1px solid #feb2b2;
color: #c53030;
}
#cl-app .cl-btn:hover {
opacity: 0.88;
}
#cl-app .cl-toast {
display: none;
position: fixed;
bottom: 24px;
right: 24px;
background: #2d3748;
color: #fff;
padding: 10px 20px;
border-radius: 8px;
font-size: 0.9rem;
font-weight: 700;
z-index: 9999;
box-shadow: 0 4px 16px rgba(0,0,0,0.18);
animation: cl-fadein 0.2s ease;
font-family: inherit;
}
@keyframes cl-fadein {
from { opacity: 0; transform: translateY(8px); }
to   { opacity: 1; transform: translateY(0); }
}
#cl-app .cl-append-area {
width: 100%;
min-height: 90px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 0.83rem;
resize: vertical;
}
#cl-app .cl-info {
font-size: 0.82rem;
color: #718096;
margin-top: 6px;
}
#cl-app .cl-section-title {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.05em;
color: #667eea;
margin-bottom: 10px;
}
#cl-app .cl-cta {
background: linear-gradient(135deg, #f0f4ff 0%, #faf5ff 100%);
border: 1.5px solid #c3dafe;
border-radius: 10px;
padding: 20px 22px;
margin-top: 28px;
display: flex;
gap: 16px;
align-items: flex-start;
flex-wrap: wrap;
}
#cl-app .cl-cta-icon {
font-size: 2rem;
flex-shrink: 0;
line-height: 1;
}
#cl-app .cl-cta-body { flex: 1; min-width: 220px; }
#cl-app .cl-cta-body strong {
display: block;
font-size: 1rem;
font-weight: 700;
color: #434190;
margin-bottom: 4px;
}
#cl-app .cl-cta-body p {
font-size: 0.88rem;
color: #4a5568;
margin: 0 0 12px 0;
line-height: 1.6;
}
#cl-app .cl-cta-link {
display: inline-block;
background: #667eea;
color: #fff;
padding: 8px 18px;
border-radius: 7px;
font-size: 0.88rem;
font-weight: 700;
text-decoration: none;
transition: background 0.15s;
}
#cl-app .cl-cta-link:hover { background: #5a67d8; }
@media (max-width: 600px) {
#cl-app .cl-row { flex-direction: column; }
#cl-app .cl-tab { padding: 8px 10px; font-size: 0.8rem; }
#cl-app .cl-action-row { flex-direction: column; }
#cl-app .cl-btn { width: 100%; text-align: center; }
#cl-app .cl-cta { flex-direction: column; }
}
</style>

<!-- プリセット -->
<div class="cl-section">
<div class="cl-section-title">クイックプリセット</div>
<div class="cl-presets">
<button class="cl-preset-btn" onclick="clApplyPreset('major')">メジャーリリース</button>
<button class="cl-preset-btn" onclick="clApplyPreset('minor')">マイナーアップデート</button>
<button class="cl-preset-btn" onclick="clApplyPreset('patch')">パッチ / バグ修正</button>
<button class="cl-preset-btn" onclick="clApplyPreset('security')">セキュリティ更新</button>
<button class="cl-preset-btn" onclick="clApplyPreset('clear')">すべてクリア</button>
</div>
</div>

<!-- リリース情報 -->
<div class="cl-section">
<h2>リリース情報</h2>
<div class="cl-row">
<div class="cl-field">
<label for="cl-version">バージョン番号</label>
<input type="text" id="cl-version" placeholder="例: 2.1.0" />
</div>
<div class="cl-field">
<label for="cl-date">リリース日</label>
<input type="date" id="cl-date" />
</div>
<div class="cl-field">
<label for="cl-project">プロジェクト名（任意）</label>
<input type="text" id="cl-project" placeholder="例: マイアプリ" />
</div>
</div>
</div>

<!-- カテゴリ別エントリ -->
<div class="cl-section">
<h2>変更エントリ</h2>

<div class="cl-category cl-cat-added" id="cl-cat-added">
<div class="cl-cat-header" onclick="clToggleCat('added')">
<span class="cl-cat-badge">追加 (Added)</span>
<span class="cl-cat-count" id="cl-count-added">0</span>
<span class="cl-cat-toggle" id="cl-toggle-added">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-added">
<div id="cl-entries-added"></div>
<button class="cl-add-btn" onclick="clAddEntry('added')">+ エントリを追加</button>
</div>
</div>

<div class="cl-category cl-cat-changed" id="cl-cat-changed">
<div class="cl-cat-header" onclick="clToggleCat('changed')">
<span class="cl-cat-badge">変更 (Changed)</span>
<span class="cl-cat-count" id="cl-count-changed">0</span>
<span class="cl-cat-toggle" id="cl-toggle-changed">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-changed">
<div id="cl-entries-changed"></div>
<button class="cl-add-btn" onclick="clAddEntry('changed')">+ エントリを追加</button>
</div>
</div>

<div class="cl-category cl-cat-deprecated" id="cl-cat-deprecated">
<div class="cl-cat-header" onclick="clToggleCat('deprecated')">
<span class="cl-cat-badge">非推奨 (Deprecated)</span>
<span class="cl-cat-count" id="cl-count-deprecated">0</span>
<span class="cl-cat-toggle" id="cl-toggle-deprecated">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-deprecated">
<div id="cl-entries-deprecated"></div>
<button class="cl-add-btn" onclick="clAddEntry('deprecated')">+ エントリを追加</button>
</div>
</div>

<div class="cl-category cl-cat-removed" id="cl-cat-removed">
<div class="cl-cat-header" onclick="clToggleCat('removed')">
<span class="cl-cat-badge">削除 (Removed)</span>
<span class="cl-cat-count" id="cl-count-removed">0</span>
<span class="cl-cat-toggle" id="cl-toggle-removed">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-removed">
<div id="cl-entries-removed"></div>
<button class="cl-add-btn" onclick="clAddEntry('removed')">+ エントリを追加</button>
</div>
</div>

<div class="cl-category cl-cat-fixed" id="cl-cat-fixed">
<div class="cl-cat-header" onclick="clToggleCat('fixed')">
<span class="cl-cat-badge">修正 (Fixed)</span>
<span class="cl-cat-count" id="cl-count-fixed">0</span>
<span class="cl-cat-toggle" id="cl-toggle-fixed">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-fixed">
<div id="cl-entries-fixed"></div>
<button class="cl-add-btn" onclick="clAddEntry('fixed')">+ エントリを追加</button>
</div>
</div>

<div class="cl-category cl-cat-security" id="cl-cat-security">
<div class="cl-cat-header" onclick="clToggleCat('security')">
<span class="cl-cat-badge">セキュリティ (Security)</span>
<span class="cl-cat-count" id="cl-count-security">0</span>
<span class="cl-cat-toggle" id="cl-toggle-security">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-security">
<div id="cl-entries-security"></div>
<button class="cl-add-btn" onclick="clAddEntry('security')">+ エントリを追加</button>
</div>
</div>
</div>

<!-- 既存の変更履歴に追記 -->
<div class="cl-section">
<h2>既存の変更履歴に追記</h2>
<p class="cl-info">既存の変更履歴を貼り付けると、新しいリリースをその上に追記します。</p>
<textarea class="cl-append-area" id="cl-existing" placeholder="# Changelog&#10;&#10;## [1.0.0] - 2025-01-01&#10;..."></textarea>
</div>

<!-- 出力フォーマット + プレビュー -->
<div class="cl-section">
<h2>プレビューと出力</h2>
<div class="cl-format-tabs">
<button class="cl-tab active" id="cl-tab-md"   onclick="clSetFormat('md')">Markdown</button>
<button class="cl-tab"        id="cl-tab-html" onclick="clSetFormat('html')">HTML</button>
<button class="cl-tab"        id="cl-tab-txt"  onclick="clSetFormat('txt')">プレーンテキスト</button>
</div>
<div class="cl-preview-box" id="cl-preview" aria-live="polite"></div>
<div class="cl-action-row">
<button class="cl-btn cl-btn-primary"    onclick="clCopy()">クリップボードにコピー</button>
<button class="cl-btn cl-btn-secondary"  onclick="clDownload()">ファイルをダウンロード</button>
<button class="cl-btn cl-btn-danger"     onclick="clReset()">リセット</button>
</div>
</div>

<div class="cl-toast" id="cl-toast"></div>

<script>
(function () {
var CL = {
format: 'md',
collapsed: {},
cats: ['added', 'changed', 'deprecated', 'removed', 'fixed', 'security'],
catLabels: {
added: '追加',
changed: '変更',
deprecated: '非推奨',
removed: '削除',
fixed: '修正',
security: 'セキュリティ'
},
catLabelsEn: {
added: 'Added',
changed: 'Changed',
deprecated: 'Deprecated',
removed: 'Removed',
fixed: 'Fixed',
security: 'Security'
}
};

function $(id) { return document.getElementById(id); }

function clShowToast(msg) {
var t = $('cl-toast');
t.textContent = msg;
t.style.display = 'block';
setTimeout(function () { t.style.display = 'none'; }, 2200);
}

function clTodayISO() {
var d = new Date();
return d.toISOString().split('T')[0];
}

function clGetEntries(cat) {
var inputs = $('cl-entries-' + cat).querySelectorAll('input[type="text"]');
var vals = [];
inputs.forEach(function (inp) {
var v = inp.value.trim();
if (v) vals.push(v);
});
return vals;
}

function clUpdateCount(cat) {
var n = $('cl-entries-' + cat).querySelectorAll('.cl-entry-row').length;
$('cl-count-' + cat).textContent = n;
}

window.clToggleCat = function (cat) {
var body = $('cl-body-' + cat);
var tog  = $('cl-toggle-' + cat);
if (CL.collapsed[cat]) {
body.style.display = '';
tog.innerHTML = '&#9660;';
CL.collapsed[cat] = false;
} else {
body.style.display = 'none';
tog.innerHTML = '&#9654;';
CL.collapsed[cat] = true;
}
};

window.clAddEntry = function (cat, value) {
var container = $('cl-entries-' + cat);
var row = document.createElement('div');
row.className = 'cl-entry-row';
var inp = document.createElement('input');
inp.type = 'text';
inp.className = 'cl-entry-input';
inp.placeholder = '変更内容を入力…';
if (value) inp.value = value;
inp.addEventListener('input', clUpdatePreview);
var btn = document.createElement('button');
btn.className = 'cl-remove-btn';
btn.textContent = '×';
btn.addEventListener('click', function () {
row.remove();
clUpdateCount(cat);
clUpdatePreview();
});
row.appendChild(inp);
row.appendChild(btn);
container.appendChild(row);
clUpdateCount(cat);
clUpdatePreview();
inp.focus();
};

window.clSetFormat = function (fmt) {
CL.format = fmt;
['md','html','txt'].forEach(function (f) {
$('cl-tab-' + f).classList.toggle('active', f === fmt);
});
clUpdatePreview();
};

function clBuildMd() {
var version = $('cl-version').value.trim() || 'X.Y.Z';
var date    = $('cl-date').value    || clTodayISO();
var project = $('cl-project').value.trim();
var lines   = [];

if (project) lines.push('# ' + project + ' 変更履歴\n');
lines.push('## [' + version + '] - ' + date);

CL.cats.forEach(function (cat) {
var entries = clGetEntries(cat);
if (entries.length) {
lines.push('\n### ' + CL.catLabelsEn[cat]);
entries.forEach(function (e) { lines.push('- ' + e); });
}
});

var existing = $('cl-existing').value.trim();
if (existing) lines.push('\n---\n\n' + existing);

return lines.join('\n');
}

function clBuildHtml() {
var version = $('cl-version').value.trim() || 'X.Y.Z';
var date    = $('cl-date').value    || clTodayISO();
var project = $('cl-project').value.trim();
var html    = [];

if (project) html.push('<h1>' + clEsc(project) + ' 変更履歴</h1>');
html.push('<h2>[' + clEsc(version) + '] &mdash; ' + clEsc(date) + '</h2>');

CL.cats.forEach(function (cat) {
var entries = clGetEntries(cat);
if (entries.length) {
html.push('<h3>' + CL.catLabelsEn[cat] + ' (' + CL.catLabels[cat] + ')</h3>');
html.push('<ul>');
entries.forEach(function (e) { html.push('  <li>' + clEsc(e) + '</li>'); });
html.push('</ul>');
}
});

var existing = $('cl-existing').value.trim();
if (existing) {
html.push('<hr>');
html.push('<pre>' + clEsc(existing) + '</pre>');
}

return html.join('\n');
}

function clBuildTxt() {
var version = $('cl-version').value.trim() || 'X.Y.Z';
var date    = $('cl-date').value    || clTodayISO();
var project = $('cl-project').value.trim();
var lines   = [];
var bar     = '='.repeat(50);
var dash    = '-'.repeat(30);

if (project) {
lines.push(bar);
lines.push(project + ' 変更履歴');
lines.push(bar);
lines.push('');
}
lines.push('リリース: v' + version + '  |  日付: ' + date);
lines.push(dash);

CL.cats.forEach(function (cat) {
var entries = clGetEntries(cat);
if (entries.length) {
lines.push('');
lines.push('[' + CL.catLabelsEn[cat].toUpperCase() + ' / ' + CL.catLabels[cat] + ']');
entries.forEach(function (e) { lines.push('  * ' + e); });
}
});

var existing = $('cl-existing').value.trim();
if (existing) { lines.push(''); lines.push(bar); lines.push(existing); }

return lines.join('\n');
}

function clEsc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function clUpdatePreview() {
var box = $('cl-preview');
if (CL.format === 'html') {
box.classList.add('html-mode');
box.innerHTML = clBuildHtml();
} else {
box.classList.remove('html-mode');
box.textContent = CL.format === 'md' ? clBuildMd() : clBuildTxt();
}
}

window.clCopy = function () {
var text = CL.format === 'html' ? clBuildHtml() : (CL.format === 'md' ? clBuildMd() : clBuildTxt());
navigator.clipboard.writeText(text).then(function () {
clShowToast('クリップボードにコピーしました');
}).catch(function () {
clShowToast('コピーに失敗しました。手動でテキストを選択してください。');
});
};

window.clDownload = function () {
var ext  = CL.format === 'html' ? 'html' : (CL.format === 'md' ? 'md' : 'txt');
var mime = CL.format === 'html' ? 'text/html' : 'text/plain';
var text = CL.format === 'html' ? clBuildHtml() : (CL.format === 'md' ? clBuildMd() : clBuildTxt());
var version = ($('cl-version').value.trim() || 'changelog').replace(/\s+/g,'-');
var blob = new Blob([text], {type: mime + ';charset=utf-8'});
var a = document.createElement('a');
a.href = URL.createObjectURL(blob);
a.download = 'CHANGELOG-' + version + '.' + ext;
a.click();
URL.revokeObjectURL(a.href);
clShowToast('ファイルをダウンロードしました');
};

window.clReset = function () {
if (!confirm('すべてリセットしますか？')) return;
$('cl-version').value = '';
$('cl-date').value = '';
$('cl-project').value = '';
$('cl-existing').value = '';
CL.cats.forEach(function (cat) {
$('cl-entries-' + cat).innerHTML = '';
clUpdateCount(cat);
});
clUpdatePreview();
};

window.clApplyPreset = function (preset) {
CL.cats.forEach(function (cat) {
$('cl-entries-' + cat).innerHTML = '';
clUpdateCount(cat);
});

$('cl-date').value = clTodayISO();

if (preset === 'clear') {
$('cl-version').value = '';
$('cl-project').value = '';
$('cl-existing').value = '';
clUpdatePreview();
return;
}

if (preset === 'major') {
$('cl-version').value = '2.0.0';
clAddEntry('added',   'ユーザーインターフェースを全面リデザイン');
clAddEntry('added',   '新しいAPI v2（パフォーマンス大幅向上）');
clAddEntry('added',   'ダークモード対応');
clAddEntry('changed', '認証システムを新方式に移行');
clAddEntry('changed', 'スケーラビリティ向上のためDBスキーマ変更');
clAddEntry('removed', '非推奨だったv1 APIエンドポイントを削除');
clAddEntry('fixed',   '高負荷時の重大なパフォーマンス問題を修正');
} else if (preset === 'minor') {
$('cl-version').value = '1.3.0';
clAddEntry('added',   'CSVエクスポート機能を追加');
clAddEntry('added',   'よく使う操作のキーボードショートカットを追加');
clAddEntry('changed', 'リクエスト失敗時のエラーメッセージを改善');
clAddEntry('deprecated', 'レガシーインポート形式（v2.0で削除予定）');
clAddEntry('fixed',   '検索結果のページネーションが機能しない問題を修正');
} else if (preset === 'patch') {
$('cl-version').value = '1.2.1';
clAddEntry('fixed', 'iOS 17で設定画面を開くとクラッシュする問題を修正');
clAddEntry('fixed', 'サマリービューで合計値が誤って表示される問題を修正');
clAddEntry('fixed', 'セッションタイムアウト後のログインループを修正');
} else if (preset === 'security') {
$('cl-version').value = '1.2.2';
clAddEntry('security', 'コメント欄のXSS脆弱性を修正 (CVE-2025-XXXX)');
clAddEntry('security', '既知の脆弱性に対応するため依存パッケージを更新');
clAddEntry('fixed',    'エッジケースで入力バリデーションが回避できる問題を修正');
}

clUpdatePreview();
};

/* 初期化 */
$('cl-date').value = clTodayISO();
['cl-version','cl-date','cl-project','cl-existing'].forEach(function (id) {
$(id).addEventListener('input', clUpdatePreview);
});
clUpdatePreview();
})();
</script>

<!-- freee CTA -->
<div class="cl-cta">
<div class="cl-cta-icon">&#128200;</div>
<div class="cl-cta-body">
<strong>リリース管理と経費・請求書をまとめて効率化</strong>
<p>開発チームの経費精算・請求書発行・給与計算を自動化するなら freee が便利です。無料プランから始められます。</p>
<a class="cl-cta-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee を無料で試す</a>
</div>
</div>
</div>

---

### 関連ツール

> Markdownをプレビュー → [Markdownプレビュー](/ja/tools/markdown-preview/)
> Markdownテーブルを作成 → [Markdownテーブルジェネレーター](/ja/tools/markdown-table-generator/)
> JSONを整形 → [JSONフォーマッター](/ja/tools/json-formatter/)
