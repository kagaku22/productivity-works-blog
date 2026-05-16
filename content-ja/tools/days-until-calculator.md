---
title: "日数計算ツール - あと何日？日付カウントダウン"
date: 2025-05-16
description: "あと何日か瞬時に計算。2つの日付の間の日数、営業日数、週数も計算できる無料ツール。祝日・GW・お盆などの参考情報付き。"
categories: ["無料ツール"]
slug: "days-until-calculator"
ShowToc: false
cover:
  image: "/images/covers/days-until-calculator.png"
  alt: "日数計算ツール"
---

<div id="duc-app">
<style>
#duc-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 760px;
  margin: 0 auto;
  color: #1a1a2e;
}
#duc-app * { box-sizing: border-box; }
#duc-app h2 {
  font-size: 1.2rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
  color: #1a1a2e;
}
#duc-app .duc-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}
#duc-app .duc-tab {
  padding: 0.6rem 1rem;
  font-size: 0.88rem;
  font-weight: 700;
  color: #64748b;
  background: none;
  border: none;
  border-bottom: 3px solid transparent;
  cursor: pointer;
  transition: all 0.2s;
  margin-bottom: -2px;
}
#duc-app .duc-tab:hover { color: #2563eb; }
#duc-app .duc-tab.active {
  color: #2563eb;
  border-bottom-color: #2563eb;
}
#duc-app .duc-panel { display: none; }
#duc-app .duc-panel.active { display: block; }
#duc-app .duc-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1rem;
}
#duc-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 700;
  color: #374151;
  margin-bottom: 0.4rem;
}
#duc-app input[type="date"],
#duc-app input[type="number"],
#duc-app select {
  width: 100%;
  padding: 0.6rem 0.85rem;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 0.95rem;
  color: #1a1a2e;
  background: #fff;
  transition: border-color 0.2s;
}
#duc-app input[type="date"]:focus,
#duc-app input[type="number"]:focus,
#duc-app select:focus {
  outline: none;
  border-color: #2563eb;
}
#duc-app .duc-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1rem;
}
@media (max-width: 520px) {
  #duc-app .duc-row { grid-template-columns: 1fr; }
}
#duc-app .duc-field { margin-bottom: 1rem; }
#duc-app .duc-check-row {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
#duc-app .duc-check-row input[type="checkbox"] {
  width: 16px;
  height: 16px;
  cursor: pointer;
}
#duc-app .duc-check-row label {
  margin: 0;
  font-size: 0.88rem;
  cursor: pointer;
}
#duc-app .duc-btn {
  display: inline-block;
  padding: 0.65rem 1.6rem;
  background: #2563eb;
  color: #fff;
  font-size: 0.95rem;
  font-weight: 700;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.2s;
}
#duc-app .duc-btn:hover { background: #1d4ed8; }
#duc-app .duc-results {
  display: none;
  margin-top: 1.25rem;
}
#duc-app .duc-results.show { display: block; }
#duc-app .duc-result-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.75rem;
  margin-bottom: 1rem;
}
@media (max-width: 520px) {
  #duc-app .duc-result-grid { grid-template-columns: 1fr; }
}
#duc-app .duc-result-box {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
#duc-app .duc-result-box.highlight {
  background: linear-gradient(135deg, #2563eb 0%, #7c3aed 100%);
  border-color: transparent;
}
#duc-app .duc-result-box .rval {
  font-size: 2rem;
  font-weight: 800;
  line-height: 1.1;
  color: #1a1a2e;
}
#duc-app .duc-result-box.highlight .rval { color: #fff; }
#duc-app .duc-result-box .rlabel {
  font-size: 0.76rem;
  font-weight: 700;
  color: #64748b;
  margin-top: 0.2rem;
  letter-spacing: 0.02em;
}
#duc-app .duc-result-box.highlight .rlabel { color: rgba(255,255,255,0.85); }
#duc-app .duc-progress-wrap {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-bottom: 0.75rem;
}
#duc-app .duc-progress-label {
  display: flex;
  justify-content: space-between;
  font-size: 0.82rem;
  font-weight: 700;
  color: #64748b;
  margin-bottom: 0.5rem;
}
#duc-app .duc-progress-bar {
  height: 10px;
  background: #e2e8f0;
  border-radius: 99px;
  overflow: hidden;
}
#duc-app .duc-progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #2563eb, #7c3aed);
  border-radius: 99px;
  transition: width 0.6s ease;
}
#duc-app .duc-message {
  background: #eff6ff;
  border: 1px solid #bfdbfe;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  font-size: 0.9rem;
  color: #1e3a8a;
  margin-top: 0.5rem;
}
#duc-app .duc-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
#duc-app .duc-preset-btn {
  padding: 0.35rem 0.85rem;
  font-size: 0.78rem;
  font-weight: 700;
  background: #fff;
  border: 1.5px solid #d1d5db;
  border-radius: 20px;
  cursor: pointer;
  color: #374151;
  transition: all 0.2s;
}
#duc-app .duc-preset-btn:hover {
  background: #2563eb;
  border-color: #2563eb;
  color: #fff;
}
#duc-app .duc-error {
  color: #dc2626;
  font-size: 0.85rem;
  margin-top: 0.5rem;
  display: none;
}
#duc-app .duc-error.show { display: block; }
#duc-app .duc-holiday-note {
  background: #fefce8;
  border: 1px solid #fde68a;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1rem;
  font-size: 0.85rem;
  color: #78350f;
}
#duc-app .duc-holiday-note h3 {
  font-size: 0.9rem;
  font-weight: 700;
  margin: 0 0 0.5rem 0;
  color: #92400e;
}
#duc-app .duc-holiday-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.4rem 1rem;
}
@media (max-width: 420px) {
  #duc-app .duc-holiday-grid { grid-template-columns: 1fr; }
}
#duc-app .duc-holiday-item {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px dashed #fde68a;
  padding: 0.2rem 0;
}
#duc-app .duc-holiday-item .hname { font-weight: 700; }
#duc-app .duc-holiday-item .hdays { color: #b45309; font-weight: 700; }
#duc-app .duc-cta {
  background: #f0fdf4;
  border: 1px solid #86efac;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1.25rem;
  font-size: 0.9rem;
  color: #14532d;
}
#duc-app .duc-add-result {
  display: none;
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1rem 1.25rem;
  margin-top: 1rem;
}
#duc-app .duc-add-result.show { display: block; }
#duc-app .duc-add-result .big-date {
  font-size: 1.35rem;
  font-weight: 800;
  color: #2563eb;
  margin-top: 0.3rem;
}
</style>

**無料ツール** — 日付までの残り日数・週数・営業日数を瞬時に計算します。

<div class="duc-tabs">
  <button class="duc-tab active" onclick="ducSwitchTab('countdown')">あと何日？</button>
  <button class="duc-tab" onclick="ducSwitchTab('between')">2日付間の日数</button>
  <button class="duc-tab" onclick="ducSwitchTab('addsubtract')">日数の加減算</button>
</div>

<!-- PANEL 1: カウントダウン -->
<div class="duc-panel active" id="duc-panel-countdown">
  <div class="duc-card">
    <h2>特定の日まであと何日？</h2>
    <div style="margin-bottom:0.75rem;font-size:0.82rem;color:#64748b;font-weight:700;">クイック選択：</div>
    <div class="duc-presets">
      <button class="duc-preset-btn" onclick="ducPreset('oshogatsu')">お正月</button>
      <button class="duc-preset-btn" onclick="ducPreset('gw')">GW（5/3〜5/6）</button>
      <button class="duc-preset-btn" onclick="ducPreset('obon')">お盆（8/13〜16）</button>
      <button class="duc-preset-btn" onclick="ducPreset('christmas')">クリスマス</button>
      <button class="duc-preset-btn" onclick="ducPreset('halloween')">ハロウィン</button>
      <button class="duc-preset-btn" onclick="ducPreset('valentine')">バレンタイン</button>
      <button class="duc-preset-btn" onclick="ducPreset('nendo')">年度末（3/31）</button>
      <button class="duc-preset-btn" onclick="ducPreset('nextbday')">誕生日</button>
    </div>
    <div class="duc-field">
      <label for="duc-target-date">対象の日付</label>
      <input type="date" id="duc-target-date" />
    </div>
    <div class="duc-check-row">
      <input type="checkbox" id="duc-excl-weekends" />
      <label for="duc-excl-weekends">営業日のみでカウント（土日を除く）</label>
    </div>
    <div class="duc-error" id="duc-cd-error">日付を選択してください。</div>
    <button class="duc-btn" onclick="ducCalcCountdown()">計算する</button>
    <div class="duc-results" id="duc-cd-results">
      <div class="duc-result-grid">
        <div class="duc-result-box highlight">
          <div class="rval" id="duc-cd-days">—</div>
          <div class="rlabel" id="duc-cd-days-label">日</div>
        </div>
        <div class="duc-result-box">
          <div class="rval" id="duc-cd-weeks">—</div>
          <div class="rlabel">週間</div>
        </div>
        <div class="duc-result-box">
          <div class="rval" id="duc-cd-months">—</div>
          <div class="rlabel">ヶ月（概算）</div>
        </div>
        <div class="duc-result-box">
          <div class="rval" id="duc-cd-bizdays">—</div>
          <div class="rlabel">営業日</div>
        </div>
      </div>
      <div class="duc-progress-wrap">
        <div class="duc-progress-label">
          <span>今年の経過率</span>
          <span id="duc-year-pct">0%</span>
        </div>
        <div class="duc-progress-bar">
          <div class="duc-progress-fill" id="duc-year-fill" style="width:0%"></div>
        </div>
      </div>
      <div class="duc-message" id="duc-cd-message"></div>
    </div>
  </div>

  <div class="duc-holiday-note">
    <h3>主な日本の連休・節目（参考）</h3>
    <div class="duc-holiday-grid" id="duc-holiday-grid"></div>
  </div>

  <div class="duc-cta">
    スケジュール管理を効率化 →
    <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP"
       target="_blank" rel="noopener sponsored"
       style="color:#15803d;font-weight:700;">
      freee会計で経理の締め日を管理
    </a>
  </div>
</div>

<!-- PANEL 2: 2日付間 -->
<div class="duc-panel" id="duc-panel-between">
  <div class="duc-card">
    <h2>2つの日付の間の日数</h2>
    <div class="duc-row">
      <div>
        <label for="duc-from-date">開始日</label>
        <input type="date" id="duc-from-date" />
      </div>
      <div>
        <label for="duc-to-date">終了日</label>
        <input type="date" id="duc-to-date" />
      </div>
    </div>
    <div class="duc-check-row">
      <input type="checkbox" id="duc-btw-excl" />
      <label for="duc-btw-excl">土日を除いた日数でカウント</label>
    </div>
    <div class="duc-error" id="duc-btw-error">開始日と終了日を両方選択してください。</div>
    <button class="duc-btn" onclick="ducCalcBetween()">計算する</button>
    <div class="duc-results" id="duc-btw-results">
      <div class="duc-result-grid">
        <div class="duc-result-box highlight">
          <div class="rval" id="duc-btw-days">—</div>
          <div class="rlabel" id="duc-btw-days-label">合計日数</div>
        </div>
        <div class="duc-result-box">
          <div class="rval" id="duc-btw-weeks">—</div>
          <div class="rlabel">週間</div>
        </div>
        <div class="duc-result-box">
          <div class="rval" id="duc-btw-months">—</div>
          <div class="rlabel">ヶ月（概算）</div>
        </div>
        <div class="duc-result-box">
          <div class="rval" id="duc-btw-bizdays">—</div>
          <div class="rlabel">営業日数</div>
        </div>
      </div>
      <div class="duc-message" id="duc-btw-message"></div>
    </div>
  </div>
</div>

<!-- PANEL 3: 加減算 -->
<div class="duc-panel" id="duc-panel-addsubtract">
  <div class="duc-card">
    <h2>日付に日数を足す・引く</h2>
    <div class="duc-row">
      <div>
        <label for="duc-base-date">基準日</label>
        <input type="date" id="duc-base-date" />
      </div>
      <div>
        <label for="duc-add-num">日数</label>
        <input type="number" id="duc-add-num" placeholder="例: 30" min="0" max="9999" />
      </div>
    </div>
    <div class="duc-field">
      <label for="duc-add-op">計算方法</label>
      <select id="duc-add-op">
        <option value="add">日数を足す（未来の日付）</option>
        <option value="sub">日数を引く（過去の日付）</option>
      </select>
    </div>
    <div class="duc-check-row">
      <input type="checkbox" id="duc-add-excl" />
      <label for="duc-add-excl">土日をスキップ（営業日のみ）</label>
    </div>
    <div class="duc-error" id="duc-add-error">基準日と日数を入力してください。</div>
    <button class="duc-btn" onclick="ducCalcAdd()">計算する</button>
    <div class="duc-add-result" id="duc-add-result">
      <div style="font-size:0.82rem;color:#64748b;font-weight:700;">結果の日付</div>
      <div class="big-date" id="duc-add-result-date">—</div>
      <div style="font-size:0.82rem;color:#64748b;margin-top:0.5rem;" id="duc-add-result-note"></div>
    </div>
  </div>
</div>

<script>
(function() {
  // Tab switching
  window.ducSwitchTab = function(tab) {
    var tabNames = ['countdown','between','addsubtract'];
    document.querySelectorAll('#duc-app .duc-tab').forEach(function(t, i) {
      t.classList.toggle('active', tabNames[i] === tab);
    });
    document.querySelectorAll('#duc-app .duc-panel').forEach(function(p) {
      p.classList.remove('active');
    });
    document.getElementById('duc-panel-' + tab).classList.add('active');
  };

  // Today defaults
  var today = new Date();
  var todayStr = today.toISOString().slice(0,10);
  document.getElementById('duc-from-date').value = todayStr;
  document.getElementById('duc-base-date').value = todayStr;

  // Japanese holidays reference (fixed annual)
  var y = today.getFullYear();
  var JHOLIDAYS = [
    { name: 'お正月（1/1〜3）',   date: new Date(y+1, 0, 1) },
    { name: '成人の日',           date: new Date(y, 0, 13)  },
    { name: '建国記念日',         date: new Date(y, 1, 11)  },
    { name: '春分の日（目安3/20）',date: new Date(y, 2, 20)  },
    { name: 'GW（4/29〜5/6）',    date: new Date(y, 3, 29)  },
    { name: 'お盆（8/13〜16）',   date: new Date(y, 7, 13)  },
    { name: '敬老の日',           date: new Date(y, 8, 15)  },
    { name: '秋分の日（目安9/23）',date: new Date(y, 8, 23)  },
    { name: '体育の日',           date: new Date(y, 9, 13)  },
    { name: '文化の日',           date: new Date(y, 10, 3)  },
    { name: '勤労感謝の日',       date: new Date(y, 10, 23) },
    { name: '年度末（3/31）',     date: new Date(y+1, 2, 31)},
  ];

  // Render holiday countdown list
  function renderHolidays() {
    var now = new Date(); now.setHours(0,0,0,0);
    var grid = document.getElementById('duc-holiday-grid');
    if (!grid) return;
    var html = '';
    JHOLIDAYS.forEach(function(h) {
      var d = new Date(h.date);
      if (d < now) d.setFullYear(d.getFullYear() + 1);
      var diff = Math.round((d - now) / 86400000);
      html += '<div class="duc-holiday-item"><span class="hname">' + h.name + '</span><span class="hdays">あと' + diff + '日</span></div>';
    });
    grid.innerHTML = html;
  }
  renderHolidays();

  // Presets
  window.ducPreset = function(key) {
    var now = new Date(); now.setHours(0,0,0,0);
    var yn = now.getFullYear();
    var d;
    switch(key) {
      case 'oshogatsu': d = new Date(yn+1, 0, 1); break;
      case 'gw':        d = new Date(yn, 3, 29); if(d<=now) d.setFullYear(yn+1); break;
      case 'obon':      d = new Date(yn, 7, 13); if(d<=now) d.setFullYear(yn+1); break;
      case 'christmas': d = new Date(yn, 11, 25); if(d<=now) d.setFullYear(yn+1); break;
      case 'halloween': d = new Date(yn, 9, 31); if(d<=now) d.setFullYear(yn+1); break;
      case 'valentine': d = new Date(yn, 1, 14); if(d<=now) d.setFullYear(yn+1); break;
      case 'nendo':     d = new Date(yn+1, 2, 31); break;
      case 'nextbday': {
        var stored = localStorage.getItem('duc_bday_jp');
        var month, dayN;
        if (stored) {
          var pts = stored.split('-');
          month = parseInt(pts[0]) - 1;
          dayN  = parseInt(pts[1]);
        } else {
          var inp = prompt('誕生日を入力してください（MM-DD形式、例: 08-15）：');
          if (!inp) return;
          var pp = inp.replace('/','-').split('-');
          month = parseInt(pp[0]) - 1;
          dayN  = parseInt(pp[1]);
          localStorage.setItem('duc_bday_jp', (month+1) + '-' + dayN);
        }
        d = new Date(yn, month, dayN);
        if (d <= now) d = new Date(yn+1, month, dayN);
        break;
      }
      default: return;
    }
    document.getElementById('duc-target-date').value = d.toISOString().slice(0,10);
    ducCalcCountdown();
  };

  // Business days between
  function bizDaysBetween(a, b) {
    var start = new Date(Math.min(a,b));
    var end   = new Date(Math.max(a,b));
    var count = 0;
    var cur   = new Date(start);
    cur.setDate(cur.getDate() + 1);
    while (cur <= end) {
      var wd = cur.getDay();
      if (wd !== 0 && wd !== 6) count++;
      cur.setDate(cur.getDate() + 1);
    }
    return count;
  }

  function daysDiff(a, b) { return Math.round((b - a) / 86400000); }

  function fmtDateJP(d) {
    var wd = ['日','月','火','水','木','金','土'][d.getDay()];
    return d.getFullYear() + '年' + (d.getMonth()+1) + '月' + d.getDate() + '日（' + wd + '）';
  }

  function yearProgress() {
    var now   = new Date();
    var start = new Date(now.getFullYear(), 0, 1);
    var end   = new Date(now.getFullYear() + 1, 0, 1);
    return Math.round(((now - start) / (end - start)) * 100);
  }

  function getMessage(days) {
    if (days < 0)   return 'その日はすでに' + Math.abs(days) + '日前に過ぎています。';
    if (days === 0) return 'その日は今日です！';
    if (days === 1) return '明日です！';
    if (days <= 7)  return '今週中ですね。ラストスパートを！';
    if (days <= 14) return '2週間以内。最終確認を忘れずに。';
    if (days <= 30) return '1ヶ月以内。準備は順調ですか？';
    if (days <= 90) return '3ヶ月以内。計画を立て始めましょう。';
    if (days <= 180) return '半年以内。大きなマイルストーンを設定しましょう。';
    if (days <= 365) return '1年以内。今から備えておくと安心です。';
    return '1年以上先。長期計画を立ててみましょう。';
  }

  // Panel 1: Countdown
  window.ducCalcCountdown = function() {
    var targetVal = document.getElementById('duc-target-date').value;
    var err = document.getElementById('duc-cd-error');
    if (!targetVal) { err.classList.add('show'); return; }
    err.classList.remove('show');

    var target = new Date(targetVal + 'T00:00:00');
    var now    = new Date(); now.setHours(0,0,0,0);
    var totalDays  = daysDiff(now, target);
    var exclWknd   = document.getElementById('duc-excl-weekends').checked;
    var biz        = bizDaysBetween(now, target);
    var displayDays = exclWknd ? (totalDays < 0 ? -biz : biz) : totalDays;

    document.getElementById('duc-cd-days').textContent = Math.abs(displayDays).toLocaleString('ja-JP');
    document.getElementById('duc-cd-days-label').textContent =
      totalDays < 0 ? (exclWknd ? '営業日前' : '日前') : (exclWknd ? '営業日後' : '日後');
    document.getElementById('duc-cd-weeks').textContent  = Math.abs(Math.floor(totalDays / 7)).toLocaleString('ja-JP');
    document.getElementById('duc-cd-months').textContent = Math.abs(Math.floor(totalDays / 30.44)).toLocaleString('ja-JP');
    document.getElementById('duc-cd-bizdays').textContent = biz.toLocaleString('ja-JP');

    var pct = yearProgress();
    document.getElementById('duc-year-pct').textContent = pct + '%';
    document.getElementById('duc-year-fill').style.width = pct + '%';
    document.getElementById('duc-cd-message').textContent = getMessage(totalDays);

    document.getElementById('duc-cd-results').classList.add('show');
    renderHolidays();
  };

  // Panel 2: Between
  window.ducCalcBetween = function() {
    var fromVal = document.getElementById('duc-from-date').value;
    var toVal   = document.getElementById('duc-to-date').value;
    var err = document.getElementById('duc-btw-error');
    if (!fromVal || !toVal) { err.classList.add('show'); return; }
    err.classList.remove('show');

    var from = new Date(fromVal + 'T00:00:00');
    var to   = new Date(toVal   + 'T00:00:00');
    var totalDays = Math.abs(daysDiff(from, to));
    var exclWknd  = document.getElementById('duc-btw-excl').checked;
    var displayDays = exclWknd ? bizDaysBetween(from, to) : totalDays;
    var earlier = from <= to ? fmtDateJP(from) : fmtDateJP(to);
    var later   = from <= to ? fmtDateJP(to)   : fmtDateJP(from);

    document.getElementById('duc-btw-days').textContent = displayDays.toLocaleString('ja-JP');
    document.getElementById('duc-btw-days-label').textContent = exclWknd ? '営業日数' : '合計日数';
    document.getElementById('duc-btw-weeks').textContent  = Math.floor(totalDays / 7).toLocaleString('ja-JP');
    document.getElementById('duc-btw-months').textContent = Math.floor(totalDays / 30.44).toLocaleString('ja-JP');
    document.getElementById('duc-btw-bizdays').textContent = bizDaysBetween(from, to).toLocaleString('ja-JP');
    document.getElementById('duc-btw-message').textContent = earlier + ' から ' + later + ' まで。';

    document.getElementById('duc-btw-results').classList.add('show');
  };

  // Panel 3: Add/Subtract
  window.ducCalcAdd = function() {
    var baseVal = document.getElementById('duc-base-date').value;
    var numVal  = document.getElementById('duc-add-num').value;
    var err = document.getElementById('duc-add-error');
    if (!baseVal || numVal === '') { err.classList.add('show'); return; }
    err.classList.remove('show');

    var base     = new Date(baseVal + 'T00:00:00');
    var num      = parseInt(numVal, 10);
    var op       = document.getElementById('duc-add-op').value;
    var skipWknd = document.getElementById('duc-add-excl').checked;
    var result   = new Date(base);
    var direction = op === 'add' ? 1 : -1;

    if (skipWknd) {
      var remaining = num;
      while (remaining > 0) {
        result.setDate(result.getDate() + direction);
        var wd = result.getDay();
        if (wd !== 0 && wd !== 6) remaining--;
      }
    } else {
      result.setDate(result.getDate() + direction * num);
    }

    document.getElementById('duc-add-result-date').textContent = fmtDateJP(result);
    document.getElementById('duc-add-result-note').textContent =
      fmtDateJP(base) + ' から ' +
      (skipWknd ? '営業日' : 'カレンダー日') + 'で' + num + '日' +
      (op === 'add' ? '後' : '前') + 'の日付です。';
    document.getElementById('duc-add-result').classList.add('show');
  };

  // Auto-trigger on date change
  document.getElementById('duc-target-date').addEventListener('change', ducCalcCountdown);
  document.getElementById('duc-to-date').addEventListener('change', ducCalcBetween);
})();
</script>
</div>
