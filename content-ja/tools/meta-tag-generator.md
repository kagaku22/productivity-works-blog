---
title: "メタタグジェネレーター — SEO・OGタグ自動生成"
description: "タイトル・ディスクリプション・OGPタグなどSEO最適化されたメタタグを生成。無料メタタグ作成ツール。"
date: 2025-05-16
slug: "meta-tag-generator"
categories: ["無料ツール"]
ShowToc: false
aliases:
  - "/ja/tools/seo-meta-tags/"
  - "/ja/tools/og-tag-generator/"
cover:
  image: "/images/covers/meta-tag-generator-ja.png"
  alt: "メタタグジェネレーター"
---

<style>
#meta-app *,
#meta-app *::before,
#meta-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#meta-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", "Yu Gothic", sans-serif;
  color: #1e293b;
  max-width: 860px;
  margin: 0 auto;
  padding: 0 0 2rem;
}
#meta-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  color: #0f172a;
  margin: 1.75rem 0 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid #e2e8f0;
}
#meta-app .field {
  margin-bottom: 1.1rem;
}
#meta-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.3rem;
}
#meta-app input[type="text"],
#meta-app input[type="url"],
#meta-app select,
#meta-app textarea {
  width: 100%;
  padding: 0.55rem 0.75rem;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.93rem;
  background: #fff;
  color: #1e293b;
  transition: border-color 0.18s;
  outline: none;
}
#meta-app input[type="text"]:focus,
#meta-app input[type="url"]:focus,
#meta-app select:focus,
#meta-app textarea:focus {
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37,99,235,0.12);
}
#meta-app textarea {
  resize: vertical;
  min-height: 72px;
}
#meta-app .counter {
  font-size: 0.78rem;
  margin-top: 0.25rem;
  font-weight: 500;
  transition: color 0.18s;
}
#meta-app .counter.ok   { color: #16a34a; }
#meta-app .counter.warn { color: #d97706; }
#meta-app .counter.over { color: #dc2626; }
#meta-app .row2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
#meta-app .row3 {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 580px) {
  #meta-app .row2,
  #meta-app .row3 { grid-template-columns: 1fr; }
}

/* SERP Preview */
#meta-app .serp-box {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 1.1rem 1.3rem;
  margin-top: 0.5rem;
}
#meta-app .serp-url {
  font-size: 0.82rem;
  color: #16a34a;
  margin-bottom: 0.18rem;
  word-break: break-all;
}
#meta-app .serp-title {
  font-size: 1.1rem;
  color: #2563eb;
  font-weight: 600;
  cursor: pointer;
  line-height: 1.35;
  margin-bottom: 0.22rem;
  word-break: break-word;
}
#meta-app .serp-desc {
  font-size: 0.88rem;
  color: #4b5563;
  line-height: 1.55;
  word-break: break-word;
}

/* Social Previews */
#meta-app .social-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-top: 0.5rem;
}
@media (max-width: 580px) {
  #meta-app .social-row { grid-template-columns: 1fr; }
}
#meta-app .social-card {
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  overflow: hidden;
  background: #f8fafc;
}
#meta-app .social-card-header {
  background: #e2e8f0;
  padding: 0.45rem 0.8rem;
  font-size: 0.75rem;
  font-weight: 700;
  color: #475569;
  letter-spacing: 0.03em;
  text-transform: uppercase;
}
#meta-app .social-img-placeholder {
  background: #cbd5e1;
  height: 130px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #94a3b8;
  font-size: 0.82rem;
  position: relative;
  overflow: hidden;
}
#meta-app .social-img-placeholder img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: none;
}
#meta-app .social-img-placeholder .placeholder-text { position: absolute; }
#meta-app .social-body {
  padding: 0.6rem 0.8rem 0.7rem;
}
#meta-app .fb-card .social-domain {
  font-size: 0.72rem;
  color: #6b7280;
  text-transform: uppercase;
  margin-bottom: 0.2rem;
}
#meta-app .fb-card .social-title {
  font-size: 0.9rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 0.15rem;
  line-height: 1.3;
}
#meta-app .fb-card .social-desc {
  font-size: 0.78rem;
  color: #6b7280;
  line-height: 1.4;
}
#meta-app .tw-card-inner {
  border-radius: 0 0 10px 10px;
  overflow: hidden;
}
#meta-app .tw-card .social-body {
  background: #fff;
  border-top: 1px solid #e2e8f0;
}
#meta-app .tw-card .social-title {
  font-size: 0.88rem;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 0.15rem;
}
#meta-app .tw-card .social-desc {
  font-size: 0.78rem;
  color: #6b7280;
  line-height: 1.4;
}
#meta-app .tw-card .social-domain {
  font-size: 0.72rem;
  color: #6b7280;
  margin-top: 0.2rem;
}

/* Output */
#meta-app .output-box {
  position: relative;
  margin-top: 0.5rem;
}
#meta-app pre {
  background: #0f172a;
  color: #e2e8f0;
  padding: 1.1rem 1.2rem;
  border-radius: 8px;
  font-size: 0.82rem;
  line-height: 1.65;
  overflow-x: auto;
  white-space: pre-wrap;
  word-break: break-word;
  font-family: "Fira Code", "Cascadia Code", "Consolas", monospace;
}
#meta-app .copy-btn {
  position: absolute;
  top: 0.6rem;
  right: 0.6rem;
  background: #2563eb;
  color: #fff;
  border: none;
  padding: 0.35rem 0.85rem;
  border-radius: 5px;
  font-size: 0.8rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.16s;
}
#meta-app .copy-btn:hover { background: #1d4ed8; }
#meta-app .copy-btn.copied { background: #16a34a; }

/* freee CTA */
#meta-app .freee-cta {
  margin-top: 2.2rem;
  background: linear-gradient(135deg, #eff6ff 0%, #f0fdf4 100%);
  border: 1.5px solid #bfdbfe;
  border-radius: 12px;
  padding: 1.3rem 1.5rem;
}
#meta-app .freee-cta h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #1e293b;
  margin-bottom: 0.5rem;
}
#meta-app .freee-cta p {
  font-size: 0.88rem;
  color: #374151;
  line-height: 1.65;
  margin-bottom: 0.9rem;
}
#meta-app .freee-cta a.cta-btn {
  display: inline-block;
  background: #2563eb;
  color: #fff;
  padding: 0.55rem 1.3rem;
  border-radius: 6px;
  font-size: 0.88rem;
  font-weight: 700;
  text-decoration: none;
  transition: background 0.16s;
}
#meta-app .freee-cta a.cta-btn:hover { background: #1d4ed8; }
</style>

<div id="meta-app">

<h2>基本 SEO タグ</h2>

<div class="field">
  <label for="mg-title">ページタイトル <span style="font-weight:400;color:#6b7280;">（推奨: 30〜60文字）</span></label>
  <input type="text" id="mg-title" placeholder="魅力的なページタイトルを入力" maxlength="100" oninput="mgUpdate()">
  <div class="counter ok" id="cnt-title">0 / 60</div>
</div>

<div class="field">
  <label for="mg-desc">メタディスクリプション <span style="font-weight:400;color:#6b7280;">（推奨: 70〜160文字）</span></label>
  <textarea id="mg-desc" placeholder="検索結果に表示される、ページの簡潔な説明文を入力してください。" maxlength="300" oninput="mgUpdate()"></textarea>
  <div class="counter ok" id="cnt-desc">0 / 160</div>
</div>

<div class="row2">
  <div class="field">
    <label for="mg-keywords">キーワード <span style="font-weight:400;color:#6b7280;">（カンマ区切り）</span></label>
    <input type="text" id="mg-keywords" placeholder="SEO, メタタグ, ジェネレーター" oninput="mgUpdate()">
  </div>
  <div class="field">
    <label for="mg-author">著者名</label>
    <input type="text" id="mg-author" placeholder="山田 太郎" oninput="mgUpdate()">
  </div>
</div>

<div class="row2">
  <div class="field">
    <label for="mg-robots-index">インデックス設定</label>
    <select id="mg-robots-index" onchange="mgUpdate()">
      <option value="index">index（クロール許可）</option>
      <option value="noindex">noindex（クロール拒否）</option>
    </select>
  </div>
  <div class="field">
    <label for="mg-robots-follow">リンク追跡設定</label>
    <select id="mg-robots-follow" onchange="mgUpdate()">
      <option value="follow">follow（リンク追跡許可）</option>
      <option value="nofollow">nofollow（リンク追跡拒否）</option>
    </select>
  </div>
</div>

<h2>Open Graph タグ（SNS・Facebook）</h2>

<div class="row2">
  <div class="field">
    <label for="mg-og-title">og:title</label>
    <input type="text" id="mg-og-title" placeholder="SNSシェア時のタイトル" oninput="mgUpdate()">
  </div>
  <div class="field">
    <label for="mg-og-type">og:type（コンテンツ種別）</label>
    <select id="mg-og-type" onchange="mgUpdate()">
      <option value="website">website（ウェブサイト）</option>
      <option value="article">article（記事）</option>
      <option value="product">product（商品）</option>
      <option value="video.movie">video.movie（動画）</option>
      <option value="music.song">music.song（音楽）</option>
      <option value="book">book（書籍）</option>
    </select>
  </div>
</div>

<div class="field">
  <label for="mg-og-desc">og:description</label>
  <textarea id="mg-og-desc" placeholder="SNSシェア時に表示される説明文。" oninput="mgUpdate()"></textarea>
</div>

<div class="row2">
  <div class="field">
    <label for="mg-og-url">og:url（正規URL）</label>
    <input type="url" id="mg-og-url" placeholder="https://example.com/page" oninput="mgUpdate()">
  </div>
  <div class="field">
    <label for="mg-og-image">og:image URL（シェア画像）</label>
    <input type="url" id="mg-og-image" placeholder="https://example.com/image.jpg" oninput="mgUpdate()">
  </div>
</div>

<h2>Twitter Card タグ</h2>

<div class="row3">
  <div class="field">
    <label for="mg-tw-card">twitter:card（カード形式）</label>
    <select id="mg-tw-card" onchange="mgUpdate()">
      <option value="summary_large_image">summary_large_image（大画像）</option>
      <option value="summary">summary（サマリー）</option>
      <option value="app">app（アプリ）</option>
      <option value="player">player（動画）</option>
    </select>
  </div>
  <div class="field">
    <label for="mg-tw-title">twitter:title</label>
    <input type="text" id="mg-tw-title" placeholder="Twitterシェア時のタイトル" oninput="mgUpdate()">
  </div>
  <div class="field">
    <label for="mg-tw-image">twitter:image URL</label>
    <input type="url" id="mg-tw-image" placeholder="https://example.com/image.jpg" oninput="mgUpdate()">
  </div>
</div>

<div class="field">
  <label for="mg-tw-desc">twitter:description</label>
  <textarea id="mg-tw-desc" placeholder="Twitterシェア時の説明文。" oninput="mgUpdate()" style="min-height:56px;"></textarea>
</div>

<h2>Google 検索結果プレビュー</h2>
<div class="serp-box">
  <div class="serp-url" id="prev-url">https://example.com/page</div>
  <div class="serp-title" id="prev-title">ページタイトルがここに表示されます</div>
  <div class="serp-desc" id="prev-desc">メタディスクリプションがここに表示されます。160文字以内で魅力的な説明文を入力してください。</div>
</div>

<h2>SNS シェアプレビュー</h2>
<div class="social-row">
  <div class="social-card fb-card">
    <div class="social-card-header">Facebook / Open Graph</div>
    <div class="social-img-placeholder" id="fb-img-wrap">
      <img id="fb-img" src="" alt="OG画像">
      <span class="placeholder-text" id="fb-img-placeholder">og:image プレビュー</span>
    </div>
    <div class="social-body">
      <div class="social-domain" id="fb-domain">example.com</div>
      <div class="social-title" id="fb-title">OGタイトルがここに表示されます</div>
      <div class="social-desc" id="fb-desc">og:descriptionがここに表示されます。</div>
    </div>
  </div>
  <div class="social-card tw-card">
    <div class="social-card-header">Twitter / X カード</div>
    <div class="tw-card-inner">
      <div class="social-img-placeholder" id="tw-img-wrap">
        <img id="tw-img" src="" alt="Twitter画像">
        <span class="placeholder-text" id="tw-img-placeholder">twitter:image プレビュー</span>
      </div>
      <div class="social-body">
        <div class="social-title" id="tw-title">Twitterタイトルがここに表示されます</div>
        <div class="social-desc" id="tw-desc">twitter:descriptionがここに表示されます。</div>
        <div class="social-domain" id="tw-domain">example.com</div>
      </div>
    </div>
  </div>
</div>

<h2>生成されたHTMLコード</h2>
<div class="output-box">
  <pre id="mg-output"><!-- 上のフォームを入力してタグを生成 --></pre>
  <button class="copy-btn" id="copy-btn" onclick="mgCopy()">コピー</button>
</div>

<div class="freee-cta">
  <h3>事業のSEO対策と経費管理を同時に効率化しませんか？</h3>
  <p>
    ウェブサイトのSEO改善と並行して、事業の財務管理も重要です。
    <strong>freee会計</strong>なら、売上・経費の自動仕訳、確定申告書類の自動作成、
    インボイス対応まで一括管理。Webマーケティング費用の経費処理も簡単です。
    中小企業・個人事業主の方に選ばれています。
  </p>
  <a class="cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計を無料で試す</a>
</div>

</div>

<script>
(function () {
  function v(id) { return document.getElementById(id); }

  function setCounter(elId, current, max) {
    var el = v(elId);
    el.textContent = current + " / " + max + " 文字";
    el.className = "counter";
    if (current <= max * 0.8) el.classList.add("ok");
    else if (current <= max) el.classList.add("warn");
    else el.classList.add("over");
  }

  function esc(s) {
    return s.replace(/&/g,"&amp;").replace(/"/g,"&quot;").replace(/</g,"&lt;").replace(/>/g,"&gt;");
  }

  function getDomain(url) {
    try { return new URL(url).hostname || "example.com"; }
    catch(e) { return url.replace(/^https?:\/\//,"").split("/")[0] || "example.com"; }
  }

  function updateImg(imgId, wrapId, phId, url) {
    var img = v(imgId), wrap = v(wrapId), ph = v(phId);
    if (url && url.trim()) {
      img.src = url.trim();
      img.style.display = "block";
      ph.style.display = "none";
    } else {
      img.style.display = "none";
      ph.style.display = "block";
    }
  }

  window.mgUpdate = function () {
    var title   = v("mg-title").value;
    var desc    = v("mg-desc").value;
    var kw      = v("mg-keywords").value;
    var author  = v("mg-author").value;
    var rIdx    = v("mg-robots-index").value;
    var rFol    = v("mg-robots-follow").value;

    var ogTitle = v("mg-og-title").value || title;
    var ogDesc  = v("mg-og-desc").value || desc;
    var ogType  = v("mg-og-type").value;
    var ogUrl   = v("mg-og-url").value;
    var ogImg   = v("mg-og-image").value;

    var twCard  = v("mg-tw-card").value;
    var twTitle = v("mg-tw-title").value || ogTitle;
    var twDesc  = v("mg-tw-desc").value || ogDesc;
    var twImg   = v("mg-tw-image").value || ogImg;

    // Counters
    setCounter("cnt-title", title.length, 60);
    setCounter("cnt-desc", desc.length, 160);

    // SERP Preview
    v("prev-title").textContent = title || "ページタイトルがここに表示されます";
    v("prev-url").textContent   = ogUrl || "https://example.com/page";
    v("prev-desc").textContent  = desc  || "メタディスクリプションがここに表示されます。";

    // FB Preview
    var domain = getDomain(ogUrl);
    v("fb-domain").textContent = domain;
    v("fb-title").textContent  = ogTitle || "OGタイトルがここに表示されます";
    v("fb-desc").textContent   = ogDesc  || "og:descriptionがここに表示されます。";
    updateImg("fb-img","fb-img-wrap","fb-img-placeholder", ogImg);

    // Twitter Preview
    v("tw-domain").textContent = domain;
    v("tw-title").textContent  = twTitle || "Twitterタイトルがここに表示されます";
    v("tw-desc").textContent   = twDesc  || "twitter:descriptionがここに表示されます。";
    updateImg("tw-img","tw-img-wrap","tw-img-placeholder", twImg);

    // Build output
    var lines = [];
    lines.push("<!-- プライマリ メタタグ -->");
    if (title)  lines.push('<meta name="title" content="' + esc(title) + '">');
    if (desc)   lines.push('<meta name="description" content="' + esc(desc) + '">');
    if (kw)     lines.push('<meta name="keywords" content="' + esc(kw) + '">');
    if (author) lines.push('<meta name="author" content="' + esc(author) + '">');
    lines.push('<meta name="robots" content="' + rIdx + ", " + rFol + '">');

    lines.push("");
    lines.push("<!-- Open Graph / Facebook -->");
    lines.push('<meta property="og:type" content="' + esc(ogType) + '">');
    if (ogUrl)   lines.push('<meta property="og:url" content="' + esc(ogUrl) + '">');
    if (ogTitle) lines.push('<meta property="og:title" content="' + esc(ogTitle) + '">');
    if (ogDesc)  lines.push('<meta property="og:description" content="' + esc(ogDesc) + '">');
    if (ogImg)   lines.push('<meta property="og:image" content="' + esc(ogImg) + '">');

    lines.push("");
    lines.push("<!-- Twitter Card -->");
    lines.push('<meta property="twitter:card" content="' + esc(twCard) + '">');
    if (ogUrl)   lines.push('<meta property="twitter:url" content="' + esc(ogUrl) + '">');
    if (twTitle) lines.push('<meta property="twitter:title" content="' + esc(twTitle) + '">');
    if (twDesc)  lines.push('<meta property="twitter:description" content="' + esc(twDesc) + '">');
    if (twImg)   lines.push('<meta property="twitter:image" content="' + esc(twImg) + '">');

    v("mg-output").textContent = lines.join("\n");
  };

  window.mgCopy = function () {
    var text = v("mg-output").textContent;
    if (!text || text.trim() === "<!-- 上のフォームを入力してタグを生成 -->") return;
    navigator.clipboard.writeText(text).then(function () {
      var btn = v("copy-btn");
      btn.textContent = "コピーしました!";
      btn.classList.add("copied");
      setTimeout(function () {
        btn.textContent = "コピー";
        btn.classList.remove("copied");
      }, 2000);
    });
  };

  // Init
  mgUpdate();
})();
</script>

---

## 関連ツール

> Html Beautifier → [Html Beautifierツール](/ja/tools/html-beautifier/)
> Html Entity Converter → [Html Entity Converterツール](/ja/tools/html-entity-converter/)
> Html Entity Encoder → [Html Entity Encoderツール](/ja/tools/html-entity-encoder/)

## 関連記事

- [副業ブログの始め方｜お名前.comでドメイン取得→freeeで経費管理まで](/ja/posts/fukugyo-blog-hajimekata-domain-freee/)
- [AIを使ったブログ記事の書き方入門【2026年版・SEOで上位表示を狙う方法】](/ja/posts/ai-ブログ-書き方/)
- [レンタルサーバー おすすめ2026年版！ブログ・サイト制作向け比較](/ja/posts/rental-server-osusume-2026/)
