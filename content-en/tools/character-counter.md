---
title: "Character Counter - Text Length Analyzer"
date: 2025-05-16
description: "Free character counter tool. Count characters, words, sentences, paragraphs with/without spaces. Check Twitter (280), SMS (160), and custom limits. UTF-8 byte size."
categories: ["Free Tools"]
tags: ["character counter", "text length", "twitter character count", "sms limit", "utf-8 bytes", "text analyzer"]
slug: "character-counter"
cover:
  image: "/images/covers/character-counter.png"
  alt: "Character Counter - Text Length Analyzer"
ShowToc: false
---

<div id="cc-app">

<style>
#cc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 880px;
  margin: 0 auto;
  color: #1e1b4b;
}

#cc-app * {
  box-sizing: border-box;
}

#cc-textarea {
  width: 100%;
  min-height: 200px;
  padding: 16px;
  font-size: 1rem;
  line-height: 1.6;
  border: 2px solid #c4b5fd;
  border-radius: 10px;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  background: #faf5ff;
  color: #1e1b4b;
  font-family: inherit;
}
#cc-textarea:focus {
  border-color: #7c3aed;
  background: #fff;
  box-shadow: 0 0 0 3px rgba(124,58,237,0.1);
}
#cc-textarea::placeholder { color: #a78bfa; }

#cc-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 10px;
}
#cc-app button {
  padding: 7px 14px;
  border: none;
  border-radius: 6px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  font-family: inherit;
}
#cc-app button:active { transform: scale(0.97); }

.cc-btn-primary { background: #7c3aed; color: #fff; }
.cc-btn-primary:hover { background: #6d28d9; }
.cc-btn-secondary { background: #ede9fe; color: #5b21b6; }
.cc-btn-secondary:hover { background: #ddd6fe; }
.cc-btn-danger { background: #fee2e2; color: #b91c1c; }
.cc-btn-danger:hover { background: #fecaca; }

/* Custom limit row */
#cc-limit-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 12px;
  flex-wrap: wrap;
}
#cc-limit-row label {
  font-size: 0.85rem;
  color: #5b21b6;
  font-weight: 600;
  white-space: nowrap;
}
#cc-limit-input {
  width: 100px;
  padding: 6px 10px;
  border: 2px solid #c4b5fd;
  border-radius: 6px;
  font-size: 0.85rem;
  color: #1e1b4b;
  outline: none;
  font-family: inherit;
}
#cc-limit-input:focus { border-color: #7c3aed; }

/* Custom limit progress */
#cc-custom-progress-wrap {
  margin-top: 8px;
  display: none;
}
#cc-custom-progress-label {
  font-size: 0.8rem;
  color: #5b21b6;
  margin-bottom: 4px;
  display: flex;
  justify-content: space-between;
}
#cc-custom-progress-bg {
  width: 100%;
  height: 10px;
  background: #ede9fe;
  border-radius: 999px;
  overflow: hidden;
}
#cc-custom-progress-bar {
  height: 100%;
  background: #7c3aed;
  border-radius: 999px;
  transition: width 0.2s, background 0.2s;
  width: 0%;
}
#cc-custom-progress-bar.warn { background: #f59e0b; }
#cc-custom-progress-bar.over { background: #ef4444; }

/* Stats grid */
#cc-stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(138px, 1fr));
  gap: 12px;
  margin-top: 20px;
}
.cc-stat-card {
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  border-radius: 10px;
  padding: 14px 10px;
  text-align: center;
}
.cc-stat-value {
  font-size: 1.7rem;
  font-weight: 700;
  color: #7c3aed;
  line-height: 1;
  word-break: break-all;
}
.cc-stat-label {
  font-size: 0.72rem;
  color: #6b7280;
  margin-top: 6px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

/* Platform limit bars */
#cc-platform-section {
  margin-top: 28px;
}
#cc-platform-section h3 {
  font-size: 0.9rem;
  font-weight: 700;
  color: #5b21b6;
  margin: 0 0 14px 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.cc-platform-row {
  margin-bottom: 12px;
}
.cc-platform-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 4px;
}
.cc-platform-name {
  font-size: 0.85rem;
  font-weight: 600;
  color: #374151;
}
.cc-platform-count {
  font-size: 0.82rem;
  color: #6b7280;
  font-variant-numeric: tabular-nums;
}
.cc-platform-count.over { color: #ef4444; font-weight: 700; }
.cc-platform-track {
  width: 100%;
  height: 8px;
  background: #ede9fe;
  border-radius: 999px;
  overflow: hidden;
}
.cc-platform-bar {
  height: 100%;
  border-radius: 999px;
  transition: width 0.25s, background 0.25s;
  width: 0%;
  background: linear-gradient(90deg, #7c3aed, #a78bfa);
}
.cc-platform-bar.warn { background: linear-gradient(90deg, #f59e0b, #fbbf24); }
.cc-platform-bar.over { background: linear-gradient(90deg, #ef4444, #f87171); }

/* Character density chart */
#cc-density-section {
  margin-top: 28px;
}
#cc-density-section h3 {
  font-size: 0.9rem;
  font-weight: 700;
  color: #5b21b6;
  margin: 0 0 14px 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
#cc-density-canvas {
  width: 100%;
  max-width: 100%;
  border-radius: 8px;
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  display: block;
}
#cc-density-empty {
  text-align: center;
  color: #a78bfa;
  font-size: 0.9rem;
  padding: 24px;
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  border-radius: 8px;
}

/* Toast */
#cc-toast {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #7c3aed;
  color: #fff;
  padding: 10px 22px;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  opacity: 0;
  transition: opacity 0.3s, transform 0.3s;
  pointer-events: none;
  z-index: 9999;
}
#cc-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

@media (max-width: 500px) {
  #cc-stats-grid { grid-template-columns: repeat(2, 1fr); }
}
</style>

<textarea id="cc-textarea" placeholder="Paste or type your text here — stats update in real time..."></textarea>

<div id="cc-actions">
  <button class="cc-btn-primary" id="cc-copy-btn">Copy Text</button>
  <button class="cc-btn-danger" id="cc-clear-btn">Clear</button>
</div>

<div id="cc-limit-row">
  <label for="cc-limit-input">Custom limit:</label>
  <input type="number" id="cc-limit-input" min="1" placeholder="e.g. 500">
  <span style="font-size:0.8rem;color:#8b5cf6;">characters</span>
</div>

<div id="cc-custom-progress-wrap">
  <div id="cc-custom-progress-label">
    <span id="cc-custom-progress-text">0 / 0</span>
    <span id="cc-custom-progress-over" style="color:#ef4444;display:none;">Over limit!</span>
  </div>
  <div id="cc-custom-progress-bg">
    <div id="cc-custom-progress-bar"></div>
  </div>
</div>

<!-- Stats grid -->
<div id="cc-stats-grid">
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-chars-with">0</div>
    <div class="cc-stat-label">Characters (with spaces)</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-chars-without">0</div>
    <div class="cc-stat-label">Characters (no spaces)</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-words">0</div>
    <div class="cc-stat-label">Words</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-sentences">0</div>
    <div class="cc-stat-label">Sentences</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-paragraphs">0</div>
    <div class="cc-stat-label">Paragraphs</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-lines">0</div>
    <div class="cc-stat-label">Lines</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-unique">0</div>
    <div class="cc-stat-label">Unique Characters</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-bytes">0</div>
    <div class="cc-stat-label">UTF-8 Bytes</div>
  </div>
</div>

<!-- Platform limit bars -->
<div id="cc-platform-section">
  <h3>Platform Character Limits</h3>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">X / Twitter</span>
      <span class="cc-platform-count" id="cc-plat-twitter-label">0 / 280</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-twitter-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">SMS (standard)</span>
      <span class="cc-platform-count" id="cc-plat-sms-label">0 / 160</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-sms-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">Meta Description</span>
      <span class="cc-platform-count" id="cc-plat-meta-label">0 / 160</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-meta-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">Title Tag (SEO)</span>
      <span class="cc-platform-count" id="cc-plat-title-label">0 / 60</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-title-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">Instagram Caption</span>
      <span class="cc-platform-count" id="cc-plat-ig-label">0 / 2200</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-ig-bar"></div></div>
  </div>
</div>

<!-- Character density chart -->
<div id="cc-density-section">
  <h3>Top 10 Character Frequency</h3>
  <div id="cc-density-empty">Type text above to see character frequency chart</div>
  <canvas id="cc-density-canvas" style="display:none;" height="220"></canvas>
</div>

<div id="cc-toast">Copied to clipboard!</div>

<script>
(function() {
  var ta = document.getElementById('cc-textarea');
  var limitInput = document.getElementById('cc-limit-input');
  var customProgressWrap = document.getElementById('cc-custom-progress-wrap');
  var customProgressText = document.getElementById('cc-custom-progress-text');
  var customProgressOver = document.getElementById('cc-custom-progress-over');
  var customBar = document.getElementById('cc-custom-progress-bar');
  var toast = document.getElementById('cc-toast');
  var canvas = document.getElementById('cc-density-canvas');
  var densityEmpty = document.getElementById('cc-density-empty');
  var ctx = canvas.getContext('2d');
  var customLimit = 0;

  var platforms = [
    { id: 'twitter', limit: 280 },
    { id: 'sms',     limit: 160 },
    { id: 'meta',    limit: 160 },
    { id: 'title',   limit: 60  },
    { id: 'ig',      limit: 2200 }
  ];

  function getUtf8Bytes(str) {
    var bytes = 0;
    for (var i = 0; i < str.length; i++) {
      var code = str.charCodeAt(i);
      if (code < 0x80) bytes += 1;
      else if (code < 0x800) bytes += 2;
      else if (code >= 0xD800 && code <= 0xDBFF) { bytes += 4; i++; }
      else bytes += 3;
    }
    return bytes;
  }

  function countWords(text) {
    var t = text.trim();
    if (!t) return 0;
    return t.split(/\s+/).filter(function(w) { return w.length > 0; }).length;
  }

  function countSentences(text) {
    var t = text.trim();
    if (!t) return 0;
    var matches = t.match(/[^.!?]*[.!?]+/g);
    return matches ? matches.length : (t.length > 0 ? 1 : 0);
  }

  function countParagraphs(text) {
    var t = text.trim();
    if (!t) return 0;
    return t.split(/\n\s*\n/).filter(function(p) { return p.trim().length > 0; }).length;
  }

  function countLines(text) {
    if (!text) return 0;
    return text.split('\n').length;
  }

  function countUnique(text) {
    if (!text) return 0;
    var seen = {};
    for (var i = 0; i < text.length; i++) {
      seen[text[i]] = true;
    }
    return Object.keys(seen).length;
  }

  function getCharFrequency(text) {
    var freq = {};
    for (var i = 0; i < text.length; i++) {
      var c = text[i];
      if (c === ' ' || c === '\n' || c === '\r' || c === '\t') continue;
      freq[c] = (freq[c] || 0) + 1;
    }
    var arr = [];
    for (var ch in freq) {
      arr.push({ char: ch, count: freq[ch] });
    }
    arr.sort(function(a, b) { return b.count - a.count; });
    return arr.slice(0, 10);
  }

  function updatePlatformBar(id, count, limit) {
    var labelEl = document.getElementById('cc-plat-' + id + '-label');
    var barEl = document.getElementById('cc-plat-' + id + '-bar');
    var pct = Math.min((count / limit) * 100, 100);
    barEl.style.width = pct + '%';
    labelEl.textContent = count.toLocaleString() + ' / ' + limit.toLocaleString();
    if (count > limit) {
      barEl.className = 'cc-platform-bar over';
      labelEl.className = 'cc-platform-count over';
    } else if (pct >= 80) {
      barEl.className = 'cc-platform-bar warn';
      labelEl.className = 'cc-platform-count';
    } else {
      barEl.className = 'cc-platform-bar';
      labelEl.className = 'cc-platform-count';
    }
  }

  function drawDensityChart(freq) {
    if (freq.length === 0) {
      canvas.style.display = 'none';
      densityEmpty.style.display = 'block';
      return;
    }
    densityEmpty.style.display = 'none';
    canvas.style.display = 'block';

    var dpr = window.devicePixelRatio || 1;
    var w = canvas.parentElement.clientWidth || 600;
    canvas.width = w * dpr;
    canvas.height = 220 * dpr;
    canvas.style.width = w + 'px';
    canvas.style.height = '220px';
    ctx.scale(dpr, dpr);

    var padL = 44, padR = 16, padT = 20, padB = 48;
    var chartW = w - padL - padR;
    var chartH = 220 - padT - padB;
    var barCount = freq.length;
    var barW = Math.floor((chartW / barCount) * 0.65);
    var gap = Math.floor(chartW / barCount);
    var maxCount = freq[0].count;

    ctx.clearRect(0, 0, w, 220);

    // Grid lines
    ctx.strokeStyle = '#ddd6fe';
    ctx.lineWidth = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = padT + (chartH / 4) * g;
      ctx.beginPath();
      ctx.moveTo(padL, gy);
      ctx.lineTo(padL + chartW, gy);
      ctx.stroke();
      var gridVal = Math.round(maxCount * (1 - g / 4));
      ctx.fillStyle = '#8b5cf6';
      ctx.font = '10px -apple-system,sans-serif';
      ctx.textAlign = 'right';
      ctx.fillText(gridVal, padL - 4, gy + 4);
    }

    // Bars
    var colors = ['#7c3aed','#8b5cf6','#a78bfa','#6d28d9','#9333ea','#7c3aed','#8b5cf6','#a78bfa','#6d28d9','#9333ea'];
    for (var i = 0; i < freq.length; i++) {
      var bh = maxCount > 0 ? (freq[i].count / maxCount) * chartH : 0;
      var bx = padL + i * gap + (gap - barW) / 2;
      var by = padT + chartH - bh;

      ctx.fillStyle = colors[i % colors.length];
      ctx.beginPath();
      ctx.roundRect ? ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]) : ctx.rect(bx, by, barW, bh);
      ctx.fill();

      // Count label on bar
      ctx.fillStyle = '#5b21b6';
      ctx.font = 'bold 10px -apple-system,sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText(freq[i].count, bx + barW / 2, by - 4);

      // Char label below
      ctx.fillStyle = '#374151';
      ctx.font = 'bold 13px -apple-system,sans-serif';
      ctx.fillText(freq[i].char, bx + barW / 2, padT + chartH + 18);

      // Hex label
      var code = freq[i].char.codePointAt(0).toString(16).toUpperCase();
      ctx.fillStyle = '#9ca3af';
      ctx.font = '9px -apple-system,sans-serif';
      ctx.fillText('U+' + code.padStart(4, '0'), bx + barW / 2, padT + chartH + 32);
    }
  }

  function updateStats() {
    var text = ta.value;
    var withSpaces = text.length;
    var withoutSpaces = text.replace(/\s/g, '').length;
    var words = countWords(text);
    var sentences = countSentences(text);
    var paragraphs = countParagraphs(text);
    var lines = countLines(text);
    var unique = countUnique(text);
    var bytes = getUtf8Bytes(text);

    document.getElementById('cc-chars-with').textContent = withSpaces.toLocaleString();
    document.getElementById('cc-chars-without').textContent = withoutSpaces.toLocaleString();
    document.getElementById('cc-words').textContent = words.toLocaleString();
    document.getElementById('cc-sentences').textContent = sentences.toLocaleString();
    document.getElementById('cc-paragraphs').textContent = paragraphs.toLocaleString();
    document.getElementById('cc-lines').textContent = lines.toLocaleString();
    document.getElementById('cc-unique').textContent = unique.toLocaleString();
    document.getElementById('cc-bytes').textContent = bytes.toLocaleString();

    // Platform bars
    platforms.forEach(function(p) {
      updatePlatformBar(p.id, withSpaces, p.limit);
    });

    // Custom limit
    if (customLimit > 0) {
      var pct = Math.min((withSpaces / customLimit) * 100, 100);
      customBar.style.width = pct + '%';
      customProgressText.textContent = withSpaces.toLocaleString() + ' / ' + customLimit.toLocaleString();
      if (withSpaces > customLimit) {
        customBar.className = 'over';
        customProgressOver.style.display = 'inline';
      } else if (pct >= 80) {
        customBar.className = 'warn';
        customProgressOver.style.display = 'none';
      } else {
        customBar.className = '';
        customProgressOver.style.display = 'none';
      }
    }

    // Character density chart
    var freq = getCharFrequency(text);
    drawDensityChart(freq);
  }

  function showToast() {
    toast.classList.add('show');
    setTimeout(function() { toast.classList.remove('show'); }, 2000);
  }

  ta.addEventListener('input', updateStats);

  limitInput.addEventListener('input', function() {
    var v = parseInt(limitInput.value, 10);
    customLimit = (isNaN(v) || v <= 0) ? 0 : v;
    if (customLimit > 0) {
      customProgressWrap.style.display = 'block';
    } else {
      customProgressWrap.style.display = 'none';
    }
    updateStats();
  });

  document.getElementById('cc-copy-btn').addEventListener('click', function() {
    var text = ta.value;
    if (!text) return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(showToast);
    } else {
      ta.select();
      document.execCommand('copy');
      showToast();
    }
  });

  document.getElementById('cc-clear-btn').addEventListener('click', function() {
    ta.value = '';
    updateStats();
    ta.focus();
  });

  window.addEventListener('resize', function() {
    var freq = getCharFrequency(ta.value);
    drawDensityChart(freq);
  });

  updateStats();
})();
</script>

</div>

---

## How to Use the Character Counter

Paste or type any text into the box above — all statistics update instantly. There is nothing to submit or install; everything runs in your browser.

**Characters with spaces** counts every character including whitespace. This is what most platform limits (Twitter, SMS, meta descriptions) measure. **Characters without spaces** strips all whitespace first, useful for academic or legal requirements that specify "characters excluding spaces."

The **platform limit bars** turn amber at 80% and red when you exceed the limit, so you can see at a glance whether your text fits. Enter any number in the **Custom Limit** field to track your own target — a house style guide, a form field maximum, or a client brief.

The **character frequency chart** shows the top 10 non-whitespace characters by count, with their Unicode code points displayed below each bar. This is handy for spotting repeated filler words rendered as single characters, checking whether an unusual glyph crept into your text, or simply satisfying curiosity about your writing patterns.

---

## Why Character Counts Matter

**Twitter / X** enforces a 280-character limit per post. Unlike older counting methods, Twitter counts most Unicode characters — including CJK ideographs — as a single character. Staying under the limit before you paste into the app saves the frustration of a last-second trim.

**SMS** uses 160 characters for a single segment in GSM-7 encoding. If your message includes any character outside GSM-7 (such as curly quotes, em dashes, or emoji), the encoding automatically switches to UCS-2 and the segment limit drops to 70 characters. The UTF-8 byte counter on this page can help you catch unexpected multi-byte characters before sending.

**SEO title tags** are typically truncated in search results at around 60 characters. Meta descriptions display up to about 160 characters. Keeping within these ranges prevents Google from rewriting your snippets and helps users understand what your page is about before they click.

**UTF-8 byte size** matters whenever you are writing to a database column defined in bytes rather than characters, sending text over a size-limited API, or generating files where byte count affects storage or processing costs. A plain ASCII character is 1 byte; a CJK character or emoji is typically 3–4 bytes.

---

## Related Tools

> Need to count words and estimate reading time? [Word Counter](/tools/word-counter/)

> Analyze which words appear most often in your text: [Word Frequency Counter](/tools/word-frequency-counter/)

> Calculate how long it takes to read your article: [Reading Time Calculator](/tools/reading-time-calculator/)
