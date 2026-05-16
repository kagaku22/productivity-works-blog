---
title: "Habit Tracker"
date: 2025-05-16
description: "Free online habit tracker. Track daily habits with streaks, completion rates, and heatmap visualization — data saved locally, no sign-up required."
categories: ["Free Tools"]
slug: "habit-tracker"
ShowToc: false
cover:
  image: "/images/covers/habit-tracker.png"
  alt: "Habit Tracker"
---

<div id="ht-app">
<style>
/* ── Reset & base ── */
#ht-app *,#ht-app *::before,#ht-app *::after{box-sizing:border-box;margin:0;padding:0}
#ht-app{
  font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;
  font-size:15px;line-height:1.5;
  color:#e2e8f0;
  background:#0f172a;
  border-radius:12px;
  padding:24px;
  max-width:900px;
  margin:0 auto;
}

/* ── Typography ── */
#ht-app h2{font-size:1.35rem;font-weight:700;color:#f1f5f9;margin-bottom:16px}
#ht-app h3{font-size:1.05rem;font-weight:600;color:#cbd5e1;margin-bottom:10px}

/* ── Tabs ── */
#ht-app .ht-tabs{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:24px;border-bottom:1px solid #1e293b;padding-bottom:12px}
#ht-app .ht-tab{
  padding:7px 16px;border-radius:8px;border:none;cursor:pointer;
  font-size:0.875rem;font-weight:600;
  background:#1e293b;color:#94a3b8;
  transition:background 0.15s,color 0.15s;
}
#ht-app .ht-tab:hover{background:#334155;color:#e2e8f0}
#ht-app .ht-tab.active{background:#6366f1;color:#fff}

/* ── Panels ── */
#ht-app .ht-panel{display:none}
#ht-app .ht-panel.active{display:block}

/* ── Add-habit form ── */
#ht-app .ht-form{background:#1e293b;border-radius:10px;padding:20px;margin-bottom:24px}
#ht-app .ht-form-row{display:flex;flex-wrap:wrap;gap:12px;align-items:flex-end}
#ht-app .ht-field{display:flex;flex-direction:column;gap:5px;flex:1;min-width:140px}
#ht-app .ht-field label{font-size:0.78rem;font-weight:600;color:#94a3b8;text-transform:uppercase;letter-spacing:.04em}
#ht-app .ht-field input[type=text],
#ht-app .ht-field select{
  background:#0f172a;border:1px solid #334155;border-radius:7px;
  color:#e2e8f0;padding:8px 10px;font-size:0.9rem;outline:none;
  transition:border-color 0.15s;
}
#ht-app .ht-field input[type=text]:focus,
#ht-app .ht-field select:focus{border-color:#6366f1}
#ht-app .ht-field input[type=color]{
  width:44px;height:36px;padding:2px;border-radius:7px;
  border:1px solid #334155;background:#0f172a;cursor:pointer;
}
#ht-app .ht-days-picker{display:flex;gap:6px;flex-wrap:wrap;margin-top:6px}
#ht-app .ht-day-btn{
  width:34px;height:34px;border-radius:50%;border:1px solid #334155;
  background:#0f172a;color:#94a3b8;font-size:0.78rem;font-weight:600;
  cursor:pointer;transition:all 0.15s;
}
#ht-app .ht-day-btn.sel{background:#6366f1;border-color:#6366f1;color:#fff}
#ht-app .ht-btn{
  padding:8px 20px;border-radius:8px;border:none;cursor:pointer;
  font-size:0.9rem;font-weight:600;transition:opacity 0.15s;
}
#ht-app .ht-btn:hover{opacity:0.85}
#ht-app .ht-btn-primary{background:#6366f1;color:#fff}
#ht-app .ht-btn-sm{padding:5px 12px;font-size:0.8rem;border-radius:6px}
#ht-app .ht-btn-danger{background:#ef4444;color:#fff}
#ht-app .ht-btn-outline{background:transparent;border:1px solid #334155;color:#94a3b8}
#ht-app .ht-btn-outline:hover{border-color:#6366f1;color:#e2e8f0}
#ht-app .ht-btn-success{background:#22c55e;color:#fff}

/* ── Today view ── */
#ht-app .ht-today-list{display:flex;flex-direction:column;gap:10px}
#ht-app .ht-today-item{
  display:flex;align-items:center;gap:14px;
  background:#1e293b;border-radius:10px;padding:14px 16px;
  transition:background 0.15s;
}
#ht-app .ht-today-item.done{background:#1a2e1a}
#ht-app .ht-today-item .ht-check{
  width:26px;height:26px;border-radius:50%;border:2px solid #475569;
  background:transparent;cursor:pointer;flex-shrink:0;
  display:flex;align-items:center;justify-content:center;
  transition:all 0.15s;
}
#ht-app .ht-today-item.done .ht-check{background:#22c55e;border-color:#22c55e}
#ht-app .ht-today-item .ht-check svg{display:none}
#ht-app .ht-today-item.done .ht-check svg{display:block}
#ht-app .ht-habit-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}
#ht-app .ht-today-name{flex:1;font-weight:600;color:#e2e8f0}
#ht-app .ht-today-item.done .ht-today-name{text-decoration:line-through;color:#64748b}
#ht-app .ht-streak-badge{
  font-size:0.78rem;font-weight:700;padding:3px 9px;border-radius:99px;
  background:#1e3a5f;color:#60a5fa;white-space:nowrap;
}
#ht-app .ht-skip-badge{font-size:0.75rem;color:#64748b;margin-left:auto}
#ht-app .ht-today-actions{display:flex;gap:6px;margin-left:auto}

/* ── Weekly grid ── */
#ht-app .ht-week-table{width:100%;border-collapse:collapse;margin-bottom:20px}
#ht-app .ht-week-table th{
  font-size:0.75rem;font-weight:600;color:#64748b;
  text-align:center;padding:4px 2px;text-transform:uppercase;letter-spacing:.04em;
}
#ht-app .ht-week-table td{padding:4px 3px;vertical-align:middle}
#ht-app .ht-week-table .ht-habit-label{
  font-size:0.85rem;font-weight:600;color:#cbd5e1;
  padding-right:12px;white-space:nowrap;max-width:120px;overflow:hidden;text-overflow:ellipsis;
}
#ht-app .ht-week-cell{
  width:36px;height:36px;border-radius:6px;border:none;cursor:pointer;
  display:inline-flex;align-items:center;justify-content:center;
  font-size:0.7rem;font-weight:700;
  transition:transform 0.1s;
}
#ht-app .ht-week-cell:hover{transform:scale(1.1)}
#ht-app .ht-week-cell.future{opacity:0.25;cursor:default}
#ht-app .ht-week-cell.skipped{opacity:0.15;cursor:default}

/* ── Heatmap ── */
#ht-app .ht-heatmap-wrap{overflow-x:auto;padding-bottom:8px}
#ht-app .ht-heatmap-grid{
  display:grid;grid-template-rows:repeat(7,14px);grid-auto-flow:column;
  gap:3px;width:max-content;
}
#ht-app .ht-heatmap-cell{
  width:14px;height:14px;border-radius:3px;
  background:#1e293b;cursor:default;
  transition:transform 0.1s;
}
#ht-app .ht-heatmap-cell:hover{transform:scale(1.3)}
#ht-app .ht-heatmap-label{display:flex;gap:3px;align-items:center;margin-bottom:8px;font-size:0.75rem;color:#64748b;flex-wrap:wrap}
#ht-app .ht-heatmap-swatch{width:14px;height:14px;border-radius:3px}
#ht-app .ht-heatmap-months{
  display:flex;gap:0;width:max-content;margin-bottom:4px;
  font-size:0.7rem;color:#64748b;
}
#ht-app .ht-heatmap-month-label{text-align:left;padding-right:4px}
#ht-app .ht-heatmap-select{margin-bottom:14px}

/* ── Stats ── */
#ht-app .ht-stats-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:14px}
#ht-app .ht-stat-card{background:#1e293b;border-radius:10px;padding:16px}
#ht-app .ht-stat-card .ht-stat-name{
  font-size:0.88rem;font-weight:700;color:#e2e8f0;margin-bottom:12px;
  display:flex;align-items:center;gap:8px;
}
#ht-app .ht-stat-row{display:flex;justify-content:space-between;margin-bottom:6px;font-size:0.82rem}
#ht-app .ht-stat-label{color:#64748b}
#ht-app .ht-stat-val{color:#e2e8f0;font-weight:700}
#ht-app .ht-progress-bar{height:6px;border-radius:3px;background:#334155;margin-top:10px;overflow:hidden}
#ht-app .ht-progress-fill{height:100%;border-radius:3px;transition:width 0.4s}

/* ── Edit modal ── */
#ht-app .ht-modal-bg{
  display:none;position:fixed;inset:0;background:rgba(0,0,0,0.65);
  z-index:1000;align-items:center;justify-content:center;
}
#ht-app .ht-modal-bg.open{display:flex}
#ht-app .ht-modal{
  background:#1e293b;border-radius:12px;padding:24px;
  width:min(480px,92vw);max-height:90vh;overflow-y:auto;
}
#ht-app .ht-modal h3{margin-bottom:16px;color:#f1f5f9}
#ht-app .ht-modal-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:16px;flex-wrap:wrap}

/* ── Import/Export ── */
#ht-app .ht-io-row{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:16px}
#ht-app .ht-import-area{
  width:100%;background:#0f172a;border:1px solid #334155;border-radius:8px;
  color:#e2e8f0;padding:10px;font-size:0.82rem;resize:vertical;min-height:80px;
}

/* ── Empty state ── */
#ht-app .ht-empty{
  text-align:center;padding:40px 20px;color:#475569;
  font-size:0.95rem;
}
#ht-app .ht-empty span{font-size:2.5rem;display:block;margin-bottom:10px}

/* ── Tooltip ── */
#ht-tooltip{
  position:fixed;background:#0f172a;color:#e2e8f0;
  font-size:0.75rem;padding:5px 10px;border-radius:6px;
  pointer-events:none;z-index:9999;display:none;
  border:1px solid #334155;white-space:nowrap;
}

/* ── Responsive ── */
@media(max-width:600px){
  #ht-app{padding:14px}
  #ht-app .ht-week-table .ht-habit-label{max-width:70px}
  #ht-app .ht-week-cell{width:28px;height:28px}
}
</style>

<!-- Tooltip -->
<div id="ht-tooltip"></div>

<!-- Tabs -->
<div class="ht-tabs">
  <button class="ht-tab active" data-tab="today">Today</button>
  <button class="ht-tab" data-tab="week">Weekly Grid</button>
  <button class="ht-tab" data-tab="heatmap">Heatmap</button>
  <button class="ht-tab" data-tab="stats">Stats</button>
  <button class="ht-tab" data-tab="manage">Manage</button>
</div>

<!-- TODAY PANEL -->
<div class="ht-panel active" id="ht-panel-today">
  <h2 id="ht-today-heading"></h2>
  <div class="ht-today-list" id="ht-today-list"></div>
</div>

<!-- WEEKLY GRID PANEL -->
<div class="ht-panel" id="ht-panel-week">
  <h2>Weekly Grid</h2>
  <div style="overflow-x:auto"><table class="ht-week-table" id="ht-week-table"></table></div>
</div>

<!-- HEATMAP PANEL -->
<div class="ht-panel" id="ht-panel-heatmap">
  <h2>Monthly Heatmap</h2>
  <div class="ht-heatmap-select">
    <select id="ht-heatmap-habit-sel" class="ht-field" style="background:#1e293b;border:1px solid #334155;border-radius:7px;color:#e2e8f0;padding:7px 10px;font-size:0.88rem"></select>
  </div>
  <div class="ht-heatmap-label" id="ht-heatmap-legend"></div>
  <div class="ht-heatmap-months" id="ht-heatmap-months"></div>
  <div class="ht-heatmap-wrap"><div class="ht-heatmap-grid" id="ht-heatmap-grid"></div></div>
</div>

<!-- STATS PANEL -->
<div class="ht-panel" id="ht-panel-stats">
  <h2>Stats</h2>
  <div class="ht-stats-grid" id="ht-stats-grid"></div>
</div>

<!-- MANAGE PANEL -->
<div class="ht-panel" id="ht-panel-manage">
  <h2>Add New Habit</h2>
  <div class="ht-form">
    <div class="ht-form-row">
      <div class="ht-field" style="flex:2">
        <label>Habit name</label>
        <input type="text" id="ht-new-name" placeholder="e.g. Morning run" maxlength="40">
      </div>
      <div class="ht-field" style="flex:0 0 auto">
        <label>Color</label>
        <input type="color" id="ht-new-color" value="#6366f1">
      </div>
      <div class="ht-field" style="flex:1;min-width:140px">
        <label>Frequency</label>
        <select id="ht-new-freq">
          <option value="daily">Daily</option>
          <option value="weekdays">Weekdays</option>
          <option value="custom">Custom days</option>
        </select>
      </div>
    </div>
    <div id="ht-custom-days-wrap" style="display:none;margin-top:14px">
      <label style="font-size:0.78rem;font-weight:600;color:#94a3b8;text-transform:uppercase;letter-spacing:.04em;display:block;margin-bottom:6px">Select days</label>
      <div class="ht-days-picker" id="ht-new-days">
        <button class="ht-day-btn" data-d="0">Su</button>
        <button class="ht-day-btn sel" data-d="1">Mo</button>
        <button class="ht-day-btn sel" data-d="2">Tu</button>
        <button class="ht-day-btn sel" data-d="3">We</button>
        <button class="ht-day-btn sel" data-d="4">Th</button>
        <button class="ht-day-btn sel" data-d="5">Fr</button>
        <button class="ht-day-btn" data-d="6">Sa</button>
      </div>
    </div>
    <div style="margin-top:14px">
      <button class="ht-btn ht-btn-primary" id="ht-add-btn">Add Habit</button>
    </div>
  </div>

  <h2>My Habits</h2>
  <div id="ht-manage-list"></div>

  <h2 style="margin-top:28px">Data</h2>
  <div class="ht-io-row">
    <button class="ht-btn ht-btn-outline ht-btn-sm" id="ht-export-btn">Export JSON</button>
    <button class="ht-btn ht-btn-outline ht-btn-sm" id="ht-import-show-btn">Import JSON</button>
  </div>
  <div id="ht-import-area-wrap" style="display:none">
    <textarea class="ht-import-area" id="ht-import-area" placeholder="Paste exported JSON here..."></textarea>
    <div style="margin-top:8px;display:flex;gap:8px">
      <button class="ht-btn ht-btn-success ht-btn-sm" id="ht-import-btn">Import</button>
      <button class="ht-btn ht-btn-outline ht-btn-sm" id="ht-import-cancel-btn">Cancel</button>
    </div>
  </div>
</div>

<!-- Edit Modal -->
<div class="ht-modal-bg" id="ht-modal">
  <div class="ht-modal">
    <h3>Edit Habit</h3>
    <input type="hidden" id="ht-edit-id">
    <div class="ht-form-row" style="margin-bottom:12px">
      <div class="ht-field" style="flex:2">
        <label>Habit name</label>
        <input type="text" id="ht-edit-name" maxlength="40">
      </div>
      <div class="ht-field" style="flex:0 0 auto">
        <label>Color</label>
        <input type="color" id="ht-edit-color">
      </div>
    </div>
    <div class="ht-field" style="margin-bottom:12px">
      <label>Frequency</label>
      <select id="ht-edit-freq">
        <option value="daily">Daily</option>
        <option value="weekdays">Weekdays</option>
        <option value="custom">Custom days</option>
      </select>
    </div>
    <div id="ht-edit-days-wrap" style="display:none">
      <label style="font-size:0.78rem;font-weight:600;color:#94a3b8;text-transform:uppercase;letter-spacing:.04em;display:block;margin-bottom:6px">Select days</label>
      <div class="ht-days-picker" id="ht-edit-days">
        <button class="ht-day-btn" data-d="0">Su</button>
        <button class="ht-day-btn" data-d="1">Mo</button>
        <button class="ht-day-btn" data-d="2">Tu</button>
        <button class="ht-day-btn" data-d="3">We</button>
        <button class="ht-day-btn" data-d="4">Th</button>
        <button class="ht-day-btn" data-d="5">Fr</button>
        <button class="ht-day-btn" data-d="6">Sa</button>
      </div>
    </div>
    <div class="ht-modal-actions">
      <button class="ht-btn ht-btn-danger ht-btn-sm" id="ht-delete-btn">Delete</button>
      <button class="ht-btn ht-btn-outline ht-btn-sm" id="ht-edit-cancel-btn">Cancel</button>
      <button class="ht-btn ht-btn-primary ht-btn-sm" id="ht-edit-save-btn">Save</button>
    </div>
  </div>
</div>

<script>
(function(){
'use strict';

/* ── Utilities ── */
const $ = id => document.getElementById(id);
const qs = (sel,ctx) => (ctx||document).querySelector(sel);
const qsa = (sel,ctx) => [...(ctx||document).querySelectorAll(sel)];

function todayStr(){
  const d=new Date();
  return `${d.getFullYear()}-${p(d.getMonth()+1)}-${p(d.getDate())}`;
}
function p(n){return String(n).padStart(2,'0')}

function dateStr(d){
  return `${d.getFullYear()}-${p(d.getMonth()+1)}-${p(d.getDate())}`;
}

function parseDate(s){
  const [y,m,d]=s.split('-').map(Number);
  return new Date(y,m-1,d);
}

function uuid(){
  return Math.random().toString(36).slice(2)+Date.now().toString(36);
}

function hexToRgb(hex){
  const r=parseInt(hex.slice(1,3),16),g=parseInt(hex.slice(3,5),16),b=parseInt(hex.slice(5,7),16);
  return{r,g,b};
}

function colorWithAlpha(hex,a){
  const{r,g,b}=hexToRgb(hex);
  return`rgba(${r},${g},${b},${a})`;
}

/* ── Data model ── */
// habit: {id, name, color, freq:'daily'|'weekdays'|'custom', days:[0-6], createdAt:'YYYY-MM-DD'}
// log: {[habitId]: Set<'YYYY-MM-DD'>}  — stored as arrays in localStorage

const STORAGE_KEY='ht_data_v2';

function loadData(){
  try{
    const raw=localStorage.getItem(STORAGE_KEY);
    if(!raw)return{habits:[],log:{}};
    const d=JSON.parse(raw);
    // convert log arrays to Sets
    const log={};
    for(const k in d.log) log[k]=new Set(d.log[k]);
    return{habits:d.habits||[],log};
  }catch(e){return{habits:[],log:{}};}
}

function saveData(){
  const log={};
  for(const k in state.log) log[k]=[...state.log[k]];
  localStorage.setItem(STORAGE_KEY,JSON.stringify({habits:state.habits,log}));
}

const state=loadData();

/* ── Frequency helpers ── */
function freqLabel(h){
  if(h.freq==='daily')return'Daily';
  if(h.freq==='weekdays')return'Weekdays';
  const names=['Su','Mo','Tu','We','Th','Fr','Sa'];
  return(h.days||[]).map(d=>names[d]).join(', ')||'Custom';
}

function isScheduled(habit,dateStr){
  const d=parseDate(dateStr);
  const dow=d.getDay(); // 0=Sun
  if(habit.freq==='daily')return true;
  if(habit.freq==='weekdays')return dow>=1&&dow<=5;
  if(habit.freq==='custom')return(habit.days||[]).includes(dow);
  return true;
}

function isDone(habit,ds){
  return !!(state.log[habit.id]&&state.log[habit.id].has(ds));
}

function toggle(habit,ds){
  if(!state.log[habit.id])state.log[habit.id]=new Set();
  if(state.log[habit.id].has(ds)) state.log[habit.id].delete(ds);
  else state.log[habit.id].add(ds);
  saveData();
}

/* ── Streak calculation ── */
function getStreak(habit){
  if(!state.log[habit.id])return{cur:0,best:0};
  // Walk backwards from today
  let cur=0,best=0,streak=0;
  const today=new Date();
  // find the last 365 days
  let d=new Date(today);
  // current streak: consecutive scheduled days up to today that are done
  // start from today, go back
  let checkD=new Date(today);
  // if today is not done yet, streak starts from yesterday
  const todS=dateStr(today);
  let started=false;
  for(let i=0;i<730;i++){
    const ds=dateStr(checkD);
    if(isScheduled(habit,ds)){
      if(isDone(habit,ds)){
        streak++;
        if(!started)started=true;
      }else{
        // if today and not done yet, skip only once
        if(ds===todS&&i===0){
          checkD.setDate(checkD.getDate()-1);
          continue;
        }
        break;
      }
    }
    checkD.setDate(checkD.getDate()-1);
  }
  cur=streak;

  // best streak: walk all log entries
  // gather all dates with entries, sorted
  const allDates=[...state.log[habit.id]].sort();
  if(allDates.length===0)return{cur:0,best:0};
  let b=0,run=0;
  let prev=null;
  for(const ds of allDates){
    if(!isScheduled(habit,ds))continue;
    if(!prev){run=1;}
    else{
      // check if prev and ds are consecutive scheduled days
      const prevD=parseDate(prev);
      const curD=parseDate(ds);
      // step through from prev to cur
      let tempD=new Date(prevD);
      tempD.setDate(tempD.getDate()+1);
      let gap=false;
      while(dateStr(tempD)<ds){
        if(isScheduled(habit,dateStr(tempD))){gap=true;break;}
        tempD.setDate(tempD.getDate()+1);
      }
      if(!gap)run++;
      else run=1;
    }
    prev=ds;
    if(run>b)b=run;
  }
  best=Math.max(b,cur);
  return{cur,best};
}

function getCompletionRate(habit,days=30){
  let scheduled=0,done=0;
  const today=new Date();
  for(let i=0;i<days;i++){
    const d=new Date(today);
    d.setDate(d.getDate()-i);
    const ds=dateStr(d);
    if(parseDate(ds)<parseDate(habit.createdAt))break;
    if(isScheduled(habit,ds)){
      scheduled++;
      if(isDone(habit,ds))done++;
    }
  }
  return scheduled===0?0:Math.round(done/scheduled*100);
}

/* ── Tab switching ── */
qsa('.ht-tab').forEach(btn=>{
  btn.addEventListener('click',()=>{
    qsa('.ht-tab').forEach(t=>t.classList.remove('active'));
    qsa('.ht-panel').forEach(p=>p.classList.remove('active'));
    btn.classList.add('active');
    $('ht-panel-'+btn.dataset.tab).classList.add('active');
    renderTab(btn.dataset.tab);
  });
});

function renderTab(tab){
  if(tab==='today')renderToday();
  else if(tab==='week')renderWeek();
  else if(tab==='heatmap')renderHeatmap();
  else if(tab==='stats')renderStats();
  else if(tab==='manage')renderManage();
}

/* ── TODAY ── */
function renderToday(){
  const today=new Date();
  const ds=dateStr(today);
  const days=['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
  const months=['January','February','March','April','May','June','July','August','September','October','November','December'];
  $('ht-today-heading').textContent=`${days[today.getDay()]}, ${months[today.getMonth()]} ${today.getDate()}`;
  const list=$('ht-today-list');
  list.innerHTML='';
  const scheduled=state.habits.filter(h=>isScheduled(h,ds));
  if(scheduled.length===0){
    list.innerHTML='<div class="ht-empty"><span>&#127774;</span>No habits scheduled for today.<br>Add habits in the Manage tab.</div>';
    return;
  }
  scheduled.forEach(h=>{
    const done=isDone(h,ds);
    const {cur}=getStreak(h);
    const item=document.createElement('div');
    item.className='ht-today-item'+(done?' done':'');
    item.innerHTML=`
      <button class="ht-check" title="${done?'Mark undone':'Mark done'}">
        <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
          <path d="M2 7l4 4 6-7" stroke="#fff" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
      <span class="ht-habit-dot" style="background:${h.color}"></span>
      <span class="ht-today-name">${esc(h.name)}</span>
      ${cur>1?`<span class="ht-streak-badge">&#128293; ${cur} day streak</span>`:''}
    `;
    item.querySelector('.ht-check').addEventListener('click',()=>{
      toggle(h,ds);renderToday();
    });
    list.appendChild(item);
  });
}

/* ── WEEKLY GRID ── */
function renderWeek(){
  const table=$('ht-week-table');
  const today=new Date();
  // Get the last 7 days (Mon-based display: today + 6 days back)
  const days=[];
  for(let i=6;i>=0;i--){
    const d=new Date(today);
    d.setDate(d.getDate()-i);
    days.push(d);
  }
  const dayNames=['Su','Mo','Tu','We','Th','Fr','Sa'];
  let html='<thead><tr><th style="text-align:left;min-width:100px">Habit</th>';
  days.forEach(d=>{
    const isToday=dateStr(d)===dateStr(today);
    html+=`<th style="${isToday?'color:#818cf8':''}">${dayNames[d.getDay()]}<br><span style="font-size:0.7rem;font-weight:400">${p(d.getMonth()+1)}/${p(d.getDate())}</span></th>`;
  });
  html+='</tr></thead><tbody>';

  if(state.habits.length===0){
    html+='<tr><td colspan="8" class="ht-empty" style="text-align:center;padding:30px;color:#475569">No habits yet. Add some in Manage tab.</td></tr>';
  }

  state.habits.forEach(h=>{
    html+=`<tr><td class="ht-habit-label"><span style="display:inline-block;width:8px;height:8px;border-radius:50%;background:${h.color};margin-right:6px"></span>${esc(h.name)}</td>`;
    days.forEach(d=>{
      const ds=dateStr(d);
      const future=d>today&&ds!==dateStr(today);
      const sched=isScheduled(h,ds);
      const done=isDone(h,ds);
      let bg,title;
      if(!sched){
        bg='#1e293b';title='Not scheduled';
      }else if(done){
        bg=h.color;title='Completed';
      }else if(future){
        bg='#1e293b';title='Upcoming';
      }else{
        bg='#334155';title='Not done';
      }
      html+=`<td style="text-align:center">
        <button class="ht-week-cell${!sched||future?' skipped':''}"
          style="background:${bg};color:${done?'#fff':'#64748b'}"
          data-hid="${h.id}" data-ds="${ds}"
          data-sched="${sched}" data-future="${future}"
          title="${title} — ${ds}">
          ${done?'&#10003;':sched&&!future?'&ndash;':''}
        </button>
      </td>`;
    });
    html+='</tr>';
  });
  html+='</tbody>';
  table.innerHTML=html;

  // toggle on cell click
  qsa('.ht-week-cell',table).forEach(btn=>{
    if(btn.dataset.sched==='false'||btn.dataset.future==='true')return;
    btn.addEventListener('click',()=>{
      const h=state.habits.find(x=>x.id===btn.dataset.hid);
      if(h){toggle(h,btn.dataset.ds);renderWeek();}
    });
  });
}

/* ── HEATMAP ── */
function renderHeatmap(){
  const sel=$('ht-heatmap-habit-sel');
  sel.innerHTML='';
  if(state.habits.length===0){
    $('ht-heatmap-grid').innerHTML='<div class="ht-empty" style="padding:30px;color:#475569">No habits yet.</div>';
    return;
  }
  state.habits.forEach(h=>{
    const o=document.createElement('option');
    o.value=h.id;o.textContent=h.name;
    sel.appendChild(o);
  });
  sel.onchange=()=>drawHeatmap(sel.value);
  drawHeatmap(sel.value);
}

function drawHeatmap(hid){
  const h=state.habits.find(x=>x.id===hid);
  if(!h)return;
  const grid=$('ht-heatmap-grid');
  const monthsEl=$('ht-heatmap-months');
  const legendEl=$('ht-heatmap-legend');
  grid.innerHTML='';monthsEl.innerHTML='';legendEl.innerHTML='';

  // Show 52 weeks (364 days) + partial week
  const today=new Date();
  // Start from the Sunday 52 weeks ago
  const startD=new Date(today);
  startD.setDate(startD.getDate()-363);
  // rewind to nearest Sunday
  startD.setDate(startD.getDate()-startD.getDay());

  const totalDays=Math.ceil((today-startD)/(86400000))+1;
  const weeks=Math.ceil(totalDays/7);

  // Build grid: rows=7(dow), cols=weeks
  const cells=[];
  let monthTrack={};
  let colIdx=0;
  let d=new Date(startD);

  for(let w=0;w<weeks;w++){
    for(let dow=0;dow<7;dow++){
      const ds=dateStr(d);
      const future=d>today;
      const sched=isScheduled(h,ds);
      const done=isDone(h,ds);
      const monthKey=`${d.getFullYear()}-${d.getMonth()}`;
      if(!monthTrack[monthKey])monthTrack[monthKey]={col:w,label:['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'][d.getMonth()]};
      cells.push({ds,done,sched,future,d:new Date(d)});
      d.setDate(d.getDate()+1);
    }
    colIdx++;
  }

  // Render cells
  cells.forEach(c=>{
    const el=document.createElement('div');
    el.className='ht-heatmap-cell';
    let bg='#1e293b';
    if(!c.future){
      if(c.done) bg=h.color;
      else if(c.sched) bg=colorWithAlpha(h.color,0.15);
    }
    el.style.background=bg;
    el.title=`${c.ds}${c.done?' ✓':c.sched&&!c.future?' ○':''}`;
    // tooltip
    el.addEventListener('mouseenter',e=>{
      showTooltip(e,c.ds+(c.done?' — Done':c.sched&&!c.future?' — Not done':' — Not scheduled'));
    });
    el.addEventListener('mouseleave',hideTooltip);
    grid.appendChild(el);
  });

  // Month labels
  const colWidth=14+3; // cell+gap
  Object.values(monthTrack).forEach(m=>{
    const span=document.createElement('span');
    span.className='ht-heatmap-month-label';
    span.textContent=m.label;
    span.style.width=(colWidth)+'px';
    monthsEl.appendChild(span);
  });

  // Legend
  legendEl.innerHTML=`
    <span style="margin-right:6px">Less</span>
    <span class="ht-heatmap-swatch" style="background:#1e293b"></span>
    <span class="ht-heatmap-swatch" style="background:${colorWithAlpha(h.color,0.15)}"></span>
    <span class="ht-heatmap-swatch" style="background:${colorWithAlpha(h.color,0.5)}"></span>
    <span class="ht-heatmap-swatch" style="background:${h.color}"></span>
    <span style="margin-left:6px">More</span>
    <span style="margin-left:16px;color:#64748b">&#9679; = scheduled but missed</span>
  `;
}

/* ── STATS ── */
function renderStats(){
  const grid=$('ht-stats-grid');
  grid.innerHTML='';
  if(state.habits.length===0){
    grid.innerHTML='<div class="ht-empty"><span>&#128202;</span>No habits to show stats for yet.</div>';
    return;
  }
  state.habits.forEach(h=>{
    const {cur,best}=getStreak(h);
    const rate30=getCompletionRate(h,30);
    const rate7=getCompletionRate(h,7);
    const totalDone=state.log[h.id]?state.log[h.id].size:0;
    const card=document.createElement('div');
    card.className='ht-stat-card';
    card.innerHTML=`
      <div class="ht-stat-name">
        <span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:${h.color};flex-shrink:0"></span>
        ${esc(h.name)}
        <span style="font-size:0.72rem;color:#64748b;margin-left:auto">${freqLabel(h)}</span>
      </div>
      <div class="ht-stat-row"><span class="ht-stat-label">Current streak</span><span class="ht-stat-val">&#128293; ${cur} day${cur!==1?'s':''}</span></div>
      <div class="ht-stat-row"><span class="ht-stat-label">Longest streak</span><span class="ht-stat-val">&#127942; ${best} day${best!==1?'s':''}</span></div>
      <div class="ht-stat-row"><span class="ht-stat-label">Last 7 days</span><span class="ht-stat-val">${rate7}%</span></div>
      <div class="ht-stat-row"><span class="ht-stat-label">Last 30 days</span><span class="ht-stat-val">${rate30}%</span></div>
      <div class="ht-stat-row"><span class="ht-stat-label">Total completions</span><span class="ht-stat-val">${totalDone}</span></div>
      <div class="ht-progress-bar"><div class="ht-progress-fill" style="width:${rate30}%;background:${h.color}"></div></div>
    `;
    grid.appendChild(card);
  });
}

/* ── MANAGE ── */
function renderManage(){
  const list=$('ht-manage-list');
  list.innerHTML='';
  if(state.habits.length===0){
    list.innerHTML='<div class="ht-empty"><span>&#128221;</span>No habits yet. Add one above!</div>';
    return;
  }
  state.habits.forEach((h,idx)=>{
    const row=document.createElement('div');
    row.style.cssText='display:flex;align-items:center;gap:12px;background:#1e293b;border-radius:10px;padding:12px 16px;margin-bottom:10px;flex-wrap:wrap';
    row.innerHTML=`
      <span style="display:inline-block;width:12px;height:12px;border-radius:50%;background:${h.color};flex-shrink:0"></span>
      <span style="flex:1;font-weight:600;color:#e2e8f0;min-width:100px">${esc(h.name)}</span>
      <span style="font-size:0.78rem;color:#64748b">${freqLabel(h)}</span>
      <span style="font-size:0.75rem;color:#475569">Since ${h.createdAt}</span>
      <div style="display:flex;gap:6px;margin-left:auto">
        <button class="ht-btn ht-btn-outline ht-btn-sm ht-edit-btn" data-idx="${idx}">Edit</button>
      </div>
    `;
    list.appendChild(row);
  });

  qsa('.ht-edit-btn',list).forEach(btn=>{
    btn.addEventListener('click',()=>openEditModal(parseInt(btn.dataset.idx)));
  });
}

/* ── ADD HABIT ── */
const freqSel=$('ht-new-freq');
const customWrap=$('ht-custom-days-wrap');
freqSel.addEventListener('change',()=>{
  customWrap.style.display=freqSel.value==='custom'?'block':'none';
});

qsa('.ht-day-btn',$('ht-new-days')).forEach(btn=>{
  btn.addEventListener('click',()=>btn.classList.toggle('sel'));
});

$('ht-add-btn').addEventListener('click',()=>{
  const name=$('ht-new-name').value.trim();
  if(!name){$('ht-new-name').focus();return;}
  const color=$('ht-new-color').value;
  const freq=freqSel.value;
  const days=freq==='custom'
    ? qsa('.ht-day-btn.sel',$('ht-new-days')).map(b=>parseInt(b.dataset.d))
    : freq==='weekdays'?[1,2,3,4,5]:[0,1,2,3,4,5,6];
  state.habits.push({id:uuid(),name,color,freq,days,createdAt:todayStr()});
  saveData();
  $('ht-new-name').value='';
  renderManage();
  renderToday();
});

/* ── EDIT MODAL ── */
let editIdx=-1;

function openEditModal(idx){
  editIdx=idx;
  const h=state.habits[idx];
  $('ht-edit-id').value=h.id;
  $('ht-edit-name').value=h.name;
  $('ht-edit-color').value=h.color;
  $('ht-edit-freq').value=h.freq;
  syncEditDays(h);
  $('ht-edit-days-wrap').style.display=h.freq==='custom'?'block':'none';
  $('ht-modal').classList.add('open');
}

function syncEditDays(h){
  qsa('.ht-day-btn',$('ht-edit-days')).forEach(btn=>{
    const d=parseInt(btn.dataset.d);
    btn.classList.toggle('sel',(h.days||[]).includes(d));
  });
}

$('ht-edit-freq').addEventListener('change',()=>{
  $('ht-edit-days-wrap').style.display=$('ht-edit-freq').value==='custom'?'block':'none';
});

qsa('.ht-day-btn',$('ht-edit-days')).forEach(btn=>{
  btn.addEventListener('click',()=>btn.classList.toggle('sel'));
});

$('ht-edit-cancel-btn').addEventListener('click',()=>$('ht-modal').classList.remove('open'));
$('ht-modal').addEventListener('click',e=>{if(e.target===$('ht-modal'))$('ht-modal').classList.remove('open');});

$('ht-edit-save-btn').addEventListener('click',()=>{
  const name=$('ht-edit-name').value.trim();
  if(!name)return;
  const h=state.habits[editIdx];
  h.name=name;
  h.color=$('ht-edit-color').value;
  h.freq=$('ht-edit-freq').value;
  h.days=h.freq==='custom'
    ? qsa('.ht-day-btn.sel',$('ht-edit-days')).map(b=>parseInt(b.dataset.d))
    : h.freq==='weekdays'?[1,2,3,4,5]:[0,1,2,3,4,5,6];
  saveData();
  $('ht-modal').classList.remove('open');
  renderManage();renderToday();
});

$('ht-delete-btn').addEventListener('click',()=>{
  if(!confirm('Delete this habit and all its data? This cannot be undone.'))return;
  const h=state.habits[editIdx];
  delete state.log[h.id];
  state.habits.splice(editIdx,1);
  saveData();
  $('ht-modal').classList.remove('open');
  renderManage();renderToday();
});

/* ── EXPORT / IMPORT ── */
$('ht-export-btn').addEventListener('click',()=>{
  const log={};
  for(const k in state.log) log[k]=[...state.log[k]];
  const data=JSON.stringify({habits:state.habits,log},null,2);
  const blob=new Blob([data],{type:'application/json'});
  const url=URL.createObjectURL(blob);
  const a=document.createElement('a');
  a.href=url;a.download='habit-tracker-data.json';
  a.click();URL.revokeObjectURL(url);
});

$('ht-import-show-btn').addEventListener('click',()=>{
  $('ht-import-area-wrap').style.display='block';
  $('ht-import-area').focus();
});

$('ht-import-cancel-btn').addEventListener('click',()=>{
  $('ht-import-area-wrap').style.display='none';
  $('ht-import-area').value='';
});

$('ht-import-btn').addEventListener('click',()=>{
  try{
    const d=JSON.parse($('ht-import-area').value);
    if(!d.habits)throw new Error('Invalid format');
    state.habits=d.habits;
    state.log={};
    for(const k in d.log) state.log[k]=new Set(d.log[k]);
    saveData();
    $('ht-import-area-wrap').style.display='none';
    $('ht-import-area').value='';
    renderManage();renderToday();
    alert('Data imported successfully!');
  }catch(e){alert('Import failed: '+e.message);}
});

/* ── Tooltip ── */
const tooltip=document.getElementById('ht-tooltip');
function showTooltip(e,text){
  tooltip.textContent=text;
  tooltip.style.display='block';
  moveTooltip(e);
}
function moveTooltip(e){
  tooltip.style.left=(e.clientX+12)+'px';
  tooltip.style.top=(e.clientY-28)+'px';
}
function hideTooltip(){tooltip.style.display='none';}
document.addEventListener('mousemove',e=>{if(tooltip.style.display==='block')moveTooltip(e);});

/* ── Escape helper ── */
function esc(s){
  return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

/* ── Seed demo habits if empty ── */
if(state.habits.length===0){
  const demos=[
    {id:uuid(),name:'Morning run',color:'#22c55e',freq:'daily',days:[0,1,2,3,4,5,6],createdAt:todayStr()},
    {id:uuid(),name:'Read 20 pages',color:'#6366f1',freq:'daily',days:[0,1,2,3,4,5,6],createdAt:todayStr()},
    {id:uuid(),name:'No social media',color:'#f59e0b',freq:'weekdays',days:[1,2,3,4,5],createdAt:todayStr()},
  ];
  state.habits.push(...demos);
  // seed some past completions for demo
  const today=new Date();
  demos.forEach((h,hi)=>{
    state.log[h.id]=new Set();
    for(let i=1;i<=20+hi*5;i++){
      if(Math.random()>0.25){
        const d=new Date(today);d.setDate(d.getDate()-i);
        if(isScheduled(h,dateStr(d))) state.log[h.id].add(dateStr(d));
      }
    }
  });
  saveData();
}

/* ── Initial render ── */
renderToday();
})();
</script>

---

> Focus with Pomodoro → [Pomodoro Timer](/tools/pomodoro-timer/)
> Study with flashcards → [Flashcard Maker](/tools/flashcard-maker/)
> Plan your budget → [50/30/20 Budget Calculator](/tools/budget-calculator/)
</div>
