---
title: "String Escape Tool — Multi-Language Escaper"
date: 2025-05-16
description: "Escape and unescape strings for JSON, JavaScript, Python, Java, SQL, HTML, and more. Handle quotes, backslashes, newlines, and special characters."
categories: ["Free Tools"]
slug: "string-escape-tool"
ShowToc: false
cover:
  image: "/images/covers/string-escape-tool.png"
  alt: "String Escape Tool"
---

<div id="esc-app">

<style>
#esc-app *,
#esc-app *::before,
#esc-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#esc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 15px;
  color: #1a1a2e;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 8px 48px;
}

#esc-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 12px;
  color: #1a1a2e;
}

#esc-app .esc-intro {
  background: #f0f4ff;
  border-left: 4px solid #3b6ef8;
  border-radius: 4px;
  padding: 14px 16px;
  margin-bottom: 24px;
  font-size: 0.93rem;
  color: #333;
  line-height: 1.6;
}

/* Mode Selector */
#esc-app .esc-mode-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}

#esc-app .esc-mode-btn {
  padding: 6px 14px;
  border-radius: 20px;
  border: 2px solid #d0d5e8;
  background: #fff;
  color: #555;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
  white-space: nowrap;
}

#esc-app .esc-mode-btn:hover {
  border-color: #3b6ef8;
  color: #3b6ef8;
}

#esc-app .esc-mode-btn.active {
  background: #3b6ef8;
  border-color: #3b6ef8;
  color: #fff;
}

/* Bulk toggle */
#esc-app .esc-options-row {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

#esc-app .esc-toggle-label {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-size: 0.88rem;
  color: #444;
  user-select: none;
}

#esc-app .esc-toggle-label input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #3b6ef8;
  cursor: pointer;
}

#esc-app .esc-mode-desc {
  font-size: 0.82rem;
  color: #777;
  font-style: italic;
}

/* Textareas */
#esc-app .esc-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}

@media (max-width: 600px) {
  #esc-app .esc-panels {
    grid-template-columns: 1fr;
  }
}

#esc-app .esc-panel {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

#esc-app .esc-panel-label {
  font-size: 0.82rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #555;
}

#esc-app .esc-textarea {
  width: 100%;
  min-height: 200px;
  padding: 12px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.88rem;
  line-height: 1.6;
  border: 2px solid #d0d5e8;
  border-radius: 8px;
  background: #fafbff;
  color: #1a1a2e;
  resize: vertical;
  transition: border-color 0.15s;
  outline: none;
}

#esc-app .esc-textarea:focus {
  border-color: #3b6ef8;
  background: #fff;
}

#esc-app .esc-textarea.output {
  background: #f4f7ff;
  color: #1a3a6e;
}

/* Action buttons */
#esc-app .esc-action-row {
  display: flex;
  gap: 10px;
  margin-bottom: 8px;
  flex-wrap: wrap;
  align-items: center;
}

#esc-app .esc-btn {
  padding: 10px 24px;
  border-radius: 8px;
  border: none;
  font-size: 0.9rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  letter-spacing: 0.02em;
}

#esc-app .esc-btn:active {
  transform: scale(0.97);
}

#esc-app .esc-btn-escape {
  background: #3b6ef8;
  color: #fff;
}

#esc-app .esc-btn-escape:hover {
  background: #2550d0;
}

#esc-app .esc-btn-unescape {
  background: #12b886;
  color: #fff;
}

#esc-app .esc-btn-unescape:hover {
  background: #0a9a70;
}

#esc-app .esc-btn-copy {
  background: #f0f4ff;
  color: #3b6ef8;
  border: 2px solid #3b6ef8;
  padding: 8px 18px;
}

#esc-app .esc-btn-copy:hover {
  background: #3b6ef8;
  color: #fff;
}

#esc-app .esc-btn-clear {
  background: #fff;
  color: #999;
  border: 2px solid #d0d5e8;
  padding: 8px 14px;
  font-size: 0.82rem;
}

#esc-app .esc-btn-clear:hover {
  border-color: #e05c5c;
  color: #e05c5c;
}

/* Status message */
#esc-app .esc-status {
  font-size: 0.82rem;
  color: #12b886;
  font-weight: 600;
  min-height: 18px;
  transition: opacity 0.3s;
}

#esc-app .esc-status.error {
  color: #e05c5c;
}

/* Reference table */
#esc-app .esc-ref {
  margin-top: 32px;
  background: #fafbff;
  border: 1px solid #d0d5e8;
  border-radius: 10px;
  padding: 20px;
}

#esc-app .esc-ref h3 {
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 14px;
  color: #1a1a2e;
}

#esc-app .esc-ref-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 8px;
}

#esc-app .esc-ref-item {
  background: #fff;
  border: 1px solid #e0e5f0;
  border-radius: 6px;
  padding: 8px 12px;
  font-size: 0.82rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8px;
}

#esc-app .esc-ref-item code {
  font-family: monospace;
  background: #f0f4ff;
  padding: 1px 5px;
  border-radius: 3px;
  color: #3b6ef8;
  font-size: 0.88em;
  white-space: nowrap;
}

#esc-app .esc-ref-item span {
  color: #777;
}

/* How it works */
#esc-app .esc-howto {
  margin-top: 28px;
}

#esc-app .esc-howto h3 {
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 10px;
}

#esc-app .esc-howto ul {
  padding-left: 20px;
  line-height: 1.85;
  color: #444;
  font-size: 0.92rem;
}

/* Related links */
#esc-app .esc-related {
  margin-top: 32px;
  padding-top: 20px;
  border-top: 1px solid #e0e5f0;
}

#esc-app .esc-related h3 {
  font-size: 0.88rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #777;
  margin-bottom: 10px;
}

#esc-app .esc-related-links {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

#esc-app .esc-related-links a {
  display: inline-block;
  padding: 7px 16px;
  border-radius: 20px;
  border: 2px solid #3b6ef8;
  color: #3b6ef8;
  font-size: 0.85rem;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.15s, color 0.15s;
}

#esc-app .esc-related-links a:hover {
  background: #3b6ef8;
  color: #fff;
}
</style>

<div class="esc-intro">
  Escape and unescape strings instantly for 10 language modes: JSON, JavaScript/TypeScript, Python, Java, C#, SQL, HTML, XML, CSV, and Regex. Paste raw text, pick a mode, and hit <strong>Escape</strong> — or paste escaped text and hit <strong>Unescape</strong> to recover the original. No data leaves your browser.
</div>

<h2>Select Language / Context</h2>
<div class="esc-mode-row" id="escModeRow"></div>

<div class="esc-options-row">
  <label class="esc-toggle-label">
    <input type="checkbox" id="escBulkMode">
    Bulk mode (process each line independently)
  </label>
  <span class="esc-mode-desc" id="escModeDesc"></span>
</div>

<div class="esc-panels">
  <div class="esc-panel">
    <div class="esc-panel-label">Input</div>
    <textarea class="esc-textarea" id="escInput" placeholder="Paste your string here…" spellcheck="false"></textarea>
  </div>
  <div class="esc-panel">
    <div class="esc-panel-label">Output</div>
    <textarea class="esc-textarea output" id="escOutput" placeholder="Result will appear here…" readonly spellcheck="false"></textarea>
  </div>
</div>

<div class="esc-action-row">
  <button class="esc-btn esc-btn-escape" id="escEscapeBtn">Escape</button>
  <button class="esc-btn esc-btn-unescape" id="escUnescapeBtn">Unescape</button>
  <button class="esc-btn esc-btn-copy" id="escCopyBtn">Copy Output</button>
  <button class="esc-btn esc-btn-clear" id="escClearBtn">Clear</button>
</div>
<div class="esc-status" id="escStatus"></div>

<div class="esc-ref">
  <h3>Escape Sequence Reference</h3>
  <div class="esc-ref-grid" id="escRefGrid"></div>
</div>

<div class="esc-howto">
  <h3>How to Use</h3>
  <ul>
    <li><strong>Select a mode</strong> — choose the target language or format from the buttons above.</li>
    <li><strong>Paste input</strong> — enter the raw string you want to escape (or an already-escaped string to unescape).</li>
    <li><strong>Escape / Unescape</strong> — click the appropriate button; the result appears instantly on the right.</li>
    <li><strong>Bulk mode</strong> — when enabled, each line of input is escaped/unescaped independently, making it easy to process lists of strings.</li>
    <li><strong>Copy Output</strong> — copies the result to your clipboard with one click.</li>
  </ul>
</div>

<div class="esc-howto" style="margin-top:20px;">
  <h3>What Each Mode Handles</h3>
  <ul>
    <li><strong>JSON</strong> — <code>"</code>, <code>\</code>, <code>/</code>, control chars, unicode (<code>\uXXXX</code>)</li>
    <li><strong>JavaScript / TypeScript</strong> — single &amp; double quotes, backtick, <code>\n \t \r \0</code>, unicode</li>
    <li><strong>Python</strong> — single &amp; double quotes, <code>\n \t \r \\ \0</code>, raw-string awareness</li>
    <li><strong>Java / C#</strong> — standard C-style escapes plus unicode <code>\uXXXX</code></li>
    <li><strong>SQL</strong> — single-quote doubling, backslash mode toggle</li>
    <li><strong>HTML</strong> — named entities: <code>&amp;amp; &amp;lt; &amp;gt; &amp;quot; &amp;apos;</code></li>
    <li><strong>XML</strong> — same five entities as HTML, strictly per XML spec</li>
    <li><strong>CSV</strong> — field quoting, embedded quote doubling, newline handling</li>
    <li><strong>Regex</strong> — escapes all regex metacharacters: <code>. * + ? ^ $ { } [ ] | ( ) \</code></li>
  </ul>
</div>

<div class="esc-related">
  <h3>Related Tools</h3>
  <div class="esc-related-links">
    <a href="/tools/json-formatter/">JSON Formatter</a>
    <a href="/tools/html-entity-encoder/">HTML Entity Encoder</a>
    <a href="/tools/url-encoder/">URL Encoder</a>
  </div>
</div>

<script>
(function () {
  'use strict';

  /* ── Mode definitions ── */
  const MODES = [
    {
      id: 'json',
      label: 'JSON',
      desc: 'Escapes \\ " / and control characters per RFC 8259',
      refs: [
        { seq: '\\\\', desc: 'Backslash' },
        { seq: '\\"', desc: 'Double quote' },
        { seq: '\\/', desc: 'Forward slash' },
        { seq: '\\n', desc: 'Newline' },
        { seq: '\\r', desc: 'Carriage return' },
        { seq: '\\t', desc: 'Tab' },
        { seq: '\\b', desc: 'Backspace' },
        { seq: '\\f', desc: 'Form feed' },
        { seq: '\\uXXXX', desc: 'Unicode' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/"/g, '\\"')
          .replace(/\//g, '\\/')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\b/g, '\\b')
          .replace(/\f/g, '\\f')
          .replace(/[\x00-\x1f\x7f]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\"/g, '"')
          .replace(/\\\//g, '/')
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\b/g, '\b')
          .replace(/\\f/g, '\f')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'js',
      label: 'JS / TS',
      desc: 'Escapes for JavaScript and TypeScript string literals',
      refs: [
        { seq: '\\\\', desc: 'Backslash' },
        { seq: "\\'", desc: 'Single quote' },
        { seq: '\\"', desc: 'Double quote' },
        { seq: '\\`', desc: 'Backtick' },
        { seq: '\\n', desc: 'Newline' },
        { seq: '\\t', desc: 'Tab' },
        { seq: '\\r', desc: 'Carriage return' },
        { seq: '\\0', desc: 'Null char' },
        { seq: '\\uXXXX', desc: 'Unicode' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/'/g, "\\'")
          .replace(/"/g, '\\"')
          .replace(/`/g, '\\`')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\0/g, '\\0')
          .replace(/[\x00-\x1f\x7f]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\0/g, '\0')
          .replace(/\\'/g, "'")
          .replace(/\\"/g, '"')
          .replace(/\\`/g, '`')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'python',
      label: 'Python',
      desc: 'Escapes for Python string literals',
      refs: [
        { seq: '\\\\', desc: 'Backslash' },
        { seq: "\\'", desc: 'Single quote' },
        { seq: '\\"', desc: 'Double quote' },
        { seq: '\\n', desc: 'Newline' },
        { seq: '\\t', desc: 'Tab' },
        { seq: '\\r', desc: 'Carriage return' },
        { seq: '\\0', desc: 'Null char' },
        { seq: '\\xHH', desc: 'Hex escape' },
        { seq: '\\uXXXX', desc: 'Unicode' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/'/g, "\\'")
          .replace(/"/g, '\\"')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\0/g, '\\0')
          .replace(/[\x01-\x1f\x7f]/g, c => '\\x' + c.charCodeAt(0).toString(16).padStart(2, '0'));
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\x([0-9a-fA-F]{2})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\0/g, '\0')
          .replace(/\\'/g, "'")
          .replace(/\\"/g, '"')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'java',
      label: 'Java',
      desc: 'Java string literal escaping (also valid for Kotlin, Groovy)',
      refs: [
        { seq: '\\\\', desc: 'Backslash' },
        { seq: '\\"', desc: 'Double quote' },
        { seq: "\\'", desc: 'Single quote' },
        { seq: '\\n', desc: 'Newline' },
        { seq: '\\t', desc: 'Tab' },
        { seq: '\\r', desc: 'Carriage return' },
        { seq: '\\f', desc: 'Form feed' },
        { seq: '\\b', desc: 'Backspace' },
        { seq: '\\uXXXX', desc: 'Unicode' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/"/g, '\\"')
          .replace(/'/g, "\\'")
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\f/g, '\\f')
          .replace(/\b/g, '\\b')
          .replace(/[^\x20-\x7e]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\f/g, '\f')
          .replace(/\\b/g, '\b')
          .replace(/\\"/g, '"')
          .replace(/\\'/g, "'")
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'csharp',
      label: 'C#',
      desc: 'C# verbatim and regular string escaping',
      refs: [
        { seq: '\\\\', desc: 'Backslash' },
        { seq: '\\"', desc: 'Double quote' },
        { seq: '\\n', desc: 'Newline' },
        { seq: '\\t', desc: 'Tab' },
        { seq: '\\r', desc: 'Carriage return' },
        { seq: '\\0', desc: 'Null char' },
        { seq: '\\a', desc: 'Alert/bell' },
        { seq: '\\uXXXX', desc: 'Unicode' },
      ],
      escape(s) {
        return s
          .replace(/\\/g, '\\\\')
          .replace(/"/g, '\\"')
          .replace(/\n/g, '\\n')
          .replace(/\r/g, '\\r')
          .replace(/\t/g, '\\t')
          .replace(/\0/g, '\\0')
          .replace(/\x07/g, '\\a')
          .replace(/[^\x20-\x7e]/g, c => '\\u' + c.charCodeAt(0).toString(16).padStart(4, '0').toUpperCase());
      },
      unescape(s) {
        return s
          .replace(/\\u([0-9a-fA-F]{4})/g, (_, h) => String.fromCharCode(parseInt(h, 16)))
          .replace(/\\n/g, '\n')
          .replace(/\\r/g, '\r')
          .replace(/\\t/g, '\t')
          .replace(/\\0/g, '\0')
          .replace(/\\a/g, '\x07')
          .replace(/\\"/g, '"')
          .replace(/\\\\/g, '\\');
      },
    },
    {
      id: 'sql',
      label: 'SQL',
      desc: "Doubles single quotes (ANSI SQL standard)",
      refs: [
        { seq: "''", desc: "Single quote" },
        { seq: '\\n', desc: 'Newline (MySQL)' },
        { seq: '\\t', desc: 'Tab (MySQL)' },
        { seq: '\\\\', desc: 'Backslash (MySQL)' },
      ],
      escape(s) {
        return s.replace(/'/g, "''");
      },
      unescape(s) {
        return s.replace(/''/g, "'");
      },
    },
    {
      id: 'html',
      label: 'HTML',
      desc: 'Named HTML entities for safe embedding in HTML',
      refs: [
        { seq: '&amp;', desc: '& Ampersand' },
        { seq: '&lt;', desc: '< Less than' },
        { seq: '&gt;', desc: '> Greater than' },
        { seq: '&quot;', desc: '" Double quote' },
        { seq: '&#39;', desc: "' Single quote" },
        { seq: '&nbsp;', desc: 'Non-breaking space' },
      ],
      escape(s) {
        return s
          .replace(/&/g, '&amp;')
          .replace(/</g, '&lt;')
          .replace(/>/g, '&gt;')
          .replace(/"/g, '&quot;')
          .replace(/'/g, '&#39;');
      },
      unescape(s) {
        return s
          .replace(/&quot;/g, '"')
          .replace(/&#39;/g, "'")
          .replace(/&apos;/g, "'")
          .replace(/&lt;/g, '<')
          .replace(/&gt;/g, '>')
          .replace(/&nbsp;/g, '\u00a0')
          .replace(/&amp;/g, '&');
      },
    },
    {
      id: 'xml',
      label: 'XML',
      desc: 'XML entity encoding (five predefined entities)',
      refs: [
        { seq: '&amp;', desc: '& Ampersand' },
        { seq: '&lt;', desc: '< Less than' },
        { seq: '&gt;', desc: '> Greater than' },
        { seq: '&quot;', desc: '" Double quote' },
        { seq: '&apos;', desc: "' Apostrophe" },
      ],
      escape(s) {
        return s
          .replace(/&/g, '&amp;')
          .replace(/</g, '&lt;')
          .replace(/>/g, '&gt;')
          .replace(/"/g, '&quot;')
          .replace(/'/g, '&apos;');
      },
      unescape(s) {
        return s
          .replace(/&quot;/g, '"')
          .replace(/&apos;/g, "'")
          .replace(/&lt;/g, '<')
          .replace(/&gt;/g, '>')
          .replace(/&amp;/g, '&');
      },
    },
    {
      id: 'csv',
      label: 'CSV',
      desc: 'RFC 4180 CSV field quoting',
      refs: [
        { seq: '""', desc: 'Embedded double quote' },
        { seq: '"field"', desc: 'Quoted field wrapper' },
      ],
      escape(s) {
        if (/[",\r\n]/.test(s)) {
          return '"' + s.replace(/"/g, '""') + '"';
        }
        return s;
      },
      unescape(s) {
        const t = s.trim();
        if (t.startsWith('"') && t.endsWith('"')) {
          return t.slice(1, -1).replace(/""/g, '"');
        }
        return s;
      },
    },
    {
      id: 'regex',
      label: 'Regex',
      desc: 'Escapes all regex metacharacters so a string can be used as a literal pattern',
      refs: [
        { seq: '\\.', desc: 'Any char (dot)' },
        { seq: '\\*', desc: 'Quantifier *' },
        { seq: '\\+', desc: 'Quantifier +' },
        { seq: '\\?', desc: 'Quantifier ?' },
        { seq: '\\^', desc: 'Start anchor' },
        { seq: '\\$', desc: 'End anchor' },
        { seq: '\\(\\)', desc: 'Group' },
        { seq: '\\[\\]', desc: 'Character class' },
        { seq: '\\{\\}', desc: 'Quantifier braces' },
        { seq: '\\|', desc: 'Alternation' },
      ],
      escape(s) {
        return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
      },
      unescape(s) {
        return s.replace(/\\([.*+?^${}()|[\]\\])/g, '$1');
      },
    },
  ];

  /* ── State ── */
  let activeMode = MODES[0];

  /* ── DOM refs ── */
  const modeRow   = document.getElementById('escModeRow');
  const modeDesc  = document.getElementById('escModeDesc');
  const input     = document.getElementById('escInput');
  const output    = document.getElementById('escOutput');
  const bulkCheck = document.getElementById('escBulkMode');
  const statusEl  = document.getElementById('escStatus');
  const refGrid   = document.getElementById('escRefGrid');

  /* ── Build mode buttons ── */
  MODES.forEach(mode => {
    const btn = document.createElement('button');
    btn.className = 'esc-mode-btn' + (mode === activeMode ? ' active' : '');
    btn.textContent = mode.label;
    btn.addEventListener('click', () => {
      activeMode = mode;
      document.querySelectorAll('#esc-app .esc-mode-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      modeDesc.textContent = mode.desc;
      renderRef();
    });
    modeRow.appendChild(btn);
  });
  modeDesc.textContent = activeMode.desc;

  /* ── Render reference table ── */
  function renderRef() {
    refGrid.innerHTML = '';
    activeMode.refs.forEach(r => {
      const div = document.createElement('div');
      div.className = 'esc-ref-item';
      div.innerHTML = '<code>' + r.seq + '</code><span>' + r.desc + '</span>';
      refGrid.appendChild(div);
    });
  }
  renderRef();

  /* ── Process ── */
  function process(fn) {
    const text = input.value;
    if (!text) { showStatus('Paste some text first.', true); return; }
    try {
      if (bulkCheck.checked) {
        output.value = text.split('\n').map(line => fn(line)).join('\n');
      } else {
        output.value = fn(text);
      }
      showStatus('Done.');
    } catch (e) {
      showStatus('Error: ' + e.message, true);
    }
  }

  document.getElementById('escEscapeBtn').addEventListener('click', () => process(s => activeMode.escape(s)));
  document.getElementById('escUnescapeBtn').addEventListener('click', () => process(s => activeMode.unescape(s)));

  /* ── Copy ── */
  document.getElementById('escCopyBtn').addEventListener('click', () => {
    const text = output.value;
    if (!text) { showStatus('Nothing to copy.', true); return; }
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(() => showStatus('Copied to clipboard!')).catch(() => fallbackCopy(text));
    } else {
      fallbackCopy(text);
    }
  });

  function fallbackCopy(text) {
    output.select();
    document.execCommand('copy');
    showStatus('Copied to clipboard!');
  }

  /* ── Clear ── */
  document.getElementById('escClearBtn').addEventListener('click', () => {
    input.value = '';
    output.value = '';
    showStatus('Cleared.');
  });

  /* ── Status helper ── */
  let statusTimer;
  function showStatus(msg, isError) {
    statusEl.textContent = msg;
    statusEl.className = 'esc-status' + (isError ? ' error' : '');
    clearTimeout(statusTimer);
    statusTimer = setTimeout(() => { statusEl.textContent = ''; }, 3000);
  }
})();
</script>

</div>
