---
title: "Resume Builder - Free CV Creator"
description: "Free online resume builder. Create a professional CV with customizable sections. Choose from clean templates, export as printable HTML. No sign-up required."
slug: resume-builder
date: 2025-05-16
categories: ["Free Tools"]
ShowToc: false
cover:
  image: /images/covers/resume-builder.png
  alt: "Resume Builder - Free CV Creator"
---

Build a professional resume in minutes — no account needed. Fill in your details, pick a template, and print or save as PDF.

<div id="rb-app">

<style>
#rb-app * { box-sizing: border-box; }
#rb-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
color: #1e293b;
max-width: 1200px;
margin: 0 auto;
}
#rb-app h2 { font-size: 1.3rem; margin: 0 0 16px; color: #0f172a; }
#rb-app h3 { font-size: 1rem; margin: 0 0 10px; color: #334155; }

/* Layout */
#rb-layout {
display: flex;
gap: 24px;
align-items: flex-start;
}
#rb-editor {
flex: 0 0 420px;
min-width: 0;
}
#rb-preview-wrap {
flex: 1;
min-width: 0;
position: sticky;
top: 20px;
}
@media (max-width: 900px) {
#rb-layout { flex-direction: column; }
#rb-editor { flex: none; width: 100%; }
#rb-preview-wrap { position: static; width: 100%; }
}

/* Controls bar */
#rb-controls {
display: flex;
gap: 10px;
flex-wrap: wrap;
align-items: center;
margin-bottom: 18px;
padding: 12px 14px;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
}
#rb-controls label { font-size: 13px; color: #64748b; font-weight: 500; }
#rb-controls select, #rb-controls input[type=color] {
border: 1px solid #cbd5e1;
border-radius: 6px;
padding: 4px 8px;
font-size: 13px;
background: #fff;
cursor: pointer;
}
#rb-controls input[type=color] {
width: 38px; height: 30px; padding: 2px 4px;
}
#rb-btn-print, #rb-btn-save, #rb-btn-load, #rb-btn-clear {
padding: 6px 14px;
border-radius: 7px;
border: none;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: opacity .15s;
}
#rb-btn-print { background: #2563eb; color: #fff; }
#rb-btn-save  { background: #059669; color: #fff; }
#rb-btn-load  { background: #7c3aed; color: #fff; }
#rb-btn-clear { background: #ef4444; color: #fff; }
#rb-btn-print:hover, #rb-btn-save:hover, #rb-btn-load:hover, #rb-btn-clear:hover { opacity: .85; }

/* Sections list */
#rb-sections-list { display: flex; flex-direction: column; gap: 12px; }
.rb-section-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
}
.rb-section-header {
display: flex;
align-items: center;
gap: 8px;
padding: 10px 14px;
background: #f1f5f9;
cursor: pointer;
user-select: none;
}
.rb-section-header .rb-sec-title { font-weight: 600; font-size: 14px; flex: 1; }
.rb-section-header .rb-sec-toggle { font-size: 11px; color: #94a3b8; }
.rb-move-btn {
background: none; border: 1px solid #cbd5e1; border-radius: 5px;
width: 24px; height: 24px; font-size: 13px; cursor: pointer; color: #64748b;
display: flex; align-items: center; justify-content: center; padding: 0;
}
.rb-move-btn:hover { background: #e2e8f0; }
.rb-section-body { padding: 14px; display: block; }
.rb-section-body.hidden { display: none; }

/* Form fields */
.rb-field { margin-bottom: 10px; }
.rb-field label { display: block; font-size: 12px; font-weight: 600; color: #64748b; margin-bottom: 4px; }
.rb-field input, .rb-field textarea {
width: 100%; padding: 7px 10px; border: 1px solid #cbd5e1; border-radius: 7px;
font-size: 13px; font-family: inherit; color: #1e293b; background: #fff;
transition: border-color .15s;
}
.rb-field input:focus, .rb-field textarea:focus {
outline: none; border-color: #2563eb; box-shadow: 0 0 0 3px rgba(37,99,235,.1);
}
.rb-field textarea { resize: vertical; min-height: 70px; }
.rb-field-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }

/* Entry cards */
.rb-entry {
border: 1px solid #e2e8f0; border-radius: 8px; padding: 12px;
margin-bottom: 10px; background: #fafafa; position: relative;
}
.rb-entry-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
.rb-entry-label { font-size: 12px; font-weight: 700; color: #475569; }
.rb-remove-entry {
background: none; border: 1px solid #fca5a5; color: #ef4444;
border-radius: 5px; font-size: 11px; padding: 2px 8px; cursor: pointer;
}
.rb-remove-entry:hover { background: #fef2f2; }
.rb-add-btn {
width: 100%; padding: 8px; border: 2px dashed #cbd5e1; background: #f8fafc;
border-radius: 7px; font-size: 13px; color: #64748b; cursor: pointer; margin-top: 4px;
}
.rb-add-btn:hover { border-color: #2563eb; color: #2563eb; background: #eff6ff; }

/* Skills / Languages tags */
.rb-tags-input { display: flex; gap: 6px; }
.rb-tags-input input { flex: 1; }
.rb-tags-input button {
padding: 7px 12px; background: #2563eb; color: #fff; border: none;
border-radius: 7px; font-size: 13px; cursor: pointer; white-space: nowrap;
}
.rb-tag {
display: inline-flex; align-items: center; gap: 4px;
padding: 3px 10px; background: #dbeafe; color: #1d4ed8;
border-radius: 20px; font-size: 12px; margin: 4px 4px 0 0;
}
.rb-tag button {
background: none; border: none; cursor: pointer; color: #1d4ed8;
font-size: 13px; padding: 0; line-height: 1;
}
#rb-tags-wrap, #rb-lang-tags-wrap { margin-top: 6px; min-height: 28px; }

/* Preview */
#rb-preview-wrap h2 { font-size: 1.1rem; }
#rb-preview-box {
border: 1px solid #e2e8f0; border-radius: 10px; overflow: auto;
background: #fff; min-height: 500px;
}
#rb-preview-inner {
padding: 32px 36px;
font-family: inherit;
}

/* --- Template: Classic --- */
.rb-tpl-classic #rb-preview-inner { font-family: Georgia, 'Times New Roman', serif; }
.rb-tpl-classic .rbp-name { font-size: 26px; font-weight: 700; border-bottom: 2px solid var(--rb-accent, #2563eb); padding-bottom: 6px; margin-bottom: 6px; }
.rb-tpl-classic .rbp-contact { font-size: 12px; color: #64748b; margin-bottom: 20px; }
.rb-tpl-classic .rbp-section-title { font-size: 14px; font-weight: 700; text-transform: uppercase; letter-spacing: .08em; color: var(--rb-accent, #2563eb); border-bottom: 1px solid #e2e8f0; padding-bottom: 4px; margin: 18px 0 10px; }
.rb-tpl-classic .rbp-entry-title { font-weight: 700; font-size: 14px; }
.rb-tpl-classic .rbp-entry-sub { font-size: 12px; color: #64748b; }
.rb-tpl-classic .rbp-entry-date { font-size: 11px; color: #94a3b8; }
.rb-tpl-classic .rbp-entry-desc { font-size: 13px; margin-top: 4px; white-space: pre-wrap; }
.rb-tpl-classic .rbp-summary { font-size: 13px; white-space: pre-wrap; }
.rb-tpl-classic .rbp-tag { display: inline-block; padding: 2px 10px; border: 1px solid var(--rb-accent, #2563eb); color: var(--rb-accent, #2563eb); border-radius: 3px; font-size: 12px; margin: 2px 3px 0 0; }

/* --- Template: Modern --- */
.rb-tpl-modern #rb-preview-inner { font-family: 'Segoe UI', Roboto, sans-serif; display: grid; grid-template-columns: 200px 1fr; gap: 0; padding: 0; }
.rb-tpl-modern .rbp-sidebar { background: var(--rb-accent, #2563eb); color: #fff; padding: 28px 20px; }
.rb-tpl-modern .rbp-main { padding: 28px 28px; }
.rb-tpl-modern .rbp-name { font-size: 22px; font-weight: 700; color: #fff; margin-bottom: 4px; }
.rb-tpl-modern .rbp-contact { font-size: 11px; color: rgba(255,255,255,.85); line-height: 1.8; margin-bottom: 20px; }
.rb-tpl-modern .rbp-sidebar .rbp-section-title { font-size: 12px; font-weight: 700; text-transform: uppercase; letter-spacing: .1em; color: rgba(255,255,255,.7); border-bottom: 1px solid rgba(255,255,255,.25); padding-bottom: 4px; margin: 16px 0 8px; }
.rb-tpl-modern .rbp-main .rbp-section-title { font-size: 13px; font-weight: 700; text-transform: uppercase; letter-spacing: .08em; color: var(--rb-accent, #2563eb); border-bottom: 2px solid var(--rb-accent, #2563eb); padding-bottom: 3px; margin: 18px 0 10px; }
.rb-tpl-modern .rbp-entry-title { font-weight: 700; font-size: 14px; }
.rb-tpl-modern .rbp-entry-sub { font-size: 12px; color: #64748b; }
.rb-tpl-modern .rbp-entry-date { font-size: 11px; color: #94a3b8; }
.rb-tpl-modern .rbp-entry-desc { font-size: 13px; margin-top: 4px; white-space: pre-wrap; }
.rb-tpl-modern .rbp-summary { font-size: 13px; white-space: pre-wrap; }
.rb-tpl-modern .rbp-tag { display: inline-block; padding: 2px 8px; background: rgba(255,255,255,.2); color: #fff; border-radius: 3px; font-size: 11px; margin: 2px 2px 0 0; }
.rb-tpl-modern .rbp-main .rbp-tag { background: #eff6ff; color: var(--rb-accent, #2563eb); }
@media (max-width: 600px) {
.rb-tpl-modern #rb-preview-inner { grid-template-columns: 1fr; }
.rb-tpl-modern .rbp-sidebar { padding: 20px; }
}

/* --- Template: Minimal --- */
.rb-tpl-minimal #rb-preview-inner { font-family: 'Helvetica Neue', Arial, sans-serif; color: #1e293b; }
.rb-tpl-minimal .rbp-name { font-size: 28px; font-weight: 300; letter-spacing: -.02em; color: #0f172a; }
.rb-tpl-minimal .rbp-contact { font-size: 12px; color: #94a3b8; margin-bottom: 24px; }
.rb-tpl-minimal .rbp-section-title { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: .15em; color: var(--rb-accent, #2563eb); margin: 22px 0 10px; }
.rb-tpl-minimal .rbp-entry-title { font-weight: 600; font-size: 14px; }
.rb-tpl-minimal .rbp-entry-sub { font-size: 12px; color: #64748b; }
.rb-tpl-minimal .rbp-entry-date { font-size: 11px; color: #94a3b8; }
.rb-tpl-minimal .rbp-entry-desc { font-size: 13px; margin-top: 4px; color: #475569; white-space: pre-wrap; }
.rb-tpl-minimal .rbp-summary { font-size: 13px; color: #475569; white-space: pre-wrap; }
.rb-tpl-minimal .rbp-tag { display: inline-block; padding: 2px 8px; background: #f1f5f9; color: #475569; border-radius: 4px; font-size: 12px; margin: 2px 3px 0 0; }
.rb-tpl-minimal .rbp-entry { border-left: 2px solid var(--rb-accent, #2563eb); padding-left: 12px; margin-bottom: 12px; }

/* Print */
@media print {
#rb-app #rb-controls, #rb-app #rb-editor, #rb-app #rb-preview-wrap > h2 { display: none !important; }
#rb-app #rb-layout { display: block; }
#rb-app #rb-preview-wrap { position: static; }
#rb-app #rb-preview-box { border: none; }
body > * { display: none; }
#rb-app { display: block !important; max-width: 100%; }
}
</style>

<!-- Controls -->
<div id="rb-controls">
<label>Template:
<select id="rb-tpl-select">
<option value="classic">Classic</option>
<option value="modern">Modern</option>
<option value="minimal">Minimal</option>
</select>
</label>
<label>Color:
<input type="color" id="rb-color-pick" value="#2563eb">
</label>
<button id="rb-btn-save">Save</button>
<button id="rb-btn-load">Load</button>
<button id="rb-btn-clear">Clear</button>
<button id="rb-btn-print">Print / Save PDF</button>
</div>

<div id="rb-layout">

<!-- Editor -->
<div id="rb-editor">
<div id="rb-sections-list">

<!-- Personal Info -->
<div class="rb-section-card" data-section="personal">
<div class="rb-section-header">
<button class="rb-move-btn rb-move-up" title="Move up">↑</button>
<button class="rb-move-btn rb-move-dn" title="Move down">↓</button>
<span class="rb-sec-title">Personal Info</span>
<span class="rb-sec-toggle">▾</span>
</div>
<div class="rb-section-body">
<div class="rb-field"><label>Full Name</label><input type="text" id="rb-name" placeholder="Jane Smith"></div>
<div class="rb-field-row">
<div class="rb-field"><label>Email</label><input type="email" id="rb-email" placeholder="jane@example.com"></div>
<div class="rb-field"><label>Phone</label><input type="tel" id="rb-phone" placeholder="+1 555-0100"></div>
</div>
<div class="rb-field-row">
<div class="rb-field"><label>Location</label><input type="text" id="rb-location" placeholder="New York, NY"></div>
<div class="rb-field"><label>LinkedIn</label><input type="text" id="rb-linkedin" placeholder="linkedin.com/in/jane"></div>
</div>
<div class="rb-field"><label>Website / Portfolio</label><input type="text" id="rb-website" placeholder="janesmith.com"></div>
</div>
</div>

<!-- Summary -->
<div class="rb-section-card" data-section="summary">
<div class="rb-section-header">
<button class="rb-move-btn rb-move-up" title="Move up">↑</button>
<button class="rb-move-btn rb-move-dn" title="Move down">↓</button>
<span class="rb-sec-title">Professional Summary</span>
<span class="rb-sec-toggle">▾</span>
</div>
<div class="rb-section-body">
<div class="rb-field">
<textarea id="rb-summary" placeholder="Brief overview of your professional background and goals…"></textarea>
</div>
</div>
</div>

<!-- Work Experience -->
<div class="rb-section-card" data-section="experience">
<div class="rb-section-header">
<button class="rb-move-btn rb-move-up" title="Move up">↑</button>
<button class="rb-move-btn rb-move-dn" title="Move down">↓</button>
<span class="rb-sec-title">Work Experience</span>
<span class="rb-sec-toggle">▾</span>
</div>
<div class="rb-section-body">
<div id="rb-exp-list"></div>
<button class="rb-add-btn" id="rb-add-exp">+ Add Experience</button>
</div>
</div>

<!-- Education -->
<div class="rb-section-card" data-section="education">
<div class="rb-section-header">
<button class="rb-move-btn rb-move-up" title="Move up">↑</button>
<button class="rb-move-btn rb-move-dn" title="Move down">↓</button>
<span class="rb-sec-title">Education</span>
<span class="rb-sec-toggle">▾</span>
</div>
<div class="rb-section-body">
<div id="rb-edu-list"></div>
<button class="rb-add-btn" id="rb-add-edu">+ Add Education</button>
</div>
</div>

<!-- Skills -->
<div class="rb-section-card" data-section="skills">
<div class="rb-section-header">
<button class="rb-move-btn rb-move-up" title="Move up">↑</button>
<button class="rb-move-btn rb-move-dn" title="Move down">↓</button>
<span class="rb-sec-title">Skills</span>
<span class="rb-sec-toggle">▾</span>
</div>
<div class="rb-section-body">
<div class="rb-tags-input">
<input type="text" id="rb-skill-input" placeholder="e.g. JavaScript">
<button id="rb-skill-add">Add</button>
</div>
<div id="rb-tags-wrap"></div>
</div>
</div>

<!-- Languages -->
<div class="rb-section-card" data-section="languages">
<div class="rb-section-header">
<button class="rb-move-btn rb-move-up" title="Move up">↑</button>
<button class="rb-move-btn rb-move-dn" title="Move down">↓</button>
<span class="rb-sec-title">Languages</span>
<span class="rb-sec-toggle">▾</span>
</div>
<div class="rb-section-body">
<div class="rb-tags-input">
<input type="text" id="rb-lang-input" placeholder="e.g. English (Native)">
<button id="rb-lang-add">Add</button>
</div>
<div id="rb-lang-tags-wrap"></div>
</div>
</div>

</div>
</div>

<!-- Preview -->
<div id="rb-preview-wrap">
<h2>Live Preview</h2>
<div id="rb-preview-box">
<div id="rb-preview-inner"></div>
</div>
</div>

</div>

<script>
(function() {
'use strict';

// State
var state = {
name: '', email: '', phone: '', location: '', linkedin: '', website: '',
summary: '',
experience: [],
education: [],
skills: [],
languages: [],
template: 'classic',
color: '#2563eb',
sectionOrder: ['personal','summary','experience','education','skills','languages']
};

var expId = 0, eduId = 0;

// Helpers
function qs(sel, ctx) { return (ctx || document).querySelector(sel); }
function qsa(sel, ctx) { return (ctx || document).querySelectorAll(sel); }
function byId(id) { return document.getElementById(id); }
function esc(s) {
return String(s || '').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

// Collapse / expand sections
qsa('#rb-sections-list .rb-section-header').forEach(function(hdr) {
hdr.addEventListener('click', function(e) {
if (e.target.classList.contains('rb-move-btn')) return;
var body = hdr.nextElementSibling;
var tog = qs('.rb-sec-toggle', hdr);
body.classList.toggle('hidden');
tog.textContent = body.classList.contains('hidden') ? '▸' : '▾';
});
});

// Move up/down
function rebuildSectionOrder() {
state.sectionOrder = Array.from(qsa('#rb-sections-list .rb-section-card')).map(function(c) {
return c.getAttribute('data-section');
});
}
byId('rb-sections-list').addEventListener('click', function(e) {
var btn = e.target.closest('.rb-move-btn');
if (!btn) return;
var card = btn.closest('.rb-section-card');
var list = byId('rb-sections-list');
if (btn.classList.contains('rb-move-up')) {
var prev = card.previousElementSibling;
if (prev) list.insertBefore(card, prev);
} else {
var next = card.nextElementSibling;
if (next) list.insertBefore(next, card);
}
rebuildSectionOrder();
render();
});

// Experience entries
function addExp(data) {
data = data || {};
var id = ++expId;
state.experience.push({ id: id, title: data.title||'', company: data.company||'', start: data.start||'', end: data.end||'', desc: data.desc||'' });
renderExpList();
}
function removeExp(id) {
state.experience = state.experience.filter(function(e) { return e.id !== id; });
renderExpList();
render();
}
function renderExpList() {
var list = byId('rb-exp-list');
list.innerHTML = '';
state.experience.forEach(function(e) {
var div = document.createElement('div');
div.className = 'rb-entry';
div.innerHTML = '<div class="rb-entry-header"><span class="rb-entry-label">Experience #' + e.id + '</span><button class="rb-remove-entry" data-id="' + e.id + '">Remove</button></div>' +
'<div class="rb-field"><label>Job Title</label><input type="text" class="rb-exp-f" data-id="' + e.id + '" data-f="title" value="' + esc(e.title) + '" placeholder="Software Engineer"></div>' +
'<div class="rb-field"><label>Company</label><input type="text" class="rb-exp-f" data-id="' + e.id + '" data-f="company" value="' + esc(e.company) + '" placeholder="Acme Corp"></div>' +
'<div class="rb-field-row">' +
'<div class="rb-field"><label>Start</label><input type="text" class="rb-exp-f" data-id="' + e.id + '" data-f="start" value="' + esc(e.start) + '" placeholder="Jan 2022"></div>' +
'<div class="rb-field"><label>End</label><input type="text" class="rb-exp-f" data-id="' + e.id + '" data-f="end" value="' + esc(e.end) + '" placeholder="Present"></div>' +
'</div>' +
'<div class="rb-field"><label>Description</label><textarea class="rb-exp-f" data-id="' + e.id + '" data-f="desc" placeholder="Key responsibilities and achievements…">' + esc(e.desc) + '</textarea></div>';
list.appendChild(div);
});
// Events
qsa('.rb-remove-entry', list).forEach(function(btn) {
btn.addEventListener('click', function() { removeExp(parseInt(btn.getAttribute('data-id'))); });
});
qsa('.rb-exp-f', list).forEach(function(inp) {
inp.addEventListener('input', function() {
var id = parseInt(inp.getAttribute('data-id'));
var f = inp.getAttribute('data-f');
var entry = state.experience.find(function(e) { return e.id === id; });
if (entry) entry[f] = inp.value;
render();
});
});
}
byId('rb-add-exp').addEventListener('click', function() { addExp(); render(); });

// Education entries
function addEdu(data) {
data = data || {};
var id = ++eduId;
state.education.push({ id: id, degree: data.degree||'', school: data.school||'', start: data.start||'', end: data.end||'', desc: data.desc||'' });
renderEduList();
}
function removeEdu(id) {
state.education = state.education.filter(function(e) { return e.id !== id; });
renderEduList();
render();
}
function renderEduList() {
var list = byId('rb-edu-list');
list.innerHTML = '';
state.education.forEach(function(e) {
var div = document.createElement('div');
div.className = 'rb-entry';
div.innerHTML = '<div class="rb-entry-header"><span class="rb-entry-label">Education #' + e.id + '</span><button class="rb-remove-entry" data-id="' + e.id + '">Remove</button></div>' +
'<div class="rb-field"><label>Degree / Qualification</label><input type="text" class="rb-edu-f" data-id="' + e.id + '" data-f="degree" value="' + esc(e.degree) + '" placeholder="B.Sc. Computer Science"></div>' +
'<div class="rb-field"><label>School / University</label><input type="text" class="rb-edu-f" data-id="' + e.id + '" data-f="school" value="' + esc(e.school) + '" placeholder="State University"></div>' +
'<div class="rb-field-row">' +
'<div class="rb-field"><label>Start</label><input type="text" class="rb-edu-f" data-id="' + e.id + '" data-f="start" value="' + esc(e.start) + '" placeholder="Sep 2018"></div>' +
'<div class="rb-field"><label>End</label><input type="text" class="rb-edu-f" data-id="' + e.id + '" data-f="end" value="' + esc(e.end) + '" placeholder="Jun 2022"></div>' +
'</div>' +
'<div class="rb-field"><label>Notes</label><textarea class="rb-edu-f" data-id="' + e.id + '" data-f="desc" placeholder="Thesis, honours, GPA…">' + esc(e.desc) + '</textarea></div>';
list.appendChild(div);
});
qsa('.rb-remove-entry', list).forEach(function(btn) {
btn.addEventListener('click', function() { removeEdu(parseInt(btn.getAttribute('data-id'))); });
});
qsa('.rb-edu-f', list).forEach(function(inp) {
inp.addEventListener('input', function() {
var id = parseInt(inp.getAttribute('data-id'));
var f = inp.getAttribute('data-f');
var entry = state.education.find(function(e) { return e.id === id; });
if (entry) entry[f] = inp.value;
render();
});
});
}
byId('rb-add-edu').addEventListener('click', function() { addEdu(); render(); });

// Skills tags
function renderTags() {
var wrap = byId('rb-tags-wrap');
wrap.innerHTML = '';
state.skills.forEach(function(s, i) {
var span = document.createElement('span');
span.className = 'rb-tag';
span.innerHTML = esc(s) + '<button data-i="' + i + '" title="Remove">×</button>';
wrap.appendChild(span);
});
qsa('.rb-tag button', wrap).forEach(function(btn) {
btn.addEventListener('click', function() {
state.skills.splice(parseInt(btn.getAttribute('data-i')), 1);
renderTags(); render();
});
});
}
function addSkill() {
var inp = byId('rb-skill-input');
var v = inp.value.trim();
if (v && !state.skills.includes(v)) { state.skills.push(v); renderTags(); render(); }
inp.value = '';
inp.focus();
}
byId('rb-skill-add').addEventListener('click', addSkill);
byId('rb-skill-input').addEventListener('keydown', function(e) { if (e.key === 'Enter') { e.preventDefault(); addSkill(); } });

// Languages tags
function renderLangTags() {
var wrap = byId('rb-lang-tags-wrap');
wrap.innerHTML = '';
state.languages.forEach(function(s, i) {
var span = document.createElement('span');
span.className = 'rb-tag';
span.innerHTML = esc(s) + '<button data-i="' + i + '" title="Remove">×</button>';
wrap.appendChild(span);
});
qsa('.rb-tag button', wrap).forEach(function(btn) {
btn.addEventListener('click', function() {
state.languages.splice(parseInt(btn.getAttribute('data-i')), 1);
renderLangTags(); render();
});
});
}
function addLang() {
var inp = byId('rb-lang-input');
var v = inp.value.trim();
if (v && !state.languages.includes(v)) { state.languages.push(v); renderLangTags(); render(); }
inp.value = '';
inp.focus();
}
byId('rb-lang-add').addEventListener('click', addLang);
byId('rb-lang-input').addEventListener('keydown', function(e) { if (e.key === 'Enter') { e.preventDefault(); addLang(); } });

// Personal fields
['name','email','phone','location','linkedin','website'].forEach(function(f) {
var el = byId('rb-' + f);
if (el) el.addEventListener('input', function() { state[f] = el.value; render(); });
});
byId('rb-summary').addEventListener('input', function() { state.summary = this.value; render(); });

// Template / color
byId('rb-tpl-select').addEventListener('change', function() { state.template = this.value; render(); });
byId('rb-color-pick').addEventListener('input', function() { state.color = this.value; render(); });

// Save / Load / Clear / Print
byId('rb-btn-save').addEventListener('click', function() {
try {
localStorage.setItem('rb_state_en', JSON.stringify(state));
alert('Resume saved to browser storage.');
} catch(e) { alert('Save failed: ' + e.message); }
});
byId('rb-btn-load').addEventListener('click', function() {
try {
var raw = localStorage.getItem('rb_state_en');
if (!raw) { alert('No saved resume found.'); return; }
var saved = JSON.parse(raw);
Object.assign(state, saved);
// Restore experience/education IDs
if (state.experience.length) expId = Math.max.apply(null, state.experience.map(function(e){return e.id;}));
if (state.education.length) eduId = Math.max.apply(null, state.education.map(function(e){return e.id;}));
restoreUI();
render();
alert('Resume loaded.');
} catch(e) { alert('Load failed: ' + e.message); }
});
byId('rb-btn-clear').addEventListener('click', function() {
if (!confirm('Clear all data?')) return;
state.name=''; state.email=''; state.phone=''; state.location=''; state.linkedin=''; state.website='';
state.summary=''; state.experience=[]; state.education=[]; state.skills=[]; state.languages=[];
state.template='classic'; state.color='#2563eb';
expId=0; eduId=0;
restoreUI(); render();
});
byId('rb-btn-print').addEventListener('click', function() { window.print(); });

function restoreUI() {
['name','email','phone','location','linkedin','website'].forEach(function(f) {
var el = byId('rb-' + f); if (el) el.value = state[f] || '';
});
byId('rb-summary').value = state.summary || '';
byId('rb-tpl-select').value = state.template || 'classic';
byId('rb-color-pick').value = state.color || '#2563eb';
renderExpList(); renderEduList(); renderTags(); renderLangTags();
}

// ---- RENDER PREVIEW ----
function render() {
var tpl = state.template || 'classic';
var box = byId('rb-preview-box');
box.className = 'rb-tpl-' + tpl;
box.style.setProperty('--rb-accent', state.color || '#2563eb');

if (tpl === 'modern') {
renderModern();
} else {
renderStandard(tpl);
}
}

function contactLine() {
var parts = [];
if (state.email) parts.push(esc(state.email));
if (state.phone) parts.push(esc(state.phone));
if (state.location) parts.push(esc(state.location));
if (state.linkedin) parts.push(esc(state.linkedin));
if (state.website) parts.push(esc(state.website));
return parts.join(' &nbsp;|&nbsp; ');
}

function renderSectionBlocks(tpl, inSidebar) {
var html = '';
state.sectionOrder.forEach(function(sec) {
// Modern layout: sidebar gets skills+languages, main gets summary+exp+edu
if (tpl === 'modern') {
if (inSidebar && sec !== 'skills' && sec !== 'languages') return;
if (!inSidebar && (sec === 'skills' || sec === 'languages' || sec === 'personal')) return;
} else {
if (sec === 'personal') return; // personal rendered separately
}

if (sec === 'summary' && state.summary) {
html += '<div class="rbp-section-title">Summary</div>';
html += '<div class="rbp-summary">' + esc(state.summary) + '</div>';
}
if (sec === 'experience' && state.experience.length) {
html += '<div class="rbp-section-title">Work Experience</div>';
state.experience.forEach(function(e) {
html += '<div class="rbp-entry">';
html += '<div class="rbp-entry-title">' + esc(e.title) + '</div>';
html += '<div class="rbp-entry-sub">' + esc(e.company) + '</div>';
if (e.start || e.end) html += '<div class="rbp-entry-date">' + esc(e.start) + (e.end ? ' – ' + esc(e.end) : '') + '</div>';
if (e.desc) html += '<div class="rbp-entry-desc">' + esc(e.desc) + '</div>';
html += '</div>';
});
}
if (sec === 'education' && state.education.length) {
html += '<div class="rbp-section-title">Education</div>';
state.education.forEach(function(e) {
html += '<div class="rbp-entry">';
html += '<div class="rbp-entry-title">' + esc(e.degree) + '</div>';
html += '<div class="rbp-entry-sub">' + esc(e.school) + '</div>';
if (e.start || e.end) html += '<div class="rbp-entry-date">' + esc(e.start) + (e.end ? ' – ' + esc(e.end) : '') + '</div>';
if (e.desc) html += '<div class="rbp-entry-desc">' + esc(e.desc) + '</div>';
html += '</div>';
});
}
if (sec === 'skills' && state.skills.length) {
html += '<div class="rbp-section-title">Skills</div><div>';
state.skills.forEach(function(s) { html += '<span class="rbp-tag">' + esc(s) + '</span>'; });
html += '</div>';
}
if (sec === 'languages' && state.languages.length) {
html += '<div class="rbp-section-title">Languages</div><div>';
state.languages.forEach(function(s) { html += '<span class="rbp-tag">' + esc(s) + '</span>'; });
html += '</div>';
}
});
return html;
}

function renderStandard(tpl) {
var inner = byId('rb-preview-inner');
var html = '';
html += '<div class="rbp-name">' + (esc(state.name) || 'Your Name') + '</div>';
var cl = contactLine();
if (cl) html += '<div class="rbp-contact">' + cl + '</div>';
html += renderSectionBlocks(tpl, false);
inner.innerHTML = html;
}

function renderModern() {
var inner = byId('rb-preview-inner');
var sidebar = '<div class="rbp-sidebar">';
sidebar += '<div class="rbp-name">' + (esc(state.name) || 'Your Name') + '</div>';
var parts = [];
if (state.email) parts.push(esc(state.email));
if (state.phone) parts.push(esc(state.phone));
if (state.location) parts.push(esc(state.location));
if (state.linkedin) parts.push(esc(state.linkedin));
if (state.website) parts.push(esc(state.website));
if (parts.length) sidebar += '<div class="rbp-contact">' + parts.join('<br>') + '</div>';
sidebar += renderSectionBlocks('modern', true);
sidebar += '</div>';
var main = '<div class="rbp-main">' + renderSectionBlocks('modern', false) + '</div>';
inner.innerHTML = sidebar + main;
}

// Init
addExp(); addEdu();
render();

})();
</script>

---

> **Create cover letters** → [Lorem Ipsum Generator](/tools/lorem-ipsum-generator/)

> **Generate email signatures** → [Email Signature Generator](/tools/email-signature-generator/)

</div>

## Related Articles

- [How to Use AI to Land Your Dream Job (Resume + Interview)](/posts/ai-resume-optimization-job-search-2026/)
- [How to Create a Resume with AI (Step-by-Step Guide for 2026)](/posts/create-resume-with-ai-step-by-step/)
- [ChatGPT Resume Tips for Career Changers Over 50 (2026)](/posts/chatgpt-resume-over-50-career-change/)
