---
title: "SVGパスエディター — 無料ビジュアルツール"
date: 2025-08-05
description: "無料オンラインSVGパスエディター＆ビューアー。パスデータを貼り付けて即座にプレビュー、図形プリセット、ストローク・塗りのカスタマイズ、最適化SVGコードのコピー。"
categories: ["無料ツール"]
slug: "svg-path-editor"
ShowToc: false
aliases:
  - "/ja/tools/svg-icon-maker/"
  - "/ja/tools/svg-path-editor/"
cover:
  image: "/images/covers/svg-path-editor-ja.png"
  alt: "SVGパスエディター"
---

<div id="svg-app">
<style>
#svg-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Segoe UI", Roboto, sans-serif;
  max-width: 960px;
  margin: 0 auto;
  color: #1a1a1a;
}
#svg-app * {
  box-sizing: border-box;
}
#svg-app h2.svg-tool-title {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
  color: #111;
}
#svg-app .svg-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
  align-items: start;
}
@media (max-width: 680px) {
  #svg-app .svg-layout {
    grid-template-columns: 1fr;
  }
}
#svg-app .svg-panel {
  background: #f8f9fa;
  border: 1px solid #dee2e6;
  border-radius: 10px;
  padding: 1rem;
}
#svg-app .svg-panel-title {
  font-size: 0.78rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #6c757d;
  margin: 0 0 0.6rem 0;
}
#svg-app textarea#svg-path-input {
  width: 100%;
  height: 120px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.82rem;
  line-height: 1.5;
  border: 1px solid #ced4da;
  border-radius: 6px;
  padding: 0.55rem 0.7rem;
  resize: vertical;
  background: #fff;
  color: #212529;
  outline: none;
  transition: border-color 0.15s;
}
#svg-app textarea#svg-path-input:focus {
  border-color: #e63946;
  box-shadow: 0 0 0 3px rgba(230,57,70,0.15);
}
#svg-app .svg-presets-label {
  font-size: 0.78rem;
  font-weight: 600;
  color: #495057;
  margin: 0.75rem 0 0.4rem 0;
  display: block;
}
#svg-app .svg-presets-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
}
#svg-app .svg-preset-btn {
  background: #fff;
  border: 1px solid #ced4da;
  border-radius: 5px;
  padding: 0.28rem 0.65rem;
  font-size: 0.78rem;
  cursor: pointer;
  color: #343a40;
  transition: all 0.15s;
  line-height: 1.4;
}
#svg-app .svg-preset-btn:hover {
  background: #e63946;
  color: #fff;
  border-color: #e63946;
}
#svg-app .svg-controls-row {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 0.75rem;
  align-items: flex-end;
}
#svg-app .svg-control-group {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  min-width: 70px;
}
#svg-app .svg-control-group label {
  font-size: 0.72rem;
  font-weight: 600;
  color: #6c757d;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#svg-app .svg-control-group input[type="number"],
#svg-app .svg-control-group input[type="range"] {
  border: 1px solid #ced4da;
  border-radius: 5px;
  padding: 0.3rem 0.4rem;
  font-size: 0.82rem;
  background: #fff;
  color: #212529;
  outline: none;
  width: 100%;
}
#svg-app .svg-control-group input[type="number"]:focus {
  border-color: #e63946;
  box-shadow: 0 0 0 3px rgba(230,57,70,0.15);
}
#svg-app .svg-control-group input[type="color"] {
  border: 1px solid #ced4da;
  border-radius: 5px;
  padding: 0.15rem;
  height: 34px;
  width: 48px;
  background: #fff;
  cursor: pointer;
}
#svg-app .svg-preview-wrap {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid #ced4da;
  min-height: 260px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #fff;
  transition: background 0.2s;
}
#svg-app .svg-preview-wrap.dark-bg {
  background: #1a1a2e;
}
#svg-app .svg-preview-wrap.checker-bg {
  background-image:
    linear-gradient(45deg, #ccc 25%, transparent 25%),
    linear-gradient(-45deg, #ccc 25%, transparent 25%),
    linear-gradient(45deg, transparent 75%, #ccc 75%),
    linear-gradient(-45deg, transparent 75%, #ccc 75%);
  background-size: 16px 16px;
  background-position: 0 0, 0 8px, 8px -8px, -8px 0px;
  background-color: #fff;
}
#svg-app svg#svg-preview {
  max-width: 100%;
  max-height: 280px;
  display: block;
}
#svg-app .svg-preview-error {
  color: #dc3545;
  font-size: 0.82rem;
  padding: 0.5rem;
  text-align: center;
}
#svg-app .svg-bg-toggles {
  display: flex;
  gap: 0.4rem;
  margin-bottom: 0.6rem;
  flex-wrap: wrap;
}
#svg-app .svg-bg-btn {
  border: 1px solid #ced4da;
  border-radius: 5px;
  padding: 0.22rem 0.6rem;
  font-size: 0.75rem;
  cursor: pointer;
  background: #fff;
  color: #343a40;
  transition: all 0.15s;
}
#svg-app .svg-bg-btn.active {
  background: #e63946;
  color: #fff;
  border-color: #e63946;
}
#svg-app .svg-info-box {
  margin-top: 0.75rem;
  background: #fff;
  border: 1px solid #dee2e6;
  border-radius: 6px;
  padding: 0.6rem 0.8rem;
}
#svg-app .svg-info-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.3rem 1rem;
}
#svg-app .svg-info-item {
  display: flex;
  flex-direction: column;
}
#svg-app .svg-info-key {
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  color: #6c757d;
  letter-spacing: 0.05em;
}
#svg-app .svg-info-val {
  font-size: 0.82rem;
  font-family: "SFMono-Regular", Consolas, monospace;
  color: #212529;
}
#svg-app .svg-actions-row {
  display: flex;
  flex-wrap: wrap;
  gap: 0.45rem;
  margin-top: 0.75rem;
}
#svg-app .svg-action-btn {
  padding: 0.4rem 0.85rem;
  font-size: 0.82rem;
  font-weight: 600;
  border-radius: 6px;
  border: 1px solid #ced4da;
  cursor: pointer;
  background: #fff;
  color: #343a40;
  transition: all 0.15s;
}
#svg-app .svg-action-btn:hover {
  background: #e63946;
  color: #fff;
  border-color: #e63946;
}
#svg-app .svg-action-btn.primary {
  background: #e63946;
  color: #fff;
  border-color: #e63946;
}
#svg-app .svg-action-btn.primary:hover {
  background: #c1121f;
  border-color: #c1121f;
}
#svg-app .svg-action-btn.success {
  background: #2d9e6b;
  color: #fff;
  border-color: #2d9e6b;
}
#svg-app .svg-action-btn.success:hover {
  background: #237a53;
  border-color: #237a53;
}
#svg-app .svg-output-area {
  margin-top: 1rem;
}
#svg-app .svg-output-label {
  font-size: 0.78rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #6c757d;
  margin-bottom: 0.4rem;
}
#svg-app textarea#svg-output-code {
  width: 100%;
  height: 90px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.78rem;
  line-height: 1.5;
  border: 1px solid #ced4da;
  border-radius: 6px;
  padding: 0.5rem 0.65rem;
  resize: vertical;
  background: #f1f3f5;
  color: #212529;
  outline: none;
}
#svg-app .svg-toast {
  position: fixed;
  bottom: 1.5rem;
  right: 1.5rem;
  background: #212529;
  color: #fff;
  padding: 0.55rem 1.1rem;
  border-radius: 8px;
  font-size: 0.85rem;
  font-weight: 500;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s;
  z-index: 9999;
}
#svg-app .svg-toast.show {
  opacity: 1;
}
#svg-app .svg-section-sep {
  margin: 1.25rem 0 0 0;
}
#svg-app .svg-transform-row {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 0.5rem;
  margin-top: 0.5rem;
}
@media (max-width: 480px) {
  #svg-app .svg-transform-row {
    grid-template-columns: 1fr 1fr;
  }
  #svg-app .svg-info-grid {
    grid-template-columns: 1fr;
  }
}
</style>

<h2 class="svg-tool-title">SVGパスエディター</h2>

<div class="svg-layout">
  <!-- 左: 入力・コントロール -->
  <div>
    <div class="svg-panel">
      <p class="svg-panel-title">パスデータ（d属性）</p>
      <textarea id="svg-path-input" placeholder="SVGパスデータをここに貼り付け（例: M 10 10 L 90 90 Z）" spellcheck="false"></textarea>

      <span class="svg-presets-label">図形プリセット</span>
      <div class="svg-presets-grid">
        <button class="svg-preset-btn" data-shape="circle">円</button>
        <button class="svg-preset-btn" data-shape="star">星</button>
        <button class="svg-preset-btn" data-shape="heart">ハート</button>
        <button class="svg-preset-btn" data-shape="arrow">矢印</button>
        <button class="svg-preset-btn" data-shape="checkmark">チェック</button>
        <button class="svg-preset-btn" data-shape="xmark">バツ印</button>
        <button class="svg-preset-btn" data-shape="triangle">三角形</button>
        <button class="svg-preset-btn" data-shape="hexagon">六角形</button>
      </div>
    </div>

    <div class="svg-panel svg-section-sep">
      <p class="svg-panel-title">ストローク・塗り</p>
      <div class="svg-controls-row">
        <div class="svg-control-group">
          <label>線の色</label>
          <input type="color" id="svg-stroke-color" value="#e63946">
        </div>
        <div class="svg-control-group" style="flex:1;min-width:100px;">
          <label>線の太さ</label>
          <input type="number" id="svg-stroke-width" value="2" min="0" max="20" step="0.5">
        </div>
        <div class="svg-control-group">
          <label>塗りの色</label>
          <input type="color" id="svg-fill-color" value="#ffb3b8">
        </div>
        <div class="svg-control-group" style="flex:1;min-width:80px;">
          <label>塗り透明度</label>
          <input type="number" id="svg-fill-opacity" value="0.3" min="0" max="1" step="0.05">
        </div>
      </div>
    </div>

    <div class="svg-panel svg-section-sep">
      <p class="svg-panel-title">拡縮・移動</p>
      <div class="svg-transform-row">
        <div class="svg-control-group">
          <label>スケールX</label>
          <input type="number" id="svg-scale-x" value="1" min="0.1" max="10" step="0.1">
        </div>
        <div class="svg-control-group">
          <label>スケールY</label>
          <input type="number" id="svg-scale-y" value="1" min="0.1" max="10" step="0.1">
        </div>
        <div class="svg-control-group">
          <label>移動X</label>
          <input type="number" id="svg-translate-x" value="0" step="1">
        </div>
        <div class="svg-control-group">
          <label>移動Y</label>
          <input type="number" id="svg-translate-y" value="0" step="1">
        </div>
      </div>
    </div>
  </div>

  <!-- 右: プレビュー・出力 -->
  <div>
    <div class="svg-panel">
      <p class="svg-panel-title">プレビュー</p>
      <div class="svg-bg-toggles">
        <button class="svg-bg-btn active" data-bg="light">ライト</button>
        <button class="svg-bg-btn" data-bg="dark">ダーク</button>
        <button class="svg-bg-btn" data-bg="checker">チェッカー</button>
      </div>
      <div class="svg-preview-wrap" id="svg-preview-wrap">
        <svg id="svg-preview" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200" width="200" height="200">
          <path id="svg-preview-path" d="" />
        </svg>
        <div class="svg-preview-error" id="svg-preview-error" style="display:none"></div>
      </div>

      <div class="svg-info-box">
        <div class="svg-info-grid">
          <div class="svg-info-item">
            <span class="svg-info-key">コマンド数</span>
            <span class="svg-info-val" id="info-commands">—</span>
          </div>
          <div class="svg-info-item">
            <span class="svg-info-key">パス長</span>
            <span class="svg-info-val" id="info-length">—</span>
          </div>
          <div class="svg-info-item">
            <span class="svg-info-key">バウンディングボックス</span>
            <span class="svg-info-val" id="info-bbox">—</span>
          </div>
          <div class="svg-info-item">
            <span class="svg-info-key">データサイズ</span>
            <span class="svg-info-val" id="info-size">—</span>
          </div>
        </div>
      </div>
    </div>

    <div class="svg-panel svg-section-sep">
      <p class="svg-panel-title">出力・アクション</p>
      <div class="svg-actions-row">
        <button class="svg-action-btn" id="svg-btn-minify">圧縮</button>
        <button class="svg-action-btn" id="svg-btn-prettify">整形</button>
        <button class="svg-action-btn primary" id="svg-btn-copy-svg">SVGコードをコピー</button>
        <button class="svg-action-btn success" id="svg-btn-copy-path">パスデータをコピー</button>
        <button class="svg-action-btn" id="svg-btn-reset">リセット</button>
      </div>
      <div class="svg-output-area">
        <div class="svg-output-label">生成されたSVGコード</div>
        <textarea id="svg-output-code" readonly></textarea>
      </div>
    </div>
  </div>
</div>

<div class="svg-toast" id="svg-toast">コピーしました！</div>

<script>
(function() {
  "use strict";

  var PRESETS = {
    circle: "M 100 20 A 80 80 0 1 1 99.999 20 Z",
    star: "M 100 10 L 122 78 L 195 78 L 137 122 L 160 190 L 100 148 L 40 190 L 63 122 L 5 78 L 78 78 Z",
    heart: "M 100 170 C 20 120 10 60 50 40 C 70 30 90 38 100 55 C 110 38 130 30 150 40 C 190 60 180 120 100 170 Z",
    arrow: "M 10 85 L 130 85 L 130 60 L 190 100 L 130 140 L 130 115 L 10 115 Z",
    checkmark: "M 20 100 L 70 155 L 180 45",
    xmark: "M 30 30 L 170 170 M 170 30 L 30 170",
    triangle: "M 100 15 L 185 175 L 15 175 Z",
    hexagon: "M 100 15 L 178 57.5 L 178 142.5 L 100 185 L 22 142.5 L 22 57.5 Z"
  };

  var pathInput = document.getElementById("svg-path-input");
  var previewPath = document.getElementById("svg-preview-path");
  var previewSvg = document.getElementById("svg-preview");
  var previewWrap = document.getElementById("svg-preview-wrap");
  var previewError = document.getElementById("svg-preview-error");
  var strokeColorEl = document.getElementById("svg-stroke-color");
  var strokeWidthEl = document.getElementById("svg-stroke-width");
  var fillColorEl = document.getElementById("svg-fill-color");
  var fillOpacityEl = document.getElementById("svg-fill-opacity");
  var scaleXEl = document.getElementById("svg-scale-x");
  var scaleYEl = document.getElementById("svg-scale-y");
  var translateXEl = document.getElementById("svg-translate-x");
  var translateYEl = document.getElementById("svg-translate-y");
  var outputCode = document.getElementById("svg-output-code");
  var toastEl = document.getElementById("svg-toast");
  var infoCommands = document.getElementById("info-commands");
  var infoLength = document.getElementById("info-length");
  var infoBbox = document.getElementById("info-bbox");
  var infoSize = document.getElementById("info-size");

  var toastTimer = null;

  function showToast(msg) {
    toastEl.textContent = msg || "コピーしました！";
    toastEl.classList.add("show");
    if (toastTimer) clearTimeout(toastTimer);
    toastTimer = setTimeout(function() {
      toastEl.classList.remove("show");
    }, 2000);
  }

  function countCommands(d) {
    if (!d) return 0;
    var matches = d.match(/[MmZzLlHhVvCcSsQqTtAa]/g);
    return matches ? matches.length : 0;
  }

  function updatePreview() {
    var raw = pathInput.value.trim();
    var strokeColor = strokeColorEl.value;
    var strokeWidth = parseFloat(strokeWidthEl.value) || 2;
    var fillColor = fillColorEl.value;
    var fillOpacity = parseFloat(fillOpacityEl.value);
    if (isNaN(fillOpacity)) fillOpacity = 0.3;
    var sx = parseFloat(scaleXEl.value) || 1;
    var sy = parseFloat(scaleYEl.value) || 1;
    var tx = parseFloat(translateXEl.value) || 0;
    var ty = parseFloat(translateYEl.value) || 0;

    if (!raw) {
      previewPath.setAttribute("d", "");
      previewError.style.display = "none";
      infoCommands.textContent = "—";
      infoLength.textContent = "—";
      infoBbox.textContent = "—";
      infoSize.textContent = "—";
      outputCode.value = "";
      return;
    }

    var transform = "";
    if (sx !== 1 || sy !== 1 || tx !== 0 || ty !== 0) {
      transform = "translate(" + tx + "," + ty + ") scale(" + sx + "," + sy + ")";
    }

    previewPath.setAttribute("d", raw);
    previewPath.setAttribute("stroke", strokeColor);
    previewPath.setAttribute("stroke-width", strokeWidth);
    previewPath.setAttribute("fill", fillColor);
    previewPath.setAttribute("fill-opacity", fillOpacity);
    previewPath.setAttribute("stroke-linecap", "round");
    previewPath.setAttribute("stroke-linejoin", "round");
    if (transform) {
      previewPath.setAttribute("transform", transform);
    } else {
      previewPath.removeAttribute("transform");
    }

    previewError.style.display = "none";

    var cmdCount = countCommands(raw);
    infoCommands.textContent = cmdCount + " 個";
    infoSize.textContent = raw.length + " 文字";

    try {
      var bbox = previewPath.getBBox();
      if (bbox.width > 0 || bbox.height > 0) {
        infoBbox.textContent = Math.round(bbox.width) + "\u00d7" + Math.round(bbox.height) + " @ " + Math.round(bbox.x) + "," + Math.round(bbox.y);
        var pad = Math.max(strokeWidth * 2, 10);
        var vbX = bbox.x - pad;
        var vbY = bbox.y - pad;
        var vbW = bbox.width + pad * 2;
        var vbH = bbox.height + pad * 2;
        previewSvg.setAttribute("viewBox", vbX + " " + vbY + " " + vbW + " " + vbH);
      } else {
        infoBbox.textContent = "—";
      }
    } catch(e) {
      infoBbox.textContent = "N/A";
    }

    try {
      var len = previewPath.getTotalLength();
      infoLength.textContent = Math.round(len) + " px";
    } catch(e) {
      infoLength.textContent = "N/A";
    }

    var svgW = 200, svgH = 200;
    try {
      var b = previewPath.getBBox();
      svgW = Math.ceil(b.width + Math.max(strokeWidth*2,10)*2);
      svgH = Math.ceil(b.height + Math.max(strokeWidth*2,10)*2);
    } catch(e) {}

    var transformAttr = transform ? (' transform="' + transform + '"') : "";
    var svgCode = '<svg xmlns="http://www.w3.org/2000/svg" viewBox="' +
      previewSvg.getAttribute("viewBox") + '" width="' + svgW + '" height="' + svgH + '">\n' +
      '  <path d="' + raw + '"' + transformAttr +
      ' stroke="' + strokeColor + '" stroke-width="' + strokeWidth + '"' +
      ' fill="' + fillColor + '" fill-opacity="' + fillOpacity + '"' +
      ' stroke-linecap="round" stroke-linejoin="round"/>\n' +
      '</svg>';
    outputCode.value = svgCode;
  }

  function minifyPath(d) {
    return d.replace(/\s+/g, " ")
            .replace(/\s*([MmZzLlHhVvCcSsQqTtAa,])\s*/g, "$1")
            .replace(/,/g, " ")
            .trim();
  }

  function prettifyPath(d) {
    return d.replace(/([MmZzLlHhVvCcSsQqTtAa])/g, "\n$1 ")
            .replace(/\s+/g, " ")
            .trim();
  }

  pathInput.addEventListener("input", updatePreview);
  strokeColorEl.addEventListener("input", updatePreview);
  strokeWidthEl.addEventListener("input", updatePreview);
  fillColorEl.addEventListener("input", updatePreview);
  fillOpacityEl.addEventListener("input", updatePreview);
  scaleXEl.addEventListener("input", updatePreview);
  scaleYEl.addEventListener("input", updatePreview);
  translateXEl.addEventListener("input", updatePreview);
  translateYEl.addEventListener("input", updatePreview);

  document.querySelectorAll("#svg-app .svg-preset-btn").forEach(function(btn) {
    btn.addEventListener("click", function() {
      var shape = btn.getAttribute("data-shape");
      if (PRESETS[shape]) {
        pathInput.value = PRESETS[shape];
        updatePreview();
      }
    });
  });

  document.querySelectorAll("#svg-app .svg-bg-btn").forEach(function(btn) {
    btn.addEventListener("click", function() {
      document.querySelectorAll("#svg-app .svg-bg-btn").forEach(function(b) { b.classList.remove("active"); });
      btn.classList.add("active");
      var bg = btn.getAttribute("data-bg");
      previewWrap.classList.remove("dark-bg", "checker-bg");
      if (bg === "dark") previewWrap.classList.add("dark-bg");
      else if (bg === "checker") previewWrap.classList.add("checker-bg");
    });
  });

  document.getElementById("svg-btn-minify").addEventListener("click", function() {
    var d = pathInput.value.trim();
    if (d) { pathInput.value = minifyPath(d); updatePreview(); }
  });

  document.getElementById("svg-btn-prettify").addEventListener("click", function() {
    var d = pathInput.value.trim();
    if (d) { pathInput.value = prettifyPath(d); updatePreview(); }
  });

  document.getElementById("svg-btn-copy-svg").addEventListener("click", function() {
    if (!outputCode.value) return;
    navigator.clipboard.writeText(outputCode.value).then(function() {
      showToast("SVGコードをコピーしました！");
    }).catch(function() {
      outputCode.select();
      document.execCommand("copy");
      showToast("SVGコードをコピーしました！");
    });
  });

  document.getElementById("svg-btn-copy-path").addEventListener("click", function() {
    var d = pathInput.value.trim();
    if (!d) return;
    navigator.clipboard.writeText(d).then(function() {
      showToast("パスデータをコピーしました！");
    }).catch(function() {
      pathInput.select();
      document.execCommand("copy");
      showToast("パスデータをコピーしました！");
    });
  });

  document.getElementById("svg-btn-reset").addEventListener("click", function() {
    pathInput.value = "";
    strokeColorEl.value = "#e63946";
    strokeWidthEl.value = "2";
    fillColorEl.value = "#ffb3b8";
    fillOpacityEl.value = "0.3";
    scaleXEl.value = "1";
    scaleYEl.value = "1";
    translateXEl.value = "0";
    translateYEl.value = "0";
    previewSvg.setAttribute("viewBox", "0 0 200 200");
    updatePreview();
  });

  // デフォルトで星を表示
  pathInput.value = PRESETS["star"];
  updatePreview();
})();
</script>
</div>

---

### 関連ツール

> CSSグラデーションを生成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)

> カラーパレットを生成 → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)

> ファビコンを作成 → [ファビコンジェネレーター](/ja/tools/favicon-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
