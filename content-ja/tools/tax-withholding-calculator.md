---
title: "源泉徴収計算ツール - 給与天引き額を簡単計算"
date: 2025-05-16
categories: ["無料ツール"]
slug: "tax-withholding-calculator"
ShowToc: false
cover:
  image: "/images/covers/tax-withholding-calculator.png"
---

<div id="tw-app">

<style>
#tw-app {
  font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
}
#tw-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
  color: #1a1a2e;
}
#tw-app .tw-intro {
  background: #f0f4ff;
  border-left: 4px solid #4361ee;
  padding: 0.85rem 1.1rem;
  border-radius: 0 6px 6px 0;
  margin-bottom: 1.5rem;
  font-size: 0.92rem;
  color: #444;
  line-height: 1.7;
}
#tw-app .tw-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1.5rem;
  margin-bottom: 1.2rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.04);
}
#tw-app .tw-row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}
#tw-app .tw-field {
  flex: 1;
  min-width: 200px;
}
#tw-app .tw-field label {
  display: block;
  font-size: 0.83rem;
  font-weight: 700;
  color: #555;
  margin-bottom: 0.35rem;
}
#tw-app .tw-field input,
#tw-app .tw-field select {
  width: 100%;
  padding: 0.6rem 0.85rem;
  border: 1.5px solid #d1d5db;
  border-radius: 6px;
  font-size: 1rem;
  color: #1a1a2e;
  background: #fafafa;
  box-sizing: border-box;
  transition: border-color 0.2s;
  -webkit-appearance: none;
  font-family: inherit;
}
#tw-app .tw-field input:focus,
#tw-app .tw-field select:focus {
  outline: none;
  border-color: #4361ee;
  background: #fff;
}
#tw-app .tw-field .tw-hint {
  font-size: 0.76rem;
  color: #888;
  margin-top: 0.25rem;
  line-height: 1.5;
}
#tw-app .tw-btn {
  display: block;
  width: 100%;
  padding: 0.85rem;
  background: #4361ee;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  font-family: inherit;
}
#tw-app .tw-btn:hover {
  background: #3451d1;
  transform: translateY(-1px);
}
#tw-app .tw-btn:active {
  transform: translateY(0);
}
#tw-app .tw-results {
  display: none;
}
#tw-app .tw-results.visible {
  display: block;
}
#tw-app .tw-summary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(155px, 1fr));
  gap: 0.9rem;
  margin-bottom: 1.2rem;
}
#tw-app .tw-stat {
  background: #f8faff;
  border: 1px solid #dce5ff;
  border-radius: 8px;
  padding: 0.85rem 1rem;
  text-align: center;
}
#tw-app .tw-stat .tw-stat-label {
  font-size: 0.73rem;
  color: #666;
  font-weight: 700;
  margin-bottom: 0.3rem;
  line-height: 1.4;
}
#tw-app .tw-stat .tw-stat-value {
  font-size: 1.3rem;
  font-weight: 800;
  color: #4361ee;
}
#tw-app .tw-stat.net .tw-stat-value {
  color: #2d8a4e;
}
#tw-app .tw-stat.deduct .tw-stat-value {
  color: #c0392b;
}
#tw-app .tw-breakdown table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#tw-app .tw-breakdown th {
  background: #f0f4ff;
  padding: 0.55rem 0.7rem;
  text-align: left;
  font-size: 0.77rem;
  font-weight: 700;
  color: #4361ee;
}
#tw-app .tw-breakdown td {
  padding: 0.55rem 0.7rem;
  border-bottom: 1px solid #f0f0f0;
  color: #333;
}
#tw-app .tw-breakdown tr:last-child td {
  border-bottom: none;
}
#tw-app .tw-breakdown tr.total-row td {
  font-weight: 700;
  background: #fffbeb;
  border-top: 2px solid #f0d060;
}
#tw-app .tw-breakdown tr.net-row td {
  font-weight: 800;
  background: #edfff4;
  color: #2d8a4e;
  border-top: 2px solid #6fcf97;
  font-size: 0.97rem;
}
#tw-app .tw-period-tabs {
  display: flex;
  gap: 0.4rem;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}
#tw-app .tw-period-tab {
  padding: 0.35rem 0.85rem;
  border: 1.5px solid #4361ee;
  border-radius: 20px;
  font-size: 0.82rem;
  font-weight: 700;
  cursor: pointer;
  background: #fff;
  color: #4361ee;
  transition: all 0.15s;
  font-family: inherit;
}
#tw-app .tw-period-tab.active,
#tw-app .tw-period-tab:hover {
  background: #4361ee;
  color: #fff;
}
#tw-app .tw-disclaimer {
  font-size: 0.77rem;
  color: #888;
  background: #fafafa;
  border: 1px solid #eee;
  border-radius: 6px;
  padding: 0.75rem 1rem;
  margin-top: 1rem;
  line-height: 1.6;
}
#tw-app .tw-cta {
  background: #fff8e1;
  border: 1.5px solid #f6c90e;
  border-radius: 8px;
  padding: 1rem 1.2rem;
  margin-top: 1.2rem;
  font-size: 0.9rem;
  line-height: 1.7;
}
#tw-app .tw-cta strong {
  color: #b45309;
}
#tw-app .tw-cta a {
  color: #4361ee;
  font-weight: 700;
  text-decoration: none;
}
#tw-app .tw-cta a:hover {
  text-decoration: underline;
}
@media (max-width: 480px) {
  #tw-app .tw-card { padding: 1rem; }
  #tw-app .tw-stat .tw-stat-value { font-size: 1.1rem; }
  #tw-app .tw-breakdown th,
  #tw-app .tw-breakdown td { font-size: 0.78rem; padding: 0.45rem 0.4rem; }
}
</style>

<div class="tw-intro">
給与から毎月天引きされる<strong>所得税の源泉徴収額・社会保険料・手取り額</strong>を素早くシミュレーションできます。年収・月収を入力するだけで、給与明細の内訳を一覧表示します。
</div>

<div class="tw-card">
  <h2>給与情報を入力</h2>
  <div class="tw-row">
    <div class="tw-field">
      <label for="tw-gross">給与額</label>
      <input type="number" id="tw-gross" placeholder="例: 400000" min="0" step="1" />
    </div>
    <div class="tw-field">
      <label for="tw-period">給与の種類</label>
      <select id="tw-period">
        <option value="annual">年収（年間）</option>
        <option value="monthly" selected>月収（月額）</option>
      </select>
    </div>
  </div>
  <div class="tw-row">
    <div class="tw-field">
      <label for="tw-status">源泉徴収の区分</label>
      <select id="tw-status">
        <option value="kou">甲欄（扶養控除等申告書あり）</option>
        <option value="otsu">乙欄（扶養控除等申告書なし）</option>
      </select>
      <div class="tw-hint">主たる勤務先では甲欄、副業・掛け持ちは乙欄を選択。</div>
    </div>
    <div class="tw-field">
      <label for="tw-dependents">扶養親族等の数（人）</label>
      <input type="number" id="tw-dependents" value="0" min="0" max="10" step="1" />
      <div class="tw-hint">配偶者（控除対象）も含めてカウント。乙欄の場合は0固定。</div>
    </div>
  </div>
  <div class="tw-row">
    <div class="tw-field">
      <label for="tw-age">年齢区分</label>
      <select id="tw-age">
        <option value="general">一般（40歳未満 / 65歳以上）</option>
        <option value="care">介護保険第2号被保険者（40〜64歳）</option>
      </select>
      <div class="tw-hint">40〜64歳は介護保険料が加算されます。</div>
    </div>
    <div class="tw-field">
      <label for="tw-kenpo">健康保険料率（%）</label>
      <select id="tw-kenpo">
        <option value="9.98">協会けんぽ 東京都（9.98%）</option>
        <option value="10.21">協会けんぽ 大阪府（10.21%）</option>
        <option value="10.68">協会けんぽ 北海道（10.68%）</option>
        <option value="9.86">協会けんぽ 愛知県（9.86%）</option>
        <option value="10.16">協会けんぽ 神奈川県（10.16%）</option>
        <option value="custom">その他（手動入力）</option>
      </select>
    </div>
  </div>
  <div class="tw-row" id="tw-custom-kenpo-row" style="display:none;">
    <div class="tw-field">
      <label for="tw-custom-kenpo">健康保険料率 手動入力（%）</label>
      <input type="number" id="tw-custom-kenpo" value="10.0" min="1" max="20" step="0.01" />
    </div>
  </div>
  <button class="tw-btn" onclick="twCalculate()">源泉徴収額を計算する</button>
</div>

<div class="tw-card tw-results" id="tw-results">
  <h2>計算結果 — <span id="tw-result-period-label">月額</span></h2>
  <div class="tw-period-tabs">
    <button class="tw-period-tab active" onclick="twShowPeriod('monthly', this)">月額</button>
    <button class="tw-period-tab" onclick="twShowPeriod('annual', this)">年間</button>
  </div>
  <div class="tw-summary-grid">
    <div class="tw-stat net">
      <div class="tw-stat-label">手取り額</div>
      <div class="tw-stat-value" id="tw-net-pay">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">所得税（源泉徴収）</div>
      <div class="tw-stat-value" id="tw-fed-tax">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">健康保険料（本人）</div>
      <div class="tw-stat-value" id="tw-kenpo-disp">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">介護保険料（本人）</div>
      <div class="tw-stat-value" id="tw-kaigo-disp">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">厚生年金保険料（本人）</div>
      <div class="tw-stat-value" id="tw-nenkin-disp">--</div>
    </div>
    <div class="tw-stat deduct">
      <div class="tw-stat-label">雇用保険料（本人）</div>
      <div class="tw-stat-value" id="tw-koyo-disp">--</div>
    </div>
  </div>

  <div class="tw-breakdown">
    <h2>給与明細シミュレーション</h2>
    <table>
      <thead>
        <tr>
          <th>項目</th>
          <th>月額</th>
          <th>年間</th>
        </tr>
      </thead>
      <tbody id="tw-table-body">
      </tbody>
    </table>
  </div>

  <div class="tw-disclaimer">
    <strong>注意事項：</strong>本ツールは令和7年（2025年）の源泉徴収税額表（月額表）および標準報酬月額表を基にした概算です。実際の源泉徴収額は給与明細の支給項目・非課税通勤費・各種控除等によって異なります。正確な計算は給与ソフトまたは税理士にご確認ください。社会保険料は標準報酬月額テーブルを簡略化した近似値です。
  </div>

  <div class="tw-cta">
    <strong>給与計算を自動化したい方へ</strong><br>
    源泉徴収の計算・年末調整・社会保険手続きをまとめてデジタル化できます。<br>
    給与計算を自動化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee人事労務で源泉徴収を自動計算</a>
  </div>
</div>

<script>
(function() {
  // 2025年版 月額源泉徴収税額表（甲欄）近似実装
  // 課税所得（給与所得控除後・基礎控除後）に対する累進税率を適用
  // 月額表の実態に合わせ、月単位で計算

  var KAIGO_RATE = 0.018 / 2;   // 介護保険料率 1.82%（労使折半）本人分
  var NENKIN_RATE = 0.183 / 2;  // 厚生年金 18.3%（労使折半）本人分
  var KOYO_RATE = 0.006;        // 雇用保険 被保険者負担（一般）0.6%

  // 標準報酬月額テーブル（簡略版：上限は150万円）
  var HYOJUN_TABLE = [
    [63000, 58000], [73000, 68000], [83000, 78000], [93000, 88000],
    [101000, 98000], [107000, 104000], [114000, 110000], [122000, 118000],
    [130000, 126000], [138000, 134000], [146000, 142000], [155000, 150000],
    [165000, 160000], [175000, 170000], [185000, 180000], [195000, 190000],
    [210000, 200000], [230000, 220000], [250000, 240000], [270000, 260000],
    [290000, 280000], [310000, 300000], [330000, 320000], [350000, 340000],
    [370000, 360000], [395000, 380000], [425000, 410000], [455000, 440000],
    [485000, 470000], [515000, 500000], [545000, 530000], [575000, 560000],
    [605000, 590000], [635000, 620000], [665000, 650000], [695000, 680000],
    [730000, 710000], [770000, 750000], [810000, 790000], [855000, 830000],
    [905000, 880000], [955000, 930000], [1005000, 980000], [1055000, 1030000],
    [1115000, 1090000], [1175000, 1150000], [Infinity, 1390000]
  ];

  function getHyojun(monthly) {
    for (var i = 0; i < HYOJUN_TABLE.length; i++) {
      if (monthly < HYOJUN_TABLE[i][0]) return HYOJUN_TABLE[i][1];
    }
    return HYOJUN_TABLE[HYOJUN_TABLE.length - 1][1];
  }

  // 月額源泉徴収（甲欄）簡易計算
  // 給与所得控除・基礎控除を年換算で引いた後、累進税率を月換算
  function calcGensenchoOu(monthlyGross, dependents) {
    var annual = monthlyGross * 12;
    // 給与所得控除（2025年）
    var kyuyoKojo;
    if (annual <= 1625000) kyuyoKojo = 550000;
    else if (annual <= 1800000) kyuyoKojo = annual * 0.4 - 100000;
    else if (annual <= 3600000) kyuyoKojo = annual * 0.3 + 80000;
    else if (annual <= 6600000) kyuyoKojo = annual * 0.2 + 440000;
    else if (annual <= 8500000) kyuyoKojo = annual * 0.1 + 1100000;
    else kyuyoKojo = 1950000;
    // 基礎控除
    var kisoKojo = annual <= 24000000 ? 480000 : annual <= 24500000 ? 320000 : annual <= 25000000 ? 160000 : 0;
    // 扶養控除（1人38万）
    var huyoKojo = dependents * 380000;
    var taxable = Math.max(0, annual - kyuyoKojo - kisoKojo - huyoKojo);
    // 所得税率テーブル
    var tax = 0;
    var brackets = [
      [1950000, 0.05, 0],
      [3300000, 0.10, 97500],
      [6950000, 0.20, 427500],
      [9000000, 0.23, 636000],
      [18000000, 0.33, 1536000],
      [40000000, 0.40, 2796000],
      [Infinity, 0.45, 4796000]
    ];
    for (var i = 0; i < brackets.length; i++) {
      if (taxable <= brackets[i][0]) {
        tax = taxable * brackets[i][1] - brackets[i][2];
        break;
      }
    }
    // 復興特別所得税 2.1%
    tax = tax * 1.021;
    return Math.max(0, Math.round(tax / 12));
  }

  // 乙欄：一律で月額総支給の3.063%（近似）+ 復興特別所得税込み
  function calcGensenchoOtsu(monthlyGross) {
    // 乙欄は最低でも月額3.063%相当（実際は税額表ベース）
    var annual = monthlyGross * 12;
    var taxable = Math.max(0, annual * 0.75); // 給与所得控除なし扱いで近似
    // 簡易に20.42%（乙欄一般税率近似）
    return Math.round(monthlyGross * 0.2042);
  }

  document.getElementById('tw-kenpo').addEventListener('change', function() {
    document.getElementById('tw-custom-kenpo-row').style.display =
      this.value === 'custom' ? 'flex' : 'none';
  });

  var twData = null;
  var twCurrentView = 'monthly';

  function fmt(n) {
    return '¥' + Math.round(n).toLocaleString('ja-JP');
  }

  window.twCalculate = function() {
    var grossInput = parseFloat(document.getElementById('tw-gross').value) || 0;
    var period = document.getElementById('tw-period').value;
    var status = document.getElementById('tw-status').value;
    var dependents = parseInt(document.getElementById('tw-dependents').value) || 0;
    var ageType = document.getElementById('tw-age').value;
    var kenpoEl = document.getElementById('tw-kenpo');
    var kenpoRate = kenpoEl.value === 'custom'
      ? (parseFloat(document.getElementById('tw-custom-kenpo').value) || 10) / 100
      : parseFloat(kenpoEl.value) / 100;
    var kaigoRate = ageType === 'care' ? KAIGO_RATE : 0;

    // 月収に統一
    var monthly = period === 'annual' ? grossInput / 12 : grossInput;

    // 標準報酬月額
    var hyojun = getHyojun(monthly);

    // 社会保険料（本人負担）
    var kenpoMonthly = Math.round(hyojun * kenpoRate / 2);
    var kaigoMonthly = ageType === 'care' ? Math.round(hyojun * kaigoRate) : 0;
    var nenkinMonthly = Math.round(hyojun * NENKIN_RATE);
    var koyoMonthly = Math.round(monthly * KOYO_RATE);
    var socialTotal = kenpoMonthly + kaigoMonthly + nenkinMonthly + koyoMonthly;

    // 所得税源泉徴収
    // 社会保険料控除後の課税対象給与で計算
    var taxableMonthly = Math.max(0, monthly - socialTotal);
    var gensen;
    if (status === 'kou') {
      // 甲欄: 控除後の月額から再計算
      gensen = calcGensenchoOu(taxableMonthly, dependents);
    } else {
      gensen = calcGensenchoOtsu(taxableMonthly);
    }

    var totalDeduction = gensen + socialTotal;
    var netMonthly = monthly - totalDeduction;

    twData = {
      monthly: monthly,
      gensen: gensen,
      kenpo: kenpoMonthly,
      kaigo: kaigoMonthly,
      nenkin: nenkinMonthly,
      koyo: koyoMonthly,
      socialTotal: socialTotal,
      totalDeduction: totalDeduction,
      netMonthly: netMonthly
    };

    twCurrentView = 'monthly';
    document.querySelectorAll('#tw-app .tw-period-tab').forEach(function(t) { t.classList.remove('active'); });
    document.querySelectorAll('#tw-app .tw-period-tab')[0].classList.add('active');

    twRenderResults();

    var resultsEl = document.getElementById('tw-results');
    resultsEl.classList.add('visible');
    resultsEl.scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  window.twShowPeriod = function(view, btn) {
    twCurrentView = view;
    document.querySelectorAll('#tw-app .tw-period-tab').forEach(function(t) { t.classList.remove('active'); });
    btn.classList.add('active');
    twRenderResults();
  };

  function twRenderResults() {
    if (!twData) return;
    var d = twData;
    var mul = twCurrentView === 'annual' ? 12 : 1;
    var label = twCurrentView === 'annual' ? '年間' : '月額';

    document.getElementById('tw-result-period-label').textContent = label;

    document.getElementById('tw-net-pay').textContent = fmt(d.netMonthly * mul);
    document.getElementById('tw-fed-tax').textContent = fmt(d.gensen * mul);
    document.getElementById('tw-kenpo-disp').textContent = fmt(d.kenpo * mul);
    document.getElementById('tw-kaigo-disp').textContent = d.kaigo > 0 ? fmt(d.kaigo * mul) : '—';
    document.getElementById('tw-nenkin-disp').textContent = fmt(d.nenkin * mul);
    document.getElementById('tw-koyo-disp').textContent = fmt(d.koyo * mul);

    var rows = [
      { label: '総支給額（額面）', val: d.monthly, cls: '' },
      { label: '所得税（源泉徴収・復興税込）', val: -d.gensen, cls: 'deduct' },
      { label: '健康保険料（本人負担）', val: -d.kenpo, cls: 'deduct' },
      { label: '介護保険料（本人負担）', val: d.kaigo > 0 ? -d.kaigo : null, cls: 'deduct' },
      { label: '厚生年金保険料（本人負担）', val: -d.nenkin, cls: 'deduct' },
      { label: '雇用保険料（本人負担）', val: -d.koyo, cls: 'deduct' },
    ];

    var tbody = document.getElementById('tw-table-body');
    tbody.innerHTML = '';

    rows.forEach(function(row) {
      if (row.val === null) return;
      var tr = document.createElement('tr');
      var monthly = row.val;
      var annual = monthly * 12;
      tr.innerHTML =
        '<td>' + row.label + '</td>' +
        '<td>' + (monthly < 0 ? '-' : '') + fmt(Math.abs(monthly)) + '</td>' +
        '<td>' + (annual < 0 ? '-' : '') + fmt(Math.abs(annual)) + '</td>';
      tbody.appendChild(tr);
    });

    // 控除合計行
    var trTotal = document.createElement('tr');
    trTotal.className = 'total-row';
    trTotal.innerHTML =
      '<td>控除合計</td>' +
      '<td>-' + fmt(d.totalDeduction) + '</td>' +
      '<td>-' + fmt(d.totalDeduction * 12) + '</td>';
    tbody.appendChild(trTotal);

    // 手取り行
    var trNet = document.createElement('tr');
    trNet.className = 'net-row';
    trNet.innerHTML =
      '<td>手取り額（概算）</td>' +
      '<td>' + fmt(d.netMonthly) + '</td>' +
      '<td>' + fmt(d.netMonthly * 12) + '</td>';
    tbody.appendChild(trNet);
  }
})();
</script>

</div>
