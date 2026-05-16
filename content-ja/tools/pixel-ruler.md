---
title: "ピクセル定規ツール — 無料オンライン画面計測"
date: 2025-05-16
description: "画面上でドラッグしてピクセル・cm・インチ単位で距離を計測。カーソル座標トラッカー、DPI検出、定規の長さ・色をカスタマイズ可能。インストール不要。"
categories: ["無料ツール"]
slug: "pixel-ruler"
ShowToc: false
aliases:
  - "/ja/tools/pixel-ruler/"
  - "/ja/tools/pixel-ruler/"
cover:
  image: "/images/covers/pixel-ruler-ja.png"
  alt: "ピクセル定規ツール"
---

画面上でドラッグして距離を計測。カーソルの正確な座標をリアルタイム追跡し、画面DPIを自動検出。定規の色・長さを自由にカスタマイズできます。インストール不要で今すぐ使えます。

<div id="pr-app">

<style>
/* ── Reset ──────────────────────────────────────────────────── */
#pr-app *, #pr-app *::before, #pr-app *::after {
  box-sizing: border-box; margin: 0; padding: 0;
}
#pr-app {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
  color: #1a1a2e;
  line-height: 1.5;
  user-select: none;
}

/* ── Controls bar ───────────────────────────────────────────── */
#pr-app .pr-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  background: #f8f9fc;
  border: 1px solid #e2e6f0;
  border-radius: 12px;
  padding: 14px 16px;
  margin-bottom: 16px;
}
#pr-app .pr-ctrl-group {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: #374151;
}
#pr-app .pr-ctrl-group label {
  font-weight: 600;
  white-space: nowrap;
}
#pr-app .pr-ctrl-group input[type="range"] {
  width: 100px;
  accent-color: #6366f1;
}
#pr-app .pr-ctrl-group input[type="color"] {
  width: 34px;
  height: 30px;
  border: 1.5px solid #d1d5db;
  border-radius: 6px;
  cursor: pointer;
  padding: 2px;
  background: #fff;
}
#pr-app .pr-ctrl-group select {
  border: 1px solid #d1d5db;
  border-radius: 6px;
  padding: 5px 8px;
  font-size: 13px;
  background: #fff;
  cursor: pointer;
  outline: none;
}
#pr-app .pr-ctrl-group select:focus { border-color: #6366f1; }
#pr-app .pr-sep {
  width: 1px;
  height: 28px;
  background: #e2e6f0;
}

/* ── DPI info ───────────────────────────────────────────────── */
#pr-app .pr-dpi-badge {
  font-size: 12px;
  background: #eef2ff;
  color: #4338ca;
  padding: 3px 10px;
  border-radius: 20px;
  font-weight: 600;
  border: 1px solid #c7d2fe;
}

/* ── Canvas area ────────────────────────────────────────────── */
#pr-app .pr-canvas-wrap {
  position: relative;
  background: #fff;
  border: 1px solid #e2e6f0;
  border-radius: 12px;
  overflow: hidden;
  height: 380px;
  cursor: crosshair;
}

/* ── Coordinate display ─────────────────────────────────────── */
#pr-app .pr-coords {
  position: absolute;
  top: 10px;
  right: 14px;
  background: rgba(15,23,42,.82);
  color: #f8fafc;
  font-size: 12px;
  font-family: monospace;
  padding: 6px 12px;
  border-radius: 6px;
  pointer-events: none;
  z-index: 10;
  white-space: nowrap;
}

/* ── Measurement label ──────────────────────────────────────── */
#pr-app .pr-measure-label {
  position: absolute;
  background: rgba(15,23,42,.82);
  color: #f8fafc;
  font-size: 12px;
  font-family: monospace;
  padding: 4px 10px;
  border-radius: 6px;
  pointer-events: none;
  z-index: 10;
  white-space: nowrap;
}

/* ── Canvas ─────────────────────────────────────────────────── */
#pr-app canvas {
  display: block;
  width: 100%;
  height: 100%;
}

/* ── Info row ───────────────────────────────────────────────── */
#pr-app .pr-info-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 14px;
}
#pr-app .pr-info-card {
  flex: 1;
  min-width: 140px;
  background: #f8f9fc;
  border: 1px solid #e2e6f0;
  border-radius: 10px;
  padding: 14px 16px;
}
#pr-app .pr-info-card .pr-ic-label {
  font-size: 11px;
  color: #6b7280;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: .07em;
  margin-bottom: 4px;
}
#pr-app .pr-info-card .pr-ic-val {
  font-size: 20px;
  font-weight: 800;
  color: #1a1a2e;
  font-family: monospace;
}
#pr-app .pr-info-card .pr-ic-sub {
  font-size: 11px;
  color: #6b7280;
  margin-top: 2px;
}

/* ── Instructions ───────────────────────────────────────────── */
#pr-app .pr-hint {
  font-size: 12px;
  color: #6b7280;
  margin-top: 10px;
  padding: 10px 14px;
  background: #f8f9fc;
  border-radius: 8px;
  border-left: 3px solid #6366f1;
}

/* ── Buttons ────────────────────────────────────────────────── */
#pr-app .pr-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 7px 14px;
  border-radius: 7px;
  border: 1.5px solid #d1d5db;
  background: #fff;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  color: #374151;
  transition: background .15s;
}
#pr-app .pr-btn:hover { background: #f3f4f6; }
#pr-app .pr-btn-primary {
  background: #6366f1;
  color: #fff;
  border-color: #6366f1;
}
#pr-app .pr-btn-primary:hover { background: #4f46e5; }
</style>

<!-- コントロール -->
<div class="pr-controls">
  <div class="pr-ctrl-group">
    <label>向き:</label>
    <select id="pr-orient">
      <option value="h">水平</option>
      <option value="v">垂直</option>
      <option value="both">両方</option>
    </select>
  </div>
  <div class="pr-sep"></div>
  <div class="pr-ctrl-group">
    <label>長さ:</label>
    <input type="range" id="pr-length" min="100" max="900" value="500">
    <span id="pr-length-lbl">500 px</span>
  </div>
  <div class="pr-sep"></div>
  <div class="pr-ctrl-group">
    <label>色:</label>
    <input type="color" id="pr-color" value="#6366f1">
  </div>
  <div class="pr-sep"></div>
  <div class="pr-ctrl-group">
    <label>単位:</label>
    <select id="pr-unit">
      <option value="px">px</option>
      <option value="cm">cm</option>
      <option value="in">インチ</option>
    </select>
  </div>
  <div class="pr-sep"></div>
  <span class="pr-dpi-badge" id="pr-dpi-badge">DPI: 検出中…</span>
  <button class="pr-btn pr-btn-primary" id="pr-reset-btn">リセット</button>
</div>

<!-- キャンバスエリア -->
<div class="pr-canvas-wrap" id="pr-canvas-wrap">
  <canvas id="pr-canvas"></canvas>
  <div class="pr-coords" id="pr-coords">x: 0 　 y: 0</div>
  <div class="pr-measure-label" id="pr-meas-label" style="display:none;"></div>
</div>

<!-- 計測結果 -->
<div class="pr-info-row">
  <div class="pr-info-card">
    <div class="pr-ic-label">計測距離</div>
    <div class="pr-ic-val" id="pr-val-px">—</div>
    <div class="pr-ic-sub">ピクセル</div>
  </div>
  <div class="pr-info-card">
    <div class="pr-ic-label">センチメートル</div>
    <div class="pr-ic-val" id="pr-val-cm">—</div>
    <div class="pr-ic-sub">cm</div>
  </div>
  <div class="pr-info-card">
    <div class="pr-ic-label">インチ</div>
    <div class="pr-ic-val" id="pr-val-in">—</div>
    <div class="pr-ic-sub">in</div>
  </div>
  <div class="pr-info-card">
    <div class="pr-ic-label">画面 DPI</div>
    <div class="pr-ic-val" id="pr-val-dpi">—</div>
    <div class="pr-ic-sub">dots per inch</div>
  </div>
</div>

<p class="pr-hint">
  <strong>使い方:</strong> マウスを動かすと座標をリアルタイム表示。エリア内でドラッグすると距離を計測。定規の向き・長さ・色・単位を上部で変更できます。タッチ操作にも対応しています。
</p>

<script>
(function () {
  'use strict';

  /* ── DPI検出 ─────────────────────────────────────────────── */
  function detectDPI() {
    var dpi = 96;
    var queries = [72,96,120,144,160,192,216,240,288,320];
    for (var i = queries.length - 1; i >= 0; i--) {
      if (window.matchMedia('(min-resolution: ' + queries[i] + 'dpi)').matches) {
        dpi = queries[i];
        break;
      }
    }
    if (window.devicePixelRatio) {
      var ratioDpi = Math.round(96 * window.devicePixelRatio);
      dpi = Math.max(dpi, ratioDpi);
    }
    return dpi;
  }

  var DPI = detectDPI();
  document.getElementById('pr-dpi-badge').textContent = 'DPI: ' + DPI;
  document.getElementById('pr-val-dpi').textContent = DPI;

  /* ── 状態 ────────────────────────────────────────────────── */
  var rulerColor   = '#6366f1';
  var rulerLength  = 500;
  var orientation  = 'h';
  var unit         = 'px';
  var mouseX       = 0;
  var mouseY       = 0;
  var dragStart    = null;
  var dragEnd      = null;
  var isDragging   = false;
  var rulerX       = 40;
  var rulerY       = 40;
  var draggingRuler = false;
  var rulerDragOff  = {x:0, y:0};

  /* ── DOM ─────────────────────────────────────────────────── */
  var wrap       = document.getElementById('pr-canvas-wrap');
  var canvas     = document.getElementById('pr-canvas');
  var ctx        = canvas.getContext('2d');
  var elCoords   = document.getElementById('pr-coords');
  var elMeasLbl  = document.getElementById('pr-meas-label');
  var elValPx    = document.getElementById('pr-val-px');
  var elValCm    = document.getElementById('pr-val-cm');
  var elValIn    = document.getElementById('pr-val-in');
  var elOrient   = document.getElementById('pr-orient');
  var elLength   = document.getElementById('pr-length');
  var elLenLbl   = document.getElementById('pr-length-lbl');
  var elColor    = document.getElementById('pr-color');
  var elUnit     = document.getElementById('pr-unit');
  var elResetBtn = document.getElementById('pr-reset-btn');

  /* ── キャンバスリサイズ ──────────────────────────────────── */
  function resizeCanvas() {
    canvas.width  = wrap.clientWidth;
    canvas.height = wrap.clientHeight;
    draw();
  }

  /* ── 単位変換 ────────────────────────────────────────────── */
  function pxTo(px, u) {
    if (u === 'cm') return (px / DPI * 2.54).toFixed(2);
    if (u === 'in') return (px / DPI).toFixed(3);
    return Math.round(px);
  }

  /* ── 定規描画 ────────────────────────────────────────────── */
  function drawRuler(x, y, len, isHoriz) {
    ctx.save();
    ctx.strokeStyle = rulerColor;
    ctx.fillStyle   = rulerColor;
    ctx.lineWidth   = 2;
    ctx.font        = '10px monospace';
    ctx.textAlign   = 'center';

    ctx.beginPath();
    if (isHoriz) {
      ctx.moveTo(x, y);
      ctx.lineTo(x + len, y);
    } else {
      ctx.moveTo(x, y);
      ctx.lineTo(x, y + len);
    }
    ctx.stroke();

    for (var i = 0; i <= len; i++) {
      var tickLen;
      if (i % 100 === 0) tickLen = 16;
      else if (i % 50 === 0) tickLen = 10;
      else if (i % 10 === 0) tickLen = 6;
      else continue;

      ctx.beginPath();
      if (isHoriz) {
        ctx.moveTo(x + i, y - tickLen);
        ctx.lineTo(x + i, y + tickLen);
      } else {
        ctx.moveTo(x - tickLen, y + i);
        ctx.lineTo(x + tickLen, y + i);
      }
      ctx.stroke();

      if (i % 100 === 0 && i > 0) {
        var labelTxt = pxTo(i, unit).toString();
        ctx.save();
        if (isHoriz) {
          ctx.fillText(labelTxt, x + i, y - 20);
        } else {
          ctx.save();
          ctx.translate(x - 22, y + i);
          ctx.rotate(-Math.PI / 2);
          ctx.fillText(labelTxt, 0, 0);
          ctx.restore();
        }
        ctx.restore();
      }
    }

    ctx.beginPath();
    if (isHoriz) {
      ctx.moveTo(x, y - 16); ctx.lineTo(x, y + 16);
      ctx.moveTo(x + len, y - 16); ctx.lineTo(x + len, y + 16);
    } else {
      ctx.moveTo(x - 16, y); ctx.lineTo(x + 16, y);
      ctx.moveTo(x - 16, y + len); ctx.lineTo(x + 16, y + len);
    }
    ctx.stroke();

    ctx.restore();
  }

  /* ── クロスヘア描画 ──────────────────────────────────────── */
  function drawCrosshair(x, y) {
    ctx.save();
    ctx.strokeStyle = 'rgba(99,102,241,0.5)';
    ctx.lineWidth = 1;
    ctx.setLineDash([4, 4]);
    ctx.beginPath();
    ctx.moveTo(x, 0); ctx.lineTo(x, canvas.height);
    ctx.moveTo(0, y); ctx.lineTo(canvas.width, y);
    ctx.stroke();
    ctx.restore();
  }

  /* ── 計測線描画 ──────────────────────────────────────────── */
  function drawMeasurement() {
    if (!dragStart || !dragEnd) return;
    var x1 = dragStart.x, y1 = dragStart.y;
    var x2 = dragEnd.x,   y2 = dragEnd.y;

    ctx.save();
    ctx.strokeStyle = '#ef4444';
    ctx.lineWidth = 2;
    ctx.setLineDash([]);

    ctx.beginPath();
    ctx.moveTo(x1, y1);
    ctx.lineTo(x2, y2);
    ctx.stroke();

    [dragStart, dragEnd].forEach(function (pt) {
      ctx.beginPath();
      ctx.arc(pt.x, pt.y, 5, 0, Math.PI * 2);
      ctx.fillStyle = '#ef4444';
      ctx.fill();
    });

    var dx = x2 - x1, dy = y2 - y1;
    var dist = Math.sqrt(dx*dx + dy*dy);
    var midX = (x1 + x2) / 2;
    var midY = (y1 + y2) / 2;

    var distPx = Math.round(dist);
    elValPx.textContent = distPx + ' px';
    elValCm.textContent = (distPx / DPI * 2.54).toFixed(2) + ' cm';
    elValIn.textContent = (distPx / DPI).toFixed(3) + ' in';

    var unitLabel = unit === 'px' ? ' px' : unit === 'cm' ? ' cm' : ' in';
    var labelTxt = pxTo(dist, unit) + unitLabel;
    elMeasLbl.style.display = 'block';
    elMeasLbl.textContent = labelTxt;
    elMeasLbl.style.left = (midX + 8) + 'px';
    elMeasLbl.style.top  = (midY - 14) + 'px';

    ctx.restore();
  }

  /* ── メイン描画 ──────────────────────────────────────────── */
  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    ctx.save();
    ctx.strokeStyle = 'rgba(226,230,240,0.6)';
    ctx.lineWidth = 1;
    for (var gx = 0; gx < canvas.width; gx += 50) {
      ctx.beginPath(); ctx.moveTo(gx, 0); ctx.lineTo(gx, canvas.height); ctx.stroke();
    }
    for (var gy = 0; gy < canvas.height; gy += 50) {
      ctx.beginPath(); ctx.moveTo(0, gy); ctx.lineTo(canvas.width, gy); ctx.stroke();
    }
    ctx.restore();

    if (orientation === 'h' || orientation === 'both') {
      drawRuler(rulerX, rulerY, rulerLength, true);
    }
    if (orientation === 'v' || orientation === 'both') {
      var vx = orientation === 'both' ? rulerX + rulerLength + 30 : rulerX;
      drawRuler(vx, rulerY, rulerLength, false);
    }

    drawCrosshair(mouseX, mouseY);
    drawMeasurement();
  }

  /* ── キャンバス座標変換 ──────────────────────────────────── */
  function canvasPos(e) {
    var r = canvas.getBoundingClientRect();
    var cx = e.clientX - r.left;
    var cy = e.clientY - r.top;
    return {
      x: cx * (canvas.width / r.width),
      y: cy * (canvas.height / r.height)
    };
  }

  /* ── マウスイベント ──────────────────────────────────────── */
  wrap.addEventListener('mousemove', function (e) {
    var pos = canvasPos(e);
    mouseX = pos.x;
    mouseY = pos.y;
    elCoords.textContent = 'x: ' + Math.round(mouseX) + ' 　 y: ' + Math.round(mouseY);
    if (isDragging) dragEnd = pos;
    if (draggingRuler) { rulerX = pos.x - rulerDragOff.x; rulerY = pos.y - rulerDragOff.y; }
    draw();
  });

  wrap.addEventListener('mousedown', function (e) {
    var pos = canvasPos(e);
    var onRuler = false;
    if (orientation === 'h' || orientation === 'both') {
      if (Math.abs(pos.y - rulerY) < 20 && pos.x >= rulerX - 10 && pos.x <= rulerX + rulerLength + 10) onRuler = true;
    }
    if (onRuler && e.altKey) {
      draggingRuler = true;
      rulerDragOff = { x: pos.x - rulerX, y: pos.y - rulerY };
    } else {
      isDragging = true;
      dragStart = pos;
      dragEnd   = pos;
      elMeasLbl.style.display = 'none';
    }
    e.preventDefault();
  });

  wrap.addEventListener('mouseup', function () { isDragging = false; draggingRuler = false; });
  wrap.addEventListener('mouseleave', function () { isDragging = false; draggingRuler = false; });

  /* ── タッチ対応 ──────────────────────────────────────────── */
  function touchPos(e) { return canvasPos(e.touches[0] || e.changedTouches[0]); }

  wrap.addEventListener('touchstart', function (e) {
    var pos = touchPos(e);
    isDragging = true;
    dragStart = pos; dragEnd = pos;
    e.preventDefault();
  }, {passive: false});

  wrap.addEventListener('touchmove', function (e) {
    var pos = touchPos(e);
    mouseX = pos.x; mouseY = pos.y;
    if (isDragging) dragEnd = pos;
    elCoords.textContent = 'x: ' + Math.round(mouseX) + ' 　 y: ' + Math.round(mouseY);
    draw();
    e.preventDefault();
  }, {passive: false});

  wrap.addEventListener('touchend', function () { isDragging = false; });

  /* ── コントロール ────────────────────────────────────────── */
  elOrient.addEventListener('change', function () { orientation = elOrient.value; draw(); });

  elLength.addEventListener('input', function () {
    rulerLength = parseInt(elLength.value, 10);
    elLenLbl.textContent = rulerLength + ' px';
    draw();
  });

  elColor.addEventListener('input', function () { rulerColor = elColor.value; draw(); });
  elUnit.addEventListener('change', function () { unit = elUnit.value; draw(); });

  elResetBtn.addEventListener('click', function () {
    rulerX = 40; rulerY = 40;
    rulerLength = 500; rulerColor = '#6366f1'; orientation = 'h'; unit = 'px';
    dragStart = null; dragEnd = null;
    elOrient.value = 'h'; elLength.value = 500; elLenLbl.textContent = '500 px';
    elColor.value = '#6366f1'; elUnit.value = 'px';
    elMeasLbl.style.display = 'none';
    elValPx.textContent = '—'; elValCm.textContent = '—'; elValIn.textContent = '—';
    draw();
  });

  /* ── 初期化 ──────────────────────────────────────────────── */
  resizeCanvas();
  window.addEventListener('resize', resizeCanvas);
  draw();
})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

> 画面解像度確認 → [画面解像度ツール](/ja/tools/screen-resolution/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
