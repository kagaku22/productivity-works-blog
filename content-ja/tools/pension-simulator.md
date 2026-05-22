---
title: "年金シミュレーター｜将来の受給額を年齢・加入期間から自動計算【2026年版】"
date: 2025-12-14
description: "無料の年金シミュレーター。老後の資産推移・年金受給額・必要な積立額をシミュレーション。グラフ付きで分かりやすい、会員登録不要のオンラインツール。"
categories: ["無料ツール"]
tags: ["便利ツール", "無料ツール"]
slug: "pension-simulator"
ShowToc: false
cover:
  image: "/images/covers/pension-simulator-ja.png"
  alt: "年金シミュレーター"
---

老後の資産をどう準備するか、具体的な数字で確認できる無料ツールです。公的年金（国民年金・厚生年金）と自分の積立を合わせて、毎月の収支や資産の持続年数をグラフ付きでシミュレーションできます。

<div id="ps-app">
<style>
#ps-app {
font-family: system-ui, -apple-system, sans-serif;
color: #1e293b;
max-width: 780px;
margin: 0 auto;
padding: 0 4px;
box-sizing: border-box;
}
#ps-app *, #ps-app *::before, #ps-app *::after {
box-sizing: border-box;
}
#ps-app h2 {
font-size: 17px;
font-weight: 700;
color: #1e293b;
margin: 20px 0 12px;
padding-bottom: 6px;
border-bottom: 2px solid #cbd5e1;
}
#ps-app .ps-section {
background: #f8fafc;
border: 1px solid #cbd5e1;
border-radius: 10px;
padding: 18px 20px;
margin-bottom: 18px;
}
#ps-app .ps-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 14px;
}
#ps-app .ps-field {
display: flex;
flex-direction: column;
gap: 4px;
}
#ps-app .ps-field label {
font-size: 13px;
color: #475569;
font-weight: 600;
}
#ps-app .ps-field input[type="number"] {
padding: 8px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 15px;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
width: 100%;
}
#ps-app .ps-field input[type="number"]:focus {
outline: none;
border-color: #3b82f6;
}
#ps-app .ps-field .ps-hint {
font-size: 11px;
color: #94a3b8;
}
#ps-app .ps-pension-row {
display: flex;
align-items: center;
flex-wrap: wrap;
gap: 12px;
padding: 10px 0;
border-bottom: 1px solid #e2e8f0;
}
#ps-app .ps-pension-row:last-child {
border-bottom: none;
}
#ps-app .ps-pension-row label.ps-check-label {
display: flex;
align-items: center;
gap: 6px;
font-size: 14px;
font-weight: 700;
color: #1e293b;
min-width: 140px;
cursor: pointer;
}
#ps-app .ps-pension-row input[type="checkbox"] {
width: 17px;
height: 17px;
accent-color: #3b82f6;
cursor: pointer;
}
#ps-app .ps-pension-inputs {
display: flex;
flex-wrap: wrap;
gap: 10px;
flex: 1;
}
#ps-app .ps-pension-inputs .ps-field {
min-width: 130px;
max-width: 200px;
}
#ps-app .ps-pension-est {
font-size: 12px;
color: #0369a1;
background: #e0f2fe;
border-radius: 6px;
padding: 4px 10px;
font-weight: 600;
white-space: nowrap;
align-self: center;
}
#ps-app .ps-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 16px;
}
#ps-app .ps-preset-btn {
padding: 7px 18px;
border: 1.5px solid #cbd5e1;
border-radius: 20px;
background: #fff;
color: #475569;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#ps-app .ps-preset-btn:hover {
background: #f1f5f9;
border-color: #94a3b8;
color: #1e293b;
}
#ps-app .ps-run-btn {
display: block;
width: 100%;
padding: 14px;
background: #1e40af;
color: #fff;
font-size: 16px;
font-weight: 700;
border: none;
border-radius: 9px;
cursor: pointer;
transition: background 0.15s;
margin-bottom: 24px;
}
#ps-app .ps-run-btn:hover {
background: #1d4ed8;
}
#ps-app .ps-results {
display: none;
}
#ps-app .ps-results.visible {
display: block;
}
#ps-app .ps-cards {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
gap: 12px;
margin-bottom: 20px;
}
#ps-app .ps-card {
background: #fff;
border: 1.5px solid #cbd5e1;
border-radius: 10px;
padding: 14px 16px;
text-align: center;
}
#ps-app .ps-card .ps-card-label {
font-size: 12px;
color: #64748b;
font-weight: 600;
margin-bottom: 6px;
}
#ps-app .ps-card .ps-card-value {
font-size: 22px;
font-weight: 800;
color: #1e293b;
line-height: 1.1;
}
#ps-app .ps-card .ps-card-unit {
font-size: 12px;
color: #94a3b8;
font-weight: 500;
}
#ps-app .ps-card.green { border-color: #86efac; background: #f0fdf4; }
#ps-app .ps-card.green .ps-card-value { color: #16a34a; }
#ps-app .ps-card.orange { border-color: #fdba74; background: #fff7ed; }
#ps-app .ps-card.orange .ps-card-value { color: #ea580c; }
#ps-app .ps-card.red { border-color: #fca5a5; background: #fef2f2; }
#ps-app .ps-card.red .ps-card-value { color: #dc2626; }
#ps-app .ps-status-bar {
padding: 12px 16px;
border-radius: 9px;
font-size: 14px;
font-weight: 700;
margin-bottom: 20px;
text-align: center;
}
#ps-app .ps-status-bar.green { background: #dcfce7; color: #15803d; }
#ps-app .ps-status-bar.orange { background: #ffedd5; color: #c2410c; }
#ps-app .ps-status-bar.red { background: #fee2e2; color: #b91c1c; }
#ps-app .ps-chart-wrap {
background: #fff;
border: 1px solid #cbd5e1;
border-radius: 10px;
padding: 16px;
margin-bottom: 20px;
overflow: hidden;
}
#ps-app .ps-chart-title {
font-size: 14px;
font-weight: 700;
color: #475569;
margin-bottom: 10px;
text-align: center;
}
#ps-app canvas#ps-chart {
width: 100%;
height: auto;
display: block;
}
#ps-app .ps-needed {
background: #f8fafc;
border: 1.5px solid #cbd5e1;
border-radius: 9px;
padding: 14px 18px;
font-size: 14px;
color: #1e293b;
margin-bottom: 20px;
}
#ps-app .ps-needed span {
font-weight: 800;
color: #1e40af;
font-size: 18px;
}
</style>

<div class="ps-section">
<h2>プリセットシナリオ</h2>
<div class="ps-presets">
<button class="ps-preset-btn" onclick="psApplyPreset('stable')">安定型</button>
<button class="ps-preset-btn" onclick="psApplyPreset('balance')">バランス型</button>
<button class="ps-preset-btn" onclick="psApplyPreset('active')">積極型</button>
</div>
</div>

<div class="ps-section">
<h2>基本情報</h2>
<div class="ps-grid">
<div class="ps-field">
<label for="ps-age">現在の年齢</label>
<input type="number" id="ps-age" value="30" min="18" max="70">
<span class="ps-hint">歳</span>
</div>
<div class="ps-field">
<label for="ps-retire-age">退職年齢</label>
<input type="number" id="ps-retire-age" value="65" min="50" max="75">
<span class="ps-hint">歳</span>
</div>
<div class="ps-field">
<label for="ps-savings">現在の貯蓄額</label>
<input type="number" id="ps-savings" value="500" min="0">
<span class="ps-hint">万円</span>
</div>
<div class="ps-field">
<label for="ps-monthly">毎月の積立額</label>
<input type="number" id="ps-monthly" value="3" min="0" step="0.5">
<span class="ps-hint">万円/月</span>
</div>
<div class="ps-field">
<label for="ps-return">予想年間利回り</label>
<input type="number" id="ps-return" value="5" min="0" max="20" step="0.1">
<span class="ps-hint">%</span>
</div>
<div class="ps-field">
<label for="ps-inflation">予想インフレ率</label>
<input type="number" id="ps-inflation" value="2" min="0" max="10" step="0.1">
<span class="ps-hint">%</span>
</div>
<div class="ps-field">
<label for="ps-living">希望する毎月の生活費</label>
<input type="number" id="ps-living" value="25" min="1" step="0.5">
<span class="ps-hint">万円/月</span>
</div>
<div class="ps-field">
<label for="ps-lifespan">想定寿命</label>
<input type="number" id="ps-lifespan" value="90" min="70" max="110">
<span class="ps-hint">歳</span>
</div>
</div>
</div>

<div class="ps-section">
<h2>公的年金</h2>
<div class="ps-pension-row">
<label class="ps-check-label">
<input type="checkbox" id="ps-kokumin" checked>
国民年金（基礎年金）
</label>
<div class="ps-pension-inputs">
<div class="ps-field">
<label for="ps-kokumin-months">加入月数</label>
<input type="number" id="ps-kokumin-months" value="480" min="0" max="480">
<span class="ps-hint">月（最大480）</span>
</div>
</div>
<div class="ps-pension-est" id="ps-kokumin-est">約 65,000 円/月</div>
</div>
<div class="ps-pension-row">
<label class="ps-check-label">
<input type="checkbox" id="ps-kousei" checked>
厚生年金
</label>
<div class="ps-pension-inputs">
<div class="ps-field">
<label for="ps-kousei-salary">平均月収</label>
<input type="number" id="ps-kousei-salary" value="35" min="0" step="1">
<span class="ps-hint">万円</span>
</div>
<div class="ps-field">
<label for="ps-kousei-months">加入月数</label>
<input type="number" id="ps-kousei-months" value="420" min="0">
<span class="ps-hint">月（35年=420）</span>
</div>
</div>
<div class="ps-pension-est" id="ps-kousei-est">約 67,000 円/月</div>
</div>
</div>

<button class="ps-run-btn" onclick="psRun()">シミュレーション開始</button>

<div class="ps-results" id="ps-results">
<div class="ps-status-bar" id="ps-status-bar"></div>
<div class="ps-cards" id="ps-cards"></div>
<div class="ps-chart-wrap">
<div class="ps-chart-title">資産推移（5年ごと）</div>
<canvas id="ps-chart"></canvas>
</div>
<div class="ps-needed" id="ps-needed"></div>
</div>

<script>
(function(){
function getVal(id){ return parseFloat(document.getElementById(id).value)||0; }
function getChecked(id){ return document.getElementById(id).checked; }

function calcKokumin(){
var months = Math.min(getVal('ps-kokumin-months'),480);
return (65000 * months / 480) / 10000;
}
function calcKousei(){
var sal = getVal('ps-kousei-salary') * 10000;
var months = getVal('ps-kousei-months');
return (sal * 5.481 / 1000 * months / 12) / 10000;
}

function updatePensionEst(){
var k = calcKokumin();
document.getElementById('ps-kokumin-est').textContent =
'約 ' + Math.round(k*10000).toLocaleString() + ' 円/月';
var s = calcKousei();
document.getElementById('ps-kousei-est').textContent =
'約 ' + Math.round(s*10000).toLocaleString() + ' 円/月';
}

['ps-kokumin-months','ps-kousei-salary','ps-kousei-months'].forEach(function(id){
document.getElementById(id).addEventListener('input', updatePensionEst);
});
updatePensionEst();

window.psApplyPreset = function(type){
var presets = {
stable:  { age:35, retire:65, savings:300, monthly:3,   ret:3,  inf:2,   living:20, life:90, kmMonths:480, ksalary:30, kMonths:360 },
balance: { age:30, retire:65, savings:500, monthly:3,   ret:5,  inf:2,   living:25, life:90, kmMonths:480, ksalary:35, kMonths:420 },
active:  { age:28, retire:60, savings:200, monthly:5,   ret:7,  inf:2.5, living:30, life:90, kmMonths:360, ksalary:50, kMonths:384 }
};
var p = presets[type];
document.getElementById('ps-age').value = p.age;
document.getElementById('ps-retire-age').value = p.retire;
document.getElementById('ps-savings').value = p.savings;
document.getElementById('ps-monthly').value = p.monthly;
document.getElementById('ps-return').value = p.ret;
document.getElementById('ps-inflation').value = p.inf;
document.getElementById('ps-living').value = p.living;
document.getElementById('ps-lifespan').value = p.life;
document.getElementById('ps-kokumin-months').value = p.kmMonths;
document.getElementById('ps-kousei-salary').value = p.ksalary;
document.getElementById('ps-kousei-months').value = p.kMonths;
updatePensionEst();
};

window.psRun = function(){
var age       = getVal('ps-age');
var retireAge = getVal('ps-retire-age');
var savings   = getVal('ps-savings');
var monthly   = getVal('ps-monthly');
var ret       = getVal('ps-return') / 100;
var inf       = getVal('ps-inflation') / 100;
var living    = getVal('ps-living');
var lifespan  = getVal('ps-lifespan');

var yearsToRetire = Math.max(retireAge - age, 0);
var yearsInRetire = Math.max(lifespan - retireAge, 0);

var monthlyRet = ret / 12;
var months = yearsToRetire * 12;
var nominal = savings;
for(var m=0; m<months; m++){
nominal = nominal * (1 + monthlyRet) + monthly;
}
var realRate = (1 + ret) / (1 + inf) - 1;
var realMonthly = monthly / Math.pow(1+inf, yearsToRetire/2);
var real = savings;
var realMonthlyR = realRate / 12;
for(var m2=0; m2<months; m2++){
real = real * (1 + realMonthlyR) + monthly / Math.pow(1+inf,(m2+1)/12);
}

var publicPension = 0;
if(getChecked('ps-kokumin')) publicPension += calcKokumin();
if(getChecked('ps-kousei'))  publicPension += calcKousei();

var deficit = living - publicPension;
var privatePension = 0;
var sustainYears = 0;
if(deficit > 0){
var annualDraw = deficit * 12;
var r = ret;
if(r > 0){
var n = yearsInRetire;
var pv = annualDraw * (1 - Math.pow(1+r, -n)) / r;
privatePension = nominal > 0 ? (deficit * Math.min(nominal / pv, 1)) : 0;
if(nominal >= pv){
sustainYears = yearsInRetire;
} else {
var asset = nominal;
for(var y=0; y<200; y++){
asset = asset * (1+r) - annualDraw;
if(asset <= 0){ sustainYears = y; break; }
sustainYears = y+1;
}
}
} else {
sustainYears = nominal / annualDraw;
}
} else {
privatePension = 0;
sustainYears = yearsInRetire;
}

var totalMonthly = publicPension + (deficit > 0 ? Math.min(deficit, privatePension) : 0);
var surplusMonthly = totalMonthly - living;

var neededMonthly = 0;
if(deficit > 0 && ret > 0){
var n2 = yearsInRetire;
var pv2 = deficit * 12 * (1 - Math.pow(1+ret,-n2)) / ret;
if(yearsToRetire > 0){
var fvFactor = (Math.pow(1+monthlyRet, months) - 1) / monthlyRet;
var neededFV = Math.max(pv2 - savings * Math.pow(1+ret, yearsToRetire), 0);
neededMonthly = neededFV / fvFactor;
}
}

var status = surplusMonthly >= 0 ? 'green' : (surplusMonthly >= -5 ? 'orange' : 'red');

var cardsEl = document.getElementById('ps-cards');
cardsEl.innerHTML = '';
var cards = [
{ label:'退職時の総資産（名目）', value: Math.round(nominal).toLocaleString(), unit:'万円', cls:'' },
{ label:'退職時の総資産（実質）', value: Math.round(real).toLocaleString(), unit:'万円（インフレ調整後）', cls:'' },
{ label:'公的年金の月額受給見込み', value: Math.round(publicPension*100)/100, unit:'万円/月', cls:'' },
{ label:'私的年金（貯蓄取り崩し）月額', value: Math.round(Math.min(deficit,privatePension)*10)/10, unit:'万円/月', cls:'' },
{ label:'合計月収（見込み）', value: Math.round(totalMonthly*10)/10, unit:'万円/月', cls:status },
{ label:'過不足額', value:(surplusMonthly>=0?'+':'')+Math.round(surplusMonthly*10)/10, unit:'万円/月', cls:status },
{ label:'貯蓄が持続する年数', value: Math.round(sustainYears*10)/10, unit:'年', cls:(sustainYears>=yearsInRetire?'green':(sustainYears>=yearsInRetire*0.7?'orange':'red')) }
];
cards.forEach(function(c){
var div = document.createElement('div');
div.className = 'ps-card' + (c.cls?' '+c.cls:'');
div.innerHTML = '<div class="ps-card-label">'+c.label+'</div><div class="ps-card-value">'+c.value+'</div><div class="ps-card-unit">'+c.unit+'</div>';
cardsEl.appendChild(div);
});

var sb = document.getElementById('ps-status-bar');
if(status==='green'){
sb.className='ps-status-bar green';
sb.textContent = '老後の資産計画は順調です。希望する生活費をまかなえる見込みがあります。';
} else if(status==='orange'){
sb.className='ps-status-bar orange';
sb.textContent = '老後の資産がやや不足する可能性があります。積立額や利回りの見直しをご検討ください。';
} else {
sb.className='ps-status-bar red';
sb.textContent = '老後の資産が大きく不足する見込みです。積立額の増額や支出の見直しが必要です。';
}

var neededEl = document.getElementById('ps-needed');
if(neededMonthly > monthly + 0.1){
neededEl.innerHTML = '目標達成に必要な毎月の積立額（目安）：<span>' + Math.ceil(neededMonthly*10)/10 + ' 万円/月</span>（現在の積立額 ' + monthly + ' 万円/月 に対して <b>+' + Math.round((neededMonthly-monthly)*10)/10 + ' 万円</b> 不足）';
} else {
neededEl.innerHTML = '現在の積立額（<span>' + monthly + ' 万円/月</span>）で、老後の生活費をまかなえる見込みです。';
}

drawChart(age, retireAge, lifespan, savings, monthly, monthlyRet, ret, inf);

document.getElementById('ps-results').classList.add('visible');
};

function drawChart(age, retireAge, lifespan, savings, monthly, monthlyRet, ret, inf){
var canvas = document.getElementById('ps-chart');
var dpr = window.devicePixelRatio || 1;
var w = canvas.parentElement.clientWidth - 32;
canvas.style.width = w + 'px';
canvas.style.height = Math.round(w * 0.45) + 'px';
canvas.width  = Math.round(w * dpr);
canvas.height = Math.round(w * 0.45 * dpr);
var ctx = canvas.getContext('2d');
ctx.scale(dpr, dpr);
var cw = w, ch = Math.round(w * 0.45);

var padL=52, padR=16, padT=20, padB=44;
var chartW = cw - padL - padR;
var chartH = ch - padT - padB;

var labels = [], assetData = [];
var months = (retireAge - age) * 12;
var nominal = savings;
var m2 = 0;
for(var a=age; a<=lifespan; a+=5){
labels.push(a+'歳');
if(a <= retireAge){
var targetMonths = (a - age) * 12;
while(m2 < targetMonths){
nominal = nominal * (1 + monthlyRet) + monthly;
m2++;
}
assetData.push(nominal);
} else {
var publicP = 0;
if(getChecked('ps-kokumin')) publicP += calcKokumin();
if(getChecked('ps-kousei'))  publicP += calcKousei();
var living2 = getVal('ps-living');
var draw = Math.max(living2 - publicP, 0) * 12;
var yrsPast = a - retireAge;
var asset = nominal;
for(var y2=0; y2<yrsPast; y2++){
asset = asset * (1 + ret) - draw;
if(asset < 0){ asset = 0; break; }
}
assetData.push(asset);
}
}

var maxVal = Math.max.apply(null, assetData) * 1.1;
if(maxVal <= 0) maxVal = 1;

ctx.clearRect(0, 0, cw, ch);
ctx.fillStyle = '#fff';
ctx.fillRect(0,0,cw,ch);

var gridLines = 5;
ctx.strokeStyle = '#e2e8f0';
ctx.lineWidth = 1;
ctx.textAlign = 'right';
ctx.font = '11px system-ui,sans-serif';
ctx.fillStyle = '#94a3b8';
for(var i=0; i<=gridLines; i++){
var y = padT + chartH - (i/gridLines)*chartH;
ctx.beginPath();
ctx.moveTo(padL, y);
ctx.lineTo(padL+chartW, y);
ctx.stroke();
ctx.fillText(Math.round(maxVal * i / gridLines) + '万', padL-4, y+4);
}

var n = labels.length;
var barW = Math.max((chartW / n) * 0.6, 8);
var gap  = chartW / n;

for(var i=0; i<n; i++){
var x = padL + gap*i + gap/2;
var age_i = age + i*5;
var h = (assetData[i] / maxVal) * chartH;
var barX = x - barW/2;
var barY = padT + chartH - h;

var grad = ctx.createLinearGradient(barX, barY, barX, barY+h);
if(age_i <= retireAge){
grad.addColorStop(0,'#60a5fa');
grad.addColorStop(1,'#1e40af');
} else if(assetData[i] > 0){
grad.addColorStop(0,'#4ade80');
grad.addColorStop(1,'#15803d');
} else {
grad.addColorStop(0,'#fca5a5');
grad.addColorStop(1,'#dc2626');
}
ctx.fillStyle = grad;
ctx.beginPath();
ctx.roundRect ? ctx.roundRect(barX, barY, barW, h, [4,4,0,0]) : ctx.rect(barX, barY, barW, h);
ctx.fill();

ctx.fillStyle = '#475569';
ctx.textAlign = 'center';
ctx.font = '10px system-ui,sans-serif';
ctx.fillText(labels[i], x, ch - padB + 16);

if(assetData[i] > 0){
ctx.fillStyle = '#1e293b';
ctx.font = 'bold 10px system-ui,sans-serif';
ctx.fillText(Math.round(assetData[i])+'万', x, barY - 4);
}
}

var retireX = padL + ((retireAge - age)/5) * gap + gap/2;
ctx.save();
ctx.setLineDash([4,3]);
ctx.strokeStyle = '#f59e0b';
ctx.lineWidth = 1.5;
ctx.beginPath();
ctx.moveTo(retireX, padT);
ctx.lineTo(retireX, padT+chartH);
ctx.stroke();
ctx.restore();
ctx.fillStyle = '#f59e0b';
ctx.font = '10px system-ui,sans-serif';
ctx.textAlign = 'center';
ctx.fillText('退職', retireX, padT-4);
}
})();
</script>
</div>

<div class="ps-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

> 手取り額を計算 → [手取り計算ツール](/ja/tools/salary-tedori-calculator/)
> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-planner/)
> 複利を計算 → [複利計算ツール](/ja/tools/compound-interest-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
