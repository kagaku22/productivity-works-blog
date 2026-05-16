---
title: "Hash Generator - Free SHA256, MD5, SHA1 Online Tool"
date: 2025-05-16
description: "Generate SHA-256, MD5, SHA-1, SHA-512 hashes instantly. Hash text or check file integrity. Free online cryptographic hash generator."
categories: ["Free Tools"]
tags: ["hash generator", "sha256", "md5", "sha1", "checksum"]
slug: "hash-generator"
aliases: ["/tools/sha256-generator/", "/tools/md5-generator/", "/tools/checksum/"]
cover:
  image: "/images/covers/hash-generator.png"
  alt: "Hash Generator"
ShowToc: false
---

<div id="hash-app">

<style>
#hash-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  background: #1e293b;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  max-width: 860px;
  margin: 0 auto;
  box-sizing: border-box;
}

#hash-app * {
  box-sizing: border-box;
}

#hash-app h2.ha-title {
  margin: 0 0 4px 0;
  font-size: 1.4rem;
  color: #f1f5f9;
}

#hash-app p.ha-subtitle {
  margin: 0 0 20px 0;
  font-size: 0.88rem;
  color: #94a3b8;
}

/* Tabs */
.ha-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 20px;
  background: #0f172a;
  padding: 4px;
  border-radius: 8px;
  flex-wrap: wrap;
}

.ha-tab {
  flex: 1;
  min-width: 100px;
  padding: 8px 12px;
  background: transparent;
  border: none;
  border-radius: 6px;
  color: #94a3b8;
  cursor: pointer;
  font-size: 0.82rem;
  font-weight: 500;
  transition: all 0.15s;
  text-align: center;
}

.ha-tab:hover {
  color: #e2e8f0;
  background: #1e293b;
}

.ha-tab.active {
  background: #f59e0b;
  color: #1e293b;
  font-weight: 700;
}

/* Panels */
.ha-panel {
  display: none;
}

.ha-panel.active {
  display: block;
}

/* Labels */
.ha-label {
  display: block;
  font-size: 0.78rem;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
}

/* Textarea */
.ha-textarea {
  width: 100%;
  min-height: 110px;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 0.9rem;
  padding: 12px;
  resize: vertical;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}

.ha-textarea:focus {
  border-color: #f59e0b;
}

/* Input */
.ha-input {
  width: 100%;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 0.9rem;
  padding: 10px 12px;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}

.ha-input:focus {
  border-color: #f59e0b;
}

/* Row layouts */
.ha-row {
  display: flex;
  gap: 12px;
  align-items: center;
  flex-wrap: wrap;
  margin-top: 12px;
}

.ha-row-spread {
  display: flex;
  gap: 12px;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-top: 12px;
}

/* Algorithm selector */
.ha-algo-group {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.ha-algo-btn {
  padding: 6px 14px;
  background: #1e3a5f;
  border: 1px solid #2d4a6e;
  border-radius: 6px;
  color: #93c5fd;
  cursor: pointer;
  font-size: 0.8rem;
  font-weight: 600;
  transition: all 0.15s;
}

.ha-algo-btn:hover {
  background: #1d4ed8;
  border-color: #3b82f6;
  color: #fff;
}

.ha-algo-btn.active {
  background: #f59e0b;
  border-color: #f59e0b;
  color: #1e293b;
}

/* Buttons */
.ha-btn {
  padding: 9px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 0.88rem;
  font-weight: 600;
  transition: all 0.15s;
}

.ha-btn-primary {
  background: #f59e0b;
  color: #1e293b;
}

.ha-btn-primary:hover {
  background: #d97706;
}

.ha-btn-secondary {
  background: #334155;
  color: #e2e8f0;
}

.ha-btn-secondary:hover {
  background: #475569;
}

.ha-btn-sm {
  padding: 6px 14px;
  font-size: 0.8rem;
}

/* Hash output */
.ha-output-block {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 14px;
  margin-top: 14px;
  position: relative;
}

.ha-output-label {
  font-size: 0.72rem;
  font-weight: 700;
  color: #f59e0b;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin-bottom: 6px;
}

.ha-hash-text {
  font-family: 'Courier New', Courier, monospace;
  font-size: 0.85rem;
  color: #86efac;
  word-break: break-all;
  line-height: 1.5;
  min-height: 1.5em;
}

.ha-hash-text.empty {
  color: #475569;
  font-style: italic;
  font-family: inherit;
  font-size: 0.82rem;
}

.ha-output-actions {
  display: flex;
  gap: 6px;
  margin-top: 10px;
  flex-wrap: wrap;
  align-items: center;
}

/* All-hash table */
.ha-all-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 14px;
}

.ha-all-table tr {
  border-bottom: 1px solid #1e3a5f;
}

.ha-all-table tr:last-child {
  border-bottom: none;
}

.ha-all-table td {
  padding: 10px 8px;
  vertical-align: top;
}

.ha-all-table td:first-child {
  font-size: 0.75rem;
  font-weight: 700;
  color: #f59e0b;
  white-space: nowrap;
  width: 90px;
  padding-top: 12px;
}

.ha-all-hash {
  font-family: 'Courier New', Courier, monospace;
  font-size: 0.78rem;
  color: #86efac;
  word-break: break-all;
  line-height: 1.6;
}

.ha-all-hash.empty {
  color: #475569;
  font-style: italic;
  font-family: inherit;
}

.ha-copy-mini {
  background: #1e3a5f;
  border: none;
  border-radius: 4px;
  color: #93c5fd;
  cursor: pointer;
  font-size: 0.7rem;
  padding: 2px 8px;
  margin-left: 6px;
  vertical-align: middle;
  transition: background 0.15s;
  white-space: nowrap;
}

.ha-copy-mini:hover {
  background: #1d4ed8;
  color: #fff;
}

/* Toggle switch */
.ha-toggle-wrap {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.8rem;
  color: #94a3b8;
}

.ha-toggle {
  position: relative;
  display: inline-block;
  width: 36px;
  height: 20px;
}

.ha-toggle input {
  opacity: 0;
  width: 0;
  height: 0;
}

.ha-slider {
  position: absolute;
  cursor: pointer;
  inset: 0;
  background: #334155;
  border-radius: 20px;
  transition: 0.2s;
}

.ha-slider:before {
  content: "";
  position: absolute;
  width: 14px;
  height: 14px;
  left: 3px;
  bottom: 3px;
  background: #fff;
  border-radius: 50%;
  transition: 0.2s;
}

.ha-toggle input:checked + .ha-slider {
  background: #f59e0b;
}

.ha-toggle input:checked + .ha-slider:before {
  transform: translateX(16px);
}

/* Divider */
.ha-divider {
  border: none;
  border-top: 1px solid #1e3a5f;
  margin: 20px 0;
}

/* Compare panel */
.ha-compare-result {
  padding: 12px 16px;
  border-radius: 8px;
  margin-top: 14px;
  font-size: 0.9rem;
  font-weight: 600;
  display: none;
  align-items: center;
  gap: 10px;
}

.ha-compare-result.match {
  display: flex;
  background: #14532d;
  border: 1px solid #16a34a;
  color: #86efac;
}

.ha-compare-result.nomatch {
  display: flex;
  background: #450a0a;
  border: 1px solid #dc2626;
  color: #fca5a5;
}

.ha-compare-icon {
  font-size: 1.3rem;
}

/* File panel */
.ha-dropzone {
  border: 2px dashed #334155;
  border-radius: 10px;
  padding: 36px 20px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
  background: #0f172a;
  position: relative;
}

.ha-dropzone.dragover {
  border-color: #f59e0b;
  background: #1e293b;
}

.ha-dropzone input[type="file"] {
  position: absolute;
  inset: 0;
  opacity: 0;
  cursor: pointer;
  width: 100%;
  height: 100%;
}

.ha-dropzone-icon {
  font-size: 2.4rem;
  margin-bottom: 10px;
  color: #475569;
}

.ha-dropzone-text {
  font-size: 0.9rem;
  color: #64748b;
}

.ha-dropzone-text strong {
  color: #f59e0b;
}

.ha-file-info {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 12px 14px;
  margin-top: 12px;
  font-size: 0.83rem;
  color: #94a3b8;
  display: none;
}

.ha-file-info span {
  color: #e2e8f0;
  font-weight: 600;
}

/* HMAC panel */
.ha-hmac-note {
  font-size: 0.8rem;
  color: #64748b;
  margin-top: 6px;
}

/* Progress bar for file */
.ha-progress-wrap {
  background: #0f172a;
  border-radius: 4px;
  height: 6px;
  margin-top: 10px;
  overflow: hidden;
  display: none;
}

.ha-progress-bar {
  height: 100%;
  background: #f59e0b;
  width: 0%;
  transition: width 0.1s;
}

/* Copy feedback */
.ha-copied-toast {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #f59e0b;
  color: #1e293b;
  padding: 8px 20px;
  border-radius: 999px;
  font-size: 0.85rem;
  font-weight: 700;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s, transform 0.2s;
  z-index: 9999;
}

.ha-copied-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

/* Responsive */
@media (max-width: 600px) {
  #hash-app {
    padding: 16px;
  }

  .ha-tab {
    font-size: 0.75rem;
    padding: 7px 8px;
  }

  .ha-all-table td:first-child {
    width: 70px;
    font-size: 0.7rem;
  }

  .ha-all-hash {
    font-size: 0.7rem;
  }
}
</style>

<h2 class="ha-title">Hash Generator</h2>
<p class="ha-subtitle">Generate cryptographic hashes instantly — MD5, SHA-1, SHA-256, SHA-384, SHA-512 &amp; HMAC</p>

<!-- Tabs -->
<div class="ha-tabs">
  <button class="ha-tab active" onclick="haShowTab('text', this)">Text Hash</button>
  <button class="ha-tab" onclick="haShowTab('all', this)">Generate All</button>
  <button class="ha-tab" onclick="haShowTab('compare', this)">Compare</button>
  <button class="ha-tab" onclick="haShowTab('file', this)">File Hash</button>
  <button class="ha-tab" onclick="haShowTab('hmac', this)">HMAC</button>
</div>

<!-- TEXT HASH PANEL -->
<div id="ha-panel-text" class="ha-panel active">
  <label class="ha-label">Input Text</label>
  <textarea class="ha-textarea" id="ha-text-input" placeholder="Type or paste text here..." oninput="haAutoHash()"></textarea>

  <div class="ha-row" style="margin-top:14px;">
    <div>
      <div class="ha-label" style="margin-bottom:8px;">Algorithm</div>
      <div class="ha-algo-group" id="ha-algo-group">
        <button class="ha-algo-btn" onclick="haSelectAlgo('MD5', this)">MD5</button>
        <button class="ha-algo-btn" onclick="haSelectAlgo('SHA-1', this)">SHA-1</button>
        <button class="ha-algo-btn active" onclick="haSelectAlgo('SHA-256', this)">SHA-256</button>
        <button class="ha-algo-btn" onclick="haSelectAlgo('SHA-384', this)">SHA-384</button>
        <button class="ha-algo-btn" onclick="haSelectAlgo('SHA-512', this)">SHA-512</button>
      </div>
    </div>
  </div>

  <div class="ha-row" style="margin-top:14px;">
    <button class="ha-btn ha-btn-primary" onclick="haDoHash()">Generate Hash</button>
    <button class="ha-btn ha-btn-secondary" onclick="haClearText()">Clear</button>
    <div class="ha-toggle-wrap" style="margin-left:auto;">
      <label class="ha-toggle">
        <input type="checkbox" id="ha-upper-toggle" onchange="haApplyCaseToggle()">
        <span class="ha-slider"></span>
      </label>
      Uppercase
    </div>
  </div>

  <div class="ha-output-block" id="ha-text-output-block">
    <div class="ha-output-label" id="ha-output-algo-label">SHA-256</div>
    <div class="ha-hash-text empty" id="ha-text-hash-output">Hash will appear here...</div>
    <div class="ha-output-actions">
      <button class="ha-btn ha-btn-secondary ha-btn-sm" onclick="haCopyHash('ha-text-hash-output')">Copy Hash</button>
    </div>
  </div>
</div>

<!-- GENERATE ALL PANEL -->
<div id="ha-panel-all" class="ha-panel">
  <label class="ha-label">Input Text</label>
  <textarea class="ha-textarea" id="ha-all-input" placeholder="Type or paste text to hash with all algorithms..." oninput="haGenerateAll()"></textarea>
  <div class="ha-row" style="margin-top:10px;">
    <button class="ha-btn ha-btn-primary" onclick="haGenerateAll()">Generate All</button>
    <button class="ha-btn ha-btn-secondary" onclick="haAllClear()">Clear</button>
  </div>

  <div class="ha-output-block" style="margin-top:14px; padding:0 14px;">
    <table class="ha-all-table">
      <tbody id="ha-all-tbody">
        <tr>
          <td>MD5</td>
          <td><span class="ha-all-hash empty" id="ha-all-md5">—</span>
            <button class="ha-copy-mini" onclick="haCopyHash('ha-all-md5')">copy</button></td>
        </tr>
        <tr>
          <td>SHA-1</td>
          <td><span class="ha-all-hash empty" id="ha-all-sha1">—</span>
            <button class="ha-copy-mini" onclick="haCopyHash('ha-all-sha1')">copy</button></td>
        </tr>
        <tr>
          <td>SHA-256</td>
          <td><span class="ha-all-hash empty" id="ha-all-sha256">—</span>
            <button class="ha-copy-mini" onclick="haCopyHash('ha-all-sha256')">copy</button></td>
        </tr>
        <tr>
          <td>SHA-384</td>
          <td><span class="ha-all-hash empty" id="ha-all-sha384">—</span>
            <button class="ha-copy-mini" onclick="haCopyHash('ha-all-sha384')">copy</button></td>
        </tr>
        <tr>
          <td>SHA-512</td>
          <td><span class="ha-all-hash empty" id="ha-all-sha512">—</span>
            <button class="ha-copy-mini" onclick="haCopyHash('ha-all-sha512')">copy</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<!-- COMPARE PANEL -->
<div id="ha-panel-compare" class="ha-panel">
  <p style="font-size:0.85rem;color:#94a3b8;margin:0 0 16px;">Paste two hashes below to check if they match — useful for verifying file integrity checksums.</p>

  <label class="ha-label">Hash A</label>
  <input class="ha-input" type="text" id="ha-cmp-a" placeholder="Paste first hash..." oninput="haCompare()">

  <div style="margin-top:12px;">
    <label class="ha-label">Hash B</label>
    <input class="ha-input" type="text" id="ha-cmp-b" placeholder="Paste second hash..." oninput="haCompare()">
  </div>

  <div class="ha-compare-result" id="ha-cmp-result">
    <span class="ha-compare-icon" id="ha-cmp-icon"></span>
    <span id="ha-cmp-text"></span>
  </div>
</div>

<!-- FILE HASH PANEL -->
<div id="ha-panel-file" class="ha-panel">
  <div class="ha-row" style="margin:0 0 12px;">
    <div>
      <div class="ha-label" style="margin-bottom:8px;">Algorithm</div>
      <div class="ha-algo-group" id="ha-file-algo-group">
        <button class="ha-algo-btn" onclick="haSelectFileAlgo('MD5', this)">MD5</button>
        <button class="ha-algo-btn" onclick="haSelectFileAlgo('SHA-1', this)">SHA-1</button>
        <button class="ha-algo-btn active" onclick="haSelectFileAlgo('SHA-256', this)">SHA-256</button>
        <button class="ha-algo-btn" onclick="haSelectFileAlgo('SHA-384', this)">SHA-384</button>
        <button class="ha-algo-btn" onclick="haSelectFileAlgo('SHA-512', this)">SHA-512</button>
      </div>
    </div>
  </div>

  <div class="ha-dropzone" id="ha-dropzone"
       ondragover="haFileDragOver(event)"
       ondragleave="haFileDragLeave(event)"
       ondrop="haFileDrop(event)">
    <input type="file" id="ha-file-input" onchange="haFileSelected(event)">
    <div class="ha-dropzone-icon">&#128196;</div>
    <div class="ha-dropzone-text">
      <strong>Click to choose a file</strong> or drag &amp; drop here<br>
      <span style="font-size:0.78rem;color:#475569;">Any file type &bull; Processed locally in your browser</span>
    </div>
  </div>

  <div class="ha-progress-wrap" id="ha-file-progress-wrap">
    <div class="ha-progress-bar" id="ha-file-progress-bar"></div>
  </div>

  <div class="ha-file-info" id="ha-file-info">
    File: <span id="ha-file-name">—</span> &nbsp;|&nbsp; Size: <span id="ha-file-size">—</span>
  </div>

  <div class="ha-output-block" id="ha-file-output-block" style="display:none;">
    <div class="ha-output-label" id="ha-file-output-algo-label">SHA-256</div>
    <div class="ha-hash-text" id="ha-file-hash-output"></div>
    <div class="ha-output-actions" style="margin-top:10px;">
      <button class="ha-btn ha-btn-secondary ha-btn-sm" onclick="haCopyHash('ha-file-hash-output')">Copy Hash</button>
    </div>
  </div>
</div>

<!-- HMAC PANEL -->
<div id="ha-panel-hmac" class="ha-panel">
  <p style="font-size:0.85rem;color:#94a3b8;margin:0 0 16px;">HMAC combines a secret key with a hash function to produce a message authentication code.</p>

  <label class="ha-label">Message</label>
  <textarea class="ha-textarea" id="ha-hmac-message" placeholder="Enter the message..." oninput="haAutoHmac()"></textarea>

  <div style="margin-top:12px;">
    <label class="ha-label">Secret Key</label>
    <input class="ha-input" type="text" id="ha-hmac-key" placeholder="Enter your secret key..." oninput="haAutoHmac()">
    <div class="ha-hmac-note">Keep your secret key private. The HMAC value changes completely with any change to key or message.</div>
  </div>

  <div class="ha-row" style="margin-top:14px;">
    <div>
      <div class="ha-label" style="margin-bottom:8px;">Algorithm</div>
      <div class="ha-algo-group" id="ha-hmac-algo-group">
        <button class="ha-algo-btn" onclick="haSelectHmacAlgo('SHA-1', this)">SHA-1</button>
        <button class="ha-algo-btn active" onclick="haSelectHmacAlgo('SHA-256', this)">SHA-256</button>
        <button class="ha-algo-btn" onclick="haSelectHmacAlgo('SHA-384', this)">SHA-384</button>
        <button class="ha-algo-btn" onclick="haSelectHmacAlgo('SHA-512', this)">SHA-512</button>
      </div>
    </div>
  </div>

  <div class="ha-row" style="margin-top:14px;">
    <button class="ha-btn ha-btn-primary" onclick="haDoHmac()">Generate HMAC</button>
    <button class="ha-btn ha-btn-secondary" onclick="haHmacClear()">Clear</button>
  </div>

  <div class="ha-output-block" style="margin-top:14px;">
    <div class="ha-output-label" id="ha-hmac-output-label">HMAC-SHA-256</div>
    <div class="ha-hash-text empty" id="ha-hmac-output">HMAC will appear here...</div>
    <div class="ha-output-actions" style="margin-top:10px;">
      <button class="ha-btn ha-btn-secondary ha-btn-sm" onclick="haCopyHash('ha-hmac-output')">Copy HMAC</button>
    </div>
  </div>
</div>

<!-- Toast -->
<div class="ha-copied-toast" id="ha-toast">Copied!</div>

</div><!-- end #hash-app -->

<script>
(function () {
  'use strict';

  /* ─── State ─────────────────────────────── */
  let haCurrentAlgo = 'SHA-256';
  let haFileAlgo    = 'SHA-256';
  let haHmacAlgo    = 'SHA-256';
  let haUppercase   = false;
  let haAutoTimer   = null;
  let haLastHash    = '';

  /* ─── MD5 Implementation ─────────────────────────── */
  // Pure JS MD5 (RFC 1321)
  function haMD5(str) {
    function safeAdd(x, y) {
      var lsw = (x & 0xffff) + (y & 0xffff);
      var msw = (x >> 16) + (y >> 16) + (lsw >> 16);
      return (msw << 16) | (lsw & 0xffff);
    }
    function bitRotateLeft(num, cnt) { return (num << cnt) | (num >>> (32 - cnt)); }
    function md5cmn(q, a, b, x, s, t) { return safeAdd(bitRotateLeft(safeAdd(safeAdd(a, q), safeAdd(x, t)), s), b); }
    function md5ff(a, b, c, d, x, s, t) { return md5cmn((b & c) | (~b & d), a, b, x, s, t); }
    function md5gg(a, b, c, d, x, s, t) { return md5cmn((b & d) | (c & ~d), a, b, x, s, t); }
    function md5hh(a, b, c, d, x, s, t) { return md5cmn(b ^ c ^ d, a, b, x, s, t); }
    function md5ii(a, b, c, d, x, s, t) { return md5cmn(c ^ (b | ~d), a, b, x, s, t); }

    function md5blk(s) {
      var md5blks = [];
      for (var i = 0; i < 64; i += 4) {
        md5blks[i >> 2] = s.charCodeAt(i) + (s.charCodeAt(i + 1) << 8) + (s.charCodeAt(i + 2) << 16) + (s.charCodeAt(i + 3) << 24);
      }
      return md5blks;
    }

    function md5blk_array(a) {
      var md5blks = [];
      for (var i = 0; i < 64; i += 4) {
        md5blks[i >> 2] = a[i] + (a[i + 1] << 8) + (a[i + 2] << 16) + (a[i + 3] << 24);
      }
      return md5blks;
    }

    function md51(s) {
      var n = s.length;
      var state = [1732584193, -271733879, -1732584194, 271733878];
      var i;
      for (i = 64; i <= s.length; i += 64) {
        md5cycle(state, md5blk(s.substring(i - 64, i)));
      }
      s = s.substring(i - 64);
      var tail = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
      for (i = 0; i < s.length; i++) {
        tail[i >> 2] |= s.charCodeAt(i) << ((i % 4) << 3);
      }
      tail[i >> 2] |= 0x80 << ((i % 4) << 3);
      if (i > 55) {
        md5cycle(state, tail);
        for (i = 0; i < 16; i++) tail[i] = 0;
      }
      tail[14] = n * 8;
      md5cycle(state, tail);
      return state;
    }

    function md51_array(a) {
      var n = a.length;
      var state = [1732584193, -271733879, -1732584194, 271733878];
      var i;
      for (i = 64; i <= a.length; i += 64) {
        md5cycle(state, md5blk_array(a.slice(i - 64, i)));
      }
      a = a.slice(i - 64);
      var tail = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
      for (i = 0; i < a.length; i++) {
        tail[i >> 2] |= a[i] << ((i % 4) << 3);
      }
      tail[i >> 2] |= 0x80 << ((i % 4) << 3);
      if (i > 55) {
        md5cycle(state, tail);
        for (i = 0; i < 16; i++) tail[i] = 0;
      }
      tail[14] = n * 8;
      md5cycle(state, tail);
      return state;
    }

    function md5cycle(x, k) {
      var a = x[0], b = x[1], c = x[2], d = x[3];
      a = md5ff(a, b, c, d, k[0], 7, -680876936);
      d = md5ff(d, a, b, c, k[1], 12, -389564586);
      c = md5ff(c, d, a, b, k[2], 17, 606105819);
      b = md5ff(b, c, d, a, k[3], 22, -1044525330);
      a = md5ff(a, b, c, d, k[4], 7, -176418897);
      d = md5ff(d, a, b, c, k[5], 12, 1200080426);
      c = md5ff(c, d, a, b, k[6], 17, -1473231341);
      b = md5ff(b, c, d, a, k[7], 22, -45705983);
      a = md5ff(a, b, c, d, k[8], 7, 1770035416);
      d = md5ff(d, a, b, c, k[9], 12, -1958414417);
      c = md5ff(c, d, a, b, k[10], 17, -42063);
      b = md5ff(b, c, d, a, k[11], 22, -1990404162);
      a = md5ff(a, b, c, d, k[12], 7, 1804603682);
      d = md5ff(d, a, b, c, k[13], 12, -40341101);
      c = md5ff(c, d, a, b, k[14], 17, -1502002290);
      b = md5ff(b, c, d, a, k[15], 22, 1236535329);
      a = md5gg(a, b, c, d, k[1], 5, -165796510);
      d = md5gg(d, a, b, c, k[6], 9, -1069501632);
      c = md5gg(c, d, a, b, k[11], 14, 643717713);
      b = md5gg(b, c, d, a, k[0], 20, -373897302);
      a = md5gg(a, b, c, d, k[5], 5, -701558691);
      d = md5gg(d, a, b, c, k[10], 9, 38016083);
      c = md5gg(c, d, a, b, k[15], 14, -660478335);
      b = md5gg(b, c, d, a, k[4], 20, -405537848);
      a = md5gg(a, b, c, d, k[9], 5, 568446438);
      d = md5gg(d, a, b, c, k[14], 9, -1019803690);
      c = md5gg(c, d, a, b, k[3], 14, -187363961);
      b = md5gg(b, c, d, a, k[8], 20, 1163531501);
      a = md5gg(a, b, c, d, k[13], 5, -1444681467);
      d = md5gg(d, a, b, c, k[2], 9, -51403784);
      c = md5gg(c, d, a, b, k[7], 14, 1735328473);
      b = md5gg(b, c, d, a, k[12], 20, -1926607734);
      a = md5hh(a, b, c, d, k[5], 4, -378558);
      d = md5hh(d, a, b, c, k[8], 11, -2022574463);
      c = md5hh(c, d, a, b, k[11], 16, 1839030562);
      b = md5hh(b, c, d, a, k[14], 23, -35309556);
      a = md5hh(a, b, c, d, k[1], 4, -1530992060);
      d = md5hh(d, a, b, c, k[4], 11, 1272893353);
      c = md5hh(c, d, a, b, k[7], 16, -155497632);
      b = md5hh(b, c, d, a, k[10], 23, -1094730640);
      a = md5hh(a, b, c, d, k[13], 4, 681279174);
      d = md5hh(d, a, b, c, k[0], 11, -358537222);
      c = md5hh(c, d, a, b, k[3], 16, -722521979);
      b = md5hh(b, c, d, a, k[6], 23, 76029189);
      a = md5hh(a, b, c, d, k[9], 4, -640364487);
      d = md5hh(d, a, b, c, k[12], 11, -421815835);
      c = md5hh(c, d, a, b, k[15], 16, 530742520);
      b = md5hh(b, c, d, a, k[2], 23, -995338651);
      a = md5ii(a, b, c, d, k[0], 6, -198630844);
      d = md5ii(d, a, b, c, k[7], 10, 1126891415);
      c = md5ii(c, d, a, b, k[14], 15, -1416354905);
      b = md5ii(b, c, d, a, k[5], 21, -57434055);
      a = md5ii(a, b, c, d, k[12], 6, 1700485571);
      d = md5ii(d, a, b, c, k[3], 10, -1894986606);
      c = md5ii(c, d, a, b, k[10], 15, -1051523);
      b = md5ii(b, c, d, a, k[1], 21, -2054922799);
      a = md5ii(a, b, c, d, k[8], 6, 1873313359);
      d = md5ii(d, a, b, c, k[15], 10, -30611744);
      c = md5ii(c, d, a, b, k[6], 15, -1560198380);
      b = md5ii(b, c, d, a, k[13], 21, 1309151649);
      a = md5ii(a, b, c, d, k[4], 6, -145523070);
      d = md5ii(d, a, b, c, k[11], 10, -1120210379);
      c = md5ii(c, d, a, b, k[2], 15, 718787259);
      b = md5ii(b, c, d, a, k[9], 21, -343485551);
      x[0] = safeAdd(a, x[0]);
      x[1] = safeAdd(b, x[1]);
      x[2] = safeAdd(c, x[2]);
      x[3] = safeAdd(d, x[3]);
    }

    function hex_chr(num) { return '0123456789abcdef'.charAt(num); }

    function rhex(n) {
      var s = '';
      for (var j = 0; j < 4; j++) {
        s += hex_chr((n >> (j * 8 + 4)) & 0x0f) + hex_chr((n >> (j * 8)) & 0x0f);
      }
      return s;
    }

    function hex(x) { return x.map(rhex).join(''); }

    // Encode string to UTF-8 byte string
    var utf8Str = unescape(encodeURIComponent(str));
    return hex(md51(utf8Str));
  }

  /* ─── MD5 for ArrayBuffer (file hashing) ─────────── */
  function haMD5Buffer(buffer) {
    function safeAdd(x, y) {
      var lsw = (x & 0xffff) + (y & 0xffff);
      var msw = (x >> 16) + (y >> 16) + (lsw >> 16);
      return (msw << 16) | (lsw & 0xffff);
    }
    function bitRotateLeft(num, cnt) { return (num << cnt) | (num >>> (32 - cnt)); }
    function md5cmn(q, a, b, x, s, t) { return safeAdd(bitRotateLeft(safeAdd(safeAdd(a, q), safeAdd(x, t)), s), b); }
    function md5ff(a, b, c, d, x, s, t) { return md5cmn((b & c) | (~b & d), a, b, x, s, t); }
    function md5gg(a, b, c, d, x, s, t) { return md5cmn((b & d) | (c & ~d), a, b, x, s, t); }
    function md5hh(a, b, c, d, x, s, t) { return md5cmn(b ^ c ^ d, a, b, x, s, t); }
    function md5ii(a, b, c, d, x, s, t) { return md5cmn(c ^ (b | ~d), a, b, x, s, t); }

    var a = new Uint8Array(buffer);
    var n = a.length;
    var state = [1732584193, -271733879, -1732584194, 271733878];

    function md5blk_array(arr) {
      var md5blks = [];
      for (var i = 0; i < 64; i += 4) {
        md5blks[i >> 2] = (arr[i] || 0) + ((arr[i + 1] || 0) << 8) + ((arr[i + 2] || 0) << 16) + ((arr[i + 3] || 0) << 24);
      }
      return md5blks;
    }

    function md5cycle(x, k) {
      var a2 = x[0], b = x[1], c = x[2], d = x[3];
      a2 = md5ff(a2, b, c, d, k[0], 7, -680876936); d = md5ff(d, a2, b, c, k[1], 12, -389564586);
      c = md5ff(c, d, a2, b, k[2], 17, 606105819); b = md5ff(b, c, d, a2, k[3], 22, -1044525330);
      a2 = md5ff(a2, b, c, d, k[4], 7, -176418897); d = md5ff(d, a2, b, c, k[5], 12, 1200080426);
      c = md5ff(c, d, a2, b, k[6], 17, -1473231341); b = md5ff(b, c, d, a2, k[7], 22, -45705983);
      a2 = md5ff(a2, b, c, d, k[8], 7, 1770035416); d = md5ff(d, a2, b, c, k[9], 12, -1958414417);
      c = md5ff(c, d, a2, b, k[10], 17, -42063); b = md5ff(b, c, d, a2, k[11], 22, -1990404162);
      a2 = md5ff(a2, b, c, d, k[12], 7, 1804603682); d = md5ff(d, a2, b, c, k[13], 12, -40341101);
      c = md5ff(c, d, a2, b, k[14], 17, -1502002290); b = md5ff(b, c, d, a2, k[15], 22, 1236535329);
      a2 = md5gg(a2, b, c, d, k[1], 5, -165796510); d = md5gg(d, a2, b, c, k[6], 9, -1069501632);
      c = md5gg(c, d, a2, b, k[11], 14, 643717713); b = md5gg(b, c, d, a2, k[0], 20, -373897302);
      a2 = md5gg(a2, b, c, d, k[5], 5, -701558691); d = md5gg(d, a2, b, c, k[10], 9, 38016083);
      c = md5gg(c, d, a2, b, k[15], 14, -660478335); b = md5gg(b, c, d, a2, k[4], 20, -405537848);
      a2 = md5gg(a2, b, c, d, k[9], 5, 568446438); d = md5gg(d, a2, b, c, k[14], 9, -1019803690);
      c = md5gg(c, d, a2, b, k[3], 14, -187363961); b = md5gg(b, c, d, a2, k[8], 20, 1163531501);
      a2 = md5gg(a2, b, c, d, k[13], 5, -1444681467); d = md5gg(d, a2, b, c, k[2], 9, -51403784);
      c = md5gg(c, d, a2, b, k[7], 14, 1735328473); b = md5gg(b, c, d, a2, k[12], 20, -1926607734);
      a2 = md5hh(a2, b, c, d, k[5], 4, -378558); d = md5hh(d, a2, b, c, k[8], 11, -2022574463);
      c = md5hh(c, d, a2, b, k[11], 16, 1839030562); b = md5hh(b, c, d, a2, k[14], 23, -35309556);
      a2 = md5hh(a2, b, c, d, k[1], 4, -1530992060); d = md5hh(d, a2, b, c, k[4], 11, 1272893353);
      c = md5hh(c, d, a2, b, k[7], 16, -155497632); b = md5hh(b, c, d, a2, k[10], 23, -1094730640);
      a2 = md5hh(a2, b, c, d, k[13], 4, 681279174); d = md5hh(d, a2, b, c, k[0], 11, -358537222);
      c = md5hh(c, d, a2, b, k[3], 16, -722521979); b = md5hh(b, c, d, a2, k[6], 23, 76029189);
      a2 = md5hh(a2, b, c, d, k[9], 4, -640364487); d = md5hh(d, a2, b, c, k[12], 11, -421815835);
      c = md5hh(c, d, a2, b, k[15], 16, 530742520); b = md5hh(b, c, d, a2, k[2], 23, -995338651);
      a2 = md5ii(a2, b, c, d, k[0], 6, -198630844); d = md5ii(d, a2, b, c, k[7], 10, 1126891415);
      c = md5ii(c, d, a2, b, k[14], 15, -1416354905); b = md5ii(b, c, d, a2, k[5], 21, -57434055);
      a2 = md5ii(a2, b, c, d, k[12], 6, 1700485571); d = md5ii(d, a2, b, c, k[3], 10, -1894986606);
      c = md5ii(c, d, a2, b, k[10], 15, -1051523); b = md5ii(b, c, d, a2, k[1], 21, -2054922799);
      a2 = md5ii(a2, b, c, d, k[8], 6, 1873313359); d = md5ii(d, a2, b, c, k[15], 10, -30611744);
      c = md5ii(c, d, a2, b, k[6], 15, -1560198380); b = md5ii(b, c, d, a2, k[13], 21, 1309151649);
      a2 = md5ii(a2, b, c, d, k[4], 6, -145523070); d = md5ii(d, a2, b, c, k[11], 10, -1120210379);
      c = md5ii(c, d, a2, b, k[2], 15, 718787259); b = md5ii(b, c, d, a2, k[9], 21, -343485551);
      x[0] = safeAdd(a2, x[0]); x[1] = safeAdd(b, x[1]);
      x[2] = safeAdd(c, x[2]); x[3] = safeAdd(d, x[3]);
    }

    for (var i = 64; i <= n; i += 64) {
      md5cycle(state, md5blk_array(a.subarray(i - 64, i)));
    }
    var remaining = a.subarray(i - 64);
    var tail = new Array(16).fill(0);
    for (var j = 0; j < remaining.length; j++) {
      tail[j >> 2] |= remaining[j] << ((j % 4) << 3);
    }
    tail[j >> 2] |= 0x80 << ((j % 4) << 3);
    if (j > 55) {
      md5cycle(state, tail);
      tail = new Array(16).fill(0);
    }
    tail[14] = n * 8;
    md5cycle(state, tail);

    function rhex(n2) {
      var s = '';
      for (var k = 0; k < 4; k++) {
        s += '0123456789abcdef'.charAt((n2 >> (k * 8 + 4)) & 0x0f) +
             '0123456789abcdef'.charAt((n2 >> (k * 8)) & 0x0f);
      }
      return s;
    }
    return state.map(rhex).join('');
  }

  /* ─── Web Crypto Helpers ─────────────────────────── */
  function haEncode(str) {
    return new TextEncoder().encode(str);
  }

  function haBufferToHex(buf) {
    return Array.from(new Uint8Array(buf))
      .map(function (b) { return ('00' + b.toString(16)).slice(-2); })
      .join('');
  }

  async function haWebCryptoHash(algo, data) {
    var buf = await crypto.subtle.digest(algo, data);
    return haBufferToHex(buf);
  }

  async function haHash(algo, text) {
    if (algo === 'MD5') {
      return haMD5(text);
    }
    return haWebCryptoHash(algo, haEncode(text));
  }

  async function haHashBuffer(algo, buffer) {
    if (algo === 'MD5') {
      return haMD5Buffer(buffer);
    }
    return haWebCryptoHash(algo, buffer);
  }

  function haApplyCase(str) {
    return haUppercase ? str.toUpperCase() : str.toLowerCase();
  }

  /* ─── Tab switching ──────────────────────────────── */
  window.haShowTab = function (name, btn) {
    document.querySelectorAll('#hash-app .ha-panel').forEach(function (p) { p.classList.remove('active'); });
    document.querySelectorAll('#hash-app .ha-tab').forEach(function (t) { t.classList.remove('active'); });
    document.getElementById('ha-panel-' + name).classList.add('active');
    btn.classList.add('active');
  };

  /* ─── Algorithm selection ────────────────────────── */
  window.haSelectAlgo = function (algo, btn) {
    haCurrentAlgo = algo;
    document.querySelectorAll('#ha-algo-group .ha-algo-btn').forEach(function (b) { b.classList.remove('active'); });
    btn.classList.add('active');
    document.getElementById('ha-output-algo-label').textContent = algo;
    haAutoHash();
  };

  window.haSelectFileAlgo = function (algo, btn) {
    haFileAlgo = algo;
    document.querySelectorAll('#ha-file-algo-group .ha-algo-btn').forEach(function (b) { b.classList.remove('active'); });
    btn.classList.add('active');
    document.getElementById('ha-file-output-algo-label').textContent = algo;
  };

  window.haSelectHmacAlgo = function (algo, btn) {
    haHmacAlgo = algo;
    document.querySelectorAll('#ha-hmac-algo-group .ha-algo-btn').forEach(function (b) { b.classList.remove('active'); });
    btn.classList.add('active');
    document.getElementById('ha-hmac-output-label').textContent = 'HMAC-' + algo;
    haAutoHmac();
  };

  /* ─── Text hash (auto + manual) ─────────────────── */
  window.haAutoHash = function () {
    clearTimeout(haAutoTimer);
    haAutoTimer = setTimeout(function () { haDoHash(); }, 150);
  };

  window.haDoHash = async function () {
    var text = document.getElementById('ha-text-input').value;
    var el = document.getElementById('ha-text-hash-output');
    if (!text) {
      el.textContent = 'Hash will appear here...';
      el.classList.add('empty');
      haLastHash = '';
      return;
    }
    try {
      var h = await haHash(haCurrentAlgo, text);
      haLastHash = h;
      el.textContent = haApplyCase(h);
      el.classList.remove('empty');
    } catch (e) {
      el.textContent = 'Error: ' + e.message;
      el.classList.add('empty');
    }
  };

  window.haClearText = function () {
    document.getElementById('ha-text-input').value = '';
    var el = document.getElementById('ha-text-hash-output');
    el.textContent = 'Hash will appear here...';
    el.classList.add('empty');
    haLastHash = '';
  };

  window.haApplyCaseToggle = function () {
    haUppercase = document.getElementById('ha-upper-toggle').checked;
    if (haLastHash) {
      document.getElementById('ha-text-hash-output').textContent = haApplyCase(haLastHash);
    }
  };

  /* ─── Generate All ───────────────────────────────── */
  var haAllTimer = null;

  window.haGenerateAll = async function () {
    var text = document.getElementById('ha-all-input').value;
    var algos = ['MD5', 'SHA-1', 'SHA-256', 'SHA-384', 'SHA-512'];
    var ids    = ['ha-all-md5', 'ha-all-sha1', 'ha-all-sha256', 'ha-all-sha384', 'ha-all-sha512'];

    if (!text) {
      ids.forEach(function (id) {
        var el = document.getElementById(id);
        el.textContent = '—';
        el.classList.add('empty');
      });
      return;
    }

    for (var i = 0; i < algos.length; i++) {
      try {
        var h = await haHash(algos[i], text);
        var el = document.getElementById(ids[i]);
        el.textContent = h;
        el.classList.remove('empty');
      } catch (e) {
        document.getElementById(ids[i]).textContent = 'Error';
      }
    }
  };

  window.haAllClear = function () {
    document.getElementById('ha-all-input').value = '';
    ['ha-all-md5','ha-all-sha1','ha-all-sha256','ha-all-sha384','ha-all-sha512'].forEach(function (id) {
      var el = document.getElementById(id);
      el.textContent = '—';
      el.classList.add('empty');
    });
  };

  /* ─── Compare ────────────────────────────────────── */
  window.haCompare = function () {
    var a = document.getElementById('ha-cmp-a').value.trim().toLowerCase();
    var b = document.getElementById('ha-cmp-b').value.trim().toLowerCase();
    var result = document.getElementById('ha-cmp-result');
    var icon   = document.getElementById('ha-cmp-icon');
    var text   = document.getElementById('ha-cmp-text');

    if (!a || !b) {
      result.className = 'ha-compare-result';
      return;
    }

    if (a === b) {
      result.className = 'ha-compare-result match';
      icon.textContent = '\u2714';
      text.textContent = 'Hashes match — the data is identical.';
    } else {
      result.className = 'ha-compare-result nomatch';
      icon.textContent = '\u2718';
      text.textContent = 'Hashes do NOT match — the data differs.';
    }
  };

  /* ─── File Hash ──────────────────────────────────── */
  window.haFileDragOver = function (e) {
    e.preventDefault();
    document.getElementById('ha-dropzone').classList.add('dragover');
  };

  window.haFileDragLeave = function (e) {
    document.getElementById('ha-dropzone').classList.remove('dragover');
  };

  window.haFileDrop = function (e) {
    e.preventDefault();
    document.getElementById('ha-dropzone').classList.remove('dragover');
    var file = e.dataTransfer.files[0];
    if (file) haProcessFile(file);
  };

  window.haFileSelected = function (e) {
    var file = e.target.files[0];
    if (file) haProcessFile(file);
  };

  function haFormatBytes(bytes) {
    if (bytes < 1024) return bytes + ' B';
    if (bytes < 1048576) return (bytes / 1024).toFixed(1) + ' KB';
    return (bytes / 1048576).toFixed(2) + ' MB';
  }

  function haProcessFile(file) {
    var infoEl = document.getElementById('ha-file-info');
    infoEl.style.display = 'block';
    document.getElementById('ha-file-name').textContent = file.name;
    document.getElementById('ha-file-size').textContent = haFormatBytes(file.size);

    var progressWrap = document.getElementById('ha-file-progress-wrap');
    var progressBar  = document.getElementById('ha-file-progress-bar');
    progressWrap.style.display = 'block';
    progressBar.style.width = '0%';

    var outputBlock = document.getElementById('ha-file-output-block');
    outputBlock.style.display = 'none';

    var reader = new FileReader();
    reader.onprogress = function (e) {
      if (e.lengthComputable) {
        progressBar.style.width = Math.round((e.loaded / e.total) * 90) + '%';
      }
    };
    reader.onload = async function (e) {
      progressBar.style.width = '100%';
      try {
        var h = await haHashBuffer(haFileAlgo, e.target.result);
        var hashEl = document.getElementById('ha-file-hash-output');
        hashEl.textContent = h;
        hashEl.classList.remove('empty');
        outputBlock.style.display = 'block';
      } catch (err) {
        document.getElementById('ha-file-hash-output').textContent = 'Error: ' + err.message;
        outputBlock.style.display = 'block';
      }
      setTimeout(function () { progressWrap.style.display = 'none'; }, 600);
    };
    reader.onerror = function () {
      progressWrap.style.display = 'none';
      alert('Failed to read file.');
    };
    reader.readAsArrayBuffer(file);
  }

  /* ─── HMAC ───────────────────────────────────────── */
  var haHmacTimer = null;

  window.haAutoHmac = function () {
    clearTimeout(haHmacTimer);
    haHmacTimer = setTimeout(function () { haDoHmac(); }, 200);
  };

  window.haDoHmac = async function () {
    var message = document.getElementById('ha-hmac-message').value;
    var key     = document.getElementById('ha-hmac-key').value;
    var el      = document.getElementById('ha-hmac-output');

    if (!message || !key) {
      el.textContent = 'HMAC will appear here...';
      el.classList.add('empty');
      return;
    }

    try {
      var algoMap = { 'SHA-1': 'SHA-1', 'SHA-256': 'SHA-256', 'SHA-384': 'SHA-384', 'SHA-512': 'SHA-512' };
      var cryptoAlgo = algoMap[haHmacAlgo] || 'SHA-256';

      var cryptoKey = await crypto.subtle.importKey(
        'raw',
        haEncode(key),
        { name: 'HMAC', hash: cryptoAlgo },
        false,
        ['sign']
      );

      var sig = await crypto.subtle.sign('HMAC', cryptoKey, haEncode(message));
      var h = haBufferToHex(sig);
      el.textContent = haApplyCase(h);
      el.classList.remove('empty');
    } catch (e) {
      el.textContent = 'Error: ' + e.message;
      el.classList.add('empty');
    }
  };

  window.haHmacClear = function () {
    document.getElementById('ha-hmac-message').value = '';
    document.getElementById('ha-hmac-key').value = '';
    var el = document.getElementById('ha-hmac-output');
    el.textContent = 'HMAC will appear here...';
    el.classList.add('empty');
  };

  /* ─── Copy ───────────────────────────────────────── */
  window.haCopyHash = function (id) {
    var el = document.getElementById(id);
    var text = el.textContent;
    if (!text || el.classList.contains('empty') || text === '—') return;
    navigator.clipboard.writeText(text).then(function () {
      haShowToast('Copied!');
    }).catch(function () {
      // Fallback
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      haShowToast('Copied!');
    });
  };

  function haShowToast(msg) {
    var toast = document.getElementById('ha-toast');
    toast.textContent = msg;
    toast.classList.add('show');
    setTimeout(function () { toast.classList.remove('show'); }, 1800);
  }

})();
</script>

---

## What is a Hash Function?

A cryptographic hash function is a mathematical algorithm that transforms any input — whether a single character or an entire gigabyte file — into a fixed-length string of characters called a hash or digest. The process is deterministic (the same input always produces the same output) and effectively one-way: it is computationally infeasible to reverse a hash back into its original data. Even the smallest change to the input, such as flipping a single bit, produces a completely different hash output — a property known as the avalanche effect. This makes hash functions invaluable for verifying data integrity, since any tampering with a file or message will produce a detectably different digest.

Hash functions underpin a wide range of security-critical applications. Password storage systems hash user passwords before saving them so that even a compromised database does not expose plaintext credentials. Software distributors publish SHA-256 checksums alongside downloads so users can independently verify that the file was not corrupted or tampered with in transit. Digital signatures rely on hashing the signed document so that signing the compact digest — rather than the full document — is both efficient and equally secure. Blockchain systems chain blocks together using cryptographic hashes, making the historical record tamper-evident by design. Understanding which algorithm to choose, and its trade-offs, is essential for any developer or security practitioner working with sensitive data.

---

## Common Hash Algorithms

**MD5 (128-bit)** — Designed in 1991 by Ron Rivest, MD5 produces a 32-character hexadecimal digest. It is fast and widely recognized, but cryptographic weaknesses (collision vulnerabilities) discovered in the mid-2000s mean it is no longer suitable for security-sensitive applications such as digital signatures or certificate generation. It remains useful for non-security checksums, such as quickly verifying a file download against an expected value when tampering is not a concern.

**SHA-1 (160-bit)** — Developed by the NSA and published in 1995, SHA-1 produces a 40-character hex digest. Like MD5, SHA-1 has been found to have theoretical and practical collision vulnerabilities; Google demonstrated a real-world SHA-1 collision (SHAttered) in 2017. Major browsers and certificate authorities have deprecated SHA-1 for TLS certificates. It is still encountered in legacy systems and Git object identifiers, though migration to SHA-256 is strongly recommended.

**SHA-256 (256-bit)** — Part of the SHA-2 family, SHA-256 is the current industry standard for general-purpose cryptographic hashing. It produces a 64-character hex digest and has no known practical vulnerabilities. SHA-256 is used in TLS certificates, Bitcoin's proof-of-work algorithm, code-signing certificates, and countless security protocols. It strikes the best balance of security, performance, and ecosystem support, making it the default choice for new applications.

**SHA-512 (512-bit)** — Also part of SHA-2, SHA-512 produces a 128-character hex digest. It offers a larger security margin and can actually be faster than SHA-256 on 64-bit hardware due to its internal 64-bit word operations. SHA-512 is preferred in applications requiring long-term security or when hashing very large datasets, such as archival integrity verification or high-security password hashing schemes.

---

## Related Tools

> Encode and decode Base64 → [Base64 Encoder](/tools/base64-encoder/)

> Test regular expressions → [Regex Tester](/tools/regex-tester/)

> Generate secure passwords → [Password Generator](/tools/password-generator/)
