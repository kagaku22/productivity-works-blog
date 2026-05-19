---
title: "Color Scheme Generator — Free Online Tool"
description: "Generate beautiful color schemes from any base color. Complementary, analogous, triadic, split-complementary, tetradic, and monochromatic harmonies. Copy HEX/RGB/HSL, export CSS variables, check contrast ratios."
date: 2025-05-16
categories: ["Free Tools"]
slug: "color-scheme-generator"
ShowToc: false
aliases:
  - "/tools/color-scheme-generator/"
  - "/tools/color-scheme-generator/"
cover:
  image: "/images/covers/color-scheme-generator.png"
  alt: "Color Scheme Generator"
---

<div id="cs-app">

<style>
#cs-app *,#cs-app *::before,#cs-app *::after{box-sizing:border-box;margin:0;padding:0}
#cs-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1a1a2e;--accent:#6c63ff;--radius:10px;--shadow:0 4px 24px rgba(0,0,0,.10)}
#cs-app a{color:var(--accent)}

/* Layout */
#cs-app .cs-wrap{max-width:900px;margin:0 auto;padding:0 0 56px}
#cs-app .cs-lead{font-size:.96rem;color:#555;margin-bottom:24px;line-height:1.65}

/* Controls */
#cs-app .cs-controls{display:flex;flex-wrap:wrap;gap:12px;align-items:flex-end;margin-bottom:28px;background:#f7f7fc;border-radius:var(--radius);padding:20px 22px}
#cs-app .cs-group{display:flex;flex-direction:column;gap:6px}
#cs-app .cs-group label{font-size:.75rem;font-weight:700;color:#555;text-transform:uppercase;letter-spacing:.05em}
#cs-app .cs-color-pick{width:64px;height:46px;border:2px solid #ddd;border-radius:8px;cursor:pointer;padding:2px;background:#fff}
#cs-app .cs-color-pick:hover{border-color:var(--accent)}
#cs-app .cs-select{height:46px;padding:0 14px;border:2px solid #ddd;border-radius:8px;font-size:.9rem;background:#fff;cursor:pointer;outline:none;transition:border-color .2s;min-width:190px}
#cs-app .cs-select:focus{border-color:var(--accent)}
#cs-app .cs-hex-input{height:46px;padding:0 12px;border:2px solid #ddd;border-radius:8px;font-size:.9rem;font-family:monospace;width:110px;outline:none;transition:border-color .2s}
#cs-app .cs-hex-input:focus{border-color:var(--accent)}
#cs-app .cs-btn{height:46px;padding:0 22px;border:none;border-radius:8px;font-size:.9rem;font-weight:700;cursor:pointer;transition:transform .1s,opacity .2s;white-space:nowrap}
#cs-app .cs-btn:active{transform:scale(.97)}
#cs-app .cs-btn-primary{background:var(--accent);color:#fff}
#cs-app .cs-btn-primary:hover{opacity:.87}
#cs-app .cs-btn-secondary{background:#fff;color:#333;border:2px solid #ddd}
#cs-app .cs-btn-secondary:hover{border-color:#aaa}
#cs-app .cs-btn-sm{height:34px;padding:0 14px;font-size:.8rem}

/* Scheme label */
#cs-app .cs-scheme-label{font-size:1rem;font-weight:700;color:#1a1a2e;margin-bottom:16px;display:flex;align-items:center;gap:10px}
#cs-app .cs-scheme-label span{font-size:.8rem;font-weight:500;color:#888;font-style:italic}

/* Swatches grid */
#cs-app .cs-swatches{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:16px;margin-bottom:28px}
@media(max-width:600px){#cs-app .cs-swatches{grid-template-columns:repeat(2,1fr)}}
@media(max-width:360px){#cs-app .cs-swatches{grid-template-columns:1fr}}

#cs-app .cs-swatch-card{border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow);background:#fff;transition:transform .18s}
#cs-app .cs-swatch-card:hover{transform:translateY(-3px)}
#cs-app .cs-swatch-block{height:140px;position:relative;cursor:pointer;display:flex;align-items:center;justify-content:center}
#cs-app .cs-swatch-copy-hint{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,.18);opacity:0;transition:opacity .2s;font-size:.82rem;font-weight:700;letter-spacing:.04em}
#cs-app .cs-swatch-block:hover .cs-swatch-copy-hint{opacity:1}
#cs-app .cs-swatch-role{position:absolute;top:8px;left:10px;font-size:.68rem;font-weight:700;letter-spacing:.06em;text-transform:uppercase;padding:2px 7px;border-radius:4px;background:rgba(255,255,255,.72);backdrop-filter:blur(4px);color:#333}

#cs-app .cs-swatch-info{padding:12px 12px 14px;display:flex;flex-direction:column;gap:3px}
#cs-app .cs-swatch-hex{font-size:.95rem;font-weight:700;letter-spacing:.03em;color:#1a1a2e}
#cs-app .cs-swatch-rgb{font-size:.72rem;color:#777;font-family:monospace}
#cs-app .cs-swatch-hsl{font-size:.72rem;color:#777;font-family:monospace}
#cs-app .cs-swatch-copy-btn{margin-top:6px;height:28px;padding:0 10px;font-size:.73rem;font-weight:600;border:1.5px solid #ddd;border-radius:6px;background:#fff;cursor:pointer;transition:background .15s,border-color .15s;align-self:flex-start}
#cs-app .cs-swatch-copy-btn:hover{background:#f0f0ff;border-color:var(--accent);color:var(--accent)}

/* Contrast table */
#cs-app .cs-contrast-section{margin-bottom:28px}
#cs-app .cs-section-title{font-size:.95rem;font-weight:700;color:#1a1a2e;margin-bottom:14px;padding-bottom:8px;border-bottom:2px solid #f0f0f5}
#cs-app .cs-contrast-grid{display:grid;gap:8px}
#cs-app .cs-contrast-row{display:flex;align-items:center;gap:10px;padding:10px 14px;border-radius:8px;background:#fafafa;border:1px solid #eee;flex-wrap:wrap}
#cs-app .cs-contrast-swatch-pair{display:flex;gap:4px;flex-shrink:0}
#cs-app .cs-contrast-dot{width:22px;height:22px;border-radius:50%;border:1.5px solid rgba(0,0,0,.12)}
#cs-app .cs-contrast-label{font-size:.82rem;color:#444;flex:1;min-width:120px;font-family:monospace}
#cs-app .cs-contrast-ratio{font-size:.88rem;font-weight:700;padding:3px 10px;border-radius:20px;white-space:nowrap}
#cs-app .cs-ratio-aaa{background:#d1fae5;color:#065f46}
#cs-app .cs-ratio-aa{background:#dbeafe;color:#1e3a8a}
#cs-app .cs-ratio-fail{background:#fee2e2;color:#991b1b}
#cs-app .cs-wcag-badge{font-size:.7rem;font-weight:700;padding:2px 7px;border-radius:4px;background:#e5e7eb;color:#374151}
#cs-app .cs-wcag-aaa{background:#a7f3d0;color:#064e3b}
#cs-app .cs-wcag-aa{background:#bfdbfe;color:#1e40af}
#cs-app .cs-wcag-fail{background:#fecaca;color:#7f1d1d}

/* CSS Variables output */
#cs-app .cs-css-section{margin-bottom:28px}
#cs-app .cs-css-box{position:relative;background:#1a1a2e;border-radius:var(--radius);padding:20px 20px 20px 24px;font-family:'Courier New',monospace;font-size:.82rem;line-height:1.8;color:#e2e8f0;overflow-x:auto}
#cs-app .cs-css-box .cs-var-comment{color:#718096}
#cs-app .cs-css-box .cs-var-name{color:#81e6d9}
#cs-app .cs-css-box .cs-var-val{color:#fbd38d}
#cs-app .cs-css-copy-btn{position:absolute;top:12px;right:12px;height:30px;padding:0 14px;font-size:.75rem;font-weight:700;background:rgba(255,255,255,.12);color:#e2e8f0;border:1px solid rgba(255,255,255,.2);border-radius:6px;cursor:pointer;transition:background .15s}
#cs-app .cs-css-copy-btn:hover{background:rgba(255,255,255,.22)}

/* Copy all */
#cs-app .cs-copy-all-bar{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:32px;align-items:center}
#cs-app .cs-copy-all-bar span{font-size:.82rem;color:#666}

/* Toast */
#cs-app .cs-toast{position:fixed;bottom:32px;left:50%;transform:translateX(-50%) translateY(80px);background:#1a1a2e;color:#fff;padding:11px 26px;border-radius:50px;font-size:.87rem;font-weight:600;opacity:0;transition:opacity .25s,transform .25s;z-index:9999;pointer-events:none}
#cs-app .cs-toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* Scheme description */
#cs-app .cs-desc{font-size:.84rem;color:#555;margin-bottom:20px;padding:12px 16px;background:#f7f7fc;border-left:3px solid var(--accent);border-radius:0 8px 8px 0;line-height:1.6}
</style>

<div class="cs-wrap">

<p class="cs-lead">Pick a base color, choose a harmony type, and instantly get a complete color scheme with HEX, RGB, HSL values, CSS variables, and WCAG contrast ratios — all in your browser, no uploads, no sign-up.</p>

<!-- Controls -->
<div class="cs-controls">
<div class="cs-group">
<label>Base Color</label>
<input type="color" id="cs-picker" class="cs-color-pick" value="#6c63ff">
</div>
<div class="cs-group">
<label>HEX</label>
<input type="text" id="cs-hex-in" class="cs-hex-input" value="#6c63ff" maxlength="7" placeholder="#000000">
</div>
<div class="cs-group">
<label>Harmony Type</label>
<select id="cs-scheme-sel" class="cs-select">
<option value="complementary">Complementary</option>
<option value="analogous">Analogous</option>
<option value="triadic">Triadic</option>
<option value="split-complementary">Split-Complementary</option>
<option value="tetradic">Tetradic</option>
<option value="monochromatic">Monochromatic</option>
</select>
</div>
<div class="cs-group">
<label>&nbsp;</label>
<button class="cs-btn cs-btn-primary" id="cs-gen-btn">Generate</button>
</div>
</div>

<!-- Scheme description -->
<div class="cs-desc" id="cs-desc-box"></div>

<!-- Scheme label -->
<div class="cs-scheme-label" id="cs-scheme-label-box"></div>

<!-- Swatches -->
<div class="cs-swatches" id="cs-swatches"></div>

<!-- Copy all bar -->
<div class="cs-copy-all-bar">
<span>Copy entire scheme:</span>
<button class="cs-btn cs-btn-secondary cs-btn-sm" id="cs-copy-hex-all">Copy all HEX</button>
<button class="cs-btn cs-btn-secondary cs-btn-sm" id="cs-copy-css-all">Copy CSS vars</button>
</div>

<!-- CSS Variables output -->
<div class="cs-css-section">
<div class="cs-section-title">CSS Variables</div>
<div class="cs-css-box" id="cs-css-box">
<button class="cs-css-copy-btn" id="cs-css-copy-btn">Copy</button>
<pre id="cs-css-pre" style="white-space:pre-wrap;word-break:break-all;"></pre>
</div>
</div>

<!-- Contrast ratios -->
<div class="cs-contrast-section">
<div class="cs-section-title">Accessibility — Contrast Ratios (WCAG 2.1)</div>
<div class="cs-contrast-grid" id="cs-contrast-grid"></div>
</div>

</div>

<div class="cs-toast" id="cs-toast"></div>

<script>
(function(){
'use strict';

/* ── Colour math ── */
function hexToRgb(hex){
hex=hex.replace(/^#/,'');
if(hex.length===3)hex=hex.split('').map(c=>c+c).join('');
const n=parseInt(hex,16);
return{r:(n>>16)&255,g:(n>>8)&255,b:n&255};
}
function rgbToHex(r,g,b){
return'#'+[r,g,b].map(v=>Math.round(v).toString(16).padStart(2,'0')).join('');
}
function rgbToHsl(r,g,b){
r/=255;g/=255;b/=255;
const max=Math.max(r,g,b),min=Math.min(r,g,b);
let h,s,l=(max+min)/2;
if(max===min){h=s=0;}else{
const d=max-min;
s=l>.5?d/(2-max-min):d/(max+min);
switch(max){
case r:h=((g-b)/d+(g<b?6:0))/6;break;
case g:h=((b-r)/d+2)/6;break;
case b:h=((r-g)/d+4)/6;break;
}
}
return{h:Math.round(h*360),s:Math.round(s*100),l:Math.round(l*100)};
}
function hslToRgb(h,s,l){
s/=100;l/=100;
const k=n=>(n+h/30)%12;
const a=s*Math.min(l,1-l);
const f=n=>l-a*Math.max(-1,Math.min(k(n)-3,Math.min(9-k(n),1)));
return{r:Math.round(f(0)*255),g:Math.round(f(8)*255),b:Math.round(f(4)*255)};
}
function hslToHex(h,s,l){
const{r,g,b}=hslToRgb(h,s,l);
return rgbToHex(r,g,b);
}
function clampH(h){return((h%360)+360)%360;}

/* ── Scheme generators ── */
const SCHEMES={
complementary:{
desc:'Two colors opposite each other on the color wheel — high contrast, bold, and eye-catching.',
roles:['Primary','Complement'],
generate(h,s,l){
return[[h,s,l],[clampH(h+180),s,l]];
}
},
analogous:{
desc:'Colors adjacent on the wheel — harmonious, serene, and pleasing. Great for backgrounds and brand palettes.',
roles:['Primary','Analogous −30°','Analogous +30°','Analogous −15°','Analogous +15°'],
generate(h,s,l){
return[[h,s,l],[clampH(h-30),s,l],[clampH(h+30),s,l],[clampH(h-15),s,l],[clampH(h+15),s,l]];
}
},
triadic:{
desc:'Three colors evenly spaced 120° apart — vibrant and balanced, works well for diverse, dynamic designs.',
roles:['Primary','Triadic 2','Triadic 3'],
generate(h,s,l){
return[[h,s,l],[clampH(h+120),s,l],[clampH(h+240),s,l]];
}
},
'split-complementary':{
desc:'The base color plus two colors adjacent to its complement — high contrast with more variety than complementary.',
roles:['Primary','Split 1','Split 2'],
generate(h,s,l){
return[[h,s,l],[clampH(h+150),s,l],[clampH(h+210),s,l]];
}
},
tetradic:{
desc:'Four colors forming two complementary pairs — rich and full, best used with one dominant color.',
roles:['Primary','Tetrad 2','Tetrad 3','Tetrad 4'],
generate(h,s,l){
return[[h,s,l],[clampH(h+90),s,l],[clampH(h+180),s,l],[clampH(h+270),s,l]];
}
},
monochromatic:{
desc:'Tints, tones, and shades of a single hue — elegant, cohesive, and easy to work with.',
roles:['Base','Dark','Darker','Light','Lighter','Lightest'],
generate(h,s,l){
return[
[h,s,l],
[h,s,Math.max(l-20,5)],
[h,s,Math.max(l-38,5)],
[h,s,Math.min(l+18,95)],
[h,s,Math.min(l+33,95)],
[h,Math.max(s-20,5),Math.min(l+48,96)],
];
}
}
};

/* ── WCAG contrast ── */
function relativeLuminance(r,g,b){
const s=[r,g,b].map(v=>{v/=255;return v<=.03928?v/12.92:Math.pow((v+.055)/1.055,2.4)});
return .2126*s[0]+.7152*s[1]+.0722*s[2];
}
function contrastRatio(c1,c2){
const l1=relativeLuminance(c1.r,c1.g,c1.b);
const l2=relativeLuminance(c2.r,c2.g,c2.b);
const bright=Math.max(l1,l2),dark=Math.min(l1,l2);
return Math.round(((bright+.05)/(dark+.05))*100)/100;
}
function wcagLevel(ratio){
if(ratio>=7)return'AAA';
if(ratio>=4.5)return'AA';
if(ratio>=3)return'AA Large';
return'Fail';
}

/* ── State ── */
let currentColors=[];

/* ── DOM refs ── */
const picker=document.getElementById('cs-picker');
const hexIn=document.getElementById('cs-hex-in');
const schemeSel=document.getElementById('cs-scheme-sel');
const genBtn=document.getElementById('cs-gen-btn');
const swatchesEl=document.getElementById('cs-swatches');
const descBox=document.getElementById('cs-desc-box');
const schemeLabelBox=document.getElementById('cs-scheme-label-box');
const cssBox=document.getElementById('cs-css-box');
const cssPre=document.getElementById('cs-css-pre');
const cssCopyBtn=document.getElementById('cs-css-copy-btn');
const contrastGrid=document.getElementById('cs-contrast-grid');
const toast=document.getElementById('cs-toast');
const copyHexAll=document.getElementById('cs-copy-hex-all');
const copyCssAll=document.getElementById('cs-copy-css-all');

/* ── Toast ── */
let toastTimer;
function showToast(msg){
toast.textContent=msg;
toast.classList.add('show');
clearTimeout(toastTimer);
toastTimer=setTimeout(()=>toast.classList.remove('show'),2200);
}

/* ── Copy helper ── */
function copyText(text,msg){
navigator.clipboard.writeText(text).then(()=>showToast(msg||'Copied!')).catch(()=>{
const ta=document.createElement('textarea');
ta.value=text;ta.style.position='fixed';ta.style.opacity='0';
document.body.appendChild(ta);ta.select();document.execCommand('copy');
document.body.removeChild(ta);showToast(msg||'Copied!');
});
}

/* ── CSS var names ── */
const CSS_VAR_NAMES=['--color-primary','--color-secondary','--color-tertiary','--color-quaternary','--color-quinary','--color-senary'];
function getCssVarName(i){return CSS_VAR_NAMES[i]||('--color-'+(i+1));}

/* ── Text colour for swatch ── */
function swatchTextColor(hex){
const{r,g,b}=hexToRgb(hex);
const lum=relativeLuminance(r,g,b);
return lum>.35?'rgba(0,0,0,.82)':'rgba(255,255,255,.92)';
}

/* ── Render ── */
function generate(){
const hex=picker.value;
const{r,g,b}=hexToRgb(hex);
const{h,s,l}=rgbToHsl(r,g,b);
const schemeKey=schemeSel.value;
const scheme=SCHEMES[schemeKey];
const hslList=scheme.generate(h,s,l);

currentColors=hslList.map(([ch,cs,cl],i)=>{
const hexVal=hslToHex(ch,cs,cl);
const rgb=hexToRgb(hexVal);
return{hex:hexVal,r:rgb.r,g:rgb.g,b:rgb.b,h:ch,s:cs,l:cl,role:scheme.roles[i]||('Color '+(i+1))};
});

/* Description */
descBox.textContent=scheme.desc;

/* Label */
schemeLabelBox.innerHTML=schemeKey.split('-').map(w=>w[0].toUpperCase()+w.slice(1)).join('-')+' Scheme <span>'+currentColors.length+' colors</span>';

/* Swatches */
swatchesEl.innerHTML='';
currentColors.forEach((col,i)=>{
const tc=swatchTextColor(col.hex);
const card=document.createElement('div');
card.className='cs-swatch-card';
card.innerHTML=`
<div class="cs-swatch-block" style="background:${col.hex}" data-hex="${col.hex}">
<span class="cs-swatch-role">${col.role}</span>
<div class="cs-swatch-copy-hint" style="color:${tc}">Click to copy HEX</div>
</div>
<div class="cs-swatch-info">
<div class="cs-swatch-hex">${col.hex.toUpperCase()}</div>
<div class="cs-swatch-rgb">rgb(${col.r}, ${col.g}, ${col.b})</div>
<div class="cs-swatch-hsl">hsl(${col.h}, ${col.s}%, ${col.l}%)</div>
<button class="cs-swatch-copy-btn" data-idx="${i}">Copy HEX</button>
</div>`;
swatchesEl.appendChild(card);
});

/* CSS variables */
let cssText=':root {\n';
currentColors.forEach((col,i)=>{
const vname=getCssVarName(i);
cssText+=`  ${vname}: ${col.hex.toUpperCase()}; /* ${col.role} */\n`;
cssText+=`  ${vname}-rgb: ${col.r}, ${col.g}, ${col.b};\n`;
cssText+=`  ${vname}-hsl: ${col.h}deg ${col.s}% ${col.l}%;\n`;
});
cssText+='}';

/* Render code with spans */
cssPre.innerHTML=cssText
.replace(/(:root \{|\})/g,'<span class="cs-var-comment">$1</span>')
.replace(/(--[\w-]+)(:)/g,'<span class="cs-var-name">$1</span>$2')
.replace(/:\s*(#[0-9a-fA-F]+|\d+[^;]*);/g,(m,v)=>m.replace(v,'<span class="cs-var-val">'+v+'</span>'));

/* Contrast ratios */
contrastGrid.innerHTML='';
const pairs=[];
for(let i=0;i<currentColors.length;i++){
for(let j=i+1;j<currentColors.length;j++){
pairs.push([i,j]);
}
}
pairs.forEach(([i,j])=>{
const a=currentColors[i],b=currentColors[j];
const ratio=contrastRatio(a,b);
const level=wcagLevel(ratio);
const ratioClass=level==='AAA'?'cs-ratio-aaa':level.startsWith('AA')?'cs-ratio-aa':'cs-ratio-fail';
const badgeClass=level==='AAA'?'cs-wcag-aaa':level.startsWith('AA')?'cs-wcag-aa':'cs-wcag-fail';
const row=document.createElement('div');
row.className='cs-contrast-row';
row.innerHTML=`
<div class="cs-contrast-swatch-pair">
<div class="cs-contrast-dot" style="background:${a.hex}"></div>
<div class="cs-contrast-dot" style="background:${b.hex}"></div>
</div>
<div class="cs-contrast-label">${a.role} × ${b.role}</div>
<div class="cs-contrast-ratio ${ratioClass}">${ratio}:1</div>
<span class="cs-wcag-badge ${badgeClass}">${level}</span>`;
contrastGrid.appendChild(row);
});

/* Store raw css for copy */
cssBox.dataset.raw=cssText;
}

/* ── Events ── */
picker.addEventListener('input',()=>{
hexIn.value=picker.value;
generate();
});

hexIn.addEventListener('input',()=>{
let v=hexIn.value.trim();
if(!v.startsWith('#'))v='#'+v;
if(/^#[0-9a-fA-F]{6}$/.test(v)){
picker.value=v;
generate();
}
});

hexIn.addEventListener('keydown',e=>{
if(e.key==='Enter'){
let v=hexIn.value.trim();
if(!v.startsWith('#'))v='#'+v;
if(/^#[0-9a-fA-F]{3}$/.test(v)){
v='#'+v[1]+v[1]+v[2]+v[2]+v[3]+v[3];
}
if(/^#[0-9a-fA-F]{6}$/.test(v)){
picker.value=v;hexIn.value=v;generate();
}
}
});

schemeSel.addEventListener('change',generate);
genBtn.addEventListener('click',generate);

/* swatch click events (delegated) */
swatchesEl.addEventListener('click',e=>{
const block=e.target.closest('.cs-swatch-block');
if(block){copyText(block.dataset.hex.toUpperCase(),'HEX copied!');return;}
const btn=e.target.closest('.cs-swatch-copy-btn');
if(btn){
const idx=parseInt(btn.dataset.idx);
copyText(currentColors[idx].hex.toUpperCase(),'HEX copied!');
}
});

cssCopyBtn.addEventListener('click',()=>{
copyText(cssBox.dataset.raw||'','CSS variables copied!');
});

copyHexAll.addEventListener('click',()=>{
const text=currentColors.map(c=>c.hex.toUpperCase()).join('\n');
copyText(text,'All HEX values copied!');
});

copyCssAll.addEventListener('click',()=>{
copyText(cssBox.dataset.raw||'','CSS variables copied!');
});

/* Initial render */
generate();

})();
</script>

---

> Generate palettes → [Color Palette Generator](/tools/color-palette-generator/)

> Convert colors → [RGB HEX Converter](/tools/rgb-hex-converter/)

</div>
