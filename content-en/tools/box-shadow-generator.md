---
title: "CSS Box Shadow Generator — Free Online Tool"
date: 2025-05-16
description: "Generate CSS box-shadow code instantly. Live preview, multiple shadows, presets, opacity control, inset toggle, and Tailwind equivalents. No signup, no external libs."
categories: ["Free Tools"]
slug: "box-shadow-generator"
ShowToc: false
aliases:
  - "/tools/box-shadow-generator/"
  - "/tools/box-shadow-generator/"
cover:
  image: "/images/covers/box-shadow-generator.png"
  alt: "CSS Box Shadow Generator"
---

<div id="shadow-app">

<style>
#shadow-app *,
#shadow-app *::before,
#shadow-app *::after {
box-sizing: border-box;
}

#shadow-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #f3f4f6;
background: #374151;
border-radius: 12px;
padding: 24px;
max-width: 900px;
margin: 0 auto;
}

#shadow-app h2 {
margin: 0 0 20px;
font-size: 1.25rem;
font-weight: 600;
color: #f9fafb;
border-bottom: 1px solid #4b5563;
padding-bottom: 10px;
}

#shadow-app .sa-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 24px;
}

@media (max-width: 680px) {
#shadow-app .sa-layout {
grid-template-columns: 1fr;
}
}

/* Preview */
#shadow-app .sa-preview-area {
background: #4b5563;
border-radius: 10px;
padding: 20px;
display: flex;
flex-direction: column;
gap: 16px;
}

#shadow-app .sa-preview-label {
font-size: 0.75rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #9ca3af;
}

#shadow-app .sa-preview-box-wrap {
flex: 1;
min-height: 180px;
display: flex;
align-items: center;
justify-content: center;
background: #374151;
border-radius: 8px;
padding: 24px;
}

#shadow-app .sa-preview-box {
width: 120px;
height: 120px;
background: #ffffff;
border-radius: 8px;
transition: box-shadow 0.2s ease;
}

/* Controls panel */
#shadow-app .sa-controls {
display: flex;
flex-direction: column;
gap: 0;
}

/* Presets */
#shadow-app .sa-presets {
background: #4b5563;
border-radius: 10px;
padding: 16px;
margin-bottom: 16px;
}

#shadow-app .sa-preset-grid {
display: flex;
flex-wrap: wrap;
gap: 6px;
margin-top: 8px;
}

#shadow-app .sa-preset-btn {
background: #374151;
border: 1px solid #6b7280;
color: #d1d5db;
padding: 5px 10px;
border-radius: 6px;
font-size: 0.75rem;
cursor: pointer;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}

#shadow-app .sa-preset-btn:hover,
#shadow-app .sa-preset-btn.sa-active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}

/* Shadow list */
#shadow-app .sa-shadow-list {
display: flex;
flex-direction: column;
gap: 12px;
margin-bottom: 12px;
}

#shadow-app .sa-shadow-item {
background: #4b5563;
border-radius: 10px;
padding: 14px;
position: relative;
}

#shadow-app .sa-shadow-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 12px;
}

#shadow-app .sa-shadow-title {
font-size: 0.8rem;
font-weight: 600;
color: #e5e7eb;
}

#shadow-app .sa-shadow-actions {
display: flex;
gap: 6px;
align-items: center;
}

#shadow-app .sa-toggle-btn {
background: none;
border: 1px solid #6b7280;
color: #9ca3af;
padding: 3px 8px;
border-radius: 5px;
font-size: 0.7rem;
cursor: pointer;
transition: all 0.15s;
}

#shadow-app .sa-toggle-btn.sa-active {
background: #818cf8;
border-color: #818cf8;
color: #fff;
}

#shadow-app .sa-remove-btn {
background: none;
border: 1px solid #6b7280;
color: #9ca3af;
width: 22px;
height: 22px;
border-radius: 5px;
font-size: 0.85rem;
line-height: 1;
cursor: pointer;
display: flex;
align-items: center;
justify-content: center;
transition: all 0.15s;
}

#shadow-app .sa-remove-btn:hover {
background: #ef4444;
border-color: #ef4444;
color: #fff;
}

/* Sliders */
#shadow-app .sa-field {
display: grid;
grid-template-columns: 90px 1fr 44px;
align-items: center;
gap: 8px;
margin-bottom: 8px;
}

#shadow-app .sa-field:last-child {
margin-bottom: 0;
}

#shadow-app .sa-field label {
font-size: 0.72rem;
color: #9ca3af;
white-space: nowrap;
}

#shadow-app .sa-field input[type="range"] {
-webkit-appearance: none;
appearance: none;
width: 100%;
height: 4px;
border-radius: 2px;
background: #6b7280;
outline: none;
cursor: pointer;
}

#shadow-app .sa-field input[type="range"]::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 14px;
height: 14px;
border-radius: 50%;
background: #6366f1;
cursor: pointer;
}

#shadow-app .sa-field input[type="range"]::-moz-range-thumb {
width: 14px;
height: 14px;
border-radius: 50%;
background: #6366f1;
cursor: pointer;
border: none;
}

#shadow-app .sa-field .sa-val {
font-size: 0.72rem;
color: #d1d5db;
text-align: right;
font-variant-numeric: tabular-nums;
min-width: 40px;
}

/* Color row */
#shadow-app .sa-color-row {
display: grid;
grid-template-columns: 90px 28px 1fr 44px;
align-items: center;
gap: 8px;
margin-bottom: 8px;
}

#shadow-app .sa-color-row label {
font-size: 0.72rem;
color: #9ca3af;
}

#shadow-app .sa-color-row input[type="color"] {
-webkit-appearance: none;
appearance: none;
width: 28px;
height: 22px;
border: none;
background: none;
padding: 0;
cursor: pointer;
border-radius: 4px;
}

#shadow-app .sa-color-row input[type="range"] {
-webkit-appearance: none;
appearance: none;
width: 100%;
height: 4px;
border-radius: 2px;
background: #6b7280;
outline: none;
cursor: pointer;
}

#shadow-app .sa-color-row input[type="range"]::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 14px;
height: 14px;
border-radius: 50%;
background: #6366f1;
cursor: pointer;
}

#shadow-app .sa-color-row input[type="range"]::-moz-range-thumb {
width: 14px;
height: 14px;
border-radius: 50%;
background: #6366f1;
cursor: pointer;
border: none;
}

#shadow-app .sa-color-row .sa-val {
font-size: 0.72rem;
color: #d1d5db;
text-align: right;
font-variant-numeric: tabular-nums;
}

/* Add shadow button */
#shadow-app .sa-add-btn {
width: 100%;
background: #374151;
border: 1px dashed #6b7280;
color: #9ca3af;
padding: 8px;
border-radius: 8px;
font-size: 0.8rem;
cursor: pointer;
transition: all 0.15s;
margin-bottom: 16px;
}

#shadow-app .sa-add-btn:hover {
border-color: #6366f1;
color: #a5b4fc;
}

#shadow-app .sa-add-btn:disabled {
opacity: 0.4;
cursor: not-allowed;
}

/* Output */
#shadow-app .sa-output {
background: #4b5563;
border-radius: 10px;
padding: 16px;
grid-column: 1 / -1;
}

#shadow-app .sa-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 10px;
}

#shadow-app .sa-copy-btn {
background: #6366f1;
border: none;
color: #fff;
padding: 5px 14px;
border-radius: 6px;
font-size: 0.78rem;
cursor: pointer;
transition: background 0.15s;
}

#shadow-app .sa-copy-btn:hover {
background: #4f46e5;
}

#shadow-app .sa-copy-btn.sa-copied {
background: #10b981;
}

#shadow-app code.sa-code-block {
display: block;
background: #1f2937;
border-radius: 6px;
padding: 12px 14px;
font-family: "Fira Code", "Cascadia Code", Consolas, monospace;
font-size: 0.82rem;
color: #86efac;
white-space: pre-wrap;
word-break: break-all;
margin-bottom: 10px;
border: 1px solid #374151;
}

#shadow-app .sa-tailwind-row {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
margin-top: 6px;
}

#shadow-app .sa-tw-label {
font-size: 0.72rem;
color: #9ca3af;
white-space: nowrap;
}

#shadow-app code.sa-tw-code {
background: #1f2937;
border: 1px solid #374151;
border-radius: 5px;
padding: 3px 8px;
font-family: "Fira Code", Consolas, monospace;
font-size: 0.78rem;
color: #7dd3fc;
}
</style>

<h2>CSS Box Shadow Generator</h2>

<div class="sa-layout">
<!-- Left: preview + presets + shadows -->
<div>
<!-- Preview -->
<div class="sa-preview-area" style="margin-bottom:16px;">
<div class="sa-preview-label">Live Preview</div>
<div class="sa-preview-box-wrap">
<div class="sa-preview-box" id="sa-preview-box"></div>
</div>
</div>

<!-- Presets -->
<div class="sa-presets">
<div class="sa-preview-label">Presets</div>
<div class="sa-preset-grid" id="sa-preset-grid"></div>
</div>
</div>

<!-- Right: shadow controls -->
<div class="sa-controls">
<div class="sa-shadow-list" id="sa-shadow-list"></div>
<button class="sa-add-btn" id="sa-add-btn">+ Add Shadow Layer</button>
</div>

<!-- Output -->
<div class="sa-output">
<div class="sa-output-header">
<div class="sa-preview-label">Generated CSS</div>
<button class="sa-copy-btn" id="sa-copy-btn">Copy CSS</button>
</div>
<code class="sa-code-block" id="sa-css-output"></code>
<div class="sa-tailwind-row">
<span class="sa-tw-label">Tailwind equivalent:</span>
<code class="sa-tw-code" id="sa-tw-output">—</code>
</div>
</div>
</div>

<script>
(function () {
"use strict";

/* ── Presets ─────────────────────────────────────────────── */
const PRESETS = [
{
name: "Subtle",
shadows: [{ x: 0, y: 1, blur: 3, spread: 0, color: "#000000", opacity: 0.12, inset: false }],
},
{
name: "Medium",
shadows: [{ x: 0, y: 4, blur: 12, spread: 0, color: "#000000", opacity: 0.18, inset: false }],
},
{
name: "Large",
shadows: [{ x: 0, y: 10, blur: 30, spread: -5, color: "#000000", opacity: 0.25, inset: false }],
},
{
name: "Sharp",
shadows: [{ x: 4, y: 4, blur: 0, spread: 0, color: "#000000", opacity: 0.35, inset: false }],
},
{
name: "Soft",
shadows: [
{ x: 0, y: 2, blur: 8, spread: 0, color: "#000000", opacity: 0.08, inset: false },
{ x: 0, y: 8, blur: 24, spread: 0, color: "#000000", opacity: 0.12, inset: false },
],
},
{
name: "Neon",
shadows: [{ x: 0, y: 0, blur: 20, spread: 4, color: "#6366f1", opacity: 0.85, inset: false }],
},
{
name: "Inset",
shadows: [{ x: 0, y: 2, blur: 8, spread: 0, color: "#000000", opacity: 0.25, inset: true }],
},
{
name: "Floating",
shadows: [
{ x: 0, y: 1, blur: 2, spread: 0, color: "#000000", opacity: 0.06, inset: false },
{ x: 0, y: 4, blur: 6, spread: -1, color: "#000000", opacity: 0.1, inset: false },
{ x: 0, y: 20, blur: 40, spread: -8, color: "#000000", opacity: 0.18, inset: false },
],
},
{
name: "Brutalist",
shadows: [{ x: 6, y: 6, blur: 0, spread: 0, color: "#111827", opacity: 1, inset: false }],
},
];

/* ── Tailwind map ─────────────────────────────────────────── */
const TW_MAP = [
{ cls: "shadow-sm",  css: "0 1px 2px 0 rgb(0 0 0 / 0.05)" },
{ cls: "shadow",     css: "0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)" },
{ cls: "shadow-md",  css: "0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)" },
{ cls: "shadow-lg",  css: "0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)" },
{ cls: "shadow-xl",  css: "0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)" },
{ cls: "shadow-2xl", css: "0 25px 50px -12px rgb(0 0 0 / 0.25)" },
{ cls: "shadow-inner", css: "inset 0 2px 4px 0 rgb(0 0 0 / 0.05)" },
{ cls: "shadow-none", css: "0 0 #0000" },
];

/* ── State ────────────────────────────────────────────────── */
let shadows = [
{ x: 0, y: 4, blur: 12, spread: 0, color: "#000000", opacity: 0.18, inset: false },
];

/* ── Helpers ──────────────────────────────────────────────── */
function hexToRgb(hex) {
const r = parseInt(hex.slice(1, 3), 16);
const g = parseInt(hex.slice(3, 5), 16);
const b = parseInt(hex.slice(5, 7), 16);
return { r, g, b };
}

function shadowToCSS(s) {
const { r, g, b } = hexToRgb(s.color);
const alpha = Math.round(s.opacity * 100) / 100;
return `${s.inset ? "inset " : ""}${s.x}px ${s.y}px ${s.blur}px ${s.spread}px rgba(${r}, ${g}, ${b}, ${alpha})`;
}

function buildFullCSS() {
const val = shadows.map(shadowToCSS).join(",\n             ");
return `box-shadow: ${val};`;
}

function guessTailwind() {
if (shadows.length !== 1) return null;
const s = shadows[0];
if (s.inset && Math.abs(s.x) <= 1 && Math.abs(s.y) <= 3 && s.blur <= 6) return "shadow-inner";
if (!s.inset) {
if (s.blur === 0 && s.spread === 0 && s.opacity === 0) return "shadow-none";
if (s.blur <= 3 && Math.abs(s.y) <= 2) return "shadow-sm";
if (s.blur <= 6 && Math.abs(s.y) <= 4) return "shadow";
if (s.blur <= 10 && Math.abs(s.y) <= 6) return "shadow-md";
if (s.blur <= 18 && Math.abs(s.y) <= 12) return "shadow-lg";
if (s.blur <= 28 && Math.abs(s.y) <= 22) return "shadow-xl";
if (s.blur <= 55 && Math.abs(s.y) <= 28) return "shadow-2xl";
}
return null;
}

/* ── Render ───────────────────────────────────────────────── */
function render() {
const preview = document.getElementById("sa-preview-box");
const cssOut = document.getElementById("sa-css-output");
const twOut = document.getElementById("sa-tw-output");

const shadowCSS = shadows.map(shadowToCSS).join(", ");
preview.style.boxShadow = shadowCSS;

cssOut.textContent = buildFullCSS();

const tw = guessTailwind();
twOut.textContent = tw ? tw : "No direct Tailwind equivalent (use arbitrary value)";

renderShadowList();
updateAddBtn();
}

function updateAddBtn() {
const btn = document.getElementById("sa-add-btn");
btn.disabled = shadows.length >= 4;
}

function renderShadowList() {
const list = document.getElementById("sa-shadow-list");
list.innerHTML = "";

shadows.forEach((s, i) => {
const item = document.createElement("div");
item.className = "sa-shadow-item";

item.innerHTML = `
<div class="sa-shadow-header">
<span class="sa-shadow-title">Shadow ${i + 1}</span>
<div class="sa-shadow-actions">
<button class="sa-toggle-btn${s.inset ? " sa-active" : ""}" data-i="${i}" data-action="inset">Inset</button>
${shadows.length > 1 ? `<button class="sa-remove-btn" data-i="${i}" data-action="remove" title="Remove">×</button>` : ""}
</div>
</div>

<div class="sa-field">
<label>Horizontal</label>
<input type="range" min="-60" max="60" value="${s.x}" data-i="${i}" data-prop="x">
<span class="sa-val">${s.x}px</span>
</div>
<div class="sa-field">
<label>Vertical</label>
<input type="range" min="-60" max="60" value="${s.y}" data-i="${i}" data-prop="y">
<span class="sa-val">${s.y}px</span>
</div>
<div class="sa-field">
<label>Blur</label>
<input type="range" min="0" max="100" value="${s.blur}" data-i="${i}" data-prop="blur">
<span class="sa-val">${s.blur}px</span>
</div>
<div class="sa-field">
<label>Spread</label>
<input type="range" min="-30" max="30" value="${s.spread}" data-i="${i}" data-prop="spread">
<span class="sa-val">${s.spread}px</span>
</div>

<div class="sa-color-row">
<label>Color / Opacity</label>
<input type="color" value="${s.color}" data-i="${i}" data-prop="color">
<input type="range" min="0" max="1" step="0.01" value="${s.opacity}" data-i="${i}" data-prop="opacity">
<span class="sa-val">${Math.round(s.opacity * 100)}%</span>
</div>
`;

/* Events */
item.querySelectorAll("input[type='range'][data-prop]").forEach((el) => {
el.addEventListener("input", (e) => {
const idx = +e.target.dataset.i;
const prop = e.target.dataset.prop;
shadows[idx][prop] = parseFloat(e.target.value);
render();
});
});

item.querySelectorAll("input[type='color']").forEach((el) => {
el.addEventListener("input", (e) => {
shadows[+e.target.dataset.i].color = e.target.value;
render();
});
});

item.querySelectorAll("button[data-action]").forEach((el) => {
el.addEventListener("click", (e) => {
const idx = +e.target.dataset.i;
const action = e.target.dataset.action;
if (action === "inset") {
shadows[idx].inset = !shadows[idx].inset;
render();
} else if (action === "remove") {
shadows.splice(idx, 1);
render();
}
});
});

list.appendChild(item);
});
}

/* ── Presets ──────────────────────────────────────────────── */
function renderPresets() {
const grid = document.getElementById("sa-preset-grid");
PRESETS.forEach((p) => {
const btn = document.createElement("button");
btn.className = "sa-preset-btn";
btn.textContent = p.name;
btn.addEventListener("click", () => {
shadows = p.shadows.map((s) => ({ ...s }));
document.querySelectorAll("#sa-preset-grid .sa-preset-btn").forEach((b) =>
b.classList.remove("sa-active")
);
btn.classList.add("sa-active");
render();
});
grid.appendChild(btn);
});
}

/* ── Add shadow ───────────────────────────────────────────── */
document.getElementById("sa-add-btn").addEventListener("click", () => {
if (shadows.length < 4) {
shadows.push({ x: 0, y: 4, blur: 12, spread: 0, color: "#000000", opacity: 0.15, inset: false });
render();
}
});

/* ── Copy CSS ─────────────────────────────────────────────── */
document.getElementById("sa-copy-btn").addEventListener("click", () => {
const css = buildFullCSS();
navigator.clipboard.writeText(css).then(() => {
const btn = document.getElementById("sa-copy-btn");
btn.textContent = "Copied!";
btn.classList.add("sa-copied");
setTimeout(() => {
btn.textContent = "Copy CSS";
btn.classList.remove("sa-copied");
}, 1800);
});
});

/* ── Init ─────────────────────────────────────────────────── */
renderPresets();
render();
})();
</script>

</div>

---

### Related Tools

> Generate gradients → [CSS Gradient Generator](/tools/css-gradient-generator/)

> Build color palettes → [Color Palette Generator](/tools/color-palette-generator/)

> Create meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)
