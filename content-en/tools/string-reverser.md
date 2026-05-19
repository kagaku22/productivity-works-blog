---
title: "String Reverser & Text Tools - Free Online"
date: 2025-05-16
description: "Reverse a string, reverse word order, flip each word, toggle case, remove extra whitespace, and count vowels/consonants. Real-time preview and one-click copy. Free, no sign-up."
categories: ["Free Tools"]
tags: ["string reverser", "reverse text", "flip text", "toggle case", "text tools", "free tool"]
slug: "string-reverser"
aliases: ["/tools/string-reverser/", "/tools/string-reverser/"]
cover:
  image: "/images/covers/string-reverser.png"
  alt: "String Reverser"
ShowToc: false
---

<div id="sr-app">

<style>
#sr-app {
font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
background: #0f0f13;
color: #e2e8f0;
border-radius: 12px;
padding: 24px;
margin: 0 auto;
max-width: 900px;
box-sizing: border-box;
}

#sr-app * {
box-sizing: border-box;
}

#sr-app h2 {
font-size: 1.05rem;
font-weight: 600;
color: #f1f5f9;
margin: 0 0 10px 0;
}

#sr-app textarea {
width: 100%;
min-height: 130px;
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
color: #e2e8f0;
font-size: 0.95rem;
padding: 12px 14px;
resize: vertical;
font-family: inherit;
transition: border-color 0.2s;
outline: none;
line-height: 1.6;
}

#sr-app textarea:focus {
border-color: #8b5cf6;
}

#sr-app .sr-label {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #8b5cf6;
margin-bottom: 6px;
display: block;
}

#sr-app .sr-section {
margin-bottom: 18px;
}

#sr-app .sr-ops {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 10px;
margin-bottom: 18px;
}

#sr-app .sr-op-card {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 12px 14px;
cursor: pointer;
transition: all 0.18s;
user-select: none;
}

#sr-app .sr-op-card:hover {
border-color: #8b5cf6;
}

#sr-app .sr-op-card.active {
border-color: #8b5cf6;
background: #18122b;
}

#sr-app .sr-op-title {
font-size: 0.85rem;
font-weight: 600;
color: #f1f5f9;
margin-bottom: 3px;
}

#sr-app .sr-op-card.active .sr-op-title {
color: #a78bfa;
}

#sr-app .sr-op-desc {
font-size: 0.75rem;
color: #64748b;
line-height: 1.4;
}

#sr-app .sr-case-row {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 18px;
align-items: center;
}

#sr-app .sr-case-label {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #8b5cf6;
margin-right: 4px;
}

#sr-app .sr-btn {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 6px;
color: #cbd5e1;
font-size: 0.82rem;
padding: 6px 14px;
cursor: pointer;
transition: all 0.18s;
font-family: inherit;
font-weight: 500;
}

#sr-app .sr-btn:hover {
background: #8b5cf6;
border-color: #8b5cf6;
color: #fff;
}

#sr-app .sr-btn.active {
background: #8b5cf6;
border-color: #8b5cf6;
color: #fff;
}

#sr-app .sr-btn.success {
background: #16a34a;
border-color: #16a34a;
color: #fff;
}

#sr-app .sr-toggle {
display: flex;
align-items: center;
gap: 6px;
font-size: 0.82rem;
color: #94a3b8;
cursor: pointer;
user-select: none;
padding: 6px 10px;
border: 1px solid #2d2d3d;
border-radius: 6px;
background: #1a1a24;
transition: all 0.18s;
}

#sr-app .sr-toggle:hover {
border-color: #8b5cf6;
color: #e2e8f0;
}

#sr-app .sr-toggle input[type="checkbox"] {
accent-color: #8b5cf6;
width: 14px;
height: 14px;
cursor: pointer;
}

#sr-app .sr-output-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 6px;
}

#sr-app .sr-stats-row {
display: flex;
flex-wrap: wrap;
gap: 16px;
margin-top: 10px;
font-size: 0.82rem;
color: #94a3b8;
}

#sr-app .sr-stat-val {
color: #8b5cf6;
font-weight: 600;
}

#sr-app .sr-preview {
margin-top: 6px;
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 12px 14px;
min-height: 130px;
font-size: 0.95rem;
color: #cbd5e1;
line-height: 1.6;
white-space: pre-wrap;
word-break: break-word;
}

#sr-app .sr-placeholder {
color: #4a5568;
font-style: italic;
}
</style>

<!-- Input -->
<div class="sr-section">
<span class="sr-label">Input Text</span>
<textarea id="sr-input" placeholder="Type or paste your text here..." oninput="srProcess()"></textarea>
</div>

<!-- Reverse operations -->
<div class="sr-label">Reverse Operations (select one)</div>
<div class="sr-ops" id="sr-ops">
<div class="sr-op-card active" data-op="reverse-string" onclick="srSelectOp(this)">
<div class="sr-op-title">Reverse String</div>
<div class="sr-op-desc">Flip every character in the entire text</div>
</div>
<div class="sr-op-card" data-op="reverse-words" onclick="srSelectOp(this)">
<div class="sr-op-title">Reverse Word Order</div>
<div class="sr-op-desc">Keep spellings intact, flip word positions</div>
</div>
<div class="sr-op-card" data-op="reverse-each-word" onclick="srSelectOp(this)">
<div class="sr-op-title">Reverse Each Word</div>
<div class="sr-op-desc">Flip letters inside every individual word</div>
</div>
</div>

<!-- Case toggle -->
<div class="sr-case-row">
<span class="sr-case-label">Case:</span>
<button class="sr-btn active" id="sr-case-none" onclick="srSetCase('none')">Original</button>
<button class="sr-btn" id="sr-case-upper" onclick="srSetCase('upper')">UPPERCASE</button>
<button class="sr-btn" id="sr-case-lower" onclick="srSetCase('lower')">lowercase</button>
<button class="sr-btn" id="sr-case-title" onclick="srSetCase('title')">Title Case</button>
<button class="sr-btn" id="sr-case-sentence" onclick="srSetCase('sentence')">Sentence case</button>
</div>

<!-- Extra options -->
<div style="display:flex;flex-wrap:wrap;gap:8px;margin-bottom:18px;">
<label class="sr-toggle">
<input type="checkbox" id="sr-trim-ws" onchange="srProcess()"> Remove Extra Whitespace
</label>
</div>

<!-- Output -->
<div class="sr-output-header">
<span class="sr-label">Result (live preview)</span>
<button class="sr-btn" id="sr-copy-btn" onclick="srCopy()">Copy Result</button>
</div>
<div class="sr-preview" id="sr-preview"><span class="sr-placeholder">Result will appear here as you type...</span></div>

<!-- Stats -->
<div class="sr-stats-row">
<span>Characters: <span class="sr-stat-val" id="sr-chars">0</span></span>
<span>Words: <span class="sr-stat-val" id="sr-words">0</span></span>
<span>Vowels: <span class="sr-stat-val" id="sr-vowels">0</span></span>
<span>Consonants: <span class="sr-stat-val" id="sr-cons">0</span></span>
</div>

<script>
(function() {
var srOp = 'reverse-string';
var srCase = 'none';

window.srSelectOp = function(card) {
document.querySelectorAll('#sr-ops .sr-op-card').forEach(function(c) { c.classList.remove('active'); });
card.classList.add('active');
srOp = card.getAttribute('data-op');
srProcess();
};

window.srSetCase = function(c) {
srCase = c;
['none','upper','lower','title','sentence'].forEach(function(k) {
document.getElementById('sr-case-' + k).classList.toggle('active', k === c);
});
srProcess();
};

function reverseString(s) {
return s.split('').reverse().join('');
}

function reverseWords(s) {
return s.split(/(\s+)/).reverse().join('');
}

function reverseEachWord(s) {
return s.replace(/\S+/g, function(w) { return w.split('').reverse().join(''); });
}

function applyCase(s, c) {
if (c === 'upper') return s.toUpperCase();
if (c === 'lower') return s.toLowerCase();
if (c === 'title') return s.replace(/\w\S*/g, function(w) { return w.charAt(0).toUpperCase() + w.slice(1).toLowerCase(); });
if (c === 'sentence') return s.toLowerCase().replace(/(^\s*\w|[.!?]\s+\w)/g, function(c) { return c.toUpperCase(); });
return s;
}

function countVowels(s) {
return (s.match(/[aeiouAEIOU]/g) || []).length;
}

function countConsonants(s) {
return (s.match(/[bcdfghjklmnpqrstvwxyzBCDFGHJKLMNPQRSTVWXYZ]/g) || []).length;
}

window.srProcess = function() {
var raw = document.getElementById('sr-input').value;
var trimWs = document.getElementById('sr-trim-ws').checked;
var previewEl = document.getElementById('sr-preview');

if (!raw) {
previewEl.innerHTML = '<span class="sr-placeholder">Result will appear here as you type...</span>';
document.getElementById('sr-chars').textContent = '0';
document.getElementById('sr-words').textContent = '0';
document.getElementById('sr-vowels').textContent = '0';
document.getElementById('sr-cons').textContent = '0';
return;
}

var s = raw;
if (trimWs) {
s = s.replace(/[ \t]+/g, ' ').replace(/\n{3,}/g, '\n\n').trim();
}

if (srOp === 'reverse-string') {
s = reverseString(s);
} else if (srOp === 'reverse-words') {
s = reverseWords(s);
} else if (srOp === 'reverse-each-word') {
s = reverseEachWord(s);
}

s = applyCase(s, srCase);

previewEl.textContent = s;

// Stats (based on result)
document.getElementById('sr-chars').textContent = s.length;
document.getElementById('sr-words').textContent = s.trim() ? s.trim().split(/\s+/).length : 0;
document.getElementById('sr-vowels').textContent = countVowels(s);
document.getElementById('sr-cons').textContent = countConsonants(s);
};

window.srCopy = function() {
var text = document.getElementById('sr-preview').textContent;
if (!text || text === 'Result will appear here as you type...') return;
var btn = document.getElementById('sr-copy-btn');
var done = function() {
btn.textContent = 'Copied!';
btn.classList.add('success');
setTimeout(function() {
btn.textContent = 'Copy Result';
btn.classList.remove('success');
}, 1800);
};
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(done).catch(function() { fallbackCopy(text, done); });
} else {
fallbackCopy(text, done);
}
};

function fallbackCopy(text, cb) {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
cb();
}
})();
</script>

</div>

---

## Related Tools

> Count words → [Word Counter](/tools/word-counter/)
