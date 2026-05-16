---
title: "Daily Planner - Schedule Builder"
date: 2025-05-16
description: "Free online daily planner. Create a visual schedule with time blocks. Drag to adjust, color-code categories, and print your daily plan. Data saved in browser."
categories: ["Free Tools"]
slug: "daily-planner"
ShowToc: false
cover:
  image: "/images/covers/daily-planner.png"
  alt: "Daily Planner - Schedule Builder"
---

<div id="dp-app">
<style>
/* ── Reset & base ── */
#dp-app *,#dp-app *::before,#dp-app *::after{box-sizing:border-box;margin:0;padding:0}
#dp-app{
  font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;
  font-size:15px;line-height:1.5;
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
#dp-app .dp-header h2{font-size:1.35rem;font-weight:700;color:#f1f5f9;flex:1}
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
#dp-app .dp-timeline-wrap{position:relative}
#dp-app .dp-timeline{
  position:relative;
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
  width:54px;min-width:54px;
  font-size:0.72rem;font-weight:600;color:#475569;
  padding:4px 8px 0 8px;
  border-right:1px solid #1e293b;
  user-select:none;
}
#dp-app .dp-hour-lane{flex:1;position:relative;padding:4px 6px 4px 8px}
#dp-app .dp-half-mark{
  position:absolute;left:54px;right:0;
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
#dp-app .dp-sidebar{}
#dp-app .dp-card{
  background:#1e293b;border-radius:10px;padding:18px;margin-bottom:16px;
}
#dp-app .dp-card h3{
  font-size:0.9rem;font-weight:700;color:#94a3b8;
  text-transform:uppercase;letter-spacing:.05em;margin-bottom:14px;
}

/* ── Add-block form ── */
#dp-app .dp-field{display:flex;flex-direction:column;gap:5px;margin-bottom:12px}
#dp-app .dp-field label{font-size:0.75rem;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:.04em}
#dp-app .dp-field input[type=text],
#dp-app .dp-field input[type=time],
#dp-app .dp-field select{
  background:#0f172a;border:1px solid #334155;border-radius:7px;
  color:#e2e8f0;padding:7px 10px;font-size:0.875rem;outline:none;
  transition:border-color 0.15s;width:100%;
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
#dp-app .dp-color-row{display:flex;align-items:center;gap:8px;margin-top:2px}
#dp-app .dp-color-swatch{
  width:24px;height:24px;border-radius:50%;border:2px solid #334155;
  cursor:pointer;transition:transform 0.1s;flex-shrink:0;
}
#dp-app .dp-color-swatch:hover{transform:scale(1.15)}
#dp-app .dp-color-swatch.selected{border-color:#f1f5f9;transform:scale(1.2)}

/* ── Category presets ── */
#dp-app .dp-cat-chips{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:12px}
#dp-app .dp-cat-chip{
  padding:4px 10px;border-radius:20px;border:1px solid #334155;
  background:#0f172a;color:#94a3b8;font-size:0.75rem;font-weight:600;
  cursor:pointer;transition:all 0.15s;
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

/* ── Empty state ── */
#dp-app .dp-empty{
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  padding:40px 20px;color:#475569;font-size:0.875rem;gap:8px;text-align:center;
}
#dp-app .dp-empty-icon{font-size:2.5rem}

/* ── Edit modal ── */
#dp-app .dp-modal-backdrop{
  position:fixed;inset:0;background:rgba(0,0,0,0.6);
  display:flex;align-items:center;justify-content:center;z-index:9999;
}
#dp-app .dp-modal{
  background:#1e293b;border-radius:12px;padding:24px;width:90%;max-width:400px;
  box-shadow:0 20px 60px rgba(0,0,0,0.5);
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
  <h2>Daily Planner</h2>
  <div class="dp-date-nav">
    <button onclick="dpNav(-1)" title="Previous day">&#8592;</button>
    <input type="date" class="dp-date-input" id="dp-date-pick" onchange="dpSetDate(this.value)">
    <button onclick="dpNav(1)" title="Next day">&#8594;</button>
    <button class="dp-btn dp-btn-sm dp-btn-ghost" onclick="dpToday()">Today</button>
  </div>
  <button class="dp-btn dp-btn-sm dp-btn-print" onclick="window.print()">&#128438; Print</button>
</div>

<!-- ── Main layout ── -->
<div class="dp-layout">

  <!-- Timeline -->
  <div class="dp-timeline-wrap">
    <div class="dp-timeline" id="dp-timeline"></div>
  </div>

  <!-- Sidebar -->
  <div class="dp-sidebar">

    <!-- Add Block Form -->
    <div class="dp-card">
      <h3>Add Time Block</h3>

      <div class="dp-field">
        <label>Title</label>
        <input type="text" id="dp-title" placeholder="e.g. Team standup" maxlength="60">
      </div>

      <div class="dp-field">
        <label>Category</label>
        <div class="dp-cat-chips" id="dp-cat-chips"></div>
        <select id="dp-cat-select">
          <option value="Work">Work</option>
          <option value="Meeting">Meeting</option>
          <option value="Personal">Personal</option>
          <option value="Exercise">Exercise</option>
          <option value="Break">Break</option>
          <option value="Other">Other</option>
        </select>
      </div>

      <div class="dp-time-row">
        <div class="dp-field">
          <label>Start</label>
          <input type="time" id="dp-start" value="09:00">
        </div>
        <div class="dp-field">
          <label>End</label>
          <input type="time" id="dp-end" value="10:00">
        </div>
      </div>

      <div class="dp-field">
        <label>Color</label>
        <div class="dp-color-row" id="dp-color-row"></div>
      </div>

      <button class="dp-btn dp-btn-primary" style="width:100%;margin-top:4px" onclick="dpAddBlock()">+ Add Block</button>
    </div>

    <!-- Summary -->
    <div class="dp-card">
      <h3>Summary</h3>
      <ul class="dp-summary-list" id="dp-summary"></ul>
      <div class="dp-total-hrs" id="dp-total-hrs" style="display:none">
        Total planned: <span id="dp-total-val">0h 0m</span>
      </div>
    </div>

  </div><!-- /sidebar -->
</div><!-- /layout -->

<!-- Edit modal (injected by JS) -->

<script>
(function(){
'use strict';

/* ── Constants ── */
var HOURS_START = 6;   // 6 AM
var HOURS_END   = 24;  // midnight (exclusive label)
var LS_KEY = 'dp_data_v1';

var CAT_COLORS = {
  'Work':     '#6366f1',
  'Meeting':  '#0ea5e9',
  'Personal': '#22c55e',
  'Exercise': '#f59e0b',
  'Break':    '#94a3b8',
  'Other':    '#ec4899'
};

var PALETTE = ['#6366f1','#0ea5e9','#22c55e','#f59e0b','#ef4444','#ec4899','#8b5cf6','#14b8a6','#f97316','#94a3b8'];

/* ── State ── */
var currentDate = todayStr();
var data = {};       // { 'YYYY-MM-DD': [ {id,title,cat,start,end,color}, ... ] }
var selectedColor = PALETTE[0];
var editingId = null;

/* ── Helpers ── */
function todayStr(){
  var d = new Date();
  return d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate());
}
function pad(n){ return n < 10 ? '0'+n : ''+n; }
function uid(){ return Math.random().toString(36).slice(2,10)+Date.now().toString(36); }
function esc(s){
  var d=document.createElement('div'); d.textContent=s; return d.innerHTML;
}
function timeToMin(t){
  var p=t.split(':'); return parseInt(p[0],10)*60+parseInt(p[1],10);
}
function minToTime(m){
  return pad(Math.floor(m/60))+':'+pad(m%60);
}
function minToLabel(m){
  var h=Math.floor(m/60), mn=m%60, ampm=h>=12?'PM':'AM';
  var h12=h%12||12;
  return h12+(mn?':'+pad(mn):'')+' '+ampm;
}
function blockDuration(b){
  var s=timeToMin(b.start), e=timeToMin(b.end);
  if(e<=s) e+=24*60;
  return e-s;
}

/* ── Storage ── */
function save(){ try{localStorage.setItem(LS_KEY,JSON.stringify(data));}catch(e){} }
function load(){
  try{
    var raw=localStorage.getItem(LS_KEY);
    if(raw) data=JSON.parse(raw);
  }catch(e){ data={}; }
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
      document.querySelectorAll('#dp-cat-chips .dp-cat-chip').forEach(function(b){b.classList.remove('active')});
      btn.classList.add('active');
      btn.style.background=CAT_COLORS[cat];
      btn.style.color='#fff';
      // also update color
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
    sw.onclick=function(){
      selectedColor=c;
      refreshColorSwatches();
    };
    row.appendChild(sw);
  });
  // custom color picker
  var cp=document.createElement('input');
  cp.type='color'; cp.value=selectedColor;
  cp.title='Custom color';
  cp.style.cssText='width:24px;height:24px;padding:0;border:2px solid #334155;border-radius:50%;cursor:pointer;background:none;';
  cp.oninput=function(){ selectedColor=cp.value; refreshColorSwatches(); };
  row.appendChild(cp);
}
function refreshColorSwatches(){
  var swatches=document.querySelectorAll('#dp-color-row .dp-color-swatch');
  swatches.forEach(function(sw){
    sw.classList.toggle('selected', sw.style.background===hexToRgb(selectedColor)||sw.style.background===selectedColor);
  });
}
function hexToRgb(hex){
  // browsers sometimes return rgb() from style.background
  return hex; // good enough for toggle
}

/* ── Add block ── */
window.dpAddBlock = function(){
  var title=document.getElementById('dp-title').value.trim();
  var cat=document.getElementById('dp-cat-select').value;
  var start=document.getElementById('dp-start').value;
  var end=document.getElementById('dp-end').value;
  if(!title){ document.getElementById('dp-title').focus(); return; }
  if(!start||!end){ alert('Please set start and end time.'); return; }
  if(timeToMin(end)<=timeToMin(start)){ alert('End time must be after start time.'); return; }
  var block={ id:uid(), title:title, cat:cat, start:start, end:end, color:selectedColor };
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
  editingId=id;
  var backdrop=document.createElement('div');
  backdrop.className='dp-modal-backdrop';
  backdrop.id='dp-modal-backdrop';
  backdrop.innerHTML=
    '<div class="dp-modal" onclick="event.stopPropagation()">'+
    '<h3>Edit Block</h3>'+
    '<div class="dp-field"><label>Title</label><input type="text" id="dp-edit-title" value="'+esc(b.title)+'" maxlength="60"></div>'+
    '<div class="dp-field"><label>Category</label><select id="dp-edit-cat">'+
      Object.keys(CAT_COLORS).map(function(c){return '<option value="'+c+'"'+(c===b.cat?' selected':'')+'>'+c+'</option>';}).join('')+
      '<option value="Other"'+(b.cat==='Other'?' selected':'')+'>Other</option>'+
    '</select></div>'+
    '<div style="display:flex;gap:8px">'+
      '<div class="dp-field" style="flex:1"><label>Start</label><input type="time" id="dp-edit-start" value="'+b.start+'"></div>'+
      '<div class="dp-field" style="flex:1"><label>End</label><input type="time" id="dp-edit-end" value="'+b.end+'"></div>'+
    '</div>'+
    '<div class="dp-field"><label>Color</label><input type="color" id="dp-edit-color" value="'+b.color+'" style="width:40px;height:34px;border-radius:7px;border:1px solid #334155;background:#0f172a;cursor:pointer;"></div>'+
    '<div class="dp-modal-footer">'+
      '<button class="dp-btn dp-btn-sm dp-btn-ghost" onclick="dpCloseModal()">Cancel</button>'+
      '<button class="dp-btn dp-btn-sm dp-btn-danger" onclick="dpDeleteBlock(\''+id+'\');dpCloseModal()">Delete</button>'+
      '<button class="dp-btn dp-btn-sm dp-btn-primary" onclick="dpSaveEdit(\''+id+'\')">Save</button>'+
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
  if(timeToMin(end)<=timeToMin(start)){ alert('End time must be after start time.'); return; }
  var blocks=data[currentDate]||[];
  var b=blocks.find(function(x){return x.id===id;});
  if(b){ b.title=title; b.cat=cat; b.start=start; b.end=end; b.color=color; }
  save(); dpCloseModal(); render();
};

window.dpCloseModal = function(){
  var el=document.getElementById('dp-modal-backdrop');
  if(el) el.remove();
  editingId=null;
};

/* ── Render timeline ── */
function renderTimeline(){
  var tl=document.getElementById('dp-timeline');
  var blocks=data[currentDate]||[];
  // sort blocks by start
  blocks=blocks.slice().sort(function(a,b){ return timeToMin(a.start)-timeToMin(b.start); });

  var html='';
  for(var h=HOURS_START; h<HOURS_END; h++){
    var label = h===0?'12 AM': h<12?h+' AM': h===12?'12 PM': (h-12)+' PM';
    var hMin=h*60;
    // collect blocks that start in this hour
    var rowBlocks=blocks.filter(function(b){
      var s=timeToMin(b.start);
      return s>=hMin && s<hMin+60;
    });
    html+='<div class="dp-hour-row">';
    html+='<div class="dp-hour-label">'+label+'</div>';
    html+='<div class="dp-half-mark"></div>';
    html+='<div class="dp-hour-lane">';
    rowBlocks.forEach(function(b){
      var dur=blockDuration(b);
      var durLabel=dur>=60?(Math.floor(dur/60)+'h'+(dur%60?''+dur%60+'m':'')):dur+'m';
      var bg=b.color+'33';
      var borderColor=b.color;
      html+='<div class="dp-block" style="background:'+bg+';border-left-color:'+borderColor+'" onclick="dpEditBlock(\''+b.id+'\')">';
      html+='<div style="flex:1;min-width:0">';
      html+='<div class="dp-block-title">'+esc(b.title)+'</div>';
      html+='<div class="dp-block-time">'+minToLabel(timeToMin(b.start))+' &ndash; '+minToLabel(timeToMin(b.end))+' &middot; '+durLabel+'</div>';
      html+='</div>';
      html+='<button class="dp-block-del" onclick="event.stopPropagation();dpDeleteBlock(\''+b.id+'\')" title="Delete">&times;</button>';
      html+='</div>';
    });
    html+='</div>'; // lane
    html+='</div>'; // row
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
    if(!catMap[b.cat]) catMap[b.cat]={color:b.color, min:0};
    catMap[b.cat].min+=dur;
    catMap[b.cat].color=b.color;
    totalMin+=dur;
  });
  var list=document.getElementById('dp-summary');
  var totalEl=document.getElementById('dp-total-hrs');
  var totalVal=document.getElementById('dp-total-val');
  if(!Object.keys(catMap).length){
    list.innerHTML='<li style="color:#475569;font-size:0.8rem;padding:8px 0;">No blocks yet &mdash; add one to see your summary.</li>';
    totalEl.style.display='none';
    return;
  }
  totalEl.style.display='flex';
  totalVal.textContent=Math.floor(totalMin/60)+'h '+( totalMin%60?totalMin%60+'m':'');
  var items=Object.entries(catMap).sort(function(a,b){return b[1].min-a[1].min;});
  list.innerHTML=items.map(function(entry){
    var cat=entry[0], info=entry[1];
    var pct=totalMin>0?Math.round(info.min/totalMin*100):0;
    var h=Math.floor(info.min/60), m=info.min%60;
    var label=h?(h+'h'+(m?' '+m+'m':'')):(m+'m');
    return '<li class="dp-summary-item">'+
      '<div class="dp-summary-dot" style="background:'+info.color+'"></div>'+
      '<div style="flex:1">'+
        '<div style="display:flex;justify-content:space-between">'+
          '<span class="dp-summary-cat">'+esc(cat)+'</span>'+
          '<span class="dp-summary-hrs">'+label+' ('+pct+'%)</span>'+
        '</div>'+
        '<div class="dp-summary-bar-wrap"><div class="dp-summary-bar" style="width:'+pct+'%;background:'+info.color+'"></div></div>'+
      '</div>'+
    '</li>';
  }).join('');
}

/* ── Master render ── */
function render(){
  // Update date display
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

// Keyboard shortcut: Enter in title field
document.getElementById('dp-title').addEventListener('keydown',function(e){
  if(e.key==='Enter') dpAddBlock();
});

})();
</script>

---

> Focus your sessions with → [Pomodoro Timer](/tools/pomodoro-timer/)
> Build lasting habits → [Habit Tracker](/tools/habit-tracker/)
> Organize your tasks → [Kanban Board](/tools/kanban-board/)
</div>

## Related Articles

- [Best ChatGPT Prompts for Productivity 2026](/posts/best-chatgpt-prompts-for-productivity-2026/)
- [Best Remote Work Tools in 2026: The Complete Stack](/posts/best-remote-work-tools-2026/)
- [Best Productivity Apps for Remote Workers 2026: Tested and Ranked](/posts/best-productivity-apps-remote-workers-2026/)
