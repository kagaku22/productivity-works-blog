---
title: "Word Frequency Counter"
date: 2025-05-16
description: "Free online word frequency counter. Analyze text to find most common words, phrases, and n-grams — with sortable table and word cloud visualization."
categories: ["Free Tools"]
slug: "word-frequency-counter"
ShowToc: false
cover:
  image: "/images/covers/word-frequency-counter.png"
  alt: "Word Frequency Counter"
---

<div id="wf-app">
<style>
#wf-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 900px;
margin: 0 auto;
color: #e2e8f0;
}
#wf-app * {
box-sizing: border-box;
}
#wf-app .wf-section {
background: #1e293b;
border: 1px solid #334155;
border-radius: 10px;
padding: 20px;
margin-bottom: 20px;
}
#wf-app label {
display: block;
font-size: 0.85rem;
color: #94a3b8;
margin-bottom: 6px;
font-weight: 500;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#wf-app textarea {
width: 100%;
height: 200px;
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
color: #e2e8f0;
font-size: 0.95rem;
padding: 12px;
resize: vertical;
outline: none;
font-family: inherit;
line-height: 1.6;
}
#wf-app textarea:focus {
border-color: #6366f1;
}
#wf-app .wf-options {
display: flex;
flex-wrap: wrap;
gap: 16px;
margin-top: 14px;
align-items: center;
}
#wf-app .wf-checkbox-group {
display: flex;
align-items: center;
gap: 7px;
cursor: pointer;
font-size: 0.9rem;
color: #cbd5e1;
}
#wf-app .wf-checkbox-group input[type="checkbox"] {
width: 16px;
height: 16px;
accent-color: #6366f1;
cursor: pointer;
}
#wf-app .wf-btn-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-top: 16px;
}
#wf-app button {
padding: 10px 22px;
border-radius: 7px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
border: none;
transition: background 0.15s, transform 0.1s;
}
#wf-app button:active {
transform: scale(0.97);
}
#wf-app .wf-btn-primary {
background: #6366f1;
color: #fff;
}
#wf-app .wf-btn-primary:hover {
background: #4f46e5;
}
#wf-app .wf-btn-secondary {
background: #334155;
color: #e2e8f0;
}
#wf-app .wf-btn-secondary:hover {
background: #475569;
}
#wf-app .wf-btn-danger {
background: #1e293b;
color: #94a3b8;
border: 1px solid #334155;
}
#wf-app .wf-btn-danger:hover {
background: #334155;
color: #e2e8f0;
}
#wf-app .wf-stats-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
gap: 12px;
margin-bottom: 20px;
}
#wf-app .wf-stat-card {
background: #0f172a;
border: 1px solid #334155;
border-radius: 8px;
padding: 14px 18px;
text-align: center;
}
#wf-app .wf-stat-value {
font-size: 1.8rem;
font-weight: 700;
color: #818cf8;
line-height: 1.1;
}
#wf-app .wf-stat-label {
font-size: 0.78rem;
color: #64748b;
margin-top: 4px;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#wf-app .wf-tabs {
display: flex;
gap: 4px;
border-bottom: 1px solid #334155;
margin-bottom: 18px;
flex-wrap: wrap;
}
#wf-app .wf-tab {
padding: 8px 18px;
border-radius: 7px 7px 0 0;
font-size: 0.88rem;
font-weight: 600;
cursor: pointer;
border: 1px solid transparent;
border-bottom: none;
background: transparent;
color: #64748b;
transition: color 0.15s, background 0.15s;
}
#wf-app .wf-tab:hover {
color: #cbd5e1;
}
#wf-app .wf-tab.active {
background: #1e293b;
border-color: #334155;
color: #818cf8;
}
#wf-app .wf-tab-panel {
display: none;
}
#wf-app .wf-tab-panel.active {
display: block;
}
#wf-app .wf-table-wrap {
overflow-x: auto;
}
#wf-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
}
#wf-app th {
background: #0f172a;
color: #94a3b8;
font-size: 0.78rem;
text-transform: uppercase;
letter-spacing: 0.05em;
padding: 10px 12px;
text-align: left;
border-bottom: 1px solid #334155;
cursor: pointer;
user-select: none;
white-space: nowrap;
}
#wf-app th:hover {
color: #e2e8f0;
}
#wf-app th .wf-sort-icon {
margin-left: 5px;
opacity: 0.4;
font-style: normal;
}
#wf-app th.sort-asc .wf-sort-icon,
#wf-app th.sort-desc .wf-sort-icon {
opacity: 1;
color: #818cf8;
}
#wf-app td {
padding: 9px 12px;
border-bottom: 1px solid #1e293b;
color: #cbd5e1;
}
#wf-app tr:hover td {
background: #1e293b;
}
#wf-app .wf-bar-cell {
width: 120px;
}
#wf-app .wf-bar-bg {
background: #0f172a;
border-radius: 4px;
height: 8px;
overflow: hidden;
}
#wf-app .wf-bar-fill {
background: linear-gradient(90deg, #6366f1, #818cf8);
height: 100%;
border-radius: 4px;
transition: width 0.3s;
}
#wf-app .wf-rank {
color: #475569;
font-size: 0.8rem;
}
#wf-app canvas#wf-cloud {
display: block;
width: 100%;
max-width: 860px;
border-radius: 8px;
background: #0f172a;
border: 1px solid #334155;
margin: 0 auto;
}
#wf-app .wf-empty {
text-align: center;
color: #475569;
padding: 40px 20px;
font-size: 0.95rem;
}
#wf-app .wf-top20-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 10px;
}
#wf-app .wf-top20-item {
background: #0f172a;
border: 1px solid #334155;
border-radius: 7px;
padding: 10px 14px;
display: flex;
align-items: center;
gap: 10px;
}
#wf-app .wf-top20-rank {
font-size: 0.72rem;
font-weight: 700;
color: #6366f1;
background: #1e293b;
border-radius: 5px;
padding: 2px 7px;
min-width: 28px;
text-align: center;
}
#wf-app .wf-top20-word {
font-weight: 600;
color: #e2e8f0;
flex: 1;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}
#wf-app .wf-top20-count {
color: #818cf8;
font-size: 0.85rem;
font-weight: 600;
}
#wf-app .wf-section-title {
font-size: 1rem;
font-weight: 700;
color: #e2e8f0;
margin: 0 0 14px 0;
}
#wf-app .wf-export-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-top: 10px;
}
#wf-app .wf-notice {
font-size: 0.82rem;
color: #64748b;
margin-top: 8px;
}
@media (max-width: 600px) {
#wf-app .wf-stats-grid {
grid-template-columns: repeat(2, 1fr);
}
#wf-app .wf-bar-cell {
display: none;
}
}
</style>

<!-- INPUT SECTION -->
<div class="wf-section">
<label for="wf-input">Paste or type your text below</label>
<textarea id="wf-input" placeholder="Paste your text here to analyze word frequency..."></textarea>

<div class="wf-options">
<label class="wf-checkbox-group">
<input type="checkbox" id="wf-case-insensitive" checked>
Case-insensitive
</label>
<label class="wf-checkbox-group">
<input type="checkbox" id="wf-stop-words">
Exclude stop words
</label>
<label class="wf-checkbox-group">
<input type="checkbox" id="wf-show-ngrams" checked>
Show n-gram analysis
</label>
</div>

<div class="wf-btn-row">
<button class="wf-btn-primary" onclick="wfAnalyze()">Analyze Text</button>
<button class="wf-btn-danger" onclick="wfClear()">Clear</button>
</div>
</div>

<!-- RESULTS SECTION -->
<div class="wf-section" id="wf-results" style="display:none;">

<!-- STATS -->
<div class="wf-stats-grid" id="wf-stats"></div>

<!-- TABS -->
<div class="wf-tabs">
<button class="wf-tab active" onclick="wfSwitchTab('top20', this)">Top 20 Words</button>
<button class="wf-tab" onclick="wfSwitchTab('table', this)">Full Table</button>
<button class="wf-tab" onclick="wfSwitchTab('ngrams', this)">N-grams</button>
<button class="wf-tab" onclick="wfSwitchTab('cloud', this)">Word Cloud</button>
</div>

<!-- TOP 20 -->
<div class="wf-tab-panel active" id="wf-panel-top20">
<p class="wf-section-title">Top 20 Most Common Words</p>
<div class="wf-top20-grid" id="wf-top20"></div>
</div>

<!-- FULL TABLE -->
<div class="wf-tab-panel" id="wf-panel-table">
<div class="wf-export-row">
<button class="wf-btn-secondary" onclick="wfExportCSV('words')">Export Words CSV</button>
</div>
<br>
<div class="wf-table-wrap">
<table id="wf-table">
<thead>
<tr>
<th data-col="rank" onclick="wfSort('rank', this)">#<i class="wf-sort-icon">&#8597;</i></th>
<th data-col="word" onclick="wfSort('word', this)">Word<i class="wf-sort-icon">&#8597;</i></th>
<th data-col="count" onclick="wfSort('count', this)">Count<i class="wf-sort-icon">&#8597;</i></th>
<th data-col="pct" onclick="wfSort('pct', this)">%<i class="wf-sort-icon">&#8597;</i></th>
<th class="wf-bar-cell">Bar</th>
</tr>
</thead>
<tbody id="wf-table-body"></tbody>
</table>
</div>
<p class="wf-notice" id="wf-table-notice"></p>
</div>

<!-- N-GRAMS -->
<div class="wf-tab-panel" id="wf-panel-ngrams">
<div class="wf-export-row">
<button class="wf-btn-secondary" onclick="wfExportCSV('bigrams')">Export Bigrams CSV</button>
<button class="wf-btn-secondary" onclick="wfExportCSV('trigrams')">Export Trigrams CSV</button>
</div>
<br>
<p class="wf-section-title">Top Bigrams (2-word phrases)</p>
<div class="wf-table-wrap">
<table>
<thead>
<tr>
<th>#</th><th>Phrase</th><th>Count</th><th>%</th><th class="wf-bar-cell">Bar</th>
</tr>
</thead>
<tbody id="wf-bigram-body"></tbody>
</table>
</div>
<br>
<p class="wf-section-title">Top Trigrams (3-word phrases)</p>
<div class="wf-table-wrap">
<table>
<thead>
<tr>
<th>#</th><th>Phrase</th><th>Count</th><th>%</th><th class="wf-bar-cell">Bar</th>
</tr>
</thead>
<tbody id="wf-trigram-body"></tbody>
</table>
</div>
</div>

<!-- WORD CLOUD -->
<div class="wf-tab-panel" id="wf-panel-cloud">
<canvas id="wf-cloud" height="420"></canvas>
<p class="wf-notice" style="text-align:center;margin-top:8px;">Font size is proportional to word frequency. Top 60 words shown.</p>
</div>

</div>

<script>
(function() {

// ── STOP WORDS ──────────────────────────────────────────────────────────────
var STOP_WORDS = new Set([
'the','a','an','and','or','but','in','on','at','to','for','of','with',
'by','from','up','about','into','through','during','is','are','was','were',
'be','been','being','have','has','had','do','does','did','will','would',
'could','should','may','might','shall','can','it','its','this','that',
'these','those','i','you','he','she','we','they','me','him','her','us',
'them','my','your','his','our','their','what','which','who','whom','when',
'where','why','how','all','both','each','few','more','most','other','some',
'such','no','not','only','same','so','than','too','very','just','as','if',
'then','now','out','there','here','any','also','s','t','re','ve','ll','d','m'
]);

// ── STATE ────────────────────────────────────────────────────────────────────
var _wordData   = [];
var _bigramData = [];
var _trigramData= [];
var _sortCol    = 'count';
var _sortAsc    = false;

// ── TOKENIZE ─────────────────────────────────────────────────────────────────
function tokenize(text, caseInsensitive) {
var t = caseInsensitive ? text.toLowerCase() : text;
return t.match(/[a-zA-Z\u00C0-\u024F]+(?:[''][a-zA-Z]+)*/g) || [];
}

function countStats(text) {
var chars     = text.length;
var sentences = (text.match(/[.!?]+/g) || []).length || (text.trim().length > 0 ? 1 : 0);
return { chars: chars, sentences: sentences };
}

function buildFreqMap(tokens, excludeStop) {
var map = {};
tokens.forEach(function(w) {
if (excludeStop && STOP_WORDS.has(w.toLowerCase())) return;
if (w.length === 0) return;
map[w] = (map[w] || 0) + 1;
});
return map;
}

function buildNgrams(tokens, n, excludeStop) {
var map = {};
for (var i = 0; i <= tokens.length - n; i++) {
var gram = tokens.slice(i, i + n);
// skip if any token is a stop word (when option enabled)
if (excludeStop && gram.some(function(w){ return STOP_WORDS.has(w.toLowerCase()); })) continue;
var key = gram.join(' ');
map[key] = (map[key] || 0) + 1;
}
return map;
}

function freqMapToArray(map, totalTokens) {
return Object.keys(map).map(function(w, i) {
return { word: w, count: map[w], pct: totalTokens > 0 ? (map[w] / totalTokens * 100) : 0 };
}).sort(function(a,b){ return b.count - a.count; });
}

// ── ANALYZE ──────────────────────────────────────────────────────────────────
window.wfAnalyze = function() {
var text        = document.getElementById('wf-input').value;
var caseI       = document.getElementById('wf-case-insensitive').checked;
var stopW       = document.getElementById('wf-stop-words').checked;
var showNgrams  = document.getElementById('wf-show-ngrams').checked;

if (!text.trim()) {
alert('Please paste some text first.');
return;
}

var allTokens    = tokenize(text, caseI);
var filtTokens   = allTokens.filter(function(w){ return !(stopW && STOP_WORDS.has(w.toLowerCase())) && w.length > 0; });
var uniqueWords  = new Set(filtTokens).size;
var stats        = countStats(text);
var freqMap      = buildFreqMap(allTokens, stopW);
var totalWords   = filtTokens.length;

_wordData   = freqMapToArray(freqMap, totalWords).map(function(d,i){ return Object.assign(d,{rank:i+1}); });
_bigramData = freqMapToArray(buildNgrams(allTokens, 2, stopW), totalWords);
_trigramData= freqMapToArray(buildNgrams(allTokens, 3, stopW), totalWords);

// STATS CARDS
var statCards = [
{ label: 'Total Words',    value: totalWords.toLocaleString() },
{ label: 'Unique Words',   value: uniqueWords.toLocaleString() },
{ label: 'Characters',     value: stats.chars.toLocaleString() },
{ label: 'Sentences',      value: stats.sentences.toLocaleString() },
];
document.getElementById('wf-stats').innerHTML = statCards.map(function(s){
return '<div class="wf-stat-card"><div class="wf-stat-value">'+s.value+'</div><div class="wf-stat-label">'+s.label+'</div></div>';
}).join('');

renderTop20();
renderTable(_wordData);
renderNgrams();
renderCloud(_wordData.slice(0, 60));

document.getElementById('wf-results').style.display = 'block';
document.getElementById('wf-results').scrollIntoView({ behavior: 'smooth', block: 'start' });
};

// ── TOP 20 ───────────────────────────────────────────────────────────────────
function renderTop20() {
var top = _wordData.slice(0, 20);
document.getElementById('wf-top20').innerHTML = top.map(function(d,i){
return '<div class="wf-top20-item">'
+'<span class="wf-top20-rank">'+(i+1)+'</span>'
+'<span class="wf-top20-word">'+escHtml(d.word)+'</span>'
+'<span class="wf-top20-count">'+d.count+'</span>'
+'</div>';
}).join('') || '<p class="wf-empty">No data.</p>';
}

// ── TABLE ────────────────────────────────────────────────────────────────────
function renderTable(data) {
var top = data.slice(0, 500);
var maxCount = top.length > 0 ? top[0].count : 1;
document.getElementById('wf-table-body').innerHTML = top.map(function(d,i){
var pct  = d.pct.toFixed(2);
var barW = Math.round(d.count / maxCount * 100);
return '<tr>'
+'<td class="wf-rank">'+(i+1)+'</td>'
+'<td>'+escHtml(d.word)+'</td>'
+'<td>'+d.count+'</td>'
+'<td>'+pct+'%</td>'
+'<td class="wf-bar-cell"><div class="wf-bar-bg"><div class="wf-bar-fill" style="width:'+barW+'%"></div></div></td>'
+'</tr>';
}).join('');
var notice = data.length > 500 ? 'Showing top 500 of '+data.length+' unique words. Export CSV for full data.' : 'Showing all '+data.length+' unique words.';
document.getElementById('wf-table-notice').textContent = notice;
}

// ── SORT ─────────────────────────────────────────────────────────────────────
window.wfSort = function(col, th) {
if (_sortCol === col) {
_sortAsc = !_sortAsc;
} else {
_sortCol = col;
_sortAsc = col === 'word';
}
document.querySelectorAll('#wf-table th').forEach(function(h){
h.classList.remove('sort-asc','sort-desc');
});
th.classList.add(_sortAsc ? 'sort-asc' : 'sort-desc');

var sorted = _wordData.slice().sort(function(a,b){
var av = a[col], bv = b[col];
if (typeof av === 'string') return _sortAsc ? av.localeCompare(bv) : bv.localeCompare(av);
return _sortAsc ? av - bv : bv - av;
});
renderTable(sorted);
};

// ── N-GRAMS ──────────────────────────────────────────────────────────────────
function renderNgramTable(data, bodyId, limit) {
limit = limit || 50;
var top = data.slice(0, limit);
var maxC = top.length > 0 ? top[0].count : 1;
document.getElementById(bodyId).innerHTML = top.map(function(d,i){
var barW = Math.round(d.count / maxC * 100);
return '<tr>'
+'<td class="wf-rank">'+(i+1)+'</td>'
+'<td>'+escHtml(d.word)+'</td>'
+'<td>'+d.count+'</td>'
+'<td>'+d.pct.toFixed(2)+'%</td>'
+'<td class="wf-bar-cell"><div class="wf-bar-bg"><div class="wf-bar-fill" style="width:'+barW+'%"></div></div></td>'
+'</tr>';
}).join('') || '<tr><td colspan="5" class="wf-empty">Not enough data for n-grams.</td></tr>';
}

function renderNgrams() {
renderNgramTable(_bigramData,  'wf-bigram-body',  40);
renderNgramTable(_trigramData, 'wf-trigram-body', 40);
}

// ── WORD CLOUD ───────────────────────────────────────────────────────────────
function renderCloud(words) {
var canvas = document.getElementById('wf-cloud');
var W = canvas.parentElement.clientWidth || 860;
canvas.width  = W;
canvas.height = 420;
var ctx = canvas.getContext('2d');
ctx.clearRect(0,0,W,420);

if (!words || words.length === 0) {
ctx.fillStyle = '#475569';
ctx.font = '18px system-ui';
ctx.textAlign = 'center';
ctx.fillText('No words to display', W/2, 210);
return;
}

var maxC  = words[0].count;
var minC  = words[words.length-1].count;
var range = Math.max(maxC - minC, 1);

var palette = ['#818cf8','#6366f1','#a5b4fc','#c7d2fe','#e0e7ff','#94a3b8','#cbd5e1'];
var placed  = [];

function overlap(r1, r2) {
return !(r1.x + r1.w < r2.x || r2.x + r2.w < r1.x ||
r1.y + r1.h < r2.y || r2.y + r2.h < r1.y);
}

function tryPlace(word, fontSize) {
ctx.font = 'bold ' + fontSize + 'px system-ui';
var tw = ctx.measureText(word).width;
var th = fontSize;
// spiral placement
var cx = W / 2, cy = 210;
for (var step = 0; step < 300; step++) {
var angle = step * 0.45;
var radius= step * 2.0;
var tx = cx + radius * Math.cos(angle) - tw/2;
var ty = cy + radius * Math.sin(angle) + th/2;
var rect = { x: tx-2, y: ty-th-2, w: tw+4, h: th+4 };
if (rect.x < 2 || rect.y < 2 || rect.x+rect.w > W-2 || rect.y+rect.h > 418) continue;
var ok = true;
for (var p = 0; p < placed.length; p++) {
if (overlap(rect, placed[p])) { ok=false; break; }
}
if (ok) {
placed.push(rect);
return { x: tx, y: ty };
}
}
return null;
}

words.forEach(function(d, i) {
var t = (d.count - minC) / range;
var fontSize = Math.round(14 + t * 46);
var pos = tryPlace(d.word, fontSize);
if (!pos) return;
ctx.font = 'bold ' + fontSize + 'px system-ui';
ctx.fillStyle = palette[i % palette.length];
ctx.textAlign = 'left';
ctx.textBaseline = 'alphabetic';
ctx.fillText(d.word, pos.x, pos.y);
});
}

// ── TABS ─────────────────────────────────────────────────────────────────────
window.wfSwitchTab = function(name, btn) {
document.querySelectorAll('#wf-app .wf-tab-panel').forEach(function(p){ p.classList.remove('active'); });
document.querySelectorAll('#wf-app .wf-tab').forEach(function(b){ b.classList.remove('active'); });
document.getElementById('wf-panel-'+name).classList.add('active');
btn.classList.add('active');
if (name === 'cloud') renderCloud(_wordData.slice(0,60));
};

// ── EXPORT CSV ───────────────────────────────────────────────────────────────
window.wfExportCSV = function(type) {
var rows, filename;
if (type === 'words') {
rows = [['Rank','Word','Count','Percentage']].concat(
_wordData.map(function(d,i){ return [i+1, d.word, d.count, d.pct.toFixed(4)+'%']; })
);
filename = 'word-frequency.csv';
} else if (type === 'bigrams') {
rows = [['Rank','Bigram','Count','Percentage']].concat(
_bigramData.map(function(d,i){ return [i+1, d.word, d.count, d.pct.toFixed(4)+'%']; })
);
filename = 'bigrams.csv';
} else {
rows = [['Rank','Trigram','Count','Percentage']].concat(
_trigramData.map(function(d,i){ return [i+1, d.word, d.count, d.pct.toFixed(4)+'%']; })
);
filename = 'trigrams.csv';
}
var csv = rows.map(function(r){
return r.map(function(c){ return '"'+String(c).replace(/"/g,'""')+'"'; }).join(',');
}).join('\r\n');
var blob = new Blob(['\uFEFF'+csv], { type: 'text/csv;charset=utf-8;' });
var url  = URL.createObjectURL(blob);
var a    = document.createElement('a');
a.href     = url;
a.download = filename;
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
URL.revokeObjectURL(url);
};

// ── CLEAR ────────────────────────────────────────────────────────────────────
window.wfClear = function() {
document.getElementById('wf-input').value = '';
document.getElementById('wf-results').style.display = 'none';
_wordData = []; _bigramData = []; _trigramData = [];
};

// ── HELPERS ──────────────────────────────────────────────────────────────────
function escHtml(s) {
return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

})();
</script>

</div>

---

**Related tools:**

> Convert text case → [Text Case Converter](/tools/text-case-converter/)

> Count lines of code → [Line Counter](/tools/line-counter/)

> Check text differences → [Text Diff Checker](/tools/text-diff-checker/)
