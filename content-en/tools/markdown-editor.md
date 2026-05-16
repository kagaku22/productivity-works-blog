---
title: "Markdown Editor - Live Preview"
date: 2025-05-16
description: "Free online Markdown editor with live preview. Toolbar for bold, italic, headings, links, images, code blocks, tables, and lists. Export as HTML or download .md file."
categories: ["Free Tools"]
tags: ["markdown editor", "markdown", "live preview", "wysiwyg", "markdown to html", "writing tool", "developer tool"]
slug: "markdown-editor"
cover:
  image: "/images/covers/markdown-editor.png"
  alt: "Markdown Editor with Live Preview"
ShowToc: false
---

<div id="me-app">

<style>
/* ── Reset & Root ─────────────────────────────────────── */
#me-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", sans-serif;
  max-width: 1200px;
  margin: 0 auto;
  color: #1e1b4b;
  --accent: #7c3aed;
  --accent-dk: #6d28d9;
  --accent-lt: #ede9fe;
  --bg: #f8f7ff;
  --surface: #ffffff;
  --border: #d8d3f0;
  --text: #1e1b4b;
  --text-muted: #6b7280;
  --code-bg: #f3f0ff;
  --preview-bg: #ffffff;
  --editor-bg: #fafafe;
  --status-bg: #f3f0ff;
  --btn-ghost: #ede9fe;
  --btn-ghost-text: #5b21b6;
  --toolbar-bg: #f5f3ff;
  --shadow: 0 2px 12px rgba(124,58,237,0.10);
  --radius: 10px;
}
#me-app * { box-sizing: border-box; }

/* ── Dark theme ───────────────────────────────────────── */
#me-app.me-dark {
  --bg: #0f0e1a;
  --surface: #1a1828;
  --border: #3b3660;
  --text: #e5e1ff;
  --text-muted: #9d97c4;
  --code-bg: #2a2540;
  --preview-bg: #1a1828;
  --editor-bg: #15132a;
  --status-bg: #1a1828;
  --btn-ghost: #2a2540;
  --btn-ghost-text: #c4b5fd;
  --toolbar-bg: #1a1828;
  --shadow: 0 2px 12px rgba(0,0,0,0.40);
  color: var(--text);
}
#me-app.me-dark #me-editor { color: #e5e1ff; background: var(--editor-bg); }
#me-app.me-dark #me-fmt-toolbar { background: var(--toolbar-bg); border-color: var(--border); }

/* ── Top Bar ──────────────────────────────────────────── */
#me-topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 8px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius) var(--radius) 0 0;
  padding: 10px 14px;
  box-shadow: var(--shadow);
}
#me-title {
  font-weight: 700;
  font-size: 1rem;
  color: var(--accent);
  letter-spacing: -0.01em;
}
#me-topbar-btns {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

/* ── Formatting Toolbar ───────────────────────────────── */
#me-fmt-toolbar {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 3px;
  background: var(--toolbar-bg);
  border-left: 1px solid var(--border);
  border-right: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  padding: 7px 10px;
}
.me-sep {
  width: 1px;
  height: 20px;
  background: var(--border);
  margin: 0 4px;
  flex-shrink: 0;
}
.me-fmt-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 30px;
  height: 28px;
  padding: 0 7px;
  border: 1px solid var(--border);
  border-radius: 5px;
  background: var(--surface);
  color: var(--text);
  font-size: 0.8rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.12s, border-color 0.12s, transform 0.1s;
  white-space: nowrap;
  line-height: 1;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}
.me-fmt-btn:hover {
  background: var(--accent-lt);
  border-color: var(--accent);
  color: var(--accent);
}
.me-fmt-btn:active { transform: scale(0.93); }

/* ── Generic Buttons ──────────────────────────────────── */
.me-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 6px 13px;
  border: none;
  border-radius: 6px;
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  line-height: 1.2;
  white-space: nowrap;
}
.me-btn:active { transform: scale(0.96); }
.me-btn-primary {
  background: var(--accent);
  color: #fff;
  box-shadow: 0 1px 4px rgba(124,58,237,0.25);
}
.me-btn-primary:hover { background: var(--accent-dk); }
.me-btn-ghost {
  background: var(--btn-ghost);
  color: var(--btn-ghost-text);
}
.me-btn-ghost:hover { filter: brightness(0.95); }
.me-btn-success {
  background: #d1fae5;
  color: #065f46;
}
.me-btn-success:hover { background: #a7f3d0; }
.me-dark .me-btn-success { background: #064e3b; color: #6ee7b7; }

/* ── Split Pane ───────────────────────────────────────── */
#me-split {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border-left: 1px solid var(--border);
  border-right: 1px solid var(--border);
  min-height: 500px;
}
@media (max-width: 680px) {
  #me-split { grid-template-columns: 1fr; }
}

/* ── Pane Labels ──────────────────────────────────────── */
.me-pane-label {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  color: var(--text-muted);
  padding: 5px 14px 4px;
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  gap: 6px;
}
#me-editor-pane {
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
}
#me-preview-pane {
  display: flex;
  flex-direction: column;
  background: var(--preview-bg);
}
@media (max-width: 680px) {
  #me-editor-pane { border-right: none; border-bottom: 1px solid var(--border); }
}

/* ── Editor ───────────────────────────────────────────── */
#me-editor-wrap {
  position: relative;
  flex: 1;
  display: flex;
}
#me-line-nums {
  padding: 14px 8px 14px 10px;
  font-size: 0.82rem;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  line-height: 1.65;
  color: var(--text-muted);
  background: var(--editor-bg);
  border-right: 1px solid var(--border);
  text-align: right;
  user-select: none;
  min-width: 36px;
  overflow: hidden;
  white-space: pre;
}
#me-editor {
  flex: 1;
  width: 100%;
  padding: 14px 14px 14px 12px;
  font-size: 0.9rem;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  line-height: 1.65;
  border: none;
  outline: none;
  resize: none;
  background: var(--editor-bg);
  color: var(--text);
  min-height: 460px;
  tab-size: 2;
}
#me-editor::placeholder { color: var(--text-muted); opacity: 0.6; }

/* ── Preview ──────────────────────────────────────────── */
#me-preview {
  flex: 1;
  padding: 18px 20px;
  overflow-y: auto;
  background: var(--preview-bg);
  color: var(--text);
  font-size: 0.95rem;
  line-height: 1.75;
  min-height: 460px;
}

/* Rendered markdown styles */
#me-preview h1, #me-preview h2, #me-preview h3,
#me-preview h4, #me-preview h5, #me-preview h6 {
  color: var(--accent);
  margin: 1.1em 0 0.4em;
  line-height: 1.25;
  font-weight: 700;
}
#me-preview h1 { font-size: 1.65em; border-bottom: 2px solid var(--border); padding-bottom: 0.2em; }
#me-preview h2 { font-size: 1.35em; border-bottom: 1px solid var(--border); padding-bottom: 0.15em; }
#me-preview h3 { font-size: 1.15em; }
#me-preview h4 { font-size: 1em; }
#me-preview h5 { font-size: 0.9em; }
#me-preview h6 { font-size: 0.85em; color: var(--text-muted); }
#me-preview p { margin: 0.7em 0; }
#me-preview a { color: var(--accent); text-decoration: underline; }
#me-preview a:hover { color: var(--accent-dk); }
#me-preview strong { font-weight: 700; }
#me-preview em { font-style: italic; }
#me-preview del { text-decoration: line-through; color: var(--text-muted); }
#me-preview code {
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.88em;
  background: var(--code-bg);
  color: #9333ea;
  padding: 0.15em 0.45em;
  border-radius: 4px;
  border: 1px solid var(--border);
}
#me-preview pre {
  background: var(--code-bg);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 14px 16px;
  overflow-x: auto;
  margin: 1em 0;
}
#me-preview pre code {
  background: none;
  border: none;
  padding: 0;
  color: var(--text);
  font-size: 0.87em;
  line-height: 1.6;
}
#me-preview pre .kw { color: #9333ea; font-weight: 700; }
#me-preview pre .str { color: #059669; }
#me-preview pre .cm { color: #6b7280; font-style: italic; }
#me-preview pre .nm { color: #b45309; }
.me-dark #me-preview pre .kw { color: #c084fc; }
.me-dark #me-preview pre .str { color: #34d399; }
.me-dark #me-preview pre .cm { color: #9ca3af; }
.me-dark #me-preview pre .nm { color: #fbbf24; }
#me-preview blockquote {
  border-left: 4px solid var(--accent);
  margin: 1em 0;
  padding: 8px 16px;
  background: var(--code-bg);
  border-radius: 0 6px 6px 0;
  color: var(--text-muted);
}
#me-preview blockquote p { margin: 0; }
#me-preview ul, #me-preview ol { padding-left: 1.6em; margin: 0.6em 0; }
#me-preview li { margin: 0.25em 0; }
#me-preview ul li { list-style-type: disc; }
#me-preview ol li { list-style-type: decimal; }
#me-preview hr { border: none; border-top: 2px solid var(--border); margin: 1.5em 0; }
#me-preview img { max-width: 100%; border-radius: 6px; margin: 0.5em 0; }
#me-preview table {
  border-collapse: collapse;
  width: 100%;
  margin: 1em 0;
  font-size: 0.92em;
}
#me-preview th {
  background: var(--accent-lt);
  color: var(--accent);
  font-weight: 700;
  padding: 8px 12px;
  border: 1px solid var(--border);
  text-align: left;
}
.me-dark #me-preview th { background: #2a2540; color: #c4b5fd; }
#me-preview td { padding: 7px 12px; border: 1px solid var(--border); }
#me-preview tr:nth-child(even) td { background: var(--code-bg); }

/* ── Status Bar ───────────────────────────────────────── */
#me-status {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 14px;
  background: var(--status-bg);
  border: 1px solid var(--border);
  border-top: none;
  border-radius: 0 0 var(--radius) var(--radius);
  padding: 7px 16px;
  font-size: 0.79rem;
  color: var(--text-muted);
}
.me-stat { display: inline-flex; align-items: center; gap: 4px; }
.me-stat-val { font-weight: 700; color: var(--accent); }
#me-saved-msg {
  margin-left: auto;
  color: #059669;
  font-weight: 600;
  font-size: 0.77rem;
  opacity: 0;
  transition: opacity 0.3s;
}
#me-saved-msg.me-show { opacity: 1; }

/* ── Fullscreen ───────────────────────────────────────── */
#me-app.me-fullscreen {
  position: fixed;
  inset: 0;
  z-index: 9999;
  max-width: 100%;
  background: var(--bg);
  padding: 0;
  overflow: auto;
  border-radius: 0;
}
#me-app.me-fullscreen #me-split { min-height: calc(100vh - 160px); }

/* ── Related Links ────────────────────────────────────── */
#me-related {
  margin-top: 20px;
  padding: 12px 16px;
  background: var(--status-bg);
  border: 1px solid var(--border);
  border-radius: 8px;
  font-size: 0.88rem;
  color: var(--text-muted);
  line-height: 1.7;
}
#me-related strong { color: var(--text); }
#me-related a { color: var(--accent); font-weight: 600; text-decoration: none; }
#me-related a:hover { text-decoration: underline; }
</style>

<!-- Top Bar -->
<div id="me-topbar">
  <span id="me-title">&#9998; Markdown Editor</span>
  <div id="me-topbar-btns">
    <button class="me-btn me-btn-ghost" onclick="meLoadSample()">Load Sample</button>
    <button class="me-btn me-btn-ghost" onclick="meClear()">Clear</button>
    <button class="me-btn me-btn-ghost" onclick="meToggleTheme()">&#9790; Dark</button>
    <button class="me-btn me-btn-ghost" onclick="meToggleFullscreen()">&#x26F6; Fullscreen</button>
    <button class="me-btn me-btn-ghost" onclick="meCopyHTML()">Copy HTML</button>
    <button class="me-btn me-btn-success" onclick="meDownloadMd()">&#11015; .md</button>
    <button class="me-btn me-btn-primary" onclick="meExportHTML()">Export .html</button>
  </div>
</div>

<!-- Formatting Toolbar -->
<div id="me-fmt-toolbar">
  <button class="me-fmt-btn" title="Bold (Ctrl+B)" onclick="meFmt('bold')"><strong>B</strong></button>
  <button class="me-fmt-btn" title="Italic (Ctrl+I)" onclick="meFmt('italic')"><em>I</em></button>
  <button class="me-fmt-btn" title="Strikethrough" onclick="meFmt('strike')"><del>S</del></button>
  <div class="me-sep"></div>
  <button class="me-fmt-btn" title="Heading 1" onclick="meFmt('h1')">H1</button>
  <button class="me-fmt-btn" title="Heading 2" onclick="meFmt('h2')">H2</button>
  <button class="me-fmt-btn" title="Heading 3" onclick="meFmt('h3')">H3</button>
  <div class="me-sep"></div>
  <button class="me-fmt-btn" title="Link" onclick="meFmt('link')">&#128279;</button>
  <button class="me-fmt-btn" title="Image" onclick="meFmt('image')">&#128247;</button>
  <div class="me-sep"></div>
  <button class="me-fmt-btn" title="Inline Code" onclick="meFmt('code')">`c`</button>
  <button class="me-fmt-btn" title="Code Block" onclick="meFmt('codeblock')">```</button>
  <button class="me-fmt-btn" title="Blockquote" onclick="meFmt('quote')">&gt;</button>
  <div class="me-sep"></div>
  <button class="me-fmt-btn" title="Unordered List" onclick="meFmt('ul')">&#8226; ul</button>
  <button class="me-fmt-btn" title="Ordered List" onclick="meFmt('ol')">1. ol</button>
  <button class="me-fmt-btn" title="Task List" onclick="meFmt('task')">&#9744;</button>
  <div class="me-sep"></div>
  <button class="me-fmt-btn" title="Table" onclick="meFmt('table')">&#9776;</button>
  <button class="me-fmt-btn" title="Horizontal Rule" onclick="meFmt('hr')">&#8212;</button>
</div>

<!-- Split Pane -->
<div id="me-split">
  <div id="me-editor-pane">
    <div class="me-pane-label">&#9998; Editor</div>
    <div id="me-editor-wrap">
      <div id="me-line-nums">1</div>
      <textarea id="me-editor" placeholder="Start writing Markdown..." spellcheck="false"></textarea>
    </div>
  </div>
  <div id="me-preview-pane">
    <div class="me-pane-label">&#128065; Preview</div>
    <div id="me-preview"></div>
  </div>
</div>

<!-- Status Bar -->
<div id="me-status">
  <span class="me-stat">Words: <span class="me-stat-val" id="me-stat-words">0</span></span>
  <span class="me-stat">Chars: <span class="me-stat-val" id="me-stat-chars">0</span></span>
  <span class="me-stat">Lines: <span class="me-stat-val" id="me-stat-lines">0</span></span>
  <span class="me-stat">Read: <span class="me-stat-val" id="me-stat-read">0 min</span></span>
  <span id="me-saved-msg">&#10003; Autosaved</span>
</div>

<!-- Related Tools -->
<div id="me-related">
  <strong>Related Markdown Tools:</strong>
  <a href="/tools/markdown-preview/">Markdown Preview</a> &nbsp;&middot;&nbsp;
  <a href="/tools/markdown-table-generator/">Markdown Table Generator</a> &nbsp;&middot;&nbsp;
  <a href="/tools/markdown-toc-generator/">Markdown TOC Generator</a>
</div>

</div><!-- /#me-app -->

<script>
(function() {
  'use strict';

  /* ── Sample Content ───────────────────────────────────── */
  var SAMPLE = [
    '# Welcome to Markdown Editor',
    '',
    'A **full-featured** split-pane editor with live preview. Use the toolbar or keyboard shortcuts to format your text.',
    '',
    '## Keyboard Shortcuts',
    '',
    '| Shortcut | Action |',
    '|----------|--------|',
    '| `Ctrl+B` | Bold |',
    '| `Ctrl+I` | Italic |',
    '| `Tab` | Indent |',
    '',
    '## Text Formatting',
    '',
    '**Bold text**, *italic text*, ~~strikethrough~~, and `inline code`.',
    '',
    '## Headings',
    '',
    '# H1 Heading',
    '## H2 Heading',
    '### H3 Heading',
    '',
    '## Lists',
    '',
    '- Unordered item one',
    '- Unordered item two',
    '  - Nested item',
    '',
    '1. First ordered item',
    '2. Second ordered item',
    '3. Third ordered item',
    '',
    '- [x] Completed task',
    '- [ ] Pending task',
    '',
    '## Code',
    '',
    '```javascript',
    'function greet(name) {',
    '  // Say hello',
    '  return `Hello, ${name}!`;',
    '}',
    'console.log(greet("World"));',
    '```',
    '',
    '## Blockquote',
    '',
    '> "The best writing tool is the one you actually use."',
    '> — Productivity Proverb',
    '',
    '## Link & Image',
    '',
    '[Visit Example](https://example.com)',
    '',
    '![Placeholder](https://via.placeholder.com/400x120?text=Markdown+Editor)',
    '',
    '## Horizontal Rule',
    '',
    '---',
    '',
    'Happy writing! Your work is **autosaved** to localStorage.'
  ].join('\n');

  /* ── Markdown Parser ──────────────────────────────────── */
  function parseMarkdown(md) {
    var lines = md.split('\n');
    var out = '';
    var i = 0;
    var inFence = false;
    var fenceLang = '';
    var fenceLines = [];

    while (i < lines.length) {
      var line = lines[i];

      // Fenced code block
      var fenceMatch = line.match(/^(`{3,}|~{3,})\s*(\w*)/);
      if (fenceMatch && !inFence) {
        inFence = true;
        fenceLang = fenceMatch[2] || '';
        fenceLines = [];
        i++; continue;
      }
      if (inFence) {
        if (/^(`{3,}|~{3,})/.test(line)) {
          var cc = fenceLines.map(escapeHtml).join('\n');
          cc = highlightCode(cc, fenceLang);
          out += '<pre><code' + (fenceLang ? ' class="lang-' + escapeHtml(fenceLang) + '"' : '') + '>' + cc + '</code></pre>\n';
          inFence = false; fenceLang = ''; fenceLines = [];
        } else { fenceLines.push(line); }
        i++; continue;
      }

      // Setext h1
      if (i + 1 < lines.length && /^=+\s*$/.test(lines[i+1]) && line.trim()) {
        out += '<h1>' + inlineMd(line.trim()) + '</h1>\n'; i += 2; continue;
      }
      // Setext h2
      if (i + 1 < lines.length && /^-+\s*$/.test(lines[i+1]) && line.trim() && !/^\s*[-*+] /.test(line)) {
        out += '<h2>' + inlineMd(line.trim()) + '</h2>\n'; i += 2; continue;
      }

      // ATX headings
      var hm = line.match(/^(#{1,6})\s+(.+?)(?:\s+#+)?$/);
      if (hm) {
        var lvl = hm[1].length;
        out += '<h' + lvl + '>' + inlineMd(hm[2].trim()) + '</h' + lvl + '>\n';
        i++; continue;
      }

      // HR
      if (/^(\*{3,}|-{3,}|_{3,})\s*$/.test(line.trim())) {
        out += '<hr>\n'; i++; continue;
      }

      // Blockquote
      if (/^>\s?/.test(line)) {
        var bq = [];
        while (i < lines.length && /^>\s?/.test(lines[i])) {
          bq.push(lines[i].replace(/^>\s?/, '')); i++;
        }
        out += '<blockquote><p>' + inlineMd(bq.join('\n')) + '</p></blockquote>\n';
        continue;
      }

      // Table
      if (/\|/.test(line) && i + 1 < lines.length && /^\|?[\s:|-]+\|/.test(lines[i+1])) {
        var tbl = [];
        while (i < lines.length && /\|/.test(lines[i])) { tbl.push(lines[i]); i++; }
        out += parseTable(tbl); continue;
      }

      // Task list (before ul)
      if (/^\s*[-*+] \[[ xX]\]/.test(line)) {
        var tl = [];
        while (i < lines.length && /^\s*[-*+] \[[ xX]\]/.test(lines[i])) {
          tl.push(lines[i]); i++;
        }
        out += '<ul class="me-tasklist">' + tl.map(function(l) {
          var checked = /\[x\]/i.test(l);
          var txt = l.replace(/^\s*[-*+] \[[ xX]\]\s*/, '');
          return '<li><input type="checkbox" disabled' + (checked ? ' checked' : '') + '> ' + inlineMd(txt) + '</li>';
        }).join('') + '</ul>\n';
        continue;
      }

      // UL
      if (/^(\s*)[-*+] /.test(line)) {
        var ul = [];
        while (i < lines.length && /^(\s*)[-*+] /.test(lines[i])) { ul.push(lines[i]); i++; }
        out += '<ul>' + ul.map(function(l) {
          return '<li>' + inlineMd(l.replace(/^\s*[-*+] /, '')) + '</li>';
        }).join('') + '</ul>\n';
        continue;
      }

      // OL
      if (/^\d+\.\s/.test(line)) {
        var ol = [];
        while (i < lines.length && /^\d+\.\s/.test(lines[i])) { ol.push(lines[i]); i++; }
        out += '<ol>' + ol.map(function(l) {
          return '<li>' + inlineMd(l.replace(/^\d+\.\s/, '')) + '</li>';
        }).join('') + '</ol>\n';
        continue;
      }

      // Blank
      if (line.trim() === '') { out += '\n'; i++; continue; }

      // Paragraph
      var pl = [];
      while (i < lines.length && lines[i].trim() !== ''
        && !/^#{1,6}\s/.test(lines[i])
        && !/^(\*{3,}|-{3,}|_{3,})\s*$/.test(lines[i].trim())
        && !/^>\s?/.test(lines[i])
        && !/^\s*[-*+] /.test(lines[i])
        && !/^\d+\.\s/.test(lines[i])
        && !/\|/.test(lines[i])
        && !/^(`{3,}|~{3,})/.test(lines[i])) {
        pl.push(lines[i]); i++;
      }
      if (pl.length) out += '<p>' + inlineMd(pl.join(' ')) + '</p>\n';
    }

    if (inFence && fenceLines.length) {
      out += '<pre><code>' + fenceLines.map(escapeHtml).join('\n') + '</code></pre>\n';
    }
    return out;
  }

  function parseTable(lines) {
    if (lines.length < 2) return '';
    var hCells = splitRow(lines[0]);
    var alignRow = lines[1];
    var aligns = splitRow(alignRow).map(function(c) {
      if (/^:-+:$/.test(c.trim())) return 'center';
      if (/^-+:$/.test(c.trim())) return 'right';
      return 'left';
    });
    var html = '<table><thead><tr>';
    hCells.forEach(function(c, idx) {
      html += '<th style="text-align:' + (aligns[idx] || 'left') + '">' + inlineMd(c) + '</th>';
    });
    html += '</tr></thead><tbody>';
    lines.slice(2).forEach(function(row) {
      var cells = splitRow(row);
      html += '<tr>';
      cells.forEach(function(c, idx) {
        html += '<td style="text-align:' + (aligns[idx] || 'left') + '">' + inlineMd(c) + '</td>';
      });
      html += '</tr>';
    });
    html += '</tbody></table>\n';
    return html;
  }

  function splitRow(row) {
    return row.replace(/^\||\|$/g, '').split('|').map(function(c) { return c.trim(); });
  }

  /* ── Inline Markdown ──────────────────────────────────── */
  function inlineMd(text) {
    // Images before links
    text = text.replace(/!\[([^\]]*)\]\(([^)]+)\)/g, function(_, alt, src) {
      return '<img src="' + escapeAttr(src) + '" alt="' + escapeAttr(alt) + '">';
    });
    // Links
    text = text.replace(/\[([^\]]+)\]\(([^)]+)\)/g, function(_, label, href) {
      return '<a href="' + escapeAttr(href) + '">' + escapeHtml(label) + '</a>';
    });
    // Autolinks
    text = text.replace(/<(https?:\/\/[^>]+)>/g, function(_, url) {
      return '<a href="' + escapeAttr(url) + '">' + escapeHtml(url) + '</a>';
    });
    // Inline code (before bold/italic)
    text = text.replace(/`([^`]+)`/g, function(_, c) {
      return '<code>' + escapeHtml(c) + '</code>';
    });
    // Bold+italic
    text = text.replace(/\*\*\*(.+?)\*\*\*/g, '<strong><em>$1</em></strong>');
    text = text.replace(/___(.+?)___/g, '<strong><em>$1</em></strong>');
    // Bold
    text = text.replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
    text = text.replace(/__(.+?)__/g, '<strong>$1</strong>');
    // Italic
    text = text.replace(/\*(.+?)\*/g, '<em>$1</em>');
    text = text.replace(/_(.+?)_/g, '<em>$1</em>');
    // Strikethrough
    text = text.replace(/~~(.+?)~~/g, '<del>$1</del>');
    // Hard line break
    text = text.replace(/  $/g, '<br>');
    return text;
  }

  /* ── Syntax Highlighting ──────────────────────────────── */
  function highlightCode(code, lang) {
    if (!lang) return code;
    var l = lang.toLowerCase();
    if (l === 'javascript' || l === 'js' || l === 'typescript' || l === 'ts') return hlJS(code);
    if (l === 'python' || l === 'py') return hlPy(code);
    if (l === 'html' || l === 'xml') return hlHTML(code);
    if (l === 'css') return hlCSS(code);
    if (l === 'bash' || l === 'sh' || l === 'shell') return hlBash(code);
    return code;
  }
  function tok(cls, text) { return '<span class="' + cls + '">' + text + '</span>'; }
  function hlJS(code) {
    var kw = /\b(const|let|var|function|return|if|else|for|while|do|switch|case|break|continue|new|class|extends|import|export|default|async|await|try|catch|finally|typeof|instanceof|in|of|this|null|undefined|true|false|void|delete|throw)\b/g;
    return code
      .replace(/(\/\/.*$|\/\*[\s\S]*?\*\/)/gm, function(m) { return tok('cm', m); })
      .replace(/(["'`])(?:\\[\s\S]|(?!\1)[^\\])*?\1/g, function(m) { return tok('str', m); })
      .replace(kw, function(m) { return tok('kw', m); })
      .replace(/\b(\d+\.?\d*)\b/g, function(m) { return tok('nm', m); });
  }
  function hlPy(code) {
    var kw = /\b(def|class|import|from|return|if|elif|else|for|while|in|not|and|or|is|None|True|False|pass|break|continue|try|except|finally|with|as|lambda|yield|async|await|raise|del|global|nonlocal|print)\b/g;
    return code
      .replace(/(#.*)$/gm, function(m) { return tok('cm', m); })
      .replace(/("""[\s\S]*?"""|'''[\s\S]*?'''|"(?:\\.|[^"\\])*"|'(?:\\.|[^'\\])*')/g, function(m) { return tok('str', m); })
      .replace(kw, function(m) { return tok('kw', m); })
      .replace(/\b(\d+\.?\d*)\b/g, function(m) { return tok('nm', m); });
  }
  function hlHTML(code) {
    return code
      .replace(/(&lt;!--[\s\S]*?--&gt;)/g, function(m) { return tok('cm', m); })
      .replace(/(&lt;\/?[\w]+[^&]*?&gt;)/g, function(m) { return tok('kw', m); });
  }
  function hlCSS(code) {
    return code
      .replace(/(\/\*[\s\S]*?\*\/)/g, function(m) { return tok('cm', m); })
      .replace(/(["'])(?:\\.|[^\\])*?\1/g, function(m) { return tok('str', m); })
      .replace(/^([^{]+)(?=\{)/gm, function(m) { return tok('kw', m); })
      .replace(/(\s)([\w-]+)(?=\s*:)/g, function(_, sp, p) { return sp + tok('nm', p); });
  }
  function hlBash(code) {
    var kw = /\b(echo|cd|ls|mkdir|rm|mv|cp|cat|grep|sed|awk|curl|wget|git|npm|yarn|pip|export|source|if|then|else|fi|for|do|done|while|case|esac|function|return|exit)\b/g;
    return code
      .replace(/(#.*)$/gm, function(m) { return tok('cm', m); })
      .replace(/(["'])(?:\\.|[^\\])*?\1/g, function(m) { return tok('str', m); })
      .replace(kw, function(m) { return tok('kw', m); });
  }

  /* ── Utilities ────────────────────────────────────────── */
  function escapeHtml(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }
  function escapeAttr(s) { return String(s).replace(/"/g,'&quot;'); }

  /* ── Stats ────────────────────────────────────────────── */
  function updateStats(text) {
    var words = text.trim() ? text.trim().split(/\s+/).length : 0;
    var chars = text.length;
    var lines = text ? text.split('\n').length : 0;
    var readMin = Math.max(1, Math.ceil(words / 200));
    document.getElementById('me-stat-words').textContent = words.toLocaleString();
    document.getElementById('me-stat-chars').textContent = chars.toLocaleString();
    document.getElementById('me-stat-lines').textContent = lines.toLocaleString();
    document.getElementById('me-stat-read').textContent = readMin + ' min';
  }

  /* ── Line Numbers ─────────────────────────────────────── */
  function updateLineNums(text) {
    var count = text ? text.split('\n').length : 1;
    var nums = '';
    for (var n = 1; n <= count; n++) nums += n + '\n';
    document.getElementById('me-line-nums').textContent = nums;
  }

  /* ── Render ───────────────────────────────────────────── */
  function render() {
    var text = document.getElementById('me-editor').value;
    document.getElementById('me-preview').innerHTML = parseMarkdown(text);
    updateStats(text);
    updateLineNums(text);
  }

  /* ── Autosave ─────────────────────────────────────────── */
  var saveTimer = null;
  var SAVE_KEY = 'me-content-en';
  function scheduleSave() {
    clearTimeout(saveTimer);
    saveTimer = setTimeout(function() {
      try {
        localStorage.setItem(SAVE_KEY, document.getElementById('me-editor').value);
        var msg = document.getElementById('me-saved-msg');
        msg.classList.add('me-show');
        setTimeout(function() { msg.classList.remove('me-show'); }, 1800);
      } catch(e) {}
    }, 800);
  }

  /* ── Formatting Toolbar Actions ───────────────────────── */
  function getEditor() { return document.getElementById('me-editor'); }

  function wrapSelection(before, after, placeholder) {
    var ta = getEditor();
    var start = ta.selectionStart;
    var end = ta.selectionEnd;
    var sel = ta.value.substring(start, end) || placeholder || '';
    var replacement = before + sel + after;
    ta.value = ta.value.substring(0, start) + replacement + ta.value.substring(end);
    ta.selectionStart = start + before.length;
    ta.selectionEnd = start + before.length + sel.length;
    ta.focus();
    render(); scheduleSave();
  }

  function insertLinePrefix(prefix) {
    var ta = getEditor();
    var start = ta.selectionStart;
    var lineStart = ta.value.lastIndexOf('\n', start - 1) + 1;
    var lineEnd = ta.value.indexOf('\n', start);
    if (lineEnd === -1) lineEnd = ta.value.length;
    var line = ta.value.substring(lineStart, lineEnd);
    var newLine = prefix + line;
    ta.value = ta.value.substring(0, lineStart) + newLine + ta.value.substring(lineEnd);
    ta.selectionStart = ta.selectionEnd = lineStart + newLine.length;
    ta.focus();
    render(); scheduleSave();
  }

  function insertBlock(text) {
    var ta = getEditor();
    var start = ta.selectionStart;
    var before = ta.value.substring(0, start);
    var after = ta.value.substring(start);
    // Ensure blank line before block
    var prefix = (before.length > 0 && !before.endsWith('\n\n')) ? (before.endsWith('\n') ? '\n' : '\n\n') : '';
    var inserted = prefix + text + '\n';
    ta.value = before + inserted + after;
    ta.selectionStart = ta.selectionEnd = before.length + inserted.length;
    ta.focus();
    render(); scheduleSave();
  }

  window.meFmt = function(type) {
    switch (type) {
      case 'bold':      wrapSelection('**', '**', 'bold text'); break;
      case 'italic':    wrapSelection('*', '*', 'italic text'); break;
      case 'strike':    wrapSelection('~~', '~~', 'strikethrough'); break;
      case 'code':      wrapSelection('`', '`', 'code'); break;
      case 'h1':        insertLinePrefix('# '); break;
      case 'h2':        insertLinePrefix('## '); break;
      case 'h3':        insertLinePrefix('### '); break;
      case 'quote':     insertLinePrefix('> '); break;
      case 'ul':        insertLinePrefix('- '); break;
      case 'ol':        insertLinePrefix('1. '); break;
      case 'task':      insertLinePrefix('- [ ] '); break;
      case 'hr':        insertBlock('---'); break;
      case 'link':
        var url = window.prompt('Enter URL:', 'https://');
        if (url) wrapSelection('[', '](' + url + ')', 'link text');
        break;
      case 'image':
        var imgUrl = window.prompt('Enter image URL:', 'https://');
        var altText = imgUrl ? (window.prompt('Enter alt text:', 'image') || 'image') : null;
        if (imgUrl) insertBlock('![' + altText + '](' + imgUrl + ')');
        break;
      case 'codeblock':
        var lang = window.prompt('Language (e.g. javascript):', '') || '';
        insertBlock('```' + lang + '\n' + (getEditor().value.substring(getEditor().selectionStart, getEditor().selectionEnd) || 'code here') + '\n```');
        break;
      case 'table':
        insertBlock('| Column 1 | Column 2 | Column 3 |\n|----------|----------|----------|\n| Cell 1   | Cell 2   | Cell 3   |\n| Cell 4   | Cell 5   | Cell 6   |');
        break;
    }
  };

  /* ── Keyboard Shortcuts ───────────────────────────────── */
  document.getElementById('me-editor').addEventListener('keydown', function(e) {
    if ((e.ctrlKey || e.metaKey) && e.key === 'b') { e.preventDefault(); meFmt('bold'); }
    if ((e.ctrlKey || e.metaKey) && e.key === 'i') { e.preventDefault(); meFmt('italic'); }
    // Tab key: insert spaces
    if (e.key === 'Tab') {
      e.preventDefault();
      var ta = this;
      var s = ta.selectionStart;
      ta.value = ta.value.substring(0, s) + '  ' + ta.value.substring(ta.selectionEnd);
      ta.selectionStart = ta.selectionEnd = s + 2;
      render(); scheduleSave();
    }
  });

  /* ── Theme ────────────────────────────────────────────── */
  var darkMode = false;
  window.meToggleTheme = function() {
    darkMode = !darkMode;
    var app = document.getElementById('me-app');
    var btn = document.querySelector('#me-topbar-btns .me-btn-ghost');
    if (darkMode) {
      app.classList.add('me-dark');
    } else {
      app.classList.remove('me-dark');
    }
  };

  /* ── Fullscreen ───────────────────────────────────────── */
  window.meToggleFullscreen = function() {
    document.getElementById('me-app').classList.toggle('me-fullscreen');
  };

  /* ── Copy HTML ────────────────────────────────────────── */
  window.meCopyHTML = function() {
    var html = document.getElementById('me-preview').innerHTML;
    var msg = document.getElementById('me-saved-msg');
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(html).then(function() {
        msg.textContent = 'HTML copied!';
        msg.classList.add('me-show');
        setTimeout(function() { msg.textContent = '\u2713 Autosaved'; msg.classList.remove('me-show'); }, 2000);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = html; ta.style.position = 'fixed'; ta.style.opacity = '0';
      document.body.appendChild(ta); ta.select(); document.execCommand('copy');
      document.body.removeChild(ta);
      msg.textContent = 'HTML copied!'; msg.classList.add('me-show');
      setTimeout(function() { msg.textContent = '\u2713 Autosaved'; msg.classList.remove('me-show'); }, 2000);
    }
  };

  /* ── Download .md ─────────────────────────────────────── */
  window.meDownloadMd = function() {
    var content = document.getElementById('me-editor').value;
    var blob = new Blob([content], { type: 'text/markdown' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url; a.download = 'document.md';
    document.body.appendChild(a); a.click();
    setTimeout(function() { document.body.removeChild(a); URL.revokeObjectURL(url); }, 100);
  };

  /* ── Export HTML ──────────────────────────────────────── */
  window.meExportHTML = function() {
    var previewHtml = document.getElementById('me-preview').innerHTML;
    var full = '<!DOCTYPE html>\n<html lang="en">\n<head>\n<meta charset="UTF-8">\n'
      + '<meta name="viewport" content="width=device-width, initial-scale=1.0">\n'
      + '<title>Exported Markdown</title>\n<style>\n'
      + 'body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;max-width:860px;margin:40px auto;padding:0 20px;color:#1e1b4b;line-height:1.75}\n'
      + 'h1,h2,h3,h4,h5,h6{color:#7c3aed}\n'
      + 'h1,h2{border-bottom:1px solid #d8d3f0;padding-bottom:.2em}\n'
      + 'code{background:#f3f0ff;color:#9333ea;padding:.15em .45em;border-radius:4px;font-size:.88em}\n'
      + 'pre{background:#f3f0ff;border-radius:8px;padding:14px 16px;overflow-x:auto}\n'
      + 'pre code{background:none;color:#1e1b4b}\n'
      + 'blockquote{border-left:4px solid #7c3aed;padding:8px 16px;background:#f3f0ff;border-radius:0 6px 6px 0;color:#6b7280;margin:1em 0}\n'
      + 'table{border-collapse:collapse;width:100%;margin:1em 0}\n'
      + 'th{background:#ede9fe;color:#7c3aed;padding:8px 12px;border:1px solid #d8d3f0;text-align:left}\n'
      + 'td{padding:7px 12px;border:1px solid #d8d3f0}\n'
      + 'tr:nth-child(even) td{background:#f3f0ff}\n'
      + 'img{max-width:100%;border-radius:6px}\n'
      + 'hr{border:none;border-top:2px solid #d8d3f0;margin:1.5em 0}\n'
      + 'a{color:#7c3aed}\n'
      + '</style>\n</head>\n<body>\n'
      + previewHtml + '\n</body>\n</html>';
    var blob = new Blob([full], { type: 'text/html' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url; a.download = 'markdown-export.html';
    document.body.appendChild(a); a.click();
    setTimeout(function() { document.body.removeChild(a); URL.revokeObjectURL(url); }, 100);
  };

  /* ── Sample / Clear ───────────────────────────────────── */
  window.meLoadSample = function() {
    document.getElementById('me-editor').value = SAMPLE;
    render(); scheduleSave();
  };
  window.meClear = function() {
    if (window.confirm('Clear all content?')) {
      document.getElementById('me-editor').value = '';
      render(); scheduleSave();
    }
  };

  /* ── Sync scroll (preview tracks editor) ─────────────── */
  document.getElementById('me-editor').addEventListener('scroll', function() {
    var ratio = this.scrollTop / (this.scrollHeight - this.clientHeight || 1);
    var preview = document.getElementById('me-preview');
    preview.scrollTop = ratio * (preview.scrollHeight - preview.clientHeight);
  });

  /* ── Init ─────────────────────────────────────────────── */
  var editor = document.getElementById('me-editor');
  editor.addEventListener('input', function() { render(); scheduleSave(); });

  // Load from localStorage or sample
  var saved = '';
  try { saved = localStorage.getItem(SAVE_KEY) || ''; } catch(e) {}
  editor.value = saved || SAMPLE;
  render();

})();
</script>
