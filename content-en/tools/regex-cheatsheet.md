---
title: "Regex Cheatsheet — Interactive Reference"
date: 2025-05-16
description: "Interactive regex cheatsheet with live testing. Character classes, quantifiers, groups, lookaheads, and common patterns. Try each example instantly."
categories: ["Free Tools"]
slug: "regex-cheatsheet"
ShowToc: false
aliases:
  - "/tools/regex-reference/"
  - "/tools/regex-guide/"
cover:
  image: "/images/covers/regex-cheatsheet.png"
  alt: "Regex Cheatsheet"
---

<div id="rxcs-app">

<style>
#rxcs-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #1a1a2e;
  color: #e0e0e0;
  padding: 24px;
  border-radius: 12px;
  max-width: 960px;
  margin: 0 auto;
  box-sizing: border-box;
}

#rxcs-app * {
  box-sizing: border-box;
}

#rxcs-app h2 {
  color: #00ff88;
  margin: 0 0 6px 0;
  font-size: 1.35rem;
  letter-spacing: 0.4px;
}

#rxcs-app h3 {
  color: #00cc70;
  font-size: 0.95rem;
  margin: 20px 0 10px 0;
  text-transform: uppercase;
  letter-spacing: 1px;
  border-bottom: 1px solid #2a2a4a;
  padding-bottom: 6px;
}

#rxcs-app .rxcs-subtitle {
  color: #606080;
  font-size: 0.82rem;
  margin-bottom: 20px;
}

/* ── Test Area ── */
#rxcs-app .rxcs-tester {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 10px;
  padding: 18px;
  margin-bottom: 24px;
}

#rxcs-app .rxcs-tester-title {
  color: #a0a0c0;
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.9px;
  font-weight: 700;
  margin-bottom: 12px;
}

#rxcs-app .rxcs-row {
  display: flex;
  gap: 8px;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 10px;
}

#rxcs-app .rxcs-pattern-wrap {
  display: flex;
  align-items: center;
  background: #16162a;
  border: 1px solid #2a2a4a;
  border-radius: 7px;
  flex: 1;
  min-width: 180px;
  transition: border-color 0.2s;
}

#rxcs-app .rxcs-pattern-wrap:focus-within {
  border-color: #00ff88;
}

#rxcs-app .rxcs-slash {
  color: #00ff88;
  font-size: 1.2rem;
  padding: 0 7px;
  font-family: monospace;
  user-select: none;
}

#rxcs-app .rxcs-pattern-input {
  background: transparent;
  border: none;
  outline: none;
  color: #00ff88;
  font-family: 'Courier New', monospace;
  font-size: 0.95rem;
  flex: 1;
  padding: 9px 2px;
  width: 0;
}

#rxcs-app .rxcs-flags-wrap {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: center;
}

#rxcs-app .rxcs-flag-label {
  display: flex;
  align-items: center;
  gap: 3px;
  cursor: pointer;
  font-size: 0.82rem;
  color: #9090b0;
  user-select: none;
}

#rxcs-app .rxcs-flag-label input[type="checkbox"] {
  accent-color: #00ff88;
  width: 13px;
  height: 13px;
  cursor: pointer;
}

#rxcs-app .rxcs-flag-key {
  font-family: monospace;
  color: #00ff88;
  font-weight: 700;
}

#rxcs-app .rxcs-teststr {
  width: 100%;
  background: #16162a;
  border: 1px solid #2a2a4a;
  color: #e0e0e0;
  padding: 10px 12px;
  border-radius: 7px;
  font-family: 'Courier New', monospace;
  font-size: 0.88rem;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  line-height: 1.5;
}

#rxcs-app .rxcs-teststr:focus {
  border-color: #00ff88;
}

#rxcs-app .rxcs-stats {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 8px 0;
  flex-wrap: wrap;
}

#rxcs-app .rxcs-badge {
  background: #00ff8820;
  border: 1px solid #00ff8840;
  color: #00ff88;
  padding: 3px 11px;
  border-radius: 20px;
  font-size: 0.78rem;
  font-weight: 700;
}

#rxcs-app .rxcs-badge.no-match {
  background: #ff444420;
  border-color: #ff444440;
  color: #ff8888;
}

#rxcs-app .rxcs-badge.error {
  background: #ff220020;
  border-color: #ff220040;
  color: #ff6666;
}

#rxcs-app .rxcs-display {
  background: #16162a;
  border: 1px solid #2a2a4a;
  border-radius: 7px;
  padding: 10px 12px;
  font-family: 'Courier New', monospace;
  font-size: 0.88rem;
  line-height: 1.6;
  min-height: 60px;
  white-space: pre-wrap;
  word-break: break-all;
  color: #c0c0e0;
  margin-top: 6px;
}

#rxcs-app .rxcs-hl {
  background: #00ff8840;
  border-bottom: 2px solid #00ff88;
  border-radius: 2px;
  color: #00ff88;
}

#rxcs-app .rxcs-hl-alt {
  background: #ff88ff30;
  border-bottom: 2px solid #ff88ff;
  border-radius: 2px;
  color: #ff88ff;
}

/* ── Search bar ── */
#rxcs-app .rxcs-search-wrap {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 18px;
}

#rxcs-app .rxcs-search {
  flex: 1;
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  color: #e0e0e0;
  padding: 9px 13px;
  border-radius: 7px;
  font-size: 0.88rem;
  outline: none;
  transition: border-color 0.2s;
}

#rxcs-app .rxcs-search:focus {
  border-color: #00ff88;
}

#rxcs-app .rxcs-search::placeholder {
  color: #404060;
}

#rxcs-app .rxcs-search-clear {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  color: #808090;
  padding: 8px 13px;
  border-radius: 7px;
  cursor: pointer;
  font-size: 0.82rem;
  transition: all 0.2s;
}

#rxcs-app .rxcs-search-clear:hover {
  border-color: #00ff88;
  color: #00ff88;
}

/* ── Reference Table ── */
#rxcs-app .rxcs-table-wrap {
  overflow-x: auto;
  margin-bottom: 6px;
  border-radius: 8px;
  border: 1px solid #2a2a4a;
}

#rxcs-app .rxcs-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.85rem;
  min-width: 600px;
}

#rxcs-app .rxcs-table thead tr {
  background: #0d0d1a;
}

#rxcs-app .rxcs-table thead th {
  color: #606080;
  font-size: 0.74rem;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  padding: 9px 12px;
  text-align: left;
  font-weight: 700;
  border-bottom: 1px solid #2a2a4a;
}

#rxcs-app .rxcs-table tbody tr {
  border-bottom: 1px solid #1a1a30;
  transition: background 0.15s;
}

#rxcs-app .rxcs-table tbody tr:last-child {
  border-bottom: none;
}

#rxcs-app .rxcs-table tbody tr:hover {
  background: #1e1e38;
}

#rxcs-app .rxcs-table tbody tr.rxcs-hidden {
  display: none;
}

#rxcs-app .rxcs-table td {
  padding: 9px 12px;
  vertical-align: middle;
}

#rxcs-app .rxcs-token {
  font-family: 'Courier New', monospace;
  color: #00ff88;
  font-weight: 700;
  font-size: 0.9rem;
  white-space: nowrap;
  display: flex;
  align-items: center;
  gap: 6px;
}

#rxcs-app .rxcs-desc {
  color: #c0c0d8;
  line-height: 1.4;
}

#rxcs-app .rxcs-example {
  font-family: 'Courier New', monospace;
  color: #ffe066;
  font-size: 0.82rem;
  white-space: nowrap;
}

#rxcs-app .rxcs-actions {
  display: flex;
  gap: 5px;
  align-items: center;
  white-space: nowrap;
}

#rxcs-app .rxcs-btn-try {
  background: #00ff8818;
  border: 1px solid #00ff8840;
  color: #00ff88;
  padding: 4px 10px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 0.75rem;
  font-weight: 600;
  transition: all 0.18s;
}

#rxcs-app .rxcs-btn-try:hover {
  background: #00ff8830;
  border-color: #00ff88;
}

#rxcs-app .rxcs-btn-copy {
  background: #1a1a3a;
  border: 1px solid #2a2a4a;
  color: #8080a0;
  padding: 4px 9px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 0.75rem;
  transition: all 0.18s;
}

#rxcs-app .rxcs-btn-copy:hover {
  border-color: #5050a0;
  color: #c0c0e0;
}

#rxcs-app .rxcs-btn-copy.copied {
  border-color: #00ff88;
  color: #00ff88;
}

/* ── Section headers ── */
#rxcs-app .rxcs-section-header {
  background: #0d0d1a;
}

#rxcs-app .rxcs-section-header td {
  color: #00cc70;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  padding: 7px 12px;
  border-bottom: 1px solid #2a2a4a;
}

/* ── No results ── */
#rxcs-app .rxcs-no-results {
  text-align: center;
  color: #404060;
  padding: 28px;
  font-size: 0.88rem;
  display: none;
}

#rxcs-app .rxcs-no-results.visible {
  display: block;
}

/* ── Recipes ── */
#rxcs-app .rxcs-recipes {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 10px;
  margin-top: 8px;
}

#rxcs-app .rxcs-recipe-card {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 8px;
  padding: 13px 14px;
  transition: border-color 0.2s;
}

#rxcs-app .rxcs-recipe-card:hover {
  border-color: #3a3a6a;
}

#rxcs-app .rxcs-recipe-name {
  color: #e0e0ff;
  font-size: 0.88rem;
  font-weight: 700;
  margin-bottom: 5px;
}

#rxcs-app .rxcs-recipe-pat {
  font-family: 'Courier New', monospace;
  color: #00ff88;
  font-size: 0.78rem;
  word-break: break-all;
  margin-bottom: 7px;
  background: #16162a;
  padding: 5px 8px;
  border-radius: 5px;
  display: block;
}

#rxcs-app .rxcs-recipe-desc {
  color: #7070a0;
  font-size: 0.78rem;
  margin-bottom: 9px;
  line-height: 1.4;
}

#rxcs-app .rxcs-recipe-btns {
  display: flex;
  gap: 6px;
}

/* ── Responsive ── */
@media (max-width: 640px) {
  #rxcs-app {
    padding: 14px;
  }
  #rxcs-app .rxcs-table {
    font-size: 0.8rem;
    min-width: 480px;
  }
  #rxcs-app .rxcs-recipes {
    grid-template-columns: 1fr;
  }
  #rxcs-app .rxcs-flags-wrap {
    gap: 7px;
  }
}
</style>

<h2>Regex Interactive Cheatsheet</h2>
<p class="rxcs-subtitle">Click "Try it" on any row to load the pattern into the live tester below.</p>

<!-- ── LIVE TESTER ── -->
<div class="rxcs-tester">
  <div class="rxcs-tester-title">Live Tester</div>
  <div class="rxcs-row">
    <div class="rxcs-pattern-wrap">
      <span class="rxcs-slash">/</span>
      <input class="rxcs-pattern-input" id="rxcs-pattern" type="text" placeholder="pattern..." autocomplete="off" spellcheck="false" />
      <span class="rxcs-slash">/</span>
    </div>
    <div class="rxcs-flags-wrap">
      <label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fg" checked /><span class="rxcs-flag-key">g</span> global</label>
      <label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fi" /><span class="rxcs-flag-key">i</span> case-insensitive</label>
      <label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fm" /><span class="rxcs-flag-key">m</span> multiline</label>
      <label class="rxcs-flag-label"><input type="checkbox" id="rxcs-fs" /><span class="rxcs-flag-key">s</span> dotAll</label>
    </div>
  </div>
  <textarea class="rxcs-teststr" id="rxcs-teststr" rows="3" placeholder="Enter a test string here — then click 'Try it' on any row above..."></textarea>
  <div class="rxcs-stats">
    <span class="rxcs-badge no-match" id="rxcs-badge">No matches</span>
    <span style="color:#404060;font-size:0.78rem;" id="rxcs-expr"></span>
  </div>
  <div class="rxcs-display" id="rxcs-display">Highlighted matches appear here</div>
</div>

<!-- ── SEARCH ── -->
<div class="rxcs-search-wrap">
  <input class="rxcs-search" id="rxcs-search" type="text" placeholder="Filter cheatsheet — e.g. digit, anchor, group..." />
  <button class="rxcs-search-clear" id="rxcs-search-clear">Clear</button>
</div>

<div class="rxcs-no-results" id="rxcs-no-results">No entries match your search.</div>

<!-- ── REFERENCE TABLE ── -->
<div class="rxcs-table-wrap">
<table class="rxcs-table" id="rxcs-table">
<thead>
<tr>
  <th style="width:120px">Pattern</th>
  <th>Description</th>
  <th style="width:160px">Example</th>
  <th style="width:110px">Actions</th>
</tr>
</thead>
<tbody id="rxcs-tbody">

<!-- CHARACTER CLASSES -->
<tr class="rxcs-section-header" data-section="character-classes"><td colspan="4">Character Classes</td></tr>
<tr data-cat="character-classes" data-keywords="dot any character">
  <td><div class="rxcs-token">.</div></td>
  <td class="rxcs-desc">Any character except newline</td>
  <td class="rxcs-example">c.t → "cat", "cut", "c3t"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('c.t','The cat cut c3t')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'.')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="digit number 0-9">
  <td><div class="rxcs-token">\d</div></td>
  <td class="rxcs-desc">Any digit [0-9]</td>
  <td class="rxcs-example">\d+ → "42", "100"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+','Room 42, Floor 100, Gate 7')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\d')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="non-digit letter">
  <td><div class="rxcs-token">\D</div></td>
  <td class="rxcs-desc">Any non-digit character</td>
  <td class="rxcs-example">\D+ → "abc ", " xyz"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\D+','abc 123 xyz 456')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\D')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="word alphanumeric underscore">
  <td><div class="rxcs-token">\w</div></td>
  <td class="rxcs-desc">Word character [a-zA-Z0-9_]</td>
  <td class="rxcs-example">\w+ → "hello", "world_2"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\w+','hello world_2 foo-bar')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\w')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="non-word special punctuation">
  <td><div class="rxcs-token">\W</div></td>
  <td class="rxcs-desc">Non-word character</td>
  <td class="rxcs-example">\W → " ", "-", "@"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\W+','hello world-2 foo@bar')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\W')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="whitespace space tab newline">
  <td><div class="rxcs-token">\s</div></td>
  <td class="rxcs-desc">Whitespace (space, tab, newline…)</td>
  <td class="rxcs-example">\s+ → gap between words</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\s+','hello   world\ttab\nnewline')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\s')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="non-whitespace visible">
  <td><div class="rxcs-token">\S</div></td>
  <td class="rxcs-desc">Non-whitespace character</td>
  <td class="rxcs-example">\S+ → "hello", "world"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\S+','hello   world  here')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\S')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="tab horizontal">
  <td><div class="rxcs-token">\t</div></td>
  <td class="rxcs-desc">Horizontal tab character</td>
  <td class="rxcs-example">\t → tab in TSV data</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\t','col1\tcol2\tcol3')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\t')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="newline line break">
  <td><div class="rxcs-token">\n</div></td>
  <td class="rxcs-desc">Newline character</td>
  <td class="rxcs-example">\n → line break</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\n','line1\nline2\nline3')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\n')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="character class set bracket range">
  <td><div class="rxcs-token">[abc]</div></td>
  <td class="rxcs-desc">Character class — matches a, b, or c</td>
  <td class="rxcs-example">[aeiou] → vowels</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('[aeiou]','the quick brown fox')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[abc]')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="negated character class not except">
  <td><div class="rxcs-token">[^abc]</div></td>
  <td class="rxcs-desc">Negated class — any char except a, b, c</td>
  <td class="rxcs-example">[^aeiou\s] → consonants</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('[^aeiou\\s]','the quick brown fox')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[^abc]')">Copy</button></td>
</tr>
<tr data-cat="character-classes" data-keywords="range character class a-z A-Z 0-9">
  <td><div class="rxcs-token">[a-z]</div></td>
  <td class="rxcs-desc">Character range (a through z)</td>
  <td class="rxcs-example">[a-zA-Z]+ → words</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('[a-zA-Z]+','hello 123 WORLD 456 foo')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[a-z]')">Copy</button></td>
</tr>

<!-- QUANTIFIERS -->
<tr class="rxcs-section-header" data-section="quantifiers"><td colspan="4">Quantifiers</td></tr>
<tr data-cat="quantifiers" data-keywords="star zero or more greedy">
  <td><div class="rxcs-token">*</div></td>
  <td class="rxcs-desc">0 or more (greedy)</td>
  <td class="rxcs-example">ab* → "a", "ab", "abbb"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('ab*','a ab abb abbb b')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'*')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="plus one or more greedy">
  <td><div class="rxcs-token">+</div></td>
  <td class="rxcs-desc">1 or more (greedy)</td>
  <td class="rxcs-example">ab+ → "ab", "abbb" (not "a")</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('ab+','a ab abb abbb b')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'+')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="question mark optional zero one">
  <td><div class="rxcs-token">?</div></td>
  <td class="rxcs-desc">0 or 1 — makes preceding token optional</td>
  <td class="rxcs-example">colou?r → "color", "colour"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('colou?r','color colour colors colours')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'?')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="exact count n times braces">
  <td><div class="rxcs-token">{n}</div></td>
  <td class="rxcs-desc">Exactly n occurrences</td>
  <td class="rxcs-example">\d{4} → "2025", "1234"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d{4}','Year 2025, PIN 9876, code 12')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'{n}')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="range count min max braces between">
  <td><div class="rxcs-token">{n,m}</div></td>
  <td class="rxcs-desc">Between n and m occurrences</td>
  <td class="rxcs-example">\d{2,4} → "12", "123", "1234"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d{2,4}','1 12 123 1234 12345')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'{n,m}')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="min count at least n or more braces">
  <td><div class="rxcs-token">{n,}</div></td>
  <td class="rxcs-desc">n or more occurrences</td>
  <td class="rxcs-example">\d{3,} → "123", "12345"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d{3,}','1 12 123 12345 1234567')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'{n,}')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="lazy non-greedy minimal star question">
  <td><div class="rxcs-token">*?</div></td>
  <td class="rxcs-desc">0 or more (lazy — shortest match)</td>
  <td class="rxcs-example">&lt;.*?&gt; → each HTML tag</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('<.*?>','<b>bold</b> and <i>italic</i>')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'*?')">Copy</button></td>
</tr>
<tr data-cat="quantifiers" data-keywords="lazy non-greedy minimal plus question">
  <td><div class="rxcs-token">+?</div></td>
  <td class="rxcs-desc">1 or more (lazy — shortest match)</td>
  <td class="rxcs-example">".+?" → quoted strings</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\".+?\"','\"hello\" and \"world\" together')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'+?')">Copy</button></td>
</tr>

<!-- ANCHORS -->
<tr class="rxcs-section-header" data-section="anchors"><td colspan="4">Anchors &amp; Boundaries</td></tr>
<tr data-cat="anchors" data-keywords="caret start beginning line string">
  <td><div class="rxcs-token">^</div></td>
  <td class="rxcs-desc">Start of string (or line with m flag)</td>
  <td class="rxcs-example">^\d+ → leading digits</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('^\\d+','42 apples\n100 oranges\nno digits')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'^')">Copy</button></td>
</tr>
<tr data-cat="anchors" data-keywords="dollar end line string">
  <td><div class="rxcs-token">$</div></td>
  <td class="rxcs-desc">End of string (or line with m flag)</td>
  <td class="rxcs-example">\d+$ → trailing digits</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+$','item 42\nno number\nroom 100')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'$')">Copy</button></td>
</tr>
<tr data-cat="anchors" data-keywords="word boundary beginning end word">
  <td><div class="rxcs-token">\b</div></td>
  <td class="rxcs-desc">Word boundary (between word and non-word char)</td>
  <td class="rxcs-example">\bcat\b → "cat" not "catch"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\bcat\\b','cat catch catfish a cat sat')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\b')">Copy</button></td>
</tr>
<tr data-cat="anchors" data-keywords="non-word boundary inside">
  <td><div class="rxcs-token">\B</div></td>
  <td class="rxcs-desc">Non-word boundary (inside a word)</td>
  <td class="rxcs-example">\Bcat\B → "cat" in "concatenate"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\Bcat\\B','cat concatenate scatter')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\B')">Copy</button></td>
</tr>

<!-- GROUPS -->
<tr class="rxcs-section-header" data-section="groups"><td colspan="4">Groups &amp; Alternation</td></tr>
<tr data-cat="groups" data-keywords="capture group parentheses backreference">
  <td><div class="rxcs-token">(abc)</div></td>
  <td class="rxcs-desc">Capture group — captures matched text</td>
  <td class="rxcs-example">(\d{4})-(\d{2}) → year, month</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(\\d{4})-(\\d{2})','Date: 2025-05 and 2024-12')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(abc)')">Copy</button></td>
</tr>
<tr data-cat="groups" data-keywords="non-capturing group no capture parentheses">
  <td><div class="rxcs-token">(?:abc)</div></td>
  <td class="rxcs-desc">Non-capturing group — groups without capturing</td>
  <td class="rxcs-example">(?:foo|bar)baz → "foobaz"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?:foo|bar)baz','foobaz barbaz quxbaz')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?:abc)')">Copy</button></td>
</tr>
<tr data-cat="groups" data-keywords="named capture group name angle brackets">
  <td><div class="rxcs-token">(?&lt;name&gt;)</div></td>
  <td class="rxcs-desc">Named capture group</td>
  <td class="rxcs-example">(?&lt;yr&gt;\d{4}) → group "yr"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?<yr>\\d{4})-(?<mo>\\d{2})','2025-05, 2024-12')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?<name>)')">Copy</button></td>
</tr>
<tr data-cat="groups" data-keywords="alternation or pipe either">
  <td><div class="rxcs-token">a|b</div></td>
  <td class="rxcs-desc">Alternation — matches a or b</td>
  <td class="rxcs-example">cat|dog → "cat" or "dog"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('cat|dog','I have a cat and a dog')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'a|b')">Copy</button></td>
</tr>
<tr data-cat="groups" data-keywords="backreference group reference back">
  <td><div class="rxcs-token">\1</div></td>
  <td class="rxcs-desc">Backreference to capture group 1</td>
  <td class="rxcs-example">(\w+) \1 → repeated words</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(\\w+) \\1','the the cat sat sat on the mat mat')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\1')">Copy</button></td>
</tr>

<!-- LOOKAHEAD / LOOKBEHIND -->
<tr class="rxcs-section-header" data-section="lookahead"><td colspan="4">Lookahead &amp; Lookbehind</td></tr>
<tr data-cat="lookahead" data-keywords="positive lookahead followed by assert">
  <td><div class="rxcs-token">(?=abc)</div></td>
  <td class="rxcs-desc">Positive lookahead — followed by abc</td>
  <td class="rxcs-example">\d+(?= USD) → price before " USD"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+(?= USD)','100 USD 50 EUR 200 USD')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?=abc)')">Copy</button></td>
</tr>
<tr data-cat="lookahead" data-keywords="negative lookahead not followed assert">
  <td><div class="rxcs-token">(?!abc)</div></td>
  <td class="rxcs-desc">Negative lookahead — NOT followed by abc</td>
  <td class="rxcs-example">\d+(?! USD) → numbers not before USD</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+(?! USD)','100 USD 50 EUR 200 USD')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?!abc)')">Copy</button></td>
</tr>
<tr data-cat="lookahead" data-keywords="positive lookbehind preceded by assert behind">
  <td><div class="rxcs-token">(?&lt;=abc)</div></td>
  <td class="rxcs-desc">Positive lookbehind — preceded by abc</td>
  <td class="rxcs-example">(?&lt;=\$)\d+ → digits after $</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?<=\\$)\\d+','$100 €200 $350 ¥400')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?<=abc)')">Copy</button></td>
</tr>
<tr data-cat="lookahead" data-keywords="negative lookbehind not preceded assert behind">
  <td><div class="rxcs-token">(?&lt;!abc)</div></td>
  <td class="rxcs-desc">Negative lookbehind — NOT preceded by abc</td>
  <td class="rxcs-example">(?&lt;!\$)\d+ → digits not after $</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('(?<!\\$)\\d+','$100 €200 $350 ref:456')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?<!abc)')">Copy</button></td>
</tr>

<!-- FLAGS -->
<tr class="rxcs-section-header" data-section="flags"><td colspan="4">Flags (Modifiers)</td></tr>
<tr data-cat="flags" data-keywords="global all matches g flag">
  <td><div class="rxcs-token">g</div></td>
  <td class="rxcs-desc">Global — find all matches (not just first)</td>
  <td class="rxcs-example">/\d+/g → all numbers</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\d+','a1 b22 c333 d4444')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'g')">Copy</button></td>
</tr>
<tr data-cat="flags" data-keywords="case insensitive ignore upper lower i flag">
  <td><div class="rxcs-token">i</div></td>
  <td class="rxcs-desc">Case-insensitive matching</td>
  <td class="rxcs-example">/hello/i → "Hello", "HELLO"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('hello','Hello HELLO hello hElLo')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'i')">Copy</button></td>
</tr>
<tr data-cat="flags" data-keywords="multiline m flag caret dollar line">
  <td><div class="rxcs-token">m</div></td>
  <td class="rxcs-desc">Multiline — ^ and $ match each line start/end</td>
  <td class="rxcs-example">^\d+/m → leading numbers per line</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('^\\w+','first line\nsecond line\nthird line')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'m')">Copy</button></td>
</tr>
<tr data-cat="flags" data-keywords="dotall s flag dot newline all">
  <td><div class="rxcs-token">s</div></td>
  <td class="rxcs-desc">dotAll — dot (.) matches newlines too</td>
  <td class="rxcs-example">/.+/s → matches across lines</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('start.+end','start\nmiddle\nend')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'s')">Copy</button></td>
</tr>
<tr data-cat="flags" data-keywords="unicode u flag emoji surrogate">
  <td><div class="rxcs-token">u</div></td>
  <td class="rxcs-desc">Unicode — enables full Unicode matching</td>
  <td class="rxcs-example">/\p{L}+/u → Unicode letters</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\p{L}+','Hello café naïve')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'u')">Copy</button></td>
</tr>

<!-- ESCAPE -->
<tr class="rxcs-section-header" data-section="escape"><td colspan="4">Escaping Special Characters</td></tr>
<tr data-cat="escape" data-keywords="escape backslash literal dot period">
  <td><div class="rxcs-token">\.</div></td>
  <td class="rxcs-desc">Literal dot (escape special char with \)</td>
  <td class="rxcs-example">\. → "3.14" (only the dot)</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\.','3.14 and 2.71 not 314')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\.')">Copy</button></td>
</tr>
<tr data-cat="escape" data-keywords="escape special characters metacharacters literal">
  <td><div class="rxcs-token">\( \) \[ \]</div></td>
  <td class="rxcs-desc">Literal parentheses / brackets</td>
  <td class="rxcs-example">\(\d+\) → "(42)"</td>
  <td class="rxcs-actions"><button class="rxcs-btn-try" onclick="rxcsTry('\\(\\d+\\)','Call (800) or (555)-1234')">Try it</button><button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\(\\)')">Copy</button></td>
</tr>

</tbody>
</table>
</div>

<!-- ── COMMON RECIPES ── -->
<h3>Common Regex Recipes</h3>
<div class="rxcs-recipes" id="rxcs-recipes">

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">Email Address</div>
    <code class="rxcs-recipe-pat">[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}</code>
    <div class="rxcs-recipe-desc">Matches standard email addresses including subdomains and plus addressing.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}','user@example.com, name+tag@sub.domain.org, invalid@, @nouser.com')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">HTTP/HTTPS URL</div>
    <code class="rxcs-recipe-pat">https?:\/\/(?:www\.)?[-\w]+(?:\.[-\w]+)+[^\s]*</code>
    <div class="rxcs-recipe-desc">Matches http and https URLs with optional www and path/query.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('https?:\\/\\/(?:www\\.)?[-\\w]+(?:\\.[-\\w]+)+[^\\s]*','https://example.com, http://www.site.org/path?q=1, ftp://not-matched')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'https?:\\/\\/(?:www\\.)?[-\\w]+(?:\\.[-\\w]+)+[^\\s]*')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">US Phone Number</div>
    <code class="rxcs-recipe-pat">(?:\+1[\s\-]?)?\(?\d{3}\)?[\s\-]?\d{3}[\s\-]?\d{4}</code>
    <div class="rxcs-recipe-desc">Matches US phone numbers in various common formats.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('(?:\\+1[\\s\\-]?)?\\(?\\d{3}\\)?[\\s\\-]?\\d{3}[\\s\\-]?\\d{4}','(555) 123-4567, 555-987-6543, +1 800 555 0100')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?:\\+1[\\s\\-]?)?\\(?\\d{3}\\)?[\\s\\-]?\\d{3}[\\s\\-]?\\d{4}')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">ISO Date (YYYY-MM-DD)</div>
    <code class="rxcs-recipe-pat">\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\d|3[01])</code>
    <div class="rxcs-recipe-desc">Strictly validates ISO 8601 dates including month/day range checks.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('\\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\\d|3[01])','2025-05-16, 2024-12-31, 2025-13-01 (invalid), 2025-00-15 (invalid)')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\\d|3[01])')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">IPv4 Address</div>
    <code class="rxcs-recipe-pat">\b(?:(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d\d?)\b</code>
    <div class="rxcs-recipe-desc">Validates IPv4 addresses including boundary checks (0–255 per octet).</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('\\b(?:(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\.){3}(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\b','192.168.1.1, 10.0.0.255, 256.1.1.1 (invalid), 192.168.1')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\b(?:(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\.){3}(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\b')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">Hex Color Code</div>
    <code class="rxcs-recipe-pat">#(?:[0-9a-fA-F]{3}){1,2}\b</code>
    <div class="rxcs-recipe-desc">Matches 3-digit and 6-digit hex color codes prefixed with #.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('#(?:[0-9a-fA-F]{3}){1,2}\\b','#fff, #1a1a2e, #00FF88, #GGGGGG (invalid)')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'#(?:[0-9a-fA-F]{3}){1,2}\\b')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">US ZIP Code</div>
    <code class="rxcs-recipe-pat">\b\d{5}(?:-\d{4})?\b</code>
    <div class="rxcs-recipe-desc">Matches 5-digit ZIP codes and optional ZIP+4 format.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('\\b\\d{5}(?:-\\d{4})?\\b','90210, 10001-1234, 60601, 1234 (invalid)')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'\\b\\d{5}(?:-\\d{4})?\\b')">Copy</button>
    </div>
  </div>

  <div class="rxcs-recipe-card">
    <div class="rxcs-recipe-name">Strong Password</div>
    <code class="rxcs-recipe-pat">(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*]).{8,}</code>
    <div class="rxcs-recipe-desc">Requires at least one lowercase, uppercase, digit, and special character. Min 8 chars.</div>
    <div class="rxcs-recipe-btns">
      <button class="rxcs-btn-try" onclick="rxcsTry('(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*]).{8,}','StrongP@ss1, weakpass, NoSpecial1A, Short@1A')">Try it</button>
      <button class="rxcs-btn-copy" onclick="rxcsCopy(this,'(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*]).{8,}')">Copy</button>
    </div>
  </div>

</div>

<script>
(function() {
  var patEl   = document.getElementById('rxcs-pattern');
  var testEl  = document.getElementById('rxcs-teststr');
  var dispEl  = document.getElementById('rxcs-display');
  var badgeEl = document.getElementById('rxcs-badge');
  var exprEl  = document.getElementById('rxcs-expr');
  var searchEl = document.getElementById('rxcs-search');
  var clearEl  = document.getElementById('rxcs-search-clear');
  var noResEl  = document.getElementById('rxcs-no-results');
  var tbody    = document.getElementById('rxcs-tbody');

  var flagEls = {
    g: document.getElementById('rxcs-fg'),
    i: document.getElementById('rxcs-fi'),
    m: document.getElementById('rxcs-fm'),
    s: document.getElementById('rxcs-fs')
  };

  function getFlags() {
    return Object.keys(flagEls).filter(function(k){ return flagEls[k].checked; }).join('');
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function run() {
    var pat  = patEl.value.trim();
    var test = testEl.value;
    var flags = getFlags();

    exprEl.textContent = pat ? ('/' + pat + '/' + flags) : '';

    if (!pat || !test) {
      badgeEl.textContent = pat ? 'Enter a test string' : 'Enter a pattern';
      badgeEl.className = 'rxcs-badge no-match';
      dispEl.textContent = test || 'Highlighted matches appear here';
      return;
    }

    var re;
    try {
      var gFlags = flags.indexOf('g') === -1 ? flags + 'g' : flags;
      re = new RegExp(pat, gFlags);
    } catch(e) {
      badgeEl.textContent = 'Invalid regex';
      badgeEl.className = 'rxcs-badge error';
      dispEl.textContent = test;
      return;
    }

    var matches = [];
    var m;
    re.lastIndex = 0;
    while ((m = re.exec(test)) !== null) {
      matches.push({ index: m.index, len: m[0].length, val: m[0] });
      if (m[0].length === 0) re.lastIndex++;
      if (matches.length > 500) break;
    }

    var cnt = matches.length;
    badgeEl.textContent = cnt === 0 ? 'No matches' : (cnt === 1 ? '1 match' : cnt + ' matches');
    badgeEl.className = 'rxcs-badge' + (cnt === 0 ? ' no-match' : '');

    if (cnt === 0) {
      dispEl.textContent = test;
      return;
    }

    var parts = [];
    var last = 0;
    matches.forEach(function(match, i) {
      if (match.index > last) {
        parts.push('<span>' + escHtml(test.slice(last, match.index)) + '</span>');
      }
      var cls = i % 2 === 0 ? 'rxcs-hl' : 'rxcs-hl-alt';
      parts.push('<span class="' + cls + '">' + escHtml(match.val) + '</span>');
      last = match.index + match.len;
    });
    if (last < test.length) {
      parts.push('<span>' + escHtml(test.slice(last)) + '</span>');
    }
    dispEl.innerHTML = parts.join('');
  }

  // Search / filter
  function applySearch() {
    var q = searchEl.value.trim().toLowerCase();
    var rows = tbody.querySelectorAll('tr[data-cat]');
    var sections = tbody.querySelectorAll('tr.rxcs-section-header');
    var visibleBySection = {};

    rows.forEach(function(row) {
      var kw   = (row.getAttribute('data-keywords') || '').toLowerCase();
      var cat  = (row.getAttribute('data-cat') || '').toLowerCase();
      var text = row.textContent.toLowerCase();
      var show = !q || kw.indexOf(q) !== -1 || text.indexOf(q) !== -1 || cat.indexOf(q) !== -1;
      row.classList.toggle('rxcs-hidden', !show);
      if (show) visibleBySection[cat] = true;
    });

    sections.forEach(function(sec) {
      var secId = sec.getAttribute('data-section');
      var visible = !q || visibleBySection[secId];
      sec.classList.toggle('rxcs-hidden', !visible);
    });

    var anyVisible = tbody.querySelectorAll('tr[data-cat]:not(.rxcs-hidden)').length > 0;
    noResEl.classList.toggle('visible', !anyVisible && !!q);
  }

  searchEl.addEventListener('input', applySearch);
  clearEl.addEventListener('click', function() {
    searchEl.value = '';
    applySearch();
    searchEl.focus();
  });

  patEl.addEventListener('input', run);
  testEl.addEventListener('input', run);
  Object.keys(flagEls).forEach(function(k) {
    flagEls[k].addEventListener('change', run);
  });

  run();
})();

// Global helpers called from inline onclick
function rxcsTry(pattern, testStr) {
  var patEl  = document.getElementById('rxcs-pattern');
  var testEl = document.getElementById('rxcs-teststr');
  patEl.value  = pattern;
  testEl.value = testStr;
  patEl.dispatchEvent(new Event('input'));
  document.getElementById('rxcs-pattern').scrollIntoView({ behavior: 'smooth', block: 'center' });
}

function rxcsCopy(btn, text) {
  var copy = function() {
    btn.textContent = 'Copied!';
    btn.classList.add('copied');
    setTimeout(function() {
      btn.textContent = 'Copy';
      btn.classList.remove('copied');
    }, 1600);
  };
  if (navigator.clipboard) {
    navigator.clipboard.writeText(text).then(copy);
  } else {
    var ta = document.createElement('textarea');
    ta.value = text;
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    document.body.removeChild(ta);
    copy();
  }
}
</script>

</div>

---

## Understanding the Regex Cheatsheet

This cheatsheet covers the full JavaScript regex syntax as implemented in modern browsers (V8 engine). JavaScript regex supports all PCRE-compatible features used in most modern languages — Python, Ruby, Java, Go, PHP — with minor differences in syntax for lookbehinds (available in V8 since Node.js 9.11) and named groups.

**Key concepts to remember:**

- **Greedy vs. lazy quantifiers** — `*`, `+`, and `{n,m}` are greedy by default: they match as much as possible. Adding `?` after them (e.g. `*?`, `+?`) makes them lazy — they match as little as possible. This matters when parsing HTML or quoted strings.
- **Capture groups vs. non-capture groups** — use `(...)` when you need to extract the matched text (via `.exec()` or replace with `$1`). Use `(?:...)` when you only need grouping for alternation or quantifiers but don't need the captured value.
- **Anchors with multiline flag** — `^` and `$` match the start/end of the entire string by default. Enable the `m` flag to make them match the start/end of each line.
- **Lookaheads are zero-width** — `(?=foo)` and `(?!foo)` assert a condition without consuming characters, so the matched position is not advanced. This is useful for conditional matching without including the surrounding context in your match.

---

### Related Tools

> Test regex patterns → [Regex Tester](/tools/regex-tester/)

> Format SQL queries → [SQL Formatter](/tools/sql-formatter/)

> Search/replace text → [Text Diff Checker](/tools/text-diff/)
