---
title: "Font Size Converter - px, rem, em, pt, %"
date: 2025-05-16
description: "Free font size converter. Convert between px, rem, em, pt, %, and vw units instantly. Set custom base font size. Visual preview with live text sample."
categories: ["Free Tools"]
slug: "font-size-converter"
ShowToc: false
cover:
  image: "/images/covers/font-size-converter.png"
  alt: "Font Size Converter - px, rem, em, pt, %"
---

<div id="fs-app">

<style>
#fs-app *,
#fs-app *::before,
#fs-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#fs-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1a1a2e;
line-height: 1.6;
max-width: 860px;
margin: 0 auto;
padding: 0 16px;
}

/* Hero */
#fs-app .fs-hero {
background: linear-gradient(135deg, #0ea5e9 0%, #6366f1 100%);
color: #fff;
border-radius: 14px;
padding: 36px 28px 28px;
margin-bottom: 24px;
text-align: center;
}

#fs-app .fs-hero h2 {
font-size: 1.75rem;
font-weight: 800;
margin-bottom: 8px;
letter-spacing: -0.02em;
}

#fs-app .fs-hero p {
font-size: 1rem;
opacity: 0.9;
}

/* Cards */
#fs-app .fs-card {
background: #ffffff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}

#fs-app .fs-section-title {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #0ea5e9;
margin-bottom: 16px;
}

/* Base font size row */
#fs-app .fs-base-row {
display: flex;
align-items: center;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 0;
}

#fs-app .fs-base-row label {
font-size: 0.875rem;
font-weight: 600;
color: #374151;
white-space: nowrap;
}

#fs-app .fs-base-input {
width: 80px;
padding: 7px 10px;
border: 1px solid #cbd5e1;
border-radius: 8px;
font-size: 0.95rem;
color: #1a1a2e;
background: #f8fafc;
transition: border-color 0.15s;
}

#fs-app .fs-base-input:focus {
outline: none;
border-color: #0ea5e9;
background: #fff;
}

#fs-app .fs-base-note {
font-size: 0.8rem;
color: #64748b;
}

/* Converter grid */
#fs-app .fs-converter-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
gap: 14px;
}

#fs-app .fs-unit-block {
background: #f8fafc;
border: 2px solid #e2e8f0;
border-radius: 10px;
padding: 16px;
transition: border-color 0.15s, box-shadow 0.15s;
}

#fs-app .fs-unit-block:focus-within {
border-color: #0ea5e9;
box-shadow: 0 0 0 3px rgba(14,165,233,0.12);
}

#fs-app .fs-unit-label {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #64748b;
margin-bottom: 8px;
}

#fs-app .fs-unit-input-row {
display: flex;
align-items: center;
gap: 6px;
}

#fs-app .fs-unit-input {
flex: 1;
min-width: 0;
padding: 8px 10px;
border: 1px solid #cbd5e1;
border-radius: 7px;
font-size: 1.05rem;
font-weight: 600;
color: #1a1a2e;
background: #fff;
transition: border-color 0.15s;
}

#fs-app .fs-unit-input:focus {
outline: none;
border-color: #0ea5e9;
}

#fs-app .fs-copy-btn {
flex-shrink: 0;
padding: 7px 10px;
background: #e0f2fe;
border: none;
border-radius: 7px;
color: #0369a1;
font-size: 0.78rem;
font-weight: 700;
cursor: pointer;
white-space: nowrap;
transition: background 0.15s, color 0.15s;
}

#fs-app .fs-copy-btn:hover {
background: #0ea5e9;
color: #fff;
}

#fs-app .fs-copy-btn.copied {
background: #22c55e;
color: #fff;
}

#fs-app .fs-unit-desc {
font-size: 0.72rem;
color: #94a3b8;
margin-top: 6px;
}

/* Live Preview */
#fs-app .fs-preview-box {
border: 1px dashed #cbd5e1;
border-radius: 8px;
padding: 20px 18px;
min-height: 80px;
display: flex;
align-items: center;
justify-content: center;
background: #f8fafc;
overflow: hidden;
}

#fs-app .fs-preview-text {
font-weight: 600;
color: #1a1a2e;
transition: font-size 0.2s;
word-break: break-word;
text-align: center;
line-height: 1.3;
}

#fs-app .fs-preview-meta {
font-size: 0.8rem;
color: #64748b;
margin-top: 10px;
text-align: center;
}

/* Conversion Table */
#fs-app .fs-table-wrap {
overflow-x: auto;
-webkit-overflow-scrolling: touch;
}

#fs-app .fs-table {
width: 100%;
border-collapse: collapse;
font-size: 0.875rem;
min-width: 560px;
}

#fs-app .fs-table thead tr {
background: #0ea5e9;
color: #fff;
}

#fs-app .fs-table thead th {
padding: 10px 12px;
font-weight: 700;
text-align: right;
letter-spacing: 0.03em;
}

#fs-app .fs-table thead th:first-child {
text-align: center;
border-radius: 8px 0 0 0;
}

#fs-app .fs-table thead th:last-child {
border-radius: 0 8px 0 0;
}

#fs-app .fs-table tbody tr:nth-child(odd) {
background: #f8fafc;
}

#fs-app .fs-table tbody tr:hover {
background: #e0f2fe;
}

#fs-app .fs-table tbody td {
padding: 9px 12px;
border-bottom: 1px solid #f1f5f9;
text-align: right;
font-variant-numeric: tabular-nums;
color: #374151;
}

#fs-app .fs-table tbody td:first-child {
text-align: center;
font-weight: 700;
color: #0ea5e9;
}

#fs-app .fs-table-note {
font-size: 0.75rem;
color: #94a3b8;
margin-top: 8px;
}

/* Formulas */
#fs-app .fs-formula-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
gap: 12px;
}

#fs-app .fs-formula-item {
background: #f8fafc;
border-left: 3px solid #0ea5e9;
border-radius: 0 8px 8px 0;
padding: 12px 14px;
}

#fs-app .fs-formula-unit {
font-size: 0.72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #0ea5e9;
margin-bottom: 4px;
}

#fs-app .fs-formula-eq {
font-family: "SF Mono", "Fira Code", "Consolas", monospace;
font-size: 0.82rem;
color: #1e293b;
margin-bottom: 3px;
}

#fs-app .fs-formula-note {
font-size: 0.72rem;
color: #64748b;
}

/* Related Tools */
#fs-app .fs-crosslinks {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 4px;
}

#fs-app .fs-crosslinks a {
color: #0ea5e9;
text-decoration: none;
font-size: 0.85rem;
font-weight: 600;
padding: 5px 12px;
border: 1.5px solid #bae6fd;
border-radius: 20px;
transition: background 0.15s, color 0.15s, border-color 0.15s;
}

#fs-app .fs-crosslinks a:hover {
background: #0ea5e9;
color: #fff;
border-color: #0ea5e9;
}

/* Responsive */
@media (max-width: 600px) {
#fs-app .fs-hero { padding: 28px 18px 22px; }
#fs-app .fs-hero h2 { font-size: 1.4rem; }
#fs-app .fs-card { padding: 18px 14px; }
#fs-app .fs-converter-grid { grid-template-columns: 1fr 1fr; }
}

@media (max-width: 400px) {
#fs-app .fs-converter-grid { grid-template-columns: 1fr; }
}
</style>

<!-- Hero -->
<div class="fs-hero">
<h2>Font Size Converter</h2>
<p>Convert between px, rem, em, pt, %, and vw instantly. Set your base font size and see live results.</p>
</div>

<!-- Settings: Base Font Size -->
<div class="fs-card">
<div class="fs-section-title">Base Font Size</div>
<div class="fs-base-row">
<label for="fs-base">Root font size (px):</label>
<input class="fs-base-input" type="number" id="fs-base" value="16" min="1" max="100" step="0.5" />
<span class="fs-base-note">Browser default is 16px. Change to match your project.</span>
</div>
</div>

<!-- Converter -->
<div class="fs-card">
<div class="fs-section-title">Unit Converter — type in any field</div>
<div class="fs-converter-grid">

<div class="fs-unit-block">
<div class="fs-unit-label">px — Pixels</div>
<div class="fs-unit-input-row">
<input class="fs-unit-input" id="fs-px" type="number" min="0" step="0.5" placeholder="16" />
<button class="fs-copy-btn" data-copy="fs-px">Copy</button>
</div>
<div class="fs-unit-desc">Absolute screen pixels</div>
</div>

<div class="fs-unit-block">
<div class="fs-unit-label">rem — Root EM</div>
<div class="fs-unit-input-row">
<input class="fs-unit-input" id="fs-rem" type="number" min="0" step="0.0625" placeholder="1" />
<button class="fs-copy-btn" data-copy="fs-rem">Copy</button>
</div>
<div class="fs-unit-desc">Relative to root element font size</div>
</div>

<div class="fs-unit-block">
<div class="fs-unit-label">em — Element EM</div>
<div class="fs-unit-input-row">
<input class="fs-unit-input" id="fs-em" type="number" min="0" step="0.0625" placeholder="1" />
<button class="fs-copy-btn" data-copy="fs-em">Copy</button>
</div>
<div class="fs-unit-desc">Relative to parent element font size</div>
</div>

<div class="fs-unit-block">
<div class="fs-unit-label">pt — Points</div>
<div class="fs-unit-input-row">
<input class="fs-unit-input" id="fs-pt" type="number" min="0" step="0.5" placeholder="12" />
<button class="fs-copy-btn" data-copy="fs-pt">Copy</button>
</div>
<div class="fs-unit-desc">Print unit: 1pt = 1/72 inch = 1.333px</div>
</div>

<div class="fs-unit-block">
<div class="fs-unit-label">% — Percent</div>
<div class="fs-unit-input-row">
<input class="fs-unit-input" id="fs-pct" type="number" min="0" step="1" placeholder="100" />
<button class="fs-copy-btn" data-copy="fs-pct">Copy</button>
</div>
<div class="fs-unit-desc">% of parent/root font size</div>
</div>

<div class="fs-unit-block">
<div class="fs-unit-label">vw — Viewport Width</div>
<div class="fs-unit-input-row">
<input class="fs-unit-input" id="fs-vw" type="number" min="0" step="0.01" placeholder="1" />
<button class="fs-copy-btn" data-copy="fs-vw">Copy</button>
</div>
<div class="fs-unit-desc">1vw = 1% of viewport width (assumes 1440px)</div>
</div>

</div>
</div>

<!-- Live Preview -->
<div class="fs-card">
<div class="fs-section-title">Live Preview</div>
<div class="fs-preview-box">
<span class="fs-preview-text" id="fs-preview-text">The quick brown fox jumps over the lazy dog.</span>
</div>
<p class="fs-preview-meta" id="fs-preview-meta">Rendering at 16px</p>
</div>

<!-- Conversion Table -->
<div class="fs-card">
<div class="fs-section-title">Conversion Table — Common Sizes</div>
<div class="fs-table-wrap">
<table class="fs-table" id="fs-table">
<thead>
<tr>
<th>px</th>
<th>rem</th>
<th>em</th>
<th>pt</th>
<th>%</th>
<th>vw (1440px)</th>
</tr>
</thead>
<tbody id="fs-table-body"></tbody>
</table>
</div>
<p class="fs-table-note" id="fs-table-note">Calculated with base = 16px. Change base above to update.</p>
</div>

<!-- Formulas -->
<div class="fs-card">
<div class="fs-section-title">Conversion Formulas</div>
<div class="fs-formula-grid">
<div class="fs-formula-item">
<div class="fs-formula-unit">px → rem</div>
<div class="fs-formula-eq">rem = px ÷ base</div>
<div class="fs-formula-note">e.g. 24px ÷ 16 = 1.5rem</div>
</div>
<div class="fs-formula-item">
<div class="fs-formula-unit">rem → px</div>
<div class="fs-formula-eq">px = rem × base</div>
<div class="fs-formula-note">e.g. 1.5rem × 16 = 24px</div>
</div>
<div class="fs-formula-item">
<div class="fs-formula-unit">px → em</div>
<div class="fs-formula-eq">em = px ÷ parent-px</div>
<div class="fs-formula-note">Same as rem when parent = root</div>
</div>
<div class="fs-formula-item">
<div class="fs-formula-unit">px → pt</div>
<div class="fs-formula-eq">pt = px × 0.75</div>
<div class="fs-formula-note">e.g. 16px × 0.75 = 12pt</div>
</div>
<div class="fs-formula-item">
<div class="fs-formula-unit">px → %</div>
<div class="fs-formula-eq">% = (px ÷ base) × 100</div>
<div class="fs-formula-note">e.g. (16 ÷ 16) × 100 = 100%</div>
</div>
<div class="fs-formula-item">
<div class="fs-formula-unit">px → vw</div>
<div class="fs-formula-eq">vw = (px ÷ vp) × 100</div>
<div class="fs-formula-note">vp = viewport width (default 1440px)</div>
</div>
</div>
</div>

<!-- Related Tools -->
<div class="fs-card">
<div class="fs-section-title">Related Tools</div>
<div class="fs-crosslinks">
<a href="/tools/typography-scale/">Typography Scale Generator</a>
<a href="/tools/css-variables-generator/">CSS Variables Generator</a>
</div>
</div>

<script>
(function() {
'use strict';

var BASE_DEFAULT = 16;
var VIEWPORT_W   = 1440;
var TABLE_SIZES  = [8, 10, 12, 14, 16, 18, 20, 24, 32, 48, 64, 96];

var baseEl    = document.getElementById('fs-base');
var pxEl      = document.getElementById('fs-px');
var remEl     = document.getElementById('fs-rem');
var emEl      = document.getElementById('fs-em');
var ptEl      = document.getElementById('fs-pt');
var pctEl     = document.getElementById('fs-pct');
var vwEl      = document.getElementById('fs-vw');
var previewEl = document.getElementById('fs-preview-text');
var metaEl    = document.getElementById('fs-preview-meta');
var tbodyEl   = document.getElementById('fs-table-body');
var tableNote = document.getElementById('fs-table-note');

var MAX_PREVIEW_PX = 120;
var MIN_PREVIEW_PX = 6;

function getBase() {
var v = parseFloat(baseEl.value);
return (v > 0) ? v : BASE_DEFAULT;
}

// Round to 4 sig figs, remove trailing zeros
function fmt(n, decimals) {
if (n === null || isNaN(n)) return '';
return parseFloat(n.toFixed(decimals !== undefined ? decimals : 4)).toString();
}

// Convert from px to all units
function pxToAll(px, base) {
return {
px:  fmt(px, 4),
rem: fmt(px / base, 4),
em:  fmt(px / base, 4),
pt:  fmt(px * 0.75, 4),
pct: fmt((px / base) * 100, 2),
vw:  fmt((px / VIEWPORT_W) * 100, 4)
};
}

var updating = false;

function updateFromPx(px) {
if (updating) return;
updating = true;
var base = getBase();
var v = pxToAll(px, base);
pxEl.value  = fmt(px, 4);
remEl.value = v.rem;
emEl.value  = v.em;
ptEl.value  = v.pt;
pctEl.value = v.pct;
vwEl.value  = v.vw;
updatePreview(px);
updating = false;
}

function updatePreview(px) {
var clamped = Math.max(MIN_PREVIEW_PX, Math.min(MAX_PREVIEW_PX, px || 16));
previewEl.style.fontSize = clamped + 'px';
metaEl.textContent = 'Rendering at ' + fmt(px, 2) + 'px' + (px !== clamped ? ' (clamped to ' + clamped + 'px for display)' : '');
}

function parseInput(el) {
var v = parseFloat(el.value);
return isNaN(v) ? null : v;
}

// Each input triggers conversion
pxEl.addEventListener('input', function() {
var v = parseInput(pxEl);
if (v !== null && v >= 0) updateFromPx(v);
});

remEl.addEventListener('input', function() {
var v = parseInput(remEl);
if (v !== null && v >= 0) updateFromPx(v * getBase());
});

emEl.addEventListener('input', function() {
var v = parseInput(emEl);
if (v !== null && v >= 0) updateFromPx(v * getBase());
});

ptEl.addEventListener('input', function() {
var v = parseInput(ptEl);
if (v !== null && v >= 0) updateFromPx(v / 0.75);
});

pctEl.addEventListener('input', function() {
var v = parseInput(pctEl);
if (v !== null && v >= 0) updateFromPx((v / 100) * getBase());
});

vwEl.addEventListener('input', function() {
var v = parseInput(vwEl);
if (v !== null && v >= 0) updateFromPx((v / 100) * VIEWPORT_W);
});

baseEl.addEventListener('input', function() {
var px = parseInput(pxEl);
if (px !== null && px >= 0) {
updateFromPx(px);
}
renderTable();
tableNote.textContent = 'Calculated with base = ' + fmt(getBase(), 2) + 'px. Change base above to update.';
});

// Copy buttons
document.querySelectorAll('#fs-app .fs-copy-btn[data-copy]').forEach(function(btn) {
btn.addEventListener('click', function() {
var inputId = btn.getAttribute('data-copy');
var input = document.getElementById(inputId);
if (!input) return;
var val = input.value;
if (!val) return;
var suffix = { 'fs-px': 'px', 'fs-rem': 'rem', 'fs-em': 'em', 'fs-pt': 'pt', 'fs-pct': '%', 'fs-vw': 'vw' }[inputId] || '';
var text = val + suffix;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() {
flashCopy(btn);
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
flashCopy(btn);
}
});
});

function flashCopy(btn) {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 1800);
}

// Render conversion table
function renderTable() {
var base = getBase();
var html = '';
TABLE_SIZES.forEach(function(px) {
var v = pxToAll(px, base);
html += '<tr>' +
'<td>' + px + 'px</td>' +
'<td>' + v.rem + 'rem</td>' +
'<td>' + v.em + 'em</td>' +
'<td>' + v.pt + 'pt</td>' +
'<td>' + v.pct + '%</td>' +
'<td>' + v.vw + 'vw</td>' +
'</tr>';
});
tbodyEl.innerHTML = html;
}

// Init with 16px
updateFromPx(16);
renderTable();

})();
</script>

</div><!-- /#fs-app -->
