---
title: "Image Color Picker"
slug: "image-color-picker"
date: 2025-05-16
description: "Free image color picker. Upload any image and click to extract colors in HEX, RGB, and HSL. Build a palette from your photos — no sign-up required."
categories: ["Free Tools"]
ShowToc: false
cover:
  image: /images/covers/image-color-picker.png
  alt: "Image Color Picker tool — extract colors from any photo in HEX, RGB, and HSL"
---

Upload any image and click to extract exact colors in HEX, RGB, and HSL — instantly, in your browser. No account, no installs, no data ever leaves your device.

**Related tools:** [Color Picker](/tools/color-picker/) · [Color Palette Generator](/tools/color-palette-generator/) · [Color Converter](/tools/color-converter/)

---

<div id="icp-app">
<style>
#icp-app *,#icp-app *::before,#icp-app *::after{box-sizing:border-box;margin:0;padding:0}
#icp-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b !important;color-scheme:light;background:#f8fafc;border-radius:14px;padding:24px;max-width:860px;margin:0 auto}
#icp-app h2{font-size:18px;font-weight:700;margin-bottom:4px}
#icp-drop-zone{border:2.5px dashed #94a3b8;border-radius:12px;background:#fff;min-height:200px;display:flex;flex-direction:column;align-items:center;justify-content:center;cursor:pointer;transition:border-color .2s,background .2s;position:relative;overflow:hidden;margin-bottom:16px}
#icp-drop-zone.drag-over{border-color:#6366f1;background:#eef2ff}
#icp-drop-zone.has-image{min-height:unset;cursor:crosshair}
#icp-drop-label{display:flex;flex-direction:column;align-items:center;gap:10px;color:#64748b;pointer-events:none;user-select:none}
#icp-drop-label svg{width:48px;height:48px;opacity:.5}
#icp-drop-label span{font-size:15px}
#icp-drop-label small{font-size:12px;color:#94a3b8}
#icp-file-input{display:none}
#icp-browse-btn{pointer-events:auto;padding:8px 20px;background:#6366f1;color:#fff;border:none;border-radius:7px;font-size:13px;font-weight:600;cursor:pointer;transition:background .15s}
#icp-browse-btn:hover{background:#4f46e5}
#icp-canvas-wrap{position:relative;display:inline-block;width:100%;line-height:0}
#icp-canvas{display:block;width:100%;height:auto;cursor:crosshair;border-radius:8px}
#icp-magnifier{position:absolute;width:96px;height:96px;border-radius:50%;border:3px solid #6366f1;box-shadow:0 4px 20px rgba(0,0,0,.35);pointer-events:none;overflow:hidden;display:none;background:#000;z-index:10}
#icp-mag-canvas{position:absolute;top:0;left:0}
#icp-mag-crosshair{position:absolute;top:50%;left:50%;width:12px;height:12px;transform:translate(-50%,-50%);pointer-events:none}
#icp-mag-crosshair::before,#icp-mag-crosshair::after{content:'';position:absolute;background:rgba(255,255,255,.9)}
#icp-mag-crosshair::before{width:1.5px;height:100%;left:50%;transform:translateX(-50%)}
#icp-mag-crosshair::after{height:1.5px;width:100%;top:50%;transform:translateY(-50%)}
#icp-result-row{display:flex;gap:14px;margin-bottom:16px;flex-wrap:wrap;align-items:stretch}
#icp-color-preview{width:90px;min-height:90px;border-radius:10px;border:2px solid #e2e8f0;flex-shrink:0;background:#e2e8f0;transition:background .15s}
#icp-formats{flex:1;display:flex;flex-direction:column;gap:8px;min-width:200px}
.icp-format-row{display:flex;align-items:center;gap:8px}
.icp-format-label{font-size:11px;font-weight:700;color:#64748b;text-transform:uppercase;letter-spacing:.05em;width:34px;flex-shrink:0}
.icp-format-val{flex:1;font-size:13px;font-family:'SFMono-Regular',Consolas,monospace;background:#f1f5f9;padding:6px 10px;border-radius:6px;border:1px solid #e2e8f0;color:#1e293b;overflow:hidden;white-space:nowrap;text-overflow:ellipsis}
.icp-copy-btn{padding:5px 12px;font-size:12px;font-weight:600;background:#6366f1;color:#fff;border:none;border-radius:5px;cursor:pointer;transition:background .15s,transform .1s;white-space:nowrap;flex-shrink:0}
.icp-copy-btn:hover{background:#4f46e5}
.icp-copy-btn.copied{background:#22c55e;transform:scale(1.05)}
#icp-name-row{font-size:13px;color:#64748b;margin-top:4px}
#icp-name-row span{font-weight:600;color:#1e293b}
#icp-history-section{margin-top:4px}
#icp-history-section h3{font-size:14px;font-weight:700;color:#475569;margin-bottom:8px}
#icp-swatches{display:flex;flex-wrap:wrap;gap:8px}
.icp-swatch{width:36px;height:36px;border-radius:7px;border:2px solid #e2e8f0;cursor:pointer;transition:transform .15s,box-shadow .15s;flex-shrink:0;position:relative}
.icp-swatch:hover{transform:scale(1.18);box-shadow:0 4px 12px rgba(0,0,0,.2);z-index:5}
.icp-swatch-tip{display:none;position:absolute;bottom:calc(100% + 6px);left:50%;transform:translateX(-50%);background:#1e293b;color:#fff;font-size:11px;padding:3px 7px;border-radius:4px;white-space:nowrap;pointer-events:none;z-index:20}
.icp-swatch:hover .icp-swatch-tip{display:block}
#icp-export-row{display:flex;gap:10px;margin-top:16px;flex-wrap:wrap}
.icp-export-btn{padding:8px 18px;font-size:13px;font-weight:600;border-radius:7px;cursor:pointer;border:1.5px solid #6366f1;transition:background .15s,color .15s}
#icp-export-css{background:#6366f1;color:#fff}
#icp-export-css:hover{background:#4f46e5}
#icp-export-json{background:#fff;color:#6366f1}
#icp-export-json:hover{background:#eef2ff}
#icp-export-out{display:none;margin-top:12px;background:#1e293b;color:#e2e8f0;border-radius:8px;padding:14px 16px;font-family:'SFMono-Regular',Consolas,monospace;font-size:12px;white-space:pre-wrap;word-break:break-all;position:relative;max-height:220px;overflow-y:auto}
#icp-export-copy{position:absolute;top:8px;right:8px;padding:4px 10px;font-size:11px;font-weight:600;background:#6366f1;color:#fff;border:none;border-radius:4px;cursor:pointer}
#icp-export-copy:hover{background:#4f46e5}
#icp-instructions{font-size:13px;color:#64748b;margin-bottom:10px;display:none}
#icp-no-pick-msg{font-size:13px;color:#94a3b8;font-style:italic;margin-top:6px}
@media(max-width:520px){
#icp-result-row{flex-direction:column}
#icp-color-preview{width:100%;min-height:60px}
#icp-magnifier{width:72px;height:72px}
}
</style>

<div style="margin-bottom:12px">
<input type="file" id="icp-file-input" accept="image/*">
<div id="icp-drop-zone">
<div id="icp-drop-label">
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="3"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="M21 15l-5-5L5 21"/></svg>
<span>Drop image here or</span>
<button id="icp-browse-btn" type="button">Browse file</button>
<small>PNG, JPG, GIF, WebP, SVG — stays in your browser</small>
</div>
</div>
</div>

<div id="icp-instructions">Click anywhere on the image to pick a color. Hover to see the magnifier.</div>

<div id="icp-canvas-wrap" style="display:none">
<canvas id="icp-canvas"></canvas>
<div id="icp-magnifier">
<canvas id="icp-mag-canvas"></canvas>
<div id="icp-mag-crosshair"></div>
</div>
</div>

<div id="icp-no-pick-msg" style="display:none">No color picked yet — click the image above.</div>

<div id="icp-result-row" style="display:none">
<div id="icp-color-preview"></div>
<div id="icp-formats">
<div class="icp-format-row">
<span class="icp-format-label">HEX</span>
<span class="icp-format-val" id="icp-hex">—</span>
<button class="icp-copy-btn" data-target="icp-hex">Copy</button>
</div>
<div class="icp-format-row">
<span class="icp-format-label">RGB</span>
<span class="icp-format-val" id="icp-rgb">—</span>
<button class="icp-copy-btn" data-target="icp-rgb">Copy</button>
</div>
<div class="icp-format-row">
<span class="icp-format-label">HSL</span>
<span class="icp-format-val" id="icp-hsl">—</span>
<button class="icp-copy-btn" data-target="icp-hsl">Copy</button>
</div>
<div id="icp-name-row">Nearest name: <span id="icp-name">—</span></div>
</div>
</div>

<div id="icp-history-section" style="display:none">
<h3>Picked Colors <span id="icp-count" style="font-weight:400;color:#94a3b8;font-size:12px"></span></h3>
<div id="icp-swatches"></div>
<div id="icp-export-row">
<button class="icp-export-btn" id="icp-export-css" type="button">Export as CSS Variables</button>
<button class="icp-export-btn" id="icp-export-json" type="button">Export as JSON</button>
</div>
<div id="icp-export-out"><button id="icp-export-copy" type="button">Copy</button><span id="icp-export-text"></span></div>
</div>

<script>
(function(){
'use strict';
var dropZone=document.getElementById('icp-drop-zone');
var fileInput=document.getElementById('icp-file-input');
var browseBtn=document.getElementById('icp-browse-btn');
var canvasWrap=document.getElementById('icp-canvas-wrap');
var canvas=document.getElementById('icp-canvas');
var ctx=canvas.getContext('2d',{willReadFrequently:true});
var mag=document.getElementById('icp-magnifier');
var magCanvas=document.getElementById('icp-mag-canvas');
var magCtx=magCanvas.getContext('2d',{willReadFrequently:true});
var instructions=document.getElementById('icp-instructions');
var nopick=document.getElementById('icp-no-pick-msg');
var resultRow=document.getElementById('icp-result-row');
var preview=document.getElementById('icp-color-preview');
var hexEl=document.getElementById('icp-hex');
var rgbEl=document.getElementById('icp-rgb');
var hslEl=document.getElementById('icp-hsl');
var nameEl=document.getElementById('icp-name');
var historySec=document.getElementById('icp-history-section');
var swatchesEl=document.getElementById('icp-swatches');
var countEl=document.getElementById('icp-count');
var exportOut=document.getElementById('icp-export-out');
var exportText=document.getElementById('icp-export-text');
var exportCopy=document.getElementById('icp-export-copy');

var MAG_SIZE=96,MAG_ZOOM=6,MAX_HISTORY=12;
var history=[];
var imgObj=null;
var naturalW=0,naturalH=0;
var hasPicked=false;

magCanvas.width=MAG_SIZE;magCanvas.height=MAG_SIZE;

// CSS named colors (nearest match)
var CSS_COLORS=[
['aliceblue',[240,248,255]],['antiquewhite',[250,235,215]],['aqua',[0,255,255]],
['aquamarine',[127,255,212]],['azure',[240,255,255]],['beige',[245,245,220]],
['bisque',[255,228,196]],['black',[0,0,0]],['blanchedalmond',[255,235,205]],
['blue',[0,0,255]],['blueviolet',[138,43,226]],['brown',[165,42,42]],
['burlywood',[222,184,135]],['cadetblue',[95,158,160]],['chartreuse',[127,255,0]],
['chocolate',[210,105,30]],['coral',[255,127,80]],['cornflowerblue',[100,149,237]],
['cornsilk',[255,248,220]],['crimson',[220,20,60]],['cyan',[0,255,255]],
['darkblue',[0,0,139]],['darkcyan',[0,139,139]],['darkgoldenrod',[184,134,11]],
['darkgray',[169,169,169]],['darkgreen',[0,100,0]],['darkkhaki',[189,183,107]],
['darkmagenta',[139,0,139]],['darkolivegreen',[85,107,47]],['darkorange',[255,140,0]],
['darkorchid',[153,50,204]],['darkred',[139,0,0]],['darksalmon',[233,150,122]],
['darkseagreen',[143,188,143]],['darkslateblue',[72,61,139]],['darkslategray',[47,79,79]],
['darkturquoise',[0,206,209]],['darkviolet',[148,0,211]],['deeppink',[255,20,147]],
['deepskyblue',[0,191,255]],['dimgray',[105,105,105]],['dodgerblue',[30,144,255]],
['firebrick',[178,34,34]],['floralwhite',[255,250,240]],['forestgreen',[34,139,34]],
['fuchsia',[255,0,255]],['gainsboro',[220,220,220]],['ghostwhite',[248,248,255]],
['gold',[255,215,0]],['goldenrod',[218,165,32]],['gray',[128,128,128]],
['green',[0,128,0]],['greenyellow',[173,255,47]],['honeydew',[240,255,240]],
['hotpink',[255,105,180]],['indianred',[205,92,92]],['indigo',[75,0,130]],
['ivory',[255,255,240]],['khaki',[240,230,140]],['lavender',[230,230,250]],
['lavenderblush',[255,240,245]],['lawngreen',[124,252,0]],['lemonchiffon',[255,250,205]],
['lightblue',[173,216,230]],['lightcoral',[240,128,128]],['lightcyan',[224,255,255]],
['lightgoldenrodyellow',[250,250,210]],['lightgray',[211,211,211]],['lightgreen',[144,238,144]],
['lightpink',[255,182,193]],['lightsalmon',[255,160,122]],['lightseagreen',[32,178,170]],
['lightskyblue',[135,206,250]],['lightslategray',[119,136,153]],['lightsteelblue',[176,196,222]],
['lightyellow',[255,255,224]],['lime',[0,255,0]],['limegreen',[50,205,50]],
['linen',[250,240,230]],['magenta',[255,0,255]],['maroon',[128,0,0]],
['mediumaquamarine',[102,205,170]],['mediumblue',[0,0,205]],['mediumorchid',[186,85,211]],
['mediumpurple',[147,112,219]],['mediumseagreen',[60,179,113]],['mediumslateblue',[123,104,238]],
['mediumspringgreen',[0,250,154]],['mediumturquoise',[72,209,204]],['mediumvioletred',[199,21,133]],
['midnightblue',[25,25,112]],['mintcream',[245,255,250]],['mistyrose',[255,228,225]],
['moccasin',[255,228,181]],['navajowhite',[255,222,173]],['navy',[0,0,128]],
['oldlace',[253,245,230]],['olive',[128,128,0]],['olivedrab',[107,142,35]],
['orange',[255,165,0]],['orangered',[255,69,0]],['orchid',[218,112,214]],
['palegoldenrod',[238,232,170]],['palegreen',[152,251,152]],['paleturquoise',[175,238,238]],
['palevioletred',[219,112,147]],['papayawhip',[255,239,213]],['peachpuff',[255,218,185]],
['peru',[205,133,63]],['pink',[255,192,203]],['plum',[221,160,221]],
['powderblue',[176,224,230]],['purple',[128,0,128]],['rebeccapurple',[102,51,153]],
['red',[255,0,0]],['rosybrown',[188,143,143]],['royalblue',[65,105,225]],
['saddlebrown',[139,69,19]],['salmon',[250,128,114]],['sandybrown',[244,164,96]],
['seagreen',[46,139,87]],['seashell',[255,245,238]],['sienna',[160,82,45]],
['silver',[192,192,192]],['skyblue',[135,206,235]],['slateblue',[106,90,205]],
['slategray',[112,128,144]],['snow',[255,250,250]],['springgreen',[0,255,127]],
['steelblue',[70,130,180]],['tan',[210,180,140]],['teal',[0,128,128]],
['thistle',[216,191,216]],['tomato',[255,99,71]],['turquoise',[64,224,208]],
['violet',[238,130,238]],['wheat',[245,222,179]],['white',[255,255,255]],
['whitesmoke',[245,245,245]],['yellow',[255,255,0]],['yellowgreen',[154,205,50]]
];

function colorDist(a,b){var dr=a[0]-b[0],dg=a[1]-b[1],db=a[2]-b[2];return dr*dr+dg*dg+db*db;}
function nearestName(r,g,b){var best=CSS_COLORS[0][0],bd=Infinity;for(var i=0;i<CSS_COLORS.length;i++){var d=colorDist([r,g,b],CSS_COLORS[i][1]);if(d<bd){bd=d;best=CSS_COLORS[i][0];}}return best;}

function toHex(r,g,b){return '#'+[r,g,b].map(function(v){return v.toString(16).padStart(2,'0');}).join('');}
function toRgb(r,g,b){return 'rgb('+r+', '+g+', '+b+')';}
function toHsl(r,g,b){
var rn=r/255,gn=g/255,bn=b/255;
var max=Math.max(rn,gn,bn),min=Math.min(rn,gn,bn),h,s,l=(max+min)/2;
if(max===min){h=s=0;}else{
var d=max-min;s=l>0.5?d/(2-max-min):d/(max+min);
if(max===rn)h=((gn-bn)/d+(gn<bn?6:0))/6;
else if(max===gn)h=((bn-rn)/d+2)/6;
else h=((rn-gn)/d+4)/6;
}
return 'hsl('+Math.round(h*360)+', '+Math.round(s*100)+'%, '+Math.round(l*100)+'%)';
}

function loadImage(file){
var url=URL.createObjectURL(file);
var img=new Image();
img.onload=function(){
imgObj=img;naturalW=img.naturalWidth;naturalH=img.naturalHeight;
canvas.width=naturalW;canvas.height=naturalH;
ctx.drawImage(img,0,0);
dropZone.style.display='none';
canvasWrap.style.display='block';
instructions.style.display='block';
nopick.style.display='block';
URL.revokeObjectURL(url);
};
img.src=url;
}

browseBtn.addEventListener('click',function(){fileInput.click();});
fileInput.addEventListener('change',function(){if(fileInput.files[0])loadImage(fileInput.files[0]);});

dropZone.addEventListener('dragover',function(e){e.preventDefault();dropZone.classList.add('drag-over');});
dropZone.addEventListener('dragleave',function(){dropZone.classList.remove('drag-over');});
dropZone.addEventListener('drop',function(e){
e.preventDefault();dropZone.classList.remove('drag-over');
var f=e.dataTransfer.files[0];if(f&&f.type.startsWith('image/'))loadImage(f);
});

function getPixel(e){
var rect=canvas.getBoundingClientRect();
var scaleX=naturalW/rect.width,scaleY=naturalH/rect.height;
var cx=Math.round((e.clientX-rect.left)*scaleX);
var cy=Math.round((e.clientY-rect.top)*scaleY);
cx=Math.max(0,Math.min(naturalW-1,cx));
cy=Math.max(0,Math.min(naturalH-1,cy));
return {x:cx,y:cy,rect:rect,scaleX:scaleX,scaleY:scaleY};
}

function updateMag(e){
if(!imgObj)return;
var p=getPixel(e);
var rect=p.rect;
var half=MAG_SIZE/2;
var srcX=p.x-Math.round(half/MAG_ZOOM),srcY=p.y-Math.round(half/MAG_ZOOM);
var srcW=Math.round(MAG_SIZE/MAG_ZOOM),srcH=Math.round(MAG_SIZE/MAG_ZOOM);
magCtx.clearRect(0,0,MAG_SIZE,MAG_SIZE);
magCtx.imageSmoothingEnabled=false;
magCtx.drawImage(canvas,srcX,srcY,srcW,srcH,0,0,MAG_SIZE,MAG_SIZE);

var mx=e.clientX-rect.left+canvasWrap.getBoundingClientRect().left-canvasWrap.getBoundingClientRect().left;
var relX=e.clientX-canvasWrap.getBoundingClientRect().left;
var relY=e.clientY-canvasWrap.getBoundingClientRect().top;
var offX=relX+20,offY=relY-MAG_SIZE-12;
if(offX+MAG_SIZE>canvasWrap.offsetWidth-4)offX=relX-MAG_SIZE-20;
if(offY<4)offY=relY+20;
mag.style.left=offX+'px';
mag.style.top=offY+'px';
mag.style.display='block';
}

canvas.addEventListener('mousemove',function(e){
if(!imgObj)return;
updateMag(e);
});
canvas.addEventListener('mouseleave',function(){mag.style.display='none';});

canvas.addEventListener('click',function(e){
if(!imgObj)return;
var p=getPixel(e);
var data=ctx.getImageData(p.x,p.y,1,1).data;
var r=data[0],g=data[1],b=data[2];
var hex=toHex(r,g,b);
var rgb=toRgb(r,g,b);
var hsl=toHsl(r,g,b);
var name=nearestName(r,g,b);

preview.style.background=hex;
hexEl.textContent=hex;
rgbEl.textContent=rgb;
hslEl.textContent=hsl;
nameEl.textContent=name;

if(!hasPicked){
nopick.style.display='none';
resultRow.style.display='flex';
historySec.style.display='block';
hasPicked=true;
}

// Add to history
if(history.length===0||history[0]!==hex){
history.unshift(hex);
if(history.length>MAX_HISTORY)history.pop();
renderSwatches();
}
});

function renderSwatches(){
swatchesEl.innerHTML='';
countEl.textContent='('+history.length+')';
history.forEach(function(h,i){
var sw=document.createElement('div');
sw.className='icp-swatch';
sw.style.background=h;
sw.title=h;
var tip=document.createElement('div');
tip.className='icp-swatch-tip';
tip.textContent=h;
sw.appendChild(tip);
sw.addEventListener('click',function(){
preview.style.background=h;
var rgb2=hexToRgb(h);
hexEl.textContent=h;
rgbEl.textContent=toRgb(rgb2[0],rgb2[1],rgb2[2]);
hslEl.textContent=toHsl(rgb2[0],rgb2[1],rgb2[2]);
nameEl.textContent=nearestName(rgb2[0],rgb2[1],rgb2[2]);
});
swatchesEl.appendChild(sw);
});
}

function hexToRgb(h){
var r=parseInt(h.slice(1,3),16),g=parseInt(h.slice(3,5),16),b=parseInt(h.slice(5,7),16);
return [r,g,b];
}

document.querySelectorAll('.icp-copy-btn').forEach(function(btn){
btn.addEventListener('click',function(){
var val=document.getElementById(btn.dataset.target).textContent;
navigator.clipboard.writeText(val).then(function(){
btn.textContent='Copied!';btn.classList.add('copied');
setTimeout(function(){btn.textContent='Copy';btn.classList.remove('copied');},1400);
});
});
});

document.getElementById('icp-export-css').addEventListener('click',function(){
if(!history.length)return;
var lines=history.map(function(h,i){return '  --color-'+(i+1)+': '+h+';';});
var out=':root {\n'+lines.join('\n')+'\n}';
exportText.textContent=out;
exportOut.style.display='block';
});
document.getElementById('icp-export-json').addEventListener('click',function(){
if(!history.length)return;
var obj=Object.fromEntries(history.map(function(h,i){return ['color'+(i+1),h];}));
exportText.textContent=JSON.stringify(obj,null,2);
exportOut.style.display='block';
});
exportCopy.addEventListener('click',function(){
navigator.clipboard.writeText(exportText.textContent).then(function(){
exportCopy.textContent='Copied!';
setTimeout(function(){exportCopy.textContent='Copy';},1400);
});
});

})();
</script>
</div>

---

## How It Works

1. **Upload** — drag an image onto the canvas or click "Browse file."
2. **Hover** — a magnifier circle shows a zoomed view for pixel-perfect picking.
3. **Click** — instantly see HEX, RGB, HSL, and the nearest CSS color name.
4. **History** — up to 12 swatches are saved. Click any swatch to reload its values.
5. **Export** — download your palette as CSS custom properties or a JSON object.

Everything runs locally in your browser. No image data is sent anywhere.

---

## Tips

- **Zoom in first** — use your browser's native zoom (Ctrl/Cmd +) if you need finer control before clicking.
- **SVG images** — SVGs are supported if the browser can render them to a canvas (same-origin or inline SVGs without `<foreignObject>`).
- **Transparent pixels** — fully transparent areas return `rgb(0, 0, 0)` since canvas composites against black by default.
- **Export CSS variables** — paste directly into your `:root {}` block and reference colors as `var(--color-1)` throughout your stylesheet.

---

**More color tools:** [Color Picker](/tools/color-picker/) · [Color Palette Generator](/tools/color-palette-generator/) · [Color Converter](/tools/color-converter/)
