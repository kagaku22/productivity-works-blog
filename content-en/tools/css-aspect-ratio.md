---
title: "CSS Aspect Ratio Generator — Responsive Containers"
date: 2025-05-16
description: "Generate CSS aspect-ratio property for responsive containers. Presets for 16:9, 4:3, 1:1 and more. Modern CSS and padding-bottom fallback. Copy code instantly."
categories: ["Free Tools"]
tags: ["CSS", "Web Design", "Free Tools"]
slug: "css-aspect-ratio"
ShowToc: false
cover:
  image: "/images/covers/css-aspect-ratio.png"
  alt: "CSS Aspect Ratio Generator"
---

Generate CSS `aspect-ratio` property values for perfectly proportioned, responsive containers — no JavaScript required.

<div id="ar-app">
<style>
#ar-app *,
#ar-app *::before,
#ar-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#ar-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 15px;
color: #1a1a2e;
background: #f8f9fc;
border-radius: 12px;
padding: 28px 24px;
max-width: 760px;
margin: 32px auto;
}
#ar-app h2 {
font-size: 1.25rem;
font-weight: 700;
margin-bottom: 20px;
color: #111827;
}
#ar-app .ar-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 20px;
}
#ar-app .ar-preset-btn {
background: #fff;
border: 2px solid #d1d5db;
border-radius: 8px;
padding: 7px 14px;
font-size: 0.85rem;
font-weight: 600;
cursor: pointer;
color: #374151;
transition: border-color 0.15s, background 0.15s, color 0.15s;
}
#ar-app .ar-preset-btn:hover {
border-color: #6366f1;
color: #6366f1;
}
#ar-app .ar-preset-btn.active {
background: #6366f1;
border-color: #6366f1;
color: #fff;
}
#ar-app .ar-inputs {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 20px;
flex-wrap: wrap;
}
#ar-app .ar-inputs label {
font-size: 0.85rem;
font-weight: 600;
color: #6b7280;
white-space: nowrap;
}
#ar-app .ar-inputs input[type="number"] {
width: 90px;
padding: 8px 10px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-size: 1rem;
font-weight: 700;
color: #111827;
text-align: center;
outline: none;
transition: border-color 0.15s;
}
#ar-app .ar-inputs input[type="number"]:focus {
border-color: #6366f1;
}
#ar-app .ar-sep {
font-size: 1.3rem;
font-weight: 700;
color: #9ca3af;
user-select: none;
}
#ar-app .ar-maxwidth-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 24px;
flex-wrap: wrap;
}
#ar-app .ar-maxwidth-row label {
font-size: 0.85rem;
font-weight: 600;
color: #6b7280;
white-space: nowrap;
}
#ar-app .ar-maxwidth-row input[type="range"] {
flex: 1;
min-width: 120px;
max-width: 260px;
accent-color: #6366f1;
cursor: pointer;
}
#ar-app .ar-maxwidth-val {
font-size: 0.9rem;
font-weight: 700;
color: #6366f1;
min-width: 48px;
}
#ar-app .ar-preview-area {
margin-bottom: 24px;
}
#ar-app .ar-preview-label {
font-size: 0.8rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.07em;
color: #9ca3af;
margin-bottom: 10px;
}
#ar-app .ar-preview-wrapper {
background: #e5e7eb;
border-radius: 10px;
padding: 16px;
display: flex;
justify-content: center;
align-items: flex-start;
min-height: 80px;
}
#ar-app .ar-preview-box {
background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 50%, #a78bfa 100%);
border-radius: 8px;
display: flex;
align-items: center;
justify-content: center;
color: #fff;
font-weight: 700;
font-size: 1rem;
letter-spacing: 0.03em;
transition: aspect-ratio 0.25s, max-width 0.25s;
}
#ar-app .ar-code-section {
display: flex;
flex-direction: column;
gap: 16px;
}
#ar-app .ar-code-block {
background: #1e1b2e;
border-radius: 10px;
padding: 18px 18px 14px;
position: relative;
}
#ar-app .ar-code-title {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #a78bfa;
margin-bottom: 10px;
}
#ar-app .ar-code-title .ar-badge {
display: inline-block;
background: #312e81;
color: #c4b5fd;
border-radius: 4px;
font-size: 0.7rem;
padding: 1px 6px;
margin-left: 6px;
font-weight: 600;
vertical-align: middle;
}
#ar-app .ar-code-title .ar-badge-old {
background: #3b2a1a;
color: #fbbf24;
}
#ar-app pre {
margin: 0;
font-family: "Fira Mono", "Consolas", "Monaco", monospace;
font-size: 0.85rem;
line-height: 1.7;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
overflow-x: auto;
}
#ar-app .ar-prop   { color: #93c5fd; }
#ar-app .ar-val    { color: #6ee7b7; }
#ar-app .ar-unit   { color: #fcd34d; }
#ar-app .ar-sel    { color: #f9a8d4; }
#ar-app .ar-comment{ color: #6b7280; font-style: italic; }
#ar-app .ar-copy-btn {
position: absolute;
top: 14px;
right: 14px;
background: #312e81;
border: none;
border-radius: 6px;
color: #c4b5fd;
font-size: 0.78rem;
font-weight: 700;
padding: 5px 12px;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#ar-app .ar-copy-btn:hover {
background: #6366f1;
color: #fff;
}
#ar-app .ar-copy-btn.copied {
background: #065f46;
color: #6ee7b7;
}
@media (max-width: 520px) {
#ar-app {
padding: 18px 12px;
}
#ar-app .ar-inputs input[type="number"] {
width: 72px;
}
#ar-app .ar-maxwidth-row input[type="range"] {
min-width: 80px;
}
#ar-app pre {
font-size: 0.78rem;
}
}
</style>

<h2>CSS Aspect Ratio Generator</h2>

<div class="ar-presets" id="ar-presets">
<button class="ar-preset-btn active" data-w="16" data-h="9">16:9</button>
<button class="ar-preset-btn" data-w="4" data-h="3">4:3</button>
<button class="ar-preset-btn" data-w="1" data-h="1">1:1</button>
<button class="ar-preset-btn" data-w="21" data-h="9">21:9</button>
<button class="ar-preset-btn" data-w="9" data-h="16">9:16</button>
<button class="ar-preset-btn" data-w="3" data-h="2">3:2</button>
<button class="ar-preset-btn" data-w="2" data-h="3">2:3</button>
</div>

<div class="ar-inputs">
<label for="ar-width">Width</label>
<input type="number" id="ar-width" min="1" max="9999" value="16" />
<span class="ar-sep">:</span>
<label for="ar-height">Height</label>
<input type="number" id="ar-height" min="1" max="9999" value="9" />
</div>

<div class="ar-maxwidth-row">
<label for="ar-maxwidth">Max-width</label>
<input type="range" id="ar-maxwidth" min="100" max="100" value="100" step="5" />
<span class="ar-maxwidth-val" id="ar-maxwidth-val">100%</span>
</div>

<div class="ar-preview-area">
<div class="ar-preview-label">Live Preview</div>
<div class="ar-preview-wrapper" id="ar-preview-wrapper">
<div class="ar-preview-box" id="ar-preview-box">16 : 9</div>
</div>
</div>

<div class="ar-code-section">
<div class="ar-code-block" id="ar-block-modern">
<div class="ar-code-title">
Modern CSS — aspect-ratio
<span class="ar-badge">Recommended</span>
</div>
<button class="ar-copy-btn" id="ar-copy-modern" onclick="arCopy('modern')">Copy</button>
<pre id="ar-pre-modern"></pre>
</div>

<div class="ar-code-block" id="ar-block-hack">
<div class="ar-code-title">
Padding-bottom Hack
<span class="ar-badge ar-badge-old">Legacy Fallback</span>
</div>
<button class="ar-copy-btn" id="ar-copy-hack" onclick="arCopy('hack')">Copy</button>
<pre id="ar-pre-hack"></pre>
</div>
</div>

<script>
(function() {
var wInput  = document.getElementById('ar-width');
var hInput  = document.getElementById('ar-height');
var mwRange = document.getElementById('ar-maxwidth');
var mwVal   = document.getElementById('ar-maxwidth-val');
var preBox  = document.getElementById('ar-preview-box');
var preWrap = document.getElementById('ar-preview-wrapper');
var preModern = document.getElementById('ar-pre-modern');
var preHack   = document.getElementById('ar-pre-hack');
var presets   = document.querySelectorAll('#ar-presets .ar-preset-btn');

function gcd(a, b) { return b === 0 ? a : gcd(b, a % b); }

function simplify(w, h) {
var g = gcd(w, h);
return [w / g, h / g];
}

function hl(cls, text) {
return '<span class="' + cls + '">' + text + '</span>';
}

function render() {
var w  = Math.max(1, parseInt(wInput.value) || 16);
var h  = Math.max(1, parseInt(hInput.value) || 9);
var mw = parseInt(mwRange.value) || 100;
var sw = simplify(w, h);
var ratio = w + ' / ' + h;
var pct   = ((h / w) * 100).toFixed(4).replace(/\.?0+$/, '') + '%';

// Update preview box
preBox.style.aspectRatio = ratio;
preBox.style.width = mw + '%';
preBox.style.maxWidth = '100%';
preBox.textContent = sw[0] + ' : ' + sw[1];

// Modern CSS output
var modern = [
hl('ar-sel', '.responsive-container') + ' {',
'  ' + hl('ar-prop', 'width') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'max-width') + ': ' + hl('ar-val', mw) + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'aspect-ratio') + ': ' + hl('ar-val', w + ' / ' + h) + ';',
'  ' + hl('ar-comment', '/* overflow: hidden; — add if needed */'),
'}'
].join('\n');

preModern.innerHTML = modern;

// Padding-bottom hack output
var hack = [
hl('ar-comment', '/* Wrapper — padding-bottom trick */'),
hl('ar-sel', '.ar-wrapper') + ' {',
'  ' + hl('ar-prop', 'position') + ': ' + hl('ar-val', 'relative') + ';',
'  ' + hl('ar-prop', 'width') + ': ' + hl('ar-val', mw) + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'max-width') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'padding-bottom') + ': ' + hl('ar-val', pct) + ';',
'  ' + hl('ar-prop', 'height') + ': ' + hl('ar-val', '0') + ';',
'}',
'',
hl('ar-comment', '/* Inner content — positioned absolutely */'),
hl('ar-sel', '.ar-wrapper > *') + ' {',
'  ' + hl('ar-prop', 'position') + ': ' + hl('ar-val', 'absolute') + ';',
'  ' + hl('ar-prop', 'top') + ': ' + hl('ar-val', '0') + ';',
'  ' + hl('ar-prop', 'left') + ': ' + hl('ar-val', '0') + ';',
'  ' + hl('ar-prop', 'width') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'  ' + hl('ar-prop', 'height') + ': ' + hl('ar-val', '100') + hl('ar-unit', '%') + ';',
'}'
].join('\n');

preHack.innerHTML = hack;
}

function updatePresetButtons(w, h) {
presets.forEach(function(btn) {
btn.classList.toggle('active',
parseInt(btn.dataset.w) === w && parseInt(btn.dataset.h) === h);
});
}

presets.forEach(function(btn) {
btn.addEventListener('click', function() {
wInput.value = btn.dataset.w;
hInput.value = btn.dataset.h;
updatePresetButtons(parseInt(btn.dataset.w), parseInt(btn.dataset.h));
render();
});
});

wInput.addEventListener('input', function() {
updatePresetButtons(parseInt(wInput.value), parseInt(hInput.value));
render();
});
hInput.addEventListener('input', function() {
updatePresetButtons(parseInt(wInput.value), parseInt(hInput.value));
render();
});

mwRange.addEventListener('input', function() {
mwVal.textContent = mwRange.value + '%';
render();
});

// Responsive range max
function setRangeMax() {
var ww = preWrap.clientWidth || 600;
mwRange.max = 100;
mwRange.value = Math.min(parseInt(mwRange.value), 100);
mwVal.textContent = mwRange.value + '%';
}

window.addEventListener('resize', function() { setRangeMax(); render(); });
setRangeMax();
render();

window.arCopy = function(which) {
var pre = which === 'modern' ? preModern : preHack;
var text = pre.textContent;
var btn  = document.getElementById('ar-copy-' + which);
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('copied'); }, 1800);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('copied'); }, 1800);
}
};
})();
</script>
</div>

## How It Works

The modern `aspect-ratio` CSS property tells the browser to maintain a fixed width-to-height ratio as the element resizes. Set it on any block element and pair with `width: 100%` for a fully responsive container.

```css
.video-container {
width: 100%;
aspect-ratio: 16 / 9;
}
```

The **padding-bottom hack** achieves the same result in older browsers (pre-2021) by exploiting how percentage padding is always calculated relative to the parent's *width*, not height.

## Common Ratios Reference

| Ratio | Use Case |
|-------|----------|
| 16:9  | HD video, YouTube embeds, widescreen |
| 4:3   | Classic TV, older presentations |
| 1:1   | Square images, Instagram posts |
| 21:9  | Cinematic/ultrawide hero banners |
| 9:16  | Mobile video, Stories, Reels |
| 3:2   | DSLR photos, card thumbnails |

## Browser Support

`aspect-ratio` is supported by all modern browsers (Chrome 88+, Firefox 89+, Safari 15+, Edge 88+). For IE11 or older Safari, use the padding-bottom fallback generated above.

---

**Related Tools:**
- [Aspect Ratio Calculator](/tools/aspect-ratio-calculator/) — Find the missing dimension from any ratio
- [CSS Flexbox Generator](/tools/flexbox-generator/) — Build flexbox layouts visually
- [Image Resizer](/tools/image-resizer/) — Resize images while preserving aspect ratio
