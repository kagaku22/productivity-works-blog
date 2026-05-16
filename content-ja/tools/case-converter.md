---
title: "文字変換ツール - 大文字・小文字・キャメルケース他 無料オンライン"
date: 2025-05-16
description: "テキストをUPPERCASE・lowercase・Title Case・camelCase・snake_case・kebab-caseなど12種類に一括変換。全角←→半角・カタカナ←→ひらがな変換も対応。コピーワンクリック、無料ツール。"
categories: ["無料ツール"]
tags: ["文字変換", "大文字", "小文字", "キャメルケース", "スネークケース", "ひらがな", "カタカナ", "全角", "半角"]
slug: "case-converter"
aliases: ["/ja/tools/text-case/", "/ja/tools/uppercase-lowercase/"]
cover:
  image: "/images/covers/case-converter-ja.png"
  alt: "文字変換ツール"
ShowToc: false
---

<div id="case-app">

<style>
#case-app {
  font-family: 'Segoe UI', 'Noto Sans JP', system-ui, -apple-system, sans-serif;
  background: #0f0f13;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin: 0 auto;
  max-width: 900px;
  box-sizing: border-box;
}

#case-app * {
  box-sizing: border-box;
}

#case-app h2 {
  font-size: 1.05rem;
  font-weight: 600;
  color: #f1f5f9;
  margin: 0 0 12px 0;
  letter-spacing: 0.02em;
}

.case-section-title {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: #64748b;
  margin: 20px 0 8px 0;
  padding-bottom: 4px;
  border-bottom: 1px solid #1e1e2e;
}

.case-input-section {
  margin-bottom: 20px;
}

#case-input {
  width: 100%;
  min-height: 110px;
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  color: #e2e8f0;
  font-size: 0.97rem;
  padding: 12px 14px;
  resize: vertical;
  font-family: inherit;
  transition: border-color 0.2s;
  outline: none;
}

#case-input:focus {
  border-color: #e11d48;
}

.case-stats {
  display: flex;
  gap: 20px;
  margin-top: 8px;
  font-size: 0.82rem;
  color: #94a3b8;
  flex-wrap: wrap;
}

.case-stats span {
  display: flex;
  align-items: center;
  gap: 4px;
}

.case-stats .stat-val {
  color: #e11d48;
  font-weight: 600;
}

.case-results {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

@media (max-width: 600px) {
  .case-results {
    grid-template-columns: 1fr;
  }
}

.case-card {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  padding: 12px 14px;
  transition: border-color 0.2s;
}

.case-card:hover {
  border-color: #e11d48;
}

.case-card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 8px;
}

.case-label {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  color: #e11d48;
}

.case-copy-btn {
  background: none;
  border: 1px solid #2d2d3d;
  border-radius: 5px;
  color: #94a3b8;
  font-size: 0.75rem;
  padding: 2px 10px;
  cursor: pointer;
  transition: all 0.18s;
  font-family: inherit;
}

.case-copy-btn:hover {
  background: #e11d48;
  border-color: #e11d48;
  color: #fff;
}

.case-copy-btn.copied {
  background: #16a34a;
  border-color: #16a34a;
  color: #fff;
}

.case-output {
  font-size: 0.9rem;
  color: #cbd5e1;
  word-break: break-all;
  min-height: 1.4em;
  font-family: 'Fira Mono', 'Consolas', monospace;
  line-height: 1.5;
}

.case-placeholder {
  color: #4a5568;
  font-style: italic;
  font-family: inherit;
}
</style>

<div class="case-input-section">
  <h2>テキストを入力</h2>
  <textarea id="case-input" placeholder="ここにテキストを入力または貼り付けてください..." oninput="caseConvertAll()"></textarea>
  <div class="case-stats">
    <span>文字数: <span class="stat-val" id="char-count">0</span></span>
    <span>単語数: <span class="stat-val" id="word-count">0</span></span>
    <span>行数: <span class="stat-val" id="line-count">0</span></span>
  </div>
</div>

<div class="case-section-title">英数字ケース変換</div>
<div class="case-results" id="case-results-en"></div>

<div class="case-section-title">日本語変換</div>
<div class="case-results" id="case-results-ja"></div>

<script>
(function() {
  const CASES_EN = [
    { id: 'upper',    label: 'UPPERCASE（大文字）',     fn: s => s.toUpperCase() },
    { id: 'lower',    label: 'lowercase（小文字）',     fn: s => s.toLowerCase() },
    { id: 'title',    label: 'Title Case',              fn: titleCase },
    { id: 'sentence', label: 'Sentence case',           fn: sentenceCase },
    { id: 'camel',    label: 'camelCase',               fn: camelCase },
    { id: 'pascal',   label: 'PascalCase',              fn: pascalCase },
    { id: 'snake',    label: 'snake_case',              fn: snakeCase },
    { id: 'kebab',    label: 'kebab-case',              fn: kebabCase },
    { id: 'constant', label: 'CONSTANT_CASE',           fn: constantCase },
    { id: 'dot',      label: 'dot.case',                fn: dotCase },
    { id: 'alt',      label: 'aLtErNaTiNg（交互）',    fn: alternatingCase },
    { id: 'inverse',  label: 'iNVERSE cASE（逆転）',   fn: inverseCase },
  ];

  const CASES_JA = [
    { id: 'zen2han',  label: '全角 → 半角',             fn: zen2han },
    { id: 'han2zen',  label: '半角 → 全角',             fn: han2zen },
    { id: 'kata2hira',label: 'カタカナ → ひらがな',     fn: kata2hira },
    { id: 'hira2kata',label: 'ひらがな → カタカナ',     fn: hira2kata },
  ];

  /* ── English case helpers ── */
  function words(s) {
    return s.trim().split(/[\s\-_\.]+/).filter(Boolean);
  }

  function titleCase(s) {
    return s.replace(/\w\S*/g, w => w.charAt(0).toUpperCase() + w.slice(1).toLowerCase());
  }

  function sentenceCase(s) {
    return s.toLowerCase().replace(/(^\s*\w|[.!?]\s+\w)/g, c => c.toUpperCase());
  }

  function camelCase(s) {
    const w = words(s);
    if (!w.length) return '';
    return w[0].toLowerCase() + w.slice(1).map(w => w.charAt(0).toUpperCase() + w.slice(1).toLowerCase()).join('');
  }

  function pascalCase(s) {
    return words(s).map(w => w.charAt(0).toUpperCase() + w.slice(1).toLowerCase()).join('');
  }

  function snakeCase(s) {
    return words(s).join('_').toLowerCase();
  }

  function kebabCase(s) {
    return words(s).join('-').toLowerCase();
  }

  function constantCase(s) {
    return words(s).join('_').toUpperCase();
  }

  function dotCase(s) {
    return words(s).join('.').toLowerCase();
  }

  function alternatingCase(s) {
    return s.split('').map((c, i) => i % 2 === 0 ? c.toLowerCase() : c.toUpperCase()).join('');
  }

  function inverseCase(s) {
    return s.split('').map(c => c === c.toUpperCase() ? c.toLowerCase() : c.toUpperCase()).join('');
  }

  /* ── Japanese conversion helpers ── */
  function zen2han(s) {
    // Full-width alphanumeric + space → half-width
    return s
      .replace(/[\uff01-\uff5e]/g, c => String.fromCharCode(c.charCodeAt(0) - 0xfee0))
      .replace(/\u3000/g, ' ');
  }

  function han2zen(s) {
    // Half-width alphanumeric + space → full-width
    return s
      .replace(/[\x21-\x7e]/g, c => String.fromCharCode(c.charCodeAt(0) + 0xfee0))
      .replace(/ /g, '\u3000');
  }

  function kata2hira(s) {
    return s.replace(/[\u30a1-\u30f6]/g, c => String.fromCharCode(c.charCodeAt(0) - 0x60));
  }

  function hira2kata(s) {
    return s.replace(/[\u3041-\u3096]/g, c => String.fromCharCode(c.charCodeAt(0) + 0x60));
  }

  /* ── Card builder ── */
  function buildCards(container, cases) {
    container.innerHTML = cases.map(c => `
      <div class="case-card">
        <div class="case-card-header">
          <span class="case-label">${c.label}</span>
          <button class="case-copy-btn" onclick="caseCopy('${c.id}', this)">コピー</button>
        </div>
        <div class="case-output case-placeholder" id="out-${c.id}">変換結果がここに表示されます</div>
      </div>
    `).join('');
  }

  window.caseConvertAll = function() {
    const input = document.getElementById('case-input').value;

    // Stats
    document.getElementById('char-count').textContent = input.length;
    document.getElementById('word-count').textContent = input.trim() ? input.trim().split(/\s+/).length : 0;
    document.getElementById('line-count').textContent = input ? input.split('\n').length : 0;

    const PLACEHOLDER = '変換結果がここに表示されます';

    [...CASES_EN, ...CASES_JA].forEach(c => {
      const el = document.getElementById('out-' + c.id);
      if (!input.trim()) {
        el.textContent = PLACEHOLDER;
        el.classList.add('case-placeholder');
      } else {
        el.textContent = c.fn(input);
        el.classList.remove('case-placeholder');
      }
    });
  };

  window.caseCopy = function(id, btn) {
    const text = document.getElementById('out-' + id).textContent;
    if (!text || text === '変換結果がここに表示されます') return;
    const success = () => {
      btn.textContent = 'コピー済み!';
      btn.classList.add('copied');
      setTimeout(() => { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
    };
    navigator.clipboard.writeText(text).then(success).catch(() => {
      const ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      success();
    });
  };

  buildCards(document.getElementById('case-results-en'), CASES_EN);
  buildCards(document.getElementById('case-results-ja'), CASES_JA);
})();
</script>

</div>

---

**文書管理の効率化にはfreee**
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
