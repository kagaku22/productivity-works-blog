---
title: "空白削除ツール - 無料オンラインで余分なスペース・空行を除去"
date: 2025-05-16
description: "テキストの余分なスペース・空白行・タブ・改行をワンクリックで削除。差分ハイライト表示、削除前後の文字数カウント付き。無料のオンライン空白削除ツール。"
categories: ["無料ツール"]
tags: ["空白削除", "スペース削除", "空行削除", "テキスト整形", "タブ削除"]
slug: "whitespace-remover"
aliases: ["/ja/tools/trim-whitespace/", "/ja/tools/remove-spaces/"]
cover:
  image: "/images/covers/whitespace-remover-ja.png"
  alt: "空白削除ツール"
ShowToc: false
---

<div id="ws-app">

<style>
#ws-app {
  font-family: 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 880px;
  margin: 0 auto;
  color: #134e4a;
}

#ws-app * {
  box-sizing: border-box;
}

/* オプションパネル */
#ws-options {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 16px;
  padding: 14px 16px;
  background: #f0fdfa;
  border: 1.5px solid #99f6e4;
  border-radius: 12px;
}

.ws-opt-label {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 0.875rem;
  font-weight: 500;
  color: #134e4a;
  cursor: pointer;
  user-select: none;
  padding: 4px 10px;
  border-radius: 8px;
  transition: background 0.15s;
}

.ws-opt-label:hover {
  background: #ccfbf1;
}

.ws-opt-label input[type="checkbox"] {
  accent-color: #0d9488;
  width: 16px;
  height: 16px;
  cursor: pointer;
}

/* テキストエリア行 */
#ws-io-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 12px;
}

@media (max-width: 640px) {
  #ws-io-row {
    grid-template-columns: 1fr;
  }
}

.ws-panel-label {
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: #0f766e;
  margin-bottom: 6px;
}

#ws-input, #ws-output {
  width: 100%;
  min-height: 220px;
  padding: 14px 16px;
  font-size: 0.95rem;
  line-height: 1.7;
  border: 2px solid #99f6e4;
  border-radius: 10px;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  background: #f0fdfa;
  color: #134e4a;
  font-family: inherit;
}

#ws-input:focus {
  border-color: #0d9488;
  background: #fff;
  box-shadow: 0 0 0 3px rgba(13,148,136,0.12);
}

#ws-output {
  background: #fafffe;
  color: #134e4a;
}

/* 差分プレビュー */
#ws-diff-wrap {
  margin-bottom: 16px;
}

#ws-diff-title {
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: #0f766e;
  margin-bottom: 6px;
}

#ws-diff {
  width: 100%;
  min-height: 100px;
  max-height: 260px;
  overflow-y: auto;
  padding: 14px 16px;
  font-size: 0.9rem;
  line-height: 1.75;
  border: 2px solid #99f6e4;
  border-radius: 10px;
  background: #f0fdfa;
  white-space: pre-wrap;
  word-break: break-word;
  font-family: inherit;
}

#ws-diff .ws-removed {
  background: #fecaca;
  color: #991b1b;
  text-decoration: line-through;
  border-radius: 2px;
  padding: 0 1px;
}

/* 統計ボックス */
#ws-stats {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 14px;
}

.ws-stat-box {
  flex: 1 1 140px;
  padding: 12px 16px;
  border-radius: 10px;
  border: 1.5px solid #99f6e4;
  background: #f0fdfa;
  text-align: center;
}

.ws-stat-box .ws-stat-val {
  font-size: 1.6rem;
  font-weight: 700;
  color: #0d9488;
  line-height: 1.1;
}

.ws-stat-box .ws-stat-lbl {
  font-size: 0.78rem;
  color: #5eead4;
  margin-top: 3px;
}

/* ボタン */
#ws-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 18px;
}

.ws-btn {
  padding: 9px 20px;
  border: none;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  font-family: inherit;
}

.ws-btn:active {
  transform: scale(0.97);
}

.ws-btn-primary {
  background: #0d9488;
  color: #fff;
}

.ws-btn-primary:hover {
  background: #0f766e;
}

.ws-btn-secondary {
  background: #ccfbf1;
  color: #0f766e;
}

.ws-btn-secondary:hover {
  background: #99f6e4;
}

.ws-btn-danger {
  background: #fee2e2;
  color: #b91c1c;
}

.ws-btn-danger:hover {
  background: #fecaca;
}

/* コピートースト */
#ws-toast {
  display: none;
  padding: 8px 16px;
  background: #0d9488;
  color: #fff;
  border-radius: 8px;
  font-size: 0.85rem;
  font-weight: 600;
  align-items: center;
}

#ws-toast.ws-show {
  display: inline-flex;
}

/* freee CTA */
#ws-freee-cta {
  margin-top: 28px;
  padding: 14px 18px;
  background: #f0fdfa;
  border-left: 4px solid #0d9488;
  border-radius: 0 8px 8px 0;
  font-size: 0.9rem;
  color: #134e4a;
  line-height: 1.7;
}

#ws-freee-cta strong {
  display: block;
  margin-bottom: 4px;
  color: #0f766e;
  font-size: 0.95rem;
}

#ws-freee-cta a {
  color: #0d9488;
  font-weight: 600;
  text-decoration: none;
  border-bottom: 1.5px solid #5eead4;
  transition: color 0.15s;
}

#ws-freee-cta a:hover {
  color: #0f766e;
}
</style>

<!-- オプション -->
<div id="ws-options">
  <label class="ws-opt-label"><input type="checkbox" id="opt-trim" checked> 先頭・末尾のスペースを削除</label>
  <label class="ws-opt-label"><input type="checkbox" id="opt-double-spaces" checked> 連続スペースを1つに</label>
  <label class="ws-opt-label"><input type="checkbox" id="opt-blank-lines" checked> 空白行を削除</label>
  <label class="ws-opt-label"><input type="checkbox" id="opt-trim-lines"> 各行の前後スペースを削除</label>
  <label class="ws-opt-label"><input type="checkbox" id="opt-tabs"> タブを削除</label>
  <label class="ws-opt-label"><input type="checkbox" id="opt-linebreaks"> 改行を削除</label>
  <label class="ws-opt-label"><input type="checkbox" id="opt-all-ws"> 全空白を削除</label>
</div>

<!-- 入力 / 出力 -->
<div id="ws-io-row">
  <div>
    <div class="ws-panel-label">入力テキスト</div>
    <textarea id="ws-input" placeholder="ここにテキストを貼り付けまたは入力..."></textarea>
  </div>
  <div>
    <div class="ws-panel-label">整形後テキスト</div>
    <textarea id="ws-output" readonly placeholder="整形されたテキストがここに表示されます..."></textarea>
  </div>
</div>

<!-- 統計 -->
<div id="ws-stats">
  <div class="ws-stat-box">
    <div class="ws-stat-val" id="stat-before">0</div>
    <div class="ws-stat-lbl">整形前の文字数</div>
  </div>
  <div class="ws-stat-box">
    <div class="ws-stat-val" id="stat-after">0</div>
    <div class="ws-stat-lbl">整形後の文字数</div>
  </div>
  <div class="ws-stat-box">
    <div class="ws-stat-val" id="stat-removed">0</div>
    <div class="ws-stat-lbl">削除文字数</div>
  </div>
  <div class="ws-stat-box">
    <div class="ws-stat-val" id="stat-pct">0%</div>
    <div class="ws-stat-lbl">削減率</div>
  </div>
</div>

<!-- 差分プレビュー -->
<div id="ws-diff-wrap">
  <div id="ws-diff-title">差分プレビュー（取り消し線＝削除された文字）</div>
  <div id="ws-diff"></div>
</div>

<!-- アクション -->
<div id="ws-actions">
  <button class="ws-btn ws-btn-primary" id="btn-copy">出力をコピー</button>
  <button class="ws-btn ws-btn-secondary" id="btn-swap">出力を入力に使用</button>
  <button class="ws-btn ws-btn-danger" id="btn-clear">クリア</button>
  <span id="ws-toast">コピーしました！</span>
</div>

<!-- freee CTA -->
<div id="ws-freee-cta">
  <strong>テキスト処理の効率化にはfreee</strong>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
</div>

</div>

<script>
(function() {
  const input    = document.getElementById('ws-input');
  const output   = document.getElementById('ws-output');
  const diffEl   = document.getElementById('ws-diff');
  const statBefore  = document.getElementById('stat-before');
  const statAfter   = document.getElementById('stat-after');
  const statRemoved = document.getElementById('stat-removed');
  const statPct     = document.getElementById('stat-pct');
  const toast    = document.getElementById('ws-toast');

  const opts = {
    trim:        document.getElementById('opt-trim'),
    doubleSpaces:document.getElementById('opt-double-spaces'),
    blankLines:  document.getElementById('opt-blank-lines'),
    trimLines:   document.getElementById('opt-trim-lines'),
    tabs:        document.getElementById('opt-tabs'),
    linebreaks:  document.getElementById('opt-linebreaks'),
    allWs:       document.getElementById('opt-all-ws'),
  };

  opts.allWs.addEventListener('change', function() {
    const state = this.checked;
    [opts.trim, opts.doubleSpaces, opts.blankLines, opts.trimLines, opts.tabs, opts.linebreaks].forEach(o => {
      o.disabled = state;
    });
    process();
  });

  function clean(text) {
    if (opts.allWs.checked) {
      return text.replace(/\s/g, '');
    }
    let t = text;
    if (opts.tabs.checked)         t = t.replace(/\t/g, '');
    if (opts.trimLines.checked)    t = t.split('\n').map(l => l.trim()).join('\n');
    if (opts.linebreaks.checked)   t = t.replace(/\r?\n/g, ' ');
    if (opts.blankLines.checked)   t = t.replace(/(\r?\n){2,}/g, '\n');
    if (opts.doubleSpaces.checked) t = t.replace(/ {2,}/g, ' ');
    if (opts.trim.checked)         t = t.trim();
    return t;
  }

  function buildDiff(original, cleaned) {
    const a = original.slice(0, 5000);
    const b = cleaned.slice(0, 5000);

    const dp = [];
    for (let i = 0; i <= a.length; i++) {
      dp[i] = new Array(b.length + 1).fill(0);
    }
    for (let i = 1; i <= a.length; i++) {
      for (let j = 1; j <= b.length; j++) {
        dp[i][j] = a[i-1] === b[j-1] ? dp[i-1][j-1] + 1 : Math.max(dp[i-1][j], dp[i][j-1]);
      }
    }

    let i = a.length, j = b.length;
    const ops = [];
    while (i > 0 || j > 0) {
      if (i > 0 && j > 0 && a[i-1] === b[j-1]) {
        ops.push({ type: 'keep', ch: a[i-1] }); i--; j--;
      } else if (j > 0 && (i === 0 || dp[i][j-1] >= dp[i-1][j])) {
        j--;
      } else {
        ops.push({ type: 'del', ch: a[i-1] }); i--;
      }
    }
    ops.reverse();

    let html = '';
    let run = null;
    for (const op of ops) {
      const safe = op.ch === '<' ? '&lt;' : op.ch === '>' ? '&gt;' : op.ch === '&' ? '&amp;' : op.ch === '\n' ? '↵\n' : op.ch === '\t' ? '→' : op.ch === ' ' ? '·' : op.ch;
      if (op.type === 'del') {
        if (run !== 'del') { if (run === 'del') html += '</span>'; html += '<span class="ws-removed">'; run = 'del'; }
        html += safe;
      } else {
        if (run === 'del') { html += '</span>'; }
        run = 'keep';
        html += op.ch === '\n' ? '\n' : op.ch === '\t' ? '\t' : op.ch === '<' ? '&lt;' : op.ch === '>' ? '&gt;' : op.ch === '&' ? '&amp;' : op.ch;
      }
    }
    if (run === 'del') html += '</span>';
    if (original.length > 5000) html += '\n...（プレビューは5000文字までに制限）';
    return html;
  }

  function process() {
    const raw = input.value;
    const result = clean(raw);
    output.value = result;

    const before  = raw.length;
    const after   = result.length;
    const removed = before - after;
    const pct     = before > 0 ? Math.round((removed / before) * 100) : 0;

    statBefore.textContent  = before.toLocaleString('ja-JP');
    statAfter.textContent   = after.toLocaleString('ja-JP');
    statRemoved.textContent = removed.toLocaleString('ja-JP');
    statPct.textContent     = pct + '%';

    diffEl.innerHTML = raw.length > 0
      ? buildDiff(raw, result)
      : '<span style="color:#9ca3af;font-style:italic;">上にテキストを貼り付けると差分が表示されます...</span>';
  }

  input.addEventListener('input', process);
  Object.values(opts).forEach(o => o.addEventListener('change', process));

  document.getElementById('btn-copy').addEventListener('click', function() {
    const text = output.value;
    if (!text) return;
    navigator.clipboard.writeText(text).then(() => {
      toast.classList.add('ws-show');
      setTimeout(() => toast.classList.remove('ws-show'), 1800);
    });
  });

  document.getElementById('btn-swap').addEventListener('click', function() {
    input.value = output.value;
    process();
  });

  document.getElementById('btn-clear').addEventListener('click', function() {
    input.value = '';
    process();
  });

  process();
})();
</script>
