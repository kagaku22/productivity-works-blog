---
title: "QR Code Generator"
date: 2025-05-16
description: "Free online QR code generator. Create QR codes for URLs, text, WiFi, email, and phone — download as PNG or SVG instantly, no sign-up required."
categories: ["Free Tools"]
slug: "qr-code-generator"
ShowToc: false
cover:
  image: "/images/covers/qr-code-generator.png"
  alt: "QR Code Generator"
---

Generate QR codes instantly in your browser — no uploads, no accounts, no tracking. Supports URLs, plain text, WiFi credentials, and email links.

<div id="qr-app">
<style>
#qr-app *,#qr-app *::before,#qr-app *::after{box-sizing:border-box;margin:0;padding:0}
#qr-app{font-family:system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;color:#1e293b;max-width:680px;margin:2rem auto;padding:0 1rem}
#qr-app .qa-card{background:#fff;border:1px solid #e2e8f0;border-radius:12px;padding:1.5rem;margin-bottom:1.25rem;box-shadow:0 1px 4px rgba(0,0,0,.06)}
#qr-app .qa-tabs{display:flex;gap:.5rem;flex-wrap:wrap;margin-bottom:1.25rem}
#qr-app .qa-tab{padding:.45rem 1rem;border:1px solid #cbd5e1;border-radius:6px;background:#f8fafc;color:#475569;font-size:.875rem;cursor:pointer;transition:all .15s}
#qr-app .qa-tab:hover{background:#f1f5f9;border-color:#94a3b8}
#qr-app .qa-tab.active{background:#0f172a;color:#fff;border-color:#0f172a}
#qr-app .qa-panel{display:none}
#qr-app .qa-panel.active{display:block}
#qr-app .qa-field{margin-bottom:.9rem}
#qr-app .qa-label{display:block;font-size:.8rem;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:.04em;margin-bottom:.35rem}
#qr-app .qa-input{width:100%;padding:.55rem .75rem;border:1px solid #cbd5e1;border-radius:7px;font-size:.95rem;color:#1e293b;background:#f8fafc;transition:border-color .15s,box-shadow .15s;outline:none}
#qr-app .qa-input:focus{border-color:#6366f1;box-shadow:0 0 0 3px rgba(99,102,241,.15);background:#fff}
#qr-app select.qa-input{appearance:none;-webkit-appearance:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%2364748b' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right .75rem center;background-color:#f8fafc;padding-right:2.25rem;cursor:pointer}
#qr-app .qa-row{display:grid;grid-template-columns:1fr 1fr;gap:.75rem}
#qr-app .qa-section-title{font-size:.8rem;font-weight:700;color:#94a3b8;text-transform:uppercase;letter-spacing:.07em;margin-bottom:.85rem}
#qr-app .qa-customize{display:grid;grid-template-columns:1fr 1fr 1fr;gap:.75rem;align-items:end}
#qr-app .qa-slider-wrap{display:flex;align-items:center;gap:.6rem}
#qr-app .qa-slider{-webkit-appearance:none;appearance:none;width:100%;height:5px;border-radius:3px;background:#e2e8f0;outline:none;cursor:pointer}
#qr-app .qa-slider::-webkit-slider-thumb{-webkit-appearance:none;width:16px;height:16px;border-radius:50%;background:#6366f1;cursor:pointer;border:2px solid #fff;box-shadow:0 0 0 1px #6366f1}
#qr-app .qa-slider::-moz-range-thumb{width:16px;height:16px;border-radius:50%;background:#6366f1;cursor:pointer;border:2px solid #fff}
#qr-app .qa-slider-val{font-size:.8rem;color:#64748b;white-space:nowrap;min-width:3.2rem;text-align:right}
#qr-app .qa-color-wrap{display:flex;align-items:center;gap:.5rem}
#qr-app .qa-color-swatch{width:36px;height:36px;border-radius:7px;border:1px solid #cbd5e1;cursor:pointer;overflow:hidden;padding:2px;background:#fff;flex-shrink:0}
#qr-app .qa-color-swatch input[type=color]{width:100%;height:100%;border:none;cursor:pointer;background:transparent;padding:0;appearance:none;-webkit-appearance:none;display:block}
#qr-app .qa-color-label{font-size:.82rem;color:#64748b;font-family:monospace}
#qr-app .qa-preview{display:flex;flex-direction:column;align-items:center;gap:1.25rem}
#qr-app .qa-canvas-wrap{background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;padding:1.25rem;display:flex;align-items:center;justify-content:center;min-height:220px;width:100%}
#qr-app canvas{display:block;border-radius:4px;max-width:100%;image-rendering:pixelated}
#qr-app .qa-btns{display:flex;gap:.75rem;flex-wrap:wrap;justify-content:center}
#qr-app .qa-btn{display:inline-flex;align-items:center;gap:.45rem;padding:.55rem 1.25rem;border-radius:8px;font-size:.875rem;font-weight:600;cursor:pointer;border:none;transition:all .15s;text-decoration:none}
#qr-app .qa-btn-primary{background:#0f172a;color:#fff}
#qr-app .qa-btn-primary:hover{background:#1e293b}
#qr-app .qa-btn-primary:disabled{background:#94a3b8;cursor:not-allowed}
#qr-app .qa-btn-outline{background:#fff;color:#0f172a;border:1.5px solid #cbd5e1}
#qr-app .qa-btn-outline:hover{background:#f1f5f9;border-color:#94a3b8}
#qr-app .qa-btn-outline:disabled{color:#94a3b8;border-color:#e2e8f0;cursor:not-allowed;background:#fff}
#qr-app .qa-empty{color:#94a3b8;font-size:.9rem;text-align:center;padding:2rem 0}
@media(max-width:520px){
#qr-app .qa-customize{grid-template-columns:1fr 1fr}
#qr-app .qa-row{grid-template-columns:1fr}
}
</style>

<!-- Input Card -->
<div class="qa-card">
<div class="qa-tabs">
<button class="qa-tab active" data-tab="url">URL</button>
<button class="qa-tab" data-tab="text">Text</button>
<button class="qa-tab" data-tab="wifi">WiFi</button>
<button class="qa-tab" data-tab="email">Email</button>
</div>

<!-- URL -->
<div class="qa-panel active" id="qa-panel-url">
<div class="qa-field">
<label class="qa-label" for="qa-url-input">Website URL</label>
<input class="qa-input" id="qa-url-input" type="url" placeholder="https://example.com" value="https://">
</div>
</div>

<!-- Text -->
<div class="qa-panel" id="qa-panel-text">
<div class="qa-field">
<label class="qa-label" for="qa-text-input">Plain Text</label>
<textarea class="qa-input" id="qa-text-input" rows="3" placeholder="Enter any text&#8230;" style="resize:vertical"></textarea>
</div>
</div>

<!-- WiFi -->
<div class="qa-panel" id="qa-panel-wifi">
<div class="qa-field">
<label class="qa-label" for="qa-wifi-ssid">Network Name (SSID)</label>
<input class="qa-input" id="qa-wifi-ssid" type="text" placeholder="MyNetwork">
</div>
<div class="qa-row">
<div class="qa-field">
<label class="qa-label" for="qa-wifi-pass">Password</label>
<input class="qa-input" id="qa-wifi-pass" type="password" placeholder="password">
</div>
<div class="qa-field">
<label class="qa-label" for="qa-wifi-enc">Encryption</label>
<select class="qa-input" id="qa-wifi-enc">
<option value="WPA">WPA/WPA2</option>
<option value="WEP">WEP</option>
<option value="nopass">None (open)</option>
</select>
</div>
</div>
</div>

<!-- Email -->
<div class="qa-panel" id="qa-panel-email">
<div class="qa-field">
<label class="qa-label" for="qa-email-to">To Address</label>
<input class="qa-input" id="qa-email-to" type="email" placeholder="name@example.com">
</div>
<div class="qa-field">
<label class="qa-label" for="qa-email-subject">Subject</label>
<input class="qa-input" id="qa-email-subject" type="text" placeholder="Subject line">
</div>
<div class="qa-field">
<label class="qa-label" for="qa-email-body">Body (optional)</label>
<textarea class="qa-input" id="qa-email-body" rows="2" placeholder="Message body&#8230;" style="resize:vertical"></textarea>
</div>
</div>
</div>

<!-- Customization Card -->
<div class="qa-card">
<div class="qa-section-title">Appearance</div>
<div class="qa-customize">
<div class="qa-field">
<label class="qa-label">Size</label>
<div class="qa-slider-wrap">
<input class="qa-slider" type="range" id="qa-size" min="200" max="600" value="300" step="10">
<span class="qa-slider-val" id="qa-size-val">300px</span>
</div>
</div>
<div class="qa-field">
<label class="qa-label">Foreground</label>
<div class="qa-color-wrap">
<div class="qa-color-swatch"><input type="color" id="qa-fg" value="#000000"></div>
<span class="qa-color-label" id="qa-fg-label">#000000</span>
</div>
</div>
<div class="qa-field">
<label class="qa-label">Background</label>
<div class="qa-color-wrap">
<div class="qa-color-swatch"><input type="color" id="qa-bg" value="#ffffff"></div>
<span class="qa-color-label" id="qa-bg-label">#ffffff</span>
</div>
</div>
</div>
</div>

<!-- Preview Card -->
<div class="qa-card">
<div class="qa-section-title">Preview &amp; Download</div>
<div class="qa-preview">
<div class="qa-canvas-wrap" id="qa-canvas-wrap">
<p class="qa-empty" id="qa-empty-msg">Enter content above to generate a QR code.</p>
<canvas id="qa-canvas" style="display:none"></canvas>
</div>
<div class="qa-btns">
<button class="qa-btn qa-btn-primary" id="qa-dl-png" disabled>&#8595; Download PNG</button>
<button class="qa-btn qa-btn-outline" id="qa-dl-svg" disabled>&#8595; Download SVG</button>
</div>
</div>
</div>

<script>
(function(){
"use strict";

/* =========================================================
Pure-JS QR Code Generator
- Byte mode encoding
- Error correction level M
- Versions 1–6 (21×21 to 41×41 modules)
- Full Reed-Solomon ECC
- All 8 mask patterns evaluated (penalty scoring)
- PNG canvas render + SVG generation
========================================================= */

// ── GF(256) over primitive poly 0x11D ─────────────────────
var GF_EXP = new Uint8Array(512);
var GF_LOG = new Uint8Array(256);
(function(){
var x = 1;
for(var i = 0; i < 255; i++){
GF_EXP[i] = x;
GF_LOG[x] = i;
x <<= 1;
if(x & 256) x ^= 0x11d;
x &= 255;
}
for(var j = 255; j < 512; j++) GF_EXP[j] = GF_EXP[j - 255];
})();

function gfMul(a, b){
if(a === 0 || b === 0) return 0;
return GF_EXP[(GF_LOG[a] + GF_LOG[b]) % 255];
}

function rsGenPoly(n){
var g = [1];
for(var i = 0; i < n; i++){
var t = [1, GF_EXP[i]];
var ng = new Array(g.length + 1).fill(0);
for(var j = 0; j < g.length; j++)
for(var k = 0; k < t.length; k++)
ng[j + k] ^= gfMul(g[j], t[k]);
g = ng;
}
return g;
}

function rsEncode(data, nEC){
var gen = rsGenPoly(nEC);
var msg = data.slice();
for(var i = 0; i < nEC; i++) msg.push(0);
for(var i = 0; i < data.length; i++){
var coef = msg[i];
if(coef !== 0)
for(var j = 1; j < gen.length; j++)
msg[i + j] ^= gfMul(gen[j], coef);
}
return msg.slice(data.length);
}

// ── Version capacity table (byte mode, EC level M) ────────
// data = data codewords, ec = EC codewords per block, blocks = number of blocks
var VCAP = [
null,
{sz:21, data:16, ec:10, blk:1},  // v1
{sz:25, data:28, ec:16, blk:1},  // v2
{sz:29, data:44, ec:26, blk:1},  // v3
{sz:33, data:64, ec:18, blk:2},  // v4
{sz:37, data:86, ec:24, blk:2},  // v5
{sz:41, data:108,ec:16, blk:4},  // v6
];

function pickVersion(byteLen){
for(var v = 1; v <= 6; v++)
if(byteLen <= VCAP[v].data) return v;
return null;
}

// ── Alignment pattern centers (versions 1-6) ──────────────
var ALIGN = [null, [], [6,18], [6,22], [6,26], [6,30], [6,34]];

// ── Format info (EC=M=01, masks 0-7), pre-computed 15-bit ─
// EC level M bits = 01; XOR mask = 101010000010010
var FMT_M = [
0x5412, 0x5125, 0x5E7C, 0x5B4B,
0x45F9, 0x40CE, 0x4F97, 0x4AA0
];

// ── Build blank matrix with function modules ───────────────
function buildMatrix(ver){
var sz = VCAP[ver].sz;
var m = [];
for(var i = 0; i < sz; i++){
m.push(new Int8Array(sz)); // 0=light, 1=dark, negative=function
}

function setF(r, c, dark){
if(r >= 0 && r < sz && c >= 0 && c < sz)
m[r][c] = dark ? -1 : -2;
}

// Finder pattern at (row, col) top-left corner
function finder(ro, co){
for(var r = -1; r <= 7; r++)
for(var c = -1; c <= 7; c++){
var inPat = r >= 0 && r <= 6 && c >= 0 && c <= 6;
var dark = inPat && (r === 0 || r === 6 || c === 0 || c === 6 ||
(r >= 2 && r <= 4 && c >= 2 && c <= 4));
setF(ro + r, co + c, inPat ? dark : false);
}
}
finder(0, 0);
finder(0, sz - 7);
finder(sz - 7, 0);

// Timing strips
for(var i = 8; i < sz - 8; i++){
setF(6, i, i % 2 === 0);
setF(i, 6, i % 2 === 0);
}

// Dark module
setF(sz - 8, 8, true);

// Alignment patterns
var ap = ALIGN[ver];
for(var ri = 0; ri < ap.length; ri++){
for(var ci = 0; ci < ap.length; ci++){
var ar = ap[ri], ac = ap[ci];
if(m[ar][ac] !== 0) continue; // already occupied
for(var dr = -2; dr <= 2; dr++)
for(var dc = -2; dc <= 2; dc++)
setF(ar + dr, ac + dc,
dr === -2 || dr === 2 || dc === -2 || dc === 2 || (dr === 0 && dc === 0));
}
}

// Reserve format info areas (mark as function light)
for(var i = 0; i < 8; i++){
if(m[8][i] === 0) setF(8, i, false);
if(m[i][8] === 0) setF(i, 8, false);
setF(8, sz - 1 - i, false);
setF(sz - 1 - i, 8, false);
}

return m;
}

// ── Place data bits into matrix ────────────────────────────
function placeData(m, bits){
var sz = m.length;
var bi = 0;
var goUp = true;
var col = sz - 1;
while(col >= 0){
if(col === 6) { col--; continue; }
for(var step = 0; step < sz; step++){
var row = goUp ? (sz - 1 - step) : step;
for(var dc = 0; dc < 2; dc++){
var c = col - dc;
if(m[row][c] === 0){ // unset data cell
m[row][c] = (bi < bits.length) ? bits[bi++] : 0;
}
}
}
goUp = !goUp;
col -= 2;
}
}

// ── Mask functions ─────────────────────────────────────────
var MASKS = [
function(r,c){ return (r+c)%2===0; },
function(r,c){ return r%2===0; },
function(r,c){ return c%3===0; },
function(r,c){ return (r+c)%3===0; },
function(r,c){ return (Math.floor(r/2)+Math.floor(c/3))%2===0; },
function(r,c){ return (r*c)%2+(r*c)%3===0; },
function(r,c){ return ((r*c)%2+(r*c)%3)%2===0; },
function(r,c){ return ((r+c)%2+(r*c)%3)%2===0; }
];

function applyMask(m, maskIdx){
var sz = m.length;
var fn = MASKS[maskIdx];
var nm = [];
for(var r = 0; r < sz; r++){
nm.push(new Int8Array(m[r]));
for(var c = 0; c < sz; c++){
var v = nm[r][c];
if(v === 0 || v === 1) // data module
nm[r][c] = fn(r, c) ? (v ^ 1) : v;
}
}
return nm;
}

// ── Write format info into matrix ─────────────────────────
function writeFormat(m, maskIdx){
var sz = m.length;
var fi = FMT_M[maskIdx];
var bits = [];
for(var i = 14; i >= 0; i--) bits.push((fi >> i) & 1);

// Top-left horizontal: columns 0-5, 7, 8 at row 8
var hcols = [0,1,2,3,4,5,7,8];
for(var i = 0; i < 8; i++) m[8][hcols[i]] = bits[i];
// Top-left vertical: rows 7,5,4,3,2,1,0 at col 8
var vrows = [7,5,4,3,2,1,0];
for(var i = 0; i < 7; i++) m[vrows[i]][8] = bits[8 + i];

// Bottom-left vertical: rows sz-7 to sz-1 at col 8
for(var i = 0; i < 7; i++) m[sz - 7 + i][8] = bits[i];
// Top-right horizontal: cols sz-8 to sz-1 at row 8
for(var i = 0; i < 8; i++) m[8][sz - 8 + i] = bits[7 + i];
}

// ── Normalize: function modules become 0/1 ────────────────
function normalize(m){
var sz = m.length;
var out = [];
for(var r = 0; r < sz; r++){
out.push(new Uint8Array(sz));
for(var c = 0; c < sz; c++){
var v = m[r][c];
out[r][c] = (v === -1 || v === 1) ? 1 : 0;
}
}
return out;
}

// ── Penalty scoring ────────────────────────────────────────
function penalty(m){
var sz = m.length;
var score = 0;

// Rule 1: runs of 5+ same colour in row/col
function runPenalty(arr){
var s = 0, cnt = 1;
for(var i = 1; i < arr.length; i++){
if(arr[i] === arr[i-1]) cnt++;
else { if(cnt >= 5) s += cnt - 2; cnt = 1; }
}
if(cnt >= 5) s += cnt - 2;
return s;
}
for(var r = 0; r < sz; r++){
score += runPenalty(Array.from(m[r]));
score += runPenalty(Array.from(m.map(function(row){ return row[r]; })));
}

// Rule 2: 2x2 blocks
for(var r = 0; r < sz - 1; r++)
for(var c = 0; c < sz - 1; c++)
if(m[r][c] === m[r][c+1] && m[r][c] === m[r+1][c] && m[r][c] === m[r+1][c+1])
score += 3;

// Rule 3: finder-like patterns
var p1 = [1,0,1,1,1,0,1,0,0,0,0];
var p2 = [0,0,0,0,1,0,1,1,1,0,1];
function patPenalty(arr, pat){
var s = 0;
outer: for(var i = 0; i <= arr.length - pat.length; i++){
for(var j = 0; j < pat.length; j++) if(arr[i+j] !== pat[j]) continue outer;
s += 40;
}
return s;
}
for(var r = 0; r < sz; r++){
var row = Array.from(m[r]);
score += patPenalty(row, p1) + patPenalty(row, p2);
var col = Array.from(m.map(function(rw){ return rw[r]; }));
score += patPenalty(col, p1) + patPenalty(col, p2);
}

// Rule 4: dark ratio
var dark = 0;
for(var r = 0; r < sz; r++) for(var c = 0; c < sz; c++) dark += m[r][c];
var pct = dark * 100 / (sz * sz);
var prev = Math.floor(pct / 5) * 5;
score += Math.min(Math.abs(prev - 50), Math.abs(prev + 5 - 50)) / 5 * 10;

return score;
}

// ── Full QR encode ─────────────────────────────────────────
function encodeQR(text){
// Encode text to UTF-8 bytes
var bytes = [];
for(var i = 0; i < text.length; i++){
var cp = text.charCodeAt(i);
if(cp < 0x80){
bytes.push(cp);
} else if(cp < 0x800){
bytes.push(0xC0 | (cp >> 6), 0x80 | (cp & 0x3F));
} else {
bytes.push(0xE0 | (cp >> 12), 0x80 | ((cp >> 6) & 0x3F), 0x80 | (cp & 0x3F));
}
}

var ver = pickVersion(bytes.length);
if(!ver) return null;
var cap = VCAP[ver];

// Build data bit stream
var bits = [];
function addBits(val, n){
for(var i = n - 1; i >= 0; i--) bits.push((val >> i) & 1);
}

addBits(0b0100, 4);           // byte mode indicator
addBits(bytes.length, 8);     // character count (versions 1-9: 8 bits)
for(var i = 0; i < bytes.length; i++) addBits(bytes[i], 8);

// Terminator (up to 4 zeros)
var rem = cap.data * 8 - bits.length;
for(var i = 0; i < Math.min(4, rem); i++) bits.push(0);

// Byte-align
while(bits.length % 8 !== 0) bits.push(0);

// Padding codewords
var PAD = [0xEC, 0x11];
var pi = 0;
while(bits.length < cap.data * 8){ addBits(PAD[pi++ % 2], 8); }

// Convert bits to data codewords
var dataCW = [];
for(var i = 0; i < cap.data; i++){
var b = 0;
for(var j = 0; j < 8; j++) b = (b << 1) | bits[i * 8 + j];
dataCW.push(b);
}

// Split into blocks and generate EC codewords
var blk = cap.blk;
var baseSize = Math.floor(cap.data / blk);
var extra = cap.data % blk;  // last `extra` blocks get one more codeword
var blocks = [], offset = 0;
for(var b = 0; b < blk; b++){
var sz = b < (blk - extra) ? baseSize : baseSize + 1;
blocks.push(dataCW.slice(offset, offset + sz));
offset += sz;
}
var ecBlocks = blocks.map(function(blkData){ return rsEncode(blkData, cap.ec); });

// Interleave data codewords
var finalCW = [];
var maxLen = Math.max.apply(null, blocks.map(function(b){ return b.length; }));
for(var i = 0; i < maxLen; i++)
for(var b = 0; b < blocks.length; b++)
if(i < blocks[b].length) finalCW.push(blocks[b][i]);

// Interleave EC codewords
for(var i = 0; i < cap.ec; i++)
for(var b = 0; b < ecBlocks.length; b++)
finalCW.push(ecBlocks[b][i]);

// Final bit stream
var finalBits = [];
for(var i = 0; i < finalCW.length; i++)
for(var j = 7; j >= 0; j--) finalBits.push((finalCW[i] >> j) & 1);

// Remainder bits (ver 1=0, ver 2-6=7)
var remBits = [0, 0, 7, 7, 7, 7, 7];
for(var i = 0; i < remBits[ver]; i++) finalBits.push(0);

// Build matrix and choose best mask
var bestMask = 0, bestPen = Infinity, bestMatrix = null;

for(var mi = 0; mi < 8; mi++){
var mat = buildMatrix(ver);
placeData(mat, finalBits.slice());
var masked = applyMask(mat, mi);
writeFormat(masked, mi);
var norm = normalize(masked);
var pen = penalty(norm);
if(pen < bestPen){
bestPen = pen;
bestMask = mi;
bestMatrix = norm;
}
}

return bestMatrix;
}

// ── Canvas render ──────────────────────────────────────────
var lastMatrix = null;

function renderCanvas(matrix, size, fg, bg){
var canvas = document.getElementById('qa-canvas');
var n = matrix.length;
var quiet = 4;
var total = n + quiet * 2;
var mod = Math.floor(size / total);
var px = mod * total;
canvas.width = px;
canvas.height = px;
var ctx = canvas.getContext('2d');
ctx.fillStyle = bg;
ctx.fillRect(0, 0, px, px);
ctx.fillStyle = fg;
for(var r = 0; r < n; r++)
for(var c = 0; c < n; c++)
if(matrix[r][c])
ctx.fillRect((c + quiet) * mod, (r + quiet) * mod, mod, mod);
}

function matrixToSVG(matrix, size, fg, bg){
var n = matrix.length;
var quiet = 4;
var total = n + quiet * 2;
var mod = (size / total).toFixed(4);
var rects = [];
for(var r = 0; r < n; r++)
for(var c = 0; c < n; c++)
if(matrix[r][c]){
var x = ((c + quiet) * size / total).toFixed(3);
var y = ((r + quiet) * size / total).toFixed(3);
rects.push('<rect x="' + x + '" y="' + y + '" width="' + mod + '" height="' + mod + '"/>');
}
return '<?xml version="1.0" encoding="UTF-8"?>\n' +
'<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 ' + size + ' ' + size + '">\n' +
'<rect width="' + size + '" height="' + size + '" fill="' + bg + '"/>\n' +
'<g fill="' + fg + '">' + rects.join('') + '</g>\n</svg>';
}

// ── UI ─────────────────────────────────────────────────────
var currentTab = 'url';

function getCurrentText(){
switch(currentTab){
case 'url':
return document.getElementById('qa-url-input').value.trim();
case 'text':
return document.getElementById('qa-text-input').value;
case 'wifi': {
var ssid = document.getElementById('qa-wifi-ssid').value;
var pass = document.getElementById('qa-wifi-pass').value;
var enc  = document.getElementById('qa-wifi-enc').value;
if(!ssid) return '';
return 'WIFI:T:' + enc + ';S:' + ssid + ';P:' + pass + ';;';
}
case 'email': {
var to = document.getElementById('qa-email-to').value.trim();
if(!to) return '';
var subj = document.getElementById('qa-email-subject').value.trim();
var body = document.getElementById('qa-email-body').value.trim();
var uri = 'mailto:' + encodeURIComponent(to);
var params = [];
if(subj) params.push('subject=' + encodeURIComponent(subj));
if(body)  params.push('body=' + encodeURIComponent(body));
if(params.length) uri += '?' + params.join('&');
return uri;
}
}
return '';
}

function update(){
var text = getCurrentText();
var size = parseInt(document.getElementById('qa-size').value, 10);
var fg   = document.getElementById('qa-fg').value;
var bg   = document.getElementById('qa-bg').value;

var canvas   = document.getElementById('qa-canvas');
var emptyMsg = document.getElementById('qa-empty-msg');
var dlPng    = document.getElementById('qa-dl-png');
var dlSvg    = document.getElementById('qa-dl-svg');

if(!text){
canvas.style.display = 'none';
emptyMsg.textContent = 'Enter content above to generate a QR code.';
emptyMsg.style.display = '';
dlPng.disabled = true;
dlSvg.disabled = true;
lastMatrix = null;
return;
}

var matrix = encodeQR(text);
if(!matrix){
canvas.style.display = 'none';
emptyMsg.textContent = 'Input too long (max ~108 bytes). Please shorten.';
emptyMsg.style.display = '';
dlPng.disabled = true;
dlSvg.disabled = true;
lastMatrix = null;
return;
}

lastMatrix = matrix;
emptyMsg.style.display = 'none';
canvas.style.display = 'block';
renderCanvas(matrix, size, fg, bg);
dlPng.disabled = false;
dlSvg.disabled = false;
}

// Debounce helper
var debTimer = null;
function debouncedUpdate(ms){
clearTimeout(debTimer);
debTimer = setTimeout(update, ms || 250);
}

// Tab switching
document.querySelectorAll('#qr-app .qa-tab').forEach(function(btn){
btn.addEventListener('click', function(){
document.querySelectorAll('#qr-app .qa-tab').forEach(function(b){ b.classList.remove('active'); });
document.querySelectorAll('#qr-app .qa-panel').forEach(function(p){ p.classList.remove('active'); });
btn.classList.add('active');
currentTab = btn.dataset.tab;
document.getElementById('qa-panel-' + currentTab).classList.add('active');
update();
});
});

// Input events
['qa-url-input','qa-text-input','qa-wifi-ssid','qa-wifi-pass','qa-wifi-enc',
 'qa-email-to','qa-email-subject','qa-email-body'].forEach(function(id){
var el = document.getElementById(id);
if(el) el.addEventListener('input', function(){ debouncedUpdate(250); });
});

// Size slider
document.getElementById('qa-size').addEventListener('input', function(){
document.getElementById('qa-size-val').textContent = this.value + 'px';
debouncedUpdate(80);
});

// Color pickers
document.getElementById('qa-fg').addEventListener('input', function(){
document.getElementById('qa-fg-label').textContent = this.value;
debouncedUpdate(80);
});
document.getElementById('qa-bg').addEventListener('input', function(){
document.getElementById('qa-bg-label').textContent = this.value;
debouncedUpdate(80);
});

// Download PNG
document.getElementById('qa-dl-png').addEventListener('click', function(){
if(!lastMatrix) return;
var canvas = document.getElementById('qa-canvas');
var a = document.createElement('a');
a.href = canvas.toDataURL('image/png');
a.download = 'qrcode.png';
a.click();
});

// Download SVG
document.getElementById('qa-dl-svg').addEventListener('click', function(){
if(!lastMatrix) return;
var size = parseInt(document.getElementById('qa-size').value, 10);
var fg   = document.getElementById('qa-fg').value;
var bg   = document.getElementById('qa-bg').value;
var svg  = matrixToSVG(lastMatrix, size, fg, bg);
var blob = new Blob([svg], {type: 'image/svg+xml'});
var url  = URL.createObjectURL(blob);
var a    = document.createElement('a');
a.href = url;
a.download = 'qrcode.svg';
a.click();
setTimeout(function(){ URL.revokeObjectURL(url); }, 10000);
});

// Initial render
update();

})();
</script>
</div>

---

> Encode/decode URLs &#8594; [URL Encoder/Decoder](/tools/url-encoder-decoder/)
> Convert to Base64 &#8594; [Base64 Encoder/Decoder](/tools/base64-encoder/)
> Generate placeholder images &#8594; [Placeholder Image Generator](/tools/placeholder-image/)
