---
title: "スクリーンタイム計算ツール - 1日の画面時間を可視化"
date: 2025-05-16
categories: ["無料ツール"]
slug: "screen-time-calculator"
ShowToc: false
cover:
  image: "/images/covers/screen-time-calculator.png"
---

<div id="st-app">

<style>
#st-app {
  font-family: "Hiragino Sans", "Noto Sans JP", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 24px 16px;
  color: #1a1a2e;
}
#st-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 32px 0 12px;
  color: #1a1a2e;
}
#st-app h3 {
  font-size: 1.1rem;
  font-weight: 600;
  margin: 20px 0 8px;
  color: #16213e;
}
#st-app p {
  margin: 0 0 12px;
  line-height: 1.7;
}
#st-app .intro-box {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  border-radius: 14px;
  padding: 28px 24px;
  margin-bottom: 32px;
}
#st-app .intro-box h1 {
  font-size: 1.5rem;
  font-weight: 800;
  margin: 0 0 8px;
  color: #fff;
}
#st-app .intro-box p {
  margin: 0;
  opacity: 0.9;
  font-size: 0.95rem;
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
  font-size: 0.88rem;
  font-weight: 600;
  color: #444;
  margin-bottom: 10px;
}
#st-app .input-card .icon { font-size: 1.3rem; }
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
  min-width: 50px;
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
#st-app .results-section { display: none; }
#st-app .results-section.visible { display: block; }
#st-app .stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
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
  font-size: 1.8rem;
  font-weight: 800;
  color: #667eea;
  line-height: 1.1;
}
#st-app .stat-card .stat-label {
  font-size: 0.75rem;
  color: #888;
  margin-top: 4px;
  font-weight: 500;
  letter-spacing: 0.3px;
}
#st-app .stat-card.highlight {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-color: transparent;
}
#st-app .stat-card.highlight .stat-val,
#st-app .stat-card.highlight .stat-label { color: #fff; }
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
#st-app canvas#st-pie { max-width: 220px; max-height: 220px; }
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
#st-app .recommend-box.ok   { background: #e8f8f0; border: 2px solid #34d399; }
#st-app .recommend-box.warn { background: #fff8e1; border: 2px solid #fbbf24; }
#st-app .recommend-box.danger { background: #fef2f2; border: 2px solid #f87171; }
#st-app .recommend-box .rec-title {
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 6px;
}
#st-app .recommend-box.ok .rec-title     { color: #059669; }
#st-app .recommend-box.warn .rec-title   { color: #d97706; }
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
  font-size: 2rem;
  font-weight: 800;
  color: #c4b5fd;
  margin: 4px 0;
}
#st-app .lifetime-box p { color: #ccc; font-size: 0.88rem; }
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
  font-size: 0.91rem;
  line-height: 1.6;
}
#st-app .tips-list li .tip-icon { font-size: 1.2rem; flex-shrink: 0; margin-top: 1px; }
#st-app .instead-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(175px, 1fr));
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
#st-app .instead-card .inst-label { font-size: 0.8rem; color: #555; margin-top: 2px; }
#st-app .freee-cta {
  background: #fff7ed;
  border: 2px solid #fb923c;
  border-radius: 12px;
  padding: 20px 22px;
  margin: 32px 0;
  font-size: 0.93rem;
  line-height: 1.7;
}
#st-app .freee-cta strong { color: #ea580c; }
#st-app .freee-cta a {
  color: #ea580c;
  font-weight: 700;
  text-decoration: none;
}
#st-app .freee-cta a:hover { text-decoration: underline; }
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
  <h1>スクリーンタイム計算ツール</h1>
  <p>1日の画面時間を入力するだけで、年間・生涯にわたる画面時間と、その時間で何ができるかを可視化します。</p>
</div>

<h2>1日の画面時間を入力してください</h2>
<p>各カテゴリのスライダーを動かして、平均的な1日の時間（時間単位）を設定してください。</p>

<div class="inputs-grid" id="st-inputs">
  <div class="input-card">
    <label><span class="icon">💼</span> 仕事・学業</label>
    <div class="input-row">
      <input type="range" id="sl-work" min="0" max="14" step="0.5" value="8" oninput="stUpdate('work',this.value)">
      <span class="val-badge" id="vb-work">8時間</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">📱</span> SNS・ソーシャルメディア</label>
    <div class="input-row">
      <input type="range" id="sl-social" min="0" max="10" step="0.5" value="2" oninput="stUpdate('social',this.value)">
      <span class="val-badge" id="vb-social">2時間</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">🎬</span> 動画視聴・配信サービス</label>
    <div class="input-row">
      <input type="range" id="sl-stream" min="0" max="10" step="0.5" value="2" oninput="stUpdate('stream',this.value)">
      <span class="val-badge" id="vb-stream">2時間</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">🎮</span> ゲーム</label>
    <div class="input-row">
      <input type="range" id="sl-game" min="0" max="10" step="0.5" value="1" oninput="stUpdate('game',this.value)">
      <span class="val-badge" id="vb-game">1時間</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">🌐</span> Webブラウジング</label>
    <div class="input-row">
      <input type="range" id="sl-browse" min="0" max="10" step="0.5" value="1" oninput="stUpdate('browse',this.value)">
      <span class="val-badge" id="vb-browse">1時間</span>
    </div>
  </div>
  <div class="input-card">
    <label><span class="icon">📲</span> その他の画面利用</label>
    <div class="input-row">
      <input type="range" id="sl-other" min="0" max="10" step="0.5" value="0.5" oninput="stUpdate('other',this.value)">
      <span class="val-badge" id="vb-other">0.5時間</span>
    </div>
  </div>
</div>

<div style="margin-bottom:16px;">
  <label style="font-weight:600; font-size:0.93rem; color:#444;">現在の年齢（生涯予測に使用）：</label><br>
  <input type="number" id="st-age" min="5" max="79" value="30" style="margin-top:8px; padding:8px 12px; border:2px solid #e8eaf6; border-radius:8px; font-size:1rem; width:100px;">歳
</div>

<button class="calc-btn" onclick="stCalculate()">スクリーンタイムを計算する</button>

<div class="results-section" id="st-results">

  <h2>あなたのスクリーンタイム集計</h2>

  <div class="stats-grid">
    <div class="stat-card highlight">
      <div class="stat-val" id="res-daily">-</div>
      <div class="stat-label">時間 / 1日</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-weekly">-</div>
      <div class="stat-label">時間 / 1週間</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-monthly">-</div>
      <div class="stat-label">時間 / 1ヶ月</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-yearly">-</div>
      <div class="stat-label">時間 / 1年</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-days-year">-</div>
      <div class="stat-label">日分 / 1年</div>
    </div>
    <div class="stat-card">
      <div class="stat-val" id="res-pct-awake">-</div>
      <div class="stat-label">起きている時間の割合</div>
    </div>
  </div>

  <h2>カテゴリ別内訳</h2>
  <div class="chart-wrap">
    <canvas id="st-pie" width="220" height="220"></canvas>
    <div class="legend" id="st-legend"></div>
  </div>

  <div class="recommend-box" id="st-recommend">
    <div class="rec-title" id="rec-title"></div>
    <div id="rec-body"></div>
  </div>

  <div class="lifetime-box" id="st-lifetime">
    <h3>生涯スクリーンタイム予測</h3>
    <div class="life-stat" id="life-years">-</div>
    <p id="life-desc"></p>
    <div class="life-stat" id="life-days">-</div>
    <p id="life-desc2"></p>
  </div>

  <h2>スクリーンタイムを減らすためのヒント</h2>
  <ul class="tips-list" id="st-tips"></ul>

  <h2>その時間で何ができる？</h2>
  <p style="font-size:0.9rem;color:#666;">仕事以外のスクリーンタイム年間 <strong id="instead-hours">-</strong> 時間でできること：</p>
  <div class="instead-grid" id="st-instead"></div>

  <div class="freee-cta">
    <strong>業務時間を効率化して、もっと自由な時間を</strong><br>
    仕事での画面時間を減らすには、バックオフィス業務の自動化が近道です。<br>
    > 業務時間を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で作業時間を短縮</a>
  </div>

  <button class="reset-btn" onclick="stReset()">リセットして最初から</button>

</div>

<script>
(function() {
  var stVals = { work: 8, social: 2, stream: 2, game: 1, browse: 1, other: 0.5 };
  var stLabels = {
    work:   { label: '仕事・学業',       icon: '💼', color: '#667eea' },
    social: { label: 'SNS',              icon: '📱', color: '#f472b6' },
    stream: { label: '動画視聴',         icon: '🎬', color: '#fb923c' },
    game:   { label: 'ゲーム',           icon: '🎮', color: '#34d399' },
    browse: { label: 'Webブラウジング', icon: '🌐', color: '#60a5fa' },
    other:  { label: 'その他',           icon: '📲', color: '#a78bfa' }
  };

  window.stUpdate = function(key, val) {
    stVals[key] = parseFloat(val);
    var badge = document.getElementById('vb-' + key);
    if (badge) {
      var h = parseFloat(val);
      badge.textContent = (h % 1 === 0 ? h : h.toFixed(1)) + '時間';
    }
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
    document.getElementById('res-days-year').textContent = daysYear + '日';
    document.getElementById('res-pct-awake').textContent = pctAwake + '%';

    drawPie(stVals, total);

    var recBox   = document.getElementById('st-recommend');
    var recTitle = document.getElementById('rec-title');
    var recBody  = document.getElementById('rec-body');
    var nonWork  = total - stVals.work;

    recBox.className = 'recommend-box';
    if (nonWork <= 2) {
      recBox.classList.add('ok');
      recTitle.textContent = '優秀です！余暇のスクリーンタイムは適切な範囲内です。';
      recBody.textContent  = '専門家は成人の娯楽目的の画面利用を1日2時間以内に推奨しています。あなたはその範囲に収まっています。このバランスを維持しましょう。';
    } else if (nonWork <= 4) {
      recBox.classList.add('warn');
      recTitle.textContent = '少し多め — 改善の余地があります。';
      recBody.textContent  = '仕事以外のスクリーンタイムが1日' + nonWork.toFixed(1) + '時間あります。推奨される2時間を超えています。わずかな削減でも睡眠の質や集中力が改善される可能性があります。';
    } else {
      recBox.classList.add('danger');
      recTitle.textContent = '画面時間が多すぎます — 健康への影響に注意が必要です。';
      recBody.textContent  = '仕事以外のスクリーンタイムが1日' + nonWork.toFixed(1) + '時間と、推奨値の2倍以上です。過度な画面利用は睡眠障害、注意力の低下、不安感の増加と関連することが研究で示されています。デジタルデトックスを検討してみてください。';
    }

    var yearsLeft = 80 - age;
    if (yearsLeft < 0) yearsLeft = 0;
    var lifetimeHours = +(total * 365.25 * yearsLeft).toFixed(0);
    var lifetimeYears = +(lifetimeHours / 8760).toFixed(1);
    var lifetimeDays  = +(lifetimeHours / 24).toFixed(0);

    document.getElementById('life-years').textContent = lifetimeYears + '年分';
    document.getElementById('life-desc').textContent  =
      'のスクリーンタイムが残りの人生（' + age + '歳〜80歳）で発生します';
    document.getElementById('life-days').textContent  = Number(lifetimeDays).toLocaleString() + '日分';
    document.getElementById('life-desc2').textContent =
      '合計 ' + Number(lifetimeHours).toLocaleString() + ' 時間。もしこの10%でも別のことに使えたら、人生はどう変わるでしょうか？';

    var tips = buildTips(stVals, nonWork);
    var tipsList = document.getElementById('st-tips');
    tipsList.innerHTML = '';
    tips.forEach(function(t) {
      var li = document.createElement('li');
      li.innerHTML = '<span class="tip-icon">' + t.icon + '</span><span>' + t.text + '</span>';
      tipsList.appendChild(li);
    });

    var nonWorkYearly = nonWork * 365.25;
    document.getElementById('instead-hours').textContent = Math.round(nonWorkYearly) + '時間';
    buildInstead(nonWorkYearly);

    document.getElementById('st-results').className = 'results-section visible';
    document.getElementById('st-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function buildTips(vals, nonWork) {
    var tips = [];
    if (vals.social > 1.5) tips.push({ icon: '⏰', text: 'SNSアプリに1日の利用上限を設定しましょう。30分削減するだけで年間約180時間が節約できます。' });
    if (vals.stream > 2)   tips.push({ icon: '📺', text: '「1話だけ」ルールを導入。自動再生機能をオフにして、意図しない連続視聴を防ぎましょう。' });
    if (vals.game > 2)     tips.push({ icon: '🎮', text: 'ゲームは時間を決めてセッション制で行いましょう。物理的なタイマーを使うと終了の意識が高まります。' });
    if (vals.browse > 1.5) tips.push({ icon: '🌐', text: 'ブラウザ拡張機能（LeechBlockやStayFocusdなど）で無目的なブラウジング時間を制限しましょう。' });
    if (nonWork > 2) tips.push({ icon: '📵', text: '食卓・寝室・朝起きて最初の30分をスクリーンフリーゾーンに設定しましょう。' });
    if (nonWork > 3) tips.push({ icon: '🌿', text: '1日1時間の画面時間を散歩、運動、趣味に置き換えると、1週間以内に集中力の違いを感じられます。' });
    if (nonWork > 4) tips.push({ icon: '🔕', text: '不要なプッシュ通知をすべてオフに。通知があるたびに画面に引き戻されることを防ぎます。' });
    tips.push({ icon: '😴', text: '就寝60分前にすべての画面をオフにしましょう。ブルーライトはメラトニン分泌を妨げ、睡眠の質を低下させます。' });
    tips.push({ icon: '📖', text: '暇なとき用に本や手帳を手元に置いておきましょう。スマホに手を伸ばす代わりの習慣を作ることが大切です。' });
    tips.push({ icon: '👥', text: '定期的なリアルな交流の場を設けることで、SNSでのつながり欲求を自然に満たすことができます。' });
    return tips.slice(0, 7);
  }

  function buildInstead(nonWorkHoursPerYear) {
    var items = [
      { icon: '📚', val: Math.round(nonWorkHoursPerYear / 6),    label: '冊の本（1冊6時間換算）' },
      { icon: '🚶', val: Math.round(nonWorkHoursPerYear / 0.75), label: '回の散歩（45分換算）' },
      { icon: '🎨', val: Math.round(nonWorkHoursPerYear / 3),    label: '枚の絵・スケッチ' },
      { icon: '🍳', val: Math.round(nonWorkHoursPerYear / 1),    label: '回の自炊（1時間換算）' },
      { icon: '🧘', val: Math.round(nonWorkHoursPerYear / 0.5),  label: '回の瞑想（30分換算）' },
      { icon: '🎸', val: Math.round(nonWorkHoursPerYear / 500),  label: '年分の楽器練習時間' },
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
