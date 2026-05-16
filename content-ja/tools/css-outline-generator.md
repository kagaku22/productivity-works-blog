---
title: "CSSアウトライン ジェネレーター"
slug: "css-outline-generator"
date: 2025-05-16
description: "無料のCSSアウトラインジェネレーター。スタイル・幅・色・オフセットをライブプレビューで設定。フォーカス状態のアクセシビリティ対応も。"
categories: ["無料ツール"]
tags: ["CSS", "アウトライン", "ジェネレーター", "Webデザイン", "アクセシビリティ", "フォーカス状態"]
cover:
  image: "/images/covers/css-outline-generator-ja.png"
  alt: "CSSアウトラインジェネレーター ライブプレビュー付き無料ツール"
ShowToc: false
---

CSSの `outline` プロパティを即座に生成。スタイル・幅・色・オフセットをリアルタイムプレビューで調整し、コピーするだけで使えるCSSコードを取得できます。

<div id="ot-app">

<style>
/* ── Reset & layout ─────────────────────────────────────────────── */
#ot-app *,
#ot-app *::before,
#ot-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#ot-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Segoe UI", sans-serif;
  font-size: 15px;
  color: #1a1a2e;
  background: #f8f9fc;
  border-radius: 12px;
  padding: 0 0 32px;
  max-width: 900px;
}

/* ── Section headings ────────────────────────────────────────────── */
#ot-app .ot-section-title {
  font-size: 12px;
  font-weight: 700;
  letter-spacing: .06em;
  text-transform: uppercase;
  color: #6b7280;
  margin-bottom: 12px;
}

/* ── Two-column layout ───────────────────────────────────────────── */
#ot-app .ot-layout {
  display: grid;
  grid-template-columns: 300px 1fr;
  gap: 20px;
  align-items: start;
}
@media (max-width: 680px) {
  #ot-app .ot-layout { grid-template-columns: 1fr; }
}

/* ── Controls panel ──────────────────────────────────────────────── */
#ot-app .ot-panel {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 18px;
}

#ot-app .ot-control-group { display: flex; flex-direction: column; gap: 6px; }

#ot-app label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#ot-app label span.ot-val {
  font-weight: 700;
  color: #4f46e5;
  font-size: 12px;
  background: #eef2ff;
  border-radius: 4px;
  padding: 1px 6px;
  min-width: 44px;
  text-align: center;
}

#ot-app select,
#ot-app input[type="range"] {
  width: 100%;
}

#ot-app select {
  appearance: none;
  background: #f3f4f6 url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%236b7280' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E") no-repeat right 10px center;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  padding: 7px 30px 7px 10px;
  font-size: 13px;
  color: #1a1a2e;
  cursor: pointer;
}
#ot-app select:focus { outline: 2px solid #4f46e5; outline-offset: 1px; }

#ot-app input[type="range"] {
  accent-color: #4f46e5;
  height: 4px;
  cursor: pointer;
}

/* Color row */
#ot-app .ot-color-row {
  display: grid;
  grid-template-columns: 44px 1fr;
  gap: 8px;
  align-items: center;
}
#ot-app input[type="color"] {
  width: 44px;
  height: 36px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  padding: 2px;
  cursor: pointer;
  background: #fff;
}
#ot-app .ot-hex-input {
  width: 100%;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  padding: 7px 10px;
  font-size: 13px;
  font-family: "Fira Mono", "Courier New", monospace;
  color: #1a1a2e;
}
#ot-app .ot-hex-input:focus { outline: 2px solid #4f46e5; outline-offset: 1px; }

/* Toggle */
#ot-app .ot-toggle-row {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  cursor: pointer;
  user-select: none;
}
#ot-app .ot-toggle {
  position: relative;
  width: 40px;
  height: 22px;
  flex-shrink: 0;
}
#ot-app .ot-toggle input { opacity: 0; width: 0; height: 0; position: absolute; }
#ot-app .ot-toggle-track {
  position: absolute;
  inset: 0;
  background: #d1d5db;
  border-radius: 11px;
  transition: background .2s;
}
#ot-app .ot-toggle input:checked ~ .ot-toggle-track { background: #4f46e5; }
#ot-app .ot-toggle-thumb {
  position: absolute;
  top: 3px;
  left: 3px;
  width: 16px;
  height: 16px;
  background: #fff;
  border-radius: 50%;
  transition: transform .2s;
  box-shadow: 0 1px 3px rgba(0,0,0,.2);
}
#ot-app .ot-toggle input:checked ~ .ot-toggle-thumb { transform: translateX(18px); }

/* ── Right column ────────────────────────────────────────────────── */
#ot-app .ot-right { display: flex; flex-direction: column; gap: 20px; }

/* ── Preview area ────────────────────────────────────────────────── */
#ot-app .ot-preview-wrap {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
  padding: 24px;
}
#ot-app .ot-preview-stage {
  display: flex;
  gap: 32px;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  min-height: 140px;
  background: repeating-conic-gradient(#f0f0f0 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
  border-radius: 8px;
  padding: 32px 24px;
}
#ot-app .ot-preview-box {
  width: 120px;
  height: 80px;
  background: #fff;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  font-weight: 600;
  color: #6b7280;
  flex-direction: column;
  gap: 4px;
  transition: outline .15s, border .15s, outline-offset .15s;
}
#ot-app .ot-preview-box .ot-label {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: .05em;
  text-transform: uppercase;
  color: #9ca3af;
  margin-top: 4px;
}

/* Focus demo */
#ot-app .ot-focus-demo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}
#ot-app .ot-focus-btn {
  padding: 8px 18px;
  border: none;
  border-radius: 6px;
  background: #4f46e5;
  color: #fff;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: outline .15s, outline-offset .15s;
}
#ot-app .ot-focus-label {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: .05em;
  text-transform: uppercase;
  color: #9ca3af;
}

/* ── Presets ─────────────────────────────────────────────────────── */
#ot-app .ot-presets-wrap {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
  padding: 20px;
}
#ot-app .ot-presets-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
  gap: 10px;
}
#ot-app .ot-preset-btn {
  border: 1.5px solid #e5e7eb;
  border-radius: 8px;
  padding: 10px 12px;
  background: #f9fafb;
  font-size: 12px;
  font-weight: 600;
  color: #374151;
  cursor: pointer;
  text-align: left;
  transition: border-color .15s, background .15s;
  display: flex;
  flex-direction: column;
  gap: 4px;
}
#ot-app .ot-preset-btn:hover { border-color: #4f46e5; background: #eef2ff; color: #4f46e5; }
#ot-app .ot-preset-swatch {
  width: 100%;
  height: 28px;
  border-radius: 4px;
  background: #f3f4f6;
  margin-bottom: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* ── Output ──────────────────────────────────────────────────────── */
#ot-app .ot-output-wrap {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
  padding: 20px;
}
#ot-app .ot-output-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}
#ot-app .ot-copy-btn {
  background: #4f46e5;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 7px 16px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background .15s;
  display: flex;
  align-items: center;
  gap: 6px;
}
#ot-app .ot-copy-btn:hover { background: #4338ca; }
#ot-app .ot-copy-btn.copied { background: #059669; }
#ot-app pre.ot-code {
  background: #0f172a;
  border-radius: 8px;
  padding: 16px 18px;
  overflow-x: auto;
  font-family: "Fira Mono", "Courier New", monospace;
  font-size: 13px;
  line-height: 1.7;
  white-space: pre;
  color: #e2e8f0;
}
#ot-app .ot-kw   { color: #818cf8; }
#ot-app .ot-prop { color: #7dd3fc; }
#ot-app .ot-val-c{ color: #86efac; }
#ot-app .ot-punc { color: #94a3b8; }
#ot-app .ot-comment { color: #64748b; font-style: italic; }

/* ── A11y output ─────────────────────────────────────────────────── */
#ot-app .ot-a11y-wrap {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
  padding: 20px;
}
#ot-app .ot-a11y-note {
  font-size: 12px;
  color: #6b7280;
  margin-bottom: 12px;
  line-height: 1.6;
}
#ot-app pre.ot-code-a11y {
  background: #0f172a;
  border-radius: 8px;
  padding: 16px 18px;
  overflow-x: auto;
  font-family: "Fira Mono", "Courier New", monospace;
  font-size: 13px;
  line-height: 1.7;
  white-space: pre;
  color: #e2e8f0;
}

/* ── Info strip ──────────────────────────────────────────────────── */
#ot-app .ot-info {
  background: #eef2ff;
  border-left: 3px solid #4f46e5;
  border-radius: 0 6px 6px 0;
  padding: 12px 16px;
  font-size: 12.5px;
  color: #3730a3;
  line-height: 1.6;
}

/* ── freee CTA ───────────────────────────────────────────────────── */
#ot-app .ot-freee-cta {
  background: linear-gradient(135deg, #00c4a2 0%, #00a37a 100%);
  border-radius: 10px;
  padding: 24px 28px;
  color: #fff;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#ot-app .ot-freee-cta h3 {
  font-size: 16px;
  font-weight: 700;
  line-height: 1.4;
}
#ot-app .ot-freee-cta p {
  font-size: 13px;
  opacity: .9;
  line-height: 1.6;
}
#ot-app .ot-freee-btn {
  display: inline-block;
  background: #fff;
  color: #00a37a;
  font-weight: 700;
  font-size: 14px;
  border-radius: 6px;
  padding: 10px 22px;
  text-decoration: none;
  align-self: flex-start;
  transition: opacity .15s;
}
#ot-app .ot-freee-btn:hover { opacity: .85; }
</style>

<!-- ── Presets ──────────────────────────────────────────────── -->
<div class="ot-presets-wrap">
  <p class="ot-section-title">プリセット</p>
  <div class="ot-presets-grid" id="ot-presets"></div>
</div>

<!-- ── Main layout ─────────────────────────────────────────── -->
<div class="ot-layout">

  <!-- Controls -->
  <div class="ot-panel">
    <p class="ot-section-title">設定</p>

    <!-- outline-style -->
    <div class="ot-control-group">
      <label for="ot-style">outline-style（スタイル）</label>
      <select id="ot-style">
        <option value="solid" selected>solid（実線）</option>
        <option value="dashed">dashed（破線）</option>
        <option value="dotted">dotted（点線）</option>
        <option value="double">double（二重線）</option>
        <option value="groove">groove（溝）</option>
        <option value="ridge">ridge（隆起）</option>
        <option value="inset">inset（内側）</option>
        <option value="outset">outset（外側）</option>
      </select>
    </div>

    <!-- outline-width -->
    <div class="ot-control-group">
      <label for="ot-width">outline-width（幅）<span class="ot-val" id="ot-width-val">3px</span></label>
      <input type="range" id="ot-width" min="1" max="20" value="3" step="1">
    </div>

    <!-- outline-color -->
    <div class="ot-control-group">
      <label for="ot-color">outline-color（色）</label>
      <div class="ot-color-row">
        <input type="color" id="ot-color" value="#4f46e5">
        <input type="text" class="ot-hex-input" id="ot-hex" value="#4f46e5" maxlength="9" spellcheck="false">
      </div>
    </div>

    <!-- outline-offset -->
    <div class="ot-control-group">
      <label for="ot-offset">outline-offset（間隔）<span class="ot-val" id="ot-offset-val">3px</span></label>
      <input type="range" id="ot-offset" min="-20" max="20" value="3" step="1">
    </div>

    <!-- compare with border toggle -->
    <label class="ot-toggle-row">
      <span class="ot-toggle">
        <input type="checkbox" id="ot-compare">
        <span class="ot-toggle-track"></span>
        <span class="ot-toggle-thumb"></span>
      </span>
      border と並べて比較
    </label>

    <!-- focus state toggle -->
    <label class="ot-toggle-row">
      <span class="ot-toggle">
        <input type="checkbox" id="ot-focus-mode">
        <span class="ot-toggle-track"></span>
        <span class="ot-toggle-thumb"></span>
      </span>
      フォーカス状態をプレビュー
    </label>
  </div>

  <!-- Right column -->
  <div class="ot-right">

    <!-- Preview -->
    <div class="ot-preview-wrap">
      <p class="ot-section-title">ライブプレビュー</p>
      <div class="ot-preview-stage" id="ot-stage">
        <div>
          <div class="ot-preview-box" id="ot-box-outline">
            アウトライン
            <span class="ot-label">outline</span>
          </div>
        </div>
        <div id="ot-border-col" style="display:none">
          <div class="ot-preview-box" id="ot-box-border">
            ボーダー
            <span class="ot-label">border</span>
          </div>
        </div>
        <div id="ot-focus-col" style="display:none" class="ot-focus-demo">
          <button class="ot-focus-btn" id="ot-focus-btn">フォーカスする</button>
          <span class="ot-focus-label">Tabキーでフォーカス</span>
        </div>
      </div>
    </div>

    <!-- CSS Output -->
    <div class="ot-output-wrap">
      <div class="ot-output-header">
        <p class="ot-section-title" style="margin:0">CSSコード</p>
        <button class="ot-copy-btn" id="ot-copy-btn">
          <svg width="14" height="14" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <rect x="5" y="5" width="9" height="10" rx="1.5" stroke="currentColor" stroke-width="1.5"/>
            <path d="M3 11H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h8a1 1 0 0 1 1 1v1" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          </svg>
          CSSをコピー
        </button>
      </div>
      <pre class="ot-code" id="ot-code-out"></pre>
    </div>

    <!-- Accessibility / Focus State Output -->
    <div class="ot-a11y-wrap" id="ot-a11y-wrap">
      <div class="ot-output-header">
        <p class="ot-section-title" style="margin:0">フォーカスリング CSS（アクセシビリティ）</p>
        <button class="ot-copy-btn" id="ot-copy-a11y-btn">
          <svg width="14" height="14" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <rect x="5" y="5" width="9" height="10" rx="1.5" stroke="currentColor" stroke-width="1.5"/>
            <path d="M3 11H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h8a1 1 0 0 1 1 1v1" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          </svg>
          コピー
        </button>
      </div>
      <p class="ot-a11y-note"><code>:focus-visible</code> を使うとキーボード操作時のみフォーカスリングを表示できます（WCAG 2.4.11 推奨）。コントラスト比は隣接する色に対して最低 3:1 が必要です。</p>
      <pre class="ot-code-a11y" id="ot-a11y-out"></pre>
    </div>

    <div class="ot-info">
      <strong>ポイント：</strong><code>outline</code> はレイアウトに影響しません。<code>border</code> と異なり、周囲の要素をずらさずに要素の外側に描画されます。<code>outline-offset</code> で要素とアウトラインの間隔を調整できます。
    </div>

  </div>
</div><!-- /.ot-layout -->

<!-- ── freee CTA ─────────────────────────────────────────────── -->
<div class="ot-freee-cta" style="margin-top:24px">
  <h3>フリーランス・個人事業主の方へ — freee 会計で確定申告をかんたんに</h3>
  <p>Web制作・デザイン案件の収支管理から確定申告まで、freee なら自動仕訳と青色申告書類の自動作成でスムーズに完結します。初年度無料プランあり。</p>
  <a class="ot-freee-btn"
     href="https://px.a8.net/svt/ejp?a8mat=XXXXXXXX"
     target="_blank"
     rel="noopener sponsored"
     aria-label="freee会計 無料で始める（アフィリエイトリンク）">
    freee を無料で試す
  </a>
</div>

<script>
(function () {
  // ── State ──────────────────────────────────────────────────────────
  const state = {
    style: "solid",
    width: 3,
    color: "#4f46e5",
    offset: 3,
    compare: false,
    focusMode: false,
  };

  // ── Presets ────────────────────────────────────────────────────────
  const PRESETS = [
    { name: "フォーカスリング",  icon: "#4f46e5", style: "solid",  width: 3, color: "#4f46e5", offset: 3 },
    { name: "ダブルボーダー",    icon: "#1e40af", style: "double", width: 5, color: "#1e40af", offset: 2 },
    { name: "ネオングロー",      icon: "#22d3ee", style: "solid",  width: 3, color: "#22d3ee", offset: 4 },
    { name: "破線アクセント",    icon: "#f59e0b", style: "dashed", width: 2, color: "#f59e0b", offset: 4 },
    { name: "インセットフレーム",icon: "#6b7280", style: "inset",  width: 6, color: "#6b7280", offset: 0 },
  ];

  // ── DOM refs ───────────────────────────────────────────────────────
  const $ = (id) => document.getElementById(id);
  const elStyle      = $("ot-style");
  const elWidth      = $("ot-width");
  const elWidthVal   = $("ot-width-val");
  const elColor      = $("ot-color");
  const elHex        = $("ot-hex");
  const elOffset     = $("ot-offset");
  const elOffsetVal  = $("ot-offset-val");
  const elCompare    = $("ot-compare");
  const elFocusMode  = $("ot-focus-mode");
  const elBoxOutline = $("ot-box-outline");
  const elBoxBorder  = $("ot-box-border");
  const elBorderCol  = $("ot-border-col");
  const elFocusCol   = $("ot-focus-col");
  const elFocusBtn   = $("ot-focus-btn");
  const elCodeOut    = $("ot-code-out");
  const elA11yOut    = $("ot-a11y-out");
  const elCopyBtn    = $("ot-copy-btn");
  const elCopyA11y   = $("ot-copy-a11y-btn");
  const elPresets    = $("ot-presets");

  // ── Render presets ─────────────────────────────────────────────────
  PRESETS.forEach((p) => {
    const btn = document.createElement("button");
    btn.className = "ot-preset-btn";
    btn.innerHTML = `
      <div class="ot-preset-swatch">
        <span style="outline:${p.width}px ${p.style} ${p.color};outline-offset:${p.offset}px;width:48px;height:18px;border-radius:3px;background:#fff;display:block"></span>
      </div>
      ${p.name}
    `;
    btn.addEventListener("click", () => applyPreset(p));
    elPresets.appendChild(btn);
  });

  function applyPreset(p) {
    state.style  = p.style;
    state.width  = p.width;
    state.color  = p.color;
    state.offset = p.offset;
    syncInputs();
    render();
  }

  function syncInputs() {
    elStyle.value  = state.style;
    elWidth.value  = state.width;
    elWidthVal.textContent = state.width + "px";
    elColor.value  = state.color;
    elHex.value    = state.color;
    elOffset.value = state.offset;
    elOffsetVal.textContent = state.offset + "px";
  }

  // ── Syntax highlighter ─────────────────────────────────────────────
  function highlight(css) {
    return css
      .replace(/\/\*.*?\*\//gs, (m) => `<span class="ot-comment">${m}</span>`)
      .replace(/([.#:[\]a-zA-Z_-]+\s*(?:,\s*[.#:[\]a-zA-Z_-]+)*)\s*\{/g,
        (_, sel) => `<span class="ot-kw">${sel}</span> <span class="ot-punc">{</span>`)
      .replace(/\}/g, `<span class="ot-punc">}</span>`)
      .replace(/([\w-]+)(\s*:\s*)/g,
        (_, prop, colon) => `<span class="ot-prop">${prop}</span><span class="ot-punc">${colon}</span>`)
      .replace(/:\s*([^;<\n{]+)(;)/g,
        (_, val, semi) => `: <span class="ot-val-c">${val.trim()}</span><span class="ot-punc">;</span>`)
      ;
  }

  // ── Main render ────────────────────────────────────────────────────
  function render() {
    const { style, width, color, offset, compare, focusMode } = state;
    const outlineShorthand = `${width}px ${style} ${color}`;

    elBoxOutline.style.outline       = outlineShorthand;
    elBoxOutline.style.outlineOffset = offset + "px";

    elBorderCol.style.display = compare ? "" : "none";
    if (compare) {
      elBoxBorder.style.border  = outlineShorthand;
      elBoxBorder.style.outline = "none";
    }

    elFocusCol.style.display = focusMode ? "" : "none";
    if (focusMode) {
      elFocusBtn.style.outlineStyle  = style;
      elFocusBtn.style.outlineWidth  = width + "px";
      elFocusBtn.style.outlineColor  = color;
      elFocusBtn.style.outlineOffset = offset + "px";
    } else {
      elFocusBtn.style.outlineStyle  = "";
      elFocusBtn.style.outlineWidth  = "";
      elFocusBtn.style.outlineColor  = "";
      elFocusBtn.style.outlineOffset = "";
    }

    const cssLines = [
      `.element {`,
      `  outline-style:  ${style};`,
      `  outline-width:  ${width}px;`,
      `  outline-color:  ${color};`,
      `  outline-offset: ${offset}px;`,
      `  /* 短縮形 */`,
      `  outline: ${outlineShorthand};`,
      `}`,
    ].join("\n");
    elCodeOut.innerHTML = highlight(cssLines);

    const a11yLines = [
      `/* キーボードフォーカスリング — WCAG 2.4.11 */`,
      `.element:focus         { outline: none; }`,
      `.element:focus-visible {`,
      `  outline-style:  ${style};`,
      `  outline-width:  ${width}px;`,
      `  outline-color:  ${color};`,
      `  outline-offset: ${offset}px;`,
      `}`,
    ].join("\n");
    elA11yOut.innerHTML = highlight(a11yLines);
  }

  // ── Event listeners ────────────────────────────────────────────────
  elStyle.addEventListener("change", () => { state.style = elStyle.value; render(); });

  elWidth.addEventListener("input", () => {
    state.width = +elWidth.value;
    elWidthVal.textContent = state.width + "px";
    render();
  });

  elColor.addEventListener("input", () => {
    state.color = elColor.value;
    elHex.value = elColor.value;
    render();
  });

  elHex.addEventListener("input", () => {
    const v = elHex.value.trim();
    if (/^#[0-9a-fA-F]{6}$/.test(v) || /^#[0-9a-fA-F]{3}$/.test(v)) {
      state.color = v;
      elColor.value = v;
      render();
    }
  });

  elOffset.addEventListener("input", () => {
    state.offset = +elOffset.value;
    elOffsetVal.textContent = state.offset + "px";
    render();
  });

  elCompare.addEventListener("change", () => { state.compare = elCompare.checked; render(); });
  elFocusMode.addEventListener("change", () => { state.focusMode = elFocusMode.checked; render(); });

  // ── Copy buttons ───────────────────────────────────────────────────
  function copyText(text, btn) {
    navigator.clipboard.writeText(text).then(() => {
      const orig = btn.innerHTML;
      btn.textContent = "コピーしました!";
      btn.classList.add("copied");
      setTimeout(() => { btn.innerHTML = orig; btn.classList.remove("copied"); }, 1800);
    });
  }

  elCopyBtn.addEventListener("click", () => {
    const { style, width, color, offset } = state;
    const text = `.element {\n  outline-style:  ${style};\n  outline-width:  ${width}px;\n  outline-color:  ${color};\n  outline-offset: ${offset}px;\n  /* 短縮形 */\n  outline: ${width}px ${style} ${color};\n}`;
    copyText(text, elCopyBtn);
  });

  elCopyA11y.addEventListener("click", () => {
    const { style, width, color, offset } = state;
    const text = `/* キーボードフォーカスリング — WCAG 2.4.11 */\n.element:focus         { outline: none; }\n.element:focus-visible {\n  outline-style:  ${style};\n  outline-width:  ${width}px;\n  outline-color:  ${color};\n  outline-offset: ${offset}px;\n}`;
    copyText(text, elCopyA11y);
  });

  // ── Init ───────────────────────────────────────────────────────────
  render();
})();
</script>

</div><!-- /#ot-app -->

---

## 使い方

1. **outline-style** のドロップダウンでスタイルを選択（solid・dashed・dotted・double など）。
2. **outline-width** スライダーで太さを 1〜20px の範囲で調整。
3. **outline-color** のカラーピッカーまたは HEX 入力欄で色を設定。
4. **outline-offset** で要素とアウトラインの間隔をマイナス値（内側）〜20px の範囲で調整。
5. **border と並べて比較** を ON にすると、レイアウトへの影響の違いを並べて確認できます。
6. **フォーカス状態をプレビュー** を ON にするとボタンにアウトラインが適用され、フォーカスリングの見た目を確認できます。
7. **CSSをコピー** ボタンでコードをクリップボードにコピーして完了。

---

## outline と border の違い

| プロパティ | レイアウトに影響 | border-radius に追従 | オフセット指定 |
|---|---|---|---|
| `outline` | なし | 部分的 | あり（`outline-offset`） |
| `border` | あり | あり | なし |

`outline` はレイアウトをずらさないため、フォーカスインジケーターに最適です。コンテンツの折り返しや余白への影響なしに、要素の外側にリングを描画できます。

---

## アクセシビリティのポイント

- **WCAG 2.4.11**（WCAG 2.2 AA 基準）では、フォーカスインジケーターが隣接する色に対して最低 **3:1** のコントラスト比を持つことが求められます。
- `outline: none` を指定する場合は、必ず代替のフォーカス表示を提供してください。
- `:focus-visible` を使うと、マウス操作ではなくキーボード操作時のみフォーカスリングを表示できます。
- `outline-offset: 2〜4px` を設定すると、角丸要素でも視認性が向上します。

---

## 関連ツール

- [CSS ボーダーラジアス ジェネレーター](/tools/css-border-radius-generator/)
- [CSS ボックスシャドウ ジェネレーター](/tools/css-box-shadow-generator/)
- [CSS ボタン ジェネレーター](/tools/css-button-generator/)

---

<small>※ freee へのリンクはアフィリエイトリンクを含む場合があります。</small>

<!-- ── A8 footer ──────────────────────────────────────────────── -->
<!-- a8sales footer script placeholder -->
<div style="font-size:11px;color:#9ca3af;margin-top:16px;line-height:1.5">
  本ページにはアフィリエイト広告（A8.net）が含まれています。
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

