---
title: "乱数生成ツール｜無料オンラインランダム数字ジェネレーター"
date: 2025-05-16
description: "最小値・最大値を指定してランダムな数字を即座に生成。複数生成・重複なし・サイコロ・コイントス・リストからランダム選択にも対応。無料・登録不要。"
categories: ["無料ツール"]
tags: ["乱数", "ランダム", "サイコロ", "コイントス", "数字生成", "無料ツール"]
slug: "random-number-generator"
aliases: ["/ja/tools/random-generator/", "/ja/tools/number-picker/"]
cover:
  image: "/images/covers/random-number-generator-ja.png"
  alt: "乱数生成ツール"
ShowToc: false
---

<div id="rng-app">

<style>
#rng-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #e2e8f0;
}

#rng-app * {
  box-sizing: border-box;
}

#rng-app .rng-card {
  background: #1a0533;
  border: 1px solid #4c1d95;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 16px;
}

#rng-app .rng-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}

#rng-app .rng-tab {
  flex: 1;
  min-width: 80px;
  padding: 10px 10px;
  border: 1px solid #4c1d95;
  border-radius: 8px;
  background: #12002a;
  color: #a78bfa;
  cursor: pointer;
  font-size: 13px;
  font-weight: 500;
  transition: all 0.2s;
  text-align: center;
  user-select: none;
}

#rng-app .rng-tab:hover {
  border-color: #7c3aed;
  color: #c4b5fd;
}

#rng-app .rng-tab.active {
  background: #5b21b6;
  border-color: #7c3aed;
  color: #fff;
}

#rng-app .rng-result-box {
  background: #0d001f;
  border: 2px solid #4c1d95;
  border-radius: 12px;
  padding: 28px 20px;
  text-align: center;
  margin-bottom: 16px;
  min-height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;
  overflow: hidden;
}

#rng-app .rng-result-number {
  font-size: 56px;
  font-weight: 800;
  color: #a78bfa;
  letter-spacing: -1px;
  line-height: 1;
  transition: opacity 0.15s;
}

#rng-app .rng-result-number.animating {
  animation: rngSpinJa 0.5s ease-out;
}

@keyframes rngSpinJa {
  0%   { opacity: 0; transform: translateY(-20px) scale(0.85); }
  60%  { opacity: 1; transform: translateY(4px) scale(1.05); }
  100% { opacity: 1; transform: translateY(0) scale(1); }
}

#rng-app .rng-result-label {
  font-size: 12px;
  color: #6d28d9;
  margin-top: 8px;
  letter-spacing: 0.05em;
}

#rng-app .rng-multi-results {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  padding: 10px 0;
}

#rng-app .rng-multi-chip {
  background: #2e1065;
  border: 1px solid #5b21b6;
  border-radius: 8px;
  padding: 8px 16px;
  font-size: 20px;
  font-weight: 700;
  color: #c4b5fd;
  animation: rngSpinJa 0.5s ease-out both;
}

#rng-app .rng-btn-row {
  display: flex;
  gap: 10px;
}

#rng-app .rng-btn {
  padding: 12px 24px;
  border-radius: 8px;
  border: none;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
}

#rng-app .rng-btn-primary {
  background: #7c3aed;
  color: #fff;
  flex: 2;
}

#rng-app .rng-btn-primary:hover {
  background: #6d28d9;
  transform: translateY(-1px);
  box-shadow: 0 4px 16px #7c3aed44;
}

#rng-app .rng-btn-primary:active {
  transform: translateY(0);
}

#rng-app .rng-btn-secondary {
  background: #2e1065;
  color: #c4b5fd;
  border: 1px solid #4c1d95;
  flex: 1;
}

#rng-app .rng-btn-secondary:hover {
  background: #3b0f8a;
  color: #fff;
}

#rng-app .rng-field-row {
  display: flex;
  gap: 12px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

#rng-app .rng-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex: 1;
  min-width: 80px;
}

#rng-app .rng-label {
  font-size: 12px;
  font-weight: 600;
  color: #7c3aed;
  letter-spacing: 0.06em;
}

#rng-app .rng-input {
  background: #12002a;
  border: 1px solid #4c1d95;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 16px;
  font-weight: 600;
  padding: 10px 12px;
  outline: none;
  width: 100%;
  transition: border-color 0.2s;
}

#rng-app .rng-input:focus {
  border-color: #7c3aed;
}

#rng-app .rng-toggle-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 16px;
}

#rng-app .rng-toggle-label {
  font-size: 14px;
  color: #a78bfa;
  cursor: pointer;
  user-select: none;
}

#rng-app .rng-toggle {
  position: relative;
  width: 40px;
  height: 22px;
  flex-shrink: 0;
}

#rng-app .rng-toggle input {
  opacity: 0;
  width: 0;
  height: 0;
  position: absolute;
}

#rng-app .rng-toggle-slider {
  position: absolute;
  inset: 0;
  background: #2e1065;
  border: 1px solid #4c1d95;
  border-radius: 22px;
  cursor: pointer;
  transition: 0.2s;
}

#rng-app .rng-toggle-slider:before {
  content: '';
  position: absolute;
  width: 16px;
  height: 16px;
  background: #6d28d9;
  border-radius: 50%;
  left: 2px;
  top: 2px;
  transition: 0.2s;
}

#rng-app .rng-toggle input:checked + .rng-toggle-slider {
  background: #5b21b6;
  border-color: #7c3aed;
}

#rng-app .rng-toggle input:checked + .rng-toggle-slider:before {
  background: #c4b5fd;
  transform: translateX(18px);
}

/* Dice */
#rng-app .rng-dice-row {
  display: flex;
  gap: 14px;
  justify-content: center;
  flex-wrap: wrap;
  padding: 10px 0;
}

#rng-app .rng-die {
  width: 64px;
  height: 64px;
  background: #2e1065;
  border: 2px solid #5b21b6;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;
  animation: rngDiceRollJa 0.4s ease-out both;
}

@keyframes rngDiceRollJa {
  0%   { transform: rotate(-20deg) scale(0.7); opacity: 0; }
  60%  { transform: rotate(5deg) scale(1.08); opacity: 1; }
  100% { transform: rotate(0deg) scale(1); opacity: 1; }
}

#rng-app .rng-die-dots {
  display: grid;
  width: 44px;
  height: 44px;
  padding: 4px;
}

#rng-app .rng-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #a78bfa;
  margin: auto;
}

#rng-app .rng-dot.hidden {
  background: transparent;
}

/* Coin */
#rng-app .rng-coin-wrap {
  perspective: 600px;
  display: flex;
  justify-content: center;
  padding: 10px 0;
}

#rng-app .rng-coin {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: linear-gradient(135deg, #7c3aed, #5b21b6);
  border: 4px solid #a78bfa;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
  font-weight: 800;
  color: #fff;
  box-shadow: 0 0 24px #7c3aed66;
  transform-style: preserve-3d;
}

#rng-app .rng-coin.flipping {
  animation: rngCoinFlipJa 0.7s ease-out;
}

@keyframes rngCoinFlipJa {
  0%   { transform: rotateY(0deg); }
  50%  { transform: rotateY(900deg) scale(0.85); }
  100% { transform: rotateY(1800deg) scale(1); }
}

#rng-app .rng-coin-label {
  font-size: 14px;
  font-weight: 700;
  color: #c4b5fd;
  text-align: center;
  margin-top: 10px;
}

/* List picker */
#rng-app .rng-textarea {
  background: #12002a;
  border: 1px solid #4c1d95;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 14px;
  padding: 10px 12px;
  width: 100%;
  outline: none;
  resize: vertical;
  min-height: 100px;
  font-family: inherit;
  transition: border-color 0.2s;
}

#rng-app .rng-textarea:focus {
  border-color: #7c3aed;
}

#rng-app .rng-list-result {
  font-size: 28px;
  font-weight: 800;
  color: #a78bfa;
  text-align: center;
  min-height: 44px;
  word-break: break-word;
}

/* History */
#rng-app .rng-history-title {
  font-size: 12px;
  font-weight: 700;
  color: #6d28d9;
  letter-spacing: 0.06em;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#rng-app .rng-history-clear {
  font-size: 11px;
  color: #4c1d95;
  cursor: pointer;
  background: none;
  border: none;
  padding: 2px 6px;
  border-radius: 4px;
  transition: color 0.2s;
}

#rng-app .rng-history-clear:hover {
  color: #7c3aed;
}

#rng-app .rng-history-list {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  min-height: 32px;
}

#rng-app .rng-history-chip {
  background: #1a0533;
  border: 1px solid #3b0f8a;
  border-radius: 20px;
  padding: 4px 12px;
  font-size: 13px;
  color: #c4b5fd;
}

#rng-app .rng-section {
  display: none;
}

#rng-app .rng-section.active {
  display: block;
}

#rng-app .rng-dice-count-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

#rng-app .rng-dice-count-btn {
  width: 36px;
  height: 36px;
  border-radius: 8px;
  border: 1px solid #4c1d95;
  background: #12002a;
  color: #a78bfa;
  font-size: 20px;
  font-weight: 700;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s;
  line-height: 1;
}

#rng-app .rng-dice-count-btn:hover {
  background: #2e1065;
  border-color: #7c3aed;
  color: #fff;
}

#rng-app .rng-dice-count-val {
  font-size: 16px;
  font-weight: 700;
  color: #c4b5fd;
  min-width: 70px;
  text-align: center;
}

#rng-app .rng-dice-sum {
  font-size: 14px;
  color: #6d28d9;
  margin-top: 8px;
  text-align: center;
}

@media (max-width: 480px) {
  #rng-app .rng-card { padding: 16px; }
  #rng-app .rng-result-number { font-size: 40px; }
  #rng-app .rng-btn-row { flex-direction: column; }
  #rng-app .rng-tab { font-size: 11px; padding: 8px 4px; }
  #rng-app .rng-die { width: 52px; height: 52px; }
}
</style>

<div class="rng-card">
  <div class="rng-tabs">
    <div class="rng-tab active" id="rng-tab-number" onclick="rngSetMode('number')">数字</div>
    <div class="rng-tab" id="rng-tab-dice" onclick="rngSetMode('dice')">サイコロ</div>
    <div class="rng-tab" id="rng-tab-coin" onclick="rngSetMode('coin')">コイン</div>
    <div class="rng-tab" id="rng-tab-list" onclick="rngSetMode('list')">リスト</div>
  </div>

  <!-- 数字モード -->
  <div class="rng-section active" id="rng-sec-number">
    <div class="rng-field-row">
      <div class="rng-field">
        <label class="rng-label" for="rng-min">最小値</label>
        <input class="rng-input" type="number" id="rng-min" value="1">
      </div>
      <div class="rng-field">
        <label class="rng-label" for="rng-max">最大値</label>
        <input class="rng-input" type="number" id="rng-max" value="100">
      </div>
      <div class="rng-field">
        <label class="rng-label" for="rng-qty">生成数</label>
        <input class="rng-input" type="number" id="rng-qty" value="1" min="1" max="100">
      </div>
    </div>

    <div class="rng-toggle-row">
      <label class="rng-toggle" for="rng-no-dup">
        <input type="checkbox" id="rng-no-dup">
        <span class="rng-toggle-slider"></span>
      </label>
      <span class="rng-toggle-label">重複なし</span>
    </div>

    <div class="rng-result-box" id="rng-number-result-box">
      <div id="rng-number-output" class="rng-result-number">—</div>
      <div class="rng-result-label" id="rng-number-label">生成ボタンを押してください</div>
    </div>

    <div class="rng-btn-row">
      <button class="rng-btn rng-btn-primary" onclick="rngGenerateNumber()">&#9656; 生成する</button>
      <button class="rng-btn rng-btn-secondary" onclick="rngCopyResult()">&#128203; コピー</button>
    </div>
  </div>

  <!-- サイコロモード -->
  <div class="rng-section" id="rng-sec-dice">
    <div class="rng-dice-count-row">
      <span class="rng-label">サイコロの数：</span>
      <button class="rng-dice-count-btn" onclick="rngChangeDiceCount(-1)">&#8722;</button>
      <span class="rng-dice-count-val" id="rng-dice-count-val">2個</span>
      <button class="rng-dice-count-btn" onclick="rngChangeDiceCount(1)">+</button>
    </div>
    <div class="rng-result-box" id="rng-dice-result-box" style="flex-direction:column;gap:12px;">
      <div class="rng-dice-row" id="rng-dice-display">
        <div style="color:#4c1d95;font-size:14px;">サイコロを振るボタンを押してください</div>
      </div>
      <div class="rng-dice-sum" id="rng-dice-sum"></div>
    </div>
    <div class="rng-btn-row">
      <button class="rng-btn rng-btn-primary" onclick="rngRollDice()">&#9656; サイコロを振る</button>
    </div>
  </div>

  <!-- コインモード -->
  <div class="rng-section" id="rng-sec-coin">
    <div class="rng-result-box" id="rng-coin-result-box" style="flex-direction:column;gap:12px;min-height:160px;">
      <div class="rng-coin-wrap">
        <div class="rng-coin" id="rng-coin">?</div>
      </div>
      <div class="rng-coin-label" id="rng-coin-label">コインを投げるボタンを押してください</div>
    </div>
    <div class="rng-btn-row">
      <button class="rng-btn rng-btn-primary" onclick="rngFlipCoin()">&#9656; コインを投げる</button>
    </div>
  </div>

  <!-- リストモード -->
  <div class="rng-section" id="rng-sec-list">
    <div class="rng-field" style="margin-bottom:12px;">
      <label class="rng-label">リスト（1行に1項目）</label>
      <textarea class="rng-textarea" id="rng-list-input" placeholder="りんご&#10;バナナ&#10;さくらんぼ&#10;ぶどう&#10;メロン"></textarea>
    </div>
    <div class="rng-result-box" id="rng-list-result-box" style="min-height:80px;">
      <div class="rng-list-result" id="rng-list-output">—</div>
    </div>
    <div class="rng-btn-row">
      <button class="rng-btn rng-btn-primary" onclick="rngPickFromList()">&#9656; ランダムに選ぶ</button>
    </div>
  </div>
</div>

<!-- 履歴 -->
<div class="rng-card">
  <div class="rng-history-title">
    <span>生成履歴</span>
    <button class="rng-history-clear" onclick="rngClearHistory()">クリア</button>
  </div>
  <div class="rng-history-list" id="rng-history-list">
    <span style="color:#3b0f8a;font-size:13px;">まだ履歴がありません。</span>
  </div>
</div>

<script>
(function() {
  var rngMode = 'number';
  var rngHistory = [];
  var rngDiceCount = 2;
  var rngLastNumbers = null;

  window.rngSetMode = function(m) {
    rngMode = m;
    ['number','dice','coin','list'].forEach(function(x) {
      document.getElementById('rng-tab-' + x).classList.toggle('active', x === m);
      document.getElementById('rng-sec-' + x).classList.toggle('active', x === m);
    });
  };

  window.rngChangeDiceCount = function(delta) {
    rngDiceCount = Math.max(1, Math.min(6, rngDiceCount + delta));
    document.getElementById('rng-dice-count-val').textContent = rngDiceCount + '個';
  };

  function randInt(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    if (min > max) { var t = min; min = max; max = t; }
    var range = max - min + 1;
    var arr = new Uint32Array(1);
    var limit = Math.floor(4294967296 / range) * range;
    do { crypto.getRandomValues(arr); } while (arr[0] >= limit);
    return min + (arr[0] % range);
  }

  function animateEl(el) {
    el.classList.remove('animating');
    void el.offsetWidth;
    el.classList.add('animating');
  }

  function pushHistory(entry) {
    rngHistory.unshift(entry);
    if (rngHistory.length > 30) rngHistory.pop();
    renderHistory();
  }

  function renderHistory() {
    var el = document.getElementById('rng-history-list');
    if (rngHistory.length === 0) {
      el.innerHTML = '<span style="color:#3b0f8a;font-size:13px;">まだ履歴がありません。</span>';
      return;
    }
    el.innerHTML = '';
    rngHistory.forEach(function(h) {
      var chip = document.createElement('span');
      chip.className = 'rng-history-chip';
      chip.textContent = h;
      el.appendChild(chip);
    });
  }

  window.rngClearHistory = function() {
    rngHistory = [];
    renderHistory();
  };

  window.rngGenerateNumber = function() {
    var min = parseInt(document.getElementById('rng-min').value);
    var max = parseInt(document.getElementById('rng-max').value);
    var qty = Math.max(1, Math.min(100, parseInt(document.getElementById('rng-qty').value) || 1));
    var noDup = document.getElementById('rng-no-dup').checked;

    if (isNaN(min) || isNaN(max)) return;
    if (min > max) { var t = min; min = max; max = t; }

    var range = max - min + 1;
    var outputEl = document.getElementById('rng-number-output');
    var labelEl  = document.getElementById('rng-number-label');

    if (qty === 1) {
      var n = randInt(min, max);
      rngLastNumbers = [n];
      outputEl.innerHTML = '<span>' + n + '</span>';
      outputEl.style.fontSize = '56px';
      labelEl.textContent = '結果（範囲: ' + min + '〜' + max + '）';
      animateEl(outputEl);
      pushHistory(String(n));
    } else {
      var nums = [];
      if (noDup && qty > range) qty = range;
      if (noDup) {
        var pool = [];
        for (var i = min; i <= max; i++) pool.push(i);
        for (var j = pool.length - 1; j > 0; j--) {
          var k = randInt(0, j);
          var tmp = pool[j]; pool[j] = pool[k]; pool[k] = tmp;
        }
        nums = pool.slice(0, qty).sort(function(a,b){return a-b;});
      } else {
        for (var q = 0; q < qty; q++) nums.push(randInt(min, max));
        nums.sort(function(a,b){return a-b;});
      }
      rngLastNumbers = nums;
      if (qty <= 12) {
        var chips = nums.map(function(n) {
          return '<span class="rng-multi-chip">' + n + '</span>';
        }).join('');
        outputEl.innerHTML = '<div class="rng-multi-results">' + chips + '</div>';
        outputEl.style.fontSize = '16px';
      } else {
        outputEl.innerHTML = '<span>' + nums.join(', ') + '</span>';
        outputEl.style.fontSize = '16px';
      }
      labelEl.textContent = qty + '個の数字（範囲: ' + min + '〜' + max + (noDup ? '・重複なし' : '') + '）';
      pushHistory(nums.join(', '));
    }
  };

  window.rngCopyResult = function() {
    if (!rngLastNumbers) return;
    navigator.clipboard.writeText(rngLastNumbers.join(', ')).then(function() {
      var btn = document.querySelector('#rng-sec-number .rng-btn-secondary');
      if (btn) { btn.textContent = 'コピーしました！'; setTimeout(function(){ btn.innerHTML = '&#128203; コピー'; }, 1800); }
    });
  };

  var DOT_LAYOUTS = {
    1: [[0,0,0],[0,1,0],[0,0,0]],
    2: [[1,0,0],[0,0,0],[0,0,1]],
    3: [[1,0,0],[0,1,0],[0,0,1]],
    4: [[1,0,1],[0,0,0],[1,0,1]],
    5: [[1,0,1],[0,1,0],[1,0,1]],
    6: [[1,0,1],[1,0,1],[1,0,1]]
  };

  function makeDie(val) {
    var die = document.createElement('div');
    die.className = 'rng-die';
    var grid = document.createElement('div');
    grid.className = 'rng-die-dots';
    grid.style.gridTemplateColumns = 'repeat(3, 1fr)';
    grid.style.gridTemplateRows = 'repeat(3, 1fr)';
    var layout = DOT_LAYOUTS[val];
    for (var r = 0; r < 3; r++) {
      for (var c = 0; c < 3; c++) {
        var dot = document.createElement('div');
        dot.className = 'rng-dot' + (layout[r][c] ? '' : ' hidden');
        grid.appendChild(dot);
      }
    }
    die.appendChild(grid);
    return die;
  }

  window.rngRollDice = function() {
    var display = document.getElementById('rng-dice-display');
    var sumEl   = document.getElementById('rng-dice-sum');
    display.innerHTML = '';
    var total = 0;
    var vals = [];
    for (var i = 0; i < rngDiceCount; i++) {
      var v = randInt(1, 6);
      vals.push(v);
      total += v;
      (function(val, idx) {
        var die = makeDie(val);
        die.style.animationDelay = (idx * 80) + 'ms';
        display.appendChild(die);
      })(v, i);
    }
    sumEl.textContent = rngDiceCount > 1 ? '合計: ' + total + '  （' + vals.join(' + ') + '）' : '出目: ' + vals[0];
    pushHistory('サイコロ ' + vals.join('+') + (rngDiceCount > 1 ? '=' + total : ''));
  };

  window.rngFlipCoin = function() {
    var coin  = document.getElementById('rng-coin');
    var label = document.getElementById('rng-coin-label');
    coin.classList.remove('flipping');
    void coin.offsetWidth;
    coin.classList.add('flipping');
    setTimeout(function() {
      var result = randInt(0, 1);
      coin.textContent = result ? '表' : '裏';
      label.textContent = result ? '表（おもて）！' : '裏（うら）！';
      pushHistory(result ? 'コイン: 表' : 'コイン: 裏');
    }, 500);
  };

  window.rngPickFromList = function() {
    var raw   = document.getElementById('rng-list-input').value;
    var items = raw.split('\n').map(function(s){ return s.trim(); }).filter(function(s){ return s.length > 0; });
    var outEl = document.getElementById('rng-list-output');
    if (items.length === 0) {
      outEl.textContent = 'リストに項目を入力してください。';
      return;
    }
    var pick = items[randInt(0, items.length - 1)];
    outEl.textContent = pick;
    animateEl(outEl);
    pushHistory('リスト: ' + pick);
  };
})();
</script>

</div>

---

## 使い方

**数字モード：** 最小値・最大値・生成数を入力して「生成する」を押すだけ。重複なしトグルをオンにすると、同じ数字が出ない抽選が可能です。

**サイコロモード：** サイコロの個数（1〜6個）を選んで「サイコロを振る」を押すと、目のドット絵が表示されます。合計値も自動計算されます。

**コインモード：** 「コインを投げる」でランダムに表・裏を判定。アニメーション付きで視覚的にも楽しめます。

**リストモード：** テキストエリアに項目を1行ずつ入力し、「ランダムに選ぶ」を押すと1つをランダムに選択。出し物・当番・お昼ごはんのお店選びにも便利です。

**生成履歴：** 生成した結果はすべて履歴に記録されます（最大30件）。

---

**業務のデジタル化にはfreee**

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
