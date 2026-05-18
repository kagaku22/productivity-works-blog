---
title: "CSSアニメーションジェネレーター — キーフレームビルダー"
date: 2026-01-18
description: "ビジュアルキーフレームエディターでCSSアニメーションを作成。フェード・スライド・バウンス・パルス等のプリセット。ライブプレビューと@keyframesコード即時コピー。"
categories: ["無料ツール"]
slug: "css-animation-generator"
ShowToc: false
aliases:
  - "/ja/tools/css-animation-generator/"
  - "/ja/tools/css-animation-generator/"
cover:
  image: "/images/covers/css-animation-generator-ja.png"
  alt: "CSSアニメーションジェネレーター"
---

<div id="anim-app">

<style>
/* ── スコープ済みスタイル — すべてのセレクターに #anim-app プレフィックス ── */
#anim-app *,
#anim-app *::before,
#anim-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#anim-app {
  font-family: "Hiragino Sans", "Noto Sans JP", "Yu Gothic UI", -apple-system, BlinkMacSystemFont, sans-serif;
  font-size: 14px;
  color: #1a1a2e;
  background: #f4f6fb;
  border-radius: 12px;
  padding: 24px;
  max-width: 960px;
  margin: 0 auto;
}

/* ── レイアウトグリッド ── */
#anim-app .anim-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
@media (max-width: 680px) {
  #anim-app .anim-grid { grid-template-columns: 1fr; }
}

/* ── カード ── */
#anim-app .anim-card {
  background: #ffffff;
  border: 1px solid #e0e4f0;
  border-radius: 10px;
  padding: 18px;
}
#anim-app .anim-card h3 {
  font-size: 13px;
  font-weight: 700;
  letter-spacing: .04em;
  text-transform: none;
  color: #5b6af0;
  margin-bottom: 14px;
}

/* ── フォームコントロール ── */
#anim-app label {
  display: flex;
  flex-direction: column;
  gap: 4px;
  font-size: 12px;
  font-weight: 600;
  color: #444;
  margin-bottom: 10px;
}
#anim-app input[type="text"],
#anim-app input[type="number"],
#anim-app input[type="color"],
#anim-app select {
  font-size: 13px;
  padding: 7px 10px;
  border: 1px solid #d0d5e8;
  border-radius: 6px;
  background: #f9faff;
  color: #1a1a2e;
  width: 100%;
  outline: none;
  transition: border-color .2s;
}
#anim-app input[type="color"] {
  padding: 2px 4px;
  height: 34px;
  cursor: pointer;
}
#anim-app input:focus,
#anim-app select:focus { border-color: #5b6af0; }

#anim-app input[type="range"] {
  width: 100%;
  accent-color: #5b6af0;
  cursor: pointer;
}
#anim-app .range-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#anim-app .range-row span {
  font-size: 12px;
  font-weight: 700;
  color: #5b6af0;
  min-width: 38px;
  text-align: right;
}

/* ── プリセットボタン ── */
#anim-app .preset-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
  margin-bottom: 4px;
}
#anim-app .preset-btn {
  font-size: 12px;
  font-weight: 600;
  padding: 5px 12px;
  border: 1.5px solid #d0d5e8;
  border-radius: 20px;
  background: #f4f6fb;
  color: #444;
  cursor: pointer;
  transition: background .15s, border-color .15s, color .15s;
}
#anim-app .preset-btn:hover,
#anim-app .preset-btn.active {
  background: #5b6af0;
  border-color: #5b6af0;
  color: #fff;
}

/* ── キーフレームエディター ── */
#anim-app .kf-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#anim-app .kf-item {
  border: 1px solid #e0e4f0;
  border-radius: 8px;
  padding: 10px 12px;
  background: #f9faff;
}
#anim-app .kf-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}
#anim-app .kf-pct {
  font-size: 13px;
  font-weight: 700;
  color: #5b6af0;
}
#anim-app .kf-props {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6px 10px;
}
#anim-app .kf-props label {
  margin-bottom: 0;
  font-size: 11px;
}
#anim-app .kf-del {
  background: none;
  border: none;
  color: #c0392b;
  font-size: 16px;
  cursor: pointer;
  line-height: 1;
  padding: 0 2px;
}
#anim-app .kf-del:hover { color: #e74c3c; }
#anim-app .add-kf-row {
  display: flex;
  gap: 8px;
  align-items: center;
  margin-top: 10px;
}
#anim-app .add-kf-row input { width: 80px; flex-shrink: 0; }
#anim-app .btn-add {
  padding: 7px 14px;
  font-size: 12px;
  font-weight: 700;
  border-radius: 6px;
  border: none;
  background: #5b6af0;
  color: #fff;
  cursor: pointer;
  transition: background .2s;
}
#anim-app .btn-add:hover { background: #4454d8; }

/* ── プレビューエリア ── */
#anim-app .preview-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}
#anim-app .preview-stage {
  width: 100%;
  height: 180px;
  background: linear-gradient(135deg, #e8ecff 0%, #f4f6fb 100%);
  border-radius: 10px;
  border: 1px solid #d0d5e8;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  position: relative;
}
#anim-app #preview-box {
  width: 72px;
  height: 72px;
  background: #5b6af0;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: .02em;
  user-select: none;
  will-change: transform, opacity;
}
#anim-app .preview-controls {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
}
#anim-app .ctrl-btn {
  padding: 8px 20px;
  font-size: 13px;
  font-weight: 700;
  border-radius: 8px;
  border: none;
  cursor: pointer;
  transition: opacity .2s;
}
#anim-app .ctrl-btn:hover { opacity: .85; }
#anim-app .btn-play  { background: #27ae60; color: #fff; }
#anim-app .btn-pause { background: #e67e22; color: #fff; }
#anim-app .btn-reset { background: #636e72; color: #fff; }

/* ── スピードスライダー ── */
#anim-app .speed-row {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 12px;
  font-weight: 600;
  color: #444;
}
#anim-app .speed-row input { flex: 1; }
#anim-app .speed-row span { min-width: 34px; color: #5b6af0; font-weight: 700; }

/* ── 出力CSS ── */
#anim-app .output-wrap {
  grid-column: 1 / -1;
}
#anim-app .output-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}
#anim-app .output-header h3 { margin-bottom: 0; }
#anim-app .btn-copy {
  padding: 6px 16px;
  font-size: 12px;
  font-weight: 700;
  border-radius: 6px;
  border: none;
  background: #5b6af0;
  color: #fff;
  cursor: pointer;
  transition: background .2s;
}
#anim-app .btn-copy:hover  { background: #4454d8; }
#anim-app .btn-copy.copied { background: #27ae60; }
#anim-app #css-output {
  width: 100%;
  min-height: 160px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 12px;
  line-height: 1.6;
  padding: 14px;
  border: 1px solid #d0d5e8;
  border-radius: 8px;
  background: #1a1a2e;
  color: #a0d8ef;
  resize: vertical;
  outline: none;
}

/* ── フル幅行 ── */
#anim-app .full-row { grid-column: 1 / -1; }

/* ── freee CTA ── */
#anim-app .freee-cta {
  grid-column: 1 / -1;
  margin-top: 8px;
  background: linear-gradient(135deg, #00b0be 0%, #0076be 100%);
  border-radius: 10px;
  padding: 20px 24px;
  color: #fff;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#anim-app .freee-cta h4 {
  font-size: 15px;
  font-weight: 700;
  margin: 0;
}
#anim-app .freee-cta p {
  font-size: 13px;
  line-height: 1.6;
  margin: 0;
  opacity: .92;
}
#anim-app .freee-cta a.freee-btn {
  display: inline-block;
  background: #fff;
  color: #0076be;
  font-weight: 700;
  font-size: 13px;
  padding: 9px 22px;
  border-radius: 8px;
  text-decoration: none;
  align-self: flex-start;
  transition: opacity .2s;
}
#anim-app .freee-cta a.freee-btn:hover { opacity: .85; }
</style>

<!-- ══════════════════════════════
     プリセット
══════════════════════════════ -->
<div class="anim-card full-row" style="margin-bottom:0">
  <h3>プリセット</h3>
  <div class="preset-grid" id="preset-grid">
    <button class="preset-btn" data-preset="fadeIn">フェードイン</button>
    <button class="preset-btn" data-preset="fadeOut">フェードアウト</button>
    <button class="preset-btn" data-preset="slideInLeft">左からスライド</button>
    <button class="preset-btn" data-preset="slideInRight">右からスライド</button>
    <button class="preset-btn" data-preset="slideInUp">下からスライド</button>
    <button class="preset-btn" data-preset="slideInDown">上からスライド</button>
    <button class="preset-btn" data-preset="bounce">バウンス</button>
    <button class="preset-btn" data-preset="pulse">パルス</button>
    <button class="preset-btn" data-preset="shake">シェイク</button>
    <button class="preset-btn" data-preset="spin">スピン</button>
    <button class="preset-btn" data-preset="flip">フリップ</button>
    <button class="preset-btn" data-preset="swing">スウィング</button>
  </div>
</div>

<div class="anim-grid" style="margin-top:20px">

<!-- ══════════════════════════════
     アニメーションプロパティ
══════════════════════════════ -->
<div class="anim-card">
  <h3>アニメーションプロパティ</h3>

  <label>時間（秒）
    <div class="range-row">
      <input type="range" id="prop-duration" min="0.1" max="10" step="0.1" value="1">
      <span id="lbl-duration">1s</span>
    </div>
  </label>

  <label>遅延（秒）
    <div class="range-row">
      <input type="range" id="prop-delay" min="0" max="5" step="0.1" value="0">
      <span id="lbl-delay">0s</span>
    </div>
  </label>

  <label>タイミング関数
    <select id="prop-timing">
      <option value="ease">ease</option>
      <option value="ease-in">ease-in（加速）</option>
      <option value="ease-out">ease-out（減速）</option>
      <option value="ease-in-out">ease-in-out</option>
      <option value="linear">linear（一定）</option>
      <option value="cubic-bezier(0.68,-0.55,0.27,1.55)">cubic-bezier（バック）</option>
      <option value="steps(4,end)">steps(4, end)（ステップ）</option>
    </select>
  </label>

  <label>繰り返し回数
    <select id="prop-iteration">
      <option value="1">1回</option>
      <option value="2">2回</option>
      <option value="3">3回</option>
      <option value="5">5回</option>
      <option value="infinite" selected>無限</option>
    </select>
  </label>

  <label>再生方向
    <select id="prop-direction">
      <option value="normal">normal（通常）</option>
      <option value="reverse">reverse（逆方向）</option>
      <option value="alternate">alternate（交互）</option>
      <option value="alternate-reverse">alternate-reverse</option>
    </select>
  </label>

  <label>フィルモード
    <select id="prop-fillmode">
      <option value="none">none</option>
      <option value="forwards">forwards</option>
      <option value="backwards">backwards</option>
      <option value="both">both</option>
    </select>
  </label>
</div>

<!-- ══════════════════════════════
     ライブプレビュー
══════════════════════════════ -->
<div class="anim-card">
  <h3>ライブプレビュー</h3>
  <div class="preview-area">
    <div class="preview-stage">
      <div id="preview-box">CSS</div>
    </div>

    <div class="speed-row">
      <span>速度</span>
      <input type="range" id="speed-ctrl" min="0.25" max="4" step="0.25" value="1">
      <span id="lbl-speed">1×</span>
    </div>

    <div class="preview-controls">
      <button class="ctrl-btn btn-play"  id="btn-play">&#9654; 再生</button>
      <button class="ctrl-btn btn-pause" id="btn-pause">&#10074;&#10074; 一時停止</button>
      <button class="ctrl-btn btn-reset" id="btn-reset">&#8635; リセット</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════
     キーフレームエディター
══════════════════════════════ -->
<div class="anim-card full-row">
  <h3>キーフレームエディター</h3>
  <div class="kf-list" id="kf-list"></div>
  <div class="add-kf-row">
    <input type="number" id="new-kf-pct" min="0" max="100" step="1" value="50" placeholder="%">
    <button class="btn-add" id="btn-add-kf">＋ キーフレーム追加</button>
  </div>
</div>

<!-- ══════════════════════════════
     生成CSS出力
══════════════════════════════ -->
<div class="anim-card output-wrap">
  <div class="output-header">
    <h3>生成されたCSS</h3>
    <button class="btn-copy" id="btn-copy">コピー</button>
  </div>
  <textarea id="css-output" readonly></textarea>
</div>

<!-- ══════════════════════════════
     freee CTA
══════════════════════════════ -->
<div class="freee-cta">
  <h4>freee で会計・給与計算をもっとスマートに</h4>
  <p>CSSアニメーションでWebサイトをリッチにしたら、バックオフィスも効率化しませんか？<br>
     freee 会計・freee 人事労務は、スモールビジネスの経理・給与計算を自動化します。<br>
     まずは30日間の無料トライアルでお試しください。</p>
  <a class="freee-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">
    freee を無料で試す &rarr;
  </a>
</div>

</div><!-- /.anim-grid -->
</div><!-- /#anim-app -->

<script>
(function () {
  'use strict';

  /* ── State ─────────────────────────────────────────────── */
  var state = {
    animName: 'myAnimation',
    duration: 1,
    delay: 0,
    timing: 'ease',
    iteration: 'infinite',
    direction: 'normal',
    fillMode: 'none',
    speed: 1,
    keyframes: [],
    playing: false,
    styleEl: null
  };

  /* ── Presets ────────────────────────────────────────────── */
  var PRESETS = {
    fadeIn: {
      name: 'fadeIn', timing: 'ease', direction: 'normal', fillMode: 'both',
      keyframes: [
        { pct: 0,   opacity: 0, translateX: 0, translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0, rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    fadeOut: {
      name: 'fadeOut', timing: 'ease', direction: 'normal', fillMode: 'forwards',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0, translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 0, translateX: 0, translateY: 0, rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    slideInLeft: {
      name: 'slideInLeft', timing: 'ease-out', direction: 'normal', fillMode: 'both',
      keyframes: [
        { pct: 0,   opacity: 0, translateX: -100, translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0,    translateY: 0, rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    slideInRight: {
      name: 'slideInRight', timing: 'ease-out', direction: 'normal', fillMode: 'both',
      keyframes: [
        { pct: 0,   opacity: 0, translateX: 100, translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0,   translateY: 0, rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    slideInUp: {
      name: 'slideInUp', timing: 'ease-out', direction: 'normal', fillMode: 'both',
      keyframes: [
        { pct: 0,   opacity: 0, translateX: 0, translateY: 60, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0,  rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    slideInDown: {
      name: 'slideInDown', timing: 'ease-out', direction: 'normal', fillMode: 'both',
      keyframes: [
        { pct: 0,   opacity: 0, translateX: 0, translateY: -60, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0,   rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    bounce: {
      name: 'bounce', timing: 'ease', direction: 'normal', fillMode: 'none',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0, translateY: 0,   rotate: 0, scale: 1,    bgColor: '' },
        { pct: 25,  opacity: 1, translateX: 0, translateY: -30, rotate: 0, scale: 1,    bgColor: '' },
        { pct: 50,  opacity: 1, translateX: 0, translateY: 0,   rotate: 0, scale: 1,    bgColor: '' },
        { pct: 75,  opacity: 1, translateX: 0, translateY: -15, rotate: 0, scale: 1,    bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0,   rotate: 0, scale: 1,    bgColor: '' }
      ]
    },
    pulse: {
      name: 'pulse', timing: 'ease-in-out', direction: 'alternate', fillMode: 'none',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0, translateY: 0, rotate: 0, scale: 1,    bgColor: '' },
        { pct: 50,  opacity: 1, translateX: 0, translateY: 0, rotate: 0, scale: 1.15, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0, rotate: 0, scale: 1,    bgColor: '' }
      ]
    },
    shake: {
      name: 'shake', timing: 'ease-in-out', direction: 'normal', fillMode: 'none',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0,   translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 15,  opacity: 1, translateX: -10, translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 30,  opacity: 1, translateX: 10,  translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 45,  opacity: 1, translateX: -10, translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 60,  opacity: 1, translateX: 10,  translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 75,  opacity: 1, translateX: -5,  translateY: 0, rotate: 0, scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0,   translateY: 0, rotate: 0, scale: 1, bgColor: '' }
      ]
    },
    spin: {
      name: 'spin', timing: 'linear', direction: 'normal', fillMode: 'none',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0, translateY: 0, rotate: 0,   scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0, rotate: 360, scale: 1, bgColor: '' }
      ]
    },
    flip: {
      name: 'flip', timing: 'ease-in-out', direction: 'normal', fillMode: 'both',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0, translateY: 0, rotate: 0,   scale: 1,    bgColor: '' },
        { pct: 40,  opacity: 1, translateX: 0, translateY: 0, rotate: -20, scale: 1.1,  bgColor: '' },
        { pct: 60,  opacity: 1, translateX: 0, translateY: 0, rotate: 10,  scale: 0.9,  bgColor: '' },
        { pct: 80,  opacity: 1, translateX: 0, translateY: 0, rotate: -5,  scale: 1.05, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0, rotate: 0,   scale: 1,    bgColor: '' }
      ]
    },
    swing: {
      name: 'swing', timing: 'ease-in-out', direction: 'alternate', fillMode: 'none',
      keyframes: [
        { pct: 0,   opacity: 1, translateX: 0, translateY: 0, rotate: -20, scale: 1, bgColor: '' },
        { pct: 50,  opacity: 1, translateX: 0, translateY: 0, rotate: 0,   scale: 1, bgColor: '' },
        { pct: 100, opacity: 1, translateX: 0, translateY: 0, rotate: 20,  scale: 1, bgColor: '' }
      ]
    }
  };

  /* ── DOM refs ───────────────────────────────────────────── */
  var previewBox    = document.getElementById('preview-box');
  var kfList        = document.getElementById('kf-list');
  var cssOutput     = document.getElementById('css-output');
  var btnCopy       = document.getElementById('btn-copy');
  var btnPlay       = document.getElementById('btn-play');
  var btnPause      = document.getElementById('btn-pause');
  var btnReset      = document.getElementById('btn-reset');
  var newKfPct      = document.getElementById('new-kf-pct');
  var btnAddKf      = document.getElementById('btn-add-kf');
  var speedCtrl     = document.getElementById('speed-ctrl');
  var lblSpeed      = document.getElementById('lbl-speed');
  var propDuration  = document.getElementById('prop-duration');
  var lblDuration   = document.getElementById('lbl-duration');
  var propDelay     = document.getElementById('prop-delay');
  var lblDelay      = document.getElementById('lbl-delay');
  var propTiming    = document.getElementById('prop-timing');
  var propIteration = document.getElementById('prop-iteration');
  var propDirection = document.getElementById('prop-direction');
  var propFillMode  = document.getElementById('prop-fillmode');

  /* ── Helpers ────────────────────────────────────────────── */
  function buildTransform(kf) {
    var parts = [];
    if (kf.translateX !== 0 || kf.translateY !== 0)
      parts.push('translate(' + kf.translateX + 'px, ' + kf.translateY + 'px)');
    if (kf.rotate !== 0)
      parts.push('rotate(' + kf.rotate + 'deg)');
    if (kf.scale !== 1)
      parts.push('scale(' + kf.scale + ')');
    return parts.length ? parts.join(' ') : 'none';
  }

  function sortKeyframes() {
    state.keyframes.sort(function (a, b) { return a.pct - b.pct; });
  }

  function defaultKf(pct) {
    return { pct: pct, opacity: 1, translateX: 0, translateY: 0, rotate: 0, scale: 1, bgColor: '' };
  }

  /* ── CSS generation ─────────────────────────────────────── */
  function generateCSS() {
    sortKeyframes();
    var name = state.animName;
    var lines = ['@keyframes ' + name + ' {'];
    state.keyframes.forEach(function (kf) {
      lines.push('  ' + kf.pct + '% {');
      lines.push('    opacity: ' + kf.opacity + ';');
      var tf = buildTransform(kf);
      if (tf !== 'none') lines.push('    transform: ' + tf + ';');
      if (kf.bgColor) lines.push('    background-color: ' + kf.bgColor + ';');
      lines.push('  }');
    });
    lines.push('}');
    lines.push('');
    lines.push('.animated-element {');
    lines.push('  animation-name: ' + name + ';');
    lines.push('  animation-duration: ' + state.duration + 's;');
    lines.push('  animation-timing-function: ' + state.timing + ';');
    lines.push('  animation-delay: ' + state.delay + 's;');
    lines.push('  animation-iteration-count: ' + state.iteration + ';');
    lines.push('  animation-direction: ' + state.direction + ';');
    lines.push('  animation-fill-mode: ' + state.fillMode + ';');
    lines.push('  /* ショートハンド: */');
    lines.push('  animation: ' + name + ' ' + state.duration + 's ' + state.timing +
               ' ' + state.delay + 's ' + state.iteration + ' ' + state.direction +
               ' ' + state.fillMode + ';');
    lines.push('}');
    return lines.join('\n');
  }

  /* ── Inject animation into page ─────────────────────────── */
  function injectAnimation() {
    if (!state.styleEl) {
      state.styleEl = document.createElement('style');
      document.head.appendChild(state.styleEl);
    }
    sortKeyframes();
    var name = state.animName;
    var kfCSS = '@keyframes ' + name + ' {\n';
    state.keyframes.forEach(function (kf) {
      kfCSS += '  ' + kf.pct + '% {\n';
      kfCSS += '    opacity: ' + kf.opacity + ';\n';
      var tf = buildTransform(kf);
      if (tf !== 'none') kfCSS += '    transform: ' + tf + ';\n';
      if (kf.bgColor) kfCSS += '    background-color: ' + kf.bgColor + ';\n';
      kfCSS += '  }\n';
    });
    kfCSS += '}';
    state.styleEl.textContent = kfCSS;
  }

  function applyAnimation() {
    injectAnimation();
    var el = previewBox;
    var realDuration = state.duration / state.speed;
    el.style.animation = 'none';
    void el.offsetWidth;
    el.style.animation =
      state.animName + ' ' + realDuration + 's ' + state.timing + ' ' +
      state.delay + 's ' + state.iteration + ' ' + state.direction + ' ' + state.fillMode;
    el.style.animationPlayState = 'running';
    state.playing = true;
  }

  function pauseAnimation() {
    previewBox.style.animationPlayState = 'paused';
    state.playing = false;
  }

  function resetAnimation() {
    previewBox.style.animation = 'none';
    state.playing = false;
  }

  /* ── Render keyframe editor ─────────────────────────────── */
  function renderKeyframes() {
    sortKeyframes();
    kfList.innerHTML = '';
    state.keyframes.forEach(function (kf, idx) {
      var div = document.createElement('div');
      div.className = 'kf-item';
      div.innerHTML =
        '<div class="kf-header">' +
          '<span class="kf-pct">' + kf.pct + '%</span>' +
          (state.keyframes.length > 2 ?
            '<button class="kf-del" data-idx="' + idx + '" title="キーフレームを削除">&times;</button>' : '') +
        '</div>' +
        '<div class="kf-props">' +
          '<label>X移動（px）<input type="number" data-idx="' + idx + '" data-prop="translateX" value="' + kf.translateX + '" step="1"></label>' +
          '<label>Y移動（px）<input type="number" data-idx="' + idx + '" data-prop="translateY" value="' + kf.translateY + '" step="1"></label>' +
          '<label>回転（deg）<input type="number" data-idx="' + idx + '" data-prop="rotate" value="' + kf.rotate + '" step="1"></label>' +
          '<label>スケール<input type="number" data-idx="' + idx + '" data-prop="scale" value="' + kf.scale + '" step="0.05" min="0"></label>' +
          '<label>透明度（0–1）<input type="number" data-idx="' + idx + '" data-prop="opacity" value="' + kf.opacity + '" step="0.05" min="0" max="1"></label>' +
          '<label>背景色<input type="color" data-idx="' + idx + '" data-prop="bgColor" value="' + (kf.bgColor || '#5b6af0') + '"></label>' +
        '</div>';
      kfList.appendChild(div);
    });

    kfList.querySelectorAll('.kf-del').forEach(function (btn) {
      btn.addEventListener('click', function () {
        state.keyframes.splice(parseInt(btn.dataset.idx), 1);
        renderKeyframes();
        refresh();
      });
    });

    kfList.querySelectorAll('input[data-prop]').forEach(function (inp) {
      inp.addEventListener('input', function () {
        var i    = parseInt(inp.dataset.idx);
        var prop = inp.dataset.prop;
        var val  = inp.type === 'color' ? inp.value : parseFloat(inp.value);
        if (inp.type !== 'color' && isNaN(val)) return;
        state.keyframes[i][prop] = val;
        refresh();
      });
    });
  }

  /* ── Refresh ────────────────────────────────────────────── */
  function refresh() {
    cssOutput.value = generateCSS();
    if (state.playing) applyAnimation();
    else injectAnimation();
  }

  /* ── Load preset ────────────────────────────────────────── */
  function loadPreset(name) {
    var p = PRESETS[name];
    if (!p) return;
    state.animName  = p.name;
    state.keyframes = p.keyframes.map(function (kf) { return Object.assign({}, kf); });
    state.timing    = p.timing;
    state.direction = p.direction;
    state.fillMode  = p.fillMode;

    propTiming.value    = p.timing;
    propDirection.value = p.direction;
    propFillMode.value  = p.fillMode;

    document.querySelectorAll('#anim-app .preset-btn').forEach(function (b) {
      b.classList.toggle('active', b.dataset.preset === name);
    });

    renderKeyframes();
    applyAnimation();
    refresh();
  }

  /* ── Event wiring ───────────────────────────────────────── */
  propDuration.addEventListener('input', function () {
    state.duration = parseFloat(propDuration.value);
    lblDuration.textContent = state.duration + 's';
    refresh();
  });
  propDelay.addEventListener('input', function () {
    state.delay = parseFloat(propDelay.value);
    lblDelay.textContent = state.delay + 's';
    refresh();
  });
  propTiming.addEventListener('change', function () { state.timing = propTiming.value; refresh(); });
  propIteration.addEventListener('change', function () { state.iteration = propIteration.value; refresh(); });
  propDirection.addEventListener('change', function () { state.direction = propDirection.value; refresh(); });
  propFillMode.addEventListener('change', function () { state.fillMode = propFillMode.value; refresh(); });

  speedCtrl.addEventListener('input', function () {
    state.speed = parseFloat(speedCtrl.value);
    lblSpeed.textContent = state.speed + '×';
    if (state.playing) applyAnimation();
  });

  btnPlay.addEventListener('click', applyAnimation);
  btnPause.addEventListener('click', pauseAnimation);
  btnReset.addEventListener('click', resetAnimation);

  btnAddKf.addEventListener('click', function () {
    var pct = parseInt(newKfPct.value);
    if (isNaN(pct) || pct < 0 || pct > 100) return;
    if (state.keyframes.some(function (k) { return k.pct === pct; })) return;
    state.keyframes.push(defaultKf(pct));
    renderKeyframes();
    refresh();
  });

  document.querySelectorAll('#anim-app .preset-btn').forEach(function (btn) {
    btn.addEventListener('click', function () { loadPreset(btn.dataset.preset); });
  });

  btnCopy.addEventListener('click', function () {
    navigator.clipboard.writeText(cssOutput.value).then(function () {
      btnCopy.textContent = 'コピー完了！';
      btnCopy.classList.add('copied');
      setTimeout(function () {
        btnCopy.textContent = 'コピー';
        btnCopy.classList.remove('copied');
      }, 2000);
    }).catch(function () {
      cssOutput.select();
      document.execCommand('copy');
    });
  });

  /* ── Boot ───────────────────────────────────────────────── */
  loadPreset('fadeIn');

})();
</script>

---

### 関連ツール

> Flexboxレイアウトを作成 → [CSSフレックスボックスジェネレーター](/ja/tools/flexbox-generator/)
> グラデーションを生成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)
> ボックスシャドウを作成 → [CSSボックスシャドウジェネレーター](/ja/tools/box-shadow-generator/)
