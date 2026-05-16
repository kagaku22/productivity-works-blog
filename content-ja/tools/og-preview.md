---
title: "OGPプレビュー — SNSシェアデバッガー"
date: 2025-05-16
description: "Facebook・Twitter・LinkedIn・Google検索でのページ表示をプレビュー。OGメタタグをライブプレビュー付きで生成。文字数制限と画像サイズを確認。"
categories: ["無料ツール"]
slug: "og-preview"
ShowToc: false
aliases:
  - "/ja/tools/og-preview/"
  - "/ja/tools/og-preview/"
cover:
  image: "/images/covers/og-preview-ja.png"
  alt: "OGPプレビュー"
---

URLを貼り付けるか、以下のフィールドを入力すると、Facebook・Twitter・LinkedIn・Google検索でページがどのように表示されるかをリアルタイムでプレビューできます。

<div id="og-app">

<style>
/* ── Reset & base ── */
#og-app *,
#og-app *::before,
#og-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#og-app {
  font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  font-size: 15px;
  color: #1a1a2e;
  line-height: 1.6;
}

/* ── Layout ── */
#og-app .og-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
  margin-top: 20px;
}
@media (max-width: 760px) {
  #og-app .og-grid {
    grid-template-columns: 1fr;
  }
}

/* ── Panel ── */
#og-app .og-panel {
  background: #f8f9fc;
  border: 1px solid #dde1ea;
  border-radius: 10px;
  padding: 22px 20px;
}
#og-app .og-panel h2 {
  font-size: 15px;
  font-weight: 700;
  color: #2c3e6b;
  margin-bottom: 16px;
  padding-bottom: 10px;
  border-bottom: 2px solid #dde1ea;
  letter-spacing: 0.02em;
}

/* ── Form fields ── */
#og-app .og-field {
  margin-bottom: 14px;
}
#og-app .og-field label {
  display: block;
  font-size: 12px;
  font-weight: 600;
  color: #4a5378;
  margin-bottom: 5px;
  letter-spacing: 0.01em;
}
#og-app .og-field input,
#og-app .og-field select,
#og-app .og-field textarea {
  width: 100%;
  padding: 8px 11px;
  border: 1px solid #c8cdd8;
  border-radius: 6px;
  font-size: 13px;
  color: #1a1a2e;
  background: #fff;
  transition: border-color 0.18s;
  outline: none;
  font-family: inherit;
}
#og-app .og-field input:focus,
#og-app .og-field select:focus,
#og-app .og-field textarea:focus {
  border-color: #4f6ef7;
  box-shadow: 0 0 0 3px rgba(79,110,247,0.12);
}
#og-app .og-field textarea {
  resize: vertical;
  min-height: 64px;
}

/* ── Character counter ── */
#og-app .og-char-info {
  display: flex;
  justify-content: flex-end;
  font-size: 11px;
  margin-top: 4px;
  color: #888;
  transition: color 0.2s;
}
#og-app .og-char-info.warn {
  color: #d97706;
  font-weight: 600;
}
#og-app .og-char-info.over {
  color: #dc2626;
  font-weight: 700;
}

/* ── Image hint ── */
#og-app .og-img-hint {
  font-size: 11px;
  color: #6b7280;
  margin-top: 5px;
  line-height: 1.5;
}
#og-app .og-img-hint span {
  display: inline-block;
  background: #e8eeff;
  color: #3b5bdb;
  border-radius: 4px;
  padding: 1px 6px;
  font-weight: 600;
  font-size: 10.5px;
  margin-right: 4px;
}

/* ── Buttons ── */
#og-app .og-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 18px;
}
#og-app .og-btn {
  padding: 9px 18px;
  border-radius: 7px;
  border: none;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.18s, transform 0.1s;
  font-family: inherit;
}
#og-app .og-btn:active {
  transform: scale(0.97);
}
#og-app .og-btn-primary {
  background: #4f6ef7;
  color: #fff;
}
#og-app .og-btn-primary:hover {
  background: #3a56d4;
}
#og-app .og-btn-secondary {
  background: #e8eeff;
  color: #3b5bdb;
  border: 1px solid #c5d0ff;
}
#og-app .og-btn-secondary:hover {
  background: #d5dfff;
}
#og-app .og-btn-success {
  background: #059669;
  color: #fff;
}
#og-app .og-btn-success:hover {
  background: #047857;
}

/* ── Toast ── */
#og-app .og-toast {
  display: none;
  position: fixed;
  bottom: 28px;
  right: 28px;
  background: #1e293b;
  color: #fff;
  padding: 11px 20px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 500;
  z-index: 9999;
  box-shadow: 0 4px 18px rgba(0,0,0,0.22);
  animation: og-fadeIn 0.25s ease;
}
@keyframes og-fadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* ── Section divider ── */
#og-app .og-section-label {
  font-size: 11px;
  font-weight: 700;
  color: #4f6ef7;
  letter-spacing: 0.05em;
  margin: 18px 0 10px;
  padding-left: 2px;
}

/* ── Preview panels ── */
#og-app .og-previews {
  margin-top: 28px;
}
#og-app .og-previews h2 {
  font-size: 17px;
  font-weight: 700;
  color: #2c3e6b;
  margin-bottom: 18px;
}
#og-app .og-preview-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
@media (max-width: 680px) {
  #og-app .og-preview-grid {
    grid-template-columns: 1fr;
  }
}

/* ── Facebook card ── */
#og-app .og-card-fb {
  border: 1px solid #dde1ea;
  border-radius: 4px;
  overflow: hidden;
  background: #fff;
  font-family: Helvetica, Arial, sans-serif;
  max-width: 500px;
}
#og-app .og-card-fb .og-card-img {
  width: 100%;
  aspect-ratio: 1.91/1;
  object-fit: cover;
  background: #e5e7eb;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #9ca3af;
  font-size: 13px;
}
#og-app .og-card-fb .og-card-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
#og-app .og-card-fb .og-card-body {
  padding: 10px 12px 12px;
  border-top: 1px solid #dde1ea;
  background: #f2f3f5;
}
#og-app .og-card-fb .og-card-domain {
  font-size: 11px;
  color: #606770;
  text-transform: uppercase;
  letter-spacing: 0.02em;
  margin-bottom: 3px;
}
#og-app .og-card-fb .og-card-title {
  font-size: 16px;
  font-weight: 700;
  color: #1c1e21;
  line-height: 1.3;
  margin-bottom: 4px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
#og-app .og-card-fb .og-card-desc {
  font-size: 14px;
  color: #606770;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ── Twitter card ── */
#og-app .og-card-tw {
  border: 1px solid #e1e8ed;
  border-radius: 14px;
  overflow: hidden;
  background: #fff;
  font-family: -apple-system, "Segoe UI", sans-serif;
  max-width: 500px;
}
#og-app .og-card-tw.summary .og-tw-inner {
  display: flex;
  flex-direction: row;
}
#og-app .og-card-tw.summary .og-card-img-tw {
  width: 120px;
  min-width: 120px;
  aspect-ratio: 1/1;
  flex-shrink: 0;
}
#og-app .og-card-img-tw {
  width: 100%;
  background: #e5e7eb;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #9ca3af;
  font-size: 13px;
  overflow: hidden;
}
#og-app .og-card-img-tw img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
#og-app .og-card-tw .og-card-body-tw {
  padding: 10px 14px 12px;
  flex: 1;
}
#og-app .og-card-tw .og-card-domain-tw {
  font-size: 13px;
  color: #8899a6;
  margin-bottom: 3px;
}
#og-app .og-card-tw .og-card-title-tw {
  font-size: 15px;
  font-weight: 700;
  color: #14171a;
  line-height: 1.3;
  margin-bottom: 3px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
#og-app .og-card-tw .og-card-desc-tw {
  font-size: 13px;
  color: #657786;
  line-height: 1.4;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ── LinkedIn card ── */
#og-app .og-card-li {
  border: 1px solid #d6d6d6;
  border-radius: 2px;
  overflow: hidden;
  background: #fff;
  font-family: -apple-system, "Segoe UI", sans-serif;
  max-width: 500px;
}
#og-app .og-card-li .og-card-img-li {
  width: 100%;
  aspect-ratio: 1.91/1;
  background: #e5e7eb;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #9ca3af;
  font-size: 13px;
  overflow: hidden;
}
#og-app .og-card-li .og-card-img-li img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
#og-app .og-card-li .og-card-body-li {
  padding: 8px 12px 10px;
  background: #f3f2ef;
  border-top: 1px solid #d6d6d6;
}
#og-app .og-card-li .og-card-title-li {
  font-size: 14px;
  font-weight: 600;
  color: rgba(0,0,0,0.9);
  line-height: 1.35;
  margin-bottom: 2px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
#og-app .og-card-li .og-card-domain-li {
  font-size: 12px;
  color: rgba(0,0,0,0.6);
}

/* ── Google SERP ── */
#og-app .og-card-google {
  background: #fff;
  padding: 14px 16px;
  border: 1px solid #dde1ea;
  border-radius: 8px;
  max-width: 600px;
  font-family: arial, sans-serif;
}
#og-app .og-card-google .og-serp-url {
  font-size: 12px;
  color: #202124;
  line-height: 1.4;
  margin-bottom: 4px;
}
#og-app .og-card-google .og-serp-breadcrumb {
  font-size: 12px;
  color: #5f6368;
}
#og-app .og-card-google .og-serp-title {
  font-size: 20px;
  color: #1a0dab;
  line-height: 1.3;
  margin-bottom: 3px;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
#og-app .og-card-google .og-serp-desc {
  font-size: 14px;
  color: #4d5156;
  line-height: 1.58;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ── Card label ── */
#og-app .og-card-label {
  font-size: 11px;
  font-weight: 700;
  color: #6b7280;
  letter-spacing: 0.05em;
  margin-bottom: 7px;
}

/* ── Code output ── */
#og-app .og-code-wrap {
  margin-top: 24px;
  display: none;
}
#og-app .og-code-wrap h3 {
  font-size: 14px;
  font-weight: 700;
  color: #2c3e6b;
  margin-bottom: 8px;
}
#og-app .og-code-box {
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 8px;
  padding: 16px;
  font-family: "Fira Code", "Cascadia Code", Consolas, monospace;
  font-size: 12px;
  line-height: 1.7;
  overflow-x: auto;
  white-space: pre;
}

/* ── Dimension table ── */
#og-app .og-dim-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 12.5px;
  margin-top: 4px;
}
#og-app .og-dim-table th {
  text-align: left;
  font-weight: 600;
  color: #4a5378;
  padding: 5px 8px;
  background: #eef0f8;
  border: 1px solid #dde1ea;
}
#og-app .og-dim-table td {
  padding: 5px 8px;
  border: 1px solid #dde1ea;
  color: #374151;
}
#og-app .og-dim-table tr:nth-child(even) td {
  background: #f8f9fc;
}

/* ── freee CTA ── */
#og-app .og-freee-cta {
  margin-top: 32px;
  background: linear-gradient(135deg, #e8f4fd 0%, #f0f9ee 100%);
  border: 1px solid #b3d9f7;
  border-radius: 10px;
  padding: 20px 22px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
}
@media (max-width: 600px) {
  #og-app .og-freee-cta {
    flex-direction: column;
  }
}
#og-app .og-freee-cta .og-freee-icon {
  font-size: 32px;
  flex-shrink: 0;
  line-height: 1;
}
#og-app .og-freee-cta .og-freee-body h3 {
  font-size: 14px;
  font-weight: 700;
  color: #0f4c81;
  margin-bottom: 5px;
}
#og-app .og-freee-cta .og-freee-body p {
  font-size: 13px;
  color: #374151;
  line-height: 1.6;
  margin-bottom: 10px;
}
#og-app .og-freee-cta .og-freee-body a.og-freee-link {
  display: inline-block;
  background: #0f6fbd;
  color: #fff;
  padding: 7px 16px;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.18s;
}
#og-app .og-freee-cta .og-freee-body a.og-freee-link:hover {
  background: #0a5699;
}
</style>

<div class="og-grid">

  <!-- ═══ 左: OGフィールド ═══ -->
  <div class="og-panel">
    <h2>OGプロパティ設定</h2>

    <div class="og-section-label">基本タグ</div>

    <div class="og-field">
      <label for="og-title">og:title（タイトル）</label>
      <input type="text" id="og-title" placeholder="ページのタイトル" maxlength="200">
      <div class="og-char-info" id="og-title-count">0 / 60</div>
    </div>

    <div class="og-field">
      <label for="og-description">og:description（説明文）</label>
      <textarea id="og-description" placeholder="ページ内容の簡潔な説明..."></textarea>
      <div class="og-char-info" id="og-desc-count">0 / 160</div>
    </div>

    <div class="og-field">
      <label for="og-url">og:url（ページURL）</label>
      <input type="url" id="og-url" placeholder="https://example.com/page">
    </div>

    <div class="og-field">
      <label for="og-image">og:image（画像URL）</label>
      <input type="url" id="og-image" placeholder="https://example.com/image.jpg">
      <div class="og-img-hint">推奨サイズ: <span>1200 × 630 px</span>（比率 1.91:1）· 最小 600 × 315 px · 最大 8 MB</div>
    </div>

    <div class="og-field">
      <label for="og-type">og:type（コンテンツ種別）</label>
      <select id="og-type">
        <option value="website">website（Webサイト）</option>
        <option value="article">article（記事）</option>
        <option value="product">product（商品）</option>
        <option value="video.other">video.other（動画）</option>
        <option value="music.song">music.song（楽曲）</option>
        <option value="book">book（書籍）</option>
        <option value="profile">profile（プロフィール）</option>
      </select>
    </div>

    <div class="og-field">
      <label for="og-site-name">og:site_name（サイト名）</label>
      <input type="text" id="og-site-name" placeholder="あなたのサイト名">
    </div>

    <div class="og-section-label" style="margin-top:22px;">Twitterカード設定</div>

    <div class="og-field">
      <label for="tw-card">twitter:card（カード種別）</label>
      <select id="tw-card">
        <option value="summary_large_image">summary_large_image（大きな画像）</option>
        <option value="summary">summary（正方形の小さな画像）</option>
      </select>
    </div>

    <div class="og-field">
      <label for="tw-title">twitter:title <em style="font-weight:400;color:#9ca3af;">（空欄の場合は og:title を使用）</em></label>
      <input type="text" id="tw-title" placeholder="Twitter専用タイトル（任意）">
      <div class="og-char-info" id="tw-title-count">0 / 70</div>
    </div>

    <div class="og-field">
      <label for="tw-description">twitter:description <em style="font-weight:400;color:#9ca3af;">（空欄の場合は og:description を使用）</em></label>
      <textarea id="tw-description" placeholder="Twitter専用説明文（任意）"></textarea>
      <div class="og-char-info" id="tw-desc-count">0 / 200</div>
    </div>

    <div class="og-field">
      <label for="tw-image">twitter:image <em style="font-weight:400;color:#9ca3af;">（空欄の場合は og:image を使用）</em></label>
      <input type="url" id="tw-image" placeholder="https://example.com/twitter-image.jpg">
      <div class="og-img-hint">summary_large_image: <span>1200 × 628 px</span> · summary: <span>144 × 144 px</span></div>
    </div>

    <div class="og-btn-row">
      <button class="og-btn og-btn-primary" id="og-generate-btn">HTMLメタタグを生成</button>
      <button class="og-btn og-btn-secondary" id="og-clear-btn">全てクリア</button>
    </div>
  </div>

  <!-- ═══ 右: 画像サイズガイド ═══ -->
  <div class="og-panel">
    <h2>画像サイズ推奨一覧</h2>

    <table class="og-dim-table">
      <thead>
        <tr>
          <th>プラットフォーム</th>
          <th>推奨サイズ</th>
          <th>比率</th>
          <th>上限</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><strong>Facebook</strong></td>
          <td>1200 × 630 px</td>
          <td>1.91:1</td>
          <td>8 MB</td>
        </tr>
        <tr>
          <td><strong>Twitter 大画像</strong></td>
          <td>1200 × 628 px</td>
          <td>約1.91:1</td>
          <td>5 MB</td>
        </tr>
        <tr>
          <td><strong>Twitter 小画像</strong></td>
          <td>144 × 144 px</td>
          <td>1:1</td>
          <td>5 MB</td>
        </tr>
        <tr>
          <td><strong>LinkedIn</strong></td>
          <td>1200 × 627 px</td>
          <td>1.91:1</td>
          <td>5 MB</td>
        </tr>
        <tr>
          <td><strong>Google検索</strong></td>
          <td>（テキストのみ）</td>
          <td>—</td>
          <td>—</td>
        </tr>
      </tbody>
    </table>

    <div style="margin-top:20px;">
      <div class="og-section-label">文字数の目安</div>
      <table class="og-dim-table">
        <thead>
          <tr><th>プラットフォーム</th><th>タイトル</th><th>説明文</th></tr>
        </thead>
        <tbody>
          <tr><td><strong>Facebook OG</strong></td><td>約60文字</td><td>約160文字</td></tr>
          <tr><td><strong>Twitter</strong></td><td>約70文字</td><td>約200文字</td></tr>
          <tr><td><strong>LinkedIn</strong></td><td>約119文字</td><td>約300文字</td></tr>
          <tr><td><strong>Google検索</strong></td><td>約60文字</td><td>約160文字</td></tr>
        </tbody>
      </table>
    </div>

    <div style="margin-top:20px;">
      <div class="og-section-label">設定のコツ</div>
      <ul style="font-size:12.5px;color:#374151;padding-left:18px;line-height:1.9;">
        <li>画像URLは必ずHTTPSを使用してください（HTTPはブロックされる場合があります）。</li>
        <li>FacebookはOGデータをキャッシュします。<a href="https://developers.facebook.com/tools/debug/" target="_blank" rel="noopener" style="color:#4f6ef7;">シェアデバッガー</a>でキャッシュを更新できます。</li>
        <li>Twitterは初回シェア時に画像をクロールします。144×144 px未満の画像は無視されます。</li>
        <li>LinkedInは7日間キャッシュされます。新しいURLを投稿すると再クロールされます。</li>
        <li>タイトルは60文字以内にするとGoogle検索での切り詰めを防げます。</li>
        <li>og:titleと&lt;title&gt;タグの重複は可能な限り避けましょう。</li>
      </ul>
    </div>
  </div>

</div>

<!-- ═══ ライブプレビュー ═══ -->
<div class="og-previews">
  <h2>ライブプレビュー</h2>
  <div class="og-preview-grid">

    <!-- Facebook -->
    <div>
      <div class="og-card-label">Facebook</div>
      <div class="og-card-fb" id="prev-fb">
        <div class="og-card-img" id="prev-fb-img-wrap">
          <span>画像URLを入力してください</span>
        </div>
        <div class="og-card-body">
          <div class="og-card-domain" id="prev-fb-domain">example.com</div>
          <div class="og-card-title" id="prev-fb-title">ページタイトルがここに表示されます</div>
          <div class="og-card-desc" id="prev-fb-desc">ページの説明文がここに表示されます。</div>
        </div>
      </div>
    </div>

    <!-- Twitter -->
    <div>
      <div class="og-card-label">Twitter / X</div>
      <div class="og-card-tw summary-large" id="prev-tw">
        <div class="og-tw-inner">
          <div class="og-card-img-tw" id="prev-tw-img-wrap" style="aspect-ratio:2/1;">
            <span>画像URLを入力してください</span>
          </div>
          <div class="og-card-body-tw">
            <div class="og-card-domain-tw" id="prev-tw-domain">example.com</div>
            <div class="og-card-title-tw" id="prev-tw-title">ページタイトルがここに表示されます</div>
            <div class="og-card-desc-tw" id="prev-tw-desc">ページの説明文がここに表示されます。</div>
          </div>
        </div>
      </div>
    </div>

    <!-- LinkedIn -->
    <div>
      <div class="og-card-label">LinkedIn</div>
      <div class="og-card-li" id="prev-li">
        <div class="og-card-img-li" id="prev-li-img-wrap">
          <span>画像URLを入力してください</span>
        </div>
        <div class="og-card-body-li">
          <div class="og-card-title-li" id="prev-li-title">ページタイトルがここに表示されます</div>
          <div class="og-card-domain-li" id="prev-li-domain">example.com</div>
        </div>
      </div>
    </div>

    <!-- Google SERP -->
    <div>
      <div class="og-card-label">Google検索結果</div>
      <div class="og-card-google">
        <div class="og-serp-url">
          <span id="prev-g-sitename">あなたのサイト</span> &rsaquo;
          <span class="og-serp-breadcrumb" id="prev-g-breadcrumb">example.com</span>
        </div>
        <div class="og-serp-title" id="prev-g-title">ページタイトルがここに表示されます</div>
        <div class="og-serp-desc" id="prev-g-desc">ページの説明文がここに表示されます。Googleはクエリに関連性が高いと判断したページ内のテキストで説明を上書きする場合があります。</div>
      </div>
    </div>

  </div>
</div>

<!-- ═══ 生成コード ═══ -->
<div class="og-code-wrap" id="og-code-section">
  <h3>生成されたHTMLメタタグ</h3>
  <div class="og-btn-row" style="margin-bottom:10px;">
    <button class="og-btn og-btn-success" id="og-copy-btn">クリップボードにコピー</button>
  </div>
  <div class="og-code-box" id="og-code-output"></div>
</div>

<div id="og-toast" class="og-toast">コピーしました!</div>

<!-- ═══ freee CTA ═══ -->
<div class="og-freee-cta">
  <div class="og-freee-icon">📊</div>
  <div class="og-freee-body">
    <h3>ビジネスの会計・経理もスマートに管理しませんか？</h3>
    <p>freeeなら請求書発行・確定申告・給与計算をクラウドで一元管理。個人事業主から法人まで対応。面倒な帳簿作業を自動化して、本業に集中できます。</p>
    <a class="og-freee-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
  </div>
</div>

<script>
(function() {
  'use strict';

  /* ── ヘルパー ── */
  function el(id) { return document.getElementById(id); }

  function getDomain(url) {
    try {
      return new URL(url).hostname.replace(/^www\./, '');
    } catch(e) {
      return url ? url.replace(/^https?:\/\/(www\.)?/, '').split('/')[0] : 'example.com';
    }
  }

  function escapeHtml(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  /* ── 文字数カウンター ── */
  function bindCounter(inputId, counterId, limit) {
    var inp = el(inputId);
    var ctr = el(counterId);
    if (!inp || !ctr) return;
    inp.addEventListener('input', function() {
      var len = inp.value.length;
      ctr.textContent = len + ' / ' + limit;
      ctr.className = 'og-char-info' +
        (len > limit ? ' over' : (len > limit * 0.85 ? ' warn' : ''));
    });
  }

  bindCounter('og-title',       'og-title-count',  60);
  bindCounter('og-description', 'og-desc-count',  160);
  bindCounter('tw-title',       'tw-title-count',   70);
  bindCounter('tw-description', 'tw-desc-count',  200);

  /* ── 画像レンダリング ── */
  function renderImage(wrapId, url, placeholderText) {
    var wrap = el(wrapId);
    if (!wrap) return;
    if (url && url.trim()) {
      wrap.innerHTML = '<img src="' + escapeHtml(url.trim()) + '" alt="OGプレビュー画像" onerror="this.parentNode.innerHTML=\'<span>画像の読み込みに失敗しました</span>\'">';
    } else {
      wrap.innerHTML = '<span>' + placeholderText + '</span>';
    }
  }

  /* ── プレビュー更新 ── */
  function updatePreviews() {
    var title    = el('og-title').value.trim()       || 'ページタイトルがここに表示されます';
    var desc     = el('og-description').value.trim() || 'ページの説明文がここに表示されます。';
    var url      = el('og-url').value.trim();
    var image    = el('og-image').value.trim();
    var twCard   = el('tw-card').value;
    var twTitle  = el('tw-title').value.trim()       || title;
    var twDesc   = el('tw-description').value.trim() || desc;
    var twImage  = el('tw-image').value.trim()       || image;
    var siteName = el('og-site-name').value.trim();
    var domain   = getDomain(url) || 'example.com';

    /* Facebook */
    el('prev-fb-title').textContent  = title;
    el('prev-fb-desc').textContent   = desc;
    el('prev-fb-domain').textContent = domain.toUpperCase();
    renderImage('prev-fb-img-wrap', image, '画像URLを入力してください');

    /* Twitter */
    var twCardEl = el('prev-tw');
    var imgWrap  = el('prev-tw-img-wrap');
    if (twCard === 'summary') {
      twCardEl.className = 'og-card-tw summary';
      if (imgWrap) { imgWrap.style.aspectRatio = '1/1'; imgWrap.style.width = '120px'; }
    } else {
      twCardEl.className = 'og-card-tw summary-large';
      if (imgWrap) { imgWrap.style.aspectRatio = '2/1'; imgWrap.style.width = '100%'; }
    }
    el('prev-tw-title').textContent  = twTitle;
    el('prev-tw-desc').textContent   = twDesc;
    el('prev-tw-domain').textContent = domain;
    renderImage('prev-tw-img-wrap', twImage, '画像URLを入力してください');

    /* LinkedIn */
    el('prev-li-title').textContent  = title;
    el('prev-li-domain').textContent = domain;
    renderImage('prev-li-img-wrap', image, '画像URLを入力してください');

    /* Google */
    el('prev-g-title').textContent      = title;
    el('prev-g-desc').textContent       = desc;
    el('prev-g-breadcrumb').textContent = domain;
    el('prev-g-sitename').textContent   = siteName || 'あなたのサイト';
  }

  /* ── デバウンス ── */
  var debounceTimer;
  function debounce(fn, delay) {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(fn, delay);
  }

  var liveInputs = ['og-title','og-description','og-url','og-image','og-site-name','tw-title','tw-description','tw-image','tw-card','og-type'];
  liveInputs.forEach(function(id) {
    var elem = el(id);
    if (elem) {
      elem.addEventListener('input',  function() { debounce(updatePreviews, 120); });
      elem.addEventListener('change', function() { debounce(updatePreviews, 120); });
    }
  });

  /* ── メタタグ生成 ── */
  el('og-generate-btn').addEventListener('click', function() {
    var title    = el('og-title').value.trim();
    var desc     = el('og-description').value.trim();
    var url      = el('og-url').value.trim();
    var image    = el('og-image').value.trim();
    var type     = el('og-type').value;
    var siteName = el('og-site-name').value.trim();
    var twCard   = el('tw-card').value;
    var twTitle  = el('tw-title').value.trim();
    var twDesc   = el('tw-description').value.trim();
    var twImage  = el('tw-image').value.trim();

    var lines = [];
    lines.push('<!-- Open Graph / Facebook -->');
    if (type)     lines.push('<meta property="og:type"        content="' + escapeHtml(type)     + '" />');
    if (url)      lines.push('<meta property="og:url"         content="' + escapeHtml(url)      + '" />');
    if (title)    lines.push('<meta property="og:title"       content="' + escapeHtml(title)    + '" />');
    if (desc)     lines.push('<meta property="og:description" content="' + escapeHtml(desc)     + '" />');
    if (image)    lines.push('<meta property="og:image"       content="' + escapeHtml(image)    + '" />');
    if (siteName) lines.push('<meta property="og:site_name"   content="' + escapeHtml(siteName) + '" />');
    lines.push('');
    lines.push('<!-- Twitter Card -->');
    lines.push('<meta name="twitter:card"        content="' + escapeHtml(twCard) + '" />');
    if (twTitle || title) lines.push('<meta name="twitter:title"       content="' + escapeHtml(twTitle || title)  + '" />');
    if (twDesc  || desc)  lines.push('<meta name="twitter:description" content="' + escapeHtml(twDesc  || desc)   + '" />');
    if (twImage || image) lines.push('<meta name="twitter:image"       content="' + escapeHtml(twImage || image)  + '" />');

    var code = lines.join('\n');
    var codeSection = el('og-code-section');
    el('og-code-output').textContent = code;
    codeSection.style.display = 'block';
    codeSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
  });

  /* ── コピー ── */
  el('og-copy-btn').addEventListener('click', function() {
    var text = el('og-code-output').textContent;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(showToast);
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showToast();
    }
  });

  function showToast() {
    var t = el('og-toast');
    t.style.display = 'block';
    setTimeout(function() { t.style.display = 'none'; }, 2200);
  }

  /* ── クリア ── */
  el('og-clear-btn').addEventListener('click', function() {
    ['og-title','og-description','og-url','og-image','og-site-name','tw-title','tw-description','tw-image'].forEach(function(id) {
      var elem = el(id);
      if (elem) elem.value = '';
    });
    el('og-type').value = 'website';
    el('tw-card').value = 'summary_large_image';
    ['og-title-count','og-desc-count','tw-title-count','tw-desc-count'].forEach(function(id) {
      var elem = el(id);
      if (elem) { elem.textContent = '0 / ' + elem.textContent.split('/')[1].trim(); elem.className = 'og-char-info'; }
    });
    el('og-code-section').style.display = 'none';
    updatePreviews();
  });

  /* ── 初期レンダリング ── */
  updatePreviews();
})();
</script>

</div>

---

### 関連ツール

> メタタグを生成する → [メタタグジェネレーター](/ja/tools/meta-tag-generator/)

> ファビコンを作成する → [ファビコンジェネレーター](/ja/tools/favicon-generator/)

> プレースホルダー画像を生成する → [プレースホルダー画像ジェネレーター](/ja/tools/placeholder-image/)
