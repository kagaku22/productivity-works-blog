---
title: "URL Encoder / Decoder"
date: 2025-05-16
description: "Free online URL encoder and decoder. Encode special characters for safe URLs or decode percent-encoded strings instantly — no sign-up required."
categories: ["Free Tools"]
slug: "url-encoder-decoder"
ShowToc: false
cover:
  image: "/images/covers/url-encoder-decoder.png"
  alt: "URL Encoder / Decoder"
---

<div id="ue-app">

<style>
#ue-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1e293b;
}
#ue-app * {
  box-sizing: border-box;
}
#ue-app h2.ue-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 16px 0;
}
#ue-app .ue-card {
  background: #ffffff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 20px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
/* Mode toggle */
#ue-app .ue-mode-row {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}
#ue-app .ue-mode-label {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
#ue-app .ue-toggle-group {
  display: flex;
  background: #f1f5f9;
  border-radius: 8px;
  padding: 3px;
  gap: 2px;
}
#ue-app .ue-toggle-btn {
  padding: 7px 18px;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  background: transparent;
  color: #64748b;
  transition: background 0.15s, color 0.15s;
}
#ue-app .ue-toggle-btn.active {
  background: #ffffff;
  color: #0f172a;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12);
}
#ue-app .ue-scope-group {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  align-items: center;
}
#ue-app .ue-scope-label {
  font-size: 13px;
  color: #64748b;
  font-weight: 500;
}
#ue-app .ue-scope-btn {
  padding: 5px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  background: #fff;
  color: #475569;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
}
#ue-app .ue-scope-btn.active {
  border-color: #3b82f6;
  background: #eff6ff;
  color: #1d4ed8;
}
/* Textarea area */
#ue-app .ue-io-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
@media (max-width: 600px) {
  #ue-app .ue-io-row { grid-template-columns: 1fr; }
}
#ue-app .ue-io-block {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
#ue-app .ue-io-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#ue-app .ue-io-title {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}
#ue-app .ue-char-count {
  font-size: 11px;
  color: #94a3b8;
}
#ue-app textarea {
  width: 100%;
  min-height: 160px;
  padding: 12px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  font-family: "SFMono-Regular", "Fira Code", "Consolas", monospace;
  font-size: 13px;
  line-height: 1.6;
  color: #1e293b;
  background: #f8fafc;
  resize: vertical;
  transition: border-color 0.15s;
  outline: none;
}
#ue-app textarea:focus {
  border-color: #3b82f6;
  background: #fff;
}
#ue-app textarea.ue-output {
  background: #f0fdf4;
  border-color: #bbf7d0;
  color: #14532d;
}
#ue-app textarea.ue-output-decode {
  background: #fefce8;
  border-color: #fde68a;
  color: #78350f;
}
/* Action bar */
#ue-app .ue-action-bar {
  display: flex;
  gap: 10px;
  align-items: center;
  flex-wrap: wrap;
  margin-top: 16px;
}
#ue-app .ue-btn {
  padding: 9px 20px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  display: flex;
  align-items: center;
  gap: 6px;
}
#ue-app .ue-btn:active { transform: scale(0.97); }
#ue-app .ue-btn-primary {
  background: #3b82f6;
  color: #fff;
}
#ue-app .ue-btn-primary:hover { opacity: 0.88; }
#ue-app .ue-btn-secondary {
  background: #f1f5f9;
  color: #475569;
  border: 1.5px solid #e2e8f0;
}
#ue-app .ue-btn-secondary:hover { background: #e2e8f0; }
#ue-app .ue-btn-copy {
  background: #10b981;
  color: #fff;
}
#ue-app .ue-btn-copy:hover { opacity: 0.88; }
#ue-app .ue-auto-badge {
  margin-left: auto;
  font-size: 11px;
  color: #6366f1;
  font-weight: 600;
  background: #eef2ff;
  border-radius: 5px;
  padding: 3px 9px;
  border: 1px solid #c7d2fe;
}
/* Breakdown table */
#ue-app .ue-breakdown {
  margin-top: 20px;
}
#ue-app .ue-breakdown-title {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin-bottom: 10px;
}
#ue-app .ue-table-wrap {
  overflow-x: auto;
  border-radius: 8px;
  border: 1.5px solid #e2e8f0;
}
#ue-app table.ue-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
#ue-app table.ue-table th {
  background: #f8fafc;
  color: #64748b;
  font-weight: 700;
  padding: 8px 14px;
  text-align: left;
  border-bottom: 1.5px solid #e2e8f0;
}
#ue-app table.ue-table td {
  padding: 7px 14px;
  border-bottom: 1px solid #f1f5f9;
  font-family: "SFMono-Regular", "Fira Code", monospace;
  vertical-align: middle;
}
#ue-app table.ue-table tr:last-child td { border-bottom: none; }
#ue-app table.ue-table tr:nth-child(even) td { background: #f8fafc; }
#ue-app .ue-char-orig { color: #1e293b; font-weight: 600; }
#ue-app .ue-char-enc  { color: #1d4ed8; }
#ue-app .ue-char-note { color: #64748b; font-size: 12px; font-family: inherit; }
/* Toast */
#ue-app .ue-toast {
  position: fixed;
  bottom: 28px;
  right: 28px;
  background: #0f172a;
  color: #fff;
  padding: 11px 20px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s;
  z-index: 9999;
  box-shadow: 0 4px 16px rgba(0,0,0,0.25);
}
#ue-app .ue-toast.show { opacity: 1; }
/* Info box */
#ue-app .ue-info {
  background: #eff6ff;
  border: 1px solid #bfdbfe;
  border-radius: 8px;
  padding: 12px 16px;
  font-size: 13px;
  color: #1d4ed8;
  margin-top: 16px;
  line-height: 1.6;
}
</style>

<div class="ue-card">
  <h2 class="ue-title">URL Encoder / Decoder</h2>

  <!-- Mode toggle -->
  <div class="ue-mode-row">
    <span class="ue-mode-label">Mode:</span>
    <div class="ue-toggle-group">
      <button class="ue-toggle-btn active" id="ue-mode-encode" onclick="ueSetMode('encode')">Encode</button>
      <button class="ue-toggle-btn" id="ue-mode-decode" onclick="ueSetMode('decode')">Decode</button>
    </div>
    <div class="ue-scope-group" id="ue-scope-group">
      <span class="ue-scope-label">Scope:</span>
      <button class="ue-scope-btn active" id="ue-scope-component" onclick="ueSetScope('component')">Component <span style="font-weight:400;font-size:11px;">(encodeURIComponent)</span></button>
      <button class="ue-scope-btn" id="ue-scope-full" onclick="ueSetScope('full')">Full URL <span style="font-weight:400;font-size:11px;">(encodeURI)</span></button>
    </div>
  </div>

  <!-- I/O -->
  <div class="ue-io-row">
    <div class="ue-io-block">
      <div class="ue-io-header">
        <span class="ue-io-title" id="ue-input-label">Input</span>
        <span class="ue-char-count" id="ue-input-count">0 chars</span>
      </div>
      <textarea id="ue-input" placeholder="Paste your text or URL here…" oninput="ueOnInput()" spellcheck="false"></textarea>
    </div>
    <div class="ue-io-block">
      <div class="ue-io-header">
        <span class="ue-io-title" id="ue-output-label">Encoded Output</span>
        <span class="ue-char-count" id="ue-output-count">0 chars</span>
      </div>
      <textarea id="ue-output" class="ue-output" readonly placeholder="Result will appear here…" spellcheck="false"></textarea>
    </div>
  </div>

  <!-- Actions -->
  <div class="ue-action-bar">
    <button class="ue-btn ue-btn-primary" onclick="ueProcess()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="5 12 12 5 19 12"/><polyline points="5 19 12 12 19 19"/></svg>
      <span id="ue-process-label">Encode</span>
    </button>
    <button class="ue-btn ue-btn-copy" onclick="ueCopyResult()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
      Copy Result
    </button>
    <button class="ue-btn ue-btn-secondary" onclick="ueClear()">Clear</button>
    <button class="ue-btn ue-btn-secondary" onclick="ueSwap()">&#8645; Swap</button>
    <span class="ue-auto-badge" id="ue-auto-badge">Auto-detect ON</span>
  </div>

  <div class="ue-info" id="ue-scope-info">
    <strong>encodeURIComponent</strong> — Encodes all characters except: <code>A–Z a–z 0–9 - _ . ! ~ * ' ( )</code>. Best for encoding individual query parameters or path segments.
  </div>
</div>

<!-- Breakdown table -->
<div class="ue-card ue-breakdown" id="ue-breakdown-card" style="display:none;">
  <div class="ue-breakdown-title">Encoded Character Breakdown</div>
  <div class="ue-table-wrap">
    <table class="ue-table">
      <thead>
        <tr>
          <th>Original</th>
          <th>Encoded</th>
          <th>Unicode</th>
          <th>Note</th>
        </tr>
      </thead>
      <tbody id="ue-breakdown-body"></tbody>
    </table>
  </div>
</div>

<div class="ue-toast" id="ue-toast"></div>

<script>
(function() {
  var mode = 'encode';
  var scope = 'component';

  var charNotes = {
    ' ': 'Space',
    '!': 'Exclamation mark',
    '"': 'Quotation mark',
    '#': 'Hash / fragment',
    '$': 'Dollar sign',
    '%': 'Percent sign',
    '&': 'Ampersand',
    "'": 'Apostrophe',
    '(': 'Left paren',
    ')': 'Right paren',
    '*': 'Asterisk',
    '+': 'Plus sign',
    ',': 'Comma',
    '/': 'Forward slash',
    ':': 'Colon',
    ';': 'Semicolon',
    '=': 'Equals sign',
    '?': 'Question mark',
    '@': 'At sign',
    '[': 'Left bracket',
    ']': 'Right bracket',
  };

  window.ueSetMode = function(m) {
    mode = m;
    document.getElementById('ue-mode-encode').classList.toggle('active', m === 'encode');
    document.getElementById('ue-mode-decode').classList.toggle('active', m === 'decode');
    document.getElementById('ue-scope-group').style.display = m === 'encode' ? '' : 'none';
    document.getElementById('ue-scope-info').style.display = m === 'encode' ? '' : 'none';
    document.getElementById('ue-process-label').textContent = m === 'encode' ? 'Encode' : 'Decode';
    document.getElementById('ue-input-label').textContent = m === 'encode' ? 'Plain Text / URL' : 'Encoded URL';
    document.getElementById('ue-output-label').textContent = m === 'encode' ? 'Encoded Output' : 'Decoded Output';
    var out = document.getElementById('ue-output');
    out.className = m === 'encode' ? 'ue-output' : 'ue-output-decode';
    ueOnInput();
  };

  window.ueSetScope = function(s) {
    scope = s;
    document.getElementById('ue-scope-component').classList.toggle('active', s === 'component');
    document.getElementById('ue-scope-full').classList.toggle('active', s === 'full');
    var info = document.getElementById('ue-scope-info');
    if (s === 'component') {
      info.innerHTML = '<strong>encodeURIComponent</strong> — Encodes all characters except: <code>A–Z a–z 0–9 - _ . ! ~ * \' ( )</code>. Best for encoding individual query parameters or path segments.';
    } else {
      info.innerHTML = '<strong>encodeURI</strong> — Encodes all characters except those that are legal in a URI: <code>A–Z a–z 0–9 ; , / ? : @ & = + $ - _ . ! ~ * \' ( ) #</code>. Use for encoding a complete URL while preserving its structure.';
    }
    ueOnInput();
  };

  function ueEncode(text) {
    if (scope === 'component') return encodeURIComponent(text);
    return encodeURI(text);
  }

  function ueDecode(text) {
    try {
      return decodeURIComponent(text);
    } catch(e) {
      try { return decodeURI(text); } catch(e2) { return text; }
    }
  }

  function ueAutoDetect(text) {
    return /%[0-9A-Fa-f]{2}/.test(text) ? 'decode' : 'encode';
  }

  window.ueOnInput = function() {
    var input = document.getElementById('ue-input').value;
    document.getElementById('ue-input-count').textContent = input.length + ' chars';
    // Auto-detect
    if (input.length > 0) {
      var detected = ueAutoDetect(input);
      var badge = document.getElementById('ue-auto-badge');
      badge.textContent = 'Auto-detected: ' + (detected === 'decode' ? 'Decode' : 'Encode');
    } else {
      document.getElementById('ue-auto-badge').textContent = 'Auto-detect ON';
    }
    ueProcess();
  };

  window.ueProcess = function() {
    var input = document.getElementById('ue-input').value;
    if (!input) {
      document.getElementById('ue-output').value = '';
      document.getElementById('ue-output-count').textContent = '0 chars';
      document.getElementById('ue-breakdown-card').style.display = 'none';
      return;
    }
    var result;
    var effectiveMode = mode;
    // Auto-detect override
    if (mode === 'encode' && ueAutoDetect(input) === 'decode') {
      // Still respect user-chosen mode
    }
    try {
      result = effectiveMode === 'encode' ? ueEncode(input) : ueDecode(input);
    } catch(e) {
      result = 'Error: ' + e.message;
    }
    document.getElementById('ue-output').value = result;
    document.getElementById('ue-output-count').textContent = result.length + ' chars';
    if (effectiveMode === 'encode') ueRenderBreakdown(input, result);
    else document.getElementById('ue-breakdown-card').style.display = 'none';
  };

  function ueRenderBreakdown(original, encoded) {
    var rows = [];
    var seen = {};
    for (var i = 0; i < original.length; i++) {
      var ch = original[i];
      var encCh;
      try {
        encCh = scope === 'component' ? encodeURIComponent(ch) : encodeURI(ch);
      } catch(e) { encCh = ch; }
      if (encCh !== ch && !seen[ch]) {
        seen[ch] = true;
        var codePoint = ch.codePointAt ? ch.codePointAt(0) : ch.charCodeAt(0);
        var note = charNotes[ch] || (codePoint > 127 ? 'Non-ASCII character' : 'Special character');
        rows.push({ orig: ch, enc: encCh, uni: 'U+' + codePoint.toString(16).toUpperCase().padStart(4,'0'), note: note });
      }
    }
    var tbody = document.getElementById('ue-breakdown-body');
    var card = document.getElementById('ue-breakdown-card');
    if (rows.length === 0) { card.style.display = 'none'; return; }
    card.style.display = '';
    tbody.innerHTML = rows.map(function(r) {
      var disp = r.orig === ' ' ? '&nbsp;(space)' : r.orig.replace(/&/g,'&amp;').replace(/</g,'&lt;');
      return '<tr><td class="ue-char-orig">' + disp + '</td><td class="ue-char-enc">' + r.enc + '</td><td class="ue-char-enc">' + r.uni + '</td><td class="ue-char-note">' + r.note + '</td></tr>';
    }).join('');
  }

  window.ueCopyResult = function() {
    var val = document.getElementById('ue-output').value;
    if (!val) return;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(val).then(function() { ueShowToast('Copied to clipboard!'); });
    } else {
      var ta = document.getElementById('ue-output');
      ta.select();
      document.execCommand('copy');
      ueShowToast('Copied to clipboard!');
    }
  };

  window.ueClear = function() {
    document.getElementById('ue-input').value = '';
    document.getElementById('ue-output').value = '';
    document.getElementById('ue-input-count').textContent = '0 chars';
    document.getElementById('ue-output-count').textContent = '0 chars';
    document.getElementById('ue-breakdown-card').style.display = 'none';
    document.getElementById('ue-auto-badge').textContent = 'Auto-detect ON';
  };

  window.ueSwap = function() {
    var inp = document.getElementById('ue-input').value;
    var out = document.getElementById('ue-output').value;
    document.getElementById('ue-input').value = out;
    ueOnInput();
  };

  function ueShowToast(msg) {
    var t = document.getElementById('ue-toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(function() { t.classList.remove('show'); }, 2000);
  }
})();
</script>

</div>

---

## How It Works

**URL encoding** (percent-encoding) converts characters that are not safe for use in URLs into a `%XX` format, where `XX` is the hexadecimal value of the character's UTF-8 byte(s).

### When to use which mode

| Mode | Function | Safe characters (not encoded) |
|---|---|---|
| **encodeURIComponent** | Encode a single query param or path segment | `A–Z a–z 0–9 - _ . ! ~ * ' ( )` |
| **encodeURI** | Encode a full URL, preserving its structure | All of the above + `; , / ? : @ & = + $ #` |

### Common encoded characters

| Character | Encoded | Use case |
|---|---|---|
| Space | `%20` | Separates words in a path |
| `&` | `%26` | Ampersand in query value |
| `=` | `%3D` | Equals sign in query value |
| `+` | `%2B` | Plus sign in query value |
| `#` | `%23` | Hash character in URL |
| `?` | `%3F` | Question mark in URL |

---

> Encode HTML entities → [HTML Entity Encoder](/tools/html-entity-encoder/)
> Convert encodings → [Universal Encoder/Decoder](/tools/encoder-decoder/)
