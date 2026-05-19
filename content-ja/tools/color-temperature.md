---
title: "色温度変換ツール"
date: 2025-08-10
description: "色温度（ケルビン）からRGB・HEX値に変換。スライダーで暖色〜寒色を可視化。無料・登録不要。"
categories: ["無料ツール"]
slug: "color-temperature"
ShowToc: false
cover:
  image: "/images/covers/color-temperature-ja.png"
  alt: "色温度変換ツール"
---

**ケルビン（K）の色温度**をリアルタイムで **RGB・HEX・HSL** に変換。スライダーを動かすと暖色系から寒色系まで光の色を即座にプレビューできます。ワンクリックでカラー値をコピー可能。

<div id="ct-app">
<style>
#ct-app *, #ct-app *::before, #ct-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#ct-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f7f8fc;
border-radius: 12px;
padding: 24px;
max-width: 740px;
margin: 0 auto;
}
#ct-app h2 {
font-size: 1.1rem;
font-weight: 700;
margin-bottom: 14px;
color: #12122a;
}
#ct-app .ct-preview-block {
display: flex;
gap: 18px;
align-items: stretch;
margin-bottom: 22px;
flex-wrap: wrap;
}
#ct-app .ct-swatch {
width: 130px;
min-height: 130px;
border-radius: 12px;
border: 2px solid rgba(0,0,0,0.10);
flex-shrink: 0;
transition: background 0.15s;
}
#ct-app .ct-values {
flex: 1;
min-width: 200px;
display: flex;
flex-direction: column;
gap: 10px;
justify-content: center;
}
#ct-app .ct-value-row {
display: flex;
align-items: center;
gap: 8px;
}
#ct-app .ct-label {
font-size: 12px;
font-weight: 700;
color: #6b7280;
width: 34px;
flex-shrink: 0;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#ct-app .ct-value-box {
flex: 1;
background: #fff;
border: 1.5px solid #e5e7eb;
border-radius: 7px;
padding: 7px 10px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 14px;
color: #111827;
min-width: 0;
}
#ct-app .ct-copy-btn {
background: #6366f1;
color: #fff;
border: none;
border-radius: 7px;
padding: 7px 13px;
font-size: 12px;
font-weight: 700;
cursor: pointer;
white-space: nowrap;
transition: background 0.15s, transform 0.1s;
}
#ct-app .ct-copy-btn:hover { background: #4f46e5; }
#ct-app .ct-copy-btn:active { transform: scale(0.96); }
#ct-app .ct-copy-btn.copied { background: #22c55e; }
#ct-app .ct-kelvin-display {
text-align: center;
font-size: 2rem;
font-weight: 800;
color: #12122a;
margin-bottom: 6px;
letter-spacing: -0.02em;
}
#ct-app .ct-kelvin-display span {
font-size: 1rem;
font-weight: 500;
color: #6b7280;
margin-left: 4px;
}
#ct-app .ct-preset-name {
text-align: center;
font-size: 13px;
color: #6366f1;
font-weight: 600;
margin-bottom: 14px;
min-height: 20px;
}
#ct-app .ct-slider-wrap {
margin-bottom: 6px;
position: relative;
}
#ct-app .ct-slider {
-webkit-appearance: none;
appearance: none;
width: 100%;
height: 18px;
border-radius: 9px;
outline: none;
cursor: pointer;
background: linear-gradient(
to right,
#ff4500 0%,
#ff6a00 5%,
#ff8c00 10%,
#ffa500 15%,
#ffbf00 20%,
#ffd27f 28%,
#ffecb3 35%,
#fff4e0 42%,
#fff9f0 48%,
#ffffff 53%,
#f0f4ff 58%,
#d6e4ff 65%,
#bad4f5 72%,
#9ec5fa 80%,
#74b9ff 90%,
#4fc3f7 100%
);
border: 1.5px solid rgba(0,0,0,0.10);
}
#ct-app .ct-slider::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 26px;
height: 26px;
border-radius: 50%;
background: #fff;
border: 3px solid #6366f1;
box-shadow: 0 2px 8px rgba(99,102,241,0.3);
cursor: pointer;
transition: border-color 0.15s;
}
#ct-app .ct-slider::-moz-range-thumb {
width: 26px;
height: 26px;
border-radius: 50%;
background: #fff;
border: 3px solid #6366f1;
box-shadow: 0 2px 8px rgba(99,102,241,0.3);
cursor: pointer;
}
#ct-app .ct-scale-labels {
display: flex;
justify-content: space-between;
font-size: 11px;
color: #9ca3af;
margin-top: 4px;
margin-bottom: 20px;
}
#ct-app .ct-gradient-bar {
width: 100%;
height: 28px;
border-radius: 8px;
margin-bottom: 8px;
background: linear-gradient(
to right,
#ff4500 0%,
#ff6a00 5%,
#ff8c00 10%,
#ffa500 15%,
#ffbf00 20%,
#ffd27f 28%,
#ffecb3 35%,
#fff4e0 42%,
#fff9f0 48%,
#ffffff 53%,
#f0f4ff 58%,
#d6e4ff 65%,
#bad4f5 72%,
#9ec5fa 80%,
#74b9ff 90%,
#4fc3f7 100%
);
border: 1.5px solid rgba(0,0,0,0.08);
}
#ct-app .ct-gradient-label {
display: flex;
justify-content: space-between;
font-size: 11px;
color: #9ca3af;
margin-bottom: 22px;
}
#ct-app .ct-presets {
margin-bottom: 22px;
}
#ct-app .ct-presets h2 {
margin-bottom: 10px;
}
#ct-app .ct-preset-grid {
display: flex;
flex-wrap: wrap;
gap: 8px;
}
#ct-app .ct-preset-btn {
display: flex;
align-items: center;
gap: 8px;
padding: 7px 12px;
border-radius: 8px;
border: 1.5px solid #e5e7eb;
background: #fff;
cursor: pointer;
font-size: 13px;
color: #374151;
transition: border-color 0.15s, box-shadow 0.15s;
font-weight: 500;
}
#ct-app .ct-preset-btn:hover {
border-color: #6366f1;
box-shadow: 0 0 0 2px rgba(99,102,241,0.12);
}
#ct-app .ct-preset-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}
#ct-app .ct-preset-dot {
width: 16px;
height: 16px;
border-radius: 50%;
border: 1.5px solid rgba(0,0,0,0.12);
flex-shrink: 0;
}
#ct-app .ct-info-section {
background: #fff;
border-radius: 10px;
border: 1.5px solid #e5e7eb;
padding: 18px 20px;
margin-top: 4px;
}
#ct-app .ct-info-section h2 {
font-size: 1rem;
margin-bottom: 10px;
}
#ct-app .ct-info-section p {
font-size: 14px;
color: #374151;
line-height: 1.7;
margin-bottom: 8px;
}
#ct-app .ct-info-section p:last-child { margin-bottom: 0; }
#ct-app .ct-copy-all-btn {
display: inline-block;
margin-top: 4px;
padding: 9px 20px;
background: #6366f1;
color: #fff;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
#ct-app .ct-copy-all-btn:hover { background: #4f46e5; }
#ct-app .ct-copy-all-btn:active { transform: scale(0.97); }
#ct-app .ct-copy-all-btn.copied { background: #22c55e; }
@media (max-width: 480px) {
#ct-app { padding: 16px; }
#ct-app .ct-swatch { width: 100%; min-height: 80px; }
#ct-app .ct-kelvin-display { font-size: 1.6rem; }
}
</style>

<div class="ct-kelvin-display" id="ct-kelvin-num">5500<span>K</span></div>
<div class="ct-preset-name" id="ct-preset-name">昼光</div>

<div class="ct-slider-wrap">
<input type="range" class="ct-slider" id="ct-slider" min="1000" max="12000" step="100" value="5500">
</div>
<div class="ct-scale-labels">
<span>1000K</span>
<span>暖色</span>
<span>中間</span>
<span>寒色</span>
<span>12000K</span>
</div>

<div class="ct-gradient-bar"></div>
<div class="ct-gradient-label">
<span>暖色（赤・オレンジ系）</span>
<span>中間白色</span>
<span>寒色（青系）</span>
</div>

<div class="ct-preview-block">
<div class="ct-swatch" id="ct-swatch"></div>
<div class="ct-values">
<div class="ct-value-row">
<span class="ct-label">HEX</span>
<span class="ct-value-box" id="ct-hex">#fff4e0</span>
<button class="ct-copy-btn" onclick="ctCopy('ct-hex',this)">コピー</button>
</div>
<div class="ct-value-row">
<span class="ct-label">RGB</span>
<span class="ct-value-box" id="ct-rgb">rgb(255, 244, 224)</span>
<button class="ct-copy-btn" onclick="ctCopy('ct-rgb',this)">コピー</button>
</div>
<div class="ct-value-row">
<span class="ct-label">HSL</span>
<span class="ct-value-box" id="ct-hsl">hsl(38, 100%, 94%)</span>
<button class="ct-copy-btn" onclick="ctCopy('ct-hsl',this)">コピー</button>
</div>
<div style="margin-top:4px;">
<button class="ct-copy-all-btn" id="ct-copy-all-btn" onclick="ctCopyAll()">すべてコピー</button>
</div>
</div>
</div>

<div class="ct-presets">
<h2>代表的な光源プリセット</h2>
<div class="ct-preset-grid" id="ct-preset-grid">
<button class="ct-preset-btn" data-k="1900" onclick="ctSetPreset(1900,this)">
<span class="ct-preset-dot" id="ct-dot-1900"></span>ろうそく（1900K）
</button>
<button class="ct-preset-btn" data-k="2700" onclick="ctSetPreset(2700,this)">
<span class="ct-preset-dot" id="ct-dot-2700"></span>白熱球（2700K）
</button>
<button class="ct-preset-btn" data-k="3200" onclick="ctSetPreset(3200,this)">
<span class="ct-preset-dot" id="ct-dot-3200"></span>ハロゲン（3200K）
</button>
<button class="ct-preset-btn" data-k="4000" onclick="ctSetPreset(4000,this)">
<span class="ct-preset-dot" id="ct-dot-4000"></span>蛍光灯（4000K）
</button>
<button class="ct-preset-btn" data-k="5500" onclick="ctSetPreset(5500,this)">
<span class="ct-preset-dot" id="ct-dot-5500"></span>昼光（5500K）
</button>
<button class="ct-preset-btn" data-k="6500" onclick="ctSetPreset(6500,this)">
<span class="ct-preset-dot" id="ct-dot-6500"></span>曇天（6500K）
</button>
<button class="ct-preset-btn" data-k="7500" onclick="ctSetPreset(7500,this)">
<span class="ct-preset-dot" id="ct-dot-7500"></span>日陰（7500K）
</button>
<button class="ct-preset-btn" data-k="10000" onclick="ctSetPreset(10000,this)">
<span class="ct-preset-dot" id="ct-dot-10000"></span>青空（10000K）
</button>
</div>
</div>

<div class="ct-info-section">
<h2>暖色光と寒色光について</h2>
<p><strong>暖色光（1000〜3500K）</strong>は赤みがかったオレンジ色の光で、ろうそくや白熱電球が代表例です。リラックスできる雰囲気を作り出し、寝室やレストランでよく使われます。</p>
<p><strong>中間白色光（3500〜5000K）</strong>は白っぽく見え、朝の自然光に近い色温度です。明るさと快適さのバランスが良く、オフィスやキッチンに向いています。</p>
<p><strong>寒色光（5000〜12000K）</strong>は青白い光で、曇り空や日陰の光に相当します。カメラのホワイトバランス設定でよく使われ、一般的なPCモニターは約6500Kに設定されています。</p>
<p>ケルビン値が高いほど「冷たく」見える青みがかった光になります。これは直感に反しますが、加熱された物体が放つ色の物理的な性質によるものです。</p>
</div>

<div class="ct-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

<script>
(function(){
// Tanner Helland's algorithm for Kelvin → RGB
function kelvinToRgb(kelvin) {
var temp = kelvin / 100;
var r, g, b;

// Red
if (temp <= 66) {
r = 255;
} else {
r = temp - 60;
r = 329.698727446 * Math.pow(r, -0.1332047592);
r = Math.max(0, Math.min(255, r));
}

// Green
if (temp <= 66) {
g = temp;
g = 99.4708025861 * Math.log(g) - 161.1195681661;
g = Math.max(0, Math.min(255, g));
} else {
g = temp - 60;
g = 288.1221695283 * Math.pow(g, -0.0755148492);
g = Math.max(0, Math.min(255, g));
}

// Blue
if (temp >= 66) {
b = 255;
} else if (temp <= 19) {
b = 0;
} else {
b = temp - 10;
b = 138.5177312231 * Math.log(b) - 305.0447927307;
b = Math.max(0, Math.min(255, b));
}

return [Math.round(r), Math.round(g), Math.round(b)];
}

function rgbToHex(r, g, b) {
return '#' + [r, g, b].map(function(v){
return v.toString(16).padStart(2,'0');
}).join('');
}

function rgbToHsl(r, g, b) {
r /= 255; g /= 255; b /= 255;
var max = Math.max(r, g, b), min = Math.min(r, g, b);
var h, s, l = (max + min) / 2;
if (max === min) {
h = s = 0;
} else {
var d = max - min;
s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
switch(max) {
case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
case g: h = ((b - r) / d + 2) / 6; break;
case b: h = ((r - g) / d + 4) / 6; break;
}
}
return [Math.round(h * 360), Math.round(s * 100), Math.round(l * 100)];
}

var PRESETS = {
1900: 'ろうそく',
2700: '白熱球',
3200: 'ハロゲン',
4000: '蛍光灯',
5500: '昼光',
6500: '曇天',
7500: '日陰',
10000: '青空'
};

// Pre-color preset dots
Object.keys(PRESETS).forEach(function(k){
var dot = document.getElementById('ct-dot-' + k);
if (dot) {
var rgb = kelvinToRgb(parseInt(k));
dot.style.background = 'rgb(' + rgb[0] + ',' + rgb[1] + ',' + rgb[2] + ')';
}
});

function update(kelvin) {
var rgb = kelvinToRgb(kelvin);
var r = rgb[0], g = rgb[1], b = rgb[2];
var hex = rgbToHex(r, g, b);
var hsl = rgbToHsl(r, g, b);

document.getElementById('ct-swatch').style.background = 'rgb(' + r + ',' + g + ',' + b + ')';
document.getElementById('ct-hex').textContent = hex;
document.getElementById('ct-rgb').textContent = 'rgb(' + r + ', ' + g + ', ' + b + ')';
document.getElementById('ct-hsl').textContent = 'hsl(' + hsl[0] + ', ' + hsl[1] + '%, ' + hsl[2] + '%)';
document.getElementById('ct-kelvin-num').innerHTML = kelvin + '<span>K</span>';

// Preset name
var pname = PRESETS[kelvin] || '';
document.getElementById('ct-preset-name').textContent = pname ? pname : '';

// Highlight active preset button
var btns = document.querySelectorAll('#ct-preset-grid .ct-preset-btn');
btns.forEach(function(btn){
btn.classList.toggle('active', parseInt(btn.dataset.k) === kelvin);
});
}

var slider = document.getElementById('ct-slider');
slider.addEventListener('input', function(){
update(parseInt(this.value));
});

window.ctSetPreset = function(k, btn) {
slider.value = k;
update(k);
};

window.ctCopy = function(id, btn) {
var text = document.getElementById(id).textContent;
navigator.clipboard.writeText(text).then(function(){
btn.textContent = 'コピー済！';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1500);
});
};

window.ctCopyAll = function() {
var hex = document.getElementById('ct-hex').textContent;
var rgb = document.getElementById('ct-rgb').textContent;
var hsl = document.getElementById('ct-hsl').textContent;
var kelvin = document.getElementById('ct-slider').value + 'K';
var text = kelvin + '\n' + hex + '\n' + rgb + '\n' + hsl;
navigator.clipboard.writeText(text).then(function(){
var btn = document.getElementById('ct-copy-all-btn');
btn.textContent = 'コピー済！';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = 'すべてコピー'; btn.classList.remove('copied'); }, 1500);
});
};

// Init
update(5500);
})();
</script>

</div>

---

**関連ツール**

> カラーネーム検索 → [カラーネームファインダー](/ja/tools/color-name-finder/)

> 色を混ぜる → [カラーミキサー](/ja/tools/color-mixer/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
