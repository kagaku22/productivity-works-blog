---
title: "Color Palette Generator — Free Online Tool"
description: "Generate beautiful 5-color palettes from any base color using color theory. Complementary, analogous, triadic, and more harmony modes. Copy HEX/RGB, export CSS variables, lock colors."
date: 2025-05-16
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "color-palette-generator"
ShowToc: false
aliases:
  - "/tools/color-palette-generator/"
  - "/tools/color-scheme-generator/"
cover:
  image: "/images/covers/color-palette-generator.png"
  alt: "Color Palette Generator"
---

<div id="pal-app">

<style>
#pal-app *,#pal-app *::before,#pal-app *::after{box-sizing:border-box;margin:0;padding:0}
#pal-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1a1a2e;--accent:#6c63ff;--radius:10px;--shadow:0 4px 24px rgba(0,0,0,.10)}
#pal-app .pa-wrap{max-width:820px;margin:0 auto;padding:0 0 48px}
#pal-app .pa-lead{font-size:.97rem;color:#555;margin-bottom:24px;line-height:1.6}

/* Controls */
#pal-app .pa-controls{display:flex;flex-wrap:wrap;gap:12px;align-items:flex-end;margin-bottom:28px;background:#f7f7fc;border-radius:var(--radius);padding:20px}
#pal-app .pa-group{display:flex;flex-direction:column;gap:6px}
#pal-app .pa-group label{font-size:.78rem;font-weight:600;color:#444;text-transform:uppercase;letter-spacing:.04em}
#pal-app .pa-color-pick{width:60px;height:44px;border:2px solid #ddd;border-radius:8px;cursor:pointer;padding:2px;background:#fff}
#pal-app .pa-select{height:44px;padding:0 12px;border:2px solid #ddd;border-radius:8px;font-size:.9rem;background:#fff;cursor:pointer;outline:none;transition:border-color .2s}
#pal-app .pa-select:focus{border-color:var(--accent)}
#pal-app .pa-btn{height:44px;padding:0 22px;border:none;border-radius:8px;font-size:.9rem;font-weight:600;cursor:pointer;transition:transform .1s,opacity .2s}
#pal-app .pa-btn:active{transform:scale(.97)}
#pal-app .pa-btn-primary{background:var(--accent);color:#fff}
#pal-app .pa-btn-primary:hover{opacity:.88}
#pal-app .pa-btn-secondary{background:#fff;color:#333;border:2px solid #ddd}
#pal-app .pa-btn-secondary:hover{border-color:#aaa}
#pal-app .pa-btn-random{background:#ff6584;color:#fff}
#pal-app .pa-btn-random:hover{opacity:.88}

/* Strip */
#pal-app .pa-strip{display:flex;border-radius:var(--radius);overflow:hidden;height:80px;margin-bottom:20px;box-shadow:var(--shadow)}
#pal-app .pa-strip-swatch{flex:1;transition:flex .3s}

/* Cards */
#pal-app .pa-cards{display:grid;grid-template-columns:repeat(5,1fr);gap:12px;margin-bottom:28px}
@media(max-width:600px){#pal-app .pa-cards{grid-template-columns:repeat(2,1fr)}}
#pal-app .pa-card{border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow);background:#fff;transition:transform .18s}
#pal-app .pa-card:hover{transform:translateY(-3px)}
#pal-app .pa-card-swatch{height:120px;position:relative;cursor:pointer}
#pal-app .pa-card-swatch:hover::after{content:'Copy';position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,.22);color:#fff;font-size:.9rem;font-weight:700}
#pal-app .pa-card-swatch::after{display:flex;align-items:center;justify-content:center;font-size:.85rem;font-weight:600;color:transparent;transition:color .2s}
#pal-app .pa-lock-btn{position:absolute;top:8px;right:8px;width:28px;height:28px;border:none;border-radius:50%;background:rgba(255,255,255,.75);cursor:pointer;font-size:14px;display:flex;align-items:center;justify-content:center;backdrop-filter:blur(4px);transition:background .2s}
#pal-app .pa-lock-btn:hover{background:rgba(255,255,255,.95)}
#pal-app .pa-lock-btn.locked{background:rgba(255,255,255,.95)}
#pal-app .pa-card-info{padding:10px 10px 12px;display:flex;flex-direction:column;gap:4px}
#pal-app .pa-hex{font-size:.92rem;font-weight:700;color:#1a1a2e;letter-spacing:.02em}
#pal-app .pa-rgb{font-size:.72rem;color:#888}

/* Toast */
#pal-app .pa-toast{position:fixed;bottom:32px;left:50%;transform:translateX(-50%) translateY(80px);background:#1a1a2e;color:#fff;padding:10px 24px;border-radius:50px;font-size:.88rem;font-weight:600;opacity:0;transition:opacity .25s,transform .25s;z-index:9999;pointer-events:none}
#pal-app .pa-toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* Export */
#pal-app .pa-export{margin-bottom:28px}
#pal-app .pa-export-box{background:#1a1a2e;color:#a8ff78;font-family:'Fira Mono','Courier New',monospace;font-size:.82rem;padding:18px 20px;border-radius:var(--radius);line-height:1.7;white-space:pre;overflow-x:auto}
#pal-app .pa-export-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}
#pal-app .pa-export-header h3{font-size:.95rem;font-weight:700;color:#333}

/* Presets */
#pal-app .pa-presets-title{font-size:.95rem;font-weight:700;color:#333;margin-bottom:12px}
#pal-app .pa-presets{display:flex;flex-wrap:wrap;gap:10px;margin-bottom:32px}
#pal-app .pa-preset{border:2px solid transparent;border-radius:8px;overflow:hidden;cursor:pointer;transition:border-color .2s,transform .18s;width:120px}
#pal-app .pa-preset:hover{border-color:var(--accent);transform:translateY(-2px)}
#pal-app .pa-preset-strip{display:flex;height:28px}
#pal-app .pa-preset-swatch{flex:1}
#pal-app .pa-preset-name{font-size:.7rem;text-align:center;padding:4px;background:#fff;color:#444;font-weight:600}

/* Divider */
#pal-app .pa-divider{border:none;border-top:1px solid #eee;margin:8px 0 24px}

/* Related */
#pal-app .pa-related{font-size:.9rem;color:#555;padding:14px 18px;background:#f7f7fc;border-radius:var(--radius);border-left:4px solid var(--accent)}
#pal-app .pa-related a{color:var(--accent);font-weight:600;text-decoration:none}
#pal-app .pa-related a:hover{text-decoration:underline}
</style>

<div class="pa-wrap">
<p class="pa-lead">Pick a base color, choose a harmony mode, and instantly get a beautiful 5-color palette. Lock any color to keep it while regenerating the rest. Click any swatch to copy its HEX code.</p>

<div class="pa-controls">
<div class="pa-group">
<label>Base Color</label>
<input type="color" id="pa-base-color" class="pa-color-pick" value="#6c63ff">
</div>
<div class="pa-group">
<label>Harmony Mode</label>
<select id="pa-harmony" class="pa-select">
<option value="complementary">Complementary</option>
<option value="analogous">Analogous</option>
<option value="triadic">Triadic</option>
<option value="split-complementary">Split-Complementary</option>
<option value="monochromatic">Monochromatic</option>
</select>
</div>
<button class="pa-btn pa-btn-primary" id="pa-generate-btn">Generate</button>
<button class="pa-btn pa-btn-random" id="pa-random-btn">&#9684; Random</button>
</div>

<div class="pa-strip" id="pa-strip"></div>
<div class="pa-cards" id="pa-cards"></div>

<div class="pa-export">
<div class="pa-export-header">
<h3>CSS Variables Export</h3>
<button class="pa-btn pa-btn-secondary" id="pa-copy-css-btn">Copy CSS</button>
</div>
<div class="pa-export-box" id="pa-css-output"></div>
</div>

<hr class="pa-divider">
<p class="pa-presets-title">Trending Palette Presets</p>
<div class="pa-presets" id="pa-presets"></div>

<div class="pa-toast" id="pa-toast"></div>

<div class="pa-related">
Related: Pick individual colors → <a href="/tools/color-picker/">Color Picker</a>
</div>
</div>

<script>
(function(){
// ── Color math helpers ──────────────────────────────────────────────────
function hexToRgb(hex){
hex=hex.replace(/^#/,'');
if(hex.length===3)hex=hex.split('').map(c=>c+c).join('');
const n=parseInt(hex,16);
return{r:(n>>16)&255,g:(n>>8)&255,b:n&255};
}
function rgbToHex(r,g,b){
return'#'+[r,g,b].map(v=>Math.round(Math.max(0,Math.min(255,v))).toString(16).padStart(2,'0')).join('');
}
function rgbToHsl(r,g,b){
r/=255;g/=255;b/=255;
const max=Math.max(r,g,b),min=Math.min(r,g,b);
let h,s,l=(max+min)/2;
if(max===min){h=s=0;}else{
const d=max-min;
s=l>0.5?d/(2-max-min):d/(max+min);
switch(max){case r:h=(g-b)/d+(g<b?6:0);break;case g:h=(b-r)/d+2;break;case b:h=(r-g)/d+4;break;}
h/=6;
}
return{h:h*360,s:s*100,l:l*100};
}
function hslToRgb(h,s,l){
h/=360;s/=100;l/=100;
let r,g,b;
if(s===0){r=g=b=l;}else{
function hue2rgb(p,q,t){if(t<0)t+=1;if(t>1)t-=1;if(t<1/6)return p+(q-p)*6*t;if(t<1/2)return q;if(t<2/3)return p+(q-p)*(2/3-t)*6;return p;}
const q=l<0.5?l*(1+s):l+s-l*s,p=2*l-q;
r=hue2rgb(p,q,h+1/3);g=hue2rgb(p,q,h);b=hue2rgb(p,q,h-1/3);
}
return{r:Math.round(r*255),g:Math.round(g*255),b:Math.round(b*255)};
}
function hslHex(h,s,l){const{r,g,b}=hslToRgb(h,s,l);return rgbToHex(r,g,b);}
function clampHue(h){return((h%360)+360)%360;}

// ── Harmony generators ──────────────────────────────────────────────────
function generatePalette(baseHex,mode){
const{r,g,b}=hexToRgb(baseHex);
const{h,s,l}=rgbToHsl(r,g,b);
switch(mode){
case'complementary':
return[
baseHex,
hslHex(h,Math.min(s*0.7,100),Math.min(l+15,90)),
hslHex(h,Math.min(s*0.4,100),Math.min(l+30,94)),
hslHex(clampHue(h+180),s,l),
hslHex(clampHue(h+180),Math.min(s*0.7,100),Math.min(l+15,90)),
];
case'analogous':
return[
hslHex(clampHue(h-30),s,l),
hslHex(clampHue(h-15),s,l),
baseHex,
hslHex(clampHue(h+15),s,l),
hslHex(clampHue(h+30),s,l),
];
case'triadic':
return[
baseHex,
hslHex(clampHue(h+120),s,l),
hslHex(clampHue(h+240),s,l),
hslHex(clampHue(h+120),Math.min(s*0.6,100),Math.min(l+18,90)),
hslHex(clampHue(h+240),Math.min(s*0.6,100),Math.min(l+18,90)),
];
case'split-complementary':
return[
baseHex,
hslHex(clampHue(h+150),s,l),
hslHex(clampHue(h+210),s,l),
hslHex(clampHue(h+150),Math.min(s*0.65,100),Math.min(l+20,90)),
hslHex(clampHue(h+210),Math.min(s*0.65,100),Math.min(l+20,90)),
];
case'monochromatic':
default:
return[
hslHex(h,Math.min(s*1.1,100),Math.max(l-30,10)),
hslHex(h,s,Math.max(l-15,10)),
baseHex,
hslHex(h,Math.max(s*0.75,10),Math.min(l+18,90)),
hslHex(h,Math.max(s*0.4,8),Math.min(l+36,94)),
];
}
}

function randomHex(){
return'#'+Math.floor(Math.random()*0xFFFFFF).toString(16).padStart(6,'0');
}

// ── Presets ─────────────────────────────────────────────────────────────
const PRESETS=[
{name:'Neon Sunset',  colors:['#ff6b6b','#ffa36c','#ffd93d','#6bcb77','#4d96ff']},
{name:'Ocean Depth',  colors:['#03045e','#0077b6','#00b4d8','#90e0ef','#caf0f8']},
{name:'Forest Calm',  colors:['#1b4332','#2d6a4f','#52b788','#b7e4c7','#d8f3dc']},
{name:'Berry Bliss',  colors:['#6a0572','#ab83a1','#d6a2e8','#f8a5c2','#ff6b9d']},
{name:'Sand & Stone', colors:['#3d2b1f','#795548','#a1887f','#d7ccc8','#efebe9']},
{name:'Nordic Chill', colors:['#2b2d42','#8d99ae','#edf2f4','#ef233c','#d90429']},
{name:'Citrus Burst', colors:['#ff4800','#ff6d00','#ff9e00','#ffbd00','#ffd500']},
{name:'Lavender Fog', colors:['#7b2d8b','#9b5de5','#c77dff','#e0aaff','#f3d9fa']},
{name:'Midnight Pro', colors:['#0d0d0d','#1a1a2e','#16213e','#0f3460','#533483']},
{name:'Spring Fresh', colors:['#2dc653','#80ed99','#c7f9cc','#ffe5d9','#ff9a76']},
];

// ── State ────────────────────────────────────────────────────────────────
let palette=['#6c63ff','#8b85ff','#d4d2ff','#ff6363','#ff9898'];
let locked=[false,false,false,false,false];
let currentBase='#6c63ff';
let currentMode='complementary';

// ── DOM refs ─────────────────────────────────────────────────────────────
const baseInput=document.getElementById('pa-base-color');
const harmonySelect=document.getElementById('pa-harmony');
const strip=document.getElementById('pa-strip');
const cards=document.getElementById('pa-cards');
const cssOutput=document.getElementById('pa-css-output');
const toast=document.getElementById('pa-toast');
const presetsEl=document.getElementById('pa-presets');

// ── Toast ────────────────────────────────────────────────────────────────
let toastTimer;
function showToast(msg){
toast.textContent=msg;
toast.classList.add('show');
clearTimeout(toastTimer);
toastTimer=setTimeout(()=>toast.classList.remove('show'),1800);
}

// ── Luminance for text contrast ──────────────────────────────────────────
function textColor(hex){
const{r,g,b}=hexToRgb(hex);
const lum=(0.299*r+0.587*g+0.114*b)/255;
return lum>0.55?'#1a1a2e':'#ffffff';
}

// ── Render ────────────────────────────────────────────────────────────────
function render(){
// Strip
strip.innerHTML='';
palette.forEach(c=>{
const s=document.createElement('div');
s.className='pa-strip-swatch';
s.style.background=c;
strip.appendChild(s);
});

// Cards
cards.innerHTML='';
palette.forEach((c,i)=>{
const{r,g,b}=hexToRgb(c);
const card=document.createElement('div');
card.className='pa-card';

const sw=document.createElement('div');
sw.className='pa-card-swatch';
sw.style.background=c;
sw.title='Click to copy '+c;
sw.onclick=()=>{navigator.clipboard.writeText(c).then(()=>showToast('Copied '+c+'!'));};

const lockBtn=document.createElement('button');
lockBtn.className='pa-lock-btn'+(locked[i]?' locked':'');
lockBtn.title=locked[i]?'Unlock color':'Lock color';
lockBtn.innerHTML=locked[i]?'&#128274;':'&#128275;';
lockBtn.onclick=(e)=>{e.stopPropagation();locked[i]=!locked[i];render();};
sw.appendChild(lockBtn);

const info=document.createElement('div');
info.className='pa-card-info';
const hex=document.createElement('div');
hex.className='pa-hex';
hex.textContent=c.toUpperCase();
const rgb=document.createElement('div');
rgb.className='pa-rgb';
rgb.textContent=`rgb(${r}, ${g}, ${b})`;
info.appendChild(hex);
info.appendChild(rgb);

card.appendChild(sw);
card.appendChild(info);
cards.appendChild(card);
});

// CSS export
const varLines=palette.map((c,i)=>`  --color-${i+1}: ${c.toUpperCase()};`).join('\n');
cssOutput.textContent=`:root {\n${varLines}\n}`;
}

function generate(){
const newPalette=generatePalette(currentBase,currentMode);
palette=palette.map((old,i)=>locked[i]?old:newPalette[i]);
render();
}

// ── Event listeners ───────────────────────────────────────────────────────
baseInput.addEventListener('input',e=>{currentBase=e.target.value;generate();});
harmonySelect.addEventListener('change',e=>{currentMode=e.target.value;generate();});
document.getElementById('pa-generate-btn').addEventListener('click',generate);
document.getElementById('pa-random-btn').addEventListener('click',()=>{
currentBase=randomHex();
baseInput.value=currentBase;
locked=[false,false,false,false,false];
generate();
});
document.getElementById('pa-copy-css-btn').addEventListener('click',()=>{
navigator.clipboard.writeText(cssOutput.textContent).then(()=>showToast('CSS copied!'));
});

// ── Presets ───────────────────────────────────────────────────────────────
PRESETS.forEach(p=>{
const el=document.createElement('div');
el.className='pa-preset';
el.title='Load: '+p.name;
const pStrip=document.createElement('div');
pStrip.className='pa-preset-strip';
p.colors.forEach(c=>{const s=document.createElement('div');s.className='pa-preset-swatch';s.style.background=c;pStrip.appendChild(s);});
const pName=document.createElement('div');
pName.className='pa-preset-name';
pName.textContent=p.name;
el.appendChild(pStrip);
el.appendChild(pName);
el.onclick=()=>{
palette=[...p.colors];
locked=[false,false,false,false,false];
currentBase=p.colors[0];
baseInput.value=currentBase;
render();
showToast('Loaded: '+p.name);
};
presetsEl.appendChild(el);
});

// ── Init ──────────────────────────────────────────────────────────────────
generate();
})();
</script>

</div>

---

## Related Tools

> [Color Blindness Simulator](/tools/color-blindness-simulator/)
> [Color Contrast Checker](/tools/color-contrast-checker/)
> [Color Converter](/tools/color-converter/)

## Related Articles

- [Best AI Image Generators Free 2026](/posts/best-ai-image-generators-free-2026/)
