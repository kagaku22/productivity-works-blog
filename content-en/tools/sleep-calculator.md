---
title: "Sleep Cycle Calculator"
date: 2025-05-16
description: "Free sleep cycle calculator. Find the best bedtime or wake-up time based on 90-minute sleep cycles. Wake up feeling refreshed. Includes sleep quality tips."
categories: ["Free Tools"]
slug: "sleep-calculator"
ShowToc: false
cover:
  image: "/images/covers/sleep-calculator.png"
  alt: "Sleep Cycle Calculator"
---

Enter your wake-up time or bedtime and instantly find the ideal sleep schedule based on 90-minute sleep cycles — so you wake up between cycles feeling alert, not groggy.

<div id="sl-app">
<style>
#sl-app *,
#sl-app *::before,
#sl-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#sl-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: #1e293b;
  max-width: 700px;
  margin: 0 auto;
  padding: 8px 0;
  font-size: 15px;
  line-height: 1.6;
}
#sl-app h2 {
  font-size: 18px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 16px;
}
#sl-app .sl-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 22px 24px;
  margin-bottom: 20px;
}
#sl-app .sl-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 22px;
}
#sl-app .sl-tab {
  flex: 1;
  padding: 10px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  background: #fff;
  color: #475569;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  text-align: center;
  transition: all 0.15s;
}
#sl-app .sl-tab:hover {
  border-color: #6366f1;
  color: #6366f1;
}
#sl-app .sl-tab.active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#sl-app .sl-label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #334155;
  margin-bottom: 7px;
}
#sl-app .sl-time-input {
  width: 100%;
  max-width: 220px;
  padding: 10px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 22px;
  font-weight: 700;
  color: #0f172a;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
}
#sl-app .sl-time-input:focus {
  border-color: #6366f1;
}
#sl-app .sl-hint {
  font-size: 12px;
  color: #94a3b8;
  margin-top: 6px;
}
#sl-app .sl-btn {
  display: inline-block;
  margin-top: 16px;
  padding: 11px 28px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#sl-app .sl-btn:hover {
  background: #4f46e5;
}
#sl-app .sl-results {
  display: none;
}
#sl-app .sl-results.visible {
  display: block;
}
#sl-app .sl-results-title {
  font-size: 15px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 14px;
  padding-bottom: 8px;
  border-bottom: 2px solid #e2e8f0;
}
#sl-app .sl-cycle-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#sl-app .sl-cycle-item {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 14px 16px;
  border-radius: 10px;
  border: 1.5px solid #e2e8f0;
  background: #fff;
  position: relative;
}
#sl-app .sl-cycle-item.best {
  border-color: #6366f1;
  background: #eef2ff;
}
#sl-app .sl-cycle-item.good {
  border-color: #34d399;
  background: #f0fdf4;
}
#sl-app .sl-cycle-time {
  font-size: 24px;
  font-weight: 800;
  color: #0f172a;
  min-width: 80px;
}
#sl-app .sl-cycle-meta {
  display: flex;
  flex-direction: column;
  gap: 2px;
}
#sl-app .sl-cycle-cycles {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
}
#sl-app .sl-cycle-duration {
  font-size: 12px;
  color: #94a3b8;
}
#sl-app .sl-badge {
  margin-left: auto;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
  white-space: nowrap;
}
#sl-app .sl-badge-best {
  background: #6366f1;
  color: #fff;
}
#sl-app .sl-badge-good {
  background: #34d399;
  color: #fff;
}
#sl-app .sl-badge-ok {
  background: #f1f5f9;
  color: #64748b;
}
#sl-app .sl-timeline {
  margin-top: 8px;
  padding: 16px;
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
}
#sl-app .sl-timeline-title {
  font-size: 13px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 12px;
}
#sl-app .sl-tl-bar {
  display: flex;
  height: 28px;
  border-radius: 6px;
  overflow: hidden;
  margin-bottom: 8px;
}
#sl-app .sl-tl-seg {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  font-weight: 700;
  color: #fff;
  transition: flex 0.3s;
}
#sl-app .sl-tl-seg.fall-asleep { background: #94a3b8; }
#sl-app .sl-tl-seg.cycle { background: #6366f1; }
#sl-app .sl-tl-seg.cycle:nth-child(even) { background: #818cf8; }
#sl-app .sl-tl-legend {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}
#sl-app .sl-tl-legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 11px;
  color: #64748b;
}
#sl-app .sl-tl-dot {
  width: 10px;
  height: 10px;
  border-radius: 3px;
  flex-shrink: 0;
}
#sl-app .sl-section-label {
  font-size: 13px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 10px;
  margin-top: 18px;
}
#sl-app .sl-tips {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
#sl-app .sl-tip {
  display: flex;
  gap: 10px;
  align-items: flex-start;
  font-size: 13px;
  color: #475569;
  padding: 10px 14px;
  background: #f8fafc;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
}
#sl-app .sl-tip-icon {
  font-size: 16px;
  flex-shrink: 0;
  line-height: 1.4;
}
@media (max-width: 520px) {
  #sl-app .sl-tabs {
    flex-direction: column;
  }
  #sl-app .sl-cycle-time {
    font-size: 20px;
    min-width: 64px;
  }
}
</style>

<div class="sl-tabs">
  <button class="sl-tab active" id="sl-tab-wake" onclick="(function(){document.getElementById('sl-tab-wake').classList.add('active');document.getElementById('sl-tab-bed').classList.remove('active');document.getElementById('sl-panel-wake').style.display='block';document.getElementById('sl-panel-bed').style.display='none';document.getElementById('sl-results').classList.remove('visible');})()">I want to wake up at…</button>
  <button class="sl-tab" id="sl-tab-bed" onclick="(function(){document.getElementById('sl-tab-bed').classList.add('active');document.getElementById('sl-tab-wake').classList.remove('active');document.getElementById('sl-panel-bed').style.display='block';document.getElementById('sl-panel-wake').style.display='none';document.getElementById('sl-results').classList.remove('visible');})()">I'm going to bed at…</button>
</div>

<div class="sl-card">
  <div id="sl-panel-wake">
    <label class="sl-label" for="sl-wake-time">Target wake-up time</label>
    <input type="time" id="sl-wake-time" class="sl-time-input">
    <p class="sl-hint">We'll calculate the best bedtimes based on 90-min sleep cycles.</p>
  </div>
  <div id="sl-panel-bed" style="display:none;">
    <label class="sl-label" for="sl-bed-time">Bedtime (when you plan to sleep)</label>
    <input type="time" id="sl-bed-time" class="sl-time-input">
    <p class="sl-hint">We'll calculate the best wake-up times based on 90-min sleep cycles.</p>
  </div>
  <button class="sl-btn" onclick="slCalculate()">Calculate Sleep Times</button>
</div>

<div class="sl-results" id="sl-results">
  <div class="sl-card">
    <p class="sl-results-title" id="sl-results-title">Recommended bedtimes</p>
    <ul class="sl-cycle-list" id="sl-cycle-list"></ul>
  </div>
  <div class="sl-card" id="sl-timeline-card">
    <p class="sl-timeline-title">Sleep cycle timeline (selected option)</p>
    <div class="sl-tl-bar" id="sl-tl-bar"></div>
    <div class="sl-tl-legend">
      <div class="sl-tl-legend-item"><div class="sl-tl-dot" style="background:#94a3b8;"></div>Fall asleep (~14 min)</div>
      <div class="sl-tl-legend-item"><div class="sl-tl-dot" style="background:#6366f1;"></div>90-min cycle</div>
    </div>
  </div>
  <div class="sl-card">
    <p class="sl-section-label">Sleep Quality Tips</p>
    <ul class="sl-tips">
      <li class="sl-tip"><span class="sl-tip-icon">🌙</span><span><strong>Stick to a schedule:</strong> Going to bed and waking at the same time every day — even on weekends — anchors your circadian rhythm.</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">📵</span><span><strong>Screen-free wind-down:</strong> Avoid bright screens for 30–60 minutes before bed. Blue light suppresses melatonin production.</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">❄️</span><span><strong>Cool your room:</strong> The ideal sleep temperature is around 65–68°F (18–20°C). A cooler room helps your core body temperature drop, triggering sleep.</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">☕</span><span><strong>Cut caffeine early:</strong> Caffeine has a half-life of ~5 hours. Stop consuming it at least 6 hours before bedtime for best results.</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">🛏️</span><span><strong>Bed = sleep only:</strong> Reserve your bed for sleep. Working or watching TV in bed trains your brain to stay alert there.</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">💡</span><span><strong>5–6 cycles = optimal:</strong> Most adults feel best with 5 or 6 full 90-minute cycles (7.5–9 hours). Waking mid-cycle causes grogginess (sleep inertia).</span></li>
    </ul>
  </div>
</div>

<script>
(function () {
  var FALL_ASLEEP_MIN = 14;
  var CYCLE_MIN = 90;

  function pad(n) { return n < 10 ? '0' + n : '' + n; }

  function minutesToTime(totalMin) {
    var h = Math.floor(((totalMin % 1440) + 1440) % 1440 / 60);
    var m = ((totalMin % 1440) + 1440) % 1440 % 60;
    var ampm = h >= 12 ? 'PM' : 'AM';
    var h12 = h % 12 === 0 ? 12 : h % 12;
    return pad(h12) + ':' + pad(m) + ' ' + ampm;
  }

  function timeInputToMinutes(val) {
    if (!val) return null;
    var parts = val.split(':');
    return parseInt(parts[0], 10) * 60 + parseInt(parts[1], 10);
  }

  function setCurrentTime(inputId) {
    var now = new Date();
    var el = document.getElementById(inputId);
    if (el && !el.value) {
      el.value = pad(now.getHours()) + ':' + pad(now.getMinutes());
    }
  }

  setCurrentTime('sl-wake-time');
  setCurrentTime('sl-bed-time');

  function getBadge(cycles) {
    if (cycles >= 5 && cycles <= 6) return { cls: 'sl-badge-best', label: 'Best' };
    if (cycles === 4) return { cls: 'sl-badge-good', label: 'Good' };
    return { cls: 'sl-badge-ok', label: cycles + ' cycles' };
  }

  function renderTimeline(cycles) {
    var bar = document.getElementById('sl-tl-bar');
    bar.innerHTML = '';
    var totalMin = FALL_ASLEEP_MIN + cycles * CYCLE_MIN;
    var fallPct = (FALL_ASLEEP_MIN / totalMin * 100).toFixed(1);
    var cyclePct = (CYCLE_MIN / totalMin * 100).toFixed(1);

    var fallSeg = document.createElement('div');
    fallSeg.className = 'sl-tl-seg fall-asleep';
    fallSeg.style.flex = fallPct;
    fallSeg.title = 'Fall asleep: ~14 min';
    bar.appendChild(fallSeg);

    for (var i = 1; i <= cycles; i++) {
      var seg = document.createElement('div');
      seg.className = 'sl-tl-seg cycle';
      if (i % 2 === 0) seg.className += ' even';
      seg.style.flex = cyclePct;
      seg.textContent = i <= 4 ? i : '';
      seg.title = 'Cycle ' + i + ': 90 min';
      bar.appendChild(seg);
    }
  }

  window.slCalculate = function () {
    var isModeWake = document.getElementById('sl-tab-wake').classList.contains('active');
    var anchorMin;

    if (isModeWake) {
      anchorMin = timeInputToMinutes(document.getElementById('sl-wake-time').value);
      if (anchorMin === null) { alert('Please enter a wake-up time.'); return; }
    } else {
      anchorMin = timeInputToMinutes(document.getElementById('sl-bed-time').value);
      if (anchorMin === null) { alert('Please enter a bedtime.'); return; }
    }

    var list = document.getElementById('sl-cycle-list');
    list.innerHTML = '';

    var cycleCounts = isModeWake ? [6, 5, 4, 3] : [6, 5, 4, 3];
    var firstRender = true;

    cycleCounts.forEach(function (cycles) {
      var sleepMin = FALL_ASLEEP_MIN + cycles * CYCLE_MIN;
      var resultMin;

      if (isModeWake) {
        resultMin = anchorMin - sleepMin;
      } else {
        resultMin = anchorMin + sleepMin;
      }

      var badge = getBadge(cycles);
      var li = document.createElement('li');
      li.className = 'sl-cycle-item' + (badge.cls === 'sl-badge-best' ? ' best' : badge.cls === 'sl-badge-good' ? ' good' : '');

      var hours = Math.floor(sleepMin / 60);
      var mins = sleepMin % 60;
      var durationStr = hours + 'h ' + (mins > 0 ? mins + 'm' : '');

      li.innerHTML =
        '<span class="sl-cycle-time">' + minutesToTime(resultMin) + '</span>' +
        '<span class="sl-cycle-meta">' +
          '<span class="sl-cycle-cycles">' + cycles + ' sleep cycles</span>' +
          '<span class="sl-cycle-duration">' + durationStr + ' total sleep</span>' +
        '</span>' +
        '<span class="sl-badge ' + badge.cls + '">' + badge.label + '</span>';

      if (firstRender) {
        renderTimeline(cycles);
        firstRender = false;
      }

      list.appendChild(li);
    });

    var titleEl = document.getElementById('sl-results-title');
    titleEl.textContent = isModeWake
      ? 'Best bedtimes if you want to wake up at ' + minutesToTime(anchorMin)
      : 'Best wake-up times if you go to bed at ' + minutesToTime(anchorMin);

    document.getElementById('sl-results').classList.add('visible');
    document.getElementById('sl-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  document.addEventListener('keydown', function (e) {
    if (e.key === 'Enter') { window.slCalculate(); }
  });
})();
</script>

</div>

---

> **Disclaimer:** Sleep needs vary by individual age and health. This calculator is for general guidance only and is not medical advice.

## Related Tools

- Track your daily nutrition → [Calorie Calculator](/tools/calorie-calculator/)
- Check your body mass index → [BMI Calculator](/tools/bmi-calculator/)
- Find out your exact age → [Age Calculator](/tools/age-calculator/)
