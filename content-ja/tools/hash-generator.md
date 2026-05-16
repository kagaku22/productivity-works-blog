---
title: "ハッシュ生成ツール - SHA256・MD5・SHA1 無料オンラインツール"
date: 2025-05-16
description: "SHA-256、MD5、SHA-1、SHA-512ハッシュを即座に生成。テキストのハッシュ化やファイルのチェックサム検証に。無料オンラインハッシュジェネレーター。"
categories: ["無料ツール"]
tags: ["ハッシュ", "SHA256", "MD5", "チェックサム", "セキュリティ"]
slug: "hash-generator"
aliases: ["/ja/tools/sha256-generator/", "/ja/tools/md5-generator/"]
cover:
  image: "/images/covers/hash-generator-ja.png"
  alt: "ハッシュ生成ツール"
ShowToc: false
---

<div id="hash-app">

<style>
#hash-app {
  font-family: 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 28px;
  max-width: 860px;
  margin: 0 auto;
  box-sizing: border-box;
}
#hash-app * { box-sizing: border-box; }

#hash-app h2 {
  color: #f59e0b;
  font-size: 1.3rem;
  margin: 0 0 16px 0;
  display: flex;
  align-items: center;
  gap: 8px;
}
#hash-app h2::before { content: "🔐"; }

.hash-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}
.hash-tab-btn {
  background: #1e293b;
  border: 1px solid #334155;
  color: #94a3b8;
  padding: 7px 16px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.85rem;
  transition: all 0.2s;
}
.hash-tab-btn:hover { background: #334155; color: #e2e8f0; }
.hash-tab-btn.active {
  background: #f59e0b;
  border-color: #f59e0b;
  color: #0f172a;
  font-weight: 700;
}

.hash-panel { display: none; }
.hash-panel.active { display: block; }

/* === TEXT HASH PANEL === */
label.hash-label {
  display: block;
  font-size: 0.8rem;
  color: #94a3b8;
  margin-bottom: 6px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

textarea.hash-input {
  width: 100%;
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  padding: 12px;
  font-size: 0.95rem;
  resize: vertical;
  min-height: 110px;
  outline: none;
  transition: border-color 0.2s;
  line-height: 1.5;
}
textarea.hash-input:focus { border-color: #f59e0b; }

.algo-row {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
  margin: 14px 0;
}
.algo-label-txt { font-size: 0.85rem; color: #94a3b8; }
.algo-pill {
  background: #1e293b;
  border: 1px solid #334155;
  color: #94a3b8;
  padding: 5px 14px;
  border-radius: 20px;
  cursor: pointer;
  font-size: 0.82rem;
  transition: all 0.2s;
}
.algo-pill:hover { border-color: #f59e0b; color: #f59e0b; }
.algo-pill.selected {
  background: #f59e0b22;
  border-color: #f59e0b;
  color: #f59e0b;
  font-weight: 700;
}

.hash-btn-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 18px;
}
.btn-primary {
  background: #f59e0b;
  color: #0f172a;
  border: none;
  border-radius: 8px;
  padding: 10px 22px;
  font-size: 0.9rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s;
}
.btn-primary:hover { background: #fbbf24; }
.btn-secondary {
  background: transparent;
  color: #f59e0b;
  border: 1px solid #f59e0b;
  border-radius: 8px;
  padding: 10px 18px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}
.btn-secondary:hover { background: #f59e0b22; }

.hash-result-block {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 14px;
  margin-bottom: 10px;
}
.hash-result-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 8px;
}
.algo-name-tag {
  font-size: 0.75rem;
  font-weight: 700;
  color: #f59e0b;
  background: #f59e0b22;
  padding: 2px 10px;
  border-radius: 12px;
  text-transform: uppercase;
}
.copy-btn {
  background: transparent;
  border: 1px solid #475569;
  color: #94a3b8;
  border-radius: 6px;
  padding: 3px 12px;
  font-size: 0.78rem;
  cursor: pointer;
  transition: all 0.2s;
}
.copy-btn:hover { border-color: #f59e0b; color: #f59e0b; }
.copy-btn.copied { border-color: #22c55e; color: #22c55e; }

.hash-value {
  font-family: 'Courier New', Consolas, monospace;
  font-size: 0.82rem;
  color: #e2e8f0;
  word-break: break-all;
  line-height: 1.6;
  min-height: 20px;
}
.hash-value.uppercase { text-transform: uppercase; }
.hash-placeholder { color: #475569; font-style: italic; }

.case-toggle-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 14px;
  font-size: 0.85rem;
  color: #94a3b8;
}
.toggle-switch {
  position: relative;
  width: 42px;
  height: 22px;
  display: inline-block;
}
.toggle-switch input { opacity: 0; width: 0; height: 0; }
.toggle-slider {
  position: absolute;
  inset: 0;
  background: #334155;
  border-radius: 22px;
  cursor: pointer;
  transition: 0.2s;
}
.toggle-slider::before {
  content: '';
  position: absolute;
  width: 16px; height: 16px;
  left: 3px; bottom: 3px;
  background: #94a3b8;
  border-radius: 50%;
  transition: 0.2s;
}
.toggle-switch input:checked + .toggle-slider { background: #f59e0b44; }
.toggle-switch input:checked + .toggle-slider::before {
  transform: translateX(20px);
  background: #f59e0b;
}

/* === HMAC PANEL === */
.hmac-key-row { margin-bottom: 14px; }
input.hash-key-input {
  width: 100%;
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  padding: 10px 12px;
  font-size: 0.9rem;
  outline: none;
  transition: border-color 0.2s;
}
input.hash-key-input:focus { border-color: #f59e0b; }

/* === FILE HASH PANEL === */
.dropzone {
  border: 2px dashed #334155;
  border-radius: 10px;
  padding: 40px 20px;
  text-align: center;
  color: #64748b;
  cursor: pointer;
  transition: all 0.2s;
  margin-bottom: 16px;
  background: #1e293b;
}
.dropzone.dragover { border-color: #f59e0b; color: #f59e0b; background: #f59e0b11; }
.dropzone .dz-icon { font-size: 2.2rem; margin-bottom: 10px; }
.dropzone .dz-text { font-size: 0.95rem; }
.dropzone .dz-sub { font-size: 0.78rem; margin-top: 6px; color: #475569; }

input[type="file"]#fileInput { display: none; }

.file-info-bar {
  display: flex;
  align-items: center;
  gap: 10px;
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 10px 14px;
  margin-bottom: 14px;
  font-size: 0.85rem;
  color: #94a3b8;
}
.file-info-bar .file-name { color: #e2e8f0; font-weight: 600; flex: 1; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }

/* === COMPARE PANEL === */
.compare-inputs { display: flex; flex-direction: column; gap: 10px; margin-bottom: 14px; }
.compare-field label { display: block; font-size: 0.78rem; color: #94a3b8; margin-bottom: 5px; }
input.compare-input {
  width: 100%;
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  padding: 10px 12px;
  font-family: 'Courier New', monospace;
  font-size: 0.82rem;
  outline: none;
  transition: border-color 0.2s;
}
input.compare-input:focus { border-color: #f59e0b; }

.compare-result {
  border-radius: 8px;
  padding: 14px 18px;
  font-size: 0.95rem;
  font-weight: 600;
  text-align: center;
  display: none;
}
.compare-result.match { background: #15803d22; border: 1px solid #22c55e; color: #22c55e; }
.compare-result.mismatch { background: #dc262622; border: 1px solid #ef4444; color: #ef4444; }

.progress-bar-wrap {
  width: 100%;
  background: #1e293b;
  border-radius: 6px;
  height: 6px;
  margin-bottom: 14px;
  overflow: hidden;
  display: none;
}
.progress-bar-fill {
  height: 100%;
  background: #f59e0b;
  border-radius: 6px;
  width: 0%;
  transition: width 0.1s;
}

@media (max-width: 600px) {
  #hash-app { padding: 16px; }
  .hash-btn-row { flex-direction: column; }
  .btn-primary, .btn-secondary { width: 100%; text-align: center; }
  .algo-row { gap: 6px; }
}
</style>

<h2>ハッシュ生成ツール</h2>

<div class="hash-tabs">
  <button class="hash-tab-btn active" onclick="switchTab('text')">テキスト</button>
  <button class="hash-tab-btn" onclick="switchTab('file')">ファイル</button>
  <button class="hash-tab-btn" onclick="switchTab('hmac')">HMAC</button>
  <button class="hash-tab-btn" onclick="switchTab('compare')">ハッシュ比較</button>
</div>

<!-- TEXT PANEL -->
<div id="panel-text" class="hash-panel active">
  <label class="hash-label" for="textInput">テキスト入力</label>
  <textarea class="hash-input" id="textInput" placeholder="ハッシュ化するテキストを入力してください..."></textarea>

  <div class="algo-row">
    <span class="algo-label-txt">アルゴリズム:</span>
    <span class="algo-pill selected" data-algo="MD5" onclick="selectAlgo(this)">MD5</span>
    <span class="algo-pill" data-algo="SHA-1" onclick="selectAlgo(this)">SHA-1</span>
    <span class="algo-pill" data-algo="SHA-256" onclick="selectAlgo(this)">SHA-256</span>
    <span class="algo-pill" data-algo="SHA-384" onclick="selectAlgo(this)">SHA-384</span>
    <span class="algo-pill" data-algo="SHA-512" onclick="selectAlgo(this)">SHA-512</span>
  </div>

  <div class="case-toggle-row">
    <label class="toggle-switch">
      <input type="checkbox" id="uppercaseToggle" onchange="toggleCase()">
      <span class="toggle-slider"></span>
    </label>
    <span>大文字表示</span>
  </div>

  <div class="hash-btn-row">
    <button class="btn-primary" onclick="generateTextHash()">ハッシュ生成</button>
    <button class="btn-secondary" onclick="generateAllHashes()">全アルゴリズム生成</button>
    <button class="btn-secondary" onclick="clearText()">クリア</button>
  </div>

  <div id="text-results"></div>
</div>

<!-- FILE PANEL -->
<div id="panel-file" class="hash-panel">
  <div class="dropzone" id="dropzone" onclick="document.getElementById('fileInput').click()"
       ondragover="dzDragOver(event)" ondragleave="dzDragLeave(event)" ondrop="dzDrop(event)">
    <div class="dz-icon">📂</div>
    <div class="dz-text">ファイルをドラッグ&ドロップ</div>
    <div class="dz-sub">またはクリックしてファイルを選択（最大 2GB）</div>
  </div>
  <input type="file" id="fileInput" onchange="handleFileSelect(this.files[0])">

  <div id="file-info" style="display:none" class="file-info-bar">
    <span>📄</span>
    <span class="file-name" id="fileName"></span>
    <span id="fileSize" style="color:#64748b;font-size:0.78rem;"></span>
  </div>

  <div class="progress-bar-wrap" id="fileProgress">
    <div class="progress-bar-fill" id="fileProgressFill"></div>
  </div>

  <div class="algo-row">
    <span class="algo-label-txt">アルゴリズム:</span>
    <span class="algo-pill selected" data-algo="MD5" onclick="selectFileAlgo(this)">MD5</span>
    <span class="algo-pill" data-algo="SHA-1" onclick="selectFileAlgo(this)">SHA-1</span>
    <span class="algo-pill" data-algo="SHA-256" onclick="selectFileAlgo(this)">SHA-256</span>
    <span class="algo-pill" data-algo="SHA-384" onclick="selectFileAlgo(this)">SHA-384</span>
    <span class="algo-pill" data-algo="SHA-512" onclick="selectFileAlgo(this)">SHA-512</span>
  </div>

  <div class="hash-btn-row">
    <button class="btn-primary" onclick="generateFileHash()">ファイルをハッシュ</button>
    <button class="btn-secondary" onclick="generateAllFileHashes()">全アルゴリズム生成</button>
  </div>

  <div id="file-results"></div>
</div>

<!-- HMAC PANEL -->
<div id="panel-hmac" class="hash-panel">
  <label class="hash-label" for="hmacText">テキスト入力</label>
  <textarea class="hash-input" id="hmacText" placeholder="HMAC化するテキストを入力してください..."></textarea>

  <div class="hmac-key-row" style="margin-top:12px;">
    <label class="hash-label" for="hmacKey">秘密鍵（シークレットキー）</label>
    <input type="text" class="hash-key-input" id="hmacKey" placeholder="秘密鍵を入力してください...">
  </div>

  <div class="algo-row">
    <span class="algo-label-txt">アルゴリズム:</span>
    <span class="algo-pill selected" data-algo="SHA-1" onclick="selectHmacAlgo(this)">SHA-1</span>
    <span class="algo-pill" data-algo="SHA-256" onclick="selectHmacAlgo(this)">SHA-256</span>
    <span class="algo-pill" data-algo="SHA-384" onclick="selectHmacAlgo(this)">SHA-384</span>
    <span class="algo-pill" data-algo="SHA-512" onclick="selectHmacAlgo(this)">SHA-512</span>
  </div>

  <div class="case-toggle-row">
    <label class="toggle-switch">
      <input type="checkbox" id="hmacUppercaseToggle" onchange="toggleHmacCase()">
      <span class="toggle-slider"></span>
    </label>
    <span>大文字表示</span>
  </div>

  <div class="hash-btn-row">
    <button class="btn-primary" onclick="generateHmac()">HMAC生成</button>
    <button class="btn-secondary" onclick="clearHmac()">クリア</button>
  </div>

  <div id="hmac-results"></div>
</div>

<!-- COMPARE PANEL -->
<div id="panel-compare" class="hash-panel">
  <p style="color:#94a3b8;font-size:0.88rem;margin-top:0;">2つのハッシュ値を入力して、一致するかどうかを確認します。</p>
  <div class="compare-inputs">
    <div class="compare-field">
      <label>ハッシュ値 1</label>
      <input type="text" class="compare-input" id="hash1" placeholder="1つ目のハッシュを入力...">
    </div>
    <div class="compare-field">
      <label>ハッシュ値 2</label>
      <input type="text" class="compare-input" id="hash2" placeholder="2つ目のハッシュを入力...">
    </div>
  </div>
  <div class="hash-btn-row">
    <button class="btn-primary" onclick="compareHashes()">ハッシュを比較</button>
    <button class="btn-secondary" onclick="clearCompare()">クリア</button>
  </div>
  <div class="compare-result" id="compareResult"></div>
</div>

<script>
(function() {

/* ===== MD5 IMPLEMENTATION ===== */
function md5(str) {
  function safeAdd(x, y) {
    var lsw = (x & 0xffff) + (y & 0xffff);
    var msw = (x >> 16) + (y >> 16) + (lsw >> 16);
    return (msw << 16) | (lsw & 0xffff);
  }
  function bitRotateLeft(num, cnt) { return (num << cnt) | (num >>> (32 - cnt)); }
  function md5cmn(q, a, b, x, s, t) { return safeAdd(bitRotateLeft(safeAdd(safeAdd(a, q), safeAdd(x, t)), s), b); }
  function md5ff(a,b,c,d,x,s,t){ return md5cmn((b&c)|((~b)&d),a,b,x,s,t); }
  function md5gg(a,b,c,d,x,s,t){ return md5cmn((b&d)|(c&(~d)),a,b,x,s,t); }
  function md5hh(a,b,c,d,x,s,t){ return md5cmn(b^c^d,a,b,x,s,t); }
  function md5ii(a,b,c,d,x,s,t){ return md5cmn(c^(b|(~d)),a,b,x,s,t); }
  function binlMD5(x, len) {
    x[len >> 5] |= 0x80 << (len % 32);
    x[((len + 64) >>> 9 << 4) + 14] = len;
    var i, olda, oldb, oldc, oldd,
      a = 1732584193, b = -271733879, c = -1732584194, d = 271733878;
    for (i = 0; i < x.length; i += 16) {
      olda = a; oldb = b; oldc = c; oldd = d;
      a=md5ff(a,b,c,d,x[i],7,-680876936); d=md5ff(d,a,b,c,x[i+1],12,-389564586);
      c=md5ff(c,d,a,b,x[i+2],17,606105819); b=md5ff(b,c,d,a,x[i+3],22,-1044525330);
      a=md5ff(a,b,c,d,x[i+4],7,-176418897); d=md5ff(d,a,b,c,x[i+5],12,1200080426);
      c=md5ff(c,d,a,b,x[i+6],17,-1473231341); b=md5ff(b,c,d,a,x[i+7],22,-45705983);
      a=md5ff(a,b,c,d,x[i+8],7,1770035416); d=md5ff(d,a,b,c,x[i+9],12,-1958414417);
      c=md5ff(c,d,a,b,x[i+10],17,-42063); b=md5ff(b,c,d,a,x[i+11],22,-1990404162);
      a=md5ff(a,b,c,d,x[i+12],7,1804603682); d=md5ff(d,a,b,c,x[i+13],12,-40341101);
      c=md5ff(c,d,a,b,x[i+14],17,-1502002290); b=md5ff(b,c,d,a,x[i+15],22,1236535329);
      a=md5gg(a,b,c,d,x[i+1],5,-165796510); d=md5gg(d,a,b,c,x[i+6],9,-1069501632);
      c=md5gg(c,d,a,b,x[i+11],14,643717713); b=md5gg(b,c,d,a,x[i],20,-373897302);
      a=md5gg(a,b,c,d,x[i+5],5,-701558691); d=md5gg(d,a,b,c,x[i+10],9,38016083);
      c=md5gg(c,d,a,b,x[i+15],14,-660478335); b=md5gg(b,c,d,a,x[i+4],20,-405537848);
      a=md5gg(a,b,c,d,x[i+9],5,568446438); d=md5gg(d,a,b,c,x[i+14],9,-1019803690);
      c=md5gg(c,d,a,b,x[i+3],14,-187363961); b=md5gg(b,c,d,a,x[i+8],20,1163531501);
      a=md5gg(a,b,c,d,x[i+13],5,-1444681467); d=md5gg(d,a,b,c,x[i+2],9,-51403784);
      c=md5gg(c,d,a,b,x[i+7],14,1735328473); b=md5gg(b,c,d,a,x[i+12],20,-1926607734);
      a=md5hh(a,b,c,d,x[i+5],4,-378558); d=md5hh(d,a,b,c,x[i+8],11,-2022574463);
      c=md5hh(c,d,a,b,x[i+11],16,1839030562); b=md5hh(b,c,d,a,x[i+14],23,-35309556);
      a=md5hh(a,b,c,d,x[i+1],4,-1530992060); d=md5hh(d,a,b,c,x[i+4],11,1272893353);
      c=md5hh(c,d,a,b,x[i+7],16,-155497632); b=md5hh(b,c,d,a,x[i+10],23,-1094730640);
      a=md5hh(a,b,c,d,x[i+13],4,681279174); d=md5hh(d,a,b,c,x[i],11,-358537222);
      c=md5hh(c,d,a,b,x[i+3],16,-722521979); b=md5hh(b,c,d,a,x[i+6],23,76029189);
      a=md5hh(a,b,c,d,x[i+9],4,-640364487); d=md5hh(d,a,b,c,x[i+12],11,-421815835);
      c=md5hh(c,d,a,b,x[i+15],16,530742520); b=md5hh(b,c,d,a,x[i+2],23,-995338651);
      a=md5ii(a,b,c,d,x[i],6,-198630844); d=md5ii(d,a,b,c,x[i+7],10,1126891415);
      c=md5ii(c,d,a,b,x[i+14],15,-1416354905); b=md5ii(b,c,d,a,x[i+5],21,-57434055);
      a=md5ii(a,b,c,d,x[i+12],6,1700485571); d=md5ii(d,a,b,c,x[i+3],10,-1894986606);
      c=md5ii(c,d,a,b,x[i+10],15,-1051523); b=md5ii(b,c,d,a,x[i+1],21,-2054922799);
      a=md5ii(a,b,c,d,x[i+8],6,1873313359); d=md5ii(d,a,b,c,x[i+15],10,-30611744);
      c=md5ii(c,d,a,b,x[i+6],15,-1560198380); b=md5ii(b,c,d,a,x[i+13],21,1309151649);
      a=md5ii(a,b,c,d,x[i+4],6,-145523070); d=md5ii(d,a,b,c,x[i+11],10,-1120210379);
      c=md5ii(c,d,a,b,x[i+2],15,718787259); b=md5ii(b,c,d,a,x[i+9],21,-343485551);
      a=safeAdd(a,olda); b=safeAdd(b,oldb); c=safeAdd(c,oldc); d=safeAdd(d,oldd);
    }
    return [a, b, c, d];
  }
  function binl2hex(binarray) {
    var hexTab = '0123456789abcdef', str = '';
    for (var i = 0; i < binarray.length * 4; i++) {
      str += hexTab.charAt((binarray[i>>2] >> ((i%4)*8+4)) & 0xf) +
             hexTab.charAt((binarray[i>>2] >> ((i%4)*8)) & 0xf);
    }
    return str;
  }
  function str2binl(str) {
    var bin = [], mask = (1 << 8) - 1;
    for (var i = 0; i < str.length * 8; i += 8) {
      bin[i>>5] |= (str.charCodeAt(i/8) & mask) << (i%32);
    }
    return bin;
  }
  function utf8Encode(s) {
    return unescape(encodeURIComponent(s));
  }
  var utf8 = utf8Encode(str);
  return binl2hex(binlMD5(str2binl(utf8), utf8.length * 8));
}

/* ===== UTILITIES ===== */
var isUppercase = false;
var isHmacUppercase = false;
var selectedAlgo = 'MD5';
var selectedFileAlgo = 'MD5';
var selectedHmacAlgo = 'SHA-1';
var currentFile = null;

function buf2hex(buffer) {
  return Array.prototype.map.call(new Uint8Array(buffer), function(x) {
    return ('00' + x.toString(16)).slice(-2);
  }).join('');
}

async function computeHash(algo, text) {
  if (algo === 'MD5') return md5(text);
  var encoder = new TextEncoder();
  var data = encoder.encode(text);
  var hashBuffer = await crypto.subtle.digest(algo, data);
  return buf2hex(hashBuffer);
}

async function computeHashFromBuffer(algo, buffer) {
  if (algo === 'MD5') {
    // MD5 for ArrayBuffer: convert to string
    var bytes = new Uint8Array(buffer);
    var str = '';
    for (var i = 0; i < bytes.length; i++) str += String.fromCharCode(bytes[i]);
    return md5(str);
  }
  var hashBuffer = await crypto.subtle.digest(algo, buffer);
  return buf2hex(hashBuffer);
}

function applyCase(hash) {
  return isUppercase ? hash.toUpperCase() : hash.toLowerCase();
}

function renderResult(containerId, algo, hash, isUp) {
  var h = isUp ? hash.toUpperCase() : hash.toLowerCase();
  return '<div class="hash-result-block">' +
    '<div class="hash-result-header">' +
    '<span class="algo-name-tag">' + algo + '</span>' +
    '<button class="copy-btn" onclick="copyHash(this,\'' + h + '\')">コピー</button>' +
    '</div>' +
    '<div class="hash-value' + (isUp ? ' uppercase' : '') + '">' + h + '</div>' +
    '</div>';
}

window.copyHash = function(btn, hash) {
  navigator.clipboard.writeText(hash).then(function() {
    btn.textContent = 'コピー済';
    btn.classList.add('copied');
    setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1500);
  });
};

/* ===== TABS ===== */
window.switchTab = function(tab) {
  ['text','file','hmac','compare'].forEach(function(t) {
    document.getElementById('panel-' + t).classList.toggle('active', t === tab);
  });
  document.querySelectorAll('.hash-tab-btn').forEach(function(btn, i) {
    btn.classList.toggle('active', ['text','file','hmac','compare'][i] === tab);
  });
};

/* ===== ALGO SELECTION ===== */
window.selectAlgo = function(el) {
  document.querySelectorAll('#panel-text .algo-pill').forEach(function(p) { p.classList.remove('selected'); });
  el.classList.add('selected');
  selectedAlgo = el.dataset.algo;
};
window.selectFileAlgo = function(el) {
  document.querySelectorAll('#panel-file .algo-pill').forEach(function(p) { p.classList.remove('selected'); });
  el.classList.add('selected');
  selectedFileAlgo = el.dataset.algo;
};
window.selectHmacAlgo = function(el) {
  document.querySelectorAll('#panel-hmac .algo-pill').forEach(function(p) { p.classList.remove('selected'); });
  el.classList.add('selected');
  selectedHmacAlgo = el.dataset.algo;
};

/* ===== CASE TOGGLE ===== */
window.toggleCase = function() {
  isUppercase = document.getElementById('uppercaseToggle').checked;
  document.querySelectorAll('#text-results .hash-value').forEach(function(el) {
    el.classList.toggle('uppercase', isUppercase);
  });
};
window.toggleHmacCase = function() {
  isHmacUppercase = document.getElementById('hmacUppercaseToggle').checked;
  document.querySelectorAll('#hmac-results .hash-value').forEach(function(el) {
    el.classList.toggle('uppercase', isHmacUppercase);
  });
};

/* ===== TEXT HASHING ===== */
window.generateTextHash = async function() {
  var text = document.getElementById('textInput').value;
  if (!text) { document.getElementById('text-results').innerHTML = '<p style="color:#ef4444;font-size:0.85rem;">テキストを入力してください。</p>'; return; }
  var hash = await computeHash(selectedAlgo, text);
  document.getElementById('text-results').innerHTML = renderResult('text-results', selectedAlgo, hash, isUppercase);
};

window.generateAllHashes = async function() {
  var text = document.getElementById('textInput').value;
  if (!text) { document.getElementById('text-results').innerHTML = '<p style="color:#ef4444;font-size:0.85rem;">テキストを入力してください。</p>'; return; }
  var algos = ['MD5','SHA-1','SHA-256','SHA-384','SHA-512'];
  document.getElementById('text-results').innerHTML = '<p style="color:#64748b;font-size:0.85rem;">生成中...</p>';
  var html = '';
  for (var i = 0; i < algos.length; i++) {
    var hash = await computeHash(algos[i], text);
    html += renderResult('text-results', algos[i], hash, isUppercase);
  }
  document.getElementById('text-results').innerHTML = html;
};

window.clearText = function() {
  document.getElementById('textInput').value = '';
  document.getElementById('text-results').innerHTML = '';
};

// Realtime on input (debounced)
var debounceTimer;
document.getElementById('textInput').addEventListener('input', function() {
  clearTimeout(debounceTimer);
  debounceTimer = setTimeout(function() {
    if (document.getElementById('textInput').value) generateTextHash();
  }, 400);
});

/* ===== FILE HASHING ===== */
window.dzDragOver = function(e) {
  e.preventDefault();
  document.getElementById('dropzone').classList.add('dragover');
};
window.dzDragLeave = function() {
  document.getElementById('dropzone').classList.remove('dragover');
};
window.dzDrop = function(e) {
  e.preventDefault();
  document.getElementById('dropzone').classList.remove('dragover');
  var file = e.dataTransfer.files[0];
  if (file) handleFileSelect(file);
};
window.handleFileSelect = function(file) {
  if (!file) return;
  currentFile = file;
  document.getElementById('file-info').style.display = 'flex';
  document.getElementById('fileName').textContent = file.name;
  document.getElementById('fileSize').textContent = formatBytes(file.size);
  document.getElementById('file-results').innerHTML = '';
};

function formatBytes(bytes) {
  if (bytes < 1024) return bytes + ' B';
  if (bytes < 1048576) return (bytes/1024).toFixed(1) + ' KB';
  if (bytes < 1073741824) return (bytes/1048576).toFixed(1) + ' MB';
  return (bytes/1073741824).toFixed(1) + ' GB';
}

async function readFileAsBuffer(file) {
  return new Promise(function(resolve, reject) {
    var reader = new FileReader();
    var prog = document.getElementById('fileProgress');
    var fill = document.getElementById('fileProgressFill');
    prog.style.display = 'block';
    reader.onprogress = function(e) {
      if (e.lengthComputable) fill.style.width = (e.loaded/e.total*100) + '%';
    };
    reader.onload = function(e) {
      fill.style.width = '100%';
      setTimeout(function() { prog.style.display = 'none'; fill.style.width = '0%'; }, 500);
      resolve(e.target.result);
    };
    reader.onerror = reject;
    reader.readAsArrayBuffer(file);
  });
}

window.generateFileHash = async function() {
  if (!currentFile) { alert('ファイルを選択してください。'); return; }
  document.getElementById('file-results').innerHTML = '<p style="color:#64748b;font-size:0.85rem;">計算中...</p>';
  try {
    var buffer = await readFileAsBuffer(currentFile);
    var hash = await computeHashFromBuffer(selectedFileAlgo, buffer);
    document.getElementById('file-results').innerHTML = renderResult('file-results', selectedFileAlgo, hash, false);
  } catch(e) {
    document.getElementById('file-results').innerHTML = '<p style="color:#ef4444;font-size:0.85rem;">エラーが発生しました。</p>';
  }
};

window.generateAllFileHashes = async function() {
  if (!currentFile) { alert('ファイルを選択してください。'); return; }
  document.getElementById('file-results').innerHTML = '<p style="color:#64748b;font-size:0.85rem;">計算中...</p>';
  try {
    var buffer = await readFileAsBuffer(currentFile);
    var algos = ['MD5','SHA-1','SHA-256','SHA-384','SHA-512'];
    var html = '';
    for (var i = 0; i < algos.length; i++) {
      var hash = await computeHashFromBuffer(algos[i], buffer);
      html += renderResult('file-results', algos[i], hash, false);
    }
    document.getElementById('file-results').innerHTML = html;
  } catch(e) {
    document.getElementById('file-results').innerHTML = '<p style="color:#ef4444;font-size:0.85rem;">エラーが発生しました。</p>';
  }
};

/* ===== HMAC ===== */
window.generateHmac = async function() {
  var text = document.getElementById('hmacText').value;
  var key = document.getElementById('hmacKey').value;
  if (!text || !key) {
    document.getElementById('hmac-results').innerHTML = '<p style="color:#ef4444;font-size:0.85rem;">テキストと秘密鍵を入力してください。</p>';
    return;
  }
  try {
    var enc = new TextEncoder();
    var algoMap = { 'SHA-1': 'SHA-1', 'SHA-256': 'SHA-256', 'SHA-384': 'SHA-384', 'SHA-512': 'SHA-512' };
    var algoName = algoMap[selectedHmacAlgo] || 'SHA-256';
    var cryptoKey = await crypto.subtle.importKey(
      'raw', enc.encode(key),
      { name: 'HMAC', hash: algoName },
      false, ['sign']
    );
    var sig = await crypto.subtle.sign('HMAC', cryptoKey, enc.encode(text));
    var hash = buf2hex(sig);
    document.getElementById('hmac-results').innerHTML = renderResult('hmac-results', 'HMAC-' + selectedHmacAlgo, hash, isHmacUppercase);
  } catch(e) {
    document.getElementById('hmac-results').innerHTML = '<p style="color:#ef4444;font-size:0.85rem;">エラーが発生しました: ' + e.message + '</p>';
  }
};

window.clearHmac = function() {
  document.getElementById('hmacText').value = '';
  document.getElementById('hmacKey').value = '';
  document.getElementById('hmac-results').innerHTML = '';
};

/* ===== COMPARE ===== */
window.compareHashes = function() {
  var h1 = document.getElementById('hash1').value.trim().toLowerCase();
  var h2 = document.getElementById('hash2').value.trim().toLowerCase();
  var result = document.getElementById('compareResult');
  if (!h1 || !h2) {
    result.style.display = 'none';
    alert('両方のハッシュ値を入力してください。');
    return;
  }
  result.style.display = 'block';
  if (h1 === h2) {
    result.className = 'compare-result match';
    result.textContent = 'ハッシュ値は一致しています';
  } else {
    result.className = 'compare-result mismatch';
    // Find first differing position
    var diffPos = -1;
    var len = Math.min(h1.length, h2.length);
    for (var i = 0; i < len; i++) {
      if (h1[i] !== h2[i]) { diffPos = i; break; }
    }
    var msg = 'ハッシュ値は一致しません';
    if (h1.length !== h2.length) msg += '（長さが異なります: ' + h1.length + ' vs ' + h2.length + '文字）';
    else if (diffPos >= 0) msg += '（位置 ' + diffPos + ' で不一致）';
    result.textContent = msg;
  }
};

window.clearCompare = function() {
  document.getElementById('hash1').value = '';
  document.getElementById('hash2').value = '';
  document.getElementById('compareResult').style.display = 'none';
};

})();
</script>

</div>

## ハッシュ関数とは

ハッシュ関数とは、任意の長さのデータを固定長のビット列（ハッシュ値・ダイジェスト）に変換する一方向性の数学的関数です。同じ入力からは常に同じハッシュ値が生成される一方、ハッシュ値から元のデータを復元することは計算上不可能です。この性質から、データの改ざん検知・パスワードの安全な保存・デジタル署名など、情報セキュリティの幅広い場面で利用されています。

ハッシュ関数の重要な特徴として「衝突耐性」があります。異なる2つの入力が同一のハッシュ値を生成してしまう「衝突」が実用上起こらないこと、また入力が1ビットでも変化すると出力のハッシュ値が大きく変わる「雪崩効果」があることが求められます。ファイルのダウンロード後に公式サイトのチェックサムと比較することで、通信中の改ざんや破損を即座に検出できます。

## 主要なハッシュアルゴリズム

**MD5（128ビット）** — 1991年に設計された最も広く普及したアルゴリズム。処理が高速ですが、衝突攻撃への脆弱性が発見されているため、セキュリティ用途よりもファイル整合性の簡易チェックや非セキュリティ用途のチェックサムとして使用されます。

**SHA-1（160ビット）** — NSAが設計し、SHA-0の改良版として1995年に標準化。長年SSL/TLSやGitの内部処理に利用されてきましたが、2017年にGoogleが衝突を実証（SHAttered攻撃）し、新規のセキュリティ用途には推奨されません。

**SHA-256（256ビット）** — SHA-2ファミリーの代表格で、現在最も推奨される標準的なハッシュアルゴリズム。ビットコインのブロックチェーン、TLS証明書、コード署名など現代のセキュリティインフラで広く採用されています。衝突耐性・第2原像耐性ともに強固です。

**SHA-512（512ビット）** — SHA-2ファミリーの中で最長の出力を持ち、64ビットアーキテクチャでの処理が最適化されています。より高いセキュリティマージンが求められる場面、たとえばパスワードハッシュや長期保存が必要なデジタル署名などに適しています。

## 関連ツール

> Base64のエンコード・デコード → [Base64エンコーダー](/ja/tools/base64-encoder/)

> 正規表現をテスト → [正規表現テスター](/ja/tools/regex-tester/)

> 安全なパスワードを生成 → [パスワード生成ツール](/ja/tools/password-generator/)

---

**データセキュリティも経理も万全に**

ファイルの整合性チェックと同じくらい、経理データの正確さも大切。クラウド会計ソフト「freee」なら、銀行レベルのセキュリティで安心して財務管理ができます。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
