---
title: "Case Converter - Free Online Text Case Tool"
date: 2025-05-16
description: "Convert text between UPPERCASE, lowercase, Title Case, camelCase, PascalCase, snake_case, kebab-case and more. One-click copy, live preview, character count. Free online tool."
categories: ["Free Tools"]
tags: ["case converter", "text tool", "uppercase", "lowercase", "camelcase", "snake case", "developer tool"]
slug: "case-converter"
aliases: ["/tools/text-case/", "/tools/uppercase-lowercase/"]
cover:
  image: "/images/covers/case-converter.png"
  alt: "Case Converter"
ShowToc: false
---

<div id="case-app">

<style>
#case-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
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
  font-size: 1.1rem;
  font-weight: 600;
  color: #f1f5f9;
  margin: 0 0 12px 0;
  letter-spacing: 0.02em;
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
  text-transform: uppercase;
  letter-spacing: 0.08em;
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
}
</style>

<div class="case-input-section">
  <h2>Input Text</h2>
  <textarea id="case-input" placeholder="Type or paste your text here..." oninput="caseConvertAll()"></textarea>
  <div class="case-stats">
    <span>Characters: <span class="stat-val" id="char-count">0</span></span>
    <span>Words: <span class="stat-val" id="word-count">0</span></span>
    <span>Lines: <span class="stat-val" id="line-count">0</span></span>
  </div>
</div>

<div class="case-results" id="case-results">
  <!-- Cards rendered by JS -->
</div>

<script>
(function() {
  const CASES = [
    { id: 'upper',    label: 'UPPERCASE',     fn: s => s.toUpperCase() },
    { id: 'lower',    label: 'lowercase',     fn: s => s.toLowerCase() },
    { id: 'title',    label: 'Title Case',    fn: titleCase },
    { id: 'sentence', label: 'Sentence case', fn: sentenceCase },
    { id: 'camel',    label: 'camelCase',     fn: camelCase },
    { id: 'pascal',   label: 'PascalCase',    fn: pascalCase },
    { id: 'snake',    label: 'snake_case',    fn: snakeCase },
    { id: 'kebab',    label: 'kebab-case',    fn: kebabCase },
    { id: 'constant', label: 'CONSTANT_CASE', fn: constantCase },
    { id: 'dot',      label: 'dot.case',      fn: dotCase },
    { id: 'alt',      label: 'aLtErNaTiNg',   fn: alternatingCase },
    { id: 'inverse',  label: 'iNVERSE cASE',  fn: inverseCase },
  ];

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

  function buildCards() {
    const container = document.getElementById('case-results');
    container.innerHTML = CASES.map(c => `
      <div class="case-card">
        <div class="case-card-header">
          <span class="case-label">${c.label}</span>
          <button class="case-copy-btn" onclick="caseCopy('${c.id}', this)">Copy</button>
        </div>
        <div class="case-output case-placeholder" id="out-${c.id}">Result will appear here...</div>
      </div>
    `).join('');
  }

  window.caseConvertAll = function() {
    const input = document.getElementById('case-input').value;

    // Stats
    document.getElementById('char-count').textContent = input.length;
    document.getElementById('word-count').textContent = input.trim() ? input.trim().split(/\s+/).length : 0;
    document.getElementById('line-count').textContent = input ? input.split('\n').length : 0;

    // Conversions
    CASES.forEach(c => {
      const el = document.getElementById('out-' + c.id);
      if (!input.trim()) {
        el.textContent = 'Result will appear here...';
        el.classList.add('case-placeholder');
      } else {
        el.textContent = c.fn(input);
        el.classList.remove('case-placeholder');
      }
    });
  };

  window.caseCopy = function(id, btn) {
    const text = document.getElementById('out-' + id).textContent;
    if (!text || text === 'Result will appear here...') return;
    navigator.clipboard.writeText(text).then(() => {
      btn.textContent = 'Copied!';
      btn.classList.add('copied');
      setTimeout(() => {
        btn.textContent = 'Copy';
        btn.classList.remove('copied');
      }, 1800);
    }).catch(() => {
      const ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      btn.textContent = 'Copied!';
      btn.classList.add('copied');
      setTimeout(() => {
        btn.textContent = 'Copy';
        btn.classList.remove('copied');
      }, 1800);
    });
  };

  buildCards();
})();
</script>

</div>

---

## Related Tools

> Format your JSON with ease → [JSON Formatter](/tools/json-formatter/)

> Remove extra spaces, blank lines, and tabs from text → [Whitespace Remover](/tools/whitespace-remover/)

> Count words, characters, and lines → [Word Counter](/tools/word-counter/)

> Encode special characters to HTML entities → [HTML Entity Encoder](/tools/html-entity-encoder/)
