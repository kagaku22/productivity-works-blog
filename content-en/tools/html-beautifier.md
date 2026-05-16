---
title: "HTML Beautifier & Formatter"
date: 2025-05-16
description: "Free online HTML beautifier and formatter. Indent, format, or minify HTML code instantly. Customizable indentation, syntax highlighting, and one-click copy."
categories: ["Free Tools"]
slug: "html-beautifier"
ShowToc: false
cover:
  image: "/images/covers/html-beautifier.png"
  alt: "HTML Beautifier & Formatter"
---

<div id="hb-app">

<style>
#hb-app *,
#hb-app *::before,
#hb-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#hb-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.5;
}

#hb-app .hb-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 12px;
}

#hb-app .hb-toolbar-group {
  display: flex;
  align-items: center;
  gap: 6px;
  flex-wrap: wrap;
}

#hb-app .hb-toolbar-sep {
  width: 1px;
  height: 28px;
  background: #e2e8f0;
  margin: 0 2px;
}

#hb-app .hb-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 7px 14px;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  white-space: nowrap;
  line-height: 1;
}
#hb-app .hb-btn:active { transform: scale(0.97); }
#hb-app .hb-btn-primary   { background: #2563eb; color: #fff; }
#hb-app .hb-btn-primary:hover   { background: #1d4ed8; }
#hb-app .hb-btn-secondary { background: #f1f5f9; color: #334155; border: 1px solid #cbd5e1; }
#hb-app .hb-btn-secondary:hover { background: #e2e8f0; }
#hb-app .hb-btn-success   { background: #16a34a; color: #fff; }
#hb-app .hb-btn-success:hover   { background: #15803d; }
#hb-app .hb-btn-orange    { background: #d97706; color: #fff; }
#hb-app .hb-btn-orange:hover    { background: #b45309; }
#hb-app .hb-btn-danger    { background: #dc2626; color: #fff; }
#hb-app .hb-btn-danger:hover    { background: #b91c1c; }

#hb-app .hb-select {
  padding: 7px 10px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  background: #fff;
  color: #334155;
  cursor: pointer;
}

#hb-app .hb-label {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  white-space: nowrap;
}

#hb-app .hb-toggle-wrap {
  display: flex;
  align-items: center;
  gap: 6px;
  cursor: pointer;
  user-select: none;
}
#hb-app .hb-toggle-wrap input[type="checkbox"] {
  width: 16px;
  height: 16px;
  cursor: pointer;
  accent-color: #2563eb;
}

/* View toggle */
#hb-app .hb-view-toggle {
  display: flex;
  gap: 0;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  overflow: hidden;
}
#hb-app .hb-view-btn {
  padding: 6px 12px;
  border: none;
  background: #f8fafc;
  color: #64748b;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#hb-app .hb-view-btn.active {
  background: #2563eb;
  color: #fff;
}
#hb-app .hb-view-btn:not(.active):hover { background: #e2e8f0; }

/* Panels */
#hb-app .hb-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 12px;
}
#hb-app .hb-panels.stacked {
  grid-template-columns: 1fr;
}
@media (max-width: 700px) {
  #hb-app .hb-panels { grid-template-columns: 1fr; }
  #hb-app .hb-toolbar-sep { display: none; }
}

#hb-app .hb-panel {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

#hb-app .hb-panel-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#hb-app .hb-panel-label {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

#hb-app .hb-count {
  font-size: 11px;
  color: #94a3b8;
  font-weight: 500;
}

/* Editor wrapper */
#hb-app .hb-editor-wrap {
  position: relative;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  overflow: hidden;
  background: #fafafa;
}

#hb-app .hb-with-lines {
  display: flex;
}

#hb-app .hb-line-nums {
  width: 36px;
  min-width: 36px;
  background: #f1f5f9;
  color: #94a3b8;
  font-family: "JetBrains Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 12px;
  line-height: 1.6;
  padding: 10px 0;
  text-align: right;
  padding-right: 6px;
  user-select: none;
  overflow: hidden;
  border-right: 1px solid #e2e8f0;
}
#hb-app .hb-line-nums span { display: block; }

#hb-app .hb-textarea {
  width: 100%;
  min-height: 300px;
  padding: 10px 12px;
  border: none;
  background: transparent;
  font-family: "JetBrains Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 13px;
  line-height: 1.6;
  color: #1e293b;
  resize: vertical;
  outline: none;
}

/* Output / syntax highlighted */
#hb-app .hb-output-wrap {
  position: relative;
  min-height: 300px;
  overflow: auto;
  background: #0f172a;
  border-radius: 6px;
  padding: 10px 12px;
}

#hb-app .hb-output-pre {
  font-family: "JetBrains Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 13px;
  line-height: 1.6;
  white-space: pre;
  color: #e2e8f0;
  margin: 0;
}

/* Syntax colors */
#hb-app .hl-tag    { color: #7dd3fc; }   /* tag names */
#hb-app .hl-attr   { color: #fbbf24; }   /* attribute names */
#hb-app .hl-val    { color: #86efac; }   /* attribute values */
#hb-app .hl-cmt    { color: #64748b; font-style: italic; } /* comments */
#hb-app .hl-entity { color: #f9a8d4; }   /* entities */
#hb-app .hl-doctype{ color: #a78bfa; }   /* doctype */
#hb-app .hl-punct  { color: #94a3b8; }   /* < > = / */
#hb-app .hl-text   { color: #e2e8f0; }

/* Status bar */
#hb-app .hb-status {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 9px 14px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  min-height: 40px;
  margin-bottom: 10px;
}
#hb-app .hb-status.hb-idle  { background: #f8fafc; color: #64748b; border: 1px solid #e2e8f0; }
#hb-app .hb-status.hb-ok    { background: #f0fdf4; color: #16a34a; border: 1px solid #bbf7d0; }
#hb-app .hb-status.hb-err   { background: #fef2f2; color: #dc2626; border: 1px solid #fecaca; }

#hb-app .hb-stats {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  margin-bottom: 12px;
}
#hb-app .hb-stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 8px 16px;
  min-width: 80px;
}
#hb-app .hb-stat-val {
  font-size: 20px;
  font-weight: 700;
  color: #2563eb;
  line-height: 1.2;
}
#hb-app .hb-stat-lbl {
  font-size: 11px;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-top: 2px;
}

/* Copy toast */
#hb-app .hb-toast {
  position: fixed;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #1e293b;
  color: #fff;
  padding: 10px 22px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s, transform 0.2s;
  z-index: 9999;
  white-space: nowrap;
}
#hb-app .hb-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

/* Copy btn inside output */
#hb-app .hb-copy-overlay {
  position: absolute;
  top: 8px;
  right: 8px;
}
#hb-app .hb-copy-overlay .hb-btn {
  font-size: 12px;
  padding: 5px 11px;
  opacity: 0.85;
}
#hb-app .hb-copy-overlay .hb-btn:hover { opacity: 1; }
</style>

<!-- Toolbar -->
<div class="hb-toolbar">
  <div class="hb-toolbar-group">
    <button class="hb-btn hb-btn-primary" id="hb-beautify-btn">&#10024; Beautify</button>
    <button class="hb-btn hb-btn-orange"  id="hb-minify-btn">&#9889; Minify</button>
    <button class="hb-btn hb-btn-danger"  id="hb-clear-btn">&#10005; Clear</button>
  </div>
  <div class="hb-toolbar-sep"></div>
  <div class="hb-toolbar-group">
    <span class="hb-label">Indent:</span>
    <select class="hb-select" id="hb-indent-sel">
      <option value="2">2 Spaces</option>
      <option value="4" selected>4 Spaces</option>
      <option value="tab">Tab</option>
    </select>
  </div>
  <div class="hb-toolbar-sep"></div>
  <div class="hb-toolbar-group">
    <label class="hb-toggle-wrap">
      <input type="checkbox" id="hb-wrap-chk">
      <span class="hb-label">Wrap long lines</span>
    </label>
  </div>
  <div class="hb-toolbar-sep"></div>
  <div class="hb-toolbar-group">
    <span class="hb-label">View:</span>
    <div class="hb-view-toggle">
      <button class="hb-view-btn active" id="hb-view-side">Side-by-side</button>
      <button class="hb-view-btn" id="hb-view-stack">Stacked</button>
    </div>
  </div>
</div>

<!-- Stats -->
<div class="hb-stats" id="hb-stats-bar">
  <div class="hb-stat-item"><span class="hb-stat-val" id="hb-stat-chars">0</span><span class="hb-stat-lbl">Chars</span></div>
  <div class="hb-stat-item"><span class="hb-stat-val" id="hb-stat-lines">0</span><span class="hb-stat-lbl">Lines</span></div>
  <div class="hb-stat-item"><span class="hb-stat-val" id="hb-stat-out-chars">–</span><span class="hb-stat-lbl">Out Chars</span></div>
  <div class="hb-stat-item"><span class="hb-stat-val" id="hb-stat-out-lines">–</span><span class="hb-stat-lbl">Out Lines</span></div>
  <div class="hb-stat-item"><span class="hb-stat-val" id="hb-stat-tags">–</span><span class="hb-stat-lbl">Tags</span></div>
</div>

<!-- Status -->
<div class="hb-status hb-idle" id="hb-status">
  &#8635; Paste HTML on the left and click Beautify or Minify.
</div>

<!-- Panels -->
<div class="hb-panels" id="hb-panels">
  <!-- Input -->
  <div class="hb-panel">
    <div class="hb-panel-header">
      <span class="hb-panel-label">Input HTML</span>
      <span class="hb-count" id="hb-in-count">0 chars</span>
    </div>
    <div class="hb-editor-wrap">
      <div class="hb-with-lines">
        <div class="hb-line-nums" id="hb-in-lines"><span>1</span></div>
        <textarea class="hb-textarea" id="hb-input" placeholder="Paste your HTML here…" spellcheck="false" autocomplete="off" autocorrect="off" autocapitalize="off"></textarea>
      </div>
    </div>
  </div>
  <!-- Output -->
  <div class="hb-panel">
    <div class="hb-panel-header">
      <span class="hb-panel-label">Output</span>
      <span class="hb-count" id="hb-out-count">–</span>
    </div>
    <div class="hb-editor-wrap" style="background:#0f172a;">
      <div class="hb-output-wrap" id="hb-output-wrap">
        <pre class="hb-output-pre" id="hb-output"><span style="color:#475569;">// Output will appear here</span></pre>
        <div class="hb-copy-overlay">
          <button class="hb-btn hb-btn-success" id="hb-copy-btn">&#128203; Copy</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Toast -->
<div class="hb-toast" id="hb-toast">Copied to clipboard!</div>

<script>
(function(){
  'use strict';

  var input      = document.getElementById('hb-input');
  var output     = document.getElementById('hb-output');
  var outWrap    = document.getElementById('hb-output-wrap');
  var statusEl   = document.getElementById('hb-status');
  var inCount    = document.getElementById('hb-in-count');
  var outCount   = document.getElementById('hb-out-count');
  var inLines    = document.getElementById('hb-in-lines');
  var indentSel  = document.getElementById('hb-indent-sel');
  var wrapChk    = document.getElementById('hb-wrap-chk');
  var panels     = document.getElementById('hb-panels');
  var toast      = document.getElementById('hb-toast');

  var statChars    = document.getElementById('hb-stat-chars');
  var statLines    = document.getElementById('hb-stat-lines');
  var statOutChars = document.getElementById('hb-stat-out-chars');
  var statOutLines = document.getElementById('hb-stat-out-lines');
  var statTags     = document.getElementById('hb-stat-tags');

  var lastOutput = '';
  var toastTimer = null;

  /* ── Indent helper ── */
  function getIndent() {
    var v = indentSel.value;
    if (v === 'tab') return '\t';
    return ' '.repeat(parseInt(v, 10));
  }

  /* ── Syntax highlighter ── */
  function escape(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function highlight(code) {
    // We process token by token using a simple state machine
    var result = '';
    var i = 0;
    var len = code.length;

    while (i < len) {
      // Comment
      if (code.slice(i, i+4) === '<!--') {
        var end = code.indexOf('-->', i+4);
        if (end === -1) end = len - 3;
        var cmt = code.slice(i, end+3);
        result += '<span class="hl-cmt">' + escape(cmt) + '</span>';
        i = end + 3;
        continue;
      }
      // Doctype
      if (code.slice(i, i+2) === '<!' && code.slice(i,i+9).toLowerCase() !== '<!--') {
        var end2 = code.indexOf('>', i);
        if (end2 === -1) end2 = len - 1;
        result += '<span class="hl-doctype">' + escape(code.slice(i, end2+1)) + '</span>';
        i = end2 + 1;
        continue;
      }
      // Tag
      if (code[i] === '<') {
        var end3 = code.indexOf('>', i);
        if (end3 === -1) { result += escape(code.slice(i)); i = len; continue; }
        var tagContent = code.slice(i, end3+1);
        result += highlightTag(tagContent);
        i = end3 + 1;
        continue;
      }
      // Text node
      var next = code.indexOf('<', i);
      if (next === -1) next = len;
      var txt = code.slice(i, next);
      // highlight entities
      result += '<span class="hl-text">' + escape(txt).replace(/&amp;[a-zA-Z0-9#]+;/g, function(m){ return '<span class="hl-entity">'+m+'</span>'; }) + '</span>';
      i = next;
    }
    return result;
  }

  function highlightTag(tag) {
    // tag = e.g. <div class="foo" id="bar"> or </div> or <br/>
    var out = '';
    var inner = tag.slice(1, tag.endsWith('/>') ? -2 : (tag.endsWith('>') ? -1 : tag.length));
    var isClose = inner.startsWith('/');
    if (isClose) inner = inner.slice(1);

    // tag name
    var nameMatch = inner.match(/^([a-zA-Z0-9:\-_]+)([\s\S]*)?$/);
    if (!nameMatch) return '<span class="hl-punct">' + escape(tag) + '</span>';

    var tagName = nameMatch[1];
    var rest = nameMatch[2] || '';

    out += '<span class="hl-punct">&lt;</span>';
    if (isClose) out += '<span class="hl-punct">/</span>';
    out += '<span class="hl-tag">' + escape(tagName) + '</span>';

    // Parse attributes
    var attrReg = /\s+([a-zA-Z0-9\-_:@.]+)(?:\s*=\s*(?:"([^"]*?)"|'([^']*?)'|([^\s>]+)))?/g;
    var m;
    var lastIdx = 0;
    while ((m = attrReg.exec(rest)) !== null) {
      // whitespace before attr
      var ws = rest.slice(lastIdx, m.index + (m[0].match(/^\s+/) || [''])[0].length);
      out += escape(ws.replace(/[^ \t\n\r]/g, ''));

      var spaceLen = (m[0].match(/^\s+/) || [''])[0].length;
      out += escape(rest.slice(m.index, m.index + spaceLen));

      out += '<span class="hl-attr">' + escape(m[1]) + '</span>';
      if (m[2] !== undefined || m[3] !== undefined || m[4] !== undefined) {
        var val = m[2] !== undefined ? '"'+m[2]+'"' : (m[3] !== undefined ? "'"+m[3]+"'" : m[4]);
        var q = m[2] !== undefined ? '"' : (m[3] !== undefined ? "'" : '');
        out += '<span class="hl-punct">=</span>';
        out += '<span class="hl-val">' + escape(val) + '</span>';
      }
      lastIdx = m.index + m[0].length;
    }
    // remaining (spaces, self-close slash)
    var rem = rest.slice(lastIdx);
    if (rem) out += escape(rem);

    if (tag.endsWith('/>')) out += '<span class="hl-punct">/&gt;</span>';
    else out += '<span class="hl-punct">&gt;</span>';

    return out;
  }

  /* ── HTML Beautifier ── */
  function beautifyHTML(html, indent) {
    var INLINE = 'a abbr acronym b bdo big br cite code dfn em i img input kbd label map object output q samp select small span strong sub sup textarea time tt var button'.split(' ');
    var VOID   = 'area base br col embed hr img input link meta param source track wbr'.split(' ');

    var lines = [];
    var level = 0;
    // Tokenize
    var tokens = [];
    var re = /(<!--[\s\S]*?-->|<!DOCTYPE[^>]*>|<\/[a-zA-Z0-9:\-]+\s*>|<[a-zA-Z0-9:\-]+(?:\s[^>]*?)?\s*\/?>|[^<]+)/gi;
    var m;
    while ((m = re.exec(html)) !== null) {
      var tok = m[0];
      if (tok.trim()) tokens.push(tok);
    }

    tokens.forEach(function(tok) {
      var trimmed = tok.trim();
      if (!trimmed) return;

      // Comment or doctype
      if (trimmed.startsWith('<!--') || trimmed.startsWith('<!')) {
        lines.push(indent.repeat(level) + trimmed);
        return;
      }
      // Closing tag
      if (trimmed.startsWith('</')) {
        level = Math.max(0, level - 1);
        lines.push(indent.repeat(level) + trimmed);
        return;
      }
      // Opening tag
      if (trimmed.startsWith('<')) {
        var nameM = trimmed.match(/^<([a-zA-Z0-9:\-]+)/i);
        var name = nameM ? nameM[1].toLowerCase() : '';
        var isVoid = VOID.indexOf(name) !== -1;
        var isSelfClose = trimmed.endsWith('/>');
        var isInline = INLINE.indexOf(name) !== -1;

        lines.push(indent.repeat(level) + trimmed);

        if (!isVoid && !isSelfClose) {
          level++;
        }
        return;
      }
      // Text node
      lines.push(indent.repeat(level) + trimmed);
    });

    return lines.join('\n');
  }

  /* ── HTML Minifier ── */
  function minifyHTML(html) {
    return html
      .replace(/<!--[\s\S]*?-->/g, '')           // remove comments
      .replace(/\s+/g, ' ')                        // collapse whitespace
      .replace(/>\s+</g, '><')                     // remove space between tags
      .replace(/\s*=\s*/g, '=')                    // remove spaces around =
      .replace(/"\s+>/g, '">')                     // clean closing
      .trim();
  }

  /* ── Count tags ── */
  function countTags(html) {
    var m = html.match(/<[a-zA-Z][a-zA-Z0-9:\-]*/g);
    return m ? m.length : 0;
  }

  /* ── Update line numbers ── */
  function updateLineNums() {
    var val = input.value;
    var count = (val.match(/\n/g) || []).length + 1;
    var html = '';
    for (var i = 1; i <= count; i++) html += '<span>' + i + '</span>';
    inLines.innerHTML = html;
    // sync scroll
    inLines.scrollTop = input.scrollTop;
  }

  /* ── Update input stats ── */
  function updateInputStats() {
    var val = input.value;
    var chars = val.length;
    var lines = val ? val.split('\n').length : 0;
    inCount.textContent = chars + ' chars';
    statChars.textContent = chars.toLocaleString();
    statLines.textContent = lines.toLocaleString();
    updateLineNums();
  }

  /* ── Set status ── */
  function setStatus(type, msg) {
    statusEl.className = 'hb-status hb-' + type;
    statusEl.innerHTML = msg;
  }

  /* ── Render output ── */
  function renderOutput(text, mode) {
    lastOutput = text;
    var chars = text.length;
    var lines = text ? text.split('\n').length : 0;
    outCount.textContent = chars + ' chars';
    statOutChars.textContent = chars.toLocaleString();
    statOutLines.textContent = lines.toLocaleString();
    statTags.textContent = countTags(text).toLocaleString();

    var hl = highlight(text);
    output.innerHTML = hl;

    if (wrapChk.checked) {
      outWrap.style.whiteSpace = 'pre-wrap';
      output.style.whiteSpace = 'pre-wrap';
    } else {
      outWrap.style.whiteSpace = '';
      output.style.whiteSpace = 'pre';
    }

    var label = mode === 'minify' ? 'Minified' : 'Beautified';
    setStatus('ok', '&#10003; ' + label + ' &mdash; ' + chars.toLocaleString() + ' chars, ' + lines.toLocaleString() + ' lines');
  }

  /* ── Beautify handler ── */
  document.getElementById('hb-beautify-btn').addEventListener('click', function() {
    var val = input.value.trim();
    if (!val) { setStatus('err', '&#9888; Please paste some HTML first.'); return; }
    var indent = getIndent();
    try {
      var result = beautifyHTML(val, indent);
      renderOutput(result, 'beautify');
    } catch(e) {
      setStatus('err', '&#9888; Error: ' + e.message);
    }
  });

  /* ── Minify handler ── */
  document.getElementById('hb-minify-btn').addEventListener('click', function() {
    var val = input.value.trim();
    if (!val) { setStatus('err', '&#9888; Please paste some HTML first.'); return; }
    try {
      var result = minifyHTML(val);
      renderOutput(result, 'minify');
    } catch(e) {
      setStatus('err', '&#9888; Error: ' + e.message);
    }
  });

  /* ── Clear handler ── */
  document.getElementById('hb-clear-btn').addEventListener('click', function() {
    input.value = '';
    output.innerHTML = '<span style="color:#475569;">// Output will appear here</span>';
    lastOutput = '';
    outCount.textContent = '–';
    statOutChars.textContent = '–';
    statOutLines.textContent = '–';
    statTags.textContent = '–';
    setStatus('idle', '&#8635; Paste HTML on the left and click Beautify or Minify.');
    updateInputStats();
  });

  /* ── Copy handler ── */
  document.getElementById('hb-copy-btn').addEventListener('click', function() {
    if (!lastOutput) return;
    var el = this;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(lastOutput).then(showToast);
    } else {
      var ta = document.createElement('textarea');
      ta.value = lastOutput;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showToast();
    }
  });

  function showToast() {
    toast.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(function(){ toast.classList.remove('show'); }, 2000);
  }

  /* ── Wrap toggle ── */
  wrapChk.addEventListener('change', function() {
    if (lastOutput) {
      if (this.checked) {
        outWrap.style.whiteSpace = 'pre-wrap';
        output.style.whiteSpace = 'pre-wrap';
      } else {
        outWrap.style.whiteSpace = '';
        output.style.whiteSpace = 'pre';
      }
    }
  });

  /* ── View toggle ── */
  document.getElementById('hb-view-side').addEventListener('click', function() {
    panels.classList.remove('stacked');
    this.classList.add('active');
    document.getElementById('hb-view-stack').classList.remove('active');
  });
  document.getElementById('hb-view-stack').addEventListener('click', function() {
    panels.classList.add('stacked');
    this.classList.add('active');
    document.getElementById('hb-view-side').classList.remove('active');
  });

  /* ── Input events ── */
  input.addEventListener('input', updateInputStats);
  input.addEventListener('scroll', function() { inLines.scrollTop = this.scrollTop; });
  input.addEventListener('keydown', function(e) {
    if (e.key === 'Tab') {
      e.preventDefault();
      var start = this.selectionStart;
      var end = this.selectionEnd;
      var indent = getIndent();
      this.value = this.value.slice(0, start) + indent + this.value.slice(end);
      this.selectionStart = this.selectionEnd = start + indent.length;
      updateInputStats();
    }
  });

  /* ── Init ── */
  updateInputStats();

  /* ── Sample HTML ── */
  var sample = '<!DOCTYPE html>\n<html lang="en">\n<head>\n<meta charset="UTF-8">\n<title>Sample Page</title>\n<link rel="stylesheet" href="style.css">\n</head>\n<body>\n<header>\n<h1>Hello World</h1>\n<nav>\n<a href="/">Home</a>\n<a href="/about">About</a>\n</nav>\n</header>\n<main>\n<p>This is a <strong>sample</strong> HTML document for the <em>beautifier</em>.</p>\n<ul>\n<li>Item one</li>\n<li>Item two</li>\n<li>Item three</li>\n</ul>\n</main>\n<footer><p>&copy; 2025 Example</p></footer>\n</body>\n</html>';
  input.value = sample;
  updateInputStats();

})();
</script>

</div>

---

> Convert HTML &rarr; [HTML to Markdown](/tools/html-to-markdown/)

> Format XML &rarr; [XML Formatter](/tools/xml-formatter/)
