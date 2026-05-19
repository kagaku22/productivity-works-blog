---
title: "HTTPヘッダー分析ツール"
date: 2025-04-07
description: "無料のHTTPヘッダーリファレンス・ビルダー。50以上のHTTPヘッダーを検索・解説。セキュリティヘッダーのApache/Nginx設定を自動生成。"
categories: ["無料ツール"]
slug: "http-header-analyzer"
ShowToc: false
cover:
  image: "/images/covers/http-header-analyzer-ja.png"
  alt: "HTTPヘッダー分析ツール"
---

50以上のHTTPヘッダーを検索・解説。セキュリティヘッダーをビジュアルに設定して、Apache（.htaccess）またはNginx用の設定スニペットをワンクリックで生成。生のHTTPヘッダーを貼り付けて即座に解析することもできます。

<div id="hh-app">

<style>
#hh-app *, #hh-app *::before, #hh-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#hh-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Yu Gothic", Meiryo, "Segoe UI", sans-serif;
font-size: 15px;
color: #1a1a2e;
line-height: 1.6;
max-width: 960px;
margin: 0 auto;
}

/* ── タブ ── */
#hh-app .hh-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e2e8f0;
margin-bottom: 24px;
flex-wrap: wrap;
}
#hh-app .hh-tab {
padding: 10px 20px;
font-size: 14px;
font-weight: 600;
cursor: pointer;
border: none;
background: none;
color: #64748b;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
transition: color 0.15s, border-color 0.15s;
white-space: nowrap;
}
#hh-app .hh-tab:hover { color: #3a56d4; }
#hh-app .hh-tab.hh-active { color: #3a56d4; border-bottom-color: #3a56d4; }
#hh-app .hh-panel { display: none; }
#hh-app .hh-panel.hh-active { display: block; }

/* ── 検索・フィルター ── */
#hh-app .hh-search-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 18px;
}
#hh-app .hh-search {
flex: 1 1 240px;
padding: 9px 14px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-size: 14px;
outline: none;
transition: border-color 0.2s;
color: #1a1a2e;
}
#hh-app .hh-search:focus { border-color: #3a56d4; }
#hh-app .hh-cat-btns {
display: flex;
flex-wrap: wrap;
gap: 6px;
}
#hh-app .hh-cat-btn {
padding: 6px 13px;
border-radius: 20px;
border: 1px solid #cbd5e1;
background: #f8fafc;
font-size: 12px;
font-weight: 600;
cursor: pointer;
color: #475569;
transition: background 0.15s, border-color 0.15s, color 0.15s;
}
#hh-app .hh-cat-btn:hover { background: #e8f0fe; border-color: #3a56d4; color: #3a56d4; }
#hh-app .hh-cat-btn.hh-cat-active { background: #3a56d4; border-color: #3a56d4; color: #fff; }

/* ── ヘッダーカード ── */
#hh-app .hh-cards { display: flex; flex-direction: column; gap: 10px; }
#hh-app .hh-card {
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
}
#hh-app .hh-card-head {
display: flex;
align-items: center;
gap: 10px;
padding: 11px 16px;
background: #f8fafc;
cursor: pointer;
user-select: none;
}
#hh-app .hh-card-head:hover { background: #f0f4ff; }
#hh-app .hh-card-name {
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 13px;
font-weight: 700;
color: #1e3a8a;
flex: 1;
}
#hh-app .hh-badge {
font-size: 10px;
font-weight: 700;
padding: 2px 7px;
border-radius: 10px;
text-transform: uppercase;
letter-spacing: 0.04em;
white-space: nowrap;
flex-shrink: 0;
}
#hh-app .hh-badge-req  { background: #dbeafe; color: #1e40af; }
#hh-app .hh-badge-res  { background: #dcfce7; color: #166534; }
#hh-app .hh-badge-both { background: #fef3c7; color: #92400e; }
#hh-app .hh-badge-cat  { background: #f3e8ff; color: #6b21a8; }
#hh-app .hh-card-chevron { font-size: 10px; color: #94a3b8; flex-shrink: 0; }
#hh-app .hh-card-body {
padding: 14px 16px;
border-top: 1px solid #e2e8f0;
background: #fff;
display: none;
}
#hh-app .hh-card-body.hh-open { display: block; }
#hh-app .hh-card-desc { font-size: 13px; color: #334155; margin-bottom: 10px; }
#hh-app .hh-card-meta {
display: flex;
flex-wrap: wrap;
gap: 14px;
margin-bottom: 10px;
}
#hh-app .hh-meta-item { font-size: 12px; color: #64748b; }
#hh-app .hh-meta-item strong { color: #475569; }
#hh-app .hh-example-block {
background: #0f172a;
border-radius: 7px;
padding: 10px 14px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
}
#hh-app .hh-example-label {
font-size: 11px;
color: #94a3b8;
text-transform: uppercase;
letter-spacing: 0.06em;
margin-bottom: 5px;
font-weight: 600;
}
#hh-app .hh-no-results {
text-align: center;
padding: 40px 20px;
color: #94a3b8;
font-size: 14px;
}

/* ── セキュリティビルダー ── */
#hh-app .hh-builder-layout {
display: flex;
gap: 20px;
flex-wrap: wrap;
}
#hh-app .hh-builder-left { flex: 1 1 440px; min-width: 0; }
#hh-app .hh-builder-right { flex: 1 1 340px; min-width: 0; }
#hh-app .hh-builder-section {
border: 1px solid #e2e8f0;
border-radius: 10px;
margin-bottom: 14px;
overflow: hidden;
}
#hh-app .hh-builder-sec-head {
padding: 12px 16px;
background: #f8fafc;
font-weight: 700;
font-size: 13px;
color: #1e3a8a;
border-bottom: 1px solid #e2e8f0;
display: flex;
align-items: center;
gap: 8px;
}
#hh-app .hh-builder-sec-desc {
font-size: 11px;
color: #64748b;
font-weight: 400;
margin-left: 4px;
}
#hh-app .hh-field-group { padding: 14px 16px; display: flex; flex-direction: column; gap: 10px; }
#hh-app .hh-field-row { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; }
#hh-app .hh-field-label { font-size: 12px; color: #475569; min-width: 110px; flex-shrink: 0; }
#hh-app .hh-input, #hh-app .hh-select {
flex: 1;
min-width: 120px;
padding: 7px 10px;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
color: #1a1a2e;
background: #fff;
outline: none;
transition: border-color 0.15s;
}
#hh-app .hh-input:focus, #hh-app .hh-select:focus {
border-color: #3a56d4;
box-shadow: 0 0 0 3px rgba(58,86,212,0.1);
}
#hh-app .hh-enable-row {
display: flex; align-items: center; gap: 8px;
font-size: 13px; color: #334155;
padding: 8px 16px;
border-bottom: 1px solid #f1f5f9;
background: #fff;
}
#hh-app .hh-enable-row input[type="checkbox"] {
width: 15px; height: 15px;
accent-color: #3a56d4; cursor: pointer; flex-shrink: 0;
}
#hh-app .hh-enable-row label { cursor: pointer; }

/* ── 出力ボックス ── */
#hh-app .hh-out-box {
background: #0f172a;
border-radius: 10px;
overflow: hidden;
position: sticky;
top: 80px;
}
#hh-app .hh-out-topbar {
display: flex;
align-items: center;
justify-content: space-between;
padding: 10px 14px;
background: #1e293b;
flex-wrap: wrap;
gap: 6px;
}
#hh-app .hh-out-label {
font-size: 11px;
font-weight: 700;
color: #94a3b8;
letter-spacing: 0.06em;
text-transform: uppercase;
}
#hh-app .hh-out-actions { display: flex; gap: 6px; flex-wrap: wrap; }
#hh-app .hh-format-btns { display: flex; gap: 0; border-radius: 6px; overflow: hidden; border: 1px solid #334155; }
#hh-app .hh-format-btn {
padding: 4px 12px;
background: #1e293b;
color: #94a3b8;
border: none;
font-size: 11px;
font-weight: 700;
cursor: pointer;
transition: background 0.15s, color 0.15s;
border-right: 1px solid #334155;
}
#hh-app .hh-format-btn:last-child { border-right: none; }
#hh-app .hh-format-btn:hover { background: #334155; color: #e2e8f0; }
#hh-app .hh-format-btn.hh-fmt-active { background: #3a56d4; color: #fff; }
#hh-app .hh-copy-btn {
padding: 5px 12px;
border-radius: 6px;
font-size: 12px;
font-weight: 600;
cursor: pointer;
border: none;
background: #3a56d4;
color: #fff;
transition: background 0.15s;
}
#hh-app .hh-copy-btn:hover { background: #2d44b0; }
#hh-app .hh-copy-btn.hh-copied { background: #16a34a; }
#hh-app .hh-out-code {
padding: 16px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
line-height: 1.7;
color: #e2e8f0;
white-space: pre;
overflow-x: auto;
max-height: 540px;
overflow-y: auto;
min-height: 160px;
}
#hh-app .hh-out-code .hh-c-comment { color: #64748b; }
#hh-app .hh-out-code .hh-c-key     { color: #7dd3fc; }
#hh-app .hh-out-code .hh-c-val     { color: #86efac; }
#hh-app .hh-out-code .hh-c-tag     { color: #f9a8d4; }
#hh-app .hh-out-code .hh-c-dir     { color: #fde68a; }

/* ── パーサー ── */
#hh-app .hh-parser-layout {
display: flex;
gap: 20px;
flex-wrap: wrap;
}
#hh-app .hh-parser-left { flex: 1 1 360px; min-width: 0; }
#hh-app .hh-parser-right { flex: 1 1 380px; min-width: 0; }
#hh-app .hh-textarea {
width: 100%;
padding: 12px 14px;
border: 2px solid #d1d5db;
border-radius: 8px;
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 12px;
color: #1a1a2e;
resize: vertical;
outline: none;
transition: border-color 0.2s;
min-height: 240px;
line-height: 1.6;
}
#hh-app .hh-textarea:focus { border-color: #3a56d4; }
#hh-app .hh-parse-btn {
margin-top: 10px;
width: 100%;
padding: 11px;
background: linear-gradient(135deg, #3a56d4, #7c3aed);
color: #fff;
border: none;
border-radius: 8px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
transition: opacity 0.2s;
}
#hh-app .hh-parse-btn:hover { opacity: 0.9; }
#hh-app .hh-parsed-list { display: flex; flex-direction: column; gap: 8px; }
#hh-app .hh-parsed-item {
border: 1px solid #e2e8f0;
border-radius: 8px;
overflow: hidden;
}
#hh-app .hh-parsed-head {
display: flex;
align-items: center;
gap: 8px;
padding: 9px 13px;
background: #f8fafc;
font-size: 12px;
}
#hh-app .hh-parsed-name {
font-family: "SFMono-Regular", Consolas, monospace;
font-weight: 700;
color: #1e3a8a;
flex: 1;
}
#hh-app .hh-parsed-val {
font-family: "SFMono-Regular", Consolas, monospace;
font-size: 11px;
color: #334155;
background: #f1f5f9;
padding: 2px 7px;
border-radius: 4px;
max-width: 220px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}
#hh-app .hh-parsed-desc {
padding: 8px 13px;
font-size: 12px;
color: #475569;
border-top: 1px solid #f1f5f9;
background: #fff;
}
#hh-app .hh-parsed-unknown {
color: #94a3b8;
font-style: italic;
}
#hh-app .hh-parse-placeholder {
text-align: center;
padding: 40px 20px;
color: #94a3b8;
font-size: 13px;
border: 2px dashed #e2e8f0;
border-radius: 8px;
}

/* ── その他 ── */
#hh-app .hh-hint { font-size: 12px; color: #94a3b8; margin-top: 5px; }
#hh-app .hh-section-intro {
font-size: 13px;
color: #64748b;
margin-bottom: 18px;
padding: 12px 16px;
background: #f8fafc;
border-radius: 8px;
border-left: 3px solid #3a56d4;
}

@media (max-width: 680px) {
#hh-app .hh-builder-layout,
#hh-app .hh-parser-layout { flex-direction: column; }
#hh-app .hh-out-box { position: static; }
#hh-app .hh-tab { padding: 8px 13px; font-size: 13px; }
}
</style>

<!-- タブ -->
<div class="hh-tabs">
<button class="hh-tab hh-active" onclick="hhShowTab('reference')">リファレンス</button>
<button class="hh-tab" onclick="hhShowTab('builder')">セキュリティビルダー</button>
<button class="hh-tab" onclick="hhShowTab('parser')">ヘッダー解析</button>
</div>

<!-- ═══ TAB 1: リファレンス -->
<div class="hh-panel hh-active" id="hh-panel-reference">
<div class="hh-section-intro">50以上のHTTPヘッダーをカテゴリ別に検索できます。各ヘッダーをクリックすると説明・よく使う値・例が表示されます。</div>
<div class="hh-search-row">
<input type="text" class="hh-search" id="hh-ref-search" placeholder="ヘッダーを検索... (例: Content-Type, キャッシュ, CORS)" oninput="hhFilterRef()">
<div class="hh-cat-btns" id="hh-cat-btns"></div>
</div>
<div class="hh-cards" id="hh-cards"></div>
<div class="hh-no-results" id="hh-no-results" style="display:none;">検索条件に一致するヘッダーが見つかりませんでした。</div>
</div>

<!-- ═══ TAB 2: セキュリティビルダー -->
<div class="hh-panel" id="hh-panel-builder">
<div class="hh-section-intro">セキュリティヘッダーを選択・設定して、Apache（.htaccess）またはNginx用の設定スニペットを生成します。</div>
<div class="hh-builder-layout">
<div class="hh-builder-left">

<!-- CSP -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">
Content-Security-Policy
<span class="hh-builder-sec-desc">— 読み込み元の制御</span>
</div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-csp" onchange="hhBuild()">
<label for="hh-b-csp">CSPヘッダーを有効化</label>
</div>
<div class="hh-field-group" id="hh-b-csp-fields" style="display:none;">
<div class="hh-field-row">
<span class="hh-field-label">default-src</span>
<select class="hh-select" id="hh-csp-default" onchange="hhBuild()">
<option value="'self'">'self'（同一オリジンのみ）</option>
<option value="'self' 'unsafe-inline'">'self' 'unsafe-inline'</option>
<option value="'none'">'none'（すべて禁止）</option>
<option value="*">*（すべて許可）</option>
</select>
</div>
<div class="hh-field-row">
<span class="hh-field-label">script-src</span>
<input type="text" class="hh-input" id="hh-csp-script" placeholder="'self'（空白でdefault-srcを継承）" oninput="hhBuild()">
</div>
<div class="hh-field-row">
<span class="hh-field-label">style-src</span>
<input type="text" class="hh-input" id="hh-csp-style" placeholder="'self'（空白でdefault-srcを継承）" oninput="hhBuild()">
</div>
<div class="hh-field-row">
<span class="hh-field-label">img-src</span>
<input type="text" class="hh-input" id="hh-csp-img" placeholder="'self' data:（空白で継承）" oninput="hhBuild()">
</div>
<div class="hh-field-row">
<span class="hh-field-label">frame-src</span>
<input type="text" class="hh-input" id="hh-csp-frame" placeholder="'none'（空白で継承）" oninput="hhBuild()">
</div>
</div>
</div>

<!-- HSTS -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">Strict-Transport-Security <span class="hh-builder-sec-desc">— HTTPS強制</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-hsts" onchange="hhBuild()" checked>
<label for="hh-b-hsts">HSTSを有効化</label>
</div>
<div class="hh-field-group">
<div class="hh-field-row">
<span class="hh-field-label">max-age</span>
<select class="hh-select" id="hh-hsts-age" onchange="hhBuild()" style="max-width:240px;">
<option value="2592000">30日（2592000秒）</option>
<option value="15552000">6ヶ月（15552000秒）</option>
<option value="31536000" selected>1年（31536000秒）</option>
</select>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-hsts-sub" onchange="hhBuild()" checked>
<label for="hh-hsts-sub">includeSubDomains（サブドメインも対象）</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-hsts-pre" onchange="hhBuild()">
<label for="hh-hsts-pre">preload（HSTPSプリロードリストへ登録）</label>
</div>
</div>
</div>

<!-- X-Frame-Options -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">X-Frame-Options <span class="hh-builder-sec-desc">— クリックジャッキング対策</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-xframe" onchange="hhBuild()" checked>
<label for="hh-b-xframe">X-Frame-Optionsを有効化</label>
</div>
<div class="hh-field-group">
<div class="hh-field-row">
<span class="hh-field-label">値</span>
<select class="hh-select" id="hh-xframe-val" onchange="hhBuild()" style="max-width:240px;">
<option value="SAMEORIGIN" selected>SAMEORIGIN（同一オリジンのみ許可）</option>
<option value="DENY">DENY（すべて禁止）</option>
</select>
</div>
</div>
</div>

<!-- X-Content-Type-Options -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">X-Content-Type-Options <span class="hh-builder-sec-desc">— MIMEスニッフィング防止</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-xcto" onchange="hhBuild()" checked>
<label for="hh-b-xcto">有効化（常に nosniff）</label>
</div>
</div>

<!-- Referrer-Policy -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">Referrer-Policy <span class="hh-builder-sec-desc">— リファラー情報の制御</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-rp" onchange="hhBuild()" checked>
<label for="hh-b-rp">Referrer-Policyを有効化</label>
</div>
<div class="hh-field-group">
<div class="hh-field-row">
<span class="hh-field-label">ポリシー</span>
<select class="hh-select" id="hh-rp-val" onchange="hhBuild()">
<option value="no-referrer">no-referrer（送信しない）</option>
<option value="no-referrer-when-downgrade">no-referrer-when-downgrade</option>
<option value="strict-origin-when-cross-origin" selected>strict-origin-when-cross-origin（推奨）</option>
<option value="same-origin">same-origin（同一オリジンのみ）</option>
<option value="origin">origin</option>
</select>
</div>
</div>
</div>

<!-- Permissions-Policy -->
<div class="hh-builder-section">
<div class="hh-builder-sec-head">Permissions-Policy <span class="hh-builder-sec-desc">— ブラウザ機能の制御</span></div>
<div class="hh-enable-row">
<input type="checkbox" id="hh-b-pp" onchange="hhBuild()">
<label for="hh-b-pp">Permissions-Policyを有効化</label>
</div>
<div class="hh-field-group" id="hh-b-pp-fields" style="display:none;">
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-cam" onchange="hhBuild()" checked>
<label for="hh-pp-cam">camera=()（カメラを無効化）</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-mic" onchange="hhBuild()" checked>
<label for="hh-pp-mic">microphone=()（マイクを無効化）</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-geo" onchange="hhBuild()" checked>
<label for="hh-pp-geo">geolocation=()（位置情報を無効化）</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-pay" onchange="hhBuild()">
<label for="hh-pp-pay">payment=()（決済APIを無効化）</label>
</div>
<div class="hh-enable-row" style="padding:0;border:none;">
<input type="checkbox" id="hh-pp-usb" onchange="hhBuild()">
<label for="hh-pp-usb">usb=()（USBを無効化）</label>
</div>
</div>
</div>

</div><!-- /.hh-builder-left -->

<div class="hh-builder-right">
<div class="hh-out-box">
<div class="hh-out-topbar">
<span class="hh-out-label">生成された設定</span>
<div class="hh-out-actions">
<div class="hh-format-btns">
<button class="hh-format-btn hh-fmt-active" id="hh-fmt-apache" onclick="hhSetFmt('apache')">Apache</button>
<button class="hh-format-btn" id="hh-fmt-nginx" onclick="hhSetFmt('nginx')">Nginx</button>
</div>
<button class="hh-copy-btn" id="hh-build-copy" onclick="hhCopyBuild()">コピー</button>
</div>
</div>
<pre class="hh-out-code" id="hh-build-out"></pre>
</div>
</div>

</div><!-- /.hh-builder-layout -->
</div>

<!-- ═══ TAB 3: ヘッダー解析 -->
<div class="hh-panel" id="hh-panel-parser">
<div class="hh-section-intro">HTTPレスポンスヘッダーを貼り付けて「解析」をクリックすると、各ヘッダーの意味を日本語で確認できます。</div>
<div class="hh-parser-layout">
<div class="hh-parser-left">
<textarea class="hh-textarea" id="hh-parse-input" placeholder="HTTPヘッダーをここに貼り付けてください。例：

HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Cache-Control: max-age=3600, public
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Frame-Options: SAMEORIGIN
Content-Encoding: gzip
Vary: Accept-Encoding
Server: nginx/1.24.0"></textarea>
<button class="hh-parse-btn" onclick="hhParse()">ヘッダーを解析する</button>
<div class="hh-hint" style="margin-top:8px;">HTTP/1.1・HTTP/2 形式のレスポンスヘッダーに対応しています。</div>
</div>
<div class="hh-parser-right">
<div id="hh-parsed-out">
<div class="hh-parse-placeholder">上にヘッダーを貼り付けて「解析」をクリックすると、こちらに解説が表示されます。</div>
</div>
</div>
</div>
</div>

<script>
(function() {

/* ══ データ（説明は英語のまま、カテゴリ名は日本語） */
var HH_HEADERS = [
// 一般
{ name: 'Date', cat: '一般', dir: 'both', desc: 'メッセージが生成された日時をHTTP-date形式で示します。', values: 'HTTP-date (RFC 7231)', example: 'Date: Tue, 15 Nov 1994 08:12:31 GMT' },
{ name: 'Connection', cat: '一般', dir: 'both', desc: '現在のトランザクション終了後にネットワーク接続を維持するかどうかを制御します。', values: 'keep-alive, close', example: 'Connection: keep-alive' },
{ name: 'Transfer-Encoding', cat: '一般', dir: 'both', desc: 'メッセージボディに適用されるエンコード方式を指定します。', values: 'chunked, gzip, deflate, identity', example: 'Transfer-Encoding: chunked' },
{ name: 'Upgrade', cat: '一般', dir: 'both', desc: '別のプロトコルへの切り替えをサーバーに要求します。', values: 'websocket, HTTP/2.0', example: 'Upgrade: websocket' },
// リクエスト
{ name: 'Host', cat: 'リクエスト', dir: 'req', desc: 'リクエスト送信先のサーバーのホスト名とポートを指定します。HTTP/1.1では必須です。', values: 'hostname[:port]', example: 'Host: www.example.com' },
{ name: 'User-Agent', cat: 'リクエスト', dir: 'req', desc: 'リクエストを行うクライアントソフトウェア（ブラウザ、ボット、ライブラリ）を識別する文字列。', values: 'product/version 文字列', example: 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/124' },
{ name: 'Accept', cat: 'リクエスト', dir: 'req', desc: 'クライアントが理解できるコンテンツタイプをサーバーに伝えます。', values: 'MIMEタイプ、品質係数(q=)', example: 'Accept: text/html,application/xhtml+xml,application/json;q=0.9' },
{ name: 'Accept-Encoding', cat: 'リクエスト', dir: 'req', desc: 'クライアントがサポートするコンテンツエンコーディング（圧縮）アルゴリズムを伝えます。', values: 'gzip, deflate, br, zstd, identity', example: 'Accept-Encoding: gzip, deflate, br' },
{ name: 'Accept-Language', cat: 'リクエスト', dir: 'req', desc: 'クライアントが希望するレスポンスの言語を指定します。', values: '言語タグ (BCP 47)', example: 'Accept-Language: ja,en-US;q=0.9,en;q=0.8' },
{ name: 'Authorization', cat: 'リクエスト', dir: 'req', desc: 'サーバーとのクライアント認証に使用する認証情報を格納します。', values: 'Basic, Bearer, Digest, OAuth', example: 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...' },
{ name: 'Cookie', cat: 'リクエスト', dir: 'req', desc: 'クライアントが保存しているCookieをサーバーへ送信します。', values: 'name=value ペア', example: 'Cookie: session_id=abc123; user_pref=dark' },
{ name: 'Referer', cat: 'リクエスト', dir: 'req', desc: 'リクエストが開始されたページのURLです。（仕様書では意図的にスペルミスのまま）', values: 'URL', example: 'Referer: https://www.example.com/page' },
{ name: 'Origin', cat: 'リクエスト', dir: 'req', desc: 'リクエストの発信元（スキーム・ホスト名・ポート）を示します。CORSプリフライトで使用されます。', values: 'scheme://host[:port]', example: 'Origin: https://app.example.com' },
{ name: 'If-Modified-Since', cat: 'リクエスト', dir: 'req', desc: '条件付きリクエスト。指定日時以降に変更があった場合のみリソースを返します。', values: 'HTTP-date', example: 'If-Modified-Since: Sat, 29 Oct 2024 19:43:31 GMT' },
{ name: 'If-None-Match', cat: 'リクエスト', dir: 'req', desc: 'ETagを使った条件付きリクエスト。一致する場合は 304 Not Modified を返します。', values: 'ETag値 または *', example: 'If-None-Match: "33a64df551425fcc55e4d42a148795d9f25f89d4"' },
{ name: 'Range', cat: 'リクエスト', dir: 'req', desc: 'リソースの一部のみを要求します。レジューム可能なダウンロードやストリーミングに使用。', values: 'bytes=start-end', example: 'Range: bytes=200-1023' },
{ name: 'Expect', cat: 'リクエスト', dir: 'req', desc: 'クライアントが要求する特定のサーバー動作を示します。通常は 100-continue に使用。', values: '100-continue', example: 'Expect: 100-continue' },
// レスポンス
{ name: 'Content-Type', cat: 'レスポンス', dir: 'res', desc: 'レスポンスボディのメディアタイプを示します。文字セットを含む場合もあります。', values: 'MIMEタイプ [; charset=...]', example: 'Content-Type: text/html; charset=utf-8' },
{ name: 'Content-Length', cat: 'レスポンス', dir: 'res', desc: 'レスポンスボディのバイト数を示します。', values: '整数（バイト数）', example: 'Content-Length: 3495' },
{ name: 'Content-Encoding', cat: 'レスポンス', dir: 'res', desc: 'レスポンスボディに適用されたエンコーディングを示します。クライアントはデコードが必要です。', values: 'gzip, deflate, br, zstd', example: 'Content-Encoding: gzip' },
{ name: 'Content-Language', cat: 'レスポンス', dir: 'res', desc: 'レスポンスの対象読者の自然言語を記述します。', values: '言語タグ (BCP 47)', example: 'Content-Language: ja' },
{ name: 'Location', cat: 'レスポンス', dir: 'res', desc: '3xxレスポンスのリダイレクト先URL、または201で作成されたリソースのURLを示します。', values: 'URL', example: 'Location: https://www.example.com/new-page' },
{ name: 'Set-Cookie', cat: 'レスポンス', dir: 'res', desc: 'サーバーからユーザーエージェントへCookieを送信します。', values: 'name=value [; 属性]', example: 'Set-Cookie: id=a3fWa; Expires=Thu, 21 Oct 2025 07:28:00 GMT; Secure; HttpOnly' },
{ name: 'Server', cat: 'レスポンス', dir: 'res', desc: 'オリジンサーバーのソフトウェアを記述します。セキュリティ上、公開を控えることが推奨されます。', values: 'product/version 文字列', example: 'Server: nginx/1.24.0' },
{ name: 'WWW-Authenticate', cat: 'レスポンス', dir: 'res', desc: 'リソースへのアクセスに使用すべき認証方式を定義します。401とともに送信されます。', values: 'auth-scheme [realm="..."]', example: 'WWW-Authenticate: Basic realm="Access to the staging site"' },
{ name: 'Retry-After', cat: 'レスポンス', dir: 'res', desc: '次のリクエストまで待機すべき時間を示します。429や503とともに使用されます。', values: 'HTTP-dateまたは秒数', example: 'Retry-After: 120' },
{ name: 'Vary', cat: 'レスポンス', dir: 'res', desc: 'キャッシュがレスポンスを使用できるかを判断する際に考慮すべきリクエストヘッダーをキャッシュに伝えます。', values: 'ヘッダー名 または *', example: 'Vary: Accept-Encoding, Accept-Language' },
{ name: 'ETag', cat: 'レスポンス', dir: 'res', desc: 'リソースの特定バージョンの一意識別子。キャッシュ検証に使用されます。', values: '"opaque-tag" または W/"weak-tag"', example: 'ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4"' },
{ name: 'Last-Modified', cat: 'レスポンス', dir: 'res', desc: 'リソースが最後に変更された日時。条件付きリクエストとキャッシュに使用されます。', values: 'HTTP-date', example: 'Last-Modified: Wed, 21 Oct 2024 07:28:00 GMT' },
{ name: 'Allow', cat: 'レスポンス', dir: 'res', desc: 'リソースがサポートするHTTPメソッドを列挙します。405 Method Not Allowedとともに送信されます。', values: 'HTTPメソッドのリスト', example: 'Allow: GET, POST, HEAD' },
// セキュリティ
{ name: 'Strict-Transport-Security', cat: 'セキュリティ', dir: 'res', desc: '指定期間、ブラウザにHTTPS経由でのみサイトへアクセスするよう強制します。ダウングレード攻撃を防ぎます。', values: 'max-age=N [; includeSubDomains] [; preload]', example: 'Strict-Transport-Security: max-age=31536000; includeSubDomains; preload' },
{ name: 'Content-Security-Policy', cat: 'セキュリティ', dir: 'res', desc: 'ブラウザがリソースを読み込める発信元を制限します。XSS攻撃に対する主要な防御手段です。', values: 'ディレクティブ ソースリスト のペア', example: "Content-Security-Policy: default-src 'self'; script-src 'self' cdn.example.com" },
{ name: 'X-Frame-Options', cat: 'セキュリティ', dir: 'res', desc: '他のオリジンのiframeへのページ埋め込みを防ぎ、クリックジャッキング攻撃を軽減します。', values: 'DENY, SAMEORIGIN', example: 'X-Frame-Options: SAMEORIGIN' },
{ name: 'X-Content-Type-Options', cat: 'セキュリティ', dir: 'res', desc: 'ブラウザによるMIMEスニッフィングを防止し、宣言されたContent-Typeを強制します。', values: 'nosniff', example: 'X-Content-Type-Options: nosniff' },
{ name: 'Referrer-Policy', cat: 'セキュリティ', dir: 'res', desc: 'リクエストに含まれるリファラー情報の量を制御します。プライバシーとアナリティクスのバランスを調整します。', values: 'no-referrer, strict-origin-when-cross-origin, same-origin など', example: 'Referrer-Policy: strict-origin-when-cross-origin' },
{ name: 'Permissions-Policy', cat: 'セキュリティ', dir: 'res', desc: 'ページやiframe内でのブラウザ機能（カメラ、マイク、位置情報など）へのアクセスを制御します。', values: 'feature=(allowlist) のペア', example: 'Permissions-Policy: camera=(), microphone=(), geolocation=()' },
{ name: 'X-XSS-Protection', cat: 'セキュリティ', dir: 'res', desc: '旧ブラウザのXSSフィルターを有効化します。現代ではCSPに置き換えられていますが、レガシー対応として有用です。', values: '0, 1, 1; mode=block', example: 'X-XSS-Protection: 1; mode=block' },
{ name: 'Cross-Origin-Opener-Policy', cat: 'セキュリティ', dir: 'res', desc: 'クロスオリジン攻撃を防ぐため、ブラウジングコンテキストをクロスオリジン文書から分離します。', values: 'unsafe-none, same-origin-allow-popups, same-origin', example: 'Cross-Origin-Opener-Policy: same-origin' },
{ name: 'Cross-Origin-Embedder-Policy', cat: 'セキュリティ', dir: 'res', desc: '明示的に許可しないクロスオリジンリソースの読み込みを防止します。', values: 'unsafe-none, require-corp', example: 'Cross-Origin-Embedder-Policy: require-corp' },
{ name: 'Cross-Origin-Resource-Policy', cat: 'セキュリティ', dir: 'res', desc: '他のオリジンがレスポンスを読み取ることを防ぎます。Spectre系サイドチャネル攻撃に対する防御です。', values: 'same-origin, same-site, cross-origin', example: 'Cross-Origin-Resource-Policy: same-origin' },
// キャッシュ
{ name: 'Cache-Control', cat: 'キャッシュ', dir: 'both', desc: 'リクエスト・レスポンスのキャッシュメカニズムに対するディレクティブ。主要なキャッシュ制御ヘッダーです。', values: 'no-cache, no-store, max-age=N, public, private, must-revalidate など', example: 'Cache-Control: public, max-age=86400, must-revalidate' },
{ name: 'Expires', cat: 'キャッシュ', dir: 'res', desc: 'レスポンスが陳腐化するとみなされる日時。Cache-Control の max-age が存在する場合はそちらが優先されます。', values: 'HTTP-date または 0（即時期限切れ）', example: 'Expires: Thu, 01 Jan 2026 00:00:00 GMT' },
{ name: 'Pragma', cat: 'キャッシュ', dir: 'req', desc: '後方互換性のためのレガシーキャッシュ制御ヘッダー。現代の実装ではCache-Controlを使用してください。', values: 'no-cache', example: 'Pragma: no-cache' },
{ name: 'Age', cat: 'キャッシュ', dir: 'res', desc: 'プロキシキャッシュにオブジェクトが保存されてからの経過時間（秒）。', values: '整数（秒）', example: 'Age: 24' },
{ name: 'ETag', cat: 'キャッシュ', dir: 'res', desc: 'リソースの特定バージョンの一意識別子。キャッシュ検証に使用されます。', values: '"opaque-tag" または W/"weak-tag"', example: 'ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4"' },
// CORS
{ name: 'Access-Control-Allow-Origin', cat: 'CORS', dir: 'res', desc: 'リソースへのアクセスを許可するオリジンを指定します。CORSリクエストへのサーバー応答として設定されます。', values: '* または特定のオリジン', example: 'Access-Control-Allow-Origin: https://app.example.com' },
{ name: 'Access-Control-Allow-Methods', cat: 'CORS', dir: 'res', desc: 'CORSコンテキストでリソースへのアクセス時に許可されるHTTPメソッドを指定します。', values: 'HTTPメソッドのリスト', example: 'Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS' },
{ name: 'Access-Control-Allow-Headers', cat: 'CORS', dir: 'res', desc: 'CORSリクエスト時に使用できるHTTPヘッダーを示します。', values: 'ヘッダー名 または *', example: 'Access-Control-Allow-Headers: Content-Type, Authorization, X-Requested-With' },
{ name: 'Access-Control-Allow-Credentials', cat: 'CORS', dir: 'res', desc: 'credentials フラグが true のときにレスポンスを公開できるかどうかを示します。', values: 'true', example: 'Access-Control-Allow-Credentials: true' },
{ name: 'Access-Control-Max-Age', cat: 'CORS', dir: 'res', desc: 'プリフライトリクエストの結果をキャッシュできる時間（秒）を示します。', values: '整数（秒）', example: 'Access-Control-Max-Age: 86400' },
{ name: 'Access-Control-Request-Method', cat: 'CORS', dir: 'req', desc: 'プリフライトリクエストで、実際のリクエストで使用するHTTPメソッドを示します。', values: 'HTTPメソッド', example: 'Access-Control-Request-Method: POST' },
// コンテンツ
{ name: 'Accept-Ranges', cat: 'コンテンツ', dir: 'res', desc: 'サーバーがリソースの範囲リクエストをサポートしているかどうかを示します。', values: 'bytes, none', example: 'Accept-Ranges: bytes' },
{ name: 'Content-Disposition', cat: 'コンテンツ', dir: 'res', desc: 'コンテンツをインライン表示するか、添付ファイル（ダウンロード）として扱うかを示します。', values: 'inline, attachment [; filename="..."]', example: 'Content-Disposition: attachment; filename="report.pdf"' },
{ name: 'Vary', cat: 'コンテンツ', dir: 'res', desc: 'キャッシュが保存済みレスポンスを使用できるかを判断するために考慮すべきリクエストヘッダーをキャッシュに伝えます。', values: 'ヘッダー名 または *', example: 'Vary: Accept-Encoding, Accept-Language' },
{ name: 'X-Powered-By', cat: 'コンテンツ', dir: 'res', desc: 'サーバーで使用されている技術を示します。情報漏洩のリスクがあるため、通常は非表示にすることが推奨されます。', values: 'technology/version', example: 'X-Powered-By: PHP/8.2.0' },
{ name: 'Alt-Svc', cat: 'コンテンツ', dir: 'res', desc: 'サーバーが代替サービス（例：QUICを使うHTTP/3）を広告できます。', values: 'protocol="host:port" [; ma=N]', example: 'Alt-Svc: h3=":443"; ma=86400' },
{ name: 'X-Forwarded-For', cat: 'コンテンツ', dir: 'req', desc: 'プロキシ経由で接続するクライアントの発信元IPアドレスを識別するデファクトスタンダードなヘッダー。', values: 'IPアドレスのリスト', example: 'X-Forwarded-For: 203.0.113.195, 70.41.3.18' },
];

var HH_CATS = ['すべて','一般','リクエスト','レスポンス','セキュリティ','キャッシュ','CORS','コンテンツ'];
var hhCurrentCat = 'すべて';
var hhOpenCards = {};
var hhCurrentFmt = 'apache';

/* ══ タブ */
function hhShowTab(id) {
document.querySelectorAll('#hh-app .hh-tab').forEach(function(t, i) {
var tabs = ['reference','builder','parser'];
t.classList.toggle('hh-active', tabs[i] === id);
});
document.querySelectorAll('#hh-app .hh-panel').forEach(function(p) {
p.classList.remove('hh-active');
});
var panel = document.getElementById('hh-panel-' + id);
if (panel) panel.classList.add('hh-active');
}
window.hhShowTab = hhShowTab;

/* ══ リファレンス */
function hhBuildCatBtns() {
var cont = document.getElementById('hh-cat-btns');
if (!cont) return;
cont.innerHTML = '';
HH_CATS.forEach(function(cat) {
var btn = document.createElement('button');
btn.className = 'hh-cat-btn' + (cat === hhCurrentCat ? ' hh-cat-active' : '');
btn.textContent = cat;
btn.onclick = function() { hhCurrentCat = cat; hhBuildCatBtns(); hhFilterRef(); };
cont.appendChild(btn);
});
}

function hhFilterRef() {
var q = (document.getElementById('hh-ref-search') ? document.getElementById('hh-ref-search').value : '').toLowerCase().trim();
var cards = document.getElementById('hh-cards');
var noRes = document.getElementById('hh-no-results');
var count = 0;
if (!cards) return;
cards.querySelectorAll('.hh-card').forEach(function(card) {
var name = (card.getAttribute('data-name') || '').toLowerCase();
var cat  = (card.getAttribute('data-cat') || '').toLowerCase();
var desc = (card.getAttribute('data-desc') || '').toLowerCase();
var catMatch = hhCurrentCat === 'すべて' || card.getAttribute('data-cat') === hhCurrentCat;
var qMatch = !q || name.indexOf(q) !== -1 || cat.indexOf(q) !== -1 || desc.indexOf(q) !== -1;
var show = catMatch && qMatch;
card.style.display = show ? '' : 'none';
if (show) count++;
});
if (noRes) noRes.style.display = count === 0 ? '' : 'none';
}
window.hhFilterRef = hhFilterRef;

function hhToggleCard(name) {
hhOpenCards[name] = !hhOpenCards[name];
var body = document.getElementById('hh-card-body-' + name);
var chev = document.getElementById('hh-card-chev-' + name);
if (body) body.classList.toggle('hh-open', hhOpenCards[name]);
if (chev) chev.textContent = hhOpenCards[name] ? '▼' : '▶';
}
window.hhToggleCard = hhToggleCard;

function hhBuildDirBadge(dir) {
var map = { req: ['hh-badge-req','リクエスト'], res: ['hh-badge-res','レスポンス'], both: ['hh-badge-both','両方'] };
var info = map[dir] || ['hh-badge-both', dir];
return '<span class="hh-badge ' + info[0] + '">' + info[1] + '</span>';
}

function hhBuildCards() {
var cards = document.getElementById('hh-cards');
if (!cards) return;
cards.innerHTML = '';
HH_HEADERS.forEach(function(h) {
var safeName = h.name.replace(/[^a-zA-Z0-9-]/g, '_');
var card = document.createElement('div');
card.className = 'hh-card';
card.setAttribute('data-name', h.name);
card.setAttribute('data-cat', h.cat);
card.setAttribute('data-desc', h.desc);
card.innerHTML =
'<div class="hh-card-head" onclick="hhToggleCard(\'' + safeName + '\')">' +
'<span class="hh-card-name">' + hEsc(h.name) + '</span>' +
hhBuildDirBadge(h.dir) +
'<span class="hh-badge hh-badge-cat">' + hEsc(h.cat) + '</span>' +
'<span class="hh-card-chevron" id="hh-card-chev-' + safeName + '">▶</span>' +
'</div>' +
'<div class="hh-card-body" id="hh-card-body-' + safeName + '">' +
'<div class="hh-card-desc">' + hEsc(h.desc) + '</div>' +
'<div class="hh-card-meta">' +
'<div class="hh-meta-item"><strong>よく使う値：</strong>' + hEsc(h.values) + '</div>' +
'</div>' +
'<div class="hh-example-label">使用例</div>' +
'<div class="hh-example-block">' + hEsc(h.example) + '</div>' +
'</div>';
cards.appendChild(card);
});
}

/* ══ ビルダー */
function hhSetFmt(fmt) {
hhCurrentFmt = fmt;
document.getElementById('hh-fmt-apache').classList.toggle('hh-fmt-active', fmt === 'apache');
document.getElementById('hh-fmt-nginx').classList.toggle('hh-fmt-active', fmt === 'nginx');
hhBuild();
}
window.hhSetFmt = hhSetFmt;

function c(id) { var el = document.getElementById(id); return el ? el.checked : false; }
function v(id) { var el = document.getElementById(id); return el ? el.value.trim() : ''; }

function hhBuild() {
var cspF = document.getElementById('hh-b-csp-fields');
if (cspF) cspF.style.display = c('hh-b-csp') ? '' : 'none';
var ppF = document.getElementById('hh-b-pp-fields');
if (ppF) ppF.style.display = c('hh-b-pp') ? '' : 'none';

var headers = [];

if (c('hh-b-hsts')) {
var age = v('hh-hsts-age') || '31536000';
var hsts = 'max-age=' + age;
if (c('hh-hsts-sub')) hsts += '; includeSubDomains';
if (c('hh-hsts-pre')) hsts += '; preload';
headers.push(['Strict-Transport-Security', hsts]);
}
if (c('hh-b-xframe')) headers.push(['X-Frame-Options', v('hh-xframe-val') || 'SAMEORIGIN']);
if (c('hh-b-xcto'))   headers.push(['X-Content-Type-Options', 'nosniff']);
if (c('hh-b-rp'))     headers.push(['Referrer-Policy', v('hh-rp-val') || 'strict-origin-when-cross-origin']);
if (c('hh-b-csp')) {
var def = v('hh-csp-default') || "'self'";
var csp = "default-src " + def;
var scr = v('hh-csp-script'); if (scr) csp += "; script-src " + scr;
var sty = v('hh-csp-style');  if (sty) csp += "; style-src " + sty;
var img = v('hh-csp-img');    if (img) csp += "; img-src " + img;
var frm = v('hh-csp-frame');  if (frm) csp += "; frame-src " + frm;
headers.push(['Content-Security-Policy', csp]);
}
if (c('hh-b-pp')) {
var ppParts = [];
if (c('hh-pp-cam')) ppParts.push('camera=()');
if (c('hh-pp-mic')) ppParts.push('microphone=()');
if (c('hh-pp-geo')) ppParts.push('geolocation=()');
if (c('hh-pp-pay')) ppParts.push('payment=()');
if (c('hh-pp-usb')) ppParts.push('usb=()');
if (ppParts.length) headers.push(['Permissions-Policy', ppParts.join(', ')]);
}

var out = document.getElementById('hh-build-out');
if (!out) return;

var lines = [];
var raw = '';

if (hhCurrentFmt === 'apache') {
lines.push('# セキュリティヘッダー — HTTPヘッダー分析ツールで生成');
lines.push('# https://productivity.works/ja/tools/http-header-analyzer/');
lines.push('#');
lines.push('# .htaccess または Apache バーチャルホスト設定に追加してください');
lines.push('<IfModule mod_headers.c>');
headers.forEach(function(h) { lines.push('  Header always set ' + h[0] + ' "' + h[1] + '"'); });
lines.push('</IfModule>');
raw = lines.join('\n');
out.innerHTML = lines.map(function(line) {
if (line.startsWith('#')) return '<span class="hh-c-comment">' + hEsc(line) + '</span>';
if (line.trim().startsWith('<')) return '<span class="hh-c-tag">' + hEsc(line) + '</span>';
var m = line.match(/^(\s*Header always set )(\S+)(\s+)(".*")$/);
if (m) return hEsc(m[1]) + '<span class="hh-c-key">' + hEsc(m[2]) + '</span>' + hEsc(m[3]) + '<span class="hh-c-val">' + hEsc(m[4]) + '</span>';
return hEsc(line);
}).join('\n');
} else {
lines.push('# セキュリティヘッダー — HTTPヘッダー分析ツールで生成');
lines.push('# https://productivity.works/ja/tools/http-header-analyzer/');
lines.push('#');
lines.push('# server {} または location {} ブロック内に追加してください');
headers.forEach(function(h) { lines.push('add_header ' + h[0] + ' "' + h[1] + '" always;'); });
raw = lines.join('\n');
out.innerHTML = lines.map(function(line) {
if (line.startsWith('#')) return '<span class="hh-c-comment">' + hEsc(line) + '</span>';
var m = line.match(/^(add_header )(\S+)(\s+)(".*")(.*)/);
if (m) return '<span class="hh-c-dir">' + hEsc(m[1]) + '</span><span class="hh-c-key">' + hEsc(m[2]) + '</span>' + hEsc(m[3]) + '<span class="hh-c-val">' + hEsc(m[4]) + '</span>' + hEsc(m[5]);
return hEsc(line);
}).join('\n');
}
out.setAttribute('data-raw', raw);
}
window.hhBuild = hhBuild;

function hhCopyBuild() {
var out = document.getElementById('hh-build-out');
var raw = out ? out.getAttribute('data-raw') : '';
if (!raw) return;
var btn = document.getElementById('hh-build-copy');
if (navigator.clipboard) {
navigator.clipboard.writeText(raw).then(function() {
btn.textContent = 'コピー完了！'; btn.classList.add('hh-copied');
setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('hh-copied'); }, 2000);
});
} else {
var ta = document.createElement('textarea');
ta.value = raw; ta.style.position = 'fixed'; ta.style.opacity = '0';
document.body.appendChild(ta); ta.select(); document.execCommand('copy'); document.body.removeChild(ta);
btn.textContent = 'コピー完了！'; btn.classList.add('hh-copied');
setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('hh-copied'); }, 2000);
}
}
window.hhCopyBuild = hhCopyBuild;

/* ══ パーサー */
var HH_KNOWN = {};
HH_HEADERS.forEach(function(h) { HH_KNOWN[h.name.toLowerCase()] = h; });

function hhParse() {
var raw = document.getElementById('hh-parse-input') ? document.getElementById('hh-parse-input').value : '';
var lines = raw.split(/\r?\n/).filter(function(l) { return l.trim() && !l.match(/^HTTP\//i); });
var out = document.getElementById('hh-parsed-out');
if (!out) return;
if (!lines.length) {
out.innerHTML = '<div class="hh-parse-placeholder">上にヘッダーを貼り付けて「解析」をクリックすると、こちらに解説が表示されます。</div>';
return;
}
var parsed = [];
lines.forEach(function(line) {
var idx = line.indexOf(':');
if (idx < 1) return;
var name = line.substring(0, idx).trim();
var val  = line.substring(idx + 1).trim();
parsed.push({ name: name, val: val, known: HH_KNOWN[name.toLowerCase()] || null });
});
if (!parsed.length) {
out.innerHTML = '<div class="hh-parse-placeholder">有効なヘッダーが見つかりませんでした。各ヘッダーが <code>名前: 値</code> の形式で1行ずつ入力されているか確認してください。</div>';
return;
}
var html = '<div class="hh-parsed-list">';
parsed.forEach(function(p) {
var dir = p.known ? hhBuildDirBadge(p.known.dir) : '';
var desc = p.known ? hEsc(p.known.desc) : '<span class="hh-parsed-unknown">不明またはカスタムヘッダーです。リファレンスデータベースに登録されていません。</span>';
html +=
'<div class="hh-parsed-item">' +
'<div class="hh-parsed-head">' +
'<span class="hh-parsed-name">' + hEsc(p.name) + '</span>' +
dir +
'<span class="hh-parsed-val" title="' + hEsc(p.val) + '">' + hEsc(p.val) + '</span>' +
'</div>' +
'<div class="hh-parsed-desc">' + desc + '</div>' +
'</div>';
});
html += '</div>';
out.innerHTML = html;
}
window.hhParse = hhParse;

/* ══ ユーティリティ */
function hEsc(s) {
return (s || '').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

/* ══ 初期化 */
function hhInit() {
hhBuildCatBtns();
hhBuildCards();
hhBuild();
}
if (document.readyState === 'loading') {
document.addEventListener('DOMContentLoaded', hhInit);
} else {
hhInit();
}

})();
</script>

</div>

---

### 関連ツール

> HTTPステータスコードを確認 → [HTTPステータスコード一覧](/ja/tools/http-status-codes/)

> Apache設定ファイルを生成 → [.htaccessジェネレーター](/ja/tools/htaccess-generator/)

> Base64エンコード・デコード → [Base64エンコーダー](/ja/tools/base64-encoder/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
