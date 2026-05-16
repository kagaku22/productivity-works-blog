---
title: "JSON Diff Checker"
date: 2025-05-16
description: "Free JSON diff tool. Compare two JSON objects side by side. Highlights added, removed, and changed properties with color coding. Supports nested objects and arrays."
categories: ["Free Tools"]
slug: "json-diff"
ShowToc: false
cover:
  image: "/images/covers/json-diff.png"
  alt: "JSON Diff Checker"
---

Paste two JSON objects and instantly see every added, removed, or changed key — color-coded, with full dot-notation paths to each change. No server, no sign-up, no tracking.

<div id="jd-app">
<style>
#jd-app *,
#jd-app *::before,
#jd-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#jd-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.5;
}
#jd-app .jd-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 14px;
}
#jd-app .jd-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 7px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  background: #fff;
  color: #334155;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#jd-app .jd-btn:hover { background: #f1f5f9; border-color: #94a3b8; }
#jd-app .jd-btn.primary {
  background: #6366f1;
  color: #fff;
  border-color: #6366f1;
}
#jd-app .jd-btn.primary:hover { background: #4f46e5; border-color: #4f46e5; }
#jd-app .jd-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 12px;
}
@media (max-width: 640px) {
  #jd-app .jd-panels { grid-template-columns: 1fr; }
}
#jd-app .jd-panel-label {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 5px;
}
#jd-app textarea.jd-input {
  width: 100%;
  height: 220px;
  padding: 10px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-family: "SF Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 12.5px;
  line-height: 1.6;
  color: #1e293b;
  background: #f8fafc;
  resize: vertical;
  outline: none;
  transition: border-color 0.15s;
}
#jd-app textarea.jd-input:focus { border-color: #6366f1; background: #fff; }
#jd-app textarea.jd-input.error { border-color: #ef4444; background: #fff5f5; }
#jd-app .jd-parse-error {
  font-size: 12px;
  color: #ef4444;
  margin-top: 4px;
  min-height: 16px;
}
#jd-app .jd-stats {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 14px;
}
#jd-app .jd-stat {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 5px 12px;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 600;
}
#jd-app .jd-stat.added   { background: #dcfce7; color: #15803d; }
#jd-app .jd-stat.removed { background: #fee2e2; color: #b91c1c; }
#jd-app .jd-stat.changed { background: #fef9c3; color: #92400e; }
#jd-app .jd-stat.same    { background: #f1f5f9; color: #475569; }
#jd-app .jd-stat-dot {
  width: 9px; height: 9px;
  border-radius: 50%;
  flex-shrink: 0;
}
#jd-app .jd-stat.added   .jd-stat-dot { background: #16a34a; }
#jd-app .jd-stat.removed .jd-stat-dot { background: #dc2626; }
#jd-app .jd-stat.changed .jd-stat-dot { background: #d97706; }
#jd-app .jd-stat.same    .jd-stat-dot { background: #94a3b8; }
#jd-app .jd-result-header {
  font-size: 13px;
  font-weight: 700;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 10px;
}
#jd-app .jd-tree {
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  overflow: hidden;
  background: #fff;
}
#jd-app .jd-row {
  display: flex;
  align-items: baseline;
  gap: 0;
  border-bottom: 1px solid #f1f5f9;
  font-family: "SF Mono", "Fira Code", "Cascadia Code", monospace;
  font-size: 12.5px;
  line-height: 1.7;
}
#jd-app .jd-row:last-child { border-bottom: none; }
#jd-app .jd-row.added   { background: #f0fdf4; }
#jd-app .jd-row.removed { background: #fff5f5; }
#jd-app .jd-row.changed { background: #fefce8; }
#jd-app .jd-row.context { background: #fff; }
#jd-app .jd-row-badge {
  width: 26px;
  flex-shrink: 0;
  text-align: center;
  font-weight: 700;
  font-size: 13px;
  padding: 0 4px;
  align-self: stretch;
  display: flex;
  align-items: center;
  justify-content: center;
}
#jd-app .jd-row.added   .jd-row-badge { color: #16a34a; background: #dcfce7; }
#jd-app .jd-row.removed .jd-row-badge { color: #dc2626; background: #fee2e2; }
#jd-app .jd-row.changed .jd-row-badge { color: #d97706; background: #fef9c3; }
#jd-app .jd-row.context .jd-row-badge { color: #94a3b8; background: #f8fafc; }
#jd-app .jd-row-body {
  padding: 4px 12px;
  flex: 1;
  overflow-wrap: anywhere;
}
#jd-app .jd-row-path {
  color: #6366f1;
  font-weight: 600;
}
#jd-app .jd-row-sep {
  color: #94a3b8;
  margin: 0 5px;
}
#jd-app .jd-val-old {
  text-decoration: line-through;
  color: #dc2626;
}
#jd-app .jd-val-new { color: #16a34a; }
#jd-app .jd-val-added   { color: #15803d; }
#jd-app .jd-val-removed { color: #b91c1c; }
#jd-app .jd-empty-state {
  text-align: center;
  padding: 40px 20px;
  color: #94a3b8;
  font-size: 14px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}
#jd-app .jd-identical {
  text-align: center;
  padding: 28px 20px;
  color: #16a34a;
  font-size: 15px;
  font-weight: 600;
  background: #f0fdf4;
  border-radius: 10px;
  border: 1.5px solid #bbf7d0;
}
#jd-app .jd-section-header {
  padding: 5px 12px 5px 0;
  font-size: 11.5px;
  color: #94a3b8;
  font-style: italic;
  border-bottom: 1px solid #f1f5f9;
  background: #f8fafc;
  padding-left: 38px;
}
</style>

<div class="jd-toolbar">
  <button class="jd-btn primary" id="jd-compare">&#8644; Compare</button>
  <button class="jd-btn" id="jd-swap">&#8645; Swap</button>
  <button class="jd-btn" id="jd-fmt-left">{ } Format Left</button>
  <button class="jd-btn" id="jd-fmt-right">{ } Format Right</button>
  <button class="jd-btn" id="jd-sample">Load Sample</button>
  <button class="jd-btn" id="jd-clear">Clear</button>
</div>

<div class="jd-panels">
  <div>
    <div class="jd-panel-label">Left (Original)</div>
    <textarea class="jd-input" id="jd-left" placeholder='{"name": "Alice", "age": 30}'></textarea>
    <div class="jd-parse-error" id="jd-err-left"></div>
  </div>
  <div>
    <div class="jd-panel-label">Right (Modified)</div>
    <textarea class="jd-input" id="jd-right" placeholder='{"name": "Alice", "age": 31}'></textarea>
    <div class="jd-parse-error" id="jd-err-right"></div>
  </div>
</div>

<div class="jd-stats" id="jd-stats" style="display:none;"></div>

<div id="jd-result-wrap">
  <div class="jd-empty-state">Paste JSON into both panels and click Compare.</div>
</div>

<script>
(function() {
  'use strict';

  /* ── Helpers ── */
  function esc(s) {
    return String(s)
      .replace(/&/g,'&amp;')
      .replace(/</g,'&lt;')
      .replace(/>/g,'&gt;')
      .replace(/"/g,'&quot;');
  }

  function formatVal(v) {
    if (v === null) return '<span style="color:#7c3aed">null</span>';
    if (typeof v === 'boolean') return '<span style="color:#0891b2">' + v + '</span>';
    if (typeof v === 'number') return '<span style="color:#0369a1">' + v + '</span>';
    if (typeof v === 'string') return '<span style="color:#b45309">"' + esc(v) + '"</span>';
    if (Array.isArray(v)) return '<span style="color:#64748b">[Array(' + v.length + ')]</span>';
    return '<span style="color:#64748b">{Object}</span>';
  }

  function isPrimitive(v) {
    return v === null || typeof v !== 'object';
  }

  /* ── Deep diff ── */
  // Returns array of {type, path, oldVal, newVal}
  function deepDiff(left, right, path, results) {
    results = results || [];
    path = path || '';

    const lt = typeOf(left);
    const rt = typeOf(right);

    if (lt !== rt) {
      // Type changed — treat as changed
      results.push({ type: 'changed', path: path || '(root)', oldVal: left, newVal: right });
      return results;
    }

    if (lt === 'object') {
      const allKeys = new Set([...Object.keys(left), ...Object.keys(right)]);
      for (const key of allKeys) {
        const childPath = path ? path + '.' + key : key;
        if (!Object.prototype.hasOwnProperty.call(left, key)) {
          collectAll(right[key], childPath, 'added', results);
        } else if (!Object.prototype.hasOwnProperty.call(right, key)) {
          collectAll(left[key], childPath, 'removed', results);
        } else {
          deepDiff(left[key], right[key], childPath, results);
        }
      }
    } else if (lt === 'array') {
      const maxLen = Math.max(left.length, right.length);
      for (let i = 0; i < maxLen; i++) {
        const childPath = (path || '(root)') + '[' + i + ']';
        if (i >= left.length) {
          collectAll(right[i], childPath, 'added', results);
        } else if (i >= right.length) {
          collectAll(left[i], childPath, 'removed', results);
        } else {
          deepDiff(left[i], right[i], childPath, results);
        }
      }
    } else {
      // Primitive comparison
      if (left !== right) {
        results.push({ type: 'changed', path: path || '(root)', oldVal: left, newVal: right });
      }
      // If equal — no entry (identical)
    }

    return results;
  }

  function typeOf(v) {
    if (v === null) return 'null';
    if (Array.isArray(v)) return 'array';
    return typeof v;
  }

  // Collect all keys under a subtree as added/removed
  function collectAll(node, path, type, results) {
    if (isPrimitive(node) || typeOf(node) === 'null') {
      results.push({ type: type, path: path, val: node });
      return;
    }
    if (Array.isArray(node)) {
      if (node.length === 0) {
        results.push({ type: type, path: path, val: node });
        return;
      }
      node.forEach(function(item, i) {
        collectAll(item, path + '[' + i + ']', type, results);
      });
    } else {
      const keys = Object.keys(node);
      if (keys.length === 0) {
        results.push({ type: type, path: path, val: node });
        return;
      }
      keys.forEach(function(k) {
        collectAll(node[k], path + '.' + k, type, results);
      });
    }
  }

  /* ── Render ── */
  function renderDiff(diffs) {
    if (diffs.length === 0) {
      return '<div class="jd-identical">&#10003; Objects are identical — no differences found.</div>';
    }

    let html = '<div class="jd-tree">';

    diffs.forEach(function(d) {
      if (d.type === 'added') {
        html += '<div class="jd-row added">';
        html += '<div class="jd-row-badge">+</div>';
        html += '<div class="jd-row-body">';
        html += '<span class="jd-row-path">' + esc(d.path) + '</span>';
        html += '<span class="jd-row-sep">&#8594;</span>';
        html += '<span class="jd-val-added">' + formatVal(d.val) + '</span>';
        html += '</div></div>';
      } else if (d.type === 'removed') {
        html += '<div class="jd-row removed">';
        html += '<div class="jd-row-badge">&minus;</div>';
        html += '<div class="jd-row-body">';
        html += '<span class="jd-row-path">' + esc(d.path) + '</span>';
        html += '<span class="jd-row-sep">&#8594;</span>';
        html += '<span class="jd-val-removed">' + formatVal(d.val) + '</span>';
        html += '</div></div>';
      } else if (d.type === 'changed') {
        html += '<div class="jd-row changed">';
        html += '<div class="jd-row-badge">~</div>';
        html += '<div class="jd-row-body">';
        html += '<span class="jd-row-path">' + esc(d.path) + '</span>';
        html += '<span class="jd-row-sep">:</span> ';
        html += '<span class="jd-val-old">' + formatVal(d.oldVal) + '</span>';
        html += ' <span class="jd-row-sep">&#8594;</span> ';
        html += '<span class="jd-val-new">' + formatVal(d.newVal) + '</span>';
        html += '</div></div>';
      }
    });

    html += '</div>';
    return html;
  }

  function renderStats(diffs) {
    var added = 0, removed = 0, changed = 0;
    diffs.forEach(function(d) {
      if (d.type === 'added') added++;
      else if (d.type === 'removed') removed++;
      else if (d.type === 'changed') changed++;
    });
    var total = added + removed + changed;
    return (
      '<div class="jd-stat added"><div class="jd-stat-dot"></div>' + added + ' added</div>' +
      '<div class="jd-stat removed"><div class="jd-stat-dot"></div>' + removed + ' removed</div>' +
      '<div class="jd-stat changed"><div class="jd-stat-dot"></div>' + changed + ' changed</div>' +
      '<div class="jd-stat same"><div class="jd-stat-dot"></div>' + total + ' total differences</div>'
    );
  }

  /* ── Parse helper ── */
  function tryParse(str, errEl, inputEl) {
    errEl.textContent = '';
    inputEl.classList.remove('error');
    var s = str.trim();
    if (!s) return null;
    try {
      return JSON.parse(s);
    } catch (e) {
      errEl.textContent = 'Parse error: ' + e.message;
      inputEl.classList.add('error');
      return undefined; // distinct from null (valid JSON null)
    }
  }

  /* ── DOM refs ── */
  var leftEl    = document.getElementById('jd-left');
  var rightEl   = document.getElementById('jd-right');
  var errLeft   = document.getElementById('jd-err-left');
  var errRight  = document.getElementById('jd-err-right');
  var statsEl   = document.getElementById('jd-stats');
  var resultEl  = document.getElementById('jd-result-wrap');

  /* ── Compare ── */
  function runCompare() {
    var leftParsed  = tryParse(leftEl.value,  errLeft,  leftEl);
    var rightParsed = tryParse(rightEl.value, errRight, rightEl);

    if (leftParsed === undefined || rightParsed === undefined) {
      statsEl.style.display = 'none';
      resultEl.innerHTML = '<div class="jd-empty-state">Fix the JSON parse errors above to compare.</div>';
      return;
    }
    if (leftParsed === null && rightParsed === null && !leftEl.value.trim() && !rightEl.value.trim()) {
      statsEl.style.display = 'none';
      resultEl.innerHTML = '<div class="jd-empty-state">Paste JSON into both panels and click Compare.</div>';
      return;
    }

    var diffs = deepDiff(leftParsed, rightParsed);
    statsEl.style.display = 'flex';
    statsEl.innerHTML = renderStats(diffs);
    resultEl.innerHTML = renderDiff(diffs);
  }

  /* ── Format ── */
  function formatInput(el, errEl) {
    var parsed = tryParse(el.value, errEl, el);
    if (parsed === undefined) return;
    if (parsed === null && !el.value.trim()) return;
    el.value = JSON.stringify(parsed, null, 2);
    errEl.textContent = '';
    el.classList.remove('error');
  }

  /* ── Sample JSON ── */
  var sampleLeft = {
    "user": {
      "id": 1,
      "name": "Alice Johnson",
      "email": "alice@example.com",
      "role": "admin",
      "active": true,
      "score": 95
    },
    "settings": {
      "theme": "dark",
      "notifications": true,
      "language": "en"
    },
    "tags": ["developer", "tester"]
  };

  var sampleRight = {
    "user": {
      "id": 1,
      "name": "Alice Johnson",
      "email": "alice@newdomain.com",
      "role": "editor",
      "active": false,
      "score": 98,
      "department": "Engineering"
    },
    "settings": {
      "theme": "light",
      "notifications": true,
      "language": "en",
      "timezone": "UTC"
    },
    "tags": ["developer", "reviewer", "lead"]
  };

  /* ── Event listeners ── */
  document.getElementById('jd-compare').addEventListener('click', runCompare);

  document.getElementById('jd-swap').addEventListener('click', function() {
    var tmp = leftEl.value;
    leftEl.value = rightEl.value;
    rightEl.value = tmp;
    errLeft.textContent = '';
    errRight.textContent = '';
    leftEl.classList.remove('error');
    rightEl.classList.remove('error');
  });

  document.getElementById('jd-fmt-left').addEventListener('click', function() {
    formatInput(leftEl, errLeft);
  });

  document.getElementById('jd-fmt-right').addEventListener('click', function() {
    formatInput(rightEl, errRight);
  });

  document.getElementById('jd-sample').addEventListener('click', function() {
    leftEl.value  = JSON.stringify(sampleLeft,  null, 2);
    rightEl.value = JSON.stringify(sampleRight, null, 2);
    errLeft.textContent  = '';
    errRight.textContent = '';
    leftEl.classList.remove('error');
    rightEl.classList.remove('error');
    runCompare();
  });

  document.getElementById('jd-clear').addEventListener('click', function() {
    leftEl.value  = '';
    rightEl.value = '';
    errLeft.textContent  = '';
    errRight.textContent = '';
    leftEl.classList.remove('error');
    rightEl.classList.remove('error');
    statsEl.style.display = 'none';
    resultEl.innerHTML = '<div class="jd-empty-state">Paste JSON into both panels and click Compare.</div>';
  });

  /* ── Auto-compare on input ── */
  var debTimer;
  function maybeAutoCompare() {
    clearTimeout(debTimer);
    debTimer = setTimeout(function() {
      if (leftEl.value.trim() && rightEl.value.trim()) {
        runCompare();
      }
    }, 700);
  }
  leftEl.addEventListener('input',  maybeAutoCompare);
  rightEl.addEventListener('input', maybeAutoCompare);

  /* ── Keyboard shortcut ── */
  document.addEventListener('keydown', function(e) {
    if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') {
      e.preventDefault();
      runCompare();
    }
  });
})();
</script>
</div>

---

## How It Works

The diff engine walks both JSON trees recursively. At each node it checks:

- **Object keys** — keys present only in the right are `added`; keys only in the left are `removed`; shared keys are compared recursively.
- **Array indices** — compared index-by-index; excess elements on either side are flagged.
- **Primitives** — a strict `!==` comparison detects value changes, including type coercion differences (`1` vs `"1"`).

Each change is reported with its full **dot-notation path** (e.g. `user.email`, `tags[2]`) so you can locate it instantly in the original JSON.

All processing is client-side — your JSON never leaves the browser.

---

## Color Code Reference

| Color | Symbol | Meaning |
|---|---|---|
| Green | + | Key/value exists only in the Right (added) |
| Red | − | Key/value exists only in the Left (removed) |
| Yellow | ~ | Key exists in both but the value changed |

---

## Tips

- **Format First** — use "Format Left / Right" to pretty-print minified JSON before comparing, making paths easier to read.
- **Swap** — reverse the comparison direction in one click.
- **Sample** — click "Load Sample" to see a realistic user-object diff in action.
- **Keyboard shortcut** — press `Ctrl+Enter` (or `Cmd+Enter` on Mac) to compare without reaching for the mouse.
- **Nested objects** — the tool recurses into any depth; paths like `config.database.pool.max` are reported correctly.

---

> Validate and pretty-print JSON → [JSON Formatter](/tools/json-formatter/)

> Find values in deep JSON → [JSON Path Finder](/tools/json-path-finder/)

> Compare plain text line by line → [Text Diff Checker](/tools/text-diff-checker/)
