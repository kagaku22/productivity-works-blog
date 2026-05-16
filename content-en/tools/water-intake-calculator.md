---
title: "Water Intake Calculator - Daily Hydration Guide"
date: 2025-05-16
description: "Calculate how much water you need daily based on weight, activity level, and climate. Track your daily water intake."
categories: ["Free Tools"]
slug: "water-intake-calculator"
ShowToc: false
cover:
  image: "/images/covers/water-intake-calculator.png"
  alt: "Water Intake Calculator"
---

<div id="wi-app">
<style>
#wi-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #1a2b3c;
}
#wi-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  color: #0077cc;
}
#wi-app .wi-card {
  background: #f0f8ff;
  border: 1px solid #b3d9f5;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1.25rem;
}
#wi-app .wi-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 520px) {
  #wi-app .wi-grid { grid-template-columns: 1fr; }
}
#wi-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 0.3rem;
  color: #345;
}
#wi-app input[type="number"],
#wi-app select {
  width: 100%;
  padding: 0.55rem 0.75rem;
  border: 1.5px solid #90c4e8;
  border-radius: 8px;
  font-size: 1rem;
  background: #fff;
  box-sizing: border-box;
  transition: border-color 0.2s;
}
#wi-app input[type="number"]:focus,
#wi-app select:focus {
  border-color: #0077cc;
  outline: none;
}
#wi-app .wi-unit-toggle {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 0.75rem;
}
#wi-app .wi-unit-btn {
  flex: 1;
  padding: 0.45rem;
  border: 1.5px solid #90c4e8;
  border-radius: 8px;
  background: #fff;
  font-size: 0.9rem;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.2s;
}
#wi-app .wi-unit-btn.active {
  background: #0077cc;
  color: #fff;
  border-color: #0077cc;
}
#wi-app .wi-calc-btn {
  display: block;
  width: 100%;
  padding: 0.9rem;
  background: linear-gradient(135deg, #0077cc, #00aaff);
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 1rem;
  letter-spacing: 0.02em;
  transition: opacity 0.2s;
}
#wi-app .wi-calc-btn:hover { opacity: 0.9; }
#wi-app .wi-result-box {
  display: none;
  background: linear-gradient(135deg, #e8f5ff, #d0eeff);
  border: 2px solid #0077cc;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1.25rem;
  text-align: center;
}
#wi-app .wi-result-box.show { display: block; }
#wi-app .wi-result-liters {
  font-size: 3rem;
  font-weight: 800;
  color: #0055aa;
  line-height: 1.1;
}
#wi-app .wi-result-label {
  font-size: 1rem;
  color: #0077cc;
  font-weight: 600;
  margin-top: 0.2rem;
}
#wi-app .wi-result-glasses {
  font-size: 0.95rem;
  color: #345;
  margin-top: 0.5rem;
}
#wi-app .wi-tracker {
  display: none;
  margin-bottom: 1.25rem;
}
#wi-app .wi-tracker.show { display: block; }
#wi-app .wi-progress-bar-wrap {
  background: #d0e8f5;
  border-radius: 999px;
  height: 22px;
  overflow: hidden;
  margin: 0.6rem 0 0.4rem;
}
#wi-app .wi-progress-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #00aaff, #0077cc);
  border-radius: 999px;
  transition: width 0.4s ease;
  width: 0%;
}
#wi-app .wi-progress-label {
  font-size: 0.85rem;
  color: #456;
  text-align: right;
}
#wi-app .wi-glasses-area {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin: 1rem 0 0.75rem;
}
#wi-app .wi-glass {
  font-size: 2rem;
  cursor: pointer;
  opacity: 0.25;
  transition: opacity 0.2s, transform 0.15s;
  user-select: none;
  line-height: 1;
}
#wi-app .wi-glass.filled { opacity: 1; }
#wi-app .wi-glass:hover { transform: scale(1.15); }
#wi-app .wi-tracker-status {
  font-size: 1rem;
  font-weight: 700;
  color: #0055aa;
  margin-bottom: 0.5rem;
}
#wi-app .wi-tracker-actions {
  display: flex;
  gap: 0.75rem;
  margin-top: 0.75rem;
}
#wi-app .wi-log-btn {
  flex: 1;
  padding: 0.65rem;
  background: #0077cc;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s;
}
#wi-app .wi-log-btn:hover { opacity: 0.85; }
#wi-app .wi-reset-btn {
  padding: 0.65rem 1.1rem;
  background: #fff;
  color: #0077cc;
  border: 1.5px solid #0077cc;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s;
}
#wi-app .wi-reset-btn:hover { background: #e8f4ff; }
#wi-app .wi-congrats {
  display: none;
  background: #e6fff0;
  border: 2px solid #22bb66;
  border-radius: 10px;
  padding: 0.9rem 1.2rem;
  font-weight: 700;
  color: #117733;
  text-align: center;
  margin-bottom: 0.75rem;
  font-size: 1rem;
}
#wi-app .wi-congrats.show { display: block; }
#wi-app .wi-tips-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
#wi-app .wi-tips-list li {
  padding: 0.5rem 0 0.5rem 1.75rem;
  border-bottom: 1px solid #c8e4f5;
  position: relative;
  font-size: 0.95rem;
  line-height: 1.5;
}
#wi-app .wi-tips-list li:last-child { border-bottom: none; }
#wi-app .wi-tips-list li::before {
  content: attr(data-icon);
  position: absolute;
  left: 0;
  font-size: 1.1rem;
}
#wi-app .wi-related {
  background: #f5f9fd;
  border: 1px solid #c0d8ec;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1rem;
}
#wi-app .wi-related p {
  margin: 0 0 0.5rem;
  font-weight: 700;
  color: #0055aa;
  font-size: 0.95rem;
}
#wi-app .wi-related a {
  display: inline-block;
  margin: 0.2rem 0.4rem 0.2rem 0;
  padding: 0.3rem 0.75rem;
  background: #fff;
  border: 1.5px solid #90c4e8;
  border-radius: 20px;
  color: #0077cc;
  text-decoration: none;
  font-size: 0.88rem;
  font-weight: 600;
  transition: background 0.2s;
}
#wi-app .wi-related a:hover { background: #e0f0ff; }
</style>

<h2>Enter Your Details</h2>

<div class="wi-card">
  <div class="wi-unit-toggle">
    <button class="wi-unit-btn active" id="wi-kg-btn" onclick="wiSetUnit('kg')">kg</button>
    <button class="wi-unit-btn" id="wi-lbs-btn" onclick="wiSetUnit('lbs')">lbs</button>
  </div>
  <div class="wi-grid">
    <div>
      <label for="wi-weight">Body Weight (<span id="wi-unit-label">kg</span>)</label>
      <input type="number" id="wi-weight" min="1" max="500" placeholder="e.g. 70" />
    </div>
    <div>
      <label for="wi-activity">Activity Level</label>
      <select id="wi-activity">
        <option value="1.0">Sedentary (little/no exercise)</option>
        <option value="1.1">Light (1-3 days/week)</option>
        <option value="1.2" selected>Moderate (3-5 days/week)</option>
        <option value="1.35">Active (6-7 days/week)</option>
        <option value="1.5">Very Active (intense daily)</option>
      </select>
    </div>
    <div>
      <label for="wi-climate">Climate</label>
      <select id="wi-climate">
        <option value="0">Cool / Cold</option>
        <option value="0.3" selected>Moderate</option>
        <option value="0.5">Hot</option>
        <option value="0.75">Very Hot / Humid</option>
      </select>
    </div>
  </div>
  <button class="wi-calc-btn" onclick="wiCalculate()">Calculate My Daily Water Intake</button>
</div>

<div class="wi-result-box" id="wi-result-box">
  <div class="wi-result-liters" id="wi-result-liters">—</div>
  <div class="wi-result-label">liters per day recommended</div>
  <div class="wi-result-glasses" id="wi-result-glasses"></div>
</div>

<div class="wi-tracker wi-card" id="wi-tracker">
  <h2 style="margin-top:0">Today's Hydration Tracker</h2>
  <div class="wi-tracker-status" id="wi-tracker-status">0 / 0 glasses logged today</div>
  <div class="wi-progress-bar-wrap">
    <div class="wi-progress-bar-fill" id="wi-progress-fill"></div>
  </div>
  <div class="wi-progress-label" id="wi-progress-label">0%</div>
  <div class="wi-glasses-area" id="wi-glasses-area"></div>
  <div class="wi-congrats" id="wi-congrats">You've hit your daily hydration goal! Great work!</div>
  <div class="wi-tracker-actions">
    <button class="wi-log-btn" onclick="wiLogGlass()">+ Log a Glass (250ml)</button>
    <button class="wi-reset-btn" onclick="wiResetDay()">Reset Day</button>
  </div>
</div>

<h2>Tips for Staying Hydrated</h2>
<div class="wi-card">
  <ul class="wi-tips-list">
    <li data-icon="🌅">Start your day with a full glass of water before coffee or breakfast.</li>
    <li data-icon="⏰">Set hourly reminders on your phone to drink water throughout the day.</li>
    <li data-icon="🍃">Eat water-rich foods: cucumbers, watermelon, lettuce, and celery all count.</li>
    <li data-icon="🏃">Drink an extra 250–500 ml for every 30 minutes of exercise.</li>
    <li data-icon="☕">Caffeinated drinks are mild diuretics — balance each cup with extra water.</li>
    <li data-icon="💛">Check your urine color: pale yellow means good hydration; dark yellow means drink more.</li>
    <li data-icon="🥤">Keep a reusable water bottle visible at your desk as a constant reminder.</li>
    <li data-icon="🌡️">In hot or humid weather, increase intake by at least 500 ml above your baseline.</li>
  </ul>
</div>

<div class="wi-related">
  <p>Related Free Tools</p>
  <a href="/tools/bmi-calculator/">BMI Calculator</a>
  <a href="/tools/calorie-calculator/">Calorie Calculator</a>
  <a href="/tools/sleep-calculator/">Sleep Calculator</a>
  <a href="/tools/pomodoro-timer/">Pomodoro Timer</a>
</div>

<script>
(function() {
  var wiUnit = 'kg';
  var wiGoalLiters = 0;
  var wiGoalGlasses = 0;
  var WI_KEY_GLASSES = 'wi_glasses_logged';
  var WI_KEY_DATE    = 'wi_date';
  var WI_KEY_GOAL    = 'wi_goal_liters';

  function wiSetUnit(u) {
    wiUnit = u;
    document.getElementById('wi-unit-label').textContent = u;
    document.getElementById('wi-kg-btn').classList.toggle('active', u === 'kg');
    document.getElementById('wi-lbs-btn').classList.toggle('active', u === 'lbs');
  }
  window.wiSetUnit = wiSetUnit;

  function wiCalculate() {
    var rawWeight = parseFloat(document.getElementById('wi-weight').value);
    if (!rawWeight || rawWeight <= 0) {
      alert('Please enter a valid body weight.');
      return;
    }
    var weightKg = wiUnit === 'kg' ? rawWeight : rawWeight * 0.453592;
    var activity = parseFloat(document.getElementById('wi-activity').value);
    var climate  = parseFloat(document.getElementById('wi-climate').value);

    // Base: 35 ml per kg, adjusted by activity & climate
    var baseLiters = (weightKg * 35) / 1000;
    var total = baseLiters * activity + climate;
    total = Math.round(total * 10) / 10;

    var glasses = Math.ceil((total * 1000) / 250);

    wiGoalLiters  = total;
    wiGoalGlasses = glasses;

    document.getElementById('wi-result-liters').textContent = total.toFixed(1) + ' L';
    document.getElementById('wi-result-glasses').textContent =
      'That is approximately ' + glasses + ' standard glasses (250 ml each) per day.';
    document.getElementById('wi-result-box').classList.add('show');

    // Save goal
    localStorage.setItem(WI_KEY_GOAL, total);

    // Reset day if new date
    wiCheckDate();
    wiRenderTracker();
    document.getElementById('wi-tracker').classList.add('show');
  }
  window.wiCalculate = wiCalculate;

  function wiCheckDate() {
    var today = new Date().toDateString();
    var saved = localStorage.getItem(WI_KEY_DATE);
    if (saved !== today) {
      localStorage.setItem(WI_KEY_DATE, today);
      localStorage.setItem(WI_KEY_GLASSES, '0');
    }
  }

  function wiGetLogged() {
    return parseInt(localStorage.getItem(WI_KEY_GLASSES) || '0', 10);
  }

  function wiRenderTracker() {
    var logged  = wiGetLogged();
    var goal    = wiGoalGlasses;
    var pct     = goal > 0 ? Math.min(100, Math.round((logged / goal) * 100)) : 0;

    document.getElementById('wi-tracker-status').textContent =
      logged + ' / ' + goal + ' glasses logged today';
    document.getElementById('wi-progress-fill').style.width = pct + '%';
    document.getElementById('wi-progress-label').textContent = pct + '%';

    // Glasses icons
    var area = document.getElementById('wi-glasses-area');
    area.innerHTML = '';
    for (var i = 0; i < goal; i++) {
      var g = document.createElement('span');
      g.className = 'wi-glass' + (i < logged ? ' filled' : '');
      g.textContent = '\uD83E\uDD64';
      g.title = 'Glass ' + (i + 1);
      g.setAttribute('data-idx', i);
      g.onclick = wiGlassClick;
      area.appendChild(g);
    }

    var congrats = document.getElementById('wi-congrats');
    if (logged >= goal && goal > 0) {
      congrats.classList.add('show');
    } else {
      congrats.classList.remove('show');
    }
  }

  function wiGlassClick(e) {
    var idx    = parseInt(e.currentTarget.getAttribute('data-idx'), 10);
    var logged = wiGetLogged();
    // clicking a filled glass un-logs, clicking unfilled logs up to that glass
    if (idx < logged) {
      localStorage.setItem(WI_KEY_GLASSES, idx);
    } else {
      localStorage.setItem(WI_KEY_GLASSES, idx + 1);
    }
    wiRenderTracker();
  }

  function wiLogGlass() {
    var logged = wiGetLogged();
    if (logged < wiGoalGlasses) {
      localStorage.setItem(WI_KEY_GLASSES, logged + 1);
      wiRenderTracker();
    }
  }
  window.wiLogGlass = wiLogGlass;

  function wiResetDay() {
    localStorage.setItem(WI_KEY_GLASSES, '0');
    wiRenderTracker();
  }
  window.wiResetDay = wiResetDay;

  // On load: restore goal if saved
  (function init() {
    wiCheckDate();
    var savedGoal = parseFloat(localStorage.getItem(WI_KEY_GOAL) || '0');
    if (savedGoal > 0) {
      wiGoalLiters  = savedGoal;
      wiGoalGlasses = Math.ceil((savedGoal * 1000) / 250);
      document.getElementById('wi-result-liters').textContent = savedGoal.toFixed(1) + ' L';
      document.getElementById('wi-result-glasses').textContent =
        'That is approximately ' + wiGoalGlasses + ' standard glasses (250 ml each) per day.';
      document.getElementById('wi-result-box').classList.add('show');
      wiRenderTracker();
      document.getElementById('wi-tracker').classList.add('show');
    }
  })();
})();
</script>
</div>
