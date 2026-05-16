---
title: "Word Counter - Free Online Character & Word Count Tool"
date: 2025-05-16
description: "Count words, characters, sentences, and paragraphs instantly. Reading time estimate, keyword density analysis, and more. Free online writing tool."
categories: ["Free Tools"]
tags: ["word counter", "character counter", "writing tool", "text analysis", "reading time"]
slug: "word-counter"
aliases: ["/tools/character-counter/", "/tools/text-counter/", "/tools/letter-counter/"]
cover:
  image: "/images/covers/word-counter.png"
  alt: "Word Counter"
ShowToc: false
---

<div id="wordcount-app">

<style>
#wordcount-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1e1b4b;
}

#wordcount-app * {
  box-sizing: border-box;
}

/* Textarea */
#wc-textarea {
  width: 100%;
  min-height: 220px;
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
}
#wc-textarea:focus {
  border-color: #7c3aed;
  background: #fff;
}
#wc-textarea::placeholder {
  color: #a78bfa;
}

/* Action buttons row */
#wc-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 10px;
}

#wc-actions button {
  padding: 7px 14px;
  border: none;
  border-radius: 6px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#wc-actions button:active { transform: scale(0.97); }

.wc-btn-primary {
  background: #7c3aed;
  color: #fff;
}
.wc-btn-primary:hover { background: #6d28d9; }

.wc-btn-secondary {
  background: #ede9fe;
  color: #5b21b6;
}
.wc-btn-secondary:hover { background: #ddd6fe; }

.wc-btn-danger {
  background: #fee2e2;
  color: #b91c1c;
}
.wc-btn-danger:hover { background: #fecaca; }

/* Character limit row */
#wc-limit-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 10px;
  flex-wrap: wrap;
}
#wc-limit-row label {
  font-size: 0.85rem;
  color: #5b21b6;
  font-weight: 600;
  white-space: nowrap;
}
#wc-limit-input {
  width: 90px;
  padding: 6px 10px;
  border: 2px solid #c4b5fd;
  border-radius: 6px;
  font-size: 0.85rem;
  color: #1e1b4b;
  outline: none;
}
#wc-limit-input:focus { border-color: #7c3aed; }

/* Progress bar */
#wc-progress-wrap {
  margin-top: 8px;
  display: none;
}
#wc-progress-label {
  font-size: 0.8rem;
  color: #5b21b6;
  margin-bottom: 4px;
}
#wc-progress-bar-bg {
  width: 100%;
  height: 10px;
  background: #ede9fe;
  border-radius: 999px;
  overflow: hidden;
}
#wc-progress-bar {
  height: 100%;
  background: #7c3aed;
  border-radius: 999px;
  transition: width 0.2s, background 0.2s;
  width: 0%;
}
#wc-progress-bar.warn { background: #f59e0b; }
#wc-progress-bar.over  { background: #ef4444; }

/* Stats grid */
#wc-stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
  gap: 12px;
  margin-top: 20px;
}

.wc-stat-card {
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  border-radius: 10px;
  padding: 14px 12px;
  text-align: center;
}
.wc-stat-value {
  font-size: 1.7rem;
  font-weight: 700;
  color: #7c3aed;
  line-height: 1;
}
.wc-stat-label {
  font-size: 0.75rem;
  color: #6b7280;
  margin-top: 6px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

/* Time cards get a slightly different accent */
.wc-stat-card.time .wc-stat-value {
  color: #5b21b6;
  font-size: 1.2rem;
}

/* Keyword table */
#wc-keyword-section {
  margin-top: 28px;
}
#wc-keyword-section h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #4c1d95;
  margin-bottom: 10px;
  border-left: 4px solid #7c3aed;
  padding-left: 10px;
}
#wc-keyword-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#wc-keyword-table th {
  background: #7c3aed;
  color: #fff;
  padding: 8px 12px;
  text-align: left;
  font-weight: 600;
}
#wc-keyword-table th:last-child { text-align: right; }
#wc-keyword-table td {
  padding: 7px 12px;
  border-bottom: 1px solid #ede9fe;
  color: #1e1b4b;
}
#wc-keyword-table td:last-child { text-align: right; }
#wc-keyword-table tr:nth-child(even) td { background: #faf5ff; }
#wc-keyword-table tr:hover td { background: #ede9fe; }

.wc-density-bar-wrap {
  display: inline-block;
  width: 80px;
  height: 8px;
  background: #ede9fe;
  border-radius: 999px;
  vertical-align: middle;
  margin-right: 6px;
  overflow: hidden;
}
.wc-density-bar {
  height: 100%;
  background: #7c3aed;
  border-radius: 999px;
}

#wc-keyword-empty {
  color: #a78bfa;
  font-style: italic;
  font-size: 0.88rem;
  margin-top: 6px;
}

/* Copy feedback */
#wc-copy-feedback {
  font-size: 0.8rem;
  color: #059669;
  font-weight: 600;
  display: none;
  margin-left: 4px;
}

/* Responsive */
@media (max-width: 500px) {
  #wc-stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .wc-stat-value { font-size: 1.4rem; }
  #wc-actions button { font-size: 0.8rem; padding: 6px 10px; }
}
</style>

<textarea id="wc-textarea" placeholder="Paste or type your text here... Stats update in real time."></textarea>

<div id="wc-actions">
  <button class="wc-btn-secondary" onclick="wcTransform('upper')">UPPERCASE</button>
  <button class="wc-btn-secondary" onclick="wcTransform('lower')">lowercase</button>
  <button class="wc-btn-secondary" onclick="wcTransform('title')">Title Case</button>
  <button class="wc-btn-secondary" onclick="wcTransform('sentence')">Sentence case</button>
  <button class="wc-btn-primary"   onclick="wcCopy()">Copy Text</button>
  <span id="wc-copy-feedback">Copied!</span>
  <button class="wc-btn-danger"    onclick="wcClear()">Clear</button>
</div>

<div id="wc-limit-row">
  <label for="wc-limit-input">Character limit (optional):</label>
  <input id="wc-limit-input" type="number" min="0" placeholder="e.g. 280" oninput="wcUpdateLimit()">
</div>

<div id="wc-progress-wrap">
  <div id="wc-progress-label"></div>
  <div id="wc-progress-bar-bg"><div id="wc-progress-bar"></div></div>
</div>

<div id="wc-stats-grid">
  <div class="wc-stat-card">
    <div class="wc-stat-value" id="wc-words">0</div>
    <div class="wc-stat-label">Words</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-value" id="wc-chars">0</div>
    <div class="wc-stat-label">Characters</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-value" id="wc-chars-no-space">0</div>
    <div class="wc-stat-label">Chars (no spaces)</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-value" id="wc-sentences">0</div>
    <div class="wc-stat-label">Sentences</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-value" id="wc-paragraphs">0</div>
    <div class="wc-stat-label">Paragraphs</div>
  </div>
  <div class="wc-stat-card">
    <div class="wc-stat-value" id="wc-avg-word">0</div>
    <div class="wc-stat-label">Avg Word Length</div>
  </div>
  <div class="wc-stat-card time">
    <div class="wc-stat-value" id="wc-read-time">0 min</div>
    <div class="wc-stat-label">Reading Time</div>
  </div>
  <div class="wc-stat-card time">
    <div class="wc-stat-value" id="wc-speak-time">0 min</div>
    <div class="wc-stat-label">Speaking Time</div>
  </div>
</div>

<div id="wc-keyword-section">
  <h3>Top 10 Keyword Density</h3>
  <table id="wc-keyword-table" style="display:none;">
    <thead>
      <tr>
        <th>#</th>
        <th>Keyword</th>
        <th>Count</th>
        <th>Density</th>
      </tr>
    </thead>
    <tbody id="wc-keyword-body"></tbody>
  </table>
  <div id="wc-keyword-empty">Start typing to see keyword frequency analysis.</div>
</div>

<script>
(function () {
  var ta = document.getElementById('wc-textarea');

  var STOP_WORDS = new Set([
    'a','an','the','and','or','but','in','on','at','to','for','of','with',
    'by','from','as','is','was','are','were','be','been','being','have',
    'has','had','do','does','did','will','would','could','should','may',
    'might','shall','can','not','no','nor','so','yet','both','either',
    'neither','whether','if','then','than','that','this','these','those',
    'i','me','my','we','our','you','your','he','his','him','she','her',
    'it','its','they','them','their','what','which','who','whom','when',
    'where','how','all','each','every','more','most','other','some','such',
    'up','out','about','into','over','after','just','also','very','too',
    'only','well','here','there','now','however','although','because',
    'while','through','during','before','between','though','even','get',
    'got','go','went','going','come','came','make','made','one','two',
    'three','any','many','much','own','same','still','again','back'
  ]);

  function formatTime(minutes) {
    if (minutes < 1) {
      return Math.round(minutes * 60) + ' sec';
    }
    var m = Math.floor(minutes);
    var s = Math.round((minutes - m) * 60);
    return s > 0 ? m + ' min ' + s + ' sec' : m + ' min';
  }

  function countSentences(text) {
    var trimmed = text.trim();
    if (!trimmed) return 0;
    var matches = trimmed.match(/[^.!?]*[.!?]+/g);
    if (!matches) {
      // No terminal punctuation: treat as 1 sentence if non-empty
      return trimmed.length > 0 ? 1 : 0;
    }
    return matches.length;
  }

  function countParagraphs(text) {
    var trimmed = text.trim();
    if (!trimmed) return 0;
    return trimmed.split(/\n\s*\n+/).filter(function(p) {
      return p.trim().length > 0;
    }).length;
  }

  function getWords(text) {
    var trimmed = text.trim();
    if (!trimmed) return [];
    return trimmed.match(/\b[\w']+\b/g) || [];
  }

  function computeKeywords(words) {
    var freq = {};
    words.forEach(function(w) {
      var lw = w.toLowerCase().replace(/[^a-z0-9]/g, '');
      if (lw.length < 2) return;
      if (STOP_WORDS.has(lw)) return;
      freq[lw] = (freq[lw] || 0) + 1;
    });
    var sorted = Object.keys(freq).sort(function(a, b) {
      return freq[b] - freq[a];
    });
    return sorted.slice(0, 10).map(function(w) {
      return { word: w, count: freq[w] };
    });
  }

  function updateStats() {
    var text = ta.value;
    var words = getWords(text);
    var wordCount = words.length;
    var charCount = text.length;
    var charNoSpace = text.replace(/\s/g, '').length;
    var sentences = countSentences(text);
    var paragraphs = countParagraphs(text);

    var totalLetters = words.reduce(function(sum, w) {
      return sum + w.replace(/[^a-zA-Z0-9]/g, '').length;
    }, 0);
    var avgWord = wordCount > 0 ? (totalLetters / wordCount).toFixed(1) : 0;

    var readMin = wordCount / 200;
    var speakMin = wordCount / 130;

    document.getElementById('wc-words').textContent = wordCount.toLocaleString();
    document.getElementById('wc-chars').textContent = charCount.toLocaleString();
    document.getElementById('wc-chars-no-space').textContent = charNoSpace.toLocaleString();
    document.getElementById('wc-sentences').textContent = sentences.toLocaleString();
    document.getElementById('wc-paragraphs').textContent = paragraphs.toLocaleString();
    document.getElementById('wc-avg-word').textContent = avgWord;
    document.getElementById('wc-read-time').textContent = wordCount > 0 ? formatTime(readMin) : '0 sec';
    document.getElementById('wc-speak-time').textContent = wordCount > 0 ? formatTime(speakMin) : '0 sec';

    // Keywords
    var keywords = computeKeywords(words);
    var tbody = document.getElementById('wc-keyword-body');
    var table = document.getElementById('wc-keyword-table');
    var empty = document.getElementById('wc-keyword-empty');

    if (keywords.length === 0) {
      table.style.display = 'none';
      empty.style.display = 'block';
    } else {
      table.style.display = 'table';
      empty.style.display = 'none';
      var maxCount = keywords[0].count;
      tbody.innerHTML = keywords.map(function(kw, i) {
        var pct = wordCount > 0 ? ((kw.count / wordCount) * 100).toFixed(2) : '0.00';
        var barWidth = Math.round((kw.count / maxCount) * 100);
        return '<tr>' +
          '<td>' + (i + 1) + '</td>' +
          '<td><strong>' + kw.word + '</strong></td>' +
          '<td>' + kw.count + '</td>' +
          '<td><span class="wc-density-bar-wrap"><span class="wc-density-bar" style="width:' + barWidth + '%"></span></span>' + pct + '%</td>' +
          '</tr>';
      }).join('');
    }

    updateProgress(charCount);
  }

  function updateProgress(charCount) {
    var limitVal = parseInt(document.getElementById('wc-limit-input').value, 10);
    var wrap = document.getElementById('wc-progress-wrap');
    var bar = document.getElementById('wc-progress-bar');
    var label = document.getElementById('wc-progress-label');

    if (!limitVal || limitVal <= 0) {
      wrap.style.display = 'none';
      return;
    }

    wrap.style.display = 'block';
    var pct = Math.min((charCount / limitVal) * 100, 100);
    bar.style.width = pct + '%';
    bar.className = 'wc-density-bar';
    if (pct >= 100) {
      bar.classList.add('over');
      label.textContent = charCount + ' / ' + limitVal + ' characters — LIMIT EXCEEDED by ' + (charCount - limitVal);
    } else if (pct >= 80) {
      bar.classList.add('warn');
      label.textContent = charCount + ' / ' + limitVal + ' characters (' + (limitVal - charCount) + ' remaining)';
    } else {
      label.textContent = charCount + ' / ' + limitVal + ' characters (' + (limitVal - charCount) + ' remaining)';
    }
  }

  function wcUpdateLimit() {
    updateProgress(ta.value.length);
  }
  window.wcUpdateLimit = wcUpdateLimit;

  function wcTransform(mode) {
    var val = ta.value;
    if (!val) return;
    if (mode === 'upper') {
      ta.value = val.toUpperCase();
    } else if (mode === 'lower') {
      ta.value = val.toLowerCase();
    } else if (mode === 'title') {
      ta.value = val.replace(/\b\w+/g, function(w) {
        return w.charAt(0).toUpperCase() + w.slice(1).toLowerCase();
      });
    } else if (mode === 'sentence') {
      ta.value = val.toLowerCase().replace(/(^\s*\w|[.!?]\s*\w)/g, function(c) {
        return c.toUpperCase();
      });
    }
    updateStats();
  }
  window.wcTransform = wcTransform;

  function wcCopy() {
    if (!ta.value) return;
    navigator.clipboard.writeText(ta.value).then(function() {
      var fb = document.getElementById('wc-copy-feedback');
      fb.style.display = 'inline';
      setTimeout(function() { fb.style.display = 'none'; }, 2000);
    }).catch(function() {
      ta.select();
      document.execCommand('copy');
    });
  }
  window.wcCopy = wcCopy;

  function wcClear() {
    ta.value = '';
    document.getElementById('wc-limit-input').value = '';
    updateStats();
  }
  window.wcClear = wcClear;

  ta.addEventListener('input', updateStats);
  updateStats();
})();
</script>

</div>

---

## How to Use This Word Counter

Paste or type your text into the large input area above. All statistics — word count, character count, sentence count, paragraph count, average word length, and estimated reading and speaking times — update instantly as you type. No need to click any button; everything is calculated in real time so you can watch the numbers change as you write or edit.

To analyze a document you already have, simply open it, select all (Ctrl+A or Cmd+A), copy, and paste into the text box. The keyword density table at the bottom automatically surfaces your top 10 most-used meaningful words, excluding common filler words, so you can see at a glance which terms dominate your writing. If you need a specific character limit — say, for a tweet, a LinkedIn post caption, or an SMS — enter the limit in the character limit field and a color-coded progress bar will track how close you are.

The text transformation buttons let you instantly change the case of your entire text: convert everything to UPPERCASE for headlines, switch to lowercase for normalization, apply Title Case for formal titles, or fix capitalization with Sentence case. When you are done, use the Copy Text button to send the processed text to your clipboard in one click, or Clear to start fresh.

## Why Word Count Matters

For SEO and content marketing, hitting the right word count signals depth and authority to search engines. Studies consistently show that long-form articles (typically 1,500–2,500 words) tend to rank higher for competitive keywords, while short, focused pages of 300–500 words can win featured snippets. Knowing your word count helps you benchmark against top-ranking competitors and decide whether to expand, trim, or split your content.

Social media platforms impose strict character limits that directly shape how your message is received. Twitter and X allow 280 characters per post, LinkedIn captions cap at 700 characters for optimal display before truncation, and SMS messages are traditionally 160 characters per segment. The character counter in this tool — with and without spaces — makes it easy to craft posts that fit within these constraints without awkward truncation.

In academic and professional writing, word counts are often hard requirements. University essays, grant applications, journal abstracts, and legal briefs all have specified ranges you must stay within. Going over can disqualify your submission; coming in too short signals lack of depth. Tracking your count throughout the drafting process, rather than scrambling at the end, keeps revision stress to a minimum.

## Related Tools

> Stay focused while writing with the Pomodoro Technique → [Pomodoro Timer](/tools/pomodoro-timer/)

> Generate secure passwords for your accounts → [Password Generator](/tools/password-generator/)

> Calculate your freelance writing rate → [Freelance Rate Calculator](/tools/freelance-rate-calculator/)
