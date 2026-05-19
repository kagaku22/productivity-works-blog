---
title: "Credit Card Validator - Luhn Algorithm Checker"
date: 2025-05-16
description: "Validate credit card numbers using the Luhn algorithm. Detect card type (Visa, Mastercard, Amex, etc). Educational tool for understanding card number structure."
categories: ["Free Tools"]
slug: "credit-card-validator"
ShowToc: false
cover:
  image: "/images/covers/credit-card-validator.png"
  alt: "Credit Card Validator"
---

<div id="ccv-app">

<style>
#ccv-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1a1a2e;
}
#ccv-app * { box-sizing: border-box; }

#ccv-app .ccv-intro {
background: #f0f4ff;
border-left: 4px solid #4a6cf7;
padding: 14px 18px;
border-radius: 0 8px 8px 0;
margin-bottom: 28px;
font-size: 0.95rem;
color: #444;
}

/* Card Visual */
#ccv-app .ccv-card-visual {
width: 340px;
height: 200px;
border-radius: 16px;
margin: 0 auto 28px;
position: relative;
padding: 24px 28px;
color: #fff;
background: linear-gradient(135deg, #1a1a2e 0%, #16213e 60%, #0f3460 100%);
box-shadow: 0 10px 40px rgba(0,0,0,0.25);
overflow: hidden;
transition: background 0.4s ease;
}
#ccv-app .ccv-card-visual::before {
content: '';
position: absolute;
top: -40px; right: -40px;
width: 180px; height: 180px;
border-radius: 50%;
background: rgba(255,255,255,0.05);
}
#ccv-app .ccv-card-visual::after {
content: '';
position: absolute;
bottom: -60px; right: 40px;
width: 200px; height: 200px;
border-radius: 50%;
background: rgba(255,255,255,0.04);
}
#ccv-app .ccv-card-visual.visa-card   { background: linear-gradient(135deg, #1a1f71 0%, #1565c0 100%); }
#ccv-app .ccv-card-visual.mc-card     { background: linear-gradient(135deg, #eb001b 0%, #f79e1b 100%); }
#ccv-app .ccv-card-visual.amex-card   { background: linear-gradient(135deg, #007b5e 0%, #00b09b 100%); }
#ccv-app .ccv-card-visual.discover-card { background: linear-gradient(135deg, #f7941d 0%, #ffd200 100%); }
#ccv-app .ccv-card-visual.jcb-card    { background: linear-gradient(135deg, #003087 0%, #009246 100%); }
#ccv-app .ccv-card-visual.diners-card { background: linear-gradient(135deg, #4a4a4a 0%, #888 100%); }

#ccv-app .ccv-card-brand {
font-size: 1.1rem;
font-weight: 700;
letter-spacing: 2px;
text-transform: uppercase;
opacity: 0.9;
margin-bottom: 30px;
}
#ccv-app .ccv-card-number-display {
font-size: 1.3rem;
letter-spacing: 4px;
font-family: 'Courier New', monospace;
margin-bottom: 20px;
word-spacing: 8px;
}
#ccv-app .ccv-card-footer {
display: flex;
justify-content: space-between;
font-size: 0.75rem;
opacity: 0.7;
text-transform: uppercase;
letter-spacing: 1px;
}

/* Input Area */
#ccv-app .ccv-input-section {
background: #fff;
border: 2px solid #e0e7ff;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
}
#ccv-app .ccv-label {
display: block;
font-weight: 600;
margin-bottom: 8px;
color: #333;
font-size: 0.95rem;
}
#ccv-app .ccv-input-row {
display: flex;
gap: 12px;
align-items: center;
flex-wrap: wrap;
}
#ccv-app .ccv-number-input {
flex: 1;
min-width: 200px;
padding: 14px 18px;
font-size: 1.2rem;
letter-spacing: 3px;
font-family: 'Courier New', monospace;
border: 2px solid #d0d8ff;
border-radius: 10px;
outline: none;
transition: border-color 0.2s;
background: #fafbff;
}
#ccv-app .ccv-number-input:focus { border-color: #4a6cf7; background: #fff; }
#ccv-app .ccv-number-input.valid   { border-color: #22c55e; background: #f0fff4; }
#ccv-app .ccv-number-input.invalid { border-color: #ef4444; background: #fff5f5; }

#ccv-app .ccv-btn {
padding: 14px 22px;
border: none;
border-radius: 10px;
font-size: 0.95rem;
font-weight: 600;
cursor: pointer;
transition: all 0.2s;
}
#ccv-app .ccv-btn-primary {
background: #4a6cf7;
color: #fff;
}
#ccv-app .ccv-btn-primary:hover { background: #3a5ce6; transform: translateY(-1px); }
#ccv-app .ccv-btn-secondary {
background: #f0f4ff;
color: #4a6cf7;
border: 2px solid #d0d8ff;
}
#ccv-app .ccv-btn-secondary:hover { background: #e0e7ff; }

/* Result Badge */
#ccv-app .ccv-result-badge {
display: none;
align-items: center;
gap: 10px;
padding: 14px 20px;
border-radius: 10px;
font-weight: 600;
font-size: 1rem;
margin-top: 16px;
}
#ccv-app .ccv-result-badge.show { display: flex; }
#ccv-app .ccv-result-badge.valid-badge {
background: #f0fff4;
border: 2px solid #22c55e;
color: #15803d;
}
#ccv-app .ccv-result-badge.invalid-badge {
background: #fff5f5;
border: 2px solid #ef4444;
color: #b91c1c;
}
#ccv-app .ccv-result-icon { font-size: 1.4rem; }

/* Card Details */
#ccv-app .ccv-details-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
gap: 12px;
margin-top: 16px;
}
#ccv-app .ccv-detail-box {
background: #f8faff;
border: 1px solid #e0e7ff;
border-radius: 10px;
padding: 12px 16px;
text-align: center;
}
#ccv-app .ccv-detail-label {
font-size: 0.72rem;
color: #888;
text-transform: uppercase;
letter-spacing: 1px;
margin-bottom: 6px;
}
#ccv-app .ccv-detail-value {
font-size: 1rem;
font-weight: 700;
color: #1a1a2e;
}

/* Generate Section */
#ccv-app .ccv-generate-section {
background: #fff;
border: 2px solid #e0e7ff;
border-radius: 12px;
padding: 20px 24px;
margin-bottom: 20px;
}
#ccv-app .ccv-generate-section h3 {
margin: 0 0 6px;
font-size: 1rem;
color: #333;
}
#ccv-app .ccv-generate-note {
font-size: 0.8rem;
color: #888;
margin-bottom: 14px;
}
#ccv-app .ccv-test-cards {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-top: 12px;
}
#ccv-app .ccv-test-chip {
padding: 6px 14px;
background: #f0f4ff;
border: 1px solid #d0d8ff;
border-radius: 20px;
font-size: 0.85rem;
font-family: 'Courier New', monospace;
cursor: pointer;
transition: all 0.15s;
color: #4a6cf7;
}
#ccv-app .ccv-test-chip:hover { background: #e0e7ff; transform: translateY(-1px); }
#ccv-app .ccv-test-chip-label {
font-size: 0.75rem;
color: #888;
font-family: sans-serif;
margin-right: 4px;
}

/* Luhn Explanation */
#ccv-app .ccv-luhn-section {
background: #fff;
border: 2px solid #e0e7ff;
border-radius: 12px;
padding: 20px 24px;
margin-bottom: 20px;
}
#ccv-app .ccv-luhn-section h3 {
margin: 0 0 12px;
font-size: 1rem;
color: #333;
}
#ccv-app .ccv-luhn-steps {
display: none;
}
#ccv-app .ccv-luhn-steps.show { display: block; }
#ccv-app .ccv-luhn-step {
background: #f8faff;
border-radius: 8px;
padding: 12px 16px;
margin-bottom: 10px;
font-size: 0.88rem;
border-left: 3px solid #4a6cf7;
}
#ccv-app .ccv-luhn-step-title {
font-weight: 700;
color: #4a6cf7;
margin-bottom: 4px;
}
#ccv-app .ccv-digit-row {
display: flex;
flex-wrap: wrap;
gap: 4px;
margin-top: 6px;
}
#ccv-app .ccv-digit-cell {
width: 32px;
height: 32px;
border-radius: 6px;
display: flex;
align-items: center;
justify-content: center;
font-size: 0.8rem;
font-weight: 600;
font-family: 'Courier New', monospace;
}
#ccv-app .ccv-digit-cell.orig    { background: #e0e7ff; color: #4a6cf7; }
#ccv-app .ccv-digit-cell.doubled { background: #fef3c7; color: #92400e; }
#ccv-app .ccv-digit-cell.check   { background: #dcfce7; color: #15803d; }

#ccv-app .ccv-luhn-placeholder {
color: #aaa;
font-size: 0.88rem;
font-style: italic;
}

/* Disclaimer */
#ccv-app .ccv-disclaimer {
background: #fffbeb;
border: 1px solid #fcd34d;
border-radius: 10px;
padding: 14px 18px;
font-size: 0.85rem;
color: #78350f;
margin-bottom: 24px;
}
#ccv-app .ccv-disclaimer strong { color: #92400e; }

/* Related Tools */
#ccv-app .ccv-related {
background: #f8faff;
border-radius: 12px;
padding: 20px 24px;
}
#ccv-app .ccv-related h3 { margin: 0 0 14px; font-size: 1rem; color: #333; }
#ccv-app .ccv-related-links {
display: flex;
flex-wrap: wrap;
gap: 10px;
}
#ccv-app .ccv-related-link {
padding: 8px 16px;
background: #fff;
border: 2px solid #e0e7ff;
border-radius: 8px;
color: #4a6cf7;
text-decoration: none;
font-size: 0.88rem;
font-weight: 600;
transition: all 0.15s;
}
#ccv-app .ccv-related-link:hover {
background: #e0e7ff;
text-decoration: none;
}

@media (max-width: 480px) {
#ccv-app .ccv-card-visual { width: 100%; }
#ccv-app .ccv-input-row { flex-direction: column; align-items: stretch; }
#ccv-app .ccv-btn { width: 100%; }
}
</style>

<div class="ccv-intro">
Enter any credit card number to validate its format using the Luhn algorithm and identify the card network. This tool works entirely in your browser — no data is ever sent to a server.
</div>

<!-- Card Visual -->
<div class="ccv-card-visual" id="ccvCardVisual">
<div class="ccv-card-brand" id="ccvCardBrand">Card Network</div>
<div class="ccv-card-number-display" id="ccvCardDisplay">•••• •••• •••• ••••</div>
<div class="ccv-card-footer">
<span>VALID THRU ••/••</span>
<span id="ccvCardFooterBrand">——</span>
</div>
</div>

<!-- Input Section -->
<div class="ccv-input-section">
<label class="ccv-label" for="ccvInput">Card Number</label>
<div class="ccv-input-row">
<input
type="text"
id="ccvInput"
class="ccv-number-input"
placeholder="4111 1111 1111 1111"
maxlength="23"
inputmode="numeric"
autocomplete="off"
/>
<button class="ccv-btn ccv-btn-primary" onclick="ccvValidate()">Validate</button>
<button class="ccv-btn ccv-btn-secondary" onclick="ccvClear()">Clear</button>
</div>

<div class="ccv-result-badge" id="ccvResultBadge">
<span class="ccv-result-icon" id="ccvResultIcon"></span>
<span id="ccvResultText"></span>
</div>

<div class="ccv-details-grid" id="ccvDetailsGrid" style="display:none;">
<div class="ccv-detail-box">
<div class="ccv-detail-label">Card Network</div>
<div class="ccv-detail-value" id="ccvDetailNetwork">—</div>
</div>
<div class="ccv-detail-box">
<div class="ccv-detail-label">Number Length</div>
<div class="ccv-detail-value" id="ccvDetailLength">—</div>
</div>
<div class="ccv-detail-box">
<div class="ccv-detail-label">Luhn Check</div>
<div class="ccv-detail-value" id="ccvDetailLuhn">—</div>
</div>
<div class="ccv-detail-box">
<div class="ccv-detail-label">IIN / BIN</div>
<div class="ccv-detail-value" id="ccvDetailBin">—</div>
</div>
</div>
</div>

<!-- Generate Test Numbers -->
<div class="ccv-generate-section">
<h3>Generate Test Card Numbers</h3>
<div class="ccv-generate-note">These are mathematically valid numbers used for testing only. They are not linked to real accounts.</div>
<div style="display:flex; flex-wrap:wrap; gap:10px;">
<button class="ccv-btn ccv-btn-secondary" onclick="ccvGenerateAll()">Generate All Types</button>
</div>
<div class="ccv-test-cards" id="ccvTestCards"></div>
</div>

<!-- Luhn Algorithm Explanation -->
<div class="ccv-luhn-section">
<h3>How the Luhn Algorithm Works</h3>
<div class="ccv-luhn-placeholder" id="ccvLuhnPlaceholder">Enter a card number above to see a step-by-step breakdown.</div>
<div class="ccv-luhn-steps" id="ccvLuhnSteps"></div>
</div>

<!-- Disclaimer -->
<div class="ccv-disclaimer">
<strong>Important Notice:</strong> This tool validates number format only. It cannot verify if a card exists, is active, or has available funds. Do not use real card numbers — for testing, use the generated test numbers above.
</div>

<!-- Related Tools -->
<div class="ccv-related">
<h3>Related Tools</h3>
<div class="ccv-related-links">
<a href="/tools/iban-validator/" class="ccv-related-link">IBAN Validator</a>
<a href="/tools/password-generator/" class="ccv-related-link">Password Generator</a>
<a href="/tools/bmi-calculator/" class="ccv-related-link">BMI Calculator</a>
<a href="/tools/compound-interest-calculator/" class="ccv-related-link">Compound Interest Calculator</a>
<a href="/tools/unit-converter/" class="ccv-related-link">Unit Converter</a>
</div>
</div>

<script>
(function() {
// Card network definitions
var NETWORKS = [
{ name: 'Visa',       cssClass: 'visa-card',    pattern: /^4/,                          lengths: [13,16,19] },
{ name: 'Mastercard', cssClass: 'mc-card',      pattern: /^5[1-5]|^2(2[2-9]|[3-6]\d|7[01])/,  lengths: [16] },
{ name: 'Amex',       cssClass: 'amex-card',    pattern: /^3[47]/,                      lengths: [15] },
{ name: 'Discover',   cssClass: 'discover-card',pattern: /^6(?:011|5)/,                 lengths: [16,19] },
{ name: 'JCB',        cssClass: 'jcb-card',     pattern: /^35(?:2[89]|[3-8])/,          lengths: [16,17,18,19] },
{ name: 'Diners',     cssClass: 'diners-card',  pattern: /^3(?:0[0-5]|[68])/,           lengths: [14] },
];

// Test number seeds for each network (valid Luhn numbers)
var TEST_SEEDS = [
{ net: 'Visa',        num: '4111111111111111' },
{ net: 'Visa',        num: '4000056655665556' },
{ net: 'Mastercard',  num: '5555555555554444' },
{ net: 'Mastercard',  num: '5200828282828210' },
{ net: 'Amex',        num: '378282246310005' },
{ net: 'Amex',        num: '371449635398431' },
{ net: 'Discover',    num: '6011111111111117' },
{ net: 'JCB',         num: '3530111333300000' },
{ net: 'Diners',      num: '30569309025904' },
];

function detectNetwork(digits) {
for (var i = 0; i < NETWORKS.length; i++) {
if (NETWORKS[i].pattern.test(digits)) return NETWORKS[i];
}
return null;
}

function luhnCheck(digits) {
var sum = 0;
var alternate = false;
for (var i = digits.length - 1; i >= 0; i--) {
var n = parseInt(digits[i], 10);
if (alternate) {
n *= 2;
if (n > 9) n -= 9;
}
sum += n;
alternate = !alternate;
}
return sum % 10 === 0;
}

function luhnSteps(digits) {
// Returns detailed steps
var origArr = digits.split('').map(Number);
var doubled = [];
var alternate = false;
for (var i = origArr.length - 1; i >= 0; i--) {
var n = origArr[i];
if (alternate) {
n *= 2;
if (n > 9) n -= 9;
}
doubled[i] = n;
alternate = !alternate;
}
var sum = doubled.reduce(function(a, b) { return a + b; }, 0);
return { orig: origArr, doubled: doubled, sum: sum, valid: sum % 10 === 0 };
}

function formatDisplay(digits, net) {
if (!digits) return '•••• •••• •••• ••••';
var len = digits.length;
// Amex: 4-6-5, Diners: 4-6-4, others: 4-4-4-4
if (net && net.name === 'Amex') {
var p1 = digits.slice(0,4).padEnd(4,'•');
var p2 = digits.slice(4,10).padEnd(6,'•');
var p3 = digits.slice(10,15).padEnd(5,'•');
return p1 + ' ' + p2 + ' ' + p3;
}
if (net && net.name === 'Diners') {
var p1 = digits.slice(0,4).padEnd(4,'•');
var p2 = digits.slice(4,10).padEnd(6,'•');
var p3 = digits.slice(10,14).padEnd(4,'•');
return p1 + ' ' + p2 + ' ' + p3;
}
var groups = [];
for (var i = 0; i < 16; i += 4) {
groups.push(digits.slice(i, i+4).padEnd(4,'•'));
}
return groups.join(' ');
}

function updateCard(digits, net) {
var visual = document.getElementById('ccvCardVisual');
var brandEl = document.getElementById('ccvCardBrand');
var dispEl  = document.getElementById('ccvCardDisplay');
var footEl  = document.getElementById('ccvCardFooterBrand');

// Reset classes
visual.className = 'ccv-card-visual';
if (net) visual.classList.add(net.cssClass);

brandEl.textContent = net ? net.name : 'Card Network';
dispEl.textContent  = formatDisplay(digits, net);
footEl.textContent  = net ? net.name.toUpperCase() : '——';
}

// Auto-format input
var inp = document.getElementById('ccvInput');
inp.addEventListener('input', function(e) {
var raw = inp.value.replace(/\D/g,'');
var net = detectNetwork(raw);
// Format with spaces
var formatted;
if (net && net.name === 'Amex') {
formatted = raw.slice(0,4);
if (raw.length > 4) formatted += ' ' + raw.slice(4,10);
if (raw.length > 10) formatted += ' ' + raw.slice(10,15);
} else if (net && net.name === 'Diners') {
formatted = raw.slice(0,4);
if (raw.length > 4) formatted += ' ' + raw.slice(4,10);
if (raw.length > 10) formatted += ' ' + raw.slice(10,14);
} else {
formatted = raw.replace(/(.{4})/g, '$1 ').trim();
}
inp.value = formatted;
updateCard(raw, net);

// Live border feedback if we have enough digits
if (raw.length >= 13) {
var ok = luhnCheck(raw);
inp.className = 'ccv-number-input ' + (ok ? 'valid' : 'invalid');
} else {
inp.className = 'ccv-number-input';
}
});

window.ccvValidate = function() {
var raw = inp.value.replace(/\D/g,'');
var net = detectNetwork(raw);
var badge = document.getElementById('ccvResultBadge');
var icon  = document.getElementById('ccvResultIcon');
var text  = document.getElementById('ccvResultText');
var grid  = document.getElementById('ccvDetailsGrid');

if (raw.length < 8) {
badge.className = 'ccv-result-badge show invalid-badge';
icon.textContent = '✗';
text.textContent = 'Please enter a valid card number (at least 8 digits).';
grid.style.display = 'none';
showLuhnSteps(null);
return;
}

var luhnOk = luhnCheck(raw);
var netOk  = net && net.lengths.indexOf(raw.length) !== -1;

updateCard(raw, net);
inp.className = 'ccv-number-input ' + (luhnOk ? 'valid' : 'invalid');

if (luhnOk) {
badge.className = 'ccv-result-badge show valid-badge';
icon.textContent = '✓';
text.textContent = 'Luhn check passed! This is a structurally valid card number.' + (netOk ? '' : ' (Length is unusual for this network.)');
} else {
badge.className = 'ccv-result-badge show invalid-badge';
icon.textContent = '✗';
text.textContent = 'Luhn check failed. This number is not a valid card number format.';
}

// Details
grid.style.display = 'grid';
document.getElementById('ccvDetailNetwork').textContent = net ? net.name : 'Unknown';
document.getElementById('ccvDetailLength').textContent  = raw.length + ' digits';
document.getElementById('ccvDetailLuhn').textContent    = luhnOk ? 'Pass ✓' : 'Fail ✗';
document.getElementById('ccvDetailBin').textContent     = raw.slice(0,6);

showLuhnSteps(raw);
};

window.ccvClear = function() {
inp.value = '';
inp.className = 'ccv-number-input';
document.getElementById('ccvResultBadge').className = 'ccv-result-badge';
document.getElementById('ccvDetailsGrid').style.display = 'none';
updateCard('', null);
showLuhnSteps(null);
};

function showLuhnSteps(digits) {
var placeholder = document.getElementById('ccvLuhnPlaceholder');
var stepsEl     = document.getElementById('ccvLuhnSteps');

if (!digits) {
placeholder.style.display = '';
stepsEl.className = 'ccv-luhn-steps';
stepsEl.innerHTML = '';
return;
}

placeholder.style.display = 'none';
stepsEl.className = 'ccv-luhn-steps show';

var data = luhnSteps(digits);
var origArr = data.orig;
var doubledArr = data.doubled;

// Which positions are doubled (from right, every other starting at position 1)
var isDoubled = origArr.map(function(_, i) {
return (origArr.length - 1 - i) % 2 === 1;
});

function makeRow(arr, colorFn) {
return '<div class="ccv-digit-row">' + arr.map(function(v, i) {
return '<div class="ccv-digit-cell ' + colorFn(i) + '">' + v + '</div>';
}).join('') + '</div>';
}

var html = '';

// Step 1: Original digits
html += '<div class="ccv-luhn-step">';
html += '<div class="ccv-luhn-step-title">Step 1 — Original digits (right to left, every 2nd is doubled)</div>';
html += makeRow(origArr, function(i) { return isDoubled[i] ? 'doubled' : 'orig'; });
html += '<div style="margin-top:6px;font-size:0.8rem;color:#666;">Blue = keep as-is &nbsp;|&nbsp; Yellow = will be doubled</div>';
html += '</div>';

// Step 2: After doubling
html += '<div class="ccv-luhn-step">';
html += '<div class="ccv-luhn-step-title">Step 2 — After doubling (if result > 9, subtract 9)</div>';
html += makeRow(doubledArr, function(i) { return isDoubled[i] ? 'doubled' : 'orig'; });
html += '</div>';

// Step 3: Sum
html += '<div class="ccv-luhn-step">';
html += '<div class="ccv-luhn-step-title">Step 3 — Sum all digits</div>';
html += '<div style="font-size:0.9rem;margin-top:4px;">';
html += doubledArr.join(' + ') + ' = <strong>' + data.sum + '</strong>';
html += '</div>';
html += '</div>';

// Step 4: Check
html += '<div class="ccv-luhn-step">';
html += '<div class="ccv-luhn-step-title">Step 4 — Check if sum is divisible by 10</div>';
html += '<div style="font-size:0.9rem;margin-top:4px;">';
html += '<strong>' + data.sum + '</strong> mod 10 = <strong>' + (data.sum % 10) + '</strong> → ';
html += data.valid
? '<span style="color:#15803d;font-weight:700;">Valid! (remainder is 0)</span>'
: '<span style="color:#b91c1c;font-weight:700;">Invalid (remainder is not 0)</span>';
html += '</div>';
html += '</div>';

stepsEl.innerHTML = html;
}

window.ccvGenerateAll = function() {
var container = document.getElementById('ccvTestCards');
container.innerHTML = '';
TEST_SEEDS.forEach(function(seed) {
var chip = document.createElement('span');
chip.className = 'ccv-test-chip';
chip.innerHTML = '<span class="ccv-test-chip-label">' + seed.net + ':</span>' + seed.num;
chip.addEventListener('click', function() {
var net = detectNetwork(seed.num);
var formatted;
if (net && net.name === 'Amex') {
formatted = seed.num.slice(0,4) + ' ' + seed.num.slice(4,10) + ' ' + seed.num.slice(10);
} else {
formatted = seed.num.replace(/(.{4})/g, '$1 ').trim();
}
inp.value = formatted;
inp.className = 'ccv-number-input valid';
updateCard(seed.num, net);
ccvValidate();
});
container.appendChild(chip);
});
};
})();
</script>

</div>
