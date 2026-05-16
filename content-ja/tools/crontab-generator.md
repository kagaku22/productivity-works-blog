---
title: "Crontab生成ツール - Cronスケジュールビルダー"
date: 2025-05-16
description: "無料のCrontab生成ツール。直感的なUIでCron式を作成。分・時・日・月・曜日を選択し、次の実行時刻と人間が読める説明を即座に表示。"
categories: ["無料ツール"]
slug: "crontab-generator"
ShowToc: false
aliases:
  - "/ja/tools/cron-generator/"
cover:
  image: "/images/covers/crontab-generator-ja.png"
  alt: "Crontab生成ツール"
---

<div id="cron-app">

<style>
#cron-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #0f1117;
  color: #e2e8f0;
  padding: 24px;
  border-radius: 12px;
  max-width: 860px;
  margin: 0 auto;
  box-sizing: border-box;
}
#cron-app * { box-sizing: border-box; }

#cron-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  color: #a78bfa;
  margin: 0 0 6px 0;
}
#cron-app .subtitle {
  font-size: 0.88rem;
  color: #94a3b8;
  margin: 0 0 24px 0;
}

#cron-app .expr-box {
  background: #1e2030;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 20px 24px;
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}
#cron-app .expr-label {
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  white-space: nowrap;
}
#cron-app .expr-value {
  font-family: 'Courier New', 'Fira Mono', monospace;
  font-size: 1.55rem;
  font-weight: 700;
  color: #a78bfa;
  flex: 1;
  word-break: break-all;
}
#cron-app .copy-btn {
  background: #4f46e5;
  color: #fff;
  border: none;
  border-radius: 7px;
  padding: 9px 18px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  white-space: nowrap;
  transition: background 0.15s;
}
#cron-app .copy-btn:hover { background: #6366f1; }
#cron-app .copy-btn.copied { background: #059669; }

#cron-app .desc-box {
  background: #161b27;
  border-left: 3px solid #a78bfa;
  border-radius: 0 8px 8px 0;
  padding: 12px 18px;
  margin-bottom: 24px;
  font-size: 0.95rem;
  color: #cbd5e1;
  font-style: italic;
}

#cron-app .section-title {
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin: 0 0 10px 0;
}
#cron-app .presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 28px;
}
#cron-app .preset-btn {
  background: #1e2030;
  border: 1px solid #334155;
  color: #94a3b8;
  border-radius: 20px;
  padding: 6px 14px;
  font-size: 0.82rem;
  cursor: pointer;
  transition: all 0.15s;
  white-space: nowrap;
}
#cron-app .preset-btn:hover {
  background: #2d2f45;
  border-color: #a78bfa;
  color: #e2e8f0;
}

#cron-app .fields-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 16px;
  margin-bottom: 28px;
}
#cron-app .field-card {
  background: #1e2030;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 16px;
}
#cron-app .field-name {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #64748b;
  margin-bottom: 4px;
}
#cron-app .field-range {
  font-size: 0.7rem;
  color: #475569;
  margin-bottom: 12px;
}
#cron-app .field-card select,
#cron-app .field-card input[type="text"] {
  width: 100%;
  background: #0f1117;
  border: 1px solid #334155;
  color: #e2e8f0;
  border-radius: 6px;
  padding: 7px 10px;
  font-size: 0.85rem;
  margin-bottom: 8px;
  outline: none;
  transition: border-color 0.15s;
}
#cron-app .field-card select:focus,
#cron-app .field-card input[type="text"]:focus {
  border-color: #a78bfa;
}
#cron-app .field-card select option { background: #1e2030; }
#cron-app .custom-label {
  font-size: 0.72rem;
  color: #475569;
  margin-bottom: 4px;
}
#cron-app .field-preview {
  font-family: 'Courier New', monospace;
  font-size: 1.1rem;
  color: #a78bfa;
  text-align: center;
  padding: 6px 0 2px;
  font-weight: 700;
}

#cron-app .next-runs {
  background: #1e2030;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 28px;
}
#cron-app .next-runs-title {
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 12px;
}
#cron-app .run-list {
  list-style: none;
  margin: 0;
  padding: 0;
}
#cron-app .run-list li {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 8px 0;
  border-bottom: 1px solid #1a2030;
  font-size: 0.88rem;
}
#cron-app .run-list li:last-child { border-bottom: none; }
#cron-app .run-idx {
  width: 22px;
  height: 22px;
  background: #2d2f45;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.7rem;
  color: #a78bfa;
  font-weight: 700;
  flex-shrink: 0;
}
#cron-app .run-time { color: #e2e8f0; font-family: 'Courier New', monospace; }
#cron-app .run-rel { color: #64748b; font-size: 0.78rem; margin-left: auto; }
#cron-app .error-msg {
  color: #f87171;
  font-size: 0.85rem;
  padding: 10px 0 0;
}

#cron-app .freee-cta {
  background: #1e2030;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 18px 22px;
  font-size: 0.9rem;
  color: #cbd5e1;
  line-height: 1.7;
}
#cron-app .freee-cta a { color: #a78bfa; }
#cron-app .freee-cta a:hover { color: #c4b5fd; }

@media (max-width: 540px) {
  #cron-app .expr-value { font-size: 1.1rem; }
  #cron-app .fields-grid { grid-template-columns: 1fr 1fr; }
}
</style>

<h2>Crontab 生成ツール</h2>
<p class="subtitle">各フィールドを選択するだけでCron式を視覚的に作成。すぐにコピーできます。</p>

<!-- Expression display -->
<div class="expr-box">
  <span class="expr-label">Cron式</span>
  <span class="expr-value" id="cron-expr">* * * * *</span>
  <button class="copy-btn" id="copy-btn" onclick="cronCopyJa()">コピー</button>
</div>
<div class="desc-box" id="cron-desc">毎分実行</div>

<!-- Presets -->
<div class="section-title">よく使うプリセット</div>
<div class="presets">
  <button class="preset-btn" onclick="cronPresetJa('* * * * *')">毎分</button>
  <button class="preset-btn" onclick="cronPresetJa('0 * * * *')">毎時0分</button>
  <button class="preset-btn" onclick="cronPresetJa('0 0 * * *')">毎日0時</button>
  <button class="preset-btn" onclick="cronPresetJa('0 9 * * 1')">毎週月曜9時</button>
  <button class="preset-btn" onclick="cronPresetJa('0 0 1 * *')">毎月1日0時</button>
  <button class="preset-btn" onclick="cronPresetJa('*/5 * * * *')">5分ごと</button>
  <button class="preset-btn" onclick="cronPresetJa('0 */6 * * *')">6時間ごと</button>
  <button class="preset-btn" onclick="cronPresetJa('30 23 * * *')">毎日23:30</button>
</div>

<!-- Fields -->
<div class="section-title">スケジュールフィールド</div>
<div class="fields-grid">

  <!-- Minute -->
  <div class="field-card">
    <div class="field-name">分</div>
    <div class="field-range">0 – 59</div>
    <select id="sel-min" onchange="cronFieldChangeJa('min')">
      <option value="*">毎分 (*)</option>
      <option value="custom">特定の値</option>
      <option value="range">範囲 (例: 0-30)</option>
      <option value="step">間隔 (例: */5)</option>
    </select>
    <div class="custom-label" id="lbl-min" style="display:none">値 / 式</div>
    <input type="text" id="inp-min" placeholder="例: 0" style="display:none" oninput="cronUpdateJa()">
    <div class="field-preview" id="prev-min">*</div>
  </div>

  <!-- Hour -->
  <div class="field-card">
    <div class="field-name">時</div>
    <div class="field-range">0 – 23</div>
    <select id="sel-hour" onchange="cronFieldChangeJa('hour')">
      <option value="*">毎時 (*)</option>
      <option value="custom">特定の値</option>
      <option value="range">範囲 (例: 9-17)</option>
      <option value="step">間隔 (例: */2)</option>
    </select>
    <div class="custom-label" id="lbl-hour" style="display:none">値 / 式</div>
    <input type="text" id="inp-hour" placeholder="例: 9" style="display:none" oninput="cronUpdateJa()">
    <div class="field-preview" id="prev-hour">*</div>
  </div>

  <!-- Day of Month -->
  <div class="field-card">
    <div class="field-name">日 (月内)</div>
    <div class="field-range">1 – 31</div>
    <select id="sel-dom" onchange="cronFieldChangeJa('dom')">
      <option value="*">毎日 (*)</option>
      <option value="custom">特定の日</option>
      <option value="range">範囲 (例: 1-15)</option>
      <option value="step">間隔 (例: */2)</option>
    </select>
    <div class="custom-label" id="lbl-dom" style="display:none">値 / 式</div>
    <input type="text" id="inp-dom" placeholder="例: 1" style="display:none" oninput="cronUpdateJa()">
    <div class="field-preview" id="prev-dom">*</div>
  </div>

  <!-- Month -->
  <div class="field-card">
    <div class="field-name">月</div>
    <div class="field-range">1 – 12</div>
    <select id="sel-month" onchange="cronFieldChangeJa('month')">
      <option value="*">毎月 (*)</option>
      <option value="custom">特定の月</option>
      <option value="range">範囲 (例: 1-6)</option>
      <option value="step">間隔 (例: */3)</option>
    </select>
    <div class="custom-label" id="lbl-month" style="display:none">値 / 式</div>
    <input type="text" id="inp-month" placeholder="例: 1" style="display:none" oninput="cronUpdateJa()">
    <div class="field-preview" id="prev-month">*</div>
  </div>

  <!-- Day of Week -->
  <div class="field-card">
    <div class="field-name">曜日</div>
    <div class="field-range">0=日 … 6=土</div>
    <select id="sel-dow" onchange="cronFieldChangeJa('dow')">
      <option value="*">毎日 (*)</option>
      <option value="custom">特定の曜日</option>
      <option value="range">範囲 (例: 1-5)</option>
      <option value="step">間隔 (例: */2)</option>
    </select>
    <div class="custom-label" id="lbl-dow" style="display:none">値 / 式</div>
    <input type="text" id="inp-dow" placeholder="例: 1" style="display:none" oninput="cronUpdateJa()">
    <div class="field-preview" id="prev-dow">*</div>
  </div>

</div>

<!-- Next runs -->
<div class="next-runs">
  <div class="next-runs-title">次の5回の実行予定時刻</div>
  <ul class="run-list" id="run-list"><li><span style="color:#64748b">計算中…</span></li></ul>
</div>

<!-- freee CTA -->
<div class="freee-cta">
  <strong>確定申告・会計をもっとラクに？</strong> <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計</a> なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
</div>

</div><!-- #cron-app -->

<script>
(function() {
  var fields = {
    min:   { sel: 'sel-min',   inp: 'inp-min',   lbl: 'lbl-min',   prev: 'prev-min'   },
    hour:  { sel: 'sel-hour',  inp: 'inp-hour',  lbl: 'lbl-hour',  prev: 'prev-hour'  },
    dom:   { sel: 'sel-dom',   inp: 'inp-dom',   lbl: 'lbl-dom',   prev: 'prev-dom'   },
    month: { sel: 'sel-month', inp: 'inp-month', lbl: 'lbl-month', prev: 'prev-month' },
    dow:   { sel: 'sel-dow',   inp: 'inp-dow',   lbl: 'lbl-dow',   prev: 'prev-dow'   }
  };

  var stepHints    = { min:'*/5', hour:'*/2', dom:'*/2', month:'*/3', dow:'*/2' };
  var rangeHints   = { min:'0-30', hour:'9-17', dom:'1-15', month:'1-6', dow:'1-5' };
  var specificHints = { min:'0', hour:'9', dom:'1', month:'1', dow:'1' };

  window.cronFieldChangeJa = function(key) {
    var f = fields[key];
    var mode = document.getElementById(f.sel).value;
    var inp = document.getElementById(f.inp);
    var lbl = document.getElementById(f.lbl);
    if (mode === '*') {
      inp.style.display = 'none'; lbl.style.display = 'none';
    } else {
      inp.style.display = 'block'; lbl.style.display = 'block';
      if (mode === 'step')   inp.placeholder = stepHints[key];
      if (mode === 'range')  inp.placeholder = rangeHints[key];
      if (mode === 'custom') inp.placeholder = specificHints[key];
      inp.value = '';
    }
    cronUpdateJa();
  };

  function getFieldVal(key) {
    var f = fields[key];
    var mode = document.getElementById(f.sel).value;
    if (mode === '*') return '*';
    var raw = document.getElementById(f.inp).value.trim();
    if (!raw) {
      if (mode === 'step')  return stepHints[key];
      if (mode === 'range') return rangeHints[key];
      if (mode === 'custom') return specificHints[key];
    }
    if (mode === 'step') return raw.startsWith('*/') ? raw : '*/' + raw.replace(/[^0-9]/g,'');
    return raw;
  }

  function buildExpr() {
    return [
      getFieldVal('min'),
      getFieldVal('hour'),
      getFieldVal('dom'),
      getFieldVal('month'),
      getFieldVal('dow')
    ].join(' ');
  }

  // ── 日本語 人間語 説明 ────────────────────────────────────────────────
  var MONTHS_JA = ['','1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
  var DAYS_JA   = ['日曜','月曜','火曜','水曜','木曜','金曜','土曜'];

  function describeFieldJa(val, type) {
    if (val === '*') return null;
    if (val.startsWith('*/')) {
      var n = val.slice(2);
      var unit = {min:'分',hour:'時間',dom:'日',month:'ヶ月',dow:'日'}[type];
      return n + unit + 'ごと';
    }
    if (val.includes('-')) {
      var parts = val.split('-');
      if (type === 'dow')   return DAYS_JA[+parts[0]] + 'から' + DAYS_JA[+parts[1]] + 'まで';
      if (type === 'month') return (MONTHS_JA[+parts[0]]||parts[0]) + 'から' + (MONTHS_JA[+parts[1]]||parts[1]) + 'まで';
      return parts[0] + 'から' + parts[1] + 'まで';
    }
    if (type === 'dow')   return DAYS_JA[+val] || val;
    if (type === 'month') return MONTHS_JA[+val] || val;
    if (type === 'dom')   return val + '日';
    if (type === 'hour')  return val + '時';
    if (type === 'min')   return val + '分';
    return val;
  }

  function buildDescJa(expr) {
    var p = expr.split(' ');
    if (p.length !== 5) return '無効な式です';
    var min=p[0], hr=p[1], dom=p[2], mon=p[3], dow=p[4];

    if (expr === '* * * * *') return '毎分実行';
    if (expr === '0 * * * *') return '毎時0分に実行';
    if (expr === '0 0 * * *') return '毎日0時0分に実行';
    if (expr === '0 9 * * 1') return '毎週月曜日の9時0分に実行';
    if (expr === '0 0 1 * *') return '毎月1日の0時0分に実行';

    var parts = [];
    var minDesc  = describeFieldJa(min,  'min');
    var hrDesc   = describeFieldJa(hr,   'hour');
    var domDesc  = describeFieldJa(dom,  'dom');
    var monDesc  = describeFieldJa(mon,  'month');
    var dowDesc  = describeFieldJa(dow,  'dow');

    var when = '';
    if (min === '*' && hr === '*') {
      when = '毎分';
    } else if (/^\d+$/.test(hr) && /^\d+$/.test(min)) {
      when = hr + '時' + String(min).padStart(2,'0') + '分に';
    } else {
      if (hrDesc)  parts.push(hrDesc);
      if (minDesc) parts.push(minDesc);
      when = parts.join(' ') + 'に';
      parts = [];
    }

    var extras = [domDesc, monDesc, dowDesc].filter(Boolean);
    return when + (extras.length ? '、' + extras.join('・') : '') + ' 実行';
  }

  // ── 次の実行時刻 ────────────────────────────────────────────────────
  function matchesCron(d, p) {
    var min=p[0], hr=p[1], dom=p[2], mon=p[3], dow=p[4];
    return matchVal(d.getMinutes(), min, 0,59) &&
           matchVal(d.getHours(),   hr,  0,23) &&
           matchVal(d.getDate(),    dom, 1,31) &&
           matchVal(d.getMonth()+1, mon, 1,12) &&
           matchVal(d.getDay(),     dow, 0,6);
  }

  function matchVal(v, expr, lo, hi) {
    if (expr === '*') return true;
    if (expr.startsWith('*/')) { var step=+expr.slice(2); return v % step === 0; }
    if (expr.includes('-')) { var rp=expr.split('-'); return v>=+rp[0] && v<=+rp[1]; }
    if (expr.includes(',')) { return expr.split(',').some(function(x){ return +x===v; }); }
    return +expr === v;
  }

  function nextRuns(expr, count) {
    var p = expr.split(' ');
    if (p.length !== 5) return [];
    var results = [];
    var d = new Date();
    d.setSeconds(0, 0);
    d.setMinutes(d.getMinutes() + 1);
    var limit = 60*24*400;
    for (var i = 0; i < limit && results.length < count; i++) {
      if (matchesCron(d, p)) results.push(new Date(d));
      d.setMinutes(d.getMinutes() + 1);
    }
    return results;
  }

  function relTimeJa(d) {
    var diff = Math.round((d - Date.now()) / 1000);
    if (diff < 60)    return diff + '秒後';
    if (diff < 3600)  return Math.round(diff/60) + '分後';
    if (diff < 86400) return Math.round(diff/3600) + '時間後';
    return Math.round(diff/86400) + '日後';
  }

  function formatDateJa(d) {
    var wd = ['日','月','火','水','木','金','土'];
    return d.getFullYear() + '/' +
           String(d.getMonth()+1).padStart(2,'0') + '/' +
           String(d.getDate()).padStart(2,'0') +
           '(' + wd[d.getDay()] + ') ' +
           String(d.getHours()).padStart(2,'0') + ':' +
           String(d.getMinutes()).padStart(2,'0');
  }

  // ── メイン更新 ─────────────────────────────────────────────────────────
  window.cronUpdateJa = function() {
    var expr = buildExpr();
    document.getElementById('cron-expr').textContent = expr;

    var keys = ['min','hour','dom','month','dow'];
    var vals = expr.split(' ');
    keys.forEach(function(k, i) {
      document.getElementById(fields[k].prev).textContent = vals[i] || '*';
    });

    document.getElementById('cron-desc').textContent = buildDescJa(expr);

    var runs = nextRuns(expr, 5);
    var ul = document.getElementById('run-list');
    if (runs.length === 0) {
      ul.innerHTML = '<li><span class="error-msg">次の実行時刻を計算できません。式を確認してください。</span></li>';
      return;
    }
    ul.innerHTML = runs.map(function(d, i) {
      return '<li><span class="run-idx">' + (i+1) + '</span>' +
             '<span class="run-time">' + formatDateJa(d) + '</span>' +
             '<span class="run-rel">' + relTimeJa(d) + '</span></li>';
    }).join('');
  };

  window.cronPresetJa = function(expr) {
    var p = expr.split(' ');
    var keys = ['min','hour','dom','month','dow'];
    keys.forEach(function(k, i) {
      var f = fields[k];
      var val = p[i];
      var sel = document.getElementById(f.sel);
      var inp = document.getElementById(f.inp);
      var lbl = document.getElementById(f.lbl);
      if (val === '*') {
        sel.value = '*';
        inp.style.display = 'none'; lbl.style.display = 'none';
      } else if (val.startsWith('*/')) {
        sel.value = 'step';
        inp.style.display = 'block'; lbl.style.display = 'block';
        inp.value = val;
      } else if (val.includes('-')) {
        sel.value = 'range';
        inp.style.display = 'block'; lbl.style.display = 'block';
        inp.value = val;
      } else {
        sel.value = 'custom';
        inp.style.display = 'block'; lbl.style.display = 'block';
        inp.value = val;
      }
    });
    cronUpdateJa();
  };

  window.cronCopyJa = function() {
    var expr = document.getElementById('cron-expr').textContent;
    var btn = document.getElementById('copy-btn');
    if (navigator.clipboard) {
      navigator.clipboard.writeText(expr).then(function() {
        btn.textContent = 'コピー完了!'; btn.classList.add('copied');
        setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = expr; document.body.appendChild(ta); ta.select();
      document.execCommand('copy'); document.body.removeChild(ta);
      btn.textContent = 'コピー完了!'; btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
    }
  };

  // 初期化
  cronUpdateJa();
})();
</script>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
