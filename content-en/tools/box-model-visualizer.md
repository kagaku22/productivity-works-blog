---
title: "CSS Box Model Visualizer"
slug: "box-model-visualizer"
date: 2025-05-16
description: "Free CSS box model visualizer. See margin, border, padding, and content areas interactively — adjust values and copy CSS for your layouts."
categories: ["Free Tools"]
tags: ["css", "box model", "web design", "developer tools", "layout"]
ShowToc: false
cover:
  image: "/images/covers/box-model-visualizer.png"
  alt: "CSS Box Model Visualizer — interactive margin, border, padding, and content diagram"
---

Adjust margin, border, padding, and content dimensions in real time. The diagram updates instantly — just like Chrome DevTools — and the ready-to-copy CSS output updates alongside it.

<div id="bm-app">
<style>
#bm-app *,
#bm-app *::before,
#bm-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#bm-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 14px;
color: #1a1a2e;
background: #f5f7ff;
border-radius: 12px;
padding: 24px;
max-width: 960px;
margin: 0 auto;
}

/* ── Layout ─────────────────────────────────────────────── */
#bm-app .bm-layout {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 24px;
}
@media (max-width: 700px) {
#bm-app .bm-layout { grid-template-columns: 1fr; }
}

/* ── Controls panel ──────────────────────────────────────── */
#bm-app .bm-controls {
background: #fff;
border-radius: 10px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,.07);
display: flex;
flex-direction: column;
gap: 16px;
}

#bm-app .bm-controls h2 {
font-size: 15px;
font-weight: 700;
color: #333;
border-bottom: 2px solid #eee;
padding-bottom: 8px;
}

/* presets */
#bm-app .bm-presets {
display: flex;
flex-wrap: wrap;
gap: 6px;
}
#bm-app .bm-preset-btn {
padding: 5px 12px;
border: 1.5px solid #d0d5e8;
border-radius: 20px;
background: #f0f2ff;
color: #3a3a6e;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: background .15s, border-color .15s;
}
#bm-app .bm-preset-btn:hover,
#bm-app .bm-preset-btn.active {
background: #4c6ef5;
border-color: #4c6ef5;
color: #fff;
}

/* box-sizing toggle */
#bm-app .bm-sizing-toggle {
display: flex;
align-items: center;
gap: 10px;
font-size: 13px;
font-weight: 600;
color: #444;
}
#bm-app .bm-sizing-toggle label {
display: flex;
align-items: center;
gap: 6px;
cursor: pointer;
}
#bm-app input[type="radio"] { accent-color: #4c6ef5; cursor: pointer; }

/* section headers */
#bm-app .bm-section-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 8px;
}
#bm-app .bm-section-label {
font-size: 12px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .06em;
padding: 2px 8px;
border-radius: 4px;
}
#bm-app .bm-label-margin  { background: #ffe8cc; color: #a05a00; }
#bm-app .bm-label-border  { background: #fff3cc; color: #856500; }
#bm-app .bm-label-padding { background: #d4f5dc; color: #1a6b35; }
#bm-app .bm-label-content { background: #cce5ff; color: #004085; }

#bm-app .bm-link-toggle {
display: flex;
align-items: center;
gap: 5px;
font-size: 11px;
color: #666;
cursor: pointer;
user-select: none;
}
#bm-app .bm-link-toggle input { accent-color: #4c6ef5; cursor: pointer; }

/* 4-side grid */
#bm-app .bm-four-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
margin-bottom: 12px;
}
#bm-app .bm-four-grid label {
display: flex;
flex-direction: column;
gap: 3px;
font-size: 11px;
color: #555;
font-weight: 600;
}
#bm-app .bm-four-grid input[type="number"] {
width: 100%;
padding: 5px 8px;
border: 1.5px solid #dde2f0;
border-radius: 6px;
font-size: 13px;
color: #1a1a2e;
background: #fafbff;
transition: border-color .15s;
}
#bm-app .bm-four-grid input[type="number"]:focus {
outline: none;
border-color: #4c6ef5;
}

/* border style */
#bm-app .bm-border-style-row {
margin-bottom: 12px;
}
#bm-app .bm-border-style-row label {
font-size: 11px;
color: #555;
font-weight: 600;
display: block;
margin-bottom: 4px;
}
#bm-app select {
padding: 5px 8px;
border: 1.5px solid #dde2f0;
border-radius: 6px;
font-size: 13px;
background: #fafbff;
color: #1a1a2e;
cursor: pointer;
}
#bm-app select:focus { outline: none; border-color: #4c6ef5; }

/* ── Diagram panel ───────────────────────────────────────── */
#bm-app .bm-diagram-panel {
background: #fff;
border-radius: 10px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,.07);
display: flex;
flex-direction: column;
gap: 16px;
}
#bm-app .bm-diagram-panel h2 {
font-size: 15px;
font-weight: 700;
color: #333;
border-bottom: 2px solid #eee;
padding-bottom: 8px;
}

#bm-app .bm-diagram-wrap {
display: flex;
align-items: center;
justify-content: center;
min-height: 260px;
}

/* The nested box layers */
#bm-app .bm-layer {
display: flex;
align-items: center;
justify-content: center;
position: relative;
font-size: 10px;
font-weight: 700;
color: rgba(0,0,0,.5);
}
#bm-app .bm-layer-label {
position: absolute;
top: 4px;
left: 6px;
font-size: 9px;
font-weight: 700;
letter-spacing: .04em;
text-transform: uppercase;
opacity: .7;
}
#bm-app #bm-margin-layer  { background: #ffb347; }
#bm-app #bm-border-layer  { background: #ffd700; }
#bm-app #bm-padding-layer { background: #90ee90; }
#bm-app #bm-content-layer {
background: #6ec6ff;
font-size: 12px;
font-weight: 700;
color: #004085;
flex-direction: column;
gap: 4px;
}
#bm-app .bm-size-label { font-size: 11px; font-weight: 700; color: #004085; }

/* Computed totals */
#bm-app .bm-totals {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
}
#bm-app .bm-total-box {
background: #f0f2ff;
border: 1.5px solid #d0d5e8;
border-radius: 8px;
padding: 10px 14px;
text-align: center;
}
#bm-app .bm-total-box .bm-total-val {
font-size: 20px;
font-weight: 800;
color: #4c6ef5;
}
#bm-app .bm-total-box .bm-total-lbl {
font-size: 11px;
color: #666;
margin-top: 2px;
}

/* ── CSS Output ──────────────────────────────────────────── */
#bm-app .bm-output {
background: #fff;
border-radius: 10px;
padding: 20px;
box-shadow: 0 2px 8px rgba(0,0,0,.07);
margin-top: 0;
}
#bm-app .bm-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 12px;
}
#bm-app .bm-output h2 {
font-size: 15px;
font-weight: 700;
color: #333;
}
#bm-app .bm-copy-btn {
padding: 7px 18px;
background: #4c6ef5;
color: #fff;
border: none;
border-radius: 20px;
font-size: 13px;
font-weight: 700;
cursor: pointer;
transition: background .15s, transform .1s;
}
#bm-app .bm-copy-btn:hover  { background: #3b5bdb; }
#bm-app .bm-copy-btn:active { transform: scale(.97); }
#bm-app .bm-copy-btn.copied { background: #2f9e44; }

#bm-app .bm-css-block {
background: #1e1e2e;
color: #cdd6f4;
border-radius: 8px;
padding: 16px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 13px;
line-height: 1.7;
white-space: pre;
overflow-x: auto;
}
#bm-app .bm-css-prop  { color: #89b4fa; }
#bm-app .bm-css-val   { color: #a6e3a1; }
#bm-app .bm-css-punct { color: #cba6f7; }
</style>

<div class="bm-layout">

<!-- LEFT: Controls -->
<div class="bm-controls">
<h2>Settings</h2>

<!-- Presets -->
<div>
<div class="bm-section-header">
<span class="bm-section-label" style="background:#e8eaff;color:#3a3a6e;">Presets</span>
</div>
<div class="bm-presets">
<button class="bm-preset-btn active" onclick="bmApplyPreset('card',this)">Card</button>
<button class="bm-preset-btn" onclick="bmApplyPreset('button',this)">Button</button>
<button class="bm-preset-btn" onclick="bmApplyPreset('input',this)">Input</button>
<button class="bm-preset-btn" onclick="bmApplyPreset('container',this)">Container</button>
<button class="bm-preset-btn" onclick="bmApplyPreset('reset',this)">Reset</button>
</div>
</div>

<!-- Box-sizing -->
<div>
<div class="bm-section-header">
<span class="bm-section-label" style="background:#e8eaff;color:#3a3a6e;">box-sizing</span>
</div>
<div class="bm-sizing-toggle">
<label><input type="radio" name="bm-sizing" value="content-box" onchange="bmUpdate()"> content-box</label>
<label><input type="radio" name="bm-sizing" value="border-box" onchange="bmUpdate()" checked> border-box</label>
</div>
</div>

<!-- Content -->
<div>
<div class="bm-section-header">
<span class="bm-section-label bm-label-content">Content</span>
</div>
<div class="bm-four-grid">
<label>Width<input type="number" id="bm-cw" value="200" min="20" max="800" oninput="bmUpdate()"></label>
<label>Height<input type="number" id="bm-ch" value="100" min="20" max="800" oninput="bmUpdate()"></label>
</div>
</div>

<!-- Padding -->
<div>
<div class="bm-section-header">
<span class="bm-section-label bm-label-padding">Padding</span>
<label class="bm-link-toggle"><input type="checkbox" id="bm-link-padding" checked onchange="bmLinkChanged('padding')"> Link sides</label>
</div>
<div class="bm-four-grid">
<label>Top<input type="number" id="bm-pt" value="16" min="0" max="200" oninput="bmSideInput('padding','t')"></label>
<label>Right<input type="number" id="bm-pr" value="16" min="0" max="200" oninput="bmSideInput('padding','r')"></label>
<label>Bottom<input type="number" id="bm-pb" value="16" min="0" max="200" oninput="bmSideInput('padding','b')"></label>
<label>Left<input type="number" id="bm-pl" value="16" min="0" max="200" oninput="bmSideInput('padding','l')"></label>
</div>
</div>

<!-- Border -->
<div>
<div class="bm-section-header">
<span class="bm-section-label bm-label-border">Border</span>
<label class="bm-link-toggle"><input type="checkbox" id="bm-link-border" checked onchange="bmLinkChanged('border')"> Link sides</label>
</div>
<div class="bm-four-grid">
<label>Top<input type="number" id="bm-bt" value="1" min="0" max="50" oninput="bmSideInput('border','t')"></label>
<label>Right<input type="number" id="bm-br" value="1" min="0" max="50" oninput="bmSideInput('border','r')"></label>
<label>Bottom<input type="number" id="bm-bb" value="1" min="0" max="50" oninput="bmSideInput('border','b')"></label>
<label>Left<input type="number" id="bm-bl" value="1" min="0" max="50" oninput="bmSideInput('border','l')"></label>
</div>
<div class="bm-border-style-row">
<label>Border style</label>
<select id="bm-bstyle" onchange="bmUpdate()">
<option value="solid" selected>solid</option>
<option value="dashed">dashed</option>
<option value="dotted">dotted</option>
<option value="double">double</option>
<option value="groove">groove</option>
<option value="none">none</option>
</select>
</div>
</div>

<!-- Margin -->
<div>
<div class="bm-section-header">
<span class="bm-section-label bm-label-margin">Margin</span>
<label class="bm-link-toggle"><input type="checkbox" id="bm-link-margin" checked onchange="bmLinkChanged('margin')"> Link sides</label>
</div>
<div class="bm-four-grid">
<label>Top<input type="number" id="bm-mt" value="16" min="0" max="200" oninput="bmSideInput('margin','t')"></label>
<label>Right<input type="number" id="bm-mr" value="16" min="0" max="200" oninput="bmSideInput('margin','r')"></label>
<label>Bottom<input type="number" id="bm-mb" value="16" min="0" max="200" oninput="bmSideInput('margin','b')"></label>
<label>Left<input type="number" id="bm-ml" value="16" min="0" max="200" oninput="bmSideInput('margin','l')"></label>
</div>
</div>
</div>

<!-- RIGHT: Diagram -->
<div class="bm-diagram-panel">
<h2>Box Model Diagram</h2>
<div class="bm-diagram-wrap">
<div id="bm-margin-layer" class="bm-layer">
<span class="bm-layer-label">margin</span>
<div id="bm-border-layer" class="bm-layer">
<span class="bm-layer-label">border</span>
<div id="bm-padding-layer" class="bm-layer">
<span class="bm-layer-label">padding</span>
<div id="bm-content-layer" class="bm-layer">
<span class="bm-size-label" id="bm-content-size-lbl">200 × 100</span>
<span style="font-size:9px;color:#004085;opacity:.7;">content</span>
</div>
</div>
</div>
</div>
</div>

<!-- Computed size -->
<div class="bm-totals">
<div class="bm-total-box">
<div class="bm-total-val" id="bm-total-w">—</div>
<div class="bm-total-lbl">Total width (px)</div>
</div>
<div class="bm-total-box">
<div class="bm-total-val" id="bm-total-h">—</div>
<div class="bm-total-lbl">Total height (px)</div>
</div>
</div>
</div>
</div>

<!-- CSS Output (full width) -->
<div class="bm-output" style="margin-top:24px;">
<div class="bm-output-header">
<h2>Generated CSS</h2>
<button class="bm-copy-btn" id="bm-copy-btn" onclick="bmCopyCSS()">Copy CSS</button>
</div>
<div class="bm-css-block" id="bm-css-out"></div>
</div>

<script>
(function () {
/* ── helpers ──────────────────────────────────────────── */
function v(id) { return parseInt(document.getElementById(id).value, 10) || 0; }

/* ── link-sides logic ─────────────────────────────────── */
function bmSideInput(group, side) {
var linked = document.getElementById('bm-link-' + group).checked;
if (!linked) { bmUpdate(); return; }
var val = v('bm-' + group[0] + side);
['t','r','b','l'].forEach(function(s) {
document.getElementById('bm-' + group[0] + s).value = val;
});
bmUpdate();
}
window.bmSideInput = bmSideInput;

function bmLinkChanged(group) {
var linked = document.getElementById('bm-link-' + group).checked;
if (linked) {
var val = v('bm-' + group[0] + 't');
['r','b','l'].forEach(function(s) {
document.getElementById('bm-' + group[0] + s).value = val;
});
}
bmUpdate();
}
window.bmLinkChanged = bmLinkChanged;

/* ── presets ──────────────────────────────────────────── */
var PRESETS = {
card:      { cw:280, ch:160, pt:24, pr:24, pb:24, pl:24, bt:1,  br:1,  bb:1,  bl:1,  mt:16, mr:16, mb:16, ml:16, bs:'solid'  },
button:    { cw:120, ch:40,  pt:8,  pr:20, pb:8,  pl:20, bt:2,  br:2,  bb:2,  bl:2,  mt:8,  mr:8,  mb:8,  ml:8,  bs:'solid'  },
input:     { cw:240, ch:40,  pt:8,  pr:12, pb:8,  pl:12, bt:1,  br:1,  bb:1,  bl:1,  mt:4,  mr:0,  mb:4,  ml:0,  bs:'solid'  },
container: { cw:320, ch:200, pt:32, pr:32, pb:32, pl:32, bt:0,  br:0,  bb:0,  bl:0,  mt:0,  mr:'auto',mb:0,ml:'auto',bs:'none'},
reset:     { cw:200, ch:100, pt:0,  pr:0,  pb:0,  pl:0,  bt:0,  br:0,  bb:0,  bl:0,  mt:0,  mr:0,  mb:0,  ml:0,  bs:'solid'  }
};

function bmApplyPreset(name, btn) {
var p = PRESETS[name];
document.querySelectorAll('#bm-app .bm-preset-btn').forEach(function(b){ b.classList.remove('active'); });
btn.classList.add('active');
var fields = ['cw','ch','pt','pr','pb','pl','bt','br','bb','bl','mt','mr','mb','ml'];
fields.forEach(function(f) {
var el = document.getElementById('bm-' + f);
if (el) el.value = p[f] !== undefined ? p[f] : 0;
});
document.getElementById('bm-bstyle').value = p.bs || 'solid';
bmUpdate();
}
window.bmApplyPreset = bmApplyPreset;

/* ── main update ──────────────────────────────────────── */
function bmUpdate() {
var cw = v('bm-cw'), ch = v('bm-ch');
var pt = v('bm-pt'), pr = v('bm-pr'), pb = v('bm-pb'), pl = v('bm-pl');
var bt = v('bm-bt'), br = v('bm-br'), bb = v('bm-bb'), bl = v('bm-bl');
var mt = v('bm-mt'), mr = v('bm-mr'), mb = v('bm-mb'), ml = v('bm-ml');
var bs = document.getElementById('bm-bstyle').value;
var sizing = document.querySelector('input[name="bm-sizing"]:checked').value;

/* Diagram scale: keep max dimension ≤ 340px */
var SCALE = 1;
var totalDiagW = cw + pl + pr + bl + br + ml + mr;
var totalDiagH = ch + pt + pb + bt + bb + mt + mb;
var maxDim = Math.max(totalDiagW, totalDiagH);
if (maxDim > 340) SCALE = 340 / maxDim;
if (SCALE > 1) SCALE = 1;
function px(n) { return Math.round(n * SCALE) + 'px'; }

/* Margin layer (outermost) */
var mEl = document.getElementById('bm-margin-layer');
mEl.style.width  = px(totalDiagW);
mEl.style.height = px(totalDiagH);
mEl.style.padding = px(mt) + ' ' + px(mr) + ' ' + px(mb) + ' ' + px(ml);

/* Border layer */
var bEl = document.getElementById('bm-border-layer');
bEl.style.width  = px(cw + pl + pr + bl + br);
bEl.style.height = px(ch + pt + pb + bt + bb);
bEl.style.padding = px(bt) + ' ' + px(br) + ' ' + px(bb) + ' ' + px(bl);
bEl.style.background = (bs === 'none' || (bt+br+bb+bl === 0)) ? 'transparent' : '#ffd700';

/* Padding layer */
var pEl = document.getElementById('bm-padding-layer');
pEl.style.width  = px(cw + pl + pr);
pEl.style.height = px(ch + pt + pb);
pEl.style.padding = px(pt) + ' ' + px(pr) + ' ' + px(pb) + ' ' + px(pl);

/* Content layer */
var cEl = document.getElementById('bm-content-layer');
cEl.style.width  = px(cw);
cEl.style.height = px(ch);
document.getElementById('bm-content-size-lbl').textContent = cw + ' × ' + ch;

/* Computed totals */
var totalW, totalH;
if (sizing === 'border-box') {
totalW = Math.max(cw + pl + pr + bl + br, cw) + ml + mr;
totalH = Math.max(ch + pt + pb + bt + bb, ch) + mt + mb;
} else {
totalW = cw + pl + pr + bl + br + ml + mr;
totalH = ch + pt + pb + bt + bb + mt + mb;
}
document.getElementById('bm-total-w').textContent = totalW;
document.getElementById('bm-total-h').textContent = totalH;

/* CSS output */
renderCSS(cw, ch, pt, pr, pb, pl, bt, br, bb, bl, bs, mt, mr, mb, ml, sizing);
}
window.bmUpdate = bmUpdate;

/* ── CSS renderer ─────────────────────────────────────── */
function shorthand(t, r, b, l) {
if (t === r && r === b && b === l) return t + 'px';
if (t === b && r === l) return t + 'px ' + r + 'px';
if (r === l) return t + 'px ' + r + 'px ' + b + 'px';
return t + 'px ' + r + 'px ' + b + 'px ' + l + 'px';
}
function borderShorthand(t, r, b, l, style) {
if (style === 'none' || (t+r+b+l === 0)) return null;
if (t === r && r === b && b === l) return t + 'px ' + style + ' #000';
return null; /* use longhand below */
}

function renderCSS(cw,ch,pt,pr,pb,pl,bt,br,bb,bl,bs,mt,mr,mb,ml,sizing) {
var lines = [];
lines.push('.element {');
lines.push('  box-sizing: ' + sizing + ';');
lines.push('  width: ' + cw + 'px;');
lines.push('  height: ' + ch + 'px;');

/* padding */
var pSh = shorthand(pt,pr,pb,pl);
if (pt===0&&pr===0&&pb===0&&pl===0) {
lines.push('  /* padding: 0; */');
} else {
lines.push('  padding: ' + pSh + ';');
}

/* border */
var bSh = borderShorthand(bt,br,bb,bl,bs);
if (bs === 'none' || (bt+br+bb+bl === 0)) {
lines.push('  border: none;');
} else if (bSh) {
lines.push('  border: ' + bSh + ';');
} else {
lines.push('  border-width: ' + shorthand(bt,br,bb,bl) + ';');
lines.push('  border-style: ' + bs + ';');
lines.push('  border-color: #000;');
}

/* margin */
var mSh = shorthand(mt,mr,mb,ml);
if (mt===0&&mr===0&&mb===0&&ml===0) {
lines.push('  /* margin: 0; */');
} else {
lines.push('  margin: ' + mSh + ';');
}

lines.push('}');

/* Render with syntax highlight */
var html = lines.map(function(line) {
if (line.startsWith('  //') || line.startsWith('  /*')) {
return '<span style="color:#6c7086;">' + esc(line) + '</span>';
}
return line.replace(/^(\s*)([\w-]+)(\s*:\s*)(.+?)(;?\s*)$/, function(_, indent, prop, colon, val, semi) {
return esc(indent) +
'<span class="bm-css-prop">' + esc(prop) + '</span>' +
esc(colon) +
'<span class="bm-css-val">' + esc(val) + '</span>' +
'<span class="bm-css-punct">' + esc(semi) + '</span>';
});
}).join('\n');

document.getElementById('bm-css-out').innerHTML = html;
}

function esc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

/* ── copy ─────────────────────────────────────────────── */
function bmCopyCSS() {
var text = document.getElementById('bm-css-out').textContent;
navigator.clipboard.writeText(text).then(function() {
var btn = document.getElementById('bm-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy CSS';
btn.classList.remove('copied');
}, 2000);
});
}
window.bmCopyCSS = bmCopyCSS;

/* ── init ─────────────────────────────────────────────── */
bmUpdate();
})();
</script>
</div>

---

## How to Use

1. **Choose a preset** — Card, Button, Input, or Container loads sensible defaults instantly.
2. **Adjust values** — Each area (margin, border, padding, content) has independent top/right/bottom/left fields. Enable **Link sides** to keep all four sides equal.
3. **Toggle box-sizing** — Switch between `content-box` and `border-box` to see how the computed total changes.
4. **Read the diagram** — Colors match Chrome DevTools: orange = margin, yellow = border, green = padding, blue = content.
5. **Copy CSS** — Hit **Copy CSS** and paste directly into your stylesheet.

## Understanding the CSS Box Model

Every HTML element is a rectangular box made of four concentric layers:

| Layer | Color | Description |
|---|---|---|
| **Content** | Blue | Where text and child elements live. Set by `width` / `height`. |
| **Padding** | Green | Space between content and border. Background color fills this area. |
| **Border** | Yellow | The visible edge of the element. Can have width, style, and color. |
| **Margin** | Orange | Invisible space outside the border. Separates elements from each other. |

### content-box vs border-box

With **`content-box`** (the CSS default) `width` refers to the content area only — padding and border are added on top. With **`border-box`** `width` includes content, padding, and border, making layouts far more predictable. Most modern projects use `box-sizing: border-box` globally.

```css
*, *::before, *::after {
box-sizing: border-box;
}
```

### Margin shorthand reference

| Syntax | Meaning |
|---|---|
| `margin: 16px` | All four sides = 16 px |
| `margin: 8px 16px` | Top/Bottom = 8 px, Left/Right = 16 px |
| `margin: 8px 16px 24px` | Top = 8, Left/Right = 16, Bottom = 24 |
| `margin: 8px 12px 16px 20px` | Top / Right / Bottom / Left |

---

## Related Tools

- [CSS Spacing Generator](/tools/css-spacing-generator/) — Generate consistent spacing scales
- [CSS Grid Generator](/tools/css-grid-generator/) — Build grid layouts visually
- [Flexbox Generator](/tools/flexbox-generator/) — Design flex containers and items
