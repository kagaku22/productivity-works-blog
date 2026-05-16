---
title: "睡眠負債計算ツール - あなたの睡眠不足を可視化"
date: 2025-05-16
description: "睡眠負債（睡眠不足の蓄積）を計算します。1週間の睡眠時間を入力するだけで、不足量と回復プランを自動算出。"
categories: ["無料ツール"]
slug: "sleep-debt-calculator"
ShowToc: false
cover:
  image: "/images/covers/sleep-debt-calculator.png"
  alt: "睡眠負債計算ツール"
---

<div id="sd-app">

<style>
#sd-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 760px;
  margin: 0 auto;
  color: #1a1a2e;
}
#sd-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 1.6rem 0 0.8rem;
  color: #1a1a2e;
}
#sd-app .sd-intro {
  background: #eef2ff;
  border-left: 4px solid #4f46e5;
  border-radius: 6px;
  padding: 1rem 1.2rem;
  margin-bottom: 1.6rem;
  font-size: 0.93rem;
  color: #3730a3;
  line-height: 1.7;
}
#sd-app .sd-card {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.4rem 1.6rem;
  margin-bottom: 1.2rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#sd-app label {
  display: block;
  font-size: 0.88rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.3rem;
}
#sd-app .sd-ideal-row {
  display: flex;
  align-items: center;
  gap: 1rem;
}
#sd-app .sd-ideal-row input[type=range] {
  flex: 1;
  accent-color: #4f46e5;
}
#sd-app .sd-ideal-val {
  font-size: 1.3rem;
  font-weight: 700;
  color: #4f46e5;
  min-width: 4rem;
  text-align: center;
}
#sd-app .sd-days-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 0.6rem;
}
@media (max-width: 540px) {
  #sd-app .sd-days-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}
#sd-app .sd-day-cell {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
}
#sd-app .sd-day-cell span {
  font-size: 0.78rem;
  font-weight: 600;
  color: #6b7280;
}
#sd-app .sd-day-cell input[type=number] {
  width: 100%;
  padding: 0.4rem 0.2rem;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-size: 1rem;
  text-align: center;
  outline: none;
  transition: border-color 0.2s;
}
#sd-app .sd-day-cell input[type=number]:focus {
  border-color: #4f46e5;
  box-shadow: 0 0 0 2px rgba(79,70,229,0.15);
}
#sd-app .sd-btn {
  display: block;
  width: 100%;
  padding: 0.85rem;
  background: #4f46e5;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 1rem;
  transition: background 0.2s;
}
#sd-app .sd-btn:hover { background: #4338ca; }
#sd-app .sd-result { display: none; }
#sd-app .sd-result.visible { display: block; }
#sd-app .sd-summary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 0.8rem;
  margin-bottom: 1.2rem;
}
#sd-app .sd-stat {
  background: #f9fafb;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
  padding: 0.9rem 1rem;
  text-align: center;
}
#sd-app .sd-stat .sd-stat-val {
  font-size: 1.8rem;
  font-weight: 800;
  color: #4f46e5;
  line-height: 1.1;
}
#sd-app .sd-stat .sd-stat-lbl {
  font-size: 0.76rem;
  color: #6b7280;
  margin-top: 0.3rem;
  line-height: 1.4;
}
#sd-app .sd-badge {
  display: inline-block;
  padding: 0.35rem 0.9rem;
  border-radius: 999px;
  font-size: 0.9rem;
  font-weight: 700;
  margin-bottom: 1rem;
}
#sd-app .sd-badge.none     { background: #d1fae5; color: #065f46; }
#sd-app .sd-badge.mild     { background: #fef3c7; color: #92400e; }
#sd-app .sd-badge.moderate { background: #ffe4e6; color: #9f1239; }
#sd-app .sd-badge.severe   { background: #fce7f3; color: #831843; }
#sd-app .sd-chart-wrap {
  overflow-x: auto;
  margin-bottom: 1.2rem;
}
#sd-app .sd-chart {
  display: flex;
  align-items: flex-end;
  gap: 0.5rem;
  height: 160px;
  padding: 0.5rem 0.2rem 0;
  min-width: 320px;
}
#sd-app .sd-bar-group {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  height: 100%;
  justify-content: flex-end;
}
#sd-app .sd-bars {
  display: flex;
  align-items: flex-end;
  gap: 3px;
  width: 100%;
  height: 130px;
}
#sd-app .sd-bar {
  flex: 1;
  border-radius: 4px 4px 0 0;
  min-height: 4px;
  transition: height 0.4s ease;
}
#sd-app .sd-bar.ideal  { background: #c7d2fe; }
#sd-app .sd-bar.actual { background: #4f46e5; }
#sd-app .sd-bar-lbl {
  font-size: 0.7rem;
  color: #6b7280;
  margin-top: 4px;
}
#sd-app .sd-legend {
  display: flex;
  gap: 1rem;
  font-size: 0.8rem;
  color: #374151;
  margin-bottom: 0.8rem;
}
#sd-app .sd-legend-dot {
  width: 12px; height: 12px;
  border-radius: 3px;
  display: inline-block;
  margin-right: 4px;
  vertical-align: middle;
}
#sd-app .sd-recovery {
  background: #f0fdf4;
  border: 1px solid #bbf7d0;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  margin-bottom: 1.2rem;
}
#sd-app .sd-recovery h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #166534;
  margin: 0 0 0.4rem;
}
#sd-app .sd-recovery p {
  font-size: 0.9rem;
  color: #166534;
  margin: 0;
  line-height: 1.7;
}
#sd-app .sd-tips { list-style: none; padding: 0; margin: 0; }
#sd-app .sd-tips li {
  padding: 0.5rem 0;
  border-bottom: 1px solid #f3f4f6;
  font-size: 0.9rem;
  color: #374151;
  padding-left: 1.4rem;
  position: relative;
  line-height: 1.6;
}
#sd-app .sd-tips li:last-child { border-bottom: none; }
#sd-app .sd-tips li::before {
  content: "•";
  color: #4f46e5;
  font-weight: 700;
  position: absolute;
  left: 0.3rem;
}
#sd-app .sd-cta {
  background: #fffbeb;
  border: 1px solid #fde68a;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  margin-top: 1.6rem;
  font-size: 0.9rem;
  color: #78350f;
  line-height: 1.7;
}
#sd-app .sd-cta a {
  color: #b45309;
  font-weight: 700;
}
</style>

<div class="sd-intro">
理想の睡眠時間と、今週実際に眠った時間を入力してください。蓄積した睡眠負債の合計と回復プランを自動で計算します。小数点（例: 6.5時間）も入力可能です。
</div>

<!-- 理想睡眠時間 -->
<div class="sd-card">
  <h2 style="margin-top:0">ステップ1：理想の睡眠時間を設定</h2>
  <label for="sd-ideal">1日あたりの理想の睡眠時間</label>
  <div class="sd-ideal-row">
    <input type="range" id="sd-ideal" min="6" max="10" step="0.5" value="8" oninput="sdUpdateIdeal(this.value)">
    <div class="sd-ideal-val" id="sd-ideal-display">8.0 時間</div>
  </div>
  <p style="font-size:0.8rem;color:#6b7280;margin:0.5rem 0 0">成人の多くは7〜9時間が推奨されています。65歳以上は7〜8時間が目安です。</p>
</div>

<!-- 7日間の睡眠ログ -->
<div class="sd-card">
  <h2 style="margin-top:0">ステップ2：今週の睡眠時間を入力</h2>
  <p style="font-size:0.85rem;color:#6b7280;margin:0 0 1rem">各曜日に実際に眠った時間（時間単位）を入力してください</p>
  <div class="sd-days-grid">
    <div class="sd-day-cell"><span>月</span><input type="number" id="sd-day0" min="0" max="24" step="0.5" value="7" placeholder="0"></div>
    <div class="sd-day-cell"><span>火</span><input type="number" id="sd-day1" min="0" max="24" step="0.5" value="6" placeholder="0"></div>
    <div class="sd-day-cell"><span>水</span><input type="number" id="sd-day2" min="0" max="24" step="0.5" value="6.5" placeholder="0"></div>
    <div class="sd-day-cell"><span>木</span><input type="number" id="sd-day3" min="0" max="24" step="0.5" value="5.5" placeholder="0"></div>
    <div class="sd-day-cell"><span>金</span><input type="number" id="sd-day4" min="0" max="24" step="0.5" value="7" placeholder="0"></div>
    <div class="sd-day-cell"><span>土</span><input type="number" id="sd-day5" min="0" max="24" step="0.5" value="8.5" placeholder="0"></div>
    <div class="sd-day-cell"><span>日</span><input type="number" id="sd-day6" min="0" max="24" step="0.5" value="7.5" placeholder="0"></div>
  </div>
  <button class="sd-btn" onclick="sdCalculate()">睡眠負債を計算する</button>
</div>

<!-- 結果 -->
<div class="sd-result" id="sd-result">

  <div class="sd-card">
    <h2 style="margin-top:0">計算結果</h2>
    <div id="sd-badge-wrap"></div>

    <div class="sd-summary-grid">
      <div class="sd-stat">
        <div class="sd-stat-val" id="sd-total-debt">0.0</div>
        <div class="sd-stat-lbl">今週の睡眠負債（時間）</div>
      </div>
      <div class="sd-stat">
        <div class="sd-stat-val" id="sd-avg-actual">0.0</div>
        <div class="sd-stat-lbl">平均実際睡眠（時間/夜）</div>
      </div>
      <div class="sd-stat">
        <div class="sd-stat-val" id="sd-monthly-debt">0.0</div>
        <div class="sd-stat-lbl">このペースの月間負債（時間）</div>
      </div>
      <div class="sd-stat">
        <div class="sd-stat-val" id="sd-recovery-days">0</div>
        <div class="sd-stat-lbl">回復に必要な日数（目安）</div>
      </div>
    </div>

    <!-- Bar chart -->
    <h3 style="font-size:0.95rem;font-weight:700;color:#374151;margin:0 0 0.5rem">理想 vs 実際の睡眠時間（曜日別）</h3>
    <div class="sd-legend">
      <span><span class="sd-legend-dot" style="background:#c7d2fe"></span>理想</span>
      <span><span class="sd-legend-dot" style="background:#4f46e5"></span>実際</span>
    </div>
    <div class="sd-chart-wrap">
      <div class="sd-chart" id="sd-chart"></div>
    </div>
  </div>

  <!-- 回復プラン -->
  <div class="sd-recovery" id="sd-recovery-box">
    <h3>回復プラン</h3>
    <p id="sd-recovery-text"></p>
  </div>

  <!-- 対策Tips -->
  <div class="sd-card">
    <h2 style="margin-top:0">睡眠負債を減らすためのヒント</h2>
    <ul class="sd-tips" id="sd-tips-list"></ul>
  </div>

</div>

<!-- freee CTA -->
<div class="sd-cta">
健康管理も仕事も効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で日々の管理を自動化</a>
</div>

<script>
(function() {
  var DAYS = ['月','火','水','木','金','土','日'];
  var TIPS_ALL = [
    '就寝・起床時間を毎日（週末も）固定する。体内時計を整える最も効果的な習慣です。',
    '就寝30分前はスマートフォン・PC・テレビの画面を見ない。ブルーライトがメラトニン分泌を妨げます。',
    '寝室を18〜20℃に保ち、できる限り遮光する。体温低下が入眠を促します。',
    'カフェイン（コーヒー・エナジードリンク）は就寝6時間前に切り上げる。',
    '午後3時前に10〜20分の短い昼寝を取ると、急性の眠気を解消できます。それ以上は夜に影響します。',
    '起床後30分以内に強い光（日光が理想）を浴びる。体内時計のリセットに有効です。',
    '就寝前のアルコールは睡眠の質を大幅に低下させます。寝つきはよくなっても睡眠が浅くなります。',
    '睡眠負債の返済は一度に行わず、1晩あたり30〜60分の上乗せを数日続けるのが効果的です。',
    '就寝前の「ルーティン」（照明を落とす・軽いストレッチ・読書など）で脳に入眠を促します。',
    '2週間の睡眠ログをつけ、特定の曜日・行動との関連を把握しましょう。'
  ];

  window.sdUpdateIdeal = function(val) {
    document.getElementById('sd-ideal-display').textContent = parseFloat(val).toFixed(1) + ' 時間';
  };

  window.sdCalculate = function() {
    var ideal = parseFloat(document.getElementById('sd-ideal').value);
    var actuals = [];
    for (var i = 0; i < 7; i++) {
      var v = parseFloat(document.getElementById('sd-day' + i).value);
      actuals.push(isNaN(v) || v < 0 ? 0 : Math.min(v, 24));
    }

    var totalDebt = 0;
    for (var i = 0; i < 7; i++) {
      totalDebt += Math.max(0, ideal - actuals[i]);
    }
    var avgActual = actuals.reduce(function(a,b){return a+b;},0) / 7;
    var monthlyDebt = totalDebt * (30/7);
    var recoveryDays = totalDebt <= 0 ? 0 : Math.ceil(totalDebt / 1);

    // カテゴリ
    var cat, catLabel;
    if (totalDebt <= 0)       { cat = 'none';     catLabel = '睡眠負債なし'; }
    else if (totalDebt < 3)   { cat = 'mild';     catLabel = '軽度の睡眠負債'; }
    else if (totalDebt < 7)   { cat = 'moderate'; catLabel = '中等度の睡眠負債'; }
    else                       { cat = 'severe';   catLabel = '重度の睡眠負債'; }

    // 数値表示
    document.getElementById('sd-total-debt').textContent   = totalDebt.toFixed(1);
    document.getElementById('sd-avg-actual').textContent   = avgActual.toFixed(1);
    document.getElementById('sd-monthly-debt').textContent = monthlyDebt.toFixed(1);
    document.getElementById('sd-recovery-days').textContent = recoveryDays;

    // バッジ
    document.getElementById('sd-badge-wrap').innerHTML =
      '<span class="sd-badge ' + cat + '">' + catLabel + '</span>';

    // グラフ
    var maxH = Math.max(ideal, Math.max.apply(null, actuals));
    var chartH = 130;
    var html = '';
    for (var i = 0; i < 7; i++) {
      var ih = Math.round((ideal / maxH) * chartH);
      var ah = Math.round((actuals[i] / maxH) * chartH);
      html += '<div class="sd-bar-group">' +
        '<div class="sd-bars">' +
          '<div class="sd-bar ideal"  style="height:' + ih + 'px" title="理想: ' + ideal + '時間"></div>' +
          '<div class="sd-bar actual" style="height:' + ah + 'px" title="実際: ' + actuals[i] + '時間"></div>' +
        '</div>' +
        '<div class="sd-bar-lbl">' + DAYS[i] + '</div>' +
      '</div>';
    }
    document.getElementById('sd-chart').innerHTML = html;

    // 回復プランテキスト
    var recText;
    if (totalDebt <= 0) {
      recText = '素晴らしい！今週は睡眠負債がありません。この習慣を続けましょう。';
    } else {
      recText = '今週の睡眠負債は ' + totalDebt.toFixed(1) + ' 時間です。' +
        '回復するには、1晩あたり1時間多く眠ることを ' + recoveryDays + ' 日間続けることが目安です。' +
        'このペースが続くと月間負債は ' + monthlyDebt.toFixed(1) + ' 時間に達します。早めに対処しましょう。';
    }
    document.getElementById('sd-recovery-text').textContent = recText;

    // Tips選択
    var tips;
    if (cat === 'none')         tips = [TIPS_ALL[0], TIPS_ALL[5], TIPS_ALL[2], TIPS_ALL[6], TIPS_ALL[8]];
    else if (cat === 'mild')    tips = [TIPS_ALL[0], TIPS_ALL[1], TIPS_ALL[3], TIPS_ALL[7], TIPS_ALL[8]];
    else if (cat === 'moderate')tips = [TIPS_ALL[4], TIPS_ALL[0], TIPS_ALL[1], TIPS_ALL[3], TIPS_ALL[7]];
    else                         tips = [TIPS_ALL[7], TIPS_ALL[4], TIPS_ALL[0], TIPS_ALL[3], TIPS_ALL[9]];

    var thtml = '';
    tips.forEach(function(t){ thtml += '<li>' + t + '</li>'; });
    document.getElementById('sd-tips-list').innerHTML = thtml;

    // 結果表示
    var res = document.getElementById('sd-result');
    res.classList.add('visible');
    setTimeout(function(){ res.scrollIntoView({behavior:'smooth', block:'start'}); }, 100);
  };
})();
</script>

</div>

---

## 関連ツール

> ポモドーロタイマー → [ポモドーロタイマーツール](/ja/tools/pomodoro-timer/)
> 睡眠計算 → [睡眠計算ツール](/ja/tools/sleep-calculator/)

