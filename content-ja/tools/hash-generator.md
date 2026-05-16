---
title: "ハッシュ生成ツール"
date: 2025-05-16
description: "無料のハッシュジェネレーター。テキストやファイルからMD5・SHA-1・SHA-256・SHA-512ハッシュをブラウザで即生成。登録不要・完全クライアントサイド処理。"
categories: ["無料ツール"]
slug: "hash-generator"
ShowToc: false
cover:
  image: "/images/covers/hash-generator-ja.png"
  alt: "ハッシュ生成ツール"
---

<div id="hg-app">

<style>
#hg-app {
  font-family: "Helvetica Neue", "Hiragino Sans", "Noto Sans JP", Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  color: #1e293b;
}
#hg-app *, #hg-app *::before, #hg-app *::after {
  box-sizing: border-box;
}
/* ---- タブバー ---- */
#hg-app .hg-tab-bar {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 20px;
  overflow-x: auto;
}
#hg-app .hg-tab {
  padding: 9px 18px;
  font-size: 13px;
  font-weight: 700;
  color: #64748b;
  cursor: pointer;
  border: none;
  background: none;
  border-bottom: 2.5px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#hg-app .hg-tab.active { color: #6366f1; border-bottom-color: #6366f1; }
#hg-app .hg-tab:hover:not(.active) { color: #334155; }
/* ---- パネル ---- */
#hg-app .hg-panel { display: none; }
#hg-app .hg-panel.active { display: block; }
/* ---- カード ---- */
#hg-app .hg-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 18px 20px;
  margin-bottom: 16px;
}
/* ---- テキストエリア ---- */
#hg-app .hg-textarea {
  width: 100%;
  min-height: 110px;
  padding: 11px 13px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  font-family: "SFMono-Regular", Consolas, monospace;
  resize: vertical;
  background: #fff;
  color: #1e293b;
  transition: border-color 0.2s, box-shadow 0.2s;
}
#hg-app .hg-textarea:focus {
  outline: none;
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.13);
}
/* ---- コントロール行 ---- */
#hg-app .hg-row {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 10px;
  margin-top: 12px;
}
/* ---- ボタン ---- */
#hg-app .hg-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 8px 16px;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  border: none;
  transition: background 0.18s, transform 0.1s;
  user-select: none;
  line-height: 1;
}
#hg-app .hg-btn:active { transform: scale(0.97); }
#hg-app .hg-btn-primary   { background: #6366f1; color: #fff; }
#hg-app .hg-btn-primary:hover { background: #4f46e5; }
#hg-app .hg-btn-secondary { background: #e2e8f0; color: #374151; }
#hg-app .hg-btn-secondary:hover { background: #cbd5e1; }
/* ---- トグル ---- */
#hg-app .hg-toggle {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: #475569;
  cursor: pointer;
  user-select: none;
}
#hg-app .hg-toggle input[type=checkbox] {
  width: 15px; height: 15px;
  accent-color: #6366f1;
  cursor: pointer;
}
/* ---- プログレス ---- */
#hg-app .hg-progress {
  display: none;
  align-items: center;
  gap: 10px;
  margin-top: 10px;
  font-size: 12px;
  color: #6366f1;
}
#hg-app .hg-progress.visible { display: flex; }
#hg-app .hg-progress-track {
  flex: 1; height: 5px;
  background: #e0e7ff;
  border-radius: 3px;
  overflow: hidden;
}
#hg-app .hg-progress-fill {
  height: 100%;
  background: #6366f1;
  border-radius: 3px;
  width: 0%;
  transition: width 0.15s;
}
/* ---- ステータスバー ---- */
#hg-app .hg-status {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 9px 14px;
  border-radius: 8px;
  font-size: 13px;
  margin-bottom: 12px;
}
#hg-app .hg-status.ok  { background:#f0fdf4; border:1px solid #bbf7d0; color:#166534; }
#hg-app .hg-status.err { background:#fef2f2; border:1px solid #fecaca; color:#991b1b; }
#hg-app .hg-status.hidden { display: none; }
/* ---- ハッシュ結果テーブル ---- */
#hg-app .hg-results-header {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 8px;
}
#hg-app .hg-table-wrap {
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  overflow: hidden;
}
#hg-app .hg-table {
  width: 100%;
  border-collapse: collapse;
}
#hg-app .hg-table th {
  text-align: left;
  padding: 8px 12px;
  background: #f1f5f9;
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  border-bottom: 1.5px solid #e2e8f0;
}
#hg-app .hg-table td {
  padding: 11px 12px;
  border-bottom: 1px solid #f1f5f9;
  vertical-align: middle;
  font-size: 13px;
}
#hg-app .hg-table tr:last-child td { border-bottom: none; }
#hg-app .hg-table tr:hover td { background: #f8fafc; }
/* ---- アルゴリズムバッジ ---- */
#hg-app .hg-badge {
  display: inline-block;
  padding: 3px 9px;
  border-radius: 5px;
  font-size: 11px;
  font-weight: 700;
  white-space: nowrap;
  letter-spacing: 0.04em;
}
#hg-app .hg-badge-md5    { background:#fef3c7; color:#92400e; }
#hg-app .hg-badge-sha1   { background:#ede9fe; color:#5b21b6; }
#hg-app .hg-badge-sha256 { background:#d1fae5; color:#065f46; }
#hg-app .hg-badge-sha512 { background:#dbeafe; color:#1e40af; }
/* ---- ハッシュ値セル ---- */
#hg-app .hg-hash-val {
  font-family: "SFMono-Regular", Consolas, monospace;
  font-size: 12px;
  color: #334155;
  word-break: break-all;
  max-width: 420px;
}
#hg-app .hg-hash-meta {
  font-size: 11px;
  color: #94a3b8;
  white-space: nowrap;
}
/* ---- コピーボタン ---- */
#hg-app .hg-copy {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  padding: 4px 10px;
  border-radius: 5px;
  font-size: 11px;
  font-weight: 600;
  cursor: pointer;
  border: 1.5px solid #e2e8f0;
  background: #fff;
  color: #475569;
  transition: all 0.15s;
  white-space: nowrap;
}
#hg-app .hg-copy:hover  { border-color:#6366f1; color:#6366f1; background:#eef2ff; }
#hg-app .hg-copy.copied { border-color:#10b981; color:#10b981; background:#ecfdf5; }
/* ---- ファイルドロップゾーン ---- */
#hg-app .hg-dropzone {
  border: 2.5px dashed #c7d2fe;
  border-radius: 10px;
  padding: 32px 20px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
  background: #fafbff;
  color: #6366f1;
  font-size: 14px;
  font-weight: 500;
}
#hg-app .hg-dropzone:hover,
#hg-app .hg-dropzone.over { border-color:#6366f1; background:#eef2ff; }
#hg-app .hg-dropzone .hg-drop-icon { font-size: 34px; display: block; margin-bottom: 8px; }
#hg-app .hg-file-info {
  display: none;
  align-items: center;
  gap: 10px;
  padding: 9px 14px;
  background: #eff6ff;
  border: 1px solid #bfdbfe;
  border-radius: 8px;
  font-size: 13px;
  color: #1e40af;
  margin-top: 10px;
}
/* ---- ハッシュ比較 ---- */
#hg-app .hg-compare-label {
  display: block;
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 5px;
}
#hg-app .hg-compare-ta {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-family: "SFMono-Regular", Consolas, monospace;
  font-size: 12px;
  min-height: 58px;
  resize: vertical;
  background: #fff;
  color: #1e293b;
  transition: border-color 0.2s;
}
#hg-app .hg-compare-ta:focus { outline:none; border-color:#6366f1; }
#hg-app .hg-compare-result {
  padding: 10px 14px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  margin-top: 12px;
  display: none;
}
#hg-app .hg-compare-result.match    { background:#d1fae5; color:#065f46; border:1px solid #6ee7b7; }
#hg-app .hg-compare-result.no-match { background:#fee2e2; color:#991b1b; border:1px solid #fca5a5; }
/* ---- トースト ---- */
.hg-toast {
  position: fixed;
  bottom: 24px; right: 24px;
  background: #6366f1; color: #fff;
  padding: 10px 18px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 700;
  z-index: 9999;
  box-shadow: 0 4px 16px rgba(0,0,0,0.18);
  transition: opacity 0.3s;
  font-family: "Helvetica Neue", Arial, sans-serif;
}
@media (max-width: 580px) {
  #hg-app .hg-hash-val  { max-width: 150px; font-size: 10px; }
  #hg-app .hg-hash-meta { display: none; }
  #hg-app .hg-table th:nth-child(3),
  #hg-app .hg-table td:nth-child(3) { display: none; }
}
</style>

<!-- タブバー -->
<div class="hg-tab-bar">
  <button class="hg-tab active" onclick="hgTab('text',this)">テキスト入力</button>
  <button class="hg-tab" onclick="hgTab('file',this)">ファイルハッシュ</button>
  <button class="hg-tab" onclick="hgTab('compare',this)">ハッシュ比較</button>
</div>

<!-- ===== テキスト入力パネル ===== -->
<div id="hg-panel-text" class="hg-panel active">
  <div class="hg-card">
    <textarea id="hg-text" class="hg-textarea" placeholder="ハッシュ化するテキストをここに入力してください…（リアルタイムで生成されます）" oninput="hgLive()"></textarea>
    <div class="hg-row">
      <button class="hg-btn hg-btn-primary" onclick="hgGenAll()">ハッシュを生成</button>
      <button class="hg-btn hg-btn-secondary" onclick="hgClearText()">クリア</button>
      <label class="hg-toggle"><input type="checkbox" id="hg-uc" onchange="hgApplyCase()"> 大文字表示</label>
      <label class="hg-toggle"><input type="checkbox" id="hg-live" checked> リアルタイム更新</label>
    </div>
    <div class="hg-progress" id="hg-prog">
      <span id="hg-prog-lbl">計算中…</span>
      <div class="hg-progress-track"><div class="hg-progress-fill" id="hg-prog-fill"></div></div>
    </div>
  </div>
  <div class="hg-status hidden" id="hg-status"></div>
  <div id="hg-text-results" style="display:none">
    <div class="hg-results-header">
      <button class="hg-btn hg-btn-secondary" style="font-size:12px;padding:5px 13px" onclick="hgCopyAllText()">全てコピー</button>
    </div>
    <div class="hg-table-wrap">
      <table class="hg-table">
        <thead><tr><th>アルゴリズム</th><th>ハッシュ値</th><th>情報</th><th></th></tr></thead>
        <tbody id="hg-text-tbody"></tbody>
      </table>
    </div>
  </div>
</div>

<!-- ===== ファイルハッシュパネル ===== -->
<div id="hg-panel-file" class="hg-panel">
  <div class="hg-card">
    <div class="hg-dropzone" id="hg-dropzone"
      onclick="document.getElementById('hg-file-inp').click()"
      ondragover="hgDragOver(event)" ondragleave="hgDragLeave(event)" ondrop="hgDrop(event)">
      <span class="hg-drop-icon">&#128196;</span>
      <div>ここにファイルをドロップ、または<strong>クリックして選択</strong></div>
      <div style="font-size:12px;color:#94a3b8;margin-top:6px;">全ファイル形式対応 &bull; ブラウザ内で処理 &bull; サーバーへの送信なし</div>
    </div>
    <input type="file" id="hg-file-inp" style="display:none" onchange="hgFileSelected(this.files[0])">
    <div class="hg-file-info" id="hg-finfo">
      <span style="font-size:18px">&#128196;</span>
      <strong id="hg-fname"></strong>
      <span style="color:#93c5fd">|</span>
      <span id="hg-fsize" style="color:#3b82f6"></span>
    </div>
    <div class="hg-progress" id="hg-fprog" style="margin-top:12px">
      <span id="hg-fprog-lbl">ハッシュ計算中…</span>
      <div class="hg-progress-track"><div class="hg-progress-fill" id="hg-fprog-fill"></div></div>
    </div>
  </div>
  <div class="hg-status hidden" id="hg-fstatus"></div>
  <div id="hg-file-results" style="display:none">
    <div class="hg-results-header">
      <button class="hg-btn hg-btn-secondary" style="font-size:12px;padding:5px 13px" onclick="hgCopyAllFile()">全てコピー</button>
    </div>
    <div class="hg-table-wrap">
      <table class="hg-table">
        <thead><tr><th>アルゴリズム</th><th>ハッシュ値</th><th>情報</th><th></th></tr></thead>
        <tbody id="hg-file-tbody"></tbody>
      </table>
    </div>
  </div>
</div>

<!-- ===== ハッシュ比較パネル ===== -->
<div id="hg-panel-compare" class="hg-panel">
  <div class="hg-card">
    <p style="margin:0 0 14px;font-size:14px;color:#475569;line-height:1.7;">
      2つのハッシュ値を貼り付けて一致するか確認します。ダウンロードしたファイルの整合性チェックや、パスワードダイジェストの照合に便利です。
    </p>
    <label class="hg-compare-label">ハッシュ A</label>
    <textarea class="hg-compare-ta" id="hg-ca" placeholder="1つ目のハッシュを貼り付け…" oninput="hgCompare()"></textarea>
    <label class="hg-compare-label" style="margin-top:12px">ハッシュ B</label>
    <textarea class="hg-compare-ta" id="hg-cb" placeholder="2つ目のハッシュを貼り付け…" oninput="hgCompare()"></textarea>
    <div class="hg-compare-result" id="hg-cresult"></div>
    <div class="hg-row" style="margin-top:14px">
      <button class="hg-btn hg-btn-secondary" onclick="document.getElementById('hg-ca').value='';document.getElementById('hg-cb').value='';document.getElementById('hg-cresult').style.display='none'">クリア</button>
    </div>
  </div>
</div>

<script>
(function () {
'use strict';

/* ============================================================
   MD5 — 純粋 JS 実装 (RFC 1321)
   ============================================================ */
function md5(str) {
  function safeAdd(x,y){var l=(x&0xffff)+(y&0xffff);return((x>>16)+(y>>16)+(l>>16)<<16)|(l&0xffff);}
  function rol(n,c){return(n<<c)|(n>>>(32-c));}
  function cmn(q,a,b,x,s,t){return safeAdd(rol(safeAdd(safeAdd(a,q),safeAdd(x,t)),s),b);}
  function ff(a,b,c,d,x,s,t){return cmn((b&c)|(~b&d),a,b,x,s,t);}
  function gg(a,b,c,d,x,s,t){return cmn((b&d)|(c&~d),a,b,x,s,t);}
  function hh(a,b,c,d,x,s,t){return cmn(b^c^d,a,b,x,s,t);}
  function ii(a,b,c,d,x,s,t){return cmn(c^(b|~d),a,b,x,s,t);}
  function str2blks(s){
    var nblk=((s.length+8)>>6)+1,blks=new Array(nblk*16).fill(0),i;
    for(i=0;i<s.length;i++) blks[i>>2]|=s.charCodeAt(i)<<((i%4)*8);
    blks[s.length>>2]|=0x80<<((s.length%4)*8);
    blks[nblk*16-2]=s.length*8;
    return blks;
  }
  function hex(n){var h='',hx='0123456789abcdef',j;for(j=0;j<4;j++)h+=hx[(n>>(j*8+4))&0xf]+hx[(n>>(j*8))&0xf];return h;}
  var utf8=unescape(encodeURIComponent(str));
  var x=str2blks(utf8),a=1732584193,b=-271733879,c=-1732584194,d=271733878,i;
  for(i=0;i<x.length;i+=16){
    var oa=a,ob=b,oc=c,od=d;
    a=ff(a,b,c,d,x[i+ 0], 7,-680876936);  d=ff(d,a,b,c,x[i+ 1],12,-389564586);
    c=ff(c,d,a,b,x[i+ 2],17, 606105819);  b=ff(b,c,d,a,x[i+ 3],22,-1044525330);
    a=ff(a,b,c,d,x[i+ 4], 7,-176418897);  d=ff(d,a,b,c,x[i+ 5],12,1200080426);
    c=ff(c,d,a,b,x[i+ 6],17,-1473231341); b=ff(b,c,d,a,x[i+ 7],22,-45705983);
    a=ff(a,b,c,d,x[i+ 8], 7,1770035416);  d=ff(d,a,b,c,x[i+ 9],12,-1958414417);
    c=ff(c,d,a,b,x[i+10],17,-42063);       b=ff(b,c,d,a,x[i+11],22,-1990404162);
    a=ff(a,b,c,d,x[i+12], 7,1804603682);  d=ff(d,a,b,c,x[i+13],12,-40341101);
    c=ff(c,d,a,b,x[i+14],17,-1502002290); b=ff(b,c,d,a,x[i+15],22,1236535329);
    a=gg(a,b,c,d,x[i+ 1], 5,-165796510);  d=gg(d,a,b,c,x[i+ 6], 9,-1069501632);
    c=gg(c,d,a,b,x[i+11],14, 643717713);  b=gg(b,c,d,a,x[i+ 0],20,-373897302);
    a=gg(a,b,c,d,x[i+ 5], 5,-701558691);  d=gg(d,a,b,c,x[i+10], 9,38016083);
    c=gg(c,d,a,b,x[i+15],14,-660478335);  b=gg(b,c,d,a,x[i+ 4],20,-405537848);
    a=gg(a,b,c,d,x[i+ 9], 5, 568446438);  d=gg(d,a,b,c,x[i+14], 9,-1019803690);
    c=gg(c,d,a,b,x[i+ 3],14,-187363961);  b=gg(b,c,d,a,x[i+ 8],20,1163531501);
    a=gg(a,b,c,d,x[i+13], 5,-1444681467); d=gg(d,a,b,c,x[i+ 2], 9,-51403784);
    c=gg(c,d,a,b,x[i+ 7],14,1735328473);  b=gg(b,c,d,a,x[i+12],20,-1926607734);
    a=hh(a,b,c,d,x[i+ 5], 4,-378558);     d=hh(d,a,b,c,x[i+ 8],11,-2022574463);
    c=hh(c,d,a,b,x[i+11],16,1839030562);  b=hh(b,c,d,a,x[i+14],23,-35309556);
    a=hh(a,b,c,d,x[i+ 1], 4,-1530992060);d=hh(d,a,b,c,x[i+ 4],11,1272893353);
    c=hh(c,d,a,b,x[i+ 7],16,-155497632);  b=hh(b,c,d,a,x[i+10],23,-1094730640);
    a=hh(a,b,c,d,x[i+13], 4, 681279174);  d=hh(d,a,b,c,x[i+ 0],11,-358537222);
    c=hh(c,d,a,b,x[i+ 3],16,-722521979);  b=hh(b,c,d,a,x[i+ 6],23,76029189);
    a=hh(a,b,c,d,x[i+ 9], 4,-640364487);  d=hh(d,a,b,c,x[i+12],11,-421815835);
    c=hh(c,d,a,b,x[i+15],16, 530742520);  b=hh(b,c,d,a,x[i+ 2],23,-995338651);
    a=ii(a,b,c,d,x[i+ 0], 6,-198630844);  d=ii(d,a,b,c,x[i+ 7],10,1126891415);
    c=ii(c,d,a,b,x[i+14],15,-1416354905); b=ii(b,c,d,a,x[i+ 5],21,-57434055);
    a=ii(a,b,c,d,x[i+12], 6,1700485571);  d=ii(d,a,b,c,x[i+ 3],10,-1894986606);
    c=ii(c,d,a,b,x[i+10],15,-1051523);    b=ii(b,c,d,a,x[i+ 1],21,-2054922799);
    a=ii(a,b,c,d,x[i+ 8], 6,1873313359);  d=ii(d,a,b,c,x[i+15],10,-30611744);
    c=ii(c,d,a,b,x[i+ 6],15,-1560198380); b=ii(b,c,d,a,x[i+13],21,1309151649);
    a=ii(a,b,c,d,x[i+ 4], 6,-145523070);  d=ii(d,a,b,c,x[i+11],10,-1120210379);
    c=ii(c,d,a,b,x[i+ 2],15, 718787259);  b=ii(b,c,d,a,x[i+ 9],21,-343485551);
    a=safeAdd(a,oa);b=safeAdd(b,ob);c=safeAdd(c,oc);d=safeAdd(d,od);
  }
  return hex(a)+hex(b)+hex(c)+hex(d);
}

/* ============================================================
   SHA — Web Crypto API
   ============================================================ */
function buf2hex(buf) {
  return Array.from(new Uint8Array(buf)).map(function(b){ return b.toString(16).padStart(2,'0'); }).join('');
}
async function shaText(algo, text) {
  return buf2hex(await crypto.subtle.digest(algo, new TextEncoder().encode(text)));
}
async function shaBuf(algo, buf) {
  return buf2hex(await crypto.subtle.digest(algo, buf));
}

/* ============================================================
   状態
   ============================================================ */
var hgTextHashes = {};
var hgFileHashes = {};
var hgDebounce   = null;

var HG_ALGOS = [
  { key:'MD5',    label:'MD5',    bits:128, hexLen:32,  badge:'hg-badge-md5'    },
  { key:'SHA-1',  label:'SHA-1',  bits:160, hexLen:40,  badge:'hg-badge-sha1'   },
  { key:'SHA-256',label:'SHA-256',bits:256, hexLen:64,  badge:'hg-badge-sha256' },
  { key:'SHA-512',label:'SHA-512',bits:512, hexLen:128, badge:'hg-badge-sha512' }
];

/* ============================================================
   タブ切り替え
   ============================================================ */
window.hgTab = function(name, btn) {
  document.querySelectorAll('#hg-app .hg-tab').forEach(function(t){ t.classList.remove('active'); });
  document.querySelectorAll('#hg-app .hg-panel').forEach(function(p){ p.classList.remove('active'); });
  btn.classList.add('active');
  document.getElementById('hg-panel-'+name).classList.add('active');
};

/* ============================================================
   プログレス表示
   ============================================================ */
function hgShowProg(progId, fillId, lblId, pct, msg) {
  document.getElementById(progId).classList.add('visible');
  document.getElementById(fillId).style.width = pct+'%';
  document.getElementById(lblId).textContent  = msg;
}
function hgHideProg(progId) {
  document.getElementById(progId).classList.remove('visible');
}
function hgStatus(id, html, cls) {
  var el = document.getElementById(id);
  el.innerHTML = html;
  el.className = 'hg-status ' + cls;
}

/* ============================================================
   ハッシュテーブル描画
   ============================================================ */
function hgRenderTable(tbodyId, hashes, prefix) {
  var uc = document.getElementById('hg-uc') && document.getElementById('hg-uc').checked;
  var rows = '';
  HG_ALGOS.forEach(function(a) {
    var raw = hashes[a.key];
    if (!raw) return;
    var display = uc ? raw.toUpperCase() : raw.toLowerCase();
    var uid = prefix + a.key.replace(/-/g,'');
    rows += '<tr>'+
      '<td><span class="hg-badge '+a.badge+'">'+a.label+'</span></td>'+
      '<td><span class="hg-hash-val" id="'+uid+'">'+display+'</span></td>'+
      '<td><span class="hg-hash-meta">'+a.bits+' bits &bull; '+a.hexLen+' 文字</span></td>'+
      '<td><button class="hg-copy" onclick="hgCopy(\''+uid+'\',this)">&#128203; コピー</button></td>'+
      '</tr>';
  });
  document.getElementById(tbodyId).innerHTML = rows;
}

/* ============================================================
   コピー系
   ============================================================ */
window.hgCopy = function(spanId, btn) {
  var el = document.getElementById(spanId);
  if (!el) return;
  navigator.clipboard.writeText(el.textContent).then(function(){
    btn.innerHTML = '&#10003; コピー済';
    btn.classList.add('copied');
    setTimeout(function(){ btn.innerHTML='&#128203; コピー'; btn.classList.remove('copied'); }, 1800);
  });
};

function hgToast(msg) {
  var t = document.createElement('div');
  t.className   = 'hg-toast';
  t.textContent = msg;
  document.body.appendChild(t);
  setTimeout(function(){ t.style.opacity='0'; setTimeout(function(){ t.remove(); },300); }, 1700);
}

window.hgCopyAllText = function() {
  var uc = document.getElementById('hg-uc').checked;
  var lines = HG_ALGOS.map(function(a){
    var h = hgTextHashes[a.key]; if (!h) return '';
    return a.label+':  '+(uc ? h.toUpperCase() : h.toLowerCase());
  }).filter(Boolean).join('\n');
  navigator.clipboard.writeText(lines).then(function(){ hgToast('全ハッシュをコピーしました'); });
};

window.hgCopyAllFile = function() {
  var uc = document.getElementById('hg-uc').checked;
  var lines = HG_ALGOS.map(function(a){
    var h = hgFileHashes[a.key]; if (!h) return '';
    return a.label+':  '+(uc ? h.toUpperCase() : h.toLowerCase());
  }).filter(Boolean).join('\n');
  navigator.clipboard.writeText(lines).then(function(){ hgToast('全ハッシュをコピーしました'); });
};

/* ============================================================
   大文字/小文字切り替え
   ============================================================ */
window.hgApplyCase = function() {
  if (Object.keys(hgTextHashes).length) hgRenderTable('hg-text-tbody', hgTextHashes, 'hgt-');
  if (Object.keys(hgFileHashes).length) hgRenderTable('hg-file-tbody', hgFileHashes, 'hgf-');
};

/* ============================================================
   テキストハッシュ生成
   ============================================================ */
window.hgLive = function() {
  if (!document.getElementById('hg-live').checked) return;
  clearTimeout(hgDebounce);
  hgDebounce = setTimeout(hgGenAll, 350);
};

window.hgGenAll = async function() {
  var text = document.getElementById('hg-text').value;
  if (!text) {
    document.getElementById('hg-text-results').style.display = 'none';
    hgStatus('hg-status','','hidden');
    return;
  }
  try {
    hgShowProg('hg-prog','hg-prog-fill','hg-prog-lbl', 10,'MD5 計算中…');
    var md5h    = md5(text);
    hgShowProg('hg-prog','hg-prog-fill','hg-prog-lbl', 35,'SHA-1 計算中…');
    var sha1h   = await shaText('SHA-1', text);
    hgShowProg('hg-prog','hg-prog-fill','hg-prog-lbl', 60,'SHA-256 計算中…');
    var sha256h = await shaText('SHA-256', text);
    hgShowProg('hg-prog','hg-prog-fill','hg-prog-lbl', 85,'SHA-512 計算中…');
    var sha512h = await shaText('SHA-512', text);
    hgShowProg('hg-prog','hg-prog-fill','hg-prog-lbl',100,'完了');
    setTimeout(function(){ hgHideProg('hg-prog'); }, 400);

    hgTextHashes = {'MD5':md5h,'SHA-1':sha1h,'SHA-256':sha256h,'SHA-512':sha512h};
    hgRenderTable('hg-text-tbody', hgTextHashes, 'hgt-');
    document.getElementById('hg-text-results').style.display = 'block';
    hgStatus('hg-status','&#10003; '+text.length+'文字のハッシュを生成しました','ok');
  } catch(e) {
    hgHideProg('hg-prog');
    hgStatus('hg-status','エラー: '+e.message,'err');
  }
};

window.hgClearText = function() {
  document.getElementById('hg-text').value = '';
  document.getElementById('hg-text-results').style.display = 'none';
  hgStatus('hg-status','','hidden');
  hgTextHashes = {};
};

/* ============================================================
   ファイルハッシュ
   ============================================================ */
window.hgDragOver  = function(e){ e.preventDefault(); document.getElementById('hg-dropzone').classList.add('over'); };
window.hgDragLeave = function()  { document.getElementById('hg-dropzone').classList.remove('over'); };
window.hgDrop      = function(e) {
  e.preventDefault();
  document.getElementById('hg-dropzone').classList.remove('over');
  var f = e.dataTransfer.files[0];
  if (f) hgFileSelected(f);
};

window.hgFileSelected = async function(file) {
  if (!file) return;
  document.getElementById('hg-finfo').style.display = 'flex';
  document.getElementById('hg-fname').textContent   = file.name;
  document.getElementById('hg-fsize').textContent   = hgFmtBytes(file.size);
  document.getElementById('hg-file-results').style.display = 'none';
  hgStatus('hg-fstatus','','hidden');

  try {
    hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl', 5,'ファイル読み込み中…');
    var buf = await new Promise(function(res, rej) {
      var r = new FileReader();
      r.onprogress = function(ev){
        if (ev.lengthComputable)
          hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl', Math.round(ev.loaded/ev.total*30),'読み込み中…');
      };
      r.onload  = function(ev){ res(ev.target.result); };
      r.onerror = rej;
      r.readAsArrayBuffer(file);
    });

    hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl', 35,'MD5 計算中…');
    var md5h    = hgMd5Buf(buf);
    hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl', 52,'SHA-1 計算中…');
    var sha1h   = await shaBuf('SHA-1',   buf);
    hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl', 70,'SHA-256 計算中…');
    var sha256h = await shaBuf('SHA-256',  buf);
    hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl', 88,'SHA-512 計算中…');
    var sha512h = await shaBuf('SHA-512',  buf);
    hgShowProg('hg-fprog','hg-fprog-fill','hg-fprog-lbl',100,'完了');
    setTimeout(function(){ hgHideProg('hg-fprog'); }, 400);

    hgFileHashes = {'MD5':md5h,'SHA-1':sha1h,'SHA-256':sha256h,'SHA-512':sha512h};
    hgRenderTable('hg-file-tbody', hgFileHashes, 'hgf-');
    document.getElementById('hg-file-results').style.display = 'block';
    hgStatus('hg-fstatus','&#10003; ハッシュ完了: '+file.name+' ('+hgFmtBytes(file.size)+')','ok');
  } catch(e) {
    hgHideProg('hg-fprog');
    hgStatus('hg-fstatus','ファイル読み込みエラー: '+e.message,'err');
  }
};

function hgMd5Buf(buffer) {
  var bytes = new Uint8Array(buffer), s = '';
  for (var i = 0; i < bytes.length; i++) s += String.fromCharCode(bytes[i]);
  return md5(s);
}

function hgFmtBytes(n) {
  if (n<1024)       return n+' B';
  if (n<1048576)    return (n/1024).toFixed(1)+' KB';
  if (n<1073741824) return (n/1048576).toFixed(2)+' MB';
  return (n/1073741824).toFixed(2)+' GB';
}

/* ============================================================
   ハッシュ比較
   ============================================================ */
window.hgCompare = function() {
  var a = document.getElementById('hg-ca').value.trim().toLowerCase();
  var b = document.getElementById('hg-cb').value.trim().toLowerCase();
  var res = document.getElementById('hg-cresult');
  if (!a || !b) { res.style.display='none'; return; }
  res.style.display = 'block';
  if (a === b) {
    res.className = 'hg-compare-result match';
    res.innerHTML = '&#10003; ハッシュ値は一致しています（'+a.length*4+' bits）';
  } else {
    res.className = 'hg-compare-result no-match';
    var pos = -1;
    for (var i=0; i<Math.min(a.length,b.length); i++) { if(a[i]!==b[i]){ pos=i; break; } }
    var msg = '&#10007; ハッシュ値は一致しません。';
    if (a.length!==b.length) msg += '長さが異なります（'+a.length+' vs '+b.length+' 文字）。';
    else if (pos>=0)         msg += '位置 '+(pos+1)+' で最初の不一致。';
    res.innerHTML = msg;
  }
};

})();
</script>

</div><!-- /#hg-app -->

---

<div class="hg-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">開発業務の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、開発ツール・サーバー費用の経費精算もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

## ハッシュ関数とは？

**暗号学的ハッシュ関数**とは、任意の長さのデータを固定長のビット列（ダイジェスト）に変換する一方向性の演算です。同じ入力からは常に同じハッシュ値が得られますが、1ビットでも変化すると出力の約半分が変わります（雪崩効果）。ハッシュ値から元データを復元することは計算上不可能です。

| アルゴリズム | 出力長 | 現状 | 主な用途 |
|------------|-------|------|---------|
| MD5 | 128 bits / 32 hex | 廃止推奨 | チェックサム・非セキュリティ用途 |
| SHA-1 | 160 bits / 40 hex | 廃止推奨 (SHAttered 2017) | レガシーシステム・Git |
| SHA-256 | 256 bits / 64 hex | 現行標準 | TLS証明書・ビットコイン・コード署名 |
| SHA-512 | 512 bits / 128 hex | 現行標準 | 高セキュリティ用途・64bit最適化 |

## 使い方

**テキスト入力** — テキストを入力するとリアルタイムでハッシュが生成されます。「大文字表示」で16進数の大文字/小文字を切り替えられます。「全てコピー」でラベル付きのテキストとして一括コピーも可能です。

**ファイルハッシュ** — ファイルをドロップゾーンにドラッグ＆ドロップするか、クリックしてファイルを選択します。ブラウザの `FileReader` API と `SubtleCrypto` でローカル処理するため、ファイルがサーバーに送信されることは一切ありません。ダウンロードしたファイルの公式チェックサムとの照合に最適です。

**ハッシュ比較** — 2つのダイジェスト文字列を貼り付けて、一致するか即座に確認できます。不一致の場合は最初の差異が何文字目かも表示されます。

## プライバシーについて

本ツールでの計算はすべてブラウザ内で完結します。SHA-1/SHA-256/SHA-512 はブラウザネイティブの **Web Crypto API**（`SubtleCrypto`）を使用し、MD5 は純粋な JavaScript で実装されています。入力データが外部に送信されることはありません。

---

> テキストのエンコード/デコード → [万能エンコーダー/デコーダー](/ja/tools/encoder-decoder/)

> JWTトークンを解析してヘッダーとクレームを確認 → [JWTデコーダー](/ja/tools/jwt-decoder/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
