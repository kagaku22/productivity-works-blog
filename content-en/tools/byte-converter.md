---
title: "Byte Converter — Data Size Calculator"
date: 2025-05-16
description: "Convert between bytes, KB, MB, GB, TB and more. Binary and decimal units. Calculate download times from file size and bandwidth."
categories: ["Free Tools"]
slug: "byte-converter"
ShowToc: false
cover:
  image: "/images/covers/byte-converter.png"
  alt: "Byte Converter"
---

<div id="byte-app">
<style>
  #byte-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    max-width: 860px;
    margin: 0 auto;
    color: #1a1a2e;
  }
  #byte-app h2.ba-section-title {
    font-size: 1.1rem;
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
    line-height: 1.6;
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
    min-width: 40px;
  }
  #byte-app .ba-input-row input[type="number"] {
    flex: 1;
    min-width: 160px;
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
    font-size: 0.92rem;
    background: #fff;
    color: #1a1a2e;
    cursor: pointer;
    outline: none;
  }
  #byte-app .ba-btn {
    padding: 0.55rem 1.2rem;
    background: #e94560;
    color: #fff;
    border: none;
    border-radius: 6px;
    font-size: 0.92rem;
    font-weight: 600;
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
    font-size: 0.92rem;
  }
  #byte-app table.ba-table thead tr {
    background: #0f3460;
    color: #fff;
  }
  #byte-app table.ba-table thead th {
    padding: 0.65rem 0.9rem;
    text-align: left;
    font-weight: 600;
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
    font-weight: 600;
  }
  #byte-app .ba-badge {
    display: inline-block;
    font-size: 0.75rem;
    border-radius: 4px;
    padding: 0.1rem 0.4rem;
    font-weight: 600;
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
    line-height: 1.6;
  }
  #byte-app .ba-result-box span.ba-highlight {
    font-size: 1.3rem;
    color: #e94560;
  }
  #byte-app .ba-note {
    font-size: 0.82rem;
    color: #666;
    margin-top: 0.4rem;
  }
  #byte-app .ba-crosslinks {
    margin-top: 2rem;
    padding-top: 1.2rem;
    border-top: 1px solid #e5e9f2;
    font-size: 0.9rem;
    color: #555;
  }
  #byte-app .ba-crosslinks a {
    color: #4a90e2;
    text-decoration: none;
    margin-right: 1rem;
    font-weight: 500;
  }
  #byte-app .ba-crosslinks a:hover {
    text-decoration: underline;
  }
  #byte-app .ba-error {
    color: #c0392b;
    font-size: 0.88rem;
    margin-top: 0.3rem;
    display: none;
  }
</style>

<div class="ba-intro">
  Enter a value in any unit below and instantly see it converted into all other data size units — both binary (base-2) and decimal (base-10). The bandwidth calculator at the bottom estimates download time from file size and connection speed.
</div>

<!-- ===== CONVERTER ===== -->
<h2 class="ba-section-title">Data Size Converter</h2>

<div class="ba-input-row">
  <label for="ba-val">Value</label>
  <input type="number" id="ba-val" placeholder="e.g. 1024" min="0" step="any" />
  <select id="ba-unit">
    <option value="bit">Bit (b)</option>
    <option value="byte" selected>Byte (B)</option>
    <option value="kb_dec">Kilobyte — KB (10³)</option>
    <option value="mb_dec">Megabyte — MB (10⁶)</option>
    <option value="gb_dec">Gigabyte — GB (10⁹)</option>
    <option value="tb_dec">Terabyte — TB (10¹²)</option>
    <option value="pb_dec">Petabyte — PB (10¹⁵)</option>
    <option value="kib">Kibibyte — KiB (2¹⁰)</option>
    <option value="mib">Mebibyte — MiB (2²⁰)</option>
    <option value="gib">Gibibyte — GiB (2³⁰)</option>
    <option value="tib">Tebibyte — TiB (2⁴⁰)</option>
    <option value="pib">Pebibyte — PiB (2⁵⁰)</option>
  </select>
  <button class="ba-btn" onclick="baConvert()">Convert</button>
  <button class="ba-btn ba-btn-secondary" onclick="baClear()">Clear</button>
</div>
<p class="ba-error" id="ba-error">Please enter a valid non-negative number.</p>

<div class="ba-table-wrap" id="ba-results-wrap" style="display:none;">
  <table class="ba-table">
    <thead>
      <tr>
        <th>Unit</th>
        <th>Value</th>
        <th>Exact Value (bytes)</th>
      </tr>
    </thead>
    <tbody id="ba-tbody"></tbody>
  </table>
</div>

<!-- ===== BANDWIDTH CALCULATOR ===== -->
<h2 class="ba-section-title">Bandwidth / Download Time Calculator</h2>

<div class="ba-bw-grid">
  <div class="ba-field-group">
    <label for="ba-fsize">File Size</label>
    <input type="number" id="ba-fsize" placeholder="e.g. 700" min="0" step="any" />
  </div>
  <div class="ba-field-group">
    <label for="ba-funit">File Size Unit</label>
    <select id="ba-funit">
      <option value="byte">Byte (B)</option>
      <option value="kb_dec">Kilobyte (KB)</option>
      <option value="mb_dec" selected>Megabyte (MB)</option>
      <option value="gb_dec">Gigabyte (GB)</option>
      <option value="tb_dec">Terabyte (TB)</option>
      <option value="kib">Kibibyte (KiB)</option>
      <option value="mib">Mebibyte (MiB)</option>
      <option value="gib">Gibibyte (GiB)</option>
    </select>
  </div>
  <div class="ba-field-group">
    <label for="ba-speed">Connection Speed</label>
    <input type="number" id="ba-speed" placeholder="e.g. 100" min="0" step="any" />
  </div>
  <div class="ba-field-group">
    <label for="ba-spunit">Speed Unit</label>
    <select id="ba-spunit">
      <option value="bps">bps (bits/s)</option>
      <option value="kbps">Kbps (10³ bits/s)</option>
      <option value="mbps" selected>Mbps (10⁶ bits/s)</option>
      <option value="gbps">Gbps (10⁹ bits/s)</option>
      <option value="KBps">KB/s (10³ bytes/s)</option>
      <option value="MBps">MB/s (10⁶ bytes/s)</option>
      <option value="GBps">GB/s (10⁹ bytes/s)</option>
    </select>
  </div>
</div>

<div style="margin-bottom: 0.8rem;">
  <button class="ba-btn" onclick="baBandwidth()">Calculate Download Time</button>
  <button class="ba-btn ba-btn-secondary" style="margin-left: 0.5rem;" onclick="baBwClear()">Clear</button>
</div>
<p class="ba-error" id="ba-bw-error">Please enter valid positive numbers for both fields.</p>

<div class="ba-result-box" id="ba-bw-result" style="display:none;"></div>
<p class="ba-note">Note: Actual download speed depends on network conditions, server capacity, and protocol overhead.</p>

<!-- ===== REFERENCE TABLE ===== -->
<h2 class="ba-section-title">Unit Reference</h2>

<div class="ba-table-wrap">
  <table class="ba-table">
    <thead>
      <tr>
        <th>Unit</th>
        <th>Symbol</th>
        <th>System</th>
        <th>Exact Size</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>Bit</td><td>b</td><td>—</td><td>1/8 byte</td></tr>
      <tr><td>Byte</td><td>B</td><td>—</td><td>8 bits</td></tr>
      <tr><td>Kilobyte <span class="ba-badge ba-badge-dec">decimal</span></td><td>KB</td><td>SI (base-10)</td><td>1,000 bytes</td></tr>
      <tr><td>Kibibyte <span class="ba-badge ba-badge-bin">binary</span></td><td>KiB</td><td>IEC (base-2)</td><td>1,024 bytes</td></tr>
      <tr><td>Megabyte <span class="ba-badge ba-badge-dec">decimal</span></td><td>MB</td><td>SI (base-10)</td><td>1,000,000 bytes</td></tr>
      <tr><td>Mebibyte <span class="ba-badge ba-badge-bin">binary</span></td><td>MiB</td><td>IEC (base-2)</td><td>1,048,576 bytes</td></tr>
      <tr><td>Gigabyte <span class="ba-badge ba-badge-dec">decimal</span></td><td>GB</td><td>SI (base-10)</td><td>1,000,000,000 bytes</td></tr>
      <tr><td>Gibibyte <span class="ba-badge ba-badge-bin">binary</span></td><td>GiB</td><td>IEC (base-2)</td><td>1,073,741,824 bytes</td></tr>
      <tr><td>Terabyte <span class="ba-badge ba-badge-dec">decimal</span></td><td>TB</td><td>SI (base-10)</td><td>10¹² bytes</td></tr>
      <tr><td>Tebibyte <span class="ba-badge ba-badge-bin">binary</span></td><td>TiB</td><td>IEC (base-2)</td><td>2⁴⁰ bytes</td></tr>
      <tr><td>Petabyte <span class="ba-badge ba-badge-dec">decimal</span></td><td>PB</td><td>SI (base-10)</td><td>10¹⁵ bytes</td></tr>
      <tr><td>Pebibyte <span class="ba-badge ba-badge-bin">binary</span></td><td>PiB</td><td>IEC (base-2)</td><td>2⁵⁰ bytes</td></tr>
    </tbody>
  </table>
</div>

<h2 class="ba-section-title">Why Binary vs. Decimal?</h2>

<p>Hard drive manufacturers use decimal (1 GB = 1,000,000,000 bytes) because the numbers look larger. Operating systems traditionally use binary (1 GiB = 1,073,741,824 bytes), which is why a "500 GB" drive shows as ~465 GiB in Windows or macOS. The IEC standardized the KiB/MiB/GiB suffixes in 1998 to eliminate ambiguity.</p>

<script>
(function() {
  // Bytes per unit
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
    bit:    'Bit (b)',
    byte:   'Byte (B)',
    kb_dec: 'Kilobyte (KB)',
    mb_dec: 'Megabyte (MB)',
    gb_dec: 'Gigabyte (GB)',
    tb_dec: 'Terabyte (TB)',
    pb_dec: 'Petabyte (PB)',
    kib:    'Kibibyte (KiB)',
    mib:    'Mebibyte (MiB)',
    gib:    'Gibibyte (GiB)',
    tib:    'Tebibyte (TiB)',
    pib:    'Pebibyte (PiB)'
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
    // Up to 10 significant digits, trim trailing zeros
    var s = parseFloat(n.toPrecision(10)).toString();
    // Add thousands separators for integer part
    var parts = s.split('.');
    parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    return parts.join('.');
  }

  function baFormatBytes(bytes) {
    if (bytes >= 1e15) return bytes.toExponential(4) + ' bytes';
    return parseFloat(bytes.toPrecision(12)).toLocaleString('en-US', {maximumFractionDigits: 4}) + ' bytes';
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
        ? '<span class="ba-badge ' + (isBin ? 'ba-badge-bin' : 'ba-badge-dec') + '">' + (isBin ? 'binary' : 'decimal') + '</span>'
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
    if (seconds < 1) return (seconds * 1000).toFixed(1) + ' ms';
    if (seconds < 60) return seconds.toFixed(2) + ' seconds';
    if (seconds < 3600) {
      var m = Math.floor(seconds / 60);
      var s = (seconds % 60).toFixed(0);
      return m + ' min ' + s + ' sec';
    }
    if (seconds < 86400) {
      var h = Math.floor(seconds / 3600);
      var rem = seconds % 3600;
      var m2 = Math.floor(rem / 60);
      return h + ' hr ' + m2 + ' min';
    }
    var d = (seconds / 86400).toFixed(1);
    return d + ' days';
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

    var fileMB = (fsize * BA_FACTORS[funit] / 1e6).toFixed(3);
    var speedMbps = (bitsPerSec / 1e6).toFixed(3);

    res.innerHTML =
      'File: <strong>' + baFormatNum(fsize) + ' ' + document.getElementById('ba-funit').options[document.getElementById('ba-funit').selectedIndex].text + '</strong> &nbsp;|&nbsp; ' +
      'Speed: <strong>' + baFormatNum(speed) + ' ' + document.getElementById('ba-spunit').options[document.getElementById('ba-spunit').selectedIndex].text + '</strong><br>' +
      'Estimated download time: <span class="ba-highlight">' + baFormatTime(seconds) + '</span>';
    res.style.display = 'block';
  };

  window.baBwClear = function() {
    document.getElementById('ba-fsize').value = '';
    document.getElementById('ba-speed').value = '';
    document.getElementById('ba-bw-error').style.display = 'none';
    document.getElementById('ba-bw-result').style.display = 'none';
  };

  // Allow Enter key to trigger conversion
  document.getElementById('ba-val').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') baConvert();
  });
})();
</script>

<div class="ba-crosslinks">
  <strong>Related Tools:</strong>
  <a href="/tools/unit-converter/">Unit Converter</a>
  <a href="/tools/binary-converter/">Binary Converter</a>
  <a href="/tools/ip-address-info/">IP Address Info</a>
</div>
</div>
