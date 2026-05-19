---
title: "BMI計算ツール｜身長と体重から肥満度を自動判定【無料】"
date: 2025-09-15
draft: false
slug: "bmi-calculator"
aliases: ["/ja/tools/bmi-calculator/"]
description: "身長と体重を入力するだけでBMI（体格指数）を自動計算。日本肥満学会の基準で判定し、適正体重・美容体重も表示。無料で使えるBMI計算ツール。"
author: "Productivity Works編集部"
categories: ["無料ツール"]
tags: ["BMI", "体重管理", "健康", "ダイエット", "計算ツール"]
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/bmi-calculator.png"
  alt: "BMI計算ツール｜身長と体重から肥満度を自動判定"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# BMI計算ツール｜身長と体重から肥満度を自動判定

BMI（Body Mass Index：体格指数）は、身長と体重から算出される体格の目安です。日本肥満学会の基準に基づき、低体重・普通体重・肥満度を自動で判定します。適正体重・美容体重・モデル体重も同時に表示しますので、目標体重の参考にお役立てください。

<div id="bmi-tool-wrapper" style="font-family:'Helvetica Neue',Arial,'Hiragino Kaku Gothic ProN','Hiragino Sans',Meiryo,sans-serif;max-width:680px;margin:2rem auto;">

<style>
#bmi-tool-wrapper *{box-sizing:border-box;}
#bmi-tool-wrapper .bmi-card{background:#fff;border:1px solid #e5e7eb;border-radius:16px;padding:28px 28px 24px;box-shadow:0 2px 12px rgba(0,0,0,.07);}
#bmi-tool-wrapper .bmi-section-title{font-size:.8rem;font-weight:700;letter-spacing:.08em;color:#6b7280;text-transform:uppercase;margin:0 0 14px;}
#bmi-tool-wrapper .bmi-field{margin-bottom:20px;}
#bmi-tool-wrapper .bmi-label{display:flex;justify-content:space-between;align-items:center;font-size:.9rem;font-weight:600;color:#374151;margin-bottom:8px;}
#bmi-tool-wrapper .bmi-label span.bmi-val{font-size:1.05rem;color:#10b981;font-weight:700;}
#bmi-tool-wrapper input[type=range]{-webkit-appearance:none;appearance:none;width:100%;height:6px;border-radius:3px;background:#d1fae5;outline:none;cursor:pointer;}
#bmi-tool-wrapper input[type=range]::-webkit-slider-thumb{-webkit-appearance:none;appearance:none;width:20px;height:20px;border-radius:50%;background:#10b981;cursor:pointer;border:2px solid #fff;box-shadow:0 1px 4px rgba(0,0,0,.2);}
#bmi-tool-wrapper input[type=range]::-moz-range-thumb{width:20px;height:20px;border-radius:50%;background:#10b981;cursor:pointer;border:2px solid #fff;box-shadow:0 1px 4px rgba(0,0,0,.2);}
#bmi-tool-wrapper .bmi-number-input{display:flex;align-items:center;gap:8px;margin-top:6px;}
#bmi-tool-wrapper .bmi-number-input input[type=number]{width:90px;padding:6px 10px;border:1.5px solid #d1d5db;border-radius:8px;font-size:1rem;text-align:center;color:#111827;transition:border-color .2s;}
#bmi-tool-wrapper .bmi-number-input input[type=number]:focus{outline:none;border-color:#10b981;}
#bmi-tool-wrapper .bmi-number-input .bmi-unit{font-size:.9rem;color:#6b7280;}
#bmi-tool-wrapper .bmi-radio-group{display:flex;gap:12px;margin-top:4px;}
#bmi-tool-wrapper .bmi-radio-btn{position:relative;flex:1;}
#bmi-tool-wrapper .bmi-radio-btn input[type=radio]{position:absolute;opacity:0;width:0;height:0;}
#bmi-tool-wrapper .bmi-radio-btn label{display:block;text-align:center;padding:9px 0;border:1.5px solid #d1d5db;border-radius:8px;font-size:.9rem;font-weight:600;color:#6b7280;cursor:pointer;transition:all .2s;}
#bmi-tool-wrapper .bmi-radio-btn input[type=radio]:checked + label{border-color:#10b981;background:#f0fdf4;color:#10b981;}
#bmi-tool-wrapper .bmi-result-box{border-radius:14px;padding:24px 22px;text-align:center;margin-bottom:20px;transition:background .3s;}
#bmi-tool-wrapper .bmi-result-label{font-size:.85rem;font-weight:700;letter-spacing:.08em;color:rgba(255,255,255,.85);margin-bottom:4px;}
#bmi-tool-wrapper .bmi-result-value{font-size:4rem;font-weight:800;color:#fff;line-height:1;margin-bottom:4px;}
#bmi-tool-wrapper .bmi-result-category{font-size:1.3rem;font-weight:700;color:#fff;}
#bmi-tool-wrapper .bmi-scale-wrap{margin-bottom:20px;}
#bmi-tool-wrapper .bmi-scale-bar{position:relative;height:14px;border-radius:7px;background:linear-gradient(to right,#3b82f6 0%,#3b82f6 15.5%,#10b981 15.5%,#10b981 52.5%,#f59e0b 52.5%,#f59e0b 68.5%,#f97316 68.5%,#f97316 79%,#ef4444 79%,#ef4444 91%,#dc2626 91%,#dc2626 100%);margin:8px 0 4px;}
#bmi-tool-wrapper .bmi-scale-pointer{position:absolute;top:-5px;width:4px;height:24px;background:#1f2937;border-radius:2px;transform:translateX(-50%);transition:left .4s cubic-bezier(.34,1.56,.64,1);}
#bmi-tool-wrapper .bmi-scale-pointer::after{content:'';position:absolute;bottom:-6px;left:50%;transform:translateX(-50%);width:10px;height:10px;background:#1f2937;border-radius:50%;}
#bmi-tool-wrapper .bmi-scale-labels{display:flex;justify-content:space-between;font-size:.68rem;color:#9ca3af;margin-top:2px;}
#bmi-tool-wrapper .bmi-weight-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:20px;}
#bmi-tool-wrapper .bmi-weight-card{background:#f9fafb;border:1px solid #e5e7eb;border-radius:10px;padding:12px 14px;}
#bmi-tool-wrapper .bmi-weight-card .wc-title{font-size:.75rem;font-weight:700;color:#6b7280;margin-bottom:2px;}
#bmi-tool-wrapper .bmi-weight-card .wc-value{font-size:1.25rem;font-weight:800;color:#111827;}
#bmi-tool-wrapper .bmi-weight-card .wc-diff{font-size:.8rem;font-weight:600;margin-top:1px;}
#bmi-tool-wrapper .diff-plus{color:#ef4444;}
#bmi-tool-wrapper .diff-minus{color:#10b981;}
#bmi-tool-wrapper .diff-zero{color:#6b7280;}
#bmi-tool-wrapper .bmi-table{width:100%;border-collapse:collapse;font-size:.88rem;}
#bmi-tool-wrapper .bmi-table th,#bmi-tool-wrapper .bmi-table td{padding:8px 12px;border:1px solid #e5e7eb;text-align:left;}
#bmi-tool-wrapper .bmi-table th{background:#f3faf7;font-weight:700;color:#374151;}
#bmi-tool-wrapper .bmi-table tr.highlight-row td{font-weight:700;}
#bmi-tool-wrapper .bmi-dot{display:inline-block;width:10px;height:10px;border-radius:50%;margin-right:6px;}
@media(max-width:480px){
#bmi-tool-wrapper .bmi-card{padding:18px 14px;}
#bmi-tool-wrapper .bmi-result-value{font-size:3rem;}
#bmi-tool-wrapper .bmi-weight-grid{grid-template-columns:1fr 1fr;}
}
</style>

<!-- INPUTS -->
<div class="bmi-card" style="margin-bottom:16px;">
<div class="bmi-section-title">入力</div>

<!-- 身長 -->
<div class="bmi-field">
<div class="bmi-label">身長 <span class="bmi-val" id="lbl-height">170 cm</span></div>
<input type="range" id="sl-height" min="140" max="200" step="1" value="170" oninput="syncHeight(this.value,'range')">
<div class="bmi-number-input">
<input type="number" id="in-height" min="140" max="200" value="170" oninput="syncHeight(this.value,'num')">
<span class="bmi-unit">cm</span>
</div>
</div>

<!-- 体重 -->
<div class="bmi-field">
<div class="bmi-label">体重 <span class="bmi-val" id="lbl-weight">65 kg</span></div>
<input type="range" id="sl-weight" min="30" max="150" step="0.5" value="65" oninput="syncWeight(this.value,'range')">
<div class="bmi-number-input">
<input type="number" id="in-weight" min="30" max="150" step="0.1" value="65" oninput="syncWeight(this.value,'num')">
<span class="bmi-unit">kg</span>
</div>
</div>

<!-- 性別 -->
<div class="bmi-field" style="margin-bottom:12px;">
<div class="bmi-label">性別</div>
<div class="bmi-radio-group">
<div class="bmi-radio-btn">
<input type="radio" id="sex-male" name="bmi-sex" value="male" checked onchange="calcBMI()">
<label for="sex-male">男性</label>
</div>
<div class="bmi-radio-btn">
<input type="radio" id="sex-female" name="bmi-sex" value="female" onchange="calcBMI()">
<label for="sex-female">女性</label>
</div>
</div>
</div>

<!-- 年齢 -->
<div class="bmi-field" style="margin-bottom:0;">
<div class="bmi-label">年齢 <span style="font-size:.78rem;color:#9ca3af;font-weight:400;">（任意）</span></div>
<div class="bmi-number-input">
<input type="number" id="in-age" min="1" max="120" placeholder="例：30" style="width:90px;" oninput="calcBMI()">
<span class="bmi-unit">歳</span>
</div>
</div>
</div>

<!-- RESULTS -->
<div class="bmi-card">
<div class="bmi-section-title">判定結果</div>

<!-- BMI大表示 -->
<div class="bmi-result-box" id="result-box" style="background:#10b981;">
<div class="bmi-result-label">BMI</div>
<div class="bmi-result-value" id="result-value">22.5</div>
<div class="bmi-result-category" id="result-category">普通体重</div>
</div>

<!-- スケールバー -->
<div class="bmi-scale-wrap">
<div style="font-size:.78rem;color:#6b7280;margin-bottom:2px;">BMIスケール</div>
<div class="bmi-scale-bar">
<div class="bmi-scale-pointer" id="scale-pointer" style="left:40%;"></div>
</div>
<div class="bmi-scale-labels">
<span>15</span><span>18.5</span><span>25</span><span>30</span><span>35</span><span>40</span><span>50</span>
</div>
</div>

<!-- 体重目安パネル -->
<div style="font-size:.78rem;font-weight:700;color:#6b7280;letter-spacing:.06em;margin-bottom:10px;">体重の目安</div>
<div class="bmi-weight-grid">
<div class="bmi-weight-card">
<div class="wc-title">適正体重（BMI 22）</div>
<div class="wc-value" id="w-standard">—</div>
<div class="wc-diff" id="d-standard">—</div>
</div>
<div class="bmi-weight-card">
<div class="wc-title">美容体重（BMI 20）</div>
<div class="wc-value" id="w-beauty">—</div>
<div class="wc-diff" id="d-beauty">—</div>
</div>
<div class="bmi-weight-card">
<div class="wc-title">モデル体重（BMI 18）</div>
<div class="wc-value" id="w-model">—</div>
<div class="wc-diff" id="d-model">—</div>
</div>
<div class="bmi-weight-card">
<div class="wc-title">現在の体重</div>
<div class="wc-value" id="w-current">65.0 kg</div>
<div class="wc-diff" id="d-current" style="color:#10b981;">入力値</div>
</div>
</div>

<!-- 判定基準表 -->
<div style="font-size:.78rem;font-weight:700;color:#6b7280;letter-spacing:.06em;margin-bottom:10px;">BMI判定基準（日本肥満学会）</div>
<table class="bmi-table" id="bmi-ref-table">
<thead>
<tr><th>判定</th><th>BMI範囲</th></tr>
</thead>
<tbody>
<tr data-cat="low">
<td><span class="bmi-dot" style="background:#3b82f6;"></span>低体重</td>
<td>18.5未満</td>
</tr>
<tr data-cat="normal">
<td><span class="bmi-dot" style="background:#10b981;"></span>普通体重</td>
<td>18.5〜24.9</td>
</tr>
<tr data-cat="ob1">
<td><span class="bmi-dot" style="background:#f59e0b;"></span>肥満（1度）</td>
<td>25.0〜29.9</td>
</tr>
<tr data-cat="ob2">
<td><span class="bmi-dot" style="background:#f97316;"></span>肥満（2度）</td>
<td>30.0〜34.9</td>
</tr>
<tr data-cat="ob3">
<td><span class="bmi-dot" style="background:#ef4444;"></span>肥満（3度）</td>
<td>35.0〜39.9</td>
</tr>
<tr data-cat="ob4">
<td><span class="bmi-dot" style="background:#dc2626;"></span>肥満（4度）</td>
<td>40.0以上</td>
</tr>
</tbody>
</table>
</div>

<script>
(function(){
var CAT_MAP = [
{key:'low',  label:'低体重',     color:'#3b82f6', min:0,    max:18.5},
{key:'normal',label:'普通体重',  color:'#10b981', min:18.5, max:25},
{key:'ob1',  label:'肥満（1度）',color:'#f59e0b', min:25,   max:30},
{key:'ob2',  label:'肥満（2度）',color:'#f97316', min:30,   max:35},
{key:'ob3',  label:'肥満（3度）',color:'#ef4444', min:35,   max:40},
{key:'ob4',  label:'肥満（4度）',color:'#dc2626', min:40,   max:9999}
];

/* スケールバーのポインター位置計算 (BMI 15〜50 の範囲を 0〜100% にマップ) */
function bmiToPercent(bmi){
var SCALE_MIN = 15, SCALE_MAX = 50;
var pct = (bmi - SCALE_MIN) / (SCALE_MAX - SCALE_MIN) * 100;
return Math.min(Math.max(pct, 1), 99);
}

function getCategory(bmi){
for(var i=0;i<CAT_MAP.length;i++){
if(bmi < CAT_MAP[i].max) return CAT_MAP[i];
}
return CAT_MAP[CAT_MAP.length-1];
}

function fmtDiff(diff){
if(Math.abs(diff) < 0.05) return '<span class="diff-zero">± 0.0 kg</span>';
if(diff > 0) return '<span class="diff-plus">+ '+diff.toFixed(1)+' kg（現在より多い）</span>';
return '<span class="diff-minus">'+ diff.toFixed(1)+' kg（あと '+Math.abs(diff).toFixed(1)+' kg）</span>';
}

function setWeightCard(valId, diffId, bmiTarget, heightM, currentKg){
var target = bmiTarget * heightM * heightM;
document.getElementById(valId).textContent = target.toFixed(1)+' kg';
var diff = target - currentKg;
document.getElementById(diffId).innerHTML = fmtDiff(diff);
}

window.calcBMI = function(){
var h = parseFloat(document.getElementById('sl-height').value);
var w = parseFloat(document.getElementById('sl-weight').value);
if(isNaN(h)||isNaN(w)||h<=0||w<=0) return;
var hM = h / 100;
var bmi = w / (hM * hM);
var cat = getCategory(bmi);

/* 大表示 */
document.getElementById('result-value').textContent = bmi.toFixed(1);
document.getElementById('result-category').textContent = cat.label;
document.getElementById('result-box').style.background = cat.color;

/* スケールポインター */
document.getElementById('scale-pointer').style.left = bmiToPercent(bmi)+'%';

/* 体重目安 */
setWeightCard('w-standard','d-standard',22,hM,w);
setWeightCard('w-beauty','d-beauty',20,hM,w);
setWeightCard('w-model','d-model',18,hM,w);
document.getElementById('w-current').textContent = w.toFixed(1)+' kg';

/* テーブルハイライト */
var rows = document.querySelectorAll('#bmi-ref-table tbody tr');
for(var i=0;i<rows.length;i++){
if(rows[i].getAttribute('data-cat')===cat.key){
rows[i].classList.add('highlight-row');
rows[i].style.background = cat.color+'18';
} else {
rows[i].classList.remove('highlight-row');
rows[i].style.background = '';
}
}
};

window.syncHeight = function(val, source){
var v = parseFloat(val);
if(isNaN(v)) return;
v = Math.min(Math.max(v, 140), 200);
document.getElementById('sl-height').value = v;
document.getElementById('in-height').value = v;
document.getElementById('lbl-height').textContent = v+' cm';
calcBMI();
};

window.syncWeight = function(val, source){
var v = parseFloat(val);
if(isNaN(v)) return;
v = Math.min(Math.max(v, 30), 150);
document.getElementById('sl-weight').value = v;
document.getElementById('in-weight').value = v;
document.getElementById('lbl-weight').textContent = v+' kg';
calcBMI();
};

/* 初期計算 */
calcBMI();
})();
</script>

</div>

---

> **注意:** BMIは体格の目安であり、筋肉量や体脂肪率は考慮されません。健康管理は医療専門家にご相談ください。

## 関連ツール

> 月々の支出バランスを見直す → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)

> パーセントを計算 → [パーセント計算ツール](/ja/tools/percent-calculator/)

> サブスクの年間コストを計算 → [サブスク管理計算ツール](/ja/tools/subscription-cost-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

