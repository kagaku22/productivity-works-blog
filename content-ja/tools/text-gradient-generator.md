---
title: "CSSテキストグラデーション ジェネレーター — 無料ツール"
date: 2025-05-16
description: "美しいCSSテキストグラデーションをライブプレビューで作成。複数カラーストップ、角度調整、プリセット付き。background-clip CSSコードをワンクリックコピー。"
categories: ["無料ツール"]
slug: "text-gradient-generator"
ShowToc: false
aliases:
  - "/ja/tools/text-gradient/"
  - "/ja/tools/gradient-text/"
cover:
  image: "/images/covers/text-gradient-generator-ja.png"
  alt: "CSSテキストグラデーションジェネレーター"
---

<div id="tg-app">
<style>
/* ── スコープ済みスタイル: すべてのセレクターに #tg-app プレフィックス ── */
#tg-app *,
#tg-app *::before,
#tg-app *::after {
  box-sizing: border-box;
}
#tg-app {
  font-family: "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP",
               -apple-system, BlinkMacSystemFont, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}

/* プレビュー */
#tg-app .tg-preview-wrap {
  background: #f0f2f8;
  border-radius: 14px;
  padding: 40px 24px;
  margin-bottom: 28px;
  min-height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
#tg-app #tg-preview-text {
  display: inline-block;
  background: linear-gradient(135deg, #f5af19, #f12711);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  font-size: 64px;
  font-weight: 800;
  line-height: 1.3;
  word-break: break-all;
  transition: all 0.2s ease;
}

/* プリセットバー */
#tg-app .tg-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 24px;
}
#tg-app .tg-preset-btn {
  padding: 6px 14px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  font-size: 13px;
  font-weight: 700;
  color: #fff;
  transition: transform 0.15s, box-shadow 0.15s;
  text-shadow: 0 1px 2px rgba(0,0,0,0.3);
}
#tg-app .tg-preset-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.18);
}

/* コントロールグリッド */
#tg-app .tg-controls {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 24px;
}
@media (max-width: 600px) {
  #tg-app .tg-controls {
    grid-template-columns: 1fr;
  }
  #tg-app #tg-preview-text {
    font-size: 36px;
  }
}
#tg-app .tg-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
#tg-app .tg-field.tg-full {
  grid-column: 1 / -1;
}
#tg-app .tg-label {
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 0.04em;
  color: #555;
}
#tg-app .tg-field input[type="text"],
#tg-app .tg-field select {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #d4d8e8;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  transition: border-color 0.2s;
  font-family: inherit;
}
#tg-app .tg-field input[type="text"]:focus,
#tg-app .tg-field select:focus {
  border-color: #6c63ff;
  outline: none;
}
#tg-app .tg-field input[type="range"] {
  width: 100%;
  accent-color: #6c63ff;
}
#tg-app .tg-range-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#tg-app .tg-range-val {
  font-size: 13px;
  font-weight: 600;
  color: #6c63ff;
  min-width: 42px;
  text-align: right;
}

/* カラーストップ */
#tg-app .tg-stops-wrap {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#tg-app .tg-stop-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#tg-app .tg-color-input {
  width: 46px;
  height: 36px;
  border: 2px solid #d4d8e8;
  border-radius: 8px;
  padding: 2px;
  cursor: pointer;
  background: none;
}
#tg-app .tg-stop-label {
  font-size: 13px;
  color: #555;
  flex: 1;
}
#tg-app .tg-stop-remove {
  background: none;
  border: 1.5px solid #ddd;
  border-radius: 6px;
  width: 28px;
  height: 28px;
  cursor: pointer;
  font-size: 16px;
  color: #888;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.15s, color 0.15s;
}
#tg-app .tg-stop-remove:hover {
  background: #ffe0e0;
  color: #c0392b;
}
#tg-app .tg-add-stop-btn {
  padding: 7px 14px;
  background: #f0f2f8;
  border: 1.5px dashed #aab;
  border-radius: 8px;
  cursor: pointer;
  font-size: 13px;
  color: #666;
  transition: background 0.15s;
  width: fit-content;
  font-family: inherit;
}
#tg-app .tg-add-stop-btn:hover {
  background: #e4e8f8;
}

/* テキスト揃えボタン */
#tg-app .tg-align-group {
  display: flex;
  gap: 6px;
}
#tg-app .tg-align-btn {
  flex: 1;
  padding: 7px;
  border: 1.5px solid #d4d8e8;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 16px;
  transition: background 0.15s, border-color 0.15s;
}
#tg-app .tg-align-btn.active,
#tg-app .tg-align-btn:hover {
  background: #6c63ff;
  border-color: #6c63ff;
  color: #fff;
}

/* グラデーション種別 */
#tg-app .tg-type-group {
  display: flex;
  gap: 8px;
}
#tg-app .tg-type-btn {
  flex: 1;
  padding: 8px;
  border: 1.5px solid #d4d8e8;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 13px;
  font-weight: 700;
  transition: background 0.15s, border-color 0.15s;
  font-family: inherit;
}
#tg-app .tg-type-btn.active {
  background: #6c63ff;
  border-color: #6c63ff;
  color: #fff;
}

/* CSS出力 */
#tg-app .tg-output-wrap {
  background: #1a1a2e;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
  position: relative;
}
#tg-app .tg-output-label {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.08em;
  color: #8888bb;
  margin-bottom: 10px;
}
#tg-app #tg-css-output {
  font-family: "JetBrains Mono", "Fira Code", Consolas, monospace;
  font-size: 13px;
  line-height: 1.7;
  color: #a8e6cf;
  white-space: pre;
  overflow-x: auto;
  background: none;
  border: none;
  width: 100%;
  resize: none;
}
#tg-app .tg-copy-btn {
  position: absolute;
  top: 16px;
  right: 16px;
  padding: 7px 16px;
  background: #6c63ff;
  color: #fff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 13px;
  font-weight: 700;
  transition: background 0.2s, transform 0.15s;
  font-family: inherit;
}
#tg-app .tg-copy-btn:hover {
  background: #5548e0;
  transform: translateY(-1px);
}
#tg-app .tg-copy-btn.copied {
  background: #27ae60;
}

/* セクション見出し */
#tg-app .tg-section-title {
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 0.05em;
  color: #888;
  margin-bottom: 10px;
}
#tg-app .tg-card {
  background: #fff;
  border: 1.5px solid #e4e8f4;
  border-radius: 12px;
  padding: 18px;
  margin-bottom: 20px;
}

/* freee CTA */
#tg-app .tg-cta-box {
  background: linear-gradient(135deg, #eef2ff 0%, #f5f0ff 100%);
  border: 1.5px solid #c7d0f8;
  border-radius: 14px;
  padding: 22px 24px;
  margin-top: 32px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#tg-app .tg-cta-box h3 {
  margin: 0;
  font-size: 16px;
  color: #3a35b0;
}
#tg-app .tg-cta-box p {
  margin: 0;
  font-size: 14px;
  color: #555;
  line-height: 1.6;
}
#tg-app .tg-cta-btn {
  display: inline-block;
  padding: 10px 22px;
  background: #6c63ff;
  color: #fff;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 700;
  font-size: 14px;
  width: fit-content;
  transition: background 0.2s, transform 0.15s;
}
#tg-app .tg-cta-btn:hover {
  background: #5548e0;
  transform: translateY(-1px);
}
</style>

<!-- プレビュー -->
<div class="tg-preview-wrap">
  <span id="tg-preview-text">グラデーション文字</span>
</div>

<!-- プリセット -->
<div class="tg-section-title">プリセット</div>
<div class="tg-presets" id="tg-presets"></div>

<!-- コントロール -->
<div class="tg-card">
  <div class="tg-controls">

    <!-- テキスト入力 -->
    <div class="tg-field tg-full">
      <span class="tg-label">プレビューテキスト</span>
      <input type="text" id="tg-text-input" value="グラデーション文字" placeholder="テキストを入力..." maxlength="120">
    </div>

    <!-- グラデーション種別 -->
    <div class="tg-field">
      <span class="tg-label">グラデーション種別</span>
      <div class="tg-type-group">
        <button class="tg-type-btn active" data-type="linear">線形</button>
        <button class="tg-type-btn" data-type="radial">放射状</button>
      </div>
    </div>

    <!-- 角度（線形用） -->
    <div class="tg-field" id="tg-angle-field">
      <span class="tg-label">角度</span>
      <div class="tg-range-row">
        <input type="range" id="tg-angle" min="0" max="360" value="135">
        <span class="tg-range-val" id="tg-angle-val">135deg</span>
      </div>
    </div>

    <!-- カラーストップ -->
    <div class="tg-field tg-full">
      <span class="tg-label">カラーストップ（2〜4個）</span>
      <div class="tg-stops-wrap" id="tg-stops-wrap"></div>
      <button class="tg-add-stop-btn" id="tg-add-stop">+ カラーストップを追加</button>
    </div>

    <!-- フォントサイズ -->
    <div class="tg-field">
      <span class="tg-label">フォントサイズ</span>
      <div class="tg-range-row">
        <input type="range" id="tg-font-size" min="24" max="120" value="64">
        <span class="tg-range-val" id="tg-font-size-val">64px</span>
      </div>
    </div>

    <!-- フォントウェイト -->
    <div class="tg-field">
      <span class="tg-label">フォントウェイト</span>
      <select id="tg-font-weight">
        <option value="300">300 — ライト</option>
        <option value="400">400 — レギュラー</option>
        <option value="600">600 — セミボールド</option>
        <option value="700">700 — ボールド</option>
        <option value="800" selected>800 — エクストラボールド</option>
        <option value="900">900 — ブラック</option>
      </select>
    </div>

    <!-- テキスト揃え -->
    <div class="tg-field tg-full">
      <span class="tg-label">テキスト揃え</span>
      <div class="tg-align-group" id="tg-align-group">
        <button class="tg-align-btn active" data-align="left" title="左揃え">&#9664;</button>
        <button class="tg-align-btn" data-align="center" title="中央揃え">&#9644;</button>
        <button class="tg-align-btn" data-align="right" title="右揃え">&#9654;</button>
      </div>
    </div>

  </div>
</div>

<!-- CSS出力 -->
<div class="tg-output-wrap">
  <div class="tg-output-label">生成されたCSS</div>
  <textarea id="tg-css-output" rows="8" readonly spellcheck="false"></textarea>
  <button class="tg-copy-btn" id="tg-copy-btn">CSSをコピー</button>
</div>

<script>
(function () {
  /* ── 状態 ── */
  var state = {
    text: "グラデーション文字",
    type: "linear",
    angle: 135,
    stops: [
      { color: "#f5af19" },
      { color: "#f12711" }
    ],
    fontSize: 64,
    fontWeight: "800",
    textAlign: "left"
  };

  /* ── プリセット ── */
  var PRESETS = [
    { name: "サンセット", stops: ["#f5af19","#f12711"],        angle: 135, type: "linear" },
    { name: "オーシャン",  stops: ["#43cea2","#185a9d"],        angle: 120, type: "linear" },
    { name: "フォレスト", stops: ["#56ab2f","#a8e063"],        angle: 150, type: "linear" },
    { name: "ファイア",   stops: ["#ff4e50","#f9d423"],        angle: 90,  type: "linear" },
    { name: "ネオン",     stops: ["#12c2e9","#c471ed","#f64f59"], angle: 120, type: "linear" },
    { name: "パステル",   stops: ["#f8cdda","#1d2b64"],        angle: 100, type: "linear" },
    { name: "ゴールド",   stops: ["#f7971e","#ffd200"],        angle: 110, type: "linear" }
  ];

  var PRESET_GRADIENTS = {
    "サンセット": "linear-gradient(135deg,#f5af19,#f12711)",
    "オーシャン":  "linear-gradient(120deg,#43cea2,#185a9d)",
    "フォレスト": "linear-gradient(150deg,#56ab2f,#a8e063)",
    "ファイア":   "linear-gradient(90deg,#ff4e50,#f9d423)",
    "ネオン":     "linear-gradient(120deg,#12c2e9,#c471ed,#f64f59)",
    "パステル":   "linear-gradient(100deg,#f8cdda,#1d2b64)",
    "ゴールド":   "linear-gradient(110deg,#f7971e,#ffd200)"
  };

  /* ── DOM参照 ── */
  var previewEl   = document.getElementById("tg-preview-text");
  var textInput   = document.getElementById("tg-text-input");
  var angleSlider = document.getElementById("tg-angle");
  var angleVal    = document.getElementById("tg-angle-val");
  var angleField  = document.getElementById("tg-angle-field");
  var fsSlider    = document.getElementById("tg-font-size");
  var fsVal       = document.getElementById("tg-font-size-val");
  var fwSelect    = document.getElementById("tg-font-weight");
  var stopsWrap   = document.getElementById("tg-stops-wrap");
  var addStopBtn  = document.getElementById("tg-add-stop");
  var cssOutput   = document.getElementById("tg-css-output");
  var copyBtn     = document.getElementById("tg-copy-btn");
  var presetsWrap = document.getElementById("tg-presets");
  var alignGroup  = document.getElementById("tg-align-group");

  /* ── グラデーションCSS生成 ── */
  function gradientCSS() {
    var colors = state.stops.map(function (s) { return s.color; }).join(", ");
    if (state.type === "radial") {
      return "radial-gradient(circle, " + colors + ")";
    }
    return "linear-gradient(" + state.angle + "deg, " + colors + ")";
  }

  function buildCSS() {
    var g = gradientCSS();
    return ".gradient-text {\n" +
      "  background: " + g + ";\n" +
      "  -webkit-background-clip: text;\n" +
      "  background-clip: text;\n" +
      "  -webkit-text-fill-color: transparent;\n" +
      "  color: transparent;\n" +
      "  font-size: " + state.fontSize + "px;\n" +
      "  font-weight: " + state.fontWeight + ";\n" +
      "  text-align: " + state.textAlign + ";\n" +
      "  display: inline-block;\n" +
      "}";
  }

  function applyPreview() {
    var g = gradientCSS();
    previewEl.style.backgroundImage      = g;
    previewEl.style.webkitBackgroundClip = "text";
    previewEl.style.backgroundClip       = "text";
    previewEl.style.webkitTextFillColor  = "transparent";
    previewEl.style.color                = "transparent";
    previewEl.style.fontSize             = state.fontSize + "px";
    previewEl.style.fontWeight           = state.fontWeight;
    previewEl.style.textAlign            = state.textAlign;
    previewEl.textContent                = state.text || "グラデーション文字";
    cssOutput.value                      = buildCSS();
  }

  /* ── ストップ行のレンダリング ── */
  function renderStops() {
    stopsWrap.innerHTML = "";
    state.stops.forEach(function (stop, i) {
      var row = document.createElement("div");
      row.className = "tg-stop-row";

      var colorInput = document.createElement("input");
      colorInput.type = "color";
      colorInput.className = "tg-color-input";
      colorInput.value = stop.color;
      (function (idx) {
        colorInput.addEventListener("input", function () {
          state.stops[idx].color = this.value;
          applyPreview();
        });
      })(i);

      var lbl = document.createElement("span");
      lbl.className = "tg-stop-label";
      lbl.textContent = "ストップ " + (i + 1);

      var removeBtn = document.createElement("button");
      removeBtn.className = "tg-stop-remove";
      removeBtn.textContent = "×";
      removeBtn.title = "削除";
      removeBtn.disabled = state.stops.length <= 2;
      removeBtn.style.opacity = state.stops.length <= 2 ? "0.3" : "1";
      (function (idx) {
        removeBtn.addEventListener("click", function () {
          if (state.stops.length > 2) {
            state.stops.splice(idx, 1);
            renderStops();
            applyPreview();
          }
        });
      })(i);

      row.appendChild(colorInput);
      row.appendChild(lbl);
      row.appendChild(removeBtn);
      stopsWrap.appendChild(row);
    });

    addStopBtn.style.display = state.stops.length >= 4 ? "none" : "flex";
  }

  /* ── プリセット生成 ── */
  PRESETS.forEach(function (preset) {
    var btn = document.createElement("button");
    btn.className = "tg-preset-btn";
    btn.textContent = preset.name;
    btn.style.backgroundImage = PRESET_GRADIENTS[preset.name];
    btn.addEventListener("click", function () {
      state.type  = preset.type;
      state.angle = preset.angle;
      state.stops = preset.stops.map(function (c) { return { color: c }; });
      angleSlider.value = preset.angle;
      angleVal.textContent = preset.angle + "deg";
      document.querySelectorAll("#tg-app .tg-type-btn").forEach(function (b) {
        b.classList.toggle("active", b.dataset.type === preset.type);
      });
      angleField.style.display = preset.type === "radial" ? "none" : "";
      renderStops();
      applyPreview();
    });
    presetsWrap.appendChild(btn);
  });

  /* ── イベント: テキスト入力 ── */
  textInput.addEventListener("input", function () {
    state.text = this.value;
    applyPreview();
  });

  /* ── イベント: 角度 ── */
  angleSlider.addEventListener("input", function () {
    state.angle = parseInt(this.value, 10);
    angleVal.textContent = state.angle + "deg";
    applyPreview();
  });

  /* ── イベント: フォントサイズ ── */
  fsSlider.addEventListener("input", function () {
    state.fontSize = parseInt(this.value, 10);
    fsVal.textContent = state.fontSize + "px";
    applyPreview();
  });

  /* ── イベント: フォントウェイト ── */
  fwSelect.addEventListener("change", function () {
    state.fontWeight = this.value;
    applyPreview();
  });

  /* ── イベント: グラデーション種別 ── */
  document.querySelectorAll("#tg-app .tg-type-btn").forEach(function (btn) {
    btn.addEventListener("click", function () {
      state.type = this.dataset.type;
      document.querySelectorAll("#tg-app .tg-type-btn").forEach(function (b) {
        b.classList.toggle("active", b === btn);
      });
      angleField.style.display = state.type === "radial" ? "none" : "";
      applyPreview();
    });
  });

  /* ── イベント: テキスト揃え ── */
  alignGroup.querySelectorAll(".tg-align-btn").forEach(function (btn) {
    btn.addEventListener("click", function () {
      state.textAlign = this.dataset.align;
      alignGroup.querySelectorAll(".tg-align-btn").forEach(function (b) {
        b.classList.toggle("active", b === btn);
      });
      applyPreview();
    });
  });

  /* ── イベント: ストップ追加 ── */
  addStopBtn.addEventListener("click", function () {
    if (state.stops.length < 4) {
      state.stops.push({ color: "#ffffff" });
      renderStops();
      applyPreview();
    }
  });

  /* ── イベント: CSSコピー ── */
  copyBtn.addEventListener("click", function () {
    navigator.clipboard.writeText(cssOutput.value).then(function () {
      copyBtn.textContent = "コピー完了!";
      copyBtn.classList.add("copied");
      setTimeout(function () {
        copyBtn.textContent = "CSSをコピー";
        copyBtn.classList.remove("copied");
      }, 2000);
    }).catch(function () {
      cssOutput.select();
      document.execCommand("copy");
      copyBtn.textContent = "コピー完了!";
      setTimeout(function () { copyBtn.textContent = "CSSをコピー"; }, 2000);
    });
  });

  /* ── 初期化 ── */
  renderStops();
  applyPreview();
})();
</script>
</div>

---

## 仕組み

CSSテキストグラデーションは **`background-clip: text`** を使ったテクニックです。

1. 要素の `background` プロパティにグラデーションを適用する。
2. `-webkit-background-clip: text` と `background-clip: text` で背景をテキスト形状に切り抜く。
3. `-webkit-text-fill-color: transparent` でテキスト自体を透明にする。

SVGや画像は不要で、純粋なCSSだけでグラデーション文字を実現できます。

---

## ブラウザ対応状況

| ブラウザ | 対応状況 |
|---|---|
| Chrome / Edge | 完全対応 |
| Firefox | 完全対応（Firefox 122以降） |
| Safari | 完全対応（`-webkit-` プレフィックスが必要） |
| iOS Safari | 完全対応 |

---

## 活用のコツ

- **コントラストの高いプリセット**（サンセット、ファイア、ネオン）はダーク背景で映えます。
- **パステル系グラデーション**は大きな見出しテキストのライトモードに最適です。
- クロスブラウザ対応のため `-webkit-background-clip: text` と `background-clip: text` の**両方**を必ず記述してください。
- グラデーションが正しくクリップされるよう `display: inline-block` を付与してください。`block` 要素は横幅いっぱいに広がり、グラデーションの見え方が変わります。

---

### 関連ツール

> 背景グラデーションを作成 → [CSSグラデーションジェネレーター](/ja/tools/css-gradient-generator/)

> カラーパレットを生成 → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)

> ボックスシャドウを作成 → [CSSボックスシャドウジェネレーター](/ja/tools/box-shadow-generator/)

---

<div id="tg-app">
<div class="tg-cta-box">
<h3>freeeで会計・請求書を自動化しませんか？</h3>
<p>個人事業主・フリーランスの方に人気のクラウド会計サービス <strong>freee</strong> なら、領収書の自動読み取りから確定申告まで一括管理。ツール開発で忙しいあなたの経理を大幅に効率化できます。</p>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" class="tg-cta-btn" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>
</div>
