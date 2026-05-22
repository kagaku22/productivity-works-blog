---
title: "借金返済シミュレーター - スノーボール＆アバランチ法"
date: 2025-06-12
description: "無料の借金返済シミュレーター。スノーボール法（少額優先）とアバランチ法（高金利優先）を比較し、総利息・完済日・月別返済スケジュールを自動計算。最速で借金ゼロになる方法を見つけましょう。"
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
slug: "debt-payoff-calculator"
ShowToc: false
cover:
  image: "/images/covers/debt-payoff-calculator.png"
  alt: "借金返済シミュレーター"
---

<div id="dpcja-app">

<style>
#dpcja-app *,#dpcja-app *::before,#dpcja-app *::after{box-sizing:border-box;}
#dpcja-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Kaku Gothic ProN','Noto Sans JP',sans-serif;max-width:920px;margin:0 auto;color:#1e293b;line-height:1.7;}
#dpcja-app h2{font-size:1.2rem;font-weight:700;margin:0 0 1rem;color:#0f172a;}
#dpcja-app h3{font-size:1rem;font-weight:600;margin:0 0 .75rem;color:#1e293b !important;color-scheme:light;}
#dpcja-app .dpcja-hero{background:linear-gradient(135deg,#dc2626 0%,#7c3aed 100%);color:#fff;border-radius:16px;padding:1.5rem 2rem;margin-bottom:1.5rem;}
#dpcja-app .dpcja-hero h2{color:#fff;font-size:1.45rem;margin:0 0 .5rem;}
#dpcja-app .dpcja-hero p{margin:0;opacity:.9;font-size:.93rem;}
#dpcja-app .dpcja-card{background:#fff;border:1px solid #e2e8f0;border-radius:12px;padding:1.5rem;margin-bottom:1.25rem;box-shadow:0 1px 4px rgba(0,0,0,.06);}
#dpcja-app .dpcja-debt-row{display:grid;grid-template-columns:1.4fr 1fr 1fr 1fr auto;gap:.6rem;align-items:end;padding:.75rem;background:#f8fafc;border-radius:10px;margin-bottom:.6rem;border:1px solid #e2e8f0;}
#dpcja-app .dpcja-field label{display:block;font-size:.72rem;font-weight:700;color:#64748b;margin-bottom:.25rem;text-transform:uppercase;letter-spacing:.04em;}
#dpcja-app .dpcja-field input{width:100%;padding:.48rem .6rem;border:1.5px solid #cbd5e1;border-radius:8px;font-size:.9rem;background:#fff;transition:border-color .2s;}
#dpcja-app .dpcja-field input:focus{outline:none;border-color:#dc2626;}
#dpcja-app .dpcja-extra-row{display:flex;align-items:center;gap:1rem;flex-wrap:wrap;}
#dpcja-app .dpcja-extra-row label{font-weight:600;color:#374151;font-size:.9rem;white-space:nowrap;}
#dpcja-app .dpcja-extra-row input{width:160px;padding:.5rem .75rem;border:1.5px solid #cbd5e1;border-radius:8px;font-size:.95rem;background:#f8fafc;}
#dpcja-app .dpcja-extra-row input:focus{outline:none;border-color:#dc2626;background:#fff;}
#dpcja-app .dpcja-extra-row .dpcja-unit{color:#64748b;font-size:.88rem;}
#dpcja-app .dpcja-btn{display:inline-flex;align-items:center;gap:.4rem;padding:.5rem 1.1rem;border-radius:8px;font-size:.88rem;font-weight:700;cursor:pointer;border:none;transition:all .18s;}
#dpcja-app .dpcja-btn-primary{background:linear-gradient(135deg,#dc2626,#7c3aed);color:#fff;box-shadow:0 2px 8px rgba(220,38,38,.3);}
#dpcja-app .dpcja-btn-primary:hover{transform:translateY(-1px);box-shadow:0 4px 14px rgba(220,38,38,.4);}
#dpcja-app .dpcja-btn-add{background:#fef2f2;color:#dc2626;border:1.5px solid #fecaca;}
#dpcja-app .dpcja-btn-add:hover{background:#fee2e2;}
#dpcja-app .dpcja-btn-remove{background:#fef2f2;color:#dc2626;border:1.5px solid #fecaca;padding:.45rem .65rem;border-radius:8px;cursor:pointer;font-size:.9rem;font-weight:700;}
#dpcja-app .dpcja-btn-remove:hover{background:#fee2e2;}
#dpcja-app .dpcja-btn-reset{background:#f1f5f9;color:#374151;border:1.5px solid #e2e8f0;}
#dpcja-app .dpcja-btn-reset:hover{background:#e2e8f0;}
#dpcja-app .dpcja-actions{display:flex;gap:.75rem;flex-wrap:wrap;align-items:center;margin-top:1rem;}
#dpcja-app .dpcja-error{background:#fef2f2;border:1px solid #fecaca;border-radius:8px;padding:.75rem 1rem;color:#dc2626;font-size:.88rem;margin-bottom:1rem;display:none;}
#dpcja-app .dpcja-results{display:none;}
#dpcja-app .dpcja-results.active{display:block;}
#dpcja-app .dpcja-winner{display:flex;align-items:center;gap:.5rem;background:linear-gradient(90deg,#10b981,#059669);color:#fff;border-radius:10px;padding:.7rem 1.1rem;font-size:.9rem;font-weight:700;margin-bottom:1.25rem;}
#dpcja-app .dpcja-compare-grid{display:grid;grid-template-columns:1fr 1fr;gap:1.25rem;margin-bottom:1.25rem;}
#dpcja-app .dpcja-method-card{border-radius:12px;padding:1.25rem 1.5rem;}
#dpcja-app .dpcja-method-card.snow{background:linear-gradient(135deg,#fef2f2,#ede9fe);border:2px solid #fca5a5;}
#dpcja-app .dpcja-method-card.aval{background:linear-gradient(135deg,#fce7f3,#fef3c7);border:2px solid #f9a8d4;}
#dpcja-app .dpcja-badge{display:inline-block;font-size:.7rem;font-weight:800;letter-spacing:.06em;text-transform:uppercase;padding:.2rem .65rem;border-radius:99px;margin-bottom:.75rem;}
#dpcja-app .snow .dpcja-badge{background:#dc2626;color:#fff;}
#dpcja-app .aval .dpcja-badge{background:#7c3aed;color:#fff;}
#dpcja-app .dpcja-stat{margin-bottom:.55rem;}
#dpcja-app .dpcja-stat-label{font-size:.72rem;color:#64748b;font-weight:700;text-transform:uppercase;letter-spacing:.04em;}
#dpcja-app .dpcja-stat-value{font-size:1.35rem;font-weight:800;color:#0f172a;}
#dpcja-app .dpcja-chart-wrap{background:#f8fafc;border-radius:12px;padding:1rem;margin-bottom:1.25rem;}
#dpcja-app .dpcja-chart-wrap h2{margin-bottom:.75rem;}
#dpcja-app canvas#dpcja-chart{width:100%;display:block;border-radius:8px;}
#dpcja-app .dpcja-legend{display:flex;gap:1.5rem;margin-top:.65rem;font-size:.82rem;color:#475569;flex-wrap:wrap;}
#dpcja-app .dpcja-legend-item{display:flex;align-items:center;gap:.4rem;}
#dpcja-app .dpcja-legend-dot{width:14px;height:4px;border-radius:2px;flex-shrink:0;}
#dpcja-app .dpcja-tabs{display:flex;border-bottom:2px solid #e2e8f0;margin-bottom:1rem;}
#dpcja-app .dpcja-tab{padding:.55rem 1.2rem;font-size:.88rem;font-weight:700;color:#64748b;cursor:pointer;border:none;background:none;border-bottom:2px solid transparent;margin-bottom:-2px;transition:all .15s;}
#dpcja-app .dpcja-tab.active{color:#dc2626;border-bottom-color:#dc2626;}
#dpcja-app .dpcja-schedule-wrap{overflow-x:auto;}
#dpcja-app table.dpcja-table{width:100%;border-collapse:collapse;font-size:.82rem;}
#dpcja-app table.dpcja-table th{background:#f1f5f9;padding:.5rem .7rem;text-align:right;font-weight:700;color:#374151;font-size:.74rem;text-transform:uppercase;letter-spacing:.03em;white-space:nowrap;}
#dpcja-app table.dpcja-table th:first-child,#dpcja-app table.dpcja-table th:nth-child(2){text-align:left;}
#dpcja-app table.dpcja-table td{padding:.42rem .7rem;text-align:right;border-bottom:1px solid #f1f5f9;color:#334155;}
#dpcja-app table.dpcja-table td:first-child,#dpcja-app table.dpcja-table td:nth-child(2){text-align:left;}
#dpcja-app table.dpcja-table tr:hover td{background:#f8fafc;}
#dpcja-app .dpcja-paid-cell{color:#10b981;font-weight:700;}
#dpcja-app .dpcja-show-more{text-align:center;margin-top:.75rem;}
#dpcja-app .dpcja-cta{background:linear-gradient(135deg,#f0fdf4,#dcfce7);border:1.5px solid #86efac;border-radius:12px;padding:1rem 1.25rem;margin-top:1.5rem;font-size:.9rem;color:#166534;}
#dpcja-app .dpcja-cta a{color:#15803d;font-weight:700;}
#dpcja-app .dpcja-related{margin-top:2rem;padding-top:1.5rem;border-top:1px solid #e2e8f0;}
#dpcja-app .dpcja-related h3{font-size:1rem;color:#374151;margin-bottom:.75rem;}
#dpcja-app .dpcja-related-links{display:flex;gap:.65rem;flex-wrap:wrap;}
#dpcja-app .dpcja-related-links a{display:inline-flex;align-items:center;background:#fef2f2;color:#dc2626;border-radius:8px;padding:.42rem .9rem;font-size:.85rem;font-weight:600;text-decoration:none;transition:background .15s;}
#dpcja-app .dpcja-related-links a:hover{background:#fee2e2;}
@media(max-width:640px){
#dpcja-app .dpcja-debt-row{grid-template-columns:1fr 1fr;}
#dpcja-app .dpcja-debt-row>div:last-child{grid-column:span 2;text-align:right;}
#dpcja-app .dpcja-compare-grid{grid-template-columns:1fr;}
#dpcja-app .dpcja-hero{padding:1.25rem;}
}
</style>

<div class="dpcja-hero">
<h2>借金返済シミュレーター</h2>
<p>借入先ごとに残高・金利・最低返済額を入力して、<strong>スノーボール法</strong>（少額優先）と<strong>アバランチ法</strong>（高金利優先）を比較。総利息・完済日・月別スケジュールを自動計算します。</p>
</div>

<div class="dpcja-card">
<h2>借入一覧</h2>
<div id="dpcja-debt-list"></div>
<button class="dpcja-btn dpcja-btn-add" onclick="dpcjaAddDebt()" style="margin-top:.5rem;">＋ 借入を追加</button>
</div>

<div class="dpcja-card">
<h2>追加返済額（月額）</h2>
<div class="dpcja-extra-row">
<label for="dpcja-extra">最低返済額に上乗せする金額：</label>
<input type="number" id="dpcja-extra" placeholder="0" min="0" step="1000" value="10000">
<span class="dpcja-unit">円 / 月</span>
</div>
</div>

<div class="dpcja-error" id="dpcja-error"></div>

<div class="dpcja-actions">
<button class="dpcja-btn dpcja-btn-primary" onclick="dpcjaCalculate()">&#9654;&#xFE0E; 返済プランを計算する</button>
<button class="dpcja-btn dpcja-btn-reset" onclick="dpcjaReset()">リセット</button>
</div>

<div class="dpcja-results" id="dpcja-results">

<div style="margin-top:1.5rem;">

<div class="dpcja-winner" id="dpcja-winner-msg"></div>

<div class="dpcja-compare-grid">
<div class="dpcja-method-card snow" id="dpcja-snow-card"></div>
<div class="dpcja-method-card aval" id="dpcja-aval-card"></div>
</div>

<div class="dpcja-card dpcja-chart-wrap">
<h2>残高推移グラフ</h2>
<canvas id="dpcja-chart" height="280"></canvas>
<div class="dpcja-legend">
<div class="dpcja-legend-item"><div class="dpcja-legend-dot" style="background:#dc2626;"></div>スノーボール法</div>
<div class="dpcja-legend-item"><div class="dpcja-legend-dot" style="background:#7c3aed;"></div>アバランチ法</div>
<div class="dpcja-legend-item"><div class="dpcja-legend-dot" style="background:#94a3b8;"></div>最低返済のみ</div>
</div>
</div>

<div class="dpcja-card">
<h2>月別返済スケジュール</h2>
<div class="dpcja-tabs">
<button class="dpcja-tab active" id="dpcja-tab-snow" onclick="dpcjaShowTab('snow')">スノーボール法</button>
<button class="dpcja-tab" id="dpcja-tab-aval" onclick="dpcjaShowTab('aval')">アバランチ法</button>
</div>
<div id="dpcja-sched-snow" class="dpcja-schedule-wrap"></div>
<div id="dpcja-sched-aval" class="dpcja-schedule-wrap" style="display:none;"></div>
</div>

</div>

</div>

<div class="dpcja-cta">
家計管理をもっと効率的に &#8594; <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で収支を自動管理</a>
</div>

<script>
(function(){
'use strict';
var _debts=[];
var _nextId=1;
var _schedData={snow:[],aval:[]};
var _showN={snow:24,aval:24};

function $id(id){return document.getElementById(id);}

function fmtYen(n){return Math.round(n).toLocaleString('ja-JP')+'円';}
function fmtYen2(n){return Math.round(n).toLocaleString('ja-JP')+'円';}
function fmtMonth(offsetMonths){
var d=new Date(2025,4,1);
d.setMonth(d.getMonth()+offsetMonths);
return d.getFullYear()+'年'+(d.getMonth()+1)+'月';
}

window.dpcjaAddDebt=function(name,balance,rate,minPay){
var id=_nextId++;
_debts.push(id);
var list=$id('dpcja-debt-list');
var div=document.createElement('div');
div.id='dpcja-dr-'+id;
div.className='dpcja-debt-row';
div.innerHTML=
'<div class="dpcja-field"><label>借入先名</label><input type="text" id="dpcja-n-'+id+'" placeholder="例：リボ払い" value="'+(name||'')+'"></div>'+
'<div class="dpcja-field"><label>残高（円）</label><input type="number" id="dpcja-b-'+id+'" placeholder="500000" min="1" step="10000" value="'+(balance||'')+'"></div>'+
'<div class="dpcja-field"><label>年利（%）</label><input type="number" id="dpcja-r-'+id+'" placeholder="15" min="0" step="0.1" value="'+(rate||'')+'"></div>'+
'<div class="dpcja-field"><label>月々返済額（円）</label><input type="number" id="dpcja-m-'+id+'" placeholder="15000" min="1" step="1000" value="'+(minPay||'')+'"></div>'+
'<div><button class="dpcja-btn-remove" onclick="dpcjaRemoveDebt('+id+')" title="削除">&#10005;</button></div>';
list.appendChild(div);
};

window.dpcjaRemoveDebt=function(id){
var idx=_debts.indexOf(id);
if(idx>-1)_debts.splice(idx,1);
var el=$id('dpcja-dr-'+id);
if(el)el.remove();
};

window.dpcjaReset=function(){
_debts=[];_nextId=1;
$id('dpcja-debt-list').innerHTML='';
$id('dpcja-results').classList.remove('active');
$id('dpcja-error').style.display='none';
$id('dpcja-extra').value='10000';
dpcjaAddDebt('リボ払い',500000,15,15000);
dpcjaAddDebt('カードローン',800000,8,20000);
dpcjaAddDebt('消費者金融',200000,18,10000);
};

function getDebtsInput(){
var out=[];
for(var i=0;i<_debts.length;i++){
var id=_debts[i];
var n=($id('dpcja-n-'+id).value.trim())||('借入'+(i+1));
var b=parseFloat($id('dpcja-b-'+id).value);
var r=parseFloat($id('dpcja-r-'+id).value);
var m=parseFloat($id('dpcja-m-'+id).value);
if(isNaN(b)||b<=0||isNaN(r)||r<0||isNaN(m)||m<=0)return null;
out.push({name:n,balance:b,rate:r,minPay:m});
}
return out;
}

function simulate(debtsInput,extra,sortFn){
var ds=debtsInput.map(function(d){return{name:d.name,bal:d.balance,rate:d.rate,minPay:d.minPay,done:false};});
var months=0,totalInterest=0;
var balHistory=[ds.reduce(function(s,d){return s+d.bal;},0)];
var schedule=[];
var MAX=600;

while(months<MAX){
var open=ds.filter(function(d){return !d.done;});
if(!open.length)break;
ds.sort(sortFn);
months++;
var monthRow=[];
var freed=0;

for(var i=0;i<ds.length;i++){
var d=ds[i];
if(d.done){monthRow.push({name:d.name,done:true});continue;}
var interest=d.bal*(d.rate/100/12);
totalInterest+=interest;
var pay=d.minPay+freed;
freed=0;
if(pay<interest+0.01)pay=interest+0.01;
var prin=Math.min(pay-interest,d.bal);
d.bal=Math.max(0,d.bal-prin);
var actualPay=interest+prin;
if(d.bal<=1){freed+=(d.minPay);d.bal=0;d.done=true;}
monthRow.push({name:d.name,pay:actualPay,interest:interest,principal:prin,bal:d.bal,justDone:d.done});
}

if(extra>0){
var left=extra;
for(var j=0;j<ds.length;j++){
if(ds[j].done||left<=0)continue;
var apply=Math.min(left,ds[j].bal);
ds[j].bal=Math.max(0,ds[j].bal-apply);
left-=apply;
if(ds[j].bal<=1){ds[j].bal=0;ds[j].done=true;}
}
}

var totBal=ds.reduce(function(s,d){return s+d.bal;},0);
balHistory.push(Math.max(0,totBal));
schedule.push({month:months,debts:monthRow,totBal:totBal});
}

return{months:months,totalInterest:totalInterest,balHistory:balHistory,schedule:schedule};
}

window.dpcjaCalculate=function(){
var err=$id('dpcja-error');
err.style.display='none';
if(_debts.length===0){err.textContent='借入を1件以上追加してください。';err.style.display='block';return;}
var debtsInput=getDebtsInput();
if(!debtsInput){err.textContent='すべての項目に正しい数値を入力してください。';err.style.display='block';return;}
var extra=parseFloat($id('dpcja-extra').value)||0;

var snowRes=simulate(debtsInput,extra,function(a,b){
if(a.done&&!b.done)return 1;if(!a.done&&b.done)return-1;return a.bal-b.bal;
});
var avalRes=simulate(debtsInput,extra,function(a,b){
if(a.done&&!b.done)return 1;if(!a.done&&b.done)return-1;return b.rate-a.rate;
});

_schedData.snow=snowRes.schedule;
_schedData.aval=avalRes.schedule;
_showN.snow=24;_showN.aval=24;

function buildCard(el,res,cls,label,desc){
el.innerHTML=
'<div class="dpcja-badge">'+label+'</div>'+
'<div style="font-size:.82rem;color:#475569;margin-bottom:.9rem;">'+desc+'</div>'+
'<div class="dpcja-stat"><div class="dpcja-stat-label">支払利息合計</div><div class="dpcja-stat-value">'+fmtYen(res.totalInterest)+'</div></div>'+
'<div class="dpcja-stat"><div class="dpcja-stat-label">完済までの期間</div><div class="dpcja-stat-value">'+res.months+' <span style="font-size:1rem;font-weight:600;">ヶ月</span></div></div>'+
'<div class="dpcja-stat"><div class="dpcja-stat-label">完済予定月</div><div class="dpcja-stat-value" style="font-size:1.1rem;">'+fmtMonth(res.months)+'</div></div>';
}
buildCard($id('dpcja-snow-card'),snowRes,'snow','スノーボール法','残高が少ない借入から優先返済 — 完済件数が増えやすい');
buildCard($id('dpcja-aval-card'),avalRes,'aval','アバランチ法','金利が高い借入から優先返済 — 利息を最小化');

var w=$id('dpcja-winner-msg');
var iDiff=Math.abs(snowRes.totalInterest-avalRes.totalInterest);
var mDiff=Math.abs(snowRes.months-avalRes.months);
var winner=avalRes.totalInterest<=snowRes.totalInterest?'アバランチ法':'スノーボール法';
var msg='&#9989; '+winner+'を選ぶと利息が'+fmtYen(iDiff)+'お得';
if(mDiff>0)msg+='、'+mDiff+'ヶ月早く完済';
msg+='できます！';
if(iDiff<1)msg='&#9989; どちらの方法も利息の差はほぼゼロ。モチベーションに合わせて選択してください！';
w.innerHTML=msg;

drawChart(snowRes.balHistory,avalRes.balHistory);
renderSched('snow');
renderSched('aval');
dpcjaShowTab('snow');
$id('dpcja-results').classList.add('active');
setTimeout(function(){$id('dpcja-results').scrollIntoView({behavior:'smooth',block:'start'});},50);
};

function drawChart(snowH,avalH){
var canvas=$id('dpcja-chart');
var W=canvas.parentElement.clientWidth-32;
canvas.width=Math.max(W,300);
canvas.height=280;
var ctx=canvas.getContext('2d');
var W2=canvas.width,H=canvas.height;
var pL=90,pR=20,pT=20,pB=42;
var cW=W2-pL-pR,cH=H-pT-pB;

var maxLen=Math.max(snowH.length,avalH.length);
var allVals=snowH.concat(avalH);
var maxBal=Math.max.apply(null,allVals)||1;

ctx.clearRect(0,0,W2,H);
ctx.fillStyle='#f8fafc';ctx.fillRect(0,0,W2,H);

ctx.strokeStyle='#e2e8f0';ctx.lineWidth=1;
for(var g=0;g<=5;g++){
var gy=pT+cH-(g/5)*cH;
ctx.beginPath();ctx.moveTo(pL,gy);ctx.lineTo(pL+cW,gy);ctx.stroke();
ctx.fillStyle='#94a3b8';ctx.font='11px sans-serif';ctx.textAlign='right';
var gv=maxBal*g/5;
var label=gv>=10000?Math.round(gv/10000)+'万':'';
if(gv>=1000&&gv<10000)label=Math.round(gv/1000)+'千';
if(gv<1000)label=Math.round(gv)+'';
ctx.fillText(label+'円',pL-5,gy+4);
}

function polyLine(data,color,dash){
if(data.length<2)return;
ctx.save();
ctx.beginPath();
ctx.strokeStyle=color;ctx.lineWidth=2.5;ctx.lineJoin='round';
if(dash)ctx.setLineDash(dash);
for(var i=0;i<data.length;i++){
var x=pL+(i/(maxLen-1))*cW;
var y=pT+cH-(data[i]/maxBal)*cH;
if(i===0)ctx.moveTo(x,y);else ctx.lineTo(x,y);
}
ctx.stroke();ctx.setLineDash([]);
ctx.restore();
}

function fillArea(data,color){
if(data.length<2)return;
ctx.save();
ctx.beginPath();
ctx.moveTo(pL,pT+cH);
for(var i=0;i<data.length;i++){
var x=pL+(i/(maxLen-1))*cW;
var y=pT+cH-(data[i]/maxBal)*cH;
ctx.lineTo(x,y);
}
ctx.lineTo(pL+((data.length-1)/(maxLen-1))*cW,pT+cH);
ctx.closePath();
ctx.fillStyle=color;ctx.globalAlpha=0.07;ctx.fill();
ctx.restore();
}

fillArea(snowH,'#dc2626');
fillArea(avalH,'#7c3aed');
polyLine(snowH,'#dc2626');
polyLine(avalH,'#7c3aed');

ctx.fillStyle='#94a3b8';ctx.font='11px sans-serif';ctx.textAlign='center';
var xStep=maxLen<=13?1:maxLen<=25?3:maxLen<=49?6:12;
for(var m=0;m<maxLen;m+=xStep){
var xp=pL+(m/(maxLen-1))*cW;
ctx.fillText(m+'月',xp,H-pB+18);
}
}

function renderSched(method){
var data=_schedData[method];
var showN=_showN[method];
var wrap=$id('dpcja-sched-'+method);
if(!data||!data.length){wrap.innerHTML='<p style="color:#64748b;font-size:.88rem;">データがありません。</p>';return;}

var names=data[0].debts.map(function(d){return d.name;});
var slice=data.slice(0,showN);

var html='<table class="dpcja-table"><thead><tr><th>月数</th><th>年月</th>';
names.forEach(function(n){html+='<th>'+n+' 返済額</th><th>'+n+' 残高</th>';});
html+='<th>合計残高</th></tr></thead><tbody>';

slice.forEach(function(row){
html+='<tr><td>'+row.month+'</td><td>'+fmtMonth(row.month)+'</td>';
row.debts.forEach(function(d){
if(d.done&&d.pay===undefined){
html+='<td class="dpcja-paid-cell">完済</td><td class="dpcja-paid-cell">0円</td>';
} else {
html+='<td>'+fmtYen2(d.pay||0)+'</td><td>'+fmtYen2(d.bal||0)+'</td>';
}
});
html+='<td><strong>'+fmtYen2(Math.max(0,row.totBal))+'</strong></td></tr>';
});
html+='</tbody></table>';

if(data.length>showN){
var rem=data.length-showN;
html+='<div class="dpcja-show-more"><button class="dpcja-btn dpcja-btn-reset" onclick="dpcjaShowMore(\''+method+'\')">さらに'+rem+'ヶ月分を表示</button></div>';
}
wrap.innerHTML=html;
}

window.dpcjaShowMore=function(method){
_showN[method]+=24;
renderSched(method);
};

window.dpcjaShowTab=function(tab){
$id('dpcja-sched-snow').style.display=tab==='snow'?'block':'none';
$id('dpcja-sched-aval').style.display=tab==='aval'?'block':'none';
$id('dpcja-tab-snow').className='dpcja-tab'+(tab==='snow'?' active':'');
$id('dpcja-tab-aval').className='dpcja-tab'+(tab==='aval'?' active':'');
};

dpcjaAddDebt('リボ払い',500000,15,15000);
dpcjaAddDebt('カードローン',800000,8,20000);
dpcjaAddDebt('消費者金融',200000,18,10000);
})();
</script>

</div>

---

## 関連ツール

> ローン比較 → [ローン比較ツール](/ja/tools/loan-comparison/)
> 住宅ローン借入可能額 → [住宅ローン借入可能額ツール](/ja/tools/mortgage-affordability-calculator/)
> 住宅ローン計算 → [住宅ローン計算ツール](/ja/tools/mortgage-calculator/)

