---
title: "Word Counter & Text Statistics"
date: 2025-05-16
description: "Free online word counter with reading time, keyword density, readability score, and detailed text statistics. Paste text and get instant analysis."
categories: ["Free Tools"]
slug: "word-counter"
ShowToc: false
cover:
  image: "/images/covers/word-counter.png"
  alt: "Word Counter & Text Statistics"
---

<div id="wc-app">

<style>
#wc-app {
font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
background: #0f0f13;
color: #e2e8f0;
border-radius: 12px;
padding: 24px;
margin: 0 auto;
max-width: 960px;
box-sizing: border-box;
}
#wc-app * { box-sizing: border-box; }

#wc-app h2 {
font-size: 1.05rem;
font-weight: 600;
color: #f1f5f9;
margin: 0 0 12px 0;
letter-spacing: 0.02em;
}

#wc-app h3 {
font-size: 0.85rem;
font-weight: 600;
color: #94a3b8;
margin: 0 0 10px 0;
text-transform: uppercase;
letter-spacing: 0.06em;
}

#wc-textarea {
width: 100%;
min-height: 160px;
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
color: #e2e8f0;
font-size: 0.97rem;
padding: 12px 14px;
resize: vertical;
font-family: inherit;
transition: border-color 0.2s;
outline: none;
line-height: 1.6;
}
#wc-textarea:focus { border-color: #6366f1; }
#wc-textarea::placeholder { color: #4a4a6a; }

.wc-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 10px;
margin-bottom: 20px;
}
.wc-btn {
padding: 7px 15px;
border-radius: 6px;
border: none;
font-size: 0.84rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
.wc-btn:active { transform: scale(0.97); }
.wc-btn-primary { background: #6366f1; color: #fff; }
.wc-btn-primary:hover { background: #4f46e5; }
.wc-btn-danger { background: #1a1a24; color: #f87171; border: 1px solid #3d2020; }
.wc-btn-danger:hover { background: #2d1a1a; }
.wc-btn-secondary { background: #1e293b; color: #94a3b8; border: 1px solid #2d3748; }
.wc-btn-secondary:hover { background: #253347; color: #e2e8f0; }
.wc-copy-btn { background: #1a1a24; color: #a5b4fc; border: 1px solid #2d2d4d; }
.wc-copy-btn:hover { background: #22224a; }

.wc-stats-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
gap: 10px;
margin-bottom: 20px;
}
.wc-stat-card {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 12px 14px;
text-align: center;
}
.wc-stat-value {
font-size: 1.5rem;
font-weight: 700;
color: #a5b4fc;
line-height: 1.2;
}
.wc-stat-label {
font-size: 0.74rem;
color: #64748b;
margin-top: 4px;
line-height: 1.3;
}

.wc-time-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
gap: 10px;
margin-bottom: 20px;
}
.wc-time-card {
background: #161b2e;
border: 1px solid #1e2a4a;
border-radius: 8px;
padding: 12px 16px;
display: flex;
align-items: center;
gap: 12px;
}
.wc-time-icon { font-size: 1.4rem; line-height: 1; }
.wc-time-val {
font-size: 1.1rem;
font-weight: 700;
color: #7dd3fc;
}
.wc-time-desc { font-size: 0.74rem; color: #64748b; }

.wc-readability-wrap {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 16px;
margin-bottom: 20px;
}
.wc-rbar-track {
background: #0f0f18;
border-radius: 99px;
height: 10px;
margin: 10px 0 6px;
overflow: hidden;
}
.wc-rbar-fill {
height: 100%;
border-radius: 99px;
transition: width 0.4s ease, background 0.4s;
}
.wc-rbar-labels {
display: flex;
justify-content: space-between;
font-size: 0.7rem;
color: #475569;
}
.wc-rbar-score {
font-size: 1.2rem;
font-weight: 700;
color: #f1f5f9;
}
.wc-rbar-level {
font-size: 0.82rem;
color: #94a3b8;
margin-top: 4px;
}

.wc-section {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 16px;
margin-bottom: 20px;
}
.wc-table {
width: 100%;
border-collapse: collapse;
font-size: 0.86rem;
}
.wc-table th {
text-align: left;
color: #64748b;
font-size: 0.75rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.05em;
padding: 6px 10px;
border-bottom: 1px solid #2d2d3d;
}
.wc-table td {
padding: 7px 10px;
color: #e2e8f0;
border-bottom: 1px solid #1e1e2c;
}
.wc-table tr:last-child td { border-bottom: none; }
.wc-table tr:hover td { background: #20202e; }
.wc-density-bar {
display: inline-block;
height: 6px;
border-radius: 3px;
background: #6366f1;
vertical-align: middle;
margin-right: 6px;
transition: width 0.3s;
}

.wc-fr-grid {
display: grid;
grid-template-columns: 1fr 1fr auto;
gap: 8px;
align-items: center;
}
.wc-fr-input {
background: #0f0f18;
border: 1px solid #2d2d3d;
border-radius: 6px;
color: #e2e8f0;
font-size: 0.9rem;
padding: 8px 12px;
outline: none;
font-family: inherit;
transition: border-color 0.2s;
}
.wc-fr-input:focus { border-color: #6366f1; }
.wc-fr-input::placeholder { color: #3a3a5a; }
.wc-fr-actions {
display: flex;
gap: 6px;
flex-wrap: wrap;
margin-top: 8px;
}
.wc-fr-info {
font-size: 0.8rem;
color: #64748b;
margin-top: 6px;
min-height: 1.2em;
}

.wc-empty {
color: #3a3a5a;
font-size: 0.85rem;
text-align: center;
padding: 12px 0;
}

@media (max-width: 600px) {
#wc-app { padding: 16px 12px; }
.wc-stats-grid { grid-template-columns: repeat(2, 1fr); }
.wc-time-grid { grid-template-columns: 1fr 1fr; }
.wc-fr-grid { grid-template-columns: 1fr 1fr; }
.wc-fr-grid > .wc-btn { grid-column: 1 / -1; }
}
</style>

<h2>Paste or type your text below</h2>

<textarea id="wc-textarea" placeholder="Paste or type your text here to get instant statistics..."></textarea>

<div class="wc-toolbar">
<button class="wc-btn wc-copy-btn" onclick="wcCopyText()">Copy Text</button>
<button class="wc-btn wc-btn-danger" onclick="wcClear()">Clear</button>
</div>

<div class="wc-stats-grid">
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-words">0</div><div class="wc-stat-label">Words</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-chars">0</div><div class="wc-stat-label">Characters<br>(with spaces)</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-chars-no">0</div><div class="wc-stat-label">Characters<br>(no spaces)</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-sentences">0</div><div class="wc-stat-label">Sentences</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-paragraphs">0</div><div class="wc-stat-label">Paragraphs</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-avg-word">0</div><div class="wc-stat-label">Avg Word<br>Length</div></div>
</div>

<div class="wc-time-grid">
<div class="wc-time-card">
<div class="wc-time-icon">&#128214;</div>
<div>
<div class="wc-time-val" id="wc-read-time">0 sec</div>
<div class="wc-time-desc">Reading time (225 WPM)</div>
</div>
</div>
<div class="wc-time-card">
<div class="wc-time-icon">&#127897;</div>
<div>
<div class="wc-time-val" id="wc-speak-time">0 sec</div>
<div class="wc-time-desc">Speaking time (130 WPM)</div>
</div>
</div>
</div>

<div class="wc-readability-wrap">
<h3>Readability Score (Flesch-Kincaid)</h3>
<div style="display:flex;align-items:baseline;gap:12px;flex-wrap:wrap;">
<span class="wc-rbar-score" id="wc-fk-score">&#8212;</span>
<span class="wc-rbar-level" id="wc-fk-level">Enter text to calculate</span>
</div>
<div class="wc-rbar-track">
<div class="wc-rbar-fill" id="wc-rbar-fill" style="width:0%;background:#6366f1;"></div>
</div>
<div class="wc-rbar-labels">
<span>Very Difficult (0)</span>
<span>Standard (60)</span>
<span>Very Easy (100)</span>
</div>
</div>

<div class="wc-section">
<h3>Top 10 Keywords &amp; Density</h3>
<div id="wc-keywords-wrap"><div class="wc-empty">Enter text to see keyword analysis</div></div>
</div>

<div class="wc-section">
<h3>Find &amp; Replace</h3>
<div class="wc-fr-grid">
<input class="wc-fr-input" id="wc-find" placeholder="Find..." />
<input class="wc-fr-input" id="wc-replace" placeholder="Replace with..." />
<button class="wc-btn wc-btn-primary" onclick="wcReplaceAll()">Replace All</button>
</div>
<div class="wc-fr-actions">
<button class="wc-btn wc-btn-secondary" onclick="wcHighlightFind()">Count Matches</button>
<button class="wc-btn wc-btn-secondary" onclick="wcClearFrInfo()">Clear</button>
</div>
<div class="wc-fr-info" id="wc-fr-info"></div>
</div>

<script>
(function(){
var STOP = new Set([
'a','an','the','and','but','or','nor','for','yet','so','in','on','at','to',
'of','by','up','as','is','it','its','be','was','are','were','been','being',
'have','has','had','do','does','did','will','would','could','should','may',
'might','shall','can','this','that','these','those','i','you','he','she','we',
'they','my','your','his','her','our','their','me','him','us','them','what',
'which','who','when','where','why','how','all','each','every','both','few',
'more','most','other','some','such','no','not','only','own','same','than',
'too','very','just','because','if','then','there','here','about','into',
'through','during','before','after','above','below','from','with','without',
'also','any','get','got','been','use','used','one','two','three','new','good'
]);

function getWords(t) { return t.match(/\b[a-zA-Z']+\b/g) || []; }

function getSentences(t) {
var s = t.trim();
if (!s) return 0;
var m = s.match(/[^.!?]*[.!?]+/g);
if (!m) return s.length > 0 ? 1 : 0;
return m.length;
}

function getParagraphs(t) {
var s = t.trim();
if (!s) return 0;
return s.split(/\n\s*\n+/).filter(function(p){ return p.trim().length > 0; }).length || 1;
}

function formatTime(mins) {
if (mins === 0) return '0 sec';
if (mins < 1) return Math.round(mins * 60) + ' sec';
var m = Math.floor(mins);
var s = Math.round((mins - m) * 60);
if (s === 0) return m + ' min';
return m + ' min ' + s + ' sec';
}

function countSyllables(word) {
word = word.toLowerCase().replace(/[^a-z]/g, '');
if (!word) return 0;
if (word.length <= 3) return 1;
word = word.replace(/(?:[^laeiouy]es|ed|[^laeiouy]e)$/, '');
word = word.replace(/^y/, '');
var m = word.match(/[aeiouy]{1,2}/g);
return m ? Math.max(1, m.length) : 1;
}

function fleschKincaid(words, sentences) {
if (!words.length || !sentences) return null;
var syl = words.reduce(function(a, w){ return a + countSyllables(w); }, 0);
var asl = words.length / sentences;
var asw = syl / words.length;
var score = 206.835 - 1.015 * asl - 84.6 * asw;
return Math.round(Math.max(0, Math.min(100, score)));
}

function fkLabel(s) {
if (s >= 90) return 'Very Easy — 5th grade level';
if (s >= 80) return 'Easy — 6th grade level';
if (s >= 70) return 'Fairly Easy — 7th grade level';
if (s >= 60) return 'Standard — 8th–9th grade level';
if (s >= 50) return 'Fairly Difficult — 10th–12th grade level';
if (s >= 30) return 'Difficult — College level';
return 'Very Difficult — Professional level';
}

function fkColor(s) {
if (s >= 70) return '#4ade80';
if (s >= 50) return '#facc15';
if (s >= 30) return '#fb923c';
return '#f87171';
}

function esc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function analyze() {
var text = document.getElementById('wc-textarea').value;
var words = getWords(text);
var wc = words.length;
var sentences = getSentences(text);
var paragraphs = getParagraphs(text);
var avgLen = wc > 0
? (words.reduce(function(a,w){ return a + w.replace(/'/g,'').length; }, 0) / wc).toFixed(1)
: '0.0';

document.getElementById('wc-words').textContent = wc.toLocaleString();
document.getElementById('wc-chars').textContent = text.length.toLocaleString();
document.getElementById('wc-chars-no').textContent = text.replace(/\s/g,'').length.toLocaleString();
document.getElementById('wc-sentences').textContent = sentences.toLocaleString();
document.getElementById('wc-paragraphs').textContent = paragraphs.toLocaleString();
document.getElementById('wc-avg-word').textContent = avgLen;

document.getElementById('wc-read-time').textContent = formatTime(wc / 225);
document.getElementById('wc-speak-time').textContent = formatTime(wc / 130);

var fk = fleschKincaid(words, sentences);
var scoreEl = document.getElementById('wc-fk-score');
var levelEl = document.getElementById('wc-fk-level');
var fillEl  = document.getElementById('wc-rbar-fill');
if (fk === null) {
scoreEl.textContent = '\u2014';
levelEl.textContent = 'Enter text to calculate';
fillEl.style.width = '0%';
fillEl.style.background = '#6366f1';
} else {
scoreEl.textContent = fk;
levelEl.textContent = fkLabel(fk);
fillEl.style.width = fk + '%';
fillEl.style.background = fkColor(fk);
}

// Keywords
var wrap = document.getElementById('wc-keywords-wrap');
if (!wc) {
wrap.innerHTML = '<div class="wc-empty">Enter text to see keyword analysis</div>';
return;
}
var freq = {};
words.forEach(function(w) {
var lw = w.toLowerCase();
if (!STOP.has(lw) && lw.length > 1) freq[lw] = (freq[lw] || 0) + 1;
});
var sorted = Object.keys(freq).sort(function(a,b){ return freq[b]-freq[a]; }).slice(0,10);
if (!sorted.length) {
wrap.innerHTML = '<div class="wc-empty">No significant keywords found</div>';
return;
}
var maxC = freq[sorted[0]];
var html = '<table class="wc-table"><thead><tr><th>#</th><th>Word</th><th>Count</th><th>Density</th></tr></thead><tbody>';
sorted.forEach(function(word, i) {
var c = freq[word];
var d = ((c / wc) * 100).toFixed(2);
var bw = Math.round((c / maxC) * 80);
html += '<tr><td style="color:#475569;">' + (i+1) + '</td>'
+ '<td style="color:#a5b4fc;font-weight:600;">' + esc(word) + '</td>'
+ '<td>' + c + '</td>'
+ '<td><span class="wc-density-bar" style="width:' + bw + 'px"></span>' + d + '%</td></tr>';
});
html += '</tbody></table>';
wrap.innerHTML = html;
}

window.wcAnalyze = analyze;

window.wcClear = function() {
document.getElementById('wc-textarea').value = '';
document.getElementById('wc-find').value = '';
document.getElementById('wc-replace').value = '';
document.getElementById('wc-fr-info').textContent = '';
analyze();
};

window.wcCopyText = function() {
var ta = document.getElementById('wc-textarea');
ta.select();
try { document.execCommand('copy'); } catch(e) {}
ta.setSelectionRange(0,0);
};

window.wcReplaceAll = function() {
var find = document.getElementById('wc-find').value;
var repl = document.getElementById('wc-replace').value;
var info = document.getElementById('wc-fr-info');
if (!find) { info.textContent = 'Please enter a search term.'; return; }
var ta = document.getElementById('wc-textarea');
var regex = new RegExp(find.replace(/[.*+?^${}()|[\]\\]/g,'\\$&'), 'g');
var m = (ta.value.match(regex) || []).length;
if (!m) { info.textContent = 'No matches found for "' + find + '".'; return; }
ta.value = ta.value.replace(regex, repl);
info.textContent = 'Replaced ' + m + ' occurrence(s).';
analyze();
};

window.wcHighlightFind = function() {
var find = document.getElementById('wc-find').value;
var info = document.getElementById('wc-fr-info');
if (!find) { info.textContent = 'Please enter a search term.'; return; }
var regex = new RegExp(find.replace(/[.*+?^${}()|[\]\\]/g,'\\$&'), 'gi');
var m = (document.getElementById('wc-textarea').value.match(regex) || []).length;
info.textContent = m > 0
? 'Found ' + m + ' match(es) for "' + find + '".'
: 'No matches found for "' + find + '".';
};

window.wcClearFrInfo = function() {
document.getElementById('wc-find').value = '';
document.getElementById('wc-replace').value = '';
document.getElementById('wc-fr-info').textContent = '';
};

document.getElementById('wc-textarea').addEventListener('input', analyze);
analyze();
})();
</script>

> Count characters → [Character Counter](/tools/character-counter/)
> Check word frequency → [Word Frequency Counter](/tools/word-frequency-counter/)

</div>

## Related Articles

- [How to Use ChatGPT for Etsy Shop Descriptions (Complete 2026 Guide)](/posts/chatgpt-etsy-shop-descriptions/)
- [Etsy SEO: How to Generate Perfect Tags with ChatGPT (Step-by-Step)](/posts/etsy-seo-tags-chatgpt-optimization/)
- [AI Writing Tools Comparison 2026: Best Options Ranked and Reviewed](/posts/ai-writing-tools-comparison-2026/)
