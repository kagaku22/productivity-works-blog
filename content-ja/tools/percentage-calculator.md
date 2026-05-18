---
title: "パーセント計算ツール｜割合・増減率・割引を瞬時に計算【無料】"
date: 2025-11-26
description: "無料のパーセント計算ツール。割合・増減率・構成比を即計算。複数の計算モード対応。登録不要。"
categories: ["無料ツール"]
slug: "percentage-calculator"
ShowToc: false
cover:
  image: "/images/covers/percentage-calculator-ja.png"
  alt: "パーセント計算ツール"
---

<div id="pc-app">
<style>
#pc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Yu Gothic", "Segoe UI", Roboto, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
}
#pc-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 18px 0;
}
#pc-app .pc-mode-tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 22px;
}
#pc-app .pc-tab {
  padding: 8px 14px;
  border-radius: 8px;
  border: 1.5px solid #e2e8f0;
  background: #f8fafc;
  color: #475569;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
  white-space: nowrap;
}
#pc-app .pc-tab:hover {
  border-color: #3b82f6;
  color: #3b82f6;
}
#pc-app .pc-tab.active {
  background: #3b82f6;
  border-color: #3b82f6;
  color: #fff;
}
#pc-app .pc-panel {
  display: none;
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 22px 24px;
  margin-bottom: 18px;
}
#pc-app .pc-panel.active {
  display: block;
}
#pc-app .pc-row {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 14px;
}
#pc-app .pc-row label {
  font-size: 14px;
  font-weight: 600;
  color: #374151;
  min-width: 30px;
}
#pc-app .pc-input {
  width: 120px;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 15px;
  color: #1e293b;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
}
#pc-app .pc-input:focus {
  border-color: #3b82f6;
}
#pc-app .pc-text {
  font-size: 14px;
  color: #64748b;
}
#pc-app .pc-btn {
  padding: 10px 24px;
  background: #3b82f6;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#pc-app .pc-btn:hover {
  background: #2563eb;
}
#pc-app .pc-result-box {
  background: #fff;
  border: 1.5px solid #bae6fd;
  border-radius: 10px;
  padding: 18px 20px;
  margin-top: 16px;
  display: none;
}
#pc-app .pc-result-box.show {
  display: block;
}
#pc-app .pc-result-value {
  font-size: 2rem;
  font-weight: 800;
  color: #0284c7;
  margin-bottom: 6px;
}
#pc-app .pc-result-formula {
  font-size: 13px;
  color: #64748b;
  margin-bottom: 14px;
}
#pc-app .pc-bar-wrap {
  background: #e2e8f0;
  border-radius: 99px;
  height: 12px;
  overflow: hidden;
  margin-bottom: 6px;
}
#pc-app .pc-bar-fill {
  height: 12px;
  background: linear-gradient(90deg, #3b82f6, #0ea5e9);
  border-radius: 99px;
  transition: width 0.4s ease;
  width: 0%;
}
#pc-app .pc-bar-label {
  font-size: 12px;
  color: #94a3b8;
  text-align: right;
}
#pc-app .pc-error {
  color: #ef4444;
  font-size: 13px;
  margin-top: 8px;
  display: none;
}
#pc-app .pc-error.show {
  display: block;
}
@media (max-width: 500px) {
  #pc-app .pc-input { width: 90px; }
  #pc-app .pc-tab { font-size: 12px; padding: 7px 10px; }
  #pc-app .pc-result-value { font-size: 1.5rem; }
}
</style>

<h2>パーセント計算ツール</h2>

<div class="pc-mode-tabs">
  <button class="pc-tab active" data-mode="1">Xの何%</button>
  <button class="pc-tab" data-mode="2">何%にあたる?</button>
  <button class="pc-tab" data-mode="3">増減率</button>
  <button class="pc-tab" data-mode="4">%を加減する</button>
  <button class="pc-tab" data-mode="5">%差</button>
</div>

<!-- モード1: YのX%は? -->
<div class="pc-panel active" id="pc-panel-1">
  <div class="pc-row">
    <input class="pc-input" id="m1-y" type="number" placeholder="200" />
    <span class="pc-text">の</span>
    <input class="pc-input" id="m1-x" type="number" placeholder="15" />
    <span class="pc-text">% は?</span>
  </div>
  <button class="pc-btn" onclick="calcMode1()">計算する</button>
  <div class="pc-error" id="m1-err">有効な数値を入力してください。</div>
  <div class="pc-result-box" id="m1-result">
    <div class="pc-result-value" id="m1-val"></div>
    <div class="pc-result-formula" id="m1-formula"></div>
    <div class="pc-bar-wrap"><div class="pc-bar-fill" id="m1-bar"></div></div>
    <div class="pc-bar-label" id="m1-bar-label"></div>
  </div>
</div>

<!-- モード2: XはYの何%? -->
<div class="pc-panel" id="pc-panel-2">
  <div class="pc-row">
    <input class="pc-input" id="m2-x" type="number" placeholder="30" />
    <span class="pc-text">は</span>
    <input class="pc-input" id="m2-y" type="number" placeholder="200" />
    <span class="pc-text">の何%?</span>
  </div>
  <button class="pc-btn" onclick="calcMode2()">計算する</button>
  <div class="pc-error" id="m2-err">有効な数値を入力してください（Yは0以外）。</div>
  <div class="pc-result-box" id="m2-result">
    <div class="pc-result-value" id="m2-val"></div>
    <div class="pc-result-formula" id="m2-formula"></div>
    <div class="pc-bar-wrap"><div class="pc-bar-fill" id="m2-bar"></div></div>
    <div class="pc-bar-label" id="m2-bar-label"></div>
  </div>
</div>

<!-- モード3: 増減率 -->
<div class="pc-panel" id="pc-panel-3">
  <div class="pc-row">
    <span class="pc-text">変化前</span>
    <input class="pc-input" id="m3-x" type="number" placeholder="100" />
    <span class="pc-text">→ 変化後</span>
    <input class="pc-input" id="m3-y" type="number" placeholder="130" />
  </div>
  <button class="pc-btn" onclick="calcMode3()">計算する</button>
  <div class="pc-error" id="m3-err">有効な数値を入力してください（変化前は0以外）。</div>
  <div class="pc-result-box" id="m3-result">
    <div class="pc-result-value" id="m3-val"></div>
    <div class="pc-result-formula" id="m3-formula"></div>
    <div class="pc-bar-wrap"><div class="pc-bar-fill" id="m3-bar"></div></div>
    <div class="pc-bar-label" id="m3-bar-label"></div>
  </div>
</div>

<!-- モード4: %を加減する -->
<div class="pc-panel" id="pc-panel-4">
  <div class="pc-row">
    <input class="pc-input" id="m4-y" type="number" placeholder="200" />
    <span class="pc-text">に</span>
    <input class="pc-input" id="m4-x" type="number" placeholder="15" />
    <span class="pc-text">%を</span>
  </div>
  <div style="display:flex;gap:14px;margin-bottom:14px;">
    <label style="font-size:14px;color:#374151;display:flex;align-items:center;gap:5px;cursor:pointer;">
      <input type="radio" name="m4-op" value="add" checked /> 加算する
    </label>
    <label style="font-size:14px;color:#374151;display:flex;align-items:center;gap:5px;cursor:pointer;">
      <input type="radio" name="m4-op" value="sub" /> 減算する
    </label>
  </div>
  <button class="pc-btn" onclick="calcMode4()">計算する</button>
  <div class="pc-error" id="m4-err">有効な数値を入力してください。</div>
  <div class="pc-result-box" id="m4-result">
    <div class="pc-result-value" id="m4-val"></div>
    <div class="pc-result-formula" id="m4-formula"></div>
    <div class="pc-bar-wrap"><div class="pc-bar-fill" id="m4-bar"></div></div>
    <div class="pc-bar-label" id="m4-bar-label"></div>
  </div>
</div>

<!-- モード5: %差 -->
<div class="pc-panel" id="pc-panel-5">
  <div class="pc-row">
    <input class="pc-input" id="m5-x" type="number" placeholder="80" />
    <span class="pc-text">と</span>
    <input class="pc-input" id="m5-y" type="number" placeholder="100" />
    <span class="pc-text">の%差</span>
  </div>
  <button class="pc-btn" onclick="calcMode5()">計算する</button>
  <div class="pc-error" id="m5-err">有効な数値を入力してください（平均が0にならないよう）。</div>
  <div class="pc-result-box" id="m5-result">
    <div class="pc-result-value" id="m5-val"></div>
    <div class="pc-result-formula" id="m5-formula"></div>
    <div class="pc-bar-wrap"><div class="pc-bar-fill" id="m5-bar"></div></div>
    <div class="pc-bar-label" id="m5-bar-label"></div>
  </div>
</div>

<script>
(function() {
  // タブ切替
  var tabs = document.querySelectorAll('#pc-app .pc-tab');
  tabs.forEach(function(tab) {
    tab.addEventListener('click', function() {
      tabs.forEach(function(t) { t.classList.remove('active'); });
      document.querySelectorAll('#pc-app .pc-panel').forEach(function(p) { p.classList.remove('active'); });
      tab.classList.add('active');
      document.getElementById('pc-panel-' + tab.dataset.mode).classList.add('active');
    });
  });

  function fmt(n) {
    if (Math.abs(n) >= 1000) return n.toLocaleString('ja-JP', {maximumFractionDigits: 4});
    return parseFloat(n.toFixed(4)).toString();
  }

  function clampBar(pct) {
    return Math.min(100, Math.max(0, Math.abs(pct)));
  }

  function showResult(id, value, formula, barPct, barLabelText) {
    var box = document.getElementById(id + '-result');
    box.classList.add('show');
    document.getElementById(id + '-val').textContent = value;
    document.getElementById(id + '-formula').textContent = formula;
    document.getElementById(id + '-bar').style.width = clampBar(barPct) + '%';
    document.getElementById(id + '-bar-label').textContent = barLabelText;
  }

  function showErr(id, show) {
    document.getElementById(id + '-err').classList.toggle('show', show);
    if (show) document.getElementById(id + '-result').classList.remove('show');
  }

  // モード1: YのX%は?
  window.calcMode1 = function() {
    var x = parseFloat(document.getElementById('m1-x').value);
    var y = parseFloat(document.getElementById('m1-y').value);
    if (isNaN(x) || isNaN(y)) { showErr('m1', true); return; }
    showErr('m1', false);
    var result = (x / 100) * y;
    showResult('m1',
      fmt(result),
      fmt(y) + ' \u00d7 ' + x + '% = ' + fmt(result),
      clampBar(x),
      fmt(y) + ' の ' + x + '% = ' + fmt(result)
    );
  };

  // モード2: XはYの何%?
  window.calcMode2 = function() {
    var x = parseFloat(document.getElementById('m2-x').value);
    var y = parseFloat(document.getElementById('m2-y').value);
    if (isNaN(x) || isNaN(y) || y === 0) { showErr('m2', true); return; }
    showErr('m2', false);
    var result = (x / y) * 100;
    showResult('m2',
      fmt(result) + '%',
      fmt(x) + ' \u00f7 ' + fmt(y) + ' \u00d7 100 = ' + fmt(result) + '%',
      clampBar(result),
      fmt(x) + ' は ' + fmt(y) + ' の ' + fmt(result) + '%'
    );
  };

  // モード3: 増減率
  window.calcMode3 = function() {
    var x = parseFloat(document.getElementById('m3-x').value);
    var y = parseFloat(document.getElementById('m3-y').value);
    if (isNaN(x) || isNaN(y) || x === 0) { showErr('m3', true); return; }
    showErr('m3', false);
    var result = ((y - x) / Math.abs(x)) * 100;
    var direction = result >= 0 ? '\u2191 増加' : '\u2193 減少';
    showResult('m3',
      (result >= 0 ? '+' : '') + fmt(result) + '% (' + direction + ')',
      '(' + fmt(y) + ' \u2212 ' + fmt(x) + ') \u00f7 ' + fmt(Math.abs(x)) + ' \u00d7 100 = ' + fmt(result) + '%',
      clampBar(Math.abs(result)),
      fmt(x) + ' \u2192 ' + fmt(y) + ': ' + (result >= 0 ? '+' : '') + fmt(result) + '%'
    );
  };

  // モード4: %を加減する
  window.calcMode4 = function() {
    var y = parseFloat(document.getElementById('m4-y').value);
    var x = parseFloat(document.getElementById('m4-x').value);
    var op = document.querySelector('input[name="m4-op"]:checked').value;
    if (isNaN(x) || isNaN(y)) { showErr('m4', true); return; }
    showErr('m4', false);
    var delta = (x / 100) * y;
    var result = op === 'add' ? y + delta : y - delta;
    var sign = op === 'add' ? '+' : '\u2212';
    var opLabel = op === 'add' ? '加算' : '減算';
    showResult('m4',
      fmt(result),
      fmt(y) + ' ' + sign + ' (' + x + '% \u00d7 ' + fmt(y) + ') = ' + fmt(y) + ' ' + sign + ' ' + fmt(delta) + ' = ' + fmt(result),
      clampBar(x),
      fmt(y) + ' に ' + x + '% を' + opLabel + ' \u2192 ' + fmt(result)
    );
  };

  // モード5: %差
  window.calcMode5 = function() {
    var x = parseFloat(document.getElementById('m5-x').value);
    var y = parseFloat(document.getElementById('m5-y').value);
    var avg = (x + y) / 2;
    if (isNaN(x) || isNaN(y) || avg === 0) { showErr('m5', true); return; }
    showErr('m5', false);
    var result = (Math.abs(x - y) / Math.abs(avg)) * 100;
    showResult('m5',
      fmt(result) + '%',
      '|' + fmt(x) + ' \u2212 ' + fmt(y) + '| \u00f7 ((' + fmt(x) + ' + ' + fmt(y) + ') / 2) \u00d7 100 = ' + fmt(result) + '%',
      clampBar(result),
      fmt(x) + ' と ' + fmt(y) + ' の%差: ' + fmt(result) + '%'
    );
  };

  // Enterキー対応
  document.querySelectorAll('#pc-app .pc-input').forEach(function(inp) {
    inp.addEventListener('keydown', function(e) {
      if (e.key === 'Enter') {
        var panel = inp.closest('.pc-panel');
        var btn = panel.querySelector('.pc-btn');
        if (btn) btn.click();
      }
    });
  });
})();
</script>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>

---

**関連ツール:**

> ROI計算 → [ROI計算ツール](/ja/tools/roi-calculator/)

> 関数電卓 → [関数電卓](/ja/tools/scientific-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
