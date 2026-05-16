---
title: "JSONパスファインダー — ツリーエクスプローラー"
date: 2025-05-16
description: "インタラクティブなツリービューでJSONデータを探索。ノードをクリックしてJSONPath式を取得。検索・パスコピー・値の検査を即座に。"
categories: ["無料ツール"]
slug: "json-path-finder"
ShowToc: false
cover:
  image: "/images/covers/json-path-finder-ja.png"
  alt: "JSONパスファインダー"
---

JSONを貼り付けるだけで、インタラクティブなツリービューで構造を即座に探索できます。ノードをクリックするとドット記法・ブラケット記法の **JSONPath式** が表示されます。プラグイン不要、ブラウザ完結、無料です。

<div id="jpf-app">
<style>
  #jpf-app *,
  #jpf-app *::before,
  #jpf-app *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #jpf-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Kaku Gothic ProN", "Yu Gothic", Meiryo, sans-serif;
    font-size: 15px;
    color: #1a1a2e;
    background: #f7f9fc;
    border-radius: 12px;
    padding: 20px;
    margin: 24px 0;
    border: 1px solid #dde3ef;
  }
  #jpf-app *,
  #jpf-app *::before,
  #jpf-app *::after {
    box-sizing: border-box;
  }
  #jpf-app .jpf-toolbar {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 14px;
    align-items: center;
  }
  #jpf-app .jpf-search-wrap {
    flex: 1;
    min-width: 180px;
    position: relative;
  }
  #jpf-app .jpf-search {
    width: 100%;
    padding: 8px 12px 8px 34px;
    border: 1px solid #c8d0e0;
    border-radius: 7px;
    font-size: 14px;
    background: #fff;
    outline: none;
    transition: border-color .2s;
  }
  #jpf-app .jpf-search:focus { border-color: #4f8ef7; }
  #jpf-app .jpf-search-icon {
    position: absolute;
    left: 10px;
    top: 50%;
    transform: translateY(-50%);
    color: #8896b3;
    font-size: 14px;
    pointer-events: none;
  }
  #jpf-app .jpf-btn {
    padding: 8px 14px;
    border: 1px solid #c8d0e0;
    border-radius: 7px;
    background: #fff;
    font-size: 13px;
    cursor: pointer;
    color: #3a4a6b;
    transition: background .15s, border-color .15s;
    white-space: nowrap;
  }
  #jpf-app .jpf-btn:hover { background: #eef2fb; border-color: #4f8ef7; }
  #jpf-app .jpf-btn.jpf-btn-primary {
    background: #4f8ef7;
    color: #fff;
    border-color: #4f8ef7;
  }
  #jpf-app .jpf-btn.jpf-btn-primary:hover { background: #3a7de0; }
  #jpf-app .jpf-btn.jpf-btn-danger {
    border-color: #e05a5a;
    color: #c0392b;
  }
  #jpf-app .jpf-btn.jpf-btn-danger:hover { background: #fdecea; }
  #jpf-app .jpf-presets {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 12px;
  }
  #jpf-app .jpf-preset-btn {
    padding: 5px 11px;
    border: 1px solid #c8d0e0;
    border-radius: 20px;
    background: #fff;
    font-size: 12px;
    cursor: pointer;
    color: #4f6394;
    transition: background .15s, border-color .15s;
  }
  #jpf-app .jpf-preset-btn:hover { background: #eef2fb; border-color: #4f8ef7; }
  #jpf-app .jpf-label {
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: .05em;
    color: #7a88a8;
    margin-bottom: 5px;
  }
  #jpf-app .jpf-input-area {
    width: 100%;
    min-height: 130px;
    padding: 12px;
    border: 1px solid #c8d0e0;
    border-radius: 8px;
    font-family: "SF Mono", "Fira Code", "Cascadia Code", monospace;
    font-size: 13px;
    background: #fff;
    resize: vertical;
    outline: none;
    transition: border-color .2s;
    line-height: 1.55;
    color: #1a1a2e;
  }
  #jpf-app .jpf-input-area:focus { border-color: #4f8ef7; }
  #jpf-app .jpf-input-area.jpf-error { border-color: #e05a5a; }
  #jpf-app .jpf-error-msg {
    display: none;
    color: #c0392b;
    font-size: 13px;
    margin-top: 6px;
    padding: 7px 10px;
    background: #fdecea;
    border-radius: 6px;
    border-left: 3px solid #e05a5a;
  }
  #jpf-app .jpf-stats-bar {
    display: flex;
    flex-wrap: wrap;
    gap: 14px;
    padding: 9px 14px;
    background: #eef2fb;
    border-radius: 8px;
    margin: 12px 0;
    font-size: 13px;
    color: #4a5a80;
  }
  #jpf-app .jpf-stat { display: flex; align-items: center; gap: 5px; }
  #jpf-app .jpf-stat-val { font-weight: 700; color: #2d3f6e; }
  #jpf-app .jpf-path-box {
    background: #fff;
    border: 1px solid #c8d0e0;
    border-radius: 8px;
    padding: 12px 14px;
    margin-bottom: 12px;
    min-height: 56px;
    display: none;
  }
  #jpf-app .jpf-path-box.jpf-active { display: block; }
  #jpf-app .jpf-path-row {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    margin-bottom: 6px;
    flex-wrap: wrap;
  }
  #jpf-app .jpf-path-row:last-child { margin-bottom: 0; }
  #jpf-app .jpf-path-label {
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    color: #7a88a8;
    min-width: 72px;
    padding-top: 2px;
    letter-spacing: .04em;
  }
  #jpf-app .jpf-path-val {
    flex: 1;
    font-family: "SF Mono", "Fira Code", monospace;
    font-size: 13px;
    color: #1a5fc8;
    word-break: break-all;
    background: #f0f5ff;
    padding: 3px 8px;
    border-radius: 5px;
    min-width: 0;
  }
  #jpf-app .jpf-copy-inline {
    flex-shrink: 0;
    padding: 3px 9px;
    border: 1px solid #c8d0e0;
    border-radius: 5px;
    background: #fff;
    font-size: 12px;
    cursor: pointer;
    color: #4f6394;
    transition: background .15s;
  }
  #jpf-app .jpf-copy-inline:hover { background: #eef2fb; }
  #jpf-app .jpf-copy-inline.jpf-copied {
    background: #e6f9ef;
    border-color: #2ecc71;
    color: #27ae60;
  }
  #jpf-app .jpf-value-preview {
    margin-top: 8px;
    padding: 8px 12px;
    background: #fafbff;
    border: 1px solid #e0e7f5;
    border-radius: 6px;
    font-family: "SF Mono", "Fira Code", monospace;
    font-size: 13px;
    word-break: break-all;
    color: #2d3f6e;
    display: flex;
    gap: 10px;
    align-items: flex-start;
    flex-wrap: wrap;
  }
  #jpf-app .jpf-value-text { flex: 1; min-width: 0; }
  #jpf-app .jpf-type-badge {
    display: inline-flex;
    align-items: center;
    padding: 2px 8px;
    border-radius: 4px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: .03em;
    text-transform: uppercase;
    flex-shrink: 0;
  }
  #jpf-app .jpf-type-string  { background: #e8f5e9; color: #2e7d32; }
  #jpf-app .jpf-type-number  { background: #e3f2fd; color: #1565c0; }
  #jpf-app .jpf-type-boolean { background: #fff3e0; color: #e65100; }
  #jpf-app .jpf-type-null    { background: #f3e5f5; color: #6a1b9a; }
  #jpf-app .jpf-type-object  { background: #e8eaf6; color: #283593; }
  #jpf-app .jpf-type-array   { background: #fce4ec; color: #880e4f; }
  #jpf-app .jpf-main-layout {
    display: grid;
    grid-template-columns: 1fr;
    gap: 12px;
  }
  #jpf-app .jpf-tree-wrap {
    background: #fff;
    border: 1px solid #dde3ef;
    border-radius: 8px;
    padding: 12px;
    min-height: 200px;
    overflow-x: auto;
  }
  #jpf-app .jpf-tree-empty {
    color: #9aa5be;
    text-align: center;
    padding: 40px 20px;
    font-size: 14px;
  }
  #jpf-app .jpf-node {
    user-select: none;
    line-height: 1.6;
  }
  #jpf-app .jpf-node-row {
    display: flex;
    align-items: baseline;
    gap: 4px;
    padding: 2px 4px;
    border-radius: 5px;
    cursor: pointer;
    transition: background .1s;
    flex-wrap: nowrap;
  }
  #jpf-app .jpf-node-row:hover { background: #eef2fb; }
  #jpf-app .jpf-node-row.jpf-selected { background: #dce8ff; }
  #jpf-app .jpf-node-row.jpf-search-match { background: #fff8dc; }
  #jpf-app .jpf-node-row.jpf-selected.jpf-search-match { background: #c8dfff; }
  #jpf-app .jpf-toggle {
    display: inline-block;
    width: 16px;
    font-size: 11px;
    color: #7a88a8;
    text-align: center;
    cursor: pointer;
    flex-shrink: 0;
    transition: transform .15s;
  }
  #jpf-app .jpf-key {
    color: #8b2252;
    font-family: "SF Mono", "Fira Code", monospace;
    font-size: 13px;
    font-weight: 600;
    flex-shrink: 0;
  }
  #jpf-app .jpf-colon { color: #888; font-size: 13px; flex-shrink: 0; }
  #jpf-app .jpf-val-inline {
    font-family: "SF Mono", "Fira Code", monospace;
    font-size: 13px;
    min-width: 0;
    word-break: break-word;
  }
  #jpf-app .jpf-val-string  { color: #1e7c1e; }
  #jpf-app .jpf-val-number  { color: #1565c0; }
  #jpf-app .jpf-val-boolean { color: #e65100; }
  #jpf-app .jpf-val-null    { color: #6a1b9a; font-style: italic; }
  #jpf-app .jpf-val-collapsed { color: #7a88a8; font-size: 12px; }
  #jpf-app .jpf-children {
    margin-left: 20px;
    border-left: 1px dashed #d0d8ec;
    padding-left: 8px;
  }
  #jpf-app .jpf-node-count {
    font-size: 11px;
    color: #9aa5be;
    margin-left: 4px;
    flex-shrink: 0;
  }
  #jpf-app .jpf-actions-row {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 14px;
  }
  #jpf-app .jpf-toast {
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: #2d3f6e;
    color: #fff;
    padding: 10px 18px;
    border-radius: 8px;
    font-size: 14px;
    z-index: 9999;
    opacity: 0;
    pointer-events: none;
    transition: opacity .3s;
    box-shadow: 0 4px 16px rgba(0,0,0,.18);
  }
  #jpf-app .jpf-toast.jpf-show { opacity: 1; }
  @media (max-width: 600px) {
    #jpf-app { padding: 14px; }
    #jpf-app .jpf-path-label { min-width: 56px; font-size: 10px; }
    #jpf-app .jpf-path-val { font-size: 12px; }
    #jpf-app .jpf-stats-bar { gap: 8px; font-size: 12px; }
    #jpf-app .jpf-btn { padding: 7px 10px; font-size: 12px; }
  }
</style>

<div class="jpf-label">サンプルプリセット</div>
<div class="jpf-presets">
  <button class="jpf-preset-btn" data-preset="user">ユーザー情報</button>
  <button class="jpf-preset-btn" data-preset="ecommerce">ECオーダー</button>
  <button class="jpf-preset-btn" data-preset="github">GitHub API</button>
  <button class="jpf-preset-btn" data-preset="nested">深いネスト</button>
</div>

<div class="jpf-label">JSONを貼り付け</div>
<textarea class="jpf-input-area" id="jpfInput" placeholder='JSONをここに貼り付け、例: {"name": "山田太郎", "age": 30}'></textarea>
<div class="jpf-error-msg" id="jpfError"></div>

<div class="jpf-toolbar" style="margin-top:10px;">
  <div class="jpf-search-wrap">
    <span class="jpf-search-icon">&#128269;</span>
    <input type="text" class="jpf-search" id="jpfSearch" placeholder="キーまたは値を検索..." />
  </div>
  <button class="jpf-btn jpf-btn-primary" id="jpfParse">探索する</button>
  <button class="jpf-btn" id="jpfExpandAll">すべて展開</button>
  <button class="jpf-btn" id="jpfCollapseAll">すべて折りたたむ</button>
  <button class="jpf-btn jpf-btn-danger" id="jpfClear">クリア</button>
</div>

<div class="jpf-stats-bar" id="jpfStats" style="display:none;">
  <div class="jpf-stat">ノード数: <span class="jpf-stat-val" id="jpfStatNodes">0</span></div>
  <div class="jpf-stat">キー数: <span class="jpf-stat-val" id="jpfStatKeys">0</span></div>
  <div class="jpf-stat">配列数: <span class="jpf-stat-val" id="jpfStatArrays">0</span></div>
  <div class="jpf-stat">最大深度: <span class="jpf-stat-val" id="jpfStatDepth">0</span></div>
  <div class="jpf-stat">一致数: <span class="jpf-stat-val" id="jpfStatMatches" style="display:none">0</span></div>
</div>

<div class="jpf-path-box" id="jpfPathBox">
  <div class="jpf-path-row">
    <span class="jpf-path-label">ドット記法</span>
    <span class="jpf-path-val" id="jpfDotPath"></span>
    <button class="jpf-copy-inline" data-target="dot">コピー</button>
  </div>
  <div class="jpf-path-row">
    <span class="jpf-path-label">ブラケット</span>
    <span class="jpf-path-val" id="jpfBracketPath"></span>
    <button class="jpf-copy-inline" data-target="bracket">コピー</button>
  </div>
  <div class="jpf-value-preview" id="jpfValuePreview">
    <span class="jpf-value-text" id="jpfValueText"></span>
    <button class="jpf-copy-inline" data-target="value">値をコピー</button>
  </div>
</div>

<div class="jpf-tree-wrap">
  <div class="jpf-tree-empty" id="jpfEmpty">上にJSONを貼り付けて <strong>探索する</strong> をクリックしてください。</div>
  <div id="jpfTree"></div>
</div>

<div class="jpf-actions-row">
  <button class="jpf-btn" id="jpfCopyDotAll">ドットパスをコピー</button>
  <button class="jpf-btn" id="jpfCopyBracketAll">ブラケットパスをコピー</button>
  <button class="jpf-btn" id="jpfCopyVal">値をコピー</button>
</div>

<div class="jpf-toast" id="jpfToast"></div>

<script>
(function() {
  var el = function(id) { return document.getElementById(id); };

  var presets = {
    user: {
      "id": 1,
      "名前": "山田太郎",
      "メール": "yamada@example.com",
      "年齢": 30,
      "有効": true,
      "住所": {
        "都道府県": "東京都",
        "市区町村": "渋谷区",
        "番地": "1-2-3"
      },
      "ロール": ["管理者", "編集者"],
      "設定": {
        "テーマ": "ダーク",
        "通知": { "メール": true, "SMS": false }
      },
      "作成日時": "2024-01-15T09:30:00Z"
    },
    ecommerce: {
      "注文ID": "ORD-2024-88821",
      "ステータス": "発送済み",
      "顧客": { "id": 42, "氏名": "鈴木花子", "ランク": "ゴールド" },
      "商品": [
        { "SKU": "WIDGET-A", "数量": 2, "単価": 1980 },
        { "SKU": "GADGET-B", "数量": 1, "単価": 4980 }
      ],
      "合計": { "小計": 8940, "税": 894, "送料": 500, "合計": 10334 },
      "発送日時": "2024-05-10T14:22:00Z",
      "追跡番号": "1234-5678-90AB"
    },
    github: {
      "id": 583231,
      "login": "octocat",
      "name": "The Octocat",
      "public_repos": 8,
      "followers": 14987,
      "following": 9,
      "created_at": "2011-01-25T18:44:36Z",
      "plan": { "name": "pro", "space": 976562499, "private_repos": 9999 },
      "repos": [
        { "name": "Hello-World", "stars": 2341, "language": "Ruby" },
        { "name": "linguist", "stars": 11239, "language": "Ruby" }
      ]
    },
    nested: {
      "レベル1": {
        "レベル2": {
          "レベル3": {
            "レベル4": {
              "レベル5": {
                "値": "深いネストの値",
                "フラグ": [true, false, null, 42]
              }
            }
          }
        },
        "兄弟ノード": [1, 2, { "x": "配列内のオブジェクト" }]
      },
      "メタ": { "バージョン": "1.0", "タグ": ["アルファ", "ベータ"] }
    }
  };

  var state = {
    parsed: null,
    selectedPath: null,
    selectedDot: '',
    selectedBracket: '',
    selectedValue: null,
    searchTerm: '',
    nodeCount: 0,
    keyCount: 0,
    arrayCount: 0,
    maxDepth: 0
  };

  function showToast(msg) {
    var t = el('jpfToast');
    t.textContent = msg;
    t.classList.add('jpf-show');
    setTimeout(function() { t.classList.remove('jpf-show'); }, 1800);
  }

  function copyText(text) {
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).catch(function() { fallbackCopy(text); });
    } else { fallbackCopy(text); }
  }

  function fallbackCopy(text) {
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.opacity = '0';
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    document.body.removeChild(ta);
  }

  function typeOf(val) {
    if (val === null) return 'null';
    if (Array.isArray(val)) return 'array';
    return typeof val;
  }

  function typeBadgeJa(t) {
    var labels = {
      string: '文字列', number: '数値', boolean: '真偽値',
      null: 'NULL', object: 'オブジェクト', array: '配列'
    };
    return '<span class="jpf-type-badge jpf-type-' + t + '">' + (labels[t] || t) + '</span>';
  }

  function dotPath(segments) {
    var out = '$';
    for (var i = 0; i < segments.length; i++) {
      var s = segments[i];
      if (typeof s === 'number') {
        out += '[' + s + ']';
      } else {
        out += /^[a-zA-Z_$][a-zA-Z0-9_$]*$/.test(s) ? '.' + s : '["' + s + '"]';
      }
    }
    return out;
  }

  function bracketPath(segments) {
    var out = '$';
    for (var i = 0; i < segments.length; i++) {
      var s = segments[i];
      if (typeof s === 'number') {
        out += '[' + s + ']';
      } else {
        out += '["' + s + '"]';
      }
    }
    return out;
  }

  function gatherStats(obj, depth) {
    depth = depth || 0;
    if (depth > state.maxDepth) state.maxDepth = depth;
    state.nodeCount++;
    var t = typeOf(obj);
    if (t === 'object' && obj !== null) {
      state.keyCount += Object.keys(obj).length;
      Object.keys(obj).forEach(function(k) { gatherStats(obj[k], depth + 1); });
    } else if (t === 'array') {
      state.arrayCount++;
      obj.forEach(function(v) { gatherStats(v, depth + 1); });
    }
  }

  function buildNode(key, val, segments, isRoot) {
    var t = typeOf(val);
    var isExpandable = t === 'object' || t === 'array';
    var segs = segments.slice();
    if (!isRoot) segs.push(key);

    var node = document.createElement('div');
    node.className = 'jpf-node';

    var row = document.createElement('div');
    row.className = 'jpf-node-row';

    var q = state.searchTerm.toLowerCase();
    if (q) {
      var keyStr = String(key).toLowerCase();
      var valStr2 = (t !== 'object' && t !== 'array') ? String(val).toLowerCase() : '';
      if (keyStr.indexOf(q) !== -1 || valStr2.indexOf(q) !== -1) {
        row.classList.add('jpf-search-match');
      }
    }

    var toggle = document.createElement('span');
    toggle.className = 'jpf-toggle';
    if (isExpandable) {
      toggle.textContent = '▶';
    } else {
      toggle.innerHTML = '&nbsp;';
    }

    var keyEl = document.createElement('span');
    keyEl.className = 'jpf-key';
    if (isRoot) {
      keyEl.textContent = t === 'array' ? 'ルート []' : 'ルート {}';
    } else {
      keyEl.textContent = typeof key === 'number' ? '[' + key + ']' : key;
    }

    var colon = document.createElement('span');
    colon.className = 'jpf-colon';
    colon.textContent = ':';

    var valEl = document.createElement('span');
    valEl.className = 'jpf-val-inline';

    var children;

    if (isExpandable) {
      var count = t === 'array' ? val.length : Object.keys(val).length;
      valEl.className += ' jpf-val-collapsed';
      valEl.textContent = t === 'array' ? '[' + count + ' 件]' : '{' + count + ' キー}';

      children = document.createElement('div');
      children.className = 'jpf-children';

      if (t === 'object') {
        Object.keys(val).forEach(function(k) {
          children.appendChild(buildNode(k, val[k], segs, false));
        });
      } else {
        val.forEach(function(v, i) {
          children.appendChild(buildNode(i, v, segs, false));
        });
      }

      row.appendChild(toggle);
      if (!isRoot) {
        row.appendChild(keyEl);
        row.appendChild(colon);
      } else {
        row.appendChild(keyEl);
      }
      row.appendChild(valEl);

      var expanded = true;
      toggle.style.transform = 'rotate(90deg)';

      toggle.addEventListener('click', function(e) {
        e.stopPropagation();
        expanded = !expanded;
        children.style.display = expanded ? '' : 'none';
        toggle.style.transform = expanded ? 'rotate(90deg)' : 'rotate(0deg)';
      });

      row.addEventListener('click', function() {
        selectNode(row, segs, key, val, t, isRoot);
      });

      node.appendChild(row);
      node.appendChild(children);
    } else {
      valEl.className += ' jpf-val-' + t;
      valEl.textContent = t === 'string' ? '"' + val + '"' : (val === null ? 'null' : String(val));

      row.appendChild(toggle);
      row.appendChild(keyEl);
      row.appendChild(colon);
      row.appendChild(valEl);
      row.appendChild(document.createTextNode(' '));
      var badge = document.createElement('span');
      badge.innerHTML = typeBadgeJa(t);
      row.appendChild(badge);

      row.addEventListener('click', function() {
        selectNode(row, segs, key, val, t, isRoot);
      });

      node.appendChild(row);
    }

    node._expand = function() {
      if (isExpandable && !expanded) {
        expanded = true;
        children.style.display = '';
        toggle.style.transform = 'rotate(90deg)';
      }
      if (isExpandable) {
        Array.from(children.children).forEach(function(c) {
          if (c._expand) c._expand();
        });
      }
    };
    node._collapse = function() {
      if (isExpandable && expanded) {
        expanded = false;
        children.style.display = 'none';
        toggle.style.transform = 'rotate(0deg)';
      }
    };

    return node;
  }

  var lastSelectedRow = null;

  function selectNode(row, segs, key, val, t, isRoot) {
    if (lastSelectedRow) lastSelectedRow.classList.remove('jpf-selected');
    row.classList.add('jpf-selected');
    lastSelectedRow = row;

    var dp = isRoot ? '$' : dotPath(segs);
    var bp = isRoot ? '$' : bracketPath(segs);
    state.selectedDot = dp;
    state.selectedBracket = bp;
    state.selectedValue = val;

    el('jpfDotPath').textContent = dp;
    el('jpfBracketPath').textContent = bp;

    var valStr = t === 'object' || t === 'array' ? JSON.stringify(val, null, 2) : String(val);
    el('jpfValuePreview').innerHTML = '';
    var vt = document.createElement('span');
    vt.className = 'jpf-value-text';
    vt.textContent = valStr.length > 200 ? valStr.slice(0, 200) + '...' : valStr;
    var copyValBtn = document.createElement('button');
    copyValBtn.className = 'jpf-copy-inline';
    copyValBtn.textContent = '値をコピー';
    copyValBtn.addEventListener('click', function() {
      copyText(t === 'object' || t === 'array' ? JSON.stringify(val, null, 2) : String(val));
      showToast('値をコピーしました');
      copyValBtn.classList.add('jpf-copied');
      setTimeout(function() { copyValBtn.classList.remove('jpf-copied'); copyValBtn.textContent = '値をコピー'; }, 1500);
    });
    var badgeEl = document.createElement('span');
    badgeEl.innerHTML = typeBadgeJa(t);
    el('jpfValuePreview').appendChild(vt);
    el('jpfValuePreview').appendChild(badgeEl);
    el('jpfValuePreview').appendChild(copyValBtn);

    el('jpfPathBox').classList.add('jpf-active');
  }

  function parseAndRender() {
    var raw = el('jpfInput').value.trim();
    el('jpfInput').classList.remove('jpf-error');
    el('jpfError').style.display = 'none';
    el('jpfTree').innerHTML = '';
    el('jpfEmpty').style.display = 'none';
    el('jpfStats').style.display = 'none';
    el('jpfPathBox').classList.remove('jpf-active');
    lastSelectedRow = null;

    if (!raw) {
      el('jpfEmpty').style.display = '';
      el('jpfEmpty').textContent = '探索するJSONがありません。上に貼り付けてください。';
      return;
    }

    var parsed;
    try { parsed = JSON.parse(raw); }
    catch(e) {
      el('jpfInput').classList.add('jpf-error');
      el('jpfError').style.display = '';
      el('jpfError').textContent = 'JSON解析エラー: ' + e.message;
      el('jpfEmpty').style.display = '';
      el('jpfEmpty').textContent = '上のエラーを修正するとツリーが表示されます。';
      return;
    }

    state.parsed = parsed;
    state.nodeCount = 0;
    state.keyCount = 0;
    state.arrayCount = 0;
    state.maxDepth = 0;
    gatherStats(parsed, 0);

    el('jpfStatNodes').textContent = state.nodeCount;
    el('jpfStatKeys').textContent = state.keyCount;
    el('jpfStatArrays').textContent = state.arrayCount;
    el('jpfStatDepth').textContent = state.maxDepth;
    el('jpfStats').style.display = '';

    var root = buildNode('root', parsed, [], true);
    el('jpfTree').appendChild(root);
    if (root._expand) root._expand();

    if (state.searchTerm) applySearch();
  }

  function applySearch() {
    var q = state.searchTerm.toLowerCase();
    var rows = el('jpfTree').querySelectorAll('.jpf-node-row');
    var matchCount = 0;
    rows.forEach(function(r) { r.classList.remove('jpf-search-match'); });
    if (!q) { el('jpfStatMatches').style.display = 'none'; return; }
    rows.forEach(function(r) {
      var keyEl = r.querySelector('.jpf-key');
      var valEl = r.querySelector('.jpf-val-inline');
      var keyTxt = keyEl ? keyEl.textContent.toLowerCase() : '';
      var valTxt = valEl ? valEl.textContent.toLowerCase() : '';
      if (keyTxt.indexOf(q) !== -1 || valTxt.indexOf(q) !== -1) {
        r.classList.add('jpf-search-match');
        matchCount++;
      }
    });
    el('jpfStatMatches').textContent = matchCount + ' 件一致';
    el('jpfStatMatches').style.display = '';
  }

  el('jpfParse').addEventListener('click', parseAndRender);
  el('jpfInput').addEventListener('keydown', function(e) {
    if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') parseAndRender();
  });
  el('jpfClear').addEventListener('click', function() {
    el('jpfInput').value = '';
    el('jpfInput').classList.remove('jpf-error');
    el('jpfError').style.display = 'none';
    el('jpfTree').innerHTML = '';
    el('jpfEmpty').style.display = '';
    el('jpfEmpty').textContent = '上にJSONを貼り付けて探索するをクリックしてください。';
    el('jpfStats').style.display = 'none';
    el('jpfPathBox').classList.remove('jpf-active');
    el('jpfSearch').value = '';
    state.searchTerm = '';
    lastSelectedRow = null;
  });

  el('jpfExpandAll').addEventListener('click', function() {
    el('jpfTree').querySelectorAll('.jpf-node').forEach(function(n) {
      if (n._expand) n._expand();
    });
  });
  el('jpfCollapseAll').addEventListener('click', function() {
    Array.from(el('jpfTree').children).forEach(function(r) { if (r._collapse) r._collapse(); });
  });

  el('jpfSearch').addEventListener('input', function() {
    state.searchTerm = this.value.trim();
    applySearch();
  });

  document.querySelectorAll('#jpf-app .jpf-copy-inline[data-target]').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var target = btn.getAttribute('data-target');
      var txt = target === 'dot' ? state.selectedDot : target === 'bracket' ? state.selectedBracket : '';
      if (!txt) return;
      copyText(txt);
      showToast('コピーしました');
      btn.classList.add('jpf-copied');
      var orig = btn.textContent;
      btn.textContent = 'コピー済み';
      setTimeout(function() { btn.classList.remove('jpf-copied'); btn.textContent = orig; }, 1500);
    });
  });

  el('jpfCopyDotAll').addEventListener('click', function() {
    if (!state.selectedDot) { showToast('ノードを選択してください'); return; }
    copyText(state.selectedDot);
    showToast('ドットパスをコピーしました');
  });
  el('jpfCopyBracketAll').addEventListener('click', function() {
    if (!state.selectedBracket) { showToast('ノードを選択してください'); return; }
    copyText(state.selectedBracket);
    showToast('ブラケットパスをコピーしました');
  });
  el('jpfCopyVal').addEventListener('click', function() {
    if (state.selectedValue === null && state.selectedDot === '') { showToast('ノードを選択してください'); return; }
    var v = state.selectedValue;
    var txt = (typeof v === 'object') ? JSON.stringify(v, null, 2) : String(v);
    copyText(txt);
    showToast('値をコピーしました');
  });

  document.querySelectorAll('#jpf-app .jpf-preset-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var key = btn.getAttribute('data-preset');
      if (presets[key]) {
        el('jpfInput').value = JSON.stringify(presets[key], null, 2);
        parseAndRender();
      }
    });
  });
})();
</script>

</div>

## 使い方

1. 上のテキストエリアに **JSONを貼り付け**（またはサンプルプリセットを選択）
2. **探索する** をクリック（Ctrl+Enter / Cmd+Enter でも可）
3. ツリーの **ノードをクリック** してドット記法・ブラケット記法のJSONPathを確認
4. **コピーボタン** でパスや値をクリップボードへ
5. **検索** でキー名・値に一致するノードをハイライト

## JSONPathとは？

JSONPathはJSON向けのクエリ言語で、XPathのJSON版です。複雑なJSON構造の中から特定の値を `$.user.address.city` や `$["items"][0]["price"]` のような式で指定できます。主な用途：

- **REST APIテスト**（Postman・Insomniaのアサーション）
- **AWS Step Functions**（InputPath / OutputPath / ResultPath）
- **Kubernetes** マニフェスト・JSONパッチ
- **ログ解析**（Elasticsearch・Grafana）
- **データ変換**パイプライン

## 記法の比較

| 記法 | 例 | 特徴 |
|---|---|---|
| ドット（シンプル） | `$.user.name` | 読みやすい・英数字キー向け |
| ドット（インデックス） | `$.items[0].price` | 配列インデックスはブラケット |
| ブラケット | `$["user"]["name"]` | 日本語キーも含め常に安全 |
| ブラケット（インデックス） | `$["items"][0]["price"]` | 完全明示的 |

> **ヒント**: 日本語や記号を含むキーはブラケット記法 `$["キー名"]` を使用してください。ドット記法は英数字・アンダースコアのみのキーで有効です。

## 関連ツール

- [JSONフォーマッター](/tools/json-formatter/) — JSONの整形・バリデーション
- [JSONスキーマジェネレーター](/tools/json-schema-generator/) — サンプルJSONからJSON Schemaを自動生成
- [JSON to CSV変換ツール](/tools/json-to-csv/) — JSON配列をスプレッドシート形式に変換

---

## freeeと連携してAPIデータを探索しよう

freee APIのレスポンスJSONを解析する際にも、このツールが役立ちます。freee APIから取得した取引データや勘定科目データのJSONをそのまま貼り付けて、必要なフィールドのパスを即座に特定できます。

**freeeユーザーの方へ**: freee APIを使った自動化・データ連携にお困りですか？[freee公認のAPI連携サービス](https://developer.freee.co.jp/)で、会計データの活用をさらに効率化しましょう。開発者向けのドキュメントとサンドボックス環境が無料で利用可能です。

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

