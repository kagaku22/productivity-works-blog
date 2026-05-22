---
title: "HTML Entity Converter - Encode & Decode HTML"
date: 2025-05-16
description: "Free HTML entity encoder and decoder. Convert special characters to HTML entities and back. Supports named entities, numeric codes, and hex codes. No sign-up required."
categories: ["Free Tools"]
tags: ["Developer Tools", "Code Conversion", "Free Tools"]
slug: "html-entity-converter"
ShowToc: false
cover:
  image: "/images/covers/html-entity-converter.png"
  alt: "HTML Entity Converter"
---

<style>
#hec-app *,#hec-app *::before,#hec-app *::after{box-sizing:border-box;margin:0;padding:0}
#hec-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;max-width:900px;margin:0 auto;padding:16px;color:#1a1a2e}
#hec-app h2{font-size:1.1rem;font-weight:600;margin-bottom:12px;color:#333}
#hec-app .hec-panels{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:12px}
@media(max-width:600px){#hec-app .hec-panels{grid-template-columns:1fr}}
#hec-app .hec-panel label{display:block;font-size:.85rem;font-weight:600;color:#555;margin-bottom:6px}
#hec-app textarea{width:100%;height:200px;padding:10px;border:1.5px solid #d0d5e8;border-radius:8px;font-size:.9rem;font-family:monospace;resize:vertical;background:#fafbff;transition:border-color .2s}
#hec-app textarea:focus{outline:none;border-color:#4f6bed}
#hec-app .hec-controls{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-bottom:20px}
#hec-app button{padding:9px 20px;border:none;border-radius:7px;font-size:.9rem;font-weight:600;cursor:pointer;transition:background .2s,transform .1s}
#hec-app button:active{transform:scale(.97)}
#hec-app .btn-encode{background:#4f6bed;color:#fff}
#hec-app .btn-encode:hover{background:#3a55d4}
#hec-app .btn-decode{background:#22a67a;color:#fff}
#hec-app .btn-decode:hover{background:#198a64}
#hec-app .btn-copy-raw{background:#f0f2ff;color:#4f6bed;border:1.5px solid #c8cffa}
#hec-app .btn-copy-raw:hover{background:#e0e4ff}
#hec-app .btn-copy-enc{background:#f0f2ff;color:#22a67a;border:1.5px solid #b2e6d4}
#hec-app .btn-copy-enc:hover{background:#e0f7f0}
#hec-app .btn-clear{background:#f5f5f5;color:#666;border:1.5px solid #ddd}
#hec-app .btn-clear:hover{background:#ebebeb}
#hec-app .hec-toast{position:fixed;bottom:24px;right:24px;background:#333;color:#fff;padding:9px 18px;border-radius:8px;font-size:.85rem;opacity:0;pointer-events:none;transition:opacity .3s;z-index:9999}
#hec-app .hec-toast.show{opacity:1}
#hec-app .hec-ref{margin-top:8px}
#hec-app .hec-ref h3{font-size:1rem;font-weight:600;color:#333;margin-bottom:10px}
#hec-app .hec-ref table{width:100%;border-collapse:collapse;font-size:.85rem}
#hec-app .hec-ref th{background:#f0f2ff;color:#4f6bed;padding:8px 10px;text-align:left;border-bottom:2px solid #d0d5e8}
#hec-app .hec-ref td{padding:7px 10px;border-bottom:1px solid #eee;font-family:monospace}
#hec-app .hec-ref tr:hover td{background:#fafbff}
#hec-app .hec-ref td:first-child{font-size:1.1rem;text-align:center;font-family:inherit}
#hec-app .hec-click-cell{cursor:pointer;color:#4f6bed;text-decoration:underline dotted}
#hec-app .hec-click-cell:hover{color:#22a67a}
</style>

<div id="hec-app">

<div class="hec-panels">
<div class="hec-panel">
<label for="hec-raw">Plain Text / Raw HTML</label>
<textarea id="hec-raw" placeholder="Type or paste text here...&#10;Example: <Hello & "World">"></textarea>
</div>
<div class="hec-panel">
<label for="hec-enc">HTML Entities</label>
<textarea id="hec-enc" placeholder="Encoded output appears here...&#10;Example: &lt;Hello &amp; &quot;World&quot;&gt;"></textarea>
</div>
</div>

<div class="hec-controls">
<button class="btn-encode" onclick="hecEncode()">Encode &rarr;</button>
<button class="btn-decode" onclick="hecDecode()">&larr; Decode</button>
<button class="btn-copy-raw" onclick="hecCopy('raw')">Copy Raw</button>
<button class="btn-copy-enc" onclick="hecCopy('enc')">Copy Encoded</button>
<button class="btn-clear" onclick="hecClear()">Clear All</button>
</div>

<div class="hec-ref">
<h3>Common HTML Entities Reference</h3>
<table>
<thead>
<tr>
<th>Char</th>
<th>Named Entity</th>
<th>Numeric Code</th>
<th>Hex Code</th>
<th>Description</th>
</tr>
</thead>
<tbody id="hec-ref-body"></tbody>
</table>
<p style="font-size:.78rem;color:#888;margin-top:8px">Click any entity code to copy it to clipboard.</p>
</div>

<div class="hec-toast" id="hec-toast"></div>

</div>

<script>
(function(){
var refData=[
['&','&amp;','&#38;','&#x26;','Ampersand'],
['<','&lt;','&#60;','&#x3C;','Less-than sign'],
['>','&gt;','&#62;','&#x3E;','Greater-than sign'],
['"','&quot;','&#34;','&#x22;','Double quotation mark'],
["'",'&apos;','&#39;','&#x27;',"Single quotation mark"],
['\u00A0','&nbsp;','&#160;','&#xA0;','Non-breaking space'],
['©','&copy;','&#169;','&#xA9;','Copyright sign'],
['®','&reg;','&#174;','&#xAE;','Registered sign'],
['™','&trade;','&#8482;','&#x2122;','Trade mark sign'],
['€','&euro;','&#8364;','&#x20AC;','Euro sign'],
['£','&pound;','&#163;','&#xA3;','Pound sign'],
['¥','&yen;','&#165;','&#xA5;','Yen sign'],
['¢','&cent;','&#162;','&#xA2;','Cent sign'],
['§','&sect;','&#167;','&#xA7;','Section sign'],
['¶','&para;','&#182;','&#xB6;','Pilcrow / Paragraph sign'],
['•','&bull;','&#8226;','&#x2022;','Bullet'],
['…','&hellip;','&#8230;','&#x2026;','Horizontal ellipsis'],
['—','&mdash;','&#8212;','&#x2014;','Em dash'],
['–','&ndash;','&#8211;','&#x2013;','En dash'],
['«','&laquo;','&#171;','&#xAB;','Left double angle quotation mark'],
['»','&raquo;','&#187;','&#xBB;','Right double angle quotation mark'],
['←','&larr;','&#8592;','&#x2190;','Leftwards arrow'],
['→','&rarr;','&#8594;','&#x2192;','Rightwards arrow'],
['↑','&uarr;','&#8593;','&#x2191;','Upwards arrow'],
['↓','&darr;','&#8595;','&#x2193;','Downwards arrow'],
['×','&times;','&#215;','&#xD7;','Multiplication sign'],
['÷','&divide;','&#247;','&#xF7;','Division sign'],
['±','&plusmn;','&#177;','&#xB1;','Plus-minus sign'],
['½','&frac12;','&#189;','&#xBD;','Vulgar fraction one half'],
['¼','&frac14;','&#188;','&#xBC;','Vulgar fraction one quarter'],
['¾','&frac34;','&#190;','&#xBE;','Vulgar fraction three quarters'],
['°','&deg;','&#176;','&#xB0;','Degree sign'],
['µ','&micro;','&#181;','&#xB5;','Micro sign'],
['∞','&infin;','&#8734;','&#x221E;','Infinity'],
['≈','&asymp;','&#8776;','&#x2248;','Almost equal to'],
['≠','&ne;','&#8800;','&#x2260;','Not equal to'],
['≤','&le;','&#8804;','&#x2264;','Less-than or equal to'],
['≥','&ge;','&#8805;','&#x2265;','Greater-than or equal to'],
['∑','&sum;','&#8721;','&#x2211;','N-ary summation'],
['√','&radic;','&#8730;','&#x221A;','Square root'],
];

var tbody=document.getElementById('hec-ref-body');
refData.forEach(function(row){
var tr=document.createElement('tr');
var charTd=document.createElement('td');
charTd.textContent=row[0]==' '?'(space)':row[0];
tr.appendChild(charTd);
for(var i=1;i<=3;i++){
var td=document.createElement('td');
td.textContent=row[i];
td.className='hec-click-cell';
(function(val){td.addEventListener('click',function(){navigator.clipboard.writeText(val).then(function(){showToast('Copied: '+val)})});})(row[i]);
tr.appendChild(td);
}
var descTd=document.createElement('td');
descTd.textContent=row[4];
tr.appendChild(descTd);
tbody.appendChild(tr);
});

function encodeEntities(str){
return str
.replace(/&/g,'&amp;')
.replace(/</g,'&lt;')
.replace(/>/g,'&gt;')
.replace(/"/g,'&quot;')
.replace(/'/g,'&apos;')
.replace(/\u00A0/g,'&nbsp;')
.replace(/[^\x00-\x7E\u00A0]/g,function(c){
var code=c.codePointAt(0);
return '&#'+code+';';
});
}

function decodeEntities(str){
var txt=document.createElement('textarea');
txt.innerHTML=str;
return txt.value;
}

window.hecEncode=function(){
var raw=document.getElementById('hec-raw').value;
document.getElementById('hec-enc').value=encodeEntities(raw);
};

window.hecDecode=function(){
var enc=document.getElementById('hec-enc').value;
document.getElementById('hec-raw').value=decodeEntities(enc);
};

window.hecCopy=function(side){
var id=side==='raw'?'hec-raw':'hec-enc';
var val=document.getElementById(id).value;
if(!val){showToast('Nothing to copy');return;}
navigator.clipboard.writeText(val).then(function(){showToast('Copied to clipboard!')});
};

window.hecClear=function(){
document.getElementById('hec-raw').value='';
document.getElementById('hec-enc').value='';
};

var toastTimer=null;
function showToast(msg){
var t=document.getElementById('hec-toast');
t.textContent=msg;
t.classList.add('show');
if(toastTimer)clearTimeout(toastTimer);
toastTimer=setTimeout(function(){t.classList.remove('show');},2000);
}
})();
</script>
</div>

---

> URL encoding → [URL Encoder / Decoder](/tools/url-encoder/)

> Base64 conversion → [Base64 Encoder / Decoder](/tools/base64-encoder/)
