---
title: "Favicon Generator — Free Online Tool"
date: 2025-05-16
description: "Create favicons from text, shapes, emoji, or uploaded images. Download as PNG in 16x16 and 32x32 sizes instantly — no signup required."
categories: ["Free Tools"]
slug: "favicon-generator"
ShowToc: false
aliases:
  - "/tools/favicon-generator/"
  - "/tools/favicon-generator/"
cover:
  image: "/images/covers/favicon-generator.png"
  alt: "Favicon Generator"
---

Create a favicon for your website in seconds. Choose from text, emoji, or upload your own image — then download ready-to-use PNG files and copy the HTML snippet.

<div id="fav-app">

<style>
#fav-app *,
#fav-app *::before,
#fav-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#fav-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 780px;
color: #1e1b2e;
}

#fav-app .fav-tabs {
display: flex;
gap: 4px;
margin-bottom: 24px;
background: #f3f0ff;
padding: 4px;
border-radius: 10px;
}

#fav-app .fav-tab {
flex: 1;
padding: 9px 12px;
border: none;
background: transparent;
border-radius: 7px;
font-size: 14px;
font-weight: 500;
cursor: pointer;
color: #6b6b8a;
transition: background 0.15s, color 0.15s;
}

#fav-app .fav-tab.active {
background: #7c3aed;
color: #fff;
}

#fav-app .fav-panel { display: none; }
#fav-app .fav-panel.active { display: block; }

#fav-app .fav-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-bottom: 16px;
}

@media (max-width: 540px) {
#fav-app .fav-grid { grid-template-columns: 1fr; }
#fav-app .fav-tabs { flex-direction: column; }
}

#fav-app label {
display: block;
font-size: 13px;
font-weight: 600;
color: #4b4569;
margin-bottom: 6px;
}

#fav-app input[type="text"],
#fav-app input[type="number"],
#fav-app select,
#fav-app textarea {
width: 100%;
padding: 9px 11px;
border: 1.5px solid #d4c9f8;
border-radius: 8px;
font-size: 15px;
background: #faf9ff;
color: #1e1b2e;
outline: none;
transition: border-color 0.15s;
}

#fav-app input[type="text"]:focus,
#fav-app input[type="number"]:focus,
#fav-app select:focus,
#fav-app textarea:focus {
border-color: #7c3aed;
}

#fav-app input[type="color"] {
width: 48px;
height: 38px;
border: 1.5px solid #d4c9f8;
border-radius: 8px;
padding: 2px;
cursor: pointer;
background: #faf9ff;
}

#fav-app .color-row {
display: flex;
align-items: center;
gap: 10px;
}

#fav-app .color-row input[type="text"] {
flex: 1;
font-family: monospace;
}

#fav-app .shape-row {
display: flex;
gap: 8px;
}

#fav-app .shape-btn {
flex: 1;
padding: 8px 4px;
border: 1.5px solid #d4c9f8;
border-radius: 8px;
background: #faf9ff;
font-size: 13px;
cursor: pointer;
color: #4b4569;
font-weight: 500;
transition: border-color 0.15s, background 0.15s, color 0.15s;
}

#fav-app .shape-btn.active {
border-color: #7c3aed;
background: #ede9fe;
color: #7c3aed;
}

#fav-app .preview-section {
background: #f8f6ff;
border: 1.5px solid #e0d8fc;
border-radius: 12px;
padding: 20px;
margin-bottom: 20px;
text-align: center;
}

#fav-app .preview-section h3 {
font-size: 13px;
font-weight: 600;
color: #6b6b8a;
margin-bottom: 16px;
text-transform: uppercase;
letter-spacing: 0.05em;
}

#fav-app .preview-canvases {
display: flex;
align-items: flex-end;
justify-content: center;
gap: 24px;
flex-wrap: wrap;
}

#fav-app .preview-item {
display: flex;
flex-direction: column;
align-items: center;
gap: 6px;
}

#fav-app .preview-item span {
font-size: 12px;
color: #9490b2;
}

#fav-app canvas {
image-rendering: pixelated;
border-radius: 4px;
box-shadow: 0 1px 4px rgba(124,58,237,0.12);
background: transparent;
}

#fav-app .fav-btn {
display: inline-flex;
align-items: center;
gap: 6px;
padding: 10px 20px;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
text-decoration: none;
}

#fav-app .fav-btn:active { transform: scale(0.97); }

#fav-app .btn-primary {
background: #7c3aed;
color: #fff;
}

#fav-app .btn-secondary {
background: #ede9fe;
color: #7c3aed;
}

#fav-app .btn-primary:hover { opacity: 0.88; }
#fav-app .btn-secondary:hover { opacity: 0.80; }

#fav-app .download-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 20px;
}

#fav-app .meta-section {
background: #1e1b2e;
border-radius: 10px;
padding: 16px;
margin-bottom: 8px;
position: relative;
}

#fav-app .meta-section pre {
color: #c4b5fd;
font-size: 13px;
line-height: 1.6;
white-space: pre-wrap;
word-break: break-all;
font-family: 'Menlo', 'Consolas', monospace;
}

#fav-app .copy-btn {
position: absolute;
top: 10px;
right: 10px;
padding: 5px 12px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 6px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
}

#fav-app .copy-btn:hover { opacity: 0.85; }

#fav-app .upload-zone {
border: 2px dashed #c4b5fd;
border-radius: 10px;
padding: 32px 16px;
text-align: center;
cursor: pointer;
background: #faf9ff;
margin-bottom: 16px;
transition: background 0.15s, border-color 0.15s;
}

#fav-app .upload-zone:hover,
#fav-app .upload-zone.dragover {
background: #ede9fe;
border-color: #7c3aed;
}

#fav-app .upload-zone p {
font-size: 14px;
color: #6b6b8a;
margin-top: 8px;
}

#fav-app .upload-icon {
font-size: 36px;
line-height: 1;
}

#fav-app .emoji-grid {
display: grid;
grid-template-columns: repeat(8, 1fr);
gap: 6px;
margin-bottom: 12px;
max-height: 200px;
overflow-y: auto;
padding: 4px;
}

#fav-app .emoji-btn {
font-size: 22px;
background: #faf9ff;
border: 1.5px solid #e0d8fc;
border-radius: 7px;
padding: 4px;
cursor: pointer;
text-align: center;
line-height: 1.4;
transition: background 0.1s, border-color 0.1s;
}

#fav-app .emoji-btn:hover { background: #ede9fe; border-color: #7c3aed; }
#fav-app .emoji-btn.active { background: #7c3aed; border-color: #7c3aed; }

#fav-app .emoji-custom {
display: flex;
gap: 10px;
align-items: center;
margin-bottom: 16px;
}

#fav-app .emoji-custom input {
font-size: 22px;
width: 60px;
text-align: center;
}

#fav-app .section-divider {
border: none;
border-top: 1.5px solid #e0d8fc;
margin: 20px 0;
}

#fav-app .info-text {
font-size: 13px;
color: #9490b2;
margin-bottom: 14px;
}

#fav-app .fav-field { margin-bottom: 14px; }

#fav-app .range-row {
display: flex;
align-items: center;
gap: 10px;
}

#fav-app .range-row input[type="range"] {
flex: 1;
accent-color: #7c3aed;
}

#fav-app .range-val {
font-size: 14px;
font-weight: 600;
color: #7c3aed;
min-width: 28px;
text-align: right;
}
</style>

<div class="fav-tabs">
<button class="fav-tab active" onclick="favSwitchTab('text', this)">Text / Shape</button>
<button class="fav-tab" onclick="favSwitchTab('emoji', this)">Emoji</button>
<button class="fav-tab" onclick="favSwitchTab('upload', this)">Upload Image</button>
</div>

<!-- TEXT TAB -->
<div id="fav-panel-text" class="fav-panel active">
<div class="fav-grid">
<div>
<div class="fav-field">
<label for="fav-text">Characters (1–2)</label>
<input type="text" id="fav-text" maxlength="2" value="FV" oninput="favRender()">
</div>
<div class="fav-field">
<label>Font Size</label>
<div class="range-row">
<input type="range" id="fav-fontsize" min="14" max="52" value="36" oninput="favRender(); document.getElementById('fav-fontsize-val').textContent=this.value">
<span class="range-val" id="fav-fontsize-val">36</span>
</div>
</div>
<div class="fav-field">
<label>Font Weight</label>
<select id="fav-fontweight" onchange="favRender()">
<option value="700" selected>Bold</option>
<option value="900">Black (900)</option>
<option value="400">Regular</option>
</select>
</div>
</div>
<div>
<div class="fav-field">
<label>Shape</label>
<div class="shape-row">
<button class="shape-btn active" onclick="favSetShape('circle', this)">Circle</button>
<button class="shape-btn" onclick="favSetShape('rounded', this)">Rounded</button>
<button class="shape-btn" onclick="favSetShape('square', this)">Square</button>
</div>
</div>
<div class="fav-field">
<label>Background Color</label>
<div class="color-row">
<input type="color" id="fav-bg" value="#7c3aed" oninput="favSyncColor('bg')">
<input type="text" id="fav-bg-hex" value="#7c3aed" maxlength="7" oninput="favSyncHex('bg')">
</div>
</div>
<div class="fav-field">
<label>Text Color</label>
<div class="color-row">
<input type="color" id="fav-fg" value="#ffffff" oninput="favSyncColor('fg')">
<input type="text" id="fav-fg-hex" value="#ffffff" maxlength="7" oninput="favSyncHex('fg')">
</div>
</div>
</div>
</div>
</div>

<!-- EMOJI TAB -->
<div id="fav-panel-emoji" class="fav-panel">
<div class="fav-field">
<label>Pick an Emoji</label>
<div class="emoji-grid" id="fav-emoji-grid"></div>
</div>
<div class="emoji-custom">
<label style="white-space:nowrap; margin:0;">Or type/paste:</label>
<input type="text" id="fav-emoji-custom" maxlength="4" placeholder="e.g. 🚀" style="width:70px; font-size:22px; text-align:center;" oninput="favSetEmojiCustom(this.value)">
</div>
<div class="fav-field">
<label>Background Color</label>
<div class="color-row">
<input type="color" id="fav-emoji-bg" value="#7c3aed" oninput="favSyncEmojiColor()">
<input type="text" id="fav-emoji-bg-hex" value="#7c3aed" maxlength="7" oninput="favSyncEmojiHex()">
</div>
</div>
<div class="fav-field">
<label>Shape</label>
<div class="shape-row">
<button class="shape-btn active" id="emoji-shape-circle" onclick="favSetEmojiShape('circle', this)">Circle</button>
<button class="shape-btn" id="emoji-shape-rounded" onclick="favSetEmojiShape('rounded', this)">Rounded</button>
<button class="shape-btn" id="emoji-shape-square" onclick="favSetEmojiShape('square', this)">Square</button>
</div>
</div>
</div>

<!-- UPLOAD TAB -->
<div id="fav-panel-upload" class="fav-panel">
<div class="upload-zone" id="fav-upload-zone" onclick="document.getElementById('fav-file-input').click()" ondragover="favDragOver(event)" ondragleave="favDragLeave(event)" ondrop="favDrop(event)">
<div class="upload-icon">&#128444;</div>
<p>Click or drag &amp; drop an image here</p>
<p style="font-size:12px; margin-top:4px;">PNG, JPG, GIF, SVG, WebP</p>
</div>
<input type="file" id="fav-file-input" accept="image/*" style="display:none" onchange="favLoadFile(this)">
<div class="fav-field" id="fav-crop-controls" style="display:none">
<label>Crop / Scale</label>
<div class="range-row">
<input type="range" id="fav-crop-scale" min="10" max="200" value="100" oninput="favRenderUpload(); document.getElementById('fav-crop-scale-val').textContent=this.value+'%'">
<span class="range-val" id="fav-crop-scale-val">100%</span>
</div>
<div class="range-row" style="margin-top:8px;">
<label style="margin:0; min-width:60px;">Offset X</label>
<input type="range" id="fav-crop-x" min="-64" max="64" value="0" oninput="favRenderUpload()">
</div>
<div class="range-row" style="margin-top:8px;">
<label style="margin:0; min-width:60px;">Offset Y</label>
<input type="range" id="fav-crop-y" min="-64" max="64" value="0" oninput="favRenderUpload()">
</div>
</div>
</div>

<hr class="section-divider">

<!-- PREVIEW -->
<div class="preview-section">
<h3>Live Preview</h3>
<div class="preview-canvases">
<div class="preview-item">
<canvas id="fav-canvas-64" width="64" height="64" style="width:64px;height:64px;"></canvas>
<span>64×64 (edit canvas)</span>
</div>
<div class="preview-item">
<canvas id="fav-canvas-32" width="32" height="32" style="width:48px;height:48px;"></canvas>
<span>32×32</span>
</div>
<div class="preview-item">
<canvas id="fav-canvas-16" width="16" height="16" style="width:32px;height:32px;"></canvas>
<span>16×16</span>
</div>
</div>
</div>

<!-- DOWNLOADS -->
<div class="download-row">
<button class="fav-btn btn-primary" onclick="favDownload(32)">&#8615; Download 32×32 PNG</button>
<button class="fav-btn btn-primary" onclick="favDownload(16)">&#8615; Download 16×16 PNG</button>
<button class="fav-btn btn-secondary" onclick="favDownload(64)">&#8615; Download 64×64 PNG</button>
</div>

<!-- HTML SNIPPET -->
<label>HTML meta tags — paste into your &lt;head&gt;</label>
<div class="meta-section">
<button class="copy-btn" onclick="favCopyMeta()">Copy</button>
<pre id="fav-meta-code"></pre>
</div>
<p class="info-text" id="fav-copy-msg" style="display:none; color:#7c3aed; font-weight:600;">Copied to clipboard!</p>

</div><!-- #fav-app -->

<script>
(function() {
var _currentTab = 'text';
var _shape = 'circle';
var _emojiShape = 'circle';
var _selectedEmoji = '⭐';
var _uploadImg = null;

var EMOJIS = [
'⭐','🚀','💡','🎨','🔥','✨','🌟','💎',
'🎯','📌','🛠','⚡','🧩','🏆','🎉','💬',
'🔑','🌈','🌀','🦋','🐉','🍀','🌸','🎵',
'💻','📱','🖥','🔒','🛡','🤖','🧠','👾',
'📊','📈','💰','🏠','✈️','🌍','⚙️','🔧'
];

function init() {
buildEmojiGrid();
favRender();
updateMeta();
}

function buildEmojiGrid() {
var grid = document.getElementById('fav-emoji-grid');
EMOJIS.forEach(function(em) {
var btn = document.createElement('button');
btn.className = 'emoji-btn' + (em === _selectedEmoji ? ' active' : '');
btn.textContent = em;
btn.onclick = function() {
_selectedEmoji = em;
document.querySelectorAll('#fav-emoji-grid .emoji-btn').forEach(function(b){ b.classList.remove('active'); });
btn.classList.add('active');
document.getElementById('fav-emoji-custom').value = '';
favRenderEmoji();
updateMeta();
};
grid.appendChild(btn);
});
}

window.favSwitchTab = function(tab, btn) {
_currentTab = tab;
document.querySelectorAll('#fav-app .fav-tab').forEach(function(b){ b.classList.remove('active'); });
btn.classList.add('active');
document.querySelectorAll('#fav-app .fav-panel').forEach(function(p){ p.classList.remove('active'); });
document.getElementById('fav-panel-' + tab).classList.add('active');
favRenderAll();
updateMeta();
};

window.favSetShape = function(s, btn) {
_shape = s;
document.querySelectorAll('#fav-app .shape-btn').forEach(function(b){ if(b.onclick.toString().indexOf('favSetShape')>-1) b.classList.remove('active'); });
btn.classList.add('active');
favRender();
};

window.favSetEmojiShape = function(s, btn) {
_emojiShape = s;
['circle','rounded','square'].forEach(function(sh){
var el = document.getElementById('emoji-shape-' + sh);
if(el) el.classList.remove('active');
});
btn.classList.add('active');
favRenderEmoji();
};

window.favSyncColor = function(which) {
var col = document.getElementById('fav-' + which).value;
document.getElementById('fav-' + which + '-hex').value = col;
favRender();
};

window.favSyncHex = function(which) {
var val = document.getElementById('fav-' + which + '-hex').value;
if (/^#[0-9a-fA-F]{6}$/.test(val)) {
document.getElementById('fav-' + which).value = val;
favRender();
}
};

window.favSyncEmojiColor = function() {
var col = document.getElementById('fav-emoji-bg').value;
document.getElementById('fav-emoji-bg-hex').value = col;
favRenderEmoji();
};

window.favSyncEmojiHex = function() {
var val = document.getElementById('fav-emoji-bg-hex').value;
if (/^#[0-9a-fA-F]{6}$/.test(val)) {
document.getElementById('fav-emoji-bg').value = val;
favRenderEmoji();
}
};

window.favSetEmojiCustom = function(val) {
if (val.trim()) {
_selectedEmoji = val.trim();
document.querySelectorAll('#fav-emoji-grid .emoji-btn').forEach(function(b){ b.classList.remove('active'); });
favRenderEmoji();
updateMeta();
}
};

function drawBackground(ctx, size, shape, color) {
ctx.clearRect(0, 0, size, size);
ctx.fillStyle = color;
if (shape === 'circle') {
ctx.beginPath();
ctx.arc(size/2, size/2, size/2, 0, Math.PI*2);
ctx.fill();
} else if (shape === 'rounded') {
var r = size * 0.22;
ctx.beginPath();
ctx.moveTo(r, 0);
ctx.lineTo(size-r, 0);
ctx.quadraticCurveTo(size, 0, size, r);
ctx.lineTo(size, size-r);
ctx.quadraticCurveTo(size, size, size-r, size);
ctx.lineTo(r, size);
ctx.quadraticCurveTo(0, size, 0, size-r);
ctx.lineTo(0, r);
ctx.quadraticCurveTo(0, 0, r, 0);
ctx.closePath();
ctx.fill();
} else {
ctx.fillRect(0, 0, size, size);
}
}

function scaleDown(srcCanvas, destCanvas) {
var ctx = destCanvas.getContext('2d');
ctx.clearRect(0, 0, destCanvas.width, destCanvas.height);
ctx.imageSmoothingEnabled = true;
ctx.imageSmoothingQuality = 'high';
ctx.drawImage(srcCanvas, 0, 0, destCanvas.width, destCanvas.height);
}

window.favRender = function() {
if (_currentTab !== 'text') return;
var text = document.getElementById('fav-text').value || 'FV';
var fontSize = parseInt(document.getElementById('fav-fontsize').value);
var fontWeight = document.getElementById('fav-fontweight').value;
var bgColor = document.getElementById('fav-bg').value;
var fgColor = document.getElementById('fav-fg').value;

var c64 = document.getElementById('fav-canvas-64');
var ctx = c64.getContext('2d');
drawBackground(ctx, 64, _shape, bgColor);

ctx.fillStyle = fgColor;
ctx.font = fontWeight + ' ' + fontSize + 'px system-ui, -apple-system, sans-serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
ctx.fillText(text.substring(0,2), 32, 34);

scaleDown(c64, document.getElementById('fav-canvas-32'));
scaleDown(c64, document.getElementById('fav-canvas-16'));
updateMeta();
};

function favRenderEmoji() {
var emoji = _selectedEmoji || '⭐';
var bgColor = document.getElementById('fav-emoji-bg').value;

var c64 = document.getElementById('fav-canvas-64');
var ctx = c64.getContext('2d');
drawBackground(ctx, 64, _emojiShape, bgColor);

ctx.font = '40px serif';
ctx.textAlign = 'center';
ctx.textBaseline = 'middle';
ctx.fillText(emoji, 32, 34);

scaleDown(c64, document.getElementById('fav-canvas-32'));
scaleDown(c64, document.getElementById('fav-canvas-16'));
updateMeta();
}

window.favRenderUpload = function() {
if (!_uploadImg) return;
var c64 = document.getElementById('fav-canvas-64');
var ctx = c64.getContext('2d');
ctx.clearRect(0, 0, 64, 64);

var scale = parseInt(document.getElementById('fav-crop-scale').value) / 100;
var ox = parseInt(document.getElementById('fav-crop-x').value);
var oy = parseInt(document.getElementById('fav-crop-y').value);
var w = _uploadImg.naturalWidth * scale;
var h = _uploadImg.naturalHeight * scale;
var x = (64 - w) / 2 + ox;
var y = (64 - h) / 2 + oy;
ctx.drawImage(_uploadImg, x, y, w, h);

scaleDown(c64, document.getElementById('fav-canvas-32'));
scaleDown(c64, document.getElementById('fav-canvas-16'));
updateMeta();
};

function favRenderAll() {
if (_currentTab === 'text') favRender();
else if (_currentTab === 'emoji') favRenderEmoji();
else if (_currentTab === 'upload' && _uploadImg) favRenderUpload();
}

window.favDownload = function(size) {
var src = document.getElementById('fav-canvas-64');
var tmp = document.createElement('canvas');
tmp.width = size;
tmp.height = size;
var ctx = tmp.getContext('2d');
ctx.imageSmoothingEnabled = true;
ctx.imageSmoothingQuality = 'high';
ctx.drawImage(src, 0, 0, size, size);
var a = document.createElement('a');
a.download = 'favicon-' + size + 'x' + size + '.png';
a.href = tmp.toDataURL('image/png');
a.click();
};

function updateMeta() {
var code = '<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">\n' +
'<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">\n' +
'<link rel="shortcut icon" href="/favicon.ico">';
document.getElementById('fav-meta-code').textContent = code;
}

window.favCopyMeta = function() {
var text = document.getElementById('fav-meta-code').textContent;
navigator.clipboard.writeText(text).then(function() {
var msg = document.getElementById('fav-copy-msg');
msg.style.display = 'block';
setTimeout(function(){ msg.style.display = 'none'; }, 2000);
});
};

window.favDragOver = function(e) {
e.preventDefault();
document.getElementById('fav-upload-zone').classList.add('dragover');
};

window.favDragLeave = function(e) {
document.getElementById('fav-upload-zone').classList.remove('dragover');
};

window.favDrop = function(e) {
e.preventDefault();
document.getElementById('fav-upload-zone').classList.remove('dragover');
var file = e.dataTransfer.files[0];
if (file && file.type.startsWith('image/')) processImageFile(file);
};

window.favLoadFile = function(input) {
if (input.files && input.files[0]) processImageFile(input.files[0]);
};

function processImageFile(file) {
var reader = new FileReader();
reader.onload = function(e) {
var img = new Image();
img.onload = function() {
_uploadImg = img;
document.getElementById('fav-crop-controls').style.display = 'block';
favRenderUpload();
};
img.src = e.target.result;
};
reader.readAsDataURL(file);
}

init();
})();
</script>

---

**Related:** Pick colors for your favicon → [Color Picker](/tools/color-picker/)
