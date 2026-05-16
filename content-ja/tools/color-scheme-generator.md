---
title: "配色ジェネレーター"
description: "ベースカラーから補色・類似色・トライアド・スプリット補色・テトラード・モノクロマティックの配色を自動生成。HEX・RGB・HSL値をコピー、CSSカスタムプロパティ出力、WCAGコントラスト比チェックに対応。"
date: 2025-05-16
categories: ["無料ツール"]
slug: "color-scheme-generator"
ShowToc: false
aliases:
  - "/ja/tools/color-scheme-generator/"
  - "/ja/tools/color-scheme-generator/"
cover:
  image: "/images/covers/color-scheme-generator-ja.png"
  alt: "配色ジェネレーター"
---

<div id="cs-app">

<style>
#cs-app *,#cs-app *::before,#cs-app *::after{box-sizing:border-box;margin:0;padding:0}
#cs-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Kaku Gothic ProN','Noto Sans JP',sans-serif;color:#1a1a2e;--accent:#6c63ff;--radius:10px;--shadow:0 4px 24px rgba(0,0,0,.10)}
#cs-app a{color:var(--accent)}

/* Layout */
#cs-app .cs-wrap{max-width:900px;margin:0 auto;padding:0 0 56px}
#cs-app .cs-lead{font-size:.96rem;color:#555;margin-bottom:24px;line-height:1.75}

/* Controls */
#cs-app .cs-controls{display:flex;flex-wrap:wrap;gap:12px;align-items:flex-end;margin-bottom:28px;background:#f7f7fc;border-radius:var(--radius);padding:20px 22px}
#cs-app .cs-group{display:flex;flex-direction:column;gap:6px}
#cs-app .cs-group label{font-size:.75rem;font-weight:700;color:#555;text-transform:uppercase;letter-spacing:.04em}
#cs-app .cs-color-pick{width:64px;height:46px;border:2px solid #ddd;border-radius:8px;cursor:pointer;padding:2px;background:#fff}
#cs-app .cs-color-pick:hover{border-color:var(--accent)}
#cs-app .cs-select{height:46px;padding:0 14px;border:2px solid #ddd;border-radius:8px;font-size:.9rem;background:#fff;cursor:pointer;outline:none;transition:border-color .2s;min-width:200px}
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
#cs-app .cs-swatch-copy-hint{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,.18);opacity:0;transition:opacity .2s;font-size:.82rem;font-weight:700;letter-spacing:.02em}
#cs-app .cs-swatch-block:hover .cs-swatch-copy-hint{opacity:1}
#cs-app .cs-swatch-role{position:absolute;top:8px;left:10px;font-size:.68rem;font-weight:700;letter-spacing:.04em;padding:2px 7px;border-radius:4px;background:rgba(255,255,255,.72);backdrop-filter:blur(4px);color:#333}

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
#cs-app .cs-desc{font-size:.84rem;color:#555;margin-bottom:20px;padding:12px 16px;background:#f7f7fc;border-left:3px solid var(--accent);border-radius:0 8px 8px 0;line-height:1.7}
</style>

<div class="cs-wrap">

<p class="cs-lead">ベースカラーを選んでハーモニータイプを選択するだけで、HEX・RGB・HSL値・CSSカスタムプロパティ・WCAGコントラスト比を一括生成します。アップロード不要・登録不要、すべてブラウザ内で完結します。</p>

<!-- Controls -->
<div class="cs-controls">
  <div class="cs-group">
    <label>ベースカラー</label>
    <input type="color" id="cs-picker" class="cs-color-pick" value="#6c63ff">
  </div>
  <div class="cs-group">
    <label>HEX値</label>
    <input type="text" id="cs-hex-in" class="cs-hex-input" value="#6c63ff" maxlength="7" placeholder="#000000">
  </div>
  <div class="cs-group">
    <label>配色タイプ</label>
    <select id="cs-scheme-sel" class="cs-select">
      <option value="complementary">補色（コンプリメンタリー）</option>
      <option value="analogous">類似色（アナロガス）</option>
      <option value="triadic">トライアド</option>
      <option value="split-complementary">スプリット補色</option>
      <option value="tetradic">テトラード（4色）</option>
      <option value="monochromatic">モノクロマティック</option>
    </select>
  </div>
  <div class="cs-group">
    <label>&nbsp;</label>
    <button class="cs-btn cs-btn-primary" id="cs-gen-btn">生成する</button>
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
  <span>まとめてコピー：</span>
  <button class="cs-btn cs-btn-secondary cs-btn-sm" id="cs-copy-hex-all">全HEXをコピー</button>
  <button class="cs-btn cs-btn-secondary cs-btn-sm" id="cs-copy-css-all">CSS変数をコピー</button>
</div>

<!-- CSS Variables output -->
<div class="cs-css-section">
  <div class="cs-section-title">CSSカスタムプロパティ（変数）</div>
  <div class="cs-css-box" id="cs-css-box">
    <button class="cs-css-copy-btn" id="cs-css-copy-btn">コピー</button>
    <pre id="cs-css-pre" style="white-space:pre-wrap;word-break:break-all;"></pre>
  </div>
</div>

<!-- Contrast ratios -->
<div class="cs-contrast-section">
  <div class="cs-section-title">アクセシビリティ — コントラスト比（WCAG 2.1）</div>
  <div class="cs-contrast-grid" id="cs-contrast-grid"></div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

</div>

<div class="cs-toast" id="cs-toast"></div>

<script>
(function(){
'use strict';

/* ── カラー変換 ── */
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

/* ── 配色スキーム ── */
const SCHEMES={
  complementary:{
    desc:'カラーホイールで正反対に位置する2色の組み合わせ。コントラストが強く、力強い印象を与えます。',
    roles:['プライマリ','補色'],
    generate(h,s,l){return[[h,s,l],[clampH(h+180),s,l]];}
  },
  analogous:{
    desc:'カラーホイール上で隣り合う色の組み合わせ。自然で調和のとれた、落ち着いた印象になります。',
    roles:['プライマリ','類似色 −30°','類似色 +30°','類似色 −15°','類似色 +15°'],
    generate(h,s,l){
      return[[h,s,l],[clampH(h-30),s,l],[clampH(h+30),s,l],[clampH(h-15),s,l],[clampH(h+15),s,l]];
    }
  },
  triadic:{
    desc:'カラーホイールを3等分した位置にある3色。バランスが取れながらも活気があり、多様なデザインに向きます。',
    roles:['プライマリ','トライアド2','トライアド3'],
    generate(h,s,l){return[[h,s,l],[clampH(h+120),s,l],[clampH(h+240),s,l]];}
  },
  'split-complementary':{
    desc:'補色の両隣にある2色とベースカラーの組み合わせ。補色より柔らかく、それでも十分なコントラストを持ちます。',
    roles:['プライマリ','スプリット1','スプリット2'],
    generate(h,s,l){return[[h,s,l],[clampH(h+150),s,l],[clampH(h+210),s,l]];}
  },
  tetradic:{
    desc:'90°間隔で配置した4色。豊かな色彩表現が可能で、1色を主役にすると効果的です。',
    roles:['プライマリ','テトラード2','テトラード3','テトラード4'],
    generate(h,s,l){return[[h,s,l],[clampH(h+90),s,l],[clampH(h+180),s,l],[clampH(h+270),s,l]];}
  },
  monochromatic:{
    desc:'同じ色相の濃淡・明暗のバリエーション。統一感があり洗練された印象を与えます。',
    roles:['ベース','ダーク','ダーカー','ライト','ライター','最明'],
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

/* ── WCAGコントラスト比 ── */
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
  if(ratio>=3)return'AA 大テキスト';
  return'不合格';
}

/* ── 状態 ── */
let currentColors=[];

/* ── DOM ── */
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

/* ── トースト ── */
let toastTimer;
function showToast(msg){
  toast.textContent=msg;
  toast.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer=setTimeout(()=>toast.classList.remove('show'),2200);
}

/* ── コピー ── */
function copyText(text,msg){
  navigator.clipboard.writeText(text).then(()=>showToast(msg||'コピーしました！')).catch(()=>{
    const ta=document.createElement('textarea');
    ta.value=text;ta.style.position='fixed';ta.style.opacity='0';
    document.body.appendChild(ta);ta.select();document.execCommand('copy');
    document.body.removeChild(ta);showToast(msg||'コピーしました！');
  });
}

/* ── CSS変数名 ── */
const CSS_VAR_NAMES=['--color-primary','--color-secondary','--color-tertiary','--color-quaternary','--color-quinary','--color-senary'];
function getCssVarName(i){return CSS_VAR_NAMES[i]||('--color-'+(i+1));}

/* ── スウォッチ文字色 ── */
function swatchTextColor(hex){
  const{r,g,b}=hexToRgb(hex);
  const lum=relativeLuminance(r,g,b);
  return lum>.35?'rgba(0,0,0,.82)':'rgba(255,255,255,.92)';
}

/* ── スキーム名表示 ── */
const SCHEME_LABEL_JA={
  complementary:'補色スキーム',
  analogous:'類似色スキーム',
  triadic:'トライアドスキーム',
  'split-complementary':'スプリット補色スキーム',
  tetradic:'テトラードスキーム',
  monochromatic:'モノクロマティックスキーム'
};

/* ── 生成 ── */
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
    return{hex:hexVal,r:rgb.r,g:rgb.g,b:rgb.b,h:ch,s:cs,l:cl,role:scheme.roles[i]||('カラー'+(i+1))};
  });

  /* 説明 */
  descBox.textContent=scheme.desc;

  /* ラベル */
  schemeLabelBox.innerHTML=(SCHEME_LABEL_JA[schemeKey]||schemeKey)+' <span>全'+currentColors.length+'色</span>';

  /* スウォッチ */
  swatchesEl.innerHTML='';
  currentColors.forEach((col,i)=>{
    const tc=swatchTextColor(col.hex);
    const card=document.createElement('div');
    card.className='cs-swatch-card';
    card.innerHTML=`
      <div class="cs-swatch-block" style="background:${col.hex}" data-hex="${col.hex}">
        <span class="cs-swatch-role">${col.role}</span>
        <div class="cs-swatch-copy-hint" style="color:${tc}">クリックでHEXコピー</div>
      </div>
      <div class="cs-swatch-info">
        <div class="cs-swatch-hex">${col.hex.toUpperCase()}</div>
        <div class="cs-swatch-rgb">rgb(${col.r}, ${col.g}, ${col.b})</div>
        <div class="cs-swatch-hsl">hsl(${col.h}, ${col.s}%, ${col.l}%)</div>
        <button class="cs-swatch-copy-btn" data-idx="${i}">HEXをコピー</button>
      </div>`;
    swatchesEl.appendChild(card);
  });

  /* CSS変数 */
  let cssText=':root {\n';
  currentColors.forEach((col,i)=>{
    const vname=getCssVarName(i);
    cssText+=`  ${vname}: ${col.hex.toUpperCase()}; /* ${col.role} */\n`;
    cssText+=`  ${vname}-rgb: ${col.r}, ${col.g}, ${col.b};\n`;
    cssText+=`  ${vname}-hsl: ${col.h}deg ${col.s}% ${col.l}%;\n`;
  });
  cssText+='}';

  cssPre.innerHTML=cssText
    .replace(/(:root \{|\})/g,'<span class="cs-var-comment">$1</span>')
    .replace(/(--[\w-]+)(:)/g,'<span class="cs-var-name">$1</span>$2')
    .replace(/:\s*(#[0-9a-fA-F]+|\d+[^;]*);/g,(m,v)=>m.replace(v,'<span class="cs-var-val">'+v+'</span>'));

  /* コントラスト比 */
  contrastGrid.innerHTML='';
  const pairs=[];
  for(let i=0;i<currentColors.length;i++){
    for(let j=i+1;j<currentColors.length;j++){pairs.push([i,j]);}
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

  cssBox.dataset.raw=cssText;
}

/* ── イベント ── */
picker.addEventListener('input',()=>{hexIn.value=picker.value;generate();});

hexIn.addEventListener('input',()=>{
  let v=hexIn.value.trim();
  if(!v.startsWith('#'))v='#'+v;
  if(/^#[0-9a-fA-F]{6}$/.test(v)){picker.value=v;generate();}
});

hexIn.addEventListener('keydown',e=>{
  if(e.key==='Enter'){
    let v=hexIn.value.trim();
    if(!v.startsWith('#'))v='#'+v;
    if(/^#[0-9a-fA-F]{3}$/.test(v)){v='#'+v[1]+v[1]+v[2]+v[2]+v[3]+v[3];}
    if(/^#[0-9a-fA-F]{6}$/.test(v)){picker.value=v;hexIn.value=v;generate();}
  }
});

schemeSel.addEventListener('change',generate);
genBtn.addEventListener('click',generate);

swatchesEl.addEventListener('click',e=>{
  const block=e.target.closest('.cs-swatch-block');
  if(block){copyText(block.dataset.hex.toUpperCase(),'HEXをコピーしました！');return;}
  const btn=e.target.closest('.cs-swatch-copy-btn');
  if(btn){const idx=parseInt(btn.dataset.idx);copyText(currentColors[idx].hex.toUpperCase(),'HEXをコピーしました！');}
});

cssCopyBtn.addEventListener('click',()=>copyText(cssBox.dataset.raw||'','CSS変数をコピーしました！'));
copyHexAll.addEventListener('click',()=>copyText(currentColors.map(c=>c.hex.toUpperCase()).join('\n'),'全HEXをコピーしました！'));
copyCssAll.addEventListener('click',()=>copyText(cssBox.dataset.raw||'','CSS変数をコピーしました！'));

/* 初期描画 */
generate();

})();
</script>

---

> カラーパレット → [カラーパレット生成](/ja/tools/color-palette-generator/)

> カラー変換 → [RGB⇔HEX変換](/ja/tools/rgb-hex-converter/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
