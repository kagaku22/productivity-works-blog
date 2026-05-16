---
title: "Regex Tester - Free Online Regular Expression Tool"
date: 2025-05-16
description: "Test and debug regular expressions in real-time. Syntax highlighting, match groups, common patterns library. Free online regex tester for developers."
categories: ["Free Tools"]
tags: ["regex", "regular expression", "tester", "developer tool", "pattern matching"]
slug: "regex-tester"
aliases: ["/tools/regexp-tester/", "/tools/regular-expression/"]
cover:
  image: "/images/covers/regex-tester.png"
  alt: "Regex Tester"
ShowToc: false
---

<div id="regex-app">

<style>
#regex-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #1a1a2e;
  color: #e0e0e0;
  padding: 24px;
  border-radius: 12px;
  max-width: 900px;
  margin: 0 auto;
  box-sizing: border-box;
}

#regex-app * {
  box-sizing: border-box;
}

#regex-app h2 {
  color: #00ff88;
  margin: 0 0 20px 0;
  font-size: 1.4rem;
  letter-spacing: 0.5px;
}

#regex-app .ra-section {
  margin-bottom: 20px;
}

#regex-app label {
  display: block;
  color: #a0a0c0;
  font-size: 0.82rem;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  margin-bottom: 6px;
  font-weight: 600;
}

#regex-app .ra-pattern-row {
  display: flex;
  gap: 8px;
  align-items: center;
  flex-wrap: wrap;
}

#regex-app .ra-pattern-wrap {
  display: flex;
  align-items: center;
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 8px;
  flex: 1;
  min-width: 200px;
  transition: border-color 0.2s;
}

#regex-app .ra-pattern-wrap:focus-within {
  border-color: #00ff88;
}

#regex-app .ra-slash {
  color: #00ff88;
  font-size: 1.3rem;
  padding: 0 6px;
  font-family: monospace;
  user-select: none;
}

#regex-app .ra-pattern-input {
  background: transparent;
  border: none;
  outline: none;
  color: #00ff88;
  font-family: 'Courier New', monospace;
  font-size: 1rem;
  flex: 1;
  padding: 10px 4px;
  width: 0;
}

#regex-app .ra-flags-wrap {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

#regex-app .ra-flag-label {
  display: flex;
  align-items: center;
  gap: 4px;
  cursor: pointer;
  font-size: 0.85rem;
  color: #b0b0d0;
  text-transform: none;
  letter-spacing: 0;
  font-weight: 400;
  margin: 0;
  user-select: none;
}

#regex-app .ra-flag-label input[type="checkbox"] {
  accent-color: #00ff88;
  width: 14px;
  height: 14px;
  cursor: pointer;
}

#regex-app .ra-flag-key {
  font-family: monospace;
  color: #00ff88;
  font-weight: 700;
}

#regex-app .ra-btn {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  color: #e0e0e0;
  padding: 10px 16px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 0.85rem;
  transition: all 0.2s;
  white-space: nowrap;
}

#regex-app .ra-btn:hover {
  border-color: #00ff88;
  color: #00ff88;
}

#regex-app .ra-btn-primary {
  background: #00ff88;
  border-color: #00ff88;
  color: #0d0d1a;
  font-weight: 700;
}

#regex-app .ra-btn-primary:hover {
  background: #00cc6e;
  border-color: #00cc6e;
  color: #0d0d1a;
}

#regex-app select {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  color: #e0e0e0;
  padding: 10px 12px;
  border-radius: 8px;
  font-size: 0.85rem;
  cursor: pointer;
  outline: none;
  transition: border-color 0.2s;
  width: 100%;
}

#regex-app select:focus {
  border-color: #00ff88;
}

#regex-app textarea {
  width: 100%;
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  color: #e0e0e0;
  padding: 12px;
  border-radius: 8px;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  line-height: 1.6;
}

#regex-app textarea:focus {
  border-color: #00ff88;
}

#regex-app .ra-error {
  background: #2a0a0a;
  border: 1px solid #ff4444;
  color: #ff8888;
  padding: 10px 14px;
  border-radius: 8px;
  font-size: 0.85rem;
  font-family: monospace;
  display: none;
}

#regex-app .ra-error.visible {
  display: block;
}

#regex-app .ra-stats-bar {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 8px;
}

#regex-app .ra-match-count {
  background: #00ff8820;
  border: 1px solid #00ff8840;
  color: #00ff88;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.82rem;
  font-weight: 700;
}

#regex-app .ra-match-count.no-match {
  background: #ff444420;
  border-color: #ff444440;
  color: #ff8888;
}

#regex-app .ra-highlighted-display {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 8px;
  padding: 12px;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
  line-height: 1.6;
  min-height: 120px;
  white-space: pre-wrap;
  word-break: break-all;
  color: #e0e0e0;
}

#regex-app .ra-highlight {
  background: #00ff8840;
  border-bottom: 2px solid #00ff88;
  border-radius: 2px;
  color: #00ff88;
}

#regex-app .ra-highlight-alt {
  background: #ff88ff30;
  border-bottom: 2px solid #ff88ff;
  border-radius: 2px;
  color: #ff88ff;
}

#regex-app .ra-matches-panel {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 8px;
  max-height: 280px;
  overflow-y: auto;
  scrollbar-width: thin;
  scrollbar-color: #2a2a4a transparent;
}

#regex-app .ra-match-item {
  padding: 10px 14px;
  border-bottom: 1px solid #1a1a3a;
  display: grid;
  grid-template-columns: 60px 80px 1fr;
  gap: 10px;
  align-items: start;
  font-size: 0.84rem;
}

#regex-app .ra-match-item:last-child {
  border-bottom: none;
}

#regex-app .ra-match-idx {
  color: #606080;
  font-family: monospace;
}

#regex-app .ra-match-pos {
  color: #8080a0;
  font-family: monospace;
  font-size: 0.78rem;
}

#regex-app .ra-match-val {
  color: #00ff88;
  font-family: 'Courier New', monospace;
  word-break: break-all;
}

#regex-app .ra-match-groups {
  grid-column: 1 / -1;
  padding-left: 140px;
}

#regex-app .ra-group-item {
  color: #ff88ff;
  font-family: monospace;
  font-size: 0.78rem;
  margin-top: 3px;
}

#regex-app .ra-empty-state {
  text-align: center;
  color: #404060;
  padding: 30px;
  font-size: 0.9rem;
}

#regex-app .ra-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 12px;
  border-bottom: 1px solid #2a2a4a;
  padding-bottom: 0;
}

#regex-app .ra-tab {
  padding: 8px 16px;
  border: none;
  background: none;
  color: #606080;
  cursor: pointer;
  font-size: 0.85rem;
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  transition: all 0.2s;
}

#regex-app .ra-tab.active {
  color: #00ff88;
  border-bottom-color: #00ff88;
}

#regex-app .ra-tab-panel {
  display: none;
}

#regex-app .ra-tab-panel.active {
  display: block;
}

#regex-app .ra-replace-out {
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 8px;
  padding: 12px;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
  line-height: 1.6;
  min-height: 80px;
  white-space: pre-wrap;
  word-break: break-all;
  color: #ffe066;
}

#regex-app .ra-cheatsheet-toggle {
  width: 100%;
  text-align: left;
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-radius: 8px;
  color: #a0a0c0;
  padding: 10px 14px;
  cursor: pointer;
  font-size: 0.85rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: border-color 0.2s;
}

#regex-app .ra-cheatsheet-toggle:hover {
  border-color: #00ff88;
  color: #00ff88;
}

#regex-app .ra-cheatsheet-body {
  display: none;
  background: #0d0d1a;
  border: 1px solid #2a2a4a;
  border-top: none;
  border-radius: 0 0 8px 8px;
  padding: 14px;
}

#regex-app .ra-cheatsheet-body.open {
  display: block;
}

#regex-app .ra-cs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 8px;
}

#regex-app .ra-cs-item {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  padding: 6px 8px;
  background: #1a1a2e;
  border-radius: 6px;
}

#regex-app .ra-cs-token {
  font-family: 'Courier New', monospace;
  color: #00ff88;
  font-size: 0.88rem;
  min-width: 52px;
  font-weight: 700;
}

#regex-app .ra-cs-desc {
  color: #8080a0;
  font-size: 0.78rem;
  line-height: 1.4;
}

#regex-app .ra-two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

#regex-app .ra-copy-success {
  color: #00ff88;
  font-size: 0.8rem;
  margin-left: 8px;
  opacity: 0;
  transition: opacity 0.3s;
}

#regex-app .ra-copy-success.show {
  opacity: 1;
}

@media (max-width: 600px) {
  #regex-app {
    padding: 14px;
  }
  #regex-app .ra-two-col {
    grid-template-columns: 1fr;
  }
  #regex-app .ra-match-item {
    grid-template-columns: 50px 70px 1fr;
    gap: 6px;
  }
  #regex-app .ra-match-groups {
    padding-left: 0;
  }
  #regex-app .ra-cs-grid {
    grid-template-columns: 1fr 1fr;
  }
}
</style>

<h2>Regex Tester</h2>

<!-- Pattern Input -->
<div class="ra-section">
  <label>Regular Expression</label>
  <div class="ra-pattern-row">
    <div class="ra-pattern-wrap">
      <span class="ra-slash">/</span>
      <input class="ra-pattern-input" id="ra-pattern" type="text" placeholder="Enter pattern..." autocomplete="off" spellcheck="false" />
      <span class="ra-slash">/</span>
    </div>
    <div class="ra-flags-wrap">
      <label class="ra-flag-label"><input type="checkbox" id="ra-flag-g" checked /><span class="ra-flag-key">g</span> global</label>
      <label class="ra-flag-label"><input type="checkbox" id="ra-flag-i" /><span class="ra-flag-key">i</span> case-insensitive</label>
      <label class="ra-flag-label"><input type="checkbox" id="ra-flag-m" /><span class="ra-flag-key">m</span> multiline</label>
      <label class="ra-flag-label"><input type="checkbox" id="ra-flag-s" /><span class="ra-flag-key">s</span> dotAll</label>
      <label class="ra-flag-label"><input type="checkbox" id="ra-flag-u" /><span class="ra-flag-key">u</span> unicode</label>
    </div>
    <button class="ra-btn" id="ra-copy-btn">Copy Regex</button>
    <span class="ra-copy-success" id="ra-copy-msg">Copied!</span>
  </div>
</div>

<!-- Error -->
<div class="ra-error" id="ra-error"></div>

<!-- Common Patterns -->
<div class="ra-section">
  <label>Common Patterns</label>
  <select id="ra-presets">
    <option value="">-- Select a pattern to load --</option>
    <option value="email">[Email] Email Address</option>
    <option value="url">[URL] HTTP/HTTPS URL</option>
    <option value="phone_us">[Phone] US Phone Number</option>
    <option value="phone_int">[Phone] International Phone</option>
    <option value="ip4">[Network] IPv4 Address</option>
    <option value="ip6">[Network] IPv6 Address</option>
    <option value="date_iso">[Date] ISO 8601 (YYYY-MM-DD)</option>
    <option value="date_us">[Date] US Format (MM/DD/YYYY)</option>
    <option value="hex_color">[Color] Hex Color Code</option>
    <option value="html_tag">[HTML] HTML Tag</option>
    <option value="slug">[Web] URL Slug</option>
    <option value="username">[Auth] Username (alphanumeric)</option>
    <option value="password">[Auth] Strong Password</option>
    <option value="credit_card">[Finance] Credit Card Number</option>
    <option value="zip_us">[Address] US ZIP Code</option>
    <option value="whitespace">[Utility] Multiple Whitespace</option>
  </select>
</div>

<!-- Test String -->
<div class="ra-section">
  <label>Test String</label>
  <textarea id="ra-teststr" rows="6" placeholder="Enter your test string here..."></textarea>
</div>

<!-- Stats -->
<div class="ra-stats-bar">
  <span class="ra-match-count" id="ra-count-badge">No matches</span>
  <span style="color:#505070;font-size:0.8rem;" id="ra-flags-display"></span>
</div>

<!-- Tabs: Matches / Highlighted / Replace -->
<div class="ra-tabs">
  <button class="ra-tab active" data-tab="matches">Matches</button>
  <button class="ra-tab" data-tab="highlight">Highlighted</button>
  <button class="ra-tab" data-tab="replace">Replace</button>
</div>

<!-- Matches Panel -->
<div class="ra-tab-panel active" id="ra-tab-matches">
  <div class="ra-matches-panel" id="ra-matches-panel">
    <div class="ra-empty-state" id="ra-empty-state">Enter a pattern and test string to see matches</div>
  </div>
</div>

<!-- Highlighted Panel -->
<div class="ra-tab-panel" id="ra-tab-highlight">
  <div class="ra-highlighted-display" id="ra-highlighted-display">Matches will be highlighted here</div>
</div>

<!-- Replace Panel -->
<div class="ra-tab-panel" id="ra-tab-replace">
  <div class="ra-section" style="margin-top:4px;">
    <label>Replacement Pattern</label>
    <textarea id="ra-replace-input" rows="2" placeholder="Replacement string (use $1, $2 for groups)..."></textarea>
  </div>
  <div class="ra-section">
    <label>Replace Result</label>
    <div class="ra-replace-out" id="ra-replace-out">Result will appear here</div>
  </div>
</div>

<!-- Cheat Sheet -->
<div class="ra-section" style="margin-top:24px;">
  <button class="ra-cheatsheet-toggle" id="ra-cs-toggle">
    <span>Regex Cheat Sheet</span>
    <span id="ra-cs-arrow">▼</span>
  </button>
  <div class="ra-cheatsheet-body" id="ra-cs-body">
    <div class="ra-cs-grid">
      <div class="ra-cs-item"><span class="ra-cs-token">\d</span><span class="ra-cs-desc">Digit [0-9]</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\D</span><span class="ra-cs-desc">Non-digit</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\w</span><span class="ra-cs-desc">Word char [a-zA-Z0-9_]</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\W</span><span class="ra-cs-desc">Non-word character</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\s</span><span class="ra-cs-desc">Whitespace char</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\S</span><span class="ra-cs-desc">Non-whitespace</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">.</span><span class="ra-cs-desc">Any char (except newline)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\b</span><span class="ra-cs-desc">Word boundary</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">^</span><span class="ra-cs-desc">Start of string/line</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">$</span><span class="ra-cs-desc">End of string/line</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">*</span><span class="ra-cs-desc">0 or more (greedy)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">+</span><span class="ra-cs-desc">1 or more (greedy)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">?</span><span class="ra-cs-desc">0 or 1 (optional)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">*?</span><span class="ra-cs-desc">0 or more (lazy)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">+?</span><span class="ra-cs-desc">1 or more (lazy)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">{n}</span><span class="ra-cs-desc">Exactly n times</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">{n,m}</span><span class="ra-cs-desc">Between n and m times</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">{n,}</span><span class="ra-cs-desc">n or more times</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">[abc]</span><span class="ra-cs-desc">Character class (a, b, or c)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">[^abc]</span><span class="ra-cs-desc">Negated class</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">[a-z]</span><span class="ra-cs-desc">Character range</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">(abc)</span><span class="ra-cs-desc">Capture group</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">(?:abc)</span><span class="ra-cs-desc">Non-capture group</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">(?=abc)</span><span class="ra-cs-desc">Lookahead</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">(?!abc)</span><span class="ra-cs-desc">Negative lookahead</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">a|b</span><span class="ra-cs-desc">Alternation (a or b)</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\n</span><span class="ra-cs-desc">Newline</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">\t</span><span class="ra-cs-desc">Tab character</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">$1</span><span class="ra-cs-desc">Backreference to group 1</span></div>
      <div class="ra-cs-item"><span class="ra-cs-token">(?&lt;name&gt;)</span><span class="ra-cs-desc">Named capture group</span></div>
    </div>
  </div>
</div>

<script>
(function() {
  var PRESETS = {
    email: { pattern: '[a-zA-Z0-9._%+\\-]+@[a-zA-Z0-9.\\-]+\\.[a-zA-Z]{2,}', flags: {g:true,i:true,m:false,s:false,u:false}, test: 'Contact us at hello@example.com or support@company.org\nInvalid: not-an-email, @nodomain, missingat.com' },
    url: { pattern: 'https?:\\/\\/(?:www\\.)?[-a-zA-Z0-9@:%._\\+~#=]{1,256}\\.[a-zA-Z0-9()]{1,6}\\b(?:[-a-zA-Z0-9()@:%_\\+.~#?&\\/=]*)', flags: {g:true,i:true,m:false,s:false,u:false}, test: 'Visit https://www.example.com or http://blog.example.org/path?q=1&page=2\nAlso check https://subdomain.example.co.uk/resource#section' },
    phone_us: { pattern: '(?:\\+1[\\s\\-]?)?(?:\\(?[2-9]\\d{2}\\)?)[\\s\\-]?[2-9]\\d{2}[\\s\\-]?\\d{4}', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'Call us: (555) 123-4567 or 555-987-6543\nAlso: +1 (800) 555-0100 or 18005550100' },
    phone_int: { pattern: '\\+?[1-9]\\d{1,14}', flags: {g:true,i:false,m:false,s:false,u:false}, test: '+1 555 123 4567\n+44 20 7946 0958\n+81-3-1234-5678' },
    ip4: { pattern: '\\b(?:(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\.){3}(?:25[0-5]|2[0-4]\\d|[01]?\\d\\d?)\\b', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'Server IPs: 192.168.1.1, 10.0.0.255, 172.16.254.1\nInvalid: 256.1.1.1, 192.168.1' },
    ip6: { pattern: '(?:[0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}|(?:[0-9a-fA-F]{1,4}:){1,7}:|::(?:[0-9a-fA-F]{1,4}:){0,6}[0-9a-fA-F]{1,4}', flags: {g:true,i:true,m:false,s:false,u:false}, test: '2001:0db8:85a3:0000:0000:8a2e:0370:7334\n::1\nfe80::1' },
    date_iso: { pattern: '\\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\\d|3[01])', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'Dates: 2025-05-16, 2024-12-31, 2023-01-01\nInvalid: 2025-13-01, 2025-00-15, 25-05-16' },
    date_us: { pattern: '(?:0[1-9]|1[0-2])\\/(?:0[1-9]|[12]\\d|3[01])\\/(?:19|20)\\d{2}', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'Event dates: 05/16/2025, 12/31/2024, 01/01/2023\nInvalid: 13/01/2025, 00/15/2025' },
    hex_color: { pattern: '#(?:[0-9a-fA-F]{3}){1,2}\\b', flags: {g:true,i:true,m:false,s:false,u:false}, test: 'Colors: #fff, #1a1a2e, #00ff88, #FF5733\nInvalid: #gggggg, #12345' },
    html_tag: { pattern: '<\\/?[a-zA-Z][^>]*>', flags: {g:true,i:true,m:false,s:false,u:false}, test: '<div class="container"><p>Hello <strong>World</strong></p></div>\n<img src="image.png" alt="test" />' },
    slug: { pattern: '[a-z0-9]+(?:-[a-z0-9]+)*', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'my-blog-post\nhello-world-2025\nthis-is-a-slug\nInvalid: Has Spaces, UPPERCASE, special@chars' },
    username: { pattern: '[a-zA-Z0-9_]{3,16}', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'Valid: john_doe, User123, dev_42\nInvalid: ab (too short), has space, special@chars' },
    password: { pattern: '(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*]).{8,}', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'StrongP@ss1\nWeakpass\nNoSpecial1A\nShort@1A\nAllgood$2025A' },
    credit_card: { pattern: '(?:4\\d{3}|5[1-5]\\d{2}|6(?:011|5\\d{2})|3[47]\\d{2})[\\s\\-]?\\d{4}[\\s\\-]?\\d{4}[\\s\\-]?\\d{4}', flags: {g:true,i:false,m:false,s:false,u:false}, test: '4111 1111 1111 1111\n5500-0000-0000-0004\n378282246310005' },
    zip_us: { pattern: '\\b\\d{5}(?:-\\d{4})?\\b', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'ZIP codes: 90210, 10001-1234, 60601\nInvalid: 1234, 123456' },
    whitespace: { pattern: '\\s{2,}', flags: {g:true,i:false,m:false,s:false,u:false}, test: 'This  has   multiple    spaces\nAnd\t\ttabs\nAnd\n\nnewlines' }
  };

  var patternEl = document.getElementById('ra-pattern');
  var testEl = document.getElementById('ra-teststr');
  var errorEl = document.getElementById('ra-error');
  var countEl = document.getElementById('ra-count-badge');
  var matchesPanel = document.getElementById('ra-matches-panel');
  var emptyState = document.getElementById('ra-empty-state');
  var highlightEl = document.getElementById('ra-highlighted-display');
  var replaceInput = document.getElementById('ra-replace-input');
  var replaceOut = document.getElementById('ra-replace-out');
  var flagsDisplay = document.getElementById('ra-flags-display');
  var copyBtn = document.getElementById('ra-copy-btn');
  var copyMsg = document.getElementById('ra-copy-msg');
  var presets = document.getElementById('ra-presets');
  var csToggle = document.getElementById('ra-cs-toggle');
  var csBody = document.getElementById('ra-cs-body');
  var csArrow = document.getElementById('ra-cs-arrow');

  var flagIds = ['g','i','m','s','u'];
  function getFlags() {
    return flagIds.filter(function(f){ return document.getElementById('ra-flag-'+f).checked; }).join('');
  }
  function setFlags(flagObj) {
    flagIds.forEach(function(f){ document.getElementById('ra-flag-'+f).checked = !!flagObj[f]; });
  }

  function buildRegex() {
    var p = patternEl.value;
    if (!p) return null;
    var flags = getFlags();
    try {
      return new RegExp(p, flags);
    } catch(e) {
      return e;
    }
  }

  function escapeHtml(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function run() {
    var pattern = patternEl.value.trim();
    var test = testEl.value;
    var flags = getFlags();

    flagsDisplay.textContent = pattern ? ('/' + pattern + '/' + flags) : '';

    if (!pattern) {
      errorEl.classList.remove('visible');
      countEl.textContent = 'No matches';
      countEl.classList.add('no-match');
      matchesPanel.innerHTML = '<div class="ra-empty-state">Enter a pattern and test string to see matches</div>';
      highlightEl.textContent = test || 'Matches will be highlighted here';
      replaceOut.textContent = test || 'Result will appear here';
      return;
    }

    var regex = buildRegex();
    if (regex instanceof Error) {
      errorEl.textContent = 'Invalid regex: ' + regex.message;
      errorEl.classList.add('visible');
      countEl.textContent = 'Error';
      countEl.classList.add('no-match');
      matchesPanel.innerHTML = '<div class="ra-empty-state" style="color:#ff6666;">Fix the regex error above</div>';
      highlightEl.textContent = test;
      replaceOut.textContent = '';
      return;
    }
    errorEl.classList.remove('visible');

    if (!test) {
      countEl.textContent = 'No test string';
      countEl.classList.add('no-match');
      matchesPanel.innerHTML = '<div class="ra-empty-state">Enter a test string above</div>';
      highlightEl.textContent = '';
      replaceOut.textContent = '';
      return;
    }

    // Collect all matches
    var allMatches = [];
    var re2 = new RegExp(pattern, flags.replace('g','') + 'g' + (flags.indexOf('g') === -1 ? '' : ''));
    // Always collect with global for listing
    var reG = new RegExp(pattern, (flags.indexOf('g') === -1 ? flags + 'g' : flags));
    var m;
    reG.lastIndex = 0;
    while ((m = reG.exec(test)) !== null) {
      allMatches.push({ index: m.index, value: m[0], groups: Array.from(m).slice(1) });
      if (m[0].length === 0) reG.lastIndex++;
      if (allMatches.length > 1000) break;
    }

    // Count badge
    var cnt = allMatches.length;
    countEl.textContent = cnt === 0 ? 'No matches' : (cnt === 1 ? '1 match' : cnt + ' matches');
    countEl.classList.toggle('no-match', cnt === 0);

    // Matches panel
    if (cnt === 0) {
      matchesPanel.innerHTML = '<div class="ra-empty-state">No matches found</div>';
    } else {
      var html = '';
      allMatches.forEach(function(match, i) {
        var hasGroups = match.groups && match.groups.some(function(g){ return g !== undefined; });
        html += '<div class="ra-match-item">';
        html += '<span class="ra-match-idx">#' + (i+1) + '</span>';
        html += '<span class="ra-match-pos">@' + match.index + '</span>';
        html += '<span class="ra-match-val">' + escapeHtml(match.value) + '</span>';
        if (hasGroups) {
          html += '<div class="ra-match-groups">';
          match.groups.forEach(function(g, gi) {
            if (g !== undefined) {
              html += '<div class="ra-group-item">Group ' + (gi+1) + ': ' + escapeHtml(g) + '</div>';
            }
          });
          html += '</div>';
        }
        html += '</div>';
      });
      matchesPanel.innerHTML = html;
    }

    // Highlighted display
    if (cnt === 0) {
      highlightEl.textContent = test;
    } else {
      var parts = [];
      var last = 0;
      allMatches.forEach(function(match, i) {
        if (match.index > last) {
          parts.push('<span>' + escapeHtml(test.slice(last, match.index)) + '</span>');
        }
        var cls = i % 2 === 0 ? 'ra-highlight' : 'ra-highlight-alt';
        parts.push('<span class="' + cls + '" title="Match ' + (i+1) + '">' + escapeHtml(match.value) + '</span>');
        last = match.index + match.value.length;
      });
      if (last < test.length) {
        parts.push('<span>' + escapeHtml(test.slice(last)) + '</span>');
      }
      highlightEl.innerHTML = parts.join('');
    }

    // Replace
    runReplace(pattern, flags, test);
  }

  function runReplace(pattern, flags, test) {
    if (!pattern) { replaceOut.textContent = test || ''; return; }
    try {
      var rp = replaceInput.value;
      // Ensure global flag for full replace
      var repFlags = flags.indexOf('g') === -1 ? flags + 'g' : flags;
      var re = new RegExp(pattern, repFlags);
      var result = test.replace(re, rp);
      replaceOut.textContent = result;
    } catch(e) {
      replaceOut.textContent = '';
    }
  }

  // Tab switching
  document.querySelectorAll('#regex-app .ra-tab').forEach(function(tab) {
    tab.addEventListener('click', function() {
      document.querySelectorAll('#regex-app .ra-tab').forEach(function(t){ t.classList.remove('active'); });
      document.querySelectorAll('#regex-app .ra-tab-panel').forEach(function(p){ p.classList.remove('active'); });
      tab.classList.add('active');
      document.getElementById('ra-tab-' + tab.dataset.tab).classList.add('active');
    });
  });

  // Cheat sheet toggle
  csToggle.addEventListener('click', function() {
    csBody.classList.toggle('open');
    csArrow.textContent = csBody.classList.contains('open') ? '▲' : '▼';
  });

  // Copy button
  copyBtn.addEventListener('click', function() {
    var pattern = patternEl.value;
    var flags = getFlags();
    var text = '/' + pattern + '/' + flags;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(showCopied);
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showCopied();
    }
  });

  function showCopied() {
    copyMsg.classList.add('show');
    setTimeout(function(){ copyMsg.classList.remove('show'); }, 1800);
  }

  // Presets
  presets.addEventListener('change', function() {
    var key = presets.value;
    if (!key || !PRESETS[key]) return;
    var p = PRESETS[key];
    patternEl.value = p.pattern;
    setFlags(p.flags);
    if (p.test && !testEl.value) testEl.value = p.test;
    run();
    presets.value = '';
  });

  // Events
  patternEl.addEventListener('input', run);
  testEl.addEventListener('input', run);
  replaceInput.addEventListener('input', run);
  flagIds.forEach(function(f) {
    document.getElementById('ra-flag-'+f).addEventListener('change', run);
  });

  // Init
  run();
})();
</script>

</div>

---

## How to Use Regular Expressions

A **regular expression** (regex) is a sequence of characters that defines a search pattern. Regex patterns are used across virtually every programming language and text editor for tasks like input validation, data extraction, search-and-replace operations, and string parsing. At their core, regex patterns are built from literal characters combined with special **metacharacters** that control how and what gets matched — for example, `\d` matches any digit, `.` matches any character except newline, and `*` means "zero or more of the preceding element."

To use the tester above, enter your pattern in the `/pattern/` field, select any flags you need (the **g** flag is enabled by default to find all matches rather than just the first), and then type or paste your test string in the large textarea. Matches are highlighted in real-time in the **Highlighted** tab with alternating colors. The **Matches** tab lists every match individually, showing its position index and any captured groups. Use the **Replace** tab to test substitution patterns — reference capture groups with `$1`, `$2`, and so on.

When building complex expressions, use the **Common Patterns** dropdown to load a pre-built, tested pattern as a starting point and study how it is constructed. The **Cheat Sheet** panel at the bottom is a quick reference for the most common tokens and quantifiers. If your pattern contains a syntax error, a clear error message will appear immediately beneath the pattern field — common mistakes include unescaped special characters (use a backslash: `\.` to match a literal dot), unbalanced parentheses, and invalid quantifier syntax like `{,3}`.

---

## Common Regex Patterns

| Pattern | Regex | Description |
|---|---|---|
| Email address | `[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}` | Matches standard email addresses |
| HTTP/HTTPS URL | `https?:\/\/[\w\-]+(\.[\w\-]+)+([\w.,@?^=%&:/~+#\-]*)` | Matches web URLs with optional path and query |
| US phone number | `(\(?\d{3}\)?[\s\-]?)?\d{3}[\s\-]?\d{4}` | Matches common US phone number formats |
| IPv4 address | `\b(?:\d{1,3}\.){3}\d{1,3}\b` | Matches dotted decimal IP addresses |
| ISO date | `\d{4}-(?:0[1-9]|1[0-2])-(?:0[1-9]|[12]\d|3[01])` | Matches YYYY-MM-DD formatted dates |
| Hex color | `#(?:[0-9a-fA-F]{3}){1,2}\b` | Matches 3- and 6-digit hex color codes |
| Strong password | `(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*]).{8,}` | Requires uppercase, lowercase, digit, and symbol |
| HTML tag | `<\/?[a-zA-Z][^>]*>` | Matches opening and closing HTML tags |

---

## Related Tools

> Format and validate JSON data → [JSON Formatter](/tools/json-formatter/)

> Encode and decode Base64 → [Base64 Encoder](/tools/base64-encoder/)

> Count words and characters → [Word Counter](/tools/word-counter/)
