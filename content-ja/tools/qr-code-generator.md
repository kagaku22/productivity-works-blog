---
title: "QRコードジェネレーター"
date: 2025-05-16
description: "無料のQRコード作成ツール。URL・テキスト・WiFi・メールアドレスのQRコードをブラウザで即生成。PNG/SVGダウンロード対応、会員登録不要。"
categories: ["無料ツール"]
slug: "qr-code-generator"
ShowToc: false
cover:
  image: "/images/covers/qr-code-generator-ja.png"
  alt: "QRコードジェネレーター"
---

URLやテキスト、WiFi情報などをQRコードに変換できる無料ツールです。ブラウザ上で即座に生成でき、PNG・SVG形式でダウンロードも可能です。

<div id="qr-app">
<style>
#qr-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
}
#qr-app * {
  box-sizing: border-box;
}
#qr-app .qr-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 18px;
  flex-wrap: wrap;
}
#qr-app .qr-tab {
  padding: 8px 18px;
  border-radius: 7px;
  border: 1.5px solid #cbd5e1;
  background: #f8fafc;
  color: #475569;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
#qr-app .qr-tab:hover {
  border-color: #94a3b8;
  background: #f1f5f9;
}
#qr-app .qr-tab.active {
  background: #0f172a;
  color: #fff;
  border-color: #0f172a;
}
#qr-app .qr-panel {
  display: none;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 18px;
}
#qr-app .qr-panel.active {
  display: flex;
}
#qr-app .qr-field-label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
  margin-bottom: 3px;
  display: block;
}
#qr-app input[type="text"],
#qr-app input[type="email"],
#qr-app input[type="password"],
#qr-app textarea,
#qr-app select {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 14px;
  color: #1e293b;
  background: #f8fafc;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}
#qr-app input[type="text"]:focus,
#qr-app input[type="email"]:focus,
#qr-app input[type="password"]:focus,
#qr-app textarea:focus,
#qr-app select:focus {
  border-color: #64748b;
  background: #fff;
}
#qr-app textarea {
  resize: vertical;
  min-height: 80px;
}
#qr-app .qr-form-row {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
#qr-app .qr-customize {
  background: #f1f5f9;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 18px;
  display: flex;
  flex-wrap: wrap;
  gap: 18px;
  align-items: flex-end;
}
#qr-app .qr-customize-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
  min-width: 140px;
  flex: 1;
}
#qr-app .qr-customize-group .qr-field-label {
  font-size: 13px;
  font-weight: 600;
  color: #374151;
}
#qr-app input[type="range"] {
  width: 100%;
  accent-color: #0f172a;
}
#qr-app .qr-size-val {
  font-size: 13px;
  color: #64748b;
  font-weight: 600;
}
#qr-app .qr-color-row {
  display: flex;
  align-items: center;
  gap: 8px;
}
#qr-app input[type="color"] {
  width: 38px;
  height: 32px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  padding: 2px;
  cursor: pointer;
  background: #fff;
}
#qr-app .qr-preview-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
  margin-bottom: 18px;
}
#qr-app #qr-canvas {
  border-radius: 10px;
  box-shadow: 0 2px 12px rgba(15,23,42,0.10);
  display: block;
  max-width: 100%;
}
#qr-app .qr-btn-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
}
#qr-app .qr-btn {
  padding: 10px 24px;
  border-radius: 8px;
  border: none;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  font-family: inherit;
}
#qr-app .qr-btn:active {
  transform: scale(0.97);
}
#qr-app .qr-btn-secondary {
  background: #e2e8f0;
  color: #1e293b;
}
#qr-app .qr-btn-secondary:hover {
  background: #cbd5e1;
}
#qr-app .qr-status {
  font-size: 13px;
  color: #64748b;
  text-align: center;
  min-height: 18px;
}
#qr-app .qr-error {
  color: #dc2626;
  font-size: 13px;
  text-align: center;
}
@media (max-width: 480px) {
  #qr-app .qr-customize {
    flex-direction: column;
  }
  #qr-app .qr-btn {
    width: 100%;
    text-align: center;
  }
}
</style>

<div class="qr-tabs">
  <button class="qr-tab active" data-tab="url">URL</button>
  <button class="qr-tab" data-tab="text">テキスト</button>
  <button class="qr-tab" data-tab="wifi">WiFi</button>
  <button class="qr-tab" data-tab="email">メール</button>
</div>

<!-- URL パネル -->
<div class="qr-panel active" id="panel-url">
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-url">URL</label>
    <input type="text" id="qr-url" placeholder="https://example.com" value="https://productivity-works.com">
  </div>
</div>

<!-- テキスト パネル -->
<div class="qr-panel" id="panel-text">
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-text">テキスト</label>
    <textarea id="qr-text" placeholder="ここにテキストを入力してください"></textarea>
  </div>
</div>

<!-- WiFi パネル -->
<div class="qr-panel" id="panel-wifi">
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-wifi-ssid">SSID（ネットワーク名）</label>
    <input type="text" id="qr-wifi-ssid" placeholder="MyNetwork">
  </div>
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-wifi-pass">パスワード</label>
    <input type="password" id="qr-wifi-pass" placeholder="パスワード">
  </div>
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-wifi-enc">暗号化方式</label>
    <select id="qr-wifi-enc">
      <option value="WPA">WPA/WPA2</option>
      <option value="WEP">WEP</option>
      <option value="nopass">なし</option>
    </select>
  </div>
</div>

<!-- メール パネル -->
<div class="qr-panel" id="panel-email">
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-email-to">メールアドレス</label>
    <input type="email" id="qr-email-to" placeholder="example@example.com">
  </div>
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-email-subj">件名</label>
    <input type="text" id="qr-email-subj" placeholder="件名">
  </div>
  <div class="qr-form-row">
    <label class="qr-field-label" for="qr-email-body">本文</label>
    <textarea id="qr-email-body" placeholder="メール本文"></textarea>
  </div>
</div>

<!-- カスタマイズ -->
<div class="qr-customize">
  <div class="qr-customize-group">
    <label class="qr-field-label">サイズ: <span class="qr-size-val" id="qr-size-label">300px</span></label>
    <input type="range" id="qr-size" min="200" max="600" step="10" value="300">
  </div>
  <div class="qr-customize-group">
    <label class="qr-field-label">前景色</label>
    <div class="qr-color-row">
      <input type="color" id="qr-fg" value="#000000">
      <span style="font-size:13px;color:#64748b;">文字・モジュール色</span>
    </div>
  </div>
  <div class="qr-customize-group">
    <label class="qr-field-label">背景色</label>
    <div class="qr-color-row">
      <input type="color" id="qr-bg" value="#ffffff">
      <span style="font-size:13px;color:#64748b;">背景色</span>
    </div>
  </div>
</div>

<!-- プレビュー -->
<div class="qr-preview-area">
  <canvas id="qr-canvas" width="300" height="300"></canvas>
  <div class="qr-status" id="qr-status">QRコードを生成中...</div>
  <div class="qr-btn-row">
    <button class="qr-btn qr-btn-secondary" id="btn-png">PNG ダウンロード</button>
    <button class="qr-btn qr-btn-secondary" id="btn-svg">SVG ダウンロード</button>
  </div>
</div>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function() {
  'use strict';

  // ============================================================
  // QRコード純粋JS実装
  // バイトモード / 誤り訂正レベルM / バージョン1〜6
  // ============================================================

  // --- GF(256) 演算テーブル ---
  var GF_EXP = new Array(512);
  var GF_LOG = new Array(256);
  (function initGF() {
    var x = 1;
    for (var i = 0; i < 255; i++) {
      GF_EXP[i] = x;
      GF_LOG[x] = i;
      x = x << 1;
      if (x & 0x100) x ^= 0x11d;
    }
    for (var i = 255; i < 512; i++) GF_EXP[i] = GF_EXP[i - 255];
  })();

  function gfMul(a, b) {
    if (a === 0 || b === 0) return 0;
    return GF_EXP[(GF_LOG[a] + GF_LOG[b]) % 255];
  }

  function makeGenPoly(degree) {
    var p = [1];
    for (var i = 0; i < degree; i++) {
      var q = [1, GF_EXP[i]];
      var r = new Array(p.length + q.length - 1).fill(0);
      for (var j = 0; j < p.length; j++)
        for (var k = 0; k < q.length; k++)
          r[j + k] ^= gfMul(p[j], q[k]);
      p = r;
    }
    return p;
  }

  function rsEncode(data, nsym) {
    var gen = makeGenPoly(nsym);
    var msg = data.concat(new Array(nsym).fill(0));
    for (var i = 0; i < data.length; i++) {
      var coef = msg[i];
      if (coef !== 0)
        for (var j = 0; j < gen.length; j++)
          msg[i + j] ^= gfMul(gen[j], coef);
    }
    return msg.slice(data.length);
  }

  // --- バージョン情報 (ECレベルM) ---
  // [dataBytes, ecCodewords, [blockCount, dataPerBlock, ...]]
  var VERSION_INFO = {
    1: { data: 16, ec: 10, blocks: [[1, 16]] },
    2: { data: 28, ec: 16, blocks: [[1, 28]] },
    3: { data: 44, ec: 26, blocks: [[2, 22]] },
    4: { data: 64, ec: 36, blocks: [[2, 32]] },
    5: { data: 86, ec: 46, blocks: [[2, 43]] },
    6: { data: 108, ec: 60, blocks: [[4, 27]] },
  };

  // アライメントパターン位置
  var ALIGN_POS = { 1:[], 2:[6,18], 3:[6,22], 4:[6,26], 5:[6,30], 6:[6,34] };

  // フォーマット文字列 (ECレベルM, マスク0〜7)
  var FORMAT_STRINGS = [
    0x5412, 0x5125, 0x5E7C, 0x5B4B,
    0x45F9, 0x40CE, 0x4F97, 0x4AA0
  ];

  // UTF-8エンコード（TextEncoder非依存）
  function utf8Encode(str) {
    var bytes = [];
    for (var i = 0; i < str.length; i++) {
      var c = str.charCodeAt(i);
      if (c < 0x80) {
        bytes.push(c);
      } else if (c < 0x800) {
        bytes.push(0xC0 | (c >> 6));
        bytes.push(0x80 | (c & 0x3F));
      } else if (c >= 0xD800 && c <= 0xDBFF && i + 1 < str.length) {
        var c2 = str.charCodeAt(i + 1);
        if (c2 >= 0xDC00 && c2 <= 0xDFFF) {
          var cp = 0x10000 + ((c - 0xD800) << 10) + (c2 - 0xDC00);
          bytes.push(0xF0 | (cp >> 18));
          bytes.push(0x80 | ((cp >> 12) & 0x3F));
          bytes.push(0x80 | ((cp >> 6) & 0x3F));
          bytes.push(0x80 | (cp & 0x3F));
          i++;
        }
      } else {
        bytes.push(0xE0 | (c >> 12));
        bytes.push(0x80 | ((c >> 6) & 0x3F));
        bytes.push(0x80 | (c & 0x3F));
      }
    }
    return bytes;
  }

  function selectVersion(byteLen) {
    for (var v = 1; v <= 6; v++) {
      // バイトモード: 4 + 8 + byteLen*8 ビット → バイト換算 + 余裕
      var needed = Math.ceil((4 + 8 + byteLen * 8) / 8);
      if (needed <= VERSION_INFO[v].data) return v;
    }
    return null;
  }

  function buildDataBitstream(dataBytes, version) {
    var info = VERSION_INFO[version];
    var bits = [];
    function addBits(val, len) {
      for (var i = len - 1; i >= 0; i--) bits.push((val >> i) & 1);
    }
    addBits(4, 4);               // モード: バイト
    addBits(dataBytes.length, 8); // 文字数
    for (var i = 0; i < dataBytes.length; i++) addBits(dataBytes[i], 8);
    // ターミネーター
    var totalBits = info.data * 8;
    for (var i = 0; i < 4 && bits.length < totalBits; i++) bits.push(0);
    while (bits.length % 8 !== 0) bits.push(0);
    // パディングバイト
    var padBytes = [0xEC, 0x11];
    var pi = 0;
    while (bits.length < totalBits) {
      var pb = padBytes[pi % 2]; pi++;
      addBits(pb, 8);
    }
    // ビット→バイト
    var bytes = [];
    for (var i = 0; i < bits.length; i += 8) {
      var b = 0;
      for (var j = 0; j < 8; j++) b = (b << 1) | (bits[i + j] || 0);
      bytes.push(b);
    }
    return bytes;
  }

  function buildFinalMessage(dataBytes, version) {
    var info = VERSION_INFO[version];
    var ecPerBlock = info.ec / info.blocks.reduce(function(s, b) { return s + b[0]; }, 0);
    // ブロック分割
    var allDataBlocks = [];
    var pos = 0;
    for (var bi = 0; bi < info.blocks.length; bi++) {
      var count = info.blocks[bi][0], dlen = info.blocks[bi][1];
      for (var b = 0; b < count; b++) {
        allDataBlocks.push(dataBytes.slice(pos, pos + dlen));
        pos += dlen;
      }
    }
    // ECブロック生成
    var allECBlocks = allDataBlocks.map(function(block) {
      return rsEncode(block.slice(), ecPerBlock);
    });
    // データをインターリーブ
    var result = [];
    var maxData = Math.max.apply(null, allDataBlocks.map(function(b) { return b.length; }));
    for (var i = 0; i < maxData; i++)
      for (var b = 0; b < allDataBlocks.length; b++)
        if (i < allDataBlocks[b].length) result.push(allDataBlocks[b][i]);
    // ECをインターリーブ
    var maxEC = Math.max.apply(null, allECBlocks.map(function(b) { return b.length; }));
    for (var i = 0; i < maxEC; i++)
      for (var b = 0; b < allECBlocks.length; b++)
        if (i < allECBlocks[b].length) result.push(allECBlocks[b][i]);
    return result;
  }

  function initMatrix(size) {
    var m = [];
    for (var i = 0; i < size; i++) m.push(new Array(size).fill(null));
    return m;
  }

  function placeFinderPattern(m, r, c) {
    for (var i = 0; i < 7; i++)
      for (var j = 0; j < 7; j++) {
        var onBorder = (i === 0 || i === 6 || j === 0 || j === 6);
        var onInner  = (i >= 2 && i <= 4 && j >= 2 && j <= 4);
        if (r+i >= 0 && r+i < m.length && c+j >= 0 && c+j < m.length)
          m[r+i][c+j] = (onBorder || onInner) ? 1 : 0;
      }
  }

  function placeSeparators(m, size) {
    for (var i = 0; i < 8; i++) {
      if (m[i]   !== undefined && m[i][7]      === null) m[i][7]      = 0;
      if (m[7]   !== undefined && m[7][i]      === null) m[7][i]      = 0;
      if (m[i]   !== undefined && m[i][size-8] === null) m[i][size-8] = 0;
      if (m[size-8] !== undefined && m[size-8][i] === null) m[size-8][i] = 0;
      if (m[size-1-i] !== undefined && m[size-1-i][7] === null) m[size-1-i][7] = 0;
      if (m[7] !== undefined && m[7][size-8+i] === null) m[7][size-8+i] = 0;
    }
  }

  function placeTimingPatterns(m, size) {
    for (var i = 8; i < size - 8; i++) {
      var v = (i % 2 === 0) ? 1 : 0;
      if (m[6][i]  === null) m[6][i]  = v;
      if (m[i][6]  === null) m[i][6]  = v;
    }
  }

  function placeDarkModule(m, version) {
    m[4 * version + 9][8] = 1;
  }

  function placeAlignmentPattern(m, r, c) {
    var pat = [[1,1,1,1,1],[1,0,0,0,1],[1,0,1,0,1],[1,0,0,0,1],[1,1,1,1,1]];
    for (var i = -2; i <= 2; i++)
      for (var j = -2; j <= 2; j++)
        if (m[r+i][c+j] === null) m[r+i][c+j] = pat[i+2][j+2];
  }

  function reserveFormatArea(m, size) {
    // フォーマット情報エリアを予約（0で埋める）
    var positions = [
      [8,0],[8,1],[8,2],[8,3],[8,4],[8,5],[8,7],[8,8],
      [7,8],[5,8],[4,8],[3,8],[2,8],[1,8],[0,8]
    ];
    for (var i = 0; i < positions.length; i++)
      if (m[positions[i][0]][positions[i][1]] === null)
        m[positions[i][0]][positions[i][1]] = 0;
    for (var i = 0; i < 8; i++)
      if (m[size-1-i][8] === null) m[size-1-i][8] = 0;
    for (var i = 0; i < 8; i++)
      if (m[8][size-8+i] === null) m[8][size-8+i] = 0;
  }

  function placeFormatInfo(m, size, maskNum) {
    var fmt = FORMAT_STRINGS[maskNum];
    var bits = [];
    for (var i = 14; i >= 0; i--) bits.push((fmt >> i) & 1);
    // 上左ファインダー周辺
    var pos1 = [[8,0],[8,1],[8,2],[8,3],[8,4],[8,5],[8,7],[8,8],
                 [7,8],[5,8],[4,8],[3,8],[2,8],[1,8],[0,8]];
    for (var i = 0; i < 15; i++) m[pos1[i][0]][pos1[i][1]] = bits[i];
    // 右下ファインダー周辺
    for (var i = 0; i < 7; i++) m[size-1-i][8] = bits[i];
    for (var i = 7; i < 15; i++) m[8][size-15+i] = bits[i];
  }

  function placeData(m, size, codewords) {
    var bits = [];
    for (var i = 0; i < codewords.length; i++)
      for (var b = 7; b >= 0; b--) bits.push((codewords[i] >> b) & 1);
    var bi = 0, upward = true;
    for (var col = size - 1; col >= 1; col -= 2) {
      if (col === 6) col = 5;
      for (var row = 0; row < size; row++) {
        var r = upward ? (size - 1 - row) : row;
        for (var delta = 0; delta <= 1; delta++) {
          var c = col - delta;
          if (m[r][c] === null) m[r][c] = (bi < bits.length) ? bits[bi++] : 0;
        }
      }
      upward = !upward;
    }
  }

  function applyMask(m, size, maskNum) {
    function cond(r, c) {
      switch (maskNum) {
        case 0: return (r + c) % 2 === 0;
        case 1: return r % 2 === 0;
        case 2: return c % 3 === 0;
        case 3: return (r + c) % 3 === 0;
        case 4: return (Math.floor(r/2) + Math.floor(c/3)) % 2 === 0;
        case 5: return (r*c)%2 + (r*c)%3 === 0;
        case 6: return ((r*c)%2 + (r*c)%3) % 2 === 0;
        case 7: return ((r+c)%2 + (r*c)%3) % 2 === 0;
      }
    }
    var masked = [];
    for (var r = 0; r < size; r++) {
      masked.push(m[r].slice());
      for (var c = 0; c < size; c++)
        if (masked[r][c] !== null && cond(r, c)) masked[r][c] ^= 1;
    }
    return masked;
  }

  function penaltyScore(m, size) {
    var score = 0;
    for (var r = 0; r < size; r++) {
      var run = 1;
      for (var c = 1; c < size; c++) {
        if (m[r][c] === m[r][c-1]) { run++; if (run === 5) score += 3; else if (run > 5) score++; }
        else run = 1;
      }
    }
    for (var c = 0; c < size; c++) {
      var run = 1;
      for (var r = 1; r < size; r++) {
        if (m[r][c] === m[r-1][c]) { run++; if (run === 5) score += 3; else if (run > 5) score++; }
        else run = 1;
      }
    }
    for (var r = 0; r < size-1; r++)
      for (var c = 0; c < size-1; c++)
        if (m[r][c] === m[r][c+1] && m[r][c] === m[r+1][c] && m[r][c] === m[r+1][c+1])
          score += 3;
    var dark = 0;
    for (var r = 0; r < size; r++) for (var c = 0; c < size; c++) if (m[r][c]) dark++;
    var ratio = dark / (size * size);
    score += Math.abs(Math.round(ratio * 20) - 10) * 10;
    return score;
  }

  function generateQR(text) {
    var dataBytes = utf8Encode(text);
    var version = selectVersion(dataBytes.length);
    if (!version) return null;
    var size = version * 4 + 17;

    var msgBytes = buildDataBitstream(dataBytes, version);
    var codewords = buildFinalMessage(msgBytes, version);

    var bestMask = 0, bestScore = Infinity, bestMatrix = null;

    for (var mask = 0; mask < 8; mask++) {
      var m = initMatrix(size);
      placeFinderPattern(m, 0, 0);
      placeFinderPattern(m, 0, size - 7);
      placeFinderPattern(m, size - 7, 0);
      placeSeparators(m, size);
      placeTimingPatterns(m, size);
      placeDarkModule(m, version);
      var apos = ALIGN_POS[version];
      if (apos.length >= 2) {
        for (var ai = 0; ai < apos.length; ai++)
          for (var aj = 0; aj < apos.length; aj++)
            placeAlignmentPattern(m, apos[ai], apos[aj]);
      }
      reserveFormatArea(m, size);
      placeData(m, size, codewords.slice());
      var masked = applyMask(m, size, mask);
      placeFormatInfo(masked, size, mask);
      var sc = penaltyScore(masked, size);
      if (sc < bestScore) { bestScore = sc; bestMask = mask; bestMatrix = masked; }
    }

    return { matrix: bestMatrix, size: size, version: version };
  }

  // ---- UI ----
  var canvas = document.getElementById('qr-canvas');
  var ctx = canvas.getContext('2d');
  var statusEl = document.getElementById('qr-status');
  var sizeSlider = document.getElementById('qr-size');
  var sizeLabel = document.getElementById('qr-size-label');
  var currentQR = null;

  function getInputText() {
    var activeTab = document.querySelector('#qr-app .qr-tab.active');
    var tab = activeTab ? activeTab.getAttribute('data-tab') : 'url';
    if (tab === 'url') {
      return (document.getElementById('qr-url').value.trim()) || 'https://productivity-works.com';
    } else if (tab === 'text') {
      return document.getElementById('qr-text').value.trim() || 'テキストを入力してください';
    } else if (tab === 'wifi') {
      var ssid = document.getElementById('qr-wifi-ssid').value;
      var pass = document.getElementById('qr-wifi-pass').value;
      var enc  = document.getElementById('qr-wifi-enc').value;
      return 'WIFI:T:' + enc + ';S:' + ssid + ';P:' + pass + ';;';
    } else if (tab === 'email') {
      var to   = document.getElementById('qr-email-to').value;
      var subj = encodeURIComponent(document.getElementById('qr-email-subj').value);
      var body = encodeURIComponent(document.getElementById('qr-email-body').value);
      return 'mailto:' + to + '?subject=' + subj + '&body=' + body;
    }
    return '';
  }

  function renderQR() {
    var text = getInputText();
    var size = parseInt(sizeSlider.value);
    var fg = document.getElementById('qr-fg').value || '#000000';
    var bg = document.getElementById('qr-bg').value || '#ffffff';

    if (!text) {
      statusEl.textContent = '入力してください';
      return;
    }

    try {
      var qr = generateQR(text);
      if (!qr) {
        statusEl.textContent = 'エラー: テキストが長すぎます（バージョン6上限超過）';
        return;
      }
      currentQR = qr;
      canvas.width  = size;
      canvas.height = size;

      var qs = qr.size;
      var quiet = 4;
      var moduleSize = size / (qs + quiet * 2);

      ctx.fillStyle = bg;
      ctx.fillRect(0, 0, size, size);
      ctx.fillStyle = fg;

      for (var r = 0; r < qs; r++) {
        for (var c = 0; c < qs; c++) {
          if (qr.matrix[r][c] === 1) {
            var x = Math.round((quiet + c) * moduleSize);
            var y = Math.round((quiet + r) * moduleSize);
            var w = Math.round((quiet + c + 1) * moduleSize) - x;
            var h = Math.round((quiet + r + 1) * moduleSize) - y;
            ctx.fillRect(x, y, w, h);
          }
        }
      }
      statusEl.textContent = 'バージョン ' + qr.version + ' (' + qs + 'x' + qs + ') — ' + utf8Encode(text).length + ' バイト';
    } catch(e) {
      statusEl.textContent = 'エラーが発生しました: ' + e.message;
    }
  }

  // タブ切り替え
  var tabs = document.querySelectorAll('#qr-app .qr-tab');
  for (var i = 0; i < tabs.length; i++) {
    tabs[i].addEventListener('click', (function(tab) {
      return function() {
        var allTabs = document.querySelectorAll('#qr-app .qr-tab');
        var allPanels = document.querySelectorAll('#qr-app .qr-panel');
        for (var j = 0; j < allTabs.length; j++) allTabs[j].classList.remove('active');
        for (var j = 0; j < allPanels.length; j++) allPanels[j].classList.remove('active');
        tab.classList.add('active');
        var panelId = 'panel-' + tab.getAttribute('data-tab');
        var panel = document.getElementById(panelId);
        if (panel) panel.classList.add('active');
        renderQR();
      };
    })(tabs[i]));
  }

  // サイズスライダー
  sizeSlider.addEventListener('input', function() {
    sizeLabel.textContent = sizeSlider.value + 'px';
    renderQR();
  });

  // カラーピッカー
  document.getElementById('qr-fg').addEventListener('input', renderQR);
  document.getElementById('qr-bg').addEventListener('input', renderQR);

  // テキスト入力（デバウンス）
  var debounceTimer;
  function debounceRender() {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(renderQR, 300);
  }
  var inputIds = ['qr-url','qr-text','qr-wifi-ssid','qr-wifi-pass','qr-email-to','qr-email-subj','qr-email-body'];
  for (var i = 0; i < inputIds.length; i++) {
    var el = document.getElementById(inputIds[i]);
    if (el) el.addEventListener('input', debounceRender);
  }
  var wifiEnc = document.getElementById('qr-wifi-enc');
  if (wifiEnc) wifiEnc.addEventListener('change', renderQR);

  // PNG ダウンロード
  document.getElementById('btn-png').addEventListener('click', function() {
    if (!currentQR) return;
    var a = document.createElement('a');
    a.download = 'qrcode.png';
    a.href = canvas.toDataURL('image/png');
    a.click();
  });

  // SVG ダウンロード
  document.getElementById('btn-svg').addEventListener('click', function() {
    if (!currentQR) return;
    var qr = currentQR;
    var qs = qr.size;
    var quiet = 4;
    var total = qs + quiet * 2;
    var mod = 10;
    var svgSize = total * mod;
    var fg = document.getElementById('qr-fg').value || '#000000';
    var bg = document.getElementById('qr-bg').value || '#ffffff';

    var rects = '';
    for (var r = 0; r < qs; r++)
      for (var c = 0; c < qs; c++)
        if (qr.matrix[r][c] === 1)
          rects += '<rect x="' + ((quiet+c)*mod) + '" y="' + ((quiet+r)*mod) + '" width="' + mod + '" height="' + mod + '"/>';

    var svg = '<?xml version="1.0" encoding="UTF-8"?>' +
      '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 ' + svgSize + ' ' + svgSize + '"' +
      ' width="' + svgSize + '" height="' + svgSize + '">' +
      '<rect width="' + svgSize + '" height="' + svgSize + '" fill="' + bg + '"/>' +
      '<g fill="' + fg + '">' + rects + '</g></svg>';

    var blob = new Blob([svg], { type: 'image/svg+xml' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.download = 'qrcode.svg';
    a.href = url;
    a.click();
    setTimeout(function() { URL.revokeObjectURL(url); }, 1000);
  });

  // 初期レンダリング
  renderQR();

})();
</script>

</div>

> URLをエンコード → [URLエンコード・デコードツール](/ja/tools/url-encoder-decoder/)
> Base64に変換 → [Base64エンコーダー・デコーダー](/ja/tools/base64-encoder-decoder/)
> ダミー画像を作成 → [プレースホルダー画像生成ツール](/ja/tools/placeholder-image/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
