---
title: "HTMLテーブルジェネレーター — 無料オンラインツール"
date: 2025-12-12
description: "ビジュアルスプレッドシートエディターでHTMLテーブルを生成。行・列の追加、スタイリング、CSVインポート対応。HTMLコードをワンクリックコピー。"
categories: ["無料ツール"]
slug: "html-table-generator"
ShowToc: false
aliases:
  - "/ja/tools/html-table-generator/"
  - "/ja/tools/html-table-generator/"
cover:
  image: "/images/covers/html-table-generator-ja.png"
  alt: "HTMLテーブルジェネレーター"
---

ビジュアルエディターでHTMLテーブルを作成 — コード不要。セルをクリックして編集、行や列の追加・削除、スタイルの選択、CSVデータのインポートができます。完成したHTMLコードをワンクリックでコピー。

<div id="ht-app">

<style>
/* ── スコープ: すべてのスタイルは #ht-app プレフィックス付き ── */
#ht-app {
  font-family: system-ui, -apple-system, 'Hiragino Sans', 'Yu Gothic UI', sans-serif;
  font-size: 14px;
  color: #1a1a1a;
  max-width: 100%;
}
#ht-app * { box-sizing: border-box; }

/* ツールバー */
#ht-app .ht-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 12px;
}
#ht-app .ht-btn {
  padding: 6px 12px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  background: #fff;
  cursor: pointer;
  font-size: 13px;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#ht-app .ht-btn:hover { background: #f3f4f6; border-color: #9ca3af; }
#ht-app .ht-btn.ht-btn-primary {
  background: #2563eb; color: #fff; border-color: #2563eb;
}
#ht-app .ht-btn.ht-btn-primary:hover { background: #1d4ed8; border-color: #1d4ed8; }
#ht-app .ht-btn.ht-btn-danger {
  background: #fff; color: #dc2626; border-color: #fca5a5;
}
#ht-app .ht-btn.ht-btn-danger:hover { background: #fef2f2; }
#ht-app .ht-btn.ht-active {
  background: #eff6ff; border-color: #2563eb; color: #2563eb;
}

/* セクションラベル */
#ht-app .ht-section { margin-bottom: 12px; }
#ht-app .ht-section-title {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #6b7280;
  margin-bottom: 6px;
}

/* オプション行 */
#ht-app .ht-options {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: center;
  margin-bottom: 12px;
  padding: 10px 12px;
  background: #f9fafb;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
}
#ht-app .ht-option-group {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
}
#ht-app .ht-option-group label { cursor: pointer; user-select: none; }
#ht-app .ht-select {
  padding: 4px 8px;
  border: 1px solid #d1d5db;
  border-radius: 5px;
  background: #fff;
  font-size: 13px;
  cursor: pointer;
}

/* スプレッドシートグリッド */
#ht-app .ht-grid-wrap {
  overflow-x: auto;
  margin-bottom: 14px;
  border: 1px solid #d1d5db;
  border-radius: 8px;
}
#ht-app .ht-grid {
  border-collapse: collapse;
  min-width: 100%;
}
#ht-app .ht-grid th,
#ht-app .ht-grid td {
  border: 1px solid #d1d5db;
  padding: 0;
  min-width: 80px;
  max-width: 240px;
  position: relative;
}
#ht-app .ht-grid .ht-col-ctrl td {
  background: #f3f4f6;
  text-align: center;
  font-size: 11px;
  color: #6b7280;
  padding: 4px 2px;
  cursor: pointer;
  white-space: nowrap;
}
#ht-app .ht-grid .ht-col-ctrl td:hover { background: #fef2f2; color: #dc2626; }

#ht-app .ht-cell-input {
  width: 100%;
  min-height: 32px;
  padding: 6px 8px;
  border: none;
  outline: none;
  background: transparent;
  font-size: 13px;
  font-family: inherit;
  resize: none;
  display: block;
}
#ht-app .ht-cell-input:focus {
  background: #eff6ff;
  outline: 2px solid #2563eb;
  outline-offset: -2px;
  border-radius: 2px;
}
#ht-app .ht-header-cell .ht-cell-input {
  font-weight: 600;
  background: #f0f9ff;
}
#ht-app .ht-header-cell { background: #e0f2fe; }
#ht-app .ht-cell-selected { outline: 2px solid #f59e0b !important; outline-offset: -2px; }

/* インポートエリア */
#ht-app .ht-import-area {
  width: 100%;
  height: 80px;
  padding: 8px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-size: 12px;
  font-family: monospace;
  resize: vertical;
  background: #fff;
}
#ht-app .ht-import-area:focus { outline: 2px solid #2563eb; border-color: transparent; }

/* プレビューエリア */
#ht-app .ht-preview-wrap {
  overflow-x: auto;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  padding: 16px;
  background: #fff;
  margin-bottom: 14px;
}

/* コード出力 */
#ht-app .ht-code-wrap {
  position: relative;
  margin-bottom: 8px;
}
#ht-app .ht-code-output {
  width: 100%;
  height: 160px;
  padding: 10px;
  font-family: 'Courier New', monospace;
  font-size: 12px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  background: #1e1e2e;
  color: #cdd6f4;
  resize: vertical;
}
#ht-app .ht-copy-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  padding: 4px 10px;
  font-size: 12px;
  background: #374151;
  color: #f3f4f6;
  border: 1px solid #4b5563;
  border-radius: 4px;
  cursor: pointer;
  transition: background 0.15s;
}
#ht-app .ht-copy-btn:hover { background: #4b5563; }
#ht-app .ht-copy-btn.ht-copied { background: #16a34a; border-color: #16a34a; }

/* タブ */
#ht-app .ht-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e5e7eb;
  margin-bottom: 10px;
}
#ht-app .ht-tab {
  padding: 7px 16px;
  font-size: 13px;
  cursor: pointer;
  border: none;
  background: none;
  color: #6b7280;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s;
}
#ht-app .ht-tab:hover { color: #111; }
#ht-app .ht-tab.ht-tab-active { color: #2563eb; border-bottom-color: #2563eb; font-weight: 600; }

/* トースト通知 */
#ht-app .ht-toast {
  display: none;
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  background: #111827;
  color: #f9fafb;
  padding: 10px 20px;
  border-radius: 8px;
  font-size: 13px;
  z-index: 9999;
  box-shadow: 0 4px 12px rgba(0,0,0,0.3);
  pointer-events: none;
}
#ht-app .ht-toast.ht-show { display: block; }

/* 区切り線 */
#ht-app .ht-divider {
  border: none;
  border-top: 1px solid #e5e7eb;
  margin: 14px 0;
}

/* freee CTAバナー */
#ht-app .ht-freee-cta {
  margin-top: 24px;
  padding: 18px 20px;
  background: linear-gradient(135deg, #e8f5e9 0%, #f0fdf4 100%);
  border: 1px solid #86efac;
  border-radius: 10px;
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}
#ht-app .ht-freee-cta-icon {
  font-size: 32px;
  flex-shrink: 0;
}
#ht-app .ht-freee-cta-body {
  flex: 1;
  min-width: 180px;
}
#ht-app .ht-freee-cta-body strong {
  display: block;
  font-size: 15px;
  color: #166534;
  margin-bottom: 4px;
}
#ht-app .ht-freee-cta-body p {
  font-size: 13px;
  color: #15803d;
  margin: 0;
}
#ht-app .ht-freee-cta-link {
  display: inline-block;
  padding: 9px 18px;
  background: #16a34a;
  color: #fff;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0;
  transition: background 0.15s;
}
#ht-app .ht-freee-cta-link:hover { background: #15803d; }

/* レスポンシブ */
@media (max-width: 600px) {
  #ht-app .ht-btn { padding: 5px 9px; font-size: 12px; }
  #ht-app .ht-options { gap: 8px; }
  #ht-app .ht-cell-input { font-size: 12px; min-height: 28px; padding: 4px 6px; }
  #ht-app .ht-freee-cta { flex-direction: column; align-items: flex-start; gap: 10px; }
}
</style>

<!-- ── ツールバー ── -->
<div class="ht-section">
  <div class="ht-section-title">グリッド編集</div>
  <div class="ht-toolbar">
    <button class="ht-btn" id="ht-add-row">+ 行を追加</button>
    <button class="ht-btn ht-btn-danger" id="ht-del-row">− 最終行を削除</button>
    <button class="ht-btn" id="ht-add-col">+ 列を追加</button>
    <button class="ht-btn ht-btn-danger" id="ht-del-col">− 最終列を削除</button>
    <button class="ht-btn" id="ht-clear-all">全クリア</button>
  </div>
</div>

<!-- ── オプション ── -->
<div class="ht-options">
  <div class="ht-option-group">
    <input type="checkbox" id="ht-opt-header" checked>
    <label for="ht-opt-header">ヘッダー行</label>
  </div>
  <div class="ht-option-group">
    <input type="checkbox" id="ht-opt-border" checked>
    <label for="ht-opt-border">枠線</label>
  </div>
  <div class="ht-option-group">
    <input type="checkbox" id="ht-opt-striped">
    <label for="ht-opt-striped">縞模様行</label>
  </div>
  <div class="ht-option-group">
    <input type="checkbox" id="ht-opt-hover">
    <label for="ht-opt-hover">ホバー効果</label>
  </div>
  <div class="ht-option-group">
    <label for="ht-opt-size">サイズ:</label>
    <select class="ht-select" id="ht-opt-size">
      <option value="normal">標準</option>
      <option value="compact">コンパクト</option>
      <option value="spacious">ゆったり</option>
    </select>
  </div>
  <div class="ht-option-group">
    <label for="ht-opt-preset">CSSプリセット:</label>
    <select class="ht-select" id="ht-opt-preset">
      <option value="plain">プレーンHTML</option>
      <option value="bootstrap">Bootstrapスタイル</option>
      <option value="tailwind">Tailwindスタイル</option>
    </select>
  </div>
</div>

<!-- ── グリッド ── -->
<div class="ht-grid-wrap">
  <table class="ht-grid" id="ht-grid"></table>
</div>

<!-- ── セル結合 ── -->
<div class="ht-section">
  <div class="ht-section-title">セルの結合</div>
  <div class="ht-toolbar">
    <button class="ht-btn" id="ht-merge-sel">選択セルを結合</button>
    <button class="ht-btn" id="ht-unmerge-sel">結合を解除</button>
    <span style="font-size:12px;color:#6b7280;align-self:center;">セルをクリックで選択、Shift+クリックで範囲選択</span>
  </div>
</div>

<hr class="ht-divider">

<!-- ── インポート ── -->
<div class="ht-section">
  <div class="ht-section-title">CSV / TSV インポート</div>
  <textarea class="ht-import-area" id="ht-import-txt" placeholder="CSVまたはTSVデータをここに貼り付けて「インポート」をクリック…&#10;名前,年齢,都市&#10;田中太郎,30,東京&#10;佐藤花子,25,大阪"></textarea>
  <div class="ht-toolbar" style="margin-top:6px;">
    <button class="ht-btn ht-btn-primary" id="ht-import-csv">CSVインポート</button>
    <button class="ht-btn" id="ht-import-tsv">TSVインポート</button>
  </div>
</div>

<hr class="ht-divider">

<!-- ── ライブプレビュー ── -->
<div class="ht-section">
  <div class="ht-section-title">ライブプレビュー</div>
  <div class="ht-preview-wrap" id="ht-preview-wrap">
    <table id="ht-preview"></table>
  </div>
</div>

<!-- ── エクスポート ── -->
<div class="ht-section">
  <div class="ht-section-title">エクスポート</div>
  <div class="ht-tabs">
    <button class="ht-tab ht-tab-active" data-tab="html">HTMLコード</button>
    <button class="ht-tab" data-tab="csv">CSV</button>
    <button class="ht-tab" data-tab="md">Markdown</button>
  </div>
  <div class="ht-code-wrap">
    <textarea class="ht-code-output" id="ht-code-output" readonly></textarea>
    <button class="ht-copy-btn" id="ht-copy-btn">コピー</button>
  </div>
  <div class="ht-toolbar">
    <button class="ht-btn ht-btn-primary" id="ht-dl-html">HTMLをダウンロード</button>
    <button class="ht-btn" id="ht-dl-csv">CSVをダウンロード</button>
    <button class="ht-btn" id="ht-dl-md">.mdをダウンロード</button>
  </div>
</div>

<!-- ── freee CTAバナー ── -->
<div class="ht-freee-cta">
  <div class="ht-freee-cta-icon">📊</div>
  <div class="ht-freee-cta-body">
    <strong>請求書・帳票もfreeeでラクラク管理</strong>
    <p>表データの作成から経理・請求書発行まで、freeeならすべてをひとつにまとめて自動化できます。30日間無料トライアル実施中。</p>
  </div>
  <a class="ht-freee-cta-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>

<div class="ht-toast" id="ht-toast">コピーしました!</div>

<script>
(function () {
  'use strict';

  /* ── 状態管理 ── */
  const DEFAULT_ROWS = 4;
  const DEFAULT_COLS = 4;

  let data = [];
  let selection = [];
  let activeTab = 'html';

  /* ── DOM参照 ── */
  const grid        = document.getElementById('ht-grid');
  const preview     = document.getElementById('ht-preview');
  const codeOutput  = document.getElementById('ht-code-output');
  const toast       = document.getElementById('ht-toast');
  const importTxt   = document.getElementById('ht-import-txt');

  const optHeader   = document.getElementById('ht-opt-header');
  const optBorder   = document.getElementById('ht-opt-border');
  const optStriped  = document.getElementById('ht-opt-striped');
  const optHover    = document.getElementById('ht-opt-hover');
  const optSize     = document.getElementById('ht-opt-size');
  const optPreset   = document.getElementById('ht-opt-preset');

  /* ── データ初期化 ── */
  function makeCell(text) { return { text: text || '', colspan: 1, rowspan: 1, hidden: false }; }

  function initData(rowCount, colCount) {
    data = [];
    selection = [];
    for (let r = 0; r < rowCount; r++) {
      data[r] = [];
      for (let c = 0; c < colCount; c++) {
        data[r][c] = makeCell('');
      }
    }
  }

  function rows() { return data.length; }
  function cols() { return data[0] ? data[0].length : 0; }

  /* ── グリッド描画 ── */
  function renderGrid() {
    grid.innerHTML = '';

    /* 列コントロール行 */
    const ctrlRow = grid.insertRow();
    ctrlRow.className = 'ht-col-ctrl';
    const cornerTd = ctrlRow.insertCell();
    cornerTd.style.width = '28px';
    for (let c = 0; c < cols(); c++) {
      const td = ctrlRow.insertCell();
      td.textContent = '✕ 列' + (c + 1);
      td.dataset.col = c;
      td.addEventListener('click', function () { removeCol(+this.dataset.col); });
    }

    /* データ行 */
    for (let r = 0; r < rows(); r++) {
      const tr = grid.insertRow();
      /* 行コントロール */
      const rowCtrl = document.createElement('th');
      rowCtrl.textContent = '✕ ' + (r + 1);
      rowCtrl.dataset.row = r;
      rowCtrl.style.cssText = 'background:#f3f4f6;text-align:center;font-size:11px;color:#6b7280;padding:2px 4px;cursor:pointer;min-width:28px;width:28px;';
      rowCtrl.addEventListener('mouseenter', function () { this.style.background = '#fef2f2'; this.style.color = '#dc2626'; });
      rowCtrl.addEventListener('mouseleave', function () { this.style.background = '#f3f4f6'; this.style.color = '#6b7280'; });
      rowCtrl.addEventListener('click', function () { removeRow(+this.dataset.row); });
      tr.appendChild(rowCtrl);

      for (let c = 0; c < cols(); c++) {
        const cell = data[r][c];
        if (cell.hidden) continue;

        const isHeader = optHeader.checked && r === 0;
        const td = document.createElement(isHeader ? 'th' : 'td');
        if (isHeader) td.className = 'ht-header-cell';
        if (cell.colspan > 1) td.colSpan = cell.colspan;
        if (cell.rowspan > 1) td.rowSpan = cell.rowspan;

        if (selection.some(s => s.r === r && s.c === c)) td.classList.add('ht-cell-selected');

        const inp = document.createElement('textarea');
        inp.className = 'ht-cell-input';
        inp.value = cell.text;
        inp.rows = 1;
        inp.dataset.r = r;
        inp.dataset.c = c;
        inp.setAttribute('aria-label', (r + 1) + '行' + (c + 1) + '列');

        inp.addEventListener('input', function () {
          data[this.dataset.r][this.dataset.c].text = this.value;
          updateOutputs();
        });
        inp.addEventListener('click', function (e) {
          const rr = +this.dataset.r, cc = +this.dataset.c;
          if (e.shiftKey && selection.length > 0) {
            const last = selection[selection.length - 1];
            const r0 = Math.min(last.r, rr), r1 = Math.max(last.r, rr);
            const c0 = Math.min(last.c, cc), c1 = Math.max(last.c, cc);
            selection = [];
            for (let ri = r0; ri <= r1; ri++) for (let ci = c0; ci <= c1; ci++) selection.push({ r: ri, c: ci });
          } else {
            selection = [{ r: rr, c: cc }];
          }
          renderGrid();
        });

        td.appendChild(inp);
        tr.appendChild(td);
      }
    }
  }

  /* ── 行・列操作 ── */
  function addRow() {
    const row = [];
    for (let c = 0; c < cols(); c++) row.push(makeCell(''));
    data.push(row);
    renderGrid(); updateOutputs();
  }
  function removeRow(r) {
    if (rows() <= 1) return;
    data.splice(r, 1);
    selection = [];
    renderGrid(); updateOutputs();
  }
  function addCol() {
    for (let r = 0; r < rows(); r++) data[r].push(makeCell(''));
    renderGrid(); updateOutputs();
  }
  function removeCol(c) {
    if (cols() <= 1) return;
    for (let r = 0; r < rows(); r++) data[r].splice(c, 1);
    selection = [];
    renderGrid(); updateOutputs();
  }

  /* ── セル結合 / 解除 ── */
  function mergeCells() {
    if (selection.length < 2) return;
    const rs = selection.map(s => s.r), cs = selection.map(s => s.c);
    const r0 = Math.min(...rs), r1 = Math.max(...rs);
    const c0 = Math.min(...cs), c1 = Math.max(...cs);
    const colspan = c1 - c0 + 1, rowspan = r1 - r0 + 1;
    let combined = '';
    for (let r = r0; r <= r1; r++) for (let c = c0; c <= c1; c++) {
      if (data[r][c].text) combined += (combined ? ' ' : '') + data[r][c].text;
    }
    for (let r = r0; r <= r1; r++) for (let c = c0; c <= c1; c++) {
      data[r][c] = makeCell('');
      data[r][c].hidden = !(r === r0 && c === c0);
    }
    data[r0][c0].text = combined;
    data[r0][c0].colspan = colspan;
    data[r0][c0].rowspan = rowspan;
    data[r0][c0].hidden = false;
    selection = [];
    renderGrid(); updateOutputs();
  }

  function unmergeCells() {
    if (selection.length === 0) return;
    selection.forEach(({ r, c }) => {
      const cell = data[r][c];
      const rs = cell.rowspan, cs2 = cell.colspan;
      for (let ri = r; ri < r + rs; ri++) for (let ci = c; ci < c + cs2; ci++) {
        data[ri][ci] = makeCell(ri === r && ci === c ? cell.text : '');
      }
    });
    selection = [];
    renderGrid(); updateOutputs();
  }

  /* ── プレビュースタイル構築 ── */
  function buildTableClasses() {
    const preset = optPreset.value;
    const cls = [];
    if (preset === 'bootstrap') {
      cls.push('table');
      if (optBorder.checked)  cls.push('table-bordered');
      if (optStriped.checked) cls.push('table-striped');
      if (optHover.checked)   cls.push('table-hover');
      if (optSize.value === 'compact') cls.push('table-sm');
    } else {
      cls.push('ht-plain-table');
    }
    return cls.join(' ');
  }

  function buildInlineStyle() {
    const preset = optPreset.value;
    if (preset === 'bootstrap') return '';
    return 'border-collapse:collapse;width:100%';
  }

  function buildPreviewStyle() {
    const preset = optPreset.value;
    const padMap = { compact: '4px 8px', normal: '8px 12px', spacious: '14px 20px' };
    const pad = padMap[optSize.value] || '8px 12px';
    let css = '#ht-preview-wrap .ht-plain-table td, #ht-preview-wrap .ht-plain-table th { padding:' + pad + '; }';
    if (optBorder.checked && preset !== 'bootstrap') {
      css += ' #ht-preview-wrap table td, #ht-preview-wrap table th { border:1px solid #d1d5db; }';
    } else if (preset !== 'bootstrap') {
      css += ' #ht-preview-wrap table td, #ht-preview-wrap table th { border:none; }';
    }
    if (optStriped.checked && preset !== 'bootstrap') {
      css += ' #ht-preview-wrap table tbody tr:nth-child(even) { background:#f9fafb; }';
    }
    if (optHover.checked && preset !== 'bootstrap') {
      css += ' #ht-preview-wrap table tbody tr:hover { background:#eff6ff; }';
    }
    if (optHeader.checked) {
      css += ' #ht-preview-wrap table thead th { background:#e0f2fe; font-weight:600; }';
    }
    return css;
  }

  function renderPreview() {
    const old = document.getElementById('ht-preview-style');
    if (old) old.remove();
    const styleEl = document.createElement('style');
    styleEl.id = 'ht-preview-style';
    styleEl.textContent = buildPreviewStyle();
    document.getElementById('ht-preview-wrap').appendChild(styleEl);

    preview.innerHTML = '';
    preview.className = buildTableClasses();
    preview.setAttribute('style', buildInlineStyle());

    const hasHeader = optHeader.checked;
    if (hasHeader) {
      const thead = document.createElement('thead');
      const tr = document.createElement('tr');
      for (let c = 0; c < cols(); c++) {
        const cell = data[0][c];
        if (cell.hidden) continue;
        const th = document.createElement('th');
        th.textContent = cell.text;
        if (cell.colspan > 1) th.colSpan = cell.colspan;
        if (cell.rowspan > 1) th.rowSpan = cell.rowspan;
        tr.appendChild(th);
      }
      thead.appendChild(tr);
      preview.appendChild(thead);
    }

    const tbody = document.createElement('tbody');
    const startRow = hasHeader ? 1 : 0;
    for (let r = startRow; r < rows(); r++) {
      const tr = document.createElement('tr');
      for (let c = 0; c < cols(); c++) {
        const cell = data[r][c];
        if (cell.hidden) continue;
        const td = document.createElement('td');
        td.textContent = cell.text;
        if (cell.colspan > 1) td.colSpan = cell.colspan;
        if (cell.rowspan > 1) td.rowSpan = cell.rowspan;
        tr.appendChild(td);
      }
      tbody.appendChild(tr);
    }
    preview.appendChild(tbody);
  }

  /* ── 出力生成 ── */
  function generateHTML() {
    const preset    = optPreset.value;
    const hasHeader = optHeader.checked;
    const tableClass = buildTableClasses();
    const tableStyle = buildInlineStyle();
    const padMap = { compact: '4px 8px', normal: '8px 12px', spacious: '14px 20px' };
    const pad = padMap[optSize.value] || '8px 12px';

    let styleBlock = '';
    if (preset !== 'bootstrap') {
      let css = 'table { border-collapse: collapse; width: 100%; }\n';
      css += 'th, td { padding: ' + pad + '; }\n';
      if (optBorder.checked)  css += 'th, td { border: 1px solid #d1d5db; }\n';
      if (hasHeader)          css += 'thead th { background: #e0f2fe; font-weight: 600; }\n';
      if (optStriped.checked) css += 'tbody tr:nth-child(even) { background: #f9fafb; }\n';
      if (optHover.checked)   css += 'tbody tr:hover { background: #eff6ff; }\n';
      styleBlock = '<style>\n' + css + '</style>\n';
    }

    let html = styleBlock + '<table';
    if (tableClass) html += ' class="' + tableClass + '"';
    if (tableStyle && preset === 'tailwind') html += ' style="' + tableStyle + '"';
    html += '>\n';

    if (hasHeader) {
      html += '  <thead>\n    <tr>\n';
      for (let c = 0; c < cols(); c++) {
        const cell = data[0][c];
        if (cell.hidden) continue;
        html += '      <th';
        if (cell.colspan > 1) html += ' colspan="' + cell.colspan + '"';
        if (cell.rowspan > 1) html += ' rowspan="' + cell.rowspan + '"';
        html += '>' + escapeHtml(cell.text) + '</th>\n';
      }
      html += '    </tr>\n  </thead>\n';
    }

    html += '  <tbody>\n';
    const startRow = hasHeader ? 1 : 0;
    for (let r = startRow; r < rows(); r++) {
      html += '    <tr>\n';
      for (let c = 0; c < cols(); c++) {
        const cell = data[r][c];
        if (cell.hidden) continue;
        html += '      <td';
        if (cell.colspan > 1) html += ' colspan="' + cell.colspan + '"';
        if (cell.rowspan > 1) html += ' rowspan="' + cell.rowspan + '"';
        html += '>' + escapeHtml(cell.text) + '</td>\n';
      }
      html += '    </tr>\n';
    }
    html += '  </tbody>\n</table>';
    return html;
  }

  function generateCSV() {
    const lines = [];
    for (let r = 0; r < rows(); r++) {
      const row = [];
      for (let c = 0; c < cols(); c++) {
        if (data[r][c].hidden) continue;
        const v = data[r][c].text;
        row.push(v.includes(',') || v.includes('"') || v.includes('\n') ? '"' + v.replace(/"/g, '""') + '"' : v);
      }
      lines.push(row.join(','));
    }
    return lines.join('\n');
  }

  function generateMarkdown() {
    const visibleCols = cols();
    const widths = Array(visibleCols).fill(3);
    for (let r = 0; r < rows(); r++) {
      for (let c = 0; c < visibleCols; c++) {
        if (!data[r][c].hidden) widths[c] = Math.max(widths[c], data[r][c].text.length);
      }
    }
    const pad = (s, w) => s + ' '.repeat(Math.max(0, w - s.length));
    const lines = [];
    for (let r = 0; r < rows(); r++) {
      const cells = [];
      for (let c = 0; c < visibleCols; c++) {
        if (data[r][c].hidden) continue;
        cells.push(' ' + pad(data[r][c].text, widths[c]) + ' ');
      }
      lines.push('|' + cells.join('|') + '|');
      if (r === 0 && optHeader.checked) {
        const sep = widths.map(w => '-'.repeat(w + 2));
        lines.push('|' + sep.join('|') + '|');
      }
    }
    return lines.join('\n');
  }

  function escapeHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function updateOutputs() { renderPreview(); refreshCode(); }
  function refreshCode() {
    if (activeTab === 'html')     codeOutput.value = generateHTML();
    else if (activeTab === 'csv') codeOutput.value = generateCSV();
    else if (activeTab === 'md')  codeOutput.value = generateMarkdown();
  }

  /* ── インポート ── */
  function importDelimited(sep) {
    const raw = importTxt.value.trim();
    if (!raw) return;
    const rows2 = raw.split('\n').map(line => line.split(sep).map(v => v.trim().replace(/^"|"$/g, '').replace(/""/g, '"')));
    const maxCols = Math.max(...rows2.map(r => r.length));
    initData(rows2.length, maxCols);
    rows2.forEach((row, r) => { row.forEach((v, c) => { if (data[r][c]) data[r][c].text = v; }); });
    importTxt.value = '';
    renderGrid(); updateOutputs();
  }

  /* ── ダウンロード ── */
  function download(filename, content, mime) {
    const a = document.createElement('a');
    a.href = URL.createObjectURL(new Blob([content], { type: mime }));
    a.download = filename;
    a.click();
    URL.revokeObjectURL(a.href);
  }

  /* ── トースト通知 ── */
  function showToast(msg) {
    toast.textContent = msg;
    toast.classList.add('ht-show');
    setTimeout(() => toast.classList.remove('ht-show'), 2000);
  }

  /* ── イベント接続 ── */
  document.getElementById('ht-add-row').addEventListener('click', addRow);
  document.getElementById('ht-del-row').addEventListener('click', () => { if (rows() > 1) removeRow(rows() - 1); });
  document.getElementById('ht-add-col').addEventListener('click', addCol);
  document.getElementById('ht-del-col').addEventListener('click', () => { if (cols() > 1) removeCol(cols() - 1); });
  document.getElementById('ht-clear-all').addEventListener('click', () => { initData(DEFAULT_ROWS, DEFAULT_COLS); renderGrid(); updateOutputs(); });
  document.getElementById('ht-merge-sel').addEventListener('click', mergeCells);
  document.getElementById('ht-unmerge-sel').addEventListener('click', unmergeCells);
  document.getElementById('ht-import-csv').addEventListener('click', () => importDelimited(','));
  document.getElementById('ht-import-tsv').addEventListener('click', () => importDelimited('\t'));

  [optHeader, optBorder, optStriped, optHover, optSize, optPreset].forEach(el => el.addEventListener('change', updateOutputs));

  /* タブ切り替え */
  document.querySelectorAll('#ht-app .ht-tab').forEach(tab => {
    tab.addEventListener('click', function () {
      document.querySelectorAll('#ht-app .ht-tab').forEach(t => t.classList.remove('ht-tab-active'));
      this.classList.add('ht-tab-active');
      activeTab = this.dataset.tab;
      refreshCode();
    });
  });

  /* コピーボタン */
  document.getElementById('ht-copy-btn').addEventListener('click', function () {
    navigator.clipboard.writeText(codeOutput.value).then(() => {
      this.textContent = 'コピー済!';
      this.classList.add('ht-copied');
      showToast('クリップボードにコピーしました!');
      setTimeout(() => { this.textContent = 'コピー'; this.classList.remove('ht-copied'); }, 2000);
    });
  });

  /* ダウンロードボタン */
  document.getElementById('ht-dl-html').addEventListener('click', () => download('table.html', generateHTML(), 'text/html'));
  document.getElementById('ht-dl-csv').addEventListener('click',  () => download('table.csv',  generateCSV(),  'text/csv'));
  document.getElementById('ht-dl-md').addEventListener('click',   () => download('table.md',   generateMarkdown(), 'text/markdown'));

  /* ── サンプルデータで初期化 ── */
  initData(DEFAULT_ROWS, DEFAULT_COLS);
  const sample = [
    ['氏名', '役職', '部署', 'ステータス'],
    ['田中 太郎', 'エンジニア', '開発部', '在籍'],
    ['佐藤 花子', 'デザイナー', 'プロダクト', '在籍'],
    ['鈴木 一郎', 'マネージャー', 'マーケティング', '休暇中'],
  ];
  sample.forEach((row, r) => row.forEach((v, c) => { if (data[r] && data[r][c]) data[r][c].text = v; }));

  renderGrid();
  updateOutputs();
})();
</script>

</div>

---

### 関連ツール
> Markdownテーブルを生成 → [Markdownテーブルジェネレーター](/ja/tools/markdown-table-generator/)
> JSONをCSVに変換 → [JSON to CSV コンバーター](/ja/tools/json-to-csv/)
> SQLクエリを整形 → [SQLフォーマッター](/ja/tools/sql-formatter/)
