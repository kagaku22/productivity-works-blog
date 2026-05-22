---
title: "CSS単位変換ツール - px rem em vw vh変換"
date: 2025-08-29
description: "無料のCSS単位変換ツール。px、rem、em、vw、vh、パーセントを即座に相互変換。基本フォントサイズとビューポートサイズを設定して正確に変換。"
categories: ["無料ツール"]
tags: ["CSS", "Webデザイン", "無料ツール"]
slug: "css-unit-converter"
ShowToc: false
cover:
  image: "/images/covers/css-unit-converter-ja.png"
  alt: "CSS単位変換ツール"
---

<style>
#cuc-app *,#cuc-app *::before,#cuc-app *::after{box-sizing:border-box;margin:0;padding:0}
#cuc-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;max-width:780px;margin:0 auto;padding:16px;color:#1a1a2e}
#cuc-app .cuc-settings{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px;background:#f8f9ff;border:1.5px solid #d0d5e8;border-radius:10px;padding:14px;margin-bottom:18px}
#cuc-app .cuc-settings label{display:block;font-size:.78rem;font-weight:600;color:#555;margin-bottom:4px}
#cuc-app .cuc-settings input[type=number]{width:100%;padding:7px 10px;border:1.5px solid #d0d5e8;border-radius:7px;font-size:.9rem;background:#fff;transition:border-color .2s}
#cuc-app .cuc-settings input[type=number]:focus{outline:none;border-color:#4f6bed}
#cuc-app .cuc-input-row{display:flex;gap:10px;margin-bottom:18px;align-items:flex-end}
#cuc-app .cuc-input-row>div{flex:1}
#cuc-app .cuc-input-row label{display:block;font-size:.82rem;font-weight:600;color:#555;margin-bottom:5px}
#cuc-app .cuc-input-row input[type=number]{width:100%;padding:10px 12px;border:1.5px solid #d0d5e8;border-radius:8px;font-size:1.05rem;background:#fafbff;transition:border-color .2s}
#cuc-app .cuc-input-row input[type=number]:focus{outline:none;border-color:#4f6bed}
#cuc-app .cuc-input-row select{width:100%;padding:10px 10px;border:1.5px solid #d0d5e8;border-radius:8px;font-size:1rem;background:#fafbff;cursor:pointer;transition:border-color .2s}
#cuc-app .cuc-input-row select:focus{outline:none;border-color:#4f6bed}
#cuc-app .cuc-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:12px;margin-bottom:8px}
#cuc-app .cuc-card{background:#fff;border:1.5px solid #e2e6f8;border-radius:10px;padding:14px 16px;cursor:pointer;transition:border-color .2s,box-shadow .2s;position:relative}
#cuc-app .cuc-card:hover{border-color:#4f6bed;box-shadow:0 2px 10px rgba(79,107,237,.12)}
#cuc-app .cuc-card.cuc-active{border-color:#4f6bed;background:#f0f2ff}
#cuc-app .cuc-card-unit{font-size:.75rem;font-weight:700;color:#4f6bed;text-transform:uppercase;letter-spacing:.04em;margin-bottom:4px}
#cuc-app .cuc-card-value{font-size:1.25rem;font-weight:700;color:#1a1a2e;word-break:break-all}
#cuc-app .cuc-card-full{font-size:.72rem;color:#888;margin-top:2px}
#cuc-app .cuc-toast{position:fixed;bottom:24px;right:24px;background:#333;color:#fff;padding:9px 18px;border-radius:8px;font-size:.85rem;opacity:0;pointer-events:none;transition:opacity .3s;z-index:9999}
#cuc-app .cuc-toast.show{opacity:1}
#cuc-app .cuc-settings-title{font-size:.8rem;font-weight:700;color:#4f6bed;margin-bottom:2px;grid-column:1/-1}
#cuc-app .cuc-note{font-size:.78rem;color:#888;margin-top:4px}
</style>

<div id="cuc-app">

<div class="cuc-settings">
<div class="cuc-settings-title">設定</div>
<div>
<label for="cuc-base-font">ベースフォントサイズ (px)</label>
<input type="number" id="cuc-base-font" value="16" min="1" max="100" step="0.5" oninput="cucUpdate()">
</div>
<div>
<label for="cuc-vw">ビューポート幅 (px)</label>
<input type="number" id="cuc-vw" value="1440" min="1" max="10000" step="1" oninput="cucUpdate()">
</div>
<div>
<label for="cuc-vh">ビューポート高さ (px)</label>
<input type="number" id="cuc-vh" value="900" min="1" max="10000" step="1" oninput="cucUpdate()">
</div>
<div>
<label for="cuc-parent">親要素サイズ / コンテキスト (px)</label>
<input type="number" id="cuc-parent" value="1440" min="1" max="10000" step="0.5" oninput="cucUpdate()">
<div class="cuc-note">em・% の計算に使用されます</div>
</div>
</div>

<div class="cuc-input-row">
<div>
<label for="cuc-val">値</label>
<input type="number" id="cuc-val" value="16" step="any" oninput="cucUpdate()" placeholder="値を入力">
</div>
<div style="max-width:120px">
<label for="cuc-unit">単位</label>
<select id="cuc-unit" onchange="cucUpdate()">
<option value="px">px</option>
<option value="rem">rem</option>
<option value="em">em</option>
<option value="vw">vw</option>
<option value="vh">vh</option>
<option value="pct">%</option>
<option value="pt">pt</option>
<option value="cm">cm</option>
<option value="mm">mm</option>
<option value="in">in</option>
</select>
</div>
</div>

<div class="cuc-grid" id="cuc-grid"></div>
<p class="cuc-note" style="margin-bottom:12px">カードをクリックするとCSS値がクリップボードにコピーされます。</p>

<div class="cuc-toast" id="cuc-toast"></div>

</div>

<script>
(function(){
var UNITS=[
{key:'px',  label:'px',  name:'ピクセル'},
{key:'rem', label:'rem', name:'ルートem（ベースフォント基準）'},
{key:'em',  label:'em',  name:'em（親要素基準）'},
{key:'vw',  label:'vw',  name:'ビューポート幅の割合'},
{key:'vh',  label:'vh',  name:'ビューポート高さの割合'},
{key:'pct', label:'%',   name:'パーセント（親要素基準）'},
{key:'pt',  label:'pt',  name:'ポイント'},
{key:'cm',  label:'cm',  name:'センチメートル'},
{key:'mm',  label:'mm',  name:'ミリメートル'},
{key:'in',  label:'in',  name:'インチ'},
];

function getSettings(){
return {
base:parseFloat(document.getElementById('cuc-base-font').value)||16,
vw:parseFloat(document.getElementById('cuc-vw').value)||1440,
vh:parseFloat(document.getElementById('cuc-vh').value)||900,
parent:parseFloat(document.getElementById('cuc-parent').value)||1440,
};
}

function toPx(val,unit,s){
switch(unit){
case 'px':  return val;
case 'rem': return val*s.base;
case 'em':  return val*s.parent;
case 'vw':  return val*s.vw/100;
case 'vh':  return val*s.vh/100;
case 'pct': return val*s.parent/100;
case 'pt':  return val*96/72;
case 'cm':  return val*96/2.54;
case 'mm':  return val*96/25.4;
case 'in':  return val*96;
default:    return val;
}
}

function fromPx(px,unit,s){
switch(unit){
case 'px':  return px;
case 'rem': return px/s.base;
case 'em':  return px/s.parent;
case 'vw':  return px*100/s.vw;
case 'vh':  return px*100/s.vh;
case 'pct': return px*100/s.parent;
case 'pt':  return px*72/96;
case 'cm':  return px*2.54/96;
case 'mm':  return px*25.4/96;
case 'in':  return px/96;
default:    return px;
}
}

function fmt(n){
if(Math.abs(n)<0.0001&&n!==0)return n.toExponential(3);
var s=parseFloat(n.toFixed(6)).toString();
return s;
}

var grid=document.getElementById('cuc-grid');

function buildCards(){
grid.innerHTML='';
UNITS.forEach(function(u){
var card=document.createElement('div');
card.className='cuc-card';
card.id='cuc-card-'+u.key;
card.innerHTML='<div class="cuc-card-unit">'+u.label+'</div>'
+'<div class="cuc-card-value" id="cuc-cv-'+u.key+'">—</div>'
+'<div class="cuc-card-full">'+u.name+'</div>';
card.addEventListener('click',function(){
var raw=document.getElementById('cuc-cv-'+u.key).textContent;
if(raw==='—')return;
var cssVal=raw+(u.key==='pct'?'%':u.label==='%'?'%':u.label);
navigator.clipboard.writeText(cssVal).then(function(){showToast('コピーしました: '+cssVal)});
document.querySelectorAll('#cuc-app .cuc-card').forEach(function(c){c.classList.remove('cuc-active')});
card.classList.add('cuc-active');
});
grid.appendChild(card);
});
}

window.cucUpdate=function(){
var val=parseFloat(document.getElementById('cuc-val').value);
var unit=document.getElementById('cuc-unit').value;
var s=getSettings();
var activeCard=document.getElementById('cuc-card-'+unit);
document.querySelectorAll('#cuc-app .cuc-card').forEach(function(c){c.classList.remove('cuc-active')});
if(activeCard)activeCard.classList.add('cuc-active');
if(isNaN(val)){
UNITS.forEach(function(u){
var el=document.getElementById('cuc-cv-'+u.key);
if(el)el.textContent='—';
});
return;
}
var px=toPx(val,unit,s);
UNITS.forEach(function(u){
var el=document.getElementById('cuc-cv-'+u.key);
if(!el)return;
var converted=fromPx(px,u.key,s);
el.textContent=fmt(converted);
});
};

var toastTimer=null;
function showToast(msg){
var t=document.getElementById('cuc-toast');
t.textContent=msg;
t.classList.add('show');
if(toastTimer)clearTimeout(toastTimer);
toastTimer=setTimeout(function(){t.classList.remove('show');},2000);
}

buildCards();
cucUpdate();
})();
</script>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

## 関連ツール

> Box Shadow Generator → [Box Shadow Generatorツール](/ja/tools/box-shadow-generator/)
> Css Animation Generator → [Css Animation Generatorツール](/ja/tools/css-animation-generator/)
> Css Button Generator → [Css Button Generatorツール](/ja/tools/css-button-generator/)

