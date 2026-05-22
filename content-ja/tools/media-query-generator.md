---
title: "CSSメディアクエリジェネレーター — レスポンシブビルダー"
date: 2025-06-20
description: "CSSメディアクエリをビジュアルで生成。デバイスプリセット・ブレイクポイントビルダー・ライブビューポートマッチ。モバイルファースト対応。@mediaコードを即コピー。"
categories: ["無料ツール"]
tags: ["便利ツール", "無料ツール"]
slug: "media-query-generator"
ShowToc: false
cover:
  image: "/images/covers/media-query-generator-ja.png"
  alt: "CSSメディアクエリジェネレーター"
---

CSSメディアクエリをビジュアルで作成できます。デバイスプリセットを選ぶかブレイクポイントを入力して、向き・ダークモード・アニメーション削減などの機能を追加し、生成された `@media` コードをそのままスタイルシートに貼り付けてください。

<div id="mq-app">
<style>
#mq-app *,
#mq-app *::before,
#mq-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#mq-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", "Yu Gothic", sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f4f6fb;
border-radius: 12px;
padding: 24px;
max-width: 900px;
margin: 0 auto;
}

#mq-app h2.mq-section-title {
font-size: 13px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .06em;
color: #6b7280;
margin-bottom: 10px;
}

#mq-app .mq-card {
background: #fff;
border-radius: 10px;
padding: 20px;
margin-bottom: 16px;
border: 1px solid #e5e7eb;
box-shadow: 0 1px 3px rgba(0,0,0,.06);
}

/* --- Approach toggle --- */
#mq-app .mq-approach-row {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 4px;
}
#mq-app .mq-approach-btn {
flex: 1 1 140px;
padding: 10px 14px;
border: 2px solid #e5e7eb;
border-radius: 8px;
background: #fff;
cursor: pointer;
font-size: 14px;
font-weight: 700;
color: #374151;
transition: border-color .15s, background .15s, color .15s;
text-align: center;
}
#mq-app .mq-approach-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}

/* --- Device presets --- */
#mq-app .mq-presets-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
gap: 8px;
}
#mq-app .mq-preset-btn {
padding: 9px 6px;
border: 2px solid #e5e7eb;
border-radius: 8px;
background: #fff;
cursor: pointer;
font-size: 12px;
font-weight: 700;
color: #374151;
display: flex;
flex-direction: column;
align-items: center;
gap: 4px;
transition: border-color .15s, background .15s;
}
#mq-app .mq-preset-btn .mq-preset-icon { font-size: 20px; }
#mq-app .mq-preset-btn .mq-preset-range { font-size: 10px; color: #9ca3af; font-weight: 500; }
#mq-app .mq-preset-btn:hover,
#mq-app .mq-preset-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}
#mq-app .mq-preset-btn.active .mq-preset-range { color: #818cf8; }

/* --- Inputs --- */
#mq-app .mq-fields-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
gap: 14px;
}
#mq-app .mq-field label {
display: block;
font-size: 12px;
font-weight: 700;
color: #6b7280;
margin-bottom: 5px;
letter-spacing: .04em;
}
#mq-app .mq-field input[type="number"],
#mq-app .mq-field select {
width: 100%;
padding: 9px 11px;
border: 1.5px solid #d1d5db;
border-radius: 7px;
font-size: 14px;
color: #111827;
background: #fff;
appearance: auto;
transition: border-color .15s;
}
#mq-app .mq-field input[type="number"]:focus,
#mq-app .mq-field select:focus {
outline: none;
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,.12);
}
#mq-app .mq-field .mq-unit {
font-size: 12px;
color: #9ca3af;
margin-top: 3px;
}

/* --- Feature chips --- */
#mq-app .mq-feature-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
}
#mq-app .mq-feature-chip {
display: flex;
align-items: center;
gap: 7px;
padding: 7px 13px;
border: 1.5px solid #e5e7eb;
border-radius: 20px;
cursor: pointer;
font-size: 13px;
font-weight: 500;
color: #374151;
background: #fff;
transition: border-color .15s, background .15s, color .15s;
user-select: none;
}
#mq-app .mq-feature-chip.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}
#mq-app .mq-feature-chip input[type="checkbox"] { display: none; }
#mq-app .mq-feature-dot {
width: 8px; height: 8px;
border-radius: 50%;
background: #d1d5db;
flex-shrink: 0;
transition: background .15s;
}
#mq-app .mq-feature-chip.active .mq-feature-dot { background: #6366f1; }

/* --- Sub-select inside chip --- */
#mq-app .mq-chip-select {
border: none;
background: transparent;
font-size: 13px;
font-weight: 500;
color: #4338ca;
cursor: pointer;
padding: 0;
margin-left: 2px;
}
#mq-app .mq-chip-select:focus { outline: none; }

/* --- Live viewport --- */
#mq-app .mq-viewport-bar {
display: flex;
align-items: center;
gap: 12px;
flex-wrap: wrap;
}
#mq-app .mq-vp-badge {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 6px 13px;
border-radius: 20px;
font-size: 13px;
font-weight: 600;
background: #f3f4f6;
color: #6b7280;
}
#mq-app .mq-vp-badge.match {
background: #d1fae5;
color: #065f46;
}
#mq-app .mq-vp-size { font-size: 13px; color: #6b7280; }
#mq-app .mq-vp-dot { width: 8px; height: 8px; border-radius: 50%; background: currentColor; }

/* --- Output --- */
#mq-app .mq-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 10px;
flex-wrap: wrap;
gap: 8px;
}
#mq-app .mq-copy-btn {
padding: 7px 16px;
background: #6366f1;
color: #fff;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: background .15s;
}
#mq-app .mq-copy-btn:hover { background: #4f46e5; }
#mq-app .mq-copy-btn.copied { background: #059669; }

#mq-app pre.mq-code {
background: #0f172a;
color: #e2e8f0;
border-radius: 8px;
padding: 18px 20px;
overflow-x: auto;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.65;
white-space: pre;
min-height: 60px;
}
#mq-app .mq-kw  { color: #a78bfa; }
#mq-app .mq-feat { color: #38bdf8; }
#mq-app .mq-val  { color: #34d399; }
#mq-app .mq-cmt  { color: #64748b; }

/* --- Generate button --- */
#mq-app .mq-generate-btn {
width: 100%;
padding: 13px;
background: #6366f1;
color: #fff;
border: none;
border-radius: 9px;
font-size: 16px;
font-weight: 700;
cursor: pointer;
margin-bottom: 20px;
transition: background .15s, transform .1s;
}
#mq-app .mq-generate-btn:hover { background: #4f46e5; transform: translateY(-1px); }
#mq-app .mq-generate-btn:active { transform: translateY(0); }

/* --- Reference table --- */
#mq-app .mq-table-wrap { overflow-x: auto; }
#mq-app table.mq-ref-table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
}
#mq-app table.mq-ref-table th {
background: #f8fafc;
padding: 9px 12px;
text-align: left;
font-weight: 700;
color: #374151;
border-bottom: 2px solid #e5e7eb;
white-space: nowrap;
}
#mq-app table.mq-ref-table td {
padding: 8px 12px;
border-bottom: 1px solid #f3f4f6;
color: #374151;
vertical-align: top;
}
#mq-app table.mq-ref-table tr:last-child td { border-bottom: none; }
#mq-app table.mq-ref-table code {
background: #f1f5f9;
border-radius: 4px;
padding: 1px 5px;
font-size: 12px;
color: #7c3aed;
font-family: monospace;
}
#mq-app .mq-fw { font-weight: 600; }
#mq-app .mq-tag {
display: inline-block;
padding: 1px 7px;
border-radius: 10px;
font-size: 11px;
font-weight: 600;
background: #e0e7ff;
color: #3730a3;
margin-right: 3px;
}
#mq-app .mq-tag.tw { background: #ccfbf1; color: #0f766e; }
#mq-app .mq-tag.bs { background: #fef3c7; color: #92400e; }
#mq-app .mq-tag.cu { background: #fce7f3; color: #9d174d; }

/* --- Cross links --- */
#mq-app .mq-links { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 4px; }
#mq-app .mq-link {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 8px 14px;
background: #fff;
border: 1.5px solid #e5e7eb;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
color: #4338ca;
text-decoration: none;
transition: border-color .15s, background .15s;
}
#mq-app .mq-link:hover { border-color: #6366f1; background: #eef2ff; }

/* --- freee CTA --- */
#mq-app .mq-cta {
background: linear-gradient(135deg, #4f46e5 0%, #7c3aed 100%);
border-radius: 12px;
padding: 24px;
color: #fff;
text-align: center;
margin-top: 8px;
}
#mq-app .mq-cta h3 {
font-size: 18px;
font-weight: 800;
margin-bottom: 8px;
}
#mq-app .mq-cta p {
font-size: 14px;
opacity: .88;
margin-bottom: 16px;
line-height: 1.6;
}
#mq-app .mq-cta-btn {
display: inline-block;
padding: 11px 28px;
background: #fff;
color: #4f46e5;
border-radius: 8px;
font-size: 15px;
font-weight: 800;
text-decoration: none;
transition: transform .15s, box-shadow .15s;
box-shadow: 0 4px 14px rgba(0,0,0,.18);
}
#mq-app .mq-cta-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(0,0,0,.22); }

/* --- Responsive --- */
@media (max-width: 600px) {
#mq-app { padding: 14px; }
#mq-app .mq-fields-grid { grid-template-columns: 1fr 1fr; }
}
</style>

<!-- ===== アプローチ ===== -->
<div class="mq-card">
<h2 class="mq-section-title">アプローチ選択</h2>
<div class="mq-approach-row">
<button class="mq-approach-btn active" data-approach="mobile-first" onclick="mqSetApproach('mobile-first',this)">
モバイルファースト<br><small style="font-weight:400;font-size:11px;">min-width クエリ</small>
</button>
<button class="mq-approach-btn" data-approach="desktop-first" onclick="mqSetApproach('desktop-first',this)">
デスクトップファースト<br><small style="font-weight:400;font-size:11px;">max-width クエリ</small>
</button>
</div>
</div>

<!-- ===== デバイスプリセット ===== -->
<div class="mq-card">
<h2 class="mq-section-title">デバイスプリセット</h2>
<div class="mq-presets-grid" id="mqPresetsGrid">
<button class="mq-preset-btn" data-min="320" data-max="480" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📱</span>
iPhone SE
<span class="mq-preset-range">320–480px</span>
</button>
<button class="mq-preset-btn" data-min="375" data-max="812" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📱</span>
iPhone 12/13
<span class="mq-preset-range">375–812px</span>
</button>
<button class="mq-preset-btn" data-min="390" data-max="844" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📱</span>
iPhone 14 Pro
<span class="mq-preset-range">390–844px</span>
</button>
<button class="mq-preset-btn" data-min="768" data-max="1024" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📟</span>
iPad
<span class="mq-preset-range">768–1024px</span>
</button>
<button class="mq-preset-btn" data-min="1024" data-max="1366" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📟</span>
iPad Pro
<span class="mq-preset-range">1024–1366px</span>
</button>
<button class="mq-preset-btn" data-min="1280" data-max="1920" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">🖥️</span>
デスクトップ HD
<span class="mq-preset-range">1280–1920px</span>
</button>
<button class="mq-preset-btn" data-min="1920" data-max="2560" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">🖥️</span>
4K / QHD
<span class="mq-preset-range">1920–2560px</span>
</button>
<button class="mq-preset-btn" data-min="" data-max="" onclick="mqClearPreset(this)">
<span class="mq-preset-icon">✏️</span>
カスタム
<span class="mq-preset-range">手動入力</span>
</button>
</div>
</div>

<!-- ===== 幅・高さ ===== -->
<div class="mq-card">
<h2 class="mq-section-title">幅 &amp; 高さ</h2>
<div class="mq-fields-grid">
<div class="mq-field">
<label>最小幅（Min Width）</label>
<input type="number" id="mqMinW" min="0" max="9999" placeholder="例: 768">
<div class="mq-unit">px</div>
</div>
<div class="mq-field">
<label>最大幅（Max Width）</label>
<input type="number" id="mqMaxW" min="0" max="9999" placeholder="例: 1280">
<div class="mq-unit">px</div>
</div>
<div class="mq-field">
<label>最小高さ（Min Height）</label>
<input type="number" id="mqMinH" min="0" max="9999" placeholder="任意">
<div class="mq-unit">px</div>
</div>
<div class="mq-field">
<label>最大高さ（Max Height）</label>
<input type="number" id="mqMaxH" min="0" max="9999" placeholder="任意">
<div class="mq-unit">px</div>
</div>
</div>
</div>

<!-- ===== メディア機能 ===== -->
<div class="mq-card">
<h2 class="mq-section-title">メディア機能</h2>
<div class="mq-feature-row" id="mqFeatureRow">

<label class="mq-feature-chip" id="mqChipScreen" onclick="mqToggleChip('mqChipScreen','mqFeatScreen')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatScreen">
screen（画面）
</label>

<label class="mq-feature-chip" id="mqChipPrint" onclick="mqToggleChip('mqChipPrint','mqFeatPrint')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatPrint">
print（印刷）
</label>

<label class="mq-feature-chip" id="mqChipOrient" onclick="mqToggleChip('mqChipOrient','mqFeatOrient')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatOrient">
向き (orientation):
<select class="mq-chip-select" id="mqOrientVal" onclick="event.stopPropagation()">
<option value="portrait">縦 (portrait)</option>
<option value="landscape">横 (landscape)</option>
</select>
</label>

<label class="mq-feature-chip" id="mqChipColor" onclick="mqToggleChip('mqChipColor','mqFeatColor')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatColor">
カラースキーム:
<select class="mq-chip-select" id="mqColorVal" onclick="event.stopPropagation()">
<option value="dark">ダーク (dark)</option>
<option value="light">ライト (light)</option>
</select>
</label>

<label class="mq-feature-chip" id="mqChipMotion" onclick="mqToggleChip('mqChipMotion','mqFeatMotion')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatMotion">
モーション削減:
<select class="mq-chip-select" id="mqMotionVal" onclick="event.stopPropagation()">
<option value="reduce">reduce</option>
<option value="no-preference">no-preference</option>
</select>
</label>

</div>
</div>

<!-- ===== 生成ボタン ===== -->
<button class="mq-generate-btn" onclick="mqGenerate()">@media クエリを生成する</button>

<!-- ===== ライブビューポート ===== -->
<div class="mq-card">
<h2 class="mq-section-title">ライブ ビューポートマッチ</h2>
<div class="mq-viewport-bar">
<span class="mq-vp-size" id="mqVpSize">ビューポート: — × —</span>
<span class="mq-vp-badge" id="mqVpBadge">
<span class="mq-vp-dot"></span>
<span id="mqVpText">まだクエリが生成されていません</span>
</span>
</div>
</div>

<!-- ===== 生成CSS ===== -->
<div class="mq-card">
<div class="mq-output-header">
<h2 class="mq-section-title" style="margin-bottom:0">生成された CSS</h2>
<button class="mq-copy-btn" id="mqCopyBtn" onclick="mqCopy()">CSSをコピー</button>
</div>
<pre class="mq-code" id="mqOutput"><span class="mq-cmt">/* ここに @media クエリが表示されます */</span></pre>
</div>

<!-- ===== クイックリファレンス ===== -->
<div class="mq-card">
<h2 class="mq-section-title">クイックリファレンス — よく使うブレイクポイント</h2>
<div class="mq-table-wrap">
<table class="mq-ref-table">
<thead>
<tr>
<th>名前</th>
<th>フレームワーク</th>
<th>ブレイクポイント</th>
<th>対象デバイス</th>
</tr>
</thead>
<tbody>
<tr>
<td class="mq-fw">xs</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>&lt; 576px</code></td>
<td>小型スマートフォン</td>
</tr>
<tr>
<td class="mq-fw">sm</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 576px</code></td>
<td>スマートフォン横向き</td>
</tr>
<tr>
<td class="mq-fw">md</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 768px</code></td>
<td>タブレット縦向き</td>
</tr>
<tr>
<td class="mq-fw">lg</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 992px</code></td>
<td>タブレット横向き・小型ノートPC</td>
</tr>
<tr>
<td class="mq-fw">xl</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 1200px</code></td>
<td>デスクトップ HD</td>
</tr>
<tr>
<td class="mq-fw">xxl</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 1400px</code></td>
<td>ワイドデスクトップ</td>
</tr>
<tr>
<td class="mq-fw">sm</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 640px</code></td>
<td>スマートフォン横向き</td>
</tr>
<tr>
<td class="mq-fw">md</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 768px</code></td>
<td>タブレット</td>
</tr>
<tr>
<td class="mq-fw">lg</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 1024px</code></td>
<td>ノートPC・大型タブレット</td>
</tr>
<tr>
<td class="mq-fw">xl</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 1280px</code></td>
<td>デスクトップ</td>
</tr>
<tr>
<td class="mq-fw">2xl</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 1536px</code></td>
<td>ワイド・4K</td>
</tr>
<tr>
<td class="mq-fw">モバイル</td>
<td><span class="mq-tag cu">カスタム</span></td>
<td><code>&lt; 768px</code></td>
<td>スマートフォン全般</td>
</tr>
<tr>
<td class="mq-fw">タブレット</td>
<td><span class="mq-tag cu">カスタム</span></td>
<td><code>768px–1199px</code></td>
<td>タブレット全向き</td>
</tr>
<tr>
<td class="mq-fw">デスクトップ</td>
<td><span class="mq-tag cu">カスタム</span></td>
<td><code>≥ 1200px</code></td>
<td>ノートPC・デスクトップ</td>
</tr>
<tr>
<td class="mq-fw">4K</td>
<td><span class="mq-tag cu">カスタム</span></td>
<td><code>≥ 2560px</code></td>
<td>ウルトラワイド・4Kディスプレイ</td>
</tr>
</tbody>
</table>
</div>
</div>

<!-- ===== 関連ツール ===== -->
<div class="mq-card">
<h2 class="mq-section-title">関連ツール</h2>
<div class="mq-links">
<a href="/tools/css-flexbox-generator/" class="mq-link">&#9633; CSS Flexboxジェネレーター</a>
<a href="/tools/css-grid-generator/" class="mq-link">&#9635; CSSグリッドジェネレーター</a>
<a href="/tools/screen-resolution-checker/" class="mq-link">&#128250; 画面解像度チェッカー</a>
</div>
</div>

<!-- ===== freee CTA ===== -->
<div class="mq-cta">
<h3>フリーランス・個人事業主の方へ</h3>
<p>レスポンシブデザインの制作費を確定申告でしっかり経費処理。<br>freee会計なら銀行・クレカを自動取得してラクに帳簿が完成します。</p>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" class="mq-cta-btn" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>

<script>
(function() {
'use strict';

var mqApproach = 'mobile-first';
var mqLastQuery = '';
var mqCurrentMediaFn = null;

/* ---- アプローチ ---- */
window.mqSetApproach = function(val, btn) {
mqApproach = val;
document.querySelectorAll('#mq-app .mq-approach-btn').forEach(function(b) {
b.classList.toggle('active', b === btn);
});
};

/* ---- プリセット ---- */
window.mqApplyPreset = function(btn) {
document.querySelectorAll('#mq-app .mq-preset-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
document.getElementById('mqMinW').value = btn.getAttribute('data-min');
document.getElementById('mqMaxW').value = btn.getAttribute('data-max');
document.getElementById('mqMinH').value = '';
document.getElementById('mqMaxH').value = '';
};

window.mqClearPreset = function(btn) {
document.querySelectorAll('#mq-app .mq-preset-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
['mqMinW','mqMaxW','mqMinH','mqMaxH'].forEach(function(id) {
document.getElementById(id).value = '';
});
};

/* ---- チップトグル ---- */
window.mqToggleChip = function(chipId, cbId) {
var chip = document.getElementById(chipId);
var cb   = document.getElementById(cbId);
cb.checked = !cb.checked;
chip.classList.toggle('active', cb.checked);
};

/* ---- シンタックスハイライト ---- */
function hl(str) {
return str
.replace(/(@media)/g, '<span class="mq-kw">$1</span>')
.replace(/\b(screen|print|all)\b/g, '<span class="mq-feat">$1</span>')
.replace(/\b(min-width|max-width|min-height|max-height|orientation|prefers-color-scheme|prefers-reduced-motion)\b/g, '<span class="mq-feat">$1</span>')
.replace(/\b(\d+px|portrait|landscape|dark|light|reduce|no-preference)\b/g, '<span class="mq-val">$1</span>');
}

/* ---- 条件ビルド ---- */
function buildConditions() {
var conds = [];
var minW = document.getElementById('mqMinW').value.trim();
var maxW = document.getElementById('mqMaxW').value.trim();
var minH = document.getElementById('mqMinH').value.trim();
var maxH = document.getElementById('mqMaxH').value.trim();

if (mqApproach === 'mobile-first') {
if (minW) conds.push('(min-width: ' + minW + 'px)');
if (maxW) conds.push('(max-width: ' + maxW + 'px)');
} else {
if (maxW) conds.push('(max-width: ' + maxW + 'px)');
if (minW) conds.push('(min-width: ' + minW + 'px)');
}
if (minH) conds.push('(min-height: ' + minH + 'px)');
if (maxH) conds.push('(max-height: ' + maxH + 'px)');

if (document.getElementById('mqFeatOrient').checked) {
conds.push('(orientation: ' + document.getElementById('mqOrientVal').value + ')');
}
if (document.getElementById('mqFeatColor').checked) {
conds.push('(prefers-color-scheme: ' + document.getElementById('mqColorVal').value + ')');
}
if (document.getElementById('mqFeatMotion').checked) {
conds.push('(prefers-reduced-motion: ' + document.getElementById('mqMotionVal').value + ')');
}
return conds;
}

function buildMediaType() {
var parts = [];
if (document.getElementById('mqFeatScreen').checked) parts.push('screen');
if (document.getElementById('mqFeatPrint').checked)  parts.push('print');
return parts.join(', ') || 'screen';
}

/* ---- 生成 ---- */
window.mqGenerate = function() {
var conds     = buildConditions();
var mediaType = buildMediaType();
var query;

if (conds.length === 0) {
query = '@media ' + mediaType + ' {\n  /* ここにスタイルを記述 */\n}';
} else if (conds.length === 1) {
query = '@media ' + mediaType + ' and ' + conds[0] + ' {\n  /* ここにスタイルを記述 */\n}';
} else {
query = '@media ' + mediaType + '\n  and ' + conds.join('\n  and ') + ' {\n  /* ここにスタイルを記述 */\n}';
}

mqLastQuery = query;
document.getElementById('mqOutput').innerHTML = hl(query);

var mmStr = (conds.length === 0)
? mediaType
: mediaType + ' and ' + conds.join(' and ');

try {
mqCurrentMediaFn = window.matchMedia(mmStr);
mqUpdateBadge(mqCurrentMediaFn.matches);
if (mqCurrentMediaFn.addEventListener) {
mqCurrentMediaFn.addEventListener('change', function(e) { mqUpdateBadge(e.matches); });
}
} catch(e) {
mqUpdateBadge(null);
}
};

/* ---- バッジ更新 ---- */
function mqUpdateBadge(matches) {
var badge = document.getElementById('mqVpBadge');
var text  = document.getElementById('mqVpText');
if (matches === null) {
badge.className = 'mq-vp-badge';
text.textContent = 'クエリを評価できませんでした';
} else if (matches) {
badge.className = 'mq-vp-badge match';
text.textContent = '現在のビューポートにマッチ！';
} else {
badge.className = 'mq-vp-badge';
text.textContent = '現在のビューポートにはマッチしていません';
}
}

/* ビューポートサイズ表示 */
function mqShowVp() {
document.getElementById('mqVpSize').textContent =
'ビューポート: ' + window.innerWidth + 'px × ' + window.innerHeight + 'px';
}
mqShowVp();
window.addEventListener('resize', function() {
mqShowVp();
if (mqCurrentMediaFn) mqUpdateBadge(mqCurrentMediaFn.matches);
});

/* ---- コピー ---- */
window.mqCopy = function() {
if (!mqLastQuery) return;
var btn = document.getElementById('mqCopyBtn');
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(mqLastQuery).then(function() { mqFlash(btn); });
} else {
var ta = document.createElement('textarea');
ta.value = mqLastQuery;
ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
mqFlash(btn);
}
};

function mqFlash(btn) {
btn.textContent = 'コピーしました！';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'CSSをコピー';
btn.classList.remove('copied');
}, 2000);
}
})();
</script>
</div>

---

## 使い方

1. **アプローチを選択** — モバイルファーストは `min-width` で小さい画面から拡張、デスクトップファーストは `max-width` で大きい画面から縮小します。
2. **デバイスプリセットを選ぶ**か、最小・最大の幅・高さを手動入力します。
3. **メディア機能をトグル** — 向き・ダークモード・モーション削減・印刷を追加できます。
4. **「@media クエリを生成する」**をクリックすると CSS コードとライブマッチ状況が表示されます。
5. **「CSSをコピー」**でクリップボードにコピーしてスタイルシートへ貼り付けます。

---

## モバイルファースト vs デスクトップファースト

| | モバイルファースト | デスクトップファースト |
|---|---|---|
| ベーススタイルの対象 | 最小画面 | 最大画面 |
| クエリタイプ | `min-width` | `max-width` |
| プログレッシブエンハンスメント | 対応 | 非対応 |
| フレームワーク対応 | Tailwind、Bootstrap 4+ | 旧来のフレームワーク |

**ベストプラクティス:** モバイルファーストが現代の標準です。詳細度の衝突を減らし、ベーススタイルをシンプルに保てます。

---

## `prefers-color-scheme` の活用

```css
/* OSがダークモードのときだけダークスタイルを適用 */
@media screen and (prefers-color-scheme: dark) {
body {
background: #0f172a;
color: #e2e8f0;
}
}
```

CSS カスタムプロパティ（変数）と組み合わせると、宣言の重複を避けられます。

---

## `prefers-reduced-motion` — アクセシビリティ

前庭障害やモーション感受性のあるユーザーは OS レベルでアニメーション削減を設定できます。必ず対応しましょう:

```css
@media (prefers-reduced-motion: reduce) {
*, *::before, *::after {
animation-duration: 0.01ms !important;
transition-duration: 0.01ms !important;
}
}
```

---

## 関連ツール

- [CSS Flexbox ジェネレーター](/tools/css-flexbox-generator/) — フレックスコンテナをビジュアルで構築
- [CSS グリッドジェネレーター](/tools/css-grid-generator/) — グリッドトラックとエリアをクリックで定義
- [画面解像度チェッカー](/tools/screen-resolution-checker/) — 正確な画面サイズとデバイスピクセル比を確認
