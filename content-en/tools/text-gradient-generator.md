---
title: "CSS Text Gradient Generator — Free Tool"
date: 2025-05-16
description: "Create beautiful CSS text gradients with live preview. Multiple color stops, angle control, and presets. Copy background-clip CSS code with one click."
categories: ["Free Tools"]
slug: "text-gradient-generator"
ShowToc: false
aliases:
  - "/tools/text-gradient/"
  - "/tools/gradient-text/"
cover:
  image: "/images/covers/text-gradient-generator.png"
  alt: "CSS Text Gradient Generator"
---

<div id="tg-app">
<style>
/* ── Scoped styles: all selectors prefixed with #tg-app ── */
#tg-app *,
#tg-app *::before,
#tg-app *::after {
  box-sizing: border-box;
}
#tg-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}

/* Preview */
#tg-app .tg-preview-wrap {
  background: #f0f2f8;
  border-radius: 14px;
  padding: 40px 24px;
  margin-bottom: 28px;
  min-height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
#tg-app #tg-preview-text {
  display: inline-block;
  background: linear-gradient(135deg, #f5af19, #f12711);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  font-size: 64px;
  font-weight: 800;
  line-height: 1.2;
  word-break: break-word;
  transition: all 0.2s ease;
}

/* Presets bar */
#tg-app .tg-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 24px;
}
#tg-app .tg-preset-btn {
  padding: 6px 14px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  font-size: 13px;
  font-weight: 600;
  color: #fff;
  transition: transform 0.15s, box-shadow 0.15s;
}
#tg-app .tg-preset-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.18);
}

/* Controls grid */
#tg-app .tg-controls {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 24px;
}
@media (max-width: 600px) {
  #tg-app .tg-controls {
    grid-template-columns: 1fr;
  }
  #tg-app #tg-preview-text {
    font-size: 40px;
  }
}
#tg-app .tg-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
#tg-app .tg-field.tg-full {
  grid-column: 1 / -1;
}
#tg-app .tg-label {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #555;
}
#tg-app .tg-field input[type="text"],
#tg-app .tg-field select {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #d4d8e8;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  transition: border-color 0.2s;
}
#tg-app .tg-field input[type="text"]:focus,
#tg-app .tg-field select:focus {
  border-color: #6c63ff;
  outline: none;
}
#tg-app .tg-field input[type="range"] {
  width: 100%;
  accent-color: #6c63ff;
}
#tg-app .tg-range-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#tg-app .tg-range-val {
  font-size: 13px;
  font-weight: 600;
  color: #6c63ff;
  min-width: 38px;
  text-align: right;
}

/* Color stops */
#tg-app .tg-stops-wrap {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
#tg-app .tg-stop-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
#tg-app .tg-color-input {
  width: 46px;
  height: 36px;
  border: 2px solid #d4d8e8;
  border-radius: 8px;
  padding: 2px;
  cursor: pointer;
  background: none;
}
#tg-app .tg-stop-label {
  font-size: 13px;
  color: #555;
  flex: 1;
}
#tg-app .tg-stop-remove {
  background: none;
  border: 1.5px solid #ddd;
  border-radius: 6px;
  width: 28px;
  height: 28px;
  cursor: pointer;
  font-size: 16px;
  color: #888;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.15s, color 0.15s;
}
#tg-app .tg-stop-remove:hover {
  background: #ffe0e0;
  color: #c0392b;
}
#tg-app .tg-add-stop-btn {
  padding: 7px 14px;
  background: #f0f2f8;
  border: 1.5px dashed #aab;
  border-radius: 8px;
  cursor: pointer;
  font-size: 13px;
  color: #666;
  transition: background 0.15s;
  width: fit-content;
}
#tg-app .tg-add-stop-btn:hover {
  background: #e4e8f8;
}

/* Text-align buttons */
#tg-app .tg-align-group {
  display: flex;
  gap: 6px;
}
#tg-app .tg-align-btn {
  flex: 1;
  padding: 7px;
  border: 1.5px solid #d4d8e8;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 16px;
  transition: background 0.15s, border-color 0.15s;
}
#tg-app .tg-align-btn.active,
#tg-app .tg-align-btn:hover {
  background: #6c63ff;
  border-color: #6c63ff;
  color: #fff;
}

/* Gradient type */
#tg-app .tg-type-group {
  display: flex;
  gap: 8px;
}
#tg-app .tg-type-btn {
  flex: 1;
  padding: 8px;
  border: 1.5px solid #d4d8e8;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 13px;
  font-weight: 600;
  transition: background 0.15s, border-color 0.15s;
}
#tg-app .tg-type-btn.active {
  background: #6c63ff;
  border-color: #6c63ff;
  color: #fff;
}

/* CSS Output */
#tg-app .tg-output-wrap {
  background: #1a1a2e;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
  position: relative;
}
#tg-app .tg-output-label {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #8888bb;
  margin-bottom: 10px;
}
#tg-app #tg-css-output {
  font-family: "JetBrains Mono", "Fira Code", Consolas, monospace;
  font-size: 13px;
  line-height: 1.7;
  color: #a8e6cf;
  white-space: pre;
  overflow-x: auto;
  background: none;
  border: none;
  width: 100%;
  resize: none;
}
#tg-app .tg-copy-btn {
  position: absolute;
  top: 16px;
  right: 16px;
  padding: 7px 16px;
  background: #6c63ff;
  color: #fff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 13px;
  font-weight: 600;
  transition: background 0.2s, transform 0.15s;
}
#tg-app .tg-copy-btn:hover {
  background: #5548e0;
  transform: translateY(-1px);
}
#tg-app .tg-copy-btn.copied {
  background: #27ae60;
}

/* Section heading */
#tg-app .tg-section-title {
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  color: #888;
  margin-bottom: 10px;
}
#tg-app .tg-card {
  background: #fff;
  border: 1.5px solid #e4e8f4;
  border-radius: 12px;
  padding: 18px;
  margin-bottom: 20px;
}
</style>

<!-- Preview -->
<div class="tg-preview-wrap">
  <span id="tg-preview-text">Gradient Text</span>
</div>

<!-- Presets -->
<div class="tg-section-title">Presets</div>
<div class="tg-presets" id="tg-presets"></div>

<!-- Controls -->
<div class="tg-card">
  <div class="tg-controls">

    <!-- Text input -->
    <div class="tg-field tg-full">
      <span class="tg-label">Preview Text</span>
      <input type="text" id="tg-text-input" value="Gradient Text" placeholder="Type your text..." maxlength="120">
    </div>

    <!-- Gradient type -->
    <div class="tg-field">
      <span class="tg-label">Gradient Type</span>
      <div class="tg-type-group">
        <button class="tg-type-btn active" data-type="linear">Linear</button>
        <button class="tg-type-btn" data-type="radial">Radial</button>
      </div>
    </div>

    <!-- Angle (linear) -->
    <div class="tg-field" id="tg-angle-field">
      <span class="tg-label">Angle</span>
      <div class="tg-range-row">
        <input type="range" id="tg-angle" min="0" max="360" value="135">
        <span class="tg-range-val" id="tg-angle-val">135deg</span>
      </div>
    </div>

    <!-- Color stops -->
    <div class="tg-field tg-full">
      <span class="tg-label">Color Stops (2–4)</span>
      <div class="tg-stops-wrap" id="tg-stops-wrap"></div>
      <button class="tg-add-stop-btn" id="tg-add-stop">+ Add Color Stop</button>
    </div>

    <!-- Font size -->
    <div class="tg-field">
      <span class="tg-label">Font Size</span>
      <div class="tg-range-row">
        <input type="range" id="tg-font-size" min="24" max="120" value="64">
        <span class="tg-range-val" id="tg-font-size-val">64px</span>
      </div>
    </div>

    <!-- Font weight -->
    <div class="tg-field">
      <span class="tg-label">Font Weight</span>
      <select id="tg-font-weight">
        <option value="300">300 — Light</option>
        <option value="400">400 — Regular</option>
        <option value="600">600 — Semibold</option>
        <option value="700">700 — Bold</option>
        <option value="800" selected>800 — Extrabold</option>
        <option value="900">900 — Black</option>
      </select>
    </div>

    <!-- Text align -->
    <div class="tg-field tg-full">
      <span class="tg-label">Text Align</span>
      <div class="tg-align-group" id="tg-align-group">
        <button class="tg-align-btn active" data-align="left" title="Left">&#9664;</button>
        <button class="tg-align-btn" data-align="center" title="Center">&#9644;</button>
        <button class="tg-align-btn" data-align="right" title="Right">&#9654;</button>
      </div>
    </div>

  </div>
</div>

<!-- CSS Output -->
<div class="tg-output-wrap">
  <div class="tg-output-label">Generated CSS</div>
  <textarea id="tg-css-output" rows="8" readonly spellcheck="false"></textarea>
  <button class="tg-copy-btn" id="tg-copy-btn">Copy CSS</button>
</div>

<script>
(function () {
  /* ── State ── */
  const state = {
    text: "Gradient Text",
    type: "linear",
    angle: 135,
    stops: [
      { color: "#f5af19" },
      { color: "#f12711" }
    ],
    fontSize: 64,
    fontWeight: "800",
    textAlign: "left"
  };

  /* ── Presets ── */
  const PRESETS = [
    { name: "Sunset",  stops: ["#f5af19","#f12711"],        angle: 135, type: "linear" },
    { name: "Ocean",   stops: ["#43cea2","#185a9d"],        angle: 120, type: "linear" },
    { name: "Forest",  stops: ["#56ab2f","#a8e063"],        angle: 150, type: "linear" },
    { name: "Fire",    stops: ["#ff4e50","#f9d423"],        angle: 90,  type: "linear" },
    { name: "Neon",    stops: ["#12c2e9","#c471ed","#f64f59"], angle: 120, type: "linear" },
    { name: "Pastel",  stops: ["#f8cdda","#1d2b64"],        angle: 100, type: "linear" },
    { name: "Gold",    stops: ["#f7971e","#ffd200"],        angle: 110, type: "linear" }
  ];

  /* ── DOM refs ── */
  const previewEl   = document.getElementById("tg-preview-text");
  const textInput   = document.getElementById("tg-text-input");
  const angleSlider = document.getElementById("tg-angle");
  const angleVal    = document.getElementById("tg-angle-val");
  const angleField  = document.getElementById("tg-angle-field");
  const fsSlider    = document.getElementById("tg-font-size");
  const fsVal       = document.getElementById("tg-font-size-val");
  const fwSelect    = document.getElementById("tg-font-weight");
  const stopsWrap   = document.getElementById("tg-stops-wrap");
  const addStopBtn  = document.getElementById("tg-add-stop");
  const cssOutput   = document.getElementById("tg-css-output");
  const copyBtn     = document.getElementById("tg-copy-btn");
  const presetsWrap = document.getElementById("tg-presets");
  const alignGroup  = document.getElementById("tg-align-group");

  /* ── Render helpers ── */
  function gradientCSS() {
    const colors = state.stops.map(s => s.color).join(", ");
    if (state.type === "radial") {
      return `radial-gradient(circle, ${colors})`;
    }
    return `linear-gradient(${state.angle}deg, ${colors})`;
  }

  function buildCSS() {
    const g = gradientCSS();
    return `.gradient-text {
  background: ${g};
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  font-size: ${state.fontSize}px;
  font-weight: ${state.fontWeight};
  text-align: ${state.textAlign};
  display: inline-block;
}`;
  }

  function applyPreview() {
    const g = gradientCSS();
    previewEl.style.backgroundImage     = g;
    previewEl.style.webkitBackgroundClip = "text";
    previewEl.style.backgroundClip      = "text";
    previewEl.style.webkitTextFillColor  = "transparent";
    previewEl.style.color               = "transparent";
    previewEl.style.fontSize            = state.fontSize + "px";
    previewEl.style.fontWeight          = state.fontWeight;
    previewEl.style.textAlign           = state.textAlign;
    previewEl.textContent               = state.text || "Gradient Text";
    cssOutput.value                     = buildCSS();
  }

  /* ── Stop rows ── */
  function renderStops() {
    stopsWrap.innerHTML = "";
    state.stops.forEach(function (stop, i) {
      const row = document.createElement("div");
      row.className = "tg-stop-row";

      const colorInput = document.createElement("input");
      colorInput.type  = "color";
      colorInput.className = "tg-color-input";
      colorInput.value = stop.color;
      colorInput.addEventListener("input", function () {
        state.stops[i].color = this.value;
        applyPreview();
      });

      const lbl = document.createElement("span");
      lbl.className = "tg-stop-label";
      lbl.textContent = "Stop " + (i + 1);

      const removeBtn = document.createElement("button");
      removeBtn.className = "tg-stop-remove";
      removeBtn.textContent = "×";
      removeBtn.title = "Remove stop";
      removeBtn.disabled = state.stops.length <= 2;
      removeBtn.style.opacity = state.stops.length <= 2 ? "0.3" : "1";
      removeBtn.addEventListener("click", function () {
        if (state.stops.length > 2) {
          state.stops.splice(i, 1);
          renderStops();
          applyPreview();
        }
      });

      row.appendChild(colorInput);
      row.appendChild(lbl);
      row.appendChild(removeBtn);
      stopsWrap.appendChild(row);
    });

    addStopBtn.style.display = state.stops.length >= 4 ? "none" : "flex";
  }

  /* ── Presets ── */
  const PRESET_GRADIENTS = {
    Sunset: "linear-gradient(135deg,#f5af19,#f12711)",
    Ocean:  "linear-gradient(120deg,#43cea2,#185a9d)",
    Forest: "linear-gradient(150deg,#56ab2f,#a8e063)",
    Fire:   "linear-gradient(90deg,#ff4e50,#f9d423)",
    Neon:   "linear-gradient(120deg,#12c2e9,#c471ed,#f64f59)",
    Pastel: "linear-gradient(100deg,#f8cdda,#1d2b64)",
    Gold:   "linear-gradient(110deg,#f7971e,#ffd200)"
  };

  PRESETS.forEach(function (preset) {
    const btn = document.createElement("button");
    btn.className = "tg-preset-btn";
    btn.textContent = preset.name;
    btn.style.backgroundImage = PRESET_GRADIENTS[preset.name];
    btn.addEventListener("click", function () {
      state.type  = preset.type;
      state.angle = preset.angle;
      state.stops = preset.stops.map(function (c) { return { color: c }; });
      angleSlider.value = preset.angle;
      angleVal.textContent = preset.angle + "deg";
      document.querySelectorAll("#tg-app .tg-type-btn").forEach(function (b) {
        b.classList.toggle("active", b.dataset.type === preset.type);
      });
      angleField.style.display = preset.type === "radial" ? "none" : "";
      renderStops();
      applyPreview();
    });
    presetsWrap.appendChild(btn);
  });

  /* ── Event: text input ── */
  textInput.addEventListener("input", function () {
    state.text = this.value;
    applyPreview();
  });

  /* ── Event: angle ── */
  angleSlider.addEventListener("input", function () {
    state.angle = parseInt(this.value, 10);
    angleVal.textContent = state.angle + "deg";
    applyPreview();
  });

  /* ── Event: font size ── */
  fsSlider.addEventListener("input", function () {
    state.fontSize = parseInt(this.value, 10);
    fsVal.textContent = state.fontSize + "px";
    applyPreview();
  });

  /* ── Event: font weight ── */
  fwSelect.addEventListener("change", function () {
    state.fontWeight = this.value;
    applyPreview();
  });

  /* ── Event: gradient type ── */
  document.querySelectorAll("#tg-app .tg-type-btn").forEach(function (btn) {
    btn.addEventListener("click", function () {
      state.type = this.dataset.type;
      document.querySelectorAll("#tg-app .tg-type-btn").forEach(function (b) {
        b.classList.toggle("active", b === btn);
      });
      angleField.style.display = state.type === "radial" ? "none" : "";
      applyPreview();
    });
  });

  /* ── Event: text align ── */
  alignGroup.querySelectorAll(".tg-align-btn").forEach(function (btn) {
    btn.addEventListener("click", function () {
      state.textAlign = this.dataset.align;
      alignGroup.querySelectorAll(".tg-align-btn").forEach(function (b) {
        b.classList.toggle("active", b === btn);
      });
      applyPreview();
    });
  });

  /* ── Event: add stop ── */
  addStopBtn.addEventListener("click", function () {
    if (state.stops.length < 4) {
      state.stops.push({ color: "#ffffff" });
      renderStops();
      applyPreview();
    }
  });

  /* ── Event: copy CSS ── */
  copyBtn.addEventListener("click", function () {
    navigator.clipboard.writeText(cssOutput.value).then(function () {
      copyBtn.textContent = "Copied!";
      copyBtn.classList.add("copied");
      setTimeout(function () {
        copyBtn.textContent = "Copy CSS";
        copyBtn.classList.remove("copied");
      }, 2000);
    }).catch(function () {
      cssOutput.select();
      document.execCommand("copy");
      copyBtn.textContent = "Copied!";
      setTimeout(function () { copyBtn.textContent = "Copy CSS"; }, 2000);
    });
  });

  /* ── Init ── */
  renderStops();
  applyPreview();
})();
</script>
</div>

---

## How It Works

CSS text gradients use the **`background-clip: text`** technique:

1. Apply a gradient to the element's `background` property.
2. Clip the background to the text shape with `-webkit-background-clip: text` and `background-clip: text`.
3. Make the text itself transparent with `-webkit-text-fill-color: transparent`.

The result is gradient-painted characters with no SVG or images required — pure CSS.

---

## Browser Compatibility

| Browser | Support |
|---|---|
| Chrome / Edge | Full |
| Firefox | Full (Firefox 122+) |
| Safari | Full (`-webkit-` prefix required) |
| iOS Safari | Full |

---

## Tips for Best Results

- **High contrast presets** (Sunset, Fire, Neon) work best on dark backgrounds.
- **Pastel gradients** suit light-mode body text at large sizes.
- Always include **both** `-webkit-background-clip: text` and `background-clip: text` for cross-browser safety.
- Add `display: inline-block` so the gradient clips correctly; `block` elements expand to full width and may show extra gradient area.

---

### Related Tools

> Build background gradients → [CSS Gradient Generator](/tools/css-gradient-generator/)

> Generate color palettes → [Color Palette Generator](/tools/color-palette-generator/)

> Create box shadows → [CSS Box Shadow Generator](/tools/box-shadow-generator/)
