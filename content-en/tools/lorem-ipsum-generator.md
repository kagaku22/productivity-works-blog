---
title: "Lorem Ipsum Generator - Free Placeholder Text Tool"
date: 2025-05-16
description: "Generate Lorem Ipsum placeholder text instantly. Choose paragraphs, sentences, or words. Classic, Hipster, or Corporate Ipsum styles. HTML output, copy to clipboard."
categories: ["Free Tools"]
tags: ["lorem ipsum", "placeholder text", "dummy text", "text generator", "web design"]
slug: "lorem-ipsum-generator"
aliases: ["/tools/lorem-ipsum-generator/", "/tools/lorem-ipsum-generator/"]
cover:
  image: "/images/covers/lorem-ipsum-generator.png"
  alt: "Lorem Ipsum Generator"
ShowToc: false
---

<div id="lorem-app">

<style>
#lorem-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1c1917;
}

#lorem-app * {
  box-sizing: border-box;
}

/* Controls panel */
#lorem-app .la-controls {
  background: #fff7ed;
  border: 2px solid #fed7aa;
  border-radius: 14px;
  padding: 24px;
  margin-bottom: 24px;
}

#lorem-app .la-row {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  align-items: flex-end;
  margin-bottom: 16px;
}

#lorem-app .la-row:last-child {
  margin-bottom: 0;
}

#lorem-app .la-field {
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex: 1;
  min-width: 150px;
}

#lorem-app .la-field label {
  font-size: 0.82rem;
  font-weight: 600;
  color: #9a3412;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

#lorem-app select,
#lorem-app input[type="number"] {
  height: 42px;
  padding: 0 12px;
  border: 2px solid #fed7aa;
  border-radius: 8px;
  font-size: 0.95rem;
  background: #fff;
  color: #1c1917;
  outline: none;
  transition: border-color 0.2s;
}

#lorem-app select:focus,
#lorem-app input[type="number"]:focus {
  border-color: #ea580c;
}

#lorem-app input[type="number"] {
  width: 100px;
}

/* Checkbox row */
#lorem-app .la-check-row {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

#lorem-app .la-check-row label {
  font-size: 0.92rem;
  color: #44403c;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
}

#lorem-app input[type="checkbox"] {
  width: 18px;
  height: 18px;
  accent-color: #ea580c;
  cursor: pointer;
}

/* Generate button */
#lorem-app .la-btn-generate {
  background: #ea580c;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0 28px;
  height: 42px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  white-space: nowrap;
}

#lorem-app .la-btn-generate:hover {
  background: #c2410c;
}

#lorem-app .la-btn-generate:active {
  transform: scale(0.97);
}

/* Stats bar */
#lorem-app .la-stats {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

#lorem-app .la-stat {
  background: #fff7ed;
  border: 1px solid #fed7aa;
  border-radius: 8px;
  padding: 8px 16px;
  font-size: 0.88rem;
  color: #7c2d12;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

#lorem-app .la-stat strong {
  font-size: 1.3rem;
  font-weight: 700;
  color: #ea580c;
}

/* Output tabs */
#lorem-app .la-tabs {
  display: flex;
  gap: 0;
  margin-bottom: 0;
  border-bottom: 2px solid #fed7aa;
}

#lorem-app .la-tab {
  padding: 10px 20px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  border: 2px solid transparent;
  border-bottom: none;
  border-radius: 8px 8px 0 0;
  background: #fff7ed;
  color: #9a3412;
  margin-bottom: -2px;
  transition: background 0.15s;
}

#lorem-app .la-tab.active {
  background: #fff;
  border-color: #fed7aa;
  border-bottom-color: #fff;
  color: #ea580c;
}

/* Output panels */
#lorem-app .la-output-wrap {
  border: 2px solid #fed7aa;
  border-top: none;
  border-radius: 0 0 12px 12px;
  background: #fff;
  padding: 20px;
  margin-bottom: 16px;
}

#lorem-app .la-panel {
  display: none;
}

#lorem-app .la-panel.active {
  display: block;
}

/* Preview paragraphs */
#lorem-app .la-preview p {
  margin: 0 0 1.1em 0;
  line-height: 1.75;
  color: #44403c;
  font-size: 0.97rem;
}

#lorem-app .la-preview p:last-child {
  margin-bottom: 0;
}

/* HTML code area */
#lorem-app .la-code {
  width: 100%;
  min-height: 180px;
  padding: 14px;
  font-family: "SF Mono", "Fira Code", "Consolas", monospace;
  font-size: 0.82rem;
  line-height: 1.6;
  border: 2px solid #e7e5e4;
  border-radius: 8px;
  background: #fafaf9;
  color: #1c1917;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
}

#lorem-app .la-code:focus {
  border-color: #ea580c;
}

/* Copy buttons */
#lorem-app .la-copy-row {
  display: flex;
  justify-content: flex-end;
  margin-top: 12px;
}

#lorem-app .la-btn-copy {
  background: #fff;
  color: #ea580c;
  border: 2px solid #ea580c;
  border-radius: 8px;
  padding: 8px 20px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
  display: flex;
  align-items: center;
  gap: 6px;
}

#lorem-app .la-btn-copy:hover {
  background: #ea580c;
  color: #fff;
}

#lorem-app .la-btn-copy.copied {
  background: #16a34a;
  border-color: #16a34a;
  color: #fff;
}

/* Empty state */
#lorem-app .la-empty {
  text-align: center;
  padding: 48px 20px;
  color: #a8a29e;
  font-size: 1rem;
}

#lorem-app .la-empty-icon {
  font-size: 2.5rem;
  margin-bottom: 12px;
}

/* Responsive */
@media (max-width: 600px) {
  #lorem-app .la-controls {
    padding: 16px;
  }
  #lorem-app .la-row {
    gap: 12px;
  }
  #lorem-app .la-field {
    min-width: 120px;
  }
  #lorem-app input[type="number"] {
    width: 80px;
  }
  #lorem-app .la-tab {
    padding: 8px 14px;
    font-size: 0.82rem;
  }
}
</style>

<!-- Controls -->
<div class="la-controls">
  <div class="la-row">
    <div class="la-field">
      <label for="la-type">Generate</label>
      <select id="la-type">
        <option value="paragraphs">Paragraphs</option>
        <option value="sentences">Sentences</option>
        <option value="words">Words</option>
      </select>
    </div>
    <div class="la-field">
      <label for="la-count">Count (1–50)</label>
      <input type="number" id="la-count" value="3" min="1" max="50">
    </div>
    <div class="la-field">
      <label for="la-style">Text Style</label>
      <select id="la-style">
        <option value="classic">Classic Lorem Ipsum</option>
        <option value="hipster">Hipster Ipsum</option>
        <option value="corporate">Corporate Ipsum</option>
      </select>
    </div>
    <button class="la-btn-generate" onclick="loremGenerate()">Generate</button>
  </div>
  <div class="la-row">
    <div class="la-check-row">
      <label>
        <input type="checkbox" id="la-classic-start" checked>
        Start with "Lorem ipsum dolor sit amet..."
      </label>
    </div>
  </div>
</div>

<!-- Stats -->
<div class="la-stats">
  <div class="la-stat"><strong id="la-stat-para">—</strong>Paragraphs</div>
  <div class="la-stat"><strong id="la-stat-sent">—</strong>Sentences</div>
  <div class="la-stat"><strong id="la-stat-words">—</strong>Words</div>
  <div class="la-stat"><strong id="la-stat-chars">—</strong>Characters</div>
</div>

<!-- Output -->
<div class="la-tabs">
  <div class="la-tab active" onclick="loremSwitchTab('preview', this)">Preview</div>
  <div class="la-tab" onclick="loremSwitchTab('html', this)">HTML Output</div>
</div>

<div class="la-output-wrap">
  <div id="la-panel-preview" class="la-panel active">
    <div class="la-preview" id="la-preview-content">
      <div class="la-empty">
        <div class="la-empty-icon">&#9998;</div>
        <div>Click <strong>Generate</strong> to create placeholder text</div>
      </div>
    </div>
    <div class="la-copy-row">
      <button class="la-btn-copy" id="la-copy-plain" onclick="loremCopyPlain()">
        &#128203; Copy Plain Text
      </button>
    </div>
  </div>

  <div id="la-panel-html" class="la-panel">
    <textarea class="la-code" id="la-html-content" readonly placeholder="HTML output will appear here..."></textarea>
    <div class="la-copy-row">
      <button class="la-btn-copy" id="la-copy-html" onclick="loremCopyHtml()">
        &#128203; Copy HTML
      </button>
    </div>
  </div>
</div>

<script>
(function() {

// ── DATA ──────────────────────────────────────────────────────────────────────

const DATA = {
  classic: {
    words: [
      "lorem","ipsum","dolor","sit","amet","consectetur","adipiscing","elit",
      "sed","do","eiusmod","tempor","incididunt","ut","labore","et","dolore",
      "magna","aliqua","enim","ad","minim","veniam","quis","nostrud","exercitation",
      "ullamco","laboris","nisi","aliquip","ex","ea","commodo","consequat","duis",
      "aute","irure","in","reprehenderit","voluptate","velit","esse","cillum",
      "fugiat","nulla","pariatur","excepteur","sint","occaecat","cupidatat","non",
      "proident","sunt","culpa","qui","officia","deserunt","mollit","anim","id","est",
      "laborum","perspiciatis","unde","omnis","iste","natus","error","accusantium",
      "doloremque","laudantium","totam","rem","aperiam","eaque","ipsa","quae","ab",
      "inventore","veritatis","quasi","architecto","beatae","vitae","dicta","explicabo",
      "nemo","voluptatem","quia","voluptas","aspernatur","odit","aut","fugit","magni",
      "dolores","ratione","sequi","nesciunt","neque","porro","quisquam","dolorem"
    ],
    opener: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
  },
  hipster: {
    words: [
      "artisan","craft","aesthetic","curated","bespoke","authentic","sustainable",
      "kombucha","vinyl","gastropub","fixie","letterpress","kale","synth","flannel",
      "activated","charcoal","ethical","forage","lo-fi","normcore","poke","prism",
      "raclette","seitan","shaman","skateboard","stumptown","taiyaki","taxidermy",
      "tousled","typewriter","unicorn","vaporwave","venmo","vexillologist","wayfarers",
      "williamsburg","yuccie","occupy","heirloom","gochujang","gluten-free","farm-to-table",
      "direct","trade","cold-pressed","single-origin","pour-over","cold-brew","lomo",
      "chicharrones","microdosing","pabst","tattooed","shoreditch","poutine","tbh",
      "meggings","ugh","schlitz","retro","meh","wolf","cardigan","trust-fund","selfies"
    ],
    opener: "Artisan sustainable craft aesthetic curated bespoke kombucha vinyl gastropub fixie letterpress kale chips synth."
  },
  corporate: {
    words: [
      "synergy","leverage","paradigm","pivot","disruptive","scalable","agile","robust",
      "innovative","streamline","holistic","proactive","actionable","deliverable",
      "bandwidth","ecosystem","stakeholder","value-add","end-to-end","best-practice",
      "solution","core-competency","drill-down","empower","granular","ideation",
      "incentivize","low-hanging-fruit","mindshare","move-the-needle","onboarding",
      "repurpose","rightsizing","ROI","run-it-up-the-flagpole","seamless","silo",
      "takeaway","think-outside-the-box","touch-base","utilize","visibility","win-win",
      "circle-back","boil-the-ocean","deep-dive","double-click","growth-hacking",
      "hyperlocal","impactful","in-the-weeds","key-performance","milestone","north-star",
      "organic-growth","pain-point","ramp-up","resourceful","robust-pipeline","runway"
    ],
    opener: "Synergy leverage paradigm pivot disruptive scalable agile robust innovative streamline holistic proactive actionable deliverables."
  }
};

// ── STATE ─────────────────────────────────────────────────────────────────────

let currentParagraphs = [];

// ── HELPERS ───────────────────────────────────────────────────────────────────

function randInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function pickRandom(arr) {
  return arr[Math.floor(Math.random() * arr.length)];
}

function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

function buildSentence(words, minW, maxW) {
  const len = randInt(minW, maxW);
  let parts = [];
  for (let i = 0; i < len; i++) {
    parts.push(pickRandom(words));
  }
  return capitalize(parts.join(" ")) + ".";
}

function buildParagraph(words, sentMin, sentMax, wordMin, wordMax) {
  const n = randInt(sentMin, sentMax);
  let sentences = [];
  for (let i = 0; i < n; i++) {
    sentences.push(buildSentence(words, wordMin, wordMax));
  }
  return sentences.join(" ");
}

// ── GENERATION ────────────────────────────────────────────────────────────────

function generateText(type, count, style, useOpener) {
  const d = DATA[style];
  const words = d.words;
  let paragraphs = [];

  if (type === "paragraphs") {
    for (let i = 0; i < count; i++) {
      paragraphs.push(buildParagraph(words, 4, 8, 8, 18));
    }
  } else if (type === "sentences") {
    let sentences = [];
    for (let i = 0; i < count; i++) {
      sentences.push(buildSentence(words, 8, 18));
    }
    // Group into paragraphs of ~3 sentences
    const perPara = 3;
    for (let i = 0; i < sentences.length; i += perPara) {
      paragraphs.push(sentences.slice(i, i + perPara).join(" "));
    }
  } else if (type === "words") {
    let chosen = [];
    for (let i = 0; i < count; i++) {
      chosen.push(pickRandom(words));
    }
    paragraphs.push(capitalize(chosen.join(" ")) + ".");
  }

  if (useOpener && paragraphs.length > 0) {
    // Replace first sentence of first paragraph with the opener
    paragraphs[0] = d.opener + " " + paragraphs[0];
  }

  return paragraphs;
}

// ── STATS ─────────────────────────────────────────────────────────────────────

function updateStats(paragraphs) {
  const fullText = paragraphs.join("\n\n");
  // Count sentences (rough: split on ". " or "." at end)
  const sentCount = (fullText.match(/[.!?]+/g) || []).length;
  const wordCount = fullText.trim().split(/\s+/).filter(Boolean).length;
  const charCount = fullText.length;
  const paraCount = paragraphs.length;

  document.getElementById("la-stat-para").textContent = paraCount;
  document.getElementById("la-stat-sent").textContent = sentCount;
  document.getElementById("la-stat-words").textContent = wordCount.toLocaleString();
  document.getElementById("la-stat-chars").textContent = charCount.toLocaleString();
}

// ── RENDER ────────────────────────────────────────────────────────────────────

function renderPreview(paragraphs) {
  const container = document.getElementById("la-preview-content");
  if (!paragraphs.length) {
    container.innerHTML = '<div class="la-empty"><div class="la-empty-icon">&#9998;</div><div>Click <strong>Generate</strong> to create placeholder text</div></div>';
    return;
  }
  container.innerHTML = paragraphs
    .map(p => `<p>${escapeHtml(p)}</p>`)
    .join("");
}

function renderHtml(paragraphs) {
  const ta = document.getElementById("la-html-content");
  ta.value = paragraphs.map(p => `<p>${p}</p>`).join("\n");
}

function escapeHtml(str) {
  return str
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;");
}

// ── TABS ──────────────────────────────────────────────────────────────────────

window.loremSwitchTab = function(tab, el) {
  document.querySelectorAll("#lorem-app .la-tab").forEach(t => t.classList.remove("active"));
  document.querySelectorAll("#lorem-app .la-panel").forEach(p => p.classList.remove("active"));
  el.classList.add("active");
  document.getElementById("la-panel-" + tab).classList.add("active");
};

// ── GENERATE ──────────────────────────────────────────────────────────────────

window.loremGenerate = function() {
  const type = document.getElementById("la-type").value;
  const rawCount = parseInt(document.getElementById("la-count").value, 10);
  const count = Math.min(50, Math.max(1, isNaN(rawCount) ? 3 : rawCount));
  const style = document.getElementById("la-style").value;
  const useOpener = document.getElementById("la-classic-start").checked;

  currentParagraphs = generateText(type, count, style, useOpener);
  renderPreview(currentParagraphs);
  renderHtml(currentParagraphs);
  updateStats(currentParagraphs);
};

// ── COPY ──────────────────────────────────────────────────────────────────────

function flashCopied(btnId) {
  const btn = document.getElementById(btnId);
  const orig = btn.innerHTML;
  btn.classList.add("copied");
  btn.innerHTML = "&#10003; Copied!";
  setTimeout(() => {
    btn.classList.remove("copied");
    btn.innerHTML = orig;
  }, 2000);
}

window.loremCopyPlain = function() {
  if (!currentParagraphs.length) return;
  navigator.clipboard.writeText(currentParagraphs.join("\n\n")).then(() => {
    flashCopied("la-copy-plain");
  }).catch(() => {
    const ta = document.createElement("textarea");
    ta.value = currentParagraphs.join("\n\n");
    document.body.appendChild(ta);
    ta.select();
    document.execCommand("copy");
    document.body.removeChild(ta);
    flashCopied("la-copy-plain");
  });
};

window.loremCopyHtml = function() {
  const val = document.getElementById("la-html-content").value;
  if (!val) return;
  navigator.clipboard.writeText(val).then(() => {
    flashCopied("la-copy-html");
  }).catch(() => {
    const ta = document.createElement("textarea");
    ta.value = val;
    document.body.appendChild(ta);
    ta.select();
    document.execCommand("copy");
    document.body.removeChild(ta);
    flashCopied("la-copy-html");
  });
};

// ── INIT ──────────────────────────────────────────────────────────────────────

// Auto-generate on load with defaults
loremGenerate();

})();
</script>

</div>

---

**Related:** Count your real text with our [Word Counter](/tools/word-counter/)
