---
title: "HTML Entity Encoder / Decoder"
date: 2025-05-16
categories: ["Free Tools"]
slug: "html-entity-encoder"
tags: ["html entities", "html encoder", "html decoder", "developer tool", "web"]
cover:
  image: "/images/covers/html-entity-encoder.png"
  alt: "HTML Entity Encoder"
ShowToc: false
aliases:
  - "/tools/html-entity-encoder/"
  - "/tools/html-entity-converter/"
  - "/tools/html-entity-converter/"
description: "Free online HTML entity encoder and decoder. Convert special characters to HTML entities and back. Searchable reference table of 30+ common named entities."
---

Encode special characters to HTML entities or decode HTML entities back to plain text — instantly in your browser. No data is sent to any server.

<div id="html-enc-app">

<style>
#html-enc-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1e293b;
}
#html-enc-app *,
#html-enc-app *::before,
#html-enc-app *::after {
box-sizing: border-box;
}
#html-enc-app h2 {
font-size: 1.1rem;
font-weight: 700;
color: #475569;
margin: 1.5rem 0 0.5rem;
border-left: 4px solid #f97316;
padding-left: 0.6rem;
}
#html-enc-app .enc-mode-bar {
display: flex;
gap: 0.5rem;
margin-bottom: 1rem;
flex-wrap: wrap;
}
#html-enc-app .enc-mode-btn {
padding: 0.45rem 1.2rem;
border: 2px solid #475569;
border-radius: 6px;
background: #fff;
color: #475569;
font-size: 0.95rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#html-enc-app .enc-mode-btn.active {
background: #f97316;
border-color: #f97316;
color: #fff;
}
#html-enc-app .enc-mode-btn:hover:not(.active) {
background: #f1f5f9;
}
#html-enc-app .enc-textarea-row {
display: grid;
grid-template-columns: 1fr auto 1fr;
gap: 0.75rem;
align-items: start;
}
@media (max-width: 600px) {
#html-enc-app .enc-textarea-row {
grid-template-columns: 1fr;
}
#html-enc-app .enc-swap-col {
display: flex;
justify-content: center;
}
}
#html-enc-app .enc-col label {
display: block;
font-weight: 600;
color: #475569;
margin-bottom: 0.3rem;
font-size: 0.92rem;
}
#html-enc-app textarea {
width: 100%;
min-height: 180px;
padding: 0.75rem;
border: 2px solid #cbd5e1;
border-radius: 8px;
font-size: 0.93rem;
font-family: 'Courier New', monospace;
resize: vertical;
outline: none;
transition: border-color 0.15s;
color: #1e293b;
background: #f8fafc;
}
#html-enc-app textarea:focus {
border-color: #f97316;
background: #fff;
}
#html-enc-app textarea[readonly] {
background: #f1f5f9;
color: #475569;
cursor: default;
}
#html-enc-app .enc-swap-col {
display: flex;
align-items: center;
padding-top: 1.6rem;
}
#html-enc-app .enc-swap-btn {
background: #fff;
border: 2px solid #475569;
border-radius: 50%;
width: 40px;
height: 40px;
cursor: pointer;
font-size: 1.1rem;
display: flex;
align-items: center;
justify-content: center;
color: #475569;
transition: background 0.15s, color 0.15s;
flex-shrink: 0;
}
#html-enc-app .enc-swap-btn:hover {
background: #f97316;
border-color: #f97316;
color: #fff;
}
#html-enc-app .enc-actions {
display: flex;
gap: 0.5rem;
margin-top: 0.6rem;
flex-wrap: wrap;
}
#html-enc-app .enc-btn {
padding: 0.4rem 1rem;
border-radius: 6px;
font-size: 0.88rem;
font-weight: 600;
cursor: pointer;
border: 2px solid #f97316;
background: #f97316;
color: #fff;
transition: opacity 0.15s;
}
#html-enc-app .enc-btn:hover {
opacity: 0.85;
}
#html-enc-app .enc-btn.secondary {
background: #fff;
color: #475569;
border-color: #475569;
}
#html-enc-app .enc-btn.secondary:hover {
background: #f1f5f9;
opacity: 1;
}
#html-enc-app .enc-copy-msg {
font-size: 0.82rem;
color: #16a34a;
align-self: center;
display: none;
}
#html-enc-app .enc-copy-msg.visible {
display: inline;
}
/* Entity table */
#html-enc-app .enc-search-row {
display: flex;
gap: 0.5rem;
margin-bottom: 0.75rem;
align-items: center;
}
#html-enc-app .enc-search {
flex: 1;
padding: 0.45rem 0.75rem;
border: 2px solid #cbd5e1;
border-radius: 6px;
font-size: 0.92rem;
outline: none;
transition: border-color 0.15s;
}
#html-enc-app .enc-search:focus {
border-color: #f97316;
}
#html-enc-app .enc-table-wrap {
overflow-x: auto;
border-radius: 8px;
border: 1px solid #e2e8f0;
}
#html-enc-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.9rem;
}
#html-enc-app thead th {
background: #475569;
color: #fff;
padding: 0.5rem 0.75rem;
text-align: left;
font-weight: 600;
white-space: nowrap;
}
#html-enc-app tbody tr:nth-child(even) {
background: #f8fafc;
}
#html-enc-app tbody tr:hover {
background: #fff7ed;
}
#html-enc-app td {
padding: 0.45rem 0.75rem;
border-top: 1px solid #e2e8f0;
font-family: 'Courier New', monospace;
vertical-align: middle;
}
#html-enc-app td.render {
font-family: system-ui, sans-serif;
font-size: 1.1rem;
text-align: center;
}
#html-enc-app .enc-use-btn {
padding: 0.25rem 0.65rem;
font-size: 0.8rem;
border: 1px solid #f97316;
background: #fff;
color: #f97316;
border-radius: 5px;
cursor: pointer;
font-weight: 600;
transition: background 0.12s, color 0.12s;
}
#html-enc-app .enc-use-btn:hover {
background: #f97316;
color: #fff;
}
#html-enc-app .enc-no-results {
padding: 1rem;
text-align: center;
color: #94a3b8;
font-style: italic;
display: none;
}
</style>

<div class="enc-mode-bar">
<button class="enc-mode-btn active" id="enc-btn-encode" onclick="encSetMode('encode')">Encode</button>
<button class="enc-mode-btn" id="enc-btn-decode" onclick="encSetMode('decode')">Decode</button>
</div>

<div class="enc-textarea-row">
<div class="enc-col">
<label for="enc-input" id="enc-input-label">Input (plain text)</label>
<textarea id="enc-input" placeholder="Paste or type text here..." oninput="encProcess()"></textarea>
</div>
<div class="enc-swap-col">
<button class="enc-swap-btn" title="Swap input and output" onclick="encSwap()">&#8646;</button>
</div>
<div class="enc-col">
<label for="enc-output" id="enc-output-label">Output (HTML entities)</label>
<textarea id="enc-output" readonly placeholder="Converted result appears here..."></textarea>
</div>
</div>

<div class="enc-actions">
<button class="enc-btn" onclick="encCopy()">Copy Output</button>
<button class="enc-btn secondary" onclick="encClear()">Clear</button>
<span class="enc-copy-msg" id="enc-copy-msg">Copied!</span>
</div>

<h2>Common HTML Entity Reference</h2>

<div class="enc-search-row">
<input class="enc-search" id="enc-search" type="text" placeholder="Search by name, entity, or character..." oninput="encFilterTable()">
</div>

<div class="enc-table-wrap">
<table id="enc-table">
<thead>
<tr>
<th>Character</th>
<th>Named Entity</th>
<th>Numeric (Dec)</th>
<th>Numeric (Hex)</th>
<th>Description</th>
<th></th>
</tr>
</thead>
<tbody id="enc-tbody"></tbody>
</table>
<div class="enc-no-results" id="enc-no-results">No matching entities found.</div>
</div>

<script>
(function() {
var encMode = 'encode';

var ENTITIES = [
['&', '&amp;', '&#38;', '&#x26;', 'Ampersand'],
['<', '&lt;', '&#60;', '&#x3C;', 'Less-than sign'],
['>', '&gt;', '&#62;', '&#x3E;', 'Greater-than sign'],
['"', '&quot;', '&#34;', '&#x22;', 'Quotation mark'],
["'", '&apos;', '&#39;', '&#x27;', 'Apostrophe'],
[' ', '&nbsp;', '&#160;', '&#xA0;', 'Non-breaking space'],
['©', '&copy;', '&#169;', '&#xA9;', 'Copyright sign'],
['®', '&reg;', '&#174;', '&#xAE;', 'Registered sign'],
['™', '&trade;', '&#8482;', '&#x2122;', 'Trade mark sign'],
['€', '&euro;', '&#8364;', '&#x20AC;', 'Euro sign'],
['£', '&pound;', '&#163;', '&#xA3;', 'Pound sign'],
['¥', '&yen;', '&#165;', '&#xA5;', 'Yen sign'],
['¢', '&cent;', '&#162;', '&#xA2;', 'Cent sign'],
['§', '&sect;', '&#167;', '&#xA7;', 'Section sign'],
['¶', '&para;', '&#182;', '&#xB6;', 'Pilcrow sign'],
['·', '&middot;', '&#183;', '&#xB7;', 'Middle dot'],
['–', '&ndash;', '&#8211;', '&#x2013;', 'En dash'],
['—', '&mdash;', '&#8212;', '&#x2014;', 'Em dash'],
['\u2018', '&lsquo;', '&#8216;', '&#x2018;', 'Left single quotation'],
['\u2019', '&rsquo;', '&#8217;', '&#x2019;', 'Right single quotation'],
['\u201C', '&ldquo;', '&#8220;', '&#x201C;', 'Left double quotation'],
['\u201D', '&rdquo;', '&#8221;', '&#x201D;', 'Right double quotation'],
['…', '&hellip;', '&#8230;', '&#x2026;', 'Horizontal ellipsis'],
['•', '&bull;', '&#8226;', '&#x2022;', 'Bullet'],
['★', '', '&#9733;', '&#x2605;', 'Black star'],
['♠', '&spades;', '&#9824;', '&#x2660;', 'Black spade suit'],
['♣', '&clubs;', '&#9827;', '&#x2663;', 'Black club suit'],
['♥', '&hearts;', '&#9829;', '&#x2665;', 'Black heart suit'],
['♦', '&diams;', '&#9830;', '&#x2666;', 'Black diamond suit'],
['÷', '&divide;', '&#247;', '&#xF7;', 'Division sign'],
['×', '&times;', '&#215;', '&#xD7;', 'Multiplication sign'],
['±', '&plusmn;', '&#177;', '&#xB1;', 'Plus-minus sign'],
['¼', '&frac14;', '&#188;', '&#xBC;', 'Vulgar fraction one quarter'],
['½', '&frac12;', '&#189;', '&#xBD;', 'Vulgar fraction one half'],
['¾', '&frac34;', '&#190;', '&#xBE;', 'Vulgar fraction three quarters'],
['°', '&deg;', '&#176;', '&#xB0;', 'Degree sign'],
['µ', '&micro;', '&#181;', '&#xB5;', 'Micro sign'],
['∞', '&infin;', '&#8734;', '&#x221E;', 'Infinity'],
['←', '&larr;', '&#8592;', '&#x2190;', 'Leftwards arrow'],
['→', '&rarr;', '&#8594;', '&#x2192;', 'Rightwards arrow'],
['↑', '&uarr;', '&#8593;', '&#x2191;', 'Upwards arrow'],
['↓', '&darr;', '&#8595;', '&#x2193;', 'Downwards arrow'],
];

function buildTable() {
var tbody = document.getElementById('enc-tbody');
var html = '';
for (var i = 0; i < ENTITIES.length; i++) {
var e = ENTITIES[i];
html += '<tr data-search="' + escAttr((e[0] + ' ' + e[1] + ' ' + e[2] + ' ' + e[3] + ' ' + e[4]).toLowerCase()) + '">';
html += '<td class="render">' + escHtml(e[0]) + '</td>';
html += '<td>' + (e[1] ? escHtml(e[1]) : '<span style="color:#94a3b8">—</span>') + '</td>';
html += '<td>' + escHtml(e[2]) + '</td>';
html += '<td>' + escHtml(e[3]) + '</td>';
html += '<td style="font-family:system-ui,sans-serif;font-size:0.88rem">' + escHtml(e[4]) + '</td>';
html += '<td><button class="enc-use-btn" onclick="encUseEntity(' + i + ')">Insert</button></td>';
html += '</tr>';
}
tbody.innerHTML = html;
}

function escHtml(str) {
return str.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
}

function escAttr(str) {
return str.replace(/"/g, '&quot;');
}

window.encSetMode = function(mode) {
encMode = mode;
document.getElementById('enc-btn-encode').classList.toggle('active', mode === 'encode');
document.getElementById('enc-btn-decode').classList.toggle('active', mode === 'decode');
document.getElementById('enc-input-label').textContent = mode === 'encode' ? 'Input (plain text)' : 'Input (HTML entities)';
document.getElementById('enc-output-label').textContent = mode === 'encode' ? 'Output (HTML entities)' : 'Output (plain text)';
document.getElementById('enc-input').placeholder = mode === 'encode' ? 'Paste or type text here...' : 'Paste HTML with entities here...';
document.getElementById('enc-output').placeholder = mode === 'encode' ? 'HTML entities appear here...' : 'Decoded text appears here...';
encProcess();
};

window.encProcess = function() {
var input = document.getElementById('enc-input').value;
var output = '';
if (encMode === 'encode') {
output = encodeEntities(input);
} else {
output = decodeEntities(input);
}
document.getElementById('enc-output').value = output;
};

function encodeEntities(str) {
var result = '';
for (var i = 0; i < str.length; i++) {
var cp = str.codePointAt(i);
var ch = str[i];
if (cp > 0xFFFF) i++; // surrogate pair
if (cp === 38) { result += '&amp;'; }
else if (cp === 60) { result += '&lt;'; }
else if (cp === 62) { result += '&gt;'; }
else if (cp === 34) { result += '&quot;'; }
else if (cp === 39) { result += '&apos;'; }
else if (cp > 127) { result += '&#' + cp + ';'; }
else { result += ch; }
}
return result;
}

function decodeEntities(str) {
var ta = document.createElement('textarea');
ta.innerHTML = str;
return ta.value;
}

window.encSwap = function() {
var inp = document.getElementById('enc-input');
var out = document.getElementById('enc-output');
var tmp = inp.value;
inp.value = out.value;
out.removeAttribute('readonly');
out.value = tmp;
out.setAttribute('readonly', '');
encProcess();
};

window.encCopy = function() {
var out = document.getElementById('enc-output').value;
if (!out) return;
if (navigator.clipboard) {
navigator.clipboard.writeText(out).then(showCopied);
} else {
var ta = document.createElement('textarea');
ta.value = out;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
showCopied();
}
};

function showCopied() {
var msg = document.getElementById('enc-copy-msg');
msg.classList.add('visible');
setTimeout(function() { msg.classList.remove('visible'); }, 2000);
}

window.encClear = function() {
document.getElementById('enc-input').value = '';
document.getElementById('enc-output').value = '';
};

window.encFilterTable = function() {
var q = document.getElementById('enc-search').value.toLowerCase();
var rows = document.querySelectorAll('#enc-tbody tr');
var any = false;
rows.forEach(function(row) {
var match = !q || row.dataset.search.indexOf(q) !== -1;
row.style.display = match ? '' : 'none';
if (match) any = true;
});
document.getElementById('enc-no-results').style.display = any ? 'none' : 'block';
};

window.encUseEntity = function(idx) {
var entity = ENTITIES[idx][1] || ENTITIES[idx][2];
var inp = document.getElementById('enc-input');
var start = inp.selectionStart;
var end = inp.selectionEnd;
inp.value = inp.value.slice(0, start) + entity + inp.value.slice(end);
inp.setSelectionRange(start + entity.length, start + entity.length);
inp.focus();
encProcess();
};

buildTable();
})();
</script>

</div>

---

## Related Tools

> Encode URLs for safe use in links and APIs → [URL Encoder](/tools/url-encoder/)

> Convert text between camelCase, snake_case, kebab-case, and more → [Case Converter](/tools/case-converter/)

> Remove extra whitespace from HTML or code → [Whitespace Remover](/tools/whitespace-remover/)
