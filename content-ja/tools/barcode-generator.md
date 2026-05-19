---
title: "バーコードジェネレーター"
description: "無料のバーコード作成ツール。Code 128・Code 39・EAN-13対応。色やサイズをカスタマイズしてPNG/SVGでダウンロード。会員登録不要。"
slug: barcode-generator
date: 2025-07-23
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/barcode-generator-ja.png
  alt: "バーコードジェネレーター - Code 128・Code 39・EAN-13に対応した無料バーコード作成ツール"
---

<div id="bg-app">

<style>
#bg-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
max-width: 720px;
margin: 0 auto;
color: #1e293b;
}
#bg-app h2.bg-section-title {
font-size: 1.1rem;
font-weight: 700;
color: #0f172a;
margin: 24px 0 12px;
padding-bottom: 6px;
border-bottom: 2px solid #e2e8f0;
}
#bg-app .bg-card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 20px;
margin-bottom: 18px;
}
#bg-app label.bg-label {
display: block;
font-size: 13px;
font-weight: 600;
color: #475569;
margin-bottom: 5px;
}
#bg-app select.bg-select,
#bg-app input.bg-input {
width: 100%;
padding: 9px 12px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
background: #fff;
color: #1e293b;
box-sizing: border-box;
margin-bottom: 12px;
transition: border-color 0.2s;
}
#bg-app select.bg-select:focus,
#bg-app input.bg-input:focus {
outline: none;
border-color: #3b82f6;
}
#bg-app .bg-row {
display: flex;
gap: 14px;
flex-wrap: wrap;
}
#bg-app .bg-col {
flex: 1;
min-width: 140px;
}
#bg-app input[type="color"].bg-color {
width: 100%;
height: 40px;
padding: 2px 4px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
background: #fff;
cursor: pointer;
margin-bottom: 12px;
box-sizing: border-box;
}
#bg-app input[type="range"].bg-range {
width: 100%;
margin-bottom: 4px;
}
#bg-app .bg-range-val {
font-size: 12px;
color: #64748b;
margin-bottom: 12px;
display: block;
}
#bg-app .bg-samples {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 12px;
}
#bg-app button.bg-sample-btn {
padding: 5px 12px;
font-size: 12px;
border: 1.5px solid #3b82f6;
border-radius: 6px;
background: #eff6ff;
color: #1d4ed8;
cursor: pointer;
font-weight: 600;
transition: background 0.15s;
}
#bg-app button.bg-sample-btn:hover {
background: #dbeafe;
}
#bg-app button.bg-generate-btn {
width: 100%;
padding: 12px;
background: #2563eb;
color: #fff;
border: none;
border-radius: 8px;
font-size: 15px;
font-weight: 700;
cursor: pointer;
transition: background 0.2s;
margin-top: 4px;
}
#bg-app button.bg-generate-btn:hover {
background: #1d4ed8;
}
#bg-app .bg-error {
background: #fef2f2;
border: 1.5px solid #fca5a5;
border-radius: 8px;
color: #b91c1c;
font-size: 13px;
padding: 10px 14px;
margin-top: 10px;
display: none;
}
#bg-app .bg-result {
display: none;
margin-top: 18px;
}
#bg-app .bg-canvas-wrap {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 20px;
text-align: center;
margin-bottom: 14px;
}
#bg-app canvas#bg-canvas {
display: block;
margin: 0 auto;
max-width: 100%;
}
#bg-app button.bg-dl-btn {
display: inline-block;
padding: 10px 26px;
background: #0f172a;
color: #fff;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
text-decoration: none;
transition: background 0.2s;
}
#bg-app button.bg-dl-btn:hover {
background: #1e293b;
}
#bg-app .bg-info-box {
background: #f0fdf4;
border: 1px solid #bbf7d0;
border-radius: 8px;
padding: 14px 16px;
font-size: 13px;
color: #166534;
margin-top: 14px;
line-height: 1.6;
}
#bg-app .bg-crosslinks {
margin-top: 24px;
font-size: 14px;
color: #475569;
}
#bg-app .bg-crosslinks a {
color: #2563eb;
text-decoration: none;
}
#bg-app .bg-crosslinks a:hover {
text-decoration: underline;
}
</style>

<h2 class="bg-section-title">バーコード設定</h2>

<div class="bg-card">
<label class="bg-label" for="bg-type">バーコードの種類</label>
<select id="bg-type" class="bg-select">
<option value="code128">Code 128（汎用性が高い）</option>
<option value="code39">Code 39</option>
<option value="ean13">EAN-13</option>
</select>

<label class="bg-label" for="bg-data">データ / 値</label>
<div class="bg-samples" id="bg-samples"></div>
<input id="bg-data" class="bg-input" type="text" placeholder="バーコードのデータを入力..." />

<div class="bg-row">
<div class="bg-col">
<label class="bg-label" for="bg-bar-color">バーの色</label>
<input id="bg-bar-color" class="bg-color" type="color" value="#000000" />
</div>
<div class="bg-col">
<label class="bg-label" for="bg-bg-color">背景色</label>
<input id="bg-bg-color" class="bg-color" type="color" value="#ffffff" />
</div>
</div>

<div class="bg-row">
<div class="bg-col">
<label class="bg-label">バー幅: <span id="bg-bw-val">2</span>px</label>
<input id="bg-bar-width" class="bg-range" type="range" min="1" max="4" value="2" step="1" />
</div>
<div class="bg-col">
<label class="bg-label">高さ: <span id="bg-bh-val">80</span>px</label>
<input id="bg-bar-height" class="bg-range" type="range" min="50" max="200" value="80" step="5" />
</div>
</div>

<button class="bg-generate-btn" id="bg-generate-btn">バーコードを生成する</button>
<div class="bg-error" id="bg-error"></div>
</div>

<div class="bg-result" id="bg-result">
<div class="bg-canvas-wrap">
<canvas id="bg-canvas"></canvas>
</div>
<div style="text-align:center;">
<button class="bg-dl-btn" id="bg-dl-btn">PNGでダウンロード</button>
</div>
<div class="bg-info-box" id="bg-info-box"></div>
</div>

<div class="bg-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">在庫管理・販売管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、商品の在庫管理・売上管理もクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div class="bg-crosslinks">
<p>QRコード作成 &rarr; <a href="/ja/tools/qr-code-generator/">QRコードジェネレーター</a></p>
<p>請求書作成 &rarr; <a href="/ja/tools/invoice-generator/">請求書ジェネレーター</a></p>
</div>

<script>
(function () {
"use strict";

// ── Code 128 encoding tables ──────────────────────────────────────────────
var C128_PATTERNS = [
"11011001100","11001101100","11001100110","10010011000","10010001100",
"10001001100","10011001000","10011000100","10001100100","11001001000",
"11001000100","11000100100","10110011100","10011011100","10011001110",
"10111001100","10011101100","10011100110","11001110010","11001011100",
"11001001110","11011100100","11001110100","11101101110","11101001100",
"11100101100","11100100110","11101100100","11100110100","11100110010",
"11011011000","11011000110","11000110110","10100011000","10001011000",
"10001000110","10110001000","10001101000","10001100010","11010001000",
"11000101000","11000100010","10110111000","10110001110","10001101110",
"10111011000","10111000110","10001110110","11101110110","11010001110",
"11000101110","11011101000","11011100010","11011101110","11101011000",
"11101000110","11100010110","11101101000","11101100010","11100011010",
"11101111010","11001000010","11110001010","10100110000","10100001100",
"10010110000","10010000110","10000101100","10000100110","10110010000",
"10110000100","10011010000","10011000010","10000110100","10000110010",
"11000010010","11001010000","11110111010","11000010100","10001111010",
"10100111100","10010111100","10010011110","10111100100","10011110100",
"10011110010","11110100100","11110010100","11110010010","11011011110",
"11011110110","11110110110","10101111000","10100011110","10001011110",
"10111101000","10111100010","11110101000","11110100010","10111011110",
"10111101110","11101011110","11110101110","11010000100","11010010000",
"11010011100","11000111010"
];
var C128_START_B = "11010010000";
var C128_STOP    = "11000111010";

function encodeCode128(data) {
var bars = C128_START_B;
var checksum = 104;
for (var i = 0; i < data.length; i++) {
var code = data.charCodeAt(i) - 32;
if (code < 0 || code > 95) throw new Error("Code 128（セットB）はASCII 32〜127の文字に対応しています。無効な文字: '" + data[i] + "'");
checksum += (i + 1) * code;
bars += C128_PATTERNS[code];
}
bars += C128_PATTERNS[checksum % 103];
bars += C128_STOP + "11";
return bars;
}

// ── Code 39 encoding ─────────────────────────────────────────────────────
var C39_CHARS = {
"0":"000110100","1":"100100001","2":"001100001","3":"101100000",
"4":"000110001","5":"100110000","6":"001110000","7":"000100101",
"8":"100100100","9":"001100100","A":"100001001","B":"001001001",
"C":"101001000","D":"000011001","E":"100011000","F":"001011000",
"G":"000001101","H":"100001100","I":"001001100","J":"000011100",
"K":"100000011","L":"001000011","M":"101000010","N":"000010011",
"O":"100010010","P":"001010010","Q":"000000111","R":"100000110",
"S":"001000110","T":"000010110","U":"110000001","V":"011000001",
"W":"111000000","X":"010010001","Y":"110010000","Z":"011010000",
"-":"010000101",".":" 110000100"," ":"011000100","$":"010101000",
"/":"010100010","+":"010001010","%":"000101010","*":"010010100"
};

function encodeCode39(data) {
var str = data.toUpperCase();
var chars = "*" + str + "*";
for (var i = 1; i < chars.length - 1; i++) {
if (!C39_CHARS[chars[i]]) throw new Error("Code 39 はA-Z、0-9、および - . $ / + % スペースに対応しています。無効な文字: '" + chars[i] + "'");
}
return chars;
}

// ── EAN-13 encoding ───────────────────────────────────────────────────────
var EAN_L = ["0001101","0011001","0010011","0111101","0100011","0110001","0101111","0111011","0110111","0001011"];
var EAN_R = ["1110010","1100110","1101100","1000010","1011100","1001110","1010000","1000100","1001000","1110100"];
var EAN_G = ["0100111","0110011","0011011","0100001","0011101","0111001","0000101","0010001","0001001","0010111"];
var EAN_PARITY = ["LLLLLL","LLGLGG","LLGGLG","LLGGGL","LGLLGG","LGGLLG","LGGGLL","LGLGLG","LGLGGL","LGGLGL"];

function ean13CheckDigit(d12) {
var s = 0;
for (var i = 0; i < 12; i++) s += parseInt(d12[i]) * (i % 2 === 0 ? 1 : 3);
return ((10 - (s % 10)) % 10).toString();
}

function encodeEAN13(data) {
var d = data.replace(/\D/g, "");
if (d.length === 12) d = d + ean13CheckDigit(d);
if (d.length !== 13) throw new Error("EAN-13には12桁または13桁の数字が必要です。");
var calc = ean13CheckDigit(d.substring(0, 12));
if (d[12] !== calc) throw new Error("EAN-13チェックデジットが一致しません。期待値: " + calc + "、入力値: " + d[12] + "。");
return d;
}

// ── Rendering ─────────────────────────────────────────────────────────────
function renderCode128(canvas, bits, barColor, bgColor, barW, barH) {
var quietW = barW * 10;
var totalW = bits.length * barW + quietW * 2;
var textH = 18;
canvas.width = totalW;
canvas.height = barH + textH;
var ctx = canvas.getContext("2d");
ctx.fillStyle = bgColor;
ctx.fillRect(0, 0, totalW, canvas.height);
ctx.fillStyle = barColor;
for (var i = 0; i < bits.length; i++) {
if (bits[i] === "1") ctx.fillRect(quietW + i * barW, 0, barW, barH);
}
ctx.fillStyle = barColor;
ctx.font = "12px monospace";
ctx.textAlign = "center";
ctx.fillText(canvas._data || "", totalW / 2, barH + 14);
}

function renderCode39(canvas, chars, barColor, bgColor, barW, barH) {
var quietW = barW * 10;
var totalBits = 0;
for (var i = 0; i < chars.length; i++) {
var pat = C39_CHARS[chars[i]] || C39_CHARS["*"];
for (var j = 0; j < pat.length; j++) totalBits += (pat[j] === "1" ? 3 : 1);
if (i < chars.length - 1) totalBits += 1;
}
var textH = 18;
canvas.width = quietW * 2 + totalBits * barW;
canvas.height = barH + textH;
var ctx = canvas.getContext("2d");
ctx.fillStyle = bgColor;
ctx.fillRect(0, 0, canvas.width, canvas.height);
var x = quietW;
for (var i = 0; i < chars.length; i++) {
var pat = C39_CHARS[chars[i]] || C39_CHARS["*"];
for (var j = 0; j < pat.length; j++) {
var w = (pat[j] === "1" ? 3 : 1) * barW;
if (j % 2 === 0) { ctx.fillStyle = barColor; ctx.fillRect(x, 0, w, barH); }
x += w;
}
if (i < chars.length - 1) x += barW;
}
ctx.fillStyle = barColor;
ctx.font = "12px monospace";
ctx.textAlign = "center";
ctx.fillText(canvas._data || "", canvas.width / 2, barH + 14);
}

function renderEAN13(canvas, digits, barColor, bgColor, barW, barH) {
var first = parseInt(digits[0]);
var parity = EAN_PARITY[first];
var quietW = barW * 9;
var guardW = 3 * barW;
var midW   = 5 * barW;
var dataW  = 42 * barW;
var totalW = quietW * 2 + guardW * 2 + midW + dataW * 2;
var textH  = 18;
canvas.width  = totalW;
canvas.height = barH + textH;
var ctx = canvas.getContext("2d");
ctx.fillStyle = bgColor;
ctx.fillRect(0, 0, totalW, canvas.height);
ctx.fillStyle = barColor;

function drawBits(bits, startX, height) {
for (var i = 0; i < bits.length; i++) {
if (bits[i] === "1") ctx.fillRect(startX + i * barW, 0, barW, height);
}
}

var x = quietW;
drawBits("101", x, barH + 5); x += guardW;
for (var i = 1; i <= 6; i++) {
var d = parseInt(digits[i]);
var enc = (parity[i - 1] === "L") ? EAN_L[d] : EAN_G[d];
drawBits(enc, x, barH); x += 7 * barW;
}
drawBits("01010", x, barH + 5); x += midW;
for (var i = 7; i <= 12; i++) {
drawBits(EAN_R[parseInt(digits[i])], x, barH); x += 7 * barW;
}
drawBits("101", x, barH + 5);

ctx.fillStyle = barColor;
ctx.font = "11px monospace";
ctx.textAlign = "left";
ctx.fillText(digits[0], 2, barH + 14);
ctx.textAlign = "center";
ctx.fillText(digits.substring(1, 7), quietW + guardW + dataW / 2, barH + 14);
ctx.fillText(digits.substring(7, 13), quietW + guardW + dataW + midW + dataW / 2, barH + 14);
}

// ── Sample data ───────────────────────────────────────────────────────────
var SAMPLES = {
code128: ["Hello World", "12345678", "ABC-123", "PRODUCT-001"],
code39:  ["HELLO", "12345", "CODE39", "ITEM-001"],
ean13:   ["4901234567890", "9780201379624", "4007817326992"]
};

var typeEl    = document.getElementById("bg-type");
var dataEl    = document.getElementById("bg-data");
var samplesEl = document.getElementById("bg-samples");
var barColorEl= document.getElementById("bg-bar-color");
var bgColorEl = document.getElementById("bg-bg-color");
var barWEl    = document.getElementById("bg-bar-width");
var barHEl    = document.getElementById("bg-bar-height");
var bwVal     = document.getElementById("bg-bw-val");
var bhVal     = document.getElementById("bg-bh-val");
var genBtn    = document.getElementById("bg-generate-btn");
var errorEl   = document.getElementById("bg-error");
var resultEl  = document.getElementById("bg-result");
var canvas    = document.getElementById("bg-canvas");
var dlBtn     = document.getElementById("bg-dl-btn");
var infoBox   = document.getElementById("bg-info-box");

function updateSamples() {
var type = typeEl.value;
samplesEl.innerHTML = "";
SAMPLES[type].forEach(function (s) {
var btn = document.createElement("button");
btn.className = "bg-sample-btn";
btn.textContent = s;
btn.addEventListener("click", function () { dataEl.value = s; });
samplesEl.appendChild(btn);
});
var ph = {
code128: "ASCII文字（32〜127）を入力",
code39:  "A-Z 0-9 - . $ / + % スペース",
ean13:   "12桁または13桁の数字"
};
dataEl.placeholder = ph[type] || "データを入力...";
}

typeEl.addEventListener("change", updateSamples);
updateSamples();

barWEl.addEventListener("input", function () { bwVal.textContent = barWEl.value; });
barHEl.addEventListener("input", function () { bhVal.textContent = barHEl.value; });

function showError(msg) {
errorEl.textContent = msg;
errorEl.style.display = "block";
resultEl.style.display = "none";
}
function clearError() {
errorEl.style.display = "none";
}

genBtn.addEventListener("click", function () {
clearError();
var data = dataEl.value.trim();
if (!data) { showError("バーコードのデータを入力してください。"); return; }
var type     = typeEl.value;
var barColor = barColorEl.value;
var bgColor  = bgColorEl.value;
var barW     = parseInt(barWEl.value);
var barH     = parseInt(barHEl.value);

try {
canvas._data = data;
if (type === "code128") {
var bits = encodeCode128(data);
renderCode128(canvas, bits, barColor, bgColor, barW, barH);
infoBox.innerHTML = "<strong>Code 128B</strong> &mdash; " + data.length + "文字をエンコードしました。チェックサム検証済み。";
} else if (type === "code39") {
var chars = encodeCode39(data);
renderCode39(canvas, chars, barColor, bgColor, barW, barH);
infoBox.innerHTML = "<strong>Code 39</strong> &mdash; スタート/ストップ間に" + (chars.length - 2) + "文字をエンコードしました。";
} else if (type === "ean13") {
var digits = encodeEAN13(data);
canvas._data = digits;
renderEAN13(canvas, digits, barColor, bgColor, barW, barH);
infoBox.innerHTML = "<strong>EAN-13</strong> &mdash; チェックデジット: <strong>" + digits[12] + "</strong>。国コード（先頭3桁）: <strong>" + digits.substring(0, 3) + "</strong>。";
}
resultEl.style.display = "block";
} catch (e) {
showError(e.message);
}
});

dlBtn.addEventListener("click", function () {
var link = document.createElement("a");
link.download = "barcode-" + typeEl.value + ".png";
link.href = canvas.toDataURL("image/png");
link.click();
});
})();
</script>

</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

## 関連ツール

> QRコード生成 → [QRコード生成ツール](/ja/tools/qr-code-generator/)

