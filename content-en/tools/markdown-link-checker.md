---
title: "Markdown Link Checker — Extract & Validate Links"
date: 2025-05-16
description: "Extract and validate links from Markdown text. Find duplicates, broken formats, and categorize internal/external links. Export as CSV or JSON."
categories: ["Free Tools"]
slug: "markdown-link-checker"
ShowToc: false
cover:
  image: "/images/covers/markdown-link-checker.png"
  alt: "Markdown Link Checker"
---

Paste any Markdown text below to instantly extract every link, categorize it, detect broken formats, find duplicates, and export results as CSV or JSON.

<div id="mlc-app">

<style>
#mlc-app *,
#mlc-app *::before,
#mlc-app *::after {
box-sizing: border-box;
}

#mlc-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
font-size: 15px;
color: #1a1a2e;
max-width: 860px;
margin: 0 auto;
padding: 0;
}

#mlc-app h2.mlc-section-title {
font-size: 1.1rem;
font-weight: 700;
margin: 0 0 10px 0;
color: #0f3460;
letter-spacing: 0.02em;
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

/* Buttons row */
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
font-weight: 600;
cursor: pointer;
transition: background 0.18s, transform 0.1s;
white-space: nowrap;
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
font-weight: 600;
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
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#mlc-app button.mlc-filter-tab:hover,
#mlc-app button.mlc-filter-tab.active {
background: #4361ee;
color: #fff;
border-color: #4361ee;
}

/* Results table */
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

/* Toast / flash message */
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
font-weight: 600;
z-index: 9999;
box-shadow: 0 4px 16px rgba(0,0,0,0.25);
pointer-events: none;
}

/* Empty state */
#mlc-app .mlc-empty {
text-align: center;
padding: 40px 20px;
color: #9aa5c4;
font-size: 14px;
}

/* Action row below table */
#mlc-app .mlc-action-row {
display: none;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 18px;
}

/* Cross-link section */
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

/* Responsive */
@media (max-width: 600px) {
#mlc-app .mlc-btn-row { flex-direction: column; }
#mlc-app button.mlc-btn { width: 100%; justify-content: center; }
#mlc-app .mlc-action-row { flex-direction: column; }
#mlc-app .mlc-url-cell { max-width: 160px; }
}
</style>

<!-- Input -->
<div class="mlc-input-wrap">
<h2 class="mlc-section-title">Paste Markdown Text</h2>
<textarea id="mlc-input" placeholder="Paste your Markdown here...&#10;&#10;Example:&#10;[Google](https://google.com)&#10;![Logo](https://example.com/logo.png)&#10;[About](#about)&#10;[Internal Page](/blog/post)"></textarea>
<div class="mlc-btn-row">
<button class="mlc-btn" id="mlc-analyze-btn" onclick="mlcAnalyze()">Extract Links</button>
<button class="mlc-btn" id="mlc-clear-btn" onclick="mlcClear()">Clear</button>
</div>
</div>

<!-- Stats -->
<div class="mlc-stats-bar" id="mlc-stats-bar"></div>

<!-- Filter tabs -->
<div class="mlc-filter-row" id="mlc-filter-row"></div>

<!-- Table -->
<div class="mlc-results-wrap" id="mlc-results-wrap">
<table class="mlc-table" id="mlc-table">
<thead>
<tr>
<th>#</th>
<th>Link Text</th>
<th>URL</th>
<th>Type</th>
<th>Flags</th>
</tr>
</thead>
<tbody id="mlc-tbody"></tbody>
</table>
</div>

<!-- Action row -->
<div class="mlc-action-row" id="mlc-action-row">
<button class="mlc-btn mlc-btn-export" onclick="mlcExportCSV()">Export CSV</button>
<button class="mlc-btn mlc-btn-export" onclick="mlcExportJSON()">Export JSON</button>
<button class="mlc-btn" id="mlc-copy-urls-btn" onclick="mlcCopyAllURLs()">Copy All URLs</button>
</div>

<!-- Toast -->
<div class="mlc-toast" id="mlc-toast"></div>

<!-- Cross-links -->
<div class="mlc-crosslinks">
<p>Related tools:</p>
<a href="/tools/markdown-preview/">Markdown Preview</a>
<a href="/tools/markdown-table-generator/">Markdown Table Generator</a>
<a href="/tools/url-encoder/">URL Encoder</a>
</div>

<script>
(function () {
'use strict';

/* -----------------------------------------------
State
----------------------------------------------- */
var _allLinks = [];
var _activeFilter = 'all';

/* -----------------------------------------------
Main: Analyze
----------------------------------------------- */
window.mlcAnalyze = function () {
var raw = document.getElementById('mlc-input').value;
if (!raw.trim()) { mlcShowToast('Please paste some Markdown first.'); return; }
_allLinks = mlcExtractLinks(raw);
_activeFilter = 'all';
mlcRender();
};

/* -----------------------------------------------
Extraction
----------------------------------------------- */
function mlcExtractLinks(text) {
var links = [];
var seen = {};

// 1. Inline images: ![alt](url)
var imgRe = /!\[([^\]]*)\]\(([^)]*)\)/g;
var m;
while ((m = imgRe.exec(text)) !== null) {
links.push(mlcBuild(m[1], m[2].trim(), 'image', seen));
}

// 2. Standard inline links (not images): [text](url)
var linkRe = /(?<!!)\[([^\]]*)\]\(([^)]*)\)/g;
while ((m = linkRe.exec(text)) !== null) {
links.push(mlcBuild(m[1], m[2].trim(), null, seen));
}

// 3. Reference-style links: [text][id]  +  [id]: url
var refs = {};
var refDefRe = /^\[([^\]]+)\]:\s*(\S+)/gm;
while ((m = refDefRe.exec(text)) !== null) {
refs[m[1].toLowerCase()] = m[2].trim();
}
var refUsageRe = /(?<!!)\[([^\]]+)\]\[([^\]]*)\]/g;
while ((m = refUsageRe.exec(text)) !== null) {
var key = (m[2] || m[1]).toLowerCase();
var url = refs[key] || '[unresolved ref: ' + key + ']';
links.push(mlcBuild(m[1], url, null, seen));
}

// 4. Auto-links: <https://...>
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
// bare domain or unknown — treat as external
return 'external';
}

function mlcIsBroken(url) {
if (!url) return true;
// spaces inside URL (outside of angle-bracket auto-links)
if (/\s/.test(url)) return true;
// starts with www. but no protocol
if (/^www\./i.test(url)) return true;
// looks like a URL (has a dot + tld pattern) but missing protocol
if (/^[a-zA-Z0-9-]+\.[a-zA-Z]{2,}(\/|$)/.test(url) &&
!/^https?:\/\//i.test(url) &&
!url.startsWith('/') &&
!url.startsWith('#') &&
!url.startsWith('mailto:')) return true;
return false;
}

/* -----------------------------------------------
Render
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
var counts = mlcCounts(_allLinks);
bar.innerHTML = [
chip('chip-total',  'Total: ' + counts.total),
chip('chip-ext',    'External: ' + counts.external),
chip('chip-int',    'Internal: ' + counts.internal),
chip('chip-img',    'Images: ' + counts.image),
chip('chip-anchor', 'Anchors: ' + counts.anchor),
counts.dup    ? chip('chip-dup',    'Duplicates: ' + counts.dup) : '',
counts.broken ? chip('chip-broken', 'Broken format: ' + counts.broken) : '',
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
var counts = mlcCounts(_allLinks);
var filters = [
{ key: 'all',      label: 'All (' + counts.total + ')' },
{ key: 'external', label: 'External (' + counts.external + ')' },
{ key: 'internal', label: 'Internal (' + counts.internal + ')' },
{ key: 'image',    label: 'Images (' + counts.image + ')' },
{ key: 'anchor',   label: 'Anchors (' + counts.anchor + ')' },
{ key: 'dup',      label: 'Duplicates (' + counts.dup + ')' },
{ key: 'broken',   label: 'Broken (' + counts.broken + ')' },
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

var visible = _allLinks.filter(function (l, i) {
if (_activeFilter === 'all')      return true;
if (_activeFilter === 'dup')      return l.dup;
if (_activeFilter === 'broken')   return l.broken;
return l.type === _activeFilter;
});

if (!visible.length) {
tbody.innerHTML = '<tr><td colspan="5" class="mlc-empty">No links match this filter.</td></tr>';
return;
}

tbody.innerHTML = visible.map(function (l, i) {
var typeBadge = '<span class="mlc-badge badge-' + l.type + '">' + mlcEsc(l.type) + '</span>';
var flags = '';
if (l.dup)    flags += '<span class="mlc-badge badge-dup">dup</span>';
if (l.broken) flags += '<span class="mlc-badge badge-broken">broken format</span>';
var urlDisplay = mlcIsSafeURL(l.url)
? '<a href="' + mlcEscAttr(l.url) + '" target="_blank" rel="noopener noreferrer">' + mlcEsc(l.url) + '</a>'
: mlcEsc(l.url);
return '<tr>' +
'<td>' + (i + 1) + '</td>' +
'<td>' + mlcEsc(l.text || '(no text)') + '</td>' +
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
Export
----------------------------------------------- */
window.mlcExportCSV = function () {
if (!_allLinks.length) { mlcShowToast('No links to export.'); return; }
var rows = [['#', 'Text', 'URL', 'Type', 'Duplicate', 'Broken Format']];
_allLinks.forEach(function (l, i) {
rows.push([i + 1, l.text, l.url, l.type, l.dup ? 'yes' : 'no', l.broken ? 'yes' : 'no']);
});
var csv = rows.map(function (r) {
return r.map(function (c) { return '"' + String(c).replace(/"/g, '""') + '"'; }).join(',');
}).join('\r\n');
mlcDownload('markdown-links.csv', csv, 'text/csv;charset=utf-8;');
mlcShowToast('CSV downloaded.');
};

window.mlcExportJSON = function () {
if (!_allLinks.length) { mlcShowToast('No links to export.'); return; }
var data = _allLinks.map(function (l, i) {
return { index: i + 1, text: l.text, url: l.url, type: l.type, duplicate: l.dup, brokenFormat: l.broken };
});
mlcDownload('markdown-links.json', JSON.stringify(data, null, 2), 'application/json');
mlcShowToast('JSON downloaded.');
};

window.mlcCopyAllURLs = function () {
if (!_allLinks.length) { mlcShowToast('No links to copy.'); return; }
var urls = _allLinks.map(function (l) { return l.url; }).join('\n');
navigator.clipboard.writeText(urls).then(function () {
mlcShowToast('All URLs copied to clipboard!');
}, function () {
mlcShowToast('Copy failed — try selecting manually.');
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
Clear
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
Toast
----------------------------------------------- */
window.mlcShowToast = function (msg) {
var t = document.getElementById('mlc-toast');
t.textContent = msg;
t.style.display = 'block';
clearTimeout(t._timer);
t._timer = setTimeout(function () { t.style.display = 'none'; }, 2400);
};

/* -----------------------------------------------
Helpers
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
Keyboard shortcut: Ctrl/Cmd + Enter to analyze
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

## How to Use

1. Paste any Markdown text into the box above.
2. Click **Extract Links** (or press Ctrl+Enter / Cmd+Enter).
3. Use the filter tabs to view specific link categories.
4. Export the full list as **CSV** or **JSON**, or **Copy All URLs** to clipboard.

## What Gets Extracted

| Link type | Markdown syntax | Example |
|---|---|---|
| External link | `[text](https://...)` | `[Google](https://google.com)` |
| Internal link | `[text](/path)` | `[About](/about)` |
| Anchor | `[text](#id)` | `[Top](#top)` |
| Image | `![alt](url)` | `![Logo](logo.png)` |
| Reference link | `[text][ref]` | `[Docs][docs]` |
| Auto-link | `<https://...>` | `<https://example.com>` |

## Broken Format Detection

The checker flags links that have:

- **Missing protocol** — URLs starting with `www.` instead of `https://`
- **Spaces in URL** — Whitespace inside a URL that will cause rendering failures
- **Bare domains** — Domain-like strings with no `https://` prefix

## Related Tools

- [Markdown Preview](/tools/markdown-preview/) — Render Markdown as HTML in real time
- [Markdown Table Generator](/tools/markdown-table-generator/) — Build Markdown tables visually
- [URL Encoder](/tools/url-encoder/) — Encode and decode URLs and query strings
