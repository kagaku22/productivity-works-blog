---
title: "Code Minifier"
slug: "code-minifier"
date: 2025-05-16
description: "Free online HTML, CSS, and JavaScript minifier. Reduce file size by removing whitespace, comments, and unnecessary characters — no sign-up required."
categories: ["Free Tools"]
tags: ["Developer Tools", "Code Conversion", "Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/code-minifier.png"
  alt: "Code Minifier"
---

Paste your HTML, CSS, or JavaScript below and click **Minify** to strip whitespace, comments, and unnecessary characters. Works entirely in your browser — nothing is sent to a server.

<div id="mn-app">
<style>
#mn-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a1a1a;
}
#mn-app .mn-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e0e0e0;
margin-bottom: 0;
}
#mn-app .mn-tab {
padding: 10px 22px;
cursor: pointer;
background: #f5f5f5;
border: 1px solid #e0e0e0;
border-bottom: none;
border-radius: 6px 6px 0 0;
font-size: 0.95rem;
font-weight: 500;
color: #555;
transition: background 0.15s;
margin-right: 4px;
user-select: none;
}
#mn-app .mn-tab.active {
background: #fff;
color: #2563eb;
border-color: #e0e0e0;
border-bottom: 2px solid #fff;
margin-bottom: -2px;
z-index: 1;
}
#mn-app .mn-tab:hover:not(.active) {
background: #eee;
}
#mn-app .mn-panel {
border: 1px solid #e0e0e0;
border-top: none;
border-radius: 0 0 8px 8px;
background: #fff;
padding: 18px;
}
#mn-app .mn-options {
display: flex;
flex-wrap: wrap;
gap: 14px;
margin-bottom: 14px;
padding: 12px 14px;
background: #f8f9fa;
border-radius: 6px;
border: 1px solid #e8e8e8;
}
#mn-app .mn-options label {
display: flex;
align-items: center;
gap: 6px;
font-size: 0.88rem;
color: #444;
cursor: pointer;
user-select: none;
}
#mn-app .mn-options input[type="checkbox"] {
width: 15px;
height: 15px;
cursor: pointer;
}
#mn-app .mn-upload-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 10px;
}
#mn-app .mn-upload-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 6px 14px;
background: #f0f0f0;
border: 1px solid #ccc;
border-radius: 5px;
font-size: 0.85rem;
cursor: pointer;
color: #333;
transition: background 0.15s;
white-space: nowrap;
}
#mn-app .mn-upload-btn:hover { background: #e4e4e4; }
#mn-app .mn-file-name {
font-size: 0.82rem;
color: #888;
}
#mn-app textarea {
width: 100%;
box-sizing: border-box;
height: 200px;
padding: 12px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.82rem;
border: 1px solid #d0d0d0;
border-radius: 6px;
resize: vertical;
background: #fafafa;
color: #1a1a1a;
line-height: 1.5;
transition: border-color 0.15s;
}
#mn-app textarea:focus {
outline: none;
border-color: #2563eb;
background: #fff;
}
#mn-app .mn-actions {
display: flex;
gap: 10px;
margin-top: 12px;
flex-wrap: wrap;
align-items: center;
}
#mn-app .mn-btn {
padding: 9px 20px;
border: none;
border-radius: 6px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
#mn-app .mn-btn:active { transform: scale(0.97); }
#mn-app .mn-btn-primary {
background: #2563eb;
color: #fff;
}
#mn-app .mn-btn-primary:hover { background: #1d4ed8; }
#mn-app .mn-btn-secondary {
background: #f3f4f6;
color: #374151;
border: 1px solid #d1d5db;
}
#mn-app .mn-btn-secondary:hover { background: #e5e7eb; }
#mn-app .mn-btn-copy {
background: #10b981;
color: #fff;
}
#mn-app .mn-btn-copy:hover { background: #059669; }
#mn-app .mn-btn-clear {
background: #f9fafb;
color: #6b7280;
border: 1px solid #e5e7eb;
margin-left: auto;
}
#mn-app .mn-btn-clear:hover { background: #f3f4f6; }
#mn-app .mn-stats {
margin-top: 14px;
padding: 10px 14px;
background: #f0fdf4;
border: 1px solid #bbf7d0;
border-radius: 6px;
font-size: 0.88rem;
color: #166534;
display: none;
}
#mn-app .mn-stats.visible { display: block; }
#mn-app .mn-stats strong { color: #15803d; }
#mn-app .mn-output-label {
font-size: 0.88rem;
font-weight: 600;
color: #555;
margin-top: 16px;
margin-bottom: 6px;
}
#mn-app .mn-error {
margin-top: 10px;
padding: 10px 14px;
background: #fef2f2;
border: 1px solid #fecaca;
border-radius: 6px;
font-size: 0.88rem;
color: #b91c1c;
display: none;
}
#mn-app .mn-error.visible { display: block; }
#mn-app .mn-divider {
border: none;
border-top: 1px solid #e5e7eb;
margin: 24px 0;
}
#mn-app .mn-links {
font-size: 0.88rem;
color: #555;
}
#mn-app .mn-links a {
color: #2563eb;
text-decoration: none;
}
#mn-app .mn-links a:hover { text-decoration: underline; }
</style>

<div class="mn-tabs">
<div class="mn-tab active" data-lang="html" onclick="mnSwitchTab('html')">HTML</div>
<div class="mn-tab" data-lang="css" onclick="mnSwitchTab('css')">CSS</div>
<div class="mn-tab" data-lang="js" onclick="mnSwitchTab('js')">JavaScript</div>
</div>

<div class="mn-panel">

<!-- HTML options -->
<div id="mn-opts-html" class="mn-options">
<label><input type="checkbox" id="mn-html-comments" checked> Remove comments</label>
<label><input type="checkbox" id="mn-html-whitespace" checked> Collapse whitespace</label>
<label><input type="checkbox" id="mn-html-optional-tags"> Remove optional closing tags</label>
</div>

<!-- CSS options -->
<div id="mn-opts-css" class="mn-options" style="display:none">
<label><input type="checkbox" id="mn-css-comments" checked> Remove comments</label>
<label><input type="checkbox" id="mn-css-whitespace" checked> Remove whitespace</label>
<label><input type="checkbox" id="mn-css-last-semi" checked> Remove last semicolons</label>
<label><input type="checkbox" id="mn-css-merge"> Merge duplicate selectors</label>
</div>

<!-- JS options -->
<div id="mn-opts-js" class="mn-options" style="display:none">
<label><input type="checkbox" id="mn-js-line-comments" checked> Remove // comments</label>
<label><input type="checkbox" id="mn-js-block-comments" checked> Remove /* */ comments</label>
<label><input type="checkbox" id="mn-js-whitespace" checked> Collapse whitespace</label>
</div>

<div class="mn-upload-row">
<label class="mn-upload-btn" for="mn-file-input">&#128194; Upload file</label>
<input type="file" id="mn-file-input" style="display:none" accept=".html,.htm,.css,.js,.txt" onchange="mnLoadFile(this)">
<span class="mn-file-name" id="mn-file-name">No file chosen</span>
</div>

<textarea id="mn-input" placeholder="Paste your HTML, CSS, or JavaScript here…" spellcheck="false"></textarea>

<div class="mn-actions">
<button class="mn-btn mn-btn-primary" onclick="mnMinify()">&#9889; Minify</button>
<button class="mn-btn mn-btn-secondary" onclick="mnBeautify()">&#10024; Beautify</button>
<button class="mn-btn mn-btn-copy" onclick="mnCopy()">&#128203; Copy Result</button>
<button class="mn-btn mn-btn-clear" onclick="mnClear()">Clear</button>
</div>

<div class="mn-error" id="mn-error"></div>
<div class="mn-stats" id="mn-stats"></div>

<div class="mn-output-label">Output</div>
<textarea id="mn-output" placeholder="Minified output will appear here…" spellcheck="false" readonly></textarea>

</div>

<hr class="mn-divider">
<div class="mn-links">
Related tools: <a href="/tools/sql-formatter/">SQL Formatter</a> &nbsp;|&nbsp; <a href="/tools/json-formatter/">JSON Formatter</a>
</div>

<script>
(function () {
'use strict';

var currentLang = 'html';

function mnSwitchTab(lang) {
currentLang = lang;
document.querySelectorAll('#mn-app .mn-tab').forEach(function (t) {
t.classList.toggle('active', t.dataset.lang === lang);
});
document.getElementById('mn-opts-html').style.display = lang === 'html' ? '' : 'none';
document.getElementById('mn-opts-css').style.display  = lang === 'css'  ? '' : 'none';
document.getElementById('mn-opts-js').style.display   = lang === 'js'   ? '' : 'none';
mnHideMessages();
}
window.mnSwitchTab = mnSwitchTab;

function mnHideMessages() {
document.getElementById('mn-error').classList.remove('visible');
document.getElementById('mn-stats').classList.remove('visible');
}

function mnShowError(msg) {
var el = document.getElementById('mn-error');
el.textContent = msg;
el.classList.add('visible');
document.getElementById('mn-stats').classList.remove('visible');
}

function mnShowStats(before, after) {
var saved = before - after;
var pct = before > 0 ? ((saved / before) * 100).toFixed(1) : '0.0';
var el = document.getElementById('mn-stats');
el.innerHTML =
'Before: <strong>' + before.toLocaleString() + ' bytes</strong> &nbsp;|&nbsp; ' +
'After: <strong>' + after.toLocaleString() + ' bytes</strong> &nbsp;|&nbsp; ' +
'Saved: <strong>' + saved.toLocaleString() + ' bytes (' + pct + '%)</strong>';
el.classList.add('visible');
document.getElementById('mn-error').classList.remove('visible');
}

/* ---------- HTML minifier ---------- */
function minifyHTML(src) {
var removeComments  = document.getElementById('mn-html-comments').checked;
var collapseWS      = document.getElementById('mn-html-whitespace').checked;
var removeOptional  = document.getElementById('mn-html-optional-tags').checked;

var out = src;

if (removeComments) {
// Remove HTML comments (but not IE conditionals)
out = out.replace(/<!--(?!\[if)[\s\S]*?-->/g, '');
}

if (collapseWS) {
// Collapse runs of whitespace (space/tab/newline) to single space
// Preserve content inside <pre>, <script>, <style>, <textarea>
out = preserveBlocks(out, function (s) {
return s.replace(/\s+/g, ' ');
});
out = out.trim();
}

if (removeOptional) {
// Remove optional closing tags: </li>, </dt>, </dd>, </p>, </tr>, </th>, </td>
out = out.replace(/<\/(?:li|dt|dd|p|tr|th|td)>/gi, '');
}

return out;
}

function preserveBlocks(html, transform) {
var blocks = [];
var ph = '\x00BLOCK\x00';
// Extract verbatim blocks
var result = html.replace(/(<(?:pre|script|style|textarea)[^>]*>)([\s\S]*?)(<\/(?:pre|script|style|textarea)>)/gi, function (m) {
blocks.push(m);
return ph + (blocks.length - 1) + ph;
});
result = transform(result);
// Restore blocks
result = result.replace(new RegExp(ph.replace(/\x00/g, '\\x00') + '(\\d+)' + ph.replace(/\x00/g, '\\x00'), 'g'), function (m, idx) {
return blocks[parseInt(idx, 10)];
});
return result;
}

/* ---------- CSS minifier ---------- */
function minifyCSS(src) {
var removeComments  = document.getElementById('mn-css-comments').checked;
var removeWS        = document.getElementById('mn-css-whitespace').checked;
var removeLastSemi  = document.getElementById('mn-css-last-semi').checked;
var mergeSel        = document.getElementById('mn-css-merge').checked;

var out = src;

if (removeComments) {
out = out.replace(/\/\*[\s\S]*?\*\//g, '');
}

if (removeWS) {
out = out
.replace(/\s+/g, ' ')
.replace(/\s*([{};:,>+~])\s*/g, '$1')
.replace(/;\s*}/g, '}')
.trim();
}

if (removeLastSemi) {
out = out.replace(/;}/g, '}');
}

if (mergeSel) {
// Basic: merge adjacent identical selectors
// This is a simplified merge - collect rules into a map
try {
var ruleMap = {};
var order = [];
var ruleRe = /([^{}]+)\{([^{}]*)\}/g;
var m;
while ((m = ruleRe.exec(out)) !== null) {
var sel = m[1].trim();
var body = m[2].trim();
if (ruleMap[sel] !== undefined) {
// merge: append new declarations
var existing = ruleMap[sel].replace(/;$/, '');
ruleMap[sel] = existing + ';' + body;
} else {
ruleMap[sel] = body;
order.push(sel);
}
}
out = order.map(function (sel) {
return sel + '{' + ruleMap[sel] + '}';
}).join('');
} catch (e) {
// silently skip merge on parse error
}
}

return out;
}

/* ---------- JS minifier ---------- */
function minifyJS(src) {
var removeLineComments  = document.getElementById('mn-js-line-comments').checked;
var removeBlockComments = document.getElementById('mn-js-block-comments').checked;
var collapseWS          = document.getElementById('mn-js-whitespace').checked;

// Tokenise to avoid touching strings/regex
var tokens = [];
var i = 0;
var len = src.length;

while (i < len) {
// String: single-quoted
if (src[i] === "'") {
var j = i + 1;
while (j < len) {
if (src[j] === '\\') { j += 2; continue; }
if (src[j] === "'") { j++; break; }
j++;
}
tokens.push({ type: 'string', val: src.slice(i, j) });
i = j; continue;
}
// String: double-quoted
if (src[i] === '"') {
var j = i + 1;
while (j < len) {
if (src[j] === '\\') { j += 2; continue; }
if (src[j] === '"') { j++; break; }
j++;
}
tokens.push({ type: 'string', val: src.slice(i, j) });
i = j; continue;
}
// Template literal
if (src[i] === '`') {
var j = i + 1;
while (j < len) {
if (src[j] === '\\') { j += 2; continue; }
if (src[j] === '`') { j++; break; }
j++;
}
tokens.push({ type: 'string', val: src.slice(i, j) });
i = j; continue;
}
// Block comment
if (src[i] === '/' && src[i+1] === '*') {
var j = i + 2;
while (j < len - 1) {
if (src[j] === '*' && src[j+1] === '/') { j += 2; break; }
j++;
}
if (removeBlockComments) {
tokens.push({ type: 'comment', val: ' ' });
} else {
tokens.push({ type: 'code', val: src.slice(i, j) });
}
i = j; continue;
}
// Line comment
if (src[i] === '/' && src[i+1] === '/') {
var j = i + 2;
while (j < len && src[j] !== '\n') j++;
if (removeLineComments) {
tokens.push({ type: 'comment', val: '\n' });
} else {
tokens.push({ type: 'code', val: src.slice(i, j) });
}
i = j; continue;
}
// Regular character
tokens.push({ type: 'code', val: src[i] });
i++;
}

var out = tokens.map(function (t) { return t.val; }).join('');

if (collapseWS) {
// Collapse whitespace runs, but keep newlines that serve as statement separators
out = out
.replace(/[ \t]+/g, ' ')
.replace(/\n[ \t]*/g, '\n')
.replace(/\n{2,}/g, '\n')
.replace(/\n/g, ' ')
.replace(/[ \t]+/g, ' ')
.trim();
}

return out;
}

/* ---------- Beautify ---------- */
function beautifyHTML(src) {
var indent = 0;
var inlineVoid = /^(?:area|base|br|col|embed|hr|img|input|link|meta|param|source|track|wbr)$/i;
var lines = [];
var tagRe = /(<[^>]+>|[^<]+)/g;
var m;
while ((m = tagRe.exec(src)) !== null) {
var chunk = m[1].trim();
if (!chunk) continue;
if (chunk.startsWith('</')) {
indent = Math.max(0, indent - 1);
lines.push(pad(indent) + chunk);
} else if (chunk.startsWith('<') && !chunk.startsWith('<!') && !chunk.endsWith('/>')) {
var tagName = (chunk.match(/^<([a-zA-Z0-9-]+)/) || [])[1] || '';
lines.push(pad(indent) + chunk);
if (!inlineVoid.test(tagName)) indent++;
} else {
lines.push(pad(indent) + chunk);
}
}
return lines.join('\n');
}

function beautifyCSS(src) {
return src
.replace(/\{/g, ' {\n  ')
.replace(/;/g, ';\n  ')
.replace(/\}/g, '\n}\n')
.replace(/\n\s*\n/g, '\n')
.trim();
}

function beautifyJS(src) {
var indent = 0;
var result = '';
var i = 0;
var len = src.length;
while (i < len) {
var ch = src[i];
if (ch === '{' || ch === '[' || ch === '(') {
result += ch + '\n' + pad(++indent);
} else if (ch === '}' || ch === ']' || ch === ')') {
result += '\n' + pad(--indent) + ch;
} else if (ch === ';') {
result += ch + '\n' + pad(indent);
} else {
result += ch;
}
i++;
}
return result.replace(/\n\s*\n/g, '\n').trim();
}

function pad(n) { return '  '.repeat(n); }

/* ---------- Public actions ---------- */
window.mnMinify = function () {
mnHideMessages();
var input = document.getElementById('mn-input').value;
if (!input.trim()) { mnShowError('Please paste some code first.'); return; }
var output;
try {
if (currentLang === 'html') output = minifyHTML(input);
else if (currentLang === 'css') output = minifyCSS(input);
else output = minifyJS(input);
} catch (e) {
mnShowError('Error during minification: ' + e.message);
return;
}
document.getElementById('mn-output').value = output;
var before = new Blob([input]).size;
var after  = new Blob([output]).size;
mnShowStats(before, after);
};

window.mnBeautify = function () {
mnHideMessages();
var input = document.getElementById('mn-input').value;
if (!input.trim()) { mnShowError('Please paste some code first.'); return; }
var output;
try {
if (currentLang === 'html') output = beautifyHTML(input);
else if (currentLang === 'css') output = beautifyCSS(input);
else output = beautifyJS(input);
} catch (e) {
mnShowError('Error during beautification: ' + e.message);
return;
}
document.getElementById('mn-output').value = output;
var before = new Blob([input]).size;
var after  = new Blob([output]).size;
mnShowStats(before, after);
};

window.mnCopy = function () {
var val = document.getElementById('mn-output').value;
if (!val) { mnShowError('Nothing to copy yet — run Minify first.'); return; }
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(val).then(function () {
var btn = document.querySelector('#mn-app .mn-btn-copy');
var orig = btn.textContent;
btn.textContent = 'Copied!';
setTimeout(function () { btn.textContent = orig; }, 1500);
});
} else {
document.getElementById('mn-output').select();
document.execCommand('copy');
}
};

window.mnClear = function () {
document.getElementById('mn-input').value = '';
document.getElementById('mn-output').value = '';
document.getElementById('mn-file-name').textContent = 'No file chosen';
document.getElementById('mn-file-input').value = '';
mnHideMessages();
};

window.mnLoadFile = function (input) {
var file = input.files[0];
if (!file) return;
document.getElementById('mn-file-name').textContent = file.name;
var ext = file.name.split('.').pop().toLowerCase();
if (ext === 'css') mnSwitchTab('css');
else if (ext === 'js') mnSwitchTab('js');
else mnSwitchTab('html');
var reader = new FileReader();
reader.onload = function (e) {
document.getElementById('mn-input').value = e.target.result;
};
reader.readAsText(file);
};

})();
</script>
</div>

## How It Works

The tool runs entirely in your browser using pure JavaScript — your code is never uploaded anywhere.

| Language | What gets removed |
|----------|-------------------|
| HTML | Comments, redundant whitespace, optional closing tags |
| CSS | Comments, whitespace, trailing semicolons, duplicate selectors |
| JavaScript | `//` and `/* */` comments, excess whitespace (string-safe) |

The **Beautify** button does the reverse: it re-indents and formats your code for readability.

## Tips

- Upload a file directly using the **Upload file** button — the language tab switches automatically based on the file extension.
- The size reduction percentage is calculated on UTF-8 byte length, matching what browsers and servers measure.
- For JavaScript, whitespace inside string literals and template literals is preserved to avoid breaking your code.
- Run minified code through Beautify first if you need to debug it.

---

Related tools: [SQL Formatter](/tools/sql-formatter/) &nbsp;|&nbsp; [JSON Formatter](/tools/json-formatter/)
