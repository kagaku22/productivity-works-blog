---
title: "グラデーションギャラリー"
date: 2025-08-27
description: "無料のCSSグラデーションギャラリー。100種類以上の美しいグラデーションプリセットを一覧表示。ワンクリックでCSSコピー。色や方向のカスタマイズ対応。"
categories: ["無料ツール"]
tags: ["cssグラデーション", "グラデーションギャラリー", "グラデーションプリセット", "ウェブデザイン", "配色", "cssツール"]
slug: "gradient-gallery"
cover:
  image: "/images/covers/gradient-gallery-ja.png"
  alt: "グラデーションギャラリー - 100種類以上のCSSグラデーション"
ShowToc: false
---

<div id="gg-app">

<style>
#gg-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
max-width: 1100px;
margin: 0 auto;
padding: 0 0 56px;
color: #1e293b;
}
#gg-app * { box-sizing: border-box; }

/* Controls */
#gg-controls {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 20px;
align-items: center;
}
#gg-search {
flex: 1;
min-width: 200px;
padding: 10px 16px;
border: 1.5px solid #cbd5e1;
border-radius: 10px;
font-size: 14px;
outline: none;
transition: border-color .2s;
background: #fff;
}
#gg-search:focus { border-color: #6366f1; }
#gg-filters {
display: flex;
flex-wrap: wrap;
gap: 6px;
}
.gg-filter {
padding: 7px 14px;
border: 1.5px solid #cbd5e1;
border-radius: 20px;
background: #fff;
font-size: 13px;
cursor: pointer;
transition: all .15s;
white-space: nowrap;
}
.gg-filter:hover { border-color: #6366f1; color: #6366f1; }
.gg-filter.active { background: #6366f1; border-color: #6366f1; color: #fff; }

/* Count */
#gg-count {
font-size: 13px;
color: #64748b;
margin-bottom: 16px;
}

/* Grid */
#gg-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
gap: 16px;
}
.gg-card {
border-radius: 14px;
overflow: hidden;
box-shadow: 0 2px 10px rgba(0,0,0,0.10);
cursor: pointer;
transition: transform .18s, box-shadow .18s;
background: #fff;
}
.gg-card:hover {
transform: translateY(-4px);
box-shadow: 0 8px 28px rgba(0,0,0,0.18);
}
.gg-swatch {
width: 100%;
height: 130px;
transition: background .3s;
}
.gg-info {
padding: 10px 12px 12px;
}
.gg-name {
font-size: 13px;
font-weight: 600;
color: #1e293b;
margin-bottom: 4px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
}
.gg-css-preview {
font-size: 10px;
color: #64748b;
font-family: 'SFMono-Regular', Consolas, monospace;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
margin-bottom: 8px;
}
.gg-copy-btn {
width: 100%;
padding: 7px;
border: none;
border-radius: 8px;
background: #f1f5f9;
color: #374151;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: background .15s, color .15s;
}
.gg-copy-btn:hover { background: #6366f1; color: #fff; }
.gg-copy-btn.copied { background: #22c55e; color: #fff; }

/* No results */
#gg-empty {
grid-column: 1/-1;
text-align: center;
padding: 60px 20px;
color: #94a3b8;
font-size: 15px;
display: none;
}

/* Customizer panel */
#gg-customizer {
position: fixed;
bottom: 0; right: 0;
width: 340px;
background: #fff;
border-top-left-radius: 18px;
border-top: 2px solid #e2e8f0;
border-left: 2px solid #e2e8f0;
box-shadow: -4px -4px 24px rgba(0,0,0,0.12);
padding: 20px;
z-index: 999;
display: none;
}
#gg-customizer.open { display: block; }
#gg-cust-title {
font-size: 14px;
font-weight: 700;
color: #1e293b;
margin-bottom: 14px;
display: flex;
justify-content: space-between;
align-items: center;
}
#gg-cust-close {
background: none;
border: none;
font-size: 20px;
cursor: pointer;
color: #64748b;
line-height: 1;
}
#gg-cust-preview {
width: 100%;
height: 80px;
border-radius: 10px;
margin-bottom: 14px;
transition: background .2s;
}
.gg-cust-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 10px;
font-size: 13px;
color: #374151;
}
.gg-cust-row label { min-width: 60px; font-weight: 600; }
.gg-cust-row input[type="color"] {
width: 40px; height: 32px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
cursor: pointer;
padding: 2px;
background: none;
}
.gg-cust-row input[type="range"] {
flex: 1;
accent-color: #6366f1;
}
.gg-cust-row select {
flex: 1;
padding: 6px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 13px;
outline: none;
}
#gg-cust-code {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 10px;
font-size: 11px;
font-family: 'SFMono-Regular', Consolas, monospace;
color: #374151;
word-break: break-all;
margin-bottom: 10px;
min-height: 52px;
}
#gg-cust-copy {
width: 100%;
padding: 9px;
border: none;
border-radius: 9px;
background: #6366f1;
color: #fff;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: background .15s;
}
#gg-cust-copy:hover { background: #4f46e5; }
#gg-cust-copy.copied { background: #22c55e; }

/* Fullscreen */
#gg-fullscreen {
display: none;
position: fixed;
inset: 0;
z-index: 9999;
align-items: center;
justify-content: center;
flex-direction: column;
cursor: pointer;
}
#gg-fullscreen.open { display: flex; }
#gg-fs-label {
position: absolute;
bottom: 30px;
background: rgba(0,0,0,0.5);
color: #fff;
padding: 8px 20px;
border-radius: 20px;
font-size: 13px;
pointer-events: none;
}

/* Toast */
#gg-toast {
position: fixed;
bottom: 32px;
left: 50%;
transform: translateX(-50%) translateY(60px);
background: #1e293b;
color: #fff;
padding: 10px 22px;
border-radius: 24px;
font-size: 13px;
font-weight: 600;
z-index: 10000;
opacity: 0;
transition: opacity .25s, transform .25s;
pointer-events: none;
}
#gg-toast.show {
opacity: 1;
transform: translateX(-50%) translateY(0);
}

@media (max-width: 600px) {
#gg-customizer { width: 100%; border-radius: 18px 18px 0 0; border-left: none; }
#gg-grid { grid-template-columns: repeat(auto-fill, minmax(160px, 1fr)); }
.gg-swatch { height: 100px; }
}
</style>

<!-- コントロール -->
<div id="gg-controls">
<input type="text" id="gg-search" placeholder="グラデーションを検索..." aria-label="グラデーション検索">
<div id="gg-filters">
<button class="gg-filter active" data-family="all">すべて</button>
<button class="gg-filter" data-family="pink">ピンク</button>
<button class="gg-filter" data-family="red">レッド</button>
<button class="gg-filter" data-family="orange">オレンジ</button>
<button class="gg-filter" data-family="yellow">イエロー</button>
<button class="gg-filter" data-family="green">グリーン</button>
<button class="gg-filter" data-family="teal">ティール</button>
<button class="gg-filter" data-family="blue">ブルー</button>
<button class="gg-filter" data-family="purple">パープル</button>
<button class="gg-filter" data-family="dark">ダーク</button>
<button class="gg-filter" data-family="pastel">パステル</button>
<button class="gg-filter" data-family="warm">ウォーム</button>
<button class="gg-filter" data-family="multi">マルチ</button>
</div>
</div>
<div id="gg-count"></div>

<!-- グリッド -->
<div id="gg-grid">
<div id="gg-empty">グラデーションが見つかりません。別のキーワードをお試しください。</div>
</div>

<!-- カスタマイザー -->
<div id="gg-customizer">
<div id="gg-cust-title">
<span>カスタマイズ</span>
<button id="gg-cust-close" title="閉じる">&#x2715;</button>
</div>
<div id="gg-cust-preview"></div>
<div class="gg-cust-row">
<label>種類</label>
<select id="gg-cust-type">
<option value="linear">リニア</option>
<option value="radial">放射状</option>
<option value="conic">コニック</option>
</select>
</div>
<div class="gg-cust-row" id="gg-angle-row">
<label>角度</label>
<input type="range" id="gg-cust-angle" min="0" max="360" value="135">
<span id="gg-angle-val">135°</span>
</div>
<div class="gg-cust-row">
<label>色1</label>
<input type="color" id="gg-cust-c1" value="#667eea">
<span id="gg-c1-pct-wrap"><input type="number" id="gg-c1-pct" value="0" min="0" max="100" style="width:48px;border:1.5px solid #cbd5e1;border-radius:6px;padding:4px;font-size:12px;outline:none">%</span>
</div>
<div class="gg-cust-row">
<label>色2</label>
<input type="color" id="gg-cust-c2" value="#764ba2">
<span id="gg-c2-pct-wrap"><input type="number" id="gg-c2-pct" value="100" min="0" max="100" style="width:48px;border:1.5px solid #cbd5e1;border-radius:6px;padding:4px;font-size:12px;outline:none">%</span>
</div>
<div id="gg-cust-code"></div>
<button id="gg-cust-copy">CSSをコピー</button>
</div>

<!-- フルスクリーンオーバーレイ -->
<div id="gg-fullscreen" title="クリックして閉じる">
<div id="gg-fs-label">クリックして閉じる</div>
</div>

<!-- トースト -->
<div id="gg-toast">クリップボードにコピーしました！</div>

<script>
(function() {
'use strict';

const GRADIENTS = [
// ピンク
{ name: 'キャンディブリス', css: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)', family: ['pink', 'red'] },
{ name: 'ローズクォーツ', css: 'linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%)', family: ['pink', 'pastel', 'warm'] },
{ name: 'ピンクレモネード', css: 'linear-gradient(135deg, #f8acff 0%, #696eff 100%)', family: ['pink', 'purple'] },
{ name: 'フラミンゴ', css: 'linear-gradient(135deg, #f7797d 0%, #FBD786 50%, #C6FFDD 100%)', family: ['pink', 'multi'] },
{ name: '桜', css: 'linear-gradient(135deg, #FFB7B2 0%, #FFDAC1 100%)', family: ['pink', 'pastel'] },
{ name: 'ホットコーラル', css: 'linear-gradient(135deg, #FF6CAB 0%, #7366FF 100%)', family: ['pink', 'purple'] },
{ name: 'ブラッシュピーチ', css: 'linear-gradient(135deg, #fbc2eb 0%, #a6c1ee 100%)', family: ['pink', 'blue', 'pastel'] },
{ name: 'ローズゴールド', css: 'linear-gradient(135deg, #f3c4cc 0%, #d4a5a5 50%, #b07d7d 100%)', family: ['pink', 'warm'] },
{ name: 'コットンキャンディ', css: 'linear-gradient(135deg, #FDCBF1 0%, #E6DEE9 100%)', family: ['pink', 'pastel'] },

// レッド
{ name: 'クリムゾンタイド', css: 'linear-gradient(135deg, #C33764 0%, #1D2671 100%)', family: ['red', 'dark', 'blue'] },
{ name: 'スカーレット', css: 'linear-gradient(135deg, #ff416c 0%, #ff4b2b 100%)', family: ['red', 'orange'] },
{ name: 'ブラッドムーン', css: 'linear-gradient(135deg, #8B0000 0%, #FF4500 100%)', family: ['red', 'dark'] },
{ name: 'レッドベルベット', css: 'linear-gradient(135deg, #c0392b 0%, #8e44ad 100%)', family: ['red', 'purple'] },
{ name: '溶岩', css: 'linear-gradient(135deg, #ff0000 0%, #ff7300 50%, #ffcc00 100%)', family: ['red', 'orange', 'yellow', 'multi'] },
{ name: 'ベリージャム', css: 'linear-gradient(135deg, #9b2335 0%, #c0392b 50%, #e74c3c 100%)', family: ['red'] },
{ name: '花火', css: 'linear-gradient(135deg, #f12711 0%, #f5af19 100%)', family: ['red', 'orange'] },
{ name: 'チェリーポップ', css: 'linear-gradient(135deg, #eb3349 0%, #f45c43 100%)', family: ['red', 'orange'] },

// オレンジ
{ name: '日の出', css: 'linear-gradient(135deg, #f83600 0%, #f9d423 100%)', family: ['orange', 'yellow', 'warm'] },
{ name: '砂漠の太陽', css: 'linear-gradient(135deg, #FFD200 0%, #F7971E 100%)', family: ['orange', 'yellow', 'warm'] },
{ name: '紅葉', css: 'linear-gradient(135deg, #d4531a 0%, #f0a500 100%)', family: ['orange', 'warm'] },
{ name: 'マンゴータンゴ', css: 'linear-gradient(135deg, #FF8008 0%, #FFC837 100%)', family: ['orange', 'yellow'] },
{ name: 'エンバーグロウ', css: 'linear-gradient(135deg, #e14fad 0%, #f9d423 100%)', family: ['orange', 'pink', 'warm'] },
{ name: 'クリームシクル', css: 'linear-gradient(135deg, #FFB347 0%, #FFCC33 100%)', family: ['orange', 'yellow', 'pastel'] },
{ name: 'タンジェリンドリーム', css: 'linear-gradient(135deg, #FF6B35 0%, #F7C59F 100%)', family: ['orange', 'pastel'] },
{ name: 'ブロンズ', css: 'linear-gradient(135deg, #a0522d 0%, #d2691e 50%, #f4a460 100%)', family: ['orange', 'warm'] },

// イエロー
{ name: 'ゴールデンアワー', css: 'linear-gradient(135deg, #f6d365 0%, #fda085 100%)', family: ['yellow', 'orange', 'warm'] },
{ name: 'レモン', css: 'linear-gradient(135deg, #FFE000 0%, #799F0C 100%)', family: ['yellow', 'green'] },
{ name: 'ハニーコム', css: 'linear-gradient(135deg, #f7971e 0%, #ffd200 100%)', family: ['yellow', 'orange'] },
{ name: 'ひまわり', css: 'linear-gradient(135deg, #DAA520 0%, #FFD700 50%, #FFFACD 100%)', family: ['yellow', 'pastel'] },
{ name: 'カナリア', css: 'linear-gradient(135deg, #FDFC47 0%, #24FE41 100%)', family: ['yellow', 'green'] },
{ name: 'バタースコッチ', css: 'linear-gradient(135deg, #f7e98e 0%, #e8b86d 100%)', family: ['yellow', 'pastel', 'warm'] },
{ name: 'ネオンイエロー', css: 'linear-gradient(135deg, #ccff00 0%, #ffef00 100%)', family: ['yellow', 'green'] },

// グリーン
{ name: 'エメラルド', css: 'linear-gradient(135deg, #0f9b58 0%, #00bf8f 100%)', family: ['green', 'teal'] },
{ name: '森林', css: 'linear-gradient(135deg, #134e5e 0%, #71b280 100%)', family: ['green', 'teal', 'dark'] },
{ name: '草原', css: 'linear-gradient(135deg, #a8e063 0%, #56ab2f 100%)', family: ['green'] },
{ name: 'ライムソーダ', css: 'linear-gradient(135deg, #96fbc4 0%, #f9f586 100%)', family: ['green', 'yellow', 'pastel'] },
{ name: 'ミントチップ', css: 'linear-gradient(135deg, #b2fefa 0%, #0ed2f7 100%)', family: ['green', 'teal', 'pastel'] },
{ name: 'ジャングル', css: 'linear-gradient(135deg, #4ca1af 0%, #c4e0e5 100%)', family: ['green', 'teal', 'pastel'] },
{ name: '抹茶ラテ', css: 'linear-gradient(135deg, #C6D68F 0%, #F0E68C 100%)', family: ['green', 'yellow', 'pastel'] },
{ name: 'ネオンライム', css: 'linear-gradient(135deg, #39FF14 0%, #00bfff 100%)', family: ['green', 'blue'] },
{ name: '熱帯雨林', css: 'linear-gradient(135deg, #1a3c34 0%, #2d7a5f 50%, #4caf7d 100%)', family: ['green', 'dark'] },
{ name: 'キウイ', css: 'linear-gradient(135deg, #93f9b9 0%, #1d976c 100%)', family: ['green', 'teal'] },

// ティール
{ name: '海風', css: 'linear-gradient(135deg, #00b4db 0%, #0083b0 100%)', family: ['teal', 'blue'] },
{ name: 'アクアマリン', css: 'linear-gradient(135deg, #43e97b 0%, #38f9d7 100%)', family: ['teal', 'green'] },
{ name: 'ラグーン', css: 'linear-gradient(135deg, #43CBFF 0%, #9708CC 100%)', family: ['teal', 'purple'] },
{ name: 'シーフォーム', css: 'linear-gradient(135deg, #E0F7FA 0%, #80DEEA 50%, #00ACC1 100%)', family: ['teal', 'pastel'] },
{ name: '深海', css: 'linear-gradient(135deg, #001B2E 0%, #004E7C 50%, #0099AA 100%)', family: ['teal', 'dark', 'blue'] },
{ name: 'ターコイズ', css: 'linear-gradient(135deg, #11998e 0%, #38ef7d 100%)', family: ['teal', 'green'] },
{ name: 'アクアスプラッシュ', css: 'linear-gradient(135deg, #13547a 0%, #80d0c7 100%)', family: ['teal', 'blue'] },
{ name: '北極の霧', css: 'linear-gradient(135deg, #DFFFCD 0%, #90F9C4 50%, #39F3BB 100%)', family: ['teal', 'green', 'pastel'] },

// ブルー
{ name: 'ロイヤルブルー', css: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)', family: ['blue', 'purple'] },
{ name: 'ブルーベリー', css: 'linear-gradient(135deg, #1e3c72 0%, #2a5298 100%)', family: ['blue', 'dark'] },
{ name: 'スカイドリーム', css: 'linear-gradient(135deg, #89f7fe 0%, #66a6ff 100%)', family: ['blue', 'pastel'] },
{ name: 'サファイア', css: 'linear-gradient(135deg, #0F2027 0%, #203A43 50%, #2C5364 100%)', family: ['blue', 'dark'] },
{ name: '真夜中', css: 'linear-gradient(135deg, #2c3e50 0%, #4ca1af 100%)', family: ['blue', 'dark', 'teal'] },
{ name: 'コバルト', css: 'linear-gradient(135deg, #004bff 0%, #007cff 100%)', family: ['blue'] },
{ name: 'エレクトリックブルー', css: 'linear-gradient(135deg, #0072ff 0%, #00c6ff 100%)', family: ['blue', 'teal'] },
{ name: 'デニム', css: 'linear-gradient(135deg, #1e3a5f 0%, #2980b9 100%)', family: ['blue', 'dark'] },
{ name: '北極オーロラ', css: 'linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%)', family: ['blue', 'dark'] },
{ name: 'ベビーブルー', css: 'linear-gradient(135deg, #c2e9fb 0%, #a1c4fd 100%)', family: ['blue', 'pastel'] },
{ name: '氷河', css: 'linear-gradient(135deg, #E8F4FD 0%, #AED6F1 100%)', family: ['blue', 'pastel'] },
{ name: 'ネプチューン', css: 'linear-gradient(135deg, #24C6DC 0%, #514A9D 100%)', family: ['blue', 'purple'] },

// パープル
{ name: 'アメジスト', css: 'linear-gradient(135deg, #9D50BB 0%, #6E48AA 100%)', family: ['purple'] },
{ name: 'グレープ', css: 'linear-gradient(135deg, #4776E6 0%, #8E54E9 100%)', family: ['purple', 'blue'] },
{ name: '黄昏', css: 'linear-gradient(135deg, #a18cd1 0%, #fbc2eb 100%)', family: ['purple', 'pink', 'pastel'] },
{ name: 'コズミック', css: 'linear-gradient(135deg, #020024 0%, #090979 50%, #00d4ff 100%)', family: ['purple', 'blue', 'dark'] },
{ name: 'ラベンダー', css: 'linear-gradient(135deg, #e9d5ff 0%, #a855f7 100%)', family: ['purple', 'pastel'] },
{ name: '銀河', css: 'linear-gradient(135deg, #2c1654 0%, #6a0572 50%, #d63031 100%)', family: ['purple', 'dark', 'red'] },
{ name: 'プラム', css: 'linear-gradient(135deg, #4B0082 0%, #8B00FF 100%)', family: ['purple', 'dark'] },
{ name: 'ライラック', css: 'linear-gradient(135deg, #c3cfe2 0%, #f5f7fa 100%)', family: ['purple', 'pastel'] },
{ name: 'ウルトラバイオレット', css: 'linear-gradient(135deg, #5f0a87 0%, #a4508b 100%)', family: ['purple'] },
{ name: 'トワイライト', css: 'linear-gradient(135deg, #0F0C29 0%, #302B63 50%, #24243e 100%)', family: ['purple', 'dark'] },

// ダーク
{ name: 'オブシディアン', css: 'linear-gradient(135deg, #1a1a2e 0%, #16213e 100%)', family: ['dark'] },
{ name: 'カーボン', css: 'linear-gradient(135deg, #1c1c1c 0%, #3d3d3d 100%)', family: ['dark'] },
{ name: 'ガンメタル', css: 'linear-gradient(135deg, #29323c 0%, #485563 100%)', family: ['dark'] },
{ name: 'シャドウ', css: 'linear-gradient(135deg, #000000 0%, #434343 100%)', family: ['dark'] },
{ name: 'スレート', css: 'linear-gradient(135deg, #0f2027 0%, #203a43 100%)', family: ['dark', 'blue'] },
{ name: 'ノワール', css: 'linear-gradient(135deg, #000000 0%, #7b7b7b 100%)', family: ['dark'] },
{ name: 'アッシュ', css: 'linear-gradient(135deg, #606c88 0%, #3f4c6b 100%)', family: ['dark', 'blue'] },
{ name: 'チャコール', css: 'linear-gradient(135deg, #333333 0%, #dd1818 100%)', family: ['dark', 'red'] },
{ name: 'ストーム', css: 'linear-gradient(135deg, #373B44 0%, #4286f4 100%)', family: ['dark', 'blue'] },

// パステル
{ name: 'パステルレインボー', css: 'linear-gradient(135deg, #FFDEE9 0%, #B5FFFC 100%)', family: ['pastel', 'multi'] },
{ name: 'ソフトピーチ', css: 'linear-gradient(135deg, #FFE0B2 0%, #FFCCBC 100%)', family: ['pastel', 'orange', 'warm'] },
{ name: '夢見る', css: 'linear-gradient(135deg, #e0c3fc 0%, #8ec5fc 100%)', family: ['pastel', 'purple', 'blue'] },
{ name: '雲の上', css: 'linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%)', family: ['pastel', 'blue'] },
{ name: 'ソルベ', css: 'linear-gradient(135deg, #fccb90 0%, #d57eeb 100%)', family: ['pastel', 'pink', 'orange'] },
{ name: 'メロン', css: 'linear-gradient(135deg, #fddb92 0%, #d1fdff 100%)', family: ['pastel', 'yellow'] },
{ name: 'パウダーブルー', css: 'linear-gradient(135deg, #dfe9f3 0%, #ffffff 100%)', family: ['pastel', 'blue'] },
{ name: 'バブルガム', css: 'linear-gradient(135deg, #FFC8DD 0%, #BDE0FE 100%)', family: ['pastel', 'pink', 'blue'] },
{ name: 'アイスクリーム', css: 'linear-gradient(135deg, #ffc3a0 0%, #FFAFBD 100%)', family: ['pastel', 'pink', 'orange'] },
{ name: 'ソフトミント', css: 'linear-gradient(135deg, #B5EAD7 0%, #C7CEEA 100%)', family: ['pastel', 'green', 'purple'] },

// ウォーム
{ name: 'モハベ', css: 'linear-gradient(135deg, #f9a825 0%, #e65100 100%)', family: ['warm', 'orange'] },
{ name: 'キャラメル', css: 'linear-gradient(135deg, #C6A35D 0%, #8B5E3C 100%)', family: ['warm', 'orange'] },
{ name: 'テラコッタ', css: 'linear-gradient(135deg, #C46A39 0%, #7C3C21 100%)', family: ['warm', 'red', 'orange'] },
{ name: 'シナモン', css: 'linear-gradient(135deg, #D2691E 0%, #F4A460 100%)', family: ['warm', 'orange'] },
{ name: 'ピーチファズ', css: 'linear-gradient(135deg, #FFBE98 0%, #FFD3BA 100%)', family: ['warm', 'orange', 'pastel'] },

// マルチ
{ name: 'プリズム', css: 'linear-gradient(135deg, #ff0000, #ff7700, #ffff00, #00ff00, #0000ff, #8b00ff)', family: ['multi'] },
{ name: 'オーロラ', css: 'linear-gradient(135deg, #43e97b 0%, #38f9d7 33%, #4facfe 66%, #a18cd1 100%)', family: ['multi', 'green', 'blue', 'purple'] },
{ name: 'カーニバル', css: 'linear-gradient(135deg, #FF3CAC 0%, #784BA0 50%, #2B86C5 100%)', family: ['multi', 'pink', 'purple', 'blue'] },
{ name: 'ホログラフィック', css: 'linear-gradient(135deg, #a8edea 0%, #fed6e3 33%, #ffecd2 66%, #a8edea 100%)', family: ['multi', 'pastel'] },
{ name: '夕焼け', css: 'linear-gradient(135deg, #FDBB2D 0%, #3A1C71 100%)', family: ['multi', 'yellow', 'purple'] },
{ name: 'オパール', css: 'linear-gradient(135deg, #c3cfe2 0%, #f5f7fa 25%, #e0c3fc 75%, #8ec5fc 100%)', family: ['multi', 'pastel'] },
{ name: 'ヴェイパーウェーブ', css: 'linear-gradient(135deg, #ff71ce 0%, #01cdfe 50%, #05ffa1 100%)', family: ['multi', 'pink', 'teal', 'green'] },
{ name: 'ネオンオーロラ', css: 'linear-gradient(135deg, #00c6ff 0%, #0072ff 33%, #a100ff 66%, #ff00ff 100%)', family: ['multi', 'blue', 'purple'] },
{ name: 'タイダイ', css: 'linear-gradient(135deg, #FF61D2 0%, #FE9090 25%, #FFED86 50%, #83FF85 75%, #92FFFC 100%)', family: ['multi', 'pastel'] },
{ name: 'オイルスリック', css: 'linear-gradient(135deg, #202020 0%, #1e3a5f 25%, #4a0e8f 50%, #8b0000 75%, #202020 100%)', family: ['multi', 'dark'] },

// 特殊
{ name: '星雲', css: 'radial-gradient(ellipse at top, #1a1a3e 0%, #6b21a8 50%, #1a1a3e 100%)', family: ['purple', 'dark'] },
{ name: '太陽', css: 'radial-gradient(circle at center, #FFD700 0%, #FF8C00 50%, #FF4500 100%)', family: ['yellow', 'orange', 'warm'] },
{ name: '月の出', css: 'radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%)', family: ['dark', 'blue'] },
{ name: 'ハロー', css: 'radial-gradient(circle at center, #ffffff 0%, #e8f4fd 40%, #aed6f1 100%)', family: ['blue', 'pastel'] },
{ name: 'ネオングロウ', css: 'radial-gradient(circle at center, #39ff14 0%, #001a00 100%)', family: ['green', 'dark'] },
{ name: 'コニックホイール', css: 'conic-gradient(from 0deg, #ff0000, #ffff00, #00ff00, #00ffff, #0000ff, #ff00ff, #ff0000)', family: ['multi'] },
{ name: 'コニックパステル', css: 'conic-gradient(from 45deg, #fbc2eb, #a6c1ee, #ffecd2, #d4fc79, #fbc2eb)', family: ['multi', 'pastel'] },
{ name: 'パイスライス', css: 'conic-gradient(#e74c3c 0deg 90deg, #3498db 90deg 180deg, #2ecc71 180deg 270deg, #f39c12 270deg 360deg)', family: ['multi'] },
];

let currentFamily = 'all';
let currentSearch = '';
let custGradient = null;

const grid = document.getElementById('gg-grid');
const empty = document.getElementById('gg-empty');
const countEl = document.getElementById('gg-count');
const searchEl = document.getElementById('gg-search');
const customizer = document.getElementById('gg-customizer');
const custPreview = document.getElementById('gg-cust-preview');
const custType = document.getElementById('gg-cust-type');
const custAngle = document.getElementById('gg-cust-angle');
const angleVal = document.getElementById('gg-angle-val');
const angleRow = document.getElementById('gg-angle-row');
const custC1 = document.getElementById('gg-cust-c1');
const custC2 = document.getElementById('gg-cust-c2');
const c1Pct = document.getElementById('gg-c1-pct');
const c2Pct = document.getElementById('gg-c2-pct');
const custCode = document.getElementById('gg-cust-code');
const custCopy = document.getElementById('gg-cust-copy');
const fullscreen = document.getElementById('gg-fullscreen');
const toast = document.getElementById('gg-toast');

function showToast(msg) {
toast.textContent = msg;
toast.classList.add('show');
setTimeout(() => toast.classList.remove('show'), 2000);
}

function copyText(text) {
if (navigator.clipboard) {
navigator.clipboard.writeText(text).catch(() => fallbackCopy(text));
} else {
fallbackCopy(text);
}
}

function fallbackCopy(text) {
const ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
}

function matchesFilter(g) {
if (currentFamily !== 'all' && !g.family.includes(currentFamily)) return false;
if (currentSearch) {
const q = currentSearch.toLowerCase();
if (!g.name.toLowerCase().includes(q) && !g.css.toLowerCase().includes(q) && !g.family.join(' ').includes(q)) return false;
}
return true;
}

function buildGrid() {
const cards = grid.querySelectorAll('.gg-card');
cards.forEach(c => c.remove());

const filtered = GRADIENTS.filter(matchesFilter);
countEl.textContent = filtered.length + '件のグラデーション';

if (filtered.length === 0) {
empty.style.display = 'block';
return;
}
empty.style.display = 'none';

filtered.forEach((g) => {
const card = document.createElement('div');
card.className = 'gg-card';
card.innerHTML =
'<div class="gg-swatch" style="background:' + g.css + '"></div>' +
'<div class="gg-info">' +
'<div class="gg-name">' + escHtml(g.name) + '</div>' +
'<div class="gg-css-preview">' + escHtml(g.css) + '</div>' +
'<button class="gg-copy-btn">CSSをコピー</button>' +
'</div>';

const swatch = card.querySelector('.gg-swatch');
const btn = card.querySelector('.gg-copy-btn');

swatch.addEventListener('click', () => openCustomizer(g));
card.querySelector('.gg-name').addEventListener('click', () => openCustomizer(g));

btn.addEventListener('click', (e) => {
e.stopPropagation();
const css = 'background: ' + g.css + ';';
copyText(css);
btn.textContent = 'コピー完了！';
btn.classList.add('copied');
showToast('クリップボードにコピーしました！');
setTimeout(() => {
btn.textContent = 'CSSをコピー';
btn.classList.remove('copied');
}, 1800);
});

swatch.addEventListener('dblclick', (e) => {
e.stopPropagation();
openFullscreen(g.css);
});

grid.appendChild(card);
});
}

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function openCustomizer(g) {
custGradient = g;
if (g.css.startsWith('radial')) {
custType.value = 'radial';
} else if (g.css.startsWith('conic')) {
custType.value = 'conic';
} else {
custType.value = 'linear';
}
const colorMatch = g.css.match(/#[0-9a-fA-F]{3,6}/g);
if (colorMatch && colorMatch.length >= 2) {
custC1.value = normalizeHex(colorMatch[0]);
custC2.value = normalizeHex(colorMatch[colorMatch.length - 1]);
}
c1Pct.value = 0;
c2Pct.value = 100;
const angleMatch = g.css.match(/(\d+)deg/);
if (angleMatch) {
custAngle.value = parseInt(angleMatch[1]);
angleVal.textContent = custAngle.value + '°';
}
updateAngleRow();
updateCustPreview();
customizer.classList.add('open');
}

function normalizeHex(hex) {
if (hex.length === 4) {
return '#' + hex[1]+hex[1]+hex[2]+hex[2]+hex[3]+hex[3];
}
return hex;
}

function updateAngleRow() {
angleRow.style.display = custType.value === 'linear' ? 'flex' : 'none';
}

function buildCustCSS() {
const c1 = custC1.value, c2 = custC2.value;
const p1 = c1Pct.value, p2 = c2Pct.value;
const angle = custAngle.value;
const type = custType.value;
if (type === 'radial') {
return 'radial-gradient(ellipse at center, ' + c1 + ' ' + p1 + '%, ' + c2 + ' ' + p2 + '%)';
} else if (type === 'conic') {
return 'conic-gradient(from ' + angle + 'deg, ' + c1 + ' 0%, ' + c2 + ' 100%)';
} else {
return 'linear-gradient(' + angle + 'deg, ' + c1 + ' ' + p1 + '%, ' + c2 + ' ' + p2 + '%)';
}
}

function updateCustPreview() {
const css = buildCustCSS();
custPreview.style.background = css;
custCode.textContent = 'background: ' + css + ';';
}

custType.addEventListener('change', () => { updateAngleRow(); updateCustPreview(); });
custAngle.addEventListener('input', () => { angleVal.textContent = custAngle.value + '°'; updateCustPreview(); });
custC1.addEventListener('input', updateCustPreview);
custC2.addEventListener('input', updateCustPreview);
c1Pct.addEventListener('input', updateCustPreview);
c2Pct.addEventListener('input', updateCustPreview);

custCopy.addEventListener('click', () => {
const css = custCode.textContent;
copyText(css);
custCopy.textContent = 'コピー完了！';
custCopy.classList.add('copied');
showToast('クリップボードにコピーしました！');
setTimeout(() => {
custCopy.textContent = 'CSSをコピー';
custCopy.classList.remove('copied');
}, 1800);
});

document.getElementById('gg-cust-close').addEventListener('click', () => {
customizer.classList.remove('open');
});

function openFullscreen(css) {
fullscreen.style.background = css;
fullscreen.classList.add('open');
}

fullscreen.addEventListener('click', () => {
fullscreen.classList.remove('open');
});

searchEl.addEventListener('input', () => {
currentSearch = searchEl.value.trim();
buildGrid();
});

document.querySelectorAll('.gg-filter').forEach(btn => {
btn.addEventListener('click', () => {
document.querySelectorAll('.gg-filter').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
currentFamily = btn.dataset.family;
buildGrid();
});
});

buildGrid();
})();
</script>

</div>

100種類以上のCSSグラデーションプリセットを一覧で閲覧できます。カードをクリックするとカスタマイザーが開き、色・角度・種類を自由に調整できます。スウォッチをダブルクリックするとフルスクリーンプレビューが表示されます。

---

## 関連ツール

> グラデーションを自由に作成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)

> 配色インスピレーション → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)

---

**Webデザインの収支管理も効率化しませんか？**

フリーランスのデザイナー・エンジニアの請求書発行・経費管理・確定申告はクラウド会計ソフト「freee」で効率化しませんか？

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
