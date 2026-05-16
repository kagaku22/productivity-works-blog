---
title: "URLエンコード・デコードツール"
date: 2025-05-16
description: "無料のURLエンコーダー・デコーダー。特殊文字のパーセントエンコードや、エンコード済みURLの復元がブラウザで即完了。登録不要。"
categories: ["無料ツール"]
slug: "url-encoder-decoder"
ShowToc: false
cover:
  image: "/images/covers/url-encoder-decoder-ja.png"
  alt: "URLエンコード・デコードツール"
---

<div id="ue-app">

<style>
#ue-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Segoe UI", sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1e293b;
}
#ue-app * {
  box-sizing: border-box;
}
#ue-app h2.ue-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 16px 0;
}
#ue-app .ue-card {
  background: #ffffff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 20px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
/* Mode toggle */
#ue-app .ue-mode-row {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}
#ue-app .ue-mode-label {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
}
#ue-app .ue-toggle-group {
  display: flex;
  background: #f1f5f9;
  border-radius: 8px;
  padding: 3px;
  gap: 2px;
}
#ue-app .ue-toggle-btn {
  padding: 7px 18px;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  background: transparent;
  color: #64748b;
  transition: background 0.15s, color 0.15s;
}
#ue-app .ue-toggle-btn.active {
  background: #ffffff;
  color: #0f172a;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12);
}
#ue-app .ue-scope-group {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  align-items: center;
}
#ue-app .ue-scope-label {
  font-size: 13px;
  color: #64748b;
  font-weight: 500;
}
#ue-app .ue-scope-btn {
  padding: 5px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  background: #fff;
  color: #475569;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
}
#ue-app .ue-scope-btn.active {
  border-color: #3b82f6;
  background: #eff6ff;
  color: #1d4ed8;
}
/* Textarea area */
#ue-app .ue-io-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
@media (max-width: 600px) {
  #ue-app .ue-io-row { grid-template-columns: 1fr; }
}
#ue-app .ue-io-block {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
#ue-app .ue-io-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#ue-app .ue-io-title {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  letter-spacing: 0.03em;
}
#ue-app .ue-char-count {
  font-size: 11px;
  color: #94a3b8;
}
#ue-app textarea {
  width: 100%;
  min-height: 160px;
  padding: 12px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  font-family: "SFMono-Regular", "Fira Code", "Consolas", monospace;
  font-size: 13px;
  line-height: 1.6;
  color: #1e293b;
  background: #f8fafc;
  resize: vertical;
  transition: border-color 0.15s;
  outline: none;
}
#ue-app textarea:focus {
  border-color: #3b82f6;
  background: #fff;
}
#ue-app textarea.ue-output {
  background: #f0fdf4;
  border-color: #bbf7d0;
  color: #14532d;
}
#ue-app textarea.ue-output-decode {
  background: #fefce8;
  border-color: #fde68a;
  color: #78350f;
}
/* Action bar */
#ue-app .ue-action-bar {
  display: flex;
  gap: 10px;
  align-items: center;
  flex-wrap: wrap;
  margin-top: 16px;
}
#ue-app .ue-btn {
  padding: 9px 20px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  display: flex;
  align-items: center;
  gap: 6px;
}
#ue-app .ue-btn:active { transform: scale(0.97); }
#ue-app .ue-btn-primary {
  background: #3b82f6;
  color: #fff;
}
#ue-app .ue-btn-primary:hover { opacity: 0.88; }
#ue-app .ue-btn-secondary {
  background: #f1f5f9;
  color: #475569;
  border: 1.5px solid #e2e8f0;
}
#ue-app .ue-btn-secondary:hover { background: #e2e8f0; }
#ue-app .ue-btn-copy {
  background: #10b981;
  color: #fff;
}
#ue-app .ue-btn-copy:hover { opacity: 0.88; }
#ue-app .ue-auto-badge {
  margin-left: auto;
  font-size: 11px;
  color: #6366f1;
  font-weight: 600;
  background: #eef2ff;
  border-radius: 5px;
  padding: 3px 9px;
  border: 1px solid #c7d2fe;
}
/* Breakdown table */
#ue-app .ue-breakdown {
  margin-top: 20px;
}
#ue-app .ue-breakdown-title {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  letter-spacing: 0.03em;
  margin-bottom: 10px;
}
#ue-app .ue-table-wrap {
  overflow-x: auto;
  border-radius: 8px;
  border: 1.5px solid #e2e8f0;
}
#ue-app table.ue-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
#ue-app table.ue-table th {
  background: #f8fafc;
  color: #64748b;
  font-weight: 700;
  padding: 8px 14px;
  text-align: left;
  border-bottom: 1.5px solid #e2e8f0;
}
#ue-app table.ue-table td {
  padding: 7px 14px;
  border-bottom: 1px solid #f1f5f9;
  font-family: "SFMono-Regular", "Fira Code", monospace;
  vertical-align: middle;
}
#ue-app table.ue-table tr:last-child td { border-bottom: none; }
#ue-app table.ue-table tr:nth-child(even) td { background: #f8fafc; }
#ue-app .ue-char-orig { color: #1e293b; font-weight: 600; }
#ue-app .ue-char-enc  { color: #1d4ed8; }
#ue-app .ue-char-note { color: #64748b; font-size: 12px; font-family: inherit; }
/* Toast */
#ue-app .ue-toast {
  position: fixed;
  bottom: 28px;
  right: 28px;
  background: #0f172a;
  color: #fff;
  padding: 11px 20px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s;
  z-index: 9999;
  box-shadow: 0 4px 16px rgba(0,0,0,0.25);
}
#ue-app .ue-toast.show { opacity: 1; }
/* Info box */
#ue-app .ue-info {
  background: #eff6ff;
  border: 1px solid #bfdbfe;
  border-radius: 8px;
  padding: 12px 16px;
  font-size: 13px;
  color: #1d4ed8;
  margin-top: 16px;
  line-height: 1.6;
}
</style>

<div class="ue-card">
  <h2 class="ue-title">URLエンコード・デコードツール</h2>

  <!-- Mode toggle -->
  <div class="ue-mode-row">
    <span class="ue-mode-label">モード：</span>
    <div class="ue-toggle-group">
      <button class="ue-toggle-btn active" id="ue-mode-encode" onclick="ueSetMode('encode')">エンコード</button>
      <button class="ue-toggle-btn" id="ue-mode-decode" onclick="ueSetMode('decode')">デコード</button>
    </div>
    <div class="ue-scope-group" id="ue-scope-group">
      <span class="ue-scope-label">範囲：</span>
      <button class="ue-scope-btn active" id="ue-scope-component" onclick="ueSetScope('component')">コンポーネント <span style="font-weight:400;font-size:11px;">(encodeURIComponent)</span></button>
      <button class="ue-scope-btn" id="ue-scope-full" onclick="ueSetScope('full')">URL全体 <span style="font-weight:400;font-size:11px;">(encodeURI)</span></button>
    </div>
  </div>

  <!-- I/O -->
  <div class="ue-io-row">
    <div class="ue-io-block">
      <div class="ue-io-header">
        <span class="ue-io-title" id="ue-input-label">入力テキスト / URL</span>
        <span class="ue-char-count" id="ue-input-count">0 文字</span>
      </div>
      <textarea id="ue-input" placeholder="テキストまたはURLを貼り付けてください…" oninput="ueOnInput()" spellcheck="false"></textarea>
    </div>
    <div class="ue-io-block">
      <div class="ue-io-header">
        <span class="ue-io-title" id="ue-output-label">エンコード結果</span>
        <span class="ue-char-count" id="ue-output-count">0 文字</span>
      </div>
      <textarea id="ue-output" class="ue-output" readonly placeholder="結果がここに表示されます…" spellcheck="false"></textarea>
    </div>
  </div>

  <!-- Actions -->
  <div class="ue-action-bar">
    <button class="ue-btn ue-btn-primary" onclick="ueProcess()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="5 12 12 5 19 12"/><polyline points="5 19 12 12 19 19"/></svg>
      <span id="ue-process-label">エンコード実行</span>
    </button>
    <button class="ue-btn ue-btn-copy" onclick="ueCopyResult()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
      コピー
    </button>
    <button class="ue-btn ue-btn-secondary" onclick="ueClear()">クリア</button>
    <button class="ue-btn ue-btn-secondary" onclick="ueSwap()">&#8645; 入れ替え</button>
    <span class="ue-auto-badge" id="ue-auto-badge">自動判定: ON</span>
  </div>

  <div class="ue-info" id="ue-scope-info">
    <strong>encodeURIComponent</strong> — エンコードされない文字：<code>A–Z a–z 0–9 - _ . ! ~ * ' ( )</code>。クエリパラメータやパスセグメントのエンコードに最適。
  </div>
</div>

<!-- Breakdown table -->
<div class="ue-card ue-breakdown" id="ue-breakdown-card" style="display:none;">
  <div class="ue-breakdown-title">エンコードされた文字の内訳</div>
  <div class="ue-table-wrap">
    <table class="ue-table">
      <thead>
        <tr>
          <th>元の文字</th>
          <th>エンコード後</th>
          <th>Unicodeコード</th>
          <th>説明</th>
        </tr>
      </thead>
      <tbody id="ue-breakdown-body"></tbody>
    </table>
  </div>
</div>

<div class="ue-toast" id="ue-toast"></div>

<script>
(function() {
  var mode = 'encode';
  var scope = 'component';

  var charNotes = {
    ' ': 'スペース',
    '!': '感嘆符',
    '"': '二重引用符',
    '#': 'ハッシュ（フラグメント）',
    '$': 'ドル記号',
    '%': 'パーセント記号',
    '&': 'アンパサンド',
    "'": 'アポストロフィ',
    '(': '左括弧',
    ')': '右括弧',
    '*': 'アスタリスク',
    '+': 'プラス記号',
    ',': 'カンマ',
    '/': 'スラッシュ',
    ':': 'コロン',
    ';': 'セミコロン',
    '=': '等号',
    '?': '疑問符',
    '@': 'アットマーク',
    '[': '左角括弧',
    ']': '右角括弧',
  };

  window.ueSetMode = function(m) {
    mode = m;
    document.getElementById('ue-mode-encode').classList.toggle('active', m === 'encode');
    document.getElementById('ue-mode-decode').classList.toggle('active', m === 'decode');
    document.getElementById('ue-scope-group').style.display = m === 'encode' ? '' : 'none';
    document.getElementById('ue-scope-info').style.display = m === 'encode' ? '' : 'none';
    document.getElementById('ue-process-label').textContent = m === 'encode' ? 'エンコード実行' : 'デコード実行';
    document.getElementById('ue-input-label').textContent = m === 'encode' ? '入力テキスト / URL' : 'エンコード済みURL';
    document.getElementById('ue-output-label').textContent = m === 'encode' ? 'エンコード結果' : 'デコード結果';
    var out = document.getElementById('ue-output');
    out.className = m === 'encode' ? 'ue-output' : 'ue-output-decode';
    ueOnInput();
  };

  window.ueSetScope = function(s) {
    scope = s;
    document.getElementById('ue-scope-component').classList.toggle('active', s === 'component');
    document.getElementById('ue-scope-full').classList.toggle('active', s === 'full');
    var info = document.getElementById('ue-scope-info');
    if (s === 'component') {
      info.innerHTML = '<strong>encodeURIComponent</strong> — エンコードされない文字：<code>A–Z a–z 0–9 - _ . ! ~ * \' ( )</code>。クエリパラメータやパスセグメントのエンコードに最適。';
    } else {
      info.innerHTML = '<strong>encodeURI</strong> — URIとして有効な文字はエンコードされません：<code>A–Z a–z 0–9 ; , / ? : @ & = + $ - _ . ! ~ * \' ( ) #</code>。URL全体の構造を保ちながらエンコードする場合に使用。';
    }
    ueOnInput();
  };

  function ueEncode(text) {
    if (scope === 'component') return encodeURIComponent(text);
    return encodeURI(text);
  }

  function ueDecode(text) {
    try {
      return decodeURIComponent(text);
    } catch(e) {
      try { return decodeURI(text); } catch(e2) { return text; }
    }
  }

  function ueAutoDetect(text) {
    return /%[0-9A-Fa-f]{2}/.test(text) ? 'decode' : 'encode';
  }

  window.ueOnInput = function() {
    var input = document.getElementById('ue-input').value;
    document.getElementById('ue-input-count').textContent = input.length + ' 文字';
    if (input.length > 0) {
      var detected = ueAutoDetect(input);
      var badge = document.getElementById('ue-auto-badge');
      badge.textContent = '自動判定: ' + (detected === 'decode' ? 'デコード' : 'エンコード');
    } else {
      document.getElementById('ue-auto-badge').textContent = '自動判定: ON';
    }
    ueProcess();
  };

  window.ueProcess = function() {
    var input = document.getElementById('ue-input').value;
    if (!input) {
      document.getElementById('ue-output').value = '';
      document.getElementById('ue-output-count').textContent = '0 文字';
      document.getElementById('ue-breakdown-card').style.display = 'none';
      return;
    }
    var result;
    try {
      result = mode === 'encode' ? ueEncode(input) : ueDecode(input);
    } catch(e) {
      result = 'エラー: ' + e.message;
    }
    document.getElementById('ue-output').value = result;
    document.getElementById('ue-output-count').textContent = result.length + ' 文字';
    if (mode === 'encode') ueRenderBreakdown(input, result);
    else document.getElementById('ue-breakdown-card').style.display = 'none';
  };

  function ueRenderBreakdown(original, encoded) {
    var rows = [];
    var seen = {};
    for (var i = 0; i < original.length; i++) {
      var ch = original[i];
      var encCh;
      try {
        encCh = scope === 'component' ? encodeURIComponent(ch) : encodeURI(ch);
      } catch(e) { encCh = ch; }
      if (encCh !== ch && !seen[ch]) {
        seen[ch] = true;
        var codePoint = ch.codePointAt ? ch.codePointAt(0) : ch.charCodeAt(0);
        var note = charNotes[ch] || (codePoint > 127 ? 'ASCII以外の文字' : '特殊文字');
        rows.push({ orig: ch, enc: encCh, uni: 'U+' + codePoint.toString(16).toUpperCase().padStart(4,'0'), note: note });
      }
    }
    var tbody = document.getElementById('ue-breakdown-body');
    var card = document.getElementById('ue-breakdown-card');
    if (rows.length === 0) { card.style.display = 'none'; return; }
    card.style.display = '';
    tbody.innerHTML = rows.map(function(r) {
      var disp = r.orig === ' ' ? '&nbsp;（スペース）' : r.orig.replace(/&/g,'&amp;').replace(/</g,'&lt;');
      return '<tr><td class="ue-char-orig">' + disp + '</td><td class="ue-char-enc">' + r.enc + '</td><td class="ue-char-enc">' + r.uni + '</td><td class="ue-char-note">' + r.note + '</td></tr>';
    }).join('');
  }

  window.ueCopyResult = function() {
    var val = document.getElementById('ue-output').value;
    if (!val) return;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(val).then(function() { ueShowToast('クリップボードにコピーしました！'); });
    } else {
      var ta = document.getElementById('ue-output');
      ta.select();
      document.execCommand('copy');
      ueShowToast('クリップボードにコピーしました！');
    }
  };

  window.ueClear = function() {
    document.getElementById('ue-input').value = '';
    document.getElementById('ue-output').value = '';
    document.getElementById('ue-input-count').textContent = '0 文字';
    document.getElementById('ue-output-count').textContent = '0 文字';
    document.getElementById('ue-breakdown-card').style.display = 'none';
    document.getElementById('ue-auto-badge').textContent = '自動判定: ON';
  };

  window.ueSwap = function() {
    var out = document.getElementById('ue-output').value;
    document.getElementById('ue-input').value = out;
    ueOnInput();
  };

  function ueShowToast(msg) {
    var t = document.getElementById('ue-toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(function() { t.classList.remove('show'); }, 2000);
  }
})();
</script>

</div>

---

## 使い方

**URLエンコード**（パーセントエンコーディング）は、URLとして安全でない文字を `%XX` 形式に変換します。`XX` は文字のUTF-8バイト値の16進数表現です。

### モードの使い分け

| モード | 関数 | エンコードされない文字 |
|---|---|---|
| **encodeURIComponent** | クエリパラメータやパスセグメント単体のエンコード | `A–Z a–z 0–9 - _ . ! ~ * ' ( )` |
| **encodeURI** | URL全体のエンコード（構造を保持） | 上記に加え `; , / ? : @ & = + $ #` |

### よく使われる文字のエンコード例

| 文字 | エンコード後 | 用途 |
|---|---|---|
| スペース | `%20` | パス内の区切り |
| `&` | `%26` | クエリ値内のアンパサンド |
| `=` | `%3D` | クエリ値内の等号 |
| `+` | `%2B` | クエリ値内のプラス記号 |
| `#` | `%23` | URL内のハッシュ |
| `?` | `%3F` | URL内の疑問符 |

### よくある使用例

- **日本語URLのエンコード** — 日本語ドメインやパスを含むURLを安全な形式に変換
- **APIのクエリパラメータ** — 特殊文字を含む検索キーワードをパラメータとして送信
- **フォームデータの処理** — HTML フォームのPOSTデータに含まれる文字列の変換
- **エンコード済みURLの確認** — `%E3%81%82` などのエンコード文字列を元のテキストに戻す

---

<div class="ue-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">Webサイト運営の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、ドメイン・サーバー費用の経費精算もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

> HTMLエンティティを変換 → [HTMLエンティティエンコーダー](/ja/tools/html-entity-encoder/)
> 各種エンコーディング → [万能エンコーダー/デコーダー](/ja/tools/encoder-decoder/)
