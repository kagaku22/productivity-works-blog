---
title: "Typography Scale Generator — Modular Type System"
date: 2025-05-16
description: "Generate modular typography scales for web design. Choose ratio, base size, and preview all heading sizes. Copy CSS with rem/px values and line-height."
categories: ["Free Tools"]
slug: "typography-scale"
ShowToc: false
cover:
  image: "/images/covers/typography-scale.png"
  alt: "Typography Scale Generator"
---

<div id="ts-app2">

<style>
#ts-app2 *,
#ts-app2 *::before,
#ts-app2 *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#ts-app2 {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1a1a2e;
line-height: 1.6;
max-width: 900px;
margin: 0 auto;
padding: 0 16px;
}

#ts-app2 .ts-card {
background: #ffffff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}

#ts-app2 .ts-hero {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: #fff;
border-radius: 14px;
padding: 36px 28px 28px;
margin-bottom: 24px;
text-align: center;
}

#ts-app2 .ts-hero h2 {
font-size: 1.75rem;
font-weight: 800;
margin-bottom: 8px;
letter-spacing: -0.02em;
}

#ts-app2 .ts-hero p {
font-size: 1rem;
opacity: 0.88;
}

#ts-app2 .ts-section-title {
font-size: 0.8rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #7c3aed;
margin-bottom: 14px;
}

#ts-app2 .ts-controls-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
gap: 16px;
margin-bottom: 16px;
}

#ts-app2 .ts-field label {
display: block;
font-size: 0.8rem;
font-weight: 600;
color: #374151;
margin-bottom: 6px;
}

#ts-app2 .ts-field input[type="number"],
#ts-app2 .ts-field select {
width: 100%;
padding: 10px 14px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 0.95rem;
background: #f9fafb;
color: #1a1a2e;
transition: border-color 0.2s;
appearance: none;
-webkit-appearance: none;
}

#ts-app2 .ts-field input[type="number"]:focus,
#ts-app2 .ts-field select:focus {
outline: none;
border-color: #7c3aed;
background: #fff;
}

#ts-app2 .ts-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 6px;
}

#ts-app2 .ts-preset-btn {
padding: 6px 14px;
border-radius: 20px;
border: 1.5px solid #d1d5db;
background: #f9fafb;
font-size: 0.8rem;
font-weight: 600;
color: #374151;
cursor: pointer;
transition: all 0.15s;
}

#ts-app2 .ts-preset-btn:hover,
#ts-app2 .ts-preset-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

#ts-app2 .ts-unit-toggle {
display: flex;
gap: 6px;
flex-wrap: wrap;
}

#ts-app2 .ts-unit-btn {
padding: 6px 16px;
border-radius: 8px;
border: 1.5px solid #d1d5db;
background: #f9fafb;
font-size: 0.82rem;
font-weight: 700;
color: #374151;
cursor: pointer;
transition: all 0.15s;
}

#ts-app2 .ts-unit-btn.active {
background: #7c3aed;
border-color: #7c3aed;
color: #fff;
}

#ts-app2 .ts-scale-table {
width: 100%;
border-collapse: collapse;
margin-bottom: 8px;
}

#ts-app2 .ts-scale-table th {
font-size: 0.75rem;
font-weight: 700;
color: #6b7280;
text-transform: uppercase;
letter-spacing: 0.06em;
padding: 8px 12px;
text-align: left;
border-bottom: 2px solid #e5e7eb;
background: #f9fafb;
}

#ts-app2 .ts-scale-table td {
padding: 10px 12px;
border-bottom: 1px solid #f0f0f0;
vertical-align: middle;
}

#ts-app2 .ts-scale-table tr:last-child td {
border-bottom: none;
}

#ts-app2 .ts-scale-table tr:hover td {
background: #faf5ff;
}

#ts-app2 .ts-tag-label {
display: inline-block;
background: #ede9fe;
color: #7c3aed;
font-size: 0.75rem;
font-weight: 700;
padding: 2px 8px;
border-radius: 5px;
letter-spacing: 0.04em;
}

#ts-app2 .ts-size-value {
font-family: "SF Mono", "Fira Code", "Fira Mono", monospace;
font-size: 0.82rem;
color: #374151;
}

#ts-app2 .ts-lh-value {
font-size: 0.78rem;
color: #6b7280;
}

#ts-app2 .ts-preview-col {
max-width: 260px;
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
}

#ts-app2 .ts-preview-text {
color: #1a1a2e;
font-weight: 600;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
display: block;
}

#ts-app2 .ts-css-output {
position: relative;
background: #1e1e2e;
border-radius: 10px;
padding: 20px;
overflow: auto;
max-height: 400px;
}

#ts-app2 .ts-css-output pre {
font-family: "SF Mono", "Fira Code", "Fira Mono", monospace;
font-size: 0.82rem;
line-height: 1.7;
color: #cdd6f4;
white-space: pre;
margin: 0;
}

#ts-app2 .ts-css-output .tok-prop   { color: #89b4fa; }
#ts-app2 .ts-css-output .tok-val    { color: #a6e3a1; }
#ts-app2 .tok-selector              { color: #cba6f7; }
#ts-app2 .tok-comment               { color: #6c7086; font-style: italic; }
#ts-app2 .tok-brace                 { color: #f38ba8; }

#ts-app2 .ts-copy-btn {
position: absolute;
top: 14px;
right: 14px;
padding: 6px 14px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 7px;
font-size: 0.78rem;
font-weight: 700;
cursor: pointer;
transition: background 0.15s;
letter-spacing: 0.03em;
}

#ts-app2 .ts-copy-btn:hover { background: #6d28d9; }
#ts-app2 .ts-copy-btn.copied { background: #059669; }

#ts-app2 .ts-crosslinks {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 4px;
}

#ts-app2 .ts-crosslinks a {
color: #7c3aed;
text-decoration: none;
font-size: 0.85rem;
font-weight: 600;
padding: 5px 12px;
border: 1.5px solid #ddd6fe;
border-radius: 8px;
background: #faf5ff;
transition: all 0.15s;
}

#ts-app2 .ts-crosslinks a:hover {
background: #7c3aed;
color: #fff;
border-color: #7c3aed;
}

#ts-app2 .ts-info-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 10px;
}

#ts-app2 .ts-info-chip {
background: #f0fdf4;
border: 1px solid #bbf7d0;
color: #166534;
font-size: 0.78rem;
font-weight: 600;
padding: 4px 12px;
border-radius: 20px;
}

@media (max-width: 600px) {
#ts-app2 .ts-hero h2 { font-size: 1.3rem; }
#ts-app2 .ts-controls-grid { grid-template-columns: 1fr; }
#ts-app2 .ts-scale-table th:nth-child(4),
#ts-app2 .ts-scale-table td:nth-child(4) { display: none; }
#ts-app2 .ts-preview-col { max-width: 120px; }
}
</style>

<div class="ts-hero">
<h2>Typography Scale Generator</h2>
<p>Build modular type scales for harmonious, consistent web typography</p>
</div>

<div class="ts-card">
<div class="ts-section-title">Presets</div>
<div class="ts-presets">
<button class="ts-preset-btn" data-preset="blog">Blog</button>
<button class="ts-preset-btn" data-preset="app">App UI</button>
<button class="ts-preset-btn" data-preset="docs">Documentation</button>
<button class="ts-preset-btn" data-preset="landing">Landing Page</button>
</div>
</div>

<div class="ts-card">
<div class="ts-section-title">Settings</div>
<div class="ts-controls-grid">
<div class="ts-field">
<label for="ts-base-size">Base Font Size (px)</label>
<input type="number" id="ts-base-size" value="16" min="10" max="24" step="1">
</div>
<div class="ts-field">
<label for="ts-ratio">Scale Ratio</label>
<select id="ts-ratio">
<option value="1.067">Minor Second — 1.067</option>
<option value="1.125">Major Second — 1.125</option>
<option value="1.2">Minor Third — 1.200</option>
<option value="1.25" selected>Major Third — 1.250</option>
<option value="1.333">Perfect Fourth — 1.333</option>
<option value="1.414">Augmented Fourth — 1.414</option>
<option value="1.5">Perfect Fifth — 1.500</option>
<option value="1.618">Golden Ratio — 1.618</option>
</select>
</div>
</div>
<div class="ts-field">
<label>Output Unit</label>
<div class="ts-unit-toggle">
<button class="ts-unit-btn active" data-unit="rem">rem</button>
<button class="ts-unit-btn" data-unit="px">px</button>
<button class="ts-unit-btn" data-unit="em">em</button>
</div>
</div>
</div>

<div class="ts-card">
<div class="ts-section-title">Type Scale Preview</div>
<div style="overflow-x:auto;">
<table class="ts-scale-table" id="ts-scale-table">
<thead>
<tr>
<th>Level</th>
<th>Size</th>
<th>Line Height</th>
<th>Preview</th>
</tr>
</thead>
<tbody id="ts-scale-tbody"></tbody>
</table>
</div>
<div class="ts-info-row" id="ts-info-row"></div>
</div>

<div class="ts-card">
<div class="ts-section-title">CSS Output</div>
<div class="ts-css-output">
<button class="ts-copy-btn" id="ts-copy-btn">Copy CSS</button>
<pre id="ts-css-pre"></pre>
</div>
</div>

<div class="ts-card">
<div class="ts-section-title">Related Tools</div>
<div class="ts-crosslinks">
<a href="/tools/css-variables-generator/">CSS Variables Generator</a>
<a href="/tools/font-pair-suggester/">Font Pair Suggester</a>
<a href="/tools/reading-time-calculator/">Reading Time Calculator</a>
</div>
</div>

<script>
(function() {
'use strict';

const LEVELS = [
{ label: 'h1', step: 5, previewText: 'Heading One' },
{ label: 'h2', step: 4, previewText: 'Heading Two' },
{ label: 'h3', step: 3, previewText: 'Heading Three' },
{ label: 'h4', step: 2, previewText: 'Heading Four' },
{ label: 'h5', step: 1, previewText: 'Heading Five' },
{ label: 'body', step: 0, previewText: 'Body text — comfortable reading size' },
{ label: 'small', step: -1, previewText: 'Small / Caption text' },
];

const LINE_HEIGHTS = {
5: 1.1, 4: 1.15, 3: 1.2, 2: 1.25, 1: 1.35, 0: 1.6, '-1': 1.65
};

const PRESETS = {
blog:    { base: 18, ratio: '1.25' },
app:     { base: 14, ratio: '1.2'  },
docs:    { base: 16, ratio: '1.25' },
landing: { base: 18, ratio: '1.333' },
};

let currentUnit = 'rem';

const baseInput  = document.getElementById('ts-base-size');
const ratioSel   = document.getElementById('ts-ratio');
const tbody      = document.getElementById('ts-scale-tbody');
const cssPre     = document.getElementById('ts-css-pre');
const copyBtn    = document.getElementById('ts-copy-btn');
const infoRow    = document.getElementById('ts-info-row');

function calcSize(base, ratio, step) {
return base * Math.pow(ratio, step);
}

function formatSize(px, unit, base) {
if (unit === 'px')  return px.toFixed(2) + 'px';
if (unit === 'rem') return (px / base).toFixed(4) + 'rem';
if (unit === 'em')  return (px / base).toFixed(4) + 'em';
return px.toFixed(2) + 'px';
}

function render() {
const base  = parseFloat(baseInput.value) || 16;
const ratio = parseFloat(ratioSel.value)  || 1.25;

// Build rows
let tbodyHtml = '';
LEVELS.forEach(function(lvl) {
const px = calcSize(base, ratio, lvl.step);
const lh = LINE_HEIGHTS[lvl.step] || 1.5;
const sizeStr = formatSize(px, currentUnit, base);
const previewPx = Math.round(px);

tbodyHtml += '<tr>' +
'<td><span class="ts-tag-label">' + lvl.label + '</span></td>' +
'<td><span class="ts-size-value">' + sizeStr + '</span></td>' +
'<td><span class="ts-lh-value">' + lh.toFixed(2) + '</span></td>' +
'<td class="ts-preview-col"><span class="ts-preview-text" style="font-size:' + Math.min(previewPx, 48) + 'px;line-height:' + lh + '">' + lvl.previewText + '</span></td>' +
'</tr>';
});
tbody.innerHTML = tbodyHtml;

// Info chips
const ratioName = ratioSel.options[ratioSel.selectedIndex].text;
infoRow.innerHTML =
'<span class="ts-info-chip">Base: ' + base + 'px</span>' +
'<span class="ts-info-chip">Ratio: ' + ratio + '</span>' +
'<span class="ts-info-chip">' + ratioName.split('—')[0].trim() + '</span>' +
'<span class="ts-info-chip">Unit: ' + currentUnit + '</span>';

// CSS output
renderCSS(base, ratio);
}

function renderCSS(base, ratio) {
var lines = [];
lines.push('<span class="tok-comment">/* Typography Scale — Generated by ProductivityWorks */</span>');
lines.push('<span class="tok-comment">/* Base: ' + base + 'px | Ratio: ' + ratio + ' (' + ratioSel.options[ratioSel.selectedIndex].text.split('—')[0].trim() + ') */</span>');
lines.push('');
lines.push('<span class="tok-selector">:root</span> <span class="tok-brace">{</span>');

LEVELS.forEach(function(lvl) {
const px = calcSize(base, ratio, lvl.step);
const lh = LINE_HEIGHTS[lvl.step] || 1.5;
const sizeStr = formatSize(px, currentUnit, base);
lines.push('  <span class="tok-prop">--font-size-' + lvl.label + '</span>: <span class="tok-val">' + sizeStr + '</span>;');
lines.push('  <span class="tok-prop">--line-height-' + lvl.label + '</span>: <span class="tok-val">' + lh.toFixed(2) + '</span>;');
});

lines.push('<span class="tok-brace">}</span>');
lines.push('');

LEVELS.filter(function(l) { return l.label.startsWith('h'); }).forEach(function(lvl) {
const px = calcSize(base, ratio, lvl.step);
const lh = LINE_HEIGHTS[lvl.step] || 1.5;
const sizeStr = formatSize(px, currentUnit, base);
lines.push('<span class="tok-selector">' + lvl.label + '</span> <span class="tok-brace">{</span>');
lines.push('  <span class="tok-prop">font-size</span>: <span class="tok-val">' + sizeStr + '</span>;');
lines.push('  <span class="tok-prop">line-height</span>: <span class="tok-val">' + lh.toFixed(2) + '</span>;');
lines.push('<span class="tok-brace">}</span>');
lines.push('');
});

lines.push('<span class="tok-selector">body</span> <span class="tok-brace">{</span>');
lines.push('  <span class="tok-prop">font-size</span>: <span class="tok-val">' + formatSize(base, currentUnit, base) + '</span>;');
lines.push('  <span class="tok-prop">line-height</span>: <span class="tok-val">1.60</span>;');
lines.push('<span class="tok-brace">}</span>');
lines.push('');
lines.push('<span class="tok-selector">small, .text-small</span> <span class="tok-brace">{</span>');
const smallPx = calcSize(base, ratio, -1);
lines.push('  <span class="tok-prop">font-size</span>: <span class="tok-val">' + formatSize(smallPx, currentUnit, base) + '</span>;');
lines.push('  <span class="tok-prop">line-height</span>: <span class="tok-val">1.65</span>;');
lines.push('<span class="tok-brace">}</span>');

cssPre.innerHTML = lines.join('\n');
}

function getPlainCSS() {
const base  = parseFloat(baseInput.value) || 16;
const ratio = parseFloat(ratioSel.value)  || 1.25;
var lines = [];
lines.push('/* Typography Scale — Generated by ProductivityWorks */');
lines.push('/* Base: ' + base + 'px | Ratio: ' + ratio + ' (' + ratioSel.options[ratioSel.selectedIndex].text.split('—')[0].trim() + ') */');
lines.push('');
lines.push(':root {');
LEVELS.forEach(function(lvl) {
const px = calcSize(base, ratio, lvl.step);
const lh = LINE_HEIGHTS[lvl.step] || 1.5;
const sizeStr = formatSize(px, currentUnit, base);
lines.push('  --font-size-' + lvl.label + ': ' + sizeStr + ';');
lines.push('  --line-height-' + lvl.label + ': ' + lh.toFixed(2) + ';');
});
lines.push('}');
lines.push('');
LEVELS.filter(function(l) { return l.label.startsWith('h'); }).forEach(function(lvl) {
const px = calcSize(base, ratio, lvl.step);
const lh = LINE_HEIGHTS[lvl.step] || 1.5;
const sizeStr = formatSize(px, currentUnit, base);
lines.push(lvl.label + ' {');
lines.push('  font-size: ' + sizeStr + ';');
lines.push('  line-height: ' + lh.toFixed(2) + ';');
lines.push('}');
lines.push('');
});
lines.push('body {');
lines.push('  font-size: ' + formatSize(base, currentUnit, base) + ';');
lines.push('  line-height: 1.60;');
lines.push('}');
lines.push('');
lines.push('small, .text-small {');
const smallPx = calcSize(base, ratio, -1);
lines.push('  font-size: ' + formatSize(smallPx, currentUnit, base) + ';');
lines.push('  line-height: 1.65;');
lines.push('}');
return lines.join('\n');
}

// Copy button
copyBtn.addEventListener('click', function() {
var text = getPlainCSS();
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() {
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'Copy CSS';
copyBtn.classList.remove('copied');
}, 2000);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.focus();
ta.select();
try { document.execCommand('copy'); } catch(e) {}
document.body.removeChild(ta);
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'Copy CSS';
copyBtn.classList.remove('copied');
}, 2000);
}
});

// Unit toggle
document.querySelectorAll('#ts-app2 .ts-unit-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#ts-app2 .ts-unit-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
currentUnit = btn.dataset.unit;
render();
});
});

// Preset buttons
document.querySelectorAll('#ts-app2 .ts-preset-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
document.querySelectorAll('#ts-app2 .ts-preset-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
var p = PRESETS[btn.dataset.preset];
if (p) {
baseInput.value = p.base;
ratioSel.value  = p.ratio;
render();
}
});
});

// Input listeners
baseInput.addEventListener('input', render);
ratioSel.addEventListener('change', render);

// Init
render();
})();
</script>

</div>
