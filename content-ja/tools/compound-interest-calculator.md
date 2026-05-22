---
title: "複利計算ツール｜元本・利率・期間から将来の資産額を自動計算【無料】"
slug: "compound-interest-calculator"
description: "無料の複利計算ツール。定期積立・複利頻度を設定して資産成長をシミュレート。成長チャート付き。"
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
date: 2025-04-08
ShowToc: false
cover:
  image: "/images/covers/compound-interest-calculator-ja.png"
---

無料の複利計算ツールです。元本・毎月の積立額・年利・複利頻度・運用期間を入力すると、資産の成長をシミュレートできます。ビジュアルな成長チャートと年別の詳細テーブル付き。

<div id="ci-app">
<style>
#ci-app *,#ci-app *::before,#ci-app *::after{box-sizing:border-box;margin:0;padding:0}
#ci-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Kaku Gothic ProN','Noto Sans JP',sans-serif;color:#1a1a2e;max-width:860px;margin:0 auto}
#ci-app .ci-card{background:#fff;border:1px solid #e2e8f0;border-radius:14px;padding:28px 32px;margin-bottom:24px;box-shadow:0 2px 8px rgba(0,0,0,.06)}
#ci-app .ci-card h2{font-size:1.05rem;font-weight:700;color:#1a1a2e;margin-bottom:20px;padding-bottom:10px;border-bottom:2px solid #f0f4ff}
#ci-app .ci-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:16px}
#ci-app .ci-field label{display:block;font-size:.78rem;font-weight:700;color:#4a5568;margin-bottom:6px;letter-spacing:.03em}
#ci-app .ci-field .ci-wrap{position:relative}
#ci-app .ci-field .ci-pre{position:absolute;left:11px;top:50%;transform:translateY(-50%);color:#a0aec0;font-size:.9rem;pointer-events:none}
#ci-app .ci-field .ci-suf{position:absolute;right:11px;top:50%;transform:translateY(-50%);color:#a0aec0;font-size:.88rem;pointer-events:none}
#ci-app .ci-field input,#ci-app .ci-field select{width:100%;padding:10px 12px;border:1.5px solid #cbd5e0;border-radius:8px;font-size:.97rem;color:#1a1a2e;background:#fafbfc;outline:none;transition:border-color .2s,box-shadow .2s;-moz-appearance:textfield;appearance:textfield}
#ci-app .ci-field input::-webkit-outer-spin-button,#ci-app .ci-field input::-webkit-inner-spin-button{-webkit-appearance:none}
#ci-app .ci-field input:focus,#ci-app .ci-field select:focus{border-color:#4f8ef7;box-shadow:0 0 0 3px rgba(79,142,247,.15)}
#ci-app .ci-field.has-pre input{padding-left:26px}
#ci-app .ci-field.has-suf input{padding-right:40px}
#ci-app .ci-btn{display:block;width:100%;padding:14px;background:linear-gradient(135deg,#4f8ef7 0%,#3b6fd4 100%);color:#fff;font-size:1rem;font-weight:700;border:none;border-radius:10px;cursor:pointer;margin-top:10px;letter-spacing:.04em;transition:opacity .2s,transform .15s}
#ci-app .ci-btn:hover{opacity:.91;transform:translateY(-1px)}
#ci-app .ci-btn:active{transform:none}
#ci-app .ci-summary{display:grid;grid-template-columns:repeat(auto-fit,minmax(155px,1fr));gap:12px}
#ci-app .ci-stat{border-radius:10px;padding:16px 14px;text-align:center;background:linear-gradient(135deg,#f0f4ff,#e8f0fe)}
#ci-app .ci-stat.hi{background:linear-gradient(135deg,#4f8ef7,#3b6fd4)}
#ci-app .ci-stat .sl{font-size:.73rem;font-weight:700;letter-spacing:.03em;color:#4a5568;margin-bottom:4px}
#ci-app .ci-stat.hi .sl{color:rgba(255,255,255,.82)}
#ci-app .ci-stat .sv{font-size:1.28rem;font-weight:800;color:#1a1a2e}
#ci-app .ci-stat.hi .sv{color:#fff}
#ci-app .ci-note{font-size:.81rem;color:#718096;margin-top:14px;line-height:1.7}
#ci-app .ci-chart-outer{width:100%;overflow-x:auto}
#ci-app canvas{display:block;max-width:100%}
#ci-app .ci-legend{display:flex;justify-content:center;gap:22px;margin-top:12px;flex-wrap:wrap}
#ci-app .ci-legend-item{display:flex;align-items:center;gap:7px;font-size:.83rem;color:#4a5568;font-weight:500}
#ci-app .ci-legend-dash{width:18px;height:3px;border-radius:2px}
#ci-app .ci-table-outer{width:100%;overflow-x:auto}
#ci-app table{width:100%;border-collapse:collapse;font-size:.87rem;min-width:480px}
#ci-app table thead th{background:#f0f4ff;color:#4a5568;font-size:.74rem;font-weight:700;letter-spacing:.03em;padding:9px 12px;text-align:right;border-bottom:2px solid #e2e8f0;white-space:nowrap}
#ci-app table thead th:first-child{text-align:center}
#ci-app table tbody td{padding:8px 12px;text-align:right;border-bottom:1px solid #f0f4f8;color:#2d3748}
#ci-app table tbody td:first-child{text-align:center;font-weight:700;color:#4f8ef7}
#ci-app table tbody tr:hover{background:#f7faff}
#ci-app table tfoot td{padding:9px 12px;text-align:right;background:#f0f4ff;font-weight:700;color:#1a1a2e;border-top:2px solid #e2e8f0}
#ci-app table tfoot td:first-child{text-align:center}
#ci-app .ci-hidden{display:none!important}
#ci-app .ci-cta{background:linear-gradient(135deg,#fff7ed,#fef3c7);border:1.5px solid #f6ad55;border-radius:12px;padding:22px 26px;margin-bottom:24px}
#ci-app .ci-cta h3{font-size:.97rem;font-weight:700;color:#744210;margin-bottom:8px}
#ci-app .ci-cta p{font-size:.87rem;color:#7d5a20;line-height:1.65;margin-bottom:12px}
#ci-app .ci-cta a.ci-cta-btn{display:inline-block;padding:10px 22px;background:linear-gradient(135deg,#f6ad55,#ed8936);color:#fff;font-size:.92rem;font-weight:700;border-radius:8px;text-decoration:none;letter-spacing:.04em;transition:opacity .2s}
#ci-app .ci-cta a.ci-cta-btn:hover{opacity:.88}
#ci-app .ci-af{font-size:.75rem;color:#a0aec0;margin-top:6px}
#ci-app .ci-related{background:#f7faff;border:1px solid #e2e8f0;border-radius:12px;padding:20px 24px;margin-top:8px}
#ci-app .ci-related h3{font-size:.97rem;font-weight:700;color:#1a1a2e;margin-bottom:12px}
#ci-app .ci-related ul{list-style:none;display:flex;flex-wrap:wrap;gap:10px}
#ci-app .ci-related ul li a{display:inline-block;padding:7px 15px;background:#fff;border:1.5px solid #4f8ef7;border-radius:8px;color:#4f8ef7;font-size:.88rem;font-weight:600;text-decoration:none;transition:background .18s,color .18s}
#ci-app .ci-related ul li a:hover{background:#4f8ef7;color:#fff}
@media(max-width:520px){#ci-app .ci-card{padding:18px 14px}#ci-app .ci-stat .sv{font-size:1.05rem}}
</style>

<!-- Input Card -->
<div class="ci-card">
<h2>計算条件の入力</h2>
<div class="ci-grid">
<div class="ci-field has-pre">
<label>初期元本（円）</label>
<div class="ci-wrap"><span class="ci-pre">¥</span><input type="number" id="ci-principal" value="1000000" min="0" step="10000"></div>
</div>
<div class="ci-field has-pre">
<label>毎月の積立額（円）</label>
<div class="ci-wrap"><span class="ci-pre">¥</span><input type="number" id="ci-monthly" value="30000" min="0" step="1000"></div>
</div>
<div class="ci-field has-suf">
<label>年利（%）</label>
<div class="ci-wrap"><input type="number" id="ci-rate" value="5" min="0" max="100" step="0.1"><span class="ci-suf">%</span></div>
</div>
<div class="ci-field">
<label>複利の頻度</label>
<select id="ci-freq">
<option value="365">毎日</option>
<option value="12" selected>毎月</option>
<option value="4">四半期</option>
<option value="1">毎年</option>
</select>
</div>
<div class="ci-field has-suf">
<label>運用期間</label>
<div class="ci-wrap"><input type="number" id="ci-years" value="20" min="1" max="50" step="1"><span class="ci-suf">年</span></div>
</div>
</div>
<button class="ci-btn" onclick="ciCalc()">資産成長を計算する</button>
</div>

<!-- Summary Card -->
<div class="ci-card ci-hidden" id="ci-res-card">
<h2>計算結果サマリー</h2>
<div class="ci-summary" id="ci-summary"></div>
<p class="ci-note" id="ci-note"></p>
</div>

<!-- Chart Card -->
<div class="ci-card ci-hidden" id="ci-chart-card">
<h2>資産成長チャート</h2>
<div class="ci-chart-outer">
<canvas id="ci-canvas"></canvas>
</div>
<div class="ci-legend">
<div class="ci-legend-item"><div class="ci-legend-dash" style="background:#4f8ef7"></div>総残高</div>
<div class="ci-legend-item"><div class="ci-legend-dash" style="background:#94b8fb"></div>累計投資額</div>
</div>
</div>

<!-- Table Card -->
<div class="ci-card ci-hidden" id="ci-table-card">
<h2>年別の内訳</h2>
<div class="ci-table-outer">
<table>
<thead>
<tr>
<th>年</th>
<th>期首残高</th>
<th>年間積立額</th>
<th>利息</th>
<th>期末残高</th>
<th>累計利息</th>
</tr>
</thead>
<tbody id="ci-tbody"></tbody>
<tfoot id="ci-tfoot"></tfoot>
</table>
</div>
</div>

<!-- freee CTA -->
<div class="ci-cta">
<h3>資産管理・確定申告は freee で効率化</h3>
<p>投資収益の記録や確定申告の手続きを、freee 会計なら自動仕訳でラクに管理できます。個人投資家にも対応した国内シェアNo.1のクラウド会計ソフトです。</p>
<a class="ci-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener sponsored">freee を無料で試す</a>
<p class="ci-af">※本リンクはアフィリエイトリンクを含む場合があります。</p>
</div>

<!-- Related Tools -->
<div class="ci-related">
<h3>関連する無料ツール</h3>
<ul>
<li><a href="/tools/savings-goal-calculator/">貯蓄目標計算ツール</a></li>
<li><a href="/tools/roi-calculator/">ROI計算ツール</a></li>
</ul>
</div>

<script>
(function(){
function fmtN(n){return n.toLocaleString('ja-JP',{minimumFractionDigits:0,maximumFractionDigits:0});}
function fmtY(n){
var a=Math.abs(n);
if(a>=1e8)return(n/1e8).toFixed(2)+'億円';
if(a>=1e4)return(n/1e4).toFixed(1)+'万円';
return fmtN(n)+'円';
}
function freqLabel(n){return{365:'毎日',12:'毎月',4:'四半期ごと',1:'毎年'}[n]||'毎月';}

function buildRows(principal,monthly,rate,n,years){
var r=rate/100;
var rows=[];
var balance=principal;
var cumInterest=0;
for(var y=1;y<=years;y++){
var open=balance;
var yearContrib=monthly*12;
var bal=open;
if(n>=12){
var periodsPerMonth=n/12;
for(var m=0;m<12;m++){
bal+=monthly;
for(var pp=0;pp<periodsPerMonth;pp++){
bal=bal*(1+r/n);
}
}
} else {
var periodsPerYear=n;
var monthsPerPeriod=12/periodsPerYear;
for(var p=0;p<periodsPerYear;p++){
bal+=monthly*monthsPerPeriod;
bal=bal*(1+r/n);
}
}
var interest=bal-(open+yearContrib);
cumInterest+=interest;
rows.push({year:y,open:open,contrib:yearContrib,interest:interest,close:bal,cumInterest:cumInterest});
balance=bal;
}
return rows;
}

window.ciCalc=function(){
var principal=Math.max(0,parseFloat(document.getElementById('ci-principal').value)||0);
var monthly=Math.max(0,parseFloat(document.getElementById('ci-monthly').value)||0);
var rate=Math.max(0,parseFloat(document.getElementById('ci-rate').value)||0);
var n=parseInt(document.getElementById('ci-freq').value)||12;
var years=Math.min(50,Math.max(1,parseInt(document.getElementById('ci-years').value)||20));

var rows=buildRows(principal,monthly,rate,n,years);
var last=rows[rows.length-1];
var totalContrib=principal+monthly*12*years;
var totalInterest=last.cumInterest;
var finalBalance=last.close;

['ci-res-card','ci-chart-card','ci-table-card'].forEach(function(id){
document.getElementById(id).classList.remove('ci-hidden');
});

var stats=[
{label:'最終残高',value:fmtY(Math.round(finalBalance)),hi:true},
{label:'累計投資額',value:fmtY(Math.round(totalContrib)),hi:false},
{label:'累計利息',value:fmtY(Math.round(totalInterest)),hi:false},
{label:'利息 / 投資額',value:(totalContrib>0?(totalInterest/totalContrib*100).toFixed(1):0)+'%',hi:false}
];
document.getElementById('ci-summary').innerHTML=stats.map(function(s){
return'<div class="ci-stat'+(s.hi?' hi':'')+'"><div class="sl">'+s.label+'</div><div class="sv">'+s.value+'</div></div>';
}).join('');
document.getElementById('ci-note').textContent=
'年利'+rate+'%・'+freqLabel(n)+'複利・運用期間'+years+'年。'+
'初期元本'+fmtY(Math.round(principal))+'＋毎月積立'+fmtY(Math.round(monthly))+'で試算。';

var tbody=document.getElementById('ci-tbody');
tbody.innerHTML=rows.map(function(r){
return'<tr>'+
'<td>'+r.year+'</td>'+
'<td>'+fmtY(Math.round(r.open))+'</td>'+
'<td>'+fmtY(Math.round(r.contrib))+'</td>'+
'<td style="color:#2f855a">'+fmtY(Math.round(r.interest))+'</td>'+
'<td><strong>'+fmtY(Math.round(r.close))+'</strong></td>'+
'<td style="color:#2f855a">'+fmtY(Math.round(r.cumInterest))+'</td>'+
'</tr>';
}).join('');
document.getElementById('ci-tfoot').innerHTML=
'<tr>'+
'<td>合計</td>'+
'<td>—</td>'+
'<td>'+fmtY(Math.round(totalContrib))+'</td>'+
'<td>'+fmtY(Math.round(totalInterest))+'</td>'+
'<td>'+fmtY(Math.round(finalBalance))+'</td>'+
'<td>'+fmtY(Math.round(totalInterest))+'</td>'+
'</tr>';

drawChart(rows,principal);
};

function drawChart(rows,principal){
var canvas=document.getElementById('ci-canvas');
var W=Math.max(300,canvas.parentElement.clientWidth||760);
var H=320;
canvas.width=W;
canvas.height=H;
var ctx=canvas.getContext('2d');
ctx.clearRect(0,0,W,H);

var pad={t:20,r:20,b:44,l:88};
var cw=W-pad.l-pad.r;
var ch=H-pad.t-pad.b;
var yrs=rows.length;

var balances=rows.map(function(r){return r.close;});
var contribs=[];
var acc=principal;
rows.forEach(function(r){acc+=r.contrib;contribs.push(acc);});

var maxVal=Math.max.apply(null,balances);
var mag=Math.pow(10,Math.floor(Math.log10(maxVal||1)));
var niceMax=Math.ceil(maxVal/mag)*mag;
var gridN=5;

ctx.font='11px -apple-system,sans-serif';
ctx.textAlign='right';
ctx.textBaseline='middle';
for(var i=0;i<=gridN;i++){
var v=niceMax*i/gridN;
var yp=pad.t+ch-ch*(i/gridN);
ctx.strokeStyle='#e8edf3';ctx.lineWidth=1;
ctx.beginPath();ctx.moveTo(pad.l,yp);ctx.lineTo(pad.l+cw,yp);ctx.stroke();
ctx.fillStyle='#8896a5';
ctx.fillText(fmtY(Math.round(v)),pad.l-5,yp);
}

ctx.textAlign='center';ctx.textBaseline='top';ctx.fillStyle='#8896a5';
var xStep=Math.max(1,Math.ceil(yrs/8));
for(var xi=0;xi<yrs;xi++){
if(xi===0||xi===yrs-1||(xi+1)%xStep===0){
var xp=pad.l+cw*(xi/(yrs-1||1));
ctx.fillText((xi+1)+'年',xp,pad.t+ch+8);
}
}

function plotLine(data,lineColor,fillColor){
var pts=data.map(function(v,i){
return{x:pad.l+cw*(i/(yrs-1||1)),y:pad.t+ch-ch*(v/niceMax)};
});
ctx.beginPath();
ctx.moveTo(pts[0].x,pad.t+ch);
pts.forEach(function(p){ctx.lineTo(p.x,p.y);});
ctx.lineTo(pts[pts.length-1].x,pad.t+ch);
ctx.closePath();
ctx.fillStyle=fillColor;ctx.fill();
ctx.beginPath();
pts.forEach(function(p,i){i===0?ctx.moveTo(p.x,p.y):ctx.lineTo(p.x,p.y);});
ctx.strokeStyle=lineColor;ctx.lineWidth=2.5;ctx.lineJoin='round';ctx.stroke();
var lp=pts[pts.length-1];
ctx.beginPath();ctx.arc(lp.x,lp.y,5,0,Math.PI*2);
ctx.fillStyle=lineColor;ctx.fill();
}

plotLine(balances,'#4f8ef7','rgba(79,142,247,.13)');
plotLine(contribs,'#94b8fb','rgba(148,184,251,.10)');
}

window.ciCalc();
})();
</script>
</div>

---

### 関連ツール

- [貯蓄目標計算ツール](/tools/savings-goal-calculator/) — 目標金額に到達するために必要な毎月の積立額を逆算できます。
- [ROI計算ツール](/tools/roi-calculator/) — 投資・施策のリターンをすばやく計測できます。

## 関連記事

- [新NISA始め方2026年版【初心者向け完全ガイド】口座開設から投資スタートまで](/ja/posts/shin-nisa-hajimekata-shoshinsha-2026/)
- [NISA iDeCo どっちを先に始めるべき？優先順位を徹底解説【2026年最新版】](/ja/posts/nisa-ideco-docchi-saki/)
- [投資信託 おすすめ 初心者向け厳選ファンド完全比較【2026年最新版】](/ja/posts/toushishintaku-osusume-2026/)
