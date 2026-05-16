---
title: "Split Bill Calculator"
date: 2025-05-16
description: "Free online split bill calculator. Split restaurant bills, shared expenses, and group costs fairly — with tip calculation and unequal splits."
categories: ["Free Tools"]
slug: "split-bill-calculator"
ShowToc: false
cover:
  image: "/images/covers/split-bill-calculator.png"
  alt: "Split Bill Calculator"
---

<div id="sb-app">

<style>
#sb-app {
  font-family: system-ui, -apple-system, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #e2e8f0;
}

#sb-app *,
#sb-app *::before,
#sb-app *::after {
  box-sizing: border-box;
}

#sb-app h2 {
  font-size: 1.15rem;
  font-weight: 700;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin: 0 0 1rem 0;
  padding-bottom: 0.5rem;
  border-bottom: 1px solid #334155;
}

/* Cards */
.sb-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1.25rem;
}

/* Form rows */
.sb-row {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

.sb-field {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
  flex: 1 1 180px;
}

.sb-field label {
  font-size: 0.82rem;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.sb-field input[type="number"],
.sb-field input[type="text"],
.sb-field select {
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 1rem;
  padding: 0.55rem 0.75rem;
  width: 100%;
  transition: border-color 0.15s;
  appearance: none;
  -webkit-appearance: none;
}

.sb-field input[type="number"]:focus,
.sb-field input[type="text"]:focus,
.sb-field select:focus {
  outline: none;
  border-color: #38bdf8;
}

.sb-field select {
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2394a3b8' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 0.75rem center;
  padding-right: 2rem;
}

/* Custom tip row */
#sb-custom-tip-wrap {
  display: none;
}
#sb-custom-tip-wrap.visible {
  display: flex;
}

/* Mode toggle */
.sb-toggle {
  display: flex;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 1.25rem;
  width: 100%;
}

.sb-toggle button {
  flex: 1;
  padding: 0.6rem 1rem;
  border: none;
  background: transparent;
  color: #94a3b8;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}

.sb-toggle button.active {
  background: #38bdf8;
  color: #0f172a;
}

/* Custom split table */
#sb-people-list {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  margin-bottom: 1rem;
}

.sb-person-row {
  display: flex;
  gap: 0.6rem;
  align-items: center;
}

.sb-person-row input[type="text"] {
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 0.95rem;
  padding: 0.5rem 0.65rem;
  flex: 1 1 120px;
}

.sb-person-row input[type="number"] {
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 0.95rem;
  padding: 0.5rem 0.65rem;
  width: 110px;
}

.sb-person-row input:focus {
  outline: none;
  border-color: #38bdf8;
}

.sb-person-row button.sb-remove {
  background: #334155;
  border: none;
  border-radius: 6px;
  color: #94a3b8;
  font-size: 1rem;
  width: 32px;
  height: 32px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  transition: background 0.15s, color 0.15s;
}

.sb-person-row button.sb-remove:hover {
  background: #dc2626;
  color: #fff;
}

/* Buttons */
.sb-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  background: #334155;
  border: none;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 0.9rem;
  font-weight: 600;
  padding: 0.55rem 1rem;
  cursor: pointer;
  transition: background 0.15s;
}

.sb-btn:hover {
  background: #475569;
}

.sb-btn.primary {
  background: #0ea5e9;
  color: #fff;
}

.sb-btn.primary:hover {
  background: #38bdf8;
  color: #0f172a;
}

.sb-btn-row {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-top: 0.5rem;
}

/* Error */
.sb-error {
  color: #f87171;
  font-size: 0.85rem;
  margin-top: 0.25rem;
  display: none;
}

.sb-error.visible {
  display: block;
}

/* Results */
#sb-results {
  display: none;
}

#sb-results.visible {
  display: block;
}

.sb-summary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 0.75rem;
  margin-bottom: 1.25rem;
}

.sb-stat {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 0.85rem 1rem;
  text-align: center;
}

.sb-stat .stat-label {
  font-size: 0.75rem;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.3rem;
}

.sb-stat .stat-value {
  font-size: 1.4rem;
  font-weight: 700;
  color: #38bdf8;
}

.sb-stat .stat-value.accent-green {
  color: #34d399;
}

.sb-stat .stat-value.accent-amber {
  color: #fbbf24;
}

/* Per-person breakdown */
.sb-breakdown-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.92rem;
}

.sb-breakdown-table th {
  text-align: left;
  padding: 0.5rem 0.75rem;
  color: #64748b;
  font-weight: 600;
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  border-bottom: 1px solid #334155;
}

.sb-breakdown-table th:not(:first-child),
.sb-breakdown-table td:not(:first-child) {
  text-align: right;
}

.sb-breakdown-table td {
  padding: 0.55rem 0.75rem;
  border-bottom: 1px solid #1e293b;
  color: #cbd5e1;
}

.sb-breakdown-table tr:last-child td {
  border-bottom: none;
}

.sb-breakdown-table tr:hover td {
  background: #1e293b;
}

.sb-breakdown-table td.person-name {
  font-weight: 600;
  color: #e2e8f0;
}

.sb-breakdown-table td.person-total {
  font-weight: 700;
  color: #38bdf8;
}

/* Reset link */
.sb-reset-wrap {
  text-align: center;
  margin-top: 1rem;
}

.sb-reset-link {
  color: #64748b;
  font-size: 0.85rem;
  cursor: pointer;
  background: none;
  border: none;
  text-decoration: underline;
  padding: 0;
}

.sb-reset-link:hover {
  color: #94a3b8;
}

/* Cross-links */
.sb-crosslinks {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1.5rem;
  font-size: 0.9rem;
  color: #94a3b8;
  line-height: 2;
}

.sb-crosslinks a {
  color: #38bdf8;
  text-decoration: none;
}

.sb-crosslinks a:hover {
  text-decoration: underline;
}

@media (max-width: 480px) {
  .sb-card {
    padding: 1.1rem;
  }
  .sb-field {
    flex: 1 1 100%;
  }
  .sb-stat .stat-value {
    font-size: 1.2rem;
  }
}
</style>

<!-- ===== INPUTS ===== -->
<div class="sb-card">
  <h2>Bill Details</h2>

  <div class="sb-row">
    <div class="sb-field">
      <label for="sb-total">Total Bill Amount ($)</label>
      <input type="number" id="sb-total" min="0" step="0.01" placeholder="e.g. 120.00">
    </div>
    <div class="sb-field">
      <label for="sb-people">Number of People</label>
      <input type="number" id="sb-people" min="1" max="50" step="1" value="2">
    </div>
  </div>

  <div class="sb-row">
    <div class="sb-field">
      <label for="sb-tip-select">Tip Percentage</label>
      <select id="sb-tip-select">
        <option value="0">No tip (0%)</option>
        <option value="10">10%</option>
        <option value="15" selected>15%</option>
        <option value="18">18%</option>
        <option value="20">20%</option>
        <option value="custom">Custom…</option>
      </select>
    </div>
    <div class="sb-field" id="sb-custom-tip-wrap">
      <label for="sb-tip-custom">Custom Tip (%)</label>
      <input type="number" id="sb-tip-custom" min="0" max="100" step="0.1" placeholder="e.g. 12">
    </div>
  </div>

  <div class="sb-row">
    <div class="sb-field">
      <label for="sb-tax">Tax Amount ($) <span style="color:#64748b;font-weight:400;">(optional)</span></label>
      <input type="number" id="sb-tax" min="0" step="0.01" placeholder="0.00">
    </div>
    <div class="sb-field" style="justify-content:flex-end;">
      <!-- spacer -->
    </div>
  </div>

  <p id="sb-input-error" class="sb-error">Please enter a valid bill amount greater than 0.</p>
</div>

<!-- ===== SPLIT MODE ===== -->
<div class="sb-card">
  <h2>Split Mode</h2>

  <div class="sb-toggle">
    <button id="btn-equal" class="active" onclick="sbSetMode('equal')">Equal Split</button>
    <button id="btn-custom" onclick="sbSetMode('custom')">Custom Split</button>
  </div>

  <!-- Custom split section -->
  <div id="sb-custom-section" style="display:none;">
    <div style="display:flex;gap:0.5rem;align-items:center;margin-bottom:0.75rem;flex-wrap:wrap;">
      <span style="font-size:0.85rem;color:#94a3b8;">Enter each person's share amount. Remaining balance is shown below.</span>
    </div>
    <div id="sb-people-list"></div>
    <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:0.5rem;margin-bottom:0.5rem;">
      <button class="sb-btn" onclick="sbAddPerson()">+ Add Person</button>
      <span id="sb-remaining-label" style="font-size:0.88rem;color:#64748b;"></span>
    </div>
    <p id="sb-custom-error" class="sb-error">Custom amounts exceed the total bill.</p>
  </div>

  <div class="sb-btn-row">
    <button class="sb-btn primary" onclick="sbCalculate()">Calculate Split</button>
    <button class="sb-btn" onclick="sbReset()">Reset</button>
  </div>
</div>

<!-- ===== RESULTS ===== -->
<div id="sb-results">
  <div class="sb-card">
    <h2>Summary</h2>
    <div class="sb-summary-grid">
      <div class="sb-stat">
        <div class="stat-label">Total Bill</div>
        <div class="stat-value" id="res-total">—</div>
      </div>
      <div class="sb-stat">
        <div class="stat-label">Tip Total</div>
        <div class="stat-value accent-green" id="res-tip-total">—</div>
      </div>
      <div class="sb-stat">
        <div class="stat-label">Tax Total</div>
        <div class="stat-value accent-amber" id="res-tax-total">—</div>
      </div>
      <div class="sb-stat">
        <div class="stat-label">Grand Total</div>
        <div class="stat-value" id="res-grand-total" style="color:#e2e8f0;">—</div>
      </div>
    </div>

    <h2>Per Person Breakdown</h2>
    <div style="overflow-x:auto;">
      <table class="sb-breakdown-table">
        <thead>
          <tr>
            <th>Person</th>
            <th>Bill Share</th>
            <th>Tip</th>
            <th>Tax</th>
            <th>Total</th>
          </tr>
        </thead>
        <tbody id="res-table-body"></tbody>
      </table>
    </div>

    <div class="sb-reset-wrap">
      <button class="sb-reset-link" onclick="sbReset()">Start over</button>
    </div>
  </div>
</div>

<!-- ===== CROSS-LINKS ===== -->
<div class="sb-crosslinks">
  Calculate tips &rarr; <a href="/tools/tip-calculator/">Tip Calculator</a><br>
  Plan your budget &rarr; <a href="/tools/budget-planner/">50/30/20 Budget Calculator</a><br>
  Calculate percentages &rarr; <a href="/tools/percentage-calculator/">Percentage Calculator</a>
</div>

<script>
(function () {
  'use strict';

  /* ---- State ---- */
  var mode = 'equal';
  var personCount = 0;
  var personIdSeq = 0;

  /* ---- Helpers ---- */
  function fmt(n) {
    return '$' + n.toFixed(2);
  }

  function getFloat(id, fallback) {
    var v = parseFloat(document.getElementById(id).value);
    return isNaN(v) ? (fallback !== undefined ? fallback : 0) : v;
  }

  function getInt(id, fallback) {
    var v = parseInt(document.getElementById(id).value, 10);
    return isNaN(v) ? (fallback !== undefined ? fallback : 1) : v;
  }

  /* ---- Tip select ---- */
  document.getElementById('sb-tip-select').addEventListener('change', function () {
    var wrap = document.getElementById('sb-custom-tip-wrap');
    if (this.value === 'custom') {
      wrap.classList.add('visible');
    } else {
      wrap.classList.remove('visible');
    }
  });

  /* ---- Mode toggle ---- */
  window.sbSetMode = function (m) {
    mode = m;
    document.getElementById('btn-equal').classList.toggle('active', m === 'equal');
    document.getElementById('btn-custom').classList.toggle('active', m === 'custom');
    document.getElementById('sb-custom-section').style.display = (m === 'custom') ? 'block' : 'none';

    if (m === 'custom') {
      syncCustomPeople();
    }
  };

  /* ---- Custom people list ---- */
  function syncCustomPeople() {
    var n = getInt('sb-people', 2);
    if (n < 1) n = 1;
    var list = document.getElementById('sb-people-list');
    var current = list.querySelectorAll('.sb-person-row').length;

    while (current < n) {
      addPersonRow();
      current++;
    }
    while (current > n) {
      var rows = list.querySelectorAll('.sb-person-row');
      if (rows.length === 0) break;
      list.removeChild(rows[rows.length - 1]);
      current--;
    }
    updateRemaining();
  }

  document.getElementById('sb-people').addEventListener('input', function () {
    if (mode === 'custom') {
      syncCustomPeople();
    }
  });

  function addPersonRow() {
    personIdSeq++;
    var id = personIdSeq;
    var list = document.getElementById('sb-people-list');
    var div = document.createElement('div');
    div.className = 'sb-person-row';
    div.dataset.pid = id;
    div.innerHTML =
      '<input type="text" placeholder="Person ' + id + '" value="Person ' + id + '">' +
      '<input type="number" min="0" step="0.01" placeholder="0.00">' +
      '<button class="sb-remove" onclick="sbRemovePerson(' + id + ')" title="Remove">&#x2715;</button>';
    div.querySelector('input[type="number"]').addEventListener('input', updateRemaining);
    list.appendChild(div);
    personCount++;
    updateRemaining();
  }

  window.sbAddPerson = function () {
    addPersonRow();
    // update the people count field to match
    document.getElementById('sb-people').value = document.getElementById('sb-people-list').querySelectorAll('.sb-person-row').length;
    updateRemaining();
  };

  window.sbRemovePerson = function (id) {
    var list = document.getElementById('sb-people-list');
    var rows = list.querySelectorAll('.sb-person-row');
    if (rows.length <= 1) return; // keep at least one
    var row = list.querySelector('[data-pid="' + id + '"]');
    if (row) list.removeChild(row);
    document.getElementById('sb-people').value = list.querySelectorAll('.sb-person-row').length;
    updateRemaining();
  };

  function getGrandTotal() {
    var bill = getFloat('sb-total', 0);
    var tipPct = getTipPct();
    var tax = getFloat('sb-tax', 0);
    var tip = bill * tipPct / 100;
    return { bill: bill, tip: tip, tax: tax, grand: bill + tip + tax };
  }

  function getTipPct() {
    var sel = document.getElementById('sb-tip-select').value;
    if (sel === 'custom') {
      return getFloat('sb-tip-custom', 0);
    }
    return parseFloat(sel) || 0;
  }

  function updateRemaining() {
    var totals = getGrandTotal();
    var assigned = 0;
    var rows = document.getElementById('sb-people-list').querySelectorAll('.sb-person-row');
    rows.forEach(function (row) {
      var v = parseFloat(row.querySelector('input[type="number"]').value) || 0;
      assigned += v;
    });
    var remaining = totals.grand - assigned;
    var lbl = document.getElementById('sb-remaining-label');
    if (totals.grand === 0) {
      lbl.textContent = '';
    } else if (Math.abs(remaining) < 0.005) {
      lbl.textContent = 'Fully allocated';
      lbl.style.color = '#34d399';
    } else if (remaining < 0) {
      lbl.textContent = 'Over by ' + fmt(Math.abs(remaining));
      lbl.style.color = '#f87171';
    } else {
      lbl.textContent = fmt(remaining) + ' remaining';
      lbl.style.color = '#fbbf24';
    }
  }

  document.getElementById('sb-total').addEventListener('input', updateRemaining);
  document.getElementById('sb-tip-select').addEventListener('change', updateRemaining);
  document.getElementById('sb-tip-custom').addEventListener('input', updateRemaining);
  document.getElementById('sb-tax').addEventListener('input', updateRemaining);

  /* ---- Calculate ---- */
  window.sbCalculate = function () {
    var inputError = document.getElementById('sb-input-error');
    var customError = document.getElementById('sb-custom-error');
    inputError.classList.remove('visible');
    customError.classList.remove('visible');

    var bill = getFloat('sb-total', 0);
    if (bill <= 0) {
      inputError.classList.add('visible');
      return;
    }

    var tipPct = getTipPct();
    var tip = bill * tipPct / 100;
    var tax = getFloat('sb-tax', 0);
    var grand = bill + tip + tax;

    var results = [];

    if (mode === 'equal') {
      var n = getInt('sb-people', 2);
      if (n < 1) n = 1;
      var share = bill / n;
      var tipShare = tip / n;
      var taxShare = tax / n;
      var total = grand / n;
      for (var i = 1; i <= n; i++) {
        results.push({
          name: 'Person ' + i,
          share: share,
          tip: tipShare,
          tax: taxShare,
          total: total
        });
      }
    } else {
      // custom
      var rows = document.getElementById('sb-people-list').querySelectorAll('.sb-person-row');
      var totalAssigned = 0;
      var people = [];
      rows.forEach(function (row) {
        var name = row.querySelector('input[type="text"]').value.trim() || 'Person';
        var amt = parseFloat(row.querySelector('input[type="number"]').value) || 0;
        people.push({ name: name, share: amt });
        totalAssigned += amt;
      });

      // validate: assigned shares should be interpreted as bill shares
      // tip & tax distributed proportionally
      if (grand > 0 && totalAssigned > grand + 0.005) {
        customError.classList.add('visible');
        return;
      }

      // If shares are entered as raw bill shares, scale tip+tax proportionally
      var assigned = 0;
      people.forEach(function (p) { assigned += p.share; });
      var billBase = assigned > 0 ? assigned : grand;

      results = people.map(function (p) {
        var ratio = billBase > 0 ? p.share / billBase : 0;
        var myTip = tip * ratio;
        var myTax = tax * ratio;
        return {
          name: p.name,
          share: p.share,
          tip: myTip,
          tax: myTax,
          total: p.share + myTip + myTax
        };
      });
    }

    // Render summary stats
    document.getElementById('res-total').textContent = fmt(bill);
    document.getElementById('res-tip-total').textContent = fmt(tip) + (tipPct > 0 ? ' (' + tipPct + '%)' : '');
    document.getElementById('res-tax-total').textContent = fmt(tax);
    document.getElementById('res-grand-total').textContent = fmt(grand);

    // Render table
    var tbody = document.getElementById('res-table-body');
    tbody.innerHTML = '';
    results.forEach(function (r) {
      var tr = document.createElement('tr');
      tr.innerHTML =
        '<td class="person-name">' + escHtml(r.name) + '</td>' +
        '<td>' + fmt(r.share) + '</td>' +
        '<td>' + fmt(r.tip) + '</td>' +
        '<td>' + fmt(r.tax) + '</td>' +
        '<td class="person-total">' + fmt(r.total) + '</td>';
      tbody.appendChild(tr);
    });

    document.getElementById('sb-results').classList.add('visible');
    document.getElementById('sb-results').scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  };

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  /* ---- Reset ---- */
  window.sbReset = function () {
    document.getElementById('sb-total').value = '';
    document.getElementById('sb-people').value = 2;
    document.getElementById('sb-tip-select').value = '15';
    document.getElementById('sb-tip-custom').value = '';
    document.getElementById('sb-tax').value = '';
    document.getElementById('sb-custom-tip-wrap').classList.remove('visible');
    document.getElementById('sb-input-error').classList.remove('visible');
    document.getElementById('sb-custom-error').classList.remove('visible');
    document.getElementById('sb-results').classList.remove('visible');
    document.getElementById('sb-people-list').innerHTML = '';
    personIdSeq = 0;
    personCount = 0;
    sbSetMode('equal');
    updateRemaining();
  };

  /* ---- Init ---- */
  updateRemaining();
}());
</script>

</div>
