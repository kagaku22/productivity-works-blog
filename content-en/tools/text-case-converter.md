---
title: "Text Case Converter"
date: 2025-05-16
description: "Free online text case converter. Transform text to UPPERCASE, lowercase, Title Case, camelCase, snake_case, kebab-case, and more — instantly."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "text-case-converter"
ShowToc: false
cover:
  image: "/images/covers/text-case-converter.png"
  alt: "Text Case Converter"
---

<div id="tc-app">
<style>
#tc-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #cbd5e1;
}

#tc-app * {
box-sizing: border-box;
}

#tc-app .tc-label {
display: block;
font-size: 0.8rem;
font-weight: 600;
letter-spacing: 0.08em;
text-transform: uppercase;
color: #94a3b8;
margin-bottom: 6px;
}

#tc-app textarea {
width: 100%;
padding: 12px 14px;
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
color: #e2e8f0;
font-size: 1rem;
line-height: 1.6;
resize: vertical;
outline: none;
transition: border-color 0.2s;
font-family: inherit;
}

#tc-app textarea:focus {
border-color: #6366f1;
}

#tc-app textarea[readonly] {
background: #0f172a;
cursor: default;
}

#tc-app .tc-stats {
display: flex;
gap: 20px;
margin-top: 8px;
font-size: 0.82rem;
color: #64748b;
}

#tc-app .tc-stat span {
color: #94a3b8;
font-weight: 600;
}

#tc-app .tc-buttons {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin: 18px 0;
}

#tc-app .tc-btn {
padding: 8px 16px;
background: #1e293b;
border: 1px solid #334155;
border-radius: 6px;
color: #cbd5e1;
font-size: 0.875rem;
font-weight: 500;
cursor: pointer;
transition: background 0.15s, border-color 0.15s, color 0.15s;
white-space: nowrap;
}

#tc-app .tc-btn:hover {
background: #334155;
border-color: #6366f1;
color: #e2e8f0;
}

#tc-app .tc-btn.active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}

#tc-app .tc-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 6px;
}

#tc-app .tc-copy-btn {
padding: 5px 14px;
background: #334155;
border: 1px solid #475569;
border-radius: 6px;
color: #94a3b8;
font-size: 0.8rem;
font-weight: 500;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}

#tc-app .tc-copy-btn:hover {
background: #475569;
color: #e2e8f0;
}

#tc-app .tc-copy-btn.copied {
background: #166534;
border-color: #15803d;
color: #bbf7d0;
}

#tc-app .tc-section {
margin-bottom: 20px;
}

#tc-app .tc-divider {
border: none;
border-top: 1px solid #1e293b;
margin: 28px 0;
}

#tc-app .tc-cross-links {
background: #1e293b;
border: 1px solid #334155;
border-radius: 8px;
padding: 16px 20px;
font-size: 0.9rem;
line-height: 2;
color: #94a3b8;
}

#tc-app .tc-cross-links a {
color: #818cf8;
text-decoration: none;
}

#tc-app .tc-cross-links a:hover {
color: #a5b4fc;
text-decoration: underline;
}

@media (max-width: 600px) {
#tc-app .tc-btn {
font-size: 0.8rem;
padding: 7px 12px;
}
#tc-app .tc-stats {
flex-wrap: wrap;
gap: 10px;
}
}
</style>

<div class="tc-section">
<label class="tc-label" for="tc-input">Input Text</label>
<textarea id="tc-input" rows="7" placeholder="Paste or type your text here..."></textarea>
<div class="tc-stats">
<div class="tc-stat">Characters: <span id="tc-chars">0</span></div>
<div class="tc-stat">Words: <span id="tc-words">0</span></div>
<div class="tc-stat">Lines: <span id="tc-lines">0</span></div>
</div>
</div>

<div class="tc-buttons" id="tc-buttons">
<button class="tc-btn" data-mode="uppercase">UPPERCASE</button>
<button class="tc-btn" data-mode="lowercase">lowercase</button>
<button class="tc-btn" data-mode="titlecase">Title Case</button>
<button class="tc-btn" data-mode="sentencecase">Sentence case</button>
<button class="tc-btn" data-mode="camelcase">camelCase</button>
<button class="tc-btn" data-mode="pascalcase">PascalCase</button>
<button class="tc-btn" data-mode="snakecase">snake_case</button>
<button class="tc-btn" data-mode="kebabcase">kebab-case</button>
<button class="tc-btn" data-mode="constantcase">CONSTANT_CASE</button>
<button class="tc-btn" data-mode="dotcase">dot.case</button>
<button class="tc-btn" data-mode="alternating">aLtErNaTiNg cAsE</button>
<button class="tc-btn" data-mode="reverse">Reverse text</button>
</div>

<div class="tc-section">
<div class="tc-output-header">
<label class="tc-label" for="tc-output" style="margin-bottom:0;">Output</label>
<button class="tc-copy-btn" id="tc-copy-btn">Copy</button>
</div>
<textarea id="tc-output" rows="7" readonly placeholder="Converted text will appear here..."></textarea>
</div>

<hr class="tc-divider">

<div class="tc-cross-links">
&gt; Count word frequency &rarr; <a href="/tools/word-frequency-counter/">Word Frequency Counter</a><br>
&gt; Check text differences &rarr; <a href="/tools/text-diff-checker/">Text Diff Checker</a><br>
&gt; Encode/decode strings &rarr; <a href="/tools/encoder-decoder/">Universal Encoder/Decoder</a>
</div>

<script>
(function () {
var input   = document.getElementById('tc-input');
var output  = document.getElementById('tc-output');
var copyBtn = document.getElementById('tc-copy-btn');
var buttons = document.querySelectorAll('#tc-buttons .tc-btn');

var activeMode = null;

/* ── converters ─────────────────────────────────── */
function toWords(text) {
return text.trim().split(/[\s\-_\.]+/).filter(Boolean);
}

function titleCase(str) {
var minors = /^(a|an|the|and|but|or|nor|for|so|yet|at|by|in|of|on|to|up|as|if|it)$/i;
return str.replace(/\S+/g, function (word, offset) {
if (offset === 0) return word.charAt(0).toUpperCase() + word.slice(1).toLowerCase();
if (minors.test(word)) return word.toLowerCase();
return word.charAt(0).toUpperCase() + word.slice(1).toLowerCase();
});
}

function sentenceCase(str) {
return str.toLowerCase().replace(/(^\s*\w|[.!?]\s+\w)/g, function (m) {
return m.toUpperCase();
});
}

function camelCase(str) {
var words = toWords(str);
return words.map(function (w, i) {
return i === 0
? w.toLowerCase()
: w.charAt(0).toUpperCase() + w.slice(1).toLowerCase();
}).join('');
}

function pascalCase(str) {
return toWords(str).map(function (w) {
return w.charAt(0).toUpperCase() + w.slice(1).toLowerCase();
}).join('');
}

function snakeCase(str) {
return toWords(str).map(function (w) { return w.toLowerCase(); }).join('_');
}

function kebabCase(str) {
return toWords(str).map(function (w) { return w.toLowerCase(); }).join('-');
}

function constantCase(str) {
return toWords(str).map(function (w) { return w.toUpperCase(); }).join('_');
}

function dotCase(str) {
return toWords(str).map(function (w) { return w.toLowerCase(); }).join('.');
}

function alternatingCase(str) {
var i = 0;
return str.split('').map(function (ch) {
if (/[a-zA-Z]/.test(ch)) {
return (i++ % 2 === 0) ? ch.toLowerCase() : ch.toUpperCase();
}
return ch;
}).join('');
}

function reverseText(str) {
return str.split('').reverse().join('');
}

var converters = {
uppercase:    function (s) { return s.toUpperCase(); },
lowercase:    function (s) { return s.toLowerCase(); },
titlecase:    titleCase,
sentencecase: sentenceCase,
camelcase:    camelCase,
pascalcase:   pascalCase,
snakecase:    snakeCase,
kebabcase:    kebabCase,
constantcase: constantCase,
dotcase:      dotCase,
alternating:  alternatingCase,
reverse:      reverseText,
};

/* ── stats ───────────────────────────────────────── */
function updateStats(text) {
document.getElementById('tc-chars').textContent = text.length;
document.getElementById('tc-words').textContent =
text.trim() === '' ? 0 : text.trim().split(/\s+/).length;
document.getElementById('tc-lines').textContent =
text === '' ? 0 : text.split(/\n/).length;
}

/* ── convert & render ────────────────────────────── */
function convert() {
var text = input.value;
updateStats(text);
if (activeMode && converters[activeMode]) {
output.value = converters[activeMode](text);
} else {
output.value = '';
}
}

/* ── event: input ────────────────────────────────── */
input.addEventListener('input', convert);

/* ── event: buttons ─────────────────────────────── */
buttons.forEach(function (btn) {
btn.addEventListener('click', function () {
var mode = btn.getAttribute('data-mode');
if (activeMode === mode) {
activeMode = null;
btn.classList.remove('active');
output.value = '';
updateStats(input.value);
} else {
activeMode = mode;
buttons.forEach(function (b) { b.classList.remove('active'); });
btn.classList.add('active');
convert();
}
});
});

/* ── event: copy ─────────────────────────────────── */
copyBtn.addEventListener('click', function () {
var text = output.value;
if (!text) return;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(flash).catch(fallbackCopy);
} else {
fallbackCopy();
}
});

function fallbackCopy() {
output.select();
try { document.execCommand('copy'); flash(); } catch (e) {}
}

function flash() {
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('copied');
setTimeout(function () {
copyBtn.textContent = 'Copy';
copyBtn.classList.remove('copied');
}, 1800);
}
})();
</script>
</div>
