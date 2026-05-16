---
title: "JSON⇄CSV 変換ツール — 無料・インストール不要"
description: "JSONをCSVに、CSVをJSONに、ブラウザだけで即座に変換。ネストされたJSONのフラット化、カスタム区切り文字、ワンクリックダウンロードに対応。サーバー送信なし・外部ライブラリなし。"
date: 2025-05-16
slug: "json-to-csv"
categories: ["無料ツール"]
ShowToc: false
aliases:
  - "/ja/tools/csv-to-json/"
  - "/ja/tools/json-csv/"
cover:
  image: "/images/covers/json-to-csv-ja.png"
  alt: "JSON→CSV変換ツール"
---

JSONをCSVに、CSVをJSONに変換します。サーバー送信なし・外部ライブラリなし、すべてブラウザ内で完結します。

<style>
#j2c-app *,
#j2c-app *::before,
#j2c-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#j2c-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Hiragino Sans", "Yu Gothic", Meiryo, sans-serif;
  font-size: 15px;
  color: #1f2937;
  line-height: 1.6;
  max-width: 900px;
  margin: 2rem auto;
}

#j2c-app h2 {
  font-size: 1.05rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.5rem;
}

#j2c-app .j2c-tabs {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

#j2c-app .j2c-tab {
  padding: 0.55rem 1.2rem;
  border: 2px solid #d1fae5;
  border-radius: 6px;
  background: #fff;
  color: #059669;
  font-weight: 700;
  font-size: 0.95rem;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}

#j2c-app .j2c-tab.active {
  background: #059669;
  color: #fff;
  border-color: #059669;
}

#j2c-app .j2c-tab:hover:not(.active) {
  background: #d1fae5;
}

#j2c-app .j2c-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  align-items: center;
  background: #f9fafb;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  padding: 0.85rem 1rem;
  margin-bottom: 1.25rem;
}

#j2c-app .j2c-control-group {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

#j2c-app label {
  font-size: 0.88rem;
  font-weight: 500;
  color: #6b7280;
}

#j2c-app select {
  padding: 0.3rem 0.6rem;
  border: 1px solid #d1d5db;
  border-radius: 5px;
  font-size: 0.88rem;
  background: #fff;
  color: #374151;
  cursor: pointer;
}

#j2c-app .j2c-toggle {
  display: flex;
  align-items: center;
  gap: 0.45rem;
  cursor: pointer;
  user-select: none;
}

#j2c-app .j2c-toggle input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #059669;
  cursor: pointer;
}

#j2c-app .j2c-io-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1.25rem;
}

@media (max-width: 640px) {
  #j2c-app .j2c-io-grid {
    grid-template-columns: 1fr;
  }
}

#j2c-app .j2c-pane {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}

#j2c-app textarea {
  width: 100%;
  height: 220px;
  padding: 0.65rem 0.8rem;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.82rem;
  line-height: 1.5;
  color: #1f2937;
  background: #fff;
  resize: vertical;
  transition: border-color 0.15s;
}

#j2c-app textarea:focus {
  outline: none;
  border-color: #059669;
  box-shadow: 0 0 0 3px rgba(5,150,105,0.12);
}

#j2c-app textarea.j2c-error {
  border-color: #ef4444;
  box-shadow: 0 0 0 3px rgba(239,68,68,0.1);
}

#j2c-app .j2c-pane-actions {
  display: flex;
  gap: 0.5rem;
}

#j2c-app .j2c-btn {
  padding: 0.4rem 0.9rem;
  border: none;
  border-radius: 6px;
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, opacity 0.15s;
}

#j2c-app .j2c-btn-primary {
  background: #059669;
  color: #fff;
}

#j2c-app .j2c-btn-primary:hover {
  background: #047857;
}

#j2c-app .j2c-btn-secondary {
  background: #e5e7eb;
  color: #374151;
}

#j2c-app .j2c-btn-secondary:hover {
  background: #d1d5db;
}

#j2c-app .j2c-btn:disabled {
  opacity: 0.45;
  cursor: not-allowed;
}

#j2c-app .j2c-convert-row {
  display: flex;
  justify-content: center;
  margin-bottom: 1.25rem;
}

#j2c-app .j2c-btn-convert {
  padding: 0.6rem 2rem;
  background: #059669;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
  letter-spacing: 0.01em;
}

#j2c-app .j2c-btn-convert:hover {
  background: #047857;
}

#j2c-app .j2c-msg {
  font-size: 0.82rem;
  padding: 0.35rem 0.7rem;
  border-radius: 5px;
  margin-top: 0.25rem;
  display: none;
}

#j2c-app .j2c-msg.error {
  background: #fef2f2;
  color: #dc2626;
  border: 1px solid #fca5a5;
  display: block;
}

#j2c-app .j2c-msg.success {
  background: #ecfdf5;
  color: #059669;
  border: 1px solid #6ee7b7;
  display: block;
}

#j2c-app .j2c-preview-section {
  margin-top: 0.5rem;
}

#j2c-app .j2c-preview-section h2 {
  margin-bottom: 0.6rem;
}

#j2c-app .j2c-table-wrap {
  overflow-x: auto;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  max-height: 320px;
  overflow-y: auto;
}

#j2c-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.82rem;
}

#j2c-app th {
  background: #ecfdf5;
  color: #065f46;
  font-weight: 600;
  padding: 0.5rem 0.75rem;
  text-align: left;
  border-bottom: 2px solid #6ee7b7;
  white-space: nowrap;
  position: sticky;
  top: 0;
}

#j2c-app td {
  padding: 0.4rem 0.75rem;
  border-bottom: 1px solid #f3f4f6;
  color: #374151;
  max-width: 220px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

#j2c-app tr:last-child td {
  border-bottom: none;
}

#j2c-app tr:nth-child(even) td {
  background: #f9fafb;
}

#j2c-app .j2c-preview-meta {
  font-size: 0.78rem;
  color: #9ca3af;
  margin-top: 0.4rem;
}

#j2c-app .j2c-freee-cta {
  margin-top: 2rem;
  padding: 1.1rem 1.3rem;
  background: linear-gradient(135deg, #ecfdf5 0%, #d1fae5 100%);
  border: 1px solid #6ee7b7;
  border-radius: 10px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 1rem;
  justify-content: space-between;
}

#j2c-app .j2c-freee-cta-text {
  flex: 1;
  min-width: 200px;
}

#j2c-app .j2c-freee-cta-text strong {
  display: block;
  font-size: 0.95rem;
  color: #065f46;
  margin-bottom: 0.2rem;
}

#j2c-app .j2c-freee-cta-text p {
  font-size: 0.82rem;
  color: #374151;
  margin: 0;
}

#j2c-app .j2c-freee-cta-btn {
  display: inline-block;
  padding: 0.55rem 1.3rem;
  background: #059669;
  color: #fff;
  font-weight: 700;
  font-size: 0.88rem;
  border-radius: 7px;
  text-decoration: none;
  white-space: nowrap;
  transition: background 0.15s;
}

#j2c-app .j2c-freee-cta-btn:hover {
  background: #047857;
}
</style>

<div id="j2c-app">

  <div class="j2c-tabs">
    <button class="j2c-tab active" id="j2c-tab-j2c" onclick="j2cSetMode('j2c')">JSON → CSV</button>
    <button class="j2c-tab" id="j2c-tab-c2j" onclick="j2cSetMode('c2j')">CSV → JSON</button>
  </div>

  <div class="j2c-controls">
    <div class="j2c-control-group">
      <label for="j2c-delim">区切り文字</label>
      <select id="j2c-delim">
        <option value=",">カンマ（,）</option>
        <option value=";">セミコロン（;）</option>
        <option value="&#9;">タブ（⇥）</option>
        <option value="|">パイプ（|）</option>
      </select>
    </div>
    <div class="j2c-control-group">
      <label class="j2c-toggle">
        <input type="checkbox" id="j2c-header" checked>
        ヘッダー行を含む
      </label>
    </div>
    <div class="j2c-control-group">
      <label class="j2c-toggle">
        <input type="checkbox" id="j2c-flatten" checked>
        ネストJSONをフラット化
      </label>
    </div>
  </div>

  <div class="j2c-io-grid">
    <div class="j2c-pane">
      <h2 id="j2c-input-label">JSON入力</h2>
      <textarea id="j2c-input" placeholder='JSONをここに貼り付け（例）&#10;[&#10;  {"名前":"田中","年齢":30},&#10;  {"名前":"鈴木","年齢":25}&#10;]'></textarea>
      <div class="j2c-pane-actions">
        <button class="j2c-btn j2c-btn-secondary" onclick="j2cLoadSample()">サンプルを読み込む</button>
        <button class="j2c-btn j2c-btn-secondary" onclick="j2cClear()">クリア</button>
      </div>
      <div class="j2c-msg" id="j2c-input-msg"></div>
    </div>
    <div class="j2c-pane">
      <h2 id="j2c-output-label">CSV出力</h2>
      <textarea id="j2c-output" readonly placeholder="変換後の結果がここに表示されます…"></textarea>
      <div class="j2c-pane-actions">
        <button class="j2c-btn j2c-btn-primary" id="j2c-copy-btn" onclick="j2cCopy()" disabled>コピー</button>
        <button class="j2c-btn j2c-btn-primary" id="j2c-download-btn" onclick="j2cDownload()" disabled>ダウンロード</button>
      </div>
      <div class="j2c-msg" id="j2c-output-msg"></div>
    </div>
  </div>

  <div class="j2c-convert-row">
    <button class="j2c-btn-convert" onclick="j2cConvert()">変換する ↓</button>
  </div>

  <div class="j2c-preview-section" id="j2c-preview-section" style="display:none;">
    <h2>プレビュー</h2>
    <div class="j2c-table-wrap">
      <table id="j2c-preview-table"></table>
    </div>
    <div class="j2c-preview-meta" id="j2c-preview-meta"></div>
  </div>

  <div class="j2c-freee-cta">
    <div class="j2c-freee-cta-text">
      <strong>freee会計 — CSVインポートで仕訳を自動化</strong>
      <p>変換したCSVをfreeeに取り込めば、売上・経費の入力を大幅に削減。小規模事業者・フリーランスに最適。</p>
    </div>
    <a class="j2c-freee-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
  </div>

</div>

<script>
(function() {
  var mode = 'j2c';

  window.j2cSetMode = function(m) {
    mode = m;
    document.getElementById('j2c-tab-j2c').classList.toggle('active', m === 'j2c');
    document.getElementById('j2c-tab-c2j').classList.toggle('active', m === 'c2j');
    document.getElementById('j2c-input-label').textContent  = m === 'j2c' ? 'JSON入力'  : 'CSV入力';
    document.getElementById('j2c-output-label').textContent = m === 'j2c' ? 'CSV出力'  : 'JSON出力';
    document.getElementById('j2c-input').placeholder =
      m === 'j2c'
        ? 'JSONをここに貼り付け（例）\n[\n  {"名前":"田中","年齢":30},\n  {"名前":"鈴木","年齢":25}\n]'
        : 'CSVをここに貼り付け（例）\n名前,年齢\n田中,30\n鈴木,25';
    j2cClearOutput();
    hidePreview();
  };

  function flattenObj(obj, prefix) {
    prefix = prefix || '';
    var out = {};
    for (var key in obj) {
      if (!Object.prototype.hasOwnProperty.call(obj, key)) continue;
      var full = prefix ? prefix + '.' + key : key;
      var val  = obj[key];
      if (val !== null && typeof val === 'object' && !Array.isArray(val)) {
        var nested = flattenObj(val, full);
        for (var nk in nested) out[nk] = nested[nk];
      } else {
        out[full] = Array.isArray(val) ? JSON.stringify(val) : val;
      }
    }
    return out;
  }

  function csvCell(val, delim) {
    if (val === null || val === undefined) return '';
    var s = String(val);
    if (s.indexOf(delim) !== -1 || s.indexOf('"') !== -1 || s.indexOf('\n') !== -1) {
      return '"' + s.replace(/"/g, '""') + '"';
    }
    return s;
  }

  function jsonToCsv(jsonStr, delim, includeHeader, flatten) {
    var data;
    try { data = JSON.parse(jsonStr); } catch(e) { throw new Error('JSON形式が正しくありません: ' + e.message); }
    if (!Array.isArray(data)) throw new Error('JSONはオブジェクトの配列（[{...}, ...]）である必要があります。');
    if (data.length === 0) throw new Error('JSON配列が空です。');

    var rows = data.map(function(item) {
      if (typeof item !== 'object' || item === null) throw new Error('配列の各要素はオブジェクトである必要があります。');
      return flatten ? flattenObj(item) : item;
    });

    var keySeen = {};
    var keys = [];
    rows.forEach(function(r) {
      Object.keys(r).forEach(function(k) {
        if (!keySeen[k]) { keySeen[k] = true; keys.push(k); }
      });
    });

    var lines = [];
    if (includeHeader) lines.push(keys.map(function(k) { return csvCell(k, delim); }).join(delim));
    rows.forEach(function(r) {
      lines.push(keys.map(function(k) { return csvCell(r[k], delim); }).join(delim));
    });
    return { csv: lines.join('\n'), keys: keys, rows: rows };
  }

  function csvToJson(csvStr, delim, hasHeader) {
    var lines = csvStr.trim().split(/\r?\n/);
    if (lines.length === 0) throw new Error('CSVが空です。');

    function parseLine(line) {
      var cells = [];
      var cur = '';
      var inQ = false;
      for (var i = 0; i < line.length; i++) {
        var ch = line[i];
        if (inQ) {
          if (ch === '"' && line[i+1] === '"') { cur += '"'; i++; }
          else if (ch === '"') { inQ = false; }
          else { cur += ch; }
        } else {
          if (ch === '"') { inQ = true; }
          else if (ch === delim) { cells.push(cur); cur = ''; }
          else { cur += ch; }
        }
      }
      cells.push(cur);
      return cells;
    }

    var keys, dataLines;
    if (hasHeader) {
      keys = parseLine(lines[0]);
      dataLines = lines.slice(1);
    } else {
      var first = parseLine(lines[0]);
      keys = first.map(function(_, i) { return 'col' + (i+1); });
      dataLines = lines;
    }

    var rows = dataLines.filter(function(l) { return l.trim() !== ''; }).map(function(line) {
      var cells = parseLine(line);
      var obj = {};
      keys.forEach(function(k, i) {
        var v = cells[i] !== undefined ? cells[i] : '';
        if (v === 'true') obj[k] = true;
        else if (v === 'false') obj[k] = false;
        else if (v !== '' && !isNaN(Number(v))) obj[k] = Number(v);
        else obj[k] = v;
      });
      return obj;
    });

    return { json: JSON.stringify(rows, null, 2), keys: keys, rows: rows };
  }

  function renderPreview(keys, rows, total) {
    var section = document.getElementById('j2c-preview-section');
    var table   = document.getElementById('j2c-preview-table');
    var meta    = document.getElementById('j2c-preview-meta');
    section.style.display = '';

    var preview = rows.slice(0, 50);
    var thead = '<thead><tr>' + keys.map(function(k) { return '<th>' + esc(k) + '</th>'; }).join('') + '</tr></thead>';
    var tbody = '<tbody>' + preview.map(function(r) {
      return '<tr>' + keys.map(function(k) {
        var v = r[k]; if (v === null || v === undefined) v = '';
        return '<td title="' + esc(String(v)) + '">' + esc(String(v)) + '</td>';
      }).join('') + '</tr>';
    }).join('') + '</tbody>';
    table.innerHTML = thead + tbody;

    var shown = preview.length;
    meta.textContent = total + '行中' + shown + '行を表示' + (total > 50 ? '（先頭50行）' : '') + ' · ' + keys.length + '列';
  }

  function hidePreview() {
    document.getElementById('j2c-preview-section').style.display = 'none';
  }

  function esc(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function showMsg(id, text, type) {
    var el = document.getElementById(id);
    el.textContent = text;
    el.className = 'j2c-msg ' + type;
  }
  function clearMsg(id) {
    var el = document.getElementById(id);
    el.textContent = '';
    el.className = 'j2c-msg';
  }
  function setOutput(val) {
    var out = document.getElementById('j2c-output');
    out.value = val;
    var haVal = val && val.trim() !== '';
    document.getElementById('j2c-copy-btn').disabled     = !haVal;
    document.getElementById('j2c-download-btn').disabled = !haVal;
  }
  function j2cClearOutput() {
    setOutput('');
    clearMsg('j2c-input-msg');
    clearMsg('j2c-output-msg');
  }

  window.j2cClear = function() {
    document.getElementById('j2c-input').value = '';
    j2cClearOutput();
    hidePreview();
  };

  window.j2cLoadSample = function() {
    if (mode === 'j2c') {
      document.getElementById('j2c-input').value = JSON.stringify([
        { 氏名: "田中 太郎", 年齢: 30, 住所: { 都市: "東京", 郵便番号: "100-0001" }, 在籍: true },
        { 氏名: "鈴木 花子", 年齢: 25, 住所: { 都市: "大阪", 郵便番号: "530-0001" }, 在籍: false },
        { 氏名: "佐藤 一郎", 年齢: 35, 住所: { 都市: "名古屋", 郵便番号: "460-0001" }, 在籍: true }
      ], null, 2);
    } else {
      document.getElementById('j2c-input').value =
        '氏名,年齢,都市\n田中 太郎,30,東京\n鈴木 花子,25,大阪\n佐藤 一郎,35,名古屋';
    }
    j2cClearOutput();
    hidePreview();
  };

  window.j2cConvert = function() {
    clearMsg('j2c-input-msg');
    clearMsg('j2c-output-msg');
    var input  = document.getElementById('j2c-input').value.trim();
    var delim  = document.getElementById('j2c-delim').value;
    var header = document.getElementById('j2c-header').checked;
    var flatten = document.getElementById('j2c-flatten').checked;

    if (!input) {
      showMsg('j2c-input-msg', '変換するデータを入力してください。', 'error');
      document.getElementById('j2c-input').classList.add('j2c-error');
      return;
    }
    document.getElementById('j2c-input').classList.remove('j2c-error');

    try {
      if (mode === 'j2c') {
        var res = jsonToCsv(input, delim, header, flatten);
        setOutput(res.csv);
        renderPreview(res.keys, res.rows, res.rows.length);
        showMsg('j2c-output-msg', '変換完了 — ' + res.rows.length + '行 · ' + res.keys.length + '列', 'success');
      } else {
        var res = csvToJson(input, delim, header);
        setOutput(res.json);
        renderPreview(res.keys, res.rows, res.rows.length);
        showMsg('j2c-output-msg', '変換完了 — ' + res.rows.length + '行 · ' + res.keys.length + '列', 'success');
      }
    } catch(e) {
      showMsg('j2c-input-msg', e.message, 'error');
      document.getElementById('j2c-input').classList.add('j2c-error');
      setOutput('');
      hidePreview();
    }
  };

  window.j2cCopy = function() {
    var val = document.getElementById('j2c-output').value;
    if (!val) return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(val).then(function() {
        showMsg('j2c-output-msg', 'クリップボードにコピーしました！', 'success');
      }).catch(function() { fallbackCopy(val); });
    } else {
      fallbackCopy(val);
    }
  };

  function fallbackCopy(text) {
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.opacity = '0';
    document.body.appendChild(ta);
    ta.select();
    try {
      document.execCommand('copy');
      showMsg('j2c-output-msg', 'クリップボードにコピーしました！', 'success');
    } catch(e) {
      showMsg('j2c-output-msg', 'コピーに失敗しました。手動で選択してコピーしてください。', 'error');
    }
    document.body.removeChild(ta);
  }

  window.j2cDownload = function() {
    var val = document.getElementById('j2c-output').value;
    if (!val) return;
    var ext  = mode === 'j2c' ? 'csv' : 'json';
    var mime = mode === 'j2c' ? 'text/csv' : 'application/json';
    var blob = new Blob([val], { type: mime + ';charset=utf-8;' });
    var url  = URL.createObjectURL(blob);
    var a    = document.createElement('a');
    a.href     = url;
    a.download = 'converted.' + ext;
    a.style.display = 'none';
    document.body.appendChild(a);
    a.click();
    setTimeout(function() { URL.revokeObjectURL(url); document.body.removeChild(a); }, 500);
  };

})();
</script>

---

## 使い方

1. タブで変換の方向（**JSON → CSV** または **CSV → JSON**）を選択します。
2. 左パネルにデータを貼り付けるか、**サンプルを読み込む** をクリックして試します。
3. 区切り文字、ヘッダー行の有無、フラット化の設定を調整します。
4. **変換する** をクリックします。
5. **コピー** または **ダウンロード** で結果を取得します。

## ネストされたJSONについて

**ネストJSONをフラット化** を有効にすると、ネストされたオブジェクトがドット記法で展開されます。例:

```json
{ "住所": { "都市": "東京", "郵便番号": "100" } }
```

上記は `住所.都市` と `住所.郵便番号` の列に変換されます。オブジェクト内の配列はJSON文字列としてシリアライズされます。

## 区切り文字の選び方

| 名前 | 文字 | 主な用途 |
|---|---|---|
| カンマ | `,` | 標準CSV（Excel・Googleスプレッドシート） |
| セミコロン | `;` | 小数点にカンマを使う欧州ロケール |
| タブ | `⇥` | TSVファイル、スプレッドシートへの貼り付け |
| パイプ | `\|` | ログファイル、マークダウン形式の表 |

---

## 関連ツール

> Csv Editor → [Csv Editorツール](/ja/tools/csv-editor/)
> Csv To Json → [Csv To Jsonツール](/ja/tools/csv-to-json/)
> Json Diff → [Json Diffツール](/ja/tools/json-diff/)

