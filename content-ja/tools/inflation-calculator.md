---
title: "インフレ計算ツール｜物価上昇で将来お金の価値はどう変わる？【無料】"
date: 2026-05-16
draft: false
slug: "inflation-calculator"
aliases: ["/ja/tools/inflation-calculator/"]
description: "インフレ率を入力するだけで、将来のお金の実質価値を自動計算。100万円が10年後・20年後にいくらの価値になるか、購買力の低下を見える化する無料ツール。"
author: "Productivity Works編集部"
categories: ["無料ツール"]
tags: ["インフレ", "物価上昇", "購買力", "計算ツール", "資産防衛"]
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/inflation-calculator.png"
  alt: "インフレ計算ツール｜物価上昇で将来お金の価値はどう変わる？"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# インフレ計算ツール｜物価上昇で将来お金の価値はどう変わる？

日本でも2022年以降、物価の上昇が続いています。年2〜3%のインフレが続くと、今持っている100万円は20年後にいくらの価値になるでしょうか？このツールでは、インフレ率と期間を指定するだけで、将来のお金の実質購買力を即座に計算できます。資産防衛の第一歩として、まずは現実を数字で把握しましょう。

<div id="inflation-calc-app" style="font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Yu Gothic', sans-serif; max-width: 720px; margin: 2rem auto; color: #1c1917;">

  <!-- 入力パネル -->
  <div style="background: #fffbeb; border: 2px solid #d97706; border-radius: 16px; padding: 1.75rem 2rem; margin-bottom: 1.5rem;">
    <h2 style="margin: 0 0 1.5rem; font-size: 1.1rem; font-weight: 700; color: #92400e; letter-spacing: 0.02em;">条件を入力してください</h2>

    <!-- 現在の金額 -->
    <div style="margin-bottom: 1.4rem;">
      <label style="display: block; font-size: 0.9rem; font-weight: 600; color: #44403c; margin-bottom: 0.5rem;">現在の金額</label>
      <div style="display: flex; align-items: center; gap: 0.75rem;">
        <input
          id="ic-amount"
          type="number"
          value="100"
          min="1"
          max="100000"
          step="1"
          style="width: 130px; padding: 0.55rem 0.75rem; border: 1.5px solid #d97706; border-radius: 8px; font-size: 1.1rem; font-weight: 700; color: #1c1917; background: #fff; text-align: right;"
          oninput="icCalc()"
        />
        <span style="font-size: 1rem; color: #57534e; font-weight: 600;">万円</span>
      </div>
    </div>

    <!-- インフレ率スライダー -->
    <div style="margin-bottom: 1.4rem;">
      <label style="display: flex; justify-content: space-between; font-size: 0.9rem; font-weight: 600; color: #44403c; margin-bottom: 0.5rem;">
        <span>年間インフレ率</span>
        <span id="ic-rate-label" style="color: #d97706; font-size: 1rem; font-weight: 700;">2.5%</span>
      </label>
      <input
        id="ic-rate"
        type="range"
        min="0.5"
        max="8"
        step="0.5"
        value="2.5"
        style="width: 100%; accent-color: #d97706; cursor: pointer;"
        oninput="icUpdateRateLabel(); icCalc()"
      />
      <div style="display: flex; justify-content: space-between; font-size: 0.75rem; color: #78716c; margin-top: 0.25rem;">
        <span>0.5%</span>
        <span style="color: #d97706; font-size: 0.72rem;">日本の直近インフレ率: 2〜3%</span>
        <span>8.0%</span>
      </div>
    </div>

    <!-- 期間スライダー -->
    <div>
      <label style="display: flex; justify-content: space-between; font-size: 0.9rem; font-weight: 600; color: #44403c; margin-bottom: 0.5rem;">
        <span>計算期間</span>
        <span id="ic-years-label" style="color: #d97706; font-size: 1rem; font-weight: 700;">20年後</span>
      </label>
      <input
        id="ic-years"
        type="range"
        min="1"
        max="40"
        step="1"
        value="20"
        style="width: 100%; accent-color: #d97706; cursor: pointer;"
        oninput="icUpdateYearsLabel(); icCalc()"
      />
      <div style="display: flex; justify-content: space-between; font-size: 0.75rem; color: #78716c; margin-top: 0.25rem;">
        <span>1年</span>
        <span>40年</span>
      </div>
    </div>
  </div>

  <!-- 結果パネル -->
  <div style="background: #fff; border: 2px solid #e7e5e4; border-radius: 16px; padding: 1.75rem 2rem; margin-bottom: 1.5rem;">
    <h2 style="margin: 0 0 1.25rem; font-size: 1.05rem; font-weight: 700; color: #44403c;">計算結果</h2>

    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-bottom: 1.25rem;">

      <!-- 将来の実質価値 -->
      <div style="background: #fffbeb; border-radius: 12px; padding: 1.1rem 1.25rem; border: 1.5px solid #fcd34d; text-align: center;">
        <div style="font-size: 0.8rem; color: #92400e; font-weight: 600; margin-bottom: 0.4rem;">将来の実質価値</div>
        <div id="ic-result-value" style="font-size: 1.85rem; font-weight: 800; color: #d97706; line-height: 1.1;">—</div>
        <div style="font-size: 0.78rem; color: #78716c; margin-top: 0.2rem;">（今の価値に換算）</div>
      </div>

      <!-- 購買力の低下率 -->
      <div style="background: #fef2f2; border-radius: 12px; padding: 1.1rem 1.25rem; border: 1.5px solid #fca5a5; text-align: center;">
        <div style="font-size: 0.8rem; color: #991b1b; font-weight: 600; margin-bottom: 0.4rem;">購買力の低下率</div>
        <div id="ic-result-loss" style="font-size: 1.85rem; font-weight: 800; color: #dc2626; line-height: 1.1;">—</div>
        <div style="font-size: 0.78rem; color: #78716c; margin-top: 0.2rem;">（実質価値の目減り）</div>
      </div>
    </div>

    <!-- 現在の価値を維持するために必要な金額 -->
    <div style="background: #f0fdf4; border-radius: 12px; padding: 1rem 1.25rem; border: 1.5px solid #86efac; display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 0.5rem;">
      <div style="font-size: 0.85rem; color: #14532d; font-weight: 600;">現在の価値を維持するために将来必要な金額</div>
      <div id="ic-result-needed" style="font-size: 1.4rem; font-weight: 800; color: #16a34a;">—</div>
    </div>
  </div>

  <!-- 視覚的バー比較 -->
  <div style="background: #fff; border: 2px solid #e7e5e4; border-radius: 16px; padding: 1.75rem 2rem; margin-bottom: 1.5rem;">
    <h2 style="margin: 0 0 1.1rem; font-size: 1.05rem; font-weight: 700; color: #44403c;">購買力の比較</h2>

    <div style="margin-bottom: 0.85rem;">
      <div style="display: flex; justify-content: space-between; font-size: 0.82rem; color: #57534e; margin-bottom: 0.3rem;">
        <span>今の購買力</span>
        <span id="ic-bar-now-label" style="font-weight: 700; color: #d97706;">100%</span>
      </div>
      <div style="background: #e7e5e4; border-radius: 99px; height: 22px; overflow: hidden;">
        <div id="ic-bar-now" style="height: 100%; width: 100%; background: linear-gradient(90deg, #d97706, #f59e0b); border-radius: 99px; transition: width 0.4s ease;"></div>
      </div>
    </div>

    <div>
      <div style="display: flex; justify-content: space-between; font-size: 0.82rem; color: #57534e; margin-bottom: 0.3rem;">
        <span id="ic-bar-future-title">将来の購買力（20年後）</span>
        <span id="ic-bar-future-label" style="font-weight: 700; color: #dc2626;">—</span>
      </div>
      <div style="background: #e7e5e4; border-radius: 99px; height: 22px; overflow: hidden;">
        <div id="ic-bar-future" style="height: 100%; width: 0%; background: linear-gradient(90deg, #dc2626, #f87171); border-radius: 99px; transition: width 0.4s ease;"></div>
      </div>
    </div>
  </div>

  <!-- 年次テーブル -->
  <div style="background: #fff; border: 2px solid #e7e5e4; border-radius: 16px; padding: 1.75rem 2rem; margin-bottom: 1.5rem;">
    <h2 style="margin: 0 0 1.1rem; font-size: 1.05rem; font-weight: 700; color: #44403c;">年次推移テーブル</h2>
    <div style="overflow-x: auto;">
      <table id="ic-table" style="width: 100%; border-collapse: collapse; font-size: 0.88rem;">
        <thead>
          <tr style="background: #fef3c7; border-bottom: 2px solid #d97706;">
            <th style="padding: 0.6rem 0.75rem; text-align: center; color: #92400e; font-weight: 700; white-space: nowrap;">経過年数</th>
            <th style="padding: 0.6rem 0.75rem; text-align: right; color: #92400e; font-weight: 700; white-space: nowrap;">実質価値（万円）</th>
            <th style="padding: 0.6rem 0.75rem; text-align: right; color: #92400e; font-weight: 700; white-space: nowrap;">購買力</th>
            <th style="padding: 0.6rem 0.75rem; text-align: right; color: #92400e; font-weight: 700; white-space: nowrap;">目減り額（万円）</th>
          </tr>
        </thead>
        <tbody id="ic-table-body"></tbody>
      </table>
    </div>
    <div style="text-align: center; margin-top: 1rem;">
      <button
        id="ic-expand-btn"
        onclick="icToggleTable()"
        style="background: #d97706; color: #fff; border: none; border-radius: 8px; padding: 0.5rem 1.5rem; font-size: 0.85rem; font-weight: 700; cursor: pointer; transition: background 0.2s;"
        onmouseover="this.style.background='#b45309'"
        onmouseout="this.style.background='#d97706'"
      >全年次を表示する</button>
    </div>
  </div>

  <!-- インフレに勝つには？パネル -->
  <div style="background: #fffbeb; border: 2px solid #d97706; border-radius: 16px; padding: 1.75rem 2rem; margin-bottom: 1.5rem;">
    <h2 style="margin: 0 0 0.75rem; font-size: 1.05rem; font-weight: 700; color: #92400e;">インフレに勝つには？ — 必要な運用利回り</h2>
    <p style="margin: 0 0 1rem; font-size: 0.88rem; color: #57534e; line-height: 1.6;">資産の実質価値を維持するには、少なくともインフレ率と同等の運用利回りが必要です。購買力を増やすにはさらに高いリターンが求められます。</p>
    <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.75rem;">
      <div style="background: #fff; border-radius: 10px; padding: 0.9rem; text-align: center; border: 1.5px solid #fcd34d;">
        <div style="font-size: 0.75rem; color: #92400e; font-weight: 600; margin-bottom: 0.3rem;">価値を維持</div>
        <div id="ic-beat-maintain" style="font-size: 1.3rem; font-weight: 800; color: #d97706;">—</div>
        <div style="font-size: 0.72rem; color: #78716c;">以上の利回りが必要</div>
      </div>
      <div style="background: #fff; border-radius: 10px; padding: 0.9rem; text-align: center; border: 1.5px solid #6ee7b7;">
        <div style="font-size: 0.75rem; color: #065f46; font-weight: 600; margin-bottom: 0.3rem;">+10%増やす</div>
        <div id="ic-beat-plus10" style="font-size: 1.3rem; font-weight: 800; color: #059669;">—</div>
        <div style="font-size: 0.72rem; color: #78716c;">以上の利回りが必要</div>
      </div>
      <div style="background: #fff; border-radius: 10px; padding: 0.9rem; text-align: center; border: 1.5px solid #a5b4fc;">
        <div style="font-size: 0.75rem; color: #3730a3; font-weight: 600; margin-bottom: 0.3rem;">+30%増やす</div>
        <div id="ic-beat-plus30" style="font-size: 1.3rem; font-weight: 800; color: #4f46e5;">—</div>
        <div style="font-size: 0.72rem; color: #78716c;">以上の利回りが必要</div>
      </div>
    </div>
  </div>

  <!-- 身近な例パネル -->
  <div style="background: #fff; border: 2px solid #e7e5e4; border-radius: 16px; padding: 1.75rem 2rem; margin-bottom: 1.5rem;">
    <h2 style="margin: 0 0 1rem; font-size: 1.05rem; font-weight: 700; color: #44403c;">身近な例：100万円分の買い物が将来いくらに？</h2>
    <p style="margin: 0 0 1rem; font-size: 0.85rem; color: #57534e;">現在100万円で買えるものが、インフレが続くと将来は以下の金額が必要になります。</p>
    <div style="display: grid; grid-template-columns: 1fr; gap: 0.75rem;">

      <div style="display: flex; align-items: center; justify-content: space-between; padding: 0.9rem 1rem; background: #fafaf9; border-radius: 10px; border: 1px solid #e7e5e4; flex-wrap: wrap; gap: 0.5rem;">
        <div>
          <div style="font-size: 0.85rem; font-weight: 700; color: #1c1917;">食費・日用品（年間100万円）</div>
          <div style="font-size: 0.78rem; color: #78716c; margin-top: 0.15rem;">同じ生活水準を維持するためのコスト</div>
        </div>
        <div style="text-align: right;">
          <div style="font-size: 0.75rem; color: #78716c;">将来必要な金額</div>
          <div id="ic-ex-food" style="font-size: 1.15rem; font-weight: 800; color: #dc2626;">—</div>
        </div>
      </div>

      <div style="display: flex; align-items: center; justify-content: space-between; padding: 0.9rem 1rem; background: #fafaf9; border-radius: 10px; border: 1px solid #e7e5e4; flex-wrap: wrap; gap: 0.5rem;">
        <div>
          <div style="font-size: 0.85rem; font-weight: 700; color: #1c1917;">家賃（月8.4万円 × 年間100万円相当）</div>
          <div style="font-size: 0.78rem; color: #78716c; margin-top: 0.15rem;">都市部の賃貸マンション想定</div>
        </div>
        <div style="text-align: right;">
          <div style="font-size: 0.75rem; color: #78716c;">将来必要な金額</div>
          <div id="ic-ex-rent" style="font-size: 1.15rem; font-weight: 800; color: #dc2626;">—</div>
        </div>
      </div>

      <div style="display: flex; align-items: center; justify-content: space-between; padding: 0.9rem 1rem; background: #fafaf9; border-radius: 10px; border: 1px solid #e7e5e4; flex-wrap: wrap; gap: 0.5rem;">
        <div>
          <div style="font-size: 0.85rem; font-weight: 700; color: #1c1917;">教育費（子ども1人・年間100万円）</div>
          <div style="font-size: 0.78rem; color: #78716c; margin-top: 0.15rem;">学費・習い事・進学費用など</div>
        </div>
        <div style="text-align: right;">
          <div style="font-size: 0.75rem; color: #78716c;">将来必要な金額</div>
          <div id="ic-ex-edu" style="font-size: 1.15rem; font-weight: 800; color: #dc2626;">—</div>
        </div>
      </div>

    </div>
  </div>

</div>

<script>
(function() {
  var icTableExpanded = false;

  function fmt(val, decimals) {
    decimals = decimals === undefined ? 2 : decimals;
    return val.toFixed(decimals).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
  }

  function fmtMan(val) {
    // Format as 万円, rounding to 1 decimal
    return fmt(val, 1) + '万円';
  }

  window.icUpdateRateLabel = function() {
    var r = parseFloat(document.getElementById('ic-rate').value);
    document.getElementById('ic-rate-label').textContent = r.toFixed(1) + '%';
  };

  window.icUpdateYearsLabel = function() {
    var y = parseInt(document.getElementById('ic-years').value);
    document.getElementById('ic-years-label').textContent = y + '年後';
  };

  window.icCalc = function() {
    var amount = parseFloat(document.getElementById('ic-amount').value) || 100;
    var rate = parseFloat(document.getElementById('ic-rate').value) / 100;
    var years = parseInt(document.getElementById('ic-years').value);

    if (amount <= 0 || isNaN(amount)) amount = 100;

    // Future real value (purchasing power in today's terms)
    var factor = Math.pow(1 + rate, years);
    var realValue = amount / factor;
    var lossRate = (1 - realValue / amount) * 100;
    var neededFuture = amount * factor;

    // Update main results
    document.getElementById('ic-result-value').textContent = fmtMan(realValue);
    document.getElementById('ic-result-loss').textContent = fmt(lossRate, 1) + '%';
    document.getElementById('ic-result-needed').textContent = fmtMan(neededFuture);

    // Update bar
    var futurePct = (realValue / amount) * 100;
    document.getElementById('ic-bar-future-title').textContent = '将来の購買力（' + years + '年後）';
    document.getElementById('ic-bar-future-label').textContent = fmt(futurePct, 1) + '%';
    document.getElementById('ic-bar-future').style.width = Math.max(futurePct, 2).toFixed(1) + '%';

    // Beat inflation panel
    var rateDisplay = (rate * 100).toFixed(1) + '%';
    document.getElementById('ic-beat-maintain').textContent = rateDisplay;

    // Required return to grow 10% and 30% in real terms
    // (1+r_nominal)^years = (1+rate)^years * 1.10
    // r_nominal = (1+rate) * 10th-root(1.10) - 1... actually:
    // target real growth factor = 1.10, nominal = (1+rate)*(1+real_return)
    // but we just show nominal return needed: (targetFuture)^(1/years) - 1
    // where targetFuture = (1+rate)^years * multiplier
    var neededNominal10 = Math.pow(factor * 1.10, 1 / years) - 1;
    var neededNominal30 = Math.pow(factor * 1.30, 1 / years) - 1;
    document.getElementById('ic-beat-plus10').textContent = (neededNominal10 * 100).toFixed(1) + '%';
    document.getElementById('ic-beat-plus30').textContent = (neededNominal30 * 100).toFixed(1) + '%';

    // Everyday examples (all based on 100万円 baseline)
    var baseline = 100; // 万円
    var exFuture = baseline * factor;
    document.getElementById('ic-ex-food').textContent = fmtMan(exFuture);
    document.getElementById('ic-ex-rent').textContent = fmtMan(exFuture);
    document.getElementById('ic-ex-edu').textContent = fmtMan(exFuture);

    // Build table
    icBuildTable(amount, rate, years);
  };

  function icBuildTable(amount, rate, years) {
    var tbody = document.getElementById('ic-table-body');
    tbody.innerHTML = '';

    // Determine rows: always show key years, up to 10 if collapsed
    var allRows = [];
    for (var y = 1; y <= years; y++) {
      allRows.push(y);
    }

    var showRows = icTableExpanded ? allRows : allRows.slice(0, 10);

    for (var i = 0; i < showRows.length; i++) {
      var yr = showRows[i];
      var f = Math.pow(1 + rate, yr);
      var rv = amount / f;
      var pwr = (rv / amount) * 100;
      var loss = amount - rv;

      var tr = document.createElement('tr');
      tr.style.borderBottom = '1px solid #e7e5e4';
      tr.style.background = yr % 2 === 0 ? '#fafaf9' : '#fff';

      var milestone = (yr === 10 || yr === 20 || yr === 30) ? ' ★' : '';
      tr.innerHTML =
        '<td style="padding:0.5rem 0.75rem; text-align:center; font-weight:' + (milestone ? '700' : '400') + '; color:#44403c;">' + yr + '年後' + milestone + '</td>' +
        '<td style="padding:0.5rem 0.75rem; text-align:right; color:#d97706; font-weight:600;">' + fmt(rv, 1) + '</td>' +
        '<td style="padding:0.5rem 0.75rem; text-align:right; color:' + (pwr >= 80 ? '#16a34a' : pwr >= 60 ? '#d97706' : '#dc2626') + '; font-weight:700;">' + fmt(pwr, 1) + '%</td>' +
        '<td style="padding:0.5rem 0.75rem; text-align:right; color:#dc2626; font-weight:600;">&minus;' + fmt(loss, 1) + '</td>';
      tbody.appendChild(tr);
    }

    // Update expand button
    var btn = document.getElementById('ic-expand-btn');
    if (years <= 10) {
      btn.style.display = 'none';
    } else {
      btn.style.display = 'inline-block';
      btn.textContent = icTableExpanded ? '折りたたむ' : '全' + years + '年次を表示する';
    }
  }

  window.icToggleTable = function() {
    icTableExpanded = !icTableExpanded;
    var amount = parseFloat(document.getElementById('ic-amount').value) || 100;
    var rate = parseFloat(document.getElementById('ic-rate').value) / 100;
    var years = parseInt(document.getElementById('ic-years').value);
    icBuildTable(amount, rate, years);
  };

  // Initial render
  document.addEventListener('DOMContentLoaded', function() {
    icUpdateRateLabel();
    icUpdateYearsLabel();
    icCalc();
  });
  // Also run immediately in case DOM is already loaded
  if (document.readyState !== 'loading') {
    icUpdateRateLabel();
    icUpdateYearsLabel();
    icCalc();
  }
})();
</script>

## インフレから資産を守る方法

物価上昇が続く時代に、現金だけで資産を持ち続けることは実質的な目減りを意味します。以下の4つの対策が有効です。

**1. NISAでの積立投資**
新NISAの「つみたて投資枠」を活用し、インデックスファンドへ長期・分散投資することで、年平均3〜7%程度のリターンを狙えます。歴史的にインフレを上回るリターンが期待できる最も手軽な方法です。

**2. iDeCoで税制優遇を活用**
個人型確定拠出年金（iDeCo）は掛金が全額所得控除され、運用益も非課税です。老後資金の形成とインフレ対策を同時に行えます。

**3. 実物資産への分散**
不動産や金（ゴールド）などの実物資産は、インフレ時に価値が上昇しやすい傾向があります。ETFやREITを通じて少額から分散投資することも可能です。

**4. 変動金利型ローンに注意**
インフレ局面では政策金利が上昇しやすく、変動金利ローンの返済額が増える可能性があります。住宅ローンを変動金利で借りている方は特に注意が必要です。

---

> 収支を把握してインフレに備える → [freee会計で家計管理を始める](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

---

## 関連ツール

> 複利の効果を計算 → [複利計算シミュレーター](/ja/tools/fukuri-keisan/)

> NISAの運用シミュレーション → [NISAシミュレーター](/ja/tools/nisa-simulator/)

> FIRE達成年数を計算 → [FIREシミュレーター](/ja/tools/fire-simulator/)

> 純資産を把握する → [資産管理シミュレーター](/ja/tools/shisan-simulator/)
