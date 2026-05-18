---
title: "年齢計算ツール - 生年月日から正確な年齢を計算"
date: 2026-01-17
description: "生年月日から正確な年齢を年・月・日・時間で計算。次の誕生日までの日数、干支、星座、和暦も表示。無料のオンライン年齢計算ツール。"
categories: ["無料ツール"]
tags: ["年齢計算", "誕生日", "日数計算", "干支", "和暦"]
slug: "age-calculator"
aliases: ["/ja/tools/age-calculator/", "/ja/tools/age-calculator/"]
cover:
  image: "/images/covers/age-calculator-ja.png"
  alt: "年齢計算ツール"
ShowToc: false
---

<style>
  #age-app {
    font-family: 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', sans-serif;
    max-width: 720px;
    margin: 0 auto;
    padding: 16px;
    color: #1c1917;
  }
  #age-app * { box-sizing: border-box; }

  /* タブ切り替え */
  .age-tabs {
    display: flex;
    gap: 8px;
    margin-bottom: 20px;
  }
  .age-tab-btn {
    flex: 1;
    padding: 10px 8px;
    border: 2px solid #f59e0b;
    background: #fff;
    color: #b45309;
    font-size: 14px;
    font-weight: 700;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.2s, color 0.2s;
  }
  .age-tab-btn.active {
    background: #f59e0b;
    color: #fff;
  }

  /* 入力セクション */
  .age-input-section {
    background: #fffbeb;
    border: 1.5px solid #fde68a;
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 20px;
  }
  .age-input-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    align-items: flex-end;
  }
  .age-field {
    display: flex;
    flex-direction: column;
    gap: 6px;
    flex: 1;
    min-width: 160px;
  }
  .age-field label {
    font-size: 13px;
    font-weight: 700;
    color: #92400e;
  }
  .age-field input[type="date"] {
    padding: 10px 12px;
    border: 1.5px solid #fcd34d;
    border-radius: 8px;
    font-size: 15px;
    background: #fff;
    color: #1c1917;
    width: 100%;
    outline: none;
    transition: border-color 0.2s;
  }
  .age-field input[type="date"]:focus {
    border-color: #f59e0b;
    box-shadow: 0 0 0 3px rgba(245,158,11,0.15);
  }
  .age-calc-btn {
    padding: 10px 28px;
    background: #f59e0b;
    color: #fff;
    border: none;
    border-radius: 8px;
    font-size: 15px;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s;
    white-space: nowrap;
    align-self: flex-end;
  }
  .age-calc-btn:hover { background: #d97706; }
  .age-reset-btn {
    padding: 10px 16px;
    background: #fff;
    color: #92400e;
    border: 1.5px solid #fcd34d;
    border-radius: 8px;
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s;
    white-space: nowrap;
    align-self: flex-end;
  }
  .age-reset-btn:hover { background: #fef3c7; }

  /* 結果エリア */
  .age-results { display: none; }
  .age-results.visible { display: block; }

  /* メイン年齢カード */
  .age-main-card {
    background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
    border-radius: 14px;
    padding: 24px;
    text-align: center;
    color: #fff;
    margin-bottom: 16px;
    box-shadow: 0 4px 16px rgba(245,158,11,0.3);
  }
  .age-main-label {
    font-size: 13px;
    opacity: 0.85;
    margin-bottom: 6px;
    font-weight: 600;
    letter-spacing: 0.05em;
  }
  .age-main-value {
    font-size: 42px;
    font-weight: 900;
    line-height: 1;
    margin-bottom: 4px;
    letter-spacing: -1px;
  }
  .age-main-detail {
    font-size: 16px;
    opacity: 0.9;
    font-weight: 600;
  }

  /* 統計グリッド */
  .age-stats-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
    margin-bottom: 16px;
  }
  @media (min-width: 480px) {
    .age-stats-grid { grid-template-columns: repeat(4, 1fr); }
  }
  .age-stat-card {
    background: #fff;
    border: 1.5px solid #fde68a;
    border-radius: 10px;
    padding: 14px 10px;
    text-align: center;
  }
  .age-stat-label {
    font-size: 11px;
    color: #92400e;
    font-weight: 700;
    margin-bottom: 6px;
    letter-spacing: 0.03em;
  }
  .age-stat-value {
    font-size: 18px;
    font-weight: 800;
    color: #b45309;
    line-height: 1;
  }
  .age-stat-unit {
    font-size: 11px;
    color: #78716c;
    margin-top: 2px;
  }

  /* 情報カード */
  .age-info-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
    margin-bottom: 16px;
  }
  @media (min-width: 560px) {
    .age-info-grid { grid-template-columns: repeat(3, 1fr); }
  }
  .age-info-card {
    background: #fff;
    border: 1.5px solid #fde68a;
    border-radius: 10px;
    padding: 14px 12px;
    text-align: center;
  }
  .age-info-icon {
    font-size: 22px;
    margin-bottom: 4px;
  }
  .age-info-label {
    font-size: 11px;
    color: #92400e;
    font-weight: 700;
    margin-bottom: 4px;
  }
  .age-info-value {
    font-size: 15px;
    font-weight: 800;
    color: #1c1917;
  }
  .age-info-sub {
    font-size: 11px;
    color: #78716c;
    margin-top: 2px;
  }

  /* 誕生日カウントダウン */
  .age-countdown-card {
    background: #fff7ed;
    border: 1.5px solid #fed7aa;
    border-radius: 10px;
    padding: 16px;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .age-countdown-icon { font-size: 28px; }
  .age-countdown-text { flex: 1; }
  .age-countdown-title {
    font-size: 12px;
    font-weight: 700;
    color: #c2410c;
    margin-bottom: 3px;
  }
  .age-countdown-value {
    font-size: 20px;
    font-weight: 900;
    color: #ea580c;
  }
  .age-countdown-date {
    font-size: 12px;
    color: #78716c;
    margin-top: 2px;
  }

  /* 世代ラベル */
  .age-generation-card {
    background: #fff;
    border: 1.5px solid #fde68a;
    border-radius: 10px;
    padding: 14px 16px;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .age-gen-badge {
    background: #f59e0b;
    color: #fff;
    font-size: 13px;
    font-weight: 800;
    padding: 4px 12px;
    border-radius: 20px;
    white-space: nowrap;
  }
  .age-gen-desc {
    font-size: 13px;
    color: #57534e;
    line-height: 1.5;
  }

  /* マイルストーン */
  .age-milestone-section {
    background: #fff;
    border: 1.5px solid #fde68a;
    border-radius: 10px;
    padding: 16px;
    margin-bottom: 16px;
  }
  .age-milestone-title {
    font-size: 13px;
    font-weight: 800;
    color: #92400e;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .age-milestone-list {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .age-milestone-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 8px 10px;
    border-radius: 8px;
    font-size: 13px;
  }
  .age-milestone-item.past {
    background: #f5f5f4;
    color: #78716c;
  }
  .age-milestone-item.future {
    background: #fffbeb;
    border: 1px solid #fde68a;
    color: #1c1917;
  }
  .age-milestone-item.today {
    background: #fef3c7;
    border: 1.5px solid #f59e0b;
    color: #92400e;
    font-weight: 700;
  }
  .age-milestone-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .past .age-milestone-dot { background: #a8a29e; }
  .future .age-milestone-dot { background: #f59e0b; }
  .today .age-milestone-dot { background: #ea580c; }
  .age-milestone-name { flex: 1; font-weight: 600; }
  .age-milestone-date { font-size: 12px; color: #78716c; }
  .age-milestone-remain {
    font-size: 12px;
    font-weight: 700;
    color: #d97706;
  }

  /* 日数計算モード */
  .age-diff-result-card {
    background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
    border-radius: 14px;
    padding: 24px;
    text-align: center;
    color: #fff;
    margin-bottom: 16px;
    box-shadow: 0 4px 16px rgba(245,158,11,0.3);
  }
  .age-diff-sub-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
    margin-bottom: 16px;
  }
  @media (min-width: 480px) {
    .age-diff-sub-grid { grid-template-columns: repeat(4, 1fr); }
  }

  /* エラーメッセージ */
  .age-error {
    background: #fef2f2;
    border: 1.5px solid #fecaca;
    color: #dc2626;
    border-radius: 8px;
    padding: 12px 16px;
    font-size: 14px;
    font-weight: 600;
    margin-bottom: 12px;
    display: none;
  }
  .age-error.visible { display: block; }

  /* 区切り線 */
  .age-divider {
    border: none;
    border-top: 1.5px solid #fde68a;
    margin: 20px 0;
  }
</style>

<div id="age-app">

  <!-- タブ -->
  <div class="age-tabs">
    <button class="age-tab-btn active" id="tab-age" onclick="ageSwitchTab('age')">年齢計算</button>
    <button class="age-tab-btn" id="tab-diff" onclick="ageSwitchTab('diff')">日数計算</button>
  </div>

  <!-- 年齢計算モード -->
  <div id="mode-age">
    <div class="age-input-section">
      <div class="age-input-row">
        <div class="age-field">
          <label for="age-birth">生年月日</label>
          <input type="date" id="age-birth" max="2099-12-31">
        </div>
        <div class="age-field">
          <label for="age-base">基準日（デフォルト: 今日）</label>
          <input type="date" id="age-base" max="2099-12-31">
        </div>
        <button class="age-calc-btn" onclick="ageCalculate()">計算する</button>
        <button class="age-reset-btn" onclick="ageReset()">リセット</button>
      </div>
    </div>
    <div class="age-error" id="age-error"></div>
    <div class="age-results" id="age-results">
      <!-- メイン年齢 -->
      <div class="age-main-card">
        <div class="age-main-label">満年齢</div>
        <div class="age-main-value" id="res-age-years"></div>
        <div class="age-main-detail" id="res-age-detail"></div>
      </div>
      <!-- 統計グリッド -->
      <div class="age-stats-grid">
        <div class="age-stat-card">
          <div class="age-stat-label">総月数</div>
          <div class="age-stat-value" id="res-total-months"></div>
          <div class="age-stat-unit">ヶ月</div>
        </div>
        <div class="age-stat-card">
          <div class="age-stat-label">総週数</div>
          <div class="age-stat-value" id="res-total-weeks"></div>
          <div class="age-stat-unit">週</div>
        </div>
        <div class="age-stat-card">
          <div class="age-stat-label">総日数</div>
          <div class="age-stat-value" id="res-total-days"></div>
          <div class="age-stat-unit">日</div>
        </div>
        <div class="age-stat-card">
          <div class="age-stat-label">総時間数</div>
          <div class="age-stat-value" id="res-total-hours"></div>
          <div class="age-stat-unit">時間（概算）</div>
        </div>
      </div>
      <!-- 情報グリッド -->
      <div class="age-info-grid">
        <div class="age-info-card">
          <div class="age-info-icon">📅</div>
          <div class="age-info-label">生まれた曜日</div>
          <div class="age-info-value" id="res-weekday"></div>
        </div>
        <div class="age-info-card">
          <div class="age-info-icon">🌟</div>
          <div class="age-info-label">星座</div>
          <div class="age-info-value" id="res-zodiac-west"></div>
        </div>
        <div class="age-info-card">
          <div class="age-info-icon">🐉</div>
          <div class="age-info-label">干支（十二支）</div>
          <div class="age-info-value" id="res-zodiac-east"></div>
        </div>
        <div class="age-info-card">
          <div class="age-info-icon">🏯</div>
          <div class="age-info-label">和暦（生年）</div>
          <div class="age-info-value" id="res-wareki"></div>
          <div class="age-info-sub" id="res-wareki-sub"></div>
        </div>
        <div class="age-info-card">
          <div class="age-info-icon">🏯</div>
          <div class="age-info-label">和暦（基準日）</div>
          <div class="age-info-value" id="res-wareki-base"></div>
          <div class="age-info-sub" id="res-wareki-base-sub"></div>
        </div>
        <div class="age-info-card">
          <div class="age-info-icon">🎂</div>
          <div class="age-info-label">誕生日の元号</div>
          <div class="age-info-value" id="res-wareki-era"></div>
        </div>
      </div>
      <!-- カウントダウン -->
      <div class="age-countdown-card">
        <div class="age-countdown-icon">🎉</div>
        <div class="age-countdown-text">
          <div class="age-countdown-title">次の誕生日まで</div>
          <div class="age-countdown-value" id="res-countdown"></div>
          <div class="age-countdown-date" id="res-next-birthday"></div>
        </div>
      </div>
      <!-- 世代ラベル -->
      <div class="age-generation-card">
        <div class="age-gen-badge" id="res-generation-badge"></div>
        <div class="age-gen-desc" id="res-generation-desc"></div>
      </div>
      <!-- マイルストーン -->
      <div class="age-milestone-section">
        <div class="age-milestone-title">&#127942; 人生のマイルストーン</div>
        <div class="age-milestone-list" id="res-milestones"></div>
      </div>
    </div>
  </div>

  <!-- 日数計算モード -->
  <div id="mode-diff" style="display:none;">
    <div class="age-input-section">
      <div class="age-input-row">
        <div class="age-field">
          <label for="diff-from">開始日</label>
          <input type="date" id="diff-from" max="2099-12-31">
        </div>
        <div class="age-field">
          <label for="diff-to">終了日</label>
          <input type="date" id="diff-to" max="2099-12-31">
        </div>
        <button class="age-calc-btn" onclick="diffCalculate()">計算する</button>
        <button class="age-reset-btn" onclick="diffReset()">リセット</button>
      </div>
    </div>
    <div class="age-error" id="diff-error"></div>
    <div class="age-results" id="diff-results">
      <div class="age-diff-result-card">
        <div class="age-main-label" id="diff-label">期間</div>
        <div class="age-main-value" id="diff-days-val"></div>
        <div class="age-main-detail">日間</div>
      </div>
      <div class="age-diff-sub-grid">
        <div class="age-stat-card">
          <div class="age-stat-label">週数</div>
          <div class="age-stat-value" id="diff-weeks-val"></div>
          <div class="age-stat-unit">週</div>
        </div>
        <div class="age-stat-card">
          <div class="age-stat-label">月数（概算）</div>
          <div class="age-stat-value" id="diff-months-val"></div>
          <div class="age-stat-unit">ヶ月</div>
        </div>
        <div class="age-stat-card">
          <div class="age-stat-label">年数（概算）</div>
          <div class="age-stat-value" id="diff-years-val"></div>
          <div class="age-stat-unit">年</div>
        </div>
        <div class="age-stat-card">
          <div class="age-stat-label">時間数</div>
          <div class="age-stat-value" id="diff-hours-val"></div>
          <div class="age-stat-unit">時間</div>
        </div>
      </div>
      <div class="age-info-grid" style="grid-template-columns: repeat(2,1fr);">
        <div class="age-info-card">
          <div class="age-info-icon">📅</div>
          <div class="age-info-label">開始日の曜日</div>
          <div class="age-info-value" id="diff-from-weekday"></div>
        </div>
        <div class="age-info-card">
          <div class="age-info-icon">📅</div>
          <div class="age-info-label">終了日の曜日</div>
          <div class="age-info-value" id="diff-to-weekday"></div>
        </div>
      </div>
    </div>
  </div>

</div>

<script>
(function() {
  // ---- 初期化 ----
  var todayStr = (function() {
    var d = new Date();
    var y = d.getFullYear();
    var m = String(d.getMonth() + 1).padStart(2, '0');
    var dd = String(d.getDate()).padStart(2, '0');
    return y + '-' + m + '-' + dd;
  })();
  document.getElementById('age-base').value = todayStr;
  document.getElementById('diff-to').value = todayStr;

  // ---- タブ切り替え ----
  window.ageSwitchTab = function(tab) {
    document.getElementById('tab-age').classList.toggle('active', tab === 'age');
    document.getElementById('tab-diff').classList.toggle('active', tab === 'diff');
    document.getElementById('mode-age').style.display = tab === 'age' ? '' : 'none';
    document.getElementById('mode-diff').style.display = tab === 'diff' ? '' : 'none';
  };

  // ---- 数値フォーマット ----
  function fmt(n) { return n.toLocaleString('ja-JP'); }

  // ---- 曜日 ----
  var WEEKDAYS = ['日曜日', '月曜日', '火曜日', '水曜日', '木曜日', '金曜日', '土曜日'];

  // ---- 星座 ----
  function getZodiacWest(month, day) {
    var signs = [
      [1,20,'山羊座'], [2,18,'水瓶座'], [3,20,'魚座'], [4,19,'牡羊座'],
      [5,20,'牡牛座'], [6,21,'双子座'], [7,22,'蟹座'], [8,22,'獅子座'],
      [9,22,'乙女座'], [10,23,'天秤座'], [11,21,'蠍座'], [12,21,'射手座'], [12,31,'山羊座']
    ];
    for (var i = 0; i < signs.length; i++) {
      if (month < signs[i][0] || (month === signs[i][0] && day <= signs[i][1])) {
        return signs[i][2];
      }
    }
    return '山羊座';
  }

  // ---- 十二支 ----
  var JUNISHI = ['子（ね）', '丑（うし）', '寅（とら）', '卯（う）', '辰（たつ）', '巳（み）',
                 '午（うま）', '未（ひつじ）', '申（さる）', '酉（とり）', '戌（いぬ）', '亥（い）'];
  function getJunishi(year) { return JUNISHI[(year - 4) % 12]; }

  // ---- 和暦 ----
  function getWareki(year, month, day) {
    var d = year * 10000 + month * 100 + day;
    if (d >= 20190501) return { era: '令和', year: year - 2018, reading: 'れいわ' };
    if (d >= 19890108) return { era: '平成', year: year - 1988, reading: 'へいせい' };
    if (d >= 19261225) return { era: '昭和', year: year - 1925, reading: 'しょうわ' };
    if (d >= 19120730) return { era: '大正', year: year - 1911, reading: 'たいしょう' };
    if (d >= 18680125) return { era: '明治', year: year - 1867, reading: 'めいじ' };
    return { era: '明治以前', year: year, reading: '' };
  }
  function warekiStr(w) {
    return w.era + (w.year === 1 ? '元' : w.year) + '年';
  }

  // ---- 世代ラベル ----
  function getGeneration(birthYear) {
    if (birthYear >= 2013) return { label: 'アルファ世代', desc: '2013年以降生まれ。デジタルネイティブの次世代。' };
    if (birthYear >= 1997) return { label: 'Z世代', desc: '1997〜2012年生まれ。スマホとSNSとともに育った世代。' };
    if (birthYear >= 1981) return { label: 'ミレニアル世代', desc: '1981〜1996年生まれ。インターネット普及期に青春を過ごした世代。' };
    if (birthYear >= 1975) return { label: 'ポスト団塊ジュニア', desc: '1975〜1980年生まれ。就職氷河期世代の前期にあたる。' };
    if (birthYear >= 1971) return { label: '氷河期世代（後期）', desc: '1971〜1974年生まれ。バブル崩壊後の厳しい就職戦線を経験。' };
    if (birthYear >= 1965) return { label: '氷河期世代', desc: '1965〜1970年生まれ。就職氷河期・ロストジェネレーションとも呼ばれる。' };
    if (birthYear >= 1955) return { label: 'バブル世代', desc: '1955〜1964年生まれ。バブル景気の恩恵を受けた世代。' };
    if (birthYear >= 1947) return { label: '団塊世代', desc: '1947〜1954年生まれ。戦後ベビーブームに生まれた世代。高度成長期を牽引。' };
    if (birthYear >= 1935) return { label: '焼け跡世代', desc: '1935〜1946年生まれ。戦争・復興期を経験した世代。' };
    return { label: '昭和初期以前', desc: birthYear + '年生まれ。激動の昭和を生き抜いた世代。' };
  }

  // ---- 年齢計算 ----
  function calcAge(birth, base) {
    var by = birth.getFullYear(), bm = birth.getMonth() + 1, bd = birth.getDate();
    var ty = base.getFullYear(), tm = base.getMonth() + 1, td = base.getDate();
    var years = ty - by;
    var months = tm - bm;
    var days = td - bd;
    if (days < 0) {
      var prevMonth = new Date(ty, base.getMonth(), 0);
      days += prevMonth.getDate();
      months -= 1;
    }
    if (months < 0) { months += 12; years -= 1; }
    return { years: years, months: months, days: days };
  }

  // ---- マイルストーン ----
  function getMilestones(birthDate, baseDate, totalDays) {
    var milestones = [
      { name: '1,000日', days: 1000 },
      { name: '3,000日', days: 3000 },
      { name: '5,000日', days: 5000 },
      { name: '7,000日', days: 7000 },
      { name: '10,000日', days: 10000 },
      { name: '20歳 成人', years: 20 },
      { name: '25歳', years: 25 },
      { name: '30歳', years: 30 },
      { name: '1万時間（416.7日）', days: 417 },
      { name: '40歳', years: 40 },
      { name: '50歳', years: 50 },
      { name: '60歳 還暦', years: 60 },
      { name: '70歳 古希', years: 70 },
      { name: '77歳 喜寿', years: 77 },
      { name: '80歳 傘寿', years: 80 },
      { name: '88歳 米寿', years: 88 },
      { name: '90歳 卒寿', years: 90 },
      { name: '99歳 白寿', years: 99 },
      { name: '100歳 百寿', years: 100 },
    ];
    var result = [];
    milestones.forEach(function(m) {
      var targetDate;
      if (m.years !== undefined) {
        targetDate = new Date(birthDate.getFullYear() + m.years, birthDate.getMonth(), birthDate.getDate());
      } else {
        targetDate = new Date(birthDate.getTime() + m.days * 86400000);
      }
      var diffMs = targetDate - baseDate;
      var diffDays = Math.round(diffMs / 86400000);
      var status = diffDays < 0 ? 'past' : (diffDays === 0 ? 'today' : 'future');
      var dateStr = targetDate.getFullYear() + '年' + (targetDate.getMonth()+1) + '月' + targetDate.getDate() + '日';
      var remainStr = '';
      if (status === 'future') remainStr = 'あと' + fmt(diffDays) + '日';
      else if (status === 'today') remainStr = '今日！';
      else remainStr = fmt(-diffDays) + '日前';
      result.push({ name: m.name, dateStr: dateStr, status: status, remainStr: remainStr });
    });
    result.sort(function(a, b) {
      var order = { past: 0, today: 1, future: 2 };
      return order[a.status] - order[b.status];
    });
    return result;
  }

  // ---- 年齢計算実行 ----
  window.ageCalculate = function() {
    var birthVal = document.getElementById('age-birth').value;
    var baseVal = document.getElementById('age-base').value;
    var errEl = document.getElementById('age-error');
    var resEl = document.getElementById('age-results');

    if (!birthVal) { errEl.textContent = '生年月日を入力してください。'; errEl.classList.add('visible'); resEl.classList.remove('visible'); return; }
    if (!baseVal) { baseVal = todayStr; document.getElementById('age-base').value = todayStr; }

    var birth = new Date(birthVal);
    var base = new Date(baseVal);

    if (isNaN(birth.getTime())) { errEl.textContent = '生年月日が正しくありません。'; errEl.classList.add('visible'); resEl.classList.remove('visible'); return; }
    if (birth > base) { errEl.textContent = '生年月日が基準日より後になっています。'; errEl.classList.add('visible'); resEl.classList.remove('visible'); return; }

    errEl.classList.remove('visible');

    var by = birth.getFullYear(), bm = birth.getMonth() + 1, bd = birth.getDate();
    var ty = base.getFullYear(), tm = base.getMonth() + 1, td = base.getDate();

    var age = calcAge(birth, base);
    var totalMs = base - birth;
    var totalDays = Math.floor(totalMs / 86400000);
    var totalWeeks = Math.floor(totalDays / 7);
    var totalMonths = age.years * 12 + age.months;
    var totalHours = totalDays * 24;

    // メイン
    document.getElementById('res-age-years').textContent = age.years + '歳';
    document.getElementById('res-age-detail').textContent = age.months + 'ヶ月 ' + age.days + '日';

    // 統計
    document.getElementById('res-total-months').textContent = fmt(totalMonths);
    document.getElementById('res-total-weeks').textContent = fmt(totalWeeks);
    document.getElementById('res-total-days').textContent = fmt(totalDays);
    document.getElementById('res-total-hours').textContent = fmt(totalHours);

    // 情報
    document.getElementById('res-weekday').textContent = WEEKDAYS[birth.getDay()];
    document.getElementById('res-zodiac-west').textContent = getZodiacWest(bm, bd);
    document.getElementById('res-zodiac-east').textContent = getJunishi(by);

    var warekiBirth = getWareki(by, bm, bd);
    document.getElementById('res-wareki').textContent = warekiStr(warekiBirth);
    document.getElementById('res-wareki-sub').textContent = warekiBirth.reading ? '（' + warekiBirth.reading + '）' : '';
    document.getElementById('res-wareki-era').textContent = warekiBirth.era;

    var warekiBase = getWareki(ty, tm, td);
    document.getElementById('res-wareki-base').textContent = warekiStr(warekiBase);
    document.getElementById('res-wareki-base-sub').textContent = warekiBase.reading ? '（' + warekiBase.reading + '）' : '';

    // カウントダウン
    var nextBirthday = new Date(ty, birth.getMonth(), bd);
    if (nextBirthday <= base) nextBirthday = new Date(ty + 1, birth.getMonth(), bd);
    var countDays = Math.round((nextBirthday - base) / 86400000);
    if (countDays === 0) {
      document.getElementById('res-countdown').textContent = '今日が誕生日！';
    } else {
      document.getElementById('res-countdown').textContent = fmt(countDays) + '日';
    }
    document.getElementById('res-next-birthday').textContent =
      nextBirthday.getFullYear() + '年' + (nextBirthday.getMonth()+1) + '月' + nextBirthday.getDate() + '日（' + WEEKDAYS[nextBirthday.getDay()] + '）';

    // 世代
    var gen = getGeneration(by);
    document.getElementById('res-generation-badge').textContent = gen.label;
    document.getElementById('res-generation-desc').textContent = gen.desc;

    // マイルストーン
    var milestones = getMilestones(birth, base, totalDays);
    var html = '';
    milestones.forEach(function(m) {
      html += '<div class="age-milestone-item ' + m.status + '">' +
        '<div class="age-milestone-dot"></div>' +
        '<div class="age-milestone-name">' + m.name + '</div>' +
        '<div class="age-milestone-date">' + m.dateStr + '</div>' +
        '<div class="age-milestone-remain">' + m.remainStr + '</div>' +
        '</div>';
    });
    document.getElementById('res-milestones').innerHTML = html;

    resEl.classList.add('visible');
  };

  window.ageReset = function() {
    document.getElementById('age-birth').value = '';
    document.getElementById('age-base').value = todayStr;
    document.getElementById('age-error').classList.remove('visible');
    document.getElementById('age-results').classList.remove('visible');
  };

  // ---- 日数計算実行 ----
  window.diffCalculate = function() {
    var fromVal = document.getElementById('diff-from').value;
    var toVal = document.getElementById('diff-to').value;
    var errEl = document.getElementById('diff-error');
    var resEl = document.getElementById('diff-results');

    if (!fromVal || !toVal) { errEl.textContent = '開始日と終了日を両方入力してください。'; errEl.classList.add('visible'); resEl.classList.remove('visible'); return; }

    var fromDate = new Date(fromVal);
    var toDate = new Date(toVal);

    if (isNaN(fromDate.getTime()) || isNaN(toDate.getTime())) { errEl.textContent = '日付が正しくありません。'; errEl.classList.add('visible'); resEl.classList.remove('visible'); return; }

    errEl.classList.remove('visible');

    var earlier = fromDate <= toDate ? fromDate : toDate;
    var later = fromDate <= toDate ? toDate : fromDate;
    var earlierLabel = fromDate <= toDate ? '開始日' : '終了日';
    var laterLabel = fromDate <= toDate ? '終了日' : '開始日';

    var diffMs = later - earlier;
    var diffDays = Math.round(diffMs / 86400000);
    var diffWeeks = Math.floor(diffDays / 7);
    var diffMonths = (diffDays / 30.4375).toFixed(1);
    var diffYears = (diffDays / 365.25).toFixed(2);
    var diffHours = diffDays * 24;

    document.getElementById('diff-label').textContent =
      earlierLabel + '〜' + laterLabel + ' の期間';
    document.getElementById('diff-days-val').textContent = fmt(diffDays);
    document.getElementById('diff-weeks-val').textContent = fmt(diffWeeks);
    document.getElementById('diff-months-val').textContent = diffMonths;
    document.getElementById('diff-years-val').textContent = diffYears;
    document.getElementById('diff-hours-val').textContent = fmt(diffHours);
    document.getElementById('diff-from-weekday').textContent = WEEKDAYS[fromDate.getDay()];
    document.getElementById('diff-to-weekday').textContent = WEEKDAYS[toDate.getDay()];

    resEl.classList.add('visible');
  };

  window.diffReset = function() {
    document.getElementById('diff-from').value = '';
    document.getElementById('diff-to').value = todayStr;
    document.getElementById('diff-error').classList.remove('visible');
    document.getElementById('diff-results').classList.remove('visible');
  };
})();
</script>

---

## 正確な年齢の計算方法

年齢の計算は「誕生日の前日が終わった瞬間に年齢が加算される」という「年齢計算ニ関スル法律（明治35年）」に基づいています。つまり、誕生日の前日の午後12時（深夜0時）に満年齢が1つ増えるため、法律的には誕生日当日ではなく「誕生日の前日」に年齢が変わります。このツールでは、より直感的な「誕生日当日に年齢が増える」計算を採用しています。月・日の計算については、基準日の日付が誕生日の日付より小さい場合は前の月に繰り戻して残り日数を計算する「満年齢方式」を用いています。

総日数・総時間数はあくまで概算であり、うるう秒や夏時間などは考慮していません。うるう年（2月29日生まれ）の場合、非うるう年の誕生日は2月28日または3月1日として扱うケースがありますが、本ツールでは2月28日を誕生日として計算します。正確な法的年齢判断が必要な場合は、専門家にご相談ください。

---

## 年齢にまつわる豆知識

世界最長寿として認定されたフランス人女性ジャンヌ・カルマンは122歳164日（1875〜1997年）を生き、約44,724日という途方もない日数を過ごしました。日本では「人生の節目」を表す言葉が豊富で、60歳の「還暦」は干支が一巡することを意味し、赤いちゃんちゃんこで祝うのは「赤ちゃんに還る」という縁起から来ています。77歳「喜寿」は「喜」の草書体が七十七に見えることに由来し、88歳「米寿」は「米」の字を分解すると八十八になることから命名されました。また、1万時間の法則（マルコム・グラッドウェル著『天才！』で広まった概念）では、ある分野の専門家になるには約1万時間の練習が必要とされており、これは毎日3時間練習すると約9年、毎日8時間だと約3.4年に相当します。

---

## 関連ツール

> BMIと適正体重をチェック → [BMI計算ツール](/ja/tools/bmi-calculator/)

> 割合・割引・変化率をすぐ計算 → [パーセント計算ツール](/ja/tools/percent-calculator/)

> 長さ・重さ・温度を即座に変換 → [単位変換ツール](/ja/tools/unit-converter/)

> 海外チームと時間を合わせる → [タイムゾーン変換ツール](/ja/tools/timezone-converter/) — 世界中の都市間で時刻を即変換

---

**ライフプランに合わせた資産管理を**

年齢とともに変わるお金の課題。家計管理・確定申告はクラウド会計ソフト「freee」で効率化しませんか？

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
