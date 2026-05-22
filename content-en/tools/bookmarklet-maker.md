---
title: "Bookmarklet Maker"
description: "Free bookmarklet maker tool. Convert JavaScript code into a bookmarklet URL. Minify, encode, and test your bookmarklet. Includes ready-to-use bookmarklet examples."
slug: bookmarklet-maker
date: 2025-05-16
categories: ["Free Tools"]
tags: ["Developer Tools", "Programming", "Free Tools"]
cover:
  image: /images/covers/bookmarklet-maker.png
  alt: "Bookmarklet Maker — Convert JavaScript to bookmarklet URL"
ShowToc: false
---

A **bookmarklet** is a bookmark that runs JavaScript on any page. Paste your JS code below, click **Convert**, drag it to your bookmark bar, and it works instantly — no extensions needed.

<div id="bm-app">
<style>
#bm-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a1a2e;
}
#bm-app * { box-sizing: border-box; }
#bm-app h2 {
font-size: 1.15rem;
font-weight: 700;
margin: 1.6rem 0 0.5rem;
color: #0f3460;
border-left: 4px solid #e94560;
padding-left: 0.6rem;
}
#bm-app .bm-section {
background: #f8f9fc;
border: 1px solid #dde3f0;
border-radius: 10px;
padding: 1.2rem 1.4rem;
margin-bottom: 1.2rem;
}
#bm-app label {
display: block;
font-weight: 600;
font-size: 0.85rem;
margin-bottom: 0.35rem;
color: #333;
}
#bm-app textarea {
width: 100%;
min-height: 180px;
font-family: 'Courier New', Courier, monospace;
font-size: 0.88rem;
line-height: 1.55;
padding: 0.8rem 1rem;
border: 1.5px solid #c8d0e0;
border-radius: 7px;
background: #fff;
color: #1a1a2e;
resize: vertical;
transition: border-color 0.2s;
}
#bm-app textarea:focus {
outline: none;
border-color: #0f3460;
}
#bm-app .bm-options {
display: flex;
flex-wrap: wrap;
gap: 1rem;
align-items: center;
margin-top: 0.8rem;
}
#bm-app .bm-check {
display: flex;
align-items: center;
gap: 0.4rem;
font-size: 0.88rem;
cursor: pointer;
user-select: none;
}
#bm-app .bm-check input { cursor: pointer; width: 16px; height: 16px; }
#bm-app .bm-btn-row {
display: flex;
flex-wrap: wrap;
gap: 0.6rem;
margin-top: 1rem;
}
#bm-app .bm-btn {
padding: 0.55rem 1.2rem;
border: none;
border-radius: 6px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
}
#bm-app .bm-btn:hover { opacity: 0.88; transform: translateY(-1px); }
#bm-app .bm-btn:active { transform: translateY(0); }
#bm-app .bm-btn-primary { background: #e94560; color: #fff; }
#bm-app .bm-btn-secondary { background: #0f3460; color: #fff; }
#bm-app .bm-btn-ghost {
background: transparent;
color: #0f3460;
border: 1.5px solid #0f3460;
}
#bm-app .bm-btn-sm {
padding: 0.35rem 0.75rem;
font-size: 0.8rem;
}
#bm-app .bm-output-wrap {
position: relative;
margin-top: 0.5rem;
}
#bm-app .bm-output {
width: 100%;
min-height: 80px;
font-family: 'Courier New', Courier, monospace;
font-size: 0.82rem;
line-height: 1.5;
padding: 0.75rem 3.5rem 0.75rem 1rem;
border: 1.5px solid #c8d0e0;
border-radius: 7px;
background: #fff;
color: #1a1a2e;
word-break: break-all;
white-space: pre-wrap;
resize: vertical;
}
#bm-app .bm-copy-btn {
position: absolute;
top: 0.5rem;
right: 0.5rem;
padding: 0.3rem 0.6rem;
font-size: 0.75rem;
font-weight: 600;
background: #0f3460;
color: #fff;
border: none;
border-radius: 5px;
cursor: pointer;
transition: opacity 0.15s;
}
#bm-app .bm-copy-btn:hover { opacity: 0.8; }
#bm-app .bm-stats {
display: flex;
gap: 1.5rem;
margin-top: 0.5rem;
font-size: 0.8rem;
color: #666;
}
#bm-app .bm-stats span strong { color: #0f3460; }
#bm-app .bm-drag-box {
margin-top: 0.8rem;
padding: 0.9rem 1.2rem;
background: #eaf0ff;
border: 2px dashed #7fa7e0;
border-radius: 8px;
font-size: 0.88rem;
color: #2a4a7f;
text-align: center;
}
#bm-app .bm-drag-link {
display: inline-block;
margin-top: 0.5rem;
padding: 0.4rem 1rem;
background: #fff;
border: 1.5px solid #7fa7e0;
border-radius: 5px;
font-weight: 700;
color: #0f3460;
text-decoration: none;
cursor: grab;
}
#bm-app .bm-drag-link:hover { background: #ddeaff; }
#bm-app .bm-presets {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-top: 0.3rem;
}
#bm-app .bm-preset-btn {
padding: 0.38rem 0.85rem;
background: #fff;
border: 1.5px solid #c8d0e0;
border-radius: 20px;
font-size: 0.82rem;
cursor: pointer;
transition: border-color 0.15s, background 0.15s;
color: #333;
}
#bm-app .bm-preset-btn:hover {
border-color: #e94560;
background: #fff0f3;
color: #e94560;
}
#bm-app .bm-alert {
padding: 0.65rem 1rem;
border-radius: 6px;
font-size: 0.85rem;
margin-top: 0.6rem;
display: none;
}
#bm-app .bm-alert.error { background: #fff0f0; border: 1px solid #ffbaba; color: #c00; }
#bm-app .bm-alert.success { background: #f0fff4; border: 1px solid #a0d9b0; color: #1a7a3a; }
#bm-app .bm-divider { border: none; border-top: 1px solid #dde3f0; margin: 1.5rem 0; }
#bm-app .bm-crosslinks {
background: #f0f4ff;
border-radius: 8px;
padding: 1rem 1.2rem;
font-size: 0.88rem;
}
#bm-app .bm-crosslinks a {
color: #0f3460;
text-decoration: underline;
margin-right: 1rem;
}
</style>

<div class="bm-section">
<h2>JavaScript Code</h2>
<label for="bm-code">Paste your JavaScript here</label>
<textarea id="bm-code" placeholder="// Example: scroll to top&#10;window.scrollTo({top: 0, behavior: 'smooth'});"></textarea>
<div class="bm-options">
<label class="bm-check">
<input type="checkbox" id="bm-minify" checked>
Minify (remove comments &amp; whitespace)
</label>
<label class="bm-check">
<input type="checkbox" id="bm-encode" checked>
URI encode
</label>
<label class="bm-check">
<input type="checkbox" id="bm-wrap-iife" checked>
Wrap in IIFE (void function(){...}())
</label>
</div>
<div class="bm-btn-row">
<button class="bm-btn bm-btn-primary" id="bm-convert-btn">Convert to Bookmarklet</button>
<button class="bm-btn bm-btn-ghost" id="bm-clear-btn">Clear</button>
<button class="bm-btn bm-btn-secondary" id="bm-test-btn">Test in Console</button>
</div>
<div class="bm-alert" id="bm-alert"></div>
</div>

<div class="bm-section">
<h2>Bookmarklet Output</h2>
<div class="bm-output-wrap">
<textarea class="bm-output" id="bm-result" readonly placeholder="Your bookmarklet URL will appear here..."></textarea>
<button class="bm-copy-btn" id="bm-copy-btn">Copy</button>
</div>
<div class="bm-stats">
<span>Characters: <strong id="bm-char-count">0</strong></span>
<span>Size: <strong id="bm-size">0 B</strong></span>
<span>Status: <strong id="bm-status">—</strong></span>
</div>
<div class="bm-drag-box" id="bm-drag-box" style="display:none;">
<div>Drag this button to your bookmark bar:</div>
<a class="bm-drag-link" id="bm-drag-link" href="#">Bookmarklet</a>
<div style="margin-top:0.5rem;font-size:0.8rem;color:#5a7aaf;">(Show your bookmark bar: Ctrl+Shift+B / Cmd+Shift+B)</div>
</div>
</div>

<div class="bm-section">
<h2>Ready-to-Use Examples</h2>
<div class="bm-presets" id="bm-presets">
<button class="bm-preset-btn" data-preset="highlight-links">Highlight Links</button>
<button class="bm-preset-btn" data-preset="dark-mode">Dark Mode Toggle</button>
<button class="bm-preset-btn" data-preset="font-size">Font Size Changer</button>
<button class="bm-preset-btn" data-preset="print-page">Print Page</button>
<button class="bm-preset-btn" data-preset="scroll-top">Scroll to Top</button>
<button class="bm-preset-btn" data-preset="word-count">Word Count</button>
<button class="bm-preset-btn" data-preset="copy-url">Copy Page URL+Title</button>
</div>
</div>

<hr class="bm-divider">

<div class="bm-crosslinks">
<strong>Related Tools:</strong>
<a href="/tools/code-minifier/">Code Minifier</a>
<a href="/tools/url-encoder/">URL Encoder</a>
</div>

<script>
(function () {
'use strict';

var PRESETS = {
'highlight-links': {
name: 'Highlight Links',
code: [
'// Highlight all links on the page with a colored outline',
'var links = document.querySelectorAll("a");',
'var colors = ["#e94560","#0f3460","#f5a623","#2ecc71","#9b59b6"];',
'links.forEach(function(el, i) {',
'  el.style.outline = "3px solid " + colors[i % colors.length];',
'  el.style.outlineOffset = "2px";',
'});',
'alert("Highlighted " + links.length + " links.");'
].join('\n')
},
'dark-mode': {
name: 'Dark Mode Toggle',
code: [
'// Toggle a simple dark mode overlay on any site',
'var id = "__bm_dark__";',
'var existing = document.getElementById(id);',
'if (existing) {',
'  existing.remove();',
'} else {',
'  var s = document.createElement("style");',
'  s.id = id;',
'  s.textContent = "html{filter:invert(1) hue-rotate(180deg)!important} img,video,canvas{filter:invert(1) hue-rotate(180deg)!important}";',
'  document.head.appendChild(s);',
'}'
].join('\n')
},
'font-size': {
name: 'Font Size Changer',
code: [
'// Cycle through font sizes: 100% → 120% → 140% → 100%',
'var sizes = ["100%","120%","140%"];',
'var cur = document.documentElement.style.fontSize || "100%";',
'var idx = sizes.indexOf(cur);',
'var next = sizes[(idx + 1) % sizes.length];',
'document.documentElement.style.fontSize = next;'
].join('\n')
},
'print-page': {
name: 'Print Page',
code: '// Print the current page\nwindow.print();'
},
'scroll-top': {
name: 'Scroll to Top',
code: [
'// Smooth scroll to the top of the page',
'window.scrollTo({ top: 0, behavior: "smooth" });'
].join('\n')
},
'word-count': {
name: 'Word Count',
code: [
'// Count words in the visible body text',
'var text = document.body.innerText || document.body.textContent || "";',
'var words = text.trim().split(/\\s+/).filter(function(w){ return w.length > 0; });',
'alert("Words on this page: " + words.length);'
].join('\n')
},
'copy-url': {
name: 'Copy Page URL+Title',
code: [
'// Copy the page title and URL to clipboard',
'var txt = document.title + "\\n" + location.href;',
'navigator.clipboard.writeText(txt).then(function(){',
'  alert("Copied!\\n" + txt);',
'}).catch(function(){',
'  prompt("Copy this:", txt);',
'});'
].join('\n')
}
};

function minifyJS(code) {
// Remove single-line comments (but not URLs)
code = code.replace(/(?<![:'"])\/\/[^\n]*/g, '');
// Remove multi-line comments
code = code.replace(/\/\*[\s\S]*?\*\//g, '');
// Collapse whitespace
code = code.replace(/\s+/g, ' ').trim();
// Remove spaces around operators/punctuation (safe subset)
code = code.replace(/\s*([{};,=+\-*\/<>!&|?:])\s*/g, '$1');
// Fix: don't collapse spaces inside string literals — basic pass only
return code;
}

function buildBookmarklet(rawCode, doMinify, doEncode, doIife) {
var code = rawCode.trim();
if (!code) return null;

if (doMinify) {
code = minifyJS(code);
}
if (doIife) {
code = 'void function(){' + code + '}()';
}
if (doEncode) {
return 'javascript:' + encodeURIComponent(code);
} else {
return 'javascript:' + code;
}
}

function byteSize(str) {
return new Blob([str]).size;
}

function formatBytes(n) {
if (n < 1024) return n + ' B';
return (n / 1024).toFixed(1) + ' KB';
}

function showAlert(msg, type) {
var el = document.getElementById('bm-alert');
el.textContent = msg;
el.className = 'bm-alert ' + type;
el.style.display = 'block';
setTimeout(function () { el.style.display = 'none'; }, 4000);
}

function updateStats(url) {
var chars = url ? url.length : 0;
var bytes = url ? byteSize(url) : 0;
document.getElementById('bm-char-count').textContent = chars.toLocaleString();
document.getElementById('bm-size').textContent = formatBytes(bytes);
}

function convert() {
var code = document.getElementById('bm-code').value;
if (!code.trim()) {
showAlert('Please enter some JavaScript code first.', 'error');
return;
}

var doMinify = document.getElementById('bm-minify').checked;
var doEncode = document.getElementById('bm-encode').checked;
var doIife = document.getElementById('bm-wrap-iife').checked;

try {
var url = buildBookmarklet(code, doMinify, doEncode, doIife);
if (!url) { showAlert('Could not build bookmarklet.', 'error'); return; }

document.getElementById('bm-result').value = url;
updateStats(url);
document.getElementById('bm-status').textContent = 'Ready';

// Update drag link
var dragBox = document.getElementById('bm-drag-box');
var dragLink = document.getElementById('bm-drag-link');
dragLink.href = url;
dragBox.style.display = 'block';

showAlert('Bookmarklet ready! Drag it to your bookmark bar or click Copy.', 'success');
} catch (e) {
showAlert('Error: ' + e.message, 'error');
}
}

function copyResult() {
var val = document.getElementById('bm-result').value;
if (!val) { showAlert('Nothing to copy yet. Convert first.', 'error'); return; }
navigator.clipboard.writeText(val).then(function () {
var btn = document.getElementById('bm-copy-btn');
btn.textContent = 'Copied!';
setTimeout(function () { btn.textContent = 'Copy'; }, 2000);
}).catch(function () {
document.getElementById('bm-result').select();
document.execCommand('copy');
});
}

function testBookmarklet() {
var code = document.getElementById('bm-code').value.trim();
if (!code) { showAlert('Enter some JavaScript to test.', 'error'); return; }
try {
// Run in a sandboxed way: wrap in try/catch, use Function constructor
var fn = new Function(code);
fn();
} catch (e) {
showAlert('Runtime error: ' + e.message, 'error');
}
}

function loadPreset(key) {
var p = PRESETS[key];
if (!p) return;
document.getElementById('bm-code').value = p.code;
document.getElementById('bm-status').textContent = '—';
document.getElementById('bm-result').value = '';
document.getElementById('bm-drag-box').style.display = 'none';
updateStats('');
}

// Wire up events
document.getElementById('bm-convert-btn').addEventListener('click', convert);
document.getElementById('bm-copy-btn').addEventListener('click', copyResult);
document.getElementById('bm-test-btn').addEventListener('click', testBookmarklet);
document.getElementById('bm-clear-btn').addEventListener('click', function () {
document.getElementById('bm-code').value = '';
document.getElementById('bm-result').value = '';
document.getElementById('bm-drag-box').style.display = 'none';
document.getElementById('bm-status').textContent = '—';
updateStats('');
});

document.getElementById('bm-presets').addEventListener('click', function (e) {
if (e.target.classList.contains('bm-preset-btn')) {
loadPreset(e.target.dataset.preset);
}
});

// Live char count on code input
document.getElementById('bm-code').addEventListener('input', function () {
var url = document.getElementById('bm-result').value;
if (url) updateStats(url);
});

// Load default preset
loadPreset('scroll-top');
}());
</script>
</div>

## How to Use a Bookmarklet

1. **Paste** your JavaScript into the code area above (or pick an example).
2. **Click Convert** — the tool wraps your code in a `javascript:` URI.
3. **Drag** the generated button to your browser's bookmark bar.
4. **Visit any page** and click the bookmark — your script runs instantly.

## Tips

- **Minify** strips comments and whitespace, keeping the URL short.
- **IIFE wrap** prevents your variables from polluting the page's global scope.
- **URI encode** is required for special characters like spaces, quotes, and ampersands.
- Most browsers cap bookmarklet URLs at ~2 KB — keep scripts lean.
- Use `alert()` or `console.log()` to debug output during testing.

## Related Tools

- [Code Minifier](/tools/code-minifier/) — Minify JS, CSS, and HTML files.
- [URL Encoder](/tools/url-encoder/) — Encode/decode URL components manually.
