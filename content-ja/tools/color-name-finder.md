---
title: "カラーネームファインダー"
description: "無料の色名検索ツール。HEX・RGB・HSLを入力して最も近いCSS色名を検索。148色のCSS名前付きカラーを一覧表示・検索・コピー。Webデザインに最適。"
date: 2025-06-08
slug: color-name-finder
categories: ["無料ツール"]
tags: ["カラー", "CSS", "デザイン", "Webツール"]
cover:
  image: /images/covers/color-name-finder-ja.png
  alt: "カラーネームファインダー"
ShowToc: false
---

HEX・RGB・HSL値を入力して、最も近いCSS名前付きカラーを即座に検索。148色のCSS色名を一覧表示・検索・コピーできます。

<div id="cn-app">
<style>
#cn-app { font-family: system-ui, -apple-system, sans-serif; color: #1e293b; }
#cn-app *, #cn-app *::before, #cn-app *::after { box-sizing: border-box; }
#cn-app h2 { font-size: 1.1rem; font-weight: 700; margin: 0 0 12px; color: #0f172a; }
#cn-app .cn-card { background: #fff; border: 1px solid #e2e8f0; border-radius: 12px; padding: 20px; margin-bottom: 18px; }
#cn-app .cn-row { display: flex; gap: 14px; flex-wrap: wrap; align-items: flex-end; }
#cn-app .cn-field { display: flex; flex-direction: column; gap: 5px; }
#cn-app label { font-size: 12px; font-weight: 600; color: #64748b; text-transform: uppercase; letter-spacing: .04em; }
#cn-app input[type=text], #cn-app input[type=number] { padding: 8px 10px; border: 1.5px solid #cbd5e1; border-radius: 7px; font-size: 14px; width: 120px; outline: none; transition: border-color .2s; }
#cn-app input[type=text]:focus, #cn-app input[type=number]:focus { border-color: #6366f1; }
#cn-app input[type=color] { width: 44px; height: 38px; padding: 2px; border: 1.5px solid #cbd5e1; border-radius: 7px; cursor: pointer; background: #fff; }
#cn-app input[type=range] { width: 100px; accent-color: #6366f1; }
#cn-app .cn-btn { padding: 9px 18px; background: #6366f1; color: #fff; border: none; border-radius: 7px; font-size: 13px; font-weight: 700; cursor: pointer; transition: background .2s; white-space: nowrap; }
#cn-app .cn-btn:hover { background: #4f46e5; }
#cn-app .cn-btn-sm { padding: 5px 11px; font-size: 12px; background: #f1f5f9; color: #334155; border: 1px solid #cbd5e1; border-radius: 6px; cursor: pointer; font-weight: 600; transition: background .2s; }
#cn-app .cn-btn-sm:hover { background: #e2e8f0; }
#cn-app .cn-swatch-row { display: flex; gap: 14px; flex-wrap: wrap; margin-top: 14px; }
#cn-app .cn-swatch-box { flex: 1; min-width: 160px; border-radius: 10px; overflow: hidden; border: 1px solid #e2e8f0; }
#cn-app .cn-swatch-color { height: 80px; }
#cn-app .cn-swatch-info { padding: 10px 12px; background: #f8fafc; }
#cn-app .cn-swatch-label { font-size: 11px; color: #64748b; font-weight: 600; text-transform: uppercase; margin-bottom: 4px; }
#cn-app .cn-swatch-name { font-size: 15px; font-weight: 700; color: #0f172a; margin-bottom: 6px; }
#cn-app .cn-values { display: flex; flex-direction: column; gap: 3px; }
#cn-app .cn-val-row { display: flex; align-items: center; gap: 6px; font-size: 12px; }
#cn-app .cn-val-label { color: #94a3b8; width: 28px; flex-shrink: 0; }
#cn-app .cn-val-text { font-family: monospace; color: #334155; flex: 1; }
#cn-app .cn-copy-icon { cursor: pointer; color: #94a3b8; font-size: 11px; padding: 2px 5px; border-radius: 4px; border: 1px solid #e2e8f0; background: #fff; }
#cn-app .cn-copy-icon:hover { background: #6366f1; color: #fff; border-color: #6366f1; }
#cn-app .cn-distance { margin-top: 10px; font-size: 12px; color: #64748b; background: #f8fafc; padding: 7px 10px; border-radius: 7px; }
#cn-app .cn-distance span { font-weight: 700; color: #6366f1; }
#cn-app .cn-search-row { display: flex; gap: 10px; flex-wrap: wrap; align-items: center; margin-bottom: 14px; }
#cn-app .cn-search-row input[type=text] { width: 200px; }
#cn-app .cn-filter-btns { display: flex; gap: 6px; flex-wrap: wrap; }
#cn-app .cn-filter-btn { padding: 5px 11px; font-size: 12px; border-radius: 20px; border: 1.5px solid #cbd5e1; background: #fff; cursor: pointer; font-weight: 600; color: #475569; transition: all .15s; }
#cn-app .cn-filter-btn.active, #cn-app .cn-filter-btn:hover { background: #6366f1; color: #fff; border-color: #6366f1; }
#cn-app .cn-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(110px, 1fr)); gap: 8px; }
#cn-app .cn-color-card { border-radius: 8px; overflow: hidden; border: 2px solid transparent; cursor: pointer; transition: all .15s; }
#cn-app .cn-color-card:hover, #cn-app .cn-color-card.selected { border-color: #6366f1; box-shadow: 0 0 0 2px #a5b4fc; }
#cn-app .cn-color-card-swatch { height: 54px; }
#cn-app .cn-color-card-name { font-size: 10px; padding: 5px 6px; background: #f8fafc; font-weight: 600; color: #334155; line-height: 1.3; word-break: break-word; }
#cn-app .cn-modal-overlay { display: none; position: fixed; inset: 0; background: rgba(0,0,0,.45); z-index: 9999; align-items: center; justify-content: center; }
#cn-app .cn-modal-overlay.open { display: flex; }
#cn-app .cn-modal { background: #fff; border-radius: 14px; padding: 24px; max-width: 340px; width: 90%; box-shadow: 0 20px 60px rgba(0,0,0,.2); position: relative; }
#cn-app .cn-modal-close { position: absolute; top: 12px; right: 14px; background: none; border: none; font-size: 20px; cursor: pointer; color: #94a3b8; }
#cn-app .cn-modal-swatch { height: 90px; border-radius: 8px; margin-bottom: 14px; }
#cn-app .cn-modal-name { font-size: 20px; font-weight: 800; color: #0f172a; margin-bottom: 12px; }
#cn-app .cn-modal-vals { display: flex; flex-direction: column; gap: 7px; }
#cn-app .cn-modal-val-row { display: flex; align-items: center; gap: 8px; background: #f8fafc; padding: 7px 10px; border-radius: 7px; }
#cn-app .cn-modal-val-label { font-size: 11px; font-weight: 700; color: #94a3b8; text-transform: uppercase; width: 30px; }
#cn-app .cn-modal-val-text { font-family: monospace; font-size: 13px; color: #334155; flex: 1; }
#cn-app .cn-modal-copy { padding: 4px 10px; font-size: 11px; font-weight: 700; background: #6366f1; color: #fff; border: none; border-radius: 5px; cursor: pointer; }
#cn-app .cn-tabs { display: flex; gap: 0; border-bottom: 2px solid #e2e8f0; margin-bottom: 18px; }
#cn-app .cn-tab { padding: 9px 18px; font-size: 13px; font-weight: 700; border: none; background: none; cursor: pointer; color: #64748b; border-bottom: 2px solid transparent; margin-bottom: -2px; transition: all .15s; }
#cn-app .cn-tab.active { color: #6366f1; border-bottom-color: #6366f1; }
#cn-app .cn-section { display: none; }
#cn-app .cn-section.active { display: block; }
#cn-app .cn-rgb-sliders { display: flex; flex-direction: column; gap: 8px; }
#cn-app .cn-slider-row { display: flex; align-items: center; gap: 8px; }
#cn-app .cn-slider-row label { width: 14px; font-size: 12px; font-weight: 700; }
#cn-app .cn-slider-row span { font-size: 12px; font-family: monospace; width: 28px; text-align: right; }
#cn-app .cn-notice { font-size: 12px; color: #64748b; margin-top: 10px; }
#cn-app .cn-count { font-size: 12px; color: #94a3b8; margin-bottom: 8px; }
#cn-app .cn-freee-cta { margin-top: 28px; padding: 18px 20px; background: linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%); border: 1.5px solid #bae6fd; border-radius: 10px; }
@media (max-width: 480px) {
#cn-app .cn-row { flex-direction: column; }
#cn-app input[type=text], #cn-app input[type=number] { width: 100%; }
#cn-app .cn-search-row input[type=text] { width: 100%; }
}
</style>

<!-- Input Section -->
<div class="cn-card">
<h2>最も近いCSS色名を検索</h2>
<div class="cn-tabs">
<button class="cn-tab active" onclick="(function(){document.querySelectorAll('#cn-app .cn-tab').forEach(t=>t.classList.remove('active'));this.classList.add('active');document.querySelectorAll('#cn-app .cn-section').forEach(s=>s.classList.remove('active'));document.getElementById('cn-sec-hex').classList.add('active');}).call(this)">HEX</button>
<button class="cn-tab" onclick="(function(){document.querySelectorAll('#cn-app .cn-tab').forEach(t=>t.classList.remove('active'));this.classList.add('active');document.querySelectorAll('#cn-app .cn-section').forEach(s=>s.classList.remove('active'));document.getElementById('cn-sec-rgb').classList.add('active');}).call(this)">RGB</button>
<button class="cn-tab" onclick="(function(){document.querySelectorAll('#cn-app .cn-tab').forEach(t=>t.classList.remove('active'));this.classList.add('active');document.querySelectorAll('#cn-app .cn-section').forEach(s=>s.classList.remove('active'));document.getElementById('cn-sec-pick').classList.add('active');}).call(this)">ピッカー</button>
</div>

<div id="cn-sec-hex" class="cn-section active">
<div class="cn-row">
<div class="cn-field">
<label>HEXカラー</label>
<input type="text" id="cn-hex-input" placeholder="#6366f1" maxlength="7" style="width:140px;">
</div>
<button class="cn-btn" onclick="cnApp.findFromHex()">色名を検索</button>
</div>
<p class="cn-notice">6桁のHEXコードを入力してください（例: #ff6347）</p>
</div>

<div id="cn-sec-rgb" class="cn-section">
<div class="cn-rgb-sliders">
<div class="cn-slider-row">
<label style="color:#ef4444;">R</label>
<input type="range" min="0" max="255" value="99" id="cn-r-slider" oninput="cnApp.updateRgbFromSliders()">
<input type="number" min="0" max="255" value="99" id="cn-r-num" style="width:60px;" oninput="cnApp.updateSlidersFromNum()">
</div>
<div class="cn-slider-row">
<label style="color:#22c55e;">G</label>
<input type="range" min="0" max="255" value="102" id="cn-g-slider" oninput="cnApp.updateRgbFromSliders()">
<input type="number" min="0" max="255" value="102" id="cn-g-num" style="width:60px;" oninput="cnApp.updateSlidersFromNum()">
</div>
<div class="cn-slider-row">
<label style="color:#3b82f6;">B</label>
<input type="range" min="0" max="255" value="241" id="cn-b-slider" oninput="cnApp.updateRgbFromSliders()">
<input type="number" min="0" max="255" value="241" id="cn-b-num" style="width:60px;" oninput="cnApp.updateSlidersFromNum()">
</div>
</div>
<div style="margin-top:12px;">
<button class="cn-btn" onclick="cnApp.findFromRgb()">色名を検索</button>
</div>
</div>

<div id="cn-sec-pick" class="cn-section">
<div class="cn-row">
<div class="cn-field">
<label>カラーピッカー</label>
<input type="color" id="cn-color-picker" value="#6366f1" oninput="cnApp.findFromPicker()">
</div>
<span style="font-size:13px;color:#64748b;align-self:center;">色を選んでCSS名を検索</span>
</div>
</div>
</div>

<!-- Result Section -->
<div class="cn-card" id="cn-result-card" style="display:none;">
<h2>検索結果</h2>
<div class="cn-swatch-row">
<div class="cn-swatch-box">
<div class="cn-swatch-color" id="cn-input-swatch"></div>
<div class="cn-swatch-info">
<div class="cn-swatch-label">入力した色</div>
<div class="cn-values" id="cn-input-vals"></div>
</div>
</div>
<div class="cn-swatch-box">
<div class="cn-swatch-color" id="cn-match-swatch"></div>
<div class="cn-swatch-info">
<div class="cn-swatch-label">最も近いCSS色名</div>
<div class="cn-swatch-name" id="cn-match-name"></div>
<div class="cn-values" id="cn-match-vals"></div>
</div>
</div>
</div>
<div class="cn-distance" id="cn-distance-info"></div>
</div>

<!-- Browse Section -->
<div class="cn-card">
<h2>148色のCSS名前付きカラー一覧</h2>
<div class="cn-search-row">
<div class="cn-field">
<label>検索</label>
<input type="text" id="cn-search" placeholder="例: blue, red..." oninput="cnApp.filterColors()">
</div>
</div>
<div class="cn-filter-btns" id="cn-family-filters" style="margin-bottom:12px;"></div>
<div class="cn-count" id="cn-count"></div>
<div class="cn-grid" id="cn-color-grid"></div>
</div>

<!-- Detail Modal -->
<div class="cn-modal-overlay" id="cn-modal">
<div class="cn-modal">
<button class="cn-modal-close" onclick="document.getElementById('cn-modal').classList.remove('open')">&times;</button>
<div class="cn-modal-swatch" id="cn-modal-swatch"></div>
<div class="cn-modal-name" id="cn-modal-name"></div>
<div class="cn-modal-vals" id="cn-modal-vals"></div>
<button class="cn-btn" style="margin-top:14px;width:100%;" onclick="cnApp.useModalColor()">この色を使う</button>
</div>
</div>

<div class="cn-freee-cta">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">デザイナーの会計管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、デザインツール・素材費の経費管理もクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function() {
var CSS_COLORS = [
{name:'aliceblue',hex:'#f0f8ff',family:'blues'},
{name:'antiquewhite',hex:'#faebd7',family:'whites'},
{name:'aqua',hex:'#00ffff',family:'blues'},
{name:'aquamarine',hex:'#7fffd4',family:'greens'},
{name:'azure',hex:'#f0ffff',family:'whites'},
{name:'beige',hex:'#f5f5dc',family:'whites'},
{name:'bisque',hex:'#ffe4c4',family:'oranges'},
{name:'black',hex:'#000000',family:'grays'},
{name:'blanchedalmond',hex:'#ffebcd',family:'whites'},
{name:'blue',hex:'#0000ff',family:'blues'},
{name:'blueviolet',hex:'#8a2be2',family:'purples'},
{name:'brown',hex:'#a52a2a',family:'reds'},
{name:'burlywood',hex:'#deb887',family:'oranges'},
{name:'cadetblue',hex:'#5f9ea0',family:'blues'},
{name:'chartreuse',hex:'#7fff00',family:'greens'},
{name:'chocolate',hex:'#d2691e',family:'oranges'},
{name:'coral',hex:'#ff7f50',family:'oranges'},
{name:'cornflowerblue',hex:'#6495ed',family:'blues'},
{name:'cornsilk',hex:'#fff8dc',family:'whites'},
{name:'crimson',hex:'#dc143c',family:'reds'},
{name:'cyan',hex:'#00ffff',family:'blues'},
{name:'darkblue',hex:'#00008b',family:'blues'},
{name:'darkcyan',hex:'#008b8b',family:'blues'},
{name:'darkgoldenrod',hex:'#b8860b',family:'yellows'},
{name:'darkgray',hex:'#a9a9a9',family:'grays'},
{name:'darkgreen',hex:'#006400',family:'greens'},
{name:'darkgrey',hex:'#a9a9a9',family:'grays'},
{name:'darkkhaki',hex:'#bdb76b',family:'yellows'},
{name:'darkmagenta',hex:'#8b008b',family:'purples'},
{name:'darkolivegreen',hex:'#556b2f',family:'greens'},
{name:'darkorange',hex:'#ff8c00',family:'oranges'},
{name:'darkorchid',hex:'#9932cc',family:'purples'},
{name:'darkred',hex:'#8b0000',family:'reds'},
{name:'darksalmon',hex:'#e9967a',family:'reds'},
{name:'darkseagreen',hex:'#8fbc8f',family:'greens'},
{name:'darkslateblue',hex:'#483d8b',family:'blues'},
{name:'darkslategray',hex:'#2f4f4f',family:'grays'},
{name:'darkslategrey',hex:'#2f4f4f',family:'grays'},
{name:'darkturquoise',hex:'#00ced1',family:'blues'},
{name:'darkviolet',hex:'#9400d3',family:'purples'},
{name:'deeppink',hex:'#ff1493',family:'pinks'},
{name:'deepskyblue',hex:'#00bfff',family:'blues'},
{name:'dimgray',hex:'#696969',family:'grays'},
{name:'dimgrey',hex:'#696969',family:'grays'},
{name:'dodgerblue',hex:'#1e90ff',family:'blues'},
{name:'firebrick',hex:'#b22222',family:'reds'},
{name:'floralwhite',hex:'#fffaf0',family:'whites'},
{name:'forestgreen',hex:'#228b22',family:'greens'},
{name:'fuchsia',hex:'#ff00ff',family:'pinks'},
{name:'gainsboro',hex:'#dcdcdc',family:'grays'},
{name:'ghostwhite',hex:'#f8f8ff',family:'whites'},
{name:'gold',hex:'#ffd700',family:'yellows'},
{name:'goldenrod',hex:'#daa520',family:'yellows'},
{name:'gray',hex:'#808080',family:'grays'},
{name:'green',hex:'#008000',family:'greens'},
{name:'greenyellow',hex:'#adff2f',family:'greens'},
{name:'grey',hex:'#808080',family:'grays'},
{name:'honeydew',hex:'#f0fff0',family:'whites'},
{name:'hotpink',hex:'#ff69b4',family:'pinks'},
{name:'indianred',hex:'#cd5c5c',family:'reds'},
{name:'indigo',hex:'#4b0082',family:'purples'},
{name:'ivory',hex:'#fffff0',family:'whites'},
{name:'khaki',hex:'#f0e68c',family:'yellows'},
{name:'lavender',hex:'#e6e6fa',family:'purples'},
{name:'lavenderblush',hex:'#fff0f5',family:'pinks'},
{name:'lawngreen',hex:'#7cfc00',family:'greens'},
{name:'lemonchiffon',hex:'#fffacd',family:'yellows'},
{name:'lightblue',hex:'#add8e6',family:'blues'},
{name:'lightcoral',hex:'#f08080',family:'reds'},
{name:'lightcyan',hex:'#e0ffff',family:'blues'},
{name:'lightgoldenrodyellow',hex:'#fafad2',family:'yellows'},
{name:'lightgray',hex:'#d3d3d3',family:'grays'},
{name:'lightgreen',hex:'#90ee90',family:'greens'},
{name:'lightgrey',hex:'#d3d3d3',family:'grays'},
{name:'lightpink',hex:'#ffb6c1',family:'pinks'},
{name:'lightsalmon',hex:'#ffa07a',family:'oranges'},
{name:'lightseagreen',hex:'#20b2aa',family:'greens'},
{name:'lightskyblue',hex:'#87cefa',family:'blues'},
{name:'lightslategray',hex:'#778899',family:'grays'},
{name:'lightslategrey',hex:'#778899',family:'grays'},
{name:'lightsteelblue',hex:'#b0c4de',family:'blues'},
{name:'lightyellow',hex:'#ffffe0',family:'yellows'},
{name:'lime',hex:'#00ff00',family:'greens'},
{name:'limegreen',hex:'#32cd32',family:'greens'},
{name:'linen',hex:'#faf0e6',family:'whites'},
{name:'magenta',hex:'#ff00ff',family:'pinks'},
{name:'maroon',hex:'#800000',family:'reds'},
{name:'mediumaquamarine',hex:'#66cdaa',family:'greens'},
{name:'mediumblue',hex:'#0000cd',family:'blues'},
{name:'mediumorchid',hex:'#ba55d3',family:'purples'},
{name:'mediumpurple',hex:'#9370db',family:'purples'},
{name:'mediumseagreen',hex:'#3cb371',family:'greens'},
{name:'mediumslateblue',hex:'#7b68ee',family:'blues'},
{name:'mediumspringgreen',hex:'#00fa9a',family:'greens'},
{name:'mediumturquoise',hex:'#48d1cc',family:'blues'},
{name:'mediumvioletred',hex:'#c71585',family:'pinks'},
{name:'midnightblue',hex:'#191970',family:'blues'},
{name:'mintcream',hex:'#f5fffa',family:'whites'},
{name:'mistyrose',hex:'#ffe4e1',family:'pinks'},
{name:'moccasin',hex:'#ffe4b5',family:'oranges'},
{name:'navajowhite',hex:'#ffdead',family:'oranges'},
{name:'navy',hex:'#000080',family:'blues'},
{name:'oldlace',hex:'#fdf5e6',family:'whites'},
{name:'olive',hex:'#808000',family:'yellows'},
{name:'olivedrab',hex:'#6b8e23',family:'greens'},
{name:'orange',hex:'#ffa500',family:'oranges'},
{name:'orangered',hex:'#ff4500',family:'reds'},
{name:'orchid',hex:'#da70d6',family:'purples'},
{name:'palegoldenrod',hex:'#eee8aa',family:'yellows'},
{name:'palegreen',hex:'#98fb98',family:'greens'},
{name:'paleturquoise',hex:'#afeeee',family:'blues'},
{name:'palevioletred',hex:'#db7093',family:'pinks'},
{name:'papayawhip',hex:'#ffefd5',family:'oranges'},
{name:'peachpuff',hex:'#ffdab9',family:'oranges'},
{name:'peru',hex:'#cd853f',family:'oranges'},
{name:'pink',hex:'#ffc0cb',family:'pinks'},
{name:'plum',hex:'#dda0dd',family:'purples'},
{name:'powderblue',hex:'#b0e0e6',family:'blues'},
{name:'purple',hex:'#800080',family:'purples'},
{name:'rebeccapurple',hex:'#663399',family:'purples'},
{name:'red',hex:'#ff0000',family:'reds'},
{name:'rosybrown',hex:'#bc8f8f',family:'reds'},
{name:'royalblue',hex:'#4169e1',family:'blues'},
{name:'saddlebrown',hex:'#8b4513',family:'oranges'},
{name:'salmon',hex:'#fa8072',family:'reds'},
{name:'sandybrown',hex:'#f4a460',family:'oranges'},
{name:'seagreen',hex:'#2e8b57',family:'greens'},
{name:'seashell',hex:'#fff5ee',family:'whites'},
{name:'sienna',hex:'#a0522d',family:'oranges'},
{name:'silver',hex:'#c0c0c0',family:'grays'},
{name:'skyblue',hex:'#87ceeb',family:'blues'},
{name:'slateblue',hex:'#6a5acd',family:'blues'},
{name:'slategray',hex:'#708090',family:'grays'},
{name:'slategrey',hex:'#708090',family:'grays'},
{name:'snow',hex:'#fffafa',family:'whites'},
{name:'springgreen',hex:'#00ff7f',family:'greens'},
{name:'steelblue',hex:'#4682b4',family:'blues'},
{name:'tan',hex:'#d2b48c',family:'oranges'},
{name:'teal',hex:'#008080',family:'blues'},
{name:'thistle',hex:'#d8bfd8',family:'purples'},
{name:'tomato',hex:'#ff6347',family:'reds'},
{name:'turquoise',hex:'#40e0d0',family:'blues'},
{name:'violet',hex:'#ee82ee',family:'purples'},
{name:'wheat',hex:'#f5deb3',family:'oranges'},
{name:'white',hex:'#ffffff',family:'whites'},
{name:'whitesmoke',hex:'#f5f5f5',family:'whites'},
{name:'yellow',hex:'#ffff00',family:'yellows'},
{name:'yellowgreen',hex:'#9acd32',family:'greens'}
];

var FAMILIES = [
{key:'all',label:'すべて'},
{key:'reds',label:'赤系'},
{key:'oranges',label:'橙系'},
{key:'yellows',label:'黄系'},
{key:'greens',label:'緑系'},
{key:'blues',label:'青系'},
{key:'purples',label:'紫系'},
{key:'pinks',label:'ピンク系'},
{key:'grays',label:'グレー系'},
{key:'whites',label:'白系'}
];
var currentFamily = 'all';
var modalColor = null;

function hexToRgb(hex) {
var r = parseInt(hex.slice(1,3),16);
var g = parseInt(hex.slice(3,5),16);
var b = parseInt(hex.slice(5,7),16);
return {r:r,g:g,b:b};
}

function rgbToHex(r,g,b) {
return '#' + [r,g,b].map(function(v){ return ('0'+Math.round(v).toString(16)).slice(-2); }).join('');
}

function rgbToHsl(r,g,b) {
r/=255; g/=255; b/=255;
var max=Math.max(r,g,b), min=Math.min(r,g,b), h, s, l=(max+min)/2;
if(max===min){ h=s=0; }
else {
var d=max-min;
s = l>0.5 ? d/(2-max-min) : d/(max+min);
switch(max){
case r: h=(g-b)/d+(g<b?6:0); break;
case g: h=(b-r)/d+2; break;
case b: h=(r-g)/d+4; break;
}
h/=6;
}
return {h:Math.round(h*360), s:Math.round(s*100), l:Math.round(l*100)};
}

function colorDist(r1,g1,b1,r2,g2,b2) {
return Math.sqrt((r1-r2)*(r1-r2)+(g1-g2)*(g1-g2)+(b1-b2)*(b1-b2));
}

function findClosest(r,g,b) {
var best = null, bestDist = Infinity;
CSS_COLORS.forEach(function(c){
var rgb = hexToRgb(c.hex);
var d = colorDist(r,g,b,rgb.r,rgb.g,rgb.b);
if(d < bestDist){ bestDist=d; best=c; }
});
return {color:best, distance:bestDist};
}

function showResult(inputHex, inputR, inputG, inputB) {
var match = findClosest(inputR, inputG, inputB);
var matchRgb = hexToRgb(match.color.hex);
var matchHsl = rgbToHsl(matchRgb.r, matchRgb.g, matchRgb.b);
var inputHsl = rgbToHsl(inputR, inputG, inputB);

document.getElementById('cn-result-card').style.display = '';
document.getElementById('cn-input-swatch').style.background = inputHex;
document.getElementById('cn-match-swatch').style.background = match.color.hex;
document.getElementById('cn-match-name').textContent = match.color.name;

var inVals = [
{label:'HEX', val:inputHex},
{label:'RGB', val:'rgb('+inputR+', '+inputG+', '+inputB+')'},
{label:'HSL', val:'hsl('+inputHsl.h+', '+inputHsl.s+'%, '+inputHsl.l+'%)'}
];
var matchVals = [
{label:'HEX', val:match.color.hex},
{label:'RGB', val:'rgb('+matchRgb.r+', '+matchRgb.g+', '+matchRgb.b+')'},
{label:'HSL', val:'hsl('+matchHsl.h+', '+matchHsl.s+'%, '+matchHsl.l+'%)'}
];

function makeRows(vals) {
return vals.map(function(item){
return '<div class="cn-val-row"><span class="cn-val-label">'+item.label+'</span><span class="cn-val-text">'+item.val+'</span><button class="cn-copy-icon" onclick="navigator.clipboard.writeText(this.previousElementSibling.textContent)">コピー</button></div>';
}).join('');
}

document.getElementById('cn-input-vals').innerHTML = makeRows(inVals);
document.getElementById('cn-match-vals').innerHTML = makeRows(matchVals);

var pct = Math.round((1 - match.distance/441.67)*100);
document.getElementById('cn-distance-info').innerHTML =
'色の距離: <span>'+match.distance.toFixed(1)+'</span>（RGB空間ユークリッド距離）— 一致度: <span>'+Math.max(0,pct)+'%</span>';

document.getElementById('cn-result-card').scrollIntoView({behavior:'smooth',block:'nearest'});
}

function parseHexInput(val) {
val = val.trim();
if(!val.startsWith('#')) val = '#'+val;
if(/^#[0-9a-fA-F]{3}$/.test(val)) {
val = '#'+val[1]+val[1]+val[2]+val[2]+val[3]+val[3];
}
return /^#[0-9a-fA-F]{6}$/.test(val) ? val : null;
}

function buildGrid(list) {
var grid = document.getElementById('cn-color-grid');
grid.innerHTML = '';
list.forEach(function(c) {
var card = document.createElement('div');
card.className = 'cn-color-card';
card.innerHTML = '<div class="cn-color-card-swatch" style="background:'+c.hex+'"></div><div class="cn-color-card-name">'+c.name+'</div>';
card.onclick = function() {
document.querySelectorAll('#cn-app .cn-color-card').forEach(function(el){ el.classList.remove('selected'); });
card.classList.add('selected');
showModal(c);
};
grid.appendChild(card);
});
document.getElementById('cn-count').textContent = list.length + '色を表示中';
}

function showModal(c) {
modalColor = c;
var rgb = hexToRgb(c.hex);
var hsl = rgbToHsl(rgb.r,rgb.g,rgb.b);
document.getElementById('cn-modal-swatch').style.background = c.hex;
document.getElementById('cn-modal-name').textContent = c.name;
var vals = [
{label:'HEX', val:c.hex},
{label:'RGB', val:'rgb('+rgb.r+', '+rgb.g+', '+rgb.b+')'},
{label:'HSL', val:'hsl('+hsl.h+', '+hsl.s+'%, '+hsl.l+'%)'}
];
document.getElementById('cn-modal-vals').innerHTML = vals.map(function(item){
return '<div class="cn-modal-val-row"><span class="cn-modal-val-label">'+item.label+'</span><span class="cn-modal-val-text">'+item.val+'</span><button class="cn-modal-copy" onclick="navigator.clipboard.writeText(this.previousElementSibling.textContent)">コピー</button></div>';
}).join('');
document.getElementById('cn-modal').classList.add('open');
}

function filterColors() {
var q = document.getElementById('cn-search').value.toLowerCase();
var list = CSS_COLORS.filter(function(c){
var fam = currentFamily === 'all' || c.family === currentFamily;
var name = !q || c.name.includes(q) || c.hex.includes(q);
return fam && name;
});
buildGrid(list);
}

function buildFamilyFilters() {
var container = document.getElementById('cn-family-filters');
FAMILIES.forEach(function(f){
var btn = document.createElement('button');
btn.className = 'cn-filter-btn' + (f.key==='all'?' active':'');
btn.textContent = f.label;
btn.onclick = function(){
document.querySelectorAll('#cn-app .cn-filter-btn').forEach(function(b){ b.classList.remove('active'); });
btn.classList.add('active');
currentFamily = f.key;
filterColors();
};
container.appendChild(btn);
});
}

window.cnApp = {
findFromHex: function() {
var val = parseHexInput(document.getElementById('cn-hex-input').value);
if(!val) { alert('有効なHEXカラーを入力してください（例: #ff6347）'); return; }
var rgb = hexToRgb(val);
showResult(val, rgb.r, rgb.g, rgb.b);
},
findFromRgb: function() {
var r = parseInt(document.getElementById('cn-r-num').value)||0;
var g = parseInt(document.getElementById('cn-g-num').value)||0;
var b = parseInt(document.getElementById('cn-b-num').value)||0;
r=Math.min(255,Math.max(0,r));
g=Math.min(255,Math.max(0,g));
b=Math.min(255,Math.max(0,b));
showResult(rgbToHex(r,g,b), r, g, b);
},
findFromPicker: function() {
var val = document.getElementById('cn-color-picker').value;
var rgb = hexToRgb(val);
showResult(val, rgb.r, rgb.g, rgb.b);
},
updateRgbFromSliders: function() {
document.getElementById('cn-r-num').value = document.getElementById('cn-r-slider').value;
document.getElementById('cn-g-num').value = document.getElementById('cn-g-slider').value;
document.getElementById('cn-b-num').value = document.getElementById('cn-b-slider').value;
},
updateSlidersFromNum: function() {
document.getElementById('cn-r-slider').value = document.getElementById('cn-r-num').value;
document.getElementById('cn-g-slider').value = document.getElementById('cn-g-num').value;
document.getElementById('cn-b-slider').value = document.getElementById('cn-b-num').value;
},
filterColors: filterColors,
useModalColor: function() {
if(!modalColor) return;
var rgb = hexToRgb(modalColor.hex);
document.getElementById('cn-modal').classList.remove('open');
showResult(modalColor.hex, rgb.r, rgb.g, rgb.b);
}
};

// Init
buildFamilyFilters();
buildGrid(CSS_COLORS);

document.getElementById('cn-hex-input').addEventListener('keydown', function(e){
if(e.key==='Enter') cnApp.findFromHex();
});

document.getElementById('cn-modal').addEventListener('click', function(e){
if(e.target===this) this.classList.remove('open');
});
})();
</script>

---

**関連ツール:**

- 色を選ぶ → [カラーピッカー](/ja/tools/color-picker/)
- コントラスト確認 → [カラーコントラストチェッカー](/ja/tools/color-contrast-checker/)
- パレット生成 → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
