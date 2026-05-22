---
title: "Robots.txt Generator — Free Online Tool"
date: 2025-05-16
description: "Generate robots.txt files instantly. Visual editor with presets for blocking AI crawlers, setting crawl delays, and managing sitemaps. Copy or download with one click."
categories: ["Free Tools"]
tags: ["Utility", "Free Tools"]
slug: "robots-txt-generator"
ShowToc: false
aliases:
  - "/tools/robots-txt-generator/"
  - "/tools/robots-txt-generator/"
cover:
  image: "/images/covers/robots-txt-generator.png"
  alt: "Robots.txt Generator"
---

Build a `robots.txt` file with a visual editor — no coding required. Add user-agent blocks, allow/disallow paths, set crawl delays, and include your sitemap. Choose from presets to block AI crawlers, apply WordPress defaults, or start fresh.

<div id="robots-app">

<style>
#robots-app *,
#robots-app *::before,
#robots-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#robots-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
line-height: 1.5;
max-width: 900px;
margin: 0 auto;
}

#robots-app h2 {
font-size: 1.1rem;
font-weight: 700;
margin-bottom: 12px;
color: #1a1a2e;
}

#robots-app h3 {
font-size: 0.95rem;
font-weight: 700;
margin-bottom: 8px;
color: #333;
}

#robots-app .robots-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
}

@media (max-width: 680px) {
#robots-app .robots-layout {
grid-template-columns: 1fr;
}
}

#robots-app .panel {
background: #f8f9fc;
border: 1px solid #e0e4ef;
border-radius: 10px;
padding: 18px;
}

#robots-app .panel-full {
background: #f8f9fc;
border: 1px solid #e0e4ef;
border-radius: 10px;
padding: 18px;
margin-top: 20px;
}

/* Presets */
#robots-app .preset-grid {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 20px;
}

#robots-app .preset-btn {
padding: 7px 14px;
border-radius: 20px;
border: 1.5px solid #5a6acf;
background: #fff;
color: #5a6acf;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
white-space: nowrap;
}

#robots-app .preset-btn:hover {
background: #5a6acf;
color: #fff;
}

/* Global settings */
#robots-app .global-settings {
margin-bottom: 20px;
}

#robots-app label {
display: block;
font-size: 0.82rem;
font-weight: 600;
color: #555;
margin-bottom: 4px;
}

#robots-app input[type="text"],
#robots-app input[type="number"],
#robots-app input[type="url"] {
width: 100%;
padding: 8px 10px;
border: 1.5px solid #d0d5e8;
border-radius: 6px;
font-size: 0.9rem;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.15s;
}

#robots-app input:focus {
border-color: #5a6acf;
}

#robots-app .field-row {
margin-bottom: 12px;
}

/* User-agent blocks */
#robots-app .ua-block {
background: #fff;
border: 1.5px solid #d0d5e8;
border-radius: 8px;
padding: 14px;
margin-bottom: 12px;
}

#robots-app .ua-block-header {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 10px;
}

#robots-app .ua-block-header input {
flex: 1;
}

#robots-app .btn-icon {
background: none;
border: none;
cursor: pointer;
font-size: 1.1rem;
padding: 2px 6px;
border-radius: 4px;
line-height: 1;
color: #888;
transition: color 0.15s, background 0.15s;
}

#robots-app .btn-icon:hover {
color: #e05252;
background: #fdecea;
}

#robots-app .rules-list {
margin-bottom: 8px;
}

#robots-app .rule-row {
display: flex;
align-items: center;
gap: 6px;
margin-bottom: 6px;
}

#robots-app .rule-type-select {
padding: 6px 8px;
border: 1.5px solid #d0d5e8;
border-radius: 6px;
font-size: 0.85rem;
background: #fff;
color: #1a1a2e;
cursor: pointer;
outline: none;
}

#robots-app .rule-type-select:focus {
border-color: #5a6acf;
}

#robots-app .rule-row input {
flex: 1;
}

#robots-app .btn-add-rule {
display: inline-flex;
align-items: center;
gap: 4px;
padding: 5px 12px;
border-radius: 6px;
border: 1.5px solid #5a6acf;
background: #fff;
color: #5a6acf;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}

#robots-app .btn-add-rule:hover {
background: #5a6acf;
color: #fff;
}

#robots-app .crawl-delay-row {
display: flex;
align-items: center;
gap: 8px;
margin-top: 8px;
}

#robots-app .crawl-delay-row label {
margin-bottom: 0;
white-space: nowrap;
font-size: 0.82rem;
}

#robots-app .crawl-delay-row input {
width: 80px;
}

#robots-app .btn-add-ua {
display: flex;
align-items: center;
gap: 6px;
padding: 9px 18px;
border-radius: 7px;
border: 2px dashed #5a6acf;
background: #fff;
color: #5a6acf;
font-size: 0.88rem;
font-weight: 600;
cursor: pointer;
width: 100%;
justify-content: center;
transition: background 0.15s;
margin-top: 4px;
}

#robots-app .btn-add-ua:hover {
background: #eef0fb;
}

/* Preview */
#robots-app .preview-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 10px;
flex-wrap: wrap;
gap: 8px;
}

#robots-app .preview-actions {
display: flex;
gap: 8px;
}

#robots-app .btn-copy,
#robots-app .btn-download {
padding: 7px 16px;
border-radius: 6px;
border: none;
font-size: 0.85rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, opacity 0.15s;
}

#robots-app .btn-copy {
background: #5a6acf;
color: #fff;
}

#robots-app .btn-copy:hover {
background: #4757b8;
}

#robots-app .btn-download {
background: #27ae60;
color: #fff;
}

#robots-app .btn-download:hover {
background: #1e9150;
}

#robots-app .btn-copy.copied {
background: #27ae60;
}

#robots-app pre#robots-preview {
background: #0f1117;
color: #a8ff78;
padding: 16px;
border-radius: 8px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.82rem;
line-height: 1.7;
white-space: pre;
overflow-x: auto;
min-height: 120px;
tab-size: 2;
}

/* Syntax colors */
#robots-app .syn-comment { color: #6b8fa0; }
#robots-app .syn-key     { color: #79b8ff; }
#robots-app .syn-colon   { color: #e0e0e0; }
#robots-app .syn-val-allow   { color: #a8ff78; }
#robots-app .syn-val-disallow { color: #ff7b7b; }
#robots-app .syn-val-sitemap { color: #ffd580; }
#robots-app .syn-val-neutral { color: #e0e0e0; }

#robots-app .info-badge {
display: inline-block;
background: #eef0fb;
color: #5a6acf;
border-radius: 4px;
font-size: 0.75rem;
padding: 2px 8px;
margin-left: 8px;
font-weight: 600;
}
</style>

<!-- Preset buttons -->
<div class="preset-grid">
<button class="preset-btn" onclick="robotsApplyPreset('allow-all')">Allow All</button>
<button class="preset-btn" onclick="robotsApplyPreset('block-all')">Block All</button>
<button class="preset-btn" onclick="robotsApplyPreset('block-ai')">Block AI Crawlers</button>
<button class="preset-btn" onclick="robotsApplyPreset('wordpress')">WordPress Default</button>
<button class="preset-btn" onclick="robotsApplyPreset('standard-seo')">Standard SEO</button>
<button class="preset-btn" onclick="robotsApplyPreset('clear')">Clear All</button>
</div>

<div class="robots-layout">
<!-- Left: editor -->
<div>
<!-- Global settings -->
<div class="panel global-settings">
<h2>Global Settings</h2>
<div class="field-row">
<label for="robots-sitemap">Sitemap URL</label>
<input type="url" id="robots-sitemap" placeholder="https://example.com/sitemap.xml" oninput="robotsRender()">
</div>
</div>

<!-- UA blocks -->
<div id="robots-ua-list"></div>
<button class="btn-add-ua" onclick="robotsAddUA()">+ Add User-agent Block</button>
</div>

<!-- Right: preview -->
<div>
<div class="panel-full" style="margin-top:0; height: 100%;">
<div class="preview-header">
<h2>Live Preview <span class="info-badge">robots.txt</span></h2>
<div class="preview-actions">
<button class="btn-copy" id="robots-copy-btn" onclick="robotsCopy()">Copy</button>
<button class="btn-download" onclick="robotsDownload()">Download .txt</button>
</div>
</div>
<pre id="robots-preview"></pre>
</div>
</div>
</div>

<script>
(function() {
// State
var state = {
sitemap: '',
blocks: []
};

var blockCounter = 0;

function uid() {
return 'b' + (++blockCounter);
}

function makeBlock(ua, rules, crawlDelay) {
return {
id: uid(),
ua: ua || '*',
rules: rules || [],
crawlDelay: crawlDelay || ''
};
}

function makeRule(type, path) {
return { type: type || 'Disallow', path: path || '' };
}

// Presets
var PRESETS = {
'allow-all': function() {
state.sitemap = '';
state.blocks = [makeBlock('*', [makeRule('Allow', '/')], '')];
},
'block-all': function() {
state.sitemap = '';
state.blocks = [makeBlock('*', [makeRule('Disallow', '/')], '')];
},
'block-ai': function() {
state.sitemap = '';
var aiAgents = [
'GPTBot', 'CCBot', 'ChatGPT-User', 'anthropic-ai',
'Claude-Web', 'Omgilibot', 'FacebookBot', 'Google-Extended',
'Bytespider', 'PerplexityBot', 'YouBot'
];
state.blocks = aiAgents.map(function(a) {
return makeBlock(a, [makeRule('Disallow', '/')], '');
});
state.blocks.unshift(makeBlock('*', [makeRule('Allow', '/')], ''));
},
'wordpress': function() {
state.sitemap = 'https://example.com/sitemap.xml';
state.blocks = [
makeBlock('*', [
makeRule('Disallow', '/wp-admin/'),
makeRule('Allow', '/wp-admin/admin-ajax.php')
], '')
];
},
'standard-seo': function() {
state.sitemap = 'https://example.com/sitemap.xml';
state.blocks = [
makeBlock('*', [
makeRule('Allow', '/'),
makeRule('Disallow', '/admin/'),
makeRule('Disallow', '/private/'),
makeRule('Disallow', '/*.pdf$')
], '10')
];
},
'clear': function() {
state.sitemap = '';
state.blocks = [];
}
};

window.robotsApplyPreset = function(name) {
if (PRESETS[name]) {
PRESETS[name]();
syncFormFromState();
robotsRender();
}
};

// ---- DOM rendering ----

function syncFormFromState() {
document.getElementById('robots-sitemap').value = state.sitemap;
var list = document.getElementById('robots-ua-list');
list.innerHTML = '';
state.blocks.forEach(function(block) {
list.appendChild(buildBlockEl(block));
});
}

function buildBlockEl(block) {
var div = document.createElement('div');
div.className = 'panel';
div.style.marginBottom = '12px';
div.dataset.id = block.id;

div.innerHTML =
'<div class="ua-block">' +
'<div class="ua-block-header">' +
'<span style="font-size:0.78rem;font-weight:700;color:#888;white-space:nowrap">User-agent</span>' +
'<input type="text" value="' + esc(block.ua) + '" placeholder="e.g. * or GPTBot"' +
' oninput="robotsUAChange(\'' + block.id + '\', this.value)">' +
'<button class="btn-icon" title="Remove block" onclick="robotsRemoveBlock(\'' + block.id + '\')">&times;</button>' +
'</div>' +
'<div class="rules-list" id="rules-' + block.id + '">' +
'</div>' +
'<button class="btn-add-rule" onclick="robotsAddRule(\'' + block.id + '\')">+ Add Rule</button>' +
'<div class="crawl-delay-row">' +
'<label>Crawl-delay (sec):</label>' +
'<input type="number" min="0" value="' + esc(block.crawlDelay) + '" placeholder="none"' +
' oninput="robotsCrawlDelayChange(\'' + block.id + '\', this.value)">' +
'</div>' +
'</div>';

var rulesEl = div.querySelector('#rules-' + block.id);
block.rules.forEach(function(rule, i) {
rulesEl.appendChild(buildRuleEl(block.id, rule, i));
});

return div;
}

function buildRuleEl(blockId, rule, idx) {
var row = document.createElement('div');
row.className = 'rule-row';
row.dataset.idx = idx;

var sel = document.createElement('select');
sel.className = 'rule-type-select';
['Allow', 'Disallow'].forEach(function(t) {
var opt = document.createElement('option');
opt.value = t;
opt.textContent = t;
if (rule.type === t) opt.selected = true;
sel.appendChild(opt);
});
sel.addEventListener('change', function() {
robotsRuleTypeChange(blockId, idx, this.value);
});

var inp = document.createElement('input');
inp.type = 'text';
inp.value = rule.path;
inp.placeholder = '/path/';
inp.addEventListener('input', function() {
robotsRulePathChange(blockId, idx, this.value);
});

var del = document.createElement('button');
del.className = 'btn-icon';
del.title = 'Remove rule';
del.innerHTML = '&times;';
del.addEventListener('click', function() {
robotsRemoveRule(blockId, idx);
});

row.appendChild(sel);
row.appendChild(inp);
row.appendChild(del);
return row;
}

function esc(s) {
return String(s || '').replace(/"/g, '&quot;').replace(/</g, '&lt;').replace(/>/g, '&gt;');
}

// ---- State mutation ----

function findBlock(id) {
return state.blocks.find(function(b) { return b.id === id; });
}

window.robotsAddUA = function() {
var block = makeBlock('*', [makeRule('Disallow', '/')], '');
state.blocks.push(block);
var list = document.getElementById('robots-ua-list');
list.appendChild(buildBlockEl(block));
robotsRender();
};

window.robotsRemoveBlock = function(id) {
state.blocks = state.blocks.filter(function(b) { return b.id !== id; });
var el = document.querySelector('[data-id="' + id + '"]');
if (el) el.remove();
robotsRender();
};

window.robotsUAChange = function(id, val) {
var b = findBlock(id);
if (b) { b.ua = val; robotsRender(); }
};

window.robotsCrawlDelayChange = function(id, val) {
var b = findBlock(id);
if (b) { b.crawlDelay = val; robotsRender(); }
};

window.robotsAddRule = function(id) {
var b = findBlock(id);
if (!b) return;
var rule = makeRule('Disallow', '');
b.rules.push(rule);
var rulesEl = document.getElementById('rules-' + id);
if (rulesEl) rulesEl.appendChild(buildRuleEl(id, rule, b.rules.length - 1));
robotsRender();
};

window.robotsRemoveRule = function(blockId, idx) {
var b = findBlock(blockId);
if (!b) return;
b.rules.splice(idx, 1);
// Re-render just the block
var blockEl = document.querySelector('[data-id="' + blockId + '"]');
if (blockEl) {
var newEl = buildBlockEl(b);
blockEl.replaceWith(newEl);
}
robotsRender();
};

window.robotsRuleTypeChange = function(blockId, idx, val) {
var b = findBlock(blockId);
if (b && b.rules[idx]) { b.rules[idx].type = val; robotsRender(); }
};

window.robotsRulePathChange = function(blockId, idx, val) {
var b = findBlock(blockId);
if (b && b.rules[idx]) { b.rules[idx].path = val; robotsRender(); }
};

window.robotsRender = function() {
state.sitemap = document.getElementById('robots-sitemap').value.trim();
var lines = [];

if (state.blocks.length === 0 && !state.sitemap) {
document.getElementById('robots-preview').innerHTML =
'<span class="syn-comment"># Your robots.txt will appear here...</span>';
return;
}

state.blocks.forEach(function(block, bi) {
if (bi > 0) lines.push('');
lines.push({ key: 'User-agent', val: block.ua });
block.rules.forEach(function(rule) {
lines.push({ key: rule.type, val: rule.path });
});
if (block.crawlDelay && block.crawlDelay !== '') {
lines.push({ key: 'Crawl-delay', val: block.crawlDelay });
}
});

if (state.sitemap) {
lines.push('');
lines.push({ key: 'Sitemap', val: state.sitemap });
}

// Build highlighted HTML
var html = lines.map(function(line) {
if (line === '') return '';
if (typeof line === 'string') {
return '<span class="syn-comment">' + htmlEsc(line) + '</span>';
}
var keyClass = 'syn-key';
var valClass = 'syn-val-neutral';
if (line.key === 'Allow') valClass = 'syn-val-allow';
else if (line.key === 'Disallow') valClass = 'syn-val-disallow';
else if (line.key === 'Sitemap') valClass = 'syn-val-sitemap';

return '<span class="' + keyClass + '">' + htmlEsc(line.key) + '</span>' +
'<span class="syn-colon">: </span>' +
'<span class="' + valClass + '">' + htmlEsc(line.val) + '</span>';
}).join('\n');

document.getElementById('robots-preview').innerHTML = html || '<span class="syn-comment"># Empty</span>';
};

function htmlEsc(s) {
return String(s || '').replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;');
}

function getRawText() {
var lines = [];
state.sitemap = document.getElementById('robots-sitemap').value.trim();

state.blocks.forEach(function(block, bi) {
if (bi > 0) lines.push('');
lines.push('User-agent: ' + block.ua);
block.rules.forEach(function(rule) {
lines.push(rule.type + ': ' + rule.path);
});
if (block.crawlDelay && block.crawlDelay !== '') {
lines.push('Crawl-delay: ' + block.crawlDelay);
}
});

if (state.sitemap) {
lines.push('');
lines.push('Sitemap: ' + state.sitemap);
}

return lines.join('\n');
}

window.robotsCopy = function() {
var text = getRawText();
navigator.clipboard.writeText(text).then(function() {
var btn = document.getElementById('robots-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 2000);
}).catch(function() {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
});
};

window.robotsDownload = function() {
var text = getRawText();
var blob = new Blob([text], { type: 'text/plain' });
var url = URL.createObjectURL(blob);
var a = document.createElement('a');
a.href = url;
a.download = 'robots.txt';
a.click();
URL.revokeObjectURL(url);
};

// Init with Allow All preset
PRESETS['allow-all']();
syncFormFromState();
robotsRender();
})();
</script>

</div>

---

### Related Tools

> Generate meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)

> Format SQL queries → [SQL Formatter](/tools/sql-formatter/)

> Build cron expressions → [Cron Expression Generator](/tools/cron-generator/)

## Related Articles

- [Best Web Hosting 2026: Compared for Speed, Price & WordPress](/posts/best-web-hosting-2026/)
