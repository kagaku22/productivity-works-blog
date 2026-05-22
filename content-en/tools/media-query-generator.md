---
title: "CSS Media Query Generator — Responsive Builder"
date: 2025-05-16
description: "Generate CSS media queries visually. Device presets, breakpoint builder, and live viewport matching. Mobile-first and desktop-first approaches. Copy @media code instantly."
categories: ["Free Tools"]
tags: ["Utility", "Free Tools"]
slug: "media-query-generator"
ShowToc: false
cover:
  image: "/images/covers/media-query-generator.png"
  alt: "CSS Media Query Generator"
---

Build CSS media queries visually — pick device presets, set breakpoints, toggle orientation and accessibility features, then copy the generated `@media` code straight into your stylesheet.

<div id="mq-app">
<style>
#mq-app *,
#mq-app *::before,
#mq-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#mq-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f4f6fb;
border-radius: 12px;
padding: 24px;
max-width: 900px;
margin: 0 auto;
}

#mq-app h2.mq-section-title {
font-size: 13px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .08em;
color: #6b7280;
margin-bottom: 10px;
}

#mq-app .mq-card {
background: #fff;
border-radius: 10px;
padding: 20px;
margin-bottom: 16px;
border: 1px solid #e5e7eb;
box-shadow: 0 1px 3px rgba(0,0,0,.06);
}

/* --- Approach toggle --- */
#mq-app .mq-approach-row {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 4px;
}
#mq-app .mq-approach-btn {
flex: 1 1 140px;
padding: 10px 14px;
border: 2px solid #e5e7eb;
border-radius: 8px;
background: #fff;
cursor: pointer;
font-size: 14px;
font-weight: 600;
color: #374151;
transition: border-color .15s, background .15s, color .15s;
text-align: center;
}
#mq-app .mq-approach-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}

/* --- Device presets --- */
#mq-app .mq-presets-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
gap: 8px;
}
#mq-app .mq-preset-btn {
padding: 9px 6px;
border: 2px solid #e5e7eb;
border-radius: 8px;
background: #fff;
cursor: pointer;
font-size: 12px;
font-weight: 600;
color: #374151;
display: flex;
flex-direction: column;
align-items: center;
gap: 4px;
transition: border-color .15s, background .15s;
}
#mq-app .mq-preset-btn .mq-preset-icon { font-size: 20px; }
#mq-app .mq-preset-btn .mq-preset-range { font-size: 10px; color: #9ca3af; font-weight: 500; }
#mq-app .mq-preset-btn:hover,
#mq-app .mq-preset-btn.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}
#mq-app .mq-preset-btn.active .mq-preset-range { color: #818cf8; }

/* --- Inputs --- */
#mq-app .mq-fields-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
gap: 14px;
}
#mq-app .mq-field label {
display: block;
font-size: 12px;
font-weight: 600;
color: #6b7280;
margin-bottom: 5px;
text-transform: uppercase;
letter-spacing: .05em;
}
#mq-app .mq-field input[type="number"],
#mq-app .mq-field select {
width: 100%;
padding: 9px 11px;
border: 1.5px solid #d1d5db;
border-radius: 7px;
font-size: 14px;
color: #111827;
background: #fff;
appearance: auto;
transition: border-color .15s;
}
#mq-app .mq-field input[type="number"]:focus,
#mq-app .mq-field select:focus {
outline: none;
border-color: #6366f1;
box-shadow: 0 0 0 3px rgba(99,102,241,.12);
}
#mq-app .mq-field .mq-unit {
font-size: 12px;
color: #9ca3af;
margin-top: 3px;
}

/* --- Feature toggles --- */
#mq-app .mq-feature-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
}
#mq-app .mq-feature-chip {
display: flex;
align-items: center;
gap: 7px;
padding: 7px 13px;
border: 1.5px solid #e5e7eb;
border-radius: 20px;
cursor: pointer;
font-size: 13px;
font-weight: 500;
color: #374151;
background: #fff;
transition: border-color .15s, background .15s, color .15s;
user-select: none;
}
#mq-app .mq-feature-chip.active {
border-color: #6366f1;
background: #eef2ff;
color: #4338ca;
}
#mq-app .mq-feature-chip input[type="checkbox"] { display: none; }
#mq-app .mq-feature-dot {
width: 8px; height: 8px;
border-radius: 50%;
background: #d1d5db;
flex-shrink: 0;
transition: background .15s;
}
#mq-app .mq-feature-chip.active .mq-feature-dot { background: #6366f1; }

/* --- Sub-select inside chip --- */
#mq-app .mq-chip-select {
border: none;
background: transparent;
font-size: 13px;
font-weight: 500;
color: #4338ca;
cursor: pointer;
padding: 0;
margin-left: 2px;
}
#mq-app .mq-chip-select:focus { outline: none; }

/* --- Live viewport badge --- */
#mq-app .mq-viewport-bar {
display: flex;
align-items: center;
gap: 12px;
flex-wrap: wrap;
}
#mq-app .mq-vp-badge {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 6px 13px;
border-radius: 20px;
font-size: 13px;
font-weight: 600;
background: #f3f4f6;
color: #6b7280;
}
#mq-app .mq-vp-badge.match {
background: #d1fae5;
color: #065f46;
}
#mq-app .mq-vp-size {
font-size: 13px;
color: #6b7280;
}
#mq-app .mq-vp-dot { width: 8px; height: 8px; border-radius: 50%; background: currentColor; }

/* --- Output --- */
#mq-app .mq-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 10px;
flex-wrap: wrap;
gap: 8px;
}
#mq-app .mq-copy-btn {
padding: 7px 16px;
background: #6366f1;
color: #fff;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background .15s;
}
#mq-app .mq-copy-btn:hover { background: #4f46e5; }
#mq-app .mq-copy-btn.copied { background: #059669; }

#mq-app pre.mq-code {
background: #0f172a;
color: #e2e8f0;
border-radius: 8px;
padding: 18px 20px;
overflow-x: auto;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.65;
white-space: pre;
min-height: 60px;
}
#mq-app .mq-kw { color: #a78bfa; }
#mq-app .mq-feat { color: #38bdf8; }
#mq-app .mq-val { color: #34d399; }
#mq-app .mq-prop { color: #fbbf24; }
#mq-app .mq-cmt { color: #64748b; }

/* --- Generate button --- */
#mq-app .mq-generate-btn {
width: 100%;
padding: 13px;
background: #6366f1;
color: #fff;
border: none;
border-radius: 9px;
font-size: 16px;
font-weight: 700;
cursor: pointer;
margin-bottom: 20px;
transition: background .15s, transform .1s;
}
#mq-app .mq-generate-btn:hover { background: #4f46e5; transform: translateY(-1px); }
#mq-app .mq-generate-btn:active { transform: translateY(0); }

/* --- Quick reference table --- */
#mq-app .mq-table-wrap { overflow-x: auto; }
#mq-app table.mq-ref-table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
}
#mq-app table.mq-ref-table th {
background: #f8fafc;
padding: 9px 12px;
text-align: left;
font-weight: 700;
color: #374151;
border-bottom: 2px solid #e5e7eb;
white-space: nowrap;
}
#mq-app table.mq-ref-table td {
padding: 8px 12px;
border-bottom: 1px solid #f3f4f6;
color: #374151;
vertical-align: top;
}
#mq-app table.mq-ref-table tr:last-child td { border-bottom: none; }
#mq-app table.mq-ref-table code {
background: #f1f5f9;
border-radius: 4px;
padding: 1px 5px;
font-size: 12px;
color: #7c3aed;
font-family: monospace;
}
#mq-app .mq-fw { font-weight: 600; }
#mq-app .mq-tag {
display: inline-block;
padding: 1px 7px;
border-radius: 10px;
font-size: 11px;
font-weight: 600;
background: #e0e7ff;
color: #3730a3;
margin-right: 3px;
}
#mq-app .mq-tag.tw { background: #ccfbf1; color: #0f766e; }
#mq-app .mq-tag.bs { background: #fef3c7; color: #92400e; }
#mq-app .mq-tag.cu { background: #fce7f3; color: #9d174d; }

/* --- Cross links --- */
#mq-app .mq-links {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-top: 4px;
}
#mq-app .mq-link {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 8px 14px;
background: #fff;
border: 1.5px solid #e5e7eb;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
color: #4338ca;
text-decoration: none;
transition: border-color .15s, background .15s;
}
#mq-app .mq-link:hover { border-color: #6366f1; background: #eef2ff; }

/* --- Responsive --- */
@media (max-width: 600px) {
#mq-app { padding: 14px; }
#mq-app .mq-fields-grid { grid-template-columns: 1fr 1fr; }
}
</style>

<!-- ===== APPROACH ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Approach</h2>
<div class="mq-approach-row">
<button class="mq-approach-btn active" data-approach="mobile-first" onclick="mqSetApproach('mobile-first',this)">
Mobile-First<br><small style="font-weight:400;font-size:11px;">min-width queries</small>
</button>
<button class="mq-approach-btn" data-approach="desktop-first" onclick="mqSetApproach('desktop-first',this)">
Desktop-First<br><small style="font-weight:400;font-size:11px;">max-width queries</small>
</button>
</div>
</div>

<!-- ===== DEVICE PRESETS ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Device Presets</h2>
<div class="mq-presets-grid" id="mqPresetsGrid">
<button class="mq-preset-btn" data-min="320" data-max="480" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📱</span>
iPhone SE
<span class="mq-preset-range">320–480px</span>
</button>
<button class="mq-preset-btn" data-min="375" data-max="812" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📱</span>
iPhone 12/13
<span class="mq-preset-range">375–812px</span>
</button>
<button class="mq-preset-btn" data-min="390" data-max="844" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📱</span>
iPhone 14 Pro
<span class="mq-preset-range">390–844px</span>
</button>
<button class="mq-preset-btn" data-min="768" data-max="1024" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📟</span>
iPad
<span class="mq-preset-range">768–1024px</span>
</button>
<button class="mq-preset-btn" data-min="1024" data-max="1366" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">📟</span>
iPad Pro
<span class="mq-preset-range">1024–1366px</span>
</button>
<button class="mq-preset-btn" data-min="1280" data-max="1920" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">🖥️</span>
Desktop HD
<span class="mq-preset-range">1280–1920px</span>
</button>
<button class="mq-preset-btn" data-min="1920" data-max="2560" onclick="mqApplyPreset(this)">
<span class="mq-preset-icon">🖥️</span>
4K / QHD
<span class="mq-preset-range">1920–2560px</span>
</button>
<button class="mq-preset-btn" data-min="" data-max="" onclick="mqClearPreset(this)">
<span class="mq-preset-icon">✏️</span>
Custom
<span class="mq-preset-range">enter values</span>
</button>
</div>
</div>

<!-- ===== DIMENSIONS ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Width &amp; Height</h2>
<div class="mq-fields-grid">
<div class="mq-field">
<label>Min Width</label>
<input type="number" id="mqMinW" min="0" max="9999" placeholder="e.g. 768">
<div class="mq-unit">px</div>
</div>
<div class="mq-field">
<label>Max Width</label>
<input type="number" id="mqMaxW" min="0" max="9999" placeholder="e.g. 1280">
<div class="mq-unit">px</div>
</div>
<div class="mq-field">
<label>Min Height</label>
<input type="number" id="mqMinH" min="0" max="9999" placeholder="optional">
<div class="mq-unit">px</div>
</div>
<div class="mq-field">
<label>Max Height</label>
<input type="number" id="mqMaxH" min="0" max="9999" placeholder="optional">
<div class="mq-unit">px</div>
</div>
</div>
</div>

<!-- ===== FEATURES ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Media Features</h2>
<div class="mq-feature-row" id="mqFeatureRow">

<label class="mq-feature-chip" id="mqChipScreen" onclick="mqToggleChip('mqChipScreen','mqFeatScreen')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatScreen">
screen
</label>

<label class="mq-feature-chip" id="mqChipPrint" onclick="mqToggleChip('mqChipPrint','mqFeatPrint')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatPrint">
print
</label>

<label class="mq-feature-chip" id="mqChipOrient" onclick="mqToggleChip('mqChipOrient','mqFeatOrient')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatOrient">
orientation:
<select class="mq-chip-select" id="mqOrientVal" onclick="event.stopPropagation()">
<option value="portrait">portrait</option>
<option value="landscape">landscape</option>
</select>
</label>

<label class="mq-feature-chip" id="mqChipColor" onclick="mqToggleChip('mqChipColor','mqFeatColor')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatColor">
prefers-color-scheme:
<select class="mq-chip-select" id="mqColorVal" onclick="event.stopPropagation()">
<option value="dark">dark</option>
<option value="light">light</option>
</select>
</label>

<label class="mq-feature-chip" id="mqChipMotion" onclick="mqToggleChip('mqChipMotion','mqFeatMotion')">
<span class="mq-feature-dot"></span>
<input type="checkbox" id="mqFeatMotion">
prefers-reduced-motion:
<select class="mq-chip-select" id="mqMotionVal" onclick="event.stopPropagation()">
<option value="reduce">reduce</option>
<option value="no-preference">no-preference</option>
</select>
</label>

</div>
</div>

<!-- ===== GENERATE ===== -->
<button class="mq-generate-btn" onclick="mqGenerate()">Generate @media Query</button>

<!-- ===== LIVE VIEWPORT ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Live Viewport Match</h2>
<div class="mq-viewport-bar">
<span class="mq-vp-size" id="mqVpSize">Viewport: — × —</span>
<span class="mq-vp-badge" id="mqVpBadge">
<span class="mq-vp-dot"></span>
<span id="mqVpText">No query generated yet</span>
</span>
</div>
</div>

<!-- ===== OUTPUT ===== -->
<div class="mq-card">
<div class="mq-output-header">
<h2 class="mq-section-title" style="margin-bottom:0">Generated CSS</h2>
<button class="mq-copy-btn" id="mqCopyBtn" onclick="mqCopy()">Copy CSS</button>
</div>
<pre class="mq-code" id="mqOutput"><span class="mq-cmt">/* Your @media query will appear here */</span></pre>
</div>

<!-- ===== QUICK REFERENCE ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Quick Reference — Common Breakpoints</h2>
<div class="mq-table-wrap">
<table class="mq-ref-table">
<thead>
<tr>
<th>Name</th>
<th>Framework</th>
<th>Breakpoint</th>
<th>Typical Device</th>
</tr>
</thead>
<tbody>
<tr>
<td class="mq-fw">xs</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>&lt; 576px</code></td>
<td>Small phones</td>
</tr>
<tr>
<td class="mq-fw">sm</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 576px</code></td>
<td>Phones landscape</td>
</tr>
<tr>
<td class="mq-fw">md</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 768px</code></td>
<td>Tablets portrait</td>
</tr>
<tr>
<td class="mq-fw">lg</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 992px</code></td>
<td>Tablets landscape / small laptop</td>
</tr>
<tr>
<td class="mq-fw">xl</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 1200px</code></td>
<td>Desktop HD</td>
</tr>
<tr>
<td class="mq-fw">xxl</td>
<td><span class="mq-tag bs">Bootstrap</span></td>
<td><code>≥ 1400px</code></td>
<td>Wide desktop</td>
</tr>
<tr>
<td class="mq-fw">sm</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 640px</code></td>
<td>Phones landscape</td>
</tr>
<tr>
<td class="mq-fw">md</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 768px</code></td>
<td>Tablets</td>
</tr>
<tr>
<td class="mq-fw">lg</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 1024px</code></td>
<td>Laptop / large tablet</td>
</tr>
<tr>
<td class="mq-fw">xl</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 1280px</code></td>
<td>Desktop</td>
</tr>
<tr>
<td class="mq-fw">2xl</td>
<td><span class="mq-tag tw">Tailwind</span></td>
<td><code>≥ 1536px</code></td>
<td>Wide / 4K</td>
</tr>
<tr>
<td class="mq-fw">mobile</td>
<td><span class="mq-tag cu">Custom</span></td>
<td><code>&lt; 768px</code></td>
<td>Phones (portrait + landscape)</td>
</tr>
<tr>
<td class="mq-fw">tablet</td>
<td><span class="mq-tag cu">Custom</span></td>
<td><code>768px–1199px</code></td>
<td>Tablets all orientations</td>
</tr>
<tr>
<td class="mq-fw">desktop</td>
<td><span class="mq-tag cu">Custom</span></td>
<td><code>≥ 1200px</code></td>
<td>Laptop / desktop monitor</td>
</tr>
<tr>
<td class="mq-fw">4k</td>
<td><span class="mq-tag cu">Custom</span></td>
<td><code>≥ 2560px</code></td>
<td>Ultra-wide / 4K displays</td>
</tr>
</tbody>
</table>
</div>
</div>

<!-- ===== CROSS LINKS ===== -->
<div class="mq-card">
<h2 class="mq-section-title">Related Tools</h2>
<div class="mq-links">
<a href="/tools/flexbox-generator/" class="mq-link">&#9633; CSS Flexbox Generator</a>
<a href="/tools/css-grid-generator/" class="mq-link">&#9635; CSS Grid Generator</a>
<a href="/tools/screen-resolution/" class="mq-link">&#128250; Screen Resolution Checker</a>
</div>
</div>

<script>
(function() {
'use strict';

/* ---- State ---- */
var mqApproach = 'mobile-first';
var mqLastQuery = '';
var mqCurrentMediaFn = null;

/* ---- Approach ---- */
window.mqSetApproach = function(val, btn) {
mqApproach = val;
document.querySelectorAll('#mq-app .mq-approach-btn').forEach(function(b) {
b.classList.toggle('active', b === btn);
});
};

/* ---- Presets ---- */
window.mqApplyPreset = function(btn) {
document.querySelectorAll('#mq-app .mq-preset-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
var minVal = btn.getAttribute('data-min');
var maxVal = btn.getAttribute('data-max');
document.getElementById('mqMinW').value = minVal;
document.getElementById('mqMaxW').value = maxVal;
document.getElementById('mqMinH').value = '';
document.getElementById('mqMaxH').value = '';
};

window.mqClearPreset = function(btn) {
document.querySelectorAll('#mq-app .mq-preset-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
['mqMinW','mqMaxW','mqMinH','mqMaxH'].forEach(function(id) {
document.getElementById(id).value = '';
});
};

/* ---- Feature chips ---- */
window.mqToggleChip = function(chipId, cbId) {
var chip = document.getElementById(chipId);
var cb   = document.getElementById(cbId);
cb.checked = !cb.checked;
chip.classList.toggle('active', cb.checked);
};

/* ---- Syntax highlight helper ---- */
function hl(str) {
return str
.replace(/(@media)/g, '<span class="mq-kw">$1</span>')
.replace(/\b(screen|print|all)\b/g, '<span class="mq-feat">$1</span>')
.replace(/\b(min-width|max-width|min-height|max-height|orientation|prefers-color-scheme|prefers-reduced-motion)\b/g, '<span class="mq-feat">$1</span>')
.replace(/\b(\d+px|portrait|landscape|dark|light|reduce|no-preference)\b/g, '<span class="mq-val">$1</span>')
.replace(/\b(\/\*.*?\*\/)/g, '<span class="mq-cmt">$1</span>');
}

/* ---- Build conditions array ---- */
function buildConditions() {
var conds = [];
var minW = document.getElementById('mqMinW').value.trim();
var maxW = document.getElementById('mqMaxW').value.trim();
var minH = document.getElementById('mqMinH').value.trim();
var maxH = document.getElementById('mqMaxH').value.trim();

/* In mobile-first mode prefer min-width; desktop-first prefer max-width */
if (mqApproach === 'mobile-first') {
if (minW) conds.push('(min-width: ' + minW + 'px)');
if (maxW) conds.push('(max-width: ' + maxW + 'px)');
} else {
if (maxW) conds.push('(max-width: ' + maxW + 'px)');
if (minW) conds.push('(min-width: ' + minW + 'px)');
}
if (minH) conds.push('(min-height: ' + minH + 'px)');
if (maxH) conds.push('(max-height: ' + maxH + 'px)');

if (document.getElementById('mqFeatOrient').checked) {
conds.push('(orientation: ' + document.getElementById('mqOrientVal').value + ')');
}
if (document.getElementById('mqFeatColor').checked) {
conds.push('(prefers-color-scheme: ' + document.getElementById('mqColorVal').value + ')');
}
if (document.getElementById('mqFeatMotion').checked) {
conds.push('(prefers-reduced-motion: ' + document.getElementById('mqMotionVal').value + ')');
}
return conds;
}

function buildMediaType() {
var parts = [];
if (document.getElementById('mqFeatScreen').checked) parts.push('screen');
if (document.getElementById('mqFeatPrint').checked)  parts.push('print');
return parts.join(', ') || 'screen';
}

/* ---- Generate ---- */
window.mqGenerate = function() {
var conds     = buildConditions();
var mediaType = buildMediaType();
var query;

if (conds.length === 0) {
query = '@media ' + mediaType + ' {\n  /* Your styles here */\n}';
} else if (conds.length === 1) {
query = '@media ' + mediaType + ' and ' + conds[0] + ' {\n  /* Your styles here */\n}';
} else {
query = '@media ' + mediaType + '\n  and ' + conds.join('\n  and ') + ' {\n  /* Your styles here */\n}';
}

mqLastQuery = query;
document.getElementById('mqOutput').innerHTML = hl(query);

/* Build a matchMedia-compatible string (strip the outer @media … { }) */
var mmStr = (conds.length === 0)
? mediaType
: mediaType + ' and ' + conds.join(' and ');

/* Live match */
try {
mqCurrentMediaFn = window.matchMedia(mmStr);
mqUpdateBadge(mqCurrentMediaFn.matches);
if (mqCurrentMediaFn.addEventListener) {
mqCurrentMediaFn.addEventListener('change', function(e) { mqUpdateBadge(e.matches); });
}
} catch(e) {
mqUpdateBadge(null);
}
};

/* ---- Viewport badge ---- */
function mqUpdateBadge(matches) {
var badge = document.getElementById('mqVpBadge');
var text  = document.getElementById('mqVpText');
if (matches === null) {
badge.className = 'mq-vp-badge';
text.textContent = 'Could not evaluate query';
} else if (matches) {
badge.className = 'mq-vp-badge match';
text.textContent = 'Query MATCHES current viewport';
} else {
badge.className = 'mq-vp-badge';
text.textContent = 'Query does NOT match current viewport';
}
}

/* Viewport size display */
function mqShowVp() {
document.getElementById('mqVpSize').textContent =
'Viewport: ' + window.innerWidth + 'px × ' + window.innerHeight + 'px';
}
mqShowVp();
window.addEventListener('resize', function() {
mqShowVp();
if (mqCurrentMediaFn) mqUpdateBadge(mqCurrentMediaFn.matches);
});

/* ---- Copy ---- */
window.mqCopy = function() {
if (!mqLastQuery) return;
var btn = document.getElementById('mqCopyBtn');
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(mqLastQuery).then(function() { mqFlash(btn); });
} else {
var ta = document.createElement('textarea');
ta.value = mqLastQuery;
ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
mqFlash(btn);
}
};

function mqFlash(btn) {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy CSS';
btn.classList.remove('copied');
}, 2000);
}
})();
</script>
</div>

---

## How to Use the Generator

1. **Choose your approach** — Mobile-first outputs `min-width` queries that scale up; desktop-first uses `max-width` to scale down.
2. **Pick a device preset** or enter custom min/max width and height values.
3. **Toggle media features** — add orientation, `prefers-color-scheme`, `prefers-reduced-motion`, or print.
4. Click **Generate @media Query** to see the code and the live viewport match status.
5. Click **Copy CSS** and paste into your stylesheet.

---

## When to Use Mobile-First vs. Desktop-First

| | Mobile-First | Desktop-First |
|---|---|---|
| Base styles target | Smallest screens | Largest screens |
| Query type | `min-width` | `max-width` |
| Progressive enhancement | Yes | No |
| Framework alignment | Tailwind, Bootstrap 4+ | Older frameworks |

**Best practice:** mobile-first is the modern default. It reduces specificity conflicts and keeps base styles lean.

---

## How `prefers-color-scheme` Works

```css
/* Apply dark styles only when the OS is in dark mode */
@media screen and (prefers-color-scheme: dark) {
body {
background: #0f172a;
color: #e2e8f0;
}
}
```

Pair this with a CSS custom-property theme to avoid duplicating declarations.

---

## `prefers-reduced-motion` — Accessibility

Users who have vestibular disorders or motion sensitivity can request reduced animations at the OS level. Always respect it:

```css
@media (prefers-reduced-motion: reduce) {
*, *::before, *::after {
animation-duration: 0.01ms !important;
transition-duration: 0.01ms !important;
}
}
```

---

## Related Free Tools

- [CSS Flexbox Generator](/tools/flexbox-generator/) — build flex containers visually
- [CSS Grid Generator](/tools/css-grid-generator/) — define grid tracks and areas with a point-and-click interface
- [Screen Resolution Checker](/tools/screen-resolution/) — see your exact screen and device pixel ratio
