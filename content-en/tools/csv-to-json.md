---
title: "CSV to JSON Converter"
slug: "csv-to-json"
date: 2025-05-16
description: "Free CSV to JSON converter. Parse CSV data into JSON arrays or objects with custom delimiters, header detection, and type inference — all in your browser."
categories: ["Free Tools"]
ShowToc: false
cover:
  image: /images/covers/csv-to-json.png
  alt: "CSV to JSON Converter — free browser-based tool"
---

Convert CSV data to JSON instantly — or reverse it. Paste text, upload a file, pick your format, and download the result. Everything runs in your browser; no data is sent to any server.

**Related tools:** [JSON to CSV Converter](/tools/json-to-csv/) &nbsp;·&nbsp; [JSON Formatter](/tools/json-formatter/)

---

<div id="cj-app">

<style>
/* ── Reset / base ── */
#cj-app *, #cj-app *::before, #cj-app *::after { box-sizing: border-box; margin: 0; padding: 0; }
#cj-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.6;
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
  letter-spacing: .05em;
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
  font-weight: 600;
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
     CSV → JSON PANEL
═══════════════════════════════════════════ -->
<div id="cj-panel-csv2json">

  <!-- Options card -->
  <div class="cj-card">
    <div class="cj-section-title">Options</div>
    <div class="cj-controls">
      <!-- Delimiter -->
      <div class="cj-control-group">
        <span class="cj-label">Delimiter</span>
        <select id="cj-delimiter" onchange="cjOnDelimiterChange()">
          <option value="auto">Auto-detect</option>
          <option value=",">Comma (,)</option>
          <option value="	">Tab (\t)</option>
          <option value=";">Semicolon (;)</option>
          <option value="|">Pipe (|)</option>
          <option value="custom">Custom…</option>
        </select>
      </div>
      <div class="cj-control-group" id="cj-custom-delim-group" style="display:none;">
        <span class="cj-label">Custom char</span>
        <input type="text" id="cj-custom-delim" maxlength="3" placeholder="e.g. ~" style="width:80px;" />
      </div>
      <!-- Output format -->
      <div class="cj-control-group">
        <span class="cj-label">Output format</span>
        <select id="cj-format">
          <option value="objects">Array of objects</option>
          <option value="arrays">Array of arrays</option>
          <option value="nested">Nested (group by first col)</option>
        </select>
      </div>
      <!-- Toggles -->
      <div class="cj-control-group" style="justify-content:flex-end;gap:8px;">
        <label class="cj-toggle-label">
          <input type="checkbox" id="cj-headers" checked />
          First row as headers
        </label>
        <label class="cj-toggle-label">
          <input type="checkbox" id="cj-typeinfer" checked />
          Type inference
        </label>
        <label class="cj-toggle-label">
          <input type="checkbox" id="cj-pretty" checked />
          Pretty print
        </label>
      </div>
    </div>
  </div>

  <!-- Input card -->
  <div class="cj-card">
    <div class="cj-section-title">CSV Input</div>
    <div class="cj-drop-zone" id="cj-drop-zone">
      <textarea class="cj-textarea" id="cj-csv-input"
        placeholder="Paste CSV here, or drag &amp; drop a .csv file…&#10;&#10;Example:&#10;name,age,active&#10;Alice,30,true&#10;Bob,25,false"></textarea>
      <span class="cj-drop-hint">drag &amp; drop .csv</span>
    </div>
    <div class="cj-file-row">
      <label class="cj-btn-file" for="cj-file-input">
        <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
        Upload .csv
      </label>
      <input type="file" id="cj-file-input" accept=".csv,text/csv,text/plain" />
      <span class="cj-file-name" id="cj-file-name">No file chosen</span>
    </div>
    <div class="cj-actions">
      <button class="cj-btn cj-btn-primary" onclick="cjConvert()">Convert to JSON</button>
      <button class="cj-btn cj-btn-secondary" onclick="cjClearInput()">Clear</button>
      <button class="cj-btn cj-btn-secondary" onclick="cjLoadSample()">Load sample</button>
    </div>
    <div class="cj-msg" id="cj-input-msg"></div>
    <div class="cj-stats" id="cj-input-stats" style="display:none;">
      <span class="cj-stat-item">Rows: <strong id="cj-row-count">0</strong></span>
      <span class="cj-stat-item">Columns: <strong id="cj-col-count">0</strong></span>
      <span class="cj-stat-item">Delimiter detected: <strong id="cj-detected-delim">—</strong></span>
    </div>
  </div>

  <!-- Preview card -->
  <div class="cj-card" id="cj-preview-card" style="display:none;">
    <div class="cj-section-title">Preview Table</div>
    <div class="cj-table-wrap" id="cj-table-wrap"></div>
  </div>

  <!-- Output card -->
  <div class="cj-card" id="cj-output-card" style="display:none;">
    <div class="cj-output-header">
      <div class="cj-section-title" style="margin-bottom:0;">JSON Output</div>
      <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
        <span class="cj-copy-feedback" id="cj-copy-feedback">Copied!</span>
        <button class="cj-btn cj-btn-secondary cj-btn-sm" onclick="cjCopy()">Copy JSON</button>
        <button class="cj-btn cj-btn-success cj-btn-sm" onclick="cjDownloadJSON()">Download .json</button>
      </div>
    </div>
    <textarea class="cj-output-textarea" id="cj-json-output" readonly></textarea>
    <div class="cj-stats" id="cj-output-stats">
      <span class="cj-stat-item">Records: <strong id="cj-record-count">0</strong></span>
      <span class="cj-stat-item">Size: <strong id="cj-output-size">0 B</strong></span>
    </div>
  </div>

</div><!-- /panel csv2json -->

<!-- ═══════════════════════════════════════════
     JSON → CSV PANEL
═══════════════════════════════════════════ -->
<div id="cj-panel-json2csv" style="display:none;">

  <div class="cj-card">
    <div class="cj-section-title">Options</div>
    <div class="cj-controls">
      <div class="cj-control-group">
        <span class="cj-label">Output delimiter</span>
        <select id="cj-j2c-delimiter">
          <option value=",">Comma (,)</option>
          <option value="	">Tab (\t)</option>
          <option value=";">Semicolon (;)</option>
          <option value="|">Pipe (|)</option>
        </select>
      </div>
      <div class="cj-control-group" style="justify-content:flex-end;gap:8px;">
        <label class="cj-toggle-label">
          <input type="checkbox" id="cj-j2c-headers" checked />
          Include header row
        </label>
        <label class="cj-toggle-label">
          <input type="checkbox" id="cj-j2c-quote" checked />
          Quote all strings
        </label>
      </div>
    </div>
  </div>

  <div class="cj-card">
    <div class="cj-section-title">JSON Input</div>
    <div class="cj-drop-zone">
      <textarea class="cj-textarea" id="cj-json-input"
        placeholder='Paste a JSON array here…&#10;&#10;Example:&#10;[{"name":"Alice","age":30},{"name":"Bob","age":25}]'></textarea>
    </div>
    <div class="cj-actions">
      <button class="cj-btn cj-btn-primary" onclick="cjConvertJ2C()">Convert to CSV</button>
      <button class="cj-btn cj-btn-secondary" onclick="document.getElementById('cj-json-input').value=''">Clear</button>
      <button class="cj-btn cj-btn-secondary" onclick="cjLoadJ2CSample()">Load sample</button>
    </div>
    <div class="cj-msg" id="cj-j2c-input-msg"></div>
  </div>

  <div class="cj-card" id="cj-j2c-output-card" style="display:none;">
    <div class="cj-output-header">
      <div class="cj-section-title" style="margin-bottom:0;">CSV Output</div>
      <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
        <span class="cj-copy-feedback" id="cj-j2c-copy-feedback">Copied!</span>
        <button class="cj-btn cj-btn-secondary cj-btn-sm" onclick="cjCopyCSV()">Copy CSV</button>
        <button class="cj-btn cj-btn-success cj-btn-sm" onclick="cjDownloadCSV()">Download .csv</button>
      </div>
    </div>
    <textarea class="cj-output-textarea" id="cj-csv-output" readonly></textarea>
    <div class="cj-stats" id="cj-j2c-output-stats">
      <span class="cj-stat-item">Rows: <strong id="cj-j2c-row-count">0</strong></span>
      <span class="cj-stat-item">Columns: <strong id="cj-j2c-col-count">0</strong></span>
      <span class="cj-stat-item">Size: <strong id="cj-j2c-size">0 B</strong></span>
    </div>
  </div>

</div><!-- /panel json2csv -->

</div><!-- /#cj-app -->

<script>
(function () {
  'use strict';

  /* ── Utilities ── */
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

  /* ── Mode switching ── */
  window.cjSetMode = function (mode) {
    ['csv2json', 'json2csv'].forEach(function (m) {
      document.getElementById('cj-tab-' + m).classList.toggle('active', m === mode);
      document.getElementById('cj-panel-' + m).style.display = m === mode ? '' : 'none';
    });
  };

  /* ── Delimiter auto-detect ── */
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
    if (sel === 'auto') return null; // signal: auto
    if (sel === 'custom') return document.getElementById('cj-custom-delim').value || ',';
    return sel;
  }

  window.cjOnDelimiterChange = function () {
    var sel = document.getElementById('cj-delimiter').value;
    document.getElementById('cj-custom-delim-group').style.display = sel === 'custom' ? '' : 'none';
  };

  /* ── CSV Parser (RFC 4180-aware) ── */
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

      // Check for delimiter (supports multi-char in future)
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
    // Last field/row
    if (field !== '' || row.length > 0) { row.push(field); rows.push(row); }
    // Drop trailing empty row
    if (rows.length && rows[rows.length - 1].every(function (c) { return c === ''; })) rows.pop();
    return rows;
  }

  /* ── Type inference ── */
  function inferValue(s) {
    if (s === '' || s.toLowerCase() === 'null' || s.toLowerCase() === 'n/a') return null;
    if (s.toLowerCase() === 'true') return true;
    if (s.toLowerCase() === 'false') return false;
    if (s !== '' && !isNaN(Number(s)) && s.trim() !== '') return Number(s);
    return s;
  }

  /* ── Main convert CSV → JSON ── */
  window.cjConvert = function () {
    hideMsg('cj-input-msg');
    var raw = document.getElementById('cj-csv-input').value.trim();
    if (!raw) { showMsg('cj-input-msg', 'Please paste some CSV data or upload a file.', 'error'); return; }

    var delimSel = getDelimiter();
    var delim = delimSel === null ? detectDelimiter(raw) : delimSel;
    var displayDelim = delim === '\t' ? '\\t' : delim;

    var rows = parseCSV(raw, delim);
    if (!rows.length) { showMsg('cj-input-msg', 'Could not parse any rows.', 'error'); return; }

    var useHeaders = document.getElementById('cj-headers').checked;
    var useTypeInfer = document.getElementById('cj-typeinfer').checked;
    var pretty = document.getElementById('cj-pretty').checked;
    var format = document.getElementById('cj-format').value;

    var headers = useHeaders ? rows[0] : rows[0].map(function (_, i) { return 'col' + (i + 1); });
    var dataRows = useHeaders ? rows.slice(1) : rows;

    // Stats
    document.getElementById('cj-row-count').textContent = dataRows.length;
    document.getElementById('cj-col-count').textContent = headers.length;
    document.getElementById('cj-detected-delim').textContent = delimSel === null ? '"' + displayDelim + '" (auto)' : '"' + displayDelim + '"';
    document.getElementById('cj-input-stats').style.display = '';

    // Build output
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

  /* ── Preview table ── */
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
    if (dataRows.length > 50) html += '<p style="font-size:11px;color:#94a3b8;padding:6px 12px;">Showing first 50 of ' + dataRows.length + ' rows</p>';
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
    if (!raw) { showMsg('cj-j2c-input-msg', 'Please paste a JSON array.', 'error'); return; }

    var data;
    try { data = JSON.parse(raw); } catch (e) { showMsg('cj-j2c-input-msg', 'Invalid JSON: ' + e.message, 'error'); return; }

    if (!Array.isArray(data)) { showMsg('cj-j2c-input-msg', 'Input must be a JSON array (e.g. [{…},{…}]).', 'error'); return; }
    if (!data.length) { showMsg('cj-j2c-input-msg', 'Array is empty.', 'error'); return; }

    var delim = document.getElementById('cj-j2c-delimiter').value;
    var includeHeaders = document.getElementById('cj-j2c-headers').checked;
    var quoteAll = document.getElementById('cj-j2c-quote').checked;

    // Collect all keys
    var keysSet = {};
    var keys = [];
    data.forEach(function (item) {
      if (typeof item === 'object' && item !== null) {
        Object.keys(item).forEach(function (k) {
          if (!keysSet[k]) { keysSet[k] = true; keys.push(k); }
        });
      }
    });
    if (!keys.length) { showMsg('cj-j2c-input-msg', 'Could not extract keys from array items.', 'error'); return; }

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

  /* ── Clipboard / Download ── */
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

  /* ── Clear ── */
  window.cjClearInput = function () {
    document.getElementById('cj-csv-input').value = '';
    document.getElementById('cj-file-name').textContent = 'No file chosen';
    hide('cj-output-card'); hide('cj-preview-card');
    document.getElementById('cj-input-stats').style.display = 'none';
    hideMsg('cj-input-msg');
  };

  /* ── Sample data ── */
  window.cjLoadSample = function () {
    document.getElementById('cj-csv-input').value =
      'id,name,department,salary,full_time\n' +
      '1,Alice Johnson,Engineering,95000,true\n' +
      '2,Bob Smith,Marketing,72000,false\n' +
      '3,Carol White,Engineering,105000,true\n' +
      '4,Dave Brown,HR,,true\n' +
      '5,"Lee, James",Sales,88000,true';
    cjConvert();
  };
  window.cjLoadJ2CSample = function () {
    document.getElementById('cj-json-input').value = JSON.stringify([
      { id: 1, name: 'Alice Johnson', department: 'Engineering', salary: 95000, full_time: true },
      { id: 2, name: 'Bob Smith', department: 'Marketing', salary: 72000, full_time: false },
      { id: 3, name: 'Carol White', department: 'Engineering', salary: 105000, full_time: true }
    ], null, 2);
    cjConvertJ2C();
  };

  /* ── File upload ── */
  document.getElementById('cj-file-input').addEventListener('change', function (e) {
    var file = e.target.files[0];
    if (!file) return;
    document.getElementById('cj-file-name').textContent = file.name;
    var reader = new FileReader();
    reader.onload = function (ev) {
      document.getElementById('cj-csv-input').value = ev.target.result;
      cjConvert();
    };
    reader.readAsText(file);
  });

  /* ── Drag and drop ── */
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
    reader.readAsText(file);
  });

})();
</script>

---

### How It Works

**CSV → JSON**

1. Paste CSV text or upload a `.csv` file (drag and drop supported).
2. Choose a delimiter — or leave it on **Auto-detect** and the tool will count occurrences on the first line to find the right separator.
3. Toggle **First row as headers** to control whether row 1 becomes object keys or data.
4. Pick an output format:
   - **Array of objects** — most common; each row becomes `{ "col": "val", … }`.
   - **Array of arrays** — compact; rows stay as plain arrays.
   - **Nested** — groups rows into an object keyed by the first column's value.
5. **Type inference** automatically converts numbers, `true`/`false`, and empty/`null`/`n/a` cells to proper JSON types.
6. Hit **Convert**, review the preview table, then **Copy** or **Download**.

**JSON → CSV**

Switch to the **JSON → CSV** tab, paste any flat JSON array, choose your output delimiter, and download the result.

**Quoted fields** with commas inside (e.g. `"Lee, James"`) are handled correctly per RFC 4180.

---

**Related tools:** [JSON to CSV Converter](/tools/json-to-csv/) &nbsp;·&nbsp; [JSON Formatter](/tools/json-formatter/)

## Related Articles

- [How to Use AI for Excel Automation 2026](/posts/how-to-use-ai-for-excel-automation-2026/)
- [How to Use ChatGPT for Data Analysis 2026](/posts/how-to-use-chatgpt-for-data-analysis-2026/)
- [Google Sheets vs Excel 2026: Which Is Better for You?](/posts/google-sheets-vs-excel-2026/)
