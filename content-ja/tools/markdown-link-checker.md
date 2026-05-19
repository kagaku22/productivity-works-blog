---
title: "マークダウンリンクチェッカー — リンク抽出・検証"
date: 2025-05-28
description: "マークダウンテキストからリンクを抽出・検証。重複・不正形式の検出、内部/外部リンクの分類。CSV・JSONでエクスポート。"
categories: ["無料ツール"]
slug: "markdown-link-checker"
ShowToc: false
cover:
  image: "/images/covers/markdown-link-checker-ja.png"
  alt: "マークダウンリンクチェッカー"
---

マークダウンテキストを貼り付けると、含まれるリンクをすべて抽出・分類し、重複や不正な形式を検出。結果はCSVまたはJSONでエクスポートできます。

<div id="mlc-app">

<style>
#mlc-app *,
#mlc-app *::before,
#mlc-app *::after {
box-sizing: border-box;
}

#mlc-app {
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
font-size: 15px;
color: #1a1a2e;
max-width: 860px;
margin: 0 auto;
padding: 0;
}

#mlc-app h2.mlc-section-title {
font-size: 1.05rem;
font-weight: 700;
margin: 0 0 10px 0;
color: #0f3460;
letter-spacing: 0.03em;
}

/* Input area */
#mlc-app .mlc-input-wrap {
background: #f8f9ff;
border: 1.5px solid #d0d7f7;
border-radius: 10px;
padding: 18px;
margin-bottom: 14px;
}

#mlc-app textarea#mlc-input {
width: 100%;
min-height: 180px;
border: 1.5px solid #c3cde8;
border-radius: 7px;
padding: 12px 14px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.6;
resize: vertical;
outline: none;
background: #fff;
color: #1a1a2e;
transition: border-color 0.2s;
}
#mlc-app textarea#mlc-input:focus {
border-color: #4361ee;
}
#mlc-app textarea#mlc-input::placeholder {
color: #9aa5c4;
}

/* Buttons */
#mlc-app .mlc-btn-row {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 12px;
align-items: center;
}

#mlc-app button.mlc-btn {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 8px 18px;
border: none;
border-radius: 6px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: background 0.18s, transform 0.1s;
white-space: nowrap;
letter-spacing: 0.02em;
}
#mlc-app button.mlc-btn:active {
transform: scale(0.97);
}

#mlc-app button#mlc-analyze-btn {
background: #4361ee;
color: #fff;
}
#mlc-app button#mlc-analyze-btn:hover {
background: #3451d1;
}

#mlc-app button#mlc-clear-btn {
background: #eef0fb;
color: #4361ee;
border: 1.5px solid #c3cde8;
}
#mlc-app button#mlc-clear-btn:hover {
background: #dde1f6;
}

#mlc-app button.mlc-btn-export {
background: #16213e;
color: #fff;
}
#mlc-app button.mlc-btn-export:hover {
background: #0f3460;
}

#mlc-app button#mlc-copy-urls-btn {
background: #e8f5e9;
color: #2e7d32;
border: 1.5px solid #a5d6a7;
}
#mlc-app button#mlc-copy-urls-btn:hover {
background: #c8e6c9;
}

/* Stats bar */
#mlc-app .mlc-stats-bar {
display: none;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 14px;
}

#mlc-app .mlc-stat-chip {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 5px 13px;
border-radius: 20px;
font-size: 13px;
font-weight: 700;
background: #eef0fb;
color: #0f3460;
border: 1px solid #d0d7f7;
}

#mlc-app .mlc-stat-chip.chip-total  { background: #e8eaf6; border-color: #9fa8da; color: #283593; }
#mlc-app .mlc-stat-chip.chip-ext    { background: #e3f2fd; border-color: #90caf9; color: #1565c0; }
#mlc-app .mlc-stat-chip.chip-int    { background: #e8f5e9; border-color: #a5d6a7; color: #2e7d32; }
#mlc-app .mlc-stat-chip.chip-img    { background: #fff3e0; border-color: #ffcc80; color: #e65100; }
#mlc-app .mlc-stat-chip.chip-anchor { background: #f3e5f5; border-color: #ce93d8; color: #6a1b9a; }
#mlc-app .mlc-stat-chip.chip-dup    { background: #fce4ec; border-color: #f48fb1; color: #880e4f; }
#mlc-app .mlc-stat-chip.chip-broken { background: #ffebee; border-color: #ef9a9a; color: #b71c1c; }

/* Filter tabs */
#mlc-app .mlc-filter-row {
display: none;
flex-wrap: wrap;
gap: 6px;
margin-bottom: 12px;
}

#mlc-app button.mlc-filter-tab {
padding: 5px 14px;
border-radius: 20px;
border: 1.5px solid #c3cde8;
background: #fff;
color: #4361ee;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#mlc-app button.mlc-filter-tab:hover,
#mlc-app button.mlc-filter-tab.active {
background: #4361ee;
color: #fff;
border-color: #4361ee;
}

/* Table */
#mlc-app .mlc-results-wrap {
display: none;
overflow-x: auto;
border: 1.5px solid #d0d7f7;
border-radius: 10px;
margin-bottom: 14px;
}

#mlc-app table.mlc-table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
min-width: 580px;
}

#mlc-app table.mlc-table thead tr {
background: #0f3460;
color: #fff;
}

#mlc-app table.mlc-table thead th {
padding: 10px 13px;
text-align: left;
font-weight: 700;
white-space: nowrap;
}

#mlc-app table.mlc-table tbody tr {
border-bottom: 1px solid #e8edf7;
transition: background 0.1s;
}
#mlc-app table.mlc-table tbody tr:last-child {
border-bottom: none;
}
#mlc-app table.mlc-table tbody tr:hover {
background: #f0f3ff;
}

#mlc-app table.mlc-table td {
padding: 9px 13px;
vertical-align: top;
word-break: break-word;
}

#mlc-app .mlc-badge {
display: inline-block;
padding: 2px 8px;
border-radius: 10px;
font-size: 11px;
font-weight: 700;
white-space: nowrap;
letter-spacing: 0.02em;
}
#mlc-app .badge-external { background: #e3f2fd; color: #1565c0; }
#mlc-app .badge-internal { background: #e8f5e9; color: #2e7d32; }
#mlc-app .badge-image    { background: #fff3e0; color: #e65100; }
#mlc-app .badge-anchor   { background: #f3e5f5; color: #6a1b9a; }
#mlc-app .badge-dup      { background: #fce4ec; color: #880e4f; margin-left: 4px; }
#mlc-app .badge-broken   { background: #ffebee; color: #b71c1c; margin-left: 4px; }

#mlc-app .mlc-url-cell {
max-width: 300px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}
#mlc-app .mlc-url-cell a {
color: #4361ee;
text-decoration: none;
}
#mlc-app .mlc-url-cell a:hover {
text-decoration: underline;
}

/* Toast */
#mlc-app .mlc-toast {
display: none;
position: fixed;
bottom: 28px;
right: 28px;
background: #1a1a2e;
color: #fff;
padding: 10px 22px;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
z-index: 9999;
box-shadow: 0 4px 16px rgba(0,0,0,0.25);
pointer-events: none;
}

#mlc-app .mlc-empty {
text-align: center;
padding: 40px 20px;
color: #9aa5c4;
font-size: 14px;
}

/* Action row */
#mlc-app .mlc-action-row {
display: none;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 18px;
}

/* Cross-links */
#mlc-app .mlc-crosslinks {
border-top: 1.5px solid #e0e4f7;
padding-top: 16px;
margin-top: 8px;
}
#mlc-app .mlc-crosslinks p {
margin: 0 0 8px 0;
font-size: 13px;
color: #555e7a;
}
#mlc-app .mlc-crosslinks a {
color: #4361ee;
text-decoration: none;
font-weight: 600;
margin-right: 10px;
}
#mlc-app .mlc-crosslinks a:hover {
text-decoration: underline;
}

/* freee CTA */
#mlc-app .mlc-freee-cta {
margin-top: 20px;
background: linear-gradient(135deg, #e8f4fd 0%, #f0f8ff 100%);
border: 1.5px solid #90caf9;
border-radius: 12px;
padding: 18px 20px;
}
#mlc-app .mlc-freee-cta h3 {
margin: 0 0 8px 0;
font-size: 1rem;
font-weight: 700;
color: #0f3460;
}
#mlc-app .mlc-freee-cta p {
margin: 0 0 14px 0;
font-size: 13px;
color: #374151;
line-height: 1.65;
}
#mlc-app .mlc-freee-cta a.mlc-freee-btn {
display: inline-block;
background: #1a73e8;
color: #fff;
padding: 9px 22px;
border-radius: 7px;
font-size: 14px;
font-weight: 700;
text-decoration: none;
transition: background 0.18s;
}
#mlc-app .mlc-freee-cta a.mlc-freee-btn:hover {
background: #1557b0;
}

/* Responsive */
@media (max-width: 600px) {
#mlc-app .mlc-btn-row { flex-direction: column; }
#mlc-app button.mlc-btn { width: 100%; justify-content: center; }
#mlc-app .mlc-action-row { flex-direction: column; }
#mlc-app .mlc-url-cell { max-width: 160px; }
}
</style>

<!-- 入力エリア -->
<div class="mlc-input-wrap">
<h2 class="mlc-section-title">マークダウンを貼り付け</h2>
<textarea id="mlc-input" placeholder="マークダウンをここに貼り付けてください...&#10;&#10;例：&#10;[Google](https://google.com)&#10;![ロゴ](https://example.com/logo.png)&#10;[概要](#about)&#10;[内部ページ](/blog/post)"></textarea>
<div class="mlc-btn-row">
<button class="mlc-btn" id="mlc-analyze-btn" onclick="mlcAnalyze()">リンクを抽出</button>
<button class="mlc-btn" id="mlc-clear-btn" onclick="mlcClear()">クリア</button>
</div>
</div>

<!-- 統計バー -->
<div class="mlc-stats-bar" id="mlc-stats-bar"></div>

<!-- フィルタタブ -->
<div class="mlc-filter-row" id="mlc-filter-row"></div>

<!-- テーブル -->
<div class="mlc-results-wrap" id="mlc-results-wrap">
<table class="mlc-table" id="mlc-table">
<thead>
<tr>
<th>#</th>
<th>リンクテキスト</th>
<th>URL</th>
<th>種類</th>
<th>フラグ</th>
</tr>
</thead>
<tbody id="mlc-tbody"></tbody>
</table>
</div>

<!-- アクションボタン -->
<div class="mlc-action-row" id="mlc-action-row">
<button class="mlc-btn mlc-btn-export" onclick="mlcExportCSV()">CSVでエクスポート</button>
<button class="mlc-btn mlc-btn-export" onclick="mlcExportJSON()">JSONでエクスポート</button>
<button class="mlc-btn" id="mlc-copy-urls-btn" onclick="mlcCopyAllURLs()">全URLをコピー</button>
</div>

<!-- トースト通知 -->
<div class="mlc-toast" id="mlc-toast"></div>

<!-- 関連ツール -->
<div class="mlc-crosslinks">
<p>関連ツール：</p>
<a href="/tools/markdown-preview/">マークダウンプレビュー</a>
<a href="/tools/markdown-table-generator/">マークダウン表ジェネレーター</a>
<a href="/tools/url-encoder/">URLエンコーダー</a>
</div>

<!-- freee CTA -->
<div class="mlc-freee-cta">
<h3>フリーランス・中小企業の方へ</h3>
<p>リンク管理や文書作成だけでなく、請求書・経費・確定申告もまとめて効率化しませんか？<br>クラウド会計ソフト <strong>freee</strong> なら、面倒な経理作業をシンプルに。</p>
<a class="mlc-freee-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">freeeを無料で試す</a>
</div>

<script>
(function () {
'use strict';

/* -----------------------------------------------
状態管理
----------------------------------------------- */
var _allLinks = [];
var _activeFilter = 'all';

/* -----------------------------------------------
メイン：抽出処理
----------------------------------------------- */
window.mlcAnalyze = function () {
var raw = document.getElementById('mlc-input').value;
if (!raw.trim()) { mlcShowToast('マークダウンを貼り付けてください。'); return; }
_allLinks = mlcExtractLinks(raw);
_activeFilter = 'all';
mlcRender();
};

/* -----------------------------------------------
リンク抽出
----------------------------------------------- */
function mlcExtractLinks(text) {
var links = [];
var seen = {};

// 1. インライン画像: ![alt](url)
var imgRe = /!\[([^\]]*)\]\(([^)]*)\)/g;
var m;
while ((m = imgRe.exec(text)) !== null) {
links.push(mlcBuild(m[1], m[2].trim(), 'image', seen));
}

// 2. インラインリンク: [text](url)
var linkRe = /(?<!!)\[([^\]]*)\]\(([^)]*)\)/g;
while ((m = linkRe.exec(text)) !== null) {
links.push(mlcBuild(m[1], m[2].trim(), null, seen));
}

// 3. 参照形式: [text][id]  +  [id]: url
var refs = {};
var refDefRe = /^\[([^\]]+)\]:\s*(\S+)/gm;
while ((m = refDefRe.exec(text)) !== null) {
refs[m[1].toLowerCase()] = m[2].trim();
}
var refUsageRe = /(?<!!)\[([^\]]+)\]\[([^\]]*)\]/g;
while ((m = refUsageRe.exec(text)) !== null) {
var key = (m[2] || m[1]).toLowerCase();
var url = refs[key] || '[未解決の参照: ' + key + ']';
links.push(mlcBuild(m[1], url, null, seen));
}

// 4. 自動リンク: <https://...>
var autoRe = /<(https?:\/\/[^>]+)>/g;
while ((m = autoRe.exec(text)) !== null) {
links.push(mlcBuild(m[1], m[1].trim(), null, seen));
}

return links;
}

function mlcBuild(text, url, forceType, seen) {
var type = forceType || mlcClassify(url);
var broken = mlcIsBroken(url);
var key = url.toLowerCase();
var dup = !!seen[key];
seen[key] = true;
return { text: text, url: url, type: type, broken: broken, dup: dup };
}

function mlcClassify(url) {
if (!url) return 'external';
if (url.startsWith('#')) return 'anchor';
if (url.startsWith('/') || url.startsWith('./') || url.startsWith('../')) return 'internal';
if (/^https?:\/\//i.test(url)) return 'external';
if (/^mailto:/i.test(url)) return 'external';
return 'external';
}

function mlcIsBroken(url) {
if (!url) return true;
if (/\s/.test(url)) return true;
if (/^www\./i.test(url)) return true;
if (/^[a-zA-Z0-9-]+\.[a-zA-Z]{2,}(\/|$)/.test(url) &&
!/^https?:\/\//i.test(url) &&
!url.startsWith('/') &&
!url.startsWith('#') &&
!url.startsWith('mailto:')) return true;
return false;
}

/* -----------------------------------------------
描画
----------------------------------------------- */
function mlcRender() {
mlcRenderStats();
mlcRenderFilters();
mlcRenderTable();
document.getElementById('mlc-action-row').style.display = _allLinks.length ? 'flex' : 'none';
}

function mlcRenderStats() {
var bar = document.getElementById('mlc-stats-bar');
if (!_allLinks.length) { bar.style.display = 'none'; return; }
var c = mlcCounts(_allLinks);
bar.innerHTML = [
chip('chip-total',  '合計: ' + c.total),
chip('chip-ext',    '外部: ' + c.external),
chip('chip-int',    '内部: ' + c.internal),
chip('chip-img',    '画像: ' + c.image),
chip('chip-anchor', 'アンカー: ' + c.anchor),
c.dup    ? chip('chip-dup',    '重複: ' + c.dup) : '',
c.broken ? chip('chip-broken', '不正形式: ' + c.broken) : '',
].join('');
bar.style.display = 'flex';
}

function chip(cls, label) {
return '<span class="mlc-stat-chip ' + cls + '">' + mlcEsc(label) + '</span>';
}

function mlcCounts(links) {
var c = { total: links.length, external: 0, internal: 0, image: 0, anchor: 0, dup: 0, broken: 0 };
links.forEach(function (l) {
if (l.type === 'external') c.external++;
if (l.type === 'internal') c.internal++;
if (l.type === 'image')    c.image++;
if (l.type === 'anchor')   c.anchor++;
if (l.dup)    c.dup++;
if (l.broken) c.broken++;
});
return c;
}

function mlcRenderFilters() {
var row = document.getElementById('mlc-filter-row');
if (!_allLinks.length) { row.style.display = 'none'; return; }
var c = mlcCounts(_allLinks);
var filters = [
{ key: 'all',      label: 'すべて (' + c.total + ')' },
{ key: 'external', label: '外部 (' + c.external + ')' },
{ key: 'internal', label: '内部 (' + c.internal + ')' },
{ key: 'image',    label: '画像 (' + c.image + ')' },
{ key: 'anchor',   label: 'アンカー (' + c.anchor + ')' },
{ key: 'dup',      label: '重複 (' + c.dup + ')' },
{ key: 'broken',   label: '不正形式 (' + c.broken + ')' },
];
row.innerHTML = filters.map(function (f) {
var active = f.key === _activeFilter ? ' active' : '';
return '<button class="mlc-filter-tab' + active + '" onclick="mlcSetFilter(\'' + f.key + '\')">' + mlcEsc(f.label) + '</button>';
}).join('');
row.style.display = 'flex';
}

window.mlcSetFilter = function (key) {
_activeFilter = key;
mlcRenderFilters();
mlcRenderTable();
};

function mlcRenderTable() {
var wrap = document.getElementById('mlc-results-wrap');
var tbody = document.getElementById('mlc-tbody');
if (!_allLinks.length) { wrap.style.display = 'none'; return; }
wrap.style.display = 'block';

var visible = _allLinks.filter(function (l) {
if (_activeFilter === 'all')    return true;
if (_activeFilter === 'dup')    return l.dup;
if (_activeFilter === 'broken') return l.broken;
return l.type === _activeFilter;
});

if (!visible.length) {
tbody.innerHTML = '<tr><td colspan="5" class="mlc-empty">該当するリンクがありません。</td></tr>';
return;
}

var typeLabel = { external: '外部', internal: '内部', image: '画像', anchor: 'アンカー' };

tbody.innerHTML = visible.map(function (l, i) {
var tl = typeLabel[l.type] || l.type;
var typeBadge = '<span class="mlc-badge badge-' + l.type + '">' + mlcEsc(tl) + '</span>';
var flags = '';
if (l.dup)    flags += '<span class="mlc-badge badge-dup">重複</span>';
if (l.broken) flags += '<span class="mlc-badge badge-broken">不正形式</span>';
var urlDisplay = mlcIsSafeURL(l.url)
? '<a href="' + mlcEscAttr(l.url) + '" target="_blank" rel="noopener noreferrer">' + mlcEsc(l.url) + '</a>'
: mlcEsc(l.url);
return '<tr>' +
'<td>' + (i + 1) + '</td>' +
'<td>' + mlcEsc(l.text || '（テキストなし）') + '</td>' +
'<td class="mlc-url-cell">' + urlDisplay + '</td>' +
'<td>' + typeBadge + '</td>' +
'<td>' + (flags || '—') + '</td>' +
'</tr>';
}).join('');
}

function mlcIsSafeURL(url) {
return /^https?:\/\//i.test(url) || url.startsWith('/') || url.startsWith('#') || url.startsWith('mailto:');
}

/* -----------------------------------------------
エクスポート
----------------------------------------------- */
window.mlcExportCSV = function () {
if (!_allLinks.length) { mlcShowToast('エクスポートするリンクがありません。'); return; }
var rows = [['#', 'リンクテキスト', 'URL', '種類', '重複', '不正形式']];
_allLinks.forEach(function (l, i) {
rows.push([i + 1, l.text, l.url, l.type, l.dup ? 'はい' : 'いいえ', l.broken ? 'はい' : 'いいえ']);
});
var csv = rows.map(function (r) {
return r.map(function (c) { return '"' + String(c).replace(/"/g, '""') + '"'; }).join(',');
}).join('\r\n');
mlcDownload('markdown-links.csv', csv, 'text/csv;charset=utf-8;');
mlcShowToast('CSVをダウンロードしました。');
};

window.mlcExportJSON = function () {
if (!_allLinks.length) { mlcShowToast('エクスポートするリンクがありません。'); return; }
var data = _allLinks.map(function (l, i) {
return { index: i + 1, text: l.text, url: l.url, type: l.type, duplicate: l.dup, brokenFormat: l.broken };
});
mlcDownload('markdown-links.json', JSON.stringify(data, null, 2), 'application/json');
mlcShowToast('JSONをダウンロードしました。');
};

window.mlcCopyAllURLs = function () {
if (!_allLinks.length) { mlcShowToast('コピーするURLがありません。'); return; }
var urls = _allLinks.map(function (l) { return l.url; }).join('\n');
navigator.clipboard.writeText(urls).then(function () {
mlcShowToast('全URLをクリップボードにコピーしました！');
}, function () {
mlcShowToast('コピーに失敗しました。手動で選択してください。');
});
};

function mlcDownload(filename, content, mime) {
var blob = new Blob([content], { type: mime });
var url = URL.createObjectURL(blob);
var a = document.createElement('a');
a.href = url;
a.download = filename;
document.body.appendChild(a);
a.click();
setTimeout(function () { document.body.removeChild(a); URL.revokeObjectURL(url); }, 200);
}

/* -----------------------------------------------
クリア
----------------------------------------------- */
window.mlcClear = function () {
document.getElementById('mlc-input').value = '';
_allLinks = [];
_activeFilter = 'all';
document.getElementById('mlc-stats-bar').style.display = 'none';
document.getElementById('mlc-filter-row').style.display = 'none';
document.getElementById('mlc-results-wrap').style.display = 'none';
document.getElementById('mlc-action-row').style.display = 'none';
};

/* -----------------------------------------------
トースト通知
----------------------------------------------- */
window.mlcShowToast = function (msg) {
var t = document.getElementById('mlc-toast');
t.textContent = msg;
t.style.display = 'block';
clearTimeout(t._timer);
t._timer = setTimeout(function () { t.style.display = 'none'; }, 2400);
};

/* -----------------------------------------------
ユーティリティ
----------------------------------------------- */
function mlcEsc(s) {
return String(s)
.replace(/&/g, '&amp;')
.replace(/</g, '&lt;')
.replace(/>/g, '&gt;')
.replace(/"/g, '&quot;');
}
function mlcEscAttr(s) {
return String(s).replace(/"/g, '&quot;').replace(/'/g, '&#39;');
}

/* -----------------------------------------------
キーボードショートカット: Ctrl/Cmd + Enter
----------------------------------------------- */
document.getElementById('mlc-input').addEventListener('keydown', function (e) {
if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') {
mlcAnalyze();
}
});

})();
</script>

</div>

---

## 使い方

1. マークダウンテキストを上のボックスに貼り付けます。
2. **リンクを抽出** をクリック（または Ctrl+Enter / Cmd+Enter）。
3. フィルタタブで種類別に絞り込みます。
4. **CSVでエクスポート** / **JSONでエクスポート** でダウンロード、または **全URLをコピー** でクリップボードに一括コピー。

## 抽出されるリンクの種類

| 種類 | マークダウン記法 | 例 |
|---|---|---|
| 外部リンク | `[テキスト](https://...)` | `[Google](https://google.com)` |
| 内部リンク | `[テキスト](/パス)` | `[概要ページ](/about)` |
| アンカー | `[テキスト](#id)` | `[トップへ](#top)` |
| 画像 | `![alt](url)` | `![ロゴ](logo.png)` |
| 参照リンク | `[テキスト][ref]` | `[ドキュメント][docs]` |
| 自動リンク | `<https://...>` | `<https://example.com>` |

## 不正形式の検出

以下のパターンをフラグとして検出します：

- **プロトコル欠落** — `www.` で始まり `https://` がないURL
- **URLにスペース** — レンダリングに失敗する空白を含むURL
- **ベアドメイン** — `https://` なしのドメイン形式の文字列

## 関連ツール

- [マークダウンプレビュー](/tools/markdown-preview/) — マークダウンをリアルタイムでHTMLに変換
- [マークダウン表ジェネレーター](/tools/markdown-table-generator/) — マークダウンの表をビジュアルで作成
- [URLエンコーダー](/tools/url-encoder/) — URLおよびクエリ文字列のエンコード・デコード
