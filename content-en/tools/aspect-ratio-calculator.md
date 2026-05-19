---
title: "Aspect Ratio Calculator"
date: 2025-05-16
description: "Free online aspect ratio calculator. Convert between dimensions, lock ratios, and get pixel-perfect resolutions for video, images, and responsive design."
categories: ["Free Tools"]
slug: "aspect-ratio-calculator"
ShowToc: false
cover:
  image: "/images/covers/aspect-ratio-calculator.png"
  alt: "Aspect Ratio Calculator"
---

<div id="ar-app">

<style>
#ar-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 860px;
margin: 0 auto;
padding: 0 0 2rem;
color: #1e293b;
}
#ar-app * { box-sizing: border-box; }

#ar-app h2.ar-section-title {
font-size: 1rem;
font-weight: 700;
color: #475569;
text-transform: uppercase;
letter-spacing: 0.07em;
margin: 28px 0 12px;
border-bottom: 2px solid #e2e8f0;
padding-bottom: 6px;
}

#ar-app .ar-card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 20px 24px;
margin-bottom: 20px;
}

#ar-app .ar-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 600px) {
#ar-app .ar-grid { grid-template-columns: 1fr; }
}

#ar-app label {
display: block;
font-size: 13px;
font-weight: 600;
color: #64748b;
margin-bottom: 5px;
}

#ar-app input[type="number"] {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 15px;
color: #1e293b;
background: #fff;
transition: border-color 0.2s;
-moz-appearance: textfield;
}
#ar-app input[type="number"]::-webkit-outer-spin-button,
#ar-app input[type="number"]::-webkit-inner-spin-button { -webkit-appearance: none; margin: 0; }
#ar-app input[type="number"]:focus {
outline: none;
border-color: #6366f1;
}

#ar-app .ar-ratio-display {
display: flex;
align-items: center;
justify-content: center;
background: linear-gradient(135deg, #6366f1 0%, #818cf8 100%);
color: #fff;
border-radius: 12px;
padding: 18px 10px;
text-align: center;
flex-direction: column;
}
#ar-app .ar-ratio-display .ar-ratio-big {
font-size: 2rem;
font-weight: 800;
letter-spacing: -0.02em;
line-height: 1;
}
#ar-app .ar-ratio-display .ar-ratio-label {
font-size: 12px;
opacity: 0.8;
margin-top: 4px;
text-transform: uppercase;
letter-spacing: 0.08em;
}

#ar-app .ar-lock-row {
display: flex;
align-items: center;
gap: 10px;
margin-top: 14px;
}
#ar-app .ar-lock-btn {
display: flex;
align-items: center;
gap: 6px;
padding: 7px 14px;
border-radius: 7px;
border: 1.5px solid #6366f1;
background: #fff;
color: #6366f1;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.2s;
}
#ar-app .ar-lock-btn.locked {
background: #6366f1;
color: #fff;
}
#ar-app .ar-lock-btn:hover { opacity: 0.85; }
#ar-app .ar-lock-status {
font-size: 13px;
color: #64748b;
}

#ar-app .ar-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 4px;
}
#ar-app .ar-preset-btn {
padding: 6px 13px;
border-radius: 6px;
border: 1.5px solid #cbd5e1;
background: #fff;
color: #334155;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#ar-app .ar-preset-btn:hover,
#ar-app .ar-preset-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}

#ar-app .ar-res-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 4px;
}
#ar-app .ar-res-btn {
padding: 6px 12px;
border-radius: 6px;
border: 1.5px solid #cbd5e1;
background: #fff;
color: #334155;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#ar-app .ar-res-btn:hover {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}

#ar-app .ar-info-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 12px;
margin-top: 4px;
}
@media (max-width: 540px) {
#ar-app .ar-info-grid { grid-template-columns: repeat(2, 1fr); }
}
#ar-app .ar-info-box {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 12px 14px;
text-align: center;
}
#ar-app .ar-info-box .ar-info-val {
font-size: 1.15rem;
font-weight: 700;
color: #1e293b;
}
#ar-app .ar-info-box .ar-info-key {
font-size: 11px;
color: #94a3b8;
margin-top: 2px;
text-transform: uppercase;
letter-spacing: 0.05em;
}

/* Visual preview */
#ar-app .ar-preview-wrap {
display: flex;
align-items: center;
justify-content: center;
min-height: 180px;
background: repeating-conic-gradient(#e2e8f0 0% 25%, #f8fafc 0% 50%) 0 0 / 20px 20px;
border-radius: 10px;
padding: 20px;
overflow: hidden;
}
#ar-app .ar-preview-rect {
background: linear-gradient(135deg, #6366f1 0%, #818cf8 60%, #a5b4fc 100%);
border-radius: 6px;
display: flex;
align-items: center;
justify-content: center;
color: #fff;
font-size: 13px;
font-weight: 600;
transition: all 0.3s ease;
min-width: 40px;
min-height: 30px;
box-shadow: 0 4px 20px rgba(99,102,241,0.35);
}

/* Code output */
#ar-app .ar-code-block {
background: #1e293b;
color: #a5b4fc;
border-radius: 10px;
padding: 16px 18px;
font-family: 'Fira Mono', 'Consolas', monospace;
font-size: 13px;
line-height: 1.7;
overflow-x: auto;
white-space: pre;
position: relative;
}
#ar-app .ar-copy-btn {
position: absolute;
top: 10px;
right: 12px;
padding: 4px 11px;
background: #334155;
color: #cbd5e1;
border: none;
border-radius: 5px;
font-size: 12px;
cursor: pointer;
transition: background 0.2s;
}
#ar-app .ar-copy-btn:hover { background: #475569; }
#ar-app .ar-copy-btn.copied { background: #059669; color: #fff; }

#ar-app .ar-tabs {
display: flex;
gap: 4px;
margin-bottom: 10px;
}
#ar-app .ar-tab {
padding: 6px 14px;
border-radius: 6px;
border: 1.5px solid #cbd5e1;
background: #fff;
color: #64748b;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#ar-app .ar-tab.active {
border-color: #6366f1;
background: #6366f1;
color: #fff;
}
</style>

<h2 class="ar-section-title">Dimensions &amp; Ratio</h2>
<div class="ar-card">
<div class="ar-grid">
<div>
<div class="ar-grid" style="gap:10px;">
<div>
<label for="ar-width">Width (px)</label>
<input type="number" id="ar-width" value="1920" min="1" max="99999">
</div>
<div>
<label for="ar-height">Height (px)</label>
<input type="number" id="ar-height" value="1080" min="1" max="99999">
</div>
</div>
<div class="ar-lock-row">
<button class="ar-lock-btn" id="ar-lock-btn" onclick="arToggleLock()">
<span id="ar-lock-icon">&#128275;</span> Lock Ratio
</button>
<span class="ar-lock-status" id="ar-lock-status">Ratio unlocked</span>
</div>
</div>
<div class="ar-ratio-display">
<div class="ar-ratio-big" id="ar-ratio-out">16:9</div>
<div class="ar-ratio-label">Aspect Ratio</div>
</div>
</div>
</div>

<h2 class="ar-section-title">Common Ratio Presets</h2>
<div class="ar-card">
<div class="ar-presets" id="ar-presets">
<button class="ar-preset-btn" onclick="arSetRatio(16,9)">16:9</button>
<button class="ar-preset-btn" onclick="arSetRatio(4,3)">4:3</button>
<button class="ar-preset-btn" onclick="arSetRatio(1,1)">1:1</button>
<button class="ar-preset-btn" onclick="arSetRatio(21,9)">21:9</button>
<button class="ar-preset-btn" onclick="arSetRatio(9,16)">9:16</button>
<button class="ar-preset-btn" onclick="arSetRatio(3,2)">3:2</button>
<button class="ar-preset-btn" onclick="arSetRatio(2,3)">2:3</button>
<button class="ar-preset-btn" onclick="arSetRatio(5,4)">5:4</button>
<button class="ar-preset-btn" onclick="arSetRatio(18,9)">18:9</button>
</div>
</div>

<h2 class="ar-section-title">Resolution Presets</h2>
<div class="ar-card">
<div class="ar-res-presets">
<button class="ar-res-btn" onclick="arSetRes(1920,1080)">1080p (FHD)</button>
<button class="ar-res-btn" onclick="arSetRes(1280,720)">720p (HD)</button>
<button class="ar-res-btn" onclick="arSetRes(3840,2160)">4K (UHD)</button>
<button class="ar-res-btn" onclick="arSetRes(7680,4320)">8K</button>
<button class="ar-res-btn" onclick="arSetRes(1080,1080)">Instagram Square</button>
<button class="ar-res-btn" onclick="arSetRes(1080,1350)">Instagram Portrait</button>
<button class="ar-res-btn" onclick="arSetRes(1200,675)">Twitter/X Card</button>
<button class="ar-res-btn" onclick="arSetRes(1280,720)">YouTube Thumbnail</button>
<button class="ar-res-btn" onclick="arSetRes(2560,1440)">1440p (QHD)</button>
<button class="ar-res-btn" onclick="arSetRes(2048,1152)">2K</button>
</div>
</div>

<h2 class="ar-section-title">Visual Preview</h2>
<div class="ar-card" style="padding:16px;">
<div class="ar-preview-wrap" id="ar-preview-wrap">
<div class="ar-preview-rect" id="ar-preview-rect">16:9</div>
</div>
</div>

<h2 class="ar-section-title">Info</h2>
<div class="ar-card" style="padding:16px 20px;">
<div class="ar-info-grid">
<div class="ar-info-box">
<div class="ar-info-val" id="ar-pixels">2,073,600</div>
<div class="ar-info-key">Total Pixels</div>
</div>
<div class="ar-info-box">
<div class="ar-info-val" id="ar-mp">2.07 MP</div>
<div class="ar-info-key">Megapixels</div>
</div>
<div class="ar-info-box">
<div class="ar-info-val" id="ar-decimal">1.778</div>
<div class="ar-info-key">Decimal Ratio</div>
</div>
</div>
</div>

<h2 class="ar-section-title">Code Snippets</h2>
<div class="ar-card" style="padding:16px 20px;">
<div class="ar-tabs">
<button class="ar-tab active" id="ar-tab-css" onclick="arShowTab('css')">CSS</button>
<button class="ar-tab" id="ar-tab-html" onclick="arShowTab('html')">HTML</button>
<button class="ar-tab" id="ar-tab-tailwind" onclick="arShowTab('tailwind')">Tailwind</button>
</div>
<div style="position:relative;">
<pre class="ar-code-block" id="ar-code-out"></pre>
<button class="ar-copy-btn" id="ar-copy-btn" onclick="arCopyCode()">Copy</button>
</div>
</div>

<script>
(function() {
var locked = false;
var lockedRatioW = 16, lockedRatioH = 9;
var currentTab = 'css';

function gcd(a, b) {
a = Math.round(a); b = Math.round(b);
while (b) { var t = b; b = a % b; a = t; }
return a;
}

function getW() { return parseFloat(document.getElementById('ar-width').value) || 1; }
function getH() { return parseFloat(document.getElementById('ar-height').value) || 1; }

function update() {
var w = getW(), h = getH();
var g = gcd(w, h);
var rw = w / g, rh = h / g;
var ratioStr = rw + ':' + rh;
document.getElementById('ar-ratio-out').textContent = ratioStr;
document.getElementById('ar-pixels').textContent = (w * h).toLocaleString();
var mp = (w * h) / 1000000;
document.getElementById('ar-mp').textContent = mp.toFixed(2) + ' MP';
document.getElementById('ar-decimal').textContent = (w / h).toFixed(3);
updatePreview(w, h, ratioStr);
updateCode(w, h, rw, rh);
highlightActivePreset(rw, rh);
}

function updatePreview(w, h, ratioStr) {
var wrap = document.getElementById('ar-preview-wrap');
var rect = document.getElementById('ar-preview-rect');
var maxW = wrap.clientWidth - 40 || 300;
var maxH = 180;
var ratio = w / h;
var pw, ph;
if (ratio >= 1) {
pw = Math.min(maxW, maxH * ratio);
ph = pw / ratio;
if (ph > maxH) { ph = maxH; pw = ph * ratio; }
} else {
ph = Math.min(maxH, maxW / ratio);
pw = ph * ratio;
if (pw > maxW) { pw = maxW; ph = pw / ratio; }
}
rect.style.width = Math.round(pw) + 'px';
rect.style.height = Math.round(ph) + 'px';
rect.textContent = ratioStr;
}

function updateCode(w, h, rw, rh) {
var decimalRatio = (w / h).toFixed(4);
var codes = {
css: '/* Modern CSS aspect-ratio */\n.element {\n  width: 100%;\n  aspect-ratio: ' + rw + ' / ' + rh + ';\n}\n\n/* Padding-bottom hack (legacy) */\n.wrapper {\n  position: relative;\n  padding-bottom: ' + ((h / w) * 100).toFixed(4) + '%;\n  height: 0;\n  overflow: hidden;\n}\n.wrapper > * {\n  position: absolute;\n  top: 0; left: 0;\n  width: 100%; height: 100%;\n}',
html: '<div class="ratio-box" style="\n  width: ' + w + 'px;\n  height: ' + h + 'px;\n  aspect-ratio: ' + rw + ' / ' + rh + ';\n">\n  <!-- ' + w + ' x ' + h + ' (' + rw + ':' + rh + ') -->\n</div>',
tailwind: '<!-- Tailwind CSS -->\n<!-- Note: use [aspect-ratio:' + rw + '/' + rh + '] for custom ratios -->\n<div class="w-full [aspect-ratio:' + rw + '/' + rh + ']">\n  <!-- ' + w + ' x ' + h + ' -->\n</div>\n\n<!-- Or use inline style -->\n<div style="aspect-ratio:' + rw + '/' + rh + '" class="w-full">\n  <!-- content -->\n</div>'
};
document.getElementById('ar-code-out').textContent = codes[currentTab];
}

function highlightActivePreset(rw, rh) {
var btns = document.querySelectorAll('#ar-app .ar-preset-btn');
btns.forEach(function(btn) {
btn.classList.remove('active');
});
var presets = [[16,9],[4,3],[1,1],[21,9],[9,16],[3,2],[2,3],[5,4],[18,9]];
presets.forEach(function(p, i) {
if (p[0] === rw && p[1] === rh) {
btns[i] && btns[i].classList.add('active');
}
});
}

window.arToggleLock = function() {
locked = !locked;
var w = getW(), h = getH();
if (locked) {
var g = gcd(w, h);
lockedRatioW = w / g;
lockedRatioH = h / g;
}
document.getElementById('ar-lock-btn').classList.toggle('locked', locked);
document.getElementById('ar-lock-icon').textContent = locked ? '\uD83D\uDD12' : '\uD83D\uDD13';
document.getElementById('ar-lock-status').textContent = locked
? 'Ratio locked: ' + lockedRatioW + ':' + lockedRatioH
: 'Ratio unlocked';
};

window.arSetRatio = function(rw, rh) {
var w = getW();
var newH = Math.round(w * rh / rw);
document.getElementById('ar-height').value = newH;
if (locked) { lockedRatioW = rw; lockedRatioH = rh; }
update();
};

window.arSetRes = function(w, h) {
document.getElementById('ar-width').value = w;
document.getElementById('ar-height').value = h;
if (locked) {
var g = gcd(w, h);
lockedRatioW = w / g;
lockedRatioH = h / g;
}
update();
};

window.arShowTab = function(tab) {
currentTab = tab;
['css','html','tailwind'].forEach(function(t) {
document.getElementById('ar-tab-' + t).classList.toggle('active', t === tab);
});
var w = getW(), h = getH();
var g = gcd(w, h);
updateCode(w, h, w/g, h/g);
document.getElementById('ar-copy-btn').textContent = 'Copy';
document.getElementById('ar-copy-btn').classList.remove('copied');
};

window.arCopyCode = function() {
var code = document.getElementById('ar-code-out').textContent;
navigator.clipboard.writeText(code).then(function() {
var btn = document.getElementById('ar-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 1800);
});
};

function onWidthChange() {
if (locked) {
var w = getW();
document.getElementById('ar-height').value = Math.round(w * lockedRatioH / lockedRatioW);
}
update();
}

function onHeightChange() {
if (locked) {
var h = getH();
document.getElementById('ar-width').value = Math.round(h * lockedRatioW / lockedRatioH);
}
update();
}

document.getElementById('ar-width').addEventListener('input', onWidthChange);
document.getElementById('ar-height').addEventListener('input', onHeightChange);

update();
})();
</script>

---

> Resize images → [Image Resizer](/tools/image-resizer/)
> Social media sizes → [Social Media Image Resizer](/tools/social-media-image-resizer/)

</div>
