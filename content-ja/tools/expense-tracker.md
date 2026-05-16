---
title: "家計簿・支出管理ツール｜収入と支出を入力して貯蓄額を可視化【無料】"
date: 2025-05-16
description: "無料のオンライン家計簿ツール。収入・支出をカテゴリ別に記録してグラフで可視化。データはブラウザにローカル保存。会員登録不要。"
categories: ["無料ツール"]
slug: "expense-tracker"
ShowToc: false
cover:
  image: "/images/covers/expense-tracker-ja.png"
  alt: "家計簿・支出管理ツール"
---

<div id="et-app">

<style>
#et-app {
  font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  max-width: 760px;
  margin: 0 auto;
  color: #1e293b;
  box-sizing: border-box;
}
#et-app *, #et-app *::before, #et-app *::after {
  box-sizing: border-box;
}
#et-app h2 {
  font-size: 1.05rem;
  font-weight: 700;
  color: #334155;
  margin: 24px 0 10px;
  padding-bottom: 6px;
  border-bottom: 2px solid #e2e8f0;
}
#et-app .et-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 16px;
}
#et-app label {
  display: block;
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  margin-bottom: 4px;
  letter-spacing: 0.03em;
}
#et-app input, #et-app select {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  color: #1e293b;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}
#et-app input:focus, #et-app select:focus {
  border-color: #3b82f6;
}
#et-app .et-grid { display: grid; gap: 12px; }
#et-app .et-grid-2 { grid-template-columns: 1fr 1fr; }
#et-app .et-grid-3 { grid-template-columns: 1fr 1fr 1fr; }
#et-app .et-grid-4 { grid-template-columns: 1fr 1fr 1fr 1fr; }
@media (max-width: 560px) {
  #et-app .et-grid-2,
  #et-app .et-grid-3,
  #et-app .et-grid-4 { grid-template-columns: 1fr; }
}
#et-app .et-type-toggle {
  display: flex;
  border-radius: 8px;
  overflow: hidden;
  border: 1.5px solid #cbd5e1;
  width: 100%;
}
#et-app .et-type-toggle button {
  flex: 1;
  padding: 9px;
  border: none;
  background: #fff;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
  color: #64748b;
  font-family: inherit;
}
#et-app .et-type-toggle button.active-income { background: #22c55e; color: #fff; }
#et-app .et-type-toggle button.active-expense { background: #ef4444; color: #fff; }
#et-app .et-btn {
  display: inline-block;
  padding: 10px 22px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s;
  font-family: inherit;
}
#et-app .et-btn:hover { opacity: 0.85; }
#et-app .et-btn-primary { background: #3b82f6; color: #fff; }
#et-app .et-btn-sm {
  padding: 5px 12px;
  font-size: 12px;
  border-radius: 6px;
  font-weight: 700;
  border: none;
  cursor: pointer;
  font-family: inherit;
}
#et-app .et-btn-delete { background: #fee2e2; color: #dc2626; }
#et-app .et-btn-edit { background: #eff6ff; color: #2563eb; }
#et-app .et-btn-export { background: #f0fdf4; color: #16a34a; border: 1.5px solid #bbf7d0; }

/* Summary */
#et-app .et-summary-bar {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 12px;
  margin-bottom: 16px;
}
#et-app .et-summary-card {
  border-radius: 10px;
  padding: 14px 16px;
  text-align: center;
}
#et-app .et-summary-card .et-s-label {
  font-size: 11px;
  font-weight: 700;
  margin-bottom: 4px;
}
#et-app .et-summary-card .et-s-value {
  font-size: 1.3rem;
  font-weight: 800;
}
#et-app .et-income-card { background: #f0fdf4; border: 1.5px solid #bbf7d0; }
#et-app .et-income-card .et-s-label { color: #16a34a; }
#et-app .et-income-card .et-s-value { color: #15803d; }
#et-app .et-expense-card { background: #fef2f2; border: 1.5px solid #fecaca; }
#et-app .et-expense-card .et-s-label { color: #dc2626; }
#et-app .et-expense-card .et-s-value { color: #b91c1c; }
#et-app .et-balance-card { background: #eff6ff; border: 1.5px solid #bfdbfe; }
#et-app .et-balance-card .et-s-label { color: #2563eb; }
#et-app .et-balance-card .et-s-value { color: #1d4ed8; }
#et-app .et-balance-neg { background: #fef9c3; border-color: #fde68a; }
#et-app .et-balance-neg .et-s-label { color: #b45309; }
#et-app .et-balance-neg .et-s-value { color: #92400e; }

/* Filter */
#et-app .et-filter-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: flex-end;
  margin-bottom: 14px;
}
#et-app .et-filter-row > div { flex: 1; min-width: 120px; }

/* Table */
#et-app .et-table-wrap { overflow-x: auto; }
#et-app table { width: 100%; border-collapse: collapse; font-size: 13.5px; }
#et-app thead th {
  background: #f1f5f9;
  padding: 9px 12px;
  text-align: left;
  font-size: 11px;
  color: #64748b;
  font-weight: 700;
  white-space: nowrap;
}
#et-app tbody tr { border-bottom: 1px solid #f1f5f9; transition: background 0.1s; }
#et-app tbody tr:hover { background: #f8fafc; }
#et-app tbody td { padding: 9px 12px; vertical-align: middle; }
#et-app .et-badge {
  display: inline-block;
  padding: 2px 9px;
  border-radius: 99px;
  font-size: 11px;
  font-weight: 700;
}
#et-app .et-badge-income { background: #dcfce7; color: #16a34a; }
#et-app .et-badge-expense { background: #fee2e2; color: #dc2626; }
#et-app .et-amount-income { color: #16a34a; font-weight: 700; }
#et-app .et-amount-expense { color: #dc2626; font-weight: 700; }
#et-app .et-empty { text-align: center; padding: 32px; color: #94a3b8; font-size: 14px; }

/* Chart */
#et-app .et-chart-wrap { display: flex; gap: 24px; align-items: center; flex-wrap: wrap; }
#et-app canvas { display: block; }
#et-app .et-legend { flex: 1; min-width: 180px; }
#et-app .et-legend-item { display: flex; align-items: center; gap: 8px; margin-bottom: 7px; font-size: 13px; }
#et-app .et-legend-dot { width: 12px; height: 12px; border-radius: 3px; flex-shrink: 0; }
#et-app .et-legend-label { flex: 1; color: #475569; }
#et-app .et-legend-val { font-weight: 700; color: #1e293b; }
#et-app .et-cat-row { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
#et-app .et-cat-bar-bg { flex: 1; height: 8px; background: #e2e8f0; border-radius: 99px; overflow: hidden; }
#et-app .et-cat-bar-fill { height: 100%; border-radius: 99px; transition: width 0.3s; }
#et-app .et-cat-name { font-size: 13px; color: #475569; min-width: 100px; }
#et-app .et-cat-amt { font-size: 13px; font-weight: 700; color: #1e293b; min-width: 80px; text-align: right; }

/* Modal */
#et-app .et-modal-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.4);
  z-index: 9999;
  align-items: center;
  justify-content: center;
}
#et-app .et-modal-overlay.open { display: flex; }
#et-app .et-modal {
  background: #fff;
  border-radius: 12px;
  padding: 24px;
  width: 100%;
  max-width: 460px;
  margin: 16px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.2);
}
#et-app .et-modal h3 { margin: 0 0 16px; font-size: 1.1rem; color: #1e293b; }
#et-app .et-modal-actions { display: flex; gap: 10px; justify-content: flex-end; margin-top: 16px; }
#et-app .et-btn-secondary { background: #f1f5f9; color: #475569; }
</style>

<h2>取引を追加</h2>
<div class="et-card">
  <div class="et-grid et-grid-2" style="margin-bottom:12px;">
    <div>
      <label>日付</label>
      <input type="date" id="et-date">
    </div>
    <div>
      <label>種別</label>
      <div class="et-type-toggle">
        <button id="et-btn-income" onclick="etSetType('income')">+ 収入</button>
        <button id="et-btn-expense" class="active-expense" onclick="etSetType('expense')">- 支出</button>
      </div>
    </div>
  </div>
  <div class="et-grid et-grid-3" style="margin-bottom:12px;">
    <div style="grid-column:span 2;">
      <label>内容</label>
      <input type="text" id="et-desc" placeholder="例：スーパーで買い物">
    </div>
    <div>
      <label>金額（円）</label>
      <input type="number" id="et-amount" placeholder="0" min="0" step="1">
    </div>
  </div>
  <div class="et-grid et-grid-2" style="margin-bottom:14px;">
    <div>
      <label>カテゴリ</label>
      <select id="et-category">
        <option value="食費">食費</option>
        <option value="交通費">交通費</option>
        <option value="住居費">住居費</option>
        <option value="娯楽">娯楽</option>
        <option value="医療・健康">医療・健康</option>
        <option value="教育">教育</option>
        <option value="その他">その他</option>
      </select>
    </div>
    <div style="display:flex;align-items:flex-end;">
      <button class="et-btn et-btn-primary" onclick="etAddTransaction()" style="width:100%;">追加する</button>
    </div>
  </div>
</div>

<h2>月次サマリー</h2>
<div class="et-summary-bar">
  <div class="et-summary-card et-income-card">
    <div class="et-s-label">収入合計</div>
    <div class="et-s-value" id="et-total-income">¥0</div>
  </div>
  <div class="et-summary-card et-expense-card">
    <div class="et-s-label">支出合計</div>
    <div class="et-s-value" id="et-total-expense">¥0</div>
  </div>
  <div class="et-summary-card et-balance-card" id="et-balance-card">
    <div class="et-s-label">収支残高</div>
    <div class="et-s-value" id="et-balance">¥0</div>
  </div>
</div>

<div class="et-card" id="et-chart-section" style="display:none;">
  <div class="et-chart-wrap">
    <canvas id="et-donut" width="160" height="160"></canvas>
    <div class="et-legend" id="et-legend"></div>
  </div>
  <div style="margin-top:18px;" id="et-cat-breakdown"></div>
</div>

<h2>取引一覧</h2>
<div class="et-filter-row">
  <div>
    <label>月を選択</label>
    <input type="month" id="et-filter-month">
  </div>
  <div>
    <label>カテゴリ</label>
    <select id="et-filter-cat">
      <option value="">すべて</option>
      <option value="食費">食費</option>
      <option value="交通費">交通費</option>
      <option value="住居費">住居費</option>
      <option value="娯楽">娯楽</option>
      <option value="医療・健康">医療・健康</option>
      <option value="教育">教育</option>
      <option value="その他">その他</option>
    </select>
  </div>
  <div>
    <label>種別</label>
    <select id="et-filter-type">
      <option value="">すべて</option>
      <option value="income">収入</option>
      <option value="expense">支出</option>
    </select>
  </div>
  <div style="display:flex;align-items:flex-end;gap:8px;">
    <button class="et-btn et-btn-sm et-btn-export" onclick="etExportCSV()">CSV出力</button>
  </div>
</div>

<div class="et-table-wrap et-card" style="padding:0;overflow:hidden;">
  <table>
    <thead>
      <tr>
        <th>日付</th>
        <th>内容</th>
        <th>カテゴリ</th>
        <th>種別</th>
        <th style="text-align:right;">金額</th>
        <th></th>
      </tr>
    </thead>
    <tbody id="et-tbody"></tbody>
  </table>
</div>

<!-- 編集モーダル -->
<div class="et-modal-overlay" id="et-modal">
  <div class="et-modal">
    <h3>取引を編集</h3>
    <div class="et-grid et-grid-2" style="margin-bottom:12px;">
      <div>
        <label>日付</label>
        <input type="date" id="et-edit-date">
      </div>
      <div>
        <label>種別</label>
        <div class="et-type-toggle">
          <button id="et-edit-btn-income" onclick="etEditSetType('income')">+ 収入</button>
          <button id="et-edit-btn-expense" class="active-expense" onclick="etEditSetType('expense')">- 支出</button>
        </div>
      </div>
    </div>
    <div class="et-grid" style="margin-bottom:12px;">
      <div>
        <label>内容</label>
        <input type="text" id="et-edit-desc">
      </div>
    </div>
    <div class="et-grid et-grid-2" style="margin-bottom:12px;">
      <div>
        <label>金額（円）</label>
        <input type="number" id="et-edit-amount" min="0" step="1">
      </div>
      <div>
        <label>カテゴリ</label>
        <select id="et-edit-category">
          <option value="食費">食費</option>
          <option value="交通費">交通費</option>
          <option value="住居費">住居費</option>
          <option value="娯楽">娯楽</option>
          <option value="医療・健康">医療・健康</option>
          <option value="教育">教育</option>
          <option value="その他">その他</option>
        </select>
      </div>
    </div>
    <div class="et-modal-actions">
      <button class="et-btn et-btn-sm et-btn-secondary" onclick="etCloseModal()">キャンセル</button>
      <button class="et-btn et-btn-sm et-btn-primary" onclick="etSaveEdit()">保存する</button>
    </div>
  </div>
</div>

<script>
(function () {
  'use strict';

  var STORAGE_KEY = 'et_transactions_ja_v1';
  var COLORS = {
    '食費':      '#f97316',
    '交通費':    '#3b82f6',
    '住居費':    '#8b5cf6',
    '娯楽':      '#ec4899',
    '医療・健康': '#10b981',
    '教育':      '#f59e0b',
    'その他':    '#94a3b8'
  };

  var transactions = [];
  var currentType = 'expense';
  var editId = null;
  var editType = 'expense';

  (function init() {
    var stored = localStorage.getItem(STORAGE_KEY);
    if (stored) {
      try { transactions = JSON.parse(stored); } catch (e) { transactions = []; }
    }
    var today = new Date().toISOString().slice(0, 10);
    document.getElementById('et-date').value = today;
    document.getElementById('et-filter-month').value = today.slice(0, 7);

    document.getElementById('et-filter-month').addEventListener('change', etRender);
    document.getElementById('et-filter-cat').addEventListener('change', etRender);
    document.getElementById('et-filter-type').addEventListener('change', etRender);

    // Set default type UI
    etSetType('expense');
    etRender();
  })();

  function etSave() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(transactions));
  }

  function etSetType(type) {
    currentType = type;
    document.getElementById('et-btn-income').className = type === 'income' ? 'active-income' : '';
    document.getElementById('et-btn-expense').className = type === 'expense' ? 'active-expense' : '';
  }

  function etEditSetType(type) {
    editType = type;
    document.getElementById('et-edit-btn-income').className = type === 'income' ? 'active-income' : '';
    document.getElementById('et-edit-btn-expense').className = type === 'expense' ? 'active-expense' : '';
  }

  function etAddTransaction() {
    var date = document.getElementById('et-date').value;
    var desc = document.getElementById('et-desc').value.trim();
    var amount = parseFloat(document.getElementById('et-amount').value);
    var category = document.getElementById('et-category').value;

    if (!date) { alert('日付を入力してください。'); return; }
    if (!desc) { alert('内容を入力してください。'); return; }
    if (isNaN(amount) || amount <= 0) { alert('金額を正しく入力してください。'); return; }

    transactions.push({
      id: Date.now() + Math.random(),
      date: date,
      desc: desc,
      amount: amount,
      category: category,
      type: currentType
    });

    etSave();
    document.getElementById('et-desc').value = '';
    document.getElementById('et-amount').value = '';
    etRender();
  }

  function etDeleteTransaction(id) {
    transactions = transactions.filter(function (t) { return t.id !== id; });
    etSave();
    etRender();
  }

  function etOpenEdit(id) {
    var t = transactions.find(function (x) { return x.id === id; });
    if (!t) return;
    editId = id;
    document.getElementById('et-edit-date').value = t.date;
    document.getElementById('et-edit-desc').value = t.desc;
    document.getElementById('et-edit-amount').value = t.amount;
    document.getElementById('et-edit-category').value = t.category;
    etEditSetType(t.type);
    document.getElementById('et-modal').classList.add('open');
  }

  function etCloseModal() {
    document.getElementById('et-modal').classList.remove('open');
    editId = null;
  }

  function etSaveEdit() {
    if (editId === null) return;
    var date = document.getElementById('et-edit-date').value;
    var desc = document.getElementById('et-edit-desc').value.trim();
    var amount = parseFloat(document.getElementById('et-edit-amount').value);
    var category = document.getElementById('et-edit-category').value;

    if (!date || !desc || isNaN(amount) || amount <= 0) { alert('すべての項目を正しく入力してください。'); return; }

    transactions = transactions.map(function (t) {
      if (t.id === editId) {
        return { id: t.id, date: date, desc: desc, amount: amount, category: category, type: editType };
      }
      return t;
    });
    etSave();
    etCloseModal();
    etRender();
  }

  function etGetFiltered() {
    var month = document.getElementById('et-filter-month').value;
    var cat = document.getElementById('et-filter-cat').value;
    var type = document.getElementById('et-filter-type').value;

    return transactions.filter(function (t) {
      if (month && t.date.slice(0, 7) !== month) return false;
      if (cat && t.category !== cat) return false;
      if (type && t.type !== type) return false;
      return true;
    }).sort(function (a, b) { return b.date.localeCompare(a.date); });
  }

  function fmt(n) {
    return '¥' + Math.round(n).toLocaleString('ja-JP');
  }

  function etRender() {
    var filtered = etGetFiltered();

    var month = document.getElementById('et-filter-month').value;
    var monthTxns = month
      ? transactions.filter(function (t) { return t.date.slice(0, 7) === month; })
      : transactions;

    var totalIncome = monthTxns.filter(function (t) { return t.type === 'income'; })
      .reduce(function (s, t) { return s + t.amount; }, 0);
    var totalExpense = monthTxns.filter(function (t) { return t.type === 'expense'; })
      .reduce(function (s, t) { return s + t.amount; }, 0);
    var balance = totalIncome - totalExpense;

    document.getElementById('et-total-income').textContent = fmt(totalIncome);
    document.getElementById('et-total-expense').textContent = fmt(totalExpense);
    document.getElementById('et-balance').textContent = fmt(balance);

    var balCard = document.getElementById('et-balance-card');
    balCard.className = 'et-summary-card ' + (balance < 0 ? 'et-balance-neg' : 'et-balance-card');

    var expenseTxns = monthTxns.filter(function (t) { return t.type === 'expense'; });
    etRenderChart(expenseTxns);

    var tbody = document.getElementById('et-tbody');
    if (filtered.length === 0) {
      tbody.innerHTML = '<tr><td colspan="6" class="et-empty">取引がありません。上から追加してください。</td></tr>';
      return;
    }

    var html = '';
    filtered.forEach(function (t) {
      html += '<tr>';
      html += '<td>' + t.date + '</td>';
      html += '<td>' + escHtml(t.desc) + '</td>';
      html += '<td><span class="et-badge" style="background:' + hexBg(COLORS[t.category] || '#94a3b8') + ';color:' + (COLORS[t.category] || '#94a3b8') + ';">' + escHtml(t.category) + '</span></td>';
      html += '<td><span class="et-badge ' + (t.type === 'income' ? 'et-badge-income' : 'et-badge-expense') + '">' + (t.type === 'income' ? '収入' : '支出') + '</span></td>';
      html += '<td style="text-align:right;" class="' + (t.type === 'income' ? 'et-amount-income' : 'et-amount-expense') + '">' + (t.type === 'income' ? '+' : '-') + fmt(t.amount) + '</td>';
      html += '<td style="white-space:nowrap;text-align:right;">';
      html += '<button class="et-btn et-btn-sm et-btn-edit" onclick="etOpenEdit(' + t.id + ')" style="margin-right:4px;">編集</button>';
      html += '<button class="et-btn et-btn-sm et-btn-delete" onclick="etDeleteTransaction(' + t.id + ')">削除</button>';
      html += '</td>';
      html += '</tr>';
    });
    tbody.innerHTML = html;
  }

  function hexBg(hex) {
    var map = {
      '#f97316': '#fff7ed',
      '#3b82f6': '#eff6ff',
      '#8b5cf6': '#f5f3ff',
      '#ec4899': '#fdf2f8',
      '#10b981': '#ecfdf5',
      '#f59e0b': '#fffbeb',
      '#94a3b8': '#f1f5f9'
    };
    return map[hex] || '#f1f5f9';
  }

  function etRenderChart(expenseTxns) {
    var section = document.getElementById('et-chart-section');
    if (expenseTxns.length === 0) { section.style.display = 'none'; return; }
    section.style.display = '';

    var catMap = {};
    expenseTxns.forEach(function (t) {
      catMap[t.category] = (catMap[t.category] || 0) + t.amount;
    });
    var total = Object.values(catMap).reduce(function (s, v) { return s + v; }, 0);
    var entries = Object.entries(catMap).sort(function (a, b) { return b[1] - a[1]; });

    var canvas = document.getElementById('et-donut');
    var ctx = canvas.getContext('2d');
    var cx = 80, cy = 80, r = 68, innerR = 44;
    ctx.clearRect(0, 0, 160, 160);

    var startAngle = -Math.PI / 2;
    entries.forEach(function (entry) {
      var slice = (entry[1] / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, startAngle, startAngle + slice);
      ctx.closePath();
      ctx.fillStyle = COLORS[entry[0]] || '#94a3b8';
      ctx.fill();
      startAngle += slice;
    });

    ctx.beginPath();
    ctx.arc(cx, cy, innerR, 0, 2 * Math.PI);
    ctx.fillStyle = '#fff';
    ctx.fill();

    ctx.fillStyle = '#1e293b';
    ctx.font = 'bold 12px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(fmt(total), cx, cy);

    var legendHtml = '';
    entries.forEach(function (entry) {
      var pct = ((entry[1] / total) * 100).toFixed(1);
      legendHtml += '<div class="et-legend-item">';
      legendHtml += '<div class="et-legend-dot" style="background:' + (COLORS[entry[0]] || '#94a3b8') + ';"></div>';
      legendHtml += '<span class="et-legend-label">' + escHtml(entry[0]) + ' <span style="color:#94a3b8;font-size:11px;">(' + pct + '%)</span></span>';
      legendHtml += '<span class="et-legend-val">' + fmt(entry[1]) + '</span>';
      legendHtml += '</div>';
    });
    document.getElementById('et-legend').innerHTML = legendHtml;

    var breakHtml = '<div style="font-size:12px;font-weight:700;color:#64748b;margin-bottom:10px;">カテゴリ別内訳</div>';
    entries.forEach(function (entry) {
      var pct = (entry[1] / total) * 100;
      breakHtml += '<div class="et-cat-row">';
      breakHtml += '<span class="et-cat-name">' + escHtml(entry[0]) + '</span>';
      breakHtml += '<div class="et-cat-bar-bg"><div class="et-cat-bar-fill" style="width:' + pct.toFixed(1) + '%;background:' + (COLORS[entry[0]] || '#94a3b8') + ';"></div></div>';
      breakHtml += '<span class="et-cat-amt">' + fmt(entry[1]) + '</span>';
      breakHtml += '</div>';
    });
    document.getElementById('et-cat-breakdown').innerHTML = breakHtml;
  }

  function etExportCSV() {
    var filtered = etGetFiltered();
    if (filtered.length === 0) { alert('出力するデータがありません。'); return; }
    var rows = [['日付', '内容', 'カテゴリ', '種別', '金額']];
    filtered.forEach(function (t) {
      rows.push([t.date, '"' + t.desc.replace(/"/g, '""') + '"', t.category, t.type === 'income' ? '収入' : '支出', Math.round(t.amount)]);
    });
    var bom = '\uFEFF';
    var csv = bom + rows.map(function (r) { return r.join(','); }).join('\n');
    var blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url;
    a.download = 'kakeibo.csv';
    a.click();
    URL.revokeObjectURL(url);
  }

  function escHtml(str) {
    return String(str)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  window.etSetType = etSetType;
  window.etEditSetType = etEditSetType;
  window.etAddTransaction = etAddTransaction;
  window.etDeleteTransaction = etDeleteTransaction;
  window.etOpenEdit = etOpenEdit;
  window.etCloseModal = etCloseModal;
  window.etSaveEdit = etSaveEdit;
  window.etExportCSV = etExportCSV;
})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0 0 4px;font-size:14px;color:#0369a1;font-weight:600;">事業の経費管理はfreeeでかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、交際費・交通費などの経費精算もクラウドで自動化。確定申告もラクラク。無料トライアル実施中。</span><br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:10px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

## 関連ツール

- [予算プランナー](/ja/tools/budget-planner/) — 50/30/20ルールで月の予算を自動配分
- [割り勘計算ツール](/ja/tools/split-bill-calculator/) — 飲み会・食事の会計を均等・傾斜配分

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
