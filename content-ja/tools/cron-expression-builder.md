---
title: "Cron式ビルダー"
date: 2026-01-29
description: "無料のCron式ビルダー。ビジュアルインターフェースでcronスケジュールを作成・検証。次回実行時刻と日本語説明を表示、会員登録不要。"
categories: ["無料ツール"]
slug: "cron-expression-builder"
ShowToc: false
cover:
  image: "/images/covers/cron-expression-builder-ja.png"
  alt: "Cron式ビルダー"
---

<div id="cr-app">
<style>
#cr-app *,#cr-app *::before,#cr-app *::after{box-sizing:border-box;margin:0;padding:0}
#cr-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;max-width:820px;margin:0 auto;padding:12px 4px}
#cr-app h2{font-size:1.1rem;font-weight:700;color:#334155;margin-bottom:12px}
#cr-app .cr-card{background:#fff;border:1px solid #e2e8f0;border-radius:12px;padding:18px;margin-bottom:14px;box-shadow:0 1px 4px rgba(0,0,0,.06)}
/* Presets */
#cr-app .cr-presets{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:4px}
#cr-app .cr-preset-btn{padding:6px 13px;border:1.5px solid #94a3b8;border-radius:20px;background:#f8fafc;color:#334155;font-size:12.5px;font-weight:600;cursor:pointer;transition:all .15s}
#cr-app .cr-preset-btn:hover{border-color:#475569;background:#e2e8f0}
/* Cron expression */
#cr-app .cr-expr-row{display:flex;align-items:center;gap:10px;flex-wrap:wrap}
#cr-app .cr-expr-input{flex:1;min-width:200px;font-family:'JetBrains Mono',Consolas,monospace;font-size:1.25rem;font-weight:700;color:#0f172a;background:#f1f5f9;border:2px solid #cbd5e1;border-radius:8px;padding:10px 14px;letter-spacing:.08em;outline:none;transition:border-color .15s}
#cr-app .cr-expr-input:focus{border-color:#3b82f6;background:#fff}
#cr-app .cr-expr-input.cr-invalid{border-color:#ef4444;background:#fef2f2}
#cr-app .cr-copy-btn{padding:10px 18px;background:#475569;color:#fff;border:none;border-radius:8px;font-size:13px;font-weight:700;cursor:pointer;white-space:nowrap;transition:background .15s}
#cr-app .cr-copy-btn:hover{background:#334155}
#cr-app .cr-copy-btn.copied{background:#16a34a}
/* Validation badge */
#cr-app .cr-badge{display:inline-flex;align-items:center;gap:5px;padding:4px 10px;border-radius:20px;font-size:12px;font-weight:700;margin-top:8px}
#cr-app .cr-badge-ok{background:#dcfce7;color:#166534}
#cr-app .cr-badge-err{background:#fee2e2;color:#991b1b}
/* Description */
#cr-app .cr-desc{background:#f0f9ff;border:1px solid #bae6fd;border-radius:8px;padding:12px 16px;font-size:14px;font-weight:600;color:#0369a1;margin-top:10px;min-height:36px}
/* Field builder */
#cr-app .cr-fields{display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:10px}
#cr-app .cr-field{background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;padding:12px}
#cr-app .cr-field-label{font-size:11px;font-weight:700;text-transform:uppercase;color:#64748b;letter-spacing:.06em;margin-bottom:8px;display:flex;align-items:center;gap:6px}
#cr-app .cr-field-label span.cr-tag{background:#e2e8f0;color:#475569;border-radius:4px;padding:1px 6px;font-size:10px;font-weight:700}
#cr-app .cr-field select,#cr-app .cr-field input{width:100%;padding:6px 8px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;color:#1e293b;background:#fff;outline:none;margin-top:4px}
#cr-app .cr-field select:focus,#cr-app .cr-field input:focus{border-color:#3b82f6}
#cr-app .cr-field .cr-range-row{display:flex;align-items:center;gap:4px;margin-top:4px}
#cr-app .cr-field .cr-range-row input{flex:1;min-width:0}
#cr-app .cr-field .cr-range-row span{font-size:12px;color:#64748b;flex-shrink:0}
/* Next executions */
#cr-app .cr-next-list{list-style:none;counter-reset:cr-ctr}
#cr-app .cr-next-list li{counter-increment:cr-ctr;display:flex;align-items:baseline;gap:8px;padding:6px 10px;border-bottom:1px solid #f1f5f9;font-size:13px}
#cr-app .cr-next-list li:last-child{border-bottom:none}
#cr-app .cr-next-list li::before{content:counter(cr-ctr);display:inline-flex;align-items:center;justify-content:center;width:20px;height:20px;border-radius:50%;background:#e2e8f0;color:#475569;font-size:11px;font-weight:700;flex-shrink:0}
#cr-app .cr-next-list li .cr-dt{font-family:monospace;color:#0f172a;font-weight:600;font-size:13px}
#cr-app .cr-next-list li .cr-rel{color:#94a3b8;font-size:12px}
#cr-app .cr-err-msg{color:#b91c1c;font-size:13px;padding:8px 0}
@media(max-width:540px){
#cr-app .cr-expr-input{font-size:1rem}
#cr-app .cr-fields{grid-template-columns:1fr 1fr}
}
</style>

<!-- Presets -->
<div class="cr-card">
<h2>プリセット</h2>
<div class="cr-presets">
<button class="cr-preset-btn" data-cron="* * * * *">毎分</button>
<button class="cr-preset-btn" data-cron="0 * * * *">毎時0分</button>
<button class="cr-preset-btn" data-cron="0 0 * * *">毎日0時</button>
<button class="cr-preset-btn" data-cron="0 9 * * 1">毎週月曜9時</button>
<button class="cr-preset-btn" data-cron="0 0 1 * *">毎月1日0時</button>
<button class="cr-preset-btn" data-cron="*/5 * * * *">5分ごと</button>
<button class="cr-preset-btn" data-cron="0 8-18 * * 1-5">平日8〜18時毎時</button>
<button class="cr-preset-btn" data-cron="30 23 * * *">毎日23:30</button>
</div>
</div>

<!-- Expression -->
<div class="cr-card">
<h2>Cron式</h2>
<div class="cr-expr-row">
<input id="cr-expr" class="cr-expr-input" type="text" value="* * * * *" spellcheck="false" autocomplete="off" />
<button id="cr-copy" class="cr-copy-btn">コピー</button>
</div>
<div id="cr-badge-wrap"></div>
<div id="cr-desc" class="cr-desc" style="margin-top:10px"></div>
</div>

<!-- Visual Builder -->
<div class="cr-card">
<h2>ビジュアルビルダー</h2>
<div class="cr-fields" id="cr-fields"></div>
</div>

<!-- Next Executions -->
<div class="cr-card">
<h2>次の10回の実行時刻</h2>
<div id="cr-next"></div>
</div>

<script>
(function(){
'use strict';

/* ── field metadata ── */
const FIELDS=[
{id:'min', label:'分', tag:'0–59', min:0, max:59},
{id:'hour',label:'時', tag:'0–23', min:0, max:23},
{id:'dom', label:'日',  tag:'1–31', min:1, max:31},
{id:'mon', label:'月', tag:'1–12', min:1, max:12},
{id:'dow', label:'曜日',tag:'0–6', min:0, max:6},
];
const MONTHS_JP=['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
const DOWS_JP=['日','月','火','水','木','金','土'];

/* ── state ── */
let updating=false;

/* ── DOM refs ── */
const exprEl=document.getElementById('cr-expr');
const badgeWrap=document.getElementById('cr-badge-wrap');
const descEl=document.getElementById('cr-desc');
const nextEl=document.getElementById('cr-next');
const copyBtn=document.getElementById('cr-copy');
const fieldsContainer=document.getElementById('cr-fields');

/* ── build visual fields ── */
function buildFields(){
fieldsContainer.innerHTML='';
FIELDS.forEach(f=>{
const div=document.createElement('div');
div.className='cr-field';
div.innerHTML=`
<div class="cr-field-label">${f.label} <span class="cr-tag">${f.tag}</span></div>
<select id="cr-sel-${f.id}" data-field="${f.id}">
<option value="every">毎回 (*)</option>
<option value="specific">指定</option>
<option value="range">範囲</option>
<option value="step">間隔</option>
</select>
<div id="cr-ctrl-${f.id}" style="margin-top:6px"></div>
`;
fieldsContainer.appendChild(div);
const sel=div.querySelector('select');
sel.addEventListener('change',()=>onModeChange(f));
renderControl(f,'every');
});
}

function renderControl(f,mode,vals){
const ctrl=document.getElementById(`cr-ctrl-${f.id}`);
ctrl.innerHTML='';
if(mode==='every') return;
if(mode==='specific'){
const inp=document.createElement('input');
inp.type='number';inp.min=f.min;inp.max=f.max;
inp.placeholder=`${f.min}〜${f.max}`;
inp.value=vals&&vals.v!==undefined?vals.v:'';
inp.dataset.field=f.id;
inp.addEventListener('input',onControlChange);
ctrl.appendChild(inp);
} else if(mode==='range'){
const row=document.createElement('div');
row.className='cr-range-row';
['from','to'].forEach((k,i)=>{
const inp=document.createElement('input');
inp.type='number';inp.min=f.min;inp.max=f.max;
inp.placeholder=i===0?String(f.min):String(f.max);
inp.value=vals&&vals[k]!==undefined?vals[k]:'';
inp.dataset.field=f.id;inp.dataset.part=k;
inp.addEventListener('input',onControlChange);
row.appendChild(inp);
if(i===0){const sp=document.createElement('span');sp.textContent='〜';row.appendChild(sp);}
});
ctrl.appendChild(row);
} else if(mode==='step'){
const row=document.createElement('div');
row.className='cr-range-row';
['base','step'].forEach((k,i)=>{
const inp=document.createElement('input');
inp.type='number';inp.min=i===0?f.min:1;inp.max=f.max;
inp.placeholder=i===0?'開始':' 間隔';
inp.value=vals&&vals[k]!==undefined?vals[k]:'';
inp.dataset.field=f.id;inp.dataset.part=k;
inp.addEventListener('input',onControlChange);
row.appendChild(inp);
if(i===0){const sp=document.createElement('span');sp.textContent='/';row.appendChild(sp);}
});
ctrl.appendChild(row);
}
}

function onModeChange(f){
const mode=document.getElementById(`cr-sel-${f.id}`).value;
renderControl(f,mode);
if(!updating) buildExprFromFields();
}

function onControlChange(){
if(!updating) buildExprFromFields();
}

/* ── build expr from fields ── */
function buildExprFromFields(){
const parts=FIELDS.map(f=>{
const mode=document.getElementById(`cr-sel-${f.id}`).value;
const ctrl=document.getElementById(`cr-ctrl-${f.id}`);
if(mode==='every') return '*';
if(mode==='specific'){
const v=ctrl.querySelector('input')?.value.trim();
return v!==''&&!isNaN(v)?String(parseInt(v,10)):'*';
}
if(mode==='range'){
const inputs=ctrl.querySelectorAll('input');
const from=inputs[0]?.value.trim();
const to=inputs[1]?.value.trim();
if(from!==''&&to!==''&&!isNaN(from)&&!isNaN(to)) return `${parseInt(from,10)}-${parseInt(to,10)}`;
return '*';
}
if(mode==='step'){
const inputs=ctrl.querySelectorAll('input');
const base=inputs[0]?.value.trim();
const step=inputs[1]?.value.trim();
if(step!==''&&!isNaN(step)){
const b=base!==''&&!isNaN(base)?String(parseInt(base,10)):'*';
return `${b}/${parseInt(step,10)}`;
}
return '*';
}
return '*';
});
updating=true;
exprEl.value=parts.join(' ');
updating=false;
refresh();
}

/* ── parse & validate ── */
function parseField(tok,min,max){
if(tok==='*') return {type:'every'};
// step: base/step
if(tok.includes('/')){
const [b,s]=tok.split('/');
const base=b==='*'?min:parseInt(b,10);
const step=parseInt(s,10);
if(isNaN(base)||isNaN(step)||step<1||base<min||base>max) return null;
return {type:'step',base,step};
}
// range
if(tok.includes('-')){
const [a,b]=tok.split('-');
const from=parseInt(a,10),to=parseInt(b,10);
if(isNaN(from)||isNaN(to)||from<min||to>max||from>to) return null;
return {type:'range',from,to};
}
// list (basic: single value)
const v=parseInt(tok,10);
if(isNaN(v)||v<min||v>max) return null;
return {type:'specific',v};
}

function validate(expr){
const parts=expr.trim().split(/\s+/);
if(parts.length!==5) return {ok:false,msg:'フィールドは5つ必要です（分 時 日 月 曜日）'};
const parsed=[];
for(let i=0;i<5;i++){
const r=parseField(parts[i],FIELDS[i].min,FIELDS[i].max);
if(!r) return {ok:false,msg:`「${FIELDS[i].label}」フィールドの値が無効です: ${parts[i]}`};
parsed.push(r);
}
return {ok:true,parts,parsed};
}

/* ── describe ── */
function describeField(p,f){
if(p.type==='every') return null;
if(p.type==='specific'){
if(f.id==='dow') return DOWS_JP[p.v]+'曜日';
if(f.id==='mon') return MONTHS_JP[p.v-1];
return `${f.label}=${p.v}`;
}
if(p.type==='range'){
if(f.id==='dow') return `${DOWS_JP[p.from]}〜${DOWS_JP[p.to]}曜日`;
if(f.id==='mon') return `${MONTHS_JP[p.from-1]}〜${MONTHS_JP[p.to-1]}`;
return `${f.label}${p.from}〜${p.to}`;
}
if(p.type==='step'){
const base=p.base===FIELDS[FIELDS.findIndex(f2=>f2===f)].min&&p.base===FIELDS[FIELDS.findIndex(f2=>f2===f)].min?'':p.base;
if(f.id==='min') return `${p.step}分ごと${base!==''?`（${base}分から）`:''}`;
if(f.id==='hour') return `${p.step}時間ごと`;
return `${f.label}${p.step}ごと`;
}
return null;
}

function describe(v){
const desc=validate(v);
if(!desc.ok) return '（無効な式）';
const {parsed}=desc;
// Special cases
if(parsed.every(p=>p.type==='every')) return '毎分実行';
const mins=parsed[0],hrs=parsed[1],dom=parsed[2],mon=parsed[3],dow=parsed[4];
// step-min only
if(mins.type==='step'&&hrs.type==='every'&&dom.type==='every'&&mon.type==='every'&&dow.type==='every'){
return `${mins.step}分ごとに実行`;
}
// every hour at specific min
if(mins.type==='specific'&&hrs.type==='every'&&dom.type==='every'&&mon.type==='every'&&dow.type==='every'){
return `毎時${mins.v}分に実行`;
}
// daily at specific time
if(mins.type==='specific'&&hrs.type==='specific'&&dom.type==='every'&&mon.type==='every'&&dow.type==='every'){
return `毎日 ${String(hrs.v).padStart(2,'0')}:${String(mins.v).padStart(2,'0')} に実行`;
}
// weekly
if(mins.type==='specific'&&hrs.type==='specific'&&dom.type==='every'&&mon.type==='every'&&dow.type!=='every'){
const dowDesc=dow.type==='specific'?DOWS_JP[dow.v]+'曜日':dow.type==='range'?`${DOWS_JP[dow.from]}〜${DOWS_JP[dow.to]}曜日`:'指定曜日';
return `毎週${dowDesc} ${String(hrs.v).padStart(2,'0')}:${String(mins.v).padStart(2,'0')} に実行`;
}
// monthly
if(mins.type==='specific'&&hrs.type==='specific'&&dom.type==='specific'&&mon.type==='every'&&dow.type==='every'){
return `毎月${dom.v}日 ${String(hrs.v).padStart(2,'0')}:${String(mins.v).padStart(2,'0')} に実行`;
}
// weekdays
if(dow.type==='range'&&dow.from===1&&dow.to===5&&dom.type==='every'){
const timeStr=hrs.type==='specific'&&mins.type==='specific'?` ${String(hrs.v).padStart(2,'0')}:${String(mins.v).padStart(2,'0')}`:'';
return `平日（月〜金）${timeStr} に実行`;
}
// fallback
const parts=FIELDS.map((f,i)=>describeField(parsed[i],f)).filter(Boolean);
return parts.length?parts.join('、')+'に実行':'スケジュール実行';
}

/* ── next executions ── */
function matchField(p,v){
if(p.type==='every') return true;
if(p.type==='specific') return v===p.v;
if(p.type==='range') return v>=p.from&&v<=p.to;
if(p.type==='step'){
if(v<p.base) return false;
return (v-p.base)%p.step===0;
}
return false;
}

function nextExecutions(expr,count){
const res=validate(expr);
if(!res.ok) return [];
const {parsed}=res;
const [pMin,pHr,pDom,pMon,pDow]=parsed;
const results=[];
const now=new Date();
// start from next minute
const start=new Date(now.getFullYear(),now.getMonth(),now.getDate(),now.getHours(),now.getMinutes()+1,0,0);
let cur=new Date(start);
const limit=new Date(cur.getTime()+366*24*60*60*1000);
while(results.length<count&&cur<limit){
const m=cur.getMinutes();
const h=cur.getHours();
const d=cur.getDate();
const mo=cur.getMonth()+1;
const dw=cur.getDay();
if(matchField(pMon,mo)&&matchField(pDom,d)&&matchField(pDow,dw)&&matchField(pHr,h)&&matchField(pMin,m)){
results.push(new Date(cur));
}
cur=new Date(cur.getTime()+60000);
}
return results;
}

function relTime(d){
const diff=Math.round((d-Date.now())/60000);
if(diff<1) return '間もなく';
if(diff<60) return `約${diff}分後`;
const h=Math.round(diff/60);
if(h<24) return `約${h}時間後`;
return `約${Math.round(h/24)}日後`;
}

/* ── refresh UI ── */
function refresh(){
const expr=exprEl.value.trim();
const res=validate(expr);
// badge
if(res.ok){
exprEl.classList.remove('cr-invalid');
badgeWrap.innerHTML='<span class="cr-badge cr-badge-ok">✓ 有効なCron式</span>';
} else {
exprEl.classList.add('cr-invalid');
badgeWrap.innerHTML=`<span class="cr-badge cr-badge-err">✗ ${escHtml(res.msg)}</span>`;
}
// description
descEl.textContent=describe(expr);
// next executions
if(res.ok){
const nexts=nextExecutions(expr,10);
if(nexts.length===0){
nextEl.innerHTML='<p class="cr-err-msg">今後1年以内の実行予定が見つかりませんでした。</p>';
} else {
const ul=document.createElement('ul');
ul.className='cr-next-list';
nexts.forEach(d=>{
const li=document.createElement('li');
const dtStr=formatDate(d);
li.innerHTML=`<span class="cr-dt">${escHtml(dtStr)}</span><span class="cr-rel">${escHtml(relTime(d))}</span>`;
ul.appendChild(li);
});
nextEl.innerHTML='';
nextEl.appendChild(ul);
}
} else {
nextEl.innerHTML='<p class="cr-err-msg">有効なCron式を入力すると実行時刻を計算します。</p>';
}
// sync fields
if(!updating) syncFieldsFromExpr(expr);
}

function formatDate(d){
const Y=d.getFullYear();
const M=String(d.getMonth()+1).padStart(2,'0');
const D=String(d.getDate()).padStart(2,'0');
const h=String(d.getHours()).padStart(2,'0');
const m=String(d.getMinutes()).padStart(2,'0');
const dw=DOWS_JP[d.getDay()];
return `${Y}/${M}/${D}（${dw}） ${h}:${m}`;
}

function escHtml(s){
return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

/* ── sync fields from expression ── */
function syncFieldsFromExpr(expr){
const parts=expr.trim().split(/\s+/);
if(parts.length!==5) return;
updating=true;
FIELDS.forEach((f,i)=>{
const tok=parts[i];
const sel=document.getElementById(`cr-sel-${f.id}`);
if(!sel) return;
let mode,vals;
if(tok==='*'){mode='every';vals={};}
else if(tok.includes('/')){
mode='step';
const [b,s]=tok.split('/');
vals={base:b==='*'?f.min:parseInt(b,10),step:parseInt(s,10)};
} else if(tok.includes('-')){
mode='range';
const [a,b]=tok.split('-');
vals={from:parseInt(a,10),to:parseInt(b,10)};
} else {
mode='specific';
vals={v:parseInt(tok,10)};
}
if(sel.value!==mode){
sel.value=mode;
renderControl(f,mode,vals);
} else {
// update control values without re-render
const ctrl=document.getElementById(`cr-ctrl-${f.id}`);
if(mode==='specific'){
const inp=ctrl.querySelector('input');
if(inp&&String(inp.value)!==String(vals.v)) inp.value=vals.v;
} else if(mode==='range'){
const inputs=ctrl.querySelectorAll('input');
if(inputs[0]&&String(inputs[0].value)!==String(vals.from)) inputs[0].value=vals.from;
if(inputs[1]&&String(inputs[1].value)!==String(vals.to)) inputs[1].value=vals.to;
} else if(mode==='step'){
const inputs=ctrl.querySelectorAll('input');
if(inputs[0]&&String(inputs[0].value)!==String(vals.base)) inputs[0].value=vals.base;
if(inputs[1]&&String(inputs[1].value)!==String(vals.step)) inputs[1].value=vals.step;
}
}
});
updating=false;
}

/* ── event listeners ── */
exprEl.addEventListener('input',()=>{if(!updating)refresh();});

copyBtn.addEventListener('click',()=>{
navigator.clipboard.writeText(exprEl.value.trim()).then(()=>{
copyBtn.textContent='コピー済み';
copyBtn.classList.add('copied');
setTimeout(()=>{copyBtn.textContent='コピー';copyBtn.classList.remove('copied');},1800);
}).catch(()=>{
exprEl.select();document.execCommand('copy');
});
});

document.querySelectorAll('.cr-preset-btn').forEach(btn=>{
btn.addEventListener('click',()=>{
exprEl.value=btn.dataset.cron;
refresh();
});
});

/* ── init ── */
buildFields();
refresh();
})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

---

> Unixタイムスタンプを変換 → [Unixタイムスタンプ変換ツール](/ja/tools/timestamp-converter/)
> Gitコマンドを生成 → [Gitコマンドジェネレーター](/ja/tools/git-command-generator/)
> ファイル権限を計算 → [Chmod計算ツール](/ja/tools/chmod-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
