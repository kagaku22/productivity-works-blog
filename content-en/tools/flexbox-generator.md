---
title: "CSS Flexbox Generator — Visual Playground"
date: 2025-05-16
description: "Free visual CSS Flexbox generator. Drag controls to build flex layouts instantly. Presets for navbars, grids, and holy grail layouts. Copy CSS with one click."
categories: ["Free Tools"]
slug: "flexbox-generator"
ShowToc: false
aliases:
  - "/tools/flexbox-generator/"
  - "/tools/flexbox-generator/"
cover:
  image: "/images/covers/flexbox-generator.png"
  alt: "CSS Flexbox Generator"
---

<div id="flex-app">

<style>
#flex-app *,
#flex-app *::before,
#flex-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#flex-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 14px;
color: #1a1a2e;
background: #f0f4ff;
border-radius: 12px;
overflow: hidden;
margin: 1.5rem 0;
}

/* ── Toolbar ── */
#flex-app .fa-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
background: #1a1a2e;
padding: 10px 14px;
}

#flex-app .fa-toolbar span.fa-label {
color: #a0aec0;
font-size: 12px;
font-weight: 600;
letter-spacing: .05em;
text-transform: uppercase;
margin-right: 2px;
}

#flex-app .fa-preset-btn {
background: #2d3748;
color: #e2e8f0;
border: 1px solid #4a5568;
border-radius: 6px;
padding: 5px 11px;
cursor: pointer;
font-size: 12px;
transition: background .15s;
}
#flex-app .fa-preset-btn:hover {
background: #4a5568;
}

/* ── Main layout ── */
#flex-app .fa-main {
display: flex;
flex-wrap: wrap;
gap: 0;
min-height: 520px;
}

/* ── Control panel ── */
#flex-app .fa-controls {
width: 260px;
flex-shrink: 0;
background: #ffffff;
border-right: 1px solid #e2e8f0;
overflow-y: auto;
max-height: 680px;
}

@media (max-width: 700px) {
#flex-app .fa-controls {
width: 100%;
max-height: none;
border-right: none;
border-bottom: 1px solid #e2e8f0;
}
#flex-app .fa-main {
flex-direction: column;
}
}

#flex-app .fa-section {
border-bottom: 1px solid #e8ecf4;
padding: 12px 14px;
}

#flex-app .fa-section-title {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .07em;
color: #718096;
margin-bottom: 10px;
}

#flex-app .fa-row {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 8px;
gap: 6px;
}

#flex-app .fa-row label {
font-size: 12px;
color: #4a5568;
white-space: nowrap;
min-width: 90px;
}

#flex-app .fa-row select,
#flex-app .fa-row input[type="text"],
#flex-app .fa-row input[type="number"] {
flex: 1;
padding: 4px 7px;
border: 1px solid #cbd5e0;
border-radius: 5px;
font-size: 12px;
background: #f7fafc;
color: #2d3748;
outline: none;
transition: border-color .15s;
}
#flex-app .fa-row select:focus,
#flex-app .fa-row input:focus {
border-color: #667eea;
}

#flex-app .fa-row input[type="range"] {
flex: 1;
accent-color: #667eea;
}

/* ── Item selector ── */
#flex-app .fa-item-tabs {
display: flex;
flex-wrap: wrap;
gap: 4px;
margin-bottom: 10px;
}

#flex-app .fa-item-tab {
padding: 3px 9px;
border-radius: 4px;
border: 1px solid #cbd5e0;
font-size: 11px;
cursor: pointer;
background: #f7fafc;
color: #4a5568;
transition: all .15s;
}
#flex-app .fa-item-tab.active {
background: #667eea;
color: #fff;
border-color: #667eea;
}

#flex-app .fa-add-btn,
#flex-app .fa-remove-btn {
font-size: 11px;
padding: 3px 9px;
border-radius: 4px;
border: none;
cursor: pointer;
transition: background .15s;
}
#flex-app .fa-add-btn {
background: #48bb78;
color: #fff;
}
#flex-app .fa-add-btn:hover { background: #38a169; }
#flex-app .fa-remove-btn {
background: #fc8181;
color: #fff;
}
#flex-app .fa-remove-btn:hover { background: #e53e3e; }

/* ── Preview area ── */
#flex-app .fa-preview-col {
flex: 1;
display: flex;
flex-direction: column;
min-width: 0;
}

#flex-app .fa-preview-header {
padding: 10px 14px;
background: #edf2ff;
border-bottom: 1px solid #c3d0f5;
font-size: 12px;
font-weight: 600;
color: #4a5568;
display: flex;
align-items: center;
gap: 8px;
}

#flex-app .fa-preview-wrap {
flex: 1;
padding: 16px;
overflow: auto;
}

#flex-app #fa-preview-container {
display: flex;
width: 100%;
min-height: 260px;
background: #dde6ff;
border-radius: 8px;
border: 2px dashed #a3b4f5;
padding: 10px;
transition: all .2s;
position: relative;
}

#flex-app .fa-flex-item {
display: flex;
align-items: center;
justify-content: center;
border-radius: 6px;
font-size: 13px;
font-weight: 700;
color: #fff;
min-width: 40px;
min-height: 40px;
cursor: pointer;
transition: outline .15s, transform .1s;
position: relative;
text-shadow: 0 1px 2px rgba(0,0,0,.25);
}

#flex-app .fa-flex-item.selected {
outline: 3px solid #1a1a2e;
outline-offset: 2px;
transform: scale(1.04);
}

/* ── CSS Output ── */
#flex-app .fa-output {
background: #1a1a2e;
color: #a8d8ea;
padding: 14px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 12px;
line-height: 1.7;
white-space: pre-wrap;
word-break: break-all;
border-top: 1px solid #2d3748;
min-height: 120px;
}

#flex-app .fa-output-header {
display: flex;
align-items: center;
justify-content: space-between;
background: #2d3748;
padding: 8px 14px;
border-top: 1px solid #4a5568;
}

#flex-app .fa-output-header span {
color: #a0aec0;
font-size: 11px;
font-weight: 600;
text-transform: uppercase;
letter-spacing: .06em;
}

#flex-app .fa-copy-btn {
background: #667eea;
color: #fff;
border: none;
border-radius: 5px;
padding: 4px 12px;
font-size: 12px;
cursor: pointer;
transition: background .15s;
}
#flex-app .fa-copy-btn:hover { background: #5a67d8; }
#flex-app .fa-copy-btn.copied { background: #48bb78; }

/* ── Syntax colors ── */
#flex-app .fa-output .tok-sel  { color: #fbd38d; }
#flex-app .fa-output .tok-prop { color: #90cdf4; }
#flex-app .fa-output .tok-val  { color: #9ae6b4; }
#flex-app .fa-output .tok-punc { color: #e2e8f0; }
</style>

<!-- Toolbar: Presets -->
<div class="fa-toolbar">
<span class="fa-label">Presets:</span>
<button class="fa-preset-btn" data-preset="navbar">Navigation Bar</button>
<button class="fa-preset-btn" data-preset="cardgrid">Card Grid</button>
<button class="fa-preset-btn" data-preset="holygrail">Holy Grail</button>
<button class="fa-preset-btn" data-preset="sidebar">Sidebar Layout</button>
<button class="fa-preset-btn" data-preset="centered">Centered Content</button>
</div>

<div class="fa-main">

<!-- Controls -->
<div class="fa-controls">

<!-- Container -->
<div class="fa-section">
<div class="fa-section-title">Container</div>

<div class="fa-row">
<label>display</label>
<select id="fa-display">
<option value="flex" selected>flex</option>
<option value="inline-flex">inline-flex</option>
</select>
</div>

<div class="fa-row">
<label>flex-direction</label>
<select id="fa-direction">
<option value="row" selected>row</option>
<option value="row-reverse">row-reverse</option>
<option value="column">column</option>
<option value="column-reverse">column-reverse</option>
</select>
</div>

<div class="fa-row">
<label>justify-content</label>
<select id="fa-justify">
<option value="flex-start" selected>flex-start</option>
<option value="flex-end">flex-end</option>
<option value="center">center</option>
<option value="space-between">space-between</option>
<option value="space-around">space-around</option>
<option value="space-evenly">space-evenly</option>
</select>
</div>

<div class="fa-row">
<label>align-items</label>
<select id="fa-align-items">
<option value="stretch" selected>stretch</option>
<option value="flex-start">flex-start</option>
<option value="flex-end">flex-end</option>
<option value="center">center</option>
<option value="baseline">baseline</option>
</select>
</div>

<div class="fa-row">
<label>align-content</label>
<select id="fa-align-content">
<option value="normal" selected>normal</option>
<option value="flex-start">flex-start</option>
<option value="flex-end">flex-end</option>
<option value="center">center</option>
<option value="space-between">space-between</option>
<option value="space-around">space-around</option>
<option value="stretch">stretch</option>
</select>
</div>

<div class="fa-row">
<label>flex-wrap</label>
<select id="fa-wrap">
<option value="nowrap" selected>nowrap</option>
<option value="wrap">wrap</option>
<option value="wrap-reverse">wrap-reverse</option>
</select>
</div>

<div class="fa-row">
<label>gap</label>
<input type="text" id="fa-gap" value="0px" style="max-width:90px;">
</div>

<div class="fa-row">
<label>height</label>
<input type="text" id="fa-height" value="260px" style="max-width:90px;">
</div>
</div>

<!-- Items -->
<div class="fa-section">
<div class="fa-section-title">Items</div>
<div style="display:flex;gap:5px;margin-bottom:8px;">
<button class="fa-add-btn" id="fa-add-item">+ Add Item</button>
<button class="fa-remove-btn" id="fa-remove-item">- Remove</button>
</div>
<div class="fa-item-tabs" id="fa-item-tabs"></div>
</div>

<!-- Per-item -->
<div class="fa-section" id="fa-item-controls">
<div class="fa-section-title">Selected Item</div>

<div class="fa-row">
<label>flex-grow</label>
<input type="number" id="fa-grow" value="0" min="0" max="10" step="1" style="max-width:80px;">
</div>

<div class="fa-row">
<label>flex-shrink</label>
<input type="number" id="fa-shrink" value="1" min="0" max="10" step="1" style="max-width:80px;">
</div>

<div class="fa-row">
<label>flex-basis</label>
<input type="text" id="fa-basis" value="auto" style="max-width:80px;">
</div>

<div class="fa-row">
<label>order</label>
<input type="number" id="fa-order" value="0" min="-10" max="10" step="1" style="max-width:80px;">
</div>

<div class="fa-row">
<label>align-self</label>
<select id="fa-align-self">
<option value="auto" selected>auto</option>
<option value="flex-start">flex-start</option>
<option value="flex-end">flex-end</option>
<option value="center">center</option>
<option value="baseline">baseline</option>
<option value="stretch">stretch</option>
</select>
</div>

<div class="fa-row">
<label>width</label>
<input type="text" id="fa-item-width" value="auto" style="max-width:80px;">
</div>

<div class="fa-row">
<label>height</label>
<input type="text" id="fa-item-height" value="auto" style="max-width:80px;">
</div>

<div class="fa-row">
<label>label</label>
<input type="text" id="fa-item-label" value="" style="max-width:80px;">
</div>
</div>

</div><!-- /fa-controls -->

<!-- Preview + Output -->
<div class="fa-preview-col">
<div class="fa-preview-header">
<span>Live Preview</span>
<span style="font-weight:400;color:#718096;font-size:11px;">Click an item to select it</span>
</div>
<div class="fa-preview-wrap">
<div id="fa-preview-container"></div>
</div>

<div class="fa-output-header">
<span>Generated CSS</span>
<button class="fa-copy-btn" id="fa-copy-btn">Copy CSS</button>
</div>
<div class="fa-output" id="fa-output"></div>
</div>

</div><!-- /fa-main -->

</div><!-- #flex-app -->

<script>
(function() {
/* ── State ── */
var COLORS = [
'#667eea','#f6ad55','#68d391','#fc8181','#63b3ed',
'#b794f4','#f687b3','#4fd1c5','#fbd38d','#90cdf4'
];

var container = {
display: 'flex',
flexDirection: 'row',
justifyContent: 'flex-start',
alignItems: 'stretch',
alignContent: 'normal',
flexWrap: 'nowrap',
gap: '0px',
height: '260px'
};

var defaultItem = function(i) {
return {
grow: 0, shrink: 1, basis: 'auto',
order: 0, alignSelf: 'auto',
width: 'auto', height: 'auto',
label: 'Item ' + (i + 1),
color: COLORS[i % COLORS.length]
};
};

var items = [defaultItem(0), defaultItem(1), defaultItem(2)];
var selectedItem = 0;

/* ── DOM refs ── */
var preview   = document.getElementById('fa-preview-container');
var outputEl  = document.getElementById('fa-output');
var tabsEl    = document.getElementById('fa-item-tabs');
var copyBtn   = document.getElementById('fa-copy-btn');

/* ── Bind container controls ── */
function bindSel(id, key, obj) {
var el = document.getElementById(id);
el.addEventListener('change', function() { obj[key] = el.value; render(); });
}
function bindInput(id, key, obj) {
var el = document.getElementById(id);
el.addEventListener('input', function() { obj[key] = el.value; render(); });
}

bindSel('fa-display',        'display',        container);
bindSel('fa-direction',      'flexDirection',  container);
bindSel('fa-justify',        'justifyContent', container);
bindSel('fa-align-items',    'alignItems',     container);
bindSel('fa-align-content',  'alignContent',   container);
bindSel('fa-wrap',           'flexWrap',       container);
bindInput('fa-gap',          'gap',            container);
bindInput('fa-height',       'height',         container);

/* ── Bind item controls ── */
function getItem() { return items[selectedItem]; }

function bindItemInput(id, key, parser) {
var el = document.getElementById(id);
el.addEventListener('input', function() {
getItem()[key] = parser ? parser(el.value) : el.value;
render();
});
}
function bindItemSel(id, key) {
var el = document.getElementById(id);
el.addEventListener('change', function() {
getItem()[key] = el.value;
render();
});
}

bindItemInput('fa-grow',        'grow',    Number);
bindItemInput('fa-shrink',      'shrink',  Number);
bindItemInput('fa-basis',       'basis',   null);
bindItemInput('fa-order',       'order',   Number);
bindItemSel  ('fa-align-self',  'alignSelf');
bindItemInput('fa-item-width',  'width',   null);
bindItemInput('fa-item-height', 'height',  null);
bindItemInput('fa-item-label',  'label',   null);

/* ── Add / Remove ── */
document.getElementById('fa-add-item').addEventListener('click', function() {
if (items.length >= 10) return;
items.push(defaultItem(items.length));
selectedItem = items.length - 1;
render();
});

document.getElementById('fa-remove-item').addEventListener('click', function() {
if (items.length <= 1) return;
items.splice(selectedItem, 1);
if (selectedItem >= items.length) selectedItem = items.length - 1;
render();
});

/* ── Copy button ── */
copyBtn.addEventListener('click', function() {
var text = buildCSSText();
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(function() { flashCopy(); });
} else {
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
flashCopy();
}
});
function flashCopy() {
copyBtn.textContent = 'Copied!';
copyBtn.classList.add('copied');
setTimeout(function() {
copyBtn.textContent = 'Copy CSS';
copyBtn.classList.remove('copied');
}, 1800);
}

/* ── Presets ── */
var PRESETS = {
navbar: {
container: { display:'flex', flexDirection:'row', justifyContent:'space-between',
alignItems:'center', alignContent:'normal', flexWrap:'nowrap', gap:'0px', height:'56px' },
items: [
{ grow:0, shrink:0, basis:'auto', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Logo', color:'#667eea' },
{ grow:1, shrink:1, basis:'auto', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Nav Links', color:'#4a5568' },
{ grow:0, shrink:0, basis:'auto', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'CTA', color:'#48bb78' }
]
},
cardgrid: {
container: { display:'flex', flexDirection:'row', justifyContent:'flex-start',
alignItems:'stretch', alignContent:'normal', flexWrap:'wrap', gap:'16px', height:'auto' },
items: [0,1,2,3,4,5].map(function(i) {
return { grow:0, shrink:0, basis:'calc(33% - 12px)', order:0, alignSelf:'auto', width:'auto', height:'120px', label:'Card '+(i+1), color:COLORS[i] };
})
},
holygrail: {
container: { display:'flex', flexDirection:'row', justifyContent:'flex-start',
alignItems:'stretch', alignContent:'normal', flexWrap:'nowrap', gap:'0px', height:'320px' },
items: [
{ grow:0, shrink:0, basis:'180px', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Left Sidebar', color:'#667eea' },
{ grow:1, shrink:1, basis:'auto', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Main Content', color:'#63b3ed' },
{ grow:0, shrink:0, basis:'160px', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Right Sidebar', color:'#b794f4' }
]
},
sidebar: {
container: { display:'flex', flexDirection:'row', justifyContent:'flex-start',
alignItems:'stretch', alignContent:'normal', flexWrap:'nowrap', gap:'0px', height:'340px' },
items: [
{ grow:0, shrink:0, basis:'220px', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Sidebar', color:'#4a5568' },
{ grow:1, shrink:1, basis:'auto', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Content', color:'#68d391' }
]
},
centered: {
container: { display:'flex', flexDirection:'column', justifyContent:'center',
alignItems:'center', alignContent:'normal', flexWrap:'nowrap', gap:'12px', height:'300px' },
items: [
{ grow:0, shrink:0, basis:'auto', order:0, alignSelf:'auto', width:'auto', height:'auto', label:'Centered', color:'#f6ad55' }
]
}
};

document.querySelectorAll('#flex-app .fa-preset-btn').forEach(function(btn) {
btn.addEventListener('click', function() {
var p = PRESETS[btn.dataset.preset];
if (!p) return;
Object.assign(container, p.container);
items = p.items.map(function(it) { return Object.assign({}, it); });
selectedItem = 0;
syncContainerUI();
render();
});
});

function syncContainerUI() {
document.getElementById('fa-display').value        = container.display;
document.getElementById('fa-direction').value      = container.flexDirection;
document.getElementById('fa-justify').value        = container.justifyContent;
document.getElementById('fa-align-items').value    = container.alignItems;
document.getElementById('fa-align-content').value  = container.alignContent;
document.getElementById('fa-wrap').value           = container.flexWrap;
document.getElementById('fa-gap').value            = container.gap;
document.getElementById('fa-height').value         = container.height;
}

function syncItemUI() {
var it = getItem();
document.getElementById('fa-grow').value        = it.grow;
document.getElementById('fa-shrink').value      = it.shrink;
document.getElementById('fa-basis').value       = it.basis;
document.getElementById('fa-order').value       = it.order;
document.getElementById('fa-align-self').value  = it.alignSelf;
document.getElementById('fa-item-width').value  = it.width;
document.getElementById('fa-item-height').value = it.height;
document.getElementById('fa-item-label').value  = it.label;
}

/* ── Build CSS text ── */
function buildCSSText() {
var lines = [
'.container {',
'  display: ' + container.display + ';',
'  flex-direction: ' + container.flexDirection + ';',
'  justify-content: ' + container.justifyContent + ';',
'  align-items: ' + container.alignItems + ';'
];
if (container.alignContent !== 'normal') {
lines.push('  align-content: ' + container.alignContent + ';');
}
if (container.flexWrap !== 'nowrap') {
lines.push('  flex-wrap: ' + container.flexWrap + ';');
}
if (container.gap !== '0px' && container.gap !== '0') {
lines.push('  gap: ' + container.gap + ';');
}
if (container.height && container.height !== 'auto') {
lines.push('  height: ' + container.height + ';');
}
lines.push('}');
lines.push('');

items.forEach(function(it, i) {
var sel = '.item-' + (i + 1);
var props = [];
if (it.grow !== 0)           props.push('  flex-grow: ' + it.grow + ';');
if (it.shrink !== 1)         props.push('  flex-shrink: ' + it.shrink + ';');
if (it.basis !== 'auto')     props.push('  flex-basis: ' + it.basis + ';');
if (it.order !== 0)          props.push('  order: ' + it.order + ';');
if (it.alignSelf !== 'auto') props.push('  align-self: ' + it.alignSelf + ';');
if (it.width !== 'auto')     props.push('  width: ' + it.width + ';');
if (it.height !== 'auto')    props.push('  height: ' + it.height + ';');
if (props.length > 0) {
lines.push(sel + ' {');
props.forEach(function(p) { lines.push(p); });
lines.push('}');
lines.push('');
}
});

return lines.join('\n');
}

/* ── Render highlighted CSS ── */
function renderCSS() {
var raw = buildCSSText();
var esc = raw
.replace(/&/g,'&amp;')
.replace(/</g,'&lt;')
.replace(/>/g,'&gt;');

// Simple syntax highlight
esc = esc.replace(/(\.[\w-]+(?:\s*,\s*\.[\w-]+)*)\s*\{/g, '<span class="tok-sel">$1</span> <span class="tok-punc">{</span>');
esc = esc.replace(/\}/g, '<span class="tok-punc">}</span>');
esc = esc.replace(/([\w-]+)(\s*:\s*)([^;<\n]+)(;)/g,
'<span class="tok-prop">$1</span><span class="tok-punc">$2</span><span class="tok-val">$3</span><span class="tok-punc">$4</span>');

outputEl.innerHTML = esc;
}

/* ── Render tabs ── */
function renderTabs() {
tabsEl.innerHTML = '';
items.forEach(function(it, i) {
var btn = document.createElement('button');
btn.className = 'fa-item-tab' + (i === selectedItem ? ' active' : '');
btn.textContent = it.label || ('Item ' + (i + 1));
btn.addEventListener('click', function() {
selectedItem = i;
render();
});
tabsEl.appendChild(btn);
});
}

/* ── Render preview ── */
function renderPreview() {
// Apply container styles
preview.style.display        = container.display;
preview.style.flexDirection  = container.flexDirection;
preview.style.justifyContent = container.justifyContent;
preview.style.alignItems     = container.alignItems;
preview.style.alignContent   = container.alignContent;
preview.style.flexWrap       = container.flexWrap;
preview.style.gap            = container.gap;
preview.style.height         = container.height;

// Clear and rebuild items
preview.innerHTML = '';
items.forEach(function(it, i) {
var el = document.createElement('div');
el.className = 'fa-flex-item' + (i === selectedItem ? ' selected' : '');
el.textContent = it.label || ('Item ' + (i + 1));
el.style.background  = it.color;
el.style.flexGrow    = it.grow;
el.style.flexShrink  = it.shrink;
el.style.flexBasis   = it.basis;
el.style.order       = it.order;
el.style.alignSelf   = it.alignSelf;
if (it.width  !== 'auto') el.style.width  = it.width;
if (it.height !== 'auto') el.style.height = it.height;
el.style.padding = '8px';
el.addEventListener('click', function() {
selectedItem = i;
render();
});
preview.appendChild(el);
});
}

/* ── Master render ── */
function render() {
renderPreview();
renderTabs();
syncItemUI();
renderCSS();
}

/* ── Init ── */
render();

})();
</script>

---

### Related Tools

> Generate box shadows → [CSS Box Shadow Generator](/tools/box-shadow-generator/)

> Build gradients → [CSS Gradient Generator](/tools/css-gradient-generator/)

> Create color palettes → [Color Palette Generator](/tools/color-palette-generator/)
