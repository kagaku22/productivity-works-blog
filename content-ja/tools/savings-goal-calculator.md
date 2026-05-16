---
title: "貯金目標計算ツール｜目標金額までの期間・毎月の積立額を自動算出【無料】"
date: 2025-05-16
description: "無料の貯金目標計算ツール。複利シミュレーション・月額積立額・目標達成期間を計算。ビジュアル進捗表示付き。"
categories: ["無料ツール"]
slug: "savings-goal-calculator"
ShowToc: false
cover:
  image: "/images/covers/savings-goal-calculator-ja.png"
  alt: "貯金目標計算ツール"
---

<div id="sg-app">
<style>
#sg-app *,#sg-app *::before,#sg-app *::after{box-sizing:border-box;margin:0;padding:0}
#sg-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Kaku Gothic ProN','Noto Sans JP','Segoe UI',sans-serif;color:#1e293b;max-width:780px;margin:0 auto;padding:0 4px}
#sg-app h2.sg-h{font-size:1.3rem;font-weight:700;color:#0f172a;margin-bottom:6px}
#sg-app p.sg-sub{font-size:.9rem;color:#64748b;margin-bottom:18px}
#sg-app .sg-card{background:#fff;border:1.5px solid #e2e8f0;border-radius:12px;padding:22px 22px 18px;margin-bottom:20px;box-shadow:0 1px 4px rgba(0,0,0,.06)}
#sg-app .sg-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media(max-width:540px){#sg-app .sg-grid{grid-template-columns:1fr}}
#sg-app .sg-field{display:flex;flex-direction:column;gap:5px}
#sg-app .sg-field label{font-size:.82rem;font-weight:600;color:#475569}
#sg-app .sg-field input[type=number],#sg-app .sg-field select{border:1.5px solid #cbd5e1;border-radius:8px;padding:9px 12px;font-size:.95rem;color:#0f172a;background:#f8fafc;width:100%;outline:none;transition:border-color .2s}
#sg-app .sg-field input[type=number]:focus,#sg-app .sg-field select:focus{border-color:#3b82f6;background:#fff}
#sg-app .sg-mode-toggle{display:flex;gap:0;border:1.5px solid #cbd5e1;border-radius:9px;overflow:hidden;margin-bottom:16px}
#sg-app .sg-mode-toggle button{flex:1;padding:9px 8px;border:none;background:#f8fafc;color:#64748b;font-size:.83rem;font-weight:600;cursor:pointer;transition:background .18s,color .18s}
#sg-app .sg-mode-toggle button.sg-active{background:#3b82f6;color:#fff}
#sg-app .sg-btn{display:inline-flex;align-items:center;justify-content:center;gap:6px;padding:11px 28px;background:linear-gradient(135deg,#2563eb 0%,#3b82f6 100%);color:#fff;border:none;border-radius:9px;font-size:.97rem;font-weight:700;cursor:pointer;width:100%;margin-top:4px;transition:opacity .18s}
#sg-app .sg-btn:hover{opacity:.9}
#sg-app .sg-result-card{background:linear-gradient(135deg,#eff6ff 0%,#dbeafe 100%);border:1.5px solid #bfdbfe;border-radius:12px;padding:22px;margin-bottom:20px}
#sg-app .sg-result-headline{font-size:1.5rem;font-weight:800;color:#1d4ed8;margin-bottom:4px}
#sg-app .sg-result-sub{font-size:.9rem;color:#3730a3;margin-bottom:18px}
#sg-app .sg-summary-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:18px}
@media(max-width:480px){#sg-app .sg-summary-grid{grid-template-columns:1fr 1fr}}
#sg-app .sg-stat{background:#fff;border-radius:9px;padding:12px 10px;text-align:center;border:1px solid #bfdbfe}
#sg-app .sg-stat-val{font-size:1.05rem;font-weight:800;color:#1d4ed8;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
#sg-app .sg-stat-lbl{font-size:.72rem;color:#64748b;margin-top:2px;display:block}
#sg-app .sg-progress-wrap{margin-bottom:18px}
#sg-app .sg-progress-lbl{display:flex;justify-content:space-between;font-size:.8rem;color:#64748b;margin-bottom:5px}
#sg-app .sg-progress-track{height:20px;background:#dbeafe;border-radius:10px;overflow:hidden}
#sg-app .sg-progress-bar{height:100%;border-radius:10px;background:linear-gradient(90deg,#2563eb,#60a5fa);transition:width .5s ease}
#sg-app .sg-milestone-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
#sg-app .sg-info-tag{background:#eff6ff;color:#1d4ed8;border-radius:6px;padding:4px 10px;font-size:.78rem;font-weight:600}
#sg-app .sg-chart-wrap{margin-bottom:8px}
#sg-app .sg-chart-title{font-size:.85rem;font-weight:700;color:#374151;margin-bottom:8px}
#sg-app canvas.sg-canvas{width:100%;border-radius:8px;display:block}
#sg-app .sg-legend{display:flex;gap:16px;margin-top:7px;flex-wrap:wrap}
#sg-app .sg-legend-item{display:flex;align-items:center;gap:5px;font-size:.78rem;color:#64748b}
#sg-app .sg-legend-dot{width:12px;height:12px;border-radius:3px;flex-shrink:0}
#sg-app .sg-hidden{display:none}
#sg-app .sg-error{background:#fef2f2;border:1.5px solid #fca5a5;border-radius:8px;padding:10px 14px;color:#b91c1c;font-size:.87rem;margin-top:8px}
</style>

<div class="sg-card">
  <h2 class="sg-h">貯金目標計算ツール</h2>
  <p class="sg-sub">目標達成までの期間、または毎月の必要積立額を複利込みでシミュレーションします。</p>

  <div class="sg-mode-toggle">
    <button class="sg-active" id="sg-btn-time" onclick="sgSetMode('time')">何ヶ月で達成できる？</button>
    <button id="sg-btn-monthly" onclick="sgSetMode('monthly')">毎月いくら積み立てる？</button>
  </div>

  <div class="sg-grid">
    <div class="sg-field">
      <label for="sg-goal">目標金額（円）</label>
      <input type="number" id="sg-goal" value="1000000" min="0" step="10000">
    </div>
    <div class="sg-field">
      <label for="sg-current">現在の貯金（円）</label>
      <input type="number" id="sg-current" value="100000" min="0" step="10000">
    </div>
    <div class="sg-field" id="sg-monthly-wrap">
      <label for="sg-monthly">毎月の積立額（円）</label>
      <input type="number" id="sg-monthly" value="30000" min="0" step="1000">
    </div>
    <div class="sg-field">
      <label for="sg-rate">年利（%）</label>
      <input type="number" id="sg-rate" value="3" min="0" max="30" step="0.1">
    </div>
    <div class="sg-field sg-hidden" id="sg-years-wrap">
      <label for="sg-years">目標期間（年）</label>
      <input type="number" id="sg-years" value="5" min="1" max="50" step="1">
    </div>
    <div class="sg-field">
      <label for="sg-compound">複利計算の頻度</label>
      <select id="sg-compound">
        <option value="12" selected>毎月</option>
        <option value="4">四半期ごと</option>
        <option value="2">半年ごと</option>
        <option value="1">年1回</option>
      </select>
    </div>
  </div>
  <button class="sg-btn" onclick="sgCalculate()">&#9654; 計算する</button>
  <div id="sg-error" class="sg-error sg-hidden"></div>
</div>

<div id="sg-results" class="sg-hidden">
  <div class="sg-result-card">
    <div id="sg-headline" class="sg-result-headline"></div>
    <div id="sg-result-sub" class="sg-result-sub"></div>
    <div class="sg-summary-grid">
      <div class="sg-stat">
        <span class="sg-stat-val" id="sg-stat-principal"></span>
        <span class="sg-stat-lbl">総積立額</span>
      </div>
      <div class="sg-stat">
        <span class="sg-stat-val" id="sg-stat-interest"></span>
        <span class="sg-stat-lbl">利息合計</span>
      </div>
      <div class="sg-stat">
        <span class="sg-stat-val" id="sg-stat-total"></span>
        <span class="sg-stat-lbl">最終残高</span>
      </div>
    </div>
    <div class="sg-progress-wrap">
      <div class="sg-progress-lbl">
        <span>目標に対する現在の進捗</span>
        <span id="sg-pct-lbl">0%</span>
      </div>
      <div class="sg-progress-track">
        <div class="sg-progress-bar" id="sg-bar" style="width:0%"></div>
      </div>
    </div>
    <div class="sg-milestone-row" id="sg-milestones"></div>
  </div>

  <div class="sg-card">
    <div class="sg-chart-title">元本 vs. 利息の推移（積み上げグラフ）</div>
    <canvas class="sg-canvas" id="sg-chart" height="220"></canvas>
    <div class="sg-legend">
      <div class="sg-legend-item"><div class="sg-legend-dot" style="background:#2563eb"></div>元本（積立額）</div>
      <div class="sg-legend-item"><div class="sg-legend-dot" style="background:#60a5fa"></div>利息</div>
    </div>
  </div>
</div>

<script>
(function(){
  var sgMode = 'time';

  window.sgSetMode = function(m) {
    sgMode = m;
    document.getElementById('sg-btn-time').className = m === 'time' ? 'sg-active' : '';
    document.getElementById('sg-btn-monthly').className = m === 'monthly' ? 'sg-active' : '';
    var mw = document.getElementById('sg-monthly-wrap');
    var yw = document.getElementById('sg-years-wrap');
    mw.className = m === 'time' ? 'sg-field' : 'sg-field sg-hidden';
    yw.className = m === 'monthly' ? 'sg-field' : 'sg-field sg-hidden';
    document.getElementById('sg-results').className = 'sg-hidden';
    document.getElementById('sg-error').className = 'sg-error sg-hidden';
  };

  function fmtJPY(n) {
    if (Math.abs(n) >= 1e8) return (n / 1e8).toFixed(2) + '億円';
    if (Math.abs(n) >= 1e4) return Math.round(n).toLocaleString('ja-JP') + '円';
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }

  function getSnaps(current, monthly, rateAnnual, months, freq) {
    var r = rateAnnual / 100 / freq;
    var periodsPerMonth = freq / 12;
    var bal = current;
    var totalContrib = current;
    var snaps = [];
    for (var m = 0; m < months; m++) {
      bal = bal * Math.pow(1 + r, 1 / periodsPerMonth) + monthly;
      totalContrib += monthly;
      snaps.push({ month: m + 1, balance: bal, principal: totalContrib, interest: Math.max(0, bal - totalContrib) });
    }
    return snaps;
  }

  window.sgCalculate = function() {
    var errEl = document.getElementById('sg-error');
    errEl.className = 'sg-error sg-hidden';

    var goal    = parseFloat(document.getElementById('sg-goal').value) || 0;
    var current = parseFloat(document.getElementById('sg-current').value) || 0;
    var rate    = parseFloat(document.getElementById('sg-rate').value) || 0;
    var freq    = parseInt(document.getElementById('sg-compound').value) || 12;

    function showErr(msg) { errEl.textContent = msg; errEl.className = 'sg-error'; }

    if (goal <= 0) { showErr('目標金額を正しく入力してください。'); return; }
    if (current >= goal) { showErr('現在の貯金がすでに目標額を達成しています！'); return; }

    var months, monthly, snaps;

    if (sgMode === 'time') {
      monthly = parseFloat(document.getElementById('sg-monthly').value) || 0;
      if (monthly <= 0 && rate <= 0) { showErr('毎月の積立額または年利を入力してください。'); return; }
      var r = rate / 100 / freq;
      var bal = current;
      months = 0;
      while (bal < goal && months < 600) {
        bal = bal * Math.pow(1 + r, freq / 12) + monthly;
        months++;
      }
      if (bal < goal) { showErr('50年以内に目標を達成できません。積立額や年利を見直してください。'); return; }
      snaps = getSnaps(current, monthly, rate, months, freq);
    } else {
      var years = parseFloat(document.getElementById('sg-years').value) || 0;
      if (years <= 0) { showErr('目標期間（年）を正しく入力してください。'); return; }
      months = Math.round(years * 12);
      var r = rate / 100 / freq;
      var totalPeriods = freq * years;
      var growthFactor = Math.pow(1 + r, totalPeriods);
      if (rate === 0) {
        monthly = (goal - current) / months;
      } else {
        var annuityFactor = (growthFactor - 1) / r * (freq / 12);
        monthly = (goal - current * growthFactor) / annuityFactor;
      }
      if (monthly < 0) { showErr('現在の貯金が複利で目標額を超える見込みです。追加積立は不要です。'); return; }
      snaps = getSnaps(current, monthly, rate, months, freq);
    }

    var last = snaps[snaps.length - 1];
    var totalContrib = current + monthly * months;
    var totalInterest = Math.max(0, last.balance - totalContrib);

    // Headline
    var yrs = Math.floor(months / 12), mos = months % 12;
    var timeStr = (yrs > 0 ? yrs + '年' : '') + (mos > 0 ? mos + 'ヶ月' : '');
    if (!timeStr) timeStr = '1ヶ月未満';
    document.getElementById('sg-headline').textContent = sgMode === 'time'
      ? timeStr + 'で目標達成！'
      : '毎月 ' + fmtJPY(monthly) + ' の積立が必要';
    document.getElementById('sg-result-sub').textContent = sgMode === 'time'
      ? '毎月' + fmtJPY(monthly) + '積立・年利' + rate + '%の場合'
      : fmtJPY(goal) + 'を' + (yrs > 0 ? yrs + '年' : '') + (mos > 0 ? mos + 'ヶ月' : '') + '後に達成するために必要な月額';

    document.getElementById('sg-stat-principal').textContent = fmtJPY(totalContrib);
    document.getElementById('sg-stat-interest').textContent = fmtJPY(totalInterest);
    document.getElementById('sg-stat-total').textContent = fmtJPY(last.balance);

    // Progress bar
    var pct = Math.min(100, (current / goal) * 100);
    document.getElementById('sg-bar').style.width = pct.toFixed(1) + '%';
    document.getElementById('sg-pct-lbl').textContent = pct.toFixed(1) + '%';

    // Milestone tags
    var msEl = document.getElementById('sg-milestones');
    msEl.innerHTML = '';
    [25, 50, 75, 100].forEach(function(pctTarget) {
      var target = goal * pctTarget / 100;
      var idx = -1;
      for (var i = 0; i < snaps.length; i++) {
        if (snaps[i].balance >= target) { idx = i; break; }
      }
      if (idx >= 0) {
        var mo = idx + 1;
        var my = Math.floor(mo / 12), mm = mo % 12;
        var tag = document.createElement('span');
        tag.className = 'sg-info-tag';
        tag.textContent = pctTarget + '%: ' + (my > 0 ? my + '年' : '') + (mm > 0 ? mm + 'ヶ月' : (my > 0 ? '' : '1ヶ月未満'));
        msEl.appendChild(tag);
      }
    });

    // Chart
    sgDrawChart(snaps);
    document.getElementById('sg-results').className = '';
  };

  function sgDrawChart(snaps) {
    var canvas = document.getElementById('sg-chart');
    var container = canvas.parentElement;
    var W = container.offsetWidth - 44;
    if (W < 100) W = 300;
    canvas.width = W;
    canvas.height = 220;
    var ctx = canvas.getContext('2d');
    ctx.clearRect(0, 0, W, 220);

    var steps = Math.min(12, snaps.length);
    var indices = [];
    for (var i = 0; i < steps; i++) {
      indices.push(Math.round(i * (snaps.length - 1) / Math.max(1, steps - 1)));
    }
    var data = indices.map(function(i) { return snaps[i]; });

    var maxVal = 0;
    data.forEach(function(d) { if (d.balance > maxVal) maxVal = d.balance; });
    if (maxVal === 0) maxVal = 1;

    var pad = { top: 16, right: 12, bottom: 38, left: 68 };
    var cw = W - pad.left - pad.right;
    var ch = 220 - pad.top - pad.bottom;
    var bw = Math.max(8, Math.floor(cw / steps) - 6);

    // Grid + y-axis labels
    ctx.strokeStyle = '#e2e8f0';
    ctx.lineWidth = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = pad.top + ch - (g / 4) * ch;
      ctx.beginPath(); ctx.moveTo(pad.left, gy); ctx.lineTo(W - pad.right, gy); ctx.stroke();
      ctx.fillStyle = '#94a3b8';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'right';
      var val = maxVal * g / 4;
      var labelStr = val >= 1e8 ? (val/1e8).toFixed(1)+'億' : val >= 1e4 ? Math.round(val/1e4)+'万' : Math.round(val)+'円';
      ctx.fillText(labelStr, pad.left - 5, gy + 4);
    }

    // Bars
    data.forEach(function(d, i) {
      var slotW = cw / steps;
      var x = pad.left + i * slotW + (slotW - bw) / 2;
      var principalH = ch * (d.principal / maxVal);
      var interestH = ch * (d.interest / maxVal);

      ctx.fillStyle = '#2563eb';
      ctx.fillRect(x, pad.top + ch - principalH, bw, principalH);
      if (interestH > 0) {
        ctx.fillStyle = '#60a5fa';
        ctx.fillRect(x, pad.top + ch - principalH - interestH, bw, interestH);
      }

      // X label
      ctx.fillStyle = '#64748b';
      ctx.font = '10px sans-serif';
      ctx.textAlign = 'center';
      var mo = d.month;
      var lbl = mo >= 12 ? Math.floor(mo / 12) + '年' : mo + 'ヶ月';
      ctx.fillText(lbl, x + bw / 2, 220 - pad.bottom + 14);
    });
  }
})();
</script>

<div class="sg-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">資産管理をもっと効率的に</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、資産管理・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>

> 家計管理 → [家計簿ツール](/ja/tools/expense-tracker/)

> ROI計算 → [ROI計算ツール](/ja/tools/roi-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
