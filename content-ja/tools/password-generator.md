---
title: "パスワード生成ツール - 安全なランダムパスワード作成"
date: 2025-05-16
description: "安全で強力なランダムパスワードを無料で生成。文字数・文字種をカスタマイズ。パスワード強度チェック機能付き。"
categories: ["無料ツール"]
tags: ["パスワード", "セキュリティ", "生成ツール", "プライバシー", "オンラインツール"]
slug: "password-generator"
aliases: ["/ja/tools/random-password/", "/ja/tools/secure-password/"]
cover:
  image: "/images/covers/password-generator-ja.png"
  alt: "パスワード生成ツール"
ShowToc: false
---

<div id="password-app">

<style>
#password-app {
  font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  max-width: 760px;
  margin: 0 auto;
  color: #e2e8f0;
}

#password-app * {
  box-sizing: border-box;
}

.pw-card {
  background: #1e3a5f;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 20px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.3);
}

.pw-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #93c5fd;
  margin: 0 0 16px 0;
  letter-spacing: 0.02em;
}

/* パスワード表示エリア */
.pw-display-wrap {
  position: relative;
  background: #0f2240;
  border: 2px solid #3b82f6;
  border-radius: 8px;
  padding: 18px 120px 18px 18px;
  min-height: 64px;
  cursor: pointer;
  transition: border-color 0.2s, background 0.2s;
}
.pw-display-wrap:hover {
  border-color: #60a5fa;
  background: #132b50;
}
.pw-display-wrap.copied {
  border-color: #22c55e;
  background: #052e1a;
}

#pw-output {
  font-family: 'Courier New', Courier, monospace;
  font-size: 1.3rem;
  word-break: break-all;
  color: #f0f9ff;
  line-height: 1.5;
  user-select: all;
}

.pw-copy-inline {
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%);
  background: #3b82f6;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 8px 14px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  white-space: nowrap;
}
.pw-copy-inline:hover { background: #2563eb; }
.pw-copy-inline:active { transform: translateY(-50%) scale(0.95); }
.pw-copy-inline.copied { background: #22c55e; }

.pw-copy-hint {
  font-size: 0.75rem;
  color: #64748b;
  margin-top: 6px;
}

/* ボタン群 */
.pw-btn-row {
  display: flex;
  gap: 12px;
  margin-top: 16px;
  flex-wrap: wrap;
}

.pw-btn-generate {
  flex: 1;
  min-width: 140px;
  background: linear-gradient(135deg, #3b82f6, #1d4ed8);
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 14px 24px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.1s;
  letter-spacing: 0.03em;
}
.pw-btn-generate:hover { opacity: 0.9; }
.pw-btn-generate:active { transform: scale(0.97); }

.pw-btn-multi {
  background: #164e63;
  color: #7dd3fc;
  border: 1px solid #0e7490;
  border-radius: 8px;
  padding: 14px 18px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}
.pw-btn-multi:hover { background: #1e6a87; }
.pw-btn-multi.active { background: #0e7490; color: #fff; }

/* 強度メーター */
.pw-strength-bar-wrap {
  margin-top: 16px;
}
.pw-strength-label {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 6px;
  font-size: 0.85rem;
  color: #94a3b8;
}
.pw-strength-name {
  font-weight: 700;
  font-size: 0.95rem;
}
.pw-entropy {
  font-size: 0.78rem;
  color: #64748b;
}
.pw-bar-bg {
  height: 8px;
  background: #0f2240;
  border-radius: 4px;
  overflow: hidden;
}
.pw-bar-fill {
  height: 100%;
  border-radius: 4px;
  transition: width 0.4s ease, background 0.4s ease;
}
.pw-strength-reason {
  font-size: 0.78rem;
  color: #94a3b8;
  margin-top: 6px;
}

/* スライダー */
.pw-slider-row {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 14px;
}
.pw-slider-label {
  white-space: nowrap;
  font-size: 0.9rem;
  color: #cbd5e1;
  min-width: 80px;
}
.pw-length-val {
  font-weight: 700;
  color: #60a5fa;
  font-size: 1rem;
  min-width: 36px;
  text-align: right;
}
input[type="range"] {
  flex: 1;
  -webkit-appearance: none;
  appearance: none;
  height: 6px;
  background: #1e4a7a;
  border-radius: 3px;
  outline: none;
}
input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #3b82f6;
  cursor: pointer;
  box-shadow: 0 0 0 3px rgba(59,130,246,0.3);
}
input[type="range"]::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #3b82f6;
  cursor: pointer;
  border: none;
}

/* チェックボックス群 */
.pw-checks {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 10px;
  margin-bottom: 14px;
}
.pw-check-item {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  padding: 8px 10px;
  background: #0f2240;
  border-radius: 6px;
  border: 1px solid #1e4a7a;
  transition: border-color 0.2s;
  user-select: none;
}
.pw-check-item:hover { border-color: #3b82f6; }
.pw-check-item input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #3b82f6;
  cursor: pointer;
}
.pw-check-text {
  font-size: 0.85rem;
  color: #cbd5e1;
}
.pw-check-sample {
  font-family: monospace;
  font-size: 0.75rem;
  color: #60a5fa;
  margin-left: auto;
}

/* モード切替タブ */
.pw-mode-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}
.pw-tab {
  padding: 8px 16px;
  border-radius: 6px;
  border: 1px solid #1e4a7a;
  background: #0f2240;
  color: #94a3b8;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}
.pw-tab.active {
  background: #3b82f6;
  border-color: #3b82f6;
  color: #fff;
}
.pw-tab:hover:not(.active) { border-color: #3b82f6; color: #60a5fa; }

/* 複数生成リスト */
.pw-multi-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 8px;
}
.pw-multi-item {
  display: flex;
  align-items: center;
  gap: 10px;
  background: #0f2240;
  border: 1px solid #1e4a7a;
  border-radius: 6px;
  padding: 10px 14px;
}
.pw-multi-text {
  flex: 1;
  font-family: 'Courier New', Courier, monospace;
  font-size: 0.9rem;
  color: #f0f9ff;
  word-break: break-all;
}
.pw-btn-copy-small {
  background: #1e4a7a;
  color: #7dd3fc;
  border: 1px solid #2563eb;
  border-radius: 5px;
  padding: 5px 10px;
  font-size: 0.78rem;
  font-weight: 600;
  cursor: pointer;
  white-space: nowrap;
  transition: background 0.2s;
  flex-shrink: 0;
}
.pw-btn-copy-small:hover { background: #2563eb; color: #fff; }
.pw-btn-copy-small.copied { background: #166534; color: #86efac; border-color: #22c55e; }

/* パスフレーズ設定 */
.pw-passphrase-opts {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 10px;
}
.pw-passphrase-opts label {
  font-size: 0.85rem;
  color: #94a3b8;
}
.pw-passphrase-opts select,
.pw-passphrase-opts input[type="text"] {
  background: #0f2240;
  border: 1px solid #1e4a7a;
  border-radius: 5px;
  color: #e2e8f0;
  padding: 5px 8px;
  font-size: 0.85rem;
}

/* レスポンシブ */
@media (max-width: 500px) {
  .pw-card { padding: 16px; }
  #pw-output { font-size: 1rem; }
  .pw-display-wrap { padding-right: 14px; padding-bottom: 54px; }
  .pw-copy-inline { top: auto; bottom: 10px; right: 12px; transform: none; }
  .pw-copy-inline:active { transform: scale(0.95); }
  .pw-btn-generate { font-size: 0.95rem; padding: 12px 16px; }
  .pw-checks { grid-template-columns: 1fr 1fr; }
}
</style>

<!-- モード切替 -->
<div class="pw-card">
  <div class="pw-mode-tabs">
    <button class="pw-tab active" onclick="setMode('random')" id="tab-random">ランダム生成</button>
    <button class="pw-tab" onclick="setMode('passphrase')" id="tab-passphrase">パスフレーズ</button>
    <button class="pw-tab" onclick="setMode('multi')" id="tab-multi">複数生成</button>
  </div>

  <!-- パスワード表示 -->
  <div class="pw-display-wrap" id="pw-display-wrap" onclick="copyMain()" title="クリックしてコピー">
    <div id="pw-output">クリックして生成</div>
    <button class="pw-copy-inline" id="pw-copy-btn" onclick="event.stopPropagation(); copyMain()">コピー</button>
  </div>
  <div class="pw-copy-hint" id="pw-copy-hint">クリックでコピー</div>

  <!-- 強度メーター -->
  <div class="pw-strength-bar-wrap">
    <div class="pw-strength-label">
      <span>強度: <span class="pw-strength-name" id="pw-strength-name">—</span></span>
      <span class="pw-entropy" id="pw-entropy"></span>
    </div>
    <div class="pw-bar-bg"><div class="pw-bar-fill" id="pw-bar-fill" style="width:0%;background:#334155"></div></div>
    <div class="pw-strength-reason" id="pw-strength-reason"></div>
  </div>

  <!-- ボタン -->
  <div class="pw-btn-row">
    <button class="pw-btn-generate" onclick="generate()">生成する</button>
  </div>
</div>

<!-- ランダム設定 -->
<div class="pw-card" id="panel-random">
  <div class="pw-title">設定</div>

  <!-- 長さスライダー -->
  <div class="pw-slider-row">
    <span class="pw-slider-label">文字数</span>
    <input type="range" id="pw-length" min="8" max="128" value="16" oninput="onLengthChange()">
    <span class="pw-length-val" id="pw-length-val">16</span>
  </div>

  <!-- チェックボックス -->
  <div class="pw-checks">
    <label class="pw-check-item">
      <input type="checkbox" id="ch-upper" checked onchange="generate()">
      <span class="pw-check-text">大文字</span>
      <span class="pw-check-sample">A-Z</span>
    </label>
    <label class="pw-check-item">
      <input type="checkbox" id="ch-lower" checked onchange="generate()">
      <span class="pw-check-text">小文字</span>
      <span class="pw-check-sample">a-z</span>
    </label>
    <label class="pw-check-item">
      <input type="checkbox" id="ch-num" checked onchange="generate()">
      <span class="pw-check-text">数字</span>
      <span class="pw-check-sample">0-9</span>
    </label>
    <label class="pw-check-item">
      <input type="checkbox" id="ch-sym" checked onchange="generate()">
      <span class="pw-check-text">記号</span>
      <span class="pw-check-sample">!@#...</span>
    </label>
    <label class="pw-check-item">
      <input type="checkbox" id="ch-noamb" onchange="generate()">
      <span class="pw-check-text">紛らわしい文字を除外</span>
    </label>
  </div>
  <div style="font-size:0.75rem;color:#475569;margin-top:-6px;margin-bottom:4px;">※紛らわしい文字: I l 1 O 0</div>
</div>

<!-- パスフレーズ設定 -->
<div class="pw-card" id="panel-passphrase" style="display:none">
  <div class="pw-title">パスフレーズ設定</div>
  <div class="pw-passphrase-opts">
    <label>単語数:
      <select id="pp-words" onchange="generate()">
        <option value="3">3語</option>
        <option value="4" selected>4語</option>
        <option value="5">5語</option>
        <option value="6">6語</option>
      </select>
    </label>
    <label>区切り文字:
      <input type="text" id="pp-sep" value="-" maxlength="3" style="width:50px" oninput="generate()">
    </label>
    <label class="pw-check-item" style="flex:none">
      <input type="checkbox" id="pp-cap" checked onchange="generate()">
      <span class="pw-check-text">先頭大文字</span>
    </label>
    <label class="pw-check-item" style="flex:none">
      <input type="checkbox" id="pp-num" checked onchange="generate()">
      <span class="pw-check-text">数字を追加</span>
    </label>
  </div>
</div>

<!-- 複数生成パネル -->
<div class="pw-card" id="panel-multi" style="display:none">
  <div class="pw-title">5個同時生成</div>
  <div class="pw-multi-list" id="pw-multi-list">
    <!-- JSで生成 -->
  </div>
</div>

<script>
(function() {
  // ===== 単語リスト（日本語ローマ字 200語） =====
  var WORDS = [
    'hana','yama','kawa','umi','sora','mori','shiro','tsuki','hoshi','tori',
    'sakura','kaze','ame','yuki','kumo','taiko','fuji','nami','kiba','tama',
    'aki','natsu','fuyu','haru','yoru','asa','hiru','michi','ike','tani',
    'ishi','ki','ha','ne','mi','hana','kao','te','ashi','mimi',
    'me','kuchi','koe','kokoro','chikara','yume','inochi','mono','koto','toki',
    'basho','iro','katachi','hikari','kage','oto','kaori','aji','te','naka',
    'soto','ue','shita','mae','ushiro','migi','hidari','chika','hoka','doko',
    'itsu','naze','dare','nani','dore','kore','sore','are','koko','soko',
    'ao','aka','shiro2','kuro','ki2','midori','murasaki','kin','gin','chairo',
    'ookii','chiisai','nagai','mijikai','hayai','osoi','atarashii','furui','ii','warui',
    'takai','hikui','omoi','karui','atsui','samui','atatakai','tsumetai','katai','yawarakai',
    'hashiru','aruku','tobu','oyogu','yomu','kaku','kiku','miru','taberu','nomu',
    'neru','okiru','iku','kuru','kaeru','au','hanasu','warau','naku','utau',
    'hito','kodomo','otoko','onna','kazoku','tomodachi','sensei','gakusei','isha','keisatsu',
    'inu','neko','tori2','sakana','uma','ushi','buta','usagi','kuma','kitsune',
    'ringo','mikan','banana','ichigo','budou','suika','momo','nashi','kaki','ume',
    'gohan','pan','niku','sakana2','yasai','tamago','shio','satou','mizu','ocha',
    'kuruma','densha','hikoki','fune','jitensha','eki','michi2','hashi','koen','mise',
    'hon','tegami','shinbun','zasshi','kagi','tokei','megane','kasa','kutsu','fuku'
  ];

  // ===== 文字セット =====
  var UPPER = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  var LOWER = 'abcdefghijklmnopqrstuvwxyz';
  var NUMS  = '0123456789';
  var SYMS  = '!@#$%^&*()-_=+[]{}|;:,.<>?/';
  var AMB   = /[Il1O0]/g;

  var currentMode = 'random';
  var currentPassword = '';

  // ===== セキュアランダム =====
  function secureRandInt(max) {
    var buf = new Uint32Array(1);
    var limit = Math.floor(0x100000000 / max) * max;
    do { crypto.getRandomValues(buf); } while (buf[0] >= limit);
    return buf[0] % max;
  }

  function secureChoice(arr) {
    return arr[secureRandInt(arr.length)];
  }

  function secureRandDigit() {
    return String(secureRandInt(10));
  }

  // ===== ランダムパスワード生成 =====
  function generateRandom() {
    var len = parseInt(document.getElementById('pw-length').value);
    var useUpper = document.getElementById('ch-upper').checked;
    var useLower = document.getElementById('ch-lower').checked;
    var useNum   = document.getElementById('ch-num').checked;
    var useSym   = document.getElementById('ch-sym').checked;
    var noAmb    = document.getElementById('ch-noamb').checked;

    var pool = '';
    var guaranteed = [];

    if (useUpper) { var s = noAmb ? UPPER.replace(AMB,'') : UPPER; pool += s; guaranteed.push(secureChoice(s.split(''))); }
    if (useLower) { var s = noAmb ? LOWER.replace(AMB,'') : LOWER; pool += s; guaranteed.push(secureChoice(s.split(''))); }
    if (useNum)   { var s = noAmb ? NUMS.replace(AMB,'')  : NUMS;  pool += s; guaranteed.push(secureChoice(s.split(''))); }
    if (useSym)   { pool += SYMS; guaranteed.push(secureChoice(SYMS.split(''))); }

    if (!pool) return 'チェックボックスを選択してください';

    var chars = [];
    for (var i = 0; i < len; i++) chars.push(secureChoice(pool.split('')));

    // 必須文字を確実に埋め込む
    for (var i = 0; i < guaranteed.length && i < len; i++) {
      var pos = secureRandInt(len);
      chars[pos] = guaranteed[i];
    }

    return chars.join('');
  }

  // ===== パスフレーズ生成 =====
  function generatePassphrase() {
    var count = parseInt(document.getElementById('pp-words').value);
    var sep   = document.getElementById('pp-sep').value;
    var cap   = document.getElementById('pp-cap').checked;
    var addNum = document.getElementById('pp-num').checked;

    var parts = [];
    for (var i = 0; i < count; i++) {
      var w = WORDS[secureRandInt(WORDS.length)];
      if (cap) w = w.charAt(0).toUpperCase() + w.slice(1);
      parts.push(w);
    }
    var pw = parts.join(sep);
    if (addNum) pw += sep + (secureRandInt(90) + 10);
    return pw;
  }

  // ===== 強度計算 =====
  function calcEntropy(pw) {
    var poolSize = 0;
    if (/[A-Z]/.test(pw)) poolSize += 26;
    if (/[a-z]/.test(pw)) poolSize += 26;
    if (/[0-9]/.test(pw)) poolSize += 10;
    if (/[^A-Za-z0-9]/.test(pw)) poolSize += 32;
    if (poolSize === 0) poolSize = 26;
    return Math.floor(pw.length * Math.log2(poolSize));
  }

  function getStrength(pw) {
    if (!pw || pw.length < 2) return { level: 0, name: '—', color: '#334155', pct: 0, reason: '' };
    var entropy = calcEntropy(pw);
    var reasons = [];
    var level, name, color;

    if (pw.length < 8)  reasons.push('文字数が少なすぎます');
    if (pw.length < 12) reasons.push('12文字以上を推奨');
    if (!/[A-Z]/.test(pw)) reasons.push('大文字を追加すると強くなります');
    if (!/[a-z]/.test(pw)) reasons.push('小文字を追加すると強くなります');
    if (!/[0-9]/.test(pw)) reasons.push('数字を追加すると強くなります');
    if (!/[^A-Za-z0-9]/.test(pw)) reasons.push('記号を追加すると強くなります');

    if (entropy < 28)      { level=1; name='弱い';      color='#ef4444'; pct=15; }
    else if (entropy < 40) { level=2; name='やや弱い';  color='#f97316'; pct=35; }
    else if (entropy < 60) { level=3; name='普通';      color='#eab308'; pct=55; }
    else if (entropy < 80) { level=4; name='強い';      color='#22c55e'; pct=78; }
    else                   { level=5; name='非常に強い'; color='#3b82f6'; pct=100; }

    var reason = reasons.length ? reasons[0] : (level >= 4 ? '安全なパスワードです' : '');
    return { level, name, color, pct, reason, entropy };
  }

  // ===== UI更新 =====
  function updateStrength(pw) {
    var s = getStrength(pw);
    document.getElementById('pw-strength-name').textContent = s.name;
    document.getElementById('pw-strength-name').style.color = s.color;
    var bar = document.getElementById('pw-bar-fill');
    bar.style.width = s.pct + '%';
    bar.style.background = s.color;
    document.getElementById('pw-strength-reason').textContent = s.reason;
    document.getElementById('pw-entropy').textContent = s.entropy ? 'エントロピー: ' + s.entropy + ' bit' : '';
  }

  function setOutput(pw) {
    currentPassword = pw;
    document.getElementById('pw-output').textContent = pw;
    updateStrength(pw);
    // コピー状態リセット
    document.getElementById('pw-display-wrap').classList.remove('copied');
    document.getElementById('pw-copy-btn').classList.remove('copied');
    document.getElementById('pw-copy-btn').textContent = 'コピー';
    document.getElementById('pw-copy-hint').textContent = 'クリックでコピー';
  }

  // ===== コピー =====
  function copyText(text, btn, hint) {
    if (!text || text === 'クリックして生成') return;
    navigator.clipboard.writeText(text).then(function() {
      if (btn) {
        btn.classList.add('copied');
        btn.textContent = 'コピー済!';
        setTimeout(function() {
          btn.classList.remove('copied');
          btn.textContent = btn.dataset.origText || 'コピー';
        }, 2000);
      }
      if (hint) {
        hint.textContent = 'コピーしました!';
        setTimeout(function() { hint.textContent = 'クリックでコピー'; }, 2000);
      }
    }).catch(function() {
      // フォールバック
      var el = document.createElement('textarea');
      el.value = text;
      el.style.position = 'fixed';
      el.style.opacity = '0';
      document.body.appendChild(el);
      el.select();
      document.execCommand('copy');
      document.body.removeChild(el);
    });
  }

  window.copyMain = function() {
    if (!currentPassword || currentPassword === 'クリックして生成') return;
    var wrap = document.getElementById('pw-display-wrap');
    var btn  = document.getElementById('pw-copy-btn');
    var hint = document.getElementById('pw-copy-hint');
    wrap.classList.add('copied');
    btn.classList.add('copied');
    btn.textContent = 'コピー済!';
    hint.textContent = 'コピーしました!';
    navigator.clipboard.writeText(currentPassword).catch(function(){
      var el = document.createElement('textarea');
      el.value = currentPassword;
      el.style.position='fixed'; el.style.opacity='0';
      document.body.appendChild(el); el.select();
      document.execCommand('copy'); document.body.removeChild(el);
    });
    setTimeout(function() {
      wrap.classList.remove('copied');
      btn.classList.remove('copied');
      btn.textContent = 'コピー';
      hint.textContent = 'クリックでコピー';
    }, 2000);
  };

  // ===== 複数生成 =====
  function generateMulti() {
    var list = document.getElementById('pw-multi-list');
    list.innerHTML = '';
    for (var i = 0; i < 5; i++) {
      var pw = currentMode === 'passphrase' ? generatePassphrase() : generateRandom();
      var item = document.createElement('div');
      item.className = 'pw-multi-item';
      var span = document.createElement('span');
      span.className = 'pw-multi-text';
      span.textContent = pw;
      var copyBtn = document.createElement('button');
      copyBtn.className = 'pw-btn-copy-small';
      copyBtn.textContent = 'コピー';
      copyBtn.dataset.origText = 'コピー';
      var pwCopy = pw;
      copyBtn.addEventListener('click', (function(b, p) {
        return function() { copyText(p, b, null); };
      })(copyBtn, pwCopy));
      item.appendChild(span);
      item.appendChild(copyBtn);
      list.appendChild(item);
    }
  }

  // ===== モード切替 =====
  window.setMode = function(mode) {
    currentMode = mode;
    ['random','passphrase','multi'].forEach(function(m) {
      document.getElementById('tab-'+m).classList.toggle('active', m===mode);
      var panel = document.getElementById('panel-'+m);
      if (panel) panel.style.display = m===mode ? '' : 'none';
    });
    document.getElementById('panel-random').style.display = (mode === 'random') ? '' : 'none';
    generate();
  };

  // ===== メイン生成 =====
  window.generate = function() {
    var pw;
    if (currentMode === 'passphrase') {
      pw = generatePassphrase();
      setOutput(pw);
    } else if (currentMode === 'multi') {
      pw = generateRandom();
      setOutput(pw);
      generateMulti();
    } else {
      pw = generateRandom();
      setOutput(pw);
    }
  };

  window.onLengthChange = function() {
    var v = document.getElementById('pw-length').value;
    document.getElementById('pw-length-val').textContent = v;
    generate();
  };

  // 初期生成
  generate();
})();
</script>

</div>

---

## 安全なパスワードの作り方

パスワードとは、デジタルの世界における「カギ」です。銀行口座、メール、ショッピングサイトなど、あらゆるオンラインサービスへのアクセスはパスワードによって守られています。基本的な原則は、**長く・複雑で・使い回さない**こと。文字数が多いほど解読に時間がかかり、大文字・小文字・数字・記号を組み合わせるほど総当たり攻撃（ブルートフォース）に強くなります。8文字程度では現代のコンピュータでは数時間以内に解読される可能性があるため、最低でも12文字以上を目安にしましょう。

サイバー攻撃の件数は年々増加しており、2023年には世界で数十億件ものアカウント情報が漏洩しました。弱いパスワードや使い回しのパスワードは、一つのサービスの情報漏洩が他のサービスへの不正アクセスに連鎖する「パスワードリスト攻撃」の被害を招きます。銀行やメールアカウントなど、特に重要なサービスには必ず独自の強力なパスワードを設定することが不可欠です。

「長くて複雑なパスワードは覚えられない」という悩みには、**パスフレーズ**という方法が効果的です。ランダムな単語を3〜4個つなげたパスフレーズ（例：`Hana-Yama-Umi-2025`）は、ランダム文字列より覚えやすく、文字数が多いため十分な強度を持ちます。また、パスワードマネージャー（1Password、Bitwarden等）を活用すれば、複雑なパスワードを覚える必要がなくなります。マスターパスワード一つで全てのパスワードを安全に管理できます。

---

## パスワードセキュリティのヒント

- **使い回しは厳禁** — サービスごとに異なるパスワードを設定してください。一つが漏洩しても他のアカウントは安全です。
- **12文字以上が目安** — 文字数は強度に直結します。重要度の高いアカウントは16文字以上を推奨します。
- **二段階認証（2FA）を有効に** — パスワードと組み合わせることで、万一漏洩しても不正アクセスを防げます。SMSより認証アプリ（Google Authenticator等）がより安全です。
- **パスワードマネージャーを活用** — 全てのパスワードを安全に保管・自動入力できます。BItwarden（無料）やiCloudキーチェーンがおすすめです。
- **定期的な変更より、漏洩時の即時変更** — 定期変更よりも、不審なアクセスや情報漏洩のニュースを見たときにすぐ変更する方が効果的です。
- **フィッシングに注意** — どれだけ強いパスワードでも、偽サイトに入力すれば無意味です。URLを必ず確認し、公式サイトへはブックマークからアクセスしましょう。
- **公共Wi-Fiでのログインは避ける** — 盗聴リスクがあります。やむを得ない場合はVPNを使用してください。
- **秘密の質問は嘘の答えで** — 「母親の旧姓」などの質問は調べられる可能性があります。ランダムな文字列を答えとして設定し、パスワードマネージャーに保存しましょう。

---

## 関連ツール

> 割合・割引・変化率をすぐ計算 → [パーセント計算ツール](/ja/tools/percent-calculator/)

> サブスクの年間コストを把握 → [サブスク管理計算ツール](/ja/tools/subscription-cost-calculator/)

> ポモドーロテクニックで集中力アップ → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)

---

**フリーランス・個人事業主のセキュリティ対策に**

パスワード管理だけでなく、経理データのセキュリティも大切。クラウド会計ソフト「freee」なら、銀行レベルのセキュリティで安心して経費管理・確定申告ができます。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
