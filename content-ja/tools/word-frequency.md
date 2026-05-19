---
title: "単語頻度分析ツール"
description: "単語の出現頻度とテキスト統計を分析。最頻出単語を見つける無料ワード頻度分析ツール。"
date: 2025-05-29
slug: "word-frequency"
categories: ["無料ツール"]
ShowToc: false
aliases:
  - "/ja/tools/word-frequency-counter/"
cover:
  image: "/images/covers/word-frequency-ja.png"
  alt: "単語頻度分析ツール"
---

テキストを貼り付けるだけで単語の出現頻度を即座に分析。上位N件の棒グラフ表示、ストップワード除去、CSV出力に対応。

> 文字数を数える → [文字数カウンター](/ja/tools/word-counter/)

<div id="wf-app">

<style>
#wf-app *,
#wf-app *::before,
#wf-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#wf-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic", Roboto, sans-serif;
color: #1e293b;
max-width: 820px;
}
#wf-app h2 {
font-size: 1rem;
font-weight: 700;
color: #0f172a;
margin-bottom: 10px;
}
#wf-app textarea {
width: 100%;
height: 160px;
padding: 12px;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 14px;
line-height: 1.6;
resize: vertical;
font-family: inherit;
color: #1e293b;
background: #fff;
transition: border-color 0.2s;
}
#wf-app textarea:focus {
outline: none;
border-color: #6366f1;
}
#wf-app .wf-options {
display: flex;
flex-wrap: wrap;
gap: 12px;
margin: 14px 0;
align-items: center;
}
#wf-app .wf-option-group {
display: flex;
align-items: center;
gap: 6px;
font-size: 13px;
color: #475569;
}
#wf-app .wf-option-group label {
cursor: pointer;
user-select: none;
}
#wf-app .wf-option-group input[type="checkbox"] {
width: 15px;
height: 15px;
accent-color: #6366f1;
cursor: pointer;
}
#wf-app .wf-option-group select,
#wf-app .wf-option-group input[type="number"] {
padding: 4px 8px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
color: #1e293b;
background: #fff;
cursor: pointer;
}
#wf-app .wf-option-group input[type="number"] {
width: 64px;
}
#wf-app .wf-btn-row {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 20px;
}
#wf-app button {
padding: 9px 20px;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, background 0.15s;
}
#wf-app button:hover { opacity: 0.88; }
#wf-app .wf-btn-analyze {
background: #6366f1;
color: #fff;
}
#wf-app .wf-btn-clear {
background: #f1f5f9;
color: #475569;
}
#wf-app .wf-btn-copy {
background: #f1f5f9;
color: #475569;
}
#wf-app .wf-btn-csv {
background: #ecfdf5;
color: #065f46;
border: 1px solid #a7f3d0;
}
#wf-app .wf-stats-bar {
display: flex;
gap: 18px;
flex-wrap: wrap;
margin-bottom: 18px;
padding: 12px 16px;
background: #f8fafc;
border-radius: 8px;
font-size: 13px;
color: #475569;
}
#wf-app .wf-stats-bar span strong {
color: #1e293b;
font-size: 15px;
}
#wf-app .wf-canvas-wrap {
margin-bottom: 20px;
overflow-x: auto;
}
#wf-app canvas {
display: block;
max-width: 100%;
border-radius: 8px;
background: #fff;
border: 1px solid #e2e8f0;
}
#wf-app .wf-table-wrap {
overflow-x: auto;
border-radius: 8px;
border: 1px solid #e2e8f0;
}
#wf-app table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
}
#wf-app thead th {
background: #f8fafc;
padding: 10px 14px;
text-align: left;
font-weight: 700;
color: #475569;
border-bottom: 1.5px solid #e2e8f0;
}
#wf-app tbody tr:hover { background: #f8fafc; }
#wf-app tbody td {
padding: 8px 14px;
border-bottom: 1px solid #f1f5f9;
color: #1e293b;
}
#wf-app tbody tr:last-child td { border-bottom: none; }
#wf-app .wf-rank { color: #94a3b8; font-size: 12px; }
#wf-app .wf-bar-cell { width: 160px; }
#wf-app .wf-inline-bar {
height: 8px;
border-radius: 4px;
background: #6366f1;
min-width: 2px;
transition: width 0.3s;
}
#wf-app .wf-pct { color: #64748b; font-size: 12px; }
#wf-app .wf-empty {
text-align: center;
padding: 40px 20px;
color: #94a3b8;
font-size: 14px;
}
</style>

<h2>テキスト入力</h2>
<textarea id="wf-input" placeholder="ここにテキストを貼り付けてください..."></textarea>

<div class="wf-options">
<div class="wf-option-group">
<label for="wf-top-n">上位</label>
<select id="wf-top-n">
<option value="10">10</option>
<option value="25" selected>25</option>
<option value="50">50</option>
<option value="100">100</option>
</select>
<label for="wf-top-n">語</label>
</div>
<div class="wf-option-group">
<input type="checkbox" id="wf-stop" checked>
<label for="wf-stop">ストップワードを除外</label>
</div>
<div class="wf-option-group">
<input type="checkbox" id="wf-case" checked>
<label for="wf-case">大文字小文字を区別しない</label>
</div>
<div class="wf-option-group">
<label for="wf-minlen">最小文字数</label>
<input type="number" id="wf-minlen" value="2" min="1" max="20">
</div>
</div>

<div class="wf-btn-row">
<button class="wf-btn-analyze" id="wf-analyze-btn">分析する</button>
<button class="wf-btn-clear" id="wf-clear-btn">クリア</button>
<button class="wf-btn-copy" id="wf-copy-btn">結果をコピー</button>
<button class="wf-btn-csv" id="wf-csv-btn">CSVで出力</button>
</div>

<div id="wf-stats" class="wf-stats-bar" style="display:none"></div>
<div class="wf-canvas-wrap"><canvas id="wf-canvas" style="display:none"></canvas></div>
<div id="wf-table-container">
<div class="wf-empty">テキストを入力して「分析する」をクリックしてください。</div>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function(){
const STOP_WORDS = new Set([
"a","an","the","and","or","but","in","on","at","to","for","of","with",
"by","from","is","are","was","were","be","been","being","have","has","had",
"do","does","did","will","would","could","should","may","might","shall",
"can","not","no","nor","so","yet","both","either","neither","each","few",
"more","most","other","some","such","than","then","that","this","these",
"those","it","its","i","me","my","we","our","you","your","he","him","his",
"she","her","they","them","their","what","which","who","whom","when","where",
"why","how","all","any","as","if","up","out","about","into","through",
"during","before","after","above","below","between","same","just","also",
"very","too","much","well","only","even","still","back","here","there","now"
]);

let lastResults = [];

function tokenize(text, caseInsensitive, minLen, ignoreStop) {
if (caseInsensitive) text = text.toLowerCase();
const words = text.match(/[a-zA-Z']+/g) || [];
const freq = {};
for (let w of words) {
w = w.replace(/^'+|'+$/g, "");
if (w.length < minLen) continue;
if (ignoreStop && STOP_WORDS.has(w.toLowerCase())) continue;
freq[w] = (freq[w] || 0) + 1;
}
return Object.entries(freq).sort((a,b) => b[1]-a[1]);
}

function drawChart(data, topN) {
const canvas = document.getElementById("wf-canvas");
const items = data.slice(0, Math.min(topN, 20));
if (!items.length) { canvas.style.display = "none"; return; }
const barH = 28, padL = 110, padR = 70, padT = 20, padB = 20;
const w = Math.max(500, padL + 320 + padR);
const h = padT + items.length * barH + padB;
canvas.width = w;
canvas.height = h;
canvas.style.display = "block";
const ctx = canvas.getContext("2d");
ctx.clearRect(0, 0, w, h);
const maxVal = items[0][1];
const barMaxW = w - padL - padR;
const colors = ["#6366f1","#8b5cf6","#06b6d4","#10b981","#f59e0b","#ef4444","#ec4899","#14b8a6","#f97316","#84cc16"];
items.forEach(([word, count], i) => {
const y = padT + i * barH;
const bw = Math.max(4, (count / maxVal) * barMaxW);
ctx.fillStyle = colors[i % colors.length];
ctx.beginPath();
ctx.roundRect(padL, y + 4, bw, barH - 8, 4);
ctx.fill();
ctx.fillStyle = "#475569";
ctx.font = "12px -apple-system, sans-serif";
ctx.textAlign = "right";
ctx.fillText(word, padL - 8, y + barH / 2 + 4);
ctx.fillStyle = "#1e293b";
ctx.font = "bold 12px -apple-system, sans-serif";
ctx.textAlign = "left";
ctx.fillText(count, padL + bw + 6, y + barH / 2 + 4);
});
}

function renderTable(data, topN, total) {
const container = document.getElementById("wf-table-container");
const items = data.slice(0, topN);
if (!items.length) {
container.innerHTML = '<div class="wf-empty">現在の設定では単語が見つかりませんでした。</div>';
return;
}
const maxCount = items[0][1];
let rows = items.map(([word, count], i) => {
const pct = total > 0 ? ((count / total) * 100).toFixed(2) : 0;
const barW = Math.round((count / maxCount) * 100);
return `<tr>
<td class="wf-rank">${i+1}</td>
<td><strong>${word}</strong></td>
<td>${count}</td>
<td class="wf-bar-cell"><div class="wf-inline-bar" style="width:${barW}%"></div></td>
<td class="wf-pct">${pct}%</td>
</tr>`;
}).join("");
container.innerHTML = `<div class="wf-table-wrap"><table>
<thead><tr><th>#</th><th>単語</th><th>回数</th><th>頻度</th><th>割合</th></tr></thead>
<tbody>${rows}</tbody>
</table></div>`;
}

function analyze() {
const text = document.getElementById("wf-input").value;
const topN = parseInt(document.getElementById("wf-top-n").value);
const ignoreStop = document.getElementById("wf-stop").checked;
const caseInsensitive = document.getElementById("wf-case").checked;
const minLen = parseInt(document.getElementById("wf-minlen").value) || 1;
if (!text.trim()) {
document.getElementById("wf-table-container").innerHTML = '<div class="wf-empty">テキストを入力して「分析する」をクリックしてください。</div>';
document.getElementById("wf-canvas").style.display = "none";
document.getElementById("wf-stats").style.display = "none";
return;
}
const results = tokenize(text, caseInsensitive, minLen, ignoreStop);
lastResults = results;
const totalWords = results.reduce((s,[,c]) => s+c, 0);
const uniqueWords = results.length;
const statsEl = document.getElementById("wf-stats");
statsEl.style.display = "flex";
statsEl.innerHTML = `
<span>総単語数: <strong>${totalWords.toLocaleString()}</strong></span>
<span>ユニーク語数: <strong>${uniqueWords.toLocaleString()}</strong></span>
<span>表示中: <strong>${Math.min(topN, uniqueWords)}</strong>語</span>
`;
drawChart(results, topN);
renderTable(results, topN, totalWords);
}

document.getElementById("wf-analyze-btn").addEventListener("click", analyze);
document.getElementById("wf-input").addEventListener("keydown", function(e){
if (e.ctrlKey && e.key === "Enter") analyze();
});

document.getElementById("wf-clear-btn").addEventListener("click", function(){
document.getElementById("wf-input").value = "";
document.getElementById("wf-canvas").style.display = "none";
document.getElementById("wf-stats").style.display = "none";
document.getElementById("wf-table-container").innerHTML = '<div class="wf-empty">テキストを入力して「分析する」をクリックしてください。</div>';
lastResults = [];
});

document.getElementById("wf-copy-btn").addEventListener("click", function(){
if (!lastResults.length) return;
const topN = parseInt(document.getElementById("wf-top-n").value);
const lines = lastResults.slice(0, topN).map(([w,c],i) => `${i+1}. ${w}: ${c}`);
navigator.clipboard.writeText(lines.join("\n")).then(() => {
const btn = document.getElementById("wf-copy-btn");
const orig = btn.textContent;
btn.textContent = "コピーしました!";
setTimeout(() => btn.textContent = orig, 1500);
});
});

document.getElementById("wf-csv-btn").addEventListener("click", function(){
if (!lastResults.length) return;
const topN = parseInt(document.getElementById("wf-top-n").value);
const total = lastResults.reduce((s,[,c]) => s+c, 0);
const rows = [["順位","単語","回数","割合"]];
lastResults.slice(0, topN).forEach(([w,c],i) => {
rows.push([i+1, w, c, total > 0 ? ((c/total)*100).toFixed(2)+"%" : "0%"]);
});
const csv = rows.map(r => r.map(v => `"${v}"`).join(",")).join("\n");
const blob = new Blob(["\uFEFF"+csv], {type: "text/csv"});
const url = URL.createObjectURL(blob);
const a = document.createElement("a");
a.href = url; a.download = "word-frequency.csv"; a.click();
URL.revokeObjectURL(url);
});

["wf-top-n","wf-stop","wf-case","wf-minlen"].forEach(id => {
document.getElementById(id).addEventListener("change", function(){
if (lastResults.length || document.getElementById("wf-input").value.trim()) analyze();
});
});
})();
</script>

</div>

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
