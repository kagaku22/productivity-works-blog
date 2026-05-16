---
title: "時給換算ツール｜年収↔時給を自動変換【月収・日給も】"
date: 2026-05-16
draft: false
slug: "jikyuu-kansan-calculator"
aliases: ["/ja/tools/hourly-to-salary/", "/ja/tools/wage-calculator/"]
description: "年収から時給、時給から年収を自動換算。月収・日給・週給もまとめて表示。残業代シミュレーション、時給アップの年収インパクトも計算できる無料ツール。"
author: "Productivity Works編集部"
categories: ["無料ツール"]
tags: ["時給換算", "年収計算", "給料", "時給", "計算ツール"]
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/jikyuu-kansan-calculator.png"
  alt: "時給換算ツール｜年収↔時給を自動変換"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 時給換算ツール｜年収↔時給を自動変換【月収・日給も】

時給と年収の換算は、就職・転職・副業・フリーランス案件を比較するときに欠かせません。このツールでは「時給 → 年収」「年収 → 時給」の両方向を瞬時に計算。日給・週給・月収もまとめて表示し、残業代シミュレーションや時給アップの年収インパクトも確認できます。

<style>
/* ===== ツール全体 ===== */
#jikyuu-tool {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
  max-width: 720px;
  margin: 2rem auto;
  color: #1f2937;
}

/* モード切替タブ */
.jk-tabs {
  display: flex;
  border-radius: 10px;
  overflow: hidden;
  border: 2px solid #059669;
  margin-bottom: 1.5rem;
}
.jk-tab {
  flex: 1;
  padding: 0.85rem 1rem;
  background: #fff;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 600;
  color: #059669;
  transition: background 0.2s, color 0.2s;
}
.jk-tab.active {
  background: #059669;
  color: #fff;
}
.jk-tab:not(.active):hover {
  background: #d1fae5;
}

/* 入力パネル */
.jk-card {
  background: #f0fdf4;
  border: 1px solid #6ee7b7;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1.25rem;
}
.jk-card h3 {
  margin: 0 0 1rem;
  font-size: 1rem;
  color: #065f46;
  border-left: 4px solid #059669;
  padding-left: 0.6rem;
}

/* ラベル + 数値行 */
.jk-field {
  margin-bottom: 1.1rem;
}
.jk-field label {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  font-size: 0.9rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.35rem;
}
.jk-field label span {
  font-size: 1.05rem;
  color: #059669;
  font-weight: 700;
}

/* 数値入力 */
.jk-number-wrap {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.jk-number-wrap input[type="number"] {
  width: 130px;
  padding: 0.55rem 0.75rem;
  border: 2px solid #6ee7b7;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 700;
  color: #065f46;
  background: #fff;
  outline: none;
  transition: border-color 0.2s;
}
.jk-number-wrap input[type="number"]:focus {
  border-color: #059669;
}
.jk-number-wrap .jk-unit {
  font-size: 0.9rem;
  color: #6b7280;
  font-weight: 600;
}

/* スライダー */
input[type="range"].jk-range {
  -webkit-appearance: none;
  width: 100%;
  height: 6px;
  border-radius: 3px;
  background: #a7f3d0;
  outline: none;
  cursor: pointer;
  margin-top: 0.3rem;
}
input[type="range"].jk-range::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #059669;
  cursor: pointer;
  box-shadow: 0 2px 6px rgba(5,150,105,0.4);
}
input[type="range"].jk-range::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #059669;
  cursor: pointer;
  border: none;
}

/* 結果グリッド */
.jk-results {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.85rem;
  margin-bottom: 1.25rem;
}
@media (max-width: 480px) {
  .jk-results { grid-template-columns: 1fr; }
}
.jk-result-box {
  background: #fff;
  border: 1px solid #a7f3d0;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
.jk-result-box .jk-res-label {
  font-size: 0.8rem;
  color: #6b7280;
  margin-bottom: 0.3rem;
}
.jk-result-box .jk-res-value {
  font-size: 1.5rem;
  font-weight: 800;
  color: #059669;
}
.jk-result-box .jk-res-value.highlight {
  font-size: 1.9rem;
  color: #047857;
}
.jk-result-box .jk-res-sub {
  font-size: 0.75rem;
  color: #9ca3af;
  margin-top: 0.15rem;
}

/* 残業代パネル */
.jk-overtime {
  background: #fff7ed;
  border: 1px solid #fed7aa;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1.25rem;
}
.jk-overtime h3 {
  margin: 0 0 0.85rem;
  font-size: 1rem;
  color: #92400e;
  border-left: 4px solid #f59e0b;
  padding-left: 0.6rem;
}
.jk-overtime-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.7rem;
}
@media (max-width: 480px) {
  .jk-overtime-grid { grid-template-columns: 1fr; }
}
.jk-ot-box {
  background: #fffbeb;
  border: 1px solid #fde68a;
  border-radius: 8px;
  padding: 0.75rem;
  text-align: center;
}
.jk-ot-box .jk-ot-label {
  font-size: 0.75rem;
  color: #78716c;
  margin-bottom: 0.25rem;
}
.jk-ot-box .jk-ot-value {
  font-size: 1.15rem;
  font-weight: 700;
  color: #b45309;
}
.jk-overtime-note {
  font-size: 0.78rem;
  color: #9ca3af;
  margin-top: 0.7rem;
}

/* 時給アップ比較 */
.jk-impact {
  background: #eff6ff;
  border: 1px solid #bfdbfe;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1.25rem;
}
.jk-impact h3 {
  margin: 0 0 0.85rem;
  font-size: 1rem;
  color: #1e40af;
  border-left: 4px solid #3b82f6;
  padding-left: 0.6rem;
}
.jk-impact-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
.jk-impact-table th {
  background: #dbeafe;
  color: #1e3a8a;
  padding: 0.5rem 0.75rem;
  text-align: center;
  font-weight: 700;
}
.jk-impact-table td {
  padding: 0.5rem 0.75rem;
  text-align: center;
  border-bottom: 1px solid #e5e7eb;
}
.jk-impact-table tr:last-child td {
  border-bottom: none;
}
.jk-impact-table .plus {
  color: #059669;
  font-weight: 700;
}
.jk-impact-table tr:hover td {
  background: #f0f9ff;
}

/* クイックリファレンス */
.jk-quickref {
  background: #fafafa;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.25rem;
  margin-bottom: 1.25rem;
}
.jk-quickref h3 {
  margin: 0 0 0.85rem;
  font-size: 1rem;
  color: #374151;
  border-left: 4px solid #9ca3af;
  padding-left: 0.6rem;
}
.jk-quickref table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
.jk-quickref th {
  background: #f3f4f6;
  color: #374151;
  padding: 0.5rem 0.75rem;
  text-align: center;
  font-weight: 700;
}
.jk-quickref td {
  padding: 0.5rem 0.75rem;
  text-align: right;
  border-bottom: 1px solid #f3f4f6;
  color: #374151;
}
.jk-quickref td:first-child {
  text-align: center;
  font-weight: 700;
  color: #059669;
}
.jk-quickref tr:last-child td {
  border-bottom: none;
}
.jk-quickref tr:hover td {
  background: #f9fafb;
}

/* 非表示制御 */
.jk-mode-section { display: none; }
.jk-mode-section.active { display: block; }
</style>

<div id="jikyuu-tool">

  <!-- モード切替タブ -->
  <div class="jk-tabs" role="tablist" aria-label="計算モード">
    <button class="jk-tab active" id="tab-hourly" role="tab" aria-selected="true" onclick="jkSwitchMode('hourly')">⏱ 時給 → 年収</button>
    <button class="jk-tab" id="tab-annual" role="tab" aria-selected="false" onclick="jkSwitchMode('annual')">💴 年収 → 時給</button>
  </div>

  <!-- ===== モード①: 時給 → 年収 ===== -->
  <div class="jk-mode-section active" id="section-hourly">
    <div class="jk-card">
      <h3>入力</h3>

      <div class="jk-field">
        <label>時給<span id="disp-hourly-rate">1,500</span> 円</label>
        <div class="jk-number-wrap">
          <input type="number" id="inp-hourly-rate" value="1500" min="100" max="100000" step="10"
            oninput="jkCalcHourly()" aria-label="時給（円）">
          <span class="jk-unit">円 / 時間</span>
        </div>
      </div>

      <div class="jk-field">
        <label>週の勤務時間<span id="disp-hourly-wh">40</span> 時間</label>
        <input type="range" class="jk-range" id="inp-hourly-wh" min="1" max="60" value="40"
          oninput="jkCalcHourly()" aria-label="週の勤務時間">
      </div>

      <div class="jk-field">
        <label>年間勤務週数<span id="disp-hourly-wk">52</span> 週</label>
        <input type="range" class="jk-range" id="inp-hourly-wk" min="48" max="52" value="52"
          oninput="jkCalcHourly()" aria-label="年間勤務週数">
      </div>
    </div>

    <!-- 結果 -->
    <div class="jk-results" id="results-hourly">
      <div class="jk-result-box">
        <div class="jk-res-label">日給（8時間換算）</div>
        <div class="jk-res-value" id="res-h-daily">—</div>
        <div class="jk-res-sub">円 / 日</div>
      </div>
      <div class="jk-result-box">
        <div class="jk-res-label">週給</div>
        <div class="jk-res-value" id="res-h-weekly">—</div>
        <div class="jk-res-sub">円 / 週</div>
      </div>
      <div class="jk-result-box">
        <div class="jk-res-label">月収（÷12）</div>
        <div class="jk-res-value" id="res-h-monthly">—</div>
        <div class="jk-res-sub">円 / 月</div>
      </div>
      <div class="jk-result-box">
        <div class="jk-res-label">年収</div>
        <div class="jk-res-value highlight" id="res-h-annual">—</div>
        <div class="jk-res-sub">円 / 年</div>
      </div>
    </div>
  </div>

  <!-- ===== モード②: 年収 → 時給 ===== -->
  <div class="jk-mode-section" id="section-annual">
    <div class="jk-card">
      <h3>入力</h3>

      <div class="jk-field">
        <label>年収<span id="disp-annual-val">400</span> 万円</label>
        <div class="jk-number-wrap">
          <input type="number" id="inp-annual-val" value="400" min="50" max="10000" step="10"
            oninput="jkCalcAnnual()" aria-label="年収（万円）">
          <span class="jk-unit">万円 / 年</span>
        </div>
      </div>

      <div class="jk-field">
        <label>週の勤務時間<span id="disp-annual-wh">40</span> 時間</label>
        <input type="range" class="jk-range" id="inp-annual-wh" min="1" max="60" value="40"
          oninput="jkCalcAnnual()" aria-label="週の勤務時間">
      </div>

      <div class="jk-field">
        <label>年間勤務週数<span id="disp-annual-wk">52</span> 週</label>
        <input type="range" class="jk-range" id="inp-annual-wk" min="48" max="52" value="52"
          oninput="jkCalcAnnual()" aria-label="年間勤務週数">
      </div>
    </div>

    <!-- 結果 -->
    <div class="jk-results" id="results-annual">
      <div class="jk-result-box">
        <div class="jk-res-label">時給</div>
        <div class="jk-res-value highlight" id="res-a-hourly">—</div>
        <div class="jk-res-sub">円 / 時間</div>
      </div>
      <div class="jk-result-box">
        <div class="jk-res-label">日給（8時間換算）</div>
        <div class="jk-res-value" id="res-a-daily">—</div>
        <div class="jk-res-sub">円 / 日</div>
      </div>
      <div class="jk-result-box">
        <div class="jk-res-label">週給</div>
        <div class="jk-res-value" id="res-a-weekly">—</div>
        <div class="jk-res-sub">円 / 週</div>
      </div>
      <div class="jk-result-box">
        <div class="jk-res-label">月収（÷12）</div>
        <div class="jk-res-value" id="res-a-monthly">—</div>
        <div class="jk-res-sub">円 / 月</div>
      </div>
    </div>
  </div>

  <!-- ===== 残業代パネル（常時） ===== -->
  <div class="jk-overtime" id="panel-overtime">
    <h3>残業代シミュレーション（法定割増 1.25倍）</h3>
    <div id="overtime-content">
      <div class="jk-overtime-grid">
        <div class="jk-ot-box">
          <div class="jk-ot-label">通常時給</div>
          <div class="jk-ot-value" id="ot-base">—</div>
          <div style="font-size:0.72rem;color:#9ca3af;">円/時</div>
        </div>
        <div class="jk-ot-box">
          <div class="jk-ot-label">残業時給（×1.25）</div>
          <div class="jk-ot-value" id="ot-rate">—</div>
          <div style="font-size:0.72rem;color:#9ca3af;">円/時</div>
        </div>
        <div class="jk-ot-box">
          <div class="jk-ot-label">月20h残業の追加収入</div>
          <div class="jk-ot-value" id="ot-monthly">—</div>
          <div style="font-size:0.72rem;color:#9ca3af;">円/月</div>
        </div>
      </div>
      <p id="overtime-msg" class="jk-overtime-note" style="margin-top:0.6rem;"></p>
    </div>
  </div>

  <!-- ===== 時給アップ比較（常時） ===== -->
  <div class="jk-impact">
    <h3>時給アップの年収インパクト</h3>
    <table class="jk-impact-table" aria-label="時給アップによる年収インパクト">
      <thead>
        <tr>
          <th>時給アップ幅</th>
          <th>アップ後の時給</th>
          <th>年収増加額</th>
          <th>アップ後の年収</th>
        </tr>
      </thead>
      <tbody id="impact-tbody">
        <tr><td colspan="4" style="color:#9ca3af;">計算中...</td></tr>
      </tbody>
    </table>
  </div>

  <!-- ===== クイックリファレンス（常時） ===== -->
  <div class="jk-quickref">
    <h3>クイックリファレンス（週40h・年52週の場合）</h3>
    <table aria-label="主要時給の年収換算表">
      <thead>
        <tr>
          <th>時給</th>
          <th>日給（8h）</th>
          <th>月収</th>
          <th>年収</th>
        </tr>
      </thead>
      <tbody id="quickref-tbody"></tbody>
    </table>
  </div>

</div>

<script>
(function () {
  "use strict";

  /* ===== ユーティリティ ===== */
  function fmt(n) {
    return Math.round(n).toLocaleString("ja-JP") + " 円";
  }
  function fmtNoUnit(n) {
    return Math.round(n).toLocaleString("ja-JP");
  }
  function fmtMan(n) {
    return (n / 10000).toFixed(1) + " 万円";
  }

  /* ===== 現在モード ===== */
  var currentMode = "hourly";

  /* ===== モード切替 ===== */
  window.jkSwitchMode = function (mode) {
    currentMode = mode;
    document.getElementById("tab-hourly").classList.toggle("active", mode === "hourly");
    document.getElementById("tab-annual").classList.toggle("active", mode === "annual");
    document.getElementById("tab-hourly").setAttribute("aria-selected", mode === "hourly");
    document.getElementById("tab-annual").setAttribute("aria-selected", mode === "annual");
    document.getElementById("section-hourly").classList.toggle("active", mode === "hourly");
    document.getElementById("section-annual").classList.toggle("active", mode === "annual");
    if (mode === "hourly") {
      jkCalcHourly();
    } else {
      jkCalcAnnual();
    }
  };

  /* ===== 共通: 残業代・インパクトパネル更新 ===== */
  function updateCommonPanels(hourlyRate, weeklyHours, annualWeeks) {
    /* 残業代 */
    var otRate = hourlyRate * 1.25;
    var otMonthly = otRate * 20; /* 月20h残業 */
    document.getElementById("ot-base").textContent = fmtNoUnit(hourlyRate) + " 円";
    document.getElementById("ot-rate").textContent = fmtNoUnit(Math.round(otRate)) + " 円";
    document.getElementById("ot-monthly").textContent = fmtNoUnit(Math.round(otMonthly)) + " 円";

    if (weeklyHours > 40) {
      var otHours = weeklyHours - 40;
      var otAnnual = otRate * otHours * annualWeeks;
      document.getElementById("overtime-msg").textContent =
        "現在の設定では週" + otHours + "時間が法定時間外です。年間残業代の追加収入は約 " +
        fmtNoUnit(Math.round(otAnnual)) + " 円になります（残業分のみ1.25倍で計算）。";
    } else {
      document.getElementById("overtime-msg").textContent =
        "週の勤務時間が40時間を超えると残業割増（1.25倍）が発生します。スライダーを40hより大きくすると残業分が計算されます。";
    }

    /* 時給アップ比較 */
    var baseAnnual = hourlyRate * weeklyHours * annualWeeks;
    var diffs = [100, 200, 500];
    var rows = diffs.map(function (d) {
      var newRate = hourlyRate + d;
      var newAnnual = newRate * weeklyHours * annualWeeks;
      var diff = newAnnual - baseAnnual;
      return "<tr>" +
        "<td>+" + d.toLocaleString("ja-JP") + " 円</td>" +
        "<td>" + fmtNoUnit(newRate) + " 円</td>" +
        "<td class=\"plus\">+" + fmtNoUnit(diff) + " 円</td>" +
        "<td>" + fmtMan(newAnnual) + "</td>" +
        "</tr>";
    });
    document.getElementById("impact-tbody").innerHTML = rows.join("");
  }

  /* ===== クイックリファレンス（固定: 週40h・年52週） ===== */
  function renderQuickRef() {
    var rates = [1000, 1200, 1500, 2000, 3000, 5000];
    var wh = 40;
    var wk = 52;
    var rows = rates.map(function (r) {
      var daily = r * 8;
      var monthly = r * wh * wk / 12;
      var annual = r * wh * wk;
      return "<tr>" +
        "<td>" + r.toLocaleString("ja-JP") + " 円</td>" +
        "<td>" + fmtNoUnit(daily) + " 円</td>" +
        "<td>" + fmtNoUnit(Math.round(monthly)) + " 円</td>" +
        "<td>" + fmtMan(annual) + "</td>" +
        "</tr>";
    });
    document.getElementById("quickref-tbody").innerHTML = rows.join("");
  }

  /* ===== モード①: 時給 → 年収 ===== */
  window.jkCalcHourly = function () {
    var rate = parseFloat(document.getElementById("inp-hourly-rate").value) || 0;
    var wh = parseInt(document.getElementById("inp-hourly-wh").value, 10);
    var wk = parseInt(document.getElementById("inp-hourly-wk").value, 10);

    /* 表示ラベル更新 */
    document.getElementById("disp-hourly-rate").textContent = rate.toLocaleString("ja-JP");
    document.getElementById("disp-hourly-wh").textContent = wh;
    document.getElementById("disp-hourly-wk").textContent = wk;

    /* 計算 */
    var daily = rate * 8;
    var weekly = rate * wh;
    var annual = rate * wh * wk;
    var monthly = annual / 12;

    /* 結果表示 */
    document.getElementById("res-h-daily").textContent = fmtNoUnit(daily);
    document.getElementById("res-h-weekly").textContent = fmtNoUnit(weekly);
    document.getElementById("res-h-monthly").textContent = fmtNoUnit(Math.round(monthly));
    document.getElementById("res-h-annual").textContent = fmtNoUnit(annual);

    updateCommonPanels(rate, wh, wk);
  };

  /* ===== モード②: 年収 → 時給 ===== */
  window.jkCalcAnnual = function () {
    var annualMan = parseFloat(document.getElementById("inp-annual-val").value) || 0;
    var wh = parseInt(document.getElementById("inp-annual-wh").value, 10);
    var wk = parseInt(document.getElementById("inp-annual-wk").value, 10);

    /* 表示ラベル更新 */
    document.getElementById("disp-annual-val").textContent = annualMan.toLocaleString("ja-JP");
    document.getElementById("disp-annual-wh").textContent = wh;
    document.getElementById("disp-annual-wk").textContent = wk;

    /* 計算 */
    var annual = annualMan * 10000;
    var totalHours = wh * wk;
    var hourly = totalHours > 0 ? annual / totalHours : 0;
    var daily = hourly * 8;
    var weekly = hourly * wh;
    var monthly = annual / 12;

    /* 結果表示 */
    document.getElementById("res-a-hourly").textContent = fmtNoUnit(Math.round(hourly));
    document.getElementById("res-a-daily").textContent = fmtNoUnit(Math.round(daily));
    document.getElementById("res-a-weekly").textContent = fmtNoUnit(Math.round(weekly));
    document.getElementById("res-a-monthly").textContent = fmtNoUnit(Math.round(monthly));

    updateCommonPanels(Math.round(hourly), wh, wk);
  };

  /* ===== 初期化 ===== */
  renderQuickRef();
  jkCalcHourly();
})();
</script>

---

## 時給を上げる方法

**1. スキルアップで市場価値を高める**
資格取得や専門スキルの習得は、転職・交渉の両面で時給アップに直結します。IT・会計・語学などの需要が高いスキルは特に効果的です。

**2. 転職で年収テーブルをリセットする**
同じ仕事内容でも、企業規模や業種によって時給に大きな差があります。転職エージェントに現在の時給・年収を開示した上で上位の求人を紹介してもらうのが最短ルートです。

**3. 副業・フリーランス案件で時給単価を上げる**
本業以外に週数時間だけフリーランス案件を受けると、実質時給が大幅に改善します。クラウドソーシングや直接契約でスタートできます。

**4. 残業ではなく「単価」を上げる意識を持つ**
長時間労働で年収を増やすアプローチは限界があります。同じ時間でより高い単価を得られるポジション・職種へのシフトを意識しましょう。

> **年収アップの転職を相談する** → [doda転職エージェント](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+8P60Z6+47GS+60WN6)

---

## 関連ツール

> 年収から手取りを計算 → [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)

> 所得税・住民税を計算 → [所得税シミュレーター](/ja/tools/shotokuzei-simulator/)

> フリーランスの適正時給を計算 → [フリーランス報酬計算ツール](/ja/tools/freelance-hoshu-calculator/)

> 転職時の年収変化を計算 → [転職年収シミュレーター](/ja/tools/tenshoku-nenshu-simulator/)
