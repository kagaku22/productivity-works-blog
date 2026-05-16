---
title: "TOML/INI ↔ JSON Converter"
date: 2025-05-16
description: "Convert between TOML, INI, and JSON formats. Bidirectional conversion with syntax validation. Presets for Cargo.toml, pyproject.toml, and config files."
categories: ["Free Tools"]
slug: "toml-json-converter"
ShowToc: false
cover:
  image: "/images/covers/toml-json-converter.png"
  alt: "TOML/INI JSON Converter"
---

Convert TOML and INI configuration files to JSON — or convert JSON back to TOML. Paste your config, click Convert, and get clean output instantly. No installation, no server upload, everything runs in your browser.

<div id="toml-app">
<style>
  #toml-app *,
  #toml-app *::before,
  #toml-app *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #toml-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    font-size: 14px;
    color: #1a1a2e;
    line-height: 1.5;
  }
  #toml-app .ta-toolbar {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 14px;
    align-items: center;
  }
  #toml-app .ta-btn {
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
  }
  #toml-app .ta-btn:active { transform: scale(0.97); }
  #toml-app .ta-btn-primary {
    background: #4f46e5;
    color: #fff;
  }
  #toml-app .ta-btn-primary:hover { background: #4338ca; }
  #toml-app .ta-btn-secondary {
    background: #e0e7ff;
    color: #3730a3;
  }
  #toml-app .ta-btn-secondary:hover { background: #c7d2fe; }
  #toml-app .ta-btn-ghost {
    background: #f3f4f6;
    color: #374151;
    border: 1px solid #d1d5db;
  }
  #toml-app .ta-btn-ghost:hover { background: #e5e7eb; }
  #toml-app .ta-btn-success {
    background: #059669;
    color: #fff;
  }
  #toml-app .ta-btn-success:hover { background: #047857; }
  #toml-app .ta-panels {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  @media (max-width: 700px) {
    #toml-app .ta-panels {
      grid-template-columns: 1fr;
    }
  }
  #toml-app .ta-panel {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  #toml-app .ta-panel-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 6px;
  }
  #toml-app .ta-panel-label {
    font-size: 13px;
    font-weight: 700;
    color: #374151;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  #toml-app .ta-panel-actions {
    display: flex;
    gap: 5px;
    flex-wrap: wrap;
  }
  #toml-app textarea {
    width: 100%;
    min-height: 340px;
    padding: 12px;
    font-family: "SF Mono", "Fira Code", "Consolas", monospace;
    font-size: 12.5px;
    line-height: 1.6;
    border: 2px solid #d1d5db;
    border-radius: 8px;
    resize: vertical;
    background: #f9fafb;
    color: #111827;
    transition: border-color 0.15s;
    outline: none;
  }
  #toml-app textarea:focus { border-color: #4f46e5; background: #fff; }
  #toml-app textarea.ta-error { border-color: #ef4444; background: #fff5f5; }
  #toml-app .ta-status {
    min-height: 22px;
    font-size: 12px;
    padding: 3px 6px;
    border-radius: 4px;
  }
  #toml-app .ta-status.ok { color: #065f46; background: #d1fae5; }
  #toml-app .ta-status.err { color: #991b1b; background: #fee2e2; }
  #toml-app .ta-center-col {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 0 4px;
  }
  #toml-app .ta-convert-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin: 12px 0;
    flex-wrap: wrap;
  }
  #toml-app .ta-arrow {
    font-size: 20px;
    color: #6b7280;
    line-height: 1;
  }
  #toml-app .ta-options-row {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    margin-bottom: 14px;
    align-items: center;
  }
  #toml-app .ta-check-label {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 13px;
    color: #374151;
    cursor: pointer;
    user-select: none;
  }
  #toml-app .ta-check-label input[type="checkbox"] {
    width: 15px;
    height: 15px;
    accent-color: #4f46e5;
    cursor: pointer;
  }
  #toml-app .ta-presets-row {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
    margin-bottom: 14px;
    align-items: center;
  }
  #toml-app .ta-presets-label {
    font-size: 12px;
    font-weight: 600;
    color: #6b7280;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  #toml-app .ta-preset-btn {
    padding: 4px 10px;
    border: 1px solid #c7d2fe;
    border-radius: 5px;
    background: #eef2ff;
    color: #3730a3;
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    transition: background 0.12s;
  }
  #toml-app .ta-preset-btn:hover { background: #c7d2fe; }
  #toml-app .ta-divider {
    height: 1px;
    background: #e5e7eb;
    margin: 16px 0;
  }
  #toml-app .ta-copy-flash {
    animation: taCopyFlash 0.6s ease;
  }
  @keyframes taCopyFlash {
    0% { background: #a7f3d0; }
    100% { background: #f9fafb; }
  }
</style>

<div class="ta-presets-row">
  <span class="ta-presets-label">Presets:</span>
  <button class="ta-preset-btn" onclick="taLoadPreset('cargo')">Cargo.toml</button>
  <button class="ta-preset-btn" onclick="taLoadPreset('pyproject')">pyproject.toml</button>
  <button class="ta-preset-btn" onclick="taLoadPreset('ini')">config.ini</button>
  <button class="ta-preset-btn" onclick="taLoadPreset('json')">JSON Sample</button>
</div>

<div class="ta-options-row">
  <label class="ta-check-label">
    <input type="checkbox" id="ta-pretty" checked>
    Pretty-print JSON
  </label>
  <label class="ta-check-label">
    <input type="checkbox" id="ta-minify">
    Minify JSON output
  </label>
</div>

<div class="ta-panels">
  <div class="ta-panel">
    <div class="ta-panel-header">
      <span class="ta-panel-label">TOML / INI Input</span>
      <div class="ta-panel-actions">
        <button class="ta-btn ta-btn-ghost" onclick="taClear('ta-input')" style="font-size:12px;padding:4px 9px;">Clear</button>
        <button class="ta-btn ta-btn-ghost" onclick="taCopyText('ta-input')" style="font-size:12px;padding:4px 9px;">Copy</button>
      </div>
    </div>
    <textarea id="ta-input" placeholder="Paste TOML or INI here..." spellcheck="false"></textarea>
    <div id="ta-input-status" class="ta-status"></div>
  </div>

  <div class="ta-panel">
    <div class="ta-panel-header">
      <span class="ta-panel-label">JSON Output</span>
      <div class="ta-panel-actions">
        <button class="ta-btn ta-btn-ghost" onclick="taClear('ta-output')" style="font-size:12px;padding:4px 9px;">Clear</button>
        <button class="ta-btn ta-btn-ghost" onclick="taCopyText('ta-output')" style="font-size:12px;padding:4px 9px;">Copy</button>
      </div>
    </div>
    <textarea id="ta-output" placeholder="JSON output appears here..." spellcheck="false"></textarea>
    <div id="ta-output-status" class="ta-status"></div>
  </div>
</div>

<div class="ta-convert-row">
  <button class="ta-btn ta-btn-primary" onclick="taConvertToJson()">TOML/INI &rarr; JSON</button>
  <span class="ta-arrow">&#8644;</span>
  <button class="ta-btn ta-btn-success" onclick="taConvertToToml()">JSON &rarr; TOML</button>
</div>

<div class="ta-divider"></div>
</div>

<script>
(function () {
  // ─── Presets ─────────────────────────────────────────────────────────────
  const PRESETS = {
    cargo: `[package]
name = "my-app"
version = "0.1.0"
edition = "2021"
authors = ["Alice <alice@example.com>"]
description = "A sample Rust project"
license = "MIT"

[dependencies]
serde = { version = "1.0", features = ["derive"] }
tokio = { version = "1", features = ["full"] }
reqwest = "0.11"

[dev-dependencies]
tokio-test = "0.4"

[profile.release]
opt-level = 3
lto = true
`,
    pyproject: `[build-system]
requires = ["setuptools>=61.0", "wheel"]
build-backend = "setuptools.backends.legacy:build"

[project]
name = "my-package"
version = "1.2.3"
description = "An example Python package"
license = { text = "MIT" }
requires-python = ">=3.9"
dependencies = [
  "requests>=2.28",
  "pydantic>=2.0",
  "click>=8.0"
]

[project.optional-dependencies]
dev = ["pytest", "black", "mypy"]

[tool.black]
line-length = 88
target-version = ["py39", "py310", "py311"]
`,
    ini: `[general]
app_name = MyApplication
version = 3.2.1
debug = false
max_retries = 5

[database]
host = localhost
port = 5432
name = production_db
user = admin
pool_size = 10

[logging]
level = INFO
file = /var/log/myapp.log
rotate = true
max_size_mb = 100

[cache]
backend = redis
host = 127.0.0.1
port = 6379
ttl = 3600
`,
    json: `{
  "server": {
    "host": "0.0.0.0",
    "port": 8080,
    "debug": false
  },
  "database": {
    "url": "postgres://localhost/mydb",
    "pool_size": 10,
    "timeout": 30
  },
  "features": ["auth", "api", "websocket"],
  "limits": {
    "max_upload_mb": 50,
    "rate_limit_rps": 100
  }
}`
  };

  window.taLoadPreset = function (name) {
    if (name === 'json') {
      document.getElementById('ta-output').value = PRESETS.json;
      setStatus('ta-output-status', '', '');
    } else {
      document.getElementById('ta-input').value = PRESETS[name] || '';
      setStatus('ta-input-status', '', '');
    }
    clearStatus('ta-input-status');
    clearStatus('ta-output-status');
    document.getElementById('ta-input').classList.remove('ta-error');
    document.getElementById('ta-output').classList.remove('ta-error');
  };

  window.taClear = function (id) {
    document.getElementById(id).value = '';
    document.getElementById(id).classList.remove('ta-error');
    const statusId = id === 'ta-input' ? 'ta-input-status' : 'ta-output-status';
    clearStatus(statusId);
  };

  window.taCopyText = function (id) {
    const el = document.getElementById(id);
    const val = el.value;
    if (!val) return;
    navigator.clipboard.writeText(val).then(() => {
      el.classList.add('ta-copy-flash');
      setTimeout(() => el.classList.remove('ta-copy-flash'), 700);
    }).catch(() => {
      el.select();
      document.execCommand('copy');
    });
  };

  function setStatus(id, type, msg) {
    const el = document.getElementById(id);
    el.className = 'ta-status' + (type ? ' ' + type : '');
    el.textContent = msg;
  }
  function clearStatus(id) { setStatus(id, '', ''); }

  // ─── TOML Parser ─────────────────────────────────────────────────────────
  function parseTOML(src) {
    const lines = src.split('\n');
    const root = {};
    let current = root;
    let currentPath = [];
    let i = 0;

    function getOrCreate(obj, keys) {
      let ref = obj;
      for (const k of keys) {
        if (!(k in ref)) ref[k] = {};
        else if (Array.isArray(ref[k])) ref = ref[k][ref[k].length - 1];
        else if (typeof ref[k] !== 'object') throw new Error('Key conflict: ' + k);
        if (!Array.isArray(ref[k])) ref = ref[k];
      }
      return ref;
    }

    function deepGet(obj, keys) {
      let ref = obj;
      for (let ki = 0; ki < keys.length; ki++) {
        const k = keys[ki];
        if (!(k in ref)) return undefined;
        if (Array.isArray(ref[k]) && ki < keys.length - 1) ref = ref[k][ref[k].length - 1];
        else ref = ref[k];
      }
      return ref;
    }

    function parseValue(s) {
      s = s.trim();
      // Multi-line strings not fully supported — basic only
      if (s.startsWith('"""') || s.startsWith("'''")) {
        const delim = s.slice(0, 3);
        const end = s.indexOf(delim, 3);
        if (end === -1) throw new Error('Unterminated multi-line string');
        return s.slice(3, end);
      }
      if (s.startsWith('"')) {
        const m = s.match(/^"((?:[^"\\]|\\.)*)"$/);
        if (!m) throw new Error('Invalid string: ' + s);
        return m[1].replace(/\\n/g, '\n').replace(/\\t/g, '\t').replace(/\\r/g, '\r').replace(/\\"/g, '"').replace(/\\\\/g, '\\');
      }
      if (s.startsWith("'")) {
        const m = s.match(/^'([^']*)'$/);
        if (!m) throw new Error('Invalid literal string: ' + s);
        return m[1];
      }
      if (s.startsWith('[')) return parseArray(s);
      if (s.startsWith('{')) return parseInlineTable(s);
      if (s === 'true') return true;
      if (s === 'false') return false;
      if (/^-?\d{4}-\d{2}-\d{2}(T[\d:+Z.-]+)?$/.test(s)) return s; // datetime as string
      if (/^[+-]?(?:0x[0-9a-fA-F_]+|0o[0-7_]+|0b[01_]+)$/.test(s)) {
        const clean = s.replace(/_/g, '');
        return parseInt(clean, clean.startsWith('0x') ? 16 : clean.startsWith('0o') ? 8 : 2);
      }
      if (/^[+-]?(inf|nan)$/.test(s)) return s === 'inf' || s === '+inf' ? Infinity : s === '-inf' ? -Infinity : NaN;
      if (/^[+-]?\d[\d_]*$/.test(s)) return parseInt(s.replace(/_/g, ''), 10);
      if (/^[+-]?\d[\d_]*\.[\d_]*(e[+-]?\d+)?$/i.test(s)) return parseFloat(s.replace(/_/g, ''));
      if (/^[+-]?\d[\d_]*e[+-]?\d+$/i.test(s)) return parseFloat(s.replace(/_/g, ''));
      throw new Error('Cannot parse value: ' + s);
    }

    function parseArray(s) {
      s = s.trim();
      if (!s.startsWith('[')) throw new Error('Expected [');
      let depth = 0, inStr = false, strChar = '', result = [], buf = '';
      for (let ci = 0; ci < s.length; ci++) {
        const ch = s[ci];
        if (inStr) {
          if (ch === strChar && s[ci-1] !== '\\') inStr = false;
          buf += ch;
        } else if (ch === '"' || ch === "'") {
          inStr = true; strChar = ch; buf += ch;
        } else if (ch === '[' || ch === '{') {
          depth++; buf += ch;
        } else if (ch === ']' || ch === '}') {
          depth--;
          if (depth === 0) {
            const trimmed = buf.trim();
            if (trimmed) result.push(parseValue(trimmed));
            break;
          }
          buf += ch;
        } else if (ch === ',' && depth === 1) {
          const trimmed = buf.trim();
          if (trimmed) result.push(parseValue(trimmed));
          buf = '';
        } else if (ch === '#' && depth === 1) {
          break;
        } else {
          if (depth >= 1) buf += ch;
        }
      }
      return result;
    }

    function parseInlineTable(s) {
      s = s.trim();
      if (!s.startsWith('{')) throw new Error('Expected {');
      const inner = s.slice(1, s.lastIndexOf('}'));
      const obj = {};
      let depth = 0, inStr = false, strChar = '', buf = '', parts = [];
      for (let ci = 0; ci < inner.length; ci++) {
        const ch = inner[ci];
        if (inStr) {
          if (ch === strChar && inner[ci-1] !== '\\') inStr = false;
          buf += ch;
        } else if (ch === '"' || ch === "'") {
          inStr = true; strChar = ch; buf += ch;
        } else if (ch === '{' || ch === '[') { depth++; buf += ch; }
        else if (ch === '}' || ch === ']') { depth--; buf += ch; }
        else if (ch === ',' && depth === 0) { parts.push(buf.trim()); buf = ''; }
        else buf += ch;
      }
      if (buf.trim()) parts.push(buf.trim());
      for (const part of parts) {
        const eq = part.indexOf('=');
        if (eq === -1) throw new Error('Invalid inline table entry: ' + part);
        const k = part.slice(0, eq).trim();
        const v = part.slice(eq + 1).trim();
        obj[unquoteKey(k)] = parseValue(v);
      }
      return obj;
    }

    function unquoteKey(k) {
      if ((k.startsWith('"') && k.endsWith('"')) || (k.startsWith("'") && k.endsWith("'")))
        return k.slice(1, -1);
      return k;
    }

    function parseKey(raw) {
      const parts = [];
      let buf = '', inStr = false, strChar = '';
      for (let ci = 0; ci < raw.length; ci++) {
        const ch = raw[ci];
        if (inStr) {
          if (ch === strChar) { inStr = false; parts.push(buf); buf = ''; }
          else buf += ch;
        } else if (ch === '"' || ch === "'") {
          inStr = true; strChar = ch;
        } else if (ch === '.') {
          if (buf.trim()) parts.push(buf.trim());
          buf = '';
        } else buf += ch;
      }
      if (buf.trim()) parts.push(buf.trim());
      return parts.map(unquoteKey);
    }

    while (i < lines.length) {
      let line = lines[i].replace(/\s*#[^"']*$/, '').trim();
      i++;
      if (!line) continue;

      // Array of tables [[key]]
      if (line.startsWith('[[')) {
        const key = line.slice(2, line.indexOf(']]')).trim();
        const keyParts = parseKey(key);
        let ref = root;
        for (let ki = 0; ki < keyParts.length - 1; ki++) {
          const k = keyParts[ki];
          if (!(k in ref)) ref[k] = {};
          if (Array.isArray(ref[k])) ref = ref[k][ref[k].length - 1];
          else ref = ref[k];
        }
        const last = keyParts[keyParts.length - 1];
        if (!Array.isArray(ref[last])) ref[last] = [];
        const newTable = {};
        ref[last].push(newTable);
        current = newTable;
        currentPath = keyParts;
        continue;
      }

      // Standard table [key]
      if (line.startsWith('[')) {
        const key = line.slice(1, line.indexOf(']')).trim();
        currentPath = parseKey(key);
        current = root;
        for (let ki = 0; ki < currentPath.length; ki++) {
          const k = currentPath[ki];
          if (!(k in current)) current[k] = {};
          if (Array.isArray(current[k])) current = current[k][current[k].length - 1];
          else current = current[k];
        }
        continue;
      }

      // Key-value
      const eqIdx = line.indexOf('=');
      if (eqIdx === -1) throw new Error('Expected = in line: ' + line);
      const rawKey = line.slice(0, eqIdx).trim();
      let rawVal = line.slice(eqIdx + 1).trim();

      // Handle multi-line arrays that continue on next lines
      if (rawVal.startsWith('[') && !rawVal.includes(']')) {
        while (i < lines.length && !rawVal.includes(']')) {
          rawVal += ' ' + lines[i].replace(/\s*#.*$/, '').trim();
          i++;
        }
      }

      const keyParts = parseKey(rawKey);
      let ref = current;
      for (let ki = 0; ki < keyParts.length - 1; ki++) {
        const k = keyParts[ki];
        if (!(k in ref)) ref[k] = {};
        ref = ref[k];
      }
      ref[keyParts[keyParts.length - 1]] = parseValue(rawVal);
    }
    return root;
  }

  // ─── INI Parser ──────────────────────────────────────────────────────────
  function isINI(src) {
    const lines = src.trim().split('\n');
    for (const l of lines) {
      const t = l.trim();
      if (!t || t.startsWith(';') || t.startsWith('#') || t.startsWith('[') || t.includes('=')) continue;
      return false;
    }
    // Has at least one [section] or key=value at root
    return true;
  }

  function parseINI(src) {
    const lines = src.split('\n');
    const result = {};
    let section = null;
    for (const raw of lines) {
      const line = raw.trim();
      if (!line || line.startsWith(';') || line.startsWith('#')) continue;
      if (line.startsWith('[') && line.endsWith(']')) {
        section = line.slice(1, -1).trim();
        if (!(section in result)) result[section] = {};
        continue;
      }
      const eq = line.indexOf('=');
      if (eq === -1) continue;
      const key = line.slice(0, eq).trim();
      const val = line.slice(eq + 1).trim();
      const target = section ? result[section] : result;
      target[key] = coerceINI(val);
    }
    return result;
  }

  function coerceINI(v) {
    if (v === 'true' || v === 'yes' || v === 'on') return true;
    if (v === 'false' || v === 'no' || v === 'off') return false;
    if (/^-?\d+$/.test(v)) return parseInt(v, 10);
    if (/^-?\d+\.\d+$/.test(v)) return parseFloat(v);
    // Strip surrounding quotes if any
    if ((v.startsWith('"') && v.endsWith('"')) || (v.startsWith("'") && v.endsWith("'")))
      return v.slice(1, -1);
    return v;
  }

  // ─── JSON → TOML ─────────────────────────────────────────────────────────
  function tomlStringify(obj, indent) {
    return buildTOML(obj, [], indent || '');
  }

  function buildTOML(obj, path, indent) {
    let scalars = '', tables = '';
    for (const [k, v] of Object.entries(obj)) {
      const key = /^[A-Za-z0-9_-]+$/.test(k) ? k : '"' + k + '"';
      if (v === null || v === undefined) {
        scalars += key + ' = ""\n';
      } else if (typeof v === 'boolean') {
        scalars += key + ' = ' + v + '\n';
      } else if (typeof v === 'number') {
        scalars += key + ' = ' + v + '\n';
      } else if (typeof v === 'string') {
        scalars += key + ' = ' + JSON.stringify(v) + '\n';
      } else if (Array.isArray(v)) {
        if (v.length === 0 || typeof v[0] !== 'object' || v[0] === null) {
          scalars += key + ' = ' + tomlArray(v) + '\n';
        } else {
          // Array of tables
          for (const item of v) {
            tables += '\n[[' + [...path, key].join('.') + ']]\n';
            tables += buildTOMLScalars(item, [...path, key]);
          }
        }
      } else if (typeof v === 'object') {
        tables += '\n[' + [...path, key].join('.') + ']\n';
        tables += buildTOML(v, [...path, key], indent);
      }
    }
    return scalars + tables;
  }

  function buildTOMLScalars(obj, path) {
    let out = '';
    for (const [k, v] of Object.entries(obj)) {
      const key = /^[A-Za-z0-9_-]+$/.test(k) ? k : '"' + k + '"';
      if (typeof v === 'object' && v !== null && !Array.isArray(v)) {
        out += '\n[' + [...path, key].join('.') + ']\n';
        out += buildTOMLScalars(v, [...path, key]);
      } else if (Array.isArray(v) && v.length > 0 && typeof v[0] === 'object') {
        for (const item of v) {
          out += '\n[[' + [...path, key].join('.') + ']]\n';
          out += buildTOMLScalars(item, [...path, key]);
        }
      } else {
        if (v === null) out += key + ' = ""\n';
        else if (typeof v === 'boolean') out += key + ' = ' + v + '\n';
        else if (typeof v === 'number') out += key + ' = ' + v + '\n';
        else if (typeof v === 'string') out += key + ' = ' + JSON.stringify(v) + '\n';
        else out += key + ' = ' + tomlArray(v) + '\n';
      }
    }
    return out;
  }

  function tomlArray(arr) {
    return '[' + arr.map(v => {
      if (typeof v === 'string') return JSON.stringify(v);
      if (typeof v === 'object' && v !== null) return '{' + Object.entries(v).map(([k2, v2]) => k2 + ' = ' + (typeof v2 === 'string' ? JSON.stringify(v2) : v2)).join(', ') + '}';
      return String(v);
    }).join(', ') + ']';
  }

  // ─── Convert functions ───────────────────────────────────────────────────
  window.taConvertToJson = function () {
    const input = document.getElementById('ta-input');
    const output = document.getElementById('ta-output');
    const pretty = document.getElementById('ta-pretty').checked;
    const minify = document.getElementById('ta-minify').checked;
    const src = input.value.trim();
    if (!src) {
      setStatus('ta-input-status', 'err', 'Input is empty.');
      input.classList.add('ta-error');
      return;
    }
    input.classList.remove('ta-error');
    try {
      let parsed;
      // Detect INI by looking for ; comments or = without TOML-style quoting needs
      const looksLikeINI = /^\s*\[/.test(src) && /^\s*(;|#)/.test(src.split('\n').find(l => l.trim()) || '');
      // Better heuristic: if has ; comments or no quotes around string values -> likely INI
      const hasINIComments = src.split('\n').some(l => l.trim().startsWith(';'));
      parsed = (hasINIComments || (isINI(src) && !src.includes('"""') && !src.match(/\[.+\..+\]/)))
        ? parseINI(src)
        : parseTOML(src);
      const indent = (!minify && pretty) ? 2 : undefined;
      output.value = JSON.stringify(parsed, null, indent);
      output.classList.remove('ta-error');
      setStatus('ta-input-status', 'ok', 'Parsed successfully.');
      setStatus('ta-output-status', 'ok', 'JSON ready.');
    } catch (e) {
      input.classList.add('ta-error');
      output.value = '';
      setStatus('ta-input-status', 'err', 'Error: ' + e.message);
      setStatus('ta-output-status', '', '');
    }
  };

  window.taConvertToToml = function () {
    const input = document.getElementById('ta-input');
    const output = document.getElementById('ta-output');
    const src = output.value.trim() || document.getElementById('ta-output').value.trim();
    const jsonSrc = output.value.trim();
    if (!jsonSrc) {
      setStatus('ta-output-status', 'err', 'JSON output area is empty. Paste JSON there first.');
      output.classList.add('ta-error');
      return;
    }
    output.classList.remove('ta-error');
    try {
      const parsed = JSON.parse(jsonSrc);
      if (typeof parsed !== 'object' || parsed === null || Array.isArray(parsed)) {
        throw new Error('Top-level JSON must be an object (not array or primitive).');
      }
      const toml = tomlStringify(parsed).trimStart();
      input.value = toml;
      input.classList.remove('ta-error');
      setStatus('ta-output-status', 'ok', 'Converted to TOML.');
      setStatus('ta-input-status', 'ok', 'TOML ready.');
    } catch (e) {
      output.classList.add('ta-error');
      setStatus('ta-output-status', 'err', 'Error: ' + e.message);
    }
  };

  // Sync pretty/minify options
  document.getElementById('ta-pretty').addEventListener('change', function () {
    if (this.checked) document.getElementById('ta-minify').checked = false;
  });
  document.getElementById('ta-minify').addEventListener('change', function () {
    if (this.checked) document.getElementById('ta-pretty').checked = false;
  });
})();
</script>

---

## How It Works

**TOML/INI to JSON** — Paste your config file in the left panel and click **TOML/INI → JSON**. The tool auto-detects whether the input is TOML or INI format.

**JSON to TOML** — Paste or generate JSON in the right panel and click **JSON → TOML** to produce a clean TOML file in the left panel.

### Supported TOML Features

| Feature | Example |
|---|---|
| Strings (basic & literal) | `name = "hello"`, `path = 'C:\tmp'` |
| Integers & floats | `port = 8080`, `ratio = 3.14` |
| Booleans | `debug = true` |
| Arrays | `features = ["a", "b"]` |
| Standard tables | `[database]` |
| Array of tables | `[[dependencies]]` |
| Dotted keys | `server.host = "localhost"` |
| Inline tables | `opts = { a = 1, b = 2 }` |

### INI Format Support

INI sections (`[section]`), `key = value` pairs, and `;` or `#` comments are all parsed. Values are auto-coerced: `true`/`yes`/`on` become booleans, numeric strings become numbers.

### Tips

- Use **Cargo.toml** or **pyproject.toml** presets to see real-world examples.
- Enable **Minify JSON** to get compact output for embedding in code.
- The **Copy** button on each panel copies the content to your clipboard.
- JSON → TOML works from the right (JSON) panel — paste JSON there, then click the button.

---

## Related Tools

- [YAML ↔ JSON Converter](/tools/yaml-json-converter/) — Convert between YAML and JSON
- [JSON Formatter & Validator](/tools/json-formatter/) — Format, validate, and minify JSON
- [JSON Schema Generator](/tools/json-schema-generator/) — Generate JSON Schema from a JSON sample
