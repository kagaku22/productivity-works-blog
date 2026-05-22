---
title: "行列計算ツール"
description: "無料のオンライン行列計算ツール。加算・減算・乗算・行列式・逆行列・転置行列を2×2〜5×5行列で計算。数学・線形代数の学習に最適。"
slug: matrix-calculator
date: 2026-01-05
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
ShowToc: false
cover:
  image: /images/covers/matrix-calculator-ja.png
  alt: "行列計算ツール - 無料オンラインで行列演算"
---

<div id="mx-app">

<style>
#mx-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
color: #1a1a2e;
}
#mx-app h2 {
font-size: 1.25rem;
font-weight: 700;
margin: 0 0 0.75rem 0;
color: #1a1a2e;
}
#mx-app .mx-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 1.25rem;
margin-bottom: 1rem;
box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#mx-app .mx-row {
display: flex;
gap: 1rem;
flex-wrap: wrap;
}
#mx-app .mx-col {
flex: 1;
min-width: 200px;
}
#mx-app .mx-label {
font-size: 0.8rem;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 0.4rem;
display: block;
}
#mx-app select {
width: 100%;
padding: 0.45rem 0.6rem;
border: 1px solid #cbd5e1;
border-radius: 8px;
font-size: 0.9rem;
background: #f8fafc;
color: #1a1a2e;
cursor: pointer;
outline: none;
transition: border-color 0.2s;
}
#mx-app select:focus {
border-color: #6366f1;
}
#mx-app .mx-grid-wrap {
overflow-x: auto;
}
#mx-app .mx-grid {
display: inline-grid;
gap: 4px;
margin-top: 0.5rem;
padding: 0.5rem;
background: #f1f5f9;
border-radius: 8px;
border: 2px solid #e2e8f0;
}
#mx-app .mx-grid input {
width: 56px;
height: 44px;
text-align: center;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 0.95rem;
font-weight: 600;
color: #1a1a2e;
background: #fff;
outline: none;
transition: border-color 0.2s, box-shadow 0.2s;
-moz-appearance: textfield;
}
#mx-app .mx-grid input::-webkit-outer-spin-button,
#mx-app .mx-grid input::-webkit-inner-spin-button {
-webkit-appearance: none;
}
#mx-app .mx-grid input:focus {
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#mx-app .mx-scalar-row {
display: flex;
align-items: center;
gap: 0.75rem;
margin-top: 0.75rem;
flex-wrap: wrap;
}
#mx-app .mx-scalar-row label {
font-size: 0.875rem;
font-weight: 600;
color: #475569;
}
#mx-app .mx-scalar-row input {
width: 80px;
padding: 0.4rem 0.5rem;
border: 1px solid #cbd5e1;
border-radius: 8px;
font-size: 0.95rem;
text-align: center;
outline: none;
-moz-appearance: textfield;
}
#mx-app .mx-scalar-row input::-webkit-outer-spin-button,
#mx-app .mx-scalar-row input::-webkit-inner-spin-button {
-webkit-appearance: none;
}
#mx-app .mx-scalar-row input:focus {
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#mx-app .mx-btns {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-top: 0.75rem;
}
#mx-app .mx-btn {
padding: 0.5rem 1rem;
border: none;
border-radius: 8px;
font-size: 0.875rem;
font-weight: 600;
cursor: pointer;
transition: background 0.18s, transform 0.12s, box-shadow 0.18s;
outline: none;
}
#mx-app .mx-btn:active {
transform: scale(0.97);
}
#mx-app .mx-btn-primary {
background: #6366f1;
color: #fff;
box-shadow: 0 2px 6px rgba(99,102,241,0.25);
}
#mx-app .mx-btn-primary:hover {
background: #4f46e5;
box-shadow: 0 4px 12px rgba(99,102,241,0.35);
}
#mx-app .mx-btn-secondary {
background: #f1f5f9;
color: #475569;
border: 1px solid #e2e8f0;
}
#mx-app .mx-btn-secondary:hover {
background: #e2e8f0;
}
#mx-app .mx-btn-danger {
background: #fef2f2;
color: #dc2626;
border: 1px solid #fecaca;
}
#mx-app .mx-btn-danger:hover {
background: #fee2e2;
}
#mx-app .mx-ops {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-bottom: 0.75rem;
}
#mx-app .mx-op-btn {
padding: 0.5rem 0.9rem;
border: 2px solid #e2e8f0;
border-radius: 8px;
font-size: 0.875rem;
font-weight: 700;
cursor: pointer;
background: #fff;
color: #475569;
transition: all 0.18s;
}
#mx-app .mx-op-btn:hover {
border-color: #6366f1;
color: #6366f1;
background: #f5f3ff;
}
#mx-app .mx-op-btn.active {
background: #6366f1;
color: #fff;
border-color: #6366f1;
box-shadow: 0 2px 8px rgba(99,102,241,0.3);
}
#mx-app .mx-result-area {
background: #0f172a;
color: #e2e8f0;
border-radius: 10px;
padding: 1.25rem;
min-height: 80px;
font-family: "JetBrains Mono", "Fira Code", "Courier New", monospace;
font-size: 0.92rem;
line-height: 1.8;
white-space: pre;
overflow-x: auto;
}
#mx-app .mx-result-area.error {
background: #1c0a0a;
color: #f87171;
}
#mx-app .mx-result-area.success {
background: #0a1628;
color: #93c5fd;
}
#mx-app .mx-steps {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 1rem 1.25rem;
font-family: "JetBrains Mono", "Fira Code", "Courier New", monospace;
font-size: 0.82rem;
line-height: 1.8;
color: #475569;
white-space: pre-wrap;
overflow-x: auto;
margin-top: 0.75rem;
}
#mx-app .mx-matrix-label {
font-size: 1.1rem;
font-weight: 800;
color: #6366f1;
margin-bottom: 0.25rem;
}
#mx-app .mx-info {
font-size: 0.82rem;
color: #94a3b8;
margin-top: 0.4rem;
}
#mx-app .mx-freee-cta {
background: linear-gradient(135deg, #1a56db 0%, #1e40af 100%);
color: #fff;
border-radius: 14px;
padding: 1.5rem 1.75rem;
margin: 1.5rem 0;
display: flex;
align-items: center;
gap: 1.25rem;
flex-wrap: wrap;
box-shadow: 0 4px 16px rgba(26,86,219,0.25);
}
#mx-app .mx-freee-cta .mx-freee-icon {
font-size: 2.5rem;
flex-shrink: 0;
}
#mx-app .mx-freee-cta .mx-freee-text h3 {
font-size: 1.05rem;
font-weight: 800;
margin: 0 0 0.3rem 0;
color: #fff;
}
#mx-app .mx-freee-cta .mx-freee-text p {
font-size: 0.85rem;
color: #bfdbfe;
margin: 0;
line-height: 1.5;
}
#mx-app .mx-freee-cta a.mx-freee-btn {
display: inline-block;
background: #fff;
color: #1a56db;
font-weight: 800;
font-size: 0.9rem;
padding: 0.6rem 1.3rem;
border-radius: 9px;
text-decoration: none;
white-space: nowrap;
transition: all 0.18s;
box-shadow: 0 2px 8px rgba(0,0,0,0.15);
flex-shrink: 0;
}
#mx-app .mx-freee-cta a.mx-freee-btn:hover {
background: #eff6ff;
box-shadow: 0 4px 14px rgba(0,0,0,0.18);
}
#mx-app .mx-freee-footer {
font-size: 0.72rem;
color: #94a3b8;
margin-top: 0.5rem;
text-align: center;
}
#mx-app .mx-related {
margin-top: 2rem;
padding-top: 1.25rem;
border-top: 1px solid #e2e8f0;
}
#mx-app .mx-related h3 {
font-size: 0.9rem;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 0.6rem;
}
#mx-app .mx-related-links {
display: flex;
gap: 0.75rem;
flex-wrap: wrap;
}
#mx-app .mx-related-links a {
color: #6366f1;
text-decoration: none;
font-weight: 600;
font-size: 0.9rem;
padding: 0.35rem 0.75rem;
border: 1px solid #c7d2fe;
border-radius: 8px;
transition: all 0.18s;
}
#mx-app .mx-related-links a:hover {
background: #6366f1;
color: #fff;
border-color: #6366f1;
}
</style>

<div class="mx-card">
<h2>行列の入力</h2>
<div class="mx-row">
<div class="mx-col">
<div class="mx-matrix-label">行列 A</div>
<label class="mx-label">サイズ</label>
<select id="mx-size-a">
<option value="2">2 × 2</option>
<option value="3" selected>3 × 3</option>
<option value="4">4 × 4</option>
<option value="5">5 × 5</option>
</select>
<div class="mx-grid-wrap">
<div class="mx-grid" id="mx-grid-a"></div>
</div>
<div class="mx-btns">
<button class="mx-btn mx-btn-secondary" id="mx-rand-a">ランダム入力</button>
<button class="mx-btn mx-btn-danger" id="mx-clear-a">クリア (A)</button>
</div>
</div>
<div class="mx-col">
<div class="mx-matrix-label">行列 B</div>
<label class="mx-label">サイズ</label>
<select id="mx-size-b">
<option value="2">2 × 2</option>
<option value="3" selected>3 × 3</option>
<option value="4">4 × 4</option>
<option value="5">5 × 5</option>
</select>
<div class="mx-grid-wrap">
<div class="mx-grid" id="mx-grid-b"></div>
</div>
<div class="mx-btns">
<button class="mx-btn mx-btn-secondary" id="mx-rand-b">ランダム入力</button>
<button class="mx-btn mx-btn-danger" id="mx-clear-b">クリア (B)</button>
</div>
</div>
</div>
<div class="mx-scalar-row">
<label for="mx-scalar">スカラー (k)：</label>
<input type="number" id="mx-scalar" value="2" step="any">
<span class="mx-info">スカラー倍算（k × A）に使用</span>
</div>
</div>

<div class="mx-card">
<h2>演算の選択</h2>
<div class="mx-ops">
<button class="mx-op-btn active" data-op="add">A + B（加算）</button>
<button class="mx-op-btn" data-op="sub">A − B（減算）</button>
<button class="mx-op-btn" data-op="mul">A × B（乗算）</button>
<button class="mx-op-btn" data-op="det">det(A)（行列式）</button>
<button class="mx-op-btn" data-op="inv">A⁻¹（逆行列）</button>
<button class="mx-op-btn" data-op="tra">Aᵀ（転置）</button>
<button class="mx-op-btn" data-op="scalar">k × A（スカラー倍）</button>
</div>
<div class="mx-btns">
<button class="mx-btn mx-btn-primary" id="mx-calc">計算する</button>
</div>
</div>

<div class="mx-card">
<h2>計算結果</h2>
<div class="mx-result-area" id="mx-result">演算を選択して「計算する」を押してください。</div>
<div id="mx-steps-wrap" style="display:none">
<h2 style="margin-top:1rem">途中式・計算手順</h2>
<div class="mx-steps" id="mx-steps"></div>
</div>
</div>

<div class="mx-freee-cta">
<div class="mx-freee-icon">💼</div>
<div class="mx-freee-text">
<h3>事業の数字管理はfreeeで自動化</h3>
<p>請求書・経費・確定申告まで一括管理。個人事業主・中小企業に選ばれるクラウド会計ソフト。</p>
</div>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP?utm_source=productivity-works&utm_medium=referral&utm_campaign=matrix-calculator" class="mx-freee-btn" target="_blank" rel="noopener">freeeを試す（無料）</a>
</div>
<p class="mx-freee-footer">※本リンクはアフィリエイトリンクです。</p>

<div class="mx-related">
<h3>関連ツール</h3>
<div class="mx-related-links">
<a href="/ja/tools/scientific-calculator/">関数電卓</a>
<a href="/ja/tools/percentage-calculator/">パーセント計算ツール</a>
</div>
</div>

</div>

<script>
(function() {
'use strict';

// --- State ---
var sizeA = 3, sizeB = 3;
var currentOp = 'add';

// --- Grid rendering ---
function buildGrid(containerId, size) {
var el = document.getElementById(containerId);
el.style.gridTemplateColumns = 'repeat(' + size + ', 56px)';
el.innerHTML = '';
for (var r = 0; r < size; r++) {
for (var c = 0; c < size; c++) {
var inp = document.createElement('input');
inp.type = 'number';
inp.step = 'any';
inp.value = '0';
inp.dataset.r = r;
inp.dataset.c = c;
el.appendChild(inp);
}
}
}

function rebuildA() {
sizeA = parseInt(document.getElementById('mx-size-a').value, 10);
buildGrid('mx-grid-a', sizeA);
}

function rebuildB() {
sizeB = parseInt(document.getElementById('mx-size-b').value, 10);
buildGrid('mx-grid-b', sizeB);
}

// --- Read matrix ---
function readMatrix(gridId, size) {
var el = document.getElementById(gridId);
var inputs = el.querySelectorAll('input');
var M = [];
for (var r = 0; r < size; r++) {
M[r] = [];
for (var c = 0; c < size; c++) {
var v = parseFloat(inputs[r * size + c].value);
M[r][c] = isNaN(v) ? 0 : v;
}
}
return M;
}

function randomFill(gridId) {
var el = document.getElementById(gridId);
var inputs = el.querySelectorAll('input');
inputs.forEach(function(inp) {
inp.value = Math.floor(Math.random() * 19) - 9;
});
}

function clearGrid(gridId) {
var el = document.getElementById(gridId);
var inputs = el.querySelectorAll('input');
inputs.forEach(function(inp) { inp.value = '0'; });
}

// --- Formatting ---
function fmt(v) {
if (Math.abs(v) < 1e-9) return '0';
var r = Math.round(v * 1e8) / 1e8;
if (Number.isInteger(r)) return r.toString();
return parseFloat(r.toFixed(6)).toString();
}

function matrixToString(M, label) {
var n = M.length;
var cols = M[0].length;
var colWidths = [];
for (var c = 0; c < cols; c++) {
var max = 0;
for (var r = 0; r < n; r++) max = Math.max(max, fmt(M[r][c]).length);
colWidths[c] = max;
}
var lines = [];
if (label) lines.push(label + ':');
for (var r = 0; r < n; r++) {
var row = M[r].map(function(v, c) { return fmt(v).padStart(colWidths[c]); }).join('  ');
var prefix = r === 0 ? '┌ ' : (r === n - 1 ? '└ ' : '│ ');
var suffix = r === 0 ? ' ┐' : (r === n - 1 ? ' ┘' : ' │');
lines.push(prefix + row + suffix);
}
return lines.join('\n');
}

// --- Matrix operations ---
function matAdd(A, B) {
return A.map(function(row, r) { return row.map(function(v, c) { return v + B[r][c]; }); });
}

function matSub(A, B) {
return A.map(function(row, r) { return row.map(function(v, c) { return v - B[r][c]; }); });
}

function matMul(A, B) {
var n = A.length, m = B[0].length, p = B.length;
var C = [];
for (var r = 0; r < n; r++) {
C[r] = [];
for (var c = 0; c < m; c++) {
var s = 0;
for (var k = 0; k < p; k++) s += A[r][k] * B[k][c];
C[r][c] = s;
}
}
return C;
}

function matTranspose(A) {
var n = A.length, m = A[0].length;
var T = [];
for (var c = 0; c < m; c++) {
T[c] = [];
for (var r = 0; r < n; r++) T[c][r] = A[r][c];
}
return T;
}

function matScalar(A, k) {
return A.map(function(row) { return row.map(function(v) { return v * k; }); });
}

function getMinor(M, row, col) {
return M.filter(function(_, r) { return r !== row; }).map(function(r) {
return r.filter(function(_, c) { return c !== col; });
});
}

function detRecurse(M, steps, depth) {
var n = M.length;
if (n === 1) return M[0][0];
if (n === 2) {
var d = M[0][0] * M[1][1] - M[0][1] * M[1][0];
if (depth <= 1 && steps) {
steps.push('det = ' + fmt(M[0][0]) + ' × ' + fmt(M[1][1]) + ' − ' + fmt(M[0][1]) + ' × ' + fmt(M[1][0]) + ' = ' + fmt(d));
}
return d;
}
var det = 0;
for (var c = 0; c < n; c++) {
var sign = (c % 2 === 0) ? 1 : -1;
var minor = getMinor(M, 0, c);
var minorDet = detRecurse(minor, steps, depth + 1);
det += sign * M[0][c] * minorDet;
}
if (depth === 0 && steps) {
steps.push('第1行による余因子展開:');
var termStrs = [];
for (var c = 0; c < n; c++) {
var sign = (c % 2 === 0) ? 1 : -1;
var mdet = detRecurse(getMinor(M, 0, c), null, 99);
var sStr = sign > 0 ? '+' : '−';
termStrs.push('  ' + sStr + ' ' + fmt(Math.abs(M[0][c])) + ' × det(M' + c + ')  =  ' + sStr + ' ' + fmt(Math.abs(M[0][c])) + ' × ' + fmt(Math.abs(mdet)) + '  =  ' + fmt(sign * M[0][c] * mdet));
}
steps.push(termStrs.join('\n'));
steps.push('det(A) = ' + fmt(det));
}
return det;
}

function matDet(M) {
var steps = [];
var d = detRecurse(M, steps, 0);
return { value: d, steps: steps };
}

function matInverse(M) {
var n = M.length;
var aug = M.map(function(row, r) {
var id = new Array(n).fill(0);
id[r] = 1;
return row.slice().concat(id);
});
for (var col = 0; col < n; col++) {
var pivotRow = -1, maxVal = 0;
for (var r = col; r < n; r++) {
if (Math.abs(aug[r][col]) > maxVal) { maxVal = Math.abs(aug[r][col]); pivotRow = r; }
}
if (maxVal < 1e-12) return null;
var tmp = aug[col]; aug[col] = aug[pivotRow]; aug[pivotRow] = tmp;
var scale = aug[col][col];
aug[col] = aug[col].map(function(v) { return v / scale; });
for (var r = 0; r < n; r++) {
if (r === col) continue;
var factor = aug[r][col];
aug[r] = aug[r].map(function(v, c) { return v - factor * aug[col][c]; });
}
}
return aug.map(function(row) { return row.slice(n); });
}

// --- Display ---
function showResult(text, type) {
var el = document.getElementById('mx-result');
el.textContent = text;
el.className = 'mx-result-area ' + (type || '');
}

function showSteps(text) {
var wrap = document.getElementById('mx-steps-wrap');
var el = document.getElementById('mx-steps');
if (text) { wrap.style.display = 'block'; el.textContent = text; }
else { wrap.style.display = 'none'; el.textContent = ''; }
}

// --- Calculate ---
function calculate() {
var A = readMatrix('mx-grid-a', sizeA);
var B = readMatrix('mx-grid-b', sizeB);
var k = parseFloat(document.getElementById('mx-scalar').value) || 0;
showSteps('');

try {
if (currentOp === 'add') {
if (sizeA !== sizeB) { showResult('エラー：加算には同じサイズの行列が必要です。', 'error'); return; }
showResult(matrixToString(A, 'A') + '\n\n' + matrixToString(B, 'B') + '\n\nA + B =\n' + matrixToString(matAdd(A, B)), 'success');
} else if (currentOp === 'sub') {
if (sizeA !== sizeB) { showResult('エラー：減算には同じサイズの行列が必要です。', 'error'); return; }
showResult(matrixToString(A, 'A') + '\n\n' + matrixToString(B, 'B') + '\n\nA − B =\n' + matrixToString(matSub(A, B)), 'success');
} else if (currentOp === 'mul') {
if (sizeA !== sizeB) { showResult('エラー：A×B には A の列数 = B の行数が必要です。', 'error'); return; }
showResult(matrixToString(A, 'A') + '\n\n' + matrixToString(B, 'B') + '\n\nA × B =\n' + matrixToString(matMul(A, B)), 'success');
} else if (currentOp === 'det') {
var res = matDet(A);
showResult(matrixToString(A, 'A') + '\n\ndet(A) = ' + fmt(res.value), 'success');
showSteps('行列 A の行列式 — 余因子展開\n\n' + res.steps.join('\n'));
} else if (currentOp === 'inv') {
var inv = matInverse(A);
if (!inv) { showResult('エラー：行列 A は正則ではありません（det = 0）。逆行列は存在しません。', 'error'); return; }
showResult(matrixToString(A, 'A') + '\n\nA⁻¹ =\n' + matrixToString(inv), 'success');
showSteps('方法：ガウス・ジョルダン消去法\n拡大行列 [A|I] を行基本変形 → [I|A⁻¹]');
} else if (currentOp === 'tra') {
showResult(matrixToString(A, 'A') + '\n\nAᵀ =\n' + matrixToString(matTranspose(A)), 'success');
} else if (currentOp === 'scalar') {
showResult(matrixToString(A, 'A') + '\n\n' + fmt(k) + ' × A =\n' + matrixToString(matScalar(A, k)), 'success');
}
} catch(e) {
showResult('予期しないエラー: ' + e.message, 'error');
}
}

// --- Event listeners ---
document.getElementById('mx-size-a').addEventListener('change', rebuildA);
document.getElementById('mx-size-b').addEventListener('change', rebuildB);
document.getElementById('mx-rand-a').addEventListener('click', function() { randomFill('mx-grid-a'); });
document.getElementById('mx-rand-b').addEventListener('click', function() { randomFill('mx-grid-b'); });
document.getElementById('mx-clear-a').addEventListener('click', function() { clearGrid('mx-grid-a'); });
document.getElementById('mx-clear-b').addEventListener('click', function() { clearGrid('mx-grid-b'); });
document.getElementById('mx-calc').addEventListener('click', calculate);

document.querySelectorAll('#mx-app .mx-op-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#mx-app .mx-op-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
currentOp = btn.dataset.op;
});
});

// --- Init ---
buildGrid('mx-grid-a', sizeA);
buildGrid('mx-grid-b', sizeB);

})();
</script>

## 使い方

1. **サイズを選択** — 行列 A・B それぞれのサイズ（2×2〜5×5）を選択します。
2. **数値を入力** — 各セルをクリックして数値を入力。「ランダム入力」でテスト値を自動入力できます。
3. **演算を選択** — A+B・A−B・A×B・det(A)・A⁻¹・Aᵀ・k×A から選択します。
4. **計算する** — 「計算する」ボタンを押すと結果と計算手順が表示されます。

## 対応演算一覧

| 演算 | 説明 | 条件 |
|------|------|------|
| **A + B** | 成分ごとの加算 | 同じサイズ |
| **A − B** | 成分ごとの減算 | 同じサイズ |
| **A × B** | 行列の積 | A の列数 = B の行数 |
| **det(A)** | 余因子展開で行列式 | 正方行列 A |
| **A⁻¹** | ガウス・ジョルダン法で逆行列 | 正則な正方行列 A |
| **Aᵀ** | 転置行列 | 任意の行列 A |
| **k × A** | スカラー倍 | 任意の行列 A |

## 行列とは？

**行列**（ぎょうれつ）とは、数値を長方形状に並べた数学的な構造です。線形代数の基礎であり、機械学習・コンピュータグラフィックス・物理シミュレーション・データ科学など幅広い分野で活用されています。

- **正方行列**：行数と列数が等しい行列（行列式・逆行列の計算に必要）
- **行列式**：行列の「体積スケーリング」を表すスカラー値。0なら正則ではない
- **逆行列**：A × A⁻¹ = I（単位行列）となる行列
- **転置行列**：行と列を入れ替えた行列
