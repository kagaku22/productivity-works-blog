---
title: "JSON Path Tester - Free Online JSONPath Query Tool"
date: 2025-05-16
description: "Test JSONPath expressions against JSON data interactively. Supports dot notation, bracket notation, array indexes, wildcards, recursive descent, and basic filter expressions. Results highlighted instantly. Free, no install."
categories: ["Free Tools"]
tags: ["JSONPath", "JSON query", "JSONPath tester", "JSON filter", "JSON parser", "dot notation", "recursive descent"]
slug: "json-path-tester"
aliases: ["/tools/json-path-finder/", "/tools/json-path-finder/"]
cover:
  image: "/images/covers/json-path-tester.png"
  alt: "JSON Path Tester"
ShowToc: false
---

<div id="jp-app">

<style>
#jp-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  max-width: 900px;
  margin: 0 auto;
  box-sizing: border-box;
}
#jp-app * { box-sizing: border-box; }

#jp-app h2 {
  color: #a78bfa;
  font-size: 1.05rem;
  margin: 0 0 12px;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

#jp-app .two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 14px;
}
@media (max-width: 640px) {
  #jp-app .two-col { grid-template-columns: 1fr; }
}

#jp-app .panel {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 10px;
  padding: 14px;
  display: flex;
  flex-direction: column;
}
#jp-app .panel-label {
  font-size: 0.73rem;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.09em;
  font-weight: 600;
  margin-bottom: 8px;
}
#jp-app textarea {
  flex: 1;
  background: #0f172a;
  border: 1.5px solid #334155;
  color: #e2e8f0;
  border-radius: 7px;
  padding: 10px 12px;
  font-family: 'Courier New', monospace;
  font-size: 0.88rem;
  resize: vertical;
  min-height: 220px;
  line-height: 1.6;
  transition: border-color 0.15s;
}
#jp-app textarea:focus { outline: none; border-color: #a78bfa; }
#jp-app textarea.error { border-color: #ef4444; }

#jp-app .path-row {
  display: flex;
  gap: 10px;
  margin-bottom: 14px;
  align-items: stretch;
  flex-wrap: wrap;
}
#jp-app .path-input-wrap {
  flex: 1;
  min-width: 200px;
  position: relative;
}
#jp-app .path-input {
  width: 100%;
  background: #1e293b;
  border: 1.5px solid #334155;
  color: #e2e8f0;
  border-radius: 8px;
  padding: 11px 14px;
  font-size: 0.97rem;
  font-family: 'Courier New', monospace;
  transition: border-color 0.15s;
}
#jp-app .path-input:focus { outline: none; border-color: #a78bfa; }
#jp-app .path-input.error { border-color: #ef4444; }

#jp-app .run-btn {
  background: #7c3aed;
  border: none;
  color: #fff;
  border-radius: 8px;
  padding: 11px 22px;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
}
#jp-app .run-btn:hover { background: #6d28d9; }

#jp-app .suggestions {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  margin-bottom: 14px;
}
#jp-app .sug-label {
  font-size: 0.73rem;
  color: #64748b;
  align-self: center;
  white-space: nowrap;
}
#jp-app .sug-chip {
  background: #1e293b;
  border: 1px solid #334155;
  color: #a78bfa;
  border-radius: 5px;
  padding: 4px 10px;
  font-size: 0.78rem;
  font-family: 'Courier New', monospace;
  cursor: pointer;
  transition: all 0.15s;
}
#jp-app .sug-chip:hover {
  background: #2e1065;
  border-color: #a78bfa;
}

#jp-app .result-panel {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 14px;
}
#jp-app .result-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  flex-wrap: wrap;
  gap: 8px;
}
#jp-app .result-count {
  font-size: 0.82rem;
  color: #64748b;
}
#jp-app .result-count .match-num {
  color: #4ade80;
  font-weight: 700;
}
#jp-app .copy-result-btn {
  background: #2e1065;
  border: 1px solid #a78bfa;
  color: #a78bfa;
  border-radius: 6px;
  padding: 5px 13px;
  font-size: 0.78rem;
  cursor: pointer;
  transition: all 0.15s;
}
#jp-app .copy-result-btn:hover { background: #a78bfa; color: #0f172a; }
#jp-app .copy-result-btn.copied { background: #a78bfa; color: #0f172a; }

#jp-app .result-items {
  display: flex;
  flex-direction: column;
  gap: 6px;
  max-height: 360px;
  overflow-y: auto;
}
#jp-app .result-item {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 6px;
  padding: 8px 12px;
  font-family: 'Courier New', monospace;
  font-size: 0.87rem;
  line-height: 1.55;
  color: #c4b5fd;
  position: relative;
}
#jp-app .result-item .item-idx {
  position: absolute;
  top: 6px;
  right: 10px;
  font-size: 0.68rem;
  color: #475569;
}
#jp-app .result-item .item-val { color: #e2e8f0; }
#jp-app .result-item .item-val .str { color: #86efac; }
#jp-app .result-item .item-val .num { color: #fbbf24; }
#jp-app .result-item .item-val .bool { color: #f87171; }
#jp-app .result-item .item-val .null { color: #94a3b8; }
#jp-app .result-item .item-key { color: #a78bfa; }

#jp-app .error-panel {
  background: #1e293b;
  border: 1.5px solid #7f1d1d;
  border-radius: 10px;
  padding: 13px 16px;
  color: #fca5a5;
  font-size: 0.87rem;
  font-family: 'Courier New', monospace;
  margin-bottom: 14px;
}

#jp-app .placeholder-msg {
  text-align: center;
  color: #475569;
  padding: 28px 0;
  font-size: 0.92rem;
}

#jp-app .path-err {
  color: #ef4444;
  font-size: 0.8rem;
  margin-top: 4px;
  margin-bottom: 0;
  min-height: 16px;
}

#jp-app .json-err {
  color: #ef4444;
  font-size: 0.8rem;
  margin-top: 4px;
}
</style>

<h2>JSON Path Tester</h2>

<div class="two-col">
  <div class="panel">
    <div class="panel-label">JSON Input</div>
    <textarea id="jp-json" placeholder='{"store":{"book":[{"title":"Foo","price":8},{"title":"Bar","price":15}],"name":"MyStore"}}' oninput="jpRun()"></textarea>
    <div class="json-err" id="jp-json-err"></div>
  </div>
  <div class="panel">
    <div class="panel-label">Result</div>
    <div id="jp-result-area">
      <div class="placeholder-msg">Enter JSON and a JSONPath expression to see results</div>
    </div>
  </div>
</div>

<div class="path-row">
  <div class="path-input-wrap">
    <input class="path-input" id="jp-path" type="text" placeholder="$.store.book[0].title" oninput="jpRun()" autocomplete="off" spellcheck="false">
  </div>
  <button class="run-btn" onclick="jpRun()">Run</button>
</div>
<div class="path-err" id="jp-path-err"></div>

<div class="suggestions">
  <span class="sug-label">Try:</span>
  <span class="sug-chip" onclick="jpSug('$')">$</span>
  <span class="sug-chip" onclick="jpSug('$.store')">$.store</span>
  <span class="sug-chip" onclick="jpSug('$.store.book[0]')">$.store.book[0]</span>
  <span class="sug-chip" onclick="jpSug('$.store.book[*].title')">$.store.book[*].title</span>
  <span class="sug-chip" onclick="jpSug('$..title')">$..title</span>
  <span class="sug-chip" onclick="jpSug('$.store.book[?(@.price<10)]')">$.store.book[?(@.price&lt;10)]</span>
  <span class="sug-chip" onclick="jpSug('$.store.*')">$.store.*</span>
  <span class="sug-chip" onclick="jpSug('$..price')">$..price</span>
</div>

<script>
(function() {
  // ── JSONPath Evaluator ──────────────────────────────────────────────────────

  function jpEval(obj, path) {
    path = path.trim();
    if (!path.startsWith('$')) throw new Error('Path must start with $');

    var tokens = tokenize(path.slice(1)); // remove leading $
    return query([obj], tokens);
  }

  function tokenize(path) {
    var tokens = [];
    var i = 0;
    while (i < path.length) {
      // Recursive descent ..
      if (path[i] === '.' && path[i + 1] === '.') {
        tokens.push({ type: 'recurse' });
        i += 2;
        // Read next key if present
        var key = readKey(path, i);
        if (key !== null) {
          tokens.push({ type: 'key', value: key.value });
          i += key.len;
        }
        continue;
      }
      // Dot notation
      if (path[i] === '.') {
        i++;
        var key2 = readKey(path, i);
        if (key2 !== null) {
          tokens.push({ type: 'key', value: key2.value });
          i += key2.len;
        }
        continue;
      }
      // Bracket notation
      if (path[i] === '[') {
        var close = findClose(path, i);
        var inner = path.slice(i + 1, close).trim();
        tokens.push(parseBracket(inner));
        i = close + 1;
        continue;
      }
      i++;
    }
    return tokens;
  }

  function readKey(path, i) {
    var match = path.slice(i).match(/^([a-zA-Z_$][a-zA-Z0-9_$]*|\*)/);
    if (!match) return null;
    return { value: match[1], len: match[1].length };
  }

  function findClose(path, start) {
    var depth = 0;
    for (var i = start; i < path.length; i++) {
      if (path[i] === '[') depth++;
      else if (path[i] === ']') { depth--; if (depth === 0) return i; }
    }
    return path.length - 1;
  }

  function parseBracket(inner) {
    // Wildcard
    if (inner === '*') return { type: 'key', value: '*' };
    // Array index
    if (/^-?\d+$/.test(inner)) return { type: 'index', value: parseInt(inner, 10) };
    // Slice a:b
    if (/^-?\d*:-?\d*$/.test(inner)) {
      var parts = inner.split(':');
      return { type: 'slice', start: parts[0] !== '' ? parseInt(parts[0], 10) : 0, end: parts[1] !== '' ? parseInt(parts[1], 10) : null };
    }
    // Multi-index [0,1,2]
    if (/^[\d\s,]+$/.test(inner)) {
      var idxs = inner.split(',').map(function(s) { return parseInt(s.trim(), 10); });
      return { type: 'multi-index', values: idxs };
    }
    // Filter [?(@.key op val)]
    var filterMatch = inner.match(/^\?\(@\.([a-zA-Z_$][a-zA-Z0-9_$.]*)\s*(==|!=|<=|>=|<|>)\s*(.+)\)$/);
    if (filterMatch) {
      return { type: 'filter', key: filterMatch[1], op: filterMatch[2], val: parseFilterVal(filterMatch[3].trim()) };
    }
    // Quoted string key
    var quotedMatch = inner.match(/^['"](.+)['"]$/);
    if (quotedMatch) return { type: 'key', value: quotedMatch[1] };
    // Bare key
    return { type: 'key', value: inner };
  }

  function parseFilterVal(s) {
    if (s === 'true') return true;
    if (s === 'false') return false;
    if (s === 'null') return null;
    var n = Number(s);
    if (!isNaN(n) && s !== '') return n;
    // String
    var m = s.match(/^['"](.*)['"]$/);
    if (m) return m[1];
    return s;
  }

  function query(nodes, tokens) {
    if (tokens.length === 0) return nodes;
    var tok = tokens[0];
    var rest = tokens.slice(1);
    var results = [];

    if (tok.type === 'recurse') {
      // Collect all descendants and apply rest
      nodes.forEach(function(node) {
        var descendants = collectAll(node);
        // For recurse followed by a key token, filter to apply the next token
        if (rest.length > 0 && rest[0].type === 'key') {
          var keyTok = rest[0];
          var restRest = rest.slice(1);
          descendants.forEach(function(d) {
            var r = applyToken(d, keyTok);
            if (r.length > 0) {
              var sub = query(r, restRest);
              results = results.concat(sub);
            }
          });
        } else {
          descendants.forEach(function(d) {
            var sub = query([d], rest);
            results = results.concat(sub);
          });
        }
      });
      return results;
    }

    nodes.forEach(function(node) {
      var r = applyToken(node, tok);
      results = results.concat(query(r, rest));
    });
    return results;
  }

  function applyToken(node, tok) {
    if (tok.type === 'key') {
      if (tok.value === '*') {
        if (Array.isArray(node)) return node;
        if (node !== null && typeof node === 'object') return Object.values(node);
        return [];
      }
      if (node !== null && typeof node === 'object' && !Array.isArray(node)) {
        return node.hasOwnProperty(tok.value) ? [node[tok.value]] : [];
      }
      return [];
    }
    if (tok.type === 'index') {
      if (!Array.isArray(node)) return [];
      var idx = tok.value < 0 ? node.length + tok.value : tok.value;
      return idx >= 0 && idx < node.length ? [node[idx]] : [];
    }
    if (tok.type === 'multi-index') {
      if (!Array.isArray(node)) return [];
      var res = [];
      tok.values.forEach(function(v) {
        var idx = v < 0 ? node.length + v : v;
        if (idx >= 0 && idx < node.length) res.push(node[idx]);
      });
      return res;
    }
    if (tok.type === 'slice') {
      if (!Array.isArray(node)) return [];
      var start = tok.start < 0 ? Math.max(0, node.length + tok.start) : tok.start;
      var end = tok.end === null ? node.length : (tok.end < 0 ? node.length + tok.end : tok.end);
      return node.slice(start, end);
    }
    if (tok.type === 'filter') {
      if (!Array.isArray(node)) return [];
      return node.filter(function(item) {
        if (item === null || typeof item !== 'object') return false;
        var keyParts = tok.key.split('.');
        var val = item;
        for (var i = 0; i < keyParts.length; i++) {
          if (val === null || typeof val !== 'object') return false;
          val = val[keyParts[i]];
        }
        return compare(val, tok.op, tok.val);
      });
    }
    return [];
  }

  function compare(a, op, b) {
    switch (op) {
      case '==': return a == b;
      case '!=': return a != b;
      case '<':  return a < b;
      case '<=': return a <= b;
      case '>':  return a > b;
      case '>=': return a >= b;
    }
    return false;
  }

  function collectAll(node) {
    var results = [node];
    if (Array.isArray(node)) {
      node.forEach(function(item) { results = results.concat(collectAll(item)); });
    } else if (node !== null && typeof node === 'object') {
      Object.values(node).forEach(function(v) { results = results.concat(collectAll(v)); });
    }
    return results;
  }

  // ── Syntax Highlighting ────────────────────────────────────────────────────

  function colorizeValue(val) {
    var json = JSON.stringify(val, null, 2);
    // Simple token coloring
    json = json
      .replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;')
      .replace(/"((?:[^"\\]|\\.)*)"/g, function(m, s) { return '<span class="str">"' + s + '"</span>'; })
      .replace(/\b(-?\d+\.?\d*(?:[eE][+-]?\d+)?)\b/g, '<span class="num">$1</span>')
      .replace(/\b(true|false)\b/g, '<span class="bool">$1</span>')
      .replace(/\bnull\b/g, '<span class="null">null</span>');
    return '<div class="item-val">' + json + '</div>';
  }

  // ── Auto-suggest from JSON keys ────────────────────────────────────────────

  function collectKeys(obj, prefix, depth) {
    if (depth > 4 || obj === null || typeof obj !== 'object') return [];
    var keys = [];
    if (Array.isArray(obj)) {
      if (obj.length > 0) keys = keys.concat(collectKeys(obj[0], prefix + '[0]', depth + 1));
    } else {
      Object.keys(obj).forEach(function(k) {
        keys.push(prefix + '.' + k);
        keys = keys.concat(collectKeys(obj[k], prefix + '.' + k, depth + 1));
      });
    }
    return keys;
  }

  // ── Main Run ───────────────────────────────────────────────────────────────

  window.jpRun = function() {
    var jsonStr = document.getElementById('jp-json').value.trim();
    var pathStr = document.getElementById('jp-path').value.trim();
    var jsonErrEl = document.getElementById('jp-json-err');
    var pathErrEl = document.getElementById('jp-path-err');
    var resultArea = document.getElementById('jp-result-area');
    var jsonInp = document.getElementById('jp-json');
    var pathInp = document.getElementById('jp-path');

    // Parse JSON
    var data;
    jsonErrEl.textContent = '';
    jsonInp.classList.remove('error');
    if (!jsonStr) {
      resultArea.innerHTML = '<div class="placeholder-msg">Enter JSON and a JSONPath expression to see results</div>';
      return;
    }
    try {
      data = JSON.parse(jsonStr);
    } catch (e) {
      jsonErrEl.textContent = 'JSON parse error: ' + e.message;
      jsonInp.classList.add('error');
      resultArea.innerHTML = '<div class="error-panel">Invalid JSON: ' + escHtml(e.message) + '</div>';
      return;
    }

    if (!pathStr) {
      resultArea.innerHTML = '<div class="placeholder-msg">Enter a JSONPath expression above</div>';
      return;
    }

    // Run JSONPath
    pathErrEl.textContent = '';
    pathInp.classList.remove('error');
    var results;
    try {
      results = jpEval(data, pathStr);
    } catch (e) {
      pathErrEl.textContent = 'Path error: ' + e.message;
      pathInp.classList.add('error');
      resultArea.innerHTML = '<div class="error-panel">Path error: ' + escHtml(e.message) + '</div>';
      return;
    }

    // Render results
    var count = results.length;
    var itemsHtml = results.map(function(r, i) {
      return '<div class="result-item">' +
        '<div class="item-idx">[' + i + ']</div>' +
        colorizeValue(r) +
        '</div>';
    }).join('');

    var resultJson = JSON.stringify(results, null, 2);

    resultArea.innerHTML =
      '<div class="result-panel">' +
        '<div class="result-header">' +
          '<span class="result-count"><span class="match-num">' + count + '</span> match' + (count !== 1 ? 'es' : '') + '</span>' +
          (count > 0 ? '<button class="copy-result-btn" id="jp-copy-btn" onclick="jpCopyResult()">Copy Result</button>' : '') +
        '</div>' +
        (count === 0
          ? '<div class="placeholder-msg" style="padding:16px 0;">No matches found</div>'
          : '<div class="result-items">' + itemsHtml + '</div>') +
      '</div>';

    window._jpLastResult = resultJson;
  };

  window.jpCopyResult = function() {
    if (!window._jpLastResult) return;
    navigator.clipboard.writeText(window._jpLastResult).then(function() {
      var btn = document.getElementById('jp-copy-btn');
      if (!btn) return;
      var orig = btn.textContent;
      btn.textContent = 'Copied!';
      btn.classList.add('copied');
      setTimeout(function() { btn.textContent = orig; btn.classList.remove('copied'); }, 1500);
    });
  };

  window.jpSug = function(path) {
    document.getElementById('jp-path').value = path;
    jpRun();
  };

  function escHtml(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  // Seed with sample JSON
  window.addEventListener('load', function() {
    var ta = document.getElementById('jp-json');
    if (!ta.value) {
      ta.value = JSON.stringify({
        "store": {
          "name": "BookWorld",
          "book": [
            { "title": "Sayings of the Century", "author": "Nigel Rees", "price": 8.95 },
            { "title": "Sword of Honour", "author": "Evelyn Waugh", "price": 12.99 },
            { "title": "Moby Dick", "author": "Herman Melville", "price": 8.99 },
            { "title": "The Lord of the Rings", "author": "J. R. R. Tolkien", "price": 22.99 }
          ],
          "bicycle": { "color": "red", "price": 19.95 }
        }
      }, null, 2);
    }
  });
})();
</script>

</div>

---

> Validate JSON → [JSON Validator](/tools/json-validator/)

> Find JSON paths → [JSON Path Finder](/tools/json-path-finder/)
