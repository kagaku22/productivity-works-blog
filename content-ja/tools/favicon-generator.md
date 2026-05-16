---
title: "ファビコンジェネレーター — 無料オンラインツール"
date: 2025-05-16
description: "テキスト・図形・絵文字・画像アップロードからファビコンを作成。16x16・32x32のPNGを即時ダウンロード。登録不要・完全無料。"
categories: ["無料ツール"]
slug: "favicon-generator"
ShowToc: false
aliases:
  - "/ja/tools/favicon-maker/"
  - "/ja/tools/ico-generator/"
cover:
  image: "/images/covers/favicon-generator-ja.png"
  alt: "ファビコンジェネレーター"
---

ウェブサイト用のファビコンを数秒で作成できます。テキスト・絵文字・画像アップロードから選んで、すぐにPNGファイルをダウンロード。HTMLスニペットもコピーできます。

<div id="fav-app">

<style>
#fav-app *,
#fav-app *::before,
#fav-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#fav-app {
  font-family: system-ui, -apple-system, 'Hiragino Kaku Gothic ProN', 'Meiryo', sans-serif;
  max-width: 780px;
  color: #1e1b2e;
}

#fav-app .fav-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 24px;
  background: #f3f0ff;
  padding: 4px;
  border-radius: 10px;
}

#fav-app .fav-tab {
  flex: 1;
  padding: 9px 12px;
  border: none;
  background: transparent;
  border-radius: 7px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  color: #6b6b8a;
  transition: background 0.15s, color 0.15s;
}

#fav-app .fav-tab.active {
  background: #7c3aed;
  color: #fff;
}

#fav-app .fav-panel { display: none; }
#fav-app .fav-panel.active { display: block; }

#fav-app .fav-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}

@media (max-width: 540px) {
  #fav-app .fav-grid { grid-template-columns: 1fr; }
  #fav-app .fav-tabs { flex-direction: column; }
}

#fav-app label {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: #4b4569;
  margin-bottom: 6px;
}

#fav-app input[type="text"],
#fav-app input[type="number"],
#fav-app select,
#fav-app textarea {
  width: 100%;
  padding: 9px 11px;
  border: 1.5px solid #d4c9f8;
  border-radius: 8px;
  font-size: 15px;
  background: #faf9ff;
  color: #1e1b2e;
  outline: none;
  transition: border-color 0.15s;
}

#fav-app input[type="text"]:focus,
#fav-app input[type="number"]:focus,
#fav-app select:focus,
#fav-app textarea:focus {
  border-color: #7c3aed;
}

#fav-app input[type="color"] {
  width: 48px;
  height: 38px;
  border: 1.5px solid #d4c9f8;
  border-radius: 8px;
  padding: 2px;
  cursor: pointer;
  background: #faf9ff;
}

#fav-app .color-row {
  display: flex;
  align-items: center;
  gap: 10px;
}

#fav-app .color-row input[type="text"] {
  flex: 1;
  font-family: monospace;
}

#fav-app .shape-row {
  display: flex;
  gap: 8px;
}

#fav-app .shape-btn {
  flex: 1;
  padding: 8px 4px;
  border: 1.5px solid #d4c9f8;
  border-radius: 8px;
  background: #faf9ff;
  font-size: 13px;
  cursor: pointer;
  color: #4b4569;
  font-weight: 500;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
}

#fav-app .shape-btn.active {
  border-color: #7c3aed;
  background: #ede9fe;
  color: #7c3aed;
}

#fav-app .preview-section {
  background: #f8f6ff;
  border: 1.5px solid #e0d8fc;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
  text-align: center;
}

#fav-app .preview-section h3 {
  font-size: 13px;
  font-weight: 600;
  color: #6b6b8a;
  margin-bottom: 16px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

#fav-app .preview-canvases {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  gap: 24px;
  flex-wrap: wrap;
}

#fav-app .preview-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
}

#fav-app .preview-item span {
  font-size: 12px;
  color: #9490b2;
}

#fav-app canvas {
  image-rendering: pixelated;
  border-radius: 4px;
  box-shadow: 0 1px 4px rgba(124,58,237,0.12);
  background: transparent;
}

#fav-app .fav-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.15s, transform 0.1s;
  text-decoration: none;
}

#fav-app .fav-btn:active { transform: scale(0.97); }

#fav-app .btn-primary {
  background: #7c3aed;
  color: #fff;
}

#fav-app .btn-secondary {
  background: #ede9fe;
  color: #7c3aed;
}

#fav-app .btn-primary:hover { opacity: 0.88; }
#fav-app .btn-secondary:hover { opacity: 0.80; }

#fav-app .download-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}

#fav-app .meta-section {
  background: #1e1b2e;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 8px;
  position: relative;
}

#fav-app .meta-section pre {
  color: #c4b5fd;
  font-size: 13px;
  line-height: 1.6;
  white-space: pre-wrap;
  word-break: break-all;
  font-family: 'Menlo', 'Consolas', monospace;
}

#fav-app .copy-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 5px 12px;
  background: #7c3aed;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
}

#fav-app .copy-btn:hover { opacity: 0.85; }

#fav-app .upload-zone {
  border: 2px dashed #c4b5fd;
  border-radius: 10px;
  padding: 32px 16px;
  text-align: center;
  cursor: pointer;
  background: #faf9ff;
  margin-bottom: 16px;
  transition: background 0.15s, border-color 0.15s;
}

#fav-app .upload-zone:hover,
#fav-app .upload-zone.dragover {
  background: #ede9fe;
  border-color: #7c3aed;
}

#fav-app .upload-zone p {
  font-size: 14px;
  color: #6b6b8a;
  margin-top: 8px;
}

#fav-app .upload-icon {
  font-size: 36px;
  line-height: 1;
}

#fav-app .emoji-grid {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  gap: 6px;
  margin-bottom: 12px;
  max-height: 200px;
  overflow-y: auto;
  padding: 4px;
}

#fav-app .emoji-btn {
  font-size: 22px;
  background: #faf9ff;
  border: 1.5px solid #e0d8fc;
  border-radius: 7px;
  padding: 4px;
  cursor: pointer;
  text-align: center;
  line-height: 1.4;
  transition: background 0.1s, border-color 0.1s;
}

#fav-app .emoji-btn:hover { background: #ede9fe; border-color: #7c3aed; }
#fav-app .emoji-btn.active { background: #7c3aed; border-color: #7c3aed; }

#fav-app .emoji-custom {
  display: flex;
  gap: 10px;
  align-items: center;
  margin-bottom: 16px;
}

#fav-app .emoji-custom input {
  font-size: 22px;
  width: 60px;
  text-align: center;
}

#fav-app .section-divider {
  border: none;
  border-top: 1.5px solid #e0d8fc;
  margin: 20px 0;
}

#fav-app .info-text {
  font-size: 13px;
  color: #9490b2;
  margin-bottom: 14px;
}

#fav-app .fav-field { margin-bottom: 14px; }

#fav-app .range-row {
  display: flex;
  align-items: center;
  gap: 10px;
}

#fav-app .range-row input[type="range"] {
  flex: 1;
  accent-color: #7c3aed;
}

#fav-app .range-val {
  font-size: 14px;
  font-weight: 600;
  color: #7c3aed;
  min-width: 28px;
  text-align: right;
}

#fav-app .freee-cta {
  margin-top: 28px;
  background: linear-gradient(135deg, #f0edff 0%, #e8f4ff 100%);
  border: 1.5px solid #c4b5fd;
  border-radius: 12px;
  padding: 20px 24px;
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

#fav-app .freee-cta-text h4 {
  font-size: 15px;
  font-weight: 700;
  color: #1e1b2e;
  margin-bottom: 4px;
}

#fav-app .freee-cta-text p {
  font-size: 13px;
  color: #4b4569;
  line-height: 1.5;
}

#fav-app .freee-cta-icon {
  font-size: 32px;
  flex-shrink: 0;
}

#fav-app .freee-btn {
  display: inline-block;
  margin-top: 10px;
  padding: 9px 20px;
  background: #7c3aed;
  color: #fff;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  text-decoration: none;
  transition: opacity 0.15s;
}

#fav-app .freee-btn:hover { opacity: 0.85; }
</style>

<div class="fav-tabs">
  <button class="fav-tab active" onclick="favJaSwitchTab('text', this)">テキスト / 図形</button>
  <button class="fav-tab" onclick="favJaSwitchTab('emoji', this)">絵文字</button>
  <button class="fav-tab" onclick="favJaSwitchTab('upload', this)">画像アップロード</button>
</div>

<!-- テキストタブ -->
<div id="favja-panel-text" class="fav-panel active">
  <div class="fav-grid">
    <div>
      <div class="fav-field">
        <label for="favja-text">文字（1〜2文字）</label>
        <input type="text" id="favja-text" maxlength="2" value="FV" oninput="favJaRender()">
      </div>
      <div class="fav-field">
        <label>フォントサイズ</label>
        <div class="range-row">
          <input type="range" id="favja-fontsize" min="14" max="52" value="36" oninput="favJaRender(); document.getElementById('favja-fontsize-val').textContent=this.value">
          <span class="range-val" id="favja-fontsize-val">36</span>
        </div>
      </div>
      <div class="fav-field">
        <label>フォントウェイト</label>
        <select id="favja-fontweight" onchange="favJaRender()">
          <option value="700" selected>ボールド</option>
          <option value="900">ブラック（900）</option>
          <option value="400">レギュラー</option>
        </select>
      </div>
    </div>
    <div>
      <div class="fav-field">
        <label>形状</label>
        <div class="shape-row">
          <button class="shape-btn active" onclick="favJaSetShape('circle', this)">円形</button>
          <button class="shape-btn" onclick="favJaSetShape('rounded', this)">角丸</button>
          <button class="shape-btn" onclick="favJaSetShape('square', this)">正方形</button>
        </div>
      </div>
      <div class="fav-field">
        <label>背景色</label>
        <div class="color-row">
          <input type="color" id="favja-bg" value="#7c3aed" oninput="favJaSyncColor('bg')">
          <input type="text" id="favja-bg-hex" value="#7c3aed" maxlength="7" oninput="favJaSyncHex('bg')">
        </div>
      </div>
      <div class="fav-field">
        <label>文字色</label>
        <div class="color-row">
          <input type="color" id="favja-fg" value="#ffffff" oninput="favJaSyncColor('fg')">
          <input type="text" id="favja-fg-hex" value="#ffffff" maxlength="7" oninput="favJaSyncHex('fg')">
        </div>
      </div>
    </div>
  </div>
</div>

<!-- 絵文字タブ -->
<div id="favja-panel-emoji" class="fav-panel">
  <div class="fav-field">
    <label>絵文字を選択</label>
    <div class="emoji-grid" id="favja-emoji-grid"></div>
  </div>
  <div class="emoji-custom">
    <label style="white-space:nowrap; margin:0;">または入力：</label>
    <input type="text" id="favja-emoji-custom" maxlength="4" placeholder="例: 🚀" style="width:70px; font-size:22px; text-align:center;" oninput="favJaSetEmojiCustom(this.value)">
  </div>
  <div class="fav-field">
    <label>背景色</label>
    <div class="color-row">
      <input type="color" id="favja-emoji-bg" value="#7c3aed" oninput="favJaSyncEmojiColor()">
      <input type="text" id="favja-emoji-bg-hex" value="#7c3aed" maxlength="7" oninput="favJaSyncEmojiHex()">
    </div>
  </div>
  <div class="fav-field">
    <label>形状</label>
    <div class="shape-row">
      <button class="shape-btn active" id="favja-emoji-shape-circle" onclick="favJaSetEmojiShape('circle', this)">円形</button>
      <button class="shape-btn" id="favja-emoji-shape-rounded" onclick="favJaSetEmojiShape('rounded', this)">角丸</button>
      <button class="shape-btn" id="favja-emoji-shape-square" onclick="favJaSetEmojiShape('square', this)">正方形</button>
    </div>
  </div>
</div>

<!-- アップロードタブ -->
<div id="favja-panel-upload" class="fav-panel">
  <div class="upload-zone" id="favja-upload-zone" onclick="document.getElementById('favja-file-input').click()" ondragover="favJaDragOver(event)" ondragleave="favJaDragLeave(event)" ondrop="favJaDrop(event)">
    <div class="upload-icon">&#128444;</div>
    <p>クリックまたはドラッグ＆ドロップで画像を追加</p>
    <p style="font-size:12px; margin-top:4px;">PNG・JPG・GIF・SVG・WebP 対応</p>
  </div>
  <input type="file" id="favja-file-input" accept="image/*" style="display:none" onchange="favJaLoadFile(this)">
  <div class="fav-field" id="favja-crop-controls" style="display:none">
    <label>切り抜き / スケール調整</label>
    <div class="range-row">
      <input type="range" id="favja-crop-scale" min="10" max="200" value="100" oninput="favJaRenderUpload(); document.getElementById('favja-crop-scale-val').textContent=this.value+'%'">
      <span class="range-val" id="favja-crop-scale-val">100%</span>
    </div>
    <div class="range-row" style="margin-top:8px;">
      <label style="margin:0; min-width:80px;">横位置 (X)</label>
      <input type="range" id="favja-crop-x" min="-64" max="64" value="0" oninput="favJaRenderUpload()">
    </div>
    <div class="range-row" style="margin-top:8px;">
      <label style="margin:0; min-width:80px;">縦位置 (Y)</label>
      <input type="range" id="favja-crop-y" min="-64" max="64" value="0" oninput="favJaRenderUpload()">
    </div>
  </div>
</div>

<hr class="section-divider">

<!-- プレビュー -->
<div class="preview-section">
  <h3>リアルタイムプレビュー</h3>
  <div class="preview-canvases">
    <div class="preview-item">
      <canvas id="favja-canvas-64" width="64" height="64" style="width:64px;height:64px;"></canvas>
      <span>64×64（編集用）</span>
    </div>
    <div class="preview-item">
      <canvas id="favja-canvas-32" width="32" height="32" style="width:48px;height:48px;"></canvas>
      <span>32×32</span>
    </div>
    <div class="preview-item">
      <canvas id="favja-canvas-16" width="16" height="16" style="width:32px;height:32px;"></canvas>
      <span>16×16</span>
    </div>
  </div>
</div>

<!-- ダウンロード -->
<div class="download-row">
  <button class="fav-btn btn-primary" onclick="favJaDownload(32)">&#8615; 32×32 PNG をダウンロード</button>
  <button class="fav-btn btn-primary" onclick="favJaDownload(16)">&#8615; 16×16 PNG をダウンロード</button>
  <button class="fav-btn btn-secondary" onclick="favJaDownload(64)">&#8615; 64×64 PNG をダウンロード</button>
</div>

<!-- HTMLスニペット -->
<label>&lt;head&gt; に貼り付けるHTMLタグ</label>
<div class="meta-section">
  <button class="copy-btn" onclick="favJaCopyMeta()">コピー</button>
  <pre id="favja-meta-code"></pre>
</div>
<p class="info-text" id="favja-copy-msg" style="display:none; color:#7c3aed; font-weight:600;">クリップボードにコピーしました！</p>

<!-- freee CTA -->
<div class="freee-cta">
  <div class="freee-cta-icon">&#128176;</div>
  <div class="freee-cta-text">
    <h4>スモールビジネスの会計・請求書管理はfreeeで</h4>
    <p>ファビコンができたら次はサイトのビジネス基盤を整えましょう。freeeなら請求書の発行・経費管理・確定申告まで一括管理。はじめての方も安心のサポート付き。</p>
    <a class="freee-btn" href="https://www.freee.co.jp/" target="_blank" rel="noopener">freeeを無料で試してみる &rarr;</a>
  </div>
</div>

</div><!-- #fav-app -->

<script>
(function() {
  var _currentTab = 'text';
  var _shape = 'circle';
  var _emojiShape = 'circle';
  var _selectedEmoji = '⭐';
  var _uploadImg = null;

  var EMOJIS = [
    '⭐','🚀','💡','🎨','🔥','✨','🌟','💎',
    '🎯','📌','🛠','⚡','🧩','🏆','🎉','💬',
    '🔑','🌈','🌀','🦋','🐉','🍀','🌸','🎵',
    '💻','📱','🖥','🔒','🛡','🤖','🧠','👾',
    '📊','📈','💰','🏠','✈️','🌍','⚙️','🔧'
  ];

  function init() {
    buildEmojiGrid();
    favJaRender();
    updateMeta();
  }

  function buildEmojiGrid() {
    var grid = document.getElementById('favja-emoji-grid');
    EMOJIS.forEach(function(em) {
      var btn = document.createElement('button');
      btn.className = 'emoji-btn' + (em === _selectedEmoji ? ' active' : '');
      btn.textContent = em;
      btn.onclick = function() {
        _selectedEmoji = em;
        document.querySelectorAll('#favja-emoji-grid .emoji-btn').forEach(function(b){ b.classList.remove('active'); });
        btn.classList.add('active');
        document.getElementById('favja-emoji-custom').value = '';
        favJaRenderEmoji();
        updateMeta();
      };
      grid.appendChild(btn);
    });
  }

  window.favJaSwitchTab = function(tab, btn) {
    _currentTab = tab;
    document.querySelectorAll('#fav-app .fav-tab').forEach(function(b){ b.classList.remove('active'); });
    btn.classList.add('active');
    document.querySelectorAll('#fav-app .fav-panel').forEach(function(p){ p.classList.remove('active'); });
    document.getElementById('favja-panel-' + tab).classList.add('active');
    favJaRenderAll();
    updateMeta();
  };

  window.favJaSetShape = function(s, btn) {
    _shape = s;
    document.querySelectorAll('#favja-panel-text .shape-btn').forEach(function(b){ b.classList.remove('active'); });
    btn.classList.add('active');
    favJaRender();
  };

  window.favJaSetEmojiShape = function(s, btn) {
    _emojiShape = s;
    ['circle','rounded','square'].forEach(function(sh){
      var el = document.getElementById('favja-emoji-shape-' + sh);
      if(el) el.classList.remove('active');
    });
    btn.classList.add('active');
    favJaRenderEmoji();
  };

  window.favJaSyncColor = function(which) {
    var col = document.getElementById('favja-' + which).value;
    document.getElementById('favja-' + which + '-hex').value = col;
    favJaRender();
  };

  window.favJaSyncHex = function(which) {
    var val = document.getElementById('favja-' + which + '-hex').value;
    if (/^#[0-9a-fA-F]{6}$/.test(val)) {
      document.getElementById('favja-' + which).value = val;
      favJaRender();
    }
  };

  window.favJaSyncEmojiColor = function() {
    var col = document.getElementById('favja-emoji-bg').value;
    document.getElementById('favja-emoji-bg-hex').value = col;
    favJaRenderEmoji();
  };

  window.favJaSyncEmojiHex = function() {
    var val = document.getElementById('favja-emoji-bg-hex').value;
    if (/^#[0-9a-fA-F]{6}$/.test(val)) {
      document.getElementById('favja-emoji-bg').value = val;
      favJaRenderEmoji();
    }
  };

  window.favJaSetEmojiCustom = function(val) {
    if (val.trim()) {
      _selectedEmoji = val.trim();
      document.querySelectorAll('#favja-emoji-grid .emoji-btn').forEach(function(b){ b.classList.remove('active'); });
      favJaRenderEmoji();
      updateMeta();
    }
  };

  function drawBackground(ctx, size, shape, color) {
    ctx.clearRect(0, 0, size, size);
    ctx.fillStyle = color;
    if (shape === 'circle') {
      ctx.beginPath();
      ctx.arc(size/2, size/2, size/2, 0, Math.PI*2);
      ctx.fill();
    } else if (shape === 'rounded') {
      var r = size * 0.22;
      ctx.beginPath();
      ctx.moveTo(r, 0);
      ctx.lineTo(size-r, 0);
      ctx.quadraticCurveTo(size, 0, size, r);
      ctx.lineTo(size, size-r);
      ctx.quadraticCurveTo(size, size, size-r, size);
      ctx.lineTo(r, size);
      ctx.quadraticCurveTo(0, size, 0, size-r);
      ctx.lineTo(0, r);
      ctx.quadraticCurveTo(0, 0, r, 0);
      ctx.closePath();
      ctx.fill();
    } else {
      ctx.fillRect(0, 0, size, size);
    }
  }

  function scaleDown(srcCanvas, destCanvas) {
    var ctx = destCanvas.getContext('2d');
    ctx.clearRect(0, 0, destCanvas.width, destCanvas.height);
    ctx.imageSmoothingEnabled = true;
    ctx.imageSmoothingQuality = 'high';
    ctx.drawImage(srcCanvas, 0, 0, destCanvas.width, destCanvas.height);
  }

  window.favJaRender = function() {
    if (_currentTab !== 'text') return;
    var text = document.getElementById('favja-text').value || 'FV';
    var fontSize = parseInt(document.getElementById('favja-fontsize').value);
    var fontWeight = document.getElementById('favja-fontweight').value;
    var bgColor = document.getElementById('favja-bg').value;
    var fgColor = document.getElementById('favja-fg').value;

    var c64 = document.getElementById('favja-canvas-64');
    var ctx = c64.getContext('2d');
    drawBackground(ctx, 64, _shape, bgColor);

    ctx.fillStyle = fgColor;
    ctx.font = fontWeight + ' ' + fontSize + 'px system-ui, -apple-system, sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(text.substring(0,2), 32, 34);

    scaleDown(c64, document.getElementById('favja-canvas-32'));
    scaleDown(c64, document.getElementById('favja-canvas-16'));
    updateMeta();
  };

  function favJaRenderEmoji() {
    var emoji = _selectedEmoji || '⭐';
    var bgColor = document.getElementById('favja-emoji-bg').value;

    var c64 = document.getElementById('favja-canvas-64');
    var ctx = c64.getContext('2d');
    drawBackground(ctx, 64, _emojiShape, bgColor);

    ctx.font = '40px serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText(emoji, 32, 34);

    scaleDown(c64, document.getElementById('favja-canvas-32'));
    scaleDown(c64, document.getElementById('favja-canvas-16'));
    updateMeta();
  }

  window.favJaRenderUpload = function() {
    if (!_uploadImg) return;
    var c64 = document.getElementById('favja-canvas-64');
    var ctx = c64.getContext('2d');
    ctx.clearRect(0, 0, 64, 64);

    var scale = parseInt(document.getElementById('favja-crop-scale').value) / 100;
    var ox = parseInt(document.getElementById('favja-crop-x').value);
    var oy = parseInt(document.getElementById('favja-crop-y').value);
    var w = _uploadImg.naturalWidth * scale;
    var h = _uploadImg.naturalHeight * scale;
    var x = (64 - w) / 2 + ox;
    var y = (64 - h) / 2 + oy;
    ctx.drawImage(_uploadImg, x, y, w, h);

    scaleDown(c64, document.getElementById('favja-canvas-32'));
    scaleDown(c64, document.getElementById('favja-canvas-16'));
    updateMeta();
  };

  function favJaRenderAll() {
    if (_currentTab === 'text') favJaRender();
    else if (_currentTab === 'emoji') favJaRenderEmoji();
    else if (_currentTab === 'upload' && _uploadImg) favJaRenderUpload();
  }

  window.favJaDownload = function(size) {
    var src = document.getElementById('favja-canvas-64');
    var tmp = document.createElement('canvas');
    tmp.width = size;
    tmp.height = size;
    var ctx = tmp.getContext('2d');
    ctx.imageSmoothingEnabled = true;
    ctx.imageSmoothingQuality = 'high';
    ctx.drawImage(src, 0, 0, size, size);
    var a = document.createElement('a');
    a.download = 'favicon-' + size + 'x' + size + '.png';
    a.href = tmp.toDataURL('image/png');
    a.click();
  };

  function updateMeta() {
    var code = '<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">\n' +
               '<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">\n' +
               '<link rel="shortcut icon" href="/favicon.ico">';
    document.getElementById('favja-meta-code').textContent = code;
  }

  window.favJaCopyMeta = function() {
    var text = document.getElementById('favja-meta-code').textContent;
    navigator.clipboard.writeText(text).then(function() {
      var msg = document.getElementById('favja-copy-msg');
      msg.style.display = 'block';
      setTimeout(function(){ msg.style.display = 'none'; }, 2000);
    });
  };

  window.favJaDragOver = function(e) {
    e.preventDefault();
    document.getElementById('favja-upload-zone').classList.add('dragover');
  };

  window.favJaDragLeave = function(e) {
    document.getElementById('favja-upload-zone').classList.remove('dragover');
  };

  window.favJaDrop = function(e) {
    e.preventDefault();
    document.getElementById('favja-upload-zone').classList.remove('dragover');
    var file = e.dataTransfer.files[0];
    if (file && file.type.startsWith('image/')) processImageFile(file);
  };

  window.favJaLoadFile = function(input) {
    if (input.files && input.files[0]) processImageFile(input.files[0]);
  };

  function processImageFile(file) {
    var reader = new FileReader();
    reader.onload = function(e) {
      var img = new Image();
      img.onload = function() {
        _uploadImg = img;
        document.getElementById('favja-crop-controls').style.display = 'block';
        favJaRenderUpload();
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }

  init();
})();
</script>
