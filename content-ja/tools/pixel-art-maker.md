---
title: "ドット絵メーカー - オンラインでピクセルアートを作成"
description: "グリッドエディタでピクセルアートを作成、PNGでエクスポート。無料オンラインドット絵作成ツール。"
date: 2025-05-16
slug: "pixel-art-maker"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: "/images/covers/pixel-art-maker.png"
---

<div id="pam-app">

<style>
#pam-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic UI", Meiryo, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 16px;
  color: #222;
}
#pam-app h1 {
  font-size: 1.6rem;
  margin-bottom: 4px;
}
#pam-app p.pam-desc {
  color: #555;
  margin-top: 0;
  margin-bottom: 16px;
}
#pam-app .pam-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 12px;
  background: #f5f5f5;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 10px 12px;
}
#pam-app .pam-toolbar label {
  font-size: 0.82rem;
  color: #444;
  margin-right: 2px;
}
#pam-app select, #pam-app button {
  font-size: 0.85rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 4px 9px;
  background: #fff;
  cursor: pointer;
  transition: background 0.15s;
}
#pam-app button:hover { background: #e8e8e8; }
#pam-app button.pam-active {
  background: #3b82f6;
  color: #fff;
  border-color: #2563eb;
}
#pam-app .pam-color-wrap {
  display: flex;
  align-items: center;
  gap: 6px;
}
#pam-app input[type=color] {
  width: 34px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 1px;
  cursor: pointer;
  background: none;
}
#pam-app .pam-recent-colors {
  display: flex;
  gap: 4px;
  align-items: center;
}
#pam-app .pam-recent-swatch {
  width: 20px;
  height: 20px;
  border-radius: 3px;
  border: 1px solid #aaa;
  cursor: pointer;
  flex-shrink: 0;
  transition: transform 0.1s;
}
#pam-app .pam-recent-swatch:hover { transform: scale(1.2); }
#pam-app .pam-canvas-wrap {
  display: flex;
  justify-content: center;
  margin-bottom: 12px;
  overflow: auto;
}
#pam-app #pam-canvas {
  display: block;
  cursor: crosshair;
  border: 2px solid #555;
  image-rendering: pixelated;
  image-rendering: crisp-edges;
}
#pam-app .pam-status {
  font-size: 0.8rem;
  color: #666;
  text-align: center;
  margin-bottom: 14px;
  min-height: 18px;
}
#pam-app .pam-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}
#pam-app .pam-actions button {
  padding: 6px 14px;
}
#pam-app .pam-cta {
  background: #fff8e1;
  border: 1px solid #ffe082;
  border-radius: 8px;
  padding: 14px 16px;
  margin-bottom: 20px;
  font-size: 0.92rem;
  line-height: 1.7;
  color: #444;
}
#pam-app .pam-sep {
  width: 1px;
  height: 24px;
  background: #ccc;
  margin: 0 2px;
}
</style>

<p class="pam-desc">ブラウザでドット絵が描けるオンラインツールです。登録不要・インストール不要。グリッドサイズを選んで、色を選んで、作品をPNGでダウンロードできます。</p>

<div class="pam-toolbar">
  <label>グリッド:</label>
  <select id="pam-size-select">
    <option value="16">16×16</option>
    <option value="32" selected>32×32</option>
    <option value="64">64×64</option>
  </select>
  <div class="pam-sep"></div>
  <label>色:</label>
  <div class="pam-color-wrap">
    <input type="color" id="pam-color" value="#3b82f6">
    <div class="pam-recent-colors" id="pam-recent-colors"></div>
  </div>
  <div class="pam-sep"></div>
  <button id="pam-tool-pencil" class="pam-active" title="鉛筆">鉛筆</button>
  <button id="pam-tool-eraser" title="消しゴム">消しゴム</button>
  <button id="pam-tool-fill" title="塗りつぶし">塗りつぶし</button>
  <button id="pam-tool-eyedropper" title="スポイト">スポイト</button>
  <div class="pam-sep"></div>
  <button id="pam-grid-toggle">グリッド非表示</button>
</div>

<div class="pam-canvas-wrap">
  <canvas id="pam-canvas"></canvas>
</div>

<div class="pam-status" id="pam-status">準備完了 — クリックまたはドラッグで描画</div>

<div class="pam-actions">
  <button id="pam-undo">元に戻す</button>
  <button id="pam-redo">やり直す</button>
  <button id="pam-clear">キャンバスをクリア</button>
  <button id="pam-download">PNGでダウンロード</button>
</div>

<script>
(function() {
  var CANVAS_PX = 512;
  var gridSize = 32;
  var showGrid = true;
  var currentTool = 'pencil';
  var isDrawing = false;
  var currentColor = '#3b82f6';
  var recentColors = [];
  var history = [];
  var historyIndex = -1;
  var MAX_HISTORY = 50;

  var canvas = document.getElementById('pam-canvas');
  var ctx = canvas.getContext('2d');
  var colorInput = document.getElementById('pam-color');
  var sizeSelect = document.getElementById('pam-size-select');
  var statusEl = document.getElementById('pam-status');
  var recentColorsEl = document.getElementById('pam-recent-colors');

  var pixels = [];

  function initPixels() {
    pixels = [];
    for (var i = 0; i < gridSize * gridSize; i++) {
      pixels.push(null);
    }
  }

  function cellSize() { return CANVAS_PX / gridSize; }

  function setupCanvas() {
    canvas.width = CANVAS_PX;
    canvas.height = CANVAS_PX;
    canvas.style.width = CANVAS_PX + 'px';
    canvas.style.height = CANVAS_PX + 'px';
  }

  function drawAll() {
    var cs = cellSize();
    ctx.clearRect(0, 0, CANVAS_PX, CANVAS_PX);
    ctx.fillStyle = '#ffffff';
    ctx.fillRect(0, 0, CANVAS_PX, CANVAS_PX);

    for (var i = 0; i < gridSize; i++) {
      for (var j = 0; j < gridSize; j++) {
        var idx = i * gridSize + j;
        if (pixels[idx]) {
          ctx.fillStyle = pixels[idx];
          ctx.fillRect(j * cs, i * cs, cs, cs);
        }
      }
    }

    if (showGrid) {
      ctx.strokeStyle = 'rgba(180,180,180,0.5)';
      ctx.lineWidth = 0.5;
      for (var x = 0; x <= gridSize; x++) {
        ctx.beginPath();
        ctx.moveTo(x * cs, 0);
        ctx.lineTo(x * cs, CANVAS_PX);
        ctx.stroke();
      }
      for (var y = 0; y <= gridSize; y++) {
        ctx.beginPath();
        ctx.moveTo(0, y * cs);
        ctx.lineTo(CANVAS_PX, y * cs);
        ctx.stroke();
      }
    }
  }

  function getCell(e) {
    var rect = canvas.getBoundingClientRect();
    var scaleX = CANVAS_PX / rect.width;
    var scaleY = CANVAS_PX / rect.height;
    var x = Math.floor(((e.clientX - rect.left) * scaleX) / cellSize());
    var y = Math.floor(((e.clientY - rect.top) * scaleY) / cellSize());
    if (x < 0 || x >= gridSize || y < 0 || y >= gridSize) return null;
    return { x: x, y: y };
  }

  function pushHistory() {
    history.splice(historyIndex + 1);
    history.push(pixels.slice());
    if (history.length > MAX_HISTORY) history.shift();
    historyIndex = history.length - 1;
  }

  function applyTool(cell, saveHist) {
    if (!cell) return;
    var idx = cell.y * gridSize + cell.x;
    if (currentTool === 'pencil') {
      pixels[idx] = currentColor;
      drawAll();
    } else if (currentTool === 'eraser') {
      pixels[idx] = null;
      drawAll();
    } else if (currentTool === 'fill') {
      var targetColor = pixels[idx];
      if (targetColor === currentColor) return;
      floodFill(cell.x, cell.y, targetColor, currentColor);
      drawAll();
      if (saveHist) pushHistory();
      addRecentColor(currentColor);
      return;
    } else if (currentTool === 'eyedropper') {
      var picked = pixels[idx] || '#ffffff';
      currentColor = picked;
      colorInput.value = picked;
      setTool('pencil');
      setStatus('色を取得しました: ' + picked);
      return;
    }
    if (saveHist) pushHistory();
    if (currentTool === 'pencil') addRecentColor(currentColor);
  }

  function floodFill(startX, startY, targetColor, fillColor) {
    var stack = [[startX, startY]];
    var visited = new Set();
    while (stack.length > 0) {
      var pos = stack.pop();
      var x = pos[0], y = pos[1];
      if (x < 0 || x >= gridSize || y < 0 || y >= gridSize) continue;
      var key = y * gridSize + x;
      if (visited.has(key)) continue;
      if (pixels[key] !== targetColor) continue;
      visited.add(key);
      pixels[key] = fillColor;
      stack.push([x + 1, y], [x - 1, y], [x, y + 1], [x, y - 1]);
    }
  }

  function addRecentColor(hex) {
    recentColors = recentColors.filter(function(c) { return c !== hex; });
    recentColors.unshift(hex);
    if (recentColors.length > 10) recentColors.length = 10;
    renderRecentColors();
  }

  function renderRecentColors() {
    recentColorsEl.innerHTML = '';
    recentColors.forEach(function(c) {
      var sw = document.createElement('div');
      sw.className = 'pam-recent-swatch';
      sw.style.background = c;
      sw.title = c;
      sw.addEventListener('click', function() {
        currentColor = c;
        colorInput.value = c;
      });
      recentColorsEl.appendChild(sw);
    });
  }

  function setTool(tool) {
    currentTool = tool;
    var toolNames = { pencil: 'pam-tool-pencil', eraser: 'pam-tool-eraser', fill: 'pam-tool-fill', eyedropper: 'pam-tool-eyedropper' };
    Object.keys(toolNames).forEach(function(t) {
      var btn = document.getElementById(toolNames[t]);
      if (btn) btn.classList.toggle('pam-active', t === tool);
    });
    var cursors = { pencil: 'crosshair', eraser: 'cell', fill: 'copy', eyedropper: 'zoom-in' };
    canvas.style.cursor = cursors[tool] || 'crosshair';
  }

  function setStatus(msg) {
    statusEl.textContent = msg;
  }

  canvas.addEventListener('mousedown', function(e) {
    e.preventDefault();
    var cell = getCell(e);
    if (!cell) return;
    isDrawing = true;
    if (currentTool === 'fill' || currentTool === 'eyedropper') {
      applyTool(cell, true);
    } else {
      pushHistory();
      applyTool(cell, false);
    }
  });

  canvas.addEventListener('mousemove', function(e) {
    var cell = getCell(e);
    if (cell) setStatus('x: ' + cell.x + ', y: ' + cell.y);
    if (!isDrawing) return;
    if (currentTool === 'pencil' || currentTool === 'eraser') {
      applyTool(cell, false);
    }
  });

  canvas.addEventListener('mouseup', function() { isDrawing = false; });
  canvas.addEventListener('mouseleave', function() { isDrawing = false; });

  canvas.addEventListener('touchstart', function(e) {
    e.preventDefault();
    var touch = e.touches[0];
    var cell = getCell(touch);
    if (!cell) return;
    isDrawing = true;
    if (currentTool === 'fill' || currentTool === 'eyedropper') {
      applyTool(cell, true);
    } else {
      pushHistory();
      applyTool(cell, false);
    }
  }, { passive: false });

  canvas.addEventListener('touchmove', function(e) {
    e.preventDefault();
    if (!isDrawing) return;
    var touch = e.touches[0];
    var cell = getCell(touch);
    if (currentTool === 'pencil' || currentTool === 'eraser') {
      applyTool(cell, false);
    }
  }, { passive: false });

  canvas.addEventListener('touchend', function() { isDrawing = false; });

  colorInput.addEventListener('input', function() {
    currentColor = colorInput.value;
  });

  sizeSelect.addEventListener('change', function() {
    if (!confirm('グリッドサイズを変更するとキャンバスがクリアされます。続けますか？')) {
      sizeSelect.value = String(gridSize);
      return;
    }
    gridSize = parseInt(sizeSelect.value);
    initPixels();
    history = [];
    historyIndex = -1;
    drawAll();
    setStatus('グリッドを ' + gridSize + 'x' + gridSize + ' に変更しました');
  });

  document.getElementById('pam-tool-pencil').addEventListener('click', function() { setTool('pencil'); });
  document.getElementById('pam-tool-eraser').addEventListener('click', function() { setTool('eraser'); });
  document.getElementById('pam-tool-fill').addEventListener('click', function() { setTool('fill'); });
  document.getElementById('pam-tool-eyedropper').addEventListener('click', function() { setTool('eyedropper'); });

  document.getElementById('pam-grid-toggle').addEventListener('click', function() {
    showGrid = !showGrid;
    this.textContent = showGrid ? 'グリッド非表示' : 'グリッド表示';
    drawAll();
  });

  document.getElementById('pam-undo').addEventListener('click', function() {
    if (historyIndex <= 0) { setStatus('これ以上元に戻せません'); return; }
    historyIndex--;
    pixels = history[historyIndex].slice();
    drawAll();
    setStatus('元に戻しました');
  });

  document.getElementById('pam-redo').addEventListener('click', function() {
    if (historyIndex >= history.length - 1) { setStatus('これ以上やり直せません'); return; }
    historyIndex++;
    pixels = history[historyIndex].slice();
    drawAll();
    setStatus('やり直しました');
  });

  document.getElementById('pam-clear').addEventListener('click', function() {
    if (!confirm('キャンバスを全てクリアしますか？')) return;
    pushHistory();
    initPixels();
    drawAll();
    setStatus('キャンバスをクリアしました');
  });

  document.getElementById('pam-download').addEventListener('click', function() {
    var scale = gridSize <= 16 ? 16 : gridSize <= 32 ? 8 : 4;
    var out = document.createElement('canvas');
    out.width = gridSize * scale;
    out.height = gridSize * scale;
    var octx = out.getContext('2d');
    octx.fillStyle = '#ffffff';
    octx.fillRect(0, 0, out.width, out.height);
    for (var i = 0; i < gridSize; i++) {
      for (var j = 0; j < gridSize; j++) {
        var c = pixels[i * gridSize + j];
        if (c) {
          octx.fillStyle = c;
          octx.fillRect(j * scale, i * scale, scale, scale);
        }
      }
    }
    var link = document.createElement('a');
    link.download = 'pixel-art-' + gridSize + 'x' + gridSize + '.png';
    link.href = out.toDataURL('image/png');
    link.click();
    setStatus('PNGでダウンロードしました (' + (gridSize * scale) + 'x' + (gridSize * scale) + 'px)');
  });

  document.addEventListener('keydown', function(e) {
    if (e.target.tagName === 'INPUT' || e.target.tagName === 'SELECT') return;
    if (e.key === 'p' || e.key === 'P') setTool('pencil');
    if (e.key === 'e' || e.key === 'E') setTool('eraser');
    if (e.key === 'f' || e.key === 'F') setTool('fill');
    if (e.key === 'i' || e.key === 'I') setTool('eyedropper');
    if ((e.ctrlKey || e.metaKey) && e.key === 'z') {
      e.preventDefault();
      document.getElementById('pam-undo').click();
    }
    if ((e.ctrlKey || e.metaKey) && e.key === 'y') {
      e.preventDefault();
      document.getElementById('pam-redo').click();
    }
  });

  setupCanvas();
  initPixels();
  pushHistory();
  drawAll();
  setStatus('準備完了 — クリックまたはドラッグで描画 | ショートカット: P=鉛筆 E=消しゴム F=塗りつぶし I=スポイト Ctrl+Z=元に戻す');
})();
</script>

---

> クリエイティブ活動の確定申告も簡単 → [freee会計で副業収入を管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

<div class="pam-cta">
このツールが役に立ったら、ぜひ他の無料ツールもお試しください。作ったドット絵はSNSでシェアしてもらえると励みになります！
</div>

</div>

---

## 関連ツール

> Favicon Generator → [Favicon Generatorツール](/ja/tools/favicon-generator/)
> Image Color Picker → [Image Color Pickerツール](/ja/tools/image-color-picker/)
> 画像圧縮 → [画像圧縮ツール](/ja/tools/image-compressor/)

