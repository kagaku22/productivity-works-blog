---
title: "ページサイズ分析ツール - 読み込み時間を推定"
date: 2025-10-29
description: "Webページの各アセットサイズを入力するだけで、接続速度別の推定読み込み時間・パフォーマンススコア・最適化アドバイスを瞬時に表示します。"
categories: ["無料ツール"]
slug: "page-size-analyzer"
ShowToc: false
cover:
  image: "/images/covers/page-size-analyzer.png"
  alt: "ページサイズ分析ツール"
---

<div id="psa-app">

<style>
#psa-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Yu Gothic", sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a1a2e;
}
#psa-app h2 {
font-size: 1.5rem;
margin: 1.5rem 0 0.75rem;
color: #16213e;
border-left: 4px solid #0f3460;
padding-left: 0.6rem;
}
#psa-app .psa-intro {
background: #eef2ff;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-bottom: 1.5rem;
font-size: 0.95rem;
color: #3a3a5c;
line-height: 1.7;
}
#psa-app .psa-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
margin-bottom: 1rem;
}
@media (max-width: 600px) {
#psa-app .psa-grid { grid-template-columns: 1fr; }
}
#psa-app .psa-field {
display: flex;
flex-direction: column;
gap: 0.3rem;
}
#psa-app label {
font-size: 0.85rem;
font-weight: 700;
color: #444;
}
#psa-app input[type="number"],
#psa-app select {
padding: 0.55rem 0.75rem;
border: 1.5px solid #c8d0e7;
border-radius: 7px;
font-size: 1rem;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.2s;
}
#psa-app input[type="number"]:focus,
#psa-app select:focus {
border-color: #0f3460;
}
#psa-app .psa-speed-row {
display: flex;
gap: 1rem;
align-items: flex-end;
margin-bottom: 1rem;
flex-wrap: wrap;
}
#psa-app .psa-speed-row .psa-field {
flex: 1;
min-width: 180px;
}
#psa-app .psa-btn {
padding: 0.7rem 2rem;
background: #0f3460;
color: #fff;
border: none;
border-radius: 8px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
white-space: nowrap;
}
#psa-app .psa-btn:hover { background: #16213e; }
#psa-app .psa-btn:active { transform: scale(0.97); }
#psa-app .psa-reset-btn {
padding: 0.7rem 1.2rem;
background: #e8eaf6;
color: #0f3460;
border: 1.5px solid #c8d0e7;
border-radius: 8px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.2s;
}
#psa-app .psa-reset-btn:hover { background: #dde0f5; }
#psa-app .psa-results {
display: none;
margin-top: 1.5rem;
animation: psaFadeIn 0.35s ease;
}
@keyframes psaFadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: none; } }
#psa-app .psa-summary-cards {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 1rem;
margin-bottom: 1.5rem;
}
@media (max-width: 600px) {
#psa-app .psa-summary-cards { grid-template-columns: 1fr 1fr; }
}
#psa-app .psa-card {
background: #fff;
border: 1.5px solid #e0e5f0;
border-radius: 10px;
padding: 1rem;
text-align: center;
box-shadow: 0 2px 8px rgba(15,52,96,0.06);
}
#psa-app .psa-card .psa-card-label {
font-size: 0.78rem;
color: #888;
font-weight: 700;
margin-bottom: 0.4rem;
}
#psa-app .psa-card .psa-card-value {
font-size: 1.7rem;
font-weight: 800;
color: #0f3460;
line-height: 1.1;
}
#psa-app .psa-card .psa-card-sub {
font-size: 0.8rem;
color: #aaa;
margin-top: 0.2rem;
}
#psa-app .psa-score-wrap {
display: flex;
align-items: center;
gap: 1.25rem;
background: #fff;
border: 1.5px solid #e0e5f0;
border-radius: 10px;
padding: 1.1rem 1.4rem;
margin-bottom: 1.5rem;
box-shadow: 0 2px 8px rgba(15,52,96,0.06);
flex-wrap: wrap;
}
#psa-app .psa-score-circle {
width: 90px;
height: 90px;
border-radius: 50%;
display: flex;
align-items: center;
justify-content: center;
flex-shrink: 0;
}
#psa-app .psa-score-num {
font-size: 2.1rem;
font-weight: 900;
color: #fff;
}
#psa-app .psa-score-info { flex: 1; min-width: 160px; }
#psa-app .psa-score-grade {
font-size: 1.2rem;
font-weight: 800;
margin-bottom: 0.25rem;
}
#psa-app .psa-score-desc {
font-size: 0.88rem;
color: #666;
line-height: 1.6;
}
#psa-app .psa-chart-wrap {
background: #fff;
border: 1.5px solid #e0e5f0;
border-radius: 10px;
padding: 1.2rem;
margin-bottom: 1.5rem;
box-shadow: 0 2px 8px rgba(15,52,96,0.06);
}
#psa-app canvas { display: block; max-width: 100%; }
#psa-app .psa-recs {
background: #fff;
border: 1.5px solid #e0e5f0;
border-radius: 10px;
padding: 1.2rem 1.4rem;
margin-bottom: 1.5rem;
box-shadow: 0 2px 8px rgba(15,52,96,0.06);
}
#psa-app .psa-recs h3 {
font-size: 1.05rem;
font-weight: 700;
color: #16213e;
margin: 0 0 0.75rem;
}
#psa-app .psa-rec-item {
display: flex;
align-items: flex-start;
gap: 0.6rem;
margin-bottom: 0.55rem;
font-size: 0.92rem;
color: #333;
line-height: 1.6;
}
#psa-app .psa-rec-icon {
font-size: 1rem;
flex-shrink: 0;
margin-top: 0.1rem;
}
#psa-app .psa-compare {
background: #f0f7ff;
border: 1.5px solid #b8d4f0;
border-radius: 10px;
padding: 1.2rem 1.4rem;
margin-bottom: 1.5rem;
}
#psa-app .psa-compare h3 {
font-size: 1.05rem;
font-weight: 700;
color: #0f3460;
margin: 0 0 0.75rem;
}
#psa-app .psa-compare-note {
font-size: 0.85rem;
color: #555;
margin-bottom: 0.75rem;
line-height: 1.6;
}
#psa-app .psa-opt-grid {
display: grid;
grid-template-columns: 1fr 1fr 1fr;
gap: 0.75rem;
margin-bottom: 0.75rem;
}
@media (max-width: 600px) {
#psa-app .psa-opt-grid { grid-template-columns: 1fr; }
}
#psa-app .psa-opt-label {
font-size: 0.8rem;
font-weight: 700;
color: #444;
margin-bottom: 0.3rem;
}
#psa-app .psa-opt-input {
width: 100%;
box-sizing: border-box;
}
#psa-app .psa-compare-result {
display: none;
margin-top: 1rem;
padding-top: 1rem;
border-top: 1px solid #c8dff0;
}
#psa-app .psa-compare-bars {
display: flex;
flex-direction: column;
gap: 0.6rem;
margin-top: 0.5rem;
}
#psa-app .psa-bar-row {
display: flex;
align-items: center;
gap: 0.75rem;
font-size: 0.88rem;
}
#psa-app .psa-bar-lbl { width: 65px; font-weight: 700; color: #555; }
#psa-app .psa-bar-track {
flex: 1;
height: 18px;
background: #dde8f5;
border-radius: 9px;
overflow: hidden;
}
#psa-app .psa-bar-fill {
height: 100%;
border-radius: 9px;
transition: width 0.7s ease;
}
#psa-app .psa-bar-val { width: 60px; text-align: right; color: #333; font-weight: 700; }
#psa-app .psa-cta {
background: linear-gradient(135deg, #fff8e1 0%, #fff3cd 100%);
border: 1.5px solid #ffc107;
border-radius: 10px;
padding: 1.1rem 1.4rem;
margin-top: 1.5rem;
font-size: 0.93rem;
color: #333;
line-height: 1.7;
}
#psa-app .psa-cta strong {
display: block;
font-size: 1rem;
color: #0f3460;
margin-bottom: 0.4rem;
}
#psa-app .psa-cta a {
color: #0f3460;
font-weight: 700;
}
</style>

<div class="psa-intro">
HTMLやCSS、画像など各アセットのサイズを入力し、接続速度を選ぶだけで読み込み時間の推定値・パフォーマンススコア・改善アドバイスを即座に確認できます。最適化前後の比較機能も搭載しています。
</div>

<h2>ページアセットのサイズ入力</h2>

<div class="psa-grid">
<div class="psa-field">
<label for="psa-html">HTML（KB）</label>
<input type="number" id="psa-html" min="0" step="0.1" value="30" placeholder="例: 30">
</div>
<div class="psa-field">
<label for="psa-css">CSS（KB）</label>
<input type="number" id="psa-css" min="0" step="0.1" value="80" placeholder="例: 80">
</div>
<div class="psa-field">
<label for="psa-js">JavaScript（KB）</label>
<input type="number" id="psa-js" min="0" step="0.1" value="200" placeholder="例: 200">
</div>
<div class="psa-field">
<label for="psa-img">画像（KB）</label>
<input type="number" id="psa-img" min="0" step="1" value="500" placeholder="例: 500">
</div>
<div class="psa-field">
<label for="psa-font">フォント（KB）</label>
<input type="number" id="psa-font" min="0" step="0.1" value="60" placeholder="例: 60">
</div>
<div class="psa-field">
<label for="psa-other">その他（KB）</label>
<input type="number" id="psa-other" min="0" step="0.1" value="20" placeholder="例: 20">
</div>
</div>

<div class="psa-speed-row">
<div class="psa-field">
<label for="psa-speed">接続速度</label>
<select id="psa-speed">
<option value="0.375">3G 低速（3 Mbps）</option>
<option value="1.25" selected>3G 高速 / 4G（10 Mbps）</option>
<option value="6.25">Wi-Fi（50 Mbps）</option>
<option value="25">光回線（200 Mbps）</option>
</select>
</div>
<button class="psa-btn" onclick="psaAnalyze()">分析する</button>
<button class="psa-reset-btn" onclick="psaReset()">リセット</button>
</div>

<div class="psa-results" id="psa-results">

<div class="psa-summary-cards">
<div class="psa-card">
<div class="psa-card-label">ページ合計サイズ</div>
<div class="psa-card-value" id="psa-total-weight">—</div>
<div class="psa-card-sub" id="psa-weight-sub"></div>
</div>
<div class="psa-card">
<div class="psa-card-label">推定読み込み時間</div>
<div class="psa-card-value" id="psa-load-time">—</div>
<div class="psa-card-sub" id="psa-speed-label"></div>
</div>
<div class="psa-card">
<div class="psa-card-label">最大アセット</div>
<div class="psa-card-value" id="psa-largest">—</div>
<div class="psa-card-sub" id="psa-largest-type"></div>
</div>
</div>

<div class="psa-score-wrap">
<div class="psa-score-circle" id="psa-score-circle">
<span class="psa-score-num" id="psa-score-num">—</span>
</div>
<div class="psa-score-info">
<div class="psa-score-grade" id="psa-score-grade"></div>
<div class="psa-score-desc" id="psa-score-desc"></div>
</div>
</div>

<div class="psa-chart-wrap">
<canvas id="psa-chart" height="220"></canvas>
</div>

<div class="psa-recs" id="psa-recs">
<h3>最適化アドバイス</h3>
<div id="psa-recs-list"></div>
</div>

<div class="psa-compare">
<h3>最適化前後の比較</h3>
<p class="psa-compare-note">最適化後の想定サイズを入力すると、読み込み時間がどれだけ改善するかを可視化できます。</p>
<div class="psa-opt-grid">
<div>
<div class="psa-opt-label">最適化後 HTML（KB）</div>
<input type="number" class="psa-opt-input" id="psa-opt-html" min="0" step="0.1" placeholder="HTML">
</div>
<div>
<div class="psa-opt-label">最適化後 CSS（KB）</div>
<input type="number" class="psa-opt-input" id="psa-opt-css" min="0" step="0.1" placeholder="CSS">
</div>
<div>
<div class="psa-opt-label">最適化後 JS（KB）</div>
<input type="number" class="psa-opt-input" id="psa-opt-js" min="0" step="0.1" placeholder="JS">
</div>
<div>
<div class="psa-opt-label">最適化後 画像（KB）</div>
<input type="number" class="psa-opt-input" id="psa-opt-img" min="0" step="1" placeholder="画像">
</div>
<div>
<div class="psa-opt-label">最適化後 フォント（KB）</div>
<input type="number" class="psa-opt-input" id="psa-opt-font" min="0" step="0.1" placeholder="フォント">
</div>
<div>
<div class="psa-opt-label">最適化後 その他（KB）</div>
<input type="number" class="psa-opt-input" id="psa-opt-other" min="0" step="0.1" placeholder="その他">
</div>
</div>
<button class="psa-btn" onclick="psaCompare()" style="margin-top:0.25rem;">比較する</button>
<div class="psa-compare-result" id="psa-compare-result">
<strong id="psa-compare-summary"></strong>
<div class="psa-compare-bars" id="psa-compare-bars"></div>
</div>
</div>

<blockquote class="psa-cta">
<strong>サイト運営を効率化</strong>
ページ表示速度の改善と同様に、事業管理の効率化も重要です。<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で事業管理を自動化</a>して、本業に集中しましょう。
</blockquote>

</div>

<script>
(function() {
var SPEEDS = {
"0.375": "3G 低速（3 Mbps）",
"1.25":  "3G 高速 / 4G（10 Mbps）",
"6.25":  "Wi-Fi（50 Mbps）",
"25":    "光回線（200 Mbps）"
};

var COLORS = {
html:  "#4c9be8",
css:   "#f9a825",
js:    "#e53935",
img:   "#43a047",
font:  "#8e24aa",
other: "#6d4c41"
};

function getVal(id) {
var v = parseFloat(document.getElementById(id).value);
return isNaN(v) || v < 0 ? 0 : v;
}

function formatKB(kb) {
if (kb >= 1024) return (kb / 1024).toFixed(2) + " MB";
return kb.toFixed(1) + " KB";
}

function formatTime(seconds) {
if (seconds < 1) return (seconds * 1000).toFixed(0) + " ms";
return seconds.toFixed(2) + " 秒";
}

function calcScore(totalKB) {
if (totalKB <= 100)  return 100;
if (totalKB <= 300)  return Math.round(100 - ((totalKB - 100) / 200) * 10);
if (totalKB <= 500)  return Math.round(90 - ((totalKB - 300) / 200) * 10);
if (totalKB <= 1000) return Math.round(80 - ((totalKB - 500) / 500) * 20);
if (totalKB <= 2000) return Math.round(60 - ((totalKB - 1000) / 1000) * 20);
if (totalKB <= 3000) return Math.round(40 - ((totalKB - 2000) / 1000) * 15);
return Math.max(5, Math.round(25 - ((totalKB - 3000) / 1000) * 5));
}

function gradeInfo(score) {
if (score >= 90) return { grade: "優秀", color: "#2e7d32", bg: "#2e7d32", desc: "ページは非常に軽量です。あらゆる回線環境のユーザーに快適な体験を提供できています。" };
if (score >= 75) return { grade: "良好", color: "#388e3c", bg: "#388e3c", desc: "ページ容量は概ね適切です。わずかな改善で「優秀」評価を達成できます。" };
if (score >= 55) return { grade: "要改善", color: "#f57c00", bg: "#f57c00", desc: "ページが推奨値より重くなっています。画像とJavaScriptを中心に削減しましょう。" };
if (score >= 35) return { grade: "不良", color: "#d32f2f", bg: "#c62828", desc: "ページ容量がベストプラクティスを大幅に超えています。モバイル回線ではかなり遅くなります。" };
return { grade: "深刻", color: "#b71c1c", bg: "#b71c1c", desc: "ページが非常に重い状態です。全アセットにわたって大幅な最適化が必要です。" };
}

function buildRecs(html, css, js, img, font, other) {
var recs = [];
if (img > 500)  recs.push({ icon: "🖼️", text: "画像が " + formatKB(img) + " あります。WebP/AVIFへの変換・遅延読み込み（loading=\"lazy\"）・srcsetによるレスポンシブ配信を実施し、400 KB以下を目指しましょう。" });
if (js > 300)   recs.push({ icon: "⚡", text: "JavaScriptが " + formatKB(js) + " あります。ツリーシェイキング・ルート単位のコード分割・非同期読み込み（defer/async）で200 KB以下を目標にしてください。" });
if (css > 100)  recs.push({ icon: "🎨", text: "CSSが " + formatKB(css) + " あります。PurgeCSSで未使用ルールを削除し、クリティカルCSSのインライン化と圧縮で50 KB以下を目指しましょう。" });
if (font > 80)  recs.push({ icon: "🔤", text: "フォントが " + formatKB(font) + " あります。使用文字のサブセット化・font-display: swap の設定・フォント種類を2つ以内に絞ることで大幅に削減できます。" });
if (html > 50)  recs.push({ icon: "📄", text: "HTMLが " + formatKB(html) + " あります。サーバー側でgzip/Brotli圧縮を有効にすると転送量を70〜90%削減できます。" });
if (other > 30) recs.push({ icon: "📦", text: "その他アセットが " + formatKB(other) + " あります。サードパーティスクリプト・トラッキングピクセルを監査し、不要なものを削除または遅延読み込みしましょう。" });
if (recs.length === 0) recs.push({ icon: "✅", text: "全アセットがベストプラクティスの範囲内です。HTTP/2・CDN・適切なキャッシュヘッダーを設定してさらなる高速化を狙いましょう。" });
recs.push({ icon: "🌐", text: "CDNを導入してエッジノードから静的アセットを配信すると、世界中のユーザーへの往復遅延を大幅に削減できます。" });
recs.push({ icon: "🗜️", text: "サーバーでBrotli圧縮を有効にすると、gzipより15〜25%高い圧縮率でテキストアセットを配信できます。" });
return recs;
}

function drawChart(labels, values, colors) {
var canvas = document.getElementById("psa-chart");
var ctx = canvas.getContext("2d");
var dpr = window.devicePixelRatio || 1;
var W = canvas.parentElement.clientWidth - 40;
var H = 200;
canvas.width = W * dpr;
canvas.height = H * dpr;
canvas.style.width = W + "px";
canvas.style.height = H + "px";
ctx.scale(dpr, dpr);
ctx.clearRect(0, 0, W, H);

var pad = { top: 20, right: 20, bottom: 50, left: 60 };
var chartW = W - pad.left - pad.right;
var chartH = H - pad.top - pad.bottom;
var n = labels.length;
var barW = Math.min(50, (chartW / n) * 0.6);
var gap = chartW / n;
var maxVal = Math.max.apply(null, values.concat([1]));

ctx.strokeStyle = "#e8ecf5";
ctx.lineWidth = 1;
for (var g = 0; g <= 4; g++) {
var gy = pad.top + (chartH / 4) * g;
ctx.beginPath();
ctx.moveTo(pad.left, gy);
ctx.lineTo(pad.left + chartW, gy);
ctx.stroke();
var lbl = formatKB(maxVal * (1 - g / 4));
ctx.fillStyle = "#999";
ctx.font = "11px sans-serif";
ctx.textAlign = "right";
ctx.fillText(lbl, pad.left - 6, gy + 4);
}

for (var i = 0; i < n; i++) {
var bh = values[i] > 0 ? (values[i] / maxVal) * chartH : 0;
var bx = pad.left + gap * i + (gap - barW) / 2;
var by = pad.top + chartH - bh;

ctx.shadowColor = "rgba(0,0,0,0.08)";
ctx.shadowBlur = 6;
ctx.shadowOffsetY = 3;

ctx.fillStyle = colors[i];
ctx.beginPath();
if (ctx.roundRect) {
ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]);
} else {
ctx.rect(bx, by, barW, bh);
}
ctx.fill();

ctx.shadowColor = "transparent";
ctx.shadowBlur = 0;
ctx.shadowOffsetY = 0;

if (values[i] > 0) {
ctx.fillStyle = "#333";
ctx.font = "bold 11px sans-serif";
ctx.textAlign = "center";
ctx.fillText(formatKB(values[i]), bx + barW / 2, by - 5);
}

ctx.fillStyle = "#555";
ctx.font = "12px sans-serif";
ctx.textAlign = "center";
ctx.fillText(labels[i], bx + barW / 2, pad.top + chartH + 18);
}

ctx.strokeStyle = "#c8d0e7";
ctx.lineWidth = 1.5;
ctx.beginPath();
ctx.moveTo(pad.left, pad.top);
ctx.lineTo(pad.left, pad.top + chartH);
ctx.stroke();
}

window.psaAnalyze = function() {
var html  = getVal("psa-html");
var css   = getVal("psa-css");
var js    = getVal("psa-js");
var img   = getVal("psa-img");
var font  = getVal("psa-font");
var other = getVal("psa-other");
var speed = parseFloat(document.getElementById("psa-speed").value);
var speedKey = document.getElementById("psa-speed").value;

var total = html + css + js + img + font + other;
var loadSec = total / (speed * 1024);

var vals = [html, css, js, img, font, other];
var names = ["HTML","CSS","JS","画像","フォント","その他"];
var largest = Math.max.apply(null, vals);
var largestName = names[vals.indexOf(largest)];

document.getElementById("psa-total-weight").textContent = formatKB(total);
document.getElementById("psa-weight-sub").textContent = total >= 1024 ? ((total/1024).toFixed(2) + " MB") : "6種類のアセット合計";
document.getElementById("psa-load-time").textContent = formatTime(loadSec);
document.getElementById("psa-speed-label").textContent = SPEEDS[speedKey] || "";
document.getElementById("psa-largest").textContent = formatKB(largest);
document.getElementById("psa-largest-type").textContent = largestName;

var score = calcScore(total);
var info  = gradeInfo(score);
document.getElementById("psa-score-num").textContent = score;
document.getElementById("psa-score-circle").style.background = info.bg;
document.getElementById("psa-score-grade").textContent = info.grade;
document.getElementById("psa-score-grade").style.color = info.color;
document.getElementById("psa-score-desc").textContent = info.desc;

var recs = buildRecs(html, css, js, img, font, other);
var recsHtml = recs.map(function(r) {
return '<div class="psa-rec-item"><span class="psa-rec-icon">' + r.icon + '</span><span>' + r.text + '</span></div>';
}).join("");
document.getElementById("psa-recs-list").innerHTML = recsHtml;

var labels = ["HTML","CSS","JS","画像","フォント","その他"];
var values = [html, css, js, img, font, other];
var cols   = [COLORS.html, COLORS.css, COLORS.js, COLORS.img, COLORS.font, COLORS.other];
var filtered  = labels.filter(function(_,i){ return values[i] > 0; });
var filteredV = values.filter(function(v){ return v > 0; });
var filteredC = cols.filter(function(_,i){ return values[i] > 0; });

document.getElementById("psa-results").style.display = "block";
document.getElementById("psa-compare-result").style.display = "none";

var suggestions = [
Math.max(html * 0.7, 10).toFixed(1),
Math.max(css * 0.5, 20).toFixed(1),
Math.max(js * 0.6, 50).toFixed(1),
Math.max(img * 0.5, 50).toFixed(0),
Math.max(font * 0.7, 20).toFixed(1),
Math.max(other * 0.6, 5).toFixed(1)
];
["psa-opt-html","psa-opt-css","psa-opt-js","psa-opt-img","psa-opt-font","psa-opt-other"].forEach(function(id, i) {
document.getElementById(id).value = suggestions[i];
});

setTimeout(function() { drawChart(filtered, filteredV, filteredC); }, 50);
document.getElementById("psa-results").scrollIntoView({ behavior: "smooth", block: "nearest" });
};

window.psaCompare = function() {
var speed = parseFloat(document.getElementById("psa-speed").value);
var orig = ["psa-html","psa-css","psa-js","psa-img","psa-font","psa-other"].map(getVal);
var opts = ["psa-opt-html","psa-opt-css","psa-opt-js","psa-opt-img","psa-opt-font","psa-opt-other"].map(getVal);
var totalOrig = orig.reduce(function(a,b){return a+b;},0);
var totalOpt  = opts.reduce(function(a,b){return a+b;},0);
var timeOrig  = totalOrig / (speed * 1024);
var timeOpt   = totalOpt  / (speed * 1024);
var saved     = totalOrig - totalOpt;
var pct       = totalOrig > 0 ? ((saved / totalOrig) * 100).toFixed(1) : 0;

document.getElementById("psa-compare-summary").textContent =
"削減量: " + formatKB(saved) + "（" + pct + "%削減）— 読み込み時間: " + formatTime(timeOrig) + " → " + formatTime(timeOpt);

var maxT = Math.max(timeOrig, timeOpt, 0.001);
var barsHtml = [
{ lbl: "最適化前", val: timeOrig, color: "#e53935" },
{ lbl: "最適化後", val: timeOpt,  color: "#43a047" }
].map(function(b) {
var pct = (b.val / maxT * 100).toFixed(1);
return '<div class="psa-bar-row">' +
'<span class="psa-bar-lbl">' + b.lbl + '</span>' +
'<div class="psa-bar-track"><div class="psa-bar-fill" style="width:' + pct + '%;background:' + b.color + '"></div></div>' +
'<span class="psa-bar-val">' + formatTime(b.val) + '</span>' +
'</div>';
}).join("");

document.getElementById("psa-compare-bars").innerHTML = barsHtml;
document.getElementById("psa-compare-result").style.display = "block";
};

window.psaReset = function() {
["psa-html","psa-css","psa-js","psa-img","psa-font","psa-other"].forEach(function(id, i) {
document.getElementById(id).value = ["30","80","200","500","60","20"][i];
});
document.getElementById("psa-speed").value = "1.25";
document.getElementById("psa-results").style.display = "none";
};
})();
</script>

</div>
