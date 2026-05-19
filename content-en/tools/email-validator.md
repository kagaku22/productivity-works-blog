---
title: "Email Validator - Check Email Address Format"
date: 2025-05-16
description: "Validate email addresses for correct format. Check syntax, domain structure, and common typos. Bulk validation support."
categories: ["Free Tools"]
slug: "email-validator"
ShowToc: false
cover:
  image: "/images/covers/email-validator.png"
  alt: "Email Validator"
---

<div id="ev-app">

<style>
#ev-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 780px;
margin: 0 auto;
color: #1a1a2e;
}
#ev-app h2 {
font-size: 1.4rem;
font-weight: 700;
margin: 1.6rem 0 0.8rem;
color: #1a1a2e;
}
#ev-app .ev-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 1.4rem;
}
#ev-app .ev-tab {
padding: 0.6rem 1.4rem;
cursor: pointer;
font-size: 0.95rem;
font-weight: 600;
color: #64748b;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
background: none;
border-top: none;
border-left: none;
border-right: none;
transition: color 0.2s, border-color 0.2s;
}
#ev-app .ev-tab.active {
color: #2563eb;
border-bottom-color: #2563eb;
}
#ev-app .ev-tab:hover:not(.active) {
color: #334155;
}
#ev-app .ev-panel {
display: none;
}
#ev-app .ev-panel.active {
display: block;
}
#ev-app .ev-input-row {
display: flex;
gap: 0.6rem;
margin-bottom: 1rem;
}
#ev-app input[type="email"],
#ev-app input[type="text"] {
flex: 1;
padding: 0.65rem 1rem;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 1rem;
outline: none;
transition: border-color 0.2s;
background: #f8fafc;
}
#ev-app input[type="email"]:focus,
#ev-app input[type="text"]:focus {
border-color: #2563eb;
background: #fff;
}
#ev-app textarea {
width: 100%;
min-height: 140px;
padding: 0.7rem 1rem;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 0.95rem;
font-family: "Courier New", monospace;
outline: none;
resize: vertical;
background: #f8fafc;
box-sizing: border-box;
transition: border-color 0.2s;
}
#ev-app textarea:focus {
border-color: #2563eb;
background: #fff;
}
#ev-app .ev-btn {
padding: 0.65rem 1.4rem;
background: #2563eb;
color: #fff;
border: none;
border-radius: 8px;
font-size: 0.97rem;
font-weight: 600;
cursor: pointer;
white-space: nowrap;
transition: background 0.2s;
}
#ev-app .ev-btn:hover {
background: #1d4ed8;
}
#ev-app .ev-btn.secondary {
background: #f1f5f9;
color: #334155;
border: 1.5px solid #cbd5e1;
}
#ev-app .ev-btn.secondary:hover {
background: #e2e8f0;
}
#ev-app .ev-btn.success {
background: #16a34a;
}
#ev-app .ev-btn.success:hover {
background: #15803d;
}
#ev-app .ev-result-single {
margin-top: 1rem;
padding: 1rem 1.2rem;
border-radius: 10px;
display: none;
}
#ev-app .ev-result-single.valid {
background: #f0fdf4;
border: 1.5px solid #86efac;
display: block;
}
#ev-app .ev-result-single.invalid {
background: #fff1f2;
border: 1.5px solid #fca5a5;
display: block;
}
#ev-app .ev-result-single .ev-status {
font-size: 1.05rem;
font-weight: 700;
display: flex;
align-items: center;
gap: 0.5rem;
margin-bottom: 0.5rem;
}
#ev-app .ev-result-single.valid .ev-status { color: #16a34a; }
#ev-app .ev-result-single.invalid .ev-status { color: #dc2626; }
#ev-app .ev-result-single .ev-detail {
font-size: 0.9rem;
color: #475569;
margin: 0.2rem 0;
}
#ev-app .ev-suggestion {
margin-top: 0.5rem;
padding: 0.5rem 0.8rem;
background: #fefce8;
border: 1px solid #fde68a;
border-radius: 6px;
font-size: 0.88rem;
color: #92400e;
}
#ev-app .ev-suggestion a {
color: #d97706;
font-weight: 600;
cursor: pointer;
text-decoration: underline;
}
#ev-app .ev-provider-badge {
display: inline-block;
padding: 0.2rem 0.6rem;
border-radius: 20px;
font-size: 0.8rem;
font-weight: 600;
margin-top: 0.4rem;
}
#ev-app .ev-provider-gmail { background: #fce8e6; color: #c5221f; }
#ev-app .ev-provider-yahoo { background: #e8f0fe; color: #1a73e8; }
#ev-app .ev-provider-outlook { background: #e3f2fd; color: #0077d7; }
#ev-app .ev-provider-icloud { background: #f3e8ff; color: #7c3aed; }
#ev-app .ev-provider-proton { background: #ecfdf5; color: #059669; }
#ev-app .ev-provider-other { background: #f1f5f9; color: #475569; }
#ev-app .ev-bulk-controls {
display: flex;
gap: 0.6rem;
margin-bottom: 0.8rem;
flex-wrap: wrap;
align-items: center;
}
#ev-app .ev-bulk-results {
margin-top: 1rem;
}
#ev-app .ev-bulk-summary {
display: flex;
gap: 1rem;
margin-bottom: 1rem;
flex-wrap: wrap;
}
#ev-app .ev-summary-card {
flex: 1;
min-width: 120px;
padding: 0.7rem 1rem;
border-radius: 8px;
text-align: center;
}
#ev-app .ev-summary-card .ev-num {
font-size: 1.8rem;
font-weight: 800;
line-height: 1;
}
#ev-app .ev-summary-card .ev-label {
font-size: 0.8rem;
margin-top: 0.2rem;
font-weight: 500;
}
#ev-app .ev-summary-card.total { background: #f1f5f9; color: #334155; }
#ev-app .ev-summary-card.valid { background: #f0fdf4; color: #16a34a; }
#ev-app .ev-summary-card.invalid { background: #fff1f2; color: #dc2626; }
#ev-app .ev-bulk-list {
list-style: none;
padding: 0;
margin: 0;
max-height: 320px;
overflow-y: auto;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
}
#ev-app .ev-bulk-list li {
display: flex;
align-items: center;
gap: 0.7rem;
padding: 0.55rem 0.9rem;
border-bottom: 1px solid #f1f5f9;
font-size: 0.9rem;
}
#ev-app .ev-bulk-list li:last-child { border-bottom: none; }
#ev-app .ev-bulk-list li.valid { background: #fafffe; }
#ev-app .ev-bulk-list li.invalid { background: #fffafa; }
#ev-app .ev-icon { font-size: 1rem; flex-shrink: 0; }
#ev-app .ev-email-text { font-family: "Courier New", monospace; flex: 1; word-break: break-all; }
#ev-app .ev-reason { font-size: 0.78rem; color: #94a3b8; margin-left: auto; text-align: right; }
#ev-app .ev-copy-area { margin-top: 0.8rem; display: flex; gap: 0.6rem; align-items: center; flex-wrap: wrap; }
#ev-app .ev-copy-feedback { font-size: 0.85rem; color: #16a34a; font-weight: 600; display: none; }
#ev-app .ev-footer-links {
margin-top: 2.5rem;
padding-top: 1.2rem;
border-top: 1.5px solid #e2e8f0;
}
#ev-app .ev-footer-links h3 {
font-size: 1rem;
font-weight: 700;
margin-bottom: 0.6rem;
color: #334155;
}
#ev-app .ev-footer-links ul {
list-style: none;
padding: 0;
margin: 0;
display: flex;
flex-wrap: wrap;
gap: 0.5rem 1.4rem;
}
#ev-app .ev-footer-links ul li a {
color: #2563eb;
text-decoration: none;
font-size: 0.92rem;
}
#ev-app .ev-footer-links ul li a:hover { text-decoration: underline; }
@media (max-width: 520px) {
#ev-app .ev-input-row { flex-direction: column; }
#ev-app .ev-btn { width: 100%; }
#ev-app .ev-bulk-controls { flex-direction: column; }
}
</style>

<div class="ev-tabs">
<button class="ev-tab active" onclick="evSwitchTab('single', this)">Single Email</button>
<button class="ev-tab" onclick="evSwitchTab('bulk', this)">Bulk Validation</button>
</div>

<!-- Single Panel -->
<div id="ev-panel-single" class="ev-panel active">
<div class="ev-input-row">
<input type="text" id="ev-single-input" placeholder="Enter email address (e.g. user@example.com)" onkeydown="if(event.key==='Enter')evValidateSingle()">
<button class="ev-btn" onclick="evValidateSingle()">Validate</button>
<button class="ev-btn secondary" onclick="evClearSingle()">Clear</button>
</div>
<div id="ev-single-result" class="ev-result-single"></div>
</div>

<!-- Bulk Panel -->
<div id="ev-panel-bulk" class="ev-panel">
<div class="ev-bulk-controls">
<button class="ev-btn" onclick="evValidateBulk()">Validate All</button>
<button class="ev-btn secondary" onclick="evClearBulk()">Clear</button>
<span style="font-size:0.85rem;color:#64748b;">One email per line</span>
</div>
<textarea id="ev-bulk-input" placeholder="user@gmail.com&#10;contact@company.com&#10;invalid-email&#10;test@yahoo.co.jp&#10;..."></textarea>
<div id="ev-bulk-results" class="ev-bulk-results" style="display:none;">
<div id="ev-bulk-summary" class="ev-bulk-summary"></div>
<div class="ev-copy-area">
<button class="ev-btn success" onclick="evCopyValid()">Copy Valid Emails</button>
<span id="ev-copy-feedback" class="ev-copy-feedback">Copied!</span>
</div>
<ul id="ev-bulk-list" class="ev-bulk-list"></ul>
</div>
</div>

<div class="ev-footer-links">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/password-generator/">Password Generator</a></li>
<li><a href="/tools/word-counter/">Word Counter</a></li>
<li><a href="/tools/json-formatter/">JSON Formatter</a></li>
<li><a href="/tools/url-encoder/">URL Encoder / Decoder</a></li>
<li><a href="/tools/base64-encoder/">Base64 Encoder</a></li>
</ul>
</div>

<script>
(function () {
"use strict";

// --- Typo map: wrong domain → correct domain ---
var TYPO_MAP = {
"gmial.com": "gmail.com",
"gmai.com": "gmail.com",
"gmail.con": "gmail.com",
"gmail.cmo": "gmail.com",
"gmaill.com": "gmail.com",
"gmailcom": "gmail.com",
"gnail.com": "gmail.com",
"gamil.com": "gmail.com",
"yahooo.com": "yahoo.com",
"yaho.com": "yahoo.com",
"yahoo.con": "yahoo.com",
"yahoo.cmo": "yahoo.com",
"yahooo.co.jp": "yahoo.co.jp",
"yaho.co.jp": "yahoo.co.jp",
"hotmial.com": "hotmail.com",
"hotmail.con": "hotmail.com",
"hotmal.com": "hotmail.com",
"outllook.com": "outlook.com",
"outlok.com": "outlook.com",
"outlook.con": "outlook.com",
"outlookcom": "outlook.com",
"icoud.com": "icloud.com",
"iclod.com": "icloud.com",
"protonmal.com": "protonmail.com",
"protonmial.com": "protonmail.com"
};

// --- Provider detection ---
var PROVIDERS = {
"gmail.com": { name: "Gmail", cls: "ev-provider-gmail" },
"googlemail.com": { name: "Gmail", cls: "ev-provider-gmail" },
"yahoo.com": { name: "Yahoo Mail", cls: "ev-provider-yahoo" },
"yahoo.co.jp": { name: "Yahoo Mail JP", cls: "ev-provider-yahoo" },
"yahoo.co.uk": { name: "Yahoo Mail UK", cls: "ev-provider-yahoo" },
"ymail.com": { name: "Yahoo Mail", cls: "ev-provider-yahoo" },
"outlook.com": { name: "Outlook", cls: "ev-provider-outlook" },
"hotmail.com": { name: "Hotmail / Outlook", cls: "ev-provider-outlook" },
"live.com": { name: "Outlook / Live", cls: "ev-provider-outlook" },
"msn.com": { name: "MSN / Outlook", cls: "ev-provider-outlook" },
"icloud.com": { name: "iCloud Mail", cls: "ev-provider-icloud" },
"me.com": { name: "iCloud Mail", cls: "ev-provider-icloud" },
"mac.com": { name: "iCloud Mail", cls: "ev-provider-icloud" },
"protonmail.com": { name: "Proton Mail", cls: "ev-provider-proton" },
"pm.me": { name: "Proton Mail", cls: "ev-provider-proton" }
};

// --- Core validator ---
function validateEmail(raw) {
var email = raw.trim();
var result = {
email: email,
valid: false,
reason: "",
suggestion: null,
provider: null,
providerCls: null
};

if (!email) {
result.reason = "Email address is empty.";
return result;
}

// Basic structure check
var atCount = (email.match(/@/g) || []).length;
if (atCount === 0) {
result.reason = "Missing @ symbol.";
return result;
}
if (atCount > 1) {
result.reason = "Multiple @ symbols found.";
return result;
}

var parts = email.split("@");
var local = parts[0];
var domain = parts[1];

// Local part checks
if (!local || local.length === 0) {
result.reason = "Nothing before the @ symbol.";
return result;
}
if (local.length > 64) {
result.reason = "Local part (before @) exceeds 64 characters.";
return result;
}
if (/^\./.test(local) || /\.$/.test(local)) {
result.reason = "Local part cannot start or end with a dot.";
return result;
}
if (/\.{2,}/.test(local)) {
result.reason = "Local part contains consecutive dots.";
return result;
}
if (!/^[a-zA-Z0-9!#$%&'*+/=?^_`{|}~.-]+$/.test(local)) {
result.reason = "Local part contains invalid characters.";
return result;
}

// Domain checks
if (!domain || domain.length === 0) {
result.reason = "Nothing after the @ symbol.";
return result;
}
if (domain.length > 255) {
result.reason = "Domain exceeds maximum length.";
return result;
}
if (!domain.includes(".")) {
result.reason = "Domain has no dot (e.g. missing .com).";
// check for missing dot typos like "gmailcom"
var possibleFixed = null;
Object.keys(TYPO_MAP).forEach(function (t) {
if (domain.toLowerCase() === t.replace(".", "")) {
possibleFixed = local + "@" + TYPO_MAP[t];
}
});
if (possibleFixed) result.suggestion = possibleFixed;
return result;
}
if (/^-|-$/.test(domain.split(".")[0])) {
result.reason = "Domain label cannot start or end with a hyphen.";
return result;
}
if (/\.{2,}/.test(domain)) {
result.reason = "Domain contains consecutive dots.";
return result;
}
if (/^\.|\.$/.test(domain)) {
result.reason = "Domain cannot start or end with a dot.";
return result;
}
var tld = domain.split(".").pop();
if (!tld || tld.length < 2) {
result.reason = "TLD (e.g. .com) is too short or missing.";
return result;
}
if (!/^[a-zA-Z]{2,}$/.test(tld)) {
result.reason = "TLD contains invalid characters.";
return result;
}
if (!/^[a-zA-Z0-9.-]+$/.test(domain)) {
result.reason = "Domain contains invalid characters.";
return result;
}

// Full regex sanity check
var re = /^[a-zA-Z0-9!#$%&'*+/=?^_`{|}~.-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
if (!re.test(email)) {
result.reason = "Email format is not valid.";
return result;
}

// Typo detection
var domainLower = domain.toLowerCase();
if (TYPO_MAP[domainLower]) {
result.suggestion = local + "@" + TYPO_MAP[domainLower];
}

// Provider detection
if (PROVIDERS[domainLower]) {
result.provider = PROVIDERS[domainLower].name;
result.providerCls = PROVIDERS[domainLower].cls;
} else {
result.provider = "Custom Domain";
result.providerCls = "ev-provider-other";
}

result.valid = true;
result.reason = "Syntax and domain structure look correct.";
return result;
}

// --- Tab switcher ---
window.evSwitchTab = function (tab, btn) {
document.querySelectorAll("#ev-app .ev-panel").forEach(function (p) { p.classList.remove("active"); });
document.querySelectorAll("#ev-app .ev-tab").forEach(function (b) { b.classList.remove("active"); });
document.getElementById("ev-panel-" + tab).classList.add("active");
btn.classList.add("active");
};

// --- Single validation ---
window.evValidateSingle = function () {
var input = document.getElementById("ev-single-input").value;
var r = validateEmail(input);
var el = document.getElementById("ev-single-result");
el.className = "ev-result-single " + (r.valid ? "valid" : "invalid");

var html = '<div class="ev-status">' +
(r.valid ? "&#10003;" : "&#10007;") +
" <span>" + (r.valid ? "Valid Email Address" : "Invalid Email Address") + "</span></div>";
html += '<div class="ev-detail"><strong>Email:</strong> ' + escHtml(r.email) + "</div>";
html += '<div class="ev-detail"><strong>Result:</strong> ' + escHtml(r.reason) + "</div>";

if (r.valid && r.provider) {
html += '<span class="ev-provider-badge ' + r.providerCls + '">' + escHtml(r.provider) + "</span>";
}
if (r.suggestion) {
html += '<div class="ev-suggestion">Did you mean: <a onclick="evUseSuggestion(\'' + escAttr(r.suggestion) + '\')">' + escHtml(r.suggestion) + "</a>?</div>";
}

el.innerHTML = html;
};

window.evUseSuggestion = function (suggested) {
document.getElementById("ev-single-input").value = suggested;
evValidateSingle();
};

window.evClearSingle = function () {
document.getElementById("ev-single-input").value = "";
var el = document.getElementById("ev-single-result");
el.className = "ev-result-single";
el.innerHTML = "";
};

// --- Bulk validation ---
var bulkResults = [];

window.evValidateBulk = function () {
var raw = document.getElementById("ev-bulk-input").value;
var lines = raw.split("\n").map(function (l) { return l.trim(); }).filter(function (l) { return l.length > 0; });

if (lines.length === 0) return;

bulkResults = lines.map(validateEmail);

var valid = bulkResults.filter(function (r) { return r.valid; });
var invalid = bulkResults.filter(function (r) { return !r.valid; });

// Summary
var summary = document.getElementById("ev-bulk-summary");
summary.innerHTML =
'<div class="ev-summary-card total"><div class="ev-num">' + bulkResults.length + '</div><div class="ev-label">Total</div></div>' +
'<div class="ev-summary-card valid"><div class="ev-num">' + valid.length + '</div><div class="ev-label">Valid</div></div>' +
'<div class="ev-summary-card invalid"><div class="ev-num">' + invalid.length + '</div><div class="ev-label">Invalid</div></div>';

// List
var list = document.getElementById("ev-bulk-list");
list.innerHTML = bulkResults.map(function (r) {
return '<li class="' + (r.valid ? "valid" : "invalid") + '">' +
'<span class="ev-icon">' + (r.valid ? "&#10003;" : "&#10007;") + "</span>" +
'<span class="ev-email-text">' + escHtml(r.email) + "</span>" +
(r.provider ? '<span class="ev-provider-badge ' + r.providerCls + '" style="font-size:0.72rem;padding:0.1rem 0.4rem;">' + escHtml(r.provider) + "</span>" : "") +
'<span class="ev-reason">' + escHtml(r.reason) + "</span>" +
"</li>";
}).join("");

document.getElementById("ev-bulk-results").style.display = "block";
};

window.evClearBulk = function () {
document.getElementById("ev-bulk-input").value = "";
document.getElementById("ev-bulk-results").style.display = "none";
bulkResults = [];
};

window.evCopyValid = function () {
var validEmails = bulkResults.filter(function (r) { return r.valid; }).map(function (r) { return r.email; });
if (validEmails.length === 0) return;
var text = validEmails.join("\n");
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(showCopied);
} else {
var ta = document.createElement("textarea");
ta.value = text;
ta.style.position = "fixed";
ta.style.opacity = "0";
document.body.appendChild(ta);
ta.select();
document.execCommand("copy");
document.body.removeChild(ta);
showCopied();
}
};

function showCopied() {
var fb = document.getElementById("ev-copy-feedback");
fb.style.display = "inline";
setTimeout(function () { fb.style.display = "none"; }, 2000);
}

function escHtml(s) {
return String(s).replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot;");
}
function escAttr(s) {
return String(s).replace(/'/g, "\\'");
}
})();
</script>

</div>

---

## Related Tools

> [Email Signature Generator](/tools/email-signature-generator/)
> [Email Template Builder](/tools/email-template-builder/)

