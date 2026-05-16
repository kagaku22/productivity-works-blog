---
title: "URLエンコーダー & デコーダー - 無料オンラインURL変換ツール"
date: 2025-05-16
description: "URLを即座にエンコード・デコード。特殊文字のパーセントエンコーディング変換、URL解析機能付き。開発者向け無料オンラインツール。"
categories: ["無料ツール"]
tags: ["URLエンコード", "URLデコード", "パーセントエンコーディング", "開発ツール", "Web"]
slug: "url-encoder"
aliases: ["/ja/tools/url-decoder/", "/ja/tools/urlencode/"]
cover:
  image: "/images/covers/url-encoder-ja.png"
  alt: "URLエンコーダー"
ShowToc: false
---

<div id="url-app">
<style>
#url-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1e293b;
}
#url-app * { box-sizing: border-box; }
#url-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  padding-left: 0.6rem;
  border-left: 4px solid #2563eb;
  color: #1e293b;
}
#url-app .tab-bar {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 1.25rem;
  flex-wrap: wrap;
}
#url-app .tab-btn {
  background: none;
  border: none;
  padding: 0.6rem 1.1rem;
  font-size: 0.92rem;
  font-weight: 600;
  cursor: pointer;
  color: #64748b;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
}
#url-app .tab-btn.active {
  color: #2563eb;
  border-bottom-color: #2563eb;
}
#url-app .tab-btn:hover:not(.active) { color: #2563eb; }
#url-app .tab-panel { display: none; }
#url-app .tab-panel.active { display: block; }
#url-app textarea {
  width: 100%;
  min-height: 120px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  padding: 0.75rem;
  font-size: 0.9rem;
  font-family: "Fira Mono", "Consolas", monospace;
  resize: vertical;
  outline: none;
  transition: border-color 0.15s;
  background: #f8fafc;
  color: #1e293b;
  line-height: 1.6;
}
#url-app textarea:focus { border-color: #2563eb; background: #fff; }
#url-app .mode-row {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 0.75rem;
  flex-wrap: wrap;
}
#url-app .mode-label { font-size: 0.85rem; font-weight: 600; color: #475569; }
#url-app .mode-select {
  padding: 0.35rem 0.7rem;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.88rem;
  color: #1e293b;
  background: #fff;
  cursor: pointer;
  outline: none;
}
#url-app .mode-select:focus { border-color: #2563eb; }
#url-app .realtime-row {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  color: #475569;
}
#url-app .realtime-row input[type=checkbox] { accent-color: #2563eb; width: 15px; height: 15px; cursor: pointer; }
#url-app .btn-row {
  display: flex;
  gap: 0.5rem;
  margin: 0.75rem 0;
  flex-wrap: wrap;
}
#url-app .btn {
  padding: 0.5rem 1.1rem;
  border-radius: 7px;
  border: none;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#url-app .btn:active { transform: scale(0.97); }
#url-app .btn-primary { background: #2563eb; color: #fff; }
#url-app .btn-primary:hover { background: #1d4ed8; }
#url-app .btn-secondary { background: #e2e8f0; color: #334155; }
#url-app .btn-secondary:hover { background: #cbd5e1; }
#url-app .btn-success { background: #16a34a; color: #fff; }
#url-app .btn-success:hover { background: #15803d; }
#url-app .btn-warn { background: #dc2626; color: #fff; }
#url-app .btn-warn:hover { background: #b91c1c; }
#url-app .swap-btn {
  background: none;
  border: 1.5px solid #2563eb;
  color: #2563eb;
  border-radius: 7px;
  padding: 0.5rem 0.9rem;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#url-app .swap-btn:hover { background: #eff6ff; }
#url-app .output-label {
  font-size: 0.82rem;
  font-weight: 600;
  color: #64748b;
  margin-bottom: 0.3rem;
}
#url-app .char-count {
  font-size: 0.78rem;
  color: #94a3b8;
  text-align: right;
  margin-top: 0.3rem;
}
/* URL解析 */
#url-app .parse-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
  margin-top: 0.75rem;
}
#url-app .parse-table th {
  text-align: left;
  padding: 0.5rem 0.75rem;
  background: #eff6ff;
  color: #2563eb;
  font-weight: 700;
  border-bottom: 2px solid #bfdbfe;
}
#url-app .parse-table td {
  padding: 0.45rem 0.75rem;
  border-bottom: 1px solid #e2e8f0;
  vertical-align: top;
  word-break: break-all;
}
#url-app .parse-table tr:last-child td { border-bottom: none; }
#url-app .parse-table td:first-child { color: #475569; font-weight: 600; width: 130px; white-space: nowrap; }
#url-app .parse-table td:last-child { color: #1e293b; font-family: "Fira Mono", monospace; }
#url-app .badge {
  display: inline-block;
  background: #dbeafe;
  color: #2563eb;
  border-radius: 4px;
  padding: 0.1rem 0.45rem;
  font-size: 0.78rem;
  font-weight: 600;
  margin: 0.1rem;
}
#url-app .empty-msg { color: #94a3b8; font-style: italic; font-size: 0.85rem; }
/* クエリビルダー */
#url-app .qb-row {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 0.5rem;
  align-items: center;
}
#url-app .qb-input {
  flex: 1;
  padding: 0.45rem 0.6rem;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.88rem;
  outline: none;
  transition: border-color 0.15s;
}
#url-app .qb-input:focus { border-color: #2563eb; }
#url-app .qb-sep { color: #94a3b8; font-weight: 700; flex-shrink: 0; }
#url-app .qb-remove {
  background: none;
  border: 1.5px solid #fca5a5;
  color: #dc2626;
  border-radius: 5px;
  padding: 0.3rem 0.6rem;
  cursor: pointer;
  font-size: 0.82rem;
  font-weight: 700;
  flex-shrink: 0;
}
#url-app .qb-remove:hover { background: #fef2f2; }
#url-app .qb-result {
  background: #f1f5f9;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  padding: 0.75rem;
  font-family: "Fira Mono", monospace;
  font-size: 0.88rem;
  word-break: break-all;
  min-height: 48px;
  color: #1e293b;
  margin-top: 0.75rem;
}
/* 一括モード */
#url-app .bulk-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.82rem;
  margin-top: 0.75rem;
}
#url-app .bulk-table th {
  background: #eff6ff;
  color: #2563eb;
  padding: 0.45rem 0.6rem;
  text-align: left;
  font-weight: 700;
  border-bottom: 2px solid #bfdbfe;
}
#url-app .bulk-table td {
  padding: 0.4rem 0.6rem;
  border-bottom: 1px solid #e2e8f0;
  word-break: break-all;
  font-family: "Fira Mono", monospace;
  vertical-align: top;
}
#url-app .bulk-table tr:nth-child(even) td { background: #f8fafc; }
#url-app .bulk-table .err { color: #dc2626; }
/* コピー完了 */
#url-app .copy-toast {
  display: inline-block;
  background: #16a34a;
  color: #fff;
  font-size: 0.78rem;
  border-radius: 4px;
  padding: 0.2rem 0.6rem;
  margin-left: 0.5rem;
  opacity: 0;
  transition: opacity 0.3s;
}
#url-app .copy-toast.show { opacity: 1; }
@media (max-width: 600px) {
  #url-app .mode-row { gap: 0.5rem; }
  #url-app .parse-table td:first-child { width: 90px; }
  #url-app .qb-row { flex-wrap: wrap; }
  #url-app .btn-row { gap: 0.4rem; }
}
</style>

<!-- タブバー -->
<div class="tab-bar">
  <button class="tab-btn active" onclick="urlApp.switchTab('encode')">エンコード / デコード</button>
  <button class="tab-btn" onclick="urlApp.switchTab('parse')">URL解析</button>
  <button class="tab-btn" onclick="urlApp.switchTab('builder')">クエリビルダー</button>
  <button class="tab-btn" onclick="urlApp.switchTab('bulk')">一括処理</button>
</div>

<!-- タブ1: エンコード/デコード -->
<div id="tab-encode" class="tab-panel active">
  <div class="mode-row">
    <span class="mode-label">モード:</span>
    <select class="mode-select" id="enc-mode" onchange="urlApp.onModeChange()">
      <option value="component">encodeURIComponent（推奨）</option>
      <option value="uri">encodeURI（URL全体）</option>
    </select>
    <label class="realtime-row">
      <input type="checkbox" id="enc-realtime" checked onchange="urlApp.onRealtimeChange()">
      リアルタイム変換
    </label>
  </div>

  <div class="output-label">入力テキスト</div>
  <textarea id="enc-input" placeholder="エンコードまたはデコードするテキストを入力…" oninput="urlApp.onEncInput()"></textarea>
  <div class="char-count" id="enc-in-count">0 文字</div>

  <div class="btn-row">
    <button class="btn btn-primary" onclick="urlApp.encode()">エンコード</button>
    <button class="btn btn-primary" onclick="urlApp.decode()">デコード</button>
    <button class="swap-btn" onclick="urlApp.swap()">&#8645; スワップ</button>
    <button class="btn btn-secondary" onclick="urlApp.clearEnc()">クリア</button>
    <span class="copy-toast" id="enc-toast">コピー完了!</span>
  </div>

  <div class="output-label">出力</div>
  <textarea id="enc-output" placeholder="変換結果がここに表示されます…" readonly></textarea>
  <div class="char-count" id="enc-out-count">0 文字</div>
  <div class="btn-row" style="margin-top:0.5rem;">
    <button class="btn btn-success" onclick="urlApp.copyEnc()">出力をコピー</button>
  </div>
</div>

<!-- タブ2: URL解析 -->
<div id="tab-parse" class="tab-panel">
  <div class="output-label">解析するURLを入力</div>
  <textarea id="parse-input" rows="3" placeholder="https://example.com:8080/path/to/page?key=value&foo=bar#section" oninput="urlApp.parseUrl()"></textarea>
  <div class="btn-row">
    <button class="btn btn-primary" onclick="urlApp.parseUrl()">解析</button>
    <button class="btn btn-secondary" onclick="urlApp.clearParse()">クリア</button>
  </div>
  <div id="parse-result"></div>
</div>

<!-- タブ3: クエリビルダー -->
<div id="tab-builder" class="tab-panel">
  <div class="output-label">ベースURL（任意）</div>
  <input type="text" class="qb-input" id="qb-base" placeholder="https://example.com/search" oninput="urlApp.buildQuery()" style="width:100%;margin-bottom:0.75rem;">

  <div style="display:flex;align-items:center;gap:0.75rem;margin-bottom:0.5rem;">
    <span class="mode-label">パラメータ</span>
    <button class="btn btn-primary" onclick="urlApp.addQbRow()" style="padding:0.35rem 0.8rem;font-size:0.82rem;">+ 追加</button>
  </div>
  <div id="qb-rows"></div>

  <div class="output-label" style="margin-top:1rem;">生成されたURL / クエリ文字列</div>
  <div class="qb-result" id="qb-result">パラメータを追加すると生成されます</div>
  <div class="btn-row" style="margin-top:0.5rem;">
    <button class="btn btn-success" onclick="urlApp.copyQb()">コピー</button>
    <button class="btn btn-secondary" onclick="urlApp.clearQb()">クリア</button>
    <span class="copy-toast" id="qb-toast">コピー完了!</span>
  </div>
</div>

<!-- タブ4: 一括処理 -->
<div id="tab-bulk" class="tab-panel">
  <div class="mode-row">
    <span class="mode-label">操作:</span>
    <select class="mode-select" id="bulk-op">
      <option value="enc-component">エンコード (encodeURIComponent)</option>
      <option value="enc-uri">エンコード (encodeURI)</option>
      <option value="dec">デコード</option>
    </select>
  </div>
  <div class="output-label">URLリスト（1行に1つ）</div>
  <textarea id="bulk-input" rows="8" placeholder="https://example.com/search?q=日本語&#10;hello world&#10;https://example.com/path?foo=bar&baz=qux"></textarea>
  <div class="btn-row">
    <button class="btn btn-primary" onclick="urlApp.runBulk()">一括変換</button>
    <button class="btn btn-secondary" onclick="urlApp.clearBulk()">クリア</button>
    <button class="btn btn-success" onclick="urlApp.copyBulkResult()">結果をコピー</button>
    <span class="copy-toast" id="bulk-toast">コピー完了!</span>
  </div>
  <div id="bulk-result"></div>
</div>

<script>
(function() {
  var urlApp = window.urlApp = {};

  // --- タブ切替 ---
  urlApp.switchTab = function(name) {
    document.querySelectorAll('#url-app .tab-panel').forEach(function(p) { p.classList.remove('active'); });
    document.querySelectorAll('#url-app .tab-btn').forEach(function(b) { b.classList.remove('active'); });
    document.getElementById('tab-' + name).classList.add('active');
    var btns = document.querySelectorAll('#url-app .tab-btn');
    var map = { encode: 0, parse: 1, builder: 2, bulk: 3 };
    btns[map[name]].classList.add('active');
  };

  // --- エンコード/デコード ---
  urlApp.getMode = function() {
    return document.getElementById('enc-mode').value;
  };
  urlApp.isRealtime = function() {
    return document.getElementById('enc-realtime').checked;
  };
  urlApp.onEncInput = function() {
    var el = document.getElementById('enc-input');
    document.getElementById('enc-in-count').textContent = el.value.length + ' 文字';
    if (urlApp.isRealtime()) urlApp.encode();
  };
  urlApp.onModeChange = function() {
    var inp = document.getElementById('enc-input').value;
    if (inp) urlApp.encode();
  };
  urlApp.onRealtimeChange = function() {};
  urlApp.encode = function() {
    var inp = document.getElementById('enc-input').value;
    var out = '';
    try {
      if (urlApp.getMode() === 'component') {
        out = encodeURIComponent(inp);
      } else {
        out = encodeURI(inp);
      }
    } catch(e) { out = 'エラー: ' + e.message; }
    document.getElementById('enc-output').value = out;
    document.getElementById('enc-out-count').textContent = out.length + ' 文字';
  };
  urlApp.decode = function() {
    var inp = document.getElementById('enc-input').value;
    var out = '';
    try {
      out = decodeURIComponent(inp.replace(/\+/g, ' '));
    } catch(e) {
      try { out = decodeURI(inp); }
      catch(e2) { out = 'デコードエラー: 不正なエンコード文字列です'; }
    }
    document.getElementById('enc-output').value = out;
    document.getElementById('enc-out-count').textContent = out.length + ' 文字';
  };
  urlApp.swap = function() {
    var inp = document.getElementById('enc-input');
    var out = document.getElementById('enc-output');
    var tmp = inp.value;
    inp.value = out.value;
    out.value = tmp;
    document.getElementById('enc-in-count').textContent = inp.value.length + ' 文字';
    document.getElementById('enc-out-count').textContent = out.value.length + ' 文字';
  };
  urlApp.clearEnc = function() {
    document.getElementById('enc-input').value = '';
    document.getElementById('enc-output').value = '';
    document.getElementById('enc-in-count').textContent = '0 文字';
    document.getElementById('enc-out-count').textContent = '0 文字';
  };
  urlApp.copyEnc = function() {
    var val = document.getElementById('enc-output').value;
    urlApp._copy(val, 'enc-toast');
  };

  // --- URL解析 ---
  urlApp.parseUrl = function() {
    var raw = document.getElementById('parse-input').value.trim();
    var el = document.getElementById('parse-result');
    if (!raw) { el.innerHTML = ''; return; }
    var url;
    try { url = new URL(raw); } catch(e) {
      el.innerHTML = '<p style="color:#dc2626;font-size:0.88rem;">無効なURL: プロトコル（https://など）を含む完全なURLを入力してください。</p>';
      return;
    }
    var params = [];
    url.searchParams.forEach(function(v, k) { params.push({ k: k, v: v }); });
    var paramHtml = '';
    if (params.length === 0) {
      paramHtml = '<span class="empty-msg">なし</span>';
    } else {
      params.forEach(function(p) {
        paramHtml += '<span class="badge">' + esc(p.k) + '=' + esc(p.v) + '</span> ';
      });
    }
    var rows = [
      ['プロトコル', url.protocol],
      ['ホスト', url.hostname],
      ['ポート', url.port || '<span class="empty-msg">（デフォルト）</span>'],
      ['パス', url.pathname],
      ['クエリ文字列', url.search || '<span class="empty-msg">なし</span>'],
      ['クエリパラメータ', paramHtml],
      ['フラグメント (#)', url.hash || '<span class="empty-msg">なし</span>'],
      ['オリジン', url.origin],
      ['デコード済みパス', decodeURIComponent(url.pathname)],
    ];
    var html = '<table class="parse-table"><thead><tr><th>コンポーネント</th><th>値</th></tr></thead><tbody>';
    rows.forEach(function(r) {
      html += '<tr><td>' + r[0] + '</td><td>' + (r[1] === '' ? '<span class="empty-msg">なし</span>' : r[1]) + '</td></tr>';
    });
    html += '</tbody></table>';
    el.innerHTML = html;
  };
  urlApp.clearParse = function() {
    document.getElementById('parse-input').value = '';
    document.getElementById('parse-result').innerHTML = '';
  };

  // --- クエリビルダー ---
  var qbRows = [];
  urlApp.addQbRow = function(k, v) {
    var id = Date.now() + Math.random();
    qbRows.push({ id: id, k: k || '', v: v || '' });
    urlApp._renderQbRows();
    urlApp.buildQuery();
  };
  urlApp._renderQbRows = function() {
    var container = document.getElementById('qb-rows');
    var html = '';
    qbRows.forEach(function(row) {
      html += '<div class="qb-row" id="qbrow-' + row.id + '">'
        + '<input class="qb-input" placeholder="キー" value="' + esc(row.k) + '" oninput="urlApp._qbUpdate(\'' + row.id + '\',\'k\',this.value)">'
        + '<span class="qb-sep">=</span>'
        + '<input class="qb-input" placeholder="値" value="' + esc(row.v) + '" oninput="urlApp._qbUpdate(\'' + row.id + '\',\'v\',this.value)">'
        + '<button class="qb-remove" onclick="urlApp.removeQbRow(\'' + row.id + '\')">削除</button>'
        + '</div>';
    });
    container.innerHTML = html;
  };
  urlApp._qbUpdate = function(id, field, val) {
    qbRows.forEach(function(r) { if (String(r.id) === String(id)) r[field] = val; });
    urlApp.buildQuery();
  };
  urlApp.removeQbRow = function(id) {
    qbRows = qbRows.filter(function(r) { return String(r.id) !== String(id); });
    urlApp._renderQbRows();
    urlApp.buildQuery();
  };
  urlApp.buildQuery = function() {
    var base = document.getElementById('qb-base').value.trim();
    var parts = [];
    qbRows.forEach(function(r) {
      if (r.k) parts.push(encodeURIComponent(r.k) + '=' + encodeURIComponent(r.v));
    });
    var qs = parts.join('&');
    var result = '';
    if (base) {
      result = base + (qs ? (base.indexOf('?') >= 0 ? '&' : '?') + qs : '');
    } else {
      result = qs || '';
    }
    document.getElementById('qb-result').textContent = result || 'パラメータを追加すると生成されます';
  };
  urlApp.copyQb = function() {
    var val = document.getElementById('qb-result').textContent;
    if (val === 'パラメータを追加すると生成されます') return;
    urlApp._copy(val, 'qb-toast');
  };
  urlApp.clearQb = function() {
    document.getElementById('qb-base').value = '';
    qbRows = [];
    urlApp._renderQbRows();
    urlApp.buildQuery();
  };

  // --- 一括処理 ---
  var bulkResultData = [];
  urlApp.runBulk = function() {
    var lines = document.getElementById('bulk-input').value.split('\n');
    var op = document.getElementById('bulk-op').value;
    bulkResultData = [];
    var html = '<table class="bulk-table"><thead><tr><th>#</th><th>元の値</th><th>変換後</th></tr></thead><tbody>';
    lines.forEach(function(line, i) {
      var orig = line;
      var result = '';
      var isErr = false;
      try {
        if (op === 'enc-component') result = encodeURIComponent(orig);
        else if (op === 'enc-uri') result = encodeURI(orig);
        else result = decodeURIComponent(orig.replace(/\+/g, ' '));
      } catch(e) {
        result = 'エラー: ' + e.message;
        isErr = true;
      }
      bulkResultData.push(result);
      html += '<tr><td style="color:#94a3b8;width:2rem;">' + (i+1) + '</td>'
        + '<td>' + esc(orig) + '</td>'
        + '<td class="' + (isErr ? 'err' : '') + '">' + esc(result) + '</td></tr>';
    });
    html += '</tbody></table>';
    document.getElementById('bulk-result').innerHTML = html;
  };
  urlApp.clearBulk = function() {
    document.getElementById('bulk-input').value = '';
    document.getElementById('bulk-result').innerHTML = '';
    bulkResultData = [];
  };
  urlApp.copyBulkResult = function() {
    if (!bulkResultData.length) return;
    urlApp._copy(bulkResultData.join('\n'), 'bulk-toast');
  };

  // --- ユーティリティ ---
  function esc(s) {
    if (s === undefined || s === null) return '';
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }
  urlApp._copy = function(text, toastId) {
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(function() { urlApp._showToast(toastId); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      urlApp._showToast(toastId);
    }
  };
  urlApp._showToast = function(id) {
    var el = document.getElementById(id);
    if (!el) return;
    el.classList.add('show');
    setTimeout(function() { el.classList.remove('show'); }, 1800);
  };

  // クエリビルダー初期行
  urlApp.addQbRow('q', '');
  urlApp.addQbRow('lang', 'ja');
})();
</script>
</div>

---

## URLエンコード（パーセントエンコーディング）とは

URLエンコードとは、URLに使用できない特殊文字を `%XX` 形式（16進数）に変換する仕組みです。日本語や空白、記号などが含まれる文字列をURLで安全に送受信するために不可欠な技術です。

**`encodeURIComponent` と `encodeURI` の違い**

| 関数 | 用途 | エンコードされる文字 |
|------|------|----------------------|
| `encodeURIComponent` | クエリパラメータ値など部分文字列 | `:/?#[]@!$&'()*+,;=` も含む |
| `encodeURI` | URL全体 | スキーム・ホスト・パスは保持 |

通常のAPI通信やフォーム送信では **encodeURIComponent** を使用するのが推奨です。

---

## 使い方ガイド

1. **エンコード/デコード** タブ — テキストを入力してボタンを押すだけ。リアルタイムモードをオンにすると入力と同時に変換されます。
2. **URL解析** タブ — URLを貼り付けると、プロトコル・ホスト・パス・クエリパラメータ・フラグメントを分解表示します。
3. **クエリビルダー** タブ — キー・値ペアを追加してクエリ文字列を自動生成。ベースURLと組み合わせて完全なURLも生成できます。
4. **一括処理** タブ — 複数のURLを一度にエンコード/デコード。改行区切りで貼り付けるだけです。

---

## 関連ツール

- [Base64エンコーダー](../base64-encoder/) — バイナリデータや文字列をBase64形式に変換・デコード
- [JSONフォーマッター](../json-formatter/) — JSONの整形・圧縮・バリデーション
- [正規表現テスター](../regex-tester/) — 正規表現のリアルタイムマッチングとデバッグ

---

**Web開発者の確定申告を効率化**

URL設計にこだわるように、経理もスマートに。クラウド会計ソフト「freee」でバックオフィス業務を自動化しませんか？

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
