---
title: "CSS角丸ジェネレーター — 無料ビジュアルツール"
date: 2025-05-16
description: "ビジュアルコントロールでCSS border-radiusを生成。個別コーナー・楕円値・形状プリセット対応。CSSコードをワンクリックコピー。"
categories: ["無料ツール"]
slug: "border-radius-generator"
ShowToc: false
aliases:
  - "/ja/tools/border-radius/"
  - "/ja/tools/rounded-corners/"
cover:
  image: "/images/covers/border-radius-generator-ja.png"
  alt: "CSS角丸ジェネレーター"
---

ビジュアルで直感的にCSS border-radiusを設計できるツールです。シンプルな角丸からピル・円・ブロブ・有機的なシェイプまで、プリセットとスライダーで自由に生成。CSSコードをワンクリックでコピーできます。

<div id="br-app">

<style>
/* ── リセット & ベース ─────────────────────────────────────── */
#br-app *,
#br-app *::before,
#br-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#br-app {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
  color: #1a1a2e;
  line-height: 1.5;
}

/* ── レイアウト ───────────────────────────────────────────── */
#br-app .br-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
  margin-top: 24px;
}
@media (max-width: 720px) {
  #br-app .br-layout {
    grid-template-columns: 1fr;
  }
}

/* ── パネル ───────────────────────────────────────────────── */
#br-app .br-panel {
  background: #f8f9fc;
  border: 1px solid #e2e6f0;
  border-radius: 12px;
  padding: 20px;
}
#br-app .br-panel h3 {
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: .06em;
  color: #6b7280;
  margin-bottom: 16px;
}

/* ── プレビュー ───────────────────────────────────────────── */
#br-app .br-preview-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 260px;
  background: repeating-conic-gradient(#e5e7eb 0% 25%, #f9fafb 0% 50%) 0 0 / 20px 20px;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 16px;
}
#br-app #br-preview-box {
  width: 160px;
  height: 160px;
  background: #6366f1;
  transition: border-radius .15s ease, width .15s ease, height .15s ease, background .15s ease;
}

/* ── プレビュー操作 ───────────────────────────────────────── */
#br-app .br-preview-controls {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 10px;
  align-items: end;
}
#br-app .br-preview-controls label {
  font-size: 12px;
  color: #6b7280;
  display: block;
  margin-bottom: 4px;
}
#br-app .br-preview-controls input[type="number"] {
  width: 100%;
  padding: 6px 8px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-size: 13px;
  background: #fff;
}
#br-app .br-preview-controls input[type="color"] {
  width: 100%;
  height: 34px;
  padding: 2px 4px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  cursor: pointer;
  background: #fff;
}

/* ── プリセット ───────────────────────────────────────────── */
#br-app .br-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
#br-app .br-preset-btn {
  padding: 6px 14px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  background: #fff;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background .12s, border-color .12s, color .12s;
}
#br-app .br-preset-btn:hover,
#br-app .br-preset-btn.active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}

/* ── 単位切り替え ─────────────────────────────────────────── */
#br-app .br-unit-toggle {
  display: flex;
  gap: 0;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  overflow: hidden;
  width: fit-content;
  margin-bottom: 16px;
}
#br-app .br-unit-btn {
  padding: 5px 16px;
  border: none;
  background: #fff;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background .12s, color .12s;
}
#br-app .br-unit-btn.active {
  background: #6366f1;
  color: #fff;
}

/* ── コーナーグリッド ─────────────────────────────────────── */
#br-app .br-corner-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}
#br-app .br-corner-block {
  background: #fff;
  border: 1px solid #e2e6f0;
  border-radius: 8px;
  padding: 12px;
}
#br-app .br-corner-block label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: .05em;
  color: #6366f1;
  display: block;
  margin-bottom: 8px;
}
#br-app .br-slider-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 6px;
}
#br-app .br-slider-row span {
  font-size: 11px;
  color: #9ca3af;
  width: 10px;
  flex-shrink: 0;
}
#br-app .br-slider-row input[type="range"] {
  flex: 1;
  accent-color: #6366f1;
  cursor: pointer;
}
#br-app .br-slider-row input[type="number"] {
  width: 52px;
  padding: 3px 6px;
  border: 1px solid #d1d5db;
  border-radius: 5px;
  font-size: 12px;
  text-align: right;
}
#br-app .br-elliptic-toggle {
  font-size: 11px;
  color: #6b7280;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 4px;
  margin-top: 4px;
  user-select: none;
}
#br-app .br-elliptic-toggle input { accent-color: #6366f1; cursor: pointer; }

/* ── リンクトグル ─────────────────────────────────────────── */
#br-app .br-link-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 16px;
}
#br-app .br-link-btn {
  padding: 6px 14px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  background: #fff;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background .12s, border-color .12s, color .12s;
  display: flex;
  align-items: center;
  gap: 6px;
}
#br-app .br-link-btn.active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#br-app .br-link-btn svg {
  width: 14px; height: 14px; fill: currentColor;
}

/* ── CSS出力 ──────────────────────────────────────────────── */
#br-app .br-output-box {
  background: #1a1a2e;
  border-radius: 8px;
  padding: 16px;
  margin-top: 8px;
  position: relative;
}
#br-app .br-output-code {
  font-family: 'Fira Mono', 'Cascadia Code', monospace;
  font-size: 13px;
  color: #a5f3fc;
  word-break: break-all;
  white-space: pre-wrap;
  line-height: 1.7;
}
#br-app .br-copy-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 5px 12px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 5px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background .12s;
}
#br-app .br-copy-btn:hover { background: #4f46e5; }
#br-app .br-copy-btn.copied { background: #10b981; }

/* ── freee CTA ────────────────────────────────────────────── */
#br-app .br-cta-box {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
  padding: 24px;
  margin-top: 32px;
  color: #fff;
  text-align: center;
}
#br-app .br-cta-box h4 {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 8px;
}
#br-app .br-cta-box p {
  font-size: 14px;
  opacity: .9;
  margin-bottom: 16px;
}
#br-app .br-cta-btn {
  display: inline-block;
  padding: 10px 28px;
  background: #fff;
  color: #6366f1;
  font-weight: 700;
  font-size: 14px;
  border-radius: 8px;
  text-decoration: none;
  transition: opacity .12s;
}
#br-app .br-cta-btn:hover { opacity: .9; }
</style>

<!-- ── プリセット ── -->
<div class="br-panel" style="margin-top:24px;">
  <h3>プリセット</h3>
  <div class="br-presets">
    <button class="br-preset-btn" data-preset="none">なし</button>
    <button class="br-preset-btn" data-preset="pill">ピル</button>
    <button class="br-preset-btn" data-preset="circle">円</button>
    <button class="br-preset-btn" data-preset="blob">ブロブ</button>
    <button class="br-preset-btn" data-preset="squircle">スクワークル</button>
    <button class="br-preset-btn" data-preset="leaf">リーフ</button>
    <button class="br-preset-btn" data-preset="drop">ドロップ</button>
    <button class="br-preset-btn" data-preset="triangle">三角風</button>
  </div>
</div>

<div class="br-layout">
  <!-- 左: プレビュー -->
  <div>
    <div class="br-panel">
      <h3>プレビュー</h3>
      <div class="br-preview-wrap">
        <div id="br-preview-box"></div>
      </div>
      <div class="br-preview-controls">
        <div>
          <label for="br-pw">幅 (px)</label>
          <input type="number" id="br-pw" value="160" min="40" max="400" step="4">
        </div>
        <div>
          <label for="br-ph">高さ (px)</label>
          <input type="number" id="br-ph" value="160" min="40" max="400" step="4">
        </div>
        <div>
          <label for="br-pbg">カラー</label>
          <input type="color" id="br-pbg" value="#6366f1">
        </div>
      </div>
    </div>
  </div>

  <!-- 右: コントロール -->
  <div>
    <div class="br-panel">
      <h3>コントロール</h3>

      <!-- 単位切り替え -->
      <div class="br-unit-toggle">
        <button class="br-unit-btn active" data-unit="px">px</button>
        <button class="br-unit-btn" data-unit="%">%</button>
      </div>

      <!-- リンクトグル -->
      <div class="br-link-row">
        <button class="br-link-btn active" id="br-link-btn">
          <svg viewBox="0 0 20 20"><path d="M10.293 3.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 9H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414zM3 14a1 1 0 100 2h14a1 1 0 100-2H3z"/></svg>
          コーナーを連動
        </button>
        <span id="br-link-label" style="font-size:12px;color:#6b7280;">全コーナーが同時に変わります</span>
      </div>

      <!-- コーナースライダー -->
      <div class="br-corner-grid" id="br-corner-grid">

        <!-- 左上 -->
        <div class="br-corner-block" id="br-block-tl">
          <label>左上</label>
          <div class="br-slider-row">
            <span>H</span>
            <input type="range" id="br-tl-h" min="0" max="200" value="0">
            <input type="number" id="br-tl-h-n" min="0" max="200" value="0">
          </div>
          <div class="br-slider-row" id="br-tl-v-row" style="display:none;">
            <span>V</span>
            <input type="range" id="br-tl-v" min="0" max="200" value="0">
            <input type="number" id="br-tl-v-n" min="0" max="200" value="0">
          </div>
          <label class="br-elliptic-toggle"><input type="checkbox" id="br-tl-ell"> 楕円</label>
        </div>

        <!-- 右上 -->
        <div class="br-corner-block" id="br-block-tr">
          <label>右上</label>
          <div class="br-slider-row">
            <span>H</span>
            <input type="range" id="br-tr-h" min="0" max="200" value="0">
            <input type="number" id="br-tr-h-n" min="0" max="200" value="0">
          </div>
          <div class="br-slider-row" id="br-tr-v-row" style="display:none;">
            <span>V</span>
            <input type="range" id="br-tr-v" min="0" max="200" value="0">
            <input type="number" id="br-tr-v-n" min="0" max="200" value="0">
          </div>
          <label class="br-elliptic-toggle"><input type="checkbox" id="br-tr-ell"> 楕円</label>
        </div>

        <!-- 右下 -->
        <div class="br-corner-block" id="br-block-br">
          <label>右下</label>
          <div class="br-slider-row">
            <span>H</span>
            <input type="range" id="br-br-h" min="0" max="200" value="0">
            <input type="number" id="br-br-h-n" min="0" max="200" value="0">
          </div>
          <div class="br-slider-row" id="br-br-v-row" style="display:none;">
            <span>V</span>
            <input type="range" id="br-br-v" min="0" max="200" value="0">
            <input type="number" id="br-br-v-n" min="0" max="200" value="0">
          </div>
          <label class="br-elliptic-toggle"><input type="checkbox" id="br-br-ell"> 楕円</label>
        </div>

        <!-- 左下 -->
        <div class="br-corner-block" id="br-block-bl">
          <label>左下</label>
          <div class="br-slider-row">
            <span>H</span>
            <input type="range" id="br-bl-h" min="0" max="200" value="0">
            <input type="number" id="br-bl-h-n" min="0" max="200" value="0">
          </div>
          <div class="br-slider-row" id="br-bl-v-row" style="display:none;">
            <span>V</span>
            <input type="range" id="br-bl-v" min="0" max="200" value="0">
            <input type="number" id="br-bl-v-n" min="0" max="200" value="0">
          </div>
          <label class="br-elliptic-toggle"><input type="checkbox" id="br-bl-ell"> 楕円</label>
        </div>

      </div><!-- /.br-corner-grid -->
    </div><!-- /.br-panel -->
  </div>
</div><!-- /.br-layout -->

<!-- CSS出力 -->
<div class="br-panel" style="margin-top:0;">
  <h3>生成されたCSS</h3>
  <div class="br-output-box">
    <button class="br-copy-btn" id="br-copy-btn">コピー</button>
    <pre class="br-output-code" id="br-output-code">border-radius: 0;</pre>
  </div>
</div>

<script>
(function () {
  'use strict';

  /* ── 状態 ── */
  var unit = 'px';
  var linked = true;

  var corners = {
    tl: { h: 0, v: 0, elliptic: false },
    tr: { h: 0, v: 0, elliptic: false },
    br: { h: 0, v: 0, elliptic: false },
    bl: { h: 0, v: 0, elliptic: false }
  };

  /* ── プリセット ── */
  var PRESETS = {
    none:     { tl:{h:0,v:0,e:false}, tr:{h:0,v:0,e:false}, br:{h:0,v:0,e:false}, bl:{h:0,v:0,e:false}, unit:'px' },
    pill:     { tl:{h:999,v:999,e:false}, tr:{h:999,v:999,e:false}, br:{h:999,v:999,e:false}, bl:{h:999,v:999,e:false}, unit:'px' },
    circle:   { tl:{h:50,v:50,e:false}, tr:{h:50,v:50,e:false}, br:{h:50,v:50,e:false}, bl:{h:50,v:50,e:false}, unit:'%' },
    blob:     { tl:{h:60,v:40,e:true}, tr:{h:40,v:70,e:true}, br:{h:70,v:50,e:true}, bl:{h:50,v:60,e:true}, unit:'%' },
    squircle: { tl:{h:30,v:30,e:false}, tr:{h:30,v:30,e:false}, br:{h:30,v:30,e:false}, bl:{h:30,v:30,e:false}, unit:'%' },
    leaf:     { tl:{h:0,v:0,e:false}, tr:{h:50,v:50,e:false}, br:{h:0,v:0,e:false}, bl:{h:50,v:50,e:false}, unit:'%' },
    drop:     { tl:{h:50,v:50,e:false}, tr:{h:50,v:50,e:false}, br:{h:50,v:50,e:false}, bl:{h:0,v:0,e:false}, unit:'%' },
    triangle: { tl:{h:0,v:0,e:false}, tr:{h:100,v:0,e:true}, br:{h:100,v:100,e:true}, bl:{h:0,v:100,e:true}, unit:'%' }
  };

  /* ── DOM参照 ── */
  var preview   = document.getElementById('br-preview-box');
  var outputEl  = document.getElementById('br-output-code');
  var copyBtn   = document.getElementById('br-copy-btn');
  var linkBtn   = document.getElementById('br-link-btn');
  var linkLabel = document.getElementById('br-link-label');
  var pwInput   = document.getElementById('br-pw');
  var phInput   = document.getElementById('br-ph');
  var pbgInput  = document.getElementById('br-pbg');

  var cornerKeys = ['tl','tr','br','bl'];

  function el(id) { return document.getElementById(id); }

  /* ── CSS生成 ── */
  function buildCSS() {
    var anyElliptic = cornerKeys.some(function(k){ return corners[k].elliptic; });
    var css;
    if (anyElliptic) {
      var hParts = cornerKeys.map(function(k){
        return Math.min(corners[k].h, unit === '%' ? 50 : 200) + unit;
      });
      var vParts = cornerKeys.map(function(k){
        return Math.min(corners[k].v, unit === '%' ? 50 : 200) + unit;
      });
      css = 'border-radius: ' + hParts.join(' ') + ' / ' + vParts.join(' ') + ';';
    } else {
      var tl  = Math.min(corners.tl.h, unit === '%' ? 50 : 200) + unit;
      var tr  = Math.min(corners.tr.h, unit === '%' ? 50 : 200) + unit;
      var brv = Math.min(corners.br.h, unit === '%' ? 50 : 200) + unit;
      var bl  = Math.min(corners.bl.h, unit === '%' ? 50 : 200) + unit;
      if (tl === tr && tr === brv && brv === bl) {
        css = 'border-radius: ' + tl + ';';
      } else if (tl === brv && tr === bl) {
        css = 'border-radius: ' + tl + ' ' + tr + ';';
      } else if (tr === bl) {
        css = 'border-radius: ' + tl + ' ' + tr + ' ' + brv + ';';
      } else {
        css = 'border-radius: ' + tl + ' ' + tr + ' ' + brv + ' ' + bl + ';';
      }
    }
    return css;
  }

  function applyPreview() {
    var hParts = cornerKeys.map(function(k){
      return Math.min(corners[k].h, unit === '%' ? 50 : 200) + unit;
    });
    var vParts = cornerKeys.map(function(k){
      return Math.min(corners[k].v, unit === '%' ? 50 : 200) + unit;
    });
    preview.style.borderRadius = hParts.join(' ') + ' / ' + vParts.join(' ');
    outputEl.textContent = buildCSS();
  }

  function syncInputs() {
    cornerKeys.forEach(function(k) {
      var maxVal = unit === '%' ? 50 : 200;
      el('br-' + k + '-h').max = maxVal;
      el('br-' + k + '-h-n').max = maxVal;
      el('br-' + k + '-v').max = maxVal;
      el('br-' + k + '-v-n').max = maxVal;
      el('br-' + k + '-h').value = Math.min(corners[k].h, maxVal);
      el('br-' + k + '-h-n').value = Math.min(corners[k].h, maxVal);
      el('br-' + k + '-v').value = Math.min(corners[k].v, maxVal);
      el('br-' + k + '-v-n').value = Math.min(corners[k].v, maxVal);
      el('br-' + k + '-ell').checked = corners[k].elliptic;
      el('br-' + k + '-v-row').style.display = corners[k].elliptic ? 'flex' : 'none';
    });
  }

  /* ── スライダー↔数値 連動 ── */
  function wireCorner(k, axis) {
    var sliderEl = el('br-' + k + '-' + axis);
    var numEl    = el('br-' + k + '-' + axis + '-n');

    function onChange(val) {
      val = Math.max(0, Math.min(parseInt(val) || 0, unit === '%' ? 50 : 200));
      corners[k][axis] = val;

      if (linked && axis === 'h') {
        cornerKeys.forEach(function(ck) {
          corners[ck].h = val;
          if (!corners[ck].elliptic) corners[ck].v = val;
        });
        syncInputs();
      } else {
        sliderEl.value = val;
        numEl.value = val;
      }
      applyPreview();
    }

    sliderEl.addEventListener('input', function() { onChange(this.value); });
    numEl.addEventListener('input', function() { onChange(this.value); });
  }

  cornerKeys.forEach(function(k) {
    wireCorner(k, 'h');
    wireCorner(k, 'v');
    el('br-' + k + '-ell').addEventListener('change', function() {
      corners[k].elliptic = this.checked;
      el('br-' + k + '-v-row').style.display = this.checked ? 'flex' : 'none';
      applyPreview();
    });
  });

  /* ── コーナー連動ボタン ── */
  linkBtn.addEventListener('click', function() {
    linked = !linked;
    linkBtn.classList.toggle('active', linked);
    linkLabel.textContent = linked ? '全コーナーが同時に変わります' : 'コーナーは個別に設定できます';
  });

  /* ── 単位切り替え ── */
  document.querySelectorAll('#br-app .br-unit-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      document.querySelectorAll('#br-app .br-unit-btn').forEach(function(b){ b.classList.remove('active'); });
      this.classList.add('active');
      unit = this.dataset.unit;
      var maxVal = unit === '%' ? 50 : 200;
      cornerKeys.forEach(function(k) {
        corners[k].h = Math.min(corners[k].h, maxVal);
        corners[k].v = Math.min(corners[k].v, maxVal);
      });
      syncInputs();
      applyPreview();
    });
  });

  /* ── プリセット ── */
  document.querySelectorAll('#br-app .br-preset-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      document.querySelectorAll('#br-app .br-preset-btn').forEach(function(b){ b.classList.remove('active'); });
      this.classList.add('active');

      var p = PRESETS[this.dataset.preset];
      if (!p) return;

      unit = p.unit;
      document.querySelectorAll('#br-app .br-unit-btn').forEach(function(b){
        b.classList.toggle('active', b.dataset.unit === unit);
      });

      var maxVal = unit === '%' ? 50 : 200;
      cornerKeys.forEach(function(k) {
        corners[k].h = Math.min(p[k].h, maxVal);
        corners[k].v = Math.min(p[k].v, maxVal);
        corners[k].elliptic = p[k].e;
      });

      if (this.dataset.preset === 'pill') {
        cornerKeys.forEach(function(k) { corners[k].h = 200; });
      }

      linked = false;
      linkBtn.classList.remove('active');
      linkLabel.textContent = 'コーナーは個別に設定できます';

      syncInputs();
      applyPreview();
    });
  });

  /* ── プレビューサイズ/カラー ── */
  pwInput.addEventListener('input', function() {
    preview.style.width = Math.max(40, parseInt(this.value) || 160) + 'px';
  });
  phInput.addEventListener('input', function() {
    preview.style.height = Math.max(40, parseInt(this.value) || 160) + 'px';
  });
  pbgInput.addEventListener('input', function() {
    preview.style.background = this.value;
  });

  /* ── コピーボタン ── */
  copyBtn.addEventListener('click', function() {
    var text = outputEl.textContent;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(function() { flash(); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      flash();
    }
    function flash() {
      copyBtn.textContent = 'コピー完了!';
      copyBtn.classList.add('copied');
      setTimeout(function() {
        copyBtn.textContent = 'コピー';
        copyBtn.classList.remove('copied');
      }, 1800);
    }
  });

  /* ── 初期化 ── */
  syncInputs();
  applyPreview();

})();
</script>

<!-- freee CTA -->
<div class="br-cta-box">
  <h4>経理・会計をもっとスマートに</h4>
  <p>freee会計なら、請求書・確定申告・経費精算をまとめて自動化。エンジニアやフリーランスにも選ばれています。</p>
  <a class="br-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>

</div>

---

### 使い方

1. **プリセット**を選んでシェイプのベースを決める。または、スライダーをゼロから調整する。
2. **px / %** を切り替え — パーセントは要素サイズに対する相対値、ピクセルは絶対値。
3. **コーナー連動をオフ**にすると、各コーナーを独立して設定可能。
4. **楕円**チェックを入れると水平・垂直の半径を個別指定でき、有機的なフォルムに。
5. **プレビューサイズ**を変えてアスペクト比が変わったときの見た目を確認。
6. **CSSをコピー**してスタイルシートに直接貼り付け。

### 早見表: border-radius の書き方

| 値 | 意味 |
|---|---|
| `border-radius: 8px` | 全角が同一 |
| `border-radius: 8px 16px` | TL+BR / TR+BL |
| `border-radius: 8px 16px 24px 32px` | TL TR BR BL（時計回り）|
| `border-radius: 40% 60% / 60% 40%` | 楕円（水平 / 垂直）|

---

### 関連ツール
> ボックスシャドウを生成 → [CSS Box Shadow ジェネレーター](/ja/tools/box-shadow-generator/)
> グラデーションを作成 → [CSS グラデーションジェネレーター](/ja/tools/css-gradient-generator/)
> Flexboxレイアウトを構築 → [CSS Flexbox ジェネレーター](/ja/tools/flexbox-generator/)
