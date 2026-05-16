---
title: "Matrix Calculator"
description: "Free online matrix calculator. Perform addition, subtraction, multiplication, determinant, inverse, and transpose operations on 2x2 to 5x5 matrices."
slug: matrix-calculator
date: 2025-05-16
categories: ["Free Tools"]
ShowToc: false
cover:
  image: /images/covers/matrix-calculator.png
  alt: "Matrix Calculator - Free online tool for matrix operations"
---

<div id="mx-app">

<style>
#mx-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
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
#mx-app .mx-badge {
  display: inline-block;
  font-size: 0.7rem;
  font-weight: 700;
  padding: 0.15rem 0.45rem;
  border-radius: 999px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
#mx-app .mx-badge-a { background: #dbeafe; color: #1d4ed8; }
#mx-app .mx-badge-b { background: #dcfce7; color: #166534; }
#mx-app .mx-info {
  font-size: 0.82rem;
  color: #94a3b8;
  margin-top: 0.4rem;
}
#mx-app .mx-matrix-label {
  font-size: 1.1rem;
  font-weight: 800;
  color: #6366f1;
  margin-bottom: 0.25rem;
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
  <h2>Matrix Inputs</h2>
  <div class="mx-row">
    <div class="mx-col">
      <div class="mx-matrix-label">Matrix A</div>
      <label class="mx-label">Size</label>
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
        <button class="mx-btn mx-btn-secondary" id="mx-rand-a">Random Fill</button>
        <button class="mx-btn mx-btn-danger" id="mx-clear-a">Clear A</button>
      </div>
    </div>
    <div class="mx-col">
      <div class="mx-matrix-label">Matrix B</div>
      <label class="mx-label">Size</label>
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
        <button class="mx-btn mx-btn-secondary" id="mx-rand-b">Random Fill</button>
        <button class="mx-btn mx-btn-danger" id="mx-clear-b">Clear B</button>
      </div>
    </div>
  </div>
  <div class="mx-scalar-row">
    <label for="mx-scalar">Scalar (k):</label>
    <input type="number" id="mx-scalar" value="2" step="any">
    <span class="mx-info">Used for scalar multiplication (k × A)</span>
  </div>
</div>

<div class="mx-card">
  <h2>Operations</h2>
  <div class="mx-ops">
    <button class="mx-op-btn active" data-op="add">A + B</button>
    <button class="mx-op-btn" data-op="sub">A − B</button>
    <button class="mx-op-btn" data-op="mul">A × B</button>
    <button class="mx-op-btn" data-op="det">det(A)</button>
    <button class="mx-op-btn" data-op="inv">A⁻¹</button>
    <button class="mx-op-btn" data-op="tra">Aᵀ</button>
    <button class="mx-op-btn" data-op="scalar">k × A</button>
  </div>
  <div class="mx-btns">
    <button class="mx-btn mx-btn-primary" id="mx-calc">Calculate</button>
  </div>
</div>

<div class="mx-card">
  <h2>Result</h2>
  <div class="mx-result-area" id="mx-result">Select an operation and click Calculate.</div>
  <div id="mx-steps-wrap" style="display:none">
    <h2 style="margin-top:1rem">Step-by-Step</h2>
    <div class="mx-steps" id="mx-steps"></div>
  </div>
</div>

<div class="mx-related">
  <h3>Related Tools</h3>
  <div class="mx-related-links">
    <a href="/tools/scientific-calculator/">Scientific Calculator</a>
    <a href="/tools/percentage-calculator/">Percentage Calculator</a>
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

  // --- Read matrix from grid ---
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

  // --- Random fill ---
  function randomFill(gridId, size) {
    var el = document.getElementById(gridId);
    var inputs = el.querySelectorAll('input');
    inputs.forEach(function(inp) {
      inp.value = Math.floor(Math.random() * 19) - 9;
    });
  }

  function clearGrid(gridId, size) {
    var el = document.getElementById(gridId);
    var inputs = el.querySelectorAll('input');
    inputs.forEach(function(inp) { inp.value = '0'; });
  }

  // --- Matrix display ---
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
      for (var r = 0; r < n; r++) {
        max = Math.max(max, fmt(M[r][c]).length);
      }
      colWidths[c] = max;
    }
    var lines = [];
    if (label) lines.push(label + ':');
    for (var r = 0; r < n; r++) {
      var row = M[r].map(function(v, c) {
        var s = fmt(v);
        return s.padStart(colWidths[c]);
      }).join('  ');
      var prefix = r === 0 ? '┌ ' : (r === n - 1 ? '└ ' : '│ ');
      var suffix = r === 0 ? ' ┐' : (r === n - 1 ? ' ┘' : ' │');
      lines.push(prefix + row + suffix);
    }
    return lines.join('\n');
  }

  // --- Math ops ---
  function matAdd(A, B) {
    var n = A.length;
    return A.map(function(row, r) {
      return row.map(function(v, c) { return v + B[r][c]; });
    });
  }

  function matSub(A, B) {
    return A.map(function(row, r) {
      return row.map(function(v, c) { return v - B[r][c]; });
    });
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

  // --- Determinant with cofactor expansion (for steps) ---
  function getMinor(M, row, col) {
    return M.filter(function(_, r) { return r !== row; }).map(function(row) {
      return row.filter(function(_, c) { return c !== col; });
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
    var expansion = [];
    for (var c = 0; c < n; c++) {
      var sign = (c % 2 === 0) ? 1 : -1;
      var minor = getMinor(M, 0, c);
      var minorDet = detRecurse(minor, steps, depth + 1);
      var term = sign * M[0][c] * minorDet;
      det += term;
      expansion.push((sign > 0 ? '+' : '−') + fmt(Math.abs(M[0][c])) + '×M' + c);
    }
    if (depth === 0 && steps) {
      steps.push('Cofactor expansion along row 1:');
      var termStrs = [];
      for (var c = 0; c < n; c++) {
        var sign = (c % 2 === 0) ? 1 : -1;
        var minor = getMinor(M, 0, c);
        var mdet = detRecurse(minor, null, 99);
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

  // --- Inverse via Gauss-Jordan ---
  function matInverse(M) {
    var n = M.length;
    // Augment [M | I]
    var aug = M.map(function(row, r) {
      var identity = new Array(n).fill(0);
      identity[r] = 1;
      return row.slice().concat(identity);
    });

    for (var col = 0; col < n; col++) {
      // Find pivot
      var pivotRow = -1;
      var maxVal = 0;
      for (var r = col; r < n; r++) {
        if (Math.abs(aug[r][col]) > maxVal) {
          maxVal = Math.abs(aug[r][col]);
          pivotRow = r;
        }
      }
      if (maxVal < 1e-12) return null; // singular

      // Swap
      var tmp = aug[col]; aug[col] = aug[pivotRow]; aug[pivotRow] = tmp;

      // Scale pivot row
      var scale = aug[col][col];
      aug[col] = aug[col].map(function(v) { return v / scale; });

      // Eliminate column
      for (var r = 0; r < n; r++) {
        if (r === col) continue;
        var factor = aug[r][col];
        aug[r] = aug[r].map(function(v, c) { return v - factor * aug[col][c]; });
      }
    }

    // Extract inverse
    return aug.map(function(row) { return row.slice(n); });
  }

  // --- Result display ---
  function showResult(text, type) {
    var el = document.getElementById('mx-result');
    el.textContent = text;
    el.className = 'mx-result-area ' + (type || '');
  }

  function showSteps(text) {
    var wrap = document.getElementById('mx-steps-wrap');
    var el = document.getElementById('mx-steps');
    if (text) {
      wrap.style.display = 'block';
      el.textContent = text;
    } else {
      wrap.style.display = 'none';
      el.textContent = '';
    }
  }

  // --- Calculate ---
  function calculate() {
    var A = readMatrix('mx-grid-a', sizeA);
    var B = readMatrix('mx-grid-b', sizeB);
    var k = parseFloat(document.getElementById('mx-scalar').value) || 0;

    showSteps('');

    try {
      if (currentOp === 'add') {
        if (sizeA !== sizeB) { showResult('Error: Matrices must be the same size for addition.', 'error'); return; }
        var R = matAdd(A, B);
        showResult(matrixToString(A, 'A') + '\n\n' + matrixToString(B, 'B') + '\n\nA + B =\n' + matrixToString(R), 'success');
      } else if (currentOp === 'sub') {
        if (sizeA !== sizeB) { showResult('Error: Matrices must be the same size for subtraction.', 'error'); return; }
        var R = matSub(A, B);
        showResult(matrixToString(A, 'A') + '\n\n' + matrixToString(B, 'B') + '\n\nA − B =\n' + matrixToString(R), 'success');
      } else if (currentOp === 'mul') {
        if (sizeA !== sizeB) { showResult('Error: For A×B, number of columns of A must equal number of rows of B.\n(Currently both grids must be same size)', 'error'); return; }
        var R = matMul(A, B);
        showResult(matrixToString(A, 'A') + '\n\n' + matrixToString(B, 'B') + '\n\nA × B =\n' + matrixToString(R), 'success');
      } else if (currentOp === 'det') {
        var res = matDet(A);
        var stepText = res.steps.join('\n');
        showResult(matrixToString(A, 'A') + '\n\ndet(A) = ' + fmt(res.value), 'success');
        showSteps('Determinant of A — Cofactor Expansion\n\n' + stepText);
      } else if (currentOp === 'inv') {
        var inv = matInverse(A);
        if (!inv) {
          showResult('Error: Matrix A is singular (determinant = 0). No inverse exists.', 'error');
          return;
        }
        showResult(matrixToString(A, 'A') + '\n\nA⁻¹ =\n' + matrixToString(inv), 'success');
        showSteps('Method: Gauss-Jordan elimination\nAugmented matrix [A|I] reduced to row echelon form → [I|A⁻¹]');
      } else if (currentOp === 'tra') {
        var T = matTranspose(A);
        showResult(matrixToString(A, 'A') + '\n\nAᵀ =\n' + matrixToString(T), 'success');
      } else if (currentOp === 'scalar') {
        var R = matScalar(A, k);
        showResult(matrixToString(A, 'A') + '\n\n' + fmt(k) + ' × A =\n' + matrixToString(R), 'success');
      }
    } catch(e) {
      showResult('Unexpected error: ' + e.message, 'error');
    }
  }

  // --- Event wiring ---
  document.getElementById('mx-size-a').addEventListener('change', rebuildA);
  document.getElementById('mx-size-b').addEventListener('change', rebuildB);
  document.getElementById('mx-rand-a').addEventListener('click', function() { randomFill('mx-grid-a', sizeA); });
  document.getElementById('mx-rand-b').addEventListener('click', function() { randomFill('mx-grid-b', sizeB); });
  document.getElementById('mx-clear-a').addEventListener('click', function() { clearGrid('mx-grid-a', sizeA); });
  document.getElementById('mx-clear-b').addEventListener('click', function() { clearGrid('mx-grid-b', sizeB); });
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

## How to Use the Matrix Calculator

1. **Set sizes** — Choose grid size (2×2 to 5×5) independently for Matrix A and Matrix B.
2. **Enter values** — Click each cell and type a number. Use **Random Fill** to populate with test values.
3. **Select operation** — Click the operation button (A+B, A−B, A×B, det(A), A⁻¹, Aᵀ, or k×A).
4. **Calculate** — Press the Calculate button to see the result and step-by-step breakdown.

## Supported Operations

| Operation | Description | Requires |
|-----------|-------------|----------|
| **A + B** | Element-wise addition | Same dimensions |
| **A − B** | Element-wise subtraction | Same dimensions |
| **A × B** | Matrix multiplication | A cols = B rows |
| **det(A)** | Determinant with cofactor steps | Square matrix A |
| **A⁻¹** | Inverse via Gauss-Jordan | Square, non-singular A |
| **Aᵀ** | Transpose of A | Any matrix A |
| **k × A** | Scalar multiplication | Any matrix A |

## What is a Matrix?

A **matrix** is a rectangular array of numbers arranged in rows and columns. Matrices are fundamental to linear algebra, computer graphics, machine learning, physics simulations, and engineering.

- **Square matrix**: same number of rows and columns (required for determinant/inverse)
- **Determinant**: a scalar value encoding geometric scaling; zero means the matrix is singular
- **Inverse**: A⁻¹ such that A × A⁻¹ = I (identity matrix)
- **Transpose**: rows become columns and vice versa
