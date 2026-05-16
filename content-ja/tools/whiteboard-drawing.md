---
title: "ホワイトボードお絵かきツール"
date: 2025-05-16
description: "無料のオンラインホワイトボード。ペン・図形・テキストで自由に描画。PNG保存対応、タッチ操作可能、会員登録不要。"
categories: ["無料ツール"]
slug: "whiteboard-drawing"
ShowToc: false
cover:
  image: "/images/covers/whiteboard-drawing-ja.png"
  alt: "ホワイトボードお絵かきツール"
---

<div id="wb-app">
<style>
#wb-app *,
#wb-app *::before,
#wb-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#wb-app {
  font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  color: #1e293b;
  background: #f8fafc;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 24px rgba(0,0,0,0.10);
}
#wb-toolbar {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 8px;
  padding: 10px 14px;
  background: #1e293b;
  border-bottom: 2px solid #334155;
}
#wb-toolbar .wb-group {
  display: flex;
  align-items: center;
  gap: 6px;
  flex-wrap: wrap;
}
#wb-toolbar .wb-separator {
  width: 1px;
  height: 28px;
  background: #475569;
  margin: 0 2px;
}
#wb-app button.wb-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 4px;
  padding: 6px 11px;
  border: 1.5px solid #475569;
  border-radius: 6px;
  background: #334155;
  color: #cbd5e1;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s, color 0.15s;
  white-space: nowrap;
  line-height: 1.2;
}
#wb-app button.wb-btn:hover {
  background: #475569;
  color: #f1f5f9;
  border-color: #64748b;
}
#wb-app button.wb-btn.active {
  background: #0284c7;
  border-color: #0ea5e9;
  color: #fff;
}
#wb-app button.wb-btn:disabled {
  opacity: 0.35;
  cursor: not-allowed;
}
#wb-color-input {
  width: 34px;
  height: 30px;
  border: 1.5px solid #475569;
  border-radius: 6px;
  padding: 2px;
  background: #1e293b;
  cursor: pointer;
}
#wb-app label.wb-label {
  font-size: 12px;
  color: #94a3b8;
  white-space: nowrap;
}
#wb-size-slider {
  -webkit-appearance: none;
  appearance: none;
  width: 90px;
  height: 4px;
  border-radius: 2px;
  background: #475569;
  outline: none;
  cursor: pointer;
}
#wb-size-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #0ea5e9;
  cursor: pointer;
  border: 2px solid #fff;
}
#wb-size-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #0ea5e9;
  cursor: pointer;
  border: 2px solid #fff;
}
#wb-size-val {
  font-size: 12px;
  color: #94a3b8;
  min-width: 26px;
  text-align: right;
}
#wb-canvas-wrap {
  width: 100%;
  overflow: hidden;
  background: #fff;
  cursor: crosshair;
  position: relative;
}
#wb-canvas {
  display: block;
  width: 100%;
  height: 100%;
  touch-action: none;
}
#wb-text-input-overlay {
  display: none;
  position: absolute;
  z-index: 10;
  border: 2px dashed #0284c7;
  background: rgba(255,255,255,0.92);
  padding: 2px 4px;
  font-size: 16px;
  outline: none;
  min-width: 80px;
  min-height: 28px;
  color: #1e293b;
  border-radius: 3px;
  resize: none;
  overflow: hidden;
  line-height: 1.4;
}
#wb-status-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5px 14px;
  background: #0f172a;
  font-size: 11px;
  color: #64748b;
  min-height: 26px;
}
#wb-status-bar span {
  user-select: none;
}
@media (max-width: 600px) {
  #wb-toolbar {
    padding: 8px 8px;
    gap: 5px;
  }
  #wb-app button.wb-btn {
    font-size: 12px;
    padding: 5px 8px;
  }
  #wb-size-slider {
    width: 64px;
  }
}
</style>

<div id="wb-toolbar">
  <!-- ツール選択 -->
  <div class="wb-group">
    <button class="wb-btn active" id="wb-tool-pen" title="ペン">&#9998; ペン</button>
    <button class="wb-btn" id="wb-tool-line" title="直線">&#8212; 直線</button>
    <button class="wb-btn" id="wb-tool-rect" title="四角">&#9645; 四角</button>
    <button class="wb-btn" id="wb-tool-circle" title="円">&#9711; 円</button>
    <button class="wb-btn" id="wb-tool-text" title="テキスト">&#65332; テキスト</button>
    <button class="wb-btn" id="wb-tool-eraser" title="消しゴム">&#9003; 消しゴム</button>
  </div>
  <div class="wb-separator"></div>
  <!-- 色・太さ -->
  <div class="wb-group">
    <label class="wb-label" for="wb-color-input">色</label>
    <input type="color" id="wb-color-input" value="#1e293b" title="描画色">
    <label class="wb-label" for="wb-size-slider">太さ</label>
    <input type="range" id="wb-size-slider" min="1" max="20" value="3">
    <span id="wb-size-val">3px</span>
  </div>
  <div class="wb-separator"></div>
  <!-- 操作 -->
  <div class="wb-group">
    <button class="wb-btn" id="wb-undo-btn" title="元に戻す (Ctrl+Z)">&#8592; 戻す</button>
    <button class="wb-btn" id="wb-redo-btn" title="やり直し (Ctrl+Y)">やり直し &#8594;</button>
    <button class="wb-btn" id="wb-clear-btn" title="クリア">&#128465; クリア</button>
    <button class="wb-btn" id="wb-download-btn" title="PNGとして保存">&#11015; PNG保存</button>
  </div>
</div>

<div id="wb-canvas-wrap">
  <canvas id="wb-canvas"></canvas>
  <textarea id="wb-text-input-overlay" rows="1" placeholder="テキストを入力..."></textarea>
</div>

<div id="wb-status-bar">
  <span id="wb-coords">X: 0 &nbsp; Y: 0</span>
  <span id="wb-tool-name">ツール: ペン</span>
</div>

<script>
(function() {
  var canvas = document.getElementById('wb-canvas');
  var ctx = canvas.getContext('2d');
  var wrap = document.getElementById('wb-canvas-wrap');
  var textOverlay = document.getElementById('wb-text-input-overlay');
  var coordsEl = document.getElementById('wb-coords');
  var toolNameEl = document.getElementById('wb-tool-name');
  var colorInput = document.getElementById('wb-color-input');
  var sizeSlider = document.getElementById('wb-size-slider');
  var sizeVal = document.getElementById('wb-size-val');

  var CANVAS_H = 620;
  var currentTool = 'pen';
  var isDrawing = false;
  var startX = 0, startY = 0;
  var lastX = 0, lastY = 0;
  var undoStack = [];
  var redoStack = [];
  var MAX_HISTORY = 40;
  var snapshot = null; // for shape preview
  var textPos = {x: 0, y: 0};

  var toolNames = {
    pen: 'ペン',
    line: '直線',
    rect: '四角',
    circle: '円',
    text: 'テキスト',
    eraser: '消しゴム'
  };

  // ---- Canvas sizing ----
  function resizeCanvas() {
    var w = wrap.clientWidth;
    var imageData = null;
    if (canvas.width > 0 && canvas.height > 0) {
      imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
    }
    canvas.width = w;
    canvas.height = CANVAS_H;
    fillWhite();
    if (imageData) {
      ctx.putImageData(imageData, 0, 0);
    }
  }

  function fillWhite() {
    ctx.fillStyle = '#ffffff';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
  }

  resizeCanvas();
  window.addEventListener('resize', function() { resizeCanvas(); });

  // ---- Tool buttons ----
  var toolBtns = {
    pen: document.getElementById('wb-tool-pen'),
    line: document.getElementById('wb-tool-line'),
    rect: document.getElementById('wb-tool-rect'),
    circle: document.getElementById('wb-tool-circle'),
    text: document.getElementById('wb-tool-text'),
    eraser: document.getElementById('wb-tool-eraser')
  };

  Object.keys(toolBtns).forEach(function(t) {
    toolBtns[t].addEventListener('click', function() {
      commitTextInput();
      setTool(t);
    });
  });

  function setTool(t) {
    currentTool = t;
    Object.keys(toolBtns).forEach(function(k) {
      toolBtns[k].classList.toggle('active', k === t);
    });
    toolNameEl.textContent = 'ツール: ' + (toolNames[t] || t);
    wrap.style.cursor = (t === 'text') ? 'text' : 'crosshair';
  }

  // ---- Color & size ----
  colorInput.addEventListener('input', function() { commitTextInput(); });
  sizeSlider.addEventListener('input', function() {
    sizeVal.textContent = sizeSlider.value + 'px';
  });

  function getColor() { return colorInput.value; }
  function getSize() { return parseInt(sizeSlider.value, 10); }

  // ---- Undo / Redo ----
  function saveState() {
    var data = canvas.toDataURL();
    undoStack.push(data);
    if (undoStack.length > MAX_HISTORY) undoStack.shift();
    redoStack = [];
    updateUndoRedoBtns();
  }

  function updateUndoRedoBtns() {
    document.getElementById('wb-undo-btn').disabled = undoStack.length === 0;
    document.getElementById('wb-redo-btn').disabled = redoStack.length === 0;
  }

  function restoreState(dataUrl) {
    var img = new Image();
    img.onload = function() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.drawImage(img, 0, 0);
    };
    img.src = dataUrl;
  }

  document.getElementById('wb-undo-btn').addEventListener('click', function() {
    if (undoStack.length === 0) return;
    redoStack.push(canvas.toDataURL());
    restoreState(undoStack.pop());
    updateUndoRedoBtns();
  });

  document.getElementById('wb-redo-btn').addEventListener('click', function() {
    if (redoStack.length === 0) return;
    undoStack.push(canvas.toDataURL());
    restoreState(redoStack.pop());
    updateUndoRedoBtns();
  });

  updateUndoRedoBtns();

  // Keyboard shortcuts
  document.addEventListener('keydown', function(e) {
    if (e.target === textOverlay) return;
    if ((e.ctrlKey || e.metaKey) && e.key === 'z') {
      e.preventDefault();
      document.getElementById('wb-undo-btn').click();
    }
    if ((e.ctrlKey || e.metaKey) && (e.key === 'y' || (e.shiftKey && e.key === 'z'))) {
      e.preventDefault();
      document.getElementById('wb-redo-btn').click();
    }
  });

  // ---- Clear ----
  document.getElementById('wb-clear-btn').addEventListener('click', function() {
    commitTextInput();
    saveState();
    fillWhite();
  });

  // ---- Download ----
  document.getElementById('wb-download-btn').addEventListener('click', function() {
    commitTextInput();
    var a = document.createElement('a');
    a.download = 'whiteboard-' + Date.now() + '.png';
    a.href = canvas.toDataURL('image/png');
    a.click();
  });

  // ---- Pointer helpers ----
  function getPos(e) {
    var rect = canvas.getBoundingClientRect();
    var scaleX = canvas.width / rect.width;
    var scaleY = canvas.height / rect.height;
    var clientX, clientY;
    if (e.touches && e.touches.length > 0) {
      clientX = e.touches[0].clientX;
      clientY = e.touches[0].clientY;
    } else if (e.changedTouches && e.changedTouches.length > 0) {
      clientX = e.changedTouches[0].clientX;
      clientY = e.changedTouches[0].clientY;
    } else {
      clientX = e.clientX;
      clientY = e.clientY;
    }
    return {
      x: Math.round((clientX - rect.left) * scaleX),
      y: Math.round((clientY - rect.top) * scaleY)
    };
  }

  // ---- Drawing context setup ----
  function setupCtx(erase) {
    ctx.lineCap = 'round';
    ctx.lineJoin = 'round';
    if (erase) {
      ctx.globalCompositeOperation = 'destination-out';
      ctx.strokeStyle = 'rgba(0,0,0,1)';
      ctx.lineWidth = getSize() * 4;
    } else {
      ctx.globalCompositeOperation = 'source-over';
      ctx.strokeStyle = getColor();
      ctx.fillStyle = getColor();
      ctx.lineWidth = getSize();
    }
  }

  // ---- Text input overlay ----
  function showTextInput(x, y) {
    var rect = canvas.getBoundingClientRect();
    var scaleX = rect.width / canvas.width;
    var scaleY = rect.height / canvas.height;
    textPos = {x: x, y: y};
    textOverlay.style.left = Math.round(x * scaleX) + 'px';
    textOverlay.style.top = Math.round(y * scaleY - 4) + 'px';
    textOverlay.style.display = 'block';
    textOverlay.style.fontSize = Math.max(12, getSize() * 3) + 'px';
    textOverlay.style.color = getColor();
    textOverlay.value = '';
    textOverlay.focus();
  }

  function commitTextInput() {
    if (textOverlay.style.display === 'none') return;
    var text = textOverlay.value.trim();
    if (text) {
      saveState();
      ctx.globalCompositeOperation = 'source-over';
      ctx.fillStyle = getColor();
      ctx.font = Math.max(14, getSize() * 3) + 'px sans-serif';
      ctx.textBaseline = 'top';
      var lines = text.split('\n');
      var lineH = Math.max(14, getSize() * 3) * 1.4;
      lines.forEach(function(line, i) {
        ctx.fillText(line, textPos.x, textPos.y + i * lineH);
      });
    }
    textOverlay.style.display = 'none';
    textOverlay.value = '';
  }

  textOverlay.addEventListener('keydown', function(e) {
    if (e.key === 'Escape') {
      textOverlay.style.display = 'none';
      textOverlay.value = '';
    }
    if (e.key === 'Enter' && !e.shiftKey) {
      e.preventDefault();
      commitTextInput();
    }
  });

  // ---- Draw shapes ----
  function drawShape(x0, y0, x1, y1) {
    if (snapshot) ctx.putImageData(snapshot, 0, 0);
    setupCtx(false);
    ctx.beginPath();
    if (currentTool === 'line') {
      ctx.moveTo(x0, y0);
      ctx.lineTo(x1, y1);
      ctx.stroke();
    } else if (currentTool === 'rect') {
      ctx.strokeRect(x0, y0, x1 - x0, y1 - y0);
    } else if (currentTool === 'circle') {
      var rx = (x1 - x0) / 2;
      var ry = (y1 - y0) / 2;
      var cx = x0 + rx;
      var cy = y0 + ry;
      ctx.ellipse(cx, cy, Math.abs(rx), Math.abs(ry), 0, 0, 2 * Math.PI);
      ctx.stroke();
    }
  }

  // ---- Mouse events ----
  function onStart(e) {
    e.preventDefault();
    commitTextInput();
    var pos = getPos(e);
    if (currentTool === 'text') {
      showTextInput(pos.x, pos.y);
      return;
    }
    isDrawing = true;
    startX = pos.x;
    startY = pos.y;
    lastX = pos.x;
    lastY = pos.y;
    saveState();
    if (currentTool === 'line' || currentTool === 'rect' || currentTool === 'circle') {
      snapshot = ctx.getImageData(0, 0, canvas.width, canvas.height);
    }
    if (currentTool === 'pen' || currentTool === 'eraser') {
      setupCtx(currentTool === 'eraser');
      ctx.beginPath();
      ctx.moveTo(pos.x, pos.y);
    }
  }

  function onMove(e) {
    e.preventDefault();
    var pos = getPos(e);
    coordsEl.textContent = 'X: ' + pos.x + ' \u00a0 Y: ' + pos.y;
    if (!isDrawing) return;
    if (currentTool === 'pen' || currentTool === 'eraser') {
      setupCtx(currentTool === 'eraser');
      ctx.lineTo(pos.x, pos.y);
      ctx.stroke();
      ctx.beginPath();
      ctx.moveTo(pos.x, pos.y);
    } else if (currentTool === 'line' || currentTool === 'rect' || currentTool === 'circle') {
      drawShape(startX, startY, pos.x, pos.y);
    }
    lastX = pos.x;
    lastY = pos.y;
  }

  function onEnd(e) {
    if (!isDrawing) return;
    e.preventDefault();
    if (currentTool === 'line' || currentTool === 'rect' || currentTool === 'circle') {
      var pos = getPos(e);
      drawShape(startX, startY, pos.x, pos.y);
      snapshot = null;
    }
    isDrawing = false;
    ctx.beginPath();
    ctx.globalCompositeOperation = 'source-over';
  }

  // Mouse
  canvas.addEventListener('mousedown', onStart);
  canvas.addEventListener('mousemove', onMove);
  canvas.addEventListener('mouseup', onEnd);
  canvas.addEventListener('mouseleave', onEnd);

  // Touch
  canvas.addEventListener('touchstart', onStart, {passive: false});
  canvas.addEventListener('touchmove', onMove, {passive: false});
  canvas.addEventListener('touchend', onEnd, {passive: false});
  canvas.addEventListener('touchcancel', onEnd, {passive: false});

  // Wrap height
  wrap.style.height = CANVAS_H + 'px';
})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

> ドット絵を作成 → [ドット絵エディター](/ja/tools/pixel-art-editor/)
> SVGパスを編集 → [SVGパスエディター](/ja/tools/svg-path-editor/)
> ダミー画像を作成 → [プレースホルダー画像生成ツール](/ja/tools/placeholder-image/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
