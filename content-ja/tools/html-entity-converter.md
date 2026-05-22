---
title: "HTMLエンティティ変換ツール"
date: 2025-12-09
description: "無料のHTMLエンティティ変換ツール。特殊文字をHTMLエンティティにエンコード・デコード。名前付きエンティティ、数値コード、16進コードに対応。"
categories: ["無料ツール"]
tags: ["開発ツール", "コード変換", "無料ツール"]
slug: "html-entity-converter"
ShowToc: false
cover:
  image: "/images/covers/html-entity-converter-ja.png"
  alt: "HTMLエンティティ変換ツール"
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
<label for="hec-raw">プレーンテキスト / 生のHTML</label>
<textarea id="hec-raw" placeholder="ここにテキストを入力または貼り付けてください...&#10;例: &lt;こんにちは &amp; "世界"&gt;"></textarea>
</div>
<div class="hec-panel">
<label for="hec-enc">HTMLエンティティ</label>
<textarea id="hec-enc" placeholder="エンコード結果がここに表示されます...&#10;例: &amp;lt;こんにちは &amp;amp; &amp;quot;世界&amp;quot;&amp;gt;"></textarea>
</div>
</div>

<div class="hec-controls">
<button class="btn-encode" onclick="hecEncode()">エンコード &rarr;</button>
<button class="btn-decode" onclick="hecDecode()">&larr; デコード</button>
<button class="btn-copy-raw" onclick="hecCopy('raw')">生テキストをコピー</button>
<button class="btn-copy-enc" onclick="hecCopy('enc')">エンコード結果をコピー</button>
<button class="btn-clear" onclick="hecClear()">クリア</button>
</div>

<div class="hec-ref">
<h3>よく使うHTMLエンティティ一覧</h3>
<table>
<thead>
<tr>
<th>文字</th>
<th>名前付きエンティティ</th>
<th>数値コード</th>
<th>16進コード</th>
<th>説明</th>
</tr>
</thead>
<tbody id="hec-ref-body"></tbody>
</table>
<p style="font-size:.78rem;color:#888;margin-top:8px">エンティティコードをクリックするとクリップボードにコピーされます。</p>
</div>

<div class="hec-toast" id="hec-toast"></div>

</div>

<script>
(function(){
var refData=[
['&','&amp;','&#38;','&#x26;','アンパサンド'],
['<','&lt;','&#60;','&#x3C;','小なり記号'],
['>','&gt;','&#62;','&#x3E;','大なり記号'],
['"','&quot;','&#34;','&#x22;','二重引用符'],
["'",'&apos;','&#39;','&#x27;','一重引用符（アポストロフィ）'],
['\u00A0','&nbsp;','&#160;','&#xA0;','ノーブレークスペース'],
['©','&copy;','&#169;','&#xA9;','著作権記号'],
['®','&reg;','&#174;','&#xAE;','登録商標記号'],
['™','&trade;','&#8482;','&#x2122;','商標記号'],
['€','&euro;','&#8364;','&#x20AC;','ユーロ記号'],
['£','&pound;','&#163;','&#xA3;','ポンド記号'],
['¥','&yen;','&#165;','&#xA5;','円・人民元記号'],
['¢','&cent;','&#162;','&#xA2;','セント記号'],
['§','&sect;','&#167;','&#xA7;','セクション記号'],
['¶','&para;','&#182;','&#xB6;','段落記号'],
['•','&bull;','&#8226;','&#x2022;','中黒・ビュレット'],
['…','&hellip;','&#8230;','&#x2026;','水平省略記号'],
['—','&mdash;','&#8212;','&#x2014;','全角ダッシュ'],
['–','&ndash;','&#8211;','&#x2013;','半角ダッシュ'],
['«','&laquo;','&#171;','&#xAB;','左二重山括弧'],
['»','&raquo;','&#187;','&#xBB;','右二重山括弧'],
['←','&larr;','&#8592;','&#x2190;','左向き矢印'],
['→','&rarr;','&#8594;','&#x2192;','右向き矢印'],
['↑','&uarr;','&#8593;','&#x2191;','上向き矢印'],
['↓','&darr;','&#8595;','&#x2193;','下向き矢印'],
['×','&times;','&#215;','&#xD7;','乗算記号'],
['÷','&divide;','&#247;','&#xF7;','除算記号'],
['±','&plusmn;','&#177;','&#xB1;','プラスマイナス記号'],
['½','&frac12;','&#189;','&#xBD;','2分の1'],
['¼','&frac14;','&#188;','&#xBC;','4分の1'],
['¾','&frac34;','&#190;','&#xBE;','4分の3'],
['°','&deg;','&#176;','&#xB0;','度記号'],
['µ','&micro;','&#181;','&#xB5;','マイクロ記号'],
['∞','&infin;','&#8734;','&#x221E;','無限大'],
['≈','&asymp;','&#8776;','&#x2248;','ほぼ等しい'],
['≠','&ne;','&#8800;','&#x2260;','等しくない'],
['≤','&le;','&#8804;','&#x2264;','以下'],
['≥','&ge;','&#8805;','&#x2265;','以上'],
['∑','&sum;','&#8721;','&#x2211;','総和記号'],
['√','&radic;','&#8730;','&#x221A;','平方根'],
];

var tbody=document.getElementById('hec-ref-body');
refData.forEach(function(row){
var tr=document.createElement('tr');
var charTd=document.createElement('td');
charTd.textContent=row[0]=='\u00A0'?'(空白)':row[0];
tr.appendChild(charTd);
for(var i=1;i<=3;i++){
var td=document.createElement('td');
td.textContent=row[i];
td.className='hec-click-cell';
(function(val){td.addEventListener('click',function(){navigator.clipboard.writeText(val).then(function(){showToast('コピーしました: '+val)})});})(row[i]);
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
if(!val){showToast('コピーするテキストがありません');return;}
navigator.clipboard.writeText(val).then(function(){showToast('クリップボードにコピーしました!')});
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

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

## 関連ツール

> Html Beautifier → [Html Beautifierツール](/ja/tools/html-beautifier/)
> Html Entity Encoder → [Html Entity Encoderツール](/ja/tools/html-entity-encoder/)
> Html Table Generator → [Html Table Generatorツール](/ja/tools/html-table-generator/)

