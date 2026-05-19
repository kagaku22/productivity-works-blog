---
title: "YAML ↔ JSON Converter — Free Online Tool"
description: "Convert YAML to JSON and JSON to YAML instantly in your browser. Auto-detect format, validate input, control indentation. No external libraries, no server upload."
date: 2025-05-16
categories: ["Free Tools"]
slug: "yaml-json-converter"
ShowToc: false
aliases:
  - "/tools/yaml-json-converter/"
  - "/tools/yaml-json-converter/"
cover:
  image: "/images/covers/yaml-json-converter.png"
  alt: "YAML JSON Converter"
---

Convert between YAML and JSON instantly in your browser. Paste your input and the tool auto-detects the format.

<div id="yj-app">
<style>
#yj-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
background: #1a1a1a;
color: #e5e5e5;
border-radius: 12px;
padding: 24px;
margin: 24px 0;
}
#yj-app * { box-sizing: border-box; }
#yj-app h2 {
margin: 0 0 16px;
font-size: 1.1rem;
color: #ea580c;
letter-spacing: 0.02em;
}
#yj-app .yj-controls {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 18px;
align-items: center;
}
#yj-app button {
background: #ea580c;
color: #fff;
border: none;
border-radius: 6px;
padding: 8px 16px;
font-size: 0.9rem;
cursor: pointer;
font-weight: 600;
transition: background 0.15s;
}
#yj-app button:hover { background: #c2410c; }
#yj-app button.yj-secondary {
background: #2a2a2a;
color: #e5e5e5;
border: 1px solid #444;
font-weight: 400;
}
#yj-app button.yj-secondary:hover { background: #333; }
#yj-app .yj-indent-label {
font-size: 0.85rem;
color: #aaa;
margin-left: 4px;
display: flex;
align-items: center;
gap: 6px;
}
#yj-app select {
background: #2a2a2a;
color: #e5e5e5;
border: 1px solid #444;
border-radius: 6px;
padding: 7px 10px;
font-size: 0.9rem;
cursor: pointer;
}
#yj-app .yj-panes {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}
@media (max-width: 600px) {
#yj-app .yj-panes { grid-template-columns: 1fr; }
}
#yj-app .yj-pane-label {
font-size: 0.8rem;
color: #aaa;
margin-bottom: 6px;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#yj-app textarea {
width: 100%;
height: 280px;
background: #111;
color: #e5e5e5;
border: 1.5px solid #333;
border-radius: 8px;
padding: 12px;
font-family: "Fira Mono", "Consolas", "Menlo", monospace;
font-size: 0.85rem;
line-height: 1.6;
resize: vertical;
outline: none;
transition: border-color 0.15s;
}
#yj-app textarea:focus { border-color: #ea580c; }
#yj-app .yj-output-wrapper { position: relative; }
#yj-app .yj-copy-btn {
position: absolute;
top: 8px;
right: 8px;
background: #2a2a2a;
color: #aaa;
border: 1px solid #444;
border-radius: 5px;
padding: 4px 10px;
font-size: 0.78rem;
cursor: pointer;
font-weight: 400;
transition: background 0.15s, color 0.15s;
z-index: 2;
}
#yj-app .yj-copy-btn:hover { background: #ea580c; color: #fff; border-color: #ea580c; }
#yj-app #yj-error {
margin-top: 12px;
background: #3b0000;
border: 1px solid #7f1d1d;
color: #fca5a5;
border-radius: 6px;
padding: 10px 14px;
font-size: 0.88rem;
display: none;
}
#yj-app #yj-detect-badge {
font-size: 0.8rem;
color: #ea580c;
background: #2a1200;
border: 1px solid #7c2d12;
border-radius: 4px;
padding: 3px 9px;
display: inline-block;
}
</style>

<h2>YAML ↔ JSON Converter</h2>

<div class="yj-controls">
<button onclick="yjConvert()">Convert</button>
<button class="yj-secondary" onclick="yjLoadSampleYAML()">Sample YAML</button>
<button class="yj-secondary" onclick="yjLoadSampleJSON()">Sample JSON</button>
<button class="yj-secondary" onclick="yjClear()">Clear</button>
<span class="yj-indent-label">
Indent:
<select id="yj-indent">
<option value="2" selected>2 spaces</option>
<option value="4">4 spaces</option>
</select>
</span>
<span id="yj-detect-badge" style="display:none"></span>
</div>

<div class="yj-panes">
<div>
<div class="yj-pane-label">Input (YAML or JSON)</div>
<textarea id="yj-input" placeholder="Paste YAML or JSON here…" oninput="yjAutoDetect()"></textarea>
</div>
<div>
<div class="yj-pane-label">Output</div>
<div class="yj-output-wrapper">
<button class="yj-copy-btn" onclick="yjCopyOutput()">Copy</button>
<textarea id="yj-output" readonly placeholder="Output will appear here…"></textarea>
</div>
</div>
</div>

<div id="yj-error"></div>

<script>
(function() {

// ── YAML Parser ──────────────────────────────────────────────────────────
// Supports: key: value, nested objects, arrays (- item), strings, numbers, booleans, null
function parseYAML(text) {
var lines = text.split('\n');
var result = parseBlock(lines, 0, 0);
return result.value;
}

function getIndent(line) {
var m = line.match(/^(\s*)/);
return m ? m[1].length : 0;
}

function parseScalar(raw) {
var s = raw.trim();
if (s === 'null' || s === '~') return null;
if (s === 'true') return true;
if (s === 'false') return false;
if (s === '') return null;
// Quoted strings
if ((s[0] === '"' && s[s.length-1] === '"') ||
(s[0] === "'" && s[s.length-1] === "'")) {
return s.slice(1, -1);
}
// Number
if (/^-?(\d+\.?\d*|\.\d+)([eE][+-]?\d+)?$/.test(s)) {
var n = Number(s);
if (!isNaN(n)) return n;
}
return s;
}

// Returns {value, nextLine}
function parseBlock(lines, startLine, baseIndent) {
var i = startLine;
// Skip empty lines
while (i < lines.length && lines[i].trim() === '') i++;
if (i >= lines.length) return {value: null, nextLine: i};

var firstLine = lines[i];
var firstIndent = getIndent(firstLine);
var firstTrimmed = firstLine.trim();

// Determine if block is a sequence or mapping
if (firstTrimmed.startsWith('- ') || firstTrimmed === '-') {
// Sequence
return parseSequence(lines, i, firstIndent);
} else {
// Mapping or scalar
return parseMapping(lines, i, firstIndent);
}
}

function parseSequence(lines, startLine, baseIndent) {
var arr = [];
var i = startLine;
while (i < lines.length) {
var line = lines[i];
if (line.trim() === '') { i++; continue; }
var indent = getIndent(line);
if (indent < baseIndent) break;
if (indent > baseIndent) { i++; continue; }
var trimmed = line.trim();
if (!trimmed.startsWith('-')) break;
var afterDash = trimmed.slice(1);
if (afterDash.startsWith(' ')) afterDash = afterDash.slice(1);
// Inline value after dash?
if (afterDash.trim() !== '') {
// Could be a mapping on same line: "- key: val"
if (/^[^:]+:\s/.test(afterDash) || afterDash.endsWith(':')) {
// Inline mapping — parse as block starting with this content
// Build synthetic lines
var subIndent = indent + 2;
var synLines = [' '.repeat(subIndent) + afterDash.trim()];
var j = i + 1;
while (j < lines.length) {
if (lines[j].trim() === '') { synLines.push(''); j++; continue; }
if (getIndent(lines[j]) <= indent) break;
synLines.push(lines[j]);
j++;
}
var subResult = parseBlock(synLines, 0, subIndent);
arr.push(subResult.value);
i = j;
} else {
arr.push(parseScalar(afterDash));
i++;
}
} else {
// Next lines belong to this item
i++;
while (i < lines.length && lines[i].trim() === '') i++;
if (i < lines.length) {
var childIndent = getIndent(lines[i]);
if (childIndent > baseIndent) {
var res = parseBlock(lines, i, childIndent);
arr.push(res.value);
i = res.nextLine;
} else {
arr.push(null);
}
} else {
arr.push(null);
}
}
}
return {value: arr, nextLine: i};
}

function parseMapping(lines, startLine, baseIndent) {
var obj = {};
var i = startLine;
while (i < lines.length) {
var line = lines[i];
if (line.trim() === '') { i++; continue; }
var indent = getIndent(line);
if (indent < baseIndent) break;
if (indent > baseIndent) { i++; continue; }
var trimmed = line.trim();
if (trimmed.startsWith('-')) break; // sequence starts
// Key: value
var colonIdx = trimmed.indexOf(': ');
var key, valStr;
if (colonIdx !== -1) {
key = trimmed.slice(0, colonIdx).trim();
valStr = trimmed.slice(colonIdx + 2).trim();
} else if (trimmed.endsWith(':')) {
key = trimmed.slice(0, -1).trim();
valStr = '';
} else {
// Not a key-value pair, treat as scalar
return {value: parseScalar(trimmed), nextLine: i + 1};
}
i++;
if (valStr !== '') {
obj[key] = parseScalar(valStr);
} else {
// Value is next block
while (i < lines.length && lines[i].trim() === '') i++;
if (i < lines.length) {
var childIndent = getIndent(lines[i]);
if (childIndent > baseIndent) {
var childTrimmed = lines[i].trim();
if (childTrimmed.startsWith('- ') || childTrimmed === '-') {
var seqRes = parseSequence(lines, i, childIndent);
obj[key] = seqRes.value;
i = seqRes.nextLine;
} else {
var mapRes = parseMapping(lines, i, childIndent);
obj[key] = mapRes.value;
i = mapRes.nextLine;
}
} else {
obj[key] = null;
}
} else {
obj[key] = null;
}
}
}
return {value: obj, nextLine: i};
}

// ── JSON → YAML ──────────────────────────────────────────────────────────
function jsonToYAML(obj, indent, level) {
indent = indent || 2;
level = level || 0;
var pad = ' '.repeat(indent * level);
var childPad = ' '.repeat(indent * (level + 1));

if (obj === null) return 'null';
if (obj === true) return 'true';
if (obj === false) return 'false';
if (typeof obj === 'number') return String(obj);
if (typeof obj === 'string') {
// Quote if necessary
if (/[:#\[\]{}&*!|>'"%@`,]/.test(obj) || obj.trim() !== obj ||
obj === '' || /^\s*$/.test(obj) ||
['true','false','null','~'].indexOf(obj.toLowerCase()) !== -1 ||
/^-?\d/.test(obj)) {
return '"' + obj.replace(/\\/g, '\\\\').replace(/"/g, '\\"') + '"';
}
return obj;
}
if (Array.isArray(obj)) {
if (obj.length === 0) return '[]';
var lines = obj.map(function(item) {
if (typeof item === 'object' && item !== null && !Array.isArray(item)) {
var keys = Object.keys(item);
if (keys.length === 0) return pad + '- {}';
var firstKey = keys[0];
var rest = '';
var subLines = [];
subLines.push(pad + '- ' + firstKey + ': ' + jsonToYAML(item[firstKey], indent, 0));
for (var k = 1; k < keys.length; k++) {
subLines.push(pad + '  ' + keys[k] + ': ' + jsonToYAML(item[keys[k]], indent, 0));
}
return subLines.join('\n');
}
if (Array.isArray(item)) {
return pad + '-\n' + jsonToYAML(item, indent, level + 1);
}
return pad + '- ' + jsonToYAML(item, indent, 0);
});
return lines.join('\n');
}
if (typeof obj === 'object') {
var keys = Object.keys(obj);
if (keys.length === 0) return '{}';
var lines = keys.map(function(k) {
var val = obj[k];
if (typeof val === 'object' && val !== null) {
if (Array.isArray(val)) {
if (val.length === 0) return pad + k + ': []';
return pad + k + ':\n' + jsonToYAML(val, indent, level + 1);
} else {
if (Object.keys(val).length === 0) return pad + k + ': {}';
return pad + k + ':\n' + jsonToYAML(val, indent, level + 1);
}
}
return pad + k + ': ' + jsonToYAML(val, indent, 0);
});
return lines.join('\n');
}
return String(obj);
}

// ── Auto-detect ──────────────────────────────────────────────────────────
function detectFormat(text) {
var t = text.trim();
if (!t) return null;
if (t[0] === '{' || t[0] === '[') return 'JSON';
return 'YAML';
}

// ── UI Functions ─────────────────────────────────────────────────────────
window.yjAutoDetect = function() {
var input = document.getElementById('yj-input').value;
var badge = document.getElementById('yj-detect-badge');
var fmt = detectFormat(input);
if (fmt) {
badge.textContent = 'Detected: ' + fmt;
badge.style.display = 'inline-block';
} else {
badge.style.display = 'none';
}
};

window.yjConvert = function() {
var input = document.getElementById('yj-input').value.trim();
var errEl = document.getElementById('yj-error');
var outEl = document.getElementById('yj-output');
var indent = parseInt(document.getElementById('yj-indent').value, 10);

errEl.style.display = 'none';
outEl.value = '';

if (!input) {
showError('Input is empty. Paste YAML or JSON to convert.');
return;
}

var fmt = detectFormat(input);
try {
if (fmt === 'JSON') {
var parsed = JSON.parse(input);
var yaml = jsonToYAML(parsed, indent, 0);
outEl.value = yaml;
} else {
// YAML → JSON
var parsed = parseYAML(input);
outEl.value = JSON.stringify(parsed, null, indent);
}
} catch(e) {
showError('Parse error: ' + e.message);
}
};

window.yjCopyOutput = function() {
var outEl = document.getElementById('yj-output');
if (!outEl.value) return;
navigator.clipboard.writeText(outEl.value).then(function() {
var btn = document.querySelector('#yj-app .yj-copy-btn');
var orig = btn.textContent;
btn.textContent = 'Copied!';
setTimeout(function() { btn.textContent = orig; }, 1500);
}).catch(function() {
outEl.select();
document.execCommand('copy');
});
};

window.yjClear = function() {
document.getElementById('yj-input').value = '';
document.getElementById('yj-output').value = '';
document.getElementById('yj-error').style.display = 'none';
document.getElementById('yj-detect-badge').style.display = 'none';
};

window.yjLoadSampleYAML = function() {
document.getElementById('yj-input').value =
'name: Productivity Works\nversion: 2.1\nactive: true\nfeatures:\n  - name: YAML Converter\n    free: true\n  - name: JSON Formatter\n    free: true\nsettings:\n  theme: dark\n  indent: 2\n  maxSize: null\ntags:\n  - productivity\n  - tools\n  - free';
yjAutoDetect();
document.getElementById('yj-error').style.display = 'none';
document.getElementById('yj-output').value = '';
};

window.yjLoadSampleJSON = function() {
document.getElementById('yj-input').value =
JSON.stringify({
"name": "Productivity Works",
"version": 2.1,
"active": true,
"features": [
{"name": "YAML Converter", "free": true},
{"name": "JSON Formatter", "free": true}
],
"settings": {
"theme": "dark",
"indent": 2,
"maxSize": null
},
"tags": ["productivity", "tools", "free"]
}, null, 2);
yjAutoDetect();
document.getElementById('yj-error').style.display = 'none';
document.getElementById('yj-output').value = '';
};

function showError(msg) {
var el = document.getElementById('yj-error');
el.textContent = msg;
el.style.display = 'block';
}

})();
</script>
</div>

---

**Related:** Format JSON → [JSON Formatter](/tools/json-formatter/)
