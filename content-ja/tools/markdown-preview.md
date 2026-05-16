---
title: "マークダウンプレビュー - 無料ライブエディター・HTMLプレビューツール"
date: 2025-05-16
description: "マークダウンをリアルタイムでHTMLプレビュー。見出し・表・コードブロック・リンク・画像に対応。HTMLコピー・ファイルエクスポート・ダークモード搭載。無料・ログイン不要。"
categories: ["無料ツール"]
tags: ["マークダウン", "マークダウンエディター", "マークダウンプレビュー", "markdown to html", "ライティングツール", "開発ツール"]
slug: "markdown-preview"
aliases: ["/ja/tools/markdown-editor/", "/ja/tools/md-preview/"]
cover:
  image: "/images/covers/markdown-preview-ja.png"
  alt: "マークダウンプレビューツール"
ShowToc: false
---

<div id="md-app">

<style>
/* ── Reset & Root ─────────────────────────────────────── */
#md-app {
  font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  max-width: 1100px;
  margin: 0 auto;
  color: #1e1b4b;
  --accent: #7c3aed;
  --accent-dk: #6d28d9;
  --accent-lt: #ede9fe;
  --bg: #f8f7ff;
  --surface: #ffffff;
  --border: #d8d3f0;
  --text: #1e1b4b;
  --text-muted: #6b7280;
  --code-bg: #f3f0ff;
  --preview-bg: #ffffff;
  --editor-bg: #faf9ff;
  --status-bg: #f3f0ff;
  --btn-ghost: #ede9fe;
  --btn-ghost-text: #5b21b6;
  --shadow: 0 2px 12px rgba(124,58,237,0.10);
  --radius: 10px;
}
#md-app * { box-sizing: border-box; }

/* Dark theme */
#md-app.md-dark {
  --bg: #0f0e1a;
  --surface: #1a1828;
  --border: #3b3660;
  --text: #e5e1ff;
  --text-muted: #9d97c4;
  --code-bg: #2a2540;
  --preview-bg: #1a1828;
  --editor-bg: #15132a;
  --status-bg: #1a1828;
  --btn-ghost: #2a2540;
  --btn-ghost-text: #c4b5fd;
  --shadow: 0 2px 12px rgba(0,0,0,0.40);
  color: var(--text);
}

#md-app.md-dark #md-editor { color: #e5e1ff; }

/* ── Toolbar ──────────────────────────────────────────── */
#md-toolbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 8px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius) var(--radius) 0 0;
  padding: 10px 14px;
  box-shadow: var(--shadow);
}
#md-toolbar-title {
  font-weight: 700;
  font-size: 1rem;
  color: var(--accent);
  letter-spacing: -0.01em;
}
#md-toolbar-btns {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

/* ── Buttons ──────────────────────────────────────────── */
.md-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 6px 13px;
  border: none;
  border-radius: 6px;
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s, box-shadow 0.15s;
  line-height: 1.2;
  white-space: nowrap;
}
.md-btn:active { transform: scale(0.96); }

.md-btn-primary {
  background: var(--accent);
  color: #fff;
  box-shadow: 0 1px 4px rgba(124,58,237,0.25);
}
.md-btn-primary:hover { background: var(--accent-dk); }

.md-btn-ghost {
  background: var(--btn-ghost);
  color: var(--btn-ghost-text);
}
.md-btn-ghost:hover { filter: brightness(0.95); }

.md-btn-success {
  background: #d1fae5;
  color: #065f46;
}
.md-btn-success:hover { background: #a7f3d0; }

.md-dark .md-btn-success {
  background: #064e3b;
  color: #6ee7b7;
}

/* ── Split Pane Container ─────────────────────────────── */
#md-split {
  display: grid;
  grid-template-columns: 1fr 1fr;
  border-left: 1px solid var(--border);
  border-right: 1px solid var(--border);
  min-height: 460px;
}

@media (max-width: 640px) {
  #md-split {
    grid-template-columns: 1fr;
  }
}

/* ── Pane Labels ──────────────────────────────────────── */
.md-pane-label {
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted);
  padding: 6px 14px 4px;
  background: var(--surface);
  border-bottom: 1px solid var(--border);
}
#md-editor-pane {
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
}
#md-preview-pane {
  display: flex;
  flex-direction: column;
  background: var(--preview-bg);
}

@media (max-width: 640px) {
  #md-editor-pane { border-right: none; border-bottom: 1px solid var(--border); }
}

/* ── Editor ───────────────────────────────────────────── */
#md-editor {
  flex: 1;
  width: 100%;
  padding: 16px;
  font-size: 0.93rem;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  line-height: 1.65;
  border: none;
  outline: none;
  resize: none;
  background: var(--editor-bg);
  color: var(--text);
  min-height: 420px;
}
#md-editor::placeholder { color: var(--text-muted); opacity: 0.7; }

/* ── Preview ──────────────────────────────────────────── */
#md-preview {
  flex: 1;
  padding: 18px 20px;
  overflow-y: auto;
  background: var(--preview-bg);
  color: var(--text);
  font-size: 0.95rem;
  line-height: 1.85;
  min-height: 420px;
}

/* Rendered markdown styles inside preview */
#md-preview h1, #md-preview h2, #md-preview h3,
#md-preview h4, #md-preview h5, #md-preview h6 {
  color: var(--accent);
  margin: 1.1em 0 0.4em;
  line-height: 1.35;
  font-weight: 700;
}
#md-preview h1 { font-size: 1.65em; border-bottom: 2px solid var(--border); padding-bottom: 0.2em; }
#md-preview h2 { font-size: 1.35em; border-bottom: 1px solid var(--border); padding-bottom: 0.15em; }
#md-preview h3 { font-size: 1.15em; }
#md-preview h4 { font-size: 1em; }
#md-preview h5 { font-size: 0.9em; }
#md-preview h6 { font-size: 0.85em; color: var(--text-muted); }

#md-preview p { margin: 0.7em 0; }

#md-preview a { color: var(--accent); text-decoration: underline; }
#md-preview a:hover { color: var(--accent-dk); }

#md-preview strong { font-weight: 700; color: inherit; }
#md-preview em { font-style: italic; }
#md-preview del { text-decoration: line-through; color: var(--text-muted); }

#md-preview code {
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.88em;
  background: var(--code-bg);
  color: #9333ea;
  padding: 0.15em 0.45em;
  border-radius: 4px;
  border: 1px solid var(--border);
}

#md-preview pre {
  background: var(--code-bg);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 14px 16px;
  overflow-x: auto;
  margin: 1em 0;
}
#md-preview pre code {
  background: none;
  border: none;
  padding: 0;
  color: var(--text);
  font-size: 0.87em;
  line-height: 1.6;
}

/* Basic syntax highlight tokens */
#md-preview pre .kw { color: #9333ea; font-weight: 700; }
#md-preview pre .str { color: #059669; }
#md-preview pre .cm { color: #6b7280; font-style: italic; }
#md-preview pre .nm { color: #b45309; }
.md-dark #md-preview pre .kw { color: #c084fc; }
.md-dark #md-preview pre .str { color: #34d399; }
.md-dark #md-preview pre .cm { color: #9ca3af; }
.md-dark #md-preview pre .nm { color: #fbbf24; }

#md-preview blockquote {
  border-left: 4px solid var(--accent);
  margin: 1em 0;
  padding: 8px 16px;
  background: var(--code-bg);
  border-radius: 0 6px 6px 0;
  color: var(--text-muted);
}
#md-preview blockquote p { margin: 0; }

#md-preview ul, #md-preview ol {
  padding-left: 1.6em;
  margin: 0.6em 0;
}
#md-preview li { margin: 0.25em 0; }
#md-preview ul li { list-style-type: disc; }
#md-preview ol li { list-style-type: decimal; }

#md-preview hr {
  border: none;
  border-top: 2px solid var(--border);
  margin: 1.5em 0;
}

#md-preview img {
  max-width: 100%;
  border-radius: 6px;
  margin: 0.5em 0;
}

/* Tables */
#md-preview table {
  border-collapse: collapse;
  width: 100%;
  margin: 1em 0;
  font-size: 0.92em;
}
#md-preview th {
  background: var(--accent-lt);
  color: var(--accent);
  font-weight: 700;
  padding: 8px 12px;
  border: 1px solid var(--border);
  text-align: left;
}
.md-dark #md-preview th {
  background: #2a2540;
  color: #c4b5fd;
}
#md-preview td {
  padding: 7px 12px;
  border: 1px solid var(--border);
}
#md-preview tr:nth-child(even) td { background: var(--code-bg); }

/* ── Status Bar ───────────────────────────────────────── */
#md-status {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 14px;
  background: var(--status-bg);
  border: 1px solid var(--border);
  border-top: none;
  border-radius: 0 0 var(--radius) var(--radius);
  padding: 8px 16px;
  font-size: 0.8rem;
  color: var(--text-muted);
}
.md-stat {
  display: inline-flex;
  align-items: center;
  gap: 4px;
}
.md-stat-val {
  font-weight: 700;
  color: var(--accent);
}
#md-copy-msg {
  margin-left: auto;
  color: #059669;
  font-weight: 600;
  font-size: 0.78rem;
  opacity: 0;
  transition: opacity 0.3s;
}
#md-copy-msg.md-show { opacity: 1; }

/* ── freee CTA ────────────────────────────────────────── */
#md-freee-cta {
  margin-top: 24px;
  padding: 18px 20px;
  background: linear-gradient(135deg, #f0f4ff 0%, #faf5ff 100%);
  border: 1px solid var(--border);
  border-left: 4px solid var(--accent);
  border-radius: 10px;
  font-size: 0.9rem;
  line-height: 1.75;
  color: var(--text);
}
#md-freee-cta strong { color: var(--accent); }
#md-freee-cta a {
  display: inline-block;
  margin-top: 10px;
  padding: 8px 20px;
  background: var(--accent);
  color: #fff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 700;
  font-size: 0.88rem;
  transition: background 0.15s;
}
#md-freee-cta a:hover { background: var(--accent-dk); }

.md-dark #md-freee-cta {
  background: linear-gradient(135deg, #1a1828 0%, #2a2540 100%);
}
</style>

<!-- Toolbar -->
<div id="md-toolbar">
  <span id="md-toolbar-title">&#128196; マークダウンプレビュー</span>
  <div id="md-toolbar-btns">
    <button class="md-btn md-btn-ghost" id="md-btn-sample" onclick="mdLoadSample()">サンプル読み込み</button>
    <button class="md-btn md-btn-ghost" id="md-btn-clear" onclick="mdClear()">クリア</button>
    <button class="md-btn md-btn-ghost" id="md-btn-theme" onclick="mdToggleTheme()">&#9790; ダークモード</button>
    <button class="md-btn md-btn-ghost" id="md-btn-copy" onclick="mdCopyHTML()">HTMLをコピー</button>
    <button class="md-btn md-btn-primary" id="md-btn-export" onclick="mdExport()">.htmlで書き出す</button>
  </div>
</div>

<!-- Split Pane -->
<div id="md-split">
  <div id="md-editor-pane">
    <div class="md-pane-label">マークダウン</div>
    <textarea id="md-editor" placeholder="ここにマークダウンを入力..." spellcheck="false"></textarea>
  </div>
  <div id="md-preview-pane">
    <div class="md-pane-label">プレビュー</div>
    <div id="md-preview"></div>
  </div>
</div>

<!-- Status Bar -->
<div id="md-status">
  <span class="md-stat">単語数: <span class="md-stat-val" id="md-stat-words">0</span></span>
  <span class="md-stat">文字数: <span class="md-stat-val" id="md-stat-chars">0</span></span>
  <span class="md-stat">行数: <span class="md-stat-val" id="md-stat-lines">0</span></span>
  <span class="md-stat">読了時間: <span class="md-stat-val" id="md-stat-read">0 分</span></span>
  <span id="md-copy-msg">クリップボードにコピーしました！</span>
</div>

<!-- freee CTA -->
<div id="md-freee-cta">
  <strong>確定申告・会計管理にはfreee</strong><br>
  マークダウンでドキュメント管理をしている方は、経理もデジタル化しませんか？freeeならクラウドで確定申告が簡単に。<br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
</div>

</div><!-- /#md-app -->

<script>
(function() {
  'use strict';

  /* ── サンプルコンテンツ ─────────────────────────────── */
  var SAMPLE = [
    '# マークダウンプレビューへようこそ',
    '',
    'これは**リアルタイムHTMLプレビュー付き**のマークダウンエディターです。左のペインを編集すると、右側に即座に反映されます。',
    '',
    '## 主な機能',
    '',
    '- リアルタイムのサイドバイサイド編集',
    '- **太字**、*斜体*、~~取り消し線~~',
    '- [リンク](https://example.com)と画像の表示',
    '- コードブロックのシンタックスハイライト',
    '- 表・引用・水平線など',
    '',
    '## コードの例',
    '',
    '```javascript',
    'function greet(name) {',
    '  // 挨拶を返す',
    '  return `こんにちは、${name}！`;',
    '}',
    'console.log(greet("世界"));',
    '```',
    '',
    '## インラインコード',
    '',
    '`const` や `let` は `var` の代わりに使うのが現代的なJavaScriptです。',
    '',
    '## 引用',
    '',
    '> 「最良のツールとは、実際に使われるものだ。」',
    '> — 生産性格言',
    '',
    '## 表',
    '',
    '| 機能 | 対応 |',
    '|------|------|',
    '| 見出し | ✅ |',
    '| 太字・斜体 | ✅ |',
    '| コードブロック | ✅ |',
    '| 表 | ✅ |',
    '| 引用 | ✅ |',
    '| 画像 | ✅ |',
    '',
    '## 画像',
    '',
    '![プレースホルダー画像](https://via.placeholder.com/400x200?text=Markdown+Preview)',
    '',
    '## 水平線',
    '',
    '---',
    '',
    '### 番号付きリスト',
    '',
    '1. マークダウンでコンテンツを書く',
    '2. リアルタイムでHTMLプレビューを確認する',
    '3. HTMLをコピーまたはエクスポートする',
    '',
    '快適なライティングを！'
  ].join('\n');

  /* ── Markdown Parser ─────────────────────────────────── */
  function parseMarkdown(md) {
    var lines = md.split('\n');
    var out = '';
    var i = 0;
    var inFence = false;
    var fenceLang = '';
    var fenceLines = [];

    while (i < lines.length) {
      var line = lines[i];

      // Fenced code block
      var fenceMatch = line.match(/^(`{3,}|~{3,})\s*(\w*)/);
      if (fenceMatch && !inFence) {
        inFence = true;
        fenceLang = fenceMatch[2] || '';
        fenceLines = [];
        i++;
        continue;
      }
      if (inFence) {
        if (/^(`{3,}|~{3,})/.test(line)) {
          var codeContent = fenceLines.map(escapeHtml).join('\n');
          codeContent = highlightCode(codeContent, fenceLang);
          out += '<pre><code' + (fenceLang ? ' class="lang-' + escapeHtml(fenceLang) + '"' : '') + '>' + codeContent + '</code></pre>\n';
          inFence = false;
          fenceLang = '';
          fenceLines = [];
        } else {
          fenceLines.push(line);
        }
        i++;
        continue;
      }

      // Setext headings
      if (i + 1 < lines.length) {
        if (/^=+\s*$/.test(lines[i+1]) && line.trim()) {
          out += '<h1>' + inlineMarkdown(line.trim()) + '</h1>\n';
          i += 2; continue;
        }
        if (/^-+\s*$/.test(lines[i+1]) && line.trim() && !/^\s*[-*+] /.test(line)) {
          out += '<h2>' + inlineMarkdown(line.trim()) + '</h2>\n';
          i += 2; continue;
        }
      }

      // ATX headings
      var hMatch = line.match(/^(#{1,6})\s+(.+?)(?:\s+#+)?$/);
      if (hMatch) {
        var lvl = hMatch[1].length;
        out += '<h' + lvl + '>' + inlineMarkdown(hMatch[2].trim()) + '</h' + lvl + '>\n';
        i++; continue;
      }

      // Horizontal rule
      if (/^(\*{3,}|-{3,}|_{3,})\s*$/.test(line.trim())) {
        out += '<hr>\n'; i++; continue;
      }

      // Blockquote
      if (/^>\s?/.test(line)) {
        var bqLines = [];
        while (i < lines.length && /^>\s?/.test(lines[i])) {
          bqLines.push(lines[i].replace(/^>\s?/, ''));
          i++;
        }
        out += '<blockquote>' + parseParagraphs(bqLines.join('\n')) + '</blockquote>\n';
        continue;
      }

      // Table
      if (/\|/.test(line) && i + 1 < lines.length && /^\|?[\s:|-]+\|/.test(lines[i+1])) {
        var tableLines = [];
        while (i < lines.length && /\|/.test(lines[i])) {
          tableLines.push(lines[i]); i++;
        }
        out += parseTable(tableLines);
        continue;
      }

      // Unordered list
      if (/^(\s*)[-*+] /.test(line)) {
        var ulLines = [];
        while (i < lines.length && /^(\s*)[-*+] /.test(lines[i])) {
          ulLines.push(lines[i]); i++;
        }
        out += '<ul>' + ulLines.map(function(l) {
          return '<li>' + inlineMarkdown(l.replace(/^\s*[-*+] /, '')) + '</li>';
        }).join('') + '</ul>\n';
        continue;
      }

      // Ordered list
      if (/^\d+\.\s/.test(line)) {
        var olLines = [];
        while (i < lines.length && /^\d+\.\s/.test(lines[i])) {
          olLines.push(lines[i]); i++;
        }
        out += '<ol>' + olLines.map(function(l) {
          return '<li>' + inlineMarkdown(l.replace(/^\d+\.\s/, '')) + '</li>';
        }).join('') + '</ol>\n';
        continue;
      }

      // Blank line
      if (line.trim() === '') { out += '\n'; i++; continue; }

      // Paragraph
      var pLines = [];
      while (i < lines.length && lines[i].trim() !== ''
        && !/^#{1,6}\s/.test(lines[i])
        && !/^(\*{3,}|-{3,}|_{3,})\s*$/.test(lines[i].trim())
        && !/^>\s?/.test(lines[i])
        && !/^(\s*)[-*+] /.test(lines[i])
        && !/^\d+\.\s/.test(lines[i])
        && !/\|/.test(lines[i])) {
        pLines.push(lines[i]); i++;
      }
      if (pLines.length) {
        out += '<p>' + inlineMarkdown(pLines.join(' ')) + '</p>\n';
      }
    }

    if (inFence && fenceLines.length) {
      out += '<pre><code>' + fenceLines.map(escapeHtml).join('\n') + '</code></pre>\n';
    }

    return out;
  }

  function parseParagraphs(text) {
    return '<p>' + inlineMarkdown(text) + '</p>';
  }

  function parseTable(lines) {
    if (lines.length < 2) return '';
    var header = lines[0];
    var body = lines.slice(2);
    var headerCells = splitTableRow(header);
    var html = '<table><thead><tr>';
    headerCells.forEach(function(c) { html += '<th>' + inlineMarkdown(c) + '</th>'; });
    html += '</tr></thead><tbody>';
    body.forEach(function(row) {
      var cells = splitTableRow(row);
      html += '<tr>';
      cells.forEach(function(c) { html += '<td>' + inlineMarkdown(c) + '</td>'; });
      html += '</tr>';
    });
    html += '</tbody></table>\n';
    return html;
  }

  function splitTableRow(row) {
    return row.replace(/^\||\|$/g, '').split('|').map(function(c) { return c.trim(); });
  }

  /* ── Inline Markdown ─────────────────────────────────── */
  function inlineMarkdown(text) {
    text = text.replace(/!\[([^\]]*)\]\(([^)]+)\)/g, function(_, alt, src) {
      return '<img src="' + escapeAttr(src) + '" alt="' + escapeAttr(alt) + '">';
    });
    text = text.replace(/\[([^\]]+)\]\(([^)]+)\)/g, function(_, label, href) {
      return '<a href="' + escapeAttr(href) + '">' + escapeHtml(label) + '</a>';
    });
    text = text.replace(/<(https?:\/\/[^>]+)>/g, function(_, url) {
      return '<a href="' + escapeAttr(url) + '">' + escapeHtml(url) + '</a>';
    });
    text = text.replace(/`([^`]+)`/g, function(_, code) {
      return '<code>' + escapeHtml(code) + '</code>';
    });
    text = text.replace(/\*\*\*(.+?)\*\*\*/g, '<strong><em>$1</em></strong>');
    text = text.replace(/___(.+?)___/g, '<strong><em>$1</em></strong>');
    text = text.replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
    text = text.replace(/__(.+?)__/g, '<strong>$1</strong>');
    text = text.replace(/\*(.+?)\*/g, '<em>$1</em>');
    text = text.replace(/_(.+?)_/g, '<em>$1</em>');
    text = text.replace(/~~(.+?)~~/g, '<del>$1</del>');
    text = text.replace(/  $/g, '<br>');
    return text;
  }

  /* ── Basic Syntax Highlighting ───────────────────────── */
  function highlightCode(code, lang) {
    if (!lang) return code;
    var l = lang.toLowerCase();
    if (l === 'javascript' || l === 'js' || l === 'typescript' || l === 'ts') return highlightJS(code);
    if (l === 'python' || l === 'py') return highlightPy(code);
    if (l === 'html' || l === 'xml') return highlightHTML(code);
    if (l === 'css') return highlightCSS(code);
    if (l === 'bash' || l === 'sh' || l === 'shell') return highlightBash(code);
    return code;
  }

  function wrapToken(cls, text) {
    return '<span class="' + cls + '">' + text + '</span>';
  }

  function highlightJS(code) {
    var keywords = /\b(const|let|var|function|return|if|else|for|while|do|switch|case|break|continue|new|class|extends|import|export|default|async|await|try|catch|finally|typeof|instanceof|in|of|this|null|undefined|true|false|void|delete|throw)\b/g;
    var strings = /(["'`])(?:\\[\s\S]|(?!\1)[^\\])*?\1/g;
    var comments = /(\/\/.*$|\/\*[\s\S]*?\*\/)/gm;
    var numbers = /\b(\d+\.?\d*)\b/g;
    return code
      .replace(comments, function(m) { return wrapToken('cm', m); })
      .replace(strings, function(m) { return wrapToken('str', m); })
      .replace(keywords, function(m) { return wrapToken('kw', m); })
      .replace(numbers, function(m) { return wrapToken('nm', m); });
  }

  function highlightPy(code) {
    var keywords = /\b(def|class|import|from|return|if|elif|else|for|while|in|not|and|or|is|None|True|False|pass|break|continue|try|except|finally|with|as|lambda|yield|async|await|raise|del|global|nonlocal|print)\b/g;
    var strings = /("""[\s\S]*?"""|'''[\s\S]*?'''|"(?:\\.|[^"\\])*"|'(?:\\.|[^'\\])*')/g;
    var comments = /(#.*)$/gm;
    var numbers = /\b(\d+\.?\d*)\b/g;
    return code
      .replace(comments, function(m) { return wrapToken('cm', m); })
      .replace(strings, function(m) { return wrapToken('str', m); })
      .replace(keywords, function(m) { return wrapToken('kw', m); })
      .replace(numbers, function(m) { return wrapToken('nm', m); });
  }

  function highlightHTML(code) {
    var tags = /(&lt;\/?[\w]+[^&]*?&gt;)/g;
    var comments = /(&lt;!--[\s\S]*?--&gt;)/g;
    return code
      .replace(comments, function(m) { return wrapToken('cm', m); })
      .replace(tags, function(m) { return wrapToken('kw', m); });
  }

  function highlightCSS(code) {
    var selectors = /^([^{]+)(?=\{)/gm;
    var props = /(\s)([\w-]+)(?=\s*:)/g;
    var strings = /(["'])(?:\\.|[^\\])*?\1/g;
    var comments = /(\/\*[\s\S]*?\*\/)/g;
    return code
      .replace(comments, function(m) { return wrapToken('cm', m); })
      .replace(strings, function(m) { return wrapToken('str', m); })
      .replace(selectors, function(m) { return wrapToken('kw', m); })
      .replace(props, function(_, sp, p) { return sp + wrapToken('nm', p); });
  }

  function highlightBash(code) {
    var keywords = /\b(echo|cd|ls|mkdir|rm|mv|cp|cat|grep|sed|awk|curl|wget|git|npm|yarn|pip|export|source|if|then|else|fi|for|do|done|while|case|esac|function|return|exit)\b/g;
    var strings = /(["'])(?:\\.|[^\\])*?\1/g;
    var comments = /(#.*)$/gm;
    return code
      .replace(comments, function(m) { return wrapToken('cm', m); })
      .replace(strings, function(m) { return wrapToken('str', m); })
      .replace(keywords, function(m) { return wrapToken('kw', m); });
  }

  /* ── Utilities ───────────────────────────────────────── */
  function escapeHtml(s) {
    return String(s)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }
  function escapeAttr(s) {
    return String(s).replace(/"/g, '&quot;');
  }

  /* ── Stats ───────────────────────────────────────────── */
  function updateStats(text) {
    var words = text.trim() ? text.trim().split(/\s+/).length : 0;
    var chars = text.length;
    var lines = text ? text.split('\n').length : 0;
    var readMin = Math.ceil(words / 400) || 1;
    document.getElementById('md-stat-words').textContent = words.toLocaleString();
    document.getElementById('md-stat-chars').textContent = chars.toLocaleString();
    document.getElementById('md-stat-lines').textContent = lines.toLocaleString();
    document.getElementById('md-stat-read').textContent = readMin + ' 分';
  }

  /* ── Render ──────────────────────────────────────────── */
  function render() {
    var text = document.getElementById('md-editor').value;
    document.getElementById('md-preview').innerHTML = parseMarkdown(text);
    updateStats(text);
  }

  /* ── Theme ───────────────────────────────────────────── */
  var darkMode = false;
  window.mdToggleTheme = function() {
    darkMode = !darkMode;
    var app = document.getElementById('md-app');
    var btn = document.getElementById('md-btn-theme');
    if (darkMode) {
      app.classList.add('md-dark');
      btn.textContent = '\u2600 ライトモード';
    } else {
      app.classList.remove('md-dark');
      btn.textContent = '\u263D ダークモード';
    }
  };

  /* ── Copy HTML ───────────────────────────────────────── */
  window.mdCopyHTML = function() {
    var html = document.getElementById('md-preview').innerHTML;
    var msg = document.getElementById('md-copy-msg');
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(html).then(function() {
        msg.classList.add('md-show');
        setTimeout(function() { msg.classList.remove('md-show'); }, 2000);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = html;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      msg.classList.add('md-show');
      setTimeout(function() { msg.classList.remove('md-show'); }, 2000);
    }
  };

  /* ── Export HTML ─────────────────────────────────────── */
  window.mdExport = function() {
    var previewHtml = document.getElementById('md-preview').innerHTML;
    var fullHtml = '<!DOCTYPE html>\n<html lang="ja">\n<head>\n<meta charset="UTF-8">\n'
      + '<meta name="viewport" content="width=device-width, initial-scale=1.0">\n'
      + '<title>マークダウン書き出し</title>\n'
      + '<style>\n'
      + 'body { font-family: \'Helvetica Neue\', Arial, \'Hiragino Kaku Gothic ProN\', Meiryo, sans-serif; max-width: 860px; margin: 40px auto; padding: 0 20px; color: #1e1b4b; line-height: 1.85; }\n'
      + 'h1,h2,h3,h4,h5,h6 { color: #7c3aed; }\n'
      + 'h1,h2 { border-bottom: 1px solid #d8d3f0; padding-bottom: 0.2em; }\n'
      + 'code { background: #f3f0ff; color: #9333ea; padding: 0.15em 0.45em; border-radius: 4px; font-size: 0.88em; }\n'
      + 'pre { background: #f3f0ff; border-radius: 8px; padding: 14px 16px; overflow-x: auto; }\n'
      + 'pre code { background: none; color: #1e1b4b; }\n'
      + 'blockquote { border-left: 4px solid #7c3aed; padding: 8px 16px; background: #f3f0ff; border-radius: 0 6px 6px 0; color: #6b7280; margin: 1em 0; }\n'
      + 'table { border-collapse: collapse; width: 100%; margin: 1em 0; }\n'
      + 'th { background: #ede9fe; color: #7c3aed; padding: 8px 12px; border: 1px solid #d8d3f0; text-align: left; }\n'
      + 'td { padding: 7px 12px; border: 1px solid #d8d3f0; }\n'
      + 'tr:nth-child(even) td { background: #f3f0ff; }\n'
      + 'img { max-width: 100%; border-radius: 6px; }\n'
      + 'hr { border: none; border-top: 2px solid #d8d3f0; margin: 1.5em 0; }\n'
      + 'a { color: #7c3aed; }\n'
      + '</style>\n</head>\n<body>\n'
      + previewHtml
      + '\n</body>\n</html>';
    var blob = new Blob([fullHtml], { type: 'text/html' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url;
    a.download = 'markdown-export.html';
    document.body.appendChild(a);
    a.click();
    setTimeout(function() {
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
    }, 100);
  };

  /* ── Sample / Clear ──────────────────────────────────── */
  window.mdLoadSample = function() {
    document.getElementById('md-editor').value = SAMPLE;
    render();
  };
  window.mdClear = function() {
    document.getElementById('md-editor').value = '';
    render();
  };

  /* ── Init ────────────────────────────────────────────── */
  var editor = document.getElementById('md-editor');
  editor.addEventListener('input', render);
  editor.value = SAMPLE;
  render();

})();
</script>

---

## 関連ツール

> Html Beautifier → [Html Beautifierツール](/ja/tools/html-beautifier/)
> Html Entity Converter → [Html Entity Converterツール](/ja/tools/html-entity-converter/)
> Html Entity Encoder → [Html Entity Encoderツール](/ja/tools/html-entity-encoder/)

