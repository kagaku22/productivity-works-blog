---
title: "Number Base Converter"
date: 2025-05-16
description: "Free number base converter. Convert between binary, octal, decimal, and hexadecimal. Bitwise operations, two's complement, and custom base support."
categories: ["Free Tools"]
slug: "number-base-converter"
ShowToc: false
cover:
  image: "/images/covers/number-base-converter.png"
  alt: "Number Base Converter"
---

<div id="nb-app">

<style>
#nb-app *, #nb-app *::before, #nb-app *::after { box-sizing: border-box; margin: 0; padding: 0; }
#nb-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  max-width: 720px;
  margin: 0 auto;
  padding: 12px;
  color: #1e293b;
}
#nb-app h2.nb-title {
  font-size: 18px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 14px;
  letter-spacing: -0.3px;
}
#nb-app .nb-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 18px;
  margin-bottom: 14px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#nb-app .nb-input-row {
  display: flex;
  gap: 10px;
  align-items: flex-end;
  flex-wrap: wrap;
}
#nb-app .nb-field {
  display: flex;
  flex-direction: column;
  gap: 5px;
  flex: 1;
  min-width: 160px;
}
#nb-app .nb-field label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}
#nb-app .nb-input {
  padding: 10px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 16px;
  font-family: 'Courier New', Courier, monospace;
  font-weight: 600;
  color: #0f172a;
  background: #f8fafc;
  transition: border-color 0.2s;
  width: 100%;
}
#nb-app .nb-input:focus {
  outline: none;
  border-color: #6366f1;
  background: #fff;
}
#nb-app .nb-input.nb-error {
  border-color: #f43f5e;
  background: #fff1f2;
}
#nb-app select.nb-select {
  padding: 10px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  color: #0f172a;
  background: #f8fafc;
  cursor: pointer;
  min-width: 120px;
}
#nb-app select.nb-select:focus {
  outline: none;
  border-color: #6366f1;
}
#nb-app .nb-error-msg {
  font-size: 12px;
  color: #f43f5e;
  min-height: 16px;
  margin-top: 4px;
}
#nb-app .nb-results-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  margin-bottom: 10px;
}
#nb-app .nb-result-item {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 12px 14px;
  position: relative;
}
#nb-app .nb-result-item.nb-active {
  border-color: #6366f1;
  background: #eef2ff;
}
#nb-app .nb-result-label {
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.6px;
  margin-bottom: 4px;
}
#nb-app .nb-result-value {
  font-family: 'Courier New', Courier, monospace;
  font-size: 15px;
  font-weight: 700;
  color: #0f172a;
  word-break: break-all;
  line-height: 1.4;
  padding-right: 28px;
}
#nb-app .nb-copy-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  cursor: pointer;
  color: #94a3b8;
  font-size: 14px;
  padding: 2px 4px;
  border-radius: 4px;
  transition: color 0.2s, background 0.2s;
  line-height: 1;
}
#nb-app .nb-copy-btn:hover { color: #6366f1; background: #e0e7ff; }
#nb-app .nb-copy-btn.nb-copied { color: #22c55e; }
#nb-app .nb-custom-row {
  display: flex;
  gap: 10px;
  align-items: flex-end;
  flex-wrap: wrap;
  margin-top: 10px;
}
#nb-app .nb-custom-result {
  background: #f0fdf4;
  border: 1.5px solid #bbf7d0;
  border-radius: 10px;
  padding: 12px 14px;
  flex: 1;
  min-width: 200px;
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 3px;
}
#nb-app .nb-custom-result .nb-result-label { color: #16a34a; }
#nb-app .nb-custom-result .nb-result-value { padding-right: 28px; }
#nb-app .nb-section-title {
  font-size: 13px;
  font-weight: 700;
  color: #475569;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 6px;
}
#nb-app .nb-bit-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 10px;
  flex-wrap: wrap;
}
#nb-app .nb-tab-btn {
  padding: 5px 14px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  background: #f8fafc;
  font-size: 12px;
  font-weight: 600;
  color: #475569;
  cursor: pointer;
  transition: all 0.15s;
}
#nb-app .nb-tab-btn.nb-active-tab {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#nb-app .nb-bit-display {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
  font-family: 'Courier New', Courier, monospace;
}
#nb-app .nb-bit-group {
  display: flex;
  gap: 2px;
}
#nb-app .nb-bit {
  width: 24px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 700;
  border-radius: 5px;
  border: 1.5px solid #e2e8f0;
  background: #f8fafc;
  color: #64748b;
  transition: all 0.1s;
}
#nb-app .nb-bit.nb-one {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
}
#nb-app .nb-bit.nb-msb {
  border-color: #f43f5e;
}
#nb-app .nb-bit-indices {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
  margin-top: 2px;
}
#nb-app .nb-bit-idx-group {
  display: flex;
  gap: 2px;
}
#nb-app .nb-bit-idx {
  width: 24px;
  font-size: 9px;
  color: #94a3b8;
  text-align: center;
}
#nb-app .nb-twos-row {
  margin-top: 10px;
  background: #fef3c7;
  border: 1.5px solid #fde68a;
  border-radius: 8px;
  padding: 10px 14px;
}
#nb-app .nb-twos-row .nb-result-label { color: #92400e; margin-bottom: 4px; }
#nb-app .nb-twos-value {
  font-family: 'Courier New', Courier, monospace;
  font-size: 14px;
  font-weight: 700;
  color: #7c3aed;
  word-break: break-all;
}
#nb-app .nb-ascii-row {
  margin-top: 8px;
  background: #f0fdf4;
  border: 1.5px solid #bbf7d0;
  border-radius: 8px;
  padding: 10px 14px;
  display: flex;
  align-items: center;
  gap: 10px;
}
#nb-app .nb-ascii-label {
  font-size: 11px;
  font-weight: 700;
  color: #15803d;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  white-space: nowrap;
}
#nb-app .nb-ascii-char {
  font-family: 'Courier New', Courier, monospace;
  font-size: 22px;
  font-weight: 700;
  color: #065f46;
  background: #dcfce7;
  border-radius: 6px;
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
}
#nb-app .nb-ascii-info {
  font-size: 12px;
  color: #166534;
}
#nb-app .nb-bitwise-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}
#nb-app .nb-bitwise-result {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  padding: 10px 12px;
  position: relative;
}
#nb-app .nb-bitwise-result .nb-result-label { margin-bottom: 4px; }
#nb-app .nb-bitwise-result .nb-result-value { font-size: 13px; }
#nb-app .nb-op-label {
  font-size: 11px;
  font-weight: 800;
  color: #6366f1;
  background: #e0e7ff;
  border-radius: 4px;
  padding: 1px 6px;
  display: inline-block;
  margin-bottom: 4px;
}
#nb-app .nb-shift-controls {
  display: flex;
  gap: 8px;
  align-items: center;
  margin-top: 8px;
  flex-wrap: wrap;
}
#nb-app .nb-shift-btn {
  padding: 6px 14px;
  border: 1.5px solid #6366f1;
  border-radius: 7px;
  background: #fff;
  color: #6366f1;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.15s;
}
#nb-app .nb-shift-btn:hover { background: #6366f1; color: #fff; }
#nb-app .nb-shift-input {
  width: 56px;
  padding: 6px 8px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 13px;
  text-align: center;
}
#nb-app .nb-shift-input:focus { outline: none; border-color: #6366f1; }
#nb-app .nb-b-label {
  font-size: 12px;
  color: #64748b;
  font-weight: 600;
}
#nb-app .nb-b-input {
  padding: 8px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 15px;
  font-family: 'Courier New', Courier, monospace;
  font-weight: 600;
  width: 100%;
  background: #f8fafc;
}
#nb-app .nb-b-input:focus { outline: none; border-color: #6366f1; background: #fff; }
#nb-app .nb-b-input.nb-error { border-color: #f43f5e; background: #fff1f2; }
@media (max-width: 520px) {
  #nb-app .nb-results-grid { grid-template-columns: 1fr; }
  #nb-app .nb-bitwise-grid { grid-template-columns: 1fr; }
  #nb-app .nb-bit { width: 20px; height: 26px; font-size: 11px; }
  #nb-app .nb-bit-idx { width: 20px; }
}
</style>

<h2 class="nb-title">Number Base Converter</h2>

<div class="nb-card">
  <div class="nb-section-title">Input</div>
  <div class="nb-input-row">
    <div class="nb-field" style="flex:2;min-width:200px;">
      <label for="nb-num-input">Number</label>
      <input id="nb-num-input" class="nb-input" type="text" placeholder="Enter a number..." autocomplete="off" spellcheck="false">
    </div>
    <div class="nb-field" style="flex:1;min-width:140px;">
      <label for="nb-base-select">Input Base</label>
      <select id="nb-base-select" class="nb-select">
        <option value="2">Base 2 (Binary)</option>
        <option value="8">Base 8 (Octal)</option>
        <option value="10" selected>Base 10 (Decimal)</option>
        <option value="16">Base 16 (Hex)</option>
      </select>
    </div>
  </div>
  <div class="nb-error-msg" id="nb-error"></div>
</div>

<div class="nb-card">
  <div class="nb-section-title">Conversions</div>
  <div class="nb-results-grid">
    <div class="nb-result-item" id="nb-r-bin">
      <div class="nb-result-label">Binary (Base 2)</div>
      <div class="nb-result-value" id="nb-v-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-v-bin',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-result-item" id="nb-r-oct">
      <div class="nb-result-label">Octal (Base 8)</div>
      <div class="nb-result-value" id="nb-v-oct">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-v-oct',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-result-item" id="nb-r-dec">
      <div class="nb-result-label">Decimal (Base 10)</div>
      <div class="nb-result-value" id="nb-v-dec">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-v-dec',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-result-item" id="nb-r-hex">
      <div class="nb-result-label">Hexadecimal (Base 16)</div>
      <div class="nb-result-value" id="nb-v-hex">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-v-hex',this)" title="Copy">&#x2398;</button>
    </div>
  </div>

  <div class="nb-custom-row">
    <div class="nb-field" style="min-width:120px;max-width:160px;">
      <label for="nb-custom-base">Custom Base (2–36)</label>
      <input id="nb-custom-base" class="nb-input" type="number" min="2" max="36" value="12" style="font-size:14px;">
    </div>
    <div class="nb-custom-result">
      <div class="nb-result-label" id="nb-custom-label">Base 12</div>
      <div class="nb-result-value" id="nb-v-custom">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-v-custom',this)" title="Copy">&#x2398;</button>
    </div>
  </div>
</div>

<div class="nb-card">
  <div class="nb-section-title">Bit View</div>
  <div class="nb-bit-tabs">
    <button class="nb-tab-btn nb-active-tab" onclick="nbSetBits(8,this)">8-bit</button>
    <button class="nb-tab-btn" onclick="nbSetBits(16,this)">16-bit</button>
    <button class="nb-tab-btn" onclick="nbSetBits(32,this)">32-bit</button>
  </div>
  <div class="nb-bit-display" id="nb-bit-display"></div>
  <div class="nb-bit-indices" id="nb-bit-indices"></div>

  <div class="nb-twos-row" id="nb-twos-wrap" style="display:none;">
    <div class="nb-result-label">Two's Complement (negative representation)</div>
    <div class="nb-twos-value" id="nb-twos-value"></div>
  </div>

  <div class="nb-ascii-row" id="nb-ascii-wrap" style="display:none;">
    <div class="nb-ascii-label">ASCII</div>
    <div class="nb-ascii-char" id="nb-ascii-char"></div>
    <div class="nb-ascii-info" id="nb-ascii-info"></div>
  </div>
</div>

<div class="nb-card">
  <div class="nb-section-title">Bitwise Operations</div>
  <div style="margin-bottom:10px;">
    <div class="nb-b-label" style="margin-bottom:4px;">Operand B (decimal)</div>
    <input id="nb-b-input" class="nb-b-input" type="text" placeholder="Enter second number (decimal)..." autocomplete="off">
    <div class="nb-error-msg" id="nb-b-error"></div>
  </div>
  <div class="nb-bitwise-grid" id="nb-bitwise-grid">
    <div class="nb-bitwise-result">
      <div class="nb-op-label">AND</div>
      <div class="nb-result-label">A AND B</div>
      <div class="nb-result-value" id="nb-and-dec">—</div>
      <div class="nb-result-value" style="font-size:11px;color:#64748b;" id="nb-and-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-and-dec',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-bitwise-result">
      <div class="nb-op-label">OR</div>
      <div class="nb-result-label">A OR B</div>
      <div class="nb-result-value" id="nb-or-dec">—</div>
      <div class="nb-result-value" style="font-size:11px;color:#64748b;" id="nb-or-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-or-dec',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-bitwise-result">
      <div class="nb-op-label">XOR</div>
      <div class="nb-result-label">A XOR B</div>
      <div class="nb-result-value" id="nb-xor-dec">—</div>
      <div class="nb-result-value" style="font-size:11px;color:#64748b;" id="nb-xor-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-xor-dec',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-bitwise-result">
      <div class="nb-op-label">NOT</div>
      <div class="nb-result-label">NOT A (32-bit)</div>
      <div class="nb-result-value" id="nb-not-dec">—</div>
      <div class="nb-result-value" style="font-size:11px;color:#64748b;" id="nb-not-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-not-dec',this)" title="Copy">&#x2398;</button>
    </div>
  </div>
  <div class="nb-shift-controls">
    <span class="nb-b-label">Shift A by</span>
    <input id="nb-shift-n" class="nb-shift-input" type="number" value="1" min="1" max="31">
    <span class="nb-b-label">bits:</span>
    <button class="nb-shift-btn" onclick="nbShift('left')">&#x00AB; Left (SHL)</button>
    <button class="nb-shift-btn" onclick="nbShift('right')">Right (SHR) &#x00BB;</button>
  </div>
  <div style="margin-top:8px;display:flex;gap:10px;flex-wrap:wrap;">
    <div class="nb-bitwise-result" style="flex:1;min-width:180px;">
      <div class="nb-op-label">SHL</div>
      <div class="nb-result-label">Shift Left Result</div>
      <div class="nb-result-value" id="nb-shl-dec">—</div>
      <div class="nb-result-value" style="font-size:11px;color:#64748b;" id="nb-shl-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-shl-dec',this)" title="Copy">&#x2398;</button>
    </div>
    <div class="nb-bitwise-result" style="flex:1;min-width:180px;">
      <div class="nb-op-label">SHR</div>
      <div class="nb-result-label">Shift Right Result</div>
      <div class="nb-result-value" id="nb-shr-dec">—</div>
      <div class="nb-result-value" style="font-size:11px;color:#64748b;" id="nb-shr-bin">—</div>
      <button class="nb-copy-btn" onclick="nbCopy('nb-shr-dec',this)" title="Copy">&#x2398;</button>
    </div>
  </div>
</div>

<script>
(function(){
  var nbBitWidth = 8;
  var nbCurrentDec = null;

  function nbGetInput() {
    return document.getElementById('nb-num-input').value.trim();
  }
  function nbGetBase() {
    return parseInt(document.getElementById('nb-base-select').value, 10);
  }
  function nbSetError(msg) {
    document.getElementById('nb-error').textContent = msg || '';
  }

  function nbParseToBigInt(str, base) {
    str = str.trim().toUpperCase();
    var negative = false;
    if (str.startsWith('-')) { negative = true; str = str.slice(1); }
    if (!str) return null;
    var digits = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    var val = BigInt(0);
    var b = BigInt(base);
    for (var i = 0; i < str.length; i++) {
      var d = digits.indexOf(str[i]);
      if (d < 0 || d >= base) return null;
      val = val * b + BigInt(d);
    }
    return negative ? -val : val;
  }

  function nbConvert() {
    var str = nbGetInput();
    var base = nbGetBase();
    var ids = ['nb-r-bin','nb-r-oct','nb-r-dec','nb-r-hex'];
    ids.forEach(function(id){ document.getElementById(id).classList.remove('nb-active'); });
    var activeMap = {2:'nb-r-bin',8:'nb-r-oct',10:'nb-r-dec',16:'nb-r-hex'};
    if (activeMap[base]) document.getElementById(activeMap[base]).classList.add('nb-active');

    if (!str) {
      nbSetError('');
      ['nb-v-bin','nb-v-oct','nb-v-dec','nb-v-hex','nb-v-custom'].forEach(function(id){
        document.getElementById(id).textContent = '—';
      });
      nbCurrentDec = null;
      nbRenderBits(null);
      nbClearBitwise();
      return;
    }

    var val = nbParseToBigInt(str, base);
    if (val === null) {
      nbSetError('Invalid characters for base ' + base);
      ['nb-v-bin','nb-v-oct','nb-v-dec','nb-v-hex','nb-v-custom'].forEach(function(id){
        document.getElementById(id).textContent = '—';
      });
      document.getElementById('nb-num-input').classList.add('nb-error');
      nbCurrentDec = null;
      nbRenderBits(null);
      nbClearBitwise();
      return;
    }
    document.getElementById('nb-num-input').classList.remove('nb-error');
    nbSetError('');
    nbCurrentDec = val;

    var prefix = val < 0n ? '-' : '';
    var absVal = val < 0n ? -val : val;

    document.getElementById('nb-v-bin').textContent = prefix + absVal.toString(2);
    document.getElementById('nb-v-oct').textContent = prefix + absVal.toString(8);
    document.getElementById('nb-v-dec').textContent = val.toString(10);
    document.getElementById('nb-v-hex').textContent = (prefix + absVal.toString(16)).toUpperCase();

    var cb = parseInt(document.getElementById('nb-custom-base').value, 10);
    nbUpdateCustom(val, cb);

    nbRenderBits(val);
    nbUpdateBitwise();
    nbUpdateAscii(val);
  }

  function nbUpdateCustom(val, cb) {
    if (isNaN(cb) || cb < 2 || cb > 36) {
      document.getElementById('nb-v-custom').textContent = 'Invalid base';
      document.getElementById('nb-custom-label').textContent = 'Custom Base';
      return;
    }
    document.getElementById('nb-custom-label').textContent = 'Base ' + cb;
    if (val === null) { document.getElementById('nb-v-custom').textContent = '—'; return; }
    var prefix = val < 0n ? '-' : '';
    var absVal = val < 0n ? -val : val;
    document.getElementById('nb-v-custom').textContent = (prefix + absVal.toString(cb)).toUpperCase();
  }

  function nbRenderBits(val) {
    var display = document.getElementById('nb-bit-display');
    var indices = document.getElementById('nb-bit-indices');
    display.innerHTML = '';
    indices.innerHTML = '';

    var bits = nbBitWidth;
    var bitsArr = [];
    if (val !== null) {
      var n = val;
      if (n < 0n) {
        // Two's complement
        var mask = (1n << BigInt(bits)) - 1n;
        n = (n & mask);
      }
      var binStr = n.toString(2);
      binStr = binStr.slice(-bits).padStart(bits, '0');
      for (var i = 0; i < bits; i++) bitsArr.push(binStr[i] === '1' ? 1 : 0);
    } else {
      for (var i = 0; i < bits; i++) bitsArr.push(0);
    }

    // Render in groups of 4
    var groupSize = 4;
    var groups = Math.ceil(bits / groupSize);
    for (var g = 0; g < groups; g++) {
      var grpEl = document.createElement('div');
      grpEl.className = 'nb-bit-group';
      var start = g * groupSize;
      var end = Math.min(start + groupSize, bits);
      for (var b = start; b < end; b++) {
        var bitEl = document.createElement('div');
        bitEl.className = 'nb-bit' + (bitsArr[b] ? ' nb-one' : '') + (b === 0 ? ' nb-msb' : '');
        bitEl.textContent = bitsArr[b];
        grpEl.appendChild(bitEl);
      }
      display.appendChild(grpEl);
    }

    // Render indices
    for (var g = 0; g < groups; g++) {
      var idxGrp = document.createElement('div');
      idxGrp.className = 'nb-bit-idx-group';
      var start = g * groupSize;
      var end = Math.min(start + groupSize, bits);
      for (var b = start; b < end; b++) {
        var idxEl = document.createElement('div');
        idxEl.className = 'nb-bit-idx';
        idxEl.textContent = bits - 1 - b;
        idxGrp.appendChild(idxEl);
      }
      indices.appendChild(idxGrp);
    }

    // Two's complement display for negative values
    var twosWrap = document.getElementById('nb-twos-wrap');
    if (val !== null && val < 0n) {
      twosWrap.style.display = '';
      var mask = (1n << BigInt(bits)) - 1n;
      var tc = (val & mask);
      document.getElementById('nb-twos-value').textContent =
        tc.toString(2).padStart(bits, '0') + ' (binary) = ' + tc.toString(10) + ' (unsigned decimal) = 0x' + tc.toString(16).toUpperCase();
    } else {
      twosWrap.style.display = 'none';
    }
  }

  function nbUpdateAscii(val) {
    var wrap = document.getElementById('nb-ascii-wrap');
    if (val === null || val < 0n || val > 127n) {
      wrap.style.display = 'none';
      return;
    }
    var code = Number(val);
    wrap.style.display = '';
    var charEl = document.getElementById('nb-ascii-char');
    var infoEl = document.getElementById('nb-ascii-info');
    var controlNames = {0:'NUL',1:'SOH',2:'STX',3:'ETX',4:'EOT',5:'ENQ',6:'ACK',7:'BEL',8:'BS',9:'HT',10:'LF',11:'VT',12:'FF',13:'CR',14:'SO',15:'SI',16:'DLE',17:'DC1',18:'DC2',19:'DC3',20:'DC4',21:'NAK',22:'SYN',23:'ETB',24:'CAN',25:'EM',26:'SUB',27:'ESC',28:'FS',29:'GS',30:'RS',31:'US',127:'DEL'};
    if (controlNames[code] !== undefined) {
      charEl.textContent = controlNames[code];
      charEl.style.fontSize = '11px';
      infoEl.textContent = 'Control character (non-printable)';
    } else {
      charEl.textContent = String.fromCharCode(code);
      charEl.style.fontSize = '22px';
      infoEl.textContent = 'ASCII code ' + code + ' — printable character';
    }
  }

  function nbGetBVal() {
    var bStr = document.getElementById('nb-b-input').value.trim();
    document.getElementById('nb-b-error').textContent = '';
    document.getElementById('nb-b-input').classList.remove('nb-error');
    if (!bStr) return null;
    var bv = nbParseToBigInt(bStr, 10);
    if (bv === null) {
      document.getElementById('nb-b-error').textContent = 'Invalid decimal number';
      document.getElementById('nb-b-input').classList.add('nb-error');
      return null;
    }
    return bv;
  }

  function nbFmtBitwise(dec, prefix) {
    if (dec === null) return;
    var absVal = dec < 0n ? -dec : dec;
    var sign = dec < 0n ? '-' : '';
    var binStr = sign + absVal.toString(2);
    return { dec: dec.toString(10), bin: binStr };
  }

  function nbUpdateBitwise() {
    var a = nbCurrentDec;
    var b = nbGetBVal();

    // NOT is unary — always compute from A
    if (a !== null) {
      var notVal = ~BigInt(Number(a));
      document.getElementById('nb-not-dec').textContent = notVal.toString(10);
      var notAbs = notVal < 0n ? -notVal : notVal;
      document.getElementById('nb-not-bin').textContent = (notVal < 0n ? '-' : '') + notAbs.toString(2);
    } else {
      document.getElementById('nb-not-dec').textContent = '—';
      document.getElementById('nb-not-bin').textContent = '—';
    }

    if (a === null || b === null) {
      ['and','or','xor'].forEach(function(op){
        document.getElementById('nb-'+op+'-dec').textContent = '—';
        document.getElementById('nb-'+op+'-bin').textContent = '—';
      });
      return;
    }

    var an = BigInt(Number(a));
    var bn = BigInt(Number(b));

    var ops = {and: an & bn, or: an | bn, xor: an ^ bn};
    Object.keys(ops).forEach(function(op){
      var v = ops[op];
      var abs = v < 0n ? -v : v;
      var sign = v < 0n ? '-' : '';
      document.getElementById('nb-'+op+'-dec').textContent = v.toString(10);
      document.getElementById('nb-'+op+'-bin').textContent = sign + abs.toString(2);
    });
  }

  function nbShift(dir) {
    if (nbCurrentDec === null) return;
    var n = parseInt(document.getElementById('nb-shift-n').value, 10);
    if (isNaN(n) || n < 1) n = 1;
    var a = BigInt(Number(nbCurrentDec));
    var shlVal = a << BigInt(n);
    var shrVal = a >> BigInt(n);

    var shlAbs = shlVal < 0n ? -shlVal : shlVal;
    var shrAbs = shrVal < 0n ? -shrVal : shrVal;
    document.getElementById('nb-shl-dec').textContent = shlVal.toString(10);
    document.getElementById('nb-shl-bin').textContent = (shlVal < 0n ? '-' : '') + shlAbs.toString(2);
    document.getElementById('nb-shr-dec').textContent = shrVal.toString(10);
    document.getElementById('nb-shr-bin').textContent = (shrVal < 0n ? '-' : '') + shrAbs.toString(2);
  }

  function nbClearBitwise() {
    ['nb-and-dec','nb-and-bin','nb-or-dec','nb-or-bin','nb-xor-dec','nb-xor-bin',
     'nb-not-dec','nb-not-bin','nb-shl-dec','nb-shl-bin','nb-shr-dec','nb-shr-bin'].forEach(function(id){
      document.getElementById(id).textContent = '—';
    });
  }

  window.nbCopy = function(id, btn) {
    var txt = document.getElementById(id).textContent;
    if (!txt || txt === '—') return;
    navigator.clipboard.writeText(txt).then(function(){
      btn.classList.add('nb-copied');
      btn.textContent = '\u2713';
      setTimeout(function(){ btn.classList.remove('nb-copied'); btn.textContent = '\u2398'; }, 1200);
    });
  };

  window.nbSetBits = function(n, el) {
    nbBitWidth = n;
    document.querySelectorAll('#nb-app .nb-tab-btn').forEach(function(b){ b.classList.remove('nb-active-tab'); });
    el.classList.add('nb-active-tab');
    nbRenderBits(nbCurrentDec);
  };

  window.nbShift = nbShift;

  document.getElementById('nb-num-input').addEventListener('input', nbConvert);
  document.getElementById('nb-base-select').addEventListener('change', nbConvert);
  document.getElementById('nb-custom-base').addEventListener('input', function(){
    var cb = parseInt(this.value, 10);
    nbUpdateCustom(nbCurrentDec, cb);
  });
  document.getElementById('nb-b-input').addEventListener('input', nbUpdateBitwise);

  nbRenderBits(null);
})();
</script>

> Scientific math → [Scientific Calculator](/tools/scientific-calculator/)
> Matrix math → [Matrix Calculator](/tools/matrix-calculator/)

</div>
