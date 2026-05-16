---
title: "HTML→Markdown変換ツール"
description: "無料のHTML→Markdown変換ツール。HTMLを貼り付けるだけでMarkdownに即変換。見出し・リンク・画像・リスト・テーブル・コードブロック対応。会員登録不要。"
slug: html-to-markdown
date: 2025-05-16
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/html-to-markdown-ja.png
  alt: "HTML→Markdown変換ツール"
---

HTMLを左パネルに貼り付けるだけで、即座にMarkdownへ変換します。サーバー不要・会員登録不要、すべてブラウザ内で完結します。

> Markdownの見た目を確認したい → [Markdownプレビューツール](/ja/tools/markdown-preview/)
> テーブルをゼロから作りたい → [Markdownテーブルジェネレーター](/ja/tools/markdown-table-generator/)

<div id="hm-app">
<style>
#hm-app *,#hm-app *::before,#hm-app *::after{box-sizing:border-box;margin:0;padding:0}
#hm-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;font-size:14px;color:#1e293b;line-height:1.5}
#hm-app .hm-toolbar{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-bottom:12px;padding:10px 14px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:8px}
#hm-app .hm-btn{display:inline-flex;align-items:center;gap:5px;padding:6px 14px;border:1px solid #cbd5e1;border-radius:6px;background:#fff;color:#334155;font-size:13px;font-weight:500;cursor:pointer;transition:background .15s,border-color .15s}
#hm-app .hm-btn:hover{background:#f1f5f9;border-color:#94a3b8}
#hm-app .hm-btn.hm-btn-primary{background:#2563eb;border-color:#2563eb;color:#fff}
#hm-app .hm-btn.hm-btn-primary:hover{background:#1d4ed8;border-color:#1d4ed8}
#hm-app .hm-btn.hm-btn-success{background:#16a34a;border-color:#16a34a;color:#fff}
#hm-app .hm-btn.hm-btn-success:hover{background:#15803d;border-color:#15803d}
#hm-app .hm-toggles{display:flex;flex-wrap:wrap;gap:10px;align-items:center;margin-left:auto}
#hm-app .hm-toggle-label{display:flex;align-items:center;gap:5px;font-size:12px;color:#64748b;cursor:pointer;user-select:none}
#hm-app .hm-toggle-label input[type=checkbox]{width:14px;height:14px;cursor:pointer;accent-color:#2563eb}
#hm-app .hm-panels{display:grid;grid-template-columns:1fr 1fr;gap:12px}
@media(max-width:680px){#hm-app .hm-panels{grid-template-columns:1fr}}
#hm-app .hm-panel{display:flex;flex-direction:column;gap:6px}
#hm-app .hm-panel-header{display:flex;justify-content:space-between;align-items:center;font-size:12px;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:.04em}
#hm-app textarea,#hm-app .hm-output{width:100%;min-height:360px;padding:12px;border:1px solid #e2e8f0;border-radius:8px;font-family:"SFMono-Regular",Consolas,"Liberation Mono",Menlo,monospace;font-size:12.5px;line-height:1.6;resize:vertical;background:#fff;color:#1e293b;transition:border-color .15s}
#hm-app textarea:focus{outline:none;border-color:#2563eb;box-shadow:0 0 0 3px rgba(37,99,235,.1)}
#hm-app .hm-output{white-space:pre-wrap;word-break:break-word;background:#f8fafc;overflow:auto;cursor:text}
#hm-app .hm-status{font-size:11px;color:#94a3b8;text-align:right;margin-top:4px}
#hm-app .hm-copy-notice{font-size:12px;color:#16a34a;font-weight:600}
</style>

<div class="hm-toolbar">
  <button class="hm-btn hm-btn-primary" id="hm-sample-btn">&#128196; サンプルHTMLを読み込む</button>
  <button class="hm-btn" id="hm-clear-btn">&#10005; クリア</button>
  <div class="hm-toggles">
    <label class="hm-toggle-label"><input type="checkbox" id="hm-gfm" checked> GitHub Flavored Markdown</label>
    <label class="hm-toggle-label"><input type="checkbox" id="hm-reflinks"> 参照スタイルリンク</label>
  </div>
</div>

<div class="hm-panels">
  <div class="hm-panel">
    <div class="hm-panel-header"><span>HTML 入力</span><span id="hm-char-count">0 文字</span></div>
    <textarea id="hm-input" placeholder="HTMLをここに貼り付けてください…" spellcheck="false"></textarea>
  </div>
  <div class="hm-panel">
    <div class="hm-panel-header">
      <span>Markdown 出力</span>
      <span id="hm-copy-status"></span>
    </div>
    <div class="hm-output" id="hm-output" aria-live="polite"></div>
    <div style="display:flex;justify-content:flex-end;margin-top:6px">
      <button class="hm-btn hm-btn-success" id="hm-copy-btn">&#128203; Markdownをコピー</button>
    </div>
  </div>
</div>

<div class="hm-status" id="hm-line-count"></div>

<script>
(function () {
  'use strict';

  var input   = document.getElementById('hm-input');
  var output  = document.getElementById('hm-output');
  var copyBtn = document.getElementById('hm-copy-btn');
  var copyStatus = document.getElementById('hm-copy-status');
  var charCount  = document.getElementById('hm-char-count');
  var lineCount  = document.getElementById('hm-line-count');
  var gfmToggle  = document.getElementById('hm-gfm');
  var refToggle  = document.getElementById('hm-reflinks');
  var sampleBtn  = document.getElementById('hm-sample-btn');
  var clearBtn   = document.getElementById('hm-clear-btn');

  var SAMPLE_HTML = [
    '<h1>HTML→Markdown変換サンプル</h1>',
    '<p>このコンバーターは<strong>太字</strong>、<em>斜体</em>、<a href="https://example.com">リンク</a>に対応しています。</p>',
    '<h2>対応機能</h2>',
    '<ul>',
    '  <li>見出し h1〜h6</li>',
    '  <li>順序あり・なしリスト',
    '    <ul><li>ネストされたリストも対応</li></ul>',
    '  </li>',
    '  <li>テーブル、コードブロック、引用</li>',
    '</ul>',
    '<h2>コード例</h2>',
    '<pre><code class="language-javascript">function hello(name) {\n  return `こんにちは、${name}！`;\n}</code></pre>',
    '<h2>テーブル例</h2>',
    '<table>',
    '  <thead><tr><th>項目</th><th>型</th><th>必須</th></tr></thead>',
    '  <tbody>',
    '    <tr><td>title</td><td>string</td><td>はい</td></tr>',
    '    <tr><td>date</td><td>string</td><td>はい</td></tr>',
    '    <tr><td>draft</td><td>boolean</td><td>いいえ</td></tr>',
    '  </tbody>',
    '</table>',
    '<blockquote><p>これは<strong>引用ブロック</strong>のサンプルです。</p></blockquote>',
    '<hr>',
    '<p>画像の例: <img src="https://example.com/photo.jpg" alt="サンプル画像"></p>'
  ].join('\n');

  /* ── Core converter ── */
  function htmlToMarkdown(html, opts) {
    opts = opts || {};
    var gfm  = opts.gfm  !== false;
    var refs  = opts.refs || false;

    var refLinks = [];

    var parser = new DOMParser();
    var doc = parser.parseFromString('<body>' + html + '</body>', 'text/html');
    var body = doc.body;

    function nodeToMd(node, ctx) {
      ctx = ctx || { listDepth: 0, listType: null, inPre: false };

      if (node.nodeType === 3) {
        if (ctx.inPre) return node.textContent;
        var t = node.textContent.replace(/\n/g, ' ').replace(/\s+/g, ' ');
        return t;
      }

      if (node.nodeType !== 1) return '';

      var tag = node.tagName.toLowerCase();
      var children = Array.from(node.childNodes);

      function inner(overrideCtx) {
        return children.map(function (c) {
          return nodeToMd(c, overrideCtx || ctx);
        }).join('');
      }

      /* Heading */
      if (/^h[1-6]$/.test(tag)) {
        var level = parseInt(tag[1], 10);
        var hashes = '';
        for (var i = 0; i < level; i++) hashes += '#';
        return '\n\n' + hashes + ' ' + inner().trim() + '\n\n';
      }

      /* Paragraph */
      if (tag === 'p') {
        return '\n\n' + inner().trim() + '\n\n';
      }

      /* Line break */
      if (tag === 'br') {
        return ctx.inPre ? '\n' : '  \n';
      }

      /* Horizontal rule */
      if (tag === 'hr') {
        return '\n\n---\n\n';
      }

      /* Strong / em */
      if (tag === 'strong' || tag === 'b') {
        return '**' + inner().trim() + '**';
      }
      if (tag === 'em' || tag === 'i') {
        return '_' + inner().trim() + '_';
      }

      /* Inline code */
      if (tag === 'code' && ctx.inPre) {
        return inner({ inPre: true });
      }
      if (tag === 'code') {
        return '`' + node.textContent + '`';
      }

      /* Pre / code block */
      if (tag === 'pre') {
        var codeEl = node.querySelector('code');
        var lang = '';
        if (codeEl) {
          var cls = codeEl.className || '';
          var m = cls.match(/language-(\S+)/);
          lang = m ? m[1] : '';
        }
        var codeText = codeEl ? codeEl.textContent : node.textContent;
        codeText = codeText.replace(/\n$/, '');
        return '\n\n```' + lang + '\n' + codeText + '\n```\n\n';
      }

      /* Blockquote */
      if (tag === 'blockquote') {
        var bqContent = inner().trim().replace(/\n/g, '\n> ');
        return '\n\n> ' + bqContent + '\n\n';
      }

      /* Anchor */
      if (tag === 'a') {
        var href = node.getAttribute('href') || '';
        var title = node.getAttribute('title') || '';
        var linkText = inner().trim() || href;
        var titlePart = title ? ' "' + title + '"' : '';
        if (refs) {
          var idx = refLinks.length + 1;
          refLinks.push('[' + idx + ']: ' + href + titlePart);
          return '[' + linkText + '][' + idx + ']';
        }
        return '[' + linkText + '](' + href + titlePart + ')';
      }

      /* Image */
      if (tag === 'img') {
        var src   = node.getAttribute('src')   || '';
        var alt   = node.getAttribute('alt')   || '';
        var imgTitle = node.getAttribute('title') || '';
        var imgTitlePart = imgTitle ? ' "' + imgTitle + '"' : '';
        if (refs) {
          var imgIdx = refLinks.length + 1;
          refLinks.push('[' + imgIdx + ']: ' + src + imgTitlePart);
          return '![' + alt + '][' + imgIdx + ']';
        }
        return '![' + alt + '](' + src + imgTitlePart + ')';
      }

      /* Lists */
      if (tag === 'ul' || tag === 'ol') {
        var newCtx = { listDepth: ctx.listDepth + 1, listType: tag, inPre: ctx.inPre };
        var listItems = children.filter(function (c) {
          return c.nodeType === 1 && c.tagName.toLowerCase() === 'li';
        });
        var counter = 0;
        var result = listItems.map(function (li) {
          counter++;
          var liChildren = Array.from(li.childNodes);
          var inlineContent = '';
          var nestedLists = '';
          liChildren.forEach(function (c) {
            var cTag = c.nodeType === 1 ? c.tagName.toLowerCase() : '';
            if (cTag === 'ul' || cTag === 'ol') {
              nestedLists += nodeToMd(c, { listDepth: newCtx.listDepth, listType: cTag, inPre: ctx.inPre });
            } else {
              inlineContent += nodeToMd(c, newCtx);
            }
          });
          inlineContent = inlineContent.trim();
          var indent = '';
          for (var d = 1; d < newCtx.listDepth; d++) indent += '  ';
          var bullet = tag === 'ul' ? '-' : counter + '.';
          var line = indent + bullet + ' ' + inlineContent;
          if (nestedLists) {
            var nestedLines = nestedLists.trim().split('\n').map(function (l) {
              return indent + '  ' + l;
            }).join('\n');
            line += '\n' + nestedLines;
          }
          return line;
        }).join('\n');
        return (ctx.listDepth === 0 ? '\n\n' : '') + result + (ctx.listDepth === 0 ? '\n\n' : '');
      }

      if (tag === 'li') {
        return inner();
      }

      /* Table (GFM) */
      if (tag === 'table') {
        if (!gfm) {
          return '\n\n' + inner().trim() + '\n\n';
        }
        var allRows = node.querySelectorAll('tr');
        var thead = node.querySelector('thead');
        var headerCells = [];
        var dataRows = [];
        allRows.forEach(function (tr) {
          var cells = Array.from(tr.querySelectorAll('th,td')).map(function (cell) {
            return Array.from(cell.childNodes).map(function (c) { return nodeToMd(c, ctx); }).join('').trim();
          });
          var isHeader = tr.querySelector('th') !== null || (thead && thead.contains(tr));
          if (isHeader && headerCells.length === 0) {
            headerCells = cells;
          } else {
            dataRows.push(cells);
          }
        });

        if (headerCells.length === 0 && dataRows.length > 0) {
          headerCells = dataRows.shift();
        }

        var colCount = headerCells.length;
        var widths = headerCells.map(function (h, i) {
          var max = h.length;
          dataRows.forEach(function (row) {
            var cell = row[i] || '';
            if (cell.length > max) max = cell.length;
          });
          return Math.max(max, 3);
        });

        function padCell(text, width) {
          while (text.length < width) text += ' ';
          return text;
        }

        var headerRow = '| ' + headerCells.map(function (h, i) { return padCell(h, widths[i]); }).join(' | ') + ' |';
        var sepRow = '| ' + widths.map(function (w) {
          var s = '-';
          while (s.length < w) s += '-';
          return s;
        }).join(' | ') + ' |';
        var bodyRows = dataRows.map(function (row) {
          var cells = [];
          for (var i = 0; i < colCount; i++) {
            cells.push(padCell(row[i] || '', widths[i]));
          }
          return '| ' + cells.join(' | ') + ' |';
        });

        return '\n\n' + [headerRow, sepRow].concat(bodyRows).join('\n') + '\n\n';
      }

      /* thead / tbody / tr / th / td */
      if (tag === 'thead' || tag === 'tbody' || tag === 'tfoot' || tag === 'tr' || tag === 'th' || tag === 'td') {
        return inner();
      }

      /* Block containers */
      if (/^(div|section|article|header|footer|main|nav|aside|figure|figcaption)$/.test(tag)) {
        var divContent = inner().trim();
        return divContent ? '\n\n' + divContent + '\n\n' : '';
      }

      /* Inline fallback */
      return inner();
    }

    var md = nodeToMd(body);

    if (refs && refLinks.length > 0) {
      md = md + '\n\n' + refLinks.join('\n');
    }

    md = md.replace(/\n{3,}/g, '\n\n');
    md = md.trim();

    return md;
  }

  /* ── UI wiring ── */
  var debounceTimer;
  function convert() {
    var html = input.value;
    charCount.textContent = html.length.toLocaleString() + ' 文字';
    if (!html.trim()) {
      output.textContent = '';
      lineCount.textContent = '';
      return;
    }
    var md = htmlToMarkdown(html, {
      gfm:  gfmToggle.checked,
      refs: refToggle.checked
    });
    output.textContent = md;
    var lines = md.split('\n').length;
    lineCount.textContent = lines + ' 行 · ' + md.length.toLocaleString() + ' 文字';
  }

  input.addEventListener('input', function () {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(convert, 150);
  });

  gfmToggle.addEventListener('change', convert);
  refToggle.addEventListener('change', convert);

  sampleBtn.addEventListener('click', function () {
    input.value = SAMPLE_HTML;
    convert();
  });

  clearBtn.addEventListener('click', function () {
    input.value = '';
    output.textContent = '';
    charCount.textContent = '0 文字';
    lineCount.textContent = '';
    copyStatus.textContent = '';
  });

  copyBtn.addEventListener('click', function () {
    var text = output.textContent;
    if (!text) return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function () {
        copyStatus.textContent = 'コピーしました！';
        copyStatus.className = 'hm-copy-notice';
        setTimeout(function () { copyStatus.textContent = ''; }, 2000);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      try { document.execCommand('copy'); } catch (e) {}
      document.body.removeChild(ta);
      copyStatus.textContent = 'コピーしました！';
      copyStatus.className = 'hm-copy-notice';
      setTimeout(function () { copyStatus.textContent = ''; }, 2000);
    }
  });

  convert();
}());
</script>

<div class="hm-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">開発チームの会計管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、SaaS利用料・開発ツールの経費管理もクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>
</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

## 関連ツール

> Html Beautifier → [Html Beautifierツール](/ja/tools/html-beautifier/)
> Html Entity Converter → [Html Entity Converterツール](/ja/tools/html-entity-converter/)
> Html Entity Encoder → [Html Entity Encoderツール](/ja/tools/html-entity-encoder/)

