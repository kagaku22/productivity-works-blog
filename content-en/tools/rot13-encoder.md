---
title: "ROT13 / Caesar Cipher Encoder & Decoder"
date: 2025-05-16
slug: "rot13-encoder"
categories: ["Free Tools"]
tags: ["Developer Tools", "Code Conversion", "Free Tools"]
aliases: ["/tools/rot13-encoder/", "/tools/rot13-encoder/"]
ShowToc: false
cover:
  image: "/images/covers/rot13-encoder.png"
  alt: "ROT13 Encoder"
description: "Free online ROT13 encoder and Caesar cipher tool. Supports ROT5, ROT47, adjustable shift, brute-force all 25 shifts, encode/decode toggle — no install needed."
---

<style>
#rot-app *,
#rot-app *::before,
#rot-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#rot-app {
font-family: 'Courier New', Courier, monospace;
background: #1a2e1a;
color: #ffb300;
border-radius: 8px;
padding: 24px;
max-width: 820px;
margin: 0 auto 2rem auto;
border: 1px solid #2e4d2e;
}

#rot-app h2 {
font-size: 1.1rem;
letter-spacing: 0.12em;
text-transform: uppercase;
color: #ffd54f;
margin-bottom: 18px;
border-bottom: 1px solid #2e4d2e;
padding-bottom: 10px;
}

#rot-app .row {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 14px;
align-items: center;
}

#rot-app label {
font-size: 0.78rem;
letter-spacing: 0.08em;
color: #ffd54f;
text-transform: uppercase;
display: block;
margin-bottom: 5px;
}

#rot-app select,
#rot-app button {
background: #0f1f0f;
color: #ffb300;
border: 1px solid #3a5c3a;
border-radius: 4px;
padding: 7px 14px;
font-family: inherit;
font-size: 0.88rem;
cursor: pointer;
transition: border-color 0.15s, background 0.15s;
}

#rot-app select:focus,
#rot-app button:focus {
outline: 2px solid #ffb300;
outline-offset: 2px;
}

#rot-app button:hover {
background: #1e3d1e;
border-color: #ffb300;
}

#rot-app button.active,
#rot-app button[data-active="true"] {
background: #ffb300;
color: #0f1f0f;
border-color: #ffb300;
font-weight: 700;
}

#rot-app .btn-group {
display: flex;
gap: 6px;
}

#rot-app textarea {
width: 100%;
background: #0f1f0f;
color: #ffb300;
border: 1px solid #3a5c3a;
border-radius: 4px;
padding: 12px;
font-family: inherit;
font-size: 0.92rem;
resize: vertical;
min-height: 110px;
line-height: 1.55;
transition: border-color 0.15s;
}

#rot-app textarea:focus {
outline: none;
border-color: #ffb300;
}

#rot-app textarea[readonly] {
color: #ffd54f;
cursor: default;
}

#rot-app .slider-wrap {
width: 100%;
margin-bottom: 14px;
}

#rot-app .slider-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 8px;
}

#rot-app input[type=range] {
-webkit-appearance: none;
appearance: none;
flex: 1;
height: 6px;
background: #2e4d2e;
border-radius: 3px;
outline: none;
cursor: pointer;
}

#rot-app input[type=range]::-webkit-slider-thumb {
-webkit-appearance: none;
appearance: none;
width: 18px;
height: 18px;
border-radius: 50%;
background: #ffb300;
cursor: pointer;
border: 2px solid #0f1f0f;
}

#rot-app input[type=range]::-moz-range-thumb {
width: 18px;
height: 18px;
border-radius: 50%;
background: #ffb300;
cursor: pointer;
border: 2px solid #0f1f0f;
}

#rot-app .shift-badge {
background: #ffb300;
color: #0f1f0f;
font-weight: 700;
border-radius: 4px;
padding: 2px 10px;
font-size: 1rem;
min-width: 38px;
text-align: center;
}

#rot-app .alpha-map {
font-size: 0.72rem;
letter-spacing: 0.05em;
color: #8fbc8f;
background: #0f1f0f;
border: 1px solid #2e4d2e;
border-radius: 4px;
padding: 7px 10px;
overflow-x: auto;
white-space: nowrap;
line-height: 1.8;
}

#rot-app .alpha-map span.hi {
color: #ffb300;
font-weight: 700;
}

#rot-app .section-label {
font-size: 0.72rem;
letter-spacing: 0.1em;
text-transform: uppercase;
color: #8fbc8f;
margin-bottom: 4px;
}

#rot-app .copy-btn {
margin-top: 8px;
padding: 6px 18px;
font-size: 0.82rem;
}

#rot-app .copy-btn.copied {
background: #388e3c;
color: #fff;
border-color: #388e3c;
}

#rot-app .brute-table {
width: 100%;
border-collapse: collapse;
font-size: 0.8rem;
margin-top: 8px;
}

#rot-app .brute-table th {
background: #2e4d2e;
color: #ffd54f;
text-align: left;
padding: 5px 8px;
font-weight: 700;
letter-spacing: 0.06em;
}

#rot-app .brute-table td {
padding: 4px 8px;
border-bottom: 1px solid #1e3d1e;
color: #ffb300;
word-break: break-all;
}

#rot-app .brute-table tr:hover td {
background: #1e3d1e;
}

#rot-app .brute-table td:first-child {
color: #8fbc8f;
font-weight: 700;
width: 40px;
white-space: nowrap;
}

#rot-app .hidden {
display: none;
}

#rot-app .divider {
border: none;
border-top: 1px solid #2e4d2e;
margin: 18px 0;
}

#rot-app .mode-tag {
font-size: 0.7rem;
letter-spacing: 0.12em;
text-transform: uppercase;
color: #8fbc8f;
background: #1e3d1e;
border-radius: 3px;
padding: 2px 8px;
margin-left: 6px;
vertical-align: middle;
}
</style>

<div id="rot-app">

<h2>ROT13 / Caesar Cipher <span class="mode-tag" id="modeTag">ROT13</span></h2>

<!-- Mode selector -->
<div class="row">
<div>
<label>Cipher Mode</label>
<div class="btn-group">
<button id="btnRot13" data-active="true" onclick="rotSetMode('rot13')">ROT13</button>
<button id="btnRot5" onclick="rotSetMode('rot5')">ROT5</button>
<button id="btnRot47" onclick="rotSetMode('rot47')">ROT47</button>
<button id="btnCaesar" onclick="rotSetMode('caesar')">Caesar</button>
</div>
</div>
<div>
<label>Direction</label>
<div class="btn-group">
<button id="btnEncode" data-active="true" onclick="rotSetDir('encode')">Encode</button>
<button id="btnDecode" onclick="rotSetDir('decode')">Decode</button>
</div>
</div>
<div>
<label>View</label>
<div class="btn-group">
<button id="btnNormal" data-active="true" onclick="rotSetView('normal')">Normal</button>
<button id="btnBrute" onclick="rotSetView('brute')">Brute Force</button>
</div>
</div>
</div>

<!-- Caesar shift slider -->
<div class="slider-wrap" id="sliderWrap" style="display:none">
<div class="slider-row">
<label style="margin:0;white-space:nowrap">Shift</label>
<input type="range" id="shiftSlider" min="1" max="25" value="13" oninput="rotUpdateShift(this.value)">
<span class="shift-badge" id="shiftBadge">13</span>
</div>
<div class="alpha-map" id="alphaMap"></div>
</div>

<!-- Input -->
<div class="section-label">Input</div>
<textarea id="rotInput" placeholder="Type or paste text here..." oninput="rotProcess()"></textarea>

<hr class="divider">

<!-- Normal output -->
<div id="normalView">
<div class="section-label">Output</div>
<textarea id="rotOutput" readonly placeholder="Output will appear here..."></textarea>
<button class="copy-btn" id="copyBtn" onclick="rotCopy()">Copy Output</button>
</div>

<!-- Brute force output -->
<div id="bruteView" class="hidden">
<div class="section-label">Brute Force — All 25 Caesar Shifts</div>
<div style="overflow-x:auto">
<table class="brute-table" id="bruteTable">
<thead><tr><th>Shift</th><th>Output</th></tr></thead>
<tbody id="bruteTbody"></tbody>
</table>
</div>
</div>

</div>

<script>
(function(){
var state = {
mode: 'rot13',
dir: 'encode',
shift: 13,
view: 'normal'
};

window.rotSetMode = function(m) {
state.mode = m;
['rot13','rot5','rot47','caesar'].forEach(function(x){
var b = document.getElementById('btn' + x.charAt(0).toUpperCase() + x.slice(1));
if(b) b.dataset.active = (x === m) ? 'true' : 'false';
});
document.getElementById('sliderWrap').style.display = (m === 'caesar') ? 'block' : 'none';
if(m === 'caesar') rotRenderAlphaMap(state.shift, state.dir);
document.getElementById('modeTag').textContent = m.toUpperCase();
rotProcess();
};

window.rotSetDir = function(d) {
state.dir = d;
document.getElementById('btnEncode').dataset.active = (d === 'encode') ? 'true' : 'false';
document.getElementById('btnDecode').dataset.active = (d === 'decode') ? 'true' : 'false';
if(state.mode === 'caesar') rotRenderAlphaMap(state.shift, d);
rotProcess();
};

window.rotSetView = function(v) {
state.view = v;
document.getElementById('btnNormal').dataset.active = (v === 'normal') ? 'true' : 'false';
document.getElementById('btnBrute').dataset.active = (v === 'brute') ? 'true' : 'false';
document.getElementById('normalView').classList.toggle('hidden', v !== 'normal');
document.getElementById('bruteView').classList.toggle('hidden', v !== 'brute');
rotProcess();
};

window.rotUpdateShift = function(v) {
state.shift = parseInt(v, 10);
document.getElementById('shiftBadge').textContent = v;
rotRenderAlphaMap(state.shift, state.dir);
rotProcess();
};

function rotRenderAlphaMap(shift, dir) {
var plain = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
var s = (dir === 'decode') ? (26 - shift) % 26 : shift;
var cipher = plain.split('').map(function(c){
return plain[(plain.indexOf(c) + s) % 26];
}).join('');
var html = '<b style="color:#8fbc8f">Plain:&nbsp;</b>';
for(var i=0;i<26;i++){
html += '<span>' + plain[i] + '</span>';
if(i<25) html += ' ';
}
html += '<br><b style="color:#8fbc8f">Ciph:&nbsp;&nbsp;</b>';
for(var j=0;j<26;j++){
html += '<span class="hi">' + cipher[j] + '</span>';
if(j<25) html += ' ';
}
document.getElementById('alphaMap').innerHTML = html;
}

function rot13char(c) {
if(c >= 'a' && c <= 'z') return String.fromCharCode(((c.charCodeAt(0) - 97 + 13) % 26) + 97);
if(c >= 'A' && c <= 'Z') return String.fromCharCode(((c.charCodeAt(0) - 65 + 13) % 26) + 65);
return c;
}

function rot5char(c) {
if(c >= '0' && c <= '9') return String.fromCharCode(((c.charCodeAt(0) - 48 + 5) % 10) + 48);
return c;
}

function rot47char(c) {
var code = c.charCodeAt(0);
if(code >= 33 && code <= 126) return String.fromCharCode(((code - 33 + 47) % 94) + 33);
return c;
}

function caesarChar(c, shift) {
if(c >= 'a' && c <= 'z') return String.fromCharCode(((c.charCodeAt(0) - 97 + shift + 26) % 26) + 97);
if(c >= 'A' && c <= 'Z') return String.fromCharCode(((c.charCodeAt(0) - 65 + shift + 26) % 26) + 65);
return c;
}

function applyMode(text, mode, dir, shift) {
var effectiveShift = shift;
if(mode === 'caesar' && dir === 'decode') effectiveShift = (26 - shift) % 26;
return text.split('').map(function(c){
if(mode === 'rot13') return rot13char(c);
if(mode === 'rot5') return rot5char(c);
if(mode === 'rot47') return rot47char(c);
if(mode === 'caesar') return caesarChar(c, effectiveShift);
return c;
}).join('');
}

window.rotProcess = function() {
var input = document.getElementById('rotInput').value;
if(state.view === 'normal') {
var out = applyMode(input, state.mode, state.dir, state.shift);
document.getElementById('rotOutput').value = out;
} else {
var tbody = document.getElementById('bruteTbody');
var rows = '';
for(var s = 1; s <= 25; s++) {
var result = applyMode(input, 'caesar', 'encode', s);
rows += '<tr><td>+' + s + '</td><td>' + escHtml(result) + '</td></tr>';
}
tbody.innerHTML = rows;
}
};

function escHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

window.rotCopy = function() {
var out = document.getElementById('rotOutput').value;
if(!out) return;
navigator.clipboard.writeText(out).then(function(){
var btn = document.getElementById('copyBtn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = 'Copy Output'; btn.classList.remove('copied'); }, 1800);
}).catch(function(){
var ta = document.createElement('textarea');
ta.value = out;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
});
};
})();
</script>

## How It Works

**ROT13** rotates each letter by 13 positions in the alphabet. Since the English alphabet has 26 letters, ROT13 is its own inverse — applying it twice returns the original text. It is commonly used to obscure spoilers or puzzle answers online.

**Caesar cipher** is the generalized form: rotate by any shift from 1 to 25. Julius Caesar reportedly used a shift of 3. The **Decode** direction reverses the shift automatically.

**ROT5** applies the same rotation concept to digits (0–9) with a shift of 5. It is often combined with ROT13 as ROT18.

**ROT47** operates on all 94 printable ASCII characters (! through ~), rotating by 47. It encodes punctuation and symbols as well as letters and digits.

**Brute force mode** runs all 25 possible Caesar shifts at once, which is useful when you have an unknown shift and want to scan for readable plaintext.

### Alphabet Mapping Reference

| Plain  | A | B | C | D | E | F | G | H | I | J | K | L | M |
|--------|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ROT13  | N | O | P | Q | R | S | T | U | V | W | X | Y | Z |

| Plain  | N | O | P | Q | R | S | T | U | V | W | X | Y | Z |
|--------|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ROT13  | A | B | C | D | E | F | G | H | I | J | K | L | M |

---

Related: Hash data → [Hash Generator](/tools/hash-generator/)
