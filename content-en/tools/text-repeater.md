---
title: "Text Repeater — Repeat, Format & Transform Text Online"
description: "Repeat any text string multiple times with custom separators. Free online text repetition tool."
date: 2025-05-16
slug: "text-repeater"
categories: ["Free Tools"]
aliases: ["/tools/repeat-text/", "/tools/text-multiplier/"]
cover:
  image: "/images/covers/text-repeater.png"
  alt: "Text Repeater"
ShowToc: false
---

<style>
#rep-app *,
#rep-app *::before,
#rep-app *::after {
  box-sizing: border-box;
}
#rep-app {
  font-family: system-ui, -apple-system, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1e293b;
}
#rep-app h2 {
  font-size: 1.1rem;
  font-weight: 600;
  margin: 1.4rem 0 0.5rem;
  color: #0f766e;
}
#rep-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 500;
  margin-bottom: 0.3rem;
  color: #374151;
}
#rep-app textarea,
#rep-app input[type="text"],
#rep-app input[type="number"],
#rep-app select {
  width: 100%;
  padding: 0.55rem 0.75rem;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.95rem;
  background: #fff;
  color: #1e293b;
  transition: border-color 0.15s;
  outline: none;
}
#rep-app textarea:focus,
#rep-app input[type="text"]:focus,
#rep-app input[type="number"]:focus,
#rep-app select:focus {
  border-color: #0d9488;
  box-shadow: 0 0 0 3px rgba(13,148,136,.15);
}
#rep-app textarea {
  min-height: 110px;
  resize: vertical;
  font-family: inherit;
}
#rep-app .row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
#rep-app .row > .field {
  flex: 1;
  min-width: 160px;
}
#rep-app .field {
  margin-bottom: 0.85rem;
}
#rep-app .check-group {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem 1.2rem;
  margin-bottom: 0.85rem;
}
#rep-app .check-group label {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.9rem;
  font-weight: 400;
  cursor: pointer;
  color: #374151;
  margin: 0;
}
#rep-app input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #0d9488;
  cursor: pointer;
}
#rep-app .sep-custom {
  display: none;
  margin-top: 0.5rem;
}
#rep-app .sep-custom.visible {
  display: block;
}
#rep-app .btn-run {
  display: inline-block;
  background: #0d9488;
  color: #fff;
  border: none;
  border-radius: 7px;
  padding: 0.65rem 1.8rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  margin-top: 0.3rem;
}
#rep-app .btn-run:hover {
  background: #0f766e;
}
#rep-app .output-wrap {
  margin-top: 1.2rem;
}
#rep-app .output-meta {
  font-size: 0.82rem;
  color: #64748b;
  margin-bottom: 0.4rem;
}
#rep-app .output-box {
  position: relative;
}
#rep-app #rep-output {
  width: 100%;
  min-height: 140px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  padding: 0.65rem 0.75rem;
  font-size: 0.9rem;
  background: #f8fafc;
  color: #1e293b;
  resize: vertical;
  font-family: inherit;
}
#rep-app .btn-copy {
  display: inline-block;
  margin-top: 0.55rem;
  background: #fff;
  color: #0d9488;
  border: 1.5px solid #0d9488;
  border-radius: 6px;
  padding: 0.45rem 1.2rem;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#rep-app .btn-copy:hover {
  background: #0d9488;
  color: #fff;
}
#rep-app .copy-feedback {
  display: inline-block;
  margin-left: 0.7rem;
  font-size: 0.82rem;
  color: #0d9488;
  opacity: 0;
  transition: opacity 0.3s;
}
#rep-app .copy-feedback.show {
  opacity: 1;
}
#rep-app .divider {
  border: none;
  border-top: 1px solid #e2e8f0;
  margin: 1.1rem 0;
}
#rep-app .error {
  color: #dc2626;
  font-size: 0.85rem;
  margin-top: 0.25rem;
}
</style>

<div id="rep-app">

<div class="field">
  <label for="rep-input">Input Text</label>
  <textarea id="rep-input" placeholder="Type or paste your text here…"></textarea>
</div>

<div class="row">
  <div class="field">
    <label for="rep-count">Repeat Count (1–10000)</label>
    <input type="number" id="rep-count" value="3" min="1" max="10000">
    <div class="error" id="rep-count-err"></div>
  </div>
  <div class="field">
    <label for="rep-sep">Separator</label>
    <select id="rep-sep">
      <option value="newline">New Line</option>
      <option value="space">Space</option>
      <option value="comma">Comma</option>
      <option value="custom">Custom…</option>
    </select>
    <div class="sep-custom" id="rep-sep-custom-wrap">
      <input type="text" id="rep-sep-custom" placeholder="Enter custom separator">
    </div>
  </div>
</div>

<div class="row">
  <div class="field">
    <label for="rep-prefix">Prefix (per repetition)</label>
    <input type="text" id="rep-prefix" placeholder="e.g. - ">
  </div>
  <div class="field">
    <label for="rep-suffix">Suffix (per repetition)</label>
    <input type="text" id="rep-suffix" placeholder="e.g. ;">
  </div>
</div>

<h2>Transform Options</h2>
<div class="check-group">
  <label><input type="checkbox" id="rep-numbered"> Numbered mode (1. text, 2. text…)</label>
  <label><input type="checkbox" id="rep-reverse"> Reverse text</label>
  <label><input type="checkbox" id="rep-shuffle"> Shuffle lines</label>
  <label><input type="checkbox" id="rep-sort-az"> Sort A→Z</label>
  <label><input type="checkbox" id="rep-sort-za"> Sort Z→A</label>
  <label><input type="checkbox" id="rep-dedup"> Remove duplicate lines</label>
</div>

<button class="btn-run" id="rep-run">Generate</button>

<hr class="divider">

<div class="output-wrap">
  <div class="output-meta" id="rep-meta"></div>
  <div class="output-box">
    <textarea id="rep-output" readonly placeholder="Output will appear here…"></textarea>
  </div>
  <button class="btn-copy" id="rep-copy">Copy to Clipboard</button>
  <span class="copy-feedback" id="rep-copy-fb">Copied!</span>
</div>

</div>

<script>
(function () {
  var sepEl      = document.getElementById('rep-sep');
  var sepCustomW = document.getElementById('rep-sep-custom-wrap');
  var sepCustom  = document.getElementById('rep-sep-custom');
  var inputEl    = document.getElementById('rep-input');
  var countEl    = document.getElementById('rep-count');
  var countErr   = document.getElementById('rep-count-err');
  var prefixEl   = document.getElementById('rep-prefix');
  var suffixEl   = document.getElementById('rep-suffix');
  var numberedEl = document.getElementById('rep-numbered');
  var reverseEl  = document.getElementById('rep-reverse');
  var shuffleEl  = document.getElementById('rep-shuffle');
  var sortAZEl   = document.getElementById('rep-sort-az');
  var sortZAEl   = document.getElementById('rep-sort-za');
  var dedupEl    = document.getElementById('rep-dedup');
  var runBtn     = document.getElementById('rep-run');
  var outputEl   = document.getElementById('rep-output');
  var metaEl     = document.getElementById('rep-meta');
  var copyBtn    = document.getElementById('rep-copy');
  var copyFb     = document.getElementById('rep-copy-fb');

  sepEl.addEventListener('change', function () {
    if (sepEl.value === 'custom') {
      sepCustomW.classList.add('visible');
    } else {
      sepCustomW.classList.remove('visible');
    }
  });

  // mutual exclusivity for sort options
  sortAZEl.addEventListener('change', function () { if (this.checked) sortZAEl.checked = false; });
  sortZAEl.addEventListener('change', function () { if (this.checked) sortAZEl.checked = false; });

  function getSeparator() {
    switch (sepEl.value) {
      case 'newline': return '\n';
      case 'space':   return ' ';
      case 'comma':   return ', ';
      case 'custom':  return sepCustom.value;
      default:        return '\n';
    }
  }

  function shuffleArray(arr) {
    for (var i = arr.length - 1; i > 0; i--) {
      var j = Math.floor(Math.random() * (i + 1));
      var tmp = arr[i]; arr[i] = arr[j]; arr[j] = tmp;
    }
    return arr;
  }

  runBtn.addEventListener('click', function () {
    countErr.textContent = '';
    var text = inputEl.value;
    var count = parseInt(countEl.value, 10);

    if (!text) { outputEl.value = ''; metaEl.textContent = ''; return; }
    if (isNaN(count) || count < 1 || count > 10000) {
      countErr.textContent = 'Please enter a number between 1 and 10000.';
      return;
    }

    var prefix = prefixEl.value;
    var suffix = suffixEl.value;
    var sep = getSeparator();
    var numbered = numberedEl.checked;
    var reverse  = reverseEl.checked;
    var shuffle  = shuffleEl.checked;
    var sortAZ   = sortAZEl.checked;
    var sortZA   = sortZAEl.checked;
    var dedup    = dedupEl.checked;

    // apply reverse to input text
    var baseText = reverse ? text.split('').reverse().join('') : text;

    // build repetitions
    var items = [];
    for (var i = 0; i < count; i++) {
      var line = prefix + baseText + suffix;
      if (numbered) line = (i + 1) + '. ' + line;
      items.push(line);
    }

    // post-process lines
    if (dedup) {
      var seen = {};
      items = items.filter(function (l) {
        if (seen[l]) return false;
        seen[l] = true;
        return true;
      });
    }

    if (shuffle) {
      shuffleArray(items);
    } else if (sortAZ) {
      items.sort(function (a, b) { return a.localeCompare(b); });
    } else if (sortZA) {
      items.sort(function (a, b) { return b.localeCompare(a); });
    }

    var result = items.join(sep);
    outputEl.value = result;

    var charCount = result.length;
    var lineCount = items.length;
    metaEl.textContent = lineCount + ' repetition(s) · ' + charCount.toLocaleString() + ' characters';
  });

  copyBtn.addEventListener('click', function () {
    if (!outputEl.value) return;
    navigator.clipboard.writeText(outputEl.value).then(function () {
      copyFb.classList.add('show');
      setTimeout(function () { copyFb.classList.remove('show'); }, 1800);
    }).catch(function () {
      outputEl.select();
      document.execCommand('copy');
      copyFb.classList.add('show');
      setTimeout(function () { copyFb.classList.remove('show'); }, 1800);
    });
  });
})();
</script>

---

**Related:** Count text → [Word Counter](/tools/word-counter/)
