---
title: "Citation Generator - APA, MLA, Chicago"
description: "Free online citation generator. Create properly formatted citations in APA 7th, MLA 9th, Chicago, and Harvard styles. Supports books, journals, websites, and more."
slug: citation-generator
date: 2025-05-16
categories: ["Free Tools"]
ShowToc: false
cover:
  image: /images/covers/citation-generator.png
  alt: "Citation Generator - APA, MLA, Chicago, Harvard styles"
---

Generate properly formatted citations in APA, MLA, Chicago, and Harvard styles — for books, journal articles, websites, and conference papers. Paste them directly into your bibliography or export as text.

<div id="cg-app">

<style>
#cg-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1e293b;
}
#cg-app * { box-sizing: border-box; }
#cg-app h2 {
font-size: 1.15rem;
font-weight: 700;
margin: 0 0 12px;
color: #0f172a;
}
#cg-app .cg-row {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 14px;
}
#cg-app .cg-field {
display: flex;
flex-direction: column;
gap: 4px;
flex: 1;
min-width: 180px;
}
#cg-app .cg-field label {
font-size: 12px;
font-weight: 600;
color: #475569;
text-transform: uppercase;
letter-spacing: .03em;
}
#cg-app .cg-field input,
#cg-app .cg-field select {
padding: 8px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color .15s;
width: 100%;
}
#cg-app .cg-field input:focus,
#cg-app .cg-field select:focus {
border-color: #6366f1;
}
#cg-app .cg-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 20px 22px;
margin-bottom: 18px;
}
#cg-app .cg-author-row {
display: flex;
gap: 8px;
align-items: center;
margin-bottom: 8px;
}
#cg-app .cg-author-row input {
flex: 1;
padding: 8px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
color: #1e293b;
outline: none;
transition: border-color .15s;
}
#cg-app .cg-author-row input:focus { border-color: #6366f1; }
#cg-app .cg-btn {
padding: 8px 16px;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background .15s, transform .1s;
}
#cg-app .cg-btn:active { transform: scale(.97); }
#cg-app .cg-btn-primary {
background: #6366f1;
color: #fff;
}
#cg-app .cg-btn-primary:hover { background: #4f46e5; }
#cg-app .cg-btn-secondary {
background: #e2e8f0;
color: #334155;
}
#cg-app .cg-btn-secondary:hover { background: #cbd5e1; }
#cg-app .cg-btn-danger {
background: #fee2e2;
color: #dc2626;
padding: 8px 10px;
}
#cg-app .cg-btn-danger:hover { background: #fecaca; }
#cg-app .cg-btn-sm {
padding: 5px 11px;
font-size: 12px;
}
#cg-app .cg-preview-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 9px;
padding: 16px 18px;
margin-bottom: 10px;
}
#cg-app .cg-preview-label {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .06em;
color: #94a3b8;
margin-bottom: 6px;
}
#cg-app .cg-preview-text {
font-size: 14px;
line-height: 1.7;
color: #1e293b;
white-space: pre-wrap;
word-break: break-word;
}
#cg-app .cg-intext {
font-size: 13px;
color: #64748b;
margin-top: 8px;
padding: 9px 12px;
background: #f1f5f9;
border-radius: 7px;
}
#cg-app .cg-intext strong { color: #0f172a; }
#cg-app .cg-copy-row {
display: flex;
gap: 8px;
flex-wrap: wrap;
margin-top: 10px;
}
#cg-app .cg-toast {
display: inline-block;
font-size: 12px;
color: #16a34a;
font-weight: 600;
opacity: 0;
transition: opacity .3s;
margin-left: 6px;
align-self: center;
}
#cg-app .cg-toast.show { opacity: 1; }
#cg-app .cg-bib-list {
list-style: none;
padding: 0;
margin: 0 0 12px;
}
#cg-app .cg-bib-item {
display: flex;
align-items: flex-start;
gap: 8px;
padding: 10px 0;
border-bottom: 1px solid #e2e8f0;
font-size: 13px;
line-height: 1.6;
color: #1e293b;
word-break: break-word;
}
#cg-app .cg-bib-item:last-child { border-bottom: none; }
#cg-app .cg-bib-num {
font-size: 11px;
font-weight: 700;
color: #94a3b8;
min-width: 22px;
padding-top: 2px;
}
#cg-app .cg-bib-text { flex: 1; }
#cg-app .cg-tabs {
display: flex;
gap: 4px;
margin-bottom: 16px;
border-bottom: 2px solid #e2e8f0;
}
#cg-app .cg-tab {
padding: 8px 16px;
font-size: 13px;
font-weight: 600;
color: #64748b;
border: none;
background: none;
cursor: pointer;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
border-radius: 6px 6px 0 0;
transition: color .15s;
}
#cg-app .cg-tab.active {
color: #6366f1;
border-bottom-color: #6366f1;
}
#cg-app .cg-tab:hover:not(.active) { color: #334155; }
#cg-app .cg-section { margin-bottom: 6px; }
#cg-app .cg-divider {
border: none;
border-top: 1.5px solid #e2e8f0;
margin: 18px 0;
}
#cg-app .cg-empty {
color: #94a3b8;
font-size: 13px;
text-align: center;
padding: 18px 0;
}
@media (max-width: 600px) {
#cg-app .cg-row { flex-direction: column; }
#cg-app .cg-field { min-width: 100%; }
}
</style>

<div class="cg-card">
<div class="cg-tabs">
<button class="cg-tab active" data-tab="generator">Generator</button>
<button class="cg-tab" data-tab="bibliography">Bibliography</button>
</div>

<!-- GENERATOR TAB -->
<div id="cg-tab-generator">
<div class="cg-row">
<div class="cg-field">
<label>Source Type</label>
<select id="cg-source-type">
<option value="book">Book</option>
<option value="journal">Journal Article</option>
<option value="website">Website</option>
<option value="conference">Conference Paper</option>
</select>
</div>
<div class="cg-field">
<label>Citation Style</label>
<select id="cg-style">
<option value="apa7">APA 7th</option>
<option value="mla9">MLA 9th</option>
<option value="chicago17">Chicago 17th</option>
<option value="harvard">Harvard</option>
</select>
</div>
</div>

<!-- Authors -->
<div class="cg-section">
<label style="font-size:12px;font-weight:600;color:#475569;text-transform:uppercase;letter-spacing:.03em;">Author(s)</label>
<div id="cg-authors" style="margin-top:6px;"></div>
<button class="cg-btn cg-btn-secondary cg-btn-sm" id="cg-add-author" style="margin-top:6px;">+ Add Author</button>
</div>

<hr class="cg-divider">

<!-- Core fields -->
<div class="cg-row">
<div class="cg-field">
<label>Title</label>
<input type="text" id="cg-title" placeholder="Work title">
</div>
<div class="cg-field">
<label>Year</label>
<input type="text" id="cg-year" placeholder="2024" maxlength="4" style="max-width:120px;">
</div>
</div>

<div class="cg-row">
<div class="cg-field" id="cg-field-publisher">
<label>Publisher</label>
<input type="text" id="cg-publisher" placeholder="Publisher name">
</div>
<div class="cg-field" id="cg-field-place">
<label>Place of Publication</label>
<input type="text" id="cg-place" placeholder="New York">
</div>
</div>

<div class="cg-row" id="cg-row-journal">
<div class="cg-field">
<label>Journal Name</label>
<input type="text" id="cg-journal" placeholder="Nature, Science, ...">
</div>
<div class="cg-field" style="max-width:100px;">
<label>Volume</label>
<input type="text" id="cg-volume" placeholder="12">
</div>
<div class="cg-field" style="max-width:100px;">
<label>Issue</label>
<input type="text" id="cg-issue" placeholder="3">
</div>
<div class="cg-field" style="max-width:130px;">
<label>Pages</label>
<input type="text" id="cg-pages" placeholder="45–67">
</div>
</div>

<div class="cg-row" id="cg-row-conference">
<div class="cg-field">
<label>Conference Name</label>
<input type="text" id="cg-conference" placeholder="Proceedings of ...">
</div>
<div class="cg-field">
<label>Conference Location</label>
<input type="text" id="cg-conf-location" placeholder="San Francisco, CA">
</div>
</div>

<div class="cg-row">
<div class="cg-field">
<label>DOI</label>
<input type="text" id="cg-doi" placeholder="10.1000/xyz123">
</div>
<div class="cg-field" id="cg-field-url">
<label>URL</label>
<input type="text" id="cg-url" placeholder="https://example.com">
</div>
</div>

<div class="cg-row" id="cg-row-access">
<div class="cg-field">
<label>Access Date</label>
<input type="text" id="cg-access-date" placeholder="May 16, 2025">
</div>
<div class="cg-field">
<label>Website Name</label>
<input type="text" id="cg-site-name" placeholder="BBC News">
</div>
</div>

<hr class="cg-divider">

<!-- Preview -->
<h2>Citation Preview</h2>
<div class="cg-preview-box">
<div class="cg-preview-label">Reference List</div>
<div class="cg-preview-text" id="cg-preview-ref">Fill in the fields above to generate a citation.</div>
</div>
<div class="cg-intext" id="cg-preview-intext" style="display:none;">
<strong>In-text:</strong> <span id="cg-intext-text"></span>
</div>

<div class="cg-copy-row">
<button class="cg-btn cg-btn-primary" id="cg-copy-ref">Copy Reference</button>
<button class="cg-btn cg-btn-secondary" id="cg-copy-intext">Copy In-text</button>
<button class="cg-btn cg-btn-secondary" id="cg-add-to-bib">Add to Bibliography</button>
<span class="cg-toast" id="cg-toast"></span>
</div>
</div>

<!-- BIBLIOGRAPHY TAB -->
<div id="cg-tab-bibliography" style="display:none;">
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;flex-wrap:wrap;gap:8px;">
<h2 style="margin:0;">Bibliography</h2>
<div style="display:flex;gap:8px;flex-wrap:wrap;">
<button class="cg-btn cg-btn-secondary cg-btn-sm" id="cg-sort-alpha">Sort A–Z</button>
<button class="cg-btn cg-btn-secondary cg-btn-sm" id="cg-export-txt">Export as Text</button>
<button class="cg-btn cg-btn-danger cg-btn-sm" id="cg-clear-bib">Clear All</button>
</div>
</div>
<ul class="cg-bib-list" id="cg-bib-list">
<li class="cg-empty" id="cg-bib-empty">No citations yet. Generate one and click "Add to Bibliography".</li>
</ul>
</div>
</div>

<script>
(function() {
'use strict';

// ── State ──
var authors = [{ first: '', last: '' }];
var bibItems = [];

// ── DOM refs ──
var sourceTypeEl = document.getElementById('cg-source-type');
var styleEl = document.getElementById('cg-style');
var titleEl = document.getElementById('cg-title');
var yearEl = document.getElementById('cg-year');
var publisherEl = document.getElementById('cg-publisher');
var placeEl = document.getElementById('cg-place');
var journalEl = document.getElementById('cg-journal');
var volumeEl = document.getElementById('cg-volume');
var issueEl = document.getElementById('cg-issue');
var pagesEl = document.getElementById('cg-pages');
var doiEl = document.getElementById('cg-doi');
var urlEl = document.getElementById('cg-url');
var accessEl = document.getElementById('cg-access-date');
var siteNameEl = document.getElementById('cg-site-name');
var conferenceEl = document.getElementById('cg-conference');
var confLocEl = document.getElementById('cg-conf-location');
var authorsContainer = document.getElementById('cg-authors');
var previewRef = document.getElementById('cg-preview-ref');
var previewIntextEl = document.getElementById('cg-preview-intext');
var intextText = document.getElementById('cg-intext-text');
var toast = document.getElementById('cg-toast');
var bibList = document.getElementById('cg-bib-list');
var bibEmpty = document.getElementById('cg-bib-empty');

// ── Helpers ──
function v(el) { return el ? el.value.trim() : ''; }

function italic(text) { return '_' + text + '_'; }

function formatAuthorsAPA(auths) {
if (!auths.length) return '';
return auths.map(function(a) {
var last = a.last || a.first || 'Unknown';
var first = a.last ? a.first : '';
if (!first) return last;
var initials = first.split(/\s+/).map(function(n) { return n[0].toUpperCase() + '.'; }).join(' ');
return last + ', ' + initials;
}).join(', ');
}

function formatAuthorsMLAFull(auths) {
if (!auths.length) return '';
if (auths.length === 1) {
var a = auths[0];
return (a.last && a.first) ? a.last + ', ' + a.first : (a.last || a.first || 'Unknown');
}
var first = auths[0];
var firstStr = (first.last && first.first) ? first.last + ', ' + first.first : (first.last || first.first || 'Unknown');
var rest = auths.slice(1).map(function(a) { return (a.first ? a.first + ' ' : '') + (a.last || ''); });
if (auths.length === 2) return firstStr + ', and ' + rest[0];
return firstStr + ', et al.';
}

function formatAuthorsChicago(auths) {
if (!auths.length) return '';
if (auths.length === 1) {
var a = auths[0];
return (a.last && a.first) ? a.last + ', ' + a.first : (a.last || a.first || 'Unknown');
}
var first = auths[0];
var firstStr = (first.last && first.first) ? first.last + ', ' + first.first : (first.last || first.first || 'Unknown');
var rest = auths.slice(1).map(function(a) { return (a.first ? a.first + ' ' : '') + (a.last || ''); });
return firstStr + ', and ' + rest.join(', and ');
}

function formatAuthorsHarvard(auths) {
if (!auths.length) return '';
return auths.map(function(a, i) {
var last = a.last || a.first || 'Unknown';
var first = a.last ? a.first : '';
var initials = first ? first.split(/\s+/).map(function(n) { return n[0].toUpperCase() + '.'; }).join('') : '';
return last + (initials ? ', ' + initials : '');
}).join(', ');
}

function intextAPA(auths, year) {
var name = auths.length ? (auths[0].last || auths[0].first || 'Author') : 'Author';
var suffix = auths.length > 2 ? ' et al.' : (auths.length === 2 ? ' & ' + (auths[1].last || auths[1].first || '') : '');
return '(' + name + (auths.length === 2 ? suffix : (auths.length > 2 ? suffix : '')) + ', ' + (year || 'n.d.') + ')';
}

function intextMLA(auths) {
var name = auths.length ? (auths[0].last || auths[0].first || 'Author') : 'Author';
return '(' + name + ')';
}

function intextChicago(auths, year) {
var names = auths.slice(0, 3).map(function(a) { return a.last || a.first || 'Author'; });
if (auths.length > 3) names.push('et al.');
return '(' + names.join(', ') + ' ' + (year || 'n.d.') + ')';
}

function intextHarvard(auths, year) {
var name = auths.length ? (auths[0].last || auths[0].first || 'Author') : 'Author';
var suffix = auths.length > 2 ? ' et al.' : (auths.length === 2 ? ' and ' + (auths[1].last || auths[1].first || '') : '');
return '(' + name + suffix + ', ' + (year || 'n.d.') + ')';
}

// ── Citation Formatters ──
function buildAPA7(data) {
var a = formatAuthorsAPA(data.authors);
var yr = data.year ? '(' + data.year + ').' : '(n.d.).';
var doi = data.doi ? ' https://doi.org/' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') : '';
var url = !data.doi && data.url ? ' ' + data.url : '';

if (data.type === 'book') {
return (a ? a + ' ' : '') + yr + ' ' + italic(data.title || 'Untitled') + '.' + (data.publisher ? ' ' + data.publisher + '.' : '') + doi + url;
}
if (data.type === 'journal') {
var vol = data.volume ? ', ' + italic(data.volume) : '';
var iss = data.issue ? '(' + data.issue + ')' : '';
var pg = data.pages ? ', ' + data.pages : '';
return (a ? a + ' ' : '') + yr + ' ' + (data.title || 'Untitled') + '. ' + italic(data.journal || 'Journal') + vol + iss + pg + '.' + doi + url;
}
if (data.type === 'website') {
var site = data.siteName ? data.siteName + '. ' : '';
var acc = data.accessDate ? ' Retrieved ' + data.accessDate + ', from' : '';
return (a ? a + ' ' : '') + yr + ' ' + italic(data.title || 'Untitled') + '. ' + site + acc + (data.url ? ' ' + data.url : '');
}
if (data.type === 'conference') {
var pg2 = data.pages ? ', ' + data.pages : '';
return (a ? a + ' ' : '') + yr + ' ' + (data.title || 'Untitled') + '. In ' + italic(data.conference || 'Conference') + pg2 + '.' + doi + url;
}
return '';
}

function buildMLA9(data) {
var a = formatAuthorsMLAFull(data.authors);
if (data.type === 'book') {
return (a ? a + '. ' : '') + italic(data.title || 'Untitled') + '. ' + (data.publisher || '') + ', ' + (data.year || 'n.d.') + '.';
}
if (data.type === 'journal') {
var vol = data.volume ? 'vol. ' + data.volume + ', ' : '';
var iss = data.issue ? 'no. ' + data.issue + ', ' : '';
var pg = data.pages ? 'pp. ' + data.pages + ', ' : '';
var doi = data.doi ? 'https://doi.org/' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') + '.' : (data.url ? data.url + '.' : '');
return (a ? a + '. ' : '') + '"' + (data.title || 'Untitled') + '." ' + italic(data.journal || 'Journal') + ', ' + vol + iss + (data.year || 'n.d.') + ', ' + pg + doi;
}
if (data.type === 'website') {
var acc = data.accessDate ? ' Accessed ' + data.accessDate + '.' : '';
return (a ? a + '. ' : '') + '"' + (data.title || 'Untitled') + '." ' + (data.siteName ? italic(data.siteName) + ', ' : '') + (data.year || 'n.d.') + ', ' + (data.url || '') + '.' + acc;
}
if (data.type === 'conference') {
return (a ? a + '. ' : '') + '"' + (data.title || 'Untitled') + '." ' + italic(data.conference || 'Conference') + ', ' + (data.year || 'n.d.') + (data.pages ? ', pp. ' + data.pages : '') + '.';
}
return '';
}

function buildChicago17(data) {
var a = formatAuthorsChicago(data.authors);
if (data.type === 'book') {
return (a ? a + '. ' : '') + italic(data.title || 'Untitled') + '. ' + (data.place ? data.place + ': ' : '') + (data.publisher || '') + ', ' + (data.year || 'n.d.') + '.';
}
if (data.type === 'journal') {
var vol = data.volume ? data.volume : '';
var iss = data.issue ? ', no. ' + data.issue : '';
var yr = data.year ? ' (' + data.year + ')' : '';
var pg = data.pages ? ': ' + data.pages : '';
var doi = data.doi ? ' https://doi.org/' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') : (data.url ? ' ' + data.url : '');
return (a ? a + '. ' : '') + '"' + (data.title || 'Untitled') + '." ' + italic(data.journal || 'Journal') + ' ' + vol + iss + yr + pg + '.' + doi;
}
if (data.type === 'website') {
var acc = data.accessDate ? ' Accessed ' + data.accessDate + '.' : '';
return (a ? a + '. ' : '') + '"' + (data.title || 'Untitled') + '." ' + (data.siteName ? data.siteName + '. ' : '') + (data.year || 'n.d.') + '.' + (data.url ? ' ' + data.url + '.' : '') + acc;
}
if (data.type === 'conference') {
return (a ? a + '. ' : '') + '"' + (data.title || 'Untitled') + '." Paper presented at ' + (data.conference || 'Conference') + ', ' + (data.confLocation || '') + ', ' + (data.year || 'n.d.') + '.';
}
return '';
}

function buildHarvard(data) {
var a = formatAuthorsHarvard(data.authors);
var yr = data.year ? data.year : 'n.d.';
if (data.type === 'book') {
return (a ? a + ' ' : '') + '(' + yr + ') ' + italic(data.title || 'Untitled') + '. ' + (data.place ? data.place + ': ' : '') + (data.publisher || '') + '.';
}
if (data.type === 'journal') {
var vol = data.volume ? data.volume : '';
var iss = data.issue ? '(' + data.issue + ')' : '';
var pg = data.pages ? ', pp.' + data.pages : '';
var doi = data.doi ? ' doi:' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') : (data.url ? ' Available at: ' + data.url : '');
return (a ? a + ' ' : '') + '(' + yr + ') "' + (data.title || 'Untitled') + '", ' + italic(data.journal || 'Journal') + ', ' + vol + iss + pg + '.' + doi;
}
if (data.type === 'website') {
var acc = data.accessDate ? ' [Accessed: ' + data.accessDate + ']' : '';
return (a ? a + ' ' : '') + '(' + yr + ') ' + italic(data.title || 'Untitled') + '. ' + (data.siteName ? data.siteName + '.' : '') + (data.url ? ' Available at: ' + data.url + '.' : '') + acc;
}
if (data.type === 'conference') {
var pg2 = data.pages ? ', pp.' + data.pages : '';
return (a ? a + ' ' : '') + '(' + yr + ') "' + (data.title || 'Untitled') + '", ' + italic(data.conference || 'Conference') + pg2 + '.';
}
return '';
}

function getCitationData() {
return {
type: v(sourceTypeEl),
authors: authors.filter(function(a) { return a.first || a.last; }),
title: v(titleEl),
year: v(yearEl),
publisher: v(publisherEl),
place: v(placeEl),
journal: v(journalEl),
volume: v(volumeEl),
issue: v(issueEl),
pages: v(pagesEl),
doi: v(doiEl),
url: v(urlEl),
accessDate: v(accessEl),
siteName: v(siteNameEl),
conference: v(conferenceEl),
confLocation: v(confLocEl)
};
}

function buildCitation(data) {
var style = v(styleEl);
if (style === 'apa7') return buildAPA7(data);
if (style === 'mla9') return buildMLA9(data);
if (style === 'chicago17') return buildChicago17(data);
if (style === 'harvard') return buildHarvard(data);
return '';
}

function buildIntext(data) {
var style = v(styleEl);
var auths = data.authors;
if (style === 'apa7') return intextAPA(auths, data.year);
if (style === 'mla9') return intextMLA(auths);
if (style === 'chicago17') return intextChicago(auths, data.year);
if (style === 'harvard') return intextHarvard(auths, data.year);
return '';
}

// Render italic markers as actual italics in the display
function renderForDisplay(text) {
return text.replace(/_([^_]+)_/g, '<em>$1</em>');
}

function renderForCopy(text) {
return text.replace(/_([^_]+)_/g, '$1');
}

// ── Update visibility ──
function updateFieldVisibility() {
var type = v(sourceTypeEl);
var isJournal = type === 'journal';
var isWebsite = type === 'website';
var isConference = type === 'conference';
var isBook = type === 'book';

document.getElementById('cg-row-journal').style.display = (isJournal || isConference) ? 'flex' : 'none';
if (isConference) {
journalEl.closest('.cg-field').style.display = 'none';
} else {
journalEl.closest('.cg-field').style.display = '';
}
document.getElementById('cg-row-conference').style.display = isConference ? 'flex' : 'none';
document.getElementById('cg-row-access').style.display = isWebsite ? 'flex' : 'none';
document.getElementById('cg-field-url').style.display = isWebsite ? '' : 'flex';
document.getElementById('cg-field-publisher').style.display = (isBook || isConference || isJournal) ? '' : 'none';
document.getElementById('cg-field-place').style.display = (isBook) ? '' : 'none';
}

// ── Render authors ──
function renderAuthors() {
authorsContainer.innerHTML = '';
authors.forEach(function(a, i) {
var row = document.createElement('div');
row.className = 'cg-author-row';
row.innerHTML =
'<input type="text" placeholder="Last name" value="' + escAttr(a.last) + '" data-i="' + i + '" data-field="last">' +
'<input type="text" placeholder="First name / Initials" value="' + escAttr(a.first) + '" data-i="' + i + '" data-field="first">' +
(authors.length > 1 ? '<button class="cg-btn cg-btn-danger cg-btn-sm cg-remove-author" data-i="' + i + '">✕</button>' : '');
authorsContainer.appendChild(row);
});
authorsContainer.querySelectorAll('input').forEach(function(inp) {
inp.addEventListener('input', function() {
authors[+this.dataset.i][this.dataset.field] = this.value;
updatePreview();
});
});
authorsContainer.querySelectorAll('.cg-remove-author').forEach(function(btn) {
btn.addEventListener('click', function() {
authors.splice(+this.dataset.i, 1);
renderAuthors();
updatePreview();
});
});
}

function escAttr(s) { return (s || '').replace(/"/g, '&quot;'); }

// ── Preview ──
function updatePreview() {
var data = getCitationData();
var ref = buildCitation(data);
var intext = buildIntext(data);
if (ref) {
previewRef.innerHTML = renderForDisplay(ref);
previewIntextEl.style.display = '';
intextText.textContent = renderForCopy(intext);
} else {
previewRef.textContent = 'Fill in the fields above to generate a citation.';
previewIntextEl.style.display = 'none';
}
}

// ── Toast ──
var toastTimer;
function showToast(msg) {
toast.textContent = msg;
toast.classList.add('show');
clearTimeout(toastTimer);
toastTimer = setTimeout(function() { toast.classList.remove('show'); }, 2000);
}

// ── Copy ──
function copyText(text) {
if (navigator.clipboard) {
navigator.clipboard.writeText(text).catch(function() { fallbackCopy(text); });
} else { fallbackCopy(text); }
}
function fallbackCopy(text) {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
}

// ── Bibliography ──
function renderBib() {
var items = bibItems.slice();
var html = '';
if (!items.length) {
bibList.innerHTML = '<li class="cg-empty" id="cg-bib-empty">No citations yet. Generate one and click "Add to Bibliography".</li>';
return;
}
items.forEach(function(item, i) {
html += '<li class="cg-bib-item"><span class="cg-bib-num">' + (i+1) + '.</span><span class="cg-bib-text">' + renderForDisplay(item) + '</span>' +
'<button class="cg-btn cg-btn-danger cg-btn-sm cg-remove-bib" data-i="' + i + '" style="flex-shrink:0;">✕</button></li>';
});
bibList.innerHTML = html;
bibList.querySelectorAll('.cg-remove-bib').forEach(function(btn) {
btn.addEventListener('click', function() {
bibItems.splice(+this.dataset.i, 1);
renderBib();
});
});
}

// ── Tabs ──
document.querySelectorAll('#cg-app .cg-tab').forEach(function(tab) {
tab.addEventListener('click', function() {
document.querySelectorAll('#cg-app .cg-tab').forEach(function(t) { t.classList.remove('active'); });
this.classList.add('active');
var name = this.dataset.tab;
document.getElementById('cg-tab-generator').style.display = name === 'generator' ? '' : 'none';
document.getElementById('cg-tab-bibliography').style.display = name === 'bibliography' ? '' : 'none';
});
});

// ── Event listeners ──
sourceTypeEl.addEventListener('change', function() { updateFieldVisibility(); updatePreview(); });
styleEl.addEventListener('change', updatePreview);
[titleEl, yearEl, publisherEl, placeEl, journalEl, volumeEl, issueEl, pagesEl, doiEl, urlEl, accessEl, siteNameEl, conferenceEl, confLocEl].forEach(function(el) {
if (el) el.addEventListener('input', updatePreview);
});

document.getElementById('cg-add-author').addEventListener('click', function() {
authors.push({ first: '', last: '' });
renderAuthors();
});

document.getElementById('cg-copy-ref').addEventListener('click', function() {
var data = getCitationData();
var ref = renderForCopy(buildCitation(data));
if (!ref) { showToast('Nothing to copy'); return; }
copyText(ref);
showToast('Copied!');
});

document.getElementById('cg-copy-intext').addEventListener('click', function() {
var data = getCitationData();
var it = buildIntext(data);
if (!it) { showToast('Nothing to copy'); return; }
copyText(it);
showToast('In-text copied!');
});

document.getElementById('cg-add-to-bib').addEventListener('click', function() {
var data = getCitationData();
var ref = buildCitation(data);
if (!ref) { showToast('Generate a citation first'); return; }
bibItems.push(ref);
renderBib();
showToast('Added to bibliography!');
});

document.getElementById('cg-sort-alpha').addEventListener('click', function() {
bibItems.sort(function(a, b) { return renderForCopy(a).localeCompare(renderForCopy(b)); });
renderBib();
showToast('Sorted!');
});

document.getElementById('cg-export-txt').addEventListener('click', function() {
if (!bibItems.length) { showToast('Bibliography is empty'); return; }
var text = bibItems.map(function(item, i) { return (i+1) + '. ' + renderForCopy(item); }).join('\n\n');
var blob = new Blob([text], { type: 'text/plain' });
var a = document.createElement('a');
a.href = URL.createObjectURL(blob);
a.download = 'bibliography.txt';
a.click();
URL.revokeObjectURL(a.href);
});

document.getElementById('cg-clear-bib').addEventListener('click', function() {
if (bibItems.length && confirm('Clear all citations from bibliography?')) {
bibItems = [];
renderBib();
}
});

// ── Init ──
renderAuthors();
updateFieldVisibility();
updatePreview();
})();
</script>

</div>

---

**Related tools:**

- Count words → [Word Counter](/tools/word-counter/)
- Estimate reading time → [Reading Time Calculator](/tools/reading-time-calculator/)
