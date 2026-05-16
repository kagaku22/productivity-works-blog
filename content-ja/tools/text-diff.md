---
title: "テキスト比較ツール - 無料オンラインテキスト差分チェック"
date: 2025-05-16
description: "2つのテキストを比較して差分を即座に検出。行単位・単語単位のハイライト表示。無料のオンラインテキスト比較ツール。"
categories: ["無料ツール"]
tags: ["テキスト比較", "差分チェック", "diff", "比較ツール", "開発ツール"]
slug: "text-diff"
aliases: ["/ja/tools/diff-checker/", "/ja/tools/text-diff-checker/"]
cover:
  image: "/images/covers/text-diff-ja.png"
  alt: "テキスト比較ツール"
ShowToc: false
---

<div id="diff-app">

<style>
#diff-app {
  font-family: 'Segoe UI', 'Hiragino Sans', 'Meiryo', sans-serif;
  color: #334155;
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 8px;
  box-sizing: border-box;
}

#diff-app * {
  box-sizing: border-box;
}

.diff-header {
  text-align: center;
  margin-bottom: 24px;
}

.diff-header h2 {
  font-size: 1.4rem;
  color: #334155;
  margin: 0 0 6px;
}

.diff-header p {
  color: #64748b;
  font-size: 0.9rem;
  margin: 0;
}

.diff-options {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  margin-bottom: 16px;
  padding: 12px 16px;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
}

.diff-options label {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 0.875rem;
  color: #334155;
  cursor: pointer;
  user-select: none;
}

.diff-options input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #334155;
  cursor: pointer;
}

.diff-options-sep {
  flex: 1;
}

.diff-input-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}

@media (max-width: 640px) {
  .diff-input-row {
    grid-template-columns: 1fr;
  }
}

.diff-input-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.diff-input-group label {
  font-size: 0.875rem;
  font-weight: 600;
  color: #334155;
}

.diff-input-group textarea {
  width: 100%;
  height: 220px;
  padding: 10px 12px;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  font-family: 'Consolas', 'Courier New', monospace;
  font-size: 0.85rem;
  color: #334155;
  background: #fff;
  resize: vertical;
  outline: none;
  transition: border-color 0.15s;
  line-height: 1.6;
}

.diff-input-group textarea:focus {
  border-color: #334155;
}

.diff-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  margin-bottom: 20px;
}

.btn {
  padding: 9px 20px;
  border: none;
  border-radius: 7px;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, opacity 0.15s;
  white-space: nowrap;
}

.btn:active {
  opacity: 0.8;
}

.btn-primary {
  background: #334155;
  color: #fff;
  font-size: 1rem;
  padding: 11px 32px;
}

.btn-primary:hover {
  background: #1e293b;
}

.btn-secondary {
  background: #e2e8f0;
  color: #334155;
}

.btn-secondary:hover {
  background: #cbd5e1;
}

.btn-swap {
  background: #f1f5f9;
  color: #334155;
  border: 1px solid #cbd5e1;
}

.btn-swap:hover {
  background: #e2e8f0;
}

.btn-copy {
  background: #f0fdf4;
  color: #166534;
  border: 1px solid #bbf7d0;
}

.btn-copy:hover {
  background: #dcfce7;
}

.diff-stats {
  display: none;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  justify-content: center;
  margin-bottom: 16px;
  padding: 12px 16px;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
}

.diff-stats.visible {
  display: flex;
}

.stat-badge {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 0.82rem;
  font-weight: 600;
}

.stat-added {
  background: #dcfce7;
  color: #166534;
}

.stat-removed {
  background: #fee2e2;
  color: #991b1b;
}

.stat-unchanged {
  background: #f1f5f9;
  color: #475569;
}

.stat-similarity {
  background: #eff6ff;
  color: #1d4ed8;
}

.diff-output {
  display: none;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 16px;
}

.diff-output.visible {
  display: block;
}

.diff-output-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 16px;
  background: #f8fafc;
  border-bottom: 1px solid #e2e8f0;
  font-size: 0.82rem;
  font-weight: 600;
  color: #64748b;
}

.diff-output-legend {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 0.78rem;
}

.legend-dot {
  width: 12px;
  height: 12px;
  border-radius: 3px;
  flex-shrink: 0;
}

.legend-added { background: #bbf7d0; }
.legend-removed { background: #fecaca; }
.legend-unchanged { background: #f1f5f9; border: 1px solid #e2e8f0; }

.diff-lines {
  font-family: 'Consolas', 'Courier New', monospace;
  font-size: 0.82rem;
  overflow-x: auto;
  max-height: 500px;
  overflow-y: auto;
}

.diff-line {
  display: flex;
  align-items: stretch;
  min-height: 24px;
  line-height: 1.6;
}

.diff-line:hover {
  filter: brightness(0.97);
}

.diff-line-num {
  display: flex;
  align-items: flex-start;
  padding: 2px 8px;
  min-width: 40px;
  text-align: right;
  color: #94a3b8;
  background: #f8fafc;
  border-right: 1px solid #e2e8f0;
  user-select: none;
  font-size: 0.78rem;
  flex-shrink: 0;
  padding-top: 4px;
}

.diff-line-sign {
  display: flex;
  align-items: flex-start;
  padding: 2px 8px 2px 6px;
  min-width: 28px;
  font-weight: 700;
  flex-shrink: 0;
  padding-top: 4px;
}

.diff-line-content {
  flex: 1;
  padding: 2px 12px 2px 4px;
  white-space: pre-wrap;
  word-break: break-all;
  padding-top: 4px;
}

.line-added {
  background: #f0fdf4;
}

.line-added .diff-line-num {
  background: #dcfce7;
  color: #166534;
}

.line-added .diff-line-sign {
  background: #dcfce7;
  color: #166534;
}

.line-removed {
  background: #fff5f5;
}

.line-removed .diff-line-num {
  background: #fee2e2;
  color: #991b1b;
}

.line-removed .diff-line-sign {
  background: #fee2e2;
  color: #991b1b;
}

.line-unchanged {
  background: #fff;
}

.line-unchanged .diff-line-num {
  background: #f8fafc;
  color: #94a3b8;
}

.line-unchanged .diff-line-sign {
  background: #f8fafc;
  color: #cbd5e1;
}

/* Word-level diff highlights */
.word-added {
  background: #86efac;
  border-radius: 2px;
  padding: 0 1px;
}

.word-removed {
  background: #fca5a5;
  border-radius: 2px;
  padding: 0 1px;
  text-decoration: line-through;
}

.diff-empty {
  text-align: center;
  padding: 40px 20px;
  color: #94a3b8;
  font-size: 0.9rem;
  background: #f8fafc;
}

.copy-success {
  display: none;
  text-align: center;
  color: #166534;
  font-size: 0.82rem;
  margin-top: -12px;
  margin-bottom: 12px;
  font-weight: 600;
}

.copy-success.visible {
  display: block;
}
</style>

<div class="diff-header">
  <h2>テキスト比較ツール</h2>
  <p>2つのテキストの差分を即座に検出・ハイライト表示します</p>
</div>

<div class="diff-options">
  <label>
    <input type="checkbox" id="opt-ignore-space">
    空白を無視
  </label>
  <label>
    <input type="checkbox" id="opt-ignore-case">
    大文字小文字を無視
  </label>
  <label>
    <input type="checkbox" id="opt-word-diff">
    単語レベル差分
  </label>
</div>

<div class="diff-input-row">
  <div class="diff-input-group">
    <label for="text-original">元のテキスト</label>
    <textarea id="text-original" placeholder="比較元のテキストをここに貼り付けてください..."></textarea>
  </div>
  <div class="diff-input-group">
    <label for="text-modified">変更後のテキスト</label>
    <textarea id="text-modified" placeholder="比較先のテキストをここに貼り付けてください..."></textarea>
  </div>
</div>

<div class="diff-actions">
  <button class="btn btn-swap" id="btn-swap" title="テキストを入れ替える">⇄ 入れ替え</button>
  <button class="btn btn-primary" id="btn-compare">比較する</button>
  <button class="btn btn-secondary" id="btn-clear">クリア</button>
  <button class="btn btn-copy" id="btn-copy">差分をコピー</button>
</div>

<div class="copy-success" id="copy-success">クリップボードにコピーしました</div>

<div class="diff-stats" id="diff-stats">
  <div class="stat-badge stat-added" id="stat-added">追加: 0行</div>
  <div class="stat-badge stat-removed" id="stat-removed">削除: 0行</div>
  <div class="stat-badge stat-unchanged" id="stat-unchanged">変更なし: 0行</div>
  <div class="stat-badge stat-similarity" id="stat-similarity">類似度: 0%</div>
</div>

<div class="diff-output" id="diff-output">
  <div class="diff-output-header">
    <span>差分結果</span>
    <div class="diff-output-legend">
      <div class="legend-item"><div class="legend-dot legend-added"></div>追加</div>
      <div class="legend-item"><div class="legend-dot legend-removed"></div>削除</div>
      <div class="legend-item"><div class="legend-dot legend-unchanged"></div>変更なし</div>
    </div>
  </div>
  <div class="diff-lines" id="diff-lines"></div>
</div>

<script>
(function() {
  var optIgnoreSpace = document.getElementById('opt-ignore-space');
  var optIgnoreCase  = document.getElementById('opt-ignore-case');
  var optWordDiff    = document.getElementById('opt-word-diff');
  var textOriginal   = document.getElementById('text-original');
  var textModified   = document.getElementById('text-modified');
  var btnCompare     = document.getElementById('btn-compare');
  var btnClear       = document.getElementById('btn-clear');
  var btnSwap        = document.getElementById('btn-swap');
  var btnCopy        = document.getElementById('btn-copy');
  var copySuccess    = document.getElementById('copy-success');
  var diffStats      = document.getElementById('diff-stats');
  var diffOutput     = document.getElementById('diff-output');
  var diffLines      = document.getElementById('diff-lines');
  var statAdded      = document.getElementById('stat-added');
  var statRemoved    = document.getElementById('stat-removed');
  var statUnchanged  = document.getElementById('stat-unchanged');
  var statSimilarity = document.getElementById('stat-similarity');

  // LCS-based diff algorithm
  function computeLCS(a, b) {
    var m = a.length, n = b.length;
    // For large inputs, use linear comparison to avoid memory issues
    if (m * n > 200000) {
      return computeSimpleDiff(a, b);
    }
    var dp = [];
    for (var i = 0; i <= m; i++) {
      dp[i] = new Array(n + 1).fill(0);
    }
    for (var i = 1; i <= m; i++) {
      for (var j = 1; j <= n; j++) {
        if (a[i-1] === b[j-1]) {
          dp[i][j] = dp[i-1][j-1] + 1;
        } else {
          dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
        }
      }
    }
    // Backtrack
    var result = [];
    var i = m, j = n;
    while (i > 0 || j > 0) {
      if (i > 0 && j > 0 && a[i-1] === b[j-1]) {
        result.push({ type: 'equal', val: a[i-1], origIdx: i-1, modIdx: j-1 });
        i--; j--;
      } else if (j > 0 && (i === 0 || dp[i][j-1] >= dp[i-1][j])) {
        result.push({ type: 'added', val: b[j-1], origIdx: null, modIdx: j-1 });
        j--;
      } else {
        result.push({ type: 'removed', val: a[i-1], origIdx: i-1, modIdx: null });
        i--;
      }
    }
    return result.reverse();
  }

  function computeSimpleDiff(a, b) {
    // Fallback for very large inputs: line-by-line sequential comparison
    var result = [];
    var maxLen = Math.max(a.length, b.length);
    for (var i = 0; i < maxLen; i++) {
      if (i < a.length && i < b.length) {
        if (a[i] === b[i]) {
          result.push({ type: 'equal', val: a[i], origIdx: i, modIdx: i });
        } else {
          result.push({ type: 'removed', val: a[i], origIdx: i, modIdx: null });
          result.push({ type: 'added', val: b[i], origIdx: null, modIdx: i });
        }
      } else if (i < a.length) {
        result.push({ type: 'removed', val: a[i], origIdx: i, modIdx: null });
      } else {
        result.push({ type: 'added', val: b[i], origIdx: null, modIdx: i });
      }
    }
    return result;
  }

  // Word-level diff for changed lines
  function wordDiff(origLine, modLine) {
    var origWords = origLine.split(/(\s+)/);
    var modWords  = modLine.split(/(\s+)/);
    var diff = computeLCS(origWords, modWords);

    var origHtml = '';
    var modHtml  = '';
    diff.forEach(function(d) {
      var escaped = escHtml(d.val);
      if (d.type === 'equal') {
        origHtml += escaped;
        modHtml  += escaped;
      } else if (d.type === 'removed') {
        origHtml += '<span class="word-removed">' + escaped + '</span>';
      } else {
        modHtml += '<span class="word-added">' + escaped + '</span>';
      }
    });
    return { orig: origHtml, mod: modHtml };
  }

  function escHtml(s) {
    return s
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  function normalizeLines(text) {
    var lines = text.split('\n');
    var ignoreSpace = optIgnoreSpace.checked;
    var ignoreCase  = optIgnoreCase.checked;
    return lines.map(function(l) {
      if (ignoreSpace) l = l.replace(/\s+/g, ' ').trim();
      if (ignoreCase)  l = l.toLowerCase();
      return l;
    });
  }

  function runDiff() {
    var origRaw  = textOriginal.value;
    var modRaw   = textModified.value;
    var origLines = origRaw.split('\n');
    var modLines  = modRaw.split('\n');
    var origNorm  = normalizeLines(origRaw);
    var modNorm   = normalizeLines(modRaw);
    var useWordDiff = optWordDiff.checked;

    var diffResult = computeLCS(origNorm, modNorm);

    // Map norm indices back to original text
    var origIdxMap = {};
    var modIdxMap  = {};
    origNorm.forEach(function(v, i) { origIdxMap[i] = i; });
    modNorm.forEach(function(v, i) { modIdxMap[i] = i; });

    var addedCount   = 0;
    var removedCount = 0;
    var unchangedCount = 0;
    var html = '';
    var lineNum = 1;
    var modLineNum = 1;

    // Build pairs for word-level diff: consecutive removed+added
    var pairs = [];
    var i = 0;
    while (i < diffResult.length) {
      var d = diffResult[i];
      if (d.type === 'removed' && i + 1 < diffResult.length && diffResult[i+1].type === 'added') {
        pairs.push({ type: 'changed', removed: d, added: diffResult[i+1] });
        i += 2;
      } else {
        pairs.push(d);
        i++;
      }
    }

    pairs.forEach(function(item) {
      if (item.type === 'changed' && useWordDiff) {
        var origIdx = item.removed.origIdx;
        var modIdx  = item.added.modIdx;
        var origText = origIdx !== null ? origLines[origIdx] : '';
        var modText  = modIdx  !== null ? modLines[modIdx]   : '';
        var wd = wordDiff(origText, modText);

        removedCount++;
        html += '<div class="diff-line line-removed">';
        html += '<div class="diff-line-num">' + lineNum + '</div>';
        html += '<div class="diff-line-sign">-</div>';
        html += '<div class="diff-line-content">' + wd.orig + '</div>';
        html += '</div>';
        lineNum++;

        addedCount++;
        html += '<div class="diff-line line-added">';
        html += '<div class="diff-line-num">' + modLineNum + '</div>';
        html += '<div class="diff-line-sign">+</div>';
        html += '<div class="diff-line-content">' + wd.mod + '</div>';
        html += '</div>';
        modLineNum++;

      } else if (item.type === 'changed') {
        var origIdx = item.removed.origIdx;
        var modIdx  = item.added.modIdx;
        var origText = origIdx !== null ? origLines[origIdx] : '';
        var modText  = modIdx  !== null ? modLines[modIdx]   : '';

        removedCount++;
        html += '<div class="diff-line line-removed">';
        html += '<div class="diff-line-num">' + lineNum + '</div>';
        html += '<div class="diff-line-sign">-</div>';
        html += '<div class="diff-line-content">' + escHtml(origText) + '</div>';
        html += '</div>';
        lineNum++;

        addedCount++;
        html += '<div class="diff-line line-added">';
        html += '<div class="diff-line-num">' + modLineNum + '</div>';
        html += '<div class="diff-line-sign">+</div>';
        html += '<div class="diff-line-content">' + escHtml(modText) + '</div>';
        html += '</div>';
        modLineNum++;

      } else if (item.type === 'equal') {
        var origIdx = item.origIdx;
        var displayLine = origIdx !== null ? origLines[origIdx] : item.val;
        unchangedCount++;
        html += '<div class="diff-line line-unchanged">';
        html += '<div class="diff-line-num">' + lineNum + '</div>';
        html += '<div class="diff-line-sign"> </div>';
        html += '<div class="diff-line-content">' + escHtml(displayLine) + '</div>';
        html += '</div>';
        lineNum++;
        modLineNum++;

      } else if (item.type === 'removed') {
        var origIdx = item.origIdx;
        var displayLine = origIdx !== null ? origLines[origIdx] : item.val;
        removedCount++;
        html += '<div class="diff-line line-removed">';
        html += '<div class="diff-line-num">' + lineNum + '</div>';
        html += '<div class="diff-line-sign">-</div>';
        html += '<div class="diff-line-content">' + escHtml(displayLine) + '</div>';
        html += '</div>';
        lineNum++;

      } else if (item.type === 'added') {
        var modIdx = item.modIdx;
        var displayLine = modIdx !== null ? modLines[modIdx] : item.val;
        addedCount++;
        html += '<div class="diff-line line-added">';
        html += '<div class="diff-line-num">' + modLineNum + '</div>';
        html += '<div class="diff-line-sign">+</div>';
        html += '<div class="diff-line-content">' + escHtml(displayLine) + '</div>';
        html += '</div>';
        modLineNum++;
      }
    });

    if (html === '') {
      html = '<div class="diff-empty">差分がありません — 2つのテキストは同一です</div>';
    }

    diffLines.innerHTML = html;

    // Stats
    var totalLines = addedCount + removedCount + unchangedCount;
    var similarity = totalLines === 0 ? 100 :
      Math.round((unchangedCount / Math.max(origLines.length, modLines.length)) * 100);

    statAdded.textContent     = '追加: ' + addedCount + '行';
    statRemoved.textContent   = '削除: ' + removedCount + '行';
    statUnchanged.textContent = '変更なし: ' + unchangedCount + '行';
    statSimilarity.textContent = '類似度: ' + similarity + '%';

    diffStats.classList.add('visible');
    diffOutput.classList.add('visible');
    copySuccess.classList.remove('visible');
  }

  btnCompare.addEventListener('click', runDiff);

  btnClear.addEventListener('click', function() {
    textOriginal.value = '';
    textModified.value = '';
    diffLines.innerHTML = '';
    diffStats.classList.remove('visible');
    diffOutput.classList.remove('visible');
    copySuccess.classList.remove('visible');
  });

  btnSwap.addEventListener('click', function() {
    var tmp = textOriginal.value;
    textOriginal.value = textModified.value;
    textModified.value = tmp;
  });

  btnCopy.addEventListener('click', function() {
    var lines = diffLines.querySelectorAll('.diff-line');
    if (lines.length === 0) return;
    var text = '';
    lines.forEach(function(line) {
      var sign    = line.querySelector('.diff-line-sign');
      var content = line.querySelector('.diff-line-content');
      var num     = line.querySelector('.diff-line-num');
      text += (num ? num.textContent.trim().padStart(4) : '   ') + ' ';
      text += (sign ? sign.textContent : ' ') + ' ';
      text += (content ? content.textContent : '') + '\n';
    });
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() {
        copySuccess.classList.add('visible');
        setTimeout(function() { copySuccess.classList.remove('visible'); }, 2000);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      try { document.execCommand('copy'); } catch(e) {}
      document.body.removeChild(ta);
      copySuccess.classList.add('visible');
      setTimeout(function() { copySuccess.classList.remove('visible'); }, 2000);
    }
  });

  // Allow Ctrl+Enter to compare
  [textOriginal, textModified].forEach(function(ta) {
    ta.addEventListener('keydown', function(e) {
      if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') {
        runDiff();
      }
    });
  });
})();
</script>

</div>

## テキスト比較ツールの使い方

1. **元のテキストを貼り付ける** — 左側のテキストエリアに比較元のテキストを入力または貼り付けます。
2. **変更後のテキストを貼り付ける** — 右側に比較先のテキストを入力します。
3. **オプションを設定する** — 必要に応じて「空白を無視」「大文字小文字を無視」「単語レベル差分」を選択します。
4. **「比較する」ボタンを押す** — 差分が緑（追加）・赤（削除）でハイライト表示されます。
5. **統計を確認する** — 追加・削除・変更なし行数と類似度（%）が表示されます。
6. **差分をコピーする** — 「差分をコピー」ボタンで結果をクリップボードに保存できます。

> **ヒント:** Ctrl + Enter（Mac: ⌘ + Enter）のショートカットでも比較を実行できます。

## 関連ツール

> JSONデータを整形・検証 → [JSONフォーマッター](/ja/tools/json-formatter/)

> 正規表現をテスト → [正規表現テスター](/ja/tools/regex-tester/)

> 文字数をリアルタイムでカウント → [文字数カウンター](/ja/tools/moji-counter/)

> マークダウンエディターが必要？ → [マークダウンプレビュー](/ja/tools/markdown-preview/) — リアルタイムでプレビュー

---

**契約書・文書管理を効率化**

テキストの差分チェックと同様に、ビジネス文書の管理も効率化しませんか？クラウド会計ソフト「freee」なら、請求書の作成から経費管理まで一元化できます。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
