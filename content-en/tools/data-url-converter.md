---
title: "Data URL Converter"
date: 2025-05-16
description: "Free data URL converter. Convert files to data URIs (base64) and back. Supports images, fonts, SVGs, and any file type. Preview images, copy output, check file sizes."
categories: ["Free Tools"]
slug: "data-url-converter"
ShowToc: false
cover:
  image: "/images/covers/data-url-converter.png"
  alt: "Data URL Converter — File to Base64 Data URI Tool"
---

Convert any file to a Base64 data URL, or decode a data URL back to a downloadable file — all in your browser, no server, completely private.

<div id="du-app">
<style>
#du-app *,
#du-app *::before,
#du-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#du-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
color: #1a1a2e;
max-width: 860px;
margin: 0 auto;
padding: 0 0 48px;
}
#du-tabs {
display: flex;
gap: 8px;
margin-bottom: 24px;
}
.du-tab {
flex: 1;
padding: 12px 20px;
border: 2px solid #7c3aed;
border-radius: 10px;
background: #fff;
color: #7c3aed;
font-size: 0.97rem;
font-weight: 600;
cursor: pointer;
transition: background 0.18s, color 0.18s;
text-align: center;
}
.du-tab.du-active {
background: #7c3aed;
color: #fff;
}
.du-tab:hover:not(.du-active) {
background: #f5f3ff;
}
.du-panel {
display: none;
}
.du-panel.du-active {
display: block;
}
/* Drop zone */
#du-drop-zone {
border: 2.5px dashed #7c3aed;
border-radius: 14px;
padding: 48px 24px;
text-align: center;
cursor: pointer;
background: #f5f3ff;
transition: background 0.2s, border-color 0.2s;
position: relative;
}
#du-drop-zone.du-dragover {
background: #ede9fe;
border-color: #5b21b6;
}
#du-drop-icon {
font-size: 48px;
line-height: 1;
margin-bottom: 12px;
}
#du-drop-zone p {
color: #6d28d9;
font-size: 1.05rem;
font-weight: 500;
}
#du-drop-zone small {
display: block;
margin-top: 6px;
color: #8b5cf6;
font-size: 0.82rem;
}
#du-file-input {
position: absolute;
inset: 0;
opacity: 0;
cursor: pointer;
width: 100%;
height: 100%;
}
/* Results — encode */
#du-enc-results {
display: none;
}
#du-info-bar {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin-bottom: 20px;
padding: 14px 18px;
background: #f5f3ff;
border-radius: 10px;
border: 1px solid #ddd6fe;
font-size: 0.88rem;
}
.du-info-item {
display: flex;
flex-direction: column;
gap: 2px;
}
.du-info-label {
font-weight: 600;
color: #5b21b6;
font-size: 0.78rem;
text-transform: uppercase;
letter-spacing: 0.04em;
}
.du-info-value {
color: #1a1a2e;
font-size: 0.9rem;
}
#du-size-increase {
font-weight: 700;
color: #7c3aed;
}
/* Image preview */
#du-preview-wrap {
display: none;
margin-bottom: 20px;
text-align: center;
}
#du-preview-wrap img {
max-width: 100%;
max-height: 220px;
border-radius: 10px;
border: 1px solid #ddd6fe;
box-shadow: 0 2px 12px rgba(124,58,237,0.10);
}
#du-preview-label {
font-size: 0.8rem;
color: #8b5cf6;
margin-top: 6px;
}
/* Output blocks */
.du-output-block {
margin-bottom: 18px;
}
.du-output-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 6px;
}
.du-output-title {
font-size: 0.85rem;
font-weight: 700;
color: #5b21b6;
text-transform: uppercase;
letter-spacing: 0.04em;
}
.du-copy-btn {
padding: 5px 14px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 6px;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.18s;
}
.du-copy-btn:hover {
background: #6d28d9;
}
.du-copy-btn.du-copied {
background: #16a34a;
}
.du-output-block textarea {
width: 100%;
height: 100px;
padding: 10px 12px;
border: 1.5px solid #ddd6fe;
border-radius: 8px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.78rem;
color: #1a1a2e;
resize: vertical;
background: #fafaf9;
line-height: 1.5;
}
.du-output-block textarea:focus {
outline: none;
border-color: #7c3aed;
}
/* Actions row */
#du-enc-actions {
display: flex;
gap: 10px;
margin-top: 8px;
}
.du-btn-secondary {
padding: 9px 20px;
background: #fff;
color: #7c3aed;
border: 2px solid #7c3aed;
border-radius: 8px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.18s;
}
.du-btn-secondary:hover {
background: #f5f3ff;
}
/* Decode panel */
#du-dec-panel label {
display: block;
font-size: 0.85rem;
font-weight: 700;
color: #5b21b6;
text-transform: uppercase;
letter-spacing: 0.04em;
margin-bottom: 6px;
}
#du-paste-area {
width: 100%;
height: 130px;
padding: 10px 12px;
border: 2px solid #ddd6fe;
border-radius: 10px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.8rem;
color: #1a1a2e;
resize: vertical;
background: #f5f3ff;
margin-bottom: 14px;
line-height: 1.5;
transition: border-color 0.18s;
}
#du-paste-area:focus {
outline: none;
border-color: #7c3aed;
}
#du-dec-btn {
padding: 10px 28px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 8px;
font-size: 0.97rem;
font-weight: 700;
cursor: pointer;
transition: background 0.18s;
margin-bottom: 18px;
}
#du-dec-btn:hover {
background: #6d28d9;
}
#du-dec-error {
display: none;
padding: 10px 16px;
background: #fef2f2;
border: 1px solid #fca5a5;
border-radius: 8px;
color: #991b1b;
font-size: 0.88rem;
font-weight: 500;
margin-bottom: 14px;
}
#du-dec-results {
display: none;
}
#du-dec-info {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin-bottom: 18px;
padding: 14px 18px;
background: #f0fdf4;
border-radius: 10px;
border: 1px solid #bbf7d0;
font-size: 0.88rem;
}
#du-dec-preview-wrap {
display: none;
margin-bottom: 18px;
text-align: center;
}
#du-dec-preview-wrap img {
max-width: 100%;
max-height: 220px;
border-radius: 10px;
border: 1px solid #ddd6fe;
box-shadow: 0 2px 12px rgba(124,58,237,0.10);
}
#du-dec-preview-label {
font-size: 0.8rem;
color: #16a34a;
margin-top: 6px;
}
#du-download-btn {
display: inline-flex;
align-items: center;
gap: 8px;
padding: 10px 26px;
background: #16a34a;
color: #fff;
border: none;
border-radius: 8px;
font-size: 0.97rem;
font-weight: 700;
cursor: pointer;
text-decoration: none;
transition: background 0.18s;
}
#du-download-btn:hover {
background: #15803d;
}
/* Common use cases */
#du-usecases {
margin-top: 32px;
padding: 18px 20px;
background: #f5f3ff;
border-radius: 12px;
border: 1px solid #ddd6fe;
}
#du-usecases h3 {
font-size: 0.95rem;
font-weight: 700;
color: #5b21b6;
margin-bottom: 12px;
}
#du-usecases ul {
list-style: none;
display: flex;
flex-wrap: wrap;
gap: 8px;
}
#du-usecases li {
padding: 5px 12px;
background: #ede9fe;
border-radius: 20px;
font-size: 0.82rem;
color: #5b21b6;
font-weight: 500;
}
@media (max-width: 520px) {
#du-info-bar { flex-direction: column; gap: 8px; }
#du-tabs { flex-direction: column; }
#du-enc-actions { flex-direction: column; }
}
</style>

<div id="du-tabs">
<button class="du-tab du-active" id="du-tab-enc" onclick="(function(){document.getElementById('du-enc-panel').classList.add('du-active');document.getElementById('du-dec-panel').classList.remove('du-active');document.getElementById('du-tab-enc').classList.add('du-active');document.getElementById('du-tab-dec').classList.remove('du-active');})()">
File → Data URL
</button>
<button class="du-tab" id="du-tab-dec" onclick="(function(){document.getElementById('du-dec-panel').classList.add('du-active');document.getElementById('du-enc-panel').classList.remove('du-active');document.getElementById('du-tab-dec').classList.add('du-active');document.getElementById('du-tab-enc').classList.remove('du-active');})()">
Data URL → File
</button>
</div>

<!-- ENCODE PANEL -->
<div class="du-panel du-active" id="du-enc-panel">
<div id="du-drop-zone">
<input type="file" id="du-file-input" aria-label="Choose a file to convert">
<div id="du-drop-icon">📁</div>
<p>Drag &amp; drop any file here, or click to browse</p>
<small>Images, SVG, fonts, JSON, PDF, audio, video — any file type</small>
</div>

<div id="du-enc-results">
<div id="du-info-bar">
<div class="du-info-item">
<span class="du-info-label">File name</span>
<span class="du-info-value" id="du-fname">—</span>
</div>
<div class="du-info-item">
<span class="du-info-label">MIME type</span>
<span class="du-info-value" id="du-mime">—</span>
</div>
<div class="du-info-item">
<span class="du-info-label">Original size</span>
<span class="du-info-value" id="du-orig-size">—</span>
</div>
<div class="du-info-item">
<span class="du-info-label">Encoded size</span>
<span class="du-info-value" id="du-enc-size">—</span>
</div>
<div class="du-info-item">
<span class="du-info-label">Size increase</span>
<span class="du-info-value" id="du-size-increase">—</span>
</div>
</div>

<div id="du-preview-wrap">
<img id="du-preview-img" src="" alt="Preview">
<div id="du-preview-label">Image preview</div>
</div>

<div class="du-output-block">
<div class="du-output-header">
<span class="du-output-title">Data URL (data:mime;base64,...)</span>
<button class="du-copy-btn" data-target="du-out-dataurl">Copy</button>
</div>
<textarea id="du-out-dataurl" readonly spellcheck="false" placeholder="Data URL will appear here..."></textarea>
</div>

<div class="du-output-block">
<div class="du-output-header">
<span class="du-output-title">Base64 string only</span>
<button class="du-copy-btn" data-target="du-out-b64">Copy</button>
</div>
<textarea id="du-out-b64" readonly spellcheck="false" placeholder="Base64 string will appear here..."></textarea>
</div>

<div class="du-output-block">
<div class="du-output-header">
<span class="du-output-title">CSS background-image</span>
<button class="du-copy-btn" data-target="du-out-css">Copy</button>
</div>
<textarea id="du-out-css" readonly spellcheck="false" rows="2"></textarea>
</div>

<div class="du-output-block" id="du-img-src-block" style="display:none">
<div class="du-output-header">
<span class="du-output-title">HTML &lt;img&gt; src</span>
<button class="du-copy-btn" data-target="du-out-html">Copy</button>
</div>
<textarea id="du-out-html" readonly spellcheck="false" rows="2"></textarea>
</div>

<div class="du-output-block" id="du-font-block" style="display:none">
<div class="du-output-header">
<span class="du-output-title">CSS @font-face src</span>
<button class="du-copy-btn" data-target="du-out-font">Copy</button>
</div>
<textarea id="du-out-font" readonly spellcheck="false" rows="3"></textarea>
</div>

<div id="du-enc-actions">
<button class="du-btn-secondary" id="du-reset-btn">Convert another file</button>
</div>
</div>
</div>

<!-- DECODE PANEL -->
<div class="du-panel" id="du-dec-panel">
<label for="du-paste-area">Paste a data URL or bare Base64 string:</label>
<textarea id="du-paste-area" spellcheck="false" placeholder="data:image/png;base64,iVBORw0KGgo..."></textarea>
<button id="du-dec-btn">Decode &amp; Download</button>
<div id="du-dec-error"></div>

<div id="du-dec-results">
<div id="du-dec-info">
<div class="du-info-item">
<span class="du-info-label">Detected MIME</span>
<span class="du-info-value" id="du-dec-mime">—</span>
</div>
<div class="du-info-item">
<span class="du-info-label">Decoded size</span>
<span class="du-info-value" id="du-dec-size">—</span>
</div>
</div>
<div id="du-dec-preview-wrap">
<img id="du-dec-preview-img" src="" alt="Decoded image preview">
<div id="du-dec-preview-label">Decoded image preview</div>
</div>
<a id="du-download-btn" href="#" download="decoded-file">⬇ Download file</a>
</div>
</div>

<!-- Common use cases -->
<div id="du-usecases">
<h3>Common use cases</h3>
<ul>
<li>CSS background-image</li>
<li>HTML img src</li>
<li>Font embedding (@font-face)</li>
<li>SVG embedding</li>
<li>Email templates</li>
<li>JSON / API payloads</li>
<li>Offline web apps</li>
<li>Favicon embedding</li>
</ul>
</div>

<script>
(function () {
'use strict';

/* ── Helpers ── */
function fmtBytes(n) {
if (n < 1024) return n + ' B';
if (n < 1048576) return (n / 1024).toFixed(1) + ' KB';
return (n / 1048576).toFixed(2) + ' MB';
}

function isImageMime(mime) {
return mime && mime.startsWith('image/');
}

function isFontMime(mime) {
return mime && (
mime.startsWith('font/') ||
mime === 'application/font-woff' ||
mime === 'application/font-woff2' ||
mime === 'application/x-font-ttf' ||
mime === 'application/x-font-opentype' ||
mime === 'application/vnd.ms-fontobject'
);
}

function guessMimeFromExt(filename) {
var ext = (filename.split('.').pop() || '').toLowerCase();
var map = {
'png':'image/png','jpg':'image/jpeg','jpeg':'image/jpeg',
'gif':'image/gif','webp':'image/webp','svg':'image/svg+xml',
'ico':'image/x-icon','avif':'image/avif','bmp':'image/bmp',
'woff':'font/woff','woff2':'font/woff2','ttf':'font/ttf',
'otf':'font/otf','eot':'application/vnd.ms-fontobject',
'pdf':'application/pdf','json':'application/json',
'mp4':'video/mp4','webm':'video/webm','mp3':'audio/mpeg',
'wav':'audio/wav','ogg':'audio/ogg'
};
return map[ext] || 'application/octet-stream';
}

function guessFontFormat(mime) {
var m = {
'font/woff':'woff','font/woff2':'woff2','font/ttf':'truetype',
'font/otf':'opentype','application/font-woff':'woff',
'application/font-woff2':'woff2','application/x-font-ttf':'truetype',
'application/vnd.ms-fontobject':'embedded-opentype'
};
return m[mime] || 'truetype';
}

/* ── ENCODE TAB ── */
var dropZone   = document.getElementById('du-drop-zone');
var fileInput  = document.getElementById('du-file-input');
var encResults = document.getElementById('du-enc-results');
var resetBtn   = document.getElementById('du-reset-btn');

function processFile(file) {
var mime = file.type || guessMimeFromExt(file.name);
var reader = new FileReader();
reader.onload = function (e) {
var dataUrl = e.target.result;
var b64 = dataUrl.split(',')[1] || '';

/* info bar */
document.getElementById('du-fname').textContent      = file.name;
document.getElementById('du-mime').textContent       = mime;
document.getElementById('du-orig-size').textContent  = fmtBytes(file.size);
document.getElementById('du-enc-size').textContent   = fmtBytes(b64.length);
var pct = ((b64.length / file.size - 1) * 100).toFixed(1);
document.getElementById('du-size-increase').textContent = '+' + pct + '%';

/* outputs */
document.getElementById('du-out-dataurl').value = dataUrl;
document.getElementById('du-out-b64').value     = b64;
document.getElementById('du-out-css').value     = 'background-image: url("' + dataUrl + '");';

/* image-specific */
var imgBlock = document.getElementById('du-img-src-block');
var prevWrap = document.getElementById('du-preview-wrap');
if (isImageMime(mime)) {
document.getElementById('du-out-html').value = '<img src="' + dataUrl + '" alt="' + file.name.replace(/"/g, '&quot;') + '">';
imgBlock.style.display = '';
document.getElementById('du-preview-img').src = dataUrl;
prevWrap.style.display = '';
} else {
imgBlock.style.display = 'none';
prevWrap.style.display = 'none';
document.getElementById('du-preview-img').src = '';
}

/* font-specific */
var fontBlock = document.getElementById('du-font-block');
if (isFontMime(mime)) {
var fmt = guessFontFormat(mime);
document.getElementById('du-out-font').value =
'@font-face {\n  font-family: "MyFont";\n  src: url("' + dataUrl + '") format("' + fmt + '");\n}';
fontBlock.style.display = '';
} else {
fontBlock.style.display = 'none';
}

dropZone.style.display   = 'none';
encResults.style.display = 'block';
};
reader.readAsDataURL(file);
}

/* Drag & drop */
dropZone.addEventListener('dragover', function (e) {
e.preventDefault();
dropZone.classList.add('du-dragover');
});
dropZone.addEventListener('dragleave', function () {
dropZone.classList.remove('du-dragover');
});
dropZone.addEventListener('drop', function (e) {
e.preventDefault();
dropZone.classList.remove('du-dragover');
var file = e.dataTransfer.files[0];
if (file) processFile(file);
});

/* File picker */
fileInput.addEventListener('change', function () {
if (fileInput.files[0]) processFile(fileInput.files[0]);
});

/* Copy buttons */
document.getElementById('du-enc-panel').addEventListener('click', function (e) {
var btn = e.target.closest('.du-copy-btn');
if (!btn) return;
var ta = document.getElementById(btn.getAttribute('data-target'));
if (!ta) return;
navigator.clipboard.writeText(ta.value).then(function () {
var orig = btn.textContent;
btn.textContent = 'Copied!';
btn.classList.add('du-copied');
setTimeout(function () { btn.textContent = orig; btn.classList.remove('du-copied'); }, 2000);
}).catch(function () { ta.select(); document.execCommand('copy'); });
});

/* Reset */
resetBtn.addEventListener('click', function () {
fileInput.value              = '';
encResults.style.display     = 'none';
dropZone.style.display       = '';
document.getElementById('du-preview-img').src = '';
document.getElementById('du-preview-wrap').style.display = 'none';
['du-out-dataurl','du-out-b64','du-out-css','du-out-html','du-out-font'].forEach(function (id) {
var el = document.getElementById(id); if (el) el.value = '';
});
});

/* ── DECODE TAB ── */
var decBtn     = document.getElementById('du-dec-btn');
var pasteArea  = document.getElementById('du-paste-area');
var decError   = document.getElementById('du-dec-error');
var decResults = document.getElementById('du-dec-results');
var dlBtn      = document.getElementById('du-download-btn');

function showDecError(msg) {
decError.textContent    = msg;
decError.style.display  = 'block';
decResults.style.display = 'none';
}

decBtn.addEventListener('click', function () {
decError.style.display   = 'none';
decResults.style.display = 'none';
var raw = pasteArea.value.trim();
if (!raw) { showDecError('Please paste a data URL or Base64 string.'); return; }

var mime, b64;

if (raw.startsWith('data:')) {
var comma = raw.indexOf(',');
if (comma === -1) { showDecError('Invalid data URL: no comma separator found.'); return; }
var header = raw.slice(5, comma);  /* mime;base64 */
b64  = raw.slice(comma + 1);
mime = header.split(';')[0] || 'application/octet-stream';
} else {
/* Bare base64 — accept it, guess octet-stream */
b64  = raw;
mime = 'application/octet-stream';
}

/* Validate base64 chars (allow padding whitespace) */
var cleaned = b64.replace(/\s/g, '');
if (!/^[A-Za-z0-9+/]+=*$/.test(cleaned)) {
showDecError('Invalid Base64 characters detected. Please check your input.');
return;
}

var byteCount;
try {
var binary = atob(cleaned);
byteCount  = binary.length;
} catch (err) {
showDecError('Failed to decode Base64: ' + err.message);
return;
}

var fullDataUrl = raw.startsWith('data:') ? raw : ('data:application/octet-stream;base64,' + cleaned);

document.getElementById('du-dec-mime').textContent = mime;
document.getElementById('du-dec-size').textContent = fmtBytes(byteCount);

/* Preview if image */
var decPrev = document.getElementById('du-dec-preview-wrap');
if (isImageMime(mime)) {
document.getElementById('du-dec-preview-img').src = fullDataUrl;
decPrev.style.display = '';
} else {
decPrev.style.display = 'none';
}

/* Determine filename */
var extMap = {
'image/png':'png','image/jpeg':'jpg','image/gif':'gif','image/webp':'webp',
'image/svg+xml':'svg','image/x-icon':'ico','image/avif':'avif',
'font/woff':'woff','font/woff2':'woff2','font/ttf':'ttf','font/otf':'otf',
'application/pdf':'pdf','application/json':'json','video/mp4':'mp4',
'audio/mpeg':'mp3'
};
var ext = extMap[mime] || 'bin';
dlBtn.href     = fullDataUrl;
dlBtn.download = 'decoded-file.' + ext;

decResults.style.display = 'block';
});
})();
</script>
</div>

---

## How to use

### File to Data URL
1. Drag and drop any file onto the upload zone, or click to open the file picker.
2. The tool reads the file using the browser **FileReader API** — nothing is sent to any server.
3. Copy the output format you need: full data URL, bare Base64, CSS `background-image`, HTML `<img>` tag, or CSS `@font-face` (for font files).

### Data URL to File
1. Switch to the **Data URL → File** tab.
2. Paste your `data:mime;base64,...` string (or a bare Base64 string).
3. Click **Decode & Download** to save the original file.

## Output formats

| Format | When to use |
|---|---|
| **Data URL** | Direct value for `src`, `href`, or `url()` |
| **Base64 string** | APIs, databases, JSON payloads |
| **CSS background-image** | Paste straight into a stylesheet |
| **HTML `<img>` tag** | Paste straight into HTML |
| **CSS @font-face** | Embed a web font without external requests |

## Why use data URLs?

Embedding a file as a Base64 data URI lets you ship a **self-contained** HTML file, email template, or CSS stylesheet with no external HTTP requests. Common scenarios:

- **SVG icons in CSS** — no extra network round-trip
- **Fonts in email** — some clients block external resources
- **Offline web apps** — embed assets directly in the app shell
- **API payloads** — pass binary data as JSON strings
- **Favicon embedding** — inline tiny icons without a separate file

The trade-off is roughly a **~33% size increase** (every 3 bytes become 4 Base64 characters). Keep embedded assets small — under ~50 KB is a good rule of thumb for production use.

## Privacy

All conversion happens entirely **in your browser** using the FileReader and atob/btoa APIs. No file data is ever sent to a server.

---

**Related tools:** [Base64 Encoder / Decoder](/tools/base64-encoder/) · [Image to Base64](/tools/image-to-base64/) · [Base64 to Image](/tools/base64-to-image/)
