---
title: "Tip & Bill Splitter - Split Bills Fairly"
description: "Calculate tips and split bills evenly among friends. Free tip calculator with per-person breakdown."
date: 2025-05-16
slug: "tip-splitter"
categories: ["Free Tools"]
tags: ["Developer Tools", "Programming", "Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/tip-splitter.png"
---

<div id="ts-app">

<style>
#ts-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 680px;
margin: 0 auto;
color: #1a1a2e;
}
#ts-app * {
box-sizing: border-box;
}
#ts-app h2 {
font-size: 1.4rem;
font-weight: 700;
margin: 0 0 1.2rem 0;
color: #1a1a2e;
display: flex;
align-items: center;
gap: 0.5rem;
}
#ts-app .ts-card {
background: #fff;
border: 1.5px solid #e5e7eb;
border-radius: 14px;
padding: 1.5rem;
margin-bottom: 1.2rem;
box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
#ts-app label {
display: block;
font-size: 0.85rem;
font-weight: 600;
color: #374151;
margin-bottom: 0.4rem;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#ts-app input[type="number"] {
width: 100%;
padding: 0.7rem 1rem;
font-size: 1.1rem;
border: 1.5px solid #d1d5db;
border-radius: 8px;
outline: none;
transition: border-color 0.2s;
color: #1a1a2e;
background: #f9fafb;
}
#ts-app input[type="number"]:focus {
border-color: #6366f1;
background: #fff;
}
#ts-app .ts-input-prefix {
position: relative;
}
#ts-app .ts-input-prefix span {
position: absolute;
left: 0.9rem;
top: 50%;
transform: translateY(-50%);
font-size: 1.1rem;
color: #6b7280;
font-weight: 600;
pointer-events: none;
}
#ts-app .ts-input-prefix input {
padding-left: 2rem;
}
#ts-app .ts-tip-row {
display: flex;
align-items: center;
gap: 1rem;
margin-bottom: 0.8rem;
}
#ts-app .ts-tip-row input[type="range"] {
flex: 1;
-webkit-appearance: none;
height: 6px;
background: #e5e7eb;
border-radius: 3px;
outline: none;
cursor: pointer;
}
#ts-app input[type="range"]::-webkit-slider-thumb {
-webkit-appearance: none;
width: 20px;
height: 20px;
border-radius: 50%;
background: #6366f1;
cursor: pointer;
box-shadow: 0 1px 4px rgba(99,102,241,0.4);
}
#ts-app .ts-tip-pct-display {
min-width: 3.5rem;
text-align: center;
font-size: 1.3rem;
font-weight: 700;
color: #6366f1;
}
#ts-app .ts-quick-btns {
display: flex;
gap: 0.5rem;
flex-wrap: wrap;
}
#ts-app .ts-quick-btn {
padding: 0.4rem 0.9rem;
border: 1.5px solid #6366f1;
border-radius: 20px;
background: transparent;
color: #6366f1;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#ts-app .ts-quick-btn:hover,
#ts-app .ts-quick-btn.active {
background: #6366f1;
color: #fff;
}
#ts-app .ts-toggle-row {
display: flex;
align-items: center;
justify-content: space-between;
padding: 0.6rem 0;
border-bottom: 1px solid #f3f4f6;
font-size: 0.95rem;
color: #374151;
}
#ts-app .ts-toggle-row:last-child {
border-bottom: none;
}
#ts-app .ts-toggle {
position: relative;
width: 44px;
height: 24px;
}
#ts-app .ts-toggle input {
opacity: 0;
width: 0;
height: 0;
position: absolute;
}
#ts-app .ts-toggle-slider {
position: absolute;
inset: 0;
background: #d1d5db;
border-radius: 24px;
cursor: pointer;
transition: background 0.2s;
}
#ts-app .ts-toggle-slider::before {
content: "";
position: absolute;
width: 18px;
height: 18px;
left: 3px;
top: 3px;
background: #fff;
border-radius: 50%;
transition: transform 0.2s;
box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
#ts-app .ts-toggle input:checked + .ts-toggle-slider {
background: #6366f1;
}
#ts-app .ts-toggle input:checked + .ts-toggle-slider::before {
transform: translateX(20px);
}
#ts-app .ts-results {
background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
border-radius: 14px;
padding: 1.5rem;
color: #fff;
margin-bottom: 1.2rem;
}
#ts-app .ts-results h2 {
color: #fff;
margin-bottom: 1rem;
}
#ts-app .ts-result-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 0.8rem;
margin-bottom: 1rem;
}
#ts-app .ts-result-item {
background: rgba(255,255,255,0.15);
border-radius: 10px;
padding: 0.9rem 1rem;
}
#ts-app .ts-result-item .label {
font-size: 0.78rem;
opacity: 0.85;
margin-bottom: 0.3rem;
text-transform: uppercase;
letter-spacing: 0.05em;
font-weight: 600;
}
#ts-app .ts-result-item .value {
font-size: 1.5rem;
font-weight: 800;
}
#ts-app .ts-result-highlight {
background: rgba(255,255,255,0.25);
border-radius: 10px;
padding: 1rem;
text-align: center;
}
#ts-app .ts-result-highlight .label {
font-size: 0.85rem;
opacity: 0.9;
margin-bottom: 0.3rem;
text-transform: uppercase;
letter-spacing: 0.05em;
font-weight: 600;
}
#ts-app .ts-result-highlight .value {
font-size: 2.2rem;
font-weight: 800;
}
#ts-app .ts-custom-split {
margin-top: 1rem;
}
#ts-app .ts-person-row {
display: flex;
align-items: center;
gap: 0.7rem;
margin-bottom: 0.6rem;
}
#ts-app .ts-person-row label {
margin: 0;
font-size: 0.9rem;
font-weight: 600;
min-width: 70px;
text-transform: none;
letter-spacing: 0;
color: #374151;
}
#ts-app .ts-person-row input[type="number"] {
flex: 1;
font-size: 1rem;
padding: 0.55rem 0.8rem;
}
#ts-app .ts-person-share {
min-width: 90px;
text-align: right;
font-weight: 700;
color: #6366f1;
font-size: 1rem;
}
#ts-app .ts-custom-total-row {
display: flex;
justify-content: space-between;
align-items: center;
padding: 0.7rem 0.2rem 0;
border-top: 2px dashed #e5e7eb;
margin-top: 0.4rem;
font-weight: 700;
font-size: 0.95rem;
color: #374151;
}
#ts-app .ts-custom-total-row span:last-child {
color: #ef4444;
}
#ts-app .ts-calc-btn {
width: 100%;
padding: 0.95rem;
background: #6366f1;
color: #fff;
font-size: 1.1rem;
font-weight: 700;
border: none;
border-radius: 10px;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
margin-bottom: 1rem;
}
#ts-app .ts-calc-btn:hover {
background: #4f46e5;
}
#ts-app .ts-calc-btn:active {
transform: scale(0.98);
}
#ts-app .ts-section-label {
font-size: 0.78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #9ca3af;
margin-bottom: 0.8rem;
}
#ts-app .ts-related {
border-top: 1.5px solid #e5e7eb;
padding-top: 1.2rem;
margin-top: 0.5rem;
}
#ts-app .ts-related h3 {
font-size: 1rem;
font-weight: 700;
margin: 0 0 0.7rem 0;
color: #374151;
}
#ts-app .ts-related ul {
margin: 0;
padding: 0 0 0 1.2rem;
list-style: disc;
color: #6366f1;
font-size: 0.95rem;
line-height: 1.8;
}
#ts-app .ts-related a {
color: #6366f1;
text-decoration: none;
font-weight: 600;
}
#ts-app .ts-related a:hover {
text-decoration: underline;
}
#ts-app .ts-warning {
font-size: 0.82rem;
color: #ef4444;
font-weight: 600;
margin-top: 0.3rem;
display: none;
}
#ts-app .ts-warning.visible {
display: block;
}
@media (max-width: 480px) {
#ts-app .ts-result-grid {
grid-template-columns: 1fr;
}
#ts-app .ts-result-item .value {
font-size: 1.3rem;
}
}
</style>

<!-- INPUTS -->
<div class="ts-card">
<h2>Bill Details</h2>

<div style="margin-bottom:1.2rem;">
<label for="ts-bill">Bill Amount</label>
<div class="ts-input-prefix">
<span>$</span>
<input type="number" id="ts-bill" min="0" step="0.01" placeholder="0.00" value="" />
</div>
</div>

<div style="margin-bottom:1.2rem;">
<label>Tip Percentage</label>
<div class="ts-tip-row">
<input type="range" id="ts-tip-slider" min="0" max="30" step="1" value="18" />
<div class="ts-tip-pct-display"><span id="ts-tip-pct-val">18</span>%</div>
</div>
<div class="ts-quick-btns">
<button class="ts-quick-btn" data-pct="0">No Tip</button>
<button class="ts-quick-btn" data-pct="15">15%</button>
<button class="ts-quick-btn active" data-pct="18">18%</button>
<button class="ts-quick-btn" data-pct="20">20%</button>
<button class="ts-quick-btn" data-pct="25">25%</button>
</div>
</div>

<div>
<label for="ts-people">Number of People</label>
<input type="number" id="ts-people" min="1" step="1" value="2" placeholder="2" />
</div>
</div>

<!-- OPTIONS -->
<div class="ts-card">
<h2>Options</h2>
<div class="ts-toggle-row">
<span>Round up per-person amount (to nearest dollar)</span>
<label class="ts-toggle">
<input type="checkbox" id="ts-roundup" />
<span class="ts-toggle-slider"></span>
</label>
</div>
<div class="ts-toggle-row">
<span>Tip on pre-tax amount (toggle off = tip after tax)</span>
<label class="ts-toggle">
<input type="checkbox" id="ts-pretax" />
<span class="ts-toggle-slider"></span>
</label>
</div>
<div id="ts-pretax-row" style="display:none; margin-top:0.9rem;">
<label for="ts-tax">Tax Amount ($)</label>
<div class="ts-input-prefix">
<span>$</span>
<input type="number" id="ts-tax" min="0" step="0.01" placeholder="0.00" value="" />
</div>
</div>
<div class="ts-toggle-row" style="margin-top:0.6rem;">
<span>Custom split (unequal amounts)</span>
<label class="ts-toggle">
<input type="checkbox" id="ts-custom-toggle" />
<span class="ts-toggle-slider"></span>
</label>
</div>
</div>

<!-- CALCULATE BUTTON -->
<button class="ts-calc-btn" id="ts-calc-btn">Calculate Split</button>

<!-- RESULTS -->
<div class="ts-results" id="ts-results" style="display:none;">
<h2>Results</h2>
<div class="ts-result-grid">
<div class="ts-result-item">
<div class="label">Tip Amount</div>
<div class="value" id="ts-res-tip">$0.00</div>
</div>
<div class="ts-result-item">
<div class="label">Total with Tip</div>
<div class="value" id="ts-res-total">$0.00</div>
</div>
</div>
<div class="ts-result-highlight">
<div class="label">Each Person Pays</div>
<div class="value" id="ts-res-per-person">$0.00</div>
</div>
</div>

<!-- CUSTOM SPLIT PANEL -->
<div class="ts-card ts-custom-split" id="ts-custom-panel" style="display:none;">
<h2>Custom Split</h2>
<p style="font-size:0.88rem; color:#6b7280; margin: 0 0 1rem 0;">
Assign a share weight to each person. Amounts will be proportionally divided from the total with tip.
</p>
<div id="ts-person-rows"></div>
<div class="ts-custom-total-row">
<span>Total accounted:</span>
<span id="ts-custom-total-display">$0.00</span>
</div>
<div class="ts-warning" id="ts-custom-warning">Total does not match bill total — adjust shares.</div>
</div>

<!-- RELATED TOOLS -->
<div class="ts-related">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/loan-calculator/">Loan &amp; Mortgage Calculator</a></li>
<li><a href="/tools/compound-interest-calculator/">Compound Interest Calculator</a></li>
<li><a href="/tools/currency-converter/">Currency Converter</a></li>
<li><a href="/tools/budget-planner/">Monthly Budget Planner</a></li>
</ul>
</div>

<script>
(function () {
"use strict";

var slider = document.getElementById("ts-tip-slider");
var pctVal = document.getElementById("ts-tip-pct-val");
var quickBtns = document.querySelectorAll("#ts-app .ts-quick-btn");
var billInput = document.getElementById("ts-bill");
var peopleInput = document.getElementById("ts-people");
var roundupCb = document.getElementById("ts-roundup");
var pretaxCb = document.getElementById("ts-pretax");
var pretaxRow = document.getElementById("ts-pretax-row");
var taxInput = document.getElementById("ts-tax");
var customToggle = document.getElementById("ts-custom-toggle");
var customPanel = document.getElementById("ts-custom-panel");
var personRowsEl = document.getElementById("ts-person-rows");
var customTotalDisplay = document.getElementById("ts-custom-total-display");
var customWarning = document.getElementById("ts-custom-warning");
var calcBtn = document.getElementById("ts-calc-btn");
var resultsEl = document.getElementById("ts-results");
var resTip = document.getElementById("ts-res-tip");
var resTotal = document.getElementById("ts-res-total");
var resPerPerson = document.getElementById("ts-res-per-person");

function fmt(n) {
return "$" + n.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}

function setSlider(val) {
slider.value = val;
pctVal.textContent = val;
quickBtns.forEach(function (b) {
b.classList.toggle("active", parseInt(b.dataset.pct) === parseInt(val));
});
}

slider.addEventListener("input", function () {
setSlider(slider.value);
if (resultsEl.style.display !== "none") calculate();
});

quickBtns.forEach(function (btn) {
btn.addEventListener("click", function () {
setSlider(parseInt(btn.dataset.pct));
if (resultsEl.style.display !== "none") calculate();
});
});

pretaxCb.addEventListener("change", function () {
pretaxRow.style.display = pretaxCb.checked ? "block" : "none";
if (resultsEl.style.display !== "none") calculate();
});

[billInput, peopleInput, taxInput, roundupCb].forEach(function (el) {
el.addEventListener("input", function () {
if (resultsEl.style.display !== "none") calculate();
});
});

customToggle.addEventListener("change", function () {
if (customToggle.checked) {
customPanel.style.display = "block";
buildPersonRows();
} else {
customPanel.style.display = "none";
}
if (resultsEl.style.display !== "none") calculate();
});

function buildPersonRows() {
var n = Math.max(1, parseInt(peopleInput.value) || 2);
personRowsEl.innerHTML = "";
for (var i = 1; i <= n; i++) {
var row = document.createElement("div");
row.className = "ts-person-row";

var lbl = document.createElement("label");
lbl.textContent = "Person " + i;

var inp = document.createElement("input");
inp.type = "number";
inp.min = "0";
inp.step = "0.01";
inp.placeholder = "0.00";
inp.dataset.person = i;
inp.className = "ts-share-input";
inp.addEventListener("input", updateCustomTotals);

var share = document.createElement("div");
share.className = "ts-person-share";
share.id = "ts-person-share-" + i;
share.textContent = "$0.00";

row.appendChild(lbl);
row.appendChild(inp);
row.appendChild(share);
personRowsEl.appendChild(row);
}
updateCustomTotals();
}

function updateCustomTotals() {
var inputs = document.querySelectorAll("#ts-app .ts-share-input");
var sum = 0;
inputs.forEach(function (inp) {
sum += parseFloat(inp.value) || 0;
});
customTotalDisplay.textContent = fmt(sum);

var bill = parseFloat(billInput.value) || 0;
var tipPct = parseInt(slider.value) || 0;
var taxAmt = pretaxCb.checked ? (parseFloat(taxInput.value) || 0) : 0;
var tipBase = pretaxCb.checked ? bill : (bill + taxAmt);
var tipAmt = tipBase * (tipPct / 100);
var grandTotal = bill + taxAmt + tipAmt;

if (sum > 0 && grandTotal > 0) {
inputs.forEach(function (inp) {
var personAmt = (parseFloat(inp.value) || 0);
var ratio = personAmt / sum;
var share = ratio * grandTotal;
if (roundupCb.checked) share = Math.ceil(share);
var idx = inp.dataset.person;
var shareEl = document.getElementById("ts-person-share-" + idx);
if (shareEl) shareEl.textContent = fmt(share);
});
var diff = Math.abs(sum - grandTotal);
customWarning.classList.toggle("visible", diff > 0.02);
}
customTotalDisplay.textContent = fmt(sum);
}

peopleInput.addEventListener("input", function () {
if (customToggle.checked) buildPersonRows();
if (resultsEl.style.display !== "none") calculate();
});

function calculate() {
var bill = parseFloat(billInput.value);
if (isNaN(bill) || bill < 0) { resultsEl.style.display = "none"; return; }

var n = Math.max(1, parseInt(peopleInput.value) || 1);
var tipPct = parseInt(slider.value) || 0;
var taxAmt = pretaxCb.checked ? (parseFloat(taxInput.value) || 0) : 0;
var tipBase = pretaxCb.checked ? bill : (bill + taxAmt);
var tipAmt = tipBase * (tipPct / 100);
var grandTotal = bill + taxAmt + tipAmt;
var perPerson = grandTotal / n;
if (roundupCb.checked) perPerson = Math.ceil(perPerson);

resTip.textContent = fmt(tipAmt);
resTotal.textContent = fmt(grandTotal);
resPerPerson.textContent = fmt(perPerson);
resultsEl.style.display = "block";

if (customToggle.checked) updateCustomTotals();
}

calcBtn.addEventListener("click", function () {
var bill = parseFloat(billInput.value);
if (isNaN(bill) || bill <= 0) {
billInput.focus();
billInput.style.borderColor = "#ef4444";
setTimeout(function () { billInput.style.borderColor = ""; }, 1500);
return;
}
if (customToggle.checked) buildPersonRows();
calculate();
resultsEl.scrollIntoView({ behavior: "smooth", block: "nearest" });
});

setSlider(18);
})();
</script>

</div>
