---
title: "Password Generator - Free Secure Random Password Tool"
date: 2025-05-16
description: "Generate strong, secure random passwords instantly. Customize length, characters, and complexity. Check password strength with our free online tool."
categories: ["Free Tools"]
tags: ["password", "security", "generator", "privacy", "online tool"]
slug: "password-generator"
aliases: ["/tools/random-password/", "/tools/secure-password/"]
cover:
  image: "/images/covers/password-generator.png"
  alt: "Password Generator"
ShowToc: false
---

<div id="password-app">

<style>
#password-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #e2e8f0;
}

#password-app * {
  box-sizing: border-box;
}

.pw-card {
  background: #0f2744;
  border: 1px solid #1e3a5f;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 16px;
}

.pw-mode-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
}

.pw-tab {
  flex: 1;
  padding: 10px 16px;
  border: 1px solid #1e3a5f;
  border-radius: 8px;
  background: #0a1f3a;
  color: #94a3b8;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.2s;
  text-align: center;
}

.pw-tab:hover {
  border-color: #3b82f6;
  color: #cbd5e1;
}

.pw-tab.active {
  background: #1e3a5f;
  border-color: #3b82f6;
  color: #fff;
}

.pw-display {
  background: #060f1e;
  border: 2px solid #1e3a5f;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 14px;
  position: relative;
  cursor: pointer;
  transition: border-color 0.2s;
  min-height: 64px;
  display: flex;
  align-items: center;
}

.pw-display:hover {
  border-color: #3b82f6;
}

.pw-display.copied {
  border-color: #22c55e;
  background: #052010;
}

.pw-text {
  font-family: 'Courier New', Courier, monospace;
  font-size: 18px;
  font-weight: 600;
  word-break: break-all;
  line-height: 1.5;
  flex: 1;
  color: #e2e8f0;
  letter-spacing: 0.04em;
}

.pw-copy-hint {
  font-size: 11px;
  color: #475569;
  position: absolute;
  top: 6px;
  right: 10px;
}

.pw-copy-confirm {
  position: absolute;
  top: 50%;
  right: 14px;
  transform: translateY(-50%);
  color: #22c55e;
  font-size: 13px;
  font-weight: 600;
  opacity: 0;
  transition: opacity 0.3s;
  pointer-events: none;
}

.pw-copy-confirm.show {
  opacity: 1;
}

.pw-actions {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.pw-btn {
  padding: 11px 22px;
  border-radius: 8px;
  border: none;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  gap: 6px;
}

.pw-btn-primary {
  background: #3b82f6;
  color: #fff;
  flex: 2;
}

.pw-btn-primary:hover {
  background: #2563eb;
  transform: translateY(-1px);
}

.pw-btn-primary:active {
  transform: translateY(0);
}

.pw-btn-secondary {
  background: #1e3a5f;
  color: #cbd5e1;
  border: 1px solid #2d5a9e;
  flex: 1;
}

.pw-btn-secondary:hover {
  background: #2d5080;
  color: #fff;
}

.pw-btn-secondary.copied-btn {
  background: #14532d;
  border-color: #22c55e;
  color: #4ade80;
}

.pw-strength-section {
  margin-bottom: 20px;
}

.pw-strength-label-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 6px;
}

.pw-strength-label {
  font-size: 13px;
  color: #94a3b8;
  font-weight: 500;
}

.pw-strength-name {
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 0.05em;
}

.pw-strength-bar-bg {
  background: #0a1f3a;
  border-radius: 4px;
  height: 8px;
  overflow: hidden;
  margin-bottom: 8px;
}

.pw-strength-bar {
  height: 100%;
  border-radius: 4px;
  transition: width 0.4s ease, background 0.4s;
  width: 0%;
}

.pw-entropy {
  font-size: 12px;
  color: #64748b;
  text-align: right;
}

.pw-strength-criteria {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 8px;
}

.pw-criterion {
  font-size: 11px;
  padding: 3px 8px;
  border-radius: 20px;
  background: #0a1f3a;
  border: 1px solid #1e3a5f;
  color: #64748b;
}

.pw-criterion.met {
  background: #0a2a1a;
  border-color: #22c55e;
  color: #4ade80;
}

.pw-label {
  display: block;
  font-size: 13px;
  color: #94a3b8;
  margin-bottom: 6px;
  font-weight: 500;
}

.pw-slider-row {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 20px;
}

.pw-slider {
  flex: 1;
  -webkit-appearance: none;
  appearance: none;
  height: 6px;
  background: #1e3a5f;
  border-radius: 3px;
  outline: none;
  cursor: pointer;
}

.pw-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #3b82f6;
  cursor: pointer;
  border: 2px solid #0f2744;
  box-shadow: 0 0 0 2px #3b82f6;
  transition: transform 0.15s;
}

.pw-slider::-webkit-slider-thumb:hover {
  transform: scale(1.15);
}

.pw-slider::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #3b82f6;
  cursor: pointer;
  border: 2px solid #0f2744;
}

.pw-length-val {
  min-width: 36px;
  text-align: center;
  font-size: 16px;
  font-weight: 700;
  color: #3b82f6;
  background: #0a1f3a;
  border: 1px solid #1e3a5f;
  border-radius: 6px;
  padding: 4px 6px;
}

.pw-checkboxes {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  margin-bottom: 16px;
}

.pw-checkbox-item {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  padding: 8px 12px;
  border: 1px solid #1e3a5f;
  border-radius: 8px;
  background: #0a1f3a;
  transition: all 0.2s;
  user-select: none;
}

.pw-checkbox-item:hover {
  border-color: #3b82f6;
  background: #0f2744;
}

.pw-checkbox-item input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #3b82f6;
  cursor: pointer;
  flex-shrink: 0;
}

.pw-checkbox-item .pw-cb-label {
  font-size: 13px;
  color: #cbd5e1;
  flex: 1;
}

.pw-checkbox-item .pw-cb-chars {
  font-size: 11px;
  color: #475569;
  font-family: monospace;
}

.pw-exclude-section {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-bottom: 16px;
}

.pw-exclude-item {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  user-select: none;
}

.pw-exclude-item input[type="checkbox"] {
  width: 15px;
  height: 15px;
  accent-color: #f59e0b;
  cursor: pointer;
}

.pw-exclude-item span {
  font-size: 13px;
  color: #94a3b8;
}

.pw-section-title {
  font-size: 12px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 10px;
}

.pw-passphrase-opts {
  display: flex;
  gap: 12px;
  align-items: center;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

.pw-passphrase-opts label {
  font-size: 13px;
  color: #94a3b8;
}

.pw-passphrase-opts select,
.pw-passphrase-opts input[type="number"] {
  background: #0a1f3a;
  border: 1px solid #1e3a5f;
  color: #e2e8f0;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 13px;
  outline: none;
  cursor: pointer;
}

.pw-passphrase-opts select:focus,
.pw-passphrase-opts input[type="number"]:focus {
  border-color: #3b82f6;
}

.pw-passphrase-opts input[type="number"] {
  width: 64px;
}

.pw-multi-section {
  display: none;
}

.pw-multi-section.active {
  display: block;
}

.pw-multi-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.pw-multi-item {
  display: flex;
  align-items: center;
  gap: 10px;
  background: #060f1e;
  border: 1px solid #1e3a5f;
  border-radius: 8px;
  padding: 10px 14px;
  transition: border-color 0.2s;
}

.pw-multi-item:hover {
  border-color: #2d5a9e;
}

.pw-multi-item.copied {
  border-color: #22c55e;
  background: #052010;
}

.pw-multi-pw {
  flex: 1;
  font-family: 'Courier New', Courier, monospace;
  font-size: 14px;
  color: #e2e8f0;
  word-break: break-all;
  letter-spacing: 0.03em;
}

.pw-multi-copy {
  padding: 5px 12px;
  border-radius: 6px;
  border: 1px solid #2d5a9e;
  background: #1e3a5f;
  color: #94a3b8;
  font-size: 12px;
  cursor: pointer;
  transition: all 0.2s;
  white-space: nowrap;
  flex-shrink: 0;
}

.pw-multi-copy:hover {
  background: #2d5080;
  color: #fff;
}

.pw-multi-copy.copied-btn {
  background: #14532d;
  border-color: #22c55e;
  color: #4ade80;
}

.pw-warning {
  background: #3b1a00;
  border: 1px solid #f59e0b;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 13px;
  color: #fcd34d;
  margin-bottom: 16px;
  display: none;
}

.pw-warning.show {
  display: block;
}

@media (max-width: 500px) {
  .pw-card { padding: 16px; }
  .pw-text { font-size: 15px; }
  .pw-checkboxes { grid-template-columns: 1fr; }
  .pw-actions { flex-direction: column; }
  .pw-btn { justify-content: center; }
  .pw-passphrase-opts { flex-direction: column; align-items: flex-start; gap: 8px; }
}
</style>

<div class="pw-card">
  <div class="pw-mode-tabs">
    <div class="pw-tab active" onclick="pwSetMode('random')" id="pw-tab-random">Random Password</div>
    <div class="pw-tab" onclick="pwSetMode('passphrase')" id="pw-tab-passphrase">Passphrase</div>
    <div class="pw-tab" onclick="pwSetMode('multi')" id="pw-tab-multi">Multiple (5x)</div>
  </div>

  <div id="pw-warning" class="pw-warning">Please select at least one character type.</div>

  <div id="pw-single-display">
    <div class="pw-display" id="pw-display-box" onclick="pwCopyMain()" title="Click to copy">
      <span class="pw-copy-hint">click to copy</span>
      <span class="pw-text" id="pw-output">Click Generate to create a password</span>
      <span class="pw-copy-confirm" id="pw-copy-confirm">Copied!</span>
    </div>

    <div class="pw-actions">
      <button class="pw-btn pw-btn-primary" onclick="pwGenerate()">&#8635; Generate</button>
      <button class="pw-btn pw-btn-secondary" id="pw-copy-btn" onclick="pwCopyMain()">&#128203; Copy</button>
    </div>
  </div>

  <div id="pw-multi-section" class="pw-multi-section">
    <div class="pw-multi-list" id="pw-multi-list"></div>
    <br>
    <button class="pw-btn pw-btn-primary" style="width:100%;justify-content:center;" onclick="pwGenerateMulti()">&#8635; Generate 5 Passwords</button>
  </div>

  <div class="pw-strength-section" id="pw-strength-section">
    <div class="pw-strength-label-row">
      <span class="pw-strength-label">Strength</span>
      <span class="pw-strength-name" id="pw-strength-name">—</span>
    </div>
    <div class="pw-strength-bar-bg">
      <div class="pw-strength-bar" id="pw-strength-bar"></div>
    </div>
    <div class="pw-entropy" id="pw-entropy">Entropy: —</div>
    <div class="pw-strength-criteria" id="pw-strength-criteria"></div>
  </div>
</div>

<div class="pw-card" id="pw-random-opts">
  <div class="pw-section-title">Password Length</div>
  <div class="pw-slider-row">
    <input type="range" class="pw-slider" id="pw-length-slider" min="8" max="128" value="16" oninput="pwUpdateLength()">
    <span class="pw-length-val" id="pw-length-val">16</span>
  </div>

  <div class="pw-section-title">Character Sets</div>
  <div class="pw-checkboxes">
    <label class="pw-checkbox-item">
      <input type="checkbox" id="pw-cb-upper" checked onchange="pwGenerate()">
      <span class="pw-cb-label">Uppercase</span>
      <span class="pw-cb-chars">A-Z</span>
    </label>
    <label class="pw-checkbox-item">
      <input type="checkbox" id="pw-cb-lower" checked onchange="pwGenerate()">
      <span class="pw-cb-label">Lowercase</span>
      <span class="pw-cb-chars">a-z</span>
    </label>
    <label class="pw-checkbox-item">
      <input type="checkbox" id="pw-cb-numbers" checked onchange="pwGenerate()">
      <span class="pw-cb-label">Numbers</span>
      <span class="pw-cb-chars">0-9</span>
    </label>
    <label class="pw-checkbox-item">
      <input type="checkbox" id="pw-cb-symbols" checked onchange="pwGenerate()">
      <span class="pw-cb-label">Symbols</span>
      <span class="pw-cb-chars">!@#$...</span>
    </label>
  </div>

  <div class="pw-section-title">Exclusions</div>
  <div class="pw-exclude-section">
    <label class="pw-exclude-item">
      <input type="checkbox" id="pw-exc-similar" onchange="pwGenerate()">
      <span>Exclude similar characters <code style="color:#94a3b8;font-size:11px;">I l 1 O 0</code></span>
    </label>
    <label class="pw-exclude-item">
      <input type="checkbox" id="pw-exc-ambiguous" onchange="pwGenerate()">
      <span>Exclude ambiguous symbols <code style="color:#94a3b8;font-size:11px;">{ } [ ] ( ) / \ ' " ` ~ , ; : . &lt; &gt;</code></span>
    </label>
  </div>
</div>

<div class="pw-card" id="pw-passphrase-opts" style="display:none;">
  <div class="pw-section-title">Passphrase Options</div>
  <div class="pw-passphrase-opts">
    <label>Words: <input type="number" id="pw-pp-words" value="4" min="3" max="10" onchange="pwGenerate()"></label>
    <label>Separator:
      <select id="pw-pp-sep" onchange="pwGenerate()">
        <option value="-">Hyphen (-)</option>
        <option value=".">Dot (.)</option>
        <option value="_">Underscore (_)</option>
        <option value=" ">Space ( )</option>
        <option value="">None</option>
      </select>
    </label>
    <label class="pw-exclude-item" style="margin:0;">
      <input type="checkbox" id="pw-pp-caps" onchange="pwGenerate()">
      <span>Capitalize words</span>
    </label>
    <label class="pw-exclude-item" style="margin:0;">
      <input type="checkbox" id="pw-pp-num" checked onchange="pwGenerate()">
      <span>Add number</span>
    </label>
  </div>
</div>

<script>
(function() {
  var WORDLIST = [
    "apple","bridge","castle","dragon","eagle","falcon","garden","harbor",
    "island","jungle","kernel","lemon","mango","nature","ocean","planet",
    "queen","river","sunset","tiger","umbrella","valley","winter","yellow",
    "zebra","anchor","bottle","candle","dancer","engine","forest","golden",
    "hammer","impact","jacket","kitten","lantern","marble","napkin","orange",
    "pepper","quartz","rocket","silver","tunnel","velvet","walnut","xenon",
    "yogurt","zipper","almond","basket","cherry","desert","expose","frozen",
    "grapes","hunter","indoor","jigsaw","kettle","locket","mirror","noodle",
    "oyster","pebble","raisin","saddle","tablet","useful","vendor","waffle",
    "xyster","yearly","zephyr","artist","borrow","casual","divide","editor",
    "fabric","gentle","hollow","invite","joyful","kindle","lively","modern",
    "narrow","offset","palace","random","stable","travel","update","vision",
    "wisdom","extern","yellow","bounce","carbon","direct","eleven","figure",
    "giggle","handle","inject","jockey","locket","muscle","notify","output",
    "pillow","rabbit","safety","tennis","unique","vertex","weapon","xylol",
    "zombie","active","border","create","deploy","effect","finish","growth",
    "health","intent","junior","kernel","listen","manage","normal","observe",
    "prefer","result","signal","ticket","unlock","verify","window","xtreme",
    "yearly","action","burden","center","defend","enable","factor","global",
    "happen","import","joined","leader","market","nature","option","passed",
    "remain","select","target","unable","volume","wealth","gained","humble",
    "iconic","jested","launch","marvel","nested","object","parent","quorum",
    "rescue","sample","taught","upbeat","vacant","wonder","expert","filter",
    "growth","hidden","impact","jumped","keeper","lifted","method","nation",
    "opened","punish","record","system","thread","upward","verbal","wooden",
    "extend","flying","gained","helped","ignore","joined","killed","locked",
    "mighty","nested","online","pulled","quoted","robust","served","tested",
    "urgent","viable","warned","xenial","yonder","zoning"
  ];

  var UPPER = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  var LOWER = 'abcdefghijklmnopqrstuvwxyz';
  var NUMS  = '0123456789';
  var SYMS  = '!@#$%^&*-_=+[]{}|;:,.<>?/~`';
  var SYMS_SAFE = '!@#$%^&*-_=+';
  var SIMILAR = 'Il1O0';
  var AMBIGUOUS = '{}[]()/\\\'"`~,;:.<>';

  var currentPw = '';
  var mode = 'random';

  function secureRand(max) {
    var arr = new Uint32Array(1);
    var limit = Math.floor(4294967296 / max) * max;
    do { crypto.getRandomValues(arr); } while (arr[0] >= limit);
    return arr[0] % max;
  }

  function buildCharset() {
    var charset = '';
    var excSimilar = document.getElementById('pw-exc-similar').checked;
    var excAmbig   = document.getElementById('pw-exc-ambiguous').checked;

    function filter(str) {
      var out = '';
      for (var i = 0; i < str.length; i++) {
        if (excSimilar && SIMILAR.indexOf(str[i]) !== -1) continue;
        if (excAmbig && AMBIGUOUS.indexOf(str[i]) !== -1) continue;
        out += str[i];
      }
      return out;
    }

    if (document.getElementById('pw-cb-upper').checked)   charset += filter(UPPER);
    if (document.getElementById('pw-cb-lower').checked)   charset += filter(LOWER);
    if (document.getElementById('pw-cb-numbers').checked) charset += filter(NUMS);
    if (document.getElementById('pw-cb-symbols').checked) {
      var syms = excAmbig ? SYMS_SAFE : SYMS;
      charset += filter(syms);
    }
    return charset;
  }

  function generateRandom(len) {
    var charset = buildCharset();
    if (!charset) return null;
    var pw = '';
    for (var i = 0; i < len; i++) {
      pw += charset[secureRand(charset.length)];
    }
    return pw;
  }

  function generatePassphrase() {
    var count = parseInt(document.getElementById('pw-pp-words').value) || 4;
    var sep   = document.getElementById('pw-pp-sep').value;
    var caps  = document.getElementById('pw-pp-caps').checked;
    var addNum = document.getElementById('pw-pp-num').checked;

    var words = [];
    for (var i = 0; i < count; i++) {
      var w = WORDLIST[secureRand(WORDLIST.length)];
      if (caps) w = w.charAt(0).toUpperCase() + w.slice(1);
      words.push(w);
    }
    var pw = words.join(sep);
    if (addNum) {
      var n = secureRand(100);
      pw += sep + n;
    }
    return pw;
  }

  function calcEntropy(pw, charset) {
    if (!pw) return 0;
    var pool = 0;
    if (/[A-Z]/.test(pw)) pool += 26;
    if (/[a-z]/.test(pw)) pool += 26;
    if (/[0-9]/.test(pw)) pool += 10;
    if (/[^A-Za-z0-9]/.test(pw)) pool += 32;
    if (pool === 0) return 0;
    return Math.round(pw.length * Math.log2(pool));
  }

  function calcPassphraseEntropy(wordCount) {
    return Math.round(wordCount * Math.log2(WORDLIST.length));
  }

  var strengthLevels = [
    { min: 0,   max: 25,  label: 'Weak',      color: '#ef4444', pct: 15 },
    { min: 25,  max: 40,  label: 'Fair',      color: '#f97316', pct: 35 },
    { min: 40,  max: 60,  label: 'Good',      color: '#eab308', pct: 57 },
    { min: 60,  max: 80,  label: 'Strong',    color: '#22c55e', pct: 78 },
    { min: 80,  max: 999, label: 'Very Strong', color: '#06b6d4', pct: 100 }
  ];

  function getStrength(entropy) {
    for (var i = 0; i < strengthLevels.length; i++) {
      var s = strengthLevels[i];
      if (entropy >= s.min && entropy < s.max) return s;
    }
    return strengthLevels[strengthLevels.length - 1];
  }

  function updateStrengthUI(pw, entropy) {
    var bar   = document.getElementById('pw-strength-bar');
    var name  = document.getElementById('pw-strength-name');
    var ent   = document.getElementById('pw-entropy');
    var crit  = document.getElementById('pw-strength-criteria');

    if (!pw) {
      bar.style.width = '0%';
      name.textContent = '—';
      ent.textContent = 'Entropy: —';
      crit.innerHTML = '';
      return;
    }

    var s = getStrength(entropy);
    bar.style.width = s.pct + '%';
    bar.style.background = s.color;
    name.textContent = s.label;
    name.style.color = s.color;
    ent.textContent = 'Entropy: ~' + entropy + ' bits';

    var criteria = [
      { label: '12+ chars',   met: pw.length >= 12 },
      { label: '16+ chars',   met: pw.length >= 16 },
      { label: 'Uppercase',   met: /[A-Z]/.test(pw) },
      { label: 'Lowercase',   met: /[a-z]/.test(pw) },
      { label: 'Numbers',     met: /[0-9]/.test(pw) },
      { label: 'Symbols',     met: /[^A-Za-z0-9]/.test(pw) },
      { label: '60+ bits',    met: entropy >= 60 },
      { label: '80+ bits',    met: entropy >= 80 }
    ];

    crit.innerHTML = '';
    criteria.forEach(function(c) {
      var span = document.createElement('span');
      span.className = 'pw-criterion' + (c.met ? ' met' : '');
      span.textContent = (c.met ? '✓ ' : '✗ ') + c.label;
      crit.appendChild(span);
    });
  }

  window.pwSetMode = function(m) {
    mode = m;
    document.getElementById('pw-tab-random').classList.toggle('active', m === 'random');
    document.getElementById('pw-tab-passphrase').classList.toggle('active', m === 'passphrase');
    document.getElementById('pw-tab-multi').classList.toggle('active', m === 'multi');

    document.getElementById('pw-random-opts').style.display    = (m === 'random') ? '' : 'none';
    document.getElementById('pw-passphrase-opts').style.display = (m === 'passphrase') ? '' : 'none';

    var singleDisp = document.getElementById('pw-single-display');
    var multiSec   = document.getElementById('pw-multi-section');
    var strengthSec = document.getElementById('pw-strength-section');

    if (m === 'multi') {
      singleDisp.style.display = 'none';
      multiSec.classList.add('active');
      strengthSec.style.display = 'none';
      pwGenerateMulti();
    } else {
      singleDisp.style.display = '';
      multiSec.classList.remove('active');
      strengthSec.style.display = '';
      pwGenerate();
    }
  };

  window.pwUpdateLength = function() {
    var val = document.getElementById('pw-length-slider').value;
    document.getElementById('pw-length-val').textContent = val;
    pwGenerate();
  };

  window.pwGenerate = function() {
    var pw, entropy;
    var warning = document.getElementById('pw-warning');

    if (mode === 'passphrase') {
      pw = generatePassphrase();
      var wc = parseInt(document.getElementById('pw-pp-words').value) || 4;
      entropy = calcPassphraseEntropy(wc);
    } else {
      var len = parseInt(document.getElementById('pw-length-slider').value);
      pw = generateRandom(len);
      if (!pw) {
        warning.classList.add('show');
        document.getElementById('pw-output').textContent = '—';
        currentPw = '';
        updateStrengthUI('', 0);
        return;
      }
      entropy = calcEntropy(pw, null);
    }

    warning.classList.remove('show');
    currentPw = pw;
    document.getElementById('pw-output').textContent = pw;
    updateStrengthUI(pw, entropy);

    var box = document.getElementById('pw-display-box');
    box.classList.remove('copied');
    document.getElementById('pw-copy-confirm').classList.remove('show');
    var copyBtn = document.getElementById('pw-copy-btn');
    copyBtn.classList.remove('copied-btn');
    copyBtn.innerHTML = '&#128203; Copy';
  };

  window.pwGenerateMulti = function() {
    var list = document.getElementById('pw-multi-list');
    list.innerHTML = '';
    for (var i = 0; i < 5; i++) {
      var pw;
      if (mode === 'multi') {
        var len = parseInt(document.getElementById('pw-length-slider').value) || 16;
        // Use last slider value if opts visible, else default
        pw = generateRandom(len) || generatePassphrase();
      } else {
        pw = generateRandom(16);
      }
      if (!pw) pw = generatePassphrase();
      (function(p) {
        var item = document.createElement('div');
        item.className = 'pw-multi-item';

        var txt = document.createElement('span');
        txt.className = 'pw-multi-pw';
        txt.textContent = p;

        var btn = document.createElement('button');
        btn.className = 'pw-multi-copy';
        btn.textContent = 'Copy';
        btn.onclick = function() {
          navigator.clipboard.writeText(p).then(function() {
            btn.textContent = 'Copied!';
            btn.classList.add('copied-btn');
            item.classList.add('copied');
            setTimeout(function() {
              btn.textContent = 'Copy';
              btn.classList.remove('copied-btn');
              item.classList.remove('copied');
            }, 2000);
          });
        };

        item.appendChild(txt);
        item.appendChild(btn);
        list.appendChild(item);
      })(pw);
    }
  };

  window.pwCopyMain = function() {
    if (!currentPw) return;
    navigator.clipboard.writeText(currentPw).then(function() {
      var box     = document.getElementById('pw-display-box');
      var confirm = document.getElementById('pw-copy-confirm');
      var copyBtn = document.getElementById('pw-copy-btn');

      box.classList.add('copied');
      confirm.classList.add('show');
      copyBtn.classList.add('copied-btn');
      copyBtn.innerHTML = '&#10003; Copied!';

      setTimeout(function() {
        box.classList.remove('copied');
        confirm.classList.remove('show');
        copyBtn.classList.remove('copied-btn');
        copyBtn.innerHTML = '&#128203; Copy';
      }, 2000);
    });
  };

  // Initialize
  document.getElementById('pw-passphrase-opts').style.display = 'none';
  document.getElementById('pw-multi-section').classList.remove('active');
  pwGenerate();
})();
</script>

</div>

---

## How to Create a Strong Password

A strong password is your first line of defense against unauthorized access to your accounts. The most important factor is length — a password of 16 or more characters is exponentially harder to crack than an 8-character one, even if the shorter one uses more special characters. Aim for a minimum of 12 characters for everyday accounts, and 20 or more for financial or email accounts that could unlock everything else if compromised.

Character variety matters almost as much as length. Mixing uppercase letters, lowercase letters, numbers, and symbols dramatically increases the number of possible combinations an attacker must try. A 16-character password using all four character types has over 2 septillion possible combinations — a number that would take modern hardware billions of years to exhaust through brute force. Avoid predictable substitutions like "P@ssw0rd" or "S3cur1ty," because attackers program these patterns into their cracking tools as a first step.

Uniqueness is non-negotiable. Every account you own should have its own distinct password. When a website suffers a data breach, attackers immediately test those stolen credentials across hundreds of other services in an attack called "credential stuffing." If you reuse passwords, a breach at one small site can cascade into a full identity compromise. A password manager lets you maintain hundreds of unique, randomly generated passwords without memorizing any of them — you only need to remember one strong master password.

## Password Security Tips

- **Use a password manager.** Tools like Bitwarden, 1Password, or KeePass store and autofill your passwords securely, so you never need to reuse or write them down.
- **Enable two-factor authentication (2FA).** Even if a password is stolen, 2FA — especially an authenticator app like Google Authenticator or Authy — blocks unauthorized access.
- **Never use personal information.** Birthdays, pet names, phone numbers, and addresses are discoverable through social media and are the first things attackers try.
- **Avoid dictionary words alone.** Single dictionary words can be cracked in seconds. If you want something memorable, use a passphrase of four or more random words (like this tool's passphrase mode).
- **Change passwords after a breach.** Check services like HaveIBeenPwned.com regularly, and update your password immediately if your email appears in a known data breach.
- **Use different passwords for email accounts.** Your email is a master key — if compromised, it allows password resets on every other service you own. Treat it with extra care.
- **Avoid typing passwords on public or shared computers.** Keyloggers and shoulder surfing are real threats in libraries, hotels, and internet cafes.
- **Keep your master password and recovery codes offline.** Write your password manager master password and 2FA backup codes on paper and store them somewhere physically secure, like a locked drawer.

## Related Tools

> Calculate percentages, discounts, and tips instantly → [Percentage Calculator](/tools/percentage-calculator/)

> Track your subscription costs and save money → [Subscription Cost Calculator](/tools/subscription-cost-calculator/)

> Stay focused with the Pomodoro Technique → [Pomodoro Timer](/tools/pomodoro-timer/)
