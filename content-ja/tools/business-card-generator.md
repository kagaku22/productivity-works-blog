---
title: "名刺ジェネレーター"
description: "無料のオンライン名刺作成ツール。名前・会社名・連絡先を入力してプロフェッショナルな名刺をデザイン。テンプレート選択・PNG保存・印刷対応。会員登録不要。"
slug: business-card-generator
date: 2025-11-27
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/business-card-generator-ja.png
  alt: "名刺ジェネレーター"
---

名前・会社名・連絡先を入力するだけで、プロ仕様の名刺をすぐに作成できます。会員登録不要・完全無料。

<div id="bc-app">

<style>
#bc-app * { box-sizing: border-box; margin: 0; padding: 0; }
#bc-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
color: #1e293b;
}
#bc-app h2 {
font-size: 1.1rem;
font-weight: 700;
color: #1e293b;
margin-bottom: 12px;
padding-bottom: 6px;
border-bottom: 2px solid #e2e8f0;
}
#bc-app .bc-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 24px;
margin-top: 16px;
}
@media (max-width: 680px) {
#bc-app .bc-layout { grid-template-columns: 1fr; }
}
#bc-app .bc-panel {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 20px;
}
#bc-app label {
display: block;
font-size: 12px;
font-weight: 600;
color: #64748b;
margin-bottom: 4px;
margin-top: 12px;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#bc-app label:first-child { margin-top: 0; }
#bc-app input[type="text"],
#bc-app input[type="email"],
#bc-app input[type="tel"],
#bc-app input[type="url"] {
width: 100%;
padding: 8px 10px;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 14px;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
}
#bc-app input[type="text"]:focus,
#bc-app input[type="email"]:focus,
#bc-app input[type="tel"]:focus,
#bc-app input[type="url"]:focus {
outline: none;
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,0.1);
}
#bc-app .bc-templates {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 8px;
margin-bottom: 4px;
}
#bc-app .bc-tpl-btn {
padding: 7px 4px;
border: 2px solid #e2e8f0;
border-radius: 6px;
font-size: 11px;
font-weight: 600;
cursor: pointer;
background: #fff;
color: #475569;
transition: all 0.15s;
text-align: center;
}
#bc-app .bc-tpl-btn:hover { border-color: #6366f1; color: #6366f1; }
#bc-app .bc-tpl-btn.active { border-color: #6366f1; background: #6366f1; color: #fff; }
#bc-app .bc-colors {
display: flex;
gap: 12px;
align-items: flex-end;
flex-wrap: wrap;
}
#bc-app .bc-color-group { flex: 1; min-width: 80px; }
#bc-app input[type="color"] {
width: 100%;
height: 36px;
border: 1px solid #cbd5e1;
border-radius: 6px;
padding: 2px;
cursor: pointer;
background: #fff;
}
#bc-app .bc-preview-area { margin-top: 0; }
#bc-app .bc-tabs {
display: flex;
gap: 4px;
margin-bottom: 14px;
}
#bc-app .bc-tab {
padding: 6px 14px;
border: 1px solid #e2e8f0;
border-radius: 6px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
background: #fff;
color: #64748b;
transition: all 0.15s;
}
#bc-app .bc-tab.active { background: #6366f1; color: #fff; border-color: #6366f1; }
#bc-app .bc-canvas-wrap {
display: flex;
justify-content: center;
align-items: center;
padding: 24px;
background: #e2e8f0;
border-radius: 10px;
min-height: 180px;
}
#bc-app canvas {
border-radius: 8px;
box-shadow: 0 4px 24px rgba(0,0,0,0.18);
max-width: 100%;
height: auto;
}
#bc-app .bc-actions {
display: flex;
gap: 10px;
margin-top: 14px;
flex-wrap: wrap;
}
#bc-app .bc-btn {
flex: 1;
min-width: 120px;
padding: 10px 16px;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: all 0.15s;
text-align: center;
}
#bc-app .bc-btn-primary { background: #6366f1; color: #fff; }
#bc-app .bc-btn-primary:hover { background: #4f46e5; }
#bc-app .bc-btn-secondary { background: #fff; color: #1e293b; border: 1.5px solid #cbd5e1; }
#bc-app .bc-btn-secondary:hover { border-color: #6366f1; color: #6366f1; }
#bc-app .bc-toggle-row {
display: flex;
align-items: center;
gap: 8px;
margin-top: 12px;
font-size: 13px;
color: #475569;
}
#bc-app .bc-toggle {
width: 36px;
height: 20px;
border-radius: 10px;
background: #cbd5e1;
position: relative;
cursor: pointer;
border: none;
transition: background 0.2s;
flex-shrink: 0;
}
#bc-app .bc-toggle.on { background: #6366f1; }
#bc-app .bc-toggle::after {
content: '';
position: absolute;
width: 14px;
height: 14px;
background: #fff;
border-radius: 50%;
top: 3px;
left: 3px;
transition: left 0.2s;
}
#bc-app .bc-toggle.on::after { left: 19px; }
#bc-app .bc-note {
font-size: 12px;
color: #94a3b8;
margin-top: 8px;
line-height: 1.5;
}

@media print {
body * { visibility: hidden; }
#bc-print-target, #bc-print-target * { visibility: visible; }
#bc-print-target {
position: fixed;
top: 0; left: 0;
display: flex;
flex-direction: column;
gap: 16px;
align-items: center;
justify-content: center;
width: 100%;
height: 100%;
background: #fff;
}
}
</style>

<div id="bc-print-target" style="display:none;"></div>

<div class="bc-layout">
<div class="bc-panel">
<h2>名刺情報の入力</h2>

<label>氏名</label>
<input type="text" id="bc-name" placeholder="山田 太郎" value="山田 太郎" />

<label>役職</label>
<input type="text" id="bc-title" placeholder="代表取締役" value="代表取締役" />

<label>会社名</label>
<input type="text" id="bc-company" placeholder="株式会社サンプル" value="株式会社サンプル" />

<label>メールアドレス</label>
<input type="email" id="bc-email" placeholder="yamada@sample.co.jp" value="yamada@sample.co.jp" />

<label>電話番号</label>
<input type="tel" id="bc-phone" placeholder="03-0000-0000" value="03-0000-0000" />

<label>ウェブサイト</label>
<input type="url" id="bc-website" placeholder="sample.co.jp" value="sample.co.jp" />

<label>住所</label>
<input type="text" id="bc-address" placeholder="東京都渋谷区〇〇 1-2-3" value="東京都渋谷区〇〇 1-2-3" />

<label style="margin-top:16px;">レイアウト</label>
<div class="bc-templates">
<button class="bc-tpl-btn active" data-tpl="classic" onclick="(function(){window._bcSetTpl('classic');})()">クラシック</button>
<button class="bc-tpl-btn" data-tpl="modern" onclick="(function(){window._bcSetTpl('modern');})()">モダン</button>
<button class="bc-tpl-btn" data-tpl="minimal" onclick="(function(){window._bcSetTpl('minimal');})()">ミニマル</button>
<button class="bc-tpl-btn" data-tpl="bold" onclick="(function(){window._bcSetTpl('bold');})()">ボールド</button>
</div>

<label style="margin-top:16px;">カラー</label>
<div class="bc-colors">
<div class="bc-color-group">
<label style="margin-top:0;">背景色</label>
<input type="color" id="bc-color-bg" value="#1e293b" />
</div>
<div class="bc-color-group">
<label style="margin-top:0;">アクセント</label>
<input type="color" id="bc-color-accent" value="#6366f1" />
</div>
<div class="bc-color-group">
<label style="margin-top:0;">文字色</label>
<input type="color" id="bc-color-text" value="#ffffff" />
</div>
</div>

<div class="bc-toggle-row">
<button class="bc-toggle on" id="bc-qr-toggle" onclick="(function(){window._bcToggleQr();})()"></button>
<span>裏面にQRコードを表示</span>
</div>

<p class="bc-note">名刺サイズ: 91 × 55 mm（日本標準サイズ）</p>
</div>

<div class="bc-panel bc-preview-area">
<h2>プレビュー</h2>
<div class="bc-tabs">
<button class="bc-tab active" id="bc-tab-front" onclick="(function(){window._bcShowSide('front');})()">表面</button>
<button class="bc-tab" id="bc-tab-back" onclick="(function(){window._bcShowSide('back');})()">裏面</button>
</div>
<div class="bc-canvas-wrap">
<canvas id="bc-canvas" width="700" height="400"></canvas>
</div>
<div class="bc-actions">
<button class="bc-btn bc-btn-primary" onclick="(function(){window._bcDownload();})()">PNGでダウンロード</button>
<button class="bc-btn bc-btn-secondary" onclick="(function(){window._bcPrint();})()">印刷する</button>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">起業の会計管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、起業時の経費管理・請求書作成もクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>
</div>
</div>

<script>
(function() {
var state = {
name: '山田 太郎',
title: '代表取締役',
company: '株式会社サンプル',
email: 'yamada@sample.co.jp',
phone: '03-0000-0000',
website: 'sample.co.jp',
address: '東京都渋谷区〇〇 1-2-3',
tpl: 'classic',
bgColor: '#1e293b',
accentColor: '#6366f1',
textColor: '#ffffff',
showQr: true,
side: 'front'
};

var DPR = 2;
var CARD_W = 700;
var CARD_H = 400;

function bind(id, key) {
var el = document.getElementById(id);
if (!el) return;
el.addEventListener('input', function() {
state[key] = el.value;
render();
});
}

bind('bc-name', 'name');
bind('bc-title', 'title');
bind('bc-company', 'company');
bind('bc-email', 'email');
bind('bc-phone', 'phone');
bind('bc-website', 'website');
bind('bc-address', 'address');

document.getElementById('bc-color-bg').addEventListener('input', function() {
state.bgColor = this.value; render();
});
document.getElementById('bc-color-accent').addEventListener('input', function() {
state.accentColor = this.value; render();
});
document.getElementById('bc-color-text').addEventListener('input', function() {
state.textColor = this.value; render();
});

window._bcSetTpl = function(tpl) {
state.tpl = tpl;
document.querySelectorAll('#bc-app .bc-tpl-btn').forEach(function(b) {
b.classList.toggle('active', b.dataset.tpl === tpl);
});
var presets = {
classic: { bg: '#1e293b', accent: '#6366f1', text: '#ffffff' },
modern:  { bg: '#0f172a', accent: '#06b6d4', text: '#ffffff' },
minimal: { bg: '#ffffff', accent: '#1e293b', text: '#1e293b' },
bold:    { bg: '#7c3aed', accent: '#fbbf24', text: '#ffffff' }
};
if (presets[tpl]) {
state.bgColor = presets[tpl].bg;
state.accentColor = presets[tpl].accent;
state.textColor = presets[tpl].text;
document.getElementById('bc-color-bg').value = state.bgColor;
document.getElementById('bc-color-accent').value = state.accentColor;
document.getElementById('bc-color-text').value = state.textColor;
}
render();
};

window._bcShowSide = function(side) {
state.side = side;
document.getElementById('bc-tab-front').classList.toggle('active', side === 'front');
document.getElementById('bc-tab-back').classList.toggle('active', side === 'back');
render();
};

window._bcToggleQr = function() {
state.showQr = !state.showQr;
var btn = document.getElementById('bc-qr-toggle');
btn.classList.toggle('on', state.showQr);
render();
};

function drawFront(ctx, W, H, s) {
ctx.clearRect(0, 0, W, H);
ctx.fillStyle = s.bgColor;
ctx.beginPath();
ctx.roundRect(0, 0, W, H, 18);
ctx.fill();

if (s.tpl === 'classic') {
ctx.fillStyle = s.accentColor;
ctx.beginPath();
ctx.roundRect(0, 0, 10, H, [18, 0, 0, 18]);
ctx.fill();

ctx.fillStyle = s.textColor;
ctx.font = 'bold ' + Math.round(H * 0.115) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.name, 36, H * 0.27);

ctx.fillStyle = s.accentColor;
ctx.font = Math.round(H * 0.072) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.title, 36, H * 0.39);

ctx.fillStyle = s.accentColor;
ctx.globalAlpha = 0.3;
ctx.fillRect(36, H * 0.43, W - 72, 1.5);
ctx.globalAlpha = 1;

ctx.fillStyle = s.textColor;
ctx.globalAlpha = 0.85;
ctx.font = 'bold ' + Math.round(H * 0.072) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.company, 36, H * 0.55);
ctx.globalAlpha = 1;

var infoY = H * 0.66;
var lineH = H * 0.1;
ctx.font = Math.round(H * 0.062) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillStyle = s.textColor;
ctx.globalAlpha = 0.75;
if (s.email) { ctx.fillText(s.email, 36, infoY); infoY += lineH; }
if (s.phone) { ctx.fillText(s.phone, 36, infoY); infoY += lineH; }
ctx.globalAlpha = 1;
if (s.website) { ctx.fillStyle = s.accentColor; ctx.fillText(s.website, 36, infoY); }

} else if (s.tpl === 'modern') {
var grad = ctx.createLinearGradient(0, 0, W, 0);
grad.addColorStop(0, s.accentColor);
grad.addColorStop(1, s.bgColor);
ctx.fillStyle = grad;
ctx.fillRect(0, 0, W, H * 0.38);
ctx.fillStyle = s.bgColor;
ctx.fillRect(0, H * 0.38, W, H * 0.62);

ctx.fillStyle = '#ffffff';
ctx.font = 'bold ' + Math.round(H * 0.11) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.name, 30, H * 0.28);

ctx.fillStyle = s.accentColor;
ctx.font = Math.round(H * 0.07) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.title + (s.company ? '  /  ' + s.company : ''), 30, H * 0.5);

ctx.fillStyle = s.textColor;
ctx.globalAlpha = 0.8;
ctx.font = Math.round(H * 0.062) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
var cy = H * 0.64;
var cl = H * 0.1;
if (s.email) { ctx.fillText(s.email, 30, cy); cy += cl; }
if (s.phone) { ctx.fillText(s.phone, 30, cy); cy += cl; }
if (s.website) { ctx.fillStyle = s.accentColor; ctx.globalAlpha = 1; ctx.fillText(s.website, 30, cy); }
ctx.globalAlpha = 1;

} else if (s.tpl === 'minimal') {
ctx.fillStyle = s.accentColor;
ctx.fillRect(0, 0, W, 6);

ctx.fillStyle = s.accentColor;
ctx.font = 'bold ' + Math.round(H * 0.07) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.textAlign = 'right';
ctx.fillText(s.company, W - 30, H * 0.18);
ctx.textAlign = 'left';

ctx.fillStyle = s.textColor;
ctx.font = 'bold ' + Math.round(H * 0.12) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.name, 30, H * 0.42);

ctx.fillStyle = s.accentColor;
ctx.globalAlpha = 0.75;
ctx.font = Math.round(H * 0.07) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.title, 30, H * 0.56);
ctx.globalAlpha = 1;

ctx.fillStyle = s.textColor;
ctx.globalAlpha = 0.6;
ctx.font = Math.round(H * 0.058) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
var parts = [s.email, s.phone, s.website].filter(Boolean).join('   |   ');
ctx.fillText(parts, 30, H * 0.82);
ctx.globalAlpha = 1;

ctx.fillStyle = s.accentColor;
ctx.globalAlpha = 0.15;
ctx.fillRect(0, H - 6, W, 6);
ctx.globalAlpha = 1;

} else if (s.tpl === 'bold') {
ctx.fillStyle = s.accentColor;
ctx.beginPath();
ctx.moveTo(0, 0);
ctx.lineTo(W * 0.55, 0);
ctx.lineTo(W * 0.38, H);
ctx.lineTo(0, H);
ctx.closePath();
ctx.fill();

ctx.fillStyle = '#ffffff';
ctx.font = 'bold ' + Math.round(H * 0.105) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.name, 28, H * 0.28);

ctx.font = Math.round(H * 0.065) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.globalAlpha = 0.85;
ctx.fillText(s.title, 28, H * 0.42);
ctx.globalAlpha = 1;

if (s.company) {
ctx.font = 'bold ' + Math.round(H * 0.065) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.company, 28, H * 0.56);
}

ctx.fillStyle = s.textColor;
ctx.font = Math.round(H * 0.062) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
var ry = H * 0.3;
var rl = H * 0.1;
var rx = W * 0.46;
ctx.globalAlpha = 0.8;
if (s.email) { ctx.fillText(s.email, rx, ry); ry += rl; }
if (s.phone) { ctx.fillText(s.phone, rx, ry); ry += rl; }
if (s.website) { ctx.fillStyle = s.accentColor; ctx.globalAlpha = 1; ctx.fillText(s.website, rx, ry); ry += rl; }
ctx.globalAlpha = 0.7;
ctx.fillStyle = s.textColor;
if (s.address) { ctx.fillText(s.address, rx, ry); }
ctx.globalAlpha = 1;
}
}

function drawQr(ctx, x, y, size, data) {
var cells = 17;
var cell = size / cells;
ctx.fillStyle = '#ffffff';
ctx.fillRect(x - 2, y - 2, size + 4, size + 4);
ctx.fillStyle = '#000000';

var seed = 0;
for (var i = 0; i < data.length; i++) seed = (seed * 31 + data.charCodeAt(i)) & 0xffff;
function rand() { seed = (seed * 1664525 + 1013904223) & 0xffffffff; return (seed >>> 0) / 4294967296; }

for (var r = 0; r < cells; r++) {
for (var c = 0; c < cells; c++) {
var isFinder = (r < 3 && c < 3) || (r < 3 && c >= cells-3) || (r >= cells-3 && c < 3);
var filled = isFinder ? true : rand() > 0.5;
if (filled) ctx.fillRect(x + c * cell, y + r * cell, cell - 0.5, cell - 0.5);
}
}

ctx.fillStyle = '#000';
[[0,0],[0,cells-3],[cells-3,0]].forEach(function(pos) {
var pr = pos[0], pc = pos[1];
ctx.fillStyle = '#000';
ctx.fillRect(x + pc*cell, y + pr*cell, 3*cell, 3*cell);
ctx.fillStyle = '#fff';
ctx.fillRect(x + pc*cell+cell*0.2, y + pr*cell+cell*0.2, cell*2.6, cell*2.6);
ctx.fillStyle = '#000';
ctx.fillRect(x + pc*cell+cell*0.6, y + pr*cell+cell*0.6, cell*1.8, cell*1.8);
});
}

function drawBack(ctx, W, H, s) {
ctx.clearRect(0, 0, W, H);
ctx.fillStyle = s.bgColor;
ctx.beginPath();
ctx.roundRect(0, 0, W, H, 18);
ctx.fill();

ctx.fillStyle = s.accentColor;
ctx.globalAlpha = 0.12;
ctx.fillRect(0, H * 0.35, W, H * 0.3);
ctx.globalAlpha = 1;

ctx.fillStyle = s.textColor;
ctx.textAlign = 'center';
ctx.font = 'bold ' + Math.round(H * 0.13) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.fillText(s.company || s.name, W / 2, H * 0.38);

ctx.fillStyle = s.accentColor;
ctx.font = Math.round(H * 0.07) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
if (s.website) ctx.fillText(s.website, W / 2, H * 0.54);
ctx.textAlign = 'left';

if (s.showQr) {
var qrSize = Math.round(H * 0.42);
var qrX = W - qrSize - 28;
var qrY = Math.round((H - qrSize) / 2);
drawQr(ctx, qrX, qrY, qrSize, s.website || s.email || s.name);

ctx.fillStyle = s.textColor;
ctx.globalAlpha = 0.5;
ctx.font = Math.round(H * 0.052) + 'px -apple-system,\'Hiragino Sans\',\'Noto Sans JP\',sans-serif';
ctx.textAlign = 'right';
ctx.fillText('QRコードで読み取り', W - 28, H - 20);
ctx.textAlign = 'left';
ctx.globalAlpha = 1;
}

ctx.fillStyle = s.accentColor;
ctx.globalAlpha = 0.15;
for (var i = 0; i < 5; i++) {
ctx.beginPath();
ctx.arc(28 + i * 18, H - 24, 5, 0, Math.PI * 2);
ctx.fill();
}
ctx.globalAlpha = 1;
}

function render() {
var canvas = document.getElementById('bc-canvas');
if (!canvas) return;
var ctx = canvas.getContext('2d');

canvas.width = CARD_W * DPR;
canvas.height = CARD_H * DPR;
canvas.style.width = CARD_W + 'px';
canvas.style.height = CARD_H + 'px';
ctx.scale(DPR, DPR);

if (state.side === 'front') {
drawFront(ctx, CARD_W, CARD_H, state);
} else {
drawBack(ctx, CARD_W, CARD_H, state);
}
}

window._bcDownload = function() {
var canvas = document.getElementById('bc-canvas');
var link = document.createElement('a');
link.download = 'meishi-' + state.side + '.png';
link.href = canvas.toDataURL('image/png');
link.click();
};

window._bcPrint = function() {
var pt = document.getElementById('bc-print-target');
var tempF = document.createElement('canvas');
var tempB = document.createElement('canvas');
tempF.width = CARD_W * DPR; tempF.height = CARD_H * DPR;
tempB.width = CARD_W * DPR; tempB.height = CARD_H * DPR;
tempF.style.width = CARD_W + 'px'; tempF.style.height = CARD_H + 'px';
tempB.style.width = CARD_W + 'px'; tempB.style.height = CARD_H + 'px';

var ctxF = tempF.getContext('2d'); ctxF.scale(DPR, DPR);
var ctxB = tempB.getContext('2d'); ctxB.scale(DPR, DPR);
drawFront(ctxF, CARD_W, CARD_H, state);
drawBack(ctxB, CARD_W, CARD_H, state);

pt.style.display = 'flex';
pt.innerHTML = '';
pt.appendChild(tempF);
pt.appendChild(tempB);
window.print();
pt.style.display = 'none';
};

render();
})();
</script>

---

**関連ツール**

- 請求書を作成 → [請求書ジェネレーター](/ja/tools/invoice-generator/)
- メール署名 → [メール署名ジェネレーター](/ja/tools/email-signature-generator/)
- QRコード作成 → [QRコードジェネレーター](/ja/tools/qr-code-generator/)

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
