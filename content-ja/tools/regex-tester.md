---
title: "正規表現テスター"
date: 2025-05-16
description: "無料の正規表現テスター。リアルタイムマッチハイライト、キャプチャグループ、フラグ設定でRegexを検証。登録不要、ブラウザで完結。"
categories: ["無料ツール"]
slug: "regex-tester"
ShowToc: false
cover:
  image: "/images/covers/regex-tester-ja.png"
  alt: "正規表現テスター"
---

正規表現をブラウザ上でリアルタイムに検証。パターンを入力してフラグを選ぶだけで、マッチ箇所がハイライト表示されます。登録不要、外部ライブラリなし。

<div id="rx-app">
<style>
  #rx-app *,
  #rx-app *::before,
  #rx-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

  #rx-app {
    font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Meiryo", "Segoe UI", sans-serif;
    font-size: 14px;
    color: #1e293b;
    max-width: 860px;
    margin: 0 auto;
  }

  #rx-app .rx-card {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 10px;
    padding: 18px 20px;
    margin-bottom: 14px;
  }
  #rx-app .rx-card-title {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: .06em;
    text-transform: uppercase;
    color: #64748b;
    margin-bottom: 10px;
  }

  /* Pattern row */
  #rx-app .rx-pattern-row {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
  }
  #rx-app .rx-slash {
    font-size: 22px;
    color: #94a3b8;
    line-height: 1;
    flex-shrink: 0;
    font-family: "Fira Mono", "Consolas", monospace;
  }
  #rx-app #rx-pattern {
    flex: 1;
    min-width: 180px;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 15px;
    padding: 9px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 7px;
    outline: none;
    transition: border-color .15s;
    background: #f8fafc;
    color: #1e293b;
  }
  #rx-app #rx-pattern:focus { border-color: #6366f1; background: #fff; }
  #rx-app #rx-pattern.rx-invalid { border-color: #ef4444; background: #fff5f5; }

  /* Flag toggles */
  #rx-app .rx-flags { display: flex; gap: 5px; flex-shrink: 0; flex-wrap: wrap; }
  #rx-app .rx-flag {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 30px;
    height: 30px;
    border-radius: 6px;
    border: 2px solid #e2e8f0;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
    color: #64748b;
    background: #f8fafc;
    transition: all .15s;
    user-select: none;
  }
  #rx-app .rx-flag:hover { border-color: #6366f1; color: #6366f1; }
  #rx-app .rx-flag.on { background: #6366f1; border-color: #6366f1; color: #fff; }

  /* Error message */
  #rx-app .rx-error-msg {
    display: none;
    margin-top: 8px;
    padding: 8px 12px;
    background: #fef2f2;
    border: 1px solid #fca5a5;
    border-radius: 6px;
    color: #b91c1c;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 12px;
  }

  /* Quick-insert */
  #rx-app .rx-quick-wrap { display: flex; flex-wrap: wrap; gap: 6px; }
  #rx-app .rx-qbtn {
    padding: 5px 11px;
    font-size: 12px;
    font-weight: 600;
    border: 1.5px solid #c7d2fe;
    border-radius: 20px;
    background: #eef2ff;
    color: #4338ca;
    cursor: pointer;
    transition: all .15s;
  }
  #rx-app .rx-qbtn:hover { background: #6366f1; border-color: #6366f1; color: #fff; }

  /* Test string textarea */
  #rx-app #rx-test {
    width: 100%;
    min-height: 110px;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    line-height: 1.65;
    padding: 10px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 7px;
    outline: none;
    resize: vertical;
    background: #f8fafc;
    color: #1e293b;
    transition: border-color .15s;
  }
  #rx-app #rx-test:focus { border-color: #6366f1; background: #fff; }

  /* Highlight display */
  #rx-app #rx-hl {
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    line-height: 1.7;
    white-space: pre-wrap;
    word-break: break-all;
    min-height: 80px;
    padding: 10px 12px;
    border-radius: 7px;
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    color: #1e293b;
  }
  #rx-app mark.rx-m0 {
    background: #fde68a;
    border-radius: 3px;
    outline: 2px solid #f59e0b;
    outline-offset: 0;
    color: #1e293b;
  }
  #rx-app mark.rx-m1 {
    background: #a5f3fc;
    border-radius: 3px;
    outline: 2px solid #0ea5e9;
    outline-offset: 0;
    color: #1e293b;
  }

  /* Stats bar */
  #rx-app .rx-stats { display: flex; gap: 20px; flex-wrap: wrap; margin-top: 10px; }
  #rx-app .rx-stat { font-size: 12px; color: #64748b; }
  #rx-app .rx-stat strong { color: #1e293b; }

  /* Tabs */
  #rx-app .rx-tabs {
    display: flex;
    border-bottom: 2px solid #e2e8f0;
    margin-bottom: 14px;
  }
  #rx-app .rx-tab {
    padding: 7px 16px;
    font-size: 13px;
    font-weight: 600;
    color: #64748b;
    border: none;
    background: none;
    cursor: pointer;
    border-bottom: 2px solid transparent;
    margin-bottom: -2px;
    transition: all .15s;
  }
  #rx-app .rx-tab:hover { color: #6366f1; }
  #rx-app .rx-tab.on { color: #6366f1; border-bottom-color: #6366f1; }

  /* Match list */
  #rx-app .rx-match-list { list-style: none; max-height: 280px; overflow-y: auto; }
  #rx-app .rx-match-item {
    display: grid;
    grid-template-columns: 46px 1fr;
    gap: 8px;
    align-items: start;
    padding: 8px 0;
    border-bottom: 1px solid #f1f5f9;
  }
  #rx-app .rx-match-item:last-child { border-bottom: none; }
  #rx-app .rx-mi-num {
    font-size: 11px;
    font-weight: 700;
    color: #6366f1;
    background: #eef2ff;
    border-radius: 4px;
    padding: 2px 5px;
    text-align: center;
  }
  #rx-app .rx-mi-val {
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    background: #fde68a;
    border-radius: 3px;
    padding: 1px 5px;
    word-break: break-all;
    color: #1e293b;
  }
  #rx-app .rx-mi-pos { font-size: 11px; color: #94a3b8; margin-top: 3px; }
  #rx-app .rx-mi-groups { display: flex; flex-wrap: wrap; gap: 4px; margin-top: 5px; }
  #rx-app .rx-group-chip {
    font-size: 11px;
    font-family: "Fira Mono", "Consolas", monospace;
    background: #e0f2fe;
    color: #0369a1;
    border-radius: 3px;
    padding: 1px 6px;
  }
  #rx-app .rx-empty { text-align: center; color: #94a3b8; font-size: 13px; padding: 22px 0; }

  /* Replace panel */
  #rx-app .rx-replace-row {
    display: flex;
    gap: 8px;
    align-items: center;
    flex-wrap: wrap;
  }
  #rx-app #rx-repl-in {
    flex: 1;
    min-width: 180px;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    padding: 8px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 7px;
    background: #f8fafc;
    outline: none;
    transition: border-color .15s;
    color: #1e293b;
  }
  #rx-app #rx-repl-in:focus { border-color: #6366f1; background: #fff; }
  #rx-app #rx-repl-out {
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    line-height: 1.7;
    white-space: pre-wrap;
    word-break: break-all;
    padding: 10px 12px;
    border-radius: 7px;
    background: #f0fdf4;
    border: 1px solid #bbf7d0;
    min-height: 50px;
    margin-top: 10px;
    color: #1e293b;
  }
  #rx-app .rx-copy-btn {
    padding: 6px 13px;
    font-size: 12px;
    font-weight: 600;
    border: 1.5px solid #e2e8f0;
    border-radius: 6px;
    background: #f8fafc;
    color: #475569;
    cursor: pointer;
    transition: all .15s;
    flex-shrink: 0;
  }
  #rx-app .rx-copy-btn:hover { border-color: #6366f1; color: #6366f1; }

  /* Explain panel */
  #rx-app .rx-explain-list { list-style: none; }
  #rx-app .rx-explain-item {
    display: flex;
    gap: 12px;
    padding: 5px 0;
    border-bottom: 1px dashed #f1f5f9;
    font-size: 12px;
  }
  #rx-app .rx-explain-item:last-child { border: none; }
  #rx-app .rx-ex-tok {
    font-family: "Fira Mono", "Consolas", monospace;
    font-weight: 700;
    color: #6366f1;
    min-width: 96px;
    flex-shrink: 0;
  }
  #rx-app .rx-ex-desc { color: #475569; line-height: 1.5; }

  /* freee CTA */
  #rx-app .rx-freee-cta {
    margin-top: 28px;
    padding: 18px 20px;
    background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
    border: 1.5px solid #bae6fd;
    border-radius: 10px;
  }

  @media (max-width: 600px) {
    #rx-app .rx-pattern-row { flex-direction: column; align-items: stretch; }
    #rx-app .rx-slash { display: none; }
    #rx-app #rx-pattern { font-size: 14px; }
  }
</style>

<!-- パターン入力 -->
<div class="rx-card">
  <div class="rx-card-title">正規表現パターン</div>
  <div class="rx-pattern-row">
    <span class="rx-slash">/</span>
    <input id="rx-pattern" type="text" placeholder="パターンを入力… 例: \d{3}-\d{4}" autocomplete="off" spellcheck="false" />
    <span class="rx-slash">/</span>
    <div class="rx-flags">
      <span class="rx-flag on"  data-flag="g" title="g — 全マッチを検索">g</span>
      <span class="rx-flag"     data-flag="i" title="i — 大文字・小文字を無視">i</span>
      <span class="rx-flag"     data-flag="m" title="m — 複数行モード">m</span>
      <span class="rx-flag"     data-flag="s" title="s — ドットが改行にもマッチ">s</span>
      <span class="rx-flag"     data-flag="u" title="u — Unicodeモード">u</span>
    </div>
  </div>
  <div class="rx-error-msg" id="rx-err"></div>
</div>

<!-- よく使うパターン -->
<div class="rx-card">
  <div class="rx-card-title">クイック挿入 — よく使うパターン</div>
  <div class="rx-quick-wrap">
    <button class="rx-qbtn" data-p="[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}">メールアドレス</button>
    <button class="rx-qbtn" data-p="https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&\/=]*)">URL</button>
    <button class="rx-qbtn" data-p="0[789]0[\-\s]?\d{4}[\-\s]?\d{4}">携帯電話番号</button>
    <button class="rx-qbtn" data-p="\d{3}-\d{4}">郵便番号</button>
    <button class="rx-qbtn" data-p="\b(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\b">IPv4アドレス</button>
    <button class="rx-qbtn" data-p="\d{4}[-\/]\d{2}[-\/]\d{2}">日付 YYYY-MM-DD</button>
    <button class="rx-qbtn" data-p="[\u3041-\u3096]+">ひらがな</button>
    <button class="rx-qbtn" data-p="[\u30A1-\u30FC]+">カタカナ</button>
    <button class="rx-qbtn" data-p="[\u4E00-\u9FFF]+">漢字</button>
    <button class="rx-qbtn" data-p="#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})\b">カラーコード</button>
  </div>
</div>

<!-- テスト文字列 -->
<div class="rx-card">
  <div class="rx-card-title">テスト文字列</div>
  <textarea id="rx-test" spellcheck="false" placeholder="テストしたい文字列を入力してください…">田中さんのメールはtanaka@example.co.jpです。
電話番号: 090-1234-5678
郵便番号: 〒100-0001
ウェブサイト: https://www.example.com
IPアドレス: 192.168.1.1
日付: 2025-05-16</textarea>
</div>

<!-- マッチハイライト -->
<div class="rx-card">
  <div class="rx-card-title">マッチハイライト</div>
  <div id="rx-hl"></div>
  <div class="rx-stats">
    <span class="rx-stat">マッチ数: <strong id="rx-count">—</strong></span>
    <span class="rx-stat">実行時間: <strong id="rx-time">—</strong></span>
  </div>
</div>

<!-- 下部パネル -->
<div class="rx-card">
  <div class="rx-tabs">
    <button class="rx-tab on"  data-tab="matches">マッチ詳細</button>
    <button class="rx-tab"     data-tab="replace">置換モード</button>
    <button class="rx-tab"     data-tab="explain">パターン解説</button>
  </div>

  <!-- マッチ詳細 -->
  <div id="rx-panel-matches">
    <ul class="rx-match-list" id="rx-mlist">
      <li class="rx-empty">パターンを入力するとマッチ結果が表示されます。</li>
    </ul>
  </div>

  <!-- 置換モード -->
  <div id="rx-panel-replace" style="display:none">
    <div class="rx-replace-row">
      <label style="font-size:12px;color:#64748b;font-weight:600;white-space:nowrap;">置換文字列:</label>
      <input id="rx-repl-in" type="text" placeholder="置換後の文字列（$1, $2 でグループ参照）…" spellcheck="false" />
      <button class="rx-copy-btn" id="rx-copy-repl">結果をコピー</button>
    </div>
    <div id="rx-repl-out"></div>
  </div>

  <!-- パターン解説 -->
  <div id="rx-panel-explain" style="display:none">
    <ul class="rx-explain-list" id="rx-exlist">
      <li class="rx-empty">パターンを入力するとトークンごとの解説が表示されます。</li>
    </ul>
  </div>
</div>

<!-- freee CTA -->
<div class="rx-freee-cta">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">開発業務の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、開発ツール・クラウドサービスの経費精算もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function () {
  'use strict';

  var flagState = { g: true, i: false, m: false, s: false, u: false };
  var activeTab = 'matches';

  var elPat    = document.getElementById('rx-pattern');
  var elTest   = document.getElementById('rx-test');
  var elErr    = document.getElementById('rx-err');
  var elHl     = document.getElementById('rx-hl');
  var elCount  = document.getElementById('rx-count');
  var elTime   = document.getElementById('rx-time');
  var elMlist  = document.getElementById('rx-mlist');
  var elReplIn = document.getElementById('rx-repl-in');
  var elReplOut= document.getElementById('rx-repl-out');
  var elExlist = document.getElementById('rx-exlist');

  /* フラグトグル */
  document.querySelectorAll('#rx-app .rx-flag').forEach(function (el) {
    el.addEventListener('click', function () {
      var f = el.dataset.flag;
      flagState[f] = !flagState[f];
      el.classList.toggle('on', flagState[f]);
      run();
    });
  });

  /* タブ切替 */
  document.querySelectorAll('#rx-app .rx-tab').forEach(function (el) {
    el.addEventListener('click', function () {
      activeTab = el.dataset.tab;
      document.querySelectorAll('#rx-app .rx-tab').forEach(function (t) {
        t.classList.toggle('on', t === el);
      });
      document.getElementById('rx-panel-matches').style.display = activeTab === 'matches' ? '' : 'none';
      document.getElementById('rx-panel-replace').style.display = activeTab === 'replace'  ? '' : 'none';
      document.getElementById('rx-panel-explain').style.display = activeTab === 'explain'  ? '' : 'none';
    });
  });

  /* クイック挿入 */
  document.querySelectorAll('#rx-app .rx-qbtn').forEach(function (btn) {
    btn.addEventListener('click', function () {
      elPat.value = btn.dataset.p;
      run();
      elPat.focus();
    });
  });

  /* 結果コピー */
  document.getElementById('rx-copy-repl').addEventListener('click', function () {
    var txt = elReplOut.textContent;
    if (!txt) return;
    var btn = this;
    navigator.clipboard.writeText(txt).catch(function () {
      var ta = document.createElement('textarea');
      ta.value = txt;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
    });
    btn.textContent = 'コピーしました!';
    setTimeout(function () { btn.textContent = '結果をコピー'; }, 1600);
  });

  elPat.addEventListener('input', run);
  elTest.addEventListener('input', run);
  elReplIn.addEventListener('input', run);

  /* ═══════════ メイン実行 ═══════════ */
  function run() {
    var rawPat  = elPat.value;
    var testStr = elTest.value;
    var fStr    = buildFlagStr();

    elErr.style.display = 'none';
    elPat.classList.remove('rx-invalid');

    if (!rawPat) {
      elHl.textContent = testStr;
      elCount.textContent = '—';
      elTime.textContent  = '—';
      setEmpty('パターンを入力するとマッチ結果が表示されます。');
      elReplOut.textContent = '';
      setExplain('');
      return;
    }

    var re;
    try { re = new RegExp(rawPat, fStr); }
    catch (e) {
      elPat.classList.add('rx-invalid');
      elErr.textContent = 'エラー: ' + e.message;
      elErr.style.display = 'block';
      elHl.textContent = testStr;
      elCount.textContent = 'エラー';
      elTime.textContent  = '—';
      setEmpty('正規表現が無効です: ' + e.message);
      elReplOut.textContent = '';
      return;
    }

    var t0 = performance.now();
    var matches = [];
    if (flagState.g) {
      var reG = new RegExp(rawPat, fStr);
      var m;
      while ((m = reG.exec(testStr)) !== null) {
        matches.push({ val: m[0], idx: m.index, groups: Array.from(m).slice(1) });
        if (m[0].length === 0) reG.lastIndex++;
        if (matches.length >= 1000) break;
      }
    } else {
      var m1 = re.exec(testStr);
      if (m1) matches.push({ val: m1[0], idx: m1.index, groups: Array.from(m1).slice(1) });
    }
    var t1 = performance.now();

    elCount.textContent = matches.length + ' 件';
    elTime.textContent  = (t1 - t0).toFixed(3) + ' ms';

    renderHighlight(testStr, matches);
    renderMatchList(matches);
    renderReplace(testStr, re);
    setExplain(rawPat);
  }

  function buildFlagStr() {
    return Object.keys(flagState).filter(function (f) { return flagState[f]; }).join('');
  }

  function esc(s) {
    return String(s)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  function renderHighlight(str, matches) {
    if (!matches.length) { elHl.textContent = str; return; }
    var html = '', cur = 0;
    matches.forEach(function (m, i) {
      if (m.idx > cur) html += esc(str.slice(cur, m.idx));
      html += '<mark class="rx-m' + (i % 2) + '">' + esc(m.val) + '</mark>';
      cur = m.idx + m.val.length;
    });
    html += esc(str.slice(cur));
    elHl.innerHTML = html;
  }

  function renderMatchList(matches) {
    if (!matches.length) { setEmpty('マッチする文字列が見つかりませんでした。'); return; }
    var html = '';
    matches.forEach(function (m, i) {
      html += '<li class="rx-match-item">';
      html += '<span class="rx-mi-num">#' + (i + 1) + '</span>';
      html += '<div>';
      html += '<div class="rx-mi-val">' + esc(m.val) + '</div>';
      html += '<div class="rx-mi-pos">インデックス ' + m.idx + ' → ' + (m.idx + m.val.length) + '</div>';
      if (m.groups.length) {
        html += '<div class="rx-mi-groups">';
        m.groups.forEach(function (g, gi) {
          html += '<span class="rx-group-chip">$' + (gi + 1) + ': ' + esc(g === undefined ? '未定義' : g) + '</span>';
        });
        html += '</div>';
      }
      html += '</div></li>';
    });
    elMlist.innerHTML = html;
  }

  function setEmpty(msg) {
    elMlist.innerHTML = '<li class="rx-empty">' + esc(msg) + '</li>';
  }

  function renderReplace(str, re) {
    var repl = elReplIn.value;
    if (!repl && repl !== '0') { elReplOut.textContent = ''; return; }
    try { elReplOut.textContent = str.replace(re, repl); }
    catch (e) { elReplOut.textContent = ''; }
  }

  /* ═══════════ パターン解説 ═══════════ */
  var TOKENS = [
    [/^\^/,                       '行頭（または文字列先頭）のアンカー'],
    [/^\$/,                       '行末（または文字列末尾）のアンカー'],
    [/^\(\?<=/,                   '肯定後読みアサーション'],
    [/^\(\?<!/,                   '否定後読みアサーション'],
    [/^\(\?=/,                    '肯定先読みアサーション'],
    [/^\(\?!/,                    '否定先読みアサーション'],
    [/^\(\?:/,                    '非キャプチャグループ'],
    [/^\(\?<[a-zA-Z_]\w*>/,      '名前付きキャプチャグループ'],
    [/^\(/,                       'キャプチャグループの開始'],
    [/^\)/,                       'グループの終了'],
    [/^\[\^/,                     '否定文字クラス — 列挙した文字以外にマッチ'],
    [/^\[/,                       '文字クラス — 列挙した文字のいずれか1文字にマッチ'],
    [/^\]/,                       '文字クラスの終了'],
    [/^\\d/,                      'ショートハンド: 数字 [0-9]'],
    [/^\\D/,                      'ショートハンド: 数字以外'],
    [/^\\w/,                      'ショートハンド: 単語文字 [a-zA-Z0-9_]'],
    [/^\\W/,                      'ショートハンド: 単語文字以外'],
    [/^\\s/,                      'ショートハンド: 空白文字（スペース・タブ・改行など）'],
    [/^\\S/,                      'ショートハンド: 空白文字以外'],
    [/^\\b/,                      '単語境界アサーション'],
    [/^\\B/,                      '非単語境界アサーション'],
    [/^\\n/,                      '改行文字（リテラル）'],
    [/^\\t/,                      'タブ文字（リテラル）'],
    [/^\\r/,                      'キャリッジリターン（リテラル）'],
    [/^\\\\/,                     'バックスラッシュ（リテラル）'],
    [/^\\u[0-9a-fA-F]{4}/,       'Unicodeコードポイントエスケープ'],
    [/^\\x[0-9a-fA-F]{2}/,       '16進数文字エスケープ'],
    [/^\\([0-9]+)/,               'キャプチャグループN への後方参照'],
    [/^\\./,                      'エスケープされた特殊文字 — リテラルとして扱う'],
    [/^\{[0-9]+,[0-9]+\}\?/,     '非貪欲量指定子: {n}〜{m}回（できるだけ少なく）'],
    [/^\{[0-9]+,\}\?/,           '非貪欲量指定子: {n}回以上（できるだけ少なく）'],
    [/^\{[0-9]+\}\?/,            '非貪欲量指定子: ちょうど{n}回'],
    [/^\{[0-9]+,[0-9]+\}/,       '貪欲量指定子: {n}〜{m}回'],
    [/^\{[0-9]+,\}/,             '貪欲量指定子: {n}回以上'],
    [/^\{[0-9]+\}/,              '量指定子: ちょうど{n}回'],
    [/^\*\?/,                    '非貪欲量指定子: 0回以上（できるだけ少なく）'],
    [/^\+\?/,                    '非貪欲量指定子: 1回以上（できるだけ少なく）'],
    [/^\?\?/,                    '非貪欲量指定子: 0または1回（0を優先）'],
    [/^\*/,                      '貪欲量指定子: 0回以上'],
    [/^\+/,                      '貪欲量指定子: 1回以上'],
    [/^\?/,                      '量指定子: 0または1回（省略可能）'],
    [/^\|/,                      '選択（OR）— 左右どちらかにマッチ'],
    [/^\./,                      'ワイルドカード — 改行以外の任意の1文字（s フラグで改行にもマッチ）'],
    [/^./,                       'リテラル文字'],
  ];

  function tokenize(pat) {
    var toks = [], rem = pat, limit = 300;
    while (rem.length && limit-- > 0) {
      var hit = false;
      for (var i = 0; i < TOKENS.length; i++) {
        var m = rem.match(TOKENS[i][0]);
        if (m) {
          toks.push({ t: m[0], d: TOKENS[i][1] });
          rem = rem.slice(m[0].length);
          hit = true;
          break;
        }
      }
      if (!hit) rem = rem.slice(1);
    }
    return toks;
  }

  function setExplain(pat) {
    if (!pat) {
      elExlist.innerHTML = '<li class="rx-empty">パターンを入力するとトークンごとの解説が表示されます。</li>';
      return;
    }
    var toks = tokenize(pat);
    if (!toks.length) { elExlist.innerHTML = '<li class="rx-empty">解説できるトークンがありません。</li>'; return; }
    var html = '';
    toks.forEach(function (tk) {
      html += '<li class="rx-explain-item"><span class="rx-ex-tok">' + esc(tk.t) + '</span><span class="rx-ex-desc">' + esc(tk.d) + '</span></li>';
    });
    elExlist.innerHTML = html;
  }

  run();
})();
</script>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

> クイックリファレンス → [正規表現チートシート](/ja/tools/regex-cheatsheet/)
> 文字列をエスケープ → [文字列エスケープツール](/ja/tools/string-escape-tool/)
