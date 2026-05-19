---
title: "URL Encoder & Decoder - Free Online URL Encoding Tool"
date: 2025-05-16
description: "Encode and decode URLs instantly. Convert special characters to percent-encoding. Parse URL components. Free online URL tool for developers."
categories: ["Free Tools"]
tags: ["url encoder", "url decoder", "percent encoding", "developer tool", "web"]
slug: "url-encoder"
aliases: ["/tools/url-encoder-decoder/", "/tools/url-encoder-decoder/", "/tools/url-encoder-decoder/"]
cover:
  image: "/images/covers/url-encoder.png"
  alt: "URL Encoder Decoder"
ShowToc: false
---

<div id="url-app">
<style>
#url-app *,#url-app *::before,#url-app *::after{box-sizing:border-box;margin:0;padding:0}
#url-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;background:#f8fafc;border-radius:12px;padding:24px;max-width:900px;margin:0 auto}
#url-app h2{font-size:1.1rem;font-weight:700;color:#1e293b;margin-bottom:12px}
#url-app .tabs{display:flex;gap:4px;background:#e2e8f0;padding:4px;border-radius:8px;margin-bottom:20px;flex-wrap:wrap}
#url-app .tab-btn{flex:1;min-width:120px;padding:8px 12px;border:none;border-radius:6px;font-size:0.85rem;font-weight:600;cursor:pointer;background:transparent;color:#64748b;transition:all .2s}
#url-app .tab-btn.active{background:#fff;color:#2563eb;box-shadow:0 1px 3px rgba(0,0,0,.1)}
#url-app .tab-btn:hover:not(.active){color:#2563eb}
#url-app .panel{display:none}
#url-app .panel.active{display:block}

/* Encode/Decode Panel */
#url-app .mode-row{display:flex;align-items:center;gap:10px;margin-bottom:14px;flex-wrap:wrap}
#url-app .mode-label{font-size:0.82rem;font-weight:600;color:#64748b;white-space:nowrap}
#url-app .toggle-group{display:flex;border:1.5px solid #2563eb;border-radius:6px;overflow:hidden}
#url-app .toggle-btn{padding:6px 14px;border:none;font-size:0.82rem;font-weight:600;cursor:pointer;background:#fff;color:#2563eb;transition:all .15s}
#url-app .toggle-btn.active{background:#2563eb;color:#fff}
#url-app .rt-label{font-size:0.78rem;color:#94a3b8;margin-left:auto}

#url-app textarea{width:100%;border:1.5px solid #e2e8f0;border-radius:8px;padding:12px;font-size:0.88rem;font-family:monospace;resize:vertical;min-height:110px;outline:none;transition:border-color .2s;background:#fff;color:#1e293b}
#url-app textarea:focus{border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#url-app .textarea-label{font-size:0.8rem;font-weight:600;color:#64748b;margin-bottom:6px;display:block}

#url-app .btn-row{display:flex;gap:8px;margin:12px 0;flex-wrap:wrap}
#url-app .btn{padding:9px 18px;border:none;border-radius:7px;font-size:0.85rem;font-weight:700;cursor:pointer;transition:all .18s;display:flex;align-items:center;gap:6px}
#url-app .btn-primary{background:#2563eb;color:#fff}
#url-app .btn-primary:hover{background:#1d4ed8}
#url-app .btn-secondary{background:#f1f5f9;color:#475569;border:1.5px solid #e2e8f0}
#url-app .btn-secondary:hover{background:#e2e8f0}
#url-app .btn-danger{background:#fff;color:#ef4444;border:1.5px solid #fca5a5}
#url-app .btn-danger:hover{background:#fef2f2}
#url-app .btn-swap{background:#eff6ff;color:#2563eb;border:1.5px solid #bfdbfe}
#url-app .btn-swap:hover{background:#dbeafe}
#url-app .btn-copy{background:#f0fdf4;color:#16a34a;border:1.5px solid #bbf7d0}
#url-app .btn-copy:hover{background:#dcfce7}

#url-app .output-wrap{position:relative}
#url-app .copy-flash{position:absolute;top:10px;right:10px;background:#2563eb;color:#fff;font-size:0.75rem;font-weight:700;padding:3px 10px;border-radius:5px;opacity:0;transition:opacity .3s;pointer-events:none}

/* URL Parser */
#url-app .parse-input-row{display:flex;gap:8px;margin-bottom:16px;flex-wrap:wrap}
#url-app .parse-input{flex:1;min-width:0;border:1.5px solid #e2e8f0;border-radius:8px;padding:10px 14px;font-size:0.88rem;font-family:monospace;outline:none;background:#fff;color:#1e293b;transition:border-color .2s}
#url-app .parse-input:focus{border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#url-app .parse-table-wrap{overflow-x:auto;border-radius:8px;border:1.5px solid #e2e8f0;background:#fff}
#url-app table{width:100%;border-collapse:collapse;font-size:0.85rem}
#url-app th{background:#eff6ff;color:#2563eb;font-weight:700;padding:10px 14px;text-align:left;white-space:nowrap;border-bottom:1.5px solid #e2e8f0}
#url-app td{padding:9px 14px;border-bottom:1px solid #f1f5f9;vertical-align:top}
#url-app tr:last-child td{border-bottom:none}
#url-app td:first-child{font-weight:600;color:#64748b;white-space:nowrap;width:130px}
#url-app td:last-child{font-family:monospace;color:#1e293b;word-break:break-all}
#url-app .param-key{color:#2563eb;font-weight:700}
#url-app .param-val{color:#059669}
#url-app .empty-msg{color:#94a3b8;font-style:italic}
#url-app .parse-placeholder{text-align:center;padding:32px;color:#94a3b8;font-size:0.9rem}

/* Query Builder */
#url-app .qb-pairs{display:flex;flex-direction:column;gap:8px;margin-bottom:14px}
#url-app .qb-pair{display:flex;gap:8px;align-items:center}
#url-app .qb-pair input{flex:1;border:1.5px solid #e2e8f0;border-radius:7px;padding:8px 12px;font-size:0.85rem;outline:none;background:#fff;transition:border-color .2s;min-width:0}
#url-app .qb-pair input:focus{border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#url-app .qb-pair input::placeholder{color:#cbd5e1}
#url-app .qb-remove{background:none;border:none;cursor:pointer;color:#ef4444;font-size:1.1rem;padding:4px 6px;border-radius:5px;line-height:1;transition:background .15s}
#url-app .qb-remove:hover{background:#fef2f2}
#url-app .qb-result{background:#1e293b;color:#f8fafc;border-radius:8px;padding:14px;font-family:monospace;font-size:0.85rem;word-break:break-all;min-height:48px;margin-bottom:12px;position:relative}
#url-app .qb-result-label{font-size:0.75rem;color:#94a3b8;margin-bottom:4px}
#url-app .qb-result-text{word-break:break-all}
#url-app .qb-include-base{display:flex;align-items:center;gap:8px;margin-bottom:10px;flex-wrap:wrap}
#url-app .qb-include-base input[type=text]{flex:1;min-width:0;border:1.5px solid #e2e8f0;border-radius:7px;padding:8px 12px;font-size:0.85rem;outline:none;background:#fff;transition:border-color .2s}
#url-app .qb-include-base input[type=text]:focus{border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#url-app .qb-include-base label{font-size:0.82rem;font-weight:600;color:#64748b;white-space:nowrap}

/* Bulk Panel */
#url-app .bulk-mode-row{display:flex;gap:8px;align-items:center;margin-bottom:12px;flex-wrap:wrap}

/* Status bar */
#url-app .status{font-size:0.78rem;color:#64748b;margin-top:8px;min-height:18px}
#url-app .status.ok{color:#16a34a}
#url-app .status.err{color:#ef4444}

/* Char count */
#url-app .char-info{display:flex;justify-content:space-between;align-items:center;margin-top:4px}
#url-app .char-count{font-size:0.75rem;color:#94a3b8}

@media(max-width:600px){
#url-app{padding:14px}
#url-app .tabs{gap:2px}
#url-app .tab-btn{min-width:80px;font-size:0.78rem;padding:7px 8px}
#url-app .btn-row{gap:6px}
#url-app .btn{padding:8px 12px;font-size:0.8rem}
#url-app .parse-input-row{flex-direction:column}
#url-app td:first-child{width:90px}
}
</style>

<div class="tabs">
<button class="tab-btn active" onclick="urlApp.switchTab('encode')">Encode / Decode</button>
<button class="tab-btn" onclick="urlApp.switchTab('parser')">URL Parser</button>
<button class="tab-btn" onclick="urlApp.switchTab('builder')">Query Builder</button>
<button class="tab-btn" onclick="urlApp.switchTab('bulk')">Bulk Mode</button>
</div>

<!-- ENCODE / DECODE PANEL -->
<div id="panel-encode" class="panel active">
<div class="mode-row">
<span class="mode-label">Mode:</span>
<div class="toggle-group">
<button class="toggle-btn active" id="modeComp" onclick="urlApp.setMode('component')">encodeURIComponent</button>
<button class="toggle-btn" id="modeURI" onclick="urlApp.setMode('uri')">encodeURI</button>
</div>
<span class="rt-label">Real-time encoding</span>
</div>
<span class="textarea-label">Input</span>
<textarea id="encInput" placeholder="Type or paste text / URL here..." oninput="urlApp.onEncInput()"></textarea>
<div class="char-info">
<span class="char-count" id="encInputCount">0 chars</span>
</div>
<div class="btn-row">
<button class="btn btn-primary" onclick="urlApp.encode()">&#x1F512; Encode</button>
<button class="btn btn-primary" onclick="urlApp.decode()">&#x1F513; Decode</button>
<button class="btn btn-swap" onclick="urlApp.swap()">&#x21C5; Swap</button>
<button class="btn btn-danger" onclick="urlApp.clearEnc()">&#x2715; Clear</button>
</div>
<span class="textarea-label">Output</span>
<div class="output-wrap">
<textarea id="encOutput" placeholder="Result appears here..." readonly></textarea>
<span class="copy-flash" id="encCopyFlash">Copied!</span>
</div>
<div class="char-info">
<span class="char-count" id="encOutputCount">0 chars</span>
<button class="btn btn-copy" onclick="urlApp.copyEnc()" style="padding:4px 12px;font-size:0.78rem">Copy</button>
</div>
<div class="status" id="encStatus"></div>
<div style="margin-top:14px;background:#eff6ff;border-radius:8px;padding:12px;font-size:0.82rem;color:#1e40af">
<strong>encodeURIComponent</strong> encodes all special chars including <code style="background:#dbeafe;padding:1px 4px;border-radius:3px">:/?#[]@!$&amp;'()*+,;=</code> — use for encoding individual query parameter values.<br>
<strong>encodeURI</strong> preserves URL structure chars — use for encoding a full URL while keeping it valid.
</div>
</div>

<!-- URL PARSER PANEL -->
<div id="panel-parser" class="panel">
<h2>Parse a URL into its components</h2>
<div class="parse-input-row">
<input class="parse-input" id="parseInput" type="text" placeholder="https://example.com:8080/path?foo=bar&baz=qux#section" oninput="urlApp.parseURL()">
<button class="btn btn-danger" onclick="urlApp.clearParser()" style="padding:9px 14px">Clear</button>
</div>
<div id="parseResult">
<div class="parse-placeholder">Enter a URL above to see its components</div>
</div>
</div>

<!-- QUERY BUILDER PANEL -->
<div id="panel-builder" class="panel">
<h2>Query String Builder</h2>
<div class="qb-include-base">
<label>Base URL (optional):</label>
<input type="text" id="qbBase" placeholder="https://example.com/search" oninput="urlApp.buildQuery()">
</div>
<div class="qb-pairs" id="qbPairs">
<div class="qb-pair">
<input type="text" placeholder="Key" oninput="urlApp.buildQuery()" class="qb-key">
<input type="text" placeholder="Value" oninput="urlApp.buildQuery()" class="qb-val">
<button class="qb-remove" onclick="urlApp.removePair(this)" title="Remove">&#x2715;</button>
</div>
<div class="qb-pair">
<input type="text" placeholder="Key" oninput="urlApp.buildQuery()" class="qb-key">
<input type="text" placeholder="Value" oninput="urlApp.buildQuery()" class="qb-val">
<button class="qb-remove" onclick="urlApp.removePair(this)" title="Remove">&#x2715;</button>
</div>
</div>
<div class="btn-row" style="margin-bottom:14px">
<button class="btn btn-secondary" onclick="urlApp.addPair()">+ Add Parameter</button>
<button class="btn btn-danger" onclick="urlApp.clearBuilder()">Clear All</button>
</div>
<div class="qb-result-label" style="font-size:0.8rem;font-weight:600;color:#64748b;margin-bottom:6px">Generated URL / Query String</div>
<div class="qb-result">
<span class="qb-result-text" id="qbResult">—</span>
</div>
<div class="btn-row">
<button class="btn btn-copy" onclick="urlApp.copyBuilder()">Copy Result</button>
<span class="copy-flash" id="qbCopyFlash" style="position:static;opacity:0;transition:opacity .3s;font-size:0.78rem;background:#2563eb;color:#fff;padding:3px 10px;border-radius:5px">Copied!</span>
</div>
</div>

<!-- BULK MODE PANEL -->
<div id="panel-bulk" class="panel">
<h2>Bulk Encode / Decode</h2>
<p style="font-size:0.83rem;color:#64748b;margin-bottom:14px">Enter one URL or string per line. All lines will be processed together.</p>
<div class="bulk-mode-row">
<span class="mode-label">Mode:</span>
<div class="toggle-group">
<button class="toggle-btn active" id="bulkModeComp" onclick="urlApp.setBulkMode('component')">encodeURIComponent</button>
<button class="toggle-btn" id="bulkModeURI" onclick="urlApp.setBulkMode('uri')">encodeURI</button>
</div>
</div>
<span class="textarea-label">Input (one per line)</span>
<textarea id="bulkInput" placeholder="https://example.com/search?q=hello world&#10;hello world &amp; more&#10;another string..." style="min-height:140px"></textarea>
<div class="btn-row">
<button class="btn btn-primary" onclick="urlApp.bulkEncode()">Encode All</button>
<button class="btn btn-primary" onclick="urlApp.bulkDecode()">Decode All</button>
<button class="btn btn-swap" onclick="urlApp.bulkSwap()">&#x21C5; Swap</button>
<button class="btn btn-danger" onclick="urlApp.clearBulk()">Clear</button>
</div>
<span class="textarea-label">Output</span>
<div class="output-wrap">
<textarea id="bulkOutput" placeholder="Results appear here..." readonly style="min-height:140px"></textarea>
<span class="copy-flash" id="bulkCopyFlash">Copied!</span>
</div>
<div class="char-info">
<span class="char-count" id="bulkLineCount">0 lines</span>
<button class="btn btn-copy" onclick="urlApp.copyBulk()" style="padding:4px 12px;font-size:0.78rem">Copy</button>
</div>
<div class="status" id="bulkStatus"></div>
</div>

<script>
(function(){
const urlApp = window.urlApp = {};
let encMode = 'component';
let bulkMode = 'component';

// Tab switching
urlApp.switchTab = function(tab){
document.querySelectorAll('#url-app .tab-btn').forEach((b,i)=>{
b.classList.toggle('active', ['encode','parser','builder','bulk'][i]===tab);
});
['encode','parser','builder','bulk'].forEach(t=>{
const p = document.getElementById('panel-'+t);
if(p) p.classList.toggle('active', t===tab);
});
};

// Mode toggles
urlApp.setMode = function(mode){
encMode = mode;
document.getElementById('modeComp').classList.toggle('active', mode==='component');
document.getElementById('modeURI').classList.toggle('active', mode==='uri');
if(document.getElementById('encInput').value) urlApp.onEncInput();
};
urlApp.setBulkMode = function(mode){
bulkMode = mode;
document.getElementById('bulkModeComp').classList.toggle('active', mode==='component');
document.getElementById('bulkModeURI').classList.toggle('active', mode==='uri');
};

function doEncode(str, mode){
return mode==='uri' ? encodeURI(str) : encodeURIComponent(str);
}
function doDecode(str){
try { return decodeURIComponent(str.replace(/\+/g,' ')); }
catch(e){
// fallback: partial decode
try { return unescape(str); } catch(e2){ return str; }
}
}
function updateCount(inputId, countId){
const v = document.getElementById(inputId).value;
document.getElementById(countId).textContent = v.length + ' chars';
}

// Real-time encoding
urlApp.onEncInput = function(){
updateCount('encInput','encInputCount');
const v = document.getElementById('encInput').value;
if(!v){ setEncOutput(''); setStatus('encStatus','',''); return; }
try {
const encoded = doEncode(v, encMode);
setEncOutput(encoded);
setStatus('encStatus','Encoded in real-time','ok');
} catch(e){ setStatus('encStatus','Encoding error: '+e.message,'err'); }
};

function setEncOutput(val){
document.getElementById('encOutput').value = val;
document.getElementById('encOutputCount').textContent = val.length + ' chars';
}
function setStatus(id, msg, cls){
const el = document.getElementById(id);
el.textContent = msg;
el.className = 'status' + (cls?' '+cls:'');
}

urlApp.encode = function(){
const v = document.getElementById('encInput').value;
if(!v){ setStatus('encStatus','Please enter some text to encode','err'); return; }
try {
setEncOutput(doEncode(v, encMode));
setStatus('encStatus','Encoded successfully','ok');
} catch(e){ setStatus('encStatus','Error: '+e.message,'err'); }
};
urlApp.decode = function(){
const v = document.getElementById('encInput').value;
if(!v){ setStatus('encStatus','Please enter some text to decode','err'); return; }
try {
setEncOutput(doDecode(v));
setStatus('encStatus','Decoded successfully','ok');
} catch(e){ setStatus('encStatus','Error: '+e.message,'err'); }
};
urlApp.swap = function(){
const i = document.getElementById('encInput');
const o = document.getElementById('encOutput');
const tmp = i.value;
i.value = o.value;
setEncOutput(tmp);
updateCount('encInput','encInputCount');
setStatus('encStatus','Input and output swapped','ok');
};
urlApp.clearEnc = function(){
document.getElementById('encInput').value = '';
setEncOutput('');
setStatus('encStatus','','');
updateCount('encInput','encInputCount');
};
urlApp.copyEnc = function(){
const v = document.getElementById('encOutput').value;
if(!v) return;
copyText(v);
flashCopied('encCopyFlash');
};

// URL Parser
urlApp.parseURL = function(){
const raw = document.getElementById('parseInput').value.trim();
const out = document.getElementById('parseResult');
if(!raw){ out.innerHTML='<div class="parse-placeholder">Enter a URL above to see its components</div>'; return; }

let url;
try { url = new URL(raw); }
catch(e){
// try adding protocol
try { url = new URL('https://'+raw); }
catch(e2){
out.innerHTML='<div class="parse-placeholder" style="color:#ef4444">Invalid URL. Please include the protocol (e.g. https://)</div>';
return;
}
}

const params = [];
url.searchParams.forEach((val,key)=>params.push({key,val}));

let rows = [
{label:'Protocol', val: url.protocol},
{label:'Username', val: url.username || '<em style="color:#94a3b8">none</em>', raw:true},
{label:'Password', val: url.password ? '••••••' : '<em style="color:#94a3b8">none</em>', raw:true},
{label:'Host', val: url.hostname},
{label:'Port', val: url.port || '<em style="color:#94a3b8">default</em>', raw:!url.port},
{label:'Pathname', val: url.pathname},
{label:'Search', val: url.search || '<em style="color:#94a3b8">none</em>', raw:!url.search},
{label:'Fragment', val: url.hash || '<em style="color:#94a3b8">none</em>', raw:!url.hash},
{label:'Origin', val: url.origin},
];

let html = '<div class="parse-table-wrap"><table>';
html += '<tr><th>Component</th><th>Value</th></tr>';
rows.forEach(r=>{
html += `<tr><td>${r.label}</td><td>${r.raw ? r.val : escHTML(r.val)}</td></tr>`;
});

if(params.length){
html += `<tr><td colspan="2" style="background:#f8fafc;font-size:0.8rem;font-weight:700;color:#64748b;padding:8px 14px">Query Parameters (${params.length})</td></tr>`;
params.forEach(p=>{
html += `<tr><td><span class="param-key">${escHTML(p.key)}</span></td><td><span class="param-val">${escHTML(p.val)}</span></td></tr>`;
});
} else {
html += '<tr><td colspan="2" style="color:#94a3b8;font-style:italic;padding:10px 14px">No query parameters</td></tr>';
}
html += '</table></div>';
out.innerHTML = html;
};
urlApp.clearParser = function(){
document.getElementById('parseInput').value = '';
document.getElementById('parseResult').innerHTML = '<div class="parse-placeholder">Enter a URL above to see its components</div>';
};

// Query Builder
urlApp.addPair = function(){
const container = document.getElementById('qbPairs');
const div = document.createElement('div');
div.className = 'qb-pair';
div.innerHTML = '<input type="text" placeholder="Key" oninput="urlApp.buildQuery()" class="qb-key"><input type="text" placeholder="Value" oninput="urlApp.buildQuery()" class="qb-val"><button class="qb-remove" onclick="urlApp.removePair(this)" title="Remove">&#x2715;</button>';
container.appendChild(div);
};
urlApp.removePair = function(btn){
const pairs = document.querySelectorAll('#qbPairs .qb-pair');
if(pairs.length <= 1){ btn.closest('.qb-pair').querySelectorAll('input').forEach(i=>i.value=''); urlApp.buildQuery(); return; }
btn.closest('.qb-pair').remove();
urlApp.buildQuery();
};
urlApp.buildQuery = function(){
const base = document.getElementById('qbBase').value.trim();
const params = new URLSearchParams();
document.querySelectorAll('#qbPairs .qb-pair').forEach(pair=>{
const k = pair.querySelector('.qb-key').value.trim();
const v = pair.querySelector('.qb-val').value;
if(k) params.append(k, v);
});
const qs = params.toString();
let result = '';
if(base && qs) result = base + (base.includes('?') ? '&' : '?') + qs;
else if(base) result = base;
else if(qs) result = '?' + qs;
document.getElementById('qbResult').textContent = result || '—';
};
urlApp.clearBuilder = function(){
document.getElementById('qbBase').value = '';
document.getElementById('qbPairs').innerHTML = '<div class="qb-pair"><input type="text" placeholder="Key" oninput="urlApp.buildQuery()" class="qb-key"><input type="text" placeholder="Value" oninput="urlApp.buildQuery()" class="qb-val"><button class="qb-remove" onclick="urlApp.removePair(this)" title="Remove">&#x2715;</button></div>';
document.getElementById('qbResult').textContent = '—';
};
urlApp.copyBuilder = function(){
const v = document.getElementById('qbResult').textContent;
if(!v || v==='—') return;
copyText(v);
const fl = document.getElementById('qbCopyFlash');
fl.style.opacity='1'; setTimeout(()=>fl.style.opacity='0',1500);
};

// Bulk
urlApp.bulkEncode = function(){
const lines = document.getElementById('bulkInput').value.split('\n');
const results = lines.map(l=>{
if(!l.trim()) return '';
try { return doEncode(l, bulkMode); }
catch(e){ return '[ERROR: '+e.message+']'; }
});
document.getElementById('bulkOutput').value = results.join('\n');
const count = lines.filter(l=>l.trim()).length;
document.getElementById('bulkLineCount').textContent = count + ' lines';
setStatus('bulkStatus', count + ' lines encoded','ok');
};
urlApp.bulkDecode = function(){
const lines = document.getElementById('bulkInput').value.split('\n');
const results = lines.map(l=>{
if(!l.trim()) return '';
try { return doDecode(l); }
catch(e){ return '[ERROR: '+e.message+']'; }
});
document.getElementById('bulkOutput').value = results.join('\n');
const count = lines.filter(l=>l.trim()).length;
document.getElementById('bulkLineCount').textContent = count + ' lines';
setStatus('bulkStatus', count + ' lines decoded','ok');
};
urlApp.bulkSwap = function(){
const i = document.getElementById('bulkInput');
const o = document.getElementById('bulkOutput');
const tmp = i.value; i.value = o.value; o.value = tmp;
setStatus('bulkStatus','Input and output swapped','ok');
};
urlApp.clearBulk = function(){
document.getElementById('bulkInput').value = '';
document.getElementById('bulkOutput').value = '';
document.getElementById('bulkLineCount').textContent = '0 lines';
setStatus('bulkStatus','','');
};
urlApp.copyBulk = function(){
const v = document.getElementById('bulkOutput').value;
if(!v) return;
copyText(v);
flashCopied('bulkCopyFlash');
};

// Helpers
function escHTML(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;'); }
function copyText(t){
if(navigator.clipboard) navigator.clipboard.writeText(t).catch(()=>fallbackCopy(t));
else fallbackCopy(t);
}
function fallbackCopy(t){
const ta = document.createElement('textarea');
ta.value = t; ta.style.position='fixed'; ta.style.opacity='0';
document.body.appendChild(ta); ta.select();
try { document.execCommand('copy'); } catch(e){}
document.body.removeChild(ta);
}
function flashCopied(id){
const el = document.getElementById(id);
el.style.opacity='1'; setTimeout(()=>el.style.opacity='0',1500);
}
})();
</script>
</div>

---

## What Is URL Encoding?

URL encoding (also called **percent-encoding**) converts characters that are not allowed in URLs into a safe format. Each unsafe character is replaced with a `%` followed by two hexadecimal digits representing the character's UTF-8 byte value.

For example:
- Space becomes `%20`
- `&` becomes `%26`
- `=` becomes `%3D`

This is essential when passing data through query strings, form submissions, or API requests.

### encodeURIComponent vs encodeURI

| Function | Preserves | Best For |
|---|---|---|
| `encodeURIComponent` | Letters, digits, `-_.!~*'()` | Encoding individual query parameter values |
| `encodeURI` | URL structure chars (`:/?#[]@!$&'()*+,;=`) | Encoding a full URL while keeping it navigable |

### Common Use Cases

- **API requests** — Encode query parameter values before appending to a URL
- **Form data** — Encode user input before sending via GET requests
- **Sharing URLs** — Ensure URLs with special characters work across all systems
- **Debugging** — Decode percent-encoded URLs to make them human-readable

---

## Related Tools

- [Base64 Encoder & Decoder](/tools/base64-encoder/) — Encode and decode Base64 strings, useful for binary data in URLs and APIs
- [JSON Formatter & Validator](/tools/json-formatter/) — Prettify and validate JSON, commonly found in API query parameters
- [Regex Tester](/tools/regex-tester/) — Test regular expressions for parsing and validating URL patterns
