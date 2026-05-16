---
title: "時給・年収換算計算ツール | 給与を瞬時に変換"
date: 2026-05-16
draft: false
slug: "hourly-to-salary-calculator"
aliases:
  - "/tools/salary-to-hourly/"
  - "/tools/wage-calculator/"
description: "時給から年収、または年収から時給を瞬時に換算。週給・隔週・月給・年収の各単位で表示。残業代試算付きの無料計算ツール。"
categories:
  - "無料ツール"
tags:
  - "時給"
  - "年収計算"
  - "給与換算"
  - "給料"
  - "収入"
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/hourly-to-salary-calculator.png"
  alt: "時給・年収換算計算ツール | 給与を瞬時に変換"
  relative: false
---

*本記事にはアフィリエイトリンクが含まれています。*

# 時給・年収換算計算ツール

時給または年収を入力すると、**週給・隔週・月給・年収**の各単位での給与換算と、残業代の試算、そして少しの昇給が年収にどれだけ影響するかを瞬時に確認できます。

<style>
.hs-wrap {
  max-width: 720px;
  margin: 0 auto;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: #1e293b;
}
.hs-mode-toggle {
  display: flex;
  background: #f0fdf4;
  border: 2px solid #059669;
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 20px;
}
.hs-mode-btn {
  flex: 1;
  padding: 14px 10px;
  text-align: center;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  color: #065f46;
  transition: background 0.2s, color 0.2s;
  user-select: none;
}
.hs-mode-btn.active {
  background: #059669;
  color: #fff;
}
.hs-mode-btn:not(.active):hover {
  background: #d1fae5;
}
.hs-card {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 14px;
  padding: 28px;
  margin-bottom: 20px;
  box-shadow: 0 2px 8px rgba(5,150,105,0.07);
}
.hs-section-title {
  font-size: 15px;
  font-weight: 700;
  color: #059669;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin: 0 0 18px 0;
}
.hs-field {
  margin-bottom: 18px;
}
.hs-label {
  display: block;
  font-size: 14px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 8px;
}
.hs-input-wrap {
  position: relative;
  display: flex;
  align-items: center;
}
.hs-input-prefix {
  position: absolute;
  left: 12px;
  font-size: 16px;
  font-weight: 700;
  color: #059669;
  pointer-events: none;
}
.hs-input {
  width: 100%;
  padding: 11px 14px 11px 28px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 700;
  color: #1e293b;
  box-sizing: border-box;
  transition: border-color 0.2s;
}
.hs-input:focus {
  outline: none;
  border-color: #059669;
}
.hs-range-row {
  display: flex;
  align-items: center;
  gap: 12px;
}
.hs-range-row input[type="range"] {
  flex: 1;
  accent-color: #059669;
  height: 6px;
  cursor: pointer;
}
.hs-range-val {
  min-width: 54px;
  text-align: right;
  font-weight: 700;
  font-size: 15px;
  color: #059669;
}
.hs-results-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 6px;
}
.hs-results-grid-3 {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 14px;
  margin-bottom: 14px;
}
.hs-result-box {
  background: #f0fdf4;
  border: 2px solid #059669;
  border-radius: 12px;
  padding: 18px 14px;
  text-align: center;
}
.hs-result-box.primary {
  background: #059669;
  color: #fff;
}
.hs-result-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #065f46;
  margin-bottom: 6px;
}
.hs-result-box.primary .hs-result-label {
  color: #a7f3d0;
}
.hs-result-value {
  font-size: 26px;
  font-weight: 800;
  color: #059669;
  line-height: 1.1;
}
.hs-result-box.primary .hs-result-value {
  color: #fff;
  font-size: 32px;
}
.hs-result-sub {
  font-size: 12px;
  color: #6ee7b7;
  margin-top: 4px;
}
.hs-result-sub-dark {
  font-size: 12px;
  color: #6b7280;
  margin-top: 4px;
}
.hs-stat-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #e2e8f0;
  font-size: 14px;
}
.hs-stat-row:last-child { border-bottom: none; }
.hs-stat-label { color: #64748b; }
.hs-stat-val { font-weight: 700; color: #059669; }
.hs-ot-box {
  background: #fff7ed;
  border: 2px solid #f59e0b;
  border-radius: 12px;
  padding: 18px;
}
.hs-ot-title {
  font-size: 14px;
  font-weight: 700;
  color: #92400e;
  margin-bottom: 12px;
}
.hs-ot-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.hs-ot-item {
  background: #fef3c7;
  border-radius: 8px;
  padding: 12px;
  text-align: center;
}
.hs-ot-item-label {
  font-size: 11px;
  font-weight: 600;
  color: #78350f;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 4px;
}
.hs-ot-item-val {
  font-size: 20px;
  font-weight: 800;
  color: #d97706;
}
.hs-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}
.hs-table th {
  background: #059669;
  color: #fff;
  padding: 10px 12px;
  text-align: left;
  font-weight: 600;
}
.hs-table th:not(:first-child) {
  text-align: right;
}
.hs-table td {
  padding: 10px 12px;
  border-bottom: 1px solid #e2e8f0;
}
.hs-table td:not(:first-child) {
  text-align: right;
}
.hs-table tr.hs-current td {
  background: #f0fdf4;
  font-weight: 700;
  color: #059669;
}
.hs-table tr:hover td { background: #f8fafc; }
.hs-qr-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
.hs-qr-box {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 14px 10px;
  text-align: center;
  transition: border-color 0.2s, background 0.2s;
  cursor: pointer;
}
.hs-qr-box:hover {
  background: #f0fdf4;
  border-color: #059669;
}
.hs-qr-rate {
  font-size: 18px;
  font-weight: 800;
  color: #059669;
  margin-bottom: 4px;
}
.hs-qr-annual {
  font-size: 12px;
  font-weight: 700;
  color: #1e293b;
}
.hs-qr-label {
  font-size: 11px;
  color: #94a3b8;
  margin-top: 2px;
}
.hs-hidden { display: none; }
@media (max-width: 560px) {
  .hs-results-grid { grid-template-columns: 1fr; }
  .hs-results-grid-3 { grid-template-columns: 1fr 1fr; }
  .hs-ot-grid { grid-template-columns: 1fr; }
  .hs-qr-grid { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 380px) {
  .hs-results-grid-3 { grid-template-columns: 1fr; }
  .hs-qr-grid { grid-template-columns: 1fr; }
}
</style>

<div class="hs-wrap">

<!-- モード切替 -->
<div class="hs-mode-toggle">
  <div class="hs-mode-btn active" id="hsModeHtoS" onclick="hsSetMode('hourly')">時給 &rarr; 年収</div>
  <div class="hs-mode-btn" id="hsModeStoH" onclick="hsSetMode('salary')">年収 &rarr; 時給</div>
</div>

<!-- 入力エリア -->
<div class="hs-card">
  <div class="hs-section-title" id="hsInputTitle">あなたの時給</div>

  <!-- 時給入力 -->
  <div class="hs-field" id="hsHourlyField">
    <label class="hs-label" for="hsHourlyInput">時給</label>
    <div class="hs-input-wrap">
      <span class="hs-input-prefix">$</span>
      <input type="number" id="hsHourlyInput" class="hs-input" value="20" min="1" max="10000" step="0.25" oninput="hsCalc()">
    </div>
  </div>

  <!-- 年収入力 -->
  <div class="hs-field hs-hidden" id="hsSalaryField">
    <label class="hs-label" for="hsSalaryInput">年収</label>
    <div class="hs-input-wrap">
      <span class="hs-input-prefix">$</span>
      <input type="number" id="hsSalaryInput" class="hs-input" value="52000" min="1000" max="10000000" step="1000" oninput="hsCalc()">
    </div>
  </div>

  <!-- 週あたり時間 -->
  <div class="hs-field">
    <label class="hs-label">週あたり勤務時間: <span id="hsHoursVal" style="color:#059669;">40</span> 時間</label>
    <div class="hs-range-row">
      <span style="font-size:12px;color:#94a3b8;">1</span>
      <input type="range" id="hsHoursRange" min="1" max="60" step="1" value="40" oninput="hsCalc()">
      <span style="font-size:12px;color:#94a3b8;">60</span>
    </div>
  </div>

  <!-- 年間稼働週数 -->
  <div class="hs-field" style="margin-bottom:0;">
    <label class="hs-label">年間稼働週数: <span id="hsWeeksVal" style="color:#059669;">52</span> 週</label>
    <div class="hs-range-row">
      <span style="font-size:12px;color:#94a3b8;">48</span>
      <input type="range" id="hsWeeksRange" min="48" max="52" step="1" value="52" oninput="hsCalc()">
      <span style="font-size:12px;color:#94a3b8;">52</span>
    </div>
    <div style="font-size:12px;color:#94a3b8;margin-top:6px;">有給休暇・祝日・無給休暇を差し引いてください</div>
  </div>
</div>

<!-- 計算結果 -->
<div class="hs-card">
  <div class="hs-section-title">給与内訳</div>
  <div id="hsResultsGrid"></div>
</div>

<!-- 残業代パネル -->
<div class="hs-card" id="hsOvertimeCard" style="display:none;">
  <div class="hs-section-title">残業代内訳</div>
  <div style="font-size:13px;color:#64748b;margin-bottom:14px;">週40時間を超えています。40時間超の時間は通常の1.5倍の残業単価で計算されます。</div>
  <div class="hs-ot-box">
    <div class="hs-ot-title" id="hsOtTitle"></div>
    <div class="hs-ot-grid" id="hsOtGrid"></div>
  </div>
</div>

<!-- 比較表：時給が上がると年収はどう変わる？ -->
<div class="hs-card">
  <div class="hs-section-title">昇給による年収への影響</div>
  <div style="font-size:13px;color:#64748b;margin-bottom:14px;">時給の小さな変化が年収にどれだけ影響するかを確認できます。現在の時給をハイライト表示しています。</div>
  <div style="overflow-x:auto;">
    <table class="hs-table">
      <thead>
        <tr>
          <th>時給</th>
          <th>週給</th>
          <th>月給</th>
          <th>年収</th>
          <th>現在との差</th>
        </tr>
      </thead>
      <tbody id="hsCompBody"></tbody>
    </table>
  </div>
</div>

<!-- 時給早見表 -->
<div class="hs-card">
  <div class="hs-section-title">主な時給と年収の早見表</div>
  <div style="font-size:13px;color:#64748b;margin-bottom:14px;">クリックすると計算ツールに反映されます。</div>
  <div class="hs-qr-grid" id="hsQrGrid"></div>
</div>

</div><!-- end hs-wrap -->

<script>
var hsMode = 'hourly';

function hsSetMode(mode) {
  hsMode = mode;
  if (mode === 'hourly') {
    document.getElementById('hsModeHtoS').classList.add('active');
    document.getElementById('hsModeStoH').classList.remove('active');
    document.getElementById('hsHourlyField').classList.remove('hs-hidden');
    document.getElementById('hsSalaryField').classList.add('hs-hidden');
    document.getElementById('hsInputTitle').textContent = 'あなたの時給';
  } else {
    document.getElementById('hsModeStoH').classList.add('active');
    document.getElementById('hsModeHtoS').classList.remove('active');
    document.getElementById('hsSalaryField').classList.remove('hs-hidden');
    document.getElementById('hsHourlyField').classList.add('hs-hidden');
    document.getElementById('hsInputTitle').textContent = 'あなたの年収';
  }
  hsCalc();
}

function fmtMoney(n) {
  if (n >= 1000) {
    return '$' + Math.round(n).toLocaleString('en-US');
  }
  return '$' + n.toFixed(2);
}

function fmtDelta(n) {
  if (n === 0) return '—';
  return (n > 0 ? '+' : '') + '$' + Math.round(Math.abs(n)).toLocaleString('en-US');
}

function fmtRate(n) {
  return '$' + n.toFixed(2) + '/時';
}

function hsGetValues() {
  var hours = parseInt(document.getElementById('hsHoursRange').value) || 40;
  var weeks = parseInt(document.getElementById('hsWeeksRange').value) || 52;
  var hourly, annual;
  if (hsMode === 'hourly') {
    hourly = parseFloat(document.getElementById('hsHourlyInput').value) || 0;
    annual = hourly * hours * weeks;
  } else {
    annual = parseFloat(document.getElementById('hsSalaryInput').value) || 0;
    hourly = (hours > 0 && weeks > 0) ? annual / (hours * weeks) : 0;
  }
  return { hourly: hourly, hours: hours, weeks: weeks, annual: annual };
}

function hsCalc() {
  var v = hsGetValues();
  var hours = v.hours;
  var weeks = v.weeks;
  var hourly = v.hourly;
  var annual = v.annual;

  document.getElementById('hsHoursVal').textContent = hours;
  document.getElementById('hsWeeksVal').textContent = weeks;

  var weekly = hourly * hours;
  var biweekly = weekly * 2;
  var monthly = annual / 12;
  var daily = hourly * 8;

  var rg = document.getElementById('hsResultsGrid');
  var html = '';

  if (hsMode === 'hourly') {
    html += '<div class="hs-results-grid">';
    html += hsResultBox('週給', fmtMoney(weekly), hours + ' 時間 &times; ' + weeks + ' 週/年', false);
    html += hsResultBox('隔週給', fmtMoney(biweekly), '2週間ごと', false);
    html += '</div>';
    html += '<div class="hs-results-grid">';
    html += hsResultBox('月給', fmtMoney(monthly), '年収 &divide; 12', false);
    html += hsResultBox('年収', fmtMoney(annual), hourly.toFixed(2) + '/時 &times; ' + (hours * weeks) + ' 時間', true);
    html += '</div>';
  } else {
    html += '<div class="hs-results-grid">';
    html += hsResultBox('時給', fmtRate(hourly), annual > 0 ? fmtMoney(annual) + '/年 &divide; ' + (hours * weeks) + ' 時間' : '—', true);
    html += hsResultBox('日当', fmtMoney(daily), '8時間 &times; ' + fmtRate(hourly), false);
    html += '</div>';
    html += '<div class="hs-results-grid-3">';
    html += hsResultBox('週給', fmtMoney(weekly), hours + ' 時間/週', false);
    html += hsResultBox('隔週給', fmtMoney(biweekly), '2週間ごと', false);
    html += hsResultBox('月給', fmtMoney(monthly), '年収 &divide; 12', false);
    html += '</div>';
  }
  rg.innerHTML = html;

  var otCard = document.getElementById('hsOvertimeCard');
  if (hours > 40) {
    otCard.style.display = 'block';
    var regularHours = 40;
    var otHours = hours - 40;
    var otRate = hourly * 1.5;
    var regularWeeklyPay = regularHours * hourly;
    var otWeeklyPay = otHours * otRate;
    var totalWeeklyWithOt = regularWeeklyPay + otWeeklyPay;
    var totalAnnualWithOt = totalWeeklyWithOt * weeks;
    var otAnnualBonus = totalAnnualWithOt - (hourly * 40 * weeks);

    document.getElementById('hsOtTitle').innerHTML =
      '週' + hours + '時間勤務：通常' + regularHours + '時間 + 残業' + otHours + '時間（' + fmtRate(otRate) + '、1.5倍）';

    var og = document.getElementById('hsOtGrid');
    og.innerHTML =
      '<div class="hs-ot-item">' +
        '<div class="hs-ot-item-label">残業込み週給</div>' +
        '<div class="hs-ot-item-val">' + fmtMoney(totalWeeklyWithOt) + '</div>' +
      '</div>' +
      '<div class="hs-ot-item">' +
        '<div class="hs-ot-item-label">残業込み年収</div>' +
        '<div class="hs-ot-item-val">' + fmtMoney(totalAnnualWithOt) + '</div>' +
      '</div>' +
      '<div class="hs-ot-item">' +
        '<div class="hs-ot-item-label">週あたり残業時間</div>' +
        '<div class="hs-ot-item-val">' + otHours + ' 時間</div>' +
      '</div>' +
      '<div class="hs-ot-item">' +
        '<div class="hs-ot-item-label">残業による年収増</div>' +
        '<div class="hs-ot-item-val">+' + fmtMoney(otAnnualBonus) + '</div>' +
      '</div>';
  } else {
    otCard.style.display = 'none';
  }

  var baseHourly = hourly;
  var increments = [-2, -1, 0, 1, 2, 5];
  var cb = document.getElementById('hsCompBody');
  var ch = '';
  for (var i = 0; i < increments.length; i++) {
    var r = baseHourly + increments[i];
    if (r < 0) continue;
    var isCurrent = increments[i] === 0;
    var rowAnnual = r * hours * weeks;
    var rowWeekly = r * hours;
    var rowMonthly = rowAnnual / 12;
    var delta = rowAnnual - annual;
    var hlClass = isCurrent ? ' class="hs-current"' : '';
    var rateLabel = isCurrent ? fmtRate(r) + ' <strong>（あなた）</strong>' : fmtRate(r);
    var deltaStr = isCurrent ? '—' : fmtDelta(delta) + '/年';
    ch += '<tr' + hlClass + '>' +
      '<td>' + rateLabel + '</td>' +
      '<td>' + fmtMoney(rowWeekly) + '</td>' +
      '<td>' + fmtMoney(rowMonthly) + '</td>' +
      '<td>' + fmtMoney(rowAnnual) + '</td>' +
      '<td style="color:' + (delta > 0 ? '#059669' : delta < 0 ? '#dc2626' : '#64748b') + ';font-weight:700;">' + deltaStr + '</td>' +
    '</tr>';
  }
  cb.innerHTML = ch;

  var qrRates = [15, 20, 25, 30, 40, 50];
  var qg = document.getElementById('hsQrGrid');
  var qh = '';
  for (var j = 0; j < qrRates.length; j++) {
    var qr = qrRates[j];
    var qAnnual = qr * hours * weeks;
    qh += '<div class="hs-qr-box" onclick="hsSetRate(' + qr + ')">' +
      '<div class="hs-qr-rate">' + fmtRate(qr) + '</div>' +
      '<div class="hs-qr-annual">' + fmtMoney(qAnnual) + '/年</div>' +
      '<div class="hs-qr-label">' + hours + ' 時間 &times; ' + weeks + ' 週</div>' +
    '</div>';
  }
  qg.innerHTML = qh;
}

function hsResultBox(label, value, sub, isPrimary) {
  var cls = isPrimary ? 'hs-result-box primary' : 'hs-result-box';
  var subCls = isPrimary ? 'hs-result-sub' : 'hs-result-sub-dark';
  return '<div class="' + cls + '">' +
    '<div class="hs-result-label">' + label + '</div>' +
    '<div class="hs-result-value">' + value + '</div>' +
    '<div class="' + subCls + '">' + sub + '</div>' +
  '</div>';
}

function hsSetRate(rate) {
  hsMode = 'hourly';
  document.getElementById('hsModeHtoS').classList.add('active');
  document.getElementById('hsModeStoH').classList.remove('active');
  document.getElementById('hsHourlyField').classList.remove('hs-hidden');
  document.getElementById('hsSalaryField').classList.add('hs-hidden');
  document.getElementById('hsInputTitle').textContent = 'あなたの時給';
  document.getElementById('hsHourlyInput').value = rate;
  hsCalc();
}

document.addEventListener('DOMContentLoaded', function() { hsCalc(); });
hsCalc();
</script>

---

## 時給交渉で昇給を勝ち取る方法

### 1. 感覚ではなく市場データで交渉する

交渉の前に、同じ職種・地域・業界で実際にどれだけの報酬が支払われているかを調べましょう。厚生労働省の賃金統計、求人サイトの給与データ、業界団体の調査などを活用します。「なんとなく少ない気がする」ではなく、複数のデータソースに基づく具体的な数字を持ち込むことが説得力を生みます。

### 2. タイミングを戦略的に選ぶ

交渉に最適なタイミングは、大きな成果を出した直後です。重要プロジェクトの完了・新規顧客の獲得・好評価の受領直後が狙い目です。予算削減期・リストラ期・組織再編期は避けましょう。年次評価制度がある場合は、上司が予算折衝できるよう2〜3か月前から準備を始めてください。

### 3. 自分の貢献を金額で示す

上司が昇給を承認できるのは、そのコストを社内で正当化できる場合です。自分の仕事を売上への貢献・コスト削減・時間短縮の観点から数値化して示しましょう。「週次レポート作業を自動化し、チームの週6時間分（換算約○万円/年）の工数を削減しました」という形で示すと、承認を得やすくなります。

### 4. 時給だけでなくトータルパッケージで交渉する

時給アップが難しい場合は、総報酬の視点に切り替えましょう。在宅勤務日数・有給休暇の追加・入社一時金・成果連動ボーナス・研修費用補助・90日後の再評価保証など、すべてに実質的な金銭価値があります。通勤費用を節約できる柔軟な勤務形態は、それだけで実質的な時給上昇に相当します。

---

## 関連ツール

> フリーランスの適正時給を計算する &rarr; [フリーランス単価計算ツール](/tools/freelance-rate-calculator/)

> ローン返済を計算する &rarr; [ローン返済計算ツール](/tools/loan-repayment-calculator/)

> 月次予算を立てる &rarr; [予算プランナー](/tools/budget-planner/)

---

*免責事項：本ツールは参考・教育目的の概算を提供するものであり、税務・法務・財務アドバイスを構成するものではありません。残業規定は法域・雇用形態によって異なります。詳細は専門家にご相談ください。*

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)
