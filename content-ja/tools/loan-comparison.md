---
title: "ローン比較計算ツール"
date: 2025-05-16
description: "無料のローン比較計算ツール。最大3つのローンを並べて比較。月額返済・総利息・償還スケジュールを一覧表示。"
categories: ["無料ツール"]
slug: "loan-comparison"
ShowToc: false
cover:
  image: "/images/covers/loan-comparison-ja.png"
  alt: "ローン比較計算ツール"
---

> ローン返済 → [ローン返済シミュレーター](/ja/tools/loan-emi-calculator/)
> 貯金目標 → [貯金目標計算ツール](/ja/tools/savings-goal-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

<div id="lc-app">
<style>
#lc-app *,#lc-app *::before,#lc-app *::after{box-sizing:border-box;margin:0;padding:0}
#lc-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Kaku Gothic ProN','Yu Gothic',Meiryo,sans-serif;font-size:15px;color:#1e293b;max-width:900px;margin:0 auto;padding:16px}
#lc-app h2{font-size:1.25rem;font-weight:700;margin-bottom:16px;color:#0f172a}
#lc-app h3{font-size:1rem;font-weight:700;margin-bottom:10px;color:#0f172a}
#lc-app .lc-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px;margin-bottom:20px}
#lc-app .lc-card{background:#f8fafc;border:1.5px solid #e2e8f0;border-radius:10px;padding:16px}
#lc-app .lc-card.winner{border-color:#22c55e;background:#f0fdf4}
#lc-app .lc-card-title{font-size:0.9rem;font-weight:700;margin-bottom:12px;color:#475569;display:flex;align-items:center;gap:6px}
#lc-app .lc-badge{font-size:11px;padding:2px 8px;border-radius:20px;font-weight:700;background:#22c55e;color:#fff}
#lc-app label{display:block;font-size:12px;font-weight:600;color:#64748b;margin-bottom:4px;margin-top:10px}
#lc-app label:first-of-type{margin-top:0}
#lc-app input[type=number],#lc-app input[type=text]{width:100%;padding:8px 10px;border:1.5px solid #cbd5e1;border-radius:7px;font-size:14px;color:#1e293b;background:#fff;transition:border-color .2s}
#lc-app input[type=number]:focus,#lc-app input[type=text]:focus{outline:none;border-color:#3b82f6}
#lc-app .lc-btn{display:inline-block;padding:10px 28px;background:#3b82f6;color:#fff;border:none;border-radius:8px;font-size:15px;font-weight:700;cursor:pointer;transition:background .2s;margin-right:8px}
#lc-app .lc-btn:hover{background:#2563eb}
#lc-app .lc-btn-reset{background:#94a3b8}
#lc-app .lc-btn-reset:hover{background:#64748b}
#lc-app .lc-actions{margin-bottom:24px}
#lc-app .lc-results{margin-top:8px}
#lc-app .lc-compare-table{width:100%;border-collapse:collapse;font-size:14px;margin-bottom:24px}
#lc-app .lc-compare-table th{background:#1e293b;color:#fff;padding:10px 12px;text-align:left;font-weight:600;font-size:13px}
#lc-app .lc-compare-table td{padding:9px 12px;border-bottom:1px solid #e2e8f0}
#lc-app .lc-compare-table tr:nth-child(even) td{background:#f8fafc}
#lc-app .lc-compare-table .winner-col{background:#f0fdf4!important;font-weight:700;color:#15803d}
#lc-app .lc-chart-wrap{margin-bottom:24px}
#lc-app canvas{display:block;max-width:100%;border-radius:10px;background:#f8fafc;border:1.5px solid #e2e8f0;padding:12px}
#lc-app .lc-amort-wrap{margin-bottom:20px}
#lc-app .lc-amort-wrap details{margin-bottom:10px}
#lc-app .lc-amort-wrap summary{cursor:pointer;font-weight:700;font-size:13px;padding:8px 12px;background:#f1f5f9;border:1.5px solid #e2e8f0;border-radius:8px;list-style:none;display:flex;align-items:center;justify-content:space-between}
#lc-app .lc-amort-wrap summary::-webkit-details-marker{display:none}
#lc-app .lc-amort-wrap summary::after{content:'▼';font-size:11px;color:#94a3b8}
#lc-app details[open] summary::after{content:'▲'}
#lc-app .lc-amort-table{width:100%;border-collapse:collapse;font-size:13px;margin-top:8px}
#lc-app .lc-amort-table th{background:#475569;color:#fff;padding:7px 10px;text-align:right;font-size:12px}
#lc-app .lc-amort-table th:first-child{text-align:center}
#lc-app .lc-amort-table td{padding:6px 10px;border-bottom:1px solid #f1f5f9;text-align:right}
#lc-app .lc-amort-table td:first-child{text-align:center;font-weight:600;color:#64748b}
#lc-app .lc-amort-table tr:nth-child(even) td{background:#f8fafc}
#lc-app .lc-hidden{display:none}
#lc-app .lc-loan-toggle{display:flex;align-items:center;gap:8px;margin-bottom:8px;font-size:13px;font-weight:600;color:#64748b}
#lc-app .lc-loan-toggle input[type=checkbox]{width:16px;height:16px;cursor:pointer;accent-color:#3b82f6}
#lc-app .lc-num{font-variant-numeric:tabular-nums}
@media(max-width:600px){
  #lc-app .lc-compare-table{font-size:12px}
  #lc-app .lc-compare-table th,#lc-app .lc-compare-table td{padding:7px 8px}
  #lc-app .lc-btn{padding:9px 18px;font-size:14px}
}
</style>

<h2>ローン比較計算ツール</h2>

<div class="lc-grid" id="lc-inputs">

  <div class="lc-card" id="card-0">
    <div class="lc-card-title">ローン A</div>
    <label>ローン名</label>
    <input type="text" class="lc-name" data-i="0" value="ローン A" placeholder="例：A銀行">
    <label>借入金額（円）</label>
    <input type="number" class="lc-principal" data-i="0" value="20000000" min="0" step="100000">
    <label>年利（%）</label>
    <input type="number" class="lc-rate" data-i="0" value="1.5" min="0" step="0.01">
    <label>返済期間（年）</label>
    <input type="number" class="lc-term" data-i="0" value="35" min="1" max="50">
  </div>

  <div class="lc-card" id="card-1">
    <div class="lc-card-title">ローン B</div>
    <label>ローン名</label>
    <input type="text" class="lc-name" data-i="1" value="ローン B" placeholder="例：B銀行">
    <label>借入金額（円）</label>
    <input type="number" class="lc-principal" data-i="1" value="20000000" min="0" step="100000">
    <label>年利（%）</label>
    <input type="number" class="lc-rate" data-i="1" value="1.2" min="0" step="0.01">
    <label>返済期間（年）</label>
    <input type="number" class="lc-term" data-i="1" value="35" min="1" max="50">
  </div>

  <div class="lc-card" id="card-2">
    <div class="lc-card-title">
      <label class="lc-loan-toggle" style="margin:0">
        <input type="checkbox" id="lc-enable2"> ローン C（任意）
      </label>
    </div>
    <div id="lc-inputs2">
      <label>ローン名</label>
      <input type="text" class="lc-name" data-i="2" value="ローン C" placeholder="例：C銀行">
      <label>借入金額（円）</label>
      <input type="number" class="lc-principal" data-i="2" value="20000000" min="0" step="100000">
      <label>年利（%）</label>
      <input type="number" class="lc-rate" data-i="2" value="1.8" min="0" step="0.01">
      <label>返済期間（年）</label>
      <input type="number" class="lc-term" data-i="2" value="30" min="1" max="50">
    </div>
  </div>

</div>

<div class="lc-actions">
  <button class="lc-btn" id="lc-calc-btn">比較する</button>
  <button class="lc-btn lc-btn-reset" id="lc-reset-btn">リセット</button>
</div>

<div class="lc-results lc-hidden" id="lc-results">
  <h3>比較結果</h3>
  <div style="overflow-x:auto;margin-bottom:24px">
    <table class="lc-compare-table" id="lc-compare-table"></table>
  </div>

  <div class="lc-chart-wrap">
    <h3>コスト比較グラフ</h3>
    <canvas id="lc-chart" height="260"></canvas>
  </div>

  <div class="lc-amort-wrap" id="lc-amort-wrap">
    <h3>返済スケジュール</h3>
  </div>
</div>

<script>
(function(){
  var CURRENCY = '¥';
  var enable2 = document.getElementById('lc-enable2');
  var inputs2 = document.getElementById('lc-inputs2');
  inputs2.style.opacity = '0.4';
  inputs2.style.pointerEvents = 'none';
  enable2.addEventListener('change', function(){
    inputs2.style.opacity = enable2.checked ? '1' : '0.4';
    inputs2.style.pointerEvents = enable2.checked ? '' : 'none';
  });

  function fmt(n){
    return CURRENCY + Math.round(n).toLocaleString('ja-JP');
  }
  function fmtN(n){
    return n.toLocaleString('ja-JP', {minimumFractionDigits:2, maximumFractionDigits:2});
  }

  function calcLoan(principal, annualRate, years){
    var n = years * 12;
    var r = annualRate / 100 / 12;
    var monthly;
    if(r === 0){
      monthly = principal / n;
    } else {
      monthly = principal * r * Math.pow(1+r, n) / (Math.pow(1+r, n) - 1);
    }
    var totalPaid = monthly * n;
    var totalInterest = totalPaid - principal;
    return {monthly: monthly, totalPaid: totalPaid, totalInterest: totalInterest, n: n, r: r, principal: principal};
  }

  function buildAmortization(loan){
    var rows = [];
    var balance = loan.principal;
    var n = loan.n;
    var r = loan.r;
    var monthly = loan.monthly;
    for(var i = 1; i <= n; i++){
      var interest = balance * r;
      var princ = monthly - interest;
      balance -= princ;
      if(balance < 0) balance = 0;
      rows.push({month: i, payment: monthly, principal: princ, interest: interest, balance: balance});
    }
    return rows;
  }

  function renderAmortTable(rows, name, id){
    var html = '<details id="amort-'+id+'"><summary>'+name+' — 返済スケジュール（全'+rows.length+'回払い）</summary>';
    html += '<div style="overflow-x:auto"><table class="lc-amort-table"><thead><tr>';
    html += '<th>回数</th><th>月額返済</th><th>元金</th><th>利息</th><th>残高</th>';
    html += '</tr></thead><tbody>';
    var showAll = rows.length <= 60;
    var limit = showAll ? rows.length : 24;
    for(var i = 0; i < limit; i++){
      var row = rows[i];
      html += '<tr><td>'+row.month+'回</td><td>'+fmt(row.payment)+'</td><td>'+fmt(row.principal)+'</td><td>'+fmt(row.interest)+'</td><td>'+fmt(row.balance)+'</td></tr>';
    }
    if(!showAll){
      html += '<tr><td colspan="5" style="text-align:center;color:#94a3b8;font-style:italic;padding:10px">… 残り'+(rows.length - 24)+'回分（全'+rows.length+'回中、最初の24回を表示）</td></tr>';
      var last = rows[rows.length-1];
      html += '<tr><td>'+last.month+'回</td><td>'+fmt(last.payment)+'</td><td>'+fmt(last.principal)+'</td><td>'+fmt(last.interest)+'</td><td>'+fmt(last.balance)+'</td></tr>';
    }
    html += '</tbody></table></div></details>';
    return html;
  }

  function drawChart(results){
    var canvas = document.getElementById('lc-chart');
    var dpr = window.devicePixelRatio || 1;
    var W = canvas.parentElement.clientWidth - 24;
    var H = 260;
    canvas.width = W * dpr;
    canvas.height = H * dpr;
    canvas.style.width = W + 'px';
    canvas.style.height = H + 'px';
    var ctx = canvas.getContext('2d');
    ctx.scale(dpr, dpr);

    var pad = {top: 30, right: 20, bottom: 50, left: 90};
    var n = results.length;
    var maxVal = 0;
    results.forEach(function(r){ if(r.totalPaid > maxVal) maxVal = r.totalPaid; });
    maxVal = maxVal * 1.1;

    var colors = {principal: '#3b82f6', interest: '#f59e0b'};
    var barW = Math.floor(((W - pad.left - pad.right) / n) * 0.55);
    var gap = (W - pad.left - pad.right - barW * n) / (n + 1);
    var chartH = H - pad.top - pad.bottom;

    ctx.clearRect(0, 0, W, H);
    ctx.fillStyle = '#f8fafc';
    ctx.fillRect(0, 0, W, H);

    var steps = 4;
    ctx.strokeStyle = '#e2e8f0';
    ctx.lineWidth = 1;
    for(var s = 0; s <= steps; s++){
      var y = pad.top + chartH - (s / steps) * chartH;
      ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(W - pad.right, y); ctx.stroke();
      ctx.fillStyle = '#94a3b8';
      ctx.font = '11px sans-serif';
      ctx.textAlign = 'right';
      var labelVal = maxVal * s / steps;
      var labelStr = labelVal >= 10000000 ? (labelVal/10000).toFixed(0)+'万円' : CURRENCY + Math.round(labelVal).toLocaleString('ja-JP');
      ctx.fillText(labelStr, pad.left - 4, y + 4);
    }

    results.forEach(function(r, i){
      var x = pad.left + gap + i * (barW + gap);
      var pxH = (r.principal / maxVal) * chartH;
      var inH = (r.totalInterest / maxVal) * chartH;
      var totalH = pxH + inH;
      var baseY = pad.top + chartH;

      ctx.fillStyle = colors.principal;
      ctx.fillRect(x, baseY - pxH, barW, pxH);
      ctx.fillStyle = colors.interest;
      ctx.fillRect(x, baseY - totalH, barW, inH);

      ctx.fillStyle = '#1e293b';
      ctx.font = 'bold 12px sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText(r.name, x + barW/2, H - 10);
    });

    var lx = pad.left;
    var ly = 12;
    ctx.fillStyle = colors.principal; ctx.fillRect(lx, ly - 9, 14, 10);
    ctx.fillStyle = '#475569'; ctx.font = '12px sans-serif'; ctx.textAlign = 'left';
    ctx.fillText('元金', lx + 18, ly);
    ctx.fillStyle = colors.interest; ctx.fillRect(lx + 60, ly - 9, 14, 10);
    ctx.fillStyle = '#475569';
    ctx.fillText('利息', lx + 78, ly);
  }

  document.getElementById('lc-calc-btn').addEventListener('click', calculate);
  document.getElementById('lc-reset-btn').addEventListener('click', function(){
    document.getElementById('lc-results').classList.add('lc-hidden');
    document.querySelectorAll('#lc-inputs .lc-name').forEach(function(el,i){ el.value = ['ローン A','ローン B','ローン C'][i]; });
    document.querySelectorAll('#lc-inputs .lc-principal').forEach(function(el){ el.value = 20000000; });
    document.querySelectorAll('#lc-inputs .lc-rate').forEach(function(el,i){ el.value = [1.5,1.2,1.8][i]; });
    document.querySelectorAll('#lc-inputs .lc-term').forEach(function(el,i){ el.value = [35,35,30][i]; });
    enable2.checked = false;
    inputs2.style.opacity = '0.4';
    inputs2.style.pointerEvents = 'none';
  });

  function getLoans(){
    var loans = [];
    for(var i = 0; i < 3; i++){
      if(i === 2 && !enable2.checked) continue;
      var name = document.querySelector('.lc-name[data-i="'+i+'"]').value.trim() || 'ローン '+(i+1);
      var principal = parseFloat(document.querySelector('.lc-principal[data-i="'+i+'"]').value) || 0;
      var rate = parseFloat(document.querySelector('.lc-rate[data-i="'+i+'"]').value) || 0;
      var term = parseInt(document.querySelector('.lc-term[data-i="'+i+'"]').value) || 1;
      loans.push({name: name, principal: principal, rate: rate, term: term, idx: i});
    }
    return loans;
  }

  function calculate(){
    var loans = getLoans();
    if(!loans.length) return;

    var results = loans.map(function(l){
      return Object.assign({}, l, calcLoan(l.principal, l.rate, l.term));
    });

    var winnerIdx = 0;
    results.forEach(function(r, i){ if(r.totalPaid < results[winnerIdx].totalPaid) winnerIdx = i; });

    var rows = [
      {label: '月額返済額', key: 'monthly', format: fmt},
      {label: '総返済額', key: 'totalPaid', format: fmt},
      {label: '総利息', key: 'totalInterest', format: fmt},
      {label: '借入元金', key: 'principal', format: fmt},
      {label: '年利', fn: function(r){ return fmtN(r.rate) + '%'; }},
      {label: '返済期間', fn: function(r){ return r.term + '年（' + r.n + 'ヶ月）'; }},
    ];

    var thead = '<thead><tr><th>項目</th>';
    results.forEach(function(r, i){ thead += '<th>'+(i === winnerIdx ? '★ ' : '')+r.name+(i === winnerIdx ? '（最安）' : '')+'</th>'; });
    thead += '</tr></thead>';

    var tbody = '<tbody>';
    rows.forEach(function(row){
      tbody += '<tr><td style="font-weight:600;color:#475569">'+row.label+'</td>';
      results.forEach(function(r, i){
        var val = row.fn ? row.fn(r) : row.format(r[row.key]);
        tbody += '<td class="lc-num'+(i === winnerIdx ? ' winner-col' : '')+'">'+val+'</td>';
      });
      tbody += '</tr>';
    });
    tbody += '</tbody>';

    document.getElementById('lc-compare-table').innerHTML = thead + tbody;

    var amortWrap = document.getElementById('lc-amort-wrap');
    var amortHtml = '<h3>返済スケジュール</h3>';
    results.forEach(function(r, i){
      var amRows = buildAmortization(r);
      amortHtml += renderAmortTable(amRows, r.name, i);
    });
    amortWrap.innerHTML = amortHtml;

    document.getElementById('lc-results').classList.remove('lc-hidden');

    setTimeout(function(){ drawChart(results); }, 50);

    window.addEventListener('resize', function(){ drawChart(results); });
  }
})();
</script>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>
