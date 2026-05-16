---
title: "プレースホルダー画像生成ツール - カスタムサイズ＆カラー"
date: 2025-05-16
description: "Web開発用プレースホルダー画像を無料で生成。サイズ・背景色・テキスト色・文字を自由にカスタマイズ。PNG ダウンロードまたはデータURLコピーに対応。"
categories: ["無料ツール"]
slug: "placeholder-generator"
ShowToc: false
cover:
  image: "/images/covers/placeholder-generator.png"
  alt: "プレースホルダー画像生成ツール"
---

<div id="pg-app">
<style>
#pg-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Noto Sans JP", sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
}
#pg-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
  color: #1a1a2e;
}
#pg-app .pg-layout {
  display: grid;
  grid-template-columns: 340px 1fr;
  gap: 1.5rem;
  align-items: start;
}
@media (max-width: 680px) {
  #pg-app .pg-layout {
    grid-template-columns: 1fr;
  }
}
#pg-app .pg-panel {
  background: #f8f9fc;
  border: 1px solid #e2e5f0;
  border-radius: 10px;
  padding: 1.25rem;
}
#pg-app .pg-field {
  margin-bottom: 1rem;
}
#pg-app .pg-field label {
  display: block;
  font-size: 0.78rem;
  font-weight: 600;
  color: #555;
  margin-bottom: 0.35rem;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#pg-app .pg-field input[type="number"],
#pg-app .pg-field input[type="text"] {
  width: 100%;
  padding: 0.5rem 0.7rem;
  border: 1px solid #d0d5e8;
  border-radius: 6px;
  font-size: 0.95rem;
  background: #fff;
  box-sizing: border-box;
  transition: border-color 0.2s;
}
#pg-app .pg-field input[type="number"]:focus,
#pg-app .pg-field input[type="text"]:focus {
  outline: none;
  border-color: #4f6ef7;
}
#pg-app .pg-size-row {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}
#pg-app .pg-size-row input {
  flex: 1;
}
#pg-app .pg-size-sep {
  font-weight: 700;
  color: #888;
  font-size: 1.1rem;
}
#pg-app .pg-color-row {
  display: flex;
  gap: 0.6rem;
  align-items: center;
}
#pg-app .pg-color-row input[type="color"] {
  width: 42px;
  height: 38px;
  border: 1px solid #d0d5e8;
  border-radius: 6px;
  padding: 2px;
  cursor: pointer;
  background: #fff;
  flex-shrink: 0;
}
#pg-app .pg-color-row input[type="text"] {
  flex: 1;
  font-family: monospace;
}
#pg-app .pg-presets-label {
  font-size: 0.78rem;
  font-weight: 600;
  color: #555;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.4rem;
}
#pg-app .pg-presets-group {
  margin-bottom: 0.9rem;
}
#pg-app .pg-presets-group-title {
  font-size: 0.72rem;
  font-weight: 700;
  color: #888;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.3rem;
}
#pg-app .pg-preset-btns {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
}
#pg-app .pg-preset-btn {
  background: #fff;
  border: 1px solid #d0d5e8;
  border-radius: 5px;
  padding: 0.28rem 0.6rem;
  font-size: 0.78rem;
  cursor: pointer;
  color: #333;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#pg-app .pg-preset-btn:hover {
  background: #4f6ef7;
  border-color: #4f6ef7;
  color: #fff;
}
#pg-app .pg-font-row {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}
#pg-app .pg-font-row input[type="number"] {
  width: 80px;
}
#pg-app .pg-font-row span {
  font-size: 0.85rem;
  color: #666;
}
#pg-app .pg-preview-area {
  background: #fff;
  border: 1px solid #e2e5f0;
  border-radius: 10px;
  padding: 1.25rem;
}
#pg-app .pg-canvas-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 200px;
  background: repeating-conic-gradient(#e8eaf0 0% 25%, #f5f6fa 0% 50%) 0 0 / 20px 20px;
  border-radius: 6px;
  margin-bottom: 1rem;
  overflow: hidden;
}
#pg-app #pg-canvas {
  display: block;
  max-width: 100%;
  max-height: 400px;
  border-radius: 3px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.12);
  object-fit: contain;
}
#pg-app .pg-info {
  font-size: 0.82rem;
  color: #666;
  margin-bottom: 1rem;
  text-align: center;
}
#pg-app .pg-btn-row {
  display: flex;
  gap: 0.7rem;
  flex-wrap: wrap;
}
#pg-app .pg-btn {
  flex: 1;
  min-width: 120px;
  padding: 0.65rem 1rem;
  border: none;
  border-radius: 7px;
  font-size: 0.92rem;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
}
#pg-app .pg-btn:hover {
  opacity: 0.88;
  transform: translateY(-1px);
}
#pg-app .pg-btn:active {
  transform: translateY(0);
}
#pg-app .pg-btn-primary {
  background: #4f6ef7;
  color: #fff;
}
#pg-app .pg-btn-secondary {
  background: #1a1a2e;
  color: #fff;
}
#pg-app .pg-url-box {
  margin-top: 1rem;
  background: #f0f2fa;
  border: 1px solid #d0d5e8;
  border-radius: 6px;
  padding: 0.6rem 0.8rem;
  font-size: 0.72rem;
  font-family: monospace;
  word-break: break-all;
  color: #333;
  max-height: 80px;
  overflow-y: auto;
  display: none;
}
#pg-app .pg-toast {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #1a1a2e;
  color: #fff;
  padding: 0.6rem 1.4rem;
  border-radius: 30px;
  font-size: 0.88rem;
  font-weight: 600;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s, transform 0.25s;
  z-index: 9999;
}
#pg-app .pg-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}
#pg-app .pg-cta {
  margin-top: 2rem;
  background: linear-gradient(135deg, #f0f4ff 0%, #e8f0fe 100%);
  border: 1px solid #c7d5f8;
  border-radius: 10px;
  padding: 1.2rem 1.4rem;
  font-size: 0.9rem;
  color: #1a1a2e;
  line-height: 1.6;
}
#pg-app .pg-cta strong {
  display: block;
  font-size: 0.95rem;
  margin-bottom: 0.4rem;
  color: #2d3e9e;
}
#pg-app .pg-cta a {
  color: #4f6ef7;
  font-weight: 600;
}
</style>

<div class="pg-layout">
  <div class="pg-panel">
    <h2>設定</h2>

    <div class="pg-field">
      <label>サイズ（px）</label>
      <div class="pg-size-row">
        <input type="number" id="pg-width" value="300" min="1" max="4000" />
        <span class="pg-size-sep">×</span>
        <input type="number" id="pg-height" value="250" min="1" max="4000" />
      </div>
    </div>

    <div class="pg-field">
      <div class="pg-presets-label">プリセット</div>

      <div class="pg-presets-group">
        <div class="pg-presets-group-title">よく使うサイズ</div>
        <div class="pg-preset-btns">
          <button class="pg-preset-btn" data-w="150" data-h="150">150×150</button>
          <button class="pg-preset-btn" data-w="300" data-h="250">300×250</button>
          <button class="pg-preset-btn" data-w="400" data-h="300">400×300</button>
          <button class="pg-preset-btn" data-w="800" data-h="600">800×600</button>
          <button class="pg-preset-btn" data-w="1200" data-h="630">1200×630</button>
          <button class="pg-preset-btn" data-w="1920" data-h="1080">1920×1080</button>
        </div>
      </div>

      <div class="pg-presets-group">
        <div class="pg-presets-group-title">SNS</div>
        <div class="pg-preset-btns">
          <button class="pg-preset-btn" data-w="820" data-h="312">FBカバー</button>
          <button class="pg-preset-btn" data-w="1500" data-h="500">Xヘッダー</button>
          <button class="pg-preset-btn" data-w="1080" data-h="1080">Instagram投稿</button>
          <button class="pg-preset-btn" data-w="1080" data-h="1920">Instagramストーリー</button>
          <button class="pg-preset-btn" data-w="1200" data-h="627">LinkedIn投稿</button>
          <button class="pg-preset-btn" data-w="1280" data-h="720">YouTubeサムネイル</button>
        </div>
      </div>

      <div class="pg-presets-group">
        <div class="pg-presets-group-title">広告バナー</div>
        <div class="pg-preset-btns">
          <button class="pg-preset-btn" data-w="728" data-h="90">リーダーボード</button>
          <button class="pg-preset-btn" data-w="300" data-h="600">ハーフページ</button>
          <button class="pg-preset-btn" data-w="160" data-h="600">スカイスクレイパー</button>
          <button class="pg-preset-btn" data-w="320" data-h="50">モバイルバナー</button>
          <button class="pg-preset-btn" data-w="468" data-h="60">フルバナー</button>
        </div>
      </div>
    </div>

    <div class="pg-field">
      <label>背景色</label>
      <div class="pg-color-row">
        <input type="color" id="pg-bg-picker" value="#cccccc" />
        <input type="text" id="pg-bg-hex" value="#cccccc" maxlength="7" />
      </div>
    </div>

    <div class="pg-field">
      <label>テキスト色</label>
      <div class="pg-color-row">
        <input type="color" id="pg-text-picker" value="#666666" />
        <input type="text" id="pg-text-hex" value="#666666" maxlength="7" />
      </div>
    </div>

    <div class="pg-field">
      <label>カスタムテキスト（空白で自動表示）</label>
      <input type="text" id="pg-custom-text" placeholder="例: ロゴここ" />
    </div>

    <div class="pg-field">
      <label>フォントサイズ（px）</label>
      <div class="pg-font-row">
        <input type="number" id="pg-font-size" value="0" min="0" max="500" />
        <span>0 = 自動</span>
      </div>
    </div>
  </div>

  <div class="pg-preview-area">
    <h2>プレビュー</h2>
    <div class="pg-canvas-wrap">
      <canvas id="pg-canvas"></canvas>
    </div>
    <div class="pg-info" id="pg-info">300 × 250 px</div>
    <div class="pg-btn-row">
      <button class="pg-btn pg-btn-primary" id="pg-download">PNG ダウンロード</button>
      <button class="pg-btn pg-btn-secondary" id="pg-copy-url">データURLをコピー</button>
    </div>
    <div class="pg-url-box" id="pg-url-box"></div>
  </div>
</div>

<div class="pg-toast" id="pg-toast">コピーしました！</div>

<div class="pg-cta">
  <strong>Web制作を効率化</strong>
  フリーランスのWeb制作者・デザイナーには、経理の自動化も大切です。<br>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freee会計でフリーランスの経理を自動化</a> して、制作に集中しましょう。
</div>

<script>
(function() {
  var canvas = document.getElementById('pg-canvas');
  var ctx = canvas.getContext('2d');
  var wInput = document.getElementById('pg-width');
  var hInput = document.getElementById('pg-height');
  var bgPicker = document.getElementById('pg-bg-picker');
  var bgHex = document.getElementById('pg-bg-hex');
  var textPicker = document.getElementById('pg-text-picker');
  var textHex = document.getElementById('pg-text-hex');
  var customText = document.getElementById('pg-custom-text');
  var fontSizeInput = document.getElementById('pg-font-size');
  var info = document.getElementById('pg-info');
  var urlBox = document.getElementById('pg-url-box');
  var toast = document.getElementById('pg-toast');

  function isValidHex(v) {
    return /^#[0-9a-fA-F]{6}$/.test(v);
  }

  function render() {
    var w = Math.max(1, Math.min(4000, parseInt(wInput.value) || 300));
    var h = Math.max(1, Math.min(4000, parseInt(hInput.value) || 250));
    var bg = isValidHex(bgHex.value) ? bgHex.value : '#cccccc';
    var tc = isValidHex(textHex.value) ? textHex.value : '#666666';
    var label = customText.value.trim() || (w + '\u00d7' + h);
    var fsRaw = parseInt(fontSizeInput.value) || 0;
    var fs = fsRaw > 0 ? fsRaw : Math.max(12, Math.min(Math.floor(Math.min(w, h) / 6), 72));

    canvas.width = w;
    canvas.height = h;

    ctx.fillStyle = bg;
    ctx.fillRect(0, 0, w, h);

    // Subtle diagonal lines
    ctx.strokeStyle = tc;
    ctx.globalAlpha = 0.08;
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(0, 0); ctx.lineTo(w, h);
    ctx.moveTo(w, 0); ctx.lineTo(0, h);
    ctx.stroke();
    ctx.globalAlpha = 1;

    // Border
    ctx.strokeStyle = tc;
    ctx.globalAlpha = 0.3;
    ctx.lineWidth = Math.max(1, Math.round(Math.min(w, h) / 100));
    ctx.strokeRect(ctx.lineWidth / 2, ctx.lineWidth / 2, w - ctx.lineWidth, h - ctx.lineWidth);
    ctx.globalAlpha = 1;

    // Text
    ctx.fillStyle = tc;
    ctx.font = 'bold ' + fs + 'px -apple-system, BlinkMacSystemFont, Arial, sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(label, w / 2, h / 2);

    info.textContent = w + ' \u00d7 ' + h + ' px';
  }

  function showToast(msg) {
    toast.textContent = msg;
    toast.classList.add('show');
    setTimeout(function() { toast.classList.remove('show'); }, 2000);
  }

  bgPicker.addEventListener('input', function() {
    bgHex.value = bgPicker.value;
    render();
  });
  bgHex.addEventListener('input', function() {
    if (isValidHex(bgHex.value)) bgPicker.value = bgHex.value;
    render();
  });
  textPicker.addEventListener('input', function() {
    textHex.value = textPicker.value;
    render();
  });
  textHex.addEventListener('input', function() {
    if (isValidHex(textHex.value)) textPicker.value = textHex.value;
    render();
  });

  [wInput, hInput, customText, fontSizeInput].forEach(function(el) {
    el.addEventListener('input', render);
  });

  document.querySelectorAll('#pg-app .pg-preset-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      wInput.value = btn.dataset.w;
      hInput.value = btn.dataset.h;
      render();
    });
  });

  document.getElementById('pg-download').addEventListener('click', function() {
    render();
    var link = document.createElement('a');
    link.download = 'placeholder-' + canvas.width + 'x' + canvas.height + '.png';
    link.href = canvas.toDataURL('image/png');
    link.click();
  });

  document.getElementById('pg-copy-url').addEventListener('click', function() {
    render();
    var dataUrl = canvas.toDataURL('image/png');
    urlBox.textContent = dataUrl;
    urlBox.style.display = 'block';
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(dataUrl).then(function() {
        showToast('データURLをコピーしました！');
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = dataUrl;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      showToast('データURLをコピーしました！');
    }
  });

  render();
})();
</script>
</div>
