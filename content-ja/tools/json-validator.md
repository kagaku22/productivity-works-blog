---
title: "JSONバリデーター＆フォーマッター"
date: 2025-05-16
description: "無料オンラインJSONバリデーター・フォーマッター。JSONの構文チェック（行番号・位置付きエラー）、整形（インデント設定可）、圧縮、ツリービュー、パス表示、コピー、ファイルアップロード対応。登録不要。"
categories: ["無料ツール"]
slug: "json-validator"
ShowToc: false
aliases: ["/ja/tools/json-formatter/", "/ja/tools/json-validator/"]
cover:
  image: "/images/covers/json-validator-ja.png"
  alt: "JSONバリデーター"
---

<div id="jv-app">

<style>
#jv-app *, #jv-app *::before, #jv-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#jv-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.6;
}

/* ── Toolbar ── */
#jv-app .jv-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 10px;
}

#jv-app .jv-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 7px 14px;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  white-space: nowrap;
  line-height: 1;
}
#jv-app .jv-btn:active { transform: scale(0.97); }
#jv-app .jv-btn-primary   { background: #2563eb; color: #fff; }
#jv-app .jv-btn-primary:hover   { background: #1d4ed8; }
#jv-app .jv-btn-secondary { background: #e2e8f0; color: #334155; }
#jv-app .jv-btn-secondary:hover { background: #cbd5e1; }
#jv-app .jv-btn-success   { background: #16a34a; color: #fff; }
#jv-app .jv-btn-success:hover   { background: #15803d; }
#jv-app .jv-btn-orange    { background: #d97706; color: #fff; }
#jv-app .jv-btn-orange:hover    { background: #b45309; }
#jv-app .jv-btn-danger    { background: #dc2626; color: #fff; }
#jv-app .jv-btn-danger:hover    { background: #b91c1c; }
#jv-app .jv-btn-purple    { background: #7c3aed; color: #fff; }
#jv-app .jv-btn-purple:hover    { background: #6d28d9; }

/* ── Options bar ── */
#jv-app .jv-options-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: center;
  padding: 8px 12px;
  background: #f1f5f9;
  border-radius: 8px;
  margin-bottom: 10px;
}

#jv-app .jv-select {
  padding: 6px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  background: #fff;
  color: #334155;
  cursor: pointer;
}
#jv-app .jv-options-bar label {
  font-size: 13px;
  color: #475569;
  display: flex;
  align-items: center;
  gap: 5px;
}

/* ── Panels ── */
#jv-app .jv-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 12px;
}
@media (max-width: 660px) {
  #jv-app .jv-panels { grid-template-columns: 1fr; }
}

#jv-app .jv-pane-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
  margin-bottom: 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

#jv-app .jv-pane-label .jv-copy-btn {
  padding: 3px 9px;
  background: #e2e8f0;
  color: #334155;
  border: none;
  border-radius: 5px;
  font-size: 11px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  text-transform: none;
  letter-spacing: 0;
}
#jv-app .jv-pane-label .jv-copy-btn:hover { background: #cbd5e1; }

#jv-app textarea {
  width: 100%;
  height: 320px;
  padding: 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-family: "JetBrains Mono", "Fira Code", "Cascadia Code", Consolas, monospace;
  font-size: 12.5px;
  line-height: 1.65;
  resize: vertical;
  background: #f8fafc;
  color: #0f172a;
  transition: border-color 0.15s;
}
#jv-app textarea:focus { outline: none; border-color: #2563eb; }
#jv-app textarea.jv-error  { border-color: #dc2626; background: #fff5f5; }
#jv-app textarea.jv-valid  { border-color: #16a34a; }

/* ── Status badge ── */
#jv-app .jv-status {
  display: flex;
  align-items: flex-start;
  gap: 8px;
  padding: 10px 14px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 500;
  margin-bottom: 12px;
  min-height: 42px;
}
#jv-app .jv-status.jv-status-idle    { background: #f1f5f9; color: #64748b; }
#jv-app .jv-status.jv-status-valid   { background: #f0fdf4; color: #15803d; border: 1px solid #bbf7d0; }
#jv-app .jv-status.jv-status-error   { background: #fef2f2; color: #b91c1c; border: 1px solid #fecaca; }
#jv-app .jv-status-icon { font-size: 16px; line-height: 1.3; flex-shrink: 0; }
#jv-app .jv-status-msg  { flex: 1; word-break: break-all; font-family: "JetBrains Mono", Consolas, monospace; font-size: 12px; }

/* ── Stats bar ── */
#jv-app .jv-stats {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 12px;
}
#jv-app .jv-stat-pill {
  padding: 4px 11px;
  background: #e0f2fe;
  color: #0369a1;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
}

/* ── Path display ── */
#jv-app .jv-path-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 7px 12px;
  background: #fefce8;
  border: 1px solid #fde68a;
  border-radius: 7px;
  margin-bottom: 10px;
  font-size: 12px;
  font-family: "JetBrains Mono", Consolas, monospace;
  color: #92400e;
  min-height: 34px;
  word-break: break-all;
}
#jv-app .jv-path-bar .jv-path-label {
  font-weight: 700;
  flex-shrink: 0;
  color: #78350f;
}

/* ── Tree view ── */
#jv-app .jv-tree-wrap {
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  background: #f8fafc;
  padding: 12px 14px;
  max-height: 420px;
  overflow: auto;
  font-family: "JetBrains Mono", "Fira Code", Consolas, monospace;
  font-size: 12px;
  line-height: 1.7;
  display: none;
}
#jv-app .jv-tree-wrap.jv-visible { display: block; }

#jv-app .jv-tree-node { padding-left: 0; }
#jv-app .jv-tree-children { padding-left: 18px; border-left: 1.5px dotted #cbd5e1; margin-left: 6px; }

#jv-app .jv-node-row {
  display: flex;
  align-items: baseline;
  gap: 4px;
  cursor: pointer;
  border-radius: 4px;
  padding: 1px 4px;
  user-select: none;
}
#jv-app .jv-node-row:hover { background: #e0f2fe; }

#jv-app .jv-toggle {
  display: inline-block;
  width: 14px;
  text-align: center;
  color: #94a3b8;
  font-size: 10px;
  flex-shrink: 0;
}
#jv-app .jv-key   { color: #7c3aed; font-weight: 600; }
#jv-app .jv-colon { color: #64748b; margin-right: 2px; }
#jv-app .jv-val-string  { color: #059669; }
#jv-app .jv-val-number  { color: #2563eb; }
#jv-app .jv-val-bool    { color: #d97706; font-weight: 600; }
#jv-app .jv-val-null    { color: #94a3b8; font-style: italic; }
#jv-app .jv-val-bracket { color: #64748b; }
#jv-app .jv-count       { color: #94a3b8; font-size: 10px; margin-left: 3px; }

/* ── Tab group ── */
#jv-app .jv-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 10px;
}
#jv-app .jv-tab {
  padding: 7px 16px;
  font-size: 13px;
  font-weight: 600;
  color: #64748b;
  border: none;
  background: none;
  cursor: pointer;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
}
#jv-app .jv-tab:hover { color: #2563eb; }
#jv-app .jv-tab.active { color: #2563eb; border-bottom-color: #2563eb; }

/* ── File upload ── */
#jv-app .jv-upload-zone {
  border: 2px dashed #94a3b8;
  border-radius: 8px;
  padding: 14px 20px;
  text-align: center;
  font-size: 13px;
  color: #64748b;
  cursor: pointer;
  transition: border-color 0.15s, background 0.15s;
  margin-bottom: 10px;
}
#jv-app .jv-upload-zone:hover { border-color: #2563eb; background: #eff6ff; color: #1d4ed8; }
#jv-app input[type="file"] { display: none; }

/* ── Output section ── */
#jv-app .jv-output-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 5px;
}
</style>

<!-- ── Toolbar ── -->
<div class="jv-toolbar">
  <button class="jv-btn jv-btn-primary" onclick="jvValidate()">&#10003; 検証</button>
  <button class="jv-btn jv-btn-success" onclick="jvFormat()">&#9776; 整形</button>
  <button class="jv-btn jv-btn-orange"  onclick="jvMinify()">&#8644; 圧縮</button>
  <button class="jv-btn jv-btn-purple"  onclick="jvToggleTree()">&#9654; ツリー表示</button>
  <button class="jv-btn jv-btn-secondary" onclick="jvClear()">&#10005; クリア</button>
  <label class="jv-btn jv-btn-secondary" style="cursor:pointer;" for="jv-file-input">&#8613; JSONファイルを開く</label>
  <input type="file" id="jv-file-input" accept=".json,application/json" onchange="jvLoadFile(event)">
</div>

<!-- ── Options ── -->
<div class="jv-options-bar">
  <label>インデント:
    <select class="jv-select" id="jv-indent">
      <option value="2" selected>スペース 2</option>
      <option value="4">スペース 4</option>
      <option value="tab">タブ</option>
    </select>
  </label>
  <label>サンプル:
    <select class="jv-select" id="jv-sample" onchange="jvLoadSample()">
      <option value="">— サンプルを読み込む —</option>
      <option value="user">ユーザーオブジェクト</option>
      <option value="array">配列</option>
      <option value="nested">ネスト構造</option>
    </select>
  </label>
</div>

<!-- ── Upload drop zone ── -->
<div class="jv-upload-zone" id="jv-drop-zone"
  ondragover="event.preventDefault();this.style.borderColor='#2563eb';this.style.background='#eff6ff';"
  ondragleave="this.style.borderColor='';this.style.background='';"
  ondrop="jvHandleDrop(event)"
  onclick="document.getElementById('jv-file-input').click()">
  &#128193; <strong>.json</strong> ファイルをここにドロップ、またはクリックして選択
</div>

<!-- ── Status ── -->
<div class="jv-status jv-status-idle" id="jv-status">
  <span class="jv-status-icon">&#9432;</span>
  <span class="jv-status-msg">JSONを貼り付け・入力して「検証」または「整形」をクリックしてください。</span>
</div>

<!-- ── Stats ── -->
<div class="jv-stats" id="jv-stats" style="display:none;"></div>

<!-- ── Path display ── -->
<div class="jv-path-bar" id="jv-path-bar" style="display:none;">
  <span class="jv-path-label">パス:</span>
  <span id="jv-path-text">—</span>
</div>

<!-- ── Input / Output panels ── -->
<div class="jv-panels">
  <div>
    <div class="jv-pane-label">入力</div>
    <textarea id="jv-input" placeholder='JSONをここに貼り付け…&#10;&#10;例:&#10;{&#10;  "name": "山田太郎",&#10;  "age": 30&#10;}' spellcheck="false" oninput="jvOnInput()"></textarea>
  </div>
  <div>
    <div class="jv-pane-label">
      出力
      <button class="jv-copy-btn" onclick="jvCopyOutput()">コピー</button>
    </div>
    <textarea id="jv-output" readonly placeholder="整形・圧縮した結果がここに表示されます…" spellcheck="false"></textarea>
  </div>
</div>

<!-- ── Tabs: Tree / Raw ── -->
<div class="jv-tabs">
  <button class="jv-tab active" id="jv-tab-tree" onclick="jvSwitchTab('tree')">ツリービュー</button>
  <button class="jv-tab" id="jv-tab-raw"  onclick="jvSwitchTab('raw')">Raw</button>
</div>

<!-- ── Tree view container ── -->
<div class="jv-tree-wrap jv-visible" id="jv-tree"></div>

<script>
(function () {
  /* ── Samples ── */
  const SAMPLES = {
    user: '{\n  "id": 1,\n  "name": "山田太郎",\n  "age": 30,\n  "email": "yamada@example.com",\n  "address": {\n    "prefecture": "東京都",\n    "city": "渋谷区",\n    "zip": "150-0001"\n  },\n  "tags": ["エンジニア", "デザイナー"],\n  "active": true,\n  "score": null\n}',
    array: '[\n  { "id": 1, "product": "商品A", "price": 980, "inStock": true },\n  { "id": 2, "product": "商品B", "price": 1480, "inStock": false },\n  { "id": 3, "product": "商品C", "price": 420, "inStock": true }\n]',
    nested: '{\n  "company": "株式会社サンプル",\n  "founded": 2010,\n  "departments": [\n    {\n      "name": "エンジニアリング",\n      "headcount": 42,\n      "lead": { "name": "鈴木一郎", "email": "suzuki@sample.co.jp" }\n    },\n    {\n      "name": "マーケティング",\n      "headcount": 18,\n      "lead": { "name": "佐藤花子", "email": "sato@sample.co.jp" }\n    }\n  ],\n  "listed": false,\n  "revenue": null\n}'
  };

  /* ── Helpers ── */
  function el(id) { return document.getElementById(id); }

  function getIndent() {
    const v = el('jv-indent').value;
    return v === 'tab' ? '\t' : parseInt(v, 10);
  }

  function setStatus(type, icon, msg) {
    const s = el('jv-status');
    s.className = 'jv-status jv-status-' + type;
    s.innerHTML = '<span class="jv-status-icon">' + icon + '</span><span class="jv-status-msg">' + escHtml(msg) + '</span>';
  }

  function escHtml(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function showStats(parsed, rawLen) {
    const statsEl = el('jv-stats');
    const depth = calcDepth(parsed);
    const keys  = countKeys(parsed);
    statsEl.style.display = 'flex';
    statsEl.innerHTML =
      pill('キー数: ' + keys) +
      pill('深さ: ' + depth) +
      pill('サイズ: ' + fmtBytes(rawLen)) +
      pill('型: ' + (Array.isArray(parsed) ? '配列' : typeof parsed === 'object' && parsed !== null ? 'オブジェクト' : typeof parsed));
  }

  function pill(t) { return '<span class="jv-stat-pill">' + escHtml(t) + '</span>'; }

  function fmtBytes(n) {
    if (n < 1024) return n + ' B';
    if (n < 1024*1024) return (n/1024).toFixed(1) + ' KB';
    return (n/1024/1024).toFixed(2) + ' MB';
  }

  function calcDepth(v, d) {
    d = d || 0;
    if (v && typeof v === 'object') {
      const vals = Object.values(v);
      if (!vals.length) return d + 1;
      return Math.max(...vals.map(c => calcDepth(c, d + 1)));
    }
    return d;
  }

  function countKeys(v) {
    if (!v || typeof v !== 'object') return 0;
    let c = Object.keys(v).length;
    Object.values(v).forEach(ch => { c += countKeys(ch); });
    return c;
  }

  /* ── Parse with error location ── */
  function parseWithLocation(text) {
    try {
      return { ok: true, value: JSON.parse(text) };
    } catch (e) {
      const msg = e.message;
      const posMatch = msg.match(/position (\d+)/i);
      let lineNum = null, colNum = null, hint = msg;
      if (posMatch) {
        const pos = parseInt(posMatch[1], 10);
        const before = text.slice(0, pos);
        const lines = before.split('\n');
        lineNum = lines.length;
        colNum = lines[lines.length - 1].length + 1;
        hint = msg.replace(/position \d+/i, '行 ' + lineNum + '、列 ' + colNum);
      }
      return { ok: false, message: hint, line: lineNum, col: colNum };
    }
  }

  /* ── Core actions ── */
  window.jvValidate = function () {
    const raw = el('jv-input').value.trim();
    if (!raw) { setStatus('idle', '&#9432;', '入力が空です。'); return; }
    const result = parseWithLocation(raw);
    if (result.ok) {
      el('jv-input').className = 'jv-valid';
      setStatus('valid', '&#10003;', '有効なJSONです');
      showStats(result.value, raw.length);
      renderTree(result.value);
    } else {
      el('jv-input').className = 'jv-error';
      setStatus('error', '&#10007;', 'SyntaxError: ' + result.message);
      el('jv-stats').style.display = 'none';
      el('jv-tree').innerHTML = '';
    }
  };

  window.jvFormat = function () {
    const raw = el('jv-input').value.trim();
    if (!raw) { setStatus('idle', '&#9432;', '入力が空です。'); return; }
    const result = parseWithLocation(raw);
    if (!result.ok) {
      el('jv-input').className = 'jv-error';
      setStatus('error', '&#10007;', 'SyntaxError: ' + result.message);
      return;
    }
    const formatted = JSON.stringify(result.value, null, getIndent());
    el('jv-output').value = formatted;
    el('jv-input').className = 'jv-valid';
    setStatus('valid', '&#10003;', '整形しました');
    showStats(result.value, raw.length);
    renderTree(result.value);
  };

  window.jvMinify = function () {
    const raw = el('jv-input').value.trim();
    if (!raw) { setStatus('idle', '&#9432;', '入力が空です。'); return; }
    const result = parseWithLocation(raw);
    if (!result.ok) {
      el('jv-input').className = 'jv-error';
      setStatus('error', '&#10007;', 'SyntaxError: ' + result.message);
      return;
    }
    const minified = JSON.stringify(result.value);
    el('jv-output').value = minified;
    el('jv-input').className = 'jv-valid';
    setStatus('valid', '&#10003;', '圧縮しました — ' + fmtBytes(minified.length));
    showStats(result.value, raw.length);
    renderTree(result.value);
  };

  window.jvClear = function () {
    el('jv-input').value = '';
    el('jv-output').value = '';
    el('jv-input').className = '';
    el('jv-stats').style.display = 'none';
    el('jv-tree').innerHTML = '';
    el('jv-path-bar').style.display = 'none';
    el('jv-sample').value = '';
    setStatus('idle', '&#9432;', 'JSONを貼り付け・入力して「検証」または「整形」をクリックしてください。');
  };

  window.jvCopyOutput = function () {
    const out = el('jv-output');
    if (!out.value) return;
    navigator.clipboard.writeText(out.value).then(function () {
      const btn = document.querySelector('#jv-app .jv-copy-btn');
      const orig = btn.textContent;
      btn.textContent = 'コピーしました!';
      setTimeout(function () { btn.textContent = orig; }, 1500);
    }).catch(function () {
      out.select();
      document.execCommand('copy');
    });
  };

  window.jvOnInput = function () {
    el('jv-input').className = '';
    setStatus('idle', '&#9432;', 'JSONを貼り付け・入力して「検証」または「整形」をクリックしてください。');
    el('jv-stats').style.display = 'none';
    el('jv-tree').innerHTML = '';
    el('jv-path-bar').style.display = 'none';
  };

  window.jvLoadSample = function () {
    const key = el('jv-sample').value;
    if (!key || !SAMPLES[key]) return;
    el('jv-input').value = SAMPLES[key];
    el('jv-input').className = '';
    setStatus('idle', '&#9432;', 'サンプルを読み込みました。「整形」または「検証」をクリックしてください。');
    el('jv-stats').style.display = 'none';
    el('jv-tree').innerHTML = '';
    el('jv-path-bar').style.display = 'none';
  };

  /* ── File upload ── */
  window.jvLoadFile = function (e) {
    const file = e.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function (ev) {
      el('jv-input').value = ev.target.result;
      el('jv-input').className = '';
      setStatus('idle', '&#9432;', 'ファイルを読み込みました: ' + file.name + ' (' + fmtBytes(file.size) + ')。「検証」または「整形」をクリックしてください。');
      el('jv-stats').style.display = 'none';
      el('jv-tree').innerHTML = '';
    };
    reader.readAsText(file);
    e.target.value = '';
  };

  window.jvHandleDrop = function (e) {
    e.preventDefault();
    const dropZone = el('jv-drop-zone');
    dropZone.style.borderColor = '';
    dropZone.style.background = '';
    const file = e.dataTransfer.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function (ev) {
      el('jv-input').value = ev.target.result;
      el('jv-input').className = '';
      setStatus('idle', '&#9432;', 'ドロップされたファイルを読み込みました: ' + file.name + '。「検証」または「整形」をクリックしてください。');
      el('jv-stats').style.display = 'none';
      el('jv-tree').innerHTML = '';
    };
    reader.readAsText(file);
  };

  /* ── Tab switching ── */
  window.jvSwitchTab = function (tab) {
    el('jv-tab-tree').classList.toggle('active', tab === 'tree');
    el('jv-tab-raw').classList.toggle('active',  tab === 'raw');
    el('jv-tree').classList.toggle('jv-visible', tab === 'tree');
  };

  /* ── Tree toggle ── */
  window.jvToggleTree = function () {
    const wrap = el('jv-tree');
    const raw  = el('jv-input').value.trim();
    if (!raw) { setStatus('idle', '&#9432;', '入力が空です。'); return; }
    const result = parseWithLocation(raw);
    if (!result.ok) {
      setStatus('error', '&#10007;', 'SyntaxError: ' + result.message);
      return;
    }
    renderTree(result.value);
    jvSwitchTab('tree');
    showStats(result.value, raw.length);
    setStatus('valid', '&#10003;', 'ツリーを表示しました');
  };

  /* ── Tree renderer ── */
  function renderTree(data) {
    const wrap = el('jv-tree');
    wrap.innerHTML = '';
    wrap.appendChild(buildNode(data, '$', null, '$'));
  }

  function buildNode(value, key, parentEl, path) {
    const div = document.createElement('div');
    div.className = 'jv-tree-node';

    if (value !== null && typeof value === 'object') {
      const isArr   = Array.isArray(value);
      const entries = isArr ? value.map((v, i) => [i, v]) : Object.entries(value);
      const count   = entries.length;
      const open    = isArr ? '[' : '{';
      const close   = isArr ? ']' : '}';

      const row = document.createElement('div');
      row.className = 'jv-node-row';

      const toggle = document.createElement('span');
      toggle.className = 'jv-toggle';
      toggle.textContent = count ? '▼' : ' ';

      const keySpan = document.createElement('span');
      keySpan.className = 'jv-key';
      if (key !== null) keySpan.textContent = isNaN(key) ? '"' + key + '"' : key;

      const colonSpan = document.createElement('span');
      colonSpan.className = 'jv-colon';
      if (key !== null) colonSpan.textContent = ': ';

      const bracketSpan = document.createElement('span');
      bracketSpan.className = 'jv-val-bracket';
      bracketSpan.textContent = open;

      const countSpan = document.createElement('span');
      countSpan.className = 'jv-count';
      countSpan.textContent = count + '件';

      row.appendChild(toggle);
      if (key !== null) { row.appendChild(keySpan); row.appendChild(colonSpan); }
      row.appendChild(bracketSpan);
      row.appendChild(countSpan);
      div.appendChild(row);

      const childWrap = document.createElement('div');
      childWrap.className = 'jv-tree-children';
      entries.forEach(function ([k, v]) {
        const childPath = isArr ? path + '[' + k + ']' : path + '.' + k;
        childWrap.appendChild(buildNode(v, k, childWrap, childPath));
      });
      div.appendChild(childWrap);

      const closeRow = document.createElement('div');
      closeRow.className = 'jv-node-row';
      closeRow.innerHTML = '<span class="jv-toggle"> </span><span class="jv-val-bracket">' + close + '</span>';
      div.appendChild(closeRow);

      if (count > 0) {
        let collapsed = false;
        row.addEventListener('click', function (e) {
          e.stopPropagation();
          collapsed = !collapsed;
          childWrap.style.display = collapsed ? 'none' : '';
          closeRow.style.display  = collapsed ? 'none' : '';
          toggle.textContent = collapsed ? '▶' : '▼';
          countSpan.style.display = collapsed ? '' : 'none';
          if (collapsed) {
            bracketSpan.textContent = open + '…' + close;
          } else {
            bracketSpan.textContent = open;
          }
          showPath(path);
        });
      }

      row.addEventListener('click', function (e) { e.stopPropagation(); showPath(path); });

    } else {
      const row = document.createElement('div');
      row.className = 'jv-node-row';
      row.title = path;

      const toggle = document.createElement('span');
      toggle.className = 'jv-toggle';
      toggle.textContent = ' ';

      const keySpan = document.createElement('span');
      keySpan.className = 'jv-key';
      if (key !== null) keySpan.textContent = isNaN(key) ? '"' + key + '"' : key;

      const colonSpan = document.createElement('span');
      colonSpan.className = 'jv-colon';
      if (key !== null) colonSpan.textContent = ': ';

      const valSpan = document.createElement('span');
      if (typeof value === 'string') {
        valSpan.className = 'jv-val-string';
        valSpan.textContent = '"' + value + '"';
      } else if (typeof value === 'boolean') {
        valSpan.className = 'jv-val-bool';
        valSpan.textContent = String(value);
      } else if (value === null) {
        valSpan.className = 'jv-val-null';
        valSpan.textContent = 'null';
      } else {
        valSpan.className = 'jv-val-number';
        valSpan.textContent = String(value);
      }

      row.appendChild(toggle);
      if (key !== null) { row.appendChild(keySpan); row.appendChild(colonSpan); }
      row.appendChild(valSpan);
      div.appendChild(row);

      row.addEventListener('click', function (e) { e.stopPropagation(); showPath(path); });
    }

    return div;
  }

  function showPath(path) {
    const bar = el('jv-path-bar');
    bar.style.display = 'flex';
    el('jv-path-text').textContent = path;
  }

})();
</script>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

### 関連ツール
> JSON⇔CSV変換 → [JSON⇔CSV変換ツール](/ja/tools/json-to-csv/)
> HTMLを整形 → [HTML整形ツール](/ja/tools/html-beautifier/)
> 正規表現テスト → [正規表現テスター](/ja/tools/regex-tester/)
---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>

## 関連記事

- [ChatGPT API初心者向け完全ガイド【2026年版・サンプルコード付き】](/ja/posts/chatgpt-api-使い方-初心者/)
