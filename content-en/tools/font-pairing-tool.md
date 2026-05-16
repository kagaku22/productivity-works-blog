---
title: "Font Pairing Tool — Find Perfect Heading & Body Font Combinations"
date: 2025-05-16
description: "Explore 12 curated font pairings using system fonts. Live preview with customizable text, size, line height, letter spacing, and color. Copy CSS instantly. No external dependencies."
categories: ["Free Tools"]
slug: "font-pairing-tool"
ShowToc: false
aliases:
  - "/tools/font-pair-suggester/"
  - "/tools/font-pairing-tool/"
cover:
  image: "/images/covers/font-pairing-tool.png"
  alt: "Font Pairing Tool"
---

<div id="fp-app">

<style>
#fp-app *,
#fp-app *::before,
#fp-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#fp-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: #1a1a2e;
  line-height: 1.6;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 16px;
}

#fp-app .fp-hero {
  background: linear-gradient(135deg, #7c3aed 0%, #2563eb 100%);
  color: #fff;
  border-radius: 14px;
  padding: 36px 28px 28px;
  margin-bottom: 24px;
  text-align: center;
}

#fp-app .fp-hero h2 {
  font-size: 1.85rem;
  font-weight: 800;
  margin-bottom: 8px;
  letter-spacing: -0.02em;
}

#fp-app .fp-hero p {
  font-size: 1rem;
  opacity: 0.9;
}

#fp-app .fp-layout {
  display: grid;
  grid-template-columns: 300px 1fr;
  gap: 20px;
  align-items: start;
}

@media (max-width: 700px) {
  #fp-app .fp-layout {
    grid-template-columns: 1fr;
  }
}

#fp-app .fp-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
}

#fp-app .fp-card h3 {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 14px;
}

/* Pairing list */
#fp-app .fp-pairing-list {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

#fp-app .fp-pairing-btn {
  display: block;
  width: 100%;
  text-align: left;
  padding: 12px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 9px;
  background: #fff;
  cursor: pointer;
  transition: border-color 0.15s, background 0.15s;
}

#fp-app .fp-pairing-btn:hover {
  border-color: #7c3aed;
  background: #faf5ff;
}

#fp-app .fp-pairing-btn.active {
  border-color: #7c3aed;
  background: #f5f3ff;
}

#fp-app .fp-pairing-btn .fp-btn-heading {
  font-size: 0.95rem;
  font-weight: 700;
  color: #1e1b4b;
  line-height: 1.2;
}

#fp-app .fp-pairing-btn .fp-btn-body {
  font-size: 0.78rem;
  color: #64748b;
  margin-top: 2px;
}

#fp-app .fp-pairing-btn .fp-btn-tag {
  font-size: 0.68rem;
  padding: 2px 7px;
  border-radius: 20px;
  background: #ede9fe;
  color: #6d28d9;
  display: inline-block;
  margin-top: 5px;
  font-weight: 600;
}

/* Controls */
#fp-app .fp-controls {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 16px;
}

@media (max-width: 480px) {
  #fp-app .fp-controls {
    grid-template-columns: 1fr;
  }
}

#fp-app .fp-control-group label {
  display: block;
  font-size: 0.75rem;
  font-weight: 600;
  color: #475569;
  margin-bottom: 5px;
}

#fp-app .fp-control-group input[type="range"] {
  width: 100%;
  accent-color: #7c3aed;
  cursor: pointer;
}

#fp-app .fp-control-group input[type="text"] {
  width: 100%;
  padding: 7px 10px;
  border: 1.5px solid #e2e8f0;
  border-radius: 7px;
  font-size: 0.85rem;
  outline: none;
  transition: border-color 0.15s;
}

#fp-app .fp-control-group input[type="text"]:focus {
  border-color: #7c3aed;
}

#fp-app .fp-control-group input[type="color"] {
  width: 100%;
  height: 36px;
  padding: 2px 4px;
  border: 1.5px solid #e2e8f0;
  border-radius: 7px;
  cursor: pointer;
  background: #fff;
}

#fp-app .fp-val {
  font-size: 0.72rem;
  color: #7c3aed;
  font-weight: 700;
  margin-left: 6px;
}

/* Mode tabs */
#fp-app .fp-mode-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

#fp-app .fp-mode-tab {
  padding: 6px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 20px;
  background: #fff;
  font-size: 0.8rem;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  transition: all 0.15s;
}

#fp-app .fp-mode-tab:hover {
  border-color: #7c3aed;
  color: #7c3aed;
}

#fp-app .fp-mode-tab.active {
  background: #7c3aed;
  border-color: #7c3aed;
  color: #fff;
}

/* Preview area */
#fp-app .fp-preview-wrap {
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  overflow: hidden;
  margin-bottom: 16px;
}

#fp-app .fp-preview-label {
  font-size: 0.72rem;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  padding: 8px 14px;
  background: #f8fafc;
  border-bottom: 1px solid #e2e8f0;
}

#fp-app #fp-preview {
  padding: 28px 24px;
  min-height: 220px;
  background: #fff;
  transition: background 0.2s;
}

/* Preview mode: hero */
#fp-app #fp-preview.mode-hero {
  background: linear-gradient(135deg, #1e1b4b 0%, #312e81 100%);
  padding: 48px 36px;
}

/* Preview mode: card */
#fp-app #fp-preview.mode-card {
  background: #f1f5f9;
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  padding: 20px;
}

#fp-app .fp-preview-card {
  flex: 1;
  min-width: 180px;
  background: #fff;
  border-radius: 10px;
  padding: 18px;
  box-shadow: 0 1px 6px rgba(0,0,0,0.08);
}

#fp-app .fp-preview-card .fp-card-tag {
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #7c3aed;
  margin-bottom: 8px;
}

/* CSS output */
#fp-app .fp-css-box {
  background: #0f172a;
  border-radius: 10px;
  padding: 16px;
  position: relative;
}

#fp-app .fp-css-box pre {
  font-family: "Consolas", "Courier New", Courier, monospace;
  font-size: 0.78rem;
  color: #e2e8f0;
  white-space: pre-wrap;
  word-break: break-all;
  line-height: 1.7;
}

#fp-app .fp-copy-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 5px 12px;
  background: #7c3aed;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 0.75rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}

#fp-app .fp-copy-btn:hover {
  background: #6d28d9;
}

#fp-app .fp-copy-btn.copied {
  background: #16a34a;
}

#fp-app .fp-info-strip {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  padding: 12px 14px;
  background: #f5f3ff;
  border: 1.5px solid #ddd6fe;
  border-radius: 9px;
  margin-bottom: 16px;
}

#fp-app .fp-info-item {
  font-size: 0.78rem;
  color: #5b21b6;
}

#fp-app .fp-info-item strong {
  font-weight: 700;
}

#fp-app .fp-section-title {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #64748b;
  margin-bottom: 10px;
}
</style>

<div class="fp-hero">
  <h2>Font Pairing Tool</h2>
  <p>12 curated system-font pairings — live preview, adjust typography, copy CSS</p>
</div>

<div class="fp-layout">

  <!-- Left: Pairing selector -->
  <div class="fp-card">
    <h3>Font Pairings</h3>
    <div class="fp-pairing-list" id="fp-pairing-list"></div>
  </div>

  <!-- Right: Controls + Preview -->
  <div>

    <!-- Info strip -->
    <div class="fp-info-strip" id="fp-info-strip">
      <span class="fp-info-item"><strong>Heading:</strong> <span id="fp-info-heading">—</span></span>
      <span class="fp-info-item"><strong>Body:</strong> <span id="fp-info-body">—</span></span>
      <span class="fp-info-item"><strong>Style:</strong> <span id="fp-info-style">—</span></span>
    </div>

    <!-- Controls -->
    <div class="fp-card" style="margin-bottom:16px;">
      <h3>Customize</h3>
      <div class="fp-controls">
        <div class="fp-control-group" style="grid-column:1/-1;">
          <label>Sample Text</label>
          <input type="text" id="fp-sample-text" value="The quick brown fox jumps over the lazy dog" />
        </div>
        <div class="fp-control-group">
          <label>Heading Size <span class="fp-val" id="fp-heading-size-val">2.4rem</span></label>
          <input type="range" id="fp-heading-size" min="1.2" max="4.5" step="0.1" value="2.4" />
        </div>
        <div class="fp-control-group">
          <label>Body Size <span class="fp-val" id="fp-body-size-val">1rem</span></label>
          <input type="range" id="fp-body-size" min="0.75" max="1.5" step="0.05" value="1" />
        </div>
        <div class="fp-control-group">
          <label>Line Height <span class="fp-val" id="fp-line-height-val">1.6</span></label>
          <input type="range" id="fp-line-height" min="1.0" max="2.5" step="0.05" value="1.6" />
        </div>
        <div class="fp-control-group">
          <label>Letter Spacing <span class="fp-val" id="fp-letter-spacing-val">0em</span></label>
          <input type="range" id="fp-letter-spacing" min="-0.05" max="0.2" step="0.005" value="0" />
        </div>
        <div class="fp-control-group">
          <label>Heading Color</label>
          <input type="color" id="fp-heading-color" value="#1a1a2e" />
        </div>
        <div class="fp-control-group">
          <label>Body Color</label>
          <input type="color" id="fp-body-color" value="#374151" />
        </div>
      </div>

      <div class="fp-section-title">Preview Mode</div>
      <div class="fp-mode-tabs">
        <button class="fp-mode-tab active" data-mode="blog">Blog Post</button>
        <button class="fp-mode-tab" data-mode="hero">Hero Section</button>
        <button class="fp-mode-tab" data-mode="card">Card Layout</button>
      </div>
    </div>

    <!-- Preview -->
    <div class="fp-preview-wrap">
      <div class="fp-preview-label">Live Preview</div>
      <div id="fp-preview"></div>
    </div>

    <!-- CSS Output -->
    <div class="fp-card">
      <h3>CSS Code</h3>
      <div class="fp-css-box">
        <pre id="fp-css-output"></pre>
        <button class="fp-copy-btn" id="fp-copy-btn">Copy CSS</button>
      </div>
    </div>

  </div>
</div>

<script>
(function() {
  const PAIRINGS = [
    {
      id: "p1",
      name: "Classic Editorial",
      heading: "Georgia",
      headingStack: "Georgia, 'Times New Roman', Times, serif",
      body: "Verdana",
      bodyStack: "Verdana, Geneva, Tahoma, sans-serif",
      style: "Editorial",
      tag: "serif + sans"
    },
    {
      id: "p2",
      name: "Modern Minimal",
      heading: "Helvetica Neue",
      headingStack: "'Helvetica Neue', Helvetica, Arial, sans-serif",
      body: "Georgia",
      bodyStack: "Georgia, 'Times New Roman', Times, serif",
      style: "Minimal",
      tag: "sans + serif"
    },
    {
      id: "p3",
      name: "System Native",
      heading: "system-ui",
      headingStack: "system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif",
      body: "system-ui",
      bodyStack: "system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif",
      style: "Native",
      tag: "system + system"
    },
    {
      id: "p4",
      name: "Tech Mono",
      heading: "Consolas",
      headingStack: "Consolas, 'Courier New', Courier, monospace",
      body: "Segoe UI",
      bodyStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
      style: "Technical",
      tag: "mono + sans"
    },
    {
      id: "p5",
      name: "Timeless Serif",
      heading: "Palatino",
      headingStack: "Palatino, 'Palatino Linotype', 'Book Antiqua', Georgia, serif",
      body: "Arial",
      bodyStack: "Arial, Helvetica, sans-serif",
      style: "Timeless",
      tag: "serif + sans"
    },
    {
      id: "p6",
      name: "Bold Contrast",
      heading: "Arial",
      headingStack: "Arial, Helvetica, sans-serif",
      body: "Georgia",
      bodyStack: "Georgia, 'Times New Roman', Times, serif",
      style: "Contrast",
      tag: "sans + serif"
    },
    {
      id: "p7",
      name: "Digital Clean",
      heading: "Segoe UI",
      headingStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
      body: "Verdana",
      bodyStack: "Verdana, Geneva, Tahoma, sans-serif",
      style: "Digital",
      tag: "sans + sans"
    },
    {
      id: "p8",
      name: "Literary Classic",
      heading: "Times New Roman",
      headingStack: "'Times New Roman', Times, Georgia, serif",
      body: "Helvetica",
      bodyStack: "Helvetica, Arial, sans-serif",
      style: "Literary",
      tag: "serif + sans"
    },
    {
      id: "p9",
      name: "Humanist Warm",
      heading: "Verdana",
      headingStack: "Verdana, Geneva, Tahoma, sans-serif",
      body: "Palatino",
      bodyStack: "Palatino, 'Palatino Linotype', 'Book Antiqua', Georgia, serif",
      style: "Humanist",
      tag: "sans + serif"
    },
    {
      id: "p10",
      name: "Code & Prose",
      heading: "Courier New",
      headingStack: "'Courier New', Courier, Consolas, monospace",
      body: "Segoe UI",
      bodyStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
      style: "Developer",
      tag: "mono + sans"
    },
    {
      id: "p11",
      name: "Corporate Clean",
      heading: "Segoe UI",
      headingStack: "'Segoe UI', system-ui, -apple-system, Arial, sans-serif",
      body: "Arial",
      bodyStack: "Arial, Helvetica, sans-serif",
      style: "Corporate",
      tag: "sans + sans"
    },
    {
      id: "p12",
      name: "Elegant Book",
      heading: "Georgia",
      headingStack: "Georgia, 'Times New Roman', Times, serif",
      body: "Palatino",
      bodyStack: "Palatino, 'Palatino Linotype', 'Book Antiqua', Georgia, serif",
      style: "Elegant",
      tag: "serif + serif"
    }
  ];

  let current = PAIRINGS[0];
  let mode = "blog";
  let headingSize = 2.4;
  let bodySize = 1.0;
  let lineHeight = 1.6;
  let letterSpacing = 0;
  let headingColor = "#1a1a2e";
  let bodyColor = "#374151";
  let sampleText = "The quick brown fox jumps over the lazy dog";

  function buildPairingList() {
    const list = document.getElementById("fp-pairing-list");
    PAIRINGS.forEach(function(p, i) {
      const btn = document.createElement("button");
      btn.className = "fp-pairing-btn" + (i === 0 ? " active" : "");
      btn.setAttribute("data-id", p.id);
      btn.innerHTML =
        '<div class="fp-btn-heading" style="font-family:' + p.headingStack + '">' + p.name + '</div>' +
        '<div class="fp-btn-body">' + p.heading + ' + ' + p.body + '</div>' +
        '<span class="fp-btn-tag">' + p.tag + '</span>';
      btn.addEventListener("click", function() {
        document.querySelectorAll("#fp-app .fp-pairing-btn").forEach(function(b) { b.classList.remove("active"); });
        btn.classList.add("active");
        current = p;
        render();
      });
      list.appendChild(btn);
    });
  }

  function getSampleText() {
    return document.getElementById("fp-sample-text").value || sampleText;
  }

  function renderBlogMode(preview, txt) {
    preview.className = "";
    preview.id = "fp-preview";
    preview.style.background = "#fff";
    preview.style.padding = "28px 24px";
    const tag = document.createElement("div");
    tag.style.cssText = "font-size:0.72rem;font-weight:700;text-transform:uppercase;letter-spacing:0.08em;color:#7c3aed;margin-bottom:12px;font-family:" + current.bodyStack;
    tag.textContent = current.style + " · " + current.tag;

    const h = document.createElement("h2");
    h.style.cssText = "font-family:" + current.headingStack + ";font-size:" + headingSize + "rem;line-height:1.2;letter-spacing:" + letterSpacing + "em;color:" + headingColor + ";margin-bottom:14px;font-weight:700;";
    h.textContent = txt;

    const p1 = document.createElement("p");
    p1.style.cssText = "font-family:" + current.bodyStack + ";font-size:" + bodySize + "rem;line-height:" + lineHeight + ";letter-spacing:" + letterSpacing + "em;color:" + bodyColor + ";margin-bottom:12px;";
    p1.textContent = "Typography shapes how readers experience content. The interplay between a commanding heading font and a legible body font creates visual hierarchy that guides the eye naturally through the page.";

    const p2 = document.createElement("p");
    p2.style.cssText = p1.style.cssText;
    p2.textContent = "Great font pairings feel invisible — they let the content shine while establishing a consistent personality. Contrast in weight, width, or classification creates interest without chaos.";

    preview.innerHTML = "";
    preview.appendChild(tag);
    preview.appendChild(h);
    preview.appendChild(p1);
    preview.appendChild(p2);
  }

  function renderHeroMode(preview, txt) {
    preview.className = "mode-hero";
    preview.id = "fp-preview";
    preview.style.padding = "48px 36px";

    const eyebrow = document.createElement("div");
    eyebrow.style.cssText = "font-family:" + current.bodyStack + ";font-size:0.75rem;font-weight:700;text-transform:uppercase;letter-spacing:0.12em;color:rgba(255,255,255,0.7);margin-bottom:14px;";
    eyebrow.textContent = current.style + " pairing";

    const h = document.createElement("h1");
    h.style.cssText = "font-family:" + current.headingStack + ";font-size:" + headingSize + "rem;line-height:1.15;letter-spacing:" + letterSpacing + "em;color:#fff;margin-bottom:16px;font-weight:800;";
    h.textContent = txt;

    const sub = document.createElement("p");
    sub.style.cssText = "font-family:" + current.bodyStack + ";font-size:" + bodySize + "rem;line-height:" + lineHeight + ";color:rgba(255,255,255,0.85);max-width:520px;letter-spacing:" + letterSpacing + "em;";
    sub.textContent = "Typography is the craft of arranging type to make written language legible, readable, and appealing when displayed.";

    const btn = document.createElement("a");
    btn.style.cssText = "display:inline-block;margin-top:20px;padding:11px 24px;background:#7c3aed;color:#fff;border-radius:8px;font-family:" + current.bodyStack + ";font-size:0.9rem;font-weight:700;text-decoration:none;";
    btn.textContent = "Get Started";
    btn.href = "#";

    preview.innerHTML = "";
    preview.appendChild(eyebrow);
    preview.appendChild(h);
    preview.appendChild(sub);
    preview.appendChild(btn);
  }

  function renderCardMode(preview, txt) {
    preview.className = "mode-card";
    preview.id = "fp-preview";

    const cards = [
      { tag: "Design", title: txt, body: "Typography sets the tone for your entire visual system." },
      { tag: "Code", title: "Readable at Scale", body: "Consistent font use builds trust and improves comprehension." },
      { tag: "Content", title: "Pair With Purpose", body: "Each pairing creates a distinct mood and reader experience." }
    ];

    preview.innerHTML = "";
    cards.forEach(function(c) {
      const card = document.createElement("div");
      card.className = "fp-preview-card";

      const tagEl = document.createElement("div");
      tagEl.className = "fp-card-tag";
      tagEl.style.fontFamily = current.bodyStack;
      tagEl.textContent = c.tag;

      const titleEl = document.createElement("h3");
      titleEl.style.cssText = "font-family:" + current.headingStack + ";font-size:" + Math.max(1.0, headingSize * 0.55) + "rem;line-height:1.25;letter-spacing:" + letterSpacing + "em;color:" + headingColor + ";margin-bottom:8px;font-weight:700;";
      titleEl.textContent = c.title;

      const bodyEl = document.createElement("p");
      bodyEl.style.cssText = "font-family:" + current.bodyStack + ";font-size:" + Math.max(0.75, bodySize * 0.9) + "rem;line-height:" + lineHeight + ";color:" + bodyColor + ";letter-spacing:" + letterSpacing + "em;";
      bodyEl.textContent = c.body;

      card.appendChild(tagEl);
      card.appendChild(titleEl);
      card.appendChild(bodyEl);
      preview.appendChild(card);
    });
  }

  function updateCSS() {
    const css =
"/* Font Pairing: " + current.name + " */\n" +
"/* " + current.heading + " (heading) + " + current.body + " (body) */\n\n" +
":root {\n" +
"  --font-heading: " + current.headingStack + ";\n" +
"  --font-body: " + current.bodyStack + ";\n" +
"}\n\n" +
"h1, h2, h3, h4, h5, h6 {\n" +
"  font-family: var(--font-heading);\n" +
"  font-size: " + headingSize + "rem;\n" +
"  line-height: 1.2;\n" +
"  letter-spacing: " + letterSpacing + "em;\n" +
"  color: " + headingColor + ";\n" +
"}\n\n" +
"body, p {\n" +
"  font-family: var(--font-body);\n" +
"  font-size: " + bodySize + "rem;\n" +
"  line-height: " + lineHeight + ";\n" +
"  letter-spacing: " + letterSpacing + "em;\n" +
"  color: " + bodyColor + ";\n" +
"}";
    document.getElementById("fp-css-output").textContent = css;
  }

  function updateInfo() {
    document.getElementById("fp-info-heading").textContent = current.heading;
    document.getElementById("fp-info-body").textContent = current.body;
    document.getElementById("fp-info-style").textContent = current.style;
  }

  function render() {
    const preview = document.getElementById("fp-preview");
    const txt = getSampleText();
    if (mode === "hero") {
      renderHeroMode(preview, txt);
    } else if (mode === "card") {
      renderCardMode(preview, txt);
    } else {
      renderBlogMode(preview, txt);
    }
    updateCSS();
    updateInfo();
  }

  // Range inputs
  document.getElementById("fp-heading-size").addEventListener("input", function() {
    headingSize = parseFloat(this.value);
    document.getElementById("fp-heading-size-val").textContent = headingSize + "rem";
    render();
  });
  document.getElementById("fp-body-size").addEventListener("input", function() {
    bodySize = parseFloat(this.value);
    document.getElementById("fp-body-size-val").textContent = bodySize + "rem";
    render();
  });
  document.getElementById("fp-line-height").addEventListener("input", function() {
    lineHeight = parseFloat(this.value);
    document.getElementById("fp-line-height-val").textContent = lineHeight;
    render();
  });
  document.getElementById("fp-letter-spacing").addEventListener("input", function() {
    letterSpacing = parseFloat(this.value);
    document.getElementById("fp-letter-spacing-val").textContent = letterSpacing + "em";
    render();
  });
  document.getElementById("fp-heading-color").addEventListener("input", function() {
    headingColor = this.value;
    render();
  });
  document.getElementById("fp-body-color").addEventListener("input", function() {
    bodyColor = this.value;
    render();
  });
  document.getElementById("fp-sample-text").addEventListener("input", render);

  // Mode tabs
  document.querySelectorAll("#fp-app .fp-mode-tab").forEach(function(tab) {
    tab.addEventListener("click", function() {
      document.querySelectorAll("#fp-app .fp-mode-tab").forEach(function(t) { t.classList.remove("active"); });
      tab.classList.add("active");
      mode = tab.getAttribute("data-mode");
      render();
    });
  });

  // Copy CSS
  document.getElementById("fp-copy-btn").addEventListener("click", function() {
    const text = document.getElementById("fp-css-output").textContent;
    const btn = document.getElementById("fp-copy-btn");
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(function() {
        btn.textContent = "Copied!";
        btn.classList.add("copied");
        setTimeout(function() {
          btn.textContent = "Copy CSS";
          btn.classList.remove("copied");
        }, 2000);
      });
    } else {
      const ta = document.createElement("textarea");
      ta.value = text;
      ta.style.position = "fixed";
      ta.style.left = "-9999px";
      document.body.appendChild(ta);
      ta.select();
      document.execCommand("copy");
      document.body.removeChild(ta);
      btn.textContent = "Copied!";
      btn.classList.add("copied");
      setTimeout(function() {
        btn.textContent = "Copy CSS";
        btn.classList.remove("copied");
      }, 2000);
    }
  });

  buildPairingList();
  render();
})();
</script>

</div>

---

### Related Tools
> Convert font sizes → [Font Size Converter](/tools/font-size-converter/)
> Generate color palettes → [Color Palette Generator](/tools/color-palette-generator/)
