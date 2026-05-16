---
title: "Whiteboard Drawing Tool"
date: 2025-05-16
description: "Free online whiteboard drawing tool. Sketch, draw, and annotate with pen, shapes, and text — download as PNG, no sign-up required."
categories: ["Free Tools"]
slug: "whiteboard-drawing"
ShowToc: false
cover:
  image: "/images/covers/whiteboard-drawing.png"
  alt: "Whiteboard Drawing Tool"
---

<div id="wb-app">
<style>
  #wb-app * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  #wb-app {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    background: #1e293b;
    border-radius: 10px;
    overflow: hidden;
    user-select: none;
  }

  #wb-app .wb-toolbar {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 6px;
    padding: 10px 12px;
    background: #0f172a;
    border-bottom: 2px solid #334155;
  }

  #wb-app .wb-toolbar-group {
    display: flex;
    align-items: center;
    gap: 4px;
    padding-right: 10px;
    border-right: 1px solid #334155;
  }

  #wb-app .wb-toolbar-group:last-child {
    border-right: none;
  }

  #wb-app .wb-tool-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border: 2px solid transparent;
    border-radius: 6px;
    background: #1e293b;
    color: #94a3b8;
    cursor: pointer;
    font-size: 16px;
    transition: background 0.15s, border-color 0.15s, color 0.15s;
    flex-shrink: 0;
  }

  #wb-app .wb-tool-btn:hover {
    background: #334155;
    color: #e2e8f0;
  }

  #wb-app .wb-tool-btn.active {
    background: #3b82f6;
    border-color: #60a5fa;
    color: #ffffff;
  }

  #wb-app .wb-action-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 34px;
    padding: 0 12px;
    border: 1px solid #475569;
    border-radius: 6px;
    background: #1e293b;
    color: #94a3b8;
    cursor: pointer;
    font-size: 13px;
    font-weight: 500;
    gap: 5px;
    transition: background 0.15s, border-color 0.15s, color 0.15s;
    white-space: nowrap;
    flex-shrink: 0;
  }

  #wb-app .wb-action-btn:hover {
    background: #334155;
    color: #e2e8f0;
    border-color: #64748b;
  }

  #wb-app .wb-action-btn.danger:hover {
    background: #7f1d1d;
    border-color: #ef4444;
    color: #fca5a5;
  }

  #wb-app .wb-action-btn.download:hover {
    background: #14532d;
    border-color: #22c55e;
    color: #86efac;
  }

  #wb-app .wb-color-wrap {
    display: flex;
    align-items: center;
    gap: 6px;
  }

  #wb-app .wb-color-label {
    color: #64748b;
    font-size: 12px;
  }

  #wb-app .wb-color-input {
    width: 32px;
    height: 32px;
    border: 2px solid #475569;
    border-radius: 6px;
    padding: 2px;
    background: #1e293b;
    cursor: pointer;
  }

  #wb-app .wb-width-wrap {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  #wb-app .wb-width-label {
    color: #64748b;
    font-size: 12px;
    white-space: nowrap;
  }

  #wb-app .wb-width-slider {
    width: 90px;
    accent-color: #3b82f6;
    cursor: pointer;
  }

  #wb-app .wb-width-val {
    color: #94a3b8;
    font-size: 12px;
    min-width: 24px;
    text-align: right;
  }

  #wb-app .wb-canvas-wrap {
    position: relative;
    width: 100%;
    background: #ffffff;
    line-height: 0;
  }

  #wb-app canvas#wb-canvas {
    display: block;
    width: 100%;
    height: auto;
    min-height: 600px;
    touch-action: none;
  }

  #wb-app canvas#wb-canvas.cur-pen     { cursor: crosshair; }
  #wb-app canvas#wb-canvas.cur-line    { cursor: crosshair; }
  #wb-app canvas#wb-canvas.cur-rect    { cursor: crosshair; }
  #wb-app canvas#wb-canvas.cur-ellipse { cursor: crosshair; }
  #wb-app canvas#wb-canvas.cur-text    { cursor: text; }
  #wb-app canvas#wb-canvas.cur-eraser  { cursor: cell; }

  #wb-app .wb-text-input-overlay {
    position: absolute;
    display: none;
    border: 2px dashed #3b82f6;
    background: rgba(255,255,255,0.9);
    font-size: 16px;
    font-family: sans-serif;
    padding: 2px 6px;
    outline: none;
    min-width: 120px;
    min-height: 28px;
    z-index: 10;
    resize: none;
    overflow: hidden;
    border-radius: 3px;
    line-height: 1.4;
  }

  #wb-app .wb-crosslinks {
    padding: 14px 16px;
    background: #0f172a;
    border-top: 2px solid #334155;
    font-size: 13px;
    color: #64748b;
    display: flex;
    flex-wrap: wrap;
    gap: 6px 20px;
  }

  #wb-app .wb-crosslinks a {
    color: #60a5fa;
    text-decoration: none;
  }

  #wb-app .wb-crosslinks a:hover {
    text-decoration: underline;
    color: #93c5fd;
  }

  @media (max-width: 600px) {
    #wb-app .wb-width-slider {
      width: 60px;
    }
    #wb-app .wb-action-btn span {
      display: none;
    }
  }
</style>

<div class="wb-toolbar">
  <!-- Tool selection -->
  <div class="wb-toolbar-group">
    <button class="wb-tool-btn active" id="wb-btn-pen"     title="Pen (freehand)">&#9998;</button>
    <button class="wb-tool-btn"        id="wb-btn-line"    title="Line">&#9135;</button>
    <button class="wb-tool-btn"        id="wb-btn-rect"    title="Rectangle">&#9645;</button>
    <button class="wb-tool-btn"        id="wb-btn-ellipse" title="Circle / Ellipse">&#9711;</button>
    <button class="wb-tool-btn"        id="wb-btn-text"    title="Text">T</button>
    <button class="wb-tool-btn"        id="wb-btn-eraser"  title="Eraser">&#9003;</button>
  </div>

  <!-- Stroke color -->
  <div class="wb-toolbar-group">
    <div class="wb-color-wrap">
      <span class="wb-color-label">Color</span>
      <input class="wb-color-input" type="color" id="wb-color" value="#1e293b" title="Stroke color">
    </div>
  </div>

  <!-- Line width -->
  <div class="wb-toolbar-group">
    <div class="wb-width-wrap">
      <span class="wb-width-label">Width</span>
      <input class="wb-width-slider" type="range" id="wb-width" min="1" max="20" value="3" title="Line width">
      <span class="wb-width-val" id="wb-width-val">3</span>
    </div>
  </div>

  <!-- Undo / Redo -->
  <div class="wb-toolbar-group">
    <button class="wb-action-btn" id="wb-undo" title="Undo">&#8630; <span>Undo</span></button>
    <button class="wb-action-btn" id="wb-redo" title="Redo">&#8631; <span>Redo</span></button>
  </div>

  <!-- Clear + Download -->
  <div class="wb-toolbar-group">
    <button class="wb-action-btn danger"   id="wb-clear"    title="Clear canvas">&#10005; <span>Clear</span></button>
    <button class="wb-action-btn download" id="wb-download" title="Download as PNG">&#8595; <span>PNG</span></button>
  </div>
</div>

<div class="wb-canvas-wrap" id="wb-canvas-wrap">
  <canvas id="wb-canvas" class="cur-pen"></canvas>
  <textarea class="wb-text-input-overlay" id="wb-text-input" rows="1"></textarea>
</div>

<div class="wb-crosslinks">
  <span>Also try:</span>
  <a href="/tools/pixel-art-editor/">Pixel Art Editor</a>
  <a href="/tools/svg-path-editor/">SVG Path Editor</a>
  <a href="/tools/placeholder-image/">Placeholder Image Generator</a>
</div>

<script>
(function () {
  "use strict";

  /* ── Elements ── */
  const canvas   = document.getElementById("wb-canvas");
  const ctx      = canvas.getContext("2d");
  const wrap     = document.getElementById("wb-canvas-wrap");
  const txtInput = document.getElementById("wb-text-input");

  const btnPen     = document.getElementById("wb-btn-pen");
  const btnLine    = document.getElementById("wb-btn-line");
  const btnRect    = document.getElementById("wb-btn-rect");
  const btnEllipse = document.getElementById("wb-btn-ellipse");
  const btnText    = document.getElementById("wb-btn-text");
  const btnEraser  = document.getElementById("wb-btn-eraser");

  const colorInput = document.getElementById("wb-color");
  const widthInput = document.getElementById("wb-width");
  const widthVal   = document.getElementById("wb-width-val");

  const btnUndo     = document.getElementById("wb-undo");
  const btnRedo     = document.getElementById("wb-redo");
  const btnClear    = document.getElementById("wb-clear");
  const btnDownload = document.getElementById("wb-download");

  /* ── State ── */
  const LOGICAL_W = 1400;
  const LOGICAL_H = 900;

  let currentTool  = "pen";
  let isDrawing    = false;
  let startX = 0, startY = 0;
  let snapshot     = null;   // ImageData saved at mousedown for shape preview
  let history      = [];     // array of ImageData
  let historyIdx   = -1;

  /* ── Canvas setup ── */
  function initCanvas() {
    canvas.width  = LOGICAL_W;
    canvas.height = LOGICAL_H;
    ctx.fillStyle = "#ffffff";
    ctx.fillRect(0, 0, LOGICAL_W, LOGICAL_H);
    saveHistory();
  }

  /* ── Scale: logical px from event ── */
  function getPos(e) {
    const rect  = canvas.getBoundingClientRect();
    const scaleX = LOGICAL_W / rect.width;
    const scaleY = LOGICAL_H / rect.height;
    let clientX, clientY;
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
      x: (clientX - rect.left) * scaleX,
      y: (clientY - rect.top)  * scaleY
    };
  }

  /* ── History ── */
  function saveHistory() {
    // Truncate redo stack
    history = history.slice(0, historyIdx + 1);
    history.push(ctx.getImageData(0, 0, LOGICAL_W, LOGICAL_H));
    historyIdx = history.length - 1;
    // Keep max 50 states to avoid memory issues
    if (history.length > 50) {
      history.shift();
      historyIdx--;
    }
  }

  function undo() {
    if (historyIdx <= 0) return;
    historyIdx--;
    ctx.putImageData(history[historyIdx], 0, 0);
  }

  function redo() {
    if (historyIdx >= history.length - 1) return;
    historyIdx++;
    ctx.putImageData(history[historyIdx], 0, 0);
  }

  /* ── Drawing helpers ── */
  function setupStroke() {
    if (currentTool === "eraser") {
      ctx.strokeStyle = "#ffffff";
      ctx.lineWidth   = parseInt(widthInput.value, 10) * 4;
    } else {
      ctx.strokeStyle = colorInput.value;
      ctx.lineWidth   = parseInt(widthInput.value, 10);
    }
    ctx.lineCap  = "round";
    ctx.lineJoin = "round";
  }

  function drawLine(x1, y1, x2, y2) {
    ctx.beginPath();
    ctx.moveTo(x1, y1);
    ctx.lineTo(x2, y2);
    ctx.stroke();
  }

  function drawRect(x1, y1, x2, y2) {
    ctx.beginPath();
    ctx.strokeRect(x1, y1, x2 - x1, y2 - y1);
  }

  function drawEllipse(x1, y1, x2, y2) {
    const cx = (x1 + x2) / 2;
    const cy = (y1 + y2) / 2;
    const rx = Math.abs(x2 - x1) / 2;
    const ry = Math.abs(y2 - y1) / 2;
    ctx.beginPath();
    ctx.ellipse(cx, cy, rx, ry, 0, 0, Math.PI * 2);
    ctx.stroke();
  }

  /* ── Pointer events (mouse + touch) ── */
  function onPointerDown(e) {
    e.preventDefault();

    // Commit any in-progress text first
    if (currentTool === "text") {
      commitText();
      const pos = getPos(e);
      openTextInput(pos.x, pos.y);
      return;
    }

    isDrawing = true;
    const pos = getPos(e);
    startX = pos.x;
    startY = pos.y;

    setupStroke();

    if (currentTool === "pen" || currentTool === "eraser") {
      ctx.beginPath();
      ctx.moveTo(startX, startY);
    } else {
      // Save snapshot for shape preview
      snapshot = ctx.getImageData(0, 0, LOGICAL_W, LOGICAL_H);
    }
  }

  function onPointerMove(e) {
    e.preventDefault();
    if (!isDrawing) return;

    const pos = getPos(e);

    if (currentTool === "pen" || currentTool === "eraser") {
      setupStroke();
      ctx.lineTo(pos.x, pos.y);
      ctx.stroke();
    } else {
      // Restore snapshot then draw preview shape
      ctx.putImageData(snapshot, 0, 0);
      setupStroke();
      if (currentTool === "line") {
        drawLine(startX, startY, pos.x, pos.y);
      } else if (currentTool === "rect") {
        drawRect(startX, startY, pos.x, pos.y);
      } else if (currentTool === "ellipse") {
        drawEllipse(startX, startY, pos.x, pos.y);
      }
    }
  }

  function onPointerUp(e) {
    e.preventDefault();
    if (!isDrawing) return;
    isDrawing = false;

    const pos = getPos(e);

    if (currentTool === "pen" || currentTool === "eraser") {
      ctx.closePath();
    } else {
      ctx.putImageData(snapshot, 0, 0);
      setupStroke();
      if (currentTool === "line") {
        drawLine(startX, startY, pos.x, pos.y);
      } else if (currentTool === "rect") {
        drawRect(startX, startY, pos.x, pos.y);
      } else if (currentTool === "ellipse") {
        drawEllipse(startX, startY, pos.x, pos.y);
      }
      snapshot = null;
    }

    saveHistory();
  }

  /* ── Text tool ── */
  function openTextInput(lx, ly) {
    const rect   = canvas.getBoundingClientRect();
    const scaleX = rect.width  / LOGICAL_W;
    const scaleY = rect.height / LOGICAL_H;

    // Position overlay on screen coords
    const screenX = lx * scaleX + rect.left - wrap.getBoundingClientRect().left;
    const screenY = ly * scaleY + rect.top  - wrap.getBoundingClientRect().top;

    txtInput.style.left    = screenX + "px";
    txtInput.style.top     = screenY + "px";
    txtInput.style.display = "block";
    txtInput.style.fontSize = (16 * scaleX) + "px";
    txtInput.style.color   = colorInput.value;
    txtInput.dataset.lx    = lx;
    txtInput.dataset.ly    = ly;
    txtInput.value         = "";
    txtInput.focus();
  }

  function commitText() {
    if (txtInput.style.display === "none") return;
    const text = txtInput.value.trim();
    if (text) {
      const lx   = parseFloat(txtInput.dataset.lx);
      const ly   = parseFloat(txtInput.dataset.ly);
      const size = parseInt(widthInput.value, 10);
      const fontSize = 14 + size * 2;
      ctx.font      = `${fontSize}px sans-serif`;
      ctx.fillStyle = colorInput.value;
      // Render each line
      const lines = text.split("\n");
      lines.forEach((line, i) => {
        ctx.fillText(line, lx, ly + (i + 1) * fontSize);
      });
      saveHistory();
    }
    txtInput.style.display = "none";
    txtInput.value = "";
  }

  txtInput.addEventListener("keydown", function (e) {
    if (e.key === "Escape") {
      txtInput.style.display = "none";
      txtInput.value = "";
    }
    if (e.key === "Enter" && !e.shiftKey) {
      e.preventDefault();
      commitText();
    }
    // Auto-resize height
    setTimeout(() => {
      txtInput.style.height = "auto";
      txtInput.style.height = txtInput.scrollHeight + "px";
    }, 0);
  });

  /* ── Tool buttons ── */
  const toolMap = {
    pen: btnPen, line: btnLine, rect: btnRect,
    ellipse: btnEllipse, text: btnText, eraser: btnEraser
  };

  function setTool(name) {
    commitText();
    currentTool = name;
    Object.entries(toolMap).forEach(([t, btn]) => {
      btn.classList.toggle("active", t === name);
    });
    const cursorMap = {
      pen: "cur-pen", line: "cur-line", rect: "cur-rect",
      ellipse: "cur-ellipse", text: "cur-text", eraser: "cur-eraser"
    };
    canvas.className = cursorMap[name] || "cur-pen";
  }

  btnPen    .addEventListener("click", () => setTool("pen"));
  btnLine   .addEventListener("click", () => setTool("line"));
  btnRect   .addEventListener("click", () => setTool("rect"));
  btnEllipse.addEventListener("click", () => setTool("ellipse"));
  btnText   .addEventListener("click", () => setTool("text"));
  btnEraser .addEventListener("click", () => setTool("eraser"));

  /* ── Width label sync ── */
  widthInput.addEventListener("input", () => {
    widthVal.textContent = widthInput.value;
  });

  /* ── Actions ── */
  btnUndo.addEventListener("click", undo);
  btnRedo.addEventListener("click", redo);

  btnClear.addEventListener("click", () => {
    ctx.fillStyle = "#ffffff";
    ctx.fillRect(0, 0, LOGICAL_W, LOGICAL_H);
    saveHistory();
  });

  btnDownload.addEventListener("click", () => {
    commitText();
    const link = document.createElement("a");
    link.download = "whiteboard.png";
    link.href = canvas.toDataURL("image/png");
    link.click();
  });

  /* ── Canvas event listeners ── */
  // Mouse
  canvas.addEventListener("mousedown",  onPointerDown);
  canvas.addEventListener("mousemove",  onPointerMove);
  canvas.addEventListener("mouseup",    onPointerUp);
  canvas.addEventListener("mouseleave", (e) => { if (isDrawing) onPointerUp(e); });

  // Touch
  canvas.addEventListener("touchstart",  onPointerDown, { passive: false });
  canvas.addEventListener("touchmove",   onPointerMove, { passive: false });
  canvas.addEventListener("touchend",    onPointerUp,   { passive: false });
  canvas.addEventListener("touchcancel", onPointerUp,   { passive: false });

  // Click for text tool (mousedown already handles it, but keep for clarity)
  // Commit text when clicking outside overlay
  document.addEventListener("mousedown", (e) => {
    if (e.target !== txtInput && e.target !== canvas) {
      commitText();
    }
  });

  /* ── Keyboard shortcuts ── */
  document.addEventListener("keydown", (e) => {
    if (e.target === txtInput) return;
    if ((e.ctrlKey || e.metaKey) && e.key === "z") {
      e.preventDefault();
      if (e.shiftKey) redo(); else undo();
    }
    if ((e.ctrlKey || e.metaKey) && e.key === "y") {
      e.preventDefault();
      redo();
    }
  });

  /* ── Init ── */
  initCanvas();
})();
</script>
</div>
