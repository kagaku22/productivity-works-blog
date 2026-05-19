---
title: "Open Graph Preview — Social Share Debugger"
date: 2025-05-16
description: "Preview how your page looks on Facebook, Twitter, LinkedIn, and Google. Generate OG meta tags with live previews. Check character limits and image dimensions."
categories: ["Free Tools"]
slug: "og-preview"
ShowToc: false
aliases:
  - "/tools/og-preview/"
  - "/tools/og-preview/"
cover:
  image: "/images/covers/og-preview.png"
  alt: "Open Graph Preview"
---

Paste your URL or fill in the fields below to instantly preview how your page will appear when shared on Facebook, Twitter, LinkedIn, and in Google search results.

<div id="og-app">

<style>
/* ── Reset & base ── */
#og-app *,
#og-app *::before,
#og-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#og-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
font-size: 15px;
color: #1a1a2e;
line-height: 1.5;
}

/* ── Layout ── */
#og-app .og-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 24px;
margin-top: 20px;
}
@media (max-width: 760px) {
#og-app .og-grid {
grid-template-columns: 1fr;
}
}

/* ── Panel ── */
#og-app .og-panel {
background: #f8f9fc;
border: 1px solid #dde1ea;
border-radius: 10px;
padding: 22px 20px;
}
#og-app .og-panel h2 {
font-size: 15px;
font-weight: 700;
color: #2c3e6b;
margin-bottom: 16px;
padding-bottom: 10px;
border-bottom: 2px solid #dde1ea;
letter-spacing: 0.02em;
text-transform: uppercase;
}

/* ── Form fields ── */
#og-app .og-field {
margin-bottom: 14px;
}
#og-app .og-field label {
display: block;
font-size: 12px;
font-weight: 600;
color: #4a5378;
margin-bottom: 5px;
letter-spacing: 0.03em;
}
#og-app .og-field input,
#og-app .og-field select,
#og-app .og-field textarea {
width: 100%;
padding: 8px 11px;
border: 1px solid #c8cdd8;
border-radius: 6px;
font-size: 13px;
color: #1a1a2e;
background: #fff;
transition: border-color 0.18s;
outline: none;
font-family: inherit;
}
#og-app .og-field input:focus,
#og-app .og-field select:focus,
#og-app .og-field textarea:focus {
border-color: #4f6ef7;
box-shadow: 0 0 0 3px rgba(79,110,247,0.12);
}
#og-app .og-field textarea {
resize: vertical;
min-height: 64px;
}

/* ── Character counter ── */
#og-app .og-char-info {
display: flex;
justify-content: flex-end;
font-size: 11px;
margin-top: 4px;
color: #888;
transition: color 0.2s;
}
#og-app .og-char-info.warn {
color: #d97706;
font-weight: 600;
}
#og-app .og-char-info.over {
color: #dc2626;
font-weight: 700;
}

/* ── Image hint ── */
#og-app .og-img-hint {
font-size: 11px;
color: #6b7280;
margin-top: 5px;
line-height: 1.4;
}
#og-app .og-img-hint span {
display: inline-block;
background: #e8eeff;
color: #3b5bdb;
border-radius: 4px;
padding: 1px 6px;
font-weight: 600;
font-size: 10.5px;
margin-right: 4px;
}

/* ── Buttons ── */
#og-app .og-btn-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-top: 18px;
}
#og-app .og-btn {
padding: 9px 18px;
border-radius: 7px;
border: none;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background 0.18s, transform 0.1s;
font-family: inherit;
}
#og-app .og-btn:active {
transform: scale(0.97);
}
#og-app .og-btn-primary {
background: #4f6ef7;
color: #fff;
}
#og-app .og-btn-primary:hover {
background: #3a56d4;
}
#og-app .og-btn-secondary {
background: #e8eeff;
color: #3b5bdb;
border: 1px solid #c5d0ff;
}
#og-app .og-btn-secondary:hover {
background: #d5dfff;
}
#og-app .og-btn-success {
background: #059669;
color: #fff;
}
#og-app .og-btn-success:hover {
background: #047857;
}

/* ── Toast ── */
#og-app .og-toast {
display: none;
position: fixed;
bottom: 28px;
right: 28px;
background: #1e293b;
color: #fff;
padding: 11px 20px;
border-radius: 8px;
font-size: 13px;
font-weight: 500;
z-index: 9999;
box-shadow: 0 4px 18px rgba(0,0,0,0.22);
animation: og-fadeIn 0.25s ease;
}
@keyframes og-fadeIn {
from { opacity: 0; transform: translateY(8px); }
to   { opacity: 1; transform: translateY(0); }
}

/* ── Section divider ── */
#og-app .og-section-label {
font-size: 11px;
font-weight: 700;
color: #4f6ef7;
letter-spacing: 0.08em;
text-transform: uppercase;
margin: 18px 0 10px;
padding-left: 2px;
}

/* ── Preview panels ── */
#og-app .og-previews {
margin-top: 28px;
}
#og-app .og-previews h2 {
font-size: 17px;
font-weight: 700;
color: #2c3e6b;
margin-bottom: 18px;
}
#og-app .og-preview-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 20px;
}
@media (max-width: 680px) {
#og-app .og-preview-grid {
grid-template-columns: 1fr;
}
}

/* ── Facebook card ── */
#og-app .og-card-fb {
border: 1px solid #dde1ea;
border-radius: 4px;
overflow: hidden;
background: #fff;
font-family: Helvetica, Arial, sans-serif;
max-width: 500px;
}
#og-app .og-card-fb .og-card-img {
width: 100%;
aspect-ratio: 1.91/1;
object-fit: cover;
background: #e5e7eb;
display: flex;
align-items: center;
justify-content: center;
color: #9ca3af;
font-size: 13px;
}
#og-app .og-card-fb .og-card-img img {
width: 100%;
height: 100%;
object-fit: cover;
display: block;
}
#og-app .og-card-fb .og-card-body {
padding: 10px 12px 12px;
border-top: 1px solid #dde1ea;
background: #f2f3f5;
}
#og-app .og-card-fb .og-card-domain {
font-size: 11px;
color: #606770;
text-transform: uppercase;
letter-spacing: 0.02em;
margin-bottom: 3px;
}
#og-app .og-card-fb .og-card-title {
font-size: 16px;
font-weight: 700;
color: #1c1e21;
line-height: 1.3;
margin-bottom: 4px;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
}
#og-app .og-card-fb .og-card-desc {
font-size: 14px;
color: #606770;
line-height: 1.4;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
}

/* ── Twitter card ── */
#og-app .og-card-tw {
border: 1px solid #e1e8ed;
border-radius: 14px;
overflow: hidden;
background: #fff;
font-family: -apple-system, "Segoe UI", sans-serif;
max-width: 500px;
}
#og-app .og-card-tw.summary-large .og-card-img-tw {
aspect-ratio: 2/1;
}
#og-app .og-card-tw.summary .og-tw-inner {
display: flex;
flex-direction: row;
}
#og-app .og-card-tw.summary .og-card-img-tw {
width: 120px;
min-width: 120px;
aspect-ratio: 1/1;
flex-shrink: 0;
}
#og-app .og-card-img-tw {
width: 100%;
background: #e5e7eb;
display: flex;
align-items: center;
justify-content: center;
color: #9ca3af;
font-size: 13px;
overflow: hidden;
}
#og-app .og-card-img-tw img {
width: 100%;
height: 100%;
object-fit: cover;
display: block;
}
#og-app .og-card-tw .og-card-body-tw {
padding: 10px 14px 12px;
flex: 1;
}
#og-app .og-card-tw .og-card-domain-tw {
font-size: 13px;
color: #8899a6;
margin-bottom: 3px;
}
#og-app .og-card-tw .og-card-title-tw {
font-size: 15px;
font-weight: 700;
color: #14171a;
line-height: 1.3;
margin-bottom: 3px;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
}
#og-app .og-card-tw .og-card-desc-tw {
font-size: 13px;
color: #657786;
line-height: 1.4;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
}

/* ── LinkedIn card ── */
#og-app .og-card-li {
border: 1px solid #d6d6d6;
border-radius: 2px;
overflow: hidden;
background: #fff;
font-family: -apple-system, "Segoe UI", sans-serif;
max-width: 500px;
}
#og-app .og-card-li .og-card-img-li {
width: 100%;
aspect-ratio: 1.91/1;
background: #e5e7eb;
display: flex;
align-items: center;
justify-content: center;
color: #9ca3af;
font-size: 13px;
overflow: hidden;
}
#og-app .og-card-li .og-card-img-li img {
width: 100%;
height: 100%;
object-fit: cover;
display: block;
}
#og-app .og-card-li .og-card-body-li {
padding: 8px 12px 10px;
background: #f3f2ef;
border-top: 1px solid #d6d6d6;
}
#og-app .og-card-li .og-card-title-li {
font-size: 14px;
font-weight: 600;
color: rgba(0,0,0,0.9);
line-height: 1.35;
margin-bottom: 2px;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
}
#og-app .og-card-li .og-card-domain-li {
font-size: 12px;
color: rgba(0,0,0,0.6);
}

/* ── Google SERP ── */
#og-app .og-card-google {
background: #fff;
padding: 14px 16px;
border: 1px solid #dde1ea;
border-radius: 8px;
max-width: 600px;
font-family: arial, sans-serif;
}
#og-app .og-card-google .og-serp-url {
font-size: 12px;
color: #202124;
line-height: 1.4;
margin-bottom: 4px;
}
#og-app .og-card-google .og-serp-breadcrumb {
font-size: 12px;
color: #5f6368;
}
#og-app .og-card-google .og-serp-title {
font-size: 20px;
color: #1a0dab;
line-height: 1.3;
margin-bottom: 3px;
display: -webkit-box;
-webkit-line-clamp: 1;
-webkit-box-orient: vertical;
overflow: hidden;
cursor: pointer;
text-decoration: none;
}
#og-app .og-card-google .og-serp-title:hover {
text-decoration: underline;
}
#og-app .og-card-google .og-serp-desc {
font-size: 14px;
color: #4d5156;
line-height: 1.58;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
overflow: hidden;
}

/* ── Card label ── */
#og-app .og-card-label {
font-size: 11px;
font-weight: 700;
color: #6b7280;
text-transform: uppercase;
letter-spacing: 0.07em;
margin-bottom: 7px;
}

/* ── Code output ── */
#og-app .og-code-wrap {
margin-top: 24px;
display: none;
}
#og-app .og-code-wrap h3 {
font-size: 14px;
font-weight: 700;
color: #2c3e6b;
margin-bottom: 8px;
}
#og-app .og-code-box {
background: #0f172a;
color: #e2e8f0;
border-radius: 8px;
padding: 16px;
font-family: "Fira Code", "Cascadia Code", Consolas, monospace;
font-size: 12px;
line-height: 1.7;
overflow-x: auto;
white-space: pre;
}

/* ── Dimension table ── */
#og-app .og-dim-table {
width: 100%;
border-collapse: collapse;
font-size: 12.5px;
margin-top: 4px;
}
#og-app .og-dim-table th {
text-align: left;
font-weight: 600;
color: #4a5378;
padding: 5px 8px;
background: #eef0f8;
border: 1px solid #dde1ea;
}
#og-app .og-dim-table td {
padding: 5px 8px;
border: 1px solid #dde1ea;
color: #374151;
}
#og-app .og-dim-table tr:nth-child(even) td {
background: #f8f9fc;
}
</style>

<div class="og-grid">

<!-- ═══ LEFT: OG fields ═══ -->
<div class="og-panel">
<h2>Open Graph Properties</h2>

<div class="og-section-label">Core Tags</div>

<div class="og-field">
<label for="og-title">og:title</label>
<input type="text" id="og-title" placeholder="Your page title" maxlength="200">
<div class="og-char-info" id="og-title-count">0 / 60</div>
</div>

<div class="og-field">
<label for="og-description">og:description</label>
<textarea id="og-description" placeholder="A concise description of your page content..."></textarea>
<div class="og-char-info" id="og-desc-count">0 / 160</div>
</div>

<div class="og-field">
<label for="og-url">og:url</label>
<input type="url" id="og-url" placeholder="https://example.com/page">
</div>

<div class="og-field">
<label for="og-image">og:image (URL)</label>
<input type="url" id="og-image" placeholder="https://example.com/image.jpg">
<div class="og-img-hint">Recommended: <span>1200 × 630 px</span> (1.91:1) · Min 600 × 315 px · Max 8 MB</div>
</div>

<div class="og-field">
<label for="og-type">og:type</label>
<select id="og-type">
<option value="website">website</option>
<option value="article">article</option>
<option value="product">product</option>
<option value="video.other">video.other</option>
<option value="music.song">music.song</option>
<option value="book">book</option>
<option value="profile">profile</option>
</select>
</div>

<div class="og-field">
<label for="og-site-name">og:site_name</label>
<input type="text" id="og-site-name" placeholder="Your Site Name">
</div>

<div class="og-section-label" style="margin-top:22px;">Twitter Card</div>

<div class="og-field">
<label for="tw-card">twitter:card</label>
<select id="tw-card">
<option value="summary_large_image">summary_large_image (large image)</option>
<option value="summary">summary (small square image)</option>
</select>
</div>

<div class="og-field">
<label for="tw-title">twitter:title <em style="font-weight:400;color:#9ca3af;">(leave blank to use og:title)</em></label>
<input type="text" id="tw-title" placeholder="Twitter-specific title (optional)">
<div class="og-char-info" id="tw-title-count">0 / 70</div>
</div>

<div class="og-field">
<label for="tw-description">twitter:description <em style="font-weight:400;color:#9ca3af;">(leave blank to use og:description)</em></label>
<textarea id="tw-description" placeholder="Twitter-specific description (optional)"></textarea>
<div class="og-char-info" id="tw-desc-count">0 / 200</div>
</div>

<div class="og-field">
<label for="tw-image">twitter:image <em style="font-weight:400;color:#9ca3af;">(leave blank to use og:image)</em></label>
<input type="url" id="tw-image" placeholder="https://example.com/twitter-image.jpg">
<div class="og-img-hint">summary_large_image: <span>1200 × 628 px</span> · summary: <span>144 × 144 px</span></div>
</div>

<div class="og-btn-row">
<button class="og-btn og-btn-primary" id="og-generate-btn">Generate HTML Meta Tags</button>
<button class="og-btn og-btn-secondary" id="og-clear-btn">Clear All</button>
</div>
</div>

<!-- ═══ RIGHT: dimension reference ═══ -->
<div class="og-panel">
<h2>Image Dimension Guide</h2>

<table class="og-dim-table">
<thead>
<tr>
<th>Platform</th>
<th>Recommended Size</th>
<th>Ratio</th>
<th>Max Size</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Facebook</strong></td>
<td>1200 × 630 px</td>
<td>1.91:1</td>
<td>8 MB</td>
</tr>
<tr>
<td><strong>Twitter Large</strong></td>
<td>1200 × 628 px</td>
<td>~1.91:1</td>
<td>5 MB</td>
</tr>
<tr>
<td><strong>Twitter Summary</strong></td>
<td>144 × 144 px</td>
<td>1:1</td>
<td>5 MB</td>
</tr>
<tr>
<td><strong>LinkedIn</strong></td>
<td>1200 × 627 px</td>
<td>1.91:1</td>
<td>5 MB</td>
</tr>
<tr>
<td><strong>Google (SERP)</strong></td>
<td>N/A (uses text)</td>
<td>—</td>
<td>—</td>
</tr>
</tbody>
</table>

<div style="margin-top:20px;">
<div class="og-section-label">Title Character Limits</div>
<table class="og-dim-table">
<thead>
<tr><th>Platform</th><th>Title</th><th>Description</th></tr>
</thead>
<tbody>
<tr><td><strong>Facebook OG</strong></td><td>~60 chars</td><td>~160 chars</td></tr>
<tr><td><strong>Twitter</strong></td><td>~70 chars</td><td>~200 chars</td></tr>
<tr><td><strong>LinkedIn</strong></td><td>~119 chars</td><td>~300 chars</td></tr>
<tr><td><strong>Google SERP</strong></td><td>~60 chars</td><td>~160 chars</td></tr>
</tbody>
</table>
</div>

<div style="margin-top:20px;">
<div class="og-section-label">Tips</div>
<ul style="font-size:12.5px;color:#374151;padding-left:18px;line-height:1.8;">
<li>Use HTTPS for all image URLs (HTTP may be blocked).</li>
<li>Facebook caches OG data — use the <a href="https://developers.facebook.com/tools/json-formatter/" target="_blank" rel="noopener" style="color:#4f6ef7;">Sharing Debugger</a> to refresh.</li>
<li>Twitter crawls images on first share. Images smaller than 144×144 px are ignored.</li>
<li>LinkedIn has a 7-day cache — post a new URL to trigger a fresh crawl.</li>
<li>Keep titles under 60 characters to avoid truncation in Google search.</li>
<li>Avoid duplicate og:title and &lt;title&gt; tag values where possible.</li>
</ul>
</div>
</div>

</div>

<!-- ═══ LIVE PREVIEWS ═══ -->
<div class="og-previews">
<h2>Live Previews</h2>
<div class="og-preview-grid">

<!-- Facebook -->
<div>
<div class="og-card-label">Facebook</div>
<div class="og-card-fb" id="prev-fb">
<div class="og-card-img" id="prev-fb-img-wrap">
<span>No image URL provided</span>
</div>
<div class="og-card-body">
<div class="og-card-domain" id="prev-fb-domain">example.com</div>
<div class="og-card-title" id="prev-fb-title">Your page title will appear here</div>
<div class="og-card-desc" id="prev-fb-desc">Your page description will appear here.</div>
</div>
</div>
</div>

<!-- Twitter -->
<div>
<div class="og-card-label">Twitter / X</div>
<div class="og-card-tw summary-large" id="prev-tw">
<div class="og-tw-inner">
<div class="og-card-img-tw" id="prev-tw-img-wrap" style="aspect-ratio:2/1;">
<span>No image URL provided</span>
</div>
<div class="og-card-body-tw">
<div class="og-card-domain-tw" id="prev-tw-domain">example.com</div>
<div class="og-card-title-tw" id="prev-tw-title">Your page title will appear here</div>
<div class="og-card-desc-tw" id="prev-tw-desc">Your page description will appear here.</div>
</div>
</div>
</div>
</div>

<!-- LinkedIn -->
<div>
<div class="og-card-label">LinkedIn</div>
<div class="og-card-li" id="prev-li">
<div class="og-card-img-li" id="prev-li-img-wrap">
<span>No image URL provided</span>
</div>
<div class="og-card-body-li">
<div class="og-card-title-li" id="prev-li-title">Your page title will appear here</div>
<div class="og-card-domain-li" id="prev-li-domain">example.com</div>
</div>
</div>
</div>

<!-- Google SERP -->
<div>
<div class="og-card-label">Google Search Result</div>
<div class="og-card-google">
<div class="og-serp-url">
<span id="prev-g-sitename">Your Site</span> &rsaquo;
<span class="og-serp-breadcrumb" id="prev-g-breadcrumb">example.com</span>
</div>
<div class="og-serp-title" id="prev-g-title">Your page title will appear here</div>
<div class="og-serp-desc" id="prev-g-desc">Your page description will appear here. Google may override this with page content it deems more relevant to the query.</div>
</div>
</div>

</div>
</div>

<!-- ═══ GENERATED CODE ═══ -->
<div class="og-code-wrap" id="og-code-section">
<h3>Generated HTML Meta Tags</h3>
<div class="og-btn-row" style="margin-bottom:10px;">
<button class="og-btn og-btn-success" id="og-copy-btn">Copy to Clipboard</button>
</div>
<div class="og-code-box" id="og-code-output"></div>
</div>

<div id="og-toast" class="og-toast">Copied to clipboard!</div>

<script>
(function() {
'use strict';

/* ── Helpers ── */
function el(id) { return document.getElementById(id); }

function getDomain(url) {
try {
return new URL(url).hostname.replace(/^www\./, '');
} catch(e) {
return url ? url.replace(/^https?:\/\/(www\.)?/, '').split('/')[0] : 'example.com';
}
}

function escapeHtml(str) {
return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

/* ── Character counter ── */
function bindCounter(inputId, counterId, limit) {
var inp = el(inputId);
var ctr = el(counterId);
if (!inp || !ctr) return;
inp.addEventListener('input', function() {
var len = inp.value.length;
ctr.textContent = len + ' / ' + limit;
ctr.className = 'og-char-info' +
(len > limit ? ' over' : (len > limit * 0.85 ? ' warn' : ''));
});
}

bindCounter('og-title',       'og-title-count',  60);
bindCounter('og-description', 'og-desc-count',  160);
bindCounter('tw-title',       'tw-title-count',   70);
bindCounter('tw-description', 'tw-desc-count',  200);

/* ── Live image render ── */
function renderImage(wrapId, url, placeholderText) {
var wrap = el(wrapId);
if (!wrap) return;
if (url && url.trim()) {
wrap.innerHTML = '<img src="' + escapeHtml(url.trim()) + '" alt="OG Preview Image" onerror="this.parentNode.innerHTML=\'<span>Image failed to load</span>\'">';
} else {
wrap.innerHTML = '<span>' + placeholderText + '</span>';
}
}

/* ── Update previews ── */
function updatePreviews() {
var title    = el('og-title').value.trim()       || 'Your page title will appear here';
var desc     = el('og-description').value.trim() || 'Your page description will appear here.';
var url      = el('og-url').value.trim();
var image    = el('og-image').value.trim();
var twCard   = el('tw-card').value;
var twTitle  = el('tw-title').value.trim()       || title;
var twDesc   = el('tw-description').value.trim() || desc;
var twImage  = el('tw-image').value.trim()       || image;
var siteName = el('og-site-name').value.trim();
var domain   = getDomain(url) || 'example.com';

/* Facebook */
el('prev-fb-title').textContent  = title;
el('prev-fb-desc').textContent   = desc;
el('prev-fb-domain').textContent = domain.toUpperCase();
renderImage('prev-fb-img-wrap', image, 'No image URL provided');

/* Twitter */
var twCardEl = el('prev-tw');
if (twCard === 'summary') {
twCardEl.className = 'og-card-tw summary';
var imgWrap = el('prev-tw-img-wrap');
if (imgWrap) {
imgWrap.style.aspectRatio = '1/1';
imgWrap.style.width = '120px';
}
} else {
twCardEl.className = 'og-card-tw summary-large';
var imgWrap2 = el('prev-tw-img-wrap');
if (imgWrap2) {
imgWrap2.style.aspectRatio = '2/1';
imgWrap2.style.width = '100%';
}
}
el('prev-tw-title').textContent  = twTitle;
el('prev-tw-desc').textContent   = twDesc;
el('prev-tw-domain').textContent = domain;
renderImage('prev-tw-img-wrap', twImage, 'No image URL provided');

/* LinkedIn */
el('prev-li-title').textContent  = title;
el('prev-li-domain').textContent = domain;
renderImage('prev-li-img-wrap', image, 'No image URL provided');

/* Google */
el('prev-g-title').textContent      = title;
el('prev-g-desc').textContent       = desc;
el('prev-g-breadcrumb').textContent = domain;
el('prev-g-sitename').textContent   = siteName || domain;
}

/* ── Debounce ── */
var debounceTimer;
function debounce(fn, delay) {
clearTimeout(debounceTimer);
debounceTimer = setTimeout(fn, delay);
}

var liveInputs = ['og-title','og-description','og-url','og-image','og-site-name','tw-title','tw-description','tw-image','tw-card','og-type'];
liveInputs.forEach(function(id) {
var elem = el(id);
if (elem) {
elem.addEventListener('input',  function() { debounce(updatePreviews, 120); });
elem.addEventListener('change', function() { debounce(updatePreviews, 120); });
}
});

/* ── Generate meta tags ── */
el('og-generate-btn').addEventListener('click', function() {
var title    = el('og-title').value.trim();
var desc     = el('og-description').value.trim();
var url      = el('og-url').value.trim();
var image    = el('og-image').value.trim();
var type     = el('og-type').value;
var siteName = el('og-site-name').value.trim();
var twCard   = el('tw-card').value;
var twTitle  = el('tw-title').value.trim();
var twDesc   = el('tw-description').value.trim();
var twImage  = el('tw-image').value.trim();

var lines = [];
lines.push('<!-- Open Graph / Facebook -->');
if (type)     lines.push('<meta property="og:type"        content="' + escapeHtml(type)     + '" />');
if (url)      lines.push('<meta property="og:url"         content="' + escapeHtml(url)      + '" />');
if (title)    lines.push('<meta property="og:title"       content="' + escapeHtml(title)    + '" />');
if (desc)     lines.push('<meta property="og:description" content="' + escapeHtml(desc)     + '" />');
if (image)    lines.push('<meta property="og:image"       content="' + escapeHtml(image)    + '" />');
if (siteName) lines.push('<meta property="og:site_name"   content="' + escapeHtml(siteName) + '" />');
lines.push('');
lines.push('<!-- Twitter Card -->');
lines.push('<meta name="twitter:card"        content="' + escapeHtml(twCard) + '" />');
if (twTitle || title)  lines.push('<meta name="twitter:title"       content="' + escapeHtml(twTitle || title)   + '" />');
if (twDesc  || desc)   lines.push('<meta name="twitter:description" content="' + escapeHtml(twDesc  || desc)    + '" />');
if (twImage || image)  lines.push('<meta name="twitter:image"       content="' + escapeHtml(twImage || image)   + '" />');

var code = lines.join('\n');
var codeSection = el('og-code-section');
el('og-code-output').textContent = code;
codeSection.style.display = 'block';
codeSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
});

/* ── Copy ── */
el('og-copy-btn').addEventListener('click', function() {
var text = el('og-code-output').textContent;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(showToast);
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
showToast();
}
});

function showToast() {
var t = el('og-toast');
t.style.display = 'block';
setTimeout(function() { t.style.display = 'none'; }, 2200);
}

/* ── Clear ── */
el('og-clear-btn').addEventListener('click', function() {
['og-title','og-description','og-url','og-image','og-site-name','tw-title','tw-description','tw-image'].forEach(function(id) {
var elem = el(id);
if (elem) elem.value = '';
});
el('og-type').value  = 'website';
el('tw-card').value  = 'summary_large_image';
['og-title-count','og-desc-count','tw-title-count','tw-desc-count'].forEach(function(id) {
var elem = el(id);
if (elem) { elem.textContent = '0 / ' + elem.textContent.split('/')[1].trim(); elem.className = 'og-char-info'; }
});
el('og-code-section').style.display = 'none';
updatePreviews();
});

/* ── Initial render ── */
updatePreviews();
})();
</script>

</div>

---

### Related Tools

> Generate meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)

> Create favicons → [Favicon Generator](/tools/favicon-generator/)

> Generate placeholder images → [Placeholder Image Generator](/tools/placeholder-image/)
