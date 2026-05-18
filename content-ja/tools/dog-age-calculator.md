---
title: "犬年齢計算ツール - 犬の年齢を人間に換算"
date: 2025-06-13
description: "最新の科学的研究にもとづいて、愛犬の年齢を人間の年齢に換算します。小型・中型・大型・超大型犬に対応。"
categories: ["無料ツール"]
slug: "dog-age-calculator"
ShowToc: false
cover:
  image: "/images/covers/dog-age-calculator.png"
  alt: "犬年齢計算ツール"
---

<div id="da-app">

<style>
#da-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
}
#da-app *, #da-app *::before, #da-app *::after {
  box-sizing: border-box;
}
#da-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 1.6rem 0 0.8rem;
  color: #1a1a2e;
}
#da-app .da-intro {
  background: linear-gradient(135deg, #fff8f0 0%, #fff3e0 100%);
  border-left: 4px solid #f4a226;
  border-radius: 0 10px 10px 0;
  padding: 14px 18px;
  margin-bottom: 24px;
  font-size: 0.95rem;
  color: #5a4a2a;
  line-height: 1.7;
}
#da-app .da-card {
  background: #fff;
  border: 1px solid #e8e8f0;
  border-radius: 14px;
  padding: 24px;
  margin-bottom: 20px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.06);
}
#da-app .da-form-row {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  align-items: flex-end;
  margin-bottom: 18px;
}
#da-app .da-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex: 1;
  min-width: 130px;
}
#da-app .da-field label {
  font-size: 0.83rem;
  font-weight: 700;
  color: #555;
  letter-spacing: 0.02em;
}
#da-app .da-field input,
#da-app .da-field select {
  padding: 10px 14px;
  border: 2px solid #e0e0ea;
  border-radius: 8px;
  font-size: 1rem;
  color: #1a1a2e;
  background: #fafafa;
  transition: border-color 0.2s;
  outline: none;
  font-family: inherit;
}
#da-app .da-field input:focus,
#da-app .da-field select:focus {
  border-color: #f4a226;
  background: #fff;
}
#da-app .da-btn {
  padding: 12px 28px;
  background: linear-gradient(135deg, #f4a226 0%, #e8891a 100%);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: transform 0.15s, box-shadow 0.15s;
  white-space: nowrap;
  align-self: flex-end;
  font-family: inherit;
}
#da-app .da-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 16px rgba(244,162,38,0.4);
}
#da-app .da-btn:active {
  transform: translateY(0);
}
#da-app .da-result {
  display: none;
  animation: daFadeIn 0.4s ease;
}
#da-app .da-result.active {
  display: block;
}
@keyframes daFadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
#da-app .da-result-hero {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  border-radius: 14px;
  padding: 28px 24px;
  text-align: center;
  color: #fff;
  margin-bottom: 20px;
  position: relative;
  overflow: hidden;
}
#da-app .da-result-hero::before {
  content: '';
  position: absolute;
  top: -40px; right: -40px;
  width: 160px; height: 160px;
  background: rgba(244,162,38,0.12);
  border-radius: 50%;
}
#da-app .da-result-hero .da-paw {
  font-size: 2.4rem;
  margin-bottom: 8px;
}
#da-app .da-result-hero .da-human-age {
  font-size: 3.6rem;
  font-weight: 800;
  color: #f4a226;
  line-height: 1;
  margin-bottom: 4px;
}
#da-app .da-result-hero .da-human-age-label {
  font-size: 1rem;
  color: rgba(255,255,255,0.7);
  margin-bottom: 16px;
}
#da-app .da-stage-badge {
  display: inline-block;
  padding: 6px 18px;
  border-radius: 50px;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.04em;
}
#da-app .da-stage-puppy    { background: #4caf50; color: #fff; }
#da-app .da-stage-junior   { background: #8bc34a; color: #fff; }
#da-app .da-stage-adult    { background: #2196f3; color: #fff; }
#da-app .da-stage-mature   { background: #ff9800; color: #fff; }
#da-app .da-stage-senior   { background: #f44336; color: #fff; }
#da-app .da-stage-geriatric{ background: #9c27b0; color: #fff; }
#da-app .da-meta-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 14px;
  margin-bottom: 20px;
}
#da-app .da-meta-item {
  background: #f8f8fc;
  border-radius: 10px;
  padding: 14px 16px;
  text-align: center;
}
#da-app .da-meta-value {
  font-size: 1.5rem;
  font-weight: 700;
  color: #f4a226;
  margin-bottom: 2px;
}
#da-app .da-meta-label {
  font-size: 0.78rem;
  color: #888;
  letter-spacing: 0.03em;
}
/* Timeline */
#da-app .da-timeline {
  position: relative;
  padding: 10px 0;
  margin: 8px 0 20px;
}
#da-app .da-timeline-track {
  height: 10px;
  border-radius: 5px;
  background: linear-gradient(to right,
    #4caf50 0%, #4caf50 8%,
    #8bc34a 8%, #8bc34a 20%,
    #2196f3 20%, #2196f3 55%,
    #ff9800 55%, #ff9800 72%,
    #f44336 72%, #f44336 88%,
    #9c27b0 88%, #9c27b0 100%
  );
  position: relative;
}
#da-app .da-timeline-marker {
  position: absolute;
  top: -5px;
  width: 20px;
  height: 20px;
  background: #fff;
  border: 3px solid #1a1a2e;
  border-radius: 50%;
  transform: translateX(-50%);
  transition: left 0.5s ease;
  box-shadow: 0 2px 8px rgba(0,0,0,0.2);
}
#da-app .da-timeline-labels {
  display: flex;
  justify-content: space-between;
  margin-top: 8px;
  font-size: 0.70rem;
  color: #888;
}
/* Fun facts */
#da-app .da-fact {
  background: #f0f7ff;
  border-radius: 10px;
  padding: 14px 18px;
  margin-bottom: 10px;
  font-size: 0.92rem;
  color: #1a3a5c;
  line-height: 1.7;
  border-left: 3px solid #2196f3;
}
#da-app .da-fact-icon {
  font-weight: 700;
  color: #2196f3;
  margin-right: 6px;
}
/* Comparison table */
#da-app .da-table-wrap {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
  border-radius: 10px;
  border: 1px solid #e8e8f0;
}
#da-app table.da-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#da-app table.da-table thead tr {
  background: #1a1a2e;
  color: #fff;
}
#da-app table.da-table th {
  padding: 10px 14px;
  text-align: center;
  font-weight: 600;
  font-size: 0.82rem;
  letter-spacing: 0.03em;
}
#da-app table.da-table th:first-child {
  text-align: left;
}
#da-app table.da-table td {
  padding: 9px 14px;
  text-align: center;
  border-bottom: 1px solid #f0f0f6;
  color: #333;
}
#da-app table.da-table td:first-child {
  text-align: left;
  font-weight: 600;
  color: #1a1a2e;
}
#da-app table.da-table tbody tr:nth-child(even) {
  background: #fafafa;
}
#da-app table.da-table tbody tr.da-highlight {
  background: #fff8e1 !important;
  font-weight: 700;
}
#da-app table.da-table tbody tr:last-child td {
  border-bottom: none;
}
/* freee CTA */
#da-app .da-cta {
  background: linear-gradient(135deg, #e8f5e9 0%, #f1f8e9 100%);
  border: 1px solid #a5d6a7;
  border-radius: 12px;
  padding: 18px 22px;
  margin-top: 24px;
  font-size: 0.95rem;
  color: #2e7d32;
  line-height: 1.7;
}
#da-app .da-cta a {
  color: #1b5e20;
  font-weight: 700;
  text-decoration: underline;
}
#da-app .da-cta a:hover {
  color: #f4a226;
}
#da-app .da-error {
  color: #e53935;
  font-size: 0.88rem;
  margin-top: 6px;
  display: none;
}
@media (max-width: 480px) {
  #da-app .da-result-hero .da-human-age { font-size: 2.8rem; }
  #da-app .da-form-row { flex-direction: column; }
  #da-app .da-btn { width: 100%; }
}
</style>

<div class="da-intro">
「犬の1年は人間の7年」という説は科学的に不正確です。犬は生後1〜2年で急激に成長し、その後の老化ペースは品種サイズによって大きく異なります。このツールは最新の研究にもとづき、体重区分ごとに正確な換算を行います。
</div>

<!-- 入力カード -->
<div class="da-card">
  <h2 style="margin-top:0">愛犬の情報を入力</h2>
  <div class="da-form-row">
    <div class="da-field">
      <label for="da-years">年齢（年）</label>
      <input type="number" id="da-years" min="0" max="30" placeholder="例：5" />
    </div>
    <div class="da-field">
      <label for="da-months">月齢（月）</label>
      <input type="number" id="da-months" min="0" max="11" placeholder="0〜11" />
    </div>
    <div class="da-field" style="min-width:190px">
      <label for="da-size">体型サイズ</label>
      <select id="da-size">
        <option value="small">小型犬（10kg未満）</option>
        <option value="medium" selected>中型犬（10〜25kg）</option>
        <option value="large">大型犬（25〜45kg）</option>
        <option value="giant">超大型犬（45kg超）</option>
      </select>
    </div>
    <button class="da-btn" onclick="daCalculate()">換算する</button>
  </div>
  <div class="da-error" id="da-error">年齢を正しく入力してください（0〜30年）。</div>
</div>

<!-- 結果 -->
<div class="da-result" id="da-result">

  <div class="da-result-hero">
    <div class="da-paw">🐾</div>
    <div class="da-human-age" id="da-human-age">--</div>
    <div class="da-human-age-label">人間換算の年齢</div>
    <span class="da-stage-badge" id="da-stage-badge"></span>
  </div>

  <div class="da-meta-grid">
    <div class="da-meta-item">
      <div class="da-meta-value" id="da-dog-age-display">--</div>
      <div class="da-meta-label">犬の実際の年齢</div>
    </div>
    <div class="da-meta-item">
      <div class="da-meta-value" id="da-size-display">--</div>
      <div class="da-meta-label">体型区分</div>
    </div>
    <div class="da-meta-item">
      <div class="da-meta-value" id="da-lifespan">--</div>
      <div class="da-meta-label">平均寿命（目安）</div>
    </div>
    <div class="da-meta-item">
      <div class="da-meta-value" id="da-life-pct">--%</div>
      <div class="da-meta-label">ライフステージ進捗</div>
    </div>
  </div>

  <!-- ライフステージタイムライン -->
  <div class="da-card" style="padding:18px 20px">
    <strong style="font-size:0.88rem;color:#555;letter-spacing:0.03em">ライフステージ タイムライン</strong>
    <div class="da-timeline" style="margin-top:14px">
      <div class="da-timeline-track">
        <div class="da-timeline-marker" id="da-marker"></div>
      </div>
      <div class="da-timeline-labels">
        <span>子犬</span>
        <span>若犬</span>
        <span>成犬</span>
        <span>中年</span>
        <span>シニア</span>
        <span>老齢</span>
      </div>
    </div>
  </div>

  <!-- 豆知識 -->
  <h2>犬の老化にまつわる豆知識</h2>
  <div id="da-facts"></div>

  <!-- 比較表 -->
  <h2>犬の年齢 × 人間換算 早見表</h2>
  <div class="da-table-wrap">
    <table class="da-table" id="da-table">
      <thead>
        <tr>
          <th>犬の年齢</th>
          <th>小型犬</th>
          <th>中型犬</th>
          <th>大型犬</th>
          <th>超大型犬</th>
        </tr>
      </thead>
      <tbody id="da-tbody"></tbody>
    </table>
  </div>

  <!-- freee CTA -->
  <div class="da-cta">
    ペットの医療費・ごはん代・トリミング代など、ペット関連の出費をまとめて管理したいなら →
    <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で家計を自動管理</a>
  </div>

</div><!-- /.da-result -->

<script>
(function() {
  // 体型別・月齢別 人間換算年齢テーブル
  // 出典: AVMA ガイドライン & Horvath et al. (2020) Cell Systems エピジェネティック時計研究
  // 配列順: [小型, 中型, 大型, 超大型]
  var AGE_TABLE = {
    1:  [1, 1, 1, 1],
    2:  [3, 3, 3, 3],
    3:  [5, 5, 5, 5],
    4:  [7, 7, 7, 7],
    5:  [9, 9, 9, 9],
    6:  [10, 10, 10, 10],
    8:  [11, 11, 11, 11],
    10: [12, 12, 12, 12],
    12: [15, 15, 15, 15],
    18: [18, 18, 19, 20],
    24: [22, 22, 24, 26],
    36: [26, 28, 30, 34],
    48: [30, 34, 36, 42],
    60: [34, 38, 42, 50],
    72: [38, 42, 48, 58],
    84: [42, 46, 54, 66],
    96: [46, 50, 60, 74],
    108:[50, 54, 66, 82],
    120:[56, 60, 72, 90],
    132:[60, 65, 78, 98],
    144:[64, 70, 84, 106],
    156:[68, 75, 90, 114],
    168:[72, 80, 96, 122],
    180:[76, 85, 102, 130],
    192:[80, 90, 108, 138],
    204:[84, 95, 114, 145],
    216:[88, 100, 120, 152],
    228:[92, 105, 126, 159],
    240:[96, 110, 132, 166]
  };

  var SIZE_INDEX  = { small: 0, medium: 1, large: 2, giant: 3 };
  var SIZE_LABELS = { small: '小型犬', medium: '中型犬', large: '大型犬', giant: '超大型犬' };
  var LIFESPANS   = { small: '14〜16年', medium: '12〜14年', large: '10〜12年', giant: '8〜10年' };
  var LIFESPAN_YRS= { small: 15, medium: 13, large: 11, giant: 9 };

  var STAGE_LABELS = ['子犬期', '若犬期', '成犬期', '中年期', 'シニア期', '老齢期'];
  var STAGE_CLASSES= ['da-stage-puppy','da-stage-junior','da-stage-adult','da-stage-mature','da-stage-senior','da-stage-geriatric'];

  function interpolate(totalMonths, sizeIdx) {
    var keys = Object.keys(AGE_TABLE).map(Number).sort(function(a,b){return a-b;});
    if (totalMonths <= 0) return 0;
    if (totalMonths >= keys[keys.length-1]) return AGE_TABLE[keys[keys.length-1]][sizeIdx];
    for (var i = 0; i < keys.length - 1; i++) {
      if (totalMonths >= keys[i] && totalMonths <= keys[i+1]) {
        var lo = keys[i], hi = keys[i+1];
        var ratio = (totalMonths - lo) / (hi - lo);
        return Math.round(AGE_TABLE[lo][sizeIdx] + ratio * (AGE_TABLE[hi][sizeIdx] - AGE_TABLE[lo][sizeIdx]));
      }
    }
    return 0;
  }

  function getStage(totalMonths, size) {
    var lifespan = LIFESPAN_YRS[size] * 12;
    var ratio = totalMonths / lifespan;
    var idx;
    if (totalMonths < 12)   idx = 0;
    else if (totalMonths < 24) idx = 1;
    else if (ratio < 0.50)  idx = 2;
    else if (ratio < 0.68)  idx = 3;
    else if (ratio < 0.85)  idx = 4;
    else                    idx = 5;
    return { label: STAGE_LABELS[idx], cls: STAGE_CLASSES[idx], pct: ratio };
  }

  var FACTS = [
    '<span class="da-fact-icon">科学</span>2020年に米国セルシステムズ誌に掲載された研究では、犬のDNAメチル化パターンを調べた結果、生後1年で人間の約15〜30歳相当まで急速に老化することが判明しました。',
    '<span class="da-fact-icon">サイズ差</span>大型・超大型犬は小型犬に比べて老化が早い傾向があります。グレート・デーンの7歳は人間の約66歳相当ですが、チワワの7歳は約42歳相当にとどまります。',
    '<span class="da-fact-icon">長寿記録</span>世界最長寿として認定されたポルトガル産の牧羊犬「ボビ」は31歳165日まで生きました。換算すると人間の200歳超に相当するとも言われます。',
    '<span class="da-fact-icon">最初の1年</span>犬は生後1年で、人間の15年分に相当する発育を遂げます。新生児から性成熟まで、わずか12ヶ月で駆け抜けるのです。',
    '<span class="da-fact-icon">シニアケア</span>多くの獣医師は7歳以上をシニア犬と定義します。この段階からは年1回から年2回の健康診断への切り替えを推奨しています。早期発見が大切です。'
  ];

  function buildFacts() {
    document.getElementById('da-facts').innerHTML = FACTS.map(function(f){
      return '<div class="da-fact">' + f + '</div>';
    }).join('');
  }

  function buildTable(highlightMonths, size) {
    var rows = '';
    for (var yr = 1; yr <= 20; yr++) {
      var m = yr * 12;
      var isHL = (highlightMonths >= (m - 6) && highlightMonths < (m + 6));
      rows += '<tr' + (isHL ? ' class="da-highlight"' : '') + '>';
      rows += '<td>' + yr + '歳</td>';
      ['small','medium','large','giant'].forEach(function(s) {
        rows += '<td>' + interpolate(m, SIZE_INDEX[s]) + '</td>';
      });
      rows += '</tr>';
    }
    document.getElementById('da-tbody').innerHTML = rows;
  }

  window.daCalculate = function() {
    var yrsEl  = document.getElementById('da-years');
    var mosEl  = document.getElementById('da-months');
    var sizeEl = document.getElementById('da-size');
    var errEl  = document.getElementById('da-error');

    var yrs  = parseFloat(yrsEl.value)  || 0;
    var mos  = parseFloat(mosEl.value)  || 0;
    var size = sizeEl.value;

    if (yrs < 0 || yrs > 30 || mos < 0 || mos > 11 || (yrs === 0 && mos === 0)) {
      errEl.style.display = 'block';
      return;
    }
    errEl.style.display = 'none';

    var totalMonths = Math.round(yrs * 12 + mos);
    var humanAge    = interpolate(totalMonths, SIZE_INDEX[size]);
    var stage       = getStage(totalMonths, size);
    var lifePct     = Math.min(100, Math.round(stage.pct * 100));

    var dogAgeStr = '';
    if (yrs > 0) dogAgeStr += yrs + '歳';
    if (mos > 0) dogAgeStr += (dogAgeStr ? '' : '') + mos + 'ヶ月';

    document.getElementById('da-human-age').textContent     = humanAge;
    document.getElementById('da-dog-age-display').textContent = dogAgeStr || '生後1ヶ月未満';
    document.getElementById('da-size-display').textContent  = SIZE_LABELS[size];
    document.getElementById('da-lifespan').textContent      = LIFESPANS[size];
    document.getElementById('da-life-pct').textContent      = lifePct + '%';

    var badge = document.getElementById('da-stage-badge');
    badge.textContent = stage.label;
    badge.className   = 'da-stage-badge ' + stage.cls;

    var markerPct = Math.max(2, Math.min(96, lifePct));
    document.getElementById('da-marker').style.left = markerPct + '%';

    buildFacts();
    buildTable(totalMonths, size);

    var resultEl = document.getElementById('da-result');
    resultEl.classList.add('active');
    resultEl.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  };

  ['da-years','da-months','da-size'].forEach(function(id) {
    var el = document.getElementById(id);
    if (el) el.addEventListener('keydown', function(e) {
      if (e.key === 'Enter') window.daCalculate();
    });
  });
})();
</script>

</div>

---

## 関連ツール

> 年齢計算 → [年齢計算ツール](/ja/tools/age-calculator/)
> 出産予定日計算 → [出産予定日計算ツール](/ja/tools/pregnancy-due-date-calculator/)

