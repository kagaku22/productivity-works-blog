---
title: "CSS Clip-Pathジェネレーター — シェイプビルダー"
date: 2025-07-08
description: "CSSクリップパスをビジュアルで作成。プリセット図形・カスタムポリゴン・インタラクティブなポイント編集。CSSコードをワンクリックコピー。"
categories: ["無料ツール"]
slug: "clip-path-generator"
ShowToc: false
aliases:
  - "/ja/tools/clip-path-generator/"
  - "/ja/tools/clip-path-generator/"
cover:
  image: "/images/covers/clip-path-generator-ja.png"
  alt: "CSS Clip-Pathジェネレーター"
---

<div id="cp-app">

<style>
#cp-app *,
#cp-app *::before,
#cp-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#cp-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Segoe UI", sans-serif;
  color: #1a1a2e;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 0 2rem 0;
}
#cp-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: #16213e;
}
#cp-app .cp-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  align-items: start;
}
@media (max-width: 700px) {
  #cp-app .cp-layout {
    grid-template-columns: 1fr;
  }
}
/* Controls panel */
#cp-app .cp-controls {
  background: #f8f9fc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
}
#cp-app .cp-section-label {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #718096;
  margin-bottom: 0.45rem;
}
/* Shape type tabs */
#cp-app .cp-shape-tabs {
  display: flex;
  gap: 0.4rem;
  flex-wrap: wrap;
}
#cp-app .cp-tab {
  padding: 0.35rem 0.75rem;
  border-radius: 20px;
  border: 1.5px solid #cbd5e0;
  background: #fff;
  font-size: 0.82rem;
  cursor: pointer;
  transition: all 0.15s;
  color: #4a5568;
  font-weight: 500;
}
#cp-app .cp-tab:hover {
  border-color: #667eea;
  color: #667eea;
}
#cp-app .cp-tab.active {
  background: #667eea;
  border-color: #667eea;
  color: #fff;
}
/* Preset grid */
#cp-app .cp-presets-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 0.5rem;
}
@media (max-width: 400px) {
  #cp-app .cp-presets-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
#cp-app .cp-preset-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.5rem 0.25rem;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  transition: all 0.15s;
  font-size: 0.68rem;
  color: #4a5568;
  font-weight: 500;
}
#cp-app .cp-preset-btn:hover {
  border-color: #667eea;
  color: #667eea;
  background: #f0f4ff;
}
#cp-app .cp-preset-btn.active {
  border-color: #667eea;
  background: #eef1ff;
  color: #667eea;
}
#cp-app .cp-preset-icon {
  width: 32px;
  height: 32px;
  display: block;
}
/* Sliders */
#cp-app .cp-slider-row {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin-bottom: 0.4rem;
}
#cp-app .cp-slider-row label {
  font-size: 0.8rem;
  color: #4a5568;
  min-width: 80px;
  flex-shrink: 0;
}
#cp-app .cp-slider-row input[type=range] {
  flex: 1;
  accent-color: #667eea;
  height: 4px;
  cursor: pointer;
}
#cp-app .cp-slider-val {
  font-size: 0.78rem;
  color: #667eea;
  font-weight: 700;
  min-width: 38px;
  text-align: right;
}
/* Color picker */
#cp-app .cp-color-row {
  display: flex;
  align-items: center;
  gap: 0.7rem;
}
#cp-app .cp-color-row label {
  font-size: 0.8rem;
  color: #4a5568;
}
#cp-app .cp-color-row input[type=color] {
  width: 38px;
  height: 32px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  padding: 2px;
  background: #fff;
  border: 1px solid #e2e8f0;
}
/* Custom polygon controls */
#cp-app .cp-custom-hint {
  font-size: 0.78rem;
  color: #718096;
  background: #fff9db;
  border: 1px solid #f6e05e;
  border-radius: 8px;
  padding: 0.55rem 0.75rem;
  line-height: 1.6;
}
#cp-app .cp-custom-actions {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}
#cp-app .cp-btn {
  padding: 0.42rem 0.9rem;
  border-radius: 8px;
  border: 1.5px solid #667eea;
  background: #667eea;
  color: #fff;
  font-size: 0.8rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#cp-app .cp-btn:hover {
  background: #5a67d8;
  border-color: #5a67d8;
}
#cp-app .cp-btn-outline {
  background: #fff;
  color: #667eea;
}
#cp-app .cp-btn-outline:hover {
  background: #eef1ff;
}
#cp-app .cp-btn-danger {
  background: #fff;
  border-color: #fc8181;
  color: #e53e3e;
}
#cp-app .cp-btn-danger:hover {
  background: #fff5f5;
}
/* Inset controls */
#cp-app .cp-inset-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.4rem 0.8rem;
}
/* Right panel */
#cp-app .cp-right {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}
/* Preview box */
#cp-app .cp-preview-wrap {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.25rem;
}
#cp-app .cp-preview-label {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #718096;
  margin-bottom: 0.75rem;
}
#cp-app .cp-canvas-wrap {
  position: relative;
  width: 100%;
  padding-bottom: 70%;
  background: repeating-conic-gradient(#f0f0f0 0% 25%, #fff 0% 50%) 0 0 / 18px 18px;
  border-radius: 8px;
  overflow: hidden;
  cursor: crosshair;
}
#cp-app .cp-shape-el {
  position: absolute;
  inset: 0;
  background: #667eea;
  transition: clip-path 0.1s;
}
#cp-app .cp-point-dot {
  position: absolute;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #fff;
  border: 2.5px solid #e53e3e;
  transform: translate(-50%, -50%);
  cursor: grab;
  z-index: 10;
  touch-action: none;
}
#cp-app .cp-point-dot:hover {
  background: #fff5f5;
  border-color: #c53030;
}
/* Output box */
#cp-app .cp-output-wrap {
  background: #1a1a2e;
  border-radius: 12px;
  padding: 1.1rem 1.25rem;
}
#cp-app .cp-output-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 0.6rem;
}
#cp-app .cp-output-title {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #a0aec0;
}
#cp-app .cp-copy-btn {
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  border: 1.5px solid #4a5568;
  background: transparent;
  color: #a0aec0;
  font-size: 0.75rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
#cp-app .cp-copy-btn:hover {
  border-color: #667eea;
  color: #667eea;
}
#cp-app .cp-copy-btn.copied {
  border-color: #48bb78;
  color: #48bb78;
}
#cp-app .cp-output-code {
  font-family: "Fira Mono", "Cascadia Code", "Consolas", monospace;
  font-size: 0.82rem;
  color: #90cdf4;
  line-height: 1.7;
  word-break: break-all;
  white-space: pre-wrap;
}
#cp-app .cp-output-code .cp-prop {
  color: #f6ad55;
}
#cp-app .cp-output-code .cp-val {
  color: #68d391;
}
/* Points list */
#cp-app .cp-points-list {
  font-size: 0.75rem;
  color: #718096;
  background: #f8f9fc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 0.6rem 0.75rem;
  max-height: 90px;
  overflow-y: auto;
  line-height: 1.7;
  font-family: monospace;
}
/* freee CTA */
#cp-app .cp-freee-cta {
  margin-top: 2rem;
  background: linear-gradient(135deg, #eef1ff 0%, #f0fff4 100%);
  border: 1px solid #c3dafe;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}
#cp-app .cp-freee-cta-icon {
  font-size: 2rem;
  flex-shrink: 0;
}
#cp-app .cp-freee-cta-body {
  flex: 1;
  min-width: 180px;
}
#cp-app .cp-freee-cta-body strong {
  display: block;
  font-size: 0.95rem;
  color: #2d3748;
  margin-bottom: 0.2rem;
}
#cp-app .cp-freee-cta-body p {
  font-size: 0.8rem;
  color: #718096;
  line-height: 1.5;
}
#cp-app .cp-freee-cta-link {
  display: inline-block;
  padding: 0.5rem 1.1rem;
  background: #38a169;
  color: #fff;
  border-radius: 8px;
  font-size: 0.82rem;
  font-weight: 700;
  text-decoration: none;
  white-space: nowrap;
  transition: background 0.15s;
}
#cp-app .cp-freee-cta-link:hover {
  background: #2f855a;
  color: #fff;
}
</style>

<div class="cp-layout">

  <!-- LEFT: Controls -->
  <div class="cp-controls">

    <!-- Shape Type -->
    <div>
      <div class="cp-section-label">図形タイプ</div>
      <div class="cp-shape-tabs">
        <button class="cp-tab active" data-type="polygon" onclick="cpjaSetType('polygon')">ポリゴン</button>
        <button class="cp-tab" data-type="circle" onclick="cpjaSetType('circle')">円</button>
        <button class="cp-tab" data-type="ellipse" onclick="cpjaSetType('ellipse')">楕円</button>
        <button class="cp-tab" data-type="inset" onclick="cpjaSetType('inset')">インセット</button>
        <button class="cp-tab" data-type="custom" onclick="cpjaSetType('custom')">カスタム</button>
      </div>
    </div>

    <!-- Polygon Presets -->
    <div id="cpja-polygon-panel">
      <div class="cp-section-label">プリセット図形</div>
      <div class="cp-presets-grid">
        <button class="cp-preset-btn active" data-preset="triangle" onclick="cpjaLoadPreset('triangle')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,4 30,28 2,28" fill="#667eea"/></svg>
          三角形
        </button>
        <button class="cp-preset-btn" data-preset="diamond" onclick="cpjaLoadPreset('diamond')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 30,16 16,30 2,16" fill="#667eea"/></svg>
          菱形
        </button>
        <button class="cp-preset-btn" data-preset="pentagon" onclick="cpjaLoadPreset('pentagon')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 29,11 24,27 8,27 3,11" fill="#667eea"/></svg>
          五角形
        </button>
        <button class="cp-preset-btn" data-preset="hexagon" onclick="cpjaLoadPreset('hexagon')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 28,9 28,23 16,30 4,23 4,9" fill="#667eea"/></svg>
          六角形
        </button>
        <button class="cp-preset-btn" data-preset="octagon" onclick="cpjaLoadPreset('octagon')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="10,2 22,2 30,10 30,22 22,30 10,30 2,22 2,10" fill="#667eea"/></svg>
          八角形
        </button>
        <button class="cp-preset-btn" data-preset="star" onclick="cpjaLoadPreset('star')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 19.5,12 30,12 21.5,18.5 24.5,29 16,22.5 7.5,29 10.5,18.5 2,12 12.5,12" fill="#667eea"/></svg>
          星形
        </button>
        <button class="cp-preset-btn" data-preset="arrow" onclick="cpjaLoadPreset('arrow')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="2,10 18,10 18,4 30,16 18,28 18,22 2,22" fill="#667eea"/></svg>
          矢印
        </button>
        <button class="cp-preset-btn" data-preset="cross" onclick="cpjaLoadPreset('cross')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="10,2 22,2 22,10 30,10 30,22 22,22 22,30 10,30 10,22 2,22 2,10 10,10" fill="#667eea"/></svg>
          十字
        </button>
        <button class="cp-preset-btn" data-preset="heart" onclick="cpjaLoadPreset('heart')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><path d="M16,28 C16,28 3,18 3,10 C3,6 6,3 10,3 C12.5,3 15,5 16,7 C17,5 19.5,3 22,3 C26,3 29,6 29,10 C29,18 16,28 16,28Z" fill="#667eea"/></svg>
          ハート
        </button>
        <button class="cp-preset-btn" data-preset="chevron" onclick="cpjaLoadPreset('chevron')">
          <svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="2,6 18,6 30,16 18,26 2,26 14,16" fill="#667eea"/></svg>
          シェブロン
        </button>
      </div>
    </div>

    <!-- Circle controls -->
    <div id="cpja-circle-panel" style="display:none">
      <div class="cp-section-label">円の設定</div>
      <div class="cp-slider-row">
        <label>半径</label>
        <input type="range" id="cpja-circle-r" min="10" max="50" value="50" oninput="cpjaUpdateCircle()">
        <span class="cp-slider-val" id="cpja-circle-r-val">50%</span>
      </div>
      <div class="cp-slider-row">
        <label>中心 X</label>
        <input type="range" id="cpja-circle-cx" min="0" max="100" value="50" oninput="cpjaUpdateCircle()">
        <span class="cp-slider-val" id="cpja-circle-cx-val">50%</span>
      </div>
      <div class="cp-slider-row">
        <label>中心 Y</label>
        <input type="range" id="cpja-circle-cy" min="0" max="100" value="50" oninput="cpjaUpdateCircle()">
        <span class="cp-slider-val" id="cpja-circle-cy-val">50%</span>
      </div>
    </div>

    <!-- Ellipse controls -->
    <div id="cpja-ellipse-panel" style="display:none">
      <div class="cp-section-label">楕円の設定</div>
      <div class="cp-slider-row">
        <label>半径 X</label>
        <input type="range" id="cpja-ellipse-rx" min="5" max="50" value="50" oninput="cpjaUpdateEllipse()">
        <span class="cp-slider-val" id="cpja-ellipse-rx-val">50%</span>
      </div>
      <div class="cp-slider-row">
        <label>半径 Y</label>
        <input type="range" id="cpja-ellipse-ry" min="5" max="50" value="30" oninput="cpjaUpdateEllipse()">
        <span class="cp-slider-val" id="cpja-ellipse-ry-val">30%</span>
      </div>
      <div class="cp-slider-row">
        <label>中心 X</label>
        <input type="range" id="cpja-ellipse-cx" min="0" max="100" value="50" oninput="cpjaUpdateEllipse()">
        <span class="cp-slider-val" id="cpja-ellipse-cx-val">50%</span>
      </div>
      <div class="cp-slider-row">
        <label>中心 Y</label>
        <input type="range" id="cpja-ellipse-cy" min="0" max="100" value="50" oninput="cpjaUpdateEllipse()">
        <span class="cp-slider-val" id="cpja-ellipse-cy-val">50%</span>
      </div>
    </div>

    <!-- Inset controls -->
    <div id="cpja-inset-panel" style="display:none">
      <div class="cp-section-label">インセット設定</div>
      <div class="cp-inset-grid">
        <div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
          <label>上</label>
          <input type="range" id="cpja-inset-t" min="0" max="49" value="10" oninput="cpjaUpdateInset()">
          <span class="cp-slider-val" id="cpja-inset-t-val" style="min-width:auto">10%</span>
        </div>
        <div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
          <label>右</label>
          <input type="range" id="cpja-inset-r" min="0" max="49" value="10" oninput="cpjaUpdateInset()">
          <span class="cp-slider-val" id="cpja-inset-r-val" style="min-width:auto">10%</span>
        </div>
        <div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
          <label>下</label>
          <input type="range" id="cpja-inset-b" min="0" max="49" value="10" oninput="cpjaUpdateInset()">
          <span class="cp-slider-val" id="cpja-inset-b-val" style="min-width:auto">10%</span>
        </div>
        <div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
          <label>左</label>
          <input type="range" id="cpja-inset-l" min="0" max="49" value="10" oninput="cpjaUpdateInset()">
          <span class="cp-slider-val" id="cpja-inset-l-val" style="min-width:auto">10%</span>
        </div>
      </div>
      <div class="cp-slider-row" style="margin-top:0.5rem">
        <label>角丸半径</label>
        <input type="range" id="cpja-inset-br" min="0" max="50" value="0" oninput="cpjaUpdateInset()">
        <span class="cp-slider-val" id="cpja-inset-br-val">0%</span>
      </div>
    </div>

    <!-- Custom polygon panel -->
    <div id="cpja-custom-panel" style="display:none">
      <div class="cp-section-label">カスタムポリゴン</div>
      <div class="cp-custom-hint">
        プレビューエリアをクリックしてポイントを追加。ドラッグで移動、右クリックで削除できます。
      </div>
      <div class="cp-custom-actions" style="margin-top:0.6rem">
        <button class="cp-btn cp-btn-outline" onclick="cpjaUndoPoint()">元に戻す</button>
        <button class="cp-btn cp-btn-danger" onclick="cpjaClearPoints()">全消去</button>
      </div>
      <div class="cp-points-list" id="cpja-points-list">ポイントなし — プレビューをクリックして開始。</div>
    </div>

    <!-- Background color -->
    <div>
      <div class="cp-section-label">プレビューオプション</div>
      <div class="cp-color-row">
        <label>図形の色</label>
        <input type="color" id="cpja-shape-color" value="#667eea" oninput="cpjaUpdateColor()">
      </div>
    </div>

  </div><!-- /cp-controls -->

  <!-- RIGHT: Preview + Output -->
  <div class="cp-right">

    <div class="cp-preview-wrap">
      <div class="cp-preview-label">ライブプレビュー — <span id="cpja-preview-size-label"></span></div>
      <div class="cp-canvas-wrap" id="cpja-canvas" onclick="cpjaCanvasClick(event)">
        <div class="cp-shape-el" id="cpja-shape"></div>
      </div>
    </div>

    <div class="cp-output-wrap">
      <div class="cp-output-header">
        <span class="cp-output-title">CSS出力</span>
        <button class="cp-copy-btn" id="cpja-copy-btn" onclick="cpjaCopyCSS()">コピー</button>
      </div>
      <div class="cp-output-code" id="cpja-output-code"></div>
    </div>

  </div><!-- /cp-right -->

</div><!-- /cp-layout -->

<!-- freee CTA -->
<div class="cp-freee-cta">
  <div class="cp-freee-cta-icon">🟢</div>
  <div class="cp-freee-cta-body">
    <strong>フリーランス・個人事業主の方へ — freeeで経理・確定申告を自動化</strong>
    <p>ツール制作などの副業・フリーランス収入も、freeeなら帳簿付けから確定申告まで簡単に管理できます。</p>
  </div>
  <a class="cp-freee-cta-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを試す</a>
</div>

</div><!-- /cp-app -->

<script>
(function() {
  // ── State ──────────────────────────────────────────────────────────────────
  var cpjaState = {
    type: 'polygon',
    preset: 'triangle',
    clipPath: '',
    customPoints: [],
    draggingIdx: -1,
  };

  // ── Preset definitions (% values) ─────────────────────────────────────────
  var PRESETS = {
    triangle:  [[50,0],[100,100],[0,100]],
    diamond:   [[50,0],[100,50],[50,100],[0,50]],
    pentagon:  [[50,0],[100,38],[82,100],[18,100],[0,38]],
    hexagon:   [[50,0],[100,25],[100,75],[50,100],[0,75],[0,25]],
    octagon:   [[30,0],[70,0],[100,30],[100,70],[70,100],[30,100],[0,70],[0,30]],
    star:      [[50,0],[61,35],[98,35],[68,57],[79,91],[50,70],[21,91],[32,57],[2,35],[39,35]],
    arrow:     [[0,35],[60,35],[60,10],[100,50],[60,90],[60,65],[0,65]],
    cross:     [[35,0],[65,0],[65,35],[100,35],[100,65],[65,65],[65,100],[35,100],[35,65],[0,65],[0,35],[35,35]],
    heart:     [[50,75],[15,45],[5,30],[5,20],[15,10],[25,10],[35,15],[50,30],[65,15],[75,10],[85,10],[95,20],[95,30],[85,45]],
    chevron:   [[0,20],[65,20],[100,50],[65,80],[0,80],[35,50]],
  };

  // ── Init ───────────────────────────────────────────────────────────────────
  function init() {
    updateSizeLabel();
    cpjaLoadPreset('triangle');
    window.addEventListener('resize', updateSizeLabel);
    var canvas = document.getElementById('cpja-canvas');
    canvas.addEventListener('mousemove', onMouseMove);
    canvas.addEventListener('mouseup', onMouseUp);
    canvas.addEventListener('mouseleave', onMouseUp);
    canvas.addEventListener('touchmove', onTouchMove, {passive: false});
    canvas.addEventListener('touchend', onTouchEnd);
  }

  function updateSizeLabel() {
    var canvas = document.getElementById('cpja-canvas');
    if (!canvas) return;
    var rect = canvas.getBoundingClientRect();
    document.getElementById('cpja-preview-size-label').textContent =
      Math.round(rect.width) + ' × ' + Math.round(rect.height) + 'px';
  }

  // ── Type switching ─────────────────────────────────────────────────────────
  window.cpjaSetType = function(type) {
    cpjaState.type = type;
    document.querySelectorAll('#cp-app .cp-tab').forEach(function(t) {
      t.classList.toggle('active', t.dataset.type === type);
    });
    document.getElementById('cpja-polygon-panel').style.display  = type === 'polygon'  ? '' : 'none';
    document.getElementById('cpja-circle-panel').style.display   = type === 'circle'   ? '' : 'none';
    document.getElementById('cpja-ellipse-panel').style.display  = type === 'ellipse'  ? '' : 'none';
    document.getElementById('cpja-inset-panel').style.display    = type === 'inset'    ? '' : 'none';
    document.getElementById('cpja-custom-panel').style.display   = type === 'custom'   ? '' : 'none';
    clearDots();
    if (type === 'polygon')      { cpjaLoadPreset(cpjaState.preset); }
    else if (type === 'circle')  { cpjaUpdateCircle(); }
    else if (type === 'ellipse') { cpjaUpdateEllipse(); }
    else if (type === 'inset')   { cpjaUpdateInset(); }
    else if (type === 'custom')  { renderCustomPoints(); applyClipPath(buildPolygonCSS(cpjaState.customPoints)); }
  };

  // ── Presets ────────────────────────────────────────────────────────────────
  window.cpjaLoadPreset = function(name) {
    cpjaState.preset = name;
    document.querySelectorAll('#cp-app .cp-preset-btn').forEach(function(b) {
      b.classList.toggle('active', b.dataset.preset === name);
    });
    clearDots();
    applyClipPath(buildPolygonCSS(PRESETS[name]));
  };

  function buildPolygonCSS(pts) {
    if (!pts || pts.length < 3) return 'none';
    return 'polygon(' + pts.map(function(p) { return p[0] + '% ' + p[1] + '%'; }).join(', ') + ')';
  }

  // ── Circle ─────────────────────────────────────────────────────────────────
  window.cpjaUpdateCircle = function() {
    var r  = document.getElementById('cpja-circle-r').value;
    var cx = document.getElementById('cpja-circle-cx').value;
    var cy = document.getElementById('cpja-circle-cy').value;
    document.getElementById('cpja-circle-r-val').textContent  = r + '%';
    document.getElementById('cpja-circle-cx-val').textContent = cx + '%';
    document.getElementById('cpja-circle-cy-val').textContent = cy + '%';
    applyClipPath('circle(' + r + '% at ' + cx + '% ' + cy + '%)');
  };

  // ── Ellipse ────────────────────────────────────────────────────────────────
  window.cpjaUpdateEllipse = function() {
    var rx = document.getElementById('cpja-ellipse-rx').value;
    var ry = document.getElementById('cpja-ellipse-ry').value;
    var cx = document.getElementById('cpja-ellipse-cx').value;
    var cy = document.getElementById('cpja-ellipse-cy').value;
    document.getElementById('cpja-ellipse-rx-val').textContent = rx + '%';
    document.getElementById('cpja-ellipse-ry-val').textContent = ry + '%';
    document.getElementById('cpja-ellipse-cx-val').textContent = cx + '%';
    document.getElementById('cpja-ellipse-cy-val').textContent = cy + '%';
    applyClipPath('ellipse(' + rx + '% ' + ry + '% at ' + cx + '% ' + cy + '%)');
  };

  // ── Inset ──────────────────────────────────────────────────────────────────
  window.cpjaUpdateInset = function() {
    var t  = document.getElementById('cpja-inset-t').value;
    var r  = document.getElementById('cpja-inset-r').value;
    var b  = document.getElementById('cpja-inset-b').value;
    var l  = document.getElementById('cpja-inset-l').value;
    var br = document.getElementById('cpja-inset-br').value;
    document.getElementById('cpja-inset-t-val').textContent  = t + '%';
    document.getElementById('cpja-inset-r-val').textContent  = r + '%';
    document.getElementById('cpja-inset-b-val').textContent  = b + '%';
    document.getElementById('cpja-inset-l-val').textContent  = l + '%';
    document.getElementById('cpja-inset-br-val').textContent = br + '%';
    var val = 'inset(' + t + '% ' + r + '% ' + b + '% ' + l + '%';
    if (parseInt(br) > 0) val += ' round ' + br + '%';
    val += ')';
    applyClipPath(val);
  };

  // ── Custom polygon ─────────────────────────────────────────────────────────
  window.cpjaCanvasClick = function(e) {
    if (cpjaState.type !== 'custom') return;
    if (cpjaState.draggingIdx >= 0) return;
    var pos = getCanvasPos(e);
    cpjaState.customPoints.push([Math.round(pos.x), Math.round(pos.y)]);
    renderCustomPoints();
    applyClipPath(buildPolygonCSS(cpjaState.customPoints));
  };

  window.cpjaUndoPoint = function() {
    if (cpjaState.customPoints.length > 0) {
      cpjaState.customPoints.pop();
      renderCustomPoints();
      applyClipPath(buildPolygonCSS(cpjaState.customPoints));
    }
  };

  window.cpjaClearPoints = function() {
    cpjaState.customPoints = [];
    renderCustomPoints();
    applyClipPath('none');
  };

  function getCanvasPos(e) {
    var canvas = document.getElementById('cpja-canvas');
    var rect = canvas.getBoundingClientRect();
    var clientX = e.clientX !== undefined ? e.clientX : e.touches[0].clientX;
    var clientY = e.clientY !== undefined ? e.clientY : e.touches[0].clientY;
    return {
      x: Math.min(100, Math.max(0, ((clientX - rect.left) / rect.width) * 100)),
      y: Math.min(100, Math.max(0, ((clientY - rect.top)  / rect.height) * 100))
    };
  }

  function renderCustomPoints() {
    clearDots();
    var canvas = document.getElementById('cpja-canvas');
    cpjaState.customPoints.forEach(function(pt, idx) {
      var dot = document.createElement('div');
      dot.className = 'cp-point-dot';
      dot.style.left = pt[0] + '%';
      dot.style.top  = pt[1] + '%';
      dot.dataset.idx = idx;
      dot.addEventListener('mousedown', function(e) { e.stopPropagation(); startDrag(idx, e); });
      dot.addEventListener('touchstart', function(e) { e.stopPropagation(); startDragTouch(idx, e); }, {passive: false});
      dot.addEventListener('contextmenu', function(e) {
        e.preventDefault();
        cpjaState.customPoints.splice(idx, 1);
        renderCustomPoints();
        applyClipPath(buildPolygonCSS(cpjaState.customPoints));
      });
      canvas.appendChild(dot);
    });
    var list = document.getElementById('cpja-points-list');
    if (cpjaState.customPoints.length === 0) {
      list.textContent = 'ポイントなし — プレビューをクリックして開始。';
    } else {
      list.textContent = cpjaState.customPoints.map(function(p, i) {
        return 'P' + (i+1) + ': ' + p[0] + '% ' + p[1] + '%';
      }).join('   ');
    }
  }

  function clearDots() {
    document.querySelectorAll('#cpja-canvas .cp-point-dot').forEach(function(d) { d.remove(); });
  }

  function startDrag(idx, e) { cpjaState.draggingIdx = idx; e.preventDefault(); }
  function startDragTouch(idx, e) { cpjaState.draggingIdx = idx; e.preventDefault(); }
  function onMouseMove(e) {
    if (cpjaState.draggingIdx < 0) return;
    var pos = getCanvasPos(e);
    cpjaState.customPoints[cpjaState.draggingIdx] = [Math.round(pos.x), Math.round(pos.y)];
    renderCustomPoints();
    applyClipPath(buildPolygonCSS(cpjaState.customPoints));
  }
  function onMouseUp() { cpjaState.draggingIdx = -1; }
  function onTouchMove(e) {
    if (cpjaState.draggingIdx < 0) return;
    e.preventDefault();
    var pos = getCanvasPos(e);
    cpjaState.customPoints[cpjaState.draggingIdx] = [Math.round(pos.x), Math.round(pos.y)];
    renderCustomPoints();
    applyClipPath(buildPolygonCSS(cpjaState.customPoints));
  }
  function onTouchEnd() { cpjaState.draggingIdx = -1; }

  // ── Color ──────────────────────────────────────────────────────────────────
  window.cpjaUpdateColor = function() {
    document.getElementById('cpja-shape').style.background =
      document.getElementById('cpja-shape-color').value;
  };

  // ── Apply clip-path ────────────────────────────────────────────────────────
  function applyClipPath(val) {
    cpjaState.clipPath = val;
    var shape = document.getElementById('cpja-shape');
    shape.style.clipPath = val;
    renderOutput(val);
  }

  function renderOutput(val) {
    var code = document.getElementById('cpja-output-code');
    code.innerHTML =
      '<span class="cp-prop">.your-element</span> {\n' +
      '  <span class="cp-prop">clip-path</span>: <span class="cp-val">' + escHtml(val) + '</span>;\n' +
      '  <span class="cp-prop">-webkit-clip-path</span>: <span class="cp-val">' + escHtml(val) + '</span>;\n' +
      '}';
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  // ── Copy ───────────────────────────────────────────────────────────────────
  window.cpjaCopyCSS = function() {
    var text = '.your-element {\n  clip-path: ' + cpjaState.clipPath + ';\n  -webkit-clip-path: ' + cpjaState.clipPath + ';\n}';
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(flashCopied);
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      ta.remove();
      flashCopied();
    }
  };

  function flashCopied() {
    var btn = document.getElementById('cpja-copy-btn');
    btn.textContent = 'コピー完了！';
    btn.classList.add('copied');
    setTimeout(function() {
      btn.textContent = 'コピー';
      btn.classList.remove('copied');
    }, 1800);
  }

  // ── Boot ───────────────────────────────────────────────────────────────────
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', init);
  } else {
    init();
  }
})();
</script>

---

### 関連ツール
> ボックスシャドウを生成 → [CSS Box Shadow ジェネレーター](/ja/tools/box-shadow-generator/)
> ボーダー半径を設定 → [CSS Border Radius ジェネレーター](/ja/tools/border-radius-generator/)
> SVGパスを作成 → [SVG Path エディター](/ja/tools/svg-path-editor/)
