---
title: "Currency Converter - Exchange Rate Calculator"
date: 2025-05-16
description: "Convert between major world currencies. Reference exchange rates for USD, EUR, GBP, JPY, and more. Includes conversion table."
categories: ["Free Tools"]
slug: "currency-converter"
ShowToc: false
cover:
  image: "/images/covers/currency-converter.png"
  alt: "Currency Converter"
---

<div id="crc-app">

<style>
#crc-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1a1a2e;
}
#crc-app h2 {
font-size: 1.25rem;
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
font-weight: 600;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.04em;
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
text-transform: uppercase;
letter-spacing: 0.03em;
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
line-height: 1.6;
}
#crc-app .crc-related {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-top: 1rem;
}
#crc-app .crc-related p {
margin: 0 0 0.4rem;
font-weight: 700;
font-size: 0.9rem;
color: #475569;
}
#crc-app .crc-related a {
display: inline-block;
margin: 0.2rem 0.4rem 0.2rem 0;
padding: 0.3rem 0.75rem;
background: #fff;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 0.82rem;
color: #3b82f6;
text-decoration: none;
transition: border-color 0.15s, background 0.15s;
}
#crc-app .crc-related a:hover {
background: #eff6ff;
border-color: #3b82f6;
}
</style>

## Currency Converter

Convert any amount between 12 major world currencies using reference exchange rates.

<div class="crc-card">
<div class="crc-row">
<div class="crc-field">
<label>Amount</label>
<input type="number" id="crc-amount" value="100" min="0" step="any" oninput="crcConvert()">
</div>
<div class="crc-field">
<label>From</label>
<select id="crc-from" onchange="crcConvert()"></select>
</div>
<button class="crc-swap-btn" onclick="crcSwap()" title="Swap currencies">&#8644;</button>
<div class="crc-field">
<label>To</label>
<select id="crc-to" onchange="crcConvert()"></select>
</div>
</div>
<div class="crc-result-box" id="crc-result-box">
<div class="crc-result-main" id="crc-result-main">—</div>
<div class="crc-result-sub" id="crc-result-sub"></div>
<div class="crc-disclaimer">* Rates are approximate reference values. Not for financial transactions.</div>
</div>
</div>

## Quick Conversion Table

<div class="crc-card">
<table id="crc-quick-table">
<thead>
<tr>
<th>Amount (From Currency)</th>
<th>Result (To Currency)</th>
</tr>
</thead>
<tbody id="crc-quick-body"></tbody>
</table>
</div>

## All Currencies vs. 1 Unit

<div class="crc-card">
<p style="font-size:0.85rem;color:#64748b;margin-top:0;">Shows how much 1 unit of your <strong>From</strong> currency buys in every currency.</p>
<table id="crc-all-table">
<thead>
<tr>
<th>Currency</th>
<th>Rate (1 unit of From)</th>
</tr>
</thead>
<tbody id="crc-all-body"></tbody>
</table>
<div class="crc-note">
Reference rates as of approx. May 2025. Exchange rates fluctuate daily due to market conditions, inflation, interest rates, and geopolitical events. Always check a live rate source (e.g., your bank or XE.com) before making any financial decision.
</div>
</div>

<div class="crc-related">
<p>Related free tools</p>
<a href="/tools/percentage-calculator/">Percentage Calculator</a>
<a href="/tools/unit-converter/">Unit Converter</a>
<a href="/tools/tax-calculator/">Tax Calculator</a>
<a href="/tools/compound-interest-calculator/">Compound Interest</a>
</div>

<script>
(function() {
const CRC_CURRENCIES = [
{ code: "USD", name: "US Dollar",         flag: "🇺🇸", rateToUSD: 1 },
{ code: "EUR", name: "Euro",               flag: "🇪🇺", rateToUSD: 0.924 },
{ code: "GBP", name: "British Pound",      flag: "🇬🇧", rateToUSD: 0.792 },
{ code: "JPY", name: "Japanese Yen",       flag: "🇯🇵", rateToUSD: 155.2 },
{ code: "CNY", name: "Chinese Yuan",       flag: "🇨🇳", rateToUSD: 7.24 },
{ code: "KRW", name: "South Korean Won",   flag: "🇰🇷", rateToUSD: 1370 },
{ code: "AUD", name: "Australian Dollar",  flag: "🇦🇺", rateToUSD: 1.535 },
{ code: "CAD", name: "Canadian Dollar",    flag: "🇨🇦", rateToUSD: 1.362 },
{ code: "CHF", name: "Swiss Franc",        flag: "🇨🇭", rateToUSD: 0.904 },
{ code: "SGD", name: "Singapore Dollar",   flag: "🇸🇬", rateToUSD: 1.348 },
{ code: "HKD", name: "Hong Kong Dollar",   flag: "🇭🇰", rateToUSD: 7.785 },
{ code: "TWD", name: "New Taiwan Dollar",  flag: "🇹🇼", rateToUSD: 32.1 },
];

const QUICK_AMOUNTS = [1, 5, 10, 50, 100, 500, 1000];

function fmt(val, code) {
const big = ["JPY","KRW","TWD"];
const decimals = big.includes(code) ? 0 : 2;
return val.toLocaleString("en-US", { minimumFractionDigits: decimals, maximumFractionDigits: decimals });
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
fromSel.value = "USD";
toSel.value   = "EUR";
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
"  (1 " + fromCode + " = " + fmt(rate, toCode) + " " + toCode + ")";

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

## Related Tools

> [Dividend Income Calculator](/tools/dividend-income-calculator/)
> [Forex Profit Calculator](/tools/forex-profit-calculator/)

## Related Articles

- [Best Forex Brokers 2026: Platforms for Beginners & Traders](/posts/best-forex-brokers-2026/)
- [Best FX Brokers for English Speakers in Japan 2026: What to Look For](/posts/best-fx-brokers-japan-english/)
