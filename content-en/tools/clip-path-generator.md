---
title: "CSS Clip-Path Generator — Shape Builder"
date: 2025-05-16
description: "Create CSS clip-path shapes visually. Preset shapes, custom polygons, and interactive point editing. Copy clip-path CSS code with one click."
categories: ["Free Tools"]
slug: "clip-path-generator"
ShowToc: false
aliases:
  - "/tools/clip-path-generator/"
  - "/tools/clip-path-generator/"
cover:
  image: "/images/covers/clip-path-generator.png"
  alt: "CSS Clip-Path Generator"
---

<div id="cp-app">

<style>
#cp-app *,
#cp-app *::before,
#cp-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#cp-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1a1a2e;
max-width: 960px;
margin: 0 auto;
padding: 0 0 2rem 0;
}
#cp-app h2 {
font-size: 1.1rem;
font-weight: 700;
margin-bottom: 0.75rem;
color: #16213e;
}
#cp-app .cp-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1.5rem;
align-items: start;
}
@media (max-width: 700px) {
#cp-app .cp-layout {
grid-template-columns: 1fr;
}
}
/* Controls panel */
#cp-app .cp-controls {
background: #f8f9fc;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 1.25rem;
display: flex;
flex-direction: column;
gap: 1.1rem;
}
#cp-app .cp-section-label {
font-size: 0.72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #718096;
margin-bottom: 0.45rem;
}
/* Shape type tabs */
#cp-app .cp-shape-tabs {
display: flex;
gap: 0.4rem;
flex-wrap: wrap;
}
#cp-app .cp-tab {
padding: 0.35rem 0.75rem;
border-radius: 20px;
border: 1.5px solid #cbd5e0;
background: #fff;
font-size: 0.82rem;
cursor: pointer;
transition: all 0.15s;
color: #4a5568;
font-weight: 500;
}
#cp-app .cp-tab:hover {
border-color: #667eea;
color: #667eea;
}
#cp-app .cp-tab.active {
background: #667eea;
border-color: #667eea;
color: #fff;
}
/* Preset grid */
#cp-app .cp-presets-grid {
display: grid;
grid-template-columns: repeat(5, 1fr);
gap: 0.5rem;
}
@media (max-width: 400px) {
#cp-app .cp-presets-grid {
grid-template-columns: repeat(3, 1fr);
}
}
#cp-app .cp-preset-btn {
display: flex;
flex-direction: column;
align-items: center;
gap: 0.3rem;
padding: 0.5rem 0.25rem;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
background: #fff;
cursor: pointer;
transition: all 0.15s;
font-size: 0.7rem;
color: #4a5568;
font-weight: 500;
}
#cp-app .cp-preset-btn:hover {
border-color: #667eea;
color: #667eea;
background: #f0f4ff;
}
#cp-app .cp-preset-btn.active {
border-color: #667eea;
background: #eef1ff;
color: #667eea;
}
#cp-app .cp-preset-icon {
width: 32px;
height: 32px;
display: block;
}
/* Sliders */
#cp-app .cp-slider-row {
display: flex;
align-items: center;
gap: 0.6rem;
margin-bottom: 0.4rem;
}
#cp-app .cp-slider-row label {
font-size: 0.8rem;
color: #4a5568;
min-width: 80px;
flex-shrink: 0;
}
#cp-app .cp-slider-row input[type=range] {
flex: 1;
accent-color: #667eea;
height: 4px;
cursor: pointer;
}
#cp-app .cp-slider-val {
font-size: 0.78rem;
color: #667eea;
font-weight: 700;
min-width: 38px;
text-align: right;
}
/* Color picker */
#cp-app .cp-color-row {
display: flex;
align-items: center;
gap: 0.7rem;
}
#cp-app .cp-color-row label {
font-size: 0.8rem;
color: #4a5568;
}
#cp-app .cp-color-row input[type=color] {
width: 38px;
height: 32px;
border: none;
border-radius: 6px;
cursor: pointer;
padding: 2px;
background: #fff;
border: 1px solid #e2e8f0;
}
/* Custom polygon controls */
#cp-app .cp-custom-hint {
font-size: 0.78rem;
color: #718096;
background: #fff9db;
border: 1px solid #f6e05e;
border-radius: 8px;
padding: 0.55rem 0.75rem;
line-height: 1.5;
}
#cp-app .cp-custom-actions {
display: flex;
gap: 0.5rem;
flex-wrap: wrap;
}
#cp-app .cp-btn {
padding: 0.42rem 0.9rem;
border-radius: 8px;
border: 1.5px solid #667eea;
background: #667eea;
color: #fff;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
}
#cp-app .cp-btn:hover {
background: #5a67d8;
border-color: #5a67d8;
}
#cp-app .cp-btn-outline {
background: #fff;
color: #667eea;
}
#cp-app .cp-btn-outline:hover {
background: #eef1ff;
}
#cp-app .cp-btn-danger {
background: #fff;
border-color: #fc8181;
color: #e53e3e;
}
#cp-app .cp-btn-danger:hover {
background: #fff5f5;
}
/* Inset controls */
#cp-app .cp-inset-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 0.4rem 0.8rem;
}
/* Right panel: preview + output */
#cp-app .cp-right {
display: flex;
flex-direction: column;
gap: 1.25rem;
}
/* Preview box */
#cp-app .cp-preview-wrap {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 1.25rem;
}
#cp-app .cp-preview-label {
font-size: 0.72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #718096;
margin-bottom: 0.75rem;
}
#cp-app .cp-canvas-wrap {
position: relative;
width: 100%;
padding-bottom: 70%;
background: repeating-conic-gradient(#f0f0f0 0% 25%, #fff 0% 50%) 0 0 / 18px 18px;
border-radius: 8px;
overflow: hidden;
cursor: crosshair;
}
#cp-app .cp-shape-el {
position: absolute;
inset: 0;
background: #667eea;
transition: clip-path 0.1s;
}
#cp-app .cp-point-dot {
position: absolute;
width: 14px;
height: 14px;
border-radius: 50%;
background: #fff;
border: 2.5px solid #e53e3e;
transform: translate(-50%, -50%);
cursor: grab;
z-index: 10;
touch-action: none;
}
#cp-app .cp-point-dot:hover {
background: #fff5f5;
border-color: #c53030;
}
/* Output box */
#cp-app .cp-output-wrap {
background: #1a1a2e;
border-radius: 12px;
padding: 1.1rem 1.25rem;
}
#cp-app .cp-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 0.6rem;
}
#cp-app .cp-output-title {
font-size: 0.72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #a0aec0;
}
#cp-app .cp-copy-btn {
padding: 0.3rem 0.8rem;
border-radius: 20px;
border: 1.5px solid #4a5568;
background: transparent;
color: #a0aec0;
font-size: 0.75rem;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#cp-app .cp-copy-btn:hover {
border-color: #667eea;
color: #667eea;
}
#cp-app .cp-copy-btn.copied {
border-color: #48bb78;
color: #48bb78;
}
#cp-app .cp-output-code {
font-family: "Fira Mono", "Cascadia Code", "Consolas", monospace;
font-size: 0.82rem;
color: #90cdf4;
line-height: 1.7;
word-break: break-all;
white-space: pre-wrap;
}
#cp-app .cp-output-code .cp-prop {
color: #f6ad55;
}
#cp-app .cp-output-code .cp-val {
color: #68d391;
}
/* Points list */
#cp-app .cp-points-list {
font-size: 0.75rem;
color: #718096;
background: #f8f9fc;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 0.6rem 0.75rem;
max-height: 90px;
overflow-y: auto;
line-height: 1.7;
font-family: monospace;
}
</style>

<div class="cp-layout">

<!-- LEFT: Controls -->
<div class="cp-controls">

<!-- Shape Type -->
<div>
<div class="cp-section-label">Shape Type</div>
<div class="cp-shape-tabs">
<button class="cp-tab active" data-type="polygon" onclick="cpSetType('polygon')">Polygon</button>
<button class="cp-tab" data-type="circle" onclick="cpSetType('circle')">Circle</button>
<button class="cp-tab" data-type="ellipse" onclick="cpSetType('ellipse')">Ellipse</button>
<button class="cp-tab" data-type="inset" onclick="cpSetType('inset')">Inset</button>
<button class="cp-tab" data-type="custom" onclick="cpSetType('custom')">Custom</button>
</div>
</div>

<!-- Polygon Presets (shown when type=polygon) -->
<div id="cp-polygon-panel">
<div class="cp-section-label">Preset Shapes</div>
<div class="cp-presets-grid">
<button class="cp-preset-btn active" data-preset="triangle" onclick="cpLoadPreset('triangle')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,4 30,28 2,28" fill="#667eea"/></svg>
Triangle
</button>
<button class="cp-preset-btn" data-preset="diamond" onclick="cpLoadPreset('diamond')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 30,16 16,30 2,16" fill="#667eea"/></svg>
Diamond
</button>
<button class="cp-preset-btn" data-preset="pentagon" onclick="cpLoadPreset('pentagon')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 29,11 24,27 8,27 3,11" fill="#667eea"/></svg>
Pentagon
</button>
<button class="cp-preset-btn" data-preset="hexagon" onclick="cpLoadPreset('hexagon')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 28,9 28,23 16,30 4,23 4,9" fill="#667eea"/></svg>
Hexagon
</button>
<button class="cp-preset-btn" data-preset="octagon" onclick="cpLoadPreset('octagon')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="10,2 22,2 30,10 30,22 22,30 10,30 2,22 2,10" fill="#667eea"/></svg>
Octagon
</button>
<button class="cp-preset-btn" data-preset="star" onclick="cpLoadPreset('star')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="16,2 19.5,12 30,12 21.5,18.5 24.5,29 16,22.5 7.5,29 10.5,18.5 2,12 12.5,12" fill="#667eea"/></svg>
Star
</button>
<button class="cp-preset-btn" data-preset="arrow" onclick="cpLoadPreset('arrow')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="2,10 18,10 18,4 30,16 18,28 18,22 2,22" fill="#667eea"/></svg>
Arrow
</button>
<button class="cp-preset-btn" data-preset="cross" onclick="cpLoadPreset('cross')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="10,2 22,2 22,10 30,10 30,22 22,22 22,30 10,30 10,22 2,22 2,10 10,10" fill="#667eea"/></svg>
Cross
</button>
<button class="cp-preset-btn" data-preset="heart" onclick="cpLoadPreset('heart')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><path d="M16,28 C16,28 3,18 3,10 C3,6 6,3 10,3 C12.5,3 15,5 16,7 C17,5 19.5,3 22,3 C26,3 29,6 29,10 C29,18 16,28 16,28Z" fill="#667eea"/></svg>
Heart
</button>
<button class="cp-preset-btn" data-preset="chevron" onclick="cpLoadPreset('chevron')">
<svg class="cp-preset-icon" viewBox="0 0 32 32"><polygon points="2,6 18,6 30,16 18,26 2,26 14,16" fill="#667eea"/></svg>
Chevron
</button>
</div>
</div>

<!-- Circle controls -->
<div id="cp-circle-panel" style="display:none">
<div class="cp-section-label">Circle Settings</div>
<div class="cp-slider-row">
<label>Radius</label>
<input type="range" id="cp-circle-r" min="10" max="50" value="50" oninput="cpUpdateCircle()">
<span class="cp-slider-val" id="cp-circle-r-val">50%</span>
</div>
<div class="cp-slider-row">
<label>Center X</label>
<input type="range" id="cp-circle-cx" min="0" max="100" value="50" oninput="cpUpdateCircle()">
<span class="cp-slider-val" id="cp-circle-cx-val">50%</span>
</div>
<div class="cp-slider-row">
<label>Center Y</label>
<input type="range" id="cp-circle-cy" min="0" max="100" value="50" oninput="cpUpdateCircle()">
<span class="cp-slider-val" id="cp-circle-cy-val">50%</span>
</div>
</div>

<!-- Ellipse controls -->
<div id="cp-ellipse-panel" style="display:none">
<div class="cp-section-label">Ellipse Settings</div>
<div class="cp-slider-row">
<label>Radius X</label>
<input type="range" id="cp-ellipse-rx" min="5" max="50" value="50" oninput="cpUpdateEllipse()">
<span class="cp-slider-val" id="cp-ellipse-rx-val">50%</span>
</div>
<div class="cp-slider-row">
<label>Radius Y</label>
<input type="range" id="cp-ellipse-ry" min="5" max="50" value="30" oninput="cpUpdateEllipse()">
<span class="cp-slider-val" id="cp-ellipse-ry-val">30%</span>
</div>
<div class="cp-slider-row">
<label>Center X</label>
<input type="range" id="cp-ellipse-cx" min="0" max="100" value="50" oninput="cpUpdateEllipse()">
<span class="cp-slider-val" id="cp-ellipse-cx-val">50%</span>
</div>
<div class="cp-slider-row">
<label>Center Y</label>
<input type="range" id="cp-ellipse-cy" min="0" max="100" value="50" oninput="cpUpdateEllipse()">
<span class="cp-slider-val" id="cp-ellipse-cy-val">50%</span>
</div>
</div>

<!-- Inset controls -->
<div id="cp-inset-panel" style="display:none">
<div class="cp-section-label">Inset Settings</div>
<div class="cp-inset-grid">
<div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
<label>Top</label>
<input type="range" id="cp-inset-t" min="0" max="49" value="10" oninput="cpUpdateInset()">
<span class="cp-slider-val" id="cp-inset-t-val" style="min-width:auto">10%</span>
</div>
<div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
<label>Right</label>
<input type="range" id="cp-inset-r" min="0" max="49" value="10" oninput="cpUpdateInset()">
<span class="cp-slider-val" id="cp-inset-r-val" style="min-width:auto">10%</span>
</div>
<div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
<label>Bottom</label>
<input type="range" id="cp-inset-b" min="0" max="49" value="10" oninput="cpUpdateInset()">
<span class="cp-slider-val" id="cp-inset-b-val" style="min-width:auto">10%</span>
</div>
<div class="cp-slider-row" style="flex-direction:column;align-items:flex-start;gap:0.2rem">
<label>Left</label>
<input type="range" id="cp-inset-l" min="0" max="49" value="10" oninput="cpUpdateInset()">
<span class="cp-slider-val" id="cp-inset-l-val" style="min-width:auto">10%</span>
</div>
</div>
<div class="cp-slider-row" style="margin-top:0.5rem">
<label>Border Radius</label>
<input type="range" id="cp-inset-br" min="0" max="50" value="0" oninput="cpUpdateInset()">
<span class="cp-slider-val" id="cp-inset-br-val">0%</span>
</div>
</div>

<!-- Custom polygon panel -->
<div id="cp-custom-panel" style="display:none">
<div class="cp-section-label">Custom Polygon</div>
<div class="cp-custom-hint">
Click on the preview area to add points. Drag points to move them. Right-click a point to delete it.
</div>
<div class="cp-custom-actions" style="margin-top:0.6rem">
<button class="cp-btn cp-btn-outline" onclick="cpUndoPoint()">Undo</button>
<button class="cp-btn cp-btn-danger" onclick="cpClearPoints()">Clear All</button>
</div>
<div class="cp-points-list" id="cp-points-list">No points yet — click preview to start.</div>
</div>

<!-- Background color -->
<div>
<div class="cp-section-label">Preview Options</div>
<div class="cp-color-row">
<label>Shape Color</label>
<input type="color" id="cp-shape-color" value="#667eea" oninput="cpUpdateColor()">
</div>
</div>

</div><!-- /cp-controls -->

<!-- RIGHT: Preview + Output -->
<div class="cp-right">

<div class="cp-preview-wrap">
<div class="cp-preview-label">Live Preview — <span id="cp-preview-size-label"></span></div>
<div class="cp-canvas-wrap" id="cp-canvas" onclick="cpCanvasClick(event)">
<div class="cp-shape-el" id="cp-shape"></div>
</div>
</div>

<div class="cp-output-wrap">
<div class="cp-output-header">
<span class="cp-output-title">CSS Output</span>
<button class="cp-copy-btn" id="cp-copy-btn" onclick="cpCopyCSS()">Copy</button>
</div>
<div class="cp-output-code" id="cp-output-code"></div>
</div>

</div><!-- /cp-right -->

</div><!-- /cp-layout -->

</div><!-- /cp-app -->

<script>
(function() {
// ── State ──────────────────────────────────────────────────────────────────
var cpState = {
type: 'polygon',
preset: 'triangle',
clipPath: '',
customPoints: [],
draggingIdx: -1,
dragOffX: 0,
dragOffY: 0,
};

// ── Preset definitions (% values) ─────────────────────────────────────────
var PRESETS = {
triangle:  [[50,0],[100,100],[0,100]],
diamond:   [[50,0],[100,50],[50,100],[0,50]],
pentagon:  [[50,0],[100,38],[82,100],[18,100],[0,38]],
hexagon:   [[50,0],[100,25],[100,75],[50,100],[0,75],[0,25]],
octagon:   [[30,0],[70,0],[100,30],[100,70],[70,100],[30,100],[0,70],[0,30]],
star:      [[50,0],[61,35],[98,35],[68,57],[79,91],[50,70],[21,91],[32,57],[2,35],[39,35]],
arrow:     [[0,35],[60,35],[60,10],[100,50],[60,90],[60,65],[0,65]],
cross:     [[35,0],[65,0],[65,35],[100,35],[100,65],[65,65],[65,100],[35,100],[35,65],[0,65],[0,35],[35,35]],
heart:     [[50,75],[15,45],[5,30],[5,20],[15,10],[25,10],[35,15],[50,30],[65,15],[75,10],[85,10],[95,20],[95,30],[85,45]],
chevron:   [[0,20],[65,20],[100,50],[65,80],[0,80],[35,50]],
};

// ── Init ───────────────────────────────────────────────────────────────────
function init() {
updateSizeLabel();
cpLoadPreset('triangle');
window.addEventListener('resize', updateSizeLabel);

// Drag support
var canvas = document.getElementById('cp-canvas');
canvas.addEventListener('mousemove', onMouseMove);
canvas.addEventListener('mouseup', onMouseUp);
canvas.addEventListener('mouseleave', onMouseUp);
canvas.addEventListener('touchmove', onTouchMove, {passive: false});
canvas.addEventListener('touchend', onTouchEnd);
}

function updateSizeLabel() {
var canvas = document.getElementById('cp-canvas');
var rect = canvas.getBoundingClientRect();
document.getElementById('cp-preview-size-label').textContent =
Math.round(rect.width) + ' × ' + Math.round(rect.height) + 'px';
}

// ── Type switching ─────────────────────────────────────────────────────────
window.cpSetType = function(type) {
cpState.type = type;
document.querySelectorAll('#cp-app .cp-tab').forEach(function(t) {
t.classList.toggle('active', t.dataset.type === type);
});
document.getElementById('cp-polygon-panel').style.display  = type === 'polygon'  ? '' : 'none';
document.getElementById('cp-circle-panel').style.display   = type === 'circle'   ? '' : 'none';
document.getElementById('cp-ellipse-panel').style.display  = type === 'ellipse'  ? '' : 'none';
document.getElementById('cp-inset-panel').style.display    = type === 'inset'    ? '' : 'none';
document.getElementById('cp-custom-panel').style.display   = type === 'custom'   ? '' : 'none';
clearDots();
if (type === 'polygon') { cpLoadPreset(cpState.preset); }
else if (type === 'circle')  { cpUpdateCircle(); }
else if (type === 'ellipse') { cpUpdateEllipse(); }
else if (type === 'inset')   { cpUpdateInset(); }
else if (type === 'custom')  { renderCustomPoints(); applyClipPath(buildPolygonCSS(cpState.customPoints)); }
};

// ── Presets ────────────────────────────────────────────────────────────────
window.cpLoadPreset = function(name) {
cpState.preset = name;
document.querySelectorAll('#cp-app .cp-preset-btn').forEach(function(b) {
b.classList.toggle('active', b.dataset.preset === name);
});
clearDots();
var pts = PRESETS[name];
applyClipPath(buildPolygonCSS(pts));
};

function buildPolygonCSS(pts) {
if (!pts || pts.length < 3) return 'none';
var pairs = pts.map(function(p) { return p[0] + '% ' + p[1] + '%'; });
return 'polygon(' + pairs.join(', ') + ')';
}

// ── Circle ─────────────────────────────────────────────────────────────────
window.cpUpdateCircle = function() {
var r  = document.getElementById('cp-circle-r').value;
var cx = document.getElementById('cp-circle-cx').value;
var cy = document.getElementById('cp-circle-cy').value;
document.getElementById('cp-circle-r-val').textContent  = r + '%';
document.getElementById('cp-circle-cx-val').textContent = cx + '%';
document.getElementById('cp-circle-cy-val').textContent = cy + '%';
applyClipPath('circle(' + r + '% at ' + cx + '% ' + cy + '%)');
};

// ── Ellipse ────────────────────────────────────────────────────────────────
window.cpUpdateEllipse = function() {
var rx = document.getElementById('cp-ellipse-rx').value;
var ry = document.getElementById('cp-ellipse-ry').value;
var cx = document.getElementById('cp-ellipse-cx').value;
var cy = document.getElementById('cp-ellipse-cy').value;
document.getElementById('cp-ellipse-rx-val').textContent = rx + '%';
document.getElementById('cp-ellipse-ry-val').textContent = ry + '%';
document.getElementById('cp-ellipse-cx-val').textContent = cx + '%';
document.getElementById('cp-ellipse-cy-val').textContent = cy + '%';
applyClipPath('ellipse(' + rx + '% ' + ry + '% at ' + cx + '% ' + cy + '%)');
};

// ── Inset ──────────────────────────────────────────────────────────────────
window.cpUpdateInset = function() {
var t  = document.getElementById('cp-inset-t').value;
var r  = document.getElementById('cp-inset-r').value;
var b  = document.getElementById('cp-inset-b').value;
var l  = document.getElementById('cp-inset-l').value;
var br = document.getElementById('cp-inset-br').value;
document.getElementById('cp-inset-t-val').textContent  = t + '%';
document.getElementById('cp-inset-r-val').textContent  = r + '%';
document.getElementById('cp-inset-b-val').textContent  = b + '%';
document.getElementById('cp-inset-l-val').textContent  = l + '%';
document.getElementById('cp-inset-br-val').textContent = br + '%';
var val = 'inset(' + t + '% ' + r + '% ' + b + '% ' + l + '%';
if (parseInt(br) > 0) val += ' round ' + br + '%';
val += ')';
applyClipPath(val);
};

// ── Custom polygon ─────────────────────────────────────────────────────────
window.cpCanvasClick = function(e) {
if (cpState.type !== 'custom') return;
if (cpState.draggingIdx >= 0) return;
var pos = getCanvasPos(e);
cpState.customPoints.push([Math.round(pos.x), Math.round(pos.y)]);
renderCustomPoints();
applyClipPath(buildPolygonCSS(cpState.customPoints));
};

window.cpUndoPoint = function() {
if (cpState.customPoints.length > 0) {
cpState.customPoints.pop();
renderCustomPoints();
applyClipPath(buildPolygonCSS(cpState.customPoints));
}
};

window.cpClearPoints = function() {
cpState.customPoints = [];
renderCustomPoints();
applyClipPath('none');
};

function getCanvasPos(e) {
var canvas = document.getElementById('cp-canvas');
var rect = canvas.getBoundingClientRect();
var clientX = e.clientX !== undefined ? e.clientX : e.touches[0].clientX;
var clientY = e.clientY !== undefined ? e.clientY : e.touches[0].clientY;
return {
x: Math.min(100, Math.max(0, ((clientX - rect.left) / rect.width) * 100)),
y: Math.min(100, Math.max(0, ((clientY - rect.top)  / rect.height) * 100))
};
}

function renderCustomPoints() {
clearDots();
var canvas = document.getElementById('cp-canvas');
cpState.customPoints.forEach(function(pt, idx) {
var dot = document.createElement('div');
dot.className = 'cp-point-dot';
dot.style.left = pt[0] + '%';
dot.style.top  = pt[1] + '%';
dot.dataset.idx = idx;
dot.addEventListener('mousedown', function(e) { e.stopPropagation(); startDrag(idx, e); });
dot.addEventListener('touchstart', function(e) { e.stopPropagation(); startDragTouch(idx, e); }, {passive: false});
dot.addEventListener('contextmenu', function(e) {
e.preventDefault();
cpState.customPoints.splice(idx, 1);
renderCustomPoints();
applyClipPath(buildPolygonCSS(cpState.customPoints));
});
canvas.appendChild(dot);
});
// Points list
var list = document.getElementById('cp-points-list');
if (cpState.customPoints.length === 0) {
list.textContent = 'No points yet — click preview to start.';
} else {
list.textContent = cpState.customPoints.map(function(p, i) {
return 'P' + (i+1) + ': ' + p[0] + '% ' + p[1] + '%';
}).join('   ');
}
}

function clearDots() {
document.querySelectorAll('#cp-canvas .cp-point-dot').forEach(function(d) { d.remove(); });
}

function startDrag(idx, e) {
cpState.draggingIdx = idx;
e.preventDefault();
}
function startDragTouch(idx, e) {
cpState.draggingIdx = idx;
e.preventDefault();
}
function onMouseMove(e) {
if (cpState.draggingIdx < 0) return;
var pos = getCanvasPos(e);
cpState.customPoints[cpState.draggingIdx] = [Math.round(pos.x), Math.round(pos.y)];
renderCustomPoints();
applyClipPath(buildPolygonCSS(cpState.customPoints));
}
function onMouseUp() { cpState.draggingIdx = -1; }
function onTouchMove(e) {
if (cpState.draggingIdx < 0) return;
e.preventDefault();
var pos = getCanvasPos(e);
cpState.customPoints[cpState.draggingIdx] = [Math.round(pos.x), Math.round(pos.y)];
renderCustomPoints();
applyClipPath(buildPolygonCSS(cpState.customPoints));
}
function onTouchEnd() { cpState.draggingIdx = -1; }

// ── Color ──────────────────────────────────────────────────────────────────
window.cpUpdateColor = function() {
var color = document.getElementById('cp-shape-color').value;
document.getElementById('cp-shape').style.background = color;
};

// ── Apply clip-path ────────────────────────────────────────────────────────
function applyClipPath(val) {
cpState.clipPath = val;
var shape = document.getElementById('cp-shape');
shape.style.clipPath = val;
renderOutput(val);
}

function renderOutput(val) {
var code = document.getElementById('cp-output-code');
code.innerHTML =
'<span class="cp-prop">.your-element</span> {\n' +
'  <span class="cp-prop">clip-path</span>: <span class="cp-val">' + escHtml(val) + '</span>;\n' +
'  <span class="cp-prop">-webkit-clip-path</span>: <span class="cp-val">' + escHtml(val) + '</span>;\n' +
'}';
}

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

// ── Copy ───────────────────────────────────────────────────────────────────
window.cpCopyCSS = function() {
var text = '.your-element {\n  clip-path: ' + cpState.clipPath + ';\n  -webkit-clip-path: ' + cpState.clipPath + ';\n}';
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(flashCopied);
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
ta.remove();
flashCopied();
}
};

function flashCopied() {
var btn = document.getElementById('cp-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 1800);
}

// ── Boot ───────────────────────────────────────────────────────────────────
if (document.readyState === 'loading') {
document.addEventListener('DOMContentLoaded', init);
} else {
init();
}
})();
</script>

---

### Related Tools
> Generate box shadows → [CSS Box Shadow Generator](/tools/box-shadow-generator/)
> Build border radius → [CSS Border Radius Generator](/tools/border-radius-generator/)
> Create SVG paths → [SVG Path Editor](/tools/svg-path-editor/)
