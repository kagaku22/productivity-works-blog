---
title: ".htaccess Generator — Free Online Tool"
date: 2025-05-16
description: "Generate .htaccess files instantly. Visual editor for redirects, security headers, caching, CORS, gzip, and error pages. Presets for WordPress and static sites."
categories: ["Free Tools"]
slug: "htaccess-generator"
ShowToc: false
aliases:
  - "/tools/htaccess/"
  - "/tools/apache-config/"
cover:
  image: "/images/covers/htaccess-generator.png"
  alt: ".htaccess Generator"
---

Generate `.htaccess` files visually — no Apache expertise needed. Toggle sections, add redirect rules, configure security headers, and download a ready-to-use file in seconds.

<div id="htaccess-app">

<style>
#htaccess-app *,
#htaccess-app *::before,
#htaccess-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#htaccess-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  font-size: 15px;
  color: #1a1a2e;
  line-height: 1.6;
  max-width: 900px;
  margin: 0 auto;
}
#htaccess-app .ha-layout {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}
#htaccess-app .ha-left {
  flex: 1 1 480px;
  min-width: 0;
}
#htaccess-app .ha-right {
  flex: 1 1 320px;
  min-width: 0;
}
#htaccess-app .ha-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}
#htaccess-app .ha-preset-btn {
  padding: 6px 14px;
  background: #f0f4ff;
  border: 1px solid #c3d0f5;
  border-radius: 20px;
  cursor: pointer;
  font-size: 13px;
  color: #3a56d4;
  font-weight: 500;
  transition: background 0.15s, border-color 0.15s;
}
#htaccess-app .ha-preset-btn:hover {
  background: #dce6ff;
  border-color: #3a56d4;
}
#htaccess-app .ha-section {
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  margin-bottom: 14px;
  overflow: hidden;
}
#htaccess-app .ha-section-header {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px 16px;
  background: #f8fafc;
  cursor: pointer;
  user-select: none;
}
#htaccess-app .ha-section-header:hover {
  background: #f0f4ff;
}
#htaccess-app .ha-section-header input[type="checkbox"] {
  width: 17px;
  height: 17px;
  accent-color: #3a56d4;
  cursor: pointer;
  flex-shrink: 0;
}
#htaccess-app .ha-section-title {
  font-weight: 600;
  font-size: 14px;
  flex: 1;
}
#htaccess-app .ha-section-chevron {
  font-size: 11px;
  color: #94a3b8;
  transition: transform 0.2s;
}
#htaccess-app .ha-section-body {
  padding: 14px 16px;
  border-top: 1px solid #e2e8f0;
  background: #fff;
}
#htaccess-app .ha-section-body.ha-hidden {
  display: none;
}
#htaccess-app .ha-field-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
  flex-wrap: wrap;
}
#htaccess-app .ha-field-label {
  font-size: 13px;
  color: #475569;
  min-width: 90px;
  flex-shrink: 0;
}
#htaccess-app .ha-input,
#htaccess-app .ha-select {
  flex: 1;
  min-width: 120px;
  padding: 6px 10px;
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  color: #1a1a2e;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
}
#htaccess-app .ha-input:focus,
#htaccess-app .ha-select:focus {
  border-color: #3a56d4;
  box-shadow: 0 0 0 3px rgba(58,86,212,0.1);
}
#htaccess-app .ha-redirect-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-bottom: 10px;
}
#htaccess-app .ha-redirect-row {
  display: flex;
  gap: 8px;
  align-items: center;
  flex-wrap: wrap;
}
#htaccess-app .ha-redirect-row .ha-input {
  flex: 1;
  min-width: 100px;
}
#htaccess-app .ha-remove-btn {
  padding: 5px 10px;
  background: #fee2e2;
  border: 1px solid #fca5a5;
  border-radius: 6px;
  color: #dc2626;
  cursor: pointer;
  font-size: 12px;
  flex-shrink: 0;
  transition: background 0.15s;
}
#htaccess-app .ha-remove-btn:hover {
  background: #fecaca;
}
#htaccess-app .ha-add-btn {
  padding: 6px 14px;
  background: #f0fdf4;
  border: 1px solid #86efac;
  border-radius: 6px;
  color: #16a34a;
  cursor: pointer;
  font-size: 13px;
  font-weight: 500;
  transition: background 0.15s;
}
#htaccess-app .ha-add-btn:hover {
  background: #dcfce7;
}
#htaccess-app .ha-checkbox-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
  font-size: 13px;
  color: #334155;
}
#htaccess-app .ha-checkbox-row input[type="checkbox"] {
  width: 15px;
  height: 15px;
  accent-color: #3a56d4;
  cursor: pointer;
}
#htaccess-app .ha-hint {
  font-size: 12px;
  color: #94a3b8;
  margin-top: 4px;
}
#htaccess-app .ha-preview-box {
  background: #0f172a;
  border-radius: 10px;
  overflow: hidden;
  position: sticky;
  top: 80px;
}
#htaccess-app .ha-preview-topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 14px;
  background: #1e293b;
}
#htaccess-app .ha-preview-label {
  font-size: 12px;
  font-weight: 600;
  color: #94a3b8;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}
#htaccess-app .ha-preview-actions {
  display: flex;
  gap: 8px;
}
#htaccess-app .ha-copy-btn,
#htaccess-app .ha-download-btn {
  padding: 5px 12px;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: background 0.15s, transform 0.1s;
}
#htaccess-app .ha-copy-btn {
  background: #3a56d4;
  color: #fff;
}
#htaccess-app .ha-copy-btn:hover {
  background: #2d44b0;
}
#htaccess-app .ha-copy-btn.ha-copied {
  background: #16a34a;
}
#htaccess-app .ha-download-btn {
  background: #334155;
  color: #e2e8f0;
}
#htaccess-app .ha-download-btn:hover {
  background: #475569;
}
#htaccess-app .ha-preview-code {
  padding: 16px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 12px;
  line-height: 1.7;
  color: #e2e8f0;
  white-space: pre;
  overflow-x: auto;
  max-height: 520px;
  overflow-y: auto;
  min-height: 200px;
}
#htaccess-app .ha-preview-code .ht-comment { color: #64748b; }
#htaccess-app .ha-preview-code .ht-directive { color: #7dd3fc; }
#htaccess-app .ha-preview-code .ht-value { color: #86efac; }
#htaccess-app .ha-preview-code .ht-tag { color: #f9a8d4; }
#htaccess-app .ha-preview-code .ht-string { color: #fde68a; }
#htaccess-app .ha-preview-code .ht-section { color: #c084fc; }
#htaccess-app .ha-section-badge {
  font-size: 11px;
  background: #e0e7ff;
  color: #3730a3;
  border-radius: 10px;
  padding: 1px 8px;
  font-weight: 500;
}
#htaccess-app .ha-generate-btn {
  width: 100%;
  padding: 13px;
  background: linear-gradient(135deg, #3a56d4, #7c3aed);
  color: #fff;
  border: none;
  border-radius: 10px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  margin-bottom: 16px;
  transition: opacity 0.2s, transform 0.1s;
  letter-spacing: 0.02em;
}
#htaccess-app .ha-generate-btn:hover {
  opacity: 0.92;
  transform: translateY(-1px);
}
#htaccess-app .ha-section-count {
  font-size: 11px;
  color: #64748b;
  margin-top: 2px;
}
@media (max-width: 700px) {
  #htaccess-app .ha-layout {
    flex-direction: column;
  }
  #htaccess-app .ha-preview-box {
    position: static;
  }
}
</style>

<div class="ha-presets">
  <strong style="font-size:13px;color:#64748b;align-self:center;margin-right:4px;">Presets:</strong>
  <button class="ha-preset-btn" onclick="haApplyPreset('wordpress')">WordPress</button>
  <button class="ha-preset-btn" onclick="haApplyPreset('static')">Static Site</button>
  <button class="ha-preset-btn" onclick="haApplyPreset('https')">Force HTTPS</button>
  <button class="ha-preset-btn" onclick="haApplyPreset('bots')">Block Bad Bots</button>
  <button class="ha-preset-btn" onclick="haApplyPreset('cache')">Cache Static Assets</button>
  <button class="ha-preset-btn" onclick="haApplyPreset('reset')" style="color:#dc2626;background:#fff5f5;border-color:#fca5a5;">Reset All</button>
</div>

<div class="ha-layout">
  <div class="ha-left">

    <!-- Redirects -->
    <div class="ha-section" id="ha-sec-redirects">
      <div class="ha-section-header" onclick="haToggleSection('redirects')">
        <input type="checkbox" id="ha-chk-redirects" onclick="event.stopPropagation();haRender()" checked>
        <span class="ha-section-title">Redirects</span>
        <span class="ha-section-badge">301 / 302</span>
        <span class="ha-section-chevron" id="ha-chev-redirects">▼</span>
      </div>
      <div class="ha-section-body" id="ha-body-redirects">
        <div class="ha-field-row" style="margin-bottom:10px;">
          <span class="ha-field-label">Default type</span>
          <select class="ha-select" id="ha-redirect-type" onchange="haRender()" style="max-width:180px;">
            <option value="301">301 Permanent</option>
            <option value="302">302 Temporary</option>
          </select>
        </div>
        <div class="ha-redirect-list" id="ha-redirect-list"></div>
        <button class="ha-add-btn" onclick="haAddRedirect()">+ Add Redirect Rule</button>
        <div class="ha-hint">Source path (e.g. /old-page) → Destination URL</div>
      </div>
    </div>

    <!-- Security Headers -->
    <div class="ha-section" id="ha-sec-security">
      <div class="ha-section-header" onclick="haToggleSection('security')">
        <input type="checkbox" id="ha-chk-security" onclick="event.stopPropagation();haRender()" checked>
        <span class="ha-section-title">Security Headers</span>
        <span class="ha-section-chevron" id="ha-chev-security">▼</span>
      </div>
      <div class="ha-section-body" id="ha-body-security">
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-xframe" onchange="haRender()" checked>
          <span>X-Frame-Options: SAMEORIGIN</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-xcontent" onchange="haRender()" checked>
          <span>X-Content-Type-Options: nosniff</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-xss" onchange="haRender()" checked>
          <span>X-XSS-Protection: 1; mode=block</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-referrer" onchange="haRender()">
          <span>Referrer-Policy: strict-origin-when-cross-origin</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-hsts" onchange="haRender()">
          <span>Strict-Transport-Security (HSTS)</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-csp" onchange="haRender()">
          <span>Content-Security-Policy: default-src 'self'</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-sec-serverhide" onchange="haRender()" checked>
          <span>ServerTokens / hide server signature</span>
        </div>
      </div>
    </div>

    <!-- Caching -->
    <div class="ha-section" id="ha-sec-caching">
      <div class="ha-section-header" onclick="haToggleSection('caching')">
        <input type="checkbox" id="ha-chk-caching" onclick="event.stopPropagation();haRender()">
        <span class="ha-section-title">Browser Caching</span>
        <span class="ha-section-chevron" id="ha-chev-caching">▼</span>
      </div>
      <div class="ha-section-body ha-hidden" id="ha-body-caching">
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cache-images" onchange="haRender()" checked>
          <span>Images (jpg, png, gif, webp, svg) — 1 month</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cache-css" onchange="haRender()" checked>
          <span>CSS &amp; JavaScript — 1 week</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cache-fonts" onchange="haRender()" checked>
          <span>Fonts (woff, woff2, ttf) — 1 year</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cache-html" onchange="haRender()">
          <span>HTML — 1 hour</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cache-etag" onchange="haRender()">
          <span>Disable ETags (for CDN environments)</span>
        </div>
      </div>
    </div>

    <!-- CORS -->
    <div class="ha-section" id="ha-sec-cors">
      <div class="ha-section-header" onclick="haToggleSection('cors')">
        <input type="checkbox" id="ha-chk-cors" onclick="event.stopPropagation();haRender()">
        <span class="ha-section-title">CORS</span>
        <span class="ha-section-chevron" id="ha-chev-cors">▼</span>
      </div>
      <div class="ha-section-body ha-hidden" id="ha-body-cors">
        <div class="ha-field-row">
          <span class="ha-field-label">Allow Origin</span>
          <input type="text" class="ha-input" id="ha-cors-origin" value="*" onchange="haRender()" placeholder="* or https://example.com">
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cors-methods" onchange="haRender()" checked>
          <span>Allow Methods: GET, POST, OPTIONS</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cors-headers" onchange="haRender()" checked>
          <span>Allow Headers: Content-Type, Authorization</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-cors-fonts-only" onchange="haRender()">
          <span>CORS for fonts only (recommended)</span>
        </div>
      </div>
    </div>

    <!-- Gzip -->
    <div class="ha-section" id="ha-sec-gzip">
      <div class="ha-section-header" onclick="haToggleSection('gzip')">
        <input type="checkbox" id="ha-chk-gzip" onclick="event.stopPropagation();haRender()">
        <span class="ha-section-title">Gzip Compression</span>
        <span class="ha-section-chevron" id="ha-chev-gzip">▼</span>
      </div>
      <div class="ha-section-body ha-hidden" id="ha-body-gzip">
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-gzip-html" onchange="haRender()" checked>
          <span>HTML, XML, Plain text</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-gzip-css" onchange="haRender()" checked>
          <span>CSS &amp; JavaScript</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-gzip-fonts" onchange="haRender()" checked>
          <span>Fonts (SVG, TTF)</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-gzip-json" onchange="haRender()" checked>
          <span>JSON &amp; APIs</span>
        </div>
      </div>
    </div>

    <!-- Error Pages -->
    <div class="ha-section" id="ha-sec-errors">
      <div class="ha-section-header" onclick="haToggleSection('errors')">
        <input type="checkbox" id="ha-chk-errors" onclick="event.stopPropagation();haRender()">
        <span class="ha-section-title">Custom Error Pages</span>
        <span class="ha-section-chevron" id="ha-chev-errors">▼</span>
      </div>
      <div class="ha-section-body ha-hidden" id="ha-body-errors">
        <div class="ha-field-row">
          <span class="ha-field-label">404 Not Found</span>
          <input type="text" class="ha-input" id="ha-err-404" value="/404.html" onchange="haRender()" placeholder="/404.html">
        </div>
        <div class="ha-field-row">
          <span class="ha-field-label">403 Forbidden</span>
          <input type="text" class="ha-input" id="ha-err-403" value="/403.html" onchange="haRender()" placeholder="/403.html">
        </div>
        <div class="ha-field-row">
          <span class="ha-field-label">500 Server Error</span>
          <input type="text" class="ha-input" id="ha-err-500" value="/500.html" onchange="haRender()" placeholder="/500.html">
        </div>
        <div class="ha-field-row">
          <span class="ha-field-label">401 Unauthorized</span>
          <input type="text" class="ha-input" id="ha-err-401" value="" onchange="haRender()" placeholder="/401.html (optional)">
        </div>
      </div>
    </div>

    <!-- Directory Options -->
    <div class="ha-section" id="ha-sec-directory">
      <div class="ha-section-header" onclick="haToggleSection('directory')">
        <input type="checkbox" id="ha-chk-directory" onclick="event.stopPropagation();haRender()">
        <span class="ha-section-title">Directory Options</span>
        <span class="ha-section-chevron" id="ha-chev-directory">▼</span>
      </div>
      <div class="ha-section-body ha-hidden" id="ha-body-directory">
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-dir-noindex" onchange="haRender()" checked>
          <span>Disable directory listing (Options -Indexes)</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-dir-followlinks" onchange="haRender()">
          <span>Follow symbolic links (Options +FollowSymLinks)</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-dir-blockdotfiles" onchange="haRender()" checked>
          <span>Block access to dotfiles (.env, .git, etc.)</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-dir-blockphp" onchange="haRender()">
          <span>Block PHP execution in uploads directory</span>
        </div>
        <div class="ha-checkbox-row">
          <input type="checkbox" id="ha-dir-badbots" onchange="haRender()">
          <span>Block common bad bots</span>
        </div>
        <div class="ha-field-row" style="margin-top:8px;">
          <span class="ha-field-label">Default charset</span>
          <select class="ha-select" id="ha-dir-charset" onchange="haRender()" style="max-width:180px;">
            <option value="UTF-8" selected>UTF-8</option>
            <option value="ISO-8859-1">ISO-8859-1</option>
            <option value="">(none)</option>
          </select>
        </div>
      </div>
    </div>

  </div><!-- /.ha-left -->

  <div class="ha-right">
    <div class="ha-preview-box">
      <div class="ha-preview-topbar">
        <span class="ha-preview-label">Preview — .htaccess</span>
        <div class="ha-preview-actions">
          <button class="ha-copy-btn" id="ha-copy-btn" onclick="haCopy()">Copy</button>
          <button class="ha-download-btn" onclick="haDownload()">Download</button>
        </div>
      </div>
      <pre class="ha-preview-code" id="ha-preview-code"></pre>
    </div>
  </div>
</div><!-- /.ha-layout -->

<script>
(function() {
  var haRedirects = [{ src: '/old-page', dst: 'https://example.com/new-page' }];
  var haOpenSections = { redirects: true, security: true, caching: false, cors: false, gzip: false, errors: false, directory: false };

  function haToggleSection(id) {
    haOpenSections[id] = !haOpenSections[id];
    var body = document.getElementById('ha-body-' + id);
    var chev = document.getElementById('ha-chev-' + id);
    if (body) body.classList.toggle('ha-hidden', !haOpenSections[id]);
    if (chev) chev.textContent = haOpenSections[id] ? '▼' : '▶';
  }
  window.haToggleSection = haToggleSection;

  function haAddRedirect() {
    haRedirects.push({ src: '', dst: '' });
    haRenderRedirectList();
    haRender();
  }
  window.haAddRedirect = haAddRedirect;

  function haRemoveRedirect(i) {
    haRedirects.splice(i, 1);
    haRenderRedirectList();
    haRender();
  }
  window.haRemoveRedirect = haRemoveRedirect;

  function haRenderRedirectList() {
    var list = document.getElementById('ha-redirect-list');
    if (!list) return;
    list.innerHTML = '';
    haRedirects.forEach(function(r, i) {
      var row = document.createElement('div');
      row.className = 'ha-redirect-row';
      row.innerHTML =
        '<input type="text" class="ha-input" placeholder="/old-path" value="' + escAttr(r.src) + '" oninput="haSetRedirect(' + i + ',\'src\',this.value)">' +
        '<span style="color:#94a3b8;font-size:13px;">→</span>' +
        '<input type="text" class="ha-input" placeholder="https://example.com/new" value="' + escAttr(r.dst) + '" oninput="haSetRedirect(' + i + ',\'dst\',this.value)">' +
        '<button class="ha-remove-btn" onclick="haRemoveRedirect(' + i + ')">✕</button>';
      list.appendChild(row);
    });
  }

  function haSetRedirect(i, key, val) {
    haRedirects[i][key] = val;
    haRender();
  }
  window.haSetRedirect = haSetRedirect;

  function escAttr(s) { return (s || '').replace(/"/g, '&quot;'); }

  function v(id) { var el = document.getElementById(id); return el ? el.value : ''; }
  function c(id) { var el = document.getElementById(id); return el ? el.checked : false; }

  function haRender() {
    var lines = [];
    lines.push('# Generated by .htaccess Generator');
    lines.push('# https://productivity.works/tools/htaccess-generator/');
    lines.push('');
    lines.push('Options -MultiViews');

    // Redirects
    if (c('ha-chk-redirects')) {
      var type = v('ha-redirect-type') || '301';
      var hasRules = haRedirects.some(function(r) { return r.src && r.dst; });
      if (hasRules) {
        lines.push('');
        lines.push('# ─── Redirects ──────────────────────────────────────────');
        lines.push('RewriteEngine On');
        haRedirects.forEach(function(r) {
          if (r.src && r.dst) {
            if (type === '301') {
              lines.push('Redirect 301 ' + r.src + ' ' + r.dst);
            } else {
              lines.push('Redirect 302 ' + r.src + ' ' + r.dst);
            }
          }
        });
      }
    }

    // Security Headers
    if (c('ha-chk-security')) {
      lines.push('');
      lines.push('# ─── Security Headers ───────────────────────────────────');
      lines.push('<IfModule mod_headers.c>');
      if (c('ha-sec-xframe'))      lines.push('  Header always set X-Frame-Options "SAMEORIGIN"');
      if (c('ha-sec-xcontent'))    lines.push('  Header always set X-Content-Type-Options "nosniff"');
      if (c('ha-sec-xss'))         lines.push('  Header always set X-XSS-Protection "1; mode=block"');
      if (c('ha-sec-referrer'))    lines.push('  Header always set Referrer-Policy "strict-origin-when-cross-origin"');
      if (c('ha-sec-hsts'))        lines.push('  Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"');
      if (c('ha-sec-csp'))         lines.push('  Header always set Content-Security-Policy "default-src \'self\'"');
      if (c('ha-sec-serverhide')) {
        lines.push('  Header unset Server');
        lines.push('  Header unset X-Powered-By');
        lines.push('  ServerTokens Prod');
        lines.push('  ServerSignature Off');
      }
      lines.push('</IfModule>');
    }

    // Caching
    if (c('ha-chk-caching')) {
      lines.push('');
      lines.push('# ─── Browser Caching ────────────────────────────────────');
      lines.push('<IfModule mod_expires.c>');
      lines.push('  ExpiresActive On');
      if (c('ha-cache-images')) lines.push('  ExpiresByType image/jpeg "access plus 1 month"');
      if (c('ha-cache-images')) lines.push('  ExpiresByType image/png "access plus 1 month"');
      if (c('ha-cache-images')) lines.push('  ExpiresByType image/gif "access plus 1 month"');
      if (c('ha-cache-images')) lines.push('  ExpiresByType image/webp "access plus 1 month"');
      if (c('ha-cache-images')) lines.push('  ExpiresByType image/svg+xml "access plus 1 month"');
      if (c('ha-cache-css'))    lines.push('  ExpiresByType text/css "access plus 1 week"');
      if (c('ha-cache-css'))    lines.push('  ExpiresByType application/javascript "access plus 1 week"');
      if (c('ha-cache-fonts'))  lines.push('  ExpiresByType font/woff2 "access plus 1 year"');
      if (c('ha-cache-fonts'))  lines.push('  ExpiresByType font/woff "access plus 1 year"');
      if (c('ha-cache-fonts'))  lines.push('  ExpiresByType font/ttf "access plus 1 year"');
      if (c('ha-cache-html'))   lines.push('  ExpiresByType text/html "access plus 1 hour"');
      lines.push('</IfModule>');
      if (c('ha-cache-etag')) {
        lines.push('FileETag None');
        lines.push('Header unset ETag');
      }
    }

    // CORS
    if (c('ha-chk-cors')) {
      var origin = v('ha-cors-origin') || '*';
      lines.push('');
      lines.push('# ─── CORS ───────────────────────────────────────────────');
      lines.push('<IfModule mod_headers.c>');
      if (c('ha-cors-fonts-only')) {
        lines.push('  <FilesMatch "\\.(ttf|ttc|otf|eot|woff|woff2|font.css)$">');
        lines.push('    Header add Access-Control-Allow-Origin "' + origin + '"');
        lines.push('  </FilesMatch>');
      } else {
        lines.push('  Header add Access-Control-Allow-Origin "' + origin + '"');
        if (c('ha-cors-methods')) lines.push('  Header add Access-Control-Allow-Methods "GET, POST, OPTIONS"');
        if (c('ha-cors-headers')) lines.push('  Header add Access-Control-Allow-Headers "Content-Type, Authorization"');
      }
      lines.push('</IfModule>');
    }

    // Gzip
    if (c('ha-chk-gzip')) {
      lines.push('');
      lines.push('# ─── Gzip Compression ───────────────────────────────────');
      lines.push('<IfModule mod_deflate.c>');
      if (c('ha-gzip-html')) {
        lines.push('  AddOutputFilterByType DEFLATE text/html');
        lines.push('  AddOutputFilterByType DEFLATE text/plain');
        lines.push('  AddOutputFilterByType DEFLATE text/xml');
        lines.push('  AddOutputFilterByType DEFLATE application/xml');
        lines.push('  AddOutputFilterByType DEFLATE application/xhtml+xml');
      }
      if (c('ha-gzip-css')) {
        lines.push('  AddOutputFilterByType DEFLATE text/css');
        lines.push('  AddOutputFilterByType DEFLATE text/javascript');
        lines.push('  AddOutputFilterByType DEFLATE application/javascript');
        lines.push('  AddOutputFilterByType DEFLATE application/x-javascript');
      }
      if (c('ha-gzip-fonts')) {
        lines.push('  AddOutputFilterByType DEFLATE image/svg+xml');
        lines.push('  AddOutputFilterByType DEFLATE font/ttf');
        lines.push('  AddOutputFilterByType DEFLATE font/otf');
      }
      if (c('ha-gzip-json')) {
        lines.push('  AddOutputFilterByType DEFLATE application/json');
        lines.push('  AddOutputFilterByType DEFLATE application/ld+json');
      }
      lines.push('</IfModule>');
    }

    // Error Pages
    if (c('ha-chk-errors')) {
      lines.push('');
      lines.push('# ─── Custom Error Pages ─────────────────────────────────');
      var e404 = v('ha-err-404'); if (e404) lines.push('ErrorDocument 404 ' + e404);
      var e403 = v('ha-err-403'); if (e403) lines.push('ErrorDocument 403 ' + e403);
      var e500 = v('ha-err-500'); if (e500) lines.push('ErrorDocument 500 ' + e500);
      var e401 = v('ha-err-401'); if (e401) lines.push('ErrorDocument 401 ' + e401);
    }

    // Directory Options
    if (c('ha-chk-directory')) {
      lines.push('');
      lines.push('# ─── Directory Options ──────────────────────────────────');
      if (c('ha-dir-noindex'))     lines.push('Options -Indexes');
      if (c('ha-dir-followlinks')) lines.push('Options +FollowSymLinks');
      var charset = v('ha-dir-charset');
      if (charset) lines.push('AddDefaultCharset ' + charset);
      if (c('ha-dir-blockdotfiles')) {
        lines.push('<FilesMatch "^\\.(env|git|htaccess|htpasswd|DS_Store)">');
        lines.push('  Order allow,deny');
        lines.push('  Deny from all');
        lines.push('</FilesMatch>');
      }
      if (c('ha-dir-blockphp')) {
        lines.push('<Directory "/wp-content/uploads">');
        lines.push('  <FilesMatch "\\.php$">');
        lines.push('    Order allow,deny');
        lines.push('    Deny from all');
        lines.push('  </FilesMatch>');
        lines.push('</Directory>');
      }
      if (c('ha-dir-badbots')) {
        lines.push('<IfModule mod_rewrite.c>');
        lines.push('  RewriteEngine On');
        lines.push('  RewriteCond %{HTTP_USER_AGENT} (SemrushBot|AhrefsBot|MJ12bot|DotBot|PetalBot) [NC]');
        lines.push('  RewriteRule .* - [F,L]');
        lines.push('</IfModule>');
      }
    }

    // Syntax highlight
    var code = document.getElementById('ha-preview-code');
    if (code) {
      var raw = lines.join('\n');
      code.innerHTML = raw.split('\n').map(function(line) {
        if (line.startsWith('#')) return '<span class="ht-comment">' + hEsc(line) + '</span>';
        if (line.startsWith('<') || line.startsWith('</')) return '<span class="ht-tag">' + hEsc(line) + '</span>';
        var m = line.match(/^(\s*\S+)(.*)/);
        if (!m) return hEsc(line);
        return '<span class="ht-directive">' + hEsc(m[1]) + '</span><span class="ht-value">' + hEsc(m[2]) + '</span>';
      }).join('\n');
      code.setAttribute('data-raw', raw);
    }
  }
  window.haRender = haRender;

  function hEsc(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function haCopy() {
    var code = document.getElementById('ha-preview-code');
    var raw = code ? code.getAttribute('data-raw') : '';
    if (!raw) return;
    var btn = document.getElementById('ha-copy-btn');
    if (navigator.clipboard) {
      navigator.clipboard.writeText(raw).then(function() {
        btn.textContent = 'Copied!';
        btn.classList.add('ha-copied');
        setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('ha-copied'); }, 2000);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = raw;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      btn.textContent = 'Copied!';
      btn.classList.add('ha-copied');
      setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('ha-copied'); }, 2000);
    }
  }
  window.haCopy = haCopy;

  function haDownload() {
    var code = document.getElementById('ha-preview-code');
    var raw = code ? code.getAttribute('data-raw') : '';
    if (!raw) return;
    var blob = new Blob([raw], { type: 'text/plain' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url;
    a.download = '.htaccess';
    a.click();
    URL.revokeObjectURL(url);
  }
  window.haDownload = haDownload;

  function haApplyPreset(name) {
    var ids = ['ha-chk-redirects','ha-chk-security','ha-chk-caching','ha-chk-cors','ha-chk-gzip','ha-chk-errors','ha-chk-directory',
               'ha-sec-xframe','ha-sec-xcontent','ha-sec-xss','ha-sec-referrer','ha-sec-hsts','ha-sec-csp','ha-sec-serverhide',
               'ha-cache-images','ha-cache-css','ha-cache-fonts','ha-cache-html','ha-cache-etag',
               'ha-cors-methods','ha-cors-headers','ha-cors-fonts-only',
               'ha-gzip-html','ha-gzip-css','ha-gzip-fonts','ha-gzip-json',
               'ha-dir-noindex','ha-dir-followlinks','ha-dir-blockdotfiles','ha-dir-blockphp','ha-dir-badbots'];
    function setChk(id, val) { var el = document.getElementById(id); if (el) el.checked = val; }
    function setVal(id, val) { var el = document.getElementById(id); if (el) el.value = val; }
    ids.forEach(function(id) { setChk(id, false); });
    haRedirects = [];
    if (name === 'reset') { haRedirects = [{ src: '', dst: '' }]; haRenderRedirectList(); haRender(); return; }
    if (name === 'wordpress') {
      setChk('ha-chk-security', true); setChk('ha-chk-gzip', true); setChk('ha-chk-caching', true); setChk('ha-chk-directory', true);
      setChk('ha-sec-xframe', true); setChk('ha-sec-xcontent', true); setChk('ha-sec-xss', true); setChk('ha-sec-serverhide', true);
      setChk('ha-gzip-html', true); setChk('ha-gzip-css', true); setChk('ha-gzip-fonts', true); setChk('ha-gzip-json', true);
      setChk('ha-cache-images', true); setChk('ha-cache-css', true); setChk('ha-cache-fonts', true);
      setChk('ha-dir-noindex', true); setChk('ha-dir-blockdotfiles', true); setChk('ha-dir-blockphp', true);
    } else if (name === 'static') {
      setChk('ha-chk-security', true); setChk('ha-chk-gzip', true); setChk('ha-chk-caching', true); setChk('ha-chk-errors', true);
      setChk('ha-sec-xframe', true); setChk('ha-sec-xcontent', true); setChk('ha-sec-xss', true); setChk('ha-sec-referrer', true); setChk('ha-sec-serverhide', true);
      setChk('ha-gzip-html', true); setChk('ha-gzip-css', true); setChk('ha-gzip-fonts', true);
      setChk('ha-cache-images', true); setChk('ha-cache-css', true); setChk('ha-cache-fonts', true);
      setVal('ha-err-404', '/404.html'); setVal('ha-err-500', '/500.html');
    } else if (name === 'https') {
      setChk('ha-chk-redirects', true); setChk('ha-chk-security', true);
      setChk('ha-sec-hsts', true); setChk('ha-sec-xframe', true); setChk('ha-sec-xcontent', true);
      haRedirects = [{ src: 'http://example.com', dst: 'https://example.com' }];
    } else if (name === 'bots') {
      setChk('ha-chk-directory', true); setChk('ha-dir-badbots', true); setChk('ha-dir-noindex', true); setChk('ha-dir-blockdotfiles', true);
    } else if (name === 'cache') {
      setChk('ha-chk-caching', true); setChk('ha-chk-gzip', true);
      setChk('ha-cache-images', true); setChk('ha-cache-css', true); setChk('ha-cache-fonts', true);
      setChk('ha-gzip-html', true); setChk('ha-gzip-css', true); setChk('ha-gzip-fonts', true); setChk('ha-gzip-json', true);
    }
    // Open relevant sections
    var secMap = { wordpress: ['security','caching','gzip','directory'], static: ['security','caching','gzip','errors'],
                   https: ['redirects','security'], bots: ['directory'], cache: ['caching','gzip'] };
    Object.keys(haOpenSections).forEach(function(k) { haOpenSections[k] = false; });
    (secMap[name] || []).forEach(function(k) { haOpenSections[k] = true; });
    Object.keys(haOpenSections).forEach(function(k) {
      var body = document.getElementById('ha-body-' + k);
      var chev = document.getElementById('ha-chev-' + k);
      if (body) body.classList.toggle('ha-hidden', !haOpenSections[k]);
      if (chev) chev.textContent = haOpenSections[k] ? '▼' : '▶';
    });
    haRenderRedirectList();
    haRender();
  }
  window.haApplyPreset = haApplyPreset;

  // Init
  document.addEventListener('DOMContentLoaded', function() {
    haRenderRedirectList();
    haRender();
  });
  if (document.readyState !== 'loading') {
    haRenderRedirectList();
    haRender();
  }
})();
</script>

</div>

---

### Related Tools

> Build robots.txt → [Robots.txt Generator](/tools/robots-txt-generator/)

> Generate meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)

> Format SQL → [SQL Formatter](/tools/sql-formatter/)
