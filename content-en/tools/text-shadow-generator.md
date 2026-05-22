---
title: "CSS Text Shadow Generator"
slug: "text-shadow-generator"
date: 2025-05-16
description: "Free CSS text shadow generator. Add single or multiple text shadows with live preview, presets, and one-click CSS copy."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
ShowToc: false
cover:
  image: /images/covers/text-shadow-generator.png
  alt: "CSS Text Shadow Generator – live preview with multiple shadow layers and preset effects"
---

Generate `text-shadow` CSS instantly — add multiple shadow layers, pick from presets, preview live, and copy the CSS with one click.

---

<div id="ts-app">
<style>
#ts-app *,#ts-app *::before,#ts-app *::after{box-sizing:border-box;margin:0;padding:0}
#ts-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;font-size:14px;color:#1e293b;max-width:860px}
#ts-app h2{font-size:15px;font-weight:700;margin-bottom:10px;color:#0f172a}
#ts-app .ts-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px}
@media(max-width:640px){#ts-app .ts-grid{grid-template-columns:1fr}}
#ts-app .ts-panel{background:#f8fafc;border:1.5px solid #e2e8f0;border-radius:10px;padding:16px}
#ts-app .ts-preview-wrap{background:#1e293b;border-radius:10px;padding:30px 20px;text-align:center;min-height:140px;display:flex;align-items:center;justify-content:center;margin-bottom:16px;overflow:hidden;position:relative}
#ts-app #ts-preview-text{font-weight:700;white-space:nowrap;transition:text-shadow .15s,color .15s,font-size .15s}
#ts-app .ts-ctrl-row{display:flex;align-items:center;gap:8px;margin-bottom:10px;flex-wrap:wrap}
#ts-app .ts-ctrl-row label{min-width:90px;font-size:13px;color:#475569}
#ts-app input[type=range]{flex:1;min-width:80px;accent-color:#6366f1}
#ts-app input[type=color]{width:36px;height:28px;border:1.5px solid #cbd5e1;border-radius:5px;cursor:pointer;padding:1px}
#ts-app input[type=text]{border:1.5px solid #cbd5e1;border-radius:6px;padding:5px 8px;font-size:13px;width:100%;background:#fff}
#ts-app select{border:1.5px solid #cbd5e1;border-radius:6px;padding:5px 8px;font-size:13px;background:#fff;cursor:pointer}
#ts-app .ts-val{min-width:36px;text-align:right;font-size:12px;color:#64748b}
#ts-app .ts-btn{display:inline-flex;align-items:center;gap:6px;padding:8px 16px;border-radius:7px;font-size:13px;font-weight:600;border:none;cursor:pointer;transition:opacity .15s}
#ts-app .ts-btn-primary{background:#6366f1;color:#fff}
#ts-app .ts-btn-primary:hover{opacity:.88}
#ts-app .ts-btn-sm{padding:5px 11px;font-size:12px;background:#fff;border:1.5px solid #cbd5e1;color:#374151;border-radius:6px}
#ts-app .ts-btn-sm:hover{background:#f1f5f9}
#ts-app .ts-btn-danger{background:#fff;border:1.5px solid #fca5a5;color:#dc2626;padding:5px 10px;font-size:12px;border-radius:6px}
#ts-app .ts-btn-danger:hover{background:#fef2f2}
#ts-app .ts-layers{display:flex;flex-direction:column;gap:8px;margin-bottom:12px}
#ts-app .ts-layer-card{background:#fff;border:1.5px solid #e2e8f0;border-radius:8px;padding:12px}
#ts-app .ts-layer-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
#ts-app .ts-layer-title{font-size:13px;font-weight:600;color:#334155}
#ts-app .ts-presets{display:flex;flex-wrap:wrap;gap:7px;margin-bottom:14px}
#ts-app .ts-preset-btn{padding:6px 13px;border-radius:20px;border:1.5px solid #cbd5e1;background:#fff;font-size:12px;font-weight:600;cursor:pointer;transition:border-color .15s,background .15s}
#ts-app .ts-preset-btn:hover{border-color:#6366f1;background:#eef2ff}
#ts-app .ts-code-wrap{position:relative;background:#0f172a;border-radius:8px;padding:14px 14px 14px 14px;margin-top:4px}
#ts-app .ts-code{color:#7dd3fc;font-family:'Courier New',monospace;font-size:12.5px;word-break:break-all;white-space:pre-wrap;line-height:1.6}
#ts-app .ts-copy-btn{position:absolute;top:10px;right:10px;padding:5px 12px;background:#6366f1;color:#fff;border:none;border-radius:6px;font-size:12px;font-weight:600;cursor:pointer}
#ts-app .ts-copy-btn:hover{background:#4f46e5}
#ts-app .ts-copy-btn.copied{background:#10b981}
#ts-app .ts-preview-controls{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:14px;align-items:center}
#ts-app .ts-preview-controls label{font-size:13px;color:#475569}
#ts-app .ts-sep{border:none;border-top:1.5px solid #e2e8f0;margin:14px 0}
#ts-app .ts-add-row{display:flex;gap:8px;flex-wrap:wrap;align-items:center}
</style>

<!-- Preview Controls -->
<div class="ts-panel" style="margin-bottom:16px">
<h2>Live Preview</h2>
<div class="ts-preview-wrap" id="ts-preview-bg">
<span id="ts-preview-text">Text Shadow</span>
</div>
<div class="ts-preview-controls">
<label>Text:</label>
<input type="text" id="ts-input-text" value="Text Shadow" style="width:160px">
<label>Color:</label>
<input type="color" id="ts-input-textcolor" value="#ffffff">
<label>Size:</label>
<input type="range" id="ts-input-fontsize" min="16" max="96" value="52" style="width:100px">
<span class="ts-val" id="ts-fontsize-val">52px</span>
<label>BG:</label>
<input type="color" id="ts-input-bg" value="#1e293b">
</div>
</div>

<!-- Presets -->
<div class="ts-panel" style="margin-bottom:16px">
<h2>Presets</h2>
<div class="ts-presets" id="ts-presets"></div>
</div>

<!-- Shadow Layers + CSS Output -->
<div class="ts-grid">
<div class="ts-panel">
<h2>Shadow Layers</h2>
<div class="ts-layers" id="ts-layers"></div>
<div class="ts-add-row">
<button class="ts-btn ts-btn-primary" onclick="tsAddLayer()">+ Add Layer</button>
</div>
</div>
<div class="ts-panel">
<h2>Generated CSS</h2>
<div class="ts-code-wrap">
<pre class="ts-code" id="ts-css-out"></pre>
<button class="ts-copy-btn" id="ts-copy-btn" onclick="tsCopy()">Copy</button>
</div>
</div>
</div>

<script>
(function(){
var layers=[];
var lid=0;

var PRESETS=[
{name:"Neon Glow",layers:[
{h:0,v:0,b:4,c:"#ff00ff",a:1},
{h:0,v:0,b:16,c:"#ff00ff",a:.8},
{h:0,v:0,b:32,c:"#ff00ff",a:.4}
],bg:"#0a0a1a",tc:"#ff00ff",fs:52},
{name:"Emboss",layers:[
{h:-2,v:-2,b:4,c:"#ffffff",a:.9},
{h:2,v:2,b:4,c:"#000000",a:.4}
],bg:"#c0c8d8",tc:"#c0c8d8",fs:52},
{name:"Retro",layers:[
{h:3,v:3,b:0,c:"#f97316",a:1},
{h:6,v:6,b:0,c:"#ef4444",a:1}
],bg:"#fef9c3",tc:"#1e293b",fs:52},
{name:"Fire",layers:[
{h:0,v:-4,b:8,c:"#fbbf24",a:1},
{h:0,v:-8,b:16,c:"#f97316",a:.9},
{h:0,v:-16,b:24,c:"#ef4444",a:.6},
{h:0,v:-24,b:32,c:"#dc2626",a:.3}
],bg:"#18181b",tc:"#fef9c3",fs:52},
{name:"3D",layers:[
{h:1,v:1,b:0,c:"#475569",a:1},
{h:2,v:2,b:0,c:"#64748b",a:1},
{h:3,v:3,b:0,c:"#94a3b8",a:1},
{h:4,v:4,b:0,c:"#cbd5e1",a:1}
],bg:"#1e293b",tc:"#f8fafc",fs:52},
{name:"Outline",layers:[
{h:1,v:0,b:0,c:"#000000",a:1},
{h:-1,v:0,b:0,c:"#000000",a:1},
{h:0,v:1,b:0,c:"#000000",a:1},
{h:0,v:-1,b:0,c:"#000000",a:1}
],bg:"#f8fafc",tc:"#6366f1",fs:52}
];

function hexToRgba(hex,a){
var r=parseInt(hex.slice(1,3),16),g=parseInt(hex.slice(3,5),16),b=parseInt(hex.slice(5,7),16);
return a<1?'rgba('+r+','+g+','+b+','+a+')':'rgb('+r+','+g+','+b+')';
}

function makeCss(){
if(!layers.length)return'text-shadow: none;';
var parts=layers.map(function(l){
return l.h+'px '+l.v+'px '+l.b+'px '+hexToRgba(l.c,l.a);
});
return'text-shadow:\n  '+parts.join(',\n  ')+';';
}

function applyPreview(){
var text=document.getElementById('ts-input-text').value||'Text Shadow';
var tc=document.getElementById('ts-input-textcolor').value;
var fs=document.getElementById('ts-input-fontsize').value;
var bg=document.getElementById('ts-input-bg').value;
document.getElementById('ts-fontsize-val').textContent=fs+'px';
var el=document.getElementById('ts-preview-text');
el.textContent=text;
el.style.color=tc;
el.style.fontSize=fs+'px';
el.style.textShadow=layers.map(function(l){
return l.h+'px '+l.v+'px '+l.b+'px '+hexToRgba(l.c,l.a);
}).join(', ')||'none';
document.getElementById('ts-preview-bg').style.background=bg;
document.getElementById('ts-css-out').textContent=makeCss();
}

function renderLayers(){
var cont=document.getElementById('ts-layers');
cont.innerHTML='';
if(!layers.length){
cont.innerHTML='<p style="color:#94a3b8;font-size:13px;text-align:center;padding:16px 0;">No layers yet. Add one or pick a preset.</p>';
return;
}
layers.forEach(function(l,i){
var d=document.createElement('div');
d.className='ts-layer-card';
d.innerHTML='<div class="ts-layer-header"><span class="ts-layer-title">Layer '+(i+1)+'</span><button class="ts-btn ts-btn-danger" onclick="tsRemoveLayer('+l.id+')">Remove</button></div>'+
'<div class="ts-ctrl-row"><label>Horizontal</label><input type="range" min="-50" max="50" value="'+l.h+'" oninput="tsLayerChange('+l.id+',\'h\',this.value);document.getElementById(\'ts-h-val-'+l.id+'\').textContent=this.value+\'px\'"><span class="ts-val" id="ts-h-val-'+l.id+'">'+l.h+'px</span></div>'+
'<div class="ts-ctrl-row"><label>Vertical</label><input type="range" min="-50" max="50" value="'+l.v+'" oninput="tsLayerChange('+l.id+',\'v\',this.value);document.getElementById(\'ts-v-val-'+l.id+'\').textContent=this.value+\'px\'"><span class="ts-val" id="ts-v-val-'+l.id+'">'+l.v+'px</span></div>'+
'<div class="ts-ctrl-row"><label>Blur</label><input type="range" min="0" max="60" value="'+l.b+'" oninput="tsLayerChange('+l.id+',\'b\',this.value);document.getElementById(\'ts-b-val-'+l.id+'\').textContent=this.value+\'px\'"><span class="ts-val" id="ts-b-val-'+l.id+'">'+l.b+'px</span></div>'+
'<div class="ts-ctrl-row"><label>Color</label><input type="color" value="'+l.c+'" oninput="tsLayerChange('+l.id+',\'c\',this.value)"></div>'+
'<div class="ts-ctrl-row"><label>Opacity</label><input type="range" min="0" max="1" step="0.01" value="'+l.a+'" oninput="tsLayerChange('+l.id+',\'a\',parseFloat(this.value));document.getElementById(\'ts-a-val-'+l.id+'\').textContent=parseFloat(this.value).toFixed(2)"><span class="ts-val" id="ts-a-val-'+l.id+'">'+l.a.toFixed(2)+'</span></div>';
cont.appendChild(d);
});
}

window.tsAddLayer=function(){
layers.push({id:lid++,h:2,v:2,b:4,c:'#000000',a:0.5});
renderLayers();applyPreview();
};

window.tsRemoveLayer=function(id){
layers=layers.filter(function(l){return l.id!==id;});
renderLayers();applyPreview();
};

window.tsLayerChange=function(id,prop,val){
var l=layers.find(function(x){return x.id===id;});
if(l){l[prop]=prop==='h'||prop==='v'||prop==='b'?parseInt(val,10):val;}
applyPreview();
};

window.tsCopy=function(){
var txt=makeCss();
if(navigator.clipboard){navigator.clipboard.writeText(txt);}else{var ta=document.createElement('textarea');ta.value=txt;document.body.appendChild(ta);ta.select();document.execCommand('copy');document.body.removeChild(ta);}
var btn=document.getElementById('ts-copy-btn');
btn.textContent='Copied!';btn.classList.add('copied');
setTimeout(function(){btn.textContent='Copy';btn.classList.remove('copied');},1800);
};

// Render presets
var pb=document.getElementById('ts-presets');
PRESETS.forEach(function(p){
var b=document.createElement('button');
b.className='ts-preset-btn';b.textContent=p.name;
b.onclick=function(){
layers=p.layers.map(function(l,i){return Object.assign({id:lid++},l);});
document.getElementById('ts-input-bg').value=p.bg;
document.getElementById('ts-input-textcolor').value=p.tc;
document.getElementById('ts-input-fontsize').value=p.fs;
document.getElementById('ts-fontsize-val').textContent=p.fs+'px';
renderLayers();applyPreview();
};
pb.appendChild(b);
});

// Wire preview controls
['ts-input-text','ts-input-textcolor','ts-input-fontsize','ts-input-bg'].forEach(function(id){
document.getElementById(id).addEventListener('input',applyPreview);
});

// Init with Neon Glow
(function(){
var p=PRESETS[0];
layers=p.layers.map(function(l){return Object.assign({id:lid++},l);});
document.getElementById('ts-input-bg').value=p.bg;
document.getElementById('ts-input-textcolor').value=p.tc;
document.getElementById('ts-input-fontsize').value=p.fs;
document.getElementById('ts-fontsize-val').textContent=p.fs+'px';
renderLayers();applyPreview();
})();
})();
</script>
</div>

---

## How to use

1. **Add layers** — click "Add Layer" or choose a preset to load shadow layers instantly.
2. **Adjust each layer** — slide Horizontal, Vertical, Blur, Color, and Opacity controls.
3. **Customize preview** — change the preview text, its color, font size, and background.
4. **Copy CSS** — click "Copy" and paste the `text-shadow` rule into your stylesheet.

## Presets explained

| Preset | Effect |
|---|---|
| Neon Glow | Multi-layered glow using identical hue with expanding blur |
| Emboss | Light + dark shadows to create a pressed/raised look |
| Retro | Hard stacked shadows giving a vintage print feel |
| Fire | Upward blur layers from yellow to deep red |
| 3D | Stepped solid shadows building depth and dimension |
| Outline | Four single-pixel shadows forming a clean text stroke |

## CSS `text-shadow` syntax

```css
text-shadow: h-offset v-offset blur color, /* layer 1 */
h-offset v-offset blur color; /* layer 2 */
```

- **h-offset** — horizontal shift (negative = left, positive = right)
- **v-offset** — vertical shift (negative = up, positive = down)
- **blur** — blur radius in px (0 = sharp)
- **color** — any valid CSS color including `rgba()` for transparency

Multiple shadows are comma-separated and stack front-to-back.

---

## Related tools

- [Box Shadow Generator](/tools/box-shadow-generator/) — Generate `box-shadow` CSS for elements and cards
- [Text Gradient Generator](/tools/text-gradient-generator/) — Create `background-clip` text gradients with live preview
