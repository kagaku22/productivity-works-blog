---
title: "Page Size Analyzer - Estimate Load Time"
date: 2025-05-16
description: "Analyze your web page size and estimate load times across different connection speeds. Get a performance score and actionable optimization recommendations instantly."
categories: ["Free Tools"]
tags: ["Date & Time", "Calculator", "Free Tools"]
slug: "page-size-analyzer"
ShowToc: false
cover:
  image: "/images/covers/page-size-analyzer.png"
  alt: "Page Size Analyzer"
---

<div id="psa-app">

<style>
#psa-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
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
font-weight: 600;
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
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.04em;
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
line-height: 1.5;
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
line-height: 1.5;
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
font-weight: 600;
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
#psa-app .psa-bar-lbl { width: 60px; font-weight: 600; color: #555; }
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
display: flex;
align-items: center;
padding-right: 6px;
justify-content: flex-end;
}
#psa-app .psa-bar-val { width: 55px; text-align: right; color: #333; font-weight: 700; }
#psa-app .psa-related {
margin-top: 2rem;
padding-top: 1rem;
border-top: 2px solid #e0e5f0;
}
#psa-app .psa-related h3 {
font-size: 1rem;
font-weight: 700;
color: #16213e;
margin-bottom: 0.75rem;
}
#psa-app .psa-related ul {
list-style: none;
padding: 0;
margin: 0;
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
}
#psa-app .psa-related ul li a {
display: inline-block;
padding: 0.4rem 0.9rem;
background: #eef2ff;
border-radius: 20px;
color: #0f3460;
text-decoration: none;
font-size: 0.88rem;
font-weight: 600;
border: 1.5px solid #c8d0e7;
transition: background 0.2s;
}
#psa-app .psa-related ul li a:hover { background: #dde0f5; }
</style>

<div class="psa-intro">
Enter the size of each asset type on your web page, select your target connection speed, and instantly see your estimated load time, performance score, and tailored recommendations.
</div>

<h2>Page Asset Sizes</h2>

<div class="psa-grid">
<div class="psa-field">
<label for="psa-html">HTML (KB)</label>
<input type="number" id="psa-html" min="0" step="0.1" value="30" placeholder="e.g. 30">
</div>
<div class="psa-field">
<label for="psa-css">CSS (KB)</label>
<input type="number" id="psa-css" min="0" step="0.1" value="80" placeholder="e.g. 80">
</div>
<div class="psa-field">
<label for="psa-js">JavaScript (KB)</label>
<input type="number" id="psa-js" min="0" step="0.1" value="200" placeholder="e.g. 200">
</div>
<div class="psa-field">
<label for="psa-img">Images (KB)</label>
<input type="number" id="psa-img" min="0" step="1" value="500" placeholder="e.g. 500">
</div>
<div class="psa-field">
<label for="psa-font">Fonts (KB)</label>
<input type="number" id="psa-font" min="0" step="0.1" value="60" placeholder="e.g. 60">
</div>
<div class="psa-field">
<label for="psa-other">Other (KB)</label>
<input type="number" id="psa-other" min="0" step="0.1" value="20" placeholder="e.g. 20">
</div>
</div>

<div class="psa-speed-row">
<div class="psa-field">
<label for="psa-speed">Connection Speed</label>
<select id="psa-speed">
<option value="0.375">3G Slow (3 Mbps)</option>
<option value="1.25" selected>3G Fast / 4G (10 Mbps)</option>
<option value="6.25">WiFi (50 Mbps)</option>
<option value="25">Fiber (200 Mbps)</option>
</select>
</div>
<button class="psa-btn" onclick="psaAnalyze()">Analyze</button>
<button class="psa-reset-btn" onclick="psaReset()">Reset</button>
</div>

<div class="psa-results" id="psa-results">

<div class="psa-summary-cards">
<div class="psa-card">
<div class="psa-card-label">Total Page Weight</div>
<div class="psa-card-value" id="psa-total-weight">—</div>
<div class="psa-card-sub" id="psa-weight-sub"></div>
</div>
<div class="psa-card">
<div class="psa-card-label">Est. Load Time</div>
<div class="psa-card-value" id="psa-load-time">—</div>
<div class="psa-card-sub" id="psa-speed-label"></div>
</div>
<div class="psa-card">
<div class="psa-card-label">Largest Asset</div>
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
<h3>Optimization Recommendations</h3>
<div id="psa-recs-list"></div>
</div>

<div class="psa-compare">
<h3>Before / After Comparison</h3>
<p class="psa-compare-note">Enter optimized sizes to see how much you can improve load time.</p>
<div class="psa-opt-grid">
<div>
<div class="psa-opt-label">Optimized HTML (KB)</div>
<input type="number" class="psa-opt-input" id="psa-opt-html" min="0" step="0.1" placeholder="HTML">
</div>
<div>
<div class="psa-opt-label">Optimized CSS (KB)</div>
<input type="number" class="psa-opt-input" id="psa-opt-css" min="0" step="0.1" placeholder="CSS">
</div>
<div>
<div class="psa-opt-label">Optimized JS (KB)</div>
<input type="number" class="psa-opt-input" id="psa-opt-js" min="0" step="0.1" placeholder="JS">
</div>
<div>
<div class="psa-opt-label">Optimized Images (KB)</div>
<input type="number" class="psa-opt-input" id="psa-opt-img" min="0" step="1" placeholder="Images">
</div>
<div>
<div class="psa-opt-label">Optimized Fonts (KB)</div>
<input type="number" class="psa-opt-input" id="psa-opt-font" min="0" step="0.1" placeholder="Fonts">
</div>
<div>
<div class="psa-opt-label">Optimized Other (KB)</div>
<input type="number" class="psa-opt-input" id="psa-opt-other" min="0" step="0.1" placeholder="Other">
</div>
</div>
<button class="psa-btn" onclick="psaCompare()" style="margin-top:0.25rem;">Compare</button>
<div class="psa-compare-result" id="psa-compare-result">
<strong id="psa-compare-summary"></strong>
<div class="psa-compare-bars" id="psa-compare-bars"></div>
</div>
</div>

</div>

<script>
(function() {
var SPEEDS = {
"0.375": "3G Slow (3 Mbps)",
"1.25":  "3G Fast / 4G (10 Mbps)",
"6.25":  "WiFi (50 Mbps)",
"25":    "Fiber (200 Mbps)"
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
return seconds.toFixed(2) + " s";
}

function calcScore(totalKB) {
// Benchmarks: <500KB=90+, <1MB=70-89, <2MB=50-69, <3MB=30-49, >=3MB=<30
if (totalKB <= 100)  return 100;
if (totalKB <= 300)  return Math.round(100 - ((totalKB - 100) / 200) * 10);
if (totalKB <= 500)  return Math.round(90 - ((totalKB - 300) / 200) * 10);
if (totalKB <= 1000) return Math.round(80 - ((totalKB - 500) / 500) * 20);
if (totalKB <= 2000) return Math.round(60 - ((totalKB - 1000) / 1000) * 20);
if (totalKB <= 3000) return Math.round(40 - ((totalKB - 2000) / 1000) * 15);
return Math.max(5, Math.round(25 - ((totalKB - 3000) / 1000) * 5));
}

function gradeInfo(score) {
if (score >= 90) return { grade: "Excellent", color: "#2e7d32", bg: "#2e7d32", desc: "Your page is exceptionally lean. Users on all connection types will have a fast experience." };
if (score >= 75) return { grade: "Good", color: "#388e3c", bg: "#388e3c", desc: "Page weight is well-managed. Minor optimizations can push you into the excellent range." };
if (score >= 55) return { grade: "Needs Improvement", color: "#f57c00", bg: "#f57c00", desc: "The page is heavier than recommended. Focus on images and JavaScript to reduce size." };
if (score >= 35) return { grade: "Poor", color: "#d32f2f", bg: "#c62828", desc: "Page weight is significantly above best-practice thresholds. Users on mobile connections will experience slow loads." };
return { grade: "Critical", color: "#b71c1c", bg: "#b71c1c", desc: "Page weight is extremely high. Significant optimization is required across all asset types." };
}

function buildRecs(html, css, js, img, font, other) {
var recs = [];
if (img > 500)  recs.push({ icon: "🖼️", text: "Images are " + formatKB(img) + " — compress to WebP/AVIF, use lazy loading, and serve responsive images via srcset. Target under 400 KB." });
if (js > 300)   recs.push({ icon: "⚡", text: "JavaScript bundle is " + formatKB(js) + " — enable tree-shaking, code-split routes, and defer non-critical scripts. Target under 200 KB." });
if (css > 100)  recs.push({ icon: "🎨", text: "CSS is " + formatKB(css) + " — remove unused rules with PurgeCSS, minify, and inline critical CSS. Target under 50 KB." });
if (font > 80)  recs.push({ icon: "🔤", text: "Fonts are " + formatKB(font) + " — subset fonts to used characters, use font-display: swap, and limit to 2 font families." });
if (html > 50)  recs.push({ icon: "📄", text: "HTML is " + formatKB(html) + " — enable gzip/Brotli compression on the server. Typical HTML should compress to under 10 KB on the wire." });
if (other > 30) recs.push({ icon: "📦", text: "Other assets are " + formatKB(other) + " — audit third-party scripts, remove unused tracking pixels, and defer analytics." });
if (recs.length === 0) recs.push({ icon: "✅", text: "All asset types are within best-practice thresholds. Enable HTTP/2, use a CDN, and add cache headers for maximum performance." });
recs.push({ icon: "🌐", text: "Enable a CDN to serve static assets from edge nodes, reducing round-trip time for global users." });
recs.push({ icon: "🗜️", text: "Ensure Brotli compression is enabled on your server — it achieves 15–25% better compression than gzip for text assets." });
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

var pad = { top: 20, right: 20, bottom: 50, left: 55 };
var chartW = W - pad.left - pad.right;
var chartH = H - pad.top - pad.bottom;
var n = labels.length;
var barW = Math.min(50, (chartW / n) * 0.6);
var gap = chartW / n;
var maxVal = Math.max(...values, 1);

// Grid lines
ctx.strokeStyle = "#e8ecf5";
ctx.lineWidth = 1;
for (var g = 0; g <= 4; g++) {
var gy = pad.top + (chartH / 4) * g;
ctx.beginPath();
ctx.moveTo(pad.left, gy);
ctx.lineTo(pad.left + chartW, gy);
ctx.stroke();
var label = formatKB(maxVal * (1 - g / 4));
ctx.fillStyle = "#999";
ctx.font = "11px sans-serif";
ctx.textAlign = "right";
ctx.fillText(label, pad.left - 6, gy + 4);
}

// Bars
for (var i = 0; i < n; i++) {
var bh = values[i] > 0 ? (values[i] / maxVal) * chartH : 0;
var bx = pad.left + gap * i + (gap - barW) / 2;
var by = pad.top + chartH - bh;

// Shadow
ctx.shadowColor = "rgba(0,0,0,0.08)";
ctx.shadowBlur = 6;
ctx.shadowOffsetY = 3;

ctx.fillStyle = colors[i];
ctx.beginPath();
ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]);
ctx.fill();

ctx.shadowColor = "transparent";
ctx.shadowBlur = 0;
ctx.shadowOffsetY = 0;

// Value label
if (values[i] > 0) {
ctx.fillStyle = "#333";
ctx.font = "bold 11px sans-serif";
ctx.textAlign = "center";
ctx.fillText(formatKB(values[i]), bx + barW / 2, by - 5);
}

// X label
ctx.fillStyle = "#555";
ctx.font = "12px sans-serif";
ctx.textAlign = "center";
ctx.fillText(labels[i], bx + barW / 2, pad.top + chartH + 18);
}

// Y axis
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
var loadSec = total / (speed * 1024); // speed in MB/s -> KB/s

var largest = Math.max(html, css, js, img, font, other);
var largestName = ["HTML","CSS","JS","Images","Fonts","Other"][[html,css,js,img,font,other].indexOf(largest)];

document.getElementById("psa-total-weight").textContent = formatKB(total);
document.getElementById("psa-weight-sub").textContent = total >= 1000 ? ((total/1024).toFixed(2) + " MB") : "across 6 asset types";
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

var labels = ["HTML","CSS","JS","Images","Fonts","Other"];
var values = [html, css, js, img, font, other];
var cols   = [COLORS.html, COLORS.css, COLORS.js, COLORS.img, COLORS.font, COLORS.other];
var filtered = labels.filter(function(_,i){ return values[i] > 0; });
var filteredV = values.filter(function(v){ return v > 0; });
var filteredC = cols.filter(function(_,i){ return values[i] > 0; });

document.getElementById("psa-results").style.display = "block";
document.getElementById("psa-compare-result").style.display = "none";

// Pre-fill optimized fields with suggested targets
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
"Savings: " + formatKB(saved) + " (" + pct + "%) — load time " + formatTime(timeOrig) + " → " + formatTime(timeOpt);

var maxT = Math.max(timeOrig, timeOpt, 0.001);
var barsHtml = [
{ lbl: "Before", val: timeOrig, color: "#e53935" },
{ lbl: "After",  val: timeOpt,  color: "#43a047" }
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

---

## Related Tools

<div class="psa-related">
<h3>More Free Productivity Tools</h3>
<ul>
<li><a href="/tools/reading-time-calculator/">Reading Time Calculator</a></li>
<li><a href="/tools/word-counter/">Word Counter</a></li>
<li><a href="/tools/pomodoro-timer/">Pomodoro Timer</a></li>
<li><a href="/tools/roi-calculator/">ROI Calculator</a></li>
<li><a href="/tools/password-strength-meter/">Password Strength Checker</a></li>
<li><a href="/tools/unit-converter/">Unit Converter</a></li>
</ul>
</div>

</div>
