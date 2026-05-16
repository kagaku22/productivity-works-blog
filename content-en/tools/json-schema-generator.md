---
title: "JSON Schema Generator — Free Online Tool"
date: 2025-05-16
description: "Generate JSON Schema from sample JSON data. Auto-detect types, nested objects, and arrays. Edit properties, set required fields, and validate. Draft-07 and 2020-12 support."
categories: ["Free Tools"]
slug: "json-schema-generator"
ShowToc: false
aliases:
  - "/tools/json-schema-generator/"
  - "/tools/json-schema-generator/"
cover:
  image: "/images/covers/json-schema-generator.png"
  alt: "JSON Schema Generator"
---

<div id="jsg-app">

<style>
#jsg-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #1e1e2e;
  color: #cdd6f4;
  border-radius: 12px;
  padding: 20px;
  margin: 0 auto;
  max-width: 1200px;
  box-sizing: border-box;
}

#jsg-app * {
  box-sizing: border-box;
}

/* ── Toolbar ── */
#jsg-app .jsg-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 16px;
}

#jsg-app .jsg-toolbar-group {
  display: flex;
  align-items: center;
  gap: 6px;
  flex-wrap: wrap;
}

#jsg-app .jsg-sep {
  width: 1px;
  height: 26px;
  background: #45475a;
  margin: 0 4px;
}

#jsg-app .jsg-label {
  font-size: 12px;
  color: #a6adc8;
  white-space: nowrap;
}

#jsg-app .jsg-btn {
  padding: 7px 15px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  outline: none;
  white-space: nowrap;
}

#jsg-app .jsg-btn:active { transform: scale(0.97); }
#jsg-app .jsg-btn:hover  { opacity: 0.88; }

#jsg-app .jsg-btn-generate { background: #89b4fa; color: #1e1e2e; }
#jsg-app .jsg-btn-validate { background: #a6e3a1; color: #1e1e2e; }
#jsg-app .jsg-btn-copy     { background: #cba6f7; color: #1e1e2e; }
#jsg-app .jsg-btn-clear    { background: #45475a; color: #cdd6f4; }
#jsg-app .jsg-btn-sample   { background: #313244; color: #89b4fa; border: 1px solid #89b4fa; }

#jsg-app .jsg-select {
  background: #313244;
  color: #cdd6f4;
  border: 1px solid #45475a;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 13px;
  cursor: pointer;
  outline: none;
}
#jsg-app .jsg-select:focus { border-color: #89b4fa; }

#jsg-app .jsg-version-toggle {
  display: flex;
  gap: 0;
  border-radius: 7px;
  overflow: hidden;
  border: 1px solid #45475a;
}

#jsg-app .jsg-version-btn {
  padding: 6px 13px;
  background: #313244;
  color: #a6adc8;
  border: none;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
  outline: none;
}
#jsg-app .jsg-version-btn.active {
  background: #89b4fa;
  color: #1e1e2e;
}

/* ── Main layout ── */
#jsg-app .jsg-main {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

@media (max-width: 750px) {
  #jsg-app .jsg-main { grid-template-columns: 1fr; }
  #jsg-app .jsg-sep  { display: none; }
}

#jsg-app .jsg-pane {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

#jsg-app .jsg-pane-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #a6adc8;
}

#jsg-app .jsg-textarea {
  width: 100%;
  min-height: 320px;
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
#jsg-app .jsg-textarea:focus { border-color: #89b4fa; }
#jsg-app .jsg-textarea.jsg-error  { border-color: #f38ba8; }
#jsg-app .jsg-textarea.jsg-valid  { border-color: #a6e3a1; }

#jsg-app .jsg-output-box {
  width: 100%;
  min-height: 320px;
  background: #11111b;
  border: 2px solid #313244;
  border-radius: 9px;
  padding: 14px;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
  font-size: 13px;
  line-height: 1.65;
  overflow: auto;
  white-space: pre-wrap;
  word-break: break-all;
  transition: border-color 0.2s;
}
#jsg-app .jsg-output-box.jsg-valid { border-color: #a6e3a1; }
#jsg-app .jsg-output-box.jsg-error { border-color: #f38ba8; }

/* ── Status & error ── */
#jsg-app .jsg-status-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  font-size: 12px;
  color: #6c7086;
  margin-top: 2px;
}
#jsg-app .jsg-ok   { color: #a6e3a1; font-weight: 600; }
#jsg-app .jsg-err  { color: #f38ba8; font-weight: 600; }
#jsg-app .jsg-info { color: #89b4fa; }

#jsg-app .jsg-error-box {
  background: #1a0a0a;
  border: 1px solid #f38ba8;
  border-radius: 7px;
  color: #f38ba8;
  font-size: 13px;
  padding: 10px 14px;
  display: none;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
}
#jsg-app .jsg-error-box.visible { display: block; }

/* ── Property editor ── */
#jsg-app .jsg-editor-section {
  margin-top: 18px;
  background: #181825;
  border: 1px solid #313244;
  border-radius: 10px;
  padding: 14px;
}

#jsg-app .jsg-editor-title {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #a6adc8;
  margin-bottom: 12px;
}

#jsg-app .jsg-prop-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}

#jsg-app .jsg-prop-table th {
  text-align: left;
  color: #6c7086;
  font-weight: 600;
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  padding: 4px 8px 8px 8px;
  border-bottom: 1px solid #313244;
}

#jsg-app .jsg-prop-table td {
  padding: 6px 8px;
  vertical-align: middle;
  border-bottom: 1px solid #1e1e2e;
}

#jsg-app .jsg-prop-table tr:last-child td { border-bottom: none; }

#jsg-app .jsg-prop-key {
  color: #89b4fa;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
  white-space: nowrap;
}

#jsg-app .jsg-prop-type {
  color: #fab387;
  font-family: 'Cascadia Code', 'Fira Code', 'Consolas', monospace;
  font-size: 12px;
}

#jsg-app .jsg-prop-desc-input {
  background: #11111b;
  color: #cdd6f4;
  border: 1px solid #313244;
  border-radius: 5px;
  padding: 4px 8px;
  font-size: 12px;
  width: 100%;
  outline: none;
  transition: border-color 0.15s;
}
#jsg-app .jsg-prop-desc-input:focus { border-color: #89b4fa; }

#jsg-app .jsg-prop-req-chk {
  accent-color: #89b4fa;
  width: 16px;
  height: 16px;
  cursor: pointer;
}

#jsg-app .jsg-apply-btn {
  margin-top: 12px;
  padding: 7px 18px;
  background: #89b4fa;
  color: #1e1e2e;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s;
}
#jsg-app .jsg-apply-btn:hover { opacity: 0.85; }

/* ── Syntax highlight ── */
#jsg-app .jst-key    { color: #89b4fa; }
#jsg-app .jst-str    { color: #a6e3a1; }
#jsg-app .jst-num    { color: #fab387; }
#jsg-app .jst-bool   { color: #cba6f7; }
#jsg-app .jst-null   { color: #f38ba8; }
#jsg-app .jst-punc   { color: #6c7086; }

/* ── Toast ── */
#jsg-app .jsg-toast {
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
#jsg-app .jsg-toast.show { opacity: 1; }
</style>

<!-- Toolbar -->
<div class="jsg-toolbar">
  <div class="jsg-toolbar-group">
    <button class="jsg-btn jsg-btn-generate" onclick="jsgGenerate()">Generate Schema</button>
    <button class="jsg-btn jsg-btn-validate" onclick="jsgValidate()">Validate JSON</button>
  </div>
  <div class="jsg-sep"></div>
  <div class="jsg-toolbar-group">
    <span class="jsg-label">Schema Version:</span>
    <div class="jsg-version-toggle">
      <button class="jsg-version-btn active" id="jsg-v07" onclick="jsgSetVersion('draft-07')">Draft-07</button>
      <button class="jsg-version-btn" id="jsg-v20" onclick="jsgSetVersion('2020-12')">2020-12</button>
    </div>
  </div>
  <div class="jsg-sep"></div>
  <div class="jsg-toolbar-group">
    <span class="jsg-label">Sample:</span>
    <select class="jsg-select" id="jsg-sample-select" onchange="jsgLoadSample(this.value)">
      <option value="">— choose preset —</option>
      <option value="user">User Object</option>
      <option value="product">Product Catalog</option>
      <option value="api">API Response</option>
    </select>
  </div>
  <div class="jsg-sep"></div>
  <div class="jsg-toolbar-group">
    <button class="jsg-btn jsg-btn-copy"  onclick="jsgCopy()">Copy Schema</button>
    <button class="jsg-btn jsg-btn-clear" onclick="jsgClear()">Clear</button>
  </div>
</div>

<!-- Main panes -->
<div class="jsg-main">

  <!-- Left: JSON input -->
  <div class="jsg-pane">
    <div class="jsg-pane-label">Input JSON</div>
    <textarea
      id="jsg-input"
      class="jsg-textarea"
      placeholder='Paste sample JSON here…&#10;&#10;{"name": "Alice", "age": 30, "email": "alice@example.com"}'
      oninput="jsgOnInput()"
      spellcheck="false"
    ></textarea>
    <div class="jsg-status-bar">
      <span id="jsg-in-chars">Chars: 0</span>
      <span id="jsg-in-lines">Lines: 1</span>
    </div>
    <div id="jsg-error-box" class="jsg-error-box"></div>
  </div>

  <!-- Right: Schema output -->
  <div class="jsg-pane">
    <div class="jsg-pane-label">Generated JSON Schema</div>
    <div id="jsg-output" class="jsg-output-box"><span style="color:#45475a">// Schema will appear here after clicking Generate Schema</span></div>
    <div class="jsg-status-bar" id="jsg-out-status"></div>
  </div>

</div>

<!-- Property editor (hidden until schema generated) -->
<div class="jsg-editor-section" id="jsg-editor-section" style="display:none;">
  <div class="jsg-editor-title">Edit Schema Properties</div>
  <table class="jsg-prop-table" id="jsg-prop-table">
    <thead>
      <tr>
        <th>Property</th>
        <th>Type</th>
        <th>Description</th>
        <th>Required</th>
      </tr>
    </thead>
    <tbody id="jsg-prop-tbody"></tbody>
  </table>
  <button class="jsg-apply-btn" onclick="jsgApplyEdits()">Apply Edits &amp; Regenerate</button>
</div>

<div class="jsg-toast" id="jsg-toast">Copied to clipboard!</div>

<script>
(function () {
  'use strict';

  /* ────────────────────────────────────────
     State
  ──────────────────────────────────────── */
  var schemaVersion = 'draft-07';
  var lastSchema = null;      // raw schema object
  var lastInput  = null;      // last successfully parsed JSON
  // propMeta[key] = { description, required }  (top-level only)
  var propMeta   = {};

  /* ────────────────────────────────────────
     Utility
  ──────────────────────────────────────── */
  function esc(s) {
    return String(s)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  function syntaxHL(json) {
    return esc(json).replace(
      /("(\\u[a-fA-F0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+\-]?\d+)?|[{}\[\],:])/g,
      function (m) {
        var cls = 'jst-num';
        if (/^"/.test(m))          cls = /:$/.test(m) ? 'jst-key' : 'jst-str';
        else if (/true|false/.test(m)) cls = 'jst-bool';
        else if (/null/.test(m))       cls = 'jst-null';
        else if (/[{}\[\],:]/.test(m)) cls = 'jst-punc';
        return '<span class="' + cls + '">' + m + '</span>';
      }
    );
  }

  function showToast(msg) {
    var t = document.getElementById('jsg-toast');
    t.textContent = msg || 'Copied to clipboard!';
    t.classList.add('show');
    setTimeout(function () { t.classList.remove('show'); }, 1800);
  }

  function setError(msg) {
    var el = document.getElementById('jsg-error-box');
    if (msg) { el.textContent = msg; el.classList.add('visible'); }
    else      { el.textContent = ''; el.classList.remove('visible'); }
  }

  function setInputState(state) {
    var el = document.getElementById('jsg-input');
    el.className = 'jsg-textarea' + (state ? ' jsg-' + state : '');
  }

  function setOutputState(state) {
    var el = document.getElementById('jsg-output');
    el.className = 'jsg-output-box' + (state ? ' jsg-' + state : '');
  }

  function setOutputHTML(html) {
    document.getElementById('jsg-output').innerHTML = html;
  }

  function updateInputStats() {
    var v = document.getElementById('jsg-input').value;
    document.getElementById('jsg-in-chars').textContent = 'Chars: ' + v.length;
    document.getElementById('jsg-in-lines').textContent = 'Lines: ' + (v ? v.split('\n').length : 1);
  }

  function setOutStatus(html) {
    document.getElementById('jsg-out-status').innerHTML = html;
  }

  function parseInput() {
    var raw = document.getElementById('jsg-input').value.trim();
    if (!raw) return null;
    try {
      return { ok: true, value: JSON.parse(raw) };
    } catch (e) {
      var msg = e.message || String(e);
      var pm = msg.match(/position (\d+)/i);
      var line = null;
      if (pm) {
        var pos = parseInt(pm[1], 10);
        line = raw.slice(0, pos).split('\n').length;
      }
      return { ok: false, error: msg, line: line };
    }
  }

  /* ────────────────────────────────────────
     Format detection helpers
  ──────────────────────────────────────── */
  var RE_DATETIME = /^\d{4}-\d{2}-\d{2}(T\d{2}:\d{2}:\d{2}(\.\d+)?(Z|[+-]\d{2}:\d{2})?)?$/;
  var RE_EMAIL    = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  var RE_URI      = /^https?:\/\/.+/;
  var RE_UUID     = /^[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}$/i;

  function detectStringFormat(val) {
    if (RE_DATETIME.test(val)) return 'date-time';
    if (RE_EMAIL.test(val))    return 'email';
    if (RE_URI.test(val))      return 'uri';
    if (RE_UUID.test(val))     return 'uuid';
    return null;
  }

  function isInteger(n) {
    return Number.isFinite(n) && Math.floor(n) === n;
  }

  /* ────────────────────────────────────────
     Schema generation — recursive
  ──────────────────────────────────────── */
  function inferSchema(val, key) {
    if (val === null) return { type: 'null' };

    if (typeof val === 'boolean') return { type: 'boolean' };

    if (typeof val === 'number') {
      return { type: isInteger(val) ? 'integer' : 'number' };
    }

    if (typeof val === 'string') {
      var fmt = detectStringFormat(val);
      var s = { type: 'string' };
      if (fmt) s.format = fmt;
      return s;
    }

    if (Array.isArray(val)) {
      var schema = { type: 'array' };
      if (val.length > 0) {
        // Infer items from first element (heuristic)
        schema.items = inferSchema(val[0], null);
      }
      return schema;
    }

    if (typeof val === 'object') {
      var props = {};
      var reqArr = [];
      var keys = Object.keys(val);
      for (var i = 0; i < keys.length; i++) {
        var k = keys[i];
        props[k] = inferSchema(val[k], k);
        reqArr.push(k);
      }
      var objSchema = {
        type: 'object',
        properties: props,
        required: reqArr
      };
      return objSchema;
    }

    return {};
  }

  function buildRootSchema(parsed) {
    var $schema = schemaVersion === '2020-12'
      ? 'https://json-schema.org/draft/2020-12/schema'
      : 'http://json-schema.org/draft-07/schema#';

    var inner = inferSchema(parsed, null);

    var root = Object.assign({ $schema: $schema }, inner);

    // Apply propMeta to top-level properties
    if (root.properties) {
      var reqSet = {};
      var keys = Object.keys(root.properties);
      var newReq = [];
      for (var i = 0; i < keys.length; i++) {
        var k = keys[i];
        var meta = propMeta[k] || {};
        if (meta.description) root.properties[k].description = meta.description;
        if (meta.required !== false) newReq.push(k); // default required
      }
      // override required from propMeta
      var hasMeta = Object.keys(propMeta).length > 0;
      if (hasMeta) {
        newReq = [];
        for (var j = 0; j < keys.length; j++) {
          var kk = keys[j];
          var m = propMeta[kk];
          if (!m || m.required !== false) newReq.push(kk);
        }
        root.required = newReq;
      }
    }

    return root;
  }

  /* ────────────────────────────────────────
     Render property editor
  ──────────────────────────────────────── */
  function renderEditor(schema) {
    var section = document.getElementById('jsg-editor-section');
    var tbody   = document.getElementById('jsg-prop-tbody');

    if (!schema || schema.type !== 'object' || !schema.properties) {
      section.style.display = 'none';
      return;
    }

    var keys = Object.keys(schema.properties);
    var reqSet = {};
    if (schema.required) {
      for (var i = 0; i < schema.required.length; i++) reqSet[schema.required[i]] = true;
    }

    tbody.innerHTML = '';
    for (var j = 0; j < keys.length; j++) {
      var k = keys[j];
      var prop = schema.properties[k];
      var meta = propMeta[k] || {};
      var typeStr = prop.type || '?';
      if (prop.format) typeStr += ' (' + prop.format + ')';
      var isReq = propMeta[k] ? propMeta[k].required !== false : (reqSet[k] || false);
      var descVal = meta.description || prop.description || '';

      var tr = document.createElement('tr');
      tr.innerHTML =
        '<td class="jsg-prop-key">' + esc(k) + '</td>' +
        '<td class="jsg-prop-type">' + esc(typeStr) + '</td>' +
        '<td><input class="jsg-prop-desc-input" type="text" data-key="' + esc(k) + '" placeholder="Add description…" value="' + esc(descVal) + '"></td>' +
        '<td style="text-align:center;"><input class="jsg-prop-req-chk" type="checkbox" data-key="' + esc(k) + '"' + (isReq ? ' checked' : '') + '></td>';
      tbody.appendChild(tr);
    }
    section.style.display = 'block';
  }

  /* ────────────────────────────────────────
     Public actions
  ──────────────────────────────────────── */
  window.jsgOnInput = function () {
    updateInputStats();
    setInputState('');
    setError('');
  };

  window.jsgSetVersion = function (v) {
    schemaVersion = v;
    document.getElementById('jsg-v07').classList.toggle('active', v === 'draft-07');
    document.getElementById('jsg-v20').classList.toggle('active', v === '2020-12');
    // Regenerate if we already have a schema
    if (lastInput !== null) jsgGenerate();
  };

  window.jsgGenerate = function () {
    var r = parseInput();
    if (!r) {
      setOutputHTML('<span style="color:#45475a">// Paste JSON on the left and click Generate Schema</span>');
      setOutputState('');
      setOutStatus('');
      document.getElementById('jsg-editor-section').style.display = 'none';
      return;
    }
    if (!r.ok) {
      setInputState('error');
      setError('Parse error' + (r.line ? ' at line ' + r.line : '') + ': ' + r.error);
      setOutputState('error');
      setOutputHTML('<span style="color:#45475a">// Fix JSON errors first</span>');
      setOutStatus('<span class="jsg-err">Invalid JSON — cannot generate schema</span>');
      document.getElementById('jsg-editor-section').style.display = 'none';
      return;
    }

    setInputState('valid');
    setError('');
    lastInput = r.value;
    // Reset propMeta on fresh generate
    propMeta = {};

    lastSchema = buildRootSchema(lastInput);
    var pretty = JSON.stringify(lastSchema, null, 2);
    setOutputHTML(syntaxHL(pretty));
    setOutputState('valid');

    var propCount = lastSchema.properties ? Object.keys(lastSchema.properties).length : 0;
    setOutStatus(
      '<span class="jsg-ok">Schema generated</span>' +
      '<span class="jsg-info">' + schemaVersion + '</span>' +
      '<span>Properties: ' + propCount + '</span>' +
      '<span>Chars: ' + pretty.length + '</span>'
    );

    renderEditor(lastSchema);
  };

  window.jsgApplyEdits = function () {
    if (!lastInput) return;

    // Collect edits from table
    var descInputs = document.querySelectorAll('#jsg-prop-tbody .jsg-prop-desc-input');
    var reqChecks  = document.querySelectorAll('#jsg-prop-tbody .jsg-prop-req-chk');

    propMeta = {};
    for (var i = 0; i < descInputs.length; i++) {
      var k = descInputs[i].getAttribute('data-key');
      propMeta[k] = propMeta[k] || {};
      propMeta[k].description = descInputs[i].value.trim();
    }
    for (var j = 0; j < reqChecks.length; j++) {
      var kk = reqChecks[j].getAttribute('data-key');
      propMeta[kk] = propMeta[kk] || {};
      propMeta[kk].required = reqChecks[j].checked;
    }

    lastSchema = buildRootSchema(lastInput);
    var pretty = JSON.stringify(lastSchema, null, 2);
    setOutputHTML(syntaxHL(pretty));
    setOutputState('valid');

    var propCount = lastSchema.properties ? Object.keys(lastSchema.properties).length : 0;
    setOutStatus(
      '<span class="jsg-ok">Schema updated</span>' +
      '<span class="jsg-info">' + schemaVersion + '</span>' +
      '<span>Properties: ' + propCount + '</span>' +
      '<span>Chars: ' + pretty.length + '</span>'
    );
    showToast('Schema updated!');
  };

  window.jsgValidate = function () {
    var r = parseInput();
    if (!r) {
      setError('Enter JSON to validate.');
      return;
    }
    if (!r.ok) {
      setInputState('error');
      setError('Parse error' + (r.line ? ' at line ' + r.line : '') + ': ' + r.error);
      setOutputState('error');
      setOutputHTML('<span class="jsg-err" style="font-size:15px;font-weight:700;">Invalid JSON</span>');
      setOutStatus('<span class="jsg-err">JSON is not well-formed</span>');
      return;
    }

    if (!lastSchema) {
      setInputState('valid');
      setError('');
      setOutputHTML('<span class="jsg-ok" style="font-size:14px;font-weight:700;">Valid JSON</span>\n\n<span style="color:#6c7086">// Generate a schema first to validate against it.</span>');
      setOutputState('valid');
      setOutStatus('<span class="jsg-ok">JSON is well-formed</span>');
      return;
    }

    // Validate parsed value against lastSchema (structural, type-based)
    var errs = validateAgainstSchema(r.value, lastSchema, '$');
    if (errs.length === 0) {
      setInputState('valid');
      setError('');
      setOutputHTML('<span class="jsg-ok" style="font-size:15px;font-weight:700;">Validation Passed</span>\n\n<span style="color:#6c7086">// JSON is valid against the generated schema.</span>');
      setOutputState('valid');
      setOutStatus('<span class="jsg-ok">Passed all schema checks</span>');
    } else {
      setInputState('error');
      setError('');
      var errLines = errs.map(function (e) { return '  ' + e; }).join('\n');
      setOutputHTML('<span class="jsg-err" style="font-size:15px;font-weight:700;">Validation Failed</span>\n\n<span style="color:#f38ba8">' + esc(errLines) + '</span>');
      setOutputState('error');
      setOutStatus('<span class="jsg-err">' + errs.length + ' validation error' + (errs.length > 1 ? 's' : '') + '</span>');
    }
  };

  /* ────────────────────────────────────────
     Structural validator
  ──────────────────────────────────────── */
  function validateAgainstSchema(val, schema, path) {
    var errors = [];
    if (!schema) return errors;

    // type check
    if (schema.type) {
      var types = Array.isArray(schema.type) ? schema.type : [schema.type];
      var actualType = getType(val);
      var matched = false;
      for (var i = 0; i < types.length; i++) {
        if (types[i] === actualType) { matched = true; break; }
        // integer is a subtype of number
        if (types[i] === 'integer' && actualType === 'number' && isInteger(val)) { matched = true; break; }
      }
      if (!matched) {
        errors.push(path + ': expected ' + types.join('|') + ', got ' + actualType);
      }
    }

    // required
    if (schema.required && typeof val === 'object' && val !== null && !Array.isArray(val)) {
      for (var r = 0; r < schema.required.length; r++) {
        if (!Object.prototype.hasOwnProperty.call(val, schema.required[r])) {
          errors.push(path + ': missing required property "' + schema.required[r] + '"');
        }
      }
    }

    // properties
    if (schema.properties && typeof val === 'object' && val !== null && !Array.isArray(val)) {
      var pkeys = Object.keys(schema.properties);
      for (var p = 0; p < pkeys.length; p++) {
        var pk = pkeys[p];
        if (Object.prototype.hasOwnProperty.call(val, pk)) {
          var subErrs = validateAgainstSchema(val[pk], schema.properties[pk], path + '.' + pk);
          errors = errors.concat(subErrs);
        }
      }
    }

    // items
    if (schema.items && Array.isArray(val)) {
      for (var ai = 0; ai < val.length; ai++) {
        var aErrs = validateAgainstSchema(val[ai], schema.items, path + '[' + ai + ']');
        errors = errors.concat(aErrs);
      }
    }

    return errors;
  }

  function getType(val) {
    if (val === null)          return 'null';
    if (typeof val === 'boolean') return 'boolean';
    if (typeof val === 'number')  return 'number';
    if (typeof val === 'string')  return 'string';
    if (Array.isArray(val))       return 'array';
    if (typeof val === 'object')  return 'object';
    return 'unknown';
  }

  /* ────────────────────────────────────────
     Copy
  ──────────────────────────────────────── */
  window.jsgCopy = function () {
    var el = document.getElementById('jsg-output');
    var text = el.innerText || el.textContent;
    if (!text || text.trim().startsWith('//')) return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function () { showToast('Copied to clipboard!'); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.cssText = 'position:fixed;opacity:0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showToast('Copied to clipboard!');
    }
  };

  /* ────────────────────────────────────────
     Clear
  ──────────────────────────────────────── */
  window.jsgClear = function () {
    document.getElementById('jsg-input').value = '';
    setInputState('');
    setError('');
    updateInputStats();
    setOutputHTML('<span style="color:#45475a">// Schema will appear here after clicking Generate Schema</span>');
    setOutputState('');
    setOutStatus('');
    lastSchema = null;
    lastInput  = null;
    propMeta   = {};
    document.getElementById('jsg-editor-section').style.display = 'none';
    document.getElementById('jsg-sample-select').value = '';
  };

  /* ────────────────────────────────────────
     Sample presets
  ──────────────────────────────────────── */
  var SAMPLES = {
    user: {
      "id": "a3f8c2d1-4b7e-4f9a-8c1d-2e3f4a5b6c7d",
      "username": "alice_wonder",
      "email": "alice@example.com",
      "age": 30,
      "isPremium": true,
      "score": 98.5,
      "registeredAt": "2024-01-15T08:30:00Z",
      "address": {
        "street": "123 Main St",
        "city": "Springfield",
        "country": "US",
        "postalCode": "62701"
      },
      "tags": ["admin", "verified"],
      "preferences": null
    },
    product: {
      "sku": "PROD-00421",
      "name": "Ergonomic Keyboard Pro",
      "description": "Full-size mechanical keyboard with RGB backlight",
      "price": 129.99,
      "currency": "USD",
      "inStock": true,
      "quantity": 42,
      "rating": 4.7,
      "categories": ["electronics", "peripherals", "keyboards"],
      "images": [
        {
          "url": "https://example.com/images/kbd-front.jpg",
          "alt": "Front view",
          "isPrimary": true
        }
      ],
      "createdAt": "2023-11-01T00:00:00Z",
      "updatedAt": "2024-06-15T12:45:00Z"
    },
    api: {
      "status": "success",
      "code": 200,
      "message": "Request completed successfully",
      "data": {
        "totalCount": 1250,
        "page": 1,
        "pageSize": 25,
        "hasNextPage": true,
        "items": [
          {
            "id": 1,
            "title": "Sample Item",
            "active": true,
            "score": 0.92
          }
        ]
      },
      "meta": {
        "requestId": "req_9f3a2c1d",
        "timestamp": "2025-05-16T10:00:00Z",
        "version": "v2"
      },
      "errors": null
    }
  };

  window.jsgLoadSample = function (key) {
    if (!key || !SAMPLES[key]) return;
    document.getElementById('jsg-input').value = JSON.stringify(SAMPLES[key], null, 2);
    updateInputStats();
    setInputState('');
    setError('');
    propMeta = {};
    jsgGenerate();
  };

  // Init stats
  updateInputStats();

})();
</script>

</div>

---

## What is JSON Schema?

JSON Schema is a vocabulary that allows you to annotate and validate JSON documents. It describes the structure of JSON data — what properties an object should have, what types those properties must be, which fields are required, and what formats or constraints apply. A schema acts as a contract between producers and consumers of JSON data, making APIs more predictable and enabling automated validation, documentation generation, and code generation.

Two widely used drafts are **Draft-07**, which is supported by virtually every validation library across all languages, and **Draft 2020-12**, the current stable specification that introduces features like `$dynamicRef` and improved `unevaluatedProperties` handling. This tool lets you switch between both with a single click.

---

## How to Use This JSON Schema Generator

**Generate Schema** — Paste any valid JSON object into the left pane and click "Generate Schema." The tool inspects every value recursively: it maps `true`/`false` to `boolean`, whole numbers to `integer`, decimals to `number`, `null` to `null`, and arrays and objects to their respective schema types. String values are scanned for common patterns — if a value looks like a date-time, email, URI, or UUID, the corresponding `format` keyword is added automatically.

**Schema Version Toggle** — Click "Draft-07" or "2020-12" to switch the `$schema` URI in the output. The toggle regenerates the schema immediately if input is already present.

**Edit Properties** — After generating, the "Edit Schema Properties" table appears below the output. Add a human-readable `description` to any property, and toggle the "Required" checkbox to control which fields appear in the `required` array. Click "Apply Edits & Regenerate" to update the schema.

**Validate JSON** — Click "Validate JSON" to check your input against the generated schema. The validator checks types, required fields, and nested structures, reporting each error with its JSON path.

**Sample Presets** — Use the "Sample" dropdown to load one of three built-in examples: a **User Object** (with UUID, email, date-time, nested address, and array of tags), a **Product Catalog** entry (with price, rating, image array), or a full **API Response** envelope (with pagination, nested data, and metadata).

**Copy Schema** — Click "Copy Schema" to copy the generated schema to your clipboard for use in your codebase, API docs, or configuration.

---

### Related Tools

> Format JSON → [JSON Formatter](/tools/json-formatter/)

> Convert JSON to CSV → [JSON to CSV](/tools/json-to-csv/)

> Convert YAML ↔ JSON → [YAML↔JSON Converter](/tools/yaml-json-converter/)
