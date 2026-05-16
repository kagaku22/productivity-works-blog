---
title: "文字列エスケープツール — マルチ言語エスケーパー"
date: 2025-05-16
description: "JSON・JavaScript・Python・Java・SQL・HTML等の文字列をエスケープ/アンエスケープ。引用符・バックスラッシュ・改行・特殊文字を処理。"
categories: ["無料ツール"]
slug: "string-escape-tool"
ShowToc: false
cover:
  image: "/images/covers/string-escape-tool-ja.png"
  alt: "文字列エスケープツール"
---

<div id="esc-app">

<style>
#esc-app *,
#esc-app *::before,
#esc-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#esc-app {
  font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  font-size: 15px;
  color: #1a1a2e;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 8px 48px;
}

#esc-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 12px;
  color: #1a1a2e;
}

#esc-app .esc-intro {
  background: #f0f4ff;
  border-left: 4px solid #3b6ef8;
  border-radius: 4px;
  padding: 14px 16px;
  margin-bottom: 24px;
  font-size: 0.93rem;
  color: #333;
  line-height: 1.75;
}

/* モード選択 */
#esc-app .esc-mode-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}

#esc-app .esc-mode-btn {
  padding: 6px 14px;
  border-radius: 20px;
  border: 2px solid #d0d5e8;
  background: #fff;
  color: #555;
  font-size: 0.85rem;
  font-weight: 700;
  cursor: pointer;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
  white-space: nowrap;
}

#esc-app .esc-mode-btn:hover {
  border-color: #3b6ef8;
  color: #3b6ef8;
}

#esc-app .esc-mode-btn.active {
  background: #3b6ef8;
  border-color: #3b6ef8;
  color: #fff;
}

/* オプション行 */
#esc-app .esc-options-row {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

#esc-app .esc-toggle-label {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-size: 0.88rem;
  color: #444;
  user-select: none;
}

#esc-app .esc-toggle-label input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #3b6ef8;
  cursor: pointer;
}

#esc-app .esc-mode-desc {
  font-size: 0.82rem;
  color: #777;
  font-style: italic;
}

/* テキストエリア */
#esc-app .esc-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}

@media (max-width: 600px) {
  #esc-app .esc-panels {
    grid-template-columns: 1fr;
  }
}

#esc-app .esc-panel {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

#esc-app .esc-panel-label {
  font-size: 0.82rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #555;
}

#esc-app .esc-textarea {
  width: 100%;
  min-height: 200px;
  padding: 12px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.88rem;
  line-height: 1.6;
  border: 2px solid #d0d5e8;
  border-radius: 8px;
  background: #fafbff;
  color: #1a1a2e;
  resize: vertical;
  transition: border-color 0.15s;
  outline: none;
}

#esc-app .esc-textarea:focus {
  border-color: #3b6ef8;
  background: #fff;
}

#esc-app .esc-textarea.output {
  background: #f4f7ff;
  color: #1a3a6e;
}

/* ボタン */
#esc-app .esc-action-row {
  display: flex;
  gap: 10px;
  margin-bottom: 8px;
  flex-wrap: wrap;
  align-items: center;
}

#esc-app .esc-btn {
  padding: 10px 24px;
  border-radius: 8px;
  border: none;
  font-size: 0.9rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  letter-spacing: 0.02em;
  font-family: inherit;
}

#esc-app .esc-btn:active {
  transform: scale(0.97);
}

#esc-app .esc-btn-escape {
  background: #3b6ef8;
  color: #fff;
}

#esc-app .esc-btn-escape:hover {
  background: #2550d0;
}

#esc-app .esc-btn-unescape {
  background: #12b886;
  color: #fff;
}

#esc-app .esc-btn-unescape:hover {
  background: #0a9a70;
}

#esc-app .esc-btn-copy {
  background: #f0f4ff;
  color: #3b6ef8;
  border: 2px solid #3b6ef8;
  padding: 8px 18px;
}

#esc-app .esc-btn-copy:hover {
  background: #3b6ef8;
  color: #fff;
}

#esc-app .esc-btn-clear {
  background: #fff;
  color: #999;
  border: 2px solid #d0d5e8;
  padding: 8px 14px;
  font-size: 0.82rem;
}

#esc-app .esc-btn-clear:hover {
  border-color: #e05c5c;
  color: #e05c5c;
}

/* ステータス */
#esc-app .esc-status {
  font-size: 0.82rem;
  color: #12b886;
  font-weight: 600;
  min-height: 18px;
  transition: opacity 0.3s;
}

#esc-app .esc-status.error {
  color: #e05c5c;
}

/* 参照テーブル */
#esc-app .esc-ref {
  margin-top: 32px;
  background: #fafbff;
  border: 1px solid #d0d5e8;
  border-radius: 10px;
  padding: 20px;
}

#esc-app .esc-ref h3 {
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 14px;
  color: #1a1a2e;
}

#esc-app .esc-ref-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 8px;
}

#esc-app .esc-ref-item {
  background: #fff;
  border: 1px solid #e0e5f0;
  border-radius: 6px;
  padding: 8px 12px;
  font-size: 0.82rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8px;
}

#esc-app .esc-ref-item code {
  font-family: monospace;
  background: #f0f4ff;
  padding: 1px 5px;
  border-radius: 3px;
  color: #3b6ef8;
  font-size: 0.88em;
  white-space: nowrap;
}

#esc-app .esc-ref-item span {
  color: #777;
}

/* 使い方 */
#esc-app .esc-howto {
  margin-top: 28px;
}

#esc-app .esc-howto h3 {
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 10px;
}

#esc-app .esc-howto ul {
  padding-left: 20px;
  line-height: 1.9;
  color: #444;
  font-size: 0.92rem;
}

/* 関連リンク */
#esc-app .esc-related {
  margin-top: 32px;
  padding-top: 20px;
  border-top: 1px solid #e0e5f0;
}

#esc-app .esc-related h3 {
  font-size: 0.88rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #777;
  margin-bottom: 10px;
}

#esc-app .esc-related-links {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

#esc-app .esc-related-links a {
  display: inline-block;
  padding: 7px 16px;
  border-radius: 20px;
  border: 2px solid #3b6ef8;
  color: #3b6ef8;
  font-size: 0.85rem;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.15s, color 0.15s;
}

#esc-app .esc-related-links a:hover {
  background: #3b6ef8;
  color: #fff;
}

/* freee CTA */
#esc-app .esc-cta-freee {
  margin-top: 36px;
  background: linear-gradient(135deg, #003087 0%, #0051cc 100%);
  border-radius: 12px;
  padding: 24px 28px;
  color: #fff;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

#esc-app .esc-cta-freee h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #fff;
  margin: 0;
}

#esc-app .esc-cta-freee p {
  font-size: 0.88rem;
  line-height: 1.7;
  color: #cce0ff;
  margin: 0;
}

#esc-app .esc-cta-freee a.esc-cta-btn {
  display: inline-block;
  align-self: flex-start;
  background: #fff;
  color: #003087;
  font-weight: 700;
  font-size: 0.88rem;
  padding: 10px 22px;
  border-radius: 8px;
  text-decoration: none;
  transition: background 0.15s, color 0.15s;
}

#esc-app .esc-cta-freee a.esc-cta-btn:hover {
  background: #e6f0ff;
}

@media (max-width: 480px) {
  #esc-app .esc-cta-freee {
    padding: 18px 16px;
  }
}
</style>

<div class="esc-intro">
  JSON・JavaScript/TypeScript・Python・Java・C#・SQL・HTML・XML・CSV・正規表現の10モードに対応した文字列エスケープ/アンエスケープツールです。テキストを貼り付け、モードを選んで<strong>エスケープ</strong>ボタンを押すだけ。アンエスケープも同様に1クリックで完了します。データはブラウザ外に送信されません。
</div>

<h2>言語 / コンテキストを選択</h2>
<div class="esc-mode-row" id="escModeRow"></div>

<div class="esc-options-row">
  <label class="esc-toggle-label">
    <input type="checkbox" id="escBulkMode">
    一括モード（各行を個別にエスケープ/アンエスケープ）
  </label>
  <span class="esc-mode-desc" id="escModeDesc"></span>
</div>

<div class="esc-panels">
  <div class="esc-panel">
    <div class="esc-panel-label">入力</div>
    <textarea class="esc-textarea" id="escInput" placeholder="ここに文字列を貼り付けてください…" spellcheck="false"></textarea>
  </div>
  <div class="esc-panel">
    <div class="esc-panel-label">出力</div>
    <textarea class="esc-textarea output" id="escOutput" placeholder="結果がここに表示されます…" readonly spellcheck="false"></textarea>
  </div>
</div>

<div class="esc-action-row">
  <button class="esc-btn esc-btn-escape" id="escEscapeBtn">エスケープ</button>
  <button class="esc-btn esc-btn-unescape" id="escUnescapeBtn">アンエスケープ</button>
  <button class="esc-btn esc-btn-copy" id="escCopyBtn">出力をコピー</button>
  <button class="esc-btn esc-btn-clear" id="escClearBtn">クリア</button>
</div>
<div class="esc-status" id="escStatus"></div>

<div class="esc-ref">
  <h3>エスケープシーケンス 早見表</h3>
  <div class="esc-ref-grid" id="escRefGrid"></div>
</div>

<div class="esc-howto">
  <h3>使い方</h3>
  <ul>
    <li><strong>モードを選ぶ</strong> — 対象の言語・フォーマットをボタンで選択します。</li>
    <li><strong>入力に貼り付ける</strong> — エスケープしたい生の文字列（またはアンエスケープしたいエスケープ済み文字列）を貼り付けます。</li>
    <li><strong>エスケープ / アンエスケープ</strong> — 目的のボタンをクリックすると右側に結果が即時表示されます。</li>
    <li><strong>一括モード</strong> — チェックを入れると、入力の各行を独立してエスケープ/アンエスケープします。文字列リストの一括処理に便利です。</li>
    <li><strong>出力をコピー</strong> — ワンクリックで結果をクリップボードにコピーします。</li>
  </ul>
</div>

<div class="esc-howto" style="margin-top:20px;">
  <h3>各モードの処理内容</h3>
  <ul>
    <li><strong>JSON</strong> — <code>"</code>・<code>\</code>・<code>/</code>・制御文字・ユニコード（<code>\uXXXX</code>）をRFC 8259準拠でエスケープ</li>
    <li><strong>JavaScript / TypeScript</strong> — シングル・ダブルクォート・バッククォート・<code>\n \t \r \0</code>・ユニコード</li>
    <li><strong>Python</strong> — シングル・ダブルクォート・<code>\n \t \r \\ \0</code>・16進エスケープ</li>
    <li><strong>Java / C#</strong> — Cスタイルエスケープ + ユニコード <code>\uXXXX</code></li>
    <li><strong>SQL</strong> — シングルクォートの二重化（ANSI SQL標準）</li>
    <li><strong>HTML</strong> — 名前付きエンティティ：<code>&amp;amp; &amp;lt; &amp;gt; &amp;quot; &amp;#39;</code></li>
    <li><strong>XML</strong> — XML仕様に準拠した5つの定義済みエンティティ</li>
    <li><strong>CSV</strong> — RFC 4180に基づくフィールドクォーティング・埋め込みクォートの二重化</li>
    <li><strong>正規表現</strong> — <code>. * + ? ^ $ { } [ ] | ( ) \</code> などすべてのメタ文字をエスケープ</li>
  </ul>
</div>

<div class="esc-related">
  <h3>関連ツール</h3>
  <div class="esc-related-links">
    <a href="/ja/tools/json-formatter/">JSONフォーマッター</a>
    <a href="/ja/tools/html-entity-encoder/">HTMLエンティティエンコーダー</a>
    <a href="/ja/tools/url-encoder/">URLエンコーダー</a>
  </div>
</div>

<div class="esc-cta-freee">
  <h3>freeeで会計・経費管理をもっとスマートに</h3>
  <p>
    開発者・フリーランスの方も、freeeなら請求書発行・経費精算・確定申告をまとめて自動化できます。<br>
    面倒な帳簿作業から解放されて、本業に集中しましょう。
  </p>
  <a class="esc-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">
    freeeを無料で試す &rarr;
  </a>
</div>

<script>
(function () {
  'use strict';

  /* ── モード定義 ── */
  const MODES = [
    {
      id: 'json',
      label: 'JSON',
      desc: 'RFC 8259準拠: \\ " / および制御文字をエスケープ',
      refs: [
        { seq: '\\\\', desc: 'バックスラッシュ' },
        { seq: '\\"', desc: 'ダブルクォート' },
        { seq: '\\/', desc: 'スラッシュ' },
        { seq: '\\n', desc: '改行' },
        { seq: '\\r', desc: 'キャリッジリターン' },
        { seq: '\\t', desc: 'タブ' },
        { seq: '\\b', desc: 'バックスペース' },
        { seq: '\\f', desc: 'フォームフィード' },
        { seq: '\\uXXXX', desc: 'ユニコード' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/"/g, '\\"')
          .replace(/\//g, '\\/')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\b/g, '\\b')
          .replace(/\f/g, '\\f')
          .replace(/[\x00-\x1f\x7f]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\"/g, '"')
          .replace(/\\\//g, '/')
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\b/g, '\b')
          .replace(/\\f/g, '\f')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'js',
      label: 'JS / TS',
      desc: 'JavaScriptおよびTypeScriptの文字列リテラル向けエスケープ',
      refs: [
        { seq: '\\\\', desc: 'バックスラッシュ' },
        { seq: "\\'", desc: 'シングルクォート' },
        { seq: '\\"', desc: 'ダブルクォート' },
        { seq: '\\`', desc: 'バッククォート' },
        { seq: '\\n', desc: '改行' },
        { seq: '\\t', desc: 'タブ' },
        { seq: '\\r', desc: 'キャリッジリターン' },
        { seq: '\\0', desc: 'ヌル文字' },
        { seq: '\\uXXXX', desc: 'ユニコード' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/'/g, "\\'")
          .replace(/"/g, '\\"')
          .replace(/`/g, '\\`')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\0/g, '\\0')
          .replace(/[\x00-\x1f\x7f]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\0/g, '\0')
          .replace(/\\'/g, "'")
          .replace(/\\"/g, '"')
          .replace(/\\`/g, '`')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'python',
      label: 'Python',
      desc: 'Pythonの文字列リテラル向けエスケープ',
      refs: [
        { seq: '\\\\', desc: 'バックスラッシュ' },
        { seq: "\\'", desc: 'シングルクォート' },
        { seq: '\\"', desc: 'ダブルクォート' },
        { seq: '\\n', desc: '改行' },
        { seq: '\\t', desc: 'タブ' },
        { seq: '\\r', desc: 'キャリッジリターン' },
        { seq: '\\0', desc: 'ヌル文字' },
        { seq: '\\xHH', desc: '16進エスケープ' },
        { seq: '\\uXXXX', desc: 'ユニコード' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/'/g, "\\'")
          .replace(/"/g, '\\"')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\0/g, '\\0')
          .replace(/[\x01-\x1f\x7f]/g, c => '\\x' + c.charCodeAt(0).toString(16).padStart(2, '0'));
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\x([0-9a-fA-F]{2})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\0/g, '\0')
          .replace(/\\'/g, "'")
          .replace(/\\"/g, '"')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'java',
      label: 'Java',
      desc: 'Javaの文字列リテラルエスケープ（Kotlin・Groovyにも対応）',
      refs: [
        { seq: '\\\\', desc: 'バックスラッシュ' },
        { seq: '\\"', desc: 'ダブルクォート' },
        { seq: "\\'", desc: 'シングルクォート' },
        { seq: '\\n', desc: '改行' },
        { seq: '\\t', desc: 'タブ' },
        { seq: '\\r', desc: 'キャリッジリターン' },
        { seq: '\\f', desc: 'フォームフィード' },
        { seq: '\\b', desc: 'バックスペース' },
        { seq: '\\uXXXX', desc: 'ユニコード' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/"/g, '\\"')
          .replace(/'/g, "\\'")
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\f/g, '\\f')
          .replace(/\b/g, '\\b')
          .replace(/[^\x20-\x7e]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\f/g, '\f')
          .replace(/\\b/g, '\b')
          .replace(/\\"/g, '"')
          .replace(/\\'/g, "'")
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'csharp',
      label: 'C#',
      desc: 'C#の通常文字列リテラルエスケープ',
      refs: [
        { seq: '\\\\', desc: 'バックスラッシュ' },
        { seq: '\\"', desc: 'ダブルクォート' },
        { seq: '\\n', desc: '改行' },
        { seq: '\\t', desc: 'タブ' },
        { seq: '\\r', desc: 'キャリッジリターン' },
        { seq: '\\0', desc: 'ヌル文字' },
        { seq: '\\a', desc: 'アラート/ベル' },
        { seq: '\\uXXXX', desc: 'ユニコード' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/"/g, '\\"')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\0/g, '\\0')
          .replace(/\x07/g, '\\a')
          .replace(/[^\x20-\x7e]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\0/g, '\0')
          .replace(/\\a/g, '\x07')
          .replace(/\\"/g, '"')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'sql',
      label: 'SQL',
      desc: 'シングルクォートの二重化（ANSI SQL標準）',
      refs: [
        { seq: "''", desc: 'シングルクォート' },
        { seq: '\\n', desc: '改行（MySQL）' },
        { seq: '\\t', desc: 'タブ（MySQL）' },
        { seq: '\\\\', desc: 'バックスラッシュ（MySQL）' },
      ],
      escape(s) {
        return s.replace(/'/g, "''");
      },
      unescape(s) {
        return s.replace(/''/g, "'");
      },
    },
    {
      id: 'html',
      label: 'HTML',
      desc: 'HTMLに安全に埋め込むための名前付きエンティティ',
      refs: [
        { seq: '&amp;', desc: '& アンパサンド' },
        { seq: '&lt;', desc: '< 小なり' },
        { seq: '&gt;', desc: '> 大なり' },
        { seq: '&quot;', desc: '" ダブルクォート' },
        { seq: '&#39;', desc: "' シングルクォート" },
        { seq: '&nbsp;', desc: '非改行スペース' },
      ],
      escape(s) {
        return s
          .replace(/&/g, '&amp;')
          .replace(/</g, '&lt;')
          .replace(/>/g, '&gt;')
          .replace(/"/g, '&quot;')
          .replace(/'/g, '&#39;');
      },
      unescape(s) {
        return s
          .replace(/&quot;/g, '"')
          .replace(/&#39;/g, "'")
          .replace(/&apos;/g, "'")
          .replace(/&lt;/g, '<')
          .replace(/&gt;/g, '>')
          .replace(/&nbsp;/g, '\u00a0')
          .replace(/&amp;/g, '&');
      },
    },
    {
      id: 'xml',
      label: 'XML',
      desc: 'XML仕様の5つの定義済みエンティティ',
      refs: [
        { seq: '&amp;', desc: '& アンパサンド' },
        { seq: '&lt;', desc: '< 小なり' },
        { seq: '&gt;', desc: '> 大なり' },
        { seq: '&quot;', desc: '" ダブルクォート' },
        { seq: '&apos;', desc: "' アポストロフィ" },
      ],
      escape(s) {
        return s
          .replace(/&/g, '&amp;')
          .replace(/</g, '&lt;')
          .replace(/>/g, '&gt;')
          .replace(/"/g, '&quot;')
          .replace(/'/g, '&apos;');
      },
      unescape(s) {
        return s
          .replace(/&quot;/g, '"')
          .replace(/&apos;/g, "'")
          .replace(/&lt;/g, '<')
          .replace(/&gt;/g, '>')
          .replace(/&amp;/g, '&');
      },
    },
    {
      id: 'csv',
      label: 'CSV',
      desc: 'RFC 4180準拠のCSVフィールドクォーティング',
      refs: [
        { seq: '""', desc: '埋め込みダブルクォート' },
        { seq: '"field"', desc: 'フィールドのクォート括り' },
      ],
      escape(s) {
        if (/[",\r\n]/.test(s)) {
          return '"' + s.replace(/"/g, '""') + '"';
        }
        return s;
      },
      unescape(s) {
        const t = s.trim();
        if (t.startsWith('"') && t.endsWith('"')) {
          return t.slice(1, -1).replace(/""/g, '"');
        }
        return s;
      },
    },
    {
      id: 'regex',
      label: '正規表現',
      desc: '正規表現のメタ文字をすべてエスケープしてリテラルパターンとして使用可能にする',
      refs: [
        { seq: '\\.', desc: '任意の文字（ドット）' },
        { seq: '\\*', desc: '量指定子 *' },
        { seq: '\\+', desc: '量指定子 +' },
        { seq: '\\?', desc: '量指定子 ?' },
        { seq: '\\^', desc: '先頭アンカー' },
        { seq: '\\$', desc: '末尾アンカー' },
        { seq: '\\(\\)', desc: 'グループ' },
        { seq: '\\[\\]', desc: '文字クラス' },
        { seq: '\\{\\}', desc: '量指定子ブレース' },
        { seq: '\\|', desc: '選択' },
      ],
      escape(s) {
        return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
      },
      unescape(s) {
        return s.replace(/\\([.*+?^${}()|[\]\\])/g, '$1');
      },
    },
  ];

  /* ── 状態 ── */
  let activeMode = MODES[0];

  /* ── DOM参照 ── */
  const modeRow   = document.getElementById('escModeRow');
  const modeDesc  = document.getElementById('escModeDesc');
  const input     = document.getElementById('escInput');
  const output    = document.getElementById('escOutput');
  const bulkCheck = document.getElementById('escBulkMode');
  const statusEl  = document.getElementById('escStatus');
  const refGrid   = document.getElementById('escRefGrid');

  /* ── モードボタン生成 ── */
  MODES.forEach(mode => {
    const btn = document.createElement('button');
    btn.className = 'esc-mode-btn' + (mode === activeMode ? ' active' : '');
    btn.textContent = mode.label;
    btn.addEventListener('click', () => {
      activeMode = mode;
      document.querySelectorAll('#esc-app .esc-mode-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      modeDesc.textContent = mode.desc;
      renderRef();
    });
    modeRow.appendChild(btn);
  });
  modeDesc.textContent = activeMode.desc;

  /* ── 参照テーブル描画 ── */
  function renderRef() {
    refGrid.innerHTML = '';
    activeMode.refs.forEach(r => {
      const div = document.createElement('div');
      div.className = 'esc-ref-item';
      div.innerHTML = '<code>' + r.seq + '</code><span>' + r.desc + '</span>';
      refGrid.appendChild(div);
    });
  }
  renderRef();

  /* ── 処理 ── */
  function process(fn) {
    const text = input.value;
    if (!text) { showStatus('テキストを入力してください。', true); return; }
    try {
      if (bulkCheck.checked) {
        output.value = text.split('\n').map(line => fn(line)).join('\n');
      } else {
        output.value = fn(text);
      }
      showStatus('完了しました。');
    } catch (e) {
      showStatus('エラー: ' + e.message, true);
    }
  }

  document.getElementById('escEscapeBtn').addEventListener('click', () => process(s => activeMode.escape(s)));
  document.getElementById('escUnescapeBtn').addEventListener('click', () => process(s => activeMode.unescape(s)));

  /* ── コピー ── */
  document.getElementById('escCopyBtn').addEventListener('click', () => {
    const text = output.value;
    if (!text) { showStatus('コピーする内容がありません。', true); return; }
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(() => showStatus('クリップボードにコピーしました!')).catch(() => fallbackCopy(text));
    } else {
      fallbackCopy(text);
    }
  });

  function fallbackCopy(text) {
    output.select();
    document.execCommand('copy');
    showStatus('クリップボードにコピーしました!');
  }

  /* ── クリア ── */
  document.getElementById('escClearBtn').addEventListener('click', () => {
    input.value = '';
    output.value = '';
    showStatus('クリアしました。');
  });

  /* ── ステータス表示 ── */
  let statusTimer;
  function showStatus(msg, isError) {
    statusEl.textContent = msg;
    statusEl.className = 'esc-status' + (isError ? ' error' : '');
    clearTimeout(statusTimer);
    statusTimer = setTimeout(() => { statusEl.textContent = ''; }, 3000);
  }
})();
</script>

</div>
