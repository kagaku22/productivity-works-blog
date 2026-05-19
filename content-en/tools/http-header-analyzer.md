---
title: "HTTP Header Analyzer"
date: 2025-05-16
description: "Free HTTP header reference and builder. Browse 50+ HTTP headers with explanations, build custom header sets, and generate configuration snippets for Apache and Nginx."
categories: ["Free Tools"]
slug: "http-header-analyzer"
ShowToc: false
cover:
  image: "/images/covers/http-header-analyzer.png"
  alt: "HTTP Header Analyzer"
---

Browse 50+ HTTP headers with descriptions and examples, build a security header set visually, parse raw HTTP headers instantly, and generate ready-to-use Apache `.htaccess` and Nginx config snippets.

<div id="hh-app">

<style>
#hh-app *, #hh-app *::before, #hh-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#hh-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
font-size: 15px;
color: #1a1a2e;
line-height: 1.6;
max-width: 960px;
margin: 0 auto;
}

/* ── Tabs ── */
#hh-app .hh-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 24px;
flex-wrap: wrap;
}
#hh-app .hh-tab {
padding: 10px 20px;
font-size: 14px;
font-weight: 600;
cursor: pointer;
border: none;
background: none;
color: #64748b;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
white-space: nowrap;
}
#hh-app .hh-tab:hover { color: #3a56d4; }
#hh-app .hh-tab.hh-active { color: #3a56d4; border-bottom-color: #3a56d4; }
#hh-app .hh-panel { display: none; }
#hh-app .hh-panel.hh-active { display: block; }

/* ── Search / filter bar ── */
#hh-app .hh-search-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 18px;
}
#hh-app .hh-search {
flex: 1 1 240px;
padding: 9px 14px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-size: 14px;
outline: none;
transition: border-color 0.2s;
color: #1a1a2e;
}
#hh-app .hh-search:focus { border-color: #3a56d4; }
#hh-app .hh-cat-btns {
display: flex;
flex-wrap: wrap;
gap: 6px;
}
#hh-app .hh-cat-btn {
padding: 6px 13px;
border-radius: 20px;
border: 1px solid #cbd5e1;
background: #f8fafc;
font-size: 12px;
font-weight: 600;
cursor: pointer;
color: #475569;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}
#hh-app .hh-cat-btn:hover { background: #e8f0fe; border-color: #3a56d4; color: #3a56d4; }
#hh-app .hh-cat-btn.hh-cat-active { background: #3a56d4; border-color: #3a56d4; color: #fff; }

/* ── Header cards ── */
#hh-app .hh-cards { display: flex; flex-direction: column; gap: 10px; }
#hh-app .hh-card {
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
}
#hh-app .hh-card-head {
display: flex;
align-items: center;
gap: 10px;
padding: 11px 16px;
background: #f8fafc;
cursor: pointer;
user-select: none;
}
#hh-app .hh-card-head:hover { background: #f0f4ff; }
#hh-app .hh-card-name {
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 13px;
font-weight: 700;
color: #1e3a8a;
flex: 1;
}
#hh-app .hh-badge {
font-size: 10px;
font-weight: 700;
padding: 2px 7px;
border-radius: 10px;
text-transform: uppercase;
letter-spacing: 0.04em;
white-space: nowrap;
flex-shrink: 0;
}
#hh-app .hh-badge-req  { background: #dbeafe; color: #1e40af; }
#hh-app .hh-badge-res  { background: #dcfce7; color: #166534; }
#hh-app .hh-badge-both { background: #fef3c7; color: #92400e; }
#hh-app .hh-badge-cat  { background: #f3e8ff; color: #6b21a8; }
#hh-app .hh-card-chevron { font-size: 10px; color: #94a3b8; flex-shrink: 0; }
#hh-app .hh-card-body {
padding: 14px 16px;
border-top: 1px solid #e2e8f0;
background: #fff;
display: none;
}
#hh-app .hh-card-body.hh-open { display: block; }
#hh-app .hh-card-desc { font-size: 13px; color: #334155; margin-bottom: 10px; }
#hh-app .hh-card-meta {
display: flex;
flex-wrap: wrap;
gap: 14px;
margin-bottom: 10px;
}
#hh-app .hh-meta-item { font-size: 12px; color: #64748b; }
#hh-app .hh-meta-item strong { color: #475569; }
#hh-app .hh-example-block {
background: #0f172a;
border-radius: 7px;
padding: 10px 14px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
}
#hh-app .hh-example-label {
font-size: 11px;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.06em;
margin-bottom: 5px;
font-weight: 600;
}
#hh-app .hh-no-results {
text-align: center;
padding: 40px 20px;
color: #94a3b8;
font-size: 14px;
}

/* ── Security Builder ── */
#hh-app .hh-builder-layout {
display: flex;
gap: 20px;
flex-wrap: wrap;
}
#hh-app .hh-builder-left { flex: 1 1 440px; min-width: 0; }
#hh-app .hh-builder-right { flex: 1 1 340px; min-width: 0; }
#hh-app .hh-builder-section {
border: 1px solid #e2e8f0;
border-radius: 10px;
margin-bottom: 14px;
overflow: hidden;
}
#hh-app .hh-builder-sec-head {
padding: 12px 16px;
background: #f8fafc;
font-weight: 700;
font-size: 13px;
color: #1e3a8a;
border-bottom: 1px solid #e2e8f0;
display: flex;
align-items: center;
gap: 8px;
}
#hh-app .hh-builder-sec-desc {
font-size: 11px;
color: #64748b;
font-weight: 400;
margin-left: 4px;
}
#hh-app .hh-field-group { padding: 14px 16px; display: flex; flex-direction: column; gap: 10px; }
#hh-app .hh-field-row { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; }
#hh-app .hh-field-label { font-size: 12px; color: #475569; min-width: 100px; flex-shrink: 0; }
#hh-app .hh-input, #hh-app .hh-select {
flex: 1;
min-width: 120px;
padding: 7px 10px;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
color: #1a1a2e;
background: #fff;
outline: none;
transition: border-color 0.15s;
}
#hh-app .hh-input:focus, #hh-app .hh-select:focus {
border-color: #3a56d4;
box-shadow: 0 0 0 3px rgba(58,86,212,0.1);
}
#hh-app .hh-enable-row {
display: flex; align-items: center; gap: 8px;
font-size: 13px; color: #334155;
padding: 8px 16px;
border-bottom: 1px solid #f1f5f9;
background: #fff;
}
#hh-app .hh-enable-row input[type="checkbox"] {
width: 15px; height: 15px;
accent-color: #3a56d4; cursor: pointer; flex-shrink: 0;
}
#hh-app .hh-enable-row label { cursor: pointer; }

/* ── Output box ── */
#hh-app .hh-out-box {
background: #0f172a;
border-radius: 10px;
overflow: hidden;
position: sticky;
top: 80px;
}
#hh-app .hh-out-topbar {
display: flex;
align-items: center;
justify-content: space-between;
padding: 10px 14px;
background: #1e293b;
flex-wrap: wrap;
gap: 6px;
}
#hh-app .hh-out-label {
font-size: 11px;
font-weight: 700;
color: #94a3b8;
letter-spacing: 0.06em;
text-transform: uppercase;
}
#hh-app .hh-out-actions { display: flex; gap: 6px; flex-wrap: wrap; }
#hh-app .hh-format-btns { display: flex; gap: 0; border-radius: 6px; overflow: hidden; border: 1px solid #334155; }
#hh-app .hh-format-btn {
padding: 4px 12px;
background: #1e293b;
color: #94a3b8;
border: none;
font-size: 11px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s, color 0.15s;
border-right: 1px solid #334155;
}
#hh-app .hh-format-btn:last-child { border-right: none; }
#hh-app .hh-format-btn:hover { background: #334155; color: #e2e8f0; }
#hh-app .hh-format-btn.hh-fmt-active { background: #3a56d4; color: #fff; }
#hh-app .hh-copy-btn {
padding: 5px 12px;
border-radius: 6px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
border: none;
background: #3a56d4;
color: #fff;
transition: background 0.15s;
}
#hh-app .hh-copy-btn:hover { background: #2d44b0; }
#hh-app .hh-copy-btn.hh-copied { background: #16a34a; }
#hh-app .hh-out-code {
padding: 16px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
line-height: 1.7;
color: #e2e8f0;
white-space: pre;
overflow-x: auto;
max-height: 540px;
overflow-y: auto;
min-height: 160px;
}
#hh-app .hh-out-code .hh-c-comment { color: #64748b; }
#hh-app .hh-out-code .hh-c-key     { color: #7dd3fc; }
#hh-app .hh-out-code .hh-c-val     { color: #86efac; }
#hh-app .hh-out-code .hh-c-tag     { color: #f9a8d4; }
#hh-app .hh-out-code .hh-c-dir     { color: #fde68a; }

/* ── Parser ── */
#hh-app .hh-parser-layout {
display: flex;
gap: 20px;
flex-wrap: wrap;
}
#hh-app .hh-parser-left { flex: 1 1 360px; min-width: 0; }
#hh-app .hh-parser-right { flex: 1 1 380px; min-width: 0; }
#hh-app .hh-textarea {
width: 100%;
padding: 12px 14px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
color: #1a1a2e;
resize: vertical;
outline: none;
transition: border-color 0.2s;
min-height: 240px;
line-height: 1.6;
}
#hh-app .hh-textarea:focus { border-color: #3a56d4; }
#hh-app .hh-parse-btn {
margin-top: 10px;
width: 100%;
padding: 11px;
background: linear-gradient(135deg, #3a56d4, #7c3aed);
color: #fff;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.2s;
}
#hh-app .hh-parse-btn:hover { opacity: 0.9; }
#hh-app .hh-parsed-list { display: flex; flex-direction: column; gap: 8px; }
#hh-app .hh-parsed-item {
border: 1px solid #e2e8f0;
border-radius: 8px;
overflow: hidden;
}
#hh-app .hh-parsed-head {
display: flex;
align-items: center;
gap: 8px;
padding: 9px 13px;
background: #f8fafc;
font-size: 12px;
}
#hh-app .hh-parsed-name {
font-family: "SFMono-Regular", Consolas, monospace;
font-weight: 700;
color: #1e3a8a;
flex: 1;
}
#hh-app .hh-parsed-val {
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 11px;
color: #334155;
background: #f1f5f9;
padding: 2px 7px;
border-radius: 4px;
max-width: 220px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}
#hh-app .hh-parsed-desc {
padding: 8px 13px;
font-size: 12px;
color: #475569;
border-top: 1px solid #f1f5f9;
background: #fff;
}
#hh-app .hh-parsed-unknown {
color: #94a3b8;
font-style: italic;
}
#hh-app .hh-parse-placeholder {
text-align: center;
padding: 40px 20px;
color: #94a3b8;
font-size: 13px;
border: 2px dashed #e2e8f0;
border-radius: 8px;
}

/* ── Misc ── */
#hh-app .hh-hint { font-size: 12px; color: #94a3b8; margin-top: 5px; }
#hh-app .hh-section-intro {
font-size: 13px;
color: #64748b;
margin-bottom: 18px;
padding: 12px 16px;
background: #f8fafc;
border-radius: 8px;
border-left: 3px solid #3a56d4;
}

@media (max-width: 680px) {
#hh-app .hh-builder-layout,
#hh-app .hh-parser-layout { flex-direction: column; }
#hh-app .hh-out-box { position: static; }
#hh-app .hh-tab { padding: 8px 13px; font-size: 13px; }
}
</style>

<!-- ═══════════════════════════════════════════════════════ TABS -->
<div class="hh-tabs">
<button class="hh-tab hh-active" onclick="hhShowTab('reference')">Reference</button>
<button class="hh-tab" onclick="hhShowTab('builder')">Security Builder</button>
<button class="hh-tab" onclick="hhShowTab('parser')">Header Parser</button>
</div>

<!-- ═══════════════════════════════════════════════════════ TAB 1: REFERENCE -->
<div class="hh-panel hh-active" id="hh-panel-reference">
<div class="hh-section-intro">Browse and search 50+ HTTP headers grouped by category. Click any header to see its description, common values, and an example.</div>
<div class="hh-search-row">
<input type="text" class="hh-search" id="hh-ref-search" placeholder="Search headers... (e.g. Content-Type, cache, CORS)" oninput="hhFilterRef()">
<div class="hh-cat-btns" id="hh-cat-btns"></div>
</div>
<div class="hh-cards" id="hh-cards"></div>
<div class="hh-no-results" id="hh-no-results" style="display:none;">No headers match your search.</div>
</div>

<!-- ═══════════════════════════════════════════════════════ TAB 2: BUILDER -->
<div class="hh-panel" id="hh-panel-builder">
<div class="hh-section-intro">Select and configure security headers below, then copy the generated snippet for Apache (.htaccess) or Nginx.</div>
<div class="hh-builder-layout">
<div class="hh-builder-left">

<!-- CSP -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">
Content-Security-Policy
<span class="hh-builder-sec-desc">— Controls allowed resource origins</span>
</div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-csp" onchange="hhBuild()">
<label for="hh-b-csp">Enable CSP header</label>
</div>
<div class="hh-field-group" id="hh-b-csp-fields" style="display:none;">
<div class="hh-field-row">
<span class="hh-field-label">default-src</span>
<select class="hh-select" id="hh-csp-default" onchange="hhBuild()">
<option value="'self'">'self'</option>
<option value="'self' 'unsafe-inline'">'self' 'unsafe-inline'</option>
<option value="'none'">'none'</option>
<option value="*">* (any)</option>
</select>
</div>
<div class="hh-field-row">
<span class="hh-field-label">script-src</span>
<input type="text" class="hh-input" id="hh-csp-script" placeholder="'self' (leave blank to inherit)" oninput="hhBuild()">
</div>
<div class="hh-field-row">
<span class="hh-field-label">style-src</span>
<input type="text" class="hh-input" id="hh-csp-style" placeholder="'self' (leave blank to inherit)" oninput="hhBuild()">
</div>
<div class="hh-field-row">
<span class="hh-field-label">img-src</span>
<input type="text" class="hh-input" id="hh-csp-img" placeholder="'self' data: (leave blank to inherit)" oninput="hhBuild()">
</div>
<div class="hh-field-row">
<span class="hh-field-label">frame-src</span>
<input type="text" class="hh-input" id="hh-csp-frame" placeholder="'none' (leave blank to inherit)" oninput="hhBuild()">
</div>
</div>
</div>

<!-- HSTS -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">Strict-Transport-Security <span class="hh-builder-sec-desc">— HTTPS enforcement</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-hsts" onchange="hhBuild()" checked>
<label for="hh-b-hsts">Enable HSTS</label>
</div>
<div class="hh-field-group">
<div class="hh-field-row">
<span class="hh-field-label">max-age</span>
<select class="hh-select" id="hh-hsts-age" onchange="hhBuild()" style="max-width:220px;">
<option value="2592000">30 days (2592000)</option>
<option value="15552000">6 months (15552000)</option>
<option value="31536000" selected>1 year (31536000)</option>
</select>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-hsts-sub" onchange="hhBuild()" checked>
<label for="hh-hsts-sub">includeSubDomains</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-hsts-pre" onchange="hhBuild()">
<label for="hh-hsts-pre">preload</label>
</div>
</div>
</div>

<!-- X-Frame-Options -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">X-Frame-Options <span class="hh-builder-sec-desc">— Clickjacking protection</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-xframe" onchange="hhBuild()" checked>
<label for="hh-b-xframe">Enable X-Frame-Options</label>
</div>
<div class="hh-field-group">
<div class="hh-field-row">
<span class="hh-field-label">Value</span>
<select class="hh-select" id="hh-xframe-val" onchange="hhBuild()" style="max-width:220px;">
<option value="SAMEORIGIN" selected>SAMEORIGIN</option>
<option value="DENY">DENY</option>
</select>
</div>
</div>
</div>

<!-- X-Content-Type-Options -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">X-Content-Type-Options <span class="hh-builder-sec-desc">— MIME sniffing prevention</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-xcto" onchange="hhBuild()" checked>
<label for="hh-b-xcto">Enable (always nosniff)</label>
</div>
</div>

<!-- Referrer-Policy -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">Referrer-Policy <span class="hh-builder-sec-desc">— Controls referrer info sent</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-rp" onchange="hhBuild()" checked>
<label for="hh-b-rp">Enable Referrer-Policy</label>
</div>
<div class="hh-field-group">
<div class="hh-field-row">
<span class="hh-field-label">Policy</span>
<select class="hh-select" id="hh-rp-val" onchange="hhBuild()">
<option value="no-referrer">no-referrer</option>
<option value="no-referrer-when-downgrade">no-referrer-when-downgrade</option>
<option value="strict-origin-when-cross-origin" selected>strict-origin-when-cross-origin</option>
<option value="same-origin">same-origin</option>
<option value="origin">origin</option>
</select>
</div>
</div>
</div>

<!-- Permissions-Policy -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">Permissions-Policy <span class="hh-builder-sec-desc">— Browser feature control</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-pp" onchange="hhBuild()">
<label for="hh-b-pp">Enable Permissions-Policy</label>
</div>
<div class="hh-field-group" id="hh-b-pp-fields" style="display:none;">
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-cam" onchange="hhBuild()" checked>
<label for="hh-pp-cam">camera=()</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-mic" onchange="hhBuild()" checked>
<label for="hh-pp-mic">microphone=()</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-geo" onchange="hhBuild()" checked>
<label for="hh-pp-geo">geolocation=()</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-pay" onchange="hhBuild()">
<label for="hh-pp-pay">payment=()</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-usb" onchange="hhBuild()">
<label for="hh-pp-usb">usb=()</label>
</div>
</div>
</div>

</div><!-- /.hh-builder-left -->

<div class="hh-builder-right">
<div class="hh-out-box">
<div class="hh-out-topbar">
<span class="hh-out-label">Generated Config</span>
<div class="hh-out-actions">
<div class="hh-format-btns">
<button class="hh-format-btn hh-fmt-active" id="hh-fmt-apache" onclick="hhSetFmt('apache')">Apache</button>
<button class="hh-format-btn" id="hh-fmt-nginx" onclick="hhSetFmt('nginx')">Nginx</button>
</div>
<button class="hh-copy-btn" id="hh-build-copy" onclick="hhCopyBuild()">Copy</button>
</div>
</div>
<pre class="hh-out-code" id="hh-build-out"></pre>
</div>
</div>

</div><!-- /.hh-builder-layout -->
</div>

<!-- ═══════════════════════════════════════════════════════ TAB 3: PARSER -->
<div class="hh-panel" id="hh-panel-parser">
<div class="hh-section-intro">Paste raw HTTP response headers below and click Parse to get a formatted, explained breakdown of each header.</div>
<div class="hh-parser-layout">
<div class="hh-parser-left">
<textarea class="hh-textarea" id="hh-parse-input" placeholder="Paste HTTP headers here, e.g.:

HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Cache-Control: max-age=3600, public
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Frame-Options: SAMEORIGIN
Content-Encoding: gzip
Vary: Accept-Encoding
Server: nginx/1.24.0"></textarea>
<button class="hh-parse-btn" onclick="hhParse()">Parse Headers</button>
<div class="hh-hint" style="margin-top:8px;">Supports HTTP/1.1 and HTTP/2 response header format.</div>
</div>
<div class="hh-parser-right">
<div id="hh-parsed-out">
<div class="hh-parse-placeholder">Paste headers above and click Parse to see the breakdown here.</div>
</div>
</div>
</div>
</div>

<script>
(function() {

/* ═══════════════════════════════════════════════════════ DATA */
var HH_HEADERS = [
// General
{ name: 'Date', cat: 'General', dir: 'both', desc: 'The date and time the message was originated, in HTTP-date format.', values: 'HTTP-date (RFC 7231)', example: 'Date: Tue, 15 Nov 1994 08:12:31 GMT' },
{ name: 'Connection', cat: 'General', dir: 'both', desc: 'Controls whether the network connection stays open after the current transaction finishes.', values: 'keep-alive, close', example: 'Connection: keep-alive' },
{ name: 'Transfer-Encoding', cat: 'General', dir: 'both', desc: 'Specifies the encoding applied to the message body for safe transfer between sender and recipient.', values: 'chunked, gzip, deflate, identity', example: 'Transfer-Encoding: chunked' },
{ name: 'Upgrade', cat: 'General', dir: 'both', desc: 'Allows the client to request the server to switch to a different protocol.', values: 'websocket, HTTP/2.0', example: 'Upgrade: websocket' },
// Request
{ name: 'Host', cat: 'Request', dir: 'req', desc: 'Specifies the host and port of the server to which the request is being sent. Required in HTTP/1.1.', values: 'hostname[:port]', example: 'Host: www.example.com' },
{ name: 'User-Agent', cat: 'Request', dir: 'req', desc: 'A string identifying the client software making the request (browser, bot, library).', values: 'product/version string', example: 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/124' },
{ name: 'Accept', cat: 'Request', dir: 'req', desc: 'Informs the server about the content types the client is able to understand.', values: 'MIME types, quality factors (q=)', example: 'Accept: text/html,application/xhtml+xml,application/json;q=0.9' },
{ name: 'Accept-Encoding', cat: 'Request', dir: 'req', desc: 'Tells the server which content encoding (compression) algorithms the client supports.', values: 'gzip, deflate, br, zstd, identity', example: 'Accept-Encoding: gzip, deflate, br' },
{ name: 'Accept-Language', cat: 'Request', dir: 'req', desc: 'Specifies which languages the client prefers for the response.', values: 'language tags (BCP 47)', example: 'Accept-Language: en-US,en;q=0.9,ja;q=0.8' },
{ name: 'Authorization', cat: 'Request', dir: 'req', desc: 'Contains credentials to authenticate the client with the server.', values: 'Basic, Bearer, Digest, OAuth', example: 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...' },
{ name: 'Cookie', cat: 'Request', dir: 'req', desc: 'Sends stored cookies from the client to the server.', values: 'name=value pairs', example: 'Cookie: session_id=abc123; user_pref=dark' },
{ name: 'Referer', cat: 'Request', dir: 'req', desc: 'The URL of the page from which the request was initiated. (Note: intentionally misspelled in the spec.)', values: 'URL', example: 'Referer: https://www.example.com/page' },
{ name: 'Origin', cat: 'Request', dir: 'req', desc: 'Indicates the origin (scheme, hostname, port) of the request. Used in CORS preflight checks.', values: 'scheme://host[:port]', example: 'Origin: https://app.example.com' },
{ name: 'If-Modified-Since', cat: 'Request', dir: 'req', desc: 'Makes the request conditional. The server sends the resource only if it was modified after the given date.', values: 'HTTP-date', example: 'If-Modified-Since: Sat, 29 Oct 2024 19:43:31 GMT' },
{ name: 'If-None-Match', cat: 'Request', dir: 'req', desc: 'Makes the request conditional using ETags. Returns 304 Not Modified if the ETag matches.', values: 'ETag value or *', example: 'If-None-Match: "33a64df551425fcc55e4d42a148795d9f25f89d4"' },
{ name: 'Range', cat: 'Request', dir: 'req', desc: 'Requests only part of a resource. Used for resumable downloads and streaming.', values: 'bytes=start-end', example: 'Range: bytes=200-1023' },
{ name: 'Expect', cat: 'Request', dir: 'req', desc: 'Indicates that a specific server behavior is required by the client. Most commonly used for 100-continue.', values: '100-continue', example: 'Expect: 100-continue' },
// Response
{ name: 'Content-Type', cat: 'Response', dir: 'res', desc: 'Indicates the media type of the response body, optionally including character set.', values: 'MIME type [; charset=...]', example: 'Content-Type: text/html; charset=utf-8' },
{ name: 'Content-Length', cat: 'Response', dir: 'res', desc: 'The size of the response body in bytes.', values: 'Integer (bytes)', example: 'Content-Length: 3495' },
{ name: 'Content-Encoding', cat: 'Response', dir: 'res', desc: 'Specifies the encoding applied to the response body. The client must decode it.', values: 'gzip, deflate, br, zstd', example: 'Content-Encoding: gzip' },
{ name: 'Content-Language', cat: 'Response', dir: 'res', desc: 'Describes the natural language(s) of the intended audience for the response.', values: 'language tags (BCP 47)', example: 'Content-Language: en-US' },
{ name: 'Content-Location', cat: 'Response', dir: 'res', desc: 'Provides an alternate URL for the returned resource.', values: 'URL', example: 'Content-Location: /documents/foo.json' },
{ name: 'Content-Range', cat: 'Response', dir: 'res', desc: 'Indicates where in a full resource a partial message belongs. Sent with 206 Partial Content.', values: 'bytes start-end/total', example: 'Content-Range: bytes 200-1023/146515' },
{ name: 'Location', cat: 'Response', dir: 'res', desc: 'Indicates the URL to redirect to for 3xx responses, or the URL of a newly created resource for 201.', values: 'URL', example: 'Location: https://www.example.com/new-page' },
{ name: 'Set-Cookie', cat: 'Response', dir: 'res', desc: 'Sends a cookie from the server to the user agent.', values: 'name=value [; attributes]', example: 'Set-Cookie: id=a3fWa; Expires=Thu, 21 Oct 2025 07:28:00 GMT; Secure; HttpOnly' },
{ name: 'Server', cat: 'Response', dir: 'res', desc: 'Describes the software used by the origin server. Revealing this can aid attackers; consider omitting.', values: 'product/version string', example: 'Server: nginx/1.24.0' },
{ name: 'WWW-Authenticate', cat: 'Response', dir: 'res', desc: 'Defines the authentication method that should be used to access the resource. Sent with 401.', values: 'auth-scheme [realm="..."]', example: 'WWW-Authenticate: Basic realm="Access to the staging site"' },
{ name: 'Retry-After', cat: 'Response', dir: 'res', desc: 'Indicates how long the user agent should wait before making a follow-up request. Used with 429 or 503.', values: 'HTTP-date or seconds', example: 'Retry-After: 120' },
{ name: 'Vary', cat: 'Response', dir: 'res', desc: 'Tells caches which request headers to consider when determining if a cached response can be used.', values: 'header names or *', example: 'Vary: Accept-Encoding, Accept-Language' },
{ name: 'ETag', cat: 'Response', dir: 'res', desc: 'A unique identifier for a specific version of a resource. Used for cache validation.', values: '"opaque-tag" or W/"weak-tag"', example: 'ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4"' },
{ name: 'Last-Modified', cat: 'Response', dir: 'res', desc: 'The date and time the resource was last modified. Used for conditional requests and caching.', values: 'HTTP-date', example: 'Last-Modified: Wed, 21 Oct 2024 07:28:00 GMT' },
{ name: 'Link', cat: 'Response', dir: 'res', desc: 'Defines relationships between the current document and other resources (e.g., preload, prefetch, canonical).', values: '<URL>; rel=type', example: 'Link: </styles.css>; rel=preload; as=style' },
{ name: 'Allow', cat: 'Response', dir: 'res', desc: 'Lists HTTP methods supported by the resource. Sent with 405 Method Not Allowed.', values: 'HTTP methods list', example: 'Allow: GET, POST, HEAD' },
// Security
{ name: 'Strict-Transport-Security', cat: 'Security', dir: 'res', desc: 'Forces browsers to access the site via HTTPS only for the specified duration. Helps prevent downgrade attacks.', values: 'max-age=N [; includeSubDomains] [; preload]', example: 'Strict-Transport-Security: max-age=31536000; includeSubDomains; preload' },
{ name: 'Content-Security-Policy', cat: 'Security', dir: 'res', desc: 'Restricts the sources from which the browser can load resources. Primary defense against XSS attacks.', values: 'directive source-list pairs', example: "Content-Security-Policy: default-src 'self'; script-src 'self' cdn.example.com" },
{ name: 'X-Frame-Options', cat: 'Security', dir: 'res', desc: 'Prevents the page from being embedded in iframes on other origins, mitigating clickjacking attacks.', values: 'DENY, SAMEORIGIN', example: 'X-Frame-Options: SAMEORIGIN' },
{ name: 'X-Content-Type-Options', cat: 'Security', dir: 'res', desc: 'Prevents the browser from MIME-sniffing the content type, forcing the declared Content-Type to be respected.', values: 'nosniff', example: 'X-Content-Type-Options: nosniff' },
{ name: 'Referrer-Policy', cat: 'Security', dir: 'res', desc: 'Controls how much referrer information is included with requests. Balances privacy and analytics needs.', values: 'no-referrer, strict-origin-when-cross-origin, same-origin, etc.', example: 'Referrer-Policy: strict-origin-when-cross-origin' },
{ name: 'Permissions-Policy', cat: 'Security', dir: 'res', desc: 'Allows or blocks access to browser features (camera, microphone, geolocation) in the page and iframes.', values: 'feature=(allowlist) pairs', example: 'Permissions-Policy: camera=(), microphone=(), geolocation=()' },
{ name: 'X-XSS-Protection', cat: 'Security', dir: 'res', desc: 'Enables the cross-site scripting (XSS) filter in older browsers. Mostly superseded by CSP, but still useful for legacy browser support.', values: '0, 1, 1; mode=block', example: 'X-XSS-Protection: 1; mode=block' },
{ name: 'Cross-Origin-Opener-Policy', cat: 'Security', dir: 'res', desc: 'Isolates the browsing context from cross-origin documents to prevent cross-origin attacks.', values: 'unsafe-none, same-origin-allow-popups, same-origin', example: 'Cross-Origin-Opener-Policy: same-origin' },
{ name: 'Cross-Origin-Embedder-Policy', cat: 'Security', dir: 'res', desc: 'Prevents the document from loading cross-origin resources that do not grant permission explicitly.', values: 'unsafe-none, require-corp', example: 'Cross-Origin-Embedder-Policy: require-corp' },
{ name: 'Cross-Origin-Resource-Policy', cat: 'Security', dir: 'res', desc: 'Prevents other origins from reading the response. A defense against Spectre-class side-channel attacks.', values: 'same-origin, same-site, cross-origin', example: 'Cross-Origin-Resource-Policy: same-origin' },
// Caching
{ name: 'Cache-Control', cat: 'Caching', dir: 'both', desc: 'Directives for caching mechanisms in requests and responses. The primary caching control header.', values: 'no-cache, no-store, max-age=N, public, private, must-revalidate, etc.', example: 'Cache-Control: public, max-age=86400, must-revalidate' },
{ name: 'Expires', cat: 'Caching', dir: 'res', desc: 'The date/time after which the response is considered stale. Superseded by Cache-Control max-age when both are present.', values: 'HTTP-date or 0 (expired immediately)', example: 'Expires: Thu, 01 Jan 2026 00:00:00 GMT' },
{ name: 'Pragma', cat: 'Caching', dir: 'req', desc: 'Legacy header for backwards-compatible caching control. Use Cache-Control instead in modern implementations.', values: 'no-cache', example: 'Pragma: no-cache' },
{ name: 'Age', cat: 'Caching', dir: 'res', desc: 'The time in seconds since the object was stored in a proxy cache.', values: 'Integer (seconds)', example: 'Age: 24' },
{ name: 'Clear-Site-Data', cat: 'Caching', dir: 'res', desc: 'Clears browsing data (cookies, storage, cache) associated with the requesting site. Useful on logout.', values: '"cache", "cookies", "storage", "*"', example: 'Clear-Site-Data: "cache", "cookies", "storage"' },
// CORS
{ name: 'Access-Control-Allow-Origin', cat: 'CORS', dir: 'res', desc: 'Specifies which origins are allowed to access the resource. Set by the server in response to a CORS request.', values: '* or specific origin', example: 'Access-Control-Allow-Origin: https://app.example.com' },
{ name: 'Access-Control-Allow-Methods', cat: 'CORS', dir: 'res', desc: 'Specifies which HTTP methods are allowed when accessing the resource in a CORS context.', values: 'HTTP methods list', example: 'Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS' },
{ name: 'Access-Control-Allow-Headers', cat: 'CORS', dir: 'res', desc: 'Indicates which HTTP headers can be used when making a CORS request.', values: 'header names or *', example: 'Access-Control-Allow-Headers: Content-Type, Authorization, X-Requested-With' },
{ name: 'Access-Control-Allow-Credentials', cat: 'CORS', dir: 'res', desc: 'Indicates whether the response can be exposed when the credentials flag is true.', values: 'true', example: 'Access-Control-Allow-Credentials: true' },
{ name: 'Access-Control-Max-Age', cat: 'CORS', dir: 'res', desc: 'Indicates how long (seconds) the results of a preflight request can be cached.', values: 'Integer (seconds)', example: 'Access-Control-Max-Age: 86400' },
{ name: 'Access-Control-Expose-Headers', cat: 'CORS', dir: 'res', desc: 'Lists response headers that should be made available to the browser in a CORS context.', values: 'header names', example: 'Access-Control-Expose-Headers: X-Custom-Header, Content-Length' },
{ name: 'Access-Control-Request-Headers', cat: 'CORS', dir: 'req', desc: 'Used in a preflight request to indicate which headers will be sent in the actual request.', values: 'header names', example: 'Access-Control-Request-Headers: Content-Type, Authorization' },
{ name: 'Access-Control-Request-Method', cat: 'CORS', dir: 'req', desc: 'Used in a preflight request to indicate which HTTP method will be used in the actual request.', values: 'HTTP method', example: 'Access-Control-Request-Method: POST' },
// Content
{ name: 'Accept-Ranges', cat: 'Content', dir: 'res', desc: 'Indicates whether the server supports range requests for the resource.', values: 'bytes, none', example: 'Accept-Ranges: bytes' },
{ name: 'Content-Disposition', cat: 'Content', dir: 'res', desc: 'Indicates if the content should be displayed inline or as an attachment (download prompt).', values: 'inline, attachment [; filename="..."]', example: 'Content-Disposition: attachment; filename="report.pdf"' },
{ name: 'TE', cat: 'Content', dir: 'req', desc: 'Specifies the transfer encodings the client is willing to accept.', values: 'trailers, deflate, gzip', example: 'TE: trailers, deflate;q=0.5' },
{ name: 'Trailer', cat: 'Content', dir: 'both', desc: 'Allows the sender to include additional header fields at the end of chunked messages.', values: 'header name', example: 'Trailer: Expires' },
{ name: 'X-Powered-By', cat: 'Content', dir: 'res', desc: 'Identifies the technology used on the server. Often suppressed for security to reduce information leakage.', values: 'technology/version', example: 'X-Powered-By: PHP/8.2.0' },
{ name: 'Alt-Svc', cat: 'Content', dir: 'res', desc: 'Allows the server to advertise alternative services (e.g., HTTP/3 via QUIC).', values: 'protocol="host:port" [; ma=N]', example: 'Alt-Svc: h3=":443"; ma=86400' },
{ name: 'Forwarded', cat: 'Content', dir: 'req', desc: 'Contains information from the client-facing side of proxy servers, standardized replacement for X-Forwarded-For.', values: 'for=ip, host=host, proto=https', example: 'Forwarded: for=192.0.2.60; proto=http; by=203.0.113.43; host=example.com' },
{ name: 'X-Forwarded-For', cat: 'Content', dir: 'req', desc: 'De-facto standard header for identifying the originating IP of a client connecting through a proxy.', values: 'IP addresses list', example: 'X-Forwarded-For: 203.0.113.195, 70.41.3.18' },
];

var HH_CATS = ['All','General','Request','Response','Security','Caching','CORS','Content'];
var hhCurrentCat = 'All';
var hhOpenCards = {};
var hhCurrentFmt = 'apache';

/* ═══════════════════════════════════════════════════════ TABS */
function hhShowTab(id) {
document.querySelectorAll('#hh-app .hh-tab').forEach(function(t, i) {
var tabs = ['reference','builder','parser'];
t.classList.toggle('hh-active', tabs[i] === id);
});
document.querySelectorAll('#hh-app .hh-panel').forEach(function(p) {
p.classList.remove('hh-active');
});
var panel = document.getElementById('hh-panel-' + id);
if (panel) panel.classList.add('hh-active');
}
window.hhShowTab = hhShowTab;

/* ═══════════════════════════════════════════════════════ REFERENCE */
function hhBuildCatBtns() {
var cont = document.getElementById('hh-cat-btns');
if (!cont) return;
cont.innerHTML = '';
HH_CATS.forEach(function(cat) {
var btn = document.createElement('button');
btn.className = 'hh-cat-btn' + (cat === hhCurrentCat ? ' hh-cat-active' : '');
btn.textContent = cat;
btn.onclick = function() { hhCurrentCat = cat; hhBuildCatBtns(); hhFilterRef(); };
cont.appendChild(btn);
});
}

function hhFilterRef() {
var q = (document.getElementById('hh-ref-search') ? document.getElementById('hh-ref-search').value : '').toLowerCase().trim();
var cards = document.getElementById('hh-cards');
var noRes = document.getElementById('hh-no-results');
var count = 0;
if (!cards) return;
cards.querySelectorAll('.hh-card').forEach(function(card) {
var name = (card.getAttribute('data-name') || '').toLowerCase();
var cat  = (card.getAttribute('data-cat') || '').toLowerCase();
var desc = (card.getAttribute('data-desc') || '').toLowerCase();
var catMatch = hhCurrentCat === 'All' || card.getAttribute('data-cat') === hhCurrentCat;
var qMatch = !q || name.indexOf(q) !== -1 || cat.indexOf(q) !== -1 || desc.indexOf(q) !== -1;
var show = catMatch && qMatch;
card.style.display = show ? '' : 'none';
if (show) count++;
});
if (noRes) noRes.style.display = count === 0 ? '' : 'none';
}
window.hhFilterRef = hhFilterRef;

function hhToggleCard(name) {
hhOpenCards[name] = !hhOpenCards[name];
var body = document.getElementById('hh-card-body-' + name);
var chev = document.getElementById('hh-card-chev-' + name);
if (body) body.classList.toggle('hh-open', hhOpenCards[name]);
if (chev) chev.textContent = hhOpenCards[name] ? '▼' : '▶';
}
window.hhToggleCard = hhToggleCard;

function hhBuildDirBadge(dir) {
var map = { req: ['hh-badge-req','Request'], res: ['hh-badge-res','Response'], both: ['hh-badge-both','Both'] };
var info = map[dir] || ['hh-badge-both', dir];
return '<span class="hh-badge ' + info[0] + '">' + info[1] + '</span>';
}

function hhBuildCards() {
var cards = document.getElementById('hh-cards');
if (!cards) return;
cards.innerHTML = '';
HH_HEADERS.forEach(function(h) {
var safeName = h.name.replace(/[^a-zA-Z0-9-]/g, '_');
var card = document.createElement('div');
card.className = 'hh-card';
card.setAttribute('data-name', h.name);
card.setAttribute('data-cat', h.cat);
card.setAttribute('data-desc', h.desc);
card.innerHTML =
'<div class="hh-card-head" onclick="hhToggleCard(\'' + safeName + '\')">' +
'<span class="hh-card-name">' + hEsc(h.name) + '</span>' +
hhBuildDirBadge(h.dir) +
'<span class="hh-badge hh-badge-cat">' + hEsc(h.cat) + '</span>' +
'<span class="hh-card-chevron" id="hh-card-chev-' + safeName + '">▶</span>' +
'</div>' +
'<div class="hh-card-body" id="hh-card-body-' + safeName + '">' +
'<div class="hh-card-desc">' + hEsc(h.desc) + '</div>' +
'<div class="hh-card-meta">' +
'<div class="hh-meta-item"><strong>Common values:</strong> ' + hEsc(h.values) + '</div>' +
'</div>' +
'<div class="hh-example-label">Example</div>' +
'<div class="hh-example-block">' + hEsc(h.example) + '</div>' +
'</div>';
cards.appendChild(card);
});
}

/* ═══════════════════════════════════════════════════════ BUILDER */
function hhSetFmt(fmt) {
hhCurrentFmt = fmt;
document.getElementById('hh-fmt-apache').classList.toggle('hh-fmt-active', fmt === 'apache');
document.getElementById('hh-fmt-nginx').classList.toggle('hh-fmt-active', fmt === 'nginx');
hhBuild();
}
window.hhSetFmt = hhSetFmt;

function c(id) { var el = document.getElementById(id); return el ? el.checked : false; }
function v(id) { var el = document.getElementById(id); return el ? el.value.trim() : ''; }

function hhBuild() {
// Toggle conditional fields
var cspF = document.getElementById('hh-b-csp-fields');
if (cspF) cspF.style.display = c('hh-b-csp') ? '' : 'none';
var ppF = document.getElementById('hh-b-pp-fields');
if (ppF) ppF.style.display = c('hh-b-pp') ? '' : 'none';

var headers = [];

if (c('hh-b-hsts')) {
var age = v('hh-hsts-age') || '31536000';
var hsts = 'max-age=' + age;
if (c('hh-hsts-sub')) hsts += '; includeSubDomains';
if (c('hh-hsts-pre')) hsts += '; preload';
headers.push(['Strict-Transport-Security', hsts]);
}
if (c('hh-b-xframe')) headers.push(['X-Frame-Options', v('hh-xframe-val') || 'SAMEORIGIN']);
if (c('hh-b-xcto'))   headers.push(['X-Content-Type-Options', 'nosniff']);
if (c('hh-b-rp'))     headers.push(['Referrer-Policy', v('hh-rp-val') || 'strict-origin-when-cross-origin']);
if (c('hh-b-csp')) {
var def = v('hh-csp-default') || "'self'";
var csp = "default-src " + def;
var scr = v('hh-csp-script'); if (scr) csp += "; script-src " + scr;
var sty = v('hh-csp-style');  if (sty) csp += "; style-src " + sty;
var img = v('hh-csp-img');    if (img) csp += "; img-src " + img;
var frm = v('hh-csp-frame');  if (frm) csp += "; frame-src " + frm;
headers.push(['Content-Security-Policy', csp]);
}
if (c('hh-b-pp')) {
var ppParts = [];
if (c('hh-pp-cam')) ppParts.push('camera=()');
if (c('hh-pp-mic')) ppParts.push('microphone=()');
if (c('hh-pp-geo')) ppParts.push('geolocation=()');
if (c('hh-pp-pay')) ppParts.push('payment=()');
if (c('hh-pp-usb')) ppParts.push('usb=()');
if (ppParts.length) headers.push(['Permissions-Policy', ppParts.join(', ')]);
}

var out = document.getElementById('hh-build-out');
if (!out) return;

var lines = [];
var raw = '';

if (hhCurrentFmt === 'apache') {
lines.push('# Security headers — generated by HTTP Header Analyzer');
lines.push('# https://productivity.works/tools/http-header-analyzer/');
lines.push('#');
lines.push('# Add to your .htaccess or Apache virtual host config');
lines.push('<IfModule mod_headers.c>');
headers.forEach(function(h) { lines.push('  Header always set ' + h[0] + ' "' + h[1] + '"'); });
lines.push('</IfModule>');
raw = lines.join('\n');
out.innerHTML = lines.map(function(line) {
if (line.startsWith('#')) return '<span class="hh-c-comment">' + hEsc(line) + '</span>';
if (line.trim().startsWith('<')) return '<span class="hh-c-tag">' + hEsc(line) + '</span>';
var m = line.match(/^(\s*Header always set )(\S+)(\s+)(".*")$/);
if (m) return hEsc(m[1]) + '<span class="hh-c-key">' + hEsc(m[2]) + '</span>' + hEsc(m[3]) + '<span class="hh-c-val">' + hEsc(m[4]) + '</span>';
return hEsc(line);
}).join('\n');
} else {
lines.push('# Security headers — generated by HTTP Header Analyzer');
lines.push('# https://productivity.works/tools/http-header-analyzer/');
lines.push('#');
lines.push('# Add inside your server {} or location {} block');
headers.forEach(function(h) { lines.push('add_header ' + h[0] + ' "' + h[1] + '" always;'); });
raw = lines.join('\n');
out.innerHTML = lines.map(function(line) {
if (line.startsWith('#')) return '<span class="hh-c-comment">' + hEsc(line) + '</span>';
var m = line.match(/^(add_header )(\S+)(\s+)(".*")(.*)/);
if (m) return '<span class="hh-c-dir">' + hEsc(m[1]) + '</span><span class="hh-c-key">' + hEsc(m[2]) + '</span>' + hEsc(m[3]) + '<span class="hh-c-val">' + hEsc(m[4]) + '</span>' + hEsc(m[5]);
return hEsc(line);
}).join('\n');
}
out.setAttribute('data-raw', raw);
}
window.hhBuild = hhBuild;

function hhCopyBuild() {
var out = document.getElementById('hh-build-out');
var raw = out ? out.getAttribute('data-raw') : '';
if (!raw) return;
var btn = document.getElementById('hh-build-copy');
if (navigator.clipboard) {
navigator.clipboard.writeText(raw).then(function() {
btn.textContent = 'Copied!'; btn.classList.add('hh-copied');
setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('hh-copied'); }, 2000);
});
} else {
var ta = document.createElement('textarea');
ta.value = raw; ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta); ta.select(); document.execCommand('copy'); document.body.removeChild(ta);
btn.textContent = 'Copied!'; btn.classList.add('hh-copied');
setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('hh-copied'); }, 2000);
}
}
window.hhCopyBuild = hhCopyBuild;

/* ═══════════════════════════════════════════════════════ PARSER */
var HH_KNOWN = {};
HH_HEADERS.forEach(function(h) { HH_KNOWN[h.name.toLowerCase()] = h; });

function hhParse() {
var raw = document.getElementById('hh-parse-input') ? document.getElementById('hh-parse-input').value : '';
var lines = raw.split(/\r?\n/).filter(function(l) { return l.trim() && !l.match(/^HTTP\//i); });
var out = document.getElementById('hh-parsed-out');
if (!out) return;
if (!lines.length) {
out.innerHTML = '<div class="hh-parse-placeholder">Paste headers above and click Parse to see the breakdown here.</div>';
return;
}
var parsed = [];
lines.forEach(function(line) {
var idx = line.indexOf(':');
if (idx < 1) return;
var name = line.substring(0, idx).trim();
var val  = line.substring(idx + 1).trim();
parsed.push({ name: name, val: val, known: HH_KNOWN[name.toLowerCase()] || null });
});
if (!parsed.length) {
out.innerHTML = '<div class="hh-parse-placeholder">No valid headers found. Make sure each header is on its own line in <code>Name: Value</code> format.</div>';
return;
}
var html = '<div class="hh-parsed-list">';
parsed.forEach(function(p) {
var dir = p.known ? hhBuildDirBadge(p.known.dir) : '';
var desc = p.known ? hEsc(p.known.desc) : '<span class="hh-parsed-unknown">Unknown or custom header — not in reference database.</span>';
html +=
'<div class="hh-parsed-item">' +
'<div class="hh-parsed-head">' +
'<span class="hh-parsed-name">' + hEsc(p.name) + '</span>' +
dir +
'<span class="hh-parsed-val" title="' + hEsc(p.val) + '">' + hEsc(p.val) + '</span>' +
'</div>' +
'<div class="hh-parsed-desc">' + desc + '</div>' +
'</div>';
});
html += '</div>';
out.innerHTML = html;
}
window.hhParse = hhParse;

/* ═══════════════════════════════════════════════════════ UTILS */
function hEsc(s) {
return (s || '').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

/* ═══════════════════════════════════════════════════════ INIT */
function hhInit() {
hhBuildCatBtns();
hhBuildCards();
hhBuild();
}
if (document.readyState === 'loading') {
document.addEventListener('DOMContentLoaded', hhInit);
} else {
hhInit();
}

})();
</script>

</div>

---

### Related Tools

> Reference HTTP status codes — [HTTP Status Codes](/tools/http-status-codes/)

> Generate Apache config — [.htaccess Generator](/tools/htaccess-generator/)

> Encode and decode data — [Base64 Encoder / Decoder](/tools/base64-encoder/)
