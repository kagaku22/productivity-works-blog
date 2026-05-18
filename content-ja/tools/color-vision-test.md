---
title: "色覚テスト - あなたの色覚をチェック"
description: "石原式カラーテスト風のインタラクティブ色覚スクリーニング。無料オンライン色覚検査ツール。"
date: 2025-04-04
slug: "color-vision-test"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: "/images/covers/color-vision-test.png"
---

<div id="cvt-app">

<style>
#cvt-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Meiryo', sans-serif;
  max-width: 720px;
  margin: 0 auto;
  padding: 16px;
  color: #1a1a2e;
}
#cvt-app h2 {
  font-size: 1.5rem;
  margin-bottom: 8px;
  color: #1a1a2e;
}
#cvt-app p {
  margin: 0 0 12px;
  line-height: 1.7;
}
#cvt-app .cvt-disclaimer {
  background: #fff8e1;
  border-left: 4px solid #f9a825;
  padding: 10px 14px;
  border-radius: 4px;
  font-size: 0.85rem;
  margin-bottom: 20px;
  color: #5d4037;
}
#cvt-app .cvt-plate-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
  margin-bottom: 20px;
}
#cvt-app .cvt-progress {
  font-size: 0.9rem;
  color: #555;
}
#cvt-app canvas#cvt-canvas {
  border-radius: 50%;
  border: 3px solid #ddd;
  display: block;
  max-width: 100%;
}
#cvt-app .cvt-question {
  font-size: 1.05rem;
  font-weight: 600;
  text-align: center;
}
#cvt-app .cvt-input-row {
  display: flex;
  gap: 8px;
  align-items: center;
  flex-wrap: wrap;
  justify-content: center;
}
#cvt-app input#cvt-answer {
  border: 2px solid #ccc;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 1.1rem;
  width: 120px;
  text-align: center;
  outline: none;
  transition: border-color 0.2s;
}
#cvt-app input#cvt-answer:focus {
  border-color: #5c6bc0;
}
#cvt-app button.cvt-btn {
  background: #5c6bc0;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 10px 22px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.2s;
}
#cvt-app button.cvt-btn:hover {
  background: #3949ab;
}
#cvt-app button.cvt-btn:disabled {
  background: #aaa;
  cursor: default;
}
#cvt-app .cvt-feedback {
  font-size: 0.95rem;
  min-height: 22px;
  text-align: center;
  font-weight: 600;
}
#cvt-app .cvt-feedback.correct { color: #2e7d32; }
#cvt-app .cvt-feedback.wrong   { color: #c62828; }
#cvt-app .cvt-result {
  background: #f3f4ff;
  border: 2px solid #5c6bc0;
  border-radius: 12px;
  padding: 24px;
  text-align: center;
}
#cvt-app .cvt-result h3 {
  margin: 0 0 10px;
  font-size: 1.3rem;
  color: #1a1a2e;
}
#cvt-app .cvt-score-num {
  font-size: 2.8rem;
  font-weight: 700;
  color: #5c6bc0;
  line-height: 1;
  margin: 10px 0;
}
#cvt-app .cvt-interp {
  margin: 12px 0;
  padding: 12px;
  border-radius: 8px;
  background: #e8eaf6;
  font-size: 0.97rem;
  line-height: 1.7;
}
#cvt-app .cvt-detail-list {
  text-align: left;
  font-size: 0.9rem;
  margin: 12px 0;
  padding: 0 0 0 18px;
  color: #333;
}
#cvt-app .cvt-detail-list li {
  margin-bottom: 4px;
}
#cvt-app button#cvt-restart {
  margin-top: 14px;
  background: #5c6bc0;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 10px 28px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.2s;
}
#cvt-app button#cvt-restart:hover {
  background: #3949ab;
}
#cvt-app .cvt-cta {
  margin-top: 28px;
  padding: 16px;
  background: #f0f4ff;
  border-left: 4px solid #5c6bc0;
  border-radius: 6px;
  font-size: 0.95rem;
  line-height: 1.7;
}
#cvt-app .cvt-hidden { display: none; }
</style>

<h2>色覚テスト（石原式スクリーニング）</h2>
<p>石原式に基づいたスクリーニングテストです。各プレートを見て、隠された数字を入力してください。全5問です。</p>

<div class="cvt-disclaimer">
  <strong>注意事項：</strong>このテストはスクリーニングツールです。医学的診断ではありません。正確な診断は眼科医にご相談ください。
</div>

<div id="cvt-test-area">
  <div class="cvt-plate-area">
    <div class="cvt-progress" id="cvt-progress">第1問 / 全5問</div>
    <canvas id="cvt-canvas" width="300" height="300"></canvas>
    <div class="cvt-question" id="cvt-question">見えている数字を入力してください</div>
    <div class="cvt-input-row">
      <input type="text" id="cvt-answer" maxlength="2" placeholder="0〜99" autocomplete="off" inputmode="numeric" />
      <button class="cvt-btn" id="cvt-submit">回答する</button>
    </div>
    <div class="cvt-feedback" id="cvt-feedback"></div>
  </div>
</div>

<div id="cvt-result-area" class="cvt-result cvt-hidden">
  <h3>テスト結果</h3>
  <div class="cvt-score-num" id="cvt-score-display"></div>
  <div style="font-size:1rem;color:#555;">5問中の正解数</div>
  <div class="cvt-interp" id="cvt-interp"></div>
  <ul class="cvt-detail-list" id="cvt-detail-list"></ul>
  <div class="cvt-disclaimer" style="margin-top:14px;">
    <strong>再確認：</strong>このテストはスクリーニング目的のみです。診断は必ず眼科専門医にご相談ください。
  </div>
  <button id="cvt-restart">もう一度テストする</button>
</div>

<div class="cvt-cta">

> 健康管理も仕事も効率化 → [freee会計で日々の管理を自動化](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

</div>

<script>
(function() {
  // ── プレート定義 ──────────────────────────────────────────────────
  var plates = [
    {
      number: 12,
      fgColor: '#d44',
      bgColor: '#8a6',
      deficiency: '赤緑色覚異常（1型・2型）',
      desc: '赤系 vs 緑系'
    },
    {
      number: 8,
      fgColor: '#c84',
      bgColor: '#5a8',
      deficiency: '第2色覚異常',
      desc: 'オレンジ系 vs 緑系'
    },
    {
      number: 29,
      fgColor: '#b55',
      bgColor: '#6a9',
      deficiency: '第1色覚異常',
      desc: '赤系 vs ティール系'
    },
    {
      number: 5,
      fgColor: '#55b',
      bgColor: '#ba5',
      deficiency: '第3色覚異常（青黄）',
      desc: '青紫系 vs 黄緑系'
    },
    {
      number: 74,
      fgColor: '#c66',
      bgColor: '#7a5',
      deficiency: '赤緑色覚異常（1型・2型）',
      desc: 'サーモン系 vs オリーブ緑系'
    }
  ];

  var current = 0;
  var answers = [];
  var answered = false;

  var canvas    = document.getElementById('cvt-canvas');
  var ctx       = canvas.getContext('2d');
  var progress  = document.getElementById('cvt-progress');
  var question  = document.getElementById('cvt-question');
  var input     = document.getElementById('cvt-answer');
  var submitBtn = document.getElementById('cvt-submit');
  var feedback  = document.getElementById('cvt-feedback');
  var testArea  = document.getElementById('cvt-test-area');
  var resultArea   = document.getElementById('cvt-result-area');
  var scoreDisplay = document.getElementById('cvt-score-display');
  var interpEl     = document.getElementById('cvt-interp');
  var detailList   = document.getElementById('cvt-detail-list');
  var restartBtn   = document.getElementById('cvt-restart');

  // ── Canvas描画 ────────────────────────────────────────────────────
  function hexToRgb(hex) {
    var r = parseInt(hex.slice(1,3),16);
    var g = parseInt(hex.slice(3,5),16);
    var b = parseInt(hex.slice(5,7),16);
    return [r,g,b];
  }

  function rgbStr(c) {
    return 'rgb('+c[0]+','+c[1]+','+c[2]+')';
  }

  function seededRand(seed) {
    var s = seed;
    return function() {
      s = (s * 1664525 + 1013904223) & 0xffffffff;
      return (s >>> 0) / 0xffffffff;
    };
  }

  var FONT5x7 = {
    '0': [0x1f,0x11,0x11,0x11,0x11,0x11,0x1f],
    '1': [0x04,0x0c,0x04,0x04,0x04,0x04,0x0e],
    '2': [0x1f,0x01,0x01,0x1f,0x10,0x10,0x1f],
    '3': [0x1f,0x01,0x01,0x0f,0x01,0x01,0x1f],
    '4': [0x11,0x11,0x11,0x1f,0x01,0x01,0x01],
    '5': [0x1f,0x10,0x10,0x1f,0x01,0x01,0x1f],
    '6': [0x1f,0x10,0x10,0x1f,0x11,0x11,0x1f],
    '7': [0x1f,0x01,0x02,0x04,0x08,0x08,0x08],
    '8': [0x1f,0x11,0x11,0x1f,0x11,0x11,0x1f],
    '9': [0x1f,0x11,0x11,0x1f,0x01,0x01,0x1f]
  };

  function getDigitMask(numStr, W, H) {
    var digits = String(numStr);
    var cellW = 5, cellH = 7, gap = 1;
    var totalW = digits.length * cellW + (digits.length-1) * gap;
    var startX = (W - totalW) / 2;
    var startY = (H - cellH) / 2;
    var pixels = new Set();
    for (var di = 0; di < digits.length; di++) {
      var rows = FONT5x7[digits[di]];
      if (!rows) continue;
      for (var row = 0; row < 7; row++) {
        for (var col = 0; col < 5; col++) {
          if (rows[row] & (0x10 >> col)) {
            pixels.add((startX+di*(cellW+gap)+col)+'_'+(startY+row));
          }
        }
      }
    }
    return { pixels: pixels };
  }

  function drawPlate(plate, plateIndex) {
    var W = canvas.width, H = canvas.height, R = W/2;
    ctx.clearRect(0,0,W,H);
    var rand = seededRand(plateIndex * 7919 + 13);
    var fgRgb = hexToRgb(plate.fgColor);
    var bgRgb = hexToRgb(plate.bgColor);
    var GRID = 9;
    var cols = Math.floor(W/GRID), rows = Math.floor(H/GRID);
    var maskInfo = getDigitMask(plate.number, cols, rows);

    for (var i = 0; i < 900; i++) {
      var angle = rand()*Math.PI*2;
      var dist  = Math.sqrt(rand())*(R-8);
      var cx    = R + Math.cos(angle)*dist;
      var cy    = R + Math.sin(angle)*dist;
      var cr    = 4 + rand()*9;
      var gx = Math.floor(cx/GRID), gy = Math.floor(cy/GRID);
      var inDigit = maskInfo.pixels.has(gx+'_'+gy);
      var base = inDigit ? fgRgb : bgRgb;
      var noise = rand()*0.22 - 0.11;
      var noiseRgb = [
        Math.min(255,Math.max(0,base[0]+Math.round(noise*60))),
        Math.min(255,Math.max(0,base[1]+Math.round(noise*60))),
        Math.min(255,Math.max(0,base[2]+Math.round(noise*60)))
      ];
      ctx.beginPath();
      ctx.arc(cx, cy, cr, 0, Math.PI*2);
      ctx.fillStyle = rgbStr(noiseRgb);
      ctx.fill();
    }

    ctx.save();
    ctx.globalCompositeOperation = 'destination-in';
    ctx.beginPath();
    ctx.arc(R, R, R-2, 0, Math.PI*2);
    ctx.fillStyle = '#000';
    ctx.fill();
    ctx.restore();
  }

  // ── テスト進行 ────────────────────────────────────────────────────
  function loadPlate(idx) {
    answered = false;
    progress.textContent = '第' + (idx+1) + '問 / 全' + plates.length + '問';
    question.textContent = '見えている数字を入力してください（見えない場合は 0）';
    input.value = '';
    feedback.textContent = '';
    feedback.className = 'cvt-feedback';
    submitBtn.disabled = false;
    input.disabled = false;
    input.focus();
    drawPlate(plates[idx], idx);
  }

  function submitAnswer() {
    if (answered) return;
    var val = input.value.trim();
    if (val === '') {
      feedback.textContent = '数字を入力してください（見えない場合は 0）';
      feedback.className = 'cvt-feedback wrong';
      return;
    }
    answered = true;
    submitBtn.disabled = true;
    input.disabled = true;

    var plate = plates[current];
    var correct = parseInt(val, 10) === plate.number;
    answers.push({ plate: plate, userAnswer: val, correct: correct });

    if (correct) {
      feedback.textContent = '正解です！';
      feedback.className = 'cvt-feedback correct';
    } else {
      feedback.textContent = '正解は ' + plate.number + ' でした。';
      feedback.className = 'cvt-feedback wrong';
    }

    setTimeout(function() {
      current++;
      if (current < plates.length) {
        loadPlate(current);
      } else {
        showResult();
      }
    }, 1100);
  }

  function showResult() {
    testArea.style.display = 'none';
    resultArea.classList.remove('cvt-hidden');

    var score = answers.filter(function(a){ return a.correct; }).length;
    scoreDisplay.textContent = score + ' / ' + plates.length;

    var interp;
    if (score === 5) {
      interp = '素晴らしい！全問正解です。今回のスクリーニングでは、色覚に問題は見られませんでした。';
    } else if (score >= 3) {
      interp = (5-score) + '問を見逃しました。特定の色の組み合わせで認識が難しい場合があります。眼科での精密検査をご検討ください。';
    } else {
      interp = (5-score) + '問を見逃しました。色覚異常の可能性があります。正確な診断のため、眼科専門医への受診をお勧めします。';
    }
    interpEl.textContent = interp;

    detailList.innerHTML = '';
    answers.forEach(function(a, i) {
      var li = document.createElement('li');
      var icon = a.correct ? '○' : '×';
      li.textContent = icon + ' 第' + (i+1) + '問（' + a.plate.desc + '）: あなたの回答「' + a.userAnswer + '」、正解は ' + a.plate.number;
      li.style.color = a.correct ? '#2e7d32' : '#c62828';
      detailList.appendChild(li);
    });
  }

  function restart() {
    current = 0;
    answers = [];
    answered = false;
    resultArea.classList.add('cvt-hidden');
    testArea.style.display = '';
    loadPlate(0);
  }

  // ── イベント ──────────────────────────────────────────────────────
  submitBtn.addEventListener('click', submitAnswer);
  input.addEventListener('keydown', function(e) {
    if (e.key === 'Enter') submitAnswer();
  });
  restartBtn.addEventListener('click', restart);

  loadPlate(0);
})();
</script>

</div>

---

## 関連ツール

> Color Blindness Simulator → [Color Blindness Simulatorツール](/ja/tools/color-blindness-simulator/)
> Color Contrast Checker → [Color Contrast Checkerツール](/ja/tools/color-contrast-checker/)
> Color Converter → [Color Converterツール](/ja/tools/color-converter/)

