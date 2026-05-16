---
title: "CSS Minifier & Beautifier"
date: 2025-05-16
slug: "css-minifier"
categories: ["Free Tools"]
ShowToc: false
aliases:
  - "/tools/css-compressor/"
  - "/tools/minify-css/"
cover:
  image: "/images/covers/css-minifier.png"
  alt: "CSS Minifier and Beautifier"
---

Minify CSS to reduce file size or beautify/format compressed CSS for readability. Shows compression ratio instantly. No server upload — all processing happens in your browser.

> Format HTML → [HTML Beautifier](/tools/html-beautifier/)

<div id="cm2-app">

<style>
#cm2-app *,
#cm2-app *::before,
#cm2-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#cm2-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: #1e293b;
  max-width: 820px;
}
#cm2-app h2 {
  font-size: 1rem;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 10px;
}
#cm2-app .cm2-mode-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 16px;
}
#cm2-app .cm2-tab {
  padding: 8px 20px;
  border-radius: 7px;
  border: 1.5px solid #e2e8f0;
  background: #f8fafc;
  color: #475569;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
}
#cm2-app .cm2-tab.active {
  background: #6366f1;
  color: #fff;
  border-color: #6366f1;
}
#cm2-app .cm2-tab:hover:not(.active) {
  background: #f1f5f9;
  border-color: #cbd5e1;
}
#cm2-app .cm2-panels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 14px;
}
@media (max-width: 600px) {
  #cm2-app .cm2-panels { grid-template-columns: 1fr; }
}
#cm2-app .cm2-panel-label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
}
#cm2-app textarea {
  width: 100%;
  height: 240px;
  padding: 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 13px;
  line-height: 1.6;
  resize: vertical;
  font-family: "SFMono-Regular", "Consolas", "Menlo", monospace;
  color: #1e293b;
  background: #fff;
  transition: border-color 0.2s;
}
#cm2-app textarea:focus {
  outline: none;
  border-color: #6366f1;
}
#cm2-app textarea[readonly] {
  background: #f8fafc;
  color: #334155;
}
#cm2-app .cm2-options {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 14px;
  align-items: center;
}
#cm2-app .cm2-option-group {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: #475569;
}
#cm2-app .cm2-option-group label { cursor: pointer; user-select: none; }
#cm2-app .cm2-option-group select {
  padding: 4px 8px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  color: #1e293b;
  background: #fff;
  cursor: pointer;
}
#cm2-app .cm2-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 16px;
}
#cm2-app button {
  padding: 9px 20px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.15s;
}
#cm2-app button:hover { opacity: 0.88; }
#cm2-app .cm2-btn-go {
  background: #6366f1;
  color: #fff;
}
#cm2-app .cm2-btn-clear {
  background: #f1f5f9;
  color: #475569;
}
#cm2-app .cm2-btn-copy {
  background: #f1f5f9;
  color: #475569;
}
#cm2-app .cm2-btn-upload {
  background: #f0fdf4;
  color: #166534;
  border: 1px solid #bbf7d0;
}
#cm2-app input[type="file"] { display: none; }
#cm2-app .cm2-stats {
  display: flex;
  flex-wrap: wrap;
  gap: 18px;
  padding: 12px 16px;
  background: #f8fafc;
  border-radius: 8px;
  font-size: 13px;
  color: #475569;
  margin-bottom: 8px;
}
#cm2-app .cm2-stats span strong {
  color: #1e293b;
  font-size: 15px;
}
#cm2-app .cm2-ratio-pill {
  display: inline-block;
  padding: 2px 10px;
  border-radius: 999px;
  font-size: 12px;
  font-weight: 700;
  background: #ecfdf5;
  color: #065f46;
}
#cm2-app .cm2-ratio-pill.good { background: #ecfdf5; color: #065f46; }
#cm2-app .cm2-ratio-pill.mid { background: #fef9c3; color: #854d0e; }
#cm2-app .cm2-ratio-pill.bad { background: #fef2f2; color: #991b1b; }
</style>

<div class="cm2-mode-tabs">
  <button class="cm2-tab active" id="cm2-tab-minify">Minify</button>
  <button class="cm2-tab" id="cm2-tab-beautify">Beautify</button>
</div>

<div id="cm2-beautify-opts" class="cm2-options" style="display:none">
  <div class="cm2-option-group">
    <label for="cm2-indent">Indent:</label>
    <select id="cm2-indent">
      <option value="2">2 spaces</option>
      <option value="4">4 spaces</option>
      <option value="tab">Tab</option>
    </select>
  </div>
</div>

<div class="cm2-btn-row">
  <button class="cm2-btn-go" id="cm2-go-btn">Minify CSS</button>
  <button class="cm2-btn-clear" id="cm2-clear-btn">Clear</button>
  <button class="cm2-btn-upload" id="cm2-upload-btn">Upload File</button>
  <input type="file" id="cm2-file-input" accept=".css,text/css">
</div>

<div class="cm2-panels">
  <div>
    <div class="cm2-panel-label">Input CSS</div>
    <textarea id="cm2-input" placeholder="Paste your CSS here..."></textarea>
  </div>
  <div>
    <div class="cm2-panel-label">Output</div>
    <textarea id="cm2-output" readonly placeholder="Output will appear here..."></textarea>
  </div>
</div>

<div id="cm2-stats" class="cm2-stats" style="display:none"></div>

<div class="cm2-btn-row" style="margin-top:8px">
  <button class="cm2-btn-copy" id="cm2-copy-btn">Copy Output</button>
</div>

<script>
(function(){
  let currentMode = "minify";

  function minifyCSS(css) {
    // Remove comments
    css = css.replace(/\/\*[\s\S]*?\*\//g, "");
    // Remove whitespace around selectors and braces
    css = css.replace(/\s*([{}:;,>~+])\s*/g, "$1");
    // Remove whitespace at line starts/ends
    css = css.replace(/^\s+|\s+$/gm, "");
    // Collapse multiple spaces
    css = css.replace(/\s{2,}/g, " ");
    // Remove last semicolon before closing brace
    css = css.replace(/;}/g, "}");
    // Collapse newlines
    css = css.replace(/\n+/g, "");
    // Remove spaces inside parentheses for rgb/rgba etc (optional cleanup)
    css = css.replace(/:\s+/g, ":");
    return css.trim();
  }

  function beautifyCSS(css, indent) {
    const indentStr = indent === "tab" ? "\t" : " ".repeat(parseInt(indent));
    // First minify to normalize
    css = minifyCSS(css);
    let out = "";
    let depth = 0;
    let i = 0;
    while (i < css.length) {
      const ch = css[i];
      if (ch === "{") {
        out += " {\n";
        depth++;
        out += indentStr.repeat(depth);
      } else if (ch === "}") {
        depth = Math.max(0, depth - 1);
        out = out.replace(/\s+$/, "");
        out += "\n}\n";
        if (depth > 0) out += indentStr.repeat(depth);
      } else if (ch === ";") {
        out += ";\n" + indentStr.repeat(depth);
      } else if (ch === ",") {
        // Check if inside a rule (depth > 0) or between selectors
        if (depth === 0) {
          out += ",\n";
        } else {
          out += ", ";
        }
      } else {
        out += ch;
      }
      i++;
    }
    // Cleanup extra blank lines
    out = out.replace(/\n{3,}/g, "\n\n").trim();
    return out;
  }

  function fmtBytes(n) {
    if (n < 1024) return n + " B";
    return (n / 1024).toFixed(2) + " KB";
  }

  function process() {
    const input = document.getElementById("cm2-input").value;
    if (!input.trim()) return;
    let output;
    if (currentMode === "minify") {
      output = minifyCSS(input);
    } else {
      const indent = document.getElementById("cm2-indent").value;
      output = beautifyCSS(input, indent);
    }
    document.getElementById("cm2-output").value = output;
    const origSize = new Blob([input]).size;
    const newSize = new Blob([output]).size;
    const saved = origSize - newSize;
    const ratio = origSize > 0 ? ((saved / origSize) * 100).toFixed(1) : 0;
    const pillClass = ratio >= 30 ? "good" : ratio >= 10 ? "mid" : "bad";
    const statsEl = document.getElementById("cm2-stats");
    statsEl.style.display = "flex";
    if (currentMode === "minify") {
      statsEl.innerHTML = `
        <span>Original: <strong>${fmtBytes(origSize)}</strong></span>
        <span>Minified: <strong>${fmtBytes(newSize)}</strong></span>
        <span>Saved: <strong>${fmtBytes(Math.max(0,saved))}</strong></span>
        <span>Ratio: <span class="cm2-ratio-pill ${pillClass}">${ratio}% smaller</span></span>
      `;
    } else {
      statsEl.innerHTML = `
        <span>Original: <strong>${fmtBytes(origSize)}</strong></span>
        <span>Beautified: <strong>${fmtBytes(newSize)}</strong></span>
        <span>Lines: <strong>${output.split("\n").length}</strong></span>
      `;
    }
  }

  document.getElementById("cm2-tab-minify").addEventListener("click", function(){
    currentMode = "minify";
    this.classList.add("active");
    document.getElementById("cm2-tab-beautify").classList.remove("active");
    document.getElementById("cm2-beautify-opts").style.display = "none";
    document.getElementById("cm2-go-btn").textContent = "Minify CSS";
    document.getElementById("cm2-output").value = "";
    document.getElementById("cm2-stats").style.display = "none";
  });

  document.getElementById("cm2-tab-beautify").addEventListener("click", function(){
    currentMode = "beautify";
    this.classList.add("active");
    document.getElementById("cm2-tab-minify").classList.remove("active");
    document.getElementById("cm2-beautify-opts").style.display = "flex";
    document.getElementById("cm2-go-btn").textContent = "Beautify CSS";
    document.getElementById("cm2-output").value = "";
    document.getElementById("cm2-stats").style.display = "none";
  });

  document.getElementById("cm2-go-btn").addEventListener("click", process);

  document.getElementById("cm2-clear-btn").addEventListener("click", function(){
    document.getElementById("cm2-input").value = "";
    document.getElementById("cm2-output").value = "";
    document.getElementById("cm2-stats").style.display = "none";
  });

  document.getElementById("cm2-copy-btn").addEventListener("click", function(){
    const out = document.getElementById("cm2-output").value;
    if (!out) return;
    navigator.clipboard.writeText(out).then(() => {
      const btn = document.getElementById("cm2-copy-btn");
      const orig = btn.textContent;
      btn.textContent = "Copied!";
      setTimeout(() => btn.textContent = orig, 1500);
    });
  });

  document.getElementById("cm2-upload-btn").addEventListener("click", function(){
    document.getElementById("cm2-file-input").click();
  });

  document.getElementById("cm2-file-input").addEventListener("change", function(e){
    const file = e.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function(ev) {
      document.getElementById("cm2-input").value = ev.target.result;
      process();
    };
    reader.readAsText(file);
    e.target.value = "";
  });

  document.getElementById("cm2-input").addEventListener("keydown", function(e){
    if (e.ctrlKey && e.key === "Enter") process();
  });
})();
</script>

</div>
