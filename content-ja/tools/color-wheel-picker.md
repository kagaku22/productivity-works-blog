---
title: "カラーホイールピッカー"
date: 2025-11-11
description: "無料のカラーホイールピッカー。補色・類似色・トライアド・分裂補色など配色パターンをリアルタイムプレビュー。CSS書き出し対応、会員登録不要。"
categories: ["無料ツール"]
tags: ["CSS", "Webデザイン", "無料ツール"]
slug: "color-wheel-picker"
ShowToc: false
cover:
  image: "/images/covers/color-wheel-picker-ja.png"
  alt: "カラーホイールピッカー"
---

<div id="cw-app">

<style>
#cw-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", sans-serif;
color: #1e293b;
max-width: 760px;
margin: 0 auto;
padding: 0 8px;
box-sizing: border-box;
}
#cw-app * {
box-sizing: border-box;
}
#cw-app h2 {
font-size: 18px;
font-weight: 700;
color: #0f172a;
margin: 24px 0 10px;
padding-bottom: 6px;
border-bottom: 2px solid #e2e8f0;
}
#cw-app .cw-layout {
display: flex;
flex-wrap: wrap;
gap: 24px;
align-items: flex-start;
margin-top: 16px;
}
#cw-app .cw-canvas-col {
display: flex;
flex-direction: column;
align-items: center;
gap: 14px;
flex: 0 0 auto;
}
#cw-app .cw-controls-col {
flex: 1 1 260px;
display: flex;
flex-direction: column;
gap: 14px;
}
#cw-app canvas#cw-wheel {
border-radius: 50%;
cursor: crosshair;
display: block;
touch-action: none;
box-shadow: 0 2px 12px rgba(0,0,0,0.13);
border: 3px solid #e2e8f0;
}
#cw-app .cw-mode-label {
font-size: 13px;
font-weight: 600;
color: #475569;
margin-bottom: 4px;
}
#cw-app .cw-mode-btns {
display: flex;
flex-wrap: wrap;
gap: 7px;
}
#cw-app .cw-mode-btn {
padding: 6px 13px;
border-radius: 20px;
border: 1.5px solid #cbd5e1;
background: #f8fafc;
color: #334155;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
outline: none;
}
#cw-app .cw-mode-btn:hover {
background: #e0f2fe;
border-color: #38bdf8;
color: #0369a1;
}
#cw-app .cw-mode-btn.active {
background: #0284c7;
border-color: #0284c7;
color: #fff;
}
#cw-app .cw-swatches {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 2px;
}
#cw-app .cw-swatch-item {
display: flex;
flex-direction: column;
align-items: center;
gap: 5px;
cursor: pointer;
}
#cw-app .cw-swatch-box {
width: 54px;
height: 54px;
border-radius: 8px;
border: 2px solid #e2e8f0;
transition: transform 0.1s, box-shadow 0.1s;
position: relative;
}
#cw-app .cw-swatch-box:hover {
transform: scale(1.08);
box-shadow: 0 2px 8px rgba(0,0,0,0.18);
}
#cw-app .cw-swatch-label {
font-size: 11px;
color: #64748b;
text-align: center;
max-width: 60px;
word-break: break-all;
}
#cw-app .cw-copied-toast {
position: fixed;
bottom: 28px;
left: 50%;
transform: translateX(-50%);
background: #0f172a;
color: #fff;
padding: 9px 22px;
border-radius: 8px;
font-size: 14px;
font-weight: 600;
opacity: 0;
pointer-events: none;
transition: opacity 0.3s;
z-index: 9999;
}
#cw-app .cw-copied-toast.show {
opacity: 1;
}
#cw-app .cw-color-detail {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
display: flex;
flex-direction: column;
gap: 7px;
}
#cw-app .cw-color-detail-row {
display: flex;
align-items: center;
gap: 10px;
}
#cw-app .cw-detail-swatch {
width: 36px;
height: 36px;
border-radius: 6px;
border: 1.5px solid #e2e8f0;
flex: 0 0 auto;
}
#cw-app .cw-detail-values {
display: flex;
flex-direction: column;
gap: 2px;
}
#cw-app .cw-detail-val {
font-size: 12px;
color: #334155;
font-family: "SFMono-Regular", Consolas, monospace;
cursor: pointer;
padding: 2px 6px;
border-radius: 4px;
transition: background 0.12s;
user-select: all;
}
#cw-app .cw-detail-val:hover {
background: #e0f2fe;
color: #0369a1;
}
#cw-app .cw-css-box {
background: #0f172a;
border-radius: 10px;
padding: 14px 16px;
position: relative;
}
#cw-app .cw-css-pre {
color: #7dd3fc;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
line-height: 1.7;
margin: 0;
white-space: pre-wrap;
word-break: break-all;
}
#cw-app .cw-css-copy-btn {
position: absolute;
top: 10px;
right: 12px;
background: #1e40af;
color: #fff;
border: none;
border-radius: 5px;
padding: 4px 11px;
font-size: 12px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
}
#cw-app .cw-css-copy-btn:hover {
background: #2563eb;
}
#cw-app .cw-contrast-box {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
display: flex;
flex-direction: column;
gap: 8px;
}
#cw-app .cw-contrast-row {
display: flex;
align-items: center;
gap: 10px;
flex-wrap: wrap;
}
#cw-app .cw-contrast-preview {
padding: 7px 14px;
border-radius: 6px;
font-size: 14px;
font-weight: 700;
flex: 1 1 auto;
text-align: center;
min-width: 100px;
}
#cw-app .cw-contrast-info {
font-size: 13px;
color: #334155;
flex: 0 0 auto;
}
#cw-app .cw-wcag-badge {
display: inline-block;
padding: 2px 9px;
border-radius: 12px;
font-size: 12px;
font-weight: 700;
margin-left: 6px;
}
#cw-app .cw-wcag-pass {
background: #dcfce7;
color: #15803d;
}
#cw-app .cw-wcag-fail {
background: #fee2e2;
color: #b91c1c;
}
#cw-app .cw-crosslinks {
margin-top: 20px;
padding: 14px 18px;
background: #f1f5f9;
border-radius: 10px;
font-size: 14px;
line-height: 2;
color: #334155;
}
#cw-app .cw-crosslinks a {
color: #0284c7;
text-decoration: none;
font-weight: 600;
}
#cw-app .cw-crosslinks a:hover {
text-decoration: underline;
}
#cw-app .cw-section-title {
font-size: 13px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 4px;
}
#cw-app .cw-lightness-row {
display: flex;
align-items: center;
gap: 10px;
margin-top: 4px;
}
#cw-app .cw-lightness-row label {
font-size: 13px;
color: #475569;
font-weight: 600;
flex: 0 0 auto;
}
#cw-app input[type=range]#cw-lightness {
flex: 1;
accent-color: #0284c7;
height: 6px;
cursor: pointer;
}
#cw-app .cw-lightness-val {
font-size: 13px;
color: #334155;
font-family: monospace;
min-width: 36px;
text-align: right;
}
@media (max-width: 540px) {
#cw-app .cw-layout {
flex-direction: column;
align-items: center;
}
#cw-app .cw-controls-col {
width: 100%;
}
#cw-app canvas#cw-wheel {
width: 240px !important;
height: 240px !important;
}
}
</style>

<div class="cw-copied-toast" id="cw-toast">コピーしました</div>

<div class="cw-layout">
<div class="cw-canvas-col">
<canvas id="cw-wheel" width="300" height="300"></canvas>
<div class="cw-lightness-row">
<label for="cw-lightness">明度</label>
<input type="range" id="cw-lightness" min="20" max="80" value="50">
<span class="cw-lightness-val" id="cw-lightness-val">50%</span>
</div>
</div>
<div class="cw-controls-col">
<div>
<div class="cw-mode-label">配色モード</div>
<div class="cw-mode-btns">
<button class="cw-mode-btn active" data-mode="complementary">補色</button>
<button class="cw-mode-btn" data-mode="analogous">類似色</button>
<button class="cw-mode-btn" data-mode="triadic">トライアド</button>
<button class="cw-mode-btn" data-mode="split">分裂補色</button>
<button class="cw-mode-btn" data-mode="tetradic">テトラード</button>
</div>
</div>

<div>
<div class="cw-section-title">選択色・配色スウォッチ</div>
<div class="cw-swatches" id="cw-swatches"></div>
</div>

<div class="cw-color-detail" id="cw-color-detail">
<div class="cw-section-title">選択色の値（クリックでコピー）</div>
<div class="cw-color-detail-row">
<div class="cw-detail-swatch" id="cw-detail-swatch"></div>
<div class="cw-detail-values">
<span class="cw-detail-val" id="cw-val-hex" title="HEXをコピー"></span>
<span class="cw-detail-val" id="cw-val-rgb" title="RGBをコピー"></span>
<span class="cw-detail-val" id="cw-val-hsl" title="HSLをコピー"></span>
</div>
</div>
</div>

<div>
<div class="cw-section-title">WCAGコントラスト比（白・黒背景）</div>
<div class="cw-contrast-box" id="cw-contrast-box">
<div class="cw-contrast-row">
<div class="cw-contrast-preview" id="cw-prev-white">白背景サンプル</div>
<div class="cw-contrast-info" id="cw-cr-white"></div>
</div>
<div class="cw-contrast-row">
<div class="cw-contrast-preview" id="cw-prev-black">黒背景サンプル</div>
<div class="cw-contrast-info" id="cw-cr-black"></div>
</div>
</div>
</div>
</div>
</div>

<h2>CSSカスタムプロパティ書き出し</h2>
<div class="cw-css-box">
<pre class="cw-css-pre" id="cw-css-output"></pre>
<button class="cw-css-copy-btn" id="cw-css-copy-btn">コピー</button>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<div class="cw-crosslinks">
カラーパレットを生成 → <a href="/ja/tools/color-palette-generator/">カラーパレットジェネレーター</a><br>
コントラスト比を確認 → <a href="/ja/tools/color-contrast-checker/">カラーコントラストチェッカー</a><br>
色覚をシミュレーション → <a href="/ja/tools/color-blindness-simulator/">色覚シミュレーター</a>
</div>

<script>
(function() {
'use strict';

const canvas = document.getElementById('cw-wheel');
const ctx = canvas.getContext('2d');
const SIZE = 300;
const CX = SIZE / 2;
const CY = SIZE / 2;
const R = SIZE / 2 - 6;

let selectedHue = 0;
let lightness = 50;
let mode = 'complementary';
let isDragging = false;

const lightnessSlider = document.getElementById('cw-lightness');
const lightnessVal = document.getElementById('cw-lightness-val');
const swatchesEl = document.getElementById('cw-swatches');
const detailSwatch = document.getElementById('cw-detail-swatch');
const valHex = document.getElementById('cw-val-hex');
const valRgb = document.getElementById('cw-val-rgb');
const valHsl = document.getElementById('cw-val-hsl');
const cssOutput = document.getElementById('cw-css-output');
const cssCopyBtn = document.getElementById('cw-css-copy-btn');
const toast = document.getElementById('cw-toast');
const prevWhite = document.getElementById('cw-prev-white');
const prevBlack = document.getElementById('cw-prev-black');
const crWhite = document.getElementById('cw-cr-white');
const crBlack = document.getElementById('cw-cr-black');

// --- Color utilities ---
function hslToRgb(h, s, l) {
s /= 100; l /= 100;
const k = n => (n + h / 30) % 12;
const a = s * Math.min(l, 1 - l);
const f = n => l - a * Math.max(-1, Math.min(k(n) - 3, Math.min(9 - k(n), 1)));
return [Math.round(f(0)*255), Math.round(f(8)*255), Math.round(f(4)*255)];
}

function rgbToHex(r, g, b) {
return '#' + [r,g,b].map(x => x.toString(16).padStart(2,'0')).join('');
}

function hslToHex(h, s, l) {
const [r,g,b] = hslToRgb(h, s, l);
return rgbToHex(r, g, b);
}

function hslToRgbStr(h, s, l) {
const [r,g,b] = hslToRgb(h, s, l);
return `rgb(${r}, ${g}, ${b})`;
}

function relativeLuminance(r, g, b) {
const c = [r, g, b].map(v => {
v /= 255;
return v <= 0.04045 ? v / 12.92 : Math.pow((v + 0.055) / 1.055, 2.4);
});
return 0.2126 * c[0] + 0.7152 * c[1] + 0.0722 * c[2];
}

function contrastRatio(r1, g1, b1, r2, g2, b2) {
const L1 = relativeLuminance(r1, g1, b1);
const L2 = relativeLuminance(r2, g2, b2);
const lighter = Math.max(L1, L2);
const darker = Math.min(L1, L2);
return (lighter + 0.05) / (darker + 0.05);
}

function wcagBadge(ratio) {
const r = ratio.toFixed(2);
if (ratio >= 7) return `<span class="cw-wcag-badge cw-wcag-pass">AAA (${r}:1)</span>`;
if (ratio >= 4.5) return `<span class="cw-wcag-badge cw-wcag-pass">AA (${r}:1)</span>`;
if (ratio >= 3) return `<span class="cw-wcag-badge cw-wcag-fail">AA大 (${r}:1)</span>`;
return `<span class="cw-wcag-badge cw-wcag-fail">不合格 (${r}:1)</span>`;
}

// --- Harmony modes ---
function getHarmonyHues(baseHue, m) {
switch(m) {
case 'complementary': return [baseHue, (baseHue + 180) % 360];
case 'analogous':     return [baseHue, (baseHue + 30) % 360, (baseHue + 330) % 360];
case 'triadic':       return [baseHue, (baseHue + 120) % 360, (baseHue + 240) % 360];
case 'split':         return [baseHue, (baseHue + 150) % 360, (baseHue + 210) % 360];
case 'tetradic':      return [baseHue, (baseHue + 90) % 360, (baseHue + 180) % 360, (baseHue + 270) % 360];
default:              return [baseHue];
}
}

const modeNames = {
complementary: '補色',
analogous:     '類似色',
triadic:       'トライアド',
split:         '分裂補色',
tetradic:      'テトラード'
};

const swatchLabels = {
complementary: ['ベース', '補色'],
analogous:     ['ベース', '+30°', '-30°'],
triadic:       ['ベース', '+120°', '+240°'],
split:         ['ベース', '+150°', '+210°'],
tetradic:      ['ベース', '+90°', '+180°', '+270°']
};

// --- Draw wheel ---
function drawWheel() {
ctx.clearRect(0, 0, SIZE, SIZE);
// Draw hue ring
for (let angle = 0; angle < 360; angle += 1) {
const startAngle = (angle - 1) * Math.PI / 180;
const endAngle = (angle + 1) * Math.PI / 180;
ctx.beginPath();
ctx.moveTo(CX, CY);
ctx.arc(CX, CY, R, startAngle, endAngle);
ctx.closePath();
ctx.fillStyle = `hsl(${angle}, 80%, ${lightness}%)`;
ctx.fill();
}
// White center fade
const grad = ctx.createRadialGradient(CX, CY, 0, CX, CY, R);
grad.addColorStop(0, 'rgba(255,255,255,0.85)');
grad.addColorStop(0.45, 'rgba(255,255,255,0.0)');
ctx.beginPath();
ctx.arc(CX, CY, R, 0, Math.PI * 2);
ctx.fillStyle = grad;
ctx.fill();

// Draw harmony dots
const hues = getHarmonyHues(selectedHue, mode);
hues.forEach((h, i) => {
const angle = (h * Math.PI) / 180;
const dotR = R * 0.82;
const x = CX + dotR * Math.cos(angle);
const y = CY + dotR * Math.sin(angle);
ctx.beginPath();
ctx.arc(x, y, i === 0 ? 11 : 8, 0, Math.PI * 2);
ctx.fillStyle = `hsl(${h}, 80%, ${lightness}%)`;
ctx.fill();
ctx.lineWidth = i === 0 ? 3 : 2;
ctx.strokeStyle = '#fff';
ctx.stroke();
ctx.beginPath();
ctx.arc(x, y, i === 0 ? 11 : 8, 0, Math.PI * 2);
ctx.lineWidth = i === 0 ? 2 : 1.5;
ctx.strokeStyle = '#334155';
ctx.stroke();
});
}

// --- Update UI ---
function updateUI() {
const hues = getHarmonyHues(selectedHue, mode);
const labels = swatchLabels[mode] || [];

// Swatches
swatchesEl.innerHTML = '';
hues.forEach((h, i) => {
const hex = hslToHex(h, 80, lightness);
const item = document.createElement('div');
item.className = 'cw-swatch-item';
item.title = `${hex} をコピー`;
item.innerHTML = `<div class="cw-swatch-box" style="background:${hex};"></div><span class="cw-swatch-label">${labels[i] || ''}<br>${hex}</span>`;
item.addEventListener('click', () => copyText(hex));
swatchesEl.appendChild(item);
});

// Detail for base color
const h = selectedHue;
const [r, g, b] = hslToRgb(h, 80, lightness);
const hex = hslToHex(h, 80, lightness);
const rgb = `rgb(${r}, ${g}, ${b})`;
const hsl = `hsl(${h}, 80%, ${lightness}%)`;
detailSwatch.style.background = hex;
valHex.textContent = hex;
valRgb.textContent = rgb;
valHsl.textContent = hsl;
valHex.onclick = () => copyText(hex);
valRgb.onclick = () => copyText(rgb);
valHsl.onclick = () => copyText(hsl);

// Contrast
const crW = contrastRatio(r, g, b, 255, 255, 255);
const crB = contrastRatio(r, g, b, 0, 0, 0);
prevWhite.style.background = '#fff';
prevWhite.style.color = hex;
prevWhite.textContent = 'Aa テキストサンプル';
prevBlack.style.background = '#000';
prevBlack.style.color = hex;
prevBlack.textContent = 'Aa テキストサンプル';
crWhite.innerHTML = `白背景: ${wcagBadge(crW)}`;
crBlack.innerHTML = `黒背景: ${wcagBadge(crB)}`;

// CSS output
const cssLines = hues.map((hh, i) => {
const chex = hslToHex(hh, 80, lightness);
const name = (labels[i] || `color-${i+1}`).replace(/[°\s]/g, '-').toLowerCase();
return `  --cw-${name}: ${chex};`;
}).join('\n');
const mName = modeNames[mode] || mode;
cssOutput.textContent = `:root {\n  /* ${mName} */\n${cssLines}\n}`;

drawWheel();
}

// --- Interaction ---
function hueFromXY(x, y) {
const dx = x - CX;
const dy = y - CY;
let angle = Math.atan2(dy, dx) * 180 / Math.PI;
if (angle < 0) angle += 360;
return Math.round(angle);
}

function handlePointer(e) {
const rect = canvas.getBoundingClientRect();
const scaleX = SIZE / rect.width;
const scaleY = SIZE / rect.height;
let clientX, clientY;
if (e.touches) {
clientX = e.touches[0].clientX;
clientY = e.touches[0].clientY;
} else {
clientX = e.clientX;
clientY = e.clientY;
}
const x = (clientX - rect.left) * scaleX;
const y = (clientY - rect.top) * scaleY;
const dx = x - CX;
const dy = y - CY;
const dist = Math.sqrt(dx*dx + dy*dy);
if (dist <= R) {
selectedHue = hueFromXY(x, y);
updateUI();
}
}

canvas.addEventListener('mousedown', e => { isDragging = true; handlePointer(e); });
canvas.addEventListener('mousemove', e => { if (isDragging) handlePointer(e); });
document.addEventListener('mouseup', () => { isDragging = false; });
canvas.addEventListener('touchstart', e => { e.preventDefault(); isDragging = true; handlePointer(e); }, {passive: false});
canvas.addEventListener('touchmove', e => { e.preventDefault(); if (isDragging) handlePointer(e); }, {passive: false});
document.addEventListener('touchend', () => { isDragging = false; });

// Mode buttons
document.querySelectorAll('#cw-app .cw-mode-btn').forEach(btn => {
btn.addEventListener('click', () => {
document.querySelectorAll('#cw-app .cw-mode-btn').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
mode = btn.dataset.mode;
updateUI();
});
});

// Lightness slider
lightnessSlider.addEventListener('input', () => {
lightness = parseInt(lightnessSlider.value);
lightnessVal.textContent = lightness + '%';
updateUI();
});

// CSS copy
cssCopyBtn.addEventListener('click', () => {
copyText(cssOutput.textContent);
});

// Copy helper
function copyText(text) {
navigator.clipboard.writeText(text).then(() => {
toast.classList.add('show');
setTimeout(() => toast.classList.remove('show'), 1600);
}).catch(() => {
// fallback
const ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
toast.classList.add('show');
setTimeout(() => toast.classList.remove('show'), 1600);
});
}

// Init
updateUI();
})();
</script>

</div>

> カラーパレットを生成 → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)
> コントラスト比を確認 → [カラーコントラストチェッカー](/ja/tools/color-contrast-checker/)
> 色覚をシミュレーション → [色覚シミュレーター](/ja/tools/color-blindness-simulator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
