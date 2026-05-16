---
title: "体脂肪率計算ツール - 体脂肪率を簡単推定"
date: 2025-05-16
description: "米海軍式とBMI法で体脂肪率を計算。フィットネスカテゴリと健康インサイトをパーソナライズして提供。"
categories: ["無料ツール"]
slug: "body-fat-calculator"
ShowToc: false
cover:
  image: "/images/covers/body-fat-calculator.png"
  alt: "体脂肪率計算ツール"
---

<div id="bf-app">

<style>
#bf-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Yu Gothic UI', Meiryo, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #1a1a2e;
}
#bf-app * { box-sizing: border-box; }
#bf-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  color: #0f3460;
  border-left: 4px solid #e94560;
  padding-left: 0.6rem;
}
#bf-app .gender-row {
  display: flex;
  gap: 12px;
  margin-bottom: 1.2rem;
}
#bf-app .gender-btn {
  flex: 1;
  padding: 12px;
  border: 2px solid #dde3f0;
  border-radius: 10px;
  background: #f8faff;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 700;
  color: #555;
  transition: all 0.2s;
}
#bf-app .gender-btn.active {
  border-color: #e94560;
  background: #fff0f3;
  color: #e94560;
}
#bf-app .input-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 1.2rem;
}
#bf-app .input-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
#bf-app .input-group label {
  font-size: 0.82rem;
  font-weight: 700;
  color: #555;
  letter-spacing: 0.03em;
}
#bf-app .input-group .input-wrap {
  position: relative;
}
#bf-app .input-group input {
  width: 100%;
  padding: 10px 44px 10px 12px;
  border: 2px solid #dde3f0;
  border-radius: 8px;
  font-size: 1rem;
  background: #f8faff;
  transition: border-color 0.2s;
  outline: none;
}
#bf-app .input-group input:focus {
  border-color: #0f3460;
  background: #fff;
}
#bf-app .input-group .unit {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 0.78rem;
  color: #888;
  font-weight: 700;
  pointer-events: none;
}
#bf-app .calc-btn {
  width: 100%;
  padding: 14px;
  background: linear-gradient(135deg, #0f3460, #e94560);
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s;
  margin-bottom: 1.5rem;
  letter-spacing: 0.05em;
}
#bf-app .calc-btn:hover { opacity: 0.9; }
#bf-app .results {
  display: none;
  animation: bfFadeIn 0.4s ease;
}
@keyframes bfFadeIn {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
#bf-app .result-hero {
  text-align: center;
  background: linear-gradient(135deg, #0f3460 0%, #16213e 100%);
  border-radius: 14px;
  padding: 2rem 1rem 1.5rem;
  color: #fff;
  margin-bottom: 1.2rem;
}
#bf-app .result-hero .pct {
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1;
  margin-bottom: 0.3rem;
}
#bf-app .result-hero .cat-badge {
  display: inline-block;
  padding: 4px 18px;
  border-radius: 20px;
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 1rem;
}
#bf-app .gauge-container {
  margin: 0.8rem auto 0;
  max-width: 420px;
}
#bf-app .gauge-bar {
  height: 18px;
  border-radius: 9px;
  background: linear-gradient(to right, #4caf50, #8bc34a, #ffeb3b, #ff9800, #f44336);
  position: relative;
  overflow: visible;
}
#bf-app .gauge-needle {
  position: absolute;
  top: -6px;
  width: 4px;
  height: 30px;
  background: #fff;
  border-radius: 2px;
  transform: translateX(-50%);
  box-shadow: 0 0 0 2px rgba(0,0,0,0.4);
  transition: left 0.6s cubic-bezier(0.34,1.56,0.64,1);
}
#bf-app .gauge-labels {
  display: flex;
  justify-content: space-between;
  margin-top: 6px;
  font-size: 0.65rem;
  color: rgba(255,255,255,0.75);
}
#bf-app .stats-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 1.2rem;
}
#bf-app .stat-card {
  background: #f8faff;
  border: 2px solid #dde3f0;
  border-radius: 12px;
  padding: 1rem;
  text-align: center;
}
#bf-app .stat-card .stat-val {
  font-size: 1.75rem;
  font-weight: 800;
  color: #0f3460;
}
#bf-app .stat-card .stat-lbl {
  font-size: 0.76rem;
  color: #777;
  font-weight: 600;
  margin-top: 2px;
}
#bf-app .chart-wrap {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  background: #f8faff;
  border: 2px solid #dde3f0;
  border-radius: 12px;
  padding: 1.2rem 1.5rem;
  margin-bottom: 1.2rem;
}
#bf-app canvas#bfPie {
  flex-shrink: 0;
}
#bf-app .legend { flex: 1; }
#bf-app .legend-item {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
  font-size: 0.9rem;
}
#bf-app .legend-dot {
  width: 14px;
  height: 14px;
  border-radius: 4px;
  flex-shrink: 0;
}
#bf-app .legend-val {
  font-weight: 800;
  font-size: 1rem;
  color: #0f3460;
}
#bf-app .methods-note {
  background: #fffbf0;
  border: 1px solid #ffe082;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  font-size: 0.84rem;
  color: #7a6000;
  line-height: 1.7;
  margin-bottom: 1.2rem;
}
#bf-app .category-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.85rem;
  margin-bottom: 1.5rem;
}
#bf-app .category-table th {
  background: #0f3460;
  color: #fff;
  padding: 8px 12px;
  text-align: left;
  font-weight: 700;
}
#bf-app .category-table td {
  padding: 7px 12px;
  border-bottom: 1px solid #eee;
}
#bf-app .category-table tr:nth-child(even) td { background: #f8faff; }
#bf-app .category-table tr.highlight td {
  background: #fff0f3 !important;
  font-weight: 700;
  color: #e94560;
}
#bf-app .cta-box {
  background: linear-gradient(135deg, #f0f4ff, #fff0f3);
  border: 2px solid #dde3f0;
  border-radius: 12px;
  padding: 1.2rem 1.5rem;
  margin-top: 1.5rem;
  font-size: 0.92rem;
  line-height: 1.7;
  color: #333;
}
#bf-app .cta-box p { margin: 0; }
#bf-app .cta-box a { color: #0f3460; font-weight: 700; }
#bf-app .error-msg {
  color: #e94560;
  font-size: 0.88rem;
  font-weight: 600;
  margin-bottom: 0.8rem;
  display: none;
  padding: 8px 12px;
  background: #fff0f3;
  border-radius: 8px;
  border: 1px solid #ffc0cb;
}
@media (max-width: 500px) {
  #bf-app .input-grid { grid-template-columns: 1fr; }
  #bf-app .stats-grid { grid-template-columns: 1fr 1fr; }
  #bf-app .chart-wrap { flex-direction: column; }
}
</style>

<h2>体脂肪率計算ツール</h2>

<div class="gender-row">
  <button class="gender-btn active" id="btnMale" onclick="bfSetGender('male')">男性</button>
  <button class="gender-btn" id="btnFemale" onclick="bfSetGender('female')">女性</button>
</div>

<div class="input-grid">
  <div class="input-group">
    <label>身長</label>
    <div class="input-wrap">
      <input type="number" id="bfHeight" placeholder="170" min="100" max="250" value="">
      <span class="unit">cm</span>
    </div>
  </div>
  <div class="input-group">
    <label>体重</label>
    <div class="input-wrap">
      <input type="number" id="bfWeight" placeholder="65" min="30" max="300" value="">
      <span class="unit">kg</span>
    </div>
  </div>
  <div class="input-group">
    <label>ウエスト周囲径</label>
    <div class="input-wrap">
      <input type="number" id="bfWaist" placeholder="82" min="40" max="200" value="">
      <span class="unit">cm</span>
    </div>
  </div>
  <div class="input-group">
    <label>首周囲径</label>
    <div class="input-wrap">
      <input type="number" id="bfNeck" placeholder="37" min="20" max="80" value="">
      <span class="unit">cm</span>
    </div>
  </div>
  <div class="input-group" id="hipGroup" style="display:none;">
    <label>ヒップ周囲径</label>
    <div class="input-wrap">
      <input type="number" id="bfHip" placeholder="94" min="50" max="200" value="">
      <span class="unit">cm</span>
    </div>
  </div>
  <div class="input-group">
    <label>年齢</label>
    <div class="input-wrap">
      <input type="number" id="bfAge" placeholder="30" min="10" max="120" value="">
      <span class="unit">歳</span>
    </div>
  </div>
</div>

<div class="error-msg" id="bfError"></div>

<button class="calc-btn" onclick="bfCalculate()">体脂肪率を計算する</button>

<div class="results" id="bfResults">
  <div class="result-hero">
    <div class="pct" id="bfPctDisplay">--%</div>
    <div class="cat-badge" id="bfCatBadge">--</div>
    <div class="gauge-container">
      <div class="gauge-bar">
        <div class="gauge-needle" id="bfNeedle" style="left:0%"></div>
      </div>
      <div class="gauge-labels">
        <span>必須脂肪</span>
        <span>アスリート</span>
        <span>フィットネス</span>
        <span>平均</span>
        <span>肥満</span>
      </div>
    </div>
  </div>

  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-val" id="bfNavyVal">--%</div>
      <div class="stat-lbl">米海軍式</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="bfBmiVal">--%</div>
      <div class="stat-lbl">BMI推定法</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="bfLeanVal">-- kg</div>
      <div class="stat-lbl">除脂肪体重</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="bfFatVal">-- kg</div>
      <div class="stat-lbl">体脂肪量</div>
    </div>
  </div>

  <div class="chart-wrap">
    <canvas id="bfPie" width="140" height="140"></canvas>
    <div class="legend">
      <div class="legend-item">
        <div class="legend-dot" style="background:#e94560;"></div>
        <div>
          <div class="legend-val" id="lgFatPct">--%</div>
          <div style="color:#777;font-size:0.8rem;">体脂肪率</div>
        </div>
      </div>
      <div class="legend-item">
        <div class="legend-dot" style="background:#0f3460;"></div>
        <div>
          <div class="legend-val" id="lgLeanPct">--%</div>
          <div style="color:#777;font-size:0.8rem;">除脂肪（筋肉・骨・水分）</div>
        </div>
      </div>
    </div>
  </div>

  <div class="methods-note">
    <strong>計算方法について：</strong>「<strong>米海軍式（US Navy法）</strong>」は、ウエスト・首・ヒップ（女性）の周囲径を使った対数計算式で、米軍で採用されている実績ある方法です。「<strong>BMI推定法</strong>」はDeurenbergらの式（BF% = 1.20×BMI + 0.23×年齢 − 10.8×性別係数 − 5.4）を使用します。両者の平均値を表示しています。より正確な計測にはDEXA法（二重エネルギーX線吸収法）を推奨します。
  </div>

  <h2>体脂肪率カテゴリ一覧</h2>
  <table class="category-table" id="bfCatTable">
    <thead>
      <tr><th>カテゴリ</th><th>男性</th><th>女性</th></tr>
    </thead>
    <tbody>
      <tr id="catEssential"><td>必須脂肪</td><td>2〜5%</td><td>10〜13%</td></tr>
      <tr id="catAthletes"><td>アスリート</td><td>6〜13%</td><td>14〜20%</td></tr>
      <tr id="catFitness"><td>フィットネス</td><td>14〜17%</td><td>21〜24%</td></tr>
      <tr id="catAverage"><td>平均的</td><td>18〜24%</td><td>25〜31%</td></tr>
      <tr id="catObese"><td>肥満</td><td>25%以上</td><td>32%以上</td></tr>
    </tbody>
  </table>

  <div class="cta-box">
    <p>健康管理も仕事も効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で日々の管理を自動化</a></p>
  </div>
</div>

<script>
(function() {
  var bfGender = 'male';

  window.bfSetGender = function(g) {
    bfGender = g;
    document.getElementById('btnMale').classList.toggle('active', g === 'male');
    document.getElementById('btnFemale').classList.toggle('active', g === 'female');
    document.getElementById('hipGroup').style.display = g === 'female' ? '' : 'none';
  };

  function bfNavy(gender, height, waist, neck, hip) {
    if (gender === 'male') {
      return 495 / (1.0324 - 0.19077 * Math.log10(waist - neck) + 0.15456 * Math.log10(height)) - 450;
    } else {
      return 495 / (1.29579 - 0.35004 * Math.log10(waist + hip - neck) + 0.22100 * Math.log10(height)) - 450;
    }
  }

  function bfBmi(bmi, age, gender) {
    var sex = gender === 'male' ? 1 : 0;
    return (1.20 * bmi) + (0.23 * age) - (10.8 * sex) - 5.4;
  }

  function getCategory(bf, gender) {
    if (gender === 'male') {
      if (bf < 6)  return { name: '必須脂肪',     color: '#4caf50', row: 'catEssential', pos: 5  };
      if (bf < 14) return { name: 'アスリート',   color: '#8bc34a', row: 'catAthletes',  pos: 22 };
      if (bf < 18) return { name: 'フィットネス', color: '#ffeb3b', row: 'catFitness',   pos: 43 };
      if (bf < 25) return { name: '平均的',       color: '#ff9800', row: 'catAverage',   pos: 65 };
      return               { name: '肥満',         color: '#f44336', row: 'catObese',    pos: 88 };
    } else {
      if (bf < 14) return { name: '必須脂肪',     color: '#4caf50', row: 'catEssential', pos: 5  };
      if (bf < 21) return { name: 'アスリート',   color: '#8bc34a', row: 'catAthletes',  pos: 22 };
      if (bf < 25) return { name: 'フィットネス', color: '#ffeb3b', row: 'catFitness',   pos: 43 };
      if (bf < 32) return { name: '平均的',       color: '#ff9800', row: 'catAverage',   pos: 65 };
      return               { name: '肥満',         color: '#f44336', row: 'catObese',    pos: 88 };
    }
  }

  function drawPie(fatPct) {
    var canvas = document.getElementById('bfPie');
    if (!canvas) return;
    var ctx = canvas.getContext('2d');
    var cx = 70, cy = 70, r = 58;
    ctx.clearRect(0, 0, 140, 140);
    var fatAngle = (fatPct / 100) * Math.PI * 2;
    // Fat slice
    ctx.beginPath();
    ctx.moveTo(cx, cy);
    ctx.arc(cx, cy, r, -Math.PI/2, -Math.PI/2 + fatAngle);
    ctx.closePath();
    ctx.fillStyle = '#e94560';
    ctx.fill();
    // Lean slice
    ctx.beginPath();
    ctx.moveTo(cx, cy);
    ctx.arc(cx, cy, r, -Math.PI/2 + fatAngle, -Math.PI/2 + Math.PI*2);
    ctx.closePath();
    ctx.fillStyle = '#0f3460';
    ctx.fill();
    // Center hole
    ctx.beginPath();
    ctx.arc(cx, cy, r * 0.52, 0, Math.PI * 2);
    ctx.fillStyle = '#f8faff';
    ctx.fill();
    // Center label
    ctx.fillStyle = '#0f3460';
    ctx.font = 'bold 15px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(fatPct.toFixed(1) + '%', cx, cy);
  }

  window.bfCalculate = function() {
    var errEl = document.getElementById('bfError');
    errEl.style.display = 'none';

    var h     = parseFloat(document.getElementById('bfHeight').value);
    var w     = parseFloat(document.getElementById('bfWeight').value);
    var waist = parseFloat(document.getElementById('bfWaist').value);
    var neck  = parseFloat(document.getElementById('bfNeck').value);
    var age   = parseFloat(document.getElementById('bfAge').value);
    var hip   = parseFloat(document.getElementById('bfHip').value);

    if (!h || !w || !waist || !neck || !age) {
      errEl.textContent = '身長・体重・ウエスト・首・年齢をすべて入力してください。';
      errEl.style.display = 'block';
      return;
    }
    if (bfGender === 'female' && !hip) {
      errEl.textContent = '女性の場合、ヒップ周囲径の入力が必要です。';
      errEl.style.display = 'block';
      return;
    }
    if (waist <= neck) {
      errEl.textContent = 'ウエスト周囲径は首周囲径より大きい値を入力してください。';
      errEl.style.display = 'block';
      return;
    }

    var navy = bfNavy(bfGender, h, waist, neck, hip || 0);
    var bmi  = w / ((h/100) * (h/100));
    var bmiMethod = bfBmi(bmi, age, bfGender);

    navy      = Math.max(2, Math.min(70, navy));
    bmiMethod = Math.max(2, Math.min(70, bmiMethod));

    var avg      = (navy + bmiMethod) / 2;
    var fatMass  = (avg / 100) * w;
    var leanMass = w - fatMass;

    var cat = getCategory(avg, bfGender);

    // Update hero
    document.getElementById('bfPctDisplay').textContent = avg.toFixed(1) + '%';
    var badge = document.getElementById('bfCatBadge');
    badge.textContent = cat.name;
    badge.style.background = cat.color + '33';
    badge.style.color = cat.color;
    badge.style.border = '1.5px solid ' + cat.color;

    // Gauge needle
    document.getElementById('bfNeedle').style.left = cat.pos + '%';

    // Stats
    document.getElementById('bfNavyVal').textContent  = navy.toFixed(1) + '%';
    document.getElementById('bfBmiVal').textContent   = bmiMethod.toFixed(1) + '%';
    document.getElementById('bfLeanVal').textContent  = leanMass.toFixed(1) + ' kg';
    document.getElementById('bfFatVal').textContent   = fatMass.toFixed(1) + ' kg';

    // Legend
    document.getElementById('lgFatPct').textContent  = avg.toFixed(1) + '%';
    document.getElementById('lgLeanPct').textContent = (100 - avg).toFixed(1) + '%';

    // Pie chart
    drawPie(avg);

    // Highlight table row
    ['catEssential','catAthletes','catFitness','catAverage','catObese'].forEach(function(id) {
      document.getElementById(id).classList.remove('highlight');
    });
    document.getElementById(cat.row).classList.add('highlight');

    // Show results
    var res = document.getElementById('bfResults');
    res.style.display = 'block';
    res.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  };

  // Allow Enter key
  document.addEventListener('keydown', function(e) {
    if (e.key === 'Enter' && document.activeElement && document.activeElement.closest('#bf-app')) {
      bfCalculate();
    }
  });
})();
</script>

</div>
