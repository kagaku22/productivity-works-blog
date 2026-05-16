---
title: "カレンダー生成ツール"
date: 2025-05-16
description: "無料の印刷用カレンダー生成ツール。月別・年間カレンダーを作成、イベント追加、印刷対応。週の開始日選択可能。"
categories: ["無料ツール"]
slug: "calendar-generator"
ShowToc: false
cover:
  image: "/images/covers/calendar-generator-ja.png"
  alt: "カレンダー生成ツール"
---

<div id="cg-app">
<style>
#cg-app *,#cg-app *::before,#cg-app *::after{box-sizing:border-box;margin:0;padding:0}
#cg-app{
  font-family:'Hiragino Sans','Noto Sans JP','Yu Gothic UI',sans-serif;
  font-size:15px;line-height:1.6;
  color:#1e293b;
  background:#f8fafc;
  border-radius:12px;
  padding:20px;
  max-width:980px;
  margin:0 auto;
}

/* ── ツールバー ── */
#cg-app .cg-toolbar{
  display:flex;flex-wrap:wrap;gap:10px;align-items:center;
  background:#fff;border:1px solid #e2e8f0;border-radius:10px;
  padding:14px 16px;margin-bottom:18px;
}
#cg-app .cg-toolbar label{font-size:13px;font-weight:600;color:#475569;margin-right:4px;}
#cg-app .cg-toolbar select,
#cg-app .cg-toolbar input[type=number]{
  border:1px solid #cbd5e1;border-radius:6px;padding:5px 8px;
  font-size:14px;color:#1e293b;background:#f8fafc;
  outline:none;cursor:pointer;
}
#cg-app .cg-toolbar select:focus,
#cg-app .cg-toolbar input[type=number]:focus{border-color:#3b82f6;}
#cg-app .cg-toolbar input[type=number]{width:76px;}
#cg-app .cg-btn{
  padding:7px 14px;border-radius:7px;border:none;cursor:pointer;
  font-size:13px;font-weight:600;transition:background 0.15s,transform 0.1s;
}
#cg-app .cg-btn:active{transform:scale(0.97);}
#cg-app .cg-btn-primary{background:#3b82f6;color:#fff;}
#cg-app .cg-btn-primary:hover{background:#2563eb;}
#cg-app .cg-btn-secondary{background:#e2e8f0;color:#334155;}
#cg-app .cg-btn-secondary:hover{background:#cbd5e1;}
#cg-app .cg-btn-print{background:#10b981;color:#fff;}
#cg-app .cg-btn-print:hover{background:#059669;}
#cg-app .cg-sep{width:1px;height:28px;background:#e2e8f0;margin:0 4px;}
#cg-app .cg-toolbar-group{display:flex;align-items:center;gap:6px;}

/* ── ナビ ── */
#cg-app .cg-nav{
  display:flex;align-items:center;justify-content:space-between;
  margin-bottom:14px;
}
#cg-app .cg-nav-title{
  font-size:20px;font-weight:700;color:#1e293b;
  letter-spacing:-0.3px;
}
#cg-app .cg-nav-btns{display:flex;gap:6px;}

/* ── 月カレンダー ── */
#cg-app .cg-calendar-wrap{background:#fff;border:1px solid #e2e8f0;border-radius:10px;overflow:hidden;}
#cg-app .cg-grid{
  display:grid;grid-template-columns:repeat(7,1fr);
}
#cg-app .cg-day-header{
  text-align:center;padding:10px 0;font-size:12px;font-weight:700;
  color:#64748b;letter-spacing:0.5px;
  background:#f1f5f9;border-bottom:1px solid #e2e8f0;
}
#cg-app .cg-cell{
  min-height:90px;border-right:1px solid #f1f5f9;border-bottom:1px solid #f1f5f9;
  padding:6px;position:relative;cursor:pointer;
  transition:background 0.1s;
}
#cg-app .cg-cell:hover{background:#f0f9ff;}
#cg-app .cg-cell.cg-other-month{background:#fafafa;opacity:0.6;}
#cg-app .cg-cell.cg-today{background:#eff6ff;}
#cg-app .cg-cell.cg-today .cg-date-num{
  background:#3b82f6;color:#fff;border-radius:50%;
  width:26px;height:26px;display:flex;align-items:center;justify-content:center;
  font-weight:700;
}
#cg-app .cg-cell.cg-has-event{background:#fefce8;}
#cg-app .cg-cell.cg-today.cg-has-event{background:#eff6ff;}
#cg-app .cg-date-num{
  font-size:13px;font-weight:600;color:#334155;
  width:26px;height:26px;display:flex;align-items:center;justify-content:center;
}
#cg-app .cg-cell.cg-sunday .cg-date-num{color:#ef4444;}
#cg-app .cg-cell.cg-saturday .cg-date-num{color:#3b82f6;}
#cg-app .cg-cell.cg-today .cg-date-num{color:#fff;}
#cg-app .cg-event-tag{
  display:block;font-size:11px;line-height:1.3;
  background:#dbeafe;color:#1d4ed8;border-radius:4px;
  padding:1px 5px;margin-top:2px;word-break:break-word;
  cursor:pointer;
}
#cg-app .cg-event-tag:hover{background:#bfdbfe;}

/* ── モーダル ── */
#cg-app .cg-modal-overlay{
  display:none;position:fixed;inset:0;background:rgba(0,0,0,0.4);
  z-index:9999;align-items:center;justify-content:center;
}
#cg-app .cg-modal-overlay.cg-open{display:flex;}
#cg-app .cg-modal{
  background:#fff;border-radius:12px;padding:24px;width:90%;max-width:380px;
  box-shadow:0 20px 60px rgba(0,0,0,0.2);
}
#cg-app .cg-modal h3{font-size:16px;font-weight:700;margin-bottom:14px;color:#1e293b;}
#cg-app .cg-modal input[type=text]{
  width:100%;border:1px solid #cbd5e1;border-radius:7px;padding:9px 12px;
  font-size:14px;outline:none;margin-bottom:10px;
  font-family:inherit;
}
#cg-app .cg-modal input[type=text]:focus{border-color:#3b82f6;}
#cg-app .cg-modal-btns{display:flex;gap:8px;justify-content:flex-end;margin-top:6px;}
#cg-app .cg-event-list{margin-bottom:10px;max-height:160px;overflow-y:auto;}
#cg-app .cg-event-item{
  display:flex;align-items:center;justify-content:space-between;
  padding:5px 8px;background:#f1f5f9;border-radius:6px;margin-bottom:5px;
  font-size:13px;
}
#cg-app .cg-event-del{
  background:none;border:none;color:#94a3b8;cursor:pointer;font-size:16px;
  line-height:1;padding:0 2px;
}
#cg-app .cg-event-del:hover{color:#ef4444;}

/* ── 年間ビュー ── */
#cg-app .cg-year-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:16px;
}
#cg-app .cg-mini-cal{
  background:#fff;border:1px solid #e2e8f0;border-radius:10px;
  overflow:hidden;cursor:pointer;transition:box-shadow 0.15s;
}
#cg-app .cg-mini-cal:hover{box-shadow:0 4px 16px rgba(59,130,246,0.15);}
#cg-app .cg-mini-header{
  background:#3b82f6;color:#fff;text-align:center;
  padding:8px;font-size:13px;font-weight:700;
}
#cg-app .cg-mini-grid{
  display:grid;grid-template-columns:repeat(7,1fr);
  padding:4px;gap:1px;
}
#cg-app .cg-mini-dh{
  text-align:center;font-size:9px;font-weight:700;
  color:#94a3b8;padding:3px 0;
}
#cg-app .cg-mini-cell{
  text-align:center;font-size:10px;padding:3px 0;border-radius:3px;
  color:#334155;
}
#cg-app .cg-mini-cell.cg-mini-other{color:#cbd5e1;}
#cg-app .cg-mini-cell.cg-mini-today{background:#3b82f6;color:#fff;border-radius:50%;font-weight:700;}
#cg-app .cg-mini-cell.cg-mini-sun{color:#ef4444;}
#cg-app .cg-mini-cell.cg-mini-sat{color:#3b82f6;}
#cg-app .cg-mini-cell.cg-mini-today.cg-mini-sun,
#cg-app .cg-mini-cell.cg-mini-today.cg-mini-sat{color:#fff;}
#cg-app .cg-mini-cell.cg-mini-event{background:#fde68a;border-radius:3px;}
#cg-app .cg-mini-cell.cg-mini-today.cg-mini-event{background:#3b82f6;}

/* ── 印刷 ── */
@media print{
  body *{visibility:hidden!important;}
  #cg-app,#cg-app *{visibility:visible!important;}
  #cg-app .cg-no-print{display:none!important;}
  #cg-app{
    background:#fff!important;border:none!important;
    padding:0!important;max-width:100%!important;
    font-size:12px!important;
  }
  #cg-app .cg-cell{min-height:80px!important;page-break-inside:avoid;}
  #cg-app .cg-year-grid{grid-template-columns:repeat(3,1fr)!important;}
  #cg-app .cg-modal-overlay{display:none!important;}
}

/* ── レスポンシブ ── */
@media(max-width:600px){
  #cg-app .cg-cell{min-height:54px;padding:3px;}
  #cg-app .cg-date-num{font-size:11px;width:20px;height:20px;}
  #cg-app .cg-event-tag{font-size:9px;}
  #cg-app .cg-nav-title{font-size:16px;}
  #cg-app .cg-year-grid{grid-template-columns:repeat(2,1fr);}
}
@media(max-width:400px){
  #cg-app .cg-year-grid{grid-template-columns:1fr 1fr;}
  #cg-app .cg-mini-cell{font-size:9px;}
}
</style>

<!-- ツールバー -->
<div class="cg-toolbar cg-no-print">
  <div class="cg-toolbar-group">
    <label for="cg-view-sel">表示:</label>
    <select id="cg-view-sel" onchange="cgChangeView()">
      <option value="month">月表示</option>
      <option value="year">年間一覧</option>
    </select>
  </div>
  <div class="cg-sep"></div>
  <div class="cg-toolbar-group">
    <label for="cg-month-sel">月:</label>
    <select id="cg-month-sel" onchange="cgGoTo()">
      <option value="0">1月</option><option value="1">2月</option>
      <option value="2">3月</option><option value="3">4月</option>
      <option value="4">5月</option><option value="5">6月</option>
      <option value="6">7月</option><option value="7">8月</option>
      <option value="8">9月</option><option value="9">10月</option>
      <option value="10">11月</option><option value="11">12月</option>
    </select>
    <label for="cg-year-inp">年:</label>
    <input type="number" id="cg-year-inp" min="1900" max="2100" onchange="cgGoTo()">
  </div>
  <div class="cg-sep"></div>
  <div class="cg-toolbar-group">
    <label for="cg-week-start">週の開始:</label>
    <select id="cg-week-start" onchange="cgRender()">
      <option value="0">日曜日</option>
      <option value="1">月曜日</option>
    </select>
  </div>
  <div class="cg-sep"></div>
  <button class="cg-btn cg-btn-print" onclick="window.print()">&#128438; 印刷</button>
</div>

<!-- ナビゲーション -->
<div class="cg-nav cg-no-print" id="cg-nav-bar">
  <div class="cg-nav-btns">
    <button class="cg-btn cg-btn-secondary" onclick="cgStep(-1)">&#8592; 前へ</button>
    <button class="cg-btn cg-btn-secondary" onclick="cgToday()">今日</button>
    <button class="cg-btn cg-btn-secondary" onclick="cgStep(1)">次へ &#8594;</button>
  </div>
  <div class="cg-nav-title" id="cg-nav-title"></div>
</div>

<!-- カレンダー出力 -->
<div id="cg-output"></div>

<!-- イベント追加モーダル -->
<div class="cg-modal-overlay cg-no-print" id="cg-modal">
  <div class="cg-modal">
    <h3 id="cg-modal-date-title">予定を追加</h3>
    <div class="cg-event-list" id="cg-modal-event-list"></div>
    <input type="text" id="cg-event-input" placeholder="予定・メモを入力..." maxlength="60">
    <div class="cg-modal-btns">
      <button class="cg-btn cg-btn-secondary" onclick="cgCloseModal()">閉じる</button>
      <button class="cg-btn cg-btn-primary" onclick="cgAddEvent()">追加</button>
    </div>
  </div>
</div>

<script>
(function(){
  var MONTHS_JA = ['1月','2月','3月','4月','5月','6月',
                   '7月','8月','9月','10月','11月','12月'];
  // 週の開始が日曜→ 日月火水木金土、月曜→ 月火水木金土日
  var DAYS_SHORT_JA = ['日','月','火','水','木','金','土'];
  var DAYS_FULL_JA  = ['日曜日','月曜日','火曜日','水曜日','木曜日','金曜日','土曜日'];

  var state = {
    view: 'month',
    year: new Date().getFullYear(),
    month: new Date().getMonth(),
    weekStart: 0,
    events: {},
    modalDate: null
  };

  try {
    var saved = localStorage.getItem('cgja-events');
    if(saved) state.events = JSON.parse(saved);
  } catch(e){}

  function saveEvents(){
    try{ localStorage.setItem('cgja-events', JSON.stringify(state.events)); }catch(e){}
  }

  function evKey(y,m,d){ return y+'-'+m+'-'+d; }
  function getEvents(y,m,d){ return state.events[evKey(y,m,d)] || []; }

  function syncControls(){
    document.getElementById('cg-view-sel').value = state.view;
    document.getElementById('cg-month-sel').value = state.month;
    document.getElementById('cg-year-inp').value = state.year;
    document.getElementById('cg-week-start').value = state.weekStart;
  }

  window.cgChangeView = function(){
    state.view = document.getElementById('cg-view-sel').value;
    cgRender();
  };

  window.cgGoTo = function(){
    state.month = parseInt(document.getElementById('cg-month-sel').value);
    state.year = parseInt(document.getElementById('cg-year-inp').value) || state.year;
    cgRender();
  };

  window.cgStep = function(dir){
    if(state.view === 'year'){
      state.year += dir;
    } else {
      state.month += dir;
      if(state.month < 0){ state.month = 11; state.year--; }
      if(state.month > 11){ state.month = 0; state.year++; }
    }
    syncControls();
    cgRender();
  };

  window.cgToday = function(){
    var now = new Date();
    state.year = now.getFullYear();
    state.month = now.getMonth();
    syncControls();
    cgRender();
  };

  window.cgRender = function(){
    state.weekStart = parseInt(document.getElementById('cg-week-start').value);
    syncControls();
    var navBar = document.getElementById('cg-nav-bar');
    var navTitle = document.getElementById('cg-nav-title');
    if(state.view === 'year'){
      navTitle.textContent = state.year + '年';
      navBar.querySelector('.cg-nav-btns button:nth-child(2)').style.display = 'none';
      renderYear();
    } else {
      navTitle.textContent = state.year + '年 ' + MONTHS_JA[state.month];
      navBar.querySelector('.cg-nav-btns button:nth-child(2)').style.display = '';
      renderMonth(state.year, state.month, 'cg-output', true);
    }
  };

  function buildDayHeaders(ws){
    var html = '';
    for(var i=0;i<7;i++){
      var di = (ws + i) % 7;
      var col = di===0 ? 'color:#ef4444;' : di===6 ? 'color:#3b82f6;' : '';
      html += '<div class="cg-day-header" style="'+col+'">'+DAYS_SHORT_JA[di]+'</div>';
    }
    return html;
  }

  function renderMonth(y, m, targetId, interactive){
    var today = new Date();
    var todayY = today.getFullYear(), todayM = today.getMonth(), todayD = today.getDate();
    var ws = state.weekStart;
    var firstDay = new Date(y, m, 1).getDay();
    var daysInMonth = new Date(y, m+1, 0).getDate();
    var daysInPrev = new Date(y, m, 0).getDate();
    var offset = (firstDay - ws + 7) % 7;

    var html = '<div class="cg-calendar-wrap"><div class="cg-grid">';
    html += buildDayHeaders(ws);

    var totalCells = Math.ceil((offset + daysInMonth)/7)*7;

    for(var c=0;c<totalCells;c++){
      var day, mo, yr, isOther=false, isToday=false;
      if(c < offset){
        day = daysInPrev - offset + c + 1;
        mo = m-1; yr = y;
        if(mo < 0){ mo = 11; yr = y-1; }
        isOther = true;
      } else if(c >= offset + daysInMonth){
        day = c - offset - daysInMonth + 1;
        mo = m+1; yr = y;
        if(mo > 11){ mo = 0; yr = y+1; }
        isOther = true;
      } else {
        day = c - offset + 1;
        mo = m; yr = y;
      }

      var dow = (ws + c) % 7; // 0=Sun,6=Sat in 0-indexed
      var isSun = (dow === 0);
      var isSat = (dow === 6);
      isToday = (!isOther && yr===todayY && mo===todayM && day===todayD);

      var evs = getEvents(yr, mo, day);
      var hasEv = evs.length > 0;

      var cls = 'cg-cell';
      if(isOther) cls += ' cg-other-month';
      if(isToday) cls += ' cg-today';
      if(!isOther && isSun) cls += ' cg-sunday';
      if(!isOther && isSat) cls += ' cg-saturday';
      if(hasEv && !isOther) cls += ' cg-has-event';

      var onclick = interactive ? 'onclick="cgOpenModal('+yr+','+mo+','+day+')"' : '';

      html += '<div class="'+cls+'" '+onclick+'>';
      html += '<div class="cg-date-num">'+day+'</div>';
      if(!isOther && hasEv){
        evs.slice(0,3).forEach(function(ev){
          html += '<span class="cg-event-tag" onclick="event.stopPropagation();cgOpenModal('+yr+','+mo+','+day+')">'+escHtml(ev)+'</span>';
        });
        if(evs.length > 3){
          html += '<span style="font-size:10px;color:#64748b;padding:1px 4px;">他'+(evs.length-3)+'件</span>';
        }
      }
      html += '</div>';
    }
    html += '</div></div>';
    document.getElementById(targetId).innerHTML = html;
  }

  function renderYear(){
    var html = '<div class="cg-year-grid">';
    for(var m=0;m<12;m++){
      html += renderMiniCal(state.year, m);
    }
    html += '</div>';
    document.getElementById('cg-output').innerHTML = html;
  }

  function renderMiniCal(y, m){
    var today = new Date();
    var todayY = today.getFullYear(), todayM = today.getMonth(), todayD = today.getDate();
    var ws = state.weekStart;
    var firstDay = new Date(y, m, 1).getDay();
    var daysInMonth = new Date(y, m+1, 0).getDate();
    var daysInPrev = new Date(y, m, 0).getDate();
    var offset = (firstDay - ws + 7) % 7;

    var html = '<div class="cg-mini-cal" onclick="cgMiniClick('+m+')">';
    html += '<div class="cg-mini-header">'+MONTHS_JA[m]+'</div>';
    html += '<div class="cg-mini-grid">';

    for(var i=0;i<7;i++){
      var di = (ws+i)%7;
      var col = di===0?'color:#ef4444;':di===6?'color:#3b82f6;':'';
      html += '<div class="cg-mini-dh" style="'+col+'">'+DAYS_SHORT_JA[di]+'</div>';
    }

    var totalCells = Math.ceil((offset + daysInMonth)/7)*7;
    for(var c=0;c<totalCells;c++){
      var day, isOther=false, isToday=false;
      var mo = m, yr = y;
      if(c < offset){
        day = daysInPrev - offset + c + 1;
        isOther = true;
      } else if(c >= offset + daysInMonth){
        day = c - offset - daysInMonth + 1;
        isOther = true;
      } else {
        day = c - offset + 1;
      }
      var dow = (ws + c) % 7;
      var isSun = (dow === 0), isSat = (dow === 6);
      isToday = (!isOther && yr===todayY && mo===todayM && day===todayD);
      var hasEv = !isOther && getEvents(yr, mo, day).length > 0;

      var cls = 'cg-mini-cell';
      if(isOther) cls += ' cg-mini-other';
      else if(isToday) cls += ' cg-mini-today';
      else if(isSun) cls += ' cg-mini-sun';
      else if(isSat) cls += ' cg-mini-sat';
      if(hasEv && !isOther && !isToday) cls += ' cg-mini-event';

      html += '<div class="'+cls+'">'+(isOther?'':day)+'</div>';
    }
    html += '</div></div>';
    return html;
  }

  window.cgMiniClick = function(m){
    state.month = m;
    state.view = 'month';
    document.getElementById('cg-view-sel').value = 'month';
    syncControls();
    cgRender();
  };

  // ── モーダル ──
  window.cgOpenModal = function(y, m, d){
    state.modalDate = {y:y, m:m, d:d};
    var dow = new Date(y,m,d).getDay();
    var title = y + '年' + MONTHS_JA[m] + d + '日（' + DAYS_FULL_JA[dow] + '）';
    document.getElementById('cg-modal-date-title').textContent = title;
    document.getElementById('cg-event-input').value = '';
    renderModalEvents();
    document.getElementById('cg-modal').classList.add('cg-open');
    setTimeout(function(){ document.getElementById('cg-event-input').focus(); }, 80);
  };

  window.cgCloseModal = function(){
    document.getElementById('cg-modal').classList.remove('cg-open');
    state.modalDate = null;
  };

  function renderModalEvents(){
    var md = state.modalDate;
    var evs = getEvents(md.y, md.m, md.d);
    var html = '';
    evs.forEach(function(ev, i){
      html += '<div class="cg-event-item"><span>'+escHtml(ev)+'</span>'
            + '<button class="cg-event-del" onclick="cgDelEvent('+i+')">&#215;</button></div>';
    });
    document.getElementById('cg-modal-event-list').innerHTML = html;
  }

  window.cgAddEvent = function(){
    var inp = document.getElementById('cg-event-input');
    var val = inp.value.trim();
    if(!val || !state.modalDate) return;
    var md = state.modalDate;
    var k = evKey(md.y, md.m, md.d);
    if(!state.events[k]) state.events[k] = [];
    state.events[k].push(val);
    saveEvents();
    inp.value = '';
    renderModalEvents();
    cgRender();
  };

  window.cgDelEvent = function(idx){
    var md = state.modalDate;
    var k = evKey(md.y, md.m, md.d);
    if(state.events[k]){
      state.events[k].splice(idx, 1);
      if(!state.events[k].length) delete state.events[k];
      saveEvents();
      renderModalEvents();
      cgRender();
    }
  };

  document.getElementById('cg-modal').addEventListener('click', function(e){
    if(e.target === this) cgCloseModal();
  });

  document.getElementById('cg-event-input').addEventListener('keydown', function(e){
    if(e.key === 'Enter') cgAddEvent();
  });

  function escHtml(s){
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;')
            .replace(/"/g,'&quot;').replace(/'/g,'&#39;');
  }

  // 初期化
  syncControls();
  cgRender();
})();
</script>

---

**使い方:**

1. 月・年を選択するか、**年間一覧**で12ヶ月をまとめて表示。
2. **週の開始日**（日曜・月曜）を選択できます。
3. **日付をクリック**して予定・メモを追加 — ブラウザに自動保存されます。
4. **印刷**ボタンで印刷専用レイアウトのカレンダーを出力。

> 1日の予定管理 → [デイリープランナー](/ja/tools/daily-planner/)

> イベントカウントダウン → [イベントカウントダウン](/ja/tools/event-countdown/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

<div class="cg-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>
