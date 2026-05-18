---
title: "数字→漢数字変換ツール｜大字・金額表記も対応【無料】"
date: 2025-12-08
draft: false
slug: "number-to-words"
aliases:
  - "/ja/tools/number-base-converter/"
  - "/ja/tools/number-to-words/"
description: "数字を漢数字・大字（壱弐参）に一発変換。金額モードでは「金壱万弐千参百四拾五円也」形式に対応。小切手・領収書・契約書の記入に便利な無料ツール。"
categories: ["無料ツール"]
tags: ["漢数字", "大字", "数字変換", "金額表記", "小切手", "経理"]
author: "Productivity Works編集部"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/number-to-words-ja.png"
  alt: "数字→漢数字変換ツール"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 数字→漢数字変換ツール｜大字・金額表記も対応【無料】

数字を漢数字または大字（壱弐参…）に瞬時に変換する無料ツールです。小切手・手形・領収書・契約書など、改ざん防止のために大字表記が必要な場面でそのままコピペしてお使いいただけます。

<style>
#n2w-app * { box-sizing: border-box; }
#n2w-app {
  font-family: system-ui, -apple-system, 'Hiragino Sans', 'Yu Gothic', sans-serif;
  max-width: 680px;
  margin: 2rem auto;
  color: #1e1b4b;
}
#n2w-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 1rem;
  color: #1e1b4b;
}
#n2w-app .n2w-modes {
  display: flex;
  gap: 6px;
  margin-bottom: 1.25rem;
  flex-wrap: wrap;
}
#n2w-app .n2w-mode-btn {
  padding: 7px 16px;
  border: 2px solid #4f46e5;
  border-radius: 999px;
  background: #fff;
  color: #4f46e5;
  font-size: 0.85rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#n2w-app .n2w-mode-btn.active {
  background: #4f46e5;
  color: #fff;
}
#n2w-app .n2w-mode-btn:hover:not(.active) {
  background: #ede9fe;
}
#n2w-app .n2w-input-row {
  display: flex;
  gap: 10px;
  align-items: center;
  margin-bottom: 1.25rem;
}
#n2w-app .n2w-prefix {
  font-size: 1.4rem;
  font-weight: 700;
  color: #4f46e5;
  min-width: 20px;
  text-align: right;
}
#n2w-app .n2w-input {
  flex: 1;
  padding: 12px 16px;
  border: 2px solid #c7d2fe;
  border-radius: 10px;
  font-size: 1.3rem;
  font-weight: 600;
  color: #1e1b4b;
  outline: none;
  transition: border-color 0.15s;
  -moz-appearance: textfield;
}
#n2w-app .n2w-input:focus {
  border-color: #4f46e5;
}
#n2w-app .n2w-input::-webkit-inner-spin-button,
#n2w-app .n2w-input::-webkit-outer-spin-button {
  -webkit-appearance: none;
}
#n2w-app .n2w-result-box {
  background: #f5f3ff;
  border: 2px solid #c7d2fe;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  min-height: 70px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  margin-bottom: 1rem;
}
#n2w-app .n2w-result-text {
  font-size: 1.15rem;
  font-weight: 700;
  color: #3730a3;
  line-height: 1.6;
  flex: 1;
  word-break: break-all;
}
#n2w-app .n2w-result-text.placeholder {
  color: #a5b4fc;
  font-weight: 400;
  font-style: italic;
  font-size: 0.95rem;
}
#n2w-app .n2w-copy-btn {
  flex-shrink: 0;
  padding: 8px 16px;
  background: #4f46e5;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 0.85rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
#n2w-app .n2w-copy-btn:hover {
  background: #4338ca;
}
#n2w-app .n2w-copy-btn:active {
  transform: scale(0.96);
}
#n2w-app .n2w-copy-btn.copied {
  background: #059669;
}
#n2w-app .n2w-hint {
  font-size: 0.78rem;
  color: #6b7280;
  margin-bottom: 0.5rem;
}
#n2w-app .n2w-error {
  color: #dc2626;
  font-size: 0.85rem;
  margin-top: -0.75rem;
  margin-bottom: 0.75rem;
  min-height: 1.2em;
}
#n2w-app .n2w-examples {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 1rem;
}
#n2w-app .n2w-example-chip {
  padding: 4px 12px;
  background: #ede9fe;
  color: #4f46e5;
  border-radius: 999px;
  font-size: 0.8rem;
  font-weight: 700;
  cursor: pointer;
  border: none;
  transition: background 0.15s;
}
#n2w-app .n2w-example-chip:hover {
  background: #c7d2fe;
}
</style>

<div id="n2w-app">
  <h2>数字→漢数字変換ツール</h2>

  <div class="n2w-modes">
    <button class="n2w-mode-btn active" data-mode="kanji" onclick="n2wSetMode('kanji')">漢数字</button>
    <button class="n2w-mode-btn" data-mode="daiji" onclick="n2wSetMode('daiji')">大字</button>
    <button class="n2w-mode-btn" data-mode="kinmaku" onclick="n2wSetMode('kinmaku')">金額（¥）</button>
  </div>

  <div class="n2w-input-row">
    <span class="n2w-prefix" id="n2w-prefix"></span>
    <input
      class="n2w-input"
      id="n2w-input"
      type="number"
      inputmode="numeric"
      placeholder="数字を入力…"
      oninput="n2wConvert()"
    />
  </div>

  <div class="n2w-error" id="n2w-error"></div>

  <div class="n2w-result-box">
    <span class="n2w-result-text placeholder" id="n2w-result">変換結果がここに表示されます</span>
    <button class="n2w-copy-btn" id="n2w-copy-btn" onclick="n2wCopy()" style="display:none">コピー</button>
  </div>

  <div class="n2w-hint" id="n2w-hint">整数のみ対応。最大9,999兆（9,999,999,999,999,999）まで。</div>

  <div class="n2w-examples">
    <span style="font-size:0.78rem;color:#6b7280;align-self:center;">例：</span>
    <button class="n2w-example-chip" onclick="n2wSetExample('1234')">1,234</button>
    <button class="n2w-example-chip" onclick="n2wSetExample('10000')">1万</button>
    <button class="n2w-example-chip" onclick="n2wSetExample('123456')">123,456</button>
    <button class="n2w-example-chip" onclick="n2wSetExample('1000000')">100万</button>
    <button class="n2w-example-chip" onclick="n2wSetExample('100000000')">1億</button>
    <button class="n2w-example-chip" onclick="n2wSetExample('1000000000000')">1兆</button>
  </div>
</div>

<script>
(function() {
  var _mode = 'kanji';

  // 漢数字 digits and units
  var kanjiDigits = ['〇', '一', '二', '三', '四', '五', '六', '七', '八', '九'];
  var kanjiUnits4 = ['', '万', '億', '兆'];
  var kanjiUnits = ['', '十', '百', '千'];

  // 大字
  var daijiDigits = ['零', '壱', '弐', '参', '四', '伍', '六', '七', '八', '九'];
  var daijiUnits = ['', '拾', '百', '千'];
  var daijiUnits4 = ['', '万', '億', '兆'];

  function chunk4ToKanji(n, digits, units, units4, omitOne) {
    // n is 0..9999, returns kanji string (no unit above 千 here)
    if (n === 0) return '';
    var result = '';
    var d3 = Math.floor(n / 1000);
    var d2 = Math.floor((n % 1000) / 100);
    var d1 = Math.floor((n % 100) / 10);
    var d0 = n % 10;
    if (d3 > 0) {
      // omit "一" before 千 in standard kanji, keep in daiji
      result += (omitOne && d3 === 1 ? '' : digits[d3]) + units[3];
    }
    if (d2 > 0) {
      result += (omitOne && d2 === 1 ? '' : digits[d2]) + units[2];
    }
    if (d1 > 0) {
      result += (omitOne && d1 === 1 ? '' : digits[d1]) + units[1];
    }
    if (d0 > 0) {
      result += digits[d0];
    }
    return result;
  }

  function toKanji(n, digits, units, units4, omitOne) {
    if (n === 0) return '零';
    var neg = n < 0;
    var abs = Math.abs(n);
    if (abs > 9999999999999999) return null;

    // Split into groups of 4 from right: [兆, 億, 万, ones]
    var t = Math.floor(abs / 1000000000000);
    var rem = abs % 1000000000000;
    var ok = Math.floor(rem / 100000000);
    rem = rem % 100000000;
    var man = Math.floor(rem / 10000);
    var sen = rem % 10000;

    var parts = [];
    if (t > 0) {
      // For 兆 group: omitOne if the group value is exactly 1 (i.e. 一兆)
      var s = chunk4ToKanji(t, digits, units, units4, omitOne);
      parts.push(s + units4[3]);
    }
    if (ok > 0) {
      var s = chunk4ToKanji(ok, digits, units, units4, omitOne);
      parts.push(s + units4[2]);
    }
    if (man > 0) {
      var s = chunk4ToKanji(man, digits, units, units4, omitOne);
      parts.push(s + units4[1]);
    }
    if (sen > 0) {
      parts.push(chunk4ToKanji(sen, digits, units, units4, omitOne));
    }

    var result = parts.join('');
    return neg ? '負' + result : result;
  }

  function toKanjiStandard(n) {
    return toKanji(n, kanjiDigits, kanjiUnits, kanjiUnits4, true);
  }

  function toDaiji(n) {
    return toKanji(n, daijiDigits, daijiUnits, daijiUnits4, false);
  }

  function toKinmaku(n) {
    // 金額モード: 金[大字]円也
    // Supports integers only
    if (n === 0) return '金零円也';
    var neg = n < 0;
    var abs = Math.abs(n);
    var words = toDaiji(abs);
    if (!words) return null;
    // Replace 万 with 万, insert 拾 for tens in daiji properly — toDaiji already handles this.
    // Add 金...円也 wrapper
    var result = '金' + words + '円也';
    return neg ? '（マイナス）' + result : result;
  }

  window.n2wSetMode = function(mode) {
    _mode = mode;
    document.querySelectorAll('#n2w-app .n2w-mode-btn').forEach(function(b) {
      b.classList.toggle('active', b.dataset.mode === mode);
    });
    var prefix = document.getElementById('n2w-prefix');
    prefix.textContent = mode === 'kinmaku' ? '¥' : '';
    var hint = document.getElementById('n2w-hint');
    if (mode === 'kanji') {
      hint.textContent = '漢数字（一二三…）に変換。整数のみ、最大9,999兆まで。';
    } else if (mode === 'daiji') {
      hint.textContent = '大字（壱弐参…）に変換。公式文書・契約書向け。整数のみ。';
    } else {
      hint.textContent = '金額の大字表記（金壱万弐千参百四拾五円也）に変換。小切手・領収書向け。';
    }
    n2wConvert();
  };

  window.n2wSetExample = function(val) {
    document.getElementById('n2w-input').value = val;
    n2wConvert();
  };

  window.n2wConvert = function() {
    var raw = document.getElementById('n2w-input').value.trim();
    var resultEl = document.getElementById('n2w-result');
    var errorEl = document.getElementById('n2w-error');
    var copyBtn = document.getElementById('n2w-copy-btn');

    errorEl.textContent = '';

    if (raw === '' || raw === '-') {
      resultEl.textContent = '変換結果がここに表示されます';
      resultEl.classList.add('placeholder');
      copyBtn.style.display = 'none';
      return;
    }

    if (raw.indexOf('.') !== -1) {
      errorEl.textContent = '整数のみ対応しています。小数は入力できません。';
      resultEl.textContent = '変換結果がここに表示されます';
      resultEl.classList.add('placeholder');
      copyBtn.style.display = 'none';
      return;
    }

    var num = parseInt(raw, 10);
    if (isNaN(num)) {
      errorEl.textContent = '有効な数字を入力してください。';
      resultEl.textContent = '変換結果がここに表示されます';
      resultEl.classList.add('placeholder');
      copyBtn.style.display = 'none';
      return;
    }

    if (Math.abs(num) > 9999999999999999) {
      errorEl.textContent = '数が大きすぎます。最大 9,999兆（9,999,999,999,999,999）まで対応しています。';
      resultEl.textContent = '変換結果がここに表示されます';
      resultEl.classList.add('placeholder');
      copyBtn.style.display = 'none';
      return;
    }

    var result;
    if (_mode === 'kanji') {
      result = toKanjiStandard(num);
    } else if (_mode === 'daiji') {
      result = toDaiji(num);
    } else {
      result = toKinmaku(num);
    }

    if (!result) {
      errorEl.textContent = '変換できませんでした。入力を確認してください。';
      resultEl.textContent = '変換結果がここに表示されます';
      resultEl.classList.add('placeholder');
      copyBtn.style.display = 'none';
      return;
    }

    resultEl.textContent = result;
    resultEl.classList.remove('placeholder');
    copyBtn.style.display = 'inline-block';
    copyBtn.textContent = 'コピー';
    copyBtn.classList.remove('copied');
  };

  window.n2wCopy = function() {
    var text = document.getElementById('n2w-result').textContent;
    var btn = document.getElementById('n2w-copy-btn');
    if (!text || text === '変換結果がここに表示されます') return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() {
        btn.textContent = 'コピー完了!';
        btn.classList.add('copied');
        setTimeout(function() {
          btn.textContent = 'コピー';
          btn.classList.remove('copied');
        }, 2000);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      try { document.execCommand('copy'); } catch(e) {}
      document.body.removeChild(ta);
      btn.textContent = 'コピー完了!';
      btn.classList.add('copied');
      setTimeout(function() {
        btn.textContent = 'コピー';
        btn.classList.remove('copied');
      }, 2000);
    }
  };
})();
</script>

## 使い方

1. **モードを選択** — 漢数字 / 大字 / 金額（¥）の3種類
2. **数字を入力**するだけで即座に変換
3. **コピーボタン**で結果をクリップボードへ

## 3つのモードの違い

| モード | 入力 | 出力 |
|--------|------|------|
| 漢数字 | 12345 | 一万二千三百四十五 |
| 大字 | 12345 | 壱万弐千参百四拾伍 |
| 金額（¥） | 12345 | 金壱万弐千参百四拾伍円也 |

## 漢数字と大字の違い

**漢数字**は日常的な文書で使われる一般的な表記（一・二・三…）です。一方、**大字（だいじ）**は小切手・手形・領収書など公式文書で改ざん防止のために用いられる旧字体（壱・弐・参…）です。

日本の法律・商業実務では、金融機関への提出書類や会社の重要契約書において大字表記が慣習的に（あるいは義務として）求められる場合があります。

## よくある使用場面

- **小切手・手形の記入**（金額の大字表記）
- **領収書・請求書**（正式な金額表記）
- **不動産・金融契約書**（重要金額の改ざん防止）
- **遺言書・贈与契約書**などの法的文書
- **寄付金・祝儀袋**への金額記入

---

**請求書・領収書の漢数字変換に便利。経理業務の効率化にはfreee**

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
