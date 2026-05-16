---
title: "住宅ローン借入可能額シミュレーター - いくらまで借りられる？"
description: "年収・負債・頭金から住宅ローンの借入可能額を計算。無料住宅ローン借入可能額シミュレーター。"
date: 2025-05-16
categories: ["無料ツール"]
slug: "mortgage-affordability-calculator"
ShowToc: false
cover:
  image: "/images/covers/mortgage-affordability-calculator.png"
---

<div id="ma-app">

<style>
#ma-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Meiryo', sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a202c;
  line-height: 1.7;
}
#ma-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1.25rem 0;
  color: #1a202c;
}
#ma-app h3 {
  font-size: 1.05rem;
  font-weight: 600;
  margin: 0 0 1rem 0;
  color: #2d3748;
}
#ma-app .ma-intro {
  background: #f0f7ff;
  border-left: 4px solid #3182ce;
  padding: 1rem 1.25rem;
  border-radius: 0 8px 8px 0;
  margin-bottom: 2rem;
  font-size: 0.93rem;
  color: #2c5282;
}
#ma-app .ma-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.75rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ma-app .ma-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
}
@media (max-width: 600px) {
  #ma-app .ma-grid { grid-template-columns: 1fr; }
}
#ma-app .ma-field {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
#ma-app .ma-field label {
  font-size: 0.83rem;
  font-weight: 700;
  color: #4a5568;
  letter-spacing: 0.02em;
}
#ma-app .ma-field .ma-hint {
  font-size: 0.76rem;
  color: #718096;
  margin-top: -0.2rem;
}
#ma-app .ma-input-wrap {
  position: relative;
  display: flex;
  align-items: center;
}
#ma-app .ma-input-wrap .ma-prefix,
#ma-app .ma-input-wrap .ma-suffix {
  position: absolute;
  color: #718096;
  font-size: 0.9rem;
  font-weight: 500;
  pointer-events: none;
}
#ma-app .ma-input-wrap .ma-prefix { left: 0.75rem; }
#ma-app .ma-input-wrap .ma-suffix { right: 0.75rem; }
#ma-app .ma-input-wrap input,
#ma-app .ma-input-wrap select {
  width: 100%;
  border: 1.5px solid #cbd5e0;
  border-radius: 8px;
  padding: 0.6rem 0.85rem;
  font-size: 1rem;
  background: #fff;
  color: #1a202c;
  outline: none;
  transition: border-color 0.2s;
  box-sizing: border-box;
}
#ma-app .ma-input-wrap input:focus,
#ma-app .ma-input-wrap select:focus {
  border-color: #3182ce;
  box-shadow: 0 0 0 3px rgba(49,130,206,0.15);
}
#ma-app .ma-input-wrap.has-prefix input { padding-left: 2.2rem; }
#ma-app .ma-input-wrap.has-suffix input { padding-right: 2.4rem; }
#ma-app .ma-dti-row {
  display: flex;
  gap: 1rem;
  margin-top: 0.5rem;
}
#ma-app .ma-dti-chip {
  flex: 1;
  background: #ebf8ff;
  border: 1px solid #bee3f8;
  border-radius: 8px;
  padding: 0.7rem 0.9rem;
  text-align: center;
}
#ma-app .ma-dti-chip .ma-dti-label {
  font-size: 0.72rem;
  color: #2b6cb0;
  font-weight: 700;
}
#ma-app .ma-dti-chip .ma-dti-val {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2c5282;
}
#ma-app .ma-dti-chip.warn .ma-dti-val { color: #c05621; }
#ma-app .ma-dti-chip.danger .ma-dti-val { color: #c53030; }
#ma-app .ma-btn {
  display: block;
  width: 100%;
  padding: 0.9rem 1.5rem;
  background: linear-gradient(135deg, #3182ce, #2b6cb0);
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.1s;
  letter-spacing: 0.04em;
}
#ma-app .ma-btn:hover { opacity: 0.92; transform: translateY(-1px); }
#ma-app .ma-btn:active { transform: translateY(0); }
#ma-app .ma-results { display: none; }
#ma-app .ma-results.visible { display: block; }
#ma-app .ma-result-hero {
  background: linear-gradient(135deg, #2b6cb0, #2c5282);
  border-radius: 12px;
  padding: 2rem;
  text-align: center;
  color: #fff;
  margin-bottom: 1.5rem;
}
#ma-app .ma-result-hero .ma-hero-label {
  font-size: 0.83rem;
  letter-spacing: 0.06em;
  opacity: 0.85;
  margin-bottom: 0.4rem;
}
#ma-app .ma-result-hero .ma-hero-price {
  font-size: 2.6rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 0.75rem;
}
#ma-app .ma-result-hero .ma-hero-sub {
  font-size: 0.95rem;
  opacity: 0.9;
}
#ma-app .ma-stats-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-bottom: 1.5rem;
}
@media (max-width: 600px) {
  #ma-app .ma-stats-grid { grid-template-columns: 1fr 1fr; }
}
#ma-app .ma-stat {
  background: #f7fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
#ma-app .ma-stat .ma-stat-label {
  font-size: 0.72rem;
  color: #718096;
  font-weight: 700;
  margin-bottom: 0.3rem;
}
#ma-app .ma-stat .ma-stat-value {
  font-size: 1.2rem;
  font-weight: 700;
  color: #2d3748;
}
#ma-app .ma-stat .ma-stat-value.green { color: #276749; }
#ma-app .ma-stat .ma-stat-value.orange { color: #c05621; }
#ma-app .ma-chart-wrap {
  display: flex;
  gap: 2rem;
  align-items: center;
  flex-wrap: wrap;
}
#ma-app canvas#ma-pie {
  width: 180px !important;
  height: 180px !important;
  flex-shrink: 0;
}
#ma-app .ma-legend {
  flex: 1;
  min-width: 180px;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
#ma-app .ma-legend-item {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  font-size: 0.88rem;
}
#ma-app .ma-legend-dot {
  width: 14px;
  height: 14px;
  border-radius: 3px;
  flex-shrink: 0;
}
#ma-app .ma-legend-name { color: #4a5568; flex: 1; }
#ma-app .ma-legend-amt { font-weight: 700; color: #2d3748; }
#ma-app .ma-alert {
  border-radius: 8px;
  padding: 0.85rem 1.1rem;
  font-size: 0.88rem;
  margin-top: 1rem;
  display: flex;
  align-items: flex-start;
  gap: 0.6rem;
}
#ma-app .ma-alert.success { background: #f0fff4; border: 1px solid #9ae6b4; color: #276749; }
#ma-app .ma-alert.warn { background: #fffbeb; border: 1px solid #fbd38d; color: #744210; }
#ma-app .ma-alert.danger { background: #fff5f5; border: 1px solid #feb2b2; color: #742a2a; }
#ma-app .ma-hensai-box {
  background: #f7fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1.1rem 1.25rem;
  margin-top: 1rem;
  font-size: 0.88rem;
  color: #4a5568;
}
#ma-app .ma-hensai-box strong { color: #2d3748; }
#ma-app .ma-freee-cta {
  background: linear-gradient(135deg, #f0f7ff, #ebf8ff);
  border: 1.5px solid #bee3f8;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-top: 2rem;
  font-size: 0.93rem;
  color: #2c5282;
}
#ma-app .ma-freee-cta a {
  color: #2b6cb0;
  font-weight: 700;
}
#ma-app .ma-disclaimer {
  font-size: 0.76rem;
  color: #a0aec0;
  margin-top: 1.5rem;
  text-align: center;
  line-height: 1.6;
}
</style>

<div class="ma-intro">
  年収・毎月の返済額・頭金などを入力するだけで、住宅ローンで借りられる上限額と毎月の返済シミュレーションを自動計算します。返済負担率（フラット35基準）に基づいた目安を確認できます。
</div>

<div class="ma-card">
  <h2>あなたの財務情報を入力</h2>
  <div class="ma-grid">
    <div class="ma-field">
      <label>年収（税込）</label>
      <span class="ma-hint">給与・事業収入など全収入合計</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-income" value="6000000" min="0" step="100000" />
        <span class="ma-suffix">円</span>
      </div>
    </div>
    <div class="ma-field">
      <label>毎月の返済中の借入</label>
      <span class="ma-hint">カーローン・奨学金・カードリボ等</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-debts" value="30000" min="0" step="5000" />
        <span class="ma-suffix">円/月</span>
      </div>
    </div>
    <div class="ma-field">
      <label>頭金（金額）</label>
      <span class="ma-hint">自己資金として用意できる額</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-downpayment" value="5000000" min="0" step="100000" />
        <span class="ma-suffix">円</span>
      </div>
    </div>
    <div class="ma-field">
      <label>頭金（割合）</label>
      <span class="ma-hint">購入価格に対する割合で指定も可</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-downpct" value="" min="0" max="100" step="0.5" placeholder="例：20" />
        <span class="ma-suffix">%</span>
      </div>
    </div>
    <div class="ma-field">
      <label>年利（固定金利想定）</label>
      <span class="ma-hint">フラット35現行目安 1.8〜2.0%</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-rate" value="1.9" min="0.1" max="15" step="0.05" />
        <span class="ma-suffix">%</span>
      </div>
    </div>
    <div class="ma-field">
      <label>返済期間</label>
      <span class="ma-hint">最長35年まで選択可</span>
      <div class="ma-input-wrap">
        <select id="ma-term">
          <option value="15">15年</option>
          <option value="20">20年</option>
          <option value="25">25年</option>
          <option value="30">30年</option>
          <option value="35" selected>35年</option>
        </select>
      </div>
    </div>
    <div class="ma-field">
      <label>固定資産税率（年）</label>
      <span class="ma-hint">目安：評価額の1.4%前後</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-tax" value="1.4" min="0" max="5" step="0.05" />
        <span class="ma-suffix">%</span>
      </div>
    </div>
    <div class="ma-field">
      <label>火災・地震保険（月額）</label>
      <span class="ma-hint">目安：3,000〜8,000円/月</span>
      <div class="ma-input-wrap has-suffix">
        <input type="number" id="ma-insurance" value="5000" min="0" step="500" />
        <span class="ma-suffix">円/月</span>
      </div>
    </div>
  </div>

  <div style="margin-top:1.25rem;">
    <div style="font-size:0.82rem;font-weight:700;color:#4a5568;margin-bottom:0.5rem;">返済負担率（フラット35基準）</div>
    <div class="ma-dti-row">
      <div class="ma-dti-chip" id="ma-frontend-chip">
        <div class="ma-dti-label">住宅ローン返済負担率</div>
        <div class="ma-dti-val" id="ma-frontend-val">—</div>
        <div style="font-size:0.7rem;color:#4a5568;">上限目安：25〜30%</div>
      </div>
      <div class="ma-dti-chip" id="ma-backend-chip">
        <div class="ma-dti-label">全借入合計 返済負担率</div>
        <div class="ma-dti-val" id="ma-backend-val">—</div>
        <div style="font-size:0.7rem;color:#4a5568;">上限目安：35%</div>
      </div>
    </div>
    <div class="ma-hensai-box">
      <strong>返済負担率とは？</strong><br>
      年収に占める年間返済額の割合です。フラット35では年収400万円未満は30%以内、400万円以上は35%以内が基準。他のローン返済額も合算して審査されます。
    </div>
  </div>

  <button class="ma-btn" style="margin-top:1.5rem;" onclick="maCalculateJP()">
    借入可能額を計算する
  </button>
</div>

<div class="ma-results" id="ma-results">
  <div class="ma-result-hero">
    <div class="ma-hero-label">借入可能な住宅価格の上限（目安）</div>
    <div class="ma-hero-price" id="ma-max-price">0円</div>
    <div class="ma-hero-sub" id="ma-hero-sub">返済負担率基準に基づく試算</div>
  </div>

  <div class="ma-stats-grid">
    <div class="ma-stat">
      <div class="ma-stat-label">毎月の返済額合計</div>
      <div class="ma-stat-value" id="ma-max-payment">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">借入金額（ローン）</div>
      <div class="ma-stat-value" id="ma-loan-amt">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">頭金</div>
      <div class="ma-stat-value green" id="ma-dp-display">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">総支払利息</div>
      <div class="ma-stat-value orange" id="ma-total-interest">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">ローン総支払額</div>
      <div class="ma-stat-value" id="ma-total-cost">—</div>
    </div>
    <div class="ma-stat">
      <div class="ma-stat-label">適用金利</div>
      <div class="ma-stat-value" id="ma-rate-display">—</div>
    </div>
  </div>

  <div class="ma-card">
    <h3>毎月の支払い内訳</h3>
    <div class="ma-chart-wrap">
      <canvas id="ma-pie" width="180" height="180"></canvas>
      <div class="ma-legend" id="ma-legend"></div>
    </div>
    <div id="ma-dti-alert" class="ma-alert" style="display:none;"></div>
  </div>

  <div class="ma-freee-cta">
    住宅ローン管理を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で資産管理を自動化</a>
  </div>
</div>

<p class="ma-disclaimer">
  本シミュレーターは参考目安であり、金融・不動産アドバイスではありません。<br>
  実際の審査結果は金融機関・物件・信用状況により異なります。詳細は金融機関またはFPにご相談ください。
</p>

<script>
(function() {
  var COLORS = ['#3182ce', '#f6ad55', '#68d391', '#fc8181'];

  function fmtJP(n) {
    if (n >= 100000000) {
      var oku = n / 100000000;
      return Math.round(oku * 10) / 10 + '億円';
    } else if (n >= 10000) {
      var man = n / 10000;
      return Math.round(man * 10) / 10 + '万円';
    }
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }
  function fmtFull(n) {
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }
  function fmtMo(n) {
    return Math.round(n).toLocaleString('ja-JP') + '円/月';
  }
  function fmtPct(n) { return n.toFixed(1) + '%'; }

  var dpAmtEl = document.getElementById('ma-downpayment');
  var dpPctEl = document.getElementById('ma-downpct');
  var lastEdited = 'amt';
  dpAmtEl.addEventListener('input', function() { lastEdited = 'amt'; dpPctEl.value = ''; });
  dpPctEl.addEventListener('input', function() { lastEdited = 'pct'; dpAmtEl.value = ''; });

  window.maCalculateJP = function() {
    var income = parseFloat(document.getElementById('ma-income').value) || 0;
    var debts = parseFloat(document.getElementById('ma-debts').value) || 0;
    var rate = parseFloat(document.getElementById('ma-rate').value) / 100 / 12;
    var term = parseInt(document.getElementById('ma-term').value) * 12;
    var taxRate = parseFloat(document.getElementById('ma-tax').value) / 100;
    var insurance = parseFloat(document.getElementById('ma-insurance').value) || 0;

    var monthlyIncome = income / 12;

    // フラット35基準: 年収400万未満30%、以上35%
    var hensaiLimit = income < 4000000 ? 0.30 : 0.35;
    // 住宅ローン分の上限 = 総上限 - 既存借入
    var maxHousingPayment = monthlyIncome * hensaiLimit - debts;
    // フロントエンド上限（住宅のみ）も念のため28%で別途計算
    var maxFrontEnd = monthlyIncome * 0.28;
    maxHousingPayment = Math.min(maxHousingPayment, maxFrontEnd);

    var dpAmt = parseFloat(dpAmtEl.value) || 0;
    var dpPct = parseFloat(dpPctEl.value);
    var usePct = (dpPctEl.value !== '' && lastEdited === 'pct');

    var maxHomePrice;

    if (rate === 0) {
      if (usePct) {
        var ltvFrac = 1 - dpPct / 100;
        maxHomePrice = (maxHousingPayment - insurance) / (ltvFrac / term + taxRate / 12);
      } else {
        maxHomePrice = (maxHousingPayment - insurance + dpAmt / term) / (1 / term + taxRate / 12);
      }
    } else {
      var piFactor = rate * Math.pow(1 + rate, term) / (Math.pow(1 + rate, term) - 1);
      if (usePct) {
        var ltvFrac2 = 1 - dpPct / 100;
        maxHomePrice = (maxHousingPayment - insurance) / (ltvFrac2 * piFactor + taxRate / 12);
        dpAmt = maxHomePrice * dpPct / 100;
      } else {
        maxHomePrice = (maxHousingPayment - insurance + dpAmt * piFactor) / (piFactor + taxRate / 12);
      }
    }

    if (maxHomePrice < 0) maxHomePrice = 0;

    var loanAmt = Math.max(0, maxHomePrice - dpAmt);
    var monthlyPI, totalPaid, totalInterest;

    if (rate === 0) {
      monthlyPI = loanAmt / term;
      totalPaid = loanAmt;
      totalInterest = 0;
    } else {
      monthlyPI = loanAmt * rate * Math.pow(1 + rate, term) / (Math.pow(1 + rate, term) - 1);
      totalPaid = monthlyPI * term;
      totalInterest = totalPaid - loanAmt;
    }

    var monthlyTax = maxHomePrice * taxRate / 12;
    var totalMonthly = monthlyPI + monthlyTax + insurance;

    var frontEndDTI = (totalMonthly / monthlyIncome) * 100;
    var backEndDTI = ((totalMonthly + debts) / monthlyIncome) * 100;
    var annualHensai = (totalMonthly + debts) * 12;
    var hensaiRate = (annualHensai / income) * 100;

    // 表示更新
    document.getElementById('ma-max-price').textContent = fmtJP(maxHomePrice);
    document.getElementById('ma-hero-sub').textContent =
      '頭金 ' + fmtJP(dpAmt) + ' / ' +
      document.getElementById('ma-term').value + '年返済 / 年利' +
      document.getElementById('ma-rate').value + '%';

    document.getElementById('ma-max-payment').textContent = fmtMo(totalMonthly);
    document.getElementById('ma-loan-amt').textContent = fmtJP(loanAmt);
    document.getElementById('ma-dp-display').textContent = fmtJP(dpAmt);
    document.getElementById('ma-total-interest').textContent = fmtJP(totalInterest);
    document.getElementById('ma-total-cost').textContent = fmtJP(totalPaid + dpAmt);
    document.getElementById('ma-rate-display').textContent = document.getElementById('ma-rate').value + '%';

    updateDTIChip('ma-frontend-chip', 'ma-frontend-val', frontEndDTI, 28);
    updateDTIChip('ma-backend-chip', 'ma-backend-val', hensaiRate, hensaiLimit * 100);

    var breakdown = [
      { label: '元利返済（P+I）', value: monthlyPI, color: COLORS[0] },
      { label: '固定資産税（月割）', value: monthlyTax, color: COLORS[1] },
      { label: '火災・地震保険', value: insurance, color: COLORS[2] },
    ];
    drawPie(breakdown, totalMonthly);

    var alertEl = document.getElementById('ma-dti-alert');
    if (maxHomePrice <= 0) {
      alertEl.style.display = 'flex';
      alertEl.className = 'ma-alert danger';
      alertEl.innerHTML = '<strong>&#9888; 既存の借入が多く、住宅ローンの借入余力がありません。</strong>他の借入を返済してから再度シミュレーションしてください。';
    } else if (hensaiRate > hensaiLimit * 100) {
      alertEl.style.display = 'flex';
      alertEl.className = 'ma-alert warn';
      alertEl.innerHTML = '<strong>&#9888; 返済負担率が基準を超えています。</strong>頭金を増やすか、借入期間の見直しをご検討ください。';
    } else {
      alertEl.style.display = 'flex';
      alertEl.className = 'ma-alert success';
      alertEl.innerHTML = '<strong>&#10003; フラット35の返済負担率基準内です。</strong>一般的な審査基準を満たしています（信用審査は別途必要）。';
    }

    document.getElementById('ma-results').classList.add('visible');
    document.getElementById('ma-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  function updateDTIChip(chipId, valId, val, limit) {
    var chip = document.getElementById(chipId);
    var valEl = document.getElementById(valId);
    valEl.textContent = fmtPct(val);
    chip.className = 'ma-dti-chip';
    if (val > limit) chip.classList.add('danger');
    else if (val > limit * 0.9) chip.classList.add('warn');
  }

  function drawPie(data, total) {
    var canvas = document.getElementById('ma-pie');
    var ctx = canvas.getContext('2d');
    var dpr = window.devicePixelRatio || 1;
    canvas.width = 180 * dpr;
    canvas.height = 180 * dpr;
    canvas.style.width = '180px';
    canvas.style.height = '180px';
    ctx.scale(dpr, dpr);

    var cx = 90, cy = 90, r = 80;
    ctx.clearRect(0, 0, 180, 180);

    var start = -Math.PI / 2;
    data.forEach(function(seg) {
      var slice = (seg.value / total) * 2 * Math.PI;
      ctx.beginPath();
      ctx.moveTo(cx, cy);
      ctx.arc(cx, cy, r, start, start + slice);
      ctx.closePath();
      ctx.fillStyle = seg.color;
      ctx.fill();
      start += slice;
    });

    ctx.beginPath();
    ctx.arc(cx, cy, r * 0.52, 0, 2 * Math.PI);
    ctx.fillStyle = '#fff';
    ctx.fill();

    ctx.fillStyle = '#2d3748';
    ctx.font = 'bold 12px sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText('月返済合計', cx, cy - 10);
    ctx.font = 'bold 12px sans-serif';
    ctx.fillStyle = '#2b6cb0';
    ctx.fillText(Math.round(total / 10000) + '万円/月', cx, cy + 10);

    var legendEl = document.getElementById('ma-legend');
    legendEl.innerHTML = '';
    data.forEach(function(seg) {
      var pct = total > 0 ? ((seg.value / total) * 100).toFixed(1) : '0.0';
      legendEl.innerHTML +=
        '<div class="ma-legend-item">' +
        '<div class="ma-legend-dot" style="background:' + seg.color + ';"></div>' +
        '<span class="ma-legend-name">' + seg.label + '<br><span style="font-size:0.73rem;color:#a0aec0;">' + pct + '%</span></span>' +
        '<span class="ma-legend-amt">' + Math.round(seg.value).toLocaleString('ja-JP') + '円</span>' +
        '</div>';
    });
  }

  document.addEventListener('keydown', function(e) {
    if (e.key === 'Enter' && document.activeElement && document.activeElement.closest && document.activeElement.closest('#ma-app')) {
      maCalculateJP();
    }
  });
})();
</script>

</div>

---

## 関連ツール

> 借金返済計算 → [借金返済計算ツール](/ja/tools/debt-payoff-calculator/)
> ローン比較 → [ローン比較ツール](/ja/tools/loan-comparison/)
> 住宅ローン計算 → [住宅ローン計算ツール](/ja/tools/mortgage-calculator/)

