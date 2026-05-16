---
title: "Character Counter - Free Online Word & Character Count Tool"
date: 2026-05-16
description: "Count characters, words, sentences, and paragraphs in real time. Includes reading time estimate, keyword frequency analysis, and character limit presets for Twitter, Instagram, and more."
categories:
  - "Free Tools"
tags:
  - "character count"
  - "word count"
  - "writing"
  - "text analysis"
  - "reading time"
slug: "japanese-character-counter"
aliases: ["/en/tools/word-counter/", "/en/tools/character-counter/", "/en/tools/character-counter/"]
cover:
  image: "/images/covers/japanese-character-counter.png"
  alt: "Character Counter — Free Online Word & Character Count Tool"
ShowToc: false
---

<div id="wordcount-app">

<style>
#wordcount-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Noto Sans JP', sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 16px;
  color: #1e1b4b;
}

#wordcount-app * {
  box-sizing: border-box;
}

/* Textarea */
#wc-textarea {
  width: 100%;
  min-height: 220px;
  padding: 14px 16px;
  font-size: 15px;
  line-height: 1.7;
  border: 2px solid #c4b5fd;
  border-radius: 12px;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  background: #faf5ff;
  color: #1e1b4b;
  font-family: inherit;
}

#wc-textarea:focus {
  border-color: #7c3aed;
  background: #fff;
  box-shadow: 0 0 0 3px rgba(124,58,237,0.12);
}

/* Limit bar */
#wc-limit-bar-wrap {
  margin-top: 10px;
  display: none;
}

#wc-limit-label {
  font-size: 13px;
  color: #6d28d9;
  margin-bottom: 4px;
  display: flex;
  justify-content: space-between;
}

#wc-progress-track {
  width: 100%;
  height: 10px;
  background: #ede9fe;
  border-radius: 99px;
  overflow: hidden;
}

#wc-progress-bar {
  height: 100%;
  background: linear-gradient(90deg, #7c3aed, #a78bfa);
  border-radius: 99px;
  transition: width 0.3s, background 0.3s;
  width: 0%;
}

#wc-progress-bar.over {
  background: linear-gradient(90deg, #dc2626, #f87171);
}

/* Limit controls */
#wc-limit-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-top: 12px;
}

#wc-limit-controls label {
  font-size: 13px;
  color: #5b21b6;
  white-space: nowrap;
}

#wc-limit-input {
  width: 90px;
  padding: 5px 8px;
  border: 1px solid #c4b5fd;
  border-radius: 6px;
  font-size: 13px;
  color: #1e1b4b;
  background: #faf5ff;
  outline: none;
}

#wc-limit-input:focus {
  border-color: #7c3aed;
}

.wc-preset-btn {
  padding: 4px 10px;
  background: #ede9fe;
  color: #5b21b6;
  border: 1px solid #c4b5fd;
  border-radius: 99px;
  font-size: 12px;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
  white-space: nowrap;
}

.wc-preset-btn:hover {
  background: #7c3aed;
  color: #fff;
  border-color: #7c3aed;
}

/* Action buttons */
#wc-action-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 14px;
}

.wc-action-btn {
  padding: 7px 14px;
  border-radius: 8px;
  border: none;
  font-size: 13px;
  cursor: pointer;
  font-family: inherit;
  font-weight: 600;
  transition: background 0.15s, opacity 0.15s, transform 0.1s;
}

.wc-action-btn:active {
  transform: scale(0.97);
}

.wc-btn-primary {
  background: #7c3aed;
  color: #fff;
}

.wc-btn-primary:hover {
  background: #6d28d9;
}

.wc-btn-secondary {
  background: #ede9fe;
  color: #5b21b6;
}

.wc-btn-secondary:hover {
  background: #ddd6fe;
}

.wc-btn-danger {
  background: #fee2e2;
  color: #b91c1c;
}

.wc-btn-danger:hover {
  background: #fecaca;
}

/* Stats grid */
#wc-stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 12px;
  margin-top: 20px;
}

.wc-stat-card {
  background: linear-gradient(135deg, #faf5ff 0%, #ede9fe 100%);
  border: 1px solid #c4b5fd;
  border-radius: 12px;
  padding: 14px 16px;
  text-align: center;
  transition: box-shadow 0.2s, transform 0.2s;
}

.wc-stat-card:hover {
  box-shadow: 0 4px 16px rgba(124,58,237,0.15);
  transform: translateY(-2px);
}

.wc-stat-label {
  font-size: 11px;
  color: #6d28d9;
  font-weight: 600;
  letter-spacing: 0.03em;
  margin-bottom: 6px;
  text-transform: uppercase;
}

.wc-stat-value {
  font-size: 26px;
  font-weight: 700;
  color: #7c3aed;
  line-height: 1.1;
}

.wc-stat-unit {
  font-size: 11px;
  color: #8b5cf6;
  margin-top: 3px;
}

/* Section title */
.wc-section-title {
  font-size: 14px;
  font-weight: 700;
  color: #5b21b6;
  margin: 24px 0 10px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.wc-section-title::before {
  content: '';
  display: inline-block;
  width: 4px;
  height: 16px;
  background: #7c3aed;
  border-radius: 2px;
}

/* Frequency table */
#wc-freq-table-wrap {
  overflow-x: auto;
}

#wc-freq-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}

#wc-freq-table th {
  background: #7c3aed;
  color: #fff;
  padding: 8px 12px;
  text-align: left;
  font-weight: 600;
}

#wc-freq-table th:first-child { border-radius: 8px 0 0 0; }
#wc-freq-table th:last-child  { border-radius: 0 8px 0 0; }

#wc-freq-table td {
  padding: 8px 12px;
  border-bottom: 1px solid #ede9fe;
  color: #1e1b4b;
}

#wc-freq-table tr:nth-child(even) td {
  background: #faf5ff;
}

#wc-freq-table tr:hover td {
  background: #ede9fe;
}

.wc-freq-bar-cell {
  width: 140px;
}

.wc-freq-bar-bg {
  background: #ede9fe;
  border-radius: 99px;
  height: 8px;
  overflow: hidden;
}

.wc-freq-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #7c3aed, #a78bfa);
  border-radius: 99px;
  transition: width 0.4s;
}

/* Toast */
#wc-toast {
  position: fixed;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #1e1b4b;
  color: #fff;
  padding: 10px 24px;
  border-radius: 99px;
  font-size: 14px;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s, transform 0.3s;
  z-index: 9999;
  white-space: nowrap;
}

#wc-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

/* Responsive */
@media (max-width: 600px) {
  #wc-stats-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 8px;
  }
  .wc-stat-value { font-size: 20px; }
  #wc-action-row { gap: 6px; }
  .wc-action-btn { font-size: 12px; padding: 6px 10px; }
}
</style>

<!-- Textarea -->
<textarea id="wc-textarea" placeholder="Type or paste your text here. Character count, word count, reading time, and more are calculated in real time."></textarea>

<!-- Character limit bar -->
<div id="wc-limit-bar-wrap">
  <div id="wc-limit-label">
    <span id="wc-limit-text">Character limit: 0 / 0</span>
    <span id="wc-limit-over" style="color:#dc2626;display:none;">Limit exceeded</span>
  </div>
  <div id="wc-progress-track"><div id="wc-progress-bar"></div></div>
</div>

<!-- Limit controls -->
<div id="wc-limit-controls">
  <label>Character limit:</label>
  <input type="number" id="wc-limit-input" placeholder="Max chars" min="1" />
  <button class="wc-preset-btn" data-limit="280">Twitter/X (280)</button>
  <button class="wc-preset-btn" data-limit="2200">Instagram (2200)</button>
  <button class="wc-preset-btn" data-limit="60">Blog Title (60)</button>
  <button class="wc-preset-btn" data-limit="160">Meta Description (160)</button>
  <button class="wc-preset-btn" data-limit="500">LinkedIn Post (500)</button>
  <button class="wc-preset-btn" data-limit="0">No Limit</button>
</div>

<!-- Action buttons -->
<div id="wc-action-row">
  <button class="wc-action-btn wc-btn-primary" id="wc-copy-btn">Copy</button>
  <button class="wc-action-btn wc-btn-secondary" id="wc-upper-btn">UPPERCASE</button>
  <button class="wc-action-btn wc-btn-secondary" id="wc-lower-btn">lowercase</button>
  <button class="wc-action-btn wc-btn-secondary" id="wc-title-btn">Title Case</button>
  <button class="wc-action-btn wc-btn-danger" id="wc-clear-btn">Clear</button>
</div>

<!-- Stats grid -->
<div id="wc-stats-grid">
  <div class="wc-stat-card">
    <div class="wc-stat-label">Characters (with spaces)</div>
    <div class="wc-stat-value" id="wc-chars-with">0</div>
    <div class="wc-stat-unit">incl. spaces</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Characters (no spaces)</div>
    <div class="wc-stat-value" id="wc-chars-without">0</div>
    <div class="wc-stat-unit">excl. spaces</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Words</div>
    <div class="wc-stat-value" id="wc-words">0</div>
    <div class="wc-stat-unit">words</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Sentences</div>
    <div class="wc-stat-value" id="wc-sentences">0</div>
    <div class="wc-stat-unit">sentences</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Paragraphs</div>
    <div class="wc-stat-value" id="wc-paragraphs">0</div>
    <div class="wc-stat-unit">paragraphs</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Reading Time</div>
    <div class="wc-stat-value" id="wc-read-time">0</div>
    <div class="wc-stat-unit">min (200 wpm)</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Speaking Time</div>
    <div class="wc-stat-value" id="wc-speech-time">0</div>
    <div class="wc-stat-unit">min (130 wpm)</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-label">Byte Size</div>
    <div class="wc-stat-value" id="wc-bytes">0</div>
    <div class="wc-stat-unit">bytes (UTF-8)</div>
  </div>
</div>

<!-- Keyword frequency -->
<div class="wc-section-title">Top 10 Keywords by Frequency</div>
<div id="wc-freq-table-wrap">
  <table id="wc-freq-table">
    <thead>
      <tr>
        <th>Rank</th>
        <th>Keyword</th>
        <th>Count</th>
        <th class="wc-freq-bar-cell">Frequency</th>
      </tr>
    </thead>
    <tbody id="wc-freq-tbody">
      <tr><td colspan="4" style="color:#8b5cf6;text-align:center;padding:16px;">Enter text above to see keyword frequency</td></tr>
    </tbody>
  </table>
</div>

<!-- Toast -->
<div id="wc-toast">Copied to clipboard</div>

<script>
(function() {
  var ta = document.getElementById('wc-textarea');
  var limitInput = document.getElementById('wc-limit-input');
  var limitBarWrap = document.getElementById('wc-limit-bar-wrap');
  var limitText = document.getElementById('wc-limit-text');
  var limitOver = document.getElementById('wc-limit-over');
  var progressBar = document.getElementById('wc-progress-bar');
  var toast = document.getElementById('wc-toast');
  var currentLimit = 0;

  // English stop words
  var stopWords = new Set([
    'a','an','the','is','are','was','were','be','been','being','have','has','had',
    'do','does','did','will','would','could','should','may','might','shall',
    'and','or','but','if','in','on','at','to','for','of','with','by','from',
    'this','that','these','those','it','its','we','our','you','your','they',
    'their','i','my','me','he','she','his','her','him','us','not','no','so',
    'up','out','as','into','about','than','then','when','where','which','who',
    'what','how','all','each','every','both','few','more','most','other','some',
    'such','only','own','same','too','very','just','because','while','through',
    // Japanese stop words
    'の','に','は','を','た','が','で','て','と','し','れ','さ','ある','いる','も',
    'する','から','な','こと','として','い','や','れる','など','なり','ない','この',
    'ため','その','あ','さ','せ','で','た','どの','という','とき','また','や'
  ]);

  // Byte length
  function getByteLength(str) {
    var b = 0;
    for (var i = 0; i < str.length; i++) {
      var c = str.charCodeAt(i);
      if (c <= 0x7F) b += 1;
      else if (c <= 0x7FF) b += 2;
      else if (c <= 0xFFFF) b += 3;
      else b += 4;
    }
    return b;
  }

  // Tokenize (English words + Japanese CJK blocks)
  function tokenize(text) {
    var tokens = [];
    var en = text.match(/[a-zA-Z0-9]+/g) || [];
    tokens = tokens.concat(en);
    var ja = text.match(/[\u3040-\u309f\u30a0-\u30ff\u4e00-\u9fff\uff66-\uff9f]{2,}/g) || [];
    tokens = tokens.concat(ja);
    return tokens;
  }

  // Keyword frequency
  function getFrequency(text) {
    var tokens = tokenize(text);
    var freq = {};
    for (var i = 0; i < tokens.length; i++) {
      var w = tokens[i].toLowerCase();
      if (stopWords.has(w)) continue;
      if (w.length < 2) continue;
      freq[w] = (freq[w] || 0) + 1;
    }
    var arr = Object.keys(freq).map(function(k) { return { word: k, count: freq[k] }; });
    arr.sort(function(a, b) { return b.count - a.count; });
    return arr.slice(0, 10);
  }

  // Count paragraphs
  function countParagraphs(text) {
    if (!text.trim()) return 0;
    var paras = text.split(/\n\s*\n/).filter(function(p) { return p.trim().length > 0; });
    return paras.length || (text.trim() ? 1 : 0);
  }

  // Count sentences
  function countSentences(text) {
    if (!text.trim()) return 0;
    var matches = text.match(/[.!?]+/g);
    return matches ? matches.length : (text.trim() ? 1 : 0);
  }

  // Count words
  function countWords(text) {
    if (!text.trim()) return 0;
    var enWords = (text.match(/[a-zA-Z0-9]+(?:['\-][a-zA-Z0-9]+)*/g) || []).length;
    var jaSegments = (text.match(/[\u3040-\u309f\u30a0-\u30ff\u4e00-\u9fff\uff66-\uff9f]+/g) || []);
    var jaCount = 0;
    for (var i = 0; i < jaSegments.length; i++) {
      jaCount += Math.ceil(jaSegments[i].length / 3);
    }
    return enWords + jaCount;
  }

  // Format time
  function formatTime(minutes) {
    if (minutes < 1) return '< 1';
    return Math.ceil(minutes).toString();
  }

  // Update stats
  function updateStats() {
    var text = ta.value;
    var withSpaces = text.length;
    var withoutSpaces = text.replace(/\s/g, '').length;
    var words = countWords(text);
    var sentences = countSentences(text);
    var paragraphs = countParagraphs(text);
    var readMin = words / 200;
    var speechMin = words / 130;
    var bytes = getByteLength(text);

    document.getElementById('wc-chars-with').textContent = withSpaces.toLocaleString();
    document.getElementById('wc-chars-without').textContent = withoutSpaces.toLocaleString();
    document.getElementById('wc-words').textContent = words.toLocaleString();
    document.getElementById('wc-sentences').textContent = sentences.toLocaleString();
    document.getElementById('wc-paragraphs').textContent = paragraphs.toLocaleString();
    document.getElementById('wc-read-time').textContent = formatTime(readMin);
    document.getElementById('wc-speech-time').textContent = formatTime(speechMin);
    document.getElementById('wc-bytes').textContent = bytes.toLocaleString();

    // Limit bar
    if (currentLimit > 0) {
      var pct = Math.min((withSpaces / currentLimit) * 100, 100);
      progressBar.style.width = pct + '%';
      limitText.textContent = 'Character limit: ' + withSpaces.toLocaleString() + ' / ' + currentLimit.toLocaleString();
      if (withSpaces > currentLimit) {
        progressBar.classList.add('over');
        limitOver.style.display = 'inline';
      } else {
        progressBar.classList.remove('over');
        limitOver.style.display = 'none';
      }
    }

    updateFreqTable(text);
  }

  // Update frequency table
  function updateFreqTable(text) {
    var tbody = document.getElementById('wc-freq-tbody');
    var freq = getFrequency(text);
    if (freq.length === 0) {
      tbody.innerHTML = '<tr><td colspan="4" style="color:#8b5cf6;text-align:center;padding:16px;">Enter text above to see keyword frequency</td></tr>';
      return;
    }
    var maxCount = freq[0].count;
    var html = '';
    for (var i = 0; i < freq.length; i++) {
      var pct = maxCount > 0 ? Math.round((freq[i].count / maxCount) * 100) : 0;
      html += '<tr>'
        + '<td style="color:#8b5cf6;font-weight:700;">' + (i + 1) + '</td>'
        + '<td style="font-weight:600;">' + escHtml(freq[i].word) + '</td>'
        + '<td style="color:#7c3aed;font-weight:700;">' + freq[i].count + '</td>'
        + '<td class="wc-freq-bar-cell"><div class="wc-freq-bar-bg"><div class="wc-freq-bar-fill" style="width:' + pct + '%"></div></div></td>'
        + '</tr>';
    }
    tbody.innerHTML = html;
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  // Real-time update
  ta.addEventListener('input', updateStats);

  // Limit input
  limitInput.addEventListener('input', function() {
    var v = parseInt(limitInput.value, 10);
    currentLimit = (isNaN(v) || v <= 0) ? 0 : v;
    limitBarWrap.style.display = currentLimit > 0 ? 'block' : 'none';
    updateStats();
  });

  // Preset buttons
  document.querySelectorAll('.wc-preset-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var lim = parseInt(btn.getAttribute('data-limit'), 10);
      currentLimit = lim;
      limitInput.value = lim > 0 ? lim : '';
      limitBarWrap.style.display = currentLimit > 0 ? 'block' : 'none';
      updateStats();
    });
  });

  // Copy
  document.getElementById('wc-copy-btn').addEventListener('click', function() {
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

  function showToast() {
    toast.classList.add('show');
    setTimeout(function() { toast.classList.remove('show'); }, 2000);
  }

  // Clear
  document.getElementById('wc-clear-btn').addEventListener('click', function() {
    ta.value = '';
    updateStats();
    ta.focus();
  });

  // UPPERCASE
  document.getElementById('wc-upper-btn').addEventListener('click', function() {
    ta.value = ta.value.toUpperCase();
    updateStats();
  });

  // lowercase
  document.getElementById('wc-lower-btn').addEventListener('click', function() {
    ta.value = ta.value.toLowerCase();
    updateStats();
  });

  // Title Case
  document.getElementById('wc-title-btn').addEventListener('click', function() {
    ta.value = ta.value.replace(/\w\S*/g, function(w) {
      return w.charAt(0).toUpperCase() + w.slice(1).toLowerCase();
    });
    updateStats();
  });

  // Init
  updateStats();
})();
</script>

</div>

---

## How to Use This Tool

Paste or type any text into the box above. Character count, word count, reading time, and all other statistics update instantly as you type. The tool supports both English and Japanese text (CJK character detection included).

Use the character limit mode to check against platform restrictions — simply click a preset (Twitter/X 280, Meta Description 160, etc.) or enter your own limit. A progress bar will show how close you are to the ceiling.

The keyword frequency table filters out common stop words and ranks meaningful terms by how often they appear — useful for checking SEO keyword density or spotting unintentional repetition.

---

## Why Character Count Matters

Every platform has different constraints. Twitter/X allows 280 characters, Instagram captions get truncated after a certain length, and Google typically displays 50–60 characters of a page title in search results. Knowing your exact character count before publishing prevents truncation surprises.

For academic and business writing, many submissions require a word or character count within a specific range. This tool supports both characters-with-spaces and characters-without-spaces counts to match any submission guideline.

Reading time and speaking time estimates help you calibrate content length for your audience — whether you're writing a 5-minute blog post or a 10-minute speech.

---

## Related Tools

> Stay focused while writing -> [Compound Interest Calculator](/en/tools/compound-interest-calculator/)

> Calculate percentages instantly -> [Percentage Calculator](/en/tools/percentage-calculator/)

> Simulate your NISA investment growth -> [NISA Investment Simulator](/en/tools/nisa-investment-simulator/)
