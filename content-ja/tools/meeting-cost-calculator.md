---
title: "会議コスト計算ツール"
date: 2025-05-16
description: "無料の会議コスト計算ツール。参加者の人件費からリアルタイムで会議のコストを表示。時間あたりのコスト意識を高める、会員登録不要。"
categories: ["無料ツール"]
slug: "meeting-cost-calculator"
ShowToc: false
cover:
  image: "/images/covers/meeting-cost-calculator-ja.png"
  alt: "会議コスト計算ツール"
---

<div id="mc-app">
<style>
#mc-app *,#mc-app *::before,#mc-app *::after{box-sizing:border-box;margin:0;padding:0;}
#mc-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI','Hiragino Sans','Noto Sans JP',sans-serif;color:#1e293b;background:#f8fafc;border-radius:14px;padding:28px 24px;max-width:760px;margin:0 auto;}
#mc-app h2{font-size:1.35rem;font-weight:700;color:#0f172a;margin-bottom:6px;}
#mc-app h3{font-size:1.05rem;font-weight:700;color:#0f172a;margin-bottom:10px;}
#mc-app p.mc-sub{font-size:0.88rem;color:#64748b;margin-bottom:20px;}

/* Section cards */
#mc-app .mc-card{background:#fff;border:1px solid #e2e8f0;border-radius:10px;padding:20px 18px;margin-bottom:18px;}

/* Participant rows */
#mc-app .mc-participant-row{display:flex;align-items:center;gap:8px;margin-bottom:10px;flex-wrap:wrap;}
#mc-app .mc-participant-row input[type="text"],
#mc-app .mc-participant-row input[type="number"],
#mc-app .mc-participant-row select{height:38px;border:1px solid #cbd5e1;border-radius:7px;padding:0 10px;font-size:14px;color:#1e293b;background:#f8fafc;outline:none;transition:border-color .15s;}
#mc-app .mc-participant-row input[type="text"]{width:130px;}
#mc-app .mc-participant-row input[type="number"]{width:110px;}
#mc-app .mc-participant-row select{width:160px;}
#mc-app .mc-participant-row input:focus,
#mc-app .mc-participant-row select:focus{border-color:#3b82f6;background:#fff;}
#mc-app .mc-participant-row label{font-size:12px;color:#64748b;white-space:nowrap;}
#mc-app .mc-participant-row .mc-rate-label{font-size:13px;color:#475569;min-width:70px;white-space:nowrap;}
#mc-app .mc-btn-del{background:none;border:none;cursor:pointer;color:#94a3b8;font-size:18px;line-height:1;padding:4px 6px;border-radius:5px;transition:color .15s;}
#mc-app .mc-btn-del:hover{color:#ef4444;}

/* Buttons */
#mc-app .mc-btn{display:inline-flex;align-items:center;gap:6px;padding:9px 18px;border:none;border-radius:8px;font-size:14px;font-weight:600;cursor:pointer;transition:background .15s,opacity .15s;}
#mc-app .mc-btn:disabled{opacity:.5;cursor:not-allowed;}
#mc-app .mc-btn-primary{background:#3b82f6;color:#fff;}
#mc-app .mc-btn-primary:hover:not(:disabled){background:#2563eb;}
#mc-app .mc-btn-success{background:#22c55e;color:#fff;}
#mc-app .mc-btn-success:hover:not(:disabled){background:#16a34a;}
#mc-app .mc-btn-warning{background:#f59e0b;color:#fff;}
#mc-app .mc-btn-warning:hover:not(:disabled){background:#d97706;}
#mc-app .mc-btn-ghost{background:#f1f5f9;color:#475569;border:1px solid #e2e8f0;}
#mc-app .mc-btn-ghost:hover:not(:disabled){background:#e2e8f0;}
#mc-app .mc-btn-danger{background:#ef4444;color:#fff;}
#mc-app .mc-btn-danger:hover:not(:disabled){background:#dc2626;}
#mc-app .mc-btn-sm{padding:6px 12px;font-size:13px;}

/* Timer display */
#mc-app .mc-timer-display{text-align:center;padding:24px 16px;background:linear-gradient(135deg,#1e293b 0%,#334155 100%);border-radius:12px;margin-bottom:16px;}
#mc-app .mc-timer-time{font-size:3rem;font-weight:800;color:#f8fafc;letter-spacing:2px;font-variant-numeric:tabular-nums;}
#mc-app .mc-timer-cost{font-size:1.6rem;font-weight:700;color:#34d399;margin-top:4px;letter-spacing:1px;}
#mc-app .mc-timer-label{font-size:12px;color:#94a3b8;margin-top:2px;}
#mc-app .mc-timer-actions{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:4px;}

/* Estimate section */
#mc-app .mc-estimate-row{display:flex;align-items:center;gap:10px;flex-wrap:wrap;margin-bottom:14px;}
#mc-app .mc-estimate-row label{font-size:14px;color:#475569;white-space:nowrap;}
#mc-app .mc-estimate-row input[type="number"]{height:38px;border:1px solid #cbd5e1;border-radius:7px;padding:0 10px;font-size:14px;color:#1e293b;background:#f8fafc;outline:none;width:100px;}
#mc-app .mc-estimate-row input:focus{border-color:#3b82f6;background:#fff;}

/* Results */
#mc-app .mc-results-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:12px;margin-bottom:14px;}
#mc-app .mc-result-card{background:#f1f5f9;border-radius:9px;padding:14px 12px;text-align:center;}
#mc-app .mc-result-card .mc-rc-label{font-size:12px;color:#64748b;margin-bottom:4px;}
#mc-app .mc-result-card .mc-rc-value{font-size:1.3rem;font-weight:800;color:#0f172a;}
#mc-app .mc-result-card.mc-rc-highlight{background:linear-gradient(135deg,#eff6ff 0%,#dbeafe 100%);border:1.5px solid #bfdbfe;}
#mc-app .mc-result-card.mc-rc-highlight .mc-rc-value{color:#1d4ed8;}

/* Comparisons */
#mc-app .mc-compare-list{list-style:none;display:flex;flex-direction:column;gap:7px;}
#mc-app .mc-compare-list li{display:flex;align-items:center;gap:8px;font-size:14px;color:#475569;}
#mc-app .mc-compare-list li .mc-compare-icon{font-size:18px;width:26px;text-align:center;}
#mc-app .mc-compare-list li .mc-compare-count{font-weight:700;color:#1e293b;min-width:60px;}

/* Participant summary badges */
#mc-app .mc-badge-list{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:12px;}
#mc-app .mc-badge{background:#e0f2fe;color:#0369a1;border-radius:20px;padding:3px 12px;font-size:12px;font-weight:600;}

/* Section divider label */
#mc-app .mc-section-label{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em;color:#94a3b8;margin-bottom:10px;}

/* Responsive */
@media(max-width:480px){
  #mc-app{padding:18px 14px;}
  #mc-app .mc-timer-time{font-size:2.2rem;}
  #mc-app .mc-timer-cost{font-size:1.2rem;}
  #mc-app .mc-participant-row input[type="text"]{width:100%;}
  #mc-app .mc-participant-row{flex-direction:column;align-items:flex-start;}
}
</style>

<h2>会議コスト計算ツール</h2>
<p class="mc-sub">参加者の役職・時給を入力してリアルタイムに会議コストを計算。コスト意識を高めて生産性の高い会議を実現しましょう。</p>

<!-- Section 1: Participants -->
<div class="mc-card">
  <h3>参加者を追加</h3>
  <div id="mc-participant-list"></div>
  <div style="display:flex;gap:8px;flex-wrap:wrap;margin-top:4px;">
    <button class="mc-btn mc-btn-ghost mc-btn-sm" onclick="mcAddParticipant()">＋ 参加者を追加</button>
    <button class="mc-btn mc-btn-ghost mc-btn-sm" onclick="mcClearParticipants()">全員削除</button>
  </div>
</div>

<!-- Section 2: Timer -->
<div class="mc-card">
  <h3>会議タイマー</h3>
  <div class="mc-badge-list" id="mc-attendee-badges"></div>
  <div class="mc-timer-display">
    <div class="mc-timer-time" id="mc-timer-elapsed">00:00:00</div>
    <div class="mc-timer-cost" id="mc-timer-cost">¥0</div>
    <div class="mc-timer-label">累積コスト（リアルタイム）</div>
  </div>
  <div class="mc-timer-actions">
    <button class="mc-btn mc-btn-success" id="mc-btn-start" onclick="mcStartTimer()">▶ 開始</button>
    <button class="mc-btn mc-btn-warning" id="mc-btn-pause" onclick="mcPauseTimer()" disabled>⏸ 一時停止</button>
    <button class="mc-btn mc-btn-danger" id="mc-btn-reset" onclick="mcResetTimer()" disabled>↺ リセット</button>
  </div>
</div>

<!-- Section 3: Estimate -->
<div class="mc-card">
  <h3>事前コスト見積</h3>
  <div class="mc-estimate-row">
    <label for="mc-est-hours">予定時間</label>
    <input type="number" id="mc-est-hours" value="1" min="0" max="24" step="0.5" oninput="mcUpdateEstimate()">
    <label>時間</label>
    <input type="number" id="mc-est-minutes" value="0" min="0" max="59" step="5" oninput="mcUpdateEstimate()">
    <label>分</label>
    <button class="mc-btn mc-btn-primary mc-btn-sm" onclick="mcUpdateEstimate()">計算</button>
  </div>
  <div id="mc-estimate-result" style="display:none;">
    <div id="mc-results-area"></div>
  </div>
  <div id="mc-estimate-placeholder" style="font-size:14px;color:#94a3b8;padding:8px 0;">
    参加者を追加してから予定時間を入力してください。
  </div>
</div>

<script>
(function(){
  'use strict';

  // --- State ---
  var participants = [];
  var pidCounter = 0;
  var timerInterval = null;
  var timerElapsedMs = 0;
  var timerStartedAt = null;
  var timerRunning = false;

  var PRESETS = [
    {label:'新人（¥2,000/h）', rate:2000},
    {label:'中堅（¥3,500/h）', rate:3500},
    {label:'シニア（¥5,000/h）', rate:5000},
    {label:'管理職（¥7,000/h）', rate:7000},
    {label:'役員（¥10,000/h）', rate:10000},
    {label:'カスタム', rate:null}
  ];

  var COMPARISONS = [
    {icon:'☕',name:'スタバのコーヒー',price:700},
    {icon:'🍱',name:'ランチ定食',price:900},
    {icon:'📚',name:'ビジネス書',price:1800},
    {icon:'🍕',name:'ピザ（Mサイズ）',price:2500},
    {icon:'🎬',name:'映画チケット',price:2000},
    {icon:'🎮',name:'スマホゲーム課金',price:3000},
    {icon:'🍣',name:'回転寿司（一人前）',price:2000},
    {icon:'✈️',name:'新幹線自由席（東京-大阪）',price:13870},
    {icon:'💻',name:'Amazonプライム月額',price:600},
    {icon:'🏨',name:'ビジネスホテル1泊',price:8000}
  ];

  // --- Participants ---
  function getTotalHourlyRate(){
    return participants.reduce(function(s,p){ return s + (p.rate||0); }, 0);
  }

  window.mcAddParticipant = function(){
    var id = ++pidCounter;
    participants.push({id:id, name:'参加者'+id, rate:3500, preset:1});
    renderParticipants();
    updateBadges();
    mcUpdateEstimate();
  };

  window.mcClearParticipants = function(){
    participants = [];
    renderParticipants();
    updateBadges();
    mcUpdateEstimate();
  };

  window.mcRemoveParticipant = function(id){
    participants = participants.filter(function(p){ return p.id !== id; });
    renderParticipants();
    updateBadges();
    mcUpdateEstimate();
  };

  window.mcOnPresetChange = function(id, selectEl){
    var idx = parseInt(selectEl.value, 10);
    var p = participants.find(function(p){ return p.id === id; });
    if(!p) return;
    p.preset = idx;
    if(PRESETS[idx].rate !== null){
      p.rate = PRESETS[idx].rate;
      var rateInput = document.getElementById('mc-rate-'+id);
      var annualInput = document.getElementById('mc-annual-'+id);
      if(rateInput) rateInput.value = p.rate;
      if(annualInput) annualInput.value = '';
    }
    updateBadges();
    mcUpdateEstimate();
  };

  window.mcOnRateChange = function(id, val){
    var p = participants.find(function(p){ return p.id === id; });
    if(!p) return;
    var v = parseFloat(val)||0;
    p.rate = v;
    var annualInput = document.getElementById('mc-annual-'+id);
    if(annualInput) annualInput.value = '';
    var selectEl = document.getElementById('mc-preset-'+id);
    if(selectEl) selectEl.value = PRESETS.length - 1; // custom
    updateBadges();
    mcUpdateEstimate();
  };

  window.mcOnAnnualChange = function(id, val){
    var p = participants.find(function(p){ return p.id === id; });
    if(!p) return;
    var annual = parseFloat(val)||0;
    // annual salary / 12 months / 20 working days / 8 hours * 1.3 (social insurance factor)
    var hourly = Math.round(annual * 10000 / 12 / 20 / 8 * 1.3);
    p.rate = hourly;
    var rateInput = document.getElementById('mc-rate-'+id);
    if(rateInput) rateInput.value = hourly;
    var selectEl = document.getElementById('mc-preset-'+id);
    if(selectEl) selectEl.value = PRESETS.length - 1;
    updateBadges();
    mcUpdateEstimate();
  };

  window.mcOnNameChange = function(id, val){
    var p = participants.find(function(p){ return p.id === id; });
    if(p) p.name = val || ('参加者'+id);
    updateBadges();
  };

  function renderParticipants(){
    var container = document.getElementById('mc-participant-list');
    if(!container) return;
    if(participants.length === 0){
      container.innerHTML = '<p style="font-size:14px;color:#94a3b8;padding:6px 0 10px;">まだ参加者がいません。「参加者を追加」ボタンで追加してください。</p>';
      return;
    }
    var html = '';
    participants.forEach(function(p){
      var presetOpts = PRESETS.map(function(pr,i){
        return '<option value="'+i+'"'+(p.preset===i?' selected':'')+'>'+pr.label+'</option>';
      }).join('');
      html += '<div class="mc-participant-row" id="mc-row-'+p.id+'">';
      html += '<input type="text" placeholder="名前・役職" value="'+escHtml(p.name)+'" oninput="mcOnNameChange('+p.id+',this.value)" style="width:120px;">';
      html += '<select id="mc-preset-'+p.id+'" onchange="mcOnPresetChange('+p.id+',this)">'+presetOpts+'</select>';
      html += '<label>時給</label>';
      html += '<input type="number" id="mc-rate-'+p.id+'" value="'+p.rate+'" min="0" max="99999" step="100" oninput="mcOnRateChange('+p.id+',this.value)" placeholder="時給(円)">';
      html += '<span class="mc-rate-label">円/h</span>';
      html += '<label style="margin-left:4px;">年収</label>';
      html += '<input type="number" id="mc-annual-'+p.id+'" min="0" max="9999" step="50" placeholder="万円" oninput="mcOnAnnualChange('+p.id+',this.value)" style="width:90px;">';
      html += '<span class="mc-rate-label">万円→換算</span>';
      html += '<button class="mc-btn-del" onclick="mcRemoveParticipant('+p.id+')" title="削除">×</button>';
      html += '</div>';
    });
    container.innerHTML = html;
  }

  function updateBadges(){
    var el = document.getElementById('mc-attendee-badges');
    if(!el) return;
    if(participants.length === 0){
      el.innerHTML = '<span style="font-size:13px;color:#94a3b8;">参加者を追加するとここに表示されます</span>';
      return;
    }
    el.innerHTML = participants.map(function(p){
      return '<span class="mc-badge">'+escHtml(p.name)+' ¥'+fmt(p.rate)+'/h</span>';
    }).join('');
  }

  // --- Timer ---
  function formatMs(ms){
    var totalSec = Math.floor(ms / 1000);
    var h = Math.floor(totalSec / 3600);
    var m = Math.floor((totalSec % 3600) / 60);
    var s = totalSec % 60;
    return pad2(h)+':'+pad2(m)+':'+pad2(s);
  }

  function tickTimer(){
    timerElapsedMs = Date.now() - timerStartedAt;
    var elapsedSec = timerElapsedMs / 1000;
    var totalRate = getTotalHourlyRate();
    var cost = Math.floor((totalRate / 3600) * elapsedSec);
    document.getElementById('mc-timer-elapsed').textContent = formatMs(timerElapsedMs);
    document.getElementById('mc-timer-cost').textContent = '¥' + fmt(cost);
  }

  window.mcStartTimer = function(){
    if(participants.length === 0){
      alert('先に参加者を追加してください。');
      return;
    }
    if(timerRunning) return;
    timerRunning = true;
    timerStartedAt = Date.now() - timerElapsedMs;
    timerInterval = setInterval(tickTimer, 250);
    document.getElementById('mc-btn-start').disabled = true;
    document.getElementById('mc-btn-pause').disabled = false;
    document.getElementById('mc-btn-reset').disabled = false;
  };

  window.mcPauseTimer = function(){
    if(!timerRunning) return;
    timerRunning = false;
    clearInterval(timerInterval);
    timerInterval = null;
    document.getElementById('mc-btn-start').disabled = false;
    document.getElementById('mc-btn-pause').disabled = true;
  };

  window.mcResetTimer = function(){
    timerRunning = false;
    clearInterval(timerInterval);
    timerInterval = null;
    timerElapsedMs = 0;
    timerStartedAt = null;
    document.getElementById('mc-timer-elapsed').textContent = '00:00:00';
    document.getElementById('mc-timer-cost').textContent = '¥0';
    document.getElementById('mc-btn-start').disabled = false;
    document.getElementById('mc-btn-pause').disabled = true;
    document.getElementById('mc-btn-reset').disabled = true;
  };

  // --- Estimate ---
  window.mcUpdateEstimate = function(){
    var phEl = document.getElementById('mc-estimate-placeholder');
    var resEl = document.getElementById('mc-estimate-result');
    var areaEl = document.getElementById('mc-results-area');
    if(!phEl || !resEl || !areaEl) return;

    var totalRate = getTotalHourlyRate();
    if(participants.length === 0 || totalRate === 0){
      phEl.style.display = '';
      resEl.style.display = 'none';
      return;
    }

    var hours = parseFloat(document.getElementById('mc-est-hours').value)||0;
    var minutes = parseFloat(document.getElementById('mc-est-minutes').value)||0;
    var totalMinutes = hours * 60 + minutes;
    if(totalMinutes <= 0){
      phEl.style.display = '';
      resEl.style.display = 'none';
      return;
    }

    phEl.style.display = 'none';
    resEl.style.display = '';

    var totalHours = totalMinutes / 60;
    var totalCost = Math.round(totalRate * totalHours);
    var perMinuteCost = Math.round(totalCost / totalMinutes);
    var perPersonCost = participants.length > 0 ? Math.round(totalCost / participants.length) : 0;

    // Comparisons
    var compareHtml = '';
    var affordableItems = COMPARISONS.filter(function(c){ return totalCost >= c.price; });
    if(affordableItems.length > 0){
      compareHtml = '<ul class="mc-compare-list">';
      affordableItems.forEach(function(c){
        var count = Math.floor(totalCost / c.price);
        compareHtml += '<li><span class="mc-compare-icon">'+c.icon+'</span><span class="mc-compare-count">'+count+'個分</span><span>'+c.name+'（¥'+fmt(c.price)+'）</span></li>';
      });
      compareHtml += '</ul>';
    } else {
      compareHtml = '<p style="font-size:14px;color:#94a3b8;">もっと長い会議で比較が表示されます。</p>';
    }

    areaEl.innerHTML = ''
      + '<div class="mc-results-grid">'
      + mcResultCard('合計コスト','¥'+fmt(totalCost),true)
      + mcResultCard('1分あたり','¥'+fmt(perMinuteCost)+'/分',false)
      + mcResultCard('1人あたり','¥'+fmt(perPersonCost),false)
      + mcResultCard('参加人数',participants.length+'名',false)
      + '</div>'
      + '<div style="margin-top:4px;">'
      + '<p class="mc-section-label">このコストで買えるもの</p>'
      + compareHtml
      + '</div>';
  };

  function mcResultCard(label, value, highlight){
    return '<div class="mc-result-card'+(highlight?' mc-rc-highlight':'')+'"><div class="mc-rc-label">'+label+'</div><div class="mc-rc-value">'+value+'</div></div>';
  }

  // --- Utilities ---
  function fmt(n){
    return Number(n).toLocaleString('ja-JP');
  }
  function pad2(n){
    return n < 10 ? '0'+n : ''+n;
  }
  function escHtml(s){
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  // --- Init ---
  renderParticipants();
  updateBadges();
  // Add two default participants
  window.mcAddParticipant();
  window.mcAddParticipant();

})();
</script>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の経費・人件費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、経費精算・給与計算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

</div>

---

> ポモドーロで集中 → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)
> 手取り額を計算 → [手取り計算ツール](/ja/tools/salary-tedori-calculator/)
> 投資利益率を計算 → [ROI計算ツール](/ja/tools/roi-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
