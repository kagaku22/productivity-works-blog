---
title: "Chmod Calculator — Unix Permission Tool"
date: 2025-05-16
description: "Free chmod calculator. Visual permission editor with octal and symbolic notation. Set file permissions with presets for common configurations. Copy chmod commands instantly."
categories: ["Free Tools"]
tags: ["Developer Tools", "Programming", "Free Tools"]
slug: "chmod-calculator"
ShowToc: false
aliases:
  - "/tools/chmod-calculator/"
  - "/tools/chmod-calculator/"
cover:
  image: "/images/covers/chmod-calculator.png"
  alt: "Chmod Calculator"
---

<style>
#chmod-app *,
#chmod-app *::before,
#chmod-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#chmod-app {
font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, "Liberation Mono", monospace;
background: #0f172a;
color: #e2e8f0;
border-radius: 12px;
padding: 28px;
max-width: 860px;
margin: 0 auto;
}

#chmod-app h2 {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 1.4rem;
font-weight: 700;
color: #84cc16;
margin-bottom: 20px;
letter-spacing: -0.02em;
}

#chmod-app .ch-section-label {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.7rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.1em;
color: #64748b;
margin-bottom: 10px;
}

/* Presets */
#chmod-app .ch-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 24px;
}

#chmod-app .ch-preset-btn {
background: #1e293b;
border: 1px solid #334155;
color: #94a3b8;
border-radius: 6px;
padding: 6px 14px;
font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, monospace;
font-size: 0.85rem;
cursor: pointer;
transition: all 0.15s;
}

#chmod-app .ch-preset-btn:hover {
background: #334155;
color: #e2e8f0;
border-color: #84cc16;
}

#chmod-app .ch-preset-btn span {
font-weight: 700;
color: #84cc16;
}

/* Numeric input */
#chmod-app .ch-numeric-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 24px;
}

#chmod-app .ch-numeric-input {
background: #1e293b;
border: 1px solid #334155;
color: #84cc16;
border-radius: 8px;
padding: 10px 16px;
font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, monospace;
font-size: 1.8rem;
font-weight: 700;
width: 120px;
text-align: center;
outline: none;
transition: border-color 0.15s;
letter-spacing: 0.1em;
}

#chmod-app .ch-numeric-input:focus {
border-color: #84cc16;
}

#chmod-app .ch-numeric-hint {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.78rem;
color: #64748b;
}

/* Permission grid */
#chmod-app .ch-grid-wrapper {
overflow-x: auto;
margin-bottom: 24px;
}

#chmod-app .ch-grid {
width: 100%;
border-collapse: collapse;
min-width: 380px;
}

#chmod-app .ch-grid th {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.72rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #64748b;
padding: 8px 12px;
text-align: center;
border-bottom: 1px solid #1e293b;
}

#chmod-app .ch-grid th.ch-th-owner {
text-align: left;
color: #94a3b8;
}

#chmod-app .ch-grid td {
padding: 10px 12px;
text-align: center;
border-bottom: 1px solid #1e293b;
}

#chmod-app .ch-grid td.ch-td-label {
text-align: left;
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.88rem;
font-weight: 600;
color: #e2e8f0;
padding-left: 4px;
}

#chmod-app .ch-grid tr:last-child td {
border-bottom: none;
}

#chmod-app .ch-grid tr:hover td {
background: #1e293b22;
}

/* Checkbox custom */
#chmod-app .ch-cb-wrap {
display: inline-flex;
align-items: center;
justify-content: center;
cursor: pointer;
}

#chmod-app .ch-cb-wrap input[type="checkbox"] {
display: none;
}

#chmod-app .ch-cb-box {
width: 28px;
height: 28px;
border-radius: 6px;
border: 2px solid #334155;
background: #1e293b;
display: flex;
align-items: center;
justify-content: center;
transition: all 0.15s;
font-size: 0.9rem;
color: transparent;
user-select: none;
}

#chmod-app .ch-cb-wrap input:checked + .ch-cb-box {
background: #84cc16;
border-color: #84cc16;
color: #0f172a;
}

#chmod-app .ch-cb-wrap:hover .ch-cb-box {
border-color: #84cc16;
}

/* Row color accents */
#chmod-app .ch-row-owner td.ch-td-label { color: #38bdf8; }
#chmod-app .ch-row-group  td.ch-td-label { color: #a78bfa; }
#chmod-app .ch-row-others td.ch-td-label { color: #f97316; }

/* Special permissions */
#chmod-app .ch-special-row {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin-bottom: 24px;
}

#chmod-app .ch-special-item {
display: flex;
align-items: center;
gap: 8px;
cursor: pointer;
}

#chmod-app .ch-special-item input[type="checkbox"] {
display: none;
}

#chmod-app .ch-special-box {
width: 26px;
height: 26px;
border-radius: 5px;
border: 2px solid #334155;
background: #1e293b;
display: flex;
align-items: center;
justify-content: center;
transition: all 0.15s;
font-size: 0.8rem;
color: transparent;
}

#chmod-app .ch-special-item input:checked + .ch-special-box {
background: #f59e0b;
border-color: #f59e0b;
color: #0f172a;
}

#chmod-app .ch-special-item:hover .ch-special-box {
border-color: #f59e0b;
}

#chmod-app .ch-special-name {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.83rem;
color: #94a3b8;
}

/* Output cards */
#chmod-app .ch-outputs {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
gap: 12px;
margin-bottom: 24px;
}

#chmod-app .ch-output-card {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 14px 16px;
}

#chmod-app .ch-output-card .ch-output-label {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.68rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.1em;
color: #64748b;
margin-bottom: 6px;
}

#chmod-app .ch-output-card .ch-output-value {
font-size: 1.1rem;
font-weight: 700;
color: #84cc16;
word-break: break-all;
}

/* Copy button */
#chmod-app .ch-copy-row {
display: flex;
align-items: center;
gap: 12px;
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 12px 16px;
margin-bottom: 28px;
}

#chmod-app .ch-copy-cmd {
flex: 1;
font-size: 1rem;
color: #e2e8f0;
font-weight: 600;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
}

#chmod-app .ch-copy-btn {
background: #84cc16;
border: none;
border-radius: 6px;
color: #0f172a;
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.8rem;
font-weight: 700;
padding: 7px 16px;
cursor: pointer;
transition: background 0.15s;
white-space: nowrap;
flex-shrink: 0;
}

#chmod-app .ch-copy-btn:hover {
background: #a3e635;
}

#chmod-app .ch-copy-btn.copied {
background: #22c55e;
}

/* Explanation */
#chmod-app .ch-explain {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 20px;
margin-bottom: 20px;
}

#chmod-app .ch-explain h3 {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.95rem;
font-weight: 700;
color: #e2e8f0;
margin-bottom: 14px;
}

#chmod-app .ch-explain-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
gap: 10px;
}

#chmod-app .ch-explain-item {
display: flex;
flex-direction: column;
gap: 2px;
}

#chmod-app .ch-explain-item .ch-ei-title {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.78rem;
font-weight: 700;
color: #84cc16;
}

#chmod-app .ch-explain-item .ch-ei-desc {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.78rem;
color: #94a3b8;
line-height: 1.45;
}

/* Symbolic breakdown */
#chmod-app .ch-sym-breakdown {
display: flex;
gap: 0;
font-size: 1.3rem;
font-weight: 700;
letter-spacing: 0.05em;
margin-bottom: 6px;
flex-wrap: wrap;
}

#chmod-app .ch-sym-part {
padding: 4px 8px;
border-radius: 4px;
}

#chmod-app .ch-sym-owner { color: #38bdf8; background: #0c2340; }
#chmod-app .ch-sym-group { color: #a78bfa; background: #1a0c40; }
#chmod-app .ch-sym-others { color: #f97316; background: #3d1500; }

/* Responsive */
@media (max-width: 600px) {
#chmod-app {
padding: 18px 14px;
}
#chmod-app .ch-numeric-input {
font-size: 1.4rem;
width: 100px;
}
#chmod-app .ch-sym-breakdown {
font-size: 1rem;
}
}
</style>

<div id="chmod-app">

<h2>Chmod Permission Calculator</h2>

<div class="ch-section-label">Quick Presets</div>
<div class="ch-presets">
<button class="ch-preset-btn" onclick="chApplyPreset(644)"><span>644</span> — Files</button>
<button class="ch-preset-btn" onclick="chApplyPreset(755)"><span>755</span> — Directories</button>
<button class="ch-preset-btn" onclick="chApplyPreset(600)"><span>600</span> — Private</button>
<button class="ch-preset-btn" onclick="chApplyPreset(777)"><span>777</span> — All Access</button>
<button class="ch-preset-btn" onclick="chApplyPreset(444)"><span>444</span> — Read-Only</button>
<button class="ch-preset-btn" onclick="chApplyPreset(700)"><span>700</span> — Owner Only</button>
<button class="ch-preset-btn" onclick="chApplyPreset(664)"><span>664</span> — Group Write</button>
<button class="ch-preset-btn" onclick="chApplyPreset(640)"><span>640</span> — Group Read</button>
</div>

<div class="ch-section-label">Octal Value</div>
<div class="ch-numeric-row">
<input class="ch-numeric-input" id="ch-octal-input" type="text" maxlength="4" value="755"
oninput="chFromOctal(this.value)" placeholder="755" />
<span class="ch-numeric-hint">Type any octal value (000–777)<br>or use the grid below</span>
</div>

<div class="ch-section-label">Permission Grid</div>
<div class="ch-grid-wrapper">
<table class="ch-grid">
<thead>
<tr>
<th class="ch-th-owner">Entity</th>
<th>Read (r)</th>
<th>Write (w)</th>
<th>Execute (x)</th>
<th>Octal</th>
</tr>
</thead>
<tbody>
<tr class="ch-row-owner">
<td class="ch-td-label">Owner (u)</td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-ur" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-uw" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-ux" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td id="ch-uval" style="color:#38bdf8;font-weight:700;">7</td>
</tr>
<tr class="ch-row-group">
<td class="ch-td-label">Group (g)</td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-gr" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-gw" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-gx" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td id="ch-gval" style="color:#a78bfa;font-weight:700;">5</td>
</tr>
<tr class="ch-row-others">
<td class="ch-td-label">Others (o)</td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-or" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-ow" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td><label class="ch-cb-wrap"><input type="checkbox" id="ch-ox" onchange="chUpdate()"><span class="ch-cb-box">✓</span></label></td>
<td id="ch-oval" style="color:#f97316;font-weight:700;">5</td>
</tr>
</tbody>
</table>
</div>

<div class="ch-section-label">Special Permissions</div>
<div class="ch-special-row">
<label class="ch-special-item">
<input type="checkbox" id="ch-setuid" onchange="chUpdate()">
<span class="ch-special-box">✓</span>
<span class="ch-special-name">setuid — Run as file owner</span>
</label>
<label class="ch-special-item">
<input type="checkbox" id="ch-setgid" onchange="chUpdate()">
<span class="ch-special-box">✓</span>
<span class="ch-special-name">setgid — Run as group owner</span>
</label>
<label class="ch-special-item">
<input type="checkbox" id="ch-sticky" onchange="chUpdate()">
<span class="ch-special-box">✓</span>
<span class="ch-special-name">Sticky bit — Restrict deletion</span>
</label>
</div>

<div class="ch-section-label">Result</div>
<div class="ch-outputs">
<div class="ch-output-card">
<div class="ch-output-label">Octal (Numeric)</div>
<div class="ch-output-value" id="ch-out-octal">755</div>
</div>
<div class="ch-output-card">
<div class="ch-output-label">Symbolic Notation</div>
<div class="ch-sym-breakdown" id="ch-out-sym-parts">
<span class="ch-sym-part ch-sym-owner">rwx</span><span class="ch-sym-part ch-sym-group">r-x</span><span class="ch-sym-part ch-sym-others">r-x</span>
</div>
<div class="ch-output-value" style="font-size:0.85rem;color:#64748b;" id="ch-out-sym-full">rwxr-xr-x</div>
</div>
</div>

<div class="ch-copy-row">
<span class="ch-copy-cmd" id="ch-cmd-text">chmod 755 filename</span>
<button class="ch-copy-btn" id="ch-copy-btn" onclick="chCopyCmd()">Copy</button>
</div>

<div class="ch-explain">
<h3>What do permissions mean?</h3>
<div class="ch-explain-grid">
<div class="ch-explain-item">
<span class="ch-ei-title">Read (r) = 4</span>
<span class="ch-ei-desc">File: view contents.<br>Directory: list contents (ls).</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">Write (w) = 2</span>
<span class="ch-ei-desc">File: modify or delete.<br>Directory: create/delete files inside.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">Execute (x) = 1</span>
<span class="ch-ei-desc">File: run as a program.<br>Directory: enter (cd) the directory.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">Owner (u)</span>
<span class="ch-ei-desc">The user who owns the file. Usually the creator.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">Group (g)</span>
<span class="ch-ei-desc">Users in the file's associated group.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">Others (o)</span>
<span class="ch-ei-desc">Everyone else on the system.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">setuid (4000)</span>
<span class="ch-ei-desc">Executable runs with the owner's privileges. Appears as 's' in owner execute bit.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">setgid (2000)</span>
<span class="ch-ei-desc">Executable runs with group's privileges. New files in dir inherit group.</span>
</div>
<div class="ch-explain-item">
<span class="ch-ei-title">Sticky bit (1000)</span>
<span class="ch-ei-desc">Only the file owner can delete files in a directory. Used on /tmp.</span>
</div>
</div>
</div>

</div>

<script>
(function() {
// Initialize to 755
chApplyPreset(755);

function chGetBits() {
return {
ur: document.getElementById('ch-ur').checked,
uw: document.getElementById('ch-uw').checked,
ux: document.getElementById('ch-ux').checked,
gr: document.getElementById('ch-gr').checked,
gw: document.getElementById('ch-gw').checked,
gx: document.getElementById('ch-gx').checked,
or: document.getElementById('ch-or').checked,
ow: document.getElementById('ch-ow').checked,
ox: document.getElementById('ch-ox').checked,
setuid: document.getElementById('ch-setuid').checked,
setgid: document.getElementById('ch-setgid').checked,
sticky: document.getElementById('ch-sticky').checked
};
}

function chBitsToOctal(b) {
var u = (b.ur ? 4 : 0) + (b.uw ? 2 : 0) + (b.ux ? 1 : 0);
var g = (b.gr ? 4 : 0) + (b.gw ? 2 : 0) + (b.gx ? 1 : 0);
var o = (b.or ? 4 : 0) + (b.ow ? 2 : 0) + (b.ox ? 1 : 0);
var s = (b.setuid ? 4 : 0) + (b.setgid ? 2 : 0) + (b.sticky ? 1 : 0);
return { u: u, g: g, o: o, s: s };
}

function chBitsToSymbol(b) {
function bit(r, w, x, special, sChar) {
return (r ? 'r' : '-') + (w ? 'w' : '-') + (special ? (x ? sChar : sChar.toUpperCase()) : (x ? 'x' : '-'));
}
var uSym = bit(b.ur, b.uw, b.ux, b.setuid, 's');
var gSym = bit(b.gr, b.gw, b.gx, b.setgid, 's');
var oSym = bit(b.or, b.ow, b.ox, b.sticky, 't');
return { u: uSym, g: gSym, o: oSym };
}

window.chUpdate = function() {
var b = chGetBits();
var oct = chBitsToOctal(b);
var sym = chBitsToSymbol(b);

document.getElementById('ch-uval').textContent = oct.u;
document.getElementById('ch-gval').textContent = oct.g;
document.getElementById('ch-oval').textContent = oct.o;

var octalStr = (oct.s > 0 ? oct.s : '') + oct.u + '' + oct.g + '' + oct.o;
// Always show 3 or 4 digits
if (oct.s > 0) {
octalStr = oct.s + '' + oct.u + '' + oct.g + '' + oct.o;
} else {
octalStr = oct.u + '' + oct.g + '' + oct.o;
}

document.getElementById('ch-out-octal').textContent = octalStr;
document.getElementById('ch-out-sym-parts').innerHTML =
'<span class="ch-sym-part ch-sym-owner">' + sym.u + '</span>' +
'<span class="ch-sym-part ch-sym-group">' + sym.g + '</span>' +
'<span class="ch-sym-part ch-sym-others">' + sym.o + '</span>';
document.getElementById('ch-out-sym-full').textContent = sym.u + sym.g + sym.o;
document.getElementById('ch-cmd-text').textContent = 'chmod ' + octalStr + ' filename';
document.getElementById('ch-octal-input').value = octalStr;

// Reset copy button
var btn = document.getElementById('ch-copy-btn');
btn.textContent = 'Copy';
btn.classList.remove('copied');
};

window.chFromOctal = function(val) {
val = val.replace(/[^0-7]/g, '');
if (val.length < 3 || val.length > 4) return;

var digits;
var special = 0;
if (val.length === 4) {
special = parseInt(val[0], 8);
digits = [parseInt(val[1], 8), parseInt(val[2], 8), parseInt(val[3], 8)];
} else {
digits = [parseInt(val[0], 8), parseInt(val[1], 8), parseInt(val[2], 8)];
}

function setRow(r, w, x, prefix) {
document.getElementById('ch-' + prefix + 'r').checked = !!(r & 4);
document.getElementById('ch-' + prefix + 'w').checked = !!(r & 2);
document.getElementById('ch-' + prefix + 'x').checked = !!(r & 1);
}

setRow(digits[0], digits[0], digits[0], 'u');
setRow(digits[1], digits[1], digits[1], 'g');
setRow(digits[2], digits[2], digits[2], 'o');
document.getElementById('ch-setuid').checked = !!(special & 4);
document.getElementById('ch-setgid').checked = !!(special & 2);
document.getElementById('ch-sticky').checked = !!(special & 1);

chUpdate();
};

window.chApplyPreset = function(val) {
chFromOctal(String(val));
document.getElementById('ch-octal-input').value = String(val);
};

window.chCopyCmd = function() {
var cmd = document.getElementById('ch-cmd-text').textContent;
navigator.clipboard.writeText(cmd).then(function() {
var btn = document.getElementById('ch-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 2000);
}).catch(function() {
var ta = document.createElement('textarea');
ta.value = cmd;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
var btn = document.getElementById('ch-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 2000);
});
};

// Initialize
chApplyPreset(755);
})();
</script>

---

### Related Tools

> Build cron expressions → [Cron Expression Generator](/tools/cron-generator/)

> Generate .htaccess → [.htaccess Generator](/tools/htaccess-generator/)

> Format SQL → [SQL Formatter](/tools/sql-formatter/)
