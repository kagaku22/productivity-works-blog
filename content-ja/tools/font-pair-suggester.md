---
title: "フォントペアサジェスター — タイポグラフィツール"
date: 2025-07-14
description: "ライブプレビューで美しいフォントペアリングを発見。見出し・本文フォントの組み合わせ提案。サイズ・行間・色を調整。CSSフォントスタックを即コピー。"
categories: ["無料ツール"]
slug: "font-pair-suggester"
ShowToc: false
cover:
  image: "/images/covers/font-pair-suggester-ja.png"
  alt: "フォントペアサジェスター"
---

<div id="fp-app">

<style>
/* ── スコープ済みスタイル：全セレクターは #fp-app プレフィックス ── */
#fp-app *,
#fp-app *::before,
#fp-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#fp-app {
--fp-bg: #ffffff;
--fp-surface: #f8f9fa;
--fp-border: #dee2e6;
--fp-text: #212529;
--fp-text-muted: #6c757d;
--fp-accent: #4f46e5;
--fp-accent-hover: #4338ca;
--fp-preview-bg: #ffffff;
--fp-preview-text: #1a1a1a;
--fp-radius: 8px;
--fp-shadow: 0 1px 3px rgba(0,0,0,.12);
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, "Yu Gothic", "MS PGothic", system-ui, sans-serif;
color: var(--fp-text);
background: var(--fp-bg);
padding: 1.5rem 1rem;
max-width: 900px;
margin: 0 auto;
line-height: 1.7;
}

#fp-app.fp-dark {
--fp-bg: #0f172a;
--fp-surface: #1e293b;
--fp-border: #334155;
--fp-text: #e2e8f0;
--fp-text-muted: #94a3b8;
--fp-accent: #818cf8;
--fp-accent-hover: #a5b4fc;
--fp-preview-bg: #1e293b;
--fp-preview-text: #f1f5f9;
}

/* ヘッダー */
#fp-app .fp-header {
text-align: center;
margin-bottom: 2rem;
}
#fp-app .fp-header h1 {
font-size: clamp(1.4rem, 4vw, 2rem);
font-weight: 700;
color: var(--fp-text);
margin-bottom: .4rem;
}
#fp-app .fp-header p {
color: var(--fp-text-muted);
font-size: .95rem;
}

/* トップバー */
#fp-app .fp-topbar {
display: flex;
flex-wrap: wrap;
gap: .5rem;
align-items: center;
justify-content: space-between;
margin-bottom: 1.25rem;
}
#fp-app .fp-preset-group {
display: flex;
flex-wrap: wrap;
gap: .4rem;
}
#fp-app .fp-preset-btn {
padding: .35rem .85rem;
border: 1.5px solid var(--fp-border);
border-radius: 999px;
background: var(--fp-surface);
color: var(--fp-text);
font-size: .85rem;
cursor: pointer;
transition: all .18s;
font-family: inherit;
}
#fp-app .fp-preset-btn:hover,
#fp-app .fp-preset-btn.active {
background: var(--fp-accent);
border-color: var(--fp-accent);
color: #fff;
}
#fp-app .fp-dark-toggle {
padding: .35rem .85rem;
border: 1.5px solid var(--fp-border);
border-radius: 999px;
background: var(--fp-surface);
color: var(--fp-text);
font-size: .85rem;
cursor: pointer;
transition: all .18s;
white-space: nowrap;
font-family: inherit;
}
#fp-app .fp-dark-toggle:hover {
border-color: var(--fp-accent);
color: var(--fp-accent);
}

/* メインレイアウト */
#fp-app .fp-layout {
display: grid;
grid-template-columns: 280px 1fr;
gap: 1.25rem;
align-items: start;
}
@media (max-width: 680px) {
#fp-app .fp-layout {
grid-template-columns: 1fr;
}
}

/* コントロールパネル */
#fp-app .fp-controls {
background: var(--fp-surface);
border: 1px solid var(--fp-border);
border-radius: var(--fp-radius);
padding: 1.1rem;
display: flex;
flex-direction: column;
gap: 1rem;
}
#fp-app .fp-control-section {
display: flex;
flex-direction: column;
gap: .5rem;
}
#fp-app .fp-label {
font-size: .78rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: .06em;
color: var(--fp-text-muted);
}
#fp-app .fp-select,
#fp-app .fp-input-text {
width: 100%;
padding: .45rem .7rem;
border: 1px solid var(--fp-border);
border-radius: 6px;
background: var(--fp-bg);
color: var(--fp-text);
font-size: .9rem;
font-family: inherit;
transition: border-color .15s;
}
#fp-app .fp-select:focus,
#fp-app .fp-input-text:focus {
outline: none;
border-color: var(--fp-accent);
}

/* レンジコントロール */
#fp-app .fp-range-row {
display: flex;
align-items: center;
gap: .6rem;
}
#fp-app .fp-range {
flex: 1;
accent-color: var(--fp-accent);
cursor: pointer;
}
#fp-app .fp-range-val {
font-size: .82rem;
color: var(--fp-text-muted);
min-width: 42px;
text-align: right;
}

/* カラースウォッチ */
#fp-app .fp-color-row {
display: flex;
gap: .5rem;
flex-wrap: wrap;
}
#fp-app .fp-swatch {
width: 28px;
height: 28px;
border-radius: 50%;
border: 2px solid transparent;
cursor: pointer;
transition: transform .15s, border-color .15s;
}
#fp-app .fp-swatch:hover { transform: scale(1.15); }
#fp-app .fp-swatch.active { border-color: var(--fp-accent); }

/* プレビューパネル */
#fp-app .fp-preview-panel {
border: 1px solid var(--fp-border);
border-radius: var(--fp-radius);
overflow: hidden;
}
#fp-app .fp-preview-bar {
display: flex;
align-items: center;
justify-content: space-between;
padding: .6rem 1rem;
background: var(--fp-surface);
border-bottom: 1px solid var(--fp-border);
gap: .5rem;
flex-wrap: wrap;
}
#fp-app .fp-preview-label {
font-size: .8rem;
font-weight: 600;
color: var(--fp-text-muted);
text-transform: uppercase;
letter-spacing: .06em;
}
#fp-app .fp-pair-name {
font-size: .85rem;
color: var(--fp-accent);
font-weight: 600;
}
#fp-app .fp-preview-area {
background: var(--fp-preview-bg);
color: var(--fp-preview-text);
padding: 2rem 2rem 1.5rem;
min-height: 260px;
transition: background .2s, color .2s;
}
#fp-app .fp-preview-heading {
margin-bottom: .6rem;
line-height: 1.25;
word-break: break-word;
}
#fp-app .fp-preview-body {
line-height: inherit;
word-break: break-word;
}

/* CSS出力 */
#fp-app .fp-css-section {
margin-top: 1.25rem;
background: var(--fp-surface);
border: 1px solid var(--fp-border);
border-radius: var(--fp-radius);
overflow: hidden;
}
#fp-app .fp-css-bar {
display: flex;
align-items: center;
justify-content: space-between;
padding: .6rem 1rem;
background: var(--fp-surface);
border-bottom: 1px solid var(--fp-border);
}
#fp-app .fp-css-title {
font-size: .8rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .07em;
color: var(--fp-text-muted);
}
#fp-app .fp-copy-btn {
padding: .3rem .8rem;
background: var(--fp-accent);
color: #fff;
border: none;
border-radius: 6px;
font-size: .82rem;
font-weight: 600;
cursor: pointer;
transition: background .18s;
font-family: inherit;
}
#fp-app .fp-copy-btn:hover { background: var(--fp-accent-hover); }
#fp-app .fp-copy-btn.copied { background: #16a34a; }
#fp-app .fp-css-output {
padding: 1rem;
font-family: "Courier New", Courier, monospace;
font-size: .8rem;
line-height: 1.7;
color: var(--fp-text);
white-space: pre-wrap;
word-break: break-all;
overflow-x: auto;
}

/* ペアグリッド */
#fp-app .fp-pair-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(190px, 1fr));
gap: .6rem;
margin-top: 1.25rem;
}
#fp-app .fp-pair-card {
background: var(--fp-surface);
border: 1.5px solid var(--fp-border);
border-radius: var(--fp-radius);
padding: .75rem .9rem;
cursor: pointer;
transition: border-color .18s, transform .18s;
}
#fp-app .fp-pair-card:hover { border-color: var(--fp-accent); transform: translateY(-2px); }
#fp-app .fp-pair-card.active { border-color: var(--fp-accent); background: color-mix(in srgb, var(--fp-accent) 8%, var(--fp-surface)); }
#fp-app .fp-card-heading {
font-size: 1rem;
font-weight: 700;
line-height: 1.3;
margin-bottom: .25rem;
color: var(--fp-text);
}
#fp-app .fp-card-body {
font-size: .78rem;
color: var(--fp-text-muted);
}
#fp-app .fp-card-tag {
display: inline-block;
font-size: .68rem;
padding: .1rem .45rem;
border-radius: 999px;
background: color-mix(in srgb, var(--fp-accent) 12%, transparent);
color: var(--fp-accent);
margin-top: .35rem;
font-weight: 600;
}

/* 関連リンク */
#fp-app .fp-related {
margin-top: 2rem;
padding-top: 1.25rem;
border-top: 1px solid var(--fp-border);
}
#fp-app .fp-related-title {
font-size: .85rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .07em;
color: var(--fp-text-muted);
margin-bottom: .75rem;
}
#fp-app .fp-related-links {
display: flex;
flex-wrap: wrap;
gap: .6rem;
}
#fp-app .fp-related-links a {
color: var(--fp-accent);
text-decoration: none;
font-size: .9rem;
border: 1px solid var(--fp-border);
padding: .3rem .8rem;
border-radius: 6px;
transition: border-color .15s, background .15s;
}
#fp-app .fp-related-links a:hover {
background: color-mix(in srgb, var(--fp-accent) 8%, transparent);
border-color: var(--fp-accent);
}

/* freee CTA */
#fp-app .fp-freee-cta {
margin-top: 2rem;
padding: 1.25rem 1.5rem;
background: linear-gradient(135deg, color-mix(in srgb, var(--fp-accent) 6%, var(--fp-surface)), var(--fp-surface));
border: 1px solid var(--fp-border);
border-radius: var(--fp-radius);
display: flex;
flex-wrap: wrap;
align-items: center;
gap: 1rem;
justify-content: space-between;
}
#fp-app .fp-freee-cta-text h3 {
font-size: 1rem;
font-weight: 700;
margin-bottom: .3rem;
color: var(--fp-text);
}
#fp-app .fp-freee-cta-text p {
font-size: .85rem;
color: var(--fp-text-muted);
max-width: 480px;
line-height: 1.55;
}
#fp-app .fp-freee-cta-btn {
display: inline-block;
padding: .6rem 1.4rem;
background: var(--fp-accent);
color: #fff;
border-radius: 8px;
font-size: .9rem;
font-weight: 700;
text-decoration: none;
white-space: nowrap;
transition: background .18s;
flex-shrink: 0;
}
#fp-app .fp-freee-cta-btn:hover { background: var(--fp-accent-hover); }
</style>

<div class="fp-header">
<h1>フォントペアサジェスター</h1>
<p>フォントの組み合わせを選び、各種設定を調整して、CSSをコピー。外部APIなし・完全オフライン対応。</p>
</div>

<!-- トップバー -->
<div class="fp-topbar">
<div class="fp-preset-group" id="fp-presets">
<button class="fp-preset-btn active" data-preset="all">すべて</button>
<button class="fp-preset-btn" data-preset="modern">モダン</button>
<button class="fp-preset-btn" data-preset="classic">クラシック</button>
<button class="fp-preset-btn" data-preset="playful">ポップ</button>
<button class="fp-preset-btn" data-preset="professional">プロ向け</button>
<button class="fp-preset-btn" data-preset="minimal">ミニマル</button>
<button class="fp-preset-btn" data-preset="japanese">和文特集</button>
</div>
<button class="fp-dark-toggle" id="fp-dark-toggle">ダークモード</button>
</div>

<!-- ペアグリッド（JS描画） -->
<div class="fp-pair-grid" id="fp-pair-grid"></div>

<!-- メインレイアウト -->
<div class="fp-layout" style="margin-top:1.25rem;">
<!-- コントロール -->
<div class="fp-controls">

<div class="fp-control-section">
<span class="fp-label">見出しテキスト</span>
<input class="fp-input-text" id="fp-heading-text" type="text" value="美しい日本語タイポグラフィ" />
</div>

<div class="fp-control-section">
<span class="fp-label">本文テキスト</span>
<input class="fp-input-text" id="fp-body-text" type="text" value="適切なフォントの組み合わせは、読みやすさを高め、コンテンツの印象を決定づけます。見出しと本文のバランスを大切に。" />
</div>

<div class="fp-control-section">
<span class="fp-label">見出しサイズ</span>
<div class="fp-range-row">
<input class="fp-range" id="fp-heading-size" type="range" min="18" max="72" value="36" />
<span class="fp-range-val" id="fp-heading-size-val">36px</span>
</div>
</div>

<div class="fp-control-section">
<span class="fp-label">本文サイズ</span>
<div class="fp-range-row">
<input class="fp-range" id="fp-body-size" type="range" min="12" max="28" value="16" />
<span class="fp-range-val" id="fp-body-size-val">16px</span>
</div>
</div>

<div class="fp-control-section">
<span class="fp-label">行の高さ（行間）</span>
<div class="fp-range-row">
<input class="fp-range" id="fp-line-height" type="range" min="120" max="230" value="175" />
<span class="fp-range-val" id="fp-line-height-val">1.75</span>
</div>
</div>

<div class="fp-control-section">
<span class="fp-label">文字間隔（本文）</span>
<div class="fp-range-row">
<input class="fp-range" id="fp-letter-spacing" type="range" min="-5" max="20" value="2" />
<span class="fp-range-val" id="fp-letter-spacing-val">0.02em</span>
</div>
</div>

<div class="fp-control-section">
<span class="fp-label">文字色</span>
<div class="fp-color-row" id="fp-color-swatches">
<button class="fp-swatch active" data-color="#1a1a1a" style="background:#1a1a1a;" title="ほぼ黒"></button>
<button class="fp-swatch" data-color="#2d3748" style="background:#2d3748;" title="スレート"></button>
<button class="fp-swatch" data-color="#1a365d" style="background:#1a365d;" title="ネイビー"></button>
<button class="fp-swatch" data-color="#4a1d2e" style="background:#4a1d2e;" title="バーガンディ"></button>
<button class="fp-swatch" data-color="#065f46" style="background:#065f46;" title="フォレスト"></button>
<button class="fp-swatch" data-color="#374151" style="background:#374151;" title="クールグレー"></button>
<button class="fp-swatch" data-color="#f8f9fa" style="background:#f8f9fa; border:1.5px solid #dee2e6;" title="ほぼ白"></button>
</div>
</div>

<div class="fp-control-section">
<span class="fp-label">背景色</span>
<div class="fp-color-row" id="fp-bg-swatches">
<button class="fp-swatch active" data-bg="#ffffff" style="background:#ffffff; border:1.5px solid #dee2e6;" title="白"></button>
<button class="fp-swatch" data-bg="#f8f9fa" style="background:#f8f9fa; border:1.5px solid #dee2e6;" title="ライトグレー"></button>
<button class="fp-swatch" data-bg="#fefce8" style="background:#fefce8;" title="クリーム"></button>
<button class="fp-swatch" data-bg="#eff6ff" style="background:#eff6ff;" title="ブルーティント"></button>
<button class="fp-swatch" data-bg="#0f172a" style="background:#0f172a;" title="ダーク"></button>
<button class="fp-swatch" data-bg="#1e293b" style="background:#1e293b;" title="スレートダーク"></button>
</div>
</div>

</div><!-- /.fp-controls -->

<!-- プレビュー -->
<div class="fp-preview-panel">
<div class="fp-preview-bar">
<span class="fp-preview-label">ライブプレビュー</span>
<span class="fp-pair-name" id="fp-active-pair-name"></span>
</div>
<div class="fp-preview-area" id="fp-preview-area">
<div class="fp-preview-heading" id="fp-preview-heading">美しい日本語タイポグラフィ</div>
<div class="fp-preview-body" id="fp-preview-body">適切なフォントの組み合わせは、読みやすさを高め、コンテンツの印象を決定づけます。</div>
</div>
</div>
</div>

<!-- CSS出力 -->
<div class="fp-css-section">
<div class="fp-css-bar">
<span class="fp-css-title">CSS 出力</span>
<button class="fp-copy-btn" id="fp-copy-btn">CSSをコピー</button>
</div>
<div class="fp-css-output" id="fp-css-output"></div>
</div>

<script>
(function() {
'use strict';

/* ─── フォントペアデータ ─── */
const PAIRS = [
/* === 和文特集 === */
{
id: 'ja-1',
name: 'ヒラギノ角ゴ + Noto Serif',
style: 'japanese',
heading: { label: 'ヒラギノ角ゴ', stack: '"Hiragino Kaku Gothic ProN", "Hiragino Sans", "Yu Gothic", Meiryo, sans-serif' },
body:    { label: 'Noto Serif JP', stack: '"Noto Serif JP", "Hiragino Mincho ProN", "Yu Mincho", "MS PMincho", serif' },
},
{
id: 'ja-2',
name: 'ヒラギノ明朝 + 游ゴシック',
style: 'japanese',
heading: { label: 'ヒラギノ明朝', stack: '"Hiragino Mincho ProN", "Hiragino Mincho Pro", "Yu Mincho", "MS PMincho", serif' },
body:    { label: '游ゴシック', stack: '"Yu Gothic", "YuGothic", "Hiragino Kaku Gothic ProN", Meiryo, sans-serif' },
},
{
id: 'ja-3',
name: 'Noto Sans JP + Noto Serif JP',
style: 'japanese',
heading: { label: 'Noto Sans JP', stack: '"Noto Sans JP", "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, sans-serif' },
body:    { label: 'Noto Serif JP', stack: '"Noto Serif JP", "Hiragino Mincho ProN", "Yu Mincho", serif' },
},
{
id: 'ja-4',
name: 'メイリオ + ヒラギノ明朝',
style: 'japanese',
heading: { label: 'メイリオ', stack: 'Meiryo, "Meiryo UI", "Hiragino Kaku Gothic ProN", sans-serif' },
body:    { label: 'ヒラギノ明朝', stack: '"Hiragino Mincho ProN", "Yu Mincho", "MS PMincho", serif' },
},
{
id: 'ja-5',
name: '游明朝 + 游ゴシック',
style: 'japanese',
heading: { label: '游明朝', stack: '"Yu Mincho", "YuMincho", "Hiragino Mincho ProN", "MS PMincho", serif' },
body:    { label: '游ゴシック', stack: '"Yu Gothic", "YuGothic", Meiryo, "MS PGothic", sans-serif' },
},
/* === モダン === */
{
id: 'modern-1',
name: 'System UI + Georgia',
style: 'modern',
heading: { label: 'System UI', stack: 'system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif' },
body:    { label: 'Georgia', stack: 'Georgia, "Times New Roman", serif' },
},
{
id: 'modern-2',
name: 'Helvetica + Palatino',
style: 'modern',
heading: { label: 'Helvetica', stack: 'Helvetica, Arial, "Liberation Sans", sans-serif' },
body:    { label: 'Palatino', stack: '"Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif' },
},
{
id: 'modern-3',
name: 'Optima + Courier New',
style: 'modern',
heading: { label: 'Optima', stack: 'Optima, Candara, "Gill Sans", sans-serif' },
body:    { label: 'Courier New', stack: '"Courier New", Courier, monospace' },
},
{
id: 'modern-4',
name: 'Futura + Georgia',
style: 'modern',
heading: { label: 'Futura', stack: 'Futura, "Century Gothic", "Apple Gothic", sans-serif' },
body:    { label: 'Georgia', stack: 'Georgia, "Times New Roman", serif' },
},
/* === クラシック === */
{
id: 'classic-1',
name: 'Georgia + Trebuchet MS',
style: 'classic',
heading: { label: 'Georgia', stack: 'Georgia, "Times New Roman", Times, serif' },
body:    { label: 'Trebuchet MS', stack: '"Trebuchet MS", Helvetica, Arial, sans-serif' },
},
{
id: 'classic-2',
name: 'Palatino + Verdana',
style: 'classic',
heading: { label: 'Palatino', stack: '"Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif' },
body:    { label: 'Verdana', stack: 'Verdana, Geneva, Tahoma, sans-serif' },
},
{
id: 'classic-3',
name: 'Baskerville + Tahoma',
style: 'classic',
heading: { label: 'Baskerville', stack: 'Baskerville, "Baskerville Old Face", "Hoefler Text", Georgia, serif' },
body:    { label: 'Tahoma', stack: 'Tahoma, Verdana, Geneva, sans-serif' },
},
{
id: 'classic-4',
name: 'Garamond + Gill Sans',
style: 'classic',
heading: { label: 'Garamond', stack: 'Garamond, "EB Garamond", Georgia, serif' },
body:    { label: 'Gill Sans', stack: '"Gill Sans", "Gill Sans MT", Calibri, sans-serif' },
},
/* === ポップ === */
{
id: 'playful-1',
name: 'Impact + Trebuchet MS',
style: 'playful',
heading: { label: 'Impact', stack: 'Impact, "Arial Narrow", "Franklin Gothic Medium", sans-serif' },
body:    { label: 'Trebuchet MS', stack: '"Trebuchet MS", Helvetica, Arial, sans-serif' },
},
{
id: 'playful-2',
name: 'Gill Sans + Courier New',
style: 'playful',
heading: { label: 'Gill Sans', stack: '"Gill Sans", "Gill Sans MT", Calibri, sans-serif' },
body:    { label: 'Courier New', stack: '"Courier New", Courier, monospace' },
},
/* === プロ向け === */
{
id: 'professional-1',
name: 'Times New Roman + Arial',
style: 'professional',
heading: { label: 'Times New Roman', stack: '"Times New Roman", Times, Georgia, serif' },
body:    { label: 'Arial', stack: 'Arial, Helvetica, "Liberation Sans", sans-serif' },
},
{
id: 'professional-2',
name: 'Cambria + Calibri',
style: 'professional',
heading: { label: 'Cambria', stack: 'Cambria, "Hoefler Text", Georgia, serif' },
body:    { label: 'Calibri', stack: 'Calibri, Candara, "Gill Sans", sans-serif' },
},
{
id: 'professional-3',
name: 'Didot + Helvetica',
style: 'professional',
heading: { label: 'Didot', stack: 'Didot, "Didot LT STD", "Hoefler Text", Garamond, Georgia, serif' },
body:    { label: 'Helvetica', stack: 'Helvetica, Arial, "Liberation Sans", sans-serif' },
},
/* === ミニマル === */
{
id: 'minimal-1',
name: 'Arial + Georgia',
style: 'minimal',
heading: { label: 'Arial', stack: 'Arial, Helvetica, sans-serif' },
body:    { label: 'Georgia', stack: 'Georgia, "Times New Roman", serif' },
},
{
id: 'minimal-2',
name: 'Segoe UI + Cambria',
style: 'minimal',
heading: { label: 'Segoe UI', stack: '"Segoe UI", system-ui, -apple-system, sans-serif' },
body:    { label: 'Cambria', stack: 'Cambria, "Hoefler Text", Georgia, serif' },
},
{
id: 'minimal-3',
name: 'System UI + System UI',
style: 'minimal',
heading: { label: 'System UI (太字)', stack: 'system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif' },
body:    { label: 'System UI', stack: 'system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif' },
},
];

/* プリセットラベル（日本語表示用） */
const PRESET_LABELS = {
all: 'すべて',
modern: 'モダン',
classic: 'クラシック',
playful: 'ポップ',
professional: 'プロ向け',
minimal: 'ミニマル',
japanese: '和文特集',
};

/* ─── 状態 ─── */
let activeId      = PAIRS[0].id;
let activePreset  = 'all';
let headingSize   = 36;
let bodySize      = 16;
let lineHeight    = 1.75;
let letterSpacing = 2;   /* /100 → em */
let textColor     = '#1a1a1a';
let bgColor       = '#ffffff';
let isDark        = false;

/* ─── DOM参照 ─── */
const app            = document.getElementById('fp-app');
const pairGrid       = document.getElementById('fp-pair-grid');
const previewArea    = document.getElementById('fp-preview-area');
const previewHeading = document.getElementById('fp-preview-heading');
const previewBody    = document.getElementById('fp-preview-body');
const activePairName = document.getElementById('fp-active-pair-name');
const cssOutput      = document.getElementById('fp-css-output');
const copyBtn        = document.getElementById('fp-copy-btn');
const headingSizeEl  = document.getElementById('fp-heading-size');
const bodySizeEl     = document.getElementById('fp-body-size');
const lineHeightEl   = document.getElementById('fp-line-height');
const letterSpaceEl  = document.getElementById('fp-letter-spacing');
const headingSizeVal = document.getElementById('fp-heading-size-val');
const bodySizeVal    = document.getElementById('fp-body-size-val');
const lineHeightVal  = document.getElementById('fp-line-height-val');
const letterSpaceVal = document.getElementById('fp-letter-spacing-val');
const headingTextEl  = document.getElementById('fp-heading-text');
const bodyTextEl     = document.getElementById('fp-body-text');
const darkToggle     = document.getElementById('fp-dark-toggle');

/* ─── グリッド描画 ─── */
function renderGrid() {
const pairs = activePreset === 'all' ? PAIRS : PAIRS.filter(p => p.style === activePreset);
pairGrid.innerHTML = pairs.map(p => `
<div class="fp-pair-card${p.id === activeId ? ' active' : ''}" data-id="${p.id}" role="button" tabindex="0" aria-label="${p.name}を選択">
<div class="fp-card-heading" style="font-family:${p.heading.stack}">${p.heading.label}</div>
<div class="fp-card-body"   style="font-family:${p.body.stack}">${p.body.label}</div>
<span class="fp-card-tag">${PRESET_LABELS[p.style] || p.style}</span>
</div>
`).join('');

pairGrid.querySelectorAll('.fp-pair-card').forEach(card => {
card.addEventListener('click', () => selectPair(card.dataset.id));
card.addEventListener('keydown', e => { if (e.key === 'Enter' || e.key === ' ') selectPair(card.dataset.id); });
});
}

/* ─── ペア選択 ─── */
function selectPair(id) {
activeId = id;
renderGrid();
updatePreview();
updateCSS();
}

/* ─── プレビュー更新 ─── */
function updatePreview() {
const pair = PAIRS.find(p => p.id === activeId) || PAIRS[0];
activePairName.textContent = pair.name;

previewHeading.style.fontFamily    = pair.heading.stack;
previewHeading.style.fontSize      = headingSize + 'px';
previewHeading.style.lineHeight    = lineHeight;
previewHeading.style.color         = textColor;
previewHeading.style.fontWeight    = '700';

previewBody.style.fontFamily       = pair.body.stack;
previewBody.style.fontSize         = bodySize + 'px';
previewBody.style.lineHeight       = lineHeight;
previewBody.style.letterSpacing    = (letterSpacing / 100) + 'em';
previewBody.style.color            = textColor;

previewArea.style.backgroundColor  = bgColor;

previewHeading.textContent = headingTextEl.value || '美しい日本語タイポグラフィ';
previewBody.textContent    = bodyTextEl.value || '本文のサンプルテキストです。';
}

/* ─── CSS出力更新 ─── */
function updateCSS() {
const pair = PAIRS.find(p => p.id === activeId) || PAIRS[0];
const lsEm = (letterSpacing / 100).toFixed(2);
cssOutput.textContent =
`/* フォントペアリング: ${pair.name} */

.heading {
font-family: ${pair.heading.stack};
font-size: ${headingSize}px;
font-weight: 700;
line-height: ${lineHeight};
color: ${textColor};
}

.body-text {
font-family: ${pair.body.stack};
font-size: ${bodySize}px;
line-height: ${lineHeight};
letter-spacing: ${lsEm}em;
color: ${textColor};
}

/* 背景 */
.container {
background-color: ${bgColor};
}`;
}

/* ─── レンジコントロール ─── */
headingSizeEl.addEventListener('input', () => {
headingSize = +headingSizeEl.value;
headingSizeVal.textContent = headingSize + 'px';
updatePreview(); updateCSS();
});
bodySizeEl.addEventListener('input', () => {
bodySize = +bodySizeEl.value;
bodySizeVal.textContent = bodySize + 'px';
updatePreview(); updateCSS();
});
lineHeightEl.addEventListener('input', () => {
lineHeight = (+lineHeightEl.value / 100).toFixed(2);
lineHeightVal.textContent = lineHeight;
updatePreview(); updateCSS();
});
letterSpaceEl.addEventListener('input', () => {
letterSpacing = +letterSpaceEl.value;
letterSpaceVal.textContent = (letterSpacing / 100).toFixed(2) + 'em';
updatePreview(); updateCSS();
});

/* ─── テキスト入力 ─── */
headingTextEl.addEventListener('input', () => updatePreview());
bodyTextEl.addEventListener('input',   () => updatePreview());

/* ─── プリセットボタン ─── */
document.getElementById('fp-presets').addEventListener('click', e => {
const btn = e.target.closest('.fp-preset-btn');
if (!btn) return;
document.querySelectorAll('#fp-presets .fp-preset-btn').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
activePreset = btn.dataset.preset;
const first = activePreset === 'all' ? PAIRS[0] : PAIRS.find(p => p.style === activePreset);
if (first) { activeId = first.id; updatePreview(); updateCSS(); }
renderGrid();
});

/* ─── 文字色スウォッチ ─── */
document.getElementById('fp-color-swatches').addEventListener('click', e => {
const sw = e.target.closest('.fp-swatch');
if (!sw || !sw.dataset.color) return;
document.querySelectorAll('#fp-color-swatches .fp-swatch').forEach(s => s.classList.remove('active'));
sw.classList.add('active');
textColor = sw.dataset.color;
updatePreview(); updateCSS();
});

/* ─── 背景色スウォッチ ─── */
document.getElementById('fp-bg-swatches').addEventListener('click', e => {
const sw = e.target.closest('.fp-swatch');
if (!sw || !sw.dataset.bg) return;
document.querySelectorAll('#fp-bg-swatches .fp-swatch').forEach(s => s.classList.remove('active'));
sw.classList.add('active');
bgColor = sw.dataset.bg;
updatePreview(); updateCSS();
});

/* ─── ダークモード切り替え ─── */
darkToggle.addEventListener('click', () => {
isDark = !isDark;
app.classList.toggle('fp-dark', isDark);
darkToggle.textContent = isDark ? 'ライトモード' : 'ダークモード';
});

/* ─── CSSコピー ─── */
copyBtn.addEventListener('click', () => {
const text = cssOutput.textContent;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(() => flashCopied());
} else {
const ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
flashCopied();
}
});

function flashCopied() {
copyBtn.textContent = 'コピーしました!';
copyBtn.classList.add('copied');
setTimeout(() => {
copyBtn.textContent = 'CSSをコピー';
copyBtn.classList.remove('copied');
}, 2000);
}

/* ─── 初期化 ─── */
renderGrid();
updatePreview();
updateCSS();

})();
</script>

<!-- 関連ツール -->
<div class="fp-related">
<div class="fp-related-title">関連ツール</div>
<div class="fp-related-links">
<a href="/tools/css-variables-generator/">CSS変数ジェネレーター</a>
<a href="/tools/css-text-gradient-generator/">CSSテキストグラデーションジェネレーター</a>
<a href="/tools/reading-time-calculator/">読了時間計算機</a>
</div>
</div>

<!-- freee CTA -->
<div class="fp-freee-cta">
<div class="fp-freee-cta-text">
<h3>フリーランス・個人事業主の方へ — freeeで経理を自動化</h3>
<p>デザイン・制作業務に集中するために、請求書・確定申告・経費管理を freee でまとめて効率化。無料プランから始められます。</p>
</div>
<a class="fp-freee-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener sponsored">freeeを無料で試す</a>
</div>

</div><!-- /#fp-app -->
