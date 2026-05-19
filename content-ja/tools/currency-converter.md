---
title: "通貨換算ツール - 為替レート計算機"
date: 2025-06-17
description: "主要通貨間の換算ができる無料ツール。USD・EUR・GBP・JPY・CNYなどの参考為替レートで変換。換算表付き。"
categories: ["無料ツール"]
slug: "currency-converter"
ShowToc: false
cover:
  image: "/images/covers/currency-converter.png"
  alt: "通貨換算ツール"
---

<div id="crc-app">

<style>
#crc-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic", "Segoe UI", sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1a1a2e;
}
#crc-app h2 {
font-size: 1.2rem;
font-weight: 700;
margin: 1.5rem 0 0.75rem;
color: #1a1a2e;
}
#crc-app .crc-card {
background: #ffffff;
border: 1px solid #e2e8f0;
border-radius: 12px;
padding: 1.5rem;
margin-bottom: 1.25rem;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
}
#crc-app .crc-row {
display: flex;
gap: 0.75rem;
align-items: flex-end;
flex-wrap: wrap;
}
#crc-app .crc-field {
display: flex;
flex-direction: column;
gap: 0.3rem;
flex: 1;
min-width: 120px;
}
#crc-app .crc-field label {
font-size: 0.78rem;
font-weight: 700;
color: #64748b;
letter-spacing: 0.03em;
}
#crc-app .crc-field input,
#crc-app .crc-field select {
padding: 0.6rem 0.75rem;
border: 1.5px solid #cbd5e1;
border-radius: 8px;
font-size: 1rem;
background: #f8fafc;
color: #1a1a2e;
outline: none;
transition: border-color 0.15s;
}
#crc-app .crc-field input:focus,
#crc-app .crc-field select:focus {
border-color: #3b82f6;
background: #fff;
}
#crc-app .crc-swap-btn {
background: #3b82f6;
color: #fff;
border: none;
border-radius: 8px;
padding: 0.6rem 1rem;
font-size: 1.15rem;
cursor: pointer;
transition: background 0.15s;
align-self: flex-end;
height: 42px;
}
#crc-app .crc-swap-btn:hover {
background: #2563eb;
}
#crc-app .crc-result-box {
margin-top: 1rem;
padding: 1rem 1.25rem;
background: linear-gradient(135deg, #eff6ff 0%, #f0fdf4 100%);
border-radius: 10px;
border: 1px solid #bfdbfe;
}
#crc-app .crc-result-main {
font-size: 2rem;
font-weight: 800;
color: #1d4ed8;
line-height: 1.1;
}
#crc-app .crc-result-sub {
font-size: 0.85rem;
color: #64748b;
margin-top: 0.3rem;
}
#crc-app .crc-disclaimer {
font-size: 0.75rem;
color: #94a3b8;
margin-top: 0.5rem;
font-style: italic;
}
#crc-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.9rem;
}
#crc-app table th {
background: #f1f5f9;
color: #475569;
font-weight: 700;
text-align: left;
padding: 0.55rem 0.75rem;
border-bottom: 2px solid #e2e8f0;
font-size: 0.8rem;
}
#crc-app table td {
padding: 0.5rem 0.75rem;
border-bottom: 1px solid #f1f5f9;
color: #334155;
}
#crc-app table tr:last-child td {
border-bottom: none;
}
#crc-app table tr:hover td {
background: #f8fafc;
}
#crc-app .crc-flag {
margin-right: 0.35rem;
}
#crc-app .crc-highlight td {
font-weight: 700;
color: #1d4ed8;
background: #eff6ff !important;
}
#crc-app .crc-note {
font-size: 0.78rem;
color: #94a3b8;
padding: 0.6rem 0;
line-height: 1.7;
}
#crc-app .crc-cta {
background: linear-gradient(135deg, #fefce8 0%, #fff7ed 100%);
border: 1px solid #fde68a;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-top: 1rem;
font-size: 0.9rem;
line-height: 1.7;
}
#crc-app .crc-cta strong {
color: #92400e;
}
</style>

## 通貨換算ツール

12の主要通貨間で金額を変換できます。参考為替レートを使用しています。

<div class="crc-card">
<div class="crc-row">
<div class="crc-field">
<label>金額</label>
<input type="number" id="crc-amount" value="1000" min="0" step="any" oninput="crcConvert()">
</div>
<div class="crc-field">
<label>変換元通貨</label>
<select id="crc-from" onchange="crcConvert()"></select>
</div>
<button class="crc-swap-btn" onclick="crcSwap()" title="通貨を入れ替え">&#8644;</button>
<div class="crc-field">
<label>変換先通貨</label>
<select id="crc-to" onchange="crcConvert()"></select>
</div>
</div>
<div class="crc-result-box" id="crc-result-box">
<div class="crc-result-main" id="crc-result-main">—</div>
<div class="crc-result-sub" id="crc-result-sub"></div>
<div class="crc-disclaimer">※ レートは参考値です。実際の取引レートとは異なる場合があります。</div>
</div>
</div>

## クイック換算表

<div class="crc-card">
<table id="crc-quick-table">
<thead>
<tr>
<th>変換元の金額</th>
<th>換算結果</th>
</tr>
</thead>
<tbody id="crc-quick-body"></tbody>
</table>
</div>

## 全通貨との比較（1単位あたり）

<div class="crc-card">
<p style="font-size:0.85rem;color:#64748b;margin-top:0;">「変換元通貨」1単位で各通貨をいくら換算できるかを表示します。</p>
<table id="crc-all-table">
<thead>
<tr>
<th>通貨</th>
<th>換算レート（変換元1単位）</th>
</tr>
</thead>
<tbody id="crc-all-body"></tbody>
</table>
<div class="crc-note">
※ 参考レートは2025年5月時点の概算値です。為替レートは市場の需給、各国の金融政策、インフレ率、地政学リスクなどによって日々変動します。実際の送金・両替・会計処理には、銀行や公式レートを必ずご確認ください。
</div>
</div>

<div class="crc-cta">
<strong>外貨管理を効率化</strong><br>
外貨建て取引が多い方は、為替差損益の自動計算が便利です。<br>
→ <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で為替差損益を自動計算</a>（外部リンク）
</div>

<script>
(function() {
const CRC_CURRENCIES = [
{ code: "JPY", name: "日本円",             flag: "🇯🇵", rateToUSD: 155.2 },
{ code: "USD", name: "米ドル",             flag: "🇺🇸", rateToUSD: 1 },
{ code: "EUR", name: "ユーロ",             flag: "🇪🇺", rateToUSD: 0.924 },
{ code: "GBP", name: "英ポンド",           flag: "🇬🇧", rateToUSD: 0.792 },
{ code: "CNY", name: "中国人民元",         flag: "🇨🇳", rateToUSD: 7.24 },
{ code: "KRW", name: "韓国ウォン",         flag: "🇰🇷", rateToUSD: 1370 },
{ code: "AUD", name: "オーストラリアドル", flag: "🇦🇺", rateToUSD: 1.535 },
{ code: "CAD", name: "カナダドル",         flag: "🇨🇦", rateToUSD: 1.362 },
{ code: "CHF", name: "スイスフラン",       flag: "🇨🇭", rateToUSD: 0.904 },
{ code: "SGD", name: "シンガポールドル",   flag: "🇸🇬", rateToUSD: 1.348 },
{ code: "HKD", name: "香港ドル",           flag: "🇭🇰", rateToUSD: 7.785 },
{ code: "TWD", name: "台湾ドル",           flag: "🇹🇼", rateToUSD: 32.1 },
];

const QUICK_AMOUNTS = [100, 500, 1000, 5000, 10000, 50000, 100000];

function fmt(val, code) {
const big = ["JPY","KRW","TWD"];
const decimals = big.includes(code) ? 0 : 2;
return val.toLocaleString("ja-JP", { minimumFractionDigits: decimals, maximumFractionDigits: decimals });
}

function getRate(fromCode, toCode) {
const from = CRC_CURRENCIES.find(c => c.code === fromCode);
const to   = CRC_CURRENCIES.find(c => c.code === toCode);
if (!from || !to) return null;
return to.rateToUSD / from.rateToUSD;
}

function populateSelects() {
const fromSel = document.getElementById("crc-from");
const toSel   = document.getElementById("crc-to");
CRC_CURRENCIES.forEach(c => {
const o1 = document.createElement("option");
o1.value = c.code;
o1.textContent = c.flag + " " + c.code + " — " + c.name;
fromSel.appendChild(o1);
const o2 = o1.cloneNode(true);
toSel.appendChild(o2);
});
fromSel.value = "JPY";
toSel.value   = "USD";
}

function crcConvert() {
const amount = parseFloat(document.getElementById("crc-amount").value) || 0;
const fromCode = document.getElementById("crc-from").value;
const toCode   = document.getElementById("crc-to").value;
const rate = getRate(fromCode, toCode);
const result = amount * rate;

const fromCur = CRC_CURRENCIES.find(c => c.code === fromCode);
const toCur   = CRC_CURRENCIES.find(c => c.code === toCode);

document.getElementById("crc-result-main").textContent =
toCur.flag + " " + fmt(result, toCode) + " " + toCode;
document.getElementById("crc-result-sub").textContent =
fromCur.flag + " " + fmt(amount, fromCode) + " " + fromCode +
" = " + toCur.flag + " " + fmt(result, toCode) + " " + toCode +
"  （1 " + fromCode + " = " + fmt(rate, toCode) + " " + toCode + "）";

updateQuickTable(fromCode, toCode);
updateAllTable(fromCode);
}

function updateQuickTable(fromCode, toCode) {
const rate = getRate(fromCode, toCode);
const tbody = document.getElementById("crc-quick-body");
const currentAmount = parseFloat(document.getElementById("crc-amount").value) || 0;
tbody.innerHTML = "";
QUICK_AMOUNTS.forEach(a => {
const tr = document.createElement("tr");
const isClose = Math.abs(a - currentAmount) < 0.001;
if (isClose) tr.className = "crc-highlight";
tr.innerHTML = "<td>" + fmt(a, fromCode) + " " + fromCode + "</td>" +
"<td>" + fmt(a * rate, toCode) + " " + toCode + "</td>";
tbody.appendChild(tr);
});
}

function updateAllTable(fromCode) {
const toCode = document.getElementById("crc-to").value;
const tbody = document.getElementById("crc-all-body");
tbody.innerHTML = "";
CRC_CURRENCIES.forEach(c => {
const rate = getRate(fromCode, c.code);
const tr = document.createElement("tr");
if (c.code === toCode) tr.className = "crc-highlight";
tr.innerHTML = "<td><span class='crc-flag'>" + c.flag + "</span>" + c.code + " — " + c.name + "</td>" +
"<td>" + fmt(rate, c.code) + " " + c.code + "</td>";
tbody.appendChild(tr);
});
}

window.crcConvert = crcConvert;

window.crcSwap = function() {
const fromSel = document.getElementById("crc-from");
const toSel   = document.getElementById("crc-to");
const tmp = fromSel.value;
fromSel.value = toSel.value;
toSel.value = tmp;
crcConvert();
};

populateSelects();
crcConvert();
})();
</script>

</div>

---

## 関連ツール

> 配当金計算 → [配当金計算ツール](/ja/tools/dividend-income-calculator/)
> FX利益計算 → [FX利益計算ツール](/ja/tools/forex-profit-calculator/)
> FX利益計算 → [FX利益計算ツール](/ja/tools/fx-profit-calculator/)

## 関連記事

- [DMM FXの口座開設のやり方｜初心者でも10分で完了する全手順【2026年版】](/ja/posts/dmm-fx-koza-kaisetsu-yarikata-2026/)
- [FX口座 おすすめ2026年版！初心者向けに比較【少額から始められる】](/ja/posts/kaigai-fx-osusume-2026/)
