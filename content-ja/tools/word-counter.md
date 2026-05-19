---
title: "文字数・単語数カウンター"
date: 2025-10-11
description: "無料の文字数・単語数カウントツール。読了時間・キーワード密度・可読性スコア・詳細テキスト統計を即時分析。"
categories: ["無料ツール"]
slug: "word-counter"
ShowToc: false
cover:
  image: "/images/covers/word-counter-ja.png"
  alt: "文字数・単語数カウンター"
---

<div id="wc-app">

<style>
#wc-app {
font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Noto Sans JP', 'Meiryo', system-ui, sans-serif;
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
font-weight: 700;
color: #f1f5f9;
margin: 0 0 12px 0;
}

#wc-app h3 {
font-size: 0.82rem;
font-weight: 700;
color: #94a3b8;
margin: 0 0 10px 0;
text-transform: uppercase;
letter-spacing: 0.04em;
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
line-height: 1.7;
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
font-weight: 700;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
font-family: inherit;
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
line-height: 1.4;
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
font-weight: 700;
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

<h2>テキストを入力してください</h2>

<textarea id="wc-textarea" placeholder="ここにテキストを貼り付けるか、入力してください…"></textarea>

<div class="wc-toolbar">
<button class="wc-btn wc-copy-btn" onclick="wcCopyText()">テキストをコピー</button>
<button class="wc-btn wc-btn-danger" onclick="wcClear()">クリア</button>
</div>

<div class="wc-stats-grid">
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-words">0</div><div class="wc-stat-label">単語数</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-chars">0</div><div class="wc-stat-label">文字数<br>（スペース含む）</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-chars-no">0</div><div class="wc-stat-label">文字数<br>（スペース除く）</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-sentences">0</div><div class="wc-stat-label">文の数</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-paragraphs">0</div><div class="wc-stat-label">段落数</div></div>
<div class="wc-stat-card"><div class="wc-stat-value" id="wc-avg-word">0</div><div class="wc-stat-label">平均単語長</div></div>
</div>

<div class="wc-time-grid">
<div class="wc-time-card">
<div class="wc-time-icon">&#128214;</div>
<div>
<div class="wc-time-val" id="wc-read-time">0秒</div>
<div class="wc-time-desc">読了時間（225語/分）</div>
</div>
</div>
<div class="wc-time-card">
<div class="wc-time-icon">&#127897;</div>
<div>
<div class="wc-time-val" id="wc-speak-time">0秒</div>
<div class="wc-time-desc">朗読時間（130語/分）</div>
</div>
</div>
</div>

<div class="wc-readability-wrap">
<h3>可読性スコア（Flesch-Kincaid）</h3>
<div style="display:flex;align-items:baseline;gap:12px;flex-wrap:wrap;">
<span class="wc-rbar-score" id="wc-fk-score">&#8212;</span>
<span class="wc-rbar-level" id="wc-fk-level">テキストを入力すると計算されます</span>
</div>
<div class="wc-rbar-track">
<div class="wc-rbar-fill" id="wc-rbar-fill" style="width:0%;background:#6366f1;"></div>
</div>
<div class="wc-rbar-labels">
<span>非常に難解 (0)</span>
<span>標準 (60)</span>
<span>とても簡単 (100)</span>
</div>
</div>

<div class="wc-section">
<h3>上位10キーワードと出現頻度</h3>
<div id="wc-keywords-wrap"><div class="wc-empty">テキストを入力するとキーワード分析が表示されます</div></div>
</div>

<div class="wc-section">
<h3>検索 &amp; 置換</h3>
<div class="wc-fr-grid">
<input class="wc-fr-input" id="wc-find" placeholder="検索する語句..." />
<input class="wc-fr-input" id="wc-replace" placeholder="置換後の語句..." />
<button class="wc-btn wc-btn-primary" onclick="wcReplaceAll()">すべて置換</button>
</div>
<div class="wc-fr-actions">
<button class="wc-btn wc-btn-secondary" onclick="wcHighlightFind()">一致数を確認</button>
<button class="wc-btn wc-btn-secondary" onclick="wcClearFrInfo()">クリア</button>
</div>
<div class="wc-fr-info" id="wc-fr-info"></div>
</div>

<script>
(function(){
var STOP_JA = new Set([
'の','に','は','を','た','が','で','て','と','し','れ','さ','ある','いる','も',
'する','から','な','こと','として','い','や','れる','など','なっ','ない','この',
'ため','その','あっ','よう','また','もの','という','あり','まで','られ','なる',
'へ','か','だ','これ','によって','により','おり','より','による','ず','なり','られる'
]);
var STOP_EN = new Set([
'a','an','the','and','but','or','for','in','on','at','to','of','by','as','is',
'it','be','was','are','were','have','has','do','does','did','will','would',
'could','should','this','that','i','you','he','she','we','they','my','your',
'not','with','from','about','if','then','there','also','any','very','just'
]);

function getWords(t) { return t.match(/\b[a-zA-Z']+\b/g) || []; }

function getJaChars(t) {
// Count CJK characters as individual tokens
return (t.match(/[\u3000-\u9fff\uf900-\ufaff\uff01-\uffee]/g) || []);
}

function getSentences(t) {
var s = t.trim();
if (!s) return 0;
// Match Japanese and English sentence endings
var m = s.match(/[^。！？.!?]*[。！？.!?]+/g);
if (!m) return s.length > 0 ? 1 : 0;
return m.length;
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

function fleschKincaid(words, sentences) {
if (!words.length || !sentences) return null;
var syl = words.reduce(function(a,w){ return a + countSyllables(w); }, 0);
var asl = words.length / sentences;
var asw = syl / words.length;
var score = 206.835 - 1.015 * asl - 84.6 * asw;
return Math.round(Math.max(0, Math.min(100, score)));
}

function fkLabel(s) {
if (s >= 90) return 'とても簡単（小学5年生レベル）';
if (s >= 80) return '簡単（小学6年生レベル）';
if (s >= 70) return 'やや簡単（中学1年生レベル）';
if (s >= 60) return '標準（中学2〜3年生レベル）';
if (s >= 50) return 'やや難しい（高校レベル）';
if (s >= 30) return '難しい（大学レベル）';
return '非常に難しい（専門家レベル）';
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
// For Japanese, also count total characters as "words" proxy
var jaChars = getJaChars(text);
var totalTokens = wc + jaChars.length;
var sentences = getSentences(text);
var paragraphs = getParagraphs(text);
var avgLen = wc > 0
? (words.reduce(function(a,w){ return a + w.replace(/'/g,'').length; }, 0) / wc).toFixed(1)
: '0.0';

document.getElementById('wc-words').textContent = totalTokens.toLocaleString();
document.getElementById('wc-chars').textContent = text.length.toLocaleString();
document.getElementById('wc-chars-no').textContent = text.replace(/\s/g,'').length.toLocaleString();
document.getElementById('wc-sentences').textContent = sentences.toLocaleString();
document.getElementById('wc-paragraphs').textContent = paragraphs.toLocaleString();
document.getElementById('wc-avg-word').textContent = avgLen;

document.getElementById('wc-read-time').textContent = formatTime(totalTokens / 225);
document.getElementById('wc-speak-time').textContent = formatTime(totalTokens / 130);

var fk = words.length >= 5 ? fleschKincaid(words, sentences) : null;
var scoreEl = document.getElementById('wc-fk-score');
var levelEl = document.getElementById('wc-fk-level');
var fillEl  = document.getElementById('wc-rbar-fill');
if (fk === null) {
scoreEl.textContent = '\u2014';
levelEl.textContent = 'テキストを入力すると計算されます';
fillEl.style.width = '0%';
fillEl.style.background = '#6366f1';
} else {
scoreEl.textContent = fk;
levelEl.textContent = fkLabel(fk);
fillEl.style.width = fk + '%';
fillEl.style.background = fkColor(fk);
}

// Keywords — works for both EN and mixed JP/EN text
var wrap = document.getElementById('wc-keywords-wrap');
if (!text.trim()) {
wrap.innerHTML = '<div class="wc-empty">テキストを入力するとキーワード分析が表示されます</div>';
return;
}

var freq = {};
// English words
words.forEach(function(w) {
var lw = w.toLowerCase();
if (!STOP_EN.has(lw) && lw.length > 1) freq[lw] = (freq[lw] || 0) + 1;
});
// Japanese words (simple tokenization by known stop particle filter)
var jaParts = text.match(/[^\s、。！？\n,.!?「」『』【】\u3000]+/g) || [];
jaParts.forEach(function(p) {
if (/[\u3040-\u9fff]/.test(p) && p.length >= 2) {
var lp = p;
if (!STOP_JA.has(lp)) freq[lp] = (freq[lp] || 0) + 1;
}
});

var sorted = Object.keys(freq).sort(function(a,b){ return freq[b]-freq[a]; }).slice(0,10);
if (!sorted.length) {
wrap.innerHTML = '<div class="wc-empty">有効なキーワードが見つかりませんでした</div>';
return;
}
var maxC = freq[sorted[0]];
var html = '<table class="wc-table"><thead><tr><th>#</th><th>キーワード</th><th>出現数</th><th>密度</th></tr></thead><tbody>';
var totalRef = Math.max(totalTokens, 1);
sorted.forEach(function(word, i) {
var c = freq[word];
var d = ((c / totalRef) * 100).toFixed(2);
var bw = Math.round((c / maxC) * 80);
html += '<tr><td style="color:#475569;">' + (i+1) + '</td>'
+ '<td style="color:#a5b4fc;font-weight:700;">' + esc(word) + '</td>'
+ '<td>' + c + '</td>'
+ '<td><span class="wc-density-bar" style="width:' + bw + 'px"></span>' + d + '%</td></tr>';
});
html += '</tbody></table>';
wrap.innerHTML = html;
}

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
if (!find) { info.textContent = '検索する語句を入力してください。'; return; }
var ta = document.getElementById('wc-textarea');
var regex = new RegExp(find.replace(/[.*+?^${}()|[\]\\]/g,'\\$&'), 'g');
var m = (ta.value.match(regex) || []).length;
if (!m) { info.textContent = '"' + find + '" は見つかりませんでした。'; return; }
ta.value = ta.value.replace(regex, repl);
info.textContent = m + ' 箇所を置換しました。';
analyze();
};

window.wcHighlightFind = function() {
var find = document.getElementById('wc-find').value;
var info = document.getElementById('wc-fr-info');
if (!find) { info.textContent = '検索する語句を入力してください。'; return; }
var regex = new RegExp(find.replace(/[.*+?^${}()|[\]\\]/g,'\\$&'), 'gi');
var m = (document.getElementById('wc-textarea').value.match(regex) || []).length;
info.textContent = m > 0
? '"' + find + '" が ' + m + ' 箇所見つかりました。'
: '"' + find + '" は見つかりませんでした。';
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

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

> 文字数カウント → [文字数カウンター](/ja/tools/character-counter/)
> 単語頻度 → [単語頻度カウンター](/ja/tools/word-frequency-counter/)

<div class="wc-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>

---

## 関連ツール

> Case Converter → [Case Converterツール](/ja/tools/case-converter/)
> Character Counter → [Character Counterツール](/ja/tools/character-counter/)
> Lorem Ipsum Generator → [Lorem Ipsum Generatorツール](/ja/tools/lorem-ipsum-generator/)

## 関連記事

- [AIを使ったブログ記事の書き方入門【2026年版・SEOで上位表示を狙う方法】](/ja/posts/ai-ブログ-書き方/)
- [AIで高品質な文章を作成するコツ7つ【プロが使うテクニック】](/ja/posts/ai-文章作成-コツ/)
- [AI要約ツール おすすめ無料10選【2026年版】用途別に徹底比較](/ja/posts/ai-youyaku-tool-osusume/)
