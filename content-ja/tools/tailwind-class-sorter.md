---
title: "Tailwind CSSクラスソーター"
slug: "tailwind-class-sorter"
date: 2025-10-05
description: "無料のTailwind CSSクラス並べ替えツール。ユーティリティクラスを推奨順序に自動ソート。コピペで即整理。"
categories: ["無料ツール"]
tags: ["tailwind", "css", "ユーティリティクラス", "開発ツール", "クラスソーター"]
cover:
  image: "/images/covers/tailwind-class-sorter-ja.png"
  alt: "Tailwind CSSクラスソーター"
ShowToc: false
---

TailwindのユーティリティクラスをコピペするだけでTailwind推奨順序に自動整列。レイアウト→ポジション→サイズ→スペーシング→タイポグラフィ→背景→ボーダー→エフェクト→トランジション→インタラクションの順でキレイに並べ替えます。

関連ツール：[CSS変数ジェネレーター](/ja/tools/css-variables-generator/) · [CSSメディアクエリジェネレーター](/ja/tools/media-query-generator/)

<div id="tw-app-ja">
<style>
  #tw-app-ja {
    font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Segoe UI", sans-serif;
    max-width: 860px;
    margin: 0 auto;
    color: #1e293b;
  }
  #tw-app-ja * { box-sizing: border-box; }

  #tw-app-ja .tw-card {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 20px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
  }

  #tw-app-ja label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: #475569;
    margin-bottom: 6px;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  #tw-app-ja textarea {
    width: 100%;
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    padding: 12px 14px;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
    font-size: 13px;
    line-height: 1.6;
    resize: vertical;
    color: #0f172a;
    background: #f8fafc;
    transition: border-color 0.15s;
    min-height: 120px;
  }
  #tw-app-ja textarea:focus {
    outline: none;
    border-color: #38bdf8;
    background: #fff;
    box-shadow: 0 0 0 3px rgba(56,189,248,0.15);
  }

  #tw-app-ja .tw-options {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    align-items: center;
    margin: 16px 0;
  }

  #tw-app-ja .tw-checkbox-label {
    display: flex;
    align-items: center;
    gap: 7px;
    font-size: 14px;
    font-weight: 500;
    color: #374151;
    cursor: pointer;
    text-transform: none;
    letter-spacing: 0;
  }
  #tw-app-ja .tw-checkbox-label input[type="checkbox"] {
    width: 16px;
    height: 16px;
    accent-color: #0ea5e9;
    cursor: pointer;
  }

  #tw-app-ja .tw-btn-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 16px;
  }

  #tw-app-ja button {
    padding: 9px 18px;
    border-radius: 8px;
    border: none;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s, transform 0.1s;
  }
  #tw-app-ja button:active { transform: scale(0.97); }

  #tw-app-ja .btn-primary {
    background: #0ea5e9;
    color: #fff;
  }
  #tw-app-ja .btn-primary:hover { background: #0284c7; }

  #tw-app-ja .btn-secondary {
    background: #f1f5f9;
    color: #334155;
    border: 1px solid #e2e8f0;
  }
  #tw-app-ja .btn-secondary:hover { background: #e2e8f0; }

  #tw-app-ja .btn-danger {
    background: #f1f5f9;
    color: #64748b;
    border: 1px solid #e2e8f0;
    margin-left: auto;
  }
  #tw-app-ja .btn-danger:hover { background: #fee2e2; color: #dc2626; border-color: #fca5a5; }

  #tw-app-ja .tw-result-area { display: none; }
  #tw-app-ja .tw-result-area.visible { display: block; }

  #tw-app-ja .tw-stats {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 16px;
  }

  #tw-app-ja .tw-stat-badge {
    background: #f0f9ff;
    border: 1px solid #bae6fd;
    border-radius: 6px;
    padding: 6px 12px;
    font-size: 13px;
    color: #0369a1;
    font-weight: 500;
  }
  #tw-app-ja .tw-stat-badge span {
    font-weight: 700;
    color: #0284c7;
  }

  #tw-app-ja .tw-diff {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 16px;
  }
  @media (max-width: 600px) {
    #tw-app-ja .tw-diff { grid-template-columns: 1fr; }
  }

  #tw-app-ja .tw-diff-box { border-radius: 8px; overflow: hidden; }
  #tw-app-ja .tw-diff-label {
    padding: 8px 14px;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.04em;
    text-transform: uppercase;
  }
  #tw-app-ja .tw-diff-label.before { background: #fef3c7; color: #92400e; border-bottom: 1px solid #fde68a; }
  #tw-app-ja .tw-diff-label.after  { background: #d1fae5; color: #065f46; border-bottom: 1px solid #6ee7b7; }
  #tw-app-ja .tw-diff-content {
    padding: 12px 14px;
    font-family: "SFMono-Regular", Consolas, monospace;
    font-size: 12px;
    line-height: 1.7;
    word-break: break-all;
    min-height: 60px;
  }
  #tw-app-ja .tw-diff-box.before .tw-diff-content {
    background: #fffbeb; border: 1px solid #fde68a; border-top: none;
    border-radius: 0 0 8px 8px; color: #78350f;
  }
  #tw-app-ja .tw-diff-box.after .tw-diff-content {
    background: #f0fdf4; border: 1px solid #6ee7b7; border-top: none;
    border-radius: 0 0 8px 8px; color: #14532d;
  }

  #tw-app-ja .tw-output-wrap { position: relative; }
  #tw-app-ja .tw-output {
    width: 100%;
    background: #0f172a;
    color: #e2e8f0;
    border: 1px solid #334155;
    border-radius: 8px;
    padding: 14px;
    font-family: "SFMono-Regular", Consolas, monospace;
    font-size: 13px;
    line-height: 1.7;
    min-height: 80px;
    resize: vertical;
  }

  #tw-app-ja .tw-copy-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    padding: 5px 12px;
    font-size: 12px;
    background: #334155;
    color: #94a3b8;
    border-radius: 6px;
  }
  #tw-app-ja .tw-copy-btn:hover { background: #475569; color: #e2e8f0; }
  #tw-app-ja .tw-copy-btn.copied { background: #10b981; color: #fff; }

  #tw-app-ja .tw-error {
    background: #fef2f2;
    border: 1px solid #fecaca;
    border-radius: 8px;
    padding: 12px 16px;
    color: #dc2626;
    font-size: 14px;
    margin-top: 12px;
    display: none;
  }
  #tw-app-ja .tw-error.visible { display: block; }

  #tw-app-ja .tw-mode-toggle {
    display: flex;
    gap: 0;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    overflow: hidden;
    width: fit-content;
    margin-bottom: 16px;
  }
  #tw-app-ja .tw-mode-btn {
    padding: 7px 16px;
    font-size: 13px;
    font-weight: 600;
    background: #f8fafc;
    color: #64748b;
    border: none;
    border-radius: 0;
    cursor: pointer;
    transition: background 0.15s, color 0.15s;
  }
  #tw-app-ja .tw-mode-btn.active { background: #0ea5e9; color: #fff; }
  #tw-app-ja .tw-mode-btn:first-child { border-radius: 7px 0 0 7px; }
  #tw-app-ja .tw-mode-btn:last-child { border-radius: 0 7px 7px 0; }

  #tw-app-ja .tw-section-title {
    font-size: 15px;
    font-weight: 700;
    color: #0f172a;
    margin: 0 0 12px 0;
  }

  #tw-app-ja .tw-hint {
    font-size: 12px;
    color: #94a3b8;
    margin-top: 6px;
  }

  /* freee CTA */
  #tw-app-ja .freee-cta {
    background: linear-gradient(135deg, #e8f5e9 0%, #f1f8e9 100%);
    border: 1px solid #a5d6a7;
    border-radius: 12px;
    padding: 20px 24px;
    margin-top: 32px;
    display: flex;
    align-items: center;
    gap: 16px;
    flex-wrap: wrap;
  }
  #tw-app-ja .freee-cta-icon {
    font-size: 36px;
    flex-shrink: 0;
  }
  #tw-app-ja .freee-cta-body { flex: 1; min-width: 200px; }
  #tw-app-ja .freee-cta-title {
    font-size: 15px;
    font-weight: 700;
    color: #1b5e20;
    margin-bottom: 4px;
  }
  #tw-app-ja .freee-cta-desc {
    font-size: 13px;
    color: #388e3c;
    line-height: 1.5;
  }
  #tw-app-ja .freee-cta-btn {
    display: inline-block;
    background: #43a047;
    color: #fff;
    font-weight: 700;
    font-size: 14px;
    padding: 10px 20px;
    border-radius: 8px;
    text-decoration: none;
    white-space: nowrap;
    transition: background 0.15s;
  }
  #tw-app-ja .freee-cta-btn:hover { background: #2e7d32; }

  /* A8 footer */
  #tw-app-ja .a8-footer {
    margin-top: 24px;
    padding: 16px;
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    font-size: 11px;
    color: #94a3b8;
    line-height: 1.6;
    text-align: center;
  }
  #tw-app-ja .a8-footer a { color: #64748b; }
</style>

<div class="tw-card">
  <p class="tw-section-title">入力モード</p>
  <div class="tw-mode-toggle">
    <button class="tw-mode-btn active" id="tw-ja-mode-single" onclick="twJaSetMode('single')">クラス文字列</button>
    <button class="tw-mode-btn" id="tw-ja-mode-html" onclick="twJaSetMode('html')">HTML要素</button>
  </div>

  <label for="tw-ja-input" id="tw-ja-input-label">Tailwindクラスを貼り付け</label>
  <textarea id="tw-ja-input" placeholder="例: text-white font-bold p-4 flex bg-blue-500 rounded-lg shadow-md mt-2 hover:bg-blue-600 items-center justify-between" rows="5"></textarea>
  <p class="tw-hint" id="tw-ja-input-hint">スペース区切りのTailwindユーティリティクラスを貼り付けてください。</p>

  <div class="tw-options">
    <label class="tw-checkbox-label">
      <input type="checkbox" id="tw-ja-dedup" checked>
      重複クラスを削除する
    </label>
  </div>

  <div class="tw-btn-row">
    <button class="btn-primary" onclick="twJaSort()">クラスを並べ替え</button>
    <button class="btn-secondary" onclick="twJaSample()">サンプルを読み込む</button>
    <button class="btn-danger" onclick="twJaClear()">クリア</button>
  </div>
  <div class="tw-error" id="tw-ja-error"></div>
</div>

<div class="tw-result-area" id="tw-ja-result-area">
  <div class="tw-card">
    <p class="tw-section-title">結果</p>
    <div class="tw-stats" id="tw-ja-stats"></div>

    <div class="tw-diff" id="tw-ja-diff-wrap">
      <div class="tw-diff-box before">
        <div class="tw-diff-label before">並べ替え前</div>
        <div class="tw-diff-content" id="tw-ja-before"></div>
      </div>
      <div class="tw-diff-box after">
        <div class="tw-diff-label after">並べ替え後</div>
        <div class="tw-diff-content" id="tw-ja-after"></div>
      </div>
    </div>

    <label>ソート済み出力</label>
    <div class="tw-output-wrap">
      <textarea class="tw-output" id="tw-ja-output" readonly rows="5"></textarea>
      <button class="tw-copy-btn" id="tw-ja-copy-btn" onclick="twJaCopy()">コピー</button>
    </div>
  </div>
</div>

<script>
(function() {
  var TW_ORDER_JA = (function() {
    var groups = [
      { w: 0,   rx: /^(block|inline-block|inline|flex|inline-flex|grid|inline-grid|table|table-row|table-cell|hidden|contents|flow-root|list-item)$/ },
      { w: 10,  rx: /^(container|box-border|box-content)$/ },
      { w: 20,  rx: /^overflow/ },
      { w: 30,  rx: /^(float-|clear-|isolat)/ },
      { w: 40,  rx: /^object-/ },
      { w: 100, rx: /^(static|fixed|absolute|relative|sticky)$/ },
      { w: 110, rx: /^(inset|top-|right-|bottom-|left-|-?inset)/ },
      { w: 115, rx: /^-?(top|right|bottom|left)-/ },
      { w: 120, rx: /^z-/ },
      { w: 130, rx: /^(visible|invisible|collapse)$/ },
      { w: 200, rx: /^(flex-row|flex-col|flex-wrap|flex-nowrap|flex-row-reverse|flex-col-reverse|flex-wrap-reverse)$/ },
      { w: 210, rx: /^(grid-cols-|grid-rows-|grid-flow-|col-|row-|auto-cols-|auto-rows-|gap-|gap-x-|gap-y-)/ },
      { w: 220, rx: /^(flex-1|flex-auto|flex-initial|flex-none|grow|shrink|basis-|order-)/ },
      { w: 230, rx: /^(items-|justify-|content-|self-|place-|justify-items-|justify-self-)/ },
      { w: 300, rx: /^w-/ },
      { w: 305, rx: /^(min-w-|max-w-)/ },
      { w: 310, rx: /^h-/ },
      { w: 315, rx: /^(min-h-|max-h-)/ },
      { w: 320, rx: /^aspect-/ },
      { w: 400, rx: /^p-/ },
      { w: 402, rx: /^(px-|py-)/ },
      { w: 404, rx: /^(pt-|pr-|pb-|pl-)/ },
      { w: 410, rx: /^-?m-/ },
      { w: 412, rx: /^-?(mx-|my-)/ },
      { w: 414, rx: /^-?(mt-|mr-|mb-|ml-)/ },
      { w: 420, rx: /^space-/ },
      { w: 500, rx: /^font-(sans|serif|mono)$/ },
      { w: 505, rx: /^text-(xs|sm|base|lg|xl|2xl|3xl|4xl|5xl|6xl|7xl|8xl|9xl)$/ },
      { w: 510, rx: /^font-(thin|extralight|light|normal|medium|semibold|bold|extrabold|black)$/ },
      { w: 515, rx: /^(italic|not-italic|antialiased|subpixel-antialiased|normal-nums|ordinal|slashed-zero|lining-nums|oldstyle-nums|proportional-nums|tabular-nums|diagonal-fractions|stacked-fractions)$/ },
      { w: 520, rx: /^leading-/ },
      { w: 525, rx: /^tracking-/ },
      { w: 530, rx: /^text-/ },
      { w: 535, rx: /^(text-left|text-center|text-right|text-justify|text-start|text-end|underline|overline|line-through|no-underline|uppercase|lowercase|capitalize|normal-case|truncate|text-ellipsis|text-clip|break-|whitespace-)/ },
      { w: 540, rx: /^list-/ },
      { w: 545, rx: /^(placeholder-|caret-)/ },
      { w: 600, rx: /^(bg-|from-|via-|to-|bg-gradient-)/ },
      { w: 700, rx: /^rounded/ },
      { w: 710, rx: /^border/ },
      { w: 720, rx: /^outline/ },
      { w: 730, rx: /^ring/ },
      { w: 740, rx: /^divide/ },
      { w: 800, rx: /^shadow/ },
      { w: 810, rx: /^opacity-/ },
      { w: 820, rx: /^(mix-blend-|bg-blend-)/ },
      { w: 830, rx: /^(filter|blur-|brightness-|contrast-|grayscale|hue-rotate-|invert|saturate-|sepia|drop-shadow-|backdrop-)/ },
      { w: 900, rx: /^(transition|duration-|ease-|delay-)/ },
      { w: 910, rx: /^(transform|scale-|rotate-|translate-|skew-|-rotate-|-scale-|-translate-|-skew-|origin-)/ },
      { w: 1000, rx: /^(cursor-|pointer-events-|resize-?|select-|scroll-|touch-|will-change-|user-select-|appearance-|accent-color-)/ },
      { w: 1100, rx: /^(sr-only|not-sr-only|focus-within:|focus-visible:|focus:|active:|group|peer)/ },
      { w: 1200, rx: /^print:/ },
    ];
    return function getWeight(cls) {
      var base = cls.replace(/^([a-z-]+:)+/, '');
      var variantOffset = 0;
      var variantMatch = cls.match(/^(([a-z-]+:)+)/);
      if (variantMatch) {
        var variants = variantMatch[1].split(':').filter(Boolean);
        var responsive = { sm: 1, md: 2, lg: 3, xl: 4, '2xl': 5 };
        var state = { hover: 0.1, focus: 0.2, active: 0.3, disabled: 0.4, dark: 0.5, group: 0.6, peer: 0.7 };
        variants.forEach(function(v) {
          if (responsive[v] !== undefined) variantOffset += responsive[v] * 10000;
          else if (state[v] !== undefined) variantOffset += state[v] * 1000;
          else variantOffset += 500;
        });
      }
      for (var i = 0; i < groups.length; i++) {
        if (groups[i].rx.test(base)) return groups[i].w + variantOffset;
      }
      return 9999 + variantOffset;
    };
  })();

  var mode = 'single';

  window.twJaSetMode = function(m) {
    mode = m;
    document.getElementById('tw-ja-mode-single').classList.toggle('active', m === 'single');
    document.getElementById('tw-ja-mode-html').classList.toggle('active', m === 'html');
    var lbl = document.getElementById('tw-ja-input-label');
    var hint = document.getElementById('tw-ja-input-hint');
    var inp = document.getElementById('tw-ja-input');
    if (m === 'single') {
      lbl.textContent = 'Tailwindクラスを貼り付け';
      hint.textContent = 'スペース区切りのTailwindユーティリティクラスを貼り付けてください。';
      inp.placeholder = '例: text-white font-bold p-4 flex bg-blue-500 rounded-lg shadow-md mt-2 hover:bg-blue-600 items-center justify-between';
    } else {
      lbl.textContent = 'HTML要素を貼り付け（class="..." 属性を含む）';
      hint.textContent = '1つ以上のHTML要素を貼り付けてください。各 class="..." 属性を個別にソートします。';
      inp.placeholder = '<div class="text-white font-bold p-4 flex bg-blue-500 rounded-lg mt-2">\n  <button class="hover:bg-blue-600 items-center justify-between px-4 py-2 rounded text-sm font-medium">\n    クリック\n  </button>\n</div>';
    }
    document.getElementById('tw-ja-result-area').classList.remove('visible');
    showJaError('');
  };

  function sortClasses(classStr, dedup) {
    var classes = classStr.trim().split(/\s+/).filter(Boolean);
    var seen = {}, unique = [], dupCount = 0;
    classes.forEach(function(c) {
      if (dedup) {
        if (!seen[c]) { seen[c] = true; unique.push(c); }
        else dupCount++;
      } else { unique.push(c); }
    });
    unique.sort(function(a, b) { return TW_ORDER_JA(a) - TW_ORDER_JA(b); });
    return { sorted: unique, dupCount: dupCount, originalCount: classes.length };
  }

  function sortHtml(html, dedup) {
    var totalDups = 0, totalOriginal = 0;
    var result = html.replace(/class="([^"]*)"/g, function(match, classStr) {
      var r = sortClasses(classStr, dedup);
      totalDups += r.dupCount; totalOriginal += r.originalCount;
      return 'class="' + r.sorted.join(' ') + '"';
    });
    result = result.replace(/class='([^']*)'/g, function(match, classStr) {
      var r = sortClasses(classStr, dedup);
      totalDups += r.dupCount; totalOriginal += r.originalCount;
      return "class='" + r.sorted.join(' ') + "'";
    });
    return { sorted: result, dupCount: totalDups, originalCount: totalOriginal };
  }

  function showJaError(msg) {
    var el = document.getElementById('tw-ja-error');
    el.textContent = msg;
    el.classList.toggle('visible', !!msg);
  }

  window.twJaSort = function() {
    showJaError('');
    var input = document.getElementById('tw-ja-input').value;
    if (!input.trim()) { showJaError('TailwindクラスまたはHTMLを貼り付けてください。'); return; }
    var dedup = document.getElementById('tw-ja-dedup').checked;

    var beforeText, afterText, outputText, totalCount, dupCount;

    if (mode === 'single') {
      var r = sortClasses(input.trim(), dedup);
      beforeText = input.trim(); afterText = r.sorted.join(' ');
      outputText = r.sorted.join(' ');
      totalCount = r.originalCount; dupCount = r.dupCount;
    } else {
      var r2 = sortHtml(input, dedup);
      beforeText = input; afterText = r2.sorted; outputText = r2.sorted;
      totalCount = r2.originalCount; dupCount = r2.dupCount;
    }

    var statsHtml = '<div class="tw-stat-badge">クラス数: <span>' + totalCount + '</span></div>';
    if (dedup && dupCount > 0) {
      statsHtml += '<div class="tw-stat-badge">重複削除: <span>' + dupCount + '件</span></div>';
    }
    if (dedup && dupCount === 0) {
      statsHtml += '<div class="tw-stat-badge">重複なし</div>';
    }
    document.getElementById('tw-ja-stats').innerHTML = statsHtml;

    document.getElementById('tw-ja-before').textContent = beforeText;
    document.getElementById('tw-ja-after').textContent = afterText;
    document.getElementById('tw-ja-output').value = outputText;
    document.getElementById('tw-ja-result-area').classList.add('visible');

    var copyBtn = document.getElementById('tw-ja-copy-btn');
    copyBtn.textContent = 'コピー';
    copyBtn.classList.remove('copied');

    document.getElementById('tw-ja-result-area').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  window.twJaCopy = function() {
    var output = document.getElementById('tw-ja-output');
    output.select();
    try { document.execCommand('copy'); }
    catch(e) { if (navigator.clipboard) navigator.clipboard.writeText(output.value); }
    var btn = document.getElementById('tw-ja-copy-btn');
    btn.textContent = 'コピーしました!';
    btn.classList.add('copied');
    setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 2000);
  };

  window.twJaClear = function() {
    document.getElementById('tw-ja-input').value = '';
    document.getElementById('tw-ja-result-area').classList.remove('visible');
    showJaError('');
  };

  window.twJaSample = function() {
    if (mode === 'single') {
      document.getElementById('tw-ja-input').value = 'hover:bg-blue-600 font-bold text-white flex shadow-lg p-4 rounded-xl mt-6 bg-blue-500 items-center justify-between w-full border border-blue-300 transition-colors duration-200 focus:outline-none focus:ring-2 focus:ring-blue-400 text-lg leading-tight tracking-wide opacity-100 z-10 relative overflow-hidden';
    } else {
      document.getElementById('tw-ja-input').value = '<div class="shadow-lg flex bg-white rounded-xl p-6 mt-4 border border-gray-200 hover:shadow-xl transition-shadow duration-300 w-full max-w-md">\n  <h2 class="text-2xl font-bold text-gray-900 mb-2 leading-tight tracking-tight">\n    カードタイトル\n  </h2>\n  <button class="hover:bg-blue-600 mt-4 bg-blue-500 text-white font-semibold py-2 px-4 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-400 transition-colors duration-200 cursor-pointer">\n    クリック\n  </button>\n</div>';
    }
    document.getElementById('tw-ja-result-area').classList.remove('visible');
    showJaError('');
  };
})();
</script>

<!-- freee CTA -->
<div class="freee-cta">
  <div class="freee-cta-icon">💼</div>
  <div class="freee-cta-body">
    <div class="freee-cta-title">フリーランス・個人事業主の経理をまるごと自動化</div>
    <div class="freee-cta-desc">freee会計なら確定申告・請求書・帳簿がすべて一元管理。開発者・フリーランスエンジニアに選ばれています。</div>
  </div>
  <a class="freee-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=3ZPHQX+XXXXXX+XXXX+XXXXXX" rel="nofollow noopener" target="_blank">freeeを無料で試す</a>
</div>

<div class="a8-footer">
  <a href="https://px.a8.net/svt/ejp?a8mat=3ZPHQX+XXXXXX+XXXX+XXXXXX" rel="nofollow noopener" target="_blank">
    <img src="https://www19.a8.net/0.gif?a8mat=3ZPHQX+XXXXXX+XXXX+XXXXXX" width="1" height="1" alt="" style="border:none;" />
  </a>
  ※本記事にはアフィリエイト広告が含まれます。
</div>

</div>

---

### ソート順の仕組み

Tailwind CSS公式の[Prettier プラグイン](https://tailwindcss.com/blog/automatic-class-sorting-with-prettier)と同じ推奨順序でクラスを並べ替えます。

| グループ | 代表クラス例 |
|---|---|
| レイアウト | `flex`, `grid`, `block`, `hidden`, `overflow-hidden` |
| ポジション | `relative`, `absolute`, `top-0`, `z-10` |
| サイズ | `w-full`, `h-16`, `max-w-md` |
| スペーシング | `p-4`, `mx-auto`, `space-x-2` |
| タイポグラフィ | `text-lg`, `font-bold`, `leading-tight`, `text-gray-900` |
| 背景 | `bg-white`, `from-blue-500`, `bg-gradient-to-r` |
| ボーダー | `rounded-xl`, `border`, `ring-2` |
| エフェクト | `shadow-lg`, `opacity-75` |
| トランジション | `transition`, `duration-200`, `ease-in-out` |
| トランスフォーム | `scale-95`, `rotate-3`, `translate-x-1` |
| インタラクション | `cursor-pointer`, `select-none` |

レスポンシブ（`sm:`, `md:`, `lg:`）・状態（`hover:`, `focus:`, `dark:`）バリアントは、対応するベースクラスグループの後ろにまとめてソートされます。

---

### 使い方のヒント

- **HTML要素モード**はコンポーネントをまるごと貼り付けるときに便利。各 `class="..."` 属性を個別にソートします。
- **重複削除**はデフォルトでオンです。オフにすると元のクラス一覧がソートのみされます。
- すべてブラウザ内で処理します。入力内容はサーバーに送信されません。

関連ツール：[CSS変数ジェネレーター](/ja/tools/css-variables-generator/) · [CSSメディアクエリジェネレーター](/ja/tools/media-query-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

