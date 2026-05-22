---
title: "正規表現チートシート — インタラクティブリファレンス"
date: 2025-07-17
description: "ライブテスト付き正規表現チートシート。文字クラス・量指定子・グループ・先読み・よく使うパターン。各例を即座にテスト。"
categories: ["無料ツール"]
tags: ["開発ツール", "プログラミング", "無料ツール"]
slug: "regex-cheatsheet"
ShowToc: false
aliases:
  - "/ja/tools/regex-cheatsheet/"
  - "/ja/tools/regex-cheatsheet/"
cover:
  image: "/images/covers/regex-cheatsheet-ja.png"
  alt: "正規表現チートシート"
---

<div id="rxcs-app">

<style>
#rxcs-app {
font-family: 'Segoe UI', 'Hiragino Sans', 'Meiryo', system-ui, sans-serif;
background: #1a1a2e;
color: #e0e0e0;
padding: 24px;
border-radius: 12px;
max-width: 960px;
margin: 0 auto;
box-sizing: border-box;
}

#rxcs-app * {
box-sizing: border-box;
}

#rxcs-app h2 {
color: #00ff88;
margin: 0 0 6px 0;
font-size: 1.3rem;
letter-spacing: 0.04em;
}

#rxcs-app h3 {
color: #00cc70;
font-size: 0.9rem;
margin: 22px 0 10px 0;
text-transform: none;
letter-spacing: 0.05em;
border-bottom: 1px solid #2a2a4a;
padding-bottom: 6px;
}

#rxcs-app .rxcs-subtitle {
color: #606080;
font-size: 0.82rem;
margin-bottom: 20px;
}

/* ── テストエリア ── */
#rxcs-app .rxcs-tester {
background: #0d0d1a;
border: 1px solid #2a2a4a;
border-radius: 10px;
padding: 18px;
margin-bottom: 24px;
}

#rxcs-app .rxcs-tester-title {
color: #a0a0c0;
font-size: 0.76rem;
text-transform: uppercase;
letter-spacing: 0.9px;
font-weight: 700;
margin-bottom: 12px;
}

#rxcs-app .rxcs-row {
display: flex;
gap: 8px;
align-items: center;
flex-wrap: wrap;
margin-bottom: 10px;
}

#rxcs-app .rxcs-pattern-wrap {
display: flex;
align-items: center;
background: #16162a;
border: 1px solid #2a2a4a;
border-radius: 7px;
flex: 1;
min-width: 180px;
transition: border-color 0.2s;
}

#rxcs-app .rxcs-pattern-wrap:focus-within {
border-color: #00ff88;
}

#rxcs-app .rxcs-slash {
color: #00ff88;
font-size: 1.2rem;
padding: 0 7px;
font-family: monospace;
user-select: none;
}

#rxcs-app .rxcs-pattern-input {
background: transparent;
border: none;
outline: none;
color: #00ff88;
font-family: 'Courier New', monospace;
font-size: 0.95rem;
flex: 1;
padding: 9px 2px;
width: 0;
}

#rxcs-app .rxcs-flags-wrap {
display: flex;
gap: 10px;
flex-wrap: wrap;
align-items: center;
}

#rxcs-app .rxcs-flag-label {
display: flex;
align-items: center;
gap: 3px;
cursor: pointer;
font-size: 0.8rem;
color: #9090b0;
user-select: none;
}

#rxcs-app .rxcs-flag-label input[type="checkbox"] {
accent-color: #00ff88;
width: 13px;
height: 13px;
cursor: pointer;
}

#rxcs-app .rxcs-flag-key {
font-family: monospace;
color: #00ff88;
font-weight: 700;
}

#rxcs-app .rxcs-teststr {
width: 100%;
background: #16162a;
border: 1px solid #2a2a4a;
color: #e0e0e0;
padding: 10px 12px;
border-radius: 7px;
font-family: 'Courier New', monospace;
font-size: 0.88rem;
resize: vertical;
outline: none;
transition: border-color 0.2s;
line-height: 1.55;
}

#rxcs-app .rxcs-teststr:focus {
border-color: #00ff88;
}

#rxcs-app .rxcs-stats {
display: flex;
align-items: center;
gap: 10px;
margin: 8px 0;
flex-wrap: wrap;
}

#rxcs-app .rxcs-badge {
background: #00ff8820;
border: 1px solid #00ff8840;
color: #00ff88;
padding: 3px 11px;
border-radius: 20px;
font-size: 0.78rem;
font-weight: 700;
}

#rxcs-app .rxcs-badge.no-match {
background: #ff444420;
border-color: #ff444440;
color: #ff8888;
}

#rxcs-app .rxcs-badge.error {
background: #ff220020;
border-color: #ff220040;
color: #ff6666;
}

#rxcs-app .rxcs-display {
background: #16162a;
border: 1px solid #2a2a4a;
border-radius: 7px;
padding: 10px 12px;
font-family: 'Courier New', monospace;
font-size: 0.88rem;
line-height: 1.6;
min-height: 60px;
white-space: pre-wrap;
word-break: break-all;
color: #c0c0e0;
margin-top: 6px;
}

#rxcs-app .rxcs-hl {
background: #00ff8840;
border-bottom: 2px solid #00ff88;
border-radius: 2px;
color: #00ff88;
}

#rxcs-app .rxcs-hl-alt {
background: #ff88ff30;
border-bottom: 2px solid #ff88ff;
border-radius: 2px;
color: #ff88ff;
}

/* ── 検索バー ── */
#rxcs-app .rxcs-search-wrap {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 18px;
}

#rxcs-app .rxcs-search {
flex: 1;
background: #0d0d1a;
border: 1px solid #2a2a4a;
color: #e0e0e0;
padding: 9px 13px;
border-radius: 7px;
font-size: 0.88rem;
outline: none;
transition: border-color 0.2s;
font-family: inherit;
}

#rxcs-app .rxcs-search:focus {
border-color: #00ff88;
}

#rxcs-app .rxcs-search::placeholder {
color: #404060;
}

#rxcs-app .rxcs-search-clear {
background: #0d0d1a;
border: 1px solid #2a2a4a;
color: #808090;
padding: 8px 13px;
border-radius: 7px;
cursor: pointer;
font-size: 0.82rem;
transition: all 0.2s;
font-family: inherit;
}

#rxcs-app .rxcs-search-clear:hover {
border-color: #00ff88;
color: #00ff88;
}

/* ── リファレンステーブル ── */
#rxcs-app .rxcs-table-wrap {
overflow-x: auto;
margin-bottom: 6px;
border-radius: 8px;
border: 1px solid #2a2a4a;
}

#rxcs-app .rxcs-table {
width: 100%;
border-collapse: collapse;
font-size: 0.84rem;
min-width: 580px;
}

#rxcs-app .rxcs-table thead tr {
background: #0d0d1a;
}

#rxcs-app .rxcs-table thead th {
color: #606080;
font-size: 0.72rem;
letter-spacing: 0.6px;
padding: 9px 12px;
text-align: left;
font-weight: 700;
border-bottom: 1px solid #2a2a4a;
}

#rxcs-app .rxcs-table tbody tr {
border-bottom: 1px solid #1a1a30;
transition: background 0.15s;
}

#rxcs-app .rxcs-table tbody tr:last-child {
border-bottom: none;
}

#rxcs-app .rxcs-table tbody tr:hover {
background: #1e1e38;
}

#rxcs-app .rxcs-table tbody tr.rxcs-hidden {
display: none;
}

#rxcs-app .rxcs-table td {
padding: 9px 12px;
vertical-align: middle;
}

#rxcs-app .rxcs-token {
font-family: 'Courier New', monospace;
color: #00ff88;
font-weight: 700;
font-size: 0.9rem;
white-space: nowrap;
display: flex;
align-items: center;
gap: 6px;
}

#rxcs-app .rxcs-desc {
color: #c0c0d8;
line-height: 1.5;
font-size: 0.83rem;
}

#rxcs-app .rxcs-example {
font-family: 'Courier New', monospace;
color: #ffe066;
font-size: 0.8rem;
white-space: nowrap;
}

#rxcs-app .rxcs-actions {
display: flex;
gap: 5px;
align-items: center;
white-space: nowrap;
}

#rxcs-app .rxcs-btn-try {
background: #00ff8818;
border: 1px solid #00ff8840;
color: #00ff88;
padding: 4px 10px;
border-radius: 5px;
cursor: pointer;
font-size: 0.74rem;
font-weight: 600;
transition: all 0.18s;
font-family: inherit;
}

#rxcs-app .rxcs-btn-try:hover {
background: #00ff8830;
border-color: #00ff88;
}

#rxcs-app .rxcs-btn-copy {
background: #1a1a3a;
border: 1px solid #2a2a4a;
color: #8080a0;
padding: 4px 9px;
border-radius: 5px;
cursor: pointer;
font-size: 0.74rem;
transition: all 0.18s;
font-family: inherit;
}

#rxcs-app .rxcs-btn-copy:hover {
border-color: #5050a0;
color: #c0c0e0;
}

#rxcs-app .rxcs-btn-copy.copied {
border-color: #00ff88;
color: #00ff88;
}

/* ── セクションヘッダー ── */
#rxcs-app .rxcs-section-header {
background: #0d0d1a;
}

#rxcs-app .rxcs-section-header td {
color: #00cc70;
font-size: 0.74rem;
font-weight: 700;
letter-spacing: 0.08em;
padding: 7px 12px;
border-bottom: 1px solid #2a2a4a;
}

/* ── 結果なし ── */
#rxcs-app .rxcs-no-results {
text-align: center;
color: #404060;
padding: 28px;
font-size: 0.86rem;
display: none;
}

#rxcs-app .rxcs-no-results.visible {
display: block;
}

/* ── レシピカード ── */
#rxcs-app .rxcs-recipes {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
gap: 10px;
margin-top: 8px;
}

#rxcs-app .rxcs-recipe-card {
background: #0d0d1a;
border: 1px solid #2a2a4a;
border-radius: 8px;
padding: 13px 14px;
transition: border-color 0.2s;
}

#rxcs-app .rxcs-recipe-card:hover {
border-color: #3a3a6a;
}

#rxcs-app .rxcs-recipe-name {
color: #e0e0ff;
font-size: 0.86rem;
font-weight: 700;
margin-bottom: 5px;
}

#rxcs-app .rxcs-recipe-pat {
font-family: 'Courier New', monospace;
color: #00ff88;
font-size: 0.76rem;
word-break: break-all;
margin-bottom: 7px;
background: #16162a;
padding: 5px 8px;
border-radius: 5px;
display: block;
}

#rxcs-app .rxcs-recipe-desc {
color: #7070a0;
font-size: 0.78rem;
margin-bottom: 9px;
line-height: 1.5;
}

#rxcs-app .rxcs-recipe-btns {
display: flex;
gap: 6px;
}

/* ── freee CTA ── */
#rxcs-app .rxcs-cta {
background: linear-gradient(135deg, #0f3460 0%, #16213e 100%);
border: 1px solid #1a4a8a;
border-radius: 10px;
padding: 20px 22px;
margin-top: 28px;
display: flex;
align-items: flex-start;
gap: 16px;
flex-wrap: wrap;
}

#rxcs-app .rxcs-cta-icon {
font-size: 2rem;
line-height: 1;
flex-shrink: 0;
}

#rxcs-app .rxcs-cta-body {
flex: 1;
min-width: 200px;
}

#rxcs-app .rxcs-cta-title {
color: #e0e8ff;
font-size: 0.92rem;
font-weight: 700;
margin-bottom: 5px;
}

#rxcs-app .rxcs-cta-desc {
color: #7090c0;
font-size: 0.8rem;
line-height: 1.5;
margin-bottom: 12px;
}

#rxcs-app .rxcs-cta-btn {
display: inline-block;
background: #00ff88;
color: #0d0d1a;
font-weight: 700;
font-size: 0.84rem;
padding: 9px 20px;
border-radius: 6px;
text-decoration: none;
transition: background 0.2s;
}

#rxcs-app .rxcs-cta-btn:hover {
background: #00cc6e;
}

/* ── レスポンシブ ── */
@media (max-width: 640px) {
#rxcs-app {
padding: 14px;
}
#rxcs-app .rxcs-table {
font-size: 0.78rem;
min-width: 460px;
}
#rxcs-app .rxcs-recipes {
grid-template-columns: 1fr;
}
#rxcs-app .rxcs-flags-wrap {
gap: 7px;
}
#rxcs-app .rxcs-cta {
flex-direction: column;
gap: 10px;
}
}
</style>

<h2>正規表現 インタラクティブチートシート</h2>
<p class="rxcs-subtitle">各行の「試す」ボタンをクリックするとパターンがライブテスターに読み込まれます。</p>

<!-- ── ライブテスター ── -->
<div class="rxcs-tester">
<div class="rxcs-tester-title">ライブテスター</div>
<div class="rxcs-row">
<div class="rxcs-pattern-wrap">
<span class="rxcs-slash">/</span>
<input class="rxcs-pattern-input" id="rxcs-pattern" type="text" placeholder="パターンを入力..." autocomplete="off" spellcheck="false" />
<span class="rxcs-slash">/</span>
</div>
<div class="rxcs-flags-wrap">
<label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fg" checked /><span class="rxcs-flag-key">g</span> 全検索</label>
<label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fi" /><span class="rxcs-flag-key">i</span> 大小無視</label>
<label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fm" /><span class="rxcs-flag-key">m</span> 複数行</label>
<label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fs" /><span class="rxcs-flag-key">s</span> dotAll</label>
</div>
</div>
<textarea class="rxcs-teststr" id="rxcs-teststr" rows="3" placeholder="テスト文字列を入力してください。「試す」ボタンでパターンと文字列が自動セットされます。"></textarea>
<div class="rxcs-stats">
<span class="rxcs-badge no-match" id="rxcs-badge">マッチなし</span>
<span style="color:#404060;font-size:0.78rem;" id="rxcs-expr"></span>
</div>
<div class="rxcs-display" id="rxcs-display">マッチした箇所がここにハイライト表示されます</div>
</div>

<!-- ── 検索バー ── -->
<div class="rxcs-search-wrap">
<input class="rxcs-search" id="rxcs-search" type="text" placeholder="チートシートを絞り込む — 例：文字クラス, 量指定子, グループ..." />
<button class="rxcs-search-clear" id="rxcs-search-clear">クリア</button>
</div>

<div class="rxcs-no-results" id="rxcs-no-results">一致するエントリが見つかりませんでした。</div>

<!-- ── リファレンステーブル ── -->
<div class="rxcs-table-wrap">
<table class="rxcs-table" id="rxcs-table">
<thead>
<tr>
<th style="width:120px">パターン</th>
<th>説明</th>
<th style="width:155px">例</th>
<th style="width:110px">操作</th>
</tr>
</thead>
<tbody id="rxcs-tbody">

<!-- 文字クラス -->
<tr class="rxcs-section-header" data-section="character-classes"><td colspan="4">文字クラス (Character Classes)</td></tr>
<tr data-cat="character-classes" data-keywords="ドット 任意 改行以外 文字クラス">
<td><div class="rxcs-token">.</div></td>
<td class="rxcs-desc">改行以外の任意の1文字</td>
<td class="rxcs-example">c.t → "cat", "cut", "c3t"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('c.t','The cat cut c3t')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'.')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="digit 数字 0-9 \d">
<td><div class="rxcs-token">\d</div></td>
<td class="rxcs-desc">数字 [0-9]</td>
<td class="rxcs-example">\d+ → "42", "100"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+','部屋42番、フロア100、ゲート7')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\d')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="非数字 数字以外 \D">
<td><div class="rxcs-token">\D</div></td>
<td class="rxcs-desc">数字以外の文字</td>
<td class="rxcs-example">\D+ → "abc ", " xyz"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\D+','abc 123 xyz 456')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\D')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="word 単語文字 英数字 アンダースコア \w">
<td><div class="rxcs-token">\w</div></td>
<td class="rxcs-desc">単語文字 [a-zA-Z0-9_]</td>
<td class="rxcs-example">\w+ → "hello", "world_2"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\w+','hello world_2 foo-bar')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\w')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="非単語文字 記号 \W">
<td><div class="rxcs-token">\W</div></td>
<td class="rxcs-desc">単語文字以外（記号・空白など）</td>
<td class="rxcs-example">\W → " ", "-", "@"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\W+','hello world-2 foo@bar')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\W')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="空白 スペース タブ 改行 \s">
<td><div class="rxcs-token">\s</div></td>
<td class="rxcs-desc">空白文字（スペース・タブ・改行など）</td>
<td class="rxcs-example">\s+ → 単語間の空白</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\s+','hello   world\ttab\nnewline')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\s')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="非空白 可視文字 \S">
<td><div class="rxcs-token">\S</div></td>
<td class="rxcs-desc">空白以外の文字</td>
<td class="rxcs-example">\S+ → "hello", "world"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\S+','hello   world  here')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\S')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="タブ 水平タブ \t">
<td><div class="rxcs-token">\t</div></td>
<td class="rxcs-desc">水平タブ文字</td>
<td class="rxcs-example">\t → TSVの区切り文字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\t','col1\tcol2\tcol3')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\t')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="改行 ラインブレーク \n">
<td><div class="rxcs-token">\n</div></td>
<td class="rxcs-desc">改行文字</td>
<td class="rxcs-example">\n → 行の区切り</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\n','line1\nline2\nline3')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\n')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="文字クラス 集合 角括弧 範囲">
<td><div class="rxcs-token">[abc]</div></td>
<td class="rxcs-desc">文字クラス — a・b・cのいずれか1文字</td>
<td class="rxcs-example">[aeiou] → 母音</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('[aeiou]','the quick brown fox')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[abc]')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="否定 文字クラス 除外 [^abc]">
<td><div class="rxcs-token">[^abc]</div></td>
<td class="rxcs-desc">否定文字クラス — a・b・c以外の文字</td>
<td class="rxcs-example">[^aeiou\s] → 子音</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('[^aeiou\\s]','the quick brown fox')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[^abc]')">コピー</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="範囲 文字クラス a-z 0-9">
<td><div class="rxcs-token">[a-z]</div></td>
<td class="rxcs-desc">文字範囲（aからzまでの1文字）</td>
<td class="rxcs-example">[a-zA-Z]+ → 英単語</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('[a-zA-Z]+','hello 123 WORLD 456 foo')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[a-z]')">コピー</button></td>
</tr>

<!-- 量指定子 -->
<tr class="rxcs-section-header" data-section="quantifiers"><td colspan="4">量指定子 (Quantifiers)</td></tr>
<tr data-cat="quantifiers" data-keywords="スター 0回以上 貪欲 *">
<td><div class="rxcs-token">*</div></td>
<td class="rxcs-desc">0回以上（貪欲マッチ）</td>
<td class="rxcs-example">ab* → "a", "ab", "abbb"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('ab*','a ab abb abbb b')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'*')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="プラス 1回以上 貪欲 +">
<td><div class="rxcs-token">+</div></td>
<td class="rxcs-desc">1回以上（貪欲マッチ）</td>
<td class="rxcs-example">ab+ → "ab", "abbb"（"a"は非マッチ）</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('ab+','a ab abb abbb b')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'+')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="クエスチョン 0か1 省略可能 ?">
<td><div class="rxcs-token">?</div></td>
<td class="rxcs-desc">0回または1回（省略可能）</td>
<td class="rxcs-example">colou?r → "color", "colour"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('colou?r','color colour colors colours')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'?')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="ちょうど n回 回数指定 {n}">
<td><div class="rxcs-token">{n}</div></td>
<td class="rxcs-desc">ちょうどn回繰り返す</td>
<td class="rxcs-example">\d{4} → "2025", "1234"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d{4}','Year 2025, PIN 9876, code 12')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'{n}')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="n以上m以下 範囲 回数指定 {n,m}">
<td><div class="rxcs-token">{n,m}</div></td>
<td class="rxcs-desc">n回以上m回以下の繰り返し</td>
<td class="rxcs-example">\d{2,4} → "12", "123", "1234"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d{2,4}','1 12 123 1234 12345')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'{n,m}')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="n回以上 最小回数 {n,}">
<td><div class="rxcs-token">{n,}</div></td>
<td class="rxcs-desc">n回以上の繰り返し</td>
<td class="rxcs-example">\d{3,} → "123", "12345"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d{3,}','1 12 123 12345 1234567')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'{n,}')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="非貪欲 最短 lazy *?">
<td><div class="rxcs-token">*?</div></td>
<td class="rxcs-desc">0回以上（非貪欲 — 最短マッチ）</td>
<td class="rxcs-example">&lt;.*?&gt; → 各HTMLタグ</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('<.*?>','<b>bold</b> and <i>italic</i>')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'*?')">コピー</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="非貪欲 最短 lazy +?">
<td><div class="rxcs-token">+?</div></td>
<td class="rxcs-desc">1回以上（非貪欲 — 最短マッチ）</td>
<td class="rxcs-example">".+?" → 引用符内の文字列</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\".+?\"','\"hello\" and \"world\" together')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'+?')">コピー</button></td>
</tr>

<!-- アンカー -->
<tr class="rxcs-section-header" data-section="anchors"><td colspan="4">アンカー・境界 (Anchors &amp; Boundaries)</td></tr>
<tr data-cat="anchors" data-keywords="キャレット 先頭 行頭 文字列先頭 ^">
<td><div class="rxcs-token">^</div></td>
<td class="rxcs-desc">文字列（または行）の先頭（mフラグで行ごと）</td>
<td class="rxcs-example">^\d+ → 先頭の数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('^\\d+','42 apples\n100 oranges\nno digits')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'^')">コピー</button></td>
</tr>
<tr data-cat="anchors" data-keywords="ドル 末尾 行末 文字列末尾 $">
<td><div class="rxcs-token">$</div></td>
<td class="rxcs-desc">文字列（または行）の末尾（mフラグで行ごと）</td>
<td class="rxcs-example">\d+$ → 末尾の数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+$','item 42\nno number\nroom 100')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'$')">コピー</button></td>
</tr>
<tr data-cat="anchors" data-keywords="単語境界 word boundary \b">
<td><div class="rxcs-token">\b</div></td>
<td class="rxcs-desc">単語境界（単語文字と非単語文字の境目）</td>
<td class="rxcs-example">\bcat\b → "cat"（"catch"は非マッチ）</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\bcat\\b','cat catch catfish a cat sat')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\b')">コピー</button></td>
</tr>
<tr data-cat="anchors" data-keywords="非単語境界 単語内部 \B">
<td><div class="rxcs-token">\B</div></td>
<td class="rxcs-desc">非単語境界（単語の内側）</td>
<td class="rxcs-example">\Bcat\B → "concatenate"の中の"cat"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\Bcat\\B','cat concatenate scatter')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\B')">コピー</button></td>
</tr>

<!-- グループ -->
<tr class="rxcs-section-header" data-section="groups"><td colspan="4">グループ・交替 (Groups &amp; Alternation)</td></tr>
<tr data-cat="groups" data-keywords="キャプチャグループ 括弧 後方参照 グループ">
<td><div class="rxcs-token">(abc)</div></td>
<td class="rxcs-desc">キャプチャグループ — マッチした文字列を保存</td>
<td class="rxcs-example">(\d{4})-(\d{2}) → 年・月</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(\\d{4})-(\\d{2})','Date: 2025-05 and 2024-12')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(abc)')">コピー</button></td>
</tr>
<tr data-cat="groups" data-keywords="非キャプチャ グループ (?:abc)">
<td><div class="rxcs-token">(?:abc)</div></td>
<td class="rxcs-desc">非キャプチャグループ — グループ化のみ（保存しない）</td>
<td class="rxcs-example">(?:foo|bar)baz → "foobaz"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?:foo|bar)baz','foobaz barbaz quxbaz')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?:abc)')">コピー</button></td>
</tr>
<tr data-cat="groups" data-keywords="名前付きキャプチャ グループ (?<name>)">
<td><div class="rxcs-token">(?&lt;name&gt;)</div></td>
<td class="rxcs-desc">名前付きキャプチャグループ</td>
<td class="rxcs-example">(?&lt;yr&gt;\d{4}) → グループ"yr"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?<yr>\\d{4})-(?<mo>\\d{2})','2025-05, 2024-12')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?<name>)')">コピー</button></td>
</tr>
<tr data-cat="groups" data-keywords="交替 または パイプ |">
<td><div class="rxcs-token">a|b</div></td>
<td class="rxcs-desc">交替 — aまたはbにマッチ</td>
<td class="rxcs-example">cat|dog → "cat"または"dog"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('cat|dog','I have a cat and a dog')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'a|b')">コピー</button></td>
</tr>
<tr data-cat="groups" data-keywords="後方参照 バックリファレンス \1">
<td><div class="rxcs-token">\1</div></td>
<td class="rxcs-desc">キャプチャグループ1への後方参照</td>
<td class="rxcs-example">(\w+) \1 → 重複単語</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(\\w+) \\1','the the cat sat sat on the mat mat')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\1')">コピー</button></td>
</tr>

<!-- 先読み・後読み -->
<tr class="rxcs-section-header" data-section="lookahead"><td colspan="4">先読み・後読み (Lookahead &amp; Lookbehind)</td></tr>
<tr data-cat="lookahead" data-keywords="肯定先読み 前方アサーション (?=abc)">
<td><div class="rxcs-token">(?=abc)</div></td>
<td class="rxcs-desc">肯定先読み — abcが後ろに続く場合にマッチ</td>
<td class="rxcs-example">\d+(?= USD) → " USD"の前の数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+(?= USD)','100 USD 50 EUR 200 USD')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?=abc)')">コピー</button></td>
</tr>
<tr data-cat="lookahead" data-keywords="否定先読み 前方アサーション (?!abc)">
<td><div class="rxcs-token">(?!abc)</div></td>
<td class="rxcs-desc">否定先読み — abcが後ろに続かない場合にマッチ</td>
<td class="rxcs-example">\d+(?! USD) → USD以外の前の数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+(?! USD)','100 USD 50 EUR 200 USD')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?!abc)')">コピー</button></td>
</tr>
<tr data-cat="lookahead" data-keywords="肯定後読み 後方アサーション (?<=abc)">
<td><div class="rxcs-token">(?&lt;=abc)</div></td>
<td class="rxcs-desc">肯定後読み — abcが前にある場合にマッチ</td>
<td class="rxcs-example">(?&lt;=\$)\d+ → $の後の数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?<=\\$)\\d+','$100 €200 $350 ¥400')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?<=abc)')">コピー</button></td>
</tr>
<tr data-cat="lookahead" data-keywords="否定後読み 後方アサーション (?<!abc)">
<td><div class="rxcs-token">(?&lt;!abc)</div></td>
<td class="rxcs-desc">否定後読み — abcが前にない場合にマッチ</td>
<td class="rxcs-example">(?&lt;!\$)\d+ → $以外の後の数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?<!\\$)\\d+','$100 €200 $350 ref:456')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?<!abc)')">コピー</button></td>
</tr>

<!-- フラグ -->
<tr class="rxcs-section-header" data-section="flags"><td colspan="4">フラグ (Flags / Modifiers)</td></tr>
<tr data-cat="flags" data-keywords="グローバル 全件検索 g フラグ">
<td><div class="rxcs-token">g</div></td>
<td class="rxcs-desc">グローバル — 最初だけでなく全てのマッチを検索</td>
<td class="rxcs-example">/\d+/g → 全ての数字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+','a1 b22 c333 d4444')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'g')">コピー</button></td>
</tr>
<tr data-cat="flags" data-keywords="大文字小文字無視 case insensitive i フラグ">
<td><div class="rxcs-token">i</div></td>
<td class="rxcs-desc">大文字・小文字を区別しない</td>
<td class="rxcs-example">/hello/i → "Hello", "HELLO"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('hello','Hello HELLO hello hElLo')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'i')">コピー</button></td>
</tr>
<tr data-cat="flags" data-keywords="複数行 multiline m フラグ 行頭 行末">
<td><div class="rxcs-token">m</div></td>
<td class="rxcs-desc">複数行 — ^と$を各行の先頭・末尾に対応させる</td>
<td class="rxcs-example">^\w+/m → 各行の先頭の単語</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('^\\w+','first line\nsecond line\nthird line')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'m')">コピー</button></td>
</tr>
<tr data-cat="flags" data-keywords="dotAll ドット 改行 s フラグ">
<td><div class="rxcs-token">s</div></td>
<td class="rxcs-desc">dotAll — ドット(.)が改行もマッチするようになる</td>
<td class="rxcs-example">/.+/s → 複数行にまたがるマッチ</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('start.+end','start\nmiddle\nend')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'s')">コピー</button></td>
</tr>
<tr data-cat="flags" data-keywords="Unicode ユニコード u フラグ 絵文字">
<td><div class="rxcs-token">u</div></td>
<td class="rxcs-desc">Unicode — Unicode完全対応モード</td>
<td class="rxcs-example">/\p{L}+/u → Unicode文字</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\p{L}+','Hello café naïve')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'u')">コピー</button></td>
</tr>

<!-- エスケープ -->
<tr class="rxcs-section-header" data-section="escape"><td colspan="4">特殊文字のエスケープ (Escaping)</td></tr>
<tr data-cat="escape" data-keywords="エスケープ バックスラッシュ リテラル ドット ピリオド">
<td><div class="rxcs-token">\.</div></td>
<td class="rxcs-desc">リテラルのドット（特殊文字は\でエスケープ）</td>
<td class="rxcs-example">\. → "3.14"のドット部分</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\.','3.14 と 2.71 (314は非マッチ)')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\.')">コピー</button></td>
</tr>
<tr data-cat="escape" data-keywords="括弧 角括弧 リテラル エスケープ">
<td><div class="rxcs-token">\( \) \[ \]</div></td>
<td class="rxcs-desc">リテラルの括弧・角括弧</td>
<td class="rxcs-example">\(\d+\) → "(42)"</td>
<td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\(\\d+\\)','Call (800) or (555)-1234')">試す</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\(\\)')">コピー</button></td>
</tr>

</tbody>
</table>
</div>

<!-- ── よく使うパターン集 ── -->
<h3>よく使う正規表現パターン集</h3>
<div class="rxcs-recipes" id="rxcs-recipes">

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">メールアドレス</div>
<code class="rxcs-recipe-pat">[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}</code>
<div class="rxcs-recipe-desc">標準的なメールアドレス形式（サブドメイン・プラスアドレス対応）をマッチします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}','user@example.com, name+tag@sub.domain.org, invalid@, @nouser.com')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">HTTP/HTTPS URL</div>
<code class="rxcs-recipe-pat">https?:\/\/(?:www\.)?[-\w]+(?:\.[-\w]+)+[^\s]*</code>
<div class="rxcs-recipe-desc">httpおよびhttpsのURLをパス・クエリ付きでマッチします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('https?:\\/\\/(?:www\\.)?[-\\w]+(?:\\.[-\\w]+)+[^\\s]*','https://example.com, http://www.site.org/path?q=1, ftp://not-matched')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'https?:\\/\\/(?:www\\.)?[-\\w]+(?:\\.[-\\w]+)+[^\\s]*')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">日本の電話番号</div>
<code class="rxcs-recipe-pat">0\d{1,4}[-\s]?\d{1,4}[-\s]?\d{4}</code>
<div class="rxcs-recipe-desc">固定電話・携帯電話を含む一般的な日本の電話番号形式をマッチします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('0\\d{1,4}[-\\s]?\\d{1,4}[-\\s]?\\d{4}','03-1234-5678, 090-1234-5678, 06 1234 5678, 0120-000-000')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'0\\d{1,4}[-\\s]?\\d{1,4}[-\\s]?\\d{4}')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">日付 ISO形式 (YYYY-MM-DD)</div>
<code class="rxcs-recipe-pat">\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\d|3[01])</code>
<div class="rxcs-recipe-desc">月・日の範囲チェック付きISO 8601日付形式をバリデーションします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('\\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\\d|3[01])','2025-05-16, 2024-12-31, 2025-13-01 (無効), 2025-00-15 (無効)')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\\d|3[01])')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">IPv4アドレス</div>
<code class="rxcs-recipe-pat">\b(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\b</code>
<div class="rxcs-recipe-desc">各オクテット0〜255の範囲チェック付きIPv4アドレスをバリデーションします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('\\b(?:(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\.){3}(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\b','192.168.1.1, 10.0.0.255, 256.1.1.1 (無効)')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\b(?:(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\.){3}(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\b')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">16進数カラーコード</div>
<code class="rxcs-recipe-pat">#(?:[0-9a-fA-F]{3}){1,2}\b</code>
<div class="rxcs-recipe-desc">#で始まる3桁および6桁の16進数カラーコードをマッチします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('#(?:[0-9a-fA-F]{3}){1,2}\\b','#fff, #1a1a2e, #00FF88, #GGGGGG (無効)')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'#(?:[0-9a-fA-F]{3}){1,2}\\b')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">日本の郵便番号</div>
<code class="rxcs-recipe-pat">\d{3}-?\d{4}</code>
<div class="rxcs-recipe-desc">ハイフンあり・なし両方の日本の郵便番号形式をマッチします。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('\\d{3}-?\\d{4}','〒100-0001, 1500001, 530-0001, 無効: 123-45')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\d{3}-?\\d{4}')">コピー</button>
</div>
</div>

<div class="rxcs-recipe-card">
<div class="rxcs-recipe-name">強力なパスワード</div>
<code class="rxcs-recipe-pat">(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*]).{8,}</code>
<div class="rxcs-recipe-desc">小文字・大文字・数字・記号をそれぞれ1文字以上含む8文字以上のパスワード。</div>
<div class="rxcs-recipe-btns">
<button class="rxcs-btn-try" onclick="rxcsTry('(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*]).{8,}','StrongP@ss1, weakpass, NoSpecial1A, Short@1A')">試す</button>
<button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*]).{8,}')">コピー</button>
</div>
</div>

</div>

<!-- ── freee CTA ── -->
<div class="rxcs-cta">
<div class="rxcs-cta-icon">📊</div>
<div class="rxcs-cta-body">
<div class="rxcs-cta-title">freee会計で請求書・帳簿をラクに管理</div>
<div class="rxcs-cta-desc">正規表現でデータ抽出・加工を自動化しても、最終的な帳簿管理はfreeeにお任せ。エンジニア・フリーランスに人気のクラウド会計ソフトです。初月無料でお試しいただけます。</div>
<a class="rxcs-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>
</div>

<script>
(function() {
var patEl   = document.getElementById('rxcs-pattern');
var testEl  = document.getElementById('rxcs-teststr');
var dispEl  = document.getElementById('rxcs-display');
var badgeEl = document.getElementById('rxcs-badge');
var exprEl  = document.getElementById('rxcs-expr');
var searchEl = document.getElementById('rxcs-search');
var clearEl  = document.getElementById('rxcs-search-clear');
var noResEl  = document.getElementById('rxcs-no-results');
var tbody    = document.getElementById('rxcs-tbody');

var flagEls = {
g: document.getElementById('rxcs-fg'),
i: document.getElementById('rxcs-fi'),
m: document.getElementById('rxcs-fm'),
s: document.getElementById('rxcs-fs')
};

function getFlags() {
return Object.keys(flagEls).filter(function(k){ return flagEls[k].checked; }).join('');
}

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function run() {
var pat  = patEl.value.trim();
var test = testEl.value;
var flags = getFlags();

exprEl.textContent = pat ? ('/' + pat + '/' + flags) : '';

if (!pat || !test) {
badgeEl.textContent = pat ? 'テスト文字列を入力してください' : 'パターンを入力してください';
badgeEl.className = 'rxcs-badge no-match';
dispEl.textContent = test || 'マッチした箇所がここにハイライト表示されます';
return;
}

var re;
try {
var gFlags = flags.indexOf('g') === -1 ? flags + 'g' : flags;
re = new RegExp(pat, gFlags);
} catch(e) {
badgeEl.textContent = '正規表現エラー';
badgeEl.className = 'rxcs-badge error';
dispEl.textContent = test;
return;
}

var matches = [];
var m;
re.lastIndex = 0;
while ((m = re.exec(test)) !== null) {
matches.push({ index: m.index, len: m[0].length, val: m[0] });
if (m[0].length === 0) re.lastIndex++;
if (matches.length > 500) break;
}

var cnt = matches.length;
badgeEl.textContent = cnt === 0 ? 'マッチなし' : cnt + '件マッチ';
badgeEl.className = 'rxcs-badge' + (cnt === 0 ? ' no-match' : '');

if (cnt === 0) {
dispEl.textContent = test;
return;
}

var parts = [];
var last = 0;
matches.forEach(function(match, i) {
if (match.index > last) {
parts.push('<span>' + escHtml(test.slice(last, match.index)) + '</span>');
}
var cls = i % 2 === 0 ? 'rxcs-hl' : 'rxcs-hl-alt';
parts.push('<span class="' + cls + '">' + escHtml(match.val) + '</span>');
last = match.index + match.len;
});
if (last < test.length) {
parts.push('<span>' + escHtml(test.slice(last)) + '</span>');
}
dispEl.innerHTML = parts.join('');
}

// 検索・絞り込み
function applySearch() {
var q = searchEl.value.trim().toLowerCase();
var rows = tbody.querySelectorAll('tr[data-cat]');
var sections = tbody.querySelectorAll('tr.rxcs-section-header');
var visibleBySection = {};

rows.forEach(function(row) {
var kw   = (row.getAttribute('data-keywords') || '').toLowerCase();
var cat  = (row.getAttribute('data-cat') || '').toLowerCase();
var text = row.textContent.toLowerCase();
var show = !q || kw.indexOf(q) !== -1 || text.indexOf(q) !== -1 || cat.indexOf(q) !== -1;
row.classList.toggle('rxcs-hidden', !show);
if (show) visibleBySection[cat] = true;
});

sections.forEach(function(sec) {
var secId = sec.getAttribute('data-section');
var visible = !q || visibleBySection[secId];
sec.classList.toggle('rxcs-hidden', !visible);
});

var anyVisible = tbody.querySelectorAll('tr[data-cat]:not(.rxcs-hidden)').length > 0;
noResEl.classList.toggle('visible', !anyVisible && !!q);
}

searchEl.addEventListener('input', applySearch);
clearEl.addEventListener('click', function() {
searchEl.value = '';
applySearch();
searchEl.focus();
});

patEl.addEventListener('input', run);
testEl.addEventListener('input', run);
Object.keys(flagEls).forEach(function(k) {
flagEls[k].addEventListener('change', run);
});

run();
})();

// グローバルヘルパー（テーブル行の onclick から呼び出し）
function rxcsTry(pattern, testStr) {
var patEl  = document.getElementById('rxcs-pattern');
var testEl = document.getElementById('rxcs-teststr');
patEl.value  = pattern;
testEl.value = testStr;
patEl.dispatchEvent(new Event('input'));
document.getElementById('rxcs-pattern').scrollIntoView({ behavior: 'smooth', block: 'center' });
}

function rxcsCopy(btn, text) {
var copy = function() {
btn.textContent = 'コピー完了!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'コピー';
btn.classList.remove('copied');
}, 1600);
};
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(copy);
} else {
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
copy();
}
}
</script>

</div>

---

## 正規表現の使い方

**正規表現（Regex）**とは、文字列の検索パターンを定義する文字列の連続です。ほぼすべてのプログラミング言語やテキストエディタで、入力バリデーション・データ抽出・検索置換・文字列解析などのために活用されています。

**基本概念：**

- **貪欲 vs. 非貪欲** — `*`、`+`、`{n,m}` はデフォルトで貪欲（できるだけ長くマッチ）です。末尾に `?` を付ける（例：`*?`、`+?`）と非貪欲（できるだけ短くマッチ）になります。HTMLタグや引用符付き文字列のパースで重要です。
- **キャプチャグループ vs. 非キャプチャグループ** — マッチした文字列を後で参照（`$1` など）する場合は `(...)` を使用します。グループ化だけが目的で値を保存しない場合は `(?:...)` を使用します。
- **アンカーと複数行フラグ** — `^` と `$` はデフォルトで文字列全体の先頭・末尾にマッチします。`m` フラグを有効にすると、各行の先頭・末尾にマッチするようになります。
- **先読み・後読みはゼロ幅** — `(?=foo)` や `(?<=foo)` は条件を検証するだけで文字を消費しません。そのため、周囲の文字をマッチ結果に含めずに条件付きマッチが行えます。

---

### 関連ツール

> 正規表現をリアルタイムテスト → [正規表現テスター](/ja/tools/regex-tester/)

> SQLクエリを整形 → [SQLフォーマッター](/ja/tools/sql-formatter/)

> テキストの差分を確認 → [テキスト差分チェッカー](/ja/tools/text-diff/)
