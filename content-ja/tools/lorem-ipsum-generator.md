---
title: "ダミーテキスト生成ツール - Lorem Ipsum 無料ジェネレーター"
date: 2025-05-16
description: "Webデザイン・印刷物のダミーテキストを瞬時に生成。段落・文・単語数を指定可能。Lorem Ipsum、日本語ダミー文など複数スタイル対応。HTMLコピー機能つき。"
categories: ["無料ツール"]
tags: ["ダミーテキスト", "lorem ipsum", "仮テキスト", "プレースホルダー", "Webデザイン"]
slug: "lorem-ipsum-generator"
aliases: ["/ja/tools/lorem-ipsum-generator/", "/ja/tools/lorem-ipsum-generator/"]
cover:
  image: "/images/covers/lorem-ipsum-generator-ja.png"
  alt: "ダミーテキスト生成ツール"
ShowToc: false
---

<div id="lorem-app">

<style>
#lorem-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
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
  min-width: 140px;
}

#lorem-app .la-field label {
  font-size: 0.8rem;
  font-weight: 700;
  color: #9a3412;
  text-transform: uppercase;
  letter-spacing: 0.04em;
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
  width: 90px;
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
  font-size: 0.85rem;
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
  line-height: 1.9;
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
    width: 76px;
  }
  #lorem-app .la-tab {
    padding: 8px 12px;
    font-size: 0.82rem;
  }
}
</style>

<!-- Controls -->
<div class="la-controls">
  <div class="la-row">
    <div class="la-field">
      <label for="la-type">生成単位</label>
      <select id="la-type">
        <option value="paragraphs">段落</option>
        <option value="sentences">文</option>
        <option value="words">単語</option>
      </select>
    </div>
    <div class="la-field">
      <label for="la-count">件数（1〜50）</label>
      <input type="number" id="la-count" value="3" min="1" max="50">
    </div>
    <div class="la-field">
      <label for="la-style">テキストスタイル</label>
      <select id="la-style">
        <option value="classic">クラシック Lorem Ipsum</option>
        <option value="hipster">ヒップスター Ipsum</option>
        <option value="corporate">コーポレート Ipsum</option>
        <option value="japanese">ダミーテキスト（日本語）</option>
      </select>
    </div>
    <button class="la-btn-generate" onclick="loremGenerate()">生成する</button>
  </div>
  <div class="la-row">
    <div class="la-check-row">
      <label>
        <input type="checkbox" id="la-classic-start" checked>
        「Lorem ipsum dolor sit amet...」で始める
      </label>
    </div>
  </div>
</div>

<!-- Stats -->
<div class="la-stats">
  <div class="la-stat"><strong id="la-stat-para">—</strong>段落</div>
  <div class="la-stat"><strong id="la-stat-sent">—</strong>文</div>
  <div class="la-stat"><strong id="la-stat-words">—</strong>語数</div>
  <div class="la-stat"><strong id="la-stat-chars">—</strong>文字数</div>
</div>

<!-- Output -->
<div class="la-tabs">
  <div class="la-tab active" onclick="loremSwitchTab('preview', this)">プレビュー</div>
  <div class="la-tab" onclick="loremSwitchTab('html', this)">HTML出力</div>
</div>

<div class="la-output-wrap">
  <div id="la-panel-preview" class="la-panel active">
    <div class="la-preview" id="la-preview-content">
      <div class="la-empty">
        <div class="la-empty-icon">&#9998;</div>
        <div><strong>生成する</strong>ボタンをクリックしてください</div>
      </div>
    </div>
    <div class="la-copy-row">
      <button class="la-btn-copy" id="la-copy-plain" onclick="loremCopyPlain()">
        &#128203; テキストをコピー
      </button>
    </div>
  </div>

  <div id="la-panel-html" class="la-panel">
    <textarea class="la-code" id="la-html-content" readonly placeholder="HTMLがここに表示されます..."></textarea>
    <div class="la-copy-row">
      <button class="la-btn-copy" id="la-copy-html" onclick="loremCopyHtml()">
        &#128203; HTMLをコピー
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
    opener: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    isLatin: true
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
    opener: "Artisan sustainable craft aesthetic curated bespoke kombucha vinyl gastropub fixie letterpress kale chips synth.",
    isLatin: true
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
    opener: "Synergy leverage paradigm pivot disruptive scalable agile robust innovative streamline holistic proactive actionable deliverables.",
    isLatin: true
  },
  japanese: {
    sentences: [
      "このウェブサイトは現在制作中のため、仮のテキストが表示されています。",
      "コンテンツが完成次第、正式な文章に差し替えられる予定です。",
      "デザインの確認用として、ここに適当な日本語の文章を配置しています。",
      "実際の記事や商品説明は、後ほど担当者が入力いたします。",
      "このテキストはレイアウト確認のためのサンプルです。",
      "フォントの可読性やデザインのバランスをご確認ください。",
      "段落の長さや行間も、このダミーテキストで調整できます。",
      "弊社のサービスに関するご質問は、お問い合わせページからお寄せください。",
      "新しいプロジェクトに向けて、チーム一丸となって取り組んでいます。",
      "ユーザーの皆様に最高の体験を提供することが私たちの使命です。",
      "テクノロジーの進化に合わせて、サービスも常に改善を続けています。",
      "地域社会に貢献しながら、持続可能なビジネスを目指しています。",
      "お客様のニーズに応えるため、日々研究と開発を進めています。",
      "グローバルな視点を持ちながら、地域に根ざした活動を大切にしています。",
      "創業以来、品質とサービスの向上に真摯に取り組んでまいりました。",
      "次世代を担う若者たちの可能性を引き出すことが、私たちの目標です。",
      "デジタルトランスフォーメーションにより、業務効率を大幅に改善しました。",
      "多様な人材が活躍できる職場環境の整備を進めています。",
      "環境への配慮を最優先に考え、エコフレンドリーな製品を開発しています。",
      "お客様の声に耳を傾け、サービス品質の継続的な向上を図っています。",
      "革新的なアイデアと確かな技術で、業界をリードしてまいります。",
      "チームワークを大切にし、全員が目標に向かって協力して進んでいます。",
      "最新の技術トレンドをいち早くキャッチし、実用化に取り組んでいます。",
      "お客様との長期的な信頼関係を構築することを最重視しています。",
      "社会課題の解決に貢献するプロダクトとサービスの開発を続けています。",
      "データに基づいた意思決定により、ビジネス成果を最大化しています。",
      "世界中のパートナーと連携しながら、グローバルな事業展開を進めています。",
      "ユーザビリティとアクセシビリティを両立したプロダクト設計を心がけています。",
      "イノベーションを起こすため、失敗を恐れずに新しい挑戦を続けています。",
      "お客様の成功が私たちの成功であるという理念を胸に、日々業務に励んでいます。"
    ],
    opener: null,
    isLatin: false
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

function buildParagraphLatin(words, sentMin, sentMax, wordMin, wordMax) {
  const n = randInt(sentMin, sentMax);
  let sentences = [];
  for (let i = 0; i < n; i++) {
    sentences.push(buildSentence(words, wordMin, wordMax));
  }
  return sentences.join(" ");
}

// Shuffle-pick N unique sentences (with repetition if needed)
function pickJapaneseSentences(pool, n) {
  let result = [];
  // Copy and shuffle pool
  let shuffled = pool.slice().sort(() => Math.random() - 0.5);
  for (let i = 0; i < n; i++) {
    result.push(shuffled[i % shuffled.length]);
  }
  return result;
}

// ── GENERATION ────────────────────────────────────────────────────────────────

function generateText(type, count, style, useOpener) {
  const d = DATA[style];
  let paragraphs = [];

  if (d.isLatin) {
    // Latin-based styles
    const words = d.words;

    if (type === "paragraphs") {
      for (let i = 0; i < count; i++) {
        paragraphs.push(buildParagraphLatin(words, 4, 8, 8, 18));
      }
    } else if (type === "sentences") {
      let sentences = [];
      for (let i = 0; i < count; i++) {
        sentences.push(buildSentence(words, 8, 18));
      }
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

    if (useOpener && paragraphs.length > 0 && d.opener) {
      paragraphs[0] = d.opener + " " + paragraphs[0];
    }

  } else {
    // Japanese style
    const pool = d.sentences;

    if (type === "paragraphs") {
      // Each paragraph: 3–5 sentences
      for (let i = 0; i < count; i++) {
        const sentPerPara = randInt(3, 5);
        const sents = pickJapaneseSentences(pool, sentPerPara);
        paragraphs.push(sents.join(""));
      }
    } else if (type === "sentences") {
      const sents = pickJapaneseSentences(pool, count);
      const perPara = 3;
      for (let i = 0; i < sents.length; i += perPara) {
        paragraphs.push(sents.slice(i, i + perPara).join(""));
      }
    } else if (type === "words") {
      // For Japanese "words" mode: pick sentences but treat as a flat block
      const sents = pickJapaneseSentences(pool, Math.max(1, Math.ceil(count / 10)));
      paragraphs.push(sents.join(""));
    }
    // opener checkbox is ignored for Japanese (no Latin opener)
  }

  return paragraphs;
}

// ── STATS ─────────────────────────────────────────────────────────────────────

function updateStats(paragraphs) {
  const fullText = paragraphs.join("\n\n");
  // Sentence count: Japanese ends with 。or Latin with . ! ?
  const sentCount = (fullText.match(/[.!?。！？]+/g) || []).length;
  // Word count: for Japanese count characters instead
  const isJp = document.getElementById("la-style").value === "japanese";
  let wordCount;
  if (isJp) {
    wordCount = fullText.replace(/\s/g, "").length;
  } else {
    wordCount = fullText.trim().split(/\s+/).filter(Boolean).length;
  }
  const charCount = fullText.length;
  const paraCount = paragraphs.length;

  document.getElementById("la-stat-para").textContent = paraCount;
  document.getElementById("la-stat-sent").textContent = sentCount;
  document.getElementById("la-stat-words").textContent = wordCount.toLocaleString();
  document.getElementById("la-stat-chars").textContent = charCount.toLocaleString();

  // Update label for Japanese
  const wordLabel = document.querySelector("#lorem-app .la-stat:nth-child(3)");
  if (wordLabel) {
    wordLabel.lastChild.textContent = isJp ? "文字数（語）" : "語数";
  }
}

// ── RENDER ────────────────────────────────────────────────────────────────────

function renderPreview(paragraphs) {
  const container = document.getElementById("la-preview-content");
  if (!paragraphs.length) {
    container.innerHTML = '<div class="la-empty"><div class="la-empty-icon">&#9998;</div><div><strong>生成する</strong>ボタンをクリックしてください</div></div>';
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

function flashCopied(btnId, label) {
  const btn = document.getElementById(btnId);
  const orig = btn.innerHTML;
  btn.classList.add("copied");
  btn.innerHTML = "&#10003; " + (label || "コピーしました！");
  setTimeout(() => {
    btn.classList.remove("copied");
    btn.innerHTML = orig;
  }, 2000);
}

window.loremCopyPlain = function() {
  if (!currentParagraphs.length) return;
  navigator.clipboard.writeText(currentParagraphs.join("\n\n")).then(() => {
    flashCopied("la-copy-plain", "コピーしました！");
  }).catch(() => {
    const ta = document.createElement("textarea");
    ta.value = currentParagraphs.join("\n\n");
    document.body.appendChild(ta);
    ta.select();
    document.execCommand("copy");
    document.body.removeChild(ta);
    flashCopied("la-copy-plain", "コピーしました！");
  });
};

window.loremCopyHtml = function() {
  const val = document.getElementById("la-html-content").value;
  if (!val) return;
  navigator.clipboard.writeText(val).then(() => {
    flashCopied("la-copy-html", "コピーしました！");
  }).catch(() => {
    const ta = document.createElement("textarea");
    ta.value = val;
    document.body.appendChild(ta);
    ta.select();
    document.execCommand("copy");
    document.body.removeChild(ta);
    flashCopied("la-copy-html", "コピーしました！");
  });
};

// ── INIT ──────────────────────────────────────────────────────────────────────

loremGenerate();

})();
</script>

</div>

---

**Webサイト制作の会計管理にはfreee**
ダミーテキストを使ってサイト制作中の方、制作費用の経理もfreeeで簡単管理。
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>

---

## 関連ツール

> Case Converter → [Case Converterツール](/ja/tools/case-converter/)
> Character Counter → [Character Counterツール](/ja/tools/character-counter/)
> Reading Time Calculator → [Reading Time Calculatorツール](/ja/tools/reading-time-calculator/)

