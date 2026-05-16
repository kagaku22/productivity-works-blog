---
title: "割り勘計算ツール"
date: 2025-05-16
description: "無料の割り勘計算ツール。飲み会・食事の会計を人数で均等割り・傾斜配分。端数処理・幹事負担調整にも対応、会員登録不要。"
categories: ["無料ツール"]
slug: "split-bill-calculator"
ShowToc: false
cover:
  image: "/images/covers/split-bill-calculator-ja.png"
  alt: "割り勘計算ツール"
---

<div id="sb-app">

<style>
#sb-app {
  font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  padding: 0 4px;
  color: #1e293b;
}
#sb-app h2 {
  font-size: 1.15rem;
  font-weight: 700;
  color: #334155;
  margin: 24px 0 10px;
  padding-bottom: 6px;
  border-bottom: 2px solid #e2e8f0;
}
#sb-app .sb-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 18px;
}
#sb-app label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 5px;
}
#sb-app input[type="number"],
#sb-app input[type="text"],
#sb-app select {
  width: 100%;
  box-sizing: border-box;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  color: #1e293b;
  background: #fff;
  transition: border-color 0.15s;
  outline: none;
}
#sb-app input[type="number"]:focus,
#sb-app input[type="text"]:focus,
#sb-app select:focus {
  border-color: #38bdf8;
}
#sb-app .sb-row {
  display: flex;
  gap: 12px;
  margin-bottom: 14px;
  flex-wrap: wrap;
}
#sb-app .sb-row > div {
  flex: 1 1 160px;
  min-width: 140px;
}
#sb-app .sb-row-full {
  margin-bottom: 14px;
}
#sb-app .sb-mode-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}
#sb-app .sb-tab-btn {
  flex: 1;
  padding: 9px 4px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  background: #fff;
  font-size: 13px;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  transition: all 0.15s;
  text-align: center;
}
#sb-app .sb-tab-btn.active {
  background: #0284c7;
  border-color: #0284c7;
  color: #fff;
}
#sb-app .sb-tab-btn:hover:not(.active) {
  border-color: #38bdf8;
  color: #0284c7;
}
#sb-app .sb-members {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-bottom: 10px;
}
#sb-app .sb-member-row {
  display: flex;
  gap: 8px;
  align-items: center;
}
#sb-app .sb-member-row input[type="text"] {
  flex: 1.5;
  min-width: 80px;
}
#sb-app .sb-member-row input[type="number"] {
  flex: 1;
  min-width: 80px;
}
#sb-app .sb-member-row .sb-remove-btn {
  background: none;
  border: 1.5px solid #fca5a5;
  border-radius: 6px;
  color: #ef4444;
  font-size: 16px;
  width: 32px;
  height: 36px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  transition: background 0.12s;
}
#sb-app .sb-member-row .sb-remove-btn:hover {
  background: #fee2e2;
}
#sb-app .sb-add-btn {
  padding: 7px 14px;
  border: 1.5px dashed #94a3b8;
  border-radius: 7px;
  background: #fff;
  color: #64748b;
  font-size: 13px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.15s;
}
#sb-app .sb-add-btn:hover {
  border-color: #0284c7;
  color: #0284c7;
}
#sb-app .sb-checkbox-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 10px;
  font-size: 13px;
  color: #475569;
  font-weight: 600;
  cursor: pointer;
}
#sb-app .sb-checkbox-row input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #0284c7;
  cursor: pointer;
}
#sb-app .sb-inline-input {
  display: inline-block;
  width: 70px;
  padding: 4px 8px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 14px;
  margin: 0 4px;
  vertical-align: middle;
}
#sb-app .sb-calc-btn {
  width: 100%;
  padding: 13px;
  background: linear-gradient(135deg, #0284c7 0%, #0369a1 100%);
  color: #fff;
  border: none;
  border-radius: 9px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  margin-top: 4px;
}
#sb-app .sb-calc-btn:hover {
  opacity: 0.92;
  transform: translateY(-1px);
}
#sb-app .sb-calc-btn:active {
  transform: translateY(0);
}
#sb-app .sb-result {
  display: none;
  background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
  border: 1.5px solid #bae6fd;
  border-radius: 10px;
  padding: 20px;
  margin-top: 18px;
}
#sb-app .sb-result.visible {
  display: block;
}
#sb-app .sb-result h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #0369a1;
  margin: 0 0 14px;
}
#sb-app .sb-result-main {
  font-size: 2rem;
  font-weight: 800;
  color: #0284c7;
  margin-bottom: 6px;
  letter-spacing: -0.5px;
}
#sb-app .sb-result-sub {
  font-size: 13px;
  color: #475569;
  margin-bottom: 14px;
}
#sb-app .sb-result-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
  margin-top: 10px;
}
#sb-app .sb-result-table th {
  background: #bae6fd;
  color: #0369a1;
  padding: 7px 10px;
  text-align: left;
  font-weight: 700;
  border-radius: 0;
}
#sb-app .sb-result-table th:first-child { border-radius: 6px 0 0 0; }
#sb-app .sb-result-table th:last-child { border-radius: 0 6px 0 0; }
#sb-app .sb-result-table td {
  padding: 7px 10px;
  border-bottom: 1px solid #e0f2fe;
  color: #1e293b;
}
#sb-app .sb-result-table tr:last-child td {
  border-bottom: none;
}
#sb-app .sb-result-table tr:nth-child(even) td {
  background: #f0f9ff;
}
#sb-app .sb-badge {
  display: inline-block;
  padding: 2px 8px;
  border-radius: 99px;
  font-size: 11px;
  font-weight: 700;
  background: #fef3c7;
  color: #92400e;
  margin-left: 6px;
  vertical-align: middle;
}
#sb-app .sb-error {
  display: none;
  background: #fee2e2;
  border: 1.5px solid #fca5a5;
  border-radius: 8px;
  padding: 10px 14px;
  color: #b91c1c;
  font-size: 13px;
  font-weight: 600;
  margin-top: 10px;
}
#sb-app .sb-error.visible {
  display: block;
}
@media (max-width: 480px) {
  #sb-app .sb-row > div { flex: 1 1 100%; }
  #sb-app .sb-result-main { font-size: 1.5rem; }
}
</style>

<h2>割り勘計算ツール</h2>

<div class="sb-card">
  <h2 style="margin-top:0;border-bottom:none;padding-bottom:0;font-size:1rem;">基本情報</h2>

  <div class="sb-row">
    <div>
      <label for="sb-total">合計金額（円）</label>
      <input type="number" id="sb-total" placeholder="例: 25000" min="0" step="1">
    </div>
    <div>
      <label for="sb-people">人数</label>
      <input type="number" id="sb-people" placeholder="例: 5" min="1" step="1" value="4">
    </div>
  </div>

  <div class="sb-row-full">
    <label for="sb-service">サービス料（%、任意）</label>
    <input type="number" id="sb-service" placeholder="例: 10（サービス料10%の場合）" min="0" max="100" step="0.1">
  </div>
</div>

<div class="sb-card">
  <h2 style="margin-top:0;border-bottom:none;padding-bottom:0;font-size:1rem;">割り勘モード</h2>
  <div class="sb-mode-tabs">
    <div class="sb-tab-btn active" id="tab-equal" onclick="sbSetMode('equal')">均等割り</div>
    <div class="sb-tab-btn" id="tab-custom" onclick="sbSetMode('custom')">傾斜配分（個別指定）</div>
  </div>

  <div id="sb-mode-equal">
    <p style="font-size:13px;color:#64748b;margin:0;">全員が同じ金額を負担します。</p>
  </div>

  <div id="sb-mode-custom" style="display:none;">
    <p style="font-size:13px;color:#64748b;margin:0 0 10px;">名前と負担割合（または金額）を個別に指定できます。割合を入力してください（合計100にならない場合は按分します）。</p>
    <div class="sb-members" id="sb-members-list"></div>
    <button class="sb-add-btn" onclick="sbAddMember()">＋ メンバーを追加</button>
    <p style="font-size:12px;color:#94a3b8;margin:8px 0 0;">※ 割合を空欄にしたメンバーは均等按分の対象になります。</p>
  </div>
</div>

<div class="sb-card">
  <h2 style="margin-top:0;border-bottom:none;padding-bottom:0;font-size:1rem;">端数処理</h2>
  <div class="sb-row">
    <div>
      <label for="sb-round-method">端数処理方法</label>
      <select id="sb-round-method">
        <option value="ceil">切り上げ</option>
        <option value="floor">切り捨て</option>
        <option value="round" selected>四捨五入</option>
      </select>
    </div>
    <div>
      <label for="sb-round-unit">単位</label>
      <select id="sb-round-unit">
        <option value="1">1円単位</option>
        <option value="10">10円単位</option>
        <option value="100" selected>100円単位</option>
        <option value="1000">1000円単位</option>
      </select>
    </div>
  </div>
  <label class="sb-checkbox-row">
    <input type="checkbox" id="sb-host-absorb" checked>
    幹事が端数を負担する（端数を差し引いた金額を幹事が払う）
  </label>
  <div id="sb-host-name-row" style="margin-top:6px;">
    <label for="sb-host-name" style="font-size:12px;">幹事の名前（任意）</label>
    <input type="text" id="sb-host-name" placeholder="幹事（省略可）" style="max-width:200px;">
  </div>
</div>

<button class="sb-calc-btn" onclick="sbCalculate()">割り勘を計算する</button>

<div class="sb-error" id="sb-error"></div>

<div class="sb-result" id="sb-result">
  <h3>計算結果</h3>
  <div id="sb-result-body"></div>
</div>

<script>
(function () {
  var sbMode = 'equal';
  var sbMembers = [];
  var memberIdCounter = 0;

  window.sbSetMode = function (mode) {
    sbMode = mode;
    document.getElementById('tab-equal').className = 'sb-tab-btn' + (mode === 'equal' ? ' active' : '');
    document.getElementById('tab-custom').className = 'sb-tab-btn' + (mode === 'custom' ? ' active' : '');
    document.getElementById('sb-mode-equal').style.display = mode === 'equal' ? '' : 'none';
    document.getElementById('sb-mode-custom').style.display = mode === 'custom' ? '' : 'none';

    if (mode === 'custom' && sbMembers.length === 0) {
      var people = parseInt(document.getElementById('sb-people').value, 10) || 4;
      for (var i = 0; i < Math.max(people, 2); i++) {
        sbAddMember();
      }
    }
  };

  window.sbAddMember = function () {
    var id = 'member-' + (memberIdCounter++);
    sbMembers.push(id);
    renderMembers();
  };

  window.sbRemoveMember = function (id) {
    sbMembers = sbMembers.filter(function (m) { return m !== id; });
    renderMembers();
  };

  function renderMembers() {
    var list = document.getElementById('sb-members-list');
    list.innerHTML = '';
    sbMembers.forEach(function (id, idx) {
      var row = document.createElement('div');
      row.className = 'sb-member-row';
      row.innerHTML =
        '<input type="text" id="' + id + '-name" placeholder="名前（例: 田中）" value="' + (getSavedValue(id + '-name') || '') + '">' +
        '<input type="number" id="' + id + '-ratio" placeholder="割合（例: 2）" min="0" step="0.1" value="' + (getSavedValue(id + '-ratio') || '') + '">' +
        '<button class="sb-remove-btn" onclick="sbRemoveMember(\'' + id + '\')" title="削除">&#x2715;</button>';
      list.appendChild(row);
    });
  }

  function getSavedValue(fieldId) {
    var el = document.getElementById(fieldId);
    return el ? el.value : '';
  }

  function roundTo(value, unit, method) {
    var inv = 1 / unit;
    if (method === 'ceil') return Math.ceil(value * inv) / inv;
    if (method === 'floor') return Math.floor(value * inv) / inv;
    return Math.round(value * inv) / inv;
  }

  function formatYen(n) {
    return '¥' + Math.round(n).toLocaleString('ja-JP') + '円';
  }

  window.sbCalculate = function () {
    var errorEl = document.getElementById('sb-error');
    var resultEl = document.getElementById('sb-result');
    errorEl.className = 'sb-error';
    resultEl.className = 'sb-result';

    var totalRaw = parseFloat(document.getElementById('sb-total').value);
    var servicePct = parseFloat(document.getElementById('sb-service').value) || 0;
    var people = parseInt(document.getElementById('sb-people').value, 10);
    var roundMethod = document.getElementById('sb-round-method').value;
    var roundUnit = parseInt(document.getElementById('sb-round-unit').value, 10);
    var hostAbsorb = document.getElementById('sb-host-absorb').checked;
    var hostName = document.getElementById('sb-host-name').value.trim() || '幹事';

    if (isNaN(totalRaw) || totalRaw <= 0) {
      errorEl.textContent = '合計金額を正しく入力してください。';
      errorEl.className = 'sb-error visible';
      return;
    }
    if (isNaN(people) || people < 1) {
      errorEl.textContent = '人数を1以上で入力してください。';
      errorEl.className = 'sb-error visible';
      return;
    }

    var totalWithService = totalRaw * (1 + servicePct / 100);

    var rows = [];

    if (sbMode === 'equal') {
      var baseAmount = totalWithService / people;
      var rounded = roundTo(baseAmount, roundUnit, roundMethod);
      var sumRounded = rounded * people;
      var remainder = totalWithService - sumRounded;

      for (var i = 0; i < people; i++) {
        var label = (i === 0 && hostAbsorb) ? hostName : (i + 1) + '人目';
        var amt = rounded;
        if (i === 0 && hostAbsorb) {
          amt = rounded + remainder;
        }
        rows.push({ name: label, amount: amt, note: (i === 0 && hostAbsorb && Math.abs(remainder) > 0) ? '端数 ' + (remainder >= 0 ? '+' : '') + Math.round(remainder) + '円含む' : '' });
      }
    } else {
      if (sbMembers.length === 0) {
        errorEl.textContent = 'メンバーを追加してください。';
        errorEl.className = 'sb-error visible';
        return;
      }

      var memberData = sbMembers.map(function (id) {
        var nameEl = document.getElementById(id + '-name');
        var ratioEl = document.getElementById(id + '-ratio');
        var name = (nameEl ? nameEl.value.trim() : '') || '名前未入力';
        var ratio = ratioEl ? parseFloat(ratioEl.value) : NaN;
        return { id: id, name: name, ratio: ratio };
      });

      var hasRatio = memberData.filter(function (m) { return !isNaN(m.ratio) && m.ratio > 0; });
      var noRatio = memberData.filter(function (m) { return isNaN(m.ratio) || m.ratio <= 0; });

      var totalRatio = hasRatio.reduce(function (s, m) { return s + m.ratio; }, 0);
      var equalShare = noRatio.length;

      if (totalRatio === 0 && equalShare === 0) {
        errorEl.textContent = '割合を入力してください。';
        errorEl.className = 'sb-error visible';
        return;
      }

      var reservedTotal = (totalRatio > 0 && equalShare > 0)
        ? totalWithService * (totalRatio / (totalRatio + equalShare))
        : (totalRatio > 0 ? totalWithService : 0);

      var equalTotal = totalWithService - reservedTotal;
      var equalPerPerson = equalShare > 0 ? equalTotal / equalShare : 0;

      var amounts = memberData.map(function (m) {
        if (!isNaN(m.ratio) && m.ratio > 0) {
          return { name: m.name, raw: (m.ratio / (totalRatio + equalShare)) * totalWithService };
        } else {
          return { name: m.name, raw: equalPerPerson };
        }
      });

      var rounded2 = amounts.map(function (a) {
        return { name: a.name, rounded: roundTo(a.raw, roundUnit, roundMethod), raw: a.raw };
      });
      var sumR = rounded2.reduce(function (s, a) { return s + a.rounded; }, 0);
      var rem = totalWithService - sumR;

      rounded2.forEach(function (a, idx) {
        var note = '';
        if (idx === 0 && hostAbsorb && Math.abs(rem) > 0) {
          a.rounded += rem;
          note = '端数 ' + (rem >= 0 ? '+' : '') + Math.round(rem) + '円含む';
        }
        rows.push({ name: a.name, amount: a.rounded, note: note });
      });
    }

    var bodyEl = document.getElementById('sb-result-body');
    var html = '';

    if (sbMode === 'equal') {
      var pp = roundTo(totalWithService / people, roundUnit, roundMethod);
      html += '<div class="sb-result-main">' + formatYen(pp) + ' <span style="font-size:1rem;font-weight:600;color:#0369a1;">/ 人</span></div>';
      html += '<div class="sb-result-sub">合計: ' + formatYen(totalWithService) + (servicePct > 0 ? '（サービス料 ' + servicePct + '% 込み）' : '') + ' ÷ ' + people + '人</div>';
    } else {
      html += '<div class="sb-result-main">' + formatYen(totalWithService) + ' <span style="font-size:1rem;font-weight:600;color:#0369a1;">合計</span></div>';
      html += '<div class="sb-result-sub">' + (servicePct > 0 ? 'サービス料 ' + servicePct + '% 込み ' : '') + '傾斜配分</div>';
    }

    html += '<table class="sb-result-table"><thead><tr><th>名前</th><th>負担金額</th><th>備考</th></tr></thead><tbody>';
    rows.forEach(function (r) {
      html += '<tr><td>' + escHtml(r.name) + '</td><td style="font-weight:700;color:#0284c7;">' + formatYen(r.amount) + '</td><td>';
      if (r.note) html += '<span class="sb-badge">' + escHtml(r.note) + '</span>';
      html += '</td></tr>';
    });
    html += '</tbody></table>';

    if (hostAbsorb && sbMode === 'equal') {
      var hostAmt = rows[0].amount;
      html += '<p style="font-size:12px;color:#64748b;margin:10px 0 0;">※ ' + escHtml(rows[0].name) + 'が端数を調整して <strong>' + formatYen(hostAmt) + '</strong> を負担します。</p>';
    }

    bodyEl.innerHTML = html;
    resultEl.className = 'sb-result visible';
    resultEl.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  };

  function escHtml(str) {
    return String(str).replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
  }

  document.getElementById('sb-host-absorb').addEventListener('change', function () {
    document.getElementById('sb-host-name-row').style.display = this.checked ? '' : 'none';
  });

  document.getElementById('sb-people').addEventListener('change', function () {
    if (sbMode === 'custom') {
      var target = parseInt(this.value, 10) || 2;
      while (sbMembers.length < target) sbAddMember();
      renderMembers();
    }
  });
})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の経費精算もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、交際費・会議費の経費精算もクラウドで簡単。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

---

> チップを計算 → [チップ計算ツール](/ja/tools/tip-calculator/)
> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-planner/)
> パーセントを計算 → [パーセント計算ツール](/ja/tools/percentage-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
