---
title: "Crontab Generator"
date: 2025-05-16
description: "Free online crontab generator. Build cron expressions visually with dropdowns, use common presets, get human-readable descriptions, see next 5 run times, copy your cron expression, and validate existing ones."
categories: ["Free Tools"]
slug: "crontab-generator"
ShowToc: false
aliases:
  - "/tools/cron-generator/"
  - "/tools/cron-expression-builder/"
cover:
  image: "/images/covers/crontab-generator.png"
  alt: "Crontab Generator"
---

<div id="cg-app">

<style>
#cg-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #0f0f13;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin: 0 auto;
  max-width: 900px;
  box-sizing: border-box;
}
#cg-app * { box-sizing: border-box; }

#cg-app h2 {
  font-size: 1.05rem;
  font-weight: 600;
  color: #f1f5f9;
  margin: 0 0 14px 0;
  letter-spacing: 0.02em;
}
#cg-app h3 {
  font-size: 0.82rem;
  font-weight: 600;
  color: #94a3b8;
  margin: 0 0 12px 0;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

/* ── Presets ── */
.cg-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 22px;
}
.cg-preset-btn {
  padding: 6px 14px;
  border-radius: 20px;
  border: 1px solid #2d2d4d;
  background: #1a1a24;
  color: #a5b4fc;
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.15s, border-color 0.15s;
}
.cg-preset-btn:hover { background: #22224a; border-color: #6366f1; color: #c7d2fe; }
.cg-preset-btn.active { background: #3730a3; border-color: #6366f1; color: #fff; }

/* ── Field Builder ── */
.cg-builder {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 10px;
  padding: 18px;
  margin-bottom: 18px;
}
.cg-fields {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 12px;
}
.cg-field-wrap { }
.cg-field-label {
  font-size: 0.72rem;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
  display: block;
}
.cg-field-select {
  width: 100%;
  background: #0f0f18;
  border: 1px solid #2d2d3d;
  border-radius: 6px;
  color: #e2e8f0;
  font-size: 0.84rem;
  padding: 7px 10px;
  outline: none;
  font-family: inherit;
  cursor: pointer;
  transition: border-color 0.2s;
  appearance: none;
  -webkit-appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2364748b' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 8px center;
  padding-right: 26px;
}
.cg-field-select:focus { border-color: #6366f1; }

/* ── Expression Display ── */
.cg-expr-wrap {
  background: #12192e;
  border: 1px solid #1e2a4a;
  border-radius: 8px;
  padding: 14px 16px;
  margin-bottom: 16px;
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}
.cg-expr-code {
  font-family: 'Courier New', 'Consolas', monospace;
  font-size: 1.4rem;
  font-weight: 700;
  color: #7dd3fc;
  letter-spacing: 0.06em;
  flex: 1;
  min-width: 200px;
}
.cg-btn {
  padding: 7px 16px;
  border-radius: 6px;
  border: none;
  font-size: 0.84rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.15s, transform 0.1s;
  white-space: nowrap;
}
.cg-btn:active { transform: scale(0.97); }
.cg-btn-copy { background: #1a1a24; color: #a5b4fc; border: 1px solid #2d2d4d; }
.cg-btn-copy:hover { background: #22224a; }
.cg-btn-primary { background: #6366f1; color: #fff; }
.cg-btn-primary:hover { background: #4f46e5; }
.cg-btn-danger { background: #1a1a24; color: #f87171; border: 1px solid #3d2020; }
.cg-btn-danger:hover { background: #2d1a1a; }

/* ── Description ── */
.cg-desc-wrap {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  padding: 14px 16px;
  margin-bottom: 18px;
}
.cg-desc-text {
  font-size: 0.95rem;
  color: #c7d2fe;
  font-weight: 500;
  line-height: 1.5;
}

/* ── Next Run Times ── */
.cg-runs-wrap {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  padding: 14px 16px;
  margin-bottom: 18px;
}
.cg-run-list {
  list-style: none;
  margin: 0;
  padding: 0;
}
.cg-run-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 6px 0;
  border-bottom: 1px solid #1e1e2c;
  font-size: 0.88rem;
}
.cg-run-item:last-child { border-bottom: none; }
.cg-run-num {
  font-size: 0.72rem;
  color: #475569;
  width: 20px;
  text-align: right;
  flex-shrink: 0;
}
.cg-run-time {
  font-family: 'Courier New', monospace;
  color: #7dd3fc;
  font-weight: 600;
}
.cg-run-rel {
  color: #64748b;
  font-size: 0.78rem;
}

/* ── Validator ── */
.cg-validate-wrap {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  padding: 14px 16px;
  margin-bottom: 10px;
}
.cg-validate-row {
  display: flex;
  gap: 8px;
  align-items: center;
  flex-wrap: wrap;
}
.cg-validate-input {
  flex: 1;
  min-width: 200px;
  background: #0f0f18;
  border: 1px solid #2d2d3d;
  border-radius: 6px;
  color: #e2e8f0;
  font-size: 0.9rem;
  font-family: 'Courier New', monospace;
  padding: 8px 12px;
  outline: none;
  transition: border-color 0.2s;
}
.cg-validate-input:focus { border-color: #6366f1; }
.cg-validate-input::placeholder { color: #3a3a5a; font-family: inherit; }
.cg-validate-result {
  margin-top: 10px;
  font-size: 0.88rem;
  min-height: 1.2em;
  line-height: 1.5;
}
.cg-valid { color: #4ade80; }
.cg-invalid { color: #f87171; }

@media (max-width: 640px) {
  #cg-app { padding: 16px 12px; }
  .cg-fields { grid-template-columns: repeat(3, 1fr); }
  .cg-expr-code { font-size: 1.1rem; }
}
@media (max-width: 400px) {
  .cg-fields { grid-template-columns: repeat(2, 1fr); }
}
</style>

<h2>Build Your Cron Expression</h2>

<!-- Presets -->
<div class="cg-presets" id="cg-presets">
  <button class="cg-preset-btn" data-expr="* * * * *" onclick="cgApplyPreset(this)">Every minute</button>
  <button class="cg-preset-btn" data-expr="0 * * * *" onclick="cgApplyPreset(this)">Every hour</button>
  <button class="cg-preset-btn" data-expr="0 0 * * *" onclick="cgApplyPreset(this)">Daily at midnight</button>
  <button class="cg-preset-btn" data-expr="0 9 * * *" onclick="cgApplyPreset(this)">Daily at 9 AM</button>
  <button class="cg-preset-btn" data-expr="0 0 * * 0" onclick="cgApplyPreset(this)">Weekly (Sun)</button>
  <button class="cg-preset-btn" data-expr="0 0 1 * *" onclick="cgApplyPreset(this)">Monthly (1st)</button>
  <button class="cg-preset-btn" data-expr="0 9 * * 1-5" onclick="cgApplyPreset(this)">Weekdays 9 AM</button>
  <button class="cg-preset-btn" data-expr="*/5 * * * *" onclick="cgApplyPreset(this)">Every 5 min</button>
  <button class="cg-preset-btn" data-expr="*/15 * * * *" onclick="cgApplyPreset(this)">Every 15 min</button>
  <button class="cg-preset-btn" data-expr="0 0 1 1 *" onclick="cgApplyPreset(this)">Yearly (Jan 1)</button>
</div>

<!-- Field Builder -->
<div class="cg-builder">
  <div class="cg-fields" id="cg-fields">
    <!-- Minute -->
    <div class="cg-field-wrap">
      <label class="cg-field-label" for="cg-min">Minute</label>
      <select class="cg-field-select" id="cg-min" onchange="cgUpdate()"></select>
    </div>
    <!-- Hour -->
    <div class="cg-field-wrap">
      <label class="cg-field-label" for="cg-hr">Hour</label>
      <select class="cg-field-select" id="cg-hr" onchange="cgUpdate()"></select>
    </div>
    <!-- Day of Month -->
    <div class="cg-field-wrap">
      <label class="cg-field-label" for="cg-dom">Day (Month)</label>
      <select class="cg-field-select" id="cg-dom" onchange="cgUpdate()"></select>
    </div>
    <!-- Month -->
    <div class="cg-field-wrap">
      <label class="cg-field-label" for="cg-mon">Month</label>
      <select class="cg-field-select" id="cg-mon" onchange="cgUpdate()"></select>
    </div>
    <!-- Day of Week -->
    <div class="cg-field-wrap">
      <label class="cg-field-label" for="cg-dow">Day (Week)</label>
      <select class="cg-field-select" id="cg-dow" onchange="cgUpdate()"></select>
    </div>
  </div>
</div>

<!-- Expression Output -->
<div class="cg-expr-wrap">
  <span class="cg-expr-code" id="cg-expr">* * * * *</span>
  <button class="cg-btn cg-btn-copy" id="cg-copy-btn" onclick="cgCopyExpr()">Copy</button>
</div>

<!-- Human-readable description -->
<div class="cg-desc-wrap">
  <h3>Description</h3>
  <div class="cg-desc-text" id="cg-desc">Every minute</div>
</div>

<!-- Next 5 execution times -->
<div class="cg-runs-wrap">
  <h3>Next 5 Execution Times</h3>
  <ul class="cg-run-list" id="cg-run-list"></ul>
</div>

<!-- Validator -->
<div class="cg-validate-wrap">
  <h3>Validate an Existing Expression</h3>
  <div class="cg-validate-row">
    <input class="cg-validate-input" id="cg-val-input" placeholder="e.g. 0 9 * * 1-5" />
    <button class="cg-btn cg-btn-primary" onclick="cgValidate()">Validate</button>
    <button class="cg-btn cg-btn-danger" onclick="cgClearValidate()">Clear</button>
  </div>
  <div class="cg-validate-result" id="cg-val-result"></div>
</div>

<script>
(function(){

  /* ── Field Definitions ── */
  var FIELDS = {
    min: {
      el: null,
      any: '*',
      options: (function(){
        var o = [{ v: '*', l: 'Every minute (*)' }];
        for (var i = 0; i <= 59; i++) o.push({ v: String(i), l: 'At minute ' + i });
        o.push({ v: '*/2', l: 'Every 2 min (*/2)' });
        o.push({ v: '*/5', l: 'Every 5 min (*/5)' });
        o.push({ v: '*/10', l: 'Every 10 min (*/10)' });
        o.push({ v: '*/15', l: 'Every 15 min (*/15)' });
        o.push({ v: '*/30', l: 'Every 30 min (*/30)' });
        return o;
      })()
    },
    hr: {
      el: null,
      any: '*',
      options: (function(){
        var o = [{ v: '*', l: 'Every hour (*)' }];
        for (var i = 0; i <= 23; i++) {
          var ampm = i === 0 ? '12 AM' : i < 12 ? i + ' AM' : i === 12 ? '12 PM' : (i-12) + ' PM';
          o.push({ v: String(i), l: 'At ' + ampm + ' (' + i + ')' });
        }
        o.push({ v: '*/2', l: 'Every 2 hrs (*/2)' });
        o.push({ v: '*/3', l: 'Every 3 hrs (*/3)' });
        o.push({ v: '*/6', l: 'Every 6 hrs (*/6)' });
        o.push({ v: '*/12', l: 'Every 12 hrs (*/12)' });
        return o;
      })()
    },
    dom: {
      el: null,
      any: '*',
      options: (function(){
        var o = [{ v: '*', l: 'Every day (*)' }];
        for (var i = 1; i <= 31; i++) o.push({ v: String(i), l: 'On day ' + i });
        o.push({ v: '*/2', l: 'Every 2 days' });
        o.push({ v: '1,15', l: '1st and 15th' });
        o.push({ v: 'L', l: 'Last day of month' });
        return o;
      })()
    },
    mon: {
      el: null,
      any: '*',
      options: [
        { v: '*', l: 'Every month (*)' },
        { v: '1', l: 'January' }, { v: '2', l: 'February' }, { v: '3', l: 'March' },
        { v: '4', l: 'April' }, { v: '5', l: 'May' }, { v: '6', l: 'June' },
        { v: '7', l: 'July' }, { v: '8', l: 'August' }, { v: '9', l: 'September' },
        { v: '10', l: 'October' }, { v: '11', l: 'November' }, { v: '12', l: 'December' },
        { v: '1-3', l: 'Q1 (Jan–Mar)' }, { v: '4-6', l: 'Q2 (Apr–Jun)' },
        { v: '7-9', l: 'Q3 (Jul–Sep)' }, { v: '10-12', l: 'Q4 (Oct–Dec)' }
      ]
    },
    dow: {
      el: null,
      any: '*',
      options: [
        { v: '*', l: 'Every day of week (*)' },
        { v: '0', l: 'Sunday (0)' }, { v: '1', l: 'Monday (1)' }, { v: '2', l: 'Tuesday (2)' },
        { v: '3', l: 'Wednesday (3)' }, { v: '4', l: 'Thursday (4)' }, { v: '5', l: 'Friday (5)' },
        { v: '6', l: 'Saturday (6)' },
        { v: '1-5', l: 'Weekdays (Mon–Fri)' }, { v: '0,6', l: 'Weekends (Sat–Sun)' },
        { v: '1,3,5', l: 'Mon, Wed, Fri' }, { v: '2,4', l: 'Tue, Thu' }
      ]
    }
  };

  var MONTHS = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
  var DAYS_FULL = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
  var DAYS_SHORT = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];

  /* Populate selects */
  function buildSelects() {
    ['min','hr','dom','mon','dow'].forEach(function(key) {
      var sel = document.getElementById('cg-' + key);
      FIELDS[key].el = sel;
      FIELDS[key].options.forEach(function(opt) {
        var o = document.createElement('option');
        o.value = opt.v; o.textContent = opt.l;
        sel.appendChild(o);
      });
    });
  }

  function getExpr() {
    return ['min','hr','dom','mon','dow'].map(function(k){ return FIELDS[k].el.value; }).join(' ');
  }

  /* ── Description Generator ── */
  function describe(expr) {
    var parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return 'Invalid expression';
    var min = parts[0], hr = parts[1], dom = parts[2], mon = parts[3], dow = parts[4];

    // Common presets
    if (expr === '* * * * *') return 'Every minute';
    if (expr === '0 * * * *') return 'At the start of every hour';
    if (expr === '0 0 * * *') return 'Every day at midnight (12:00 AM)';
    if (expr === '0 0 * * 0') return 'Every Sunday at midnight';
    if (expr === '0 0 1 * *') return 'On the 1st of every month at midnight';
    if (expr === '0 0 1 1 *') return 'On January 1st at midnight (Yearly)';
    if (expr === '0 9 * * 1-5') return 'Every weekday (Monday–Friday) at 9:00 AM';

    var parts_desc = [];

    // Minute
    if (min === '*') parts_desc.push('every minute');
    else if (min.startsWith('*/')) parts_desc.push('every ' + min.slice(2) + ' minutes');
    else parts_desc.push('at minute ' + min);

    // Hour
    if (hr === '*') { /* omit "every hour" if minute already says something */ }
    else if (hr.startsWith('*/')) parts_desc.push('every ' + hr.slice(2) + ' hours');
    else {
      var h = parseInt(hr);
      var ampm = h === 0 ? '12:00 AM' : h < 12 ? h + ':' + (min === '*' ? '00' : (min.length===1?'0':'')+min) + ' AM'
        : h === 12 ? '12:' + (min === '*' ? '00' : (min.length===1?'0':'')+min) + ' PM'
        : (h-12) + ':' + (min === '*' ? '00' : (min.length===1?'0':'')+min) + ' PM';
      parts_desc = ['at ' + ampm];
    }

    // Day of month
    if (dom !== '*' && dom !== '*/1') {
      if (dom === 'L') parts_desc.push('on the last day of the month');
      else if (dom.includes('-')) parts_desc.push('on days ' + dom + ' of the month');
      else if (dom.includes(',')) parts_desc.push('on days ' + dom + ' of the month');
      else if (dom.startsWith('*/')) parts_desc.push('every ' + dom.slice(2) + ' days');
      else parts_desc.push('on day ' + dom + ' of the month');
    }

    // Month
    if (mon !== '*') {
      if (mon.includes('-')) {
        var sp = mon.split('-');
        parts_desc.push('in ' + (MONTHS[parseInt(sp[0])-1]||sp[0]) + '–' + (MONTHS[parseInt(sp[1])-1]||sp[1]));
      } else if (mon.includes(',')) {
        var ms = mon.split(',').map(function(m){ return MONTHS[parseInt(m)-1]||m; });
        parts_desc.push('in ' + ms.join(', '));
      } else {
        parts_desc.push('in ' + (MONTHS[parseInt(mon)-1] || mon));
      }
    }

    // Day of week
    if (dow !== '*') {
      if (dow === '1-5') parts_desc.push('on weekdays (Mon–Fri)');
      else if (dow === '0,6' || dow === '6,0') parts_desc.push('on weekends');
      else if (dow.includes('-')) {
        var sp2 = dow.split('-');
        parts_desc.push('on ' + (DAYS_SHORT[parseInt(sp2[0])]||sp2[0]) + '–' + (DAYS_SHORT[parseInt(sp2[1])]||sp2[1]));
      } else if (dow.includes(',')) {
        var ds = dow.split(',').map(function(d){ return DAYS_SHORT[parseInt(d)]||d; });
        parts_desc.push('on ' + ds.join(', '));
      } else {
        parts_desc.push('every ' + (DAYS_FULL[parseInt(dow)] || 'day ' + dow));
      }
    }

    return parts_desc.length ? parts_desc.join(', ') : 'Custom schedule';
  }

  /* ── Next Run Times ── */
  function nextRuns(expr, count) {
    // Parse standard 5-field cron (no seconds, no 'L', no special chars beyond */n, ranges, lists)
    var parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return [];

    function parseField(str, min, max) {
      var values = [];
      if (str === '*') {
        for (var i = min; i <= max; i++) values.push(i);
        return values;
      }
      // Handle comma-separated
      var segments = str.split(',');
      segments.forEach(function(seg) {
        seg = seg.trim();
        if (seg === '*') {
          for (var i = min; i <= max; i++) values.push(i);
        } else if (seg.startsWith('*/')) {
          var step = parseInt(seg.slice(2));
          for (var i = min; i <= max; i += step) values.push(i);
        } else if (seg.includes('-')) {
          var rng = seg.split('-');
          var from = parseInt(rng[0]), to = parseInt(rng[1]);
          for (var i = from; i <= to; i++) values.push(i);
        } else {
          var n = parseInt(seg);
          if (!isNaN(n)) values.push(n);
        }
      });
      return values.filter(function(v,i,a){ return a.indexOf(v)===i; }).sort(function(a,b){return a-b;});
    }

    // Skip 'L' or unsupported special chars for next-run calc
    try {
      var mins  = parseField(parts[0], 0, 59);
      var hrs   = parseField(parts[1], 0, 23);
      var doms  = parts[2] === '*' ? null : parseField(parts[2], 1, 31);
      var mons  = parseField(parts[3], 1, 12);
      var dows  = parts[4] === '*' ? null : parseField(parts[4], 0, 6);

      var runs = [];
      var now = new Date();
      var cur = new Date(now.getFullYear(), now.getMonth(), now.getDate(), now.getHours(), now.getMinutes() + 1, 0);
      var limit = 50000; // iteration guard

      while (runs.length < count && limit-- > 0) {
        var m = cur.getMonth() + 1; // 1-12
        var dom = cur.getDate();
        var dow = cur.getDay(); // 0=Sun
        var h = cur.getHours();
        var mi = cur.getMinutes();

        if (mons.indexOf(m) >= 0
          && (doms === null || doms.indexOf(dom) >= 0)
          && (dows === null || dows.indexOf(dow) >= 0)
          && hrs.indexOf(h) >= 0
          && mins.indexOf(mi) >= 0) {
          runs.push(new Date(cur));
        }
        cur = new Date(cur.getTime() + 60000);
      }
      return runs;
    } catch(e) {
      return [];
    }
  }

  function relTime(d) {
    var diff = Math.round((d - Date.now()) / 1000);
    if (diff < 60) return 'in ' + diff + 's';
    if (diff < 3600) return 'in ' + Math.round(diff/60) + 'min';
    if (diff < 86400) return 'in ' + Math.round(diff/3600) + 'h';
    return 'in ' + Math.round(diff/86400) + 'd';
  }

  function padZ(n) { return n < 10 ? '0' + n : String(n); }

  function fmtDate(d) {
    return d.getFullYear() + '-' + padZ(d.getMonth()+1) + '-' + padZ(d.getDate())
      + ' ' + padZ(d.getHours()) + ':' + padZ(d.getMinutes());
  }

  function renderRuns(expr) {
    var list = document.getElementById('cg-run-list');
    var runs = nextRuns(expr, 5);
    if (!runs.length) {
      list.innerHTML = '<li class="cg-run-item"><span style="color:#64748b;">Could not compute next run times for this expression.</span></li>';
      return;
    }
    list.innerHTML = runs.map(function(d, i) {
      return '<li class="cg-run-item">'
        + '<span class="cg-run-num">' + (i+1) + '</span>'
        + '<span class="cg-run-time">' + fmtDate(d) + '</span>'
        + '<span class="cg-run-rel">' + relTime(d) + '</span>'
        + '</li>';
    }).join('');
  }

  /* ── Main Update ── */
  function cgUpdate() {
    var expr = getExpr();
    document.getElementById('cg-expr').textContent = expr;
    document.getElementById('cg-desc').textContent = describe(expr);
    renderRuns(expr);
    // Clear active preset highlights
    document.querySelectorAll('.cg-preset-btn').forEach(function(b){
      b.classList.toggle('active', b.getAttribute('data-expr') === expr);
    });
  }

  /* ── Presets ── */
  window.cgApplyPreset = function(btn) {
    var expr = btn.getAttribute('data-expr');
    var parts = expr.split(' ');
    var keys = ['min','hr','dom','mon','dow'];
    keys.forEach(function(k, i) {
      var sel = FIELDS[k].el;
      // Find exact match
      var found = false;
      for (var j = 0; j < sel.options.length; j++) {
        if (sel.options[j].value === parts[i]) {
          sel.selectedIndex = j; found = true; break;
        }
      }
      if (!found) sel.selectedIndex = 0; // fallback to *
    });
    cgUpdate();
  };

  /* ── Copy ── */
  window.cgCopyExpr = function() {
    var expr = getExpr();
    var btn = document.getElementById('cg-copy-btn');
    try {
      if (navigator.clipboard) {
        navigator.clipboard.writeText(expr).then(function(){
          btn.textContent = 'Copied!';
          setTimeout(function(){ btn.textContent = 'Copy'; }, 1600);
        });
      } else {
        var ta = document.createElement('textarea');
        ta.value = expr;
        document.body.appendChild(ta);
        ta.select();
        document.execCommand('copy');
        document.body.removeChild(ta);
        btn.textContent = 'Copied!';
        setTimeout(function(){ btn.textContent = 'Copy'; }, 1600);
      }
    } catch(e) {}
  };

  /* ── Validator ── */
  function validateExpr(expr) {
    var parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return { ok: false, msg: 'A cron expression must have exactly 5 fields (minute hour day month weekday).' };
    var ranges = [[0,59],[0,23],[1,31],[1,12],[0,7]];
    var names  = ['minute','hour','day-of-month','month','day-of-week'];
    for (var i = 0; i < 5; i++) {
      var f = parts[i];
      if (f === '*') continue;
      if (/^\*\/\d+$/.test(f)) {
        var step = parseInt(f.slice(2));
        if (step < 1) return { ok: false, msg: 'Field "' + names[i] + '": step value must be ≥ 1.' };
        continue;
      }
      // Split by comma
      var segs = f.split(',');
      for (var j = 0; j < segs.length; j++) {
        var seg = segs[j].trim();
        if (/^\d+$/.test(seg)) {
          var n = parseInt(seg);
          if (n < ranges[i][0] || n > ranges[i][1]) {
            return { ok: false, msg: 'Field "' + names[i] + '": value ' + n + ' is out of range (' + ranges[i][0] + '–' + ranges[i][1] + ').' };
          }
        } else if (/^\d+-\d+$/.test(seg)) {
          var rp = seg.split('-').map(Number);
          if (rp[0] > rp[1]) return { ok: false, msg: 'Field "' + names[i] + '": range start must be ≤ end.' };
          if (rp[0] < ranges[i][0] || rp[1] > ranges[i][1]) {
            return { ok: false, msg: 'Field "' + names[i] + '": range ' + seg + ' is out of allowed range (' + ranges[i][0] + '–' + ranges[i][1] + ').' };
          }
        } else if (/^\d+-\d+\/\d+$/.test(seg)) {
          continue; // range/step — basic pass
        } else if (seg === 'L' && i === 2) {
          continue; // last day
        } else {
          return { ok: false, msg: 'Field "' + names[i] + '": unrecognised value "' + seg + '".' };
        }
      }
    }
    return { ok: true, msg: 'Valid cron expression: ' + describe(parts.join(' ')) };
  }

  window.cgValidate = function() {
    var val = document.getElementById('cg-val-input').value.trim();
    var res = document.getElementById('cg-val-result');
    if (!val) { res.textContent = 'Please enter a cron expression to validate.'; res.className = 'cg-validate-result'; return; }
    var r = validateExpr(val);
    res.textContent = r.msg;
    res.className = 'cg-validate-result ' + (r.ok ? 'cg-valid' : 'cg-invalid');
    if (r.ok) {
      // Load into builder
      var parts = val.trim().split(/\s+/);
      var keys = ['min','hr','dom','mon','dow'];
      keys.forEach(function(k, i) {
        var sel = FIELDS[k].el;
        for (var j = 0; j < sel.options.length; j++) {
          if (sel.options[j].value === parts[i]) { sel.selectedIndex = j; break; }
        }
      });
      cgUpdate();
    }
  };

  window.cgClearValidate = function() {
    document.getElementById('cg-val-input').value = '';
    document.getElementById('cg-val-result').textContent = '';
    document.getElementById('cg-val-result').className = 'cg-validate-result';
  };

  /* ── Init ── */
  buildSelects();
  cgUpdate();

  // Enter key in validator
  document.getElementById('cg-val-input').addEventListener('keydown', function(e){
    if (e.key === 'Enter') cgValidate();
  });

})();
</script>

> Build cron expressions → [Cron Expression Builder](/tools/cron-expression-builder/)

</div>
