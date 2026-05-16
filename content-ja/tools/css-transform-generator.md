---
title: "CSS Transformジェネレーター — ビジュアルプレイグラウンド"
date: 2025-05-16
description: "CSSトランスフォームをビジュアルで作成。移動・回転・拡縮・傾斜をライブプレビュー。CSSコードを即コピー。"
categories: ["無料ツール"]
slug: "css-transform-generator"
ShowToc: false
cover:
  image: "/images/covers/css-transform-generator-ja.png"
  alt: "CSS Transformジェネレーター"
---

<div id="css-transform-gen-ja-root">

<style>
#css-transform-gen-ja-root {
  font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
}
#css-transform-gen-ja-root *,
#css-transform-gen-ja-root *::before,
#css-transform-gen-ja-root *::after {
  box-sizing: border-box;
}
#css-transform-gen-ja-root .ctgja-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
  margin-bottom: 24px;
}
@media (max-width: 640px) {
  #css-transform-gen-ja-root .ctgja-layout {
    grid-template-columns: 1fr;
  }
}
#css-transform-gen-ja-root .ctgja-controls {
  background: #f8f9ff;
  border: 1px solid #dde1f0;
  border-radius: 12px;
  padding: 20px;
}
#css-transform-gen-ja-root .ctgja-preview-panel {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
#css-transform-gen-ja-root .ctgja-preview-box {
  background: #f0f4ff;
  border: 1px solid #dde1f0;
  border-radius: 12px;
  min-height: 280px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  position: relative;
}
#css-transform-gen-ja-root .ctgja-preview-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #7b82a6;
  margin-bottom: 12px;
}
#css-transform-gen-ja-root .ctgja-subject {
  width: 100px;
  height: 100px;
  background: linear-gradient(135deg, #4f6ef7 0%, #7c3aed 100%);
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 13px;
  font-weight: 700;
  transition: transform 0.15s ease;
  will-change: transform;
  user-select: none;
}
#css-transform-gen-ja-root .ctgja-section-title {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #4f6ef7;
  margin: 16px 0 10px;
  padding-bottom: 4px;
  border-bottom: 1px solid #e2e6fb;
}
#css-transform-gen-ja-root .ctgja-section-title:first-child {
  margin-top: 0;
}
#css-transform-gen-ja-root .ctgja-row {
  display: grid;
  grid-template-columns: 110px 1fr 58px;
  align-items: center;
  gap: 8px;
  margin-bottom: 10px;
}
#css-transform-gen-ja-root .ctgja-row label {
  font-size: 13px;
  color: #3a3f5c;
  font-weight: 500;
}
#css-transform-gen-ja-root .ctgja-row input[type="range"] {
  width: 100%;
  accent-color: #4f6ef7;
  cursor: pointer;
}
#css-transform-gen-ja-root .ctgja-row .ctgja-val {
  font-size: 12px;
  font-weight: 700;
  color: #4f6ef7;
  text-align: right;
  white-space: nowrap;
}
#css-transform-gen-ja-root .ctgja-output {
  background: #1a1a2e;
  border-radius: 10px;
  padding: 14px 16px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 13px;
  color: #a8b4ff;
  word-break: break-all;
  line-height: 1.6;
  min-height: 60px;
  white-space: pre-wrap;
}
#css-transform-gen-ja-root .ctgja-output span.ctgja-prop {
  color: #7ee8a2;
}
#css-transform-gen-ja-root .ctgja-output span.ctgja-val-text {
  color: #ffd97d;
}
#css-transform-gen-ja-root .ctgja-btn-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}
#css-transform-gen-ja-root .ctgja-btn {
  padding: 9px 18px;
  border: none;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#css-transform-gen-ja-root .ctgja-btn:active {
  transform: scale(0.97);
}
#css-transform-gen-ja-root .ctgja-btn-primary {
  background: #4f6ef7;
  color: #fff;
}
#css-transform-gen-ja-root .ctgja-btn-primary:hover {
  background: #3a57e8;
}
#css-transform-gen-ja-root .ctgja-btn-secondary {
  background: #e8eaff;
  color: #4f6ef7;
}
#css-transform-gen-ja-root .ctgja-btn-secondary:hover {
  background: #d4d9ff;
}
#css-transform-gen-ja-root .ctgja-presets-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}
#css-transform-gen-ja-root .ctgja-preset-btn {
  padding: 6px 14px;
  border: 1.5px solid #dde1f0;
  border-radius: 20px;
  background: #fff;
  font-size: 12px;
  font-weight: 700;
  color: #4a4f72;
  cursor: pointer;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
}
#css-transform-gen-ja-root .ctgja-preset-btn:hover {
  border-color: #4f6ef7;
  color: #4f6ef7;
  background: #f0f3ff;
}
#css-transform-gen-ja-root .ctgja-copy-notice {
  font-size: 12px;
  color: #22c55e;
  font-weight: 700;
  min-height: 18px;
  transition: opacity 0.3s;
}
#css-transform-gen-ja-root .ctgja-perspective-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}
#css-transform-gen-ja-root .ctgja-perspective-row input[type="checkbox"] {
  accent-color: #4f6ef7;
  width: 15px;
  height: 15px;
  cursor: pointer;
}
#css-transform-gen-ja-root .ctgja-perspective-row label {
  font-size: 13px;
  color: #3a3f5c;
  font-weight: 500;
  cursor: pointer;
}
#css-transform-gen-ja-root .ctgja-freee-cta {
  background: linear-gradient(135deg, #e8f5e9 0%, #f1f8e9 100%);
  border: 1.5px solid #a5d6a7;
  border-radius: 12px;
  padding: 20px 24px;
  margin-top: 32px;
}
#css-transform-gen-ja-root .ctgja-freee-cta h3 {
  margin: 0 0 8px;
  font-size: 16px;
  color: #1b5e20;
}
#css-transform-gen-ja-root .ctgja-freee-cta p {
  margin: 0 0 14px;
  font-size: 14px;
  color: #2e7d32;
  line-height: 1.6;
}
#css-transform-gen-ja-root .ctgja-freee-cta a {
  display: inline-block;
  padding: 10px 22px;
  background: #2e7d32;
  color: #fff;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  text-decoration: none;
  transition: background 0.15s;
}
#css-transform-gen-ja-root .ctgja-freee-cta a:hover {
  background: #1b5e20;
}
</style>

## CSS `transform` とは？

`transform` プロパティを使うと、ドキュメントのレイアウトを崩さずに、要素を視覚的に移動・回転・拡縮・傾斜させることができます。トランスフォームはGPUアクセラレーション対応で、アニメーションとの相性も抜群です。

---

## CSS Transformジェネレーター

スライダーを動かしてリアルタイムでトランスフォームを調整し、**CSSをコピー**ボタンで即座にコードを取得できます。

**プリセット：**

<div id="ctgja-app">
  <div class="ctgja-presets-row">
    <button class="ctgja-preset-btn" onclick="ctgjaApplyPreset('flip')">フリップ</button>
    <button class="ctgja-preset-btn" onclick="ctgjaApplyPreset('tilt')">チルト</button>
    <button class="ctgja-preset-btn" onclick="ctgjaApplyPreset('zoom')">ズーム</button>
    <button class="ctgja-preset-btn" onclick="ctgjaApplyPreset('rotate3d')">3D回転</button>
    <button class="ctgja-preset-btn" onclick="ctgjaApplyPreset('reset')">リセット</button>
  </div>

  <div class="ctgja-layout">
    <div class="ctgja-controls">
      <div class="ctgja-section-title">移動 (Translate)</div>
      <div class="ctgja-row">
        <label for="ctgja-tx">X軸移動</label>
        <input type="range" id="ctgja-tx" min="-200" max="200" value="0" step="1" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-tx-val">0px</span>
      </div>
      <div class="ctgja-row">
        <label for="ctgja-ty">Y軸移動</label>
        <input type="range" id="ctgja-ty" min="-200" max="200" value="0" step="1" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-ty-val">0px</span>
      </div>

      <div class="ctgja-section-title">回転 (Rotate)</div>
      <div class="ctgja-row">
        <label for="ctgja-rot">回転角度</label>
        <input type="range" id="ctgja-rot" min="-360" max="360" value="0" step="1" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-rot-val">0deg</span>
      </div>

      <div class="ctgja-section-title">拡縮 (Scale)</div>
      <div class="ctgja-row">
        <label for="ctgja-sx">X軸拡縮</label>
        <input type="range" id="ctgja-sx" min="0" max="3" value="1" step="0.01" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-sx-val">1.00</span>
      </div>
      <div class="ctgja-row">
        <label for="ctgja-sy">Y軸拡縮</label>
        <input type="range" id="ctgja-sy" min="0" max="3" value="1" step="0.01" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-sy-val">1.00</span>
      </div>

      <div class="ctgja-section-title">傾斜 (Skew)</div>
      <div class="ctgja-row">
        <label for="ctgja-skx">X軸傾斜</label>
        <input type="range" id="ctgja-skx" min="-60" max="60" value="0" step="1" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-skx-val">0deg</span>
      </div>
      <div class="ctgja-row">
        <label for="ctgja-sky">Y軸傾斜</label>
        <input type="range" id="ctgja-sky" min="-60" max="60" value="0" step="1" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-sky-val">0deg</span>
      </div>

      <div class="ctgja-section-title">遠近感 (Perspective)</div>
      <div class="ctgja-perspective-row">
        <input type="checkbox" id="ctgja-persp-en" onchange="ctgjaUpdate()">
        <label for="ctgja-persp-en">遠近感を有効化</label>
      </div>
      <div class="ctgja-row">
        <label for="ctgja-persp">奥行き距離</label>
        <input type="range" id="ctgja-persp" min="100" max="2000" value="600" step="10" oninput="ctgjaUpdate()">
        <span class="ctgja-val" id="ctgja-persp-val">600px</span>
      </div>
    </div>

    <div class="ctgja-preview-panel">
      <div>
        <div class="ctgja-preview-label">ライブプレビュー</div>
        <div class="ctgja-preview-box">
          <div class="ctgja-subject" id="ctgja-subject">ボックス</div>
        </div>
      </div>
      <div>
        <div class="ctgja-preview-label">生成されたCSS</div>
        <div class="ctgja-output" id="ctgja-output"><span class="ctgja-prop">transform</span>: <span class="ctgja-val-text">none</span>;</div>
      </div>
      <div class="ctgja-btn-row">
        <button class="ctgja-btn ctgja-btn-primary" onclick="ctgjaCopy()">CSSをコピー</button>
        <button class="ctgja-btn ctgja-btn-secondary" onclick="ctgjaApplyPreset('reset')">すべてリセット</button>
      </div>
      <div class="ctgja-copy-notice" id="ctgja-copy-notice"></div>
    </div>
  </div>
</div>

<script>
(function () {
  var presets = {
    flip:    { tx:0, ty:0, rot:0,  sx:-1,   sy:1,    skx:0,  sky:0,  persp:false, perspVal:600 },
    tilt:    { tx:0, ty:0, rot:15, sx:1,    sy:1,    skx:10, sky:0,  persp:false, perspVal:600 },
    zoom:    { tx:0, ty:0, rot:0,  sx:1.5,  sy:1.5,  skx:0,  sky:0,  persp:false, perspVal:600 },
    rotate3d:{ tx:0, ty:0, rot:30, sx:1,    sy:0.85, skx:0,  sky:0,  persp:true,  perspVal:600 },
    reset:   { tx:0, ty:0, rot:0,  sx:1,    sy:1,    skx:0,  sky:0,  persp:false, perspVal:600 }
  };

  function r(id) { return document.getElementById(id); }

  function ctgjaUpdate() {
    var tx   = parseFloat(r('ctgja-tx').value);
    var ty   = parseFloat(r('ctgja-ty').value);
    var rot  = parseFloat(r('ctgja-rot').value);
    var sx   = parseFloat(r('ctgja-sx').value);
    var sy   = parseFloat(r('ctgja-sy').value);
    var skx  = parseFloat(r('ctgja-skx').value);
    var sky  = parseFloat(r('ctgja-sky').value);
    var perspEn  = r('ctgja-persp-en').checked;
    var perspVal = parseFloat(r('ctgja-persp').value);

    r('ctgja-tx-val').textContent    = tx + 'px';
    r('ctgja-ty-val').textContent    = ty + 'px';
    r('ctgja-rot-val').textContent   = rot + 'deg';
    r('ctgja-sx-val').textContent    = sx.toFixed(2);
    r('ctgja-sy-val').textContent    = sy.toFixed(2);
    r('ctgja-skx-val').textContent   = skx + 'deg';
    r('ctgja-sky-val').textContent   = sky + 'deg';
    r('ctgja-persp-val').textContent = perspVal + 'px';

    var parts = [];
    if (tx !== 0 || ty !== 0) parts.push('translate(' + tx + 'px, ' + ty + 'px)');
    if (rot !== 0)             parts.push('rotate(' + rot + 'deg)');
    if (sx !== 1 || sy !== 1)  parts.push('scale(' + sx.toFixed(2) + ', ' + sy.toFixed(2) + ')');
    if (skx !== 0 || sky !== 0) parts.push('skew(' + skx + 'deg, ' + sky + 'deg)');

    var transformVal  = parts.length ? parts.join(' ') : 'none';
    var perspPrefix   = perspEn ? 'perspective(' + perspVal + 'px) ' : '';
    var fullTransform = perspPrefix + (parts.length ? parts.join(' ') : 'none');

    r('ctgja-subject').style.transform = fullTransform;

    var cssText = perspEn
      ? 'perspective: ' + perspVal + 'px;\ntransform: ' + transformVal + ';'
      : 'transform: ' + fullTransform + ';';

    r('ctgja-output').innerHTML =
      (perspEn
        ? '<span class="ctgja-prop">perspective</span>: <span class="ctgja-val-text">' + perspVal + 'px</span>;\n'
        : '') +
      '<span class="ctgja-prop">transform</span>: <span class="ctgja-val-text">' + (perspPrefix + transformVal) + '</span>;';

    r('ctgja-output')._cssText = cssText;
  }

  function ctgjaApplyPreset(name) {
    var p = presets[name];
    r('ctgja-tx').value        = p.tx;
    r('ctgja-ty').value        = p.ty;
    r('ctgja-rot').value       = p.rot;
    r('ctgja-sx').value        = p.sx;
    r('ctgja-sy').value        = p.sy;
    r('ctgja-skx').value       = p.skx;
    r('ctgja-sky').value       = p.sky;
    r('ctgja-persp-en').checked = p.persp;
    r('ctgja-persp').value     = p.perspVal;
    ctgjaUpdate();
  }

  function ctgjaCopy() {
    var text = r('ctgja-output')._cssText || r('ctgja-output').textContent;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function () { ctgjaShowCopied(); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      ctgjaShowCopied();
    }
  }

  function ctgjaShowCopied() {
    var el = r('ctgja-copy-notice');
    el.textContent = 'クリップボードにコピーしました！';
    el.style.opacity = '1';
    setTimeout(function () { el.style.opacity = '0'; }, 2000);
  }

  window.ctgjaUpdate      = ctgjaUpdate;
  window.ctgjaApplyPreset = ctgjaApplyPreset;
  window.ctgjaCopy        = ctgjaCopy;

  ctgjaUpdate();
})();
</script>

---

## トランスフォーム関数の解説

| 関数 | 構文 | 説明 |
|---|---|---|
| `translate()` | `translate(x, y)` | 要素をX・Y軸方向に移動 |
| `rotate()` | `rotate(deg)` | 正の値で時計回り、負の値で反時計回りに回転 |
| `scale()` | `scale(x, y)` | 要素を拡縮。`1`が原寸、`-1`で反転 |
| `skew()` | `skew(xdeg, ydeg)` | 各軸に沿って要素を傾斜 |
| `perspective()` | `perspective(px)` | 3D空間の奥行き感を設定 |

### トランスフォームの順序に注意

複数のトランスフォームは右から左の順に適用されます。`translate(50px, 0) rotate(45deg)` は「まず回転してから移動」という意味になります。順序を変えると見た目が変わるので注意が必要です。

### パフォーマンスのコツ

- アニメーションには `transform` と `opacity` を優先的に使用してください — レイアウトと描画の処理をスキップできます。
- 頻繁にアニメーションする要素には `will-change: transform` を追加しましょう。
- 静的な要素への `will-change` の多用は GPUメモリを消費するため避けてください。

### 3D トランスフォームのサンプル

```css
/* 親要素で3D空間を設定 */
.container {
  perspective: 600px;
}

/* 子要素に3D変換を適用 */
.card {
  transform: rotateY(30deg) rotateX(10deg);
  transform-style: preserve-3d;
  backface-visibility: hidden;
}
```

---

## 関連ツール

- [CSSアニメーションジェネレーター](/ja/tools/css-animation-generator/) — キーフレームアニメーションをビジュアルで作成
- [CSS Flexboxジェネレーター](/ja/tools/css-flexbox-generator/) — フレックスレイアウトをライブプレビューで設計
- [CSS ボックスシャドウジェネレーター](/ja/tools/css-box-shadow-generator/) — 多層シャドウをインタラクティブに作成

---

<div class="ctgja-freee-cta">
  <h3>freee会計で経理をもっとスマートに</h3>
  <p>個人事業主・フリーランスの方に。確定申告・請求書・経費管理をクラウドで一元化。面倒な帳簿付けを自動化して、本業に集中しましょう。</p>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">freeeを無料で試す</a>
</div>

</div>
