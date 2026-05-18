---
title: "バイナリ⇔テキスト変換ツール"
date: 2025-05-12
description: "テキストをバイナリに、バイナリをテキストにリアルタイム変換。UTF-8・Unicode対応、16進数・8進数出力、文字ごとの詳細表示つき。無料オンラインツール。"
categories: ["無料ツール"]
tags: ["バイナリ", "テキスト変換", "binary to text", "text to binary", "16進数", "8進数", "開発ツール", "エンコーディング"]
slug: "binary-text-converter"
aliases: ["/ja/tools/binary-text-converter/", "/ja/tools/binary-converter/"]
cover:
  image: "/images/covers/binary-text-converter-ja.png"
  alt: "バイナリ⇔テキスト変換ツール"
ShowToc: false
---

<div id="btc-app">

<style>
#btc-app {
  font-family: ui-sans-serif, system-ui, -apple-system, sans-serif;
  color: #e2e8f0;
  max-width: 900px;
  margin: 0 auto;
  padding: 0;
}
#btc-app * { box-sizing: border-box; }

.btc-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 16px;
}

.btc-row {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  align-items: center;
  margin-bottom: 16px;
}

.btc-label {
  font-size: 13px;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.btc-label-text { color: #94a3b8; }

.btc-char-count {
  font-size: 12px;
  font-weight: 400;
  color: #64748b;
  text-transform: none;
  letter-spacing: 0;
}

.btc-textarea {
  width: 100%;
  min-height: 120px;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  font-family: 'Courier New', Courier, monospace;
  font-size: 14px;
  padding: 12px;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  line-height: 1.6;
}
.btc-textarea:focus { border-color: #6366f1; }
.btc-textarea::placeholder { color: #475569; }

.btc-btn {
  padding: 9px 18px;
  border-radius: 7px;
  border: none;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  white-space: nowrap;
}
.btc-btn:active { transform: scale(0.97); }

.btc-btn-primary {
  background: #6366f1;
  color: #fff;
}
.btc-btn-primary:hover { background: #4f46e5; }

.btc-btn-secondary {
  background: #334155;
  color: #cbd5e1;
}
.btc-btn-secondary:hover { background: #475569; }

.btc-btn-copy {
  background: #0f4c81;
  color: #93c5fd;
  padding: 5px 12px;
  font-size: 12px;
  border-radius: 6px;
}
.btc-btn-copy:hover { background: #1d4ed8; color: #fff; }
.btc-btn-copy.copied { background: #065f46; color: #6ee7b7; }

.btc-mode-group {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.btc-mode-btn {
  padding: 7px 14px;
  border-radius: 6px;
  border: 1.5px solid #334155;
  background: #0f172a;
  color: #94a3b8;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
.btc-mode-btn.active {
  border-color: #6366f1;
  background: #312e81;
  color: #a5b4fc;
}
.btc-mode-btn:hover:not(.active) { border-color: #6366f1; color: #e2e8f0; }

.btc-toggle-group {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: #94a3b8;
}

.btc-toggle {
  position: relative;
  width: 40px;
  height: 22px;
  flex-shrink: 0;
}
.btc-toggle input { opacity: 0; width: 0; height: 0; }
.btc-toggle-slider {
  position: absolute;
  inset: 0;
  background: #334155;
  border-radius: 22px;
  cursor: pointer;
  transition: background 0.2s;
}
.btc-toggle-slider::before {
  content: '';
  position: absolute;
  width: 16px; height: 16px;
  left: 3px; top: 3px;
  background: #94a3b8;
  border-radius: 50%;
  transition: transform 0.2s, background 0.2s;
}
.btc-toggle input:checked + .btc-toggle-slider { background: #4f46e5; }
.btc-toggle input:checked + .btc-toggle-slider::before {
  transform: translateX(18px);
  background: #fff;
}

.btc-output-box {
  position: relative;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 14px;
  min-height: 100px;
  font-family: 'Courier New', Courier, monospace;
  font-size: 13px;
  color: #a5b4fc;
  word-break: break-all;
  line-height: 1.7;
  white-space: pre-wrap;
}

.btc-error {
  color: #f87171;
  font-size: 13px;
  margin-top: 6px;
  min-height: 18px;
}

.btc-section-title {
  font-size: 15px;
  font-weight: 700;
  color: #c7d2fe;
  margin: 0 0 14px 0;
}

.btc-dir-arrows {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin: 4px 0 4px;
}
.btc-dir-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 10px 22px;
  border-radius: 8px;
  border: none;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
}
.btc-dir-btn:active { transform: scale(0.97); }
.btc-dir-btn-encode {
  background: #6366f1;
  color: #fff;
}
.btc-dir-btn-encode:hover { background: #4f46e5; }
.btc-dir-btn-decode {
  background: #0891b2;
  color: #fff;
}
.btc-dir-btn-decode:hover { background: #0e7490; }

/* Breakdown table */
.btc-table-wrap {
  overflow-x: auto;
  margin-top: 8px;
}
.btc-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
.btc-table th {
  background: #0f172a;
  color: #94a3b8;
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  padding: 8px 10px;
  text-align: left;
  border-bottom: 1px solid #334155;
}
.btc-table td {
  padding: 7px 10px;
  border-bottom: 1px solid #1e293b;
  font-family: 'Courier New', Courier, monospace;
  color: #e2e8f0;
  vertical-align: middle;
}
.btc-table tr:hover td { background: #1e2d3d; }
.btc-table .td-char {
  font-size: 15px;
  font-weight: 700;
  color: #fbbf24;
  min-width: 32px;
}
.btc-table .td-cp { color: #94a3b8; font-size: 12px; }
.btc-table .td-bin { color: #a5b4fc; }
.btc-table .td-hex { color: #34d399; }
.btc-table .td-oct { color: #fb923c; }
.btc-table .td-dec { color: #e2e8f0; }

.btc-empty-msg {
  text-align: center;
  color: #475569;
  font-size: 13px;
  padding: 20px 0;
}

.btc-options-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 10px;
  margin-bottom: 16px;
}

.btc-badge {
  display: inline-block;
  padding: 2px 8px;
  border-radius: 4px;
  font-size: 11px;
  font-weight: 700;
  margin-left: 6px;
  vertical-align: middle;
}
.btc-badge-bin { background: #312e81; color: #a5b4fc; }
.btc-badge-hex { background: #064e3b; color: #34d399; }
.btc-badge-oct { background: #431407; color: #fb923c; }

@media (max-width: 600px) {
  .btc-dir-arrows { flex-direction: column; align-items: stretch; }
  .btc-dir-btn { justify-content: center; }
  .btc-row { flex-direction: column; align-items: flex-start; }
  .btc-options-grid { grid-template-columns: 1fr; }
}
</style>

<!-- ===== 入力カード ===== -->
<div class="btc-card">
  <p class="btc-section-title">テキスト入力</p>

  <!-- 出力モード -->
  <div class="btc-row" style="margin-bottom:10px;">
    <span style="font-size:12px;color:#64748b;font-weight:600;margin-right:4px;">出力形式：</span>
    <div class="btc-mode-group">
      <button class="btc-mode-btn active" data-mode="bin" onclick="btcSetMode('bin')">バイナリ <span class="btc-badge btc-badge-bin">01</span></button>
      <button class="btc-mode-btn" data-mode="hex" onclick="btcSetMode('hex')">16進数 <span class="btc-badge btc-badge-hex">0x</span></button>
      <button class="btc-mode-btn" data-mode="oct" onclick="btcSetMode('oct')">8進数 <span class="btc-badge btc-badge-oct">0o</span></button>
    </div>
    <div style="flex:1"></div>
    <label class="btc-toggle-group" title="コード単位間にスペースを挿入">
      <span>スペース区切り</span>
      <span class="btc-toggle">
        <input type="checkbox" id="btcSpaces" checked onchange="btcRun()">
        <span class="btc-toggle-slider"></span>
      </span>
    </label>
  </div>

  <div class="btc-label">
    <span class="btc-label-text">テキスト</span>
    <span class="btc-char-count" id="btcInCount">0 文字</span>
  </div>
  <textarea class="btc-textarea" id="btcTextIn" placeholder="テキストを入力または貼り付け…" oninput="btcEncodeRun()" rows="5"></textarea>

  <div class="btc-dir-arrows" style="margin-top:14px;">
    <button class="btc-dir-btn btc-dir-btn-encode" onclick="btcEncodeRun()">&#x21D3; テキスト → エンコード</button>
  </div>

  <div class="btc-label" style="margin-top:14px;">
    <span class="btc-label-text" id="btcOutLabel">バイナリ出力</span>
    <button class="btc-btn btc-btn-copy" id="btcCopyEnc" onclick="btcCopy('btcEncOut','btcCopyEnc')">コピー</button>
  </div>
  <div class="btc-output-box" id="btcEncOut" style="min-height:80px;"></div>
</div>

<!-- ===== デコードカード ===== -->
<div class="btc-card">
  <p class="btc-section-title">デコード（エンコード → テキスト）</p>

  <div class="btc-label">
    <span class="btc-label-text" id="btcDecInLabel">バイナリ / 16進数 / 8進数 を入力</span>
    <button class="btc-btn btc-btn-copy" id="btcCopyDec" onclick="btcCopy('btcDecOut','btcCopyDec')">結果をコピー</button>
  </div>
  <textarea class="btc-textarea" id="btcBinIn" placeholder="エンコード済み文字列を貼り付け（バイナリ・16進・8進に対応）…" oninput="btcDecodeRun()" rows="4"></textarea>
  <div class="btc-error" id="btcDecErr"></div>

  <div class="btc-dir-arrows" style="margin-top:10px;">
    <button class="btc-dir-btn btc-dir-btn-decode" onclick="btcDecodeRun()">&#x21D1; エンコード → テキスト</button>
  </div>

  <div class="btc-label" style="margin-top:14px;">
    <span class="btc-label-text">デコード結果</span>
  </div>
  <div class="btc-output-box" id="btcDecOut" style="color:#e2e8f0;min-height:60px;"></div>
</div>

<!-- ===== 文字ごとの内訳カード ===== -->
<div class="btc-card">
  <p class="btc-section-title">文字ごとの詳細内訳</p>
  <div class="btc-table-wrap">
    <table class="btc-table">
      <thead>
        <tr>
          <th>文字</th>
          <th>コードポイント</th>
          <th>10進数</th>
          <th class="td-bin">バイナリ（UTF-8バイト列）</th>
          <th class="td-hex">16進数</th>
          <th class="td-oct">8進数</th>
        </tr>
      </thead>
      <tbody id="btcTableBody">
        <tr><td colspan="6" class="btc-empty-msg">上にテキストを入力すると、文字ごとの内訳が表示されます。</td></tr>
      </tbody>
    </table>
  </div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function(){
  var _mode = 'bin';

  function setMode(m){
    _mode = m;
    document.querySelectorAll('#btc-app .btc-mode-btn').forEach(function(b){
      b.classList.toggle('active', b.dataset.mode === m);
    });
    var labels = { bin: 'バイナリ出力', hex: '16進数出力', oct: '8進数出力' };
    document.getElementById('btcOutLabel').textContent = labels[m];
    btcEncodeRun();
  }
  window.btcSetMode = setMode;

  function spaces(){ return document.getElementById('btcSpaces').checked; }

  /* ---- UTF-8 encode a single code point → array of bytes ---- */
  function cpToUtf8Bytes(cp){
    if(cp < 0x80)   return [cp];
    if(cp < 0x800)  return [0xC0|(cp>>6), 0x80|(cp&0x3F)];
    if(cp < 0x10000)return [0xE0|(cp>>12), 0x80|((cp>>6)&0x3F), 0x80|(cp&0x3F)];
    return [0xF0|(cp>>18), 0x80|((cp>>12)&0x3F), 0x80|((cp>>6)&0x3F), 0x80|(cp&0x3F)];
  }

  function byteToBin(b){ return b.toString(2).padStart(8,'0'); }
  function byteToHex(b){ return b.toString(16).padStart(2,'0').toUpperCase(); }
  function byteToOct(b){ return b.toString(8).padStart(3,'0'); }

  function encodeText(text){
    var sp = spaces();
    var parts = [];
    for(var i=0;i<text.length;){
      var cp = text.codePointAt(i);
      var bytes = cpToUtf8Bytes(cp);
      var unit;
      if(_mode==='bin'){
        unit = bytes.map(byteToBin).join(sp?' ':'');
      } else if(_mode==='hex'){
        unit = bytes.map(byteToHex).join(sp?' ':'');
      } else {
        unit = bytes.map(byteToOct).join(sp?' ':'');
      }
      parts.push(unit);
      i += cp > 0xFFFF ? 2 : 1;
    }
    return parts.join(sp ? '  ' : ' ');
  }

  /* ---- Decode binary string → text ---- */
  function decodeBin(str){
    var tokens = str.trim().split(/\s+/).filter(function(t){ return t.length>0; });
    var allBytes = [];
    for(var i=0;i<tokens.length;i++){
      var t = tokens[i];
      if(!/^[01]+$/.test(t)) throw new Error('不正なバイナリ値: "'+t+'"');
      if(t.length % 8 !== 0) throw new Error('ビット数が8の倍数ではありません（'+t.length+'ビット: "'+t+'"）');
      for(var j=0;j<t.length;j+=8){
        allBytes.push(parseInt(t.slice(j,j+8),2));
      }
    }
    return utf8BytesToString(allBytes);
  }

  /* ---- Decode hex string → text ---- */
  function decodeHex(str){
    var tokens = str.trim().split(/\s+/).filter(function(t){ return t.length>0; });
    var allBytes = [];
    for(var i=0;i<tokens.length;i++){
      var t = tokens[i].replace(/^0x/i,'');
      if(!/^[0-9a-fA-F]+$/.test(t)) throw new Error('不正な16進数値: "'+t+'"');
      if(t.length % 2 !== 0) throw new Error('16進数の桁数が偶数ではありません: "'+t+'"');
      for(var j=0;j<t.length;j+=2){
        allBytes.push(parseInt(t.slice(j,j+2),16));
      }
    }
    return utf8BytesToString(allBytes);
  }

  /* ---- Decode octal string → text ---- */
  function decodeOct(str){
    var tokens = str.trim().split(/\s+/).filter(function(t){ return t.length>0; });
    var allBytes = [];
    for(var i=0;i<tokens.length;i++){
      var t = tokens[i].replace(/^0o/i,'');
      if(!/^[0-7]+$/.test(t)) throw new Error('不正な8進数値: "'+t+'"');
      if(t.length % 3 !== 0) throw new Error('8進数の桁数が3の倍数ではありません: "'+t+'"');
      for(var j=0;j<t.length;j+=3){
        allBytes.push(parseInt(t.slice(j,j+3),8));
      }
    }
    return utf8BytesToString(allBytes);
  }

  /* ---- UTF-8 bytes → JS string ---- */
  function utf8BytesToString(bytes){
    var result = '';
    var i = 0;
    while(i < bytes.length){
      var b = bytes[i];
      var cp, extra;
      if((b & 0x80) === 0){ cp = b; extra = 0; }
      else if((b & 0xE0) === 0xC0){ cp = b & 0x1F; extra = 1; }
      else if((b & 0xF0) === 0xE0){ cp = b & 0x0F; extra = 2; }
      else if((b & 0xF8) === 0xF0){ cp = b & 0x07; extra = 3; }
      else throw new Error('不正なUTF-8バイト: 0x'+b.toString(16));
      for(var j=1;j<=extra;j++){
        if(i+j >= bytes.length) throw new Error('UTF-8シーケンスが途中で終わっています');
        cp = (cp<<6) | (bytes[i+j] & 0x3F);
      }
      result += String.fromCodePoint(cp);
      i += 1 + extra;
    }
    return result;
  }

  /* ---- Auto-detect mode from decode input ---- */
  function detectMode(str){
    var s = str.trim();
    if(/^[01\s]+$/.test(s)) return 'bin';
    if(/^[0-9a-fA-F\s]+$/.test(s)) return 'hex';
    if(/^[0-7\s]+$/.test(s)) return 'oct';
    return null;
  }

  /* ---- Encode run ---- */
  window.btcEncodeRun = function(){
    var text = document.getElementById('btcTextIn').value;
    document.getElementById('btcInCount').textContent = [...text].length + ' 文字';
    var out = document.getElementById('btcEncOut');
    if(!text){ out.textContent = ''; buildTable([]); return; }
    out.textContent = encodeText(text);
    buildTable(getCharData(text));
  };

  /* ---- Decode run ---- */
  window.btcDecodeRun = function(){
    var raw = document.getElementById('btcBinIn').value;
    var err = document.getElementById('btcDecErr');
    var out = document.getElementById('btcDecOut');
    err.textContent = '';
    out.textContent = '';
    if(!raw.trim()) return;
    try{
      var m = detectMode(raw);
      var result;
      if(m==='bin') result = decodeBin(raw);
      else if(m==='hex') result = decodeHex(raw);
      else if(m==='oct') result = decodeOct(raw);
      else throw new Error('エンコード形式を検出できませんでした。');
      out.textContent = result;
    } catch(e){
      err.textContent = 'エラー: ' + e.message;
    }
  };

  window.btcRun = function(){ btcEncodeRun(); btcDecodeRun(); };

  /* ---- Clipboard copy ---- */
  window.btcCopy = function(srcId, btnId){
    var text = document.getElementById(srcId).textContent;
    if(!text) return;
    var btn = document.getElementById(btnId);
    navigator.clipboard.writeText(text).then(function(){
      var orig = btn.textContent;
      btn.textContent = 'コピー済み!';
      btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = orig; btn.classList.remove('copied'); }, 1800);
    }).catch(function(){
      var ta = document.createElement('textarea');
      ta.value = text; ta.style.position='fixed'; ta.style.opacity='0';
      document.body.appendChild(ta); ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      var orig = btn.textContent;
      btn.textContent = 'コピー済み!'; btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = orig; btn.classList.remove('copied'); }, 1800);
    });
  };

  /* ---- Build breakdown table ---- */
  function getCharData(text){
    var chars = [];
    for(var i=0;i<text.length;){
      var cp = text.codePointAt(i);
      var bytes = cpToUtf8Bytes(cp);
      chars.push({ ch: String.fromCodePoint(cp), cp: cp, bytes: bytes });
      i += cp > 0xFFFF ? 2 : 1;
    }
    return chars;
  }

  function buildTable(chars){
    var tb = document.getElementById('btcTableBody');
    if(!chars.length){
      tb.innerHTML = '<tr><td colspan="6" class="btc-empty-msg">上にテキストを入力すると、文字ごとの内訳が表示されます。</td></tr>';
      return;
    }
    var limit = 200;
    var rows = '';
    var shown = Math.min(chars.length, limit);
    for(var i=0;i<shown;i++){
      var c = chars[i];
      var binStr = c.bytes.map(byteToBin).join(' ');
      var hexStr = c.bytes.map(byteToHex).join(' ');
      var octStr = c.bytes.map(byteToOct).join(' ');
      var display = c.ch === ' ' ? '&nbsp;(スペース)' : c.ch === '\n' ? '&#x21B5;(改行)' : c.ch === '\t' ? '&#x21B9;(TAB)' : escHtml(c.ch);
      rows += '<tr>'
        + '<td class="td-char">'+display+'</td>'
        + '<td class="td-cp">U+'+c.cp.toString(16).toUpperCase().padStart(4,'0')+'</td>'
        + '<td class="td-dec">'+c.cp+'</td>'
        + '<td class="td-bin">'+binStr+'</td>'
        + '<td class="td-hex">'+hexStr+'</td>'
        + '<td class="td-oct">'+octStr+'</td>'
        + '</tr>';
    }
    if(chars.length > limit){
      rows += '<tr><td colspan="6" class="btc-empty-msg">… さらに '+(chars.length-limit)+' 文字あります（先頭'+limit+'文字を表示中）</td></tr>';
    }
    tb.innerHTML = rows;
  }

  function escHtml(s){
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }
})();
</script>

---

### 関連ツール
> 進数変換 → [進数変換ツール](/ja/tools/number-base-converter/)
> Base64エンコード → [Base64エンコーダー](/ja/tools/base64-encoder/)
> モールス信号 → [モールス信号変換](/ja/tools/morse-code/)
---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
</div>
