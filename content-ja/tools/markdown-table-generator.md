---
title: "マークダウン表作成ツール — 無料オンラインツール"
date: 2025-07-04
description: "マークダウン形式の表を瞬時に作成できる無料オンラインツールです。行・列の追加削除、列ごとの整列指定、CSV/TSVインポート、ワンクリックコピーに対応しています。"
categories: ["無料ツール"]
slug: "markdown-table-generator"
aliases:
  - "/ja/tools/markdown-table-generator/"
  - "/ja/tools/html-table-generator/"
ShowToc: false
cover:
  image: "/images/covers/markdown-table-generator-ja.png"
  alt: "マークダウン表作成ツール"
---

<div id="mdtable-app">

<style>
#mdtable-app *,
#mdtable-app *::before,
#mdtable-app *::after {
  box-sizing: border-box;
}
#mdtable-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", "Meiryo", sans-serif;
  color: #1e1e2e;
  max-width: 900px;
  margin: 0 auto;
}
#mdtable-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 1.5rem 0 0.5rem;
  color: #4f46e5;
  letter-spacing: 0.01em;
}
#mdtable-app .toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
  align-items: center;
}
#mdtable-app .toolbar label {
  font-size: 0.85rem;
  color: #555;
}
#mdtable-app .toolbar input[type="number"] {
  width: 3.5rem;
  padding: 0.3rem 0.4rem;
  border: 1px solid #c7d2fe;
  border-radius: 6px;
  font-size: 0.9rem;
  text-align: center;
}
#mdtable-app .btn {
  display: inline-flex;
  align-items: center;
  gap: 0.3rem;
  padding: 0.4rem 0.85rem;
  border: none;
  border-radius: 7px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#mdtable-app .btn:active { transform: scale(0.97); }
#mdtable-app .btn-primary {
  background: #4f46e5;
  color: #fff;
}
#mdtable-app .btn-primary:hover { background: #4338ca; }
#mdtable-app .btn-secondary {
  background: #e0e7ff;
  color: #4f46e5;
}
#mdtable-app .btn-secondary:hover { background: #c7d2fe; }
#mdtable-app .btn-danger {
  background: #fee2e2;
  color: #b91c1c;
}
#mdtable-app .btn-danger:hover { background: #fecaca; }
#mdtable-app .btn-success {
  background: #d1fae5;
  color: #065f46;
}
#mdtable-app .btn-success:hover { background: #a7f3d0; }
#mdtable-app .table-wrap {
  overflow-x: auto;
  border: 1px solid #e0e7ff;
  border-radius: 10px;
  margin-bottom: 1rem;
}
#mdtable-app table.editor-table {
  border-collapse: collapse;
  width: 100%;
  min-width: 400px;
}
#mdtable-app table.editor-table th,
#mdtable-app table.editor-table td {
  border: 1px solid #c7d2fe;
  padding: 0;
}
#mdtable-app table.editor-table th {
  background: #eef2ff;
}
#mdtable-app .cell-input {
  width: 100%;
  min-width: 80px;
  padding: 0.45rem 0.55rem;
  border: none;
  outline: none;
  background: transparent;
  font-size: 0.9rem;
  font-family: inherit;
  color: #1e1e2e;
  resize: none;
  overflow: hidden;
  line-height: 1.4;
}
#mdtable-app .cell-input:focus {
  background: #f5f3ff;
}
#mdtable-app .align-row th {
  background: #f5f3ff;
  padding: 4px 6px;
  text-align: center;
}
#mdtable-app .align-select {
  padding: 2px 4px;
  border: 1px solid #c7d2fe;
  border-radius: 5px;
  font-size: 0.78rem;
  background: #fff;
  color: #4f46e5;
  cursor: pointer;
}
#mdtable-app .col-ctrl-row th {
  background: #f5f3ff;
  padding: 4px 6px;
  text-align: center;
}
#mdtable-app .output-area {
  position: relative;
}
#mdtable-app textarea#md-output {
  width: 100%;
  min-height: 140px;
  padding: 0.75rem 1rem;
  border: 1px solid #c7d2fe;
  border-radius: 10px;
  font-family: "Fira Mono", "Courier New", monospace;
  font-size: 0.88rem;
  line-height: 1.6;
  background: #f8f7ff;
  color: #1e1e2e;
  resize: vertical;
  outline: none;
}
#mdtable-app .copy-btn-wrap {
  display: flex;
  justify-content: flex-end;
  margin-top: 0.4rem;
}
#mdtable-app .import-area {
  margin-top: 1rem;
}
#mdtable-app textarea#csv-input {
  width: 100%;
  min-height: 80px;
  padding: 0.6rem 0.8rem;
  border: 1px solid #c7d2fe;
  border-radius: 8px;
  font-family: "Fira Mono", "Courier New", monospace;
  font-size: 0.85rem;
  color: #333;
  resize: vertical;
  outline: none;
}
#mdtable-app .import-controls {
  display: flex;
  gap: 0.5rem;
  margin-top: 0.4rem;
  flex-wrap: wrap;
  align-items: center;
}
#mdtable-app .status-msg {
  font-size: 0.82rem;
  color: #059669;
  font-weight: 600;
  min-height: 1.2em;
}
#mdtable-app .divider {
  border: none;
  border-top: 1px solid #e0e7ff;
  margin: 1.5rem 0;
}
#mdtable-app .freee-cta {
  margin-top: 2rem;
  padding: 1.2rem 1.4rem;
  background: linear-gradient(135deg, #eef2ff 0%, #f5f3ff 100%);
  border: 1.5px solid #c7d2fe;
  border-radius: 12px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 1rem;
}
#mdtable-app .freee-cta-text {
  flex: 1;
  min-width: 200px;
}
#mdtable-app .freee-cta-text strong {
  display: block;
  font-size: 1rem;
  color: #4f46e5;
  margin-bottom: 0.3rem;
}
#mdtable-app .freee-cta-text p {
  margin: 0;
  font-size: 0.85rem;
  color: #555;
  line-height: 1.5;
}
#mdtable-app .freee-cta-btn {
  display: inline-block;
  padding: 0.6rem 1.4rem;
  background: #4f46e5;
  color: #fff;
  font-weight: 700;
  font-size: 0.92rem;
  border-radius: 8px;
  text-decoration: none;
  white-space: nowrap;
  transition: background 0.15s;
}
#mdtable-app .freee-cta-btn:hover { background: #4338ca; }
</style>

<div class="toolbar">
  <label>行数&nbsp;<input type="number" id="row-count" value="3" min="1" max="50"></label>
  <label>列数&nbsp;<input type="number" id="col-count" value="3" min="1" max="20"></label>
  <button class="btn btn-primary" onclick="mdtableApp.applyDimensions()">適用</button>
  <button class="btn btn-secondary" onclick="mdtableApp.addRow()">＋ 行追加</button>
  <button class="btn btn-secondary" onclick="mdtableApp.addCol()">＋ 列追加</button>
  <button class="btn btn-danger" onclick="mdtableApp.removeRow()">－ 行削除</button>
  <button class="btn btn-danger" onclick="mdtableApp.removeCol()">－ 列削除</button>
</div>

<div class="table-wrap">
  <table class="editor-table" id="editor-table">
    <thead id="editor-thead"></thead>
    <tbody id="editor-tbody"></tbody>
  </table>
</div>

<h2>マークダウン出力</h2>
<div class="output-area">
  <textarea id="md-output" readonly></textarea>
  <div class="copy-btn-wrap">
    <button class="btn btn-success" onclick="mdtableApp.copyOutput()">マークダウンをコピー</button>
    <span class="status-msg" id="copy-status" style="margin-left:0.6rem;line-height:2.2;"></span>
  </div>
</div>

<hr class="divider">

<h2>CSV / TSV インポート</h2>
<p style="font-size:0.88rem;color:#555;margin:0 0 0.4rem;">CSVまたはTSV形式のデータを貼り付けるか、クリップボードから取得してください。区切り文字は自動判別されます。</p>
<div class="import-area">
  <textarea id="csv-input" placeholder="名前, 年齢, 都市&#10;田中, 32, 東京&#10;鈴木, 28, 大阪"></textarea>
  <div class="import-controls">
    <button class="btn btn-primary" onclick="mdtableApp.importCSV()">インポート</button>
    <button class="btn btn-secondary" onclick="mdtableApp.pasteFromClipboard()">クリップボードから貼り付け</button>
    <span class="status-msg" id="import-status"></span>
  </div>
</div>

<div class="freee-cta">
  <div class="freee-cta-text">
    <strong>freee で会計・経費管理を自動化しませんか？</strong>
    <p>表でまとめた経費データも、freee なら自動で仕訳・集計。中小企業・フリーランスに最適なクラウド会計ソフトです。</p>
  </div>
  <a class="freee-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee を無料で試す</a>
</div>

</div><!-- #mdtable-app -->

<script>
(function () {
  const state = {
    rows: 3,
    cols: 3,
    data: [],
    aligns: [],
  };

  function initData(rows, cols, oldData, oldAligns) {
    const data = [];
    const aligns = [];
    for (let c = 0; c < cols; c++) {
      aligns.push((oldAligns && oldAligns[c]) ? oldAligns[c] : 'left');
    }
    for (let r = 0; r < rows; r++) {
      const row = [];
      for (let c = 0; c < cols; c++) {
        const oldVal = (oldData && oldData[r] && oldData[r][c] !== undefined) ? oldData[r][c] : '';
        row.push(oldVal);
      }
      data.push(row);
    }
    state.data = data;
    state.aligns = aligns;
    state.rows = rows;
    state.cols = cols;
  }

  function buildTable() {
    const thead = document.getElementById('editor-thead');
    const tbody = document.getElementById('editor-tbody');
    thead.innerHTML = '';
    tbody.innerHTML = '';

    // --- 整列制御行 ---
    const alignRow = document.createElement('tr');
    alignRow.className = 'align-row';
    for (let c = 0; c < state.cols; c++) {
      const th = document.createElement('th');
      const sel = document.createElement('select');
      sel.className = 'align-select';
      sel.title = '列の整列';
      const alignLabels = { left: '左揃え', center: '中央揃え', right: '右揃え' };
      ['left', 'center', 'right'].forEach(a => {
        const opt = document.createElement('option');
        opt.value = a;
        opt.textContent = alignLabels[a];
        if (state.aligns[c] === a) opt.selected = true;
        sel.appendChild(opt);
      });
      (function(col) {
        sel.addEventListener('change', function () {
          state.aligns[col] = this.value;
          renderOutput();
        });
      })(c);
      th.appendChild(sel);
      alignRow.appendChild(th);
    }
    thead.appendChild(alignRow);

    // --- ヘッダー行 (row 0) ---
    const headerRow = document.createElement('tr');
    for (let c = 0; c < state.cols; c++) {
      const th = document.createElement('th');
      th.appendChild(makeInput(0, c, true));
      headerRow.appendChild(th);
    }
    thead.appendChild(headerRow);

    // --- ボディ行 ---
    for (let r = 1; r < state.rows; r++) {
      const tr = document.createElement('tr');
      for (let c = 0; c < state.cols; c++) {
        const td = document.createElement('td');
        td.appendChild(makeInput(r, c, false));
        tr.appendChild(td);
      }
      tbody.appendChild(tr);
    }

    renderOutput();
  }

  function makeInput(r, c, isHeader) {
    const el = document.createElement('textarea');
    el.className = 'cell-input';
    el.rows = 1;
    el.placeholder = isHeader ? '見出し ' + (c + 1) : '';
    el.value = state.data[r][c] || '';
    el.addEventListener('input', function () {
      state.data[r][c] = this.value;
      autoResize(this);
      renderOutput();
    });
    el.addEventListener('keydown', function (e) {
      if (e.key === 'Tab') {
        e.preventDefault();
        const inputs = document.querySelectorAll('#editor-table .cell-input');
        const idx = Array.from(inputs).indexOf(this);
        if (idx < inputs.length - 1) inputs[idx + 1].focus();
      }
    });
    setTimeout(() => autoResize(el), 0);
    return el;
  }

  function autoResize(el) {
    el.style.height = 'auto';
    el.style.height = el.scrollHeight + 'px';
  }

  function alignSep(a) {
    if (a === 'center') return ':---:';
    if (a === 'right') return '---:';
    return ':---';
  }

  function escCell(s) {
    return s.replace(/\|/g, '\\|').replace(/\n/g, ' ');
  }

  function renderOutput() {
    if (state.rows < 1 || state.cols < 1) {
      document.getElementById('md-output').value = '';
      return;
    }
    const lines = [];
    lines.push('| ' + state.data[0].map(escCell).join(' | ') + ' |');
    lines.push('| ' + state.aligns.map(alignSep).join(' | ') + ' |');
    for (let r = 1; r < state.rows; r++) {
      lines.push('| ' + state.data[r].map(escCell).join(' | ') + ' |');
    }
    document.getElementById('md-output').value = lines.join('\n');
  }

  function syncDimensionInputs() {
    document.getElementById('row-count').value = state.rows;
    document.getElementById('col-count').value = state.cols;
  }

  const app = {
    applyDimensions() {
      const rows = Math.max(1, Math.min(50, parseInt(document.getElementById('row-count').value) || 1));
      const cols = Math.max(1, Math.min(20, parseInt(document.getElementById('col-count').value) || 1));
      initData(rows, cols, state.data, state.aligns);
      buildTable();
      syncDimensionInputs();
    },
    addRow() {
      const newRow = Array(state.cols).fill('');
      state.data.push(newRow);
      state.rows++;
      buildTable();
      syncDimensionInputs();
    },
    addCol() {
      state.data.forEach(row => row.push(''));
      state.aligns.push('left');
      state.cols++;
      buildTable();
      syncDimensionInputs();
    },
    removeRow() {
      if (state.rows <= 1) return;
      state.data.pop();
      state.rows--;
      buildTable();
      syncDimensionInputs();
    },
    removeCol() {
      if (state.cols <= 1) return;
      state.data.forEach(row => row.pop());
      state.aligns.pop();
      state.cols--;
      buildTable();
      syncDimensionInputs();
    },
    copyOutput() {
      const out = document.getElementById('md-output').value;
      if (!out) return;
      const statusEl = document.getElementById('copy-status');
      if (navigator.clipboard && navigator.clipboard.writeText) {
        navigator.clipboard.writeText(out).then(() => {
          statusEl.textContent = 'コピーしました！';
          setTimeout(() => { statusEl.textContent = ''; }, 2000);
        });
      } else {
        document.getElementById('md-output').select();
        document.execCommand('copy');
        statusEl.textContent = 'コピーしました！';
        setTimeout(() => { statusEl.textContent = ''; }, 2000);
      }
    },
    importCSV() {
      const raw = document.getElementById('csv-input').value.trim();
      if (!raw) return;
      parseAndLoad(raw, 'import-status');
    },
    pasteFromClipboard() {
      const statusEl = document.getElementById('import-status');
      if (navigator.clipboard && navigator.clipboard.readText) {
        navigator.clipboard.readText().then(text => {
          if (!text.trim()) { statusEl.textContent = 'クリップボードが空です。'; return; }
          document.getElementById('csv-input').value = text;
          parseAndLoad(text.trim(), 'import-status');
        }).catch(() => {
          statusEl.textContent = 'クリップボードへのアクセスが拒否されました。手動で貼り付けてください。';
        });
      } else {
        statusEl.textContent = 'クリップボード API が利用できません。下のテキストエリアに貼り付けてください。';
      }
    },
  };

  function detectDelimiter(firstLine) {
    const tabs = (firstLine.match(/\t/g) || []).length;
    const commas = (firstLine.match(/,/g) || []).length;
    return tabs >= commas ? '\t' : ',';
  }

  function parseAndLoad(raw, statusId) {
    const statusEl = document.getElementById(statusId);
    const lines = raw.split(/\r?\n/).filter(l => l.trim() !== '');
    if (lines.length === 0) { statusEl.textContent = 'データが見つかりません。'; return; }
    const delim = detectDelimiter(lines[0]);
    const parsed = lines.map(l => l.split(delim).map(c => c.trim()));
    const cols = Math.max(...parsed.map(r => r.length));
    const rows = parsed.length;
    const padded = parsed.map(r => { while (r.length < cols) r.push(''); return r; });
    initData(rows, cols, padded, null);
    buildTable();
    syncDimensionInputs();
    statusEl.textContent = rows + ' 行 × ' + cols + ' 列を読み込みました。';
    setTimeout(() => { statusEl.textContent = ''; }, 3000);
  }

  // 初期化
  initData(3, 3, null, null);
  buildTable();

  window.mdtableApp = app;
})();
</script>
