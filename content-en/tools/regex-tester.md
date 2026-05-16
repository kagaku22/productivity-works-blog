---
title: "Regex Tester"
date: 2025-05-16
description: "Free online regex tester. Test regular expressions against sample text with real-time match highlighting, capture groups, and flags — no sign-up required."
categories: ["Free Tools"]
slug: "regex-tester"
ShowToc: false
cover:
  image: "/images/covers/regex-tester.png"
  alt: "Regex Tester"
---

Test regular expressions instantly in your browser. Paste your pattern, choose flags, and see matches highlighted in real time — no sign-up, no server, no external libraries.

<div id="rx-app">
<style>
  #rx-app *,
  #rx-app *::before,
  #rx-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

  #rx-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    font-size: 14px;
    color: #1e293b;
    max-width: 860px;
    margin: 0 auto;
  }

  #rx-app .rx-card {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 10px;
    padding: 18px 20px;
    margin-bottom: 14px;
  }
  #rx-app .rx-card-title {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: .07em;
    text-transform: uppercase;
    color: #64748b;
    margin-bottom: 10px;
  }

  /* Pattern row */
  #rx-app .rx-pattern-row {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
  }
  #rx-app .rx-slash {
    font-size: 22px;
    color: #94a3b8;
    line-height: 1;
    flex-shrink: 0;
    font-family: "Fira Mono", "Consolas", monospace;
  }
  #rx-app #rx-pattern {
    flex: 1;
    min-width: 180px;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 15px;
    padding: 9px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 7px;
    outline: none;
    transition: border-color .15s;
    background: #f8fafc;
    color: #1e293b;
  }
  #rx-app #rx-pattern:focus { border-color: #6366f1; background: #fff; }
  #rx-app #rx-pattern.rx-invalid { border-color: #ef4444; background: #fff5f5; }

  /* Flag toggles */
  #rx-app .rx-flags { display: flex; gap: 5px; flex-shrink: 0; flex-wrap: wrap; }
  #rx-app .rx-flag {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 30px;
    height: 30px;
    border-radius: 6px;
    border: 2px solid #e2e8f0;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
    color: #64748b;
    background: #f8fafc;
    transition: all .15s;
    user-select: none;
  }
  #rx-app .rx-flag:hover { border-color: #6366f1; color: #6366f1; }
  #rx-app .rx-flag.on { background: #6366f1; border-color: #6366f1; color: #fff; }

  /* Error message */
  #rx-app .rx-error-msg {
    display: none;
    margin-top: 8px;
    padding: 8px 12px;
    background: #fef2f2;
    border: 1px solid #fca5a5;
    border-radius: 6px;
    color: #b91c1c;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 12px;
  }

  /* Quick-insert buttons */
  #rx-app .rx-quick-wrap { display: flex; flex-wrap: wrap; gap: 6px; }
  #rx-app .rx-qbtn {
    padding: 5px 11px;
    font-size: 12px;
    font-weight: 600;
    border: 1.5px solid #c7d2fe;
    border-radius: 20px;
    background: #eef2ff;
    color: #4338ca;
    cursor: pointer;
    transition: all .15s;
  }
  #rx-app .rx-qbtn:hover { background: #6366f1; border-color: #6366f1; color: #fff; }

  /* Test-string textarea */
  #rx-app #rx-test {
    width: 100%;
    min-height: 110px;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    line-height: 1.65;
    padding: 10px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 7px;
    outline: none;
    resize: vertical;
    background: #f8fafc;
    color: #1e293b;
    transition: border-color .15s;
  }
  #rx-app #rx-test:focus { border-color: #6366f1; background: #fff; }

  /* Highlighted output */
  #rx-app #rx-hl {
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    line-height: 1.7;
    white-space: pre-wrap;
    word-break: break-all;
    min-height: 80px;
    padding: 10px 12px;
    border-radius: 7px;
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    color: #1e293b;
  }
  #rx-app mark.rx-m0 {
    background: #fde68a;
    border-radius: 3px;
    outline: 2px solid #f59e0b;
    outline-offset: 0;
    color: #1e293b;
  }
  #rx-app mark.rx-m1 {
    background: #a5f3fc;
    border-radius: 3px;
    outline: 2px solid #0ea5e9;
    outline-offset: 0;
    color: #1e293b;
  }

  /* Stats bar */
  #rx-app .rx-stats { display: flex; gap: 20px; flex-wrap: wrap; margin-top: 10px; }
  #rx-app .rx-stat { font-size: 12px; color: #64748b; }
  #rx-app .rx-stat strong { color: #1e293b; }

  /* Tabs */
  #rx-app .rx-tabs {
    display: flex;
    gap: 0;
    border-bottom: 2px solid #e2e8f0;
    margin-bottom: 14px;
  }
  #rx-app .rx-tab {
    padding: 7px 16px;
    font-size: 13px;
    font-weight: 600;
    color: #64748b;
    border: none;
    background: none;
    cursor: pointer;
    border-bottom: 2px solid transparent;
    margin-bottom: -2px;
    transition: all .15s;
  }
  #rx-app .rx-tab:hover { color: #6366f1; }
  #rx-app .rx-tab.on { color: #6366f1; border-bottom-color: #6366f1; }

  /* Match list */
  #rx-app .rx-match-list { list-style: none; max-height: 280px; overflow-y: auto; }
  #rx-app .rx-match-item {
    display: grid;
    grid-template-columns: 46px 1fr;
    gap: 8px;
    align-items: start;
    padding: 8px 0;
    border-bottom: 1px solid #f1f5f9;
  }
  #rx-app .rx-match-item:last-child { border-bottom: none; }
  #rx-app .rx-mi-num {
    font-size: 11px;
    font-weight: 700;
    color: #6366f1;
    background: #eef2ff;
    border-radius: 4px;
    padding: 2px 5px;
    text-align: center;
  }
  #rx-app .rx-mi-val {
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    background: #fde68a;
    border-radius: 3px;
    padding: 1px 5px;
    word-break: break-all;
    color: #1e293b;
  }
  #rx-app .rx-mi-pos { font-size: 11px; color: #94a3b8; margin-top: 3px; }
  #rx-app .rx-mi-groups { display: flex; flex-wrap: wrap; gap: 4px; margin-top: 5px; }
  #rx-app .rx-group-chip {
    font-size: 11px;
    font-family: "Fira Mono", "Consolas", monospace;
    background: #e0f2fe;
    color: #0369a1;
    border-radius: 3px;
    padding: 1px 6px;
  }
  #rx-app .rx-empty {
    text-align: center;
    color: #94a3b8;
    font-size: 13px;
    padding: 22px 0;
  }

  /* Replace panel */
  #rx-app .rx-replace-row {
    display: flex;
    gap: 8px;
    align-items: center;
    flex-wrap: wrap;
  }
  #rx-app #rx-repl-in {
    flex: 1;
    min-width: 180px;
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    padding: 8px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 7px;
    background: #f8fafc;
    outline: none;
    transition: border-color .15s;
    color: #1e293b;
  }
  #rx-app #rx-repl-in:focus { border-color: #6366f1; background: #fff; }
  #rx-app #rx-repl-out {
    font-family: "Fira Mono", "Consolas", monospace;
    font-size: 13px;
    line-height: 1.7;
    white-space: pre-wrap;
    word-break: break-all;
    padding: 10px 12px;
    border-radius: 7px;
    background: #f0fdf4;
    border: 1px solid #bbf7d0;
    min-height: 50px;
    margin-top: 10px;
    color: #1e293b;
  }
  #rx-app .rx-copy-btn {
    padding: 6px 13px;
    font-size: 12px;
    font-weight: 600;
    border: 1.5px solid #e2e8f0;
    border-radius: 6px;
    background: #f8fafc;
    color: #475569;
    cursor: pointer;
    transition: all .15s;
    flex-shrink: 0;
  }
  #rx-app .rx-copy-btn:hover { border-color: #6366f1; color: #6366f1; }

  /* Explain panel */
  #rx-app .rx-explain-list { list-style: none; }
  #rx-app .rx-explain-item {
    display: flex;
    gap: 12px;
    padding: 5px 0;
    border-bottom: 1px dashed #f1f5f9;
    font-size: 12px;
  }
  #rx-app .rx-explain-item:last-child { border: none; }
  #rx-app .rx-ex-tok {
    font-family: "Fira Mono", "Consolas", monospace;
    font-weight: 700;
    color: #6366f1;
    min-width: 96px;
    flex-shrink: 0;
  }
  #rx-app .rx-ex-desc { color: #475569; line-height: 1.5; }

  @media (max-width: 600px) {
    #rx-app .rx-pattern-row { flex-direction: column; align-items: stretch; }
    #rx-app .rx-slash { display: none; }
    #rx-app #rx-pattern { font-size: 14px; }
  }
</style>

<!-- PATTERN INPUT -->
<div class="rx-card">
  <div class="rx-card-title">Regular Expression</div>
  <div class="rx-pattern-row">
    <span class="rx-slash">/</span>
    <input id="rx-pattern" type="text" placeholder="Enter pattern…" autocomplete="off" spellcheck="false" />
    <span class="rx-slash">/</span>
    <div class="rx-flags">
      <span class="rx-flag on"  data-flag="g" title="Global — find all matches">g</span>
      <span class="rx-flag"     data-flag="i" title="Case-insensitive">i</span>
      <span class="rx-flag"     data-flag="m" title="Multiline — ^ and $ match line boundaries">m</span>
      <span class="rx-flag"     data-flag="s" title="Dotall — dot matches newline">s</span>
      <span class="rx-flag"     data-flag="u" title="Unicode mode">u</span>
    </div>
  </div>
  <div class="rx-error-msg" id="rx-err"></div>
</div>

<!-- QUICK INSERT -->
<div class="rx-card">
  <div class="rx-card-title">Quick Insert — Common Patterns</div>
  <div class="rx-quick-wrap">
    <button class="rx-qbtn" data-p="[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}">Email</button>
    <button class="rx-qbtn" data-p="https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&\/=]*)">URL</button>
    <button class="rx-qbtn" data-p="\+?[\d\s\-().]{7,20}">Phone</button>
    <button class="rx-qbtn" data-p="\b(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\b">IPv4</button>
    <button class="rx-qbtn" data-p="\b\d{4}[-\/]\d{2}[-\/]\d{2}\b">Date YYYY-MM-DD</button>
    <button class="rx-qbtn" data-p="#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})\b">Hex Color</button>
    <button class="rx-qbtn" data-p="\b\d{1,3}(?:,\d{3})*(?:\.\d+)?\b">Number</button>
    <button class="rx-qbtn" data-p="^[a-zA-Z0-9_]{3,16}$">Username</button>
    <button class="rx-qbtn" data-p="(?=.*[A-Z])(?=.*[a-z])(?=.*\d).{8,}">Strong Password</button>
    <button class="rx-qbtn" data-p="<([a-zA-Z][a-zA-Z0-9]*)\b[^>]*>[\s\S]*?<\/\1>">HTML Tag</button>
  </div>
</div>

<!-- TEST STRING -->
<div class="rx-card">
  <div class="rx-card-title">Test String</div>
  <textarea id="rx-test" spellcheck="false" placeholder="Paste or type your test string here…">Contact us at hello@example.com or support@company.org
Visit https://www.example.com or http://docs.site.io/page
Call +1 (800) 555-0123 or 020 7946 0958
Server IP: 192.168.1.1, fallback: 10.0.0.254
Today is 2025-05-16, event on 2025/12/31</textarea>
</div>

<!-- MATCH HIGHLIGHTS -->
<div class="rx-card">
  <div class="rx-card-title">Match Highlights</div>
  <div id="rx-hl"></div>
  <div class="rx-stats">
    <span class="rx-stat">Matches: <strong id="rx-count">—</strong></span>
    <span class="rx-stat">Execution: <strong id="rx-time">—</strong></span>
  </div>
</div>

<!-- BOTTOM PANELS: Match Details / Replace / Explain -->
<div class="rx-card">
  <div class="rx-tabs">
    <button class="rx-tab on"  data-tab="matches">Match Details</button>
    <button class="rx-tab"     data-tab="replace">Replace</button>
    <button class="rx-tab"     data-tab="explain">Explain</button>
  </div>

  <!-- Match Details -->
  <div id="rx-panel-matches">
    <ul class="rx-match-list" id="rx-mlist">
      <li class="rx-empty">Enter a pattern above to see match details.</li>
    </ul>
  </div>

  <!-- Replace -->
  <div id="rx-panel-replace" style="display:none">
    <div class="rx-replace-row">
      <label style="font-size:12px;color:#64748b;font-weight:600;white-space:nowrap;">Replace with:</label>
      <input id="rx-repl-in" type="text" placeholder="Replacement string — use $1, $2 for capture groups…" spellcheck="false" />
      <button class="rx-copy-btn" id="rx-copy-repl">Copy result</button>
    </div>
    <div id="rx-repl-out"></div>
  </div>

  <!-- Explain -->
  <div id="rx-panel-explain" style="display:none">
    <ul class="rx-explain-list" id="rx-exlist">
      <li class="rx-empty">Enter a pattern above to see a token-by-token explanation.</li>
    </ul>
  </div>
</div>

<script>
(function () {
  'use strict';

  /* ── State ── */
  var flagState = { g: true, i: false, m: false, s: false, u: false };
  var activeTab = 'matches';

  /* ── DOM refs ── */
  var elPat    = document.getElementById('rx-pattern');
  var elTest   = document.getElementById('rx-test');
  var elErr    = document.getElementById('rx-err');
  var elHl     = document.getElementById('rx-hl');
  var elCount  = document.getElementById('rx-count');
  var elTime   = document.getElementById('rx-time');
  var elMlist  = document.getElementById('rx-mlist');
  var elReplIn = document.getElementById('rx-repl-in');
  var elReplOut= document.getElementById('rx-repl-out');
  var elExlist = document.getElementById('rx-exlist');

  /* ── Flag toggles ── */
  document.querySelectorAll('#rx-app .rx-flag').forEach(function (el) {
    el.addEventListener('click', function () {
      var f = el.dataset.flag;
      flagState[f] = !flagState[f];
      el.classList.toggle('on', flagState[f]);
      run();
    });
  });

  /* ── Tab switching ── */
  document.querySelectorAll('#rx-app .rx-tab').forEach(function (el) {
    el.addEventListener('click', function () {
      activeTab = el.dataset.tab;
      document.querySelectorAll('#rx-app .rx-tab').forEach(function (t) {
        t.classList.toggle('on', t === el);
      });
      document.getElementById('rx-panel-matches').style.display = activeTab === 'matches' ? '' : 'none';
      document.getElementById('rx-panel-replace').style.display = activeTab === 'replace'  ? '' : 'none';
      document.getElementById('rx-panel-explain').style.display = activeTab === 'explain'  ? '' : 'none';
    });
  });

  /* ── Quick-insert ── */
  document.querySelectorAll('#rx-app .rx-qbtn').forEach(function (btn) {
    btn.addEventListener('click', function () {
      elPat.value = btn.dataset.p;
      run();
      elPat.focus();
    });
  });

  /* ── Copy result ── */
  document.getElementById('rx-copy-repl').addEventListener('click', function () {
    var txt = elReplOut.textContent;
    if (!txt) return;
    var btn = this;
    navigator.clipboard.writeText(txt).catch(function () {
      var ta = document.createElement('textarea');
      ta.value = txt;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
    });
    btn.textContent = 'Copied!';
    setTimeout(function () { btn.textContent = 'Copy result'; }, 1600);
  });

  /* ── Input listeners ── */
  elPat.addEventListener('input', run);
  elTest.addEventListener('input', run);
  elReplIn.addEventListener('input', run);

  /* ═══════════════════ CORE RUN ═══════════════════ */
  function run() {
    var rawPat  = elPat.value;
    var testStr = elTest.value;
    var fStr    = buildFlagStr();

    /* Reset error */
    elErr.style.display = 'none';
    elPat.classList.remove('rx-invalid');

    if (!rawPat) {
      elHl.textContent = testStr;
      elCount.textContent = '—';
      elTime.textContent  = '—';
      setEmpty('Enter a pattern above to see match details.');
      elReplOut.textContent = '';
      setExplain('');
      return;
    }

    /* Build regex */
    var re;
    try { re = new RegExp(rawPat, fStr); }
    catch (e) {
      elPat.classList.add('rx-invalid');
      elErr.textContent = e.message;
      elErr.style.display = 'block';
      elHl.textContent = testStr;
      elCount.textContent = 'Error';
      elTime.textContent  = '—';
      setEmpty('Invalid pattern: ' + e.message);
      elReplOut.textContent = '';
      return;
    }

    /* Find matches */
    var t0 = performance.now();
    var matches = [];
    if (flagState.g) {
      var reG = new RegExp(rawPat, fStr);
      var m;
      while ((m = reG.exec(testStr)) !== null) {
        matches.push({ val: m[0], idx: m.index, groups: Array.from(m).slice(1) });
        if (m[0].length === 0) reG.lastIndex++;
        if (matches.length >= 1000) break;
      }
    } else {
      var m1 = re.exec(testStr);
      if (m1) matches.push({ val: m1[0], idx: m1.index, groups: Array.from(m1).slice(1) });
    }
    var t1 = performance.now();

    elCount.textContent = matches.length;
    elTime.textContent  = (t1 - t0).toFixed(3) + ' ms';

    renderHighlight(testStr, matches);
    renderMatchList(matches);
    renderReplace(testStr, re);
    setExplain(rawPat);
  }

  /* ── Helpers ── */
  function buildFlagStr() {
    return Object.keys(flagState).filter(function (f) { return flagState[f]; }).join('');
  }

  function esc(s) {
    return String(s)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  /* ── Highlight renderer ── */
  function renderHighlight(str, matches) {
    if (!matches.length) { elHl.textContent = str; return; }
    var html = '', cur = 0;
    matches.forEach(function (m, i) {
      if (m.idx > cur) html += esc(str.slice(cur, m.idx));
      html += '<mark class="rx-m' + (i % 2) + '">' + esc(m.val) + '</mark>';
      cur = m.idx + m.val.length;
    });
    html += esc(str.slice(cur));
    elHl.innerHTML = html;
  }

  /* ── Match list renderer ── */
  function renderMatchList(matches) {
    if (!matches.length) { setEmpty('No matches found.'); return; }
    var html = '';
    matches.forEach(function (m, i) {
      html += '<li class="rx-match-item">';
      html += '<span class="rx-mi-num">#' + (i + 1) + '</span>';
      html += '<div>';
      html += '<div class="rx-mi-val">' + esc(m.val) + '</div>';
      html += '<div class="rx-mi-pos">index ' + m.idx + ' → ' + (m.idx + m.val.length) + '</div>';
      if (m.groups.length) {
        html += '<div class="rx-mi-groups">';
        m.groups.forEach(function (g, gi) {
          html += '<span class="rx-group-chip">$' + (gi + 1) + ': ' + esc(g === undefined ? 'undefined' : g) + '</span>';
        });
        html += '</div>';
      }
      html += '</div></li>';
    });
    elMlist.innerHTML = html;
  }

  function setEmpty(msg) {
    elMlist.innerHTML = '<li class="rx-empty">' + esc(msg) + '</li>';
  }

  /* ── Replace renderer ── */
  function renderReplace(str, re) {
    var repl = elReplIn.value;
    if (!repl && repl !== '0') { elReplOut.textContent = ''; return; }
    try { elReplOut.textContent = str.replace(re, repl); }
    catch (e) { elReplOut.textContent = ''; }
  }

  /* ══════════════════ EXPLAIN ══════════════════ */
  var TOKENS = [
    [/^\^/,                       'Start-of-string (or line with m flag) anchor'],
    [/^\$/,                       'End-of-string (or line with m flag) anchor'],
    [/^\(\?<=/,                   'Positive lookbehind assertion'],
    [/^\(\?<!/,                   'Negative lookbehind assertion'],
    [/^\(\?=/,                    'Positive lookahead assertion'],
    [/^\(\?!/,                    'Negative lookahead assertion'],
    [/^\(\?:/,                    'Non-capturing group'],
    [/^\(\?<[a-zA-Z_]\w*>/,      'Named capturing group'],
    [/^\(/,                       'Opening of a capturing group'],
    [/^\)/,                       'Closing of a group'],
    [/^\[^\]/,                    'Negated character class — match anything NOT listed'],
    [/^\[/,                       'Character class — match any one of the listed characters'],
    [/^\]/,                       'End of character class'],
    [/^\\d/,                      'Shorthand: any digit [0-9]'],
    [/^\\D/,                      'Shorthand: any non-digit'],
    [/^\\w/,                      'Shorthand: word character [a-zA-Z0-9_]'],
    [/^\\W/,                      'Shorthand: non-word character'],
    [/^\\s/,                      'Shorthand: whitespace (space, tab, newline…)'],
    [/^\\S/,                      'Shorthand: non-whitespace'],
    [/^\\b/,                      'Word boundary assertion'],
    [/^\\B/,                      'Non-word-boundary assertion'],
    [/^\\n/,                      'Literal newline character'],
    [/^\\t/,                      'Literal tab character'],
    [/^\\r/,                      'Literal carriage-return character'],
    [/^\\\\/,                     'Literal backslash'],
    [/^\\u[0-9a-fA-F]{4}/,       'Unicode code-point escape'],
    [/^\\x[0-9a-fA-F]{2}/,       'Hexadecimal character escape'],
    [/^\\([0-9]+)/,               'Backreference to capture group N'],
    [/^\\./,                      'Escaped special character — treated as literal'],
    [/^\{[0-9]+,[0-9]+\}\?/,     'Lazy quantifier: between {n} and {m} times'],
    [/^\{[0-9]+,\}\?/,           'Lazy quantifier: {n} or more times'],
    [/^\{[0-9]+\}\?/,            'Lazy quantifier: exactly {n} times'],
    [/^\{[0-9]+,[0-9]+\}/,       'Greedy quantifier: between {n} and {m} times'],
    [/^\{[0-9]+,\}/,             'Greedy quantifier: {n} or more times'],
    [/^\{[0-9]+\}/,              'Greedy quantifier: exactly {n} times'],
    [/^\*\?/,                    'Lazy quantifier: zero or more times (as few as possible)'],
    [/^\+\?/,                    'Lazy quantifier: one or more times (as few as possible)'],
    [/^\?\?/,                    'Lazy quantifier: zero or one time (prefer zero)'],
    [/^\*/,                      'Greedy quantifier: zero or more times'],
    [/^\+/,                      'Greedy quantifier: one or more times'],
    [/^\?/,                      'Greedy quantifier: zero or one time (optional)'],
    [/^\|/,                      'Alternation — match either the left or right side'],
    [/^\./,                      'Wildcard — any character except newline (unless s flag)'],
    [/^./,                       'Literal character'],
  ];

  function tokenize(pat) {
    var toks = [], rem = pat, limit = 300;
    while (rem.length && limit-- > 0) {
      var hit = false;
      for (var i = 0; i < TOKENS.length; i++) {
        var m = rem.match(TOKENS[i][0]);
        if (m) {
          toks.push({ t: m[0], d: TOKENS[i][1] });
          rem = rem.slice(m[0].length);
          hit = true;
          break;
        }
      }
      if (!hit) rem = rem.slice(1);
    }
    return toks;
  }

  function setExplain(pat) {
    if (!pat) {
      elExlist.innerHTML = '<li class="rx-empty">Enter a pattern above to see a token-by-token explanation.</li>';
      return;
    }
    var toks = tokenize(pat);
    if (!toks.length) { elExlist.innerHTML = '<li class="rx-empty">Nothing to explain.</li>'; return; }
    var html = '';
    toks.forEach(function (tk) {
      html += '<li class="rx-explain-item"><span class="rx-ex-tok">' + esc(tk.t) + '</span><span class="rx-ex-desc">' + esc(tk.d) + '</span></li>';
    });
    elExlist.innerHTML = html;
  }

  /* Initial render */
  run();
})();
</script>
</div>

---

> Quick reference → [Regex Cheatsheet](/tools/regex-cheatsheet/)
> Escape strings → [String Escape Tool](/tools/string-escape-tool/)

## Related Articles

- [Best Online Coding Bootcamps 2026: Honest Comparison by Career Goal](/posts/best-online-coding-bootcamps-2026/)
