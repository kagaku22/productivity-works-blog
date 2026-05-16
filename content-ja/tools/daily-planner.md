---
title: "デイリープランナー"
date: 2025-05-16
description: "無料のオンラインデイリープランナー。タイムブロックで1日のスケジュールを可視化。カテゴリ別色分け・印刷対応。ブラウザにデータ保存。"
categories: ["無料ツール"]
slug: "daily-planner"
ShowToc: false
cover:
  image: "/images/covers/daily-planner-ja.png"
  alt: "デイリープランナー"
---

<div id="dp-app">
<style>
/* ── Reset & base ── */
#dp-app *,#dp-app *::before,#dp-app *::after{box-sizing:border-box;margin:0;padding:0}
#dp-app{
  font-family:'Hiragino Sans','Noto Sans JP','Yu Gothic UI',sans-serif;
  font-size:15px;line-height:1.6;
  color:#e2e8f0;
  background:#0f172a;
  border-radius:12px;
  padding:24px;
  max-width:960px;
  margin:0 auto;
}

/* ── Header ── */
#dp-app .dp-header{
  display:flex;flex-wrap:wrap;align-items:center;gap:12px;
  margin-bottom:24px;padding-bottom:16px;
  border-bottom:1px solid #1e293b;
}
#dp-app .dp-header h2{font-size:1.3rem;font-weight:700;color:#f1f5f9;flex:1}
#dp-app .dp-date-nav{display:flex;align-items:center;gap:8px}
#dp-app .dp-date-nav button{
  background:#1e293b;border:none;color:#94a3b8;
  padding:6px 10px;border-radius:7px;cursor:pointer;font-size:1rem;
  transition:background 0.15s,color 0.15s;
}
#dp-app .dp-date-nav button:hover{background:#334155;color:#f1f5f9}
#dp-app .dp-date-input{
  background:#1e293b;border:1px solid #334155;color:#e2e8f0;
  padding:7px 10px;border-radius:7px;font-size:0.875rem;outline:none;
  transition:border-color 0.15s;
}
#dp-app .dp-date-input:focus{border-color:#6366f1}
#dp-app .dp-btn{
  padding:8px 18px;border-radius:8px;border:none;cursor:pointer;
  font-size:0.875rem;font-weight:600;transition:opacity 0.15s;
}
#dp-app .dp-btn:hover{opacity:0.85}
#dp-app .dp-btn-primary{background:#6366f1;color:#fff}
#dp-app .dp-btn-sm{padding:5px 12px;font-size:0.8rem;border-radius:6px}
#dp-app .dp-btn-danger{background:#ef4444;color:#fff}
#dp-app .dp-btn-ghost{background:transparent;border:1px solid #334155;color:#94a3b8}
#dp-app .dp-btn-ghost:hover{border-color:#6366f1;color:#e2e8f0}
#dp-app .dp-btn-print{background:#0f766e;color:#fff}

/* ── Two-column layout ── */
#dp-app .dp-layout{display:grid;grid-template-columns:1fr 300px;gap:20px}
@media(max-width:720px){#dp-app .dp-layout{grid-template-columns:1fr}}

/* ── Timeline ── */
#dp-app .dp-timeline{
  background:#0a0f1e;
  border-radius:10px;
  border:1px solid #1e293b;
  overflow:hidden;
}
#dp-app .dp-hour-row{
  display:flex;align-items:stretch;
  border-bottom:1px solid #1e293b;
  min-height:52px;
  position:relative;
}
#dp-app .dp-hour-row:last-child{border-bottom:none}
#dp-app .dp-hour-label{
  width:56px;min-width:56px;
  font-size:0.72rem;font-weight:600;color:#475569;
  padding:4px 6px 0 8px;
  border-right:1px solid #1e293b;
  user-select:none;
}
#dp-app .dp-hour-lane{flex:1;position:relative;padding:4px 6px 4px 8px}
#dp-app .dp-half-mark{
  position:absolute;left:56px;right:0;
  top:50%;border-top:1px dashed #1e293b;
  pointer-events:none;
}

/* ── Blocks on timeline ── */
#dp-app .dp-block{
  display:flex;align-items:flex-start;gap:6px;
  padding:4px 8px;border-radius:6px;
  margin-bottom:3px;cursor:pointer;
  transition:opacity 0.15s,transform 0.1s;
  border-left:3px solid transparent;
  font-size:0.8rem;
  word-break:break-word;
}
#dp-app .dp-block:hover{opacity:0.85;transform:translateX(2px)}
#dp-app .dp-block-title{font-weight:600;color:#f1f5f9;flex:1}
#dp-app .dp-block-time{font-size:0.7rem;color:rgba(255,255,255,0.55);white-space:nowrap}
#dp-app .dp-block-del{
  background:none;border:none;color:rgba(255,255,255,0.4);
  cursor:pointer;font-size:0.85rem;padding:0 2px;
  line-height:1;transition:color 0.15s;
}
#dp-app .dp-block-del:hover{color:#ef4444}

/* ── Sidebar ── */
#dp-app .dp-card{
  background:#1e293b;border-radius:10px;padding:18px;margin-bottom:16px;
}
#dp-app .dp-card h3{
  font-size:0.88rem;font-weight:700;color:#94a3b8;
  text-transform:uppercase;letter-spacing:.04em;margin-bottom:14px;
}

/* ── Add-block form ── */
#dp-app .dp-field{display:flex;flex-direction:column;gap:5px;margin-bottom:12px}
#dp-app .dp-field label{font-size:0.75rem;font-weight:700;color:#64748b;letter-spacing:.02em}
#dp-app .dp-field input[type=text],
#dp-app .dp-field input[type=time],
#dp-app .dp-field select{
  background:#0f172a;border:1px solid #334155;border-radius:7px;
  color:#e2e8f0;padding:7px 10px;font-size:0.875rem;outline:none;
  transition:border-color 0.15s;width:100%;
  font-family:inherit;
}
#dp-app .dp-field input[type=text]:focus,
#dp-app .dp-field input[type=time]:focus,
#dp-app .dp-field select:focus{border-color:#6366f1}
#dp-app .dp-field input[type=color]{
  width:38px;height:34px;padding:2px;border-radius:7px;
  border:1px solid #334155;background:#0f172a;cursor:pointer;
}
#dp-app .dp-time-row{display:flex;gap:8px}
#dp-app .dp-time-row .dp-field{flex:1}
#dp-app .dp-color-row{display:flex;align-items:center;gap:8px;flex-wrap:wrap;margin-top:2px}
#dp-app .dp-color-swatch{
  width:24px;height:24px;border-radius:50%;border:2px solid #334155;
  cursor:pointer;transition:transform 0.1s;flex-shrink:0;
}
#dp-app .dp-color-swatch:hover{transform:scale(1.15)}
#dp-app .dp-color-swatch.selected{border-color:#f1f5f9;transform:scale(1.2)}

/* ── Category presets ── */
#dp-app .dp-cat-chips{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:10px}
#dp-app .dp-cat-chip{
  padding:4px 9px;border-radius:20px;border:1px solid #334155;
  background:#0f172a;color:#94a3b8;font-size:0.75rem;font-weight:600;
  cursor:pointer;transition:all 0.15s;
  font-family:inherit;
}
#dp-app .dp-cat-chip:hover{border-color:#6366f1;color:#a5b4fc}
#dp-app .dp-cat-chip.active{color:#fff;border-color:transparent}

/* ── Summary ── */
#dp-app .dp-summary-list{list-style:none}
#dp-app .dp-summary-item{
  display:flex;align-items:center;gap:8px;
  padding:6px 0;border-bottom:1px solid #0f172a;font-size:0.85rem;
}
#dp-app .dp-summary-item:last-child{border-bottom:none}
#dp-app .dp-summary-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}
#dp-app .dp-summary-cat{flex:1;color:#cbd5e1}
#dp-app .dp-summary-hrs{color:#94a3b8;font-size:0.8rem;white-space:nowrap}
#dp-app .dp-summary-bar-wrap{
  height:4px;background:#0f172a;border-radius:2px;margin-top:2px;overflow:hidden;
}
#dp-app .dp-summary-bar{height:100%;border-radius:2px;transition:width 0.4s}
#dp-app .dp-total-hrs{
  margin-top:12px;padding-top:10px;border-top:1px solid #0f172a;
  font-size:0.85rem;color:#94a3b8;display:flex;justify-content:space-between;
}
#dp-app .dp-total-hrs span{color:#f1f5f9;font-weight:700}

/* ── Edit modal ── */
#dp-app .dp-modal-backdrop{
  position:fixed;inset:0;background:rgba(0,0,0,0.6);
  display:flex;align-items:center;justify-content:center;z-index:9999;
}
#dp-app .dp-modal{
  background:#1e293b;border-radius:12px;padding:24px;width:90%;max-width:400px;
  box-shadow:0 20px 60px rgba(0,0,0,0.5);
  font-family:'Hiragino Sans','Noto Sans JP','Yu Gothic UI',sans-serif;
}
#dp-app .dp-modal h3{font-size:1rem;font-weight:700;color:#f1f5f9;margin-bottom:16px}
#dp-app .dp-modal-footer{display:flex;gap:8px;justify-content:flex-end;margin-top:16px}

/* ── Print ── */
@media print{
  #dp-app .dp-sidebar,#dp-app .dp-header .dp-btn,
  #dp-app .dp-block-del,#dp-app .dp-date-nav button{display:none!important}
  #dp-app .dp-layout{grid-template-columns:1fr}
  #dp-app{background:#fff;color:#1e293b;padding:0}
  #dp-app .dp-timeline{border:1px solid #e2e8f0;background:#fff}
  #dp-app .dp-hour-row{border-bottom-color:#f1f5f9;min-height:40px}
  #dp-app .dp-hour-label{color:#94a3b8;border-right-color:#f1f5f9}
  #dp-app .dp-block-title{color:#0f172a}
  #dp-app .dp-block-time{color:#475569}
  #dp-app .dp-header h2{color:#0f172a}
  #dp-app .dp-date-input{color:#0f172a;background:#fff;border-color:#e2e8f0}
}
</style>

<!-- ── Header ── -->
<div class="dp-header">
  <h2>デイリープランナー</h2>
  <div class="dp-date-nav">
    <button onclick="dpNav(-1)" title="前の日">&#8592;</button>
    <input type="date" class="dp-date-input" id="dp-date-pick" onchange="dpSetDate(this.value)">
    <button onclick="dpNav(1)" title="次の日">&#8594;</button>
    <button class="dp-btn dp-btn-sm dp-btn-ghost" onclick="dpToday()">今日</button>
  </div>
  <button class="dp-btn dp-btn-sm dp-btn-print" onclick="window.print()">&#128438; 印刷</button>
</div>

<!-- ── Main layout ── -->
<div class="dp-layout">

  <!-- Timeline -->
  <div>
    <div class="dp-timeline" id="dp-timeline"></div>
  </div>

  <!-- Sidebar -->
  <div>

    <!-- Add Block Form -->
    <div class="dp-card">
      <h3>タイムブロックを追加</h3>

      <div class="dp-field">
        <label>タイトル</label>
        <input type="text" id="dp-title" placeholder="例：チームミーティング" maxlength="60">
      </div>

      <div class="dp-field">
        <label>カテゴリ</label>
        <div class="dp-cat-chips" id="dp-cat-chips"></div>
        <select id="dp-cat-select">
          <option value="仕事">仕事</option>
          <option value="ミーティング">ミーティング</option>
          <option value="プライベート">プライベート</option>
          <option value="運動">運動</option>
          <option value="休憩">休憩</option>
          <option value="その他">その他</option>
        </select>
      </div>

      <div class="dp-time-row">
        <div class="dp-field">
          <label>開始</label>
          <input type="time" id="dp-start" value="09:00">
        </div>
        <div class="dp-field">
          <label>終了</label>
          <input type="time" id="dp-end" value="10:00">
        </div>
      </div>

      <div class="dp-field">
        <label>カラー</label>
        <div class="dp-color-row" id="dp-color-row"></div>
      </div>

      <button class="dp-btn dp-btn-primary" style="width:100%;margin-top:4px" onclick="dpAddBlock()">＋ 追加</button>
    </div>

    <!-- Summary -->
    <div class="dp-card">
      <h3>カテゴリ別集計</h3>
      <ul class="dp-summary-list" id="dp-summary"></ul>
      <div class="dp-total-hrs" id="dp-total-hrs" style="display:none">
        合計予定時間: <span id="dp-total-val">0時間</span>
      </div>
    </div>

  </div><!-- /sidebar -->
</div><!-- /layout -->

<script>
(function(){
'use strict';

/* ── Constants ── */
var HOURS_START = 6;
var HOURS_END   = 24;
var LS_KEY = 'dp_data_ja_v1';

var CAT_COLORS = {
  '仕事':       '#6366f1',
  'ミーティング':'#0ea5e9',
  'プライベート':'#22c55e',
  '運動':       '#f59e0b',
  '休憩':       '#94a3b8',
  'その他':     '#ec4899'
};

var PALETTE = ['#6366f1','#0ea5e9','#22c55e','#f59e0b','#ef4444','#ec4899','#8b5cf6','#14b8a6','#f97316','#94a3b8'];

/* ── State ── */
var currentDate = todayStr();
var data = {};
var selectedColor = PALETTE[0];

/* ── Helpers ── */
function todayStr(){
  var d=new Date();
  return d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate());
}
function pad(n){ return n<10?'0'+n:''+n; }
function uid(){ return Math.random().toString(36).slice(2,10)+Date.now().toString(36); }
function esc(s){ var d=document.createElement('div');d.textContent=s;return d.innerHTML; }
function timeToMin(t){ var p=t.split(':');return parseInt(p[0],10)*60+parseInt(p[1],10); }
function minToLabel(m){
  var h=Math.floor(m/60), mn=m%60;
  return pad(h)+':'+pad(mn);
}
function blockDuration(b){
  var s=timeToMin(b.start), e=timeToMin(b.end);
  if(e<=s) e+=24*60;
  return e-s;
}
function durLabel(min){
  var h=Math.floor(min/60), m=min%60;
  return h?(h+'時間'+(m?m+'分':'')):(m+'分');
}

/* ── Storage ── */
function save(){ try{localStorage.setItem(LS_KEY,JSON.stringify(data));}catch(e){} }
function load(){
  try{ var raw=localStorage.getItem(LS_KEY); if(raw) data=JSON.parse(raw); }
  catch(e){ data={}; }
}

/* ── Date navigation ── */
window.dpNav = function(delta){
  var d=new Date(currentDate+'T00:00:00');
  d.setDate(d.getDate()+delta);
  currentDate=d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate());
  document.getElementById('dp-date-pick').value=currentDate;
  render();
};
window.dpSetDate = function(v){ currentDate=v; render(); };
window.dpToday = function(){ currentDate=todayStr(); document.getElementById('dp-date-pick').value=currentDate; render(); };

/* ── Category chips ── */
function initCatChips(){
  var wrap=document.getElementById('dp-cat-chips');
  wrap.innerHTML='';
  Object.keys(CAT_COLORS).forEach(function(cat){
    var btn=document.createElement('button');
    btn.className='dp-cat-chip';
    btn.textContent=cat;
    btn.style.background=CAT_COLORS[cat]+'22';
    btn.style.borderColor=CAT_COLORS[cat]+'66';
    btn.style.color=CAT_COLORS[cat];
    btn.onclick=function(){
      document.getElementById('dp-cat-select').value=cat;
      document.querySelectorAll('#dp-cat-chips .dp-cat-chip').forEach(function(b){
        b.classList.remove('active');
        b.style.background=CAT_COLORS[b.textContent]+'22';
        b.style.color=CAT_COLORS[b.textContent];
      });
      btn.classList.add('active');
      btn.style.background=CAT_COLORS[cat];
      btn.style.color='#fff';
      selectedColor=CAT_COLORS[cat];
      refreshColorSwatches();
    };
    wrap.appendChild(btn);
  });
}

/* ── Color palette ── */
function initColorRow(){
  var row=document.getElementById('dp-color-row');
  row.innerHTML='';
  PALETTE.forEach(function(c){
    var sw=document.createElement('div');
    sw.className='dp-color-swatch'+(c===selectedColor?' selected':'');
    sw.style.background=c;
    sw.title=c;
    sw.onclick=function(){ selectedColor=c; refreshColorSwatches(); };
    row.appendChild(sw);
  });
  var cp=document.createElement('input');
  cp.type='color'; cp.value=selectedColor;
  cp.title='カスタムカラー';
  cp.style.cssText='width:24px;height:24px;padding:0;border:2px solid #334155;border-radius:50%;cursor:pointer;';
  cp.oninput=function(){ selectedColor=cp.value; refreshColorSwatches(); };
  row.appendChild(cp);
}
function refreshColorSwatches(){
  document.querySelectorAll('#dp-color-row .dp-color-swatch').forEach(function(sw){
    sw.classList.toggle('selected', sw.style.backgroundColor===hexToRgb(selectedColor)||sw.style.background===selectedColor);
  });
}
function hexToRgb(hex){ return hex; }

/* ── Add block ── */
window.dpAddBlock = function(){
  var title=document.getElementById('dp-title').value.trim();
  var cat=document.getElementById('dp-cat-select').value;
  var start=document.getElementById('dp-start').value;
  var end=document.getElementById('dp-end').value;
  if(!title){ document.getElementById('dp-title').focus(); return; }
  if(!start||!end){ alert('開始・終了時刻を設定してください。'); return; }
  if(timeToMin(end)<=timeToMin(start)){ alert('終了時刻は開始時刻より後にしてください。'); return; }
  var block={id:uid(),title:title,cat:cat,start:start,end:end,color:selectedColor};
  if(!data[currentDate]) data[currentDate]=[];
  data[currentDate].push(block);
  save();
  document.getElementById('dp-title').value='';
  render();
};

/* ── Delete block ── */
window.dpDeleteBlock = function(id){
  if(!data[currentDate]) return;
  data[currentDate]=data[currentDate].filter(function(b){return b.id!==id;});
  save(); render();
};

/* ── Edit modal ── */
window.dpEditBlock = function(id){
  var blocks=data[currentDate]||[];
  var b=blocks.find(function(x){return x.id===id;});
  if(!b) return;
  var backdrop=document.createElement('div');
  backdrop.className='dp-modal-backdrop';
  backdrop.id='dp-modal-backdrop';
  backdrop.innerHTML=
    '<div class="dp-modal" onclick="event.stopPropagation()">'+
    '<h3>ブロックを編集</h3>'+
    '<div class="dp-field"><label>タイトル</label><input type="text" id="dp-edit-title" value="'+esc(b.title)+'" maxlength="60" style="background:#0f172a;border:1px solid #334155;border-radius:7px;color:#e2e8f0;padding:7px 10px;font-size:.875rem;outline:none;width:100%;font-family:inherit;"></div>'+
    '<div class="dp-field"><label>カテゴリ</label><select id="dp-edit-cat" style="background:#0f172a;border:1px solid #334155;border-radius:7px;color:#e2e8f0;padding:7px 10px;font-size:.875rem;outline:none;width:100%;font-family:inherit;">'+
      Object.keys(CAT_COLORS).map(function(c){return '<option value="'+c+'"'+(c===b.cat?' selected':'')+'>'+c+'</option>';}).join('')+
      '<option value="その他"'+(b.cat==='その他'?' selected':'')+'>その他</option>'+
    '</select></div>'+
    '<div style="display:flex;gap:8px">'+
      '<div class="dp-field" style="flex:1"><label>開始</label><input type="time" id="dp-edit-start" value="'+b.start+'" style="background:#0f172a;border:1px solid #334155;border-radius:7px;color:#e2e8f0;padding:7px 10px;font-size:.875rem;outline:none;width:100%;"></div>'+
      '<div class="dp-field" style="flex:1"><label>終了</label><input type="time" id="dp-edit-end" value="'+b.end+'" style="background:#0f172a;border:1px solid #334155;border-radius:7px;color:#e2e8f0;padding:7px 10px;font-size:.875rem;outline:none;width:100%;"></div>'+
    '</div>'+
    '<div class="dp-field"><label>カラー</label><input type="color" id="dp-edit-color" value="'+b.color+'" style="width:40px;height:34px;border-radius:7px;border:1px solid #334155;background:#0f172a;cursor:pointer;"></div>'+
    '<div class="dp-modal-footer">'+
      '<button class="dp-btn dp-btn-sm dp-btn-ghost" onclick="dpCloseModal()">キャンセル</button>'+
      '<button class="dp-btn dp-btn-sm dp-btn-danger" onclick="dpDeleteBlock(\''+id+'\');dpCloseModal()">削除</button>'+
      '<button class="dp-btn dp-btn-sm dp-btn-primary" onclick="dpSaveEdit(\''+id+'\')">保存</button>'+
    '</div>'+
    '</div>';
  backdrop.onclick=function(){ dpCloseModal(); };
  document.getElementById('dp-app').appendChild(backdrop);
  document.getElementById('dp-edit-title').focus();
};

window.dpSaveEdit = function(id){
  var title=document.getElementById('dp-edit-title').value.trim();
  var cat=document.getElementById('dp-edit-cat').value;
  var start=document.getElementById('dp-edit-start').value;
  var end=document.getElementById('dp-edit-end').value;
  var color=document.getElementById('dp-edit-color').value;
  if(!title||!start||!end) return;
  if(timeToMin(end)<=timeToMin(start)){ alert('終了時刻は開始時刻より後にしてください。'); return; }
  var b=(data[currentDate]||[]).find(function(x){return x.id===id;});
  if(b){ b.title=title; b.cat=cat; b.start=start; b.end=end; b.color=color; }
  save(); dpCloseModal(); render();
};

window.dpCloseModal = function(){
  var el=document.getElementById('dp-modal-backdrop');
  if(el) el.remove();
};

/* ── Render timeline ── */
function renderTimeline(){
  var tl=document.getElementById('dp-timeline');
  var blocks=(data[currentDate]||[]).slice().sort(function(a,b){return timeToMin(a.start)-timeToMin(b.start);});
  var html='';
  for(var h=HOURS_START; h<HOURS_END; h++){
    var label=pad(h)+':00';
    var hMin=h*60;
    var rowBlocks=blocks.filter(function(b){ var s=timeToMin(b.start); return s>=hMin&&s<hMin+60; });
    html+='<div class="dp-hour-row">';
    html+='<div class="dp-hour-label">'+label+'</div>';
    html+='<div class="dp-half-mark"></div>';
    html+='<div class="dp-hour-lane">';
    rowBlocks.forEach(function(b){
      var dur=blockDuration(b);
      var dl=durLabel(dur);
      var bg=b.color+'33';
      html+='<div class="dp-block" style="background:'+bg+';border-left-color:'+b.color+'" onclick="dpEditBlock(\''+b.id+'\')">';
      html+='<div style="flex:1;min-width:0">';
      html+='<div class="dp-block-title">'+esc(b.title)+'</div>';
      html+='<div class="dp-block-time">'+minToLabel(timeToMin(b.start))+' &#12316; '+minToLabel(timeToMin(b.end))+' &middot; '+dl+'</div>';
      html+='</div>';
      html+='<button class="dp-block-del" onclick="event.stopPropagation();dpDeleteBlock(\''+b.id+'\')" title="削除">&times;</button>';
      html+='</div>';
    });
    html+='</div></div>';
  }
  tl.innerHTML=html;
}

/* ── Render summary ── */
function renderSummary(){
  var blocks=data[currentDate]||[];
  var catMap={};
  var totalMin=0;
  blocks.forEach(function(b){
    var dur=blockDuration(b);
    if(!catMap[b.cat]) catMap[b.cat]={color:b.color,min:0};
    catMap[b.cat].min+=dur;
    catMap[b.cat].color=b.color;
    totalMin+=dur;
  });
  var list=document.getElementById('dp-summary');
  var totalEl=document.getElementById('dp-total-hrs');
  var totalVal=document.getElementById('dp-total-val');
  if(!Object.keys(catMap).length){
    list.innerHTML='<li style="color:#475569;font-size:0.8rem;padding:8px 0;">ブロックを追加すると集計が表示されます。</li>';
    totalEl.style.display='none';
    return;
  }
  totalEl.style.display='flex';
  totalVal.textContent=durLabel(totalMin);
  var items=Object.entries(catMap).sort(function(a,b){return b[1].min-a[1].min;});
  list.innerHTML=items.map(function(entry){
    var cat=entry[0], info=entry[1];
    var pct=totalMin>0?Math.round(info.min/totalMin*100):0;
    var dl=durLabel(info.min);
    return '<li class="dp-summary-item">'+
      '<div class="dp-summary-dot" style="background:'+info.color+'"></div>'+
      '<div style="flex:1">'+
        '<div style="display:flex;justify-content:space-between">'+
          '<span class="dp-summary-cat">'+esc(cat)+'</span>'+
          '<span class="dp-summary-hrs">'+dl+' ('+pct+'%)</span>'+
        '</div>'+
        '<div class="dp-summary-bar-wrap"><div class="dp-summary-bar" style="width:'+pct+'%;background:'+info.color+'"></div></div>'+
      '</div>'+
    '</li>';
  }).join('');
}

/* ── Master render ── */
function render(){
  var dp=document.getElementById('dp-date-pick');
  if(dp&&dp.value!==currentDate) dp.value=currentDate;
  renderTimeline();
  renderSummary();
}

/* ── Init ── */
load();
document.getElementById('dp-date-pick').value=currentDate;
initCatChips();
initColorRow();
render();

document.getElementById('dp-title').addEventListener('keydown',function(e){
  if(e.key==='Enter') dpAddBlock();
});

})();
</script>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">スケジュール管理と一緒に、請求・経費もクラウドで</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までまとめて管理。個人事業主・フリーランスにも最適。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:8px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

> 集中力を高める → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)
> 習慣を継続する → [習慣トラッカー](/ja/tools/habit-tracker/)
> タスクを整理する → [カンバンボード](/ja/tools/kanban-board/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
</div>
