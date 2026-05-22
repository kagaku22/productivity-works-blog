---
title: "CSS Button Generator — Free Visual Builder"
date: 2025-05-16
description: "Design CSS buttons with live preview. Customize colors, borders, shadows, hover effects, and transitions. Presets for primary, outline, gradient, and 3D buttons."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "css-button-generator"
ShowToc: false
cover:
  image: "/images/covers/css-button-generator.png"
  alt: "CSS Button Generator"
---

Design professional CSS buttons visually — no coding required. Adjust every style property in real time, pick from built-in presets, and copy the finished CSS and HTML with one click.

<div id="btn-app">
<style>
#btn-app *,
#btn-app *::before,
#btn-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#btn-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 14px;
color: #1a1a2e;
line-height: 1.5;
}
#btn-app .bgen-wrap {
display: grid;
grid-template-columns: 320px 1fr;
gap: 24px;
margin: 24px 0;
}
@media (max-width: 768px) {
#btn-app .bgen-wrap {
grid-template-columns: 1fr;
}
}
/* Panel */
#btn-app .bgen-panel {
background: #f8f9fa;
border: 1px solid #e0e0e0;
border-radius: 12px;
padding: 20px;
display: flex;
flex-direction: column;
gap: 16px;
}
#btn-app .bgen-section-title {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #888;
margin-bottom: 4px;
}
#btn-app .bgen-field {
display: flex;
flex-direction: column;
gap: 4px;
}
#btn-app .bgen-field label {
font-size: 13px;
font-weight: 500;
color: #333;
display: flex;
justify-content: space-between;
align-items: center;
}
#btn-app .bgen-field label span.bgen-val {
font-weight: 400;
color: #666;
font-size: 12px;
}
#btn-app .bgen-field input[type="range"] {
width: 100%;
accent-color: #4f46e5;
cursor: pointer;
}
#btn-app .bgen-field input[type="color"] {
width: 40px;
height: 28px;
border: 1px solid #ccc;
border-radius: 6px;
padding: 2px;
cursor: pointer;
background: none;
}
#btn-app .bgen-color-row {
display: flex;
align-items: center;
gap: 8px;
}
#btn-app .bgen-color-row input[type="text"] {
flex: 1;
border: 1px solid #ccc;
border-radius: 6px;
padding: 4px 8px;
font-size: 12px;
font-family: monospace;
color: #333;
}
#btn-app .bgen-select {
width: 100%;
border: 1px solid #ccc;
border-radius: 6px;
padding: 5px 8px;
font-size: 13px;
background: #fff;
color: #333;
cursor: pointer;
}
#btn-app .bgen-toggle-row {
display: flex;
align-items: center;
justify-content: space-between;
}
#btn-app .bgen-toggle {
position: relative;
width: 36px;
height: 20px;
}
#btn-app .bgen-toggle input {
opacity: 0;
width: 0;
height: 0;
}
#btn-app .bgen-toggle-slider {
position: absolute;
inset: 0;
background: #ccc;
border-radius: 20px;
cursor: pointer;
transition: background 0.2s;
}
#btn-app .bgen-toggle-slider::before {
content: "";
position: absolute;
width: 14px;
height: 14px;
left: 3px;
top: 3px;
background: #fff;
border-radius: 50%;
transition: transform 0.2s;
}
#btn-app .bgen-toggle input:checked + .bgen-toggle-slider {
background: #4f46e5;
}
#btn-app .bgen-toggle input:checked + .bgen-toggle-slider::before {
transform: translateX(16px);
}
#btn-app .bgen-divider {
border: none;
border-top: 1px solid #e0e0e0;
}
/* Presets */
#btn-app .bgen-presets {
display: flex;
flex-wrap: wrap;
gap: 6px;
}
#btn-app .bgen-preset-btn {
border: 1px solid #ccc;
border-radius: 6px;
padding: 4px 10px;
font-size: 12px;
cursor: pointer;
background: #fff;
color: #333;
transition: all 0.15s;
}
#btn-app .bgen-preset-btn:hover {
border-color: #4f46e5;
color: #4f46e5;
}
/* Preview area */
#btn-app .bgen-right {
display: flex;
flex-direction: column;
gap: 16px;
}
#btn-app .bgen-preview-box {
border: 1px solid #e0e0e0;
border-radius: 12px;
min-height: 180px;
display: flex;
align-items: center;
justify-content: center;
transition: background 0.3s;
padding: 32px;
position: relative;
}
#btn-app .bgen-preview-box.dark {
background: #1a1a2e;
border-color: #333;
}
#btn-app .bgen-preview-box.light {
background: #ffffff;
}
#btn-app .bgen-preview-label {
position: absolute;
top: 10px;
left: 14px;
font-size: 11px;
color: #aaa;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#btn-app .bgen-theme-toggle {
position: absolute;
top: 8px;
right: 12px;
display: flex;
gap: 6px;
}
#btn-app .bgen-theme-btn {
border: 1px solid #ccc;
border-radius: 6px;
padding: 2px 8px;
font-size: 11px;
cursor: pointer;
background: #fff;
color: #555;
}
#btn-app .bgen-theme-btn.active {
background: #4f46e5;
color: #fff;
border-color: #4f46e5;
}
/* Generated button */
#btn-app #bgen-live-btn {
display: inline-block;
cursor: pointer;
text-decoration: none;
border: 2px solid transparent;
transition: all 0.3s ease;
}
/* Code output */
#btn-app .bgen-code-block {
background: #1e1e2e;
border-radius: 10px;
padding: 16px;
position: relative;
}
#btn-app .bgen-code-tabs {
display: flex;
gap: 4px;
margin-bottom: 12px;
}
#btn-app .bgen-code-tab {
padding: 4px 12px;
border-radius: 6px;
font-size: 12px;
cursor: pointer;
background: #2d2d44;
color: #aaa;
border: none;
}
#btn-app .bgen-code-tab.active {
background: #4f46e5;
color: #fff;
}
#btn-app .bgen-code-output {
font-family: "Fira Code", "Cascadia Code", monospace;
font-size: 12px;
color: #cdd6f4;
white-space: pre-wrap;
word-break: break-all;
line-height: 1.6;
max-height: 200px;
overflow-y: auto;
}
#btn-app .bgen-copy-btn {
position: absolute;
top: 12px;
right: 12px;
background: #4f46e5;
color: #fff;
border: none;
border-radius: 6px;
padding: 4px 12px;
font-size: 12px;
cursor: pointer;
transition: background 0.15s;
}
#btn-app .bgen-copy-btn:hover {
background: #4338ca;
}
#btn-app .bgen-copy-btn.copied {
background: #16a34a;
}
</style>

<div class="bgen-wrap">
<!-- LEFT: Controls -->
<div class="bgen-panel">

<div>
<div class="bgen-section-title">Presets</div>
<div class="bgen-presets">
<button class="bgen-preset-btn" data-preset="primary">Primary</button>
<button class="bgen-preset-btn" data-preset="secondary">Secondary</button>
<button class="bgen-preset-btn" data-preset="outline">Outline</button>
<button class="bgen-preset-btn" data-preset="ghost">Ghost</button>
<button class="bgen-preset-btn" data-preset="gradient">Gradient</button>
<button class="bgen-preset-btn" data-preset="threed">3D</button>
<button class="bgen-preset-btn" data-preset="pill">Pill</button>
<button class="bgen-preset-btn" data-preset="icon">Icon Button</button>
</div>
</div>

<hr class="bgen-divider">

<!-- Button Text -->
<div class="bgen-field">
<label>Button Text</label>
<input type="text" id="bgen-text" class="bgen-select" value="Click Me" style="padding:5px 8px;">
</div>

<!-- Colors -->
<div class="bgen-section-title">Colors</div>

<div class="bgen-field">
<label>Background Color</label>
<div class="bgen-color-row">
<input type="color" id="bgen-bg" value="#4f46e5">
<input type="text" id="bgen-bg-hex" value="#4f46e5">
</div>
</div>

<div class="bgen-field">
<label>Text Color</label>
<div class="bgen-color-row">
<input type="color" id="bgen-color" value="#ffffff">
<input type="text" id="bgen-color-hex" value="#ffffff">
</div>
</div>

<div class="bgen-field">
<label>Border Color</label>
<div class="bgen-color-row">
<input type="color" id="bgen-border-color" value="#4f46e5">
<input type="text" id="bgen-border-color-hex" value="#4f46e5">
</div>
</div>

<hr class="bgen-divider">

<!-- Typography & Size -->
<div class="bgen-section-title">Size & Typography</div>

<div class="bgen-field">
<label>Font Size <span class="bgen-val" id="bgen-fontsize-val">16px</span></label>
<input type="range" id="bgen-fontsize" min="10" max="36" value="16">
</div>

<div class="bgen-field">
<label>Padding H <span class="bgen-val" id="bgen-padh-val">20px</span></label>
<input type="range" id="bgen-padh" min="4" max="80" value="20">
</div>

<div class="bgen-field">
<label>Padding V <span class="bgen-val" id="bgen-padv-val">12px</span></label>
<input type="range" id="bgen-padv" min="2" max="40" value="12">
</div>

<div class="bgen-field">
<label>Border Radius <span class="bgen-val" id="bgen-radius-val">8px</span></label>
<input type="range" id="bgen-radius" min="0" max="60" value="8">
</div>

<hr class="bgen-divider">

<!-- Border -->
<div class="bgen-section-title">Border</div>

<div class="bgen-field">
<label>Border Width <span class="bgen-val" id="bgen-bwidth-val">0px</span></label>
<input type="range" id="bgen-bwidth" min="0" max="8" value="0">
</div>

<div class="bgen-field">
<label>Border Style</label>
<select id="bgen-bstyle" class="bgen-select">
<option value="solid">Solid</option>
<option value="dashed">Dashed</option>
<option value="dotted">Dotted</option>
<option value="double">Double</option>
</select>
</div>

<hr class="bgen-divider">

<!-- Box Shadow -->
<div class="bgen-section-title">Box Shadow</div>

<div class="bgen-field">
<label>Shadow X <span class="bgen-val" id="bgen-sx-val">0px</span></label>
<input type="range" id="bgen-sx" min="-20" max="20" value="0">
</div>
<div class="bgen-field">
<label>Shadow Y <span class="bgen-val" id="bgen-sy-val">4px</span></label>
<input type="range" id="bgen-sy" min="-20" max="20" value="4">
</div>
<div class="bgen-field">
<label>Shadow Blur <span class="bgen-val" id="bgen-sblur-val">14px</span></label>
<input type="range" id="bgen-sblur" min="0" max="60" value="14">
</div>
<div class="bgen-field">
<label>Shadow Spread <span class="bgen-val" id="bgen-sspread-val">0px</span></label>
<input type="range" id="bgen-sspread" min="-10" max="20" value="0">
</div>
<div class="bgen-field">
<label>Shadow Color</label>
<div class="bgen-color-row">
<input type="color" id="bgen-scolor" value="#4f46e5">
<input type="text" id="bgen-scolor-hex" value="#4f46e5">
</div>
</div>
<div class="bgen-field">
<label>Shadow Opacity <span class="bgen-val" id="bgen-sopacity-val">30%</span></label>
<input type="range" id="bgen-sopacity" min="0" max="100" value="30">
</div>

<hr class="bgen-divider">

<!-- Hover Effects -->
<div class="bgen-section-title">Hover Effects</div>

<div class="bgen-field">
<label>Hover Background</label>
<div class="bgen-color-row">
<input type="color" id="bgen-hbg" value="#4338ca">
<input type="text" id="bgen-hbg-hex" value="#4338ca">
</div>
</div>

<div class="bgen-toggle-row">
<label style="font-size:13px;font-weight:500;color:#333;">Scale on Hover</label>
<label class="bgen-toggle">
<input type="checkbox" id="bgen-hover-scale">
<span class="bgen-toggle-slider"></span>
</label>
</div>

<div class="bgen-field">
<label>Hover Scale <span class="bgen-val" id="bgen-hscale-val">1.05</span></label>
<input type="range" id="bgen-hscale" min="100" max="120" value="105">
</div>

<div class="bgen-toggle-row">
<label style="font-size:13px;font-weight:500;color:#333;">Hover Shadow</label>
<label class="bgen-toggle">
<input type="checkbox" id="bgen-hover-shadow" checked>
<span class="bgen-toggle-slider"></span>
</label>
</div>

<div class="bgen-field">
<label>Transition Duration <span class="bgen-val" id="bgen-trans-val">300ms</span></label>
<input type="range" id="bgen-trans" min="50" max="1000" step="50" value="300">
</div>

</div>

<!-- RIGHT: Preview + Code -->
<div class="bgen-right">

<div class="bgen-preview-box light" id="bgen-preview-box">
<span class="bgen-preview-label">Live Preview</span>
<div class="bgen-theme-toggle">
<button class="bgen-theme-btn active" data-theme="light">Light</button>
<button class="bgen-theme-btn" data-theme="dark">Dark</button>
</div>
<button id="bgen-live-btn">Click Me</button>
</div>

<div class="bgen-code-block">
<div class="bgen-code-tabs">
<button class="bgen-code-tab active" data-tab="css">CSS</button>
<button class="bgen-code-tab" data-tab="html">HTML</button>
</div>
<button class="bgen-copy-btn" id="bgen-copy-btn">Copy</button>
<div class="bgen-code-output" id="bgen-code-output"></div>
</div>

</div>
</div>

<script>
(function() {
// State
var S = {
text: "Click Me",
bg: "#4f46e5",
color: "#ffffff",
borderColor: "#4f46e5",
fontSize: 16,
padH: 20,
padV: 12,
radius: 8,
bwidth: 0,
bstyle: "solid",
sx: 0, sy: 4, sblur: 14, sspread: 0,
scolor: "#4f46e5",
sopacity: 30,
hbg: "#4338ca",
hoverScale: false,
hscale: 1.05,
hoverShadow: true,
trans: 300,
activeTab: "css"
};

var presets = {
primary: { bg:"#4f46e5", color:"#ffffff", borderColor:"#4f46e5", bwidth:0, radius:8, sx:0, sy:4, sblur:14, sspread:0, scolor:"#4f46e5", sopacity:30, hbg:"#4338ca", hoverScale:false, hoverShadow:true, padH:20, padV:12 },
secondary: { bg:"#6b7280", color:"#ffffff", borderColor:"#6b7280", bwidth:0, radius:8, sx:0, sy:2, sblur:8, sspread:0, scolor:"#000000", sopacity:20, hbg:"#4b5563", hoverScale:false, hoverShadow:false, padH:20, padV:12 },
outline: { bg:"#ffffff", color:"#4f46e5", borderColor:"#4f46e5", bwidth:2, radius:8, sx:0, sy:0, sblur:0, sspread:0, scolor:"#4f46e5", sopacity:0, hbg:"#eef2ff", hoverScale:false, hoverShadow:false, padH:20, padV:12 },
ghost: { bg:"transparent", color:"#4f46e5", borderColor:"transparent", bwidth:0, radius:8, sx:0, sy:0, sblur:0, sspread:0, scolor:"#4f46e5", sopacity:0, hbg:"#eef2ff", hoverScale:false, hoverShadow:false, padH:20, padV:12 },
gradient: { bg:"#6366f1", color:"#ffffff", borderColor:"transparent", bwidth:0, radius:10, sx:0, sy:4, sblur:20, sspread:0, scolor:"#6366f1", sopacity:40, hbg:"#4f46e5", hoverScale:true, hoverShadow:true, padH:24, padV:14 },
threed: { bg:"#4f46e5", color:"#ffffff", borderColor:"#3730a3", bwidth:0, radius:8, sx:0, sy:5, sblur:0, sspread:0, scolor:"#3730a3", sopacity:100, hbg:"#4338ca", hoverScale:false, hoverShadow:false, padH:20, padV:12 },
pill: { bg:"#4f46e5", color:"#ffffff", borderColor:"#4f46e5", bwidth:0, radius:60, sx:0, sy:4, sblur:14, sspread:0, scolor:"#4f46e5", sopacity:30, hbg:"#4338ca", hoverScale:true, hoverShadow:true, padH:28, padV:12 },
icon: { bg:"#4f46e5", color:"#ffffff", borderColor:"#4f46e5", bwidth:0, radius:50, sx:0, sy:4, sblur:14, sspread:0, scolor:"#4f46e5", sopacity:30, hbg:"#4338ca", hoverScale:true, hoverShadow:true, padH:14, padV:14 }
};

function hexToRgb(hex) {
var r = 0, g = 0, b = 0;
hex = hex.replace('#','');
if(hex.length === 3) hex = hex[0]+hex[0]+hex[1]+hex[1]+hex[2]+hex[2];
if(hex.length === 6) {
r = parseInt(hex.substring(0,2),16);
g = parseInt(hex.substring(2,4),16);
b = parseInt(hex.substring(4,6),16);
}
return {r:r,g:g,b:b};
}

function shadowCSS() {
var rgb = hexToRgb(S.scolor);
var a = S.sopacity / 100;
return S.sx+'px '+S.sy+'px '+S.sblur+'px '+S.sspread+'px rgba('+rgb.r+','+rgb.g+','+rgb.b+','+a.toFixed(2)+')';
}

function hoverShadowCSS() {
var rgb = hexToRgb(S.scolor);
return S.sx+'px '+(S.sy+4)+'px '+(S.sblur+10)+'px '+S.sspread+'px rgba('+rgb.r+','+rgb.g+','+rgb.b+',0.45)';
}

function buildBaseCSS() {
var bg = S.bg === 'transparent' ? 'transparent' : S.bg;
var shadow = (S.sopacity > 0 || S.sx !== 0 || S.sy !== 0 || S.sblur !== 0 || S.sspread !== 0) ? shadowCSS() : 'none';
return [
'display: inline-block;',
'background-color: '+bg+';',
'color: '+S.color+';',
'font-size: '+S.fontSize+'px;',
'padding: '+S.padV+'px '+S.padH+'px;',
'border-radius: '+S.radius+'px;',
'border: '+S.bwidth+'px '+S.bstyle+' '+S.borderColor+';',
'box-shadow: '+shadow+';',
'cursor: pointer;',
'transition: all '+S.trans+'ms ease;',
'text-decoration: none;',
].join('\n  ');
}

function buildHoverCSS() {
var parts = ['background-color: '+S.hbg+';'];
if(S.hoverScale) parts.push('transform: scale('+S.hscale+');');
if(S.hoverShadow) parts.push('box-shadow: '+hoverShadowCSS()+';');
return parts.join('\n  ');
}

function generateCSS() {
return '.my-button {\n  '+buildBaseCSS()+'\n}\n\n.my-button:hover {\n  '+buildHoverCSS()+'\n}';
}

function generateHTML() {
return '<button class="my-button">'+S.text+'</button>';
}

var liveBtn = document.getElementById('bgen-live-btn');
var codeOut = document.getElementById('bgen-code-output');

function applyLiveStyle() {
var bg = S.bg === 'transparent' ? 'transparent' : S.bg;
var shadow = (S.sopacity > 0 || S.sx !== 0 || S.sy !== 0 || S.sblur !== 0 || S.sspread !== 0) ? shadowCSS() : 'none';
liveBtn.textContent = S.text;
liveBtn.style.backgroundColor = bg;
liveBtn.style.color = S.color;
liveBtn.style.fontSize = S.fontSize+'px';
liveBtn.style.padding = S.padV+'px '+S.padH+'px';
liveBtn.style.borderRadius = S.radius+'px';
liveBtn.style.border = S.bwidth+'px '+S.bstyle+' '+S.borderColor;
liveBtn.style.boxShadow = shadow;
liveBtn.style.transition = 'all '+S.trans+'ms ease';
liveBtn.style.cursor = 'pointer';
liveBtn.style.background = S.bg === 'gradient'
? 'linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%)'
: bg;

// Hover via mouseover/mouseout
liveBtn.onmouseover = function() {
this.style.backgroundColor = S.hbg;
if(S.hoverScale) this.style.transform = 'scale('+S.hscale+')';
if(S.hoverShadow) this.style.boxShadow = hoverShadowCSS();
};
liveBtn.onmouseout = function() {
this.style.backgroundColor = bg;
this.style.transform = '';
this.style.boxShadow = shadow;
};
}

function updateCode() {
if(S.activeTab === 'css') {
codeOut.textContent = generateCSS();
} else {
codeOut.textContent = generateHTML();
}
}

function update() {
applyLiveStyle();
updateCode();
}

// Helpers: sync color picker + hex text
function syncColor(pickerId, hexId, stateKey) {
var picker = document.getElementById(pickerId);
var hex = document.getElementById(hexId);
picker.addEventListener('input', function() {
S[stateKey] = this.value;
hex.value = this.value;
update();
});
hex.addEventListener('input', function() {
if(/^#[0-9a-fA-F]{6}$/.test(this.value)) {
S[stateKey] = this.value;
picker.value = this.value;
update();
}
});
}

function syncRange(id, stateKey, valId, suffix, divisor) {
var el = document.getElementById(id);
var valEl = document.getElementById(valId);
el.addEventListener('input', function() {
var v = parseFloat(this.value);
S[stateKey] = divisor ? v/divisor : v;
valEl.textContent = divisor ? (v/divisor).toFixed(2) : v+suffix;
update();
});
}

// Wire up controls
document.getElementById('bgen-text').addEventListener('input', function() {
S.text = this.value || "Button";
update();
});

syncColor('bgen-bg','bgen-bg-hex','bg');
syncColor('bgen-color','bgen-color-hex','color');
syncColor('bgen-border-color','bgen-border-color-hex','borderColor');
syncColor('bgen-scolor','bgen-scolor-hex','scolor');
syncColor('bgen-hbg','bgen-hbg-hex','hbg');

syncRange('bgen-fontsize','fontSize','bgen-fontsize-val','px',null);
syncRange('bgen-padh','padH','bgen-padh-val','px',null);
syncRange('bgen-padv','padV','bgen-padv-val','px',null);
syncRange('bgen-radius','radius','bgen-radius-val','px',null);
syncRange('bgen-bwidth','bwidth','bgen-bwidth-val','px',null);
syncRange('bgen-sx','sx','bgen-sx-val','px',null);
syncRange('bgen-sy','sy','bgen-sy-val','px',null);
syncRange('bgen-sblur','sblur','bgen-sblur-val','px',null);
syncRange('bgen-sspread','sspread','bgen-sspread-val','px',null);
syncRange('bgen-sopacity','sopacity','bgen-sopacity-val','%',null);
syncRange('bgen-hscale','hscale','bgen-hscale-val','',100);
syncRange('bgen-trans','trans','bgen-trans-val','ms',null);

document.getElementById('bgen-bstyle').addEventListener('change', function() {
S.bstyle = this.value; update();
});
document.getElementById('bgen-hover-scale').addEventListener('change', function() {
S.hoverScale = this.checked; update();
});
document.getElementById('bgen-hover-shadow').addEventListener('change', function() {
S.hoverShadow = this.checked; update();
});

// Presets
document.querySelectorAll('#btn-app .bgen-preset-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
var p = presets[this.dataset.preset];
if(!p) return;
Object.assign(S, p);
// Sync all inputs
document.getElementById('bgen-bg').value = S.bg !== 'transparent' ? S.bg : '#ffffff';
document.getElementById('bgen-bg-hex').value = S.bg;
document.getElementById('bgen-color').value = S.color;
document.getElementById('bgen-color-hex').value = S.color;
document.getElementById('bgen-border-color').value = S.borderColor !== 'transparent' ? S.borderColor : '#ffffff';
document.getElementById('bgen-border-color-hex').value = S.borderColor;
document.getElementById('bgen-scolor').value = S.scolor;
document.getElementById('bgen-scolor-hex').value = S.scolor;
document.getElementById('bgen-hbg').value = S.hbg;
document.getElementById('bgen-hbg-hex').value = S.hbg;
document.getElementById('bgen-fontsize').value = S.fontSize;
document.getElementById('bgen-fontsize-val').textContent = S.fontSize+'px';
document.getElementById('bgen-padh').value = S.padH;
document.getElementById('bgen-padh-val').textContent = S.padH+'px';
document.getElementById('bgen-padv').value = S.padV;
document.getElementById('bgen-padv-val').textContent = S.padV+'px';
document.getElementById('bgen-radius').value = S.radius;
document.getElementById('bgen-radius-val').textContent = S.radius+'px';
document.getElementById('bgen-bwidth').value = S.bwidth;
document.getElementById('bgen-bwidth-val').textContent = S.bwidth+'px';
document.getElementById('bgen-sx').value = S.sx;
document.getElementById('bgen-sx-val').textContent = S.sx+'px';
document.getElementById('bgen-sy').value = S.sy;
document.getElementById('bgen-sy-val').textContent = S.sy+'px';
document.getElementById('bgen-sblur').value = S.sblur;
document.getElementById('bgen-sblur-val').textContent = S.sblur+'px';
document.getElementById('bgen-sspread').value = S.sspread;
document.getElementById('bgen-sspread-val').textContent = S.sspread+'px';
document.getElementById('bgen-sopacity').value = S.sopacity;
document.getElementById('bgen-sopacity-val').textContent = S.sopacity+'%';
document.getElementById('bgen-hscale').value = Math.round(S.hscale*100);
document.getElementById('bgen-hscale-val').textContent = S.hscale.toFixed(2);
document.getElementById('bgen-hover-scale').checked = S.hoverScale;
document.getElementById('bgen-hover-shadow').checked = S.hoverShadow;
document.getElementById('bgen-trans').value = S.trans;
document.getElementById('bgen-trans-val').textContent = S.trans+'ms';
update();
});
});

// Theme toggle
document.querySelectorAll('#btn-app .bgen-theme-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#btn-app .bgen-theme-btn').forEach(function(b){ b.classList.remove('active'); });
this.classList.add('active');
var box = document.getElementById('bgen-preview-box');
box.classList.remove('light','dark');
box.classList.add(this.dataset.theme);
});
});

// Code tabs
document.querySelectorAll('#btn-app .bgen-code-tab').forEach(function(tab) {
tab.addEventListener('click', function() {
document.querySelectorAll('#btn-app .bgen-code-tab').forEach(function(t){ t.classList.remove('active'); });
this.classList.add('active');
S.activeTab = this.dataset.tab;
updateCode();
});
});

// Copy button
document.getElementById('bgen-copy-btn').addEventListener('click', function() {
var text = codeOut.textContent;
var btn = this;
if(navigator.clipboard) {
navigator.clipboard.writeText(text).then(function() {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent='Copy'; btn.classList.remove('copied'); }, 1800);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent='Copy'; btn.classList.remove('copied'); }, 1800);
}
});

// Init
update();
})();
</script>
</div>

---

## How to Use the CSS Button Generator

1. **Choose a preset** — start with Primary, Outline, Gradient, or any of the 8 presets.
2. **Adjust controls** — tweak colors, size, border, shadow, and hover effects live.
3. **Toggle preview theme** — check how the button looks on light and dark backgrounds.
4. **Copy CSS or HTML** — switch tabs and click Copy to grab the finished code.
5. **Paste into your project** — rename `.my-button` to match your class name.

---

## CSS Properties Explained

| Property | What it does |
|---|---|
| `background-color` | Fill color of the button |
| `color` | Text color |
| `font-size` | Text size in pixels |
| `padding` | Inner spacing (vertical / horizontal) |
| `border-radius` | Corner roundness; `9999px` = pill shape |
| `border` | Width, style, and color of the border |
| `box-shadow` | Drop or glow shadow with full offset control |
| `transition` | Animation speed for hover effects |
| `transform: scale()` | Scale-up effect on hover |

---

## Preset Reference

- **Primary** — solid indigo fill, subtle shadow, standard border-radius
- **Secondary** — muted gray, minimal shadow
- **Outline** — transparent background, colored border and text
- **Ghost** — no border, no background; background appears on hover only
- **Gradient** — `linear-gradient` background with glow shadow and scale hover
- **3D** — solid bottom shadow creates a raised, pressable look
- **Pill** — `border-radius: 9999px` for fully rounded ends
- **Icon Button** — compact square with equal padding, suitable for icon-only actions

---

## Tips for Accessible Buttons

- Maintain at least **4.5:1 contrast ratio** between text and background.
- Never rely on color alone — add a visible focus ring with `:focus-visible`.
- Keep tap targets at least **44×44 px** for mobile users.
- Use `<button>` for actions and `<a>` for navigation links.

---

## Related Free Tools

- [CSS Box Shadow Generator](/tools/box-shadow-generator/) — build and preview multi-layer shadows
- [CSS Gradient Generator](/tools/css-gradient-generator/) — linear, radial, and conic gradients with live preview
- [CSS Animation Generator](/tools/css-animation-generator/) — keyframe animations with timing and easing controls
