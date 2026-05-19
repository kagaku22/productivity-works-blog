---
title: "Markdown TOC Generator"
slug: "markdown-toc-generator"
description: "Free Markdown table of contents generator. Paste your Markdown and generate a clickable TOC with proper anchor links — copy and paste into your document."
date: 2025-05-16
categories: ["Free Tools"]
tags: ["markdown", "table of contents", "toc", "documentation", "anchor links"]
ShowToc: false
cover:
  image: "/images/covers/markdown-toc-generator.png"
  alt: "Markdown TOC Generator — free tool to generate clickable table of contents from Markdown headings"
---

Generate a clickable table of contents from any Markdown document. Paste your Markdown, configure the heading levels and list style, then copy the generated TOC right back into your document. Anchor links follow the GitHub-style slug format so they work on GitHub, GitLab, and most Markdown renderers.

<div id="mt-app">

<style>
#mt-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1a1a2e;
max-width: 900px;
margin: 0 auto;
padding: 0;
}
#mt-app * { box-sizing: border-box; }

#mt-app .mt-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-bottom: 16px;
}
@media (max-width: 640px) {
#mt-app .mt-grid { grid-template-columns: 1fr; }
}

#mt-app .mt-panel {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
}
#mt-app .mt-panel-header {
background: #f8fafc;
border-bottom: 1px solid #e2e8f0;
padding: 10px 14px;
font-size: 13px;
font-weight: 600;
color: #475569;
display: flex;
align-items: center;
justify-content: space-between;
}
#mt-app textarea {
width: 100%;
border: none;
outline: none;
resize: vertical;
padding: 12px 14px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.6;
color: #1e293b;
background: #fff;
min-height: 260px;
display: block;
}
#mt-app .mt-output {
padding: 12px 14px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.6;
color: #1e293b;
min-height: 260px;
white-space: pre-wrap;
word-break: break-word;
background: #fff;
}
#mt-app .mt-output.placeholder {
color: #94a3b8;
font-style: italic;
}

#mt-app .mt-controls {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
margin-bottom: 16px;
display: flex;
flex-wrap: wrap;
gap: 18px;
align-items: flex-end;
}
#mt-app .mt-control-group {
display: flex;
flex-direction: column;
gap: 5px;
}
#mt-app .mt-control-group label {
font-size: 12px;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#mt-app select,
#mt-app input[type="checkbox"] {
cursor: pointer;
}
#mt-app select {
padding: 6px 10px;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
color: #1e293b;
background: #f8fafc;
outline: none;
min-width: 90px;
}
#mt-app select:focus {
border-color: #6366f1;
box-shadow: 0 0 0 2px rgba(99,102,241,0.15);
}
#mt-app .mt-checkbox-row {
display: flex;
align-items: center;
gap: 7px;
font-size: 13px;
color: #334155;
padding-top: 4px;
}
#mt-app input[type="checkbox"] {
width: 15px;
height: 15px;
accent-color: #6366f1;
}

#mt-app .mt-btn-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 16px;
}
#mt-app .mt-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 9px 18px;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
border: none;
transition: background 0.15s, transform 0.1s;
}
#mt-app .mt-btn:active { transform: scale(0.97); }
#mt-app .mt-btn-primary {
background: #6366f1;
color: #fff;
}
#mt-app .mt-btn-primary:hover { background: #4f46e5; }
#mt-app .mt-btn-secondary {
background: #f1f5f9;
color: #334155;
border: 1px solid #e2e8f0;
}
#mt-app .mt-btn-secondary:hover { background: #e2e8f0; }
#mt-app .mt-btn-copy {
background: #10b981;
color: #fff;
}
#mt-app .mt-btn-copy:hover { background: #059669; }
#mt-app .mt-btn-copy.copied { background: #475569; }

#mt-app .mt-stats {
font-size: 12px;
color: #64748b;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 10px 14px;
margin-bottom: 16px;
display: flex;
gap: 20px;
flex-wrap: wrap;
}
#mt-app .mt-stat { display: flex; flex-direction: column; gap: 2px; }
#mt-app .mt-stat strong { font-size: 18px; color: #1e293b; font-weight: 700; }

#mt-app .mt-preview {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
margin-bottom: 16px;
}
#mt-app .mt-preview-body {
padding: 14px 18px;
font-size: 14px;
line-height: 1.7;
color: #1e293b;
}
#mt-app .mt-preview-body ul,
#mt-app .mt-preview-body ol {
margin: 0;
padding-left: 20px;
}
#mt-app .mt-preview-body li { margin: 2px 0; }
#mt-app .mt-preview-body a {
color: #6366f1;
text-decoration: none;
}
#mt-app .mt-preview-body a:hover { text-decoration: underline; }
#mt-app .mt-empty-state {
padding: 32px;
text-align: center;
color: #94a3b8;
font-size: 13px;
}
#mt-app .mt-tabs {
display: flex;
border-bottom: 1px solid #e2e8f0;
padding: 0 14px;
background: #f8fafc;
gap: 2px;
}
#mt-app .mt-tab {
padding: 8px 14px;
font-size: 12px;
font-weight: 600;
color: #64748b;
cursor: pointer;
border-bottom: 2px solid transparent;
transition: color 0.15s, border-color 0.15s;
margin-bottom: -1px;
background: none;
border-top: none;
border-left: none;
border-right: none;
outline: none;
}
#mt-app .mt-tab.active {
color: #6366f1;
border-bottom-color: #6366f1;
}
#mt-app .mt-tab-content { display: none; }
#mt-app .mt-tab-content.active { display: block; }
</style>

<div class="mt-controls">
<div class="mt-control-group">
<label>Min Heading Level</label>
<select id="mt-min-level">
<option value="1">H1</option>
<option value="2" selected>H2</option>
<option value="3">H3</option>
<option value="4">H4</option>
</select>
</div>
<div class="mt-control-group">
<label>Max Heading Level</label>
<select id="mt-max-level">
<option value="2">H2</option>
<option value="3" selected>H3</option>
<option value="4">H4</option>
<option value="5">H5</option>
<option value="6">H6</option>
</select>
</div>
<div class="mt-control-group">
<label>List Style</label>
<select id="mt-list-style">
<option value="bullet" selected>Bullet ( - )</option>
<option value="numbered">Numbered ( 1. )</option>
</select>
</div>
<div class="mt-control-group">
<label>Indent</label>
<select id="mt-indent">
<option value="2" selected>2 spaces</option>
<option value="4">4 spaces</option>
<option value="tab">Tab</option>
</select>
</div>
<div class="mt-control-group">
<label>&nbsp;</label>
<div class="mt-checkbox-row">
<input type="checkbox" id="mt-bold-h1">
<span>Bold H1 entries</span>
</div>
</div>
<div class="mt-control-group">
<label>&nbsp;</label>
<div class="mt-checkbox-row">
<input type="checkbox" id="mt-add-title" checked>
<span>Add "Table of Contents" header</span>
</div>
</div>
</div>

<div class="mt-btn-row">
<button class="mt-btn mt-btn-primary" onclick="mtGenerate()">&#9654; Generate TOC</button>
<button class="mt-btn mt-btn-secondary" onclick="mtLoadSample()">Load Sample</button>
<button class="mt-btn mt-btn-secondary" onclick="mtClear()">Clear</button>
<button class="mt-btn mt-btn-copy" id="mt-copy-btn" onclick="mtCopy()">&#128203; Copy TOC</button>
</div>

<div class="mt-grid">
<div class="mt-panel">
<div class="mt-panel-header">
<span>Markdown Input</span>
<span id="mt-line-count" style="font-weight:400;color:#94a3b8;"></span>
</div>
<textarea id="mt-input" placeholder="Paste your Markdown here...&#10;&#10;# Introduction&#10;## Getting Started&#10;### Installation&#10;## Usage&#10;### Basic Example&#10;## API Reference" oninput="mtOnInput()"></textarea>
</div>
<div class="mt-panel">
<div class="mt-panel-header">
<span>Generated TOC</span>
</div>
<div class="mt-output placeholder" id="mt-output">TOC will appear here after generation...</div>
</div>
</div>

<div class="mt-stats" id="mt-stats" style="display:none;">
<div class="mt-stat"><strong id="stat-headings">0</strong><span>Headings found</span></div>
<div class="mt-stat"><strong id="stat-h1">0</strong><span>H1</span></div>
<div class="mt-stat"><strong id="stat-h2">0</strong><span>H2</span></div>
<div class="mt-stat"><strong id="stat-h3">0</strong><span>H3</span></div>
<div class="mt-stat"><strong id="stat-h4plus">0</strong><span>H4+</span></div>
<div class="mt-stat"><strong id="stat-toc-lines">0</strong><span>TOC lines</span></div>
</div>

<div class="mt-preview" id="mt-preview" style="display:none;">
<div class="mt-panel-header" style="background:#f8fafc;border-bottom:1px solid #e2e8f0;padding:10px 14px;font-size:13px;font-weight:600;color:#475569;">
Live Preview
</div>
<div class="mt-preview-body" id="mt-preview-body"></div>
</div>

<script>
(function() {
// GitHub-style slug generation
function slugify(text) {
return text
.toLowerCase()
.replace(/[^\w\s\-]/g, '')   // remove non-word chars except hyphens
.replace(/\s+/g, '-')         // spaces to hyphens
.replace(/-+/g, '-')          // collapse multiple hyphens
.replace(/^-|-$/g, '');       // trim hyphens
}

function parseHeadings(markdown) {
const lines = markdown.split('\n');
const headings = [];
let inFencedCode = false;
let fenceChar = '';

for (let i = 0; i < lines.length; i++) {
const line = lines[i];

// Detect fenced code blocks
const fenceMatch = line.match(/^(`{3,}|~{3,})/);
if (fenceMatch) {
if (!inFencedCode) {
inFencedCode = true;
fenceChar = fenceMatch[1][0];
} else if (fenceChar === fenceMatch[1][0]) {
inFencedCode = false;
fenceChar = '';
}
continue;
}
if (inFencedCode) continue;

// Match ATX headings (# style)
const headingMatch = line.match(/^(#{1,6})\s+(.+?)(?:\s+#+\s*)?$/);
if (headingMatch) {
const level = headingMatch[1].length;
const text = headingMatch[2].trim();
// Strip inline code, bold, italic from display text for slug
const plainText = text
.replace(/`[^`]+`/g, m => m.slice(1,-1))
.replace(/\*\*([^*]+)\*\*/g, '$1')
.replace(/__([^_]+)__/g, '$1')
.replace(/\*([^*]+)\*/g, '$1')
.replace(/_([^_]+)_/g, '$1')
.replace(/\[([^\]]+)\]\([^)]+\)/g, '$1');
headings.push({ level, text, plainText });
}
}
return headings;
}

function buildToc(headings, opts) {
const { minLevel, maxLevel, listStyle, indent, boldH1, addTitle } = opts;

// Filter by level
const filtered = headings.filter(h => h.level >= minLevel && h.level <= maxLevel);
if (filtered.length === 0) return { toc: '', lines: 0 };

// Track duplicates for GitHub-style suffix
const slugCount = {};

// Numbered list counters per level
const counters = {};

const tocLines = [];
if (addTitle) tocLines.push('## Table of Contents\n');

for (const h of filtered) {
// Build slug
let slug = slugify(h.plainText);
if (slugCount[slug] === undefined) {
slugCount[slug] = 0;
} else {
slugCount[slug]++;
slug = slug + '-' + slugCount[slug];
}

// Indentation: relative to minLevel
const depth = h.level - minLevel;
const indentStr = indent === 'tab'
? '\t'.repeat(depth)
: ' '.repeat(Number(indent) * depth);

let prefix;
if (listStyle === 'numbered') {
// Reset deeper levels when a shallower heading appears
for (const key of Object.keys(counters)) {
if (Number(key) > h.level) delete counters[key];
}
counters[h.level] = (counters[h.level] || 0) + 1;
prefix = counters[h.level] + '.';
} else {
prefix = '-';
}

let displayText = h.text;
if (boldH1 && h.level === 1) displayText = '**' + displayText + '**';

tocLines.push(indentStr + prefix + ' [' + displayText + '](#' + slug + ')');
}

const toc = tocLines.join('\n');
return { toc, lines: filtered.length };
}

function updateStats(headings, tocLineCount) {
const el = id => document.getElementById(id);
const counts = { 1:0, 2:0, 3:0, '4+':0 };
for (const h of headings) {
if (h.level <= 3) counts[h.level]++;
else counts['4+']++;
}
el('stat-headings').textContent = headings.length;
el('stat-h1').textContent = counts[1];
el('stat-h2').textContent = counts[2];
el('stat-h3').textContent = counts[3];
el('stat-h4plus').textContent = counts['4+'];
el('stat-toc-lines').textContent = tocLineCount;
document.getElementById('mt-stats').style.display = 'flex';
}

function renderPreview(tocMd) {
// Simple Markdown list renderer for preview
const lines = tocMd.split('\n');
let html = '';
let listStack = []; // stack of { type, depth }

// Check if numbered or bullet
const isNumbered = lines.some(l => /^\s*\d+\./.test(l));

const getDepth = line => {
const m = line.match(/^(\s*)/);
return m ? m[1].replace(/\t/g, '  ').length : 0;
};

// Flush open lists
const flushTo = depth => {
while (listStack.length > 0 && listStack[listStack.length-1].depth > depth) {
const t = listStack.pop();
html += t.type === 'ol' ? '</ol>' : '</ul>';
}
};

for (const line of lines) {
if (!line.trim()) continue;
// Section header
if (line.startsWith('## ')) {
flushTo(-1);
html += '<strong>' + esc(line.replace(/^## /, '')) + '</strong>';
continue;
}
const itemMatch = line.match(/^(\s*)(?:\d+\.|-)\s+\[(.+?)\]\(#([^)]+)\)(.*)$/);
if (!itemMatch) continue;
const [, ws, text, anchor] = itemMatch;
const depth = ws.replace(/\t/g, '  ').length;
const type = isNumbered && /^\s*\d+\./.test(line) ? 'ol' : 'ul';

flushTo(depth - 1);

if (listStack.length === 0 || listStack[listStack.length-1].depth < depth) {
html += type === 'ol' ? '<ol>' : '<ul>';
listStack.push({ type, depth });
}

// Render bold if wrapped in **
let displayText = esc(text).replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
html += '<li><a href="#' + esc(anchor) + '">' + displayText + '</a></li>';
}
flushTo(-1);

document.getElementById('mt-preview-body').innerHTML = html || '<em style="color:#94a3b8">Nothing to preview.</em>';
document.getElementById('mt-preview').style.display = 'block';
}

function esc(str) {
return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function getOpts() {
return {
minLevel: Number(document.getElementById('mt-min-level').value),
maxLevel: Number(document.getElementById('mt-max-level').value),
listStyle: document.getElementById('mt-list-style').value,
indent: document.getElementById('mt-indent').value,
boldH1: document.getElementById('mt-bold-h1').checked,
addTitle: document.getElementById('mt-add-title').checked,
};
}

window.mtGenerate = function() {
const input = document.getElementById('mt-input').value;
if (!input.trim()) {
setOutput('Please paste some Markdown content first.', true);
return;
}
const opts = getOpts();
const headings = parseHeadings(input);

if (headings.length === 0) {
setOutput('No headings found in the input. Make sure you have lines starting with #.', true);
document.getElementById('mt-stats').style.display = 'none';
document.getElementById('mt-preview').style.display = 'none';
return;
}

const { toc, lines } = buildToc(headings, opts);
if (!toc) {
setOutput('No headings found within the selected level range (H' + opts.minLevel + '–H' + opts.maxLevel + ').', true);
return;
}

setOutput(toc, false);
updateStats(headings, lines);
renderPreview(toc);
};

function setOutput(text, isPlaceholder) {
const el = document.getElementById('mt-output');
el.textContent = text;
el.classList.toggle('placeholder', isPlaceholder);
}

window.mtOnInput = function() {
const input = document.getElementById('mt-input').value;
const lines = input ? input.split('\n').length : 0;
document.getElementById('mt-line-count').textContent = lines ? lines + ' lines' : '';
};

window.mtClear = function() {
document.getElementById('mt-input').value = '';
setOutput('TOC will appear here after generation...', true);
document.getElementById('mt-line-count').textContent = '';
document.getElementById('mt-stats').style.display = 'none';
document.getElementById('mt-preview').style.display = 'none';
};

window.mtLoadSample = function() {
document.getElementById('mt-input').value = `# My Project Documentation

## Introduction

Welcome to the project documentation.

### What is This?

An overview of the tool.

### Why Use It?

Key benefits and use cases.

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

Step-by-step installation guide.

### Configuration

How to configure the tool.

## Usage

### Basic Example

A simple usage example.

### Advanced Options

Advanced configuration options.

#### Option A

Details about option A.

#### Option B

Details about option B.

## API Reference

### Methods

List of available methods.

### Events

List of available events.

## Contributing

How to contribute to this project.

## License

MIT License.`;
mtOnInput();
mtGenerate();
};

window.mtCopy = function() {
const output = document.getElementById('mt-output');
const text = output.textContent;
if (!text || output.classList.contains('placeholder')) return;
navigator.clipboard.writeText(text).then(() => {
const btn = document.getElementById('mt-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(() => {
btn.innerHTML = '&#128203; Copy TOC';
btn.classList.remove('copied');
}, 2000);
});
};
})();
</script>

</div>

## How to Use

1. **Paste your Markdown** into the input box on the left
2. **Configure options** — choose heading levels, list style, and indentation
3. **Click Generate TOC** to extract all headings and build your table of contents
4. **Copy the TOC** and paste it at the top of your Markdown document

## How Anchor Links Work

This tool uses the **GitHub-style slug algorithm** to generate anchor links:

- Text is lowercased
- Spaces become hyphens `-`
- Special characters (except hyphens) are removed
- **Duplicate headings** automatically get a numeric suffix: `#installation`, `#installation-1`, `#installation-2`

This format is compatible with GitHub, GitLab, Obsidian, VS Code Preview, and most Markdown renderers.

## Related Tools

- [Markdown Preview](/tools/markdown-preview/) — Render Markdown in real time
- [Markdown Link Checker](/tools/markdown-link-checker/) — Validate all links in your Markdown
- [HTML Table Generator](/tools/html-table-generator/) — Build HTML tables visually
