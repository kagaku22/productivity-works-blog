---
title: "テキストリピーター — テキストを繰り返し・変換するオンラインツール"
description: "任意のテキストを指定回数繰り返し生成。区切り文字のカスタマイズも可能。無料テキストリピートツール。"
date: 2025-06-22
slug: "text-repeater"
categories: ["無料ツール"]
aliases: ["/ja/tools/text-repeater/", "/ja/tools/text-repeater/"]
cover:
  image: "/images/covers/text-repeater-ja.png"
  alt: "テキストリピーター"
ShowToc: false
---

<style>
#rep-app *,
#rep-app *::before,
#rep-app *::after {
  box-sizing: border-box;
}
#rep-app {
  font-family: system-ui, -apple-system, 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1e293b;
}
#rep-app h2 {
  font-size: 1.05rem;
  font-weight: 600;
  margin: 1.4rem 0 0.5rem;
  color: #0f766e;
}
#rep-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 500;
  margin-bottom: 0.3rem;
  color: #374151;
}
#rep-app textarea,
#rep-app input[type="text"],
#rep-app input[type="number"],
#rep-app select {
  width: 100%;
  padding: 0.55rem 0.75rem;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 0.95rem;
  background: #fff;
  color: #1e293b;
  transition: border-color 0.15s;
  outline: none;
}
#rep-app textarea:focus,
#rep-app input[type="text"]:focus,
#rep-app input[type="number"]:focus,
#rep-app select:focus {
  border-color: #0d9488;
  box-shadow: 0 0 0 3px rgba(13,148,136,.15);
}
#rep-app textarea {
  min-height: 110px;
  resize: vertical;
  font-family: inherit;
}
#rep-app .row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
#rep-app .row > .field {
  flex: 1;
  min-width: 160px;
}
#rep-app .field {
  margin-bottom: 0.85rem;
}
#rep-app .check-group {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem 1.2rem;
  margin-bottom: 0.85rem;
}
#rep-app .check-group label {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.9rem;
  font-weight: 400;
  cursor: pointer;
  color: #374151;
  margin: 0;
}
#rep-app input[type="checkbox"] {
  width: 16px;
  height: 16px;
  accent-color: #0d9488;
  cursor: pointer;
}
#rep-app .sep-custom {
  display: none;
  margin-top: 0.5rem;
}
#rep-app .sep-custom.visible {
  display: block;
}
#rep-app .btn-run {
  display: inline-block;
  background: #0d9488;
  color: #fff;
  border: none;
  border-radius: 7px;
  padding: 0.65rem 1.8rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  margin-top: 0.3rem;
}
#rep-app .btn-run:hover {
  background: #0f766e;
}
#rep-app .output-wrap {
  margin-top: 1.2rem;
}
#rep-app .output-meta {
  font-size: 0.82rem;
  color: #64748b;
  margin-bottom: 0.4rem;
}
#rep-app .output-box {
  position: relative;
}
#rep-app #rep-output {
  width: 100%;
  min-height: 140px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  padding: 0.65rem 0.75rem;
  font-size: 0.9rem;
  background: #f8fafc;
  color: #1e293b;
  resize: vertical;
  font-family: inherit;
}
#rep-app .btn-copy {
  display: inline-block;
  margin-top: 0.55rem;
  background: #fff;
  color: #0d9488;
  border: 1.5px solid #0d9488;
  border-radius: 6px;
  padding: 0.45rem 1.2rem;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#rep-app .btn-copy:hover {
  background: #0d9488;
  color: #fff;
}
#rep-app .copy-feedback {
  display: inline-block;
  margin-left: 0.7rem;
  font-size: 0.82rem;
  color: #0d9488;
  opacity: 0;
  transition: opacity 0.3s;
}
#rep-app .copy-feedback.show {
  opacity: 1;
}
#rep-app .divider {
  border: none;
  border-top: 1px solid #e2e8f0;
  margin: 1.1rem 0;
}
#rep-app .error {
  color: #dc2626;
  font-size: 0.85rem;
  margin-top: 0.25rem;
}
#rep-app .freee-cta {
  margin-top: 2rem;
  padding: 1.1rem 1.3rem;
  background: #f0fdfa;
  border: 1.5px solid #99f6e4;
  border-radius: 10px;
  font-size: 0.9rem;
  color: #134e4a;
  line-height: 1.6;
}
#rep-app .freee-cta strong {
  display: block;
  font-size: 1rem;
  margin-bottom: 0.4rem;
  color: #0f766e;
}
#rep-app .freee-cta a {
  color: #0d9488;
  font-weight: 600;
  text-decoration: underline;
}
</style>

<div id="rep-app">

<div class="field">
  <label for="rep-input">入力テキスト</label>
  <textarea id="rep-input" placeholder="ここにテキストを入力または貼り付けてください…"></textarea>
</div>

<div class="row">
  <div class="field">
    <label for="rep-count">繰り返し回数（1〜10000）</label>
    <input type="number" id="rep-count" value="3" min="1" max="10000">
    <div class="error" id="rep-count-err"></div>
  </div>
  <div class="field">
    <label for="rep-sep">区切り文字</label>
    <select id="rep-sep">
      <option value="newline">改行</option>
      <option value="space">スペース</option>
      <option value="comma">カンマ</option>
      <option value="custom">カスタム…</option>
    </select>
    <div class="sep-custom" id="rep-sep-custom-wrap">
      <input type="text" id="rep-sep-custom" placeholder="区切り文字を入力">
    </div>
  </div>
</div>

<div class="row">
  <div class="field">
    <label for="rep-prefix">プレフィックス（各繰り返しの前）</label>
    <input type="text" id="rep-prefix" placeholder="例：- ">
  </div>
  <div class="field">
    <label for="rep-suffix">サフィックス（各繰り返しの後）</label>
    <input type="text" id="rep-suffix" placeholder="例：；">
  </div>
</div>

<h2>変換オプション</h2>
<div class="check-group">
  <label><input type="checkbox" id="rep-numbered"> 番号付きモード（1. テキスト、2. テキスト…）</label>
  <label><input type="checkbox" id="rep-reverse"> テキストを逆順にする</label>
  <label><input type="checkbox" id="rep-shuffle"> 行をシャッフル</label>
  <label><input type="checkbox" id="rep-sort-az"> 昇順ソート（A→Z）</label>
  <label><input type="checkbox" id="rep-sort-za"> 降順ソート（Z→A）</label>
  <label><input type="checkbox" id="rep-dedup"> 重複行を削除</label>
</div>

<button class="btn-run" id="rep-run">生成する</button>

<hr class="divider">

<div class="output-wrap">
  <div class="output-meta" id="rep-meta"></div>
  <div class="output-box">
    <textarea id="rep-output" readonly placeholder="出力結果がここに表示されます…"></textarea>
  </div>
  <button class="btn-copy" id="rep-copy">クリップボードにコピー</button>
  <span class="copy-feedback" id="rep-copy-fb">コピーしました！</span>
</div>

<div class="freee-cta">
  <strong>業務効率化をもっと加速させたいなら</strong>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計・freee人事労務</a> なら、請求書・給与計算・確定申告をまとめてクラウドで自動化。手作業を減らして本来の業務に集中しましょう。<br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す →</a>
</div>

</div>

<script>
(function () {
  var sepEl      = document.getElementById('rep-sep');
  var sepCustomW = document.getElementById('rep-sep-custom-wrap');
  var sepCustom  = document.getElementById('rep-sep-custom');
  var inputEl    = document.getElementById('rep-input');
  var countEl    = document.getElementById('rep-count');
  var countErr   = document.getElementById('rep-count-err');
  var prefixEl   = document.getElementById('rep-prefix');
  var suffixEl   = document.getElementById('rep-suffix');
  var numberedEl = document.getElementById('rep-numbered');
  var reverseEl  = document.getElementById('rep-reverse');
  var shuffleEl  = document.getElementById('rep-shuffle');
  var sortAZEl   = document.getElementById('rep-sort-az');
  var sortZAEl   = document.getElementById('rep-sort-za');
  var dedupEl    = document.getElementById('rep-dedup');
  var runBtn     = document.getElementById('rep-run');
  var outputEl   = document.getElementById('rep-output');
  var metaEl     = document.getElementById('rep-meta');
  var copyBtn    = document.getElementById('rep-copy');
  var copyFb     = document.getElementById('rep-copy-fb');

  sepEl.addEventListener('change', function () {
    if (sepEl.value === 'custom') {
      sepCustomW.classList.add('visible');
    } else {
      sepCustomW.classList.remove('visible');
    }
  });

  sortAZEl.addEventListener('change', function () { if (this.checked) sortZAEl.checked = false; });
  sortZAEl.addEventListener('change', function () { if (this.checked) sortAZEl.checked = false; });

  function getSeparator() {
    switch (sepEl.value) {
      case 'newline': return '\n';
      case 'space':   return ' ';
      case 'comma':   return '、';
      case 'custom':  return sepCustom.value;
      default:        return '\n';
    }
  }

  function shuffleArray(arr) {
    for (var i = arr.length - 1; i > 0; i--) {
      var j = Math.floor(Math.random() * (i + 1));
      var tmp = arr[i]; arr[i] = arr[j]; arr[j] = tmp;
    }
    return arr;
  }

  runBtn.addEventListener('click', function () {
    countErr.textContent = '';
    var text = inputEl.value;
    var count = parseInt(countEl.value, 10);

    if (!text) { outputEl.value = ''; metaEl.textContent = ''; return; }
    if (isNaN(count) || count < 1 || count > 10000) {
      countErr.textContent = '1〜10000の数値を入力してください。';
      return;
    }

    var prefix = prefixEl.value;
    var suffix = suffixEl.value;
    var sep = getSeparator();
    var numbered = numberedEl.checked;
    var reverse  = reverseEl.checked;
    var shuffle  = shuffleEl.checked;
    var sortAZ   = sortAZEl.checked;
    var sortZA   = sortZAEl.checked;
    var dedup    = dedupEl.checked;

    var baseText = reverse ? text.split('').reverse().join('') : text;

    var items = [];
    for (var i = 0; i < count; i++) {
      var line = prefix + baseText + suffix;
      if (numbered) line = (i + 1) + '. ' + line;
      items.push(line);
    }

    if (dedup) {
      var seen = {};
      items = items.filter(function (l) {
        if (seen[l]) return false;
        seen[l] = true;
        return true;
      });
    }

    if (shuffle) {
      shuffleArray(items);
    } else if (sortAZ) {
      items.sort(function (a, b) { return a.localeCompare(b, 'ja'); });
    } else if (sortZA) {
      items.sort(function (a, b) { return b.localeCompare(a, 'ja'); });
    }

    var result = items.join(sep);
    outputEl.value = result;

    var charCount = result.length;
    var lineCount = items.length;
    metaEl.textContent = lineCount + '回繰り返し · ' + charCount.toLocaleString('ja-JP') + '文字';
  });

  copyBtn.addEventListener('click', function () {
    if (!outputEl.value) return;
    navigator.clipboard.writeText(outputEl.value).then(function () {
      copyFb.classList.add('show');
      setTimeout(function () { copyFb.classList.remove('show'); }, 1800);
    }).catch(function () {
      outputEl.select();
      document.execCommand('copy');
      copyFb.classList.add('show');
      setTimeout(function () { copyFb.classList.remove('show'); }, 1800);
    });
  });
})();
</script>
