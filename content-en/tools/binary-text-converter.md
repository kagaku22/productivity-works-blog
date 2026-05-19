---
title: "Binary ↔ Text Converter - Free Online Tool"
date: 2025-05-16
description: "Convert text to binary and binary to text instantly. Supports UTF-8, Unicode, hex and octal output, character breakdown table, and clipboard copy. Free online binary converter tool."
categories: ["Free Tools"]
tags: ["binary", "text converter", "binary to text", "text to binary", "hex", "octal", "developer tool", "encoding"]
slug: "binary-text-converter"
aliases: ["/tools/binary-text-converter/", "/tools/binary-converter/"]
cover:
  image: "/images/covers/binary-text-converter.png"
  alt: "Binary Text Converter"
ShowToc: false
---

<div id="btc-app">

<style>
#btc-app {
font-family: ui-sans-serif, system-ui, -apple-system, sans-serif;
color: #e2e8f0;
max-width: 900px;
margin: 0 auto;
padding: 0;
}
#btc-app * { box-sizing: border-box; }

.btc-card {
background: #1e293b;
border: 1px solid #334155;
border-radius: 12px;
padding: 24px;
margin-bottom: 16px;
}

.btc-row {
display: flex;
gap: 12px;
flex-wrap: wrap;
align-items: center;
margin-bottom: 16px;
}

.btc-label {
font-size: 13px;
font-weight: 600;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 8px;
display: flex;
justify-content: space-between;
align-items: center;
}

.btc-label-text { color: #94a3b8; }

.btc-char-count {
font-size: 12px;
font-weight: 400;
color: #64748b;
text-transform: none;
letter-spacing: 0;
}

.btc-textarea {
width: 100%;
min-height: 120px;
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
color: #e2e8f0;
font-family: 'Courier New', Courier, monospace;
font-size: 14px;
padding: 12px;
resize: vertical;
outline: none;
transition: border-color 0.2s;
line-height: 1.6;
}
.btc-textarea:focus { border-color: #6366f1; }
.btc-textarea::placeholder { color: #475569; }

.btc-btn {
padding: 9px 18px;
border-radius: 7px;
border: none;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
white-space: nowrap;
}
.btc-btn:active { transform: scale(0.97); }

.btc-btn-primary {
background: #6366f1;
color: #fff;
}
.btc-btn-primary:hover { background: #4f46e5; }

.btc-btn-secondary {
background: #334155;
color: #cbd5e1;
}
.btc-btn-secondary:hover { background: #475569; }

.btc-btn-copy {
background: #0f4c81;
color: #93c5fd;
padding: 5px 12px;
font-size: 12px;
border-radius: 6px;
}
.btc-btn-copy:hover { background: #1d4ed8; color: #fff; }
.btc-btn-copy.copied { background: #065f46; color: #6ee7b7; }

.btc-mode-group {
display: flex;
gap: 6px;
flex-wrap: wrap;
}

.btc-mode-btn {
padding: 7px 14px;
border-radius: 6px;
border: 1.5px solid #334155;
background: #0f172a;
color: #94a3b8;
font-size: 12px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
.btc-mode-btn.active {
border-color: #6366f1;
background: #312e81;
color: #a5b4fc;
}
.btc-mode-btn:hover:not(.active) { border-color: #6366f1; color: #e2e8f0; }

.btc-toggle-group {
display: flex;
align-items: center;
gap: 8px;
font-size: 13px;
color: #94a3b8;
}

.btc-toggle {
position: relative;
width: 40px;
height: 22px;
flex-shrink: 0;
}
.btc-toggle input { opacity: 0; width: 0; height: 0; }
.btc-toggle-slider {
position: absolute;
inset: 0;
background: #334155;
border-radius: 22px;
cursor: pointer;
transition: background 0.2s;
}
.btc-toggle-slider::before {
content: '';
position: absolute;
width: 16px; height: 16px;
left: 3px; top: 3px;
background: #94a3b8;
border-radius: 50%;
transition: transform 0.2s, background 0.2s;
}
.btc-toggle input:checked + .btc-toggle-slider { background: #4f46e5; }
.btc-toggle input:checked + .btc-toggle-slider::before {
transform: translateX(18px);
background: #fff;
}

.btc-output-box {
position: relative;
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
padding: 14px;
min-height: 100px;
font-family: 'Courier New', Courier, monospace;
font-size: 13px;
color: #a5b4fc;
word-break: break-all;
line-height: 1.7;
white-space: pre-wrap;
}

.btc-error {
color: #f87171;
font-size: 13px;
margin-top: 6px;
min-height: 18px;
}

.btc-section-title {
font-size: 15px;
font-weight: 700;
color: #c7d2fe;
margin: 0 0 14px 0;
}

.btc-dir-arrows {
display: flex;
justify-content: center;
gap: 10px;
margin: 4px 0 4px;
}
.btc-dir-btn {
display: flex;
align-items: center;
gap: 6px;
padding: 10px 22px;
border-radius: 8px;
border: none;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
}
.btc-dir-btn:active { transform: scale(0.97); }
.btc-dir-btn-encode {
background: #6366f1;
color: #fff;
}
.btc-dir-btn-encode:hover { background: #4f46e5; }
.btc-dir-btn-decode {
background: #0891b2;
color: #fff;
}
.btc-dir-btn-decode:hover { background: #0e7490; }

/* Breakdown table */
.btc-table-wrap {
overflow-x: auto;
margin-top: 8px;
}
.btc-table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
}
.btc-table th {
background: #0f172a;
color: #94a3b8;
font-size: 11px;
text-transform: uppercase;
letter-spacing: 0.05em;
padding: 8px 10px;
text-align: left;
border-bottom: 1px solid #334155;
}
.btc-table td {
padding: 7px 10px;
border-bottom: 1px solid #1e293b;
font-family: 'Courier New', Courier, monospace;
color: #e2e8f0;
vertical-align: middle;
}
.btc-table tr:hover td { background: #1e2d3d; }
.btc-table .td-char {
font-size: 15px;
font-weight: 700;
color: #fbbf24;
min-width: 32px;
}
.btc-table .td-cp { color: #94a3b8; font-size: 12px; }
.btc-table .td-bin { color: #a5b4fc; }
.btc-table .td-hex { color: #34d399; }
.btc-table .td-oct { color: #fb923c; }
.btc-table .td-dec { color: #e2e8f0; }

.btc-empty-msg {
text-align: center;
color: #475569;
font-size: 13px;
padding: 20px 0;
}

.btc-options-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
gap: 10px;
margin-bottom: 16px;
}

.btc-badge {
display: inline-block;
padding: 2px 8px;
border-radius: 4px;
font-size: 11px;
font-weight: 700;
margin-left: 6px;
vertical-align: middle;
}
.btc-badge-bin { background: #312e81; color: #a5b4fc; }
.btc-badge-hex { background: #064e3b; color: #34d399; }
.btc-badge-oct { background: #431407; color: #fb923c; }

@media (max-width: 600px) {
.btc-dir-arrows { flex-direction: column; align-items: stretch; }
.btc-dir-btn { justify-content: center; }
.btc-row { flex-direction: column; align-items: flex-start; }
.btc-options-grid { grid-template-columns: 1fr; }
}
</style>

<!-- ===== INPUT CARD ===== -->
<div class="btc-card">
<p class="btc-section-title">Input</p>

<!-- Output mode tabs -->
<div class="btc-row" style="margin-bottom:10px;">
<span style="font-size:12px;color:#64748b;font-weight:600;margin-right:4px;">Output mode:</span>
<div class="btc-mode-group">
<button class="btc-mode-btn active" data-mode="bin" onclick="btcSetMode('bin')">Binary <span class="btc-badge btc-badge-bin">01</span></button>
<button class="btc-mode-btn" data-mode="hex" onclick="btcSetMode('hex')">Hex <span class="btc-badge btc-badge-hex">0x</span></button>
<button class="btc-mode-btn" data-mode="oct" onclick="btcSetMode('oct')">Octal <span class="btc-badge btc-badge-oct">0o</span></button>
</div>
<div style="flex:1"></div>
<label class="btc-toggle-group" title="Insert a space between each code unit">
<span>Spaces</span>
<span class="btc-toggle">
<input type="checkbox" id="btcSpaces" checked onchange="btcRun()">
<span class="btc-toggle-slider"></span>
</span>
</label>
</div>

<!-- Text input -->
<div class="btc-label">
<span class="btc-label-text">Text input</span>
<span class="btc-char-count" id="btcInCount">0 chars</span>
</div>
<textarea class="btc-textarea" id="btcTextIn" placeholder="Type or paste text here…" oninput="btcEncodeRun()" rows="5"></textarea>

<!-- Encode button -->
<div class="btc-dir-arrows" style="margin-top:14px;">
<button class="btc-dir-btn btc-dir-btn-encode" onclick="btcEncodeRun()">&#x21D3; Text → Encoded</button>
</div>

<!-- Encoded output -->
<div class="btc-label" style="margin-top:14px;">
<span class="btc-label-text" id="btcOutLabel">Binary output</span>
<button class="btc-btn btc-btn-copy" id="btcCopyEnc" onclick="btcCopy('btcEncOut','btcCopyEnc')">Copy</button>
</div>
<div class="btc-output-box" id="btcEncOut" style="min-height:80px;"></div>
</div>

<!-- ===== DECODE CARD ===== -->
<div class="btc-card">
<p class="btc-section-title">Decode</p>

<div class="btc-label">
<span class="btc-label-text" id="btcDecInLabel">Binary / Hex / Octal input</span>
<button class="btc-btn btc-btn-copy" id="btcCopyDec" onclick="btcCopy('btcDecOut','btcCopyDec')">Copy result</button>
</div>
<textarea class="btc-textarea" id="btcBinIn" placeholder="Paste encoded string here (binary, hex or octal)…" oninput="btcDecodeRun()" rows="4"></textarea>
<div class="btc-error" id="btcDecErr"></div>

<!-- Decode button -->
<div class="btc-dir-arrows" style="margin-top:10px;">
<button class="btc-dir-btn btc-dir-btn-decode" onclick="btcDecodeRun()">&#x21D1; Encoded → Text</button>
</div>

<div class="btc-label" style="margin-top:14px;">
<span class="btc-label-text">Decoded text</span>
</div>
<div class="btc-output-box" id="btcDecOut" style="color:#e2e8f0;min-height:60px;"></div>
</div>

<!-- ===== BREAKDOWN CARD ===== -->
<div class="btc-card">
<p class="btc-section-title">Character-by-character breakdown</p>
<div class="btc-table-wrap">
<table class="btc-table">
<thead>
<tr>
<th>Char</th>
<th>Code point</th>
<th>Decimal</th>
<th class="td-bin">Binary (UTF-8 bytes)</th>
<th class="td-hex">Hex</th>
<th class="td-oct">Octal</th>
</tr>
</thead>
<tbody id="btcTableBody">
<tr><td colspan="6" class="btc-empty-msg">Type some text above to see the breakdown.</td></tr>
</tbody>
</table>
</div>
</div>

<script>
(function(){
var _mode = 'bin';

function setMode(m){
_mode = m;
document.querySelectorAll('#btc-app .btc-mode-btn').forEach(function(b){
b.classList.toggle('active', b.dataset.mode === m);
});
var labels = { bin: 'Binary output', hex: 'Hex output', oct: 'Octal output' };
document.getElementById('btcOutLabel').textContent = labels[m];
btcEncodeRun();
}
window.btcSetMode = setMode;

function spaces(){ return document.getElementById('btcSpaces').checked; }

/* ---- UTF-8 encode a single code point → array of bytes ---- */
function cpToUtf8Bytes(cp){
if(cp < 0x80)   return [cp];
if(cp < 0x800)  return [0xC0|(cp>>6), 0x80|(cp&0x3F)];
if(cp < 0x10000)return [0xE0|(cp>>12), 0x80|((cp>>6)&0x3F), 0x80|(cp&0x3F)];
return [0xF0|(cp>>18), 0x80|((cp>>12)&0x3F), 0x80|((cp>>6)&0x3F), 0x80|(cp&0x3F)];
}

function byteToBin(b){ return b.toString(2).padStart(8,'0'); }
function byteToHex(b){ return b.toString(16).padStart(2,'0').toUpperCase(); }
function byteToOct(b){ return b.toString(8).padStart(3,'0'); }

function encodeText(text){
var sp = spaces();
var parts = [];
for(var i=0;i<text.length;){
var cp = text.codePointAt(i);
var bytes = cpToUtf8Bytes(cp);
var unit;
if(_mode==='bin'){
unit = bytes.map(byteToBin).join(sp?' ':'');
} else if(_mode==='hex'){
unit = bytes.map(byteToHex).join(sp?' ':'');
} else {
unit = bytes.map(byteToOct).join(sp?' ':'');
}
parts.push(unit);
i += cp > 0xFFFF ? 2 : 1;
}
return parts.join(sp ? '  ' : ' ');
}

/* ---- Decode binary string → text ---- */
function decodeBin(str){
// strip extra whitespace, split on 1-2 spaces or continuous 8-bit chunks
var tokens = str.trim().split(/\s+/).filter(function(t){ return t.length>0; });
// each token may be one byte (8 bits) or multiple bytes concatenated
var allBytes = [];
for(var i=0;i<tokens.length;i++){
var t = tokens[i];
if(!/^[01]+$/.test(t)) throw new Error('Invalid binary: "'+t+'"');
if(t.length % 8 !== 0) throw new Error('Bit count not multiple of 8 (got '+t.length+' bits in "'+t+'")');
for(var j=0;j<t.length;j+=8){
allBytes.push(parseInt(t.slice(j,j+8),2));
}
}
return utf8BytesToString(allBytes);
}

/* ---- Decode hex string → text ---- */
function decodeHex(str){
var tokens = str.trim().split(/\s+/).filter(function(t){ return t.length>0; });
var allBytes = [];
for(var i=0;i<tokens.length;i++){
var t = tokens[i].replace(/^0x/i,'');
if(!/^[0-9a-fA-F]+$/.test(t)) throw new Error('Invalid hex: "'+t+'"');
if(t.length % 2 !== 0) throw new Error('Hex nibble count not even (got "'+t+'")');
for(var j=0;j<t.length;j+=2){
allBytes.push(parseInt(t.slice(j,j+2),16));
}
}
return utf8BytesToString(allBytes);
}

/* ---- Decode octal string → text ---- */
function decodeOct(str){
var tokens = str.trim().split(/\s+/).filter(function(t){ return t.length>0; });
var allBytes = [];
for(var i=0;i<tokens.length;i++){
var t = tokens[i].replace(/^0o/i,'');
if(!/^[0-7]+$/.test(t)) throw new Error('Invalid octal: "'+t+'"');
if(t.length % 3 !== 0) throw new Error('Octal digit count not multiple of 3 (got "'+t+'")');
for(var j=0;j<t.length;j+=3){
allBytes.push(parseInt(t.slice(j,j+3),8));
}
}
return utf8BytesToString(allBytes);
}

/* ---- UTF-8 bytes → JS string ---- */
function utf8BytesToString(bytes){
var result = '';
var i = 0;
while(i < bytes.length){
var b = bytes[i];
var cp, extra;
if((b & 0x80) === 0){ cp = b; extra = 0; }
else if((b & 0xE0) === 0xC0){ cp = b & 0x1F; extra = 1; }
else if((b & 0xF0) === 0xE0){ cp = b & 0x0F; extra = 2; }
else if((b & 0xF8) === 0xF0){ cp = b & 0x07; extra = 3; }
else throw new Error('Invalid UTF-8 byte: 0x'+b.toString(16));
for(var j=1;j<=extra;j++){
if(i+j >= bytes.length) throw new Error('Truncated UTF-8 sequence');
cp = (cp<<6) | (bytes[i+j] & 0x3F);
}
result += String.fromCodePoint(cp);
i += 1 + extra;
}
return result;
}

/* ---- Auto-detect mode from decode input ---- */
function detectMode(str){
var s = str.trim();
if(/^[01\s]+$/.test(s)) return 'bin';
if(/^[0-9a-fA-F\s]+$/.test(s)) return 'hex';
if(/^[0-7\s]+$/.test(s)) return 'oct';
return null;
}

/* ---- Encode run ---- */
window.btcEncodeRun = function(){
var text = document.getElementById('btcTextIn').value;
document.getElementById('btcInCount').textContent = [...text].length + ' chars';
var out = document.getElementById('btcEncOut');
if(!text){ out.textContent = ''; buildTable([]); return; }
out.textContent = encodeText(text);
buildTable(getCharData(text));
};

/* ---- Decode run ---- */
window.btcDecodeRun = function(){
var raw = document.getElementById('btcBinIn').value;
var err = document.getElementById('btcDecErr');
var out = document.getElementById('btcDecOut');
err.textContent = '';
out.textContent = '';
if(!raw.trim()) return;
try{
var m = detectMode(raw);
var result;
if(m==='bin') result = decodeBin(raw);
else if(m==='hex') result = decodeHex(raw);
else if(m==='oct') result = decodeOct(raw);
else throw new Error('Cannot detect encoding format.');
out.textContent = result;
} catch(e){
err.textContent = 'Error: ' + e.message;
}
};

window.btcRun = function(){ btcEncodeRun(); btcDecodeRun(); };

/* ---- Clipboard copy ---- */
window.btcCopy = function(srcId, btnId){
var text = document.getElementById(srcId).textContent;
if(!text) return;
var btn = document.getElementById(btnId);
navigator.clipboard.writeText(text).then(function(){
var orig = btn.textContent;
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = orig; btn.classList.remove('copied'); }, 1800);
}).catch(function(){
var ta = document.createElement('textarea');
ta.value = text; ta.style.position='fixed'; ta.style.opacity='0';
document.body.appendChild(ta); ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
var orig = btn.textContent;
btn.textContent = 'Copied!'; btn.classList.add('copied');
setTimeout(function(){ btn.textContent = orig; btn.classList.remove('copied'); }, 1800);
});
};

/* ---- Build breakdown table ---- */
function getCharData(text){
var chars = [];
for(var i=0;i<text.length;){
var cp = text.codePointAt(i);
var bytes = cpToUtf8Bytes(cp);
chars.push({ ch: String.fromCodePoint(cp), cp: cp, bytes: bytes });
i += cp > 0xFFFF ? 2 : 1;
}
return chars;
}

function buildTable(chars){
var tb = document.getElementById('btcTableBody');
if(!chars.length){
tb.innerHTML = '<tr><td colspan="6" class="btc-empty-msg">Type some text above to see the breakdown.</td></tr>';
return;
}
var limit = 200;
var rows = '';
var shown = Math.min(chars.length, limit);
for(var i=0;i<shown;i++){
var c = chars[i];
var binStr = c.bytes.map(byteToBin).join(' ');
var hexStr = c.bytes.map(byteToHex).join(' ');
var octStr = c.bytes.map(byteToOct).join(' ');
var display = c.ch === ' ' ? '&nbsp;(space)' : c.ch === '\n' ? '&#x21B5;(LF)' : c.ch === '\t' ? '&#x21B9;(TAB)' : escHtml(c.ch);
rows += '<tr>'
+ '<td class="td-char">'+display+'</td>'
+ '<td class="td-cp">U+'+c.cp.toString(16).toUpperCase().padStart(4,'0')+'</td>'
+ '<td class="td-dec">'+c.cp+'</td>'
+ '<td class="td-bin">'+binStr+'</td>'
+ '<td class="td-hex">'+hexStr+'</td>'
+ '<td class="td-oct">'+octStr+'</td>'
+ '</tr>';
}
if(chars.length > limit){
rows += '<tr><td colspan="6" class="btc-empty-msg">… and '+(chars.length-limit)+' more characters (showing first '+limit+')</td></tr>';
}
tb.innerHTML = rows;
}

function escHtml(s){
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}
})();
</script>

---

### Related Tools
> Convert number bases → [Number Base Converter](/tools/number-base-converter/)
> Encode Base64 → [Base64 Encoder](/tools/base64-encoder/)
> Translate Morse code → [Morse Code Translator](/tools/morse-code/)
</div>
