---
title: "Base64 Encoder & Decoder - Free Online Tool"
date: 2025-05-16
description: "Encode and decode Base64 strings instantly. Supports text, URLs, and file encoding. Free online Base64 conversion tool for developers."
categories: ["Free Tools"]
tags: ["base64", "encoder", "decoder", "developer tool", "encoding"]
slug: "base64-encoder"
aliases: ["/tools/base64-decoder/", "/tools/base64-converter/"]
cover:
  image: "/images/covers/base64-encoder.png"
  alt: "Base64 Encoder Decoder"
ShowToc: false
---

<div id="base64-app">

<style>
#base64-app {
  font-family: ui-sans-serif, system-ui, -apple-system, sans-serif;
  color: #e2e8f0;
  max-width: 860px;
  margin: 0 auto;
  padding: 0;
}

#base64-app * {
  box-sizing: border-box;
}

.b64-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 16px;
}

.b64-label {
  font-size: 13px;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.b64-count {
  font-size: 12px;
  font-weight: 400;
  color: #64748b;
  text-transform: none;
  letter-spacing: 0;
}

.b64-textarea {
  width: 100%;
  min-height: 140px;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #e2e8f0;
  font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
  font-size: 14px;
  line-height: 1.6;
  padding: 12px;
  resize: vertical;
  transition: border-color 0.2s;
  outline: none;
}

.b64-textarea:focus {
  border-color: #06b6d4;
}

.b64-textarea.b64-error-border {
  border-color: #f87171;
}

.b64-textarea::placeholder {
  color: #475569;
}

.b64-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin: 16px 0;
  align-items: center;
}

.b64-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 9px 20px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: background 0.15s, transform 0.1s, opacity 0.15s;
  white-space: nowrap;
  outline: none;
}

.b64-btn:active {
  transform: scale(0.97);
}

.b64-btn-primary {
  background: #06b6d4;
  color: #0f172a;
}

.b64-btn-primary:hover {
  background: #22d3ee;
}

.b64-btn-secondary {
  background: #475569;
  color: #e2e8f0;
}

.b64-btn-secondary:hover {
  background: #64748b;
}

.b64-btn-ghost {
  background: transparent;
  color: #94a3b8;
  border: 1px solid #334155;
}

.b64-btn-ghost:hover {
  background: #1e293b;
  color: #e2e8f0;
  border-color: #475569;
}

.b64-btn-success {
  background: #10b981 !important;
  color: #fff !important;
}

.b64-btn-danger {
  background: #ef4444;
  color: #fff;
}

.b64-btn-danger:hover {
  background: #f87171;
}

.b64-divider-row {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 4px 0;
}

.b64-swap-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 7px 16px;
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 20px;
  color: #94a3b8;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}

.b64-swap-btn:hover {
  background: #334155;
  color: #e2e8f0;
  border-color: #475569;
}

.b64-toggles {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  margin: 12px 0 0;
  padding-top: 12px;
  border-top: 1px solid #1e293b;
}

.b64-toggle-item {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  user-select: none;
}

.b64-toggle-item input[type="checkbox"] {
  appearance: none;
  -webkit-appearance: none;
  width: 36px;
  height: 20px;
  background: #334155;
  border-radius: 10px;
  position: relative;
  cursor: pointer;
  transition: background 0.2s;
  flex-shrink: 0;
}

.b64-toggle-item input[type="checkbox"]:checked {
  background: #06b6d4;
}

.b64-toggle-item input[type="checkbox"]::after {
  content: '';
  position: absolute;
  width: 14px;
  height: 14px;
  background: #fff;
  border-radius: 50%;
  top: 3px;
  left: 3px;
  transition: left 0.2s;
}

.b64-toggle-item input[type="checkbox"]:checked::after {
  left: 19px;
}

.b64-toggle-label {
  font-size: 13px;
  color: #94a3b8;
}

.b64-error {
  background: #450a0a;
  border: 1px solid #f87171;
  border-radius: 8px;
  color: #fca5a5;
  font-size: 13px;
  padding: 10px 14px;
  margin-top: 8px;
  display: none;
}

.b64-error.visible {
  display: block;
}

.b64-auto-badge {
  display: inline-block;
  background: #164e63;
  color: #67e8f9;
  font-size: 11px;
  font-weight: 700;
  padding: 2px 8px;
  border-radius: 10px;
  margin-left: 6px;
  vertical-align: middle;
  letter-spacing: 0.03em;
}

/* File drop zone */
.b64-drop-zone {
  border: 2px dashed #334155;
  border-radius: 10px;
  padding: 28px 20px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
  background: #0f172a;
}

.b64-drop-zone:hover,
.b64-drop-zone.b64-drag-over {
  border-color: #06b6d4;
  background: #0c1a2e;
}

.b64-drop-zone-icon {
  font-size: 32px;
  margin-bottom: 8px;
  line-height: 1;
}

.b64-drop-zone-text {
  font-size: 14px;
  color: #64748b;
  margin-bottom: 10px;
}

.b64-drop-zone-text strong {
  color: #94a3b8;
}

.b64-file-input {
  display: none;
}

.b64-file-info {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 13px;
  color: #94a3b8;
  margin-top: 12px;
  display: none;
}

.b64-file-info.visible {
  display: flex;
  align-items: center;
  gap: 8px;
  flex-wrap: wrap;
}

.b64-file-name {
  color: #e2e8f0;
  font-weight: 600;
  word-break: break-all;
}

.b64-file-size {
  color: #64748b;
  font-size: 12px;
}

.b64-section-title {
  font-size: 15px;
  font-weight: 700;
  color: #cbd5e1;
  margin-bottom: 14px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.b64-section-title::before {
  content: '';
  display: block;
  width: 3px;
  height: 16px;
  background: #06b6d4;
  border-radius: 2px;
}

@media (max-width: 600px) {
  .b64-card {
    padding: 16px;
  }
  .b64-btn {
    padding: 8px 14px;
    font-size: 13px;
  }
  .b64-textarea {
    min-height: 110px;
    font-size: 13px;
  }
  .b64-btn-row {
    gap: 8px;
  }
}
</style>

<!-- INPUT SECTION -->
<div class="b64-card">
  <div class="b64-section-title">Text Encoder / Decoder</div>

  <div class="b64-label">
    <span>Input <span id="b64-auto-indicator" class="b64-auto-badge" style="display:none;">AUTO-DETECT</span></span>
    <span class="b64-count" id="b64-input-count">0 chars</span>
  </div>
  <textarea
    class="b64-textarea"
    id="b64-input"
    placeholder="Type or paste text / Base64 string here..."
    spellcheck="false"
  ></textarea>

  <div class="b64-btn-row">
    <button class="b64-btn b64-btn-primary" id="b64-encode-btn" onclick="b64Encode()">Encode</button>
    <button class="b64-btn b64-btn-primary" id="b64-decode-btn" onclick="b64Decode()">Decode</button>
    <button class="b64-btn b64-btn-ghost" id="b64-clear-btn" onclick="b64Clear()">Clear</button>
  </div>

  <div class="b64-toggles">
    <label class="b64-toggle-item" title="Replace + with - and / with _ for URL-safe Base64">
      <input type="checkbox" id="b64-url-safe" onchange="b64OnOptionChange()">
      <span class="b64-toggle-label">URL-safe mode (<code>+/</code> → <code>-_</code>)</span>
    </label>
    <label class="b64-toggle-item" title="Automatically detect if input looks like Base64 and switch mode">
      <input type="checkbox" id="b64-auto-detect" onchange="b64OnAutoDetectChange()">
      <span class="b64-toggle-label">Auto-detect mode</span>
    </label>
    <label class="b64-toggle-item" title="Prepend data URI prefix to encoded output">
      <input type="checkbox" id="b64-data-uri" onchange="b64OnOptionChange()">
      <span class="b64-toggle-label">Output as data URI</span>
    </label>
  </div>
</div>

<!-- SWAP ROW -->
<div class="b64-divider-row">
  <button class="b64-swap-btn" onclick="b64Swap()" title="Swap input and output">
    &#8645; Swap Input / Output
  </button>
</div>

<!-- OUTPUT SECTION -->
<div class="b64-card">
  <div class="b64-label">
    <span>Output</span>
    <span class="b64-count" id="b64-output-count">0 chars</span>
  </div>
  <textarea
    class="b64-textarea"
    id="b64-output"
    placeholder="Result will appear here..."
    spellcheck="false"
    readonly
  ></textarea>

  <div class="b64-error" id="b64-error-msg"></div>

  <div class="b64-btn-row" style="margin-bottom:0;">
    <button class="b64-btn b64-btn-secondary" id="b64-copy-btn" onclick="b64Copy()">Copy Output</button>
  </div>
</div>

<!-- FILE TO BASE64 SECTION -->
<div class="b64-card">
  <div class="b64-section-title">File to Base64</div>

  <div
    class="b64-drop-zone"
    id="b64-drop-zone"
    onclick="document.getElementById('b64-file-input').click()"
    ondragover="b64DragOver(event)"
    ondragleave="b64DragLeave(event)"
    ondrop="b64Drop(event)"
  >
    <div class="b64-drop-zone-icon">&#128196;</div>
    <div class="b64-drop-zone-text">
      <strong>Drag &amp; drop a file here</strong>, or click to browse
    </div>
    <button class="b64-btn b64-btn-ghost" style="font-size:13px;padding:6px 14px;" onclick="event.stopPropagation(); document.getElementById('b64-file-input').click()">
      Choose File
    </button>
  </div>
  <input type="file" class="b64-file-input" id="b64-file-input" onchange="b64FileSelected(this)">

  <div class="b64-file-info" id="b64-file-info"></div>

  <div class="b64-btn-row" style="margin-top:12px; margin-bottom:0;">
    <label class="b64-toggle-item">
      <input type="checkbox" id="b64-file-data-uri" checked>
      <span class="b64-toggle-label">Include data URI prefix (e.g. <code>data:image/png;base64,...</code>)</span>
    </label>
  </div>
</div>

<script>
(function() {
  // ---- Utility ----
  function isBase64Like(str) {
    var s = str.trim();
    // URL-safe or standard base64
    return /^[A-Za-z0-9+/\-_]+=*$/.test(s) && s.length > 0 && s.length % 4 === 0;
  }

  function updateCount(id, text) {
    document.getElementById(id).textContent = text.length.toLocaleString() + ' chars';
  }

  function showError(msg) {
    var el = document.getElementById('b64-error-msg');
    el.textContent = msg;
    el.classList.add('visible');
    document.getElementById('b64-output').classList.add('b64-error-border');
  }

  function clearError() {
    var el = document.getElementById('b64-error-msg');
    el.textContent = '';
    el.classList.remove('visible');
    document.getElementById('b64-output').classList.remove('b64-error-border');
  }

  function setOutput(val) {
    document.getElementById('b64-output').value = val;
    updateCount('b64-output-count', val);
  }

  function getInput() {
    return document.getElementById('b64-input').value;
  }

  function isUrlSafe() {
    return document.getElementById('b64-url-safe').checked;
  }

  function isDataUri() {
    return document.getElementById('b64-data-uri').checked;
  }

  // ---- Encode ----
  window.b64Encode = function() {
    clearError();
    var input = getInput();
    if (!input) { setOutput(''); return; }
    try {
      var encoded = btoa(unescape(encodeURIComponent(input)));
      if (isUrlSafe()) {
        encoded = encoded.replace(/\+/g, '-').replace(/\//g, '_');
      }
      if (isDataUri()) {
        encoded = 'data:text/plain;base64,' + encoded;
      }
      setOutput(encoded);
    } catch(e) {
      showError('Encoding failed: ' + e.message);
      setOutput('');
    }
  };

  // ---- Decode ----
  window.b64Decode = function() {
    clearError();
    var input = getInput().trim();
    if (!input) { setOutput(''); return; }

    // Strip data URI prefix if present
    var raw = input.replace(/^data:[^;]+;base64,/, '');

    // Convert URL-safe chars back
    raw = raw.replace(/-/g, '+').replace(/_/g, '/');

    // Pad if needed
    while (raw.length % 4 !== 0) { raw += '='; }

    try {
      var decoded = decodeURIComponent(escape(atob(raw)));
      setOutput(decoded);
    } catch(e) {
      showError('Decode failed: Input does not appear to be valid Base64. ' + e.message);
      setOutput('');
    }
  };

  // ---- Clear ----
  window.b64Clear = function() {
    document.getElementById('b64-input').value = '';
    setOutput('');
    clearError();
    updateCount('b64-input-count', '');
    document.getElementById('b64-auto-indicator').style.display = 'none';
  };

  // ---- Swap ----
  window.b64Swap = function() {
    var inputEl = document.getElementById('b64-input');
    var outputEl = document.getElementById('b64-output');
    var tmp = inputEl.value;
    inputEl.value = outputEl.value;
    outputEl.value = tmp;
    clearError();
    updateCount('b64-input-count', inputEl.value);
    updateCount('b64-output-count', outputEl.value);
  };

  // ---- Copy ----
  window.b64Copy = function() {
    var val = document.getElementById('b64-output').value;
    if (!val) return;
    var btn = document.getElementById('b64-copy-btn');
    navigator.clipboard.writeText(val).then(function() {
      btn.textContent = 'Copied!';
      btn.classList.add('b64-btn-success');
      setTimeout(function() {
        btn.textContent = 'Copy Output';
        btn.classList.remove('b64-btn-success');
      }, 1800);
    }).catch(function() {
      // Fallback
      var ta = document.createElement('textarea');
      ta.value = val;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      btn.textContent = 'Copied!';
      btn.classList.add('b64-btn-success');
      setTimeout(function() {
        btn.textContent = 'Copy Output';
        btn.classList.remove('b64-btn-success');
      }, 1800);
    });
  };

  // ---- Option change (re-run last operation) ----
  window.b64OnOptionChange = function() {
    // Do nothing on toggle alone; user clicks Encode/Decode explicitly
  };

  // ---- Auto-detect ----
  window.b64OnAutoDetectChange = function() {
    var on = document.getElementById('b64-auto-detect').checked;
    var indicator = document.getElementById('b64-auto-indicator');
    indicator.style.display = on ? 'inline-block' : 'none';
    if (on) b64AutoRun();
  };

  function b64AutoRun() {
    var input = getInput().trim();
    if (!input) return;
    if (isBase64Like(input)) {
      b64Decode();
    } else {
      b64Encode();
    }
  }

  // ---- Input listener ----
  document.getElementById('b64-input').addEventListener('input', function() {
    updateCount('b64-input-count', this.value);
    clearError();
    if (document.getElementById('b64-auto-detect').checked) {
      b64AutoRun();
    }
  });

  // ---- File to Base64 ----
  window.b64DragOver = function(e) {
    e.preventDefault();
    document.getElementById('b64-drop-zone').classList.add('b64-drag-over');
  };

  window.b64DragLeave = function(e) {
    document.getElementById('b64-drop-zone').classList.remove('b64-drag-over');
  };

  window.b64Drop = function(e) {
    e.preventDefault();
    document.getElementById('b64-drop-zone').classList.remove('b64-drag-over');
    var files = e.dataTransfer.files;
    if (files && files.length > 0) {
      b64ProcessFile(files[0]);
    }
  };

  window.b64FileSelected = function(input) {
    if (input.files && input.files.length > 0) {
      b64ProcessFile(input.files[0]);
    }
  };

  function formatBytes(bytes) {
    if (bytes < 1024) return bytes + ' B';
    if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + ' KB';
    return (bytes / (1024 * 1024)).toFixed(2) + ' MB';
  }

  function b64ProcessFile(file) {
    var infoEl = document.getElementById('b64-file-info');
    var reader = new FileReader();
    reader.onload = function(e) {
      var result = e.target.result; // data URI: data:<mime>;base64,<data>
      var useDataUri = document.getElementById('b64-file-data-uri').checked;
      var outputEl = document.getElementById('b64-output');

      var outputVal;
      if (useDataUri) {
        outputVal = result;
      } else {
        // Strip the data URI prefix
        var commaIdx = result.indexOf(',');
        outputVal = commaIdx >= 0 ? result.substring(commaIdx + 1) : result;
      }

      outputEl.value = outputVal;
      outputEl.removeAttribute('readonly');
      updateCount('b64-output-count', outputVal);

      infoEl.innerHTML =
        '<span>&#128196;</span>' +
        '<span class="b64-file-name">' + file.name + '</span>' +
        '<span class="b64-file-size">(' + formatBytes(file.size) + ')</span>' +
        '<span style="color:#10b981;font-weight:600;">&#10003; Encoded</span>';
      infoEl.classList.add('visible');
    };
    reader.onerror = function() {
      infoEl.innerHTML = '<span style="color:#f87171;">Failed to read file.</span>';
      infoEl.classList.add('visible');
    };
    reader.readAsDataURL(file);
  }
})();
</script>

</div>

---

## What is Base64 Encoding?

Base64 is a binary-to-text encoding scheme that represents binary data using a set of 64 printable ASCII characters (A–Z, a–z, 0–9, `+`, and `/`), with `=` used for padding. The name comes from the 64 characters used in the alphabet. Each Base64 character encodes exactly 6 bits of binary data, meaning every 3 bytes of input become 4 Base64 characters — increasing the data size by approximately 33%. Base64 was standardized in RFC 4648 and is universally supported across programming languages, browsers, and operating systems.

Base64 is not a form of encryption — it is purely an encoding mechanism designed to safely transport binary data over channels that were designed to handle text. A URL-safe variant replaces `+` with `-` and `/` with `_`, making the encoded string safe to embed in URLs and file names without percent-encoding. Data URIs (`data:<mime>;base64,<data>`) are a common application, allowing images and other binary assets to be embedded directly inside HTML, CSS, or JSON without a separate HTTP request.

## Common Use Cases

- **Email attachments** — MIME email protocols use Base64 to encode binary files (images, PDFs) so they can travel through text-based email systems without corruption.
- **Embedding images in HTML/CSS** — Small icons and background images can be inlined as Base64 data URIs to eliminate extra HTTP requests and simplify asset bundling.
- **API and JSON payloads** — Binary data (audio, images, certificates) is Base64-encoded before being included in JSON fields or HTTP request/response bodies.
- **JWT tokens** — JSON Web Tokens use URL-safe Base64 to encode their header and payload sections for compact, URL-friendly transmission.
- **Configuration and secrets** — Kubernetes secrets, environment variables, and configuration files often store binary credentials or keys as Base64 strings for safe storage in text-based formats.

## Related Tools

> Format and validate JSON → [JSON Formatter](/tools/json-formatter/)

> Generate secure passwords → [Password Generator](/tools/password-generator/)

> Count words and characters → [Word Counter](/tools/word-counter/)
