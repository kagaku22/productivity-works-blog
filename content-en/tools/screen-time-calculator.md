---
title: "Screen Time Calculator - Track Your Daily Screen Usage"
description: "Track and analyze your daily screen time across devices. Get recommendations for healthier digital habits."
date: 2025-05-16
categories: ["Free Tools"]
slug: "screen-time-calculator"
ShowToc: false
cover:
  image: "/images/covers/screen-time-calculator.png"
---

<div id="st-app">

<style>
#st-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 24px 16px;
  color: #1a1a2e;
}
#st-app h2 {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 32px 0 12px;
  color: #1a1a2e;
}
#st-app h3 {
  font-size: 1.15rem;
  font-weight: 600;
  margin: 20px 0 8px;
  color: #16213e;
}
#st-app p {
  margin: 0 0 12px;
  line-height: 1.6;
}
#st-app .intro-box {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  border-radius: 14px;
  padding: 28px 24px;
  margin-bottom: 32px;
}
#st-app .intro-box h1 {
  font-size: 1.6rem;
  font-weight: 800;
  margin: 0 0 8px;
  color: #fff;
}
#st-app .intro-box p {
  margin: 0;
  opacity: 0.9;
  font-size: 0.97rem;
}
#st-app .inputs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 16px;
  margin-bottom: 24px;
}
#st-app .input-card {
  background: #f8f9ff;
  border: 2px solid #e8eaf6;
  border-radius: 12px;
  padding: 16px 18px;
  transition: border-color 0.2s;
}
#st-app .input-card:focus-within {
  border-color: #667eea;
}
#st-app .input-card label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  color: #444;
  margin-bottom: 10px;
}
#st-app .input-card .icon {
  font-size: 1.3rem;
}
#st-app .input-row {
  display: flex;
  align-items: center;
  gap: 8px;
}
#st-app .input-card input[type="range"] {
  flex: 1;
  -webkit-appearance: none;
  height: 6px;
  border-radius: 3px;
  background: #d1d5f0;
  outline: none;
  cursor: pointer;
}
#st-app .input-card input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #667eea;
  cursor: pointer;
  box-shadow: 0 1px 4px rgba(102,126,234,0.4);
}
#st-app .val-badge {
  min-width: 48px;
  text-align: center;
  background: #667eea;
  color: #fff;
  border-radius: 8px;
  padding: 3px 8px;
  font-size: 0.85rem;
  font-weight: 700;
}
#st-app .calc-btn {
  display: block;
  width: 100%;
  padding: 15px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  font-size: 1.05rem;
  font-weight: 700;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  letter-spacing: 0.5px;
  margin-bottom: 32px;
  transition: opacity 0.2s, transform 0.1s;
}
#st-app .calc-btn:hover { opacity: 0.92; transform: translateY(-1px); }
#st-app .calc-btn:active { transform: translateY(0); }
#st-app .results-section {
  display: none;
}
#st-app .results-section.visible {
  display: block;
}
#st-app .stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 14px;
  margin-bottom: 28px;
}
#st-app .stat-card {
  background: #fff;
  border: 2px solid #e8eaf6;
  border-radius: 12px;
  padding: 18px 14px;
  text-align: center;
}
#st-app .stat-card .stat-val {
  font-size: 1.9rem;
  font-weight: 800;
  color: #667eea;
  line-height: 1.1;
}
#st-app .stat-card .stat-label {
  font-size: 0.78rem;
  color: #888;
  margin-top: 4px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}
#st-app .stat-card.highlight {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-color: transparent;
}
#st-app .stat-card.highlight .stat-val,
#st-app .stat-card.highlight .stat-label {
  color: #fff;
}
#st-app .chart-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  margin-bottom: 32px;
}
@media (min-width: 560px) {
  #st-app .chart-wrap { flex-direction: row; align-items: flex-start; }
}
#st-app canvas#st-pie {
  max-width: 220px;
  max-height: 220px;
}
#st-app .legend {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
#st-app .legend-item {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 0.88rem;
}
#st-app .legend-dot {
  width: 13px;
  height: 13px;
  border-radius: 50%;
  flex-shrink: 0;
}
#st-app .legend-label { flex: 1; color: #444; font-weight: 500; }
#st-app .legend-pct { font-weight: 700; color: #222; }
#st-app .recommend-box {
  border-radius: 12px;
  padding: 20px 22px;
  margin-bottom: 24px;
}
#st-app .recommend-box.ok { background: #e8f8f0; border: 2px solid #34d399; }
#st-app .recommend-box.warn { background: #fff8e1; border: 2px solid #fbbf24; }
#st-app .recommend-box.danger { background: #fef2f2; border: 2px solid #f87171; }
#st-app .recommend-box .rec-title {
  font-size: 1.05rem;
  font-weight: 700;
  margin-bottom: 6px;
}
#st-app .recommend-box.ok .rec-title { color: #059669; }
#st-app .recommend-box.warn .rec-title { color: #d97706; }
#st-app .recommend-box.danger .rec-title { color: #dc2626; }
#st-app .lifetime-box {
  background: #1a1a2e;
  color: #fff;
  border-radius: 14px;
  padding: 24px 22px;
  margin-bottom: 28px;
}
#st-app .lifetime-box h3 { color: #a78bfa; margin-top: 0; }
#st-app .lifetime-box .life-stat {
  font-size: 2.2rem;
  font-weight: 800;
  color: #c4b5fd;
  margin: 4px 0;
}
#st-app .lifetime-box p { color: #ccc; font-size: 0.9rem; }
#st-app .tips-list {
  list-style: none;
  padding: 0;
  margin: 0 0 28px;
}
#st-app .tips-list li {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  padding: 10px 14px;
  background: #f8f9ff;
  border-radius: 10px;
  margin-bottom: 8px;
  font-size: 0.92rem;
  line-height: 1.5;
}
#st-app .tips-list li .tip-icon { font-size: 1.2rem; flex-shrink: 0; margin-top: 1px; }
#st-app .instead-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
  gap: 12px;
  margin-bottom: 32px;
}
#st-app .instead-card {
  background: #f0f4ff;
  border-radius: 12px;
  padding: 16px;
  text-align: center;
}
#st-app .instead-card .inst-icon { font-size: 2rem; margin-bottom: 6px; }
#st-app .instead-card .inst-val { font-size: 1.4rem; font-weight: 800; color: #667eea; }
#st-app .instead-card .inst-label { font-size: 0.82rem; color: #555; margin-top: 2px; }
#st-app .related-links {
  background: #f8f9ff;
  border-radius: 12px;
  padding: 20px 22px;
  margin-top: 32px;
}
#st-app .related-links h3 { margin-top: 0; }
#st-app .related-links ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
#st-app .related-links ul li {
  padding: 6px 0;
  border-bottom: 1px solid #e8eaf6;
}
#st-app .related-links ul li:last-child { border-bottom: none; }
#st-app .related-links a {
  color: #667eea;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.93rem;
}
#st-app .related-links a:hover { text-decoration: underline; }
#st-app .reset-btn {
  background: none;
  border: 2px solid #667eea;
  color: #667eea;
  border-radius: 10px;
  padding: 10px 24px;
  font-size: 0.92rem;
  font-weight: 600;
  cursor: pointer;
  margin-top: 8px;
  transition: background 0.2s, color 0.2s;
}
#st-app .reset-btn:hover { background: #667eea; color: #fff; }
</style>

<div class="intro-box">
  <h1>Screen Time Calculator</h1>
  <p>Find out exactly how much of your life is spent looking at screens — and what you could do with that time instead.</p>
</div>

<h2>Enter Your Daily Screen Time</h2>
<p>Drag each slider to match your average hours per day for each activity.</p>

<div class="inputs-grid" id="st-inputs">
  <div class="input-card">
    <label><span class="icon">💼</span> Work / School</label>
    <div class="input-row">
      <input type="range" id="sl-work" min="0" max="14" step="0.5" value="8" oninput="stUpdate('work',this.value)">
      <span class="val-badge" id="vb-work">8h</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">📱</span> Social Media</label>
    <div class="input-row">
      <input type="range" id="sl-social" min="0" max="10" step="0.5" value="2" oninput="stUpdate('social',this.value)">
      <span class="val-badge" id="vb-social">2h</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">🎬</span> Streaming (TV/Video)</label>
    <div class="input-row">
      <input type="range" id="sl-stream" min="0" max="10" step="0.5" value="2" oninput="stUpdate('stream',this.value)">
      <span class="val-badge" id="vb-stream">2h</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">🎮</span> Gaming</label>
    <div class="input-row">
      <input type="range" id="sl-game" min="0" max="10" step="0.5" value="1" oninput="stUpdate('game',this.value)">
      <span class="val-badge" id="vb-game">1h</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">🌐</span> Web Browsing</label>
    <div class="input-row">
      <input type="range" id="sl-browse" min="0" max="10" step="0.5" value="1" oninput="stUpdate('browse',this.value)">
      <span class="val-badge" id="vb-browse">1h</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">📲</span> Other Screens</label>
    <div class="input-row">
      <input type="range" id="sl-other" min="0" max="10" step="0.5" value="0.5" oninput="stUpdate('other',this.value)">
      <span class="val-badge" id="vb-other">0.5h</span>
    </div>
  </div>
</div>

<div style="margin-bottom:16px;">
  <label style="font-weight:600; font-size:0.93rem; color:#444;">Your current age (for lifetime projection):</label><br>
  <input type="number" id="st-age" min="5" max="79" value="30" style="margin-top:8px; padding:8px 12px; border:2px solid #e8eaf6; border-radius:8px; font-size:1rem; width:100px;">
</div>

<button class="calc-btn" onclick="stCalculate()">Calculate My Screen Time</button>

<div class="results-section" id="st-results">

  <h2>Your Screen Time Summary</h2>

  <div class="stats-grid">
    <div class="stat-card highlight">
      <div class="stat-val" id="res-daily">-</div>
      <div class="stat-label">Hours / Day</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-weekly">-</div>
      <div class="stat-label">Hours / Week</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-monthly">-</div>
      <div class="stat-label">Hours / Month</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-yearly">-</div>
      <div class="stat-label">Hours / Year</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-days-year">-</div>
      <div class="stat-label">Full Days / Year</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-pct-awake">-</div>
      <div class="stat-label">% of Waking Hours</div>
    </div>
  </div>

  <h2>Breakdown by Activity</h2>
  <div class="chart-wrap">
    <canvas id="st-pie" width="220" height="220"></canvas>
    <div class="legend" id="st-legend"></div>
  </div>

  <div class="recommend-box" id="st-recommend">
    <div class="rec-title" id="rec-title"></div>
    <div id="rec-body"></div>
  </div>

  <div class="lifetime-box" id="st-lifetime">
    <h3>Lifetime Screen Time Projection</h3>
    <div class="life-stat" id="life-years">-</div>
    <p id="life-desc"></p>
    <div class="life-stat" id="life-days">-</div>
    <p id="life-desc2"></p>
  </div>

  <h2>Tips to Reduce Screen Time</h2>
  <ul class="tips-list" id="st-tips"></ul>

  <h2>What Else Could You Do With That Time?</h2>
  <p style="font-size:0.9rem;color:#666;">Based on your <strong id="instead-hours">-</strong> hours of non-work screen time per year:</p>
  <div class="instead-grid" id="st-instead"></div>

  <button class="reset-btn" onclick="stReset()">Reset Calculator</button>

</div>

<div class="related-links">
  <h3>Related Free Tools</h3>
  <ul>
    <li><a href="/tools/pomodoro-timer/">Pomodoro Timer — Focus in 25-minute sprints</a></li>
    <li><a href="/tools/sleep-debt-calculator/">Sleep Debt Calculator — Find out if you're sleep-deprived</a></li>
    <li><a href="/tools/stopwatch-timer/">Work Hours Tracker — Log and analyze your working time</a></li>
    <li><a href="/tools/meeting-cost-calculator/">Distraction Cost Calculator — See how much interruptions cost you</a></li>
    <li><a href="/tools/habit-tracker/">Habit Streak Tracker — Build screen-free routines</a></li>
  </ul>
</div>

<script>
(function() {
  var stVals = { work: 8, social: 2, stream: 2, game: 1, browse: 1, other: 0.5 };
  var stLabels = {
    work:   { label: 'Work / School',      icon: '💼', color: '#667eea' },
    social: { label: 'Social Media',       icon: '📱', color: '#f472b6' },
    stream: { label: 'Streaming',          icon: '🎬', color: '#fb923c' },
    game:   { label: 'Gaming',             icon: '🎮', color: '#34d399' },
    browse: { label: 'Web Browsing',       icon: '🌐', color: '#60a5fa' },
    other:  { label: 'Other Screens',      icon: '📲', color: '#a78bfa' }
  };

  window.stUpdate = function(key, val) {
    stVals[key] = parseFloat(val);
    var badge = document.getElementById('vb-' + key);
    if (badge) badge.textContent = parseFloat(val) % 1 === 0 ? val + 'h' : parseFloat(val).toFixed(1) + 'h';
  };

  window.stCalculate = function() {
    var total = 0;
    Object.keys(stVals).forEach(function(k) { total += stVals[k]; });
    var age = parseInt(document.getElementById('st-age').value) || 30;
    age = Math.min(79, Math.max(5, age));

    var weekly  = +(total * 7).toFixed(1);
    var monthly = +(total * 30.44).toFixed(0);
    var yearly  = +(total * 365.25).toFixed(0);
    var daysYear = +(yearly / 24).toFixed(1);
    var pctAwake = +((total / 16) * 100).toFixed(1);

    document.getElementById('res-daily').textContent   = total.toFixed(1) + 'h';
    document.getElementById('res-weekly').textContent  = weekly + 'h';
    document.getElementById('res-monthly').textContent = monthly + 'h';
    document.getElementById('res-yearly').textContent  = yearly + 'h';
    document.getElementById('res-days-year').textContent = daysYear;
    document.getElementById('res-pct-awake').textContent = pctAwake + '%';

    // Pie chart
    drawPie(stVals, total);

    // Recommendation
    var recBox = document.getElementById('st-recommend');
    var recTitle = document.getElementById('rec-title');
    var recBody = document.getElementById('rec-body');
    var nonWork = total - stVals.work;

    recBox.className = 'recommend-box';
    if (nonWork <= 2) {
      recBox.classList.add('ok');
      recTitle.textContent = 'Great job! Your leisure screen time is within healthy limits.';
      recBody.textContent = 'Experts recommend keeping recreational screen time under 2 hours per day for adults. You\'re right on target. Keep up the balance!';
    } else if (nonWork <= 4) {
      recBox.classList.add('warn');
      recTitle.textContent = 'Moderate screen time — some room for improvement.';
      recBody.textContent = 'Your non-work screen time is ' + nonWork.toFixed(1) + ' hours/day, which is above the recommended 2 hours. Small reductions can meaningfully improve sleep quality and mental focus.';
    } else {
      recBox.classList.add('danger');
      recTitle.textContent = 'High screen time — your wellbeing may be at risk.';
      recBody.textContent = 'Your non-work screen time is ' + nonWork.toFixed(1) + ' hours/day — more than double the recommended limit. Research links excessive screen time to disrupted sleep, reduced attention span, and increased anxiety. Consider a digital detox plan.';
    }

    // Lifetime projection
    var yearsLeft = 80 - age;
    if (yearsLeft < 0) yearsLeft = 0;
    var lifetimeHours = +(total * 365.25 * yearsLeft).toFixed(0);
    var lifetimeYears = +(lifetimeHours / 8760).toFixed(1);
    var lifetimeDays  = +(lifetimeHours / 24).toFixed(0);

    document.getElementById('life-years').textContent = lifetimeYears + ' years';
    document.getElementById('life-desc').textContent  =
      'of screen time remaining in your life (from age ' + age + ' to 80)';
    document.getElementById('life-days').textContent  = Number(lifetimeDays).toLocaleString() + ' days';
    document.getElementById('life-desc2').textContent =
      'That\'s ' + Number(lifetimeHours).toLocaleString() + ' total hours spent on screens. What would you do with even 10% of that time back?';

    // Tips
    var tips = buildTips(stVals, nonWork);
    var tipsList = document.getElementById('st-tips');
    tipsList.innerHTML = '';
    tips.forEach(function(t) {
      var li = document.createElement('li');
      li.innerHTML = '<span class="tip-icon">' + t.icon + '</span><span>' + t.text + '</span>';
      tipsList.appendChild(li);
    });

    // Instead
    var nonWorkYearly = nonWork * 365.25;
    document.getElementById('instead-hours').textContent = Math.round(nonWorkYearly) + ' hours';
    buildInstead(nonWorkYearly);

    document.getElementById('st-results').className = 'results-section visible';
    document.getElementById('st-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function buildTips(vals, nonWork) {
    var tips = [];
    if (vals.social > 1.5) tips.push({ icon: '⏰', text: 'Set a daily app timer for social media. Even cutting by 30 minutes saves over 180 hours per year.' });
    if (vals.stream > 2) tips.push({ icon: '📺', text: 'Try a "one episode" rule for streaming. Finishing at a natural stopping point reduces auto-play temptation.' });
    if (vals.game > 2) tips.push({ icon: '🎮', text: 'Schedule gaming sessions rather than open-ended play. Use a physical timer to signal stop time.' });
    if (vals.browse > 1.5) tips.push({ icon: '🌐', text: 'Use browser extensions like LeechBlock or StayFocusd to cap mindless browsing time.' });
    if (nonWork > 2) tips.push({ icon: '📵', text: 'Designate screen-free zones: the dinner table, the bedroom, and the first 30 minutes after waking up.' });
    if (nonWork > 3) tips.push({ icon: '🌿', text: 'Replace one hour of screen time per day with a walk, workout, or hobby. The difference in mental clarity is noticeable within a week.' });
    if (nonWork > 4) tips.push({ icon: '🔕', text: 'Turn off all non-essential push notifications. Every ping pulls you back to the screen involuntarily.' });
    tips.push({ icon: '😴', text: 'Stop all screens at least 60 minutes before bed. Blue light disrupts melatonin production and delays sleep onset.' });
    tips.push({ icon: '📖', text: 'Keep a physical book or journal nearby as a default "boredom activity" instead of reaching for your phone.' });
    tips.push({ icon: '👥', text: 'Schedule regular in-person social activities to naturally replace online social media browsing.' });
    return tips.slice(0, 7);
  }

  function buildInstead(nonWorkHoursPerYear) {
    var items = [
      { icon: '📚', val: Math.round(nonWorkHoursPerYear / 6),    label: 'Books read (6 hrs each)' },
      { icon: '🚶', val: Math.round(nonWorkHoursPerYear / 0.75), label: 'Walks taken (45 min each)' },
      { icon: '🎨', val: Math.round(nonWorkHoursPerYear / 3),    label: 'Paintings or drawings' },
      { icon: '🍳', val: Math.round(nonWorkHoursPerYear / 1),    label: 'Home-cooked meals' },
      { icon: '🧘', val: Math.round(nonWorkHoursPerYear / 0.5),  label: 'Meditation sessions (30 min)' },
      { icon: '🎸', val: Math.round(nonWorkHoursPerYear / 500),  label: 'Years to learn an instrument' },
    ];
    var grid = document.getElementById('st-instead');
    grid.innerHTML = '';
    items.forEach(function(it) {
      var card = document.createElement('div');
      card.className = 'instead-card';
      card.innerHTML =
        '<div class="inst-icon">' + it.icon + '</div>' +
        '<div class="inst-val">' + it.val.toLocaleString() + '</div>' +
        '<div class="inst-label">' + it.label + '</div>';
      grid.appendChild(card);
    });
  }

  function drawPie(vals, total) {
    var canvas = document.getElementById('st-pie');
    if (!canvas) return;
    var ctx = canvas.getContext('2d');
    var W = canvas.width, H = canvas.height;
    ctx.clearRect(0, 0, W, H);
    if (total === 0) return;

    var keys = Object.keys(vals).filter(function(k) { return vals[k] > 0; });
    var startAngle = -Math.PI / 2;
    var cx = W / 2, cy = H / 2, r = Math.min(W, H) / 2 - 6;

    keys.forEach(function(k) {
      var slice = (vals[k] / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, startAngle, startAngle + slice);
      ctx.closePath();
      ctx.fillStyle = stLabels[k].color;
      ctx.fill();
      ctx.strokeStyle = '#fff';
      ctx.lineWidth = 2;
      ctx.stroke();
      startAngle += slice;
    });

    // Legend
    var legend = document.getElementById('st-legend');
    legend.innerHTML = '';
    keys.forEach(function(k) {
      var pct = ((vals[k] / total) * 100).toFixed(1);
      var item = document.createElement('div');
      item.className = 'legend-item';
      item.innerHTML =
        '<div class="legend-dot" style="background:' + stLabels[k].color + '"></div>' +
        '<span class="legend-label">' + stLabels[k].icon + ' ' + stLabels[k].label + '</span>' +
        '<span class="legend-pct">' + pct + '%</span>';
      legend.appendChild(item);
    });
  }

  window.stReset = function() {
    stVals = { work: 8, social: 2, stream: 2, game: 1, browse: 1, other: 0.5 };
    Object.keys(stVals).forEach(function(k) {
      var sl = document.getElementById('sl-' + k);
      if (sl) { sl.value = stVals[k]; stUpdate(k, stVals[k]); }
    });
    document.getElementById('st-age').value = 30;
    document.getElementById('st-results').className = 'results-section';
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };
})();
</script>

</div>
