---
title: "Base64→画像変換ツール"
slug: "base64-to-image"
date: 2025-05-16
description: "無料のBase64→画像デコーダー。Base64文字列を貼り付けて画像をプレビュー・ダウンロード。登録不要。"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: "/images/covers/base64-to-image-ja.png"
  alt: "Base64→画像変換ツールのスクリーンショット"
---

ブラウザだけで完結するBase64デコーダーです。data URI付きでもプレーンなBase64文字列でも貼り付けるだけで画像をプレビュー・ダウンロードできます。アップロード不要・サーバー送信なし・登録不要。

<div id="bd-app">

<style>
#bd-app *,
#bd-app *::before,
#bd-app *::after {
  box-sizing: border-box;
}
#bd-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1a1a2e;
}
#bd-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 1.6rem 0 0.5rem;
  color: #1a1a2e;
}
#bd-app .bd-row {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  align-items: center;
  margin-bottom: 0.75rem;
}
#bd-app textarea {
  width: 100%;
  min-height: 160px;
  padding: 0.75rem;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.8rem;
  line-height: 1.5;
  border: 1.5px solid #c8ccd4;
  border-radius: 8px;
  resize: vertical;
  background: #f8f9fb;
  color: #1a1a2e;
  transition: border-color 0.2s;
}
#bd-app textarea:focus {
  outline: none;
  border-color: #4f6ef7;
  background: #fff;
}
#bd-app textarea::placeholder {
  color: #9aa0ad;
}
#bd-app button {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.55rem 1.15rem;
  font-size: 0.9rem;
  font-weight: 700;
  border: none;
  border-radius: 7px;
  cursor: pointer;
  transition: background 0.18s, opacity 0.18s;
}
#bd-app button:active { opacity: 0.82; }
#bd-app .bd-btn-primary { background: #4f6ef7; color: #fff; }
#bd-app .bd-btn-primary:hover { background: #3a58e0; }
#bd-app .bd-btn-secondary { background: #eef0f8; color: #4f6ef7; border: 1.5px solid #c8ccd4; }
#bd-app .bd-btn-secondary:hover { background: #dde1f5; }
#bd-app .bd-btn-danger { background: #fff0f0; color: #d9534f; border: 1.5px solid #f5c6c6; }
#bd-app .bd-btn-danger:hover { background: #ffe0e0; }
#bd-app .bd-btn-green { background: #1db954; color: #fff; }
#bd-app .bd-btn-green:hover { background: #17a348; }
#bd-app .bd-status {
  padding: 0.55rem 0.85rem;
  border-radius: 7px;
  font-size: 0.875rem;
  font-weight: 500;
  margin-bottom: 0.75rem;
  display: none;
}
#bd-app .bd-status.info  { display: block; background: #eef3ff; color: #3a58e0; border: 1px solid #c5d1fb; }
#bd-app .bd-status.error { display: block; background: #fff0f0; color: #c0392b; border: 1px solid #f5c6c6; }
#bd-app .bd-status.ok    { display: block; background: #eafaf1; color: #1a7a43; border: 1px solid #a9dfbf; }
#bd-app .bd-preview-box {
  display: none;
  border: 1.5px solid #c8ccd4;
  border-radius: 10px;
  overflow: hidden;
  background: repeating-conic-gradient(#e0e0e0 0% 25%, #f8f8f8 0% 50%) 0 0 / 16px 16px;
  text-align: center;
  padding: 12px;
  margin-bottom: 0.75rem;
  min-height: 80px;
}
#bd-app .bd-preview-box img {
  max-width: 100%;
  max-height: 480px;
  display: block;
  margin: 0 auto;
  border-radius: 4px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.12);
}
#bd-app .bd-meta {
  display: none;
  background: #f4f6fb;
  border: 1.5px solid #dde2ef;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  font-size: 0.85rem;
  margin-bottom: 0.75rem;
  line-height: 1.7;
}
#bd-app .bd-meta span { display: inline-block; margin-right: 1.5rem; }
#bd-app .bd-meta strong { color: #4f6ef7; }
#bd-app .bd-copy-uri {
  font-family: "SFMono-Regular", Consolas, monospace;
  font-size: 0.78rem;
  background: #f4f6fb;
  border: 1.5px solid #dde2ef;
  border-radius: 7px;
  padding: 0.55rem 0.8rem;
  width: 100%;
  resize: none;
  height: 3.8rem;
  color: #444;
  display: none;
  margin-bottom: 0.4rem;
}
#bd-app .bd-divider { border: none; border-top: 1.5px solid #eaecf2; margin: 1.4rem 0; }
#bd-app .bd-how {
  background: #f8f9fb;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  font-size: 0.88rem;
  line-height: 1.85;
  color: #444;
}
#bd-app .bd-how ol { margin: 0.4rem 0 0 1.2rem; padding: 0; }
#bd-app .bd-how li { margin-bottom: 0.3rem; }
#bd-app .bd-links {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-top: 1.2rem;
}
#bd-app .bd-links a {
  padding: 0.45rem 1rem;
  background: #eef0f8;
  color: #4f6ef7;
  border-radius: 6px;
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 600;
  border: 1.5px solid #c8ccd4;
  transition: background 0.15s;
}
#bd-app .bd-links a:hover { background: #dde1f5; }
/* freee CTA */
#bd-app .bd-freee-cta {
  margin: 1.8rem 0 0;
  padding: 1.2rem 1.4rem;
  background: linear-gradient(135deg, #e8f4fd 0%, #f0f8ff 100%);
  border: 1.5px solid #b3d9f5;
  border-radius: 12px;
}
#bd-app .bd-freee-cta h3 {
  margin: 0 0 0.5rem;
  font-size: 1rem;
  color: #1a5276;
}
#bd-app .bd-freee-cta p {
  margin: 0 0 0.8rem;
  font-size: 0.875rem;
  color: #2c3e50;
  line-height: 1.65;
}
#bd-app .bd-freee-cta a.bd-freee-btn {
  display: inline-block;
  background: #0078d4;
  color: #fff;
  font-weight: 700;
  font-size: 0.9rem;
  padding: 0.6rem 1.4rem;
  border-radius: 7px;
  text-decoration: none;
  transition: background 0.18s;
}
#bd-app .bd-freee-cta a.bd-freee-btn:hover { background: #005fa3; }
/* A8 footer */
#bd-app .bd-a8-footer {
  margin-top: 1.6rem;
  padding: 0.75rem 1rem;
  background: #fafafa;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  font-size: 0.78rem;
  color: #777;
  line-height: 1.6;
}
#bd-app .bd-a8-footer a { color: #4f6ef7; text-decoration: underline; }
</style>

<h2>Base64文字列を貼り付け</h2>

<textarea id="bd-input" placeholder="Base64文字列をここに貼り付けてください。data:image/png;base64, のようなdata URIプレフィックスは自動で取り除かれます。改行・空白も自動除去します。"></textarea>

<div class="bd-row">
  <button class="bd-btn-primary" onclick="bdDecode()">&#9654; デコードしてプレビュー</button>
  <button class="bd-btn-secondary" onclick="bdPasteSample()">サンプルを読み込む</button>
  <button class="bd-btn-danger" onclick="bdClear()">&#10005; クリア</button>
</div>

<div id="bd-status" class="bd-status"></div>

<div id="bd-preview-box" class="bd-preview-box">
  <img id="bd-img" src="" alt="デコードした画像プレビュー" />
</div>

<div id="bd-meta" class="bd-meta">
  <span>フォーマット: <strong id="bd-fmt">—</strong></span>
  <span>サイズ: <strong id="bd-dims">—</strong></span>
  <span>デコード後バイト数: <strong id="bd-size">—</strong></span>
</div>

<div id="bd-action-row" class="bd-row" style="display:none">
  <button class="bd-btn-green" onclick="bdDownload()">&#8595; 画像をダウンロード</button>
  <button class="bd-btn-secondary" onclick="bdCopyUri()">&#128203; data URIをコピー</button>
</div>

<textarea id="bd-uri-out" class="bd-copy-uri" readonly></textarea>

<hr class="bd-divider" />

<h2>使い方</h2>
<div class="bd-how">
  <ol>
    <li>Base64文字列をテキストエリアに貼り付けます。</li>
    <li><code>data:image/...;base64,</code> のプレフィックスは自動検出・除去されます。改行や空白も自動的に取り除かれます。</li>
    <li>ブラウザ内でデコードし、画像フォーマット（PNG / JPEG / GIF / WebP / SVG など）を自動判定してプレビュー表示します。</li>
    <li>フォーマット・ピクセルサイズ・バイト数を確認できます。</li>
    <li>「画像をダウンロード」で画像ファイルを保存、または data URI をクリップボードへコピーできます。</li>
  </ol>
</div>

<div class="bd-links">
  <a href="/tools/image-to-base64/">&#8592; 画像→Base64変換</a>
  <a href="/tools/base64-encoder/">Base64エンコーダー</a>
</div>

<div class="bd-freee-cta">
  <h3>経理・会計の効率化も自動化しませんか？</h3>
  <p>freee会計は、請求書・領収書の管理から確定申告・法人決算まで自動化できるクラウド会計ソフトです。銀行口座・クレジットカードと連携して仕訳を自動作成。今なら30日間無料でお試しいただけます。</p>
  <a class="bd-freee-btn" href="https://www.freee.co.jp/" target="_blank" rel="noopener noreferrer">freee会計を無料で試す</a>
</div>

<script>
(function () {
  'use strict';

  var SAMPLE = 'iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mP8z8BQDwADhQGAWjR9awAAAABJRU5ErkJggg==';

  function showStatus(msg, type) {
    var el = document.getElementById('bd-status');
    el.textContent = msg;
    el.className = 'bd-status ' + type;
  }

  function hideStatus() {
    document.getElementById('bd-status').className = 'bd-status';
  }

  function formatBytes(n) {
    if (n < 1024) return n + ' B';
    if (n < 1024 * 1024) return (n / 1024).toFixed(1) + ' KB';
    return (n / (1024 * 1024)).toFixed(2) + ' MB';
  }

  function detectMime(b64clean) {
    try {
      var raw = atob(b64clean.substring(0, 16));
      var bytes = [];
      for (var i = 0; i < raw.length; i++) bytes.push(raw.charCodeAt(i));
      if (bytes[0] === 0x89 && bytes[1] === 0x50) return 'image/png';
      if (bytes[0] === 0xFF && bytes[1] === 0xD8) return 'image/jpeg';
      if (bytes[0] === 0x47 && bytes[1] === 0x49) return 'image/gif';
      if (bytes[0] === 0x52 && bytes[1] === 0x49 && bytes[8] === 0x57) return 'image/webp';
      if (bytes[0] === 0x42 && bytes[1] === 0x4D) return 'image/bmp';
      if (bytes[0] === 0x00 && bytes[1] === 0x00 && bytes[2] === 0x01) return 'image/x-icon';
    } catch (e) {}
    var preview = atob(b64clean.substring(0, 64));
    if (preview.indexOf('<svg') !== -1 || preview.indexOf('<?xml') !== -1) return 'image/svg+xml';
    return 'image/png';
  }

  function mimeToExt(mime) {
    var map = { 'image/png':'png','image/jpeg':'jpg','image/gif':'gif','image/webp':'webp','image/bmp':'bmp','image/svg+xml':'svg','image/x-icon':'ico' };
    return map[mime] || 'png';
  }

  function mimeToLabel(mime) {
    var map = { 'image/png':'PNG','image/jpeg':'JPEG','image/gif':'GIF','image/webp':'WebP','image/bmp':'BMP','image/svg+xml':'SVG','image/x-icon':'ICO' };
    return map[mime] || mime;
  }

  window.bdDecode = function () {
    var raw = document.getElementById('bd-input').value.trim();
    if (!raw) { showStatus('Base64文字列を貼り付けてください。', 'info'); return; }

    var b64 = raw;
    var detectedMime = null;
    var prefixMatch = raw.match(/^data:([^;]+);base64,(.+)$/s);
    if (prefixMatch) {
      detectedMime = prefixMatch[1].trim();
      b64 = prefixMatch[2].trim();
    }
    b64 = b64.replace(/\s+/g, '');

    if (!/^[A-Za-z0-9+/]+=*$/.test(b64)) {
      showStatus('不正なBase64文字列です。使用できない文字が含まれています。', 'error');
      return;
    }

    var mime = detectedMime || detectMime(b64);
    var dataUri = 'data:' + mime + ';base64,' + b64;

    var img = document.getElementById('bd-img');
    img.onload = function () {
      var pad = (b64.slice(-2) === '==' ? 2 : b64.slice(-1) === '=' ? 1 : 0);
      var byteLen = (b64.length * 3 / 4) - pad;

      document.getElementById('bd-fmt').textContent = mimeToLabel(mime);
      document.getElementById('bd-dims').textContent = img.naturalWidth + ' × ' + img.naturalHeight + ' px';
      document.getElementById('bd-size').textContent = formatBytes(byteLen);

      document.getElementById('bd-meta').style.display = 'block';
      document.getElementById('bd-preview-box').style.display = 'block';
      document.getElementById('bd-action-row').style.display = 'flex';
      document.getElementById('bd-uri-out').style.display = 'none';

      showStatus('デコード成功 — フォーマット: ' + mimeToLabel(mime) + '、' + img.naturalWidth + '×' + img.naturalHeight + ' px', 'ok');
    };
    img.onerror = function () {
      document.getElementById('bd-preview-box').style.display = 'none';
      document.getElementById('bd-meta').style.display = 'none';
      document.getElementById('bd-action-row').style.display = 'none';
      showStatus('画像を表示できませんでした。Base64データが壊れているか、未対応のフォーマットの可能性があります。', 'error');
    };
    img.src = dataUri;
    hideStatus();
  };

  window.bdDownload = function () {
    var img = document.getElementById('bd-img');
    if (!img.src) return;
    var mimeMatch = img.src.match(/^data:([^;]+);/);
    var mime = mimeMatch ? mimeMatch[1] : 'image/png';
    var ext = mimeToExt(mime);
    var a = document.createElement('a');
    a.href = img.src;
    a.download = 'decoded-image.' + ext;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  };

  window.bdCopyUri = function () {
    var img = document.getElementById('bd-img');
    if (!img.src) return;
    var out = document.getElementById('bd-uri-out');
    out.value = img.src;
    out.style.display = 'block';
    if (navigator.clipboard) {
      navigator.clipboard.writeText(img.src).then(function () {
        showStatus('data URIをクリップボードにコピーしました。', 'ok');
      }).catch(function () {
        out.select();
        showStatus('上のテキストを手動でコピーしてください。', 'info');
      });
    } else {
      out.select();
      try { document.execCommand('copy'); showStatus('data URIをクリップボードにコピーしました。', 'ok'); }
      catch (e) { showStatus('上のテキストを手動でコピーしてください。', 'info'); }
    }
  };

  window.bdPasteSample = function () {
    document.getElementById('bd-input').value = SAMPLE;
    showStatus('サンプルBase64を読み込みました（1×1 赤PNG）。「デコードしてプレビュー」をクリックしてください。', 'info');
  };

  window.bdClear = function () {
    document.getElementById('bd-input').value = '';
    document.getElementById('bd-img').src = '';
    document.getElementById('bd-preview-box').style.display = 'none';
    document.getElementById('bd-meta').style.display = 'none';
    document.getElementById('bd-action-row').style.display = 'none';
    document.getElementById('bd-uri-out').style.display = 'none';
    document.getElementById('bd-uri-out').value = '';
    hideStatus();
  };
})();
</script>

<div class="bd-a8-footer">
  ※本記事にはアフィリエイト広告が含まれる場合があります。掲載している商品・サービスの選定はコンテンツ編集部が行っており、広告主の意向に関わらず独自の基準で選んでいます。<br>
  <a href="https://www.a8.net/" target="_blank" rel="noopener noreferrer">A8.net</a> 提携広告プログラムに参加しています。
</div>

</div>
