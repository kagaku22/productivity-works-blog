---
title: "フォントペアリングツール"
date: 2025-11-30
description: "見出し＋本文の相性抜群なフォント組み合わせを12種類収録。システムフォントのみ使用。文字サイズ・行間・字間・色をリアルタイムで調整し、CSSをそのままコピー。"
categories: ["無料ツール"]
slug: "font-pairing-tool"
ShowToc: false
aliases:
  - "/ja/tools/font-pair-suggester/"
  - "/ja/tools/font-pairing-tool/"
cover:
  image: "/images/covers/font-pairing-tool-ja.png"
  alt: "フォントペアリングツール"
---

<div id="fp-app">

<style>
#fp-app *,
#fp-app *::before,
#fp-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#fp-app {
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1a1a2e;
line-height: 1.7;
max-width: 960px;
margin: 0 auto;
padding: 0 16px;
}

#fp-app .fp-hero {
background: linear-gradient(135deg, #7c3aed 0%, #2563eb 100%);
color: #fff;
border-radius: 14px;
padding: 36px 28px 28px;
margin-bottom: 24px;
text-align: center;
}

#fp-app .fp-hero h2 {
font-size: 1.7rem;
font-weight: 800;
margin-bottom: 8px;
letter-spacing: -0.01em;
}

#fp-app .fp-hero p {
font-size: 0.95rem;
opacity: 0.9;
}

#fp-app .fp-layout {
display: grid;
grid-template-columns: 300px 1fr;
gap: 20px;
align-items: start;
}

@media (max-width: 700px) {
#fp-app .fp-layout {
grid-template-columns: 1fr;
}
}

#fp-app .fp-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px;
}

#fp-app .fp-card h3 {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #64748b;
margin-bottom: 14px;
}

/* Pairing list */
#fp-app .fp-pairing-list {
display: flex;
flex-direction: column;
gap: 6px;
}

#fp-app .fp-pairing-btn {
display: block;
width: 100%;
text-align: left;
padding: 12px 14px;
border: 1.5px solid #e2e8f0;
border-radius: 9px;
background: #fff;
cursor: pointer;
transition: border-color 0.15s, background 0.15s;
}

#fp-app .fp-pairing-btn:hover {
border-color: #7c3aed;
background: #faf5ff;
}

#fp-app .fp-pairing-btn.active {
border-color: #7c3aed;
background: #f5f3ff;
}

#fp-app .fp-pairing-btn .fp-btn-heading {
font-size: 0.93rem;
font-weight: 700;
color: #1e1b4b;
line-height: 1.25;
}

#fp-app .fp-pairing-btn .fp-btn-body {
font-size: 0.76rem;
color: #64748b;
margin-top: 2px;
}

#fp-app .fp-pairing-btn .fp-btn-tag {
font-size: 0.67rem;
padding: 2px 7px;
border-radius: 20px;
background: #ede9fe;
color: #6d28d9;
display: inline-block;
margin-top: 5px;
font-weight: 600;
}

/* Controls */
#fp-app .fp-controls {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
margin-bottom: 16px;
}

@media (max-width: 480px) {
#fp-app .fp-controls {
grid-template-columns: 1fr;
}
}

#fp-app .fp-control-group label {
display: block;
font-size: 0.73rem;
font-weight: 600;
color: #475569;
margin-bottom: 5px;
}

#fp-app .fp-control-group input[type="range"] {
width: 100%;
accent-color: #7c3aed;
cursor: pointer;
}

#fp-app .fp-control-group input[type="text"] {
width: 100%;
padding: 7px 10px;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
font-size: 0.85rem;
outline: none;
transition: border-color 0.15s;
font-family: inherit;
}

#fp-app .fp-control-group input[type="text"]:focus {
border-color: #7c3aed;
}

#fp-app .fp-control-group input[type="color"] {
width: 100%;
height: 36px;
padding: 2px 4px;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
cursor: pointer;
background: #fff;
}

#fp-app .fp-val {
font-size: 0.72rem;
color: #7c3aed;
font-weight: 700;
margin-left: 6px;
}

/* Mode tabs */
#fp-app .fp-mode-tabs {
display: flex;
gap: 6px;
margin-bottom: 16px;
flex-wrap: wrap;
}

#fp-app .fp-mode-tab {
padding: 6px 14px;
border: 1.5px solid #e2e8f0;
border-radius: 20px;
background: #fff;
font-size: 0.78rem;
font-weight: 600;
color: #64748b;
cursor: pointer;
transition: all 0.15s;
}

#fp-app .fp-mode-tab:hover {
border-color: #7c3aed;
color: #7c3aed;
}

#fp-app .fp-mode-tab.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

/* Preview area */
#fp-app .fp-preview-wrap {
border: 1.5px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
margin-bottom: 16px;
}

#fp-app .fp-preview-label {
font-size: 0.7rem;
font-weight: 600;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.07em;
padding: 8px 14px;
background: #f8fafc;
border-bottom: 1px solid #e2e8f0;
}

#fp-app #fp-preview {
padding: 28px 24px;
min-height: 220px;
background: #fff;
transition: background 0.2s;
}

#fp-app #fp-preview.mode-hero {
background: linear-gradient(135deg, #1e1b4b 0%, #312e81 100%);
padding: 48px 36px;
}

#fp-app #fp-preview.mode-card {
background: #f1f5f9;
display: flex;
gap: 16px;
flex-wrap: wrap;
padding: 20px;
}

#fp-app .fp-preview-card {
flex: 1;
min-width: 180px;
background: #fff;
border-radius: 10px;
padding: 18px;
box-shadow: 0 1px 6px rgba(0,0,0,0.08);
}

#fp-app .fp-preview-card .fp-card-tag {
font-size: 0.68rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #7c3aed;
margin-bottom: 8px;
}

/* CSS output */
#fp-app .fp-css-box {
background: #0f172a;
border-radius: 10px;
padding: 16px;
position: relative;
}

#fp-app .fp-css-box pre {
font-family: "Consolas", "Courier New", Courier, monospace;
font-size: 0.77rem;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
line-height: 1.7;
}

#fp-app .fp-copy-btn {
position: absolute;
top: 10px;
right: 10px;
padding: 5px 12px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 6px;
font-size: 0.73rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
font-family: inherit;
}

#fp-app .fp-copy-btn:hover {
background: #6d28d9;
}

#fp-app .fp-copy-btn.copied {
background: #16a34a;
}

#fp-app .fp-info-strip {
display: flex;
gap: 10px;
flex-wrap: wrap;
padding: 12px 14px;
background: #f5f3ff;
border: 1.5px solid #ddd6fe;
border-radius: 9px;
margin-bottom: 16px;
}

#fp-app .fp-info-item {
font-size: 0.77rem;
color: #5b21b6;
}

#fp-app .fp-info-item strong {
font-weight: 700;
}

#fp-app .fp-section-title {
font-size: 0.77rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #64748b;
margin-bottom: 10px;
}
</style>

<div class="fp-hero">
<h2>フォントペアリングツール</h2>
<p>12種類のフォント組み合わせをリアルタイムプレビュー — 調整してCSSをコピー</p>
</div>

<div class="fp-layout">

<!-- 左：ペアリング選択 -->
<div class="fp-card">
<h3>フォントの組み合わせ</h3>
<div class="fp-pairing-list" id="fp-pairing-list"></div>
</div>

<!-- 右：コントロール + プレビュー -->
<div>

<!-- 情報バー -->
<div class="fp-info-strip" id="fp-info-strip">
<span class="fp-info-item"><strong>見出し：</strong><span id="fp-info-heading">—</span></span>
<span class="fp-info-item"><strong>本文：</strong><span id="fp-info-body">—</span></span>
<span class="fp-info-item"><strong>スタイル：</strong><span id="fp-info-style">—</span></span>
</div>

<!-- コントロール -->
<div class="fp-card" style="margin-bottom:16px;">
<h3>カスタマイズ</h3>
<div class="fp-controls">
<div class="fp-control-group" style="grid-column:1/-1;">
<label>サンプルテキスト</label>
<input type="text" id="fp-sample-text" value="人間の知恵と技術が融合し、新たな創造の地平が拓かれる" />
</div>
<div class="fp-control-group">
<label>見出しサイズ <span class="fp-val" id="fp-heading-size-val">2.4rem</span></label>
<input type="range" id="fp-heading-size" min="1.2" max="4.5" step="0.1" value="2.4" />
</div>
<div class="fp-control-group">
<label>本文サイズ <span class="fp-val" id="fp-body-size-val">1rem</span></label>
<input type="range" id="fp-body-size" min="0.75" max="1.5" step="0.05" value="1" />
</div>
<div class="fp-control-group">
<label>行間 <span class="fp-val" id="fp-line-height-val">1.7</span></label>
<input type="range" id="fp-line-height" min="1.0" max="2.5" step="0.05" value="1.7" />
</div>
<div class="fp-control-group">
<label>字間 <span class="fp-val" id="fp-letter-spacing-val">0em</span></label>
<input type="range" id="fp-letter-spacing" min="-0.05" max="0.2" step="0.005" value="0" />
</div>
<div class="fp-control-group">
<label>見出しカラー</label>
<input type="color" id="fp-heading-color" value="#1a1a2e" />
</div>
<div class="fp-control-group">
<label>本文カラー</label>
<input type="color" id="fp-body-color" value="#374151" />
</div>
</div>

<div class="fp-section-title">プレビューモード</div>
<div class="fp-mode-tabs">
<button class="fp-mode-tab active" data-mode="blog">ブログ記事</button>
<button class="fp-mode-tab" data-mode="hero">ヒーローセクション</button>
<button class="fp-mode-tab" data-mode="card">カードレイアウト</button>
</div>
</div>

<!-- プレビュー -->
<div class="fp-preview-wrap">
<div class="fp-preview-label">ライブプレビュー</div>
<div id="fp-preview"></div>
</div>

<!-- CSS出力 -->
<div class="fp-card">
<h3>CSSコード</h3>
<div class="fp-css-box">
<pre id="fp-css-output"></pre>
<button class="fp-copy-btn" id="fp-copy-btn">CSSをコピー</button>
</div>
</div>

</div>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function() {
const PAIRINGS = [
{
id: "p1",
name: "クラシック編集",
heading: "Georgia",
headingStack: "Georgia, 'Times New Roman', Times, serif",
body: "Verdana",
bodyStack: "Verdana, Geneva, Tahoma, sans-serif",
style: "エディトリアル",
tag: "セリフ + サンセリフ"
},
{
id: "p2",
name: "モダンミニマル",
heading: "Helvetica Neue",
headingStack: "'Helvetica Neue', Helvetica, Arial, sans-serif",
body: "Georgia",
bodyStack: "Georgia, 'Times New Roman', Times, serif",
style: "ミニマル",
tag: "サンセリフ + セリフ"
},
{
id: "p3",
name: "システムネイティブ",
heading: "system-ui",
headingStack: "system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif",
body: "system-ui",
bodyStack: "system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif",
style: "ネイティブ",
tag: "システム + システム"
},
{
id: "p4",
name: "テックモノ",
heading: "Consolas",
headingStack: "Consolas, 'Courier New', Courier, monospace",
body: "Segoe UI",
bodyStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
style: "テクニカル",
tag: "等幅 + サンセリフ"
},
{
id: "p5",
name: "タイムレスセリフ",
heading: "Palatino",
headingStack: "Palatino, 'Palatino Linotype', 'Book Antiqua', Georgia, serif",
body: "Arial",
bodyStack: "Arial, Helvetica, sans-serif",
style: "タイムレス",
tag: "セリフ + サンセリフ"
},
{
id: "p6",
name: "ボールドコントラスト",
heading: "Arial",
headingStack: "Arial, Helvetica, sans-serif",
body: "Georgia",
bodyStack: "Georgia, 'Times New Roman', Times, serif",
style: "コントラスト",
tag: "サンセリフ + セリフ"
},
{
id: "p7",
name: "デジタルクリーン",
heading: "Segoe UI",
headingStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
body: "Verdana",
bodyStack: "Verdana, Geneva, Tahoma, sans-serif",
style: "デジタル",
tag: "サンセリフ + サンセリフ"
},
{
id: "p8",
name: "文芸クラシック",
heading: "Times New Roman",
headingStack: "'Times New Roman', Times, Georgia, serif",
body: "Helvetica",
bodyStack: "Helvetica, Arial, sans-serif",
style: "文芸",
tag: "セリフ + サンセリフ"
},
{
id: "p9",
name: "ヒューマニストウォーム",
heading: "Verdana",
headingStack: "Verdana, Geneva, Tahoma, sans-serif",
body: "Palatino",
bodyStack: "Palatino, 'Palatino Linotype', 'Book Antiqua', Georgia, serif",
style: "ヒューマニスト",
tag: "サンセリフ + セリフ"
},
{
id: "p10",
name: "コード & プローズ",
heading: "Courier New",
headingStack: "'Courier New', Courier, Consolas, monospace",
body: "Segoe UI",
bodyStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
style: "開発者向け",
tag: "等幅 + サンセリフ"
},
{
id: "p11",
name: "コーポレートクリーン",
heading: "Segoe UI",
headingStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
body: "Arial",
bodyStack: "Arial, Helvetica, sans-serif",
style: "コーポレート",
tag: "サンセリフ + サンセリフ"
},
{
id: "p12",
name: "エレガントブック",
heading: "Georgia",
headingStack: "Georgia, 'Times New Roman', Times, serif",
body: "Palatino",
bodyStack: "Palatino, 'Palatino Linotype', 'Book Antiqua', Georgia, serif",
style: "エレガント",
tag: "セリフ + セリフ"
}
];

let current = PAIRINGS[0];
let mode = "blog";
let headingSize = 2.4;
let bodySize = 1.0;
let lineHeight = 1.7;
let letterSpacing = 0;
let headingColor = "#1a1a2e";
let bodyColor = "#374151";
let sampleText = "人間の知恵と技術が融合し、新たな創造の地平が拓かれる";

function buildPairingList() {
const list = document.getElementById("fp-pairing-list");
PAIRINGS.forEach(function(p, i) {
const btn = document.createElement("button");
btn.className = "fp-pairing-btn" + (i === 0 ? " active" : "");
btn.setAttribute("data-id", p.id);
btn.innerHTML =
'<div class="fp-btn-heading" style="font-family:' + p.headingStack + '">' + p.name + '</div>' +
'<div class="fp-btn-body">' + p.heading + ' + ' + p.body + '</div>' +
'<span class="fp-btn-tag">' + p.tag + '</span>';
btn.addEventListener("click", function() {
document.querySelectorAll("#fp-app .fp-pairing-btn").forEach(function(b) { b.classList.remove("active"); });
btn.classList.add("active");
current = p;
render();
});
list.appendChild(btn);
});
}

function getSampleText() {
return document.getElementById("fp-sample-text").value || sampleText;
}

function renderBlogMode(preview, txt) {
preview.className = "";
preview.id = "fp-preview";
preview.style.background = "#fff";
preview.style.padding = "28px 24px";

const tag = document.createElement("div");
tag.style.cssText = "font-size:0.7rem;font-weight:700;text-transform:uppercase;letter-spacing:0.08em;color:#7c3aed;margin-bottom:12px;font-family:" + current.bodyStack;
tag.textContent = current.style + " · " + current.tag;

const h = document.createElement("h2");
h.style.cssText = "font-family:" + current.headingStack + ";font-size:" + headingSize + "rem;line-height:1.25;letter-spacing:" + letterSpacing + "em;color:" + headingColor + ";margin-bottom:14px;font-weight:700;";
h.textContent = txt;

const p1 = document.createElement("p");
p1.style.cssText = "font-family:" + current.bodyStack + ";font-size:" + bodySize + "rem;line-height:" + lineHeight + ";letter-spacing:" + letterSpacing + "em;color:" + bodyColor + ";margin-bottom:12px;";
p1.textContent = "タイポグラフィは、読者がコンテンツを体験する方法を形作ります。力強い見出しフォントと読みやすい本文フォントの相互作用が、目を自然にページ上で誘導する視覚的な階層を生み出します。";

const p2 = document.createElement("p");
p2.style.cssText = p1.style.cssText;
p2.textContent = "優れたフォントペアリングは透明に感じられます。コンテンツを輝かせながら、一貫したパーソナリティを確立します。ウェイト・幅・分類のコントラストが、混乱なく視覚的な興味を生み出します。";

preview.innerHTML = "";
preview.appendChild(tag);
preview.appendChild(h);
preview.appendChild(p1);
preview.appendChild(p2);
}

function renderHeroMode(preview, txt) {
preview.className = "mode-hero";
preview.id = "fp-preview";
preview.style.padding = "48px 36px";

const eyebrow = document.createElement("div");
eyebrow.style.cssText = "font-family:" + current.bodyStack + ";font-size:0.73rem;font-weight:700;text-transform:uppercase;letter-spacing:0.12em;color:rgba(255,255,255,0.7);margin-bottom:14px;";
eyebrow.textContent = current.style + " ペアリング";

const h = document.createElement("h1");
h.style.cssText = "font-family:" + current.headingStack + ";font-size:" + headingSize + "rem;line-height:1.2;letter-spacing:" + letterSpacing + "em;color:#fff;margin-bottom:16px;font-weight:800;";
h.textContent = txt;

const sub = document.createElement("p");
sub.style.cssText = "font-family:" + current.bodyStack + ";font-size:" + bodySize + "rem;line-height:" + lineHeight + ";color:rgba(255,255,255,0.85);max-width:520px;letter-spacing:" + letterSpacing + "em;";
sub.textContent = "タイポグラフィとは、文字を美しく・読みやすく・魅力的に配置する技術です。適切なフォントの組み合わせがブランドの印象を決定します。";

const btn = document.createElement("a");
btn.style.cssText = "display:inline-block;margin-top:20px;padding:11px 24px;background:#7c3aed;color:#fff;border-radius:8px;font-family:" + current.bodyStack + ";font-size:0.88rem;font-weight:700;text-decoration:none;";
btn.textContent = "はじめる";
btn.href = "#";

preview.innerHTML = "";
preview.appendChild(eyebrow);
preview.appendChild(h);
preview.appendChild(sub);
preview.appendChild(btn);
}

function renderCardMode(preview, txt) {
preview.className = "mode-card";
preview.id = "fp-preview";

const cards = [
{ tag: "デザイン", title: txt, body: "タイポグラフィはビジュアルシステム全体のトーンを設定します。" },
{ tag: "コード", title: "スケールで読みやすく", body: "一貫したフォント使用が信頼を構築し、理解を深めます。" },
{ tag: "コンテンツ", title: "目的を持って組み合わせる", body: "各ペアリングは独自のムードと読者体験を生み出します。" }
];

preview.innerHTML = "";
cards.forEach(function(c) {
const card = document.createElement("div");
card.className = "fp-preview-card";

const tagEl = document.createElement("div");
tagEl.className = "fp-card-tag";
tagEl.style.fontFamily = current.bodyStack;
tagEl.textContent = c.tag;

const titleEl = document.createElement("h3");
titleEl.style.cssText = "font-family:" + current.headingStack + ";font-size:" + Math.max(1.0, headingSize * 0.55) + "rem;line-height:1.3;letter-spacing:" + letterSpacing + "em;color:" + headingColor + ";margin-bottom:8px;font-weight:700;";
titleEl.textContent = c.title;

const bodyEl = document.createElement("p");
bodyEl.style.cssText = "font-family:" + current.bodyStack + ";font-size:" + Math.max(0.75, bodySize * 0.9) + "rem;line-height:" + lineHeight + ";color:" + bodyColor + ";letter-spacing:" + letterSpacing + "em;";
bodyEl.textContent = c.body;

card.appendChild(tagEl);
card.appendChild(titleEl);
card.appendChild(bodyEl);
preview.appendChild(card);
});
}

function updateCSS() {
const css =
"/* フォントペアリング: " + current.name + " */\n" +
"/* 見出し: " + current.heading + " / 本文: " + current.body + " */\n\n" +
":root {\n" +
"  --font-heading: " + current.headingStack + ";\n" +
"  --font-body: " + current.bodyStack + ";\n" +
"}\n\n" +
"h1, h2, h3, h4, h5, h6 {\n" +
"  font-family: var(--font-heading);\n" +
"  font-size: " + headingSize + "rem;\n" +
"  line-height: 1.2;\n" +
"  letter-spacing: " + letterSpacing + "em;\n" +
"  color: " + headingColor + ";\n" +
"}\n\n" +
"body, p {\n" +
"  font-family: var(--font-body);\n" +
"  font-size: " + bodySize + "rem;\n" +
"  line-height: " + lineHeight + ";\n" +
"  letter-spacing: " + letterSpacing + "em;\n" +
"  color: " + bodyColor + ";\n" +
"}";
document.getElementById("fp-css-output").textContent = css;
}

function updateInfo() {
document.getElementById("fp-info-heading").textContent = current.heading;
document.getElementById("fp-info-body").textContent = current.body;
document.getElementById("fp-info-style").textContent = current.style;
}

function render() {
const preview = document.getElementById("fp-preview");
const txt = getSampleText();
if (mode === "hero") {
renderHeroMode(preview, txt);
} else if (mode === "card") {
renderCardMode(preview, txt);
} else {
renderBlogMode(preview, txt);
}
updateCSS();
updateInfo();
}

// Range inputs
document.getElementById("fp-heading-size").addEventListener("input", function() {
headingSize = parseFloat(this.value);
document.getElementById("fp-heading-size-val").textContent = headingSize + "rem";
render();
});
document.getElementById("fp-body-size").addEventListener("input", function() {
bodySize = parseFloat(this.value);
document.getElementById("fp-body-size-val").textContent = bodySize + "rem";
render();
});
document.getElementById("fp-line-height").addEventListener("input", function() {
lineHeight = parseFloat(this.value);
document.getElementById("fp-line-height-val").textContent = lineHeight;
render();
});
document.getElementById("fp-letter-spacing").addEventListener("input", function() {
letterSpacing = parseFloat(this.value);
document.getElementById("fp-letter-spacing-val").textContent = letterSpacing + "em";
render();
});
document.getElementById("fp-heading-color").addEventListener("input", function() {
headingColor = this.value;
render();
});
document.getElementById("fp-body-color").addEventListener("input", function() {
bodyColor = this.value;
render();
});
document.getElementById("fp-sample-text").addEventListener("input", render);

// Mode tabs
document.querySelectorAll("#fp-app .fp-mode-tab").forEach(function(tab) {
tab.addEventListener("click", function() {
document.querySelectorAll("#fp-app .fp-mode-tab").forEach(function(t) { t.classList.remove("active"); });
tab.classList.add("active");
mode = tab.getAttribute("data-mode");
render();
});
});

// CSS コピー
document.getElementById("fp-copy-btn").addEventListener("click", function() {
const text = document.getElementById("fp-css-output").textContent;
const btn = document.getElementById("fp-copy-btn");
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(function() {
btn.textContent = "コピーしました!";
btn.classList.add("copied");
setTimeout(function() {
btn.textContent = "CSSをコピー";
btn.classList.remove("copied");
}, 2000);
});
} else {
const ta = document.createElement("textarea");
ta.value = text;
ta.style.position = "fixed";
ta.style.left = "-9999px";
document.body.appendChild(ta);
ta.select();
document.execCommand("copy");
document.body.removeChild(ta);
btn.textContent = "コピーしました!";
btn.classList.add("copied");
setTimeout(function() {
btn.textContent = "CSSをコピー";
btn.classList.remove("copied");
}, 2000);
}
});

buildPairingList();
render();
})();
</script>

</div>

---

### 関連ツール
> フォントサイズ変換 → [フォントサイズ変換ツール](/ja/tools/font-size-converter/)
> カラーパレット → [カラーパレット生成](/ja/tools/color-palette-generator/)
---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
