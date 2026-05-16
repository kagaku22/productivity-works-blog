---
title: "OGP画像プレビューツール"
date: 2025-05-16
description: "無料のOGP画像プレビューツール。og:titleやog:imageなどのメタタグを入力するだけで、Twitter/X・Facebook・LinkedIn・Discordでのシェア時の見え方を即確認。文字数チェック・HTMLコピー機能付き。"
categories: ["無料ツール"]
slug: "og-image-tester"
ShowToc: false
aliases: ["/ja/tools/og-preview/", "/ja/tools/og-image-tester/"]
cover:
  image: "/images/covers/og-image-tester-ja.png"
  alt: "OGP画像プレビューツール"
---

<div id="og-app">

<style>
#og-app *,
#og-app *::before,
#og-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#og-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Hiragino Sans", "Yu Gothic UI", sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.5;
}

#og-app h2 {
  font-size: 15px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 12px;
  padding-bottom: 6px;
  border-bottom: 2px solid #e2e8f0;
}

#og-app h3 {
  font-size: 13px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 10px;
}

#og-app .og-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 20px;
}

#og-app .og-field {
  margin-bottom: 14px;
}

#og-app .og-label {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  font-size: 12px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 5px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

#og-app .og-counter {
  font-size: 11px;
  font-weight: 400;
  color: #94a3b8;
}

#og-app .og-counter.warn { color: #f59e0b; }
#og-app .og-counter.over { color: #ef4444; }

#og-app input[type="text"],
#og-app input[type="url"],
#og-app select,
#og-app textarea {
  width: 100%;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  padding: 8px 10px;
  font-size: 13px;
  color: #1e293b;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}

#og-app input[type="text"]:focus,
#og-app input[type="url"]:focus,
#og-app select:focus,
#og-app textarea:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.08);
}

#og-app textarea { resize: vertical; min-height: 60px; }

#og-app .og-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 9px 18px;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: background 0.15s, transform 0.1s;
  font-family: inherit;
}

#og-app .og-btn:active { transform: scale(0.97); }

#og-app .og-btn-primary {
  background: #6366f1;
  color: #fff;
}
#og-app .og-btn-primary:hover { background: #4f46e5; }

#og-app .og-btn-secondary {
  background: #e2e8f0;
  color: #334155;
}
#og-app .og-btn-secondary:hover { background: #cbd5e1; }

#og-app .og-btn-copy {
  background: #0ea5e9;
  color: #fff;
  font-size: 12px;
  padding: 6px 14px;
}
#og-app .og-btn-copy:hover { background: #0284c7; }
#og-app .og-btn-copy.copied { background: #22c55e; }

#og-app .og-row {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

#og-app .og-col {
  flex: 1;
  min-width: 260px;
}

/* Tag grid */
#og-app .og-tags-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 8px;
  margin-bottom: 12px;
}

#og-app .og-tag-item {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 7px;
  padding: 8px 10px;
  font-size: 12px;
}

#og-app .og-tag-name {
  font-weight: 600;
  color: #6366f1;
  font-family: monospace;
  font-size: 11px;
  margin-bottom: 2px;
}

#og-app .og-tag-value {
  color: #334155;
  word-break: break-all;
}

#og-app .og-tag-item.missing {
  border-color: #fca5a5;
  background: #fff5f5;
}
#og-app .og-tag-item.missing .og-tag-name { color: #ef4444; }
#og-app .og-tag-item.missing .og-tag-value { color: #ef4444; font-style: italic; }

/* Warnings */
#og-app .og-warnings {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-bottom: 14px;
}

#og-app .og-warning {
  display: flex;
  align-items: flex-start;
  gap: 8px;
  padding: 8px 12px;
  border-radius: 7px;
  font-size: 12px;
}

#og-app .og-warning.warn { background: #fffbeb; border: 1px solid #fde68a; color: #92400e; }
#og-app .og-warning.ok { background: #f0fdf4; border: 1px solid #bbf7d0; color: #166534; }
#og-app .og-warning.err { background: #fef2f2; border: 1px solid #fecaca; color: #991b1b; }

#og-app .og-warning-icon { font-size: 14px; flex-shrink: 0; margin-top: 1px; }

/* Platform tabs */
#og-app .og-tabs {
  display: flex;
  gap: 4px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

#og-app .og-tab {
  padding: 7px 16px;
  border-radius: 6px;
  border: 1.5px solid #e2e8f0;
  background: #fff;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  color: #64748b;
  transition: all 0.15s;
  font-family: inherit;
}

#og-app .og-tab:hover { border-color: #6366f1; color: #6366f1; }
#og-app .og-tab.active { background: #6366f1; border-color: #6366f1; color: #fff; }

/* Platform previews */
#og-app .og-platform-preview { display: none; }
#og-app .og-platform-preview.active { display: block; }

/* ---- Twitter / X ---- */
#og-app .og-twitter-wrap {
  background: #000;
  border-radius: 12px;
  padding: 20px;
  max-width: 500px;
}

#og-app .og-twitter-card {
  border: 1px solid #2f3336;
  border-radius: 12px;
  overflow: hidden;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  background: #000;
  cursor: pointer;
}

#og-app .og-twitter-img-wrap {
  width: 100%;
  padding-bottom: 52.5%;
  position: relative;
  background: #2f3336;
  overflow: hidden;
}

#og-app .og-twitter-img-wrap img {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: cover;
}

#og-app .og-twitter-img-placeholder {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #536471;
  font-size: 13px;
  flex-direction: column;
  gap: 8px;
}

#og-app .og-twitter-img-placeholder svg { opacity: 0.4; }

#og-app .og-twitter-meta {
  padding: 10px 14px 12px;
  background: #000;
  border-top: 1px solid #2f3336;
}

#og-app .og-twitter-domain {
  font-size: 13px;
  color: #536471;
  margin-bottom: 2px;
}

#og-app .og-twitter-title {
  font-size: 15px;
  font-weight: 700;
  color: #e7e9ea;
  line-height: 1.3;
  margin-bottom: 2px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#og-app .og-twitter-desc {
  font-size: 13px;
  color: #536471;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ---- Facebook ---- */
#og-app .og-fb-wrap {
  background: #f0f2f5;
  border-radius: 8px;
  padding: 20px;
  max-width: 500px;
}

#og-app .og-fb-card {
  border: 1px solid #dddfe2;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

#og-app .og-fb-img-wrap {
  width: 100%;
  padding-bottom: 52.5%;
  position: relative;
  background: #e4e6ea;
  overflow: hidden;
}

#og-app .og-fb-img-wrap img {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: cover;
}

#og-app .og-fb-img-placeholder {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #bcc0c4;
  font-size: 13px;
  flex-direction: column;
  gap: 8px;
}

#og-app .og-fb-meta {
  padding: 10px 12px 12px;
  border-top: 1px solid #dddfe2;
  background: #f2f3f5;
}

#og-app .og-fb-domain {
  font-size: 11px;
  color: #606770;
  text-transform: uppercase;
  letter-spacing: 0.03em;
  margin-bottom: 2px;
}

#og-app .og-fb-title {
  font-size: 16px;
  font-weight: 700;
  color: #1c1e21;
  line-height: 1.3;
  margin-bottom: 3px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#og-app .og-fb-desc {
  font-size: 14px;
  color: #606770;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ---- LinkedIn ---- */
#og-app .og-li-wrap {
  background: #f3f2ef;
  border-radius: 8px;
  padding: 20px;
  max-width: 500px;
}

#og-app .og-li-card {
  border: 1px solid #e0dfdb;
  border-radius: 2px;
  overflow: hidden;
  background: #fff;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

#og-app .og-li-img-wrap {
  width: 100%;
  padding-bottom: 52.5%;
  position: relative;
  background: #e8e6e1;
  overflow: hidden;
}

#og-app .og-li-img-wrap img {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: cover;
}

#og-app .og-li-img-placeholder {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #b0aba2;
  font-size: 13px;
  flex-direction: column;
  gap: 8px;
}

#og-app .og-li-meta {
  padding: 8px 12px 12px;
  border-top: 1px solid #e0dfdb;
  background: #eef3f8;
}

#og-app .og-li-title {
  font-size: 14px;
  font-weight: 600;
  color: rgba(0,0,0,0.9);
  line-height: 1.3;
  margin-bottom: 3px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#og-app .og-li-domain {
  font-size: 12px;
  color: rgba(0,0,0,0.6);
}

/* ---- Discord ---- */
#og-app .og-dc-wrap {
  background: #36393f;
  border-radius: 8px;
  padding: 20px;
  max-width: 500px;
}

#og-app .og-dc-embed {
  border-left: 4px solid #5865f2;
  background: #2f3136;
  border-radius: 4px;
  padding: 12px 16px;
  font-family: "Whitney", "Helvetica Neue", Helvetica, Arial, sans-serif;
}

#og-app .og-dc-site {
  font-size: 12px;
  font-weight: 600;
  color: #fff;
  margin-bottom: 4px;
}

#og-app .og-dc-title {
  font-size: 15px;
  font-weight: 600;
  color: #00aff4;
  margin-bottom: 4px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#og-app .og-dc-desc {
  font-size: 13px;
  color: #dcddde;
  margin-bottom: 12px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  line-height: 1.4;
}

#og-app .og-dc-img {
  width: 100%;
  border-radius: 4px;
  display: block;
  max-height: 300px;
  object-fit: cover;
}

#og-app .og-dc-img-placeholder {
  width: 100%;
  height: 180px;
  background: #40444b;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #72767d;
  font-size: 13px;
  flex-direction: column;
  gap: 8px;
}

/* Image dimension checker */
#og-app .og-dim-result {
  margin-top: 10px;
  padding: 10px 14px;
  border-radius: 7px;
  font-size: 12px;
  display: none;
}

#og-app .og-dim-result.show { display: block; }
#og-app .og-dim-result.ok { background: #f0fdf4; border: 1px solid #bbf7d0; color: #166534; }
#og-app .og-dim-result.warn { background: #fffbeb; border: 1px solid #fde68a; color: #92400e; }
#og-app .og-dim-result.err { background: #fef2f2; border: 1px solid #fecaca; color: #991b1b; }

/* Output code */
#og-app .og-code-block {
  background: #0f172a;
  border-radius: 8px;
  padding: 14px 16px;
  font-family: "Fira Code", "Cascadia Code", monospace;
  font-size: 12px;
  color: #94a3b8;
  overflow-x: auto;
  white-space: pre;
  line-height: 1.6;
  margin-bottom: 10px;
}

/* Responsive */
@media (max-width: 600px) {
  #og-app .og-row { flex-direction: column; }
  #og-app .og-col { min-width: 0; }
  #og-app .og-tabs { gap: 3px; }
  #og-app .og-tab { padding: 6px 12px; font-size: 11px; }
}
</style>

<!-- ===== 手動入力 ===== -->
<div class="og-card">
  <h2>OGタグを入力してプレビュー</h2>

  <div class="og-row">
    <div class="og-col">
      <div class="og-field">
        <div class="og-label">
          <span>og:title（タイトル）</span>
          <span class="og-counter" id="og-title-count">0 / 60文字</span>
        </div>
        <input type="text" id="og-title" placeholder="ページのタイトルを入力（推奨: 60文字以内）" maxlength="200">
      </div>

      <div class="og-field">
        <div class="og-label">
          <span>og:description（説明文）</span>
          <span class="og-counter" id="og-desc-count">0 / 155文字</span>
        </div>
        <textarea id="og-desc" rows="3" placeholder="SNSシェア時に表示される説明文（推奨: 155文字以内）"></textarea>
      </div>

      <div class="og-field">
        <div class="og-label"><span>og:url（ページURL）</span></div>
        <input type="url" id="og-url" placeholder="https://example.com/my-page">
      </div>
    </div>

    <div class="og-col">
      <div class="og-field">
        <div class="og-label"><span>og:image（画像URL）</span></div>
        <input type="url" id="og-image" placeholder="https://example.com/og-image.png">
        <div class="og-dim-result" id="og-dim-result"></div>
      </div>

      <div class="og-field">
        <div class="og-label"><span>og:type（種別）</span></div>
        <select id="og-type">
          <option value="website">website</option>
          <option value="article">article</option>
          <option value="product">product</option>
          <option value="profile">profile</option>
          <option value="video.other">video.other</option>
        </select>
      </div>

      <div class="og-field">
        <div class="og-label"><span>twitter:card</span></div>
        <select id="og-twcard">
          <option value="summary_large_image">summary_large_image（大画像）</option>
          <option value="summary">summary（小画像）</option>
          <option value="app">app</option>
          <option value="player">player</option>
        </select>
      </div>

      <div class="og-field">
        <div class="og-label"><span>twitter:site（任意）</span></div>
        <input type="text" id="og-twsite" placeholder="@yourusername">
      </div>
    </div>
  </div>

  <div style="display:flex;gap:10px;flex-wrap:wrap;margin-top:4px;">
    <button class="og-btn og-btn-primary" onclick="ogUpdate()">プレビューを更新</button>
    <button class="og-btn og-btn-secondary" onclick="ogReset()">リセット</button>
  </div>
</div>

<!-- ===== 分析 ===== -->
<div class="og-card" id="og-analysis-card" style="display:none;">
  <h2>チェック結果</h2>
  <div class="og-warnings" id="og-warnings"></div>
</div>

<!-- ===== 検出タグ ===== -->
<div class="og-card" id="og-tags-card" style="display:none;">
  <h2>設定済みOGタグ一覧</h2>
  <div class="og-tags-grid" id="og-tags-grid"></div>
</div>

<!-- ===== プラットフォームプレビュー ===== -->
<div class="og-card" id="og-preview-card" style="display:none;">
  <h2>プラットフォーム別プレビュー</h2>
  <div class="og-tabs">
    <button class="og-tab active" onclick="ogTab(this,'twitter')">Twitter / X</button>
    <button class="og-tab" onclick="ogTab(this,'facebook')">Facebook</button>
    <button class="og-tab" onclick="ogTab(this,'linkedin')">LinkedIn</button>
    <button class="og-tab" onclick="ogTab(this,'discord')">Discord</button>
  </div>

  <!-- Twitter -->
  <div class="og-platform-preview active" id="prev-twitter">
    <div class="og-twitter-wrap">
      <div class="og-twitter-card">
        <div class="og-twitter-img-wrap" id="tw-img-wrap">
          <div class="og-twitter-img-placeholder" id="tw-img-ph">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="M21 15l-5-5L5 21"/></svg>
            画像が未設定です
          </div>
          <img id="tw-img" src="" alt="" style="display:none;">
        </div>
        <div class="og-twitter-meta">
          <div class="og-twitter-domain" id="tw-domain">example.com</div>
          <div class="og-twitter-title" id="tw-title">ページタイトル</div>
          <div class="og-twitter-desc" id="tw-desc">ここにページの説明が表示されます。</div>
        </div>
      </div>
    </div>
    <p style="font-size:11px;color:#94a3b8;margin-top:8px;">Twitter/Xは <code>summary_large_image</code> カードで1200&times;630pxの画像を推奨。</p>
  </div>

  <!-- Facebook -->
  <div class="og-platform-preview" id="prev-facebook">
    <div class="og-fb-wrap">
      <div class="og-fb-card">
        <div class="og-fb-img-wrap" id="fb-img-wrap">
          <div class="og-fb-img-placeholder" id="fb-img-ph">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="M21 15l-5-5L5 21"/></svg>
            画像が未設定です
          </div>
          <img id="fb-img" src="" alt="" style="display:none;">
        </div>
        <div class="og-fb-meta">
          <div class="og-fb-domain" id="fb-domain">example.com</div>
          <div class="og-fb-title" id="fb-title">ページタイトル</div>
          <div class="og-fb-desc" id="fb-desc">ここにページの説明が表示されます。</div>
        </div>
      </div>
    </div>
    <p style="font-size:11px;color:#94a3b8;margin-top:8px;">Facebookは1200&times;630px推奨。最小サイズは200&times;200px。</p>
  </div>

  <!-- LinkedIn -->
  <div class="og-platform-preview" id="prev-linkedin">
    <div class="og-li-wrap">
      <div class="og-li-card">
        <div class="og-li-img-wrap" id="li-img-wrap">
          <div class="og-li-img-placeholder" id="li-img-ph">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="M21 15l-5-5L5 21"/></svg>
            画像が未設定です
          </div>
          <img id="li-img" src="" alt="" style="display:none;">
        </div>
        <div class="og-li-meta">
          <div class="og-li-title" id="li-title">ページタイトル</div>
          <div class="og-li-domain" id="li-domain">example.com</div>
        </div>
      </div>
    </div>
    <p style="font-size:11px;color:#94a3b8;margin-top:8px;">LinkedInは1200&times;627px推奨。カード表示ではタイトルのみ（説明文は非表示）。</p>
  </div>

  <!-- Discord -->
  <div class="og-platform-preview" id="prev-discord">
    <div class="og-dc-wrap">
      <div class="og-dc-embed">
        <div class="og-dc-site" id="dc-site">example.com</div>
        <div class="og-dc-title" id="dc-title">ページタイトル</div>
        <div class="og-dc-desc" id="dc-desc">ここにページの説明が表示されます。</div>
        <div id="dc-img-wrap">
          <div class="og-dc-img-placeholder" id="dc-img-ph">
            <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="M21 15l-5-5L5 21"/></svg>
            画像が未設定です
          </div>
          <img id="dc-img" src="" alt="" class="og-dc-img" style="display:none;">
        </div>
      </div>
    </div>
    <p style="font-size:11px;color:#94a3b8;margin-top:8px;">Discordはog:imageとog:descriptionを読み込みます。埋め込みの最大幅は約400px。</p>
  </div>
</div>

<!-- ===== HTMLコード出力 ===== -->
<div class="og-card" id="og-output-card" style="display:none;">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
    <h2 style="margin:0;border:none;padding:0;">HTMLメタタグ</h2>
    <button class="og-btn og-btn-copy" id="og-copy-btn" onclick="ogCopyTags()">HTMLをコピー</button>
  </div>
  <div class="og-code-block" id="og-code-out"></div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<script>
(function(){
  var titleEl   = document.getElementById('og-title');
  var descEl    = document.getElementById('og-desc');
  var urlEl     = document.getElementById('og-url');
  var imageEl   = document.getElementById('og-image');
  var typeEl    = document.getElementById('og-type');
  var twcardEl  = document.getElementById('og-twcard');
  var twsiteEl  = document.getElementById('og-twsite');

  // ライブ文字数カウント
  function updateCount(inputEl, countEl, limit, unit) {
    var n = inputEl.value.length;
    countEl.textContent = n + ' / ' + limit + unit;
    countEl.className = 'og-counter' + (n > limit ? ' over' : n > limit * 0.85 ? ' warn' : '');
  }

  titleEl.addEventListener('input', function(){ updateCount(titleEl, document.getElementById('og-title-count'), 60, '文字'); });
  descEl.addEventListener('input',  function(){ updateCount(descEl,  document.getElementById('og-desc-count'),  155, '文字'); });

  // 画像サイズチェック
  imageEl.addEventListener('change', ogCheckImage);
  imageEl.addEventListener('blur',   ogCheckImage);

  function ogCheckImage() {
    var src = imageEl.value.trim();
    var dimEl = document.getElementById('og-dim-result');
    if (!src) { dimEl.className = 'og-dim-result'; return; }
    var img = new Image();
    img.onload = function() {
      var w = img.naturalWidth, h = img.naturalHeight;
      var ratio = (w / h).toFixed(2);
      var ideal = (1200 / 630).toFixed(2);
      var msg = w + ' x ' + h + 'px（比率 ' + ratio + '）';
      if (w >= 1200 && h >= 630 && ratio === ideal) {
        dimEl.className = 'og-dim-result ok show';
        dimEl.innerHTML = '&#10003; ' + msg + ' &mdash; 全プラットフォームに最適なサイズです！';
      } else if (w >= 600 && h >= 315) {
        dimEl.className = 'og-dim-result warn show';
        dimEl.innerHTML = '&#9888; ' + msg + ' &mdash; 表示可能ですが、1200&times;630px推奨です。';
      } else {
        dimEl.className = 'og-dim-result err show';
        dimEl.innerHTML = '&#10007; ' + msg + ' &mdash; 小さすぎます。最低600&times;315px以上にしてください。';
      }
    };
    img.onerror = function() {
      dimEl.className = 'og-dim-result warn show';
      dimEl.innerHTML = '&#9888; 画像を読み込めませんでした（CORS制限または無効なURLの可能性があります）。';
    };
    img.src = src;
  }

  // タブ切り替え
  window.ogTab = function(btn, id) {
    document.querySelectorAll('#og-app .og-tab').forEach(function(t){ t.classList.remove('active'); });
    document.querySelectorAll('#og-app .og-platform-preview').forEach(function(p){ p.classList.remove('active'); });
    btn.classList.add('active');
    document.getElementById('prev-' + id).classList.add('active');
  };

  function getDomain(url) {
    try { return new URL(url).hostname.replace('www.',''); } catch(e) { return url || 'example.com'; }
  }

  function setImg(imgId, phId, src) {
    var imgEl = document.getElementById(imgId);
    var phEl  = document.getElementById(phId);
    if (src) {
      imgEl.src = src;
      imgEl.style.display = 'block';
      phEl.style.display  = 'none';
    } else {
      imgEl.style.display = 'none';
      phEl.style.display  = 'flex';
    }
  }

  window.ogUpdate = function() {
    var title   = titleEl.value.trim();
    var desc    = descEl.value.trim();
    var url     = urlEl.value.trim();
    var image   = imageEl.value.trim();
    var type    = typeEl.value;
    var twcard  = twcardEl.value;
    var twsite  = twsiteEl.value.trim();
    var domain  = getDomain(url);

    // カードを表示
    document.getElementById('og-analysis-card').style.display = '';
    document.getElementById('og-tags-card').style.display     = '';
    document.getElementById('og-preview-card').style.display  = '';
    document.getElementById('og-output-card').style.display   = '';

    // --- チェック結果 ---
    var warnings = [];

    if (!title) {
      warnings.push({type:'err', text:'og:title が設定されていません。SNSシェアに必須のタグです。'});
    } else if (title.length > 60) {
      warnings.push({type:'warn', text:'og:title が ' + title.length + ' 文字あります。60文字以内を推奨。プラットフォームによっては切り詰められます。'});
    } else {
      warnings.push({type:'ok', text:'og:title の文字数は適切です（' + title.length + '/60文字）。'});
    }

    if (!desc) {
      warnings.push({type:'warn', text:'og:description が設定されていません。説明文なしでシェアされる可能性があります。'});
    } else if (desc.length > 155) {
      warnings.push({type:'warn', text:'og:description が ' + desc.length + ' 文字あります。155文字以内を推奨。'});
    } else {
      warnings.push({type:'ok', text:'og:description の文字数は適切です（' + desc.length + '/155文字）。'});
    }

    if (!image) {
      warnings.push({type:'err', text:'og:image が設定されていません。画像なしではほとんどのプラットフォームでカードが表示されません。'});
    } else {
      warnings.push({type:'ok', text:'og:image が設定されています。'});
    }

    if (!url) {
      warnings.push({type:'warn', text:'og:url が設定されていません。このページの正規URLを設定することを推奨します。'});
    }

    var wHtml = '';
    warnings.forEach(function(w) {
      var icon = w.type === 'ok' ? '&#10003;' : w.type === 'warn' ? '&#9888;' : '&#10007;';
      wHtml += '<div class="og-warning ' + w.type + '"><span class="og-warning-icon">' + icon + '</span><span>' + w.text + '</span></div>';
    });
    document.getElementById('og-warnings').innerHTML = wHtml;

    // --- タグ一覧 ---
    var tags = [
      { name: 'og:title',        val: title },
      { name: 'og:description',  val: desc },
      { name: 'og:url',          val: url },
      { name: 'og:image',        val: image },
      { name: 'og:type',         val: type },
      { name: 'twitter:card',    val: twcard },
      { name: 'twitter:title',   val: title },
      { name: 'twitter:description', val: desc },
      { name: 'twitter:image',   val: image },
    ];
    if (twsite) tags.push({ name: 'twitter:site', val: twsite });

    var gridHtml = '';
    tags.forEach(function(t) {
      var missing = !t.val;
      gridHtml += '<div class="og-tag-item' + (missing ? ' missing' : '') + '">'
        + '<div class="og-tag-name">' + esc(t.name) + '</div>'
        + '<div class="og-tag-value">' + (missing ? '未設定' : esc(t.val.length > 80 ? t.val.slice(0,80)+'...' : t.val)) + '</div>'
        + '</div>';
    });
    document.getElementById('og-tags-grid').innerHTML = gridHtml;

    // --- プラットフォームプレビュー ---
    // Twitter
    document.getElementById('tw-domain').textContent = domain;
    document.getElementById('tw-title').textContent  = title || 'ページタイトル';
    document.getElementById('tw-desc').textContent   = desc  || 'ここにページの説明が表示されます。';
    setImg('tw-img', 'tw-img-ph', image);

    // Facebook
    document.getElementById('fb-domain').textContent = domain;
    document.getElementById('fb-title').textContent  = title || 'ページタイトル';
    document.getElementById('fb-desc').textContent   = desc  || 'ここにページの説明が表示されます。';
    setImg('fb-img', 'fb-img-ph', image);

    // LinkedIn
    document.getElementById('li-domain').textContent = domain;
    document.getElementById('li-title').textContent  = title || 'ページタイトル';
    setImg('li-img', 'li-img-ph', image);

    // Discord
    document.getElementById('dc-site').textContent  = domain;
    document.getElementById('dc-title').textContent = title || 'ページタイトル';
    document.getElementById('dc-desc').textContent  = desc  || 'ここにページの説明が表示されます。';
    setImg('dc-img', 'dc-img-ph', image);

    // --- HTMLコード出力 ---
    var lines = [];
    lines.push('<meta property="og:title" content="' + esc(title) + '">');
    if (desc)  lines.push('<meta property="og:description" content="' + esc(desc) + '">');
    if (url)   lines.push('<meta property="og:url" content="' + esc(url) + '">');
    if (image) lines.push('<meta property="og:image" content="' + esc(image) + '">');
    lines.push('<meta property="og:type" content="' + esc(type) + '">');
    lines.push('<meta name="twitter:card" content="' + esc(twcard.split('（')[0]) + '">');
    lines.push('<meta name="twitter:title" content="' + esc(title) + '">');
    if (desc)   lines.push('<meta name="twitter:description" content="' + esc(desc) + '">');
    if (image)  lines.push('<meta name="twitter:image" content="' + esc(image) + '">');
    if (twsite) lines.push('<meta name="twitter:site" content="' + esc(twsite) + '">');

    document.getElementById('og-code-out').textContent = lines.join('\n');
  };

  window.ogReset = function() {
    [titleEl, descEl, urlEl, imageEl, twsiteEl].forEach(function(el){ el.value = ''; });
    typeEl.value   = 'website';
    twcardEl.value = 'summary_large_image';
    document.getElementById('og-title-count').textContent = '0 / 60文字';
    document.getElementById('og-desc-count').textContent  = '0 / 155文字';
    document.getElementById('og-dim-result').className    = 'og-dim-result';
    document.getElementById('og-analysis-card').style.display = 'none';
    document.getElementById('og-tags-card').style.display     = 'none';
    document.getElementById('og-preview-card').style.display  = 'none';
    document.getElementById('og-output-card').style.display   = 'none';
  };

  window.ogCopyTags = function() {
    var code = document.getElementById('og-code-out').textContent;
    var btn  = document.getElementById('og-copy-btn');
    if (!code) return;
    navigator.clipboard.writeText(code).then(function(){
      btn.textContent = 'コピーしました！';
      btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = 'HTMLをコピー'; btn.classList.remove('copied'); }, 1800);
    }).catch(function(){
      var ta = document.createElement('textarea');
      ta.value = code; ta.style.position = 'fixed'; ta.style.opacity = '0';
      document.body.appendChild(ta); ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      btn.textContent = 'コピーしました！';
      btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = 'HTMLをコピー'; btn.classList.remove('copied'); }, 1800);
    });
  };

  function esc(s) {
    return String(s).replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }
})();
</script>

</div>

---
### 関連ツール
> メタタグ生成 → [メタタグ生成ツール](/ja/tools/meta-tag-generator/)
> プレースホルダー画像 → [プレースホルダー画像生成](/ja/tools/placeholder-image/)
---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
