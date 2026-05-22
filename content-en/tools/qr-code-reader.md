---
title: "QR Code Generator"
date: 2025-05-16
description: "Free online QR code generator. Create scannable QR codes from any text or URL. Customize size and colors, then download as PNG. No sign-up required."
categories: ["Free Tools"]
tags: ["Developer Tools", "Code Conversion", "Free Tools"]
slug: "qr-code-generator"
ShowToc: false
cover:
  image: "/images/covers/qr-code-generator.png"
  alt: "QR Code Generator"
---

<div id="qr-app">

<style>
#qr-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 740px;
margin: 0 auto;
color: #1e293b;
}
#qr-app h2.qr-section-title {
font-size: 1.05rem;
font-weight: 700;
color: #0f172a;
margin: 22px 0 10px;
padding-bottom: 5px;
border-bottom: 2px solid #e2e8f0;
}
#qr-app .qr-card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 20px;
margin-bottom: 16px;
}
#qr-app label.qr-label {
display: block;
font-size: 13px;
font-weight: 600;
color: #475569;
margin-bottom: 5px;
}
#qr-app textarea.qr-textarea,
#qr-app input.qr-input,
#qr-app select.qr-select {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
background: #fff;
color: #1e293b;
box-sizing: border-box;
margin-bottom: 12px;
transition: border-color 0.2s;
font-family: inherit;
}
#qr-app textarea.qr-textarea { resize: vertical; min-height: 80px; }
#qr-app textarea.qr-textarea:focus,
#qr-app input.qr-input:focus,
#qr-app select.qr-select:focus {
outline: none;
border-color: #3b82f6;
}
#qr-app .qr-row {
display: flex;
gap: 14px;
flex-wrap: wrap;
}
#qr-app .qr-row > div { flex: 1; min-width: 150px; }
#qr-app .qr-color-row {
display: flex;
gap: 14px;
flex-wrap: wrap;
align-items: flex-end;
margin-bottom: 12px;
}
#qr-app .qr-color-group { flex: 1; min-width: 130px; }
#qr-app .qr-color-group label.qr-label { margin-bottom: 4px; }
#qr-app .qr-color-input-wrap {
display: flex;
align-items: center;
gap: 8px;
}
#qr-app .qr-color-swatch {
width: 36px; height: 36px;
border-radius: 6px;
border: 1.5px solid #cbd5e1;
cursor: pointer;
padding: 0;
background: none;
}
#qr-app .qr-color-hex {
width: 90px;
padding: 6px 8px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
font-family: monospace;
background: #fff;
color: #1e293b;
}
#qr-app .qr-btn {
display: inline-block;
padding: 10px 22px;
border-radius: 7px;
font-size: 14px;
font-weight: 600;
cursor: pointer;
border: none;
transition: background 0.2s, opacity 0.2s;
}
#qr-app .qr-btn-primary {
background: #3b82f6;
color: #fff;
}
#qr-app .qr-btn-primary:hover { background: #2563eb; }
#qr-app .qr-btn-secondary {
background: #e2e8f0;
color: #1e293b;
}
#qr-app .qr-btn-secondary:hover { background: #cbd5e1; }
#qr-app .qr-btn-green {
background: #22c55e;
color: #fff;
}
#qr-app .qr-btn-green:hover { background: #16a34a; }
#qr-app .qr-output-area {
text-align: center;
padding: 24px 16px;
}
#qr-app canvas#qr-canvas {
display: block;
margin: 0 auto 16px;
border: 1px solid #e2e8f0;
border-radius: 8px;
image-rendering: pixelated;
}
#qr-app .qr-char-count {
font-size: 12px;
color: #64748b;
text-align: right;
margin-top: -10px;
margin-bottom: 10px;
}
#qr-app .qr-error-msg {
background: #fef2f2;
border: 1px solid #fca5a5;
border-radius: 8px;
color: #dc2626;
padding: 10px 14px;
font-size: 13px;
margin-bottom: 12px;
display: none;
}
#qr-app .qr-info-bar {
font-size: 12px;
color: #64748b;
margin-bottom: 10px;
}
#qr-app .qr-history-list {
list-style: none;
padding: 0;
margin: 0;
}
#qr-app .qr-history-list li {
display: flex;
align-items: center;
justify-content: space-between;
padding: 8px 10px;
border-bottom: 1px solid #f1f5f9;
font-size: 13px;
gap: 8px;
}
#qr-app .qr-history-list li:last-child { border-bottom: none; }
#qr-app .qr-history-text {
flex: 1;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
color: #334155;
cursor: pointer;
}
#qr-app .qr-history-text:hover { color: #3b82f6; text-decoration: underline; }
#qr-app .qr-history-del {
background: none;
border: none;
color: #94a3b8;
cursor: pointer;
font-size: 16px;
padding: 0 4px;
line-height: 1;
}
#qr-app .qr-history-del:hover { color: #ef4444; }
#qr-app .qr-empty-history {
text-align: center;
color: #94a3b8;
font-size: 13px;
padding: 16px 0;
}
#qr-app .qr-ec-info {
display: flex;
gap: 8px;
flex-wrap: wrap;
margin-bottom: 12px;
}
#qr-app .qr-ec-badge {
padding: 4px 10px;
border-radius: 20px;
font-size: 12px;
font-weight: 600;
background: #f1f5f9;
color: #475569;
border: 1.5px solid #e2e8f0;
cursor: pointer;
transition: all 0.15s;
}
#qr-app .qr-ec-badge.active {
background: #3b82f6;
color: #fff;
border-color: #3b82f6;
}
@media (max-width: 500px) {
#qr-app .qr-row > div { min-width: 100%; }
#qr-app .qr-color-group { min-width: 100%; }
}
</style>

<h2 class="qr-section-title">QR Code Generator</h2>

<div class="qr-card">
<label class="qr-label" for="qr-text">Text or URL</label>
<textarea class="qr-textarea" id="qr-text" placeholder="Enter text, URL, phone number, email..." maxlength="2953"></textarea>
<div class="qr-char-count"><span id="qr-char-cur">0</span> / 2953 characters</div>

<div class="qr-row">
<div>
<label class="qr-label" for="qr-size">Output Size</label>
<select class="qr-select" id="qr-size">
<option value="200">200 × 200 px</option>
<option value="300" selected>300 × 300 px</option>
<option value="400">400 × 400 px</option>
<option value="500">500 × 500 px</option>
</select>
</div>
<div>
<label class="qr-label">Error Correction</label>
<div class="qr-ec-info">
<span class="qr-ec-badge active" data-ec="L">L — 7%</span>
<span class="qr-ec-badge" data-ec="M">M — 15%</span>
<span class="qr-ec-badge" data-ec="Q">Q — 25%</span>
<span class="qr-ec-badge" data-ec="H">H — 30%</span>
</div>
</div>
</div>

<div class="qr-color-row">
<div class="qr-color-group">
<label class="qr-label">Foreground Color</label>
<div class="qr-color-input-wrap">
<input type="color" class="qr-color-swatch" id="qr-fg-picker" value="#000000">
<input type="text" class="qr-color-hex" id="qr-fg-hex" value="#000000" maxlength="7">
</div>
</div>
<div class="qr-color-group">
<label class="qr-label">Background Color</label>
<div class="qr-color-input-wrap">
<input type="color" class="qr-color-swatch" id="qr-bg-picker" value="#ffffff">
<input type="text" class="qr-color-hex" id="qr-bg-hex" value="#ffffff" maxlength="7">
</div>
</div>
</div>

<div class="qr-error-msg" id="qr-error"></div>

<div style="display:flex;gap:10px;flex-wrap:wrap;">
<button class="qr-btn qr-btn-primary" id="qr-generate-btn">Generate QR Code</button>
<button class="qr-btn qr-btn-secondary" id="qr-clear-btn">Clear</button>
</div>
</div>

<div class="qr-card" id="qr-output-card" style="display:none;">
<h2 class="qr-section-title" style="margin-top:0;">Generated QR Code</h2>
<div class="qr-output-area">
<canvas id="qr-canvas"></canvas>
<div class="qr-info-bar" id="qr-info-bar"></div>
<div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
<button class="qr-btn qr-btn-green" id="qr-download-btn">Download PNG</button>
<button class="qr-btn qr-btn-secondary" id="qr-copy-btn">Copy to Clipboard</button>
</div>
</div>
</div>

<div class="qr-card" id="qr-history-card">
<h2 class="qr-section-title" style="margin-top:0;">History</h2>
<ul class="qr-history-list" id="qr-history-list">
<li><div class="qr-empty-history">No QR codes generated yet.</div></li>
</ul>
<div style="text-align:right;margin-top:6px;">
<button class="qr-btn qr-btn-secondary" id="qr-clear-history-btn" style="font-size:12px;padding:6px 14px;">Clear History</button>
</div>
</div>

<script>
(function() {
'use strict';

// ─── GF(256) Arithmetic ───────────────────────────────────────────────────────
var GF_EXP = new Uint8Array(512);
var GF_LOG  = new Uint8Array(256);
(function(){
var x = 1;
for (var i = 0; i < 255; i++) {
GF_EXP[i] = x;
GF_LOG[x] = i;
x <<= 1;
if (x & 0x100) x ^= 0x11d;
}
for (var i = 255; i < 512; i++) GF_EXP[i] = GF_EXP[i - 255];
})();

function gfMul(a, b) {
if (a === 0 || b === 0) return 0;
return GF_EXP[(GF_LOG[a] + GF_LOG[b]) % 255];
}
function gfPow(x, power) {
return GF_EXP[(GF_LOG[x] * power) % 255];
}

function rsGeneratorPoly(degree) {
var poly = [1];
for (var i = 0; i < degree; i++) {
var term = [1, GF_EXP[i]];
var res = new Array(poly.length + term.length - 1).fill(0);
for (var j = 0; j < poly.length; j++)
for (var k = 0; k < term.length; k++)
res[j + k] ^= gfMul(poly[j], term[k]);
poly = res;
}
return poly;
}

function rsEncode(data, ecLen) {
var gen = rsGeneratorPoly(ecLen);
var msg = data.slice();
for (var i = 0; i < ecLen; i++) msg.push(0);
for (var i = 0; i < data.length; i++) {
var coef = msg[i];
if (coef !== 0) {
for (var j = 0; j < gen.length; j++)
msg[i + j] ^= gfMul(gen[j], coef);
}
}
return msg.slice(data.length);
}

// ─── QR Code Spec Tables ──────────────────────────────────────────────────────
// EC codewords and blocks per version (1-40), per EC level L/M/Q/H
// Format: [ecPerBlock, blocks1, dataPerBlock1, blocks2, dataPerBlock2]
var EC_TABLE = {
L: [
null, // index 0 unused
[7,1,19,0,0],[10,1,34,0,0],[15,1,55,0,0],[20,1,80,0,0],[26,1,108,0,0],
[18,2,68,0,0],[20,2,78,0,0],[24,2,97,0,0],[30,2,116,0,0],[18,2,68,2,69],
[20,4,81,0,0],[24,2,92,2,93],[26,4,107,0,0],[30,3,115,1,116],[22,5,87,1,88],
[24,5,98,1,99],[28,1,107,5,108],[30,5,120,1,121],[28,3,113,4,114],[28,3,107,5,108],
[28,4,116,4,117],[28,2,111,7,112],[30,4,121,5,122],[30,6,117,4,118],[26,8,106,4,107],
[28,10,114,2,115],[30,8,122,4,123],[30,3,117,10,118],[30,7,116,7,117],[30,5,115,10,116],
[30,13,115,3,116],[30,17,115,0,0],[30,17,115,1,116],[30,13,115,6,116],[30,12,121,7,122],
[30,6,121,14,122],[30,17,122,4,123],[30,4,122,18,123],[30,20,117,4,118],[30,19,118,6,119]
],
M: [
null,
[10,1,16,0,0],[16,1,28,0,0],[26,1,44,0,0],[18,2,32,0,0],[24,2,43,0,0],
[16,4,27,0,0],[18,4,31,0,0],[22,2,38,2,39],[22,3,36,2,37],[26,4,43,1,44],
[30,1,50,4,51],[22,6,36,2,37],[22,8,37,1,38],[24,4,40,5,41],[24,5,41,5,42],
[28,7,45,3,46],[28,10,46,1,47],[26,9,43,4,44],[26,3,44,11,45],[26,3,41,13,42],
[26,17,42,0,0],[28,17,46,0,0],[28,4,47,14,48],[28,6,45,14,46],[28,8,46,13,47],
[28,19,46,4,47],[28,22,45,3,46],[28,3,45,23,46],[28,21,45,7,46],[28,19,45,10,46],
[28,2,45,29,46],[28,10,45,23,46],[28,14,45,21,46],[28,14,46,21,47],[28,12,45,26,46],
[28,6,45,34,46],[28,29,45,14,46],[28,13,45,32,46],[28,40,45,7,46],[28,18,45,31,46]
],
Q: [
null,
[13,1,13,0,0],[22,1,22,0,0],[18,2,17,0,0],[26,2,24,0,0],[18,2,15,2,16],
[24,4,19,0,0],[18,2,14,4,15],[22,4,18,2,19],[20,4,16,4,17],[24,6,19,2,20],
[28,4,22,6,23],[26,4,20,6,21],[24,8,20,4,21],[20,11,16,5,17],[30,5,24,7,25],
[24,15,19,2,20],[28,1,22,15,23],[28,17,22,1,23],[26,17,21,4,22],[30,15,24,5,25],
[28,17,22,6,23],[30,7,24,16,25],[30,11,24,14,25],[30,11,24,16,25],[30,7,24,22,25],
[28,28,22,6,23],[30,8,23,26,24],[30,4,24,31,25],[30,1,23,37,24],[30,15,24,25,25],
[30,42,24,1,25],[30,10,24,35,25],[30,29,24,19,25],[30,44,24,7,25],[30,39,24,14,25],
[30,46,24,10,25],[30,49,24,10,25],[30,48,24,14,25],[30,43,24,22,25],[30,34,24,34,25]
],
H: [
null,
[17,1,9,0,0],[28,1,16,0,0],[22,2,13,0,0],[16,4,9,0,0],[22,2,11,2,12],
[28,4,15,0,0],[26,4,13,1,14],[26,4,14,2,15],[24,4,12,4,13],[28,6,15,2,16],
[24,3,12,8,13],[28,7,14,4,15],[22,11,11,5,12],[30,11,12,5,13],[24,11,12,7,13],
[28,3,15,13,16],[28,2,14,17,15],[28,2,14,19,15],[26,9,13,16,14],[28,15,15,10,16],
[30,19,16,6,17],[24,34,13,0,0],[30,16,15,14,16],[28,30,16,2,17],[30,22,15,13,16],
[30,33,15,4,16],[30,12,15,28,16],[30,11,15,31,16],[30,19,15,26,16],[30,23,15,25,16],
[30,23,15,28,16],[30,19,15,35,16],[30,11,15,46,16],[30,59,16,1,17],[30,22,15,41,16],
[30,2,15,64,16],[30,24,15,46,16],[30,42,15,32,16],[30,10,15,67,16],[30,20,15,61,16]
]
};

// Number of data codewords per version/EC level
function getDataCapacity(ver, ecLevel) {
var row = EC_TABLE[ecLevel][ver];
return row[1] * row[2] + row[3] * row[4];
}

// Alignment pattern centers per version
var ALIGN_POS = [
null,[],[6,18],[6,22],[6,26],[6,30],[6,34],
[6,22,38],[6,24,42],[6,26,46],[6,28,50],[6,30,54],
[6,32,58],[6,34,62],[6,26,46,66],[6,26,48,70],[6,26,50,74],
[6,30,54,78],[6,30,56,82],[6,30,58,86],[6,34,62,90],
[6,28,50,72,94],[6,26,50,74,98],[6,30,54,78,102],[6,28,54,80,106],
[6,32,58,84,110],[6,30,58,86,114],[6,34,62,90,118],
[6,26,50,74,98,122],[6,30,54,78,102,126],[6,26,52,78,104,130],
[6,30,56,82,108,132],[6,34,60,86,112,136],[6,30,58,86,114,142],
[6,34,62,90,118,146],[6,30,54,78,102,126,150],
[6,24,50,76,102,128,154],[6,28,54,80,106,132,158],
[6,32,58,84,110,136,162],[6,26,54,82,110,138,166],
[6,30,58,86,114,142,170]
];

// Format info strings (15-bit, EC+mask) pre-computed for all EC levels + 8 masks
// These include BCH error correction
var FORMAT_INFO = {
L: [0x77c4,0x72f3,0x7daa,0x789d,0x662f,0x6318,0x6c41,0x6976],
M: [0x5412,0x5125,0x5e7c,0x5b4b,0x45f9,0x40ce,0x4f97,0x4aa0],
Q: [0x355f,0x3068,0x3f31,0x3a06,0x24b4,0x2183,0x2eda,0x2bed],
H: [0x1689,0x13be,0x1ce7,0x19d0,0x0762,0x0255,0x0d0c,0x083b]
};

// Version info (18-bit) for versions 7+
var VERSION_INFO = [
null,null,null,null,null,null,null,
0x07c94,0x085bc,0x09a99,0x0a4d3,0x0bbf6,0x0c762,0x0d847,0x0e60d,0x0f928,
0x10b78,0x1145d,0x12a17,0x13532,0x149a6,0x15683,0x168c9,0x177ec,
0x18ec4,0x191e1,0x1afab,0x1b08e,0x1cc1a,0x1d33f,0x1ed75,0x1f250,
0x209d5,0x216f0,0x228ba,0x2379f,0x24b0b,0x2542e,0x26a64,0x27541,
0x28c69
];

// ─── QR Encoder ──────────────────────────────────────────────────────────────
function QRCode(text, ecLevel) {
this.text = text;
this.ecLevel = ecLevel || 'M';
this.version = 1;
this.modules = null;
this.size = 0;
this._encode();
}

QRCode.prototype._encode = function() {
var data = this._encodeData();
this.modules = this._buildMatrix(data);
};

QRCode.prototype._encodeData = function() {
var text = this.text;
var ecLevel = this.ecLevel;

// Determine mode: numeric, alphanumeric, or byte
var mode = this._chooseMode(text);
var modeIndicator = { numeric: 0x1, alphanumeric: 0x2, byte: 0x4 };

// Find minimum version
var ver = 1;
for (ver = 1; ver <= 40; ver++) {
var cap = getDataCapacity(ver, ecLevel);
var len = this._encodedLength(text, mode, ver);
if (Math.ceil(len / 8) <= cap) break;
}
if (ver > 40) throw new Error('Data too long for QR code');
this.version = ver;
this.size = ver * 4 + 17;

// Build data bit stream
var bits = [];
var push = function(val, count) {
for (var i = count - 1; i >= 0; i--)
bits.push((val >> i) & 1);
};

// Mode indicator
push(modeIndicator[mode], 4);

// Character count indicator
var ccBits = this._ccBits(mode, ver);
push(text.length, ccBits);

// Data
if (mode === 'numeric') {
for (var i = 0; i < text.length; ) {
var chunk = text.slice(i, i + 3);
var digits = chunk.length;
push(parseInt(chunk, 10), digits === 3 ? 10 : digits === 2 ? 7 : 4);
i += 3;
}
} else if (mode === 'alphanumeric') {
var ANC = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ $%*+-./:';
for (var i = 0; i < text.length; ) {
if (i + 1 < text.length) {
push(ANC.indexOf(text[i]) * 45 + ANC.indexOf(text[i+1]), 11);
i += 2;
} else {
push(ANC.indexOf(text[i]), 6);
i++;
}
}
} else { // byte
var bytes = this._toUTF8(text);
for (var i = 0; i < bytes.length; i++)
push(bytes[i], 8);
}

// Terminator
var totalBits = getDataCapacity(ver, ecLevel) * 8;
for (var i = 0; i < 4 && bits.length < totalBits; i++) bits.push(0);

// Pad to byte boundary
while (bits.length % 8 !== 0) bits.push(0);

// Pad codewords
var padBytes = [0xec, 0x11];
var pi = 0;
while (bits.length < totalBits) {
push(padBytes[pi % 2], 8);
pi++;
}

// Convert bits to bytes
var dataBytes = [];
for (var i = 0; i < bits.length; i += 8) {
var b = 0;
for (var j = 0; j < 8; j++) b = (b << 1) | bits[i + j];
dataBytes.push(b);
}

// Interleave data and EC codewords per QR spec
var row = EC_TABLE[ecLevel][ver];
var ecPerBlock = row[0];
var blocks1 = row[1], dataPerBlock1 = row[2];
var blocks2 = row[3], dataPerBlock2 = row[4];
var totalBlocks = blocks1 + blocks2;

// Split into blocks
var blocks = [];
var offset = 0;
for (var b = 0; b < blocks1; b++) {
blocks.push(dataBytes.slice(offset, offset + dataPerBlock1));
offset += dataPerBlock1;
}
for (var b = 0; b < blocks2; b++) {
blocks.push(dataBytes.slice(offset, offset + dataPerBlock2));
offset += dataPerBlock2;
}

// Generate EC for each block
var ecBlocks = blocks.map(function(blk) { return rsEncode(blk, ecPerBlock); });

// Interleave data codewords
var result = [];
var maxData = Math.max(dataPerBlock1, dataPerBlock2);
for (var i = 0; i < maxData; i++)
for (var b = 0; b < blocks.length; b++)
if (i < blocks[b].length) result.push(blocks[b][i]);

// Interleave EC codewords
for (var i = 0; i < ecPerBlock; i++)
for (var b = 0; b < ecBlocks.length; b++)
result.push(ecBlocks[b][i]);

return result;
};

QRCode.prototype._chooseMode = function(text) {
if (/^\d+$/.test(text)) return 'numeric';
if (/^[0-9A-Z $%*+\-./:]+$/.test(text)) return 'alphanumeric';
return 'byte';
};

QRCode.prototype._ccBits = function(mode, ver) {
var table = {
numeric:      [10, 12, 14],
alphanumeric: [9, 11, 13],
byte:         [8, 16, 16]
};
var idx = ver <= 9 ? 0 : ver <= 26 ? 1 : 2;
return table[mode][idx];
};

QRCode.prototype._encodedLength = function(text, mode, ver) {
var ccBits = this._ccBits(mode, ver);
if (mode === 'numeric') {
var full = Math.floor(text.length / 3);
var rem  = text.length % 3;
return 4 + ccBits + full * 10 + (rem === 2 ? 7 : rem === 1 ? 4 : 0);
} else if (mode === 'alphanumeric') {
return 4 + ccBits + Math.floor(text.length / 2) * 11 + (text.length % 2) * 6;
} else {
var bytes = this._toUTF8(text);
return 4 + ccBits + bytes.length * 8;
}
};

QRCode.prototype._toUTF8 = function(str) {
var bytes = [];
for (var i = 0; i < str.length; i++) {
var code = str.charCodeAt(i);
if (code < 0x80) {
bytes.push(code);
} else if (code < 0x800) {
bytes.push(0xc0 | (code >> 6), 0x80 | (code & 0x3f));
} else if (code >= 0xd800 && code <= 0xdbff && i + 1 < str.length) {
var hi = code, lo = str.charCodeAt(++i);
var cp = 0x10000 + ((hi - 0xd800) << 10) + (lo - 0xdc00);
bytes.push(0xf0|(cp>>18), 0x80|((cp>>12)&0x3f), 0x80|((cp>>6)&0x3f), 0x80|(cp&0x3f));
} else {
bytes.push(0xe0|(code>>12), 0x80|((code>>6)&0x3f), 0x80|(code&0x3f));
}
}
return bytes;
};

QRCode.prototype._buildMatrix = function(data) {
var ver = this.version;
var size = this.size;
var N = size;

// Matrix: true = dark, false = light, null = unset
var mat = [];
var func = []; // functional module (cannot be overwritten by data)
for (var r = 0; r < N; r++) {
mat.push(new Array(N).fill(false));
func.push(new Array(N).fill(false));
}

var setFunc = function(r, c, dark) {
mat[r][c] = dark;
func[r][c] = true;
};

// Finder patterns
var placeFinder = function(row, col) {
for (var r = -1; r <= 7; r++) {
for (var c = -1; c <= 7; c++) {
if (row + r < 0 || row + r >= N || col + c < 0 || col + c >= N) continue;
var dark = (r >= 0 && r <= 6 && (c === 0 || c === 6)) ||
(c >= 0 && c <= 6 && (r === 0 || r === 6)) ||
(r >= 2 && r <= 4 && c >= 2 && c <= 4);
setFunc(row + r, col + c, dark);
}
}
};
placeFinder(0, 0);
placeFinder(0, N - 7);
placeFinder(N - 7, 0);

// Separators are already set to light by finder (border of -1)

// Timing patterns
for (var i = 8; i < N - 8; i++) {
setFunc(6, i, i % 2 === 0);
setFunc(i, 6, i % 2 === 0);
}

// Dark module (always dark, version 1+)
setFunc(N - 8, 8, true);

// Alignment patterns
var ap = ALIGN_POS[ver];
for (var ai = 0; ai < ap.length; ai++) {
for (var aj = 0; aj < ap.length; aj++) {
var cr = ap[ai], cc = ap[aj];
if (func[cr][cc]) continue; // skip if finder already placed
for (var r = -2; r <= 2; r++) {
for (var c = -2; c <= 2; c++) {
setFunc(cr + r, cc + c,
r === -2 || r === 2 || c === -2 || c === 2 || (r === 0 && c === 0));
}
}
}
}

// Format info placeholders (will be overwritten)
for (var i = 0; i <= 8; i++) {
if (!func[8][i]) func[8][i] = true;
if (!func[i][8]) func[i][8] = true;
}
for (var i = N - 8; i < N; i++) {
func[8][i] = true;
func[i][8] = true;
}

// Version info placeholders (version 7+)
if (ver >= 7) {
for (var r = 0; r < 6; r++) {
for (var c = N - 11; c < N - 8; c++) {
func[r][c] = true;
func[c][r] = true;
}
}
}

// Place data bits
var dataBits = [];
for (var i = 0; i < data.length; i++)
for (var b = 7; b >= 0; b--)
dataBits.push((data[i] >> b) & 1);

var bitIdx = 0;
var right = N - 1;
var goUp = true;
while (right >= 1) {
if (right === 6) right--; // skip timing column
for (var vert = 0; vert < N; vert++) {
var row = goUp ? N - 1 - vert : vert;
for (var col = right; col >= right - 1; col--) {
if (!func[row][col]) {
mat[row][col] = bitIdx < dataBits.length ? dataBits[bitIdx] === 1 : false;
bitIdx++;
}
}
}
right -= 2;
goUp = !goUp;
}

// Apply best mask
var bestMask = 0, bestPenalty = Infinity;
for (var mask = 0; mask < 8; mask++) {
var masked = applyMask(mat, func, mask, N);
var penalty = calcPenalty(masked, N);
if (penalty < bestPenalty) {
bestPenalty = penalty;
bestMask = mask;
}
}

var final = applyMask(mat, func, bestMask, N);

// Place format information
var fmtBits = FORMAT_INFO[this.ecLevel][bestMask];
placeFormat(final, fmtBits, N);

// Place version information
if (ver >= 7) {
var verBits = VERSION_INFO[ver];
placeVersion(final, verBits, N);
}

return final;
};

function applyMask(mat, func, mask, N) {
var out = [];
for (var r = 0; r < N; r++) out.push(mat[r].slice());
var conditions = [
function(r,c){return (r+c)%2===0;},
function(r,c){return r%2===0;},
function(r,c){return c%3===0;},
function(r,c){return (r+c)%3===0;},
function(r,c){return (Math.floor(r/2)+Math.floor(c/3))%2===0;},
function(r,c){return (r*c)%2+(r*c)%3===0;},
function(r,c){return ((r*c)%2+(r*c)%3)%2===0;},
function(r,c){return ((r+c)%2+(r*c)%3)%2===0;}
];
var cond = conditions[mask];
for (var r = 0; r < N; r++)
for (var c = 0; c < N; c++)
if (!func[r][c] && cond(r, c)) out[r][c] = !out[r][c];
return out;
}

function calcPenalty(mat, N) {
var pen = 0;
// Rule 1: 5+ in a row
for (var r = 0; r < N; r++) {
for (var c = 0; c < N; ) {
var color = mat[r][c], len = 0;
while (c < N && mat[r][c] === color) { len++; c++; }
if (len >= 5) pen += len - 2;
}
}
for (var c = 0; c < N; c++) {
for (var r = 0; r < N; ) {
var color = mat[r][c], len = 0;
while (r < N && mat[r][c] === color) { len++; r++; }
if (len >= 5) pen += len - 2;
}
}
// Rule 2: 2x2 blocks
for (var r = 0; r < N - 1; r++)
for (var c = 0; c < N - 1; c++)
if (mat[r][c] === mat[r+1][c] && mat[r][c] === mat[r][c+1] && mat[r][c] === mat[r+1][c+1])
pen += 3;
// Rule 3: finder-like patterns
var p1 = [1,0,1,1,1,0,1,0,0,0,0], p2 = [0,0,0,0,1,0,1,1,1,0,1];
for (var r = 0; r < N; r++) {
for (var c = 0; c <= N - 11; c++) {
var m1=true,m2=true;
for (var k=0;k<11;k++){
if(mat[r][c+k]!==(p1[k]===1)) m1=false;
if(mat[r][c+k]!==(p2[k]===1)) m2=false;
}
if(m1||m2) pen+=40;
m1=true; m2=true;
for(var k=0;k<11;k++){
if(mat[c+k][r]!==(p1[k]===1)) m1=false;
if(mat[c+k][r]!==(p2[k]===1)) m2=false;
}
if(m1||m2) pen+=40;
}
}
// Rule 4: dark module ratio
var dark = 0;
for (var r = 0; r < N; r++) for (var c = 0; c < N; c++) if (mat[r][c]) dark++;
var ratio = dark / (N * N);
pen += Math.abs(Math.round(ratio * 20) - 10) * 10;
return pen;
}

function placeFormat(mat, bits, N) {
// Format around top-left finder
var seq = [8,8,8,8,8,8,8,8,7,5,4,3,2,1,0];
var pos = [
[8,0],[8,1],[8,2],[8,3],[8,4],[8,5],[8,7],[8,8],
[7,8],[5,8],[4,8],[3,8],[2,8],[1,8],[0,8]
];
for (var i = 0; i < 15; i++) {
var dark = ((bits >> (14 - i)) & 1) === 1;
mat[pos[i][0]][pos[i][1]] = dark;
if (i < 8)
mat[N - 1 - i][8] = dark;
else
mat[8][N - 15 + i] = dark;
}
mat[N - 8][8] = true; // dark module
}

function placeVersion(mat, bits, N) {
for (var i = 0; i < 18; i++) {
var dark = ((bits >> i) & 1) === 1;
var r = Math.floor(i / 3), c = N - 11 + (i % 3);
mat[r][c] = dark;
mat[c][r] = dark;
}
}

// ─── Canvas Rendering ─────────────────────────────────────────────────────────
function renderQR(qr, canvas, size, fg, bg) {
var N = qr.size;
var quiet = 4; // quiet zone modules
var total = N + quiet * 2;
var mod = size / total;
canvas.width = size;
canvas.height = size;
var ctx = canvas.getContext('2d');
ctx.fillStyle = bg;
ctx.fillRect(0, 0, size, size);
ctx.fillStyle = fg;
for (var r = 0; r < N; r++) {
for (var c = 0; c < N; c++) {
if (qr.modules[r][c]) {
var x = (c + quiet) * mod;
var y = (r + quiet) * mod;
ctx.fillRect(Math.floor(x), Math.floor(y), Math.ceil(mod), Math.ceil(mod));
}
}
}
}

// ─── UI Logic ─────────────────────────────────────────────────────────────────
var currentEC = 'L';
var history = [];

// EC badge selection
document.querySelectorAll('#qr-app .qr-ec-badge').forEach(function(badge) {
badge.addEventListener('click', function() {
document.querySelectorAll('#qr-app .qr-ec-badge').forEach(function(b) { b.classList.remove('active'); });
badge.classList.add('active');
currentEC = badge.getAttribute('data-ec');
});
});

// Character count
var textArea = document.getElementById('qr-text');
var charCur = document.getElementById('qr-char-cur');
textArea.addEventListener('input', function() {
charCur.textContent = textArea.value.length;
});

// Color pickers
function syncColor(picker, hex) {
picker.addEventListener('input', function() {
hex.value = picker.value.toUpperCase();
});
hex.addEventListener('input', function() {
if (/^#[0-9A-Fa-f]{6}$/.test(hex.value)) picker.value = hex.value;
});
}
syncColor(document.getElementById('qr-fg-picker'), document.getElementById('qr-fg-hex'));
syncColor(document.getElementById('qr-bg-picker'), document.getElementById('qr-bg-hex'));

// Generate
document.getElementById('qr-generate-btn').addEventListener('click', function() {
var text = textArea.value.trim();
var errEl = document.getElementById('qr-error');
errEl.style.display = 'none';
if (!text) {
errEl.textContent = 'Please enter some text or URL.';
errEl.style.display = 'block';
return;
}
var size = parseInt(document.getElementById('qr-size').value, 10);
var fg = document.getElementById('qr-fg-hex').value || '#000000';
var bg = document.getElementById('qr-bg-hex').value || '#ffffff';
try {
var qr = new QRCode(text, currentEC);
var canvas = document.getElementById('qr-canvas');
renderQR(qr, canvas, size, fg, bg);
document.getElementById('qr-output-card').style.display = 'block';
document.getElementById('qr-info-bar').textContent =
'Version ' + qr.version + ' · ' + qr.size + '×' + qr.size + ' modules · EC Level ' + currentEC;
addHistory(text);
} catch (e) {
errEl.textContent = 'Error: ' + e.message;
errEl.style.display = 'block';
}
});

// Clear
document.getElementById('qr-clear-btn').addEventListener('click', function() {
textArea.value = '';
charCur.textContent = '0';
document.getElementById('qr-error').style.display = 'none';
document.getElementById('qr-output-card').style.display = 'none';
});

// Download
document.getElementById('qr-download-btn').addEventListener('click', function() {
var canvas = document.getElementById('qr-canvas');
var a = document.createElement('a');
a.download = 'qrcode.png';
a.href = canvas.toDataURL('image/png');
a.click();
});

// Copy to clipboard
document.getElementById('qr-copy-btn').addEventListener('click', function() {
var canvas = document.getElementById('qr-canvas');
canvas.toBlob(function(blob) {
try {
navigator.clipboard.write([new ClipboardItem({'image/png': blob})]).then(function() {
var btn = document.getElementById('qr-copy-btn');
btn.textContent = 'Copied!';
setTimeout(function() { btn.textContent = 'Copy to Clipboard'; }, 2000);
});
} catch(e) {
alert('Copy to clipboard not supported in this browser. Use Download instead.');
}
});
});

// History
function addHistory(text) {
history = history.filter(function(h) { return h !== text; });
history.unshift(text);
if (history.length > 20) history.pop();
renderHistory();
}

function renderHistory() {
var list = document.getElementById('qr-history-list');
if (history.length === 0) {
list.innerHTML = '<li><div class="qr-empty-history">No QR codes generated yet.</div></li>';
return;
}
list.innerHTML = history.map(function(text, idx) {
return '<li>' +
'<span class="qr-history-text" data-idx="' + idx + '" title="' + escHtml(text) + '">' + escHtml(text.length > 60 ? text.slice(0, 60) + '…' : text) + '</span>' +
'<button class="qr-history-del" data-idx="' + idx + '" title="Remove">&#215;</button>' +
'</li>';
}).join('');
list.querySelectorAll('.qr-history-text').forEach(function(el) {
el.addEventListener('click', function() {
textArea.value = history[parseInt(el.getAttribute('data-idx'), 10)];
charCur.textContent = textArea.value.length;
document.getElementById('qr-generate-btn').click();
});
});
list.querySelectorAll('.qr-history-del').forEach(function(el) {
el.addEventListener('click', function() {
history.splice(parseInt(el.getAttribute('data-idx'), 10), 1);
renderHistory();
});
});
}

document.getElementById('qr-clear-history-btn').addEventListener('click', function() {
history = [];
renderHistory();
});

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

renderHistory();

})();
</script>

---

> Generate barcodes → [Barcode Generator](/tools/barcode-generator/)

> Create business cards → [Business Card Generator](/tools/business-card-generator/)

</div>
