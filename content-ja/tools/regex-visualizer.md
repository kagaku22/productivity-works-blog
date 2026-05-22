---
title: "正規表現ビジュアライザー"
date: 2025-12-19
description: "無料の正規表現解説ツール。正規表現を入力するとトークンごとに日本語で意味を表示。テスト文字列のマッチをハイライト。グループ抽出対応。"
categories: ["無料ツール"]
tags: ["開発ツール", "プログラミング", "無料ツール"]
slug: "regex-visualizer"
ShowToc: false
cover:
  image: "/images/covers/regex-visualizer-ja.png"
  alt: "正規表現ビジュアライザー"
---

正規表現をブラウザ上でビジュアル解析。パターンを入力するとトークンごとに日本語で意味を表示し、テスト文字列のマッチをハイライト表示します。登録不要、外部ライブラリなし。

<div id="rv-app">
<style>
#rv-app *, #rv-app *::before, #rv-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#rv-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Meiryo", "Segoe UI", sans-serif;
font-size: 14px;
color: #1e293b;
max-width: 900px;
margin: 0 auto;
}

#rv-app .rv-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 18px 20px;
margin-bottom: 14px;
}

#rv-app .rv-label {
font-size: 11px;
font-weight: 700;
letter-spacing: .06em;
text-transform: uppercase;
color: #64748b;
margin-bottom: 10px;
}

/* Pattern row */
#rv-app .rv-pattern-row {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
}
#rv-app .rv-slash {
font-size: 22px;
color: #94a3b8;
font-family: "Fira Mono", "Consolas", monospace;
flex-shrink: 0;
}
#rv-app #rv-pattern {
flex: 1;
min-width: 180px;
font-family: "Fira Mono", "Consolas", monospace;
font-size: 15px;
padding: 8px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
outline: none;
color: #1e293b;
background: #f8fafc;
transition: border-color .15s;
}
#rv-app #rv-pattern:focus { border-color: #6366f1; background: #fff; }

#rv-app .rv-flags {
display: flex;
gap: 5px;
flex-wrap: wrap;
}
#rv-app .rv-flag {
padding: 6px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
cursor: pointer;
font-size: 12px;
font-weight: 700;
font-family: "Fira Mono", monospace;
background: #f8fafc;
color: #64748b;
transition: all .15s;
user-select: none;
}
#rv-app .rv-flag.on { background: #6366f1; border-color: #6366f1; color: #fff; }
#rv-app .rv-flag:hover:not(.on) { border-color: #6366f1; color: #6366f1; }

#rv-app .rv-copy-btn {
padding: 7px 14px;
background: #f1f5f9;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
cursor: pointer;
font-size: 12px;
font-weight: 600;
color: #475569;
transition: all .15s;
white-space: nowrap;
}
#rv-app .rv-copy-btn:hover { background: #e2e8f0; }
#rv-app .rv-copy-btn.copied { background: #d1fae5; border-color: #6ee7b7; color: #065f46; }

/* Error */
#rv-app .rv-error {
display: none;
background: #fef2f2;
border: 1px solid #fca5a5;
color: #b91c1c;
border-radius: 7px;
padding: 8px 12px;
font-size: 13px;
margin-top: 8px;
}

/* Visual breakdown */
#rv-app .rv-breakdown {
display: flex;
flex-wrap: wrap;
gap: 6px;
min-height: 40px;
align-items: flex-start;
}
#rv-app .rv-token {
display: flex;
flex-direction: column;
align-items: center;
gap: 3px;
}
#rv-app .rv-tok-text {
font-family: "Fira Mono", "Consolas", monospace;
font-size: 13px;
font-weight: 700;
padding: 4px 8px;
border-radius: 5px;
white-space: pre;
}
#rv-app .rv-tok-desc {
font-size: 10px;
color: #475569;
text-align: center;
max-width: 100px;
line-height: 1.3;
}

/* Token color palette */
#rv-app .rv-tok-anchor    { background: #fef9c3; color: #854d0e; }
#rv-app .rv-tok-quant     { background: #dcfce7; color: #166534; }
#rv-app .rv-tok-escape    { background: #ede9fe; color: #5b21b6; }
#rv-app .rv-tok-charclass { background: #dbeafe; color: #1e40af; }
#rv-app .rv-tok-group     { background: #fce7f3; color: #9d174d; }
#rv-app .rv-tok-alt       { background: #ffedd5; color: #9a3412; }
#rv-app .rv-tok-dot       { background: #f0f9ff; color: #0369a1; }
#rv-app .rv-tok-literal   { background: #f1f5f9; color: #334155; }

/* Legend */
#rv-app .rv-legend {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 10px;
}
#rv-app .rv-legend-item {
display: flex;
align-items: center;
gap: 5px;
font-size: 11px;
color: #475569;
}
#rv-app .rv-legend-swatch {
width: 12px;
height: 12px;
border-radius: 3px;
flex-shrink: 0;
}

/* Patterns library */
#rv-app .rv-lib {
display: flex;
flex-wrap: wrap;
gap: 7px;
}
#rv-app .rv-lib-btn {
padding: 6px 12px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 6px;
cursor: pointer;
font-size: 12px;
font-weight: 600;
color: #475569;
transition: all .15s;
}
#rv-app .rv-lib-btn:hover { background: #ede9fe; border-color: #a5b4fc; color: #4338ca; }

/* Test string */
#rv-app #rv-test {
width: 100%;
min-height: 90px;
font-family: "Fira Mono", "Consolas", monospace;
font-size: 13px;
padding: 10px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
resize: vertical;
outline: none;
background: #f8fafc;
color: #1e293b;
transition: border-color .15s;
}
#rv-app #rv-test:focus { border-color: #6366f1; background: #fff; }

/* Highlight output */
#rv-app .rv-hl-box {
font-family: "Fira Mono", "Consolas", monospace;
font-size: 13px;
line-height: 1.7;
padding: 10px 12px;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 7px;
white-space: pre-wrap;
word-break: break-all;
min-height: 42px;
}
#rv-app .rv-hl-box .rv-m0  { background: #fde68a; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m1  { background: #bbf7d0; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m2  { background: #bfdbfe; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m3  { background: #fecdd3; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m4  { background: #e9d5ff; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m5  { background: #fed7aa; border-radius: 3px; }

#rv-app .rv-stats {
display: flex;
gap: 16px;
margin-top: 10px;
flex-wrap: wrap;
}
#rv-app .rv-stat {
font-size: 12px;
color: #64748b;
}
#rv-app .rv-stat strong { color: #1e293b; }

/* Match list */
#rv-app .rv-match-list {
list-style: none;
display: flex;
flex-direction: column;
gap: 8px;
max-height: 280px;
overflow-y: auto;
}
#rv-app .rv-match-item {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 7px;
padding: 8px 12px;
font-size: 12px;
}
#rv-app .rv-match-item .rv-mi-head {
font-weight: 700;
color: #334155;
margin-bottom: 4px;
}
#rv-app .rv-match-item .rv-mi-val {
font-family: "Fira Mono", monospace;
background: #fde68a;
padding: 2px 6px;
border-radius: 4px;
font-size: 12px;
}
#rv-app .rv-match-item .rv-mi-grp {
margin-top: 4px;
font-size: 11px;
color: #64748b;
}
#rv-app .rv-match-item .rv-mi-grp span {
font-family: "Fira Mono", monospace;
background: #bbf7d0;
padding: 1px 5px;
border-radius: 3px;
color: #065f46;
margin-left: 4px;
}
#rv-app .rv-empty-msg {
color: #94a3b8;
font-size: 13px;
text-align: center;
padding: 16px 0;
}

/* freee CTA */
#rv-app + .rv-freee-cta, .rv-freee-cta {
background: linear-gradient(135deg, #e0f2fe 0%, #f0f9ff 100%);
border: 1px solid #7dd3fc;
border-radius: 10px;
padding: 16px 20px;
margin-top: 16px;
display: flex;
flex-direction: column;
gap: 6px;
}
</style>

<!-- パターン入力 -->
<div class="rv-card">
<div class="rv-label">正規表現パターン</div>
<div class="rv-pattern-row">
<span class="rv-slash">/</span>
<input id="rv-pattern" type="text" placeholder="例: (\d{4})年(\d{1,2})月(\d{1,2})日" autocomplete="off" spellcheck="false" />
<span class="rv-slash">/</span>
<div class="rv-flags">
<button class="rv-flag on" data-flag="g" title="グローバル検索">g</button>
<button class="rv-flag" data-flag="i" title="大文字小文字を区別しない">i</button>
<button class="rv-flag" data-flag="m" title="複数行">m</button>
<button class="rv-flag" data-flag="s" title="ドットオール">s</button>
</div>
<button class="rv-copy-btn" id="rv-copy-btn">コピー</button>
</div>
<div class="rv-error" id="rv-error"></div>
</div>

<!-- よく使うパターン -->
<div class="rv-card">
<div class="rv-label">よく使うパターン</div>
<div class="rv-lib">
<button class="rv-lib-btn" data-pattern="[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}">メールアドレス</button>
<button class="rv-lib-btn" data-pattern="https?:\/\/(www\.)?[-a-zA-Z0-9@:%._+~#=]{1,256}\.[a-zA-Z]{2,6}\b([-a-zA-Z0-9@:%_+.~#?&\/=]*)">URL</button>
<button class="rv-lib-btn" data-pattern="0\d{1,4}-\d{1,4}-\d{4}">電話番号（日本）</button>
<button class="rv-lib-btn" data-pattern="\d{3}-\d{4}">郵便番号</button>
<button class="rv-lib-btn" data-pattern="(\d{4})年(\d{1,2})月(\d{1,2})日">日付（漢字）</button>
<button class="rv-lib-btn" data-pattern="\d{4}[-\/]\d{2}[-\/]\d{2}">日付 YYYY-MM-DD</button>
<button class="rv-lib-btn" data-pattern="\b((25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(25[0-5]|2[0-4]\d|[01]?\d\d?)\b">IPアドレス</button>
<button class="rv-lib-btn" data-pattern="[一-龥ぁ-んァ-ヶ]+">日本語（漢字・かな）</button>
</div>
</div>

<!-- ビジュアル解説 -->
<div class="rv-card">
<div class="rv-label">ビジュアル解説</div>
<div class="rv-breakdown" id="rv-breakdown">
<span class="rv-empty-msg">上にパターンを入力するとトークンごとの解説が表示されます。</span>
</div>
<div class="rv-legend">
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#fef9c3;border:1px solid #fde047;"></div>アンカー</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#dcfce7;border:1px solid #86efac;"></div>量指定子</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#ede9fe;border:1px solid #c4b5fd;"></div>エスケープ / 特殊</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#dbeafe;border:1px solid #93c5fd;"></div>文字クラス</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#fce7f3;border:1px solid #f9a8d4;"></div>グループ</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#ffedd5;border:1px solid #fdba74;"></div>選択（OR）</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#f0f9ff;border:1px solid #7dd3fc;"></div>ワイルドカード</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#f1f5f9;border:1px solid #cbd5e1;"></div>リテラル</div>
</div>
</div>

<!-- テスト文字列 -->
<div class="rv-card">
<div class="rv-label">テスト文字列</div>
<textarea id="rv-test" placeholder="テストしたいテキストを貼り付けてください…"></textarea>
</div>

<!-- マッチハイライト -->
<div class="rv-card">
<div class="rv-label">マッチハイライト</div>
<div class="rv-hl-box" id="rv-hl"><span class="rv-empty-msg">マッチ結果がここに表示されます。</span></div>
<div class="rv-stats">
<div class="rv-stat">マッチ数: <strong id="rv-count">—</strong></div>
<div class="rv-stat">文字数: <strong id="rv-len">0</strong></div>
</div>
</div>

<!-- マッチ詳細・グループ抽出 -->
<div class="rv-card">
<div class="rv-label">マッチ詳細・キャプチャグループ</div>
<ul class="rv-match-list" id="rv-match-list">
<li class="rv-empty-msg">まだマッチがありません。</li>
</ul>
</div>

<!-- freee CTA -->
<div class="rv-freee-cta">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">開発業務の経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、クラウドサービス・開発ツールの経費精算もまとめて管理。確定申告もラクラク。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function () {
'use strict';

var flagState = { g: true, i: false, m: false, s: false };

var elPat     = document.getElementById('rv-pattern');
var elTest    = document.getElementById('rv-test');
var elError   = document.getElementById('rv-error');
var elBreak   = document.getElementById('rv-breakdown');
var elHl      = document.getElementById('rv-hl');
var elCount   = document.getElementById('rv-count');
var elLen     = document.getElementById('rv-len');
var elMlist   = document.getElementById('rv-match-list');
var elCopy    = document.getElementById('rv-copy-btn');

/* ── Helpers ── */
function esc(s) {
return String(s)
.replace(/&/g,'&amp;')
.replace(/</g,'&lt;')
.replace(/>/g,'&gt;');
}

/* ── Flags ── */
document.querySelectorAll('#rv-app .rv-flag').forEach(function (el) {
el.addEventListener('click', function () {
var f = el.dataset.flag;
flagState[f] = !flagState[f];
el.classList.toggle('on', flagState[f]);
run();
});
});

/* ── Copy button ── */
elCopy.addEventListener('click', function () {
var pat = elPat.value;
if (!pat) return;
var flags = buildFlags();
navigator.clipboard.writeText('/' + pat + '/' + flags).then(function () {
elCopy.textContent = 'コピー完了！';
elCopy.classList.add('copied');
setTimeout(function () {
elCopy.textContent = 'コピー';
elCopy.classList.remove('copied');
}, 1800);
}).catch(function () {});
});

/* ── Common patterns library ── */
document.querySelectorAll('#rv-app .rv-lib-btn').forEach(function (el) {
el.addEventListener('click', function () {
elPat.value = el.dataset.pattern;
run();
});
});

/* ── Build flags string ── */
function buildFlags() {
return ['g','i','m','s'].filter(function (f) { return flagState[f]; }).join('');
}

/* ── Tokenizer（日本語説明） ── */
var TOKENS = [
// アンカー
[/^\^/,                         'anchor',    '行頭アンカー（文字列または行の先頭）'],
[/^\$/,                         'anchor',    '行末アンカー（文字列または行の末尾）'],
[/^\\b/,                        'escape',    '単語境界'],
[/^\\B/,                        'escape',    '非単語境界'],
[/^\\A/,                        'escape',    '文字列の先頭（\\A）'],
[/^\\Z/,                        'escape',    '文字列の末尾（\\Z）'],
// エスケープ
[/^\\d/,                        'escape',    '任意の数字 [0-9]'],
[/^\\D/,                        'escape',    '数字以外 [^0-9]'],
[/^\\w/,                        'escape',    '単語文字 [a-zA-Z0-9_]'],
[/^\\W/,                        'escape',    '非単語文字'],
[/^\\s/,                        'escape',    '空白文字（スペース・タブ等）'],
[/^\\S/,                        'escape',    '非空白文字'],
[/^\\t/,                        'escape',    'タブ文字'],
[/^\\n/,                        'escape',    '改行文字'],
[/^\\r/,                        'escape',    'キャリッジリターン'],
[/^\\f/,                        'escape',    'フォームフィード'],
[/^\\v/,                        'escape',    '垂直タブ'],
[/^\\0/,                        'escape',    'ヌル文字'],
[/^\\x[0-9a-fA-F]{2}/,         'escape',    '16進数エスケープ'],
[/^\\u[0-9a-fA-F]{4}/,         'escape',    'Unicodeエスケープ'],
[/^\\[^a-zA-Z0-9]/,            'escape',    '特殊文字のエスケープ'],
// グループ
[/^\(\?<[^>]+>/,               'group',     '名前付きキャプチャグループ開始'],
[/^\(\?:/,                      'group',     '非キャプチャグループ開始'],
[/^\(\?=/,                      'group',     '前読み（肯定）開始'],
[/^\(\?!/,                      'group',     '前読み（否定）開始'],
[/^\(\?<=/,                     'group',     '後読み（肯定）開始'],
[/^\(\?<!/,                     'group',     '後読み（否定）開始'],
[/^\(/,                         'group',     'キャプチャグループ開始'],
[/^\)/,                         'group',     'グループ終了'],
// 文字クラス
[/^\[\^[^\]]*\]/,              'charclass', '否定文字クラス（クラス内の文字以外）'],
[/^\[[^\]]*\]/,                'charclass', '文字クラス（クラス内のいずれかの文字）'],
// 量指定子
[/^\{[0-9]+,[0-9]+\}\?/,      'quant',     '非貪欲量指定子: {n,m}回'],
[/^\{[0-9]+,\}\?/,            'quant',     '非貪欲量指定子: {n}回以上'],
[/^\{[0-9]+\}\?/,             'quant',     '非貪欲量指定子: ちょうど{n}回'],
[/^\{[0-9]+,[0-9]+\}/,        'quant',     '貪欲量指定子: {n}〜{m}回'],
[/^\{[0-9]+,\}/,              'quant',     '貪欲量指定子: {n}回以上'],
[/^\{[0-9]+\}/,               'quant',     '量指定子: ちょうど{n}回'],
[/^\*\?/,                      'quant',     '非貪欲: 0回以上（できるだけ少なく）'],
[/^\+\?/,                      'quant',     '非貪欲: 1回以上（できるだけ少なく）'],
[/^\?\?/,                      'quant',     '非貪欲: 0または1回（0を優先）'],
[/^\*/,                        'quant',     '貪欲: 0回以上'],
[/^\+/,                        'quant',     '貪欲: 1回以上'],
[/^\?/,                        'quant',     '量指定子: 0または1回（省略可能）'],
// 選択
[/^\|/,                        'alt',       '選択（OR）— 左右どちらかにマッチ'],
// ワイルドカード
[/^\./,                        'dot',       'ワイルドカード（改行以外の任意の1文字）'],
// リテラル
[/^[^]/,                       'literal',   'リテラル文字'],
];

var TYPE_CLASS = {
anchor:    'rv-tok-anchor',
quant:     'rv-tok-quant',
escape:    'rv-tok-escape',
charclass: 'rv-tok-charclass',
group:     'rv-tok-group',
alt:       'rv-tok-alt',
dot:       'rv-tok-dot',
literal:   'rv-tok-literal',
};

function tokenize(pat) {
var toks = [], rem = pat, limit = 500;
while (rem.length && limit-- > 0) {
var hit = false;
for (var i = 0; i < TOKENS.length; i++) {
var m = rem.match(TOKENS[i][0]);
if (m) {
toks.push({ text: m[0], type: TOKENS[i][1], desc: TOKENS[i][2] });
rem = rem.slice(m[0].length);
hit = true;
break;
}
}
if (!hit) rem = rem.slice(1);
}
return toks;
}

/* ── ビジュアル解説レンダリング ── */
function renderBreakdown(pat) {
if (!pat) {
elBreak.innerHTML = '<span class="rv-empty-msg">上にパターンを入力するとトークンごとの解説が表示されます。</span>';
return;
}
var toks = tokenize(pat);
if (!toks.length) {
elBreak.innerHTML = '<span class="rv-empty-msg">解析できるトークンがありません。</span>';
return;
}
var html = '';
toks.forEach(function (tk) {
var cls = TYPE_CLASS[tk.type] || 'rv-tok-literal';
html += '<div class="rv-token">'
+ '<span class="rv-tok-text ' + cls + '">' + esc(tk.text) + '</span>'
+ '<span class="rv-tok-desc">' + esc(tk.desc) + '</span>'
+ '</div>';
});
elBreak.innerHTML = html;
}

/* ── マッチハイライト ── */
var MATCH_COLORS = ['rv-m0','rv-m1','rv-m2','rv-m3','rv-m4','rv-m5'];

function renderMatches(text, regex) {
elLen.textContent = text.length;
if (!regex) {
elHl.innerHTML = '<span class="rv-empty-msg">マッチ結果がここに表示されます。</span>';
elCount.textContent = '—';
elMlist.innerHTML = '<li class="rv-empty-msg">まだマッチがありません。</li>';
return;
}

var matches = [];
var re = new RegExp(regex.source, regex.flags.replace('g','') + 'g');
var m;
var safety = 0;
while ((m = re.exec(text)) !== null && safety++ < 500) {
matches.push({ index: m.index, end: m.index + m[0].length, value: m[0], groups: Array.from(m).slice(1) });
if (m[0].length === 0) re.lastIndex++;
}

elCount.textContent = matches.length;

if (matches.length === 0) {
elHl.innerHTML = '<span class="rv-empty-msg" style="color:#f97316;">マッチが見つかりませんでした。</span>'
+ (text ? esc(text) : '');
elMlist.innerHTML = '<li class="rv-empty-msg">マッチが見つかりませんでした。</li>';
return;
}

var hlHtml = '', pos = 0, ci = 0;
matches.forEach(function (mt) {
if (mt.index > pos) hlHtml += esc(text.slice(pos, mt.index));
var cls = MATCH_COLORS[ci % MATCH_COLORS.length];
hlHtml += '<span class="' + cls + '">' + esc(mt.value) + '</span>';
pos = mt.end;
ci++;
});
if (pos < text.length) hlHtml += esc(text.slice(pos));
elHl.innerHTML = hlHtml;

var listHtml = '';
matches.forEach(function (mt, idx) {
listHtml += '<li class="rv-match-item">'
+ '<div class="rv-mi-head">マッチ ' + (idx+1) + ' &nbsp;<span class="rv-mi-val">' + esc(mt.value) + '</span>'
+ ' &nbsp;<span style="font-size:11px;color:#94a3b8;">位置 ' + mt.index + '〜' + mt.end + '</span></div>';
if (mt.groups.length) {
listHtml += '<div class="rv-mi-grp">グループ:';
mt.groups.forEach(function (g, gi) {
listHtml += ' <span>$' + (gi+1) + ': ' + esc(g !== undefined ? g : 'undefined') + '</span>';
});
listHtml += '</div>';
}
listHtml += '</li>';
});
elMlist.innerHTML = listHtml;
}

/* ── メイン実行 ── */
function run() {
var pat = elPat.value;
var text = elTest.value;
elLen.textContent = text.length;
elError.style.display = 'none';

renderBreakdown(pat);

if (!pat) {
renderMatches(text, null);
return;
}

var flags = buildFlags();
var regex;
try {
regex = new RegExp(pat, flags);
} catch (e) {
elError.style.display = 'block';
elError.textContent = '正規表現エラー: ' + e.message;
elHl.innerHTML = '<span class="rv-empty-msg">パターンを修正するとハイライトが表示されます。</span>';
elCount.textContent = '—';
elMlist.innerHTML = '<li class="rv-empty-msg">—</li>';
return;
}

renderMatches(text, regex);
}

elPat.addEventListener('input', run);
elTest.addEventListener('input', run);

// デフォルト例
elPat.value = '(\\d{4})年(\\d{1,2})月(\\d{1,2})日';
elTest.value = '予定日: 2025年5月16日\n締切: 2025年12月31日\n開始: 2024年4月1日';
run();
})();
</script>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

> 関連ツール → [正規表現テスター](/ja/tools/regex-tester/) · [正規表現チートシート](/ja/tools/regex-cheatsheet/)
