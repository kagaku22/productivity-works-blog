---
title: "パーセント計算ツール｜割引・値上げ率・割合を自動計算【無料】"
date: 2026-05-16
draft: false
slug: "percent-calculator"
aliases:
  - "/ja/tools/percentage-calculator/"
  - "/ja/tools/discount-calculator/"
  - "/ja/tools/waribiki-calculator/"
description: "パーセント計算5モード対応：割合計算・百分率・変化率・割引額・チップ計算。買い物の割引額やセール価格、値上がり率などを瞬時に計算できる無料ツール。"
author: "Productivity Works編集部"
categories: ["無料ツール"]
tags: ["パーセント", "割引計算", "割合", "計算ツール", "節約"]
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/percent-calculator.png"
  alt: "パーセント計算ツール｜割引・値上げ率・割合を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# パーセント計算ツール｜割引・値上げ率・割合を自動計算【無料】

割引セールの値引き額、値上がりした商品の新価格、2つの数字の割合など、日常でよく使うパーセント計算を5つのモードで瞬時に計算できる無料ツールです。スライダーや入力フォームで直感的に操作でき、計算式もあわせて表示するので仕組みも一目でわかります。

<div id="percent-calculator-app" style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; max-width: 680px; margin: 0 auto;">

<style>
#percent-calculator-app * { box-sizing: border-box; }
#percent-calculator-app .pc-tabs { display: flex; flex-wrap: wrap; gap: 4px; margin-bottom: 0; }
#percent-calculator-app .pc-tab-btn {
  padding: 8px 14px; border: 2px solid #e0e0e0; border-bottom: none;
  background: #f5f5f5; color: #555; cursor: pointer; border-radius: 6px 6px 0 0;
  font-size: 13px; font-weight: 600; transition: all 0.15s; white-space: nowrap;
}
#percent-calculator-app .pc-tab-btn:hover { background: #ede9fe; border-color: #a5b4fc; color: #4f46e5; }
#percent-calculator-app .pc-tab-btn.active { background: #4f46e5; color: #fff; border-color: #4f46e5; }
#percent-calculator-app .pc-panel {
  display: none; background: #fff; border: 2px solid #4f46e5;
  border-radius: 0 6px 6px 6px; padding: 24px; margin-bottom: 24px;
}
#percent-calculator-app .pc-panel.active { display: block; }
#percent-calculator-app .pc-field { margin-bottom: 16px; }
#percent-calculator-app .pc-field label {
  display: block; font-size: 13px; font-weight: 600; color: #374151; margin-bottom: 6px;
}
#percent-calculator-app .pc-field input[type="number"] {
  width: 100%; padding: 10px 14px; border: 1.5px solid #d1d5db; border-radius: 8px;
  font-size: 16px; outline: none; transition: border-color 0.15s;
}
#percent-calculator-app .pc-field input[type="number"]:focus { border-color: #4f46e5; box-shadow: 0 0 0 3px rgba(79,70,229,0.1); }
#percent-calculator-app .pc-field input[type="range"] {
  width: 100%; accent-color: #4f46e5; height: 6px; cursor: pointer;
}
#percent-calculator-app .pc-slider-row { display: flex; align-items: center; gap: 12px; }
#percent-calculator-app .pc-slider-val {
  min-width: 60px; text-align: center; font-size: 20px; font-weight: 700; color: #4f46e5;
}
#percent-calculator-app .pc-calc-btn {
  width: 100%; padding: 12px; background: #4f46e5; color: #fff; border: none;
  border-radius: 8px; font-size: 16px; font-weight: 700; cursor: pointer;
  transition: background 0.15s; margin-top: 4px;
}
#percent-calculator-app .pc-calc-btn:hover { background: #4338ca; }
#percent-calculator-app .pc-result {
  margin-top: 18px; padding: 16px; background: #f5f3ff; border-radius: 10px;
  border-left: 4px solid #4f46e5;
}
#percent-calculator-app .pc-result-main { font-size: 28px; font-weight: 800; color: #4f46e5; }
#percent-calculator-app .pc-result-formula { font-size: 13px; color: #6b7280; margin-top: 6px; }
#percent-calculator-app .pc-result-up { color: #16a34a; }
#percent-calculator-app .pc-result-down { color: #dc2626; }
#percent-calculator-app .pc-highlight {
  margin-top: 10px; padding: 10px 14px; background: #fef3c7;
  border-radius: 8px; font-size: 14px; font-weight: 600; color: #92400e;
}
#percent-calculator-app .pc-quick-btns { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 10px; }
#percent-calculator-app .pc-quick-btn {
  padding: 6px 14px; border: 1.5px solid #4f46e5; border-radius: 20px;
  background: #fff; color: #4f46e5; font-size: 13px; font-weight: 600;
  cursor: pointer; transition: all 0.15s;
}
#percent-calculator-app .pc-quick-btn:hover { background: #4f46e5; color: #fff; }
#percent-calculator-app .pc-table-wrap { overflow-x: auto; margin-top: 8px; }
#percent-calculator-app .pc-table {
  width: 100%; border-collapse: collapse; font-size: 14px;
}
#percent-calculator-app .pc-table th {
  background: #4f46e5; color: #fff; padding: 10px 12px; text-align: right; white-space: nowrap;
}
#percent-calculator-app .pc-table th:first-child { text-align: left; }
#percent-calculator-app .pc-table td {
  padding: 9px 12px; text-align: right; border-bottom: 1px solid #e5e7eb;
}
#percent-calculator-app .pc-table td:first-child { text-align: left; font-weight: 600; color: #374151; }
#percent-calculator-app .pc-table tr:nth-child(even) td { background: #f9fafb; }
#percent-calculator-app .pc-section-title {
  font-size: 16px; font-weight: 700; color: #1f2937; margin: 24px 0 10px;
  padding-bottom: 6px; border-bottom: 2px solid #e5e7eb;
}
#percent-calculator-app .pc-note { font-size: 13px; color: #6b7280; margin-top: 8px; }
#percent-calculator-app .pc-example-box {
  margin-top: 10px; padding: 12px 16px; background: #f0fdf4; border-radius: 8px;
  border-left: 4px solid #16a34a; font-size: 14px; color: #166534;
}
</style>

<!-- タブナビゲーション -->
<div class="pc-tabs">
  <button class="pc-tab-btn active" onclick="pcShowTab(0, this)">AのB%はいくら？</button>
  <button class="pc-tab-btn" onclick="pcShowTab(1, this)">AはBの何%？</button>
  <button class="pc-tab-btn" onclick="pcShowTab(2, this)">変化率</button>
  <button class="pc-tab-btn" onclick="pcShowTab(3, this)">割引計算</button>
  <button class="pc-tab-btn" onclick="pcShowTab(4, this)">値上げ計算</button>
</div>

<!-- タブ0: AのB%はいくら？ -->
<div class="pc-panel active" id="pc-panel-0">
  <div class="pc-field">
    <label>数値 A</label>
    <input type="number" id="p0-a" placeholder="例：5000" oninput="pcCalc0()">
  </div>
  <div class="pc-field">
    <label>パーセント B（%）</label>
    <input type="number" id="p0-b" placeholder="例：20" oninput="pcCalc0()">
  </div>
  <div id="p0-result" class="pc-result" style="display:none;">
    <div class="pc-result-main" id="p0-main"></div>
    <div class="pc-result-formula" id="p0-formula"></div>
  </div>
</div>

<!-- タブ1: AはBの何%？ -->
<div class="pc-panel" id="pc-panel-1">
  <div class="pc-field">
    <label>数値 A（部分）</label>
    <input type="number" id="p1-a" placeholder="例：800" oninput="pcCalc1()">
  </div>
  <div class="pc-field">
    <label>数値 B（全体）</label>
    <input type="number" id="p1-b" placeholder="例：4000" oninput="pcCalc1()">
  </div>
  <div id="p1-result" class="pc-result" style="display:none;">
    <div class="pc-result-main" id="p1-main"></div>
    <div class="pc-result-formula" id="p1-formula"></div>
  </div>
</div>

<!-- タブ2: 変化率 -->
<div class="pc-panel" id="pc-panel-2">
  <div class="pc-field">
    <label>変更前の値</label>
    <input type="number" id="p2-before" placeholder="例：1000" oninput="pcCalc2()">
  </div>
  <div class="pc-field">
    <label>変更後の値</label>
    <input type="number" id="p2-after" placeholder="例：1200" oninput="pcCalc2()">
  </div>
  <div id="p2-result" class="pc-result" style="display:none;">
    <div class="pc-result-main" id="p2-main"></div>
    <div class="pc-result-formula" id="p2-formula"></div>
  </div>
</div>

<!-- タブ3: 割引計算 -->
<div class="pc-panel" id="pc-panel-3">
  <div class="pc-field">
    <label>元の価格（円）</label>
    <input type="number" id="p3-price" placeholder="例：3980" value="" oninput="pcCalc3()">
  </div>
  <div class="pc-field">
    <label>割引率</label>
    <div class="pc-slider-row">
      <input type="range" id="p3-rate" min="5" max="90" value="20" step="5" oninput="pcSlider3(); pcCalc3();">
      <div class="pc-slider-val" id="p3-rate-val">20%</div>
    </div>
    <div class="pc-quick-btns">
      <button class="pc-quick-btn" onclick="pcSetDiscount(10)">10% OFF</button>
      <button class="pc-quick-btn" onclick="pcSetDiscount(20)">20% OFF</button>
      <button class="pc-quick-btn" onclick="pcSetDiscount(30)">30% OFF</button>
      <button class="pc-quick-btn" onclick="pcSetDiscount(50)">半額（50%）</button>
    </div>
  </div>
  <div id="p3-result" class="pc-result" style="display:none;">
    <div id="p3-main"></div>
    <div class="pc-result-formula" id="p3-formula"></div>
    <div class="pc-highlight" id="p3-highlight"></div>
  </div>
</div>

<!-- タブ4: 値上げ計算 -->
<div class="pc-panel" id="pc-panel-4">
  <div class="pc-field">
    <label>元の価格（円）</label>
    <input type="number" id="p4-price" placeholder="例：1000" value="" oninput="pcCalc4()">
  </div>
  <div class="pc-field">
    <label>値上げ率</label>
    <div class="pc-slider-row">
      <input type="range" id="p4-rate" min="1" max="50" value="10" step="1" oninput="pcSlider4(); pcCalc4();">
      <div class="pc-slider-val" id="p4-rate-val">10%</div>
    </div>
  </div>
  <div id="p4-result" class="pc-result" style="display:none;">
    <div id="p4-main"></div>
    <div class="pc-result-formula" id="p4-formula"></div>
  </div>
  <div class="pc-example-box" id="p4-example">
    身近な例：100円の商品が10%値上げで <strong>110円</strong> になります。
  </div>
</div>

<!-- 早見表 -->
<div class="pc-section-title">パーセント早見表</div>
<p style="font-size:14px; color:#6b7280; margin-bottom:10px;">よくある金額に対する各割引・割合の計算結果一覧です。</p>
<div class="pc-table-wrap">
  <table class="pc-table">
    <thead>
      <tr>
        <th>金額</th>
        <th>10%</th>
        <th>20%</th>
        <th>30%</th>
        <th>50%</th>
      </tr>
    </thead>
    <tbody id="pc-table-body"></tbody>
  </table>
</div>
<p class="pc-note">※各セルの数値は「その金額の○%に相当する額（円）」です。</p>

<script>
(function() {
  // 早見表の生成
  var amounts = [100, 500, 1000, 5000, 10000];
  var rates = [10, 20, 30, 50];
  var tbody = document.getElementById('pc-table-body');
  amounts.forEach(function(amount) {
    var tr = document.createElement('tr');
    var tdLabel = document.createElement('td');
    tdLabel.textContent = amount.toLocaleString('ja-JP') + '円';
    tr.appendChild(tdLabel);
    rates.forEach(function(rate) {
      var td = document.createElement('td');
      td.textContent = (amount * rate / 100).toLocaleString('ja-JP') + '円';
      tr.appendChild(td);
    });
    tbody.appendChild(tr);
  });

  // タブ切り替え
  window.pcShowTab = function(index, btn) {
    var panels = document.querySelectorAll('#percent-calculator-app .pc-panel');
    var btns = document.querySelectorAll('#percent-calculator-app .pc-tab-btn');
    panels.forEach(function(p) { p.classList.remove('active'); });
    btns.forEach(function(b) { b.classList.remove('active'); });
    panels[index].classList.add('active');
    btn.classList.add('active');
  };

  // ヘルパー: 整数なら整数表示、小数なら小数点以下2桁まで
  function fmtNum(n) {
    if (n === null || isNaN(n)) return '—';
    return Math.abs(n - Math.round(n)) < 0.001 ? Math.round(n).toLocaleString('ja-JP') : n.toFixed(2).replace(/\.?0+$/, '');
  }
  function fmtYen(n) {
    return Math.round(n).toLocaleString('ja-JP') + '円';
  }

  // タブ0: AのB%はいくら？
  window.pcCalc0 = function() {
    var a = parseFloat(document.getElementById('p0-a').value);
    var b = parseFloat(document.getElementById('p0-b').value);
    var res = document.getElementById('p0-result');
    if (isNaN(a) || isNaN(b)) { res.style.display = 'none'; return; }
    var result = a * b / 100;
    document.getElementById('p0-main').textContent = fmtNum(result);
    document.getElementById('p0-formula').textContent =
      fmtNum(a) + ' × ' + fmtNum(b) + ' ÷ 100 ＝ ' + fmtNum(result);
    res.style.display = 'block';
  };

  // タブ1: AはBの何%？
  window.pcCalc1 = function() {
    var a = parseFloat(document.getElementById('p1-a').value);
    var b = parseFloat(document.getElementById('p1-b').value);
    var res = document.getElementById('p1-result');
    if (isNaN(a) || isNaN(b) || b === 0) { res.style.display = 'none'; return; }
    var result = (a / b) * 100;
    document.getElementById('p1-main').textContent = fmtNum(result) + '%';
    document.getElementById('p1-formula').textContent =
      fmtNum(a) + ' ÷ ' + fmtNum(b) + ' × 100 ＝ ' + fmtNum(result) + '%';
    res.style.display = 'block';
  };

  // タブ2: 変化率
  window.pcCalc2 = function() {
    var before = parseFloat(document.getElementById('p2-before').value);
    var after = parseFloat(document.getElementById('p2-after').value);
    var res = document.getElementById('p2-result');
    if (isNaN(before) || isNaN(after) || before === 0) { res.style.display = 'none'; return; }
    var rate = ((after - before) / Math.abs(before)) * 100;
    var sign = rate >= 0 ? '+' : '';
    var cls = rate >= 0 ? 'pc-result-up' : 'pc-result-down';
    var label = rate >= 0 ? '増加' : '減少';
    document.getElementById('p2-main').innerHTML =
      '<span class="' + cls + '">' + sign + fmtNum(rate) + '%</span>&nbsp;<span style="font-size:16px;font-weight:600;color:#6b7280;">(' + label + ')</span>';
    document.getElementById('p2-formula').textContent =
      '（' + fmtNum(after) + ' − ' + fmtNum(before) + '） ÷ ' + fmtNum(Math.abs(before)) + ' × 100 ＝ ' + sign + fmtNum(rate) + '%';
    res.style.display = 'block';
  };

  // タブ3: 割引計算
  window.pcSlider3 = function() {
    var val = document.getElementById('p3-rate').value;
    document.getElementById('p3-rate-val').textContent = val + '%';
  };
  window.pcSetDiscount = function(v) {
    document.getElementById('p3-rate').value = v;
    document.getElementById('p3-rate-val').textContent = v + '%';
    pcCalc3();
  };
  window.pcCalc3 = function() {
    var price = parseFloat(document.getElementById('p3-price').value);
    var rate = parseFloat(document.getElementById('p3-rate').value);
    var res = document.getElementById('p3-result');
    if (isNaN(price) || price <= 0) { res.style.display = 'none'; return; }
    var discount = Math.round(price * rate / 100);
    var pay = price - discount;
    document.getElementById('p3-main').innerHTML =
      '<div style="display:flex;gap:16px;flex-wrap:wrap;">' +
      '<div><div style="font-size:12px;color:#6b7280;font-weight:600;">割引額</div><div class="pc-result-main pc-result-down">−' + fmtYen(discount) + '</div></div>' +
      '<div><div style="font-size:12px;color:#6b7280;font-weight:600;">支払額</div><div class="pc-result-main">' + fmtYen(pay) + '</div></div>' +
      '</div>';
    document.getElementById('p3-formula').textContent =
      fmtYen(price) + ' × ' + rate + '% ＝ 割引額 ' + fmtYen(discount) + '　／　支払額 ' + fmtYen(price) + ' − ' + fmtYen(discount) + ' ＝ ' + fmtYen(pay);
    document.getElementById('p3-highlight').textContent =
      'お得額：' + fmtYen(discount) + ' お得！（元値の' + rate + '%OFF）';
    res.style.display = 'block';
  };

  // タブ4: 値上げ計算
  window.pcSlider4 = function() {
    var val = document.getElementById('p4-rate').value;
    document.getElementById('p4-rate-val').textContent = val + '%';
  };
  window.pcCalc4 = function() {
    var price = parseFloat(document.getElementById('p4-price').value);
    var rate = parseFloat(document.getElementById('p4-rate').value);
    var res = document.getElementById('p4-result');
    var exampleRate = parseFloat(document.getElementById('p4-rate').value);
    var exampleNew = Math.round(100 * (1 + exampleRate / 100));
    document.getElementById('p4-example').innerHTML =
      '身近な例：100円の商品が' + exampleRate + '%値上げで <strong>' + exampleNew + '円</strong> になります。';
    if (isNaN(price) || price <= 0) { res.style.display = 'none'; return; }
    var increase = Math.round(price * rate / 100);
    var newPrice = price + increase;
    document.getElementById('p4-main').innerHTML =
      '<div style="display:flex;gap:16px;flex-wrap:wrap;">' +
      '<div><div style="font-size:12px;color:#6b7280;font-weight:600;">値上げ額</div><div class="pc-result-main pc-result-down">+' + fmtYen(increase) + '</div></div>' +
      '<div><div style="font-size:12px;color:#6b7280;font-weight:600;">新価格</div><div class="pc-result-main">' + fmtYen(newPrice) + '</div></div>' +
      '</div>';
    document.getElementById('p4-formula').textContent =
      fmtYen(price) + ' × ' + rate + '% ＝ 値上げ額 ' + fmtYen(increase) + '　／　新価格 ' + fmtYen(price) + ' + ' + fmtYen(increase) + ' ＝ ' + fmtYen(newPrice);
    res.style.display = 'block';
  };

  // 初期化: スライダー表示を同期
  window.pcSlider3();
  window.pcSlider4();
})();
</script>

</div>

---

## 関連ツール

> 月々の支出バランスを見直す → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)

> 複利の効果を計算 → [複利計算シミュレーター](/ja/tools/fukuri-keisan/)

> サブスクの年間コストを計算 → [サブスク管理計算ツール](/ja/tools/subscription-cost-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [Excel関数よく使うもの一覧【2026年版・コピペ即使える】仕事で役立つ厳選50選](/ja/posts/excel-kansu-yoku-tsukau-ichiran/)
- [飲食店の原価率計算をExcelで簡単管理する方法2026](/ja/posts/insyoku-excel-genkaritu-keisan-2026/)
- [飲食店経営Excel管理テンプレート活用ガイド2026](/ja/posts/insyoku-keiei-excel-kanri-2026/)
