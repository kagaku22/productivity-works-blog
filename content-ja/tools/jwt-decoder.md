---
title: "JWTデコーダー — トークン解析ツール"
date: 2025-05-16
description: "JWTトークンを即座にデコード・検査。ヘッダー・ペイロード・クレームを有効期限チェック付きで表示。クライアントサイド処理のみ、データ送信なし。"
categories: ["無料ツール"]
slug: "jwt-decoder"
ShowToc: false
aliases:
  - "/ja/tools/jwt-decoder/"
  - "/ja/tools/jwt-decoder/"
cover:
  image: "/images/covers/jwt-decoder-ja.png"
  alt: "JWTデコーダー"
---

<div id="jwt-app">

<style>
#jwt-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Segoe UI", sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 12px;
  box-sizing: border-box;
}
#jwt-app * {
  box-sizing: border-box;
}
#jwt-app .jwt-notice {
  background: #fff8e1;
  border: 1px solid #ffe082;
  border-radius: 6px;
  padding: 10px 14px;
  font-size: 0.85rem;
  color: #6d4c00;
  margin-bottom: 18px;
  display: flex;
  align-items: flex-start;
  gap: 8px;
}
#jwt-app .jwt-notice-icon {
  font-size: 1.1rem;
  flex-shrink: 0;
  margin-top: 1px;
}
#jwt-app .jwt-input-label {
  font-weight: 600;
  font-size: 0.9rem;
  margin-bottom: 6px;
  color: #222;
}
#jwt-app textarea#jwt-input {
  width: 100%;
  min-height: 110px;
  padding: 12px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.82rem;
  border: 2px solid #d0d0d0;
  border-radius: 8px;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  background: #fafafa;
  color: #1a1a1a;
  line-height: 1.5;
}
#jwt-app textarea#jwt-input:focus {
  border-color: #1a73e8;
  background: #fff;
}
#jwt-app .jwt-actions-row {
  display: flex;
  gap: 10px;
  margin-top: 10px;
  flex-wrap: wrap;
}
#jwt-app .jwt-btn {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 600;
  transition: background 0.15s, opacity 0.15s;
}
#jwt-app .jwt-btn-primary {
  background: #1a73e8;
  color: #fff;
}
#jwt-app .jwt-btn-primary:hover {
  background: #1558b0;
}
#jwt-app .jwt-btn-secondary {
  background: #f1f3f4;
  color: #333;
  border: 1px solid #ccc;
}
#jwt-app .jwt-btn-secondary:hover {
  background: #e2e5e8;
}
#jwt-app .jwt-btn-danger {
  background: #fce8e6;
  color: #c5221f;
  border: 1px solid #f5c6c4;
}
#jwt-app .jwt-btn-danger:hover {
  background: #f5c6c4;
}
#jwt-app .jwt-structure-box {
  margin: 18px 0 10px;
  padding: 12px 14px;
  background: #1e1e2e;
  border-radius: 8px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.82rem;
  word-break: break-all;
  line-height: 1.6;
  display: none;
}
#jwt-app .jwt-structure-box.visible {
  display: block;
}
#jwt-app .jwt-part-header-color {
  color: #f28b82;
}
#jwt-app .jwt-part-sep {
  color: #aaa;
  margin: 0 1px;
}
#jwt-app .jwt-part-payload-color {
  color: #81c995;
}
#jwt-app .jwt-part-sig-color {
  color: #8ab4f8;
}
#jwt-app .jwt-status-bar {
  display: none;
  margin: 12px 0;
  padding: 10px 14px;
  border-radius: 6px;
  font-size: 0.88rem;
  font-weight: 600;
  align-items: center;
  gap: 8px;
}
#jwt-app .jwt-status-bar.visible {
  display: flex;
}
#jwt-app .jwt-status-bar.valid {
  background: #e6f4ea;
  color: #1e6e35;
  border: 1px solid #a8d5b5;
}
#jwt-app .jwt-status-bar.expired {
  background: #fce8e6;
  color: #c5221f;
  border: 1px solid #f5c6c4;
}
#jwt-app .jwt-status-bar.no-exp {
  background: #e8f0fe;
  color: #1a55b0;
  border: 1px solid #aac4f8;
}
#jwt-app .jwt-panels {
  display: none;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-top: 16px;
}
#jwt-app .jwt-panels.visible {
  display: grid;
}
@media (max-width: 600px) {
  #jwt-app .jwt-panels.visible {
    grid-template-columns: 1fr;
  }
}
#jwt-app .jwt-panel {
  border: 1px solid #dde1e7;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
}
#jwt-app .jwt-panel-header {
  padding: 8px 12px;
  font-weight: 700;
  font-size: 0.8rem;
  letter-spacing: 0.04em;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
#jwt-app .jwt-panel-header-alg {
  font-size: 0.72rem;
  font-weight: 500;
  opacity: 0.85;
  margin-left: 6px;
}
#jwt-app .jwt-panel.panel-header .jwt-panel-header {
  background: #fde8e7;
  color: #b31412;
  border-bottom: 1px solid #f5c6c4;
}
#jwt-app .jwt-panel.panel-payload .jwt-panel-header {
  background: #e6f4ea;
  color: #1a6b31;
  border-bottom: 1px solid #a8d5b5;
}
#jwt-app .jwt-panel.panel-signature .jwt-panel-header {
  background: #e8f0fe;
  color: #1a55b0;
  border-bottom: 1px solid #aac4f8;
}
#jwt-app .jwt-panel.panel-signature {
  grid-column: 1 / -1;
}
#jwt-app .jwt-panel-body {
  padding: 12px;
}
#jwt-app pre.jwt-json {
  margin: 0;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.8rem;
  white-space: pre-wrap;
  word-break: break-all;
  line-height: 1.6;
  color: #1a1a1a;
  background: none;
  border: none;
  padding: 0;
}
#jwt-app .jwt-copy-btn {
  font-size: 0.72rem;
  padding: 3px 8px;
  border-radius: 4px;
  background: rgba(255,255,255,0.7);
  border: 1px solid rgba(0,0,0,0.12);
  cursor: pointer;
  white-space: nowrap;
  transition: background 0.15s;
  color: inherit;
  font-weight: 600;
}
#jwt-app .jwt-copy-btn:hover {
  background: rgba(255,255,255,0.95);
}
#jwt-app .jwt-claims-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.8rem;
  margin-top: 8px;
}
#jwt-app .jwt-claims-table th {
  text-align: left;
  font-weight: 600;
  color: #555;
  padding: 4px 8px 4px 0;
  border-bottom: 1px solid #eee;
  white-space: nowrap;
}
#jwt-app .jwt-claims-table td {
  padding: 5px 8px 5px 0;
  border-bottom: 1px solid #f5f5f5;
  vertical-align: top;
  color: #222;
}
#jwt-app .jwt-claims-table td.claim-name {
  font-family: "SFMono-Regular", Consolas, monospace;
  color: #1a73e8;
  font-weight: 600;
  white-space: nowrap;
}
#jwt-app .jwt-claims-table td.claim-desc {
  color: #777;
  font-style: italic;
}
#jwt-app .jwt-sig-hex {
  font-family: "SFMono-Regular", Consolas, monospace;
  font-size: 0.78rem;
  word-break: break-all;
  color: #333;
  padding: 8px;
  background: #f8f9fa;
  border-radius: 4px;
  border: 1px solid #e0e0e0;
}
#jwt-app .jwt-sig-note {
  margin-top: 8px;
  font-size: 0.78rem;
  color: #888;
  font-style: italic;
}
#jwt-app .jwt-error-box {
  display: none;
  background: #fce8e6;
  border: 1px solid #f5c6c4;
  border-radius: 6px;
  padding: 10px 14px;
  color: #c5221f;
  font-size: 0.85rem;
  margin-top: 10px;
}
#jwt-app .jwt-error-box.visible {
  display: block;
}
#jwt-app .jwt-empty-state {
  text-align: center;
  color: #aaa;
  font-size: 0.9rem;
  padding: 32px 0 16px;
  display: block;
}
#jwt-app .jwt-empty-state.hidden {
  display: none;
}
#jwt-app .sh-key { color: #c62828; }
#jwt-app .sh-str { color: #2e7d32; }
#jwt-app .sh-num { color: #1565c0; }
#jwt-app .sh-bool { color: #6a1b9a; }
#jwt-app .sh-null { color: #bf360c; }
/* freee CTA */
#jwt-app .jwt-freee-cta {
  margin-top: 32px;
  padding: 20px 22px;
  background: linear-gradient(135deg, #e8f5e9 0%, #e3f2fd 100%);
  border: 1px solid #b2dfdb;
  border-radius: 10px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
  flex-wrap: wrap;
}
#jwt-app .jwt-freee-cta-icon {
  font-size: 2rem;
  flex-shrink: 0;
}
#jwt-app .jwt-freee-cta-body {
  flex: 1;
  min-width: 220px;
}
#jwt-app .jwt-freee-cta-body strong {
  display: block;
  font-size: 0.95rem;
  color: #1b5e20;
  margin-bottom: 4px;
}
#jwt-app .jwt-freee-cta-body p {
  margin: 0 0 10px;
  font-size: 0.84rem;
  color: #2e4057;
  line-height: 1.55;
}
#jwt-app .jwt-freee-cta-link {
  display: inline-block;
  background: #00c853;
  color: #fff;
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 700;
  padding: 8px 18px;
  border-radius: 6px;
  transition: background 0.15s;
}
#jwt-app .jwt-freee-cta-link:hover {
  background: #00a845;
  color: #fff;
}
</style>

<div class="jwt-notice">
  <span class="jwt-notice-icon">&#x1F512;</span>
  <span><strong>プライバシー保護:</strong> すべてのデコード処理はブラウザ内のJavaScriptで完結します。トークンがサーバーに送信されることは一切ありません。署名の検証は行いません — このツールは内容の確認専用です。</span>
</div>

<div class="jwt-input-label">JWTトークンを貼り付け</div>
<textarea id="jwt-input" placeholder="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" spellcheck="false" autocomplete="off" autocorrect="off" autocapitalize="off"></textarea>

<div class="jwt-actions-row">
  <button class="jwt-btn jwt-btn-secondary" id="jwt-sample-btn">サンプルJWTを読み込む</button>
  <button class="jwt-btn jwt-btn-danger" id="jwt-clear-btn">クリア</button>
</div>

<div class="jwt-error-box" id="jwt-error"></div>

<div class="jwt-structure-box" id="jwt-structure"></div>
<div class="jwt-status-bar" id="jwt-status"></div>

<span class="jwt-empty-state" id="jwt-empty">上のフォームにJWTを貼り付けると解析結果が表示されます</span>

<div class="jwt-panels" id="jwt-panels">
  <div class="jwt-panel panel-header">
    <div class="jwt-panel-header">
      <span>ヘッダー <span class="jwt-panel-header-alg" id="jwt-alg-badge"></span></span>
      <button class="jwt-copy-btn" data-target="header">JSONをコピー</button>
    </div>
    <div class="jwt-panel-body">
      <pre class="jwt-json" id="jwt-header-json"></pre>
    </div>
  </div>

  <div class="jwt-panel panel-payload">
    <div class="jwt-panel-header">
      <span>ペイロード</span>
      <button class="jwt-copy-btn" data-target="payload">JSONをコピー</button>
    </div>
    <div class="jwt-panel-body">
      <pre class="jwt-json" id="jwt-payload-json"></pre>
    </div>
  </div>

  <div class="jwt-panel panel-signature">
    <div class="jwt-panel-header">
      <span>署名</span>
      <button class="jwt-copy-btn" data-target="signature">Hexをコピー</button>
    </div>
    <div class="jwt-panel-body">
      <div class="jwt-sig-hex" id="jwt-sig-hex"></div>
      <div class="jwt-sig-note">署名バイト列を16進数で表示しています。検証にはシークレットキーまたは公開鍵が必要であり、このツールでは検証を行いません。</div>
    </div>
  </div>
</div>

<div id="jwt-claims-section" style="display:none; margin-top:20px;">
  <div class="jwt-input-label" style="margin-bottom:8px;">標準クレームの説明</div>
  <table class="jwt-claims-table" id="jwt-claims-table">
    <thead>
      <tr>
        <th>クレーム</th>
        <th>値</th>
        <th>説明</th>
      </tr>
    </thead>
    <tbody></tbody>
  </table>
</div>

<div class="jwt-freee-cta">
  <div class="jwt-freee-cta-icon">&#x1F4CA;</div>
  <div class="jwt-freee-cta-body">
    <strong>freee会計 — 中小企業・フリーランス向けクラウド会計</strong>
    <p>請求書・経費・確定申告をひとつにまとめて自動化。JWTを使うAPIとの連携もかんたん。無料トライアルでお試しください。</p>
    <a class="jwt-freee-cta-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す &rarr;</a>
  </div>
</div>

<script>
(function() {
  var SAMPLE = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJ1c2VyXzEyMzQ1NiIsIm5hbWUiOiLlsbHnlJ_lkI3lpKkiLCJlbWFpbCI6InVzZXJAZXhhbXBsZS5jb20iLCJpc3MiOiJodHRwczovL2F1dGguZXhhbXBsZS5jb20iLCJhdWQiOiJodHRwczovL2FwaS5leGFtcGxlLmNvbSIsImlhdCI6MTcxNjIzOTAyMiwibmJmIjoxNzE2MjM5MDIyLCJleHAiOjQ4NzAyMzkwMjIsImp0aSI6ImFiY2RlZjEyMzQ1Njc4OTAifQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c";

  var CLAIM_DEFS = {
    iss: "Issuer（発行者）— トークンを発行したサービス",
    sub: "Subject（主体）— このトークンが表すユーザーID等",
    aud: "Audience（受信者）— トークンの利用を想定した対象",
    exp: "Expiration Time（有効期限）— この時刻以降は無効（Unixタイムスタンプ）",
    nbf: "Not Before（有効開始）— この時刻より前は無効（Unixタイムスタンプ）",
    iat: "Issued At（発行日時）— トークンが発行された日時（Unixタイムスタンプ）",
    jti: "JWT ID（一意識別子）— このトークン固有のID（リプレイ防止等に使用）"
  };

  var stored = { header: null, payload: null, sig: null };

  function b64urlDecode(str) {
    str = str.replace(/-/g, '+').replace(/_/g, '/');
    while (str.length % 4 !== 0) str += '=';
    try { return atob(str); } catch(e) { return null; }
  }

  function b64urlToHex(str) {
    var raw = b64urlDecode(str);
    if (!raw) return null;
    var hex = '';
    for (var i = 0; i < raw.length; i++) {
      var b = raw.charCodeAt(i).toString(16);
      hex += (b.length === 1 ? '0' : '') + b;
    }
    return hex;
  }

  function escapeHtml(s) {
    return String(s)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }

  function syntaxHighlight(json) {
    var escaped = escapeHtml(json);
    return escaped.replace(/("(\\u[a-fA-F0-9]{4}|\\[^u]|[^\\"])*"(\s*:)?|\b(true|false|null)\b|-?\d+(?:\.\d*)?(?:[eE][+\-]?\d+)?)/g, function(match) {
      var cls = 'sh-num';
      if (/^"/.test(match)) {
        if (/:$/.test(match)) cls = 'sh-key';
        else cls = 'sh-str';
      } else if (/true|false/.test(match)) {
        cls = 'sh-bool';
      } else if (/null/.test(match)) {
        cls = 'sh-null';
      }
      return '<span class="' + cls + '">' + match + '</span>';
    });
  }

  function formatTs(ts) {
    try {
      var d = new Date(ts * 1000);
      return d.toLocaleString('ja-JP', { timeZone: 'Asia/Tokyo', year: 'numeric', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit', second: '2-digit' }) + ' JST';
    } catch(e) { return String(ts); }
  }

  function truncate(s, n) {
    s = String(s);
    return s.length > n ? s.slice(0, n) + '...' : s;
  }

  function decodeJwt(raw) {
    raw = raw.trim();
    if (!raw) return null;
    var parts = raw.split('.');
    if (parts.length !== 3) return { error: '不正なJWT: ドット区切りで3パートが必要ですが、' + parts.length + 'パートが検出されました。' };
    var headerRaw = b64urlDecode(parts[0]);
    if (!headerRaw) return { error: 'ヘッダーのBase64urlデコードに失敗しました。' };
    var payloadRaw = b64urlDecode(parts[1]);
    if (!payloadRaw) return { error: 'ペイロードのBase64urlデコードに失敗しました。' };
    var headerObj, payloadObj;
    try { headerObj = JSON.parse(headerRaw); } catch(e) { return { error: 'ヘッダーが有効なJSONではありません: ' + e.message }; }
    try { payloadObj = JSON.parse(payloadRaw); } catch(e) { return { error: 'ペイロードが有効なJSONではありません: ' + e.message }; }
    var sigHex = b64urlToHex(parts[2]);
    return { header: headerObj, payload: payloadObj, sigHex: sigHex, parts: parts };
  }

  function humanDuration(secs) {
    if (secs < 60) return secs + '秒';
    if (secs < 3600) return Math.floor(secs / 60) + '分' + (secs % 60) + '秒';
    if (secs < 86400) return Math.floor(secs / 3600) + '時間' + Math.floor((secs % 3600) / 60) + '分';
    return Math.floor(secs / 86400) + '日' + Math.floor((secs % 86400) / 3600) + '時間';
  }

  function render(raw) {
    var errorEl = document.getElementById('jwt-error');
    var structEl = document.getElementById('jwt-structure');
    var statusEl = document.getElementById('jwt-status');
    var panelsEl = document.getElementById('jwt-panels');
    var emptyEl = document.getElementById('jwt-empty');
    var claimsSec = document.getElementById('jwt-claims-section');

    errorEl.classList.remove('visible');
    structEl.classList.remove('visible');
    statusEl.classList.remove('visible', 'valid', 'expired', 'no-exp');
    panelsEl.classList.remove('visible');
    claimsSec.style.display = 'none';
    emptyEl.classList.remove('hidden');

    raw = (raw || '').trim();
    if (!raw) {
      stored.header = null; stored.payload = null; stored.sig = null;
      return;
    }

    var result = decodeJwt(raw);
    if (result.error) {
      errorEl.textContent = result.error;
      errorEl.classList.add('visible');
      stored.header = null; stored.payload = null; stored.sig = null;
      return;
    }

    emptyEl.classList.add('hidden');
    stored.header = result.header;
    stored.payload = result.payload;
    stored.sig = result.sigHex;

    // Structure visualization
    var p = result.parts;
    structEl.innerHTML =
      '<span style="color:#aaa;font-size:0.75rem;display:block;margin-bottom:4px;">トークン構造（header.payload.signature）</span>' +
      '<span class="jwt-part-header-color">' + escapeHtml(truncate(p[0], 60)) + '</span>' +
      '<span class="jwt-part-sep">.</span>' +
      '<span class="jwt-part-payload-color">' + escapeHtml(truncate(p[1], 80)) + '</span>' +
      '<span class="jwt-part-sep">.</span>' +
      '<span class="jwt-part-sig-color">' + escapeHtml(truncate(p[2], 60)) + '</span>';
    structEl.classList.add('visible');

    // Expiration status
    var now = Math.floor(Date.now() / 1000);
    var pl = result.payload;
    if (pl.exp !== undefined) {
      var exp = Number(pl.exp);
      if (now > exp) {
        var ago = now - exp;
        statusEl.innerHTML = '&#x274C; トークンは<strong>期限切れ</strong>です &mdash; ' + humanDuration(ago) + '前に失効 (' + formatTs(exp) + ')';
        statusEl.classList.add('visible', 'expired');
      } else {
        var rem = exp - now;
        statusEl.innerHTML = '&#x2705; トークンは<strong>有効</strong>です &mdash; 残り ' + humanDuration(rem) + ' (' + formatTs(exp) + ')';
        statusEl.classList.add('visible', 'valid');
      }
    } else {
      statusEl.innerHTML = 'ℹ exp クレームがありません &mdash; このトークンには有効期限が設定されていません。';
      statusEl.classList.add('visible', 'no-exp');
    }

    // Panels
    var algBadge = document.getElementById('jwt-alg-badge');
    algBadge.textContent = result.header.alg ? '(' + result.header.alg + ')' : '';

    document.getElementById('jwt-header-json').innerHTML = syntaxHighlight(JSON.stringify(result.header, null, 2));
    document.getElementById('jwt-payload-json').innerHTML = syntaxHighlight(JSON.stringify(result.payload, null, 2));
    document.getElementById('jwt-sig-hex').textContent = result.sigHex || '（署名のデコードに失敗しました）';
    panelsEl.classList.add('visible');

    // Standard claims table
    var knownClaims = Object.keys(CLAIM_DEFS).filter(function(k) { return pl[k] !== undefined; });
    if (knownClaims.length > 0) {
      var tbody = document.querySelector('#jwt-claims-table tbody');
      tbody.innerHTML = '';
      knownClaims.forEach(function(k) {
        var val = pl[k];
        var displayVal;
        if (k === 'exp' || k === 'nbf' || k === 'iat') {
          displayVal = escapeHtml(String(val)) + '<br><small style="color:#888;">' + escapeHtml(formatTs(val)) + '</small>';
        } else if (Array.isArray(val)) {
          displayVal = escapeHtml(val.join(', '));
        } else {
          displayVal = escapeHtml(String(val));
        }
        var tr = document.createElement('tr');
        tr.innerHTML = '<td class="claim-name">' + escapeHtml(k) + '</td><td>' + displayVal + '</td><td class="claim-desc">' + escapeHtml(CLAIM_DEFS[k]) + '</td>';
        tbody.appendChild(tr);
      });
      claimsSec.style.display = 'block';
    }
  }

  // Copy logic
  document.addEventListener('click', function(e) {
    var btn = e.target.closest('.jwt-copy-btn');
    if (!btn) return;
    var target = btn.getAttribute('data-target');
    var text = '';
    if (target === 'header' && stored.header) text = JSON.stringify(stored.header, null, 2);
    else if (target === 'payload' && stored.payload) text = JSON.stringify(stored.payload, null, 2);
    else if (target === 'signature' && stored.sig) text = stored.sig;
    if (!text) return;
    navigator.clipboard && navigator.clipboard.writeText(text).then(function() {
      var orig = btn.textContent;
      btn.textContent = 'コピーしました!';
      setTimeout(function() { btn.textContent = orig; }, 1500);
    });
  });

  var inputEl = document.getElementById('jwt-input');
  inputEl.addEventListener('input', function() { render(this.value); });
  inputEl.addEventListener('paste', function() { setTimeout(function() { render(inputEl.value); }, 0); });

  document.getElementById('jwt-sample-btn').addEventListener('click', function() {
    inputEl.value = SAMPLE;
    render(SAMPLE);
  });

  document.getElementById('jwt-clear-btn').addEventListener('click', function() {
    inputEl.value = '';
    render('');
  });
})();
</script>

</div>

---

### 関連ツール

> Base64のエンコード・デコード → [Base64エンコーダー](/ja/tools/base64-encoder/)

> JSONの整形・検証 → [JSONフォーマッター](/ja/tools/json-formatter/)

> ハッシュ値の生成 → [ハッシュジェネレーター](/ja/tools/hash-generator/)
