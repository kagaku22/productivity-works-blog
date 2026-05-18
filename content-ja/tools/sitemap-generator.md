---
title: "サイトマップXMLジェネレーター — 無料オンラインツール"
date: 2025-04-24
description: "XMLサイトマップを即座に生成。URL・優先度・更新頻度・最終更新日を設定。SEO改善のためsitemap.xmlをダウンロード・コピー。"
categories: ["無料ツール"]
slug: "sitemap-generator"
ShowToc: false
aliases:
  - "/ja/tools/sitemap-generator/"
  - "/ja/tools/sitemap-generator/"
cover:
  image: "/images/covers/sitemap-generator-ja.png"
  alt: "サイトマップXMLジェネレーター"
---

XMLサイトマップをブラウザ上で即座に作成。URLを1件ずつ追加するか、まとめて貼り付けて、優先度・更新頻度・最終更新日を設定したら `sitemap.xml` をダウンロード・コピーできます。

<div id="sitemap-app">
<style>
  #sitemap-app *,
  #sitemap-app *::before,
  #sitemap-app *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  #sitemap-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
    font-size: 15px;
    color: #1a1a1a;
    line-height: 1.6;
    max-width: 860px;
    margin: 0 auto;
  }

  #sitemap-app .sa-section {
    background: #fff;
    border: 1px solid #e0e0e0;
    border-radius: 10px;
    padding: 20px;
    margin-bottom: 16px;
  }

  #sitemap-app .sa-section-title {
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 0.04em;
    color: #555;
    margin-bottom: 14px;
  }

  #sitemap-app .sa-row {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    align-items: flex-end;
    margin-bottom: 10px;
  }

  #sitemap-app .sa-field {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  #sitemap-app .sa-field label {
    font-size: 12px;
    font-weight: 600;
    color: #444;
  }

  #sitemap-app .sa-field.sa-url {
    flex: 1 1 260px;
  }

  #sitemap-app .sa-field.sa-lastmod {
    flex: 0 0 155px;
  }

  #sitemap-app .sa-field.sa-changefreq {
    flex: 0 0 140px;
  }

  #sitemap-app .sa-field.sa-priority {
    flex: 0 0 90px;
  }

  #sitemap-app input[type="text"],
  #sitemap-app input[type="date"],
  #sitemap-app input[type="number"],
  #sitemap-app select,
  #sitemap-app textarea {
    font-size: 14px;
    padding: 7px 10px;
    border: 1px solid #ccc;
    border-radius: 6px;
    background: #fafafa;
    color: #1a1a1a;
    width: 100%;
    transition: border-color 0.15s;
    font-family: inherit;
  }

  #sitemap-app input:focus,
  #sitemap-app select:focus,
  #sitemap-app textarea:focus {
    outline: none;
    border-color: #4a7cf0;
    background: #fff;
  }

  #sitemap-app textarea {
    resize: vertical;
    min-height: 100px;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
    font-size: 13px;
  }

  #sitemap-app .sa-btn {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 8px 16px;
    border: none;
    border-radius: 6px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s, transform 0.1s;
    font-family: inherit;
    white-space: nowrap;
  }

  #sitemap-app .sa-btn:active { transform: scale(0.97); }

  #sitemap-app .sa-btn-primary {
    background: #4a7cf0;
    color: #fff;
  }
  #sitemap-app .sa-btn-primary:hover { background: #3a6ce0; }

  #sitemap-app .sa-btn-success {
    background: #22a06b;
    color: #fff;
  }
  #sitemap-app .sa-btn-success:hover { background: #1a8a5a; }

  #sitemap-app .sa-btn-outline {
    background: #fff;
    color: #333;
    border: 1px solid #ccc;
  }
  #sitemap-app .sa-btn-outline:hover { background: #f5f5f5; }

  #sitemap-app .sa-btn-danger {
    background: #fff;
    color: #d93025;
    border: 1px solid #f5c6c4;
    padding: 6px 10px;
    font-size: 13px;
  }
  #sitemap-app .sa-btn-danger:hover { background: #fff5f5; }

  #sitemap-app .sa-btn-preset {
    background: #f0f4ff;
    color: #4a7cf0;
    border: 1px solid #c8d8ff;
    font-size: 13px;
    padding: 6px 12px;
  }
  #sitemap-app .sa-btn-preset:hover { background: #e0eaff; }

  #sitemap-app .sa-url-list {
    display: flex;
    flex-direction: column;
    gap: 8px;
    margin-bottom: 14px;
  }

  #sitemap-app .sa-url-entry {
    display: flex;
    gap: 8px;
    align-items: flex-end;
    padding: 12px;
    background: #f9f9f9;
    border: 1px solid #eee;
    border-radius: 8px;
    flex-wrap: wrap;
  }

  #sitemap-app .sa-url-entry .sa-field.sa-url {
    flex: 1 1 220px;
  }

  #sitemap-app .sa-url-entry .sa-remove-btn {
    flex: 0 0 auto;
    align-self: flex-end;
  }

  #sitemap-app .sa-tabs {
    display: flex;
    gap: 0;
    border-bottom: 2px solid #e0e0e0;
    margin-bottom: 16px;
  }

  #sitemap-app .sa-tab {
    padding: 8px 18px;
    font-size: 14px;
    font-weight: 600;
    color: #777;
    cursor: pointer;
    border-bottom: 2px solid transparent;
    margin-bottom: -2px;
    transition: color 0.15s, border-color 0.15s;
    user-select: none;
  }

  #sitemap-app .sa-tab.active {
    color: #4a7cf0;
    border-bottom-color: #4a7cf0;
  }

  #sitemap-app .sa-tab-content {
    display: none;
  }
  #sitemap-app .sa-tab-content.active {
    display: block;
  }

  #sitemap-app .sa-defaults-row {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    align-items: flex-end;
    margin-bottom: 10px;
  }

  #sitemap-app .sa-presets-row {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 10px;
  }

  #sitemap-app .sa-stats-bar {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 10px 14px;
    background: #f0f4ff;
    border-radius: 8px;
    margin-bottom: 14px;
    font-size: 14px;
  }

  #sitemap-app .sa-stats-bar .sa-count {
    font-weight: 700;
    color: #4a7cf0;
  }

  #sitemap-app .sa-valid-badge {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-size: 13px;
    font-weight: 600;
    padding: 3px 10px;
    border-radius: 20px;
  }
  #sitemap-app .sa-valid-badge.valid {
    background: #e6f9f1;
    color: #22a06b;
  }
  #sitemap-app .sa-valid-badge.invalid {
    background: #fff0f0;
    color: #d93025;
  }

  #sitemap-app .sa-output-box {
    background: #1e1e2e;
    color: #cdd6f4;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
    font-size: 13px;
    border-radius: 8px;
    padding: 16px;
    overflow-x: auto;
    white-space: pre;
    min-height: 120px;
    max-height: 420px;
    overflow-y: auto;
    line-height: 1.6;
    margin-bottom: 12px;
  }

  #sitemap-app .sa-output-actions {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }

  #sitemap-app .sa-copy-feedback {
    font-size: 13px;
    color: #22a06b;
    font-weight: 600;
    align-self: center;
    opacity: 0;
    transition: opacity 0.3s;
  }
  #sitemap-app .sa-copy-feedback.show { opacity: 1; }

  #sitemap-app .sa-notice {
    font-size: 13px;
    color: #888;
    margin-top: 8px;
  }

  @media (max-width: 600px) {
    #sitemap-app .sa-field.sa-lastmod,
    #sitemap-app .sa-field.sa-changefreq,
    #sitemap-app .sa-field.sa-priority {
      flex: 1 1 120px;
    }
    #sitemap-app .sa-url-entry {
      padding: 10px 8px;
    }
    #sitemap-app .sa-output-box {
      font-size: 11.5px;
    }
  }
</style>

<!-- プリセット & デフォルト -->
<div class="sa-section">
  <div class="sa-section-title">プリセット</div>
  <div class="sa-presets-row">
    <button class="sa-btn sa-btn-preset" onclick="sitemapApp.applyPreset('blog')">ブログ</button>
    <button class="sa-btn sa-btn-preset" onclick="sitemapApp.applyPreset('ecommerce')">ECサイト</button>
    <button class="sa-btn sa-btn-preset" onclick="sitemapApp.applyPreset('portfolio')">ポートフォリオ</button>
    <button class="sa-btn sa-btn-outline" onclick="sitemapApp.clearAll()">すべてクリア</button>
  </div>
  <div class="sa-section-title" style="margin-top:14px;">デフォルト値（新規追加時に適用）</div>
  <div class="sa-defaults-row">
    <div class="sa-field">
      <label>デフォルト更新頻度</label>
      <select id="sa-default-freq">
        <option value="always">always（常時）</option>
        <option value="hourly">hourly（毎時）</option>
        <option value="daily">daily（毎日）</option>
        <option value="weekly" selected>weekly（毎週）</option>
        <option value="monthly">monthly（毎月）</option>
        <option value="yearly">yearly（毎年）</option>
        <option value="never">never（変更なし）</option>
      </select>
    </div>
    <div class="sa-field">
      <label>デフォルト優先度</label>
      <input type="number" id="sa-default-priority" value="0.5" min="0.0" max="1.0" step="0.1" style="width:90px;">
    </div>
  </div>
</div>

<!-- 入力タブ -->
<div class="sa-section">
  <div class="sa-tabs">
    <div class="sa-tab active" onclick="sitemapApp.switchTab('individual', this)">URLを1件ずつ追加</div>
    <div class="sa-tab" onclick="sitemapApp.switchTab('bulk', this)">まとめて貼り付け</div>
  </div>

  <!-- 個別追加タブ -->
  <div class="sa-tab-content active" id="sa-tab-individual">
    <div class="sa-url-list" id="sa-url-list"></div>
    <button class="sa-btn sa-btn-primary" onclick="sitemapApp.addEntry()">+ URLを追加</button>
    <p class="sa-notice">各URLに最終更新日・更新頻度・優先度（0.0〜1.0）を個別設定できます。</p>
  </div>

  <!-- まとめて貼り付けタブ -->
  <div class="sa-tab-content" id="sa-tab-bulk">
    <div class="sa-field" style="margin-bottom:10px;">
      <label>URLを貼り付け（1行に1URL）</label>
      <textarea id="sa-bulk-input" placeholder="https://example.com/&#10;https://example.com/about/&#10;https://example.com/blog/"></textarea>
    </div>
    <button class="sa-btn sa-btn-primary" onclick="sitemapApp.importBulk()">URLをインポート</button>
    <p class="sa-notice">デフォルト設定の更新頻度と優先度が適用されます。インポート後は「URLを1件ずつ追加」タブで個別に編集できます。</p>
  </div>
</div>

<!-- 出力 -->
<div class="sa-section">
  <div class="sa-section-title">生成されたサイトマップXML</div>
  <div class="sa-stats-bar">
    <span>URL数: <span class="sa-count" id="sa-url-count">0</span></span>
    <span id="sa-valid-badge" class="sa-valid-badge valid">&#10003; 有効なXML</span>
  </div>
  <div class="sa-output-box" id="sa-output"></div>
  <div class="sa-output-actions">
    <button class="sa-btn sa-btn-success" onclick="sitemapApp.copyXml()">XMLをコピー</button>
    <button class="sa-btn sa-btn-outline" onclick="sitemapApp.downloadXml()">sitemap.xmlをダウンロード</button>
    <span class="sa-copy-feedback" id="sa-copy-feedback">コピーしました！</span>
  </div>
</div>

<script>
(function() {
  var app = {
    entries: [],
    nextId: 1,

    getDefaultFreq: function() {
      var el = document.getElementById('sa-default-freq');
      return el ? el.value : 'weekly';
    },
    getDefaultPriority: function() {
      var el = document.getElementById('sa-default-priority');
      var v = el ? parseFloat(el.value) : 0.5;
      if (isNaN(v)) return 0.5;
      return Math.min(1.0, Math.max(0.0, v));
    },

    addEntry: function(url, lastmod, freq, priority) {
      var id = this.nextId++;
      var entry = {
        id: id,
        url: url || '',
        lastmod: lastmod || '',
        freq: freq || this.getDefaultFreq(),
        priority: (priority !== undefined) ? priority : this.getDefaultPriority()
      };
      this.entries.push(entry);
      this.renderList();
      this.generate();
    },

    removeEntry: function(id) {
      this.entries = this.entries.filter(function(e) { return e.id !== id; });
      this.renderList();
      this.generate();
    },

    renderList: function() {
      var list = document.getElementById('sa-url-list');
      var self = this;
      list.innerHTML = '';
      this.entries.forEach(function(entry) {
        var div = document.createElement('div');
        div.className = 'sa-url-entry';
        div.id = 'sa-entry-' + entry.id;
        div.innerHTML =
          '<div class="sa-field sa-url">' +
            '<label>URL</label>' +
            '<input type="text" placeholder="https://example.com/page/" value="' + self.escAttr(entry.url) + '" ' +
              'onchange="sitemapApp.updateField(' + entry.id + ', \'url\', this.value)">' +
          '</div>' +
          '<div class="sa-field sa-lastmod">' +
            '<label>最終更新日</label>' +
            '<input type="date" value="' + self.escAttr(entry.lastmod) + '" ' +
              'onchange="sitemapApp.updateField(' + entry.id + ', \'lastmod\', this.value)">' +
          '</div>' +
          '<div class="sa-field sa-changefreq">' +
            '<label>更新頻度</label>' +
            '<select onchange="sitemapApp.updateField(' + entry.id + ', \'freq\', this.value)">' +
              self.freqOptions(entry.freq) +
            '</select>' +
          '</div>' +
          '<div class="sa-field sa-priority">' +
            '<label>優先度</label>' +
            '<input type="number" value="' + entry.priority + '" min="0.0" max="1.0" step="0.1" ' +
              'onchange="sitemapApp.updateField(' + entry.id + ', \'priority\', this.value)">' +
          '</div>' +
          '<div class="sa-remove-btn">' +
            '<button class="sa-btn sa-btn-danger" onclick="sitemapApp.removeEntry(' + entry.id + ')">削除</button>' +
          '</div>';
        list.appendChild(div);
      });
    },

    freqOptions: function(selected) {
      var opts = [
        { val: 'always',  label: 'always（常時）' },
        { val: 'hourly',  label: 'hourly（毎時）' },
        { val: 'daily',   label: 'daily（毎日）' },
        { val: 'weekly',  label: 'weekly（毎週）' },
        { val: 'monthly', label: 'monthly（毎月）' },
        { val: 'yearly',  label: 'yearly（毎年）' },
        { val: 'never',   label: 'never（変更なし）' }
      ];
      return opts.map(function(o) {
        return '<option value="' + o.val + '"' + (o.val === selected ? ' selected' : '') + '>' + o.label + '</option>';
      }).join('');
    },

    updateField: function(id, field, value) {
      var entry = this.entries.find(function(e) { return e.id === id; });
      if (!entry) return;
      if (field === 'priority') {
        var v = parseFloat(value);
        entry[field] = isNaN(v) ? 0.5 : Math.min(1.0, Math.max(0.0, v));
      } else {
        entry[field] = value;
      }
      this.generate();
    },

    switchTab: function(tab, el) {
      document.querySelectorAll('#sitemap-app .sa-tab').forEach(function(t) { t.classList.remove('active'); });
      document.querySelectorAll('#sitemap-app .sa-tab-content').forEach(function(c) { c.classList.remove('active'); });
      el.classList.add('active');
      document.getElementById('sa-tab-' + tab).classList.add('active');
    },

    importBulk: function() {
      var raw = document.getElementById('sa-bulk-input').value;
      var lines = raw.split('\n').map(function(l) { return l.trim(); }).filter(function(l) { return l.length > 0; });
      var self = this;
      lines.forEach(function(url) {
        self.entries.push({
          id: self.nextId++,
          url: url,
          lastmod: '',
          freq: self.getDefaultFreq(),
          priority: self.getDefaultPriority()
        });
      });
      document.getElementById('sa-bulk-input').value = '';
      this.renderList();
      this.generate();
      this.switchTab('individual', document.querySelectorAll('#sitemap-app .sa-tab')[0]);
    },

    generate: function() {
      var lines = [];
      lines.push('<?xml version="1.0" encoding="UTF-8"?>');
      lines.push('<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">');
      var valid = true;
      this.entries.forEach(function(entry) {
        if (!entry.url) { valid = false; return; }
        lines.push('  <url>');
        lines.push('    <loc>' + entry.url + '</loc>');
        if (entry.lastmod) {
          lines.push('    <lastmod>' + entry.lastmod + '</lastmod>');
        }
        // freq値にある日本語部分を除去してXMLに出力
        var freqVal = entry.freq.split('\uff08')[0].trim();
        lines.push('    <changefreq>' + freqVal + '</changefreq>');
        lines.push('    <priority>' + parseFloat(entry.priority).toFixed(1) + '</priority>');
        lines.push('  </url>');
      });
      lines.push('</urlset>');

      var xml = lines.join('\n');
      document.getElementById('sa-output').textContent = xml;
      document.getElementById('sa-url-count').textContent = this.entries.length;

      var badge = document.getElementById('sa-valid-badge');
      if (valid && this.entries.length > 0) {
        badge.textContent = '\u2713 有効なXML';
        badge.className = 'sa-valid-badge valid';
      } else if (this.entries.length === 0) {
        badge.textContent = '\u2014 URLなし';
        badge.className = 'sa-valid-badge invalid';
      } else {
        badge.textContent = '\u26A0 URLが空の項目あり';
        badge.className = 'sa-valid-badge invalid';
      }
    },

    getXml: function() {
      return document.getElementById('sa-output').textContent;
    },

    copyXml: function() {
      var xml = this.getXml();
      var self = this;
      var showFeedback = function() {
        var fb = document.getElementById('sa-copy-feedback');
        fb.classList.add('show');
        setTimeout(function() { fb.classList.remove('show'); }, 1800);
      };
      navigator.clipboard.writeText(xml).then(showFeedback).catch(function() {
        var ta = document.createElement('textarea');
        ta.value = xml;
        ta.style.position = 'fixed';
        ta.style.opacity = '0';
        document.body.appendChild(ta);
        ta.select();
        document.execCommand('copy');
        document.body.removeChild(ta);
        showFeedback();
      });
    },

    downloadXml: function() {
      var xml = this.getXml();
      var blob = new Blob([xml], { type: 'application/xml' });
      var url = URL.createObjectURL(blob);
      var a = document.createElement('a');
      a.href = url;
      a.download = 'sitemap.xml';
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
    },

    clearAll: function() {
      this.entries = [];
      this.renderList();
      this.generate();
    },

    applyPreset: function(name) {
      this.entries = [];
      this.nextId = 1;
      var today = new Date().toISOString().slice(0, 10);
      var presets = {
        blog: [
          { url: 'https://example.com/', lastmod: today, freq: 'daily', priority: 1.0 },
          { url: 'https://example.com/blog/', lastmod: today, freq: 'daily', priority: 0.9 },
          { url: 'https://example.com/about/', lastmod: today, freq: 'monthly', priority: 0.5 }
        ],
        ecommerce: [
          { url: 'https://example.com/', lastmod: today, freq: 'hourly', priority: 1.0 },
          { url: 'https://example.com/products/', lastmod: today, freq: 'hourly', priority: 0.9 },
          { url: 'https://example.com/categories/', lastmod: today, freq: 'daily', priority: 0.8 },
          { url: 'https://example.com/cart/', lastmod: today, freq: 'always', priority: 0.3 },
          { url: 'https://example.com/contact/', lastmod: today, freq: 'monthly', priority: 0.5 }
        ],
        portfolio: [
          { url: 'https://example.com/', lastmod: today, freq: 'monthly', priority: 1.0 },
          { url: 'https://example.com/work/', lastmod: today, freq: 'monthly', priority: 0.9 },
          { url: 'https://example.com/about/', lastmod: today, freq: 'yearly', priority: 0.6 },
          { url: 'https://example.com/contact/', lastmod: today, freq: 'yearly', priority: 0.5 }
        ]
      };
      var self = this;
      (presets[name] || []).forEach(function(p) {
        self.entries.push({
          id: self.nextId++,
          url: p.url,
          lastmod: p.lastmod,
          freq: p.freq,
          priority: p.priority
        });
      });
      this.renderList();
      this.generate();
    },

    escAttr: function(s) {
      return (s || '').replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
    },

    init: function() {
      this.generate();
    }
  };

  window.sitemapApp = app;
  app.init();
})();
</script>
</div>

---

## 使い方

1. **URLを追加** — 「URLを追加」ボタンで1件ずつ入力するか、「まとめて貼り付け」タブで複数URLを一括インポートします。
2. **各フィールドを設定** — 最終更新日・更新頻度・優先度（0.0〜1.0）を任意で設定します。
3. **プリセットを活用** — ブログ・ECサイト・ポートフォリオのテンプレートをワンクリックで読み込めます。
4. **コピーまたはダウンロード** — 「XMLをコピー」でクリップボードへ、「sitemap.xmlをダウンロード」でファイル保存。
5. **Googleへ送信** — `sitemap.xml` をサーバーのルートディレクトリにアップロードし、[Google Search Console](https://search.google.com/search-console/) で送信します。

## XMLサイトマップとは

XMLサイトマップは、Webサイトの重要なページをリストアップしたファイルで、GoogleやBingなどの検索エンジンがコンテンツを効率よく発見・インデックスするのを助けます。フォーマットは [sitemaps.org](https://www.sitemaps.org/protocol.html) で定義された標準規格に準拠しています。

各 `<url>` エントリに設定できる項目:

| フィールド | 説明 |
|---|---|
| `<loc>` | ページの完全なURL（必須） |
| `<lastmod>` | ページの最終更新日（YYYY-MM-DD形式） |
| `<changefreq>` | ページの更新頻度（daily、weeklyなど） |
| `<priority>` | 他のページに対する相対的な重要度（0.0〜1.0） |

---

### 関連ツール

> robots.txtを生成 → [Robots.txtジェネレーター](/ja/tools/robots-txt-generator/)

> メタタグを作成 → [メタタグジェネレーター](/ja/tools/meta-tag-generator/)

> プライバシーポリシーを作成 → [プライバシーポリシージェネレーター](/ja/tools/privacy-policy-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [副業ブログの始め方｜お名前.comでドメイン取得→freeeで経費管理まで](/ja/posts/fukugyo-blog-hajimekata-domain-freee/)
