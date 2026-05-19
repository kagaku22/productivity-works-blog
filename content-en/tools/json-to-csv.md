---
title: "JSON to CSV Converter — Free Online Tool"
description: "Convert JSON arrays to CSV and CSV back to JSON instantly in your browser. No upload, no server, no external libraries. Supports nested JSON, custom delimiters, and one-click download."
date: 2025-05-16
slug: "json-to-csv"
categories: ["Free Tools"]
ShowToc: false
aliases:
  - "/tools/csv-to-json/"
  - "/tools/json-to-csv/"
cover:
  image: "/images/covers/json-to-csv.png"
  alt: "JSON to CSV Converter"
---

Convert JSON arrays to CSV and CSV back to JSON — right in your browser. No server, no upload, no external libraries.

<style>
#j2c-app *,
#j2c-app *::before,
#j2c-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#j2c-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1f2937;
line-height: 1.5;
max-width: 900px;
margin: 2rem auto;
}

#j2c-app h2 {
font-size: 1.1rem;
font-weight: 600;
color: #374151;
margin-bottom: 0.5rem;
}

#j2c-app .j2c-tabs {
display: flex;
gap: 0.5rem;
margin-bottom: 1.5rem;
}

#j2c-app .j2c-tab {
padding: 0.55rem 1.2rem;
border: 2px solid #d1fae5;
border-radius: 6px;
background: #fff;
color: #059669;
font-weight: 600;
font-size: 0.95rem;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}

#j2c-app .j2c-tab.active {
background: #059669;
color: #fff;
border-color: #059669;
}

#j2c-app .j2c-tab:hover:not(.active) {
background: #d1fae5;
}

#j2c-app .j2c-controls {
display: flex;
flex-wrap: wrap;
gap: 1rem;
align-items: center;
background: #f9fafb;
border: 1px solid #e5e7eb;
border-radius: 8px;
padding: 0.85rem 1rem;
margin-bottom: 1.25rem;
}

#j2c-app .j2c-control-group {
display: flex;
align-items: center;
gap: 0.5rem;
}

#j2c-app label {
font-size: 0.88rem;
font-weight: 500;
color: #6b7280;
}

#j2c-app select {
padding: 0.3rem 0.6rem;
border: 1px solid #d1d5db;
border-radius: 5px;
font-size: 0.88rem;
background: #fff;
color: #374151;
cursor: pointer;
}

#j2c-app .j2c-toggle {
display: flex;
align-items: center;
gap: 0.45rem;
cursor: pointer;
user-select: none;
}

#j2c-app .j2c-toggle input[type="checkbox"] {
width: 16px;
height: 16px;
accent-color: #059669;
cursor: pointer;
}

#j2c-app .j2c-io-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
margin-bottom: 1.25rem;
}

@media (max-width: 640px) {
#j2c-app .j2c-io-grid {
grid-template-columns: 1fr;
}
}

#j2c-app .j2c-pane {
display: flex;
flex-direction: column;
gap: 0.4rem;
}

#j2c-app textarea {
width: 100%;
height: 220px;
padding: 0.65rem 0.8rem;
border: 1px solid #d1d5db;
border-radius: 8px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.82rem;
line-height: 1.5;
color: #1f2937;
background: #fff;
resize: vertical;
transition: border-color 0.15s;
}

#j2c-app textarea:focus {
outline: none;
border-color: #059669;
box-shadow: 0 0 0 3px rgba(5,150,105,0.12);
}

#j2c-app textarea.j2c-error {
border-color: #ef4444;
box-shadow: 0 0 0 3px rgba(239,68,68,0.1);
}

#j2c-app .j2c-pane-actions {
display: flex;
gap: 0.5rem;
}

#j2c-app .j2c-btn {
padding: 0.4rem 0.9rem;
border: none;
border-radius: 6px;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, opacity 0.15s;
}

#j2c-app .j2c-btn-primary {
background: #059669;
color: #fff;
}

#j2c-app .j2c-btn-primary:hover {
background: #047857;
}

#j2c-app .j2c-btn-secondary {
background: #e5e7eb;
color: #374151;
}

#j2c-app .j2c-btn-secondary:hover {
background: #d1d5db;
}

#j2c-app .j2c-btn:disabled {
opacity: 0.45;
cursor: not-allowed;
}

#j2c-app .j2c-convert-row {
display: flex;
justify-content: center;
margin-bottom: 1.25rem;
}

#j2c-app .j2c-btn-convert {
padding: 0.6rem 2rem;
background: #059669;
color: #fff;
border: none;
border-radius: 8px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
letter-spacing: 0.01em;
}

#j2c-app .j2c-btn-convert:hover {
background: #047857;
}

#j2c-app .j2c-msg {
font-size: 0.82rem;
padding: 0.35rem 0.7rem;
border-radius: 5px;
margin-top: 0.25rem;
display: none;
}

#j2c-app .j2c-msg.error {
background: #fef2f2;
color: #dc2626;
border: 1px solid #fca5a5;
display: block;
}

#j2c-app .j2c-msg.success {
background: #ecfdf5;
color: #059669;
border: 1px solid #6ee7b7;
display: block;
}

#j2c-app .j2c-preview-section {
margin-top: 0.5rem;
}

#j2c-app .j2c-preview-section h2 {
margin-bottom: 0.6rem;
}

#j2c-app .j2c-table-wrap {
overflow-x: auto;
border: 1px solid #e5e7eb;
border-radius: 8px;
max-height: 320px;
overflow-y: auto;
}

#j2c-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.82rem;
}

#j2c-app th {
background: #ecfdf5;
color: #065f46;
font-weight: 600;
padding: 0.5rem 0.75rem;
text-align: left;
border-bottom: 2px solid #6ee7b7;
white-space: nowrap;
position: sticky;
top: 0;
}

#j2c-app td {
padding: 0.4rem 0.75rem;
border-bottom: 1px solid #f3f4f6;
color: #374151;
max-width: 220px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}

#j2c-app tr:last-child td {
border-bottom: none;
}

#j2c-app tr:nth-child(even) td {
background: #f9fafb;
}

#j2c-app .j2c-preview-meta {
font-size: 0.78rem;
color: #9ca3af;
margin-top: 0.4rem;
}

#j2c-app .j2c-sample-link {
font-size: 0.8rem;
color: #059669;
text-decoration: underline;
cursor: pointer;
background: none;
border: none;
padding: 0;
}
</style>

<div id="j2c-app">

<div class="j2c-tabs">
<button class="j2c-tab active" id="j2c-tab-j2c" onclick="j2cSetMode('j2c')">JSON → CSV</button>
<button class="j2c-tab" id="j2c-tab-c2j" onclick="j2cSetMode('c2j')">CSV → JSON</button>
</div>

<div class="j2c-controls">
<div class="j2c-control-group">
<label for="j2c-delim">Delimiter</label>
<select id="j2c-delim">
<option value=",">Comma ( , )</option>
<option value=";">Semicolon ( ; )</option>
<option value="&#9;">Tab ( ⇥ )</option>
<option value="|">Pipe ( | )</option>
</select>
</div>
<div class="j2c-control-group">
<label class="j2c-toggle">
<input type="checkbox" id="j2c-header" checked>
Include header row
</label>
</div>
<div class="j2c-control-group">
<label class="j2c-toggle">
<input type="checkbox" id="j2c-flatten" checked>
Flatten nested JSON
</label>
</div>
</div>

<div class="j2c-io-grid">
<div class="j2c-pane">
<h2 id="j2c-input-label">JSON Input</h2>
<textarea id="j2c-input" placeholder='Paste JSON here, e.g.&#10;[&#10;  {"name":"Alice","age":30},&#10;  {"name":"Bob","age":25}&#10;]'></textarea>
<div class="j2c-pane-actions">
<button class="j2c-btn j2c-btn-secondary" onclick="j2cLoadSample()">Load Sample</button>
<button class="j2c-btn j2c-btn-secondary" onclick="j2cClear()">Clear</button>
</div>
<div class="j2c-msg" id="j2c-input-msg"></div>
</div>
<div class="j2c-pane">
<h2 id="j2c-output-label">CSV Output</h2>
<textarea id="j2c-output" readonly placeholder="Output will appear here after conversion…"></textarea>
<div class="j2c-pane-actions">
<button class="j2c-btn j2c-btn-primary" id="j2c-copy-btn" onclick="j2cCopy()" disabled>Copy</button>
<button class="j2c-btn j2c-btn-primary" id="j2c-download-btn" onclick="j2cDownload()" disabled>Download</button>
</div>
<div class="j2c-msg" id="j2c-output-msg"></div>
</div>
</div>

<div class="j2c-convert-row">
<button class="j2c-btn-convert" onclick="j2cConvert()">Convert ↓</button>
</div>

<div class="j2c-preview-section" id="j2c-preview-section" style="display:none;">
<h2>Preview</h2>
<div class="j2c-table-wrap">
<table id="j2c-preview-table"></table>
</div>
<div class="j2c-preview-meta" id="j2c-preview-meta"></div>
</div>

</div>

<script>
(function() {
var mode = 'j2c'; // 'j2c' or 'c2j'

window.j2cSetMode = function(m) {
mode = m;
document.getElementById('j2c-tab-j2c').classList.toggle('active', m === 'j2c');
document.getElementById('j2c-tab-c2j').classList.toggle('active', m === 'c2j');
document.getElementById('j2c-input-label').textContent  = m === 'j2c' ? 'JSON Input'  : 'CSV Input';
document.getElementById('j2c-output-label').textContent = m === 'j2c' ? 'CSV Output'  : 'JSON Output';
document.getElementById('j2c-input').placeholder =
m === 'j2c'
? 'Paste JSON here, e.g.\n[\n  {"name":"Alice","age":30},\n  {"name":"Bob","age":25}\n]'
: 'Paste CSV here, e.g.\nname,age\nAlice,30\nBob,25';
j2cClearOutput();
hidePreview();
};

// ── Flatten nested object ──────────────────────────────────────────────────
function flattenObj(obj, prefix) {
prefix = prefix || '';
var out = {};
for (var key in obj) {
if (!Object.prototype.hasOwnProperty.call(obj, key)) continue;
var full = prefix ? prefix + '.' + key : key;
var val  = obj[key];
if (val !== null && typeof val === 'object' && !Array.isArray(val)) {
var nested = flattenObj(val, full);
for (var nk in nested) out[nk] = nested[nk];
} else {
out[full] = Array.isArray(val) ? JSON.stringify(val) : val;
}
}
return out;
}

// ── Escape a CSV cell ──────────────────────────────────────────────────────
function csvCell(val, delim) {
if (val === null || val === undefined) return '';
var s = String(val);
if (s.indexOf(delim) !== -1 || s.indexOf('"') !== -1 || s.indexOf('\n') !== -1) {
return '"' + s.replace(/"/g, '""') + '"';
}
return s;
}

// ── JSON → CSV ─────────────────────────────────────────────────────────────
function jsonToCsv(jsonStr, delim, includeHeader, flatten) {
var data;
try { data = JSON.parse(jsonStr); } catch(e) { throw new Error('Invalid JSON: ' + e.message); }
if (!Array.isArray(data)) throw new Error('JSON must be an array of objects at the top level.');
if (data.length === 0) throw new Error('JSON array is empty.');

var rows = data.map(function(item) {
if (typeof item !== 'object' || item === null) throw new Error('Each array element must be an object.');
return flatten ? flattenObj(item) : item;
});

// Collect all keys preserving insertion order
var keySeen = {};
var keys = [];
rows.forEach(function(r) {
Object.keys(r).forEach(function(k) {
if (!keySeen[k]) { keySeen[k] = true; keys.push(k); }
});
});

var lines = [];
if (includeHeader) lines.push(keys.map(function(k) { return csvCell(k, delim); }).join(delim));
rows.forEach(function(r) {
lines.push(keys.map(function(k) { return csvCell(r[k], delim); }).join(delim));
});
return { csv: lines.join('\n'), keys: keys, rows: rows };
}

// ── CSV → JSON ─────────────────────────────────────────────────────────────
function csvToJson(csvStr, delim, hasHeader) {
var lines = csvStr.trim().split(/\r?\n/);
if (lines.length === 0) throw new Error('CSV is empty.');

function parseLine(line) {
var cells = [];
var cur = '';
var inQ = false;
for (var i = 0; i < line.length; i++) {
var ch = line[i];
if (inQ) {
if (ch === '"' && line[i+1] === '"') { cur += '"'; i++; }
else if (ch === '"') { inQ = false; }
else { cur += ch; }
} else {
if (ch === '"') { inQ = true; }
else if (ch === delim) { cells.push(cur); cur = ''; }
else { cur += ch; }
}
}
cells.push(cur);
return cells;
}

var keys, dataLines;
if (hasHeader) {
keys = parseLine(lines[0]);
dataLines = lines.slice(1);
} else {
var first = parseLine(lines[0]);
keys = first.map(function(_, i) { return 'col' + (i+1); });
dataLines = lines;
}

var rows = dataLines.filter(function(l) { return l.trim() !== ''; }).map(function(line) {
var cells = parseLine(line);
var obj = {};
keys.forEach(function(k, i) {
var v = cells[i] !== undefined ? cells[i] : '';
// coerce numbers and booleans
if (v === 'true') obj[k] = true;
else if (v === 'false') obj[k] = false;
else if (v !== '' && !isNaN(Number(v))) obj[k] = Number(v);
else obj[k] = v;
});
return obj;
});

return { json: JSON.stringify(rows, null, 2), keys: keys, rows: rows };
}

// ── Preview ────────────────────────────────────────────────────────────────
function renderPreview(keys, rows, total) {
var section = document.getElementById('j2c-preview-section');
var table   = document.getElementById('j2c-preview-table');
var meta    = document.getElementById('j2c-preview-meta');
section.style.display = '';

var preview = rows.slice(0, 50);
var thead = '<thead><tr>' + keys.map(function(k) { return '<th>' + esc(k) + '</th>'; }).join('') + '</tr></thead>';
var tbody = '<tbody>' + preview.map(function(r) {
return '<tr>' + keys.map(function(k) {
var v = r[k]; if (v === null || v === undefined) v = '';
return '<td title="' + esc(String(v)) + '">' + esc(String(v)) + '</td>';
}).join('') + '</tr>';
}).join('') + '</tbody>';
table.innerHTML = thead + tbody;

var shown = preview.length;
meta.textContent = shown + ' of ' + total + ' row(s) shown' + (total > 50 ? ' (first 50)' : '') + ' · ' + keys.length + ' column(s)';
}

function hidePreview() {
document.getElementById('j2c-preview-section').style.display = 'none';
}

function esc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

// ── UI helpers ─────────────────────────────────────────────────────────────
function showMsg(id, text, type) {
var el = document.getElementById(id);
el.textContent = text;
el.className = 'j2c-msg ' + type;
}
function clearMsg(id) {
var el = document.getElementById(id);
el.textContent = '';
el.className = 'j2c-msg';
}
function setOutput(val) {
var out = document.getElementById('j2c-output');
out.value = val;
var haVal = val && val.trim() !== '';
document.getElementById('j2c-copy-btn').disabled     = !haVal;
document.getElementById('j2c-download-btn').disabled = !haVal;
}
function j2cClearOutput() {
setOutput('');
clearMsg('j2c-input-msg');
clearMsg('j2c-output-msg');
}

window.j2cClear = function() {
document.getElementById('j2c-input').value = '';
j2cClearOutput();
hidePreview();
};

window.j2cLoadSample = function() {
if (mode === 'j2c') {
document.getElementById('j2c-input').value = JSON.stringify([
{ name: "Alice", age: 30, address: { city: "New York", zip: "10001" }, active: true },
{ name: "Bob",   age: 25, address: { city: "London",   zip: "EC1A"  }, active: false },
{ name: "Carol", age: 35, address: { city: "Tokyo",    zip: "100-0001" }, active: true }
], null, 2);
} else {
document.getElementById('j2c-input').value =
'name,age,city\nAlice,30,New York\nBob,25,London\nCarol,35,Tokyo';
}
j2cClearOutput();
hidePreview();
};

window.j2cConvert = function() {
clearMsg('j2c-input-msg');
clearMsg('j2c-output-msg');
var input  = document.getElementById('j2c-input').value.trim();
var delim  = document.getElementById('j2c-delim').value;
var header = document.getElementById('j2c-header').checked;
var flatten = document.getElementById('j2c-flatten').checked;

if (!input) {
showMsg('j2c-input-msg', 'Please paste some input first.', 'error');
document.getElementById('j2c-input').classList.add('j2c-error');
return;
}
document.getElementById('j2c-input').classList.remove('j2c-error');

try {
if (mode === 'j2c') {
var res = jsonToCsv(input, delim, header, flatten);
setOutput(res.csv);
renderPreview(res.keys, res.rows, res.rows.length);
showMsg('j2c-output-msg', 'Converted successfully — ' + res.rows.length + ' row(s), ' + res.keys.length + ' column(s).', 'success');
} else {
var res = csvToJson(input, delim, header);
setOutput(res.json);
renderPreview(res.keys, res.rows, res.rows.length);
showMsg('j2c-output-msg', 'Converted successfully — ' + res.rows.length + ' row(s), ' + res.keys.length + ' column(s).', 'success');
}
} catch(e) {
showMsg('j2c-input-msg', e.message, 'error');
document.getElementById('j2c-input').classList.add('j2c-error');
setOutput('');
hidePreview();
}
};

window.j2cCopy = function() {
var val = document.getElementById('j2c-output').value;
if (!val) return;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(val).then(function() {
showMsg('j2c-output-msg', 'Copied to clipboard!', 'success');
}).catch(function() { fallbackCopy(val); });
} else {
fallbackCopy(val);
}
};

function fallbackCopy(text) {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
try {
document.execCommand('copy');
showMsg('j2c-output-msg', 'Copied to clipboard!', 'success');
} catch(e) {
showMsg('j2c-output-msg', 'Copy failed — please select and copy manually.', 'error');
}
document.body.removeChild(ta);
}

window.j2cDownload = function() {
var val = document.getElementById('j2c-output').value;
if (!val) return;
var ext  = mode === 'j2c' ? 'csv' : 'json';
var mime = mode === 'j2c' ? 'text/csv' : 'application/json';
var blob = new Blob([val], { type: mime + ';charset=utf-8;' });
var url  = URL.createObjectURL(blob);
var a    = document.createElement('a');
a.href     = url;
a.download = 'converted.' + ext;
a.style.display = 'none';
document.body.appendChild(a);
a.click();
setTimeout(function() { URL.revokeObjectURL(url); document.body.removeChild(a); }, 500);
};

})();
</script>

---

## How to use

1. Choose the conversion direction — **JSON → CSV** or **CSV → JSON** — using the tabs.
2. Paste your data into the left panel (or click **Load Sample** to try it).
3. Pick a delimiter and toggle header / flatten options as needed.
4. Click **Convert**.
5. Use **Copy** or **Download** to grab the result.

## Nested JSON

When **Flatten nested JSON** is checked, nested objects are flattened using dot notation. For example:

```json
{ "address": { "city": "Tokyo", "zip": "100" } }
```

becomes columns `address.city` and `address.zip`. Arrays inside objects are serialised as JSON strings.

## Delimiter reference

| Name | Character | Common use |
|---|---|---|
| Comma | `,` | Standard CSV (Excel, Google Sheets) |
| Semicolon | `;` | European locales where comma is decimal separator |
| Tab | `⇥` | TSV files, paste-friendly |
| Pipe | `\|` | Log files, markdown-style tables |

---

Related: Format JSON → [JSON Formatter](/tools/json-formatter/)
