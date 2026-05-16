---
title: "JSONフォーマッター｜JSON整形・バリデーション・圧縮ツール【無料】"
date: 2025-05-16
description: "JSONデータを即座に整形・検証・圧縮。シンタックスハイライト、エラー検出、ツリービュー機能付き。無料のオンライン開発ツール。"
categories: ["無料ツール"]
tags: ["JSON", "フォーマッター", "バリデーター", "開発ツール", "コード"]
slug: "json-formatter"
aliases: ["/ja/tools/json-validator/", "/ja/tools/json-formatter/"]
cover:
  image: "/images/covers/json-formatter-ja.png"
  alt: "JSONフォーマッター"
ShowToc: false
---

<div id="json-app">

<style>
#json-app {
  font-family: 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  background: #1e1e2e;
  color: #cdd6f4;
  border-radius: 12px;
  padding: 20px;
  margin: 0 -16px;
}

#json-app * {
  box-sizing: border-box;
}

.json-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 16px;
  align-items: center;
}

.json-btn {
  background: #313244;
  color: #cdd6f4;
  border: 1px solid #45475a;
  border-radius: 6px;
  padding: 7px 14px;
  font-size: 13px;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
}

.json-btn:hover {
  background: #45475a;
  border-color: #89b4fa;
}

.json-btn.primary {
  background: #89b4fa;
  color: #1e1e2e;
  border-color: #89b4fa;
  font-weight: 600;
}

.json-btn.primary:hover {
  background: #b4d0ff;
  border-color: #b4d0ff;
}

.json-btn.danger {
  border-color: #f38ba8;
  color: #f38ba8;
}

.json-btn.danger:hover {
  background: #f38ba822;
}

.indent-select {
  background: #313244;
  color: #cdd6f4;
  border: 1px solid #45475a;
  border-radius: 6px;
  padding: 7px 10px;
  font-size: 13px;
  cursor: pointer;
}

.indent-select:focus {
  outline: none;
  border-color: #89b4fa;
}

.json-panes {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

@media (max-width: 700px) {
  .json-panes {
    grid-template-columns: 1fr;
  }
}

.json-pane-label {
  font-size: 11px;
  color: #6c7086;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 6px;
}

.json-textarea {
  width: 100%;
  height: 300px;
  background: #181825;
  color: #cdd6f4;
  border: 1px solid #313244;
  border-radius: 8px;
  padding: 12px;
  font-family: 'JetBrains Mono', 'Fira Code', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.6;
  resize: vertical;
  outline: none;
  transition: border-color 0.15s;
}

.json-textarea:focus {
  border-color: #89b4fa;
}

.json-textarea.error-border {
  border-color: #f38ba8;
}

.json-output {
  width: 100%;
  min-height: 300px;
  background: #181825;
  border: 1px solid #313244;
  border-radius: 8px;
  padding: 12px;
  font-family: 'JetBrains Mono', 'Fira Code', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.6;
  overflow: auto;
  white-space: pre;
  word-break: break-all;
}

.json-output.tree-mode {
  white-space: normal;
}

.json-status-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 10px;
  font-size: 12px;
  color: #6c7086;
  align-items: center;
}

.json-status-ok {
  color: #a6e3a1;
  font-weight: 600;
}

.json-status-err {
  color: #f38ba8;
  font-weight: 600;
}

.json-error-box {
  background: #2e1c24;
  border: 1px solid #f38ba8;
  border-radius: 6px;
  padding: 10px 14px;
  margin-top: 10px;
  font-size: 13px;
  color: #f38ba8;
  display: none;
}

.json-copy-notice {
  color: #a6e3a1;
  font-size: 12px;
  display: none;
}

/* Syntax highlight colors */
.jsh-string  { color: #a6e3a1; }
.jsh-number  { color: #fab387; }
.jsh-bool    { color: #cba6f7; }
.jsh-null    { color: #f38ba8; }
.jsh-key     { color: #89b4fa; }
.jsh-punct   { color: #6c7086; }

/* Tree view */
.tree-node {
  margin-left: 18px;
  position: relative;
}

.tree-toggle {
  cursor: pointer;
  user-select: none;
  display: inline-block;
  width: 16px;
  text-align: center;
  color: #89b4fa;
  font-size: 11px;
  margin-right: 2px;
}

.tree-key {
  color: #89b4fa;
  font-weight: 600;
}

.tree-string { color: #a6e3a1; }
.tree-number { color: #fab387; }
.tree-bool   { color: #cba6f7; }
.tree-null   { color: #f38ba8; }

.tree-collapsed > .tree-node-children {
  display: none;
}

.toolbar-sep {
  width: 1px;
  height: 24px;
  background: #45475a;
  margin: 0 4px;
}
</style>

<div class="json-toolbar">
  <button class="json-btn primary" onclick="jsonFormat()">整形</button>
  <select class="indent-select" id="indentSelect">
    <option value="2">インデント: 2スペース</option>
    <option value="4">インデント: 4スペース</option>
    <option value="tab">インデント: タブ</option>
  </select>
  <button class="json-btn" onclick="jsonMinify()">圧縮</button>
  <button class="json-btn" onclick="jsonValidate()">検証</button>
  <div class="toolbar-sep"></div>
  <button class="json-btn" onclick="jsonSample()">サンプル</button>
  <button class="json-btn" onclick="toggleTreeView()" id="treeBtn">ツリービュー</button>
  <div class="toolbar-sep"></div>
  <button class="json-btn" onclick="jsonCopy()">コピー</button>
  <span class="json-copy-notice" id="copyNotice">コピーしました</span>
  <button class="json-btn danger" onclick="jsonClear()">クリア</button>
</div>

<div class="json-panes">
  <div>
    <div class="json-pane-label">入力 JSON</div>
    <textarea class="json-textarea" id="jsonInput" placeholder='{"key": "value"}' oninput="onInputChange()"></textarea>
  </div>
  <div>
    <div class="json-pane-label">出力</div>
    <div class="json-output" id="jsonOutput"></div>
  </div>
</div>

<div class="json-status-bar">
  <span id="statusText">準備完了</span>
  <span id="charCount">文字数: 0</span>
  <span id="lineCount">行数: 0</span>
</div>

<div class="json-error-box" id="errorBox"></div>

<script>
(function() {
  var treeMode = false;
  var lastParsed = null;

  function getIndent() {
    var v = document.getElementById('indentSelect').value;
    if (v === 'tab') return '\t';
    return parseInt(v, 10);
  }

  function highlightJSON(str) {
    return str.replace(
      /("(\\u[a-fA-F0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+\-]?\d+)?|[{}\[\],:])/g,
      function(match) {
        if (/^"/.test(match)) {
          if (/:$/.test(match)) {
            return '<span class="jsh-key">' + escHtml(match) + '</span>';
          }
          return '<span class="jsh-string">' + escHtml(match) + '</span>';
        }
        if (/true|false/.test(match)) return '<span class="jsh-bool">' + match + '</span>';
        if (/null/.test(match))       return '<span class="jsh-null">' + match + '</span>';
        if (/[{}\[\],:]/.test(match)) return '<span class="jsh-punct">' + match + '</span>';
        return '<span class="jsh-number">' + match + '</span>';
      }
    );
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function setOutput(html) {
    var out = document.getElementById('jsonOutput');
    out.innerHTML = html;
    if (treeMode) {
      out.classList.add('tree-mode');
    } else {
      out.classList.remove('tree-mode');
    }
  }

  function setError(msg) {
    var eb = document.getElementById('errorBox');
    eb.textContent = msg;
    eb.style.display = msg ? 'block' : 'none';
    document.getElementById('jsonInput').classList.toggle('error-border', !!msg);
  }

  function setStatus(text, type) {
    var el = document.getElementById('statusText');
    el.textContent = text;
    el.className = type === 'ok' ? 'json-status-ok' : type === 'err' ? 'json-status-err' : '';
  }

  function updateCounts() {
    var val = document.getElementById('jsonInput').value;
    document.getElementById('charCount').textContent = '文字数: ' + val.length;
    document.getElementById('lineCount').textContent = '行数: ' + (val ? val.split('\n').length : 0);
  }

  window.onInputChange = function() {
    updateCounts();
    setError('');
    setStatus('準備完了');
  };

  window.jsonFormat = function() {
    var input = document.getElementById('jsonInput').value.trim();
    if (!input) { setStatus('JSONを入力してください'); return; }
    try {
      var parsed = JSON.parse(input);
      lastParsed = parsed;
      var indent = getIndent();
      var formatted = JSON.stringify(parsed, null, indent);
      document.getElementById('jsonInput').value = formatted;
      updateCounts();
      setError('');
      if (treeMode) {
        renderTree(parsed);
      } else {
        setOutput(highlightJSON(escHtml(formatted)));
      }
      setStatus('整形完了 — 有効なJSON', 'ok');
    } catch(e) {
      handleParseError(e, input);
    }
  };

  window.jsonMinify = function() {
    var input = document.getElementById('jsonInput').value.trim();
    if (!input) { setStatus('JSONを入力してください'); return; }
    try {
      var parsed = JSON.parse(input);
      lastParsed = parsed;
      var minified = JSON.stringify(parsed);
      setError('');
      if (treeMode) {
        renderTree(parsed);
      } else {
        setOutput(highlightJSON(escHtml(minified)));
      }
      setStatus('圧縮完了 — ' + minified.length + '文字', 'ok');
    } catch(e) {
      handleParseError(e, input);
    }
  };

  window.jsonValidate = function() {
    var input = document.getElementById('jsonInput').value.trim();
    if (!input) { setStatus('JSONを入力してください'); return; }
    try {
      var parsed = JSON.parse(input);
      lastParsed = parsed;
      setError('');
      setStatus('有効なJSON — 構文エラーなし', 'ok');
      setOutput('<span style="color:#a6e3a1;font-size:15px;">有効なJSON</span>');
    } catch(e) {
      handleParseError(e, input);
    }
  };

  function handleParseError(e, input) {
    lastParsed = null;
    var msg = e.message;
    var lineNum = '';
    var match = msg.match(/position (\d+)/);
    if (match) {
      var pos = parseInt(match[1], 10);
      var before = input.substring(0, pos);
      var ln = before.split('\n').length;
      lineNum = '（' + ln + '行目付近）';
    }
    setError('JSONエラー: ' + msg + lineNum);
    setStatus('無効なJSON', 'err');
    setOutput('<span style="color:#f38ba8;">JSONの解析に失敗しました。エラー詳細を確認してください。</span>');
  }

  window.jsonCopy = function() {
    var out = document.getElementById('jsonOutput');
    var text = out.innerText || out.textContent;
    if (!text.trim()) { setStatus('コピーする内容がありません'); return; }
    navigator.clipboard.writeText(text).then(function() {
      var notice = document.getElementById('copyNotice');
      notice.style.display = 'inline';
      setTimeout(function() { notice.style.display = 'none'; }, 1800);
    });
  };

  window.jsonClear = function() {
    document.getElementById('jsonInput').value = '';
    setOutput('');
    setError('');
    setStatus('準備完了');
    updateCounts();
    lastParsed = null;
    document.getElementById('jsonInput').classList.remove('error-border');
  };

  window.jsonSample = function() {
    var sample = {
      "会社情報": {
        "会社名": "株式会社サンプル",
        "設立年": 2020,
        "上場": false,
        "従業員数": 42,
        "本社": "東京都渋谷区"
      },
      "製品": [
        {
          "ID": "P001",
          "名称": "生産性管理ツール",
          "価格": 9800,
          "在庫": true,
          "タグ": ["SaaS", "AI", "クラウド"]
        },
        {
          "ID": "P002",
          "名称": "データ分析プラットフォーム",
          "価格": 29800,
          "在庫": false,
          "タグ": ["分析", "BI"]
        }
      ],
      "メモ": null
    };
    document.getElementById('jsonInput').value = JSON.stringify(sample, null, 2);
    updateCounts();
    setError('');
    setStatus('サンプルを読み込みました');
    lastParsed = sample;
    if (treeMode) {
      renderTree(sample);
    } else {
      setOutput(highlightJSON(escHtml(JSON.stringify(sample, null, 2))));
    }
  };

  window.toggleTreeView = function() {
    treeMode = !treeMode;
    var btn = document.getElementById('treeBtn');
    btn.textContent = treeMode ? 'テキストビュー' : 'ツリービュー';
    btn.style.borderColor = treeMode ? '#89b4fa' : '';
    btn.style.color = treeMode ? '#89b4fa' : '';

    var input = document.getElementById('jsonInput').value.trim();
    if (!input) return;
    try {
      var parsed = JSON.parse(input);
      lastParsed = parsed;
      if (treeMode) {
        renderTree(parsed);
      } else {
        var indent = getIndent();
        setOutput(highlightJSON(escHtml(JSON.stringify(parsed, null, indent))));
      }
    } catch(e) {
      // keep current output
    }
  };

  function renderTree(data) {
    var out = document.getElementById('jsonOutput');
    out.classList.add('tree-mode');
    out.innerHTML = buildTreeHTML(data, null, 0);
    attachTreeToggles();
  }

  function buildTreeHTML(val, key, depth) {
    var html = '';
    var keyHtml = key !== null ? '<span class="tree-key">' + escHtml(JSON.stringify(key)) + '</span>: ' : '';

    if (val === null) {
      html = '<div>' + keyHtml + '<span class="tree-null">null</span></div>';
    } else if (typeof val === 'boolean') {
      html = '<div>' + keyHtml + '<span class="tree-bool">' + val + '</span></div>';
    } else if (typeof val === 'number') {
      html = '<div>' + keyHtml + '<span class="tree-number">' + val + '</span></div>';
    } else if (typeof val === 'string') {
      html = '<div>' + keyHtml + '<span class="tree-string">' + escHtml(JSON.stringify(val)) + '</span></div>';
    } else if (Array.isArray(val)) {
      var count = val.length;
      html += '<div class="tree-collapsible">';
      html += '<span class="tree-toggle" onclick="treeToggle(this)">&#9660;</span>';
      html += keyHtml + '<span style="color:#6c7086;">[ ' + count + '件 ]</span>';
      html += '<div class="tree-node-children">';
      for (var i = 0; i < count; i++) {
        html += '<div class="tree-node">' + buildTreeHTML(val[i], i, depth+1) + '</div>';
      }
      html += '</div></div>';
    } else if (typeof val === 'object') {
      var keys = Object.keys(val);
      html += '<div class="tree-collapsible">';
      html += '<span class="tree-toggle" onclick="treeToggle(this)">&#9660;</span>';
      html += keyHtml + '<span style="color:#6c7086;">{ ' + keys.length + '件 }</span>';
      html += '<div class="tree-node-children">';
      for (var k = 0; k < keys.length; k++) {
        html += '<div class="tree-node">' + buildTreeHTML(val[keys[k]], keys[k], depth+1) + '</div>';
      }
      html += '</div></div>';
    }
    return html;
  }

  window.treeToggle = function(el) {
    var parent = el.closest('.tree-collapsible');
    parent.classList.toggle('tree-collapsed');
    el.innerHTML = parent.classList.contains('tree-collapsed') ? '&#9654;' : '&#9660;';
  };

  function attachTreeToggles() {
    // toggles are inline onclick, no extra wiring needed
  }

  updateCounts();
})();
</script>

</div>

## JSONとは

JSON（JavaScript Object Notation）は、人間にも機械にも読みやすい軽量なデータ交換フォーマットです。テキストベースで構造化データを表現でき、WebAPIのレスポンスや設定ファイル、データベースのエクスポートなど、あらゆる場面で広く利用されています。キーと値のペア、配列、ネストされたオブジェクトを組み合わせることで、複雑なデータ構造もシンプルに記述できます。

開発現場では、APIのデバッグ時に圧縮されたJSONを読みやすく整形したり、構文エラーを素早く特定したりする場面が頻繁に発生します。このツールはそういった日常的な作業をブラウザ上で即座に完結させるために設計されており、インストール不要・登録不要で誰でも無料で利用できます。

## このJSONフォーマッターの使い方

**整形**: 左の入力エリアにJSONを貼り付け、「整形」ボタンをクリックすると右側に見やすく整形されたJSONが表示されます。インデント幅（2スペース・4スペース・タブ）はドロップダウンで切り替えられます。

**圧縮**: 「圧縮」ボタンで空白・改行をすべて除去し、データ転送に適したコンパクトなJSON文字列を生成します。

**検証**: 「検証」ボタンでJSON構文の正確さをチェックします。エラーがある場合は行番号と詳細なメッセージを表示するので、どこを修正すればよいかすぐに分かります。

**ツリービュー**: 「ツリービュー」ボタンでフォルダのような折りたたみ可能なツリー表示に切り替えられます。階層の深いJSONを俯瞰したいときに便利です。

**コピー**: 整形・圧縮後の結果を「コピー」ボタンでクリップボードに一発コピーできます。

## 関連ツール

> 文字数・単語数をリアルタイムでカウント → [文字数カウンター](/ja/tools/moji-counter/)

> 安全なパスワードを即座に生成 → [パスワード生成ツール](/ja/tools/password-generator/)

> ポモドーロテクニックで集中力アップ → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)

> マークダウンエディターが必要？ → [マークダウンプレビュー](/ja/tools/markdown-preview/) — リアルタイムでプレビュー

---

**エンジニア・フリーランスの確定申告を自動化**

開発に集中したいのに、経理業務に時間を取られていませんか？クラウド会計ソフト「freee」なら、銀行口座・クレジットカードと自動連携。確定申告もワンクリック。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">

## 関連記事

- [無料で使えるAIツールおすすめ15選【2026年版・目的別に厳選】](/ja/posts/無料-ai-ツール-おすすめ/)
- [ChatGPT API初心者向け完全ガイド【2026年版・サンプルコード付き】](/ja/posts/chatgpt-api-使い方-初心者/)
- [AIでExcel作業を自動化する方法【マクロ不要で誰でもできる】](/ja/posts/ai-excel-自動化/)
