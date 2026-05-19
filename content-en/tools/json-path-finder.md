---
title: "JSON Path Finder — Tree Explorer"
date: 2025-05-16
description: "Explore JSON data with an interactive tree view. Click any node to get its JSONPath expression. Search, copy paths, and inspect values instantly."
categories: ["Free Tools"]
slug: "json-path-finder"
ShowToc: false
cover:
  image: "/images/covers/json-path-finder.png"
  alt: "JSON Path Finder"
---

Paste any JSON and instantly explore its structure with an interactive tree view. Click any node to reveal its exact **JSONPath expression** in both dot notation and bracket notation — no plugins, no sign-up, runs entirely in your browser.

<div id="jpf-app">
<style>
#jpf-app *,
#jpf-app *::before,
#jpf-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#jpf-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f7f9fc;
border-radius: 12px;
padding: 20px;
margin: 24px 0;
border: 1px solid #dde3ef;
}
#jpf-app .jpf-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 14px;
align-items: center;
}
#jpf-app .jpf-search-wrap {
flex: 1;
min-width: 180px;
position: relative;
}
#jpf-app .jpf-search {
width: 100%;
padding: 8px 12px 8px 34px;
border: 1px solid #c8d0e0;
border-radius: 7px;
font-size: 14px;
background: #fff;
outline: none;
transition: border-color .2s;
}
#jpf-app .jpf-search:focus { border-color: #4f8ef7; }
#jpf-app .jpf-search-icon {
position: absolute;
left: 10px;
top: 50%;
transform: translateY(-50%);
color: #8896b3;
font-size: 14px;
pointer-events: none;
}
#jpf-app .jpf-btn {
padding: 8px 14px;
border: 1px solid #c8d0e0;
border-radius: 7px;
background: #fff;
font-size: 13px;
cursor: pointer;
color: #3a4a6b;
transition: background .15s, border-color .15s;
white-space: nowrap;
}
#jpf-app .jpf-btn:hover { background: #eef2fb; border-color: #4f8ef7; }
#jpf-app .jpf-btn.jpf-btn-primary {
background: #4f8ef7;
color: #fff;
border-color: #4f8ef7;
}
#jpf-app .jpf-btn.jpf-btn-primary:hover { background: #3a7de0; }
#jpf-app .jpf-btn.jpf-btn-danger {
border-color: #e05a5a;
color: #c0392b;
}
#jpf-app .jpf-btn.jpf-btn-danger:hover { background: #fdecea; }
#jpf-app .jpf-presets {
display: flex;
flex-wrap: wrap;
gap: 6px;
margin-bottom: 12px;
}
#jpf-app .jpf-preset-btn {
padding: 5px 11px;
border: 1px solid #c8d0e0;
border-radius: 20px;
background: #fff;
font-size: 12px;
cursor: pointer;
color: #4f6394;
transition: background .15s, border-color .15s;
}
#jpf-app .jpf-preset-btn:hover { background: #eef2fb; border-color: #4f8ef7; }
#jpf-app .jpf-label {
font-size: 11px;
font-weight: 600;
text-transform: uppercase;
letter-spacing: .05em;
color: #7a88a8;
margin-bottom: 5px;
}
#jpf-app .jpf-input-area {
width: 100%;
min-height: 130px;
padding: 12px;
border: 1px solid #c8d0e0;
border-radius: 8px;
font-family: "SF Mono", "Fira Code", "Cascadia Code", monospace;
font-size: 13px;
background: #fff;
resize: vertical;
outline: none;
transition: border-color .2s;
line-height: 1.55;
color: #1a1a2e;
}
#jpf-app .jpf-input-area:focus { border-color: #4f8ef7; }
#jpf-app .jpf-input-area.jpf-error { border-color: #e05a5a; }
#jpf-app .jpf-error-msg {
display: none;
color: #c0392b;
font-size: 13px;
margin-top: 6px;
padding: 7px 10px;
background: #fdecea;
border-radius: 6px;
border-left: 3px solid #e05a5a;
}
#jpf-app .jpf-stats-bar {
display: flex;
flex-wrap: wrap;
gap: 14px;
padding: 9px 14px;
background: #eef2fb;
border-radius: 8px;
margin: 12px 0;
font-size: 13px;
color: #4a5a80;
}
#jpf-app .jpf-stat { display: flex; align-items: center; gap: 5px; }
#jpf-app .jpf-stat-val { font-weight: 700; color: #2d3f6e; }
#jpf-app .jpf-path-box {
background: #fff;
border: 1px solid #c8d0e0;
border-radius: 8px;
padding: 12px 14px;
margin-bottom: 12px;
min-height: 56px;
display: none;
}
#jpf-app .jpf-path-box.jpf-active { display: block; }
#jpf-app .jpf-path-row {
display: flex;
align-items: flex-start;
gap: 10px;
margin-bottom: 6px;
flex-wrap: wrap;
}
#jpf-app .jpf-path-row:last-child { margin-bottom: 0; }
#jpf-app .jpf-path-label {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
color: #7a88a8;
min-width: 72px;
padding-top: 2px;
letter-spacing: .04em;
}
#jpf-app .jpf-path-val {
flex: 1;
font-family: "SF Mono", "Fira Code", monospace;
font-size: 13px;
color: #1a5fc8;
word-break: break-all;
background: #f0f5ff;
padding: 3px 8px;
border-radius: 5px;
min-width: 0;
}
#jpf-app .jpf-copy-inline {
flex-shrink: 0;
padding: 3px 9px;
border: 1px solid #c8d0e0;
border-radius: 5px;
background: #fff;
font-size: 12px;
cursor: pointer;
color: #4f6394;
transition: background .15s;
}
#jpf-app .jpf-copy-inline:hover { background: #eef2fb; }
#jpf-app .jpf-copy-inline.jpf-copied {
background: #e6f9ef;
border-color: #2ecc71;
color: #27ae60;
}
#jpf-app .jpf-value-preview {
margin-top: 8px;
padding: 8px 12px;
background: #fafbff;
border: 1px solid #e0e7f5;
border-radius: 6px;
font-family: "SF Mono", "Fira Code", monospace;
font-size: 13px;
word-break: break-all;
color: #2d3f6e;
display: flex;
gap: 10px;
align-items: flex-start;
flex-wrap: wrap;
}
#jpf-app .jpf-value-text { flex: 1; min-width: 0; }
#jpf-app .jpf-type-badge {
display: inline-flex;
align-items: center;
padding: 2px 8px;
border-radius: 4px;
font-size: 11px;
font-weight: 700;
letter-spacing: .03em;
text-transform: uppercase;
flex-shrink: 0;
}
#jpf-app .jpf-type-string  { background: #e8f5e9; color: #2e7d32; }
#jpf-app .jpf-type-number  { background: #e3f2fd; color: #1565c0; }
#jpf-app .jpf-type-boolean { background: #fff3e0; color: #e65100; }
#jpf-app .jpf-type-null    { background: #f3e5f5; color: #6a1b9a; }
#jpf-app .jpf-type-object  { background: #e8eaf6; color: #283593; }
#jpf-app .jpf-type-array   { background: #fce4ec; color: #880e4f; }
#jpf-app .jpf-main-layout {
display: grid;
grid-template-columns: 1fr;
gap: 12px;
}
#jpf-app .jpf-tree-wrap {
background: #fff;
border: 1px solid #dde3ef;
border-radius: 8px;
padding: 12px;
min-height: 200px;
overflow-x: auto;
}
#jpf-app .jpf-tree-empty {
color: #9aa5be;
text-align: center;
padding: 40px 20px;
font-size: 14px;
}
#jpf-app .jpf-node {
user-select: none;
line-height: 1.6;
}
#jpf-app .jpf-node-row {
display: flex;
align-items: baseline;
gap: 4px;
padding: 2px 4px;
border-radius: 5px;
cursor: pointer;
transition: background .1s;
flex-wrap: nowrap;
}
#jpf-app .jpf-node-row:hover { background: #eef2fb; }
#jpf-app .jpf-node-row.jpf-selected { background: #dce8ff; }
#jpf-app .jpf-node-row.jpf-search-match { background: #fff8dc; }
#jpf-app .jpf-node-row.jpf-selected.jpf-search-match { background: #c8dfff; }
#jpf-app .jpf-toggle {
display: inline-block;
width: 16px;
font-size: 11px;
color: #7a88a8;
text-align: center;
cursor: pointer;
flex-shrink: 0;
transition: transform .15s;
}
#jpf-app .jpf-toggle.jpf-open { transform: rotate(0deg); }
#jpf-app .jpf-key {
color: #8b2252;
font-family: "SF Mono", "Fira Code", monospace;
font-size: 13px;
font-weight: 600;
flex-shrink: 0;
}
#jpf-app .jpf-colon { color: #888; font-size: 13px; flex-shrink: 0; }
#jpf-app .jpf-val-inline {
font-family: "SF Mono", "Fira Code", monospace;
font-size: 13px;
min-width: 0;
word-break: break-word;
}
#jpf-app .jpf-val-string  { color: #1e7c1e; }
#jpf-app .jpf-val-number  { color: #1565c0; }
#jpf-app .jpf-val-boolean { color: #e65100; }
#jpf-app .jpf-val-null    { color: #6a1b9a; font-style: italic; }
#jpf-app .jpf-val-collapsed { color: #7a88a8; font-size: 12px; }
#jpf-app .jpf-children {
margin-left: 20px;
border-left: 1px dashed #d0d8ec;
padding-left: 8px;
}
#jpf-app .jpf-node-count {
font-size: 11px;
color: #9aa5be;
margin-left: 4px;
flex-shrink: 0;
}
#jpf-app .jpf-actions-row {
display: flex;
flex-wrap: wrap;
gap: 6px;
margin-top: 14px;
}
#jpf-app .jpf-toast {
position: fixed;
bottom: 24px;
right: 24px;
background: #2d3f6e;
color: #fff;
padding: 10px 18px;
border-radius: 8px;
font-size: 14px;
z-index: 9999;
opacity: 0;
pointer-events: none;
transition: opacity .3s;
box-shadow: 0 4px 16px rgba(0,0,0,.18);
}
#jpf-app .jpf-toast.jpf-show { opacity: 1; }
@media (max-width: 600px) {
#jpf-app { padding: 14px; }
#jpf-app .jpf-path-label { min-width: 56px; font-size: 10px; }
#jpf-app .jpf-path-val { font-size: 12px; }
#jpf-app .jpf-stats-bar { gap: 8px; font-size: 12px; }
#jpf-app .jpf-btn { padding: 7px 10px; font-size: 12px; }
}
</style>

<div class="jpf-label">Sample Presets</div>
<div class="jpf-presets">
<button class="jpf-preset-btn" data-preset="user">User Object</button>
<button class="jpf-preset-btn" data-preset="ecommerce">E-Commerce Order</button>
<button class="jpf-preset-btn" data-preset="github">GitHub API</button>
<button class="jpf-preset-btn" data-preset="nested">Deep Nested</button>
</div>

<div class="jpf-label">Paste JSON</div>
<textarea class="jpf-input-area" id="jpfInput" placeholder='Paste your JSON here, e.g. {"name": "Alice", "age": 30}'></textarea>
<div class="jpf-error-msg" id="jpfError"></div>

<div class="jpf-toolbar" style="margin-top:10px;">
<div class="jpf-search-wrap">
<span class="jpf-search-icon">&#128269;</span>
<input type="text" class="jpf-search" id="jpfSearch" placeholder="Search keys or values..." />
</div>
<button class="jpf-btn jpf-btn-primary" id="jpfParse">Explore</button>
<button class="jpf-btn" id="jpfExpandAll">Expand All</button>
<button class="jpf-btn" id="jpfCollapseAll">Collapse All</button>
<button class="jpf-btn jpf-btn-danger" id="jpfClear">Clear</button>
</div>

<div class="jpf-stats-bar" id="jpfStats" style="display:none;">
<div class="jpf-stat">Nodes: <span class="jpf-stat-val" id="jpfStatNodes">0</span></div>
<div class="jpf-stat">Keys: <span class="jpf-stat-val" id="jpfStatKeys">0</span></div>
<div class="jpf-stat">Arrays: <span class="jpf-stat-val" id="jpfStatArrays">0</span></div>
<div class="jpf-stat">Max Depth: <span class="jpf-stat-val" id="jpfStatDepth">0</span></div>
<div class="jpf-stat">Matches: <span class="jpf-stat-val" id="jpfStatMatches" style="display:none">0</span></div>
</div>

<div class="jpf-path-box" id="jpfPathBox">
<div class="jpf-path-row">
<span class="jpf-path-label">Dot</span>
<span class="jpf-path-val" id="jpfDotPath"></span>
<button class="jpf-copy-inline" data-target="dot">Copy</button>
</div>
<div class="jpf-path-row">
<span class="jpf-path-label">Bracket</span>
<span class="jpf-path-val" id="jpfBracketPath"></span>
<button class="jpf-copy-inline" data-target="bracket">Copy</button>
</div>
<div class="jpf-value-preview" id="jpfValuePreview">
<span class="jpf-value-text" id="jpfValueText"></span>
<button class="jpf-copy-inline" data-target="value">Copy Value</button>
</div>
</div>

<div class="jpf-tree-wrap">
<div class="jpf-tree-empty" id="jpfEmpty">Paste JSON above and click <strong>Explore</strong> to begin.</div>
<div id="jpfTree"></div>
</div>

<div class="jpf-actions-row">
<button class="jpf-btn" id="jpfCopyDotAll">Copy Dot Path</button>
<button class="jpf-btn" id="jpfCopyBracketAll">Copy Bracket Path</button>
<button class="jpf-btn" id="jpfCopyVal">Copy Value</button>
</div>

<div class="jpf-toast" id="jpfToast"></div>

<script>
(function() {
var el = function(id) { return document.getElementById(id); };

var presets = {
user: {
"id": 1,
"name": "Alice Johnson",
"email": "alice@example.com",
"age": 30,
"active": true,
"address": {
"street": "123 Main St",
"city": "Springfield",
"zip": "62701",
"country": "US"
},
"roles": ["admin", "editor"],
"preferences": {
"theme": "dark",
"notifications": { "email": true, "sms": false }
},
"createdAt": "2024-01-15T09:30:00Z"
},
ecommerce: {
"orderId": "ORD-2024-88821",
"status": "shipped",
"customer": { "id": 42, "name": "Bob Smith", "tier": "gold" },
"items": [
{ "sku": "WIDGET-A", "qty": 2, "price": 19.99 },
{ "sku": "GADGET-B", "qty": 1, "price": 49.99 }
],
"totals": { "subtotal": 89.97, "tax": 7.20, "shipping": 5.00, "total": 102.17 },
"shippedAt": "2024-05-10T14:22:00Z",
"trackingNumber": "1Z999AA10123456784"
},
github: {
"id": 583231,
"login": "octocat",
"name": "The Octocat",
"public_repos": 8,
"followers": 14987,
"following": 9,
"created_at": "2011-01-25T18:44:36Z",
"plan": { "name": "pro", "space": 976562499, "private_repos": 9999 },
"repos": [
{ "name": "Hello-World", "stars": 2341, "language": "Ruby" },
{ "name": "linguist", "stars": 11239, "language": "Ruby" }
]
},
nested: {
"level1": {
"level2": {
"level3": {
"level4": {
"level5": {
"value": "deep value",
"flags": [true, false, null, 42]
}
}
}
},
"sibling": [1, 2, { "x": "nested in array" }]
},
"meta": { "version": "1.0", "tags": ["alpha", "beta"] }
}
};

var state = {
parsed: null,
selectedPath: null,
selectedDot: '',
selectedBracket: '',
selectedValue: null,
searchTerm: '',
nodeCount: 0,
keyCount: 0,
arrayCount: 0,
maxDepth: 0
};

function showToast(msg) {
var t = el('jpfToast');
t.textContent = msg;
t.classList.add('jpf-show');
setTimeout(function() { t.classList.remove('jpf-show'); }, 1800);
}

function copyText(text) {
if (navigator.clipboard) {
navigator.clipboard.writeText(text).catch(function() { fallbackCopy(text); });
} else { fallbackCopy(text); }
}

function fallbackCopy(text) {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
}

function typeOf(val) {
if (val === null) return 'null';
if (Array.isArray(val)) return 'array';
return typeof val;
}

function typeBadge(t) {
return '<span class="jpf-type-badge jpf-type-' + t + '">' + t + '</span>';
}

function valueDisplay(val, t) {
if (t === 'string') return '"' + val + '"';
if (t === 'null') return 'null';
if (t === 'boolean') return String(val);
if (t === 'number') return String(val);
if (t === 'array') return 'Array[' + val.length + ']';
if (t === 'object') {
var keys = Object.keys(val);
return 'Object{' + keys.length + '}';
}
return String(val);
}

function dotPath(segments) {
var out = '$';
for (var i = 0; i < segments.length; i++) {
var s = segments[i];
if (typeof s === 'number') {
out += '[' + s + ']';
} else {
out += /^[a-zA-Z_$][a-zA-Z0-9_$]*$/.test(s) ? '.' + s : '["' + s + '"]';
}
}
return out;
}

function bracketPath(segments) {
var out = '$';
for (var i = 0; i < segments.length; i++) {
var s = segments[i];
if (typeof s === 'number') {
out += '[' + s + ']';
} else {
out += '["' + s + '"]';
}
}
return out;
}

function gatherStats(obj, depth) {
depth = depth || 0;
if (depth > state.maxDepth) state.maxDepth = depth;
state.nodeCount++;
var t = typeOf(obj);
if (t === 'object' && obj !== null) {
state.keyCount += Object.keys(obj).length;
Object.keys(obj).forEach(function(k) { gatherStats(obj[k], depth + 1); });
} else if (t === 'array') {
state.arrayCount++;
obj.forEach(function(v) { gatherStats(v, depth + 1); });
}
}

function matchesSearch(key, val, t) {
if (!state.searchTerm) return false;
var q = state.searchTerm.toLowerCase();
if (String(key).toLowerCase().indexOf(q) !== -1) return true;
if (t !== 'object' && t !== 'array') {
if (String(val).toLowerCase().indexOf(q) !== -1) return true;
}
return false;
}

function buildNode(key, val, segments, isRoot) {
var t = typeOf(val);
var isExpandable = t === 'object' || t === 'array';
var segs = segments.slice();
if (!isRoot) segs.push(key);

var node = document.createElement('div');
node.className = 'jpf-node';
node.setAttribute('data-type', t);

var row = document.createElement('div');
row.className = 'jpf-node-row';

var hasMatch = matchesSearch(key, val, t);
if (hasMatch) row.classList.add('jpf-search-match');

var toggle = document.createElement('span');
toggle.className = 'jpf-toggle';
if (isExpandable) {
toggle.textContent = '▶';
toggle.classList.add('jpf-open');
} else {
toggle.innerHTML = '&nbsp;';
}

var keyEl = document.createElement('span');
keyEl.className = 'jpf-key';
if (isRoot) {
keyEl.textContent = t === 'array' ? 'root []' : 'root {}';
} else {
keyEl.textContent = typeof key === 'number' ? '[' + key + ']' : key;
}

var colon = document.createElement('span');
colon.className = 'jpf-colon';
colon.textContent = ':';

var valEl = document.createElement('span');
valEl.className = 'jpf-val-inline';

var children;

if (isExpandable) {
var count = t === 'array' ? val.length : Object.keys(val).length;
valEl.className += ' jpf-val-collapsed';
valEl.textContent = t === 'array' ? '[' + count + ' items]' : '{' + count + ' keys}';

var countBadge = document.createElement('span');
countBadge.className = 'jpf-node-count';
countBadge.textContent = '';

children = document.createElement('div');
children.className = 'jpf-children';

if (t === 'object') {
Object.keys(val).forEach(function(k) {
children.appendChild(buildNode(k, val[k], segs, false));
});
} else {
val.forEach(function(v, i) {
children.appendChild(buildNode(i, v, segs, false));
});
}

row.appendChild(toggle);
if (!isRoot) {
row.appendChild(keyEl);
row.appendChild(colon);
} else {
row.appendChild(keyEl);
}
row.appendChild(valEl);
row.appendChild(countBadge);

var expanded = true;

toggle.addEventListener('click', function(e) {
e.stopPropagation();
expanded = !expanded;
children.style.display = expanded ? '' : 'none';
toggle.style.transform = expanded ? 'rotate(90deg)' : 'rotate(0deg)';
});
toggle.style.transform = 'rotate(90deg)';

row.addEventListener('click', function() {
selectNode(row, segs, key, val, t, isRoot);
});

node.appendChild(row);
node.appendChild(children);
} else {
valEl.className += ' jpf-val-' + t;
valEl.textContent = t === 'string' ? '"' + val + '"' : (val === null ? 'null' : String(val));

row.appendChild(toggle);
row.appendChild(keyEl);
row.appendChild(colon);
row.appendChild(valEl);
row.appendChild(document.createTextNode(' '));
var badge = document.createElement('span');
badge.innerHTML = typeBadge(t);
row.appendChild(badge);

row.addEventListener('click', function() {
selectNode(row, segs, key, val, t, isRoot);
});

node.appendChild(row);
}

node._expand = function() {
if (isExpandable && !expanded) {
expanded = true;
children.style.display = '';
toggle.style.transform = 'rotate(90deg)';
}
if (isExpandable) {
Array.from(children.children).forEach(function(c) {
if (c._expand) c._expand();
});
}
};
node._collapse = function() {
if (isExpandable && expanded) {
expanded = false;
children.style.display = 'none';
toggle.style.transform = 'rotate(0deg)';
}
};

return node;
}

var lastSelectedRow = null;

function selectNode(row, segs, key, val, t, isRoot) {
if (lastSelectedRow) lastSelectedRow.classList.remove('jpf-selected');
row.classList.add('jpf-selected');
lastSelectedRow = row;

var dp = isRoot ? '$' : dotPath(segs);
var bp = isRoot ? '$' : bracketPath(segs);
state.selectedDot = dp;
state.selectedBracket = bp;
state.selectedValue = val;

el('jpfDotPath').textContent = dp;
el('jpfBracketPath').textContent = bp;

var valStr = t === 'object' || t === 'array' ? JSON.stringify(val, null, 2) : String(val);
el('jpfValueText').textContent = valStr;
el('jpfValuePreview').innerHTML = '';
var vt = document.createElement('span');
vt.className = 'jpf-value-text';
vt.textContent = valStr.length > 200 ? valStr.slice(0, 200) + '...' : valStr;
var copyValBtn = document.createElement('button');
copyValBtn.className = 'jpf-copy-inline';
copyValBtn.setAttribute('data-target', 'value');
copyValBtn.textContent = 'Copy Value';
copyValBtn.addEventListener('click', function() {
copyText(t === 'object' || t === 'array' ? JSON.stringify(val, null, 2) : String(val));
showToast('Value copied!');
copyValBtn.classList.add('jpf-copied');
setTimeout(function() { copyValBtn.classList.remove('jpf-copied'); }, 1500);
});
var badgeEl = document.createElement('span');
badgeEl.innerHTML = typeBadge(t);
el('jpfValuePreview').appendChild(vt);
el('jpfValuePreview').appendChild(badgeEl);
el('jpfValuePreview').appendChild(copyValBtn);

el('jpfPathBox').classList.add('jpf-active');
}

function parseAndRender() {
var raw = el('jpfInput').value.trim();
el('jpfInput').classList.remove('jpf-error');
el('jpfError').style.display = 'none';
el('jpfError').textContent = '';
el('jpfTree').innerHTML = '';
el('jpfEmpty').style.display = 'none';
el('jpfStats').style.display = 'none';
el('jpfPathBox').classList.remove('jpf-active');
lastSelectedRow = null;

if (!raw) {
el('jpfEmpty').style.display = '';
el('jpfEmpty').textContent = 'Nothing to explore. Paste some JSON above.';
return;
}

var parsed;
try { parsed = JSON.parse(raw); }
catch(e) {
el('jpfInput').classList.add('jpf-error');
el('jpfError').style.display = '';
el('jpfError').textContent = 'JSON Parse Error: ' + e.message;
el('jpfEmpty').style.display = '';
el('jpfEmpty').textContent = 'Fix the JSON error above to see the tree.';
return;
}

state.parsed = parsed;
state.nodeCount = 0;
state.keyCount = 0;
state.arrayCount = 0;
state.maxDepth = 0;
gatherStats(parsed, 0);

el('jpfStatNodes').textContent = state.nodeCount;
el('jpfStatKeys').textContent = state.keyCount;
el('jpfStatArrays').textContent = state.arrayCount;
el('jpfStatDepth').textContent = state.maxDepth;
el('jpfStats').style.display = '';

var root = buildNode('root', parsed, [], true);
el('jpfTree').appendChild(root);
if (root._expand) root._expand();

if (state.searchTerm) applySearch();
}

function applySearch() {
var q = state.searchTerm.toLowerCase();
var rows = el('jpfTree').querySelectorAll('.jpf-node-row');
var matchCount = 0;
rows.forEach(function(r) {
r.classList.remove('jpf-search-match');
});
if (!q) {
el('jpfStatMatches').style.display = 'none';
return;
}
rows.forEach(function(r) {
var keyEl = r.querySelector('.jpf-key');
var valEl = r.querySelector('.jpf-val-inline');
var keyTxt = keyEl ? keyEl.textContent.toLowerCase() : '';
var valTxt = valEl ? valEl.textContent.toLowerCase() : '';
if (keyTxt.indexOf(q) !== -1 || valTxt.indexOf(q) !== -1) {
r.classList.add('jpf-search-match');
matchCount++;
}
});
el('jpfStatMatches').textContent = matchCount + ' matches';
el('jpfStatMatches').style.display = '';
}

// Wire up events
el('jpfParse').addEventListener('click', parseAndRender);
el('jpfInput').addEventListener('keydown', function(e) {
if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') parseAndRender();
});
el('jpfClear').addEventListener('click', function() {
el('jpfInput').value = '';
el('jpfInput').classList.remove('jpf-error');
el('jpfError').style.display = 'none';
el('jpfTree').innerHTML = '';
el('jpfEmpty').style.display = '';
el('jpfEmpty').textContent = 'Paste JSON above and click Explore to begin.';
el('jpfStats').style.display = 'none';
el('jpfPathBox').classList.remove('jpf-active');
el('jpfSearch').value = '';
state.searchTerm = '';
lastSelectedRow = null;
});

el('jpfExpandAll').addEventListener('click', function() {
el('jpfTree').querySelectorAll('.jpf-node').forEach(function(n) {
if (n._expand) n._expand();
});
});

el('jpfCollapseAll').addEventListener('click', function() {
var roots = el('jpfTree').children;
Array.from(roots).forEach(function(r) { if (r._collapse) r._collapse(); });
});

el('jpfSearch').addEventListener('input', function() {
state.searchTerm = this.value.trim();
applySearch();
});

document.querySelectorAll('#jpf-app .jpf-copy-inline[data-target]').forEach(function(btn) {
btn.addEventListener('click', function() {
var t = btn.getAttribute('data-target');
var txt = t === 'dot' ? state.selectedDot : t === 'bracket' ? state.selectedBracket : '';
if (!txt) return;
copyText(txt);
showToast('Copied!');
btn.classList.add('jpf-copied');
btn.textContent = 'Copied!';
setTimeout(function() { btn.classList.remove('jpf-copied'); btn.textContent = 'Copy'; }, 1500);
});
});

el('jpfCopyDotAll').addEventListener('click', function() {
if (!state.selectedDot) { showToast('Select a node first'); return; }
copyText(state.selectedDot);
showToast('Dot path copied!');
});
el('jpfCopyBracketAll').addEventListener('click', function() {
if (!state.selectedBracket) { showToast('Select a node first'); return; }
copyText(state.selectedBracket);
showToast('Bracket path copied!');
});
el('jpfCopyVal').addEventListener('click', function() {
if (state.selectedValue === null && state.selectedDot === '') { showToast('Select a node first'); return; }
var v = state.selectedValue;
var txt = (typeof v === 'object') ? JSON.stringify(v, null, 2) : String(v);
copyText(txt);
showToast('Value copied!');
});

document.querySelectorAll('#jpf-app .jpf-preset-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
var key = btn.getAttribute('data-preset');
if (presets[key]) {
el('jpfInput').value = JSON.stringify(presets[key], null, 2);
parseAndRender();
}
});
});
})();
</script>

</div>

## How to Use

1. **Paste JSON** into the text area above (or pick a sample preset).
2. Click **Explore** (or press Ctrl+Enter / Cmd+Enter).
3. **Click any node** in the tree to see its JSONPath in dot and bracket notation.
4. Use the **Copy** buttons to grab the path or value.
5. **Search** to highlight nodes whose key or value matches your query.

## What Is JSONPath?

JSONPath is a query language for JSON, analogous to XPath for XML. It lets you pinpoint values inside complex JSON documents using path expressions like `$.user.address.city` or `$["items"][0]["price"]`. JSONPath expressions are used in:

- **REST API testing** (Postman, Insomnia assertions)
- **AWS Step Functions** (Input/OutputPath, ResultPath)
- **Kubernetes** manifests and JSON patches
- **Log analysis** (Elasticsearch, Grafana)
- **Data transformation** pipelines

## Path Notation Guide

| Notation | Example | Notes |
|---|---|---|
| Dot (simple) | `$.user.name` | Clean, readable; works for simple keys |
| Dot (index) | `$.items[0].price` | Array index in brackets |
| Bracket | `$["user"]["name"]` | Always safe; works with any key |
| Bracket (index) | `$["items"][0]["price"]` | Fully explicit |

## Related Tools

- [JSON Formatter & Beautifier](/tools/json-formatter/) — Pretty-print and validate JSON
- [JSON Schema Generator](/tools/json-schema-generator/) — Auto-generate a JSON Schema from sample data
- [JSON to CSV Converter](/tools/json-to-csv/) — Flatten JSON arrays into spreadsheet format
