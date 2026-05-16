---
title: "ROI計算ツール｜投資利益率・回収期間をシミュレーション【無料】"
date: 2025-05-16
description: "無料のROI（投資利益率）計算ツール。投資の収益率・年間ROI・損益分岐点をシミュレーション。グラフ付きで分かりやすい、会員登録不要。"
categories: ["無料ツール"]
slug: "roi-calculator"
ShowToc: false
cover:
  image: "/images/covers/roi-calculator-ja.png"
  alt: "ROI計算ツール"
---

投資の収益性を素早く把握したいときに使える、無料のROI（投資利益率）計算ツールです。シンプルな計算から、NPV・IRR・回収期間を含む詳細分析、さらに複数投資の比較まで、グラフ付きで直感的にシミュレーションできます。

<div id="roi-app">

<style>
#roi-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1e293b;
  font-size: 15px;
}

/* Tab Navigation */
#roi-app .tab-nav {
  display: flex;
  gap: 4px;
  border-bottom: 2px solid #cbd5e1;
  margin-bottom: 24px;
  flex-wrap: wrap;
}
#roi-app .tab-btn {
  padding: 10px 18px;
  border: none;
  background: transparent;
  color: #64748b;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  border-radius: 6px 6px 0 0;
  transition: color 0.15s, border-color 0.15s, background 0.15s;
}
#roi-app .tab-btn:hover {
  color: #334155;
  background: #f1f5f9;
}
#roi-app .tab-btn.active {
  color: #0f172a;
  border-bottom-color: #0284c7;
  background: #f8fafc;
}

/* Tab panels */
#roi-app .tab-panel { display: none; }
#roi-app .tab-panel.active { display: block; }

/* Form grid */
#roi-app .form-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
@media (max-width: 560px) {
  #roi-app .form-grid { grid-template-columns: 1fr; }
}

#roi-app .form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
#roi-app .form-group.full { grid-column: 1 / -1; }

#roi-app label {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
}
#roi-app input[type="number"],
#roi-app select {
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  color: #0f172a;
  background: #f8fafc;
  outline: none;
  transition: border-color 0.15s;
  width: 100%;
  box-sizing: border-box;
}
#roi-app input[type="number"]:focus,
#roi-app select:focus {
  border-color: #38bdf8;
  background: #fff;
}

/* Toggle group: "最終価値 / 損益額" */
#roi-app .toggle-group {
  display: flex;
  gap: 0;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  overflow: hidden;
  margin-bottom: 4px;
}
#roi-app .toggle-group button {
  flex: 1;
  padding: 8px;
  border: none;
  background: #f1f5f9;
  color: #64748b;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#roi-app .toggle-group button.active {
  background: #0284c7;
  color: #fff;
}

/* Calc button */
#roi-app .calc-btn {
  display: inline-block;
  margin-top: 20px;
  padding: 11px 32px;
  background: #0284c7;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#roi-app .calc-btn:hover { background: #0369a1; }

/* Dynamic cost rows */
#roi-app .cost-row {
  display: flex;
  gap: 8px;
  align-items: center;
  margin-bottom: 8px;
}
#roi-app .cost-row input { flex: 1; margin-bottom: 0; }
#roi-app .remove-btn {
  padding: 7px 12px;
  background: #fee2e2;
  color: #dc2626;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
}
#roi-app .add-btn {
  padding: 7px 16px;
  background: #e0f2fe;
  color: #0369a1;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  margin-top: 4px;
}

/* Results section */
#roi-app .results-section {
  margin-top: 28px;
  display: none;
}
#roi-app .results-section.visible { display: block; }

#roi-app .result-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 14px;
  margin-bottom: 24px;
}
#roi-app .result-card {
  padding: 16px 14px;
  border-radius: 10px;
  border: 1.5px solid #e2e8f0;
  text-align: center;
}
#roi-app .result-card.positive {
  background: linear-gradient(135deg, #f0fdf4, #dcfce7);
  border-color: #86efac;
}
#roi-app .result-card.negative {
  background: linear-gradient(135deg, #fff1f2, #fee2e2);
  border-color: #fca5a5;
}
#roi-app .result-card.neutral {
  background: linear-gradient(135deg, #f8fafc, #f1f5f9);
  border-color: #cbd5e1;
}
#roi-app .result-card .card-label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  margin-bottom: 6px;
}
#roi-app .result-card .card-value {
  font-size: 22px;
  font-weight: 800;
  color: #0f172a;
  letter-spacing: -0.5px;
}
#roi-app .result-card.positive .card-value { color: #16a34a; }
#roi-app .result-card.negative .card-value { color: #dc2626; }

/* Chart area */
#roi-app .chart-container {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 20px 16px 12px;
  margin-bottom: 20px;
}
#roi-app .chart-title {
  font-size: 13px;
  font-weight: 700;
  color: #475569;
  margin-bottom: 12px;
  text-align: center;
}
#roi-app canvas { display: block; max-width: 100%; }

/* Breakeven timeline */
#roi-app .timeline {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 16px 18px;
  margin-bottom: 20px;
}
#roi-app .timeline-title {
  font-size: 13px;
  font-weight: 700;
  color: #475569;
  margin-bottom: 10px;
}
#roi-app .timeline-bar-wrap {
  position: relative;
  height: 22px;
  background: #e2e8f0;
  border-radius: 999px;
  overflow: hidden;
}
#roi-app .timeline-bar-fill {
  position: absolute;
  left: 0; top: 0; bottom: 0;
  border-radius: 999px;
  transition: width 0.5s;
}
#roi-app .timeline-label {
  font-size: 12px;
  color: #64748b;
  margin-top: 6px;
  text-align: right;
}

/* Compare tab */
#roi-app .compare-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}
#roi-app .compare-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 16px;
}
#roi-app .compare-card h4 {
  margin: 0 0 12px;
  font-size: 14px;
  color: #334155;
  font-weight: 700;
}
#roi-app .compare-result {
  margin-top: 14px;
  padding-top: 12px;
  border-top: 1px solid #e2e8f0;
}
#roi-app .compare-result .cr-row {
  display: flex;
  justify-content: space-between;
  font-size: 13px;
  margin-bottom: 5px;
}
#roi-app .compare-result .cr-label { color: #64748b; }
#roi-app .compare-result .cr-value { font-weight: 700; color: #0f172a; }
#roi-app .compare-result .cr-value.pos { color: #16a34a; }
#roi-app .compare-result .cr-value.neg { color: #dc2626; }

#roi-app .section-divider {
  border: none;
  border-top: 1.5px solid #e2e8f0;
  margin: 24px 0;
}

/* Cross-links */
#roi-app .cross-links {
  margin-top: 24px;
  padding: 14px 18px;
  background: #f1f5f9;
  border-radius: 8px;
  font-size: 13px;
  color: #475569;
  line-height: 2;
}
#roi-app .cross-links a { color: #0284c7; font-weight: 600; text-decoration: none; }
#roi-app .cross-links a:hover { text-decoration: underline; }
</style>

<!-- Tab Navigation -->
<nav class="tab-nav">
  <button class="tab-btn active" onclick="roiShowTab('simple', this)">シンプルROI</button>
  <button class="tab-btn" onclick="roiShowTab('detail', this)">詳細ROI</button>
  <button class="tab-btn" onclick="roiShowTab('compare', this)">投資比較</button>
</nav>

<!-- ========== TAB 1: シンプルROI ========== -->
<div id="roi-tab-simple" class="tab-panel active">
  <div class="form-grid">
    <div class="form-group">
      <label for="s-initial">初期投資額（万円）</label>
      <input type="number" id="s-initial" min="0" step="0.1" placeholder="例: 100" />
    </div>
    <div class="form-group">
      <label>計算モード</label>
      <div class="toggle-group">
        <button id="s-mode-final" class="active" onclick="roiSimpleMode('final')">最終価値で入力</button>
        <button id="s-mode-gain" onclick="roiSimpleMode('gain')">損益額で入力</button>
      </div>
    </div>
    <div class="form-group" id="s-final-group">
      <label for="s-final">最終価値（万円）</label>
      <input type="number" id="s-final" min="0" step="0.1" placeholder="例: 150" />
    </div>
    <div class="form-group" id="s-gain-group" style="display:none;">
      <label for="s-gain">損益額（万円、損失はマイナス）</label>
      <input type="number" id="s-gain" step="0.1" placeholder="例: 50" />
    </div>
    <div class="form-group">
      <label for="s-period">投資期間</label>
      <input type="number" id="s-period" min="1" step="1" placeholder="例: 12" />
    </div>
    <div class="form-group">
      <label for="s-period-unit">期間の単位</label>
      <select id="s-period-unit">
        <option value="month">月</option>
        <option value="year">年</option>
      </select>
    </div>
  </div>
  <button class="calc-btn" onclick="roiCalcSimple()">計算する</button>

  <div id="s-results" class="results-section">
    <hr class="section-divider" />
    <div class="result-cards" id="s-cards"></div>
    <div class="chart-container">
      <div class="chart-title">年別：投資額 vs 累積価値</div>
      <canvas id="s-chart" height="220"></canvas>
    </div>
    <div class="timeline">
      <div class="timeline-title">損益分岐タイムライン</div>
      <div class="timeline-bar-wrap">
        <div class="timeline-bar-fill" id="s-timeline-fill" style="width:0%;background:#22c55e;"></div>
      </div>
      <div class="timeline-label" id="s-timeline-label"></div>
    </div>
  </div>
</div>

<!-- ========== TAB 2: 詳細ROI ========== -->
<div id="roi-tab-detail" class="tab-panel">
  <div class="form-grid">
    <div class="form-group">
      <label for="d-initial">初期投資額（万円）</label>
      <input type="number" id="d-initial" min="0" step="0.1" placeholder="例: 500" />
    </div>
    <div class="form-group">
      <label for="d-revenue">年間収益（万円）</label>
      <input type="number" id="d-revenue" min="0" step="0.1" placeholder="例: 200" />
    </div>
    <div class="form-group full">
      <label>年間コスト（複数行追加可）（万円）</label>
      <div id="d-cost-rows"></div>
      <button class="add-btn" onclick="roiAddCostRow()">＋ コスト行を追加</button>
    </div>
    <div class="form-group">
      <label for="d-years">投資期間（年）</label>
      <input type="number" id="d-years" min="1" max="50" step="1" placeholder="例: 5" />
    </div>
    <div class="form-group">
      <label for="d-discount">割引率（NPV用、%）</label>
      <input type="number" id="d-discount" min="0" max="100" step="0.1" placeholder="例: 5" />
    </div>
  </div>
  <button class="calc-btn" onclick="roiCalcDetail()">計算する</button>

  <div id="d-results" class="results-section">
    <hr class="section-divider" />
    <div class="result-cards" id="d-cards"></div>
    <div class="chart-container">
      <div class="chart-title">年別：投資vs累積収益</div>
      <canvas id="d-chart" height="220"></canvas>
    </div>
    <div class="timeline">
      <div class="timeline-title">損益分岐タイムライン</div>
      <div class="timeline-bar-wrap">
        <div class="timeline-bar-fill" id="d-timeline-fill" style="width:0%;background:#22c55e;"></div>
      </div>
      <div class="timeline-label" id="d-timeline-label"></div>
    </div>
  </div>
</div>

<!-- ========== TAB 3: 投資比較 ========== -->
<div id="roi-tab-compare" class="tab-panel">
  <div class="compare-grid" id="compare-grid">
    <!-- Cards rendered by JS -->
  </div>
  <button class="calc-btn" onclick="roiCalcCompare()">比較する</button>

  <div id="c-results" class="results-section">
    <hr class="section-divider" />
    <div class="chart-container">
      <div class="chart-title">投資比較：ROI%</div>
      <canvas id="c-chart" height="220"></canvas>
    </div>
  </div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の経費・投資管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、事業の収支・経費・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<!-- Cross-links -->
<div class="cross-links">
  複利を計算 → <a href="/ja/tools/compound-interest-calculator/">複利計算ツール</a><br>
  年金をシミュレーション → <a href="/ja/tools/pension-simulator/">年金シミュレーター</a><br>
  家計を見直す → <a href="/ja/tools/budget-planner/">50/30/20 家計バランス計算</a>
</div>

<script>
(function () {
  "use strict";

  /* ── Utility ── */
  function fmt(n, digits) {
    digits = digits === undefined ? 2 : digits;
    return n.toLocaleString("ja-JP", { minimumFractionDigits: digits, maximumFractionDigits: digits });
  }
  function fmtMan(n) { return fmt(n) + " 万円"; }
  function fmtPct(n) { return fmt(n) + "%"; }

  /* ── Tab switching ── */
  window.roiShowTab = function (tab, btn) {
    document.querySelectorAll("#roi-app .tab-panel").forEach(function (p) { p.classList.remove("active"); });
    document.querySelectorAll("#roi-app .tab-btn").forEach(function (b) { b.classList.remove("active"); });
    document.getElementById("roi-tab-" + tab).classList.add("active");
    btn.classList.add("active");
  };

  /* ── Simple mode toggle ── */
  var sMode = "final";
  window.roiSimpleMode = function (mode) {
    sMode = mode;
    document.getElementById("s-final-group").style.display = mode === "final" ? "" : "none";
    document.getElementById("s-gain-group").style.display = mode === "gain" ? "" : "none";
    document.getElementById("s-mode-final").classList.toggle("active", mode === "final");
    document.getElementById("s-mode-gain").classList.toggle("active", mode === "gain");
  };

  /* ── Result card builder ── */
  function makeCard(label, value, tone) {
    return '<div class="result-card ' + (tone || "neutral") + '">' +
      '<div class="card-label">' + label + '</div>' +
      '<div class="card-value">' + value + '</div>' +
      '</div>';
  }

  /* ── Canvas bar chart ── */
  function drawBarChart(canvasId, labels, datasets) {
    var canvas = document.getElementById(canvasId);
    if (!canvas) return;
    var W = canvas.parentElement.clientWidth - 32;
    var H = 220;
    canvas.width = W;
    canvas.height = H;
    var ctx = canvas.getContext("2d");
    ctx.clearRect(0, 0, W, H);

    var padL = 54, padR = 16, padT = 20, padB = 36;
    var chartW = W - padL - padR;
    var chartH = H - padT - padB;

    // find max/min
    var allVals = [];
    datasets.forEach(function (ds) { allVals = allVals.concat(ds.data); });
    var maxV = Math.max.apply(null, allVals.map(function (v) { return Math.abs(v); }));
    if (maxV === 0) maxV = 1;
    var hasNeg = allVals.some(function (v) { return v < 0; });
    var minV = hasNeg ? -maxV : 0;
    var range = maxV - minV;

    // zero line
    var zeroY = padT + chartH * (1 - (0 - minV) / range);

    // grid
    ctx.strokeStyle = "#e2e8f0";
    ctx.lineWidth = 1;
    [0, 0.25, 0.5, 0.75, 1].forEach(function (t) {
      var y = padT + chartH * t;
      ctx.beginPath(); ctx.moveTo(padL, y); ctx.lineTo(padL + chartW, y); ctx.stroke();
      var val = maxV - t * range;
      ctx.fillStyle = "#94a3b8";
      ctx.font = "11px system-ui";
      ctx.textAlign = "right";
      ctx.fillText(fmt(val, 0), padL - 4, y + 4);
    });

    // bars
    var n = labels.length;
    var groupW = chartW / n;
    var barW = Math.max(8, Math.min(32, (groupW / datasets.length) * 0.7));
    var totalBarsW = barW * datasets.length;
    var COLORS = ["#38bdf8", "#34d399", "#f472b6"];

    datasets.forEach(function (ds, di) {
      ctx.fillStyle = COLORS[di % COLORS.length];
      ds.data.forEach(function (v, i) {
        var gx = padL + i * groupW + (groupW - totalBarsW) / 2 + di * barW;
        var barH = Math.abs(v) / range * chartH;
        var by = v >= 0 ? zeroY - barH : zeroY;
        ctx.fillRect(gx, by, barW - 2, barH);
      });
    });

    // zero axis
    ctx.strokeStyle = "#64748b";
    ctx.lineWidth = 1.5;
    ctx.beginPath(); ctx.moveTo(padL, zeroY); ctx.lineTo(padL + chartW, zeroY); ctx.stroke();

    // x labels
    ctx.fillStyle = "#64748b";
    ctx.font = "11px system-ui";
    ctx.textAlign = "center";
    labels.forEach(function (l, i) {
      var gx = padL + i * groupW + groupW / 2;
      ctx.fillText(l, gx, H - padB + 16);
    });

    // legend
    var lx = padL;
    datasets.forEach(function (ds, di) {
      ctx.fillStyle = COLORS[di % COLORS.length];
      ctx.fillRect(lx, 4, 12, 10);
      ctx.fillStyle = "#475569";
      ctx.font = "11px system-ui";
      ctx.textAlign = "left";
      ctx.fillText(ds.label, lx + 14, 13);
      lx += ctx.measureText(ds.label).width + 30;
    });
  }

  /* ── Breakeven timeline ── */
  function setTimeline(fillId, labelId, beYear, totalYears) {
    var fill = document.getElementById(fillId);
    var lbl = document.getElementById(labelId);
    if (beYear === null || beYear > totalYears) {
      fill.style.width = "100%";
      fill.style.background = "#f87171";
      lbl.textContent = "投資期間内に損益分岐点に到達しません";
    } else if (beYear <= 0) {
      fill.style.width = "5%";
      fill.style.background = "#22c55e";
      lbl.textContent = "即座に黒字（損益分岐点: 投資直前）";
    } else {
      var pct = Math.min(100, (beYear / totalYears) * 100);
      fill.style.width = pct.toFixed(1) + "%";
      fill.style.background = pct < 70 ? "#22c55e" : "#f59e0b";
      lbl.textContent = "損益分岐点: " + fmt(beYear, 2) + " 年後（期間の " + fmt(pct, 1) + "% 地点）";
    }
  }

  /* ─────────────────────────────────────────
     TAB 1: シンプルROI
  ───────────────────────────────────────── */
  window.roiCalcSimple = function () {
    var initial = parseFloat(document.getElementById("s-initial").value);
    var period = parseFloat(document.getElementById("s-period").value);
    var unit = document.getElementById("s-period-unit").value;
    var years = unit === "year" ? period : period / 12;

    var gain, finalVal;
    if (sMode === "final") {
      finalVal = parseFloat(document.getElementById("s-final").value);
      gain = finalVal - initial;
    } else {
      gain = parseFloat(document.getElementById("s-gain").value);
      finalVal = initial + gain;
    }

    if (isNaN(initial) || initial <= 0 || isNaN(finalVal) || isNaN(years) || years <= 0) {
      alert("入力値を確認してください。"); return;
    }

    var roi = (gain / initial) * 100;
    var annualRoi = (Math.pow(finalVal / initial, 1 / years) - 1) * 100;
    var tone = gain >= 0 ? "positive" : "negative";

    // Cards
    var cards = document.getElementById("s-cards");
    cards.innerHTML =
      makeCard("ROI", fmtPct(roi), tone) +
      makeCard("年間ROI", fmtPct(annualRoi), tone) +
      makeCard("純利益", fmtMan(gain), tone) +
      makeCard("初期投資額", fmtMan(initial), "neutral") +
      makeCard("最終価値", fmtMan(finalVal), "neutral") +
      makeCard("投資期間", fmt(years, 2) + " 年", "neutral");

    // Chart: yearly investment vs value
    var chartLabels = [];
    var invData = [], valData = [];
    var totalYearsInt = Math.ceil(years);
    for (var y = 0; y <= totalYearsInt; y++) {
      chartLabels.push(y + "年");
      invData.push(initial);
      var v = initial * Math.pow(1 + annualRoi / 100, y);
      valData.push(parseFloat(v.toFixed(2)));
    }
    drawBarChart("s-chart", chartLabels, [
      { label: "投資額", data: invData },
      { label: "累積価値", data: valData }
    ]);

    // Breakeven: when cumulative value >= initial
    // For simple, if gain >= 0 breakeven is at start; if negative never
    var beYear = gain >= 0 ? 0 : null;
    setTimeline("s-timeline-fill", "s-timeline-label", beYear, years);

    document.getElementById("s-results").classList.add("visible");
  };

  /* ─────────────────────────────────────────
     TAB 2: 詳細ROI
  ───────────────────────────────────────── */
  // Add initial cost row
  function roiAddCostRow(defaultVal) {
    var row = document.createElement("div");
    row.className = "cost-row";
    row.innerHTML =
      '<input type="number" min="0" step="0.1" placeholder="例: 30" class="d-cost-input" />' +
      '<button class="remove-btn" onclick="this.parentElement.remove()">削除</button>';
    if (defaultVal !== undefined) {
      row.querySelector("input").value = defaultVal;
    }
    document.getElementById("d-cost-rows").appendChild(row);
  }
  window.roiAddCostRow = roiAddCostRow;

  // Init with one row
  roiAddCostRow();

  /* Newton-Raphson IRR */
  function calcIRR(cashflows) {
    var r = 0.1;
    for (var iter = 0; iter < 100; iter++) {
      var npv = 0, dnpv = 0;
      cashflows.forEach(function (cf, t) {
        npv += cf / Math.pow(1 + r, t);
        dnpv += -t * cf / Math.pow(1 + r, t + 1);
      });
      if (Math.abs(dnpv) < 1e-12) break;
      var rn = r - npv / dnpv;
      if (Math.abs(rn - r) < 1e-8) { r = rn; break; }
      r = rn;
      if (r < -0.9999) r = -0.9999;
    }
    return isFinite(r) ? r : null;
  }

  window.roiCalcDetail = function () {
    var initial = parseFloat(document.getElementById("d-initial").value);
    var revenue = parseFloat(document.getElementById("d-revenue").value);
    var years = parseInt(document.getElementById("d-years").value);
    var discount = parseFloat(document.getElementById("d-discount").value) / 100 || 0;

    var costs = 0;
    document.querySelectorAll(".d-cost-input").forEach(function (inp) {
      var v = parseFloat(inp.value);
      if (!isNaN(v)) costs += v;
    });

    if (isNaN(initial) || initial <= 0 || isNaN(revenue) || isNaN(years) || years <= 0) {
      alert("入力値を確認してください。"); return;
    }

    var annualNet = revenue - costs;
    var totalNet = annualNet * years;
    var roi = (totalNet / initial) * 100;

    // NPV
    var cashflows = [-initial];
    for (var y = 1; y <= years; y++) cashflows.push(annualNet);
    var npv = cashflows.reduce(function (acc, cf, t) {
      return acc + cf / Math.pow(1 + discount, t);
    }, 0);

    // IRR
    var irrVal = calcIRR(cashflows);
    var irrStr = irrVal !== null ? fmtPct(irrVal * 100) : "計算不可";

    // Payback period
    var payback = annualNet > 0 ? initial / annualNet : null;

    var tone = totalNet >= 0 ? "positive" : "negative";

    // Cards
    var cards = document.getElementById("d-cards");
    cards.innerHTML =
      makeCard("ROI", fmtPct(roi), tone) +
      makeCard("NPV", fmtMan(npv), npv >= 0 ? "positive" : "negative") +
      makeCard("IRR", irrStr, irrVal !== null && irrVal > 0 ? "positive" : "neutral") +
      makeCard("回収期間", payback !== null ? fmt(payback, 2) + " 年" : "回収不可", payback !== null && payback <= years ? "positive" : "negative") +
      makeCard("年間純利益", fmtMan(annualNet), annualNet >= 0 ? "positive" : "negative") +
      makeCard("累計純利益", fmtMan(totalNet), tone);

    // Chart
    var chartLabels = ["0年"];
    var invData = [initial];
    var cumData = [0];
    for (var yi = 1; yi <= years; yi++) {
      chartLabels.push(yi + "年");
      invData.push(initial);
      cumData.push(annualNet * yi);
    }
    drawBarChart("d-chart", chartLabels, [
      { label: "初期投資", data: invData },
      { label: "累計純利益", data: cumData }
    ]);

    // Breakeven
    setTimeline("d-timeline-fill", "d-timeline-label", payback, years);

    document.getElementById("d-results").classList.add("visible");
  };

  /* ─────────────────────────────────────────
     TAB 3: 投資比較
  ───────────────────────────────────────── */
  var compareCount = 3;

  function buildCompareGrid() {
    var grid = document.getElementById("compare-grid");
    grid.innerHTML = "";
    var names = ["投資案A", "投資案B", "投資案C"];
    for (var i = 0; i < compareCount; i++) {
      var card = document.createElement("div");
      card.className = "compare-card";
      card.innerHTML = '<h4>' + names[i] + '</h4>' +
        '<div class="form-group"><label>初期投資額（万円）</label>' +
        '<input type="number" class="c-initial" min="0" step="0.1" placeholder="例: 100" /></div>' +
        '<div class="form-group" style="margin-top:10px;"><label>年間収益（万円）</label>' +
        '<input type="number" class="c-revenue" min="0" step="0.1" placeholder="例: 30" /></div>' +
        '<div class="form-group" style="margin-top:10px;"><label>年間コスト（万円）</label>' +
        '<input type="number" class="c-cost" min="0" step="0.1" placeholder="例: 10" /></div>' +
        '<div class="form-group" style="margin-top:10px;"><label>投資期間（年）</label>' +
        '<input type="number" class="c-years" min="1" step="1" placeholder="例: 5" /></div>' +
        '<div class="compare-result" id="cr-' + i + '" style="display:none;"></div>';
      grid.appendChild(card);
    }
  }
  buildCompareGrid();

  window.roiCalcCompare = function () {
    var initials = document.querySelectorAll(".c-initial");
    var revenues = document.querySelectorAll(".c-revenue");
    var costs = document.querySelectorAll(".c-cost");
    var yearsList = document.querySelectorAll(".c-years");

    var rois = [];
    var labels = ["投資案A", "投資案B", "投資案C"].slice(0, compareCount);

    for (var i = 0; i < compareCount; i++) {
      var init = parseFloat(initials[i].value);
      var rev = parseFloat(revenues[i].value);
      var cost = parseFloat(costs[i].value) || 0;
      var yrs = parseFloat(yearsList[i].value);

      if (isNaN(init) || init <= 0 || isNaN(rev) || isNaN(yrs) || yrs <= 0) {
        rois.push(null); continue;
      }
      var net = (rev - cost) * yrs;
      var roi = (net / init) * 100;
      rois.push(roi);

      var payback = (rev - cost) > 0 ? init / (rev - cost) : null;
      var cr = document.getElementById("cr-" + i);
      cr.style.display = "";
      cr.innerHTML =
        '<div class="cr-row"><span class="cr-label">ROI</span><span class="cr-value ' + (roi >= 0 ? "pos" : "neg") + '">' + fmtPct(roi) + '</span></div>' +
        '<div class="cr-row"><span class="cr-label">累計純利益</span><span class="cr-value ' + (net >= 0 ? "pos" : "neg") + '">' + fmtMan(net) + '</span></div>' +
        '<div class="cr-row"><span class="cr-label">回収期間</span><span class="cr-value">' + (payback !== null ? fmt(payback, 2) + " 年" : "回収不可") + '</span></div>';
    }

    // Draw compare bar chart
    var validLabels = [], validData = [];
    labels.forEach(function (l, i) {
      if (rois[i] !== null) { validLabels.push(l); validData.push(rois[i]); }
    });
    drawBarChart("c-chart", validLabels, [{ label: "ROI (%)", data: validData }]);

    document.getElementById("c-results").classList.add("visible");
  };

  // Resize charts on window resize
  var resizeTimer;
  window.addEventListener("resize", function () {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(function () {
      // Redraw will happen on next calc; nothing to do passively
    }, 200);
  });

})();
</script>

</div>

> 複利を計算 → [複利計算ツール](/ja/tools/compound-interest-calculator/)
> 年金をシミュレーション → [年金シミュレーター](/ja/tools/pension-simulator/)
> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-planner/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [AI副業で稼ぐ方法2026年最新完全ガイド](/ja/posts/ai-副業-稼ぐ-方法-2026/)
- [会社員が不動産投資を始めるならRENOSY？｜NISAやiDeCoとの使い分けガイド](/ja/posts/kaishain-fudousan-toushi-renosy/)
- [RENOSYの利回りは本当？｜評判・口コミを徹底検証【2026年版データ分析】](/ja/posts/renosy-rimawari-hyoban-kensho-2026/)
