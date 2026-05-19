---
title: "Color Wheel Picker"
date: 2025-05-16
description: "Free online color wheel picker. Explore color harmonies — complementary, triadic, analogous, split-complementary — with real-time preview and CSS export."
categories: ["Free Tools"]
slug: "color-wheel-picker"
ShowToc: false
cover:
  image: "/images/covers/color-wheel-picker.png"
  alt: "Color Wheel Picker"
---

<div id="cw-app">
<style>
#cw-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #e2e8f0;
}
#cw-app * {
box-sizing: border-box;
}
#cw-app .cw-layout {
display: flex;
flex-wrap: wrap;
gap: 24px;
align-items: flex-start;
}
#cw-app .cw-left {
display: flex;
flex-direction: column;
align-items: center;
gap: 16px;
flex: 0 0 auto;
}
#cw-app .cw-right {
flex: 1 1 320px;
display: flex;
flex-direction: column;
gap: 16px;
}
#cw-app .cw-wheel-wrap {
position: relative;
width: 300px;
height: 300px;
}
#cw-app #cw-wheel {
border-radius: 50%;
cursor: crosshair;
display: block;
}
#cw-app .cw-brightness-wrap {
width: 300px;
display: flex;
flex-direction: column;
gap: 6px;
}
#cw-app .cw-brightness-label {
font-size: 12px;
color: #94a3b8;
letter-spacing: 0.05em;
text-transform: uppercase;
}
#cw-app #cw-brightness-canvas {
width: 300px;
height: 28px;
border-radius: 6px;
cursor: crosshair;
display: block;
}
#cw-app #cw-saturation-canvas {
width: 300px;
height: 28px;
border-radius: 6px;
cursor: crosshair;
display: block;
}
#cw-app .cw-harmony-buttons {
display: flex;
flex-wrap: wrap;
gap: 8px;
width: 300px;
}
#cw-app .cw-btn {
padding: 6px 12px;
border-radius: 6px;
border: 1px solid #475569;
background: #1e293b;
color: #cbd5e1;
font-size: 13px;
cursor: pointer;
transition: background 0.15s, border-color 0.15s, color 0.15s;
white-space: nowrap;
}
#cw-app .cw-btn:hover {
background: #334155;
color: #f1f5f9;
}
#cw-app .cw-btn.active {
background: #3b82f6;
border-color: #3b82f6;
color: #fff;
}
#cw-app .cw-section-title {
font-size: 13px;
font-weight: 600;
color: #94a3b8;
letter-spacing: 0.07em;
text-transform: uppercase;
margin-bottom: 2px;
}
#cw-app .cw-swatches {
display: flex;
flex-direction: column;
gap: 10px;
}
#cw-app .cw-swatch-row {
display: flex;
align-items: center;
gap: 12px;
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 10px 14px;
}
#cw-app .cw-swatch-box {
width: 48px;
height: 48px;
border-radius: 8px;
flex-shrink: 0;
border: 2px solid #475569;
}
#cw-app .cw-swatch-info {
display: flex;
flex-direction: column;
gap: 4px;
flex: 1;
}
#cw-app .cw-swatch-label {
font-size: 11px;
color: #64748b;
font-weight: 500;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#cw-app .cw-values {
display: flex;
flex-wrap: wrap;
gap: 6px;
}
#cw-app .cw-val-chip {
font-size: 12px;
font-family: "SFMono-Regular", Consolas, monospace;
background: #0f172a;
border: 1px solid #334155;
border-radius: 4px;
padding: 2px 8px;
color: #93c5fd;
cursor: pointer;
transition: background 0.12s, color 0.12s;
user-select: none;
}
#cw-app .cw-val-chip:hover {
background: #1d4ed8;
color: #fff;
border-color: #2563eb;
}
#cw-app .cw-val-chip.copied {
background: #16a34a;
color: #fff;
border-color: #16a34a;
}
#cw-app .cw-contrast-box {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 14px;
display: flex;
flex-direction: column;
gap: 8px;
}
#cw-app .cw-contrast-row {
display: flex;
align-items: center;
justify-content: space-between;
font-size: 13px;
flex-wrap: wrap;
gap: 6px;
}
#cw-app .cw-contrast-ratio {
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 18px;
font-weight: 700;
color: #f1f5f9;
}
#cw-app .cw-wcag-badge {
padding: 2px 10px;
border-radius: 20px;
font-size: 11px;
font-weight: 700;
letter-spacing: 0.05em;
}
#cw-app .badge-pass {
background: #14532d;
color: #4ade80;
border: 1px solid #16a34a;
}
#cw-app .badge-fail {
background: #450a0a;
color: #f87171;
border: 1px solid #dc2626;
}
#cw-app .badge-aa {
background: #1c3a6e;
color: #93c5fd;
border: 1px solid #2563eb;
}
#cw-app .cw-contrast-preview {
display: flex;
gap: 8px;
}
#cw-app .cw-cp-sample {
flex: 1;
border-radius: 6px;
padding: 8px 10px;
font-size: 13px;
font-weight: 600;
text-align: center;
border: 1px solid #334155;
}
#cw-app .cw-export-box {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 14px;
display: flex;
flex-direction: column;
gap: 8px;
}
#cw-app .cw-export-header {
display: flex;
align-items: center;
justify-content: space-between;
}
#cw-app #cw-css-output {
background: #0f172a;
color: #7dd3fc;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
border: 1px solid #334155;
border-radius: 6px;
padding: 10px;
resize: vertical;
min-height: 90px;
width: 100%;
white-space: pre;
overflow-x: auto;
}
#cw-app .cw-copy-css-btn {
padding: 6px 16px;
border-radius: 6px;
border: 1px solid #3b82f6;
background: #1d4ed8;
color: #fff;
font-size: 13px;
cursor: pointer;
transition: background 0.15s;
}
#cw-app .cw-copy-css-btn:hover {
background: #2563eb;
}
#cw-app .cw-copy-css-btn.copied {
background: #16a34a;
border-color: #16a34a;
}
#cw-app .cw-crosslinks {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 14px 18px;
font-size: 13px;
color: #94a3b8;
line-height: 1.8;
}
#cw-app .cw-crosslinks a {
color: #60a5fa;
text-decoration: none;
}
#cw-app .cw-crosslinks a:hover {
text-decoration: underline;
}
@media (max-width: 640px) {
#cw-app .cw-layout {
flex-direction: column;
align-items: center;
}
#cw-app .cw-right {
width: 100%;
}
#cw-app .cw-wheel-wrap,
#cw-app #cw-wheel,
#cw-app .cw-brightness-wrap,
#cw-app #cw-brightness-canvas,
#cw-app #cw-saturation-canvas,
#cw-app .cw-harmony-buttons {
width: 280px;
}
#cw-app .cw-wheel-wrap {
height: 280px;
}
#cw-app #cw-wheel {
width: 280px;
height: 280px;
}
}
</style>

<div class="cw-layout">

<!-- LEFT: Wheel + sliders + harmony buttons -->
<div class="cw-left">
<div class="cw-wheel-wrap">
<canvas id="cw-wheel" width="300" height="300"></canvas>
</div>

<div class="cw-brightness-wrap">
<div class="cw-brightness-label">Brightness</div>
<canvas id="cw-brightness-canvas" width="300" height="28"></canvas>
<div class="cw-brightness-label">Saturation</div>
<canvas id="cw-saturation-canvas" width="300" height="28"></canvas>
</div>

<div class="cw-harmony-buttons">
<button class="cw-btn active" data-mode="complementary">Complementary</button>
<button class="cw-btn" data-mode="analogous">Analogous</button>
<button class="cw-btn" data-mode="triadic">Triadic</button>
<button class="cw-btn" data-mode="split">Split-Comp</button>
<button class="cw-btn" data-mode="tetradic">Tetradic</button>
</div>
</div>

<!-- RIGHT: Swatches + contrast + export -->
<div class="cw-right">
<div class="cw-section-title">Color Palette</div>
<div class="cw-swatches" id="cw-swatches"></div>

<div class="cw-section-title">WCAG Contrast</div>
<div class="cw-contrast-box" id="cw-contrast-box">
<div class="cw-contrast-row">
<span style="color:#94a3b8;font-size:13px;">Base vs Harmony #1</span>
<span class="cw-contrast-ratio" id="cw-ratio-val">—</span>
<span class="cw-wcag-badge" id="cw-wcag-badge">—</span>
</div>
<div class="cw-contrast-preview">
<div class="cw-cp-sample" id="cw-cp-dark">Aa</div>
<div class="cw-cp-sample" id="cw-cp-light">Aa</div>
</div>
</div>

<div class="cw-section-title">CSS Export</div>
<div class="cw-export-box">
<div class="cw-export-header">
<span style="font-size:13px;color:#94a3b8;">CSS Custom Properties</span>
<button class="cw-copy-css-btn" id="cw-copy-css">Copy CSS</button>
</div>
<textarea id="cw-css-output" readonly></textarea>
</div>

<div class="cw-crosslinks">
Generate color palettes &rarr; <a href="/tools/color-palette-generator/">Color Palette Generator</a><br>
Check color contrast &rarr; <a href="/tools/color-contrast-checker/">Color Contrast Checker</a><br>
Simulate color blindness &rarr; <a href="/tools/color-blindness-simulator/">Color Blindness Simulator</a>
</div>
</div>
</div>

<script>
(function () {
"use strict";

// ── State ──────────────────────────────────────────────────────────────────
var state = {
hue: 200,
sat: 80,
bri: 55,
mode: "complementary",
};

// ── Canvas references ──────────────────────────────────────────────────────
var wheelCanvas = document.getElementById("cw-wheel");
var wCtx = wheelCanvas.getContext("2d");
var brCanvas = document.getElementById("cw-brightness-canvas");
var brCtx = brCanvas.getContext("2d");
var saCanvas = document.getElementById("cw-saturation-canvas");
var saCtx = saCanvas.getContext("2d");

var WHEEL_R = 150; // radius of wheel canvas

// ── Color math ────────────────────────────────────────────────────────────
function hslToRgb(h, s, l) {
s /= 100; l /= 100;
var c = (1 - Math.abs(2 * l - 1)) * s;
var x = c * (1 - Math.abs((h / 60) % 2 - 1));
var m = l - c / 2;
var r, g, b;
if (h < 60)       { r=c; g=x; b=0; }
else if (h < 120) { r=x; g=c; b=0; }
else if (h < 180) { r=0; g=c; b=x; }
else if (h < 240) { r=0; g=x; b=c; }
else if (h < 300) { r=x; g=0; b=c; }
else              { r=c; g=0; b=x; }
return [
Math.round((r + m) * 255),
Math.round((g + m) * 255),
Math.round((b + m) * 255),
];
}

function rgbToHex(r, g, b) {
return "#" + [r, g, b].map(function(v) {
return v.toString(16).padStart(2, "0");
}).join("");
}

function colorInfo(h, s, l) {
var rgb = hslToRgb(h, s, l);
return {
hsl: "hsl(" + Math.round(h) + ", " + Math.round(s) + "%, " + Math.round(l) + "%)",
hex: rgbToHex(rgb[0], rgb[1], rgb[2]),
rgb: "rgb(" + rgb[0] + ", " + rgb[1] + ", " + rgb[2] + ")",
r: rgb[0], g: rgb[1], b: rgb[2],
};
}

// Harmony offsets (degrees) for each mode
function harmonyOffsets(mode) {
switch (mode) {
case "complementary":    return [180];
case "analogous":        return [-30, 30];
case "triadic":          return [120, 240];
case "split":            return [150, 210];
case "tetradic":         return [90, 180, 270];
default:                 return [180];
}
}

function buildPalette() {
var offsets = harmonyOffsets(state.mode);
var colors = [colorInfo(state.hue, state.sat, state.bri)];
offsets.forEach(function(off) {
var h = ((state.hue + off) % 360 + 360) % 360;
colors.push(colorInfo(h, state.sat, state.bri));
});
return colors;
}

// ── Draw wheel ────────────────────────────────────────────────────────────
function drawWheel() {
var size = wheelCanvas.width;
var cx = size / 2, cy = size / 2, r = size / 2 - 2;
wCtx.clearRect(0, 0, size, size);

// HSL hue ring
for (var angle = 0; angle < 360; angle += 1) {
var startAngle = (angle - 1) * Math.PI / 180;
var endAngle   = (angle + 1) * Math.PI / 180;
var grad = wCtx.createRadialGradient(cx, cy, 0, cx, cy, r);
grad.addColorStop(0,   "hsl(" + angle + ",0%,50%)");
grad.addColorStop(0.5, "hsl(" + angle + "," + state.sat + "%," + state.bri + "%)");
grad.addColorStop(1,   "hsl(" + angle + "," + state.sat + "%," + state.bri + "%)");
wCtx.beginPath();
wCtx.moveTo(cx, cy);
wCtx.arc(cx, cy, r, startAngle, endAngle);
wCtx.closePath();
wCtx.fillStyle = grad;
wCtx.fill();
}

// White radial overlay for inner white fade
var fade = wCtx.createRadialGradient(cx, cy, 0, cx, cy, r);
fade.addColorStop(0,   "rgba(255,255,255,0.7)");
fade.addColorStop(0.4, "rgba(255,255,255,0.1)");
fade.addColorStop(1,   "rgba(255,255,255,0)");
wCtx.beginPath();
wCtx.arc(cx, cy, r, 0, Math.PI * 2);
wCtx.fillStyle = fade;
wCtx.fill();

// Clip to circle
wCtx.save();
wCtx.beginPath();
wCtx.arc(cx, cy, r, 0, Math.PI * 2);
wCtx.clip();

// Draw harmony dots + base dot
var offsets = harmonyOffsets(state.mode);
var allHues = [state.hue].concat(offsets.map(function(o) {
return ((state.hue + o) % 360 + 360) % 360;
}));
var dotColors = ["#ffffff"].concat(["#fbbf24", "#34d399", "#f472b6", "#a78bfa"]);

allHues.forEach(function(h, i) {
var rad = (h - 90) * Math.PI / 180;
var dotR = r * 0.82;
var dx = cx + dotR * Math.cos(rad);
var dy = cy + dotR * Math.sin(rad);
wCtx.beginPath();
wCtx.arc(dx, dy, 9, 0, Math.PI * 2);
wCtx.fillStyle = "hsl(" + h + "," + state.sat + "%," + state.bri + "%)";
wCtx.fill();
wCtx.strokeStyle = dotColors[i] || "#fff";
wCtx.lineWidth = 2.5;
wCtx.stroke();
});

wCtx.restore();
}

// ── Draw brightness strip ─────────────────────────────────────────────────
function drawBrightnessStrip() {
var w = brCanvas.width, h = brCanvas.height;
var grad = brCtx.createLinearGradient(0, 0, w, 0);
grad.addColorStop(0,   "hsl(" + state.hue + "," + state.sat + "%,0%)");
grad.addColorStop(0.5, "hsl(" + state.hue + "," + state.sat + "%,50%)");
grad.addColorStop(1,   "hsl(" + state.hue + "," + state.sat + "%,100%)");
brCtx.clearRect(0, 0, w, h);
brCtx.fillStyle = grad;
brCtx.fillRect(0, 0, w, h);
// Indicator
var x = Math.round((state.bri / 100) * w);
brCtx.beginPath();
brCtx.arc(x, h / 2, 10, 0, Math.PI * 2);
brCtx.fillStyle = "hsl(" + state.hue + "," + state.sat + "%," + state.bri + "%)";
brCtx.fill();
brCtx.strokeStyle = "#fff";
brCtx.lineWidth = 2;
brCtx.stroke();
}

// ── Draw saturation strip ─────────────────────────────────────────────────
function drawSaturationStrip() {
var w = saCanvas.width, h = saCanvas.height;
var grad = saCtx.createLinearGradient(0, 0, w, 0);
grad.addColorStop(0, "hsl(" + state.hue + ",0%," + state.bri + "%)");
grad.addColorStop(1, "hsl(" + state.hue + ",100%," + state.bri + "%)");
saCtx.clearRect(0, 0, w, h);
saCtx.fillStyle = grad;
saCtx.fillRect(0, 0, w, h);
var x = Math.round((state.sat / 100) * w);
saCtx.beginPath();
saCtx.arc(x, h / 2, 10, 0, Math.PI * 2);
saCtx.fillStyle = "hsl(" + state.hue + "," + state.sat + "%," + state.bri + "%)";
saCtx.fill();
saCtx.strokeStyle = "#fff";
saCtx.lineWidth = 2;
saCtx.stroke();
}

// ── WCAG contrast ─────────────────────────────────────────────────────────
function relativeLuminance(r, g, b) {
var sRGB = [r, g, b].map(function(c) {
c /= 255;
return c <= 0.03928 ? c / 12.92 : Math.pow((c + 0.055) / 1.055, 2.4);
});
return 0.2126 * sRGB[0] + 0.7152 * sRGB[1] + 0.0722 * sRGB[2];
}

function contrastRatio(c1, c2) {
var L1 = relativeLuminance(c1.r, c1.g, c1.b);
var L2 = relativeLuminance(c2.r, c2.g, c2.b);
var lighter = Math.max(L1, L2);
var darker  = Math.min(L1, L2);
return (lighter + 0.05) / (darker + 0.05);
}

// ── Render swatches ────────────────────────────────────────────────────────
var labels = ["Base", "Harmony 1", "Harmony 2", "Harmony 3", "Harmony 4"];

function copyText(text, chip) {
navigator.clipboard.writeText(text).then(function() {
chip.classList.add("copied");
var orig = chip.textContent;
chip.textContent = "Copied!";
setTimeout(function() {
chip.classList.remove("copied");
chip.textContent = orig;
}, 1200);
}).catch(function() {
// fallback
var ta = document.createElement("textarea");
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand("copy");
document.body.removeChild(ta);
chip.classList.add("copied");
var orig = chip.textContent;
chip.textContent = "Copied!";
setTimeout(function() {
chip.classList.remove("copied");
chip.textContent = orig;
}, 1200);
});
}

function renderSwatches(palette) {
var container = document.getElementById("cw-swatches");
container.innerHTML = "";
palette.forEach(function(color, i) {
var row = document.createElement("div");
row.className = "cw-swatch-row";

var box = document.createElement("div");
box.className = "cw-swatch-box";
box.style.background = color.hex;

var info = document.createElement("div");
info.className = "cw-swatch-info";

var lbl = document.createElement("div");
lbl.className = "cw-swatch-label";
lbl.textContent = labels[i] || ("Color " + (i + 1));

var vals = document.createElement("div");
vals.className = "cw-values";

[color.hex, color.rgb, color.hsl].forEach(function(val) {
var chip = document.createElement("span");
chip.className = "cw-val-chip";
chip.textContent = val;
chip.title = "Click to copy";
chip.addEventListener("click", function() { copyText(val, chip); });
vals.appendChild(chip);
});

info.appendChild(lbl);
info.appendChild(vals);
row.appendChild(box);
row.appendChild(info);
container.appendChild(row);
});
}

// ── Render contrast ────────────────────────────────────────────────────────
function renderContrast(palette) {
if (palette.length < 2) return;
var c1 = palette[0], c2 = palette[1];
var ratio = contrastRatio(c1, c2);
var ratioStr = ratio.toFixed(2) + ":1";

document.getElementById("cw-ratio-val").textContent = ratioStr;

var badge = document.getElementById("cw-wcag-badge");
if (ratio >= 7) {
badge.textContent = "AAA Pass";
badge.className = "cw-wcag-badge badge-pass";
} else if (ratio >= 4.5) {
badge.textContent = "AA Pass";
badge.className = "cw-wcag-badge badge-aa";
} else if (ratio >= 3) {
badge.textContent = "AA Large";
badge.className = "cw-wcag-badge badge-aa";
} else {
badge.textContent = "Fail";
badge.className = "cw-wcag-badge badge-fail";
}

// Preview samples
var dark = document.getElementById("cw-cp-dark");
var light = document.getElementById("cw-cp-light");
dark.style.background = c1.hex;
dark.style.color = c2.hex;
dark.textContent = "Aa — " + ratioStr;
light.style.background = c2.hex;
light.style.color = c1.hex;
light.textContent = "Aa — " + ratioStr;
}

// ── Render CSS export ──────────────────────────────────────────────────────
function renderCSS(palette) {
var lines = [":root {"];
palette.forEach(function(color, i) {
var name = i === 0 ? "base" : ("harmony-" + i);
lines.push("  --color-" + name + ": " + color.hex + ";");
lines.push("  --color-" + name + "-rgb: " + color.r + ", " + color.g + ", " + color.b + ";");
lines.push("  --color-" + name + "-hsl: " + color.hsl + ";");
});
lines.push("}");
document.getElementById("cw-css-output").value = lines.join("\n");
}

// ── Full render ────────────────────────────────────────────────────────────
function render() {
drawWheel();
drawBrightnessStrip();
drawSaturationStrip();
var palette = buildPalette();
renderSwatches(palette);
renderContrast(palette);
renderCSS(palette);
}

// ── Wheel interaction ──────────────────────────────────────────────────────
function wheelHueFromEvent(e) {
var rect = wheelCanvas.getBoundingClientRect();
var clientX = e.touches ? e.touches[0].clientX : e.clientX;
var clientY = e.touches ? e.touches[0].clientY : e.clientY;
var scaleX = wheelCanvas.width / rect.width;
var scaleY = wheelCanvas.height / rect.height;
var x = (clientX - rect.left) * scaleX - WHEEL_R;
var y = (clientY - rect.top)  * scaleY - WHEEL_R;
var angle = Math.atan2(y, x) * 180 / Math.PI + 90;
return ((angle % 360) + 360) % 360;
}

var wheelDragging = false;
wheelCanvas.addEventListener("mousedown", function(e) {
wheelDragging = true;
state.hue = wheelHueFromEvent(e);
render();
});
window.addEventListener("mousemove", function(e) {
if (!wheelDragging) return;
state.hue = wheelHueFromEvent(e);
render();
});
window.addEventListener("mouseup", function() { wheelDragging = false; });

wheelCanvas.addEventListener("touchstart", function(e) {
e.preventDefault();
wheelDragging = true;
state.hue = wheelHueFromEvent(e);
render();
}, { passive: false });
wheelCanvas.addEventListener("touchmove", function(e) {
e.preventDefault();
if (!wheelDragging) return;
state.hue = wheelHueFromEvent(e);
render();
}, { passive: false });
wheelCanvas.addEventListener("touchend", function() { wheelDragging = false; });

// ── Brightness strip interaction ───────────────────────────────────────────
function briFromEvent(e) {
var rect = brCanvas.getBoundingClientRect();
var clientX = e.touches ? e.touches[0].clientX : e.clientX;
var x = clientX - rect.left;
return Math.max(0, Math.min(100, Math.round((x / rect.width) * 100)));
}
var briDragging = false;
brCanvas.addEventListener("mousedown", function(e) {
briDragging = true;
state.bri = briFromEvent(e);
render();
});
window.addEventListener("mousemove", function(e) {
if (!briDragging) return;
state.bri = briFromEvent(e);
render();
});
window.addEventListener("mouseup", function() { briDragging = false; });
brCanvas.addEventListener("touchstart", function(e) {
e.preventDefault(); briDragging = true;
state.bri = briFromEvent(e); render();
}, { passive: false });
brCanvas.addEventListener("touchmove", function(e) {
e.preventDefault();
if (!briDragging) return;
state.bri = briFromEvent(e); render();
}, { passive: false });
brCanvas.addEventListener("touchend", function() { briDragging = false; });

// ── Saturation strip interaction ───────────────────────────────────────────
function satFromEvent(e) {
var rect = saCanvas.getBoundingClientRect();
var clientX = e.touches ? e.touches[0].clientX : e.clientX;
var x = clientX - rect.left;
return Math.max(0, Math.min(100, Math.round((x / rect.width) * 100)));
}
var satDragging = false;
saCanvas.addEventListener("mousedown", function(e) {
satDragging = true;
state.sat = satFromEvent(e);
render();
});
window.addEventListener("mousemove", function(e) {
if (!satDragging) return;
state.sat = satFromEvent(e);
render();
});
window.addEventListener("mouseup", function() { satDragging = false; });
saCanvas.addEventListener("touchstart", function(e) {
e.preventDefault(); satDragging = true;
state.sat = satFromEvent(e); render();
}, { passive: false });
saCanvas.addEventListener("touchmove", function(e) {
e.preventDefault();
if (!satDragging) return;
state.sat = satFromEvent(e); render();
}, { passive: false });
saCanvas.addEventListener("touchend", function() { satDragging = false; });

// ── Harmony mode buttons ───────────────────────────────────────────────────
document.querySelectorAll("#cw-app .cw-btn[data-mode]").forEach(function(btn) {
btn.addEventListener("click", function() {
document.querySelectorAll("#cw-app .cw-btn[data-mode]").forEach(function(b) {
b.classList.remove("active");
});
btn.classList.add("active");
state.mode = btn.getAttribute("data-mode");
render();
});
});

// ── Copy CSS button ────────────────────────────────────────────────────────
document.getElementById("cw-copy-css").addEventListener("click", function() {
var btn = document.getElementById("cw-copy-css");
var text = document.getElementById("cw-css-output").value;
navigator.clipboard.writeText(text).then(function() {
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(function() {
btn.textContent = "Copy CSS";
btn.classList.remove("copied");
}, 1400);
}).catch(function() {
var ta = document.getElementById("cw-css-output");
ta.select();
document.execCommand("copy");
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(function() {
btn.textContent = "Copy CSS";
btn.classList.remove("copied");
}, 1400);
});
});

// ── Initial render ─────────────────────────────────────────────────────────
render();
})();
</script>
</div>

---

## Related Tools

> [Color Blindness Simulator](/tools/color-blindness-simulator/)
> [Color Contrast Checker](/tools/color-contrast-checker/)
> [Color Converter](/tools/color-converter/)

