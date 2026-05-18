---
title: "Unicode文字マップ — 記号検索ツール"
date: 2025-12-26
description: "Unicode文字を閲覧・検索。矢印・数学記号・通貨記号・特殊文字を探す。文字・コードポイント・HTMLエンティティをコピー。"
categories: ["無料ツール"]
slug: "unicode-character-map"
ShowToc: false
cover:
  image: "/images/covers/unicode-character-map-ja.png"
  alt: "Unicode文字マップ"
---

Unicode文字セットを閲覧・検索できるツールです。カテゴリを選ぶか文字名を入力し、気になる文字をクリックするとコードポイント・HTMLエンティティ・CSS値・UTF-8バイト列をコピーできます。

<div id="umap-app">

<style>
/* ── スコープ付きスタイル: すべてのルールを #umap-app でプレフィックス ── */
#umap-app {
  font-family: system-ui, -apple-system, "Helvetica Neue", sans-serif;
  max-width: 960px;
  margin: 0 auto;
  color: #1a1a1a;
}
#umap-app *,
#umap-app *::before,
#umap-app *::after {
  box-sizing: border-box;
}

/* コントロール */
#umap-app .umap-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 18px;
}
#umap-app .umap-search {
  flex: 1 1 220px;
  padding: 10px 14px;
  font-size: 1rem;
  border: 2px solid #d1d5db;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.2s;
}
#umap-app .umap-search:focus {
  border-color: #6366f1;
}
#umap-app .umap-category-wrap {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
}
#umap-app .umap-cat-btn {
  padding: 7px 14px;
  font-size: 0.85rem;
  border: 2px solid #d1d5db;
  border-radius: 20px;
  background: #fff;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s, color 0.15s;
  white-space: nowrap;
}
#umap-app .umap-cat-btn:hover {
  border-color: #6366f1;
  color: #6366f1;
}
#umap-app .umap-cat-btn.active {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}

/* ステータスバー */
#umap-app .umap-status {
  font-size: 0.82rem;
  color: #6b7280;
  margin-bottom: 12px;
  min-height: 1.2em;
}

/* グリッド */
#umap-app .umap-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(72px, 1fr));
  gap: 8px;
  margin-bottom: 24px;
}
#umap-app .umap-cell {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 10px 4px 6px;
  border: 1.5px solid #e5e7eb;
  border-radius: 8px;
  cursor: pointer;
  background: #fafafa;
  transition: border-color 0.15s, background 0.15s, transform 0.1s;
  min-height: 72px;
  position: relative;
  user-select: none;
}
#umap-app .umap-cell:hover {
  border-color: #6366f1;
  background: #eef2ff;
  transform: translateY(-2px);
}
#umap-app .umap-cell:active {
  transform: translateY(0);
}
#umap-app .umap-cell.copied {
  border-color: #10b981;
  background: #d1fae5;
}
#umap-app .umap-glyph {
  font-size: 1.6rem;
  line-height: 1;
  margin-bottom: 4px;
}
#umap-app .umap-cp {
  font-size: 0.62rem;
  color: #9ca3af;
  font-family: monospace;
}

/* 詳細パネル */
#umap-app .umap-detail {
  display: none;
  border: 2px solid #6366f1;
  border-radius: 12px;
  padding: 20px 24px;
  background: #f5f3ff;
  margin-bottom: 24px;
  position: relative;
}
#umap-app .umap-detail.visible {
  display: block;
}
#umap-app .umap-detail-close {
  position: absolute;
  top: 12px;
  right: 14px;
  background: none;
  border: none;
  font-size: 1.2rem;
  cursor: pointer;
  color: #6b7280;
  line-height: 1;
}
#umap-app .umap-detail-glyph {
  font-size: 3.5rem;
  line-height: 1;
  margin-bottom: 12px;
}
#umap-app .umap-detail-name {
  font-weight: 700;
  font-size: 1rem;
  margin-bottom: 14px;
  color: #374151;
}
#umap-app .umap-detail-rows {
  display: grid;
  grid-template-columns: auto 1fr auto;
  gap: 10px 16px;
  align-items: center;
}
#umap-app .umap-detail-label {
  font-size: 0.8rem;
  color: #6b7280;
  white-space: nowrap;
}
#umap-app .umap-detail-value {
  font-family: monospace;
  font-size: 0.92rem;
  color: #1a1a1a;
  word-break: break-all;
}
#umap-app .umap-copy-btn {
  padding: 4px 12px;
  font-size: 0.78rem;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
}
#umap-app .umap-copy-btn:hover {
  background: #4f46e5;
}
#umap-app .umap-copy-btn.ok {
  background: #10b981;
}

/* トースト通知 */
#umap-app .umap-toast {
  position: fixed;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #1f2937;
  color: #fff;
  padding: 10px 22px;
  border-radius: 24px;
  font-size: 0.9rem;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s, transform 0.25s;
  z-index: 9999;
  white-space: nowrap;
}
#umap-app .umap-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

/* 結果なし */
#umap-app .umap-empty {
  text-align: center;
  color: #9ca3af;
  padding: 48px 0;
  font-size: 1rem;
}

/* 関連リンク */
#umap-app .umap-related {
  border-top: 1px solid #e5e7eb;
  padding-top: 18px;
  margin-top: 8px;
  font-size: 0.88rem;
  color: #6b7280;
}
#umap-app .umap-related a {
  color: #6366f1;
  text-decoration: none;
  margin-right: 14px;
}
#umap-app .umap-related a:hover {
  text-decoration: underline;
}

/* freee CTA */
#umap-app .umap-cta {
  margin-top: 32px;
  padding: 20px 24px;
  background: linear-gradient(135deg, #e0e7ff 0%, #f0fdf4 100%);
  border: 1px solid #c7d2fe;
  border-radius: 12px;
  font-size: 0.9rem;
  color: #374151;
  line-height: 1.6;
}
#umap-app .umap-cta strong {
  color: #4338ca;
}
#umap-app .umap-cta a.umap-cta-link {
  display: inline-block;
  margin-top: 10px;
  padding: 8px 20px;
  background: #4338ca;
  color: #fff;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.88rem;
  transition: background 0.15s;
}
#umap-app .umap-cta a.umap-cta-link:hover {
  background: #3730a3;
}

/* モバイル */
@media (max-width: 600px) {
  #umap-app .umap-grid {
    grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
    gap: 6px;
  }
  #umap-app .umap-glyph {
    font-size: 1.3rem;
  }
  #umap-app .umap-detail-rows {
    grid-template-columns: auto 1fr;
  }
  #umap-app .umap-copy-btn {
    grid-column: 1 / -1;
  }
  #umap-app .umap-detail-glyph {
    font-size: 2.5rem;
  }
}
</style>

<div class="umap-controls">
  <input
    class="umap-search"
    id="umap-search"
    type="search"
    placeholder="文字名またはコードポイントで検索（例: arrow、U+2192）"
    autocomplete="off"
  />
</div>
<div class="umap-controls" style="margin-top:-4px">
  <div class="umap-category-wrap" id="umap-cats"></div>
</div>

<div class="umap-status" id="umap-status"></div>

<div class="umap-detail" id="umap-detail">
  <button class="umap-detail-close" id="umap-detail-close" title="閉じる">&#x2715;</button>
  <div class="umap-detail-glyph" id="umap-dg"></div>
  <div class="umap-detail-name" id="umap-dn"></div>
  <div class="umap-detail-rows" id="umap-dr"></div>
</div>

<div class="umap-grid" id="umap-grid"></div>
<div class="umap-toast" id="umap-toast"></div>

<div class="umap-related">
  関連ツール:
  <a href="/tools/html-entity-encoder/">HTMLエンティティエンコーダー</a>
  <a href="/tools/emoji-picker/">絵文字ピッカー</a>
  <a href="/tools/morse-code-translator/">モールス信号変換</a>
</div>

<div class="umap-cta">
  <strong>事業の帳簿・請求書管理もスムーズに</strong><br>
  freee会計なら、売上・経費の記録から確定申告・決算書の作成まで、クラウドで一括管理。
  銀行口座・クレジットカードと自動連携し、入力の手間を大幅に削減できます。
  <br>
  <a class="umap-cta-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">
    freee会計を無料で試す &rarr;
  </a>
</div>

<script>
(function () {
  "use strict";

  /* ── 文字データ ── */
  var CATS = [
    {
      id: "arrows",
      label: "矢印",
      chars: [
        [0x2190, "LEFTWARDS ARROW"],
        [0x2191, "UPWARDS ARROW"],
        [0x2192, "RIGHTWARDS ARROW"],
        [0x2193, "DOWNWARDS ARROW"],
        [0x2194, "LEFT RIGHT ARROW"],
        [0x2195, "UP DOWN ARROW"],
        [0x2196, "NORTH WEST ARROW"],
        [0x2197, "NORTH EAST ARROW"],
        [0x2198, "SOUTH EAST ARROW"],
        [0x2199, "SOUTH WEST ARROW"],
        [0x219a, "LEFTWARDS ARROW WITH STROKE"],
        [0x219b, "RIGHTWARDS ARROW WITH STROKE"],
        [0x219c, "LEFTWARDS WAVE ARROW"],
        [0x219d, "RIGHTWARDS WAVE ARROW"],
        [0x219e, "LEFTWARDS TWO HEADED ARROW"],
        [0x21a0, "RIGHTWARDS TWO HEADED ARROW"],
        [0x21a2, "LEFTWARDS ARROW WITH TAIL"],
        [0x21a3, "RIGHTWARDS ARROW WITH TAIL"],
        [0x21a6, "RIGHTWARDS ARROW FROM BAR"],
        [0x21a9, "LEFTWARDS ARROW WITH HOOK"],
        [0x21aa, "RIGHTWARDS ARROW WITH HOOK"],
        [0x21b0, "UPWARDS ARROW WITH TIP LEFTWARDS"],
        [0x21b1, "UPWARDS ARROW WITH TIP RIGHTWARDS"],
        [0x21b2, "DOWNWARDS ARROW WITH TIP LEFTWARDS"],
        [0x21b3, "DOWNWARDS ARROW WITH TIP RIGHTWARDS"],
        [0x21b4, "RIGHTWARDS ARROW WITH CORNER DOWNWARDS"],
        [0x21b5, "DOWNWARDS ARROW WITH CORNER LEFTWARDS"],
        [0x21b6, "ANTICLOCKWISE TOP SEMICIRCLE ARROW"],
        [0x21b7, "CLOCKWISE TOP SEMICIRCLE ARROW"],
        [0x21ba, "ANTICLOCKWISE OPEN CIRCLE ARROW"],
        [0x21bb, "CLOCKWISE OPEN CIRCLE ARROW"],
        [0x21bc, "LEFTWARDS HARPOON WITH BARB UPWARDS"],
        [0x21c0, "RIGHTWARDS HARPOON WITH BARB UPWARDS"],
        [0x21c4, "RIGHTWARDS ARROW OVER LEFTWARDS ARROW"],
        [0x21c6, "LEFTWARDS ARROW OVER RIGHTWARDS ARROW"],
        [0x21c7, "LEFTWARDS PAIRED ARROWS"],
        [0x21c8, "UPWARDS PAIRED ARROWS"],
        [0x21c9, "RIGHTWARDS PAIRED ARROWS"],
        [0x21ca, "DOWNWARDS PAIRED ARROWS"],
        [0x21cb, "LEFTWARDS HARPOON OVER RIGHTWARDS HARPOON"],
        [0x21cc, "RIGHTWARDS HARPOON OVER LEFTWARDS HARPOON"],
        [0x21cd, "LEFTWARDS DOUBLE ARROW WITH STROKE"],
        [0x21ce, "LEFT RIGHT DOUBLE ARROW WITH STROKE"],
        [0x21cf, "RIGHTWARDS DOUBLE ARROW WITH STROKE"],
        [0x21d0, "LEFTWARDS DOUBLE ARROW"],
        [0x21d1, "UPWARDS DOUBLE ARROW"],
        [0x21d2, "RIGHTWARDS DOUBLE ARROW"],
        [0x21d3, "DOWNWARDS DOUBLE ARROW"],
        [0x21d4, "LEFT RIGHT DOUBLE ARROW"],
        [0x21d5, "UP DOWN DOUBLE ARROW"],
        [0x21e6, "LEFTWARDS WHITE ARROW"],
        [0x21e7, "UPWARDS WHITE ARROW"],
        [0x21e8, "RIGHTWARDS WHITE ARROW"],
        [0x21e9, "DOWNWARDS WHITE ARROW"],
        [0x27a1, "BLACK RIGHTWARDS ARROW"],
        [0x2b05, "LEFTWARDS BLACK ARROW"],
        [0x2b06, "UPWARDS BLACK ARROW"],
        [0x2b07, "DOWNWARDS BLACK ARROW"],
        [0x2b95, "RIGHTWARDS BLACK ARROW"],
      ],
    },
    {
      id: "math",
      label: "数学",
      chars: [
        [0x00b1, "PLUS-MINUS SIGN"],
        [0x00d7, "MULTIPLICATION SIGN"],
        [0x00f7, "DIVISION SIGN"],
        [0x2200, "FOR ALL"],
        [0x2202, "PARTIAL DIFFERENTIAL"],
        [0x2203, "THERE EXISTS"],
        [0x2204, "THERE DOES NOT EXIST"],
        [0x2205, "EMPTY SET"],
        [0x2207, "NABLA"],
        [0x2208, "ELEMENT OF"],
        [0x2209, "NOT AN ELEMENT OF"],
        [0x220b, "CONTAINS AS MEMBER"],
        [0x220f, "N-ARY PRODUCT"],
        [0x2211, "N-ARY SUMMATION"],
        [0x2212, "MINUS SIGN"],
        [0x2213, "MINUS-OR-PLUS SIGN"],
        [0x2217, "ASTERISK OPERATOR"],
        [0x221a, "SQUARE ROOT"],
        [0x221b, "CUBE ROOT"],
        [0x221c, "FOURTH ROOT"],
        [0x221e, "INFINITY"],
        [0x2220, "ANGLE"],
        [0x2221, "MEASURED ANGLE"],
        [0x2222, "SPHERICAL ANGLE"],
        [0x2223, "DIVIDES"],
        [0x2225, "PARALLEL TO"],
        [0x2227, "LOGICAL AND"],
        [0x2228, "LOGICAL OR"],
        [0x2229, "INTERSECTION"],
        [0x222a, "UNION"],
        [0x222b, "INTEGRAL"],
        [0x222c, "DOUBLE INTEGRAL"],
        [0x222d, "TRIPLE INTEGRAL"],
        [0x2236, "RATIO"],
        [0x2237, "PROPORTION"],
        [0x223c, "TILDE OPERATOR"],
        [0x2243, "ASYMPTOTICALLY EQUAL TO"],
        [0x2245, "APPROXIMATELY EQUAL TO"],
        [0x2248, "ALMOST EQUAL TO"],
        [0x2249, "NOT ALMOST EQUAL TO"],
        [0x2260, "NOT EQUAL TO"],
        [0x2261, "IDENTICAL TO"],
        [0x2262, "NOT IDENTICAL TO"],
        [0x2264, "LESS-THAN OR EQUAL TO"],
        [0x2265, "GREATER-THAN OR EQUAL TO"],
        [0x226a, "MUCH LESS-THAN"],
        [0x226b, "MUCH GREATER-THAN"],
        [0x2282, "SUBSET OF"],
        [0x2283, "SUPERSET OF"],
        [0x2284, "NOT A SUBSET OF"],
        [0x2286, "SUBSET OF OR EQUAL TO"],
        [0x2287, "SUPERSET OF OR EQUAL TO"],
        [0x2295, "CIRCLED PLUS"],
        [0x2297, "CIRCLED TIMES"],
        [0x22c5, "DOT OPERATOR"],
        [0x25b3, "WHITE UP-POINTING TRIANGLE"],
        [0x03c0, "GREEK SMALL LETTER PI"],
        [0x03b1, "GREEK SMALL LETTER ALPHA"],
        [0x03b2, "GREEK SMALL LETTER BETA"],
        [0x03b3, "GREEK SMALL LETTER GAMMA"],
      ],
    },
    {
      id: "currency",
      label: "通貨",
      chars: [
        [0x0024, "DOLLAR SIGN"],
        [0x00a2, "CENT SIGN"],
        [0x00a3, "POUND SIGN"],
        [0x00a4, "CURRENCY SIGN"],
        [0x00a5, "YEN SIGN"],
        [0x20a0, "EURO-CURRENCY SIGN"],
        [0x20a1, "COLON SIGN"],
        [0x20a2, "CRUZEIRO SIGN"],
        [0x20a3, "FRENCH FRANC SIGN"],
        [0x20a4, "LIRA SIGN"],
        [0x20a6, "NAIRA SIGN"],
        [0x20a7, "PESETA SIGN"],
        [0x20a8, "RUPEE SIGN"],
        [0x20a9, "WON SIGN"],
        [0x20aa, "NEW SHEQEL SIGN"],
        [0x20ab, "DONG SIGN"],
        [0x20ac, "EURO SIGN"],
        [0x20ad, "KIP SIGN"],
        [0x20ae, "TUGRIK SIGN"],
        [0x20af, "DRACHMA SIGN"],
        [0x20b0, "GERMAN PENNY SIGN"],
        [0x20b1, "PESO SIGN"],
        [0x20b2, "GUARANI SIGN"],
        [0x20b3, "AUSTRAL SIGN"],
        [0x20b4, "HRYVNIA SIGN"],
        [0x20b5, "CEDI SIGN"],
        [0x20b6, "LIVRE TOURNOIS SIGN"],
        [0x20b8, "TENGE SIGN"],
        [0x20b9, "INDIAN RUPEE SIGN"],
        [0x20ba, "TURKISH LIRA SIGN"],
        [0x20bb, "NORDIC MARK SIGN"],
        [0x20bc, "MANAT SIGN"],
        [0x20bd, "RUBLE SIGN"],
        [0x20be, "LARI SIGN"],
        [0x20bf, "BITCOIN SIGN"],
        [0x09f3, "BENGALI RUPEE SIGN"],
        [0x0af1, "GUJARATI RUPEE SIGN"],
        [0x0bf9, "TAMIL RUPEE SIGN"],
      ],
    },
    {
      id: "symbols",
      label: "記号",
      chars: [
        [0x00a9, "COPYRIGHT SIGN"],
        [0x00ae, "REGISTERED SIGN"],
        [0x2122, "TRADE MARK SIGN"],
        [0x00b0, "DEGREE SIGN"],
        [0x00b5, "MICRO SIGN"],
        [0x00b6, "PILCROW SIGN"],
        [0x00a7, "SECTION SIGN"],
        [0x2020, "DAGGER"],
        [0x2021, "DOUBLE DAGGER"],
        [0x2022, "BULLET"],
        [0x2023, "TRIANGULAR BULLET"],
        [0x2026, "HORIZONTAL ELLIPSIS"],
        [0x2030, "PER MILLE SIGN"],
        [0x2031, "PER TEN THOUSAND SIGN"],
        [0x2032, "PRIME"],
        [0x2033, "DOUBLE PRIME"],
        [0x2034, "TRIPLE PRIME"],
        [0x2035, "REVERSED PRIME"],
        [0x203b, "REFERENCE MARK"],
        [0x203c, "DOUBLE EXCLAMATION MARK"],
        [0x203d, "INTERROBANG"],
        [0x2047, "DOUBLE QUESTION MARK"],
        [0x2048, "QUESTION EXCLAMATION MARK"],
        [0x2049, "EXCLAMATION QUESTION MARK"],
        [0x2116, "NUMERO SIGN"],
        [0x211e, "PRESCRIPTION TAKE"],
        [0x2120, "SERVICE MARK"],
        [0x2126, "OHM SIGN"],
        [0x212b, "ANGSTROM SIGN"],
        [0x2139, "INFORMATION SOURCE"],
        [0x231a, "WATCH"],
        [0x231b, "HOURGLASS"],
        [0x2328, "KEYBOARD"],
        [0x23ce, "RETURN SYMBOL"],
        [0x23f0, "ALARM CLOCK"],
        [0x23f3, "HOURGLASS WITH FLOWING SAND"],
        [0x2602, "UMBRELLA"],
        [0x2603, "SNOWMAN"],
        [0x2604, "COMET"],
        [0x260e, "BLACK TELEPHONE"],
        [0x2615, "HOT BEVERAGE"],
        [0x2620, "SKULL AND CROSSBONES"],
        [0x2622, "RADIOACTIVE SIGN"],
        [0x2623, "BIOHAZARD SIGN"],
        [0x262e, "PEACE SYMBOL"],
        [0x262f, "YIN YANG"],
        [0x2639, "WHITE FROWNING FACE"],
        [0x263a, "WHITE SMILING FACE"],
        [0x2640, "FEMALE SIGN"],
        [0x2642, "MALE SIGN"],
        [0x2660, "BLACK SPADE SUIT"],
        [0x2663, "BLACK CLUB SUIT"],
        [0x2665, "BLACK HEART SUIT"],
        [0x2666, "BLACK DIAMOND SUIT"],
        [0x2713, "CHECK MARK"],
        [0x2714, "HEAVY CHECK MARK"],
        [0x2715, "MULTIPLICATION X"],
        [0x2716, "HEAVY MULTIPLICATION X"],
      ],
    },
    {
      id: "dingbats",
      label: "装飾記号",
      chars: [
        [0x2701, "UPPER BLADE SCISSORS"],
        [0x2702, "BLACK SCISSORS"],
        [0x2703, "LOWER BLADE SCISSORS"],
        [0x2704, "WHITE SCISSORS"],
        [0x2706, "TELEPHONE LOCATION SIGN"],
        [0x2708, "AIRPLANE"],
        [0x2709, "ENVELOPE"],
        [0x270a, "RAISED FIST"],
        [0x270b, "RAISED HAND"],
        [0x270c, "VICTORY HAND"],
        [0x270d, "WRITING HAND"],
        [0x270e, "LOWER RIGHT PENCIL"],
        [0x270f, "PENCIL"],
        [0x2710, "UPPER RIGHT PENCIL"],
        [0x2711, "WHITE NIB"],
        [0x2712, "BLACK NIB"],
        [0x2713, "CHECK MARK"],
        [0x2714, "HEAVY CHECK MARK"],
        [0x2715, "MULTIPLICATION X"],
        [0x2716, "HEAVY MULTIPLICATION X"],
        [0x2717, "BALLOT X"],
        [0x2718, "HEAVY BALLOT X"],
        [0x271a, "HEAVY GREEK CROSS"],
        [0x271b, "OPEN CENTRE CROSS"],
        [0x2720, "MALTESE CROSS"],
        [0x2721, "STAR OF DAVID"],
        [0x2726, "BLACK FOUR POINTED STAR"],
        [0x2727, "WHITE FOUR POINTED STAR"],
        [0x2728, "SPARKLES"],
        [0x2729, "STRESS OUTLINED WHITE STAR"],
        [0x272a, "CIRCLED WHITE STAR"],
        [0x272b, "OPEN CENTRE BLACK STAR"],
        [0x272c, "BLACK CENTRE WHITE STAR"],
        [0x272d, "OUTLINED BLACK STAR"],
        [0x272f, "PINWHEEL STAR"],
        [0x2730, "SHADOWED WHITE STAR"],
        [0x2731, "HEAVY ASTERISK"],
        [0x2732, "OPEN CENTRE ASTERISK"],
        [0x2733, "EIGHT SPOKED ASTERISK"],
        [0x2734, "EIGHT POINTED BLACK STAR"],
        [0x2736, "SIX POINTED BLACK STAR"],
        [0x2739, "TWELVE POINTED BLACK STAR"],
        [0x273a, "SIXTEEN POINTED ASTERISK"],
        [0x273f, "BLACK FLORETTE"],
        [0x2740, "WHITE FLORETTE"],
        [0x2744, "SNOWFLAKE"],
        [0x2762, "HEAVY EXCLAMATION MARK ORNAMENT"],
        [0x2763, "HEAVY HEART EXCLAMATION MARK ORNAMENT"],
        [0x2764, "HEAVY BLACK HEART"],
        [0x2765, "ROTATED HEAVY BLACK HEART BULLET"],
        [0x2767, "ROTATED FLORAL HEART BULLET"],
      ],
    },
    {
      id: "box",
      label: "罫線",
      chars: [
        [0x2500, "BOX DRAWINGS LIGHT HORIZONTAL"],
        [0x2501, "BOX DRAWINGS HEAVY HORIZONTAL"],
        [0x2502, "BOX DRAWINGS LIGHT VERTICAL"],
        [0x2503, "BOX DRAWINGS HEAVY VERTICAL"],
        [0x2504, "BOX DRAWINGS LIGHT TRIPLE DASH HORIZONTAL"],
        [0x2505, "BOX DRAWINGS HEAVY TRIPLE DASH HORIZONTAL"],
        [0x2506, "BOX DRAWINGS LIGHT TRIPLE DASH VERTICAL"],
        [0x2507, "BOX DRAWINGS HEAVY TRIPLE DASH VERTICAL"],
        [0x2508, "BOX DRAWINGS LIGHT QUADRUPLE DASH HORIZONTAL"],
        [0x2509, "BOX DRAWINGS HEAVY QUADRUPLE DASH HORIZONTAL"],
        [0x250c, "BOX DRAWINGS LIGHT DOWN AND RIGHT"],
        [0x250d, "BOX DRAWINGS DOWN LIGHT AND RIGHT HEAVY"],
        [0x250e, "BOX DRAWINGS DOWN HEAVY AND RIGHT LIGHT"],
        [0x250f, "BOX DRAWINGS HEAVY DOWN AND RIGHT"],
        [0x2510, "BOX DRAWINGS LIGHT DOWN AND LEFT"],
        [0x2511, "BOX DRAWINGS DOWN LIGHT AND LEFT HEAVY"],
        [0x2512, "BOX DRAWINGS DOWN HEAVY AND LEFT LIGHT"],
        [0x2513, "BOX DRAWINGS HEAVY DOWN AND LEFT"],
        [0x2514, "BOX DRAWINGS LIGHT UP AND RIGHT"],
        [0x2515, "BOX DRAWINGS UP LIGHT AND RIGHT HEAVY"],
        [0x2516, "BOX DRAWINGS UP HEAVY AND RIGHT LIGHT"],
        [0x2517, "BOX DRAWINGS HEAVY UP AND RIGHT"],
        [0x2518, "BOX DRAWINGS LIGHT UP AND LEFT"],
        [0x2519, "BOX DRAWINGS UP LIGHT AND LEFT HEAVY"],
        [0x251a, "BOX DRAWINGS UP HEAVY AND LEFT LIGHT"],
        [0x251b, "BOX DRAWINGS HEAVY UP AND LEFT"],
        [0x251c, "BOX DRAWINGS LIGHT VERTICAL AND RIGHT"],
        [0x251d, "BOX DRAWINGS VERTICAL LIGHT AND RIGHT HEAVY"],
        [0x2520, "BOX DRAWINGS VERTICAL HEAVY AND RIGHT LIGHT"],
        [0x2523, "BOX DRAWINGS HEAVY VERTICAL AND RIGHT"],
        [0x2524, "BOX DRAWINGS LIGHT VERTICAL AND LEFT"],
        [0x252c, "BOX DRAWINGS LIGHT DOWN AND HORIZONTAL"],
        [0x2534, "BOX DRAWINGS LIGHT UP AND HORIZONTAL"],
        [0x253c, "BOX DRAWINGS LIGHT VERTICAL AND HORIZONTAL"],
        [0x2550, "BOX DRAWINGS DOUBLE HORIZONTAL"],
        [0x2551, "BOX DRAWINGS DOUBLE VERTICAL"],
        [0x2554, "BOX DRAWINGS DOUBLE DOWN AND RIGHT"],
        [0x2557, "BOX DRAWINGS DOUBLE DOWN AND LEFT"],
        [0x255a, "BOX DRAWINGS DOUBLE UP AND RIGHT"],
        [0x255d, "BOX DRAWINGS DOUBLE UP AND LEFT"],
        [0x256c, "BOX DRAWINGS DOUBLE VERTICAL AND HORIZONTAL"],
        [0x2580, "UPPER HALF BLOCK"],
        [0x2584, "LOWER HALF BLOCK"],
        [0x2588, "FULL BLOCK"],
        [0x258c, "LEFT HALF BLOCK"],
        [0x2590, "RIGHT HALF BLOCK"],
        [0x2591, "LIGHT SHADE"],
        [0x2592, "MEDIUM SHADE"],
        [0x2593, "DARK SHADE"],
        [0x25a0, "BLACK SQUARE"],
        [0x25a1, "WHITE SQUARE"],
        [0x25aa, "BLACK SMALL SQUARE"],
        [0x25ab, "WHITE SMALL SQUARE"],
        [0x25b2, "BLACK UP-POINTING TRIANGLE"],
        [0x25b6, "BLACK RIGHT-POINTING TRIANGLE"],
        [0x25bc, "BLACK DOWN-POINTING TRIANGLE"],
        [0x25c0, "BLACK LEFT-POINTING TRIANGLE"],
        [0x25c6, "BLACK DIAMOND"],
        [0x25c7, "WHITE DIAMOND"],
        [0x25cf, "BLACK CIRCLE"],
        [0x25d8, "INVERSE BULLET"],
        [0x25e6, "WHITE BULLET"],
      ],
    },
    {
      id: "greek",
      label: "ギリシャ文字",
      chars: [
        [0x0391, "GREEK CAPITAL LETTER ALPHA"],
        [0x0392, "GREEK CAPITAL LETTER BETA"],
        [0x0393, "GREEK CAPITAL LETTER GAMMA"],
        [0x0394, "GREEK CAPITAL LETTER DELTA"],
        [0x0395, "GREEK CAPITAL LETTER EPSILON"],
        [0x0396, "GREEK CAPITAL LETTER ZETA"],
        [0x0397, "GREEK CAPITAL LETTER ETA"],
        [0x0398, "GREEK CAPITAL LETTER THETA"],
        [0x0399, "GREEK CAPITAL LETTER IOTA"],
        [0x039a, "GREEK CAPITAL LETTER KAPPA"],
        [0x039b, "GREEK CAPITAL LETTER LAMDA"],
        [0x039c, "GREEK CAPITAL LETTER MU"],
        [0x039d, "GREEK CAPITAL LETTER NU"],
        [0x039e, "GREEK CAPITAL LETTER XI"],
        [0x039f, "GREEK CAPITAL LETTER OMICRON"],
        [0x03a0, "GREEK CAPITAL LETTER PI"],
        [0x03a1, "GREEK CAPITAL LETTER RHO"],
        [0x03a3, "GREEK CAPITAL LETTER SIGMA"],
        [0x03a4, "GREEK CAPITAL LETTER TAU"],
        [0x03a5, "GREEK CAPITAL LETTER UPSILON"],
        [0x03a6, "GREEK CAPITAL LETTER PHI"],
        [0x03a7, "GREEK CAPITAL LETTER CHI"],
        [0x03a8, "GREEK CAPITAL LETTER PSI"],
        [0x03a9, "GREEK CAPITAL LETTER OMEGA"],
        [0x03b1, "GREEK SMALL LETTER ALPHA"],
        [0x03b2, "GREEK SMALL LETTER BETA"],
        [0x03b3, "GREEK SMALL LETTER GAMMA"],
        [0x03b4, "GREEK SMALL LETTER DELTA"],
        [0x03b5, "GREEK SMALL LETTER EPSILON"],
        [0x03b6, "GREEK SMALL LETTER ZETA"],
        [0x03b7, "GREEK SMALL LETTER ETA"],
        [0x03b8, "GREEK SMALL LETTER THETA"],
        [0x03b9, "GREEK SMALL LETTER IOTA"],
        [0x03ba, "GREEK SMALL LETTER KAPPA"],
        [0x03bb, "GREEK SMALL LETTER LAMDA"],
        [0x03bc, "GREEK SMALL LETTER MU"],
        [0x03bd, "GREEK SMALL LETTER NU"],
        [0x03be, "GREEK SMALL LETTER XI"],
        [0x03bf, "GREEK SMALL LETTER OMICRON"],
        [0x03c0, "GREEK SMALL LETTER PI"],
        [0x03c1, "GREEK SMALL LETTER RHO"],
        [0x03c3, "GREEK SMALL LETTER SIGMA"],
        [0x03c4, "GREEK SMALL LETTER TAU"],
        [0x03c5, "GREEK SMALL LETTER UPSILON"],
        [0x03c6, "GREEK SMALL LETTER PHI"],
        [0x03c7, "GREEK SMALL LETTER CHI"],
        [0x03c8, "GREEK SMALL LETTER PSI"],
        [0x03c9, "GREEK SMALL LETTER OMEGA"],
      ],
    },
    {
      id: "cyrillic",
      label: "キリル文字",
      chars: [
        [0x0410, "CYRILLIC CAPITAL LETTER A"],
        [0x0411, "CYRILLIC CAPITAL LETTER BE"],
        [0x0412, "CYRILLIC CAPITAL LETTER VE"],
        [0x0413, "CYRILLIC CAPITAL LETTER GHE"],
        [0x0414, "CYRILLIC CAPITAL LETTER DE"],
        [0x0415, "CYRILLIC CAPITAL LETTER IE"],
        [0x0416, "CYRILLIC CAPITAL LETTER ZHE"],
        [0x0417, "CYRILLIC CAPITAL LETTER ZE"],
        [0x0418, "CYRILLIC CAPITAL LETTER I"],
        [0x0419, "CYRILLIC CAPITAL LETTER SHORT I"],
        [0x041a, "CYRILLIC CAPITAL LETTER KA"],
        [0x041b, "CYRILLIC CAPITAL LETTER EL"],
        [0x041c, "CYRILLIC CAPITAL LETTER EM"],
        [0x041d, "CYRILLIC CAPITAL LETTER EN"],
        [0x041e, "CYRILLIC CAPITAL LETTER O"],
        [0x041f, "CYRILLIC CAPITAL LETTER PE"],
        [0x0420, "CYRILLIC CAPITAL LETTER ER"],
        [0x0421, "CYRILLIC CAPITAL LETTER ES"],
        [0x0422, "CYRILLIC CAPITAL LETTER TE"],
        [0x0423, "CYRILLIC CAPITAL LETTER U"],
        [0x0424, "CYRILLIC CAPITAL LETTER EF"],
        [0x0425, "CYRILLIC CAPITAL LETTER HA"],
        [0x0426, "CYRILLIC CAPITAL LETTER TSE"],
        [0x0427, "CYRILLIC CAPITAL LETTER CHE"],
        [0x0428, "CYRILLIC CAPITAL LETTER SHA"],
        [0x0429, "CYRILLIC CAPITAL LETTER SHCHA"],
        [0x042a, "CYRILLIC CAPITAL LETTER HARD SIGN"],
        [0x042b, "CYRILLIC CAPITAL LETTER YERU"],
        [0x042c, "CYRILLIC CAPITAL LETTER SOFT SIGN"],
        [0x042d, "CYRILLIC CAPITAL LETTER E"],
        [0x042e, "CYRILLIC CAPITAL LETTER YU"],
        [0x042f, "CYRILLIC CAPITAL LETTER YA"],
        [0x0430, "CYRILLIC SMALL LETTER A"],
        [0x0431, "CYRILLIC SMALL LETTER BE"],
        [0x0432, "CYRILLIC SMALL LETTER VE"],
        [0x0433, "CYRILLIC SMALL LETTER GHE"],
        [0x0434, "CYRILLIC SMALL LETTER DE"],
        [0x0435, "CYRILLIC SMALL LETTER IE"],
        [0x0436, "CYRILLIC SMALL LETTER ZHE"],
        [0x0437, "CYRILLIC SMALL LETTER ZE"],
        [0x0438, "CYRILLIC SMALL LETTER I"],
        [0x0439, "CYRILLIC SMALL LETTER SHORT I"],
        [0x043a, "CYRILLIC SMALL LETTER KA"],
        [0x043b, "CYRILLIC SMALL LETTER EL"],
        [0x043c, "CYRILLIC SMALL LETTER EM"],
        [0x043d, "CYRILLIC SMALL LETTER EN"],
        [0x043e, "CYRILLIC SMALL LETTER O"],
        [0x043f, "CYRILLIC SMALL LETTER PE"],
        [0x0440, "CYRILLIC SMALL LETTER ER"],
        [0x0441, "CYRILLIC SMALL LETTER ES"],
        [0x0442, "CYRILLIC SMALL LETTER TE"],
        [0x0443, "CYRILLIC SMALL LETTER U"],
        [0x0444, "CYRILLIC SMALL LETTER EF"],
        [0x0445, "CYRILLIC SMALL LETTER HA"],
        [0x0446, "CYRILLIC SMALL LETTER TSE"],
        [0x0447, "CYRILLIC SMALL LETTER CHE"],
        [0x0448, "CYRILLIC SMALL LETTER SHA"],
        [0x0449, "CYRILLIC SMALL LETTER SHCHA"],
        [0x044a, "CYRILLIC SMALL LETTER HARD SIGN"],
        [0x044b, "CYRILLIC SMALL LETTER YERU"],
        [0x044c, "CYRILLIC SMALL LETTER SOFT SIGN"],
        [0x044d, "CYRILLIC SMALL LETTER E"],
        [0x044e, "CYRILLIC SMALL LETTER YU"],
        [0x044f, "CYRILLIC SMALL LETTER YA"],
      ],
    },
    {
      id: "emoji",
      label: "絵文字",
      chars: [
        [0x1f600, "GRINNING FACE"],
        [0x1f601, "GRINNING FACE WITH SMILING EYES"],
        [0x1f602, "FACE WITH TEARS OF JOY"],
        [0x1f603, "SMILING FACE WITH OPEN MOUTH"],
        [0x1f604, "SMILING FACE WITH OPEN MOUTH AND SMILING EYES"],
        [0x1f605, "SMILING FACE WITH OPEN MOUTH AND COLD SWEAT"],
        [0x1f607, "SMILING FACE WITH HALO"],
        [0x1f608, "SMILING FACE WITH HORNS"],
        [0x1f609, "WINKING FACE"],
        [0x1f60a, "SMILING FACE WITH SMILING EYES"],
        [0x1f60b, "FACE SAVOURING DELICIOUS FOOD"],
        [0x1f60d, "SMILING FACE WITH HEART-SHAPED EYES"],
        [0x1f60e, "SMILING FACE WITH SUNGLASSES"],
        [0x1f610, "NEUTRAL FACE"],
        [0x1f611, "EXPRESSIONLESS FACE"],
        [0x1f614, "PENSIVE FACE"],
        [0x1f615, "CONFUSED FACE"],
        [0x1f618, "FACE THROWING A KISS"],
        [0x1f61a, "KISSING FACE WITH CLOSED EYES"],
        [0x1f61c, "FACE WITH STUCK-OUT TONGUE AND WINKING EYE"],
        [0x1f620, "ANGRY FACE"],
        [0x1f621, "POUTING FACE"],
        [0x1f622, "CRYING FACE"],
        [0x1f625, "DISAPPOINTED BUT RELIEVED FACE"],
        [0x1f628, "FEARFUL FACE"],
        [0x1f62d, "LOUDLY CRYING FACE"],
        [0x1f631, "FACE SCREAMING IN FEAR"],
        [0x1f634, "SLEEPING FACE"],
        [0x1f637, "FACE WITH MEDICAL MASK"],
        [0x1f638, "GRINNING CAT FACE WITH SMILING EYES"],
        [0x1f44d, "THUMBS UP SIGN"],
        [0x1f44e, "THUMBS DOWN SIGN"],
        [0x1f44f, "CLAPPING HANDS SIGN"],
        [0x1f450, "OPEN HANDS SIGN"],
        [0x1f451, "CROWN"],
        [0x1f452, "WOMANS HAT"],
        [0x1f453, "EYEGLASSES"],
        [0x1f454, "NECKTIE"],
        [0x1f455, "T-SHIRT"],
        [0x1f456, "JEANS"],
        [0x1f457, "DRESS"],
        [0x1f458, "KIMONO"],
        [0x1f459, "BIKINI"],
        [0x1f4a9, "PILE OF POO"],
        [0x1f4af, "HUNDRED POINTS SYMBOL"],
        [0x1f525, "FIRE"],
        [0x1f389, "PARTY POPPER"],
        [0x1f38a, "CONFETTI BALL"],
        [0x1f3b5, "MUSICAL NOTE"],
        [0x1f3b6, "MULTIPLE MUSICAL NOTES"],
        [0x1f31f, "GLOWING STAR"],
        [0x2764, "HEAVY BLACK HEART"],
        [0x1f49a, "GREEN HEART"],
        [0x1f49b, "YELLOW HEART"],
        [0x1f49c, "PURPLE HEART"],
        [0x1f499, "BLUE HEART"],
        [0x1f498, "HEART WITH ARROW"],
      ],
    },
  ];

  /* ── 全文字リスト（横断検索用） ── */
  var ALL_CHARS = [];
  CATS.forEach(function (cat) {
    cat.chars.forEach(function (ch) {
      ALL_CHARS.push({ cp: ch[0], name: ch[1], cat: cat.id });
    });
  });

  /* ── 状態 ── */
  var activeCat = "arrows";
  var activeSearch = "";
  var selectedChar = null;

  /* ── DOM参照 ── */
  var grid = document.getElementById("umap-grid");
  var statusEl = document.getElementById("umap-status");
  var searchEl = document.getElementById("umap-search");
  var catsEl = document.getElementById("umap-cats");
  var detail = document.getElementById("umap-detail");
  var detailGlyph = document.getElementById("umap-dg");
  var detailName = document.getElementById("umap-dn");
  var detailRows = document.getElementById("umap-dr");
  var toastEl = document.getElementById("umap-toast");
  var toastTimer = null;

  /* ── ユーティリティ ── */
  function cpToStr(cp) {
    return String.fromCodePoint(cp);
  }

  function cpToHex(cp) {
    return cp.toString(16).toUpperCase().padStart(4, "0");
  }

  function cpToCodePoint(cp) {
    return "U+" + cpToHex(cp);
  }

  function cpToHtmlDec(cp) {
    return "&#" + cp + ";";
  }

  function cpToHtmlHex(cp) {
    return "&#x" + cpToHex(cp) + ";";
  }

  function cpToCss(cp) {
    return '\\' + cp.toString(16).toUpperCase();
  }

  function cpToUtf8(cp) {
    var utf8 = [];
    if (cp < 0x80) {
      utf8.push(cp);
    } else if (cp < 0x800) {
      utf8.push(0xc0 | (cp >> 6));
      utf8.push(0x80 | (cp & 0x3f));
    } else if (cp < 0x10000) {
      utf8.push(0xe0 | (cp >> 12));
      utf8.push(0x80 | ((cp >> 6) & 0x3f));
      utf8.push(0x80 | (cp & 0x3f));
    } else {
      utf8.push(0xf0 | (cp >> 18));
      utf8.push(0x80 | ((cp >> 12) & 0x3f));
      utf8.push(0x80 | ((cp >> 6) & 0x3f));
      utf8.push(0x80 | (cp & 0x3f));
    }
    return utf8.map(function (b) {
      return "0x" + b.toString(16).toUpperCase().padStart(2, "0");
    }).join(" ");
  }

  function showToast(msg) {
    toastEl.textContent = msg;
    toastEl.classList.add("show");
    clearTimeout(toastTimer);
    toastTimer = setTimeout(function () {
      toastEl.classList.remove("show");
    }, 1800);
  }

  function copyText(text) {
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).catch(function () {
        fallbackCopy(text);
      });
    } else {
      fallbackCopy(text);
    }
  }

  function fallbackCopy(text) {
    var ta = document.createElement("textarea");
    ta.value = text;
    ta.style.position = "fixed";
    ta.style.opacity = "0";
    document.body.appendChild(ta);
    ta.select();
    try { document.execCommand("copy"); } catch (e) {}
    document.body.removeChild(ta);
  }

  /* ── フィルタリング ── */
  function getFilteredChars() {
    var q = activeSearch.trim().toLowerCase();
    if (q === "") {
      var cat = CATS.find(function (c) { return c.id === activeCat; });
      return cat ? cat.chars.map(function (ch) {
        return { cp: ch[0], name: ch[1] };
      }) : [];
    }
    // コードポイント検索
    var cpMatch = q.match(/^u\+?([0-9a-f]{4,6})$/i) || q.match(/^0x([0-9a-f]{4,6})$/i);
    if (!cpMatch) cpMatch = q.match(/^([0-9a-f]{4,6})$/i);
    if (cpMatch) {
      var target = parseInt(cpMatch[1], 16);
      return ALL_CHARS.filter(function (c) { return c.cp === target; });
    }
    return ALL_CHARS.filter(function (c) {
      return c.name.toLowerCase().indexOf(q) !== -1;
    });
  }

  /* ── グリッド描画 ── */
  function renderGrid() {
    var chars = getFilteredChars();
    statusEl.textContent = chars.length + " 文字を表示中";
    grid.innerHTML = "";
    if (chars.length === 0) {
      var empty = document.createElement("div");
      empty.className = "umap-empty";
      empty.style.gridColumn = "1 / -1";
      empty.textContent = "文字が見つかりません。";
      grid.appendChild(empty);
      return;
    }
    chars.forEach(function (ch) {
      var cell = document.createElement("div");
      cell.className = "umap-cell";
      cell.title = ch.name + "\n" + cpToCodePoint(ch.cp);
      var glyph = document.createElement("div");
      glyph.className = "umap-glyph";
      glyph.textContent = cpToStr(ch.cp);
      var cpLabel = document.createElement("div");
      cpLabel.className = "umap-cp";
      cpLabel.textContent = cpToCodePoint(ch.cp);
      cell.appendChild(glyph);
      cell.appendChild(cpLabel);
      cell.addEventListener("click", function () {
        openDetail(ch.cp, ch.name, cell);
        cell.classList.add("copied");
        setTimeout(function () { cell.classList.remove("copied"); }, 700);
      });
      grid.appendChild(cell);
    });
  }

  /* ── 詳細パネル ── */
  function openDetail(cp, name, _cell) {
    selectedChar = { cp: cp, name: name };
    detailGlyph.textContent = cpToStr(cp);
    detailName.textContent = name + " — " + cpToCodePoint(cp);

    var rows = [
      { label: "文字", value: cpToStr(cp) },
      { label: "コードポイント", value: cpToCodePoint(cp) },
      { label: "HTML（10進）", value: cpToHtmlDec(cp) },
      { label: "HTML（16進）", value: cpToHtmlHex(cp) },
      { label: "CSS content値", value: "'" + cpToCss(cp) + "'" },
      { label: "UTF-8バイト列", value: cpToUtf8(cp) },
    ];

    detailRows.innerHTML = "";
    rows.forEach(function (row) {
      var lbl = document.createElement("div");
      lbl.className = "umap-detail-label";
      lbl.textContent = row.label;

      var val = document.createElement("div");
      val.className = "umap-detail-value";
      val.textContent = row.value;

      var btn = document.createElement("button");
      btn.className = "umap-copy-btn";
      btn.textContent = "コピー";
      (function (v, b) {
        b.addEventListener("click", function () {
          copyText(v);
          b.textContent = "コピー完了";
          b.classList.add("ok");
          showToast("コピーしました: " + v);
          setTimeout(function () {
            b.textContent = "コピー";
            b.classList.remove("ok");
          }, 1500);
        });
      })(row.value, btn);

      detailRows.appendChild(lbl);
      detailRows.appendChild(val);
      detailRows.appendChild(btn);
    });

    detail.classList.add("visible");
    detail.scrollIntoView({ behavior: "smooth", block: "nearest" });
  }

  document.getElementById("umap-detail-close").addEventListener("click", function () {
    detail.classList.remove("visible");
    selectedChar = null;
  });

  /* ── カテゴリボタン生成 ── */
  CATS.forEach(function (cat) {
    var btn = document.createElement("button");
    btn.className = "umap-cat-btn" + (cat.id === activeCat ? " active" : "");
    btn.textContent = cat.label;
    btn.addEventListener("click", function () {
      activeCat = cat.id;
      activeSearch = "";
      searchEl.value = "";
      document.querySelectorAll("#umap-app .umap-cat-btn").forEach(function (b) {
        b.classList.remove("active");
      });
      btn.classList.add("active");
      detail.classList.remove("visible");
      renderGrid();
    });
    catsEl.appendChild(btn);
  });

  /* ── 検索 ── */
  var searchDebounce;
  searchEl.addEventListener("input", function () {
    clearTimeout(searchDebounce);
    searchDebounce = setTimeout(function () {
      activeSearch = searchEl.value;
      if (activeSearch.trim() !== "") {
        document.querySelectorAll("#umap-app .umap-cat-btn").forEach(function (b) {
          b.classList.remove("active");
        });
      } else {
        document.querySelectorAll("#umap-app .umap-cat-btn")[
          CATS.findIndex(function (c) { return c.id === activeCat; })
        ].classList.add("active");
      }
      detail.classList.remove("visible");
      renderGrid();
    }, 200);
  });

  /* ── 初期化 ── */
  renderGrid();
})();
</script>

</div>

---

### 使い方

1. **カテゴリを選択** — 「矢印」「数学」「通貨」などのボタンをクリックして文字一覧を表示します。
2. **検索** — 文字名（例: `arrow left`）またはコードポイント（例: `U+2192`）を入力すると全カテゴリを横断して絞り込みます。
3. **文字をクリック** — 詳細パネルに文字・Unicodeコードポイント・HTMLエンティティ（10進・16進）・CSS `content` 値・UTF-8バイト列が表示されます。各項目に「コピー」ボタンがあります。

### 各項目の意味

| 項目 | 例 | 使いどころ |
|---|---|---|
| コードポイント | `U+2192` | ドキュメントや仕様書での参照 |
| HTML（10進） | `&#8594;` | HTMLへの埋め込み（エンコード問題を回避） |
| HTML（16進） | `&#x2192;` | 同上、16進表記 |
| CSS content値 | `'\2192'` | `::before` / `::after` 疑似要素での使用 |
| UTF-8バイト列 | `0xE2 0x86 0x92` | バイナリストリームやファイルエンコーディングの確認 |

### 関連ツール

- [HTMLエンティティエンコーダー](/tools/html-entity-encoder/) — HTMLエンティティの一括エンコード・デコード
- [絵文字ピッカー](/tools/emoji-picker/) — スキントーン・キーワード対応の絵文字ブラウザ
- [モールス信号変換](/tools/morse-code-translator/) — テキストとモールス信号の相互変換
