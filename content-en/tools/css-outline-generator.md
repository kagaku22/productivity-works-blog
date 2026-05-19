---
title: "CSS Outline Generator"
slug: "css-outline-generator"
date: 2025-05-16
description: "Free CSS outline generator. Customize outline style, width, color, and offset with live preview — copy CSS code for borders and focus states."
categories: ["Free Tools"]
tags: ["CSS", "outline", "generator", "web design", "accessibility", "focus state"]
cover:
  image: "/images/covers/css-outline-generator.png"
  alt: "CSS Outline Generator tool with live preview"
ShowToc: false
---

Generate CSS outline code instantly. Adjust style, width, color, and offset — see the live preview update in real time, then copy the ready-to-use CSS.

<div id="ot-app">

<style>
/* ── Reset & layout ─────────────────────────────────────────────── */
#ot-app *,
#ot-app *::before,
#ot-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#ot-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f8f9fc;
border-radius: 12px;
padding: 0 0 32px;
max-width: 900px;
}

/* ── Section headings ────────────────────────────────────────────── */
#ot-app .ot-section-title {
font-size: 13px;
font-weight: 700;
letter-spacing: .06em;
text-transform: uppercase;
color: #6b7280;
margin-bottom: 12px;
}

/* ── Two-column layout ───────────────────────────────────────────── */
#ot-app .ot-layout {
display: grid;
grid-template-columns: 300px 1fr;
gap: 20px;
align-items: start;
}
@media (max-width: 680px) {
#ot-app .ot-layout { grid-template-columns: 1fr; }
}

/* ── Controls panel ──────────────────────────────────────────────── */
#ot-app .ot-panel {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 20px;
display: flex;
flex-direction: column;
gap: 18px;
}

#ot-app .ot-control-group { display: flex; flex-direction: column; gap: 6px; }

#ot-app label {
font-size: 13px;
font-weight: 600;
color: #374151;
display: flex;
justify-content: space-between;
align-items: center;
}
#ot-app label span.ot-val {
font-weight: 700;
color: #4f46e5;
font-size: 12px;
background: #eef2ff;
border-radius: 4px;
padding: 1px 6px;
min-width: 44px;
text-align: center;
}

#ot-app select,
#ot-app input[type="range"] {
width: 100%;
}

#ot-app select {
appearance: none;
background: #f3f4f6 url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%236b7280' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E") no-repeat right 10px center;
border: 1px solid #d1d5db;
border-radius: 6px;
padding: 7px 30px 7px 10px;
font-size: 13px;
color: #1a1a2e;
cursor: pointer;
}
#ot-app select:focus { outline: 2px solid #4f46e5; outline-offset: 1px; }

#ot-app input[type="range"] {
accent-color: #4f46e5;
height: 4px;
cursor: pointer;
}

/* Color row */
#ot-app .ot-color-row {
display: grid;
grid-template-columns: 44px 1fr;
gap: 8px;
align-items: center;
}
#ot-app input[type="color"] {
width: 44px;
height: 36px;
border: 1px solid #d1d5db;
border-radius: 6px;
padding: 2px;
cursor: pointer;
background: #fff;
}
#ot-app .ot-hex-input {
width: 100%;
border: 1px solid #d1d5db;
border-radius: 6px;
padding: 7px 10px;
font-size: 13px;
font-family: "Fira Mono", "Courier New", monospace;
color: #1a1a2e;
}
#ot-app .ot-hex-input:focus { outline: 2px solid #4f46e5; outline-offset: 1px; }

/* Toggle */
#ot-app .ot-toggle-row {
display: flex;
align-items: center;
gap: 10px;
font-size: 13px;
font-weight: 600;
color: #374151;
cursor: pointer;
user-select: none;
}
#ot-app .ot-toggle {
position: relative;
width: 40px;
height: 22px;
flex-shrink: 0;
}
#ot-app .ot-toggle input { opacity: 0; width: 0; height: 0; position: absolute; }
#ot-app .ot-toggle-track {
position: absolute;
inset: 0;
background: #d1d5db;
border-radius: 11px;
transition: background .2s;
}
#ot-app .ot-toggle input:checked ~ .ot-toggle-track { background: #4f46e5; }
#ot-app .ot-toggle-thumb {
position: absolute;
top: 3px;
left: 3px;
width: 16px;
height: 16px;
background: #fff;
border-radius: 50%;
transition: transform .2s;
box-shadow: 0 1px 3px rgba(0,0,0,.2);
}
#ot-app .ot-toggle input:checked ~ .ot-toggle-thumb { transform: translateX(18px); }

/* ── Right column ────────────────────────────────────────────────── */
#ot-app .ot-right { display: flex; flex-direction: column; gap: 20px; }

/* ── Preview area ────────────────────────────────────────────────── */
#ot-app .ot-preview-wrap {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 24px;
}
#ot-app .ot-preview-stage {
display: flex;
gap: 32px;
flex-wrap: wrap;
justify-content: center;
align-items: center;
min-height: 140px;
background: repeating-conic-gradient(#f0f0f0 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
border-radius: 8px;
padding: 32px 24px;
}
#ot-app .ot-preview-box {
width: 120px;
height: 80px;
background: #fff;
border-radius: 6px;
display: flex;
align-items: center;
justify-content: center;
font-size: 12px;
font-weight: 600;
color: #6b7280;
flex-direction: column;
gap: 4px;
transition: outline .15s, border .15s, outline-offset .15s;
}
#ot-app .ot-preview-box .ot-label {
font-size: 10px;
font-weight: 700;
letter-spacing: .05em;
text-transform: uppercase;
color: #9ca3af;
margin-top: 4px;
}

/* Focus demo */
#ot-app .ot-focus-demo {
display: flex;
flex-direction: column;
align-items: center;
gap: 8px;
}
#ot-app .ot-focus-btn {
padding: 8px 18px;
border: none;
border-radius: 6px;
background: #4f46e5;
color: #fff;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: outline .15s, outline-offset .15s;
}
#ot-app .ot-focus-btn:focus { outline-style: solid; outline-width: 2px; outline-color: #4f46e5; outline-offset: 3px; }
#ot-app .ot-focus-label {
font-size: 10px;
font-weight: 700;
letter-spacing: .05em;
text-transform: uppercase;
color: #9ca3af;
}

/* ── Presets ─────────────────────────────────────────────────────── */
#ot-app .ot-presets-wrap {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 20px;
}
#ot-app .ot-presets-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
gap: 10px;
}
#ot-app .ot-preset-btn {
border: 1.5px solid #e5e7eb;
border-radius: 8px;
padding: 10px 12px;
background: #f9fafb;
font-size: 12px;
font-weight: 600;
color: #374151;
cursor: pointer;
text-align: left;
transition: border-color .15s, background .15s;
display: flex;
flex-direction: column;
gap: 4px;
}
#ot-app .ot-preset-btn:hover { border-color: #4f46e5; background: #eef2ff; color: #4f46e5; }
#ot-app .ot-preset-swatch {
width: 100%;
height: 28px;
border-radius: 4px;
background: #f3f4f6;
margin-bottom: 4px;
display: flex;
align-items: center;
justify-content: center;
}
#ot-app .ot-preset-swatch span {
width: 60px;
height: 16px;
background: #fff;
border-radius: 3px;
}

/* ── Output ──────────────────────────────────────────────────────── */
#ot-app .ot-output-wrap {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 20px;
}
#ot-app .ot-output-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 12px;
}
#ot-app .ot-copy-btn {
background: #4f46e5;
color: #fff;
border: none;
border-radius: 6px;
padding: 7px 16px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background .15s;
display: flex;
align-items: center;
gap: 6px;
}
#ot-app .ot-copy-btn:hover { background: #4338ca; }
#ot-app .ot-copy-btn.copied { background: #059669; }
#ot-app pre.ot-code {
background: #0f172a;
border-radius: 8px;
padding: 16px 18px;
overflow-x: auto;
font-family: "Fira Mono", "Courier New", monospace;
font-size: 13px;
line-height: 1.7;
white-space: pre;
color: #e2e8f0;
}
#ot-app .ot-kw  { color: #818cf8; }
#ot-app .ot-prop{ color: #7dd3fc; }
#ot-app .ot-val-c{ color: #86efac; }
#ot-app .ot-punc{ color: #94a3b8; }
#ot-app .ot-comment { color: #64748b; font-style: italic; }

/* ── Accessibility output ────────────────────────────────────────── */
#ot-app .ot-a11y-wrap {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 10px;
padding: 20px;
}
#ot-app .ot-a11y-note {
font-size: 12px;
color: #6b7280;
margin-bottom: 12px;
line-height: 1.5;
}
#ot-app pre.ot-code-a11y {
background: #0f172a;
border-radius: 8px;
padding: 16px 18px;
overflow-x: auto;
font-family: "Fira Mono", "Courier New", monospace;
font-size: 13px;
line-height: 1.7;
white-space: pre;
color: #e2e8f0;
}

/* ── Info strip ──────────────────────────────────────────────────── */
#ot-app .ot-info {
background: #eef2ff;
border-left: 3px solid #4f46e5;
border-radius: 0 6px 6px 0;
padding: 12px 16px;
font-size: 12.5px;
color: #3730a3;
line-height: 1.6;
}
</style>

<!-- ── Presets ──────────────────────────────────────────────── -->
<div class="ot-presets-wrap">
<p class="ot-section-title">Presets</p>
<div class="ot-presets-grid" id="ot-presets"></div>
</div>

<!-- ── Main layout ─────────────────────────────────────────── -->
<div class="ot-layout">

<!-- Controls -->
<div class="ot-panel">
<p class="ot-section-title">Controls</p>

<!-- outline-style -->
<div class="ot-control-group">
<label for="ot-style">outline-style</label>
<select id="ot-style">
<option value="solid" selected>solid</option>
<option value="dashed">dashed</option>
<option value="dotted">dotted</option>
<option value="double">double</option>
<option value="groove">groove</option>
<option value="ridge">ridge</option>
<option value="inset">inset</option>
<option value="outset">outset</option>
</select>
</div>

<!-- outline-width -->
<div class="ot-control-group">
<label for="ot-width">outline-width <span class="ot-val" id="ot-width-val">3px</span></label>
<input type="range" id="ot-width" min="1" max="20" value="3" step="1">
</div>

<!-- outline-color -->
<div class="ot-control-group">
<label for="ot-color">outline-color</label>
<div class="ot-color-row">
<input type="color" id="ot-color" value="#4f46e5">
<input type="text" class="ot-hex-input" id="ot-hex" value="#4f46e5" maxlength="9" spellcheck="false">
</div>
</div>

<!-- outline-offset -->
<div class="ot-control-group">
<label for="ot-offset">outline-offset <span class="ot-val" id="ot-offset-val">3px</span></label>
<input type="range" id="ot-offset" min="-20" max="20" value="3" step="1">
</div>

<!-- compare with border toggle -->
<label class="ot-toggle-row">
<span class="ot-toggle">
<input type="checkbox" id="ot-compare">
<span class="ot-toggle-track"></span>
<span class="ot-toggle-thumb"></span>
</span>
Compare with border
</label>

<!-- focus state toggle -->
<label class="ot-toggle-row">
<span class="ot-toggle">
<input type="checkbox" id="ot-focus-mode">
<span class="ot-toggle-track"></span>
<span class="ot-toggle-thumb"></span>
</span>
Focus state preview
</label>
</div>

<!-- Right column -->
<div class="ot-right">

<!-- Preview -->
<div class="ot-preview-wrap">
<p class="ot-section-title">Live Preview</p>
<div class="ot-preview-stage" id="ot-stage">
<div>
<div class="ot-preview-box" id="ot-box-outline">
Outline
<span class="ot-label">outline</span>
</div>
</div>
<div id="ot-border-col" style="display:none">
<div class="ot-preview-box" id="ot-box-border">
Border
<span class="ot-label">border</span>
</div>
</div>
<div id="ot-focus-col" style="display:none" class="ot-focus-demo">
<button class="ot-focus-btn" id="ot-focus-btn">Focus me</button>
<span class="ot-focus-label">Tab to focus</span>
</div>
</div>
</div>

<!-- CSS Output -->
<div class="ot-output-wrap">
<div class="ot-output-header">
<p class="ot-section-title" style="margin:0">CSS Output</p>
<button class="ot-copy-btn" id="ot-copy-btn">
<svg width="14" height="14" viewBox="0 0 16 16" fill="none" aria-hidden="true">
<rect x="5" y="5" width="9" height="10" rx="1.5" stroke="currentColor" stroke-width="1.5"/>
<path d="M3 11H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h8a1 1 0 0 1 1 1v1" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
</svg>
Copy CSS
</button>
</div>
<pre class="ot-code" id="ot-code-out"></pre>
</div>

<!-- Accessibility / Focus State Output -->
<div class="ot-a11y-wrap" id="ot-a11y-wrap">
<div class="ot-output-header">
<p class="ot-section-title" style="margin:0">Focus State CSS (Accessibility)</p>
<button class="ot-copy-btn" id="ot-copy-a11y-btn">
<svg width="14" height="14" viewBox="0 0 16 16" fill="none" aria-hidden="true">
<rect x="5" y="5" width="9" height="10" rx="1.5" stroke="currentColor" stroke-width="1.5"/>
<path d="M3 11H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h8a1 1 0 0 1 1 1v1" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
</svg>
Copy
</button>
</div>
<p class="ot-a11y-note">Use <code>:focus-visible</code> for keyboard-only focus rings (WCAG 2.4.11 recommendation). Minimum 3:1 contrast ratio required.</p>
<pre class="ot-code-a11y" id="ot-a11y-out"></pre>
</div>

<div class="ot-info">
<strong>Tip:</strong> Unlike <code>border</code>, <code>outline</code> does not affect layout — it draws outside the element without shifting surrounding content. Use <code>outline-offset</code> to create a gap between element and outline.
</div>

</div>
</div><!-- /.ot-layout -->

<script>
(function () {
// ── State ──────────────────────────────────────────────────────────
const state = {
style: "solid",
width: 3,
color: "#4f46e5",
offset: 3,
compare: false,
focusMode: false,
};

// ── Presets ────────────────────────────────────────────────────────
const PRESETS = [
{
name: "Focus Ring",
icon: "focus",
style: "solid", width: 3, color: "#4f46e5", offset: 3,
},
{
name: "Double Border",
icon: "double",
style: "double", width: 5, color: "#1e40af", offset: 2,
},
{
name: "Neon Glow",
icon: "neon",
style: "solid", width: 3, color: "#22d3ee", offset: 4,
},
{
name: "Dashed Accent",
icon: "dashed",
style: "dashed", width: 2, color: "#f59e0b", offset: 4,
},
{
name: "Inset Frame",
icon: "inset",
style: "inset", width: 6, color: "#6b7280", offset: 0,
},
];

const PRESET_ICONS = {
focus:  "#4f46e5",
double: "#1e40af",
neon:   "#22d3ee",
dashed: "#f59e0b",
inset:  "#6b7280",
};

// ── DOM refs ───────────────────────────────────────────────────────
const $ = (id) => document.getElementById(id);
const elStyle      = $("ot-style");
const elWidth      = $("ot-width");
const elWidthVal   = $("ot-width-val");
const elColor      = $("ot-color");
const elHex        = $("ot-hex");
const elOffset     = $("ot-offset");
const elOffsetVal  = $("ot-offset-val");
const elCompare    = $("ot-compare");
const elFocusMode  = $("ot-focus-mode");
const elBoxOutline = $("ot-box-outline");
const elBoxBorder  = $("ot-box-border");
const elBorderCol  = $("ot-border-col");
const elFocusCol   = $("ot-focus-col");
const elFocusBtn   = $("ot-focus-btn");
const elCodeOut    = $("ot-code-out");
const elA11yOut    = $("ot-a11y-out");
const elCopyBtn    = $("ot-copy-btn");
const elCopyA11y   = $("ot-copy-a11y-btn");
const elPresets    = $("ot-presets");

// ── Render presets ─────────────────────────────────────────────────
PRESETS.forEach((p) => {
const btn = document.createElement("button");
btn.className = "ot-preset-btn";
const swatchColor = PRESET_ICONS[p.icon];
btn.innerHTML = `
<div class="ot-preset-swatch" style="background:#f0f0f0">
<span style="outline:${p.width}px ${p.style} ${p.color};outline-offset:${p.offset}px;width:48px;height:18px;border-radius:3px;background:#fff;display:block"></span>
</div>
${p.name}
`;
btn.addEventListener("click", () => applyPreset(p));
elPresets.appendChild(btn);
});

function applyPreset(p) {
state.style  = p.style;
state.width  = p.width;
state.color  = p.color;
state.offset = p.offset;
syncInputs();
render();
}

function syncInputs() {
elStyle.value  = state.style;
elWidth.value  = state.width;
elWidthVal.textContent = state.width + "px";
elColor.value  = state.color;
elHex.value    = state.color;
elOffset.value = state.offset;
elOffsetVal.textContent = state.offset + "px";
}

// ── Syntax highlighter ─────────────────────────────────────────────
function highlight(css) {
// Very light manual highlight — no external lib
return css
.replace(/\/\*.*?\*\//gs, (m) => `<span class="ot-comment">${m}</span>`)
.replace(/([.#:[\]a-zA-Z_-]+\s*(?:,\s*[.#:[\]a-zA-Z_-]+)*)\s*\{/g,
(_, sel) => `<span class="ot-kw">${sel}</span> <span class="ot-punc">{</span>`)
.replace(/\}/g, `<span class="ot-punc">}</span>`)
.replace(/([\w-]+)(\s*:\s*)/g,
(_, prop, colon) => `<span class="ot-prop">${prop}</span><span class="ot-punc">${colon}</span>`)
.replace(/:\s*([^;<\n{]+)(;)/g,
(_, val, semi) => `: <span class="ot-val-c">${val.trim()}</span><span class="ot-punc">;</span>`)
;
}

// ── Main render ────────────────────────────────────────────────────
function render() {
const { style, width, color, offset, compare, focusMode } = state;
const outlineShorthand = `${width}px ${style} ${color}`;

// Preview element
elBoxOutline.style.outline       = outlineShorthand;
elBoxOutline.style.outlineOffset = offset + "px";

// Compare border
elBorderCol.style.display = compare ? "" : "none";
if (compare) {
elBoxBorder.style.border = outlineShorthand;
elBoxBorder.style.outline = "none";
}

// Focus preview
elFocusCol.style.display = focusMode ? "" : "none";
if (focusMode) {
elFocusBtn.style.setProperty("--ot-fw", width + "px");
elFocusBtn.style.setProperty("--ot-fs", style);
elFocusBtn.style.setProperty("--ot-fc", color);
elFocusBtn.style.setProperty("--ot-fo", offset + "px");
// apply directly
elFocusBtn.style.outlineStyle  = style;
elFocusBtn.style.outlineWidth  = width + "px";
elFocusBtn.style.outlineColor  = color;
elFocusBtn.style.outlineOffset = offset + "px";
} else {
elFocusBtn.style.outlineStyle  = "";
elFocusBtn.style.outlineWidth  = "";
elFocusBtn.style.outlineColor  = "";
elFocusBtn.style.outlineOffset = "";
}

// CSS output
const cssLines = [
`.element {`,
`  outline-style:  ${style};`,
`  outline-width:  ${width}px;`,
`  outline-color:  ${color};`,
`  outline-offset: ${offset}px;`,
`  /* shorthand: */`,
`  outline: ${outlineShorthand};`,
`}`,
].join("\n");

elCodeOut.innerHTML = highlight(cssLines);

// A11y focus CSS
const a11yLines = [
`/* Keyboard focus ring — WCAG 2.4.11 */`,
`.element:focus        { outline: none; }`,
`.element:focus-visible {`,
`  outline-style:  ${style};`,
`  outline-width:  ${width}px;`,
`  outline-color:  ${color};`,
`  outline-offset: ${offset}px;`,
`}`,
].join("\n");

elA11yOut.innerHTML = highlight(a11yLines);
}

// ── Event listeners ────────────────────────────────────────────────
elStyle.addEventListener("change", () => { state.style = elStyle.value; render(); });

elWidth.addEventListener("input", () => {
state.width = +elWidth.value;
elWidthVal.textContent = state.width + "px";
render();
});

elColor.addEventListener("input", () => {
state.color = elColor.value;
elHex.value = elColor.value;
render();
});

elHex.addEventListener("input", () => {
const v = elHex.value.trim();
if (/^#[0-9a-fA-F]{6}$/.test(v) || /^#[0-9a-fA-F]{3}$/.test(v)) {
state.color = v;
elColor.value = v;
render();
}
});

elOffset.addEventListener("input", () => {
state.offset = +elOffset.value;
elOffsetVal.textContent = state.offset + "px";
render();
});

elCompare.addEventListener("change", () => { state.compare = elCompare.checked; render(); });
elFocusMode.addEventListener("change", () => { state.focusMode = elFocusMode.checked; render(); });

// ── Copy buttons ───────────────────────────────────────────────────
function copyText(text, btn) {
navigator.clipboard.writeText(text).then(() => {
const orig = btn.innerHTML;
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(() => { btn.innerHTML = orig; btn.classList.remove("copied"); }, 1800);
});
}

elCopyBtn.addEventListener("click", () => {
const { style, width, color, offset } = state;
const text = `.element {\n  outline-style:  ${style};\n  outline-width:  ${width}px;\n  outline-color:  ${color};\n  outline-offset: ${offset}px;\n  /* shorthand: */\n  outline: ${width}px ${style} ${color};\n}`;
copyText(text, elCopyBtn);
});

elCopyA11y.addEventListener("click", () => {
const { style, width, color, offset } = state;
const text = `/* Keyboard focus ring — WCAG 2.4.11 */\n.element:focus         { outline: none; }\n.element:focus-visible {\n  outline-style:  ${style};\n  outline-width:  ${width}px;\n  outline-color:  ${color};\n  outline-offset: ${offset}px;\n}`;
copyText(text, elCopyA11y);
});

// ── Init ───────────────────────────────────────────────────────────
render();
})();
</script>

</div><!-- /#ot-app -->

---

## How to Use

1. Choose an **outline-style** from the dropdown — solid, dashed, dotted, double, and more.
2. Drag **outline-width** to set thickness (1–20 px).
3. Pick an **outline-color** from the color picker or type a hex value.
4. Adjust **outline-offset** to push the outline away from (or inside) the element boundary.
5. Enable **Compare with border** to see the layout difference side by side.
6. Enable **Focus state preview** to see how the outline looks as a focus ring.
7. Click **Copy CSS** to copy the generated code.

---

## Outline vs. Border — Key Differences

| Property | Affects layout | Follows border-radius | Offset support |
|---|---|---|---|
| `outline` | No | Partially | Yes (`outline-offset`) |
| `border` | Yes | Yes | No |

Because `outline` does not affect layout, it is ideal for **focus indicators** — adding a visible ring around focused elements without causing content reflow.

---

## Accessibility Tips

- WCAG 2.4.11 (AA, WCAG 2.2) requires focus indicators to have a contrast ratio of at least **3:1** against adjacent colors.
- Use `:focus-visible` instead of `:focus` to show rings only for keyboard navigation, not mouse clicks.
- `outline-offset` of 2–4 px improves legibility on rounded elements.
- Never use `outline: none` without providing an alternative focus style.

---

## Related Tools

- [CSS Border Radius Generator](/tools/border-radius-generator/)
- [CSS Box Shadow Generator](/tools/box-shadow-generator/)
- [CSS Button Generator](/tools/css-button-generator/)
