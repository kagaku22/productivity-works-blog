---
title: "ASCII Art Generator"
date: 2025-05-16
description: "Free online ASCII art generator. Convert text to large ASCII art banners with multiple font styles — copy to clipboard instantly, no sign-up required."
categories: ["Free Tools"]
slug: "ascii-art-generator"
ShowToc: false
cover:
  image: "/images/covers/ascii-art-generator.png"
  alt: "ASCII Art Generator"
---

<div id="aa-app">
<style>
#aa-app {
  font-family: system-ui, -apple-system, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #cbd5e1;
}
#aa-app .aa-section {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 20px 24px;
  margin-bottom: 18px;
}
#aa-app label {
  display: block;
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #94a3b8;
  margin-bottom: 6px;
}
#aa-app input[type="text"],
#aa-app select {
  width: 100%;
  box-sizing: border-box;
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 6px;
  color: #f1f5f9;
  font-size: 1rem;
  padding: 10px 12px;
  outline: none;
  transition: border-color 0.15s;
}
#aa-app input[type="text"]:focus,
#aa-app select:focus {
  border-color: #6366f1;
}
#aa-app select {
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%2394a3b8' stroke-width='2'%3E%3Cpolyline points='6 9 12 15 18 9'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 12px center;
  padding-right: 36px;
}
#aa-app .aa-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
#aa-app .aa-grid-3 {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 16px;
}
@media (max-width: 580px) {
  #aa-app .aa-grid,
  #aa-app .aa-grid-3 {
    grid-template-columns: 1fr;
  }
}
#aa-app .aa-radio-group {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}
#aa-app .aa-radio-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 6px;
  padding: 7px 14px;
  cursor: pointer;
  font-size: 0.875rem;
  color: #cbd5e1;
  transition: border-color 0.15s, background 0.15s;
  user-select: none;
}
#aa-app .aa-radio-btn input[type="radio"] {
  accent-color: #6366f1;
  width: 14px;
  height: 14px;
  flex-shrink: 0;
}
#aa-app .aa-radio-btn.aa-selected {
  border-color: #6366f1;
  background: #1e1b4b;
  color: #a5b4fc;
}
#aa-app .aa-output-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 12px;
  flex-wrap: wrap;
  gap: 8px;
}
#aa-app .aa-output-title {
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #94a3b8;
}
#aa-app .aa-char-count {
  font-size: 0.78rem;
  color: #64748b;
}
#aa-app pre#aa-output {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 6px;
  color: #a5b4fc;
  font-family: "Courier New", Courier, monospace;
  font-size: 0.62rem;
  line-height: 1.15;
  overflow-x: auto;
  padding: 16px;
  white-space: pre;
  margin: 0;
  min-height: 120px;
  tab-size: 1;
}
#aa-app .aa-btn-row {
  display: flex;
  gap: 10px;
  margin-top: 14px;
  flex-wrap: wrap;
}
#aa-app .aa-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  border: none;
  border-radius: 7px;
  cursor: pointer;
  font-size: 0.875rem;
  font-weight: 600;
  padding: 10px 20px;
  transition: opacity 0.15s, transform 0.1s;
}
#aa-app .aa-btn:active {
  transform: scale(0.97);
}
#aa-app .aa-btn-primary {
  background: #6366f1;
  color: #fff;
}
#aa-app .aa-btn-primary:hover {
  opacity: 0.88;
}
#aa-app .aa-btn-secondary {
  background: #1e293b;
  border: 1px solid #475569;
  color: #cbd5e1;
}
#aa-app .aa-btn-secondary:hover {
  border-color: #6366f1;
  color: #a5b4fc;
}
#aa-app .aa-toast {
  display: none;
  align-items: center;
  gap: 8px;
  background: #16a34a;
  color: #fff;
  border-radius: 7px;
  padding: 10px 18px;
  font-size: 0.875rem;
  font-weight: 600;
  margin-top: 12px;
}
#aa-app .aa-crosslinks {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 16px 24px;
  font-size: 0.875rem;
  color: #94a3b8;
  line-height: 2;
}
#aa-app .aa-crosslinks a {
  color: #818cf8;
  text-decoration: none;
}
#aa-app .aa-crosslinks a:hover {
  text-decoration: underline;
}
</style>

<!-- Input Section -->
<div class="aa-section">
  <label for="aa-text-input">Text to convert</label>
  <input type="text" id="aa-text-input" placeholder="Type something... e.g. HELLO" maxlength="30" autocomplete="off" spellcheck="false">
</div>

<!-- Font & Options -->
<div class="aa-section">
  <div class="aa-grid" style="margin-bottom:16px;">
    <div>
      <label for="aa-font-select">Font style</label>
      <select id="aa-font-select">
        <option value="standard">Standard — classic # blocks</option>
        <option value="banner">Banner — = and | wide style</option>
        <option value="shadow">Shadow — / and _ with depth</option>
        <option value="thin">Thin — minimalist lines</option>
        <option value="block">Block — solid █ characters</option>
      </select>
    </div>
    <div>
      <label for="aa-fill-char">Custom fill character</label>
      <input type="text" id="aa-fill-char" placeholder="Leave blank to use font default" maxlength="1" autocomplete="off">
    </div>
  </div>
  <div class="aa-grid-3">
    <div>
      <label>Character width</label>
      <div class="aa-radio-group" id="aa-width-group">
        <label class="aa-radio-btn"><input type="radio" name="aa-width" value="narrow"> Narrow</label>
        <label class="aa-radio-btn aa-selected"><input type="radio" name="aa-width" value="normal" checked> Normal</label>
        <label class="aa-radio-btn"><input type="radio" name="aa-width" value="wide"> Wide</label>
      </div>
    </div>
    <div>
      <label>Orientation</label>
      <div class="aa-radio-group" id="aa-orient-group">
        <label class="aa-radio-btn aa-selected"><input type="radio" name="aa-orient" value="horizontal" checked> Horizontal</label>
        <label class="aa-radio-btn"><input type="radio" name="aa-orient" value="vertical"> Vertical</label>
      </div>
    </div>
  </div>
</div>

<!-- Output Section -->
<div class="aa-section">
  <div class="aa-output-header">
    <span class="aa-output-title">Output</span>
    <span class="aa-char-count" id="aa-char-count">0 characters</span>
  </div>
  <pre id="aa-output">Type text above to generate ASCII art...</pre>
  <div class="aa-btn-row">
    <button class="aa-btn aa-btn-primary" id="aa-copy-btn">Copy to Clipboard</button>
    <button class="aa-btn aa-btn-secondary" id="aa-clear-btn">Clear</button>
  </div>
  <div class="aa-toast" id="aa-toast">Copied to clipboard!</div>
</div>

<!-- Cross-links -->
<div class="aa-crosslinks">
  Generate QR codes &rarr; <a href="/tools/qr-code-generator/">QR Code Generator</a><br>
  Create placeholder images &rarr; <a href="/tools/placeholder-image/">Placeholder Image Generator</a><br>
  Explore Unicode characters &rarr; <a href="/tools/unicode-character-map/">Unicode Character Map</a>
</div>

<script>
(function () {
  "use strict";

  // ─────────────────────────────────────────
  // FONT DEFINITIONS
  // Each glyph is an array of 6 strings (rows).
  // Glyphs are padded to equal width within the font.
  // ─────────────────────────────────────────

  var FONTS = {};

  // ── STANDARD (# blocks) ──────────────────
  FONTS.standard = {
    _rows: 6,
    _fill: "#",
    glyphs: {
      "A": ["  ##  "," #  # ","######","#    #","#    #","      "],
      "B": ["##### ","#    #","##### ","#    #","##### ","      "],
      "C": [" #####","#     ","#     ","#     "," #####","      "],
      "D": ["##### ","#    #","#    #","#    #","##### ","      "],
      "E": ["######","#     ","####  ","#     ","######","      "],
      "F": ["######","#     ","####  ","#     ","#     ","      "],
      "G": [" #####","#     ","#  ###","#    #"," #####","      "],
      "H": ["#    #","#    #","######","#    #","#    #","      "],
      "I": ["######","  ##  ","  ##  ","  ##  ","######","      "],
      "J": ["######","   ## ","   ## ","#  ## "," ###  ","      "],
      "K": ["#   # ","#  #  ","###   ","#  #  ","#   # ","      "],
      "L": ["#     ","#     ","#     ","#     ","######","      "],
      "M": ["#    #","##  ##","# ## #","#    #","#    #","      "],
      "N": ["#    #","##   #","# #  #","#  # #","#   ##","      "],
      "O": [" #### ","#    #","#    #","#    #"," #### ","      "],
      "P": ["##### ","#    #","##### ","#     ","#     ","      "],
      "Q": [" #### ","#    #","#  # #","#   ##"," #### ","      "],
      "R": ["##### ","#    #","##### ","#  #  ","#   # ","      "],
      "S": [" #####","#     "," #### ","     #","##### ","      "],
      "T": ["######","  ##  ","  ##  ","  ##  ","  ##  ","      "],
      "U": ["#    #","#    #","#    #","#    #"," #### ","      "],
      "V": ["#    #","#    #"," #  # "," #  # ","  ##  ","      "],
      "W": ["#    #","#    #","# ## #","##  ##","#    #","      "],
      "X": ["#    #"," #  # ","  ##  "," #  # ","#    #","      "],
      "Y": ["#    #"," #  # ","  ##  ","  ##  ","  ##  ","      "],
      "Z": ["######","    # ","  ##  "," #    ","######","      "],
      "0": [" #### ","#   ##","#  # #","## # #"," #### ","      "],
      "1": ["  ##  "," ###  ","  ##  ","  ##  ","######","      "],
      "2": [" #### ","#    #","   ## ","  ##  ","######","      "],
      "3": ["##### ","     #"," #### ","     #","##### ","      "],
      "4": ["#   # ","#   # ","######","    # ","    # ","      "],
      "5": ["######","#     ","##### ","     #","##### ","      "],
      "6": [" #### ","#     ","##### ","#    #"," #### ","      "],
      "7": ["######","    # ","   #  ","  #   ","  #   ","      "],
      "8": [" #### ","#    #"," #### ","#    #"," #### ","      "],
      "9": [" #### ","#    #"," #####","     #"," #### ","      "],
      " ": ["      ","      ","      ","      ","      ","      "],
      ".": ["      ","      ","      ","  ##  ","  ##  ","      "],
      "!": ["  ##  ","  ##  ","  ##  ","      ","  ##  ","      "],
      "?": [" #### ","#    #","   ## ","      ","  ##  ","      "],
      "-": ["      ","      ","######","      ","      ","      "],
      "_": ["      ","      ","      ","      ","######","      "],
      "+": ["      ","  ##  ","######","  ##  ","      ","      "],
      "@": [" #### ","# ## #","# ## #","#     "," #### ","      "],
      "#": [" #  # ","######"," #  # ","######"," #  # ","      "],
    }
  };

  // ── BANNER (= and |) ─────────────────────
  FONTS.banner = {
    _rows: 6,
    _fill: "=",
    glyphs: {
      "A": ["  /\\  "," /==\\ ","|====|","|    |","|    |","      "],
      "B": ["|===\\ ","|    |","|===< ","|    |","|===/ ","      "],
      "C": [" /===","|    ","|    ","|    "," \\===","      "],
      "D": ["|===\\ ","|    |","|    |","|    |","|===/ ","      "],
      "E": ["|====","|    ","|=== ","|    ","|====","      "],
      "F": ["|====","|    ","|=== ","|    ","|    ","      "],
      "G": [" /===","|    ","|  ==","|   |"," \\===","      "],
      "H": ["|    |","|    |","|====|","|    |","|    |","      "],
      "I": ["|====","  ||  ","  ||  ","  ||  ","|====","      "],
      "J": ["|====","   || ","   || ","|  || "," \\==/ ","      "],
      "K": ["|   |","|  / ","|<   ","|  \\ ","|   |","      "],
      "L": ["|    ","|    ","|    ","|    ","|====","      "],
      "M": ["|\\  /|","| \\/ |","| /\\ |","|    |","|    |","      "],
      "N": ["|\\   |","| \\  |","|  \\ |","|   \\|","|    |","      "],
      "O": [" /==\\ ","|    |","|    |","|    |"," \\==/ ","      "],
      "P": ["|===\\ ","|    |","|===/ ","|    ","| ","      "],
      "Q": [" /==\\ ","|    |","|    |","|  \\/|"," \\==\\","      "],
      "R": ["|===\\ ","|    |","|===/ ","|  \\ ","|   |","      "],
      "S": [" /===","|    "," \\==\\"," ===|","\\===/ ","      "],
      "T": ["|====","  ||  ","  ||  ","  ||  ","  ||  ","      "],
      "U": ["|    |","|    |","|    |","|    |"," \\==/ ","      "],
      "V": ["|    |","|    |"," \\  / "," \\  / ","  \\/  ","      "],
      "W": ["|    |","|    |","| \\/ |","| /\\ |","|    |","      "],
      "X": ["|    |"," \\  / ","  \\/  "," /  \\ ","|    |","      "],
      "Y": ["|    |"," \\  / ","  \\/  ","  ||  ","  ||  ","      "],
      "Z": ["|====","   /  ","  /   "," /    ","|====","      "],
      "0": [" /==\\ ","|  / |","| /  |","| \\  |"," \\==/ ","      "],
      "1": [" /|  ","  |  ","  |  ","  |  ","|====","      "],
      "2": [" /==\\ ","|    |","  ==/ "," /    ","|====","      "],
      "3": ["|=== ","     |"," ===< ","     |","|=== ","      "],
      "4": ["|   |","|   |","|===|","    |","    |","      "],
      "5": ["|====","|    ","|=== ","    |","===/ ","      "],
      "6": [" /===","|    ","|=== ","|   |"," \\==/ ","      "],
      "7": ["|====","    |","   / ","  /  "," /   ","      "],
      "8": [" /==\\ ","|    |"," \\==/ ","|    |"," \\==/ ","      "],
      "9": [" /==\\ ","|    |"," \\===","     |"," ===/ ","      "],
      " ": ["      ","      ","      ","      ","      ","      "],
      ".": ["      ","      ","      "," /\\ "," \\/ ","      "],
      "!": ["  ||  ","  ||  ","  ||  ","      "," /\\  ","      "],
      "?": [" /==\\ ","     |","  ==/ ","      ","  /\\  ","      "],
      "-": ["      ","      ","|====|","      ","      ","      "],
      "_": ["      ","      ","      ","      ","|====|","      "],
    }
  };

  // ── SHADOW (/ _ with depth) ───────────────
  FONTS.shadow = {
    _rows: 6,
    _fill: "/",
    glyphs: {
      "A": ["  _   "," /_\\  ","/ _ \\ ","/_/ \\_\\","      ","      "],
      "B": ["|_)   ","|_) _ ","| |_)","|_)_)","      ","      "],
      "C": [" ___ ","/ __|","| (__ "," \\___|","      ","      "],
      "D": ["|  \\ ","| |) ","| |/ ","__/  ","      ","      "],
      "E": ["|__ ","| __","| _|","| |_ ","      ","      "],
      "F": ["|__ ","| __","| _|","|   ","      ","      "],
      "G": [" ___ ","/ __|","| (_ ","\\____|","      ","      "],
      "H": ["|_|_|","| _ ","| |_|","      ","      ","      "],
      "I": ["|_|"," | "," | ","|_|","      ","      "],
      "J": ["  _| ","  | ","_\\ | ","\\__|","      ","      "],
      "K": ["|/ ","| <","|__\\","      ","      ","      "],
      "L": ["|   ","| __","| |_","      ","      ","      "],
      "M": ["|\\/|","_\\/_","      ","      ","      ","      "],
      "N": ["|\\ |","| \\|","      ","      ","      ","      "],
      "O": [" ___ ","/ _ \\","\\___/","      ","      ","      "],
      "P": ["|_) ","| .\\","| |  ","      ","      ","      "],
      "Q": [" ___ ","/ _ \\","\\__\\/","      ","      ","      "],
      "R": ["|_) ","| \\ ","      ","      ","      ","      "],
      "S": [" ___ ","/ __|","\\__ \\","\\___/","      ","      "],
      "T": ["|_ |","  | ","  |_|","      ","      ","      "],
      "U": ["|_|_|","  |  ","  |  ","  |_|","      ","      "],
      "V": ["\\/ ","/ \\ ","      ","      ","      ","      "],
      "W": ["\\    /","\\  / ","\\/ ","      ","      ","      "],
      "X": ["\\_/","/ \\","      ","      ","      ","      "],
      "Y": ["\\_/ "," | ","      ","      ","      ","      "],
      "Z": ["|__ ","  / ","/__\\","      ","      ","      "],
      "0": [" ___ ","/ _ \\","\\___/","      ","      ","      "],
      "1": [" /| ","  | ","  |_|","      ","      ","      "],
      "2": [" ___ ","   _/","  /  ","/___ ","      ","      "],
      "3": [" __  ","   \\ ","__  |"," \\___|","      ","      "],
      "4": ["|_| |","  _| ","      ","      ","      ","      "],
      "5": ["|___ ","/___ ","     |","\\____|","      ","      "],
      "6": [" /_| ","|___ ","| __/","\\___/","      ","      "],
      "7": ["____","   /","  / ","      ","      ","      "],
      "8": [" ___ ","/ _ \\","\\___/","      ","      ","      "],
      "9": [" ___ ","/ _ \\","\\__/|","      ","      ","      "],
      " ": ["  ","  ","  ","  ","  ","  "],
      ".": ["  "," _","(_)","      ","      ","      "],
      "!": [" | "," | ","  ","      ","      ","      "],
      "?": [" _? ","  _|","      ","      ","      ","      "],
      "-": ["    ","____","    ","      ","      ","      "],
    }
  };

  // ── THIN (minimalist) ─────────────────────
  FONTS.thin = {
    _rows: 5,
    _fill: "|",
    glyphs: {
      "A": [" /\\ "," || ","/__\\","|| ||","      "],
      "B": ["|--. ","|--< ","|--' ","      ","      "],
      "C": [" /--","| ","| ","\\--","      "],
      "D": ["|--. ","| `|","| ,|","|--' ","      "],
      "E": ["|--","|--","|","| ","      "],
      "F": ["|--","|--","|","|","      "],
      "G": [" /--","| ","| --","\\--.","      "],
      "H": ["| |","|-|","| |","      ","      "],
      "I": ["-|-"," | "," | ","-|-","      "],
      "J": [" -|"," | ","\\|","      ","      "],
      "K": ["| /","|< ","|  \\","      ","      "],
      "L": ["|  ","| ","| ","|-","      "],
      "M": ["|V|","| |","      ","      ","      "],
      "N": ["|\\|","| \\","| |","      ","      "],
      "O": [" /\\ ","|  |","\\__/","      ","      "],
      "P": ["|--.","|--'","|   ","      ","      "],
      "Q": [" /\\ ","|  |","\\/\\ ","      ","      "],
      "R": ["|--.","|--\\","| \\","      ","      "],
      "S": ["/--","\\--","__/","      ","      "],
      "T": ["-|-"," | "," | "," | ","      "],
      "U": ["| |","| |","\\|/","      ","      "],
      "V": ["| |"," V ","      ","      ","      "],
      "W": ["|   |","| | |"," \\ / ","      ","      "],
      "X": ["\\ /","/ \\","      ","      ","      "],
      "Y": ["| |"," V "," | ","      ","      "],
      "Z": ["---","  /","/--","      ","      "],
      "0": [" 0 ","/ \\","\\_/","      ","      "],
      "1": ["/| "," | "," | ","      ","      "],
      "2": ["-. ","  |","  |","'-'","      "],
      "3": ["-, "," \\","_/","      ","      "],
      "4": ["|_|"," | ","      ","      ","      "],
      "5": ["|--","'--","__/","      ","      "],
      "6": [" / ","|-. ","\\-'","      ","      "],
      "7": ["--/","  /","  ","      ","      "],
      "8": ["/\\","\\/","/\\","\\/","      "],
      "9": ["/\\","\\_"," /","      ","      "],
      " ": ["  ","  ","  ","  ","  "],
      ".": ["  "," .","  ","      ","      "],
      "!": ["|"," ","      ","      ","      "],
      "?": ["-?","  ","      ","      ","      "],
      "-": ["   ","---","   ","      ","      "],
    }
  };

  // ── BLOCK (solid █) ──────────────────────
  FONTS.block = {
    _rows: 5,
    _fill: "\u2588",
    glyphs: {
      "A": [" \u2588\u2588\u2588 ","\u2588   \u2588","\u2588\u2588\u2588\u2588\u2588","\u2588   \u2588","      "],
      "B": ["\u2588\u2588\u2588\u2588 ","\u2588   \u2588","\u2588\u2588\u2588\u2588 ","\u2588   \u2588","\u2588\u2588\u2588\u2588 "],
      "C": [" \u2588\u2588\u2588\u2588","\u2588    ","\u2588    ","\u2588    "," \u2588\u2588\u2588\u2588"],
      "D": ["\u2588\u2588\u2588  ","\u2588  \u2588\u2588","\u2588  \u2588\u2588","\u2588  \u2588\u2588","\u2588\u2588\u2588  "],
      "E": ["\u2588\u2588\u2588\u2588\u2588","\u2588    ","\u2588\u2588\u2588  ","\u2588    ","\u2588\u2588\u2588\u2588\u2588"],
      "F": ["\u2588\u2588\u2588\u2588\u2588","\u2588    ","\u2588\u2588\u2588  ","\u2588    ","\u2588    "],
      "G": [" \u2588\u2588\u2588\u2588","\u2588    ","\u2588  \u2588\u2588","\u2588   \u2588"," \u2588\u2588\u2588\u2588"],
      "H": ["\u2588   \u2588","\u2588   \u2588","\u2588\u2588\u2588\u2588\u2588","\u2588   \u2588","\u2588   \u2588"],
      "I": ["\u2588\u2588\u2588\u2588\u2588","  \u2588  ","  \u2588  ","  \u2588  ","\u2588\u2588\u2588\u2588\u2588"],
      "J": ["\u2588\u2588\u2588\u2588\u2588","   \u2588 ","   \u2588 ","\u2588  \u2588 "," \u2588\u2588  "],
      "K": ["\u2588   \u2588","\u2588  \u2588 ","\u2588\u2588\u2588  ","\u2588  \u2588 ","\u2588   \u2588"],
      "L": ["\u2588    ","\u2588    ","\u2588    ","\u2588    ","\u2588\u2588\u2588\u2588\u2588"],
      "M": ["\u2588\u2588 \u2588\u2588","\u2588 \u2588 \u2588","\u2588   \u2588","\u2588   \u2588","\u2588   \u2588"],
      "N": ["\u2588   \u2588","\u2588\u2588  \u2588","\u2588 \u2588 \u2588","\u2588  \u2588\u2588","\u2588   \u2588"],
      "O": [" \u2588\u2588\u2588 ","\u2588   \u2588","\u2588   \u2588","\u2588   \u2588"," \u2588\u2588\u2588 "],
      "P": ["\u2588\u2588\u2588\u2588 ","\u2588   \u2588","\u2588\u2588\u2588\u2588 ","\u2588    ","\u2588    "],
      "Q": [" \u2588\u2588\u2588 ","\u2588   \u2588","\u2588 \u2588 \u2588","\u2588  \u2588\u2588"," \u2588\u2588\u2588\u2588"],
      "R": ["\u2588\u2588\u2588\u2588 ","\u2588   \u2588","\u2588\u2588\u2588\u2588 ","\u2588  \u2588 ","\u2588   \u2588"],
      "S": [" \u2588\u2588\u2588\u2588","\u2588    "," \u2588\u2588\u2588 ","    \u2588","\u2588\u2588\u2588\u2588 "],
      "T": ["\u2588\u2588\u2588\u2588\u2588","  \u2588  ","  \u2588  ","  \u2588  ","  \u2588  "],
      "U": ["\u2588   \u2588","\u2588   \u2588","\u2588   \u2588","\u2588   \u2588"," \u2588\u2588\u2588 "],
      "V": ["\u2588   \u2588","\u2588   \u2588","\u2588   \u2588"," \u2588 \u2588 ","  \u2588  "],
      "W": ["\u2588   \u2588","\u2588   \u2588","\u2588 \u2588 \u2588","\u2588\u2588 \u2588\u2588","\u2588   \u2588"],
      "X": ["\u2588   \u2588"," \u2588 \u2588 ","  \u2588  "," \u2588 \u2588 ","\u2588   \u2588"],
      "Y": ["\u2588   \u2588"," \u2588 \u2588 ","  \u2588  ","  \u2588  ","  \u2588  "],
      "Z": ["\u2588\u2588\u2588\u2588\u2588","   \u2588 ","  \u2588  "," \u2588   ","\u2588\u2588\u2588\u2588\u2588"],
      "0": [" \u2588\u2588\u2588 ","\u2588  \u2588\u2588","\u2588 \u2588 \u2588","\u2588\u2588  \u2588"," \u2588\u2588\u2588 "],
      "1": ["  \u2588  "," \u2588\u2588  ","  \u2588  ","  \u2588  ","\u2588\u2588\u2588\u2588\u2588"],
      "2": [" \u2588\u2588\u2588 ","\u2588   \u2588","  \u2588\u2588 "," \u2588   ","\u2588\u2588\u2588\u2588\u2588"],
      "3": ["\u2588\u2588\u2588\u2588 ","    \u2588"," \u2588\u2588\u2588 ","    \u2588","\u2588\u2588\u2588\u2588 "],
      "4": ["\u2588   \u2588","\u2588   \u2588","\u2588\u2588\u2588\u2588\u2588","    \u2588","    \u2588"],
      "5": ["\u2588\u2588\u2588\u2588\u2588","\u2588    ","\u2588\u2588\u2588\u2588 ","    \u2588","\u2588\u2588\u2588\u2588 "],
      "6": [" \u2588\u2588\u2588\u2588","\u2588    ","\u2588\u2588\u2588\u2588 ","\u2588   \u2588"," \u2588\u2588\u2588 "],
      "7": ["\u2588\u2588\u2588\u2588\u2588","   \u2588 ","  \u2588  "," \u2588   ","\u2588    "],
      "8": [" \u2588\u2588\u2588 ","\u2588   \u2588"," \u2588\u2588\u2588 ","\u2588   \u2588"," \u2588\u2588\u2588 "],
      "9": [" \u2588\u2588\u2588 ","\u2588   \u2588"," \u2588\u2588\u2588\u2588","    \u2588"," \u2588\u2588\u2588\u2588"],
      " ": ["   ","   ","   ","   ","   "],
      ".": ["   ","   ","   "," \u2588 ","   "],
      "!": [" \u2588 "," \u2588 "," \u2588 ","   "," \u2588 "],
      "?": ["\u2588\u2588\u2588 ","  \u2588\u2588"," \u2588\u2588 ","   ","  \u2588 "],
      "-": ["   ","\u2588\u2588\u2588","   ","   ","   "],
    }
  };

  // ─────────────────────────────────────────
  // STATE
  // ─────────────────────────────────────────
  var state = {
    text: "",
    font: "standard",
    fillChar: "",
    width: "normal",
    orientation: "horizontal"
  };

  // ─────────────────────────────────────────
  // DOM REFS
  // ─────────────────────────────────────────
  var textInput   = document.getElementById("aa-text-input");
  var fontSelect  = document.getElementById("aa-font-select");
  var fillInput   = document.getElementById("aa-fill-char");
  var outputEl    = document.getElementById("aa-output");
  var charCount   = document.getElementById("aa-char-count");
  var copyBtn     = document.getElementById("aa-copy-btn");
  var clearBtn    = document.getElementById("aa-clear-btn");
  var toast       = document.getElementById("aa-toast");
  var widthGroup  = document.getElementById("aa-width-group");
  var orientGroup = document.getElementById("aa-orient-group");

  // ─────────────────────────────────────────
  // RADIO HIGHLIGHT HELPER
  // ─────────────────────────────────────────
  function syncRadioHighlight(group) {
    var labels = group.querySelectorAll(".aa-radio-btn");
    labels.forEach(function (lbl) {
      var radio = lbl.querySelector("input[type='radio']");
      if (radio && radio.checked) {
        lbl.classList.add("aa-selected");
      } else {
        lbl.classList.remove("aa-selected");
      }
    });
  }

  // ─────────────────────────────────────────
  // RENDER ENGINE
  // ─────────────────────────────────────────
  function getGlyph(fontDef, ch, customFill) {
    var key = ch.toUpperCase();
    var g = fontDef.glyphs[key] || fontDef.glyphs[" "] || ["?"];
    // Deep copy
    var rows = g.slice();

    // Optionally replace fill character
    if (customFill && customFill.length === 1) {
      var defaultFill = fontDef._fill;
      rows = rows.map(function (row) {
        return row.split("").map(function (c) {
          // Replace the "ink" chars — anything that's not space
          if (c !== " " && c === defaultFill) return customFill;
          return c;
        }).join("");
      });
    }
    return rows;
  }

  function applyWidth(rows, width) {
    if (width === "narrow") {
      // Remove one space of padding on each side
      return rows.map(function (r) { return r.replace(/^ /, "").replace(/ $/, ""); });
    } else if (width === "wide") {
      return rows.map(function (r) { return " " + r + " "; });
    }
    return rows;
  }

  function renderHorizontal(text, fontDef, customFill, width) {
    var numRows = fontDef._rows;
    var lines = [];
    for (var r = 0; r < numRows; r++) lines.push("");

    for (var i = 0; i < text.length; i++) {
      var glyph = getGlyph(fontDef, text[i], customFill);
      glyph = applyWidth(glyph, width);
      // Pad to numRows
      while (glyph.length < numRows) glyph.push("");
      for (var r2 = 0; r2 < numRows; r2++) {
        lines[r2] += glyph[r2] + " ";
      }
    }
    return lines.join("\n");
  }

  function renderVertical(text, fontDef, customFill, width) {
    var result = [];
    for (var i = 0; i < text.length; i++) {
      var glyph = getGlyph(fontDef, text[i], customFill);
      glyph = applyWidth(glyph, width);
      result.push(glyph.join("\n"));
      if (i < text.length - 1) result.push(""); // blank separator line
    }
    return result.join("\n");
  }

  function render() {
    var text = state.text;
    if (!text) {
      outputEl.textContent = "Type text above to generate ASCII art...";
      charCount.textContent = "0 characters";
      return;
    }

    var fontDef  = FONTS[state.font] || FONTS.standard;
    var fill     = state.fillChar.length === 1 ? state.fillChar : "";
    var art;

    if (state.orientation === "vertical") {
      art = renderVertical(text, fontDef, fill, state.width);
    } else {
      art = renderHorizontal(text, fontDef, fill, state.width);
    }

    outputEl.textContent = art;
    var len = art.length;
    charCount.textContent = len.toLocaleString() + " character" + (len === 1 ? "" : "s");
  }

  // ─────────────────────────────────────────
  // EVENT LISTENERS
  // ─────────────────────────────────────────
  textInput.addEventListener("input", function () {
    state.text = this.value;
    render();
  });

  fontSelect.addEventListener("change", function () {
    state.font = this.value;
    render();
  });

  fillInput.addEventListener("input", function () {
    state.fillChar = this.value.slice(-1); // keep only last char
    this.value = state.fillChar;
    render();
  });

  widthGroup.addEventListener("change", function (e) {
    if (e.target && e.target.name === "aa-width") {
      state.width = e.target.value;
      syncRadioHighlight(widthGroup);
      render();
    }
  });

  orientGroup.addEventListener("change", function (e) {
    if (e.target && e.target.name === "aa-orient") {
      state.orientation = e.target.value;
      syncRadioHighlight(orientGroup);
      render();
    }
  });

  copyBtn.addEventListener("click", function () {
    var art = outputEl.textContent;
    if (!art || art === "Type text above to generate ASCII art...") return;
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(art).then(showToast).catch(fallbackCopy);
    } else {
      fallbackCopy();
    }

    function fallbackCopy() {
      var ta = document.createElement("textarea");
      ta.value = art;
      ta.style.position = "fixed";
      ta.style.opacity = "0";
      document.body.appendChild(ta);
      ta.focus();
      ta.select();
      try { document.execCommand("copy"); showToast(); } catch (e) {}
      document.body.removeChild(ta);
    }
  });

  function showToast() {
    toast.style.display = "inline-flex";
    setTimeout(function () { toast.style.display = "none"; }, 2200);
  }

  clearBtn.addEventListener("click", function () {
    textInput.value = "";
    state.text = "";
    fillInput.value = "";
    state.fillChar = "";
    render();
    textInput.focus();
  });

  // Initial render
  render();
})();
</script>
</div>
