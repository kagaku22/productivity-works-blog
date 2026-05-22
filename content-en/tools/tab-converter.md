---
title: "Tab ↔ Spaces Converter"
date: 2025-05-16
description: "Free online tool to convert tabs to spaces or spaces to tabs. Configurable indent size (2/4/8), real-time whitespace preview, line stats, clipboard copy, and file upload."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "tab-converter"
ShowToc: false
aliases: ["/tools/tab-converter/", "/tools/tab-converter/"]
cover:
  image: "/images/covers/tab-converter.png"
  alt: "Tab Spaces Converter"
---

Convert tabs to spaces (or spaces to tabs) instantly — choose your indent width, preview whitespace characters, and copy the result in one click.

> Related Tool: Format HTML → [HTML Beautifier](/tools/html-beautifier/)

<div id="tc-app">
<style>
#tc-app *,#tc-app *::before,#tc-app *::after{box-sizing:border-box;margin:0;padding:0}
#tc-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;font-size:14px;color:#1e293b !important;color-scheme:light;background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:20px;max-width:900px}
#tc-app h2{display:none}
#tc-app .tc-row{display:flex;gap:12px;flex-wrap:wrap;align-items:center;margin-bottom:14px}
#tc-app .tc-label{font-weight:600;font-size:13px;color:#475569;white-space:nowrap}
#tc-app .tc-btn-group{display:flex;gap:6px;flex-wrap:wrap}
#tc-app .tc-btn{padding:7px 14px;border-radius:7px;border:1.5px solid #cbd5e1;background:#fff;color:#334155;font-size:13px;font-weight:500;cursor:pointer;transition:all .15s}
#tc-app .tc-btn:hover{border-color:#6366f1;color:#6366f1}
#tc-app .tc-btn.active{background:#6366f1;border-color:#6366f1;color:#fff}
#tc-app .tc-btn.action{background:#6366f1;border-color:#6366f1;color:#fff;font-weight:600}
#tc-app .tc-btn.action:hover{background:#4f46e5;border-color:#4f46e5}
#tc-app .tc-btn.secondary{background:#f1f5f9;border-color:#cbd5e1;color:#475569}
#tc-app .tc-btn.secondary:hover{border-color:#6366f1;color:#6366f1;background:#f1f5f9}
#tc-app .tc-check-label{display:flex;align-items:center;gap:6px;font-size:13px;color:#475569;cursor:pointer;user-select:none}
#tc-app .tc-check-label input{accent-color:#6366f1;width:15px;height:15px;cursor:pointer}
#tc-app .tc-panels{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media(max-width:640px){#tc-app .tc-panels{grid-template-columns:1fr}}
#tc-app .tc-panel-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px}
#tc-app .tc-panel-title{font-weight:600;font-size:13px;color:#64748b}
#tc-app .tc-panel-actions{display:flex;gap:6px}
#tc-app textarea{width:100%;height:280px;padding:10px 12px;border:1.5px solid #e2e8f0;border-radius:8px;font-family:"SFMono-Regular",Consolas,"Liberation Mono",Menlo,monospace;font-size:13px;line-height:1.6;color:#1e293b !important;background:#fff !important;resize:vertical;outline:none;transition:border-color .15s}
#tc-app textarea:focus{border-color:#6366f1}
#tc-app .tc-preview{width:100%;height:280px;padding:10px 12px;border:1.5px solid #e2e8f0;border-radius:8px;font-family:"SFMono-Regular",Consolas,"Liberation Mono",Menlo,monospace;font-size:13px;line-height:1.6;background:#fff;overflow:auto;white-space:pre;word-break:normal}
#tc-app .tc-preview .ws-space{color:#94a3b8}
#tc-app .tc-preview .ws-tab{color:#a78bfa}
#tc-app .tc-stats{display:flex;gap:14px;flex-wrap:wrap;padding:10px 14px;background:#f1f5f9;border-radius:8px;margin-top:12px}
#tc-app .tc-stat{font-size:12px;color:#64748b}
#tc-app .tc-stat strong{color:#1e293b;font-weight:600}
#tc-app .tc-divider{border:none;border-top:1px solid #e2e8f0;margin:14px 0}
#tc-app .tc-copy-note{font-size:12px;color:#10b981;font-weight:600;display:none}
#tc-app .tc-upload-wrap{position:relative;display:inline-block}
#tc-app .tc-upload-wrap input[type=file]{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%}
#tc-app .tc-mode-desc{font-size:12px;color:#94a3b8;margin-left:4px}
</style>

<!-- Controls -->
<div class="tc-row">
<span class="tc-label">Mode:</span>
<div class="tc-btn-group">
<button class="tc-btn active" id="tc-mode-t2s" onclick="tcSetMode('t2s')">Tabs → Spaces</button>
<button class="tc-btn" id="tc-mode-s2t" onclick="tcSetMode('s2t')">Spaces → Tabs</button>
</div>
</div>

<div class="tc-row">
<span class="tc-label">Tab Width:</span>
<div class="tc-btn-group">
<button class="tc-btn active" id="tc-w-2" onclick="tcSetWidth(2)">2 spaces</button>
<button class="tc-btn" id="tc-w-4" onclick="tcSetWidth(4)">4 spaces</button>
<button class="tc-btn" id="tc-w-8" onclick="tcSetWidth(8)">8 spaces</button>
</div>
</div>

<div class="tc-row">
<label class="tc-check-label"><input type="checkbox" id="tc-trim" onchange="tcProcess()"> Trim trailing whitespace</label>
<label class="tc-check-label"><input type="checkbox" id="tc-normalize" onchange="tcProcess()"> Normalize line endings (CRLF → LF)</label>
<label class="tc-check-label"><input type="checkbox" id="tc-preview-ws" onchange="tcProcess()" checked> Show whitespace in preview</label>
</div>

<div class="tc-row">
<div class="tc-btn-group">
<button class="tc-btn action" onclick="tcProcess()">Convert</button>
<button class="tc-btn secondary" onclick="tcSwap()">Swap Input / Output</button>
<button class="tc-btn secondary" onclick="tcClear()">Clear</button>
<div class="tc-upload-wrap">
<button class="tc-btn secondary">Upload File</button>
<input type="file" accept="text/*" onchange="tcUpload(event)">
</div>
</div>
</div>

<hr class="tc-divider">

<!-- Editor panels -->
<div class="tc-panels">
<div>
<div class="tc-panel-head">
<span class="tc-panel-title">INPUT</span>
<div class="tc-panel-actions">
<button class="tc-btn secondary" style="padding:4px 10px;font-size:12px" onclick="tcPaste()">Paste</button>
</div>
</div>
<textarea id="tc-input" placeholder="Paste your code here, or upload a file above..." oninput="tcProcess()" spellcheck="false"></textarea>
</div>
<div>
<div class="tc-panel-head">
<span class="tc-panel-title">OUTPUT <span class="tc-mode-desc" id="tc-mode-label">(tabs → spaces)</span></span>
<div class="tc-panel-actions">
<button class="tc-btn secondary" style="padding:4px 10px;font-size:12px" onclick="tcCopy()">Copy</button>
<span class="tc-copy-note" id="tc-copy-note">Copied!</span>
</div>
</div>
<div class="tc-preview" id="tc-output-preview" aria-live="polite"></div>
<textarea id="tc-output-raw" style="display:none" readonly spellcheck="false"></textarea>
</div>
</div>

<!-- Stats -->
<div class="tc-stats" id="tc-stats">
<span class="tc-stat">Lines: <strong id="tc-stat-lines">0</strong></span>
<span class="tc-stat">Input chars: <strong id="tc-stat-in-chars">0</strong></span>
<span class="tc-stat">Output chars: <strong id="tc-stat-out-chars">0</strong></span>
<span class="tc-stat">Tab stops (input): <strong id="tc-stat-tabs">0</strong></span>
<span class="tc-stat">Space indents (input): <strong id="tc-stat-spaces">0</strong></span>
<span class="tc-stat">Trailing WS lines: <strong id="tc-stat-trailing">0</strong></span>
</div>

<script>
(function(){
var mode = 't2s';
var width = 2;

function setMode(m){
mode = m;
document.getElementById('tc-mode-t2s').classList.toggle('active', m==='t2s');
document.getElementById('tc-mode-s2t').classList.toggle('active', m==='s2t');
document.getElementById('tc-mode-label').textContent = m==='t2s' ? '(tabs → spaces)' : '(spaces → tabs)';
process();
}
function setWidth(w){
width = w;
[2,4,8].forEach(function(n){
document.getElementById('tc-w-'+n).classList.toggle('active', n===w);
});
process();
}

function process(){
var input = document.getElementById('tc-input').value;
var trim = document.getElementById('tc-trim').checked;
var norm = document.getElementById('tc-normalize').checked;
var showWs = document.getElementById('tc-preview-ws').checked;

// Normalize line endings first if requested
var text = norm ? input.replace(/\r\n/g,'\n').replace(/\r/g,'\n') : input;

// Convert
var lines = text.split('\n');
var outLines = lines.map(function(line){
var converted;
if(mode === 't2s'){
// Replace tabs with spaces — handle mid-line tabs too with tab-stop logic
var result = '';
var col = 0;
for(var i=0;i<line.length;i++){
var ch = line[i];
if(ch==='\t'){
var spaces = width - (col % width);
result += ' '.repeat(spaces);
col += spaces;
} else {
result += ch;
col++;
}
}
converted = result;
} else {
// Spaces → tabs: only convert leading whitespace
var leadMatch = line.match(/^( +)/);
if(leadMatch){
var spCount = leadMatch[1].length;
var tabs = Math.floor(spCount / width);
var rem = spCount % width;
converted = '\t'.repeat(tabs) + ' '.repeat(rem) + line.slice(spCount);
} else {
converted = line;
}
}
if(trim) converted = converted.replace(/[ \t]+$/, '');
return converted;
});

var output = outLines.join('\n');
document.getElementById('tc-output-raw').value = output;

// Stats
var tabCount = 0;
var spaceIndentCount = 0;
var trailingCount = 0;
lines.forEach(function(l){
if(/\t/.test(l)) tabCount++;
if(/^ +/.test(l)) spaceIndentCount++;
if(/[ \t]+$/.test(l)) trailingCount++;
});
document.getElementById('tc-stat-lines').textContent = lines.length;
document.getElementById('tc-stat-in-chars').textContent = input.length;
document.getElementById('tc-stat-out-chars').textContent = output.length;
document.getElementById('tc-stat-tabs').textContent = tabCount;
document.getElementById('tc-stat-spaces').textContent = spaceIndentCount;
document.getElementById('tc-stat-trailing').textContent = trailingCount;

// Render preview
renderPreview(output, showWs);
}

function renderPreview(text, showWs){
var el = document.getElementById('tc-output-preview');
if(!showWs){
el.textContent = text;
return;
}
// Escape HTML then replace whitespace markers
var escaped = text
.replace(/&/g,'&amp;')
.replace(/</g,'&lt;')
.replace(/>/g,'&gt;');
var marked = escaped
.replace(/ /g,'<span class="ws-space">\u00b7</span>')
.replace(/\t/g,'<span class="ws-tab">\u2192   </span>');
el.innerHTML = marked;
}

function swap(){
var raw = document.getElementById('tc-output-raw').value;
document.getElementById('tc-input').value = raw;
process();
}

function clear(){
document.getElementById('tc-input').value = '';
document.getElementById('tc-output-raw').value = '';
document.getElementById('tc-output-preview').textContent = '';
['tc-stat-lines','tc-stat-in-chars','tc-stat-out-chars','tc-stat-tabs','tc-stat-spaces','tc-stat-trailing'].forEach(function(id){
document.getElementById(id).textContent = '0';
});
}

function copy(){
var val = document.getElementById('tc-output-raw').value;
if(!val) return;
if(navigator.clipboard && navigator.clipboard.writeText){
navigator.clipboard.writeText(val).then(flashCopy);
} else {
var ta = document.createElement('textarea');
ta.value = val;
ta.style.position='fixed';ta.style.opacity='0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
flashCopy();
}
}

function flashCopy(){
var note = document.getElementById('tc-copy-note');
note.style.display='inline';
setTimeout(function(){ note.style.display='none'; }, 1800);
}

function paste(){
if(navigator.clipboard && navigator.clipboard.readText){
navigator.clipboard.readText().then(function(t){
document.getElementById('tc-input').value = t;
process();
});
}
}

function upload(e){
var file = e.target.files[0];
if(!file) return;
var reader = new FileReader();
reader.onload = function(ev){
document.getElementById('tc-input').value = ev.target.result;
process();
};
reader.readAsText(file);
e.target.value = '';
}

// Expose to inline handlers
window.tcSetMode = setMode;
window.tcSetWidth = setWidth;
window.tcProcess = process;
window.tcSwap = swap;
window.tcClear = clear;
window.tcCopy = copy;
window.tcPaste = paste;
window.tcUpload = upload;

// Init
process();
})();
</script>
</div>

---

**How it works:**
- **Tabs → Spaces**: Each tab is expanded to the next tab-stop boundary using the chosen width (2, 4, or 8 spaces).
- **Spaces → Tabs**: Only leading whitespace is converted — groups of N spaces become one tab. Remaining partial spaces are kept.
- **Whitespace preview**: Spaces show as `·`, tabs show as `→` so you can verify the conversion at a glance.
- **Trim trailing whitespace**: Strips any spaces or tabs at the end of each line.
- **Normalize line endings**: Converts Windows CRLF and old Mac CR to Unix LF.
