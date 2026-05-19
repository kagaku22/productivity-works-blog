---
title: "タイポグラフィスケールジェネレーター — モジュラー書体システム"
date: 2025-07-02
description: "Webデザイン用モジュラータイポグラフィスケールを生成。比率・ベースサイズを選択して全見出しサイズをプレビュー。rem/px値・行間付きCSSをコピー。"
categories: ["無料ツール"]
slug: "typography-scale"
ShowToc: false
cover:
  image: "/images/covers/typography-scale-ja.png"
  alt: "タイポグラフィスケールジェネレーター"
---

<div id="ts-app2">

<style>
#ts-app2 *,
#ts-app2 *::before,
#ts-app2 *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#ts-app2 {
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1a1a2e;
line-height: 1.7;
max-width: 900px;
margin: 0 auto;
padding: 0 16px;
}

#ts-app2 .ts-card {
background: #ffffff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}

#ts-app2 .ts-hero {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: #fff;
border-radius: 14px;
padding: 36px 28px 28px;
margin-bottom: 24px;
text-align: center;
}

#ts-app2 .ts-hero h2 {
font-size: 1.65rem;
font-weight: 800;
margin-bottom: 8px;
letter-spacing: -0.01em;
}

#ts-app2 .ts-hero p {
font-size: 0.95rem;
opacity: 0.88;
}

#ts-app2 .ts-section-title {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #7c3aed;
margin-bottom: 14px;
}

#ts-app2 .ts-controls-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
gap: 16px;
margin-bottom: 16px;
}

#ts-app2 .ts-field label {
display: block;
font-size: 0.8rem;
font-weight: 600;
color: #374151;
margin-bottom: 6px;
}

#ts-app2 .ts-field input[type="number"],
#ts-app2 .ts-field select {
width: 100%;
padding: 10px 14px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 0.95rem;
background: #f9fafb;
color: #1a1a2e;
transition: border-color 0.2s;
appearance: none;
-webkit-appearance: none;
}

#ts-app2 .ts-field input[type="number"]:focus,
#ts-app2 .ts-field select:focus {
outline: none;
border-color: #7c3aed;
background: #fff;
}

#ts-app2 .ts-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 6px;
}

#ts-app2 .ts-preset-btn {
padding: 6px 14px;
border-radius: 20px;
border: 1.5px solid #d1d5db;
background: #f9fafb;
font-size: 0.8rem;
font-weight: 600;
color: #374151;
cursor: pointer;
transition: all 0.15s;
}

#ts-app2 .ts-preset-btn:hover,
#ts-app2 .ts-preset-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

#ts-app2 .ts-unit-toggle {
display: flex;
gap: 6px;
flex-wrap: wrap;
}

#ts-app2 .ts-unit-btn {
padding: 6px 16px;
border-radius: 8px;
border: 1.5px solid #d1d5db;
background: #f9fafb;
font-size: 0.82rem;
font-weight: 700;
color: #374151;
cursor: pointer;
transition: all 0.15s;
}

#ts-app2 .ts-unit-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

#ts-app2 .ts-scale-table {
width: 100%;
border-collapse: collapse;
margin-bottom: 8px;
}

#ts-app2 .ts-scale-table th {
font-size: 0.75rem;
font-weight: 700;
color: #6b7280;
text-transform: uppercase;
letter-spacing: 0.04em;
padding: 8px 12px;
text-align: left;
border-bottom: 2px solid #e5e7eb;
background: #f9fafb;
}

#ts-app2 .ts-scale-table td {
padding: 10px 12px;
border-bottom: 1px solid #f0f0f0;
vertical-align: middle;
}

#ts-app2 .ts-scale-table tr:last-child td {
border-bottom: none;
}

#ts-app2 .ts-scale-table tr:hover td {
background: #faf5ff;
}

#ts-app2 .ts-tag-label {
display: inline-block;
background: #ede9fe;
color: #7c3aed;
font-size: 0.75rem;
font-weight: 700;
padding: 2px 8px;
border-radius: 5px;
letter-spacing: 0.04em;
}

#ts-app2 .ts-size-value {
font-family: "SF Mono", "Fira Code", "Fira Mono", monospace;
font-size: 0.82rem;
color: #374151;
}

#ts-app2 .ts-lh-value {
font-size: 0.78rem;
color: #6b7280;
}

#ts-app2 .ts-preview-col {
max-width: 240px;
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
}

#ts-app2 .ts-preview-text {
color: #1a1a2e;
font-weight: 600;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
display: block;
}

#ts-app2 .ts-css-output {
position: relative;
background: #1e1e2e;
border-radius: 10px;
padding: 20px;
overflow: auto;
max-height: 400px;
}

#ts-app2 .ts-css-output pre {
font-family: "SF Mono", "Fira Code", "Fira Mono", monospace;
font-size: 0.82rem;
line-height: 1.7;
color: #cdd6f4;
white-space: pre;
margin: 0;
}

#ts-app2 .ts-css-output .tok-prop   { color: #89b4fa; }
#ts-app2 .ts-css-output .tok-val    { color: #a6e3a1; }
#ts-app2 .tok-selector              { color: #cba6f7; }
#ts-app2 .tok-comment               { color: #6c7086; font-style: italic; }
#ts-app2 .tok-brace                 { color: #f38ba8; }

#ts-app2 .ts-copy-btn {
position: absolute;
top: 14px;
right: 14px;
padding: 6px 14px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 7px;
font-size: 0.78rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
letter-spacing: 0.03em;
}

#ts-app2 .ts-copy-btn:hover { background: #6d28d9; }
#ts-app2 .ts-copy-btn.copied { background: #059669; }

#ts-app2 .ts-crosslinks {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 4px;
}

#ts-app2 .ts-crosslinks a {
color: #7c3aed;
text-decoration: none;
font-size: 0.85rem;
font-weight: 600;
padding: 5px 12px;
border: 1.5px solid #ddd6fe;
border-radius: 8px;
background: #faf5ff;
transition: all 0.15s;
}

#ts-app2 .ts-crosslinks a:hover {
background: #7c3aed;
color: #fff;
border-color: #7c3aed;
}

#ts-app2 .ts-info-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 10px;
}

#ts-app2 .ts-info-chip {
background: #f0fdf4;
border: 1px solid #bbf7d0;
color: #166534;
font-size: 0.78rem;
font-weight: 600;
padding: 4px 12px;
border-radius: 20px;
}

#ts-app2 .ts-freee-cta {
background: linear-gradient(135deg, #1e40af 0%, #1d4ed8 100%);
color: #fff;
border-radius: 12px;
padding: 24px 28px;
margin-bottom: 20px;
display: flex;
align-items: center;
gap: 20px;
flex-wrap: wrap;
}

#ts-app2 .ts-freee-cta-text h3 {
font-size: 1rem;
font-weight: 800;
margin-bottom: 4px;
}

#ts-app2 .ts-freee-cta-text p {
font-size: 0.85rem;
opacity: 0.9;
line-height: 1.5;
}

#ts-app2 .ts-freee-btn {
display: inline-block;
padding: 10px 24px;
background: #fff;
color: #1d4ed8;
font-weight: 800;
font-size: 0.88rem;
border-radius: 8px;
text-decoration: none;
white-space: nowrap;
transition: opacity 0.15s;
flex-shrink: 0;
}

#ts-app2 .ts-freee-btn:hover {
opacity: 0.88;
}

@media (max-width: 600px) {
#ts-app2 .ts-hero h2 { font-size: 1.2rem; }
#ts-app2 .ts-controls-grid { grid-template-columns: 1fr; }
#ts-app2 .ts-scale-table th:nth-child(4),
#ts-app2 .ts-scale-table td:nth-child(4) { display: none; }
#ts-app2 .ts-preview-col { max-width: 100px; }
#ts-app2 .ts-freee-cta { flex-direction: column; text-align: center; }
}
</style>

<div class="ts-hero">
<h2>タイポグラフィスケールジェネレーター</h2>
<p>モジュラーな比率で統一感のある文字サイズ体系を自動生成します</p>
</div>

<div class="ts-card">
<div class="ts-section-title">プリセット</div>
<div class="ts-presets">
<button class="ts-preset-btn" data-preset="blog">ブログ</button>
<button class="ts-preset-btn" data-preset="app">アプリUI</button>
<button class="ts-preset-btn" data-preset="docs">ドキュメント</button>
<button class="ts-preset-btn" data-preset="landing">ランディングページ</button>
</div>
</div>

<div class="ts-card">
<div class="ts-section-title">設定</div>
<div class="ts-controls-grid">
<div class="ts-field">
<label for="ts-base-size">ベースフォントサイズ（px）</label>
<input type="number" id="ts-base-size" value="16" min="10" max="24" step="1">
</div>
<div class="ts-field">
<label for="ts-ratio">スケール比率</label>
<select id="ts-ratio">
<option value="1.067">短2度（Minor Second） — 1.067</option>
<option value="1.125">長2度（Major Second） — 1.125</option>
<option value="1.2">短3度（Minor Third） — 1.200</option>
<option value="1.25" selected>長3度（Major Third） — 1.250</option>
<option value="1.333">完全4度（Perfect Fourth） — 1.333</option>
<option value="1.414">増4度（Augmented Fourth） — 1.414</option>
<option value="1.5">完全5度（Perfect Fifth） — 1.500</option>
<option value="1.618">黄金比（Golden Ratio） — 1.618</option>
</select>
</div>
</div>
<div class="ts-field">
<label>出力単位</label>
<div class="ts-unit-toggle">
<button class="ts-unit-btn active" data-unit="rem">rem</button>
<button class="ts-unit-btn" data-unit="px">px</button>
<button class="ts-unit-btn" data-unit="em">em</button>
</div>
</div>
</div>

<div class="ts-card">
<div class="ts-section-title">タイプスケール プレビュー</div>
<div style="overflow-x:auto;">
<table class="ts-scale-table" id="ts-scale-table">
<thead>
<tr>
<th>レベル</th>
<th>サイズ</th>
<th>行間</th>
<th>プレビュー</th>
</tr>
</thead>
<tbody id="ts-scale-tbody"></tbody>
</table>
</div>
<div class="ts-info-row" id="ts-info-row"></div>
</div>

<div class="ts-card">
<div class="ts-section-title">CSS 出力</div>
<div class="ts-css-output">
<button class="ts-copy-btn" id="ts-copy-btn">CSSをコピー</button>
<pre id="ts-css-pre"></pre>
</div>
</div>

<div class="ts-freee-cta">
<div class="ts-freee-cta-text">
<h3>freeeで経理・会計をもっとスマートに</h3>
<p>デザイン作業の請求書発行・経費管理もクラウドで完結。フリーランス・個人事業主に最適な会計ソフト。</p>
</div>
<a class="ts-freee-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>

<div class="ts-card">
<div class="ts-section-title">関連ツール</div>
<div class="ts-crosslinks">
<a href="/ja/tools/css-variables-generator/">CSS変数ジェネレーター</a>
<a href="/ja/tools/font-pair-suggester/">フォントペアサジェスター</a>
<a href="/ja/tools/reading-time-calculator/">読了時間計算ツール</a>
</div>
</div>

<script>
(function() {
'use strict';

var LEVELS = [
{ label: 'h1', step: 5, previewText: '見出し1 — メインタイトル' },
{ label: 'h2', step: 4, previewText: '見出し2 — セクションタイトル' },
{ label: 'h3', step: 3, previewText: '見出し3 — サブセクション' },
{ label: 'h4', step: 2, previewText: '見出し4 — 小見出し' },
{ label: 'h5', step: 1, previewText: '見出し5 — キャプション見出し' },
{ label: 'body', step: 0, previewText: '本文テキスト — 読みやすい基準サイズ' },
{ label: 'small', step: -1, previewText: '小文字 / 注釈テキスト' },
];

var LINE_HEIGHTS = {
5: 1.1, 4: 1.15, 3: 1.2, 2: 1.25, 1: 1.35, 0: 1.8, '-1': 1.75
};

var PRESETS = {
blog:    { base: 18, ratio: '1.25' },
app:     { base: 14, ratio: '1.2'  },
docs:    { base: 16, ratio: '1.25' },
landing: { base: 18, ratio: '1.333' },
};

var currentUnit = 'rem';

var baseInput = document.getElementById('ts-base-size');
var ratioSel  = document.getElementById('ts-ratio');
var tbody     = document.getElementById('ts-scale-tbody');
var cssPre    = document.getElementById('ts-css-pre');
var copyBtn   = document.getElementById('ts-copy-btn');
var infoRow   = document.getElementById('ts-info-row');

function calcSize(base, ratio, step) {
return base * Math.pow(ratio, step);
}

function formatSize(px, unit, base) {
if (unit === 'px')  return px.toFixed(2) + 'px';
if (unit === 'rem') return (px / base).toFixed(4) + 'rem';
if (unit === 'em')  return (px / base).toFixed(4) + 'em';
return px.toFixed(2) + 'px';
}

function render() {
var base  = parseFloat(baseInput.value) || 16;
var ratio = parseFloat(ratioSel.value)  || 1.25;

var tbodyHtml = '';
LEVELS.forEach(function(lvl) {
var px = calcSize(base, ratio, lvl.step);
var lh = LINE_HEIGHTS[lvl.step] || 1.6;
var sizeStr = formatSize(px, currentUnit, base);
var previewPx = Math.round(px);

tbodyHtml += '<tr>' +
'<td><span class="ts-tag-label">' + lvl.label + '</span></td>' +
'<td><span class="ts-size-value">' + sizeStr + '</span></td>' +
'<td><span class="ts-lh-value">' + lh.toFixed(2) + '</span></td>' +
'<td class="ts-preview-col"><span class="ts-preview-text" style="font-size:' + Math.min(previewPx, 48) + 'px;line-height:' + lh + '">' + lvl.previewText + '</span></td>' +
'</tr>';
});
tbody.innerHTML = tbodyHtml;

var ratioLabel = ratioSel.options[ratioSel.selectedIndex].text.split('—')[0].trim();
infoRow.innerHTML =
'<span class="ts-info-chip">ベース: ' + base + 'px</span>' +
'<span class="ts-info-chip">比率: ' + ratio + '</span>' +
'<span class="ts-info-chip">' + ratioLabel + '</span>' +
'<span class="ts-info-chip">単位: ' + currentUnit + '</span>';

renderCSS(base, ratio);
}

function renderCSS(base, ratio) {
var lines = [];
var ratioLabel = ratioSel.options[ratioSel.selectedIndex].text.split('—')[0].trim();
lines.push('<span class="tok-comment">/* タイポグラフィスケール — ProductivityWorksで生成 */</span>');
lines.push('<span class="tok-comment">/* ベース: ' + base + 'px | 比率: ' + ratio + ' (' + ratioLabel + ') */</span>');
lines.push('');
lines.push('<span class="tok-selector">:root</span> <span class="tok-brace">{</span>');

LEVELS.forEach(function(lvl) {
var px = calcSize(base, ratio, lvl.step);
var lh = LINE_HEIGHTS[lvl.step] || 1.6;
var sizeStr = formatSize(px, currentUnit, base);
lines.push('  <span class="tok-prop">--font-size-' + lvl.label + '</span>: <span class="tok-val">' + sizeStr + '</span>;');
lines.push('  <span class="tok-prop">--line-height-' + lvl.label + '</span>: <span class="tok-val">' + lh.toFixed(2) + '</span>;');
});

lines.push('<span class="tok-brace">}</span>');
lines.push('');

LEVELS.filter(function(l) { return l.label.startsWith('h'); }).forEach(function(lvl) {
var px = calcSize(base, ratio, lvl.step);
var lh = LINE_HEIGHTS[lvl.step] || 1.5;
var sizeStr = formatSize(px, currentUnit, base);
lines.push('<span class="tok-selector">' + lvl.label + '</span> <span class="tok-brace">{</span>');
lines.push('  <span class="tok-prop">font-size</span>: <span class="tok-val">' + sizeStr + '</span>;');
lines.push('  <span class="tok-prop">line-height</span>: <span class="tok-val">' + lh.toFixed(2) + '</span>;');
lines.push('<span class="tok-brace">}</span>');
lines.push('');
});

lines.push('<span class="tok-selector">body</span> <span class="tok-brace">{</span>');
lines.push('  <span class="tok-prop">font-size</span>: <span class="tok-val">' + formatSize(base, currentUnit, base) + '</span>;');
lines.push('  <span class="tok-prop">line-height</span>: <span class="tok-val">1.80</span>;');
lines.push('<span class="tok-brace">}</span>');
lines.push('');
lines.push('<span class="tok-selector">small, .text-small</span> <span class="tok-brace">{</span>');
var smallPx = calcSize(base, ratio, -1);
lines.push('  <span class="tok-prop">font-size</span>: <span class="tok-val">' + formatSize(smallPx, currentUnit, base) + '</span>;');
lines.push('  <span class="tok-prop">line-height</span>: <span class="tok-val">1.75</span>;');
lines.push('<span class="tok-brace">}</span>');

cssPre.innerHTML = lines.join('\n');
}

function getPlainCSS() {
var base  = parseFloat(baseInput.value) || 16;
var ratio = parseFloat(ratioSel.value)  || 1.25;
var ratioLabel = ratioSel.options[ratioSel.selectedIndex].text.split('—')[0].trim();
var lines = [];
lines.push('/* タイポグラフィスケール — ProductivityWorksで生成 */');
lines.push('/* ベース: ' + base + 'px | 比率: ' + ratio + ' (' + ratioLabel + ') */');
lines.push('');
lines.push(':root {');
LEVELS.forEach(function(lvl) {
var px = calcSize(base, ratio, lvl.step);
var lh = LINE_HEIGHTS[lvl.step] || 1.6;
var sizeStr = formatSize(px, currentUnit, base);
lines.push('  --font-size-' + lvl.label + ': ' + sizeStr + ';');
lines.push('  --line-height-' + lvl.label + ': ' + lh.toFixed(2) + ';');
});
lines.push('}');
lines.push('');
LEVELS.filter(function(l) { return l.label.startsWith('h'); }).forEach(function(lvl) {
var px = calcSize(base, ratio, lvl.step);
var lh = LINE_HEIGHTS[lvl.step] || 1.5;
var sizeStr = formatSize(px, currentUnit, base);
lines.push(lvl.label + ' {');
lines.push('  font-size: ' + sizeStr + ';');
lines.push('  line-height: ' + lh.toFixed(2) + ';');
lines.push('}');
lines.push('');
});
lines.push('body {');
lines.push('  font-size: ' + formatSize(base, currentUnit, base) + ';');
lines.push('  line-height: 1.80;');
lines.push('}');
lines.push('');
lines.push('small, .text-small {');
var smallPx = calcSize(base, ratio, -1);
lines.push('  font-size: ' + formatSize(smallPx, currentUnit, base) + ';');
lines.push('  line-height: 1.75;');
lines.push('}');
return lines.join('\n');
}

// コピーボタン
copyBtn.addEventListener('click', function() {
var text = getPlainCSS();
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() {
copyBtn.textContent = 'コピー完了！';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'CSSをコピー';
copyBtn.classList.remove('copied');
}, 2000);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.focus();
ta.select();
try { document.execCommand('copy'); } catch(e) {}
document.body.removeChild(ta);
copyBtn.textContent = 'コピー完了！';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'CSSをコピー';
copyBtn.classList.remove('copied');
}, 2000);
}
});

// 単位切り替え
document.querySelectorAll('#ts-app2 .ts-unit-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#ts-app2 .ts-unit-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
currentUnit = btn.dataset.unit;
render();
});
});

// プリセットボタン
document.querySelectorAll('#ts-app2 .ts-preset-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#ts-app2 .ts-preset-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
var p = PRESETS[btn.dataset.preset];
if (p) {
baseInput.value = p.base;
ratioSel.value  = p.ratio;
render();
}
});
});

// 入力監視
baseInput.addEventListener('input', render);
ratioSel.addEventListener('change', render);

// 初期描画
render();
})();
</script>

</div>
