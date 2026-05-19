---
title: "Regex Visualizer & Explainer"
date: 2025-05-16
description: "Free regex visualizer tool. Enter a regular expression to see a visual breakdown of each component. Highlights matches in test text with group extraction."
categories: ["Free Tools"]
slug: "regex-visualizer"
ShowToc: false
cover:
  image: "/images/covers/regex-visualizer.png"
  alt: "Regex Visualizer & Explainer"
---

Enter a regular expression to get an instant visual breakdown of every token, highlight all matches in your test string, and extract capture groups — no sign-up, no server, no external libraries.

<div id="rv-app">
<style>
#rv-app *, #rv-app *::before, #rv-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#rv-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
font-size: 14px;
color: #1e293b;
max-width: 900px;
margin: 0 auto;
}

#rv-app .rv-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 18px 20px;
margin-bottom: 14px;
}

#rv-app .rv-label {
font-size: 11px;
font-weight: 700;
letter-spacing: .07em;
text-transform: uppercase;
color: #64748b;
margin-bottom: 10px;
}

/* Pattern row */
#rv-app .rv-pattern-row {
display: flex;
align-items: center;
gap: 8px;
flex-wrap: wrap;
}
#rv-app .rv-slash {
font-size: 22px;
color: #94a3b8;
font-family: "Fira Mono", "Consolas", monospace;
flex-shrink: 0;
}
#rv-app #rv-pattern {
flex: 1;
min-width: 180px;
font-family: "Fira Mono", "Consolas", monospace;
font-size: 15px;
padding: 8px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
outline: none;
color: #1e293b;
background: #f8fafc;
transition: border-color .15s;
}
#rv-app #rv-pattern:focus { border-color: #6366f1; background: #fff; }

#rv-app .rv-flags {
display: flex;
gap: 5px;
flex-wrap: wrap;
}
#rv-app .rv-flag {
padding: 6px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
cursor: pointer;
font-size: 12px;
font-weight: 700;
font-family: "Fira Mono", monospace;
background: #f8fafc;
color: #64748b;
transition: all .15s;
user-select: none;
}
#rv-app .rv-flag.on { background: #6366f1; border-color: #6366f1; color: #fff; }
#rv-app .rv-flag:hover:not(.on) { border-color: #6366f1; color: #6366f1; }

#rv-app .rv-copy-btn {
padding: 7px 14px;
background: #f1f5f9;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
cursor: pointer;
font-size: 12px;
font-weight: 600;
color: #475569;
transition: all .15s;
white-space: nowrap;
}
#rv-app .rv-copy-btn:hover { background: #e2e8f0; }
#rv-app .rv-copy-btn.copied { background: #d1fae5; border-color: #6ee7b7; color: #065f46; }

/* Error */
#rv-app .rv-error {
display: none;
background: #fef2f2;
border: 1px solid #fca5a5;
color: #b91c1c;
border-radius: 7px;
padding: 8px 12px;
font-size: 13px;
margin-top: 8px;
}

/* Visual breakdown */
#rv-app .rv-breakdown {
display: flex;
flex-wrap: wrap;
gap: 6px;
min-height: 40px;
align-items: flex-start;
}
#rv-app .rv-token {
display: flex;
flex-direction: column;
align-items: center;
gap: 3px;
}
#rv-app .rv-tok-text {
font-family: "Fira Mono", "Consolas", monospace;
font-size: 13px;
font-weight: 700;
padding: 4px 8px;
border-radius: 5px;
white-space: pre;
}
#rv-app .rv-tok-desc {
font-size: 10px;
color: #475569;
text-align: center;
max-width: 90px;
line-height: 1.3;
}

/* Token color palette */
#rv-app .rv-tok-anchor    { background: #fef9c3; color: #854d0e; }
#rv-app .rv-tok-quant     { background: #dcfce7; color: #166534; }
#rv-app .rv-tok-escape    { background: #ede9fe; color: #5b21b6; }
#rv-app .rv-tok-charclass { background: #dbeafe; color: #1e40af; }
#rv-app .rv-tok-group     { background: #fce7f3; color: #9d174d; }
#rv-app .rv-tok-alt       { background: #ffedd5; color: #9a3412; }
#rv-app .rv-tok-dot       { background: #f0f9ff; color: #0369a1; }
#rv-app .rv-tok-literal   { background: #f1f5f9; color: #334155; }

/* Legend */
#rv-app .rv-legend {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 10px;
}
#rv-app .rv-legend-item {
display: flex;
align-items: center;
gap: 5px;
font-size: 11px;
color: #475569;
}
#rv-app .rv-legend-swatch {
width: 12px;
height: 12px;
border-radius: 3px;
flex-shrink: 0;
}

/* Patterns library */
#rv-app .rv-lib {
display: flex;
flex-wrap: wrap;
gap: 7px;
}
#rv-app .rv-lib-btn {
padding: 6px 12px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 6px;
cursor: pointer;
font-size: 12px;
font-weight: 600;
color: #475569;
transition: all .15s;
}
#rv-app .rv-lib-btn:hover { background: #ede9fe; border-color: #a5b4fc; color: #4338ca; }

/* Test string */
#rv-app #rv-test {
width: 100%;
min-height: 90px;
font-family: "Fira Mono", "Consolas", monospace;
font-size: 13px;
padding: 10px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
resize: vertical;
outline: none;
background: #f8fafc;
color: #1e293b;
transition: border-color .15s;
}
#rv-app #rv-test:focus { border-color: #6366f1; background: #fff; }

/* Highlight output */
#rv-app .rv-hl-box {
font-family: "Fira Mono", "Consolas", monospace;
font-size: 13px;
line-height: 1.7;
padding: 10px 12px;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 7px;
white-space: pre-wrap;
word-break: break-all;
min-height: 42px;
}
#rv-app .rv-hl-box .rv-m0  { background: #fde68a; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m1  { background: #bbf7d0; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m2  { background: #bfdbfe; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m3  { background: #fecdd3; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m4  { background: #e9d5ff; border-radius: 3px; }
#rv-app .rv-hl-box .rv-m5  { background: #fed7aa; border-radius: 3px; }

#rv-app .rv-stats {
display: flex;
gap: 16px;
margin-top: 10px;
flex-wrap: wrap;
}
#rv-app .rv-stat {
font-size: 12px;
color: #64748b;
}
#rv-app .rv-stat strong { color: #1e293b; }

/* Match list */
#rv-app .rv-match-list {
list-style: none;
display: flex;
flex-direction: column;
gap: 8px;
max-height: 280px;
overflow-y: auto;
}
#rv-app .rv-match-item {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 7px;
padding: 8px 12px;
font-size: 12px;
}
#rv-app .rv-match-item .rv-mi-head {
font-weight: 700;
color: #334155;
margin-bottom: 4px;
}
#rv-app .rv-match-item .rv-mi-val {
font-family: "Fira Mono", monospace;
background: #fde68a;
padding: 2px 6px;
border-radius: 4px;
font-size: 12px;
}
#rv-app .rv-match-item .rv-mi-grp {
margin-top: 4px;
font-size: 11px;
color: #64748b;
}
#rv-app .rv-match-item .rv-mi-grp span {
font-family: "Fira Mono", monospace;
background: #bbf7d0;
padding: 1px 5px;
border-radius: 3px;
color: #065f46;
margin-left: 4px;
}
#rv-app .rv-empty-msg {
color: #94a3b8;
font-size: 13px;
text-align: center;
padding: 16px 0;
}
</style>

<!-- Pattern Input -->
<div class="rv-card">
<div class="rv-label">Regular Expression</div>
<div class="rv-pattern-row">
<span class="rv-slash">/</span>
<input id="rv-pattern" type="text" placeholder="e.g. (\d{3})-(\d{4})" autocomplete="off" spellcheck="false" />
<span class="rv-slash">/</span>
<div class="rv-flags">
<button class="rv-flag on" data-flag="g" title="Global">g</button>
<button class="rv-flag" data-flag="i" title="Case-insensitive">i</button>
<button class="rv-flag" data-flag="m" title="Multiline">m</button>
<button class="rv-flag" data-flag="s" title="Dotall">s</button>
</div>
<button class="rv-copy-btn" id="rv-copy-btn">Copy</button>
</div>
<div class="rv-error" id="rv-error"></div>
</div>

<!-- Common Patterns Library -->
<div class="rv-card">
<div class="rv-label">Common Patterns</div>
<div class="rv-lib">
<button class="rv-lib-btn" data-pattern="[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}" data-label="Email">Email</button>
<button class="rv-lib-btn" data-pattern="https?:\/\/(www\.)?[-a-zA-Z0-9@:%._+~#=]{1,256}\.[a-zA-Z]{2,6}\b([-a-zA-Z0-9@:%_+.~#?&\/=]*)" data-label="URL">URL</button>
<button class="rv-lib-btn" data-pattern="\+?1?\s*\(?\d{3}\)?[\s.\-]?\d{3}[\s.\-]?\d{4}" data-label="Phone (US)">Phone (US)</button>
<button class="rv-lib-btn" data-pattern="\d{4}[-\/]\d{2}[-\/]\d{2}" data-label="Date (YYYY-MM-DD)">Date YYYY-MM-DD</button>
<button class="rv-lib-btn" data-pattern="\b((25[0-5]|2[0-4]\d|[01]?\d\d?)\.){3}(25[0-5]|2[0-4]\d|[01]?\d\d?)\b" data-label="IP Address">IP Address</button>
<button class="rv-lib-btn" data-pattern="^#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3})$" data-label="Hex Color">Hex Color</button>
<button class="rv-lib-btn" data-pattern="[A-Z][a-z]+" data-label="Capitalized Word">Capitalized Word</button>
<button class="rv-lib-btn" data-pattern="\b\d+(\.\d+)?\b" data-label="Number">Number</button>
</div>
</div>

<!-- Visual Breakdown -->
<div class="rv-card">
<div class="rv-label">Visual Breakdown</div>
<div class="rv-breakdown" id="rv-breakdown">
<span class="rv-empty-msg">Enter a regex pattern above to see the breakdown.</span>
</div>
<div class="rv-legend">
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#fef9c3;border:1px solid #fde047;"></div>Anchor</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#dcfce7;border:1px solid #86efac;"></div>Quantifier</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#ede9fe;border:1px solid #c4b5fd;"></div>Escape / Special</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#dbeafe;border:1px solid #93c5fd;"></div>Character Class</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#fce7f3;border:1px solid #f9a8d4;"></div>Group</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#ffedd5;border:1px solid #fdba74;"></div>Alternation</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#f0f9ff;border:1px solid #7dd3fc;"></div>Wildcard</div>
<div class="rv-legend-item"><div class="rv-legend-swatch" style="background:#f1f5f9;border:1px solid #cbd5e1;"></div>Literal</div>
</div>
</div>

<!-- Test String -->
<div class="rv-card">
<div class="rv-label">Test String</div>
<textarea id="rv-test" placeholder="Paste your test text here…"></textarea>
</div>

<!-- Match Highlights -->
<div class="rv-card">
<div class="rv-label">Highlighted Matches</div>
<div class="rv-hl-box" id="rv-hl"><span class="rv-empty-msg">Matches will appear here.</span></div>
<div class="rv-stats">
<div class="rv-stat">Matches: <strong id="rv-count">—</strong></div>
<div class="rv-stat">Test length: <strong id="rv-len">0</strong></div>
</div>
</div>

<!-- Match Detail List -->
<div class="rv-card">
<div class="rv-label">Match Details &amp; Captured Groups</div>
<ul class="rv-match-list" id="rv-match-list">
<li class="rv-empty-msg">No matches yet.</li>
</ul>
</div>

<script>
(function () {
'use strict';

var flagState = { g: true, i: false, m: false, s: false };

var elPat     = document.getElementById('rv-pattern');
var elTest    = document.getElementById('rv-test');
var elError   = document.getElementById('rv-error');
var elBreak   = document.getElementById('rv-breakdown');
var elHl      = document.getElementById('rv-hl');
var elCount   = document.getElementById('rv-count');
var elLen     = document.getElementById('rv-len');
var elMlist   = document.getElementById('rv-match-list');
var elCopy    = document.getElementById('rv-copy-btn');

/* ── Helpers ── */
function esc(s) {
return String(s)
.replace(/&/g,'&amp;')
.replace(/</g,'&lt;')
.replace(/>/g,'&gt;');
}

/* ── Flags ── */
document.querySelectorAll('#rv-app .rv-flag').forEach(function (el) {
el.addEventListener('click', function () {
var f = el.dataset.flag;
flagState[f] = !flagState[f];
el.classList.toggle('on', flagState[f]);
run();
});
});

/* ── Copy button ── */
elCopy.addEventListener('click', function () {
var pat = elPat.value;
if (!pat) return;
var flags = buildFlags();
navigator.clipboard.writeText('/' + pat + '/' + flags).then(function () {
elCopy.textContent = 'Copied!';
elCopy.classList.add('copied');
setTimeout(function () {
elCopy.textContent = 'Copy';
elCopy.classList.remove('copied');
}, 1800);
}).catch(function () {});
});

/* ── Common patterns library ── */
document.querySelectorAll('#rv-app .rv-lib-btn').forEach(function (el) {
el.addEventListener('click', function () {
elPat.value = el.dataset.pattern;
run();
});
});

/* ── Build flags string ── */
function buildFlags() {
return ['g','i','m','s'].filter(function (f) { return flagState[f]; }).join('');
}

/* ── Tokenizer ── */
var TOKENS = [
// Anchors
[/^\^/,                         'anchor', 'Start of string / line'],
[/^\$/,                         'anchor', 'End of string / line'],
[/^\\b/,                        'escape', 'Word boundary'],
[/^\\B/,                        'escape', 'Non-word boundary'],
[/^\\A/,                        'escape', 'Start of string (\\A)'],
[/^\\Z/,                        'escape', 'End of string (\\Z)'],
// Escaped specials
[/^\\d/,                        'escape', 'Any digit [0-9]'],
[/^\\D/,                        'escape', 'Non-digit [^0-9]'],
[/^\\w/,                        'escape', 'Word char [a-zA-Z0-9_]'],
[/^\\W/,                        'escape', 'Non-word char'],
[/^\\s/,                        'escape', 'Whitespace'],
[/^\\S/,                        'escape', 'Non-whitespace'],
[/^\\t/,                        'escape', 'Tab character'],
[/^\\n/,                        'escape', 'Newline'],
[/^\\r/,                        'escape', 'Carriage return'],
[/^\\f/,                        'escape', 'Form feed'],
[/^\\v/,                        'escape', 'Vertical tab'],
[/^\\0/,                        'escape', 'Null character'],
[/^\\x[0-9a-fA-F]{2}/,         'escape', 'Hex escape'],
[/^\\u[0-9a-fA-F]{4}/,         'escape', 'Unicode escape'],
[/^\\[^a-zA-Z0-9]/,            'escape', 'Escaped special character'],
// Groups
[/^\(\?</,                       'group', 'Named lookbehind / named group start'],
[/^\(\?<[^>]+>/,               'group', 'Named capture group start'],
[/^\(\?:/,                      'group', 'Non-capturing group start'],
[/^\(\?=/,                      'group', 'Lookahead (positive) start'],
[/^\(\?!/,                      'group', 'Lookahead (negative) start'],
[/^\(\?<=/,                     'group', 'Lookbehind (positive) start'],
[/^\(\?<!/,                     'group', 'Lookbehind (negative) start'],
[/^\(/,                         'group', 'Capture group start'],
[/^\)/,                         'group', 'Group end'],
// Character classes
[/^\[\^[^\]]*\]/,              'charclass', 'Negated character class'],
[/^\[[^\]]*\]/,                'charclass', 'Character class'],
// Quantifiers
[/^\{[0-9]+,[0-9]+\}\?/,      'quant', 'Lazy quantifier {n,m}'],
[/^\{[0-9]+,\}\?/,            'quant', 'Lazy quantifier {n,} (n or more)'],
[/^\{[0-9]+\}\?/,             'quant', 'Lazy quantifier {n}'],
[/^\{[0-9]+,[0-9]+\}/,        'quant', 'Quantifier: between n and m times'],
[/^\{[0-9]+,\}/,              'quant', 'Quantifier: n or more times'],
[/^\{[0-9]+\}/,               'quant', 'Quantifier: exactly n times'],
[/^\*\?/,                      'quant', 'Lazy: 0 or more (as few as possible)'],
[/^\+\?/,                      'quant', 'Lazy: 1 or more (as few as possible)'],
[/^\?\?/,                      'quant', 'Lazy: 0 or 1 (prefer 0)'],
[/^\*/,                        'quant', 'Greedy: 0 or more'],
[/^\+/,                        'quant', 'Greedy: 1 or more'],
[/^\?/,                        'quant', '0 or 1 (optional)'],
// Alternation
[/^\|/,                        'alt', 'Alternation (OR)'],
// Wildcard
[/^\./,                        'dot', 'Any character except newline'],
// Literal fallback
[/^[^]/,                       'literal', 'Literal character'],
];

var TYPE_CLASS = {
anchor:    'rv-tok-anchor',
quant:     'rv-tok-quant',
escape:    'rv-tok-escape',
charclass: 'rv-tok-charclass',
group:     'rv-tok-group',
alt:       'rv-tok-alt',
dot:       'rv-tok-dot',
literal:   'rv-tok-literal',
};

function tokenize(pat) {
var toks = [], rem = pat, limit = 500;
while (rem.length && limit-- > 0) {
var hit = false;
for (var i = 0; i < TOKENS.length; i++) {
var m = rem.match(TOKENS[i][0]);
if (m) {
toks.push({ text: m[0], type: TOKENS[i][1], desc: TOKENS[i][2] });
rem = rem.slice(m[0].length);
hit = true;
break;
}
}
if (!hit) rem = rem.slice(1);
}
return toks;
}

/* ── Render breakdown ── */
function renderBreakdown(pat) {
if (!pat) {
elBreak.innerHTML = '<span class="rv-empty-msg">Enter a regex pattern above to see the breakdown.</span>';
return;
}
var toks = tokenize(pat);
if (!toks.length) {
elBreak.innerHTML = '<span class="rv-empty-msg">No tokens found.</span>';
return;
}
var html = '';
toks.forEach(function (tk) {
var cls = TYPE_CLASS[tk.type] || 'rv-tok-literal';
html += '<div class="rv-token">'
+ '<span class="rv-tok-text ' + cls + '">' + esc(tk.text) + '</span>'
+ '<span class="rv-tok-desc">' + esc(tk.desc) + '</span>'
+ '</div>';
});
elBreak.innerHTML = html;
}

/* ── Highlight matches ── */
var MATCH_COLORS = ['rv-m0','rv-m1','rv-m2','rv-m3','rv-m4','rv-m5'];

function renderMatches(text, regex) {
elLen.textContent = text.length;
if (!regex) {
elHl.innerHTML = '<span class="rv-empty-msg">Matches will appear here.</span>';
elCount.textContent = '—';
elMlist.innerHTML = '<li class="rv-empty-msg">No matches yet.</li>';
return;
}

// Collect all matches
var matches = [];
var re = new RegExp(regex.source, regex.flags.replace('g','') + 'g');
var m;
var safety = 0;
while ((m = re.exec(text)) !== null && safety++ < 500) {
matches.push({ index: m.index, end: m.index + m[0].length, value: m[0], groups: Array.from(m).slice(1) });
if (m[0].length === 0) re.lastIndex++;
}

elCount.textContent = matches.length;

// Build highlighted HTML
if (matches.length === 0) {
elHl.innerHTML = '<span class="rv-empty-msg" style="color:#f97316;">No matches found.</span>'
+ (text ? esc(text) : '');
elMlist.innerHTML = '<li class="rv-empty-msg">No matches found.</li>';
return;
}

var hlHtml = '', pos = 0, ci = 0;
matches.forEach(function (mt) {
if (mt.index > pos) hlHtml += esc(text.slice(pos, mt.index));
var cls = MATCH_COLORS[ci % MATCH_COLORS.length];
hlHtml += '<span class="' + cls + '">' + esc(mt.value) + '</span>';
pos = mt.end;
ci++;
});
if (pos < text.length) hlHtml += esc(text.slice(pos));
elHl.innerHTML = hlHtml;

// Build match list
var listHtml = '';
matches.forEach(function (mt, idx) {
var colorCls = MATCH_COLORS[idx % MATCH_COLORS.length];
listHtml += '<li class="rv-match-item">'
+ '<div class="rv-mi-head">Match ' + (idx+1) + ' &nbsp;<span class="rv-mi-val">' + esc(mt.value) + '</span>'
+ ' &nbsp;<span style="font-size:11px;color:#94a3b8;">pos ' + mt.index + '–' + mt.end + '</span></div>';
if (mt.groups.length) {
listHtml += '<div class="rv-mi-grp">Groups:';
mt.groups.forEach(function (g, gi) {
listHtml += ' <span>$' + (gi+1) + ': ' + esc(g !== undefined ? g : 'undefined') + '</span>';
});
listHtml += '</div>';
}
listHtml += '</li>';
});
elMlist.innerHTML = listHtml;
}

/* ── Main run ── */
function run() {
var pat = elPat.value;
var text = elTest.value;
elLen.textContent = text.length;
elError.style.display = 'none';

renderBreakdown(pat);

if (!pat) {
renderMatches(text, null);
return;
}

var flags = buildFlags();
var regex;
try {
regex = new RegExp(pat, flags);
} catch (e) {
elError.style.display = 'block';
elError.textContent = 'Invalid regex: ' + e.message;
elHl.innerHTML = '<span class="rv-empty-msg">Fix the pattern to see highlights.</span>';
elCount.textContent = '—';
elMlist.innerHTML = '<li class="rv-empty-msg">—</li>';
return;
}

renderMatches(text, regex);
}

elPat.addEventListener('input', run);
elTest.addEventListener('input', run);

// Default example
elPat.value = '(\\w+)@(\\w+\\.\\w+)';
elTest.value = 'Contact us at hello@example.com or support@company.org for help.';
run();
})();
</script>
</div>

---

Related tools: [Regex Tester](/tools/regex-tester/) · [Regex Cheatsheet](/tools/regex-cheatsheet/)
