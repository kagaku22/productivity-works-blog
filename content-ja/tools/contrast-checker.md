---
title: "カラーコントラストチェッカー"
slug: "contrast-checker"
description: "無料のWCAGカラーコントラストチェッカー。前景・背景色の組み合わせでアクセシビリティ準拠を確認。AA・AAAレベル対応。"
categories: ["無料ツール"]
date: 2026-01-11
ShowToc: false
cover:
  image: "/images/covers/contrast-checker-ja.png"
---

<div id="cc-app">

<style>
#cc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Meiryo", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a1a;
}
#cc-app *, #cc-app *::before, #cc-app *::after {
  box-sizing: border-box;
}
#cc-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 1rem;
  color: #111;
}
#cc-app h3 {
  font-size: 1.05rem;
  font-weight: 600;
  margin: 0 0 0.75rem;
  color: #333;
}
#cc-app .cc-intro {
  font-size: 0.97rem;
  color: #555;
  margin-bottom: 1.75rem;
  line-height: 1.7;
}
#cc-app .cc-pickers-row {
  display: flex;
  gap: 1.25rem;
  align-items: flex-end;
  flex-wrap: wrap;
  margin-bottom: 1.25rem;
}
#cc-app .cc-picker-group {
  flex: 1;
  min-width: 200px;
}
#cc-app .cc-picker-label {
  display: block;
  font-size: 0.82rem;
  font-weight: 700;
  color: #555;
  letter-spacing: 0.03em;
  margin-bottom: 0.5rem;
}
#cc-app .cc-picker-inner {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  border: 1.5px solid #d0d5dd;
  border-radius: 8px;
  padding: 0.45rem 0.75rem;
  background: #fff;
}
#cc-app .cc-picker-inner input[type="color"] {
  width: 38px;
  height: 38px;
  border: none;
  border-radius: 6px;
  padding: 0;
  cursor: pointer;
  background: transparent;
  flex-shrink: 0;
}
#cc-app .cc-hex-input {
  flex: 1;
  border: none;
  outline: none;
  font-size: 1rem;
  font-family: "Courier New", monospace;
  font-weight: 600;
  color: #1a1a1a;
  background: transparent;
  width: 90px;
}
#cc-app .cc-swap-btn {
  background: #f4f5f7;
  border: 1.5px solid #d0d5dd;
  border-radius: 8px;
  padding: 0.6rem 1.1rem;
  cursor: pointer;
  font-size: 1.25rem;
  transition: background 0.15s;
  flex-shrink: 0;
  align-self: flex-end;
  line-height: 1;
}
#cc-app .cc-swap-btn:hover {
  background: #e8eaed;
}
#cc-app .cc-ratio-card {
  background: linear-gradient(135deg, #1e3a5f 0%, #2d5a9e 100%);
  color: #fff;
  border-radius: 12px;
  padding: 1.5rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
  gap: 1rem;
}
#cc-app .cc-ratio-label {
  font-size: 0.88rem;
  opacity: 0.85;
  font-weight: 500;
  margin-bottom: 0.25rem;
}
#cc-app .cc-ratio-value {
  font-size: 2.8rem;
  font-weight: 800;
  line-height: 1;
  letter-spacing: -0.02em;
}
#cc-app .cc-ratio-tag {
  font-size: 0.8rem;
  opacity: 0.75;
  margin-top: 0.3rem;
}
#cc-app .cc-preview-box {
  border-radius: 10px;
  padding: 1.25rem 1.75rem;
  min-width: 220px;
  border: 1px solid rgba(255,255,255,0.2);
}
#cc-app .cc-preview-label {
  font-size: 0.75rem;
  opacity: 0.8;
  font-weight: 600;
  margin-bottom: 0.4rem;
}
#cc-app .cc-preview-normal {
  font-size: 1rem;
  margin-bottom: 0.35rem;
}
#cc-app .cc-preview-large {
  font-size: 1.4rem;
  font-weight: 700;
}
#cc-app .cc-results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 1rem;
  margin-bottom: 1.75rem;
}
#cc-app .cc-result-card {
  background: #fff;
  border: 1.5px solid #e2e6ea;
  border-radius: 10px;
  padding: 1.1rem 1.25rem;
}
#cc-app .cc-result-card.pass {
  border-left: 4px solid #22c55e;
}
#cc-app .cc-result-card.fail {
  border-left: 4px solid #ef4444;
}
#cc-app .cc-result-type {
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.07em;
  color: #888;
  margin-bottom: 0.3rem;
}
#cc-app .cc-result-name {
  font-size: 0.97rem;
  font-weight: 600;
  color: #1a1a1a;
  margin-bottom: 0.5rem;
}
#cc-app .cc-result-req {
  font-size: 0.82rem;
  color: #777;
  margin-bottom: 0.5rem;
}
#cc-app .cc-badge {
  display: inline-block;
  padding: 0.2rem 0.7rem;
  border-radius: 999px;
  font-size: 0.82rem;
  font-weight: 700;
}
#cc-app .cc-badge.pass {
  background: #dcfce7;
  color: #166534;
}
#cc-app .cc-badge.fail {
  background: #fee2e2;
  color: #991b1b;
}
#cc-app .cc-section-title {
  font-size: 0.82rem;
  font-weight: 700;
  color: #888;
  margin: 1.75rem 0 0.85rem;
  padding-bottom: 0.4rem;
  border-bottom: 1px solid #e8eaed;
  letter-spacing: 0.04em;
}
#cc-app .cc-suggestions {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-bottom: 1.75rem;
}
#cc-app .cc-sug-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.4rem 0.85rem;
  border-radius: 7px;
  border: 1.5px solid #d0d5dd;
  cursor: pointer;
  font-size: 0.83rem;
  font-weight: 500;
  background: #fff;
  transition: all 0.15s;
  color: #333;
}
#cc-app .cc-sug-btn:hover {
  border-color: #2d5a9e;
  background: #f0f4ff;
}
#cc-app .cc-sug-swatch {
  display: inline-flex;
  gap: 2px;
}
#cc-app .cc-sug-swatch span {
  display: inline-block;
  width: 14px;
  height: 14px;
  border-radius: 3px;
  border: 1px solid rgba(0,0,0,0.12);
}
#cc-app .cc-cta-box {
  background: #f0f7ff;
  border: 1.5px solid #bfdbfe;
  border-radius: 10px;
  padding: 1.25rem 1.5rem;
  margin-top: 2rem;
  font-size: 0.92rem;
  color: #1e3a5f;
  line-height: 1.7;
}
#cc-app .cc-cta-box strong {
  display: block;
  font-size: 1rem;
  margin-bottom: 0.4rem;
  color: #1a1a1a;
}
#cc-app .cc-cta-box a {
  color: #2d5a9e;
  font-weight: 700;
  text-decoration: underline;
}
#cc-app .cc-freee-box {
  background: #fff7ed;
  border: 1.5px solid #fed7aa;
  border-radius: 10px;
  padding: 1.25rem 1.5rem;
  margin-top: 1rem;
  font-size: 0.92rem;
  color: #7c3409;
  line-height: 1.7;
}
#cc-app .cc-freee-box strong {
  display: block;
  font-size: 1rem;
  margin-bottom: 0.4rem;
  color: #431407;
}
#cc-app .cc-freee-box a {
  color: #c2410c;
  font-weight: 700;
  text-decoration: underline;
}
#cc-app .cc-related {
  margin-top: 2rem;
  padding-top: 1.25rem;
  border-top: 1px solid #e8eaed;
}
#cc-app .cc-related-links {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-top: 0.75rem;
}
#cc-app .cc-related-links a {
  display: inline-block;
  padding: 0.45rem 1rem;
  background: #f4f5f7;
  border: 1.5px solid #d0d5dd;
  border-radius: 7px;
  color: #2d5a9e;
  font-size: 0.88rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.15s;
}
#cc-app .cc-related-links a:hover {
  background: #e8edf7;
  border-color: #2d5a9e;
}
@media (max-width: 540px) {
  #cc-app .cc-ratio-card {
    flex-direction: column;
    align-items: flex-start;
  }
  #cc-app .cc-pickers-row {
    flex-direction: column;
  }
  #cc-app .cc-swap-btn {
    align-self: center;
  }
}
</style>

<p class="cc-intro">前景色（テキスト色）と背景色を入力するだけで、WCAG 2.1 コントラスト比を即座に計算します。通常テキスト・大きなテキスト・UIコンポーネントそれぞれについて、AA・AAAレベルの合否をリアルタイムで確認できます。</p>

<div class="cc-pickers-row">
  <div class="cc-picker-group">
    <span class="cc-picker-label">前景色（テキスト）</span>
    <div class="cc-picker-inner">
      <input type="color" id="cc-fg-color" value="#1a1a1a">
      <input type="text" class="cc-hex-input" id="cc-fg-hex" value="#1a1a1a" maxlength="7" spellcheck="false">
    </div>
  </div>
  <button class="cc-swap-btn" id="cc-swap" title="色を入れ替え" aria-label="前景色と背景色を入れ替える">&#8644;</button>
  <div class="cc-picker-group">
    <span class="cc-picker-label">背景色</span>
    <div class="cc-picker-inner">
      <input type="color" id="cc-bg-color" value="#ffffff">
      <input type="text" class="cc-hex-input" id="cc-bg-hex" value="#ffffff" maxlength="7" spellcheck="false">
    </div>
  </div>
</div>

<div class="cc-ratio-card" id="cc-ratio-card">
  <div>
    <div class="cc-ratio-label">コントラスト比</div>
    <div class="cc-ratio-value" id="cc-ratio-display">21:1</div>
    <div class="cc-ratio-tag">最高コントラスト</div>
  </div>
  <div class="cc-preview-box" id="cc-preview-box">
    <div class="cc-preview-label">ライブプレビュー</div>
    <div class="cc-preview-normal" id="cc-preview-normal">通常テキストのサンプル</div>
    <div class="cc-preview-large" id="cc-preview-large">大きなテキスト</div>
  </div>
</div>

<div class="cc-results-grid" id="cc-results-grid">
</div>

<div class="cc-section-title">人気のカラーペア</div>
<div class="cc-suggestions" id="cc-suggestions"></div>

<div class="cc-freee-box">
  <strong>freee会計でデザイン制作の経費管理もラクラク</strong>
  アクセシビリティ対応のデザイン業務や外注費も、<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="nofollow noopener">freee会計</a>なら自動仕訳でスマートに管理。確定申告もまとめてサポートします。
</div>

<div class="cc-cta-box">
  <strong>チームのカラーパレットをドキュメント化しよう</strong>
  承認済みのアクセシブルな色の組み合わせは、<a href="https://www.awin1.com/cread.php?awinmid=XXXXX&awinaffid=YYYYYY&ued=https%3A%2F%2Fwww.notion.so%2F" target="_blank" rel="nofollow noopener">Notion のデザインシステムページ</a>にまとめておくとチーム全体で再利用できます。
</div>

<div class="cc-related">
  <h3>関連ツール</h3>
  <div class="cc-related-links">
    <a href="/ja/tools/color-name-finder/">カラーネームファインダー</a>
    <a href="/ja/tools/color-blindness-simulator/">色覚シミュレーター</a>
  </div>
</div>

<script>
(function() {
  'use strict';

  function hexToRgb(hex) {
    hex = hex.replace(/^#/, '');
    if (hex.length === 3) hex = hex.split('').map(function(c){ return c+c; }).join('');
    if (hex.length !== 6) return null;
    var r = parseInt(hex.slice(0,2),16);
    var g = parseInt(hex.slice(2,4),16);
    var b = parseInt(hex.slice(4,6),16);
    if (isNaN(r)||isNaN(g)||isNaN(b)) return null;
    return {r:r,g:g,b:b};
  }

  function toLinear(c) {
    var s = c / 255;
    return s <= 0.04045 ? s / 12.92 : Math.pow((s + 0.055) / 1.055, 2.4);
  }

  function luminance(rgb) {
    return 0.2126*toLinear(rgb.r) + 0.7152*toLinear(rgb.g) + 0.0722*toLinear(rgb.b);
  }

  function contrastRatio(hex1, hex2) {
    var rgb1 = hexToRgb(hex1);
    var rgb2 = hexToRgb(hex2);
    if (!rgb1 || !rgb2) return null;
    var l1 = luminance(rgb1);
    var l2 = luminance(rgb2);
    var lighter = Math.max(l1,l2);
    var darker  = Math.min(l1,l2);
    return (lighter + 0.05) / (darker + 0.05);
  }

  var fg = '#1a1a1a';
  var bg = '#ffffff';

  var fgColor   = document.getElementById('cc-fg-color');
  var bgColor   = document.getElementById('cc-bg-color');
  var fgHex     = document.getElementById('cc-fg-hex');
  var bgHex     = document.getElementById('cc-bg-hex');
  var swapBtn   = document.getElementById('cc-swap');
  var ratioDisp = document.getElementById('cc-ratio-display');
  var ratioCard = document.getElementById('cc-ratio-card');
  var prevBox   = document.getElementById('cc-preview-box');
  var prevNorm  = document.getElementById('cc-preview-normal');
  var prevLrg   = document.getElementById('cc-preview-large');
  var resultsGrid = document.getElementById('cc-results-grid');
  var sugCont   = document.getElementById('cc-suggestions');

  var criteria = [
    { level:'AA',  label:'通常テキスト',        req:4.5, desc:'18pt未満、または14pt未満の太字' },
    { level:'AA',  label:'大きなテキスト',       req:3.0, desc:'18pt以上、または14pt以上の太字' },
    { level:'AA',  label:'UIコンポーネント',     req:3.0, desc:'ボタン、アイコン、境界線など'    },
    { level:'AAA', label:'通常テキスト（強化）', req:7.0, desc:'より高い可読性基準'              },
    { level:'AAA', label:'大きなテキスト（強化）',req:4.5,desc:'大きなテキストの強化基準'        },
  ];

  var suggestions = [
    { name:'クラシック',       fg:'#000000', bg:'#ffffff' },
    { name:'ダークモード',     fg:'#f8f8f2', bg:'#282a36' },
    { name:'オーシャン',       fg:'#ffffff', bg:'#0077b6' },
    { name:'フォレスト',       fg:'#ffffff', bg:'#2d6a4f' },
    { name:'注意色',           fg:'#1a1a1a', bg:'#ffc107' },
    { name:'スカイブルー',     fg:'#003366', bg:'#cce5ff' },
    { name:'チャコール',       fg:'#f5f5f5', bg:'#3a3a3a' },
    { name:'クリムゾン',       fg:'#ffffff', bg:'#c0392b' },
  ];

  function render() {
    var ratio = contrastRatio(fg, bg);
    if (!ratio) return;

    ratioDisp.textContent = ratio.toFixed(2) + ':1';

    if (ratio >= 7) {
      ratioCard.style.background = 'linear-gradient(135deg, #14532d 0%, #166534 100%)';
    } else if (ratio >= 4.5) {
      ratioCard.style.background = 'linear-gradient(135deg, #1e3a5f 0%, #2d5a9e 100%)';
    } else if (ratio >= 3.0) {
      ratioCard.style.background = 'linear-gradient(135deg, #78350f 0%, #b45309 100%)';
    } else {
      ratioCard.style.background = 'linear-gradient(135deg, #7f1d1d 0%, #b91c1c 100%)';
    }

    prevBox.style.background = bg;
    prevBox.style.color = fg;
    prevNorm.style.color = fg;
    prevLrg.style.color  = fg;

    resultsGrid.innerHTML = '';
    criteria.forEach(function(c) {
      var pass = ratio >= c.req;
      var card = document.createElement('div');
      card.className = 'cc-result-card ' + (pass ? 'pass' : 'fail');
      card.innerHTML =
        '<div class="cc-result-type">WCAG ' + c.level + '</div>' +
        '<div class="cc-result-name">' + c.label + '</div>' +
        '<div class="cc-result-req">必要比率 ' + c.req.toFixed(1) + ':1 &mdash; ' + c.desc + '</div>' +
        '<span class="cc-badge ' + (pass?'pass':'fail') + '">' + (pass ? '合格' : '不合格') + '</span>';
      resultsGrid.appendChild(card);
    });
  }

  function normHex(h) {
    h = h.trim();
    if (!h.startsWith('#')) h = '#' + h;
    return h.toLowerCase();
  }

  fgColor.addEventListener('input', function() {
    fg = fgColor.value;
    fgHex.value = fg;
    render();
  });
  bgColor.addEventListener('input', function() {
    bg = bgColor.value;
    bgHex.value = bg;
    render();
  });

  function handleHexInput(hexInput, colorPicker, isF) {
    hexInput.addEventListener('input', function() {
      var val = normHex(hexInput.value);
      if (/^#[0-9a-f]{6}$/i.test(val)) {
        colorPicker.value = val;
        if (isF) { fg = val; } else { bg = val; }
        render();
      }
    });
    hexInput.addEventListener('blur', function() {
      var val = normHex(hexInput.value);
      if (/^#[0-9a-f]{6}$/i.test(val)) {
        hexInput.value = val;
      } else {
        hexInput.value = isF ? fg : bg;
      }
    });
  }
  handleHexInput(fgHex, fgColor, true);
  handleHexInput(bgHex, bgColor, false);

  swapBtn.addEventListener('click', function() {
    var tmp = fg; fg = bg; bg = tmp;
    fgColor.value = fg; fgHex.value = fg;
    bgColor.value = bg; bgHex.value = bg;
    render();
  });

  suggestions.forEach(function(s) {
    var btn = document.createElement('button');
    btn.className = 'cc-sug-btn';
    btn.innerHTML =
      '<span class="cc-sug-swatch">' +
        '<span style="background:' + s.fg + '"></span>' +
        '<span style="background:' + s.bg + '"></span>' +
      '</span>' +
      s.name;
    btn.addEventListener('click', function() {
      fg = s.fg; bg = s.bg;
      fgColor.value = fg; fgHex.value = fg;
      bgColor.value = bg; bgHex.value = bg;
      render();
    });
    sugCont.appendChild(btn);
  });

  render();
})();
</script>

</div>
