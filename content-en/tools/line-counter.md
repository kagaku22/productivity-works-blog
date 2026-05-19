---
title: "Line Counter & Code Statistics — Free Online Tool"
slug: "line-counter"
date: 2025-05-16
description: "Free online line counter and code statistics tool. Count lines, words, characters, blank lines, and code vs comment lines — no sign-up required."
categories: ["Free Tools"]
tags: ["line counter", "code statistics", "developer tools", "word count", "character count"]
ShowToc: false
cover:
  image: /images/covers/line-counter.png
  alt: "Line Counter and Code Statistics Tool"
---

<div id="lc-app">

<style>
#lc-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1e293b;
}
#lc-app h2 {
font-size: 1.15rem;
font-weight: 700;
margin: 1.4rem 0 0.5rem;
color: #0f172a;
}
#lc-app .lc-toolbar {
display: flex;
flex-wrap: wrap;
gap: 10px;
align-items: center;
margin-bottom: 10px;
}
#lc-app .lc-toolbar label {
font-size: 13px;
font-weight: 600;
color: #475569;
}
#lc-app select,
#lc-app button {
font-size: 13px;
padding: 6px 14px;
border-radius: 7px;
border: 1.5px solid #cbd5e1;
background: #fff;
cursor: pointer;
color: #1e293b;
transition: border-color 0.15s, background 0.15s;
}
#lc-app select:focus,
#lc-app button:focus {
outline: 2px solid #3b82f6;
outline-offset: 1px;
}
#lc-app button.lc-btn-primary {
background: #2563eb;
color: #fff;
border-color: #2563eb;
font-weight: 700;
}
#lc-app button.lc-btn-primary:hover {
background: #1d4ed8;
border-color: #1d4ed8;
}
#lc-app button.lc-btn-danger {
background: #fee2e2;
color: #b91c1c;
border-color: #fca5a5;
font-weight: 600;
}
#lc-app button.lc-btn-danger:hover {
background: #fecaca;
}
#lc-app button.lc-btn-secondary {
background: #f1f5f9;
color: #334155;
border-color: #cbd5e1;
}
#lc-app button.lc-btn-secondary:hover {
background: #e2e8f0;
}
#lc-app textarea#lc-input {
width: 100%;
min-height: 260px;
padding: 14px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13.5px;
line-height: 1.6;
border: 1.5px solid #cbd5e1;
border-radius: 10px;
resize: vertical;
box-sizing: border-box;
background: #f8fafc;
color: #0f172a;
transition: border-color 0.15s;
}
#lc-app textarea#lc-input:focus {
border-color: #3b82f6;
outline: none;
background: #fff;
}
#lc-app .lc-upload-row {
display: flex;
align-items: center;
gap: 10px;
margin-top: 8px;
flex-wrap: wrap;
}
#lc-app .lc-upload-label {
display: inline-block;
padding: 6px 14px;
background: #f1f5f9;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
color: #334155;
cursor: pointer;
transition: background 0.15s;
}
#lc-app .lc-upload-label:hover {
background: #e2e8f0;
}
#lc-app input[type="file"] {
display: none;
}
#lc-app .lc-file-name {
font-size: 12px;
color: #64748b;
}
#lc-app .lc-stats-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
gap: 12px;
margin-top: 18px;
}
#lc-app .lc-stat-card {
background: #f1f5f9;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
text-align: center;
}
#lc-app .lc-stat-card.lc-highlight {
background: #eff6ff;
border-color: #bfdbfe;
}
#lc-app .lc-stat-value {
font-size: 2rem;
font-weight: 800;
color: #2563eb;
line-height: 1.1;
}
#lc-app .lc-stat-label {
font-size: 11.5px;
color: #64748b;
margin-top: 4px;
font-weight: 500;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#lc-app .lc-code-stats {
margin-top: 18px;
background: #0f172a;
border-radius: 10px;
padding: 16px 20px;
color: #e2e8f0;
}
#lc-app .lc-code-stats h3 {
font-size: 13px;
font-weight: 700;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.05em;
margin: 0 0 10px;
}
#lc-app .lc-code-row {
display: flex;
justify-content: space-between;
font-size: 13.5px;
padding: 4px 0;
border-bottom: 1px solid #1e293b;
}
#lc-app .lc-code-row:last-child {
border-bottom: none;
}
#lc-app .lc-code-key {
color: #7dd3fc;
}
#lc-app .lc-code-val {
font-weight: 700;
color: #86efac;
}
#lc-app .lc-longest-bar {
margin-top: 14px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
}
#lc-app .lc-longest-bar p {
margin: 0;
font-size: 13px;
color: #475569;
}
#lc-app .lc-longest-content {
font-family: monospace;
font-size: 12px;
background: #1e293b;
color: #f1f5f9;
border-radius: 6px;
padding: 8px 12px;
margin-top: 8px;
word-break: break-all;
white-space: pre-wrap;
}
#lc-app .lc-mode-toggle {
display: flex;
align-items: center;
gap: 8px;
}
#lc-app .lc-switch {
position: relative;
display: inline-block;
width: 38px;
height: 22px;
}
#lc-app .lc-switch input {
opacity: 0;
width: 0;
height: 0;
}
#lc-app .lc-slider {
position: absolute;
cursor: pointer;
top: 0; left: 0; right: 0; bottom: 0;
background: #cbd5e1;
border-radius: 22px;
transition: 0.2s;
}
#lc-app .lc-slider:before {
position: absolute;
content: "";
height: 16px;
width: 16px;
left: 3px;
bottom: 3px;
background: white;
border-radius: 50%;
transition: 0.2s;
}
#lc-app input:checked + .lc-slider {
background: #2563eb;
}
#lc-app input:checked + .lc-slider:before {
transform: translateX(16px);
}
#lc-app .lc-switch-label {
font-size: 13px;
font-weight: 600;
color: #334155;
}
#lc-app .lc-export-row {
margin-top: 14px;
display: flex;
gap: 8px;
flex-wrap: wrap;
}
#lc-app .lc-info {
font-size: 13px;
color: #64748b;
margin-top: 6px;
}
#lc-app .lc-divider {
border: none;
border-top: 1.5px solid #e2e8f0;
margin: 28px 0 20px;
}
#lc-app .lc-links {
font-size: 13.5px;
color: #475569;
}
#lc-app .lc-links a {
color: #2563eb;
text-decoration: none;
font-weight: 600;
}
#lc-app .lc-links a:hover {
text-decoration: underline;
}
@media (max-width: 540px) {
#lc-app .lc-stats-grid {
grid-template-columns: repeat(2, 1fr);
}
}
</style>

<!-- Toolbar -->
<div class="lc-toolbar">
<div class="lc-mode-toggle">
<label class="lc-switch">
<input type="checkbox" id="lc-code-mode">
<span class="lc-slider"></span>
</label>
<span class="lc-switch-label">Code Mode</span>
</div>
<label for="lc-lang">Language:</label>
<select id="lc-lang">
<option value="js">JavaScript / CSS</option>
<option value="python">Python / Shell</option>
<option value="html">HTML</option>
<option value="sql">SQL</option>
</select>
<button class="lc-btn-danger" id="lc-clear-btn">Clear</button>
</div>

<!-- Textarea -->
<textarea id="lc-input" placeholder="Paste your text or code here, or upload a file below…" spellcheck="false"></textarea>

<!-- File upload -->
<div class="lc-upload-row">
<label class="lc-upload-label" for="lc-file-input">Upload File</label>
<input type="file" id="lc-file-input" accept=".txt,.js,.ts,.py,.html,.htm,.css,.scss,.sql,.sh,.bash,.md,.json,.xml,.csv,.yaml,.yml,.rb,.java,.c,.cpp,.go,.rs,.php">
<span class="lc-file-name" id="lc-file-name">No file chosen</span>
</div>
<p class="lc-info">Supports: .txt, .js, .ts, .py, .html, .css, .sql, .sh, .md, .json, and more</p>

<!-- Stats grid -->
<div class="lc-stats-grid" id="lc-stats-grid">
<div class="lc-stat-card lc-highlight">
<div class="lc-stat-value" id="st-total-lines">0</div>
<div class="lc-stat-label">Total Lines</div>
</div>
<div class="lc-stat-card">
<div class="lc-stat-value" id="st-non-blank">0</div>
<div class="lc-stat-label">Non-Blank Lines</div>
</div>
<div class="lc-stat-card">
<div class="lc-stat-value" id="st-blank">0</div>
<div class="lc-stat-label">Blank Lines</div>
</div>
<div class="lc-stat-card lc-highlight">
<div class="lc-stat-value" id="st-words">0</div>
<div class="lc-stat-label">Words</div>
</div>
<div class="lc-stat-card">
<div class="lc-stat-value" id="st-chars">0</div>
<div class="lc-stat-label">Characters</div>
</div>
<div class="lc-stat-card">
<div class="lc-stat-value" id="st-chars-nospace">0</div>
<div class="lc-stat-label">Chars (no spaces)</div>
</div>
<div class="lc-stat-card">
<div class="lc-stat-value" id="st-paragraphs">0</div>
<div class="lc-stat-label">Paragraphs</div>
</div>
<div class="lc-stat-card">
<div class="lc-stat-value" id="st-avg-len">0</div>
<div class="lc-stat-label">Avg Line Length</div>
</div>
</div>

<!-- Code stats (shown in code mode) -->
<div class="lc-code-stats" id="lc-code-stats" style="display:none;">
<h3>Code Analysis</h3>
<div class="lc-code-row"><span class="lc-code-key">Code Lines</span><span class="lc-code-val" id="st-code-lines">0</span></div>
<div class="lc-code-row"><span class="lc-code-key">Comment Lines</span><span class="lc-code-val" id="st-comment-lines">0</span></div>
<div class="lc-code-row"><span class="lc-code-key">Block Comment Lines</span><span class="lc-code-val" id="st-block-comment-lines">0</span></div>
<div class="lc-code-row"><span class="lc-code-key">Code / Comment Ratio</span><span class="lc-code-val" id="st-ratio">—</span></div>
</div>

<!-- Longest line -->
<div class="lc-longest-bar" id="lc-longest-bar" style="display:none;">
<p><strong>Longest line</strong>: <span id="st-longest-len">0</span> characters (line <span id="st-longest-num">—</span>)</p>
<div class="lc-longest-content" id="st-longest-content"></div>
</div>

<!-- Export -->
<div class="lc-export-row">
<button class="lc-btn-primary" id="lc-export-btn">Export Statistics</button>
<button class="lc-btn-secondary" id="lc-copy-btn">Copy Stats</button>
</div>

<hr class="lc-divider">

<div class="lc-links">
Also try: <a href="/tools/word-counter/">Word Counter</a> &nbsp;|&nbsp; <a href="/tools/reading-time-calculator/">Reading Time Calculator</a>
</div>

<script>
(function () {
"use strict";

var textarea = document.getElementById("lc-input");
var codeModeToggle = document.getElementById("lc-code-mode");
var langSelect = document.getElementById("lc-lang");
var clearBtn = document.getElementById("lc-clear-btn");
var fileInput = document.getElementById("lc-file-input");
var fileName = document.getElementById("lc-file-name");
var exportBtn = document.getElementById("lc-export-btn");
var copyBtn = document.getElementById("lc-copy-btn");
var codeStatsDiv = document.getElementById("lc-code-stats");
var longestBar = document.getElementById("lc-longest-bar");

function isCommentLine(line, lang) {
var trimmed = line.trim();
if (lang === "js") {
return /^\/\//.test(trimmed) || /^\/\*/.test(trimmed) || /^\*/.test(trimmed) || /\*\/$/.test(trimmed);
}
if (lang === "python") {
return /^#/.test(trimmed) || /^"""/.test(trimmed) || /^'''/.test(trimmed);
}
if (lang === "html") {
return /^<!--/.test(trimmed) || /-->$/.test(trimmed) || (trimmed === "" ? false : false);
}
if (lang === "sql") {
return /^--/.test(trimmed) || /^\/\*/.test(trimmed) || /^\*/.test(trimmed);
}
return /^\/\//.test(trimmed) || /^#/.test(trimmed) || /^\/\*/.test(trimmed) || /^\*/.test(trimmed);
}

function isBlockCommentLine(line, lang) {
var trimmed = line.trim();
if (lang === "js" || lang === "sql") {
return /^\/\*/.test(trimmed) || /^\*/.test(trimmed) || /\*\/$/.test(trimmed);
}
if (lang === "python") {
return /^"""/.test(trimmed) || /^'''/.test(trimmed);
}
if (lang === "html") {
return /^<!--/.test(trimmed) || /-->$/.test(trimmed);
}
return false;
}

function computeStats(text) {
var lang = langSelect.value;
var codeMode = codeModeToggle.checked;
var lines = text === "" ? [] : text.split("\n");
var totalLines = lines.length;
if (text === "") totalLines = 0;

var blankLines = 0;
var nonBlankLines = 0;
var codeLines = 0;
var commentLines = 0;
var blockCommentLines = 0;
var longestLen = 0;
var longestIdx = -1;
var longestContent = "";
var totalLineLen = 0;

for (var i = 0; i < lines.length; i++) {
var l = lines[i];
if (l.trim() === "") {
blankLines++;
} else {
nonBlankLines++;
if (codeMode) {
if (isBlockCommentLine(l, lang)) {
blockCommentLines++;
commentLines++;
} else if (isCommentLine(l, lang)) {
commentLines++;
} else {
codeLines++;
}
}
}
totalLineLen += l.length;
if (l.length > longestLen) {
longestLen = l.length;
longestIdx = i + 1;
longestContent = l;
}
}

var words = text.trim() === "" ? 0 : text.trim().split(/\s+/).length;
var chars = text.length;
var charsNoSpace = text.replace(/\s/g, "").length;
var paragraphs = text.trim() === "" ? 0 : text.trim().split(/\n\s*\n/).length;
var avgLen = totalLines > 0 ? Math.round(totalLineLen / totalLines) : 0;

var ratio = "—";
if (codeMode && commentLines > 0) {
ratio = (codeLines / commentLines).toFixed(1) + " : 1";
} else if (codeMode && codeLines > 0) {
ratio = "No comments";
}

return {
totalLines: totalLines,
nonBlankLines: nonBlankLines,
blankLines: blankLines,
words: words,
chars: chars,
charsNoSpace: charsNoSpace,
paragraphs: paragraphs,
avgLen: avgLen,
codeLines: codeLines,
commentLines: commentLines,
blockCommentLines: blockCommentLines,
ratio: ratio,
longestLen: longestLen,
longestIdx: longestIdx,
longestContent: longestContent,
codeMode: codeMode
};
}

function fmt(n) {
return n.toLocaleString();
}

function renderStats(s) {
document.getElementById("st-total-lines").textContent = fmt(s.totalLines);
document.getElementById("st-non-blank").textContent = fmt(s.nonBlankLines);
document.getElementById("st-blank").textContent = fmt(s.blankLines);
document.getElementById("st-words").textContent = fmt(s.words);
document.getElementById("st-chars").textContent = fmt(s.chars);
document.getElementById("st-chars-nospace").textContent = fmt(s.charsNoSpace);
document.getElementById("st-paragraphs").textContent = fmt(s.paragraphs);
document.getElementById("st-avg-len").textContent = fmt(s.avgLen);

if (s.codeMode) {
document.getElementById("st-code-lines").textContent = fmt(s.codeLines);
document.getElementById("st-comment-lines").textContent = fmt(s.commentLines);
document.getElementById("st-block-comment-lines").textContent = fmt(s.blockCommentLines);
document.getElementById("st-ratio").textContent = s.ratio;
codeStatsDiv.style.display = "block";
} else {
codeStatsDiv.style.display = "none";
}

if (s.totalLines > 0 && s.longestLen > 0) {
document.getElementById("st-longest-len").textContent = s.longestLen;
document.getElementById("st-longest-num").textContent = s.longestIdx;
document.getElementById("st-longest-content").textContent = s.longestContent;
longestBar.style.display = "block";
} else {
longestBar.style.display = "none";
}
}

function buildExportText(s) {
var lines = [
"=== Line Counter Statistics ===",
"Generated: " + new Date().toLocaleString(),
"",
"Total Lines       : " + fmt(s.totalLines),
"Non-Blank Lines   : " + fmt(s.nonBlankLines),
"Blank Lines       : " + fmt(s.blankLines),
"Words             : " + fmt(s.words),
"Characters        : " + fmt(s.chars),
"Chars (no spaces) : " + fmt(s.charsNoSpace),
"Paragraphs        : " + fmt(s.paragraphs),
"Avg Line Length   : " + fmt(s.avgLen),
"Longest Line      : " + s.longestLen + " chars (line " + s.longestIdx + ")"
];
if (s.codeMode) {
lines.push("");
lines.push("--- Code Analysis ---");
lines.push("Code Lines        : " + fmt(s.codeLines));
lines.push("Comment Lines     : " + fmt(s.commentLines));
lines.push("Block Comments    : " + fmt(s.blockCommentLines));
lines.push("Code/Comment Ratio: " + s.ratio);
}
return lines.join("\n");
}

function update() {
var s = computeStats(textarea.value);
renderStats(s);
}

textarea.addEventListener("input", update);
codeModeToggle.addEventListener("change", update);
langSelect.addEventListener("change", update);

clearBtn.addEventListener("click", function () {
textarea.value = "";
fileName.textContent = "No file chosen";
fileInput.value = "";
update();
});

fileInput.addEventListener("change", function () {
var file = fileInput.files[0];
if (!file) return;
fileName.textContent = file.name;
var reader = new FileReader();
reader.onload = function (e) {
textarea.value = e.target.result;
update();
};
reader.readAsText(file);
});

exportBtn.addEventListener("click", function () {
var s = computeStats(textarea.value);
var txt = buildExportText(s);
var blob = new Blob([txt], { type: "text/plain" });
var url = URL.createObjectURL(blob);
var a = document.createElement("a");
a.href = url;
a.download = "line-counter-stats.txt";
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
URL.revokeObjectURL(url);
});

copyBtn.addEventListener("click", function () {
var s = computeStats(textarea.value);
var txt = buildExportText(s);
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(txt).then(function () {
var orig = copyBtn.textContent;
copyBtn.textContent = "Copied!";
setTimeout(function () { copyBtn.textContent = orig; }, 1800);
});
} else {
var ta = document.createElement("textarea");
ta.value = txt;
ta.style.position = "fixed";
ta.style.opacity = "0";
document.body.appendChild(ta);
ta.select();
document.execCommand("copy");
document.body.removeChild(ta);
var orig = copyBtn.textContent;
copyBtn.textContent = "Copied!";
setTimeout(function () { copyBtn.textContent = orig; }, 1800);
}
});

update();
})();
</script>

</div>

---

## How to Use the Line Counter

1. **Paste your text or code** into the textarea, or click **Upload File** to load a local file.
2. Statistics update **instantly** as you type.
3. Enable **Code Mode** to see code vs comment breakdown, then pick your language.
4. Use **Export Statistics** to download a `.txt` summary, or **Copy Stats** to copy to clipboard.

---

## What Each Statistic Means

| Stat | Description |
|---|---|
| Total Lines | Every line including blank ones |
| Non-Blank Lines | Lines with at least one non-whitespace character |
| Blank Lines | Empty or whitespace-only lines |
| Words | Whitespace-delimited tokens |
| Characters | Total character count including spaces and newlines |
| Chars (no spaces) | Characters excluding all whitespace |
| Paragraphs | Blocks of text separated by blank lines |
| Avg Line Length | Mean characters per line |
| Longest Line | The single line with the most characters |
| Code Lines | Non-blank, non-comment lines (Code Mode) |
| Comment Lines | Lines starting with `//`, `#`, `/*`, `*`, or `<!--` depending on language |

---

## Comment Detection by Language

| Language | Single-line | Block |
|---|---|---|
| JavaScript / CSS | `//` | `/* … */` |
| Python / Shell | `#` | `"""…"""` / `'''…'''` |
| HTML | — | `<!-- … -->` |
| SQL | `--` | `/* … */` |

---

## Related Tools

- [Word Counter](/tools/word-counter/) — detailed word frequency and readability stats
- [Reading Time Calculator](/tools/reading-time-calculator/) — estimate how long your content takes to read
