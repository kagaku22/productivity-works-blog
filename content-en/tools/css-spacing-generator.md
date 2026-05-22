---
title: "CSS Spacing Generator — Margin & Padding Tool"
date: 2025-05-16
description: "Visual CSS margin and padding editor with box model diagram. Individual side controls, unit options, and presets. Copy shorthand or longhand CSS instantly."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "css-spacing-generator"
ShowToc: false
cover:
  image: "/images/covers/css-spacing-generator.png"
  alt: "CSS Spacing Generator"
---

<div id="sp-app">

<style>
#sp-app *,
#sp-app *::before,
#sp-app *::after {
box-sizing: border-box;
}

#sp-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
line-height: 1.5;
max-width: 900px;
margin: 0 auto;
padding: 0 0 40px;
}

#sp-app h2 {
font-size: 1.1rem;
font-weight: 700;
margin: 0 0 12px;
color: #1a1a2e;
}

/* Layout */
#sp-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
margin-bottom: 20px;
}

@media (max-width: 640px) {
#sp-layout {
grid-template-columns: 1fr;
}
}

/* Panel */
.sp-panel {
background: #f8f9fc;
border: 1px solid #dde1ec;
border-radius: 10px;
padding: 18px;
}

/* Unit selector */
#sp-unit-bar {
display: flex;
gap: 6px;
margin-bottom: 18px;
flex-wrap: wrap;
}

#sp-unit-bar label {
font-size: 0.78rem;
font-weight: 600;
color: #555;
margin-right: 4px;
align-self: center;
}

.sp-unit-btn {
padding: 4px 12px;
border: 1px solid #c0c7d8;
border-radius: 5px;
background: #fff;
font-size: 0.82rem;
cursor: pointer;
transition: background 0.15s, color 0.15s, border-color 0.15s;
color: #444;
}

.sp-unit-btn:hover {
border-color: #6c63ff;
color: #6c63ff;
}

.sp-unit-btn.active {
background: #6c63ff;
color: #fff;
border-color: #6c63ff;
}

/* Side controls grid */
.sp-sides-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 10px;
}

.sp-side-group {
display: flex;
flex-direction: column;
gap: 4px;
}

.sp-side-group label {
font-size: 0.78rem;
font-weight: 600;
color: #666;
text-transform: uppercase;
letter-spacing: 0.04em;
}

.sp-side-row {
display: flex;
align-items: center;
gap: 6px;
}

.sp-side-row input[type="range"] {
flex: 1;
accent-color: #6c63ff;
height: 4px;
cursor: pointer;
}

.sp-side-row input[type="number"] {
width: 56px;
padding: 4px 6px;
border: 1px solid #c0c7d8;
border-radius: 5px;
font-size: 0.82rem;
text-align: right;
background: #fff;
color: #1a1a2e;
}

.sp-side-row input[type="number"]:focus {
outline: 2px solid #6c63ff;
border-color: #6c63ff;
}

/* Link toggle */
#sp-link-bar {
display: flex;
align-items: center;
gap: 8px;
margin: 12px 0;
}

#sp-link-bar label {
font-size: 0.82rem;
color: #555;
cursor: pointer;
}

.sp-toggle {
position: relative;
width: 36px;
height: 20px;
flex-shrink: 0;
}

.sp-toggle input {
opacity: 0;
width: 0;
height: 0;
position: absolute;
}

.sp-toggle-track {
position: absolute;
inset: 0;
background: #c0c7d8;
border-radius: 20px;
cursor: pointer;
transition: background 0.2s;
}

.sp-toggle input:checked + .sp-toggle-track {
background: #6c63ff;
}

.sp-toggle-track::after {
content: "";
position: absolute;
top: 2px;
left: 2px;
width: 16px;
height: 16px;
background: #fff;
border-radius: 50%;
transition: transform 0.2s;
}

.sp-toggle input:checked + .sp-toggle-track::after {
transform: translateX(16px);
}

/* Section divider */
.sp-divider {
border: none;
border-top: 1px solid #dde1ec;
margin: 14px 0;
}

/* Box model diagram */
#sp-box-diagram {
position: relative;
width: 100%;
max-width: 340px;
margin: 0 auto 16px;
aspect-ratio: 1;
user-select: none;
}

.sp-layer {
position: absolute;
display: flex;
align-items: center;
justify-content: center;
border-radius: 6px;
font-size: 0.72rem;
font-weight: 700;
letter-spacing: 0.06em;
text-transform: uppercase;
}

#sp-margin-layer {
inset: 0;
background: #fde8cc;
border: 2px dashed #e8a45a;
color: #c47a20;
}

#sp-padding-layer {
background: #cce8fd;
border: 2px solid #5aade8;
color: #1a6fad;
}

#sp-content-layer {
background: #d4f5e0;
border: 2px solid #4caf78;
color: #2a7a50;
font-size: 0.8rem;
}

.sp-layer-label {
position: absolute;
pointer-events: none;
}

#sp-margin-layer > .sp-layer-label { top: 4px; left: 8px; }
#sp-padding-layer > .sp-layer-label { top: 4px; left: 8px; }

/* Edge handles */
.sp-edge {
position: absolute;
background: transparent;
cursor: ns-resize;
display: flex;
align-items: center;
justify-content: center;
font-size: 0.65rem;
font-weight: 700;
color: rgba(0,0,0,0.45);
z-index: 10;
border-radius: 4px;
transition: background 0.12s;
}

.sp-edge:hover { background: rgba(108,99,255,0.12); }
.sp-edge.horiz { cursor: ew-resize; }

/* Presets */
#sp-presets {
display: flex;
flex-wrap: wrap;
gap: 7px;
margin-bottom: 18px;
}

.sp-preset-btn {
padding: 5px 12px;
border: 1px solid #c0c7d8;
border-radius: 6px;
background: #fff;
font-size: 0.8rem;
cursor: pointer;
color: #444;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}

.sp-preset-btn:hover {
border-color: #6c63ff;
color: #6c63ff;
}

/* Preview */
#sp-preview-wrap {
background: #e8eaf2;
border-radius: 10px;
padding: 20px;
display: flex;
align-items: center;
justify-content: center;
min-height: 140px;
overflow: auto;
}

#sp-preview-box {
background: #fff;
border: 2px dashed #aaa;
border-radius: 6px;
max-width: 100%;
}

#sp-preview-inner {
background: #6c63ff;
color: #fff;
border-radius: 4px;
font-size: 0.82rem;
font-weight: 600;
text-align: center;
white-space: nowrap;
}

/* CSS Output */
#sp-output-wrap {
margin-top: 20px;
}

#sp-output-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #dde1ec;
margin-bottom: 0;
}

.sp-tab-btn {
padding: 7px 18px;
border: none;
background: none;
font-size: 0.85rem;
font-weight: 600;
color: #888;
cursor: pointer;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
transition: color 0.15s;
}

.sp-tab-btn.active {
color: #6c63ff;
border-bottom-color: #6c63ff;
}

#sp-output-code {
background: #1a1a2e;
color: #e0e0f0;
border-radius: 0 0 10px 10px;
padding: 16px 18px;
font-family: "Fira Code", "Courier New", monospace;
font-size: 0.82rem;
line-height: 1.7;
white-space: pre;
overflow-x: auto;
min-height: 80px;
}

#sp-copy-btn {
margin-top: 10px;
padding: 8px 22px;
background: #6c63ff;
color: #fff;
border: none;
border-radius: 7px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}

#sp-copy-btn:hover { background: #574fd6; }
#sp-copy-btn:active { transform: scale(0.97); }
#sp-copy-btn.copied { background: #2ea86a; }
</style>

<!-- Presets -->
<div style="margin-bottom:18px;">
<h2>Presets</h2>
<div id="sp-presets">
<button class="sp-preset-btn" data-preset="card">Comfortable Card</button>
<button class="sp-preset-btn" data-preset="list">Tight List</button>
<button class="sp-preset-btn" data-preset="section">Section Spacing</button>
<button class="sp-preset-btn" data-preset="button">Button Padding</button>
<button class="sp-preset-btn" data-preset="input">Input Field</button>
</div>
</div>

<!-- Unit bar -->
<div id="sp-unit-bar">
<label>Unit:</label>
<button class="sp-unit-btn active" data-unit="px">px</button>
<button class="sp-unit-btn" data-unit="rem">rem</button>
<button class="sp-unit-btn" data-unit="em">em</button>
<button class="sp-unit-btn" data-unit="%">%</button>
</div>

<!-- Link toggle -->
<div id="sp-link-bar">
<label class="sp-toggle" for="sp-link-toggle">
<input type="checkbox" id="sp-link-toggle">
<span class="sp-toggle-track"></span>
</label>
<label for="sp-link-toggle">Link all sides</label>
</div>

<!-- Controls + Diagram -->
<div id="sp-layout">
<!-- Left: Margin + Padding controls -->
<div>
<div class="sp-panel">
<h2>Margin</h2>
<div class="sp-sides-grid" id="sp-margin-controls"></div>
<hr class="sp-divider">
<h2>Padding</h2>
<div class="sp-sides-grid" id="sp-padding-controls"></div>
</div>
</div>

<!-- Right: Box model diagram + preview -->
<div>
<div class="sp-panel">
<h2>Box Model</h2>
<div id="sp-box-diagram">
<!-- Layers rendered by JS -->
</div>
</div>
<div class="sp-panel" style="margin-top:14px;">
<h2>Live Preview</h2>
<div id="sp-preview-wrap">
<div id="sp-preview-box">
<div id="sp-preview-inner">Content</div>
</div>
</div>
</div>
</div>
</div>

<!-- CSS Output -->
<div id="sp-output-wrap" class="sp-panel">
<h2>CSS Output</h2>
<div id="sp-output-tabs">
<button class="sp-tab-btn active" data-tab="shorthand">Shorthand</button>
<button class="sp-tab-btn" data-tab="longhand">Longhand</button>
</div>
<pre id="sp-output-code"></pre>
<button id="sp-copy-btn">Copy CSS</button>
</div>

<script>
(function() {
// State
var state = {
unit: "px",
linked: false,
margin: { top: 16, right: 16, bottom: 16, left: 16 },
padding: { top: 12, right: 16, bottom: 12, left: 16 },
tab: "shorthand"
};

var PRESETS = {
card:    { margin: {top:0,right:0,bottom:0,left:0},    padding: {top:24,right:24,bottom:24,left:24} },
list:    { margin: {top:4,right:0,bottom:4,left:0},     padding: {top:6,right:12,bottom:6,left:12} },
section: { margin: {top:48,right:0,bottom:48,left:0},   padding: {top:32,right:24,bottom:32,left:24} },
button:  { margin: {top:0,right:8,bottom:0,left:8},     padding: {top:10,right:20,bottom:10,left:20} },
input:   { margin: {top:4,right:0,bottom:4,left:0},     padding: {top:8,right:12,bottom:8,left:12} }
};

var MAX_VAL = { px: 120, rem: 8, em: 8, "%": 20 };
var STEP    = { px: 1,   rem: 0.25, em: 0.25, "%": 0.5 };

// Helpers
function fmt(v) {
if (state.unit === "px" || state.unit === "%") return Math.round(v);
return parseFloat(v.toFixed(2));
}

function clamp(v) { return Math.max(0, Math.min(v, MAX_VAL[state.unit])); }

function val2px(v) {
if (state.unit === "px") return v;
if (state.unit === "rem" || state.unit === "em") return v * 16;
return v * 3; // rough % estimate for diagram
}

// Build side controls
function buildControls(prop, containerId) {
var container = document.getElementById(containerId);
container.innerHTML = "";
["top","right","bottom","left"].forEach(function(side) {
var group = document.createElement("div");
group.className = "sp-side-group";

var lbl = document.createElement("label");
lbl.textContent = side.charAt(0).toUpperCase() + side.slice(1);
group.appendChild(lbl);

var row = document.createElement("div");
row.className = "sp-side-row";

var range = document.createElement("input");
range.type = "range";
range.min = 0;
range.max = MAX_VAL[state.unit];
range.step = STEP[state.unit];
range.value = state[prop][side];
range.id = "sp-" + prop + "-" + side + "-range";

var num = document.createElement("input");
num.type = "number";
num.min = 0;
num.max = MAX_VAL[state.unit];
num.step = STEP[state.unit];
num.value = fmt(state[prop][side]);
num.id = "sp-" + prop + "-" + side + "-num";

function onRangeChange() {
var v = clamp(parseFloat(range.value) || 0);
setSide(prop, side, v);
}
function onNumChange() {
var v = clamp(parseFloat(num.value) || 0);
setSide(prop, side, v);
}

range.addEventListener("input", onRangeChange);
num.addEventListener("input", onNumChange);

row.appendChild(range);
row.appendChild(num);
group.appendChild(row);
container.appendChild(group);
});
}

function setSide(prop, side, v) {
if (state.linked) {
["top","right","bottom","left"].forEach(function(s) {
state[prop][s] = v;
});
// also mirror to the other prop if linked
} else {
state[prop][side] = v;
}
syncInputs(prop);
render();
}

function syncInputs(prop) {
["top","right","bottom","left"].forEach(function(side) {
var r = document.getElementById("sp-" + prop + "-" + side + "-range");
var n = document.getElementById("sp-" + prop + "-" + side + "-num");
if (r) { r.max = MAX_VAL[state.unit]; r.step = STEP[state.unit]; r.value = state[prop][side]; }
if (n) { n.max = MAX_VAL[state.unit]; n.step = STEP[state.unit]; n.value = fmt(state[prop][side]); }
});
}

// Box model diagram
function renderDiagram() {
var diagram = document.getElementById("sp-box-diagram");
var W = diagram.offsetWidth || 300;
var H = W; // square

// px values for diagram
var m = {}, p = {};
["top","right","bottom","left"].forEach(function(s) {
m[s] = Math.min(val2px(state.margin[s]), W * 0.22);
p[s] = Math.min(val2px(state.padding[s]), W * 0.18);
});

diagram.innerHTML = "";

// Margin layer
var mLayer = document.createElement("div");
mLayer.className = "sp-layer";
mLayer.id = "sp-margin-layer";
Object.assign(mLayer.style, {
top: "0", left: "0", right: "0", bottom: "0"
});
var mLbl = document.createElement("span");
mLbl.className = "sp-layer-label";
mLbl.textContent = "Margin";
mLayer.appendChild(mLbl);
diagram.appendChild(mLayer);

// Padding layer (inside margin)
var pLayer = document.createElement("div");
pLayer.className = "sp-layer";
pLayer.id = "sp-padding-layer";
Object.assign(pLayer.style, {
top: m.top + "px",
right: m.right + "px",
bottom: m.bottom + "px",
left: m.left + "px"
});
var pLbl = document.createElement("span");
pLbl.className = "sp-layer-label";
pLbl.textContent = "Padding";
pLayer.appendChild(pLbl);
diagram.appendChild(pLayer);

// Content layer (inside padding)
var cLayer = document.createElement("div");
cLayer.className = "sp-layer";
cLayer.id = "sp-content-layer";
Object.assign(cLayer.style, {
top: (m.top + p.top) + "px",
right: (m.right + p.right) + "px",
bottom: (m.bottom + p.bottom) + "px",
left: (m.left + p.left) + "px"
});
cLayer.textContent = "Content";
diagram.appendChild(cLayer);

// Edge labels
var edges = [
{ prop:"margin", side:"top",    style:{ top: "2px", left:"50%", transform:"translateX(-50%)" } },
{ prop:"margin", side:"bottom", style:{ bottom:"2px", left:"50%", transform:"translateX(-50%)" } },
{ prop:"margin", side:"left",   style:{ left:"2px", top:"50%", transform:"translateY(-50%)" } },
{ prop:"margin", side:"right",  style:{ right:"2px", top:"50%", transform:"translateY(-50%)" } },
{ prop:"padding", side:"top",    layer: pLayer, style:{ top: "2px", left:"50%", transform:"translateX(-50%)" } },
{ prop:"padding", side:"bottom", layer: pLayer, style:{ bottom:"2px", left:"50%", transform:"translateX(-50%)" } },
{ prop:"padding", side:"left",   layer: pLayer, style:{ left:"2px", top:"50%", transform:"translateY(-50%)" } },
{ prop:"padding", side:"right",  layer: pLayer, style:{ right:"2px", top:"50%", transform:"translateY(-50%)" } },
];

edges.forEach(function(e) {
var el = document.createElement("span");
el.style.position = "absolute";
el.style.fontSize = "0.62rem";
el.style.fontWeight = "700";
el.style.color = "rgba(0,0,0,0.5)";
el.style.pointerEvents = "none";
el.style.whiteSpace = "nowrap";
Object.assign(el.style, e.style);
el.textContent = fmt(state[e.prop][e.side]) + state.unit;
(e.layer || mLayer).appendChild(el);
});
}

// Preview
function renderPreview() {
var box = document.getElementById("sp-preview-box");
var inner = document.getElementById("sp-preview-inner");
function u(v) { return fmt(v) + state.unit; }
box.style.margin = u(state.margin.top) + " " + u(state.margin.right) + " " + u(state.margin.bottom) + " " + u(state.margin.left);
inner.style.padding = u(state.padding.top) + " " + u(state.padding.right) + " " + u(state.padding.bottom) + " " + u(state.padding.left);
}

// CSS output
function shorthand(prop, obj) {
function u(v) { return fmt(v) + state.unit; }
var t = u(obj.top), r = u(obj.right), b = u(obj.bottom), l = u(obj.left);
if (t===r && r===b && b===l) return prop + ": " + t + ";";
if (t===b && r===l) return prop + ": " + t + " " + r + ";";
if (r===l) return prop + ": " + t + " " + r + " " + b + ";";
return prop + ": " + t + " " + r + " " + b + " " + l + ";";
}

function longhand(prop, obj) {
function u(v) { return fmt(v) + state.unit; }
return [
prop + "-top: " + u(obj.top) + ";",
prop + "-right: " + u(obj.right) + ";",
prop + "-bottom: " + u(obj.bottom) + ";",
prop + "-left: " + u(obj.left) + ";"
].join("\n");
}

function renderOutput() {
var code = document.getElementById("sp-output-code");
if (state.tab === "shorthand") {
code.textContent = shorthand("margin", state.margin) + "\n" + shorthand("padding", state.padding);
} else {
code.textContent = longhand("margin", state.margin) + "\n" + longhand("padding", state.padding);
}
}

function render() {
renderDiagram();
renderPreview();
renderOutput();
}

// Init controls
function initControls() {
buildControls("margin", "sp-margin-controls");
buildControls("padding", "sp-padding-controls");
}

// Unit buttons
document.querySelectorAll(".sp-unit-btn").forEach(function(btn) {
btn.addEventListener("click", function() {
document.querySelectorAll(".sp-unit-btn").forEach(function(b){ b.classList.remove("active"); });
btn.classList.add("active");
state.unit = btn.dataset.unit;
// Convert values to new unit (approximate: keep logical ratios via px base)
initControls();
syncInputs("margin");
syncInputs("padding");
render();
});
});

// Link toggle
document.getElementById("sp-link-toggle").addEventListener("change", function() {
state.linked = this.checked;
});

// Presets
document.querySelectorAll(".sp-preset-btn").forEach(function(btn) {
btn.addEventListener("click", function() {
var p = PRESETS[btn.dataset.preset];
// Copy values; if unit is not px, scale down
var scale = state.unit === "px" ? 1 : state.unit === "rem" || state.unit === "em" ? 1/16 : 1/5;
["top","right","bottom","left"].forEach(function(s) {
state.margin[s] = clamp(p.margin[s] * (state.unit === "px" ? 1 : scale));
state.padding[s] = clamp(p.padding[s] * (state.unit === "px" ? 1 : scale));
});
syncInputs("margin");
syncInputs("padding");
render();
});
});

// Tab buttons
document.querySelectorAll(".sp-tab-btn").forEach(function(btn) {
btn.addEventListener("click", function() {
document.querySelectorAll(".sp-tab-btn").forEach(function(b){ b.classList.remove("active"); });
btn.classList.add("active");
state.tab = btn.dataset.tab;
renderOutput();
});
});

// Copy button
document.getElementById("sp-copy-btn").addEventListener("click", function() {
var text = document.getElementById("sp-output-code").textContent;
var btn = this;
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(function() {
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(function(){ btn.textContent = "Copy CSS"; btn.classList.remove("copied"); }, 1600);
});
} else {
var ta = document.createElement("textarea");
ta.value = text;
ta.style.position = "fixed"; ta.style.opacity = "0";
document.body.appendChild(ta);
ta.select();
document.execCommand("copy");
document.body.removeChild(ta);
btn.textContent = "Copied!";
btn.classList.add("copied");
setTimeout(function(){ btn.textContent = "Copy CSS"; btn.classList.remove("copied"); }, 1600);
}
});

// Init
initControls();
render();

// Redraw diagram on resize
var resizeTimer;
window.addEventListener("resize", function() {
clearTimeout(resizeTimer);
resizeTimer = setTimeout(renderDiagram, 120);
});
})();
</script>

</div>

---

## How to Use the CSS Spacing Generator

1. **Choose a preset** or set your own values.
2. **Select a unit** — px, rem, em, or %.
3. **Adjust margin and padding** per side using sliders or number inputs.
4. **Enable "Link all sides"** to set all four sides at once.
5. **Watch the box model diagram and live preview** update instantly.
6. **Pick Shorthand or Longhand** output, then click **Copy CSS**.

---

## Box Model Quick Reference

| Layer   | Purpose                                              |
|---------|------------------------------------------------------|
| Margin  | Space **outside** the element border                 |
| Border  | The element's border (set separately)                |
| Padding | Space **inside** the border, around the content      |
| Content | The actual content area (text, images, etc.)         |

---

## CSS Shorthand Rules

CSS uses a clockwise order: **top → right → bottom → left**.

```css
/* 1 value: all sides equal */
margin: 16px;

/* 2 values: top/bottom  left/right */
padding: 12px 24px;

/* 3 values: top  left/right  bottom */
margin: 8px 16px 24px;

/* 4 values: top right bottom left */
padding: 8px 16px 12px 16px;
```

---

## Related Tools

- [CSS Flexbox Generator](/tools/flexbox-generator/) — Build flexbox layouts visually with live output.
- [CSS Box Shadow Generator](/tools/box-shadow-generator/) — Design layered shadows with real-time preview.
- [CSS Variables Generator](/tools/css-variables-generator/) — Define and export custom property systems.
