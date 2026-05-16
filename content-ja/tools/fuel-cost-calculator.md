---
title: "ガソリン代計算ツール"
date: 2025-05-16
description: "無料のガソリン代計算ツール。距離・燃費・ガソリン価格から費用を計算。往復・年間コスト・車両比較対応。通勤費の計算に最適。"
categories: ["無料ツール"]
slug: "fuel-cost-calculator"
ShowToc: false
cover:
  image: "/images/covers/fuel-cost-calculator-ja.png"
  alt: "ガソリン代計算ツール"
---

<div id="fc-app">
<style>
#fc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1e293b;
}
#fc-app * { box-sizing: border-box; }

#fc-app h2 {
  font-size: 1.15rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 1rem 0;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e2e8f0;
}
#fc-app h3 {
  font-size: 0.9rem;
  font-weight: 700;
  color: #334155;
  margin: 0 0 0.6rem 0;
}

/* Tabs */
#fc-app .fc-tabs {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}
#fc-app .fc-tab {
  padding: 0.5rem 1.1rem;
  border-radius: 6px;
  border: 1.5px solid #cbd5e1;
  background: #f8fafc;
  color: #475569;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 600;
  transition: all 0.15s ease;
}
#fc-app .fc-tab:hover { border-color: #059669; color: #059669; }
#fc-app .fc-tab.active { background: #059669; border-color: #059669; color: #fff; }

/* Panels */
#fc-app .fc-panel { display: none; }
#fc-app .fc-panel.active { display: block; }

/* Card */
#fc-app .fc-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 1.25rem;
  margin-bottom: 1rem;
}

/* Grid */
#fc-app .fc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(190px, 1fr));
  gap: 0.85rem;
  margin-bottom: 1rem;
}
#fc-app .fc-field { display: flex; flex-direction: column; gap: 0.3rem; }
#fc-app .fc-field label {
  font-size: 0.72rem;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#fc-app .fc-field input,
#fc-app .fc-field select {
  padding: 0.55rem 0.75rem;
  background: #fff;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  color: #1e293b;
  font-size: 0.9rem;
  outline: none;
  width: 100%;
  transition: border-color 0.15s;
}
#fc-app .fc-field input:focus,
#fc-app .fc-field select:focus { border-color: #059669; }

/* Toggle row */
#fc-app .fc-toggles {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-bottom: 1rem;
  align-items: center;
}
#fc-app .fc-toggle-label {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  cursor: pointer;
  color: #334155;
  font-size: 0.875rem;
  user-select: none;
}
#fc-app .fc-toggle-label input[type="checkbox"] {
  width: 1rem;
  height: 1rem;
  accent-color: #059669;
  cursor: pointer;
}

/* Button */
#fc-app .fc-btn {
  padding: 0.6rem 1.4rem;
  border: none;
  border-radius: 7px;
  background: #059669;
  color: #fff;
  font-size: 0.9rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#fc-app .fc-btn:hover { background: #047857; }

/* Results bar */
#fc-app .fc-result-bar {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
  gap: 0.75rem;
  background: #ecfdf5;
  border: 1px solid #a7f3d0;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1rem;
}
#fc-app .fc-result-item { text-align: center; }
#fc-app .fc-result-val {
  font-size: 1.5rem;
  font-weight: 800;
  color: #059669;
  line-height: 1.2;
}
#fc-app .fc-result-lbl {
  font-size: 0.7rem;
  color: #64748b;
  margin-top: 0.2rem;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}

/* Compare grid */
#fc-app .fc-compare-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1rem;
}
@media (max-width: 540px) {
  #fc-app .fc-compare-grid { grid-template-columns: 1fr; }
}
#fc-app .fc-vehicle-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  padding: 1rem;
}
#fc-app .fc-vehicle-card h3 {
  font-size: 0.85rem;
  color: #059669;
  margin: 0 0 0.75rem 0;
}
#fc-app .fc-vehicle-card .fc-field { margin-bottom: 0.6rem; }

/* Compare table */
#fc-app .fc-cmp-table { width: 100%; border-collapse: collapse; font-size: 0.875rem; }
#fc-app .fc-cmp-table th {
  background: #f1f5f9;
  color: #64748b;
  padding: 0.5rem 0.75rem;
  text-align: left;
  font-weight: 700;
  font-size: 0.72rem;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}
#fc-app .fc-cmp-table td {
  padding: 0.5rem 0.75rem;
  border-bottom: 1px solid #e2e8f0;
  color: #1e293b;
}
#fc-app .fc-cmp-table tr:last-child td { border-bottom: none; }
#fc-app .fc-cmp-table .winner { color: #059669; font-weight: 700; }
#fc-app .fc-cmp-table .loser  { color: #94a3b8; }

/* Annual stats */
#fc-app .fc-annual-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 0.75rem;
  margin-bottom: 1rem;
}
#fc-app .fc-annual-stat {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 0.85rem 1rem;
  text-align: center;
}
#fc-app .fc-annual-stat .val { font-size: 1.25rem; font-weight: 800; color: #059669; }
#fc-app .fc-annual-stat .lbl { font-size: 0.7rem; color: #64748b; margin-top: 0.2rem; }

/* Chart */
#fc-app .fc-chart-wrap { position: relative; width: 100%; margin-top: 1rem; }
#fc-app canvas { display: block; width: 100%; border-radius: 6px; }

/* Tip */
#fc-app .fc-tip {
  background: #f0fdf4;
  border-left: 3px solid #059669;
  border-radius: 0 6px 6px 0;
  padding: 0.65rem 1rem;
  font-size: 0.8rem;
  color: #166534;
  margin-top: 0.75rem;
}

/* Cross-links */
#fc-app .fc-crosslinks {
  margin-top: 1.5rem;
  padding: 1rem 1.25rem;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
#fc-app .fc-crosslinks a { color: #0284c7; text-decoration: none; }
#fc-app .fc-crosslinks a:hover { text-decoration: underline; }
#fc-app .fc-crosslinks span { color: #94a3b8; margin-right: 0.4rem; }
#fc-app .fc-crosslinks div { font-size: 0.875rem; color: #475569; }
</style>

<!-- TABS -->
<div class="fc-tabs">
  <button class="fc-tab active" onclick="fcSwitchTab('trip')">移動費計算</button>
  <button class="fc-tab" onclick="fcSwitchTab('compare')">車両比較</button>
  <button class="fc-tab" onclick="fcSwitchTab('annual')">年間コスト試算</button>
</div>

<!-- ==============================
     PANEL: TRIP
     ============================== -->
<div id="fc-panel-trip" class="fc-panel active">
  <div class="fc-card">
    <h2>ガソリン代計算</h2>

    <div class="fc-toggles">
      <label class="fc-toggle-label">
        <input type="checkbox" id="fc-roundtrip" onchange="fcCalcTrip()"> 往復で計算する
      </label>
    </div>

    <div class="fc-grid">
      <div class="fc-field">
        <label>走行距離 (km)</label>
        <input type="number" id="fc-distance" value="100" min="0" step="1" oninput="fcCalcTrip()">
      </div>
      <div class="fc-field">
        <label>燃費の表示方法</label>
        <select id="fc-eff-mode" onchange="fcCalcTrip()">
          <option value="kml">km/L（日本標準）</option>
          <option value="l100km">L/100km</option>
          <option value="mpg">MPG（米国）</option>
        </select>
      </div>
      <div class="fc-field">
        <label id="fc-eff-val-lbl">燃費の値 (km/L)</label>
        <input type="number" id="fc-efficiency" value="15" min="0.1" step="0.1" oninput="fcCalcTrip()">
      </div>
      <div class="fc-field">
        <label>ガソリン価格 (円/L)</label>
        <input type="number" id="fc-price" value="170" min="1" step="1" oninput="fcCalcTrip()">
      </div>
    </div>

    <button class="fc-btn" onclick="fcCalcTrip()">計算する</button>

    <div class="fc-result-bar" id="fc-trip-results">
      <div class="fc-result-item">
        <div class="fc-result-val" id="fc-r-fuel">—</div>
        <div class="fc-result-lbl">必要燃料</div>
      </div>
      <div class="fc-result-item">
        <div class="fc-result-val" id="fc-r-cost">—</div>
        <div class="fc-result-lbl">合計費用</div>
      </div>
      <div class="fc-result-item">
        <div class="fc-result-val" id="fc-r-dist">—</div>
        <div class="fc-result-lbl">走行距離</div>
      </div>
      <div class="fc-result-item">
        <div class="fc-result-val" id="fc-r-perkm">—</div>
        <div class="fc-result-lbl">1kmあたり費用</div>
      </div>
    </div>

    <div class="fc-tip" id="fc-trip-tip"></div>
  </div>
</div>

<!-- ==============================
     PANEL: COMPARE
     ============================== -->
<div id="fc-panel-compare" class="fc-panel">
  <div class="fc-card">
    <h2>2台の車を比較する</h2>

    <div class="fc-grid" style="margin-bottom:1rem;">
      <div class="fc-field">
        <label>走行距離 (km)</label>
        <input type="number" id="fc-cmp-dist" value="200" min="1" step="1" oninput="fcCalcCompare()">
      </div>
      <div class="fc-field">
        <label>ガソリン価格 (円/L)</label>
        <input type="number" id="fc-cmp-price" value="170" min="1" step="1" oninput="fcCalcCompare()">
      </div>
    </div>

    <div class="fc-compare-grid">
      <div class="fc-vehicle-card">
        <h3>車両 A</h3>
        <div class="fc-field">
          <label>車名</label>
          <input type="text" id="fc-va-name" value="現在の車" oninput="fcCalcCompare()">
        </div>
        <div class="fc-field">
          <label>燃費の表示方法</label>
          <select id="fc-va-mode" onchange="fcCalcCompare()">
            <option value="kml">km/L</option>
            <option value="l100km">L/100km</option>
            <option value="mpg">MPG</option>
          </select>
        </div>
        <div class="fc-field">
          <label>燃費の値</label>
          <input type="number" id="fc-va-eff" value="12" min="0.1" step="0.1" oninput="fcCalcCompare()">
        </div>
      </div>

      <div class="fc-vehicle-card">
        <h3>車両 B</h3>
        <div class="fc-field">
          <label>車名</label>
          <input type="text" id="fc-vb-name" value="新しい車" oninput="fcCalcCompare()">
        </div>
        <div class="fc-field">
          <label>燃費の表示方法</label>
          <select id="fc-vb-mode" onchange="fcCalcCompare()">
            <option value="kml">km/L</option>
            <option value="l100km">L/100km</option>
            <option value="mpg">MPG</option>
          </select>
        </div>
        <div class="fc-field">
          <label>燃費の値</label>
          <input type="number" id="fc-vb-eff" value="20" min="0.1" step="0.1" oninput="fcCalcCompare()">
        </div>
      </div>
    </div>

    <table class="fc-cmp-table">
      <thead>
        <tr>
          <th>項目</th>
          <th id="fc-cmp-th-a">車両 A</th>
          <th id="fc-cmp-th-b">車両 B</th>
        </tr>
      </thead>
      <tbody id="fc-cmp-tbody"></tbody>
    </table>

    <div class="fc-chart-wrap">
      <canvas id="fc-cmp-chart" height="240"></canvas>
    </div>
  </div>
</div>

<!-- ==============================
     PANEL: ANNUAL
     ============================== -->
<div id="fc-panel-annual" class="fc-panel">
  <div class="fc-card">
    <h2>年間ガソリン代試算</h2>

    <div class="fc-grid">
      <div class="fc-field">
        <label>片道通勤距離 (km)</label>
        <input type="number" id="fc-ann-commute" value="20" min="0" step="1" oninput="fcCalcAnnual()">
      </div>
      <div class="fc-field">
        <label>週の出勤日数</label>
        <input type="number" id="fc-ann-workdays" value="5" min="1" max="7" step="1" oninput="fcCalcAnnual()">
      </div>
      <div class="fc-field">
        <label>燃費の表示方法</label>
        <select id="fc-ann-mode" onchange="fcCalcAnnual()">
          <option value="kml">km/L</option>
          <option value="l100km">L/100km</option>
          <option value="mpg">MPG</option>
        </select>
      </div>
      <div class="fc-field">
        <label>燃費の値</label>
        <input type="number" id="fc-ann-eff" value="15" min="0.1" step="0.1" oninput="fcCalcAnnual()">
      </div>
      <div class="fc-field">
        <label>ガソリン価格 (円/L)</label>
        <input type="number" id="fc-ann-price" value="170" min="1" step="1" oninput="fcCalcAnnual()">
      </div>
      <div class="fc-field">
        <label>週の追加走行 (km)</label>
        <input type="number" id="fc-ann-extra" value="50" min="0" step="10" oninput="fcCalcAnnual()">
      </div>
    </div>

    <div class="fc-annual-grid">
      <div class="fc-annual-stat"><div class="val" id="fc-an-weekly">—</div><div class="lbl">週あたり</div></div>
      <div class="fc-annual-stat"><div class="val" id="fc-an-monthly">—</div><div class="lbl">月あたり</div></div>
      <div class="fc-annual-stat"><div class="val" id="fc-an-yearly">—</div><div class="lbl">年間合計</div></div>
      <div class="fc-annual-stat"><div class="val" id="fc-an-liters">—</div><div class="lbl">年間給油量</div></div>
      <div class="fc-annual-stat"><div class="val" id="fc-an-km">—</div><div class="lbl">年間走行距離</div></div>
      <div class="fc-annual-stat"><div class="val" id="fc-an-perday">—</div><div class="lbl">1日あたり</div></div>
    </div>

    <div class="fc-chart-wrap">
      <canvas id="fc-ann-chart" height="240"></canvas>
    </div>
  </div>
</div>

<!-- Cross-links -->
<div class="fc-crosslinks">
  <div><span>&#8594;</span>毎月の家計を管理する → <a href="/ja/tools/electricity-calculator/">電気代計算ツール</a></div>
  <div><span>&#8594;</span>収支を一元管理する → <a href="/ja/tools/budget-planner/">家計簿・予算管理ツール</a></div>
</div>

</div><!-- /#fc-app -->

<script>
(function () {
  'use strict';

  function num(id) {
    var v = parseFloat(document.getElementById(id).value);
    return isNaN(v) ? 0 : v;
  }
  function val(id) { return document.getElementById(id).value; }
  function set(id, t) { document.getElementById(id).textContent = t; }
  function fmtYen(n) { return Math.round(n).toLocaleString('ja-JP') + '円'; }
  function fmtL(n)   { return n.toFixed(1) + ' L'; }

  /* 燃費をL/100kmに統一 */
  function toLper100km(mode, v) {
    if (v <= 0) return 0;
    if (mode === 'l100km') return v;
    if (mode === 'kml')    return 100 / v;
    if (mode === 'mpg')    return 235.214 / v;
    return v;
  }

  function fuelLiters(distKm, lPer100) {
    if (lPer100 <= 0) return 0;
    return distKm * lPer100 / 100;
  }

  /* ── タブ切り替え ── */
  window.fcSwitchTab = function (name) {
    document.querySelectorAll('#fc-app .fc-tab').forEach(function (b) { b.classList.remove('active'); });
    document.querySelectorAll('#fc-app .fc-panel').forEach(function (p) { p.classList.remove('active'); });
    var btn = document.querySelector('#fc-app .fc-tab[onclick*="' + name + '"]');
    if (btn) btn.classList.add('active');
    var panel = document.getElementById('fc-panel-' + name);
    if (panel) panel.classList.add('active');
    if (name === 'compare') fcCalcCompare();
    if (name === 'annual')  fcCalcAnnual();
  };

  /* ── 移動費計算 ── */
  window.fcCalcTrip = function () {
    var roundtrip = document.getElementById('fc-roundtrip').checked;
    var mode      = val('fc-eff-mode');
    var modeLabel = { kml: 'km/L', l100km: 'L/100km', mpg: 'MPG' };
    document.getElementById('fc-eff-val-lbl').textContent = '燃費の値 (' + modeLabel[mode] + ')';

    var rawDist = num('fc-distance');
    var effVal  = num('fc-efficiency');
    var price   = num('fc-price');
    var distKm  = roundtrip ? rawDist * 2 : rawDist;

    var lPer100 = toLper100km(mode, effVal);
    var liters  = fuelLiters(distKm, lPer100);
    var cost    = liters * price;
    var dispDist = rawDist * (roundtrip ? 2 : 1);

    set('fc-r-fuel', fmtL(liters));
    set('fc-r-cost', fmtYen(cost));
    set('fc-r-dist', dispDist.toFixed(0) + ' km');
    set('fc-r-perkm', dispDist > 0 ? fmtYen(cost / dispDist) : '—');

    var tip = '';
    if (mode === 'kml' && effVal > 0) {
      if (effVal < 10) tip = '燃費10km/L未満の車は、タイヤ空気圧のチェックやアイドリングストップを心がけると改善効果があります。';
      else if (effVal >= 20) tip = '燃費20km/L以上は優秀です。定期的なエンジンオイル交換で性能を維持しましょう。';
      else tip = 'ヒント：急加速・急ブレーキを避けるエコドライブで燃費を10〜15%向上させることができます。';
    } else {
      tip = 'ヒント：エアコンの使用を控えたり、高速道路での速度を抑えると燃料消費を節約できます。';
    }
    document.getElementById('fc-trip-tip').textContent = tip;
  };

  /* ── 車両比較 ── */
  window.fcCalcCompare = function () {
    var dist  = num('fc-cmp-dist');
    var price = num('fc-cmp-price');
    var aName = document.getElementById('fc-va-name').value || '車両A';
    var bName = document.getElementById('fc-vb-name').value || '車両B';

    var aMode = val('fc-va-mode');
    var bMode = val('fc-vb-mode');
    var aEff  = num('fc-va-eff');
    var bEff  = num('fc-vb-eff');

    var aL100 = toLper100km(aMode, aEff);
    var bL100 = toLper100km(bMode, bEff);

    var aFuel = fuelLiters(dist, aL100);
    var bFuel = fuelLiters(dist, bL100);
    var aCost = aFuel * price;
    var bCost = bFuel * price;
    var aAnn  = aCost * 365;
    var bAnn  = bCost * 365;
    var saving = Math.abs(aAnn - bAnn);
    var winner = aCost <= bCost ? 'a' : 'b';

    set('fc-cmp-th-a', aName);
    set('fc-cmp-th-b', bName);

    var rows = [
      ['L/100km換算', aL100.toFixed(2) + ' L', bL100.toFixed(2) + ' L', aL100 <= bL100 ? 'a' : 'b'],
      [dist + 'km分の燃料', fmtL(aFuel), fmtL(bFuel), aFuel <= bFuel ? 'a' : 'b'],
      ['この距離のガソリン代', fmtYen(aCost), fmtYen(bCost), winner],
      ['年間ガソリン代（同距離）', fmtYen(aAnn), fmtYen(bAnn), aCost <= bCost ? 'a' : 'b'],
      ['年間節約額', aCost <= bCost ? fmtYen(saving) : '—', bCost < aCost ? fmtYen(saving) : '—', winner],
    ];

    var tbody = document.getElementById('fc-cmp-tbody');
    tbody.innerHTML = '';
    rows.forEach(function (r) {
      var tr = document.createElement('tr');
      var metric = r[0], av = r[1], bv = r[2], w = r[3];
      tr.innerHTML =
        '<td>' + metric + '</td>' +
        '<td class="' + (w === 'a' ? 'winner' : 'loser') + '">' + av + '</td>' +
        '<td class="' + (w === 'b' ? 'winner' : 'loser') + '">' + bv + '</td>';
      tbody.appendChild(tr);
    });

    fcDrawCompareChart(aName, bName, aCost, bCost, aFuel, bFuel);
  };

  function fcDrawCompareChart(aName, bName, aCost, bCost, aFuel, bFuel) {
    var canvas = document.getElementById('fc-cmp-chart');
    if (!canvas) return;
    var W = canvas.offsetWidth || 600;
    canvas.width  = W * window.devicePixelRatio;
    canvas.height = 240 * window.devicePixelRatio;
    canvas.style.height = '240px';
    var ctx = canvas.getContext('2d');
    ctx.scale(window.devicePixelRatio, window.devicePixelRatio);

    var groups = [
      { label: 'ガソリン代（円）', a: aCost, b: bCost },
      { label: '燃料（L）',        a: aFuel, b: bFuel },
    ];

    var padL = 60, padR = 20, padT = 20, padB = 50;
    var chartW = W - padL - padR;
    var chartH = 240 - padT - padB;
    var maxVal = Math.max(aCost, bCost, aFuel, bFuel) * 1.2 || 1;

    ctx.fillStyle = '#f8fafc';
    ctx.fillRect(0, 0, W, 240);

    ctx.strokeStyle = '#e2e8f0'; ctx.lineWidth = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = padT + chartH - (g / 4) * chartH;
      ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(W - padR, gy); ctx.stroke();
      ctx.fillStyle = '#94a3b8'; ctx.font = '10px sans-serif'; ctx.textAlign = 'right';
      ctx.fillText((maxVal * g / 4).toFixed(0), padL - 5, gy + 4);
    }

    var colors = { a: '#059669', b: '#3b82f6' };
    var groupW = chartW / groups.length;
    var barW   = Math.min(60, groupW * 0.3);

    groups.forEach(function (grp, gi) {
      var gx = padL + gi * groupW;
      ['a', 'b'].forEach(function (key, ki) {
        var v = grp[key];
        var bx = gx + ki * (barW + 6) + (groupW - 2 * barW - 6) / 2;
        var bh = (v / maxVal) * chartH;
        var by = padT + chartH - bh;
        ctx.fillStyle = colors[key];
        ctx.beginPath();
        ctx.roundRect ? ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]) : ctx.rect(bx, by, barW, bh);
        ctx.fill();
        ctx.fillStyle = '#0f172a'; ctx.font = 'bold 10px sans-serif'; ctx.textAlign = 'center';
        ctx.fillText(v.toFixed(0), bx + barW / 2, Math.max(by - 4, padT + 12));
      });
      ctx.fillStyle = '#475569'; ctx.font = '11px sans-serif'; ctx.textAlign = 'center';
      ctx.fillText(grp.label, gx + groupW / 2, padT + chartH + 16);
    });

    /* legend */
    var lx = padL;
    [{ key: 'a', name: aName }, { key: 'b', name: bName }].forEach(function (item) {
      ctx.fillStyle = colors[item.key];
      ctx.fillRect(lx, padT + chartH + 28, 10, 10);
      ctx.fillStyle = '#334155'; ctx.font = '11px sans-serif'; ctx.textAlign = 'left';
      ctx.fillText(item.name.length > 14 ? item.name.slice(0, 13) + '…' : item.name, lx + 14, padT + chartH + 38);
      lx += 160;
    });
  }

  /* ── 年間試算 ── */
  window.fcCalcAnnual = function () {
    var commute  = num('fc-ann-commute');
    var workdays = Math.min(7, Math.max(1, num('fc-ann-workdays')));
    var mode     = val('fc-ann-mode');
    var effVal   = num('fc-ann-eff');
    var price    = num('fc-ann-price');
    var extra    = num('fc-ann-extra');

    var lPer100 = toLper100km(mode, effVal);
    var weeklyKm  = commute * 2 * workdays + extra;
    var yearlyKm  = weeklyKm * 52;
    var yearlyL   = fuelLiters(yearlyKm, lPer100);
    var yearlyCost  = yearlyL * price;
    var monthlyCost = yearlyCost / 12;
    var weeklyCost  = yearlyCost / 52;
    var dailyCost   = yearlyCost / 365;

    set('fc-an-weekly',  fmtYen(weeklyCost));
    set('fc-an-monthly', fmtYen(monthlyCost));
    set('fc-an-yearly',  fmtYen(yearlyCost));
    set('fc-an-liters',  yearlyL.toFixed(0) + ' L');
    set('fc-an-km',      Math.round(yearlyKm).toLocaleString('ja-JP') + ' km');
    set('fc-an-perday',  fmtYen(dailyCost));

    fcDrawAnnualChart(weeklyCost, monthlyCost, yearlyCost);
  };

  function fcDrawAnnualChart(weekly, monthly, yearly) {
    var canvas = document.getElementById('fc-ann-chart');
    if (!canvas) return;
    var W = canvas.offsetWidth || 600;
    canvas.width  = W * window.devicePixelRatio;
    canvas.height = 240 * window.devicePixelRatio;
    canvas.style.height = '240px';
    var ctx = canvas.getContext('2d');
    ctx.scale(window.devicePixelRatio, window.devicePixelRatio);

    var labels = ['週あたり', '月あたり', '年間'];
    var values = [weekly, monthly, yearly];
    var clrs   = ['#059669', '#3b82f6', '#f59e0b'];

    var padL = 65, padR = 20, padT = 20, padB = 40;
    var chartW = W - padL - padR;
    var chartH = 240 - padT - padB;
    var maxVal = Math.max.apply(null, values) * 1.2 || 1;
    var barW   = Math.min(80, (chartW / labels.length) * 0.55);
    var gap    = chartW / labels.length;

    ctx.fillStyle = '#f8fafc';
    ctx.fillRect(0, 0, W, 240);

    ctx.strokeStyle = '#e2e8f0'; ctx.lineWidth = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = padT + chartH - (g / 4) * chartH;
      ctx.beginPath(); ctx.moveTo(padL, gy); ctx.lineTo(W - padR, gy); ctx.stroke();
      ctx.fillStyle = '#94a3b8'; ctx.font = '10px sans-serif'; ctx.textAlign = 'right';
      ctx.fillText((maxVal * g / 4).toFixed(0) + '円', padL - 5, gy + 4);
    }

    values.forEach(function (v, i) {
      var bx = padL + i * gap + (gap - barW) / 2;
      var bh = (v / maxVal) * chartH;
      var by = padT + chartH - bh;
      ctx.fillStyle = clrs[i];
      ctx.beginPath();
      ctx.roundRect ? ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]) : ctx.rect(bx, by, barW, bh);
      ctx.fill();
      ctx.fillStyle = '#0f172a'; ctx.font = 'bold 10px sans-serif'; ctx.textAlign = 'center';
      ctx.fillText(Math.round(v).toLocaleString('ja-JP') + '円', bx + barW / 2, Math.max(by - 5, padT + 12));
      ctx.fillStyle = '#475569'; ctx.font = '11px sans-serif';
      ctx.fillText(labels[i], bx + barW / 2, padT + chartH + 18);
    });
  }

  /* ── リサイズ対応 ── */
  var resizeTimer;
  window.addEventListener('resize', function () {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(function () {
      var active = document.querySelector('#fc-app .fc-panel.active');
      if (!active) return;
      if (active.id === 'fc-panel-compare') fcCalcCompare();
      if (active.id === 'fc-panel-annual')  fcCalcAnnual();
    }, 150);
  });

  /* ── 初期化 ── */
  fcCalcTrip();
  fcCalcCompare();
  fcCalcAnnual();
})();
</script>

---

## ガソリン代の節約に役立つ豆知識

**エコドライブで燃費を改善**

急加速・急ブレーキを避けてなめらかな運転を心がけることで、燃費を10〜15%程度改善できます。また、タイヤの空気圧を適正値に保つだけで燃費が約2〜3%向上することが知られています。

**ガソリン価格をチェックする習慣**

ガソリンスタンドによって価格が数円異なることは珍しくありません。通勤経路にある安いスタンドを把握しておくだけで、年間で数千円の節約につながります。

**通勤費の経費申告を忘れずに**

会社員の方は通勤費として申告できる場合があります。自営業・フリーランスの方は、業務で利用した走行分を経費として計上できます。領収書やガソリン代の記録を整理しておきましょう。

---

## 関連ツール

> 毎月の電気代を把握する → [電気代計算ツール](/ja/tools/electricity-calculator/)

> 収支を管理して節約を見える化 → [家計簿・予算管理ツール](/ja/tools/budget-planner/)

---

**車の維持費・家計管理を一元化しよう**

ガソリン代・保険・車検・ローン返済など、クルマにかかるコストをまとめて管理したいなら、クラウド会計ソフト「freee」が便利です。レシートの自動取り込みや確定申告サポートで、家計・事業の両方に対応しています。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
