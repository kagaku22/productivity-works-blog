---
title: "Text Diff Checker"
date: 2025-05-16
description: "Free online text diff checker. Compare two texts side by side and highlight additions, deletions, and changes — no sign-up, works entirely in your browser."
categories: ["Free Tools"]
slug: "text-diff-checker"
ShowToc: false
cover:
  image: "/images/covers/text-diff-checker.png"
  alt: "Text Diff Checker"
---

Compare two texts instantly and see exactly what changed — line by line, color-coded, with summary stats. No server, no sign-up, no tracking. Everything runs in your browser.

<div id="df-app">
<style>
#df-app *,
#df-app *::before,
#df-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#df-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 14px;
color: #1e293b;
line-height: 1.5;
}
#df-app .df-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 14px;
}
#df-app .df-toolbar-group {
display: flex;
gap: 6px;
align-items: center;
}
#df-app .df-toolbar-sep {
width: 1px;
height: 26px;
background: #cbd5e1;
margin: 0 2px;
}
#df-app label.df-check {
display: flex;
align-items: center;
gap: 5px;
font-size: 13px;
color: #475569;
cursor: pointer;
user-select: none;
}
#df-app label.df-check input[type="checkbox"] {
width: 15px;
height: 15px;
accent-color: #6366f1;
cursor: pointer;
}
#df-app .df-btn {
padding: 6px 14px;
border-radius: 6px;
border: 1.5px solid #cbd5e1;
background: #f8fafc;
color: #334155;
font-size: 13px;
font-weight: 500;
cursor: pointer;
transition: background 0.15s, border-color 0.15s, color 0.15s;
white-space: nowrap;
}
#df-app .df-btn:hover {
background: #f1f5f9;
border-color: #94a3b8;
}
#df-app .df-btn-primary {
background: #6366f1;
border-color: #6366f1;
color: #fff;
font-weight: 600;
}
#df-app .df-btn-primary:hover {
background: #4f46e5;
border-color: #4f46e5;
}
#df-app .df-btn-danger {
background: #fff;
border-color: #fca5a5;
color: #dc2626;
}
#df-app .df-btn-danger:hover {
background: #fef2f2;
border-color: #f87171;
}
#df-app .df-view-toggle {
display: flex;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
overflow: hidden;
}
#df-app .df-view-toggle button {
padding: 5px 12px;
border: none;
background: #f8fafc;
color: #64748b;
font-size: 12px;
font-weight: 500;
cursor: pointer;
transition: background 0.15s, color 0.15s;
border-right: 1px solid #cbd5e1;
}
#df-app .df-view-toggle button:last-child {
border-right: none;
}
#df-app .df-view-toggle button.active {
background: #6366f1;
color: #fff;
}
#df-app .df-inputs {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
margin-bottom: 14px;
}
@media (max-width: 640px) {
#df-app .df-inputs {
grid-template-columns: 1fr;
}
}
#df-app .df-input-block {
display: flex;
flex-direction: column;
gap: 6px;
}
#df-app .df-input-label {
font-size: 12px;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#df-app textarea.df-ta {
width: 100%;
height: 200px;
padding: 10px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.6;
color: #1e293b;
background: #f8fafc;
resize: vertical;
outline: none;
transition: border-color 0.15s;
}
#df-app textarea.df-ta:focus {
border-color: #6366f1;
background: #fff;
}
#df-app .df-stats {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 14px;
padding: 12px 16px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
}
#df-app .df-stat {
display: flex;
align-items: center;
gap: 6px;
font-size: 13px;
color: #475569;
}
#df-app .df-stat-badge {
display: inline-block;
padding: 2px 8px;
border-radius: 999px;
font-size: 12px;
font-weight: 700;
min-width: 28px;
text-align: center;
}
#df-app .df-stat-added .df-stat-badge  { background: #dcfce7; color: #15803d; }
#df-app .df-stat-removed .df-stat-badge { background: #fee2e2; color: #b91c1c; }
#df-app .df-stat-changed .df-stat-badge { background: #fef9c3; color: #a16207; }
#df-app .df-stat-unchanged .df-stat-badge { background: #f1f5f9; color: #475569; }
#df-app .df-result-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 8px;
}
#df-app .df-result-title {
font-size: 12px;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#df-app .df-result-wrap {
border: 1.5px solid #e2e8f0;
border-radius: 8px;
overflow: hidden;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.6;
}
/* Side-by-side */
#df-app .df-side {
display: grid;
grid-template-columns: 1fr 1fr;
min-height: 60px;
}
#df-app .df-side-col {
overflow-x: auto;
}
#df-app .df-side-col:first-child {
border-right: 1.5px solid #e2e8f0;
}
#df-app .df-side-col-header {
padding: 6px 10px;
font-size: 11px;
font-weight: 600;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.07em;
background: #f1f5f9;
border-bottom: 1px solid #e2e8f0;
}
#df-app .df-line {
display: flex;
align-items: stretch;
min-height: 22px;
}
#df-app .df-line-num {
min-width: 38px;
padding: 1px 8px;
text-align: right;
color: #94a3b8;
user-select: none;
border-right: 1px solid #e2e8f0;
background: #f8fafc;
font-size: 12px;
flex-shrink: 0;
}
#df-app .df-line-content {
padding: 1px 10px;
white-space: pre;
flex: 1;
min-width: 0;
}
#df-app .df-line.added    { background: #f0fdf4; }
#df-app .df-line.removed  { background: #fef2f2; }
#df-app .df-line.changed  { background: #fefce8; }
#df-app .df-line.empty    { background: #fafafa; }
#df-app .df-line-num.added   { background: #dcfce7; color: #15803d; }
#df-app .df-line-num.removed { background: #fee2e2; color: #b91c1c; }
#df-app .df-line-num.changed { background: #fef9c3; color: #a16207; }
#df-app .df-line-mark {
min-width: 18px;
text-align: center;
flex-shrink: 0;
font-weight: 700;
padding: 1px 2px;
font-size: 13px;
}
#df-app .added  .df-line-mark { color: #16a34a; }
#df-app .removed .df-line-mark { color: #dc2626; }
#df-app .changed .df-line-mark { color: #ca8a04; }
/* Unified */
#df-app .df-unified {
min-height: 60px;
}
#df-app .df-unified .df-line-num {
min-width: 60px;
}
#df-app .df-empty-state {
padding: 40px 20px;
text-align: center;
color: #94a3b8;
font-size: 14px;
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}
#df-app .df-copy-toast {
display: none;
position: fixed;
bottom: 24px;
right: 24px;
background: #1e293b;
color: #fff;
padding: 10px 18px;
border-radius: 8px;
font-size: 13px;
font-weight: 500;
z-index: 9999;
box-shadow: 0 4px 16px rgba(0,0,0,0.18);
pointer-events: none;
}
#df-app .df-copy-toast.show { display: block; }
/* char-level highlight within a changed line */
#df-app .df-char-add  { background: #bbf7d0; border-radius: 2px; }
#df-app .df-char-del  { background: #fecaca; border-radius: 2px; text-decoration: line-through; }
</style>

<!-- Toolbar -->
<div class="df-toolbar">
<div class="df-toolbar-group">
<button class="df-btn df-btn-primary" id="df-run">Compare</button>
<button class="df-btn" id="df-swap">⇄ Swap</button>
<button class="df-btn df-btn-danger" id="df-clear">Clear</button>
</div>
<div class="df-toolbar-sep"></div>
<div class="df-toolbar-group">
<label class="df-check"><input type="checkbox" id="df-ignore-ws"> Ignore whitespace</label>
<label class="df-check"><input type="checkbox" id="df-ignore-case"> Case-insensitive</label>
</div>
<div class="df-toolbar-sep"></div>
<div class="df-view-toggle">
<button id="df-view-side" class="active">Side by Side</button>
<button id="df-view-unified">Unified</button>
</div>
<div class="df-toolbar-sep"></div>
<button class="df-btn" id="df-copy">Copy Result</button>
</div>

<!-- Inputs -->
<div class="df-inputs">
<div class="df-input-block">
<div class="df-input-label">Original</div>
<textarea class="df-ta" id="df-orig" placeholder="Paste original text here..."></textarea>
</div>
<div class="df-input-block">
<div class="df-input-label">Modified</div>
<textarea class="df-ta" id="df-mod" placeholder="Paste modified text here..."></textarea>
</div>
</div>

<!-- Stats -->
<div class="df-stats" id="df-stats" style="display:none;">
<div class="df-stat df-stat-added"><span class="df-stat-badge" id="df-s-add">0</span> Added</div>
<div class="df-stat df-stat-removed"><span class="df-stat-badge" id="df-s-rem">0</span> Removed</div>
<div class="df-stat df-stat-changed"><span class="df-stat-badge" id="df-s-chg">0</span> Changed</div>
<div class="df-stat df-stat-unchanged"><span class="df-stat-badge" id="df-s-unc">0</span> Unchanged</div>
</div>

<!-- Result -->
<div class="df-result-header">
<div class="df-result-title">Diff Result</div>
</div>
<div class="df-result-wrap" id="df-result">
<div class="df-empty-state">Enter text above and click <strong>Compare</strong> to see the diff.</div>
</div>

<div class="df-copy-toast" id="df-toast">Copied to clipboard!</div>

<script>
(function() {
'use strict';

// ── LCS-based line diff ──────────────────────────────────────────
function lcs(a, b) {
const m = a.length, n = b.length;
// Use Hunt-Szymanski / Myers O(ND) approximation for large inputs
// For simplicity and correctness we use the standard DP with space optimization
if (m === 0 || n === 0) return [];
// Build DP table row by row (only keep two rows)
const dp = new Array(n + 1).fill(0);
const prev = new Array(n + 1).fill(0);
const bt = [];  // backtrack: store full table only up to 400x400, else greedy
if (m * n <= 160000) {
const table = Array.from({length: m + 1}, () => new Uint16Array(n + 1));
for (let i = 1; i <= m; i++) {
for (let j = 1; j <= n; j++) {
if (a[i-1] === b[j-1]) table[i][j] = table[i-1][j-1] + 1;
else table[i][j] = Math.max(table[i-1][j], table[i][j-1]);
}
}
// Backtrack
let i = m, j = n;
const seq = [];
while (i > 0 && j > 0) {
if (a[i-1] === b[j-1]) { seq.push([i-1, j-1]); i--; j--; }
else if (table[i-1][j] >= table[i][j-1]) i--;
else j--;
}
return seq.reverse();
} else {
// Greedy: just pair matching lines in order (fallback for huge inputs)
const result = [];
let ai = 0, bi = 0;
const bMap = new Map();
b.forEach((line, idx) => {
if (!bMap.has(line)) bMap.set(line, []);
bMap.get(line).push(idx);
});
while (ai < m && bi < n) {
if (a[ai] === b[bi]) { result.push([ai, bi]); ai++; bi++; }
else { ai++; }
}
return result;
}
}

// Returns array of {type, origLine, modLine} objects
// type: 'unchanged' | 'added' | 'removed' | 'changed'
function computeDiff(origLines, modLines) {
const matches = lcs(origLines, modLines);
const result = [];
let oi = 0, mi = 0, matchIdx = 0;

while (oi < origLines.length || mi < modLines.length) {
const nextMatch = matches[matchIdx];
if (nextMatch && oi === nextMatch[0] && mi === nextMatch[1]) {
result.push({ type: 'unchanged', orig: origLines[oi], mod: modLines[mi], oi, mi });
oi++; mi++; matchIdx++;
} else {
// Collect consecutive non-matching orig and mod lines
const remStart = oi, addStart = mi;
while (oi < origLines.length && (!nextMatch || oi < nextMatch[0])) oi++;
// recalc nextMatch after advancing oi
const curMatch = matches[matchIdx];
while (mi < modLines.length && (!curMatch || mi < curMatch[1])) mi++;

const remLines = origLines.slice(remStart, oi);
const addLines = modLines.slice(addStart, mi);
const pairLen = Math.min(remLines.length, addLines.length);
// Pair removed+added as changed
for (let k = 0; k < pairLen; k++) {
result.push({ type: 'changed', orig: remLines[k], mod: addLines[k], oi: remStart+k, mi: addStart+k });
}
for (let k = pairLen; k < remLines.length; k++) {
result.push({ type: 'removed', orig: remLines[k], mod: null, oi: remStart+k, mi: null });
}
for (let k = pairLen; k < addLines.length; k++) {
result.push({ type: 'added', orig: null, mod: addLines[k], oi: null, mi: addStart+k });
}
}
}
return result;
}

// ── Character-level diff for changed lines ────────────────────────
function charDiff(a, b) {
// Returns [origHTML, modHTML] with inline highlights
const la = Array.from(a), lb = Array.from(b);
if (la.length * lb.length > 4000) {
return [esc(a), esc(b)]; // skip for very long lines
}
const m = la.length, n = lb.length;
const table = Array.from({length: m+1}, () => new Uint16Array(n+1));
for (let i = 1; i <= m; i++)
for (let j = 1; j <= n; j++)
table[i][j] = la[i-1]===lb[j-1] ? table[i-1][j-1]+1 : Math.max(table[i-1][j],table[i][j-1]);
// backtrack
let i = m, j = n;
const ops = []; // [type, char]  type: 'eq'|'del'|'ins'
while (i > 0 || j > 0) {
if (i > 0 && j > 0 && la[i-1]===lb[j-1]) { ops.push(['eq',la[i-1]]); i--; j--; }
else if (j > 0 && (i===0 || table[i][j-1] >= table[i-1][j])) { ops.push(['ins',lb[j-1]]); j--; }
else { ops.push(['del',la[i-1]]); i--; }
}
ops.reverse();
let oh='', mh='';
for (const [t,c] of ops) {
const ec = esc(c);
if      (t==='eq')  { oh += ec; mh += ec; }
else if (t==='del') { oh += `<span class="df-char-del">${ec}</span>`; }
else                { mh += `<span class="df-char-add">${ec}</span>`; }
}
return [oh, mh];
}

function esc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

// ── Prepare lines ─────────────────────────────────────────────────
function prepareLines(text, ignoreWs, ignoreCase) {
let lines = text.split('\n');
// Remove trailing empty line if text ends with newline
if (lines.length > 0 && lines[lines.length-1] === '') lines.pop();
return lines.map(l => {
let r = l;
if (ignoreWs) r = r.trim().replace(/\s+/g, ' ');
if (ignoreCase) r = r.toLowerCase();
return r;
});
}

// ── Render side-by-side ───────────────────────────────────────────
function renderSide(diffs) {
let leftHTML = '', rightHTML = '';
let ln = 0, rn = 0;

for (const d of diffs) {
if (d.type === 'unchanged') {
ln++; rn++;
const content = esc(d.orig);
leftHTML  += `<div class="df-line"><div class="df-line-num">${ln}</div><div class="df-line-mark"> </div><div class="df-line-content">${content}</div></div>`;
rightHTML += `<div class="df-line"><div class="df-line-num">${rn}</div><div class="df-line-mark"> </div><div class="df-line-content">${content}</div></div>`;
} else if (d.type === 'removed') {
ln++;
leftHTML  += `<div class="df-line removed"><div class="df-line-num removed">${ln}</div><div class="df-line-mark">−</div><div class="df-line-content">${esc(d.orig)}</div></div>`;
rightHTML += `<div class="df-line empty"><div class="df-line-num"> </div><div class="df-line-mark"> </div><div class="df-line-content"> </div></div>`;
} else if (d.type === 'added') {
rn++;
leftHTML  += `<div class="df-line empty"><div class="df-line-num"> </div><div class="df-line-mark"> </div><div class="df-line-content"> </div></div>`;
rightHTML += `<div class="df-line added"><div class="df-line-num added">${rn}</div><div class="df-line-mark">+</div><div class="df-line-content">${esc(d.mod)}</div></div>`;
} else { // changed
ln++; rn++;
const [oh, mh] = charDiff(d.orig, d.mod);
leftHTML  += `<div class="df-line changed"><div class="df-line-num changed">${ln}</div><div class="df-line-mark">~</div><div class="df-line-content">${oh}</div></div>`;
rightHTML += `<div class="df-line changed"><div class="df-line-num changed">${rn}</div><div class="df-line-mark">~</div><div class="df-line-content">${mh}</div></div>`;
}
}

if (!leftHTML && !rightHTML) {
return '<div class="df-empty-state">No differences found — the texts are identical.</div>';
}

return `<div class="df-side">
<div class="df-side-col">
<div class="df-side-col-header">Original</div>
${leftHTML}
</div>
<div class="df-side-col">
<div class="df-side-col-header">Modified</div>
${rightHTML}
</div>
</div>`;
}

// ── Render unified ────────────────────────────────────────────────
function renderUnified(diffs) {
let html = '';
let ln = 0, rn = 0;

for (const d of diffs) {
if (d.type === 'unchanged') {
ln++; rn++;
html += `<div class="df-line"><div class="df-line-num">${ln} / ${rn}</div><div class="df-line-mark"> </div><div class="df-line-content">${esc(d.orig)}</div></div>`;
} else if (d.type === 'removed') {
ln++;
html += `<div class="df-line removed"><div class="df-line-num removed">${ln} /</div><div class="df-line-mark">−</div><div class="df-line-content">${esc(d.orig)}</div></div>`;
} else if (d.type === 'added') {
rn++;
html += `<div class="df-line added"><div class="df-line-num added">/ ${rn}</div><div class="df-line-mark">+</div><div class="df-line-content">${esc(d.mod)}</div></div>`;
} else {
ln++; rn++;
const [oh, mh] = charDiff(d.orig, d.mod);
html += `<div class="df-line removed"><div class="df-line-num removed">${ln} /</div><div class="df-line-mark">−</div><div class="df-line-content">${oh}</div></div>`;
html += `<div class="df-line added"><div class="df-line-num added">/ ${rn}</div><div class="df-line-mark">+</div><div class="df-line-content">${mh}</div></div>`;
}
}

if (!html) {
return '<div class="df-empty-state">No differences found — the texts are identical.</div>';
}
return `<div class="df-unified">${html}</div>`;
}

// ── Plain text for copy ───────────────────────────────────────────
function buildPlainText(diffs) {
let out = '';
for (const d of diffs) {
if      (d.type === 'unchanged') out += `  ${d.orig}\n`;
else if (d.type === 'removed')   out += `- ${d.orig}\n`;
else if (d.type === 'added')     out += `+ ${d.mod}\n`;
else { out += `- ${d.orig}\n+ ${d.mod}\n`; }
}
return out;
}

// ── State ─────────────────────────────────────────────────────────
let currentDiffs = null;
let currentView = 'side'; // 'side' | 'unified'

function runDiff() {
const origText = document.getElementById('df-orig').value;
const modText  = document.getElementById('df-mod').value;
const ignoreWs   = document.getElementById('df-ignore-ws').checked;
const ignoreCase = document.getElementById('df-ignore-case').checked;

const origLines = prepareLines(origText, ignoreWs, ignoreCase);
const modLines  = prepareLines(modText,  ignoreWs, ignoreCase);

// We still want to display original (un-normalized) lines, so recompute display lines
const rawOrig = origText.split('\n');
const rawMod  = modText.split('\n');
if (rawOrig.length > 0 && rawOrig[rawOrig.length-1]==='') rawOrig.pop();
if (rawMod.length  > 0 && rawMod[rawMod.length-1]==='')   rawMod.pop();

const diffs = computeDiff(origLines, modLines);

// Map diffs back to raw (display) lines
const displayDiffs = diffs.map(d => {
const nd = { type: d.type };
if (d.oi !== null && d.oi !== undefined) nd.orig = rawOrig[d.oi] ?? '';
else nd.orig = null;
if (d.mi !== null && d.mi !== undefined) nd.mod  = rawMod[d.mi]  ?? '';
else nd.mod  = null;
return nd;
});

currentDiffs = displayDiffs;

// Stats
let added=0, removed=0, changed=0, unchanged=0;
for (const d of displayDiffs) {
if      (d.type==='added')     added++;
else if (d.type==='removed')   removed++;
else if (d.type==='changed')   changed++;
else                           unchanged++;
}
document.getElementById('df-s-add').textContent = added;
document.getElementById('df-s-rem').textContent = removed;
document.getElementById('df-s-chg').textContent = changed;
document.getElementById('df-s-unc').textContent = unchanged;
document.getElementById('df-stats').style.display = 'flex';

renderResult();
}

function renderResult() {
if (!currentDiffs) return;
const el = document.getElementById('df-result');
el.innerHTML = currentView === 'side'
? renderSide(currentDiffs)
: renderUnified(currentDiffs);
}

function showToast(msg) {
const t = document.getElementById('df-toast');
t.textContent = msg;
t.classList.add('show');
setTimeout(() => t.classList.remove('show'), 2000);
}

// ── Wire up events ────────────────────────────────────────────────
document.getElementById('df-run').addEventListener('click', runDiff);

document.getElementById('df-swap').addEventListener('click', function() {
const a = document.getElementById('df-orig');
const b = document.getElementById('df-mod');
const tmp = a.value;
a.value = b.value;
b.value = tmp;
if (currentDiffs) runDiff();
});

document.getElementById('df-clear').addEventListener('click', function() {
document.getElementById('df-orig').value = '';
document.getElementById('df-mod').value  = '';
currentDiffs = null;
document.getElementById('df-stats').style.display = 'none';
document.getElementById('df-result').innerHTML = '<div class="df-empty-state">Enter text above and click <strong>Compare</strong> to see the diff.</div>';
});

document.getElementById('df-copy').addEventListener('click', function() {
if (!currentDiffs) { showToast('Nothing to copy yet.'); return; }
const text = buildPlainText(currentDiffs);
navigator.clipboard.writeText(text).then(() => showToast('Copied to clipboard!')).catch(() => {
const ta = document.createElement('textarea');
ta.value = text; ta.style.position='fixed'; ta.style.opacity='0';
document.body.appendChild(ta); ta.select();
document.execCommand('copy'); document.body.removeChild(ta);
showToast('Copied to clipboard!');
});
});

document.getElementById('df-view-side').addEventListener('click', function() {
currentView = 'side';
this.classList.add('active');
document.getElementById('df-view-unified').classList.remove('active');
renderResult();
});

document.getElementById('df-view-unified').addEventListener('click', function() {
currentView = 'unified';
this.classList.add('active');
document.getElementById('df-view-side').classList.remove('active');
renderResult();
});

// Auto-run when both textareas have content (on input, debounced)
let debTimer;
function maybeAutoRun() {
clearTimeout(debTimer);
debTimer = setTimeout(function() {
if (document.getElementById('df-orig').value && document.getElementById('df-mod').value) {
runDiff();
}
}, 600);
}
document.getElementById('df-orig').addEventListener('input', maybeAutoRun);
document.getElementById('df-mod').addEventListener('input',  maybeAutoRun);
})();
</script>
</div>

---

## How It Works

The tool implements a **Longest Common Subsequence (LCS)** algorithm in pure JavaScript — the same foundation used by `git diff`. It compares your texts line by line, then applies character-level diffing on changed lines so you can see exactly which characters were inserted or deleted.

All processing happens in your browser. No text is ever sent to a server.

---

## When to Use a Text Diff Checker

| Scenario | What to look for |
|---|---|
| Code review | Changed logic, added/removed lines |
| Document revision | Edited paragraphs, reworded sentences |
| Config comparison | Environment differences |
| Translation QA | Structural alignment between source and target |

---

## Tips

- **Ignore whitespace** — useful when comparing code reformatted by a linter or prettier.
- **Case-insensitive** — handy for comparing user-entered data that may have inconsistent capitalisation.
- **Swap** — quickly reverse the comparison direction to check the diff from the other side.
- **Unified view** — a single-column view familiar to git users (`+`/`−` markers).

---

> Format your code before diffing → [SQL Formatter](/tools/sql-formatter/)

> Preview Markdown in your browser → [Markdown Preview](/tools/markdown-preview/)
