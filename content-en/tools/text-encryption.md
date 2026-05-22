---
title: "Text Encryption & Decryption"
date: 2025-05-16
description: "Free text encryption tool. Encrypt and decrypt text using AES-256, Caesar cipher, Vigenere cipher, and XOR. All processing done locally in your browser."
categories: ["Free Tools"]
tags: ["Text Tools", "String Processing", "Free Tools"]
slug: "text-encryption"
ShowToc: false
cover:
  image: "/images/covers/text-encryption.png"
  alt: "Text Encryption & Decryption"
---

<div id="te-app">

<style>
#te-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1e293b;
}
#te-app *, #te-app *::before, #te-app *::after {
box-sizing: border-box;
}
/* ---- Tab bar ---- */
#te-app .te-tab-bar {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 20px;
overflow-x: auto;
}
#te-app .te-tab {
padding: 9px 20px;
font-size: 13px;
font-weight: 600;
color: #64748b;
cursor: pointer;
border: none;
background: none;
border-bottom: 2.5px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
white-space: nowrap;
}
#te-app .te-tab.active { color: #7c3aed; border-bottom-color: #7c3aed; }
#te-app .te-tab:hover:not(.active) { color: #334155; }
/* ---- Panel ---- */
#te-app .te-panel { display: none; }
#te-app .te-panel.active { display: block; }
/* ---- Card ---- */
#te-app .te-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 18px 20px;
margin-bottom: 16px;
}
/* ---- Labels ---- */
#te-app .te-label {
display: block;
font-size: 11px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
margin-bottom: 6px;
}
/* ---- Textareas ---- */
#te-app .te-textarea {
width: 100%;
min-height: 110px;
padding: 11px 13px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 14px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", monospace;
resize: vertical;
background: #fff;
color: #1e293b;
transition: border-color 0.2s, box-shadow 0.2s;
}
#te-app .te-textarea:focus {
outline: none;
border-color: #7c3aed;
box-shadow: 0 0 0 3px rgba(124,58,237,0.12);
}
/* ---- Select ---- */
#te-app .te-select {
padding: 8px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 13px;
background: #fff;
color: #1e293b;
cursor: pointer;
transition: border-color 0.2s;
min-width: 160px;
}
#te-app .te-select:focus { outline: none; border-color: #7c3aed; }
/* ---- Input field ---- */
#te-app .te-input {
padding: 8px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 13px;
font-family: "SFMono-Regular", Consolas, monospace;
background: #fff;
color: #1e293b;
transition: border-color 0.2s, box-shadow 0.2s;
width: 100%;
}
#te-app .te-input:focus {
outline: none;
border-color: #7c3aed;
box-shadow: 0 0 0 3px rgba(124,58,237,0.12);
}
/* ---- Controls row ---- */
#te-app .te-row {
display: flex;
flex-wrap: wrap;
align-items: flex-end;
gap: 10px;
margin-bottom: 12px;
}
#te-app .te-field {
display: flex;
flex-direction: column;
gap: 4px;
flex: 1;
min-width: 140px;
}
/* ---- Mode toggle ---- */
#te-app .te-mode-group {
display: flex;
border: 1.5px solid #e2e8f0;
border-radius: 7px;
overflow: hidden;
flex-shrink: 0;
}
#te-app .te-mode-btn {
padding: 8px 18px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
border: none;
background: #f1f5f9;
color: #64748b;
transition: background 0.15s, color 0.15s;
line-height: 1;
}
#te-app .te-mode-btn.active { background: #7c3aed; color: #fff; }
#te-app .te-mode-btn:hover:not(.active) { background: #e2e8f0; }
/* ---- Buttons ---- */
#te-app .te-btn {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 9px 18px;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
border: none;
transition: background 0.18s, transform 0.1s;
user-select: none;
line-height: 1;
white-space: nowrap;
}
#te-app .te-btn:active { transform: scale(0.97); }
#te-app .te-btn-primary   { background: #7c3aed; color: #fff; }
#te-app .te-btn-primary:hover { background: #6d28d9; }
#te-app .te-btn-secondary { background: #e2e8f0; color: #374151; }
#te-app .te-btn-secondary:hover { background: #cbd5e1; }
/* ---- Output area ---- */
#te-app .te-output-wrap {
display: none;
margin-top: 4px;
}
#te-app .te-output-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 6px;
}
#te-app .te-output-label {
font-size: 11px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#te-app .te-output-ta {
width: 100%;
min-height: 100px;
padding: 11px 13px;
border: 1.5px solid #c4b5fd;
border-radius: 8px;
font-size: 14px;
font-family: "SFMono-Regular", Consolas, monospace;
resize: vertical;
background: #faf5ff;
color: #1e293b;
word-break: break-all;
}
/* ---- Status ---- */
#te-app .te-status {
display: flex;
align-items: center;
gap: 8px;
padding: 9px 14px;
border-radius: 8px;
font-size: 13px;
margin-bottom: 14px;
}
#te-app .te-status.ok   { background:#f0fdf4; border:1px solid #bbf7d0; color:#166534; }
#te-app .te-status.err  { background:#fef2f2; border:1px solid #fecaca; color:#991b1b; }
#te-app .te-status.hidden { display:none; }
/* ---- Shift range ---- */
#te-app .te-shift-row {
display: flex;
align-items: center;
gap: 10px;
}
#te-app .te-range {
flex: 1;
accent-color: #7c3aed;
cursor: pointer;
}
#te-app .te-shift-val {
min-width: 28px;
text-align: center;
font-weight: 700;
font-size: 15px;
color: #7c3aed;
}
/* ---- Badge ---- */
#te-app .te-badge {
display: inline-block;
padding: 3px 9px;
border-radius: 5px;
font-size: 11px;
font-weight: 700;
white-space: nowrap;
letter-spacing: 0.04em;
background: #ede9fe;
color: #5b21b6;
}
/* ---- Copy button ---- */
#te-app .te-copy {
display: inline-flex;
align-items: center;
gap: 4px;
padding: 5px 12px;
border-radius: 6px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
border: 1.5px solid #e2e8f0;
background: #fff;
color: #475569;
transition: all 0.15s;
white-space: nowrap;
}
#te-app .te-copy:hover   { border-color:#7c3aed; color:#7c3aed; background:#f5f3ff; }
#te-app .te-copy.copied  { border-color:#10b981; color:#10b981; background:#ecfdf5; }
/* ---- Info box ---- */
#te-app .te-info {
padding: 12px 16px;
background: #f5f3ff;
border: 1px solid #ddd6fe;
border-radius: 8px;
font-size: 12.5px;
color: #4c1d95;
line-height: 1.6;
margin-bottom: 14px;
}
/* ---- AES progress ---- */
#te-app .te-progress {
display: none;
align-items: center;
gap: 10px;
margin-top: 8px;
font-size: 12px;
color: #7c3aed;
}
#te-app .te-progress.visible { display: flex; }
#te-app .te-progress-track {
flex: 1; height: 4px;
background: #ede9fe;
border-radius: 3px;
overflow: hidden;
}
#te-app .te-progress-fill {
height: 100%;
background: #7c3aed;
border-radius: 3px;
width: 0%;
transition: width 0.2s;
}
/* ---- Toast ---- */
.te-toast {
position: fixed;
bottom: 24px; right: 24px;
background: #7c3aed; color: #fff;
padding: 10px 18px;
border-radius: 8px;
font-size: 13px;
font-weight: 600;
z-index: 9999;
box-shadow: 0 4px 16px rgba(0,0,0,0.18);
transition: opacity 0.3s;
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}
@media (max-width: 540px) {
#te-app .te-mode-btn { padding: 8px 12px; }
#te-app .te-tab { padding: 9px 14px; }
}
</style>

<!-- TAB BAR -->
<div class="te-tab-bar">
<button class="te-tab active" onclick="teTab('caesar',this)">Caesar</button>
<button class="te-tab" onclick="teTab('vigenere',this)">Vigenere</button>
<button class="te-tab" onclick="teTab('xor',this)">XOR</button>
<button class="te-tab" onclick="teTab('aes',this)">AES-256</button>
</div>

<!-- ===== CAESAR PANEL ===== -->
<div id="te-panel-caesar" class="te-panel active">
<div class="te-card">
<div class="te-info">
Caesar cipher shifts each letter by a fixed number of positions in the alphabet. The same shift is used for both encryption and decryption (just use the inverse). Non-letter characters are preserved unchanged.
</div>
<div class="te-row">
<div class="te-field" style="max-width:260px">
<span class="te-label">Shift (1–25)</span>
<div class="te-shift-row">
<input type="range" class="te-range" id="te-cs-range" min="1" max="25" value="13"
oninput="document.getElementById('te-cs-val').textContent=this.value; teCaesarRun()">
<span class="te-shift-val" id="te-cs-val">13</span>
</div>
</div>
<div class="te-field">
<span class="te-label">Mode</span>
<div class="te-mode-group">
<button class="te-mode-btn active" id="te-cs-enc-btn" onclick="teSetMode('caesar','encrypt')">Encrypt</button>
<button class="te-mode-btn" id="te-cs-dec-btn" onclick="teSetMode('caesar','decrypt')">Decrypt</button>
</div>
</div>
</div>
<span class="te-label">Input Text</span>
<textarea id="te-cs-input" class="te-textarea" placeholder="Type or paste text here…" oninput="teCaesarRun()"></textarea>
<div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
<button class="te-btn te-btn-primary" onclick="teCaesarRun()">&#128274; Run Caesar</button>
<button class="te-btn te-btn-secondary" onclick="teClearPanel('caesar')">Clear</button>
</div>
</div>
<div class="te-status hidden" id="te-cs-status"></div>
<div class="te-output-wrap" id="te-cs-output-wrap">
<div class="te-output-header">
<span class="te-output-label">Result <span class="te-badge" id="te-cs-badge">Encrypted</span></span>
<button class="te-copy" id="te-cs-copy" onclick="teCopyOutput('te-cs-out',this)">&#128203; Copy</button>
</div>
<textarea id="te-cs-out" class="te-output-ta" readonly></textarea>
</div>
</div>

<!-- ===== VIGENERE PANEL ===== -->
<div id="te-panel-vigenere" class="te-panel">
<div class="te-card">
<div class="te-info">
Vigenere cipher uses a keyword to apply a different Caesar shift to each character. The keyword repeats to match the input length. Only letters A–Z and a–z are shifted; everything else passes through unchanged.
</div>
<div class="te-row">
<div class="te-field">
<span class="te-label">Keyword</span>
<input type="text" id="te-vig-key" class="te-input" placeholder="e.g. SECRET" oninput="teVigenereRun()">
</div>
<div class="te-field" style="flex:0;min-width:auto">
<span class="te-label">Mode</span>
<div class="te-mode-group">
<button class="te-mode-btn active" id="te-vig-enc-btn" onclick="teSetMode('vigenere','encrypt')">Encrypt</button>
<button class="te-mode-btn" id="te-vig-dec-btn" onclick="teSetMode('vigenere','decrypt')">Decrypt</button>
</div>
</div>
</div>
<span class="te-label">Input Text</span>
<textarea id="te-vig-input" class="te-textarea" placeholder="Type or paste text here…" oninput="teVigenereRun()"></textarea>
<div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
<button class="te-btn te-btn-primary" onclick="teVigenereRun()">&#128274; Run Vigenere</button>
<button class="te-btn te-btn-secondary" onclick="teClearPanel('vigenere')">Clear</button>
</div>
</div>
<div class="te-status hidden" id="te-vig-status"></div>
<div class="te-output-wrap" id="te-vig-output-wrap">
<div class="te-output-header">
<span class="te-output-label">Result <span class="te-badge" id="te-vig-badge">Encrypted</span></span>
<button class="te-copy" id="te-vig-copy" onclick="teCopyOutput('te-vig-out',this)">&#128203; Copy</button>
</div>
<textarea id="te-vig-out" class="te-output-ta" readonly></textarea>
</div>
</div>

<!-- ===== XOR PANEL ===== -->
<div id="te-panel-xor" class="te-panel">
<div class="te-card">
<div class="te-info">
XOR cipher applies a bitwise XOR between each character and the repeating key. Applying the same key twice restores the original — so Encrypt and Decrypt are identical operations. Output is Base64-encoded to stay readable.
</div>
<div class="te-row">
<div class="te-field">
<span class="te-label">Key (any text)</span>
<input type="text" id="te-xor-key" class="te-input" placeholder="e.g. myKey123" oninput="teXorRun()">
</div>
<div class="te-field" style="flex:0;min-width:auto">
<span class="te-label">Mode</span>
<div class="te-mode-group">
<button class="te-mode-btn active" id="te-xor-enc-btn" onclick="teSetMode('xor','encrypt')">Encrypt</button>
<button class="te-mode-btn" id="te-xor-dec-btn" onclick="teSetMode('xor','decrypt')">Decrypt</button>
</div>
</div>
</div>
<span class="te-label">Input Text</span>
<textarea id="te-xor-input" class="te-textarea" placeholder="Plain text to encrypt, or Base64 XOR ciphertext to decrypt…" oninput="teXorRun()"></textarea>
<div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
<button class="te-btn te-btn-primary" onclick="teXorRun()">&#128274; Run XOR</button>
<button class="te-btn te-btn-secondary" onclick="teClearPanel('xor')">Clear</button>
</div>
</div>
<div class="te-status hidden" id="te-xor-status"></div>
<div class="te-output-wrap" id="te-xor-output-wrap">
<div class="te-output-header">
<span class="te-output-label">Result <span class="te-badge" id="te-xor-badge">Encrypted</span></span>
<button class="te-copy" id="te-xor-copy" onclick="teCopyOutput('te-xor-out',this)">&#128203; Copy</button>
</div>
<textarea id="te-xor-out" class="te-output-ta" readonly></textarea>
</div>
</div>

<!-- ===== AES-256 PANEL ===== -->
<div id="te-panel-aes" class="te-panel">
<div class="te-card">
<div class="te-info">
AES-256-GCM via the browser's native <strong>Web Crypto API</strong>. A random 96-bit IV is generated per encryption; ciphertext is stored as <code>iv:ciphertext</code> in Base64. Decryption automatically extracts the IV. Your password never leaves the browser.
</div>
<div class="te-row">
<div class="te-field">
<span class="te-label">Password</span>
<input type="password" id="te-aes-pw" class="te-input" placeholder="Enter a strong password…" oninput="teAesRun()">
</div>
<div class="te-field" style="flex:0;min-width:auto">
<span class="te-label">Mode</span>
<div class="te-mode-group">
<button class="te-mode-btn active" id="te-aes-enc-btn" onclick="teSetMode('aes','encrypt')">Encrypt</button>
<button class="te-mode-btn" id="te-aes-dec-btn" onclick="teSetMode('aes','decrypt')">Decrypt</button>
</div>
</div>
</div>
<span class="te-label">Input Text</span>
<textarea id="te-aes-input" class="te-textarea" placeholder="Plain text to encrypt, or Base64 AES ciphertext to decrypt…" oninput="teAesRun()"></textarea>
<div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
<button class="te-btn te-btn-primary" onclick="teAesRun()">&#128274; Run AES-256</button>
<button class="te-btn te-btn-secondary" onclick="teClearPanel('aes')">Clear</button>
</div>
<div class="te-progress" id="te-aes-prog">
<span id="te-aes-prog-lbl">Processing…</span>
<div class="te-progress-track"><div class="te-progress-fill" id="te-aes-prog-fill"></div></div>
</div>
</div>
<div class="te-status hidden" id="te-aes-status"></div>
<div class="te-output-wrap" id="te-aes-output-wrap">
<div class="te-output-header">
<span class="te-output-label">Result <span class="te-badge" id="te-aes-badge">Encrypted</span></span>
<button class="te-copy" id="te-aes-copy" onclick="teCopyOutput('te-aes-out',this)">&#128203; Copy</button>
</div>
<textarea id="te-aes-out" class="te-output-ta" readonly></textarea>
</div>
</div>

<script>
(function () {
'use strict';

/* ============================================================
State
============================================================ */
var teMode = { caesar: 'encrypt', vigenere: 'encrypt', xor: 'encrypt', aes: 'encrypt' };
var teAesDebounce = null;

/* ============================================================
Tab switching
============================================================ */
window.teTab = function(name, btn) {
document.querySelectorAll('#te-app .te-tab').forEach(function(t){ t.classList.remove('active'); });
document.querySelectorAll('#te-app .te-panel').forEach(function(p){ p.classList.remove('active'); });
btn.classList.add('active');
document.getElementById('te-panel-'+name).classList.add('active');
};

/* ============================================================
Mode toggle
============================================================ */
window.teSetMode = function(cipher, mode) {
teMode[cipher] = mode;
var encBtn = document.getElementById('te-'+cipher.slice(0,3)+'-enc-btn') ||
document.getElementById('te-vig-enc-btn') ||
document.getElementById('te-xor-enc-btn') ||
document.getElementById('te-aes-enc-btn');
var decBtn = document.getElementById('te-'+cipher.slice(0,3)+'-dec-btn') ||
document.getElementById('te-vig-dec-btn') ||
document.getElementById('te-xor-dec-btn') ||
document.getElementById('te-aes-dec-btn');
// Find buttons within the active panel
var prefix = cipher === 'caesar' ? 'cs' : cipher === 'vigenere' ? 'vig' : cipher === 'xor' ? 'xor' : 'aes';
document.getElementById('te-'+prefix+'-enc-btn').classList.toggle('active', mode==='encrypt');
document.getElementById('te-'+prefix+'-dec-btn').classList.toggle('active', mode==='decrypt');
var badge = document.getElementById('te-'+prefix+'-badge');
if (badge) badge.textContent = mode === 'encrypt' ? 'Encrypted' : 'Decrypted';
// Re-run
if (cipher === 'caesar')   teCaesarRun();
if (cipher === 'vigenere') teVigenereRun();
if (cipher === 'xor')      teXorRun();
if (cipher === 'aes')      teAesRun();
};

/* ============================================================
Status helpers
============================================================ */
function teStatus(id, html, cls) {
var el = document.getElementById(id);
el.innerHTML = html;
el.className = 'te-status ' + cls;
}
function teShowOutput(prefix, text, mode) {
document.getElementById('te-'+prefix+'-out').value = text;
document.getElementById('te-'+prefix+'-output-wrap').style.display = 'block';
if (document.getElementById('te-'+prefix+'-badge'))
document.getElementById('te-'+prefix+'-badge').textContent = mode === 'encrypt' ? 'Encrypted' : 'Decrypted';
}
function teHideOutput(prefix) {
document.getElementById('te-'+prefix+'-output-wrap').style.display = 'none';
}

/* ============================================================
Clear panels
============================================================ */
window.teClearPanel = function(cipher) {
var prefix = cipher === 'caesar' ? 'cs' : cipher === 'vigenere' ? 'vig' : cipher === 'xor' ? 'xor' : 'aes';
var inp = document.getElementById('te-'+prefix+'-input') || document.getElementById('te-cs-input');
if (cipher === 'caesar')   document.getElementById('te-cs-input').value = '';
if (cipher === 'vigenere') document.getElementById('te-vig-input').value = '';
if (cipher === 'xor')      document.getElementById('te-xor-input').value = '';
if (cipher === 'aes')      document.getElementById('te-aes-input').value = '';
teHideOutput(prefix);
teStatus('te-'+prefix+'-status','','hidden');
};

/* ============================================================
Copy helper
============================================================ */
window.teCopyOutput = function(taId, btn) {
var val = document.getElementById(taId).value;
if (!val) return;
navigator.clipboard.writeText(val).then(function() {
btn.innerHTML = '&#10003; Copied';
btn.classList.add('copied');
setTimeout(function(){ btn.innerHTML='&#128203; Copy'; btn.classList.remove('copied'); }, 1800);
});
};

function teToast(msg) {
var t = document.createElement('div');
t.className = 'te-toast';
t.textContent = msg;
document.body.appendChild(t);
setTimeout(function(){ t.style.opacity='0'; setTimeout(function(){ t.remove(); },300); }, 1700);
}

/* ============================================================
Caesar Cipher
============================================================ */
function caesarShift(text, shift, decrypt) {
if (decrypt) shift = (26 - shift) % 26;
var result = '';
for (var i = 0; i < text.length; i++) {
var c = text.charCodeAt(i);
if (c >= 65 && c <= 90) {
result += String.fromCharCode(((c - 65 + shift) % 26) + 65);
} else if (c >= 97 && c <= 122) {
result += String.fromCharCode(((c - 97 + shift) % 26) + 97);
} else {
result += text[i];
}
}
return result;
}

window.teCaesarRun = function() {
var text  = document.getElementById('te-cs-input').value;
var shift = parseInt(document.getElementById('te-cs-range').value, 10);
var mode  = teMode.caesar;
if (!text) { teHideOutput('cs'); teStatus('te-cs-status','','hidden'); return; }
var out = caesarShift(text, shift, mode === 'decrypt');
teShowOutput('cs', out, mode);
teStatus('te-cs-status', '&#10003; ' + (mode==='encrypt'?'Encrypted':'Decrypted') + ' with shift ' + shift, 'ok');
};

/* ============================================================
Vigenere Cipher
============================================================ */
function vigenereProcess(text, key, decrypt) {
if (!key) return text;
key = key.toUpperCase().replace(/[^A-Z]/g, '');
if (!key.length) return text;
var result = '';
var ki = 0;
for (var i = 0; i < text.length; i++) {
var c = text.charCodeAt(i);
var k = key.charCodeAt(ki % key.length) - 65;
if (c >= 65 && c <= 90) {
var shifted = decrypt ? ((c - 65 - k + 26) % 26) : ((c - 65 + k) % 26);
result += String.fromCharCode(shifted + 65);
ki++;
} else if (c >= 97 && c <= 122) {
var shifted2 = decrypt ? ((c - 97 - k + 26) % 26) : ((c - 97 + k) % 26);
result += String.fromCharCode(shifted2 + 97);
ki++;
} else {
result += text[i];
}
}
return result;
}

window.teVigenereRun = function() {
var text = document.getElementById('te-vig-input').value;
var key  = document.getElementById('te-vig-key').value;
var mode = teMode.vigenere;
if (!text) { teHideOutput('vig'); teStatus('te-vig-status','','hidden'); return; }
if (!key || !key.replace(/[^A-Za-z]/g,'').length) {
teStatus('te-vig-status','&#9888; Please enter a keyword (letters only).','err');
teHideOutput('vig');
return;
}
var out = vigenereProcess(text, key, mode === 'decrypt');
teShowOutput('vig', out, mode);
teStatus('te-vig-status', '&#10003; ' + (mode==='encrypt'?'Encrypted':'Decrypted') + ' with key "' + key.toUpperCase().replace(/[^A-Z]/g,'') + '"', 'ok');
};

/* ============================================================
XOR Cipher
============================================================ */
function xorEncrypt(text, key) {
if (!key) return text;
var bytes = new TextEncoder().encode(text);
var keyBytes = new TextEncoder().encode(key);
var out = new Uint8Array(bytes.length);
for (var i = 0; i < bytes.length; i++) {
out[i] = bytes[i] ^ keyBytes[i % keyBytes.length];
}
return btoa(String.fromCharCode.apply(null, out));
}

function xorDecrypt(b64, key) {
if (!key) return b64;
try {
var raw = atob(b64);
var bytes = new Uint8Array(raw.length);
for (var i = 0; i < raw.length; i++) bytes[i] = raw.charCodeAt(i);
var keyBytes = new TextEncoder().encode(key);
var out = new Uint8Array(bytes.length);
for (var j = 0; j < bytes.length; j++) {
out[j] = bytes[j] ^ keyBytes[j % keyBytes.length];
}
return new TextDecoder().decode(out);
} catch(e) {
throw new Error('Invalid Base64 ciphertext. Make sure you paste the XOR-encrypted output.');
}
}

window.teXorRun = function() {
var text = document.getElementById('te-xor-input').value;
var key  = document.getElementById('te-xor-key').value;
var mode = teMode.xor;
if (!text) { teHideOutput('xor'); teStatus('te-xor-status','','hidden'); return; }
if (!key) {
teStatus('te-xor-status','&#9888; Please enter a key.','err');
teHideOutput('xor');
return;
}
try {
var out = mode === 'encrypt' ? xorEncrypt(text, key) : xorDecrypt(text.trim(), key);
teShowOutput('xor', out, mode);
teStatus('te-xor-status', '&#10003; ' + (mode==='encrypt'?'Encrypted (Base64 output)':'Decrypted'), 'ok');
} catch(e) {
teStatus('te-xor-status', '&#10007; ' + e.message, 'err');
teHideOutput('xor');
}
};

/* ============================================================
AES-256-GCM via Web Crypto API
============================================================ */
function teAesShowProg(pct, msg) {
var el = document.getElementById('te-aes-prog');
el.classList.add('visible');
document.getElementById('te-aes-prog-fill').style.width = pct + '%';
document.getElementById('te-aes-prog-lbl').textContent  = msg;
}
function teAesHideProg() {
document.getElementById('te-aes-prog').classList.remove('visible');
}

async function aesKeyFromPassword(password, salt) {
var enc = new TextEncoder();
var keyMaterial = await crypto.subtle.importKey(
'raw', enc.encode(password), 'PBKDF2', false, ['deriveKey']
);
return crypto.subtle.deriveKey(
{ name: 'PBKDF2', salt: salt, iterations: 100000, hash: 'SHA-256' },
keyMaterial,
{ name: 'AES-GCM', length: 256 },
false,
['encrypt', 'decrypt']
);
}

function buf2b64(buf) {
return btoa(String.fromCharCode.apply(null, new Uint8Array(buf)));
}
function b64toBuf(b64) {
var raw = atob(b64);
var buf = new Uint8Array(raw.length);
for (var i = 0; i < raw.length; i++) buf[i] = raw.charCodeAt(i);
return buf;
}

async function aesEncrypt(plaintext, password) {
var enc = new TextEncoder();
var salt = crypto.getRandomValues(new Uint8Array(16));
var iv   = crypto.getRandomValues(new Uint8Array(12));
var key  = await aesKeyFromPassword(password, salt);
var cipherBuf = await crypto.subtle.encrypt(
{ name: 'AES-GCM', iv: iv },
key,
enc.encode(plaintext)
);
// Format: base64(salt):base64(iv):base64(ciphertext)
return buf2b64(salt) + ':' + buf2b64(iv) + ':' + buf2b64(cipherBuf);
}

async function aesDecrypt(encoded, password) {
var parts = encoded.trim().split(':');
if (parts.length !== 3) throw new Error('Invalid ciphertext format. Expected salt:iv:ciphertext in Base64.');
var salt      = b64toBuf(parts[0]);
var iv        = b64toBuf(parts[1]);
var cipherBuf = b64toBuf(parts[2]);
var key = await aesKeyFromPassword(password, salt);
var plainBuf = await crypto.subtle.decrypt(
{ name: 'AES-GCM', iv: iv },
key,
cipherBuf
);
return new TextDecoder().decode(plainBuf);
}

window.teAesRun = function() {
clearTimeout(teAesDebounce);
teAesDebounce = setTimeout(teAesRunNow, 300);
};

async function teAesRunNow() {
var text = document.getElementById('te-aes-input').value;
var pw   = document.getElementById('te-aes-pw').value;
var mode = teMode.aes;
if (!text) { teHideOutput('aes'); teStatus('te-aes-status','','hidden'); teAesHideProg(); return; }
if (!pw) {
teStatus('te-aes-status','&#9888; Please enter a password.','err');
teHideOutput('aes');
return;
}
try {
if (mode === 'encrypt') {
teAesShowProg(30, 'Deriving key (PBKDF2)…');
var cipher = await aesEncrypt(text, pw);
teAesShowProg(100, 'Done');
setTimeout(teAesHideProg, 400);
teShowOutput('aes', cipher, mode);
teStatus('te-aes-status', '&#10003; Encrypted with AES-256-GCM (PBKDF2 key derivation)', 'ok');
} else {
teAesShowProg(30, 'Deriving key (PBKDF2)…');
var plain = await aesDecrypt(text, pw);
teAesShowProg(100, 'Done');
setTimeout(teAesHideProg, 400);
teShowOutput('aes', plain, mode);
teStatus('te-aes-status', '&#10003; Decrypted successfully', 'ok');
}
} catch(e) {
teAesHideProg();
var msg = e.message || 'Unknown error';
if (msg.indexOf('operation-specific') !== -1 || msg.indexOf('OperationError') !== -1 || msg.toLowerCase().indexOf('decrypt') !== -1) {
msg = 'Decryption failed — wrong password or corrupted ciphertext.';
}
teStatus('te-aes-status', '&#10007; ' + msg, 'err');
teHideOutput('aes');
}
}

})();
</script>

</div><!-- /#te-app -->

---

## How Each Cipher Works

### Caesar Cipher

The Caesar cipher is one of the oldest encryption techniques. It shifts every letter in the plaintext forward (encrypt) or backward (decrypt) by a fixed number of positions in the 26-letter alphabet. A shift of 13 is the special case known as ROT13 — applying it twice returns the original text. Digits, spaces, and punctuation are left unchanged.

**Strength:** Very weak by modern standards — there are only 25 possible shifts and brute-forcing all of them takes seconds.

### Vigenere Cipher

The Vigenere cipher improves on Caesar by using a keyword instead of a single fixed shift. Each letter of the keyword specifies the shift for the corresponding input letter. When the key is shorter than the input, it wraps around. This makes simple frequency analysis harder — but repeated key patterns can still be exploited by the Kasiski examination.

**Strength:** Historically considered strong; now easily broken with key-length analysis. Good for learning and puzzles, not for securing sensitive data.

### XOR Cipher

XOR applies the bitwise exclusive-OR operation between each byte of the plaintext and the corresponding byte of a repeating key. Because XOR is its own inverse, the encrypt and decrypt operations are identical — just apply the key again. This tool outputs the result as Base64 for readability. A truly random key of the same length as the message (a one-time pad) is theoretically unbreakable, but a short repeating key is vulnerable to known-plaintext attacks.

**Strength:** Depends entirely on key length and randomness. Only use with long, random, non-repeating keys for serious security.

### AES-256-GCM

AES (Advanced Encryption Standard) with a 256-bit key in GCM (Galois/Counter Mode) is the current industry standard for symmetric encryption. This tool derives the encryption key from your password using PBKDF2 with SHA-256 and 100,000 iterations over a random 16-byte salt — making brute-force dictionary attacks significantly harder. A random 96-bit IV (nonce) is generated for every encryption operation, so encrypting the same plaintext twice produces different ciphertext. The output encodes salt, IV, and ciphertext as Base64 separated by colons.

**Strength:** Very strong when used with a long, random password. The Web Crypto API runs in the browser's native cryptographic layer — your password and plaintext never leave your device.

## Privacy Notice

All operations run entirely in your browser. No text, keys, or passwords are transmitted to any server. AES-256-GCM uses the browser's built-in **Web Crypto API** (`SubtleCrypto`). Caesar, Vigenere, and XOR are implemented in pure JavaScript.

---

> Generate secure random passwords → [Password Generator](/tools/password-generator/)

> Hash text with MD5, SHA-256, SHA-512 → [Hash Generator](/tools/hash-generator/)

> Encode and rotate text with ROT13 → [ROT13 Encoder](/tools/rot13-encoder/)
