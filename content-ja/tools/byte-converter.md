---
title: "バイト変換ツール — データサイズ計算"
date: 2025-05-16
description: "バイト・KB・MB・GB・TB間の変換。2進数・10進数単位対応。ファイルサイズと帯域幅からダウンロード時間を計算。"
categories: ["無料ツール"]
slug: "byte-converter"
ShowToc: false
cover:
  image: "/images/covers/byte-converter-ja.png"
  alt: "バイト変換ツール"
---

<div id="byte-app">
<style>
  #byte-app {
    font-family: "Hiragino Kaku Gothic ProN", "Noto Sans JP", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    max-width: 860px;
    margin: 0 auto;
    color: #1a1a2e;
  }
  #byte-app h2.ba-section-title {
    font-size: 1.05rem;
    font-weight: 700;
    color: #0f3460;
    border-left: 4px solid #e94560;
    padding-left: 0.6rem;
    margin: 1.8rem 0 1rem;
  }
  #byte-app .ba-intro {
    background: #f0f4ff;
    border-radius: 8px;
    padding: 1rem 1.2rem;
    font-size: 0.92rem;
    color: #444;
    margin-bottom: 1.5rem;
    line-height: 1.75;
  }
  #byte-app .ba-input-row {
    display: flex;
    gap: 0.5rem;
    align-items: center;
    margin-bottom: 1rem;
    flex-wrap: wrap;
  }
  #byte-app .ba-input-row label {
    font-size: 0.88rem;
    font-weight: 600;
    color: #333;
    min-width: 44px;
  }
  #byte-app .ba-input-row input[type="number"] {
    flex: 1;
    min-width: 150px;
    padding: 0.55rem 0.75rem;
    border: 1.5px solid #c8d0e0;
    border-radius: 6px;
    font-size: 1rem;
    outline: none;
    transition: border-color 0.2s;
    background: #fff;
    color: #1a1a2e;
  }
  #byte-app .ba-input-row input[type="number"]:focus {
    border-color: #4a90e2;
  }
  #byte-app .ba-input-row select {
    padding: 0.55rem 0.65rem;
    border: 1.5px solid #c8d0e0;
    border-radius: 6px;
    font-size: 0.9rem;
    background: #fff;
    color: #1a1a2e;
    cursor: pointer;
    outline: none;
  }
  #byte-app .ba-btn {
    padding: 0.55rem 1.1rem;
    background: #e94560;
    color: #fff;
    border: none;
    border-radius: 6px;
    font-size: 0.92rem;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s;
    white-space: nowrap;
  }
  #byte-app .ba-btn:hover {
    background: #c73652;
  }
  #byte-app .ba-btn-secondary {
    background: #6c757d;
  }
  #byte-app .ba-btn-secondary:hover {
    background: #545b62;
  }
  #byte-app .ba-table-wrap {
    overflow-x: auto;
    border-radius: 8px;
    box-shadow: 0 1px 6px rgba(0,0,0,0.08);
    margin-bottom: 1.5rem;
  }
  #byte-app table.ba-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.91rem;
  }
  #byte-app table.ba-table thead tr {
    background: #0f3460;
    color: #fff;
  }
  #byte-app table.ba-table thead th {
    padding: 0.65rem 0.9rem;
    text-align: left;
    font-weight: 700;
    white-space: nowrap;
  }
  #byte-app table.ba-table tbody tr:nth-child(even) {
    background: #f5f7fb;
  }
  #byte-app table.ba-table tbody tr:hover {
    background: #eef2ff;
  }
  #byte-app table.ba-table tbody td {
    padding: 0.6rem 0.9rem;
    border-bottom: 1px solid #e5e9f2;
    white-space: nowrap;
  }
  #byte-app table.ba-table tbody td:nth-child(2),
  #byte-app table.ba-table tbody td:nth-child(3) {
    font-family: "Courier New", Courier, monospace;
    color: #0f3460;
    font-weight: 700;
  }
  #byte-app .ba-badge {
    display: inline-block;
    font-size: 0.72rem;
    border-radius: 4px;
    padding: 0.1rem 0.35rem;
    font-weight: 700;
    margin-left: 0.3rem;
    vertical-align: middle;
  }
  #byte-app .ba-badge-bin {
    background: #d4edda;
    color: #155724;
  }
  #byte-app .ba-badge-dec {
    background: #cce5ff;
    color: #004085;
  }
  #byte-app .ba-bw-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin-bottom: 1rem;
  }
  @media (max-width: 600px) {
    #byte-app .ba-bw-grid {
      grid-template-columns: 1fr;
    }
    #byte-app .ba-input-row {
      flex-direction: column;
      align-items: flex-start;
    }
    #byte-app .ba-input-row input[type="number"] {
      width: 100%;
    }
  }
  #byte-app .ba-field-group {
    display: flex;
    flex-direction: column;
    gap: 0.35rem;
  }
  #byte-app .ba-field-group label {
    font-size: 0.85rem;
    font-weight: 600;
    color: #444;
  }
  #byte-app .ba-field-group input,
  #byte-app .ba-field-group select {
    padding: 0.55rem 0.75rem;
    border: 1.5px solid #c8d0e0;
    border-radius: 6px;
    font-size: 0.95rem;
    outline: none;
    transition: border-color 0.2s;
    background: #fff;
    color: #1a1a2e;
  }
  #byte-app .ba-field-group input:focus,
  #byte-app .ba-field-group select:focus {
    border-color: #4a90e2;
  }
  #byte-app .ba-result-box {
    background: #eef6ff;
    border: 1.5px solid #b3d4f5;
    border-radius: 8px;
    padding: 1rem 1.2rem;
    font-size: 1rem;
    color: #0f3460;
    font-weight: 600;
    margin-top: 0.8rem;
    min-height: 2.5rem;
    line-height: 1.7;
  }
  #byte-app .ba-result-box span.ba-highlight {
    font-size: 1.3rem;
    color: #e94560;
    font-weight: 700;
  }
  #byte-app .ba-note {
    font-size: 0.82rem;
    color: #666;
    margin-top: 0.4rem;
    line-height: 1.6;
  }
  #byte-app .ba-error {
    color: #c0392b;
    font-size: 0.88rem;
    margin-top: 0.3rem;
    display: none;
  }
  #byte-app .ba-crosslinks {
    margin-top: 2rem;
    padding-top: 1.2rem;
    border-top: 1px solid #e5e9f2;
    font-size: 0.9rem;
    color: #555;
    line-height: 1.9;
  }
  #byte-app .ba-crosslinks a {
    color: #4a90e2;
    text-decoration: none;
    margin-right: 1rem;
    font-weight: 600;
  }
  #byte-app .ba-crosslinks a:hover {
    text-decoration: underline;
  }
  #byte-app .ba-cta-freee {
    margin-top: 2rem;
    background: linear-gradient(135deg, #0f3460 0%, #16213e 100%);
    border-radius: 10px;
    padding: 1.4rem 1.6rem;
    color: #fff;
    display: flex;
    align-items: center;
    gap: 1.2rem;
    flex-wrap: wrap;
  }
  #byte-app .ba-cta-freee .ba-cta-text {
    flex: 1;
    min-width: 200px;
  }
  #byte-app .ba-cta-freee .ba-cta-text strong {
    display: block;
    font-size: 1rem;
    margin-bottom: 0.3rem;
    color: #ffd700;
  }
  #byte-app .ba-cta-freee .ba-cta-text p {
    font-size: 0.87rem;
    margin: 0;
    color: #cdd9f0;
    line-height: 1.6;
  }
  #byte-app .ba-cta-freee a.ba-cta-btn {
    display: inline-block;
    background: #e94560;
    color: #fff;
    text-decoration: none;
    padding: 0.65rem 1.4rem;
    border-radius: 6px;
    font-weight: 700;
    font-size: 0.92rem;
    white-space: nowrap;
    transition: background 0.2s;
  }
  #byte-app .ba-cta-freee a.ba-cta-btn:hover {
    background: #c73652;
  }
</style>

<div class="ba-intro">
  任意の単位に値を入力すると、Bit・Byte・KB・MB・GB・TB・PBすべてに即時変換します。2進数（KiB/MiB/GiB）と10進数（KB/MB/GB）の両方に対応。下部の帯域幅計算機でダウンロード時間も算出できます。
</div>

<!-- ===== 変換ツール ===== -->
<h2 class="ba-section-title">データサイズ変換</h2>

<div class="ba-input-row">
  <label for="ba-val">値</label>
  <input type="number" id="ba-val" placeholder="例: 1024" min="0" step="any" />
  <select id="ba-unit">
    <option value="bit">ビット (b)</option>
    <option value="byte" selected>バイト (B)</option>
    <option value="kb_dec">キロバイト — KB (10³)</option>
    <option value="mb_dec">メガバイト — MB (10⁶)</option>
    <option value="gb_dec">ギガバイト — GB (10⁹)</option>
    <option value="tb_dec">テラバイト — TB (10¹²)</option>
    <option value="pb_dec">ペタバイト — PB (10¹⁵)</option>
    <option value="kib">キビバイト — KiB (2¹⁰)</option>
    <option value="mib">メビバイト — MiB (2²⁰)</option>
    <option value="gib">ギビバイト — GiB (2³⁰)</option>
    <option value="tib">テビバイト — TiB (2⁴⁰)</option>
    <option value="pib">ペビバイト — PiB (2⁵⁰)</option>
  </select>
  <button class="ba-btn" onclick="baConvert()">変換</button>
  <button class="ba-btn ba-btn-secondary" onclick="baClear()">クリア</button>
</div>
<p class="ba-error" id="ba-error">有効な0以上の数値を入力してください。</p>

<div class="ba-table-wrap" id="ba-results-wrap" style="display:none;">
  <table class="ba-table">
    <thead>
      <tr>
        <th>単位</th>
        <th>変換後の値</th>
        <th>バイト数</th>
      </tr>
    </thead>
    <tbody id="ba-tbody"></tbody>
  </table>
</div>

<!-- ===== 帯域幅計算機 ===== -->
<h2 class="ba-section-title">帯域幅 / ダウンロード時間計算</h2>

<div class="ba-bw-grid">
  <div class="ba-field-group">
    <label for="ba-fsize">ファイルサイズ</label>
    <input type="number" id="ba-fsize" placeholder="例: 700" min="0" step="any" />
  </div>
  <div class="ba-field-group">
    <label for="ba-funit">サイズ単位</label>
    <select id="ba-funit">
      <option value="byte">バイト (B)</option>
      <option value="kb_dec">キロバイト (KB)</option>
      <option value="mb_dec" selected>メガバイト (MB)</option>
      <option value="gb_dec">ギガバイト (GB)</option>
      <option value="tb_dec">テラバイト (TB)</option>
      <option value="kib">キビバイト (KiB)</option>
      <option value="mib">メビバイト (MiB)</option>
      <option value="gib">ギビバイト (GiB)</option>
    </select>
  </div>
  <div class="ba-field-group">
    <label for="ba-speed">回線速度</label>
    <input type="number" id="ba-speed" placeholder="例: 100" min="0" step="any" />
  </div>
  <div class="ba-field-group">
    <label for="ba-spunit">速度単位</label>
    <select id="ba-spunit">
      <option value="bps">bps (ビット/秒)</option>
      <option value="kbps">Kbps (10³ビット/秒)</option>
      <option value="mbps" selected>Mbps (10⁶ビット/秒)</option>
      <option value="gbps">Gbps (10⁹ビット/秒)</option>
      <option value="KBps">KB/s (10³バイト/秒)</option>
      <option value="MBps">MB/s (10⁶バイト/秒)</option>
      <option value="GBps">GB/s (10⁹バイト/秒)</option>
    </select>
  </div>
</div>

<div style="margin-bottom: 0.8rem;">
  <button class="ba-btn" onclick="baBandwidth()">ダウンロード時間を計算</button>
  <button class="ba-btn ba-btn-secondary" style="margin-left: 0.5rem;" onclick="baBwClear()">クリア</button>
</div>
<p class="ba-error" id="ba-bw-error">ファイルサイズと回線速度に正の数値を入力してください。</p>

<div class="ba-result-box" id="ba-bw-result" style="display:none;"></div>
<p class="ba-note">※ 実際のダウンロード速度はネットワーク状況・サーバー負荷・プロトコルオーバーヘッドにより異なります。</p>

<!-- ===== 単位早見表 ===== -->
<h2 class="ba-section-title">単位早見表</h2>

<div class="ba-table-wrap">
  <table class="ba-table">
    <thead>
      <tr>
        <th>単位名</th>
        <th>記号</th>
        <th>方式</th>
        <th>正確なバイト数</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>ビット</td><td>b</td><td>—</td><td>1/8 バイト</td></tr>
      <tr><td>バイト</td><td>B</td><td>—</td><td>8 ビット</td></tr>
      <tr><td>キロバイト <span class="ba-badge ba-badge-dec">10進数</span></td><td>KB</td><td>SI (基数10)</td><td>1,000 バイト</td></tr>
      <tr><td>キビバイト <span class="ba-badge ba-badge-bin">2進数</span></td><td>KiB</td><td>IEC (基数2)</td><td>1,024 バイト</td></tr>
      <tr><td>メガバイト <span class="ba-badge ba-badge-dec">10進数</span></td><td>MB</td><td>SI (基数10)</td><td>1,000,000 バイト</td></tr>
      <tr><td>メビバイト <span class="ba-badge ba-badge-bin">2進数</span></td><td>MiB</td><td>IEC (基数2)</td><td>1,048,576 バイト</td></tr>
      <tr><td>ギガバイト <span class="ba-badge ba-badge-dec">10進数</span></td><td>GB</td><td>SI (基数10)</td><td>1,000,000,000 バイト</td></tr>
      <tr><td>ギビバイト <span class="ba-badge ba-badge-bin">2進数</span></td><td>GiB</td><td>IEC (基数2)</td><td>1,073,741,824 バイト</td></tr>
      <tr><td>テラバイト <span class="ba-badge ba-badge-dec">10進数</span></td><td>TB</td><td>SI (基数10)</td><td>10¹² バイト</td></tr>
      <tr><td>テビバイト <span class="ba-badge ba-badge-bin">2進数</span></td><td>TiB</td><td>IEC (基数2)</td><td>2⁴⁰ バイト</td></tr>
      <tr><td>ペタバイト <span class="ba-badge ba-badge-dec">10進数</span></td><td>PB</td><td>SI (基数10)</td><td>10¹⁵ バイト</td></tr>
      <tr><td>ペビバイト <span class="ba-badge ba-badge-bin">2進数</span></td><td>PiB</td><td>IEC (基数2)</td><td>2⁵⁰ バイト</td></tr>
    </tbody>
  </table>
</div>

<h2 class="ba-section-title">2進数と10進数の違いとは？</h2>

<p>ハードディスクメーカーは「1 GB = 10億バイト」という10進数表記を採用しています（数字が大きく見えるため）。一方、OSは伝統的に「1 GiB = 約10億7374万バイト」という2進数表記を使います。そのため「500GB」と表示されたHDDがWindowsやmacOSでは「約465 GiB」と表示されます。IEC（国際電気標準会議）は1998年にKiB/MiB/GiBという表記を標準化し、この混乱を解消しました。</p>

<script>
(function() {
  var BA_FACTORS = {
    bit:    1 / 8,
    byte:   1,
    kb_dec: 1e3,
    mb_dec: 1e6,
    gb_dec: 1e9,
    tb_dec: 1e12,
    pb_dec: 1e15,
    kib:    1024,
    mib:    1048576,
    gib:    1073741824,
    tib:    1099511627776,
    pib:    1125899906842624
  };

  var BA_LABELS = {
    bit:    'ビット (b)',
    byte:   'バイト (B)',
    kb_dec: 'キロバイト (KB)',
    mb_dec: 'メガバイト (MB)',
    gb_dec: 'ギガバイト (GB)',
    tb_dec: 'テラバイト (TB)',
    pb_dec: 'ペタバイト (PB)',
    kib:    'キビバイト (KiB)',
    mib:    'メビバイト (MiB)',
    gib:    'ギビバイト (GiB)',
    tib:    'テビバイト (TiB)',
    pib:    'ペビバイト (PiB)'
  };

  var BA_ORDER = ['bit','byte','kb_dec','kib','mb_dec','mib','gb_dec','gib','tb_dec','tib','pb_dec','pib'];

  var BA_BW_FACTORS = {
    bps:  1,
    kbps: 1e3,
    mbps: 1e6,
    gbps: 1e9,
    KBps: 8e3,
    MBps: 8e6,
    GBps: 8e9
  };

  function baFormatNum(n) {
    if (n === 0) return '0';
    if (n >= 1e15) return n.toExponential(6);
    if (n < 1e-6 && n > 0) return n.toExponential(6);
    var s = parseFloat(n.toPrecision(10)).toString();
    var parts = s.split('.');
    parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    return parts.join('.');
  }

  function baFormatBytes(bytes) {
    if (bytes >= 1e15) return bytes.toExponential(4) + ' バイト';
    return parseFloat(bytes.toPrecision(12)).toLocaleString('ja-JP', {maximumFractionDigits: 4}) + ' バイト';
  }

  window.baConvert = function() {
    var err = document.getElementById('ba-error');
    var wrap = document.getElementById('ba-results-wrap');
    var val = parseFloat(document.getElementById('ba-val').value);
    var unit = document.getElementById('ba-unit').value;
    err.style.display = 'none';

    if (isNaN(val) || val < 0) {
      err.style.display = 'block';
      wrap.style.display = 'none';
      return;
    }

    var bytes = val * BA_FACTORS[unit];
    var tbody = document.getElementById('ba-tbody');
    tbody.innerHTML = '';

    BA_ORDER.forEach(function(u) {
      var converted = bytes / BA_FACTORS[u];
      var tr = document.createElement('tr');
      if (u === unit) tr.style.background = '#fffbe6';
      var isBin = ['kib','mib','gib','tib','pib'].indexOf(u) !== -1;
      var badge = (u !== 'bit' && u !== 'byte')
        ? '<span class="ba-badge ' + (isBin ? 'ba-badge-bin' : 'ba-badge-dec') + '">' + (isBin ? '2進数' : '10進数') + '</span>'
        : '';
      tr.innerHTML =
        '<td>' + BA_LABELS[u] + badge + '</td>' +
        '<td>' + baFormatNum(converted) + '</td>' +
        '<td>' + baFormatBytes(bytes) + '</td>';
      tbody.appendChild(tr);
    });

    wrap.style.display = 'block';
  };

  window.baClear = function() {
    document.getElementById('ba-val').value = '';
    document.getElementById('ba-error').style.display = 'none';
    document.getElementById('ba-results-wrap').style.display = 'none';
    document.getElementById('ba-tbody').innerHTML = '';
  };

  function baFormatTime(seconds) {
    if (seconds < 1) return (seconds * 1000).toFixed(1) + ' ミリ秒';
    if (seconds < 60) return seconds.toFixed(2) + ' 秒';
    if (seconds < 3600) {
      var m = Math.floor(seconds / 60);
      var s = (seconds % 60).toFixed(0);
      return m + ' 分 ' + s + ' 秒';
    }
    if (seconds < 86400) {
      var h = Math.floor(seconds / 3600);
      var rem = seconds % 3600;
      var m2 = Math.floor(rem / 60);
      return h + ' 時間 ' + m2 + ' 分';
    }
    var d = (seconds / 86400).toFixed(1);
    return d + ' 日';
  }

  window.baBandwidth = function() {
    var err = document.getElementById('ba-bw-error');
    var res = document.getElementById('ba-bw-result');
    var fsize = parseFloat(document.getElementById('ba-fsize').value);
    var funit = document.getElementById('ba-funit').value;
    var speed = parseFloat(document.getElementById('ba-speed').value);
    var spunit = document.getElementById('ba-spunit').value;
    err.style.display = 'none';
    res.style.display = 'none';

    if (isNaN(fsize) || fsize <= 0 || isNaN(speed) || speed <= 0) {
      err.style.display = 'block';
      return;
    }

    var fileBits = fsize * BA_FACTORS[funit] * 8;
    var bitsPerSec = speed * BA_BW_FACTORS[spunit];
    var seconds = fileBits / bitsPerSec;

    var fsizeLabel = document.getElementById('ba-funit').options[document.getElementById('ba-funit').selectedIndex].text;
    var speedLabel = document.getElementById('ba-spunit').options[document.getElementById('ba-spunit').selectedIndex].text;

    res.innerHTML =
      'ファイルサイズ: <strong>' + baFormatNum(fsize) + ' ' + fsizeLabel + '</strong> &nbsp;|&nbsp; ' +
      '回線速度: <strong>' + baFormatNum(speed) + ' ' + speedLabel + '</strong><br>' +
      '推定ダウンロード時間: <span class="ba-highlight">' + baFormatTime(seconds) + '</span>';
    res.style.display = 'block';
  };

  window.baBwClear = function() {
    document.getElementById('ba-fsize').value = '';
    document.getElementById('ba-speed').value = '';
    document.getElementById('ba-bw-error').style.display = 'none';
    document.getElementById('ba-bw-result').style.display = 'none';
  };

  document.getElementById('ba-val').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') baConvert();
  });
})();
</script>

<div class="ba-crosslinks">
  <strong>関連ツール:</strong><br>
  <a href="/ja/tools/unit-converter/">単位変換ツール</a>
  <a href="/ja/tools/binary-converter/">2進数変換ツール</a>
  <a href="/ja/tools/ip-address-info/">IPアドレス情報</a>
</div>

<!-- freee CTA -->
<div class="ba-cta-freee">
  <div class="ba-cta-text">
    <strong>freee会計で経理をもっとスマートに</strong>
    <p>クラウド会計ソフト「freee」なら、請求書・経費精算・確定申告をひとつのツールで完結。データのバックアップもクラウドで安心管理。</p>
  </div>
  <a class="ba-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
</div>

</div>
