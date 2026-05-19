---
title: "CSSアスペクト比ジェネレーター — レスポンシブコンテナ"
date: 2025-04-15
description: "レスポンシブコンテナ用CSS aspect-ratioプロパティを生成。16:9、4:3、1:1等のプリセット。モダンCSS＆padding-bottomフォールバック。コード即コピー。"
categories: ["無料ツール"]
slug: "css-aspect-ratio"
ShowToc: false
cover:
  image: "/images/covers/css-aspect-ratio-ja.png"
  alt: "CSSアスペクト比ジェネレーター"
---

レスポンシブコンテナに最適な CSS `aspect-ratio` プロパティを即座に生成。JavaScriptなしで完璧な縦横比を維持できます。

<div id="ar-app">
<style>
#ar-app *,
#ar-app *::before,
#ar-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#ar-app {
font-family: "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP", -apple-system, BlinkMacSystemFont, sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f8f9fc;
border-radius: 12px;
padding: 28px 24px;
max-width: 760px;
margin: 32px auto;
}
#ar-app h2 {
font-size: 1.2rem;
font-weight: 700;
margin-bottom: 20px;
color: #111827;
}
#ar-app .ar-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 20px;
}
#ar-app .ar-preset-btn {
background: #fff;
border: 2px solid #d1d5db;
border-radius: 8px;
padding: 7px 14px;
font-size: 0.85rem;
font-weight: 700;
cursor: pointer;
color: #374151;
transition: border-color 0.15s, background 0.15s, color 0.15s;
}
#ar-app .ar-preset-btn:hover {
border-color: #6366f1;
color: #6366f1;
}
#ar-app .ar-preset-btn.active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}
#ar-app .ar-inputs {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 20px;
flex-wrap: wrap;
}
#ar-app .ar-inputs label {
font-size: 0.85rem;
font-weight: 600;
color: #6b7280;
white-space: nowrap;
}
#ar-app .ar-inputs input[type="number"] {
width: 90px;
padding: 8px 10px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-size: 1rem;
font-weight: 700;
color: #111827;
text-align: center;
outline: none;
transition: border-color 0.15s;
}
#ar-app .ar-inputs input[type="number"]:focus {
border-color: #6366f1;
}
#ar-app .ar-sep {
font-size: 1.3rem;
font-weight: 700;
color: #9ca3af;
user-select: none;
}
#ar-app .ar-maxwidth-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 24px;
flex-wrap: wrap;
}
#ar-app .ar-maxwidth-row label {
font-size: 0.85rem;
font-weight: 600;
color: #6b7280;
white-space: nowrap;
}
#ar-app .ar-maxwidth-row input[type="range"] {
flex: 1;
min-width: 120px;
max-width: 260px;
accent-color: #6366f1;
cursor: pointer;
}
#ar-app .ar-maxwidth-val {
font-size: 0.9rem;
font-weight: 700;
color: #6366f1;
min-width: 48px;
}
#ar-app .ar-preview-area {
margin-bottom: 24px;
}
#ar-app .ar-preview-label {
font-size: 0.8rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #9ca3af;
margin-bottom: 10px;
}
#ar-app .ar-preview-wrapper {
background: #e5e7eb;
border-radius: 10px;
padding: 16px;
display: flex;
justify-content: center;
align-items: flex-start;
min-height: 80px;
}
#ar-app .ar-preview-box {
background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 50%, #a78bfa 100%);
border-radius: 8px;
display: flex;
align-items: center;
justify-content: center;
color: #fff;
font-weight: 700;
font-size: 1rem;
letter-spacing: 0.03em;
transition: aspect-ratio 0.25s, max-width 0.25s;
}
#ar-app .ar-code-section {
display: flex;
flex-direction: column;
gap: 16px;
}
#ar-app .ar-code-block {
background: #1e1b2e;
border-radius: 10px;
padding: 18px 18px 14px;
position: relative;
}
#ar-app .ar-code-title {
font-size: 0.75rem;
font-weight: 700;
letter-spacing: 0.05em;
color: #a78bfa;
margin-bottom: 10px;
}
#ar-app .ar-code-title .ar-badge {
display: inline-block;
background: #312e81;
color: #c4b5fd;
border-radius: 4px;
font-size: 0.7rem;
padding: 1px 6px;
margin-left: 6px;
font-weight: 600;
vertical-align: middle;
}
#ar-app .ar-code-title .ar-badge-old {
background: #3b2a1a;
color: #fbbf24;
}
#ar-app pre {
margin: 0;
font-family: "Fira Mono", "Consolas", "Monaco", monospace;
font-size: 0.85rem;
line-height: 1.7;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
overflow-x: auto;
}
#ar-app .ar-prop    { color: #93c5fd; }
#ar-app .ar-val     { color: #6ee7b7; }
#ar-app .ar-unit    { color: #fcd34d; }
#ar-app .ar-sel     { color: #f9a8d4; }
#ar-app .ar-comment { color: #6b7280; font-style: italic; }
#ar-app .ar-copy-btn {
position: absolute;
top: 14px;
right: 14px;
background: #312e81;
border: none;
border-radius: 6px;
color: #c4b5fd;
font-size: 0.78rem;
font-weight: 700;
padding: 5px 12px;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#ar-app .ar-copy-btn:hover {
background: #6366f1;
color: #fff;
}
#ar-app .ar-copy-btn.copied {
background: #065f46;
color: #6ee7b7;
}
#ar-app .ar-freee-cta {
margin-top: 32px;
background: linear-gradient(135deg, #1d4ed8 0%, #4338ca 100%);
border-radius: 12px;
padding: 22px 22px 20px;
color: #fff;
}
#ar-app .ar-freee-cta h3 {
font-size: 1rem;
font-weight: 700;
margin-bottom: 8px;
color: #fff;
}
#ar-app .ar-freee-cta p {
font-size: 0.87rem;
line-height: 1.6;
color: #bfdbfe;
margin-bottom: 14px;
}
#ar-app .ar-freee-cta a {
display: inline-block;
background: #fff;
color: #1d4ed8;
font-weight: 700;
font-size: 0.9rem;
padding: 9px 22px;
border-radius: 8px;
text-decoration: none;
transition: background 0.15s, color 0.15s;
}
#ar-app .ar-freee-cta a:hover {
background: #eff6ff;
}
@media (max-width: 520px) {
#ar-app {
padding: 18px 12px;
}
#ar-app .ar-inputs input[type="number"] {
width: 72px;
}
#ar-app .ar-maxwidth-row input[type="range"] {
min-width: 80px;
}
#ar-app pre {
font-size: 0.78rem;
}
}
</style>

<h2>CSSアスペクト比ジェネレーター</h2>

<div class="ar-presets" id="ar-presets">
<button class="ar-preset-btn active" data-w="16" data-h="9">16:9</button>
<button class="ar-preset-btn" data-w="4" data-h="3">4:3</button>
<button class="ar-preset-btn" data-w="1" data-h="1">1:1</button>
<button class="ar-preset-btn" data-w="21" data-h="9">21:9</button>
<button class="ar-preset-btn" data-w="9" data-h="16">9:16</button>
<button class="ar-preset-btn" data-w="3" data-h="2">3:2</button>
<button class="ar-preset-btn" data-w="2" data-h="3">2:3</button>
</div>

<div class="ar-inputs">
<label for="ar-width">横幅</label>
<input type="number" id="ar-width" min="1" max="9999" value="16" />
<span class="ar-sep">:</span>
<label for="ar-height">高さ</label>
<input type="number" id="ar-height" min="1" max="9999" value="9" />
</div>

<div class="ar-maxwidth-row">
<label for="ar-maxwidth">最大幅（max-width）</label>
<input type="range" id="ar-maxwidth" min="10" max="100" value="100" step="5" />
<span class="ar-maxwidth-val" id="ar-maxwidth-val">100%</span>
</div>

<div class="ar-preview-area">
<div class="ar-preview-label">ライブプレビュー</div>
<div class="ar-preview-wrapper" id="ar-preview-wrapper">
<div class="ar-preview-box" id="ar-preview-box">16 : 9</div>
</div>
</div>

<div class="ar-code-section">
<div class="ar-code-block" id="ar-block-modern">
<div class="ar-code-title">
モダンCSS — aspect-ratio プロパティ
<span class="ar-badge">推奨</span>
</div>
<button class="ar-copy-btn" id="ar-copy-modern" onclick="arCopy('modern')">コピー</button>
<pre id="ar-pre-modern"></pre>
</div>

<div class="ar-code-block" id="ar-block-hack">
<div class="ar-code-title">
padding-bottom ハック
<span class="ar-badge ar-badge-old">旧ブラウザ対応</span>
</div>
<button class="ar-copy-btn" id="ar-copy-hack" onclick="arCopy('hack')">コピー</button>
<pre id="ar-pre-hack"></pre>
</div>
</div>

<div class="ar-freee-cta">
<h3>フリーランス・法人の経費管理をもっとスマートに</h3>
<p>CSSを書くだけでなく、事業の経費・請求書・確定申告もスッキリ整理。freee会計なら面倒な経理を自動化できます。</p>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計を無料で試す →</a>
</div>

<script>
(function() {
var wInput  = document.getElementById('ar-width');
var hInput  = document.getElementById('ar-height');
var mwRange = document.getElementById('ar-maxwidth');
var mwVal   = document.getElementById('ar-maxwidth-val');
var preBox  = document.getElementById('ar-preview-box');
var preWrap = document.getElementById('ar-preview-wrapper');
var preModern = document.getElementById('ar-pre-modern');
var preHack   = document.getElementById('ar-pre-hack');
var presets   = document.querySelectorAll('#ar-presets .ar-preset-btn');

function gcd(a, b) { return b === 0 ? a : gcd(b, a % b); }

function simplify(w, h) {
var g = gcd(w, h);
return [w / g, h / g];
}

function hl(cls, text) {
return '<span class="' + cls + '">' + text + '</span>';
}

function render() {
var w  = Math.max(1, parseInt(wInput.value) || 16);
var h  = Math.max(1, parseInt(hInput.value) || 9);
var mw = parseInt(mwRange.value) || 100;
var sw = simplify(w, h);
var ratio = w + ' / ' + h;
var pct   = ((h / w) * 100).toFixed(4).replace(/\.?0+$/, '') + '%';

// プレビュー更新
preBox.style.aspectRatio = ratio;
preBox.style.width = mw + '%';
preBox.style.maxWidth = '100%';
preBox.textContent = sw[0] + ' : ' + sw[1];

// モダンCSS出力
var modern = [
hl('ar-sel', '.responsive-container') + ' {',
'  ' + hl('ar-prop', 'width') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'max-width') + ': ' + hl('ar-val', mw) + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'aspect-ratio') + ': ' + hl('ar-val', w + ' / ' + h) + ';',
'  ' + hl('ar-comment', '/* overflow: hidden; — 必要に応じて追加 */'),
'}'
].join('\n');

preModern.innerHTML = modern;

// padding-bottom ハック出力
var hack = [
hl('ar-comment', '/* ラッパー — padding-bottomトリック */'),
hl('ar-sel', '.ar-wrapper') + ' {',
'  ' + hl('ar-prop', 'position') + ': ' + hl('ar-val', 'relative') + ';',
'  ' + hl('ar-prop', 'width') + ': ' + hl('ar-val', mw) + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'max-width') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'padding-bottom') + ': ' + hl('ar-val', pct) + ';',
'  ' + hl('ar-prop', 'height') + ': ' + hl('ar-val', '0') + ';',
'}',
'',
hl('ar-comment', '/* 内側コンテンツ — 絶対配置 */'),
hl('ar-sel', '.ar-wrapper > *') + ' {',
'  ' + hl('ar-prop', 'position') + ': ' + hl('ar-val', 'absolute') + ';',
'  ' + hl('ar-prop', 'top') + ': ' + hl('ar-val', '0') + ';',
'  ' + hl('ar-prop', 'left') + ': ' + hl('ar-val', '0') + ';',
'  ' + hl('ar-prop', 'width') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'height') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'}'
].join('\n');

preHack.innerHTML = hack;
}

function updatePresetButtons(w, h) {
presets.forEach(function(btn) {
btn.classList.toggle('active',
parseInt(btn.dataset.w) === w && parseInt(btn.dataset.h) === h);
});
}

presets.forEach(function(btn) {
btn.addEventListener('click', function() {
wInput.value = btn.dataset.w;
hInput.value = btn.dataset.h;
updatePresetButtons(parseInt(btn.dataset.w), parseInt(btn.dataset.h));
render();
});
});

wInput.addEventListener('input', function() {
updatePresetButtons(parseInt(wInput.value), parseInt(hInput.value));
render();
});
hInput.addEventListener('input', function() {
updatePresetButtons(parseInt(wInput.value), parseInt(hInput.value));
render();
});

mwRange.addEventListener('input', function() {
mwVal.textContent = mwRange.value + '%';
render();
});

window.addEventListener('resize', function() { render(); });
render();

window.arCopy = function(which) {
var pre = which === 'modern' ? preModern : preHack;
var text = pre.textContent;
var btn  = document.getElementById('ar-copy-' + which);
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() {
btn.textContent = 'コピー完了!';
btn.classList.add('copied');
setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
btn.textContent = 'コピー完了!';
btn.classList.add('copied');
setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
}
};
})();
</script>
</div>

## 使い方

`aspect-ratio` CSSプロパティは、要素のサイズが変わっても横縦比を固定するようブラウザに指示します。`width: 100%` と組み合わせることで、完全なレスポンシブコンテナを実現できます。

```css
.video-container {
width: 100%;
aspect-ratio: 16 / 9;
}
```

**padding-bottom ハック**は、`aspect-ratio` が対応していない古いブラウザ向けの代替手法です。パーセンテージ指定のpadding-bottomが常に親要素の*横幅*を基準に計算されるという仕様を利用しています。

## よく使われるアスペクト比

| 比率 | 主な用途 |
|------|----------|
| 16:9  | HD動画、YouTube埋め込み、ワイドスクリーン |
| 4:3   | 旧来のテレビ、プレゼンテーション |
| 1:1   | 正方形画像、Instagramポスト |
| 21:9  | 映画的/ウルトラワイドのヒーローバナー |
| 9:16  | スマホ縦動画、ストーリーズ、リール |
| 3:2   | 一眼レフ写真、カードサムネイル |

## ブラウザ対応

`aspect-ratio` は全てのモダンブラウザ（Chrome 88+、Firefox 89+、Safari 15+、Edge 88+）でサポートされています。IE11や旧Safari向けには、上記で生成されたpadding-bottomフォールバックをご利用ください。

---

**関連ツール:**
- [アスペクト比計算機](/tools/aspect-ratio-calculator/) — 比率から不明な辺を算出
- [CSS Flexboxジェネレーター](/tools/css-flexbox-generator/) — Flexboxレイアウトをビジュアルで構築
- [画像リサイザー](/tools/image-resizer/) — アスペクト比を維持したまま画像をリサイズ
