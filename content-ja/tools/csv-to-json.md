---
title: "CSV↔JSON変換ツール"
slug: "csv-to-json"
date: 2025-04-26
description: "無料のCSV↔JSON変換ツール。CSVデータをJSON配列・オブジェクトに変換。区切り文字自動検出・型推論対応。ブラウザで完結。"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/csv-to-json-ja.png
  alt: "CSV↔JSON変換ツール — ブラウザで完結する無料ツール"
---

CSVデータをJSON形式に（またはその逆に）即座に変換できます。テキストを貼り付けるかファイルをアップロードして、フォーマットを選択してダウンロードするだけ。データはサーバーに送信されず、すべてブラウザ内で処理されます。

**関連ツール:** [JSON→CSV変換](/ja/tools/json-to-csv/) &nbsp;·&nbsp; [JSONフォーマッター](/ja/tools/json-formatter/)

---

<div id="cj-app">

<style>
/* ── Reset / base ── */
#cj-app *, #cj-app *::before, #cj-app *::after { box-sizing: border-box; margin: 0; padding: 0; }
#cj-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic UI", Meiryo, sans-serif;
font-size: 14px;
color: #1e293b;
line-height: 1.7;
}

/* ── Layout ── */
#cj-app .cj-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
margin-bottom: 16px;
}

/* ── Section headers ── */
#cj-app .cj-section-title {
font-size: 13px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: .04em;
margin-bottom: 10px;
}

/* ── Mode tabs ── */
#cj-app .cj-tabs {
display: flex;
gap: 4px;
margin-bottom: 16px;
background: #f1f5f9;
border-radius: 8px;
padding: 4px;
}
#cj-app .cj-tab {
flex: 1;
padding: 8px 12px;
border: none;
border-radius: 6px;
background: transparent;
font-size: 13px;
font-weight: 700;
color: #64748b;
cursor: pointer;
transition: all .15s;
}
#cj-app .cj-tab.active {
background: #fff;
color: #0f172a;
box-shadow: 0 1px 3px rgba(0,0,0,.12);
}

/* ── Controls row ── */
#cj-app .cj-controls {
display: flex;
flex-wrap: wrap;
gap: 10px;
align-items: flex-end;
margin-bottom: 14px;
}
#cj-app .cj-control-group {
display: flex;
flex-direction: column;
gap: 4px;
}
#cj-app .cj-label {
font-size: 12px;
font-weight: 600;
color: #475569;
}
#cj-app select, #cj-app input[type="text"] {
border: 1px solid #cbd5e1;
border-radius: 6px;
padding: 6px 10px;
font-size: 13px;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color .15s;
}
#cj-app select:focus, #cj-app input[type="text"]:focus {
border-color: #3b82f6;
}
#cj-app .cj-toggle-label {
display: flex;
align-items: center;
gap: 6px;
font-size: 13px;
color: #1e293b;
cursor: pointer;
user-select: none;
}
#cj-app .cj-toggle-label input[type="checkbox"] {
width: 15px;
height: 15px;
accent-color: #3b82f6;
cursor: pointer;
}

/* ── Textarea / file drop ── */
#cj-app .cj-drop-zone {
position: relative;
border: 2px dashed #cbd5e1;
border-radius: 8px;
transition: border-color .15s, background .15s;
}
#cj-app .cj-drop-zone.drag-over {
border-color: #3b82f6;
background: #eff6ff;
}
#cj-app .cj-textarea {
width: 100%;
min-height: 160px;
border: none;
border-radius: 8px;
padding: 12px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12.5px;
color: #0f172a;
background: transparent;
resize: vertical;
outline: none;
display: block;
}
#cj-app .cj-drop-hint {
position: absolute;
bottom: 8px;
right: 12px;
font-size: 11px;
color: #94a3b8;
pointer-events: none;
}

/* ── File upload button ── */
#cj-app .cj-file-row {
display: flex;
align-items: center;
gap: 10px;
margin-top: 8px;
}
#cj-app .cj-btn-file {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 6px 14px;
border: 1px solid #94a3b8;
border-radius: 6px;
background: #f8fafc;
font-size: 12px;
font-weight: 600;
color: #475569;
cursor: pointer;
transition: background .15s;
}
#cj-app .cj-btn-file:hover { background: #f1f5f9; }
#cj-app #cj-file-input { display: none; }
#cj-app .cj-file-name {
font-size: 12px;
color: #64748b;
font-style: italic;
}

/* ── Action buttons ── */
#cj-app .cj-actions {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 12px;
}
#cj-app .cj-btn {
padding: 8px 18px;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: opacity .15s, transform .1s;
}
#cj-app .cj-btn:hover { opacity: .88; }
#cj-app .cj-btn:active { transform: scale(.97); }
#cj-app .cj-btn-primary {
background: #3b82f6;
color: #fff;
}
#cj-app .cj-btn-secondary {
background: #f1f5f9;
color: #334155;
border: 1px solid #cbd5e1;
}
#cj-app .cj-btn-success {
background: #10b981;
color: #fff;
}
#cj-app .cj-btn-sm {
padding: 5px 12px;
font-size: 12px;
}

/* ── Stats bar ── */
#cj-app .cj-stats {
display: flex;
gap: 16px;
font-size: 12px;
color: #64748b;
margin-top: 8px;
flex-wrap: wrap;
}
#cj-app .cj-stat-item strong { color: #0f172a; }

/* ── Output area ── */
#cj-app .cj-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 8px;
flex-wrap: wrap;
gap: 8px;
}
#cj-app .cj-output-textarea {
width: 100%;
min-height: 220px;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 12px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
color: #0f172a;
background: #f8fafc;
resize: vertical;
outline: none;
}

/* ── Preview table ── */
#cj-app .cj-table-wrap {
overflow-x: auto;
border: 1px solid #e2e8f0;
border-radius: 8px;
max-height: 280px;
overflow-y: auto;
}
#cj-app .cj-table {
border-collapse: collapse;
width: 100%;
font-size: 12px;
}
#cj-app .cj-table th {
background: #f1f5f9;
color: #475569;
font-weight: 700;
padding: 7px 12px;
text-align: left;
border-bottom: 1px solid #e2e8f0;
white-space: nowrap;
position: sticky;
top: 0;
}
#cj-app .cj-table td {
padding: 5px 12px;
border-bottom: 1px solid #f1f5f9;
white-space: nowrap;
max-width: 200px;
overflow: hidden;
text-overflow: ellipsis;
}
#cj-app .cj-table tr:hover td { background: #f8fafc; }
#cj-app .cj-table .cj-type-num { color: #0891b2; }
#cj-app .cj-table .cj-type-bool { color: #7c3aed; }
#cj-app .cj-table .cj-type-null { color: #94a3b8; font-style: italic; }

/* ── Message / error ── */
#cj-app .cj-msg {
padding: 10px 14px;
border-radius: 7px;
font-size: 13px;
font-weight: 500;
margin-top: 10px;
display: none;
}
#cj-app .cj-msg.show { display: block; }
#cj-app .cj-msg.error { background: #fef2f2; color: #b91c1c; border: 1px solid #fecaca; }
#cj-app .cj-msg.success { background: #f0fdf4; color: #166534; border: 1px solid #bbf7d0; }

/* ── Copy feedback ── */
#cj-app .cj-copy-feedback {
font-size: 12px;
color: #10b981;
font-weight: 600;
opacity: 0;
transition: opacity .3s;
}
#cj-app .cj-copy-feedback.show { opacity: 1; }

/* ── Responsive ── */
@media (max-width: 560px) {
#cj-app .cj-controls { flex-direction: column; align-items: stretch; }
#cj-app .cj-output-header { flex-direction: column; align-items: flex-start; }
}
</style>

<!-- ═══════════════════════════════════════════
MODE TABS
═══════════════════════════════════════════ -->
<div class="cj-tabs">
<button class="cj-tab active" id="cj-tab-csv2json" onclick="cjSetMode('csv2json')">CSV → JSON</button>
<button class="cj-tab" id="cj-tab-json2csv" onclick="cjSetMode('json2csv')">JSON → CSV</button>
</div>

<!-- ═══════════════════════════════════════════
CSV → JSON パネル
═══════════════════════════════════════════ -->
<div id="cj-panel-csv2json">

<!-- オプション -->
<div class="cj-card">
<div class="cj-section-title">オプション</div>
<div class="cj-controls">
<!-- 区切り文字 -->
<div class="cj-control-group">
<span class="cj-label">区切り文字</span>
<select id="cj-delimiter" onchange="cjOnDelimiterChange()">
<option value="auto">自動検出</option>
<option value=",">カンマ (,)</option>
<option value="	">タブ (\t)</option>
<option value=";">セミコロン (;)</option>
<option value="|">パイプ (|)</option>
<option value="custom">カスタム…</option>
</select>
</div>
<div class="cj-control-group" id="cj-custom-delim-group" style="display:none;">
<span class="cj-label">カスタム文字</span>
<input type="text" id="cj-custom-delim" maxlength="3" placeholder="例: ~" style="width:80px;" />
</div>
<!-- 出力フォーマット -->
<div class="cj-control-group">
<span class="cj-label">出力フォーマット</span>
<select id="cj-format">
<option value="objects">オブジェクト配列</option>
<option value="arrays">配列の配列</option>
<option value="nested">ネスト（第1列でグループ化）</option>
</select>
</div>
<!-- トグル -->
<div class="cj-control-group" style="justify-content:flex-end;gap:8px;">
<label class="cj-toggle-label">
<input type="checkbox" id="cj-headers" checked />
1行目をヘッダーとして使用
</label>
<label class="cj-toggle-label">
<input type="checkbox" id="cj-typeinfer" checked />
型推論を有効化
</label>
<label class="cj-toggle-label">
<input type="checkbox" id="cj-pretty" checked />
整形出力（Pretty print）
</label>
</div>
</div>
</div>

<!-- 入力 -->
<div class="cj-card">
<div class="cj-section-title">CSV 入力</div>
<div class="cj-drop-zone" id="cj-drop-zone">
<textarea class="cj-textarea" id="cj-csv-input"
placeholder="CSVをここに貼り付けるか、.csvファイルをドラッグ＆ドロップ…&#10;&#10;例:&#10;名前,年齢,在籍&#10;田中太郎,30,true&#10;鈴木花子,25,false"></textarea>
<span class="cj-drop-hint">.csv をドロップ</span>
</div>
<div class="cj-file-row">
<label class="cj-btn-file" for="cj-file-input">
<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
.csvをアップロード
</label>
<input type="file" id="cj-file-input" accept=".csv,text/csv,text/plain" />
<span class="cj-file-name" id="cj-file-name">ファイル未選択</span>
</div>
<div class="cj-actions">
<button class="cj-btn cj-btn-primary" onclick="cjConvert()">JSONに変換</button>
<button class="cj-btn cj-btn-secondary" onclick="cjClearInput()">クリア</button>
<button class="cj-btn cj-btn-secondary" onclick="cjLoadSample()">サンプルを読み込む</button>
</div>
<div class="cj-msg" id="cj-input-msg"></div>
<div class="cj-stats" id="cj-input-stats" style="display:none;">
<span class="cj-stat-item">行数: <strong id="cj-row-count">0</strong></span>
<span class="cj-stat-item">列数: <strong id="cj-col-count">0</strong></span>
<span class="cj-stat-item">検出された区切り文字: <strong id="cj-detected-delim">—</strong></span>
</div>
</div>

<!-- プレビュー -->
<div class="cj-card" id="cj-preview-card" style="display:none;">
<div class="cj-section-title">プレビュー テーブル</div>
<div class="cj-table-wrap" id="cj-table-wrap"></div>
</div>

<!-- 出力 -->
<div class="cj-card" id="cj-output-card" style="display:none;">
<div class="cj-output-header">
<div class="cj-section-title" style="margin-bottom:0;">JSON 出力</div>
<div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
<span class="cj-copy-feedback" id="cj-copy-feedback">コピーしました！</span>
<button class="cj-btn cj-btn-secondary cj-btn-sm" onclick="cjCopy()">JSONをコピー</button>
<button class="cj-btn cj-btn-success cj-btn-sm" onclick="cjDownloadJSON()">.jsonをダウンロード</button>
</div>
</div>
<textarea class="cj-output-textarea" id="cj-json-output" readonly></textarea>
<div class="cj-stats" id="cj-output-stats">
<span class="cj-stat-item">レコード数: <strong id="cj-record-count">0</strong></span>
<span class="cj-stat-item">サイズ: <strong id="cj-output-size">0 B</strong></span>
</div>
</div>

</div><!-- /panel csv2json -->

<!-- ═══════════════════════════════════════════
JSON → CSV パネル
═══════════════════════════════════════════ -->
<div id="cj-panel-json2csv" style="display:none;">

<div class="cj-card">
<div class="cj-section-title">オプション</div>
<div class="cj-controls">
<div class="cj-control-group">
<span class="cj-label">出力区切り文字</span>
<select id="cj-j2c-delimiter">
<option value=",">カンマ (,)</option>
<option value="	">タブ (\t)</option>
<option value=";">セミコロン (;)</option>
<option value="|">パイプ (|)</option>
</select>
</div>
<div class="cj-control-group" style="justify-content:flex-end;gap:8px;">
<label class="cj-toggle-label">
<input type="checkbox" id="cj-j2c-headers" checked />
ヘッダー行を含める
</label>
<label class="cj-toggle-label">
<input type="checkbox" id="cj-j2c-quote" checked />
文字列をすべてクォート
</label>
</div>
</div>
</div>

<div class="cj-card">
<div class="cj-section-title">JSON 入力</div>
<div class="cj-drop-zone">
<textarea class="cj-textarea" id="cj-json-input"
placeholder='JSONの配列を貼り付けてください…&#10;&#10;例:&#10;[{"名前":"田中太郎","年齢":30},{"名前":"鈴木花子","年齢":25}]'></textarea>
</div>
<div class="cj-actions">
<button class="cj-btn cj-btn-primary" onclick="cjConvertJ2C()">CSVに変換</button>
<button class="cj-btn cj-btn-secondary" onclick="document.getElementById('cj-json-input').value=''">クリア</button>
<button class="cj-btn cj-btn-secondary" onclick="cjLoadJ2CSample()">サンプルを読み込む</button>
</div>
<div class="cj-msg" id="cj-j2c-input-msg"></div>
</div>

<div class="cj-card" id="cj-j2c-output-card" style="display:none;">
<div class="cj-output-header">
<div class="cj-section-title" style="margin-bottom:0;">CSV 出力</div>
<div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
<span class="cj-copy-feedback" id="cj-j2c-copy-feedback">コピーしました！</span>
<button class="cj-btn cj-btn-secondary cj-btn-sm" onclick="cjCopyCSV()">CSVをコピー</button>
<button class="cj-btn cj-btn-success cj-btn-sm" onclick="cjDownloadCSV()">.csvをダウンロード</button>
</div>
</div>
<textarea class="cj-output-textarea" id="cj-csv-output" readonly></textarea>
<div class="cj-stats" id="cj-j2c-output-stats">
<span class="cj-stat-item">行数: <strong id="cj-j2c-row-count">0</strong></span>
<span class="cj-stat-item">列数: <strong id="cj-j2c-col-count">0</strong></span>
<span class="cj-stat-item">サイズ: <strong id="cj-j2c-size">0 B</strong></span>
</div>
</div>

</div><!-- /panel json2csv -->

</div><!-- /#cj-app -->

<script>
(function () {
'use strict';

/* ── ユーティリティ ── */
function showMsg(id, text, type) {
var el = document.getElementById(id);
el.textContent = text;
el.className = 'cj-msg show ' + type;
}
function hideMsg(id) {
var el = document.getElementById(id);
el.className = 'cj-msg';
}
function show(id) { var el = document.getElementById(id); if (el) el.style.display = ''; }
function hide(id) { var el = document.getElementById(id); if (el) el.style.display = 'none'; }
function formatBytes(n) {
if (n < 1024) return n + ' B';
if (n < 1048576) return (n / 1024).toFixed(1) + ' KB';
return (n / 1048576).toFixed(2) + ' MB';
}

/* ── モード切り替え ── */
window.cjSetMode = function (mode) {
['csv2json', 'json2csv'].forEach(function (m) {
document.getElementById('cj-tab-' + m).classList.toggle('active', m === mode);
document.getElementById('cj-panel-' + m).style.display = m === mode ? '' : 'none';
});
};

/* ── 区切り文字自動検出 ── */
function detectDelimiter(text) {
var candidates = [',', '\t', ';', '|'];
var firstLine = text.split('\n')[0] || '';
var best = ','; var bestCount = 0;
candidates.forEach(function (d) {
var count = firstLine.split(d).length - 1;
if (count > bestCount) { bestCount = count; best = d; }
});
return best;
}

function getDelimiter() {
var sel = document.getElementById('cj-delimiter').value;
if (sel === 'auto') return null;
if (sel === 'custom') return document.getElementById('cj-custom-delim').value || ',';
return sel;
}

window.cjOnDelimiterChange = function () {
var sel = document.getElementById('cj-delimiter').value;
document.getElementById('cj-custom-delim-group').style.display = sel === 'custom' ? '' : 'none';
};

/* ── CSVパーサー（RFC 4180準拠） ── */
function parseCSV(text, delimiter) {
var rows = [];
var len = text.length;
var row = [];
var field = '';
var inQuote = false;
var i = 0;
var d = delimiter;
var dLen = d.length;

while (i < len) {
var ch = text[i];

if (inQuote) {
if (ch === '"') {
if (text[i + 1] === '"') { field += '"'; i += 2; continue; }
inQuote = false; i++; continue;
}
field += ch; i++; continue;
}

if (ch === '"') { inQuote = true; i++; continue; }

if (text.substr(i, dLen) === d) {
row.push(field); field = ''; i += dLen; continue;
}

if (ch === '\r') {
if (text[i + 1] === '\n') i++;
row.push(field); rows.push(row); row = []; field = ''; i++; continue;
}
if (ch === '\n') {
row.push(field); rows.push(row); row = []; field = ''; i++; continue;
}

field += ch; i++;
}
if (field !== '' || row.length > 0) { row.push(field); rows.push(row); }
if (rows.length && rows[rows.length - 1].every(function (c) { return c === ''; })) rows.pop();
return rows;
}

/* ── 型推論 ── */
function inferValue(s) {
if (s === '' || s.toLowerCase() === 'null' || s.toLowerCase() === 'n/a') return null;
if (s.toLowerCase() === 'true') return true;
if (s.toLowerCase() === 'false') return false;
if (s !== '' && !isNaN(Number(s)) && s.trim() !== '') return Number(s);
return s;
}

/* ── メイン変換 CSV → JSON ── */
window.cjConvert = function () {
hideMsg('cj-input-msg');
var raw = document.getElementById('cj-csv-input').value.trim();
if (!raw) { showMsg('cj-input-msg', 'CSVデータを貼り付けるか、ファイルをアップロードしてください。', 'error'); return; }

var delimSel = getDelimiter();
var delim = delimSel === null ? detectDelimiter(raw) : delimSel;
var displayDelim = delim === '\t' ? '\\t' : delim;

var rows = parseCSV(raw, delim);
if (!rows.length) { showMsg('cj-input-msg', '行を解析できませんでした。', 'error'); return; }

var useHeaders = document.getElementById('cj-headers').checked;
var useTypeInfer = document.getElementById('cj-typeinfer').checked;
var pretty = document.getElementById('cj-pretty').checked;
var format = document.getElementById('cj-format').value;

var headers = useHeaders ? rows[0] : rows[0].map(function (_, i) { return 'col' + (i + 1); });
var dataRows = useHeaders ? rows.slice(1) : rows;

document.getElementById('cj-row-count').textContent = dataRows.length;
document.getElementById('cj-col-count').textContent = headers.length;
document.getElementById('cj-detected-delim').textContent = delimSel === null ? '"' + displayDelim + '" (自動)' : '"' + displayDelim + '"';
document.getElementById('cj-input-stats').style.display = '';

var result;
if (format === 'arrays') {
result = useHeaders ? [headers].concat(dataRows.map(function (r) {
return r.map(function (c) { return useTypeInfer ? inferValue(c) : c; });
})) : dataRows.map(function (r) {
return r.map(function (c) { return useTypeInfer ? inferValue(c) : c; });
});
} else if (format === 'nested') {
result = {};
dataRows.forEach(function (r) {
var key = r[0] || '';
var obj = {};
headers.slice(1).forEach(function (h, hi) {
obj[h] = useTypeInfer ? inferValue(r[hi + 1] || '') : (r[hi + 1] || '');
});
result[key] = obj;
});
} else {
result = dataRows.map(function (r) {
var obj = {};
headers.forEach(function (h, hi) {
obj[h] = useTypeInfer ? inferValue(r[hi] || '') : (r[hi] || '');
});
return obj;
});
}

var jsonStr = pretty ? JSON.stringify(result, null, 2) : JSON.stringify(result);
document.getElementById('cj-json-output').value = jsonStr;
document.getElementById('cj-record-count').textContent = Array.isArray(result) ? result.length : Object.keys(result).length;
document.getElementById('cj-output-size').textContent = formatBytes(new Blob([jsonStr]).size);

show('cj-output-card');
buildPreviewTable(headers, dataRows, useTypeInfer);
};

/* ── プレビューテーブル ── */
function buildPreviewTable(headers, dataRows, useTypeInfer) {
var maxRows = Math.min(dataRows.length, 50);
var html = '<table class="cj-table"><thead><tr>';
headers.forEach(function (h) { html += '<th>' + escHtml(h) + '</th>'; });
html += '</tr></thead><tbody>';
for (var i = 0; i < maxRows; i++) {
html += '<tr>';
headers.forEach(function (_, hi) {
var raw = dataRows[i][hi] !== undefined ? dataRows[i][hi] : '';
var val = useTypeInfer ? inferValue(raw) : raw;
var cls = '';
if (typeof val === 'number') cls = 'cj-type-num';
else if (typeof val === 'boolean') cls = 'cj-type-bool';
else if (val === null) cls = 'cj-type-null';
var display = val === null ? 'null' : String(val);
html += '<td class="' + cls + '">' + escHtml(display) + '</td>';
});
html += '</tr>';
}
html += '</tbody></table>';
if (dataRows.length > 50) html += '<p style="font-size:11px;color:#94a3b8;padding:6px 12px;">' + dataRows.length + '行中50行を表示</p>';
document.getElementById('cj-table-wrap').innerHTML = html;
show('cj-preview-card');
}

function escHtml(s) {
return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

/* ── JSON → CSV ── */
function csvEscapeField(val, delim, quoteAll) {
var s = val === null || val === undefined ? '' : String(val);
var needsQuote = quoteAll || s.includes('"') || s.includes(delim) || s.includes('\n') || s.includes('\r');
if (needsQuote) s = '"' + s.replace(/"/g, '""') + '"';
return s;
}

window.cjConvertJ2C = function () {
hideMsg('cj-j2c-input-msg');
var raw = document.getElementById('cj-json-input').value.trim();
if (!raw) { showMsg('cj-j2c-input-msg', 'JSON配列を貼り付けてください。', 'error'); return; }

var data;
try { data = JSON.parse(raw); } catch (e) { showMsg('cj-j2c-input-msg', '無効なJSON: ' + e.message, 'error'); return; }

if (!Array.isArray(data)) { showMsg('cj-j2c-input-msg', '入力はJSON配列（例: [{…},{…}]）である必要があります。', 'error'); return; }
if (!data.length) { showMsg('cj-j2c-input-msg', '配列が空です。', 'error'); return; }

var delim = document.getElementById('cj-j2c-delimiter').value;
var includeHeaders = document.getElementById('cj-j2c-headers').checked;
var quoteAll = document.getElementById('cj-j2c-quote').checked;

var keysSet = {};
var keys = [];
data.forEach(function (item) {
if (typeof item === 'object' && item !== null) {
Object.keys(item).forEach(function (k) {
if (!keysSet[k]) { keysSet[k] = true; keys.push(k); }
});
}
});
if (!keys.length) { showMsg('cj-j2c-input-msg', '配列のアイテムからキーを抽出できませんでした。', 'error'); return; }

var lines = [];
if (includeHeaders) lines.push(keys.map(function (k) { return csvEscapeField(k, delim, quoteAll); }).join(delim));
data.forEach(function (item) {
var row = keys.map(function (k) { return csvEscapeField(item[k], delim, quoteAll); });
lines.push(row.join(delim));
});

var csvStr = lines.join('\r\n');
document.getElementById('cj-csv-output').value = csvStr;
document.getElementById('cj-j2c-row-count').textContent = data.length;
document.getElementById('cj-j2c-col-count').textContent = keys.length;
document.getElementById('cj-j2c-size').textContent = formatBytes(new Blob([csvStr]).size);
show('cj-j2c-output-card');
};

/* ── クリップボード / ダウンロード ── */
window.cjCopy = function () {
var txt = document.getElementById('cj-json-output').value;
navigator.clipboard && navigator.clipboard.writeText(txt).then(function () { flashCopy('cj-copy-feedback'); });
};
window.cjCopyCSV = function () {
var txt = document.getElementById('cj-csv-output').value;
navigator.clipboard && navigator.clipboard.writeText(txt).then(function () { flashCopy('cj-j2c-copy-feedback'); });
};
function flashCopy(id) {
var el = document.getElementById(id);
el.classList.add('show');
setTimeout(function () { el.classList.remove('show'); }, 1800);
}
window.cjDownloadJSON = function () {
var txt = document.getElementById('cj-json-output').value;
downloadFile(txt, 'output.json', 'application/json');
};
window.cjDownloadCSV = function () {
var txt = document.getElementById('cj-csv-output').value;
downloadFile(txt, 'output.csv', 'text/csv');
};
function downloadFile(content, filename, mime) {
var a = document.createElement('a');
a.href = URL.createObjectURL(new Blob([content], { type: mime }));
a.download = filename;
a.click();
setTimeout(function () { URL.revokeObjectURL(a.href); }, 1000);
}

/* ── クリア ── */
window.cjClearInput = function () {
document.getElementById('cj-csv-input').value = '';
document.getElementById('cj-file-name').textContent = 'ファイル未選択';
hide('cj-output-card'); hide('cj-preview-card');
document.getElementById('cj-input-stats').style.display = 'none';
hideMsg('cj-input-msg');
};

/* ── サンプルデータ ── */
window.cjLoadSample = function () {
document.getElementById('cj-csv-input').value =
'id,名前,部署,給与,正社員\n' +
'1,田中太郎,エンジニアリング,550000,true\n' +
'2,鈴木花子,マーケティング,420000,false\n' +
'3,佐藤次郎,エンジニアリング,620000,true\n' +
'4,山田由美,人事,,true\n' +
'5,"田中, 健一",営業,480000,true';
cjConvert();
};
window.cjLoadJ2CSample = function () {
document.getElementById('cj-json-input').value = JSON.stringify([
{ id: 1, 名前: '田中太郎', 部署: 'エンジニアリング', 給与: 550000, 正社員: true },
{ id: 2, 名前: '鈴木花子', 部署: 'マーケティング', 給与: 420000, 正社員: false },
{ id: 3, 名前: '佐藤次郎', 部署: 'エンジニアリング', 給与: 620000, 正社員: true }
], null, 2);
cjConvertJ2C();
};

/* ── ファイルアップロード ── */
document.getElementById('cj-file-input').addEventListener('change', function (e) {
var file = e.target.files[0];
if (!file) return;
document.getElementById('cj-file-name').textContent = file.name;
var reader = new FileReader();
reader.onload = function (ev) {
document.getElementById('cj-csv-input').value = ev.target.result;
cjConvert();
};
reader.readAsText(file, 'UTF-8');
});

/* ── ドラッグ＆ドロップ ── */
var dz = document.getElementById('cj-drop-zone');
dz.addEventListener('dragover', function (e) { e.preventDefault(); dz.classList.add('drag-over'); });
dz.addEventListener('dragleave', function () { dz.classList.remove('drag-over'); });
dz.addEventListener('drop', function (e) {
e.preventDefault();
dz.classList.remove('drag-over');
var file = e.dataTransfer.files[0];
if (!file) return;
document.getElementById('cj-file-name').textContent = file.name;
var reader = new FileReader();
reader.onload = function (ev) {
document.getElementById('cj-csv-input').value = ev.target.result;
cjConvert();
};
reader.readAsText(file, 'UTF-8');
});

})();
</script>

---

### 使い方

**CSV → JSON 変換**

1. CSVテキストを貼り付けるか、`.csv`ファイルをアップロードします（ドラッグ＆ドロップ対応）。
2. 区切り文字を選択。**自動検出**のままにすると、1行目の出現数を確認して最適な区切り文字を判断します。
3. **1行目をヘッダーとして使用**で、最初の行をキー名にするか通常データとして扱うかを切り替えます。
4. 出力フォーマットを選択：
- **オブジェクト配列** — 最も一般的。各行が `{ "キー": "値", … }` になります。
- **配列の配列** — コンパクト形式。行がそのまま配列で保持されます。
- **ネスト** — 第1列の値をキーとしてオブジェクトにグループ化します。
5. **型推論**が数値・`true`/`false`・空欄/`null`/`n/a`セルを適切なJSON型に自動変換します。
6. 「JSONに変換」を押し、プレビューテーブルで確認後、コピーまたはダウンロード。

**JSON → CSV 変換**

**JSON → CSV**タブに切り替えて、フラットなJSON配列を貼り付け、出力区切り文字を選んでダウンロードします。

カンマを含むクォートフィールド（例: `"田中, 健一"`）もRFC 4180に従って正しく処理されます。

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">データ管理の経費もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、SaaSツール費用の経費精算もクラウドで一元管理。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

---

**関連ツール:** [JSON→CSV変換](/ja/tools/json-to-csv/) &nbsp;·&nbsp; [JSONフォーマッター](/ja/tools/json-formatter/)

## 関連記事

- [AIでExcel作業を自動化する方法【マクロ不要で誰でもできる】](/ja/posts/ai-excel-自動化/)
- [Excel関数よく使うもの一覧【2026年版・コピペ即使える】仕事で役立つ厳選50選](/ja/posts/excel-kansu-yoku-tsukau-ichiran/)
