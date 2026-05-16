---
title: "ドット絵エディター"
date: 2025-05-16
description: "無料のドット絵エディター。カスタマイズ可能なグリッドでピクセルアートを作成。カラーパレット・塗りつぶし・PNG書き出し対応、会員登録不要。"
categories: ["無料ツール"]
slug: "pixel-art-editor"
ShowToc: false
cover:
  image: "/images/covers/pixel-art-editor-ja.png"
  alt: "ドット絵エディター"
---

<div id="px-app">
<style>
#px-app *,
#px-app *::before,
#px-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#px-app {
  font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  color: #1e293b;
  max-width: 900px;
  margin: 0 auto;
  padding: 16px 8px;
}
#px-app h2 {
  font-size: 1.25rem;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 12px;
}
/* --- Layout --- */
#px-app .px-layout {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
#px-app .px-row {
  display: flex;
  gap: 12px;
  align-items: flex-start;
  flex-wrap: wrap;
}
/* --- Sidebar --- */
#px-app .px-sidebar {
  display: flex;
  flex-direction: column;
  gap: 10px;
  min-width: 160px;
  flex: 0 0 160px;
}
#px-app .px-panel {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 10px 12px;
}
#px-app .px-panel-title {
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  margin-bottom: 8px;
}
/* --- Tools --- */
#px-app .px-tools {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5px;
}
#px-app .px-tool-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 3px;
  padding: 7px 4px;
  background: #fff;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  cursor: pointer;
  font-size: 11px;
  color: #374151;
  font-weight: 600;
  transition: all 0.15s;
  line-height: 1.2;
  text-align: center;
  user-select: none;
}
#px-app .px-tool-btn:hover {
  background: #e0f2fe;
  border-color: #38bdf8;
  color: #0369a1;
}
#px-app .px-tool-btn.active {
  background: #0284c7;
  border-color: #0284c7;
  color: #fff;
}
#px-app .px-tool-icon {
  font-size: 18px;
  line-height: 1;
}
/* --- Color current --- */
#px-app .px-color-preview {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
}
#px-app .px-current-swatch {
  width: 36px;
  height: 36px;
  border-radius: 7px;
  border: 2px solid #94a3b8;
  cursor: pointer;
  flex-shrink: 0;
}
#px-app .px-color-label {
  font-size: 11px;
  color: #64748b;
  font-weight: 600;
}
#px-app .px-color-hex {
  font-size: 11px;
  color: #334155;
  font-family: monospace;
}
#px-app .px-custom-input {
  width: 100%;
  height: 32px;
  border-radius: 6px;
  border: 1.5px solid #cbd5e1;
  cursor: pointer;
  background: #fff;
}
/* --- Palette --- */
#px-app .px-palette {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 4px;
}
#px-app .px-palette-swatch {
  width: 100%;
  aspect-ratio: 1;
  border-radius: 5px;
  border: 2px solid transparent;
  cursor: pointer;
  transition: transform 0.1s, border-color 0.1s;
}
#px-app .px-palette-swatch:hover {
  transform: scale(1.15);
  border-color: #94a3b8;
}
#px-app .px-palette-swatch.selected {
  border-color: #0284c7;
  transform: scale(1.1);
}
/* --- Controls --- */
#px-app .px-controls {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
#px-app .px-ctrl-row {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  color: #374151;
}
#px-app .px-ctrl-row label {
  font-size: 11px;
  color: #64748b;
  font-weight: 600;
  min-width: 36px;
}
#px-app .px-select {
  flex: 1;
  padding: 4px 6px;
  border-radius: 6px;
  border: 1.5px solid #cbd5e1;
  font-size: 12px;
  color: #1e293b;
  background: #fff;
  cursor: pointer;
}
#px-app .px-toggle {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 11px;
  color: #374151;
  cursor: pointer;
  user-select: none;
}
#px-app .px-toggle input[type="checkbox"] {
  width: 14px;
  height: 14px;
  cursor: pointer;
  accent-color: #0284c7;
}
/* --- Action buttons --- */
#px-app .px-actions {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
#px-app .px-action-btn {
  padding: 7px 10px;
  border-radius: 7px;
  border: 1.5px solid #cbd5e1;
  background: #fff;
  color: #374151;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  text-align: center;
  transition: all 0.15s;
  width: 100%;
}
#px-app .px-action-btn:hover {
  background: #f1f5f9;
  border-color: #94a3b8;
}
#px-app .px-action-btn:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}
#px-app .px-action-btn.danger {
  border-color: #fca5a5;
  color: #dc2626;
}
#px-app .px-action-btn.danger:hover {
  background: #fef2f2;
}
#px-app .px-action-btn.primary {
  background: #0284c7;
  border-color: #0284c7;
  color: #fff;
}
#px-app .px-action-btn.primary:hover {
  background: #0369a1;
}
/* --- Canvas area --- */
#px-app .px-canvas-area {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}
#px-app .px-zoom-bar {
  display: flex;
  align-items: center;
  gap: 8px;
}
#px-app .px-zoom-btn {
  width: 30px;
  height: 30px;
  border-radius: 6px;
  border: 1.5px solid #cbd5e1;
  background: #fff;
  color: #374151;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.12s;
  line-height: 1;
}
#px-app .px-zoom-btn:hover {
  background: #e0f2fe;
  border-color: #38bdf8;
}
#px-app .px-zoom-label {
  font-size: 12px;
  color: #64748b;
  font-weight: 600;
  min-width: 40px;
  text-align: center;
}
#px-app .px-canvas-wrapper {
  overflow: auto;
  border: 2px solid #cbd5e1;
  border-radius: 8px;
  background: #f1f5f9;
  width: 100%;
  max-width: 100%;
  cursor: crosshair;
  position: relative;
  user-select: none;
}
#px-app canvas {
  display: block;
  image-rendering: pixelated;
  image-rendering: crisp-edges;
  cursor: crosshair;
}
/* --- Status bar --- */
#px-app .px-status {
  font-size: 11px;
  color: #94a3b8;
  height: 16px;
}
/* --- Responsive --- */
@media (max-width: 600px) {
  #px-app .px-row {
    flex-direction: column;
  }
  #px-app .px-sidebar {
    flex: none;
    width: 100%;
    flex-direction: row;
    flex-wrap: wrap;
  }
  #px-app .px-panel {
    flex: 1;
    min-width: 140px;
  }
}
</style>

<div class="px-layout">
  <!-- Top controls row -->
  <div class="px-row" style="align-items:center;flex-wrap:wrap;gap:8px;">
    <div style="font-size:13px;font-weight:700;color:#0f172a;">ドット絵エディター</div>
    <div class="px-ctrl-row" style="margin-left:auto;">
      <label for="px-size-select">グリッド:</label>
      <select id="px-size-select" class="px-select" style="width:auto;">
        <option value="8">8×8</option>
        <option value="16" selected>16×16</option>
        <option value="32">32×32</option>
        <option value="64">64×64</option>
      </select>
    </div>
    <button id="px-btn-new" class="px-action-btn danger" style="width:auto;padding:6px 14px;">新規作成</button>
  </div>

  <!-- Main row: sidebar + canvas -->
  <div class="px-row">
    <!-- Sidebar -->
    <div class="px-sidebar">
      <!-- Tools -->
      <div class="px-panel">
        <div class="px-panel-title">ツール</div>
        <div class="px-tools">
          <button class="px-tool-btn active" data-tool="pen" title="ペン">
            <span class="px-tool-icon">&#9998;</span>
            <span>ペン</span>
          </button>
          <button class="px-tool-btn" data-tool="eraser" title="消しゴム">
            <span class="px-tool-icon">&#9723;</span>
            <span>消しゴム</span>
          </button>
          <button class="px-tool-btn" data-tool="fill" title="塗りつぶし">
            <span class="px-tool-icon">&#9724;</span>
            <span>塗りつぶし</span>
          </button>
          <button class="px-tool-btn" data-tool="eyedropper" title="スポイト">
            <span class="px-tool-icon">&#128449;</span>
            <span>スポイト</span>
          </button>
        </div>
      </div>

      <!-- Color -->
      <div class="px-panel">
        <div class="px-panel-title">カラー</div>
        <div class="px-color-preview">
          <div id="px-current-swatch" class="px-current-swatch" title="現在の色"></div>
          <div>
            <div class="px-color-label">現在の色</div>
            <div id="px-color-hex-display" class="px-color-hex">#000000</div>
          </div>
        </div>
        <input type="color" id="px-custom-color" class="px-custom-input" value="#000000" title="カスタムカラー">
        <div style="font-size:10px;color:#94a3b8;margin-top:4px;">カスタムカラーを選択</div>
      </div>

      <!-- Palette -->
      <div class="px-panel">
        <div class="px-panel-title">パレット</div>
        <div class="px-palette" id="px-palette"></div>
      </div>

      <!-- Grid toggle -->
      <div class="px-panel">
        <div class="px-panel-title">表示</div>
        <label class="px-toggle">
          <input type="checkbox" id="px-grid-toggle" checked>
          グリッド表示
        </label>
      </div>

      <!-- Actions -->
      <div class="px-panel">
        <div class="px-panel-title">操作</div>
        <div class="px-actions">
          <button id="px-btn-undo" class="px-action-btn" disabled>&#8617; 元に戻す</button>
          <button id="px-btn-redo" class="px-action-btn" disabled>&#8618; やり直し</button>
          <button id="px-btn-clear" class="px-action-btn danger">&#128465; クリア</button>
          <button id="px-btn-export" class="px-action-btn primary">&#128190; PNG書き出し</button>
        </div>
      </div>
    </div>

    <!-- Canvas area -->
    <div class="px-canvas-area">
      <div class="px-zoom-bar">
        <button class="px-zoom-btn" id="px-btn-zoom-out" title="ズームアウト">&#8722;</button>
        <span class="px-zoom-label" id="px-zoom-label">×16</span>
        <button class="px-zoom-btn" id="px-btn-zoom-in" title="ズームイン">&#43;</button>
        <span style="font-size:11px;color:#94a3b8;margin-left:8px;">右クリック: 消去</span>
      </div>
      <div class="px-canvas-wrapper" id="px-canvas-wrapper">
        <canvas id="px-canvas"></canvas>
      </div>
      <div class="px-status" id="px-status"></div>
    </div>
  </div>
</div>

<script>
(function() {
  'use strict';

  // --- Palette (16 colors, slate-inspired) ---
  var PALETTE = [
    '#000000','#334155','#64748b','#94a3b8',
    '#ffffff','#f8fafc','#fef08a','#fb923c',
    '#f87171','#e879f9','#818cf8','#60a5fa',
    '#34d399','#4ade80','#a78bfa','#f472b6'
  ];

  // --- State ---
  var gridSize = 16;
  var cellSize = 16;
  var showGrid = true;
  var currentColor = '#000000';
  var currentTool = 'pen';
  var isDrawing = false;
  var lastCell = null;

  var pixels = [];       // flat array of color strings or null
  var undoStack = [];
  var redoStack = [];
  var MAX_HISTORY = 20;

  // --- DOM refs ---
  var canvas = document.getElementById('px-canvas');
  var ctx = canvas.getContext('2d');
  var wrapper = document.getElementById('px-canvas-wrapper');
  var sizeSelect = document.getElementById('px-size-select');
  var gridToggle = document.getElementById('px-grid-toggle');
  var currentSwatch = document.getElementById('px-current-swatch');
  var hexDisplay = document.getElementById('px-color-hex-display');
  var customColor = document.getElementById('px-custom-color');
  var paletteEl = document.getElementById('px-palette');
  var btnUndo = document.getElementById('px-btn-undo');
  var btnRedo = document.getElementById('px-btn-redo');
  var btnClear = document.getElementById('px-btn-clear');
  var btnExport = document.getElementById('px-btn-export');
  var btnNew = document.getElementById('px-btn-new');
  var btnZoomIn = document.getElementById('px-btn-zoom-in');
  var btnZoomOut = document.getElementById('px-btn-zoom-out');
  var zoomLabel = document.getElementById('px-zoom-label');
  var statusEl = document.getElementById('px-status');
  var toolBtns = document.querySelectorAll('#px-app .px-tool-btn');

  // --- Init pixels ---
  function initPixels() {
    pixels = new Array(gridSize * gridSize).fill(null);
  }

  // --- Canvas sizing ---
  function resizeCanvas() {
    canvas.width = gridSize * cellSize;
    canvas.height = gridSize * cellSize;
    zoomLabel.textContent = '\xd7' + cellSize;
  }

  // --- Draw ---
  function render() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Draw pixels
    for (var i = 0; i < pixels.length; i++) {
      if (pixels[i]) {
        var col = i % gridSize;
        var row = Math.floor(i / gridSize);
        ctx.fillStyle = pixels[i];
        ctx.fillRect(col * cellSize, row * cellSize, cellSize, cellSize);
      }
    }

    // Draw checkerboard for empty cells
    for (var i = 0; i < pixels.length; i++) {
      if (!pixels[i]) {
        var col = i % gridSize;
        var row = Math.floor(i / gridSize);
        var light = (col + row) % 2 === 0;
        ctx.fillStyle = light ? '#e2e8f0' : '#cbd5e1';
        ctx.fillRect(col * cellSize, row * cellSize, cellSize, cellSize);
      }
    }

    // Draw grid
    if (showGrid && cellSize >= 4) {
      ctx.strokeStyle = 'rgba(100,116,139,0.35)';
      ctx.lineWidth = 0.5;
      for (var c = 0; c <= gridSize; c++) {
        ctx.beginPath();
        ctx.moveTo(c * cellSize, 0);
        ctx.lineTo(c * cellSize, canvas.height);
        ctx.stroke();
      }
      for (var r = 0; r <= gridSize; r++) {
        ctx.beginPath();
        ctx.moveTo(0, r * cellSize);
        ctx.lineTo(canvas.width, r * cellSize);
        ctx.stroke();
      }
    }
  }

  // --- Get cell from mouse event ---
  function getCellFromEvent(e) {
    var rect = canvas.getBoundingClientRect();
    var x = (e.clientX - rect.left);
    var y = (e.clientY - rect.top);
    // Account for CSS scaling
    var scaleX = canvas.width / rect.width;
    var scaleY = canvas.height / rect.height;
    var col = Math.floor(x * scaleX / cellSize);
    var row = Math.floor(y * scaleY / cellSize);
    if (col < 0 || col >= gridSize || row < 0 || row >= gridSize) return null;
    return { col: col, row: row, idx: row * gridSize + col };
  }

  // --- History ---
  function saveHistory() {
    undoStack.push(pixels.slice());
    if (undoStack.length > MAX_HISTORY) undoStack.shift();
    redoStack = [];
    updateHistoryButtons();
  }

  function updateHistoryButtons() {
    btnUndo.disabled = undoStack.length === 0;
    btnRedo.disabled = redoStack.length === 0;
  }

  function undo() {
    if (undoStack.length === 0) return;
    redoStack.push(pixels.slice());
    pixels = undoStack.pop();
    updateHistoryButtons();
    render();
  }

  function redo() {
    if (redoStack.length === 0) return;
    undoStack.push(pixels.slice());
    pixels = redoStack.pop();
    updateHistoryButtons();
    render();
  }

  // --- Flood fill ---
  function floodFill(startIdx, targetColor, fillColor) {
    if (targetColor === fillColor) return;
    var stack = [startIdx];
    var visited = new Uint8Array(pixels.length);
    while (stack.length > 0) {
      var idx = stack.pop();
      if (idx < 0 || idx >= pixels.length) continue;
      if (visited[idx]) continue;
      var current = pixels[idx] || null;
      if (current !== targetColor) continue;
      visited[idx] = 1;
      pixels[idx] = fillColor;
      var col = idx % gridSize;
      var row = Math.floor(idx / gridSize);
      if (col > 0) stack.push(idx - 1);
      if (col < gridSize - 1) stack.push(idx + 1);
      if (row > 0) stack.push(idx - gridSize);
      if (row < gridSize - 1) stack.push(idx + gridSize);
    }
  }

  // --- Apply tool ---
  function applyTool(cell, erase) {
    if (!cell) return;
    var sameCell = lastCell && lastCell.idx === cell.idx;
    if (isDrawing && sameCell && currentTool !== 'fill') return;
    lastCell = cell;

    if (currentTool === 'eyedropper') {
      var picked = pixels[cell.idx] || null;
      if (picked) setColor(picked);
      return;
    }

    if (currentTool === 'fill') {
      var targetColor = pixels[cell.idx] || null;
      var fillColor = erase ? null : currentColor;
      saveHistory();
      floodFill(cell.idx, targetColor, fillColor);
      render();
      return;
    }

    if (currentTool === 'pen' && !erase) {
      if (pixels[cell.idx] === currentColor) return;
      if (!sameCell || pixels[cell.idx] !== currentColor) {
        saveHistory();
        pixels[cell.idx] = currentColor;
        render();
      }
    } else if (currentTool === 'eraser' || erase) {
      if (pixels[cell.idx] === null) return;
      saveHistory();
      pixels[cell.idx] = null;
      render();
    }
  }

  // --- Mouse events ---
  canvas.addEventListener('mousedown', function(e) {
    e.preventDefault();
    isDrawing = true;
    lastCell = null;
    var cell = getCellFromEvent(e);
    applyTool(cell, e.button === 2);
  });

  canvas.addEventListener('mousemove', function(e) {
    if (!isDrawing) {
      var cell = getCellFromEvent(e);
      if (cell) {
        statusEl.textContent = 'X: ' + (cell.col + 1) + '  Y: ' + (cell.row + 1);
      }
      return;
    }
    var cell = getCellFromEvent(e);
    applyTool(cell, e.button === 2);
  });

  canvas.addEventListener('mouseup', function(e) {
    isDrawing = false;
    lastCell = null;
  });

  canvas.addEventListener('mouseleave', function() {
    isDrawing = false;
    lastCell = null;
    statusEl.textContent = '';
  });

  canvas.addEventListener('contextmenu', function(e) {
    e.preventDefault();
  });

  // --- Touch events ---
  canvas.addEventListener('touchstart', function(e) {
    e.preventDefault();
    isDrawing = true;
    lastCell = null;
    var touch = e.touches[0];
    var cell = getCellFromEvent(touch);
    applyTool(cell, false);
  }, { passive: false });

  canvas.addEventListener('touchmove', function(e) {
    e.preventDefault();
    var touch = e.touches[0];
    var cell = getCellFromEvent(touch);
    applyTool(cell, false);
  }, { passive: false });

  canvas.addEventListener('touchend', function() {
    isDrawing = false;
    lastCell = null;
  });

  // --- Color ---
  function setColor(hex) {
    currentColor = hex;
    currentSwatch.style.background = hex;
    hexDisplay.textContent = hex.toUpperCase();
    customColor.value = hex;
    // Update palette selection
    document.querySelectorAll('#px-app .px-palette-swatch').forEach(function(sw) {
      sw.classList.toggle('selected', sw.dataset.color === hex);
    });
  }

  customColor.addEventListener('input', function() {
    setColor(customColor.value);
  });

  // --- Palette ---
  function buildPalette() {
    paletteEl.innerHTML = '';
    PALETTE.forEach(function(color) {
      var sw = document.createElement('div');
      sw.className = 'px-palette-swatch';
      sw.dataset.color = color;
      sw.style.background = color;
      sw.title = color;
      sw.addEventListener('click', function() {
        setColor(color);
      });
      paletteEl.appendChild(sw);
    });
  }

  // --- Tools ---
  toolBtns.forEach(function(btn) {
    btn.addEventListener('click', function() {
      currentTool = btn.dataset.tool;
      toolBtns.forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
    });
  });

  // --- Grid toggle ---
  gridToggle.addEventListener('change', function() {
    showGrid = gridToggle.checked;
    render();
  });

  // --- Size select ---
  sizeSelect.addEventListener('change', function() {
    if (!confirm('グリッドサイズを変更すると、現在の絵が消えます。よろしいですか？')) {
      sizeSelect.value = String(gridSize);
      return;
    }
    gridSize = parseInt(sizeSelect.value, 10);
    initPixels();
    undoStack = [];
    redoStack = [];
    updateHistoryButtons();
    resizeCanvas();
    render();
  });

  // --- Zoom ---
  var ZOOM_LEVELS = [2, 4, 6, 8, 10, 12, 16, 20, 24, 32];

  function getZoomIndex() {
    var idx = ZOOM_LEVELS.indexOf(cellSize);
    return idx >= 0 ? idx : 6;
  }

  btnZoomIn.addEventListener('click', function() {
    var idx = getZoomIndex();
    if (idx < ZOOM_LEVELS.length - 1) {
      cellSize = ZOOM_LEVELS[idx + 1];
      resizeCanvas();
      render();
    }
  });

  btnZoomOut.addEventListener('click', function() {
    var idx = getZoomIndex();
    if (idx > 0) {
      cellSize = ZOOM_LEVELS[idx - 1];
      resizeCanvas();
      render();
    }
  });

  // --- Undo / Redo ---
  btnUndo.addEventListener('click', undo);
  btnRedo.addEventListener('click', redo);

  // Keyboard shortcuts
  document.addEventListener('keydown', function(e) {
    if ((e.ctrlKey || e.metaKey) && e.key === 'z' && !e.shiftKey) {
      e.preventDefault();
      undo();
    }
    if ((e.ctrlKey || e.metaKey) && (e.key === 'y' || (e.key === 'z' && e.shiftKey))) {
      e.preventDefault();
      redo();
    }
  });

  // --- Clear ---
  btnClear.addEventListener('click', function() {
    if (!confirm('キャンバスをクリアしますか？')) return;
    saveHistory();
    initPixels();
    render();
  });

  // --- New ---
  btnNew.addEventListener('click', function() {
    if (!confirm('新規作成すると、現在の絵が消えます。よろしいですか？')) return;
    initPixels();
    undoStack = [];
    redoStack = [];
    updateHistoryButtons();
    render();
  });

  // --- Export PNG ---
  btnExport.addEventListener('click', function() {
    var scale = 4;
    var exportCanvas = document.createElement('canvas');
    exportCanvas.width = gridSize * scale;
    exportCanvas.height = gridSize * scale;
    var ectx = exportCanvas.getContext('2d');
    ectx.imageSmoothingEnabled = false;

    // Checkerboard bg
    for (var i = 0; i < pixels.length; i++) {
      var col = i % gridSize;
      var row = Math.floor(i / gridSize);
      if (!pixels[i]) {
        ectx.fillStyle = (col + row) % 2 === 0 ? '#e2e8f0' : '#cbd5e1';
      } else {
        ectx.fillStyle = pixels[i];
      }
      ectx.fillRect(col * scale, row * scale, scale, scale);
    }

    var link = document.createElement('a');
    link.download = 'pixel-art.png';
    link.href = exportCanvas.toDataURL('image/png');
    link.click();
  });

  // --- Init ---
  buildPalette();
  setColor('#000000');
  initPixels();
  resizeCanvas();
  render();
  updateHistoryButtons();

})();
</script>

---

## 使い方

1. **グリッドサイズ**を選択（8×8〜64×64）
2. **ツール**を選択してキャンバスに描画
   - **ペン**: クリック・ドラッグで描画
   - **消しゴム**: クリック・ドラッグで消去（右クリックでも消去）
   - **塗りつぶし**: 隣接する同色のエリアを一括塗りつぶし
   - **スポイト**: クリックした色を現在の色として取得
3. **パレット**から色を選択、またはカスタムカラーピッカーで任意の色を指定
4. **元に戻す / やり直し**（Ctrl+Z / Ctrl+Y）で作業履歴を管理
5. **PNG書き出し**で画像をダウンロード

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

---

> アスキーアートを作成 → [アスキーアートジェネレーター](/ja/tools/ascii-art-generator/)
> 画像から色を抽出 → [画像カラーピッカー](/ja/tools/image-color-picker/)
> ダミー画像を作成 → [プレースホルダー画像生成ツール](/ja/tools/placeholder-image/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
