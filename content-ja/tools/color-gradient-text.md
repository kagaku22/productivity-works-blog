---
title: "グラデーションテキスト生成 — 無料オンラインツール"
date: 2025-05-16
description: "テキストにカラーグラデーションを適用。最大5色のカラーストップで虹色・グラデーション文字を作成。HTML（インラインスタイル）とCSSコードをワンクリックでコピー。"
categories: ["無料ツール"]
slug: "color-gradient-text"
ShowToc: false
aliases:
  - "/ja/tools/gradient-text/"
  - "/ja/tools/rainbow-text/"
cover:
  image: "/images/covers/color-gradient-text-ja.png"
  alt: "グラデーションテキスト生成ツール"
---

テキストを入力し、最大5つのカラーストップを設定して美しいグラデーション文字を生成。HTMLのインラインスパンタグまたはCSS `background-clip` グラデーションコードをコピーできます。

<div id="gt-app">

<style>
/* ── Reset ──────────────────────────────────────────────────── */
#gt-app *, #gt-app *::before, #gt-app *::after {
  box-sizing: border-box; margin: 0; padding: 0;
}
#gt-app {
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 14px;
  color: #1a1a2e;
  line-height: 1.5;
}

/* ── Layout ─────────────────────────────────────────────────── */
#gt-app .gt-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-top: 20px;
}
@media (max-width: 740px) {
  #gt-app .gt-grid { grid-template-columns: 1fr; }
}

/* ── Panel ──────────────────────────────────────────────────── */
#gt-app .gt-panel {
  background: #f8f9fc;
  border: 1px solid #e2e6f0;
  border-radius: 12px;
  padding: 18px;
}
#gt-app .gt-panel h3 {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: .07em;
  color: #6b7280;
  margin-bottom: 14px;
}

/* ── Text input ─────────────────────────────────────────────── */
#gt-app textarea {
  width: 100%;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  padding: 10px 12px;
  font-size: 15px;
  font-family: inherit;
  resize: vertical;
  min-height: 80px;
  outline: none;
  transition: border-color .2s;
}
#gt-app textarea:focus { border-color: #6366f1; }

/* ── Color stops ────────────────────────────────────────────── */
#gt-app .gt-stops {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#gt-app .gt-stop-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#gt-app .gt-stop-row input[type="color"] {
  width: 38px;
  height: 38px;
  border: 2px solid #e2e6f0;
  border-radius: 8px;
  cursor: pointer;
  padding: 2px;
  background: #fff;
}
#gt-app .gt-stop-row input[type="text"] {
  width: 90px;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 13px;
  font-family: monospace;
  outline: none;
  text-transform: uppercase;
}
#gt-app .gt-stop-row input[type="text"]:focus { border-color: #6366f1; }
#gt-app .gt-stop-row .gt-stop-label {
  font-size: 12px;
  color: #6b7280;
  flex: 1;
}
#gt-app .gt-stop-row button.gt-rm {
  background: none;
  border: 1px solid #e5e7eb;
  border-radius: 6px;
  width: 28px; height: 28px;
  cursor: pointer;
  font-size: 15px;
  color: #ef4444;
  line-height: 1;
  display: flex; align-items: center; justify-content: center;
}
#gt-app .gt-stop-row button.gt-rm:hover { background: #fef2f2; }
#gt-app button.gt-add-stop {
  margin-top: 6px;
  background: none;
  border: 1.5px dashed #6366f1;
  border-radius: 8px;
  padding: 7px 14px;
  font-size: 13px;
  color: #6366f1;
  cursor: pointer;
  width: 100%;
  font-weight: 600;
}
#gt-app button.gt-add-stop:hover { background: #eef2ff; }
#gt-app button.gt-add-stop:disabled { opacity: .4; cursor: not-allowed; }

/* ── Options ────────────────────────────────────────────────── */
#gt-app .gt-options {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 14px;
}
#gt-app .gt-option-row {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: #374151;
  cursor: pointer;
}
#gt-app .gt-option-row input[type="checkbox"] { accent-color: #6366f1; width: 15px; height: 15px; }

/* ── Preview ────────────────────────────────────────────────── */
#gt-app .gt-preview-box {
  min-height: 90px;
  background: #fff;
  border: 1px solid #e2e6f0;
  border-radius: 10px;
  padding: 20px 16px;
  font-size: 32px;
  font-weight: 800;
  letter-spacing: .01em;
  word-break: break-all;
  line-height: 1.3;
  margin-bottom: 14px;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

/* ── Gradient bar ───────────────────────────────────────────── */
#gt-app .gt-bar {
  height: 10px;
  border-radius: 5px;
  margin-bottom: 16px;
  border: 1px solid #e2e6f0;
}

/* ── Output ─────────────────────────────────────────────────── */
#gt-app .gt-output {
  margin-top: 4px;
}
#gt-app .gt-output pre {
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 8px;
  padding: 14px;
  font-size: 12px;
  font-family: monospace;
  overflow-x: auto;
  white-space: pre-wrap;
  word-break: break-all;
  max-height: 180px;
  line-height: 1.6;
}
#gt-app .gt-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 10px;
}
#gt-app .gt-tab {
  padding: 6px 14px;
  border-radius: 6px;
  border: 1.5px solid #d1d5db;
  background: #fff;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  color: #374151;
}
#gt-app .gt-tab.active {
  background: #6366f1;
  color: #fff;
  border-color: #6366f1;
}

/* ── Buttons ────────────────────────────────────────────────── */
#gt-app .gt-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 16px;
  border-radius: 8px;
  border: none;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background .15s, transform .1s;
}
#gt-app .gt-btn:active { transform: scale(.97); }
#gt-app .gt-btn-primary {
  background: #6366f1;
  color: #fff;
}
#gt-app .gt-btn-primary:hover { background: #4f46e5; }
#gt-app .gt-btn-ghost {
  background: #f3f4f6;
  color: #374151;
}
#gt-app .gt-btn-ghost:hover { background: #e5e7eb; }
#gt-app .gt-btn-row {
  display: flex;
  gap: 8px;
  margin-top: 10px;
  flex-wrap: wrap;
}

/* ── Toast ──────────────────────────────────────────────────── */
#gt-app .gt-toast {
  display: none;
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  background: #1e293b;
  color: #f8fafc;
  padding: 10px 22px;
  border-radius: 8px;
  font-size: 13px;
  z-index: 9999;
  pointer-events: none;
}
#gt-app .gt-toast.show { display: block; }

/* ── Font size ──────────────────────────────────────────────── */
#gt-app .gt-font-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 10px;
  font-size: 13px;
  color: #374151;
}
#gt-app .gt-font-row input[type="range"] {
  flex: 1;
  accent-color: #6366f1;
}
</style>

<div class="gt-grid">

  <!-- LEFT: Controls -->
  <div>
    <div class="gt-panel">
      <h3>テキスト入力</h3>
      <textarea id="gt-text" rows="3" placeholder="ここにテキストを入力...">こんにちは！Hello World!</textarea>
      <div class="gt-font-row">
        <span>プレビューサイズ:</span>
        <input type="range" id="gt-font-size" min="16" max="72" value="36">
        <span id="gt-font-label">36px</span>
      </div>
    </div>

    <div class="gt-panel" style="margin-top:16px;">
      <h3>カラーストップ</h3>
      <div class="gt-stops" id="gt-stops-list"></div>
      <button class="gt-add-stop" id="gt-add-stop-btn">＋ カラーストップを追加</button>
      <div class="gt-options">
        <label class="gt-option-row">
          <input type="checkbox" id="gt-skip-spaces"> スペースをスキップ（空白に色を付けない）
        </label>
        <label class="gt-option-row">
          <input type="checkbox" id="gt-bold" checked> 太字プレビュー
        </label>
      </div>
    </div>
  </div>

  <!-- RIGHT: Preview + Output -->
  <div>
    <div class="gt-panel">
      <h3>リアルタイムプレビュー</h3>
      <div class="gt-bar" id="gt-gradient-bar"></div>
      <div class="gt-preview-box" id="gt-preview"></div>
    </div>

    <div class="gt-panel" style="margin-top:16px;">
      <h3>出力コード</h3>
      <div class="gt-tabs">
        <button class="gt-tab active" id="gt-tab-html" onclick="gtSwitchTab('html')">HTML（インラインスパン）</button>
        <button class="gt-tab" id="gt-tab-css" onclick="gtSwitchTab('css')">CSSグラデーション</button>
      </div>
      <div class="gt-output">
        <pre id="gt-output-code"></pre>
      </div>
      <div class="gt-btn-row">
        <button class="gt-btn gt-btn-primary" onclick="gtCopy()">コードをコピー</button>
        <button class="gt-btn gt-btn-ghost" onclick="gtReset()">リセット</button>
      </div>
    </div>
  </div>

</div>

<div class="gt-toast" id="gt-toast">コピーしました！</div>

<script>
(function () {
  'use strict';

  /* ── State ───────────────────────────────────────────────── */
  var gtStops = [
    { color: '#6366f1' },
    { color: '#ec4899' },
  ];
  var gtTab = 'html';

  /* ── DOM refs ────────────────────────────────────────────── */
  var elText     = document.getElementById('gt-text');
  var elPreview  = document.getElementById('gt-preview');
  var elBar      = document.getElementById('gt-gradient-bar');
  var elCode     = document.getElementById('gt-output-code');
  var elAddBtn   = document.getElementById('gt-add-stop-btn');
  var elStopList = document.getElementById('gt-stops-list');
  var elSkip     = document.getElementById('gt-skip-spaces');
  var elBold     = document.getElementById('gt-bold');
  var elFontSize = document.getElementById('gt-font-size');
  var elFontLbl  = document.getElementById('gt-font-label');
  var elToast    = document.getElementById('gt-toast');

  /* ── Color helpers ───────────────────────────────────────── */
  function hexToRgb(hex) {
    hex = hex.replace(/^#/, '');
    if (hex.length === 3) hex = hex[0]+hex[0]+hex[1]+hex[1]+hex[2]+hex[2];
    var n = parseInt(hex, 16);
    return [(n >> 16) & 255, (n >> 8) & 255, n & 255];
  }

  function rgbToHex(r, g, b) {
    return '#' + [r, g, b].map(function (v) {
      return Math.round(v).toString(16).padStart(2, '0');
    }).join('');
  }

  function lerpColor(stops, t) {
    if (stops.length === 1) return stops[0].color;
    var seg = 1 / (stops.length - 1);
    var i = Math.min(Math.floor(t / seg), stops.length - 2);
    var lt = (t - i * seg) / seg;
    var a = hexToRgb(stops[i].color);
    var b = hexToRgb(stops[i + 1].color);
    return rgbToHex(
      a[0] + (b[0] - a[0]) * lt,
      a[1] + (b[1] - a[1]) * lt,
      a[2] + (b[2] - a[2]) * lt
    );
  }

  /* ── Stop labels (JP) ────────────────────────────────────── */
  function stopLabel(i, total) {
    if (i === 0) return '開始色';
    if (i === total - 1) return '終了色';
    return 'ストップ ' + (i + 1);
  }

  /* ── Render stop list ────────────────────────────────────── */
  function renderStops() {
    elStopList.innerHTML = '';
    gtStops.forEach(function (stop, i) {
      var row = document.createElement('div');
      row.className = 'gt-stop-row';

      var picker = document.createElement('input');
      picker.type = 'color';
      picker.value = stop.color;
      picker.addEventListener('input', function () {
        gtStops[i].color = picker.value;
        hexInput.value = picker.value.toUpperCase();
        update();
      });

      var hexInput = document.createElement('input');
      hexInput.type = 'text';
      hexInput.maxLength = 7;
      hexInput.value = stop.color.toUpperCase();
      hexInput.addEventListener('input', function () {
        var v = hexInput.value.trim();
        if (/^#?[0-9a-fA-F]{6}$/.test(v)) {
          var hex = v.startsWith('#') ? v : '#' + v;
          gtStops[i].color = hex;
          picker.value = hex;
          update();
        }
      });

      var label = document.createElement('span');
      label.className = 'gt-stop-label';
      label.textContent = stopLabel(i, gtStops.length);

      row.appendChild(picker);
      row.appendChild(hexInput);
      row.appendChild(label);

      if (gtStops.length > 2) {
        var rmBtn = document.createElement('button');
        rmBtn.className = 'gt-rm';
        rmBtn.textContent = '×';
        rmBtn.title = '削除';
        rmBtn.addEventListener('click', function () {
          gtStops.splice(i, 1);
          renderStops();
          update();
        });
        row.appendChild(rmBtn);
      }

      elStopList.appendChild(row);
    });
    elAddBtn.disabled = gtStops.length >= 5;
  }

  elAddBtn.addEventListener('click', function () {
    if (gtStops.length < 5) {
      gtStops.push({ color: '#facc15' });
      renderStops();
      update();
    }
  });

  /* ── Update ──────────────────────────────────────────────── */
  function update() {
    var text = elText.value || '';
    var skip = elSkip.checked;
    var bold = elBold.checked;
    var fs   = elFontSize.value + 'px';

    var colors = gtStops.map(function (s) { return s.color; });
    elBar.style.background = 'linear-gradient(90deg, ' + colors.join(', ') + ')';

    var chars = text.split('');
    var colorable = skip
      ? chars.filter(function (c) { return c !== ' '; })
      : chars;
    var total = colorable.length;
    var colorIdx = 0;

    elPreview.innerHTML = '';
    elPreview.style.fontSize = fs;
    elPreview.style.fontWeight = bold ? '800' : '400';

    chars.forEach(function (ch) {
      var span = document.createElement('span');
      if (skip && ch === ' ') {
        span.textContent = '\u00a0';
      } else {
        var t = total <= 1 ? 0 : colorIdx / (total - 1);
        var col = lerpColor(gtStops, t);
        span.style.color = col;
        span.textContent = ch;
        colorIdx++;
      }
      elPreview.appendChild(span);
    });

    if (gtTab === 'html') {
      renderHtmlOutput(chars, skip, bold);
    } else {
      renderCssOutput(colors);
    }
  }

  function renderHtmlOutput(chars, skip, bold) {
    var total = skip
      ? chars.filter(function (c) { return c !== ' '; }).length
      : chars.length;
    var colorIdx = 0;
    var parts = chars.map(function (ch) {
      if (skip && ch === ' ') return ' ';
      var t = total <= 1 ? 0 : colorIdx / (total - 1);
      var col = lerpColor(gtStops, t);
      colorIdx++;
      return '<span style="color:' + col + '">' + escHtml(ch) + '</span>';
    });
    var tag = bold ? 'b' : 'span';
    elCode.textContent = '<' + tag + '>' + parts.join('') + '</' + tag + '>';
  }

  function renderCssOutput(colors) {
    var gradient = 'linear-gradient(90deg, ' + colors.join(', ') + ')';
    elCode.textContent =
      '.gradient-text {\n' +
      '  background: ' + gradient + ';\n' +
      '  -webkit-background-clip: text;\n' +
      '  -webkit-text-fill-color: transparent;\n' +
      '  background-clip: text;\n' +
      '  display: inline-block;\n' +
      '}';
  }

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  window.gtSwitchTab = function (tab) {
    gtTab = tab;
    document.getElementById('gt-tab-html').classList.toggle('active', tab === 'html');
    document.getElementById('gt-tab-css').classList.toggle('active', tab === 'css');
    update();
  };

  window.gtCopy = function () {
    var txt = elCode.textContent;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(txt).then(showToast);
    } else {
      var ta = document.createElement('textarea');
      ta.value = txt;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showToast();
    }
  };

  function showToast() {
    elToast.classList.add('show');
    setTimeout(function () { elToast.classList.remove('show'); }, 1800);
  }

  window.gtReset = function () {
    elText.value = 'こんにちは！Hello World!';
    gtStops = [{ color: '#6366f1' }, { color: '#ec4899' }];
    elSkip.checked = false;
    elBold.checked = true;
    elFontSize.value = 36;
    elFontLbl.textContent = '36px';
    renderStops();
    update();
  };

  elText.addEventListener('input', update);
  elSkip.addEventListener('change', update);
  elBold.addEventListener('change', update);
  elFontSize.addEventListener('input', function () {
    elFontLbl.textContent = elFontSize.value + 'px';
    update();
  });

  renderStops();
  update();
})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

> 配色生成 → [配色ジェネレーター](/ja/tools/color-scheme-generator/)

> カラー変換 → [RGB⇔HEX変換](/ja/tools/rgb-hex-converter/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
