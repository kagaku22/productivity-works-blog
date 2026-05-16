---
title: "文字数カウンター｜文字数・単語数・行数をリアルタイム表示【無料】"
date: 2025-05-16
description: "無料の文字数カウントツール。文字数（スペース含む/除く）・単語数・文数・段落数をリアルタイム計算。X(280文字)・SMS(70文字)等の制限チェック付き。"
categories: ["無料ツール"]
tags: ["文字数カウンター", "文字数チェック", "Twitter文字数", "SMS文字数", "UTF-8バイト数", "テキスト分析"]
slug: "character-counter"
cover:
  image: "/images/covers/character-counter-ja.png"
  alt: "文字数カウンター"
ShowToc: false
---

<div id="cc-app">

<style>
#cc-app {
  font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 880px;
  margin: 0 auto;
  color: #1e1b4b;
}

#cc-app * {
  box-sizing: border-box;
}

#cc-textarea {
  width: 100%;
  min-height: 200px;
  padding: 16px;
  font-size: 1rem;
  line-height: 1.7;
  border: 2px solid #c4b5fd;
  border-radius: 10px;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  background: #faf5ff;
  color: #1e1b4b;
  font-family: inherit;
}
#cc-textarea:focus {
  border-color: #7c3aed;
  background: #fff;
  box-shadow: 0 0 0 3px rgba(124,58,237,0.1);
}
#cc-textarea::placeholder { color: #a78bfa; }

#cc-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 10px;
}
#cc-app button {
  padding: 7px 14px;
  border: none;
  border-radius: 6px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  font-family: inherit;
}
#cc-app button:active { transform: scale(0.97); }

.cc-btn-primary { background: #7c3aed; color: #fff; }
.cc-btn-primary:hover { background: #6d28d9; }
.cc-btn-secondary { background: #ede9fe; color: #5b21b6; }
.cc-btn-secondary:hover { background: #ddd6fe; }
.cc-btn-danger { background: #fee2e2; color: #b91c1c; }
.cc-btn-danger:hover { background: #fecaca; }

/* カスタム制限入力 */
#cc-limit-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 12px;
  flex-wrap: wrap;
}
#cc-limit-row label {
  font-size: 0.85rem;
  color: #5b21b6;
  font-weight: 600;
  white-space: nowrap;
}
#cc-limit-input {
  width: 100px;
  padding: 6px 10px;
  border: 2px solid #c4b5fd;
  border-radius: 6px;
  font-size: 0.85rem;
  color: #1e1b4b;
  outline: none;
  font-family: inherit;
}
#cc-limit-input:focus { border-color: #7c3aed; }

/* カスタム制限プログレス */
#cc-custom-progress-wrap {
  margin-top: 8px;
  display: none;
}
#cc-custom-progress-label {
  font-size: 0.8rem;
  color: #5b21b6;
  margin-bottom: 4px;
  display: flex;
  justify-content: space-between;
}
#cc-custom-progress-bg {
  width: 100%;
  height: 10px;
  background: #ede9fe;
  border-radius: 999px;
  overflow: hidden;
}
#cc-custom-progress-bar {
  height: 100%;
  background: #7c3aed;
  border-radius: 999px;
  transition: width 0.2s, background 0.2s;
  width: 0%;
}
#cc-custom-progress-bar.warn { background: #f59e0b; }
#cc-custom-progress-bar.over { background: #ef4444; }

/* 統計グリッド */
#cc-stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(138px, 1fr));
  gap: 12px;
  margin-top: 20px;
}
.cc-stat-card {
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  border-radius: 10px;
  padding: 14px 10px;
  text-align: center;
}
.cc-stat-value {
  font-size: 1.7rem;
  font-weight: 700;
  color: #7c3aed;
  line-height: 1;
  word-break: break-all;
}
.cc-stat-label {
  font-size: 0.72rem;
  color: #6b7280;
  margin-top: 6px;
  letter-spacing: 0.02em;
}

/* プラットフォーム制限バー */
#cc-platform-section {
  margin-top: 28px;
}
#cc-platform-section h3 {
  font-size: 0.9rem;
  font-weight: 700;
  color: #5b21b6;
  margin: 0 0 14px 0;
  letter-spacing: 0.03em;
}
.cc-platform-row {
  margin-bottom: 12px;
}
.cc-platform-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 4px;
}
.cc-platform-name {
  font-size: 0.85rem;
  font-weight: 600;
  color: #374151;
}
.cc-platform-count {
  font-size: 0.82rem;
  color: #6b7280;
  font-variant-numeric: tabular-nums;
}
.cc-platform-count.over { color: #ef4444; font-weight: 700; }
.cc-platform-track {
  width: 100%;
  height: 8px;
  background: #ede9fe;
  border-radius: 999px;
  overflow: hidden;
}
.cc-platform-bar {
  height: 100%;
  border-radius: 999px;
  transition: width 0.25s, background 0.25s;
  width: 0%;
  background: linear-gradient(90deg, #7c3aed, #a78bfa);
}
.cc-platform-bar.warn { background: linear-gradient(90deg, #f59e0b, #fbbf24); }
.cc-platform-bar.over { background: linear-gradient(90deg, #ef4444, #f87171); }

/* 文字頻度チャート */
#cc-density-section {
  margin-top: 28px;
}
#cc-density-section h3 {
  font-size: 0.9rem;
  font-weight: 700;
  color: #5b21b6;
  margin: 0 0 14px 0;
  letter-spacing: 0.03em;
}
#cc-density-canvas {
  width: 100%;
  max-width: 100%;
  border-radius: 8px;
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  display: block;
}
#cc-density-empty {
  text-align: center;
  color: #a78bfa;
  font-size: 0.9rem;
  padding: 24px;
  background: #faf5ff;
  border: 1.5px solid #ddd6fe;
  border-radius: 8px;
}

/* トースト */
#cc-toast {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #7c3aed;
  color: #fff;
  padding: 10px 22px;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  opacity: 0;
  transition: opacity 0.3s, transform 0.3s;
  pointer-events: none;
  z-index: 9999;
}
#cc-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

@media (max-width: 500px) {
  #cc-stats-grid { grid-template-columns: repeat(2, 1fr); }
}
</style>

<textarea id="cc-textarea" placeholder="ここにテキストを貼り付けるか入力してください — リアルタイムで文字数が計算されます..."></textarea>

<div id="cc-actions">
  <button class="cc-btn-primary" id="cc-copy-btn">テキストをコピー</button>
  <button class="cc-btn-danger" id="cc-clear-btn">クリア</button>
</div>

<div id="cc-limit-row">
  <label for="cc-limit-input">カスタム文字数制限：</label>
  <input type="number" id="cc-limit-input" min="1" placeholder="例：500">
  <span style="font-size:0.8rem;color:#8b5cf6;">文字</span>
</div>

<div id="cc-custom-progress-wrap">
  <div id="cc-custom-progress-label">
    <span id="cc-custom-progress-text">0 / 0</span>
    <span id="cc-custom-progress-over" style="color:#ef4444;display:none;">制限超過！</span>
  </div>
  <div id="cc-custom-progress-bg">
    <div id="cc-custom-progress-bar"></div>
  </div>
</div>

<!-- 統計グリッド -->
<div id="cc-stats-grid">
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-chars-with">0</div>
    <div class="cc-stat-label">文字数（スペース含む）</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-chars-without">0</div>
    <div class="cc-stat-label">文字数（スペース除く）</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-words">0</div>
    <div class="cc-stat-label">単語数</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-sentences">0</div>
    <div class="cc-stat-label">文数</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-paragraphs">0</div>
    <div class="cc-stat-label">段落数</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-lines">0</div>
    <div class="cc-stat-label">行数</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-unique">0</div>
    <div class="cc-stat-label">ユニーク文字数</div>
  </div>
  <div class="cc-stat-card">
    <div class="cc-stat-value" id="cc-bytes">0</div>
    <div class="cc-stat-label">UTF-8バイト数</div>
  </div>
</div>

<!-- プラットフォーム制限バー -->
<div id="cc-platform-section">
  <h3>プラットフォーム文字数制限チェック</h3>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">X（Twitter）日本語</span>
      <span class="cc-platform-count" id="cc-plat-twitter-label">0 / 280</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-twitter-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">SMS（Unicode・日本語）</span>
      <span class="cc-platform-count" id="cc-plat-sms-label">0 / 70</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-sms-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">メタディスクリプション</span>
      <span class="cc-platform-count" id="cc-plat-meta-label">0 / 120</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-meta-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">タイトルタグ（SEO）</span>
      <span class="cc-platform-count" id="cc-plat-title-label">0 / 32</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-title-bar"></div></div>
  </div>

  <div class="cc-platform-row">
    <div class="cc-platform-header">
      <span class="cc-platform-name">Instagramキャプション</span>
      <span class="cc-platform-count" id="cc-plat-ig-label">0 / 2200</span>
    </div>
    <div class="cc-platform-track"><div class="cc-platform-bar" id="cc-plat-ig-bar"></div></div>
  </div>
</div>

<!-- 文字頻度チャート -->
<div id="cc-density-section">
  <h3>文字頻度 Top 10（スペース除く）</h3>
  <div id="cc-density-empty">テキストを入力すると文字頻度グラフが表示されます</div>
  <canvas id="cc-density-canvas" style="display:none;" height="220"></canvas>
</div>

<div id="cc-toast">クリップボードにコピーしました</div>

<script>
(function() {
  var ta = document.getElementById('cc-textarea');
  var limitInput = document.getElementById('cc-limit-input');
  var customProgressWrap = document.getElementById('cc-custom-progress-wrap');
  var customProgressText = document.getElementById('cc-custom-progress-text');
  var customProgressOver = document.getElementById('cc-custom-progress-over');
  var customBar = document.getElementById('cc-custom-progress-bar');
  var toast = document.getElementById('cc-toast');
  var canvas = document.getElementById('cc-density-canvas');
  var densityEmpty = document.getElementById('cc-density-empty');
  var ctx = canvas.getContext('2d');
  var customLimit = 0;

  var platforms = [
    { id: 'twitter', limit: 280 },
    { id: 'sms',     limit: 70  },
    { id: 'meta',    limit: 120 },
    { id: 'title',   limit: 32  },
    { id: 'ig',      limit: 2200 }
  ];

  function getUtf8Bytes(str) {
    var bytes = 0;
    for (var i = 0; i < str.length; i++) {
      var code = str.charCodeAt(i);
      if (code < 0x80) bytes += 1;
      else if (code < 0x800) bytes += 2;
      else if (code >= 0xD800 && code <= 0xDBFF) { bytes += 4; i++; }
      else bytes += 3;
    }
    return bytes;
  }

  function countWords(text) {
    var t = text.trim();
    if (!t) return 0;
    // 日本語は文字単位、英語はスペース区切り
    var latin = t.match(/[a-zA-ZÀ-ÿ]+/g) || [];
    var cjk = t.match(/[\u3040-\u30ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff\uff66-\uff9f]+/g) || [];
    return latin.length + cjk.length;
  }

  function countSentences(text) {
    var t = text.trim();
    if (!t) return 0;
    var matches = t.match(/[^。！？.!?]*[。！？.!?]+/g);
    return matches ? matches.length : (t.length > 0 ? 1 : 0);
  }

  function countParagraphs(text) {
    var t = text.trim();
    if (!t) return 0;
    return t.split(/\n\s*\n/).filter(function(p) { return p.trim().length > 0; }).length;
  }

  function countLines(text) {
    if (!text) return 0;
    return text.split('\n').length;
  }

  function countUnique(text) {
    if (!text) return 0;
    var seen = {};
    for (var i = 0; i < text.length; i++) {
      seen[text[i]] = true;
    }
    return Object.keys(seen).length;
  }

  function getCharFrequency(text) {
    var freq = {};
    for (var i = 0; i < text.length; i++) {
      var c = text[i];
      if (c === ' ' || c === '\u3000' || c === '\n' || c === '\r' || c === '\t') continue;
      freq[c] = (freq[c] || 0) + 1;
    }
    var arr = [];
    for (var ch in freq) {
      arr.push({ char: ch, count: freq[ch] });
    }
    arr.sort(function(a, b) { return b.count - a.count; });
    return arr.slice(0, 10);
  }

  function updatePlatformBar(id, count, limit) {
    var labelEl = document.getElementById('cc-plat-' + id + '-label');
    var barEl = document.getElementById('cc-plat-' + id + '-bar');
    var pct = Math.min((count / limit) * 100, 100);
    barEl.style.width = pct + '%';
    labelEl.textContent = count.toLocaleString() + ' / ' + limit.toLocaleString();
    if (count > limit) {
      barEl.className = 'cc-platform-bar over';
      labelEl.className = 'cc-platform-count over';
    } else if (pct >= 80) {
      barEl.className = 'cc-platform-bar warn';
      labelEl.className = 'cc-platform-count';
    } else {
      barEl.className = 'cc-platform-bar';
      labelEl.className = 'cc-platform-count';
    }
  }

  function drawDensityChart(freq) {
    if (freq.length === 0) {
      canvas.style.display = 'none';
      densityEmpty.style.display = 'block';
      return;
    }
    densityEmpty.style.display = 'none';
    canvas.style.display = 'block';

    var dpr = window.devicePixelRatio || 1;
    var w = canvas.parentElement.clientWidth || 600;
    canvas.width = w * dpr;
    canvas.height = 220 * dpr;
    canvas.style.width = w + 'px';
    canvas.style.height = '220px';
    ctx.scale(dpr, dpr);

    var padL = 44, padR = 16, padT = 20, padB = 48;
    var chartW = w - padL - padR;
    var chartH = 220 - padT - padB;
    var barCount = freq.length;
    var barW = Math.floor((chartW / barCount) * 0.65);
    var gap = Math.floor(chartW / barCount);
    var maxCount = freq[0].count;

    ctx.clearRect(0, 0, w, 220);

    // グリッド線
    ctx.strokeStyle = '#ddd6fe';
    ctx.lineWidth = 1;
    for (var g = 0; g <= 4; g++) {
      var gy = padT + (chartH / 4) * g;
      ctx.beginPath();
      ctx.moveTo(padL, gy);
      ctx.lineTo(padL + chartW, gy);
      ctx.stroke();
      var gridVal = Math.round(maxCount * (1 - g / 4));
      ctx.fillStyle = '#8b5cf6';
      ctx.font = '10px sans-serif';
      ctx.textAlign = 'right';
      ctx.fillText(gridVal, padL - 4, gy + 4);
    }

    // バー
    var colors = ['#7c3aed','#8b5cf6','#a78bfa','#6d28d9','#9333ea','#7c3aed','#8b5cf6','#a78bfa','#6d28d9','#9333ea'];
    for (var i = 0; i < freq.length; i++) {
      var bh = maxCount > 0 ? (freq[i].count / maxCount) * chartH : 0;
      var bx = padL + i * gap + (gap - barW) / 2;
      var by = padT + chartH - bh;

      ctx.fillStyle = colors[i % colors.length];
      ctx.beginPath();
      if (ctx.roundRect) {
        ctx.roundRect(bx, by, barW, bh, [4, 4, 0, 0]);
      } else {
        ctx.rect(bx, by, barW, bh);
      }
      ctx.fill();

      // カウントラベル
      ctx.fillStyle = '#5b21b6';
      ctx.font = 'bold 10px sans-serif';
      ctx.textAlign = 'center';
      ctx.fillText(freq[i].count, bx + barW / 2, by - 4);

      // 文字ラベル
      ctx.fillStyle = '#374151';
      ctx.font = 'bold 14px sans-serif';
      ctx.fillText(freq[i].char, bx + barW / 2, padT + chartH + 18);

      // Unicodeコードポイント
      var code = freq[i].char.codePointAt(0).toString(16).toUpperCase();
      ctx.fillStyle = '#9ca3af';
      ctx.font = '9px sans-serif';
      ctx.fillText('U+' + code.padStart(4, '0'), bx + barW / 2, padT + chartH + 32);
    }
  }

  function updateStats() {
    var text = ta.value;
    var withSpaces = text.length;
    var withoutSpaces = text.replace(/[\s\u3000]/g, '').length;
    var words = countWords(text);
    var sentences = countSentences(text);
    var paragraphs = countParagraphs(text);
    var lines = countLines(text);
    var unique = countUnique(text);
    var bytes = getUtf8Bytes(text);

    document.getElementById('cc-chars-with').textContent = withSpaces.toLocaleString();
    document.getElementById('cc-chars-without').textContent = withoutSpaces.toLocaleString();
    document.getElementById('cc-words').textContent = words.toLocaleString();
    document.getElementById('cc-sentences').textContent = sentences.toLocaleString();
    document.getElementById('cc-paragraphs').textContent = paragraphs.toLocaleString();
    document.getElementById('cc-lines').textContent = lines.toLocaleString();
    document.getElementById('cc-unique').textContent = unique.toLocaleString();
    document.getElementById('cc-bytes').textContent = bytes.toLocaleString();

    // プラットフォームバー
    platforms.forEach(function(p) {
      updatePlatformBar(p.id, withSpaces, p.limit);
    });

    // カスタム制限
    if (customLimit > 0) {
      var pct = Math.min((withSpaces / customLimit) * 100, 100);
      customBar.style.width = pct + '%';
      customProgressText.textContent = withSpaces.toLocaleString() + ' / ' + customLimit.toLocaleString() + ' 文字';
      if (withSpaces > customLimit) {
        customBar.className = 'over';
        customProgressOver.style.display = 'inline';
      } else if (pct >= 80) {
        customBar.className = 'warn';
        customProgressOver.style.display = 'none';
      } else {
        customBar.className = '';
        customProgressOver.style.display = 'none';
      }
    }

    // 文字頻度チャート
    var freq = getCharFrequency(text);
    drawDensityChart(freq);
  }

  function showToast() {
    toast.classList.add('show');
    setTimeout(function() { toast.classList.remove('show'); }, 2000);
  }

  ta.addEventListener('input', updateStats);

  limitInput.addEventListener('input', function() {
    var v = parseInt(limitInput.value, 10);
    customLimit = (isNaN(v) || v <= 0) ? 0 : v;
    if (customLimit > 0) {
      customProgressWrap.style.display = 'block';
    } else {
      customProgressWrap.style.display = 'none';
    }
    updateStats();
  });

  document.getElementById('cc-copy-btn').addEventListener('click', function() {
    var text = ta.value;
    if (!text) return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(showToast);
    } else {
      ta.select();
      document.execCommand('copy');
      showToast();
    }
  });

  document.getElementById('cc-clear-btn').addEventListener('click', function() {
    ta.value = '';
    updateStats();
    ta.focus();
  });

  window.addEventListener('resize', function() {
    var freq = getCharFrequency(ta.value);
    drawDensityChart(freq);
  });

  updateStats();
})();
</script>

</div>

---

## 文字数カウンターの使い方

テキストエリアに文章を貼り付けるか入力するだけで、8つの統計値がリアルタイムで更新されます。インストール不要・登録不要で、すべてブラウザ上で動作します。

**スペース含む文字数**は改行・空白を含むすべての文字数で、TwitterやSMSなどほとんどのプラットフォームの制限はこの方式です。**スペース除く文字数**は空白類を除いた純粋な文字数で、論文や公募要件の「○○字以内（スペース除く）」に対応します。**UTF-8バイト数**はデータベースや外部APIのバイト上限チェックに使えます。日本語1文字は通常3バイト、絵文字は4バイトです。

プラットフォーム制限バーは80%到達で黄色、超過で赤くなります。カスタム制限欄に数字を入力すれば、自社規定や入稿フォームの上限を任意に設定できます。

文字頻度グラフは、スペース・改行を除いた文字のうち出現数が多い上位10文字を棒グラフで表示します。各バーの下にはUnicodeコードポイントも表示されるため、意図しない特殊文字の混入チェックにも使えます。

---

## 文字数制限が重要な場面

**SNS投稿**では各プラットフォームに文字数制限があります。X（Twitter）は日本語でも1文字1カウントの280文字制限。日本語SMSはUnicode（UCS-2）エンコードとなるため1通あたり70文字が上限です。制限を超えるとメッセージが分割され、受信側で見づらくなります。

**SEO・Webコンテンツ**では、タイトルタグは全角換算で約32文字（半角なら60文字前後）を超えると検索結果で切れます。メタディスクリプションも日本語では120文字程度が適切です。このツールでリアルタイムに確認しながら書くことで、検索結果での表示を最適化できます。

**論文・レポート・公募申請書**では「○○字以内」「○○字以上○○字以内」という要件が厳格に課されます。スペース含む/除くの切り替えや、段落数・行数の確認が一画面でできるため、提出前の最終チェックに役立ちます。

**APIやデータベース連携**では、テキストフィールドのバイト上限（例: MySQLのVARCHAR(255) は255バイト）に気をつける必要があります。日本語はASCIIの3倍のバイト数を消費するため、UTF-8バイト数の確認は必須です。

---

## 関連ツール

> 単語数・読了時間を計算 → [単語数・文字数カウンター](/ja/tools/moji-counter/)

> 頻出キーワードを分析 → [単語頻度カウンター](/ja/tools/word-frequency-counter/)

> 記事の読了時間を計算 → [読了時間計算ツール](/ja/tools/reading-time-calculator/)

---

**ライター・フリーランスの経理を効率化**

文章を書くのは得意でも、経費管理や確定申告は面倒…。クラウド会計ソフト「freee」なら、レシート撮影で経費入力完了。確定申告もスマホで簡単に。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
