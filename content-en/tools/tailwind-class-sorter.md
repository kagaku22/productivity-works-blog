---
title: "Tailwind CSS Class Sorter"
slug: "tailwind-class-sorter"
date: 2025-05-16
description: "Free Tailwind CSS class sorter. Organize your Tailwind utility classes in the recommended order — paste classes and get them sorted instantly."
categories: ["Free Tools"]
tags: ["tailwind", "css", "utility classes", "developer tools", "class sorter"]
cover:
  image: "/images/covers/tailwind-class-sorter.png"
  alt: "Tailwind CSS Class Sorter"
ShowToc: false
---

Paste your Tailwind CSS utility classes and get them sorted in the recommended order — layout first, effects last. Supports single class strings or multi-element HTML snippets.

Related tools: [CSS Variables Generator](/tools/css-variables-generator/) · [CSS Media Query Generator](/tools/media-query-generator/)

<div id="tw-app">
<style>
  #tw-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    max-width: 860px;
    margin: 0 auto;
    color: #1e293b;
  }
  #tw-app * { box-sizing: border-box; }

  #tw-app .tw-card {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 20px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
  }

  #tw-app label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: #475569;
    margin-bottom: 6px;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  #tw-app textarea {
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
  #tw-app textarea:focus {
    outline: none;
    border-color: #38bdf8;
    background: #fff;
    box-shadow: 0 0 0 3px rgba(56,189,248,0.15);
  }

  #tw-app .tw-options {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    align-items: center;
    margin: 16px 0;
  }

  #tw-app .tw-checkbox-label {
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
  #tw-app .tw-checkbox-label input[type="checkbox"] {
    width: 16px;
    height: 16px;
    accent-color: #0ea5e9;
    cursor: pointer;
  }

  #tw-app .tw-btn-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 16px;
  }

  #tw-app button {
    padding: 9px 18px;
    border-radius: 8px;
    border: none;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s, transform 0.1s;
  }
  #tw-app button:active { transform: scale(0.97); }

  #tw-app .btn-primary {
    background: #0ea5e9;
    color: #fff;
  }
  #tw-app .btn-primary:hover { background: #0284c7; }

  #tw-app .btn-secondary {
    background: #f1f5f9;
    color: #334155;
    border: 1px solid #e2e8f0;
  }
  #tw-app .btn-secondary:hover { background: #e2e8f0; }

  #tw-app .btn-success {
    background: #10b981;
    color: #fff;
  }
  #tw-app .btn-success:hover { background: #059669; }

  #tw-app .btn-danger {
    background: #f1f5f9;
    color: #64748b;
    border: 1px solid #e2e8f0;
    margin-left: auto;
  }
  #tw-app .btn-danger:hover { background: #fee2e2; color: #dc2626; border-color: #fca5a5; }

  #tw-app .tw-result-area {
    display: none;
  }
  #tw-app .tw-result-area.visible { display: block; }

  #tw-app .tw-stats {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 16px;
  }

  #tw-app .tw-stat-badge {
    background: #f0f9ff;
    border: 1px solid #bae6fd;
    border-radius: 6px;
    padding: 6px 12px;
    font-size: 13px;
    color: #0369a1;
    font-weight: 500;
  }
  #tw-app .tw-stat-badge span {
    font-weight: 700;
    color: #0284c7;
  }

  #tw-app .tw-diff {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 16px;
  }
  @media (max-width: 600px) {
    #tw-app .tw-diff { grid-template-columns: 1fr; }
  }

  #tw-app .tw-diff-box {
    border-radius: 8px;
    overflow: hidden;
  }
  #tw-app .tw-diff-label {
    padding: 8px 14px;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }
  #tw-app .tw-diff-label.before {
    background: #fef3c7;
    color: #92400e;
    border-bottom: 1px solid #fde68a;
  }
  #tw-app .tw-diff-label.after {
    background: #d1fae5;
    color: #065f46;
    border-bottom: 1px solid #6ee7b7;
  }
  #tw-app .tw-diff-content {
    padding: 12px 14px;
    font-family: "SFMono-Regular", Consolas, monospace;
    font-size: 12px;
    line-height: 1.7;
    word-break: break-all;
    min-height: 60px;
  }
  #tw-app .tw-diff-box.before .tw-diff-content {
    background: #fffbeb;
    border: 1px solid #fde68a;
    border-top: none;
    border-radius: 0 0 8px 8px;
    color: #78350f;
  }
  #tw-app .tw-diff-box.after .tw-diff-content {
    background: #f0fdf4;
    border: 1px solid #6ee7b7;
    border-top: none;
    border-radius: 0 0 8px 8px;
    color: #14532d;
  }

  #tw-app .tw-output-wrap {
    position: relative;
  }
  #tw-app .tw-output {
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

  #tw-app .tw-copy-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    padding: 5px 12px;
    font-size: 12px;
    background: #334155;
    color: #94a3b8;
    border-radius: 6px;
  }
  #tw-app .tw-copy-btn:hover { background: #475569; color: #e2e8f0; }
  #tw-app .tw-copy-btn.copied { background: #10b981; color: #fff; }

  #tw-app .tw-error {
    background: #fef2f2;
    border: 1px solid #fecaca;
    border-radius: 8px;
    padding: 12px 16px;
    color: #dc2626;
    font-size: 14px;
    margin-top: 12px;
    display: none;
  }
  #tw-app .tw-error.visible { display: block; }

  #tw-app .tw-mode-toggle {
    display: flex;
    gap: 0;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    overflow: hidden;
    width: fit-content;
    margin-bottom: 16px;
  }
  #tw-app .tw-mode-btn {
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
  #tw-app .tw-mode-btn.active {
    background: #0ea5e9;
    color: #fff;
  }
  #tw-app .tw-mode-btn:first-child { border-radius: 7px 0 0 7px; }
  #tw-app .tw-mode-btn:last-child { border-radius: 0 7px 7px 0; }

  #tw-app .tw-section-title {
    font-size: 15px;
    font-weight: 700;
    color: #0f172a;
    margin: 0 0 12px 0;
  }

  #tw-app .tw-hint {
    font-size: 12px;
    color: #94a3b8;
    margin-top: 6px;
  }
</style>

<div class="tw-card">
  <p class="tw-section-title">Input Mode</p>
  <div class="tw-mode-toggle">
    <button class="tw-mode-btn active" id="tw-mode-single" onclick="twSetMode('single')">Single Class String</button>
    <button class="tw-mode-btn" id="tw-mode-html" onclick="twSetMode('html')">HTML Elements</button>
  </div>

  <label for="tw-input" id="tw-input-label">Paste Tailwind classes</label>
  <textarea id="tw-input" placeholder="e.g. text-white font-bold p-4 flex bg-blue-500 rounded-lg shadow-md mt-2 hover:bg-blue-600 items-center justify-between" rows="5"></textarea>
  <p class="tw-hint" id="tw-input-hint">Paste a space-separated list of Tailwind utility classes.</p>

  <div class="tw-options">
    <label class="tw-checkbox-label">
      <input type="checkbox" id="tw-dedup" checked>
      Remove duplicate classes
    </label>
  </div>

  <div class="tw-btn-row">
    <button class="btn-primary" onclick="twSort()">Sort Classes</button>
    <button class="btn-secondary" onclick="twSample()">Load Sample</button>
    <button class="btn-danger" onclick="twClear()">Clear</button>
  </div>
  <div class="tw-error" id="tw-error"></div>
</div>

<div class="tw-result-area" id="tw-result-area">
  <div class="tw-card">
    <p class="tw-section-title">Results</p>
    <div class="tw-stats" id="tw-stats"></div>

    <div class="tw-diff" id="tw-diff-wrap">
      <div class="tw-diff-box before">
        <div class="tw-diff-label before">Before</div>
        <div class="tw-diff-content" id="tw-before"></div>
      </div>
      <div class="tw-diff-box after">
        <div class="tw-diff-label after">After</div>
        <div class="tw-diff-content" id="tw-after"></div>
      </div>
    </div>

    <label>Sorted Output</label>
    <div class="tw-output-wrap">
      <textarea class="tw-output" id="tw-output" readonly rows="5"></textarea>
      <button class="tw-copy-btn" id="tw-copy-btn" onclick="twCopy()">Copy</button>
    </div>
  </div>
</div>

<script>
(function() {
  // Tailwind recommended sort order — grouped by category
  // Each entry: [prefix patterns or exact names, order weight]
  // Lower weight = earlier in output

  var TW_ORDER = (function() {
    // Returns a numeric sort key for a single Tailwind class token
    var groups = [
      // 0: Layout — display
      { w: 0,   rx: /^(block|inline-block|inline|flex|inline-flex|grid|inline-grid|table|table-row|table-cell|hidden|contents|flow-root|list-item)$/ },
      // 1: Layout — container / box-sizing
      { w: 10,  rx: /^(container|box-border|box-content)$/ },
      // 2: Layout — overflow
      { w: 20,  rx: /^overflow/ },
      // 3: Layout — float / clear / isolation
      { w: 30,  rx: /^(float-|clear-|isolat)/ },
      // 4: Layout — object fit/position
      { w: 40,  rx: /^object-/ },
      // 5: Positioning — position
      { w: 100, rx: /^(static|fixed|absolute|relative|sticky)$/ },
      // 6: Positioning — inset / top / right / bottom / left / z
      { w: 110, rx: /^(inset|top-|right-|bottom-|left-|-?inset)/ },
      { w: 115, rx: /^-?(top|right|bottom|left)-/ },
      { w: 120, rx: /^z-/ },
      // 7: Visibility / opacity top-level
      { w: 130, rx: /^(visible|invisible|collapse)$/ },
      // 8: Flexbox / Grid — direction, wrap, flow
      { w: 200, rx: /^(flex-row|flex-col|flex-wrap|flex-nowrap|flex-row-reverse|flex-col-reverse|flex-wrap-reverse)$/ },
      { w: 210, rx: /^(grid-cols-|grid-rows-|grid-flow-|col-|row-|auto-cols-|auto-rows-|gap-|gap-x-|gap-y-)/ },
      // 9: Flexbox — flex-grow, shrink, basis, order
      { w: 220, rx: /^(flex-1|flex-auto|flex-initial|flex-none|grow|shrink|basis-|order-)/ },
      // 10: Alignment
      { w: 230, rx: /^(items-|justify-|content-|self-|place-|justify-items-|justify-self-)/ },
      // 11: Sizing — width
      { w: 300, rx: /^w-/ },
      { w: 305, rx: /^(min-w-|max-w-)/ },
      // 12: Sizing — height
      { w: 310, rx: /^h-/ },
      { w: 315, rx: /^(min-h-|max-h-)/ },
      // 13: Sizing — aspect ratio
      { w: 320, rx: /^aspect-/ },
      // 14: Spacing — padding
      { w: 400, rx: /^p-/ },
      { w: 402, rx: /^(px-|py-)/ },
      { w: 404, rx: /^(pt-|pr-|pb-|pl-)/ },
      // 15: Spacing — margin
      { w: 410, rx: /^-?m-/ },
      { w: 412, rx: /^-?(mx-|my-)/ },
      { w: 414, rx: /^-?(mt-|mr-|mb-|ml-)/ },
      // 16: Spacing — space between
      { w: 420, rx: /^space-/ },
      // 17: Typography — font family
      { w: 500, rx: /^font-(sans|serif|mono)$/ },
      // 18: Typography — font size
      { w: 505, rx: /^text-(xs|sm|base|lg|xl|2xl|3xl|4xl|5xl|6xl|7xl|8xl|9xl)$/ },
      // 19: Typography — font weight
      { w: 510, rx: /^font-(thin|extralight|light|normal|medium|semibold|bold|extrabold|black)$/ },
      // 20: Typography — font style / variant / smoothing
      { w: 515, rx: /^(italic|not-italic|antialiased|subpixel-antialiased|normal-nums|ordinal|slashed-zero|lining-nums|oldstyle-nums|proportional-nums|tabular-nums|diagonal-fractions|stacked-fractions)$/ },
      // 21: Typography — line height
      { w: 520, rx: /^leading-/ },
      // 22: Typography — letter spacing
      { w: 525, rx: /^tracking-/ },
      // 23: Typography — text color
      { w: 530, rx: /^text-/ },
      // 24: Typography — text align / decoration / transform / overflow
      { w: 535, rx: /^(text-left|text-center|text-right|text-justify|text-start|text-end|underline|overline|line-through|no-underline|uppercase|lowercase|capitalize|normal-case|truncate|text-ellipsis|text-clip|break-|whitespace-)/ },
      // 25: Typography — list style
      { w: 540, rx: /^list-/ },
      // 26: Typography — placeholder / caret
      { w: 545, rx: /^(placeholder-|caret-)/ },
      // 27: Background
      { w: 600, rx: /^(bg-|from-|via-|to-|bg-gradient-)/ },
      // 28: Border — radius
      { w: 700, rx: /^rounded/ },
      // 29: Border — width, style, color
      { w: 710, rx: /^border/ },
      // 30: Border — outline
      { w: 720, rx: /^outline/ },
      // 31: Border — ring
      { w: 730, rx: /^ring/ },
      // 32: Border — divide
      { w: 740, rx: /^divide/ },
      // 33: Effects — shadow
      { w: 800, rx: /^shadow/ },
      // 34: Effects — opacity
      { w: 810, rx: /^opacity-/ },
      // 35: Effects — mix-blend / background-blend
      { w: 820, rx: /^(mix-blend-|bg-blend-)/ },
      // 36: Filters
      { w: 830, rx: /^(filter|blur-|brightness-|contrast-|grayscale|hue-rotate-|invert|saturate-|sepia|drop-shadow-|backdrop-)/ },
      // 37: Transitions
      { w: 900, rx: /^(transition|duration-|ease-|delay-)/ },
      // 38: Transforms
      { w: 910, rx: /^(transform|scale-|rotate-|translate-|skew-|-rotate-|-scale-|-translate-|-skew-|origin-)/ },
      // 39: Interactivity
      { w: 1000, rx: /^(cursor-|pointer-events-|resize-?|select-|scroll-|touch-|will-change-|user-select-|appearance-|accent-color-)/ },
      // 40: Accessibility
      { w: 1100, rx: /^(sr-only|not-sr-only|focus-within:|focus-visible:|focus:|active:|group|peer)/ },
      // 41: Misc — print, etc.
      { w: 1200, rx: /^print:/ },
    ];

    return function getWeight(cls) {
      // Strip variant prefixes for matching (e.g. hover:, md:, dark:, focus:, etc.)
      // but keep the full class for output
      var base = cls.replace(/^([a-z-]+:)+/, '');

      // Variant prefix adds offset so responsive / state variants sort after base
      var variantOffset = 0;
      var variantMatch = cls.match(/^(([a-z-]+:)+)/);
      if (variantMatch) {
        var variants = variantMatch[1].split(':').filter(Boolean);
        // responsive variants
        var responsive = { sm: 1, md: 2, lg: 3, xl: 4, '2xl': 5 };
        // state variants
        var state = { hover: 0.1, focus: 0.2, active: 0.3, disabled: 0.4, dark: 0.5, group: 0.6, peer: 0.7 };
        variants.forEach(function(v) {
          if (responsive[v] !== undefined) variantOffset += responsive[v] * 10000;
          else if (state[v] !== undefined) variantOffset += state[v] * 1000;
          else variantOffset += 500;
        });
      }

      for (var i = 0; i < groups.length; i++) {
        if (groups[i].rx.test(base)) {
          return groups[i].w + variantOffset;
        }
      }
      // Unknown classes go to the end
      return 9999 + variantOffset;
    };
  })();

  var mode = 'single';

  window.twSetMode = function(m) {
    mode = m;
    document.getElementById('tw-mode-single').classList.toggle('active', m === 'single');
    document.getElementById('tw-mode-html').classList.toggle('active', m === 'html');
    var lbl = document.getElementById('tw-input-label');
    var hint = document.getElementById('tw-input-hint');
    var inp = document.getElementById('tw-input');
    if (m === 'single') {
      lbl.textContent = 'Paste Tailwind classes';
      hint.textContent = 'Paste a space-separated list of Tailwind utility classes.';
      inp.placeholder = 'e.g. text-white font-bold p-4 flex bg-blue-500 rounded-lg shadow-md mt-2 hover:bg-blue-600 items-center justify-between';
    } else {
      lbl.textContent = 'Paste HTML elements (with class="...")';
      hint.textContent = 'Paste one or more HTML elements. Each class="..." attribute will be sorted in place.';
      inp.placeholder = '<div class="text-white font-bold p-4 flex bg-blue-500 rounded-lg mt-2">\n  <button class="hover:bg-blue-600 items-center justify-between px-4 py-2 rounded text-sm font-medium">\n    Click me\n  </button>\n</div>';
    }
    document.getElementById('tw-result-area').classList.remove('visible');
    showError('');
  };

  function sortClasses(classStr, dedup) {
    var classes = classStr.trim().split(/\s+/).filter(Boolean);
    var seen = {};
    var unique = [];
    var dupCount = 0;
    classes.forEach(function(c) {
      if (dedup) {
        if (!seen[c]) { seen[c] = true; unique.push(c); }
        else dupCount++;
      } else {
        unique.push(c);
      }
    });
    unique.sort(function(a, b) {
      return TW_ORDER(a) - TW_ORDER(b);
    });
    return { sorted: unique, dupCount: dupCount, originalCount: classes.length };
  }

  function sortHtml(html, dedup) {
    var totalDups = 0;
    var totalOriginal = 0;
    var result = html.replace(/class="([^"]*)"/g, function(match, classStr) {
      var r = sortClasses(classStr, dedup);
      totalDups += r.dupCount;
      totalOriginal += r.originalCount;
      return 'class="' + r.sorted.join(' ') + '"';
    });
    result = result.replace(/class='([^']*)'/g, function(match, classStr) {
      var r = sortClasses(classStr, dedup);
      totalDups += r.dupCount;
      totalOriginal += r.originalCount;
      return "class='" + r.sorted.join(' ') + "'";
    });
    return { sorted: result, dupCount: totalDups, originalCount: totalOriginal };
  }

  function showError(msg) {
    var el = document.getElementById('tw-error');
    el.textContent = msg;
    el.classList.toggle('visible', !!msg);
  }

  window.twSort = function() {
    showError('');
    var input = document.getElementById('tw-input').value;
    if (!input.trim()) { showError('Please paste some Tailwind classes or HTML first.'); return; }
    var dedup = document.getElementById('tw-dedup').checked;

    var beforeText, afterText, outputText, totalCount, dupCount;

    if (mode === 'single') {
      var r = sortClasses(input.trim(), dedup);
      beforeText = input.trim();
      afterText = r.sorted.join(' ');
      outputText = r.sorted.join(' ');
      totalCount = r.originalCount;
      dupCount = r.dupCount;
    } else {
      var r2 = sortHtml(input, dedup);
      beforeText = input;
      afterText = r2.sorted;
      outputText = r2.sorted;
      totalCount = r2.originalCount;
      dupCount = r2.dupCount;
    }

    // Stats
    var statsHtml = '<div class="tw-stat-badge">Total classes: <span>' + totalCount + '</span></div>';
    if (dedup && dupCount > 0) {
      statsHtml += '<div class="tw-stat-badge">Duplicates removed: <span>' + dupCount + '</span></div>';
    }
    if (dedup && dupCount === 0) {
      statsHtml += '<div class="tw-stat-badge">No duplicates found</div>';
    }
    document.getElementById('tw-stats').innerHTML = statsHtml;

    // Diff
    document.getElementById('tw-before').textContent = beforeText;
    document.getElementById('tw-after').textContent = afterText;

    // Output
    document.getElementById('tw-output').value = outputText;

    // Show result
    document.getElementById('tw-result-area').classList.add('visible');

    // Reset copy button
    var copyBtn = document.getElementById('tw-copy-btn');
    copyBtn.textContent = 'Copy';
    copyBtn.classList.remove('copied');

    // Scroll to results
    document.getElementById('tw-result-area').scrollIntoView({ behavior: 'smooth', block: 'start' });
  };

  window.twCopy = function() {
    var output = document.getElementById('tw-output');
    output.select();
    try {
      document.execCommand('copy');
    } catch(e) {
      if (navigator.clipboard) navigator.clipboard.writeText(output.value);
    }
    var btn = document.getElementById('tw-copy-btn');
    btn.textContent = 'Copied!';
    btn.classList.add('copied');
    setTimeout(function() {
      btn.textContent = 'Copy';
      btn.classList.remove('copied');
    }, 2000);
  };

  window.twClear = function() {
    document.getElementById('tw-input').value = '';
    document.getElementById('tw-result-area').classList.remove('visible');
    showError('');
  };

  window.twSample = function() {
    if (mode === 'single') {
      document.getElementById('tw-input').value = 'hover:bg-blue-600 font-bold text-white flex shadow-lg p-4 rounded-xl mt-6 bg-blue-500 items-center justify-between w-full border border-blue-300 transition-colors duration-200 focus:outline-none focus:ring-2 focus:ring-blue-400 text-lg leading-tight tracking-wide opacity-100 z-10 relative overflow-hidden';
    } else {
      document.getElementById('tw-input').value = '<div class="shadow-lg flex bg-white rounded-xl p-6 mt-4 border border-gray-200 hover:shadow-xl transition-shadow duration-300 w-full max-w-md">\n  <h2 class="text-2xl font-bold text-gray-900 mb-2 leading-tight tracking-tight">\n    Card Title\n  </h2>\n  <button class="hover:bg-blue-600 mt-4 bg-blue-500 text-white font-semibold py-2 px-4 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-400 transition-colors duration-200 cursor-pointer">\n    Click me\n  </button>\n</div>';
    }
    document.getElementById('tw-result-area').classList.remove('visible');
    showError('');
  };
})();
</script>
</div>

---

### How the Sort Order Works

The sorter follows Tailwind's recommended class ordering — the same order enforced by the official [Prettier plugin for Tailwind CSS](https://tailwindcss.com/blog/automatic-class-sorting-with-prettier):

| Group | Examples |
|---|---|
| Layout | `flex`, `grid`, `block`, `hidden`, `overflow-hidden` |
| Positioning | `relative`, `absolute`, `top-0`, `z-10` |
| Sizing | `w-full`, `h-16`, `max-w-md` |
| Spacing | `p-4`, `mx-auto`, `space-x-2` |
| Typography | `text-lg`, `font-bold`, `leading-tight`, `text-gray-900` |
| Backgrounds | `bg-white`, `from-blue-500`, `bg-gradient-to-r` |
| Borders | `rounded-xl`, `border`, `ring-2` |
| Effects | `shadow-lg`, `opacity-75` |
| Transitions | `transition`, `duration-200`, `ease-in-out` |
| Transforms | `scale-95`, `rotate-3`, `translate-x-1` |
| Interactivity | `cursor-pointer`, `select-none` |

Responsive (`sm:`, `md:`, `lg:`) and state (`hover:`, `focus:`, `dark:`) variants are sorted after their base-class group.

---

### Tips

- **HTML mode** is useful when you paste a full component — every `class="..."` attribute is sorted independently.
- **Remove duplicates** is on by default. Turn it off to see the full original class list sorted.
- The sorter works entirely in your browser — no data is sent anywhere.

Related tools: [CSS Variables Generator](/tools/css-variables-generator/) · [CSS Media Query Generator](/tools/media-query-generator/)
