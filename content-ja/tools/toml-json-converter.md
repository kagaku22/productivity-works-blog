---
title: "TOML/INI ↔ JSON 変換ツール"
date: 2025-08-13
description: "TOML・INI・JSON形式間の変換。双方向変換＆構文検証。Cargo.toml・pyproject.toml・設定ファイルのプリセット。"
categories: ["無料ツール"]
slug: "toml-json-converter"
ShowToc: false
cover:
  image: "/images/covers/toml-json-converter-ja.png"
  alt: "TOML/INI ↔ JSON 変換ツール"
---

TOML・INI 形式の設定ファイルを JSON に変換、または JSON を TOML に変換できるツールです。ブラウザ上で完結するので、ファイルのアップロード不要。インストール不要でそのまま使えます。

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
    font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", "Segoe UI", sans-serif;
    font-size: 14px;
    color: #1a1a2e;
    line-height: 1.6;
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
    letter-spacing: 0.04em;
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
    letter-spacing: 0.04em;
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
    animation: taCopyFlashJa 0.6s ease;
  }
  @keyframes taCopyFlashJa {
    0% { background: #a7f3d0; }
    100% { background: #f9fafb; }
  }
  #toml-app .ta-freee-cta {
    margin-top: 24px;
    padding: 18px 20px;
    background: linear-gradient(135deg, #eef2ff 0%, #f0fdf4 100%);
    border: 1px solid #c7d2fe;
    border-radius: 10px;
    font-size: 13.5px;
    color: #1e1b4b;
    line-height: 1.7;
  }
  #toml-app .ta-freee-cta strong {
    display: block;
    font-size: 15px;
    margin-bottom: 6px;
    color: #3730a3;
  }
  #toml-app .ta-freee-cta a {
    display: inline-block;
    margin-top: 10px;
    padding: 8px 18px;
    background: #4f46e5;
    color: #fff;
    border-radius: 6px;
    text-decoration: none;
    font-weight: 600;
    font-size: 13px;
    transition: background 0.15s;
  }
  #toml-app .ta-freee-cta a:hover { background: #4338ca; }
</style>

<div class="ta-presets-row">
  <span class="ta-presets-label">プリセット:</span>
  <button class="ta-preset-btn" onclick="taJaLoadPreset('cargo')">Cargo.toml</button>
  <button class="ta-preset-btn" onclick="taJaLoadPreset('pyproject')">pyproject.toml</button>
  <button class="ta-preset-btn" onclick="taJaLoadPreset('ini')">config.ini</button>
  <button class="ta-preset-btn" onclick="taJaLoadPreset('json')">JSONサンプル</button>
</div>

<div class="ta-options-row">
  <label class="ta-check-label">
    <input type="checkbox" id="taja-pretty" checked>
    JSONを整形して出力
  </label>
  <label class="ta-check-label">
    <input type="checkbox" id="taja-minify">
    JSONを最小化（minify）
  </label>
</div>

<div class="ta-panels">
  <div class="ta-panel">
    <div class="ta-panel-header">
      <span class="ta-panel-label">TOML / INI 入力</span>
      <div class="ta-panel-actions">
        <button class="ta-btn ta-btn-ghost" onclick="taJaClear('taja-input')" style="font-size:12px;padding:4px 9px;">クリア</button>
        <button class="ta-btn ta-btn-ghost" onclick="taJaCopyText('taja-input')" style="font-size:12px;padding:4px 9px;">コピー</button>
      </div>
    </div>
    <textarea id="taja-input" placeholder="TOMLまたはINIをここに貼り付け..." spellcheck="false"></textarea>
    <div id="taja-input-status" class="ta-status"></div>
  </div>

  <div class="ta-panel">
    <div class="ta-panel-header">
      <span class="ta-panel-label">JSON 出力</span>
      <div class="ta-panel-actions">
        <button class="ta-btn ta-btn-ghost" onclick="taJaClear('taja-output')" style="font-size:12px;padding:4px 9px;">クリア</button>
        <button class="ta-btn ta-btn-ghost" onclick="taJaCopyText('taja-output')" style="font-size:12px;padding:4px 9px;">コピー</button>
      </div>
    </div>
    <textarea id="taja-output" placeholder="JSON出力がここに表示されます..." spellcheck="false"></textarea>
    <div id="taja-output-status" class="ta-status"></div>
  </div>
</div>

<div class="ta-convert-row">
  <button class="ta-btn ta-btn-primary" onclick="taJaConvertToJson()">TOML/INI &rarr; JSON に変換</button>
  <span class="ta-arrow">&#8644;</span>
  <button class="ta-btn ta-btn-success" onclick="taJaConvertToToml()">JSON &rarr; TOML に変換</button>
</div>

<div class="ta-divider"></div>

<div class="ta-freee-cta">
  <strong>freee会計と連携している開発者の方へ</strong>
  freee APIのレスポンスはJSON形式です。このツールでJSONをTOML設定ファイルに変換し、Rustなどの設定管理に活用できます。freee APIの活用方法やAI自動化については下記をご覧ください。
  <a href="/freee-api-automation/" target="_blank" rel="noopener">freee API活用ガイドを見る</a>
</div>
</div>

<script>
(function () {
  var PRESETS_JA = {
    cargo: `[package]
name = "my-app"
version = "0.1.0"
edition = "2021"
authors = ["Taro <taro@example.com>"]
description = "Rustプロジェクトのサンプル"
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
description = "Pythonパッケージのサンプル"
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

  window.taJaLoadPreset = function (name) {
    if (name === 'json') {
      document.getElementById('taja-output').value = PRESETS_JA.json;
    } else {
      document.getElementById('taja-input').value = PRESETS_JA[name] || '';
    }
    document.getElementById('taja-input').classList.remove('ta-error');
    document.getElementById('taja-output').classList.remove('ta-error');
    setStatusJa('taja-input-status', '', '');
    setStatusJa('taja-output-status', '', '');
  };

  window.taJaClear = function (id) {
    document.getElementById(id).value = '';
    document.getElementById(id).classList.remove('ta-error');
    var statusId = id === 'taja-input' ? 'taja-input-status' : 'taja-output-status';
    setStatusJa(statusId, '', '');
  };

  window.taJaCopyText = function (id) {
    var el = document.getElementById(id);
    var val = el.value;
    if (!val) return;
    navigator.clipboard.writeText(val).then(function () {
      el.classList.add('ta-copy-flash');
      setTimeout(function () { el.classList.remove('ta-copy-flash'); }, 700);
    }).catch(function () {
      el.select();
      document.execCommand('copy');
    });
  };

  function setStatusJa(id, type, msg) {
    var el = document.getElementById(id);
    el.className = 'ta-status' + (type ? ' ' + type : '');
    el.textContent = msg;
  }

  // ─── TOML Parser ─────────────────────────────────────────────────────────
  function parseTOMLJa(src) {
    var lines = src.split('\n');
    var root = {};
    var current = root;
    var currentPath = [];
    var i = 0;

    function parseValueJa(s) {
      s = s.trim();
      if (s.startsWith('"""') || s.startsWith("'''")) {
        var delim = s.slice(0, 3);
        var end = s.indexOf(delim, 3);
        if (end === -1) throw new Error('未終端の複数行文字列');
        return s.slice(3, end);
      }
      if (s.startsWith('"')) {
        var m = s.match(/^"((?:[^"\\]|\\.)*)"$/);
        if (!m) throw new Error('文字列が不正: ' + s);
        return m[1].replace(/\\n/g, '\n').replace(/\\t/g, '\t').replace(/\\r/g, '\r').replace(/\\"/g, '"').replace(/\\\\/g, '\\');
      }
      if (s.startsWith("'")) {
        var ml = s.match(/^'([^']*)'$/);
        if (!ml) throw new Error('リテラル文字列が不正: ' + s);
        return ml[1];
      }
      if (s.startsWith('[')) return parseArrayJa(s);
      if (s.startsWith('{')) return parseInlineTableJa(s);
      if (s === 'true') return true;
      if (s === 'false') return false;
      if (/^-?\d{4}-\d{2}-\d{2}(T[\d:+Z.-]+)?$/.test(s)) return s;
      if (/^[+-]?(?:0x[0-9a-fA-F_]+|0o[0-7_]+|0b[01_]+)$/.test(s)) {
        var clean = s.replace(/_/g, '');
        return parseInt(clean, clean.startsWith('0x') ? 16 : clean.startsWith('0o') ? 8 : 2);
      }
      if (/^[+-]?(inf|nan)$/.test(s)) return s === 'inf' || s === '+inf' ? Infinity : s === '-inf' ? -Infinity : NaN;
      if (/^[+-]?\d[\d_]*$/.test(s)) return parseInt(s.replace(/_/g, ''), 10);
      if (/^[+-]?\d[\d_]*\.[\d_]*(e[+-]?\d+)?$/i.test(s)) return parseFloat(s.replace(/_/g, ''));
      if (/^[+-]?\d[\d_]*e[+-]?\d+$/i.test(s)) return parseFloat(s.replace(/_/g, ''));
      throw new Error('値を解析できません: ' + s);
    }

    function parseArrayJa(s) {
      s = s.trim();
      var depth = 0, inStr = false, strChar = '', result = [], buf = '';
      for (var ci = 0; ci < s.length; ci++) {
        var ch = s[ci];
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
            var t = buf.trim();
            if (t) result.push(parseValueJa(t));
            break;
          }
          buf += ch;
        } else if (ch === ',' && depth === 1) {
          var t2 = buf.trim();
          if (t2) result.push(parseValueJa(t2));
          buf = '';
        } else if (ch === '#' && depth === 1) {
          break;
        } else {
          if (depth >= 1) buf += ch;
        }
      }
      return result;
    }

    function parseInlineTableJa(s) {
      s = s.trim();
      var inner = s.slice(1, s.lastIndexOf('}'));
      var obj = {};
      var depth = 0, inStr = false, strChar2 = '', buf = '', parts = [];
      for (var ci = 0; ci < inner.length; ci++) {
        var ch = inner[ci];
        if (inStr) {
          if (ch === strChar2 && inner[ci-1] !== '\\') inStr = false;
          buf += ch;
        } else if (ch === '"' || ch === "'") {
          inStr = true; strChar2 = ch; buf += ch;
        } else if (ch === '{' || ch === '[') { depth++; buf += ch; }
        else if (ch === '}' || ch === ']') { depth--; buf += ch; }
        else if (ch === ',' && depth === 0) { parts.push(buf.trim()); buf = ''; }
        else buf += ch;
      }
      if (buf.trim()) parts.push(buf.trim());
      for (var pi = 0; pi < parts.length; pi++) {
        var part = parts[pi];
        var eq = part.indexOf('=');
        if (eq === -1) throw new Error('インラインテーブルのエントリが不正: ' + part);
        var k = part.slice(0, eq).trim();
        var v = part.slice(eq + 1).trim();
        obj[unquoteKeyJa(k)] = parseValueJa(v);
      }
      return obj;
    }

    function unquoteKeyJa(k) {
      if ((k.startsWith('"') && k.endsWith('"')) || (k.startsWith("'") && k.endsWith("'")))
        return k.slice(1, -1);
      return k;
    }

    function parseKeyJa(raw) {
      var parts = [], buf = '', inStr = false, strChar3 = '';
      for (var ci = 0; ci < raw.length; ci++) {
        var ch = raw[ci];
        if (inStr) {
          if (ch === strChar3) { inStr = false; parts.push(buf); buf = ''; }
          else buf += ch;
        } else if (ch === '"' || ch === "'") {
          inStr = true; strChar3 = ch;
        } else if (ch === '.') {
          if (buf.trim()) parts.push(buf.trim());
          buf = '';
        } else buf += ch;
      }
      if (buf.trim()) parts.push(buf.trim());
      return parts.map(unquoteKeyJa);
    }

    while (i < lines.length) {
      var line = lines[i].replace(/\s*#[^"']*$/, '').trim();
      i++;
      if (!line) continue;

      if (line.startsWith('[[')) {
        var key = line.slice(2, line.indexOf(']]')).trim();
        var keyParts = parseKeyJa(key);
        var ref = root;
        for (var ki = 0; ki < keyParts.length - 1; ki++) {
          var k = keyParts[ki];
          if (!(k in ref)) ref[k] = {};
          if (Array.isArray(ref[k])) ref = ref[k][ref[k].length - 1];
          else ref = ref[k];
        }
        var last = keyParts[keyParts.length - 1];
        if (!Array.isArray(ref[last])) ref[last] = [];
        var newTable = {};
        ref[last].push(newTable);
        current = newTable;
        currentPath = keyParts;
        continue;
      }

      if (line.startsWith('[')) {
        var key2 = line.slice(1, line.indexOf(']')).trim();
        currentPath = parseKeyJa(key2);
        current = root;
        for (var ki2 = 0; ki2 < currentPath.length; ki2++) {
          var k2 = currentPath[ki2];
          if (!(k2 in current)) current[k2] = {};
          if (Array.isArray(current[k2])) current = current[k2][current[k2].length - 1];
          else current = current[k2];
        }
        continue;
      }

      var eqIdx = line.indexOf('=');
      if (eqIdx === -1) throw new Error('等号が見つかりません: ' + line);
      var rawKey = line.slice(0, eqIdx).trim();
      var rawVal = line.slice(eqIdx + 1).trim();

      if (rawVal.startsWith('[') && !rawVal.includes(']')) {
        while (i < lines.length && !rawVal.includes(']')) {
          rawVal += ' ' + lines[i].replace(/\s*#.*$/, '').trim();
          i++;
        }
      }

      var keyPartsKV = parseKeyJa(rawKey);
      var refKV = current;
      for (var kki = 0; kki < keyPartsKV.length - 1; kki++) {
        var kk = keyPartsKV[kki];
        if (!(kk in refKV)) refKV[kk] = {};
        refKV = refKV[kk];
      }
      refKV[keyPartsKV[keyPartsKV.length - 1]] = parseValueJa(rawVal);
    }
    return root;
  }

  // ─── INI Parser ──────────────────────────────────────────────────────────
  function parseINIJa(src) {
    var lines = src.split('\n');
    var result = {};
    var section = null;
    for (var li = 0; li < lines.length; li++) {
      var line = lines[li].trim();
      if (!line || line.startsWith(';') || line.startsWith('#')) continue;
      if (line.startsWith('[') && line.endsWith(']')) {
        section = line.slice(1, -1).trim();
        if (!(section in result)) result[section] = {};
        continue;
      }
      var eq = line.indexOf('=');
      if (eq === -1) continue;
      var key = line.slice(0, eq).trim();
      var val = line.slice(eq + 1).trim();
      var target = section ? result[section] : result;
      target[key] = coerceINIJa(val);
    }
    return result;
  }

  function coerceINIJa(v) {
    if (v === 'true' || v === 'yes' || v === 'on') return true;
    if (v === 'false' || v === 'no' || v === 'off') return false;
    if (/^-?\d+$/.test(v)) return parseInt(v, 10);
    if (/^-?\d+\.\d+$/.test(v)) return parseFloat(v);
    if ((v.startsWith('"') && v.endsWith('"')) || (v.startsWith("'") && v.endsWith("'")))
      return v.slice(1, -1);
    return v;
  }

  // ─── JSON → TOML ─────────────────────────────────────────────────────────
  function buildTOMLJa(obj, path) {
    var scalars = '', tables = '';
    var entries = Object.entries(obj);
    for (var ei = 0; ei < entries.length; ei++) {
      var k = entries[ei][0], v = entries[ei][1];
      var key = /^[A-Za-z0-9_-]+$/.test(k) ? k : '"' + k + '"';
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
          scalars += key + ' = ' + tomlArrayJa(v) + '\n';
        } else {
          for (var ai = 0; ai < v.length; ai++) {
            tables += '\n[[' + path.concat(key).join('.') + ']]\n';
            tables += buildTOMLScalarsJa(v[ai], path.concat(key));
          }
        }
      } else if (typeof v === 'object') {
        tables += '\n[' + path.concat(key).join('.') + ']\n';
        tables += buildTOMLJa(v, path.concat(key));
      }
    }
    return scalars + tables;
  }

  function buildTOMLScalarsJa(obj, path) {
    var out = '';
    var entries = Object.entries(obj);
    for (var ei = 0; ei < entries.length; ei++) {
      var k = entries[ei][0], v = entries[ei][1];
      var key = /^[A-Za-z0-9_-]+$/.test(k) ? k : '"' + k + '"';
      if (typeof v === 'object' && v !== null && !Array.isArray(v)) {
        out += '\n[' + path.concat(key).join('.') + ']\n';
        out += buildTOMLScalarsJa(v, path.concat(key));
      } else if (Array.isArray(v) && v.length > 0 && typeof v[0] === 'object') {
        for (var ai = 0; ai < v.length; ai++) {
          out += '\n[[' + path.concat(key).join('.') + ']]\n';
          out += buildTOMLScalarsJa(v[ai], path.concat(key));
        }
      } else {
        if (v === null) out += key + ' = ""\n';
        else if (typeof v === 'boolean') out += key + ' = ' + v + '\n';
        else if (typeof v === 'number') out += key + ' = ' + v + '\n';
        else if (typeof v === 'string') out += key + ' = ' + JSON.stringify(v) + '\n';
        else out += key + ' = ' + tomlArrayJa(v) + '\n';
      }
    }
    return out;
  }

  function tomlArrayJa(arr) {
    return '[' + arr.map(function(v) {
      if (typeof v === 'string') return JSON.stringify(v);
      if (typeof v === 'object' && v !== null) {
        return '{' + Object.entries(v).map(function(e) {
          return e[0] + ' = ' + (typeof e[1] === 'string' ? JSON.stringify(e[1]) : e[1]);
        }).join(', ') + '}';
      }
      return String(v);
    }).join(', ') + ']';
  }

  // ─── Convert ─────────────────────────────────────────────────────────────
  window.taJaConvertToJson = function () {
    var input = document.getElementById('taja-input');
    var output = document.getElementById('taja-output');
    var pretty = document.getElementById('taja-pretty').checked;
    var minify = document.getElementById('taja-minify').checked;
    var src = input.value.trim();
    if (!src) {
      setStatusJa('taja-input-status', 'err', '入力が空です。');
      input.classList.add('ta-error');
      return;
    }
    input.classList.remove('ta-error');
    try {
      var parsed;
      var hasINIComments = src.split('\n').some(function(l) { return l.trim().startsWith(';'); });
      parsed = hasINIComments ? parseINIJa(src) : parseTOMLJa(src);
      var indent = (!minify && pretty) ? 2 : undefined;
      output.value = JSON.stringify(parsed, null, indent);
      output.classList.remove('ta-error');
      setStatusJa('taja-input-status', 'ok', '解析成功');
      setStatusJa('taja-output-status', 'ok', 'JSON出力完了');
    } catch (e) {
      input.classList.add('ta-error');
      output.value = '';
      setStatusJa('taja-input-status', 'err', 'エラー: ' + e.message);
      setStatusJa('taja-output-status', '', '');
    }
  };

  window.taJaConvertToToml = function () {
    var input = document.getElementById('taja-input');
    var output = document.getElementById('taja-output');
    var jsonSrc = output.value.trim();
    if (!jsonSrc) {
      setStatusJa('taja-output-status', 'err', 'JSON出力欄が空です。先にJSONを貼り付けてください。');
      output.classList.add('ta-error');
      return;
    }
    output.classList.remove('ta-error');
    try {
      var parsed = JSON.parse(jsonSrc);
      if (typeof parsed !== 'object' || parsed === null || Array.isArray(parsed)) {
        throw new Error('JSONのトップレベルはオブジェクト（{}）である必要があります。');
      }
      var toml = buildTOMLJa(parsed, []).replace(/^\n/, '');
      input.value = toml;
      input.classList.remove('ta-error');
      setStatusJa('taja-output-status', 'ok', 'TOMLへの変換完了');
      setStatusJa('taja-input-status', 'ok', 'TOML出力完了');
    } catch (e) {
      output.classList.add('ta-error');
      setStatusJa('taja-output-status', 'err', 'エラー: ' + e.message);
    }
  };

  document.getElementById('taja-pretty').addEventListener('change', function () {
    if (this.checked) document.getElementById('taja-minify').checked = false;
  });
  document.getElementById('taja-minify').addEventListener('change', function () {
    if (this.checked) document.getElementById('taja-pretty').checked = false;
  });
})();
</script>

---

## 使い方

**TOML/INI → JSON 変換**
左のテキストエリアに TOML または INI ファイルの内容を貼り付け、「TOML/INI → JSON に変換」ボタンをクリックします。形式は自動判定されます（`;` コメントがある場合は INI として処理）。

**JSON → TOML 変換**
右のテキストエリアに JSON を貼り付け（またはTOML→JSON変換後の結果をそのまま使い）、「JSON → TOML に変換」ボタンをクリックします。

### 対応している TOML の機能

| 機能 | 例 |
|---|---|
| 文字列（基本・リテラル） | `name = "hello"`, `path = 'C:\tmp'` |
| 整数・浮動小数点数 | `port = 8080`, `ratio = 3.14` |
| 真偽値 | `debug = true` |
| 配列 | `features = ["a", "b"]` |
| 標準テーブル | `[database]` |
| テーブルの配列 | `[[dependencies]]` |
| ドット区切りキー | `server.host = "localhost"` |
| インラインテーブル | `opts = { a = 1, b = 2 }` |

### INI 形式について

`[セクション]`、`key = value` の形式、`;` や `#` のコメント行に対応しています。値は自動的に型変換されます（`true`/`yes`/`on` は真偽値、数値文字列は数値型に変換）。

### 使いこなしのコツ

- **Cargo.toml**・**pyproject.toml** のプリセットで実際の設定ファイル例を確認できます。
- **JSONを最小化** オプションでコード埋め込みに適したコンパクトなJSONを出力できます。
- **コピー** ボタンでクリップボードにコピーできます。
- JSON → TOML 変換は右側（JSON出力欄）にJSONを貼り付けてから変換ボタンを押してください。

---

## 関連ツール

- [YAML ↔ JSON 変換ツール](/ja/tools/yaml-json-converter/) — YAMLとJSONを相互変換
- [JSONフォーマッター・バリデーター](/ja/tools/json-formatter/) — JSONの整形・検証・最小化
- [JSONスキーマジェネレーター](/ja/tools/json-schema-generator/) — JSONサンプルからJSONスキーマを自動生成

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

