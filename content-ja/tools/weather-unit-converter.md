---
title: "気象単位変換ツール"
date: 2025-06-19
description: "気温（°C・°F・K）、風速（m/s・km/h・mph・ノット）、気圧（hPa・mmHg・inHg・atm・psi）、降水量（mm・インチ）、視程（km・マイル）をリアルタイムで相互変換。変換式も表示する無料オンラインツール。"
categories: ["無料ツール"]
slug: "weather-unit-converter"
ShowToc: false
aliases: ["/ja/tools/weather-unit-converter/", "/ja/tools/weather-unit-converter/"]
cover:
  image: "/images/covers/weather-unit-converter-ja.png"
  alt: "気象単位変換ツール"
---

気象観測で使われる単位をリアルタイムで変換。気温・風速・気圧・降水量・視程に対応し、各変換の計算式も表示します。

> 単位変換 → [単位変換ツール](/ja/tools/unit-converter/)

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div id="wu-app">
<style>
#wu-app *,#wu-app *::before,#wu-app *::after{box-sizing:border-box;margin:0;padding:0}
#wu-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;font-size:14px;color:#1e293b;max-width:860px;margin-top:20px}
#wu-app .wu-tabs{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:20px}
#wu-app .wu-tab{padding:8px 18px;border-radius:8px;border:1.5px solid #cbd5e1;background:#fff;color:#334155;font-size:13px;font-weight:600;cursor:pointer;transition:all .15s}
#wu-app .wu-tab:hover{border-color:#0ea5e9;color:#0ea5e9}
#wu-app .wu-tab.active{background:#0ea5e9;border-color:#0ea5e9;color:#fff}
#wu-app .wu-section{display:none;background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:20px}
#wu-app .wu-section.active{display:block}
#wu-app .wu-section-title{font-size:16px;font-weight:700;color:#0f172a;margin-bottom:16px;display:flex;align-items:center;gap:8px}
#wu-app .wu-section-icon{font-size:20px;line-height:1}
#wu-app .wu-temp-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
@media(max-width:560px){#wu-app .wu-temp-grid{grid-template-columns:1fr}}
#wu-app .wu-conv-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:12px}
#wu-app .wu-field{display:flex;flex-direction:column;gap:4px}
#wu-app .wu-field label{font-size:12px;font-weight:600;color:#64748b;letter-spacing:.03em}
#wu-app .wu-field input{padding:10px 12px;border:1.5px solid #e2e8f0;border-radius:8px;font-size:15px;font-weight:600;color:#1e293b !important;background:#fff !important;outline:none;transition:border-color .15s;width:100%}
#wu-app .wu-field input:focus{border-color:#0ea5e9}
#wu-app .wu-field input.source{border-color:#0ea5e9;background:#f0f9ff}
#wu-app .wu-formula{margin-top:14px;padding:10px 14px;background:#fff;border:1px solid #e2e8f0;border-radius:8px;font-size:12px;color:#64748b;line-height:1.7;font-family:"SFMono-Regular",Consolas,monospace}
#wu-app .wu-formula-title{font-size:11px;font-weight:700;color:#94a3b8;letter-spacing:.06em;text-transform:uppercase;margin-bottom:4px}
#wu-app .wu-formula-row{color:#475569}
#wu-app .wu-formula-row strong{color:#0369a1}
#wu-app .wu-reset-row{margin-top:14px;display:flex;gap:8px;align-items:center}
#wu-app .wu-btn{padding:7px 16px;border-radius:7px;border:1.5px solid #cbd5e1;background:#f1f5f9;color:#475569;font-size:13px;font-weight:500;cursor:pointer;transition:all .15s}
#wu-app .wu-btn:hover{border-color:#0ea5e9;color:#0ea5e9}
</style>

<!-- カテゴリタブ -->
<div class="wu-tabs">
<button class="wu-tab active" onclick="wuTab('temp')">気温</button>
<button class="wu-tab" onclick="wuTab('wind')">風速</button>
<button class="wu-tab" onclick="wuTab('pres')">気圧</button>
<button class="wu-tab" onclick="wuTab('precip')">降水量</button>
<button class="wu-tab" onclick="wuTab('vis')">視程</button>
</div>

<!-- 気温 -->
<div class="wu-section active" id="wu-sec-temp">
<div class="wu-section-title"><span class="wu-section-icon">&#127777;</span> 気温</div>
<div class="wu-temp-grid">
<div class="wu-field">
<label>摂氏 (°C)</label>
<input type="number" id="wu-tc" placeholder="0" oninput="wuTempFrom('c')" onfocus="wuTempFocus('c')">
</div>
<div class="wu-field">
<label>華氏 (°F)</label>
<input type="number" id="wu-tf" placeholder="32" oninput="wuTempFrom('f')" onfocus="wuTempFocus('f')">
</div>
<div class="wu-field">
<label>ケルビン (K)</label>
<input type="number" id="wu-tk" placeholder="273.15" oninput="wuTempFrom('k')" onfocus="wuTempFocus('k')">
</div>
</div>
<div class="wu-formula" id="wu-temp-formula">
<div class="wu-formula-title">変換式</div>
<div class="wu-formula-row">°F = °C × 9/5 + 32</div>
<div class="wu-formula-row">K = °C + 273.15</div>
<div class="wu-formula-row">°C = (°F − 32) × 5/9</div>
<div class="wu-formula-row">°C = K − 273.15</div>
</div>
<div class="wu-reset-row"><button class="wu-btn" onclick="wuTempReset()">リセット</button></div>
</div>

<!-- 風速 -->
<div class="wu-section" id="wu-sec-wind">
<div class="wu-section-title"><span class="wu-section-icon">&#127744;</span> 風速</div>
<div class="wu-conv-grid">
<div class="wu-field"><label>m/s（メートル毎秒）</label><input type="number" id="wu-wms" placeholder="0" oninput="wuWindFrom('ms')" onfocus="wuWindFocus('ms')"></div>
<div class="wu-field"><label>km/h（キロメートル毎時）</label><input type="number" id="wu-wkh" placeholder="0" oninput="wuWindFrom('kh')" onfocus="wuWindFocus('kh')"></div>
<div class="wu-field"><label>mph（マイル毎時）</label><input type="number" id="wu-wmp" placeholder="0" oninput="wuWindFrom('mp')" onfocus="wuWindFocus('mp')"></div>
<div class="wu-field"><label>ノット (kn)</label><input type="number" id="wu-wkn" placeholder="0" oninput="wuWindFrom('kn')" onfocus="wuWindFocus('kn')"></div>
</div>
<div class="wu-formula">
<div class="wu-formula-title">変換式（基準: m/s）</div>
<div class="wu-formula-row">km/h = m/s × 3.6</div>
<div class="wu-formula-row">mph = m/s × 2.23694</div>
<div class="wu-formula-row">ノット = m/s × 1.94384</div>
</div>
<div class="wu-reset-row"><button class="wu-btn" onclick="wuWindReset()">リセット</button></div>
</div>

<!-- 気圧 -->
<div class="wu-section" id="wu-sec-pres">
<div class="wu-section-title"><span class="wu-section-icon">&#9729;</span> 気圧</div>
<div class="wu-conv-grid">
<div class="wu-field"><label>hPa（ヘクトパスカル）</label><input type="number" id="wu-phpa" placeholder="1013.25" oninput="wuPresFrom('hpa')" onfocus="wuPresFocus('hpa')"></div>
<div class="wu-field"><label>mmHg（水銀柱ミリメートル）</label><input type="number" id="wu-pmmhg" placeholder="760" oninput="wuPresFrom('mmhg')" onfocus="wuPresFocus('mmhg')"></div>
<div class="wu-field"><label>inHg（水銀柱インチ）</label><input type="number" id="wu-pinhg" placeholder="29.92" oninput="wuPresFrom('inhg')" onfocus="wuPresFocus('inhg')"></div>
<div class="wu-field"><label>atm（標準大気圧）</label><input type="number" id="wu-patm" placeholder="1" oninput="wuPresFrom('atm')" onfocus="wuPresFocus('atm')"></div>
<div class="wu-field"><label>psi（重量ポンド毎平方インチ）</label><input type="number" id="wu-ppsi" placeholder="14.696" oninput="wuPresFrom('psi')" onfocus="wuPresFocus('psi')"></div>
</div>
<div class="wu-formula">
<div class="wu-formula-title">変換式（基準: hPa）</div>
<div class="wu-formula-row">mmHg = hPa × 0.750062</div>
<div class="wu-formula-row">inHg = hPa × 0.02953</div>
<div class="wu-formula-row">atm = hPa ÷ 1013.25</div>
<div class="wu-formula-row">psi = hPa × 0.0145038</div>
</div>
<div class="wu-reset-row"><button class="wu-btn" onclick="wuPresReset()">リセット</button></div>
</div>

<!-- 降水量 -->
<div class="wu-section" id="wu-sec-precip">
<div class="wu-section-title"><span class="wu-section-icon">&#127783;</span> 降水量</div>
<div class="wu-conv-grid">
<div class="wu-field"><label>ミリメートル (mm)</label><input type="number" id="wu-pmm" placeholder="0" oninput="wuPrecipFrom('mm')" onfocus="wuPrecipFocus('mm')"></div>
<div class="wu-field"><label>インチ (in)</label><input type="number" id="wu-pin" placeholder="0" oninput="wuPrecipFrom('in')" onfocus="wuPrecipFocus('in')"></div>
</div>
<div class="wu-formula">
<div class="wu-formula-title">変換式</div>
<div class="wu-formula-row">インチ = mm ÷ 25.4</div>
<div class="wu-formula-row">mm = インチ × 25.4</div>
</div>
<div class="wu-reset-row"><button class="wu-btn" onclick="wuPrecipReset()">リセット</button></div>
</div>

<!-- 視程 -->
<div class="wu-section" id="wu-sec-vis">
<div class="wu-section-title"><span class="wu-section-icon">&#128065;</span> 視程</div>
<div class="wu-conv-grid">
<div class="wu-field"><label>キロメートル (km)</label><input type="number" id="wu-vkm" placeholder="0" oninput="wuVisFrom('km')" onfocus="wuVisFocus('km')"></div>
<div class="wu-field"><label>マイル (mi)</label><input type="number" id="wu-vmi" placeholder="0" oninput="wuVisFrom('mi')" onfocus="wuVisFocus('mi')"></div>
</div>
<div class="wu-formula">
<div class="wu-formula-title">変換式</div>
<div class="wu-formula-row">マイル = km ÷ 1.60934</div>
<div class="wu-formula-row">km = マイル × 1.60934</div>
</div>
<div class="wu-reset-row"><button class="wu-btn" onclick="wuVisReset()">リセット</button></div>
</div>

<script>
(function(){
var currentTab = 'temp';

function tab(id){
currentTab = id;
document.querySelectorAll('#wu-app .wu-tab').forEach(function(b,i){
var ids=['temp','wind','pres','precip','vis'];
b.classList.toggle('active', ids[i]===id);
});
document.querySelectorAll('#wu-app .wu-section').forEach(function(s){
s.classList.remove('active');
});
document.getElementById('wu-sec-'+id).classList.add('active');
}

function r(v, dp){ return Math.round(v * Math.pow(10,dp)) / Math.pow(10,dp); }
function setVal(id, v){ var el=document.getElementById(id); if(el) el.value = isNaN(v)||!isFinite(v)?'':r(v,6); }

/* 気温 */
function tempFrom(src){
var vc = parseFloat(document.getElementById('wu-tc').value);
var vf = parseFloat(document.getElementById('wu-tf').value);
var vk = parseFloat(document.getElementById('wu-tk').value);
var c;
if(src==='c'){ c = vc; }
else if(src==='f'){ c = (vf-32)*5/9; }
else { c = vk-273.15; }
if(isNaN(c)) return;
if(src!=='c') setVal('wu-tc', c);
if(src!=='f') setVal('wu-tf', c*9/5+32);
if(src!=='k') setVal('wu-tk', c+273.15);
updateTempFormula(src, c);
}
function tempFocus(src){
['wu-tc','wu-tf','wu-tk'].forEach(function(id){ document.getElementById(id).classList.remove('source'); });
var map={c:'wu-tc',f:'wu-tf',k:'wu-tk'};
document.getElementById(map[src]).classList.add('source');
}
function updateTempFormula(src, c){
var el = document.getElementById('wu-temp-formula');
var f = r(c*9/5+32,4), k = r(c+273.15,4), cv = r(c,4);
var lines = [];
if(src==='c'){
lines.push('°F = '+cv+' × 9/5 + 32 = <strong>'+f+' °F</strong>');
lines.push('K = '+cv+' + 273.15 = <strong>'+k+' K</strong>');
} else if(src==='f'){
var fv=r(parseFloat(document.getElementById('wu-tf').value),4);
lines.push('°C = ('+fv+' − 32) × 5/9 = <strong>'+cv+' °C</strong>');
lines.push('K = '+cv+' + 273.15 = <strong>'+k+' K</strong>');
} else {
var kv=r(parseFloat(document.getElementById('wu-tk').value),4);
lines.push('°C = '+kv+' − 273.15 = <strong>'+cv+' °C</strong>');
lines.push('°F = '+cv+' × 9/5 + 32 = <strong>'+f+' °F</strong>');
}
el.innerHTML = '<div class="wu-formula-title">計算結果</div>' +
lines.map(function(l){ return '<div class="wu-formula-row">'+l+'</div>'; }).join('');
}
function tempReset(){
['wu-tc','wu-tf','wu-tk'].forEach(function(id){ document.getElementById(id).value=''; document.getElementById(id).classList.remove('source'); });
document.getElementById('wu-temp-formula').innerHTML='<div class="wu-formula-title">変換式</div><div class="wu-formula-row">°F = °C × 9/5 + 32</div><div class="wu-formula-row">K = °C + 273.15</div><div class="wu-formula-row">°C = (°F − 32) × 5/9</div><div class="wu-formula-row">°C = K − 273.15</div>';
}

/* 風速 */
var windFactors = {ms:1, kh:3.6, mp:2.23694, kn:1.94384};
var windIds = {ms:'wu-wms', kh:'wu-wkh', mp:'wu-wmp', kn:'wu-wkn'};
function windFrom(src){
var v = parseFloat(document.getElementById(windIds[src]).value);
if(isNaN(v)) return;
var ms = v / windFactors[src];
Object.keys(windIds).forEach(function(k){ if(k!==src) setVal(windIds[k], ms*windFactors[k]); });
}
function windFocus(src){ Object.keys(windIds).forEach(function(k){ document.getElementById(windIds[k]).classList.toggle('source',k===src); }); }
function windReset(){ Object.keys(windIds).forEach(function(k){ document.getElementById(windIds[k]).value=''; document.getElementById(windIds[k]).classList.remove('source'); }); }

/* 気圧 */
var presFactors = {hpa:1, mmhg:0.750062, inhg:0.02953, atm:1/1013.25, psi:0.0145038};
var presIds = {hpa:'wu-phpa', mmhg:'wu-pmmhg', inhg:'wu-pinhg', atm:'wu-patm', psi:'wu-ppsi'};
function presFrom(src){
var v = parseFloat(document.getElementById(presIds[src]).value);
if(isNaN(v)) return;
var hpa = v / presFactors[src];
Object.keys(presIds).forEach(function(k){ if(k!==src) setVal(presIds[k], hpa*presFactors[k]); });
}
function presFocus(src){ Object.keys(presIds).forEach(function(k){ document.getElementById(presIds[k]).classList.toggle('source',k===src); }); }
function presReset(){ Object.keys(presIds).forEach(function(k){ document.getElementById(presIds[k]).value=''; document.getElementById(presIds[k]).classList.remove('source'); }); }

/* 降水量 */
function precipFrom(src){
var v = parseFloat(document.getElementById(src==='mm'?'wu-pmm':'wu-pin').value);
if(isNaN(v)) return;
if(src==='mm') setVal('wu-pin', v/25.4);
else setVal('wu-pmm', v*25.4);
}
function precipFocus(src){
['wu-pmm','wu-pin'].forEach(function(id){ document.getElementById(id).classList.remove('source'); });
document.getElementById(src==='mm'?'wu-pmm':'wu-pin').classList.add('source');
}
function precipReset(){ ['wu-pmm','wu-pin'].forEach(function(id){ document.getElementById(id).value=''; document.getElementById(id).classList.remove('source'); }); }

/* 視程 */
function visFrom(src){
var v = parseFloat(document.getElementById(src==='km'?'wu-vkm':'wu-vmi').value);
if(isNaN(v)) return;
if(src==='km') setVal('wu-vmi', v/1.60934);
else setVal('wu-vkm', v*1.60934);
}
function visFocus(src){
['wu-vkm','wu-vmi'].forEach(function(id){ document.getElementById(id).classList.remove('source'); });
document.getElementById(src==='km'?'wu-vkm':'wu-vmi').classList.add('source');
}
function visReset(){ ['wu-vkm','wu-vmi'].forEach(function(id){ document.getElementById(id).value=''; document.getElementById(id).classList.remove('source'); }); }

window.wuTab = tab;
window.wuTempFrom = tempFrom; window.wuTempFocus = tempFocus; window.wuTempReset = tempReset;
window.wuWindFrom = windFrom; window.wuWindFocus = windFocus; window.wuWindReset = windReset;
window.wuPresFrom = presFrom; window.wuPresFocus = presFocus; window.wuPresReset = presReset;
window.wuPrecipFrom = precipFrom; window.wuPrecipFocus = precipFocus; window.wuPrecipReset = precipReset;
window.wuVisFrom = visFrom; window.wuVisFocus = visFocus; window.wuVisReset = visReset;
})();
</script>
</div>

---

**対応単位一覧：**

| カテゴリ | 対応単位 |
|---|---|
| 気温 | °C（摂氏）、°F（華氏）、K（ケルビン）— 3方向すべて対応 |
| 風速 | m/s、km/h、mph、ノット |
| 気圧 | hPa/mbar、mmHg/Torr、inHg、atm、psi |
| 降水量 | mm（ミリメートル）、インチ |
| 視程 | km（キロメートル）、マイル |

気圧の基準単位はhPa（ヘクトパスカル）を使用。世界の多くの気象機関で標準的に使用されています。

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
