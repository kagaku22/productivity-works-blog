---
title: "正規表現テスター - 無料オンラインRegexツール"
date: 2025-05-16
description: "正規表現をリアルタイムでテスト・デバッグ。マッチハイライト、グループ表示、よく使うパターン集付き。開発者向け無料オンラインツール。"
categories: ["無料ツール"]
tags: ["正規表現", "Regex", "テスター", "開発ツール", "パターンマッチング"]
slug: "regex-tester"
aliases: ["/ja/tools/regexp-tester/", "/ja/tools/regular-expression/"]
cover:
  image: "/images/covers/regex-tester-ja.png"
  alt: "正規表現テスター"
ShowToc: false
---

<div id="regex-app">

<style>
#regex-app {
  font-family: 'Segoe UI', 'Hiragino Sans', 'Meiryo', sans-serif;
  background: #1a1a2e;
  color: #e0e0e0;
  border-radius: 12px;
  padding: 24px;
  max-width: 900px;
  margin: 0 auto;
  box-sizing: border-box;
}
#regex-app * { box-sizing: border-box; }

#regex-app h2 {
  color: #00ff88;
  font-size: 1.1rem;
  margin: 0 0 8px 0;
  letter-spacing: 0.04em;
}

#regex-app .ra-section {
  background: #16213e;
  border: 1px solid #0f3460;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 16px;
}

#regex-app .ra-row {
  display: flex;
  gap: 10px;
  align-items: center;
  flex-wrap: wrap;
}

#regex-app input[type="text"],
#regex-app textarea,
#regex-app select {
  background: #0d0d1a;
  border: 1px solid #0f3460;
  border-radius: 6px;
  color: #e0e0e0;
  font-size: 0.95rem;
  padding: 8px 12px;
  outline: none;
  transition: border-color 0.2s;
  font-family: 'Courier New', 'Consolas', monospace;
}
#regex-app input[type="text"]:focus,
#regex-app textarea:focus,
#regex-app select:focus {
  border-color: #00ff88;
}

#regex-app #ra-pattern {
  flex: 1;
  min-width: 200px;
}

#regex-app .ra-flags {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: center;
}
#regex-app .ra-flag-item {
  display: flex;
  align-items: center;
  gap: 4px;
  font-size: 0.88rem;
  color: #aaa;
  cursor: pointer;
  user-select: none;
}
#regex-app .ra-flag-item input[type="checkbox"] {
  accent-color: #00ff88;
  width: 15px;
  height: 15px;
  cursor: pointer;
}
#regex-app .ra-flag-item:hover { color: #00ff88; }

#regex-app textarea {
  width: 100%;
  resize: vertical;
  min-height: 120px;
  line-height: 1.6;
}

#regex-app .ra-error {
  color: #ff4d6d;
  font-size: 0.85rem;
  margin-top: 6px;
  min-height: 18px;
  font-family: monospace;
}

#regex-app .ra-match-count {
  font-size: 0.88rem;
  color: #00ff88;
  font-weight: bold;
  margin-top: 6px;
  min-height: 18px;
}

/* highlight inside textarea emulation: use a div overlay */
#regex-app .ra-highlight-wrapper {
  position: relative;
  width: 100%;
}
#regex-app #ra-highlight-display {
  position: absolute;
  top: 0; left: 0;
  width: 100%;
  min-height: 120px;
  padding: 8px 12px;
  font-size: 0.95rem;
  font-family: 'Courier New', 'Consolas', monospace;
  line-height: 1.6;
  color: transparent;
  pointer-events: none;
  white-space: pre-wrap;
  word-break: break-all;
  border: 1px solid transparent;
  border-radius: 6px;
  overflow: hidden;
}
#regex-app #ra-highlight-display mark {
  background: rgba(0,255,136,0.35);
  color: transparent;
  border-radius: 2px;
}
#regex-app #ra-test-input {
  background: transparent;
  color: #e0e0e0;
  caret-color: #00ff88;
  position: relative;
  z-index: 1;
}

/* Match result panel */
#regex-app #ra-results {
  max-height: 260px;
  overflow-y: auto;
  margin-top: 10px;
}
#regex-app .ra-match-item {
  background: #0d0d1a;
  border: 1px solid #0f3460;
  border-left: 3px solid #00ff88;
  border-radius: 5px;
  padding: 8px 12px;
  margin-bottom: 8px;
  font-size: 0.88rem;
}
#regex-app .ra-match-header {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  color: #aaa;
  margin-bottom: 4px;
}
#regex-app .ra-match-header span { color: #00ff88; }
#regex-app .ra-match-val {
  font-family: 'Courier New', monospace;
  color: #fff;
  word-break: break-all;
  background: #1a1a2e;
  border-radius: 3px;
  padding: 2px 6px;
  display: inline-block;
}
#regex-app .ra-group-list {
  margin-top: 6px;
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}
#regex-app .ra-group-badge {
  background: #16213e;
  border: 1px solid #00ff88;
  border-radius: 4px;
  padding: 2px 8px;
  font-size: 0.82rem;
  color: #00ff88;
  font-family: monospace;
}

/* Replace mode */
#regex-app .ra-replace-row {
  display: flex;
  gap: 10px;
  align-items: center;
  flex-wrap: wrap;
  margin-top: 10px;
}
#regex-app #ra-replace-pattern {
  flex: 1;
  min-width: 180px;
}
#regex-app #ra-replace-output {
  background: #0d0d1a;
  border: 1px solid #0f3460;
  border-radius: 6px;
  color: #e0e0e0;
  font-size: 0.95rem;
  padding: 8px 12px;
  width: 100%;
  min-height: 80px;
  font-family: 'Courier New', monospace;
  white-space: pre-wrap;
  word-break: break-all;
  margin-top: 10px;
}

/* Patterns dropdown */
#regex-app select {
  min-width: 200px;
  cursor: pointer;
}

/* Cheatsheet */
#regex-app .ra-cheatsheet {
  margin-top: 0;
}
#regex-app .ra-cs-toggle {
  background: none;
  border: 1px solid #0f3460;
  border-radius: 6px;
  color: #00ff88;
  padding: 6px 14px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: background 0.2s;
}
#regex-app .ra-cs-toggle:hover { background: #0f3460; }
#regex-app #ra-cs-body {
  display: none;
  margin-top: 12px;
  overflow-x: auto;
}
#regex-app #ra-cs-body.open { display: block; }
#regex-app .ra-cs-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.85rem;
}
#regex-app .ra-cs-table th {
  background: #0f3460;
  color: #00ff88;
  padding: 6px 10px;
  text-align: left;
  font-weight: 600;
}
#regex-app .ra-cs-table td {
  padding: 5px 10px;
  border-bottom: 1px solid #0f3460;
  vertical-align: top;
}
#regex-app .ra-cs-table tr:hover td { background: #16213e; }
#regex-app .ra-cs-table code {
  color: #00ff88;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
}

/* Buttons */
#regex-app .ra-btn {
  background: #00ff88;
  color: #1a1a2e;
  border: none;
  border-radius: 6px;
  padding: 7px 16px;
  font-size: 0.88rem;
  font-weight: bold;
  cursor: pointer;
  transition: opacity 0.2s;
  white-space: nowrap;
}
#regex-app .ra-btn:hover { opacity: 0.85; }
#regex-app .ra-btn-ghost {
  background: none;
  border: 1px solid #00ff88;
  color: #00ff88;
  border-radius: 6px;
  padding: 7px 16px;
  font-size: 0.88rem;
  cursor: pointer;
  transition: background 0.2s;
  white-space: nowrap;
}
#regex-app .ra-btn-ghost:hover { background: #00ff8822; }

/* Mode tabs */
#regex-app .ra-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 12px;
}
#regex-app .ra-tab {
  background: #0d0d1a;
  border: 1px solid #0f3460;
  border-radius: 6px;
  color: #aaa;
  padding: 6px 18px;
  cursor: pointer;
  font-size: 0.88rem;
  transition: all 0.2s;
}
#regex-app .ra-tab.active {
  background: #00ff88;
  color: #1a1a2e;
  border-color: #00ff88;
  font-weight: bold;
}

/* Copy feedback */
#regex-app .ra-copy-msg {
  font-size: 0.82rem;
  color: #00ff88;
  margin-left: 8px;
  opacity: 0;
  transition: opacity 0.3s;
}
#regex-app .ra-copy-msg.show { opacity: 1; }

/* Scrollbar */
#regex-app ::-webkit-scrollbar { width: 6px; height: 6px; }
#regex-app ::-webkit-scrollbar-track { background: #0d0d1a; }
#regex-app ::-webkit-scrollbar-thumb { background: #0f3460; border-radius: 3px; }

/* Responsive */
@media (max-width: 600px) {
  #regex-app { padding: 14px; }
  #regex-app .ra-row { flex-direction: column; align-items: stretch; }
  #regex-app select { min-width: 100%; }
}
</style>

<!-- ========== PATTERN & FLAGS ========== -->
<div class="ra-section">
  <h2>正規表現パターン</h2>
  <div class="ra-row" style="margin-bottom:10px;">
    <span style="color:#aaa;font-size:1.1rem;">/</span>
    <input type="text" id="ra-pattern" placeholder="正規表現を入力... 例: \d{3}-\d{4}" autocomplete="off" spellcheck="false">
    <span style="color:#aaa;font-size:1.1rem;">/</span>
    <span id="ra-flag-display" style="color:#00ff88;font-family:monospace;min-width:40px;">g</span>
  </div>
  <div class="ra-flags">
    <span style="font-size:0.85rem;color:#aaa;margin-right:4px;">フラグ:</span>
    <label class="ra-flag-item"><input type="checkbox" id="flag-g" checked> g <span style="color:#666;font-size:0.78rem;">(全体)</span></label>
    <label class="ra-flag-item"><input type="checkbox" id="flag-i"> i <span style="color:#666;font-size:0.78rem;">(大小無視)</span></label>
    <label class="ra-flag-item"><input type="checkbox" id="flag-m"> m <span style="color:#666;font-size:0.78rem;">(複数行)</span></label>
    <label class="ra-flag-item"><input type="checkbox" id="flag-s"> s <span style="color:#666;font-size:0.78rem;">(ドット改行)</span></label>
    <label class="ra-flag-item"><input type="checkbox" id="flag-u"> u <span style="color:#666;font-size:0.78rem;">(Unicode)</span></label>
  </div>
  <div class="ra-error" id="ra-error"></div>

  <!-- Preset patterns -->
  <div class="ra-row" style="margin-top:12px;">
    <span style="font-size:0.85rem;color:#aaa;white-space:nowrap;">よく使うパターン:</span>
    <select id="ra-presets">
      <option value="">-- 選択してください --</option>
      <optgroup label="基本">
        <option value="\\d+">数字 (\d+)</option>
        <option value="\\w+">単語文字 (\w+)</option>
        <option value="\\s+">空白文字 (\s+)</option>
        <option value="[a-zA-Z]+">英字のみ</option>
      </optgroup>
      <optgroup label="連絡先">
        <option value="[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}">メールアドレス</option>
        <option value="https?://[\\w/:%#\\$&\\?\\(\\)~\\.=\\+\\-]+">URL (http/https)</option>
        <option value="0\\d{1,4}[\\-\\s]?\\d{1,4}[\\-\\s]?\\d{4}">電話番号（固定・携帯）</option>
        <option value="0[789]0[\\-\\s]?\\d{4}[\\-\\s]?\\d{4}">携帯電話番号</option>
      </optgroup>
      <optgroup label="日本の住所・コード">
        <option value="\\d{3}-\\d{4}">郵便番号 (123-4567)</option>
        <option value="〒?\\d{3}-\\d{4}">郵便番号 (〒付き)</option>
        <option value="\\d{4}[年/\\-]\\d{1,2}[月/\\-]\\d{1,2}日?">日付（年月日）</option>
        <option value="[A-Z]{2}\\d{2}[A-Z]\\d{7}">国際郵便追跡番号</option>
      </optgroup>
      <optgroup label="日本語文字">
        <option value="[\\u3041-\\u3096]+">ひらがな</option>
        <option value="[\\u30A1-\\u30FC]+">カタカナ（半角除く）</option>
        <option value="[\\uFF65-\\uFF9F]+">半角カタカナ</option>
        <option value="[\\u4E00-\\u9FFF]+">漢字（CJK統合）</option>
        <option value="[\\u3041-\\u3096\\u30A1-\\u30FC\\u4E00-\\u9FFF]+">日本語（ひら・カタ・漢字）</option>
        <option value="[\\uFF01-\\uFF5E]+">全角英数字・記号</option>
        <option value="[\\u3000-\\u303F]+">CJK記号・句読点</option>
      </optgroup>
      <optgroup label="フォーマット">
        <option value="#[0-9a-fA-F]{3,6}">カラーコード (HEX)</option>
        <option value="\\d{4}-\\d{2}-\\d{2}">日付 (YYYY-MM-DD)</option>
        <option value="\\d{1,3}\\.\\d{1,3}\\.\\d{1,3}\\.\\d{1,3}">IPアドレス (v4)</option>
        <option value="([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}">MACアドレス</option>
        <option value="[0-9]{4}[\\s\\-]?[0-9]{4}[\\s\\-]?[0-9]{4}[\\s\\-]?[0-9]{4}">クレジットカード番号</option>
      </optgroup>
    </select>
    <button class="ra-btn-ghost" onclick="applyPreset()">適用</button>
  </div>
</div>

<!-- ========== TEST STRING ========== -->
<div class="ra-section">
  <h2>テスト文字列</h2>
  <div class="ra-highlight-wrapper">
    <div id="ra-highlight-display" aria-hidden="true"></div>
    <textarea id="ra-test-input" placeholder="テストしたい文字列を入力してください...&#10;例: 田中さんのメールはtanaka@example.co.jpです。電話は090-1234-5678。"></textarea>
  </div>
  <div class="ra-match-count" id="ra-match-count"></div>
</div>

<!-- ========== MODE TABS ========== -->
<div class="ra-section">
  <div class="ra-tabs">
    <button class="ra-tab active" id="tab-match" onclick="setMode('match')">マッチ結果</button>
    <button class="ra-tab" id="tab-replace" onclick="setMode('replace')">置換モード</button>
  </div>

  <!-- Match results -->
  <div id="mode-match">
    <div id="ra-results"><p style="color:#666;font-size:0.88rem;">マッチ結果がここに表示されます。</p></div>
  </div>

  <!-- Replace mode -->
  <div id="mode-replace" style="display:none;">
    <div class="ra-replace-row">
      <span style="color:#aaa;font-size:0.88rem;white-space:nowrap;">置換パターン:</span>
      <input type="text" id="ra-replace-pattern" placeholder="置換後の文字列（$1, $2 でグループ参照）" autocomplete="off" spellcheck="false">
      <button class="ra-btn" onclick="copyReplaceOutput()">コピー</button>
      <span class="ra-copy-msg" id="ra-copy-replace-msg">コピーしました</span>
    </div>
    <div id="ra-replace-output">置換結果がここに表示されます。</div>
  </div>
</div>

<!-- ========== CHEATSHEET ========== -->
<div class="ra-section ra-cheatsheet">
  <div style="display:flex;align-items:center;gap:12px;flex-wrap:wrap;">
    <h2 style="margin:0;">正規表現チートシート</h2>
    <button class="ra-cs-toggle" onclick="toggleCheatsheet()">▼ 表示する</button>
  </div>
  <div id="ra-cs-body">
    <table class="ra-cs-table">
      <thead><tr><th>パターン</th><th>説明</th><th>例</th></tr></thead>
      <tbody>
        <tr><td><code>.</code></td><td>任意の1文字（改行除く）</td><td><code>a.c</code> → "abc", "a1c"</td></tr>
        <tr><td><code>^</code></td><td>行の先頭</td><td><code>^Hello</code></td></tr>
        <tr><td><code>$</code></td><td>行の末尾</td><td><code>end$</code></td></tr>
        <tr><td><code>*</code></td><td>0回以上の繰り返し</td><td><code>ab*c</code> → "ac", "abc", "abbc"</td></tr>
        <tr><td><code>+</code></td><td>1回以上の繰り返し</td><td><code>ab+c</code> → "abc", "abbc"</td></tr>
        <tr><td><code>?</code></td><td>0回または1回</td><td><code>colou?r</code></td></tr>
        <tr><td><code>{n}</code></td><td>ちょうどn回</td><td><code>\d{4}</code> → 4桁の数字</td></tr>
        <tr><td><code>{n,m}</code></td><td>n〜m回</td><td><code>\d{2,4}</code></td></tr>
        <tr><td><code>[abc]</code></td><td>いずれか1文字</td><td><code>[aeiou]</code> → 母音</td></tr>
        <tr><td><code>[^abc]</code></td><td>以外の1文字</td><td><code>[^0-9]</code> → 数字以外</td></tr>
        <tr><td><code>(abc)</code></td><td>キャプチャグループ</td><td><code>(\d{3})-(\d{4})</code></td></tr>
        <tr><td><code>(?:abc)</code></td><td>非キャプチャグループ</td><td><code>(?:https?)</code></td></tr>
        <tr><td><code>a|b</code></td><td>aまたはb</td><td><code>cat|dog</code></td></tr>
        <tr><td><code>\d</code></td><td>数字 [0-9]</td><td><code>\d+</code></td></tr>
        <tr><td><code>\D</code></td><td>数字以外</td><td></td></tr>
        <tr><td><code>\w</code></td><td>単語文字 [a-zA-Z0-9_]</td><td></td></tr>
        <tr><td><code>\W</code></td><td>単語文字以外</td><td></td></tr>
        <tr><td><code>\s</code></td><td>空白文字</td><td></td></tr>
        <tr><td><code>\S</code></td><td>空白文字以外</td><td></td></tr>
        <tr><td><code>\b</code></td><td>単語境界</td><td><code>\bword\b</code></td></tr>
        <tr><td><code>(?=...)</code></td><td>肯定先読み</td><td><code>\d(?=px)</code></td></tr>
        <tr><td><code>(?!...)</code></td><td>否定先読み</td><td><code>\d(?!px)</code></td></tr>
        <tr><td><code>*?</code> / <code>+?</code></td><td>非貪欲マッチ</td><td><code>&lt;.+?&gt;</code></td></tr>
      </tbody>
    </table>
  </div>
</div>

</div><!-- #regex-app -->

<script>
(function() {
  'use strict';

  var currentMode = 'match';
  var debounceTimer = null;

  function getFlags() {
    var f = '';
    if (document.getElementById('flag-g').checked) f += 'g';
    if (document.getElementById('flag-i').checked) f += 'i';
    if (document.getElementById('flag-m').checked) f += 'm';
    if (document.getElementById('flag-s').checked) f += 's';
    if (document.getElementById('flag-u').checked) f += 'u';
    return f;
  }

  function updateFlagDisplay() {
    document.getElementById('ra-flag-display').textContent = getFlags() || '(なし)';
  }

  function escapeHtml(str) {
    return str
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  function run() {
    var patternVal = document.getElementById('ra-pattern').value;
    var testVal = document.getElementById('ra-test-input').value;
    var errorEl = document.getElementById('ra-error');
    var countEl = document.getElementById('ra-match-count');
    var highlightEl = document.getElementById('ra-highlight-display');
    var resultsEl = document.getElementById('ra-results');

    updateFlagDisplay();

    if (!patternVal) {
      errorEl.textContent = '';
      countEl.textContent = '';
      highlightEl.innerHTML = '';
      resultsEl.innerHTML = '<p style="color:#666;font-size:0.88rem;">マッチ結果がここに表示されます。</p>';
      updateReplace(null, testVal);
      return;
    }

    var flags = getFlags();
    var regex;
    try {
      regex = new RegExp(patternVal, flags);
      errorEl.textContent = '';
    } catch(e) {
      errorEl.textContent = 'エラー: ' + e.message;
      countEl.textContent = '';
      highlightEl.innerHTML = '';
      resultsEl.innerHTML = '<p style="color:#ff4d6d;font-size:0.88rem;">正規表現が無効です。</p>';
      updateReplace(null, testVal);
      return;
    }

    // Find all matches
    var matches = [];
    var safeRegex;
    try {
      safeRegex = new RegExp(patternVal, flags.indexOf('g') === -1 ? flags : flags);
      if (flags.indexOf('g') !== -1) {
        var m;
        // Reset lastIndex safety
        safeRegex.lastIndex = 0;
        while ((m = safeRegex.exec(testVal)) !== null) {
          matches.push(m);
          if (!m[0] && m.index === safeRegex.lastIndex) {
            safeRegex.lastIndex++;
          }
          if (matches.length > 1000) break;
        }
      } else {
        var single = safeRegex.exec(testVal);
        if (single) matches.push(single);
      }
    } catch(e) {
      matches = [];
    }

    // Match count
    if (matches.length === 0) {
      countEl.textContent = 'マッチなし';
      countEl.style.color = '#ff4d6d';
    } else {
      countEl.textContent = matches.length + ' 件マッチ';
      countEl.style.color = '#00ff88';
    }

    // Highlight
    buildHighlight(testVal, matches, highlightEl);

    // Results panel
    buildResults(matches, resultsEl);

    // Replace
    updateReplace(regex, testVal);
  }

  function buildHighlight(text, matches, el) {
    if (matches.length === 0) {
      el.innerHTML = escapeHtml(text);
      return;
    }
    var result = '';
    var last = 0;
    for (var i = 0; i < matches.length; i++) {
      var m = matches[i];
      var start = m.index;
      var end = m.index + m[0].length;
      result += escapeHtml(text.slice(last, start));
      result += '<mark>' + escapeHtml(m[0] || ' ') + '</mark>';
      last = end;
    }
    result += escapeHtml(text.slice(last));
    el.innerHTML = result;
  }

  function buildResults(matches, el) {
    if (matches.length === 0) {
      el.innerHTML = '<p style="color:#ff4d6d;font-size:0.88rem;">マッチする文字列が見つかりませんでした。</p>';
      return;
    }
    var html = '';
    var limit = Math.min(matches.length, 100);
    for (var i = 0; i < limit; i++) {
      var m = matches[i];
      html += '<div class="ra-match-item">';
      html += '<div class="ra-match-header">';
      html += 'マッチ <span>#' + (i+1) + '</span>';
      html += '&nbsp;&nbsp;インデックス: <span>' + m.index + '</span>';
      html += '&nbsp;&nbsp;長さ: <span>' + m[0].length + '</span>';
      html += '</div>';
      html += '<div><span class="ra-match-val">' + escapeHtml(m[0]) + '</span></div>';
      if (m.length > 1) {
        html += '<div class="ra-group-list">';
        for (var g = 1; g < m.length; g++) {
          html += '<span class="ra-group-badge">$' + g + ': ' + (m[g] !== undefined ? escapeHtml(m[g]) : '<i style="color:#666">未定義</i>') + '</span>';
        }
        html += '</div>';
      }
      html += '</div>';
    }
    if (matches.length > 100) {
      html += '<p style="color:#aaa;font-size:0.82rem;">... 他 ' + (matches.length - 100) + ' 件（表示は100件まで）</p>';
    }
    el.innerHTML = html;
  }

  function updateReplace(regex, testVal) {
    var replaceOutput = document.getElementById('ra-replace-output');
    if (currentMode !== 'replace') return;
    if (!regex) {
      replaceOutput.textContent = testVal || '置換結果がここに表示されます。';
      return;
    }
    var replPat = document.getElementById('ra-replace-pattern').value;
    try {
      var result = testVal.replace(regex, replPat);
      replaceOutput.textContent = result;
    } catch(e) {
      replaceOutput.textContent = 'エラー: ' + e.message;
    }
  }

  window.setMode = function(mode) {
    currentMode = mode;
    document.getElementById('tab-match').className = 'ra-tab' + (mode === 'match' ? ' active' : '');
    document.getElementById('tab-replace').className = 'ra-tab' + (mode === 'replace' ? ' active' : '');
    document.getElementById('mode-match').style.display = mode === 'match' ? '' : 'none';
    document.getElementById('mode-replace').style.display = mode === 'replace' ? '' : 'none';
    run();
  };

  window.applyPreset = function() {
    var sel = document.getElementById('ra-presets');
    var val = sel.value;
    if (!val) return;
    document.getElementById('ra-pattern').value = val;
    // Set flags appropriately
    document.getElementById('flag-g').checked = true;
    document.getElementById('flag-u').checked = (val.indexOf('\\u') !== -1);
    run();
  };

  window.toggleCheatsheet = function() {
    var body = document.getElementById('ra-cs-body');
    var btn = document.querySelector('.ra-cs-toggle');
    if (body.classList.contains('open')) {
      body.classList.remove('open');
      btn.textContent = '▼ 表示する';
    } else {
      body.classList.add('open');
      btn.textContent = '▲ 閉じる';
    }
  };

  window.copyReplaceOutput = function() {
    var text = document.getElementById('ra-replace-output').textContent;
    if (!text) return;
    navigator.clipboard.writeText(text).then(function() {
      showCopyMsg('ra-copy-replace-msg');
    }).catch(function() {
      var ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showCopyMsg('ra-copy-replace-msg');
    });
  };

  function showCopyMsg(id) {
    var el = document.getElementById(id);
    el.classList.add('show');
    setTimeout(function() { el.classList.remove('show'); }, 2000);
  }

  function debounce(fn, ms) {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(fn, ms);
  }

  // Sync highlight overlay scroll with textarea scroll
  var testInput = document.getElementById('ra-test-input');
  var highlightDisplay = document.getElementById('ra-highlight-display');

  testInput.addEventListener('scroll', function() {
    highlightDisplay.scrollTop = testInput.scrollTop;
    highlightDisplay.scrollLeft = testInput.scrollLeft;
  });

  // Event listeners
  document.getElementById('ra-pattern').addEventListener('input', function() { debounce(run, 120); });
  document.getElementById('ra-test-input').addEventListener('input', function() { debounce(run, 80); });
  document.getElementById('ra-replace-pattern').addEventListener('input', function() { debounce(run, 120); });

  var flags = ['flag-g','flag-i','flag-m','flag-s','flag-u'];
  flags.forEach(function(id) {
    document.getElementById(id).addEventListener('change', function() { run(); });
  });

  // Initial state
  document.getElementById('ra-test-input').value = '田中さんのメールはtanaka@example.co.jpです。\n電話番号: 090-1234-5678\n郵便番号: 〒100-0001\nウェブサイト: https://www.example.com';
  document.getElementById('ra-pattern').value = '[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}';
  run();
})();
</script>

---

## 正規表現の基礎

正規表現（Regular Expression、略して「regex」または「regexp」）は、文字列のパターンを記述するための特殊な記法です。テキスト検索・抽出・置換・バリデーションなど、開発現場のあらゆる場面で活用されています。たとえば、メールアドレスの検証、ログファイルからの特定データ抽出、Webスクレイピングでの情報取得など、正規表現を使いこなすことでコードを大幅に簡潔にできます。

JavaScriptでは `new RegExp(pattern, flags)` またはリテラル記法 `/pattern/flags` で正規表現を作成できます。フラグには `g`（グローバル：全てのマッチを検索）、`i`（大文字小文字を無視）、`m`（複数行モード）、`s`（`.` で改行にもマッチ）、`u`（Unicodeモード）があり、目的に合わせて組み合わせて使います。日本語テキストを扱う場合は `u` フラグを有効にすることで、Unicodeのコードポイントを正しく処理できます。

正規表現はメタ文字（`. * + ? ^ $ { } [ ] | ( ) \`）を使って柔軟なパターンを表現します。最初は複雑に見えますが、基本的なメタ文字の意味を覚えれば、あとは組み合わせるだけです。上のチートシートや、よく使うパターン集を参考に、まずはシンプルなパターンから試してみましょう。

---

## よく使う正規表現パターン

| パターン | 正規表現 | 説明 |
|---|---|---|
| メールアドレス | `[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}` | 標準的なメールアドレス形式 |
| 日本の携帯番号 | `0[789]0[\-\s]?\d{4}[\-\s]?\d{4}` | 070/080/090 始まりの携帯番号 |
| 郵便番号 | `\d{3}-\d{4}` | 123-4567 形式 |
| ひらがな | `[\u3041-\u3096]+` | ひらがなのみを抽出 |
| カタカナ | `[\u30A1-\u30FC]+` | 全角カタカナのみを抽出 |
| 漢字 | `[\u4E00-\u9FFF]+` | CJK統合漢字ブロック |
| 日付 (YYYY-MM-DD) | `\d{4}-\d{2}-\d{2}` | ISO 8601形式の日付 |
| IPアドレス (v4) | `\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}` | IPv4アドレスの簡易マッチ |

---

## 関連ツール

> JSONデータを整形・検証 → [JSONフォーマッター](/ja/tools/json-formatter/)

> Base64のエンコード・デコード → [Base64エンコーダー](/ja/tools/base64-encoder/)

> 文字数をリアルタイムでカウント → [文字数カウンター](/ja/tools/moji-counter/)

---

**エンジニアの経理業務を自動化**

正規表現で効率化するように、経理も自動化しませんか？クラウド会計ソフト「freee」なら、API連携で経費データの取り込みも自動化できます。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
