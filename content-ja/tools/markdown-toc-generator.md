---
title: "Markdown目次ジェネレーター"
slug: "markdown-toc-generator"
description: "無料のMarkdown目次（TOC）生成ツール。Markdownを貼り付けてクリック可能な目次を自動生成。GitHub形式のアンカーリンク対応。"
date: 2025-10-27
categories: ["無料ツール"]
tags: ["markdown", "目次", "TOC", "アンカーリンク", "ドキュメント"]
ShowToc: false
cover:
  image: "/images/covers/markdown-toc-generator-ja.png"
  alt: "Markdown目次ジェネレーター — Markdownの見出しからクリック可能な目次を自動生成する無料ツール"
---

Markdownドキュメントからクリック可能な目次（TOC）を自動生成します。Markdownを貼り付けて見出しレベルやリスト形式を設定するだけで、GitHub形式のアンカーリンク付き目次が完成します。そのままドキュメントの先頭にコピーして使えます。

<div id="mt-app">

<style>
  #mt-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    color: #1a1a2e;
    max-width: 900px;
    margin: 0 auto;
    padding: 0;
  }
  #mt-app * { box-sizing: border-box; }

  #mt-app .mt-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 16px;
  }
  @media (max-width: 640px) {
    #mt-app .mt-grid { grid-template-columns: 1fr; }
  }

  #mt-app .mt-panel {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 10px;
    overflow: hidden;
  }
  #mt-app .mt-panel-header {
    background: #f8fafc;
    border-bottom: 1px solid #e2e8f0;
    padding: 10px 14px;
    font-size: 13px;
    font-weight: 600;
    color: #475569;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  #mt-app textarea {
    width: 100%;
    border: none;
    outline: none;
    resize: vertical;
    padding: 12px 14px;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
    font-size: 13px;
    line-height: 1.6;
    color: #1e293b;
    background: #fff;
    min-height: 260px;
    display: block;
  }
  #mt-app .mt-output {
    padding: 12px 14px;
    font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
    font-size: 13px;
    line-height: 1.6;
    color: #1e293b;
    min-height: 260px;
    white-space: pre-wrap;
    word-break: break-word;
    background: #fff;
  }
  #mt-app .mt-output.placeholder {
    color: #94a3b8;
    font-style: italic;
  }

  #mt-app .mt-controls {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 10px;
    padding: 14px 16px;
    margin-bottom: 16px;
    display: flex;
    flex-wrap: wrap;
    gap: 18px;
    align-items: flex-end;
  }
  #mt-app .mt-control-group {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }
  #mt-app .mt-control-group label {
    font-size: 12px;
    font-weight: 600;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }
  #mt-app select,
  #mt-app input[type="checkbox"] {
    cursor: pointer;
  }
  #mt-app select {
    padding: 6px 10px;
    border: 1px solid #cbd5e1;
    border-radius: 6px;
    font-size: 13px;
    color: #1e293b;
    background: #f8fafc;
    outline: none;
    min-width: 90px;
  }
  #mt-app select:focus {
    border-color: #6366f1;
    box-shadow: 0 0 0 2px rgba(99,102,241,0.15);
  }
  #mt-app .mt-checkbox-row {
    display: flex;
    align-items: center;
    gap: 7px;
    font-size: 13px;
    color: #334155;
    padding-top: 4px;
  }
  #mt-app input[type="checkbox"] {
    width: 15px;
    height: 15px;
    accent-color: #6366f1;
  }

  #mt-app .mt-btn-row {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 16px;
  }
  #mt-app .mt-btn {
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
  }
  #mt-app .mt-btn:active { transform: scale(0.97); }
  #mt-app .mt-btn-primary {
    background: #6366f1;
    color: #fff;
  }
  #mt-app .mt-btn-primary:hover { background: #4f46e5; }
  #mt-app .mt-btn-secondary {
    background: #f1f5f9;
    color: #334155;
    border: 1px solid #e2e8f0;
  }
  #mt-app .mt-btn-secondary:hover { background: #e2e8f0; }
  #mt-app .mt-btn-copy {
    background: #10b981;
    color: #fff;
  }
  #mt-app .mt-btn-copy:hover { background: #059669; }
  #mt-app .mt-btn-copy.copied { background: #475569; }

  #mt-app .mt-stats {
    font-size: 12px;
    color: #64748b;
    background: #f8fafc;
    border: 1px solid #e2e8f0;
    border-radius: 8px;
    padding: 10px 14px;
    margin-bottom: 16px;
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
  }
  #mt-app .mt-stat { display: flex; flex-direction: column; gap: 2px; }
  #mt-app .mt-stat strong { font-size: 18px; color: #1e293b; font-weight: 700; }

  #mt-app .mt-preview {
    background: #fff;
    border: 1px solid #e2e8f0;
    border-radius: 10px;
    overflow: hidden;
    margin-bottom: 16px;
  }
  #mt-app .mt-preview-body {
    padding: 14px 18px;
    font-size: 14px;
    line-height: 1.7;
    color: #1e293b;
  }
  #mt-app .mt-preview-body ul,
  #mt-app .mt-preview-body ol {
    margin: 0;
    padding-left: 20px;
  }
  #mt-app .mt-preview-body li { margin: 2px 0; }
  #mt-app .mt-preview-body a {
    color: #6366f1;
    text-decoration: none;
  }
  #mt-app .mt-preview-body a:hover { text-decoration: underline; }

  /* freee CTA */
  #mt-app .mt-freee-cta {
    background: linear-gradient(135deg, #00c4a7 0%, #00a88d 100%);
    border-radius: 12px;
    padding: 20px 24px;
    margin-bottom: 16px;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    flex-wrap: wrap;
  }
  #mt-app .mt-freee-cta .cta-text h3 {
    margin: 0 0 4px;
    font-size: 15px;
    font-weight: 700;
  }
  #mt-app .mt-freee-cta .cta-text p {
    margin: 0;
    font-size: 13px;
    opacity: 0.9;
  }
  #mt-app .mt-freee-cta .cta-btn {
    background: #fff;
    color: #00a88d;
    font-weight: 700;
    font-size: 13px;
    padding: 10px 20px;
    border-radius: 7px;
    text-decoration: none;
    white-space: nowrap;
    transition: opacity 0.15s;
    flex-shrink: 0;
  }
  #mt-app .mt-freee-cta .cta-btn:hover { opacity: 0.9; }
</style>

<div class="mt-controls">
  <div class="mt-control-group">
    <label>最小見出しレベル</label>
    <select id="mt-min-level">
      <option value="1">H1</option>
      <option value="2" selected>H2</option>
      <option value="3">H3</option>
      <option value="4">H4</option>
    </select>
  </div>
  <div class="mt-control-group">
    <label>最大見出しレベル</label>
    <select id="mt-max-level">
      <option value="2">H2</option>
      <option value="3" selected>H3</option>
      <option value="4">H4</option>
      <option value="5">H5</option>
      <option value="6">H6</option>
    </select>
  </div>
  <div class="mt-control-group">
    <label>リスト形式</label>
    <select id="mt-list-style">
      <option value="bullet" selected>箇条書き ( - )</option>
      <option value="numbered">番号付き ( 1. )</option>
    </select>
  </div>
  <div class="mt-control-group">
    <label>インデント</label>
    <select id="mt-indent">
      <option value="2" selected>スペース2個</option>
      <option value="4">スペース4個</option>
      <option value="tab">タブ</option>
    </select>
  </div>
  <div class="mt-control-group">
    <label>&nbsp;</label>
    <div class="mt-checkbox-row">
      <input type="checkbox" id="mt-bold-h1">
      <span>H1を太字にする</span>
    </div>
  </div>
  <div class="mt-control-group">
    <label>&nbsp;</label>
    <div class="mt-checkbox-row">
      <input type="checkbox" id="mt-add-title" checked>
      <span>「目次」ヘッダーを追加</span>
    </div>
  </div>
</div>

<div class="mt-btn-row">
  <button class="mt-btn mt-btn-primary" onclick="mtGenerate()">&#9654; 目次を生成</button>
  <button class="mt-btn mt-btn-secondary" onclick="mtLoadSample()">サンプルを読み込む</button>
  <button class="mt-btn mt-btn-secondary" onclick="mtClear()">クリア</button>
  <button class="mt-btn mt-btn-copy" id="mt-copy-btn" onclick="mtCopy()">&#128203; 目次をコピー</button>
</div>

<div class="mt-grid">
  <div class="mt-panel">
    <div class="mt-panel-header">
      <span>Markdown入力</span>
      <span id="mt-line-count" style="font-weight:400;color:#94a3b8;"></span>
    </div>
    <textarea id="mt-input" placeholder="ここにMarkdownを貼り付けてください...&#10;&#10;# はじめに&#10;## セットアップ&#10;### インストール&#10;## 使い方&#10;### 基本的な例&#10;## APIリファレンス" oninput="mtOnInput()"></textarea>
  </div>
  <div class="mt-panel">
    <div class="mt-panel-header">
      <span>生成された目次</span>
    </div>
    <div class="mt-output placeholder" id="mt-output">生成ボタンを押すと目次がここに表示されます...</div>
  </div>
</div>

<div class="mt-stats" id="mt-stats" style="display:none;">
  <div class="mt-stat"><strong id="stat-headings">0</strong><span>見出し数</span></div>
  <div class="mt-stat"><strong id="stat-h1">0</strong><span>H1</span></div>
  <div class="mt-stat"><strong id="stat-h2">0</strong><span>H2</span></div>
  <div class="mt-stat"><strong id="stat-h3">0</strong><span>H3</span></div>
  <div class="mt-stat"><strong id="stat-h4plus">0</strong><span>H4以上</span></div>
  <div class="mt-stat"><strong id="stat-toc-lines">0</strong><span>目次の行数</span></div>
</div>

<div class="mt-preview" id="mt-preview" style="display:none;">
  <div class="mt-panel-header" style="background:#f8fafc;border-bottom:1px solid #e2e8f0;padding:10px 14px;font-size:13px;font-weight:600;color:#475569;">
    プレビュー
  </div>
  <div class="mt-preview-body" id="mt-preview-body"></div>
</div>

<div class="mt-freee-cta">
  <div class="cta-text">
    <h3>フリーランス・個人事業主の確定申告をかんたんに</h3>
    <p>freee会計なら請求書・帳簿・確定申告書類をまとめて管理。クラウドだからどこからでもアクセスできます。</p>
  </div>
  <a class="cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener sponsored">freeeを無料で試す</a>
</div>

<script>
(function() {
  function slugify(text) {
    return text
      .toLowerCase()
      .replace(/[^\w\s\-]/g, '')
      .replace(/\s+/g, '-')
      .replace(/-+/g, '-')
      .replace(/^-|-$/g, '');
  }

  function parseHeadings(markdown) {
    const lines = markdown.split('\n');
    const headings = [];
    let inFencedCode = false;
    let fenceChar = '';

    for (let i = 0; i < lines.length; i++) {
      const line = lines[i];
      const fenceMatch = line.match(/^(`{3,}|~{3,})/);
      if (fenceMatch) {
        if (!inFencedCode) {
          inFencedCode = true;
          fenceChar = fenceMatch[1][0];
        } else if (fenceChar === fenceMatch[1][0]) {
          inFencedCode = false;
          fenceChar = '';
        }
        continue;
      }
      if (inFencedCode) continue;

      const headingMatch = line.match(/^(#{1,6})\s+(.+?)(?:\s+#+\s*)?$/);
      if (headingMatch) {
        const level = headingMatch[1].length;
        const text = headingMatch[2].trim();
        const plainText = text
          .replace(/`[^`]+`/g, m => m.slice(1,-1))
          .replace(/\*\*([^*]+)\*\*/g, '$1')
          .replace(/__([^_]+)__/g, '$1')
          .replace(/\*([^*]+)\*/g, '$1')
          .replace(/_([^_]+)_/g, '$1')
          .replace(/\[([^\]]+)\]\([^)]+\)/g, '$1');
        headings.push({ level, text, plainText });
      }
    }
    return headings;
  }

  function buildToc(headings, opts) {
    const { minLevel, maxLevel, listStyle, indent, boldH1, addTitle } = opts;
    const filtered = headings.filter(h => h.level >= minLevel && h.level <= maxLevel);
    if (filtered.length === 0) return { toc: '', lines: 0 };

    const slugCount = {};
    const counters = {};
    const tocLines = [];

    if (addTitle) tocLines.push('## 目次\n');

    for (const h of filtered) {
      let slug = slugify(h.plainText);
      if (slugCount[slug] === undefined) {
        slugCount[slug] = 0;
      } else {
        slugCount[slug]++;
        slug = slug + '-' + slugCount[slug];
      }

      const depth = h.level - minLevel;
      const indentStr = indent === 'tab'
        ? '\t'.repeat(depth)
        : ' '.repeat(Number(indent) * depth);

      let prefix;
      if (listStyle === 'numbered') {
        for (const key of Object.keys(counters)) {
          if (Number(key) > h.level) delete counters[key];
        }
        counters[h.level] = (counters[h.level] || 0) + 1;
        prefix = counters[h.level] + '.';
      } else {
        prefix = '-';
      }

      let displayText = h.text;
      if (boldH1 && h.level === 1) displayText = '**' + displayText + '**';

      tocLines.push(indentStr + prefix + ' [' + displayText + '](#' + slug + ')');
    }

    const toc = tocLines.join('\n');
    return { toc, lines: filtered.length };
  }

  function updateStats(headings, tocLineCount) {
    const el = id => document.getElementById(id);
    const counts = { 1:0, 2:0, 3:0, '4+':0 };
    for (const h of headings) {
      if (h.level <= 3) counts[h.level]++;
      else counts['4+']++;
    }
    el('stat-headings').textContent = headings.length;
    el('stat-h1').textContent = counts[1];
    el('stat-h2').textContent = counts[2];
    el('stat-h3').textContent = counts[3];
    el('stat-h4plus').textContent = counts['4+'];
    el('stat-toc-lines').textContent = tocLineCount;
    document.getElementById('mt-stats').style.display = 'flex';
  }

  function renderPreview(tocMd) {
    const lines = tocMd.split('\n');
    let html = '';
    let listStack = [];
    const isNumbered = lines.some(l => /^\s*\d+\./.test(l));

    const flushTo = depth => {
      while (listStack.length > 0 && listStack[listStack.length-1].depth > depth) {
        const t = listStack.pop();
        html += t.type === 'ol' ? '</ol>' : '</ul>';
      }
    };

    for (const line of lines) {
      if (!line.trim()) continue;
      if (line.startsWith('## ')) {
        flushTo(-1);
        html += '<strong>' + esc(line.replace(/^## /, '')) + '</strong>';
        continue;
      }
      const itemMatch = line.match(/^(\s*)(?:\d+\.|-)\s+\[(.+?)\]\(#([^)]+)\)(.*)$/);
      if (!itemMatch) continue;
      const [, ws, text, anchor] = itemMatch;
      const depth = ws.replace(/\t/g, '  ').length;
      const type = isNumbered && /^\s*\d+\./.test(line) ? 'ol' : 'ul';

      flushTo(depth - 1);

      if (listStack.length === 0 || listStack[listStack.length-1].depth < depth) {
        html += type === 'ol' ? '<ol>' : '<ul>';
        listStack.push({ type, depth });
      }

      let displayText = esc(text).replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
      html += '<li><a href="#' + esc(anchor) + '">' + displayText + '</a></li>';
    }
    flushTo(-1);

    document.getElementById('mt-preview-body').innerHTML = html || '<em style="color:#94a3b8">プレビューできる内容がありません。</em>';
    document.getElementById('mt-preview').style.display = 'block';
  }

  function esc(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function getOpts() {
    return {
      minLevel: Number(document.getElementById('mt-min-level').value),
      maxLevel: Number(document.getElementById('mt-max-level').value),
      listStyle: document.getElementById('mt-list-style').value,
      indent: document.getElementById('mt-indent').value,
      boldH1: document.getElementById('mt-bold-h1').checked,
      addTitle: document.getElementById('mt-add-title').checked,
    };
  }

  window.mtGenerate = function() {
    const input = document.getElementById('mt-input').value;
    if (!input.trim()) {
      setOutput('Markdownを入力してください。', true);
      return;
    }
    const opts = getOpts();
    const headings = parseHeadings(input);

    if (headings.length === 0) {
      setOutput('見出しが見つかりませんでした。# で始まる行があるか確認してください。', true);
      document.getElementById('mt-stats').style.display = 'none';
      document.getElementById('mt-preview').style.display = 'none';
      return;
    }

    const { toc, lines } = buildToc(headings, opts);
    if (!toc) {
      setOutput('選択したレベル範囲（H' + opts.minLevel + '〜H' + opts.maxLevel + '）の見出しが見つかりませんでした。', true);
      return;
    }

    setOutput(toc, false);
    updateStats(headings, lines);
    renderPreview(toc);
  };

  function setOutput(text, isPlaceholder) {
    const el = document.getElementById('mt-output');
    el.textContent = text;
    el.classList.toggle('placeholder', isPlaceholder);
  }

  window.mtOnInput = function() {
    const input = document.getElementById('mt-input').value;
    const lines = input ? input.split('\n').length : 0;
    document.getElementById('mt-line-count').textContent = lines ? lines + ' 行' : '';
  };

  window.mtClear = function() {
    document.getElementById('mt-input').value = '';
    setOutput('生成ボタンを押すと目次がここに表示されます...', true);
    document.getElementById('mt-line-count').textContent = '';
    document.getElementById('mt-stats').style.display = 'none';
    document.getElementById('mt-preview').style.display = 'none';
  };

  window.mtLoadSample = function() {
    document.getElementById('mt-input').value = `# プロジェクトドキュメント

## はじめに

プロジェクトへようこそ。

### このツールとは

ツールの概要説明。

### なぜ使うのか

主なメリットとユースケース。

## セットアップ

### 前提条件

- Node.js 18以上
- npmまたはyarn

### インストール

インストール手順の説明。

### 設定

ツールの設定方法。

## 使い方

### 基本的な例

シンプルな使用例。

### 高度なオプション

高度な設定オプション。

#### オプションA

オプションAの詳細。

#### オプションB

オプションBの詳細。

## APIリファレンス

### メソッド

利用可能なメソッド一覧。

### イベント

利用可能なイベント一覧。

## コントリビューション

プロジェクトへの貢献方法。

## ライセンス

MITライセンス。`;
    mtOnInput();
    mtGenerate();
  };

  window.mtCopy = function() {
    const output = document.getElementById('mt-output');
    const text = output.textContent;
    if (!text || output.classList.contains('placeholder')) return;
    navigator.clipboard.writeText(text).then(() => {
      const btn = document.getElementById('mt-copy-btn');
      btn.textContent = 'コピーしました！';
      btn.classList.add('copied');
      setTimeout(() => {
        btn.innerHTML = '&#128203; 目次をコピー';
        btn.classList.remove('copied');
      }, 2000);
    });
  };
})();
</script>

</div>

## 使い方

1. **Markdownを貼り付ける** — 左側の入力エリアにMarkdownテキストを貼り付けます
2. **オプションを設定する** — 見出しレベル、リスト形式、インデントを選択します
3. **「目次を生成」をクリック** — 全見出しが抽出され、目次が生成されます
4. **目次をコピー** — 生成された目次をコピーしてMarkdownドキュメントの先頭に貼り付けます

## アンカーリンクの仕組み

このツールは **GitHub形式のスラッグアルゴリズム** でアンカーリンクを生成します。

- テキストを小文字に変換
- スペースをハイフン `-` に変換
- ハイフン以外の特殊文字を削除
- **重複する見出し** には自動的に連番サフィックスを付与：`#installation`、`#installation-1`、`#installation-2`

この形式はGitHub、GitLab、Obsidian、VS Codeプレビュー、ほとんどのMarkdownレンダラーで動作します。

## 関連ツール

- [Markdownプレビュー](/tools/markdown-preview/) — Markdownをリアルタイムにレンダリング
- [Markdownリンクチェッカー](/tools/markdown-link-checker/) — Markdown内のリンクを一括検証

---

<small>※本ページにはアフィリエイト広告が含まれます（A8.net）。</small>
