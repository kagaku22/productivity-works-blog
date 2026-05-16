---
title: "Favicon Checker"
slug: "favicon-checker"
date: 2025-05-16
description: "Free favicon checker and preview tool. Upload your favicon and see how it looks in browser tabs, bookmarks, mobile home screens, and Google search results."
categories: ["Free Tools"]
tags: ["favicon", "web design", "seo", "preview"]
cover:
  image: /images/covers/favicon-checker.png
  alt: "Favicon Checker and Preview Tool"
ShowToc: false
---

Check how your favicon looks across browsers, bookmarks, search results, and mobile home screens — all client-side, nothing uploaded to any server.

**Related tools:** Generate favicons → [Favicon Generator](/tools/favicon-generator/) &nbsp;|&nbsp; Meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)

---

<div id="fc-app">

<style>
#fc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1e293b;
}
#fc-app *, #fc-app *::before, #fc-app *::after {
  box-sizing: border-box;
}
#fc-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 1.4rem 0 0.6rem;
  color: #0f172a;
}
#fc-drop-zone {
  border: 2.5px dashed #94a3b8;
  border-radius: 12px;
  padding: 36px 24px;
  text-align: center;
  cursor: pointer;
  transition: border-color 0.2s, background 0.2s;
  background: #f8fafc;
  position: relative;
}
#fc-drop-zone.fc-drag-over {
  border-color: #3b82f6;
  background: #eff6ff;
}
#fc-drop-zone p {
  margin: 0 0 10px;
  color: #64748b;
  font-size: 0.95rem;
}
#fc-drop-zone input[type="file"] {
  display: none;
}
#fc-upload-btn {
  display: inline-block;
  padding: 9px 22px;
  background: #3b82f6;
  color: #fff;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: background 0.18s;
}
#fc-upload-btn:hover { background: #2563eb; }
#fc-file-info {
  display: none;
  margin-top: 14px;
  padding: 12px 16px;
  background: #f1f5f9;
  border-radius: 8px;
  font-size: 0.88rem;
  color: #475569;
  text-align: left;
}
#fc-file-info span { display: inline-block; margin-right: 18px; }
#fc-file-info strong { color: #1e293b; }
#fc-warnings {
  margin-top: 10px;
  display: none;
}
.fc-warn {
  display: flex;
  align-items: flex-start;
  gap: 8px;
  padding: 8px 12px;
  background: #fef3c7;
  border-left: 3px solid #f59e0b;
  border-radius: 6px;
  margin-bottom: 6px;
  font-size: 0.85rem;
  color: #92400e;
}
.fc-warn-icon { flex-shrink: 0; font-size: 1rem; }
#fc-size-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
  gap: 12px;
  margin-top: 8px;
}
.fc-size-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 12px;
  text-align: center;
}
.fc-size-card canvas {
  display: block;
  margin: 0 auto 6px;
  image-rendering: pixelated;
  border: 1px solid #e2e8f0;
  border-radius: 4px;
}
.fc-size-label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #475569;
}
.fc-size-usage {
  font-size: 0.72rem;
  color: #94a3b8;
  margin-top: 2px;
}
.fc-size-ok { color: #16a34a; font-size: 0.75rem; margin-top: 3px; font-weight: 600; }
.fc-size-warn { color: #dc2626; font-size: 0.75rem; margin-top: 3px; font-weight: 600; }

/* Preview section */
#fc-previews { margin-top: 4px; }
#fc-dark-toggle {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-size: 0.85rem;
  color: #475569;
  user-select: none;
  margin-bottom: 14px;
}
#fc-dark-toggle input { cursor: pointer; }

.fc-preview-block {
  margin-bottom: 20px;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  overflow: hidden;
}
.fc-preview-label {
  padding: 8px 14px;
  font-size: 0.82rem;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  border-bottom: 1px solid #e2e8f0;
  background: #f8fafc;
}
.fc-preview-inner {
  padding: 20px 20px;
}
.fc-preview-inner.fc-dark {
  background: #1e293b;
}
.fc-preview-inner.fc-light {
  background: #ffffff;
}

/* Chrome tab mockup */
.fc-chrome-tab {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 6px 14px 6px 10px;
  background: #fff;
  border-radius: 8px 8px 0 0;
  border: 1px solid #d1d5db;
  border-bottom: none;
  font-size: 0.82rem;
  color: #374151;
  min-width: 140px;
  max-width: 200px;
  box-shadow: 0 -1px 3px rgba(0,0,0,0.06);
}
.fc-chrome-tab.fc-dark-tab {
  background: #374151;
  color: #f9fafb;
  border-color: #4b5563;
}
.fc-chrome-tab img, .fc-chrome-tab canvas {
  width: 16px; height: 16px;
  flex-shrink: 0;
  border-radius: 2px;
}
.fc-tab-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  flex: 1;
}
.fc-tab-close {
  font-size: 0.75rem;
  color: #9ca3af;
  flex-shrink: 0;
}
.fc-tab-bar {
  background: #e5e7eb;
  padding: 6px 8px 0;
  border-radius: 4px;
  display: inline-flex;
}
.fc-tab-bar.fc-dark { background: #1f2937; }

/* Safari tab */
.fc-safari-bar {
  background: #f2f2f7;
  padding: 10px 12px;
  border-radius: 4px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.fc-safari-bar.fc-dark { background: #2c2c2e; }
.fc-safari-urlbar {
  flex: 1;
  background: #fff;
  border-radius: 8px;
  padding: 5px 10px;
  font-size: 0.8rem;
  color: #6b7280;
  display: flex;
  align-items: center;
  gap: 6px;
}
.fc-safari-urlbar.fc-dark { background: #3a3a3c; color: #aeaeb2; }
.fc-safari-urlbar img, .fc-safari-urlbar canvas {
  width: 14px; height: 14px;
  border-radius: 2px;
  flex-shrink: 0;
}

/* Firefox tab */
.fc-firefox-bar {
  background: #f0f0f4;
  padding: 8px 10px 0;
  border-radius: 4px;
  display: inline-flex;
}
.fc-firefox-bar.fc-dark { background: #2b2a33; }
.fc-firefox-tab {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 7px 12px;
  background: #fff;
  border-radius: 6px 6px 0 0;
  font-size: 0.82rem;
  color: #374151;
  min-width: 140px;
  box-shadow: 0 -1px 4px rgba(0,0,0,0.08);
}
.fc-firefox-tab.fc-dark { background: #42414d; color: #fbfbfe; }
.fc-firefox-tab img, .fc-firefox-tab canvas {
  width: 16px; height: 16px;
  flex-shrink: 0;
  border-radius: 2px;
}

/* Bookmarks bar */
.fc-bookmarks-bar {
  display: flex;
  align-items: center;
  gap: 2px;
  padding: 4px 10px;
  background: #f3f4f6;
  border-radius: 4px;
  border: 1px solid #e5e7eb;
  flex-wrap: wrap;
}
.fc-bookmarks-bar.fc-dark {
  background: #374151;
  border-color: #4b5563;
}
.fc-bookmark-item {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 3px 8px;
  border-radius: 4px;
  font-size: 0.8rem;
  color: #374151;
  cursor: default;
}
.fc-bookmark-item:hover { background: rgba(0,0,0,0.06); }
.fc-bookmark-item.fc-dark { color: #d1d5db; }
.fc-bookmark-item img, .fc-bookmark-item canvas {
  width: 16px; height: 16px;
  border-radius: 2px;
  flex-shrink: 0;
}

/* Google search result */
.fc-google-result {
  padding: 4px 0;
  max-width: 480px;
}
.fc-google-site-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 4px;
}
.fc-google-site-row img, .fc-google-site-row canvas {
  width: 18px; height: 18px;
  border-radius: 50%;
  flex-shrink: 0;
}
.fc-google-site-name {
  font-size: 0.82rem;
  color: #202124;
  font-weight: 600;
}
.fc-google-site-name.fc-dark { color: #bdc1c6; }
.fc-google-site-url {
  font-size: 0.78rem;
  color: #5f6368;
}
.fc-google-title {
  font-size: 1.1rem;
  color: #1a0dab;
  font-weight: 400;
  line-height: 1.3;
  cursor: pointer;
}
.fc-google-title.fc-dark { color: #8ab4f8; }
.fc-google-desc {
  font-size: 0.83rem;
  color: #4d5156;
  margin-top: 2px;
}
.fc-google-desc.fc-dark { color: #9aa0a6; }

/* Mobile home screen */
.fc-mobile-screen {
  display: inline-flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px 16px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 20px;
  min-width: 200px;
}
.fc-mobile-screen.fc-dark {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
}
.fc-mobile-row {
  display: flex;
  gap: 16px;
  justify-content: center;
}
.fc-app-icon-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
}
.fc-app-icon {
  width: 60px;
  height: 60px;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.3);
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}
.fc-app-icon canvas {
  width: 60px;
  height: 60px;
  border-radius: 14px;
  display: block;
}
.fc-app-icon-name {
  font-size: 0.7rem;
  color: #fff;
  text-align: center;
  max-width: 60px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  text-shadow: 0 1px 3px rgba(0,0,0,0.5);
}

/* Windows taskbar */
.fc-taskbar {
  display: flex;
  align-items: center;
  gap: 2px;
  padding: 6px 8px;
  background: #1a1a2a;
  border-radius: 6px;
}
.fc-taskbar-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 5px 10px;
  border-radius: 4px;
  background: rgba(255,255,255,0.08);
  border-bottom: 2px solid #3b82f6;
  font-size: 0.8rem;
  color: #f1f5f9;
}
.fc-taskbar-item canvas {
  width: 20px; height: 20px;
  flex-shrink: 0;
}

#fc-placeholder-msg {
  margin-top: 28px;
  padding: 24px;
  background: #f8fafc;
  border: 1.5px dashed #cbd5e1;
  border-radius: 10px;
  text-align: center;
  color: #94a3b8;
  font-size: 0.9rem;
}

#fc-sections { display: none; }
</style>

<div id="fc-drop-zone">
  <p>Drag &amp; drop your favicon here</p>
  <p style="font-size:0.8rem;color:#94a3b8;margin-bottom:14px;">Supports PNG, ICO, SVG, JPG, WebP</p>
  <label id="fc-upload-btn" for="fc-file-input">Choose File</label>
  <input type="file" id="fc-file-input" accept=".png,.ico,.svg,.jpg,.jpeg,.webp,image/x-icon,image/vnd.microsoft.icon,image/svg+xml,image/png,image/jpeg,image/webp">
</div>

<div id="fc-file-info"></div>
<div id="fc-warnings"></div>

<div id="fc-placeholder-msg">Upload a favicon above to see previews and size checks.</div>

<div id="fc-sections">
  <h2>Size Preview</h2>
  <div id="fc-size-grid"></div>

  <h2>Browser &amp; Context Previews</h2>
  <label id="fc-dark-toggle">
    <input type="checkbox" id="fc-dark-cb"> Dark mode previews
  </label>
  <div id="fc-previews"></div>
</div>

<script>
(function() {
  var dropZone = document.getElementById('fc-drop-zone');
  var fileInput = document.getElementById('fc-file-input');
  var fileInfo = document.getElementById('fc-file-info');
  var warningsEl = document.getElementById('fc-warnings');
  var sizeGrid = document.getElementById('fc-size-grid');
  var previewsEl = document.getElementById('fc-previews');
  var darkCb = document.getElementById('fc-dark-cb');
  var placeholder = document.getElementById('fc-placeholder-msg');
  var sections = document.getElementById('fc-sections');

  var currentImg = null;
  var isDark = false;

  var SIZES = [
    { px: 16,  label: '16×16',   usage: 'Browser tab' },
    { px: 32,  label: '32×32',   usage: 'Desktop shortcut' },
    { px: 48,  label: '48×48',   usage: 'Windows taskbar' },
    { px: 64,  label: '64×64',   usage: 'High-DPI tab' },
    { px: 128, label: '128×128', usage: 'Chrome Web Store' },
    { px: 180, label: '180×180', usage: 'Apple Touch Icon' },
    { px: 192, label: '192×192', usage: 'Android PWA' },
    { px: 512, label: '512×512', usage: 'PWA splash screen' },
  ];

  // Drag and drop
  dropZone.addEventListener('dragover', function(e) {
    e.preventDefault();
    dropZone.classList.add('fc-drag-over');
  });
  dropZone.addEventListener('dragleave', function() {
    dropZone.classList.remove('fc-drag-over');
  });
  dropZone.addEventListener('drop', function(e) {
    e.preventDefault();
    dropZone.classList.remove('fc-drag-over');
    var file = e.dataTransfer.files[0];
    if (file) processFile(file);
  });
  fileInput.addEventListener('change', function() {
    if (this.files[0]) processFile(this.files[0]);
  });
  darkCb.addEventListener('change', function() {
    isDark = this.checked;
    if (currentImg) renderPreviews(currentImg);
  });

  function formatBytes(b) {
    if (b < 1024) return b + ' B';
    if (b < 1024 * 1024) return (b / 1024).toFixed(1) + ' KB';
    return (b / (1024 * 1024)).toFixed(2) + ' MB';
  }

  function processFile(file) {
    var reader = new FileReader();
    reader.onload = function(e) {
      var src = e.target.result;
      var img = new Image();
      img.onload = function() {
        currentImg = img;
        showFileInfo(file, img);
        renderSizes(img, file);
        renderPreviews(img);
        showWarnings(img, file);
        placeholder.style.display = 'none';
        sections.style.display = '';
      };
      img.onerror = function() {
        alert('Could not load image. Please try a different file.');
      };
      img.src = src;
    };
    reader.readAsDataURL(file);
  }

  function showFileInfo(file, img) {
    var ext = file.name.split('.').pop().toUpperCase();
    fileInfo.style.display = '';
    fileInfo.innerHTML =
      '<span><strong>File:</strong> ' + escHtml(file.name) + '</span>' +
      '<span><strong>Format:</strong> ' + ext + '</span>' +
      '<span><strong>Size:</strong> ' + formatBytes(file.size) + '</span>' +
      '<span><strong>Dimensions:</strong> ' + img.naturalWidth + '×' + img.naturalHeight + 'px</span>';
  }

  function showWarnings(img, file) {
    var warns = [];
    var w = img.naturalWidth, h = img.naturalHeight;
    if (w !== h) {
      warns.push('Image is not square (' + w + '×' + h + '). Favicons should be square for best results.');
    }
    if (w < 32 || h < 32) {
      warns.push('Image is smaller than 32×32 px. It may appear blurry in browser tabs and on desktop.');
    }
    if (w < 180 || h < 180) {
      warns.push('Image is smaller than 180×180 px. Apple Touch Icon (home screen) will be upscaled and may look blurry.');
    }
    if (w < 192 || h < 192) {
      warns.push('Image is smaller than 192×192 px. Android PWA icon may appear low-quality.');
    }
    if (w < 512 || h < 512) {
      warns.push('Image is smaller than 512×512 px. PWA splash screen icon will be upscaled.');
    }
    if (file.size > 100 * 1024) {
      warns.push('File size is ' + formatBytes(file.size) + '. Favicon files should ideally be under 100 KB.');
    }
    warningsEl.innerHTML = '';
    if (warns.length > 0) {
      warningsEl.style.display = '';
      warns.forEach(function(msg) {
        var d = document.createElement('div');
        d.className = 'fc-warn';
        d.innerHTML = '<span class="fc-warn-icon">⚠️</span><span>' + escHtml(msg) + '</span>';
        warningsEl.appendChild(d);
      });
    } else {
      warningsEl.style.display = 'none';
    }
  }

  function renderSizes(img, file) {
    sizeGrid.innerHTML = '';
    SIZES.forEach(function(s) {
      var card = document.createElement('div');
      card.className = 'fc-size-card';

      var cvs = document.createElement('canvas');
      var displaySize = Math.min(s.px, 64);
      cvs.width = s.px;
      cvs.height = s.px;
      cvs.style.width = displaySize + 'px';
      cvs.style.height = displaySize + 'px';
      var ctx = cvs.getContext('2d');
      ctx.drawImage(img, 0, 0, s.px, s.px);

      var srcW = img.naturalWidth, srcH = img.naturalHeight;
      var isOk = srcW >= s.px && srcH >= s.px;

      var labelDiv = document.createElement('div');
      labelDiv.className = 'fc-size-label';
      labelDiv.textContent = s.label;

      var usageDiv = document.createElement('div');
      usageDiv.className = 'fc-size-usage';
      usageDiv.textContent = s.usage;

      var statusDiv = document.createElement('div');
      statusDiv.className = isOk ? 'fc-size-ok' : 'fc-size-warn';
      statusDiv.textContent = isOk ? '✓ Good' : '✗ Too small';

      card.appendChild(cvs);
      card.appendChild(labelDiv);
      card.appendChild(usageDiv);
      card.appendChild(statusDiv);
      sizeGrid.appendChild(card);
    });
  }

  function makeIconCanvas(img, size) {
    var cvs = document.createElement('canvas');
    cvs.width = size;
    cvs.height = size;
    cvs.style.width = size + 'px';
    cvs.style.height = size + 'px';
    cvs.getContext('2d').drawImage(img, 0, 0, size, size);
    return cvs;
  }

  function renderPreviews(img) {
    previewsEl.innerHTML = '';

    var dark = isDark;
    var darkCls = dark ? ' fc-dark' : '';
    var darkInner = dark ? 'fc-dark' : 'fc-light';

    // --- Chrome tab ---
    var chromeBlock = makeBlock('Chrome Tab');
    var chromeInner = document.createElement('div');
    chromeInner.className = 'fc-preview-inner ' + darkInner;
    var tabBar = document.createElement('div');
    tabBar.className = 'fc-tab-bar' + darkCls;
    var tab = document.createElement('div');
    tab.className = 'fc-chrome-tab' + darkCls;
    tab.appendChild(makeIconCanvas(img, 16));
    var titleSpan = document.createElement('span');
    titleSpan.className = 'fc-tab-title';
    titleSpan.textContent = 'Your Website';
    var closeSpan = document.createElement('span');
    closeSpan.className = 'fc-tab-close';
    closeSpan.textContent = '✕';
    tab.appendChild(titleSpan);
    tab.appendChild(closeSpan);
    tabBar.appendChild(tab);
    chromeInner.appendChild(tabBar);
    chromeBlock.appendChild(chromeInner);
    previewsEl.appendChild(chromeBlock);

    // --- Safari tab ---
    var safariBlock = makeBlock('Safari Address Bar');
    var safariInner = document.createElement('div');
    safariInner.className = 'fc-preview-inner ' + darkInner;
    var safariBar = document.createElement('div');
    safariBar.className = 'fc-safari-bar' + darkCls;
    var urlBar = document.createElement('div');
    urlBar.className = 'fc-safari-urlbar' + darkCls;
    urlBar.appendChild(makeIconCanvas(img, 14));
    var urlText = document.createElement('span');
    urlText.textContent = 'yourwebsite.com';
    urlBar.appendChild(urlText);
    safariBar.appendChild(urlBar);
    safariInner.appendChild(safariBar);
    safariBlock.appendChild(safariInner);
    previewsEl.appendChild(safariBlock);

    // --- Firefox tab ---
    var ffBlock = makeBlock('Firefox Tab');
    var ffInner = document.createElement('div');
    ffInner.className = 'fc-preview-inner ' + darkInner;
    var ffBar = document.createElement('div');
    ffBar.className = 'fc-firefox-bar' + darkCls;
    var ffTab = document.createElement('div');
    ffTab.className = 'fc-firefox-tab' + darkCls;
    ffTab.appendChild(makeIconCanvas(img, 16));
    var ffTitle = document.createElement('span');
    ffTitle.textContent = 'Your Website';
    ffTab.appendChild(ffTitle);
    ffBar.appendChild(ffTab);
    ffInner.appendChild(ffBar);
    ffBlock.appendChild(ffInner);
    previewsEl.appendChild(ffBlock);

    // --- Bookmarks bar ---
    var bkBlock = makeBlock('Bookmarks Bar');
    var bkInner = document.createElement('div');
    bkInner.className = 'fc-preview-inner ' + darkInner;
    var bkBar = document.createElement('div');
    bkBar.className = 'fc-bookmarks-bar' + darkCls;
    var bkItems = [
      { name: 'Your Site' },
      { name: 'Dashboard' },
      { name: 'Docs' }
    ];
    bkItems.forEach(function(item, i) {
      var bkItem = document.createElement('div');
      bkItem.className = 'fc-bookmark-item' + darkCls;
      bkItem.appendChild(makeIconCanvas(img, 16));
      var bkName = document.createElement('span');
      bkName.textContent = item.name;
      bkItem.appendChild(bkName);
      bkBar.appendChild(bkItem);
    });
    bkInner.appendChild(bkBar);
    bkBlock.appendChild(bkInner);
    previewsEl.appendChild(bkBlock);

    // --- Google search result ---
    var gBlock = makeBlock('Google Search Result');
    var gInner = document.createElement('div');
    gInner.className = 'fc-preview-inner ' + (dark ? 'fc-dark' : 'fc-light');
    if (dark) gInner.style.background = '#202124';
    var gResult = document.createElement('div');
    gResult.className = 'fc-google-result';
    var siteRow = document.createElement('div');
    siteRow.className = 'fc-google-site-row';
    siteRow.appendChild(makeIconCanvas(img, 18));
    var siteNames = document.createElement('div');
    var siteName = document.createElement('div');
    siteName.className = 'fc-google-site-name' + darkCls;
    siteName.textContent = 'Your Website';
    var siteUrl = document.createElement('div');
    siteUrl.className = 'fc-google-site-url';
    siteUrl.textContent = 'https://yourwebsite.com › page';
    siteNames.appendChild(siteName);
    siteNames.appendChild(siteUrl);
    siteRow.appendChild(siteNames);
    var gTitle = document.createElement('div');
    gTitle.className = 'fc-google-title' + darkCls;
    gTitle.textContent = 'Page Title — Your Website';
    var gDesc = document.createElement('div');
    gDesc.className = 'fc-google-desc' + darkCls;
    gDesc.textContent = 'A short description of the page content appears here in Google search results, typically truncated at around 155–160 characters.';
    gResult.appendChild(siteRow);
    gResult.appendChild(gTitle);
    gResult.appendChild(gDesc);
    gInner.appendChild(gResult);
    gBlock.appendChild(gInner);
    previewsEl.appendChild(gBlock);

    // --- Mobile home screen ---
    var mBlock = makeBlock('Mobile Home Screen');
    var mInner = document.createElement('div');
    mInner.className = 'fc-preview-inner ' + darkInner;
    var mScreen = document.createElement('div');
    mScreen.className = 'fc-mobile-screen' + darkCls;
    var row1 = document.createElement('div');
    row1.className = 'fc-mobile-row';
    var fakeApps = [
      { name: 'Your App', isYours: true },
      { name: 'Photos', isYours: false },
      { name: 'Maps', isYours: false },
      { name: 'Mail', isYours: false },
    ];
    fakeApps.forEach(function(app) {
      var wrap = document.createElement('div');
      wrap.className = 'fc-app-icon-wrap';
      var iconWrap = document.createElement('div');
      iconWrap.className = 'fc-app-icon';
      if (app.isYours) {
        iconWrap.appendChild(makeIconCanvas(img, 60));
      } else {
        var placeholder2 = document.createElement('div');
        placeholder2.style.cssText = 'width:60px;height:60px;border-radius:14px;background:' +
          ['#ef4444','#3b82f6','#10b981'][Math.floor(Math.random() * 3)] + ';';
        iconWrap.appendChild(placeholder2);
      }
      var appName = document.createElement('div');
      appName.className = 'fc-app-icon-name';
      appName.textContent = app.name;
      wrap.appendChild(iconWrap);
      wrap.appendChild(appName);
      row1.appendChild(wrap);
    });
    mScreen.appendChild(row1);
    mInner.appendChild(mScreen);
    mBlock.appendChild(mInner);
    previewsEl.appendChild(mBlock);

    // --- Windows taskbar ---
    var wBlock = makeBlock('Windows Taskbar');
    var wInner = document.createElement('div');
    wInner.className = 'fc-preview-inner fc-dark';
    wInner.style.background = '#0f172a';
    var taskbar = document.createElement('div');
    taskbar.className = 'fc-taskbar';
    var tbItem = document.createElement('div');
    tbItem.className = 'fc-taskbar-item';
    tbItem.appendChild(makeIconCanvas(img, 20));
    var tbLabel = document.createElement('span');
    tbLabel.textContent = 'Your Website';
    tbItem.appendChild(tbLabel);
    taskbar.appendChild(tbItem);
    wInner.appendChild(taskbar);
    wBlock.appendChild(wInner);
    previewsEl.appendChild(wBlock);
  }

  function makeBlock(labelText) {
    var block = document.createElement('div');
    block.className = 'fc-preview-block';
    var label = document.createElement('div');
    label.className = 'fc-preview-label';
    label.textContent = labelText;
    block.appendChild(label);
    return block;
  }

  function escHtml(str) {
    return String(str)
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;');
  }
})();
</script>

</div>

---

**Related tools:** Generate favicons → [Favicon Generator](/tools/favicon-generator/) &nbsp;|&nbsp; Meta tags → [Meta Tag Generator](/tools/meta-tag-generator/)
