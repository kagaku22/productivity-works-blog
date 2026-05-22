---
title: "ダウンロード時間計算ツール - ファイル転送時間を推定"
description: "ファイルサイズと回線速度からダウンロード所要時間を計算。無料ダウンロード時間計算ツール。"
date: 2025-05-19
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
slug: "download-time-calculator"
ShowToc: false
cover:
  image: "/images/covers/download-time-calculator.png"
---

<div id="dt-app">
<style>
#dt-app {
font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Noto Sans JP', 'Yu Gothic', sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a202c;
}
#dt-app * { box-sizing: border-box; }
#dt-app h2 {
font-size: 1.2rem;
font-weight: 700;
margin: 1.6rem 0 0.8rem;
color: #2d3748;
border-left: 4px solid #4299e1;
padding-left: 0.6rem;
}
#dt-app .card {
background: #f7fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 1.4rem 1.6rem;
margin-bottom: 1.4rem;
}
#dt-app .row {
display: flex;
gap: 1rem;
flex-wrap: wrap;
align-items: flex-end;
margin-bottom: 1rem;
}
#dt-app .field {
display: flex;
flex-direction: column;
gap: 0.3rem;
}
#dt-app label {
font-size: 0.8rem;
font-weight: 700;
color: #4a5568;
letter-spacing: 0.02em;
}
#dt-app input[type="number"] {
padding: 0.55rem 0.75rem;
border: 1.5px solid #cbd5e0;
border-radius: 7px;
font-size: 1rem;
width: 160px;
background: #fff;
transition: border-color 0.2s;
}
#dt-app input[type="number"]:focus {
outline: none;
border-color: #4299e1;
box-shadow: 0 0 0 3px rgba(66,153,225,0.15);
}
#dt-app select {
padding: 0.55rem 0.75rem;
border: 1.5px solid #cbd5e0;
border-radius: 7px;
font-size: 0.95rem;
background: #fff;
cursor: pointer;
transition: border-color 0.2s;
}
#dt-app select:focus {
outline: none;
border-color: #4299e1;
}
#dt-app .presets {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-bottom: 0.8rem;
}
#dt-app .preset-btn {
padding: 0.38rem 0.85rem;
border: 1.5px solid #bee3f8;
border-radius: 20px;
background: #ebf8ff;
color: #2b6cb0;
font-size: 0.82rem;
font-weight: 700;
cursor: pointer;
transition: all 0.18s;
white-space: nowrap;
}
#dt-app .preset-btn:hover {
background: #4299e1;
color: #fff;
border-color: #4299e1;
}
#dt-app .preset-btn.active {
background: #2b6cb0;
color: #fff;
border-color: #2b6cb0;
}
#dt-app .calc-btn {
padding: 0.65rem 2rem;
background: linear-gradient(135deg, #4299e1, #2b6cb0);
color: #fff;
border: none;
border-radius: 8px;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: opacity 0.2s, transform 0.1s;
margin-top: 0.5rem;
}
#dt-app .calc-btn:hover { opacity: 0.9; transform: translateY(-1px); }
#dt-app .calc-btn:active { transform: translateY(0); }
#dt-app .result-box {
background: linear-gradient(135deg, #ebf8ff, #e6fffa);
border: 2px solid #4299e1;
border-radius: 10px;
padding: 1.2rem 1.6rem;
margin-top: 1rem;
display: none;
}
#dt-app .result-box.show { display: block; }
#dt-app .result-time {
font-size: 2rem;
font-weight: 800;
color: #2b6cb0;
margin-bottom: 0.3rem;
}
#dt-app .result-detail {
font-size: 0.88rem;
color: #4a5568;
line-height: 1.7;
}
#dt-app .converter-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(155px, 1fr));
gap: 0.8rem;
}
#dt-app .conv-field {
display: flex;
flex-direction: column;
gap: 0.3rem;
}
#dt-app .conv-field input { width: 100%; }
#dt-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
}
#dt-app th {
background: #4299e1;
color: #fff;
padding: 0.6rem 0.8rem;
text-align: left;
font-weight: 700;
font-size: 0.83rem;
}
#dt-app th:first-child { border-radius: 6px 0 0 0; }
#dt-app th:last-child { border-radius: 0 6px 0 0; }
#dt-app td {
padding: 0.55rem 0.8rem;
border-bottom: 1px solid #e2e8f0;
}
#dt-app tr:nth-child(even) td { background: #f7fafc; }
#dt-app tr:hover td { background: #ebf8ff; }
#dt-app .highlight-row td { font-weight: 700; color: #2b6cb0; }
#dt-app .section-label {
font-size: 0.78rem;
color: #718096;
margin-bottom: 0.5rem;
}
#dt-app .error-msg {
color: #e53e3e;
font-size: 0.85rem;
margin-top: 0.4rem;
display: none;
}
#dt-app .freee-cta {
background: #fffbeb;
border: 1px solid #f6e05e;
border-left: 4px solid #d69e2e;
border-radius: 8px;
padding: 1rem 1.4rem;
margin-top: 1.4rem;
font-size: 0.92rem;
color: #744210;
line-height: 1.7;
}
#dt-app .freee-cta a {
color: #b7791f;
font-weight: 700;
}
#dt-app .freee-cta a:hover { color: #975a16; }
@media (max-width: 600px) {
#dt-app input[type="number"] { width: 120px; }
#dt-app .result-time { font-size: 1.5rem; }
#dt-app table { font-size: 0.8rem; }
#dt-app td, #dt-app th { padding: 0.4rem 0.5rem; }
}
</style>

<h2>ファイルサイズ・速度の入力</h2>
<div class="card">
<div class="section-label">よく使うファイルサイズのプリセット：</div>
<div class="presets" id="size-presets">
<button class="preset-btn" onclick="dtSetSize(5,'MB','MP3')">MP3（5 MB）</button>
<button class="preset-btn" onclick="dtSetSize(10,'MB','写真')">写真（10 MB）</button>
<button class="preset-btn" onclick="dtSetSize(25,'MB','書類')">書類（25 MB）</button>
<button class="preset-btn" onclick="dtSetSize(700,'MB','CD')">CD（700 MB）</button>
<button class="preset-btn" onclick="dtSetSize(5,'GB','HD映画')">HD映画（5 GB）</button>
<button class="preset-btn" onclick="dtSetSize(25,'GB','4K映画')">4K映画（25 GB）</button>
<button class="preset-btn" onclick="dtSetSize(50,'GB','PCゲーム')">PCゲーム（50 GB）</button>
<button class="preset-btn" onclick="dtSetSize(100,'GB','大型ゲーム')">大型ゲーム（100 GB）</button>
</div>
<div class="row">
<div class="field">
<label>ファイルサイズ</label>
<input type="number" id="dt-filesize" min="0" step="any" placeholder="例: 1.5" value="">
</div>
<div class="field">
<label>単位</label>
<select id="dt-sizeunit">
<option value="KB">KB（キロバイト）</option>
<option value="MB" selected>MB（メガバイト）</option>
<option value="GB">GB（ギガバイト）</option>
<option value="TB">TB（テラバイト）</option>
</select>
</div>
</div>
<div class="section-label" style="margin-top:0.8rem;">通信速度のプリセット：</div>
<div class="presets" id="speed-presets">
<button class="preset-btn" onclick="dtSetSpeed(1,'3G（低速）')">3G — 1 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(5,'3G（標準）')">3G — 5 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(25,'4G LTE')">4G LTE — 25 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(50,'4G+')">4G+ — 50 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(100,'Wi-Fi 100')">Wi-Fi — 100 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(300,'Wi-Fi 300')">Wi-Fi — 300 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(500,'光回線 500')">光回線 — 500 Mbps</button>
<button class="preset-btn" onclick="dtSetSpeed(1000,'光回線 1Gbps')">光回線 — 1 Gbps</button>
</div>
<div class="row">
<div class="field">
<label>インターネット速度（Mbps）</label>
<input type="number" id="dt-speed" min="0.01" step="any" placeholder="例: 100" value="">
</div>
</div>
<div class="error-msg" id="dt-error">ファイルサイズと通信速度に0より大きい値を入力してください。</div>
<button class="calc-btn" onclick="dtCalculate()">ダウンロード時間を計算する</button>

<div class="result-box" id="dt-result">
<div class="result-time" id="dt-result-time"></div>
<div class="result-detail" id="dt-result-detail"></div>
</div>
</div>

<h2>速度単位コンバーター</h2>
<div class="card">
<div class="section-label">いずれかの欄に値を入力すると、他の欄が自動で変換されます。</div>
<div class="converter-grid">
<div class="conv-field">
<label>Mbps</label>
<input type="number" id="cv-mbps" min="0" step="any" placeholder="例: 100" oninput="dtConvert('mbps')">
</div>
<div class="conv-field">
<label>MBps（MB/s）</label>
<input type="number" id="cv-mbps2" min="0" step="any" placeholder="" oninput="dtConvert('mbps2')">
</div>
<div class="conv-field">
<label>Kbps</label>
<input type="number" id="cv-kbps" min="0" step="any" placeholder="" oninput="dtConvert('kbps')">
</div>
<div class="conv-field">
<label>KBps（KB/s）</label>
<input type="number" id="cv-kbps2" min="0" step="any" placeholder="" oninput="dtConvert('kbps2')">
</div>
<div class="conv-field">
<label>Gbps</label>
<input type="number" id="cv-gbps" min="0" step="any" placeholder="" oninput="dtConvert('gbps')">
</div>
</div>
</div>

<h2>速度別ダウンロード時間比較</h2>
<div class="card" style="padding: 0.6rem 0; overflow-x:auto;">
<table id="dt-table">
<thead>
<tr>
<th>回線種別</th>
<th>速度</th>
<th id="th-col1">—</th>
<th id="th-col2">—</th>
<th id="th-col3">—</th>
</tr>
</thead>
<tbody id="dt-tbody"></tbody>
</table>
<div style="font-size:0.78rem;color:#718096;padding:0.5rem 0.8rem 0;">
上でファイルサイズを計算すると、表が自動的に更新されます。
</div>
</div>

> IT環境の管理を効率化 → [freee会計でIT経費を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

<div class="freee-cta">
IT機器・回線・クラウドサービスなどのIT経費を毎月手入力していませんか？<br>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計</a>なら、銀行・カード明細を自動取込してIT経費を一括管理できます。
</div>

<script>
(function() {
window.dtSetSize = function(val, unit, label) {
document.getElementById('dt-filesize').value = val;
document.getElementById('dt-sizeunit').value = unit;
document.querySelectorAll('#size-presets .preset-btn').forEach(function(b) { b.classList.remove('active'); });
event.target.classList.add('active');
};

window.dtSetSpeed = function(val, label) {
document.getElementById('dt-speed').value = val;
document.querySelectorAll('#speed-presets .preset-btn').forEach(function(b) { b.classList.remove('active'); });
event.target.classList.add('active');
};

function dtToBytes(val, unit) {
var u = { KB: 1024, MB: 1024*1024, GB: 1024*1024*1024, TB: 1024*1024*1024*1024 };
return val * (u[unit] || 1);
}

function dtFormatTime(seconds) {
seconds = Math.round(seconds);
if (seconds < 1) return '1秒未満';
var d = Math.floor(seconds / 86400);
var h = Math.floor((seconds % 86400) / 3600);
var m = Math.floor((seconds % 3600) / 60);
var s = seconds % 60;
var parts = [];
if (d > 0) parts.push(d + '日');
if (h > 0) parts.push(h + '時間');
if (m > 0) parts.push(m + '分');
if (s > 0 && d === 0) parts.push(s + '秒');
return parts.join(' ');
}

function dtFormatTimeShort(seconds) {
seconds = Math.round(seconds);
if (seconds < 1) return '< 1秒';
var d = Math.floor(seconds / 86400);
var h = Math.floor((seconds % 86400) / 3600);
var m = Math.floor((seconds % 3600) / 60);
var s = seconds % 60;
if (d > 0) return d + '日' + h + '時間' + m + '分';
if (h > 0) return h + '時間' + m + '分' + s + '秒';
if (m > 0) return m + '分' + s + '秒';
return s + '秒';
}

function dtFormatSize(bytes) {
if (bytes >= 1024*1024*1024*1024) return (bytes/(1024*1024*1024*1024)).toFixed(2) + ' TB';
if (bytes >= 1024*1024*1024) return (bytes/(1024*1024*1024)).toFixed(2) + ' GB';
if (bytes >= 1024*1024) return (bytes/(1024*1024)).toFixed(2) + ' MB';
if (bytes >= 1024) return (bytes/1024).toFixed(2) + ' KB';
return bytes + ' B';
}

window.dtCalculate = function() {
var sizeVal = parseFloat(document.getElementById('dt-filesize').value);
var sizeUnit = document.getElementById('dt-sizeunit').value;
var speedMbps = parseFloat(document.getElementById('dt-speed').value);
var errEl = document.getElementById('dt-error');
var resBox = document.getElementById('dt-result');

if (!sizeVal || sizeVal <= 0 || !speedMbps || speedMbps <= 0) {
errEl.style.display = 'block';
resBox.classList.remove('show');
return;
}
errEl.style.display = 'none';

var bytes = dtToBytes(sizeVal, sizeUnit);
var bits = bytes * 8;
var bitsPerSec = speedMbps * 1000000;
var seconds = bits / bitsPerSec;

document.getElementById('dt-result-time').textContent = dtFormatTime(seconds);
document.getElementById('dt-result-detail').innerHTML =
'ファイルサイズ：<strong>' + dtFormatSize(bytes) + '</strong><br>' +
'通信速度：<strong>' + speedMbps + ' Mbps</strong>（' + (speedMbps/8).toFixed(2) + ' MB/s）<br>' +
'合計秒数：<strong>' + Math.round(seconds).toLocaleString() + ' 秒</strong>';
resBox.classList.add('show');

dtBuildTable(bytes, sizeVal, sizeUnit);
};

function dtBuildTable(bytes, sizeVal, sizeUnit) {
var cols = [
{ label: sizeVal + ' ' + sizeUnit, bytes: bytes },
{ label: dtFormatSize(bytes * 5), bytes: bytes * 5 },
{ label: dtFormatSize(bytes * 20), bytes: bytes * 20 }
];
document.getElementById('th-col1').textContent = cols[0].label;
document.getElementById('th-col2').textContent = cols[1].label;
document.getElementById('th-col3').textContent = cols[2].label;

var speeds = [
{ name: '3G（低速）', mbps: 1 },
{ name: '3G（標準）', mbps: 5 },
{ name: '4G LTE', mbps: 25 },
{ name: '4G+', mbps: 50 },
{ name: 'Wi-Fi（100 Mbps）', mbps: 100 },
{ name: 'Wi-Fi（300 Mbps）', mbps: 300 },
{ name: '光回線（500 Mbps）', mbps: 500 },
{ name: '光回線（1 Gbps）', mbps: 1000 }
];

var currentSpeed = parseFloat(document.getElementById('dt-speed').value);
var tbody = document.getElementById('dt-tbody');
tbody.innerHTML = '';

speeds.forEach(function(sp) {
var bps = sp.mbps * 1000000;
var tr = document.createElement('tr');
if (sp.mbps === currentSpeed) tr.className = 'highlight-row';
var tdName = document.createElement('td');
tdName.textContent = sp.name;
var tdSpeed = document.createElement('td');
tdSpeed.textContent = sp.mbps >= 1000 ? (sp.mbps/1000) + ' Gbps' : sp.mbps + ' Mbps';
tr.appendChild(tdName);
tr.appendChild(tdSpeed);
cols.forEach(function(col) {
var td = document.createElement('td');
var secs = (col.bytes * 8) / bps;
td.textContent = dtFormatTimeShort(secs);
tr.appendChild(td);
});
tbody.appendChild(tr);
});
}

// Initialize table with defaults
dtBuildTable(1024*1024*100, 100, 'MB');
document.getElementById('th-col1').textContent = '100 MB';
document.getElementById('th-col2').textContent = '500 MB';
document.getElementById('th-col3').textContent = '2 GB';

window.dtConvert = function(source) {
var mbps, val;
var fields = {
mbps:  document.getElementById('cv-mbps'),
mbps2: document.getElementById('cv-mbps2'),
kbps:  document.getElementById('cv-kbps'),
kbps2: document.getElementById('cv-kbps2'),
gbps:  document.getElementById('cv-gbps')
};
val = parseFloat(fields[source].value);
if (isNaN(val) || val < 0) return;
switch(source) {
case 'mbps':  mbps = val; break;
case 'mbps2': mbps = val * 8; break;
case 'kbps':  mbps = val / 1000; break;
case 'kbps2': mbps = val * 8 / 1000; break;
case 'gbps':  mbps = val * 1000; break;
}
if (source !== 'mbps')  fields.mbps.value  = +mbps.toPrecision(6);
if (source !== 'mbps2') fields.mbps2.value = +(mbps / 8).toPrecision(6);
if (source !== 'kbps')  fields.kbps.value  = +(mbps * 1000).toPrecision(6);
if (source !== 'kbps2') fields.kbps2.value = +(mbps * 1000 / 8).toPrecision(6);
if (source !== 'gbps')  fields.gbps.value  = +(mbps / 1000).toPrecision(6);
};
})();
</script>
</div>

## 関連記事

- [光回線 おすすめ2026年版！速度・料金・キャッシュバックで比較](/ja/posts/hikari-kaisen-osusume-2026/)
- [WiFiルーター おすすめ2026年版！速度・範囲・価格で選ぶ最強機種](/ja/posts/wifi-router-osusume-2026/)
