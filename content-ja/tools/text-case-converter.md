---
title: "テキスト変換ツール"
date: 2025-05-16
description: "無料のテキスト変換ツール。大文字・小文字・タイトルケース・camelCase・snake_case・kebab-caseなど12種類の変換を即実行。"
categories: ["無料ツール"]
slug: "text-case-converter"
ShowToc: false
cover:
  image: "/images/covers/text-case-converter-ja.png"
  alt: "テキスト変換ツール"
---

<div id="tc-app">

<style>
#tc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1e293b;
}
#tc-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  color: #334155;
  margin: 0 0 10px 0;
}
#tc-app label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  margin-bottom: 5px;
}
#tc-app textarea {
  width: 100%;
  box-sizing: border-box;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  padding: 12px 14px;
  font-size: 14px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  color: #1e293b;
  background: #f8fafc;
  resize: vertical;
  transition: border-color 0.2s;
  line-height: 1.6;
}
#tc-app textarea:focus {
  outline: none;
  border-color: #64748b;
  background: #fff;
}
#tc-app .tc-stats {
  font-size: 12px;
  color: #94a3b8;
  margin-top: 5px;
  text-align: right;
}
#tc-app .tc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 8px;
  margin: 16px 0;
}
#tc-app .tc-btn {
  background: #f1f5f9;
  border: 1.5px solid #e2e8f0;
  border-radius: 7px;
  padding: 9px 12px;
  font-size: 13px;
  font-weight: 600;
  color: #334155;
  cursor: pointer;
  text-align: left;
  transition: background 0.15s, border-color 0.15s, color 0.15s;
  line-height: 1.4;
}
#tc-app .tc-btn:hover {
  background: #475569;
  border-color: #475569;
  color: #fff;
}
#tc-app .tc-btn .tc-btn-sub {
  display: block;
  font-size: 11px;
  font-weight: 400;
  opacity: 0.7;
  margin-top: 2px;
}
#tc-app .tc-output-section {
  margin-top: 20px;
}
#tc-app .tc-output-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 6px;
}
#tc-app .tc-copy-btn {
  background: #475569;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 6px 14px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#tc-app .tc-copy-btn:hover {
  background: #334155;
}
#tc-app .tc-copy-btn.copied {
  background: #16a34a;
}
#tc-app .tc-label-tag {
  display: inline-block;
  background: #e2e8f0;
  color: #475569;
  border-radius: 5px;
  padding: 2px 9px;
  font-size: 11px;
  font-weight: 700;
  margin-left: 8px;
  vertical-align: middle;
}
#tc-app .tc-divider {
  border: none;
  border-top: 1.5px solid #e2e8f0;
  margin: 22px 0;
}
@media (max-width: 520px) {
  #tc-app .tc-grid {
    grid-template-columns: 1fr 1fr;
  }
}
</style>

<h2>入力テキスト</h2>
<label for="tc-input">変換したいテキストを入力してください</label>
<textarea id="tc-input" rows="6" placeholder="ここにテキストを入力または貼り付けてください..."></textarea>
<div class="tc-stats" id="tc-input-stats">文字数: 0 &nbsp;|&nbsp; 単語数: 0</div>

<div class="tc-grid" id="tc-buttons">
  <button class="tc-btn" onclick="tcConvert('upper')">大文字 (UPPER CASE)<span class="tc-btn-sub">HELLO WORLD</span></button>
  <button class="tc-btn" onclick="tcConvert('lower')">小文字 (lower case)<span class="tc-btn-sub">hello world</span></button>
  <button class="tc-btn" onclick="tcConvert('title')">タイトルケース<span class="tc-btn-sub">Hello World</span></button>
  <button class="tc-btn" onclick="tcConvert('sentence')">文頭大文字<span class="tc-btn-sub">Hello world</span></button>
  <button class="tc-btn" onclick="tcConvert('camel')">camelCase<span class="tc-btn-sub">helloWorld</span></button>
  <button class="tc-btn" onclick="tcConvert('pascal')">PascalCase<span class="tc-btn-sub">HelloWorld</span></button>
  <button class="tc-btn" onclick="tcConvert('snake')">snake_case<span class="tc-btn-sub">hello_world</span></button>
  <button class="tc-btn" onclick="tcConvert('screaming')">SCREAMING_SNAKE<span class="tc-btn-sub">HELLO_WORLD</span></button>
  <button class="tc-btn" onclick="tcConvert('kebab')">kebab-case<span class="tc-btn-sub">hello-world</span></button>
  <button class="tc-btn" onclick="tcConvert('train')">Train-Case<span class="tc-btn-sub">Hello-World</span></button>
  <button class="tc-btn" onclick="tcConvert('dot')">dot.case<span class="tc-btn-sub">hello.world</span></button>
  <button class="tc-btn" onclick="tcConvert('alternate')">交互大文字<span class="tc-btn-sub">hElLo WoRlD</span></button>
</div>

<div class="tc-output-section">
  <div class="tc-output-header">
    <div>
      <label for="tc-output" style="margin:0;display:inline;">変換結果</label>
      <span class="tc-label-tag" id="tc-mode-tag">—</span>
    </div>
    <button class="tc-copy-btn" id="tc-copy-btn" onclick="tcCopy()">コピー</button>
  </div>
  <textarea id="tc-output" rows="6" readonly placeholder="変換後のテキストがここに表示されます..."></textarea>
  <div class="tc-stats" id="tc-output-stats">文字数: 0 &nbsp;|&nbsp; 単語数: 0</div>
</div>

<script>
(function() {
  var inputEl = document.getElementById('tc-input');
  var outputEl = document.getElementById('tc-output');
  var inputStats = document.getElementById('tc-input-stats');
  var outputStats = document.getElementById('tc-output-stats');
  var modeTag = document.getElementById('tc-mode-tag');
  var copyBtn = document.getElementById('tc-copy-btn');

  var modeNames = {
    upper: '大文字 (UPPER CASE)',
    lower: '小文字 (lower case)',
    title: 'タイトルケース',
    sentence: '文頭大文字',
    camel: 'camelCase',
    pascal: 'PascalCase',
    snake: 'snake_case',
    screaming: 'SCREAMING_SNAKE_CASE',
    kebab: 'kebab-case',
    train: 'Train-Case',
    dot: 'dot.case',
    alternate: '交互大文字'
  };

  function countStats(text) {
    var chars = text.length;
    var words = text.trim() === '' ? 0 : text.trim().split(/\s+/).length;
    return '文字数: ' + chars + ' &nbsp;|&nbsp; 単語数: ' + words;
  }

  function tokenize(text) {
    return text
      .replace(/([a-z])([A-Z])/g, '$1 $2')
      .replace(/([A-Z]+)([A-Z][a-z])/g, '$1 $2')
      .replace(/[-_\.]+/g, ' ')
      .toLowerCase()
      .trim()
      .split(/\s+/)
      .filter(function(w) { return w.length > 0; });
  }

  function convertText(text, mode) {
    if (!text) return '';
    switch (mode) {
      case 'upper':
        return text.toUpperCase();
      case 'lower':
        return text.toLowerCase();
      case 'title':
        return text.replace(/\S+/g, function(w) {
          return w.charAt(0).toUpperCase() + w.slice(1).toLowerCase();
        });
      case 'sentence':
        return text.toLowerCase().replace(/(^\s*\w|[.!?]\s+\w)/g, function(c) {
          return c.toUpperCase();
        });
      case 'camel': {
        var words = tokenize(text);
        if (words.length === 0) return '';
        return words[0] + words.slice(1).map(function(w) {
          return w.charAt(0).toUpperCase() + w.slice(1);
        }).join('');
      }
      case 'pascal': {
        var words = tokenize(text);
        return words.map(function(w) {
          return w.charAt(0).toUpperCase() + w.slice(1);
        }).join('');
      }
      case 'snake': {
        return tokenize(text).join('_');
      }
      case 'screaming': {
        return tokenize(text).join('_').toUpperCase();
      }
      case 'kebab': {
        return tokenize(text).join('-');
      }
      case 'train': {
        var words = tokenize(text);
        return words.map(function(w) {
          return w.charAt(0).toUpperCase() + w.slice(1);
        }).join('-');
      }
      case 'dot': {
        return tokenize(text).join('.');
      }
      case 'alternate': {
        var chars = text.split('');
        var upper = true;
        return chars.map(function(c) {
          if (c.trim() === '') { return c; }
          var result = upper ? c.toUpperCase() : c.toLowerCase();
          upper = !upper;
          return result;
        }).join('');
      }
      default:
        return text;
    }
  }

  inputEl.addEventListener('input', function() {
    inputStats.innerHTML = countStats(inputEl.value);
  });

  window.tcConvert = function(mode) {
    var input = inputEl.value;
    var result = convertText(input, mode);
    outputEl.value = result;
    modeTag.textContent = modeNames[mode] || mode;
    outputStats.innerHTML = countStats(result);
    copyBtn.textContent = 'コピー';
    copyBtn.classList.remove('copied');
  };

  window.tcCopy = function() {
    var text = outputEl.value;
    if (!text) return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() {
        copyBtn.textContent = 'コピー済み!';
        copyBtn.classList.add('copied');
        setTimeout(function() {
          copyBtn.textContent = 'コピー';
          copyBtn.classList.remove('copied');
        }, 2000);
      });
    } else {
      outputEl.select();
      document.execCommand('copy');
      copyBtn.textContent = 'コピー済み!';
      copyBtn.classList.add('copied');
      setTimeout(function() {
        copyBtn.textContent = 'コピー';
        copyBtn.classList.remove('copied');
      }, 2000);
    }
  };
})();
</script>

</div>

<hr style="border:none;border-top:1.5px solid #e2e8f0;margin:28px 0;">

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<hr style="border:none;border-top:1.5px solid #e2e8f0;margin:28px 0;">

> 単語の出現頻度を分析 → [単語頻度カウンター](/ja/tools/word-frequency-counter/)
> テキストの差分を確認 → [テキスト差分比較ツール](/ja/tools/text-diff-checker/)
> 文字列をエンコード → [万能エンコーダー・デコーダー](/ja/tools/encoder-decoder/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
