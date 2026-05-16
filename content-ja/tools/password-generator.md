---
title: "パスワード生成ツール｜安全な強力パスワードをワンクリック作成【無料】"
date: 2025-05-16
description: "無料のセキュアなパスワードジェネレーター。文字種・長さ・強度を自由にカスタマイズして安全なパスワードを即生成。ブラウザ内処理で安心。"
categories: ["無料ツール"]
slug: "password-generator"
ShowToc: false
cover:
  image: "/images/covers/password-generator-ja.png"
  alt: "パスワード生成ツール"
---

安全なパスワードをブラウザ内で即座に生成。入力内容はサーバーに一切送信されません。

<div id="pw-app-ja">

<style>
#pw-app-ja {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, "Segoe UI", sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
}
#pw-app-ja * { box-sizing: border-box; }

#pw-app-ja .pw-section {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 16px;
}

#pw-app-ja h3.pw-section-title {
  margin: 0 0 14px 0;
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
}

#pw-app-ja .pw-output-box {
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
#pw-app-ja .pw-output-box .pw-pass-text {
  font-family: "Courier New", Courier, monospace;
  font-size: 15px;
  word-break: break-all;
  flex: 1;
  color: #0f172a;
  line-height: 1.5;
}
#pw-app-ja .pw-copy-btn {
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
#pw-app-ja .pw-copy-btn:hover { background: #2563eb; }
#pw-app-ja .pw-copy-btn.pw-copied { background: #16a34a; }

#pw-app-ja .pw-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 4px;
}
#pw-app-ja .pw-btn-primary {
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
#pw-app-ja .pw-btn-primary:hover { background: #2563eb; }
#pw-app-ja .pw-btn-secondary {
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
#pw-app-ja .pw-btn-secondary:hover { background: #f1f5f9; border-color: #94a3b8; }

#pw-app-ja .pw-strength-wrap { margin-bottom: 16px; }
#pw-app-ja .pw-strength-label {
  font-size: 13px;
  font-weight: 600;
  margin-bottom: 5px;
  display: flex;
  justify-content: space-between;
}
#pw-app-ja .pw-strength-bar-bg {
  background: #e2e8f0;
  border-radius: 99px;
  height: 8px;
  overflow: hidden;
}
#pw-app-ja .pw-strength-bar {
  height: 8px;
  border-radius: 99px;
  transition: width 0.3s, background 0.3s;
  width: 0%;
}

#pw-app-ja .pw-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
#pw-app-ja .pw-row label {
  font-size: 14px;
  font-weight: 600;
  min-width: 80px;
  color: #374151;
}
#pw-app-ja input[type="range"] {
  flex: 1;
  accent-color: #3b82f6;
  cursor: pointer;
}
#pw-app-ja .pw-num-input {
  width: 62px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  padding: 5px 8px;
  font-size: 14px;
  text-align: center;
  color: #0f172a;
}
#pw-app-ja .pw-num-input:focus { outline: 2px solid #3b82f6; border-color: transparent; }

#pw-app-ja .pw-row-count {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
#pw-app-ja .pw-row-count label {
  font-size: 14px;
  font-weight: 600;
  min-width: 80px;
  color: #374151;
}

#pw-app-ja .pw-checks {
  display: flex;
  flex-wrap: wrap;
  gap: 10px 22px;
  margin-bottom: 14px;
}
#pw-app-ja .pw-check-item {
  display: flex;
  align-items: center;
  gap: 7px;
  font-size: 14px;
  cursor: pointer;
  user-select: none;
}
#pw-app-ja .pw-check-item input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #3b82f6;
  cursor: pointer;
}

#pw-app-ja .pw-exclude-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 6px;
}
#pw-app-ja .pw-exclude-row label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  white-space: nowrap;
}
#pw-app-ja .pw-exclude-input {
  flex: 1;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 13px;
  font-family: "Courier New", Courier, monospace;
  color: #0f172a;
}
#pw-app-ja .pw-exclude-input:focus { outline: 2px solid #3b82f6; border-color: transparent; }

#pw-app-ja .pw-mode-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 16px;
}
#pw-app-ja .pw-mode-tab {
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
#pw-app-ja .pw-mode-tab.pw-tab-active {
  background: #3b82f6;
  color: #fff;
  border-color: #3b82f6;
}
#pw-app-ja .pw-mode-tab:hover:not(.pw-tab-active) { background: #f1f5f9; }

#pw-app-ja .pw-history-list {
  list-style: none;
  padding: 0;
  margin: 0;
  max-height: 220px;
  overflow-y: auto;
}
#pw-app-ja .pw-history-list li {
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
#pw-app-ja .pw-history-list li:last-child { border-bottom: none; }
#pw-app-ja .pw-history-copy {
  flex-shrink: 0;
  background: none;
  border: 1px solid #cbd5e1;
  border-radius: 5px;
  padding: 3px 9px;
  font-size: 12px;
  cursor: pointer;
  color: #374151;
}
#pw-app-ja .pw-history-copy:hover { background: #f1f5f9; }
#pw-app-ja .pw-empty-history {
  font-size: 13px;
  color: #94a3b8;
  text-align: center;
  padding: 14px 0;
}

#pw-app-ja .pw-multi-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
#pw-app-ja .pw-multi-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 7px 0;
  border-bottom: 1px solid #e2e8f0;
  gap: 8px;
}
#pw-app-ja .pw-multi-list li:last-child { border-bottom: none; }
#pw-app-ja .pw-multi-list .pw-multi-text {
  font-family: "Courier New", Courier, monospace;
  font-size: 13px;
  word-break: break-all;
  color: #0f172a;
  flex: 1;
}

@media (max-width: 480px) {
  #pw-app-ja .pw-row { flex-wrap: wrap; }
  #pw-app-ja .pw-row label { min-width: 100%; margin-bottom: 2px; }
  #pw-app-ja .pw-section { padding: 16px; }
  #pw-app-ja .pw-mode-tab { font-size: 12px; padding: 8px 5px; }
}
</style>

<!-- モード切替 -->
<div class="pw-section">
  <h3 class="pw-section-title">モード</h3>
  <div class="pw-mode-tabs">
    <div class="pw-mode-tab pw-tab-active" onclick="pwjaSetMode('random',this)">ランダム</div>
    <div class="pw-mode-tab" onclick="pwjaSetMode('pronounceable',this)">発音しやすい</div>
    <div class="pw-mode-tab" onclick="pwjaSetMode('passphrase',this)">パスフレーズ</div>
  </div>

  <!-- ランダム / 発音しやすい オプション -->
  <div id="pwja-random-opts">
    <div class="pw-row">
      <label for="pwja-length-slider">文字数</label>
      <input type="range" id="pwja-length-slider" min="4" max="128" value="20" oninput="pwjaSyncLength(this.value)">
      <input type="number" class="pw-num-input" id="pwja-length-num" min="4" max="128" value="20" oninput="pwjaSyncLength(this.value)">
    </div>
    <div class="pw-checks">
      <label class="pw-check-item"><input type="checkbox" id="pwja-upper" checked onchange="pwjaGenerate()"> 大文字 (A-Z)</label>
      <label class="pw-check-item"><input type="checkbox" id="pwja-lower" checked onchange="pwjaGenerate()"> 小文字 (a-z)</label>
      <label class="pw-check-item"><input type="checkbox" id="pwja-nums" checked onchange="pwjaGenerate()"> 数字 (0-9)</label>
      <label class="pw-check-item"><input type="checkbox" id="pwja-syms" onchange="pwjaGenerate()"> 記号 (!@#$...)</label>
      <label class="pw-check-item"><input type="checkbox" id="pwja-noambig" onchange="pwjaGenerate()"> 紛らわしい文字を除外 (0/O, l/1/I)</label>
    </div>
    <div class="pw-exclude-row">
      <label for="pwja-exclude-chars">除外する文字:</label>
      <input type="text" class="pw-exclude-input" id="pwja-exclude-chars" placeholder="例: {}[]" oninput="pwjaGenerate()">
    </div>
  </div>

  <!-- パスフレーズ オプション -->
  <div id="pwja-passphrase-opts" style="display:none;">
    <div class="pw-row">
      <label for="pwja-word-count">単語数</label>
      <input type="range" id="pwja-word-count" min="2" max="10" value="4" oninput="pwjaSyncWords(this.value)">
      <input type="number" class="pw-num-input" id="pwja-word-count-num" min="2" max="10" value="4" oninput="pwjaSyncWords(this.value)">
    </div>
    <div class="pw-checks">
      <label class="pw-check-item"><input type="checkbox" id="pwja-pp-cap" checked onchange="pwjaGenerate()"> 先頭を大文字にする</label>
      <label class="pw-check-item"><input type="checkbox" id="pwja-pp-num" checked onchange="pwjaGenerate()"> 末尾に数字を追加</label>
    </div>
    <div class="pw-exclude-row">
      <label for="pwja-pp-sep">区切り文字:</label>
      <input type="text" class="pw-exclude-input" id="pwja-pp-sep" value="-" maxlength="5" style="max-width:80px;" oninput="pwjaGenerate()">
    </div>
  </div>

  <!-- 生成数 -->
  <div class="pw-row-count" style="margin-top:14px;">
    <label for="pwja-count">生成数</label>
    <input type="number" class="pw-num-input" id="pwja-count" min="1" max="20" value="1" oninput="pwjaGenerate()">
    <span style="font-size:13px;color:#64748b;">個まとめて生成 (最大20)</span>
  </div>
</div>

<!-- 出力 -->
<div class="pw-section">
  <h3 class="pw-section-title">生成結果</h3>

  <div class="pw-strength-wrap" id="pwja-strength-wrap">
    <div class="pw-strength-label">
      <span>強度</span>
      <span id="pwja-strength-text" style="color:#94a3b8;">--</span>
    </div>
    <div class="pw-strength-bar-bg">
      <div class="pw-strength-bar" id="pwja-strength-bar"></div>
    </div>
  </div>

  <div class="pw-output-box" id="pwja-single-out">
    <span class="pw-pass-text" id="pwja-pass-display">生成ボタンを押してください</span>
    <button class="pw-copy-btn" id="pwja-copy-main" onclick="pwjaCopyMain()">コピー</button>
  </div>

  <ul class="pw-multi-list" id="pwja-multi-out" style="display:none;"></ul>

  <div class="pw-actions">
    <button class="pw-btn-primary" onclick="pwjaGenerate()">&#x21bb; 生成する</button>
    <button class="pw-btn-secondary" id="pwja-copy-all-btn" onclick="pwjaCopyAll()" style="display:none;">すべてコピー</button>
  </div>
</div>

<!-- 履歴 -->
<div class="pw-section">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
    <h3 class="pw-section-title" style="margin:0;">生成履歴 <span style="font-weight:400;color:#94a3b8;font-size:11px;">(セッション内のみ保存)</span></h3>
    <button class="pw-btn-secondary" style="padding:5px 12px;font-size:12px;" onclick="pwjaClearHistory()">クリア</button>
  </div>
  <ul class="pw-history-list" id="pwja-history-list">
    <li><span class="pw-empty-history" style="width:100%;">まだパスワードが生成されていません。</span></li>
  </ul>
</div>

<script>
(function(){
  var _mode = 'random';
  var _hist = [];

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

  var _CON = 'bcdfghjklmnpqrstvwxyz';
  var _VOW = 'aeiou';

  function _ri(max) {
    var a = new Uint32Array(1);
    var lim = Math.floor(4294967296 / max) * max;
    do { crypto.getRandomValues(a); } while (a[0] >= lim);
    return a[0] % max;
  }

  function _cs() {
    var upper = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    var lower = 'abcdefghijklmnopqrstuvwxyz';
    var nums  = '0123456789';
    var syms  = '!@#$%^&*()-_=+[]{}|;:,.<>?';
    var ambig = '0Ol1I';
    var useUp = document.getElementById('pwja-upper').checked;
    var useLo = document.getElementById('pwja-lower').checked;
    var useNu = document.getElementById('pwja-nums').checked;
    var useSy = document.getElementById('pwja-syms').checked;
    var noAmb = document.getElementById('pwja-noambig').checked;
    var excl  = document.getElementById('pwja-exclude-chars').value;
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
    var cs = _cs();
    if (!cs) return '(文字種を1つ以上選択してください)';
    var out = '';
    for (var i=0; i<len; i++) out += cs[_ri(cs.length)];
    return out;
  }

  function _genPronounceable(len) {
    var useUp = document.getElementById('pwja-upper').checked;
    var noAmb = document.getElementById('pwja-noambig').checked;
    var excl  = document.getElementById('pwja-exclude-chars').value;
    var con = noAmb ? _CON.replace(/l/g,'') : _CON;
    var vow = _VOW;
    var out = '';
    var useC = true;
    for (var i=0; i<len; i++) {
      var pool = useC ? con : vow;
      var ch = pool[_ri(pool.length)];
      if (useUp && _ri(4)===0) ch = ch.toUpperCase();
      out += ch;
      useC = !useC;
    }
    if (excl) {
      var fixed='';
      for(var j=0;j<out.length;j++){
        if(excl.indexOf(out[j])===-1){ fixed+=out[j]; }
        else { var p=(j%2===0)?con:vow; fixed+=p[_ri(p.length)]; }
      }
      out=fixed;
    }
    return out;
  }

  function _genPassphrase() {
    var cnt = Math.min(10,Math.max(2,parseInt(document.getElementById('pwja-word-count').value)||4));
    var cap = document.getElementById('pwja-pp-cap').checked;
    var num = document.getElementById('pwja-pp-num').checked;
    var sep = document.getElementById('pwja-pp-sep').value;
    var ws = [];
    for (var i=0; i<cnt; i++) {
      var w = _WORDS[_ri(_WORDS.length)];
      if (cap) w = w.charAt(0).toUpperCase()+w.slice(1);
      ws.push(w);
    }
    var r = ws.join(sep);
    if (num) r += sep + (_ri(90)+10);
    return r;
  }

  function _genOne() {
    var len = parseInt(document.getElementById('pwja-length-slider').value)||20;
    if (_mode==='random')        return _genRandom(len);
    if (_mode==='pronounceable') return _genPronounceable(len);
    if (_mode==='passphrase')    return _genPassphrase();
    return '';
  }

  function _entropy(pass) {
    var cs = _cs();
    var pool = cs ? cs.length : 26;
    return pass.length * Math.log2(pool > 1 ? pool : 2);
  }

  function _ppEntropy(pass) {
    var sep = document.getElementById('pwja-pp-sep').value || '-';
    var sepE = sep.replace(/[-[\]{}()*+?.,\\^$|#\s]/g,'\\$&');
    var wc = (pass.match(new RegExp('['+sepE+']','g'))||[]).length + 1;
    return wc * Math.log2(_WORDS.length);
  }

  function _strengthInfo(bits) {
    if (bits < 28)  return {label:'非常に弱い', pct:10,  color:'#ef4444'};
    if (bits < 36)  return {label:'弱い',       pct:25,  color:'#f97316'};
    if (bits < 60)  return {label:'普通',        pct:50,  color:'#eab308'};
    if (bits < 80)  return {label:'強い',        pct:72,  color:'#22c55e'};
    if (bits < 100) return {label:'とても強い',  pct:88,  color:'#16a34a'};
    return               {label:'非常に強い',  pct:100, color:'#15803d'};
  }

  function _updateStrength(pass) {
    var bits = (_mode==='passphrase') ? _ppEntropy(pass) : _entropy(pass);
    var info = _strengthInfo(bits);
    document.getElementById('pwja-strength-text').textContent = info.label + ' (~'+Math.round(bits)+' bits)';
    document.getElementById('pwja-strength-text').style.color = info.color;
    document.getElementById('pwja-strength-bar').style.width = info.pct+'%';
    document.getElementById('pwja-strength-bar').style.background = info.color;
  }

  function _addHistory(passwords) {
    for (var i=0; i<passwords.length; i++) _hist.unshift(passwords[i]);
    if (_hist.length>10) _hist = _hist.slice(0,10);
    _renderHistory();
  }

  function _renderHistory() {
    var ul = document.getElementById('pwja-history-list');
    ul.innerHTML = '';
    if (_hist.length===0) {
      ul.innerHTML = '<li><span class="pw-empty-history" style="width:100%;">まだパスワードが生成されていません。</span></li>';
      return;
    }
    _hist.forEach(function(p) {
      var li=document.createElement('li');
      var sp=document.createElement('span'); sp.textContent=p;
      var btn=document.createElement('button');
      btn.className='pw-history-copy'; btn.textContent='コピー';
      (function(pass,b){ b.onclick=function(){ _clip(pass); b.textContent='コピー済!'; setTimeout(function(){ b.textContent='コピー'; },1500); }; })(p,btn);
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

  window.pwjaGenerate = function() {
    var count = Math.min(20,Math.max(1,parseInt(document.getElementById('pwja-count').value)||1));
    var passwords = [];
    for (var i=0; i<count; i++) passwords.push(_genOne());

    var singleOut    = document.getElementById('pwja-single-out');
    var multiOut     = document.getElementById('pwja-multi-out');
    var copyAllBtn   = document.getElementById('pwja-copy-all-btn');
    var strengthWrap = document.getElementById('pwja-strength-wrap');

    if (count===1) {
      document.getElementById('pwja-pass-display').textContent = passwords[0];
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
        var li=document.createElement('li');
        var sp=document.createElement('span'); sp.className='pw-multi-text'; sp.textContent=p;
        var btn=document.createElement('button');
        btn.className='pw-copy-btn'; btn.textContent='コピー';
        btn.style.fontSize='12px'; btn.style.padding='5px 12px';
        (function(pass,b){ b.onclick=function(){ _clip(pass); b.textContent='コピー済!'; b.classList.add('pw-copied'); setTimeout(function(){ b.textContent='コピー'; b.classList.remove('pw-copied'); },1500); }; })(p,btn);
        li.appendChild(sp); li.appendChild(btn); multiOut.appendChild(li);
      });
    }
    _addHistory(passwords);
  };

  window.pwjaCopyMain = function() {
    var text = document.getElementById('pwja-pass-display').textContent;
    if (!text || text==='生成ボタンを押してください') return;
    _clip(text);
    var btn = document.getElementById('pwja-copy-main');
    btn.textContent='コピー済!'; btn.classList.add('pw-copied');
    setTimeout(function(){ btn.textContent='コピー'; btn.classList.remove('pw-copied'); },1500);
  };

  window.pwjaCopyAll = function() {
    var items = document.querySelectorAll('#pwja-multi-out .pw-multi-text');
    var all = Array.prototype.slice.call(items).map(function(el){ return el.textContent; }).join('\n');
    _clip(all);
    var btn = document.getElementById('pwja-copy-all-btn');
    btn.textContent='コピー完了!';
    setTimeout(function(){ btn.textContent='すべてコピー'; },1500);
  };

  window.pwjaClearHistory = function() { _hist=[]; _renderHistory(); };

  window.pwjaSyncLength = function(val) {
    var v = Math.min(128,Math.max(4,parseInt(val)||4));
    document.getElementById('pwja-length-slider').value = v;
    document.getElementById('pwja-length-num').value    = v;
    pwjaGenerate();
  };

  window.pwjaSyncWords = function(val) {
    var v = Math.min(10,Math.max(2,parseInt(val)||4));
    document.getElementById('pwja-word-count').value     = v;
    document.getElementById('pwja-word-count-num').value = v;
    pwjaGenerate();
  };

  window.pwjaSetMode = function(mode, el) {
    _mode = mode;
    var tabs = document.querySelectorAll('#pw-app-ja .pw-mode-tab');
    for (var i=0; i<tabs.length; i++) tabs[i].classList.remove('pw-tab-active');
    el.classList.add('pw-tab-active');
    var isPhrase = (mode==='passphrase');
    document.getElementById('pwja-random-opts').style.display     = isPhrase ? 'none'  : 'block';
    document.getElementById('pwja-passphrase-opts').style.display = isPhrase ? 'block' : 'none';
    pwjaGenerate();
  };

  pwjaGenerate();
})();
</script>

</div>

<div class="pw-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">アカウント管理の経費もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、SaaSツールのサブスク費用も経費として一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

## パスワードの仕組みと安全性

パスワードはすべて **Web Crypto API**（`crypto.getRandomValues()`）を使ってブラウザ内で生成されます。暗号学的に安全な乱数を使用しており、生成したパスワードはサーバーに一切送信されません。

**エントロピー**はパスワードの予測困難さを表す指標です。計算式は `文字数 x log2(文字種の数)` です。全文字種を使った20文字のパスワードは約120ビットのエントロピーを持ち、現在のコンピュータでは事実上解読不可能です。

### モードの使い分け

| モード | 向いている用途 |
|---|---|
| ランダム | 最高のセキュリティ。パスワードマネージャーと組み合わせて使用 |
| 発音しやすい | 口頭で伝えやすい。子音・母音を交互に配置 |
| パスフレーズ | 覚えやすく高エントロピー。単語の組み合わせで構成 |

### 安全なパスワードのヒント

- 一般的なアカウントは16文字以上、重要なアカウントは24文字以上を推奨します。
- ランダムモードでは記号を有効にするとエントロピーが最大になります。
- 記憶が必要なパスワードにはパスフレーズモードが最適です。
- 同じパスワードを複数のサービスで使い回さないでください。パスワードマネージャーで管理しましょう。
- 「紛らわしい文字を除外」オプションは、`0`/`O` や `l`/`1`/`I` の混同を防ぎます。

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

> ハッシュを生成 → [ハッシュ生成ツール](/ja/tools/hash-generator/)

> テキストのエンコード/デコード → [万能エンコーダー/デコーダー](/ja/tools/encoder-decoder/)

## 関連記事

- [無料で使えるAIツールおすすめ15選【2026年版・目的別に厳選】](/ja/posts/無料-ai-ツール-おすすめ/)
- [VPN おすすめ2026年版！用途別に比較【初心者向けガイド】](/ja/posts/vpn-osusume-2026/)
