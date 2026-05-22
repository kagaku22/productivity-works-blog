---
title: "Neumorphism Generator"
date: 2025-05-16
description: "Free CSS neumorphism generator. Create soft UI shadow effects with customizable size, intensity, blur, and shape — copy CSS code instantly."
categories: ["Free Tools"]
tags: ["Utility", "Free Tools"]
slug: "neumorphism-generator"
ShowToc: false
cover:
  image: "/images/covers/neumorphism-generator.png"
  alt: "Neumorphism Generator"
---

Create soft UI shadow effects with full control over distance, blur, intensity, shape type, and border radius. Pick a background color and the generator automatically calculates the correct light and dark shadows for a perfect neumorphic look. Copy the CSS in one click.

<div id="nm-app" style="font-family:system-ui,-apple-system,sans-serif;max-width:900px;margin:0 auto;color:#333;">

<style>
#nm-app *,#nm-app *::before,#nm-app *::after{box-sizing:border-box;}
#nm-app .nm-layout{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-top:16px;}
@media(max-width:660px){#nm-app .nm-layout{grid-template-columns:1fr;}}
#nm-app .nm-panel{background:#f5f5f5;border-radius:14px;padding:20px;}
#nm-app .nm-preview-wrap{display:flex;align-items:center;justify-content:center;border-radius:14px;min-height:220px;transition:background .3s;}
#nm-app .nm-preview-el{transition:all .3s;cursor:default;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:600;color:#888;letter-spacing:.04em;}
#nm-app label.nm-label{display:block;font-size:12px;font-weight:700;color:#555;margin-bottom:4px;margin-top:14px;text-transform:uppercase;letter-spacing:.06em;}
#nm-app label.nm-label:first-child{margin-top:0;}
#nm-app input[type=range]{width:100%;accent-color:#6366f1;height:4px;cursor:pointer;}
#nm-app input[type=color]{width:48px;height:32px;border:none;border-radius:6px;cursor:pointer;padding:2px;background:none;}
#nm-app .nm-row{display:flex;align-items:center;gap:10px;}
#nm-app .nm-val{font-size:12px;color:#6366f1;font-weight:700;min-width:36px;text-align:right;}
#nm-app .nm-seg{display:flex;gap:6px;flex-wrap:wrap;}
#nm-app .nm-seg button{padding:5px 12px;border-radius:6px;border:1.5px solid #ddd;background:#fff;font-size:12px;cursor:pointer;font-weight:600;color:#555;transition:all .15s;}
#nm-app .nm-seg button.active{background:#6366f1;color:#fff;border-color:#6366f1;}
#nm-app .nm-presets{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:16px;}
#nm-app .nm-preset-btn{padding:6px 14px;border-radius:20px;border:1.5px solid #c7d2fe;background:#eef2ff;font-size:12px;cursor:pointer;font-weight:600;color:#4338ca;transition:all .15s;}
#nm-app .nm-preset-btn:hover{background:#6366f1;color:#fff;border-color:#6366f1;}
#nm-app .nm-code-wrap{position:relative;margin-top:16px;}
#nm-app .nm-code{background:#1e1e2e;color:#cdd6f4;border-radius:10px;padding:16px;font-size:12.5px;font-family:'Fira Mono','Courier New',monospace;line-height:1.7;overflow-x:auto;white-space:pre;tab-size:2;}
#nm-app .nm-code .c-prop{color:#89b4fa;}
#nm-app .nm-code .c-val{color:#a6e3a1;}
#nm-app .nm-code .c-punc{color:#cdd6f4;}
#nm-app .nm-copy-btn{position:absolute;top:10px;right:10px;padding:5px 14px;background:#6366f1;color:#fff;border:none;border-radius:6px;font-size:12px;font-weight:700;cursor:pointer;transition:background .15s;}
#nm-app .nm-copy-btn:hover{background:#4f46e5;}
#nm-app .nm-copy-btn.copied{background:#22c55e;}
#nm-app h3.nm-section-title{margin:0 0 12px;font-size:14px;font-weight:800;color:#4338ca;text-transform:uppercase;letter-spacing:.08em;}
#nm-app .nm-color-row{display:flex;align-items:center;gap:10px;}
#nm-app .nm-color-hex{font-size:13px;font-weight:700;color:#555;font-family:monospace;}
#nm-app .nm-divider{height:1px;background:#e5e7eb;margin:14px 0;}
</style>

<div class="nm-presets">
<button class="nm-preset-btn" onclick="nmLoadPreset('softcard')">Soft Card</button>
<button class="nm-preset-btn" onclick="nmLoadPreset('button')">Button</button>
<button class="nm-preset-btn" onclick="nmLoadPreset('circle')">Circle</button>
<button class="nm-preset-btn" onclick="nmLoadPreset('input')">Input Field</button>
<button class="nm-preset-btn" onclick="nmLoadPreset('toggle')">Toggle Switch</button>
</div>

<div class="nm-layout">
<!-- Left: Controls -->
<div class="nm-panel">
<h3 class="nm-section-title">Controls</h3>

<label class="nm-label">Background Color</label>
<div class="nm-color-row">
<input type="color" id="nm-bg" value="#e0e5ec" oninput="nmUpdate()">
<span class="nm-color-hex" id="nm-bg-hex">#e0e5ec</span>
</div>

<div class="nm-divider"></div>

<label class="nm-label">Shape Type</label>
<div class="nm-seg" id="nm-shape-seg">
<button class="active" onclick="nmShape('flat',this)">Flat</button>
<button onclick="nmShape('concave',this)">Concave</button>
<button onclick="nmShape('convex',this)">Convex</button>
<button onclick="nmShape('pressed',this)">Pressed</button>
</div>

<label class="nm-label">Element Shape</label>
<div class="nm-seg" id="nm-el-seg">
<button class="active" onclick="nmElShape('card',this)">Card</button>
<button onclick="nmElShape('button',this)">Button</button>
<button onclick="nmElShape('circle',this)">Circle</button>
</div>

<div class="nm-divider"></div>

<label class="nm-label">Size <span class="nm-val" id="v-size">160px</span></label>
<input type="range" id="nm-size" min="60" max="300" value="160" oninput="nmUpdate()">

<label class="nm-label">Shadow Distance <span class="nm-val" id="v-dist">10px</span></label>
<input type="range" id="nm-dist" min="1" max="50" value="10" oninput="nmUpdate()">

<label class="nm-label">Blur <span class="nm-val" id="v-blur">20px</span></label>
<input type="range" id="nm-blur" min="1" max="100" value="20" oninput="nmUpdate()">

<label class="nm-label">Intensity <span class="nm-val" id="v-int">0.25</span></label>
<input type="range" id="nm-int" min="1" max="50" value="25" oninput="nmUpdate()">

<label class="nm-label">Border Radius <span class="nm-val" id="v-rad">16px</span></label>
<input type="range" id="nm-rad" min="0" max="60" value="16" oninput="nmUpdate()">
</div>

<!-- Right: Preview -->
<div>
<div class="nm-panel" style="padding:0;overflow:hidden;">
<div class="nm-preview-wrap" id="nm-preview-wrap">
<div class="nm-preview-el" id="nm-preview-el">PREVIEW</div>
</div>
</div>
<div class="nm-code-wrap">
<pre class="nm-code" id="nm-code-out"></pre>
<button class="nm-copy-btn" id="nm-copy-btn" onclick="nmCopy()">Copy CSS</button>
</div>
</div>
</div>

<script>
(function(){
var state = {
bg: '#e0e5ec',
dist: 10,
blur: 20,
intensity: 0.25,
radius: 16,
size: 160,
shape: 'flat',
elShape: 'card'
};

function hexToRgb(hex) {
hex = hex.replace('#','');
if(hex.length===3) hex=hex[0]+hex[0]+hex[1]+hex[1]+hex[2]+hex[2];
var n=parseInt(hex,16);
return {r:(n>>16)&255,g:(n>>8)&255,b:n&255};
}

function rgbToHex(r,g,b){
return '#'+[r,g,b].map(function(v){
v=Math.max(0,Math.min(255,Math.round(v)));
return v.toString(16).padStart(2,'0');
}).join('');
}

function calcShadows(hex, dist, blur, intensity) {
var c = hexToRgb(hex);
var lighten = intensity * 255;
var darken = intensity * 255;
var light = rgbToHex(c.r+lighten, c.g+lighten, c.b+lighten);
var dark  = rgbToHex(c.r-darken,  c.g-darken,  c.b-darken);
return {light:light, dark:dark};
}

function buildBoxShadow(dist, blur, sh, shape, inset) {
var prefix = inset ? 'inset ' : '';
var base = prefix+(-dist)+'px '+(-dist)+'px '+blur+'px '+sh.light+', '+
prefix+dist+'px '+dist+'px '+blur+'px '+sh.dark;
return base;
}

function buildBackground(bg, shape) {
if(shape==='flat') return bg;
var c = hexToRgb(bg);
if(shape==='concave'){
var d=20;
var c1=rgbToHex(c.r-d,c.g-d,c.b-d);
var c2=rgbToHex(c.r+d,c.g+d,c.b+d);
return 'linear-gradient(145deg,'+c1+','+c2+')';
}
if(shape==='convex'){
var d=20;
var c1=rgbToHex(c.r+d,c.g+d,c.b+d);
var c2=rgbToHex(c.r-d,c.g-d,c.b-d);
return 'linear-gradient(145deg,'+c1+','+c2+')';
}
return bg;
}

function getRadiusForElShape(elShape, radius) {
if(elShape==='circle') return '50%';
if(elShape==='button') return Math.min(radius,30)+'px';
return radius+'px';
}

function getSizeStyle(elShape, size) {
if(elShape==='circle') return {width:size+'px',height:size+'px'};
if(elShape==='button') return {width:(size*1.6)+'px',height:(size*0.5)+'px'};
return {width:size+'px',height:size+'px'};
}

function nmUpdate() {
state.bg      = document.getElementById('nm-bg').value;
state.dist    = parseInt(document.getElementById('nm-dist').value);
state.blur    = parseInt(document.getElementById('nm-blur').value);
state.intensity = parseInt(document.getElementById('nm-int').value)/100;
state.radius  = parseInt(document.getElementById('nm-rad').value);
state.size    = parseInt(document.getElementById('nm-size').value);

document.getElementById('nm-bg-hex').textContent = state.bg;
document.getElementById('v-dist').textContent = state.dist+'px';
document.getElementById('v-blur').textContent = state.blur+'px';
document.getElementById('v-int').textContent  = state.intensity.toFixed(2);
document.getElementById('v-rad').textContent  = state.radius+'px';
document.getElementById('v-size').textContent = state.size+'px';

var sh = calcShadows(state.bg, state.dist, state.blur, state.intensity);
var isPressed = state.shape==='pressed';
var boxShadow = buildBoxShadow(state.dist, state.blur, sh, state.shape, isPressed);
var bg = buildBackground(state.bg, state.shape);
var borderRadius = getRadiusForElShape(state.elShape, state.radius);
var sz = getSizeStyle(state.elShape, state.size);

// Update preview wrap
var wrap = document.getElementById('nm-preview-wrap');
wrap.style.background = state.bg;
wrap.style.padding = '40px';

// Update preview element
var el = document.getElementById('nm-preview-el');
el.style.width = sz.width;
el.style.height = sz.height;
el.style.borderRadius = borderRadius;
el.style.background = bg;
el.style.boxShadow = boxShadow;

// Generate CSS
var radiusVal = borderRadius;
var bgVal = bg;
var lines = [];
lines.push('.nm-element {');
lines.push('  background: '+bgVal+';');
lines.push('  border-radius: '+radiusVal+';');
lines.push('  box-shadow: '+boxShadow+';');
if(sz.width===sz.height && state.elShape!=='button') {
lines.push('  width: '+sz.width+';');
lines.push('  height: '+sz.height+';');
} else {
lines.push('  width: '+sz.width+';');
lines.push('  height: '+sz.height+';');
}
lines.push('}');

renderCode(lines.join('\n'), sh);
}

function renderCode(css, sh) {
// Simple syntax highlighting
var html = css
.replace(/&/g,'&amp;')
.replace(/</g,'&lt;')
.replace(/>/g,'&gt;')
.replace(/([\w-]+)(?=\s*:)/g,'<span class="c-prop">$1</span>')
.replace(/:\s*([^;{}\n]+)/g,function(m,v){
return ': <span class="c-val">'+v+'</span>';
})
.replace(/[{}]/g,'<span class="c-punc">$&</span>');
document.getElementById('nm-code-out').innerHTML = html;
}

window.nmUpdate = nmUpdate;

window.nmShape = function(s, btn) {
state.shape = s;
document.querySelectorAll('#nm-shape-seg button').forEach(function(b){b.classList.remove('active');});
btn.classList.add('active');
nmUpdate();
};

window.nmElShape = function(s, btn) {
state.elShape = s;
document.querySelectorAll('#nm-el-seg button').forEach(function(b){b.classList.remove('active');});
btn.classList.add('active');
nmUpdate();
};

window.nmCopy = function() {
var code = document.getElementById('nm-code-out').textContent;
navigator.clipboard.writeText(code).then(function(){
var btn = document.getElementById('nm-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){btn.textContent='Copy CSS';btn.classList.remove('copied');},1800);
});
};

var presets = {
softcard:  {bg:'#e0e5ec',dist:10,blur:20,int:25,rad:16,size:160,shape:'flat',elShape:'card'},
button:    {bg:'#e8ecf0',dist:6, blur:12,int:20,rad:10,size:130,shape:'convex',elShape:'button'},
circle:    {bg:'#dde1e7',dist:8, blur:16,int:22,rad:50,size:140,shape:'flat',elShape:'circle'},
input:     {bg:'#eaeef3',dist:5, blur:10,int:18,rad:8, size:160,shape:'pressed',elShape:'button'},
toggle:    {bg:'#e0e5ec',dist:6, blur:12,int:20,rad:30,size:100,shape:'flat',elShape:'button'}
};

window.nmLoadPreset = function(name) {
var p = presets[name];
if(!p) return;
document.getElementById('nm-bg').value = p.bg;
document.getElementById('nm-dist').value = p.dist;
document.getElementById('nm-blur').value = p.blur;
document.getElementById('nm-int').value = p.int;
document.getElementById('nm-rad').value = p.rad;
document.getElementById('nm-size').value = p.size;
state.shape = p.shape;
state.elShape = p.elShape;
// Update shape seg buttons
document.querySelectorAll('#nm-shape-seg button').forEach(function(b){
b.classList.toggle('active', b.textContent.toLowerCase()===p.shape||(p.shape==='pressed'&&b.textContent==='Pressed'));
});
document.querySelectorAll('#nm-el-seg button').forEach(function(b){
var label = b.textContent.toLowerCase();
b.classList.toggle('active', label===p.elShape);
});
nmUpdate();
};

// Init
nmUpdate();
})();
</script>

</div>

---

### How Neumorphism Works

Neumorphism (soft UI) creates depth by casting two shadows from a single element — one light shadow in the top-left direction and one dark shadow in the bottom-right direction, both derived from the background color. The element itself must use the same color as its container background, which is why the background color picker is the most critical control.

**Key tips:**
- Keep background colors in a mid-range lightness (not too dark, not too bright)
- Shadow intensity above 0.4 can look harsh — 0.15–0.30 is the sweet spot
- Use **Pressed** shape for active states like clicked buttons or focused inputs
- **Concave** and **Convex** use a gradient overlay to enhance the 3D illusion
- Neumorphism works best at larger sizes — tiny elements lose the effect

---

### Related Tools

> Glassmorphism effects → [Glassmorphism Generator](/tools/glassmorphism-generator/)
> Box shadows → [Box Shadow Generator](/tools/box-shadow-generator/)
> CSS buttons → [CSS Button Generator](/tools/css-button-generator/)
