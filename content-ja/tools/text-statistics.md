---
title: "テキスト統計分析ツール"
date: 2026-01-01
description: "無料のテキスト統計分析ツール。単語数・文字数・文数・段落数・平均単語長・読了時間・朗読時間・可読性スコア（Flesch-Kincaid）・頻出キーワード・ユニーク語率を即時計算。"
categories: ["無料ツール"]
tags: ["テキストツール", "文字列処理", "無料ツール"]
slug: "text-statistics"
ShowToc: false
aliases:
  - "/ja/tools/text-statistics/"
cover:
  image: "/images/covers/text-statistics-ja.png"
  alt: "テキスト統計分析ツール"
---

<div id="ts-app">

<style>
#ts-app {
font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Noto Sans JP', 'Meiryo', system-ui, sans-serif;
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
font-weight: 700;
color: #f1f5f9;
margin: 0 0 12px 0;
}
#ts-app h3 {
font-size: 0.82rem;
font-weight: 700;
color: #94a3b8;
margin: 0 0 10px 0;
text-transform: uppercase;
letter-spacing: 0.04em;
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
line-height: 1.7;
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
font-weight: 700;
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
line-height: 1.4;
}

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
font-weight: 700;
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

<h2>テキストを入力してください</h2>

<textarea id="ts-textarea" placeholder="ここにテキストを貼り付けるか入力してください…"></textarea>

<div class="ts-toolbar">
<button class="ts-btn ts-btn-copy" onclick="tsCopyText()">テキストをコピー</button>
<button class="ts-btn ts-btn-danger" onclick="tsClear()">クリア</button>
</div>

<!-- 基本統計 -->
<div class="ts-stats-grid">
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-words">0</div>
<div class="ts-stat-label">単語数</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-chars">0</div>
<div class="ts-stat-label">文字数<br>（スペース含む）</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-chars-no">0</div>
<div class="ts-stat-label">文字数<br>（スペース除く）</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-sentences">0</div>
<div class="ts-stat-label">文の数</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-paragraphs">0</div>
<div class="ts-stat-label">段落数</div>
</div>
<div class="ts-stat-card">
<div class="ts-stat-value" id="ts-avg-word">0.0</div>
<div class="ts-stat-label">平均単語長</div>
</div>
</div>

<!-- ユニーク語率 -->
<div class="ts-unique-badge">
<span class="ts-unique-pct" id="ts-unique-pct">0%</span>
<span>ユニーク語率 &nbsp;（<span id="ts-unique-count">0</span> / <span id="ts-unique-total">0</span> 語）</span>
</div>

<!-- 読了・朗読時間 -->
<div class="ts-time-grid">
<div class="ts-time-card">
<div class="ts-time-icon">&#128214;</div>
<div>
<div class="ts-time-val" id="ts-read-time">0秒</div>
<div class="ts-time-desc">読了時間（225語/分）</div>
</div>
</div>
<div class="ts-time-card">
<div class="ts-time-icon">&#127897;</div>
<div>
<div class="ts-time-val" id="ts-speak-time">0秒</div>
<div class="ts-time-desc">朗読時間（130語/分）</div>
</div>
</div>
</div>

<!-- 可読性スコア -->
<div class="ts-readability-wrap">
<h3>可読性スコア（英文テキスト向け）</h3>
<div class="ts-scores-row">
<!-- Flesch Reading Ease -->
<div class="ts-score-block">
<div class="ts-score-label">Flesch Reading Ease（0〜100、高いほど読みやすい）</div>
<div class="ts-score-num" id="ts-fre-score">—</div>
<div class="ts-rbar-track">
<div class="ts-rbar-fill" id="ts-fre-fill" style="width:0%;background:#6366f1;"></div>
</div>
<div class="ts-rbar-labels"><span>0 難解</span><span>60 標準</span><span>100 易しい</span></div>
<div class="ts-score-desc" id="ts-fre-desc">テキストを入力すると計算されます</div>
</div>
<!-- Flesch-Kincaid Grade Level -->
<div class="ts-score-block">
<div class="ts-score-label">Flesch-Kincaid グレードレベル（米国学年相当）</div>
<div class="ts-score-num" id="ts-fkg-score">—</div>
<div class="ts-rbar-track">
<div class="ts-rbar-fill" id="ts-fkg-fill" style="width:0%;background:#6366f1;"></div>
</div>
<div class="ts-rbar-labels"><span>K学年</span><span>8年</span><span>16+（大学）</span></div>
<div class="ts-score-desc" id="ts-fkg-desc">テキストを入力すると計算されます</div>
</div>
</div>
</div>

<!-- 頻出キーワード -->
<div class="ts-section">
<h3>頻出キーワード（上位10件）</h3>
<div id="ts-keywords-wrap"><div class="ts-empty">テキストを入力するとキーワード分析が表示されます</div></div>
</div>

<script>
(function(){
var STOP_EN = new Set([
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
var STOP_JA = new Set([
'の','に','は','を','た','が','で','て','と','し','れ','さ','ある','いる','も',
'する','から','な','こと','として','い','や','れる','など','なっ','ない','この',
'ため','その','あっ','よう','また','もの','という','あり','まで','られ','なる',
'へ','か','だ','これ','によって','により','おり','より','による','ず','なり','られる'
]);

function getWords(t) { return t.match(/\b[a-zA-Z']+\b/g) || []; }

function getJaChars(t) {
return (t.match(/[\u3000-\u9fff\uf900-\ufaff\uff01-\uffee]/g) || []);
}

function getSentences(t) {
var s = t.trim();
if (!s) return 0;
var m = s.match(/[^。！？.!?]*[。！？.!?]+/g);
return m ? m.length : (s.length > 0 ? 1 : 0);
}

function getParagraphs(t) {
var s = t.trim();
if (!s) return 0;
return s.split(/\n\s*\n+/).filter(function(p){ return p.trim().length > 0; }).length || 1;
}

function formatTime(mins) {
if (mins === 0) return '0秒';
if (mins < 1) return Math.round(mins * 60) + '秒';
var m = Math.floor(mins);
var s = Math.round((mins - m) * 60);
if (s === 0) return m + '分';
return m + '分' + s + '秒';
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
var asl = words.length / sentences;
var asw = syl / words.length;
var fre = 206.835 - 1.015 * asl - 84.6 * asw;
fre = Math.round(Math.max(0, Math.min(100, fre)));
var fkg = 0.39 * asl + 11.8 * asw - 15.59;
fkg = Math.max(0, fkg);
return { fre: fre, fkg: parseFloat(fkg.toFixed(1)) };
}

function freLabel(s) {
if (s >= 90) return 'とても簡単（小学5年生レベル）';
if (s >= 80) return '簡単（小学6年生レベル）';
if (s >= 70) return 'やや簡単（中学1年生レベル）';
if (s >= 60) return '標準（中学2〜3年生レベル）';
if (s >= 50) return 'やや難しい（高校レベル）';
if (s >= 30) return '難しい（大学レベル）';
return '非常に難しい（専門家レベル）';
}

function freColor(s) {
if (s >= 70) return '#4ade80';
if (s >= 50) return '#facc15';
if (s >= 30) return '#fb923c';
return '#f87171';
}

function fkgLabel(g) {
if (g <= 1) return '幼稚園・小学低学年相当';
if (g <= 6) return '小学校レベル';
if (g <= 8) return '中学校レベル';
if (g <= 12) return '高校レベル';
if (g <= 16) return '大学レベル';
return '大学院・専門家レベル';
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
var jaChars = getJaChars(text);
var totalTokens = wc + jaChars.length;

var sentences = getSentences(text);
var paragraphs = getParagraphs(text);
var avgLen = wc > 0
? (words.reduce(function(a,w){ return a + w.replace(/'/g,'').length; }, 0) / wc).toFixed(1)
: '0.0';

// Unique words (EN)
var lower = words.map(function(w){ return w.toLowerCase(); });
var uniqueSet = new Set(lower);
var uniqueCount = uniqueSet.size;
var uniquePct = wc > 0 ? Math.round((uniqueCount / wc) * 100) : 0;

document.getElementById('ts-words').textContent = totalTokens.toLocaleString();
document.getElementById('ts-chars').textContent = text.length.toLocaleString();
document.getElementById('ts-chars-no').textContent = text.replace(/\s/g,'').length.toLocaleString();
document.getElementById('ts-sentences').textContent = sentences.toLocaleString();
document.getElementById('ts-paragraphs').textContent = paragraphs.toLocaleString();
document.getElementById('ts-avg-word').textContent = avgLen;

document.getElementById('ts-unique-pct').textContent = uniquePct + '%';
document.getElementById('ts-unique-count').textContent = uniqueCount.toLocaleString();
document.getElementById('ts-unique-total').textContent = wc.toLocaleString();

document.getElementById('ts-read-time').textContent = formatTime(totalTokens / 225);
document.getElementById('ts-speak-time').textContent = formatTime(totalTokens / 130);

var rd = words.length >= 5 ? computeReadability(words, sentences) : null;
var freScoreEl = document.getElementById('ts-fre-score');
var freDescEl  = document.getElementById('ts-fre-desc');
var freFillEl  = document.getElementById('ts-fre-fill');
var fkgScoreEl = document.getElementById('ts-fkg-score');
var fkgDescEl  = document.getElementById('ts-fkg-desc');
var fkgFillEl  = document.getElementById('ts-fkg-fill');

if (!rd) {
freScoreEl.textContent = '\u2014'; freDescEl.textContent = 'テキストを入力すると計算されます';
freFillEl.style.width = '0%'; freFillEl.style.background = '#6366f1';
fkgScoreEl.textContent = '\u2014'; fkgDescEl.textContent = 'テキストを入力すると計算されます';
fkgFillEl.style.width = '0%'; fkgFillEl.style.background = '#6366f1';
} else {
freScoreEl.textContent = rd.fre;
freDescEl.textContent = freLabel(rd.fre);
freFillEl.style.width = rd.fre + '%';
freFillEl.style.background = freColor(rd.fre);

fkgScoreEl.textContent = rd.fkg;
fkgDescEl.textContent = fkgLabel(rd.fkg);
var fkgPct = Math.min(100, Math.round((rd.fkg / 16) * 100));
fkgFillEl.style.width = fkgPct + '%';
fkgFillEl.style.background = fkgColor(rd.fkg);
}

// Keywords
var wrap = document.getElementById('ts-keywords-wrap');
if (!text.trim()) {
wrap.innerHTML = '<div class="ts-empty">テキストを入力するとキーワード分析が表示されます</div>';
return;
}
var freq = {};
lower.forEach(function(lw) {
if (!STOP_EN.has(lw) && lw.replace(/'/g,'').length > 1) {
freq[lw] = (freq[lw] || 0) + 1;
}
});
// Japanese phrase tokens
var jaParts = text.match(/[^\s、。！？\n,.!?「」『』【】\u3000]+/g) || [];
jaParts.forEach(function(p) {
if (/[\u3040-\u9fff]/.test(p) && p.length >= 2) {
if (!STOP_JA.has(p)) freq[p] = (freq[p] || 0) + 1;
}
});
var sorted = Object.keys(freq).sort(function(a,b){ return freq[b]-freq[a]; }).slice(0,10);
if (!sorted.length) {
wrap.innerHTML = '<div class="ts-empty">有効なキーワードが見つかりませんでした</div>';
return;
}
var maxC = freq[sorted[0]];
var totalRef = Math.max(totalTokens, 1);
var html = '<table class="ts-table"><thead><tr><th>#</th><th>キーワード</th><th>出現数</th><th>密度</th></tr></thead><tbody>';
sorted.forEach(function(word, i) {
var c = freq[word];
var d = ((c / totalRef) * 100).toFixed(2);
var bw = Math.round((c / maxC) * 90);
html += '<tr>'
+ '<td style="color:#475569;">' + (i+1) + '</td>'
+ '<td style="color:#a5b4fc;font-weight:700;">' + esc(word) + '</td>'
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

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

> 文字数カウント → [文字数カウンター](/ja/tools/word-counter/)

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

</div>

---

## 関連ツール

> Case Converter → [Case Converterツール](/ja/tools/case-converter/)
> Character Counter → [Character Counterツール](/ja/tools/character-counter/)
> Lorem Ipsum Generator → [Lorem Ipsum Generatorツール](/ja/tools/lorem-ipsum-generator/)

## 関連記事

- [AIで高品質な文章を作成するコツ7つ【プロが使うテクニック】](/ja/posts/ai-文章作成-コツ/)
- [AI要約ツール おすすめ無料10選【2026年版】用途別に徹底比較](/ja/posts/ai-youyaku-tool-osusume/)
- [ChatGPTプロンプトの書き方コツ【2026年版】すぐ使える例文テンプレート付き](/ja/posts/chatgpt-prompt-kakikata-kotsu/)
