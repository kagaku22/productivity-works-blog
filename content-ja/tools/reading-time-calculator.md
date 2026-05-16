---
title: "読書時間計算ツール"
date: 2025-05-16
description: "テキストを貼り付けるだけで読書時間を瞬時に計算。読書速度の調整、文字数・語数・文数のカウント、可読性スコアも確認できる無料ツールです。"
categories: ["無料ツール"]
slug: "reading-time-calculator"
aliases: ["/ja/tools/reading-speed/", "/ja/tools/wpm-calculator/"]
ShowToc: false
cover:
  image: "/images/covers/reading-time-calculator-ja.png"
  alt: "読書時間計算ツール"
---

<div id="rt-app">

<style>
#rt-app {
  font-family: "Noto Sans JP", "Hiragino Sans", "Yu Gothic", system-ui, sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1f2937;
}
#rt-app * { box-sizing: border-box; }
#rt-app h2 {
  font-size: 1.15rem;
  font-weight: 700;
  margin: 1.5rem 0 0.75rem;
  color: #92400e;
}
#rt-app .card {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1.25rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
#rt-app textarea {
  width: 100%;
  min-height: 160px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  font-size: 0.95rem;
  font-family: inherit;
  resize: vertical;
  transition: border-color 0.2s;
  outline: none;
  line-height: 1.7;
}
#rt-app textarea:focus { border-color: #d97706; }
#rt-app .or-divider {
  text-align: center;
  color: #9ca3af;
  font-size: 0.85rem;
  margin: 0.75rem 0;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
#rt-app .or-divider::before,
#rt-app .or-divider::after {
  content: "";
  flex: 1;
  height: 1px;
  background: #e5e7eb;
}
#rt-app .word-count-row {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
}
#rt-app .word-count-row label {
  font-size: 0.9rem;
  color: #374151;
  font-weight: 500;
  white-space: nowrap;
}
#rt-app input[type="number"] {
  width: 130px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  padding: 0.45rem 0.75rem;
  font-size: 0.95rem;
  font-family: inherit;
  outline: none;
  transition: border-color 0.2s;
}
#rt-app input[type="number"]:focus { border-color: #d97706; }
#rt-app .speed-section {
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}
#rt-app .speed-label {
  font-size: 0.9rem;
  color: #374151;
  font-weight: 500;
  white-space: nowrap;
}
#rt-app input[type="range"] {
  flex: 1;
  min-width: 140px;
  accent-color: #d97706;
  height: 6px;
  cursor: pointer;
}
#rt-app .speed-val {
  background: #fef3c7;
  color: #92400e;
  border-radius: 20px;
  padding: 0.2rem 0.75rem;
  font-size: 0.88rem;
  font-weight: 700;
  white-space: nowrap;
}
#rt-app .speed-presets {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  margin-top: 0.5rem;
}
#rt-app .preset-btn {
  border: 1.5px solid #d97706;
  background: transparent;
  color: #92400e;
  border-radius: 20px;
  padding: 0.2rem 0.75rem;
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#rt-app .preset-btn:hover,
#rt-app .preset-btn.active {
  background: #d97706;
  color: #fff;
}
#rt-app .results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 0.75rem;
  margin-bottom: 0.5rem;
}
#rt-app .result-box {
  background: #fffbeb;
  border: 1.5px solid #fde68a;
  border-radius: 10px;
  padding: 0.9rem 1rem;
  text-align: center;
}
#rt-app .result-box .r-val {
  font-size: 1.5rem;
  font-weight: 800;
  color: #d97706;
  line-height: 1.1;
}
#rt-app .result-box .r-lbl {
  font-size: 0.73rem;
  color: #6b7280;
  margin-top: 0.2rem;
  line-height: 1.3;
}
#rt-app .progress-wrap {
  margin: 1rem 0 0.25rem;
}
#rt-app .progress-label {
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
  color: #9ca3af;
  margin-bottom: 0.3rem;
}
#rt-app .progress-bar-bg {
  width: 100%;
  height: 14px;
  background: #f3f4f6;
  border-radius: 999px;
  overflow: hidden;
}
#rt-app .progress-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #f59e0b, #d97706);
  border-radius: 999px;
  transition: width 0.4s ease;
  min-width: 4px;
}
#rt-app .speed-comparison {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.6rem;
  margin-top: 0.75rem;
}
#rt-app .cmp-box {
  border-radius: 10px;
  padding: 0.65rem 0.75rem;
  text-align: center;
  border: 1.5px solid #e5e7eb;
}
#rt-app .cmp-box.slow  { border-color: #fca5a5; background: #fff1f1; }
#rt-app .cmp-box.avg   { border-color: #fde68a; background: #fffbeb; }
#rt-app .cmp-box.fast  { border-color: #6ee7b7; background: #ecfdf5; }
#rt-app .cmp-box .cmp-t { font-size: 0.72rem; font-weight: 700; color: #6b7280; }
#rt-app .cmp-box .cmp-v { font-size: 1.1rem; font-weight: 800; margin: 0.1rem 0; }
#rt-app .cmp-box.slow  .cmp-v { color: #dc2626; }
#rt-app .cmp-box.avg   .cmp-v { color: #d97706; }
#rt-app .cmp-box.fast  .cmp-v { color: #059669; }
#rt-app .cmp-box .cmp-wpm { font-size: 0.7rem; color: #9ca3af; }
#rt-app .book-row {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
}
#rt-app .book-row label { font-size: 0.9rem; color: #374151; font-weight: 500; white-space: nowrap; }
#rt-app .book-result {
  margin-top: 0.75rem;
  padding: 0.65rem 1rem;
  background: #fffbeb;
  border: 1.5px solid #fde68a;
  border-radius: 8px;
  font-size: 0.92rem;
  color: #92400e;
  font-weight: 600;
  line-height: 1.6;
}
#rt-app .readability-section { margin-top: 0.5rem; }
#rt-app .rdbl-row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  align-items: flex-start;
}
#rt-app .rdbl-item { flex: 1; min-width: 150px; }
#rt-app .rdbl-item .rdbl-val { font-size: 1.3rem; font-weight: 800; color: #d97706; }
#rt-app .rdbl-item .rdbl-lbl { font-size: 0.75rem; color: #6b7280; margin-top: 0.15rem; }
#rt-app .rdbl-item .rdbl-note { font-size: 0.78rem; color: #374151; margin-top: 0.1rem; }
#rt-app .clear-btn {
  background: transparent;
  border: 1.5px solid #e5e7eb;
  color: #6b7280;
  border-radius: 8px;
  padding: 0.35rem 1rem;
  font-size: 0.82rem;
  cursor: pointer;
  transition: border-color 0.15s, color 0.15s;
  float: right;
  margin-top: 0.25rem;
}
#rt-app .clear-btn:hover { border-color: #d97706; color: #d97706; }
#rt-app .empty-state {
  text-align: center;
  color: #9ca3af;
  font-size: 0.9rem;
  padding: 1.5rem 0;
}
#rt-app .freee-cta {
  margin-top: 2rem;
  padding: 1.1rem 1.4rem;
  background: linear-gradient(135deg, #fef3c7 0%, #fffbeb 100%);
  border: 1.5px solid #fde68a;
  border-radius: 12px;
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}
#rt-app .freee-cta .cta-icon {
  font-size: 2rem;
  flex-shrink: 0;
}
#rt-app .freee-cta .cta-body { flex: 1; min-width: 180px; }
#rt-app .freee-cta .cta-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: #92400e;
  margin-bottom: 0.2rem;
}
#rt-app .freee-cta .cta-text {
  font-size: 0.82rem;
  color: #6b7280;
  line-height: 1.5;
}
#rt-app .freee-cta .cta-btn {
  display: inline-block;
  background: #d97706;
  color: #fff;
  border-radius: 8px;
  padding: 0.5rem 1.2rem;
  font-size: 0.88rem;
  font-weight: 700;
  text-decoration: none;
  white-space: nowrap;
  transition: background 0.15s;
}
#rt-app .freee-cta .cta-btn:hover { background: #b45309; }
@media (max-width: 500px) {
  #rt-app .results-grid { grid-template-columns: 1fr 1fr; }
  #rt-app .speed-comparison { grid-template-columns: 1fr; }
}
</style>

<!-- INPUT -->
<div class="card">
  <h2 style="margin-top:0">テキストを貼り付ける</h2>
  <textarea id="rt-textarea" placeholder="ここにテキストを貼り付けるか、入力してください…" oninput="rtUpdate()"></textarea>
  <button class="clear-btn" onclick="rtClear()">クリア</button>
  <div class="or-divider">または文字数を直接入力</div>
  <div class="word-count-row">
    <label for="rt-wc-input">文字数:</label>
    <input type="number" id="rt-wc-input" min="1" max="9999999" placeholder="例: 3000" oninput="rtUpdate()" />
    <span style="font-size:0.8rem;color:#9ca3af;">（上のテキスト入力時は不要）</span>
  </div>
</div>

<!-- SPEED -->
<div class="card">
  <h2 style="margin-top:0">読書速度</h2>
  <div class="speed-section">
    <span class="speed-label">文字/分:</span>
    <input type="range" id="rt-speed" min="100" max="1200" value="500" oninput="rtSpeedChange(this.value)" />
    <span class="speed-val" id="rt-speed-val">500 文字/分</span>
  </div>
  <div class="speed-presets">
    <button class="preset-btn" onclick="rtSetSpeed(300)">ゆっくり (300)</button>
    <button class="preset-btn active" onclick="rtSetSpeed(500)">普通 (500)</button>
    <button class="preset-btn" onclick="rtSetSpeed(700)">速い (700)</button>
    <button class="preset-btn" onclick="rtSetSpeed(1000)">速読 (1000)</button>
  </div>
  <div style="font-size:0.78rem;color:#9ca3af;margin-top:0.5rem;">一般的な日本語の読書速度: 400〜600文字/分（黙読）</div>
</div>

<!-- RESULTS -->
<div class="card" id="rt-results-card">
  <h2 style="margin-top:0">計算結果</h2>
  <div id="rt-results-body">
    <div class="empty-state">テキストを貼り付けるか、文字数を入力すると結果が表示されます。</div>
  </div>
</div>

<!-- BOOK ESTIMATE -->
<div class="card">
  <h2 style="margin-top:0">本の読書時間を推定</h2>
  <div class="book-row">
    <label for="rt-pages">ページ数:</label>
    <input type="number" id="rt-pages" min="1" max="10000" placeholder="例: 300" oninput="rtBookUpdate()" />
    <label for="rt-wppage">1ページあたりの文字数:</label>
    <input type="number" id="rt-wppage" min="50" max="3000" value="600" placeholder="600" oninput="rtBookUpdate()" />
  </div>
  <div id="rt-book-result" class="book-result" style="display:none"></div>
</div>

<script>
(function() {
  var cpm = 500; // characters per minute (JP default)
  var spkCpm = 300; // speaking rate (JP)

  function fmtTime(minutes) {
    if (minutes < 1) return "1分未満";
    if (minutes < 60) {
      var m = Math.round(minutes);
      return m + "分";
    }
    var h = Math.floor(minutes / 60);
    var m = Math.round(minutes % 60);
    return h + "時間" + (m > 0 ? m + "分" : "");
  }

  function fmtNum(n) {
    return n.toLocaleString();
  }

  function analyzeText(text) {
    var charCount = text.replace(/\s/g, "").length; // chars excluding whitespace
    var charCountAll = text.length;
    // Word count: count sequences of non-space chars (for CJK, each char ~ 1 word)
    var wordCount = text.trim().match(/\S+/g) ? text.trim().match(/\S+/g).length : 0;
    // Sentence count: split on Japanese/Western punctuation
    var sentences = text.split(/[。！？!?.]+/).filter(function(s) { return s.trim().length > 0; });
    var sentenceCount = sentences.length;
    var avgCharsPerSentence = sentenceCount > 0 ? (charCount / sentenceCount) : 0;
    return {
      charCount: charCount,
      charCountAll: charCountAll,
      wordCount: wordCount,
      sentenceCount: sentenceCount,
      avgCharsPerSentence: avgCharsPerSentence
    };
  }

  function readabilityLabel(avgCps) {
    if (avgCps < 30) return { label: "非常に読みやすい", color: "#059669" };
    if (avgCps < 50) return { label: "読みやすい", color: "#10b981" };
    if (avgCps < 70) return { label: "普通", color: "#d97706" };
    if (avgCps < 100) return { label: "やや難しい", color: "#f59e0b" };
    return { label: "難しい", color: "#dc2626" };
  }

  function progressPercent(minutes) {
    return Math.min(100, Math.max(2, (minutes / 60) * 100));
  }

  window.rtUpdate = function() {
    var text = document.getElementById("rt-textarea").value;
    var wcInput = document.getElementById("rt-wc-input").value;
    var hasText = text.trim().length > 0;
    var hasWC = wcInput && parseInt(wcInput) > 0;

    if (!hasText && !hasWC) {
      document.getElementById("rt-results-body").innerHTML =
        '<div class="empty-state">テキストを貼り付けるか、文字数を入力すると結果が表示されます。</div>';
      return;
    }

    var data = hasText ? analyzeText(text) : null;
    var charCount = hasText ? data.charCount : parseInt(wcInput);
    var readMin = charCount / cpm;
    var spkMin = charCount / spkCpm;

    var html = '<div class="results-grid">';
    html += '<div class="result-box"><div class="r-val">' + fmtTime(readMin) + '</div><div class="r-lbl">読書時間</div></div>';
    html += '<div class="result-box"><div class="r-val">' + fmtTime(spkMin) + '</div><div class="r-lbl">音読時間<br>(300文字/分)</div></div>';
    if (hasText) {
      html += '<div class="result-box"><div class="r-val">' + fmtNum(data.charCount) + '</div><div class="r-lbl">文字数<br>(空白除く)</div></div>';
      html += '<div class="result-box"><div class="r-val">' + fmtNum(data.charCountAll) + '</div><div class="r-lbl">文字数<br>(全体)</div></div>';
      html += '<div class="result-box"><div class="r-val">' + fmtNum(data.sentenceCount) + '</div><div class="r-lbl">文数</div></div>';
    } else {
      html += '<div class="result-box"><div class="r-val">' + fmtNum(charCount) + '</div><div class="r-lbl">文字数</div></div>';
    }
    html += '</div>';

    // Progress bar
    var pct = progressPercent(readMin);
    html += '<div class="progress-wrap">';
    html += '<div class="progress-label"><span>読書時間</span><span>' + fmtTime(readMin) + ' (' + cpm + '文字/分)</span></div>';
    html += '<div class="progress-bar-bg"><div class="progress-bar-fill" style="width:' + pct + '%"></div></div>';
    html += '</div>';

    // Speed comparison
    html += '<div class="speed-comparison">';
    html += '<div class="cmp-box slow"><div class="cmp-t">ゆっくり</div><div class="cmp-v">' + fmtTime(charCount/300) + '</div><div class="cmp-wpm">300文字/分</div></div>';
    html += '<div class="cmp-box avg"><div class="cmp-t">普通</div><div class="cmp-v">' + fmtTime(charCount/500) + '</div><div class="cmp-wpm">500文字/分</div></div>';
    html += '<div class="cmp-box fast"><div class="cmp-t">速い</div><div class="cmp-v">' + fmtTime(charCount/800) + '</div><div class="cmp-wpm">800文字/分</div></div>';
    html += '</div>';

    // Readability
    if (hasText && data.charCount > 10 && data.sentenceCount > 0) {
      var rdbl = readabilityLabel(data.avgCharsPerSentence);
      html += '<div class="readability-section"><h2>可読性</h2>';
      html += '<div class="rdbl-row">';
      html += '<div class="rdbl-item"><div class="rdbl-val" style="color:' + rdbl.color + '">' + rdbl.label + '</div><div class="rdbl-lbl">全体の難易度</div></div>';
      html += '<div class="rdbl-item"><div class="rdbl-val">' + data.avgCharsPerSentence.toFixed(1) + '</div><div class="rdbl-lbl">1文あたりの平均文字数</div><div class="rdbl-note">' + (data.avgCharsPerSentence < 30 ? "簡潔で読みやすい" : data.avgCharsPerSentence < 60 ? "適切な文の長さ" : "文が長め") + '</div></div>';
      html += '<div class="rdbl-item"><div class="rdbl-val">' + fmtNum(data.sentenceCount) + '</div><div class="rdbl-lbl">文の総数</div></div>';
      html += '</div></div>';
    }

    document.getElementById("rt-results-body").innerHTML = html;
  };

  window.rtSpeedChange = function(val) {
    cpm = parseInt(val);
    document.getElementById("rt-speed-val").textContent = cpm + " 文字/分";
    document.querySelectorAll("#rt-app .preset-btn").forEach(function(b) { b.classList.remove("active"); });
    rtUpdate();
    rtBookUpdate();
  };

  window.rtSetSpeed = function(val) {
    cpm = val;
    document.getElementById("rt-speed").value = val;
    document.getElementById("rt-speed-val").textContent = val + " 文字/分";
    document.querySelectorAll("#rt-app .preset-btn").forEach(function(b) {
      var m = b.textContent.match(/\d+/);
      b.classList.toggle("active", m && parseInt(m[0]) === val);
    });
    rtUpdate();
    rtBookUpdate();
  };

  window.rtClear = function() {
    document.getElementById("rt-textarea").value = "";
    document.getElementById("rt-wc-input").value = "";
    rtUpdate();
  };

  window.rtBookUpdate = function() {
    var pages = parseInt(document.getElementById("rt-pages").value);
    var cpPage = parseInt(document.getElementById("rt-wppage").value) || 600;
    var el = document.getElementById("rt-book-result");
    if (!pages || pages < 1) { el.style.display = "none"; return; }
    var totalChars = pages * cpPage;
    var mins = totalChars / cpm;
    el.style.display = "block";
    el.innerHTML = "<strong>" + pages + "ページ</strong>の本（約" + fmtNum(totalChars) + "文字）は、あなたの読書速度（" + cpm + "文字/分）で約<strong>" + fmtTime(mins) + "</strong>かかります。";
  };
})();
</script>

</div>

---

<div style="margin-top:2rem;padding:1.1rem 1.4rem;background:linear-gradient(135deg,#fef3c7 0%,#fffbeb 100%);border:1.5px solid #fde68a;border-radius:12px;display:flex;align-items:center;gap:1rem;flex-wrap:wrap;">
  <div style="font-size:2rem;flex-shrink:0;">📊</div>
  <div style="flex:1;min-width:180px;">
    <div style="font-size:0.95rem;font-weight:700;color:#92400e;margin-bottom:0.2rem;">freee会計でビジネスをもっとスマートに</div>
    <div style="font-size:0.82rem;color:#6b7280;line-height:1.5;">確定申告・請求書・経費管理をまとめて自動化。個人事業主・フリーランスに人気のクラウド会計ソフト。</div>
  </div>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;background:#d97706;color:#fff;border-radius:8px;padding:0.5rem 1.2rem;font-size:0.88rem;font-weight:700;text-decoration:none;white-space:nowrap;">freeeを無料で試す</a>
</div>
