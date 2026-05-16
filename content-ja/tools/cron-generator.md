---
title: "Cron式ジェネレーター"
date: 2025-05-16
description: "無料のオンラインCron式ジェネレーター。ドロップダウンで視覚的にスケジュールを構築し、日本語で説明を確認。次回5回の実行時刻もすぐわかります。"
categories: ["無料ツール"]
slug: "cron-generator"
ShowToc: false
cover:
  image: "/images/covers/cron-generator-ja.png"
  alt: "Cron式ジェネレーター"
aliases:
  - "/ja/tools/cron-expression-builder/"
  - "/ja/tools/crontab-generator/"
---

<style>
#cron-app *,
#cron-app *::before,
#cron-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#cron-app {
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, "Liberation Mono", monospace;
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 28px;
  max-width: 860px;
  margin: 0 auto;
}

#cron-app h2 {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #84cc16;
  margin-bottom: 20px;
  letter-spacing: -0.01em;
}

#cron-app .ca-section-label {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.7rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
  margin-bottom: 10px;
}

/* Presets */
#cron-app .ca-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 24px;
}

#cron-app .ca-preset-btn {
  background: #1e293b;
  border: 1px solid #334155;
  color: #94a3b8;
  font-size: 0.75rem;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  padding: 6px 12px;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.15s;
  white-space: nowrap;
}

#cron-app .ca-preset-btn:hover {
  background: #253347;
  border-color: #84cc16;
  color: #84cc16;
}

/* Manual input */
#cron-app .ca-manual-row {
  display: flex;
  gap: 10px;
  margin-bottom: 24px;
  align-items: center;
}

#cron-app .ca-manual-input {
  flex: 1;
  background: #1e293b;
  border: 1px solid #334155;
  color: #f1f5f9;
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace;
  font-size: 1rem;
  padding: 10px 14px;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.15s;
}

#cron-app .ca-manual-input:focus {
  border-color: #84cc16;
}

#cron-app .ca-parse-btn,
#cron-app .ca-copy-btn {
  background: #84cc16;
  border: none;
  color: #0f172a;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-weight: 700;
  font-size: 0.8rem;
  padding: 10px 16px;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
}

#cron-app .ca-parse-btn:hover,
#cron-app .ca-copy-btn:hover {
  background: #a3e635;
}

/* Builder grid */
#cron-app .ca-builder {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 12px;
  margin-bottom: 24px;
}

@media (max-width: 600px) {
  #cron-app .ca-builder {
    grid-template-columns: repeat(2, 1fr);
  }
}

#cron-app .ca-field {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 14px 12px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

#cron-app .ca-field-label {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.65rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #84cc16;
}

#cron-app .ca-field select,
#cron-app .ca-field input[type="text"] {
  background: #0f172a;
  border: 1px solid #334155;
  color: #f1f5f9;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.78rem;
  padding: 6px 8px;
  border-radius: 6px;
  outline: none;
  width: 100%;
  transition: border-color 0.15s;
  cursor: pointer;
}

#cron-app .ca-field input[type="text"] {
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace;
  cursor: text;
}

#cron-app .ca-field select:focus,
#cron-app .ca-field input[type="text"]:focus {
  border-color: #84cc16;
}

#cron-app .ca-field .ca-field-hint {
  font-size: 0.63rem;
  color: #475569;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
}

/* Result */
#cron-app .ca-result-box {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 16px;
}

#cron-app .ca-expr-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  margin-bottom: 12px;
}

#cron-app .ca-expr-display {
  font-size: 1.35rem;
  font-weight: 700;
  color: #84cc16;
  letter-spacing: 0.08em;
  word-break: break-all;
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace;
}

#cron-app .ca-description {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.9rem;
  color: #cbd5e1;
  line-height: 1.6;
  padding-top: 10px;
  border-top: 1px solid #334155;
}

#cron-app .ca-error {
  color: #f87171;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.85rem;
  padding-top: 10px;
  border-top: 1px solid #334155;
}

/* Next runs */
#cron-app .ca-next-box {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 16px 20px;
  margin-bottom: 20px;
}

#cron-app .ca-next-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-top: 10px;
}

#cron-app .ca-next-list li {
  font-size: 0.82rem;
  color: #94a3b8;
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace;
}

#cron-app .ca-next-list li::before {
  content: '';
  display: inline-block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #84cc16;
  flex-shrink: 0;
}

#cron-app .ca-copy-feedback {
  font-size: 0.72rem;
  color: #84cc16;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  opacity: 0;
  transition: opacity 0.3s;
  white-space: nowrap;
}

#cron-app .ca-copy-feedback.visible {
  opacity: 1;
}

/* freee CTA */
#cron-app .ca-freee-cta {
  background: linear-gradient(135deg, #1e293b 0%, #162032 100%);
  border: 1px solid #334155;
  border-left: 3px solid #84cc16;
  border-radius: 10px;
  padding: 18px 20px;
  margin-top: 8px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

#cron-app .ca-freee-cta-body {
  flex: 1;
}

#cron-app .ca-freee-cta-label {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.65rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #84cc16;
  margin-bottom: 6px;
}

#cron-app .ca-freee-cta-title {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.92rem;
  font-weight: 700;
  color: #f1f5f9;
  margin-bottom: 4px;
  line-height: 1.4;
}

#cron-app .ca-freee-cta-desc {
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-size: 0.78rem;
  color: #94a3b8;
  line-height: 1.5;
}

#cron-app .ca-freee-btn {
  display: inline-block;
  margin-top: 12px;
  background: #84cc16;
  color: #0f172a;
  font-family: ui-sans-serif, system-ui, "Hiragino Sans", "Yu Gothic", sans-serif;
  font-weight: 700;
  font-size: 0.78rem;
  padding: 8px 16px;
  border-radius: 6px;
  text-decoration: none;
  transition: background 0.15s;
  white-space: nowrap;
}

#cron-app .ca-freee-btn:hover {
  background: #a3e635;
}
</style>

<div id="cron-app">

<h2>Cron式ジェネレーター</h2>

<div class="ca-section-label">よく使うプリセット</div>
<div class="ca-presets">
  <button class="ca-preset-btn" data-expr="* * * * *">毎分</button>
  <button class="ca-preset-btn" data-expr="0 * * * *">毎時0分</button>
  <button class="ca-preset-btn" data-expr="0 0 * * *">毎日0時</button>
  <button class="ca-preset-btn" data-expr="0 9 * * *">毎日9時</button>
  <button class="ca-preset-btn" data-expr="0 0 * * 1">毎週月曜0時</button>
  <button class="ca-preset-btn" data-expr="0 9 * * 1">毎週月曜9時</button>
  <button class="ca-preset-btn" data-expr="0 0 1 * *">毎月1日0時</button>
  <button class="ca-preset-btn" data-expr="0 0 1 1 *">毎年1月1日</button>
  <button class="ca-preset-btn" data-expr="*/5 * * * *">5分ごと</button>
  <button class="ca-preset-btn" data-expr="*/15 * * * *">15分ごと</button>
  <button class="ca-preset-btn" data-expr="*/30 * * * *">30分ごと</button>
  <button class="ca-preset-btn" data-expr="0 9-17 * * 1-5">平日9〜17時（毎時）</button>
</div>

<div class="ca-section-label">式を直接入力・解析</div>
<div class="ca-manual-row">
  <input class="ca-manual-input" id="ca-manual" type="text" placeholder="例: */5 * * * *" spellcheck="false" />
  <button class="ca-parse-btn" id="ca-parse-btn">解析</button>
</div>

<div class="ca-section-label">ビジュアルビルダー</div>
<div class="ca-builder">
  <div class="ca-field">
    <div class="ca-field-label">分 (Minute)</div>
    <select id="ca-min-mode">
      <option value="any">毎分 (*)</option>
      <option value="every">N分ごと</option>
      <option value="specific">特定の分</option>
      <option value="range">範囲指定</option>
    </select>
    <input type="text" id="ca-min-val" placeholder="例: 0,30" style="display:none" />
    <div class="ca-field-hint" id="ca-min-hint"></div>
  </div>
  <div class="ca-field">
    <div class="ca-field-label">時 (Hour)</div>
    <select id="ca-hr-mode">
      <option value="any">毎時 (*)</option>
      <option value="every">N時間ごと</option>
      <option value="specific">特定の時間</option>
      <option value="range">範囲指定</option>
    </select>
    <input type="text" id="ca-hr-val" placeholder="例: 9,17" style="display:none" />
    <div class="ca-field-hint" id="ca-hr-hint"></div>
  </div>
  <div class="ca-field">
    <div class="ca-field-label">日 (Day)</div>
    <select id="ca-dom-mode">
      <option value="any">毎日 (*)</option>
      <option value="specific">特定の日</option>
      <option value="range">範囲指定</option>
    </select>
    <input type="text" id="ca-dom-val" placeholder="例: 1,15" style="display:none" />
    <div class="ca-field-hint" id="ca-dom-hint"></div>
  </div>
  <div class="ca-field">
    <div class="ca-field-label">月 (Month)</div>
    <select id="ca-mon-mode">
      <option value="any">毎月 (*)</option>
      <option value="specific">特定の月</option>
      <option value="range">範囲指定</option>
    </select>
    <input type="text" id="ca-mon-val" placeholder="例: 1,6,12" style="display:none" />
    <div class="ca-field-hint" id="ca-mon-hint"></div>
  </div>
  <div class="ca-field">
    <div class="ca-field-label">曜日 (Weekday)</div>
    <select id="ca-dow-mode">
      <option value="any">毎曜日 (*)</option>
      <option value="specific">特定の曜日</option>
      <option value="range">範囲指定</option>
    </select>
    <input type="text" id="ca-dow-val" placeholder="0=日〜6=土" style="display:none" />
    <div class="ca-field-hint" id="ca-dow-hint"></div>
  </div>
</div>

<div class="ca-result-box">
  <div class="ca-expr-row">
    <div class="ca-expr-display" id="ca-expr-display">* * * * *</div>
    <div style="display:flex;align-items:center;gap:10px">
      <span class="ca-copy-feedback" id="ca-copy-feedback">コピーしました！</span>
      <button class="ca-copy-btn" id="ca-copy-btn">コピー</button>
    </div>
  </div>
  <div class="ca-description" id="ca-description">毎分実行されます。</div>
</div>

<div class="ca-next-box">
  <div class="ca-section-label">次の5回の実行時刻</div>
  <ul class="ca-next-list" id="ca-next-list"></ul>
</div>

<div class="ca-freee-cta">
  <div class="ca-freee-cta-body">
    <div class="ca-freee-cta-label">連携ツール紹介</div>
    <div class="ca-freee-cta-title">freee会計で業務を自動化しませんか？</div>
    <div class="ca-freee-cta-desc">
      Cron定期実行と freee API を組み合わせることで、売上集計・請求書作成・経費仕訳を完全自動化できます。スモールビジネスから上場企業まで対応のクラウド会計ソフトです。
    </div>
    <a class="ca-freee-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">freeeを無料で試す &rarr;</a>
  </div>
</div>

</div>

<script>
(function () {
  'use strict';

  // ── DOM refs ─────────────────────────────────────────────────────────────
  const manual      = document.getElementById('ca-manual');
  const parseBtn    = document.getElementById('ca-parse-btn');
  const exprDisplay = document.getElementById('ca-expr-display');
  const descEl      = document.getElementById('ca-description');
  const nextList    = document.getElementById('ca-next-list');
  const copyBtn     = document.getElementById('ca-copy-btn');
  const copyFb      = document.getElementById('ca-copy-feedback');

  const fields = ['min', 'hr', 'dom', 'mon', 'dow'];
  const modes  = {};
  const vals   = {};
  const hints  = {};

  fields.forEach(f => {
    modes[f] = document.getElementById('ca-' + f + '-mode');
    vals[f]  = document.getElementById('ca-' + f + '-val');
    hints[f] = document.getElementById('ca-' + f + '-hint');
  });

  // ── Mode → show/hide value input ────────────────────────────────────────
  function updateFieldUI(f) {
    const m = modes[f].value;
    const needVal = m !== 'any';
    vals[f].style.display = needVal ? 'block' : 'none';

    const hintMap = {
      every:    { min: 'N (1〜59)', hr: 'N (1〜23)', dom: '', mon: '', dow: '' },
      specific: { min: '例: 0,15,30,45', hr: '例: 9,12,18', dom: '例: 1,15', mon: '例: 1,6,12', dow: '0=日 1=月 … 6=土' },
      range:    { min: '例: 0-29', hr: '例: 9-17', dom: '例: 1-15', mon: '例: 1-6', dow: '例: 1-5' },
    };
    hints[f].textContent = (m === 'any') ? '' : (hintMap[m] ? hintMap[m][f] || '' : '');

    if (m !== 'any' && !vals[f].value) {
      const defaults = {
        every:    { min: '5', hr: '2', dom: '', mon: '', dow: '' },
        specific: { min: '0', hr: '9', dom: '1', mon: '1', dow: '1' },
        range:    { min: '0-29', hr: '9-17', dom: '1-15', mon: '1-6', dow: '1-5' },
      };
      vals[f].value = defaults[m] ? (defaults[m][f] || '') : '';
    }
    rebuild();
  }

  fields.forEach(f => {
    modes[f].addEventListener('change', () => updateFieldUI(f));
    vals[f].addEventListener('input', rebuild);
  });

  // ── Build expression from UI ─────────────────────────────────────────────
  function fieldExpr(f) {
    const m = modes[f].value;
    const v = vals[f].value.trim();
    if (m === 'any') return '*';
    if (m === 'every') {
      const n = parseInt(v, 10);
      if (!v || isNaN(n) || n < 1) return '*';
      return '*/' + n;
    }
    return v || '*';
  }

  function rebuild() {
    const expr = fields.map(f => fieldExpr(f)).join(' ');
    setExpression(expr);
  }

  // ── Parse & describe ─────────────────────────────────────────────────────
  function setExpression(expr) {
    expr = expr.trim();
    exprDisplay.textContent = expr;
    manual.value = expr;

    const result = parseExpr(expr);
    if (result.error) {
      descEl.className = 'ca-error';
      descEl.textContent = result.error;
      nextList.innerHTML = '';
    } else {
      descEl.className = 'ca-description';
      descEl.textContent = result.description;
      renderNext(expr);
    }
  }

  function parseExpr(expr) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5)
      return { error: 'Cron式は「分 時 日 月 曜日」の5フィールドで記述してください。' };

    const [min, hr, dom, mon, dow] = parts;
    const ranges = [
      [min, 0, 59, '分'],
      [hr,  0, 23, '時'],
      [dom, 1, 31, '日'],
      [mon, 1, 12, '月'],
      [dow, 0,  7, '曜日'],
    ];
    for (const [f, lo, hi, name] of ranges) {
      const err = validateField(f, lo, hi);
      if (err) return { error: name + 'の値が不正です: ' + err };
    }

    return { description: describe(min, hr, dom, mon, dow) };
  }

  function validateField(f, lo, hi) {
    if (f === '*') return null;
    if (/^\*\/\d+$/.test(f)) {
      const n = parseInt(f.slice(2), 10);
      if (n < 1) return 'ステップは1以上にしてください';
      return null;
    }
    const parts = f.split(',');
    for (const p of parts) {
      if (p.includes('-')) {
        const [a, b] = p.split('-').map(Number);
        if (isNaN(a) || isNaN(b) || a < lo || b > hi || a > b)
          return '"' + p + '" は有効な範囲ではありません（' + lo + '〜' + hi + '）';
      } else {
        const n = Number(p);
        if (isNaN(n) || n < lo || n > hi)
          return '"' + p + '" は範囲外です（' + lo + '〜' + hi + '）';
      }
    }
    return null;
  }

  // ── Human-readable description (Japanese) ───────────────────────────────
  const MONTHS_JA = ['','1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
  const DAYS_JA   = ['日曜','月曜','火曜','水曜','木曜','金曜','土曜','日曜'];

  function fmtField(f, type) {
    if (f === '*') return null;
    if (f.startsWith('*/')) {
      const n = f.slice(2);
      const label = { min: '分', hr: '時間', dom: '日', mon: 'ヶ月', dow: '曜日' }[type];
      return n + label + 'ごと';
    }
    const parts = f.split(',');
    const fmted = parts.map(p => {
      if (p.includes('-')) {
        const [a, b] = p.split('-');
        if (type === 'mon') return MONTHS_JA[+a] + '〜' + MONTHS_JA[+b];
        if (type === 'dow') return DAYS_JA[+a] + '〜' + DAYS_JA[+b];
        return p;
      }
      if (type === 'mon') return MONTHS_JA[+p] || p;
      if (type === 'dow') return DAYS_JA[+p] || p;
      return p;
    });
    return fmted.join('、');
  }

  function describe(min, hr, dom, mon, dow) {
    let time = '';
    const pad = n => String(n).padStart(2, '0');

    if (min === '*' && hr === '*') {
      time = '毎分';
    } else if (min.startsWith('*/') && hr === '*') {
      time = min.slice(2) + '分ごと';
    } else if (hr.startsWith('*/') && min === '0') {
      time = hr.slice(2) + '時間ごと（0分に実行）';
    } else if (hr.startsWith('*/')) {
      time = hr.slice(2) + '時間ごと（' + min + '分に実行）';
    } else {
      const hrParts = hr.split(',');
      const minStr = min === '*' ? 'xx分' : (min.includes(',') ? '[' + min + ']分' : pad(+min) + '分');
      const times = hrParts.map(h => {
        if (h.includes('-')) return h + '時台の' + minStr;
        return h + '時' + minStr;
      });
      time = times.join('、') + 'に';
    }

    const dowStr = fmtField(dow, 'dow');
    const domStr = fmtField(dom, 'dom');
    const monStr = fmtField(mon, 'mon');

    let schedule = '';

    if (monStr) schedule += monStr + 'の';

    if (dowStr) {
      schedule += dowStr + 'の';
    } else if (domStr) {
      if (dom.startsWith('*/')) {
        schedule += domStr + 'の';
      } else {
        const domParts = dom.split(',');
        const domFmt = domParts.map(p => {
          if (p.includes('-')) return p + '日';
          return p + '日';
        });
        schedule += domFmt.join('・') + 'の';
      }
    }

    const isTime = time.endsWith('に');
    schedule += time + (isTime ? '実行されます。' : 'に実行されます。');

    return schedule;
  }

  // ── Next 5 execution times ────────────────────────────────────────────────
  function renderNext(expr) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) { nextList.innerHTML = ''; return; }
    const [min, hr, dom, mon, dow] = parts;

    const times = nextRuns(min, hr, dom, mon, dow, 5);
    nextList.innerHTML = times.map(d => '<li>' + formatDate(d) + '</li>').join('');
  }

  function expandField(f, lo, hi) {
    if (f === '*') {
      const r = [];
      for (let i = lo; i <= hi; i++) r.push(i);
      return r;
    }
    if (f.startsWith('*/')) {
      const step = parseInt(f.slice(2), 10);
      const r = [];
      for (let i = lo; i <= hi; i += step) r.push(i);
      return r;
    }
    const result = new Set();
    f.split(',').forEach(p => {
      if (p.includes('-')) {
        const [a, b] = p.split('-').map(Number);
        for (let i = a; i <= b; i++) result.add(i);
      } else {
        result.add(Number(p));
      }
    });
    return [...result].sort((a,b) => a-b);
  }

  function nextRuns(minF, hrF, domF, monF, dowF, count) {
    const mins = expandField(minF, 0, 59);
    const hrs  = expandField(hrF,  0, 23);
    const doms = expandField(domF, 1, 31);
    const mons = expandField(monF, 1, 12);
    const dows = dowF === '*' ? null : expandField(dowF.replace('7','0'), 0, 6);

    const results = [];
    const now = new Date();
    const start = new Date(now.getFullYear(), now.getMonth(), now.getDate(), now.getHours(), now.getMinutes() + 1, 0, 0);

    let d = new Date(start);
    const limit = new Date(start.getTime() + 366 * 24 * 60 * 60 * 1000);

    while (results.length < count && d < limit) {
      const m  = d.getMonth() + 1;
      const dy = d.getDate();
      const h  = d.getHours();
      const mn = d.getMinutes();
      const wd = d.getDay();

      if (!mons.includes(m)) {
        const nextMon = mons.find(x => x > m);
        if (nextMon) {
          d = new Date(d.getFullYear(), nextMon - 1, 1, 0, 0, 0, 0);
        } else {
          d = new Date(d.getFullYear() + 1, mons[0] - 1, 1, 0, 0, 0, 0);
        }
        continue;
      }

      const domOk = doms.includes(dy);
      const dowOk = dows === null || dows.includes(wd);
      if (!domOk && !dowOk) {
        d = new Date(d.getFullYear(), d.getMonth(), d.getDate() + 1, 0, 0, 0, 0);
        continue;
      }

      if (!hrs.includes(h)) {
        const nextHr = hrs.find(x => x > h);
        if (nextHr !== undefined) {
          d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), nextHr, 0, 0, 0);
        } else {
          d = new Date(d.getFullYear(), d.getMonth(), d.getDate() + 1, 0, 0, 0, 0);
        }
        continue;
      }

      if (!mins.includes(mn)) {
        const nextMin = mins.find(x => x > mn);
        if (nextMin !== undefined) {
          d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), d.getHours(), nextMin, 0, 0);
        } else {
          const nextHr = hrs.find(x => x > h);
          if (nextHr !== undefined) {
            d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), nextHr, 0, 0, 0);
          } else {
            d = new Date(d.getFullYear(), d.getMonth(), d.getDate() + 1, 0, 0, 0, 0);
          }
        }
        continue;
      }

      results.push(new Date(d));
      d = new Date(d.getFullYear(), d.getMonth(), d.getDate(), d.getHours(), d.getMinutes() + 1, 0, 0);
    }

    return results;
  }

  function formatDate(d) {
    const days = ['日','月','火','水','木','金','土'];
    const pad = n => String(n).padStart(2, '0');
    return d.getFullYear() + '年' + pad(d.getMonth()+1) + '月' + pad(d.getDate()) + '日（' +
      days[d.getDay()] + '）  ' + pad(d.getHours()) + ':' + pad(d.getMinutes());
  }

  // ── Presets ──────────────────────────────────────────────────────────────
  document.querySelectorAll('#cron-app .ca-preset-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const expr = btn.dataset.expr;
      loadExprIntoBuilder(expr);
      setExpression(expr);
    });
  });

  function loadExprIntoBuilder(expr) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return;
    const [minV, hrV, domV, monV, dowV] = parts;

    function detectMode(f) {
      if (f === '*') return 'any';
      if (f.startsWith('*/')) return 'every';
      if (f.includes('-')) return 'range';
      return 'specific';
    }

    [['min', minV],['hr', hrV],['dom', domV],['mon', monV],['dow', dowV]].forEach(([f, v]) => {
      const m = detectMode(v);
      modes[f].value = m;
      if (m === 'any') {
        vals[f].value = '';
        vals[f].style.display = 'none';
      } else if (m === 'every') {
        vals[f].value = v.slice(2);
        vals[f].style.display = 'block';
      } else {
        vals[f].value = v;
        vals[f].style.display = 'block';
      }
      hints[f].textContent = '';
    });
  }

  // ── Manual parse ─────────────────────────────────────────────────────────
  parseBtn.addEventListener('click', () => {
    const expr = manual.value.trim();
    if (!expr) return;
    loadExprIntoBuilder(expr);
    setExpression(expr);
  });

  manual.addEventListener('keydown', e => {
    if (e.key === 'Enter') parseBtn.click();
  });

  // ── Copy ─────────────────────────────────────────────────────────────────
  copyBtn.addEventListener('click', () => {
    const expr = exprDisplay.textContent;
    navigator.clipboard.writeText(expr).then(() => {
      copyFb.classList.add('visible');
      setTimeout(() => copyFb.classList.remove('visible'), 1800);
    }).catch(() => {
      const ta = document.createElement('textarea');
      ta.value = expr;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      copyFb.classList.add('visible');
      setTimeout(() => copyFb.classList.remove('visible'), 1800);
    });
  });

  // ── Init ─────────────────────────────────────────────────────────────────
  setExpression('* * * * *');

})();
</script>
