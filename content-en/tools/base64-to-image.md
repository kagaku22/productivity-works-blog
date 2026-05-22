---
title: "Base64 to Image Converter"
slug: "base64-to-image"
date: 2025-05-16
description: "Free Base64 to image converter. Paste a Base64 string and preview the decoded image — download as PNG, JPEG, or other formats instantly."
categories: ["Free Tools"]
tags: ["Developer Tools", "Code Conversion", "Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/base64-to-image.png"
  alt: "Base64 to Image Converter tool screenshot"
---

Free, in-browser Base64 to image decoder. Paste any Base64 string — with or without a data URI prefix — and instantly preview, inspect, and download the decoded image. No upload, no server, no sign-up required.

<div id="bd-app">

<style>
#bd-app *,
#bd-app *::before,
#bd-app *::after {
box-sizing: border-box;
}
#bd-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1a1a2e;
}
#bd-app h2 {
font-size: 1.15rem;
font-weight: 600;
margin: 1.6rem 0 0.5rem;
color: #1a1a2e;
}
#bd-app .bd-row {
display: flex;
gap: 0.75rem;
flex-wrap: wrap;
align-items: center;
margin-bottom: 0.75rem;
}
#bd-app textarea {
width: 100%;
min-height: 160px;
padding: 0.75rem;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.8rem;
line-height: 1.5;
border: 1.5px solid #c8ccd4;
border-radius: 8px;
resize: vertical;
background: #f8f9fb;
color: #1a1a2e;
transition: border-color 0.2s;
}
#bd-app textarea:focus {
outline: none;
border-color: #4f6ef7;
background: #fff;
}
#bd-app textarea::placeholder {
color: #9aa0ad;
}
#bd-app button {
display: inline-flex;
align-items: center;
gap: 0.4rem;
padding: 0.55rem 1.15rem;
font-size: 0.9rem;
font-weight: 600;
border: none;
border-radius: 7px;
cursor: pointer;
transition: background 0.18s, opacity 0.18s;
}
#bd-app button:active { opacity: 0.82; }
#bd-app .bd-btn-primary {
background: #4f6ef7;
color: #fff;
}
#bd-app .bd-btn-primary:hover { background: #3a58e0; }
#bd-app .bd-btn-secondary {
background: #eef0f8;
color: #4f6ef7;
border: 1.5px solid #c8ccd4;
}
#bd-app .bd-btn-secondary:hover { background: #dde1f5; }
#bd-app .bd-btn-danger {
background: #fff0f0;
color: #d9534f;
border: 1.5px solid #f5c6c6;
}
#bd-app .bd-btn-danger:hover { background: #ffe0e0; }
#bd-app .bd-btn-green {
background: #1db954;
color: #fff;
}
#bd-app .bd-btn-green:hover { background: #17a348; }
#bd-app .bd-status {
padding: 0.55rem 0.85rem;
border-radius: 7px;
font-size: 0.875rem;
font-weight: 500;
margin-bottom: 0.75rem;
display: none;
}
#bd-app .bd-status.info  { display: block; background: #eef3ff; color: #3a58e0; border: 1px solid #c5d1fb; }
#bd-app .bd-status.error { display: block; background: #fff0f0; color: #c0392b; border: 1px solid #f5c6c6; }
#bd-app .bd-status.ok    { display: block; background: #eafaf1; color: #1a7a43; border: 1px solid #a9dfbf; }
#bd-app .bd-preview-box {
display: none;
border: 1.5px solid #c8ccd4;
border-radius: 10px;
overflow: hidden;
background: repeating-conic-gradient(#e0e0e0 0% 25%, #f8f8f8 0% 50%) 0 0 / 16px 16px;
text-align: center;
padding: 12px;
margin-bottom: 0.75rem;
min-height: 80px;
}
#bd-app .bd-preview-box img {
max-width: 100%;
max-height: 480px;
display: block;
margin: 0 auto;
border-radius: 4px;
box-shadow: 0 2px 12px rgba(0,0,0,0.12);
}
#bd-app .bd-meta {
display: none;
background: #f4f6fb;
border: 1.5px solid #dde2ef;
border-radius: 8px;
padding: 0.75rem 1rem;
font-size: 0.85rem;
margin-bottom: 0.75rem;
line-height: 1.7;
}
#bd-app .bd-meta span {
display: inline-block;
margin-right: 1.5rem;
}
#bd-app .bd-meta strong { color: #4f6ef7; }
#bd-app .bd-copy-uri {
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 0.78rem;
background: #f4f6fb;
border: 1.5px solid #dde2ef;
border-radius: 7px;
padding: 0.55rem 0.8rem;
width: 100%;
resize: none;
height: 3.8rem;
color: #444;
display: none;
margin-bottom: 0.4rem;
}
#bd-app .bd-divider {
border: none;
border-top: 1.5px solid #eaecf2;
margin: 1.4rem 0;
}
#bd-app .bd-how {
background: #f8f9fb;
border-radius: 10px;
padding: 1rem 1.2rem;
font-size: 0.88rem;
line-height: 1.75;
color: #444;
}
#bd-app .bd-how ol { margin: 0.4rem 0 0 1.2rem; padding: 0; }
#bd-app .bd-how li { margin-bottom: 0.25rem; }
#bd-app .bd-links {
display: flex;
gap: 0.75rem;
flex-wrap: wrap;
margin-top: 1.2rem;
}
#bd-app .bd-links a {
padding: 0.45rem 1rem;
background: #eef0f8;
color: #4f6ef7;
border-radius: 6px;
text-decoration: none;
font-size: 0.875rem;
font-weight: 500;
border: 1.5px solid #c8ccd4;
transition: background 0.15s;
}
#bd-app .bd-links a:hover { background: #dde1f5; }
</style>

<h2>Paste Base64 String</h2>

<textarea id="bd-input" placeholder="Paste your Base64 string here — data URI prefix (data:image/png;base64,...) is auto-detected and stripped"></textarea>

<div class="bd-row">
<button class="bd-btn-primary" onclick="bdDecode()">&#9654; Decode &amp; Preview</button>
<button class="bd-btn-secondary" onclick="bdPasteSample()">Load Sample</button>
<button class="bd-btn-danger" onclick="bdClear()">&#10005; Clear</button>
</div>

<div id="bd-status" class="bd-status"></div>

<div id="bd-preview-box" class="bd-preview-box">
<img id="bd-img" src="" alt="Decoded image preview" />
</div>

<div id="bd-meta" class="bd-meta">
<span>Format: <strong id="bd-fmt">—</strong></span>
<span>Dimensions: <strong id="bd-dims">—</strong></span>
<span>Decoded size: <strong id="bd-size">—</strong></span>
</div>

<div id="bd-action-row" class="bd-row" style="display:none">
<button class="bd-btn-green" onclick="bdDownload()">&#8595; Download Image</button>
<button class="bd-btn-secondary" onclick="bdCopyUri()">&#128203; Copy as Data URI</button>
</div>

<textarea id="bd-uri-out" class="bd-copy-uri" readonly></textarea>

<hr class="bd-divider" />

<h2>How it works</h2>
<div class="bd-how">
<ol>
<li>Paste a Base64-encoded string into the text area above.</li>
<li>The tool automatically strips any <code>data:image/...;base64,</code> prefix and removes whitespace/newlines.</li>
<li>It decodes the string in your browser, detects the image format (PNG, JPEG, GIF, WebP, SVG…), and renders a live preview.</li>
<li>Inspect the detected format, pixel dimensions, and decoded file size.</li>
<li>Download the image file or copy the full data URI to your clipboard.</li>
</ol>
</div>

<div class="bd-links">
<a href="/tools/image-to-base64/">&#8592; Image to Base64</a>
<a href="/tools/base64-encoder/">Base64 Encoder</a>
</div>

<script>
(function () {
'use strict';

// Minimal 1×1 red PNG for the sample
var SAMPLE = 'iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8z8BQDwADhQGAWjR9awAAAABJRU5ErkJggg==';

function showStatus(msg, type) {
var el = document.getElementById('bd-status');
el.textContent = msg;
el.className = 'bd-status ' + type;
}

function hideStatus() {
var el = document.getElementById('bd-status');
el.className = 'bd-status';
}

function formatBytes(n) {
if (n < 1024) return n + ' B';
if (n < 1024 * 1024) return (n / 1024).toFixed(1) + ' KB';
return (n / (1024 * 1024)).toFixed(2) + ' MB';
}

function detectMime(b64clean) {
// Decode first few bytes to detect magic
try {
var raw = atob(b64clean.substring(0, 16));
var bytes = [];
for (var i = 0; i < raw.length; i++) bytes.push(raw.charCodeAt(i));
if (bytes[0] === 0x89 && bytes[1] === 0x50) return 'image/png';
if (bytes[0] === 0xFF && bytes[1] === 0xD8) return 'image/jpeg';
if (bytes[0] === 0x47 && bytes[1] === 0x49) return 'image/gif';
if (bytes[0] === 0x52 && bytes[1] === 0x49 && bytes[8] === 0x57) return 'image/webp';
if (bytes[0] === 0x42 && bytes[1] === 0x4D) return 'image/bmp';
if (bytes[0] === 0x00 && bytes[1] === 0x00 && bytes[2] === 0x01) return 'image/x-icon';
} catch (e) {}
// Fallback: check if it looks like SVG text
var preview = atob(b64clean.substring(0, 64));
if (preview.indexOf('<svg') !== -1 || preview.indexOf('<?xml') !== -1) return 'image/svg+xml';
return 'image/png'; // safe default
}

function mimeToExt(mime) {
var map = {
'image/png': 'png',
'image/jpeg': 'jpg',
'image/gif': 'gif',
'image/webp': 'webp',
'image/bmp': 'bmp',
'image/svg+xml': 'svg',
'image/x-icon': 'ico'
};
return map[mime] || 'png';
}

function mimeToLabel(mime) {
var map = {
'image/png': 'PNG',
'image/jpeg': 'JPEG',
'image/gif': 'GIF',
'image/webp': 'WebP',
'image/bmp': 'BMP',
'image/svg+xml': 'SVG',
'image/x-icon': 'ICO'
};
return map[mime] || mime;
}

window.bdDecode = function () {
var raw = document.getElementById('bd-input').value.trim();
if (!raw) { showStatus('Please paste a Base64 string first.', 'info'); return; }

// Strip data URI prefix
var b64 = raw;
var detectedMime = null;
var prefixMatch = raw.match(/^data:([^;]+);base64,(.+)$/s);
if (prefixMatch) {
detectedMime = prefixMatch[1].trim();
b64 = prefixMatch[2].trim();
}

// Strip all whitespace and newlines
b64 = b64.replace(/\s+/g, '');

// Basic validation
if (!/^[A-Za-z0-9+/]+=*$/.test(b64)) {
showStatus('Invalid Base64 — unexpected characters found. Check your input.', 'error');
return;
}

var mime = detectedMime || detectMime(b64);
var dataUri = 'data:' + mime + ';base64,' + b64;

var img = document.getElementById('bd-img');
img.onload = function () {
// Decoded byte count: each Base64 char = 6 bits; padding = 0 bytes
var pad = (b64.slice(-2) === '==' ? 2 : b64.slice(-1) === '=' ? 1 : 0);
var byteLen = (b64.length * 3 / 4) - pad;

document.getElementById('bd-fmt').textContent = mimeToLabel(mime);
document.getElementById('bd-dims').textContent = img.naturalWidth + ' × ' + img.naturalHeight + ' px';
document.getElementById('bd-size').textContent = formatBytes(byteLen);

document.getElementById('bd-meta').style.display = 'block';
document.getElementById('bd-preview-box').style.display = 'block';
document.getElementById('bd-action-row').style.display = 'flex';
document.getElementById('bd-uri-out').style.display = 'none';

showStatus('Decoded successfully — format: ' + mimeToLabel(mime) + ', ' + img.naturalWidth + '×' + img.naturalHeight + ' px.', 'ok');
};
img.onerror = function () {
document.getElementById('bd-preview-box').style.display = 'none';
document.getElementById('bd-meta').style.display = 'none';
document.getElementById('bd-action-row').style.display = 'none';
showStatus('Could not render image. The Base64 data may be corrupted or an unsupported format.', 'error');
};
img.src = dataUri;
hideStatus();
};

window.bdDownload = function () {
var img = document.getElementById('bd-img');
if (!img.src) return;
var mimeMatch = img.src.match(/^data:([^;]+);/);
var mime = mimeMatch ? mimeMatch[1] : 'image/png';
var ext = mimeToExt(mime);
var a = document.createElement('a');
a.href = img.src;
a.download = 'decoded-image.' + ext;
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
};

window.bdCopyUri = function () {
var img = document.getElementById('bd-img');
if (!img.src) return;
var out = document.getElementById('bd-uri-out');
out.value = img.src;
out.style.display = 'block';
if (navigator.clipboard) {
navigator.clipboard.writeText(img.src).then(function () {
showStatus('Data URI copied to clipboard.', 'ok');
}).catch(function () {
out.select();
showStatus('Select the text above and copy manually.', 'info');
});
} else {
out.select();
try { document.execCommand('copy'); showStatus('Data URI copied to clipboard.', 'ok'); }
catch (e) { showStatus('Select the text above and copy manually.', 'info'); }
}
};

window.bdPasteSample = function () {
document.getElementById('bd-input').value = SAMPLE;
showStatus('Sample Base64 loaded (1×1 red PNG). Click Decode & Preview.', 'info');
};

window.bdClear = function () {
document.getElementById('bd-input').value = '';
document.getElementById('bd-img').src = '';
document.getElementById('bd-preview-box').style.display = 'none';
document.getElementById('bd-meta').style.display = 'none';
document.getElementById('bd-action-row').style.display = 'none';
document.getElementById('bd-uri-out').style.display = 'none';
document.getElementById('bd-uri-out').value = '';
hideStatus();
};
})();
</script>

</div>

---

## Related Tools

> [Base64 Encoder](/tools/base64-encoder/)
> [Encoder Decoder](/tools/encoder-decoder/)
> [Hash Generator](/tools/hash-generator/)

