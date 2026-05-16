---
title: "Calendar Generator"
date: 2025-05-16
description: "Free printable calendar generator. Create monthly or yearly calendars, add events, and print. Choose week start day and layout. No sign-up required."
categories: ["Free Tools"]
slug: "calendar-generator"
ShowToc: false
cover:
  image: "/images/covers/calendar-generator.png"
  alt: "Calendar Generator"
---

<div id="cg-app">
<style>
#cg-app *,#cg-app *::before,#cg-app *::after{box-sizing:border-box;margin:0;padding:0}
#cg-app{
  font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;
  font-size:15px;line-height:1.6;
  color:#1e293b;
  background:#f8fafc;
  border-radius:12px;
  padding:20px;
  max-width:980px;
  margin:0 auto;
}

/* ── Toolbar ── */
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
#cg-app .cg-toolbar input[type=number]{width:72px;}
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

/* ── Nav header ── */
#cg-app .cg-nav{
  display:flex;align-items:center;justify-content:space-between;
  margin-bottom:14px;
}
#cg-app .cg-nav-title{
  font-size:20px;font-weight:700;color:#1e293b;
  letter-spacing:-0.3px;
}
#cg-app .cg-nav-btns{display:flex;gap:6px;}

/* ── Monthly calendar ── */
#cg-app .cg-calendar-wrap{background:#fff;border:1px solid #e2e8f0;border-radius:10px;overflow:hidden;}
#cg-app .cg-grid{
  display:grid;grid-template-columns:repeat(7,1fr);
}
#cg-app .cg-day-header{
  text-align:center;padding:10px 0;font-size:12px;font-weight:700;
  color:#64748b;text-transform:uppercase;letter-spacing:0.5px;
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
#cg-app .cg-cell.cg-weekend .cg-date-num{color:#ef4444;}
#cg-app .cg-cell.cg-today .cg-date-num{color:#fff;}
#cg-app .cg-event-tag{
  display:block;font-size:11px;line-height:1.3;
  background:#dbeafe;color:#1d4ed8;border-radius:4px;
  padding:1px 5px;margin-top:2px;word-break:break-word;
  cursor:pointer;
}
#cg-app .cg-event-tag:hover{background:#bfdbfe;}

/* ── Event modal ── */
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

/* ── Year view ── */
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
#cg-app .cg-mini-cell.cg-mini-weekend{color:#ef4444;}
#cg-app .cg-mini-cell.cg-mini-today.cg-mini-weekend{color:#fff;}
#cg-app .cg-mini-cell.cg-mini-event{background:#fde68a;border-radius:3px;}
#cg-app .cg-mini-cell.cg-mini-today.cg-mini-event{background:#3b82f6;}

/* ── Print ── */
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

/* ── Responsive ── */
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

<!-- Toolbar -->
<div class="cg-toolbar cg-no-print">
  <div class="cg-toolbar-group">
    <label for="cg-view-sel">View:</label>
    <select id="cg-view-sel" onchange="cgChangeView()">
      <option value="month">Monthly</option>
      <option value="year">Year at a Glance</option>
    </select>
  </div>
  <div class="cg-sep"></div>
  <div class="cg-toolbar-group">
    <label for="cg-month-sel">Month:</label>
    <select id="cg-month-sel" onchange="cgGoTo()">
      <option value="0">January</option><option value="1">February</option>
      <option value="2">March</option><option value="3">April</option>
      <option value="4">May</option><option value="5">June</option>
      <option value="6">July</option><option value="7">August</option>
      <option value="8">September</option><option value="9">October</option>
      <option value="10">November</option><option value="11">December</option>
    </select>
    <label for="cg-year-inp">Year:</label>
    <input type="number" id="cg-year-inp" min="1900" max="2100" onchange="cgGoTo()">
  </div>
  <div class="cg-sep"></div>
  <div class="cg-toolbar-group">
    <label for="cg-week-start">Week starts:</label>
    <select id="cg-week-start" onchange="cgRender()">
      <option value="0">Sunday</option>
      <option value="1">Monday</option>
    </select>
  </div>
  <div class="cg-sep"></div>
  <button class="cg-btn cg-btn-print" onclick="window.print()">&#128438; Print</button>
</div>

<!-- Nav -->
<div class="cg-nav cg-no-print" id="cg-nav-bar">
  <div class="cg-nav-btns">
    <button class="cg-btn cg-btn-secondary" onclick="cgStep(-1)">&#8592; Prev</button>
    <button class="cg-btn cg-btn-secondary" onclick="cgToday()">Today</button>
    <button class="cg-btn cg-btn-secondary" onclick="cgStep(1)">Next &#8594;</button>
  </div>
  <div class="cg-nav-title" id="cg-nav-title"></div>
</div>

<!-- Calendar output -->
<div id="cg-output"></div>

<!-- Event Modal -->
<div class="cg-modal-overlay cg-no-print" id="cg-modal">
  <div class="cg-modal">
    <h3 id="cg-modal-date-title">Add Event</h3>
    <div class="cg-event-list" id="cg-modal-event-list"></div>
    <input type="text" id="cg-event-input" placeholder="Event or note..." maxlength="60">
    <div class="cg-modal-btns">
      <button class="cg-btn cg-btn-secondary" onclick="cgCloseModal()">Close</button>
      <button class="cg-btn cg-btn-primary" onclick="cgAddEvent()">Add</button>
    </div>
  </div>
</div>

<script>
(function(){
  var MONTHS = ['January','February','March','April','May','June',
                'July','August','September','October','November','December'];
  var DAYS_FULL = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
  var DAYS_SHORT = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];

  var state = {
    view: 'month',
    year: new Date().getFullYear(),
    month: new Date().getMonth(),
    weekStart: 0,
    events: {},   // key: "YYYY-M-D" -> []
    modalDate: null
  };

  // Load persisted events
  try {
    var saved = localStorage.getItem('cg-events');
    if(saved) state.events = JSON.parse(saved);
  } catch(e){}

  function saveEvents(){
    try{ localStorage.setItem('cg-events', JSON.stringify(state.events)); }catch(e){}
  }

  function evKey(y,m,d){ return y+'-'+m+'-'+d; }

  function getEvents(y,m,d){
    return state.events[evKey(y,m,d)] || [];
  }

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
      navTitle.textContent = state.year;
      navBar.querySelector('.cg-nav-btns button:nth-child(2)').style.display = 'none';
      renderYear();
    } else {
      navTitle.textContent = MONTHS[state.month] + ' ' + state.year;
      navBar.querySelector('.cg-nav-btns button:nth-child(2)').style.display = '';
      renderMonth(state.year, state.month, 'cg-output', true);
    }
  };

  function buildDayHeaders(ws){
    var html = '';
    for(var i=0;i<7;i++){
      var di = (ws + i) % 7;
      html += '<div class="cg-day-header">'+DAYS_SHORT[di]+'</div>';
    }
    return html;
  }

  function renderMonth(y, m, targetId, interactive){
    var today = new Date();
    var todayY = today.getFullYear(), todayM = today.getMonth(), todayD = today.getDate();
    var ws = state.weekStart;
    var firstDay = new Date(y, m, 1).getDay(); // 0=Sun
    var daysInMonth = new Date(y, m+1, 0).getDate();
    var daysInPrev = new Date(y, m, 0).getDate();

    // offset: how many cells before day 1
    var offset = (firstDay - ws + 7) % 7;

    var html = '<div class="cg-calendar-wrap"><div class="cg-grid">';
    html += buildDayHeaders(ws);

    var totalCells = Math.ceil((offset + daysInMonth) / 7) * 7;

    for(var c=0; c<totalCells; c++){
      var day, mo, yr, isOther = false, isToday = false, isWeekend = false;
      if(c < offset){
        day = daysInPrev - offset + c + 1;
        mo = m - 1; yr = y;
        if(mo < 0){ mo = 11; yr = y-1; }
        isOther = true;
      } else if(c >= offset + daysInMonth){
        day = c - offset - daysInMonth + 1;
        mo = m + 1; yr = y;
        if(mo > 11){ mo = 0; yr = y+1; }
        isOther = true;
      } else {
        day = c - offset + 1;
        mo = m; yr = y;
      }

      var dayOfWeek = (ws + c) % 7; // col in grid -> actual day index (0=Sun,6=Sat)
      var actualDow = (ws + c) % 7;
      // We need actual day of week: column c corresponds to day (ws+c)%7
      var dow = (ws + c) % 7; // 0..6
      isWeekend = (dow === 0 || dow === 6);
      isToday = (!isOther && yr===todayY && mo===todayM && day===todayD);

      var evs = getEvents(yr, mo, day);
      var hasEv = evs.length > 0;

      var cls = 'cg-cell';
      if(isOther) cls += ' cg-other-month';
      if(isToday) cls += ' cg-today';
      if(isWeekend && !isOther) cls += ' cg-weekend';
      if(hasEv && !isOther) cls += ' cg-has-event';

      var onclick = interactive ? 'onclick="cgOpenModal('+yr+','+mo+','+day+')"' : '';

      html += '<div class="'+cls+'" '+onclick+'>';
      html += '<div class="cg-date-num">'+day+'</div>';
      if(!isOther && hasEv){
        evs.slice(0,3).forEach(function(ev){
          html += '<span class="cg-event-tag" onclick="event.stopPropagation();cgOpenModal('+yr+','+mo+','+day+')">'+escHtml(ev)+'</span>';
        });
        if(evs.length > 3){
          html += '<span style="font-size:10px;color:#64748b;padding:1px 4px;">+' + (evs.length-3) + ' more</span>';
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
    html += '<div class="cg-mini-header">'+MONTHS[m]+'</div>';
    html += '<div class="cg-mini-grid">';

    for(var i=0;i<7;i++){
      html += '<div class="cg-mini-dh">'+DAYS_SHORT[(ws+i)%7].charAt(0)+'</div>';
    }

    var totalCells = Math.ceil((offset + daysInMonth)/7)*7;
    for(var c=0;c<totalCells;c++){
      var day, isOther=false, isToday=false, isWeekend=false;
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
      isWeekend = (dow===0 || dow===6);
      isToday = (!isOther && yr===todayY && mo===todayM && day===todayD);
      var hasEv = !isOther && getEvents(yr, mo, day).length > 0;

      var cls = 'cg-mini-cell';
      if(isOther) cls += ' cg-mini-other';
      else if(isToday) cls += ' cg-mini-today';
      else if(isWeekend) cls += ' cg-mini-weekend';
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

  // ── Modal ──
  window.cgOpenModal = function(y, m, d){
    state.modalDate = {y:y, m:m, d:d};
    var title = DAYS_FULL[new Date(y,m,d).getDay()] + ', ' + MONTHS[m] + ' ' + d + ', ' + y;
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

  // Close modal on overlay click
  document.getElementById('cg-modal').addEventListener('click', function(e){
    if(e.target === this) cgCloseModal();
  });

  // Enter key in modal
  document.getElementById('cg-event-input').addEventListener('keydown', function(e){
    if(e.key === 'Enter') cgAddEvent();
  });

  function escHtml(s){
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;')
            .replace(/"/g,'&quot;').replace(/'/g,'&#39;');
  }

  // Init
  syncControls();
  cgRender();
})();
</script>

---

**How to use:**

1. Select a month and year, or switch to **Year at a Glance** for all 12 months.
2. Choose whether your week starts on **Sunday or Monday**.
3. **Click any date** to add events or notes — they save automatically in your browser.
4. Hit **Print** to generate a clean, print-optimized calendar.

> Plan your day → [Daily Planner](/tools/daily-planner/)

> Event countdown → [Event Countdown](/tools/event-countdown/)

</div>
