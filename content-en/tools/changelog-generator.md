---
title: "Changelog Generator — Release Notes Tool"
date: 2025-05-16
description: "Generate changelogs and release notes in Keep a Changelog format. Add entries by category, preview in markdown, and copy or download. Free, no sign-up."
categories: ["Free Tools"]
tags: ["Developer Tools", "Documentation", "Free Tools"]
slug: "changelog-generator"
ShowToc: false
aliases:
  - "/tools/changelog-generator/"
  - "/tools/changelog-generator/"
cover:
  image: "/images/covers/changelog-generator.png"
  alt: "Changelog Generator"
---

Generate professional changelogs in [Keep a Changelog](https://keepachangelog.com/) format. Add version info, categorize your changes, preview the output, and copy or download — no account needed.

<div id="cl-app">
<style>
#cl-app *,
#cl-app *::before,
#cl-app *::after {
box-sizing: border-box;
}
#cl-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
margin: 0 auto;
max-width: 900px;
}
#cl-app h2 {
font-size: 1.1rem;
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
font-size: 0.82rem;
font-weight: 600;
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
margin-bottom: 0;
}
#cl-app .cl-preset-btn {
padding: 6px 14px;
border-radius: 20px;
border: 1.5px solid #667eea;
background: #fff;
color: #667eea;
font-size: 0.83rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
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
letter-spacing: 0.03em;
text-transform: uppercase;
}
#cl-app .cl-cat-added    .cl-cat-badge { background: #c6f6d5; color: #22543d; }
#cl-app .cl-cat-changed  .cl-cat-badge { background: #bee3f8; color: #2a4365; }
#cl-app .cl-cat-deprecated .cl-cat-badge { background: #fefcbf; color: #744210; }
#cl-app .cl-cat-removed  .cl-cat-badge { background: #fed7d7; color: #742a2a; }
#cl-app .cl-cat-fixed    .cl-cat-badge { background: #e9d8fd; color: #44337a; }
#cl-app .cl-cat-security .cl-cat-badge { background: #feebc8; color: #7b341e; }
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
font-weight: 600;
color: #718096;
cursor: pointer;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
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
tab-size: 2;
}
#cl-app .cl-preview-box.html-mode {
background: #fff;
color: #1a1a2e;
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 0.95rem;
border: 1px solid #e2e8f0;
line-height: 1.7;
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
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
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
font-weight: 600;
z-index: 9999;
box-shadow: 0 4px 16px rgba(0,0,0,0.18);
animation: cl-fadein 0.2s ease;
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
@media (max-width: 600px) {
#cl-app .cl-row { flex-direction: column; }
#cl-app .cl-tab { padding: 8px 12px; font-size: 0.82rem; }
#cl-app .cl-action-row { flex-direction: column; }
#cl-app .cl-btn { width: 100%; text-align: center; }
}
</style>

<!-- PRESETS -->
<div class="cl-section">
<div class="cl-section-title">Quick Presets</div>
<div class="cl-presets">
<button class="cl-preset-btn" onclick="clApplyPreset('major')">Major Release</button>
<button class="cl-preset-btn" onclick="clApplyPreset('minor')">Minor Update</button>
<button class="cl-preset-btn" onclick="clApplyPreset('patch')">Patch / Bugfix</button>
<button class="cl-preset-btn" onclick="clApplyPreset('security')">Security Update</button>
<button class="cl-preset-btn" onclick="clApplyPreset('clear')">Clear All</button>
</div>
</div>

<!-- RELEASE INFO -->
<div class="cl-section">
<h2>Release Info</h2>
<div class="cl-row">
<div class="cl-field">
<label for="cl-version">Version Number</label>
<input type="text" id="cl-version" placeholder="e.g. 2.1.0" />
</div>
<div class="cl-field">
<label for="cl-date">Release Date</label>
<input type="date" id="cl-date" />
</div>
<div class="cl-field">
<label for="cl-project">Project Name (optional)</label>
<input type="text" id="cl-project" placeholder="e.g. My App" />
</div>
</div>
</div>

<!-- CATEGORIES -->
<div class="cl-section">
<h2>Change Entries</h2>

<div class="cl-category cl-cat-added" id="cl-cat-added">
<div class="cl-cat-header" onclick="clToggleCat('added')">
<span class="cl-cat-badge">Added</span>
<span class="cl-cat-count" id="cl-count-added">0</span>
<span class="cl-cat-toggle" id="cl-toggle-added">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-added">
<div id="cl-entries-added"></div>
<button class="cl-add-btn" onclick="clAddEntry('added')">+ Add entry</button>
</div>
</div>

<div class="cl-category cl-cat-changed" id="cl-cat-changed">
<div class="cl-cat-header" onclick="clToggleCat('changed')">
<span class="cl-cat-badge">Changed</span>
<span class="cl-cat-count" id="cl-count-changed">0</span>
<span class="cl-cat-toggle" id="cl-toggle-changed">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-changed">
<div id="cl-entries-changed"></div>
<button class="cl-add-btn" onclick="clAddEntry('changed')">+ Add entry</button>
</div>
</div>

<div class="cl-category cl-cat-deprecated" id="cl-cat-deprecated">
<div class="cl-cat-header" onclick="clToggleCat('deprecated')">
<span class="cl-cat-badge">Deprecated</span>
<span class="cl-cat-count" id="cl-count-deprecated">0</span>
<span class="cl-cat-toggle" id="cl-toggle-deprecated">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-deprecated">
<div id="cl-entries-deprecated"></div>
<button class="cl-add-btn" onclick="clAddEntry('deprecated')">+ Add entry</button>
</div>
</div>

<div class="cl-category cl-cat-removed" id="cl-cat-removed">
<div class="cl-cat-header" onclick="clToggleCat('removed')">
<span class="cl-cat-badge">Removed</span>
<span class="cl-cat-count" id="cl-count-removed">0</span>
<span class="cl-cat-toggle" id="cl-toggle-removed">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-removed">
<div id="cl-entries-removed"></div>
<button class="cl-add-btn" onclick="clAddEntry('removed')">+ Add entry</button>
</div>
</div>

<div class="cl-category cl-cat-fixed" id="cl-cat-fixed">
<div class="cl-cat-header" onclick="clToggleCat('fixed')">
<span class="cl-cat-badge">Fixed</span>
<span class="cl-cat-count" id="cl-count-fixed">0</span>
<span class="cl-cat-toggle" id="cl-toggle-fixed">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-fixed">
<div id="cl-entries-fixed"></div>
<button class="cl-add-btn" onclick="clAddEntry('fixed')">+ Add entry</button>
</div>
</div>

<div class="cl-category cl-cat-security" id="cl-cat-security">
<div class="cl-cat-header" onclick="clToggleCat('security')">
<span class="cl-cat-badge">Security</span>
<span class="cl-cat-count" id="cl-count-security">0</span>
<span class="cl-cat-toggle" id="cl-toggle-security">&#9660;</span>
</div>
<div class="cl-cat-body" id="cl-body-security">
<div id="cl-entries-security"></div>
<button class="cl-add-btn" onclick="clAddEntry('security')">+ Add entry</button>
</div>
</div>
</div>

<!-- APPEND EXISTING -->
<div class="cl-section">
<h2>Append to Existing Changelog</h2>
<p class="cl-info">Paste your existing changelog below. The new release will be prepended above it.</p>
<textarea class="cl-append-area" id="cl-existing" placeholder="# Changelog&#10;&#10;## [1.0.0] - 2025-01-01&#10;..."></textarea>
</div>

<!-- OUTPUT FORMAT + PREVIEW -->
<div class="cl-section">
<h2>Preview &amp; Output</h2>
<div class="cl-format-tabs">
<button class="cl-tab active" id="cl-tab-md"   onclick="clSetFormat('md')">Markdown</button>
<button class="cl-tab"        id="cl-tab-html" onclick="clSetFormat('html')">HTML</button>
<button class="cl-tab"        id="cl-tab-txt"  onclick="clSetFormat('txt')">Plain Text</button>
</div>
<div class="cl-preview-box" id="cl-preview" aria-live="polite"></div>
<div class="cl-action-row">
<button class="cl-btn cl-btn-primary" onclick="clCopy()">Copy to Clipboard</button>
<button class="cl-btn cl-btn-secondary" onclick="clDownload()">Download File</button>
<button class="cl-btn cl-btn-danger" onclick="clReset()">Reset All</button>
</div>
</div>

<div class="cl-toast" id="cl-toast"></div>

<script>
(function () {
var CL = {
format: 'md',
collapsed: {},
counters: { added: 0, changed: 0, deprecated: 0, removed: 0, fixed: 0, security: 0 },
cats: ['added', 'changed', 'deprecated', 'removed', 'fixed', 'security']
};

/* ---- helpers ---- */
function $(id) { return document.getElementById(id); }

function clShowToast(msg) {
var t = $('cl-toast');
t.textContent = msg;
t.style.display = 'block';
setTimeout(function () { t.style.display = 'none'; }, 2000);
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

/* ---- toggle collapse ---- */
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

/* ---- add entry ---- */
window.clAddEntry = function (cat, value) {
var container = $('cl-entries-' + cat);
var row = document.createElement('div');
row.className = 'cl-entry-row';
var inp = document.createElement('input');
inp.type = 'text';
inp.className = 'cl-entry-input';
inp.placeholder = 'Describe the change…';
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

/* ---- format tabs ---- */
window.clSetFormat = function (fmt) {
CL.format = fmt;
CL.cats.forEach(function (c) {});
['md','html','txt'].forEach(function (f) {
$('cl-tab-' + f).classList.toggle('active', f === fmt);
});
clUpdatePreview();
};

/* ---- build output ---- */
function clBuildMd() {
var version = $('cl-version').value.trim() || 'X.Y.Z';
var date    = $('cl-date').value    || clTodayISO();
var project = $('cl-project').value.trim();
var lines   = [];

if (project) lines.push('# ' + project + ' Changelog\n');

lines.push('## [' + version + '] - ' + date);

CL.cats.forEach(function (cat) {
var entries = clGetEntries(cat);
if (entries.length) {
lines.push('\n### ' + cat.charAt(0).toUpperCase() + cat.slice(1));
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

if (project) html.push('<h1>' + clEsc(project) + ' Changelog</h1>');
html.push('<h2>[' + clEsc(version) + '] &mdash; ' + clEsc(date) + '</h2>');

CL.cats.forEach(function (cat) {
var entries = clGetEntries(cat);
if (entries.length) {
html.push('<h3>' + cat.charAt(0).toUpperCase() + cat.slice(1) + '</h3>');
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

if (project) { lines.push(bar); lines.push(project + ' CHANGELOG'); lines.push(bar); lines.push(''); }
lines.push('Release: v' + version + '  |  Date: ' + date);
lines.push(dash);

CL.cats.forEach(function (cat) {
var entries = clGetEntries(cat);
if (entries.length) {
lines.push('');
lines.push('[' + cat.toUpperCase() + ']');
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

/* ---- preview ---- */
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

/* ---- copy ---- */
window.clCopy = function () {
var text = CL.format === 'html' ? clBuildHtml() : (CL.format === 'md' ? clBuildMd() : clBuildTxt());
navigator.clipboard.writeText(text).then(function () {
clShowToast('Copied to clipboard!');
}).catch(function () {
clShowToast('Copy failed — try selecting text manually.');
});
};

/* ---- download ---- */
window.clDownload = function () {
var ext  = CL.format === 'html' ? 'html' : (CL.format === 'md' ? 'md' : 'txt');
var mime = CL.format === 'html' ? 'text/html' : 'text/plain';
var text = CL.format === 'html' ? clBuildHtml() : (CL.format === 'md' ? clBuildMd() : clBuildTxt());
var version = ($('cl-version').value.trim() || 'changelog').replace(/\s+/g,'-');
var blob = new Blob([text], {type: mime});
var a = document.createElement('a');
a.href = URL.createObjectURL(blob);
a.download = 'CHANGELOG-' + version + '.' + ext;
a.click();
URL.revokeObjectURL(a.href);
clShowToast('File downloaded!');
};

/* ---- reset ---- */
window.clReset = function () {
if (!confirm('Reset everything?')) return;
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

/* ---- presets ---- */
window.clApplyPreset = function (preset) {
CL.cats.forEach(function (cat) {
$('cl-entries-' + cat).innerHTML = '';
clUpdateCount(cat);
});

var today = clTodayISO();
$('cl-date').value = today;

if (preset === 'clear') {
$('cl-version').value = '';
$('cl-project').value = '';
$('cl-existing').value = '';
clUpdatePreview();
return;
}

if (preset === 'major') {
$('cl-version').value = '2.0.0';
clAddEntry('added',   'Completely redesigned user interface');
clAddEntry('added',   'New API v2 with improved performance');
clAddEntry('added',   'Dark mode support');
clAddEntry('changed', 'Migrated to new authentication system');
clAddEntry('changed', 'Database schema updated for scalability');
clAddEntry('removed', 'Deprecated v1 API endpoints');
clAddEntry('fixed',   'Critical performance issues under high load');
} else if (preset === 'minor') {
$('cl-version').value = '1.3.0';
clAddEntry('added',   'Export to CSV feature');
clAddEntry('added',   'Keyboard shortcuts for common actions');
clAddEntry('changed', 'Improved error messages for failed requests');
clAddEntry('deprecated', 'Legacy import format (will be removed in v2.0)');
clAddEntry('fixed',   'Pagination not working on search results');
} else if (preset === 'patch') {
$('cl-version').value = '1.2.1';
clAddEntry('fixed', 'Crash when opening settings on iOS 17');
clAddEntry('fixed', 'Incorrect total displayed in summary view');
clAddEntry('fixed', 'Login loop after session timeout');
} else if (preset === 'security') {
$('cl-version').value = '1.2.2';
clAddEntry('security', 'Patched XSS vulnerability in comment field (CVE-2025-XXXX)');
clAddEntry('security', 'Updated dependencies to address known vulnerabilities');
clAddEntry('fixed',    'Input validation bypassed in edge case');
}

clUpdatePreview();
};

/* ---- init ---- */
$('cl-date').value = clTodayISO();
['cl-version','cl-date','cl-project','cl-existing'].forEach(function (id) {
$(id).addEventListener('input', clUpdatePreview);
});
clUpdatePreview();
})();
</script>
</div>

---

### Related Tools

> Preview markdown → [Markdown Preview](/tools/markdown-preview/)
> Generate markdown tables → [Markdown Table Generator](/tools/markdown-table-generator/)
> Format JSON → [JSON Formatter](/tools/json-formatter/)
