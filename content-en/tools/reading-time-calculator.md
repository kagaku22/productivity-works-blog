---
title: "Reading Time Calculator"
date: 2025-05-16
description: "Calculate how long it takes to read any text. Paste your content, adjust reading speed, and get instant reading time, word count, sentence count, and readability scores."
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
slug: "reading-time-calculator"
aliases: ["/tools/reading-speed-calculator/", "/tools/reading-speed-calculator/"]
ShowToc: false
cover:
  image: "/images/covers/reading-time-calculator.png"
  alt: "Reading Time Calculator"
---

<div id="rt-app">

<style>
#rt-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1f2937;
}
#rt-app * { box-sizing: border-box; }
#rt-app h2 {
font-size: 1.25rem;
font-weight: 700;
margin: 1.5rem 0 0.75rem;
color: #92400e;
}
#rt-app .card {
background: #fff;
border: 1px solid #e5e7eb;
border-radius: 12px;
padding: 1.25rem 1.5rem;
margin-bottom: 1.25rem;
box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
#rt-app textarea {
width: 100%;
min-height: 160px;
border: 2px solid #e5e7eb;
border-radius: 8px;
padding: 0.75rem 1rem;
font-size: 0.95rem;
font-family: inherit;
resize: vertical;
transition: border-color 0.2s;
outline: none;
}
#rt-app textarea:focus { border-color: #d97706; }
#rt-app .or-divider {
text-align: center;
color: #9ca3af;
font-size: 0.85rem;
margin: 0.75rem 0;
display: flex;
align-items: center;
gap: 0.5rem;
}
#rt-app .or-divider::before,
#rt-app .or-divider::after {
content: "";
flex: 1;
height: 1px;
background: #e5e7eb;
}
#rt-app .word-count-row {
display: flex;
align-items: center;
gap: 0.75rem;
flex-wrap: wrap;
}
#rt-app .word-count-row label {
font-size: 0.9rem;
color: #374151;
font-weight: 500;
white-space: nowrap;
}
#rt-app input[type="number"] {
width: 120px;
border: 2px solid #e5e7eb;
border-radius: 8px;
padding: 0.45rem 0.75rem;
font-size: 0.95rem;
font-family: inherit;
outline: none;
transition: border-color 0.2s;
}
#rt-app input[type="number"]:focus { border-color: #d97706; }
#rt-app .speed-section {
display: flex;
align-items: center;
gap: 1rem;
flex-wrap: wrap;
}
#rt-app .speed-label {
font-size: 0.9rem;
color: #374151;
font-weight: 500;
white-space: nowrap;
}
#rt-app input[type="range"] {
flex: 1;
min-width: 140px;
accent-color: #d97706;
height: 6px;
cursor: pointer;
}
#rt-app .speed-val {
background: #fef3c7;
color: #92400e;
border-radius: 20px;
padding: 0.2rem 0.75rem;
font-size: 0.88rem;
font-weight: 700;
white-space: nowrap;
}
#rt-app .speed-presets {
display: flex;
gap: 0.5rem;
flex-wrap: wrap;
margin-top: 0.5rem;
}
#rt-app .preset-btn {
border: 1.5px solid #d97706;
background: transparent;
color: #92400e;
border-radius: 20px;
padding: 0.2rem 0.75rem;
font-size: 0.82rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#rt-app .preset-btn:hover,
#rt-app .preset-btn.active {
background: #d97706;
color: #fff;
}
#rt-app .results-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
gap: 0.75rem;
margin-bottom: 0.5rem;
}
#rt-app .result-box {
background: #fffbeb;
border: 1.5px solid #fde68a;
border-radius: 10px;
padding: 0.9rem 1rem;
text-align: center;
}
#rt-app .result-box .r-val {
font-size: 1.5rem;
font-weight: 800;
color: #d97706;
line-height: 1.1;
}
#rt-app .result-box .r-lbl {
font-size: 0.75rem;
color: #6b7280;
margin-top: 0.2rem;
}
#rt-app .progress-wrap {
margin: 1rem 0 0.25rem;
}
#rt-app .progress-label {
display: flex;
justify-content: space-between;
font-size: 0.8rem;
color: #9ca3af;
margin-bottom: 0.3rem;
}
#rt-app .progress-bar-bg {
width: 100%;
height: 14px;
background: #f3f4f6;
border-radius: 999px;
overflow: hidden;
}
#rt-app .progress-bar-fill {
height: 100%;
background: linear-gradient(90deg, #f59e0b, #d97706);
border-radius: 999px;
transition: width 0.4s ease;
min-width: 4px;
}
#rt-app .speed-comparison {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 0.6rem;
margin-top: 0.75rem;
}
#rt-app .cmp-box {
border-radius: 10px;
padding: 0.65rem 0.75rem;
text-align: center;
border: 1.5px solid #e5e7eb;
}
#rt-app .cmp-box.slow  { border-color: #fca5a5; background: #fff1f1; }
#rt-app .cmp-box.avg   { border-color: #fde68a; background: #fffbeb; }
#rt-app .cmp-box.fast  { border-color: #6ee7b7; background: #ecfdf5; }
#rt-app .cmp-box .cmp-t { font-size: 0.72rem; font-weight: 700; color: #6b7280; text-transform: uppercase; letter-spacing: 0.05em; }
#rt-app .cmp-box .cmp-v { font-size: 1.1rem; font-weight: 800; margin: 0.1rem 0; }
#rt-app .cmp-box.slow  .cmp-v { color: #dc2626; }
#rt-app .cmp-box.avg   .cmp-v { color: #d97706; }
#rt-app .cmp-box.fast  .cmp-v { color: #059669; }
#rt-app .cmp-box .cmp-wpm { font-size: 0.7rem; color: #9ca3af; }
#rt-app .book-row {
display: flex;
align-items: center;
gap: 0.75rem;
flex-wrap: wrap;
}
#rt-app .book-row label { font-size: 0.9rem; color: #374151; font-weight: 500; }
#rt-app .book-result {
margin-top: 0.75rem;
padding: 0.65rem 1rem;
background: #fffbeb;
border: 1.5px solid #fde68a;
border-radius: 8px;
font-size: 0.92rem;
color: #92400e;
font-weight: 600;
}
#rt-app .readability-section { margin-top: 0.5rem; }
#rt-app .rdbl-row {
display: flex;
gap: 1rem;
flex-wrap: wrap;
align-items: flex-start;
}
#rt-app .rdbl-item {
flex: 1;
min-width: 160px;
}
#rt-app .rdbl-item .rdbl-val {
font-size: 1.3rem;
font-weight: 800;
color: #d97706;
}
#rt-app .rdbl-item .rdbl-lbl {
font-size: 0.75rem;
color: #6b7280;
margin-top: 0.15rem;
}
#rt-app .rdbl-item .rdbl-note {
font-size: 0.78rem;
color: #374151;
margin-top: 0.1rem;
}
#rt-app .clear-btn {
background: transparent;
border: 1.5px solid #e5e7eb;
color: #6b7280;
border-radius: 8px;
padding: 0.35rem 1rem;
font-size: 0.82rem;
cursor: pointer;
transition: border-color 0.15s, color 0.15s;
float: right;
margin-top: 0.25rem;
}
#rt-app .clear-btn:hover { border-color: #d97706; color: #d97706; }
#rt-app .empty-state {
text-align: center;
color: #9ca3af;
font-size: 0.9rem;
padding: 1.5rem 0;
}
#rt-app .related-note {
margin-top: 2rem;
padding: 0.85rem 1.1rem;
background: #f9fafb;
border-left: 4px solid #d97706;
border-radius: 0 8px 8px 0;
font-size: 0.9rem;
color: #374151;
}
#rt-app .related-note a { color: #d97706; font-weight: 600; text-decoration: none; }
#rt-app .related-note a:hover { text-decoration: underline; }
@media (max-width: 500px) {
#rt-app .results-grid { grid-template-columns: 1fr 1fr; }
#rt-app .speed-comparison { grid-template-columns: 1fr; }
}
</style>

<!-- INPUT -->
<div class="card">
<h2 style="margin-top:0">Paste Your Text</h2>
<textarea id="rt-textarea" placeholder="Paste or type your text here…" oninput="rtUpdate()"></textarea>
<button class="clear-btn" onclick="rtClear()">Clear</button>
<div class="or-divider">or enter word count directly</div>
<div class="word-count-row">
<label for="rt-wc-input">Word count:</label>
<input type="number" id="rt-wc-input" min="1" max="999999" placeholder="e.g. 1500" oninput="rtUpdate()" />
<span style="font-size:0.8rem;color:#9ca3af;">(leave blank if using text above)</span>
</div>
</div>

<!-- SPEED -->
<div class="card">
<h2 style="margin-top:0">Reading Speed</h2>
<div class="speed-section">
<span class="speed-label">WPM:</span>
<input type="range" id="rt-speed" min="100" max="400" value="200" oninput="rtSpeedChange(this.value)" />
<span class="speed-val" id="rt-speed-val">200 WPM</span>
</div>
<div class="speed-presets">
<button class="preset-btn" onclick="rtSetSpeed(150)">Slow (150)</button>
<button class="preset-btn active" onclick="rtSetSpeed(200)">Average (200)</button>
<button class="preset-btn" onclick="rtSetSpeed(300)">Fast (300)</button>
<button class="preset-btn" onclick="rtSetSpeed(400)">Speed reader (400)</button>
</div>
</div>

<!-- RESULTS -->
<div class="card" id="rt-results-card">
<h2 style="margin-top:0">Results</h2>
<div id="rt-results-body">
<div class="empty-state">Paste text or enter a word count above to see results.</div>
</div>
</div>

<!-- BOOK ESTIMATE -->
<div class="card">
<h2 style="margin-top:0">Book Reading Estimate</h2>
<div class="book-row">
<label for="rt-pages">Number of pages:</label>
<input type="number" id="rt-pages" min="1" max="10000" placeholder="e.g. 300" oninput="rtBookUpdate()" />
<label for="rt-wppage">Words per page:</label>
<input type="number" id="rt-wppage" min="50" max="1000" value="250" placeholder="250" oninput="rtBookUpdate()" />
</div>
<div id="rt-book-result" class="book-result" style="display:none"></div>
</div>

<script>
(function() {
var wpm = 200;
var spkWpm = 130;

function fmtTime(minutes) {
if (minutes < 1) return "< 1 min";
if (minutes < 60) {
var m = Math.round(minutes);
return m + " min" + (m !== 1 ? "s" : "");
}
var h = Math.floor(minutes / 60);
var m = Math.round(minutes % 60);
return h + "h " + (m > 0 ? m + "m" : "");
}

function fmtNum(n) {
return n.toLocaleString();
}

function countSyllables(word) {
word = word.toLowerCase().replace(/[^a-z]/g, "");
if (!word) return 0;
if (word.length <= 3) return 1;
word = word.replace(/(?:[^laeiouy]es|ed|[^laeiouy]e)$/, "");
word = word.replace(/^y/, "");
var m = word.match(/[aeiouy]{1,2}/g);
return m ? m.length : 1;
}

function analyzeText(text) {
var words = text.trim().match(/\b\w+\b/g) || [];
var wordCount = words.length;
var charCount = text.length;
var sentences = text.split(/[.!?]+/).filter(function(s) { return s.trim().length > 2; });
var sentenceCount = sentences.length;
var totalSyllables = 0;
for (var i = 0; i < words.length; i++) {
totalSyllables += countSyllables(words[i]);
}
var avgWordsPerSentence = sentenceCount > 0 ? (wordCount / sentenceCount) : 0;
var avgSyllablesPerWord = wordCount > 0 ? (totalSyllables / wordCount) : 0;
return { wordCount: wordCount, charCount: charCount, sentenceCount: sentenceCount,
avgWordsPerSentence: avgWordsPerSentence, avgSyllablesPerWord: avgSyllablesPerWord };
}

function readabilityLabel(awps, aspw) {
// Simple heuristic
var score = awps * 0.5 + aspw * 8;
if (score < 12) return { label: "Very Easy", color: "#059669" };
if (score < 16) return { label: "Easy", color: "#10b981" };
if (score < 20) return { label: "Moderate", color: "#d97706" };
if (score < 26) return { label: "Difficult", color: "#f59e0b" };
return { label: "Complex", color: "#dc2626" };
}

function progressPercent(minutes) {
// 0 min = 0%, 60 min = 100% (cap)
return Math.min(100, Math.max(2, (minutes / 60) * 100));
}

window.rtUpdate = function() {
var text = document.getElementById("rt-textarea").value;
var wcInput = document.getElementById("rt-wc-input").value;
var hasText = text.trim().length > 0;
var hasWC = wcInput && parseInt(wcInput) > 0;

if (!hasText && !hasWC) {
document.getElementById("rt-results-body").innerHTML =
'<div class="empty-state">Paste text or enter a word count above to see results.</div>';
return;
}

var data = hasText ? analyzeText(text) : null;
var wordCount = hasText ? data.wordCount : parseInt(wcInput);
var readMin = wordCount / wpm;
var spkMin = wordCount / spkWpm;

var html = '<div class="results-grid">';
html += '<div class="result-box"><div class="r-val">' + fmtTime(readMin) + '</div><div class="r-lbl">Reading Time</div></div>';
html += '<div class="result-box"><div class="r-val">' + fmtTime(spkMin) + '</div><div class="r-lbl">Speaking Time (130 WPM)</div></div>';
html += '<div class="result-box"><div class="r-val">' + fmtNum(wordCount) + '</div><div class="r-lbl">Words</div></div>';
if (hasText) {
html += '<div class="result-box"><div class="r-val">' + fmtNum(data.charCount) + '</div><div class="r-lbl">Characters</div></div>';
html += '<div class="result-box"><div class="r-val">' + fmtNum(data.sentenceCount) + '</div><div class="r-lbl">Sentences</div></div>';
}
html += '</div>';

// Progress bar
var pct = progressPercent(readMin);
html += '<div class="progress-wrap">';
html += '<div class="progress-label"><span>Reading time</span><span>' + fmtTime(readMin) + ' at ' + wpm + ' WPM</span></div>';
html += '<div class="progress-bar-bg"><div class="progress-bar-fill" style="width:' + pct + '%"></div></div>';
html += '</div>';

// Speed comparison
html += '<div class="speed-comparison">';
html += '<div class="cmp-box slow"><div class="cmp-t">Slow reader</div><div class="cmp-v">' + fmtTime(wordCount/150) + '</div><div class="cmp-wpm">150 WPM</div></div>';
html += '<div class="cmp-box avg"><div class="cmp-t">Average</div><div class="cmp-v">' + fmtTime(wordCount/200) + '</div><div class="cmp-wpm">200 WPM</div></div>';
html += '<div class="cmp-box fast"><div class="cmp-t">Fast reader</div><div class="cmp-v">' + fmtTime(wordCount/300) + '</div><div class="cmp-wpm">300 WPM</div></div>';
html += '</div>';

// Readability
if (hasText && data.wordCount > 5) {
var awps = data.avgWordsPerSentence;
var aspw = data.avgSyllablesPerWord;
var rdbl = readabilityLabel(awps, aspw);
html += '<div class="readability-section"><h2>Readability</h2>';
html += '<div class="rdbl-row">';
html += '<div class="rdbl-item"><div class="rdbl-val" style="color:' + rdbl.color + '">' + rdbl.label + '</div><div class="rdbl-lbl">Overall difficulty</div></div>';
html += '<div class="rdbl-item"><div class="rdbl-val">' + awps.toFixed(1) + '</div><div class="rdbl-lbl">Avg words / sentence</div><div class="rdbl-note">' + (awps < 15 ? "Clear & concise" : awps < 22 ? "Readable" : "Long sentences") + '</div></div>';
html += '<div class="rdbl-item"><div class="rdbl-val">' + aspw.toFixed(2) + '</div><div class="rdbl-lbl">Avg syllables / word</div><div class="rdbl-note">' + (aspw < 1.5 ? "Simple vocabulary" : aspw < 2.0 ? "Moderate vocabulary" : "Complex vocabulary") + '</div></div>';
html += '</div></div>';
}

document.getElementById("rt-results-body").innerHTML = html;
};

window.rtSpeedChange = function(val) {
wpm = parseInt(val);
document.getElementById("rt-speed-val").textContent = wpm + " WPM";
// Update active preset
document.querySelectorAll("#rt-app .preset-btn").forEach(function(b) { b.classList.remove("active"); });
rtUpdate();
};

window.rtSetSpeed = function(val) {
wpm = val;
document.getElementById("rt-speed").value = val;
document.getElementById("rt-speed-val").textContent = val + " WPM";
document.querySelectorAll("#rt-app .preset-btn").forEach(function(b) {
b.classList.toggle("active", parseInt(b.textContent.match(/\d+/)[0]) === val);
});
rtUpdate();
};

window.rtClear = function() {
document.getElementById("rt-textarea").value = "";
document.getElementById("rt-wc-input").value = "";
rtUpdate();
};

window.rtBookUpdate = function() {
var pages = parseInt(document.getElementById("rt-pages").value);
var wpp = parseInt(document.getElementById("rt-wppage").value) || 250;
var el = document.getElementById("rt-book-result");
if (!pages || pages < 1) { el.style.display = "none"; return; }
var totalWords = pages * wpp;
var mins = totalWords / wpm;
el.style.display = "block";
el.innerHTML = "A <strong>" + pages + "-page</strong> book (~" + fmtNum(totalWords) + " words) would take approximately <strong>" + fmtTime(mins) + "</strong> to read at your current speed (" + wpm + " WPM).";
};
})();
</script>

</div>

---

<div class="related-note">
Related: Count words in your content with the <a href="/tools/word-counter/">Word Counter</a>.
</div>
