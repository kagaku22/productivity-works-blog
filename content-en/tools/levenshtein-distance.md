---
title: "Levenshtein Distance Calculator"
date: 2025-05-16
description: "Free Levenshtein distance calculator. Measure the edit distance between two strings. Shows step-by-step operations (insert, delete, substitute) and similarity percentage."
categories: ["Free Tools"]
tags: ["Utility", "Free Tools"]
slug: "levenshtein-distance"
ShowToc: false
cover:
  image: "/images/covers/levenshtein-distance.png"
  alt: "Levenshtein Distance Calculator"
---

Enter two strings and instantly calculate their edit distance — how many single-character insertions, deletions, or substitutions it takes to transform one into the other. Visualize the full DP matrix, trace the edit path, and run batch comparisons. Everything runs in your browser with no server, no sign-up, no tracking.

<div id="ld-app">
<style>
#ld-app *,
#ld-app *::before,
#ld-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#ld-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 14px;
color: #1e293b;
line-height: 1.5;
}
#ld-app .ld-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 18px 20px;
margin-bottom: 16px;
}
#ld-app .ld-row {
display: flex;
gap: 14px;
flex-wrap: wrap;
}
#ld-app .ld-col {
flex: 1;
min-width: 180px;
display: flex;
flex-direction: column;
gap: 6px;
}
#ld-app label.ld-label {
font-size: 12px;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#ld-app input.ld-input {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 15px;
font-family: "SF Mono", "Fira Code", Consolas, monospace;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color 0.15s, box-shadow 0.15s;
}
#ld-app input.ld-input:focus {
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#ld-app .ld-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 0;
}
#ld-app .ld-btn {
padding: 7px 16px;
border-radius: 7px;
border: 1.5px solid #cbd5e1;
background: #f8fafc;
color: #334155;
font-size: 13px;
font-weight: 500;
cursor: pointer;
transition: background 0.15s, border-color 0.15s;
white-space: nowrap;
}
#ld-app .ld-btn:hover {
background: #f1f5f9;
border-color: #94a3b8;
}
#ld-app .ld-btn-primary {
background: #6366f1;
border-color: #6366f1;
color: #fff;
font-weight: 600;
}
#ld-app .ld-btn-primary:hover {
background: #4f46e5;
border-color: #4f46e5;
}
#ld-app label.ld-check {
display: flex;
align-items: center;
gap: 5px;
font-size: 13px;
color: #475569;
cursor: pointer;
user-select: none;
}
#ld-app label.ld-check input[type="checkbox"] {
width: 15px;
height: 15px;
accent-color: #6366f1;
cursor: pointer;
}
#ld-app .ld-result-banner {
display: none;
gap: 20px;
flex-wrap: wrap;
background: linear-gradient(135deg, #eef2ff 0%, #f0fdf4 100%);
border: 1.5px solid #c7d2fe;
border-radius: 10px;
padding: 16px 20px;
margin-bottom: 16px;
}
#ld-app .ld-result-banner.show { display: flex; }
#ld-app .ld-stat {
display: flex;
flex-direction: column;
align-items: center;
gap: 2px;
min-width: 80px;
}
#ld-app .ld-stat-num {
font-size: 28px;
font-weight: 700;
color: #4f46e5;
line-height: 1;
}
#ld-app .ld-stat-label {
font-size: 11px;
color: #64748b;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.04em;
text-align: center;
}
#ld-app .ld-ops-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
align-items: center;
}
#ld-app .ld-op-badge {
padding: 4px 10px;
border-radius: 20px;
font-size: 12px;
font-weight: 600;
}
#ld-app .ld-op-ins  { background: #dcfce7; color: #166534; }
#ld-app .ld-op-del  { background: #fee2e2; color: #991b1b; }
#ld-app .ld-op-sub  { background: #fef9c3; color: #854d0e; }
#ld-app .ld-op-eq   { background: #f1f5f9; color: #475569; }
#ld-app .ld-section-title {
font-size: 12px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 10px;
}
#ld-app .ld-steps {
display: none;
flex-direction: column;
gap: 6px;
max-height: 280px;
overflow-y: auto;
padding-right: 4px;
}
#ld-app .ld-steps.show { display: flex; }
#ld-app .ld-step {
display: flex;
align-items: flex-start;
gap: 10px;
padding: 8px 12px;
border-radius: 7px;
border-left: 4px solid transparent;
background: #f8fafc;
font-size: 13px;
}
#ld-app .ld-step.ins { border-left-color: #22c55e; background: #f0fdf4; }
#ld-app .ld-step.del { border-left-color: #ef4444; background: #fef2f2; }
#ld-app .ld-step.sub { border-left-color: #f59e0b; background: #fffbeb; }
#ld-app .ld-step.eq  { border-left-color: #cbd5e1; }
#ld-app .ld-step-icon { font-weight: 700; font-size: 14px; min-width: 18px; }
#ld-app .ld-step-text { color: #334155; line-height: 1.4; }
#ld-app .ld-step-text code {
font-family: "SF Mono", "Fira Code", Consolas, monospace;
background: rgba(0,0,0,0.06);
padding: 1px 5px;
border-radius: 4px;
font-size: 12px;
}
/* DP Matrix */
#ld-app .ld-matrix-wrap {
display: none;
overflow-x: auto;
margin-top: 4px;
}
#ld-app .ld-matrix-wrap.show { display: block; }
#ld-app .ld-matrix-table {
border-collapse: collapse;
font-family: "SF Mono", "Fira Code", Consolas, monospace;
font-size: 12px;
}
#ld-app .ld-matrix-table th,
#ld-app .ld-matrix-table td {
width: 32px;
height: 32px;
text-align: center;
vertical-align: middle;
border: 1px solid #e2e8f0;
}
#ld-app .ld-matrix-table th {
background: #f1f5f9;
color: #64748b;
font-weight: 700;
font-size: 11px;
}
#ld-app .ld-matrix-table td {
background: #fff;
color: #1e293b;
}
#ld-app .ld-matrix-table td.ld-path {
background: #eef2ff;
color: #4f46e5;
font-weight: 700;
}
#ld-app .ld-matrix-table td.ld-path-end {
background: #6366f1;
color: #fff;
font-weight: 700;
}
/* Similarity bar */
#ld-app .ld-sim-bar-wrap {
margin-top: 8px;
background: #e2e8f0;
border-radius: 99px;
height: 8px;
overflow: hidden;
}
#ld-app .ld-sim-bar {
height: 100%;
border-radius: 99px;
background: linear-gradient(90deg, #6366f1, #22c55e);
transition: width 0.4s ease;
width: 0%;
}
/* Batch mode */
#ld-app .ld-batch-area {
width: 100%;
min-height: 100px;
padding: 10px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-family: "SF Mono", "Fira Code", Consolas, monospace;
font-size: 13px;
resize: vertical;
outline: none;
color: #1e293b;
background: #fff;
transition: border-color 0.15s, box-shadow 0.15s;
}
#ld-app .ld-batch-area:focus {
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#ld-app .ld-batch-results {
display: none;
flex-direction: column;
gap: 6px;
margin-top: 10px;
}
#ld-app .ld-batch-results.show { display: flex; }
#ld-app .ld-batch-row {
display: flex;
align-items: center;
gap: 10px;
padding: 8px 12px;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 7px;
font-size: 13px;
flex-wrap: wrap;
}
#ld-app .ld-batch-pair {
font-family: "SF Mono", "Fira Code", Consolas, monospace;
color: #475569;
flex: 1;
min-width: 120px;
}
#ld-app .ld-batch-dist {
font-weight: 700;
color: #4f46e5;
min-width: 80px;
text-align: right;
}
#ld-app .ld-batch-sim {
color: #16a34a;
font-weight: 600;
min-width: 60px;
text-align: right;
}
#ld-app .ld-tab-row {
display: flex;
gap: 4px;
margin-bottom: 14px;
border-bottom: 2px solid #e2e8f0;
}
#ld-app .ld-tab {
padding: 8px 16px;
font-size: 13px;
font-weight: 600;
color: #64748b;
cursor: pointer;
border: none;
background: none;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
}
#ld-app .ld-tab.active {
color: #6366f1;
border-bottom-color: #6366f1;
}
#ld-app .ld-tab-panel { display: none; }
#ld-app .ld-tab-panel.active { display: block; }
#ld-app .ld-hint {
font-size: 12px;
color: #94a3b8;
margin-top: 5px;
}
#ld-app .ld-empty {
color: #94a3b8;
font-size: 13px;
text-align: center;
padding: 20px 0;
}
#ld-app .ld-error {
color: #dc2626;
font-size: 13px;
padding: 8px 12px;
background: #fef2f2;
border-radius: 7px;
border: 1px solid #fecaca;
}
</style>

<!-- Tab navigation -->
<div class="ld-tab-row">
<button class="ld-tab active" data-tab="single">Single Pair</button>
<button class="ld-tab" data-tab="batch">Batch Mode</button>
</div>

<!-- ===== SINGLE PAIR TAB ===== -->
<div class="ld-tab-panel active" id="ld-tab-single">

<div class="ld-card">
<div class="ld-row" style="margin-bottom:14px;">
<div class="ld-col">
<label class="ld-label" for="ld-str1">String A</label>
<input class="ld-input" id="ld-str1" type="text" placeholder="e.g. kitten" autocomplete="off" spellcheck="false">
</div>
<div class="ld-col">
<label class="ld-label" for="ld-str2">String B</label>
<input class="ld-input" id="ld-str2" type="text" placeholder="e.g. sitting" autocomplete="off" spellcheck="false">
</div>
</div>
<div class="ld-toolbar">
<button class="ld-btn ld-btn-primary" id="ld-calc-btn">Calculate</button>
<button class="ld-btn" id="ld-swap-btn">&#8646; Swap</button>
<button class="ld-btn" id="ld-clear-btn">Clear</button>
<label class="ld-check">
<input type="checkbox" id="ld-case-toggle"> Case-sensitive
</label>
<label class="ld-check">
<input type="checkbox" id="ld-matrix-toggle"> Show DP matrix
</label>
</div>
</div>

<!-- Result banner -->
<div class="ld-result-banner" id="ld-banner">
<div class="ld-stat">
<span class="ld-stat-num" id="ld-dist-num">—</span>
<span class="ld-stat-label">Edit Distance</span>
</div>
<div class="ld-stat">
<span class="ld-stat-num" id="ld-sim-num">—</span>
<span class="ld-stat-label">Similarity</span>
</div>
<div class="ld-stat">
<span class="ld-stat-num" id="ld-ins-num" style="color:#16a34a;">0</span>
<span class="ld-stat-label">Insertions</span>
</div>
<div class="ld-stat">
<span class="ld-stat-num" id="ld-del-num" style="color:#dc2626;">0</span>
<span class="ld-stat-label">Deletions</span>
</div>
<div class="ld-stat">
<span class="ld-stat-num" id="ld-sub-num" style="color:#d97706;">0</span>
<span class="ld-stat-label">Substitutions</span>
</div>
<div style="flex:1;min-width:140px;display:flex;flex-direction:column;justify-content:center;">
<div style="font-size:11px;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:0.04em;margin-bottom:5px;">Similarity</div>
<div class="ld-sim-bar-wrap"><div class="ld-sim-bar" id="ld-sim-bar"></div></div>
</div>
</div>

<!-- Step-by-step explanation -->
<div class="ld-card" id="ld-steps-card" style="display:none;">
<div class="ld-section-title">Step-by-step Edit Operations</div>
<div class="ld-steps show" id="ld-steps"></div>
</div>

<!-- DP Matrix -->
<div class="ld-card" id="ld-matrix-card" style="display:none;">
<div class="ld-section-title">Dynamic Programming Matrix <span style="font-size:11px;font-weight:400;color:#94a3b8;">(highlighted cells = optimal path)</span></div>
<div class="ld-matrix-wrap show" id="ld-matrix"></div>
</div>

</div>

<!-- ===== BATCH TAB ===== -->
<div class="ld-tab-panel" id="ld-tab-batch">
<div class="ld-card">
<div class="ld-section-title" style="margin-bottom:8px;">Batch Compare</div>
<p class="ld-hint" style="margin-bottom:10px;">Enter one pair per line, separated by a comma: <code style="font-family:monospace;background:#f1f5f9;padding:1px 5px;border-radius:3px;">word1,word2</code></p>
<textarea class="ld-batch-area" id="ld-batch-input" placeholder="kitten,sitting&#10;sunday,saturday&#10;hello,hallo&#10;algorithm,altruistic"></textarea>
<div style="margin-top:10px;display:flex;gap:8px;">
<button class="ld-btn ld-btn-primary" id="ld-batch-btn">Compare All</button>
<button class="ld-btn" id="ld-batch-clear-btn">Clear</button>
<label class="ld-check">
<input type="checkbox" id="ld-batch-case"> Case-sensitive
</label>
</div>
<div class="ld-batch-results" id="ld-batch-results"></div>
</div>
</div>

<script>
(function () {
'use strict';

/* ── Core Levenshtein ── */
function buildMatrix(a, b) {
var m = a.length, n = b.length;
var dp = [];
for (var i = 0; i <= m; i++) {
dp[i] = [];
for (var j = 0; j <= n; j++) {
if (i === 0) { dp[i][j] = j; }
else if (j === 0) { dp[i][j] = i; }
else if (a[i - 1] === b[j - 1]) { dp[i][j] = dp[i - 1][j - 1]; }
else { dp[i][j] = 1 + Math.min(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1]); }
}
}
return dp;
}

function traceback(dp, a, b) {
var ops = [];
var i = a.length, j = b.length;
while (i > 0 || j > 0) {
if (i > 0 && j > 0 && a[i - 1] === b[j - 1]) {
ops.unshift({ type: 'eq', ch: a[i - 1] });
i--; j--;
} else if (j > 0 && (i === 0 || dp[i][j - 1] <= dp[i - 1][j] && dp[i][j - 1] <= dp[i - 1][j - 1])) {
ops.unshift({ type: 'ins', ch: b[j - 1], pos: j - 1 });
j--;
} else if (i > 0 && (j === 0 || dp[i - 1][j] <= dp[i][j - 1] && dp[i - 1][j] <= dp[i - 1][j - 1])) {
ops.unshift({ type: 'del', ch: a[i - 1], pos: i - 1 });
i--;
} else {
ops.unshift({ type: 'sub', from: a[i - 1], to: b[j - 1] });
i--; j--;
}
}
return ops;
}

function levenshtein(a, b) {
var dp = buildMatrix(a, b);
var dist = dp[a.length][b.length];
var ops = traceback(dp, a, b);
var ins = 0, del = 0, sub = 0;
for (var k = 0; k < ops.length; k++) {
if (ops[k].type === 'ins') ins++;
else if (ops[k].type === 'del') del++;
else if (ops[k].type === 'sub') sub++;
}
var maxLen = Math.max(a.length, b.length);
var sim = maxLen === 0 ? 100 : Math.round((1 - dist / maxLen) * 100);
return { dist: dist, sim: sim, ins: ins, del: del, sub: sub, ops: ops, dp: dp };
}

function esc(s) {
return s.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
}

/* ── Render steps ── */
function renderSteps(ops) {
if (ops.length === 0) return '<p class="ld-empty">Identical strings — no operations needed.</p>';
var html = '';
var step = 0;
for (var k = 0; k < ops.length; k++) {
var op = ops[k];
if (op.type === 'eq') {
html += '<div class="ld-step eq"><span class="ld-step-icon" style="color:#94a3b8;">=</span><span class="ld-step-text">Keep <code>' + esc(op.ch) + '</code></span></div>';
} else if (op.type === 'ins') {
step++;
html += '<div class="ld-step ins"><span class="ld-step-icon" style="color:#16a34a;">+</span><span class="ld-step-text"><strong>Step ' + step + ':</strong> Insert <code>' + esc(op.ch) + '</code></span></div>';
} else if (op.type === 'del') {
step++;
html += '<div class="ld-step del"><span class="ld-step-icon" style="color:#dc2626;">−</span><span class="ld-step-text"><strong>Step ' + step + ':</strong> Delete <code>' + esc(op.ch) + '</code></span></div>';
} else if (op.type === 'sub') {
step++;
html += '<div class="ld-step sub"><span class="ld-step-icon" style="color:#d97706;">~</span><span class="ld-step-text"><strong>Step ' + step + ':</strong> Substitute <code>' + esc(op.from) + '</code> → <code>' + esc(op.to) + '</code></span></div>';
}
}
return html;
}

/* ── Render DP Matrix ── */
function renderMatrix(dp, a, b) {
/* Find optimal path cells */
var pathSet = {};
var i = a.length, j = b.length;
pathSet[i + ',' + j] = true;
while (i > 0 || j > 0) {
if (i > 0 && j > 0 && a[i - 1] === b[j - 1]) { i--; j--; }
else if (j > 0 && (i === 0 || dp[i][j - 1] <= dp[i - 1][j] && dp[i][j - 1] <= dp[i - 1][j - 1])) { j--; }
else if (i > 0 && (j === 0 || dp[i - 1][j] <= dp[i][j - 1] && dp[i - 1][j] <= dp[i - 1][j - 1])) { i--; }
else { i--; j--; }
pathSet[i + ',' + j] = true;
}
var html = '<table class="ld-matrix-table"><thead><tr><th></th><th style="background:#e0e7ff;color:#4f46e5;">ε</th>';
for (var jj = 0; jj < b.length; jj++) {
html += '<th style="background:#e0e7ff;color:#4f46e5;">' + esc(b[jj]) + '</th>';
}
html += '</tr></thead><tbody>';
for (var ii = 0; ii <= a.length; ii++) {
html += '<tr>';
if (ii === 0) html += '<th style="background:#e0e7ff;color:#4f46e5;">ε</th>';
else html += '<th style="background:#e0e7ff;color:#4f46e5;">' + esc(a[ii - 1]) + '</th>';
for (var jj2 = 0; jj2 <= b.length; jj2++) {
var key = ii + ',' + jj2;
var isEnd = (ii === a.length && jj2 === b.length);
var cls = isEnd ? 'ld-path-end' : (pathSet[key] ? 'ld-path' : '');
html += '<td class="' + cls + '">' + dp[ii][jj2] + '</td>';
}
html += '</tr>';
}
html += '</tbody></table>';
return html;
}

/* ── Single pair calculation ── */
function calculate() {
var rawA = document.getElementById('ld-str1').value;
var rawB = document.getElementById('ld-str2').value;
var caseSensitive = document.getElementById('ld-case-toggle').checked;
var a = caseSensitive ? rawA : rawA.toLowerCase();
var b = caseSensitive ? rawB : rawB.toLowerCase();

var result = levenshtein(a, b);

/* Banner */
var banner = document.getElementById('ld-banner');
banner.classList.add('show');
document.getElementById('ld-dist-num').textContent = result.dist;
document.getElementById('ld-sim-num').textContent = result.sim + '%';
document.getElementById('ld-ins-num').textContent = result.ins;
document.getElementById('ld-del-num').textContent = result.del;
document.getElementById('ld-sub-num').textContent = result.sub;
document.getElementById('ld-sim-bar').style.width = result.sim + '%';

/* Steps */
var stepsCard = document.getElementById('ld-steps-card');
stepsCard.style.display = 'block';
document.getElementById('ld-steps').innerHTML = renderSteps(result.ops);

/* Matrix */
var showMatrix = document.getElementById('ld-matrix-toggle').checked;
var matrixCard = document.getElementById('ld-matrix-card');
if (showMatrix && a.length <= 20 && b.length <= 20) {
matrixCard.style.display = 'block';
document.getElementById('ld-matrix').innerHTML = renderMatrix(result.dp, a, b);
} else if (showMatrix && (a.length > 20 || b.length > 20)) {
matrixCard.style.display = 'block';
document.getElementById('ld-matrix').innerHTML = '<p class="ld-hint" style="color:#f59e0b;">Matrix display is limited to strings of 20 characters or fewer to maintain readability.</p>';
} else {
matrixCard.style.display = 'none';
}
}

/* ── Batch calculation ── */
function calculateBatch() {
var raw = document.getElementById('ld-batch-input').value.trim();
var caseSensitive = document.getElementById('ld-batch-case').checked;
var resultsEl = document.getElementById('ld-batch-results');
if (!raw) {
resultsEl.innerHTML = '';
resultsEl.classList.remove('show');
return;
}
var lines = raw.split('\n');
var html = '';
var hasResult = false;
for (var i = 0; i < lines.length; i++) {
var line = lines[i].trim();
if (!line) continue;
var parts = line.split(',');
if (parts.length < 2) {
html += '<div class="ld-error">Line ' + (i + 1) + ': invalid format — expected "string1,string2"</div>';
continue;
}
var rawA = parts[0].trim();
var rawB = parts.slice(1).join(',').trim();
var a = caseSensitive ? rawA : rawA.toLowerCase();
var b = caseSensitive ? rawB : rawB.toLowerCase();
var r = levenshtein(a, b);
hasResult = true;
html += '<div class="ld-batch-row">'
+ '<span class="ld-batch-pair">' + esc(rawA) + ' ↔ ' + esc(rawB) + '</span>'
+ '<span class="ld-batch-dist">Distance: ' + r.dist + '</span>'
+ '<span class="ld-batch-sim">' + r.sim + '% similar</span>'
+ '<span style="font-size:12px;color:#64748b;">+' + r.ins + ' −' + r.del + ' ~' + r.sub + '</span>'
+ '</div>';
}
if (!hasResult && !html) {
resultsEl.innerHTML = '';
resultsEl.classList.remove('show');
return;
}
resultsEl.innerHTML = html;
resultsEl.classList.add('show');
}

/* ── Tab switching ── */
document.querySelectorAll('#ld-app .ld-tab').forEach(function (tab) {
tab.addEventListener('click', function () {
document.querySelectorAll('#ld-app .ld-tab').forEach(function (t) { t.classList.remove('active'); });
document.querySelectorAll('#ld-app .ld-tab-panel').forEach(function (p) { p.classList.remove('active'); });
tab.classList.add('active');
document.getElementById('ld-tab-' + tab.dataset.tab).classList.add('active');
});
});

/* ── Event listeners ── */
document.getElementById('ld-calc-btn').addEventListener('click', calculate);

document.getElementById('ld-swap-btn').addEventListener('click', function () {
var a = document.getElementById('ld-str1');
var b = document.getElementById('ld-str2');
var tmp = a.value;
a.value = b.value;
b.value = tmp;
});

document.getElementById('ld-clear-btn').addEventListener('click', function () {
document.getElementById('ld-str1').value = '';
document.getElementById('ld-str2').value = '';
document.getElementById('ld-banner').classList.remove('show');
document.getElementById('ld-steps-card').style.display = 'none';
document.getElementById('ld-matrix-card').style.display = 'none';
});

document.getElementById('ld-matrix-toggle').addEventListener('change', function () {
if (document.getElementById('ld-banner').classList.contains('show')) calculate();
});

var debounceTimer;
function maybeAutoRun() {
clearTimeout(debounceTimer);
debounceTimer = setTimeout(function () {
if (document.getElementById('ld-str1').value || document.getElementById('ld-str2').value) {
calculate();
}
}, 400);
}
document.getElementById('ld-str1').addEventListener('input', maybeAutoRun);
document.getElementById('ld-str2').addEventListener('input', maybeAutoRun);

document.getElementById('ld-batch-btn').addEventListener('click', calculateBatch);
document.getElementById('ld-batch-clear-btn').addEventListener('click', function () {
document.getElementById('ld-batch-input').value = '';
var r = document.getElementById('ld-batch-results');
r.innerHTML = '';
r.classList.remove('show');
});

/* Pre-fill example */
document.getElementById('ld-str1').value = 'kitten';
document.getElementById('ld-str2').value = 'sitting';
calculate();
})();
</script>
</div>

---

## What Is Levenshtein Distance?

The **Levenshtein distance** (also called *edit distance*) between two strings is the minimum number of single-character edits — **insertions**, **deletions**, and **substitutions** — needed to transform one string into the other.

The classic example: transforming **"kitten"** into **"sitting"** requires 3 operations, so their Levenshtein distance is **3**.

| Operation | Example | Cost |
|---|---|---|
| Substitution | k → s (kitten → sitten) | 1 |
| Substitution | e → i (sitten → sittin) | 1 |
| Insertion | sittin → sitting | 1 |

**Similarity %** is computed as `(1 − distance / max(len_a, len_b)) × 100`.

---

## How the DP Algorithm Works

The calculator builds an `(m+1) × (n+1)` matrix where `m` and `n` are the lengths of the two strings. Each cell `dp[i][j]` stores the minimum edit distance between the first `i` characters of string A and the first `j` characters of string B. The recurrence is:

- If `A[i] == B[j]`: `dp[i][j] = dp[i-1][j-1]` (no cost)
- Otherwise: `dp[i][j] = 1 + min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1])` (substitute, delete, insert)

Tracing back through the matrix from `dp[m][n]` reveals the specific sequence of operations shown in the step-by-step breakdown.

---

## Common Use Cases

| Application | How edit distance helps |
|---|---|
| Spell checking | Find the closest dictionary word |
| DNA sequencing | Measure genetic sequence similarity |
| Fuzzy search | Rank search results by closeness |
| Plagiarism detection | Detect near-duplicate passages |
| Record linkage | Merge duplicate database entries |
| Autocorrect | Suggest the most likely intended word |
| NLP / ML | Feature for text similarity models |

---

## Tips

- **Case-sensitive toggle** — By default, comparison is case-insensitive. Enable case-sensitivity when comparing code identifiers or passwords.
- **DP matrix** — Enable "Show DP matrix" to see the full dynamic programming table with the optimal path highlighted. Limited to strings of 20 characters or fewer for readability.
- **Batch mode** — Paste a list of `word1,word2` pairs to compare many strings at once — handy for evaluating fuzzy-match thresholds.
- **Swap** — Swap the two inputs instantly; Levenshtein distance is symmetric (`d(A,B) == d(B,A)`).

---

> Compare full text blocks line by line → [Text Diff Checker](/tools/text-diff-checker/)

> Count words, characters, and sentences → [Word Counter](/tools/word-counter/)
