---
title: "Text Statistics Analyzer"
date: 2025-05-16
description: "Free online text statistics analyzer. Instantly get word count, character count, sentence count, paragraph count, reading time, speaking time, readability scores, top keywords, and unique word percentage."
categories: ["Free Tools"]
tags: ["Text Tools", "String Processing", "Free Tools"]
slug: "text-statistics"
ShowToc: false
aliases:
  - "/tools/text-statistics/"
  - "/tools/reading-speed-calculator/"
cover:
  image: "/images/covers/text-statistics.png"
  alt: "Text Statistics Analyzer"
---

<div id="ts-app">

<style>
#ts-app {
font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
background: #0f0f13;
color: #e2e8f0;
border-radius: 12px;
padding: 24px;
margin: 0 auto;
max-width: 980px;
box-sizing: border-box;
}
#ts-app * { box-sizing: border-box; }

#ts-app h2 {
font-size: 1.05rem;
font-weight: 600;
color: #f1f5f9;
margin: 0 0 12px 0;
letter-spacing: 0.02em;
}
#ts-app h3 {
font-size: 0.82rem;
font-weight: 600;
color: #94a3b8;
margin: 0 0 10px 0;
text-transform: uppercase;
letter-spacing: 0.06em;
}

#ts-textarea {
width: 100%;
min-height: 170px;
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
line-height: 1.65;
}
#ts-textarea:focus { border-color: #6366f1; }
#ts-textarea::placeholder { color: #4a4a6a; }

.ts-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 10px;
margin-bottom: 22px;
}
.ts-btn {
padding: 7px 16px;
border-radius: 6px;
border: none;
font-size: 0.84rem;
font-weight: 600;
cursor: pointer;
font-family: inherit;
transition: background 0.15s, transform 0.1s;
}
.ts-btn:active { transform: scale(0.97); }
.ts-btn-primary { background: #6366f1; color: #fff; }
.ts-btn-primary:hover { background: #4f46e5; }
.ts-btn-danger { background: #1a1a24; color: #f87171; border: 1px solid #3d2020; }
.ts-btn-danger:hover { background: #2d1a1a; }
.ts-btn-copy { background: #1a1a24; color: #a5b4fc; border: 1px solid #2d2d4d; }
.ts-btn-copy:hover { background: #22224a; }

/* ── Main Stats Grid ── */
.ts-stats-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
gap: 10px;
margin-bottom: 20px;
}
.ts-stat-card {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 12px 14px;
text-align: center;
}
.ts-stat-value {
font-size: 1.45rem;
font-weight: 700;
color: #a5b4fc;
line-height: 1.2;
}
.ts-stat-label {
font-size: 0.73rem;
color: #64748b;
margin-top: 4px;
line-height: 1.35;
}

/* ── Time Cards ── */
.ts-time-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
gap: 10px;
margin-bottom: 20px;
}
.ts-time-card {
background: #161b2e;
border: 1px solid #1e2a4a;
border-radius: 8px;
padding: 12px 16px;
display: flex;
align-items: center;
gap: 12px;
}
.ts-time-icon { font-size: 1.4rem; line-height: 1; }
.ts-time-val {
font-size: 1.1rem;
font-weight: 700;
color: #7dd3fc;
}
.ts-time-desc { font-size: 0.73rem; color: #64748b; margin-top: 2px; }

/* ── Readability Section ── */
.ts-readability-wrap {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 16px;
margin-bottom: 20px;
}
.ts-scores-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
margin-top: 10px;
}
.ts-score-block { }
.ts-score-label {
font-size: 0.75rem;
color: #64748b;
margin-bottom: 6px;
}
.ts-score-num {
font-size: 1.6rem;
font-weight: 700;
color: #f1f5f9;
line-height: 1;
}
.ts-score-desc {
font-size: 0.78rem;
color: #94a3b8;
margin-top: 5px;
}
.ts-rbar-track {
background: #0f0f18;
border-radius: 99px;
height: 8px;
margin: 8px 0 4px;
overflow: hidden;
}
.ts-rbar-fill {
height: 100%;
border-radius: 99px;
transition: width 0.4s ease, background 0.4s;
}
.ts-rbar-labels {
display: flex;
justify-content: space-between;
font-size: 0.68rem;
color: #475569;
}

/* ── Keywords Section ── */
.ts-section {
background: #1a1a24;
border: 1px solid #2d2d3d;
border-radius: 8px;
padding: 16px;
margin-bottom: 20px;
}
.ts-table {
width: 100%;
border-collapse: collapse;
font-size: 0.85rem;
}
.ts-table th {
text-align: left;
color: #64748b;
font-size: 0.73rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.05em;
padding: 6px 10px;
border-bottom: 1px solid #2d2d3d;
}
.ts-table td {
padding: 7px 10px;
color: #e2e8f0;
border-bottom: 1px solid #1e1e2c;
}
.ts-table tr:last-child td { border-bottom: none; }
.ts-table tr:hover td { background: #20202e; }
.ts-density-bar {
display: inline-block;
height: 6px;
border-radius: 3px;
background: #6366f1;
vertical-align: middle;
margin-right: 6px;
transition: width 0.3s;
}

/* ── Unique Words Badge ── */
.ts-unique-badge {
display: inline-flex;
align-items: center;
gap: 8px;
background: #12192e;
border: 1px solid #1e2a4a;
border-radius: 8px;
padding: 10px 16px;
margin-bottom: 20px;
font-size: 0.88rem;
color: #94a3b8;
}
.ts-unique-pct {
font-size: 1.4rem;
font-weight: 700;
color: #34d399;
}

.ts-empty {
color: #3a3a5a;
font-size: 0.84rem;
text-align: center;
padding: 14px 0;
}

@media (max-width: 600px) {
#ts-app { padding: 16px 12px; }
.ts-stats-grid { grid-template-columns: repeat(2, 1fr); }
.ts-time-grid { grid-template-columns: 1fr 1fr; }
.ts-scores-row { grid-template-columns: 1fr; }
}
</style>

<h2>Paste or type your text below</h2>

<textarea id="ts-textarea" placeholder="Paste or type your text here to get comprehensive statistics instantly…"></textarea>

<div class="ts-toolbar">
<button class="ts-btn ts-btn-copy" onclick="tsCopyText()">Copy Text</button>
<button class="ts-btn ts-btn-danger" onclick="tsClear()">Clear</button>
</div>

<!-- Core Stats -->
<div class="ts-stats-grid">
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-words">0</div>
<div class="ts-stat-label">Words</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-chars">0</div>
<div class="ts-stat-label">Characters<br>(with spaces)</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-chars-no">0</div>
<div class="ts-stat-label">Characters<br>(no spaces)</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-sentences">0</div>
<div class="ts-stat-label">Sentences</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-paragraphs">0</div>
<div class="ts-stat-label">Paragraphs</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-avg-word">0.0</div>
<div class="ts-stat-label">Avg Word<br>Length</div>
</div>
</div>

<!-- Unique Words -->
<div class="ts-unique-badge">
<span class="ts-unique-pct" id="ts-unique-pct">0%</span>
<span>unique words &nbsp;(<span id="ts-unique-count">0</span> of <span id="ts-unique-total">0</span>)</span>
</div>

<!-- Reading / Speaking Time -->
<div class="ts-time-grid">
<div class="ts-time-card">
<div class="ts-time-icon">&#128214;</div>
<div>
<div class="ts-time-val" id="ts-read-time">0 sec</div>
<div class="ts-time-desc">Reading time (225 WPM)</div>
</div>
</div>
<div class="ts-time-card">
<div class="ts-time-icon">&#127897;</div>
<div>
<div class="ts-time-val" id="ts-speak-time">0 sec</div>
<div class="ts-time-desc">Speaking time (130 WPM)</div>
</div>
</div>
</div>

<!-- Readability Scores -->
<div class="ts-readability-wrap">
<h3>Readability Scores</h3>
<div class="ts-scores-row">
<!-- Flesch Reading Ease -->
<div class="ts-score-block">
<div class="ts-score-label">Flesch Reading Ease (0–100, higher = easier)</div>
<div class="ts-score-num" id="ts-fre-score">—</div>
<div class="ts-rbar-track">
<div class="ts-rbar-fill" id="ts-fre-fill" style="width:0%;background:#6366f1;"></div>
</div>
<div class="ts-rbar-labels"><span>0 Hard</span><span>60 Std</span><span>100 Easy</span></div>
<div class="ts-score-desc" id="ts-fre-desc">Enter text to calculate</div>
</div>
<!-- Flesch-Kincaid Grade Level -->
<div class="ts-score-block">
<div class="ts-score-label">Flesch-Kincaid Grade Level (US school grade)</div>
<div class="ts-score-num" id="ts-fkg-score">—</div>
<div class="ts-rbar-track">
<div class="ts-rbar-fill" id="ts-fkg-fill" style="width:0%;background:#6366f1;"></div>
</div>
<div class="ts-rbar-labels"><span>K (0)</span><span>8th</span><span>16+ (College)</span></div>
<div class="ts-score-desc" id="ts-fkg-desc">Enter text to calculate</div>
</div>
</div>
</div>

<!-- Top Keywords -->
<div class="ts-section">
<h3>Top Keywords</h3>
<div id="ts-keywords-wrap"><div class="ts-empty">Enter text to see keyword analysis</div></div>
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
'also','any','get','got','use','used','one','two','three','new','good','like'
]);

function getWords(t) { return t.match(/\b[a-zA-Z']+\b/g) || []; }

function getSentences(t) {
var s = t.trim();
if (!s) return 0;
var m = s.match(/[^.!?]*[.!?]+/g);
return m ? m.length : (s.length > 0 ? 1 : 0);
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

function computeReadability(words, sentences) {
if (!words.length || !sentences) return null;
var syl = words.reduce(function(a,w){ return a + countSyllables(w); }, 0);
var asl = words.length / sentences;   // avg sentence length
var asw = syl / words.length;         // avg syllables per word
// Flesch Reading Ease
var fre = 206.835 - 1.015 * asl - 84.6 * asw;
fre = Math.round(Math.max(0, Math.min(100, fre)));
// Flesch-Kincaid Grade Level
var fkg = 0.39 * asl + 11.8 * asw - 15.59;
fkg = Math.max(0, fkg);
return { fre: fre, fkg: parseFloat(fkg.toFixed(1)) };
}

function freLabel(s) {
if (s >= 90) return 'Very Easy — 5th grade';
if (s >= 80) return 'Easy — 6th grade';
if (s >= 70) return 'Fairly Easy — 7th grade';
if (s >= 60) return 'Standard — 8th–9th grade';
if (s >= 50) return 'Fairly Difficult — 10th–12th grade';
if (s >= 30) return 'Difficult — College level';
return 'Very Difficult — Professional';
}

function freColor(s) {
if (s >= 70) return '#4ade80';
if (s >= 50) return '#facc15';
if (s >= 30) return '#fb923c';
return '#f87171';
}

function fkgLabel(g) {
if (g <= 1) return 'Kindergarten';
if (g <= 6) return 'Elementary school';
if (g <= 8) return 'Middle school';
if (g <= 12) return 'High school';
if (g <= 16) return 'College level';
return 'Graduate / Professional';
}

function fkgColor(g) {
if (g <= 6) return '#4ade80';
if (g <= 9) return '#facc15';
if (g <= 12) return '#fb923c';
return '#f87171';
}

function esc(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function analyze() {
var text = document.getElementById('ts-textarea').value;
var words = getWords(text);
var wc = words.length;
var sentences = getSentences(text);
var paragraphs = getParagraphs(text);

var avgLen = wc > 0
? (words.reduce(function(a,w){ return a + w.replace(/'/g,'').length; }, 0) / wc).toFixed(1)
: '0.0';

// Unique words
var lower = words.map(function(w){ return w.toLowerCase(); });
var uniqueSet = new Set(lower);
var uniqueCount = uniqueSet.size;
var uniquePct = wc > 0 ? Math.round((uniqueCount / wc) * 100) : 0;

// Core stats
document.getElementById('ts-words').textContent = wc.toLocaleString();
document.getElementById('ts-chars').textContent = text.length.toLocaleString();
document.getElementById('ts-chars-no').textContent = text.replace(/\s/g,'').length.toLocaleString();
document.getElementById('ts-sentences').textContent = sentences.toLocaleString();
document.getElementById('ts-paragraphs').textContent = paragraphs.toLocaleString();
document.getElementById('ts-avg-word').textContent = avgLen;

// Unique words
document.getElementById('ts-unique-pct').textContent = uniquePct + '%';
document.getElementById('ts-unique-count').textContent = uniqueCount.toLocaleString();
document.getElementById('ts-unique-total').textContent = wc.toLocaleString();

// Time
document.getElementById('ts-read-time').textContent = formatTime(wc / 225);
document.getElementById('ts-speak-time').textContent = formatTime(wc / 130);

// Readability
var rd = computeReadability(words, sentences);
var freScoreEl = document.getElementById('ts-fre-score');
var freDescEl  = document.getElementById('ts-fre-desc');
var freFillEl  = document.getElementById('ts-fre-fill');
var fkgScoreEl = document.getElementById('ts-fkg-score');
var fkgDescEl  = document.getElementById('ts-fkg-desc');
var fkgFillEl  = document.getElementById('ts-fkg-fill');

if (!rd) {
freScoreEl.textContent = '\u2014'; freDescEl.textContent = 'Enter text to calculate';
freFillEl.style.width = '0%'; freFillEl.style.background = '#6366f1';
fkgScoreEl.textContent = '\u2014'; fkgDescEl.textContent = 'Enter text to calculate';
fkgFillEl.style.width = '0%'; fkgFillEl.style.background = '#6366f1';
} else {
freScoreEl.textContent = rd.fre;
freDescEl.textContent = freLabel(rd.fre);
freFillEl.style.width = rd.fre + '%';
freFillEl.style.background = freColor(rd.fre);

fkgScoreEl.textContent = rd.fkg;
fkgDescEl.textContent = fkgLabel(rd.fkg);
// Grade 0–16 mapped to 0–100%
var fkgPct = Math.min(100, Math.round((rd.fkg / 16) * 100));
fkgFillEl.style.width = fkgPct + '%';
fkgFillEl.style.background = fkgColor(rd.fkg);
}

// Keywords
var wrap = document.getElementById('ts-keywords-wrap');
if (!wc) {
wrap.innerHTML = '<div class="ts-empty">Enter text to see keyword analysis</div>';
return;
}
var freq = {};
lower.forEach(function(lw) {
if (!STOP.has(lw) && lw.replace(/'/g,'').length > 1) {
freq[lw] = (freq[lw] || 0) + 1;
}
});
var sorted = Object.keys(freq).sort(function(a,b){ return freq[b]-freq[a]; }).slice(0, 10);
if (!sorted.length) {
wrap.innerHTML = '<div class="ts-empty">No significant keywords found</div>';
return;
}
var maxC = freq[sorted[0]];
var html = '<table class="ts-table"><thead><tr><th>#</th><th>Keyword</th><th>Count</th><th>Density</th></tr></thead><tbody>';
sorted.forEach(function(word, i) {
var c = freq[word];
var d = ((c / wc) * 100).toFixed(2);
var bw = Math.round((c / maxC) * 90);
html += '<tr>'
+ '<td style="color:#475569;">' + (i+1) + '</td>'
+ '<td style="color:#a5b4fc;font-weight:600;">' + esc(word) + '</td>'
+ '<td>' + c + '</td>'
+ '<td><span class="ts-density-bar" style="width:' + bw + 'px"></span>' + d + '%</td>'
+ '</tr>';
});
html += '</tbody></table>';
wrap.innerHTML = html;
}

window.tsClear = function() {
document.getElementById('ts-textarea').value = '';
analyze();
};

window.tsCopyText = function() {
var ta = document.getElementById('ts-textarea');
ta.select();
try { document.execCommand('copy'); } catch(e) {}
ta.setSelectionRange(0, 0);
};

document.getElementById('ts-textarea').addEventListener('input', analyze);
analyze();
})();
</script>

> Count words → [Word Counter](/tools/word-counter/)
> Analyze frequency → [Word Frequency](/tools/word-frequency/)

</div>

## Related Articles

- [AI Writing Tools Comparison 2026: Best Options Ranked and Reviewed](/posts/ai-writing-tools-comparison-2026/)
- [Claude AI vs ChatGPT Comparison 2026](/posts/claude-ai-vs-chatgpt-comparison-2026/)
- [AI Prompt Engineering Tips for Beginners 2026](/posts/ai-prompt-engineering-tips-for-beginners-2026/)
