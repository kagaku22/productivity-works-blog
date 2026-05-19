---
title: "Text Diff Checker - Free Online Text Comparison Tool"
date: 2025-05-16
description: "Compare two texts and find differences instantly. Line-by-line and word-by-word diff highlighting. Free online text comparison tool."
categories: ["Free Tools"]
tags: ["diff checker", "text comparison", "compare text", "difference finder", "developer tool"]
slug: "text-diff"
aliases: ["/tools/diff-checker/", "/tools/text-diff-checker/"]
cover:
  image: "/images/covers/text-diff.png"
  alt: "Text Diff Checker"
ShowToc: false
---

<div id="diff-app">

<style>
#diff-app * {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#diff-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1e293b;
max-width: 100%;
}

#diff-app .da-section-title {
font-size: 1.05rem;
font-weight: 600;
color: #334155;
margin-bottom: 8px;
}

/* Input panels */
#diff-app .da-input-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-bottom: 16px;
}

@media (max-width: 640px) {
#diff-app .da-input-row {
grid-template-columns: 1fr;
}
}

#diff-app .da-panel {
display: flex;
flex-direction: column;
gap: 8px;
}

#diff-app .da-panel-label {
font-size: 0.875rem;
font-weight: 600;
color: #475569;
display: flex;
align-items: center;
gap: 6px;
}

#diff-app .da-panel-label .da-badge {
font-size: 0.7rem;
font-weight: 600;
padding: 2px 7px;
border-radius: 9999px;
letter-spacing: 0.03em;
}

#diff-app .da-badge-original {
background: #fee2e2;
color: #b91c1c;
}

#diff-app .da-badge-modified {
background: #dcfce7;
color: #15803d;
}

#diff-app textarea {
width: 100%;
height: 220px;
padding: 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-family: "Fira Mono", "Cascadia Code", "Consolas", monospace;
font-size: 0.85rem;
line-height: 1.6;
color: #1e293b;
background: #f8fafc;
resize: vertical;
transition: border-color 0.15s;
outline: none;
}

#diff-app textarea:focus {
border-color: #334155;
background: #fff;
}

/* Options row */
#diff-app .da-options-row {
display: flex;
flex-wrap: wrap;
align-items: center;
gap: 16px;
padding: 12px 16px;
background: #f1f5f9;
border-radius: 8px;
margin-bottom: 14px;
}

#diff-app .da-toggle-group {
display: flex;
align-items: center;
gap: 8px;
font-size: 0.875rem;
color: #475569;
cursor: pointer;
user-select: none;
}

#diff-app .da-toggle-group input[type="checkbox"] {
width: 16px;
height: 16px;
accent-color: #334155;
cursor: pointer;
}

/* Action buttons */
#diff-app .da-actions {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 20px;
}

#diff-app button {
cursor: pointer;
border: none;
border-radius: 7px;
font-size: 0.875rem;
font-weight: 600;
padding: 9px 18px;
transition: background 0.15s, transform 0.1s;
display: inline-flex;
align-items: center;
gap: 6px;
}

#diff-app button:active {
transform: scale(0.97);
}

#diff-app .da-btn-primary {
background: #334155;
color: #fff;
font-size: 0.95rem;
padding: 10px 24px;
}

#diff-app .da-btn-primary:hover {
background: #1e293b;
}

#diff-app .da-btn-secondary {
background: #e2e8f0;
color: #334155;
}

#diff-app .da-btn-secondary:hover {
background: #cbd5e1;
}

#diff-app .da-btn-success {
background: #f0fdf4;
color: #15803d;
border: 1.5px solid #bbf7d0;
}

#diff-app .da-btn-success:hover {
background: #dcfce7;
}

#diff-app .da-btn-danger {
background: #fff1f2;
color: #b91c1c;
border: 1.5px solid #fecdd3;
}

#diff-app .da-btn-danger:hover {
background: #ffe4e6;
}

/* Stats bar */
#diff-app .da-stats {
display: none;
flex-wrap: wrap;
gap: 12px;
padding: 12px 16px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
margin-bottom: 16px;
}

#diff-app .da-stats.da-visible {
display: flex;
}

#diff-app .da-stat-item {
display: flex;
align-items: center;
gap: 6px;
font-size: 0.875rem;
}

#diff-app .da-stat-dot {
width: 10px;
height: 10px;
border-radius: 50%;
flex-shrink: 0;
}

#diff-app .da-stat-dot-added   { background: #22c55e; }
#diff-app .da-stat-dot-removed { background: #ef4444; }
#diff-app .da-stat-dot-same    { background: #94a3b8; }
#diff-app .da-stat-dot-sim     { background: #334155; }

#diff-app .da-stat-value {
font-weight: 700;
color: #1e293b;
}

#diff-app .da-stat-sep {
color: #cbd5e1;
}

/* Diff output */
#diff-app .da-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 8px;
}

#diff-app .da-output-wrap {
display: none;
}

#diff-app .da-output-wrap.da-visible {
display: block;
}

#diff-app .da-diff-table {
width: 100%;
border-collapse: collapse;
font-family: "Fira Mono", "Cascadia Code", "Consolas", monospace;
font-size: 0.8rem;
line-height: 1.6;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
overflow: hidden;
}

#diff-app .da-diff-table td {
padding: 2px 10px;
vertical-align: top;
white-space: pre-wrap;
word-break: break-all;
}

#diff-app .da-line-num {
width: 38px;
min-width: 38px;
text-align: right;
color: #94a3b8;
font-size: 0.75rem;
padding-right: 12px;
user-select: none;
border-right: 1.5px solid #e2e8f0;
}

#diff-app .da-line-sym {
width: 22px;
min-width: 22px;
text-align: center;
font-weight: 700;
user-select: none;
padding: 2px 4px;
}

#diff-app .da-line-added {
background: #f0fdf4;
}

#diff-app .da-line-added .da-line-num,
#diff-app .da-line-added .da-line-sym {
background: #dcfce7;
color: #15803d;
}

#diff-app .da-line-removed {
background: #fff1f2;
}

#diff-app .da-line-removed .da-line-num,
#diff-app .da-line-removed .da-line-sym {
background: #ffe4e6;
color: #b91c1c;
}

#diff-app .da-line-same {
background: #fff;
}

#diff-app .da-line-same .da-line-num {
background: #f8fafc;
}

#diff-app .da-line-same .da-line-sym {
background: #f8fafc;
color: #94a3b8;
}

/* Word-level diff highlights */
#diff-app .da-word-added {
background: #86efac;
border-radius: 3px;
padding: 0 2px;
}

#diff-app .da-word-removed {
background: #fca5a5;
border-radius: 3px;
padding: 0 2px;
text-decoration: line-through;
}

/* Empty state */
#diff-app .da-empty {
text-align: center;
padding: 40px 20px;
color: #94a3b8;
font-size: 0.9rem;
border: 1.5px dashed #e2e8f0;
border-radius: 8px;
}

/* Copy feedback */
#diff-app .da-copy-feedback {
font-size: 0.75rem;
color: #15803d;
font-weight: 600;
opacity: 0;
transition: opacity 0.3s;
margin-left: 6px;
}

#diff-app .da-copy-feedback.da-show {
opacity: 1;
}
</style>

<!-- Input row -->
<div class="da-input-row">
<div class="da-panel">
<div class="da-panel-label">
Original Text
<span class="da-badge da-badge-original">A</span>
</div>
<textarea id="da-original" placeholder="Paste your original text here..."></textarea>
</div>
<div class="da-panel">
<div class="da-panel-label">
Modified Text
<span class="da-badge da-badge-modified">B</span>
</div>
<textarea id="da-modified" placeholder="Paste your modified text here..."></textarea>
</div>
</div>

<!-- Options -->
<div class="da-options-row">
<label class="da-toggle-group">
<input type="checkbox" id="da-opt-word"> Word-level diff
</label>
<label class="da-toggle-group">
<input type="checkbox" id="da-opt-whitespace"> Ignore whitespace
</label>
<label class="da-toggle-group">
<input type="checkbox" id="da-opt-case"> Ignore case
</label>
</div>

<!-- Actions -->
<div class="da-actions">
<button class="da-btn-primary" id="da-btn-compare">&#9654; Compare</button>
<button class="da-btn-secondary" id="da-btn-swap">&#8646; Swap</button>
<button class="da-btn-danger" id="da-btn-clear">&#10005; Clear Both</button>
<button class="da-btn-success" id="da-btn-copy">&#128203; Copy Diff</button>
<span class="da-copy-feedback" id="da-copy-feedback">Copied!</span>
</div>

<!-- Stats -->
<div class="da-stats" id="da-stats">
<div class="da-stat-item">
<span class="da-stat-dot da-stat-dot-added"></span>
<span>Added: <span class="da-stat-value" id="da-stat-added">0</span></span>
</div>
<span class="da-stat-sep">|</span>
<div class="da-stat-item">
<span class="da-stat-dot da-stat-dot-removed"></span>
<span>Removed: <span class="da-stat-value" id="da-stat-removed">0</span></span>
</div>
<span class="da-stat-sep">|</span>
<div class="da-stat-item">
<span class="da-stat-dot da-stat-dot-same"></span>
<span>Unchanged: <span class="da-stat-value" id="da-stat-same">0</span></span>
</div>
<span class="da-stat-sep">|</span>
<div class="da-stat-item">
<span class="da-stat-dot da-stat-dot-sim"></span>
<span>Similarity: <span class="da-stat-value" id="da-stat-sim">0%</span></span>
</div>
</div>

<!-- Output -->
<div class="da-output-wrap" id="da-output-wrap">
<div class="da-output-header">
<span class="da-section-title">Diff Result</span>
</div>
<table class="da-diff-table" id="da-diff-table"></table>
</div>

<div class="da-empty" id="da-empty">
Enter text in both panels above and click <strong>Compare</strong> to see differences.
</div>

<script>
(function() {
'use strict';

// ---- LCS-based line diff ----
function lcs(a, b) {
var m = a.length, n = b.length;
// Use Hunt-Szymanski or simple DP; for large inputs we cap at 500 lines each.
var maxLen = 500;
if (m > maxLen) a = a.slice(0, maxLen), m = maxLen;
if (n > maxLen) b = b.slice(0, maxLen), n = maxLen;

var dp = [];
for (var i = 0; i <= m; i++) {
dp[i] = new Array(n + 1).fill(0);
}
for (var i = 1; i <= m; i++) {
for (var j = 1; j <= n; j++) {
if (a[i-1] === b[j-1]) {
dp[i][j] = dp[i-1][j-1] + 1;
} else {
dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
}
}
}
// Backtrack
var result = [];
var i = m, j = n;
while (i > 0 && j > 0) {
if (a[i-1] === b[j-1]) {
result.unshift({ type: 'same', val: a[i-1] });
i--; j--;
} else if (dp[i-1][j] >= dp[i][j-1]) {
result.unshift({ type: 'removed', val: a[i-1] });
i--;
} else {
result.unshift({ type: 'added', val: b[j-1] });
j--;
}
}
while (i > 0) { result.unshift({ type: 'removed', val: a[i-1] }); i--; }
while (j > 0) { result.unshift({ type: 'added', val: b[j-1] }); j--; }
return result;
}

// ---- Word-level diff ----
function wordDiff(oldLine, newLine) {
var oldWords = tokenize(oldLine);
var newWords = tokenize(newLine);
var diff = lcs(oldWords, newWords);
var oldHtml = '', newHtml = '';
diff.forEach(function(d) {
var esc = escHtml(d.val);
if (d.type === 'same') {
oldHtml += esc;
newHtml += esc;
} else if (d.type === 'removed') {
oldHtml += '<span class="da-word-removed">' + esc + '</span>';
} else {
newHtml += '<span class="da-word-added">' + esc + '</span>';
}
});
return { oldHtml: oldHtml, newHtml: newHtml };
}

function tokenize(str) {
// Split into words and whitespace tokens
return str.match(/\S+|\s+/g) || [];
}

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function normalize(line, ignWs, ignCase) {
if (ignWs) line = line.replace(/\s+/g, ' ').trim();
if (ignCase) line = line.toLowerCase();
return line;
}

function getLines(text) {
return text.split('\n');
}

// ---- Render ----
function render() {
var origText = document.getElementById('da-original').value;
var modiText = document.getElementById('da-modified').value;
var wordMode = document.getElementById('da-opt-word').checked;
var ignWs   = document.getElementById('da-opt-whitespace').checked;
var ignCase = document.getElementById('da-opt-case').checked;

var origLines = getLines(origText);
var modiLines = getLines(modiText);

// Normalize for comparison keys only
var origKeys = origLines.map(function(l){ return normalize(l, ignWs, ignCase); });
var modiKeys = modiLines.map(function(l){ return normalize(l, ignWs, ignCase); });

var diff = lcs(origKeys, modiKeys);

// Re-map diff to original line content
var oIdx = 0, mIdx = 0;
var rows = diff.map(function(d) {
if (d.type === 'same') {
var row = { type: 'same', orig: origLines[oIdx], modi: modiLines[mIdx], oNum: oIdx+1, mNum: mIdx+1 };
oIdx++; mIdx++;
return row;
} else if (d.type === 'removed') {
var row = { type: 'removed', orig: origLines[oIdx], oNum: oIdx+1 };
oIdx++;
return row;
} else {
var row = { type: 'added', modi: modiLines[mIdx], mNum: mIdx+1 };
mIdx++;
return row;
}
});

// Stats
var added = 0, removed = 0, same = 0;
rows.forEach(function(r) {
if (r.type === 'added') added++;
else if (r.type === 'removed') removed++;
else same++;
});
var total = added + removed + same;
var sim = total === 0 ? 100 : Math.round((same / total) * 100);

document.getElementById('da-stat-added').textContent   = added;
document.getElementById('da-stat-removed').textContent = removed;
document.getElementById('da-stat-same').textContent    = same;
document.getElementById('da-stat-sim').textContent     = sim + '%';
document.getElementById('da-stats').classList.add('da-visible');

// Build table
var tableEl = document.getElementById('da-diff-table');
var html = '';

rows.forEach(function(r) {
if (r.type === 'removed') {
var content = wordMode
? '<td class="da-line-content">' + escHtml(r.orig) + '</td>'
: '<td class="da-line-content">' + escHtml(r.orig) + '</td>';
html += '<tr class="da-line-removed">'
+ '<td class="da-line-num">' + r.oNum + '</td>'
+ '<td class="da-line-sym">-</td>'
+ '<td class="da-line-content">' + escHtml(r.orig) + '</td>'
+ '</tr>';
} else if (r.type === 'added') {
html += '<tr class="da-line-added">'
+ '<td class="da-line-num">' + r.mNum + '</td>'
+ '<td class="da-line-sym">+</td>'
+ '<td class="da-line-content">' + escHtml(r.modi) + '</td>'
+ '</tr>';
} else {
// same — if word mode, we only highlight words if adjacent remove+add pairs exist; for 'same' lines no highlight needed
html += '<tr class="da-line-same">'
+ '<td class="da-line-num">' + r.oNum + '</td>'
+ '<td class="da-line-sym"> </td>'
+ '<td class="da-line-content">' + escHtml(r.orig) + '</td>'
+ '</tr>';
}
});

// Word-level: pair up adjacent removed+added and re-render
if (wordMode) {
// Re-parse rows into paired structure
html = '';
var i = 0;
while (i < rows.length) {
var r = rows[i];
if (r.type === 'removed' && i + 1 < rows.length && rows[i+1].type === 'added') {
// Pair: show word diff
var wd = wordDiff(r.orig, rows[i+1].modi);
html += '<tr class="da-line-removed">'
+ '<td class="da-line-num">' + r.oNum + '</td>'
+ '<td class="da-line-sym">-</td>'
+ '<td class="da-line-content">' + wd.oldHtml + '</td>'
+ '</tr>';
html += '<tr class="da-line-added">'
+ '<td class="da-line-num">' + rows[i+1].mNum + '</td>'
+ '<td class="da-line-sym">+</td>'
+ '<td class="da-line-content">' + wd.newHtml + '</td>'
+ '</tr>';
i += 2;
} else if (r.type === 'removed') {
html += '<tr class="da-line-removed">'
+ '<td class="da-line-num">' + r.oNum + '</td>'
+ '<td class="da-line-sym">-</td>'
+ '<td class="da-line-content">' + escHtml(r.orig) + '</td>'
+ '</tr>';
i++;
} else if (r.type === 'added') {
html += '<tr class="da-line-added">'
+ '<td class="da-line-num">' + r.mNum + '</td>'
+ '<td class="da-line-sym">+</td>'
+ '<td class="da-line-content">' + escHtml(r.modi) + '</td>'
+ '</tr>';
i++;
} else {
html += '<tr class="da-line-same">'
+ '<td class="da-line-num">' + r.oNum + '</td>'
+ '<td class="da-line-sym"> </td>'
+ '<td class="da-line-content">' + escHtml(r.orig) + '</td>'
+ '</tr>';
i++;
}
}
}

tableEl.innerHTML = html || '<tr><td colspan="3" style="padding:16px;text-align:center;color:#94a3b8;">No differences found. Texts are identical.</td></tr>';

document.getElementById('da-output-wrap').classList.add('da-visible');
document.getElementById('da-empty').style.display = 'none';
}

function copyDiff() {
var tableEl = document.getElementById('da-diff-table');
if (!tableEl) return;
var rows = tableEl.querySelectorAll('tr');
var lines = [];
rows.forEach(function(row) {
var cells = row.querySelectorAll('td');
if (cells.length >= 3) {
var sym = cells[1].textContent.trim() || ' ';
var content = cells[2].textContent;
lines.push(sym + ' ' + content);
}
});
var text = lines.join('\n');
if (!text) return;

var textarea = document.createElement('textarea');
textarea.value = text;
textarea.style.position = 'fixed';
textarea.style.opacity = '0';
document.body.appendChild(textarea);
textarea.select();
document.execCommand('copy');
document.body.removeChild(textarea);

var fb = document.getElementById('da-copy-feedback');
fb.classList.add('da-show');
setTimeout(function() { fb.classList.remove('da-show'); }, 2000);
}

// Wire up events
document.getElementById('da-btn-compare').addEventListener('click', render);

document.getElementById('da-btn-swap').addEventListener('click', function() {
var orig = document.getElementById('da-original');
var modi = document.getElementById('da-modified');
var tmp = orig.value;
orig.value = modi.value;
modi.value = tmp;
});

document.getElementById('da-btn-clear').addEventListener('click', function() {
document.getElementById('da-original').value = '';
document.getElementById('da-modified').value = '';
document.getElementById('da-output-wrap').classList.remove('da-visible');
document.getElementById('da-stats').classList.remove('da-visible');
document.getElementById('da-empty').style.display = '';
});

document.getElementById('da-btn-copy').addEventListener('click', copyDiff);

// Allow Ctrl+Enter to compare
[document.getElementById('da-original'), document.getElementById('da-modified')].forEach(function(el) {
el.addEventListener('keydown', function(e) {
if (e.ctrlKey && e.key === 'Enter') render();
});
});
})();
</script>

</div>

---

## How to Use the Text Diff Checker

1. **Paste your original text** into the left panel (labeled A).
2. **Paste your modified text** into the right panel (labeled B).
3. Click **Compare** (or press Ctrl+Enter) to generate the diff.
4. Review the results:
- Lines highlighted in **green** (with `+`) were added in the modified text.
- Lines highlighted in **red** (with `-`) were removed from the original.
- Lines with no highlight are unchanged.
5. Use the **statistics bar** to see a quick summary: lines added, removed, unchanged, and an overall similarity percentage.

**Options explained:**

- **Word-level diff** — instead of highlighting entire lines, individual changed words within paired lines are highlighted. Useful for spotting small edits.
- **Ignore whitespace** — treats lines that differ only in leading/trailing spaces or tab width as identical.
- **Ignore case** — `Hello` and `hello` are treated as the same for comparison purposes.
- **Swap** — flips original and modified panels so you can reverse the direction of comparison.
- **Copy Diff** — copies the plain-text diff output to your clipboard.

---

## Related Tools

> Format and validate JSON → [JSON Formatter](/tools/json-formatter/)

> Test regular expressions → [Regex Tester](/tools/regex-tester/)

> Count words and characters → [Word Counter](/tools/word-counter/)

> Need a markdown editor? → [Markdown Preview](/tools/markdown-preview/) — write and preview markdown live
