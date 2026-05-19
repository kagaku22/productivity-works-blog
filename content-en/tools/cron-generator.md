---
title: "Cron Expression Generator"
date: 2025-05-16
description: "Free online cron expression generator. Build cron schedules visually, get human-readable descriptions, and preview the next 5 execution times — no signup required."
categories: ["Free Tools"]
slug: "cron-generator"
ShowToc: false
cover:
  image: "/images/covers/cron-generator.png"
  alt: "Cron Expression Generator"
aliases:
  - "/tools/cron-expression-builder/"
  - "/tools/crontab-generator/"
---

<style>
#cron-app *,
#cron-app *::before,
#cron-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#cron-app {
font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, "Liberation Mono", monospace;
background: #0f172a;
color: #e2e8f0;
border-radius: 12px;
padding: 28px;
max-width: 860px;
margin: 0 auto;
}

#cron-app h2 {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 1.4rem;
font-weight: 700;
color: #84cc16;
margin-bottom: 20px;
letter-spacing: -0.02em;
}

#cron-app .ca-section-label {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.7rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.1em;
color: #64748b;
margin-bottom: 10px;
}

/* Presets */
#cron-app .ca-presets {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 24px;
}

#cron-app .ca-preset-btn {
background: #1e293b;
border: 1px solid #334155;
color: #94a3b8;
font-size: 0.75rem;
font-family: inherit;
padding: 6px 12px;
border-radius: 6px;
cursor: pointer;
transition: all 0.15s;
white-space: nowrap;
}

#cron-app .ca-preset-btn:hover {
background: #253347;
border-color: #84cc16;
color: #84cc16;
}

/* Manual input */
#cron-app .ca-manual-row {
display: flex;
gap: 10px;
margin-bottom: 24px;
align-items: center;
}

#cron-app .ca-manual-input {
flex: 1;
background: #1e293b;
border: 1px solid #334155;
color: #f1f5f9;
font-family: inherit;
font-size: 1rem;
padding: 10px 14px;
border-radius: 8px;
outline: none;
transition: border-color 0.15s;
}

#cron-app .ca-manual-input:focus {
border-color: #84cc16;
}

#cron-app .ca-parse-btn,
#cron-app .ca-copy-btn {
background: #84cc16;
border: none;
color: #0f172a;
font-family: ui-sans-serif, system-ui, sans-serif;
font-weight: 700;
font-size: 0.8rem;
padding: 10px 16px;
border-radius: 8px;
cursor: pointer;
transition: background 0.15s;
white-space: nowrap;
}

#cron-app .ca-parse-btn:hover,
#cron-app .ca-copy-btn:hover {
background: #a3e635;
}

/* Builder grid */
#cron-app .ca-builder {
display: grid;
grid-template-columns: repeat(5, 1fr);
gap: 12px;
margin-bottom: 24px;
}

@media (max-width: 600px) {
#cron-app .ca-builder {
grid-template-columns: repeat(2, 1fr);
}
}

#cron-app .ca-field {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 14px 12px;
display: flex;
flex-direction: column;
gap: 8px;
}

#cron-app .ca-field-label {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.65rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.1em;
color: #84cc16;
}

#cron-app .ca-field select,
#cron-app .ca-field input[type="text"] {
background: #0f172a;
border: 1px solid #334155;
color: #f1f5f9;
font-family: inherit;
font-size: 0.8rem;
padding: 6px 8px;
border-radius: 6px;
outline: none;
width: 100%;
transition: border-color 0.15s;
cursor: pointer;
}

#cron-app .ca-field select:focus,
#cron-app .ca-field input[type="text"]:focus {
border-color: #84cc16;
}

#cron-app .ca-field input[type="text"] {
cursor: text;
}

#cron-app .ca-field .ca-field-hint {
font-size: 0.65rem;
color: #475569;
font-family: ui-sans-serif, system-ui, sans-serif;
}

/* Result */
#cron-app .ca-result-box {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 18px 20px;
margin-bottom: 16px;
}

#cron-app .ca-expr-row {
display: flex;
align-items: center;
justify-content: space-between;
gap: 12px;
margin-bottom: 12px;
}

#cron-app .ca-expr-display {
font-size: 1.35rem;
font-weight: 700;
color: #84cc16;
letter-spacing: 0.08em;
word-break: break-all;
}

#cron-app .ca-description {
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.9rem;
color: #cbd5e1;
line-height: 1.5;
padding-top: 10px;
border-top: 1px solid #334155;
}

#cron-app .ca-error {
color: #f87171;
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.85rem;
padding-top: 10px;
border-top: 1px solid #334155;
}

/* Next runs */
#cron-app .ca-next-box {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 16px 20px;
}

#cron-app .ca-next-list {
list-style: none;
display: flex;
flex-direction: column;
gap: 6px;
margin-top: 10px;
}

#cron-app .ca-next-list li {
font-size: 0.82rem;
color: #94a3b8;
display: flex;
align-items: center;
gap: 10px;
}

#cron-app .ca-next-list li::before {
content: '';
display: inline-block;
width: 6px;
height: 6px;
border-radius: 50%;
background: #84cc16;
flex-shrink: 0;
}

#cron-app .ca-copy-feedback {
font-size: 0.72rem;
color: #84cc16;
font-family: ui-sans-serif, system-ui, sans-serif;
opacity: 0;
transition: opacity 0.3s;
white-space: nowrap;
}

#cron-app .ca-copy-feedback.visible {
opacity: 1;
}

#cron-app .ca-related {
margin-top: 20px;
padding-top: 16px;
border-top: 1px solid #1e293b;
font-family: ui-sans-serif, system-ui, sans-serif;
font-size: 0.82rem;
color: #64748b;
}

#cron-app .ca-related a {
color: #84cc16;
text-decoration: none;
}

#cron-app .ca-related a:hover {
text-decoration: underline;
}
</style>

<div id="cron-app">

<h2>Cron Expression Generator</h2>

<div class="ca-section-label">Common Presets</div>
<div class="ca-presets">
<button class="ca-preset-btn" data-expr="* * * * *">Every minute</button>
<button class="ca-preset-btn" data-expr="0 * * * *">Every hour</button>
<button class="ca-preset-btn" data-expr="0 0 * * *">Daily at midnight</button>
<button class="ca-preset-btn" data-expr="0 9 * * *">Daily at 9 AM</button>
<button class="ca-preset-btn" data-expr="0 0 * * 1">Weekly (Mon midnight)</button>
<button class="ca-preset-btn" data-expr="0 9 * * 1">Weekly (Mon 9 AM)</button>
<button class="ca-preset-btn" data-expr="0 0 1 * *">Monthly 1st</button>
<button class="ca-preset-btn" data-expr="0 0 1 1 *">Yearly (Jan 1st)</button>
<button class="ca-preset-btn" data-expr="*/5 * * * *">Every 5 min</button>
<button class="ca-preset-btn" data-expr="*/15 * * * *">Every 15 min</button>
<button class="ca-preset-btn" data-expr="*/30 * * * *">Every 30 min</button>
<button class="ca-preset-btn" data-expr="0 9-17 * * 1-5">Hourly (9–5 weekdays)</button>
</div>

<div class="ca-section-label">Manual Entry / Parse</div>
<div class="ca-manual-row">
<input class="ca-manual-input" id="ca-manual" type="text" placeholder="e.g.  */5 * * * *" spellcheck="false" />
<button class="ca-parse-btn" id="ca-parse-btn">Parse</button>
</div>

<div class="ca-section-label">Visual Builder</div>
<div class="ca-builder">
<div class="ca-field">
<div class="ca-field-label">Minute</div>
<select id="ca-min-mode">
<option value="any">Every minute (*)</option>
<option value="every">Every N minutes</option>
<option value="specific">Specific minute(s)</option>
<option value="range">Range</option>
</select>
<input type="text" id="ca-min-val" placeholder="e.g. 0,30" style="display:none" />
<div class="ca-field-hint" id="ca-min-hint"></div>
</div>
<div class="ca-field">
<div class="ca-field-label">Hour</div>
<select id="ca-hr-mode">
<option value="any">Every hour (*)</option>
<option value="every">Every N hours</option>
<option value="specific">Specific hour(s)</option>
<option value="range">Range</option>
</select>
<input type="text" id="ca-hr-val" placeholder="e.g. 9,17" style="display:none" />
<div class="ca-field-hint" id="ca-hr-hint"></div>
</div>
<div class="ca-field">
<div class="ca-field-label">Day of Month</div>
<select id="ca-dom-mode">
<option value="any">Every day (*)</option>
<option value="specific">Specific day(s)</option>
<option value="range">Range</option>
</select>
<input type="text" id="ca-dom-val" placeholder="e.g. 1,15" style="display:none" />
<div class="ca-field-hint" id="ca-dom-hint"></div>
</div>
<div class="ca-field">
<div class="ca-field-label">Month</div>
<select id="ca-mon-mode">
<option value="any">Every month (*)</option>
<option value="specific">Specific month(s)</option>
<option value="range">Range</option>
</select>
<input type="text" id="ca-mon-val" placeholder="e.g. 1,6,12" style="display:none" />
<div class="ca-field-hint" id="ca-mon-hint"></div>
</div>
<div class="ca-field">
<div class="ca-field-label">Weekday</div>
<select id="ca-dow-mode">
<option value="any">Any day (*)</option>
<option value="specific">Specific day(s)</option>
<option value="range">Range</option>
</select>
<input type="text" id="ca-dow-val" placeholder="0=Sun … 6=Sat" style="display:none" />
<div class="ca-field-hint" id="ca-dow-hint"></div>
</div>
</div>

<div class="ca-result-box">
<div class="ca-expr-row">
<div class="ca-expr-display" id="ca-expr-display">* * * * *</div>
<div style="display:flex;align-items:center;gap:10px">
<span class="ca-copy-feedback" id="ca-copy-feedback">Copied!</span>
<button class="ca-copy-btn" id="ca-copy-btn">Copy</button>
</div>
</div>
<div class="ca-description" id="ca-description">Runs every minute.</div>
</div>

<div class="ca-next-box">
<div class="ca-section-label">Next 5 Execution Times</div>
<ul class="ca-next-list" id="ca-next-list"></ul>
</div>

<div class="ca-related">
Related: Format code with <a href="/tools/json-formatter/">JSON Formatter</a>
</div>

</div>

<script>
(function () {
'use strict';

// ── DOM refs ─────────────────────────────────────────────────────────────
const manual      = document.getElementById('ca-manual');
const parseBtn    = document.getElementById('ca-parse-btn');
const exprDisplay = document.getElementById('ca-expr-display');
const descEl      = document.getElementById('ca-description');
const nextList    = document.getElementById('ca-next-list');
const copyBtn     = document.getElementById('ca-copy-btn');
const copyFb      = document.getElementById('ca-copy-feedback');

const fields = ['min', 'hr', 'dom', 'mon', 'dow'];
const modes  = {};
const vals   = {};
const hints  = {};

fields.forEach(f => {
modes[f] = document.getElementById('ca-' + f + '-mode');
vals[f]  = document.getElementById('ca-' + f + '-val');
hints[f] = document.getElementById('ca-' + f + '-hint');
});

// ── Mode → show/hide value input ────────────────────────────────────────
function updateFieldUI(f) {
const m = modes[f].value;
const needVal = m !== 'any';
vals[f].style.display = needVal ? 'block' : 'none';

const hintMap = {
any:      '',
every:    { min: 'N (1–59)', hr: 'N (1–23)', dom: '', mon: '', dow: '' },
specific: { min: 'e.g. 0,15,30,45', hr: 'e.g. 9,12,18', dom: 'e.g. 1,15', mon: 'e.g. 1,6,12', dow: '0=Sun 1=Mon … 6=Sat' },
range:    { min: 'start-end e.g. 0-29', hr: 'e.g. 9-17', dom: 'e.g. 1-15', mon: 'e.g. 1-6', dow: 'e.g. 1-5' },
};
hints[f].textContent = (m === 'any') ? '' : (hintMap[m][f] || '');
if (m !== 'any' && !vals[f].value) {
const defaults = {
every:    { min: '5', hr: '2', dom: '', mon: '', dow: '' },
specific: { min: '0', hr: '9', dom: '1', mon: '1', dow: '1' },
range:    { min: '0-29', hr: '9-17', dom: '1-15', mon: '1-6', dow: '1-5' },
};
vals[f].value = defaults[m] ? (defaults[m][f] || '') : '';
}
rebuild();
}

fields.forEach(f => {
modes[f].addEventListener('change', () => updateFieldUI(f));
vals[f].addEventListener('input', rebuild);
});

// ── Build expression from UI ─────────────────────────────────────────────
function fieldExpr(f) {
const m = modes[f].value;
const v = vals[f].value.trim();
if (m === 'any') return '*';
if (m === 'every') {
const n = parseInt(v, 10);
if (!v || isNaN(n) || n < 1) return '*';
return '*/' + n;
}
if (m === 'specific' || m === 'range') {
return v || '*';
}
return '*';
}

function rebuild() {
const parts = fields.map(f => fieldExpr(f));
const expr = parts.join(' ');
setExpression(expr);
}

// ── Parse & describe ─────────────────────────────────────────────────────
function setExpression(expr) {
expr = expr.trim();
exprDisplay.textContent = expr;
manual.value = expr;

const result = parseExpr(expr);
if (result.error) {
descEl.className = 'ca-error';
descEl.textContent = result.error;
nextList.innerHTML = '';
} else {
descEl.className = 'ca-description';
descEl.textContent = result.description;
renderNext(expr);
}
}

function parseExpr(expr) {
const parts = expr.trim().split(/\s+/);
if (parts.length !== 5) return { error: 'Cron expression must have exactly 5 fields: minute hour day month weekday' };

const [min, hr, dom, mon, dow] = parts;

// Basic validation
const ranges = [
[min, 0, 59, 'minute'],
[hr,  0, 23, 'hour'],
[dom, 1, 31, 'day-of-month'],
[mon, 1, 12, 'month'],
[dow, 0,  7, 'weekday'],
];
for (const [f, lo, hi, name] of ranges) {
const err = validateField(f, lo, hi);
if (err) return { error: 'Invalid ' + name + ': ' + err };
}

return { description: describe(min, hr, dom, mon, dow) };
}

function validateField(f, lo, hi) {
if (f === '*') return null;
if (/^\*\/\d+$/.test(f)) {
const n = parseInt(f.slice(2), 10);
if (n < 1) return 'step must be >= 1';
return null;
}
const parts = f.split(',');
for (const p of parts) {
if (p.includes('-')) {
const [a, b] = p.split('-').map(Number);
if (isNaN(a) || isNaN(b) || a < lo || b > hi || a > b)
return '"' + p + '" is not a valid range (' + lo + '-' + hi + ')';
} else {
const n = Number(p);
if (isNaN(n) || n < lo || n > hi)
return '"' + p + '" out of range (' + lo + '-' + hi + ')';
}
}
return null;
}

// ── Human-readable description ───────────────────────────────────────────
const MONTHS = ['','January','February','March','April','May','June','July','August','September','October','November','December'];
const DAYS   = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday'];

function fmtField(f, type) {
if (f === '*') return null; // "any"
if (f.startsWith('*/')) {
const n = f.slice(2);
const label = { min: 'minute', hr: 'hour', dom: 'day', mon: 'month', dow: 'day' }[type];
return 'every ' + n + ' ' + label + (n === '1' ? '' : 's');
}
// specific / range / list
const parts = f.split(',');
const fmted = parts.map(p => {
if (p.includes('-')) {
const [a, b] = p.split('-');
if (type === 'mon') return MONTHS[+a] + ' through ' + MONTHS[+b];
if (type === 'dow') return DAYS[+a] + ' through ' + DAYS[+b];
return p;
}
if (type === 'mon') return MONTHS[+p] || p;
if (type === 'dow') return DAYS[+p] || p;
return p;
});
return fmted.join(', ');
}

function ordinal(n) {
const s = ['th','st','nd','rd'];
const v = n % 100;
return n + (s[(v-20)%10] || s[v] || s[0]);
}

function describe(min, hr, dom, mon, dow) {
// Time description
let time = '';
if (min === '*' && hr === '*') {
time = 'every minute';
} else if (min.startsWith('*/') && hr === '*') {
time = 'every ' + min.slice(2) + ' minutes';
} else if (hr.startsWith('*/') && min === '0') {
time = 'every ' + hr.slice(2) + ' hours (at minute 0)';
} else if (hr.startsWith('*/')) {
time = 'every ' + hr.slice(2) + ' hours at minute ' + min;
} else {
// specific times
const hrParts = hr.split(',');
const minParts = min === '*' ? ['every minute'] : min.split(',').map(m => m.padStart(2,'0'));
const times = hrParts.map(h => {
if (h.includes('-')) return 'hours ' + h + ':' + (min === '*' ? 'xx' : min.padStart(2,'0'));
return h.padStart(2,'0') + ':' + (min === '*' ? 'xx' : (min.includes(',') ? '[' + min + ']' : min.padStart(2,'0')));
});
time = 'at ' + times.join(', ');
}

// Day/Month description
const domStr = fmtField(dom, 'dom');
const monStr = fmtField(mon, 'mon');
const dowStr = fmtField(dow, 'dow');

let schedule = 'Runs ' + time;

if (dowStr) {
schedule += ' on ' + dowStr;
} else if (domStr) {
// check if all specific days
const domParts = dom.split(',');
const ordinals = domParts.map(p => {
if (p.includes('-')) return 'days ' + p;
return ordinal(+p);
});
schedule += ' on the ' + ordinals.join(', ') + ' of the month';
}

if (monStr) {
schedule += ' in ' + monStr;
}

schedule += '.';
return schedule;
}

// ── Next 5 execution times ────────────────────────────────────────────────
function renderNext(expr) {
const parts = expr.trim().split(/\s+/);
if (parts.length !== 5) { nextList.innerHTML = ''; return; }
const [min, hr, dom, mon, dow] = parts;

const times = nextRuns(min, hr, dom, mon, dow, 5);
nextList.innerHTML = times.map(d => '<li>' + formatDate(d) + '</li>').join('');
}

function expandField(f, lo, hi) {
if (f === '*') {
const r = [];
for (let i = lo; i <= hi; i++) r.push(i);
return r;
}
if (f.startsWith('*/')) {
const step = parseInt(f.slice(2), 10);
const r = [];
for (let i = lo; i <= hi; i += step) r.push(i);
return r;
}
const result = new Set();
f.split(',').forEach(p => {
if (p.includes('-')) {
const [a, b] = p.split('-').map(Number);
for (let i = a; i <= b; i++) result.add(i);
} else {
result.add(Number(p));
}
});
return [...result].sort((a,b) => a-b);
}

function nextRuns(minF, hrF, domF, monF, dowF, count) {
const mins = expandField(minF, 0, 59);
const hrs  = expandField(hrF,  0, 23);
const doms = expandField(domF, 1, 31);
const mons = expandField(monF, 1, 12);
const dows = dowF === '*' ? null : expandField(dowF.replace('7','0'), 0, 6);

const results = [];
const now = new Date();
// Start from next minute
const start = new Date(now.getFullYear(), now.getMonth(), now.getDate(), now.getHours(), now.getMinutes() + 1, 0, 0);

let d = new Date(start);
const limit = new Date(start.getTime() + 366 * 24 * 60 * 60 * 1000); // max 1 year ahead

while (results.length < count && d < limit) {
const m  = d.getMonth() + 1; // 1-based
const dy = d.getDate();
const h  = d.getHours();
const mn = d.getMinutes();
const wd = d.getDay();

if (!mons.includes(m)) {
// advance to 1st of next valid month
const nextMon = mons.find(x => x > m);
if (nextMon) {
d = new Date(d.getFullYear(), nextMon - 1, 1, 0, 0, 0, 0);
} else {
d = new Date(d.getFullYear() + 1, mons[0] - 1, 1, 0, 0, 0, 0);
}
continue;
}

const domOk = doms.includes(dy);
const dowOk = dows === null || dows.includes(wd);
if (!domOk && !dowOk) {
d = new Date(d.getFullYear(), d.getMonth(), d.getDate() + 1, 0, 0, 0, 0);
continue;
}

if (!hrs.includes(h)) {
const nextHr = hrs.find(x => x > h);
if (nextHr !== undefined) {
d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), nextHr, 0, 0, 0);
} else {
d = new Date(d.getFullYear(), d.getMonth(), d.getDate() + 1, 0, 0, 0, 0);
}
continue;
}

if (!mins.includes(mn)) {
const nextMin = mins.find(x => x > mn);
if (nextMin !== undefined) {
d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), d.getHours(), nextMin, 0, 0);
} else {
const nextHr = hrs.find(x => x > h);
if (nextHr !== undefined) {
d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), nextHr, 0, 0, 0);
} else {
d = new Date(d.getFullYear(), d.getMonth(), d.getDate() + 1, 0, 0, 0, 0);
}
}
continue;
}

results.push(new Date(d));
d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), d.getHours(), d.getMinutes() + 1, 0, 0);
}

return results;
}

function formatDate(d) {
const days = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];
const pad = n => String(n).padStart(2, '0');
return days[d.getDay()] + ' ' +
d.getFullYear() + '-' + pad(d.getMonth()+1) + '-' + pad(d.getDate()) +
'  ' + pad(d.getHours()) + ':' + pad(d.getMinutes());
}

// ── Presets ──────────────────────────────────────────────────────────────
document.querySelectorAll('#cron-app .ca-preset-btn').forEach(btn => {
btn.addEventListener('click', () => {
const expr = btn.dataset.expr;
loadExprIntoBuilder(expr);
setExpression(expr);
});
});

function loadExprIntoBuilder(expr) {
const parts = expr.trim().split(/\s+/);
if (parts.length !== 5) return;
const [minV, hrV, domV, monV, dowV] = parts;

function detectMode(f) {
if (f === '*') return 'any';
if (f.startsWith('*/')) return 'every';
if (f.includes('-')) return 'range';
return 'specific';
}

const fieldMap = [
['min', minV],
['hr',  hrV],
['dom', domV],
['mon', monV],
['dow', dowV],
];

fieldMap.forEach(([f, v]) => {
const m = detectMode(v);
modes[f].value = m;
if (m === 'any') {
vals[f].value = '';
vals[f].style.display = 'none';
} else if (m === 'every') {
vals[f].value = v.slice(2);
vals[f].style.display = 'block';
} else {
vals[f].value = v;
vals[f].style.display = 'block';
}
hints[f].textContent = '';
});
}

// ── Manual parse ─────────────────────────────────────────────────────────
parseBtn.addEventListener('click', () => {
const expr = manual.value.trim();
if (!expr) return;
loadExprIntoBuilder(expr);
setExpression(expr);
});

manual.addEventListener('keydown', e => {
if (e.key === 'Enter') parseBtn.click();
});

// ── Copy ─────────────────────────────────────────────────────────────────
copyBtn.addEventListener('click', () => {
const expr = exprDisplay.textContent;
navigator.clipboard.writeText(expr).then(() => {
copyFb.classList.add('visible');
setTimeout(() => copyFb.classList.remove('visible'), 1800);
}).catch(() => {
// fallback
const ta = document.createElement('textarea');
ta.value = expr;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
copyFb.classList.add('visible');
setTimeout(() => copyFb.classList.remove('visible'), 1800);
});
});

// ── Init ─────────────────────────────────────────────────────────────────
setExpression('* * * * *');

})();
</script>
