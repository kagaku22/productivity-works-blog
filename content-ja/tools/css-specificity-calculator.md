---
title: "CSS詳細度計算ツール"
date: 2025-11-09
description: "無料のCSS詳細度（Specificity）計算ツール。CSSセレクタを入力して詳細度スコアを即計算。複数セレクタの比較・バーチャート表示対応。"
categories: ["無料ツール"]
slug: "css-specificity-calculator"
ShowToc: false
cover:
  image: "/images/covers/css-specificity-calculator-ja.png"
  alt: "CSS詳細度計算ツール"
---

<div id="cs-app">
<style>
#cs-app *,
#cs-app *::before,
#cs-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#cs-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Meiryo", "Segoe UI", sans-serif;
font-size: 14px;
color: #1a1a2e;
background: #f8f9ff;
border-radius: 12px;
padding: 24px;
max-width: 100%;
overflow: hidden;
}

#cs-app h2.cs-title {
font-size: 1.4rem;
font-weight: 700;
margin-bottom: 4px;
color: #1a1a2e;
}

#cs-app p.cs-subtitle {
color: #666;
margin-bottom: 20px;
font-size: 0.9rem;
}

/* 入力エリア */
#cs-app .cs-input-row {
display: flex;
gap: 8px;
margin-bottom: 16px;
align-items: stretch;
}

#cs-app #cs-selector-input {
flex: 1;
border: 2px solid #d0d7ff;
border-radius: 8px;
padding: 10px 14px;
font-size: 1rem;
font-family: "Courier New", monospace;
outline: none;
background: #fff;
color: #1a1a2e;
transition: border-color 0.15s;
}

#cs-app #cs-selector-input:focus {
border-color: #3a3aff;
}

#cs-app #cs-selector-input::placeholder {
color: #aaa;
font-family: "Courier New", monospace;
}

#cs-app .cs-btn {
background: #3a3aff;
color: #fff;
border: none;
border-radius: 8px;
padding: 10px 20px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
white-space: nowrap;
}

#cs-app .cs-btn:hover { background: #2020cc; }

#cs-app .cs-btn-secondary {
background: #f0f0ff;
color: #3a3aff;
border: 2px solid #d0d7ff;
border-radius: 8px;
padding: 10px 16px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
white-space: nowrap;
}

#cs-app .cs-btn-secondary:hover {
background: #3a3aff;
color: #fff;
border-color: #3a3aff;
}

/* スコア表示 */
#cs-app .cs-score-panel {
background: #fff;
border-radius: 10px;
padding: 20px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
display: none;
}

#cs-app .cs-score-panel.cs-visible { display: block; }

#cs-app .cs-score-label {
font-size: 0.78rem;
font-weight: 700;
color: #888;
text-transform: uppercase;
letter-spacing: 0.06em;
margin-bottom: 12px;
}

#cs-app .cs-score-boxes {
display: flex;
gap: 12px;
align-items: center;
flex-wrap: wrap;
margin-bottom: 16px;
}

#cs-app .cs-score-box {
display: flex;
flex-direction: column;
align-items: center;
gap: 4px;
}

#cs-app .cs-score-value {
width: 64px;
height: 64px;
border-radius: 12px;
display: flex;
align-items: center;
justify-content: center;
font-size: 1.8rem;
font-weight: 800;
color: #fff;
}

#cs-app .cs-score-value.cs-inline  { background: #ef4444; }
#cs-app .cs-score-value.cs-ids     { background: #8b5cf6; }
#cs-app .cs-score-value.cs-classes { background: #3a3aff; }
#cs-app .cs-score-value.cs-elements{ background: #10b981; }

#cs-app .cs-score-type {
font-size: 0.72rem;
font-weight: 600;
color: #666;
text-align: center;
max-width: 70px;
}

#cs-app .cs-score-sep {
font-size: 1.6rem;
color: #ccc;
font-weight: 300;
line-height: 1;
padding-bottom: 20px;
}

#cs-app .cs-score-total {
background: #1a1a2e;
color: #fff;
border-radius: 10px;
padding: 10px 18px;
font-size: 1rem;
font-weight: 700;
font-family: "Courier New", monospace;
display: inline-block;
margin-bottom: 12px;
}

/* バーチャート */
#cs-app .cs-bars {
display: flex;
flex-direction: column;
gap: 8px;
}

#cs-app .cs-bar-row {
display: flex;
align-items: center;
gap: 10px;
}

#cs-app .cs-bar-label {
width: 110px;
font-size: 0.78rem;
font-weight: 600;
color: #555;
flex-shrink: 0;
text-align: right;
}

#cs-app .cs-bar-track {
flex: 1;
height: 16px;
background: #f0f0ff;
border-radius: 99px;
overflow: hidden;
}

#cs-app .cs-bar-fill {
height: 100%;
border-radius: 99px;
transition: width 0.4s cubic-bezier(0.4,0,0.2,1);
min-width: 0;
}

#cs-app .cs-bar-fill.cs-inline   { background: #ef4444; }
#cs-app .cs-bar-fill.cs-ids      { background: #8b5cf6; }
#cs-app .cs-bar-fill.cs-classes  { background: #3a3aff; }
#cs-app .cs-bar-fill.cs-elements { background: #10b981; }

#cs-app .cs-bar-count {
width: 28px;
font-size: 0.82rem;
font-weight: 700;
color: #444;
text-align: left;
}

/* 内訳 */
#cs-app .cs-breakdown {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
display: none;
}

#cs-app .cs-breakdown.cs-visible { display: block; }

#cs-app .cs-breakdown h3 {
font-size: 0.9rem;
font-weight: 700;
color: #3a3aff;
margin-bottom: 12px;
}

#cs-app .cs-tokens {
display: flex;
flex-wrap: wrap;
gap: 8px;
}

#cs-app .cs-token {
display: inline-flex;
align-items: center;
gap: 5px;
border-radius: 6px;
padding: 4px 10px;
font-size: 0.82rem;
font-weight: 600;
font-family: "Courier New", monospace;
}

#cs-app .cs-token-dot {
width: 8px;
height: 8px;
border-radius: 50%;
flex-shrink: 0;
}

#cs-app .cs-token.cs-t-inline   { background: #fef2f2; color: #ef4444; }
#cs-app .cs-token.cs-t-inline .cs-token-dot   { background: #ef4444; }
#cs-app .cs-token.cs-t-id       { background: #f5f3ff; color: #7c3aed; }
#cs-app .cs-token.cs-t-id .cs-token-dot       { background: #8b5cf6; }
#cs-app .cs-token.cs-t-class    { background: #eff6ff; color: #3a3aff; }
#cs-app .cs-token.cs-t-class .cs-token-dot    { background: #3a3aff; }
#cs-app .cs-token.cs-t-element  { background: #f0fdf4; color: #059669; }
#cs-app .cs-token.cs-t-element .cs-token-dot  { background: #10b981; }
#cs-app .cs-token.cs-t-combinator { background: #f5f5f5; color: #888; }

#cs-app .cs-legend {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin-top: 12px;
font-size: 0.75rem;
color: #666;
}

#cs-app .cs-legend-item {
display: flex;
align-items: center;
gap: 5px;
}

#cs-app .cs-legend-dot {
width: 10px;
height: 10px;
border-radius: 50%;
flex-shrink: 0;
}

/* 比較リスト */
#cs-app .cs-compare-section {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
}

#cs-app .cs-compare-section h3 {
font-size: 0.9rem;
font-weight: 700;
color: #3a3aff;
margin-bottom: 12px;
}

#cs-app .cs-compare-list {
display: flex;
flex-direction: column;
gap: 6px;
margin-bottom: 10px;
max-height: 320px;
overflow-y: auto;
}

#cs-app .cs-compare-item {
display: flex;
align-items: center;
gap: 10px;
padding: 8px 12px;
border-radius: 8px;
border: 1.5px solid #e0e4ff;
background: #f8f9ff;
transition: border-color 0.15s;
}

#cs-app .cs-compare-item:hover {
border-color: #3a3aff;
}

#cs-app .cs-compare-item.cs-winner {
border-color: #8b5cf6;
background: #faf5ff;
}

#cs-app .cs-compare-rank {
font-size: 0.75rem;
font-weight: 800;
color: #aaa;
width: 20px;
text-align: center;
flex-shrink: 0;
}

#cs-app .cs-compare-rank.cs-rank-1 { color: #f59e0b; }
#cs-app .cs-compare-rank.cs-rank-2 { color: #9ca3af; }
#cs-app .cs-compare-rank.cs-rank-3 { color: #b45309; }

#cs-app .cs-compare-selector {
flex: 1;
font-family: "Courier New", monospace;
font-size: 0.85rem;
color: #1a1a2e;
word-break: break-all;
}

#cs-app .cs-compare-score {
font-family: "Courier New", monospace;
font-size: 0.82rem;
font-weight: 700;
color: #3a3aff;
white-space: nowrap;
flex-shrink: 0;
}

#cs-app .cs-compare-del {
background: none;
border: none;
cursor: pointer;
color: #ccc;
font-size: 1rem;
line-height: 1;
padding: 0 2px;
flex-shrink: 0;
transition: color 0.1s;
}

#cs-app .cs-compare-del:hover { color: #ef4444; }

#cs-app .cs-compare-actions {
display: flex;
gap: 8px;
flex-wrap: wrap;
margin-top: 8px;
}

#cs-app .cs-empty-compare {
color: #aaa;
font-size: 0.85rem;
text-align: center;
padding: 16px 0;
}

/* 例 */
#cs-app .cs-examples-section {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
}

#cs-app .cs-examples-section h3 {
font-size: 0.9rem;
font-weight: 700;
color: #3a3aff;
margin-bottom: 10px;
}

#cs-app .cs-examples-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
gap: 8px;
}

#cs-app .cs-example-btn {
background: #f8f9ff;
border: 1.5px solid #d0d7ff;
border-radius: 8px;
padding: 8px 12px;
text-align: left;
cursor: pointer;
transition: all 0.15s;
display: flex;
flex-direction: column;
gap: 3px;
}

#cs-app .cs-example-btn:hover {
background: #eff6ff;
border-color: #3a3aff;
}

#cs-app .cs-example-selector {
font-family: "Courier New", monospace;
font-size: 0.82rem;
color: #1a1a2e;
font-weight: 600;
}

#cs-app .cs-example-score {
font-size: 0.72rem;
color: #888;
}

/* 説明カード */
#cs-app .cs-info-section {
background: #fff;
border-radius: 10px;
padding: 16px;
border: 1px solid #e0e4ff;
margin-bottom: 20px;
}

#cs-app .cs-info-section h3 {
font-size: 0.9rem;
font-weight: 700;
color: #3a3aff;
margin-bottom: 10px;
}

#cs-app .cs-info-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 10px;
}

#cs-app .cs-info-card {
border-radius: 8px;
padding: 12px;
font-size: 0.82rem;
line-height: 1.6;
}

#cs-app .cs-info-card.cs-c-inline  { background: #fef2f2; border: 1px solid #fca5a5; }
#cs-app .cs-info-card.cs-c-id      { background: #f5f3ff; border: 1px solid #c4b5fd; }
#cs-app .cs-info-card.cs-c-class   { background: #eff6ff; border: 1px solid #93c5fd; }
#cs-app .cs-info-card.cs-c-element { background: #f0fdf4; border: 1px solid #6ee7b7; }

#cs-app .cs-info-card-title {
font-weight: 700;
margin-bottom: 4px;
font-size: 0.85rem;
}

#cs-app .cs-info-card.cs-c-inline  .cs-info-card-title { color: #ef4444; }
#cs-app .cs-info-card.cs-c-id      .cs-info-card-title { color: #7c3aed; }
#cs-app .cs-info-card.cs-c-class   .cs-info-card-title { color: #3a3aff; }
#cs-app .cs-info-card.cs-c-element .cs-info-card-title { color: #059669; }

#cs-app .cs-info-card code {
background: rgba(0,0,0,0.06);
border-radius: 3px;
padding: 0 3px;
font-size: 0.78rem;
font-family: "Courier New", monospace;
}

/* エラー */
#cs-app .cs-error {
background: #fef2f2;
border: 1px solid #fca5a5;
border-radius: 8px;
padding: 10px 14px;
color: #ef4444;
font-size: 0.85rem;
margin-bottom: 16px;
display: none;
}

#cs-app .cs-error.cs-visible { display: block; }

/* レスポンシブ */
@media (max-width: 600px) {
#cs-app { padding: 14px; }
#cs-app .cs-input-row { flex-wrap: wrap; }
#cs-app .cs-score-boxes { gap: 8px; }
#cs-app .cs-score-value { width: 52px; height: 52px; font-size: 1.4rem; }
#cs-app .cs-bar-label { width: 86px; font-size: 0.7rem; }
#cs-app .cs-info-grid { grid-template-columns: 1fr; }
}
</style>

<h2 class="cs-title">CSS詳細度計算ツール</h2>
<p class="cs-subtitle">CSSセレクタを入力するとスコア (a, b, c, d) を即座に計算。複数セレクタを比較してカスケードの優先順位を視覚的に確認できます。</p>

<!-- 入力 -->
<div class="cs-input-row">
<input type="text" id="cs-selector-input" placeholder='例: #nav .menu > li:hover' autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false">
<button class="cs-btn" onclick="csCalc()">計算</button>
<button class="cs-btn-secondary" onclick="csAddToCompare()">+ 比較追加</button>
</div>

<div class="cs-error" id="cs-error"></div>

<!-- スコアパネル -->
<div class="cs-score-panel" id="cs-score-panel">
<div class="cs-score-label">詳細度スコア (a, b, c, d)</div>
<div class="cs-score-boxes">
<div class="cs-score-box">
<div class="cs-score-value cs-inline" id="cs-val-a">0</div>
<div class="cs-score-type">インライン<br>スタイル (a)</div>
</div>
<div class="cs-score-sep">,</div>
<div class="cs-score-box">
<div class="cs-score-value cs-ids" id="cs-val-b">0</div>
<div class="cs-score-type">IDセレクタ (b)</div>
</div>
<div class="cs-score-sep">,</div>
<div class="cs-score-box">
<div class="cs-score-value cs-classes" id="cs-val-c">0</div>
<div class="cs-score-type">クラス・<br>属性・<br>擬似クラス (c)</div>
</div>
<div class="cs-score-sep">,</div>
<div class="cs-score-box">
<div class="cs-score-value cs-elements" id="cs-val-d">0</div>
<div class="cs-score-type">要素・<br>擬似要素 (d)</div>
</div>
</div>
<div class="cs-score-total" id="cs-score-total">(0, 0, 0, 0)</div>
<div class="cs-bars">
<div class="cs-bar-row">
<div class="cs-bar-label">インライン (a)</div>
<div class="cs-bar-track"><div class="cs-bar-fill cs-inline" id="cs-bar-a" style="width:0%"></div></div>
<div class="cs-bar-count" id="cs-bc-a">0</div>
</div>
<div class="cs-bar-row">
<div class="cs-bar-label">ID (b)</div>
<div class="cs-bar-track"><div class="cs-bar-fill cs-ids" id="cs-bar-b" style="width:0%"></div></div>
<div class="cs-bar-count" id="cs-bc-b">0</div>
</div>
<div class="cs-bar-row">
<div class="cs-bar-label">クラス等 (c)</div>
<div class="cs-bar-track"><div class="cs-bar-fill cs-classes" id="cs-bar-c" style="width:0%"></div></div>
<div class="cs-bar-count" id="cs-bc-c">0</div>
</div>
<div class="cs-bar-row">
<div class="cs-bar-label">要素等 (d)</div>
<div class="cs-bar-track"><div class="cs-bar-fill cs-elements" id="cs-bar-d" style="width:0%"></div></div>
<div class="cs-bar-count" id="cs-bc-d">0</div>
</div>
</div>
</div>

<!-- 内訳 -->
<div class="cs-breakdown" id="cs-breakdown">
<h3>セレクタの内訳</h3>
<div class="cs-tokens" id="cs-tokens"></div>
<div class="cs-legend">
<div class="cs-legend-item"><div class="cs-legend-dot" style="background:#ef4444"></div> インラインスタイル</div>
<div class="cs-legend-item"><div class="cs-legend-dot" style="background:#8b5cf6"></div> IDセレクタ</div>
<div class="cs-legend-item"><div class="cs-legend-dot" style="background:#3a3aff"></div> クラス / 属性 / 擬似クラス</div>
<div class="cs-legend-item"><div class="cs-legend-dot" style="background:#10b981"></div> 要素 / 擬似要素</div>
<div class="cs-legend-item"><div class="cs-legend-dot" style="background:#ccc"></div> 結合子（カウントなし）</div>
</div>
</div>

<!-- 比較 -->
<div class="cs-compare-section">
<h3>セレクタ比較 — 詳細度順にソート</h3>
<div class="cs-compare-list" id="cs-compare-list">
<div class="cs-empty-compare" id="cs-compare-empty">セレクタがまだ追加されていません。セレクタを入力して「+ 比較追加」をクリックしてください。</div>
</div>
<div class="cs-compare-actions">
<button class="cs-btn-secondary" onclick="csSortCompare()">詳細度順にソート</button>
<button class="cs-btn-secondary" onclick="csClearCompare()">すべてクリア</button>
</div>
</div>

<!-- 例 -->
<div class="cs-examples-section">
<h3>よくある例 — クリックで計算</h3>
<div class="cs-examples-grid" id="cs-examples-grid"></div>
</div>

<!-- 説明 -->
<div class="cs-info-section">
<h3>CSS詳細度の仕組み</h3>
<div class="cs-info-grid">
<div class="cs-info-card cs-c-inline">
<div class="cs-info-card-title">a — インラインスタイル</div>
HTML要素に直接書かれたスタイル (<code>style="..."</code>)。最も優先度が高く、セレクタより常に勝ります。
</div>
<div class="cs-info-card cs-c-id">
<div class="cs-info-card-title">b — IDセレクタ</div>
<code>#id</code> 形式のセレクタ。非常に高い詳細度。クラスや要素が何個あっても1つのIDが勝ります。
</div>
<div class="cs-info-card cs-c-class">
<div class="cs-info-card-title">c — クラス・属性・擬似クラス</div>
クラス (<code>.class</code>)、属性 (<code>[attr]</code>)、擬似クラス (<code>:hover</code>、<code>:nth-child()</code>) などが対象です。
</div>
<div class="cs-info-card cs-c-element">
<div class="cs-info-card-title">d — 要素・擬似要素</div>
タイプセレクタ (<code>div</code>、<code>p</code>) と擬似要素 (<code>::before</code>、<code>::after</code>)。最も低い詳細度です。
</div>
</div>
</div>

<script>
(function() {
var EXAMPLES = [
{ sel: '*',                           label: 'ユニバーサルセレクタ' },
{ sel: 'div',                         label: '要素セレクタ' },
{ sel: 'div p',                       label: '子孫結合子' },
{ sel: 'div > p',                     label: '子結合子' },
{ sel: '.menu',                       label: 'クラスセレクタ' },
{ sel: '#header',                     label: 'IDセレクタ' },
{ sel: 'a:hover',                     label: '要素 + 擬似クラス' },
{ sel: '.nav > li.active',            label: 'クラス + 子 + クラス' },
{ sel: '#main .content p',            label: 'ID + クラス + 要素' },
{ sel: 'input[type="text"]',          label: '属性セレクタ' },
{ sel: 'ul li:first-child',           label: '擬似クラス :first-child' },
{ sel: 'p::first-line',              label: '擬似要素' },
{ sel: '#app .sidebar ul li a:hover', label: '複合セレクタ' },
{ sel: ':not(.disabled)',             label: ':not() 擬似クラス' },
{ sel: '[data-active="true"]',        label: '属性値セレクタ' },
{ sel: 'h1 + p',                      label: '隣接兄弟結合子' }
];

var csCompareList = [];

function csParseSelector(sel) {
sel = sel.trim();
var a = 0;
var b = 0;
var c = 0;
var d = 0;
var tokens = [];

var s = sel;

// 擬似要素
var pseudoElements = /:{1,2}(before|after|first-line|first-letter|selection|placeholder|marker|backdrop|file-selector-button|cue|part|slotted)(\([^)]*\))?/gi;
s = s.replace(pseudoElements, function(m) {
d++;
tokens.push({ text: m, type: 'element' });
return '';
});

// :is(), :not(), :has(), :where()
s = s.replace(/:(?:not|is|has|matches)\(([^)]*)\)/gi, function(m, inner) {
var funcName = m.match(/:([a-z-]+)/i)[1].toLowerCase();
if (funcName === 'where') {
tokens.push({ text: m, type: 'combinator' });
return '';
}
var args = inner.split(',').map(function(a) { return a.trim(); });
var best = { a:0, b:0, c:0, d:0 };
args.forEach(function(arg) {
var r = csParseSelector(arg);
if (csCompareScore(r, best) > 0) best = r;
});
b += best.b;
c += best.c;
d += best.d;
tokens.push({ text: m, type: best.b > 0 ? 'id' : (best.c > 0 ? 'class' : 'element') });
return '';
});

var remaining = s;

// ID
remaining = remaining.replace(/#[a-zA-Z_-][a-zA-Z0-9_-]*/g, function(m) {
b++;
tokens.push({ text: m, type: 'id' });
return '';
});

// クラス
remaining = remaining.replace(/\.[a-zA-Z_-][a-zA-Z0-9_-]*/g, function(m) {
c++;
tokens.push({ text: m, type: 'class' });
return '';
});

// 属性
remaining = remaining.replace(/\[[^\]]*\]/g, function(m) {
c++;
tokens.push({ text: m, type: 'class' });
return '';
});

// 擬似クラス
remaining = remaining.replace(/:[a-zA-Z_-][a-zA-Z0-9_-]*(?:\([^)]*\))?/g, function(m) {
c++;
tokens.push({ text: m, type: 'class' });
return '';
});

// 要素・ユニバーサル
remaining = remaining.replace(/\*|[a-zA-Z][a-zA-Z0-9-]*/g, function(m) {
if (m === '*') {
tokens.push({ text: m, type: 'combinator' });
} else {
d++;
tokens.push({ text: m, type: 'element' });
}
return '';
});

var combinatorChars = remaining.replace(/\s+/g, ' ').trim();
if (combinatorChars) {
combinatorChars.split('').forEach(function(ch) {
if (ch !== ' ') tokens.push({ text: ch, type: 'combinator' });
});
}

return { a: a, b: b, c: c, d: d, tokens: tokens, selector: sel };
}

function csCompareScore(x, y) {
if (x.a !== y.a) return x.a - y.a;
if (x.b !== y.b) return x.b - y.b;
if (x.c !== y.c) return x.c - y.c;
return x.d - y.d;
}

function csScoreStr(r) {
return '(' + r.a + ', ' + r.b + ', ' + r.c + ', ' + r.d + ')';
}

function csNumericScore(r) {
return r.a * 1000000 + r.b * 10000 + r.c * 100 + r.d;
}

function csCalc() {
var input = document.getElementById('cs-selector-input').value.trim();
var errorEl = document.getElementById('cs-error');
if (!input) {
errorEl.textContent = 'CSSセレクタを入力してください。';
errorEl.classList.add('cs-visible');
return;
}
errorEl.classList.remove('cs-visible');

var result = csParseSelector(input);

document.getElementById('cs-val-a').textContent = result.a;
document.getElementById('cs-val-b').textContent = result.b;
document.getElementById('cs-val-c').textContent = result.c;
document.getElementById('cs-val-d').textContent = result.d;
document.getElementById('cs-score-total').textContent = csScoreStr(result);

var maxVal = Math.max(result.a, result.b, result.c, result.d, 1);
function pct(v) { return Math.round(v / maxVal * 100) + '%'; }
document.getElementById('cs-bar-a').style.width = pct(result.a);
document.getElementById('cs-bar-b').style.width = pct(result.b);
document.getElementById('cs-bar-c').style.width = pct(result.c);
document.getElementById('cs-bar-d').style.width = pct(result.d);
document.getElementById('cs-bc-a').textContent = result.a;
document.getElementById('cs-bc-b').textContent = result.b;
document.getElementById('cs-bc-c').textContent = result.c;
document.getElementById('cs-bc-d').textContent = result.d;

document.getElementById('cs-score-panel').classList.add('cs-visible');

var tokensEl = document.getElementById('cs-tokens');
tokensEl.innerHTML = '';
var displayResult = csParseSelector(input);
var typeMap = { inline: 'cs-t-inline', id: 'cs-t-id', class: 'cs-t-class', element: 'cs-t-element', combinator: 'cs-t-combinator' };
var typeLabel = { inline: 'インライン', id: 'IDセレクタ', class: 'クラス/属性/擬似クラス', element: '要素/擬似要素', combinator: '結合子' };

displayResult.tokens.forEach(function(tok) {
var span = document.createElement('span');
span.className = 'cs-token ' + (typeMap[tok.type] || 'cs-t-combinator');
var dot = document.createElement('span');
dot.className = 'cs-token-dot';
span.appendChild(dot);
span.appendChild(document.createTextNode(tok.text));
span.title = typeLabel[tok.type] || '';
tokensEl.appendChild(span);
});

document.getElementById('cs-breakdown').classList.add('cs-visible');
}

function csAddToCompare() {
var input = document.getElementById('cs-selector-input').value.trim();
var errorEl = document.getElementById('cs-error');
if (!input) {
errorEl.textContent = '比較するCSSセレクタを入力してください。';
errorEl.classList.add('cs-visible');
return;
}
errorEl.classList.remove('cs-visible');

for (var i = 0; i < csCompareList.length; i++) {
if (csCompareList[i].selector === input) return;
}

var result = csParseSelector(input);
csCompareList.push(result);
csCalc();
csRenderCompare();
}

function csRenderCompare() {
var listEl = document.getElementById('cs-compare-list');
var emptyEl = document.getElementById('cs-compare-empty');

if (csCompareList.length === 0) {
listEl.innerHTML = '';
listEl.appendChild(emptyEl);
emptyEl.style.display = '';
return;
}

emptyEl.style.display = 'none';
listEl.innerHTML = '';

var sorted = csCompareList.slice().sort(function(x, y) { return csCompareScore(y, x); });
var winnerScore = csNumericScore(sorted[0]);

sorted.forEach(function(item, idx) {
var rank = idx + 1;
var div = document.createElement('div');
div.className = 'cs-compare-item' + (csNumericScore(item) === winnerScore ? ' cs-winner' : '');

var rankEl = document.createElement('div');
rankEl.className = 'cs-compare-rank' + (rank <= 3 ? ' cs-rank-' + rank : '');
rankEl.textContent = rank;

var selEl = document.createElement('div');
selEl.className = 'cs-compare-selector';
selEl.textContent = item.selector;

var scoreEl = document.createElement('div');
scoreEl.className = 'cs-compare-score';
scoreEl.textContent = csScoreStr(item);

var delBtn = document.createElement('button');
delBtn.className = 'cs-compare-del';
delBtn.textContent = '\u00d7';
delBtn.title = '削除';
(function(sel) {
delBtn.onclick = function() {
csCompareList = csCompareList.filter(function(x) { return x.selector !== sel; });
csRenderCompare();
};
})(item.selector);

div.appendChild(rankEl);
div.appendChild(selEl);
div.appendChild(scoreEl);
div.appendChild(delBtn);
listEl.appendChild(div);
});
}

function csSortCompare() {
csCompareList.sort(function(x, y) { return csCompareScore(y, x); });
csRenderCompare();
}

function csClearCompare() {
csCompareList = [];
csRenderCompare();
}

function csRenderExamples() {
var grid = document.getElementById('cs-examples-grid');
EXAMPLES.forEach(function(ex) {
var result = csParseSelector(ex.sel);
var btn = document.createElement('button');
btn.className = 'cs-example-btn';
var sel = document.createElement('div');
sel.className = 'cs-example-selector';
sel.textContent = ex.sel;
var score = document.createElement('div');
score.className = 'cs-example-score';
score.textContent = ex.label + ' — ' + csScoreStr(result);
btn.appendChild(sel);
btn.appendChild(score);
btn.onclick = function() {
document.getElementById('cs-selector-input').value = ex.sel;
csCalc();
window.scrollTo({ top: document.getElementById('cs-score-panel').getBoundingClientRect().top + window.scrollY - 80, behavior: 'smooth' });
};
grid.appendChild(btn);
});
}

window.csCalc = csCalc;
window.csAddToCompare = csAddToCompare;
window.csSortCompare = csSortCompare;
window.csClearCompare = csClearCompare;

document.getElementById('cs-selector-input').addEventListener('keydown', function(e) {
if (e.key === 'Enter') csCalc();
});

csRenderExamples();
csRenderCompare();
})();
</script>
</div>

---

### 関連ツール

> グリッドレイアウトを視覚的に構築 → [CSS Gridジェネレーター](/ja/tools/css-grid-generator/)

> Flexboxレイアウトを生成 → [CSS Flexboxジェネレーター](/ja/tools/flexbox-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
