---
title: "Password Generator"
date: 2025-05-16
description: "Free secure password generator. Create strong, random passwords with customizable length, character types, and strength indicator — all processed in your browser."
categories: ["Free Tools"]
slug: "password-generator"
ShowToc: false
cover:
  image: "/images/covers/password-generator.png"
  alt: "Password Generator"
---

Generate strong, random passwords instantly — all processing happens in your browser. Nothing is sent to any server.

<div id="pw-app">

<style>
#pw-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
}
#pw-app * { box-sizing: border-box; }

#pw-app .pw-section {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 16px;
}

#pw-app h3.pw-section-title {
  margin: 0 0 14px 0;
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
}

#pw-app .pw-output-box {
  background: #fff;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  padding: 14px 16px;
  margin-bottom: 10px;
  min-height: 52px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}
#pw-app .pw-output-box .pw-pass-text {
  font-family: "Courier New", Courier, monospace;
  font-size: 15px;
  word-break: break-all;
  flex: 1;
  color: #0f172a;
  line-height: 1.5;
}
#pw-app .pw-copy-btn {
  flex-shrink: 0;
  background: #3b82f6;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 6px 14px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#pw-app .pw-copy-btn:hover { background: #2563eb; }
#pw-app .pw-copy-btn.pw-copied { background: #16a34a; }

#pw-app .pw-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 4px;
}
#pw-app .pw-btn-primary {
  background: #3b82f6;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 11px 22px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
  flex: 1;
  min-width: 150px;
}
#pw-app .pw-btn-primary:hover { background: #2563eb; }
#pw-app .pw-btn-secondary {
  background: #fff;
  color: #374151;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  padding: 11px 18px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
}
#pw-app .pw-btn-secondary:hover { background: #f1f5f9; border-color: #94a3b8; }

#pw-app .pw-strength-wrap { margin-bottom: 16px; }
#pw-app .pw-strength-label {
  font-size: 13px;
  font-weight: 600;
  margin-bottom: 5px;
  display: flex;
  justify-content: space-between;
}
#pw-app .pw-strength-bar-bg {
  background: #e2e8f0;
  border-radius: 99px;
  height: 8px;
  overflow: hidden;
}
#pw-app .pw-strength-bar {
  height: 8px;
  border-radius: 99px;
  transition: width 0.3s, background 0.3s;
  width: 0%;
}

#pw-app .pw-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
#pw-app .pw-row label {
  font-size: 14px;
  font-weight: 600;
  min-width: 110px;
  color: #374151;
}
#pw-app input[type="range"] {
  flex: 1;
  accent-color: #3b82f6;
  cursor: pointer;
}
#pw-app .pw-num-input {
  width: 62px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  padding: 5px 8px;
  font-size: 14px;
  text-align: center;
  color: #0f172a;
}
#pw-app .pw-num-input:focus { outline: 2px solid #3b82f6; border-color: transparent; }

#pw-app .pw-row-count {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
#pw-app .pw-row-count label {
  font-size: 14px;
  font-weight: 600;
  min-width: 110px;
  color: #374151;
}

#pw-app .pw-checks {
  display: flex;
  flex-wrap: wrap;
  gap: 10px 22px;
  margin-bottom: 14px;
}
#pw-app .pw-check-item {
  display: flex;
  align-items: center;
  gap: 7px;
  font-size: 14px;
  cursor: pointer;
  user-select: none;
}
#pw-app .pw-check-item input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #3b82f6;
  cursor: pointer;
}

#pw-app .pw-exclude-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 6px;
}
#pw-app .pw-exclude-row label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  white-space: nowrap;
}
#pw-app .pw-exclude-input {
  flex: 1;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 13px;
  font-family: "Courier New", Courier, monospace;
  color: #0f172a;
}
#pw-app .pw-exclude-input:focus { outline: 2px solid #3b82f6; border-color: transparent; }

#pw-app .pw-mode-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 16px;
}
#pw-app .pw-mode-tab {
  flex: 1;
  text-align: center;
  padding: 9px 10px;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  background: #fff;
  color: #374151;
  transition: all 0.15s;
}
#pw-app .pw-mode-tab.pw-tab-active {
  background: #3b82f6;
  color: #fff;
  border-color: #3b82f6;
}
#pw-app .pw-mode-tab:hover:not(.pw-tab-active) { background: #f1f5f9; }

#pw-app .pw-history-list {
  list-style: none;
  padding: 0;
  margin: 0;
  max-height: 220px;
  overflow-y: auto;
}
#pw-app .pw-history-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 7px 0;
  border-bottom: 1px solid #e2e8f0;
  font-family: "Courier New", Courier, monospace;
  font-size: 13px;
  word-break: break-all;
  gap: 8px;
  color: #0f172a;
}
#pw-app .pw-history-list li:last-child { border-bottom: none; }
#pw-app .pw-history-copy {
  flex-shrink: 0;
  background: none;
  border: 1px solid #cbd5e1;
  border-radius: 5px;
  padding: 3px 9px;
  font-size: 12px;
  cursor: pointer;
  color: #374151;
}
#pw-app .pw-history-copy:hover { background: #f1f5f9; }
#pw-app .pw-empty-history {
  font-size: 13px;
  color: #94a3b8;
  text-align: center;
  padding: 14px 0;
}

#pw-app .pw-multi-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
#pw-app .pw-multi-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 7px 0;
  border-bottom: 1px solid #e2e8f0;
  gap: 8px;
}
#pw-app .pw-multi-list li:last-child { border-bottom: none; }
#pw-app .pw-multi-list .pw-multi-text {
  font-family: "Courier New", Courier, monospace;
  font-size: 13px;
  word-break: break-all;
  color: #0f172a;
  flex: 1;
}

@media (max-width: 480px) {
  #pw-app .pw-row { flex-wrap: wrap; }
  #pw-app .pw-row label { min-width: 100%; margin-bottom: 2px; }
  #pw-app .pw-section { padding: 16px; }
  #pw-app .pw-mode-tab { font-size: 12px; padding: 8px 6px; }
}
</style>

<!-- Mode selector -->
<div class="pw-section">
  <h3 class="pw-section-title">Mode</h3>
  <div class="pw-mode-tabs">
    <div class="pw-mode-tab pw-tab-active" onclick="pwSetMode('random',this)">Random</div>
    <div class="pw-mode-tab" onclick="pwSetMode('pronounceable',this)">Pronounceable</div>
    <div class="pw-mode-tab" onclick="pwSetMode('passphrase',this)">Passphrase</div>
  </div>

  <!-- Random / Pronounceable options -->
  <div id="pw-random-opts">
    <div class="pw-row">
      <label for="pw-length-slider">Length</label>
      <input type="range" id="pw-length-slider" min="4" max="128" value="20" oninput="pwSyncLength(this.value)">
      <input type="number" class="pw-num-input" id="pw-length-num" min="4" max="128" value="20" oninput="pwSyncLength(this.value)">
    </div>
    <div class="pw-checks">
      <label class="pw-check-item"><input type="checkbox" id="pw-upper" checked onchange="pwGenerate()"> Uppercase (A-Z)</label>
      <label class="pw-check-item"><input type="checkbox" id="pw-lower" checked onchange="pwGenerate()"> Lowercase (a-z)</label>
      <label class="pw-check-item"><input type="checkbox" id="pw-nums" checked onchange="pwGenerate()"> Numbers (0-9)</label>
      <label class="pw-check-item"><input type="checkbox" id="pw-syms" onchange="pwGenerate()"> Symbols (!@#$...)</label>
      <label class="pw-check-item"><input type="checkbox" id="pw-noambig" onchange="pwGenerate()"> Exclude ambiguous (0/O, l/1/I)</label>
    </div>
    <div class="pw-exclude-row">
      <label for="pw-exclude-chars">Exclude chars:</label>
      <input type="text" class="pw-exclude-input" id="pw-exclude-chars" placeholder="e.g. {}[]" oninput="pwGenerate()">
    </div>
  </div>

  <!-- Passphrase options -->
  <div id="pw-passphrase-opts" style="display:none;">
    <div class="pw-row">
      <label for="pw-word-count">Word count</label>
      <input type="range" id="pw-word-count" min="2" max="10" value="4" oninput="pwSyncWords(this.value)">
      <input type="number" class="pw-num-input" id="pw-word-count-num" min="2" max="10" value="4" oninput="pwSyncWords(this.value)">
    </div>
    <div class="pw-checks">
      <label class="pw-check-item"><input type="checkbox" id="pw-pp-cap" checked onchange="pwGenerate()"> Capitalize words</label>
      <label class="pw-check-item"><input type="checkbox" id="pw-pp-num" checked onchange="pwGenerate()"> Append number</label>
    </div>
    <div class="pw-exclude-row">
      <label for="pw-pp-sep">Separator:</label>
      <input type="text" class="pw-exclude-input" id="pw-pp-sep" value="-" maxlength="5" style="max-width:80px;" oninput="pwGenerate()">
    </div>
  </div>

  <!-- Count -->
  <div class="pw-row-count" style="margin-top:14px;">
    <label for="pw-count">Generate</label>
    <input type="number" class="pw-num-input" id="pw-count" min="1" max="20" value="1" oninput="pwGenerate()">
    <span style="font-size:13px;color:#64748b;">password(s) at once (max 20)</span>
  </div>
</div>

<!-- Output -->
<div class="pw-section">
  <h3 class="pw-section-title">Output</h3>

  <div class="pw-strength-wrap" id="pw-strength-wrap">
    <div class="pw-strength-label">
      <span>Strength</span>
      <span id="pw-strength-text" style="color:#94a3b8;">--</span>
    </div>
    <div class="pw-strength-bar-bg">
      <div class="pw-strength-bar" id="pw-strength-bar"></div>
    </div>
  </div>

  <div class="pw-output-box" id="pw-single-out">
    <span class="pw-pass-text" id="pw-pass-display">Click Generate</span>
    <button class="pw-copy-btn" id="pw-copy-main" onclick="pwCopyMain()">Copy</button>
  </div>

  <ul class="pw-multi-list" id="pw-multi-out" style="display:none;"></ul>

  <div class="pw-actions">
    <button class="pw-btn-primary" onclick="pwGenerate()">&#x21bb; Generate</button>
    <button class="pw-btn-secondary" id="pw-copy-all-btn" onclick="pwCopyAll()" style="display:none;">Copy All</button>
  </div>
</div>

<!-- History -->
<div class="pw-section">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
    <h3 class="pw-section-title" style="margin:0;">History <span style="font-weight:400;color:#94a3b8;font-size:11px;">(session only)</span></h3>
    <button class="pw-btn-secondary" style="padding:5px 12px;font-size:12px;" onclick="pwClearHistory()">Clear</button>
  </div>
  <ul class="pw-history-list" id="pw-history-list">
    <li><span class="pw-empty-history" style="width:100%;">No passwords generated yet.</span></li>
  </ul>
</div>

<script>
(function(){
  var _pwMode = 'random';
  var _pwHistory = [];

  var _WORDS = [
    "apple","brave","cloud","dance","eagle","flame","grace","house","ivory","juice",
    "kneel","lemon","mango","night","ocean","piano","queen","river","stone","tiger",
    "ultra","viper","wheat","xenon","yacht","zebra","amber","blaze","coral","drift",
    "ember","frost","globe","haste","inlet","joker","karma","laser","maple","novel",
    "olive","pearl","quill","ridge","solar","tidal","umbra","vault","waltz","pixel",
    "azure","boost","crisp","delta","epoch","flint","grove","hinge","irony","jazzy",
    "knife","lunar","moose","nerve","orbit","prism","quartz","robin","scout","torch",
    "unity","visor","woven","oxide","yield","zonal","alpha","bench","cedar","depot",
    "easel","field","glare","hedge","index","jelly","kinky","lotus","metal","noble",
    "ozone","plumb","quota","ranch","swift","trout","urban","vivid","water","xylem",
    "yearn","zippy","alert","blunt","curve","dense","erupt","fluke","groan","hyper",
    "image","jewel","knack","lofty","micro","nifty","opera","plain","quiet","risky",
    "spite","tango","usher","vigor","wider","extra","young","zesty","agile","brisk",
    "crimp","dwell","elbow","finch","guava","hyena","infer","jaunt","kudos","lyric",
    "merch","navel","onset","patch","quirk","ruddy","sleek","taunt","unfold","venom",
    "wrath","adept","brine","clamp","drive","elegy","forge","glyph","hatch","intro",
    "jumbo","latch","mirth","nudge","optic","plaid","quest","radar","snowy","tapir",
    "untie","vocal","whirl","exert","zilch","amber","birch","candy","daisy","denim",
    "fable","gauge","hazel","kiosk","lilac","melon","nicer","onion","pansy","racer",
    "rivet","swamp","vivid","windy","boxer","crane","floss","graze","kneel","primo"
  ];

  var _CONSONANTS = 'bcdfghjklmnpqrstvwxyz';
  var _VOWELS     = 'aeiou';

  function _randInt(max) {
    var a = new Uint32Array(1);
    var lim = Math.floor(4294967296 / max) * max;
    do { crypto.getRandomValues(a); } while (a[0] >= lim);
    return a[0] % max;
  }

  function _charset() {
    var upper = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    var lower = 'abcdefghijklmnopqrstuvwxyz';
    var nums  = '0123456789';
    var syms  = '!@#$%^&*()-_=+[]{}|;:,.<>?';
    var ambig = '0Ol1I';
    var useUp = document.getElementById('pw-upper').checked;
    var useLo = document.getElementById('pw-lower').checked;
    var useNu = document.getElementById('pw-nums').checked;
    var useSy = document.getElementById('pw-syms').checked;
    var noAmb = document.getElementById('pw-noambig').checked;
    var excl  = document.getElementById('pw-exclude-chars').value;
    var cs = '';
    if (useUp) cs += upper;
    if (useLo) cs += lower;
    if (useNu) cs += nums;
    if (useSy) cs += syms;
    if (noAmb) { var t=''; for(var i=0;i<cs.length;i++) if(ambig.indexOf(cs[i])===-1) t+=cs[i]; cs=t; }
    if (excl)  { var t=''; for(var i=0;i<cs.length;i++) if(excl.indexOf(cs[i])===-1) t+=cs[i]; cs=t; }
    return cs;
  }

  function _genRandom(len) {
    var cs = _charset();
    if (!cs) return '(select at least one character type)';
    var out = '';
    for (var i=0; i<len; i++) out += cs[_randInt(cs.length)];
    return out;
  }

  function _genPronounceable(len) {
    var useUp = document.getElementById('pw-upper').checked;
    var noAmb = document.getElementById('pw-noambig').checked;
    var excl  = document.getElementById('pw-exclude-chars').value;
    var con = noAmb ? _CONSONANTS.replace(/l/g,'') : _CONSONANTS;
    var vow = _VOWELS;
    var out = '';
    var useC = true;
    for (var i=0; i<len; i++) {
      var pool = useC ? con : vow;
      var ch = pool[_randInt(pool.length)];
      if (useUp && _randInt(4)===0) ch = ch.toUpperCase();
      out += ch;
      useC = !useC;
    }
    if (excl) {
      var fixed = '';
      for (var j=0; j<out.length; j++) {
        if (excl.indexOf(out[j])===-1) { fixed += out[j]; }
        else { var p=(j%2===0)?con:vow; fixed += p[_randInt(p.length)]; }
      }
      out = fixed;
    }
    return out;
  }

  function _genPassphrase() {
    var cnt = Math.min(10,Math.max(2,parseInt(document.getElementById('pw-word-count').value)||4));
    var cap = document.getElementById('pw-pp-cap').checked;
    var num = document.getElementById('pw-pp-num').checked;
    var sep = document.getElementById('pw-pp-sep').value;
    var ws = [];
    for (var i=0; i<cnt; i++) {
      var w = _WORDS[_randInt(_WORDS.length)];
      if (cap) w = w.charAt(0).toUpperCase()+w.slice(1);
      ws.push(w);
    }
    var r = ws.join(sep);
    if (num) r += sep + (_randInt(90)+10);
    return r;
  }

  function _genOne() {
    var len = parseInt(document.getElementById('pw-length-slider').value)||20;
    if (_pwMode==='random')       return _genRandom(len);
    if (_pwMode==='pronounceable') return _genPronounceable(len);
    if (_pwMode==='passphrase')    return _genPassphrase();
    return '';
  }

  function _entropy(pass) {
    var cs = _charset();
    var pool = cs ? cs.length : 26;
    return pass.length * Math.log2(pool > 1 ? pool : 2);
  }

  function _strengthInfo(bits) {
    if (bits < 28)  return {label:'Very Weak',  pct:10,  color:'#ef4444'};
    if (bits < 36)  return {label:'Weak',        pct:25,  color:'#f97316'};
    if (bits < 60)  return {label:'Fair',         pct:50,  color:'#eab308'};
    if (bits < 80)  return {label:'Good',         pct:72,  color:'#22c55e'};
    if (bits < 100) return {label:'Strong',       pct:88,  color:'#16a34a'};
    return               {label:'Very Strong',  pct:100, color:'#15803d'};
  }

  function _passphraseEntropy(pass) {
    var sep = document.getElementById('pw-pp-sep').value || '-';
    var sepE = sep.replace(/[-[\]{}()*+?.,\\^$|#\s]/g,'\\$&');
    var wc = (pass.match(new RegExp('['+sepE+']','g'))||[]).length + 1;
    return wc * Math.log2(_WORDS.length);
  }

  function _updateStrength(pass) {
    var bits = (_pwMode==='passphrase') ? _passphraseEntropy(pass) : _entropy(pass);
    var info = _strengthInfo(bits);
    document.getElementById('pw-strength-text').textContent = info.label + ' (~'+Math.round(bits)+' bits)';
    document.getElementById('pw-strength-text').style.color = info.color;
    document.getElementById('pw-strength-bar').style.width = info.pct+'%';
    document.getElementById('pw-strength-bar').style.background = info.color;
  }

  function _addHistory(passwords) {
    for (var i=0; i<passwords.length; i++) _pwHistory.unshift(passwords[i]);
    if (_pwHistory.length>10) _pwHistory = _pwHistory.slice(0,10);
    _renderHistory();
  }

  function _renderHistory() {
    var ul = document.getElementById('pw-history-list');
    ul.innerHTML = '';
    if (_pwHistory.length===0) {
      ul.innerHTML = '<li><span class="pw-empty-history" style="width:100%;">No passwords generated yet.</span></li>';
      return;
    }
    _pwHistory.forEach(function(p) {
      var li = document.createElement('li');
      var sp = document.createElement('span'); sp.textContent = p;
      var btn = document.createElement('button');
      btn.className = 'pw-history-copy'; btn.textContent = 'Copy';
      (function(pass,b){ b.onclick=function(){ _clip(pass); b.textContent='Copied!'; setTimeout(function(){ b.textContent='Copy'; },1500); }; })(p,btn);
      li.appendChild(sp); li.appendChild(btn); ul.appendChild(li);
    });
  }

  function _clip(text) {
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).catch(function(){});
    } else {
      var ta=document.createElement('textarea'); ta.value=text;
      ta.style.position='fixed'; ta.style.opacity='0';
      document.body.appendChild(ta); ta.select();
      document.execCommand('copy'); document.body.removeChild(ta);
    }
  }

  window.pwGenerate = function() {
    var count = Math.min(20,Math.max(1,parseInt(document.getElementById('pw-count').value)||1));
    var passwords = [];
    for (var i=0; i<count; i++) passwords.push(_genOne());

    var singleOut    = document.getElementById('pw-single-out');
    var multiOut     = document.getElementById('pw-multi-out');
    var copyAllBtn   = document.getElementById('pw-copy-all-btn');
    var strengthWrap = document.getElementById('pw-strength-wrap');

    if (count===1) {
      document.getElementById('pw-pass-display').textContent = passwords[0];
      singleOut.style.display    = 'flex';
      multiOut.style.display     = 'none';
      copyAllBtn.style.display   = 'none';
      strengthWrap.style.display = 'block';
      _updateStrength(passwords[0]);
    } else {
      singleOut.style.display    = 'none';
      strengthWrap.style.display = 'none';
      multiOut.style.display     = 'block';
      copyAllBtn.style.display   = 'inline-block';
      multiOut.innerHTML = '';
      passwords.forEach(function(p) {
        var li = document.createElement('li');
        var sp = document.createElement('span'); sp.className='pw-multi-text'; sp.textContent=p;
        var btn = document.createElement('button');
        btn.className='pw-copy-btn'; btn.textContent='Copy';
        btn.style.fontSize='12px'; btn.style.padding='5px 12px';
        (function(pass,b){ b.onclick=function(){ _clip(pass); b.textContent='Copied!'; b.classList.add('pw-copied'); setTimeout(function(){ b.textContent='Copy'; b.classList.remove('pw-copied'); },1500); }; })(p,btn);
        li.appendChild(sp); li.appendChild(btn); multiOut.appendChild(li);
      });
    }
    _addHistory(passwords);
  };

  window.pwCopyMain = function() {
    var text = document.getElementById('pw-pass-display').textContent;
    if (!text || text==='Click Generate') return;
    _clip(text);
    var btn = document.getElementById('pw-copy-main');
    btn.textContent='Copied!'; btn.classList.add('pw-copied');
    setTimeout(function(){ btn.textContent='Copy'; btn.classList.remove('pw-copied'); },1500);
  };

  window.pwCopyAll = function() {
    var items = document.querySelectorAll('#pw-multi-out .pw-multi-text');
    var all = Array.prototype.slice.call(items).map(function(el){ return el.textContent; }).join('\n');
    _clip(all);
    var btn = document.getElementById('pw-copy-all-btn');
    btn.textContent='Copied All!';
    setTimeout(function(){ btn.textContent='Copy All'; },1500);
  };

  window.pwClearHistory = function() { _pwHistory=[]; _renderHistory(); };

  window.pwSyncLength = function(val) {
    var v = Math.min(128,Math.max(4,parseInt(val)||4));
    document.getElementById('pw-length-slider').value = v;
    document.getElementById('pw-length-num').value    = v;
    pwGenerate();
  };

  window.pwSyncWords = function(val) {
    var v = Math.min(10,Math.max(2,parseInt(val)||4));
    document.getElementById('pw-word-count').value     = v;
    document.getElementById('pw-word-count-num').value = v;
    pwGenerate();
  };

  window.pwSetMode = function(mode, el) {
    _pwMode = mode;
    var tabs = document.querySelectorAll('#pw-app .pw-mode-tab');
    for (var i=0; i<tabs.length; i++) tabs[i].classList.remove('pw-tab-active');
    el.classList.add('pw-tab-active');
    var isPhrase = (mode==='passphrase');
    document.getElementById('pw-random-opts').style.display     = isPhrase ? 'none'  : 'block';
    document.getElementById('pw-passphrase-opts').style.display = isPhrase ? 'block' : 'none';
    pwGenerate();
  };

  pwGenerate();
})();
</script>

</div>

---

## How It Works

Passwords are generated entirely in your browser using the **Web Crypto API** (`crypto.getRandomValues()`), which produces cryptographically secure random values. No data is ever sent to a server.

**Entropy** measures how unpredictable a password is. The calculation is `length x log2(charset size)`. A 20-character password using all character types reaches approximately 120 bits of entropy — well beyond brute-force reach with current hardware.

### Mode Guide

| Mode | Best for |
|---|---|
| Random | Maximum security; use with a password manager |
| Pronounceable | Easier to type aloud; consonant-vowel alternation |
| Passphrase | Memorable; high entropy from word combinations |

### Tips for Strong Passwords

- Use 16+ characters for everyday accounts; 24+ for critical ones.
- Enable symbols to maximize entropy in Random mode.
- Use Passphrase mode for passwords you need to remember.
- Never reuse passwords across sites — use a password manager.
- The "Exclude ambiguous" option avoids confusion between `0`/`O` and `l`/`1`/`I` when reading passwords aloud.

---

> Generate hashes → [Hash Generator](/tools/hash-generator/)

> Encode/decode text → [Universal Encoder/Decoder](/tools/encoder-decoder/)

## Related Articles

- [Best AI Tools for Small Business 2026: The Complete Roundup](/posts/best-ai-tools-small-business-2026/)
- [Best Password Managers 2026: Secure Every Account for $3/Month](/posts/best-password-managers-2026/)
- [Best VPN Services 2026: Privacy, Streaming & Remote Work](/posts/best-vpn-services-2026/)
