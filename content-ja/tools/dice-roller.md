---
title: "サイコロシミュレーター"
description: "無料のオンラインサイコロツール。1〜10個のダイスを4面・6面・8面・10面・12面・20面で振れます。ボードゲーム・TRPG・テーブルゲームに最適。アニメーション付き。"
slug: dice-roller
date: 2025-04-03
categories: ["無料ツール"]
tags: ["サイコロ", "ダイス", "TRPG", "ボードゲーム", "乱数", "シミュレーター"]
ShowToc: false
cover:
  image: /images/covers/dice-roller-ja.png
  alt: "サイコロシミュレーター - 無料オンラインダイスローラー"
---

ブラウザだけでサイコロが振れます。ボードゲーム・TRPG・テーブルゲームに最適。ダイスの種類と数を選んでロールしましょう。

<div id="dr-app">

<style>
#dr-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
}
#dr-app * { box-sizing: border-box; }

#dr-app .dr-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  align-items: flex-end;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
}
#dr-app .dr-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
#dr-app .dr-field label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#dr-app select {
  padding: 10px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 15px;
  background: #fff;
  color: #1e293b;
  cursor: pointer;
  outline: none;
  transition: border-color 0.15s;
}
#dr-app select:focus { border-color: #6366f1; }

#dr-app .dr-btn {
  padding: 11px 28px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  transition: transform 0.1s, background 0.15s;
  user-select: none;
}
#dr-app .dr-btn:active { transform: scale(0.96); }
#dr-app .dr-btn-roll {
  background: #6366f1;
  color: #fff;
  font-size: 17px;
  padding: 12px 36px;
}
#dr-app .dr-btn-roll:hover { background: #4f46e5; }
#dr-app .dr-btn-sound {
  background: #e2e8f0;
  color: #475569;
  padding: 11px 16px;
  font-size: 18px;
}
#dr-app .dr-btn-sound:hover { background: #cbd5e1; }

#dr-app .dr-quick-btns {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}
#dr-app .dr-quick-btns span {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  align-self: center;
  margin-right: 4px;
}
#dr-app .dr-btn-quick {
  padding: 7px 16px;
  background: #fff;
  border: 1.5px solid #6366f1;
  color: #6366f1;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#dr-app .dr-btn-quick:hover {
  background: #6366f1;
  color: #fff;
}

#dr-app .dr-result-area {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 20px;
  min-height: 140px;
  text-align: center;
}
#dr-app .dr-dice-row {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  margin-bottom: 16px;
  min-height: 64px;
  align-items: center;
}
#dr-app .dr-die {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 22px;
  font-weight: 800;
  box-shadow: 0 4px 12px rgba(99,102,241,0.3), inset 0 1px 0 rgba(255,255,255,0.2);
  transition: transform 0.15s;
}
#dr-app .dr-die.rolling {
  animation: dr-spin 0.5s ease-out;
}
@keyframes dr-spin {
  0%   { transform: rotateY(0deg) rotateX(0deg) scale(0.8); opacity: 0.4; }
  40%  { transform: rotateY(180deg) rotateX(90deg) scale(1.1); opacity: 1; }
  70%  { transform: rotateY(320deg) rotateX(40deg) scale(0.95); }
  100% { transform: rotateY(360deg) rotateX(0deg) scale(1); opacity: 1; }
}
#dr-app .dr-total {
  font-size: 32px;
  font-weight: 800;
  color: #4f46e5;
}
#dr-app .dr-total-label {
  font-size: 13px;
  color: #94a3b8;
  margin-top: 2px;
}
#dr-app .dr-note {
  font-size: 13px;
  color: #64748b;
  margin-top: 8px;
  font-style: italic;
}
#dr-app .dr-placeholder {
  color: #94a3b8;
  font-size: 15px;
  padding: 20px 0;
}

#dr-app .dr-stats {
  display: flex;
  gap: 12px;
  margin-bottom: 20px;
}
#dr-app .dr-stat-box {
  flex: 1;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 14px;
  text-align: center;
}
#dr-app .dr-stat-val {
  font-size: 22px;
  font-weight: 700;
  color: #4f46e5;
}
#dr-app .dr-stat-lbl {
  font-size: 11px;
  color: #94a3b8;
  margin-top: 2px;
}

#dr-app .dr-history-title {
  font-size: 13px;
  font-weight: 600;
  color: #64748b;
  margin-bottom: 10px;
}
#dr-app .dr-history-list {
  list-style: none;
  padding: 0;
  margin: 0;
  max-height: 240px;
  overflow-y: auto;
}
#dr-app .dr-history-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 12px;
  border-radius: 7px;
  font-size: 13px;
  color: #475569;
  border-bottom: 1px solid #f1f5f9;
}
#dr-app .dr-history-list li:last-child { border-bottom: none; }
#dr-app .dr-history-list li:nth-child(odd) { background: #f8fafc; }
#dr-app .dr-history-total {
  font-weight: 700;
  color: #4f46e5;
}
#dr-app .dr-empty-history {
  text-align: center;
  color: #94a3b8;
  font-size: 14px;
  padding: 16px;
}

@media (max-width: 500px) {
  #dr-app .dr-controls { flex-direction: column; }
  #dr-app .dr-stats { flex-wrap: wrap; }
  #dr-app .dr-stat-box { min-width: calc(50% - 6px); }
  #dr-app .dr-die { width: 52px; height: 52px; font-size: 18px; }
}
</style>

<!-- コントロール -->
<div class="dr-controls">
  <div class="dr-field">
    <label>ダイスの数</label>
    <select id="dr-num-dice">
      <option value="1">1個</option>
      <option value="2" selected>2個</option>
      <option value="3">3個</option>
      <option value="4">4個</option>
      <option value="5">5個</option>
      <option value="6">6個</option>
      <option value="7">7個</option>
      <option value="8">8個</option>
      <option value="9">9個</option>
      <option value="10">10個</option>
    </select>
  </div>
  <div class="dr-field">
    <label>面数</label>
    <select id="dr-sides">
      <option value="4">d4（4面）</option>
      <option value="6" selected>d6（6面）</option>
      <option value="8">d8（8面）</option>
      <option value="10">d10（10面）</option>
      <option value="12">d12（12面）</option>
      <option value="20">d20（20面）</option>
    </select>
  </div>
  <button class="dr-btn dr-btn-roll" id="dr-roll-btn">🎲 ロール</button>
  <button class="dr-btn dr-btn-sound" id="dr-sound-btn" title="サウンドのオン/オフ">🔊</button>
</div>

<!-- クイックロール -->
<div class="dr-quick-btns">
  <span>クイックロール：</span>
  <button class="dr-btn-quick" data-num="2" data-sides="6">2d6</button>
  <button class="dr-btn-quick" data-num="1" data-sides="20">1d20</button>
  <button class="dr-btn-quick" data-num="3" data-sides="6">3d6</button>
  <button class="dr-btn-quick" data-num="4" data-sides="6" data-drop-lowest="1">4d6最低値除外</button>
</div>

<!-- 結果エリア -->
<div class="dr-result-area">
  <div class="dr-dice-row" id="dr-dice-row">
    <div class="dr-placeholder">ダイスを選んでロールしてください</div>
  </div>
  <div id="dr-total-wrap" style="display:none;">
    <div class="dr-total" id="dr-total"></div>
    <div class="dr-total-label" id="dr-total-label"></div>
    <div class="dr-note" id="dr-note"></div>
  </div>
</div>

<!-- 統計 -->
<div class="dr-stats">
  <div class="dr-stat-box">
    <div class="dr-stat-val" id="dr-stat-avg">—</div>
    <div class="dr-stat-lbl">平均</div>
  </div>
  <div class="dr-stat-box">
    <div class="dr-stat-val" id="dr-stat-min">—</div>
    <div class="dr-stat-lbl">最小値</div>
  </div>
  <div class="dr-stat-box">
    <div class="dr-stat-val" id="dr-stat-max">—</div>
    <div class="dr-stat-lbl">最大値</div>
  </div>
  <div class="dr-stat-box">
    <div class="dr-stat-val" id="dr-stat-count">0</div>
    <div class="dr-stat-lbl">総ロール数</div>
  </div>
</div>

<!-- 履歴 -->
<div>
  <div class="dr-history-title">ロール履歴（直近20回）</div>
  <ul class="dr-history-list" id="dr-history-list">
    <li class="dr-empty-history" id="dr-empty-hist">まだロールしていません。ダイスを振ってみましょう！</li>
  </ul>
</div>

<script>
(function() {
  'use strict';

  var numDiceEl  = document.getElementById('dr-num-dice');
  var sidesEl    = document.getElementById('dr-sides');
  var rollBtn    = document.getElementById('dr-roll-btn');
  var soundBtn   = document.getElementById('dr-sound-btn');
  var diceRow    = document.getElementById('dr-dice-row');
  var totalWrap  = document.getElementById('dr-total-wrap');
  var totalEl    = document.getElementById('dr-total');
  var totalLabel = document.getElementById('dr-total-label');
  var noteEl     = document.getElementById('dr-note');
  var historyEl  = document.getElementById('dr-history-list');
  var statAvg    = document.getElementById('dr-stat-avg');
  var statMin    = document.getElementById('dr-stat-min');
  var statMax    = document.getElementById('dr-stat-max');
  var statCount  = document.getElementById('dr-stat-count');

  var soundOn = true;
  var history = [];
  var allTotals = [];
  var rolling = false;

  var audioCtx = null;
  function getAudioCtx() {
    if (!audioCtx) {
      try { audioCtx = new (window.AudioContext || window.webkitAudioContext)(); } catch(e) {}
    }
    return audioCtx;
  }
  function playRollSound() {
    if (!soundOn) return;
    var ctx = getAudioCtx();
    if (!ctx) return;
    for (var i = 0; i < 3; i++) {
      (function(delay) {
        setTimeout(function() {
          var osc = ctx.createOscillator();
          var gain = ctx.createGain();
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.type = 'triangle';
          osc.frequency.setValueAtTime(280 + Math.random() * 180, ctx.currentTime);
          osc.frequency.exponentialRampToValueAtTime(80, ctx.currentTime + 0.08);
          gain.gain.setValueAtTime(0.18, ctx.currentTime);
          gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.1);
          osc.start(ctx.currentTime);
          osc.stop(ctx.currentTime + 0.12);
        }, delay);
      })(i * 80);
    }
  }

  soundBtn.addEventListener('click', function() {
    soundOn = !soundOn;
    soundBtn.textContent = soundOn ? '🔊' : '🔇';
  });

  document.querySelectorAll('#dr-app .dr-btn-quick').forEach(function(btn) {
    btn.addEventListener('click', function() {
      numDiceEl.value = btn.dataset.num;
      sidesEl.value   = btn.dataset.sides;
      doRoll(parseInt(btn.dataset.num), parseInt(btn.dataset.sides), parseInt(btn.dataset.dropLowest || '0'));
    });
  });

  rollBtn.addEventListener('click', function() {
    var n = parseInt(numDiceEl.value);
    var s = parseInt(sidesEl.value);
    doRoll(n, s, 0);
  });

  function randInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  function doRoll(numDice, sides, dropLowest) {
    if (rolling) return;
    rolling = true;
    rollBtn.disabled = true;
    playRollSound();

    var results = [];
    for (var i = 0; i < numDice; i++) {
      results.push(randInt(1, sides));
    }

    var dropped = null;
    var usedResults = results.slice();
    if (dropLowest > 0 && usedResults.length > dropLowest) {
      var sorted = usedResults.slice().sort(function(a, b) { return a - b; });
      dropped = sorted.slice(0, dropLowest);
      for (var d = 0; d < dropped.length; d++) {
        var idx = usedResults.indexOf(dropped[d]);
        if (idx !== -1) usedResults.splice(idx, 1);
      }
    }
    var total = usedResults.reduce(function(a, b) { return a + b; }, 0);

    diceRow.innerHTML = '';
    totalWrap.style.display = 'none';

    results.forEach(function(val, idx) {
      var die = document.createElement('div');
      die.className = 'dr-die';
      var isDropped = dropped && dropped.includes(val) && idx >= usedResults.length;
      die.textContent = '?';
      if (isDropped) {
        die.style.opacity = '0.35';
        die.style.background = '#94a3b8';
        die.title = '除外';
      }
      diceRow.appendChild(die);

      (function(el, finalVal, delay) {
        el.classList.add('rolling');
        var shuffleInterval = setInterval(function() {
          el.textContent = randInt(1, sides);
        }, 60);
        setTimeout(function() {
          clearInterval(shuffleInterval);
          el.textContent = finalVal;
          el.classList.remove('rolling');
        }, delay + 400);
      })(die, val, idx * 80);
    });

    var totalDelay = results.length * 80 + 500;
    setTimeout(function() {
      totalWrap.style.display = 'block';
      totalEl.textContent = total;
      var diceLabel = numDice + 'd' + sides;
      if (dropLowest > 0) diceLabel += ' 最低値除外';
      totalLabel.textContent = '合計（' + diceLabel + '）';
      if (results.length > 1) {
        var indivStr = results.map(function(v, i) {
          if (dropped && i >= usedResults.length) return '[' + v + ']';
          return v;
        }).join(' + ');
        noteEl.textContent = '内訳: ' + indivStr;
      } else {
        noteEl.textContent = '';
      }

      addHistory(results, total, sides, dropLowest, usedResults);
      updateStats();

      rolling = false;
      rollBtn.disabled = false;
    }, totalDelay);
  }

  function addHistory(results, total, sides, dropLowest, usedResults) {
    allTotals.push(total);
    var entry = {
      label: results.length + 'd' + sides + (dropLowest > 0 ? ' DL' : ''),
      results: results,
      total: total
    };
    history.unshift(entry);
    if (history.length > 20) history.pop();

    historyEl.innerHTML = '';
    if (history.length === 0) {
      var li = document.createElement('li');
      li.id = 'dr-empty-hist';
      li.className = 'dr-empty-history';
      li.textContent = 'まだロールしていません。';
      historyEl.appendChild(li);
      return;
    }
    history.forEach(function(h, idx) {
      var li = document.createElement('li');
      var left = document.createElement('span');
      left.textContent = '#' + (history.length - idx) + '  ' + h.label + '  [' + h.results.join(', ') + ']';
      var right = document.createElement('span');
      right.className = 'dr-history-total';
      right.textContent = '= ' + h.total;
      li.appendChild(left);
      li.appendChild(right);
      historyEl.appendChild(li);
    });
  }

  function updateStats() {
    if (allTotals.length === 0) return;
    var sum = allTotals.reduce(function(a, b) { return a + b; }, 0);
    var avg = (sum / allTotals.length).toFixed(1);
    var min = Math.min.apply(null, allTotals);
    var max = Math.max.apply(null, allTotals);
    statAvg.textContent = avg;
    statMin.textContent = min;
    statMax.textContent = max;
    statCount.textContent = allTotals.length;
  }
})();
</script>

</div>

---

<div class="dr-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">ボードゲームカフェの経営にも</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、店舗経営の売上・経費管理もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

## 使い方

1. **ダイスの数を選ぶ** — 1〜10個から選択。
2. **面数を選ぶ** — d4・d6・d8・d10・d12・d20から選択。
3. **ロールをクリック** — アニメーションとともに結果と合計が表示されます。
4. **クイックロール** — よく使う組み合わせをワンクリックで。

## よく使うダイスの組み合わせ

| 組み合わせ | 用途 |
|---|---|
| 2d6 | 一般的なボードゲーム、すごろく |
| 1d20 | D&D 攻撃ロール・技能判定 |
| 3d6 | 多くのTRPGでの能力値決定 |
| 4d6最低値除外 | D&D 5e キャラクター能力値作成 |
| 1d6 | 簡単な乱数決定 |

## 関連ツール

- 乱数を生成 → [乱数ジェネレーター](/ja/tools/random-number-generator/)
- ゲームタイマー → [カウントダウンタイマー](/ja/tools/countdown-timer/)

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
