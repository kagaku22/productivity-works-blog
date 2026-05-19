---
title: "Number to Words Converter | Convert Numbers to English Words Free"
date: 2025-05-16
draft: false
slug: "number-to-words"
aliases: ["/tools/number-base-converter/", "/tools/number-to-words/"]
description: "Free number to words converter. Instantly convert numbers into English words, currency amounts, or ordinal forms. Supports numbers up to trillions. No sign-up needed."
categories: ["Free Tools"]
tags: ["number to words", "number converter", "spell numbers", "currency words", "ordinal numbers"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/number-to-words.png"
  alt: "Number to Words Converter"
  relative: false
---

*Disclosure: This page may contain affiliate links. If you make a purchase through these links, we may earn a commission at no extra cost to you. We only recommend tools and services we genuinely find useful.*

# Number to Words Converter

Need to write a check, draft a legal document, or just double-check how to spell a large number in English? This free tool converts any number — up to the trillions — into plain English words instantly. Switch to Currency mode to spell out dollar amounts with cents, or Ordinal mode to get "first," "second," "twenty-third," and so on.

<style>
#n2w-app * { box-sizing: border-box; }
#n2w-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 680px;
margin: 2rem auto;
color: #1e1b4b;
}
#n2w-app h2 {
font-size: 1.1rem;
font-weight: 700;
margin: 0 0 1rem;
color: #1e1b4b;
}
#n2w-app .n2w-modes {
display: flex;
gap: 6px;
margin-bottom: 1.25rem;
flex-wrap: wrap;
}
#n2w-app .n2w-mode-btn {
padding: 7px 16px;
border: 2px solid #4f46e5;
border-radius: 999px;
background: #fff;
color: #4f46e5;
font-size: 0.85rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
}
#n2w-app .n2w-mode-btn.active {
background: #4f46e5;
color: #fff;
}
#n2w-app .n2w-mode-btn:hover:not(.active) {
background: #ede9fe;
}
#n2w-app .n2w-input-row {
display: flex;
gap: 10px;
align-items: center;
margin-bottom: 1.25rem;
}
#n2w-app .n2w-prefix {
font-size: 1.4rem;
font-weight: 700;
color: #4f46e5;
min-width: 20px;
text-align: right;
}
#n2w-app .n2w-input {
flex: 1;
padding: 12px 16px;
border: 2px solid #c7d2fe;
border-radius: 10px;
font-size: 1.3rem;
font-weight: 600;
color: #1e1b4b;
outline: none;
transition: border-color 0.15s;
-moz-appearance: textfield;
}
#n2w-app .n2w-input:focus {
border-color: #4f46e5;
}
#n2w-app .n2w-input::-webkit-inner-spin-button,
#n2w-app .n2w-input::-webkit-outer-spin-button {
-webkit-appearance: none;
}
#n2w-app .n2w-result-box {
background: #f5f3ff;
border: 2px solid #c7d2fe;
border-radius: 12px;
padding: 1.25rem 1.5rem;
min-height: 70px;
display: flex;
align-items: center;
justify-content: space-between;
gap: 12px;
margin-bottom: 1rem;
}
#n2w-app .n2w-result-text {
font-size: 1.05rem;
font-weight: 600;
color: #3730a3;
line-height: 1.5;
flex: 1;
word-break: break-word;
}
#n2w-app .n2w-result-text.placeholder {
color: #a5b4fc;
font-weight: 400;
font-style: italic;
}
#n2w-app .n2w-copy-btn {
flex-shrink: 0;
padding: 8px 16px;
background: #4f46e5;
color: #fff;
border: none;
border-radius: 8px;
font-size: 0.85rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
#n2w-app .n2w-copy-btn:hover {
background: #4338ca;
}
#n2w-app .n2w-copy-btn:active {
transform: scale(0.96);
}
#n2w-app .n2w-copy-btn.copied {
background: #059669;
}
#n2w-app .n2w-hint {
font-size: 0.78rem;
color: #6b7280;
margin-bottom: 0.5rem;
}
#n2w-app .n2w-error {
color: #dc2626;
font-size: 0.85rem;
margin-top: -0.75rem;
margin-bottom: 0.75rem;
min-height: 1.2em;
}
#n2w-app .n2w-examples {
display: flex;
flex-wrap: wrap;
gap: 6px;
margin-top: 1rem;
}
#n2w-app .n2w-example-chip {
padding: 4px 12px;
background: #ede9fe;
color: #4f46e5;
border-radius: 999px;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
border: none;
transition: background 0.15s;
}
#n2w-app .n2w-example-chip:hover {
background: #c7d2fe;
}
</style>

<div id="n2w-app">
<h2>Number to Words Converter</h2>

<div class="n2w-modes">
<button class="n2w-mode-btn active" data-mode="standard" onclick="n2wSetMode('standard')">Standard</button>
<button class="n2w-mode-btn" data-mode="currency" onclick="n2wSetMode('currency')">Currency ($)</button>
<button class="n2w-mode-btn" data-mode="ordinal" onclick="n2wSetMode('ordinal')">Ordinal</button>
</div>

<div class="n2w-input-row">
<span class="n2w-prefix" id="n2w-prefix"></span>
<input
class="n2w-input"
id="n2w-input"
type="number"
inputmode="decimal"
placeholder="Enter a number…"
oninput="n2wConvert()"
/>
</div>

<div class="n2w-error" id="n2w-error"></div>

<div class="n2w-result-box">
<span class="n2w-result-text placeholder" id="n2w-result">Your result will appear here</span>
<button class="n2w-copy-btn" id="n2w-copy-btn" onclick="n2wCopy()" style="display:none">Copy</button>
</div>

<div class="n2w-hint" id="n2w-hint">Supports integers up to 999 trillion. Currency mode supports two decimal places.</div>

<div class="n2w-examples">
<span style="font-size:0.78rem;color:#6b7280;align-self:center;">Try:</span>
<button class="n2w-example-chip" onclick="n2wSetExample('42')">42</button>
<button class="n2w-example-chip" onclick="n2wSetExample('1234')">1,234</button>
<button class="n2w-example-chip" onclick="n2wSetExample('1000000')">1,000,000</button>
<button class="n2w-example-chip" onclick="n2wSetExample('1234567890')">1,234,567,890</button>
<button class="n2w-example-chip" onclick="n2wSetExample('999999999999999')">999 trillion</button>
</div>
</div>

<script>
(function() {
var _mode = 'standard';

var ones = ['', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine',
'ten', 'eleven', 'twelve', 'thirteen', 'fourteen', 'fifteen', 'sixteen',
'seventeen', 'eighteen', 'nineteen'];
var tens = ['', '', 'twenty', 'thirty', 'forty', 'fifty', 'sixty', 'seventy', 'eighty', 'ninety'];

var ordinalMap = {
'one': 'first', 'two': 'second', 'three': 'third', 'four': 'fourth',
'five': 'fifth', 'six': 'sixth', 'seven': 'seventh', 'eight': 'eighth',
'nine': 'ninth', 'ten': 'tenth', 'eleven': 'eleventh', 'twelve': 'twelfth',
'thirteen': 'thirteenth', 'fourteen': 'fourteenth', 'fifteen': 'fifteenth',
'sixteen': 'sixteenth', 'seventeen': 'seventeenth', 'eighteen': 'eighteenth',
'nineteen': 'nineteenth', 'twenty': 'twentieth', 'thirty': 'thirtieth',
'forty': 'fortieth', 'fifty': 'fiftieth', 'sixty': 'sixtieth',
'seventy': 'seventieth', 'eighty': 'eightieth', 'ninety': 'ninetieth',
'hundred': 'hundredth', 'thousand': 'thousandth', 'million': 'millionth',
'billion': 'billionth', 'trillion': 'trillionth', 'zero': 'zeroth'
};

function belowThousand(n) {
if (n === 0) return '';
if (n < 20) return ones[n];
if (n < 100) {
var t = tens[Math.floor(n / 10)];
var o = ones[n % 10];
return o ? t + '-' + o : t;
}
var h = Math.floor(n / 100);
var rem = n % 100;
var base = ones[h] + ' hundred';
if (rem === 0) return base;
return base + ' ' + belowThousand(rem);
}

function toWords(n) {
if (n === 0) return 'zero';
var neg = n < 0;
var abs = Math.abs(n);
if (abs > 999999999999999) return null;

var parts = [];
var scales = [
[1000000000000, 'trillion'],
[1000000000, 'billion'],
[1000000, 'million'],
[1000, 'thousand']
];

for (var i = 0; i < scales.length; i++) {
var val = scales[i][0];
var name = scales[i][1];
if (abs >= val) {
var chunk = Math.floor(abs / val);
abs = abs % val;
parts.push(belowThousand(chunk) + ' ' + name);
}
}
if (abs > 0) parts.push(belowThousand(abs));

var words = parts.join(' ');
return neg ? 'negative ' + words : words;
}

function toOrdinal(words) {
if (!words) return words;
var parts = words.split(' ');
var last = parts[parts.length - 1];
// handle hyphenated (e.g. "thirty-four" -> "thirty-fourth")
if (last.indexOf('-') !== -1) {
var hypParts = last.split('-');
var lastSub = hypParts[hypParts.length - 1];
if (ordinalMap[lastSub]) {
hypParts[hypParts.length - 1] = ordinalMap[lastSub];
parts[parts.length - 1] = hypParts.join('-');
return parts.join(' ');
}
}
if (ordinalMap[last]) {
parts[parts.length - 1] = ordinalMap[last];
} else {
parts[parts.length - 1] = last + 'th';
}
return parts.join(' ');
}

function centsToWords(cents) {
if (cents === 0) return 'zero cents';
var w = toWords(cents);
return w + (cents === 1 ? ' cent' : ' cents');
}

window.n2wSetMode = function(mode) {
_mode = mode;
document.querySelectorAll('#n2w-app .n2w-mode-btn').forEach(function(b) {
b.classList.toggle('active', b.dataset.mode === mode);
});
var prefix = document.getElementById('n2w-prefix');
prefix.textContent = mode === 'currency' ? '$' : '';
var hint = document.getElementById('n2w-hint');
if (mode === 'currency') {
hint.textContent = 'Supports amounts up to $999,999,999,999,999.99.';
} else if (mode === 'ordinal') {
hint.textContent = 'Converts whole numbers to ordinal words (first, second, third…).';
} else {
hint.textContent = 'Supports integers up to 999 trillion. Currency mode supports two decimal places.';
}
n2wConvert();
};

window.n2wSetExample = function(val) {
document.getElementById('n2w-input').value = val;
n2wConvert();
};

window.n2wConvert = function() {
var raw = document.getElementById('n2w-input').value.trim();
var resultEl = document.getElementById('n2w-result');
var errorEl = document.getElementById('n2w-error');
var copyBtn = document.getElementById('n2w-copy-btn');

errorEl.textContent = '';

if (raw === '' || raw === '-') {
resultEl.textContent = 'Your result will appear here';
resultEl.classList.add('placeholder');
copyBtn.style.display = 'none';
return;
}

var result = '';

if (_mode === 'currency') {
var parsed = parseFloat(raw);
if (isNaN(parsed)) {
errorEl.textContent = 'Please enter a valid number.';
resultEl.textContent = 'Your result will appear here';
resultEl.classList.add('placeholder');
copyBtn.style.display = 'none';
return;
}
var negative = parsed < 0;
var abs = Math.abs(parsed);
if (abs > 999999999999999.99) {
errorEl.textContent = 'Number too large. Maximum is 999,999,999,999,999.99.';
resultEl.textContent = 'Your result will appear here';
resultEl.classList.add('placeholder');
copyBtn.style.display = 'none';
return;
}
var dollars = Math.floor(abs);
var cents = Math.round((abs - dollars) * 100);
var dollarsWords = dollars === 0 ? 'zero' : toWords(dollars);
var dollarLabel = dollars === 1 ? 'dollar' : 'dollars';
if (cents === 0) {
result = dollarsWords + ' ' + dollarLabel + ' and no cents';
} else {
var centsWords = toWords(cents);
var centLabel = cents === 1 ? 'cent' : 'cents';
result = dollarsWords + ' ' + dollarLabel + ' and ' + centsWords + ' ' + centLabel;
}
if (negative) result = 'negative ' + result;
} else {
if (raw.indexOf('.') !== -1) {
errorEl.textContent = 'Standard and Ordinal modes require whole numbers. Use Currency mode for decimals.';
resultEl.textContent = 'Your result will appear here';
resultEl.classList.add('placeholder');
copyBtn.style.display = 'none';
return;
}
var num = parseInt(raw, 10);
if (isNaN(num)) {
errorEl.textContent = 'Please enter a valid number.';
resultEl.textContent = 'Your result will appear here';
resultEl.classList.add('placeholder');
copyBtn.style.display = 'none';
return;
}
if (Math.abs(num) > 999999999999999) {
errorEl.textContent = 'Number too large. Maximum is 999,999,999,999,999.';
resultEl.textContent = 'Your result will appear here';
resultEl.classList.add('placeholder');
copyBtn.style.display = 'none';
return;
}
result = toWords(num);
if (_mode === 'ordinal') {
result = toOrdinal(result);
}
}

resultEl.textContent = result;
resultEl.classList.remove('placeholder');
copyBtn.style.display = 'inline-block';
copyBtn.textContent = 'Copy';
copyBtn.classList.remove('copied');
};

window.n2wCopy = function() {
var text = document.getElementById('n2w-result').textContent;
var btn = document.getElementById('n2w-copy-btn');
if (!text || text === 'Your result will appear here') return;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(text).then(function() {
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 2000);
});
} else {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
try { document.execCommand('copy'); } catch(e) {}
document.body.removeChild(ta);
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function() {
btn.textContent = 'Copy';
btn.classList.remove('copied');
}, 2000);
}
};
})();
</script>

## How to Use

1. **Choose a mode** — Standard, Currency ($), or Ordinal
2. **Type your number** in the input field
3. **Read the result** instantly below
4. **Click Copy** to copy the words to your clipboard

## Mode Guide

| Mode | Input | Output |
|------|-------|--------|
| Standard | 1,234,567 | one million two hundred thirty-four thousand five hundred sixty-seven |
| Currency | 1234.56 | one thousand two hundred thirty-four dollars and fifty-six cents |
| Ordinal | 21 | twenty-first |

## Common Use Cases

- **Writing checks**: Banks often require the dollar amount spelled out in words
- **Legal documents**: Contracts frequently spell out key figures to prevent alteration
- **Academic writing**: Some style guides require numbers under a certain threshold to be written out
- **Learning English**: See exactly how large numbers are spoken aloud
- **Proofreading**: Verify you're spelling a number correctly in formal correspondence

## Numbers Up to Trillion

This converter handles numbers from negative 999 trillion to positive 999 trillion — more than enough for any real-world use case including national budgets, astronomical distances, and financial reports.

---

Related: Calculate percentages with our [Percentage Calculator](/tools/percentage-calculator/)
