---
title: "JSON差分比較ツール"
date: 2025-05-16
description: "無料のJSON差分比較ツール。2つのJSONオブジェクトをサイドバイサイドで比較。追加・削除・変更されたプロパティをカラーコードで表示。ネスト対応。"
categories: ["無料ツール"]
slug: "json-diff"
ShowToc: false
cover:
  image: "/images/covers/json-diff-ja.png"
  alt: "JSON差分比較ツール"
---

2つのJSONを貼り付けるだけで、追加・削除・変更されたキーを色分けして一覧表示。ドット記法のパス付き。サーバー送信なし、登録不要。

<div id="jd-app">
<style>
#jd-app *,
#jd-app *::before,
#jd-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#jd-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.6;
}
#jd-app .jd-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 14px;
}
#jd-app .jd-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 7px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  background: #fff;
  color: #334155;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#jd-app .jd-btn:hover { background: #f1f5f9; border-color: #94a3b8; }
#jd-app .jd-btn.primary {
  background: #6366f1;
  color: #fff;
  border-color: #6366f1;
}
#jd-app .jd-btn.primary:hover { background: #4f46e5; border-color: #4f46e5; }
#jd-app .jd-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 12px;
}
@media (max-width: 640px) {
  #jd-app .jd-panels { grid-template-columns: 1fr; }
}
#jd-app .jd-panel-label {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 5px;
}
#jd-app textarea.jd-input {
  width: 100%;
  height: 220px;
  padding: 10px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-family: "SF Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 12.5px;
  line-height: 1.6;
  color: #1e293b;
  background: #f8fafc;
  resize: vertical;
  outline: none;
  transition: border-color 0.15s;
}
#jd-app textarea.jd-input:focus { border-color: #6366f1; background: #fff; }
#jd-app textarea.jd-input.error { border-color: #ef4444; background: #fff5f5; }
#jd-app .jd-parse-error {
  font-size: 12px;
  color: #ef4444;
  margin-top: 4px;
  min-height: 16px;
}
#jd-app .jd-stats {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 14px;
}
#jd-app .jd-stat {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 600;
}
#jd-app .jd-stat.added   { background: #dcfce7; color: #15803d; }
#jd-app .jd-stat.removed { background: #fee2e2; color: #b91c1c; }
#jd-app .jd-stat.changed { background: #fef9c3; color: #92400e; }
#jd-app .jd-stat.same    { background: #f1f5f9; color: #475569; }
#jd-app .jd-stat-dot {
  width: 9px; height: 9px;
  border-radius: 50%;
  flex-shrink: 0;
}
#jd-app .jd-stat.added   .jd-stat-dot { background: #16a34a; }
#jd-app .jd-stat.removed .jd-stat-dot { background: #dc2626; }
#jd-app .jd-stat.changed .jd-stat-dot { background: #d97706; }
#jd-app .jd-stat.same    .jd-stat-dot { background: #94a3b8; }
#jd-app .jd-tree {
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  overflow: hidden;
  background: #fff;
}
#jd-app .jd-row {
  display: flex;
  align-items: baseline;
  border-bottom: 1px solid #f1f5f9;
  font-family: "SF Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 12.5px;
  line-height: 1.7;
}
#jd-app .jd-row:last-child { border-bottom: none; }
#jd-app .jd-row.added   { background: #f0fdf4; }
#jd-app .jd-row.removed { background: #fff5f5; }
#jd-app .jd-row.changed { background: #fefce8; }
#jd-app .jd-row-badge {
  width: 26px;
  flex-shrink: 0;
  text-align: center;
  font-weight: 700;
  font-size: 13px;
  padding: 0 4px;
  align-self: stretch;
  display: flex;
  align-items: center;
  justify-content: center;
}
#jd-app .jd-row.added   .jd-row-badge { color: #16a34a; background: #dcfce7; }
#jd-app .jd-row.removed .jd-row-badge { color: #dc2626; background: #fee2e2; }
#jd-app .jd-row.changed .jd-row-badge { color: #d97706; background: #fef9c3; }
#jd-app .jd-row-body {
  padding: 4px 12px;
  flex: 1;
  overflow-wrap: anywhere;
}
#jd-app .jd-row-path {
  color: #6366f1;
  font-weight: 600;
}
#jd-app .jd-row-sep {
  color: #94a3b8;
  margin: 0 5px;
}
#jd-app .jd-val-old {
  text-decoration: line-through;
  color: #dc2626;
}
#jd-app .jd-val-new { color: #16a34a; }
#jd-app .jd-val-added   { color: #15803d; }
#jd-app .jd-val-removed { color: #b91c1c; }
#jd-app .jd-empty-state {
  text-align: center;
  padding: 40px 20px;
  color: #94a3b8;
  font-size: 14px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
}
#jd-app .jd-identical {
  text-align: center;
  padding: 28px 20px;
  color: #16a34a;
  font-size: 15px;
  font-weight: 600;
  background: #f0fdf4;
  border-radius: 10px;
  border: 1.5px solid #bbf7d0;
}
</style>

<div class="jd-toolbar">
  <button class="jd-btn primary" id="jd-compare">&#8644; 比較する</button>
  <button class="jd-btn" id="jd-swap">&#8645; 入れ替え</button>
  <button class="jd-btn" id="jd-fmt-left">{ } 左を整形</button>
  <button class="jd-btn" id="jd-fmt-right">{ } 右を整形</button>
  <button class="jd-btn" id="jd-sample">サンプル</button>
  <button class="jd-btn" id="jd-clear">クリア</button>
</div>

<div class="jd-panels">
  <div>
    <div class="jd-panel-label">左（変更前）</div>
    <textarea class="jd-input" id="jd-left" placeholder='{"name": "田中太郎", "age": 30}'></textarea>
    <div class="jd-parse-error" id="jd-err-left"></div>
  </div>
  <div>
    <div class="jd-panel-label">右（変更後）</div>
    <textarea class="jd-input" id="jd-right" placeholder='{"name": "田中太郎", "age": 31}'></textarea>
    <div class="jd-parse-error" id="jd-err-right"></div>
  </div>
</div>

<div class="jd-stats" id="jd-stats" style="display:none;"></div>

<div id="jd-result-wrap">
  <div class="jd-empty-state">両方のパネルにJSONを貼り付けて「比較する」をクリックしてください。</div>
</div>

<script>
(function() {
  'use strict';

  function esc(s) {
    return String(s)
      .replace(/&/g,'&amp;')
      .replace(/</g,'&lt;')
      .replace(/>/g,'&gt;')
      .replace(/"/g,'&quot;');
  }

  function formatVal(v) {
    if (v === null) return '<span style="color:#7c3aed">null</span>';
    if (typeof v === 'boolean') return '<span style="color:#0891b2">' + v + '</span>';
    if (typeof v === 'number') return '<span style="color:#0369a1">' + v + '</span>';
    if (typeof v === 'string') return '<span style="color:#b45309">"' + esc(v) + '"</span>';
    if (Array.isArray(v)) return '<span style="color:#64748b">[配列(' + v.length + '件)]</span>';
    return '<span style="color:#64748b">{オブジェクト}</span>';
  }

  function isPrimitive(v) {
    return v === null || typeof v !== 'object';
  }

  function typeOf(v) {
    if (v === null) return 'null';
    if (Array.isArray(v)) return 'array';
    return typeof v;
  }

  function deepDiff(left, right, path, results) {
    results = results || [];
    path = path || '';

    var lt = typeOf(left);
    var rt = typeOf(right);

    if (lt !== rt) {
      results.push({ type: 'changed', path: path || '(root)', oldVal: left, newVal: right });
      return results;
    }

    if (lt === 'object') {
      var allKeys = new Set(Object.keys(left).concat(Object.keys(right)));
      allKeys.forEach(function(key) {
        var childPath = path ? path + '.' + key : key;
        if (!Object.prototype.hasOwnProperty.call(left, key)) {
          collectAll(right[key], childPath, 'added', results);
        } else if (!Object.prototype.hasOwnProperty.call(right, key)) {
          collectAll(left[key], childPath, 'removed', results);
        } else {
          deepDiff(left[key], right[key], childPath, results);
        }
      });
    } else if (lt === 'array') {
      var maxLen = Math.max(left.length, right.length);
      for (var i = 0; i < maxLen; i++) {
        var childPath = (path || '(root)') + '[' + i + ']';
        if (i >= left.length) {
          collectAll(right[i], childPath, 'added', results);
        } else if (i >= right.length) {
          collectAll(left[i], childPath, 'removed', results);
        } else {
          deepDiff(left[i], right[i], childPath, results);
        }
      }
    } else {
      if (left !== right) {
        results.push({ type: 'changed', path: path || '(root)', oldVal: left, newVal: right });
      }
    }

    return results;
  }

  function collectAll(node, path, type, results) {
    if (isPrimitive(node) || typeOf(node) === 'null') {
      results.push({ type: type, path: path, val: node });
      return;
    }
    if (Array.isArray(node)) {
      if (node.length === 0) {
        results.push({ type: type, path: path, val: node });
        return;
      }
      node.forEach(function(item, i) {
        collectAll(item, path + '[' + i + ']', type, results);
      });
    } else {
      var keys = Object.keys(node);
      if (keys.length === 0) {
        results.push({ type: type, path: path, val: node });
        return;
      }
      keys.forEach(function(k) {
        collectAll(node[k], path + '.' + k, type, results);
      });
    }
  }

  function renderDiff(diffs) {
    if (diffs.length === 0) {
      return '<div class="jd-identical">&#10003; 差分なし — 2つのJSONは同一です。</div>';
    }

    var html = '<div class="jd-tree">';

    diffs.forEach(function(d) {
      if (d.type === 'added') {
        html += '<div class="jd-row added">';
        html += '<div class="jd-row-badge">+</div>';
        html += '<div class="jd-row-body">';
        html += '<span class="jd-row-path">' + esc(d.path) + '</span>';
        html += '<span class="jd-row-sep">&#8594;</span>';
        html += '<span class="jd-val-added">' + formatVal(d.val) + '</span>';
        html += '</div></div>';
      } else if (d.type === 'removed') {
        html += '<div class="jd-row removed">';
        html += '<div class="jd-row-badge">&minus;</div>';
        html += '<div class="jd-row-body">';
        html += '<span class="jd-row-path">' + esc(d.path) + '</span>';
        html += '<span class="jd-row-sep">&#8594;</span>';
        html += '<span class="jd-val-removed">' + formatVal(d.val) + '</span>';
        html += '</div></div>';
      } else if (d.type === 'changed') {
        html += '<div class="jd-row changed">';
        html += '<div class="jd-row-badge">~</div>';
        html += '<div class="jd-row-body">';
        html += '<span class="jd-row-path">' + esc(d.path) + '</span>';
        html += '<span class="jd-row-sep">:</span> ';
        html += '<span class="jd-val-old">' + formatVal(d.oldVal) + '</span>';
        html += ' <span class="jd-row-sep">&#8594;</span> ';
        html += '<span class="jd-val-new">' + formatVal(d.newVal) + '</span>';
        html += '</div></div>';
      }
    });

    html += '</div>';
    return html;
  }

  function renderStats(diffs) {
    var added = 0, removed = 0, changed = 0;
    diffs.forEach(function(d) {
      if (d.type === 'added') added++;
      else if (d.type === 'removed') removed++;
      else if (d.type === 'changed') changed++;
    });
    var total = added + removed + changed;
    return (
      '<div class="jd-stat added"><div class="jd-stat-dot"></div>' + added + ' 件追加</div>' +
      '<div class="jd-stat removed"><div class="jd-stat-dot"></div>' + removed + ' 件削除</div>' +
      '<div class="jd-stat changed"><div class="jd-stat-dot"></div>' + changed + ' 件変更</div>' +
      '<div class="jd-stat same"><div class="jd-stat-dot"></div>合計 ' + total + ' 件の差分</div>'
    );
  }

  function tryParse(str, errEl, inputEl) {
    errEl.textContent = '';
    inputEl.classList.remove('error');
    var s = str.trim();
    if (!s) return null;
    try {
      return JSON.parse(s);
    } catch (e) {
      errEl.textContent = 'パースエラー: ' + e.message;
      inputEl.classList.add('error');
      return undefined;
    }
  }

  var leftEl   = document.getElementById('jd-left');
  var rightEl  = document.getElementById('jd-right');
  var errLeft  = document.getElementById('jd-err-left');
  var errRight = document.getElementById('jd-err-right');
  var statsEl  = document.getElementById('jd-stats');
  var resultEl = document.getElementById('jd-result-wrap');

  function runCompare() {
    var leftParsed  = tryParse(leftEl.value,  errLeft,  leftEl);
    var rightParsed = tryParse(rightEl.value, errRight, rightEl);

    if (leftParsed === undefined || rightParsed === undefined) {
      statsEl.style.display = 'none';
      resultEl.innerHTML = '<div class="jd-empty-state">上のパースエラーを修正してから比較してください。</div>';
      return;
    }
    if (leftParsed === null && rightParsed === null && !leftEl.value.trim() && !rightEl.value.trim()) {
      statsEl.style.display = 'none';
      resultEl.innerHTML = '<div class="jd-empty-state">両方のパネルにJSONを貼り付けて「比較する」をクリックしてください。</div>';
      return;
    }

    var diffs = deepDiff(leftParsed, rightParsed);
    statsEl.style.display = 'flex';
    statsEl.innerHTML = renderStats(diffs);
    resultEl.innerHTML = renderDiff(diffs);
  }

  function formatInput(el, errEl) {
    var parsed = tryParse(el.value, errEl, el);
    if (parsed === undefined) return;
    if (parsed === null && !el.value.trim()) return;
    el.value = JSON.stringify(parsed, null, 2);
    errEl.textContent = '';
    el.classList.remove('error');
  }

  var sampleLeft = {
    "ユーザー": {
      "id": 1,
      "名前": "田中太郎",
      "メール": "tanaka@example.com",
      "役割": "管理者",
      "有効": true,
      "スコア": 95
    },
    "設定": {
      "テーマ": "ダーク",
      "通知": true,
      "言語": "ja"
    },
    "タグ": ["開発者", "テスター"]
  };

  var sampleRight = {
    "ユーザー": {
      "id": 1,
      "名前": "田中太郎",
      "メール": "tanaka@newdomain.com",
      "役割": "編集者",
      "有効": false,
      "スコア": 98,
      "部署": "エンジニアリング"
    },
    "設定": {
      "テーマ": "ライト",
      "通知": true,
      "言語": "ja",
      "タイムゾーン": "Asia/Tokyo"
    },
    "タグ": ["開発者", "レビュアー", "リード"]
  };

  document.getElementById('jd-compare').addEventListener('click', runCompare);

  document.getElementById('jd-swap').addEventListener('click', function() {
    var tmp = leftEl.value;
    leftEl.value = rightEl.value;
    rightEl.value = tmp;
    errLeft.textContent = '';
    errRight.textContent = '';
    leftEl.classList.remove('error');
    rightEl.classList.remove('error');
  });

  document.getElementById('jd-fmt-left').addEventListener('click', function() {
    formatInput(leftEl, errLeft);
  });

  document.getElementById('jd-fmt-right').addEventListener('click', function() {
    formatInput(rightEl, errRight);
  });

  document.getElementById('jd-sample').addEventListener('click', function() {
    leftEl.value  = JSON.stringify(sampleLeft,  null, 2);
    rightEl.value = JSON.stringify(sampleRight, null, 2);
    errLeft.textContent  = '';
    errRight.textContent = '';
    leftEl.classList.remove('error');
    rightEl.classList.remove('error');
    runCompare();
  });

  document.getElementById('jd-clear').addEventListener('click', function() {
    leftEl.value  = '';
    rightEl.value = '';
    errLeft.textContent  = '';
    errRight.textContent = '';
    leftEl.classList.remove('error');
    rightEl.classList.remove('error');
    statsEl.style.display = 'none';
    resultEl.innerHTML = '<div class="jd-empty-state">両方のパネルにJSONを貼り付けて「比較する」をクリックしてください。</div>';
  });

  var debTimer;
  function maybeAutoCompare() {
    clearTimeout(debTimer);
    debTimer = setTimeout(function() {
      if (leftEl.value.trim() && rightEl.value.trim()) {
        runCompare();
      }
    }, 700);
  }
  leftEl.addEventListener('input',  maybeAutoCompare);
  rightEl.addEventListener('input', maybeAutoCompare);

  document.addEventListener('keydown', function(e) {
    if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') {
      e.preventDefault();
      runCompare();
    }
  });
})();
</script>
</div>

---

<div class="jd-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">API・開発ツールの経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、クラウドサービス・開発ツールの経費精算もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

## 使い方

1. **左パネル**に変更前のJSONを貼り付けます
2. **右パネル**に変更後のJSONを貼り付けます
3. 「**比較する**」ボタンをクリック（両方入力後700ms後に自動比較）
4. 色分けされた差分一覧を確認します

| 色 | 記号 | 意味 |
|---|---|---|
| 緑 | + | 右にのみ存在するキー（追加） |
| 赤 | − | 左にのみ存在するキー（削除） |
| 黄 | ~ | 両方に存在するが値が変化したキー |

---

## 主な機能

- **再帰的な深い比較** — ネストしたオブジェクトや配列も完全にトレース
- **ドット記法パス** — `user.email`、`tags[2]` のように変更箇所の正確な位置を表示
- **サマリー統計** — 追加・削除・変更の件数を一目で確認
- **整形ボタン** — ミニファイされたJSONを比較前に整形
- **入れ替えボタン** — 変更前・変更後を一発で反転
- **サンプルJSON** — 実際のユーザーオブジェクト差分をすぐ体験
- **キーボードショートカット** — `Ctrl+Enter`（Mac: `Cmd+Enter`）で素早く比較

---

## こんな場面で活躍

- APIレスポンスの変化確認（本番 vs ステージング）
- 設定ファイルの環境差異チェック（dev / prod）
- フロントエンドとバックエンドのデータ形式の照合
- JSONスキーマ移行前後の差分確認
- デバッグ時の状態オブジェクト比較

---

> JSONをバリデーション・整形 → [JSONフォーマッター](/ja/tools/json-formatter/)

> テキストを行単位で比較 → [テキスト差分比較ツール](/ja/tools/text-diff-checker/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
