---
title: "アスペクト比計算ツール"
date: 2025-05-16
description: "無料のアスペクト比計算ツール。動画・画像・画面のアスペクト比を計算・変換・比較。ビジュアルプレビュー付き、会員登録不要。"
categories: ["無料ツール"]
slug: "aspect-ratio-calculator"
ShowToc: false
cover:
  image: "/images/covers/aspect-ratio-calculator-ja.png"
  alt: "アスペクト比計算ツール"
---

<div id="ar-app">

<style>
#ar-app {
  font-family: 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1e293b;
}
#ar-app h2.ar-section-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #1e293b;
  border-left: 4px solid #475569;
  padding-left: 10px;
  margin: 28px 0 14px;
}
#ar-app .ar-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 20px 22px;
  margin-bottom: 20px;
}
#ar-app label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 4px;
}
#ar-app input[type="number"],
#ar-app select {
  width: 100%;
  padding: 9px 12px;
  border: 1px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  color: #1e293b;
  background: #fff;
  box-sizing: border-box;
  outline: none;
  transition: border-color 0.2s;
}
#ar-app input[type="number"]:focus,
#ar-app select:focus {
  border-color: #475569;
}
#ar-app .ar-row {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}
#ar-app .ar-row > div {
  flex: 1 1 120px;
  min-width: 100px;
}
#ar-app .ar-btn {
  display: inline-block;
  padding: 10px 22px;
  background: #334155;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  margin-top: 12px;
  transition: background 0.18s;
}
#ar-app .ar-btn:hover {
  background: #1e293b;
}
#ar-app .ar-result {
  margin-top: 14px;
  padding: 13px 16px;
  background: #e0f2fe;
  border: 1px solid #bae6fd;
  border-radius: 8px;
  font-size: 15px;
  color: #0c4a6e;
  font-weight: 600;
  min-height: 38px;
}
#ar-app .ar-result.error {
  background: #fef2f2;
  border-color: #fecaca;
  color: #b91c1c;
}
#ar-app .ar-preset-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 4px;
}
#ar-app .ar-preset-btn {
  padding: 7px 15px;
  background: #fff;
  border: 1.5px solid #cbd5e1;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 600;
  color: #334155;
  cursor: pointer;
  transition: all 0.16s;
}
#ar-app .ar-preset-btn:hover,
#ar-app .ar-preset-btn.active {
  background: #334155;
  color: #fff;
  border-color: #334155;
}
#ar-app canvas {
  display: block;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  background: #f1f5f9;
  max-width: 100%;
}
#ar-app .ar-canvas-wrap {
  display: flex;
  gap: 18px;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 10px;
}
#ar-app .ar-canvas-item {
  text-align: center;
  flex: 1 1 200px;
}
#ar-app .ar-canvas-label {
  font-size: 12px;
  color: #64748b;
  margin-top: 6px;
}
#ar-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
  margin-top: 8px;
}
#ar-app th {
  background: #e2e8f0;
  color: #1e293b;
  font-weight: 700;
  padding: 8px 10px;
  text-align: left;
}
#ar-app td {
  padding: 7px 10px;
  border-bottom: 1px solid #f1f5f9;
  color: #334155;
}
#ar-app tr:nth-child(even) td {
  background: #f8fafc;
}
#ar-app .ar-compare-flex {
  display: flex;
  gap: 18px;
  margin-top: 14px;
  flex-wrap: wrap;
}
#ar-app .ar-compare-box {
  flex: 1 1 200px;
  background: #f1f5f9;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 12px 14px;
  text-align: center;
}
#ar-app .ar-compare-box .ar-compare-ratio {
  font-size: 1.25rem;
  font-weight: 800;
  color: #1e293b;
}
#ar-app .ar-compare-box .ar-compare-name {
  font-size: 12px;
  color: #64748b;
  margin-top: 4px;
}
@media (max-width: 540px) {
  #ar-app .ar-row { flex-direction: column; }
  #ar-app .ar-compare-flex { flex-direction: column; }
  #ar-app .ar-canvas-wrap { flex-direction: column; align-items: center; }
}
</style>

---

## 使い方

幅と高さを入力してアスペクト比を計算、または比率から辺の長さを逆算。プリセット・プレビュー・比較モード付き。

---

<h2 class="ar-section-title">1. アスペクト比を計算する（幅 x 高さ &#x2192; 比率）</h2>

<div class="ar-card">
  <div class="ar-row">
    <div>
      <label for="ar-width">幅（px）</label>
      <input type="number" id="ar-width" placeholder="例: 1920" min="1">
    </div>
    <div>
      <label for="ar-height">高さ（px）</label>
      <input type="number" id="ar-height" placeholder="例: 1080" min="1">
    </div>
  </div>
  <button class="ar-btn" onclick="arCalcRatio()">アスペクト比を計算</button>
  <div class="ar-result" id="ar-ratio-result">幅と高さを入力して「計算」ボタンを押してください。</div>
</div>

<h2 class="ar-section-title">2. 比率でリサイズ（一辺 + 比率 &#x2192; もう一辺）</h2>

<div class="ar-card">
  <div class="ar-row">
    <div>
      <label for="ar-resize-w">幅（px）</label>
      <input type="number" id="ar-resize-w" placeholder="例: 1280" min="1">
    </div>
    <div>
      <label for="ar-resize-h">高さ（px）</label>
      <input type="number" id="ar-resize-h" placeholder="空欄で自動計算" min="1">
    </div>
    <div>
      <label for="ar-resize-rw">比率 W</label>
      <input type="number" id="ar-resize-rw" placeholder="例: 16" min="1" value="16">
    </div>
    <div>
      <label for="ar-resize-rh">比率 H</label>
      <input type="number" id="ar-resize-rh" placeholder="例: 9" min="1" value="9">
    </div>
  </div>
  <p style="font-size:12px;color:#64748b;margin:8px 0 0;">幅か高さのどちらか一方を入力し、もう一方を空欄にしてください。</p>
  <button class="ar-btn" onclick="arCalcResize()">もう一辺を計算</button>
  <div class="ar-result" id="ar-resize-result">一辺と比率を入力してください。</div>
</div>

<h2 class="ar-section-title">3. プリセットから選ぶ</h2>

<div class="ar-card">
  <p style="font-size:13px;color:#475569;margin:0 0 10px;">よく使われるアスペクト比をワンクリックで選択。プレビューに反映されます。</p>
  <div class="ar-preset-grid" id="ar-preset-grid"></div>
  <div class="ar-result" id="ar-preset-result" style="margin-top:14px;">プリセットを選択してください。</div>
</div>

<h2 class="ar-section-title">4. ビジュアルプレビュー</h2>

<div class="ar-card">
  <p style="font-size:13px;color:#475569;margin:0 0 10px;">上のセクションで計算・プリセット選択した比率がここに表示されます。</p>
  <div class="ar-canvas-wrap">
    <div class="ar-canvas-item">
      <canvas id="ar-preview-canvas" width="320" height="180"></canvas>
      <div class="ar-canvas-label" id="ar-preview-label">プレビュー</div>
    </div>
  </div>
</div>

<h2 class="ar-section-title">5. 比較モード（2つの比率を並列表示）</h2>

<div class="ar-card">
  <div class="ar-row">
    <div>
      <label>比率A — W</label>
      <input type="number" id="ar-cmp-aw" placeholder="例: 16" min="1" value="16">
    </div>
    <div>
      <label>比率A — H</label>
      <input type="number" id="ar-cmp-ah" placeholder="例: 9" min="1" value="9">
    </div>
    <div>
      <label>比率B — W</label>
      <input type="number" id="ar-cmp-bw" placeholder="例: 4" min="1" value="4">
    </div>
    <div>
      <label>比率B — H</label>
      <input type="number" id="ar-cmp-bh" placeholder="例: 3" min="1" value="3">
    </div>
  </div>
  <button class="ar-btn" onclick="arCompare()">比較する</button>
  <div id="ar-compare-output" style="display:none;">
    <div class="ar-canvas-wrap" style="margin-top:16px;">
      <div class="ar-canvas-item">
        <canvas id="ar-cmp-canvas-a" width="240" height="160"></canvas>
        <div class="ar-canvas-label" id="ar-cmp-label-a">比率A</div>
      </div>
      <div class="ar-canvas-item">
        <canvas id="ar-cmp-canvas-b" width="240" height="160"></canvas>
        <div class="ar-canvas-label" id="ar-cmp-label-b">比率B</div>
      </div>
    </div>
    <div class="ar-compare-flex" style="margin-top:10px;">
      <div class="ar-compare-box">
        <div class="ar-compare-ratio" id="ar-cmp-ratio-a">—</div>
        <div class="ar-compare-name">比率A（簡略）</div>
      </div>
      <div class="ar-compare-box">
        <div class="ar-compare-ratio" id="ar-cmp-ratio-b">—</div>
        <div class="ar-compare-name">比率B（簡略）</div>
      </div>
    </div>
  </div>
</div>

<h2 class="ar-section-title">6. 主な解像度とアスペクト比 一覧</h2>

<div class="ar-card" style="padding:14px 10px;">
  <table>
    <thead>
      <tr>
        <th>解像度</th>
        <th>アスペクト比</th>
        <th>主な用途</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>3840 &#xd7; 2160</td><td>16:9</td><td>4K UHD</td></tr>
      <tr><td>1920 &#xd7; 1080</td><td>16:9</td><td>Full HD / YouTube</td></tr>
      <tr><td>1280 &#xd7; 720</td><td>16:9</td><td>HD</td></tr>
      <tr><td>1280 &#xd7; 960</td><td>4:3</td><td>旧来のモニター・プレゼン</td></tr>
      <tr><td>1024 &#xd7; 768</td><td>4:3</td><td>XGA</td></tr>
      <tr><td>2560 &#xd7; 1080</td><td>21:9（64:27）</td><td>ウルトラワイドモニター</td></tr>
      <tr><td>3440 &#xd7; 1440</td><td>21:9（43:18）</td><td>ウルトラワイドQHD</td></tr>
      <tr><td>1080 &#xd7; 1080</td><td>1:1</td><td>Instagram正方形</td></tr>
      <tr><td>1080 &#xd7; 1920</td><td>9:16</td><td>TikTok / Instagram Stories</td></tr>
      <tr><td>1080 &#xd7; 1350</td><td>4:5</td><td>Instagram縦型</td></tr>
      <tr><td>6000 &#xd7; 4000</td><td>3:2</td><td>一眼レフカメラ</td></tr>
      <tr><td>4032 &#xd7; 3024</td><td>4:3</td><td>スマートフォンカメラ</td></tr>
      <tr><td>2560 &#xd7; 1600</td><td>16:10</td><td>MacBook / ノートPC</td></tr>
      <tr><td>1366 &#xd7; 768</td><td>16:9</td><td>一般的なラップトップ</td></tr>
    </tbody>
  </table>
</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す &#x2192;</a>
</div>

---

> 画像をリサイズ &#x2192; [画像リサイズツール](/ja/tools/image-resizer/)
> CSSアスペクト比を生成 &#x2192; [CSSアスペクト比計算ツール](/ja/tools/css-aspect-ratio/)
> ダミー画像を作成 &#x2192; [プレースホルダー画像生成ツール](/ja/tools/placeholder-image/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

<script>
(function () {
  /* ---------- Utility ---------- */
  function gcd(a, b) {
    a = Math.round(Math.abs(a));
    b = Math.round(Math.abs(b));
    while (b) { var t = b; b = a % b; a = t; }
    return a || 1;
  }
  function simplifyRatio(w, h) {
    var g = gcd(Math.round(w), Math.round(h));
    return [Math.round(w) / g, Math.round(h) / g];
  }

  /* ---------- 1. Calculate ratio ---------- */
  window.arCalcRatio = function () {
    var w = parseFloat(document.getElementById('ar-width').value);
    var h = parseFloat(document.getElementById('ar-height').value);
    var el = document.getElementById('ar-ratio-result');
    el.classList.remove('error');
    if (!w || !h || w <= 0 || h <= 0) {
      el.classList.add('error');
      el.textContent = '幅と高さに正の数値を入力してください。';
      return;
    }
    var r = simplifyRatio(w, h);
    var ratio = (w / h).toFixed(4);
    el.textContent = '比率: ' + r[0] + ':' + r[1] + '\u3000（小数: ' + ratio + '）\u3000入力: ' + w + ' \u00d7 ' + h;
    drawPreview(r[0], r[1], w + ' \u00d7 ' + h + ' \u2192 ' + r[0] + ':' + r[1]);
  };

  /* ---------- 2. Resize calc ---------- */
  window.arCalcResize = function () {
    var wVal = document.getElementById('ar-resize-w').value;
    var hVal = document.getElementById('ar-resize-h').value;
    var rw   = parseFloat(document.getElementById('ar-resize-rw').value);
    var rh   = parseFloat(document.getElementById('ar-resize-rh').value);
    var el   = document.getElementById('ar-resize-result');
    el.classList.remove('error');

    if (!rw || !rh || rw <= 0 || rh <= 0) {
      el.classList.add('error');
      el.textContent = '比率の W・H に正の数値を入力してください。';
      return;
    }
    var hasW = wVal !== '' && parseFloat(wVal) > 0;
    var hasH = hVal !== '' && parseFloat(hVal) > 0;

    if (hasW && !hasH) {
      var w = parseFloat(wVal);
      var h = Math.round(w * rh / rw);
      el.textContent = '計算結果: 幅 ' + w + 'px \u2192 高さ ' + h + 'px（比率 ' + rw + ':' + rh + '）';
      drawPreview(rw, rh, w + ' \u00d7 ' + h);
    } else if (!hasW && hasH) {
      var h2 = parseFloat(hVal);
      var w2 = Math.round(h2 * rw / rh);
      el.textContent = '計算結果: 高さ ' + h2 + 'px \u2192 幅 ' + w2 + 'px（比率 ' + rw + ':' + rh + '）';
      drawPreview(rw, rh, w2 + ' \u00d7 ' + h2);
    } else if (hasW && hasH) {
      el.classList.add('error');
      el.textContent = '幅か高さのどちらか一方だけを入力し、もう一方を空欄にしてください。';
    } else {
      el.classList.add('error');
      el.textContent = '幅か高さのいずれかに数値を入力してください。';
    }
  };

  /* ---------- 3. Presets ---------- */
  var presets = [
    { label: '16:9',  w: 16, h: 9,  desc: 'YouTube・テレビ・Full HD' },
    { label: '4:3',   w: 4,  h: 3,  desc: '旧来のモニター・プレゼン' },
    { label: '21:9',  w: 21, h: 9,  desc: 'ウルトラワイド・映画' },
    { label: '1:1',   w: 1,  h: 1,  desc: 'Instagram正方形' },
    { label: '9:16',  w: 9,  h: 16, desc: 'スマホ縦・TikTok・Stories' },
    { label: '3:2',   w: 3,  h: 2,  desc: '一眼レフカメラ' }
  ];

  var grid = document.getElementById('ar-preset-grid');
  presets.forEach(function (p) {
    var btn = document.createElement('button');
    btn.className = 'ar-preset-btn';
    btn.textContent = p.label;
    btn.addEventListener('click', function () {
      document.querySelectorAll('#ar-app .ar-preset-btn').forEach(function (b) { b.classList.remove('active'); });
      btn.classList.add('active');
      var el = document.getElementById('ar-preset-result');
      el.classList.remove('error');
      el.textContent = p.label + ' \u2014 ' + p.desc;
      drawPreview(p.w, p.h, p.label + '\u3000' + p.desc);
    });
    grid.appendChild(btn);
  });

  /* ---------- 4. Canvas preview ---------- */
  function drawPreview(rw, rh, labelText) {
    var canvas = document.getElementById('ar-preview-canvas');
    var ctx    = canvas.getContext('2d');
    var maxW   = 320, maxH = 220;
    var cw, ch;
    if (rw / rh >= maxW / maxH) {
      cw = maxW;
      ch = Math.round(maxW * rh / rw);
    } else {
      ch = maxH;
      cw = Math.round(maxH * rw / rh);
    }
    cw = Math.max(cw, 40);
    ch = Math.max(ch, 40);
    canvas.width  = cw;
    canvas.height = ch;

    var grad = ctx.createLinearGradient(0, 0, cw, ch);
    grad.addColorStop(0, '#334155');
    grad.addColorStop(1, '#64748b');
    ctx.fillStyle = grad;
    ctx.fillRect(0, 0, cw, ch);

    ctx.strokeStyle = 'rgba(255,255,255,0.1)';
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(0, 0);  ctx.lineTo(cw, ch);
    ctx.moveTo(cw, 0); ctx.lineTo(0, ch);
    ctx.stroke();

    var fontSize = Math.max(14, Math.min(Math.floor(cw / 5), 36));
    ctx.fillStyle    = '#fff';
    ctx.textAlign    = 'center';
    ctx.textBaseline = 'middle';
    ctx.font         = 'bold ' + fontSize + 'px sans-serif';
    ctx.fillText(rw + ':' + rh, cw / 2, ch / 2);

    ctx.font      = '11px sans-serif';
    ctx.fillStyle = 'rgba(255,255,255,0.55)';
    ctx.fillText(cw + ' \u00d7 ' + ch + ' px (preview)', cw / 2, ch - 10);

    document.getElementById('ar-preview-label').textContent = labelText || (rw + ':' + rh);
  }

  /* ---------- 5. Compare ---------- */
  window.arCompare = function () {
    var aw = parseFloat(document.getElementById('ar-cmp-aw').value);
    var ah = parseFloat(document.getElementById('ar-cmp-ah').value);
    var bw = parseFloat(document.getElementById('ar-cmp-bw').value);
    var bh = parseFloat(document.getElementById('ar-cmp-bh').value);

    if (!aw || !ah || !bw || !bh || aw <= 0 || ah <= 0 || bw <= 0 || bh <= 0) {
      alert('4つの値すべてに正の数値を入力してください。');
      return;
    }

    var ra = simplifyRatio(aw, ah);
    var rb = simplifyRatio(bw, bh);

    document.getElementById('ar-compare-output').style.display = 'block';
    document.getElementById('ar-cmp-ratio-a').textContent = ra[0] + ':' + ra[1];
    document.getElementById('ar-cmp-ratio-b').textContent = rb[0] + ':' + rb[1];

    drawCompareCanvas('ar-cmp-canvas-a', ra[0], ra[1], '#1e3a5f', '#3b82f6');
    document.getElementById('ar-cmp-label-a').textContent = '比率A: ' + ra[0] + ':' + ra[1];

    drawCompareCanvas('ar-cmp-canvas-b', rb[0], rb[1], '#3b1f5e', '#a855f7');
    document.getElementById('ar-cmp-label-b').textContent = '比率B: ' + rb[0] + ':' + rb[1];
  };

  function drawCompareCanvas(id, rw, rh, colorA, colorB) {
    var canvas = document.getElementById(id);
    var ctx    = canvas.getContext('2d');
    var maxW   = 240, maxH = 160;
    var cw, ch;
    if (rw / rh >= maxW / maxH) {
      cw = maxW;
      ch = Math.round(maxW * rh / rw);
    } else {
      ch = maxH;
      cw = Math.round(maxH * rw / rh);
    }
    canvas.width  = Math.max(cw, 40);
    canvas.height = Math.max(ch, 40);
    cw = canvas.width;
    ch = canvas.height;

    var grad = ctx.createLinearGradient(0, 0, cw, ch);
    grad.addColorStop(0, colorA);
    grad.addColorStop(1, colorB);
    ctx.fillStyle = grad;
    ctx.fillRect(0, 0, cw, ch);

    ctx.strokeStyle = 'rgba(255,255,255,0.1)';
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(0, 0);  ctx.lineTo(cw, ch);
    ctx.moveTo(cw, 0); ctx.lineTo(0, ch);
    ctx.stroke();

    var fontSize = Math.max(12, Math.min(Math.floor(cw / 5), 28));
    ctx.fillStyle    = '#fff';
    ctx.textAlign    = 'center';
    ctx.textBaseline = 'middle';
    ctx.font         = 'bold ' + fontSize + 'px sans-serif';
    ctx.fillText(rw + ':' + rh, cw / 2, ch / 2);
  }

  /* ---------- Initial render ---------- */
  drawPreview(16, 9, '16:9\u3000YouTube\u30fbFull HD\u30fbTV');
})();
</script>

</div>
