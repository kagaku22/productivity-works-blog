---
title: "睡眠サイクル計算ツール"
date: 2025-05-16
description: "無料の睡眠サイクル計算ツール。90分周期に基づいて最適な就寝時刻・起床時刻を計算。すっきり目覚めるための睡眠サイクルを提案。"
categories: ["無料ツール"]
slug: "sleep-calculator"
ShowToc: false
cover:
  image: "/images/covers/sleep-calculator-ja.png"
  alt: "睡眠サイクル計算ツール"
---

起床時刻か就寝時刻を入力するだけで、90分の睡眠サイクルに基づいた最適なスケジュールを計算。サイクルの途中で目覚めずに、すっきりした朝を迎えましょう。

<div id="sl-app">
<style>
#sl-app *,
#sl-app *::before,
#sl-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#sl-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: #1e293b;
  max-width: 700px;
  margin: 0 auto;
  padding: 8px 0;
  font-size: 15px;
  line-height: 1.6;
}
#sl-app h2 {
  font-size: 18px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 16px;
}
#sl-app .sl-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 22px 24px;
  margin-bottom: 20px;
}
#sl-app .sl-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 22px;
}
#sl-app .sl-tab {
  flex: 1;
  padding: 10px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  background: #fff;
  color: #475569;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  text-align: center;
  transition: all 0.15s;
}
#sl-app .sl-tab:hover {
  border-color: #6366f1;
  color: #6366f1;
}
#sl-app .sl-tab.active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#sl-app .sl-label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #334155;
  margin-bottom: 7px;
}
#sl-app .sl-time-input {
  width: 100%;
  max-width: 220px;
  padding: 10px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 22px;
  font-weight: 700;
  color: #0f172a;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
}
#sl-app .sl-time-input:focus {
  border-color: #6366f1;
}
#sl-app .sl-hint {
  font-size: 12px;
  color: #94a3b8;
  margin-top: 6px;
}
#sl-app .sl-btn {
  display: inline-block;
  margin-top: 16px;
  padding: 11px 28px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#sl-app .sl-btn:hover {
  background: #4f46e5;
}
#sl-app .sl-results {
  display: none;
}
#sl-app .sl-results.visible {
  display: block;
}
#sl-app .sl-results-title {
  font-size: 15px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 14px;
  padding-bottom: 8px;
  border-bottom: 2px solid #e2e8f0;
}
#sl-app .sl-cycle-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#sl-app .sl-cycle-item {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 14px 16px;
  border-radius: 10px;
  border: 1.5px solid #e2e8f0;
  background: #fff;
}
#sl-app .sl-cycle-item.best {
  border-color: #6366f1;
  background: #eef2ff;
}
#sl-app .sl-cycle-item.good {
  border-color: #34d399;
  background: #f0fdf4;
}
#sl-app .sl-cycle-time {
  font-size: 24px;
  font-weight: 800;
  color: #0f172a;
  min-width: 72px;
}
#sl-app .sl-cycle-meta {
  display: flex;
  flex-direction: column;
  gap: 2px;
}
#sl-app .sl-cycle-cycles {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
}
#sl-app .sl-cycle-duration {
  font-size: 12px;
  color: #94a3b8;
}
#sl-app .sl-badge {
  margin-left: auto;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
  white-space: nowrap;
}
#sl-app .sl-badge-best {
  background: #6366f1;
  color: #fff;
}
#sl-app .sl-badge-good {
  background: #34d399;
  color: #fff;
}
#sl-app .sl-badge-ok {
  background: #f1f5f9;
  color: #64748b;
}
#sl-app .sl-timeline {
  margin-top: 8px;
  padding: 16px;
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
}
#sl-app .sl-timeline-title {
  font-size: 13px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 12px;
}
#sl-app .sl-tl-bar {
  display: flex;
  height: 28px;
  border-radius: 6px;
  overflow: hidden;
  margin-bottom: 8px;
}
#sl-app .sl-tl-seg {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  font-weight: 700;
  color: #fff;
  transition: flex 0.3s;
}
#sl-app .sl-tl-seg.fall-asleep { background: #94a3b8; }
#sl-app .sl-tl-seg.cycle { background: #6366f1; }
#sl-app .sl-tl-seg.cycle.even { background: #818cf8; }
#sl-app .sl-tl-legend {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}
#sl-app .sl-tl-legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 11px;
  color: #64748b;
}
#sl-app .sl-tl-dot {
  width: 10px;
  height: 10px;
  border-radius: 3px;
  flex-shrink: 0;
}
#sl-app .sl-section-label {
  font-size: 13px;
  font-weight: 700;
  color: #334155;
  margin-bottom: 10px;
  margin-top: 18px;
}
#sl-app .sl-tips {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
#sl-app .sl-tip {
  display: flex;
  gap: 10px;
  align-items: flex-start;
  font-size: 13px;
  color: #475569;
  padding: 10px 14px;
  background: #f8fafc;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
}
#sl-app .sl-tip-icon {
  font-size: 16px;
  flex-shrink: 0;
  line-height: 1.4;
}
@media (max-width: 520px) {
  #sl-app .sl-tabs {
    flex-direction: column;
  }
  #sl-app .sl-cycle-time {
    font-size: 20px;
    min-width: 60px;
  }
}
</style>

<div class="sl-tabs">
  <button class="sl-tab active" id="sl-tab-wake" onclick="(function(){document.getElementById('sl-tab-wake').classList.add('active');document.getElementById('sl-tab-bed').classList.remove('active');document.getElementById('sl-panel-wake').style.display='block';document.getElementById('sl-panel-bed').style.display='none';document.getElementById('sl-results').classList.remove('visible');})()">起床時刻から計算する</button>
  <button class="sl-tab" id="sl-tab-bed" onclick="(function(){document.getElementById('sl-tab-bed').classList.add('active');document.getElementById('sl-tab-wake').classList.remove('active');document.getElementById('sl-panel-bed').style.display='block';document.getElementById('sl-panel-wake').style.display='none';document.getElementById('sl-results').classList.remove('visible');})()">就寝時刻から計算する</button>
</div>

<div class="sl-card">
  <div id="sl-panel-wake">
    <label class="sl-label" for="sl-wake-time">目標の起床時刻</label>
    <input type="time" id="sl-wake-time" class="sl-time-input">
    <p class="sl-hint">90分の睡眠サイクルに基づいて、最適な就寝時刻を計算します。</p>
  </div>
  <div id="sl-panel-bed" style="display:none;">
    <label class="sl-label" for="sl-bed-time">就寝時刻（眠りにつく時刻）</label>
    <input type="time" id="sl-bed-time" class="sl-time-input">
    <p class="sl-hint">90分の睡眠サイクルに基づいて、最適な起床時刻を計算します。</p>
  </div>
  <button class="sl-btn" onclick="slCalculate()">睡眠時刻を計算する</button>
</div>

<div class="sl-results" id="sl-results">
  <div class="sl-card">
    <p class="sl-results-title" id="sl-results-title">おすすめの就寝時刻</p>
    <ul class="sl-cycle-list" id="sl-cycle-list"></ul>
  </div>
  <div class="sl-card" id="sl-timeline-card">
    <p class="sl-timeline-title">睡眠サイクルのタイムライン（ベスト選択時）</p>
    <div class="sl-tl-bar" id="sl-tl-bar"></div>
    <div class="sl-tl-legend">
      <div class="sl-tl-legend-item"><div class="sl-tl-dot" style="background:#94a3b8;"></div>入眠時間（約14分）</div>
      <div class="sl-tl-legend-item"><div class="sl-tl-dot" style="background:#6366f1;"></div>90分サイクル</div>
    </div>
  </div>
  <div class="sl-card">
    <p class="sl-section-label">睡眠の質を高めるヒント</p>
    <ul class="sl-tips">
      <li class="sl-tip"><span class="sl-tip-icon">🌙</span><span><strong>毎日同じ時間に寝起きする：</strong>週末も含めて就寝・起床時刻を固定することで、体内時計が安定します。</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">📵</span><span><strong>寝る前はスクリーンを避ける：</strong>就寝30〜60分前からスマホ・PC画面を控えましょう。ブルーライトはメラトニン分泌を抑制します。</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">❄️</span><span><strong>寝室を涼しく保つ：</strong>理想的な室温は18〜20℃。体温が下がることで眠気が誘発されます。</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">☕</span><span><strong>カフェインは早めにカット：</strong>カフェインの半減期は約5時間。就寝6時間前には摂取を控えるのがベストです。</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">🛏️</span><span><strong>ベッドは睡眠専用に：</strong>ベッドで作業や動画視聴をしないことで、脳が「ベッド＝眠る場所」と認識します。</span></li>
      <li class="sl-tip"><span class="sl-tip-icon">💡</span><span><strong>5〜6サイクルが理想：</strong>多くの成人は5〜6回の90分サイクル（7.5〜9時間）で最もすっきり目覚められます。サイクルの途中で起きると睡眠慣性（だるさ）が残ります。</span></li>
    </ul>
  </div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function () {
  var FALL_ASLEEP_MIN = 14;
  var CYCLE_MIN = 90;

  function pad(n) { return n < 10 ? '0' + n : '' + n; }

  function minutesToTime(totalMin) {
    var norm = ((totalMin % 1440) + 1440) % 1440;
    var h = Math.floor(norm / 60);
    var m = norm % 60;
    return pad(h) + ':' + pad(m);
  }

  function timeInputToMinutes(val) {
    if (!val) return null;
    var parts = val.split(':');
    return parseInt(parts[0], 10) * 60 + parseInt(parts[1], 10);
  }

  function setCurrentTime(inputId) {
    var now = new Date();
    var el = document.getElementById(inputId);
    if (el && !el.value) {
      el.value = pad(now.getHours()) + ':' + pad(now.getMinutes());
    }
  }

  setCurrentTime('sl-wake-time');
  setCurrentTime('sl-bed-time');

  function getBadge(cycles) {
    if (cycles >= 5 && cycles <= 6) return { cls: 'sl-badge-best', label: 'ベスト' };
    if (cycles === 4) return { cls: 'sl-badge-good', label: '良好' };
    return { cls: 'sl-badge-ok', label: cycles + 'サイクル' };
  }

  function renderTimeline(cycles) {
    var bar = document.getElementById('sl-tl-bar');
    bar.innerHTML = '';
    var totalMin = FALL_ASLEEP_MIN + cycles * CYCLE_MIN;
    var fallPct = (FALL_ASLEEP_MIN / totalMin * 100).toFixed(1);
    var cyclePct = (CYCLE_MIN / totalMin * 100).toFixed(1);

    var fallSeg = document.createElement('div');
    fallSeg.className = 'sl-tl-seg fall-asleep';
    fallSeg.style.flex = fallPct;
    fallSeg.title = '入眠時間：約14分';
    bar.appendChild(fallSeg);

    for (var i = 1; i <= cycles; i++) {
      var seg = document.createElement('div');
      seg.className = 'sl-tl-seg cycle' + (i % 2 === 0 ? ' even' : '');
      seg.style.flex = cyclePct;
      seg.textContent = i <= 4 ? i : '';
      seg.title = 'サイクル' + i + '：90分';
      bar.appendChild(seg);
    }
  }

  window.slCalculate = function () {
    var isModeWake = document.getElementById('sl-tab-wake').classList.contains('active');
    var anchorMin;

    if (isModeWake) {
      anchorMin = timeInputToMinutes(document.getElementById('sl-wake-time').value);
      if (anchorMin === null) { alert('起床時刻を入力してください。'); return; }
    } else {
      anchorMin = timeInputToMinutes(document.getElementById('sl-bed-time').value);
      if (anchorMin === null) { alert('就寝時刻を入力してください。'); return; }
    }

    var list = document.getElementById('sl-cycle-list');
    list.innerHTML = '';

    var cycleCounts = [6, 5, 4, 3];
    var firstRender = true;

    cycleCounts.forEach(function (cycles) {
      var sleepMin = FALL_ASLEEP_MIN + cycles * CYCLE_MIN;
      var resultMin;

      if (isModeWake) {
        resultMin = anchorMin - sleepMin;
      } else {
        resultMin = anchorMin + sleepMin;
      }

      var badge = getBadge(cycles);
      var li = document.createElement('li');
      li.className = 'sl-cycle-item' + (badge.cls === 'sl-badge-best' ? ' best' : badge.cls === 'sl-badge-good' ? ' good' : '');

      var hours = Math.floor(sleepMin / 60);
      var mins = sleepMin % 60;
      var durationStr = hours + '時間' + (mins > 0 ? mins + '分' : '');

      li.innerHTML =
        '<span class="sl-cycle-time">' + minutesToTime(resultMin) + '</span>' +
        '<span class="sl-cycle-meta">' +
          '<span class="sl-cycle-cycles">' + cycles + 'サイクル</span>' +
          '<span class="sl-cycle-duration">合計睡眠 ' + durationStr + '</span>' +
        '</span>' +
        '<span class="sl-badge ' + badge.cls + '">' + badge.label + '</span>';

      if (firstRender) {
        renderTimeline(cycles);
        firstRender = false;
      }

      list.appendChild(li);
    });

    var titleEl = document.getElementById('sl-results-title');
    var anchorStr = minutesToTime(anchorMin);
    titleEl.textContent = isModeWake
      ? anchorStr + ' に起きるための就寝時刻'
      : anchorStr + ' に就寝した場合のおすすめ起床時刻';

    document.getElementById('sl-results').classList.add('visible');
    document.getElementById('sl-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  document.addEventListener('keydown', function (e) {
    if (e.key === 'Enter') { window.slCalculate(); }
  });
})();
</script>

</div>

---

> カロリーを計算 → [カロリー計算ツール](/ja/tools/calorie-calculator/)
> BMIを確認する → [BMI計算ツール](/ja/tools/bmi-calculator/)
> 正確な年齢を調べる → [年齢計算ツール](/ja/tools/age-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
