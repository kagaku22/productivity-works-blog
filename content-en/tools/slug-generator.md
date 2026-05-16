---
title: "URL Slug Generator"
date: 2025-05-16
description: "Free URL slug generator. Convert any text to a clean, URL-safe slug instantly. Supports separator choice, max length, stop word removal, accented character transliteration, and bulk mode."
categories: ["Free Tools"]
slug: "slug-generator"
ShowToc: false
cover:
  image: "/images/covers/slug-generator.png"
  alt: "URL Slug Generator"
aliases: ["/tools/url-slug/", "/tools/slugify/"]
---

<div id="sg-app">
<style>
#sg-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 700px;
  margin: 0 auto;
  color: #1e293b;
  box-sizing: border-box;
}
#sg-app *, #sg-app *::before, #sg-app *::after {
  box-sizing: border-box;
}
#sg-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 14px 0;
  color: #0f172a;
}
#sg-app .sg-card {
  background: #ffffff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 22px 20px;
  margin-bottom: 18px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#sg-app label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 6px;
}
#sg-app input[type="text"],
#sg-app textarea,
#sg-app select,
#sg-app input[type="number"] {
  width: 100%;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  padding: 10px 12px;
  font-size: 15px;
  color: #1e293b;
  background: #f8fafc;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}
#sg-app input[type="text"]:focus,
#sg-app textarea:focus,
#sg-app select:focus,
#sg-app input[type="number"]:focus {
  border-color: #6366f1;
  background: #fff;
}
#sg-app textarea {
  resize: vertical;
  min-height: 90px;
}
#sg-app .sg-options-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 14px;
  margin-bottom: 0;
}
@media (max-width: 560px) {
  #sg-app .sg-options-grid {
    grid-template-columns: 1fr 1fr;
  }
}
@media (max-width: 380px) {
  #sg-app .sg-options-grid {
    grid-template-columns: 1fr;
  }
}
#sg-app .sg-checkbox-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 4px;
}
#sg-app .sg-checkbox-row input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #6366f1;
  cursor: pointer;
  flex-shrink: 0;
}
#sg-app .sg-checkbox-row label {
  margin: 0;
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  cursor: pointer;
}
#sg-app .sg-result-box {
  background: #f1f5f9;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  padding: 11px 14px;
  font-size: 15px;
  font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
  color: #1e293b;
  word-break: break-all;
  min-height: 42px;
  line-height: 1.5;
}
#sg-app .sg-result-box.empty {
  color: #94a3b8;
  font-family: inherit;
  font-size: 14px;
}
#sg-app .sg-preview-box {
  background: #eff6ff;
  border: 1.5px solid #bfdbfe;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 13px;
  font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
  color: #1d4ed8;
  word-break: break-all;
  margin-top: 10px;
  min-height: 38px;
  line-height: 1.5;
}
#sg-app .sg-preview-box.empty {
  color: #94a3b8;
  font-family: inherit;
  font-size: 13px;
}
#sg-app .sg-row {
  display: flex;
  gap: 10px;
  align-items: center;
  flex-wrap: wrap;
}
#sg-app .sg-copy-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 9px 18px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
}
#sg-app .sg-copy-btn:hover {
  background: #4f46e5;
}
#sg-app .sg-copy-btn.copied {
  background: #16a34a;
}
#sg-app .sg-char-badge {
  font-size: 12px;
  color: #64748b;
  background: #f1f5f9;
  border: 1px solid #e2e8f0;
  border-radius: 20px;
  padding: 3px 10px;
}
#sg-app .sg-tab-row {
  display: flex;
  gap: 0;
  margin-bottom: 16px;
  border-bottom: 2px solid #e2e8f0;
}
#sg-app .sg-tab {
  padding: 8px 20px;
  font-size: 13px;
  font-weight: 700;
  color: #64748b;
  cursor: pointer;
  border: none;
  background: none;
  border-bottom: 2.5px solid transparent;
  margin-bottom: -2px;
  transition: color 0.12s, border-color 0.12s;
}
#sg-app .sg-tab.active {
  color: #6366f1;
  border-bottom-color: #6366f1;
}
#sg-app .sg-bulk-results {
  margin-top: 12px;
}
#sg-app .sg-bulk-row {
  display: flex;
  align-items: flex-start;
  gap: 8px;
  padding: 7px 0;
  border-bottom: 1px solid #f1f5f9;
}
#sg-app .sg-bulk-row:last-child {
  border-bottom: none;
}
#sg-app .sg-bulk-input {
  font-size: 13px;
  color: #64748b;
  flex: 1;
  word-break: break-all;
  padding-top: 1px;
}
#sg-app .sg-bulk-arrow {
  font-size: 13px;
  color: #94a3b8;
  flex-shrink: 0;
  padding-top: 1px;
}
#sg-app .sg-bulk-slug {
  font-size: 13px;
  font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
  color: #4f46e5;
  flex: 1.5;
  word-break: break-all;
  padding-top: 1px;
}
#sg-app .sg-bulk-copy {
  background: none;
  border: 1px solid #c7d2fe;
  border-radius: 5px;
  color: #6366f1;
  font-size: 11px;
  font-weight: 700;
  padding: 2px 9px;
  cursor: pointer;
  flex-shrink: 0;
  transition: background 0.12s;
}
#sg-app .sg-bulk-copy:hover {
  background: #eef2ff;
}
#sg-app .sg-bulk-copy-all {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 7px 16px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  margin-top: 12px;
  transition: background 0.15s;
}
#sg-app .sg-bulk-copy-all:hover {
  background: #4f46e5;
}
#sg-app .sg-section-label {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #94a3b8;
  margin-bottom: 10px;
}
#sg-app .sg-base-url-row {
  display: flex;
  align-items: center;
  gap: 0;
  margin-top: 10px;
}
#sg-app .sg-base-url-prefix {
  background: #e2e8f0;
  border: 1.5px solid #cbd5e1;
  border-right: none;
  border-radius: 8px 0 0 8px;
  padding: 10px 10px;
  font-size: 13px;
  color: #64748b;
  white-space: nowrap;
  font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
}
#sg-app .sg-base-url-input {
  border-radius: 0 8px 8px 0 !important;
}
</style>

<div class="sg-card">
  <div class="sg-tab-row">
    <button class="sg-tab active" id="sg-tab-single" onclick="sgSwitchTab('single')">Single</button>
    <button class="sg-tab" id="sg-tab-bulk" onclick="sgSwitchTab('bulk')">Bulk</button>
  </div>

  <!-- Single mode -->
  <div id="sg-panel-single">
    <div style="margin-bottom:14px;">
      <label for="sg-input">Input Text</label>
      <input type="text" id="sg-input" placeholder="e.g. Hello World! My Blog Post Title" oninput="sgConvert()" />
    </div>

    <div class="sg-options-grid" style="margin-bottom:16px;">
      <div>
        <label for="sg-separator">Separator</label>
        <select id="sg-separator" onchange="sgConvert()">
          <option value="-">Hyphen ( - )</option>
          <option value="_">Underscore ( _ )</option>
          <option value=".">Dot ( . )</option>
        </select>
      </div>
      <div>
        <label for="sg-maxlen">Max Length</label>
        <input type="number" id="sg-maxlen" value="80" min="10" max="500" oninput="sgConvert()" />
      </div>
      <div style="display:flex;flex-direction:column;justify-content:flex-end;">
        <div class="sg-checkbox-row" style="margin-bottom:6px;">
          <input type="checkbox" id="sg-stopwords" onchange="sgConvert()" />
          <label for="sg-stopwords">Remove stop words</label>
        </div>
        <div class="sg-checkbox-row">
          <input type="checkbox" id="sg-translit" checked onchange="sgConvert()" />
          <label for="sg-translit">Transliterate accents</label>
        </div>
      </div>
    </div>

    <div style="margin-bottom:10px;">
      <div class="sg-section-label">Preview Base URL</div>
      <div class="sg-base-url-row">
        <span class="sg-base-url-prefix">https://</span>
        <input type="text" id="sg-baseurl" class="sg-base-url-input" value="example.com/" placeholder="example.com/" oninput="sgConvert()" />
      </div>
    </div>

    <div style="margin-bottom:8px;">
      <div class="sg-section-label">Generated Slug</div>
      <div class="sg-result-box empty" id="sg-result">Your slug will appear here…</div>
      <div class="sg-preview-box empty" id="sg-preview">Full URL preview will appear here…</div>
    </div>

    <div class="sg-row" style="margin-top:12px;">
      <button class="sg-copy-btn" id="sg-copy-btn" onclick="sgCopySlug()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
        Copy Slug
      </button>
      <button class="sg-copy-btn" id="sg-copy-url-btn" onclick="sgCopyUrl()" style="background:#0284c7;">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"/><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"/></svg>
        Copy Full URL
      </button>
      <span class="sg-char-badge" id="sg-char-count">0 chars</span>
    </div>
  </div>

  <!-- Bulk mode -->
  <div id="sg-panel-bulk" style="display:none;">
    <div style="margin-bottom:14px;">
      <label for="sg-bulk-input">Paste multiple lines (one title per line)</label>
      <textarea id="sg-bulk-input" placeholder="My First Post Title&#10;Hello World Example&#10;Another Great Article" oninput="sgBulkConvert()" rows="6"></textarea>
    </div>

    <div class="sg-options-grid" style="margin-bottom:16px;">
      <div>
        <label for="sg-bulk-separator">Separator</label>
        <select id="sg-bulk-separator" onchange="sgBulkConvert()">
          <option value="-">Hyphen ( - )</option>
          <option value="_">Underscore ( _ )</option>
          <option value=".">Dot ( . )</option>
        </select>
      </div>
      <div>
        <label for="sg-bulk-maxlen">Max Length</label>
        <input type="number" id="sg-bulk-maxlen" value="80" min="10" max="500" oninput="sgBulkConvert()" />
      </div>
      <div style="display:flex;flex-direction:column;justify-content:flex-end;">
        <div class="sg-checkbox-row" style="margin-bottom:6px;">
          <input type="checkbox" id="sg-bulk-stopwords" onchange="sgBulkConvert()" />
          <label for="sg-bulk-stopwords">Remove stop words</label>
        </div>
        <div class="sg-checkbox-row">
          <input type="checkbox" id="sg-bulk-translit" checked onchange="sgBulkConvert()" />
          <label for="sg-bulk-translit">Transliterate accents</label>
        </div>
      </div>
    </div>

    <div class="sg-bulk-results" id="sg-bulk-results"></div>
  </div>
</div>

<script>
(function() {
  // --- Stop words list ---
  var STOP_WORDS = new Set([
    'a','an','the','and','or','but','in','on','at','to','for','of','with',
    'by','from','up','about','into','through','during','before','after',
    'above','below','between','out','off','over','under','again','then',
    'once','is','are','was','were','be','been','being','have','has','had',
    'do','does','did','will','would','shall','should','may','might','must',
    'can','could','not','no','nor','so','yet','both','either','neither',
    'this','that','these','those','it','its','my','your','his','her',
    'our','their','we','they','he','she','i','you','as','if','than'
  ]);

  // --- Transliteration map ---
  var TRANSLIT = {
    'à':'a','á':'a','â':'a','ã':'a','ä':'a','å':'a','æ':'ae',
    'ç':'c','è':'e','é':'e','ê':'e','ë':'e',
    'ì':'i','í':'i','î':'i','ï':'i',
    'ð':'d','ñ':'n',
    'ò':'o','ó':'o','ô':'o','õ':'o','ö':'o','ø':'o',
    'ù':'u','ú':'u','û':'u','ü':'u',
    'ý':'y','þ':'th','ß':'ss',
    'À':'a','Á':'a','Â':'a','Ã':'a','Ä':'a','Å':'a','Æ':'ae',
    'Ç':'c','È':'e','É':'e','Ê':'e','Ë':'e',
    'Ì':'i','Í':'i','Î':'i','Ï':'i',
    'Ð':'d','Ñ':'n',
    'Ò':'o','Ó':'o','Ô':'o','Õ':'o','Ö':'o','Ø':'o',
    'Ù':'u','Ú':'u','Û':'u','Ü':'u',
    'Ý':'y','Þ':'th',
    'ā':'a','ē':'e','ī':'i','ō':'o','ū':'u',
    'Ā':'a','Ē':'e','Ī':'i','Ō':'o','Ū':'u',
    'ă':'a','ĕ':'e','ĭ':'i','ŏ':'o','ŭ':'u',
    'ć':'c','ĉ':'c','č':'c','ď':'d','ě':'e',
    'ğ':'g','ĝ':'g','ġ':'g','ģ':'g',
    'ĥ':'h','ħ':'h','ĵ':'j','ķ':'k','ĺ':'l','ļ':'l','ľ':'l','ł':'l',
    'ń':'n','ņ':'n','ň':'n','ŕ':'r','ř':'r','ś':'s','ŝ':'s','ş':'s','š':'s',
    'ţ':'t','ť':'t','ź':'z','ż':'z','ž':'z',
    'œ':'oe','Œ':'oe','ĳ':'ij','Ĳ':'ij',
    '&':'and',"'":'','"':''
  };

  function transliterate(str) {
    return str.replace(/[^\u0000-\u007E]/g, function(ch) {
      return TRANSLIT[ch] || '';
    }).replace(/[&'"]/g, function(ch) {
      return TRANSLIT[ch] !== undefined ? TRANSLIT[ch] : '';
    });
  }

  function makeSlug(text, sep, maxLen, removeStop, doTranslit) {
    if (!text || !text.trim()) return '';
    var s = text;
    // Replace & early
    s = s.replace(/&/g, ' and ');
    // Transliterate
    if (doTranslit) s = transliterate(s);
    // Lowercase
    s = s.toLowerCase();
    // Remove apostrophes and quotes
    s = s.replace(/[''"""]/g, '');
    // Replace non-alphanumeric with sep
    s = s.replace(/[^a-z0-9]+/g, sep);
    // Trim sep from edges
    var re = new RegExp('^[' + escRe(sep) + ']+|[' + escRe(sep) + ']+$', 'g');
    s = s.replace(re, '');
    // Remove stop words
    if (removeStop && sep !== '') {
      var parts = s.split(sep).filter(function(w) { return w.length > 0; });
      var filtered = parts.filter(function(w, i) {
        // Keep at least one word
        return !STOP_WORDS.has(w) || (i === 0 && parts.length === 1);
      });
      // If filtering removed everything, revert
      if (filtered.length === 0) filtered = parts;
      s = filtered.join(sep);
    }
    // Max length: truncate at sep boundary
    if (maxLen && s.length > maxLen) {
      s = s.substring(0, maxLen);
      var lastSep = s.lastIndexOf(sep);
      if (lastSep > 0) s = s.substring(0, lastSep);
    }
    // Final trim of sep
    s = s.replace(re, '');
    return s;
  }

  function escRe(ch) {
    return ch.replace(/[-\.]/g, '\\$&');
  }

  function getBaseUrl() {
    var raw = (document.getElementById('sg-baseurl').value || 'example.com/').trim();
    if (!raw.startsWith('http://') && !raw.startsWith('https://')) raw = 'https://' + raw;
    if (!raw.endsWith('/')) raw += '/';
    return raw;
  }

  window.sgConvert = function() {
    var text = document.getElementById('sg-input').value;
    var sep = document.getElementById('sg-separator').value;
    var maxLen = parseInt(document.getElementById('sg-maxlen').value) || 80;
    var removeStop = document.getElementById('sg-stopwords').checked;
    var doTranslit = document.getElementById('sg-translit').checked;

    var slug = makeSlug(text, sep, maxLen, removeStop, doTranslit);

    var resultEl = document.getElementById('sg-result');
    var previewEl = document.getElementById('sg-preview');
    var countEl = document.getElementById('sg-char-count');

    if (slug) {
      resultEl.textContent = slug;
      resultEl.classList.remove('empty');
      var fullUrl = getBaseUrl() + slug;
      previewEl.textContent = fullUrl;
      previewEl.classList.remove('empty');
      countEl.textContent = slug.length + ' chars';
    } else {
      resultEl.textContent = 'Your slug will appear here\u2026';
      resultEl.classList.add('empty');
      previewEl.textContent = 'Full URL preview will appear here\u2026';
      previewEl.classList.add('empty');
      countEl.textContent = '0 chars';
    }
  };

  window.sgCopySlug = function() {
    var slug = document.getElementById('sg-result').textContent;
    if (!slug || document.getElementById('sg-result').classList.contains('empty')) return;
    copyText(slug, 'sg-copy-btn', 'Copy Slug', 'Copied!');
  };

  window.sgCopyUrl = function() {
    var url = document.getElementById('sg-preview').textContent;
    if (!url || document.getElementById('sg-preview').classList.contains('empty')) return;
    copyText(url, 'sg-copy-url-btn', 'Copy Full URL', 'Copied!');
  };

  function copyText(text, btnId, origLabel, doneLabel) {
    var btn = document.getElementById(btnId);
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() { flashBtn(btn, doneLabel, origLabel); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      flashBtn(btn, doneLabel, origLabel);
    }
  }

  function flashBtn(btn, doneLabel, origLabel) {
    var orig = btn.innerHTML;
    btn.classList.add('copied');
    btn.innerHTML = '<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg> ' + doneLabel;
    setTimeout(function() {
      btn.classList.remove('copied');
      btn.innerHTML = orig;
    }, 1600);
  }

  window.sgSwitchTab = function(tab) {
    document.getElementById('sg-panel-single').style.display = tab === 'single' ? '' : 'none';
    document.getElementById('sg-panel-bulk').style.display = tab === 'bulk' ? '' : 'none';
    document.getElementById('sg-tab-single').classList.toggle('active', tab === 'single');
    document.getElementById('sg-tab-bulk').classList.toggle('active', tab === 'bulk');
  };

  window.sgBulkConvert = function() {
    var raw = document.getElementById('sg-bulk-input').value;
    var sep = document.getElementById('sg-bulk-separator').value;
    var maxLen = parseInt(document.getElementById('sg-bulk-maxlen').value) || 80;
    var removeStop = document.getElementById('sg-bulk-stopwords').checked;
    var doTranslit = document.getElementById('sg-bulk-translit').checked;

    var lines = raw.split('\n');
    var container = document.getElementById('sg-bulk-results');

    if (!raw.trim()) {
      container.innerHTML = '';
      return;
    }

    var html = '';
    var results = [];
    lines.forEach(function(line, idx) {
      if (!line.trim()) return;
      var slug = makeSlug(line, sep, maxLen, removeStop, doTranslit);
      results.push(slug);
      html += '<div class="sg-bulk-row">' +
        '<span class="sg-bulk-input">' + esc(line) + '</span>' +
        '<span class="sg-bulk-arrow">&rarr;</span>' +
        '<span class="sg-bulk-slug" id="sg-br-' + idx + '">' + esc(slug) + '</span>' +
        '<button class="sg-bulk-copy" onclick="sgBulkCopyOne(' + idx + ',\'' + esc(slug).replace(/'/g,"\\'") + '\',this)">Copy</button>' +
        '</div>';
    });

    if (results.length > 0) {
      html += '<button class="sg-bulk-copy-all" onclick="sgBulkCopyAll()">Copy All Slugs</button>';
    }
    container.innerHTML = html;
    container._results = results;
  };

  window.sgBulkCopyOne = function(idx, slug, btn) {
    var origText = btn.textContent;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(slug).then(function() { btn.textContent = 'Copied!'; setTimeout(function(){btn.textContent=origText;},1400); });
    } else {
      fallbackCopy(slug);
      btn.textContent = 'Copied!';
      setTimeout(function(){btn.textContent=origText;},1400);
    }
  };

  window.sgBulkCopyAll = function() {
    var container = document.getElementById('sg-bulk-results');
    var results = container._results || [];
    var text = results.join('\n');
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text);
    } else {
      fallbackCopy(text);
    }
    var btn = container.querySelector('.sg-bulk-copy-all');
    if (btn) { var o=btn.textContent; btn.textContent='All Copied!'; setTimeout(function(){btn.textContent=o;},1600); }
  };

  function fallbackCopy(text) {
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.opacity = '0';
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    document.body.removeChild(ta);
  }

  function esc(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }
})();
</script>
</div>

---

> Encode URLs → [URL Encoder](/tools/url-encoder/)

> Generate meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)
