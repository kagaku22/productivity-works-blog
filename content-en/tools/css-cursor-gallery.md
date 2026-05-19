---
title: "CSS Cursor Gallery"
slug: "css-cursor-gallery"
date: 2025-05-16
description: "Free CSS cursor reference. See all 30+ CSS cursor values in action — hover to preview each cursor type and copy the CSS instantly."
categories: ["Free Tools"]
tags: ["CSS", "cursor", "reference", "web design", "frontend"]
cover:
  image: "/images/covers/css-cursor-gallery.png"
  alt: "CSS Cursor Gallery"
ShowToc: false
---

Browse all CSS `cursor` values interactively. Hover any card to preview the cursor, then click to copy the CSS snippet. Use the search box or category tabs to filter.

<div id="cu-app">
<style>
#cu-app *,#cu-app *::before,#cu-app *::after{box-sizing:border-box;margin:0;padding:0}
#cu-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;max-width:960px;margin:0 auto;padding:0 0 48px}
#cu-app h2{display:none}

/* ── controls ── */
#cu-controls{display:flex;flex-wrap:wrap;gap:10px;margin-bottom:20px;align-items:center}
#cu-search{flex:1;min-width:180px;padding:9px 14px;border:1.5px solid #cbd5e1;border-radius:8px;font-size:14px;outline:none;transition:border-color .2s}
#cu-search:focus{border-color:#6366f1}
#cu-cats{display:flex;flex-wrap:wrap;gap:6px}
.cu-cat{padding:6px 14px;border:1.5px solid #cbd5e1;border-radius:20px;background:#fff;font-size:13px;cursor:pointer;transition:all .15s}
.cu-cat:hover{border-color:#6366f1;color:#6366f1}
.cu-cat.active{background:#6366f1;border-color:#6366f1;color:#fff}

/* ── grid ── */
#cu-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(148px,1fr));gap:12px}
.cu-card{position:relative;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:8px;height:110px;border:1.5px solid #e2e8f0;border-radius:10px;background:#f8fafc;transition:border-color .15s,box-shadow .15s;user-select:none}
.cu-card:hover{border-color:#6366f1;box-shadow:0 2px 12px rgba(99,102,241,.15)}
.cu-icon{font-size:22px;pointer-events:none}
.cu-name{font-size:12px;font-weight:600;color:#475569;pointer-events:none}
.cu-copy-btn{padding:3px 10px;font-size:11px;border:1px solid #cbd5e1;border-radius:5px;background:#fff;color:#6366f1;cursor:pointer;transition:all .15s;pointer-events:auto}
.cu-copy-btn:hover{background:#6366f1;color:#fff;border-color:#6366f1}
.cu-copied{position:absolute;top:6px;right:8px;font-size:10px;color:#22c55e;font-weight:700;opacity:0;transition:opacity .3s}
.cu-copied.show{opacity:1}
.cu-no-results{grid-column:1/-1;text-align:center;padding:40px;color:#94a3b8;font-size:15px}

/* ── custom builder ── */
#cu-builder{margin-top:36px;border:1.5px solid #e2e8f0;border-radius:12px;overflow:hidden}
#cu-builder-header{background:#6366f1;color:#fff;padding:14px 20px;font-size:15px;font-weight:700;display:flex;align-items:center;gap:8px;cursor:pointer}
#cu-builder-body{padding:20px;display:grid;grid-template-columns:1fr 1fr;gap:20px}
@media(max-width:600px){#cu-builder-body{grid-template-columns:1fr}}
.cu-b-label{font-size:13px;font-weight:600;color:#475569;display:block;margin-bottom:5px}
.cu-b-input{width:100%;padding:8px 11px;border:1.5px solid #cbd5e1;border-radius:7px;font-size:13px;outline:none;transition:border-color .2s}
.cu-b-input:focus{border-color:#6366f1}
#cu-preview-area{display:flex;align-items:center;justify-content:center;height:120px;border:2px dashed #cbd5e1;border-radius:8px;font-size:13px;color:#94a3b8;transition:border-color .2s;margin-top:0}
#cu-preview-area:hover{border-color:#6366f1}
#cu-output{background:#1e293b;color:#e2e8f0;border-radius:8px;padding:14px;font-family:'Fira Code',Consolas,monospace;font-size:12.5px;white-space:pre-wrap;word-break:break-all;min-height:60px;margin-top:0}
#cu-copy-output{margin-top:8px;padding:8px 16px;background:#6366f1;color:#fff;border:none;border-radius:7px;font-size:13px;font-weight:600;cursor:pointer;transition:background .15s}
#cu-copy-output:hover{background:#4f46e5}
#cu-upload-label{display:inline-flex;align-items:center;gap:6px;padding:8px 14px;background:#f1f5f9;border:1.5px dashed #cbd5e1;border-radius:7px;font-size:13px;cursor:pointer;transition:border-color .2s}
#cu-upload-label:hover{border-color:#6366f1}
#cu-file-input{display:none}
#cu-img-preview{max-width:64px;max-height:64px;margin-top:8px;border-radius:4px;display:none}

/* ── cross-links ── */
#cu-links{margin-top:32px;display:flex;flex-wrap:wrap;gap:10px}
.cu-link-card{flex:1;min-width:180px;padding:14px 18px;border:1.5px solid #e2e8f0;border-radius:10px;text-decoration:none;color:#1e293b;transition:border-color .15s,box-shadow .15s}
.cu-link-card:hover{border-color:#6366f1;box-shadow:0 2px 10px rgba(99,102,241,.12)}
.cu-link-card span{display:block;font-size:11px;color:#94a3b8;margin-bottom:3px}
.cu-link-card strong{font-size:14px;font-weight:700;color:#6366f1}
</style>

<!-- Controls -->
<div id="cu-controls">
<input id="cu-search" type="search" placeholder="Search cursors…" autocomplete="off">
<div id="cu-cats">
<button class="cu-cat active" data-cat="all">All</button>
<button class="cu-cat" data-cat="general">General</button>
<button class="cu-cat" data-cat="links">Links &amp; Status</button>
<button class="cu-cat" data-cat="selection">Selection</button>
<button class="cu-cat" data-cat="dnd">Drag &amp; Drop</button>
<button class="cu-cat" data-cat="resize">Resize</button>
<button class="cu-cat" data-cat="zoom">Zoom</button>
</div>
</div>

<!-- Card Grid -->
<div id="cu-grid"></div>

<!-- Custom Cursor Builder -->
<div id="cu-builder">
<div id="cu-builder-header">&#9881; Custom Cursor URL Builder</div>
<div id="cu-builder-body">
<div>
<label class="cu-b-label">Upload cursor image (PNG, ICO, SVG)</label>
<label id="cu-upload-label" for="cu-file-input">&#128247; Choose image</label>
<input id="cu-file-input" type="file" accept="image/png,image/x-icon,image/svg+xml,image/gif">
<img id="cu-img-preview" alt="cursor preview">
<br>
<label class="cu-b-label" style="margin-top:14px">Hotspot X (px)</label>
<input id="cu-hx" class="cu-b-input" type="number" value="0" min="0" max="128">
<label class="cu-b-label" style="margin-top:10px">Hotspot Y (px)</label>
<input id="cu-hy" class="cu-b-input" type="number" value="0" min="0" max="128">
<label class="cu-b-label" style="margin-top:10px">Fallback cursor</label>
<select id="cu-fallback" class="cu-b-input">
<option value="auto">auto</option>
<option value="default">default</option>
<option value="pointer" selected>pointer</option>
<option value="crosshair">crosshair</option>
<option value="move">move</option>
<option value="grab">grab</option>
<option value="none">none</option>
</select>
</div>
<div style="display:flex;flex-direction:column;gap:12px">
<div>
<label class="cu-b-label">Preview (hover here)</label>
<div id="cu-preview-area">Hover here to preview your cursor</div>
</div>
<div>
<label class="cu-b-label">Generated CSS</label>
<div id="cu-output">/* Upload an image to generate CSS */</div>
<button id="cu-copy-output">Copy CSS</button>
</div>
</div>
</div>
</div>

<!-- Cross-links -->
<div id="cu-links">
<a class="cu-link-card" href="/tools/css-animation-generator/">
<span>CSS Animations</span>
<strong>CSS Animation Generator</strong>
</a>
<a class="cu-link-card" href="/tools/css-button-generator/">
<span>CSS Buttons</span>
<strong>CSS Button Generator</strong>
</a>
</div>

<script>
(function(){
'use strict';

const CURSORS = [
// General
{name:'auto',       cat:'general', icon:'🖱️'},
{name:'default',    cat:'general', icon:'↖️'},
{name:'none',       cat:'general', icon:'🚫'},
// Links & Status
{name:'context-menu', cat:'links', icon:'📋'},
{name:'help',         cat:'links', icon:'❓'},
{name:'pointer',      cat:'links', icon:'👆'},
{name:'progress',     cat:'links', icon:'⏳'},
{name:'wait',         cat:'links', icon:'⌛'},
// Selection
{name:'cell',          cat:'selection', icon:'⊞'},
{name:'crosshair',     cat:'selection', icon:'✛'},
{name:'text',          cat:'selection', icon:'I'},
{name:'vertical-text', cat:'selection', icon:'⌶'},
// Drag & Drop
{name:'alias',       cat:'dnd', icon:'↗️'},
{name:'copy',        cat:'dnd', icon:'📄'},
{name:'move',        cat:'dnd', icon:'✥'},
{name:'no-drop',     cat:'dnd', icon:'🚫'},
{name:'not-allowed', cat:'dnd', icon:'⛔'},
{name:'grab',        cat:'dnd', icon:'🖐'},
{name:'grabbing',    cat:'dnd', icon:'✊'},
{name:'all-scroll',  cat:'dnd', icon:'⊹'},
// Resize
{name:'col-resize',   cat:'resize', icon:'↔'},
{name:'row-resize',   cat:'resize', icon:'↕'},
{name:'n-resize',     cat:'resize', icon:'↑'},
{name:'e-resize',     cat:'resize', icon:'→'},
{name:'s-resize',     cat:'resize', icon:'↓'},
{name:'w-resize',     cat:'resize', icon:'←'},
{name:'ne-resize',    cat:'resize', icon:'↗'},
{name:'nw-resize',    cat:'resize', icon:'↖'},
{name:'se-resize',    cat:'resize', icon:'↘'},
{name:'sw-resize',    cat:'resize', icon:'↙'},
{name:'ew-resize',    cat:'resize', icon:'↔'},
{name:'ns-resize',    cat:'resize', icon:'↕'},
{name:'nesw-resize',  cat:'resize', icon:'↗↙'},
{name:'nwse-resize',  cat:'resize', icon:'↖↘'},
// Zoom
{name:'zoom-in',  cat:'zoom', icon:'🔍'},
{name:'zoom-out', cat:'zoom', icon:'🔎'},
];

let currentCat = 'all';
let searchTerm = '';

const grid = document.getElementById('cu-grid');
const searchEl = document.getElementById('cu-search');
const catBtns = document.querySelectorAll('.cu-cat');

function css(name){ return `cursor: ${name};`; }

function renderGrid(){
const q = searchTerm.toLowerCase();
const filtered = CURSORS.filter(c =>
(currentCat === 'all' || c.cat === currentCat) &&
c.name.includes(q)
);
grid.innerHTML = '';
if(!filtered.length){
grid.innerHTML = '<div class="cu-no-results">No cursors match your search.</div>';
return;
}
filtered.forEach(c => {
const card = document.createElement('div');
card.className = 'cu-card';
card.style.cursor = c.name;
card.innerHTML = `
<span class="cu-icon">${c.icon}</span>
<span class="cu-name">${c.name}</span>
<button class="cu-copy-btn" data-name="${c.name}">Copy CSS</button>
<span class="cu-copied" id="cp-${c.name.replace(/[^a-z]/g,'-')}">Copied!</span>
`;
card.querySelector('.cu-copy-btn').addEventListener('click', e => {
e.stopPropagation();
const snippet = css(c.name);
navigator.clipboard.writeText(snippet).catch(()=>{
const ta = document.createElement('textarea');
ta.value = snippet; document.body.appendChild(ta);
ta.select(); document.execCommand('copy');
document.body.removeChild(ta);
});
const badge = card.querySelector('.cu-copied');
badge.classList.add('show');
setTimeout(()=>badge.classList.remove('show'), 1500);
});
grid.appendChild(card);
});
}

// Category filter
catBtns.forEach(btn => {
btn.addEventListener('click', ()=>{
catBtns.forEach(b=>b.classList.remove('active'));
btn.classList.add('active');
currentCat = btn.dataset.cat;
renderGrid();
});
});

// Search
searchEl.addEventListener('input', ()=>{
searchTerm = searchEl.value;
renderGrid();
});

// ── Custom Cursor Builder ──
const fileInput  = document.getElementById('cu-file-input');
const imgPreview = document.getElementById('cu-img-preview');
const hxInput    = document.getElementById('cu-hx');
const hyInput    = document.getElementById('cu-hy');
const fallback   = document.getElementById('cu-fallback');
const previewArea= document.getElementById('cu-preview-area');
const output     = document.getElementById('cu-output');
const copyOutput = document.getElementById('cu-copy-output');
let dataUrl = null;

function updateBuilder(){
if(!dataUrl){ return; }
const hx = parseInt(hxInput.value)||0;
const hy = parseInt(hyInput.value)||0;
const fb = fallback.value;
const css = `cursor: url('${dataUrl}') ${hx} ${hy}, ${fb};`;
output.textContent = css;
previewArea.style.cursor = `url('${dataUrl}') ${hx} ${hy}, ${fb}`;
}

fileInput.addEventListener('change', ()=>{
const file = fileInput.files[0];
if(!file) return;
const reader = new FileReader();
reader.onload = e => {
dataUrl = e.target.result;
imgPreview.src = dataUrl;
imgPreview.style.display = 'block';
updateBuilder();
};
reader.readAsDataURL(file);
});

[hxInput, hyInput, fallback].forEach(el => el.addEventListener('input', updateBuilder));

copyOutput.addEventListener('click', ()=>{
const text = output.textContent;
if(text.startsWith('/*')) return;
navigator.clipboard.writeText(text).catch(()=>{
const ta = document.createElement('textarea');
ta.value = text; document.body.appendChild(ta);
ta.select(); document.execCommand('copy');
document.body.removeChild(ta);
});
copyOutput.textContent = 'Copied!';
setTimeout(()=>{ copyOutput.textContent = 'Copy CSS'; }, 1500);
});

renderGrid();
})();
</script>
</div>

## How to Use CSS Cursors

Set the cursor on any element using the `cursor` CSS property:

```css
/* keyword cursor */
.btn { cursor: pointer; }

/* custom image cursor */
.custom { cursor: url('/cursors/my-cursor.png') 0 0, auto; }
```

The `cursor` property accepts a comma-separated list — the browser uses the first value it supports, falling back to the last. Always end custom cursor lists with a CSS keyword such as `auto` or `default`.

## Browser Support

All keyword cursor values listed above are supported in every modern browser (Chrome, Firefox, Safari, Edge). Custom URL cursors support PNG, SVG, and ICO formats; recommended maximum size is **128×128 px**.

---

**Related tools:** [CSS Animation Generator](/tools/css-animation-generator/) &nbsp;|&nbsp; [CSS Button Generator](/tools/css-button-generator/)
