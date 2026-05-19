---
title: "2進数・16進数・10進数変換ツール - 無料オンライン進数変換"
date: 2025-12-07
description: "2進数・10進数・16進数・8進数を瞬時に相互変換。テキスト↔バイナリ変換、2の補数表示、ビット操作表示など全機能無料。インストール不要。"
categories: ["無料ツール"]
tags: ["2進数変換", "16進数変換", "10進数変換", "進数変換", "バイナリ変換", "2の補数", "ビット操作"]
slug: "binary-converter"
aliases: ["/ja/tools/rgb-hex-converter/", "/ja/tools/number-base-converter/"]
cover:
  image: "/images/covers/binary-converter-ja.png"
  alt: "2進数変換ツール"
ShowToc: false
---

<div id="bin-app">

<style>
#bin-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
background: #0f172a;
color: #e2e8f0;
border-radius: 12px;
padding: 24px;
max-width: 860px;
margin: 0 auto;
box-sizing: border-box;
}
#bin-app * { box-sizing: border-box; }

#bin-app h2 {
color: #06b6d4;
font-size: 1.1rem;
margin: 0 0 16px;
font-weight: 600;
letter-spacing: 0.03em;
text-transform: uppercase;
}

#bin-app .mode-tabs {
display: flex;
gap: 8px;
margin-bottom: 20px;
flex-wrap: wrap;
}
#bin-app .mode-tab {
padding: 8px 18px;
border-radius: 8px;
border: 1.5px solid #334155;
background: #1e293b;
color: #94a3b8;
cursor: pointer;
font-size: 0.9rem;
font-weight: 500;
transition: all 0.15s;
}
#bin-app .mode-tab.active,
#bin-app .mode-tab:hover {
border-color: #06b6d4;
background: #0e4a58;
color: #06b6d4;
}

#bin-app .input-row {
display: flex;
gap: 10px;
margin-bottom: 18px;
align-items: stretch;
flex-wrap: wrap;
}
#bin-app .input-row select {
background: #1e293b;
border: 1.5px solid #334155;
color: #e2e8f0;
border-radius: 8px;
padding: 10px 12px;
font-size: 0.9rem;
cursor: pointer;
min-width: 160px;
}
#bin-app .input-row select:focus { outline: none; border-color: #06b6d4; }
#bin-app #main-input {
flex: 1;
background: #1e293b;
border: 1.5px solid #334155;
color: #e2e8f0;
border-radius: 8px;
padding: 10px 14px;
font-size: 1rem;
font-family: 'Courier New', monospace;
min-width: 0;
transition: border-color 0.15s;
}
#bin-app #main-input:focus { outline: none; border-color: #06b6d4; }
#bin-app #main-input.error { border-color: #ef4444; }

#bin-app .error-msg {
color: #ef4444;
font-size: 0.82rem;
margin-top: -12px;
margin-bottom: 14px;
min-height: 16px;
}

#bin-app .outputs-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
margin-bottom: 20px;
}
@media (max-width: 560px) {
#bin-app .outputs-grid { grid-template-columns: 1fr; }
}

#bin-app .output-card {
background: #1e293b;
border: 1.5px solid #334155;
border-radius: 10px;
padding: 14px;
}
#bin-app .output-card .label {
font-size: 0.75rem;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.08em;
margin-bottom: 6px;
font-weight: 600;
}
#bin-app .output-card .value {
font-family: 'Courier New', monospace;
font-size: 0.95rem;
color: #06b6d4;
word-break: break-all;
min-height: 22px;
margin-bottom: 10px;
line-height: 1.5;
}
#bin-app .output-card .copy-btn {
background: #0e4a58;
border: 1px solid #06b6d4;
color: #06b6d4;
border-radius: 6px;
padding: 5px 12px;
font-size: 0.78rem;
cursor: pointer;
transition: all 0.15s;
}
#bin-app .output-card .copy-btn:hover { background: #06b6d4; color: #0f172a; }
#bin-app .output-card .copy-btn.copied { background: #06b6d4; color: #0f172a; }

#bin-app .bit-section {
background: #1e293b;
border: 1.5px solid #334155;
border-radius: 10px;
padding: 16px;
margin-bottom: 20px;
}
#bin-app .bit-toggle-row {
display: flex;
gap: 8px;
margin-bottom: 14px;
flex-wrap: wrap;
}
#bin-app .bit-toggle {
padding: 5px 14px;
border-radius: 6px;
border: 1px solid #334155;
background: #0f172a;
color: #94a3b8;
cursor: pointer;
font-size: 0.82rem;
font-weight: 500;
transition: all 0.15s;
}
#bin-app .bit-toggle.active,
#bin-app .bit-toggle:hover {
border-color: #06b6d4;
color: #06b6d4;
background: #0e4a58;
}

#bin-app .bit-grid {
display: flex;
flex-wrap: wrap;
gap: 4px;
}
#bin-app .bit-cell {
width: 32px;
height: 32px;
border-radius: 5px;
border: 1px solid #334155;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
font-family: 'Courier New', monospace;
font-size: 0.85rem;
font-weight: 700;
color: #94a3b8;
background: #0f172a;
}
#bin-app .bit-cell.one {
background: #0e4a58;
border-color: #06b6d4;
color: #06b6d4;
}
#bin-app .bit-cell .bit-idx {
font-size: 0.5rem;
color: #475569;
font-weight: 400;
margin-top: 1px;
}

#bin-app .twos-section {
background: #1e293b;
border: 1.5px solid #334155;
border-radius: 10px;
padding: 16px;
margin-bottom: 20px;
}
#bin-app .twos-row {
display: flex;
flex-direction: column;
gap: 8px;
}
#bin-app .twos-line {
display: flex;
gap: 12px;
align-items: center;
flex-wrap: wrap;
}
#bin-app .twos-line .t-label {
font-size: 0.78rem;
color: #64748b;
min-width: 140px;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.05em;
}
#bin-app .twos-line .t-val {
font-family: 'Courier New', monospace;
font-size: 0.92rem;
color: #a5f3fc;
word-break: break-all;
}

#bin-app .text-section {
background: #1e293b;
border: 1.5px solid #334155;
border-radius: 10px;
padding: 16px;
margin-bottom: 12px;
}
#bin-app .text-section textarea {
width: 100%;
background: #0f172a;
border: 1.5px solid #334155;
color: #e2e8f0;
border-radius: 8px;
padding: 10px 12px;
font-family: 'Courier New', monospace;
font-size: 0.9rem;
resize: vertical;
min-height: 90px;
transition: border-color 0.15s;
}
#bin-app .text-section textarea:focus { outline: none; border-color: #06b6d4; }
#bin-app .text-out {
margin-top: 12px;
padding: 10px 12px;
background: #0f172a;
border-radius: 8px;
font-family: 'Courier New', monospace;
font-size: 0.85rem;
color: #06b6d4;
word-break: break-all;
min-height: 44px;
line-height: 1.7;
}
#bin-app .text-actions {
display: flex;
gap: 8px;
margin-top: 10px;
flex-wrap: wrap;
}
#bin-app .text-actions button {
background: #0e4a58;
border: 1px solid #06b6d4;
color: #06b6d4;
border-radius: 6px;
padding: 6px 14px;
font-size: 0.82rem;
cursor: pointer;
transition: all 0.15s;
}
#bin-app .text-actions button:hover { background: #06b6d4; color: #0f172a; }
#bin-app .text-actions button.copied { background: #06b6d4; color: #0f172a; }

#bin-app .section-title {
font-size: 0.78rem;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.08em;
font-weight: 600;
margin-bottom: 10px;
}
</style>

<!-- モード切替タブ -->
<div class="mode-tabs">
<button class="mode-tab active" onclick="binSetMode('number')" id="tab-number">進数変換</button>
<button class="mode-tab" onclick="binSetMode('text2bin')" id="tab-text2bin">テキスト → バイナリ</button>
<button class="mode-tab" onclick="binSetMode('bin2text')" id="tab-bin2text">バイナリ → テキスト</button>
</div>

<!-- 進数変換モード -->
<div id="mode-number">
<h2>進数変換</h2>
<div class="input-row">
<select id="base-select" onchange="binConvert()">
<option value="2">2進数（Base 2）</option>
<option value="8">8進数（Base 8）</option>
<option value="10" selected>10進数（Base 10）</option>
<option value="16">16進数（Base 16）</option>
</select>
<input type="text" id="main-input" placeholder="数値を入力..." oninput="binConvert()" autocomplete="off" spellcheck="false">
</div>
<div class="error-msg" id="error-msg"></div>

<div class="outputs-grid">
<div class="output-card">
<div class="label">2進数（Base 2）</div>
<div class="value" id="out-bin">—</div>
<button class="copy-btn" onclick="binCopy('out-bin', this)">コピー</button>
</div>
<div class="output-card">
<div class="label">8進数（Base 8）</div>
<div class="value" id="out-oct">—</div>
<button class="copy-btn" onclick="binCopy('out-oct', this)">コピー</button>
</div>
<div class="output-card">
<div class="label">10進数（Base 10）</div>
<div class="value" id="out-dec">—</div>
<button class="copy-btn" onclick="binCopy('out-dec', this)">コピー</button>
</div>
<div class="output-card">
<div class="label">16進数（Base 16）</div>
<div class="value" id="out-hex">—</div>
<button class="copy-btn" onclick="binCopy('out-hex', this)">コピー</button>
</div>
</div>

<!-- ビット操作表示 -->
<div class="bit-section">
<div class="section-title">ビット操作表示</div>
<div class="bit-toggle-row">
<button class="bit-toggle active" onclick="binSetBits(8, this)">8ビット</button>
<button class="bit-toggle" onclick="binSetBits(16, this)">16ビット</button>
<button class="bit-toggle" onclick="binSetBits(32, this)">32ビット</button>
</div>
<div class="bit-grid" id="bit-grid"></div>
</div>

<!-- 2の補数表示 -->
<div class="twos-section" id="twos-section" style="display:none">
<div class="section-title">2の補数（負の数）</div>
<div class="twos-row" id="twos-rows"></div>
</div>
</div>

<!-- テキスト → バイナリモード -->
<div id="mode-text2bin" style="display:none">
<h2>テキスト → バイナリ</h2>
<div class="text-section">
<div class="section-title">入力テキスト</div>
<textarea id="t2b-input" placeholder="テキストを入力または貼り付け..." oninput="binText2Bin()"></textarea>
<div class="section-title" style="margin-top:14px">バイナリ出力（1文字 = 8ビット）</div>
<div class="text-out" id="t2b-output"></div>
<div class="text-actions">
<button onclick="binCopyEl('t2b-output', this)">バイナリをコピー</button>
<button onclick="binClearText('t2b-input','t2b-output')">クリア</button>
</div>
</div>
</div>

<!-- バイナリ → テキストモード -->
<div id="mode-bin2text" style="display:none">
<h2>バイナリ → テキスト</h2>
<div class="text-section">
<div class="section-title">バイナリ入力（スペース区切りの8ビットグループ）</div>
<textarea id="b2t-input" placeholder="01001000 01100101 01101100 01101100 01101111" oninput="binBin2Text()"></textarea>
<div class="section-title" style="margin-top:14px">テキスト出力</div>
<div class="text-out" id="b2t-output"></div>
<div class="text-actions">
<button onclick="binCopyEl('b2t-output', this)">テキストをコピー</button>
<button onclick="binClearText('b2t-input','b2t-output')">クリア</button>
</div>
</div>
</div>

<script>
(function() {
var _bitWidth = 8;
var _currentVal = null;

window.binSetMode = function(mode) {
['number','text2bin','bin2text'].forEach(function(m) {
document.getElementById('mode-'+m).style.display = (m === mode) ? '' : 'none';
var tab = document.getElementById('tab-'+m);
if (tab) tab.classList.toggle('active', m === mode);
});
};

window.binConvert = function() {
var inp = document.getElementById('main-input').value.trim();
var base = parseInt(document.getElementById('base-select').value);
var errEl = document.getElementById('error-msg');
var mainInp = document.getElementById('main-input');

if (!inp) {
['out-bin','out-oct','out-dec','out-hex'].forEach(function(id) {
document.getElementById(id).textContent = '—';
});
document.getElementById('twos-section').style.display = 'none';
mainInp.classList.remove('error');
errEl.textContent = '';
_currentVal = null;
binRenderBits(null);
return;
}

var patterns = { 2: /^-?[01]+$/, 8: /^-?[0-7]+$/, 10: /^-?\d+$/, 16: /^-?[0-9a-fA-F]+$/ };
if (!patterns[base].test(inp)) {
mainInp.classList.add('error');
errEl.textContent = '選択した進数で無効な文字が含まれています。';
return;
}
mainInp.classList.remove('error');
errEl.textContent = '';

var isNeg = inp.startsWith('-');
var absStr = isNeg ? inp.slice(1) : inp;
var n;
try {
if (base === 10) { n = BigInt(inp); }
else {
var pos = BigInt('0x' + (base === 16 ? absStr : parseInt(absStr, base).toString(16)));
n = isNeg ? -pos : pos;
}
} catch(e) {
mainInp.classList.add('error');
errEl.textContent = '数値が大きすぎるか無効です。';
return;
}

_currentVal = n;

var absN = n < 0n ? -n : n;
document.getElementById('out-bin').textContent = (n < 0n ? '-' : '') + absN.toString(2);
document.getElementById('out-oct').textContent = (n < 0n ? '-' : '') + absN.toString(8);
document.getElementById('out-dec').textContent = n.toString(10);
document.getElementById('out-hex').textContent = (n < 0n ? '-' : '') + absN.toString(16).toUpperCase();

binRenderBits(n);
binRenderTwos(n);
};

window.binSetBits = function(w, btn) {
_bitWidth = w;
document.querySelectorAll('#bin-app .bit-toggle').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
binRenderBits(_currentVal);
};

function binRenderBits(n) {
var grid = document.getElementById('bit-grid');
grid.innerHTML = '';
var bits = [];
if (n === null || n === undefined) {
for (var i = 0; i < _bitWidth; i++) bits.push(0);
} else {
var absN = n < 0n ? -n : n;
var binStr;
if (n < 0n) {
binStr = twosComplementStr(n, _bitWidth);
} else {
binStr = absN.toString(2).slice(-_bitWidth).padStart(_bitWidth, '0');
}
for (var j = 0; j < binStr.length; j++) bits.push(parseInt(binStr[j]));
}
for (var k = 0; k < bits.length; k++) {
var cell = document.createElement('div');
cell.className = 'bit-cell' + (bits[k] ? ' one' : '');
var bval = document.createElement('div');
bval.textContent = bits[k];
var bidx = document.createElement('div');
bidx.className = 'bit-idx';
bidx.textContent = (bits.length - 1 - k);
cell.appendChild(bval);
cell.appendChild(bidx);
grid.appendChild(cell);
}
}

function twosComplementStr(n, width) {
var mask = (1n << BigInt(width)) - 1n;
var tc = (((-n) ^ mask) + 1n) & mask;
return tc.toString(2).padStart(width, '0');
}

function binRenderTwos(n) {
var sec = document.getElementById('twos-section');
var rows = document.getElementById('twos-rows');
if (n === null || n >= 0n) { sec.style.display = 'none'; return; }
sec.style.display = '';
var absN = -n;
var w = _bitWidth;
if (absN >= (1n << BigInt(w - 1))) w = 16;
if (absN >= (1n << BigInt(w - 1))) w = 32;
if (absN >= (1n << BigInt(w - 1))) w = 64;

var original = absN.toString(2).padStart(w, '0');
var inverted = '';
for (var i = 0; i < original.length; i++) inverted += original[i] === '0' ? '1' : '0';
var tc = twosComplementStr(n, w);
var decVal = n.toString(10);

rows.innerHTML = '';
[
['元の値（絶対値）', original],
['ビット反転（1の補数）', inverted],
['2の補数（' + w + 'ビット）', tc],
['10進数値', decVal]
].forEach(function(pair) {
var row = document.createElement('div');
row.className = 'twos-line';
row.innerHTML = '<span class="t-label">' + pair[0] + '</span><span class="t-val">' + pair[1] + '</span>';
rows.appendChild(row);
});
}

window.binCopy = function(id, btn) {
var text = document.getElementById(id).textContent;
if (text === '—' || !text) return;
navigator.clipboard.writeText(text).then(function() {
btn.textContent = 'コピー済！';
btn.classList.add('copied');
setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1500);
});
};

window.binCopyEl = function(id, btn) {
var text = document.getElementById(id).textContent;
if (!text) return;
navigator.clipboard.writeText(text).then(function() {
var orig = btn.textContent;
btn.textContent = 'コピー済！';
btn.classList.add('copied');
setTimeout(function() { btn.textContent = orig; btn.classList.remove('copied'); }, 1500);
});
};

window.binText2Bin = function() {
var text = document.getElementById('t2b-input').value;
var out = document.getElementById('t2b-output');
if (!text) { out.textContent = ''; return; }
var result = Array.from(text).map(function(ch) {
return ch.charCodeAt(0).toString(2).padStart(8, '0');
}).join(' ');
out.textContent = result;
};

window.binBin2Text = function() {
var raw = document.getElementById('b2t-input').value.trim();
var out = document.getElementById('b2t-output');
if (!raw) { out.textContent = ''; return; }
var groups = raw.split(/\s+/);
var result = '';
var valid = true;
groups.forEach(function(g) {
if (/^[01]{1,8}$/.test(g)) {
result += String.fromCharCode(parseInt(g, 2));
} else {
valid = false;
}
});
out.textContent = valid ? result : result + '（一部のグループが無効です）';
};

window.binClearText = function(inId, outId) {
document.getElementById(inId).value = '';
document.getElementById(outId).textContent = '';
};

binRenderBits(null);
})();
</script>

</div>

---

**開発業務の経費管理にはfreee**
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
