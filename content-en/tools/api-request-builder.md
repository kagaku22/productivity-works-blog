---
title: "API Request Builder - Generate cURL, Fetch & Axios Code"
date: 2025-05-16
description: "Build API requests visually and generate code for cURL, JavaScript Fetch, Axios, Python requests, and more. No actual requests sent."
categories: ["Free Tools"]
slug: "api-request-builder"
ShowToc: false
cover:
  image: "/images/covers/api-request-builder.png"
  alt: "API Request Builder"
---

<div id="arb-app">

<style>
#arb-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 960px;
margin: 0 auto;
color: #1a1a2e;
}
#arb-app * { box-sizing: border-box; }
#arb-app h2 {
font-size: 1.4rem;
margin: 0 0 1rem;
color: #0f3460;
border-bottom: 2px solid #e2e8f0;
padding-bottom: 0.5rem;
}
#arb-app .arb-notice {
background: #eff6ff;
border: 1px solid #bfdbfe;
border-radius: 8px;
padding: 0.75rem 1rem;
font-size: 0.85rem;
color: #1d4ed8;
margin-bottom: 1.5rem;
display: flex;
align-items: center;
gap: 0.5rem;
}
#arb-app .arb-notice::before { content: "ℹ"; font-weight: bold; font-size: 1rem; }
#arb-app .arb-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 1.25rem 1.5rem;
margin-bottom: 1.25rem;
box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#arb-app .arb-row {
display: flex;
gap: 0.75rem;
align-items: stretch;
margin-bottom: 0.75rem;
}
#arb-app .arb-method-select {
padding: 0.6rem 0.75rem;
border: 2px solid #e2e8f0;
border-radius: 7px;
font-size: 0.95rem;
font-weight: 700;
cursor: pointer;
background: #f8fafc;
color: #0f3460;
min-width: 110px;
appearance: none;
text-align: center;
}
#arb-app .arb-method-select:focus { outline: none; border-color: #3b82f6; }
#arb-app select[data-method="GET"] { color: #16a34a; border-color: #bbf7d0; background: #f0fdf4; }
#arb-app select[data-method="POST"] { color: #ca8a04; border-color: #fde68a; background: #fefce8; }
#arb-app select[data-method="PUT"] { color: #d97706; border-color: #fed7aa; background: #fff7ed; }
#arb-app select[data-method="PATCH"] { color: #7c3aed; border-color: #ddd6fe; background: #faf5ff; }
#arb-app select[data-method="DELETE"] { color: #dc2626; border-color: #fecaca; background: #fff5f5; }
#arb-app .arb-url-input {
flex: 1;
padding: 0.6rem 0.9rem;
border: 2px solid #e2e8f0;
border-radius: 7px;
font-size: 0.95rem;
font-family: 'Courier New', monospace;
transition: border-color 0.2s;
}
#arb-app .arb-url-input:focus { outline: none; border-color: #3b82f6; }
#arb-app .arb-btn {
padding: 0.6rem 1.1rem;
border: none;
border-radius: 7px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
white-space: nowrap;
}
#arb-app .arb-btn:active { transform: scale(0.97); }
#arb-app .arb-btn-primary { background: #3b82f6; color: #fff; }
#arb-app .arb-btn-primary:hover { background: #2563eb; }
#arb-app .arb-btn-secondary { background: #f1f5f9; color: #475569; border: 1px solid #e2e8f0; }
#arb-app .arb-btn-secondary:hover { background: #e2e8f0; }
#arb-app .arb-btn-danger { background: #fee2e2; color: #dc2626; font-size: 0.8rem; padding: 0.35rem 0.6rem; }
#arb-app .arb-btn-danger:hover { background: #fecaca; }
#arb-app .arb-btn-add { background: #f0fdf4; color: #16a34a; border: 1px dashed #86efac; font-size: 0.85rem; }
#arb-app .arb-btn-add:hover { background: #dcfce7; }
#arb-app .arb-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 1rem;
overflow-x: auto;
}
#arb-app .arb-tab {
padding: 0.5rem 1rem;
font-size: 0.88rem;
font-weight: 600;
cursor: pointer;
color: #64748b;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
white-space: nowrap;
transition: color 0.15s;
background: none;
border-top: none;
border-left: none;
border-right: none;
}
#arb-app .arb-tab:hover { color: #3b82f6; }
#arb-app .arb-tab.active { color: #3b82f6; border-bottom-color: #3b82f6; }
#arb-app .arb-tab-content { display: none; }
#arb-app .arb-tab-content.active { display: block; }
#arb-app .arb-kv-table { width: 100%; border-collapse: collapse; }
#arb-app .arb-kv-table th {
text-align: left;
font-size: 0.78rem;
font-weight: 700;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.05em;
padding: 0.3rem 0.5rem 0.6rem;
}
#arb-app .arb-kv-table td { padding: 0.3rem 0.4rem; vertical-align: middle; }
#arb-app .arb-kv-input {
width: 100%;
padding: 0.45rem 0.65rem;
border: 1px solid #e2e8f0;
border-radius: 6px;
font-size: 0.88rem;
font-family: 'Courier New', monospace;
background: #f8fafc;
transition: border-color 0.2s;
}
#arb-app .arb-kv-input:focus { outline: none; border-color: #93c5fd; background: #fff; }
#arb-app .arb-kv-enable {
width: 16px; height: 16px; cursor: pointer; accent-color: #3b82f6;
}
#arb-app .arb-kv-td-check { width: 28px; text-align: center; }
#arb-app .arb-kv-td-del { width: 36px; text-align: center; }
#arb-app .arb-kv-td-key { width: 38%; }
#arb-app .arb-kv-td-val { }
#arb-app .arb-body-select {
padding: 0.45rem 0.75rem;
border: 1px solid #e2e8f0;
border-radius: 6px;
font-size: 0.88rem;
background: #f8fafc;
margin-bottom: 0.75rem;
cursor: pointer;
}
#arb-app .arb-body-select:focus { outline: none; border-color: #93c5fd; }
#arb-app .arb-body-editor {
width: 100%;
min-height: 140px;
padding: 0.75rem;
border: 1px solid #e2e8f0;
border-radius: 7px;
font-family: 'Courier New', monospace;
font-size: 0.875rem;
line-height: 1.6;
resize: vertical;
background: #1e1e2e;
color: #cdd6f4;
}
#arb-app .arb-body-editor:focus { outline: none; border-color: #93c5fd; }
#arb-app .arb-auth-select {
padding: 0.45rem 0.75rem;
border: 1px solid #e2e8f0;
border-radius: 6px;
font-size: 0.88rem;
background: #f8fafc;
margin-bottom: 0.75rem;
cursor: pointer;
min-width: 200px;
}
#arb-app .arb-auth-select:focus { outline: none; border-color: #93c5fd; }
#arb-app .arb-auth-fields { display: flex; flex-direction: column; gap: 0.6rem; }
#arb-app .arb-auth-field-row { display: flex; align-items: center; gap: 0.75rem; }
#arb-app .arb-auth-label { font-size: 0.85rem; font-weight: 600; color: #475569; min-width: 110px; }
#arb-app .arb-auth-input {
flex: 1;
padding: 0.45rem 0.65rem;
border: 1px solid #e2e8f0;
border-radius: 6px;
font-size: 0.88rem;
font-family: 'Courier New', monospace;
background: #f8fafc;
}
#arb-app .arb-auth-input:focus { outline: none; border-color: #93c5fd; background: #fff; }
#arb-app .arb-generate-row {
display: flex;
flex-wrap: wrap;
gap: 0.75rem;
align-items: center;
margin-bottom: 1.25rem;
}
#arb-app .arb-lang-select {
padding: 0.6rem 0.9rem;
border: 2px solid #3b82f6;
border-radius: 7px;
font-size: 0.92rem;
font-weight: 600;
background: #eff6ff;
color: #1d4ed8;
cursor: pointer;
min-width: 200px;
}
#arb-app .arb-lang-select:focus { outline: none; }
#arb-app .arb-output-wrap {
position: relative;
background: #1e1e2e;
border-radius: 10px;
overflow: hidden;
border: 1px solid #313244;
}
#arb-app .arb-output-header {
display: flex;
justify-content: space-between;
align-items: center;
padding: 0.65rem 1rem;
background: #181825;
border-bottom: 1px solid #313244;
}
#arb-app .arb-output-lang-badge {
font-size: 0.78rem;
font-weight: 700;
color: #89b4fa;
text-transform: uppercase;
letter-spacing: 0.08em;
}
#arb-app .arb-copy-btn {
padding: 0.35rem 0.85rem;
background: #313244;
color: #cdd6f4;
border: none;
border-radius: 5px;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
}
#arb-app .arb-copy-btn:hover { background: #45475a; }
#arb-app .arb-copy-btn.copied { background: #1e3a2f; color: #a6e3a1; }
#arb-app .arb-code-block {
padding: 1.25rem 1.5rem;
overflow-x: auto;
margin: 0;
}
#arb-app .arb-code-block code {
font-family: 'Courier New', Consolas, monospace;
font-size: 0.875rem;
line-height: 1.7;
white-space: pre;
display: block;
color: #cdd6f4;
}
/* Syntax highlight tokens */
#arb-app .t-kw { color: #cba6f7; }
#arb-app .t-str { color: #a6e3a1; }
#arb-app .t-num { color: #fab387; }
#arb-app .t-fn { color: #89b4fa; }
#arb-app .t-cm { color: #6c7086; font-style: italic; }
#arb-app .t-op { color: #89dceb; }
#arb-app .t-flag { color: #f38ba8; }
#arb-app .t-url { color: #f9e2af; }
#arb-app .t-prop { color: #89dceb; }
#arb-app .arb-related {
margin-top: 2rem;
padding: 1.25rem 1.5rem;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
}
#arb-app .arb-related h3 { font-size: 1rem; color: #0f3460; margin: 0 0 0.75rem; }
#arb-app .arb-related ul { margin: 0; padding: 0 0 0 1.25rem; }
#arb-app .arb-related li { margin-bottom: 0.4rem; font-size: 0.9rem; }
#arb-app .arb-related a { color: #3b82f6; text-decoration: none; }
#arb-app .arb-related a:hover { text-decoration: underline; }
@media (max-width: 600px) {
#arb-app .arb-row { flex-direction: column; }
#arb-app .arb-generate-row { flex-direction: column; align-items: stretch; }
#arb-app .arb-lang-select { min-width: unset; }
}
</style>

<div class="arb-notice">This tool generates code only. No actual API requests are sent from your browser.</div>

<!-- Request Line -->
<div class="arb-card">
<h2>Request</h2>
<div class="arb-row">
<select class="arb-method-select" id="arb-method" onchange="arbMethodColor()">
<option value="GET">GET</option>
<option value="POST">POST</option>
<option value="PUT">PUT</option>
<option value="PATCH">PATCH</option>
<option value="DELETE">DELETE</option>
</select>
<input type="url" class="arb-url-input" id="arb-url" placeholder="https://api.example.com/endpoint" value="https://api.example.com/users" />
</div>
</div>

<!-- Tabs: Headers / Params / Body / Auth -->
<div class="arb-card">
<div class="arb-tabs">
<button class="arb-tab active" onclick="arbTab('headers',this)">Headers</button>
<button class="arb-tab" onclick="arbTab('params',this)">Query Params</button>
<button class="arb-tab" onclick="arbTab('body',this)">Body</button>
<button class="arb-tab" onclick="arbTab('auth',this)">Auth</button>
</div>

<!-- Headers -->
<div class="arb-tab-content active" id="arb-tab-headers">
<table class="arb-kv-table" id="arb-headers-table">
<thead><tr>
<th class="arb-kv-td-check"></th>
<th class="arb-kv-td-key">Header Name</th>
<th>Value</th>
<th class="arb-kv-td-del"></th>
</tr></thead>
<tbody id="arb-headers-body"></tbody>
</table>
<button class="arb-btn arb-btn-add" style="margin-top:0.6rem" onclick="arbAddRow('headers')">+ Add Header</button>
</div>

<!-- Query Params -->
<div class="arb-tab-content" id="arb-tab-params">
<table class="arb-kv-table" id="arb-params-table">
<thead><tr>
<th class="arb-kv-td-check"></th>
<th class="arb-kv-td-key">Parameter</th>
<th>Value</th>
<th class="arb-kv-td-del"></th>
</tr></thead>
<tbody id="arb-params-body"></tbody>
</table>
<button class="arb-btn arb-btn-add" style="margin-top:0.6rem" onclick="arbAddRow('params')">+ Add Parameter</button>
</div>

<!-- Body -->
<div class="arb-tab-content" id="arb-tab-body">
<select class="arb-body-select" id="arb-body-type" onchange="arbBodyTypeChange()">
<option value="none">None</option>
<option value="json" selected>JSON</option>
<option value="form">Form Data (URL-encoded)</option>
<option value="raw">Raw Text</option>
</select>
<div id="arb-body-editor-wrap">
<textarea class="arb-body-editor" id="arb-body-editor" placeholder='{\n  "key": "value"\n}'>{\n  "name": "John Doe",\n  "email": "john@example.com"\n}</textarea>
</div>
<div id="arb-body-form-wrap" style="display:none">
<table class="arb-kv-table">
<thead><tr>
<th class="arb-kv-td-check"></th>
<th class="arb-kv-td-key">Field</th>
<th>Value</th>
<th class="arb-kv-td-del"></th>
</tr></thead>
<tbody id="arb-formdata-body"></tbody>
</table>
<button class="arb-btn arb-btn-add" style="margin-top:0.6rem" onclick="arbAddRow('formdata')">+ Add Field</button>
</div>
</div>

<!-- Auth -->
<div class="arb-tab-content" id="arb-tab-auth">
<select class="arb-auth-select" id="arb-auth-type" onchange="arbAuthTypeChange()">
<option value="none">No Auth</option>
<option value="bearer">Bearer Token</option>
<option value="basic">Basic Auth</option>
<option value="apikey">API Key</option>
</select>
<div class="arb-auth-fields" id="arb-auth-fields"></div>
</div>
</div>

<!-- Generate -->
<div class="arb-generate-row">
<select class="arb-lang-select" id="arb-lang">
<option value="curl">cURL</option>
<option value="fetch">JavaScript - Fetch</option>
<option value="axios">JavaScript - Axios</option>
<option value="python">Python - requests</option>
<option value="php">PHP - cURL</option>
</select>
<button class="arb-btn arb-btn-primary" onclick="arbGenerate()" style="padding:0.6rem 1.8rem;font-size:1rem">Generate Code</button>
</div>

<!-- Output -->
<div class="arb-output-wrap" id="arb-output-wrap">
<div class="arb-output-header">
<span class="arb-output-lang-badge" id="arb-output-badge">cURL</span>
<button class="arb-copy-btn" id="arb-copy-btn" onclick="arbCopy()">Copy</button>
</div>
<pre class="arb-code-block"><code id="arb-output-code">Click "Generate Code" to see the output here.</code></pre>
</div>

<div class="arb-related">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/json-formatter/">JSON Formatter & Validator</a></li>
<li><a href="/tools/base64-encoder/">Base64 Encoder / Decoder</a></li>
<li><a href="/tools/url-encoder/">URL Encoder / Decoder</a></li>
<li><a href="/tools/jwt-decoder/">JWT Decoder</a></li>
<li><a href="/tools/regex-tester/">Regex Tester</a></li>
</ul>
</div>

<script>
(function() {
// ---- State ----
var arbRows = { headers: [], params: [], formdata: [] };
var arbIdCounter = 0;

function arbId() { return 'arbr' + (++arbIdCounter); }

// ---- Init ----
arbAddRow('headers', 'Content-Type', 'application/json');
arbAddRow('headers', 'Accept', 'application/json');
arbAddRow('params', 'limit', '20');
arbAddRow('formdata');
arbMethodColor();

// ---- Method color ----
window.arbMethodColor = function() {
var sel = document.getElementById('arb-method');
sel.setAttribute('data-method', sel.value);
};

// ---- Tab switching ----
window.arbTab = function(name, btn) {
document.querySelectorAll('#arb-app .arb-tab-content').forEach(function(el){ el.classList.remove('active'); });
document.querySelectorAll('#arb-app .arb-tab').forEach(function(el){ el.classList.remove('active'); });
document.getElementById('arb-tab-' + name).classList.add('active');
btn.classList.add('active');
};

// ---- KV rows ----
window.arbAddRow = function(section, key, val) {
var id = arbId();
arbRows[section].push(id);
var tbody = document.getElementById('arb-' + section + '-body');
var tr = document.createElement('tr');
tr.id = 'arbrow-' + id;
tr.innerHTML = '<td class="arb-kv-td-check"><input type="checkbox" class="arb-kv-enable" checked id="arbck-' + id + '"></td>' +
'<td class="arb-kv-td-key"><input type="text" class="arb-kv-input" id="arbk-' + id + '" placeholder="Key" value="' + esc(key||'') + '"></td>' +
'<td><input type="text" class="arb-kv-input" id="arbv-' + id + '" placeholder="Value" value="' + esc(val||'') + '"></td>' +
'<td class="arb-kv-td-del"><button class="arb-btn arb-btn-danger" onclick="arbDelRow(\'' + section + '\',\'' + id + '\')">✕</button></td>';
tbody.appendChild(tr);
};

window.arbDelRow = function(section, id) {
var row = document.getElementById('arbrow-' + id);
if (row) row.parentNode.removeChild(row);
arbRows[section] = arbRows[section].filter(function(x){ return x !== id; });
};

function getKVRows(section) {
var result = [];
arbRows[section].forEach(function(id) {
var ck = document.getElementById('arbck-' + id);
var k = document.getElementById('arbk-' + id);
var v = document.getElementById('arbv-' + id);
if (ck && ck.checked && k && k.value.trim()) {
result.push([k.value.trim(), v ? v.value : '']);
}
});
return result;
}

// ---- Body type ----
window.arbBodyTypeChange = function() {
var type = document.getElementById('arb-body-type').value;
document.getElementById('arb-body-editor-wrap').style.display = (type === 'json' || type === 'raw') ? '' : 'none';
document.getElementById('arb-body-form-wrap').style.display = (type === 'form') ? '' : 'none';
};

// ---- Auth ----
window.arbAuthTypeChange = function() {
var type = document.getElementById('arb-auth-type').value;
var fields = document.getElementById('arb-auth-fields');
fields.innerHTML = '';
if (type === 'bearer') {
fields.innerHTML = '<div class="arb-auth-field-row"><span class="arb-auth-label">Token</span><input type="text" class="arb-auth-input" id="arb-auth-token" placeholder="your-bearer-token-here"></div>';
} else if (type === 'basic') {
fields.innerHTML = '<div class="arb-auth-field-row"><span class="arb-auth-label">Username</span><input type="text" class="arb-auth-input" id="arb-auth-user" placeholder="username"></div>' +
'<div class="arb-auth-field-row"><span class="arb-auth-label">Password</span><input type="password" class="arb-auth-input" id="arb-auth-pass" placeholder="password"></div>';
} else if (type === 'apikey') {
fields.innerHTML = '<div class="arb-auth-field-row"><span class="arb-auth-label">Key Name</span><input type="text" class="arb-auth-input" id="arb-auth-key-name" placeholder="X-API-Key"></div>' +
'<div class="arb-auth-field-row"><span class="arb-auth-label">Value</span><input type="text" class="arb-auth-input" id="arb-auth-key-val" placeholder="your-api-key-here"></div>' +
'<div class="arb-auth-field-row"><span class="arb-auth-label">Add To</span><select class="arb-auth-input" id="arb-auth-key-loc" style="font-family:inherit"><option value="header">Header</option><option value="query">Query Param</option></select></div>';
}
};

// ---- Collect request state ----
function arbCollect() {
var method = document.getElementById('arb-method').value;
var url = document.getElementById('arb-url').value.trim() || 'https://api.example.com/endpoint';
var headers = getKVRows('headers');
var params = getKVRows('params');
var bodyType = document.getElementById('arb-body-type').value;
var bodyRaw = document.getElementById('arb-body-editor') ? document.getElementById('arb-body-editor').value : '';
var formData = getKVRows('formdata');
var authType = document.getElementById('arb-auth-type').value;

// Auth injection
var extraHeaders = [];
var extraParams = [];
if (authType === 'bearer') {
var tok = (document.getElementById('arb-auth-token') || {}).value || 'YOUR_TOKEN';
extraHeaders.push(['Authorization', 'Bearer ' + tok]);
} else if (authType === 'basic') {
var user = (document.getElementById('arb-auth-user') || {}).value || 'username';
var pass = (document.getElementById('arb-auth-pass') || {}).value || 'password';
extraHeaders.push(['Authorization', 'Basic ' + btoa(user + ':' + pass)]);
} else if (authType === 'apikey') {
var kn = (document.getElementById('arb-auth-key-name') || {}).value || 'X-API-Key';
var kv = (document.getElementById('arb-auth-key-val') || {}).value || 'YOUR_API_KEY';
var loc = (document.getElementById('arb-auth-key-loc') || {}).value || 'header';
if (loc === 'header') extraHeaders.push([kn, kv]);
else extraParams.push([kn, kv]);
}

var allHeaders = headers.concat(extraHeaders);
var allParams = params.concat(extraParams);

// Build full URL with query params
var fullUrl = url;
if (allParams.length > 0) {
var qs = allParams.map(function(p){ return encodeURIComponent(p[0]) + '=' + encodeURIComponent(p[1]); }).join('&');
fullUrl += (url.indexOf('?') >= 0 ? '&' : '?') + qs;
}

return { method: method, url: url, fullUrl: fullUrl, headers: allHeaders, params: allParams, bodyType: bodyType, bodyRaw: bodyRaw, formData: formData };
}

// ---- Generators ----
function genCurl(r) {
var parts = ['curl'];
if (r.method !== 'GET') parts.push('-X ' + r.method);
r.headers.forEach(function(h) { parts.push("-H '" + h[0] + ': ' + h[1] + "'"); });
if (r.bodyType === 'json' && r.bodyRaw.trim() && r.method !== 'GET') {
parts.push("--data '" + r.bodyRaw.replace(/'/g, "'\\''") + "'");
} else if (r.bodyType === 'form' && r.formData.length > 0 && r.method !== 'GET') {
r.formData.forEach(function(f){ parts.push("--data-urlencode '" + f[0] + '=' + f[1] + "'"); });
} else if (r.bodyType === 'raw' && r.bodyRaw.trim() && r.method !== 'GET') {
parts.push("--data '" + r.bodyRaw.replace(/'/g, "'\\''") + "'");
}
parts.push("'" + r.fullUrl + "'");
return parts.join(' \\\n  ');
}

function genFetch(r) {
var lines = [];
lines.push('const response = await fetch(');
lines.push("  '" + r.fullUrl + "',");
lines.push('  {');
lines.push("    method: '" + r.method + "',");
if (r.headers.length > 0) {
lines.push('    headers: {');
r.headers.forEach(function(h, i){
lines.push("      '" + h[0] + "': '" + h[1] + "'" + (i < r.headers.length - 1 ? ',' : ''));
});
lines.push('    },');
}
if (r.method !== 'GET' && r.bodyType === 'json' && r.bodyRaw.trim()) {
lines.push('    body: JSON.stringify(' + r.bodyRaw + '),');
} else if (r.method !== 'GET' && r.bodyType === 'form' && r.formData.length > 0) {
lines.push("    body: '" + r.formData.map(function(f){ return encodeURIComponent(f[0])+'='+encodeURIComponent(f[1]); }).join('&') + "',");
} else if (r.method !== 'GET' && r.bodyType === 'raw' && r.bodyRaw.trim()) {
lines.push('    body: `' + r.bodyRaw + '`,');
}
lines.push('  }');
lines.push(');');
lines.push('');
lines.push('const data = await response.json();');
lines.push('console.log(data);');
return lines.join('\n');
}

function genAxios(r) {
var lines = [];
lines.push("import axios from 'axios';");
lines.push('');
lines.push('const response = await axios({');
lines.push("  method: '" + r.method.toLowerCase() + "',");
lines.push("  url: '" + r.url + "',");
if (r.params.length > 0) {
lines.push('  params: {');
r.params.forEach(function(p, i){
lines.push("    " + p[0] + ": '" + p[1] + "'" + (i < r.params.length - 1 ? ',' : ''));
});
lines.push('  },');
}
if (r.headers.length > 0) {
lines.push('  headers: {');
r.headers.forEach(function(h, i){
lines.push("    '" + h[0] + "': '" + h[1] + "'" + (i < r.headers.length - 1 ? ',' : ''));
});
lines.push('  },');
}
if (r.method !== 'GET' && r.bodyType === 'json' && r.bodyRaw.trim()) {
lines.push('  data: ' + r.bodyRaw + ',');
} else if (r.method !== 'GET' && r.bodyType === 'form' && r.formData.length > 0) {
lines.push("  data: '" + r.formData.map(function(f){ return encodeURIComponent(f[0])+'='+encodeURIComponent(f[1]); }).join('&') + "',");
} else if (r.method !== 'GET' && r.bodyType === 'raw' && r.bodyRaw.trim()) {
lines.push("  data: `" + r.bodyRaw + "`,");
}
lines.push('});');
lines.push('');
lines.push('console.log(response.data);');
return lines.join('\n');
}

function genPython(r) {
var lines = [];
lines.push('import requests');
lines.push('');
if (r.headers.length > 0) {
lines.push('headers = {');
r.headers.forEach(function(h, i){
lines.push("    '" + h[0] + "': '" + h[1] + "'" + (i < r.headers.length - 1 ? ',' : ''));
});
lines.push('}');
lines.push('');
}
if (r.params.length > 0) {
lines.push('params = {');
r.params.forEach(function(p, i){
lines.push("    '" + p[0] + "': '" + p[1] + "'" + (i < r.params.length - 1 ? ',' : ''));
});
lines.push('}');
lines.push('');
}
var callArgs = ["'" + r.url + "'"];
if (r.headers.length > 0) callArgs.push('headers=headers');
if (r.params.length > 0) callArgs.push('params=params');
if (r.method !== 'GET' && r.bodyType === 'json' && r.bodyRaw.trim()) {
lines.push('payload = ' + r.bodyRaw);
lines.push('');
callArgs.push('json=payload');
} else if (r.method !== 'GET' && r.bodyType === 'form' && r.formData.length > 0) {
lines.push('data = {');
r.formData.forEach(function(f, i){
lines.push("    '" + f[0] + "': '" + f[1] + "'" + (i < r.formData.length - 1 ? ',' : ''));
});
lines.push('}');
lines.push('');
callArgs.push('data=data');
}
lines.push('response = requests.' + r.method.toLowerCase() + '(');
callArgs.forEach(function(a, i){ lines.push('    ' + a + (i < callArgs.length - 1 ? ',' : '')); });
lines.push(')');
lines.push('');
lines.push('print(response.status_code)');
lines.push('print(response.json())');
return lines.join('\n');
}

function genPhp(r) {
var lines = [];
lines.push('<?php');
lines.push('');
lines.push('$ch = curl_init();');
lines.push('');
lines.push("curl_setopt($ch, CURLOPT_URL, '" + r.fullUrl + "');");
lines.push('curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);');
if (r.method !== 'GET') {
lines.push("curl_setopt($ch, CURLOPT_CUSTOMREQUEST, '" + r.method + "');");
}
if (r.headers.length > 0) {
lines.push('curl_setopt($ch, CURLOPT_HTTPHEADER, [');
r.headers.forEach(function(h){ lines.push("    '" + h[0] + ': ' + h[1] + "',"); });
lines.push(']);');
}
if (r.method !== 'GET' && r.bodyType === 'json' && r.bodyRaw.trim()) {
lines.push("curl_setopt($ch, CURLOPT_POSTFIELDS, '" + r.bodyRaw.replace(/'/g, "\\'") + "');");
} else if (r.method !== 'GET' && r.bodyType === 'form' && r.formData.length > 0) {
lines.push("curl_setopt($ch, CURLOPT_POSTFIELDS, '" + r.formData.map(function(f){ return encodeURIComponent(f[0])+'='+encodeURIComponent(f[1]); }).join('&') + "');");
}
lines.push('');
lines.push('$response = curl_exec($ch);');
lines.push('$httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);');
lines.push('curl_close($ch);');
lines.push('');
lines.push('echo "Status: $httpCode\\n";');
lines.push('echo $response;');
return lines.join('\n');
}

// ---- Simple syntax highlight ----
function highlight(code, lang) {
// Escape HTML first
code = code.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');

if (lang === 'curl') {
code = code.replace(/(curl)/g, '<span class="t-kw">$1</span>');
code = code.replace(/(-X|-H|--data|--data-urlencode|-u|-G)/g, '<span class="t-flag">$1</span>');
code = code.replace(/'([^']*)'/g, function(m, inner){ return '<span class="t-str">\'' + inner + '\'</span>'; });
} else if (lang === 'python') {
code = code.replace(/\b(import|def|return|if|else|print|True|False|None)\b/g, '<span class="t-kw">$1</span>');
code = code.replace(/#[^\n]*/g, '<span class="t-cm">$&</span>');
code = code.replace(/'([^']*)'/g, '<span class="t-str">\'$1\'</span>');
code = code.replace(/\b(requests)\b/g, '<span class="t-fn">$1</span>');
} else if (lang === 'fetch' || lang === 'axios') {
code = code.replace(/\b(const|let|var|await|async|import|from|new|return|true|false|null|undefined)\b/g, '<span class="t-kw">$1</span>');
code = code.replace(/'([^']*)'/g, '<span class="t-str">\'$1\'</span>');
code = code.replace(/`([^`]*)`/g, '<span class="t-str">`$1`</span>');
code = code.replace(/\b(fetch|axios|console\.log|JSON\.stringify|JSON\.parse)\b/g, '<span class="t-fn">$1</span>');
code = code.replace(/\/\/[^\n]*/g, '<span class="t-cm">$&</span>');
} else if (lang === 'php') {
code = code.replace(/\b(echo|curl_init|curl_setopt|curl_exec|curl_close|curl_getinfo|true|false|null)\b/g, '<span class="t-fn">$1</span>');
code = code.replace(/(&lt;\?php|&lt;\?|\?&gt;)/g, '<span class="t-kw">$1</span>');
code = code.replace(/'([^']*)'/g, '<span class="t-str">\'$1\'</span>');
code = code.replace(/(CURLOPT_\w+|CURLINFO_\w+)/g, '<span class="t-prop">$1</span>');
code = code.replace(/\/\/[^\n]*/g, '<span class="t-cm">$&</span>');
}
return code;
}

var langLabels = { curl: 'cURL', fetch: 'JavaScript (Fetch)', axios: 'JavaScript (Axios)', python: 'Python', php: 'PHP' };

// ---- Generate ----
window.arbGenerate = function() {
var r = arbCollect();
var lang = document.getElementById('arb-lang').value;
var code = '';
if (lang === 'curl') code = genCurl(r);
else if (lang === 'fetch') code = genFetch(r);
else if (lang === 'axios') code = genAxios(r);
else if (lang === 'python') code = genPython(r);
else if (lang === 'php') code = genPhp(r);

document.getElementById('arb-output-code').innerHTML = highlight(code, lang);
document.getElementById('arb-output-badge').textContent = langLabels[lang] || lang;
// Store raw for copy
document.getElementById('arb-output-code').setAttribute('data-raw', code);
// Reset copy button
var cb = document.getElementById('arb-copy-btn');
cb.textContent = 'Copy';
cb.classList.remove('copied');
};

// ---- Copy ----
window.arbCopy = function() {
var code = document.getElementById('arb-output-code').getAttribute('data-raw') ||
document.getElementById('arb-output-code').textContent;
if (!code || code.indexOf('Generate Code') >= 0) return;
navigator.clipboard.writeText(code).then(function(){
var btn = document.getElementById('arb-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = 'Copy'; btn.classList.remove('copied'); }, 2000);
}).catch(function(){
var ta = document.createElement('textarea');
ta.value = code;
ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
var btn = document.getElementById('arb-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = 'Copy'; btn.classList.remove('copied'); }, 2000);
});
};

function esc(s) { return s.replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

// Auto-generate on load
arbGenerate();
})();
</script>

</div>

---

## Related Tools

> [Dns Record Guide](/tools/dns-record-guide/)
> [Http Status Codes](/tools/http-status-codes/)
> [Ip Address Calculator](/tools/ip-address-calculator/)

