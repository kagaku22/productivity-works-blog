---
title: "JSON Formatter & Validator - Free Online JSON Tool"
date: 2025-05-16
description: "Format, validate, and minify JSON data instantly. Syntax highlighting, error detection, tree view, and copy-to-clipboard. Free online developer tool."
categories: ["Free Tools"]
tags: ["json", "formatter", "validator", "developer tool", "code"]
slug: "json-formatter"
aliases: ["/tools/json-validator/", "/tools/json-beautifier/", "/tools/json-minifier/"]
cover:
  image: "/images/covers/json-formatter.png"
  alt: "JSON Formatter"
ShowToc: false
---

<div id="json-app">

<style>
#json-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #1e1e2e;
  color: #cdd6f4;
  border-radius: 12px;
  padding: 20px;
  margin: 0 auto;
  max-width: 1100px;
  box-sizing: border-box;
}

#json-app * {
  box-sizing: border-box;
}

.json-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 16px;
}

.json-toolbar label {
  color: #a6adc8;
  font-size: 13px;
  margin-right: 2px;
}

.json-btn {
  padding: 7px 16px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  outline: none;
}

.json-btn:active {
  transform: scale(0.97);
}

.json-btn:hover {
  opacity: 0.88;
}

.btn-format  { background: #89b4fa; color: #1e1e2e; }
.btn-minify  { background: #a6e3a1; color: #1e1e2e; }
.btn-validate{ background: #f9e2af; color: #1e1e2e; }
.btn-copy    { background: #cba6f7; color: #1e1e2e; }
.btn-clear   { background: #45475a; color: #cdd6f4; }
.btn-sample  { background: #313244; color: #89b4fa; border: 1px solid #89b4fa; }
.btn-tree    { background: #313244; color: #94e2d5; border: 1px solid #94e2d5; }
.btn-tree.active { background: #94e2d5; color: #1e1e2e; }

.indent-select {
  background: #313244;
  color: #cdd6f4;
  border: 1px solid #45475a;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 13px;
  cursor: pointer;
  outline: none;
}

.indent-select:focus {
  border-color: #89b4fa;
}

.json-panes {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

@media (max-width: 700px) {
  .json-panes {
    grid-template-columns: 1fr;
  }
}

.json-pane {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.pane-label {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #a6adc8;
}

.json-input {
  width: 100%;
  min-height: 340px;
  background: #11111b;
  color: #cdd6f4;
  border: 2px solid #313244;
  border-radius: 9px;
  padding: 14px;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.65;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  tab-size: 2;
}

.json-input:focus {
  border-color: #89b4fa;
}

.json-input.error {
  border-color: #f38ba8;
}

.json-output {
  width: 100%;
  min-height: 340px;
  background: #11111b;
  border: 2px solid #313244;
  border-radius: 9px;
  padding: 14px;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.65;
  overflow: auto;
  white-space: pre;
  word-break: break-all;
  white-space: pre-wrap;
  transition: border-color 0.2s;
}

.json-output.valid {
  border-color: #a6e3a1;
}

.json-output.error {
  border-color: #f38ba8;
}

.json-tree {
  width: 100%;
  min-height: 340px;
  background: #11111b;
  border: 2px solid #45475a;
  border-radius: 9px;
  padding: 14px;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.7;
  overflow: auto;
  display: none;
}

.json-tree.visible {
  display: block;
}

.status-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 10px;
  font-size: 12px;
  color: #6c7086;
}

.status-item {
  display: flex;
  align-items: center;
  gap: 4px;
}

.status-ok   { color: #a6e3a1; }
.status-err  { color: #f38ba8; }
.status-info { color: #89b4fa; }

.error-msg {
  background: #1a0a0a;
  border: 1px solid #f38ba8;
  border-radius: 7px;
  color: #f38ba8;
  font-size: 13px;
  padding: 10px 14px;
  margin-top: 6px;
  display: none;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
}

.error-msg.visible {
  display: block;
}

.copy-toast {
  position: fixed;
  bottom: 32px;
  right: 32px;
  background: #a6e3a1;
  color: #1e1e2e;
  font-weight: 700;
  font-size: 14px;
  padding: 10px 22px;
  border-radius: 8px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.4);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s;
  z-index: 9999;
}

.copy-toast.show {
  opacity: 1;
}

/* Syntax highlight colors */
.jt-key    { color: #89b4fa; }
.jt-str    { color: #a6e3a1; }
.jt-num    { color: #fab387; }
.jt-bool   { color: #cba6f7; }
.jt-null   { color: #f38ba8; }
.jt-punc   { color: #6c7086; }

/* Tree view */
.tree-node { }
.tree-toggle {
  cursor: pointer;
  user-select: none;
  color: #89b4fa;
  font-weight: 700;
  margin-right: 2px;
}
.tree-toggle:hover { color: #cdd6f4; }
.tree-children { margin-left: 20px; }
.tree-key   { color: #89b4fa; }
.tree-str   { color: #a6e3a1; }
.tree-num   { color: #fab387; }
.tree-bool  { color: #cba6f7; }
.tree-null  { color: #f38ba8; }
.tree-meta  { color: #6c7086; font-size: 11px; margin-left: 6px; }
.tree-collapsed > .tree-children { display: none; }
</style>

<div class="json-toolbar">
  <button class="json-btn btn-format" onclick="jsonFormat()">Format / Beautify</button>
  <label for="json-indent">Indent:</label>
  <select id="json-indent" class="indent-select">
    <option value="2">2 spaces</option>
    <option value="4">4 spaces</option>
    <option value="tab">Tab</option>
  </select>
  <button class="json-btn btn-minify" onclick="jsonMinify()">Minify</button>
  <button class="json-btn btn-validate" onclick="jsonValidate()">Validate</button>
  <button class="json-btn btn-tree" id="treeToggleBtn" onclick="jsonToggleTree()">Tree View</button>
  <button class="json-btn btn-copy" onclick="jsonCopy()">Copy Output</button>
  <button class="json-btn btn-sample" onclick="jsonSample()">Sample JSON</button>
  <button class="json-btn btn-clear" onclick="jsonClear()">Clear</button>
</div>

<div class="json-panes">
  <div class="json-pane">
    <div class="pane-label">Input</div>
    <textarea
      id="json-input"
      class="json-input"
      placeholder='Paste your JSON here…&#10;&#10;{"name": "example", "value": 42}'
      oninput="jsonOnInput()"
      spellcheck="false"
    ></textarea>
    <div class="status-bar">
      <span class="status-item" id="stat-chars">Chars: 0</span>
      <span class="status-item" id="stat-lines">Lines: 1</span>
    </div>
  </div>

  <div class="json-pane">
    <div class="pane-label">Output</div>
    <div id="json-output" class="json-output"><span style="color:#45475a">// Formatted output will appear here</span></div>
    <div id="json-tree-view" class="json-tree"></div>
    <div id="json-error" class="error-msg"></div>
    <div class="status-bar" id="stat-output-bar"></div>
  </div>
</div>

<div class="copy-toast" id="copy-toast">Copied to clipboard!</div>

<script>
(function () {
  var treeVisible = false;

  /* ── Helpers ── */
  function getInput() {
    return document.getElementById('json-input').value;
  }

  function getIndent() {
    var v = document.getElementById('json-indent').value;
    return v === 'tab' ? '\t' : parseInt(v, 10);
  }

  function setOutput(html, state) {
    var el = document.getElementById('json-output');
    el.innerHTML = html;
    el.className = 'json-output' + (state ? ' ' + state : '');
  }

  function setError(msg) {
    var el = document.getElementById('json-error');
    if (msg) {
      el.textContent = msg;
      el.classList.add('visible');
    } else {
      el.textContent = '';
      el.classList.remove('visible');
    }
  }

  function setInputState(state) {
    var el = document.getElementById('json-input');
    el.className = 'json-input' + (state ? ' ' + state : '');
  }

  function updateStats(text) {
    document.getElementById('stat-chars').textContent = 'Chars: ' + text.length;
    document.getElementById('stat-lines').textContent = 'Lines: ' + (text.split('\n').length);
  }

  function setOutputStats(text, state) {
    var bar = document.getElementById('stat-output-bar');
    if (!text) { bar.innerHTML = ''; return; }
    var cls = state === 'valid' ? 'status-ok' : state === 'error' ? 'status-err' : 'status-info';
    bar.innerHTML =
      '<span class="status-item ' + cls + '">' +
      (state === 'valid' ? 'Valid JSON' : state === 'error' ? 'Invalid JSON' : '') +
      '</span>' +
      '<span class="status-item">Chars: ' + text.length + '</span>' +
      '<span class="status-item">Lines: ' + text.split('\n').length + '</span>';
  }

  /* ── Syntax Highlighting ── */
  function escapeHtml(s) {
    return s
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;');
  }

  function syntaxHighlight(json) {
    var escaped = escapeHtml(json);
    return escaped.replace(
      /("(\\u[a-fA-F0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+\-]?\d+)?|[{}\[\],:])/g,
      function (match) {
        var cls = 'jt-num';
        if (/^"/.test(match)) {
          if (/:$/.test(match)) {
            cls = 'jt-key';
          } else {
            cls = 'jt-str';
          }
        } else if (/true|false/.test(match)) {
          cls = 'jt-bool';
        } else if (/null/.test(match)) {
          cls = 'jt-null';
        } else if (/[{}\[\],:]/.test(match)) {
          cls = 'jt-punc';
        }
        return '<span class="' + cls + '">' + match + '</span>';
      }
    );
  }

  /* ── Parse with error location ── */
  function parseJSON(text) {
    try {
      return { ok: true, value: JSON.parse(text) };
    } catch (e) {
      var msg = e.message || String(e);
      // Try to extract position info
      var posMatch = msg.match(/position (\d+)/i);
      var lineNum = null;
      if (posMatch) {
        var pos = parseInt(posMatch[1], 10);
        var before = text.slice(0, pos);
        lineNum = before.split('\n').length;
      }
      return {
        ok: false,
        error: msg,
        line: lineNum
      };
    }
  }

  /* ── Actions ── */
  window.jsonFormat = function () {
    var text = getInput().trim();
    if (!text) { setOutput('<span style="color:#45475a">// Nothing to format</span>', ''); setError(''); return; }
    var result = parseJSON(text);
    if (!result.ok) {
      setInputState('error');
      setOutput('<span style="color:#45475a">// Fix errors first</span>', 'error');
      setError('Parse error' + (result.line ? ' (line ' + result.line + ')' : '') + ': ' + result.error);
      setOutputStats('', 'error');
      return;
    }
    setInputState('');
    setError('');
    var indent = getIndent();
    var formatted = JSON.stringify(result.value, null, indent);
    setOutput(syntaxHighlight(formatted), 'valid');
    setOutputStats(formatted, 'valid');
    if (treeVisible) renderTree(result.value);
  };

  window.jsonMinify = function () {
    var text = getInput().trim();
    if (!text) { setOutput('<span style="color:#45475a">// Nothing to minify</span>', ''); setError(''); return; }
    var result = parseJSON(text);
    if (!result.ok) {
      setInputState('error');
      setOutput('<span style="color:#45475a">// Fix errors first</span>', 'error');
      setError('Parse error' + (result.line ? ' (line ' + result.line + ')' : '') + ': ' + result.error);
      setOutputStats('', 'error');
      return;
    }
    setInputState('');
    setError('');
    var minified = JSON.stringify(result.value);
    setOutput('<span class="jt-punc">' + escapeHtml(minified) + '</span>', 'valid');
    setOutputStats(minified, 'valid');
  };

  window.jsonValidate = function () {
    var text = getInput().trim();
    if (!text) {
      setOutput('<span style="color:#45475a">// Enter JSON to validate</span>', '');
      setError('');
      setOutputStats('', '');
      return;
    }
    var result = parseJSON(text);
    if (result.ok) {
      setInputState('');
      setError('');
      setOutput('<span class="status-ok" style="font-size:15px;font-weight:700;">Valid JSON</span>\n\n<span style="color:#6c7086">// Your JSON is well-formed and valid.</span>', 'valid');
      setOutputStats(text, 'valid');
    } else {
      setInputState('error');
      var errHtml = '<span class="status-err" style="font-size:15px;font-weight:700;">Invalid JSON</span>';
      setOutput(errHtml, 'error');
      setError('Parse error' + (result.line ? ' at line ' + result.line : '') + ': ' + result.error);
      setOutputStats('', 'error');
    }
  };

  window.jsonClear = function () {
    document.getElementById('json-input').value = '';
    setOutput('<span style="color:#45475a">// Formatted output will appear here</span>', '');
    setError('');
    setInputState('');
    updateStats('');
    setOutputStats('', '');
    hideTree();
    document.getElementById('json-tree-view').innerHTML = '';
  };

  window.jsonSample = function () {
    var sample = {
      "name": "JSON Formatter",
      "version": "1.0.0",
      "description": "A free online JSON tool",
      "features": ["format", "minify", "validate", "syntax highlighting", "tree view"],
      "author": {
        "name": "Developer",
        "email": "dev@example.com",
        "active": true
      },
      "stats": {
        "users": 42000,
        "rating": 4.9,
        "premium": false,
        "deprecated": null
      },
      "tags": ["json", "developer", "tool"]
    };
    document.getElementById('json-input').value = JSON.stringify(sample, null, 2);
    jsonOnInput();
    jsonFormat();
  };

  window.jsonCopy = function () {
    var el = document.getElementById('json-output');
    var text = el.innerText || el.textContent;
    if (!text || text.trim() === '// Formatted output will appear here') return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(showToast);
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showToast();
    }
  };

  function showToast() {
    var t = document.getElementById('copy-toast');
    t.classList.add('show');
    setTimeout(function () { t.classList.remove('show'); }, 1800);
  }

  window.jsonOnInput = function () {
    var text = getInput();
    updateStats(text);
    setInputState('');
    setError('');
  };

  /* ── Tree View ── */
  window.jsonToggleTree = function () {
    treeVisible = !treeVisible;
    var btn = document.getElementById('treeToggleBtn');
    var treeEl = document.getElementById('json-tree-view');
    var outputEl = document.getElementById('json-output');

    if (treeVisible) {
      btn.classList.add('active');
      btn.textContent = 'Hide Tree';
      treeEl.classList.add('visible');
      outputEl.style.display = 'none';
      // Try to render tree from current input
      var text = getInput().trim();
      if (text) {
        var result = parseJSON(text);
        if (result.ok) {
          renderTree(result.value);
        } else {
          treeEl.innerHTML = '<span style="color:#f38ba8">// Render tree after fixing JSON errors.</span>';
        }
      } else {
        treeEl.innerHTML = '<span style="color:#45475a">// Tree view will appear here after formatting.</span>';
      }
    } else {
      hideTree();
    }
  };

  function hideTree() {
    treeVisible = false;
    var btn = document.getElementById('treeToggleBtn');
    var treeEl = document.getElementById('json-tree-view');
    var outputEl = document.getElementById('json-output');
    btn.classList.remove('active');
    btn.textContent = 'Tree View';
    treeEl.classList.remove('visible');
    outputEl.style.display = '';
  }

  function renderTree(data) {
    var treeEl = document.getElementById('json-tree-view');
    treeEl.innerHTML = buildTreeHTML(data, 0);
    // Attach toggle events
    treeEl.querySelectorAll('.tree-toggle').forEach(function (tog) {
      tog.addEventListener('click', function () {
        var node = tog.parentElement;
        node.classList.toggle('tree-collapsed');
        tog.textContent = node.classList.contains('tree-collapsed') ? '[+]' : '[-]';
      });
    });
  }

  function buildTreeHTML(val, depth) {
    if (val === null) return '<span class="tree-null">null</span>';
    if (typeof val === 'boolean') return '<span class="tree-bool">' + val + '</span>';
    if (typeof val === 'number') return '<span class="tree-num">' + val + '</span>';
    if (typeof val === 'string') return '<span class="tree-str">"' + escapeHtml(val) + '"</span>';

    if (Array.isArray(val)) {
      if (val.length === 0) return '<span class="jt-punc">[]</span>';
      var html = '<span class="tree-node">';
      html += '<span class="tree-toggle">[-]</span> <span class="jt-punc">[</span>';
      html += '<span class="tree-meta">' + val.length + ' item' + (val.length !== 1 ? 's' : '') + '</span>';
      html += '<div class="tree-children">';
      val.forEach(function (item, i) {
        html += '<div>';
        html += '<span class="tree-num">[' + i + ']</span>: ';
        html += buildTreeHTML(item, depth + 1);
        html += (i < val.length - 1 ? '<span class="jt-punc">,</span>' : '');
        html += '</div>';
      });
      html += '</div>';
      html += '<span class="jt-punc">]</span>';
      html += '</span>';
      return html;
    }

    if (typeof val === 'object') {
      var keys = Object.keys(val);
      if (keys.length === 0) return '<span class="jt-punc">{}</span>';
      var html = '<span class="tree-node">';
      html += '<span class="tree-toggle">[-]</span> <span class="jt-punc">{</span>';
      html += '<span class="tree-meta">' + keys.length + ' key' + (keys.length !== 1 ? 's' : '') + '</span>';
      html += '<div class="tree-children">';
      keys.forEach(function (k, i) {
        html += '<div>';
        html += '<span class="tree-key">"' + escapeHtml(k) + '"</span>: ';
        html += buildTreeHTML(val[k], depth + 1);
        html += (i < keys.length - 1 ? '<span class="jt-punc">,</span>' : '');
        html += '</div>';
      });
      html += '</div>';
      html += '<span class="jt-punc">}</span>';
      html += '</span>';
      return html;
    }

    return escapeHtml(String(val));
  }

  // Keyboard shortcut: Ctrl+Enter to format
  document.getElementById('json-input').addEventListener('keydown', function (e) {
    if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') {
      e.preventDefault();
      jsonFormat();
    }
  });

})();
</script>

</div>

---

## What is JSON?

JSON (JavaScript Object Notation) is a lightweight, human-readable data interchange format originally derived from JavaScript object syntax. It uses a simple structure of key-value pairs, arrays, strings, numbers, booleans, and null values, making it straightforward to read and write for humans while remaining easy to parse and generate for machines. Today JSON has become the de facto standard for data exchange in web APIs, configuration files, and inter-service communication across virtually every programming language and platform.

Because JSON is strictly text-based and language-independent, it is widely used for transmitting structured data between a web server and a browser, between microservices, and in NoSQL databases such as MongoDB. However, even minor syntax issues — a missing comma, an extra bracket, or an unquoted key — will render a JSON document invalid and cause parsing failures. Tools like this formatter help you instantly spot and fix such errors, beautify minified payloads for readability, and verify that your data conforms to the JSON specification before integrating it into your application.

---

## How to Use This JSON Formatter

**Format / Beautify** — Paste raw or minified JSON into the left pane and click "Format / Beautify" (or press Ctrl+Enter). The tool parses the input and displays it with consistent indentation and syntax coloring on the right. Use the indent selector to choose 2 spaces, 4 spaces, or tabs.

**Minify** — Click "Minify" to strip all whitespace and produce the most compact JSON string, ideal for reducing payload size in API calls.

**Validate** — Click "Validate" to check whether your JSON is well-formed. If errors are found, the exact error message and line number are displayed below the output pane so you can jump straight to the problem.

**Tree View** — Toggle "Tree View" to explore nested objects and arrays as a collapsible tree. Click the `[-]` / `[+]` buttons to expand or collapse any branch.

**Copy Output** — After formatting or minifying, click "Copy Output" to copy the result to your clipboard with one click.

**Sample JSON** — Click "Sample JSON" to load a built-in example and see the tool in action immediately.

---

## Related Tools

> Count words and characters in your text → [Word Counter](/tools/word-counter/)

> Generate secure passwords → [Password Generator](/tools/password-generator/)

> Stay focused while coding → [Pomodoro Timer](/tools/pomodoro-timer/)
