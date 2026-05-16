---
title: "CSVエディター"
slug: "csv-editor"
description: "無料のオンラインCSVエディター。貼り付けまたはファイルアップロードでインポートし、スプレッドシート感覚でCSVを編集・ソート・フィルター・エクスポート。RFC 4180準拠。"
categories: ["無料ツール"]
date: 2025-05-16
ShowToc: false
cover:
  image: "/images/covers/csv-editor-ja.png"
  alt: "CSVエディター"
aliases: ["/ja/tools/csv-viewer/", "/ja/tools/csv-editor/"]
---

ブラウザだけで動作するCSVエディター。貼り付けまたはファイルアップロードでインポートし、セルを直接編集、行・列の追加削除、ソート、フィルタリング、CSVエクスポートまで一括対応。サーバー送信なし・外部ライブラリなし。

<style>
#csv-app*,#csv-app*::before,#csv-app*::after{box-sizing:border-box;margin:0;padding:0}
#csv-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Kaku Gothic ProN','Hiragino Sans','Yu Gothic',Meiryo,sans-serif;font-size:15px;color:#1f2937;line-height:1.6;max-width:980px;margin:1.5rem auto}
#csv-app h2{font-size:.95rem;font-weight:700;color:#111827;margin-bottom:.45rem}
#csv-app .ca-toolbar{display:flex;flex-wrap:wrap;gap:.5rem;align-items:center;background:#f9fafb;border:1px solid #e5e7eb;border-radius:9px;padding:.65rem .9rem;margin-bottom:.9rem}
#csv-app .ca-btn{padding:.38rem .85rem;border:none;border-radius:6px;font-size:.82rem;font-weight:600;cursor:pointer;transition:background .13s,opacity .13s;white-space:nowrap}
#csv-app .ca-btn:disabled{opacity:.38;cursor:not-allowed}
#csv-app .ca-btn-blue{background:#2563eb;color:#fff}
#csv-app .ca-btn-blue:hover:not(:disabled){background:#1d4ed8}
#csv-app .ca-btn-green{background:#059669;color:#fff}
#csv-app .ca-btn-green:hover:not(:disabled){background:#047857}
#csv-app .ca-btn-red{background:#ef4444;color:#fff}
#csv-app .ca-btn-red:hover:not(:disabled){background:#dc2626}
#csv-app .ca-btn-gray{background:#e5e7eb;color:#374151}
#csv-app .ca-btn-gray:hover:not(:disabled){background:#d1d5db}
#csv-app .ca-btn-orange{background:#f59e0b;color:#fff}
#csv-app .ca-btn-orange:hover:not(:disabled){background:#d97706}
#csv-app .ca-sep{width:1px;height:24px;background:#d1d5db;margin:0 .15rem}
#csv-app .ca-search{padding:.36rem .7rem;border:1.5px solid #d1d5db;border-radius:6px;font-size:.82rem;color:#374151;outline:none;width:200px;transition:border-color .13s}
#csv-app .ca-search:focus{border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#csv-app .ca-import-area{display:flex;flex-direction:column;gap:.65rem;margin-bottom:1rem}
#csv-app .ca-import-row{display:flex;flex-wrap:wrap;gap:.5rem;align-items:flex-start}
#csv-app textarea.ca-paste{width:100%;height:140px;padding:.6rem .75rem;border:1.5px solid #d1d5db;border-radius:8px;font-family:'SFMono-Regular',Consolas,'Liberation Mono',Menlo,monospace;font-size:.78rem;line-height:1.55;color:#1f2937;background:#fff;resize:vertical;outline:none;transition:border-color .13s}
#csv-app textarea.ca-paste:focus{border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#csv-app .ca-file-label{display:inline-flex;align-items:center;gap:.35rem;padding:.38rem .85rem;background:#f3f4f6;border:1.5px dashed #9ca3af;border-radius:7px;font-size:.82rem;font-weight:600;color:#4b5563;cursor:pointer;transition:background .13s,border-color .13s}
#csv-app .ca-file-label:hover{background:#e5e7eb;border-color:#6b7280}
#csv-app input[type=file].ca-file-input{display:none}
#csv-app .ca-opt-row{display:flex;flex-wrap:wrap;gap:.65rem 1.2rem;align-items:center;font-size:.8rem;color:#4b5563}
#csv-app .ca-opt-row label{display:flex;align-items:center;gap:.3rem;cursor:pointer;user-select:none}
#csv-app .ca-opt-row select{padding:.25rem .45rem;border:1px solid #d1d5db;border-radius:5px;font-size:.8rem;color:#374151;background:#fff;cursor:pointer}
#csv-app .ca-opt-row input[type=checkbox]{width:14px;height:14px;accent-color:#2563eb;cursor:pointer}
#csv-app .ca-table-wrap{overflow:auto;border:1.5px solid #d1d5db;border-radius:10px;max-height:480px;margin-bottom:.75rem;position:relative}
#csv-app .ca-table-wrap table{border-collapse:collapse;font-size:.8rem;min-width:100%;table-layout:auto}
#csv-app .ca-table-wrap thead{position:sticky;top:0;z-index:10}
#csv-app .ca-table-wrap th.ca-th-num{background:#f3f4f6;color:#6b7280;font-weight:600;padding:.38rem .55rem;border-bottom:2px solid #d1d5db;border-right:1px solid #e5e7eb;min-width:38px;text-align:center;position:sticky;left:0;z-index:12}
#csv-app .ca-table-wrap th.ca-th-col{background:#eff6ff;color:#1e3a8a;font-weight:700;padding:.38rem .5rem;border-bottom:2px solid #bfdbfe;border-right:1px solid #dbeafe;white-space:nowrap;cursor:default;min-width:90px}
#csv-app .ca-table-wrap th.ca-th-col .ca-th-inner{display:flex;align-items:center;gap:0;min-height:26px}
#csv-app .ca-table-wrap th.ca-th-col .ca-th-name{flex:1;outline:none;border:none;background:transparent;font:inherit;font-weight:700;color:#1e3a8a;cursor:text;min-width:60px;padding:0 2px}
#csv-app .ca-table-wrap th.ca-th-col .ca-sort-btn{background:none;border:none;padding:2px 3px;cursor:pointer;font-size:.75rem;color:#6b7280;line-height:1;border-radius:3px;flex-shrink:0}
#csv-app .ca-table-wrap th.ca-th-col .ca-sort-btn:hover{background:#dbeafe;color:#1d4ed8}
#csv-app .ca-table-wrap th.ca-th-col .ca-sort-btn.ca-sort-active{color:#2563eb}
#csv-app .ca-table-wrap th.ca-th-col .ca-del-col-btn{background:none;border:none;padding:2px 3px;cursor:pointer;font-size:.7rem;color:#9ca3af;line-height:1;border-radius:3px;flex-shrink:0;opacity:0;transition:opacity .12s}
#csv-app .ca-table-wrap th.ca-th-col:hover .ca-del-col-btn{opacity:1}
#csv-app .ca-table-wrap th.ca-th-col .ca-del-col-btn:hover{background:#fee2e2;color:#dc2626}
#csv-app .ca-table-wrap td.ca-td-num{background:#f9fafb;color:#9ca3af;font-size:.72rem;text-align:center;padding:.3rem .4rem;border-bottom:1px solid #f3f4f6;border-right:1px solid #e5e7eb;min-width:38px;position:sticky;left:0;z-index:2}
#csv-app .ca-table-wrap td.ca-td-cell{padding:0;border-bottom:1px solid #f3f4f6;border-right:1px solid #f3f4f6}
#csv-app .ca-table-wrap td.ca-td-cell input{display:block;width:100%;height:100%;padding:.32rem .55rem;border:none;outline:none;background:transparent;font-family:inherit;font-size:.8rem;color:#1f2937;min-height:30px}
#csv-app .ca-table-wrap td.ca-td-cell input:focus{background:#eff6ff;box-shadow:inset 0 0 0 2px #2563eb}
#csv-app .ca-table-wrap tr:nth-child(even) td{background:#f9fafb}
#csv-app .ca-table-wrap tr:nth-child(even) td.ca-td-num{background:#f3f4f6}
#csv-app .ca-table-wrap tr:nth-child(even) td.ca-td-cell input{background:transparent}
#csv-app .ca-table-wrap tr:nth-child(even) td.ca-td-cell input:focus{background:#eff6ff}
#csv-app .ca-table-wrap td.ca-td-del{padding:.3rem .35rem;border-bottom:1px solid #f3f4f6;text-align:center;vertical-align:middle}
#csv-app .ca-table-wrap td.ca-td-del button{background:none;border:none;cursor:pointer;color:#d1d5db;font-size:.85rem;line-height:1;border-radius:4px;padding:2px 5px;transition:color .12s,background .12s}
#csv-app .ca-table-wrap td.ca-td-del button:hover{color:#ef4444;background:#fee2e2}
#csv-app .ca-table-wrap th.ca-th-del{background:#f3f4f6;border-bottom:2px solid #d1d5db;border-right:1px solid #e5e7eb;padding:.38rem .35rem;min-width:32px}
#csv-app .ca-status{display:flex;justify-content:space-between;align-items:center;font-size:.78rem;color:#6b7280;margin-bottom:.5rem;flex-wrap:wrap;gap:.3rem}
#csv-app .ca-status .ca-filtered-note{color:#d97706;font-weight:600}
#csv-app .ca-msg{font-size:.8rem;padding:.3rem .65rem;border-radius:5px;margin-bottom:.5rem;display:none}
#csv-app .ca-msg.err{background:#fef2f2;color:#dc2626;border:1px solid #fca5a5;display:block}
#csv-app .ca-msg.ok{background:#ecfdf5;color:#059669;border:1px solid #6ee7b7;display:block}
#csv-app .ca-export-wrap{display:flex;flex-direction:column;gap:.5rem}
#csv-app .ca-export-row{display:flex;flex-wrap:wrap;gap:.5rem;align-items:center}
#csv-app textarea.ca-export-ta{width:100%;height:120px;padding:.55rem .7rem;border:1.5px solid #d1d5db;border-radius:8px;font-family:'SFMono-Regular',Consolas,'Liberation Mono',Menlo,monospace;font-size:.76rem;line-height:1.5;color:#374151;background:#f8fafc;resize:vertical;outline:none}
#csv-app .ca-empty{text-align:center;padding:2.5rem 1rem;color:#9ca3af;font-size:.88rem}
#csv-app .ca-related{background:#f8fafc;border:1.5px solid #e5e7eb;border-radius:10px;padding:1rem 1.2rem;margin-top:1.6rem}
#csv-app .ca-related h3{font-size:.9rem;font-weight:700;margin-bottom:.6rem;color:#374151}
#csv-app .ca-related-links{display:flex;flex-wrap:wrap;gap:.45rem}
#csv-app .ca-related-links a{display:inline-block;padding:.32rem .8rem;background:#eff6ff;color:#1d4ed8;border:1px solid #bfdbfe;border-radius:6px;font-size:.8rem;font-weight:600;text-decoration:none;transition:background .13s}
#csv-app .ca-related-links a:hover{background:#dbeafe}
@media(max-width:640px){#csv-app .ca-search{width:100%}#csv-app .ca-toolbar{gap:.4rem}#csv-app .ca-sep{display:none}}
</style>

<div id="csv-app">

<div class="ca-import-area">
  <h2>CSVをインポート</h2>
  <div class="ca-opt-row">
    <label>区切り文字: <select id="ca-delim"><option value=",">カンマ (,)</option><option value="	">タブ (\t)</option><option value=";">セミコロン (;)</option><option value="|">パイプ (|)</option></select></label>
    <label><input type="checkbox" id="ca-has-header" checked> 1行目を見出しにする</label>
  </div>
  <textarea class="ca-paste" id="ca-paste" placeholder="CSVをここに貼り付け（例: 名前,年齢,都市&#10;Alice,30,東京&#10;Bob,25,大阪）"></textarea>
  <div class="ca-import-row">
    <button class="ca-btn ca-btn-blue" id="ca-import-paste-btn">貼り付けからインポート</button>
    <label class="ca-file-label"><span>&#128196; CSVファイルをアップロード</span><input type="file" class="ca-file-input" id="ca-file-input" accept=".csv,text/csv,text/plain"></label>
    <button class="ca-btn ca-btn-gray" id="ca-load-sample-btn">サンプルを読み込む</button>
  </div>
</div>

<div class="ca-msg" id="ca-msg"></div>

<div id="ca-editor-section" style="display:none">
  <div class="ca-toolbar">
    <input class="ca-search" id="ca-search" type="search" placeholder="行を検索・フィルター...">
    <div class="ca-sep"></div>
    <button class="ca-btn ca-btn-green" id="ca-add-row-btn">+ 行を追加</button>
    <button class="ca-btn ca-btn-green" id="ca-add-col-btn">+ 列を追加</button>
    <div class="ca-sep"></div>
    <button class="ca-btn ca-btn-gray" id="ca-clear-btn">全消去</button>
  </div>

  <div class="ca-status">
    <span id="ca-status-text"></span>
    <span id="ca-filtered-note" class="ca-filtered-note" style="display:none"></span>
  </div>

  <div class="ca-table-wrap" id="ca-table-wrap">
    <div class="ca-empty">データがありません。</div>
  </div>

  <div class="ca-export-wrap" style="margin-top:.9rem">
    <h2>CSVをエクスポート</h2>
    <div class="ca-export-row">
      <button class="ca-btn ca-btn-blue" id="ca-generate-btn">CSV生成</button>
      <button class="ca-btn ca-btn-green" id="ca-copy-btn" disabled>クリップボードにコピー</button>
      <button class="ca-btn ca-btn-orange" id="ca-download-btn" disabled>CSVをダウンロード</button>
    </div>
    <textarea class="ca-export-ta" id="ca-export-ta" readonly placeholder="「CSV生成」をクリックするとここにプレビューが表示されます..."></textarea>
  </div>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div class="ca-related">
  <h3>関連ツール</h3>
  <div class="ca-related-links">
    <a href="/ja/tools/json-to-csv/">JSON⇔CSV変換ツール</a>
    <a href="/ja/tools/markdown-table-generator/">Markdownテーブル生成</a>
  </div>
</div>

</div>

<script>
(function(){
'use strict';

// ── 状態 ────────────────────────────────────────────────────────────────────
var state = {
  headers: [],
  rows: [],
  sortCol: -1,
  sortDir: 1,
  filter: '',
  lastCsv: ''
};

// ── 要素取得 ────────────────────────────────────────────────────────────────
var app          = document.getElementById('csv-app');
var pasteEl      = document.getElementById('ca-paste');
var fileInput    = document.getElementById('ca-file-input');
var delimEl      = document.getElementById('ca-delim');
var headerCb     = document.getElementById('ca-has-header');
var importBtn    = document.getElementById('ca-import-paste-btn');
var sampleBtn    = document.getElementById('ca-load-sample-btn');
var searchEl     = document.getElementById('ca-search');
var addRowBtn    = document.getElementById('ca-add-row-btn');
var addColBtn    = document.getElementById('ca-add-col-btn');
var clearBtn     = document.getElementById('ca-clear-btn');
var tableWrap    = document.getElementById('ca-table-wrap');
var statusText   = document.getElementById('ca-status-text');
var filteredNote = document.getElementById('ca-filtered-note');
var editorSec    = document.getElementById('ca-editor-section');
var msgEl        = document.getElementById('ca-msg');
var generateBtn  = document.getElementById('ca-generate-btn');
var copyBtn      = document.getElementById('ca-copy-btn');
var downloadBtn  = document.getElementById('ca-download-btn');
var exportTa     = document.getElementById('ca-export-ta');

// ── RFC 4180 パーサー ────────────────────────────────────────────────────────
function parseCSV(text, delim) {
  delim = delim || ',';
  var rows = [], row = [], field = '', inQuote = false, i = 0, c, nc;
  text = text.replace(/\r\n/g, '\n').replace(/\r/g, '\n');
  if (text.length && text[text.length-1] !== '\n') text += '\n';
  while (i < text.length) {
    c = text[i];
    if (inQuote) {
      if (c === '"') {
        nc = text[i+1];
        if (nc === '"') { field += '"'; i += 2; continue; }
        inQuote = false; i++; continue;
      }
      field += c; i++; continue;
    }
    if (c === '"') { inQuote = true; i++; continue; }
    if (c === delim) { row.push(field); field = ''; i++; continue; }
    if (c === '\n') {
      row.push(field); field = '';
      if (i < text.length - 1 || row.some(function(f){return f!==''})) rows.push(row);
      row = []; i++; continue;
    }
    field += c; i++;
  }
  return rows;
}

// ── RFC 4180 シリアライザー ──────────────────────────────────────────────────
function serializeCSV(headers, rows, delim) {
  delim = delim || ',';
  function escField(f) {
    f = String(f == null ? '' : f);
    if (f.indexOf(delim) !== -1 || f.indexOf('"') !== -1 || f.indexOf('\n') !== -1 || f.indexOf('\r') !== -1) {
      return '"' + f.replace(/"/g, '""') + '"';
    }
    return f;
  }
  var lines = [];
  if (headers.length) lines.push(headers.map(escField).join(delim));
  rows.forEach(function(r){ lines.push(r.map(escField).join(delim)); });
  return lines.join('\r\n');
}

// ── 行幅を正規化 ────────────────────────────────────────────────────────────
function normalizeRows() {
  var w = state.headers.length;
  state.rows.forEach(function(r) {
    while (r.length < w) r.push('');
    r.length = w;
  });
}

// ── フィルター／ソート済みビュー ────────────────────────────────────────────
function getView() {
  var rows = state.rows.slice();
  var q = state.filter.trim().toLowerCase();
  if (q) {
    rows = rows.filter(function(r) {
      return r.some(function(c){ return String(c).toLowerCase().indexOf(q) !== -1; });
    });
  }
  if (state.sortCol >= 0 && state.sortCol < state.headers.length) {
    var col = state.sortCol, dir = state.sortDir;
    rows = rows.slice().sort(function(a, b) {
      var av = a[col] || '', bv = b[col] || '';
      var an = parseFloat(av), bn = parseFloat(bv);
      if (!isNaN(an) && !isNaN(bn)) return (an - bn) * dir;
      return av.localeCompare(bv) * dir;
    });
  }
  return rows;
}

// ── テーブル描画 ────────────────────────────────────────────────────────────
function render() {
  var view = getView();

  statusText.textContent = state.rows.length + ' 行、' + state.headers.length + ' 列';
  if (state.filter.trim()) {
    filteredNote.textContent = state.rows.length + ' 行中 ' + view.length + ' 行を表示（フィルター中）';
    filteredNote.style.display = '';
  } else {
    filteredNote.style.display = 'none';
  }

  if (!state.headers.length && !state.rows.length) {
    tableWrap.innerHTML = '<div class="ca-empty">データがありません。CSVをインポートするか、「行を追加」「列を追加」から開始してください。</div>';
    return;
  }

  var html = '<table><thead><tr>';
  html += '<th class="ca-th-num">#</th>';
  state.headers.forEach(function(h, ci) {
    var sortIcon = '⇅';
    var sortCls = '';
    if (state.sortCol === ci) { sortIcon = state.sortDir === 1 ? '↑' : '↓'; sortCls = ' ca-sort-active'; }
    html += '<th class="ca-th-col" data-ci="' + ci + '">' +
      '<div class="ca-th-inner">' +
      '<input class="ca-th-name" data-ci="' + ci + '" value="' + escAttr(h) + '" title="列名を変更">' +
      '<button class="ca-sort-btn' + sortCls + '" data-ci="' + ci + '" title="ソート">' + sortIcon + '</button>' +
      '<button class="ca-del-col-btn" data-ci="' + ci + '" title="列を削除">✕</button>' +
      '</div></th>';
  });
  html += '<th class="ca-th-del"></th>';
  html += '</tr></thead><tbody>';

  view.forEach(function(row, vi) {
    var origIdx = state.rows.indexOf(row);
    html += '<tr>';
    html += '<td class="ca-td-num">' + (vi + 1) + '</td>';
    state.headers.forEach(function(_, ci) {
      var val = row[ci] != null ? row[ci] : '';
      html += '<td class="ca-td-cell"><input type="text" value="' + escAttr(val) + '" data-orig="' + origIdx + '" data-ci="' + ci + '"></td>';
    });
    html += '<td class="ca-td-del"><button data-orig="' + origIdx + '" title="行を削除">✕</button></td>';
    html += '</tr>';
  });

  html += '</tbody></table>';
  tableWrap.innerHTML = html;

  // ── イベント登録 ───────────────────────────────────────────────────────
  tableWrap.querySelectorAll('.ca-th-name').forEach(function(inp) {
    inp.addEventListener('change', function() {
      state.headers[+this.dataset.ci] = this.value;
      invalidateExport();
    });
    inp.addEventListener('keydown', function(e){ if(e.key==='Enter') this.blur(); });
  });
  tableWrap.querySelectorAll('.ca-sort-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var ci = +this.dataset.ci;
      if (state.sortCol === ci) {
        if (state.sortDir === 1) { state.sortDir = -1; }
        else { state.sortCol = -1; state.sortDir = 1; }
      } else { state.sortCol = ci; state.sortDir = 1; }
      render();
    });
  });
  tableWrap.querySelectorAll('.ca-del-col-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var ci = +this.dataset.ci;
      if (!confirm('列「' + state.headers[ci] + '」を削除しますか？')) return;
      state.headers.splice(ci, 1);
      state.rows.forEach(function(r){ r.splice(ci, 1); });
      if (state.sortCol === ci) { state.sortCol = -1; }
      else if (state.sortCol > ci) { state.sortCol--; }
      invalidateExport(); render();
    });
  });
  tableWrap.querySelectorAll('.ca-td-cell input').forEach(function(inp) {
    inp.addEventListener('change', function() {
      var orig = +this.dataset.orig, ci = +this.dataset.ci;
      if (state.rows[orig]) { state.rows[orig][ci] = this.value; invalidateExport(); }
    });
    inp.addEventListener('keydown', function(e){
      if (e.key === 'Enter') { e.preventDefault(); moveFocus(this, 1, 0); }
      if (e.key === 'Tab' && !e.shiftKey) { e.preventDefault(); moveFocus(this, 0, 1); }
      if (e.key === 'Tab' && e.shiftKey) { e.preventDefault(); moveFocus(this, 0, -1); }
    });
  });
  tableWrap.querySelectorAll('.ca-td-del button').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var orig = +this.dataset.orig;
      state.rows.splice(orig, 1);
      invalidateExport(); render();
    });
  });
}

function moveFocus(inp, dr, dc) {
  var inputs = Array.from(tableWrap.querySelectorAll('.ca-td-cell input'));
  var idx = inputs.indexOf(inp);
  if (idx < 0) return;
  var cols = state.headers.length;
  var newIdx = idx + dr * cols + dc;
  if (newIdx >= 0 && newIdx < inputs.length) inputs[newIdx].focus();
}

function escAttr(s) {
  return String(s == null ? '' : s).replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function showMsg(txt, type) {
  msgEl.textContent = txt;
  msgEl.className = 'ca-msg ' + (type || 'ok');
  clearTimeout(msgEl._t);
  msgEl._t = setTimeout(function(){ msgEl.className = 'ca-msg'; }, 3500);
}

function invalidateExport() {
  state.lastCsv = '';
  exportTa.value = '';
  copyBtn.disabled = true;
  downloadBtn.disabled = true;
}

function showEditor() { editorSec.style.display = ''; }

// ── インポート処理 ───────────────────────────────────────────────────────────
function importText(text) {
  var delim = delimEl.value;
  var rows = parseCSV(text.trim(), delim);
  if (!rows.length) { showMsg('データが見つかりませんでした。', 'err'); return; }
  var hasHeader = headerCb.checked;
  if (hasHeader && rows.length > 0) {
    state.headers = rows[0].map(function(h){ return h.trim(); });
    state.rows = rows.slice(1).map(function(r){ return r.slice(); });
  } else {
    var maxCols = rows.reduce(function(m,r){ return Math.max(m, r.length); }, 0);
    state.headers = [];
    for (var i=0;i<maxCols;i++) state.headers.push('列' + (i+1));
    state.rows = rows.map(function(r){ return r.slice(); });
  }
  normalizeRows();
  state.sortCol = -1; state.sortDir = 1; state.filter = ''; searchEl.value = '';
  invalidateExport();
  showEditor();
  render();
  showMsg(state.rows.length + ' 行、' + state.headers.length + ' 列をインポートしました。', 'ok');
}

importBtn.addEventListener('click', function() {
  var text = pasteEl.value;
  if (!text.trim()) { showMsg('CSVを貼り付けてください。', 'err'); return; }
  importText(text);
});

fileInput.addEventListener('change', function() {
  var file = this.files[0];
  if (!file) return;
  var reader = new FileReader();
  reader.onload = function(e) { importText(e.target.result); };
  reader.onerror = function() { showMsg('ファイルを読み込めませんでした。', 'err'); };
  reader.readAsText(file, 'UTF-8');
  fileInput.value = '';
});

sampleBtn.addEventListener('click', function() {
  pasteEl.value = '名前,年齢,都市,国,スコア\nAlice,30,東京,日本,92.5\nBob,25,ロンドン,イギリス,87.0\nCarla,34,ニューヨーク,アメリカ,95.5\n"Smith, John",28,"パリ, フランス",フランス,80.0\nEva,22,シドニー,オーストラリア,78.5';
  delimEl.value = ',';
  headerCb.checked = true;
  showMsg('サンプルデータを読み込みました。「貼り付けからインポート」をクリックしてください。', 'ok');
});

// ── 検索・フィルター ─────────────────────────────────────────────────────────
searchEl.addEventListener('input', function() {
  state.filter = this.value;
  render();
});

// ── 行・列追加 ───────────────────────────────────────────────────────────────
addRowBtn.addEventListener('click', function() {
  if (!state.headers.length) {
    state.headers = ['列1'];
  }
  var newRow = [];
  for (var i=0;i<state.headers.length;i++) newRow.push('');
  state.rows.push(newRow);
  invalidateExport(); showEditor(); render();
  setTimeout(function(){ tableWrap.scrollTop = tableWrap.scrollHeight; }, 30);
});

addColBtn.addEventListener('click', function() {
  var name = prompt('新しい列名を入力してください:', '列' + (state.headers.length + 1));
  if (name === null) return;
  name = name.trim() || ('列' + (state.headers.length + 1));
  state.headers.push(name);
  state.rows.forEach(function(r){ r.push(''); });
  invalidateExport(); showEditor(); render();
});

clearBtn.addEventListener('click', function() {
  if (!confirm('すべてのデータを消去しますか？')) return;
  state.headers = []; state.rows = [];
  state.sortCol = -1; state.sortDir = 1; state.filter = '';
  searchEl.value = ''; pasteEl.value = '';
  invalidateExport(); render();
  editorSec.style.display = 'none';
});

// ── エクスポート ─────────────────────────────────────────────────────────────
generateBtn.addEventListener('click', function() {
  var delim = delimEl.value;
  var csv = serializeCSV(state.headers, state.rows, delim);
  state.lastCsv = csv;
  exportTa.value = csv;
  copyBtn.disabled = false;
  downloadBtn.disabled = false;
  showMsg('CSVを生成しました。', 'ok');
});

copyBtn.addEventListener('click', function() {
  if (!state.lastCsv) return;
  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(state.lastCsv).then(function() {
      showMsg('クリップボードにコピーしました！', 'ok');
    }).catch(function() { fallbackCopy(); });
  } else { fallbackCopy(); }
});

function fallbackCopy() {
  exportTa.select();
  try { document.execCommand('copy'); showMsg('クリップボードにコピーしました！', 'ok'); }
  catch(e) { showMsg('コピーに失敗しました。手動で選択してコピーしてください。', 'err'); }
}

downloadBtn.addEventListener('click', function() {
  if (!state.lastCsv) return;
  var blob = new Blob([state.lastCsv], {type:'text/csv;charset=utf-8;'});
  var url = URL.createObjectURL(blob);
  var a = document.createElement('a');
  a.href = url; a.download = 'data.csv';
  document.body.appendChild(a); a.click();
  setTimeout(function(){ document.body.removeChild(a); URL.revokeObjectURL(url); }, 500);
  showMsg('ダウンロードを開始しました。', 'ok');
});

})();
</script>

---
### 関連ツール
> JSON⇔CSV変換 → [JSON⇔CSV変換ツール](/ja/tools/json-to-csv/)
> Markdownテーブル → [Markdownテーブル生成](/ja/tools/markdown-table-generator/)
---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
