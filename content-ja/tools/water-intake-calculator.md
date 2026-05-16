---
title: "水分摂取量計算ツール - 1日の必要水分量ガイド"
date: 2025-05-16
description: "体重・運動量・気候に基づいて1日に必要な水分量を計算。毎日の水分補給を記録して健康管理をサポートします。"
categories: ["無料ツール"]
slug: "water-intake-calculator"
ShowToc: false
cover:
  image: "/images/covers/water-intake-calculator.png"
  alt: "水分摂取量計算ツール"
---

<div id="wi-app">
<style>
#wi-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Yu Gothic UI', Meiryo, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #1a2b3c;
}
#wi-app h2 {
  font-size: 1.25rem;
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
  font-size: 1.05rem;
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
  line-height: 1.6;
}
#wi-app .wi-tips-list li:last-child { border-bottom: none; }
#wi-app .wi-tips-list li::before {
  content: attr(data-icon);
  position: absolute;
  left: 0;
  font-size: 1.1rem;
}
#wi-app .wi-cta {
  background: #fffbea;
  border: 1.5px solid #f5c842;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1rem;
  font-size: 0.95rem;
  line-height: 1.6;
}
#wi-app .wi-cta a {
  color: #c47d00;
  font-weight: 700;
}
</style>

<h2>あなたの情報を入力してください</h2>

<div class="wi-card">
  <div class="wi-unit-toggle">
    <button class="wi-unit-btn active" id="wi-kg-btn" onclick="wiSetUnit('kg')">kg</button>
    <button class="wi-unit-btn" id="wi-lbs-btn" onclick="wiSetUnit('lbs')">lbs</button>
  </div>
  <div class="wi-grid">
    <div>
      <label for="wi-weight">体重（<span id="wi-unit-label">kg</span>）</label>
      <input type="number" id="wi-weight" min="1" max="500" placeholder="例：60" />
    </div>
    <div>
      <label for="wi-activity">運動量</label>
      <select id="wi-activity">
        <option value="1.0">ほぼ運動しない（座り仕事中心）</option>
        <option value="1.1">軽い運動（週1〜3日）</option>
        <option value="1.2" selected>適度な運動（週3〜5日）</option>
        <option value="1.35">活発（週6〜7日）</option>
        <option value="1.5">非常に活発（毎日ハードに運動）</option>
      </select>
    </div>
    <div>
      <label for="wi-climate">気候・環境</label>
      <select id="wi-climate">
        <option value="0">涼しい・寒い</option>
        <option value="0.3" selected>普通（温暖）</option>
        <option value="0.5">暑い</option>
        <option value="0.75">非常に暑い・多湿</option>
      </select>
    </div>
  </div>
  <button class="wi-calc-btn" onclick="wiCalculate()">1日の必要水分量を計算する</button>
</div>

<div class="wi-result-box" id="wi-result-box">
  <div class="wi-result-liters" id="wi-result-liters">—</div>
  <div class="wi-result-label">リットル / 日 が目安です</div>
  <div class="wi-result-glasses" id="wi-result-glasses"></div>
</div>

<div class="wi-tracker wi-card" id="wi-tracker">
  <h2 style="margin-top:0">今日の水分補給トラッカー</h2>
  <div class="wi-tracker-status" id="wi-tracker-status">0 / 0 杯 ログ済み</div>
  <div class="wi-progress-bar-wrap">
    <div class="wi-progress-bar-fill" id="wi-progress-fill"></div>
  </div>
  <div class="wi-progress-label" id="wi-progress-label">0%</div>
  <div class="wi-glasses-area" id="wi-glasses-area"></div>
  <div class="wi-congrats" id="wi-congrats">今日の目標達成！素晴らしい水分補給ができました！</div>
  <div class="wi-tracker-actions">
    <button class="wi-log-btn" onclick="wiLogGlass()">+ コップ1杯（250ml）を記録</button>
    <button class="wi-reset-btn" onclick="wiResetDay()">リセット</button>
  </div>
</div>

<h2>水分補給を習慣化するコツ</h2>
<div class="wi-card">
  <ul class="wi-tips-list">
    <li data-icon="🌅">朝起きたらまずコップ1杯の水を飲む習慣をつけましょう。</li>
    <li data-icon="⏰">スマートフォンに1時間おきの水分補給アラームをセットする。</li>
    <li data-icon="🥒">きゅうり・スイカ・レタスなど水分の多い食材を積極的に摂る。</li>
    <li data-icon="🏃">運動30分ごとに追加で250〜500mlを摂取しましょう。</li>
    <li data-icon="☕">カフェイン飲料は利尿作用があるため、コーヒー1杯に対して水を1杯追加する。</li>
    <li data-icon="💛">尿の色が薄い黄色なら適切な水分補給ができているサイン。濃い場合は要注意。</li>
    <li data-icon="🥤">デスクに水筒を置いておくだけで飲む頻度が自然に増えます。</li>
    <li data-icon="🌡️">夏や高温多湿の環境では、目安量より最低500ml多めに飲みましょう。</li>
  </ul>
</div>

> 健康管理も仕事も効率化 → [freee会計で日々の管理を自動化](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

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
      alert('体重を正しく入力してください。');
      return;
    }
    var weightKg = wiUnit === 'kg' ? rawWeight : rawWeight * 0.453592;
    var activity = parseFloat(document.getElementById('wi-activity').value);
    var climate  = parseFloat(document.getElementById('wi-climate').value);

    var baseLiters = (weightKg * 35) / 1000;
    var total = baseLiters * activity + climate;
    total = Math.round(total * 10) / 10;

    var glasses = Math.ceil((total * 1000) / 250);

    wiGoalLiters  = total;
    wiGoalGlasses = glasses;

    document.getElementById('wi-result-liters').textContent = total.toFixed(1) + ' L';
    document.getElementById('wi-result-glasses').textContent =
      '1日あたり約 ' + glasses + ' 杯（コップ250ml換算）が目安です。';
    document.getElementById('wi-result-box').classList.add('show');

    localStorage.setItem(WI_KEY_GOAL, total);

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
    var logged = wiGetLogged();
    var goal   = wiGoalGlasses;
    var pct    = goal > 0 ? Math.min(100, Math.round((logged / goal) * 100)) : 0;

    document.getElementById('wi-tracker-status').textContent =
      logged + ' / ' + goal + ' 杯 ログ済み';
    document.getElementById('wi-progress-fill').style.width = pct + '%';
    document.getElementById('wi-progress-label').textContent = pct + '%';

    var area = document.getElementById('wi-glasses-area');
    area.innerHTML = '';
    for (var i = 0; i < goal; i++) {
      var g = document.createElement('span');
      g.className = 'wi-glass' + (i < logged ? ' filled' : '');
      g.textContent = '\uD83E\uDD64';
      g.title = (i + 1) + '杯目';
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

  (function init() {
    wiCheckDate();
    var savedGoal = parseFloat(localStorage.getItem(WI_KEY_GOAL) || '0');
    if (savedGoal > 0) {
      wiGoalLiters  = savedGoal;
      wiGoalGlasses = Math.ceil((savedGoal * 1000) / 250);
      document.getElementById('wi-result-liters').textContent = savedGoal.toFixed(1) + ' L';
      document.getElementById('wi-result-glasses').textContent =
        '1日あたり約 ' + wiGoalGlasses + ' 杯（コップ250ml換算）が目安です。';
      document.getElementById('wi-result-box').classList.add('show');
      wiRenderTracker();
      document.getElementById('wi-tracker').classList.add('show');
    }
  })();
})();
</script>
</div>

---

## 関連ツール

> BMI計算 → [BMI計算ツール](/ja/tools/bmi-calculator/)
> 体脂肪率計算 → [体脂肪率計算ツール](/ja/tools/body-fat-calculator/)
> カロリー計算 → [カロリー計算ツール](/ja/tools/calorie-calculator/)

