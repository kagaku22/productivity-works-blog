---
title: "テキスト暗号化・復号ツール"
date: 2025-06-21
description: "無料のテキスト暗号化ツール。AES-256・シーザー暗号・ヴィジュネル暗号・XOR対応。すべてブラウザ内で処理、サーバー送信なし。"
categories: ["無料ツール"]
slug: "text-encryption"
ShowToc: false
cover:
  image: "/images/covers/text-encryption-ja.png"
  alt: "テキスト暗号化・復号ツール"
---

<div id="te-app">

<style>
#te-app {
  font-family: "Helvetica Neue", "Hiragino Sans", "Noto Sans JP", Arial, sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1e293b;
}
#te-app *, #te-app *::before, #te-app *::after {
  box-sizing: border-box;
}
/* ---- タブバー ---- */
#te-app .te-tab-bar {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 20px;
  overflow-x: auto;
}
#te-app .te-tab {
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
#te-app .te-tab.active { color: #7c3aed; border-bottom-color: #7c3aed; }
#te-app .te-tab:hover:not(.active) { color: #334155; }
/* ---- パネル ---- */
#te-app .te-panel { display: none; }
#te-app .te-panel.active { display: block; }
/* ---- カード ---- */
#te-app .te-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 18px 20px;
  margin-bottom: 16px;
}
/* ---- ラベル ---- */
#te-app .te-label {
  display: block;
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
}
/* ---- テキストエリア ---- */
#te-app .te-textarea {
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
#te-app .te-textarea:focus {
  outline: none;
  border-color: #7c3aed;
  box-shadow: 0 0 0 3px rgba(124,58,237,0.12);
}
/* ---- セレクト ---- */
#te-app .te-select {
  padding: 8px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 13px;
  background: #fff;
  color: #1e293b;
  cursor: pointer;
  transition: border-color 0.2s;
  min-width: 160px;
}
#te-app .te-select:focus { outline: none; border-color: #7c3aed; }
/* ---- 入力フィールド ---- */
#te-app .te-input {
  padding: 8px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 13px;
  font-family: "SFMono-Regular", Consolas, monospace;
  background: #fff;
  color: #1e293b;
  transition: border-color 0.2s, box-shadow 0.2s;
  width: 100%;
}
#te-app .te-input:focus {
  outline: none;
  border-color: #7c3aed;
  box-shadow: 0 0 0 3px rgba(124,58,237,0.12);
}
/* ---- コントロール行 ---- */
#te-app .te-row {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-end;
  gap: 10px;
  margin-bottom: 12px;
}
#te-app .te-field {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex: 1;
  min-width: 140px;
}
/* ---- モードトグル ---- */
#te-app .te-mode-group {
  display: flex;
  border: 1.5px solid #e2e8f0;
  border-radius: 7px;
  overflow: hidden;
  flex-shrink: 0;
}
#te-app .te-mode-btn {
  padding: 8px 16px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  border: none;
  background: #f1f5f9;
  color: #64748b;
  transition: background 0.15s, color 0.15s;
  line-height: 1;
}
#te-app .te-mode-btn.active { background: #7c3aed; color: #fff; }
#te-app .te-mode-btn:hover:not(.active) { background: #e2e8f0; }
/* ---- ボタン ---- */
#te-app .te-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 9px 18px;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  border: none;
  transition: background 0.18s, transform 0.1s;
  user-select: none;
  line-height: 1;
  white-space: nowrap;
}
#te-app .te-btn:active { transform: scale(0.97); }
#te-app .te-btn-primary   { background: #7c3aed; color: #fff; }
#te-app .te-btn-primary:hover { background: #6d28d9; }
#te-app .te-btn-secondary { background: #e2e8f0; color: #374151; }
#te-app .te-btn-secondary:hover { background: #cbd5e1; }
/* ---- 出力エリア ---- */
#te-app .te-output-wrap {
  display: none;
  margin-top: 4px;
}
#te-app .te-output-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 6px;
}
#te-app .te-output-label {
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
#te-app .te-output-ta {
  width: 100%;
  min-height: 100px;
  padding: 11px 13px;
  border: 1.5px solid #c4b5fd;
  border-radius: 8px;
  font-size: 14px;
  font-family: "SFMono-Regular", Consolas, monospace;
  resize: vertical;
  background: #faf5ff;
  color: #1e293b;
  word-break: break-all;
}
/* ---- ステータス ---- */
#te-app .te-status {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 9px 14px;
  border-radius: 8px;
  font-size: 13px;
  margin-bottom: 14px;
}
#te-app .te-status.ok   { background:#f0fdf4; border:1px solid #bbf7d0; color:#166534; }
#te-app .te-status.err  { background:#fef2f2; border:1px solid #fecaca; color:#991b1b; }
#te-app .te-status.hidden { display:none; }
/* ---- シフトスライダー ---- */
#te-app .te-shift-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#te-app .te-range {
  flex: 1;
  accent-color: #7c3aed;
  cursor: pointer;
}
#te-app .te-shift-val {
  min-width: 28px;
  text-align: center;
  font-weight: 700;
  font-size: 15px;
  color: #7c3aed;
}
/* ---- バッジ ---- */
#te-app .te-badge {
  display: inline-block;
  padding: 3px 9px;
  border-radius: 5px;
  font-size: 11px;
  font-weight: 700;
  white-space: nowrap;
  letter-spacing: 0.04em;
  background: #ede9fe;
  color: #5b21b6;
}
/* ---- コピーボタン ---- */
#te-app .te-copy {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  padding: 5px 12px;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  border: 1.5px solid #e2e8f0;
  background: #fff;
  color: #475569;
  transition: all 0.15s;
  white-space: nowrap;
}
#te-app .te-copy:hover   { border-color:#7c3aed; color:#7c3aed; background:#f5f3ff; }
#te-app .te-copy.copied  { border-color:#10b981; color:#10b981; background:#ecfdf5; }
/* ---- 説明ボックス ---- */
#te-app .te-info {
  padding: 12px 16px;
  background: #f5f3ff;
  border: 1px solid #ddd6fe;
  border-radius: 8px;
  font-size: 12.5px;
  color: #4c1d95;
  line-height: 1.7;
  margin-bottom: 14px;
}
/* ---- AES プログレス ---- */
#te-app .te-progress {
  display: none;
  align-items: center;
  gap: 10px;
  margin-top: 8px;
  font-size: 12px;
  color: #7c3aed;
}
#te-app .te-progress.visible { display: flex; }
#te-app .te-progress-track {
  flex: 1; height: 4px;
  background: #ede9fe;
  border-radius: 3px;
  overflow: hidden;
}
#te-app .te-progress-fill {
  height: 100%;
  background: #7c3aed;
  border-radius: 3px;
  width: 0%;
  transition: width 0.2s;
}
/* ---- トースト ---- */
.te-toast {
  position: fixed;
  bottom: 24px; right: 24px;
  background: #7c3aed; color: #fff;
  padding: 10px 18px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 700;
  z-index: 9999;
  box-shadow: 0 4px 16px rgba(0,0,0,0.18);
  transition: opacity 0.3s;
  font-family: "Helvetica Neue", Arial, sans-serif;
}
@media (max-width: 540px) {
  #te-app .te-mode-btn { padding: 8px 10px; font-size: 12px; }
  #te-app .te-tab { padding: 9px 12px; }
}
</style>

<!-- タブバー -->
<div class="te-tab-bar">
  <button class="te-tab active" onclick="teTab('caesar',this)">シーザー</button>
  <button class="te-tab" onclick="teTab('vigenere',this)">ヴィジュネル</button>
  <button class="te-tab" onclick="teTab('xor',this)">XOR</button>
  <button class="te-tab" onclick="teTab('aes',this)">AES-256</button>
</div>

<!-- ===== シーザー暗号パネル ===== -->
<div id="te-panel-caesar" class="te-panel active">
  <div class="te-card">
    <div class="te-info">
      シーザー暗号はアルファベットの各文字を固定シフト数だけずらします。暗号化・復号は同じシフト値を使います（復号は逆向きに適用）。英字以外の文字はそのまま保持されます。
    </div>
    <div class="te-row">
      <div class="te-field" style="max-width:260px">
        <span class="te-label">シフト数（1〜25）</span>
        <div class="te-shift-row">
          <input type="range" class="te-range" id="te-cs-range" min="1" max="25" value="13"
            oninput="document.getElementById('te-cs-val').textContent=this.value; teCaesarRun()">
          <span class="te-shift-val" id="te-cs-val">13</span>
        </div>
      </div>
      <div class="te-field">
        <span class="te-label">モード</span>
        <div class="te-mode-group">
          <button class="te-mode-btn active" id="te-cs-enc-btn" onclick="teSetMode('caesar','encrypt')">暗号化</button>
          <button class="te-mode-btn" id="te-cs-dec-btn" onclick="teSetMode('caesar','decrypt')">復号</button>
        </div>
      </div>
    </div>
    <span class="te-label">入力テキスト</span>
    <textarea id="te-cs-input" class="te-textarea" placeholder="テキストを入力してください…" oninput="teCaesarRun()"></textarea>
    <div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
      <button class="te-btn te-btn-primary" onclick="teCaesarRun()">&#128274; 実行</button>
      <button class="te-btn te-btn-secondary" onclick="teClearPanel('caesar')">クリア</button>
    </div>
  </div>
  <div class="te-status hidden" id="te-cs-status"></div>
  <div class="te-output-wrap" id="te-cs-output-wrap">
    <div class="te-output-header">
      <span class="te-output-label">結果 <span class="te-badge" id="te-cs-badge">暗号化済み</span></span>
      <button class="te-copy" id="te-cs-copy" onclick="teCopyOutput('te-cs-out',this)">&#128203; コピー</button>
    </div>
    <textarea id="te-cs-out" class="te-output-ta" readonly></textarea>
  </div>
</div>

<!-- ===== ヴィジュネル暗号パネル ===== -->
<div id="te-panel-vigenere" class="te-panel">
  <div class="te-card">
    <div class="te-info">
      ヴィジュネル暗号はキーワードを使って各文字に異なるシフトを適用します。キーワードが入力より短い場合は繰り返されます。A〜Z・a〜zのみがシフトされ、それ以外はそのまま出力されます。
    </div>
    <div class="te-row">
      <div class="te-field">
        <span class="te-label">キーワード（英字）</span>
        <input type="text" id="te-vig-key" class="te-input" placeholder="例: SECRET" oninput="teVigenereRun()">
      </div>
      <div class="te-field" style="flex:0;min-width:auto">
        <span class="te-label">モード</span>
        <div class="te-mode-group">
          <button class="te-mode-btn active" id="te-vig-enc-btn" onclick="teSetMode('vigenere','encrypt')">暗号化</button>
          <button class="te-mode-btn" id="te-vig-dec-btn" onclick="teSetMode('vigenere','decrypt')">復号</button>
        </div>
      </div>
    </div>
    <span class="te-label">入力テキスト</span>
    <textarea id="te-vig-input" class="te-textarea" placeholder="テキストを入力してください…" oninput="teVigenereRun()"></textarea>
    <div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
      <button class="te-btn te-btn-primary" onclick="teVigenereRun()">&#128274; 実行</button>
      <button class="te-btn te-btn-secondary" onclick="teClearPanel('vigenere')">クリア</button>
    </div>
  </div>
  <div class="te-status hidden" id="te-vig-status"></div>
  <div class="te-output-wrap" id="te-vig-output-wrap">
    <div class="te-output-header">
      <span class="te-output-label">結果 <span class="te-badge" id="te-vig-badge">暗号化済み</span></span>
      <button class="te-copy" id="te-vig-copy" onclick="teCopyOutput('te-vig-out',this)">&#128203; コピー</button>
    </div>
    <textarea id="te-vig-out" class="te-output-ta" readonly></textarea>
  </div>
</div>

<!-- ===== XOR 暗号パネル ===== -->
<div id="te-panel-xor" class="te-panel">
  <div class="te-card">
    <div class="te-info">
      XOR暗号は各文字バイトに対してキーとのビット単位排他的論理和（XOR）を適用します。同じキーを2回適用すると元のテキストに戻るため、暗号化と復号の操作は同一です。出力はBase64エンコードされます。
    </div>
    <div class="te-row">
      <div class="te-field">
        <span class="te-label">キー（任意のテキスト）</span>
        <input type="text" id="te-xor-key" class="te-input" placeholder="例: myKey123" oninput="teXorRun()">
      </div>
      <div class="te-field" style="flex:0;min-width:auto">
        <span class="te-label">モード</span>
        <div class="te-mode-group">
          <button class="te-mode-btn active" id="te-xor-enc-btn" onclick="teSetMode('xor','encrypt')">暗号化</button>
          <button class="te-mode-btn" id="te-xor-dec-btn" onclick="teSetMode('xor','decrypt')">復号</button>
        </div>
      </div>
    </div>
    <span class="te-label">入力テキスト</span>
    <textarea id="te-xor-input" class="te-textarea" placeholder="暗号化するテキスト、または復号するBase64暗号文…" oninput="teXorRun()"></textarea>
    <div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
      <button class="te-btn te-btn-primary" onclick="teXorRun()">&#128274; 実行</button>
      <button class="te-btn te-btn-secondary" onclick="teClearPanel('xor')">クリア</button>
    </div>
  </div>
  <div class="te-status hidden" id="te-xor-status"></div>
  <div class="te-output-wrap" id="te-xor-output-wrap">
    <div class="te-output-header">
      <span class="te-output-label">結果 <span class="te-badge" id="te-xor-badge">暗号化済み</span></span>
      <button class="te-copy" id="te-xor-copy" onclick="teCopyOutput('te-xor-out',this)">&#128203; コピー</button>
    </div>
    <textarea id="te-xor-out" class="te-output-ta" readonly></textarea>
  </div>
</div>

<!-- ===== AES-256 パネル ===== -->
<div id="te-panel-aes" class="te-panel">
  <div class="te-card">
    <div class="te-info">
      ブラウザ標準の <strong>Web Crypto API</strong> を使ったAES-256-GCM暗号化。パスワードからPBKDF2（SHA-256・10万回）でキーを導出し、ランダムなIV（96ビット）とソルト（128ビット）を毎回生成します。出力は <code>ソルト:IV:暗号文</code> のBase64形式。パスワードはブラウザ外に出ません。
    </div>
    <div class="te-row">
      <div class="te-field">
        <span class="te-label">パスワード</span>
        <input type="password" id="te-aes-pw" class="te-input" placeholder="強力なパスワードを入力…" oninput="teAesRun()">
      </div>
      <div class="te-field" style="flex:0;min-width:auto">
        <span class="te-label">モード</span>
        <div class="te-mode-group">
          <button class="te-mode-btn active" id="te-aes-enc-btn" onclick="teSetMode('aes','encrypt')">暗号化</button>
          <button class="te-mode-btn" id="te-aes-dec-btn" onclick="teSetMode('aes','decrypt')">復号</button>
        </div>
      </div>
    </div>
    <span class="te-label">入力テキスト</span>
    <textarea id="te-aes-input" class="te-textarea" placeholder="暗号化するテキスト、または復号するBase64暗号文…" oninput="teAesRun()"></textarea>
    <div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
      <button class="te-btn te-btn-primary" onclick="teAesRun()">&#128274; AES-256 実行</button>
      <button class="te-btn te-btn-secondary" onclick="teClearPanel('aes')">クリア</button>
    </div>
    <div class="te-progress" id="te-aes-prog">
      <span id="te-aes-prog-lbl">処理中…</span>
      <div class="te-progress-track"><div class="te-progress-fill" id="te-aes-prog-fill"></div></div>
    </div>
  </div>
  <div class="te-status hidden" id="te-aes-status"></div>
  <div class="te-output-wrap" id="te-aes-output-wrap">
    <div class="te-output-header">
      <span class="te-output-label">結果 <span class="te-badge" id="te-aes-badge">暗号化済み</span></span>
      <button class="te-copy" id="te-aes-copy" onclick="teCopyOutput('te-aes-out',this)">&#128203; コピー</button>
    </div>
    <textarea id="te-aes-out" class="te-output-ta" readonly></textarea>
  </div>
</div>

<script>
(function () {
'use strict';

/* ============================================================
   状態管理
   ============================================================ */
var teMode = { caesar: 'encrypt', vigenere: 'encrypt', xor: 'encrypt', aes: 'encrypt' };
var teAesDebounce = null;

/* ============================================================
   タブ切り替え
   ============================================================ */
window.teTab = function(name, btn) {
  document.querySelectorAll('#te-app .te-tab').forEach(function(t){ t.classList.remove('active'); });
  document.querySelectorAll('#te-app .te-panel').forEach(function(p){ p.classList.remove('active'); });
  btn.classList.add('active');
  document.getElementById('te-panel-'+name).classList.add('active');
};

/* ============================================================
   モード切り替え
   ============================================================ */
window.teSetMode = function(cipher, mode) {
  teMode[cipher] = mode;
  var prefix = cipher === 'caesar' ? 'cs' : cipher === 'vigenere' ? 'vig' : cipher === 'xor' ? 'xor' : 'aes';
  document.getElementById('te-'+prefix+'-enc-btn').classList.toggle('active', mode==='encrypt');
  document.getElementById('te-'+prefix+'-dec-btn').classList.toggle('active', mode==='decrypt');
  var badge = document.getElementById('te-'+prefix+'-badge');
  if (badge) badge.textContent = mode === 'encrypt' ? '暗号化済み' : '復号済み';
  if (cipher === 'caesar')   teCaesarRun();
  if (cipher === 'vigenere') teVigenereRun();
  if (cipher === 'xor')      teXorRun();
  if (cipher === 'aes')      teAesRun();
};

/* ============================================================
   ステータス・表示ヘルパー
   ============================================================ */
function teStatus(id, html, cls) {
  var el = document.getElementById(id);
  el.innerHTML = html;
  el.className = 'te-status ' + cls;
}
function teShowOutput(prefix, text, mode) {
  document.getElementById('te-'+prefix+'-out').value = text;
  document.getElementById('te-'+prefix+'-output-wrap').style.display = 'block';
  var badge = document.getElementById('te-'+prefix+'-badge');
  if (badge) badge.textContent = mode === 'encrypt' ? '暗号化済み' : '復号済み';
}
function teHideOutput(prefix) {
  document.getElementById('te-'+prefix+'-output-wrap').style.display = 'none';
}

/* ============================================================
   クリア
   ============================================================ */
window.teClearPanel = function(cipher) {
  var prefix = cipher === 'caesar' ? 'cs' : cipher === 'vigenere' ? 'vig' : cipher === 'xor' ? 'xor' : 'aes';
  if (cipher === 'caesar')   document.getElementById('te-cs-input').value = '';
  if (cipher === 'vigenere') document.getElementById('te-vig-input').value = '';
  if (cipher === 'xor')      document.getElementById('te-xor-input').value = '';
  if (cipher === 'aes')      document.getElementById('te-aes-input').value = '';
  teHideOutput(prefix);
  teStatus('te-'+prefix+'-status','','hidden');
};

/* ============================================================
   コピーヘルパー
   ============================================================ */
window.teCopyOutput = function(taId, btn) {
  var val = document.getElementById(taId).value;
  if (!val) return;
  navigator.clipboard.writeText(val).then(function() {
    btn.innerHTML = '&#10003; コピー済';
    btn.classList.add('copied');
    setTimeout(function(){ btn.innerHTML='&#128203; コピー'; btn.classList.remove('copied'); }, 1800);
  });
};

/* ============================================================
   シーザー暗号
   ============================================================ */
function caesarShift(text, shift, decrypt) {
  if (decrypt) shift = (26 - shift) % 26;
  var result = '';
  for (var i = 0; i < text.length; i++) {
    var c = text.charCodeAt(i);
    if (c >= 65 && c <= 90) {
      result += String.fromCharCode(((c - 65 + shift) % 26) + 65);
    } else if (c >= 97 && c <= 122) {
      result += String.fromCharCode(((c - 97 + shift) % 26) + 97);
    } else {
      result += text[i];
    }
  }
  return result;
}

window.teCaesarRun = function() {
  var text  = document.getElementById('te-cs-input').value;
  var shift = parseInt(document.getElementById('te-cs-range').value, 10);
  var mode  = teMode.caesar;
  if (!text) { teHideOutput('cs'); teStatus('te-cs-status','','hidden'); return; }
  var out = caesarShift(text, shift, mode === 'decrypt');
  teShowOutput('cs', out, mode);
  teStatus('te-cs-status', '&#10003; シフト' + shift + 'で' + (mode==='encrypt'?'暗号化':'復号') + 'しました', 'ok');
};

/* ============================================================
   ヴィジュネル暗号
   ============================================================ */
function vigenereProcess(text, key, decrypt) {
  if (!key) return text;
  key = key.toUpperCase().replace(/[^A-Z]/g, '');
  if (!key.length) return text;
  var result = '';
  var ki = 0;
  for (var i = 0; i < text.length; i++) {
    var c = text.charCodeAt(i);
    var k = key.charCodeAt(ki % key.length) - 65;
    if (c >= 65 && c <= 90) {
      var s1 = decrypt ? ((c - 65 - k + 26) % 26) : ((c - 65 + k) % 26);
      result += String.fromCharCode(s1 + 65);
      ki++;
    } else if (c >= 97 && c <= 122) {
      var s2 = decrypt ? ((c - 97 - k + 26) % 26) : ((c - 97 + k) % 26);
      result += String.fromCharCode(s2 + 97);
      ki++;
    } else {
      result += text[i];
    }
  }
  return result;
}

window.teVigenereRun = function() {
  var text = document.getElementById('te-vig-input').value;
  var key  = document.getElementById('te-vig-key').value;
  var mode = teMode.vigenere;
  if (!text) { teHideOutput('vig'); teStatus('te-vig-status','','hidden'); return; }
  if (!key || !key.replace(/[^A-Za-z]/g,'').length) {
    teStatus('te-vig-status','&#9888; キーワードを英字で入力してください。','err');
    teHideOutput('vig');
    return;
  }
  var out = vigenereProcess(text, key, mode === 'decrypt');
  teShowOutput('vig', out, mode);
  teStatus('te-vig-status', '&#10003; キー「' + key.toUpperCase().replace(/[^A-Z]/g,'') + '」で' + (mode==='encrypt'?'暗号化':'復号') + 'しました', 'ok');
};

/* ============================================================
   XOR 暗号
   ============================================================ */
function xorEncrypt(text, key) {
  if (!key) return text;
  var bytes = new TextEncoder().encode(text);
  var keyBytes = new TextEncoder().encode(key);
  var out = new Uint8Array(bytes.length);
  for (var i = 0; i < bytes.length; i++) {
    out[i] = bytes[i] ^ keyBytes[i % keyBytes.length];
  }
  return btoa(String.fromCharCode.apply(null, out));
}

function xorDecrypt(b64, key) {
  if (!key) return b64;
  try {
    var raw = atob(b64);
    var bytes = new Uint8Array(raw.length);
    for (var i = 0; i < raw.length; i++) bytes[i] = raw.charCodeAt(i);
    var keyBytes = new TextEncoder().encode(key);
    var out = new Uint8Array(bytes.length);
    for (var j = 0; j < bytes.length; j++) {
      out[j] = bytes[j] ^ keyBytes[j % keyBytes.length];
    }
    return new TextDecoder().decode(out);
  } catch(e) {
    throw new Error('Base64形式が不正です。XOR暗号化の出力をそのまま貼り付けてください。');
  }
}

window.teXorRun = function() {
  var text = document.getElementById('te-xor-input').value;
  var key  = document.getElementById('te-xor-key').value;
  var mode = teMode.xor;
  if (!text) { teHideOutput('xor'); teStatus('te-xor-status','','hidden'); return; }
  if (!key) {
    teStatus('te-xor-status','&#9888; キーを入力してください。','err');
    teHideOutput('xor');
    return;
  }
  try {
    var out = mode === 'encrypt' ? xorEncrypt(text, key) : xorDecrypt(text.trim(), key);
    teShowOutput('xor', out, mode);
    teStatus('te-xor-status', '&#10003; ' + (mode==='encrypt'?'暗号化しました（Base64出力）':'復号しました'), 'ok');
  } catch(e) {
    teStatus('te-xor-status', '&#10007; ' + e.message, 'err');
    teHideOutput('xor');
  }
};

/* ============================================================
   AES-256-GCM（Web Crypto API）
   ============================================================ */
function teAesShowProg(pct, msg) {
  var el = document.getElementById('te-aes-prog');
  el.classList.add('visible');
  document.getElementById('te-aes-prog-fill').style.width = pct + '%';
  document.getElementById('te-aes-prog-lbl').textContent  = msg;
}
function teAesHideProg() {
  document.getElementById('te-aes-prog').classList.remove('visible');
}

async function aesKeyFromPassword(password, salt) {
  var enc = new TextEncoder();
  var keyMaterial = await crypto.subtle.importKey(
    'raw', enc.encode(password), 'PBKDF2', false, ['deriveKey']
  );
  return crypto.subtle.deriveKey(
    { name: 'PBKDF2', salt: salt, iterations: 100000, hash: 'SHA-256' },
    keyMaterial,
    { name: 'AES-GCM', length: 256 },
    false,
    ['encrypt', 'decrypt']
  );
}

function buf2b64(buf) {
  return btoa(String.fromCharCode.apply(null, new Uint8Array(buf)));
}
function b64toBuf(b64) {
  var raw = atob(b64);
  var buf = new Uint8Array(raw.length);
  for (var i = 0; i < raw.length; i++) buf[i] = raw.charCodeAt(i);
  return buf;
}

async function aesEncrypt(plaintext, password) {
  var enc  = new TextEncoder();
  var salt = crypto.getRandomValues(new Uint8Array(16));
  var iv   = crypto.getRandomValues(new Uint8Array(12));
  var key  = await aesKeyFromPassword(password, salt);
  var cipherBuf = await crypto.subtle.encrypt(
    { name: 'AES-GCM', iv: iv },
    key,
    enc.encode(plaintext)
  );
  return buf2b64(salt) + ':' + buf2b64(iv) + ':' + buf2b64(cipherBuf);
}

async function aesDecrypt(encoded, password) {
  var parts = encoded.trim().split(':');
  if (parts.length !== 3) throw new Error('暗号文の形式が不正です。salt:iv:ciphertext 形式のBase64が必要です。');
  var salt      = b64toBuf(parts[0]);
  var iv        = b64toBuf(parts[1]);
  var cipherBuf = b64toBuf(parts[2]);
  var key = await aesKeyFromPassword(password, salt);
  var plainBuf = await crypto.subtle.decrypt(
    { name: 'AES-GCM', iv: iv },
    key,
    cipherBuf
  );
  return new TextDecoder().decode(plainBuf);
}

window.teAesRun = function() {
  clearTimeout(teAesDebounce);
  teAesDebounce = setTimeout(teAesRunNow, 300);
};

async function teAesRunNow() {
  var text = document.getElementById('te-aes-input').value;
  var pw   = document.getElementById('te-aes-pw').value;
  var mode = teMode.aes;
  if (!text) { teHideOutput('aes'); teStatus('te-aes-status','','hidden'); teAesHideProg(); return; }
  if (!pw) {
    teStatus('te-aes-status','&#9888; パスワードを入力してください。','err');
    teHideOutput('aes');
    return;
  }
  try {
    if (mode === 'encrypt') {
      teAesShowProg(30, 'PBKDF2 鍵導出中…');
      var cipher = await aesEncrypt(text, pw);
      teAesShowProg(100, '完了');
      setTimeout(teAesHideProg, 400);
      teShowOutput('aes', cipher, mode);
      teStatus('te-aes-status', '&#10003; AES-256-GCMで暗号化しました（PBKDF2鍵導出）', 'ok');
    } else {
      teAesShowProg(30, 'PBKDF2 鍵導出中…');
      var plain = await aesDecrypt(text, pw);
      teAesShowProg(100, '完了');
      setTimeout(teAesHideProg, 400);
      teShowOutput('aes', plain, mode);
      teStatus('te-aes-status', '&#10003; 復号に成功しました', 'ok');
    }
  } catch(e) {
    teAesHideProg();
    var msg = e.message || '不明なエラー';
    if (msg.indexOf('operation-specific') !== -1 || msg.indexOf('OperationError') !== -1 || msg.toLowerCase().indexOf('decrypt') !== -1) {
      msg = '復号に失敗しました — パスワードが違うか、暗号文が破損しています。';
    }
    teStatus('te-aes-status', '&#10007; ' + msg, 'err');
    teHideOutput('aes');
  }
}

})();
</script>

</div><!-- /#te-app -->

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f5f3ff 0%,#ede9fe 100%);border:1.5px solid #c4b5fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#5b21b6;font-weight:700;">個人・法人の確定申告・会計管理をかんたんに</p>
  <span style="font-size:13px;color:#4c1d95;line-height:1.7;">freee会計なら、クラウドで経費・請求・確定申告をワンストップ管理。無料トライアル実施中。</span><br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:8px;padding:9px 22px;background:#7c3aed;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

## 各暗号方式の解説

### シーザー暗号

シーザー暗号は最も古い暗号のひとつで、平文の各アルファベット文字を固定シフト数だけ後方（暗号化）または前方（復号）にずらします。シフト13の場合はROT13と呼ばれ、同じ操作を2回行うと元のテキストに戻ります。数字・記号・スペースはそのまま保持されます。

**強度:** 現代では非常に弱い暗号。シフト数は25通りしかなく、全探索は一瞬で完了します。

### ヴィジュネル暗号

ヴィジュネル暗号はキーワードを使い、各文字に異なるシフトを適用することでシーザー暗号を改良した方式です。キーワードが入力より短い場合は繰り返して使われます。単純な頻度分析は困難になりますが、カシスキー検定などでキー長を特定されると解読可能です。

**強度:** 歴史的に堅牢とされてきましたが、現代では解読されやすい方式です。学習・パズル用途に向いています。

### XOR暗号

XOR暗号は平文の各バイトとキーを繰り返しながらビット単位XOR演算します。XORは逆演算が自身と同一なので、同じキーを再度適用すれば元に戻ります。このツールでは出力をBase64でエンコードして可読性を保ちます。キーが平文と同じ長さの完全乱数（ワンタイムパッド）であれば理論上解読不可能ですが、短い繰り返しキーは既知平文攻撃に弱いです。

**強度:** キーの長さとランダム性に完全依存。長くランダムなキーを使う場合のみ実用的。

### AES-256-GCM

AES-256-GCMはブラウザ標準の **Web Crypto API**（`SubtleCrypto`）を用いた現代の業界標準対称暗号です。パスワードからPBKDF2（SHA-256・10万回・ランダムソルト）で256ビット鍵を導出し、暗号化ごとにランダムなIV（96ビット）を生成するため、同じ平文を2回暗号化しても異なる暗号文になります。出力はソルト・IV・暗号文をBase64コロン区切りで保存します。

**強度:** 長くランダムなパスワードを使えば非常に高い安全性。パスワードと平文はブラウザ外に出ません。

## プライバシーについて

本ツールでのすべての処理はブラウザ内で完結します。AES-256-GCMはブラウザネイティブの **Web Crypto API**（`SubtleCrypto`）を使用し、シーザー・ヴィジュネル・XORは純粋なJavaScriptで実装されています。入力データ・パスワードが外部に送信されることは一切ありません。

---

> 安全なランダムパスワードを生成 → [パスワード生成ツール](/ja/tools/password-generator/)

> MD5・SHA-256・SHA-512ハッシュを生成 → [ハッシュ生成ツール](/ja/tools/hash-generator/)

> ROT13・シーザー暗号をワンクリック変換 → [ROT13エンコーダー](/ja/tools/rot13-encoder/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
