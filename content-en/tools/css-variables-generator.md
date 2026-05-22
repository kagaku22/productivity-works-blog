---
title: "CSS Variables Generator — Design Token Builder"
date: 2025-05-16
description: "Generate CSS custom properties for design systems. Build color palettes, typography scales, spacing, and more. Preview live and copy :root variables."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "css-variables-generator"
ShowToc: false
cover:
  image: "/images/covers/css-variables-generator.png"
  alt: "CSS Variables Generator"
---

<div id="cssvar-app">

<style>
#cssvar-app *,
#cssvar-app *::before,
#cssvar-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#cssvar-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
line-height: 1.5;
background: #f4f6fb;
border-radius: 12px;
padding: 0 0 32px 0;
overflow: hidden;
}

/* ── Header ── */
#cssvar-app .cv-header {
background: linear-gradient(135deg, #2563eb 0%, #7c3aed 100%);
color: #fff;
padding: 28px 32px 24px;
margin-bottom: 0;
}
#cssvar-app .cv-header h1 {
font-size: 1.55rem;
font-weight: 700;
letter-spacing: -0.5px;
margin-bottom: 4px;
}
#cssvar-app .cv-header p {
font-size: 0.92rem;
opacity: 0.85;
}

/* ── Preset bar ── */
#cssvar-app .cv-preset-bar {
background: #fff;
border-bottom: 1px solid #e2e8f0;
padding: 12px 32px;
display: flex;
align-items: center;
gap: 10px;
flex-wrap: wrap;
}
#cssvar-app .cv-preset-label {
font-size: 0.8rem;
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-right: 4px;
white-space: nowrap;
}
#cssvar-app .cv-preset-btn {
padding: 6px 16px;
border-radius: 20px;
border: 1.5px solid #cbd5e1;
background: #f8fafc;
color: #334155;
font-size: 0.82rem;
font-weight: 500;
cursor: pointer;
transition: all 0.15s;
white-space: nowrap;
}
#cssvar-app .cv-preset-btn:hover {
border-color: #2563eb;
color: #2563eb;
background: #eff6ff;
}
#cssvar-app .cv-preset-btn.active {
background: #2563eb;
border-color: #2563eb;
color: #fff;
}

/* ── Main layout ── */
#cssvar-app .cv-main {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 0;
}
@media (max-width: 820px) {
#cssvar-app .cv-main {
grid-template-columns: 1fr;
}
}

/* ── Panel ── */
#cssvar-app .cv-panel {
padding: 24px 28px;
border-right: 1px solid #e2e8f0;
overflow-y: auto;
}
@media (max-width: 820px) {
#cssvar-app .cv-panel {
border-right: none;
border-bottom: 1px solid #e2e8f0;
}
}

/* ── Section ── */
#cssvar-app .cv-section {
margin-bottom: 28px;
}
#cssvar-app .cv-section-title {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #94a3b8;
margin-bottom: 14px;
padding-bottom: 8px;
border-bottom: 1px solid #e2e8f0;
display: flex;
align-items: center;
gap: 6px;
}
#cssvar-app .cv-section-icon {
width: 18px;
height: 18px;
border-radius: 4px;
display: inline-flex;
align-items: center;
justify-content: center;
font-size: 11px;
}

/* ── Row / field ── */
#cssvar-app .cv-row {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 10px;
}
#cssvar-app .cv-row-label {
font-size: 0.8rem;
color: #475569;
width: 140px;
flex-shrink: 0;
font-weight: 500;
}
@media (max-width: 500px) {
#cssvar-app .cv-row {
flex-wrap: wrap;
}
#cssvar-app .cv-row-label {
width: 100%;
margin-bottom: 2px;
}
}

/* Color input */
#cssvar-app .cv-color-wrap {
display: flex;
align-items: center;
gap: 8px;
flex: 1;
}
#cssvar-app .cv-color-swatch {
width: 34px;
height: 34px;
border-radius: 8px;
border: 2px solid #e2e8f0;
cursor: pointer;
padding: 0;
background: transparent;
overflow: hidden;
flex-shrink: 0;
}
#cssvar-app .cv-color-swatch input[type="color"] {
width: 44px;
height: 44px;
border: none;
padding: 0;
cursor: pointer;
transform: translate(-5px, -5px);
}
#cssvar-app .cv-hex-input {
flex: 1;
min-width: 80px;
padding: 6px 10px;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
font-size: 0.82rem;
font-family: "Fira Mono", "Consolas", monospace;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
max-width: 110px;
}
#cssvar-app .cv-hex-input:focus {
outline: none;
border-color: #2563eb;
}

/* Text / select input */
#cssvar-app .cv-text-input,
#cssvar-app .cv-select-input {
flex: 1;
padding: 6px 10px;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
font-size: 0.82rem;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
}
#cssvar-app .cv-text-input:focus,
#cssvar-app .cv-select-input:focus {
outline: none;
border-color: #2563eb;
}

/* ── Preview panel ── */
#cssvar-app .cv-preview-panel {
padding: 24px 28px;
background: #f8fafc;
}
#cssvar-app .cv-preview-title {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #94a3b8;
margin-bottom: 16px;
padding-bottom: 8px;
border-bottom: 1px solid #e2e8f0;
}

/* Preview card */
#cssvar-app .cv-preview-area {
border-radius: 10px;
overflow: hidden;
border: 1.5px solid #e2e8f0;
margin-bottom: 16px;
}
#cssvar-app .cv-preview-inner {
padding: 24px;
transition: background 0.3s;
}

/* Output area */
#cssvar-app .cv-output-section {
margin-top: 0;
}
#cssvar-app .cv-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 8px;
}
#cssvar-app .cv-output-label {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #94a3b8;
}
#cssvar-app .cv-copy-btn {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 7px 16px;
background: #2563eb;
color: #fff;
border: none;
border-radius: 7px;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
#cssvar-app .cv-copy-btn:hover {
background: #1d4ed8;
}
#cssvar-app .cv-copy-btn:active {
transform: scale(0.97);
}
#cssvar-app .cv-copy-btn.copied {
background: #16a34a;
}
#cssvar-app .cv-code-box {
background: #0f172a;
color: #94d2bd;
font-family: "Fira Mono", "Consolas", "Monaco", monospace;
font-size: 0.76rem;
line-height: 1.7;
padding: 16px 18px;
border-radius: 9px;
overflow-x: auto;
overflow-y: auto;
max-height: 300px;
white-space: pre;
tab-size: 2;
}

/* ── Cross-links ── */
#cssvar-app .cv-links {
margin: 24px 28px 0;
padding: 18px 20px;
background: #eff6ff;
border-radius: 10px;
border: 1px solid #bfdbfe;
}
#cssvar-app .cv-links-title {
font-size: 0.8rem;
font-weight: 700;
color: #1d4ed8;
margin-bottom: 8px;
}
#cssvar-app .cv-links ul {
list-style: none;
display: flex;
flex-wrap: wrap;
gap: 8px;
}
#cssvar-app .cv-links ul li a {
display: inline-block;
padding: 5px 14px;
background: #fff;
border: 1.5px solid #93c5fd;
border-radius: 20px;
color: #1d4ed8;
font-size: 0.82rem;
font-weight: 500;
text-decoration: none;
transition: all 0.15s;
}
#cssvar-app .cv-links ul li a:hover {
background: #2563eb;
color: #fff;
border-color: #2563eb;
}
</style>

<div class="cv-header">
<h1>CSS Variables Generator</h1>
<p>Build design tokens as CSS custom properties — color, typography, spacing, radius, shadows.</p>
</div>

<div class="cv-preset-bar">
<span class="cv-preset-label">Presets:</span>
<button class="cv-preset-btn active" data-preset="light-modern">Light Modern</button>
<button class="cv-preset-btn" data-preset="dark-mode">Dark Mode</button>
<button class="cv-preset-btn" data-preset="ocean">Ocean</button>
<button class="cv-preset-btn" data-preset="forest">Forest</button>
<button class="cv-preset-btn" data-preset="warm">Warm</button>
</div>

<div class="cv-main">
<!-- Left: Controls -->
<div class="cv-panel">

<!-- Colors -->
<div class="cv-section" id="cv-section-colors">
<div class="cv-section-title">
<span class="cv-section-icon" style="background:#ede9fe;">&#127912;</span>
Colors
</div>

<div class="cv-row">
<span class="cv-row-label">Primary</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-primary" value="#2563eb"></div>
<input type="text" class="cv-hex-input" id="h-primary" value="#2563eb" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Secondary</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-secondary" value="#7c3aed"></div>
<input type="text" class="cv-hex-input" id="h-secondary" value="#7c3aed" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Accent</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-accent" value="#f59e0b"></div>
<input type="text" class="cv-hex-input" id="h-accent" value="#f59e0b" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Background</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-bg" value="#ffffff"></div>
<input type="text" class="cv-hex-input" id="h-bg" value="#ffffff" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Surface</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-surface" value="#f8fafc"></div>
<input type="text" class="cv-hex-input" id="h-surface" value="#f8fafc" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Text</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-text" value="#1e293b"></div>
<input type="text" class="cv-hex-input" id="h-text" value="#1e293b" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Text Muted</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-text-muted" value="#64748b"></div>
<input type="text" class="cv-hex-input" id="h-text-muted" value="#64748b" maxlength="7">
</div>
</div>
<div class="cv-row">
<span class="cv-row-label">Border</span>
<div class="cv-color-wrap">
<div class="cv-color-swatch"><input type="color" id="c-border" value="#e2e8f0"></div>
<input type="text" class="cv-hex-input" id="h-border" value="#e2e8f0" maxlength="7">
</div>
</div>
</div>

<!-- Typography -->
<div class="cv-section" id="cv-section-typography">
<div class="cv-section-title">
<span class="cv-section-icon" style="background:#fef9c3;">T</span>
Typography
</div>

<div class="cv-row">
<span class="cv-row-label">Font Family</span>
<select class="cv-select-input" id="t-font-family">
<option value="-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif">System UI</option>
<option value="'Inter', sans-serif">Inter</option>
<option value="'Roboto', sans-serif">Roboto</option>
<option value="'Poppins', sans-serif">Poppins</option>
<option value="'Playfair Display', serif">Playfair Display</option>
<option value="Georgia, 'Times New Roman', serif">Georgia Serif</option>
<option value="'Fira Code', 'Consolas', monospace">Fira Code Mono</option>
</select>
</div>
<div class="cv-row">
<span class="cv-row-label">Base Size</span>
<input type="text" class="cv-text-input" id="t-base" value="1rem">
</div>
<div class="cv-row">
<span class="cv-row-label">Size SM</span>
<input type="text" class="cv-text-input" id="t-sm" value="0.875rem">
</div>
<div class="cv-row">
<span class="cv-row-label">Size LG</span>
<input type="text" class="cv-text-input" id="t-lg" value="1.125rem">
</div>
<div class="cv-row">
<span class="cv-row-label">Size XL</span>
<input type="text" class="cv-text-input" id="t-xl" value="1.25rem">
</div>
<div class="cv-row">
<span class="cv-row-label">Size 2XL</span>
<input type="text" class="cv-text-input" id="t-2xl" value="1.5rem">
</div>
<div class="cv-row">
<span class="cv-row-label">Weight Normal</span>
<select class="cv-select-input" id="t-weight-normal">
<option value="300">300 Light</option>
<option value="400" selected>400 Regular</option>
<option value="500">500 Medium</option>
</select>
</div>
<div class="cv-row">
<span class="cv-row-label">Weight Bold</span>
<select class="cv-select-input" id="t-weight-bold">
<option value="600">600 Semibold</option>
<option value="700" selected>700 Bold</option>
<option value="800">800 Extrabold</option>
<option value="900">900 Black</option>
</select>
</div>
<div class="cv-row">
<span class="cv-row-label">Line Height</span>
<input type="text" class="cv-text-input" id="t-leading" value="1.6">
</div>
<div class="cv-row">
<span class="cv-row-label">Leading Tight</span>
<input type="text" class="cv-text-input" id="t-leading-tight" value="1.25">
</div>
</div>

<!-- Spacing -->
<div class="cv-section" id="cv-section-spacing">
<div class="cv-section-title">
<span class="cv-section-icon" style="background:#dcfce7;">&#8596;</span>
Spacing
</div>

<div class="cv-row">
<span class="cv-row-label">XS</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-xs" value="4px">
</div>
<div class="cv-row">
<span class="cv-row-label">SM</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-sm" value="8px">
</div>
<div class="cv-row">
<span class="cv-row-label">MD</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-md" value="16px">
</div>
<div class="cv-row">
<span class="cv-row-label">LG</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-lg" value="24px">
</div>
<div class="cv-row">
<span class="cv-row-label">XL</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-xl" value="32px">
</div>
<div class="cv-row">
<span class="cv-row-label">2XL</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-2xl" value="48px">
</div>
<div class="cv-row">
<span class="cv-row-label">3XL</span>
<input type="text" class="cv-text-input cv-spacing" id="sp-3xl" value="64px">
</div>
</div>

<!-- Border Radius -->
<div class="cv-section" id="cv-section-radius">
<div class="cv-section-title">
<span class="cv-section-icon" style="background:#fce7f3;">&#11096;</span>
Border Radius
</div>

<div class="cv-row">
<span class="cv-row-label">SM</span>
<input type="text" class="cv-text-input cv-radius" id="r-sm" value="4px">
</div>
<div class="cv-row">
<span class="cv-row-label">MD</span>
<input type="text" class="cv-text-input cv-radius" id="r-md" value="8px">
</div>
<div class="cv-row">
<span class="cv-row-label">LG</span>
<input type="text" class="cv-text-input cv-radius" id="r-lg" value="12px">
</div>
<div class="cv-row">
<span class="cv-row-label">XL</span>
<input type="text" class="cv-text-input cv-radius" id="r-xl" value="16px">
</div>
<div class="cv-row">
<span class="cv-row-label">Full (pill)</span>
<input type="text" class="cv-text-input cv-radius" id="r-full" value="9999px">
</div>
</div>

<!-- Shadows -->
<div class="cv-section" id="cv-section-shadows">
<div class="cv-section-title">
<span class="cv-section-icon" style="background:#e0f2fe;">&#9737;</span>
Shadows
</div>

<div class="cv-row">
<span class="cv-row-label">SM</span>
<input type="text" class="cv-text-input cv-shadow" id="sh-sm" value="0 1px 3px rgba(0,0,0,0.1)">
</div>
<div class="cv-row">
<span class="cv-row-label">MD</span>
<input type="text" class="cv-text-input cv-shadow" id="sh-md" value="0 4px 12px rgba(0,0,0,0.12)">
</div>
<div class="cv-row">
<span class="cv-row-label">LG</span>
<input type="text" class="cv-text-input cv-shadow" id="sh-lg" value="0 8px 24px rgba(0,0,0,0.15)">
</div>
<div class="cv-row">
<span class="cv-row-label">XL</span>
<input type="text" class="cv-text-input cv-shadow" id="sh-xl" value="0 16px 48px rgba(0,0,0,0.2)">
</div>
</div>

</div><!-- /cv-panel -->

<!-- Right: Preview + Output -->
<div class="cv-preview-panel">

<div class="cv-preview-title">Live Preview</div>

<div class="cv-preview-area">
<div class="cv-preview-inner" id="cv-preview-inner">
<!-- Rendered by JS -->
</div>
</div>

<div class="cv-output-section">
<div class="cv-output-header">
<span class="cv-output-label">Generated CSS</span>
<button class="cv-copy-btn" id="cv-copy-btn">Copy CSS</button>
</div>
<div class="cv-code-box" id="cv-code-box"></div>
</div>

</div><!-- /cv-preview-panel -->
</div><!-- /cv-main -->

<div class="cv-links">
<div class="cv-links-title">Related Tools</div>
<ul>
<li><a href="/tools/color-palette-generator/">Color Palette Generator</a></li>
<li><a href="/tools/css-gradient-generator/">CSS Gradient Generator</a></li>
<li><a href="/tools/color-contrast-checker/">Color Contrast Checker</a></li>
</ul>
</div>

</div><!-- #cssvar-app -->

<script>
(function() {
'use strict';

/* ── Presets ── */
const PRESETS = {
'light-modern': {
colors: { primary:'#2563eb', secondary:'#7c3aed', accent:'#f59e0b', bg:'#ffffff', surface:'#f8fafc', text:'#1e293b', 'text-muted':'#64748b', border:'#e2e8f0' },
font: 'system',
radius: { sm:'4px', md:'8px', lg:'12px', xl:'16px', full:'9999px' },
shadows: { sm:'0 1px 3px rgba(0,0,0,0.1)', md:'0 4px 12px rgba(0,0,0,0.12)', lg:'0 8px 24px rgba(0,0,0,0.15)', xl:'0 16px 48px rgba(0,0,0,0.2)' },
},
'dark-mode': {
colors: { primary:'#60a5fa', secondary:'#a78bfa', accent:'#fbbf24', bg:'#0f172a', surface:'#1e293b', text:'#f1f5f9', 'text-muted':'#94a3b8', border:'#334155' },
font: 'system',
radius: { sm:'4px', md:'8px', lg:'12px', xl:'16px', full:'9999px' },
shadows: { sm:'0 1px 3px rgba(0,0,0,0.4)', md:'0 4px 12px rgba(0,0,0,0.5)', lg:'0 8px 24px rgba(0,0,0,0.6)', xl:'0 16px 48px rgba(0,0,0,0.7)' },
},
'ocean': {
colors: { primary:'#0ea5e9', secondary:'#06b6d4', accent:'#f0abfc', bg:'#f0f9ff', surface:'#e0f2fe', text:'#0c4a6e', 'text-muted':'#0369a1', border:'#bae6fd' },
font: 'system',
radius: { sm:'6px', md:'10px', lg:'16px', xl:'22px', full:'9999px' },
shadows: { sm:'0 1px 4px rgba(14,165,233,0.15)', md:'0 4px 14px rgba(14,165,233,0.2)', lg:'0 8px 28px rgba(14,165,233,0.25)', xl:'0 16px 50px rgba(14,165,233,0.3)' },
},
'forest': {
colors: { primary:'#16a34a', secondary:'#15803d', accent:'#ca8a04', bg:'#f0fdf4', surface:'#dcfce7', text:'#14532d', 'text-muted':'#166534', border:'#bbf7d0' },
font: 'system',
radius: { sm:'3px', md:'6px', lg:'10px', xl:'14px', full:'9999px' },
shadows: { sm:'0 1px 3px rgba(22,163,74,0.12)', md:'0 4px 12px rgba(22,163,74,0.18)', lg:'0 8px 24px rgba(22,163,74,0.22)', xl:'0 16px 48px rgba(22,163,74,0.28)' },
},
'warm': {
colors: { primary:'#dc2626', secondary:'#ea580c', accent:'#d97706', bg:'#fff7ed', surface:'#ffedd5', text:'#431407', 'text-muted':'#9a3412', border:'#fed7aa' },
font: 'system',
radius: { sm:'5px', md:'10px', lg:'18px', xl:'24px', full:'9999px' },
shadows: { sm:'0 1px 3px rgba(220,38,38,0.1)', md:'0 4px 12px rgba(220,38,38,0.15)', lg:'0 8px 24px rgba(220,38,38,0.2)', xl:'0 16px 48px rgba(220,38,38,0.25)' },
}
};

/* ── State ── */
let activePreset = 'light-modern';

/* ── Helpers ── */
function gid(id) { return document.getElementById(id); }

function getVal(id) {
const el = gid(id);
return el ? el.value.trim() : '';
}

function setVal(id, val) {
const el = gid(id);
if (el) el.value = val;
}

function setSwatch(id, hex) {
const el = gid(id);
if (el) {
// update background of parent swatch div too
el.value = hex;
const swatch = el.closest('.cv-color-swatch');
if (swatch) swatch.style.background = hex;
}
}

/* ── Apply preset ── */
function applyPreset(key) {
const p = PRESETS[key];
if (!p) return;
const c = p.colors;
setSwatch('c-primary',    c.primary);    setVal('h-primary',    c.primary);
setSwatch('c-secondary',  c.secondary);  setVal('h-secondary',  c.secondary);
setSwatch('c-accent',     c.accent);     setVal('h-accent',     c.accent);
setSwatch('c-bg',         c.bg);         setVal('h-bg',         c.bg);
setSwatch('c-surface',    c.surface);    setVal('h-surface',    c.surface);
setSwatch('c-text',       c.text);       setVal('h-text',       c.text);
setSwatch('c-text-muted', c['text-muted']); setVal('h-text-muted', c['text-muted']);
setSwatch('c-border',     c.border);     setVal('h-border',     c.border);

const r = p.radius;
setVal('r-sm', r.sm); setVal('r-md', r.md); setVal('r-lg', r.lg);
setVal('r-xl', r.xl); setVal('r-full', r.full);

const s = p.shadows;
setVal('sh-sm', s.sm); setVal('sh-md', s.md);
setVal('sh-lg', s.lg); setVal('sh-xl', s.xl);

updateAll();
}

/* ── Build CSS string ── */
function buildCSS() {
const lines = [':root {'];

// Colors
lines.push('  /* Colors */');
lines.push('  --color-primary:    ' + getVal('h-primary') + ';');
lines.push('  --color-secondary:  ' + getVal('h-secondary') + ';');
lines.push('  --color-accent:     ' + getVal('h-accent') + ';');
lines.push('  --color-bg:         ' + getVal('h-bg') + ';');
lines.push('  --color-surface:    ' + getVal('h-surface') + ';');
lines.push('  --color-text:       ' + getVal('h-text') + ';');
lines.push('  --color-text-muted: ' + getVal('h-text-muted') + ';');
lines.push('  --color-border:     ' + getVal('h-border') + ';');
lines.push('');

// Typography
lines.push('  /* Typography */');
const ffEl = gid('t-font-family');
lines.push('  --font-family:        ' + (ffEl ? ffEl.value : 'system-ui') + ';');
lines.push('  --font-size-base:     ' + getVal('t-base') + ';');
lines.push('  --font-size-sm:       ' + getVal('t-sm') + ';');
lines.push('  --font-size-lg:       ' + getVal('t-lg') + ';');
lines.push('  --font-size-xl:       ' + getVal('t-xl') + ';');
lines.push('  --font-size-2xl:      ' + getVal('t-2xl') + ';');
const wnEl = gid('t-weight-normal');
const wbEl = gid('t-weight-bold');
lines.push('  --font-weight-normal: ' + (wnEl ? wnEl.value : '400') + ';');
lines.push('  --font-weight-bold:   ' + (wbEl ? wbEl.value : '700') + ';');
lines.push('  --line-height:        ' + getVal('t-leading') + ';');
lines.push('  --line-height-tight:  ' + getVal('t-leading-tight') + ';');
lines.push('');

// Spacing
lines.push('  /* Spacing */');
lines.push('  --space-xs:  ' + getVal('sp-xs') + ';');
lines.push('  --space-sm:  ' + getVal('sp-sm') + ';');
lines.push('  --space-md:  ' + getVal('sp-md') + ';');
lines.push('  --space-lg:  ' + getVal('sp-lg') + ';');
lines.push('  --space-xl:  ' + getVal('sp-xl') + ';');
lines.push('  --space-2xl: ' + getVal('sp-2xl') + ';');
lines.push('  --space-3xl: ' + getVal('sp-3xl') + ';');
lines.push('');

// Radius
lines.push('  /* Border Radius */');
lines.push('  --radius-sm:   ' + getVal('r-sm') + ';');
lines.push('  --radius-md:   ' + getVal('r-md') + ';');
lines.push('  --radius-lg:   ' + getVal('r-lg') + ';');
lines.push('  --radius-xl:   ' + getVal('r-xl') + ';');
lines.push('  --radius-full: ' + getVal('r-full') + ';');
lines.push('');

// Shadows
lines.push('  /* Shadows */');
lines.push('  --shadow-sm: ' + getVal('sh-sm') + ';');
lines.push('  --shadow-md: ' + getVal('sh-md') + ';');
lines.push('  --shadow-lg: ' + getVal('sh-lg') + ';');
lines.push('  --shadow-xl: ' + getVal('sh-xl') + ';');

lines.push('}');
return lines.join('\n');
}

/* ── Build preview HTML ── */
function buildPreview() {
const bg        = getVal('h-bg');
const surface   = getVal('h-surface');
const primary   = getVal('h-primary');
const secondary = getVal('h-secondary');
const accent    = getVal('h-accent');
const text      = getVal('h-text');
const muted     = getVal('h-text-muted');
const border    = getVal('h-border');
const rmd       = getVal('r-md');
const rlg       = getVal('r-lg');
const shmd      = getVal('sh-md');
const spmd      = getVal('sp-md');
const splg      = getVal('sp-lg');
const rfull     = getVal('r-full');
const wbEl      = gid('t-weight-bold');
const wb        = wbEl ? wbEl.value : '700';
const ffEl      = gid('t-font-family');
const ff        = ffEl ? ffEl.value : 'system-ui';
const baseSz    = getVal('t-base');
const smSz      = getVal('t-sm');
const lgSz      = getVal('t-lg');
const xl2Sz     = getVal('t-2xl');

const inner = gid('cv-preview-inner');
inner.style.background = bg;

inner.innerHTML = `
<div style="font-family:${ff}; color:${text}; max-width:100%;">

<!-- Heading -->
<div style="margin-bottom:${splg};">
<h2 style="font-size:${xl2Sz}; font-weight:${wb}; color:${text}; line-height:1.25; margin-bottom:6px;">Design System Preview</h2>
<p style="font-size:${smSz}; color:${muted}; margin:0;">Your CSS variables applied in real-time.</p>
</div>

<!-- Card -->
<div style="background:${surface}; border:1.5px solid ${border}; border-radius:${rlg}; padding:${splg}; margin-bottom:${spmd}; box-shadow:${shmd};">
<div style="display:flex; align-items:center; gap:10px; margin-bottom:12px;">
<div style="width:38px; height:38px; border-radius:${rfull}; background:${primary}; flex-shrink:0;"></div>
<div>
<div style="font-size:${baseSz}; font-weight:${wb}; color:${text};">Card Component</div>
<div style="font-size:${smSz}; color:${muted};">Using surface + border tokens</div>
</div>
</div>
<p style="font-size:${smSz}; color:${muted}; margin-bottom:${spmd}; line-height:1.6;">
This card uses <code style="background:${bg}; padding:2px 6px; border-radius:${rmd}; font-size:0.78rem; color:${primary};">--color-surface</code>,
<code style="background:${bg}; padding:2px 6px; border-radius:${rmd}; font-size:0.78rem; color:${primary};">--radius-lg</code>,
and <code style="background:${bg}; padding:2px 6px; border-radius:${rmd}; font-size:0.78rem; color:${primary};">--shadow-md</code>.
</p>
<div style="display:flex; gap:8px; flex-wrap:wrap;">
<button style="padding:8px 18px; background:${primary}; color:#fff; border:none; border-radius:${rmd}; font-size:${smSz}; font-weight:${wb}; cursor:default; box-shadow:${shmd};">Primary</button>
<button style="padding:8px 18px; background:${secondary}; color:#fff; border:none; border-radius:${rmd}; font-size:${smSz}; font-weight:${wb}; cursor:default;">Secondary</button>
<button style="padding:8px 18px; background:${accent}; color:#fff; border:none; border-radius:${rmd}; font-size:${smSz}; font-weight:${wb}; cursor:default;">Accent</button>
<button style="padding:8px 18px; background:transparent; color:${primary}; border:1.5px solid ${primary}; border-radius:${rmd}; font-size:${smSz}; font-weight:${wb}; cursor:default;">Outline</button>
</div>
</div>

<!-- Typography scale -->
<div style="background:${surface}; border:1.5px solid ${border}; border-radius:${rlg}; padding:${splg}; margin-bottom:${spmd};">
<div style="font-size:${smSz}; color:${muted}; font-weight:${wb}; margin-bottom:10px; text-transform:uppercase; letter-spacing:0.06em;">Typography Scale</div>
<div style="font-size:${xl2Sz}; font-weight:${wb}; color:${text}; line-height:1.25;">2XL — ${xl2Sz}</div>
<div style="font-size:${lgSz}; font-weight:${wb}; color:${text};">LG — ${lgSz}</div>
<div style="font-size:${baseSz}; color:${text};">Base — ${baseSz}</div>
<div style="font-size:${smSz}; color:${muted};">SM — ${smSz} (muted)</div>
</div>

<!-- Spacing + radius swatches -->
<div style="display:flex; gap:${spmd}; flex-wrap:wrap;">
<div style="flex:1; min-width:140px; background:${surface}; border:1.5px solid ${border}; border-radius:${rlg}; padding:${spmd};">
<div style="font-size:${smSz}; color:${muted}; font-weight:${wb}; margin-bottom:8px; text-transform:uppercase; letter-spacing:0.06em;">Radius</div>
<div style="display:flex; gap:6px; flex-wrap:wrap; align-items:flex-end;">
<div style="width:28px; height:28px; background:${primary}; border-radius:${getVal('r-sm')};"></div>
<div style="width:28px; height:28px; background:${secondary}; border-radius:${getVal('r-md')};"></div>
<div style="width:28px; height:28px; background:${accent}; border-radius:${getVal('r-lg')};"></div>
<div style="width:28px; height:28px; background:${primary}; border-radius:${getVal('r-full')};"></div>
</div>
</div>
<div style="flex:1; min-width:140px; background:${surface}; border:1.5px solid ${border}; border-radius:${rlg}; padding:${spmd};">
<div style="font-size:${smSz}; color:${muted}; font-weight:${wb}; margin-bottom:8px; text-transform:uppercase; letter-spacing:0.06em;">Colors</div>
<div style="display:flex; gap:4px; flex-wrap:wrap;">
${[primary, secondary, accent, text, muted, border].map(c =>
`<div style="width:22px; height:22px; border-radius:4px; background:${c}; border:1px solid rgba(0,0,0,0.08);"></div>`
).join('')}
</div>
</div>
</div>

</div>
`;
}

/* ── Main update ── */
function updateAll() {
buildPreview();
const css = buildCSS();
const box = gid('cv-code-box');
if (box) box.textContent = css;
}

/* ── Color picker sync ── */
function bindColor(colorId, hexId) {
const cEl = gid(colorId);
const hEl = gid(hexId);
if (!cEl || !hEl) return;
cEl.addEventListener('input', () => {
hEl.value = cEl.value;
updateAll();
});
hEl.addEventListener('input', () => {
const v = hEl.value.trim();
if (/^#[0-9a-fA-F]{6}$/.test(v)) {
cEl.value = v;
}
updateAll();
});
// init swatch bg
const swatch = cEl.closest('.cv-color-swatch');
if (swatch) swatch.style.background = cEl.value;
cEl.addEventListener('change', () => {
const swatch = cEl.closest('.cv-color-swatch');
if (swatch) swatch.style.background = cEl.value;
});
cEl.addEventListener('input', () => {
const swatch = cEl.closest('.cv-color-swatch');
if (swatch) swatch.style.background = cEl.value;
});
}

/* ── Copy button ── */
function initCopy() {
const btn = gid('cv-copy-btn');
if (!btn) return;
btn.addEventListener('click', () => {
const css = buildCSS();
navigator.clipboard.writeText(css).then(() => {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(() => {
btn.textContent = 'Copy CSS';
btn.classList.remove('copied');
}, 2000);
}).catch(() => {
// fallback
const ta = document.createElement('textarea');
ta.value = css;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(() => {
btn.textContent = 'Copy CSS';
btn.classList.remove('copied');
}, 2000);
});
});
}

/* ── Preset buttons ── */
function initPresets() {
document.querySelectorAll('#cssvar-app .cv-preset-btn').forEach(btn => {
btn.addEventListener('click', () => {
document.querySelectorAll('#cssvar-app .cv-preset-btn').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
activePreset = btn.dataset.preset;
applyPreset(activePreset);
});
});
}

/* ── Generic input listeners ── */
function initInputs() {
const ids = [
't-font-family', 't-base', 't-sm', 't-lg', 't-xl', 't-2xl',
't-weight-normal', 't-weight-bold', 't-leading', 't-leading-tight',
'sp-xs','sp-sm','sp-md','sp-lg','sp-xl','sp-2xl','sp-3xl',
'r-sm','r-md','r-lg','r-xl','r-full',
'sh-sm','sh-md','sh-lg','sh-xl'
];
ids.forEach(id => {
const el = gid(id);
if (el) el.addEventListener('input', updateAll);
if (el) el.addEventListener('change', updateAll);
});
}

/* ── Init ── */
function init() {
bindColor('c-primary',    'h-primary');
bindColor('c-secondary',  'h-secondary');
bindColor('c-accent',     'h-accent');
bindColor('c-bg',         'h-bg');
bindColor('c-surface',    'h-surface');
bindColor('c-text',       'h-text');
bindColor('c-text-muted', 'h-text-muted');
bindColor('c-border',     'h-border');
initInputs();
initPresets();
initCopy();
updateAll();
}

if (document.readyState === 'loading') {
document.addEventListener('DOMContentLoaded', init);
} else {
init();
}
})();
</script>

---

## Related Tools

> [Box Shadow Generator](/tools/box-shadow-generator/)
> [Css Animation Generator](/tools/css-animation-generator/)
> [Css Button Generator](/tools/css-button-generator/)

