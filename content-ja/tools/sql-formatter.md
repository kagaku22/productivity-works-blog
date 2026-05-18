---
title: "SQLフォーマッター — 無料オンラインツール"
description: "SQLクエリをブラウザ上で即座に整形・美化・ミニファイ。キーワード大文字化、サブクエリインデント、シンタックスハイライト対応。データはサーバーに送信されません。"
date: 2026-01-25
categories: ["無料ツール"]
slug: "sql-formatter"
aliases: ["/ja/tools/sql-formatter/", "/ja/tools/sql-formatter/"]
ShowToc: false
cover:
  image: "/images/covers/sql-formatter-ja.png"
  alt: "SQLフォーマッター"
---

SQLを貼り付けるだけで、適切なインデント・キーワード大文字化・シンタックスハイライト付きで整形できます。すべてブラウザ内で完結し、データは一切サーバーに送信されません。

<style>
#sql-app *,
#sql-app *::before,
#sql-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#sql-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic UI", "Meiryo", sans-serif;
  background: #1a1a2e;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  max-width: 900px;
  margin: 0 auto 2rem auto;
}
#sql-app h2 {
  font-size: 1.1rem;
  color: #93c5fd;
  margin-bottom: 12px;
  letter-spacing: 0.03em;
}
#sql-app .sql-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 16px;
  align-items: center;
}
#sql-app .sql-btn {
  background: #2563eb;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 8px 18px;
  font-size: 0.92rem;
  cursor: pointer;
  transition: background 0.15s;
  font-weight: 700;
}
#sql-app .sql-btn:hover { background: #1d4ed8; }
#sql-app .sql-btn.secondary {
  background: #374151;
  color: #e2e8f0;
}
#sql-app .sql-btn.secondary:hover { background: #4b5563; }
#sql-app .sql-label {
  font-size: 0.85rem;
  color: #94a3b8;
  display: flex;
  align-items: center;
  gap: 6px;
}
#sql-app .sql-label select {
  background: #0f172a;
  color: #e2e8f0;
  border: 1px solid #334155;
  border-radius: 5px;
  padding: 5px 8px;
  font-size: 0.88rem;
}
#sql-app .sql-label input[type="checkbox"] {
  accent-color: #60a5fa;
  width: 15px;
  height: 15px;
}
#sql-app .sql-pane {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 14px;
}
@media (max-width: 620px) {
  #sql-app .sql-pane { grid-template-columns: 1fr; }
}
#sql-app .sql-section label {
  display: block;
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 6px;
}
#sql-app textarea {
  width: 100%;
  height: 220px;
  background: #0f172a;
  color: #e2e8f0;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 12px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.85rem;
  resize: vertical;
  line-height: 1.6;
  outline: none;
  transition: border-color 0.15s;
}
#sql-app textarea:focus { border-color: #60a5fa; }
#sql-app .sql-output-wrap {
  position: relative;
}
#sql-app .sql-output {
  width: 100%;
  min-height: 220px;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 12px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.85rem;
  line-height: 1.6;
  white-space: pre;
  overflow: auto;
  color: #e2e8f0;
}
#sql-app .sql-copy-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: #1e293b;
  color: #94a3b8;
  border: 1px solid #334155;
  border-radius: 5px;
  padding: 4px 10px;
  font-size: 0.78rem;
  cursor: pointer;
  transition: all 0.15s;
}
#sql-app .sql-copy-btn:hover { background: #334155; color: #e2e8f0; }
#sql-app .sql-status {
  font-size: 0.82rem;
  color: #4ade80;
  min-height: 1.2em;
  margin-top: 4px;
}
#sql-app .kw  { color: #60a5fa; font-weight: 700; }
#sql-app .str { color: #4ade80; }
#sql-app .num { color: #fb923c; }
#sql-app .cmt { color: #6b7280; font-style: italic; }

/* freee CTA */
#sql-app .freee-cta {
  margin-top: 20px;
  background: #0f172a;
  border: 1px solid #2563eb;
  border-radius: 10px;
  padding: 16px 20px;
  display: flex;
  align-items: center;
  gap: 14px;
  flex-wrap: wrap;
}
#sql-app .freee-cta .freee-text {
  flex: 1;
  min-width: 200px;
}
#sql-app .freee-cta .freee-text strong {
  display: block;
  color: #93c5fd;
  font-size: 0.95rem;
  margin-bottom: 4px;
}
#sql-app .freee-cta .freee-text span {
  font-size: 0.82rem;
  color: #94a3b8;
}
#sql-app .freee-cta a.freee-link {
  background: #2563eb;
  color: #fff;
  text-decoration: none;
  border-radius: 6px;
  padding: 9px 20px;
  font-size: 0.88rem;
  font-weight: 700;
  white-space: nowrap;
  transition: background 0.15s;
}
#sql-app .freee-cta a.freee-link:hover { background: #1d4ed8; }
</style>

<div id="sql-app">
  <h2>SQLフォーマッター</h2>

  <div class="sql-controls">
    <button class="sql-btn" id="sql-format-btn">整形する</button>
    <button class="sql-btn secondary" id="sql-minify-btn">ミニファイ</button>
    <button class="sql-btn secondary" id="sql-clear-btn">クリア</button>
    <label class="sql-label">
      <input type="checkbox" id="sql-highlight-chk" checked>
      シンタックスハイライト
    </label>
    <label class="sql-label">
      インデント幅:
      <select id="sql-tabsize-sel">
        <option value="2">スペース2</option>
        <option value="4" selected>スペース4</option>
      </select>
    </label>
  </div>

  <div class="sql-pane">
    <div class="sql-section">
      <label>入力SQL</label>
      <textarea id="sql-input" placeholder="SQLをここに貼り付けてください…" spellcheck="false"></textarea>
    </div>
    <div class="sql-section">
      <label>整形結果</label>
      <div class="sql-output-wrap">
        <div class="sql-output" id="sql-output"></div>
        <button class="sql-copy-btn" id="sql-copy-btn">コピー</button>
      </div>
    </div>
  </div>

  <div class="sql-status" id="sql-status"></div>

  <div class="freee-cta">
    <div class="freee-text">
      <strong>freee会計で経理・帳簿を自動化しませんか？</strong>
      <span>SQLで集計する前に、まずはfreeeでデータを一元管理。30日間無料トライアル実施中。</span>
    </div>
    <a class="freee-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freeeを無料で試す</a>
  </div>
</div>

<script>
(function () {
  'use strict';

  const KEYWORDS = [
    'SELECT','FROM','WHERE','AND','OR',
    'LEFT JOIN','RIGHT JOIN','INNER JOIN','OUTER JOIN','FULL JOIN',
    'JOIN','ON','GROUP BY','ORDER BY','HAVING','LIMIT','OFFSET',
    'INSERT INTO','INSERT','UPDATE','DELETE','CREATE TABLE','CREATE INDEX',
    'CREATE','ALTER TABLE','ALTER','DROP TABLE','DROP',
    'TABLE','INDEX','VALUES','SET','AS','IN','NOT IN','NOT',
    'NULL','IS NULL','IS NOT NULL','IS',
    'LIKE','BETWEEN','UNION ALL','UNION',
    'ALL','DISTINCT','COUNT','SUM','AVG','MAX','MIN',
    'CASE','WHEN','THEN','ELSE','END',
    'WITH','EXISTS','RETURNING'
  ];

  const CLAUSE_KW = [
    'SELECT','FROM','WHERE','LEFT JOIN','RIGHT JOIN','INNER JOIN',
    'OUTER JOIN','FULL JOIN','JOIN','ON','GROUP BY','ORDER BY',
    'HAVING','LIMIT','OFFSET','INSERT INTO','INSERT','UPDATE',
    'DELETE','CREATE TABLE','CREATE INDEX','CREATE','ALTER TABLE',
    'ALTER','DROP TABLE','DROP','SET','VALUES','UNION ALL','UNION',
    'WITH','RETURNING'
  ];

  function tokenize(sql) {
    const tokens = [];
    let i = 0;
    while (i < sql.length) {
      if (sql[i] === '-' && sql[i+1] === '-') {
        let j = i;
        while (j < sql.length && sql[j] !== '\n') j++;
        tokens.push({ type: 'comment', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (sql[i] === '/' && sql[i+1] === '*') {
        let j = i + 2;
        while (j < sql.length && !(sql[j] === '*' && sql[j+1] === '/')) j++;
        j += 2;
        tokens.push({ type: 'comment', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (sql[i] === "'") {
        let j = i + 1;
        while (j < sql.length) {
          if (sql[j] === "'" && sql[j+1] === "'") { j += 2; continue; }
          if (sql[j] === "'") { j++; break; }
          j++;
        }
        tokens.push({ type: 'string', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (sql[i] === '"') {
        let j = i + 1;
        while (j < sql.length && sql[j] !== '"') j++;
        j++;
        tokens.push({ type: 'ident', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (sql[i] === '`') {
        let j = i + 1;
        while (j < sql.length && sql[j] !== '`') j++;
        j++;
        tokens.push({ type: 'ident', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (/[0-9]/.test(sql[i]) || (sql[i] === '.' && /[0-9]/.test(sql[i+1]))) {
        let j = i;
        while (j < sql.length && /[0-9.\-eExX_a-fA-F]/.test(sql[j])) j++;
        tokens.push({ type: 'number', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (/\s/.test(sql[i])) {
        let j = i;
        while (j < sql.length && /\s/.test(sql[j])) j++;
        tokens.push({ type: 'ws', val: sql.slice(i, j) });
        i = j; continue;
      }
      if (/[(),;*=<>!+\-\/%&|^~]/.test(sql[i])) {
        tokens.push({ type: 'punct', val: sql[i] });
        i++; continue;
      }
      let j = i;
      while (j < sql.length && /[A-Za-z0-9_$#@]/.test(sql[j])) j++;
      if (j === i) { tokens.push({ type: 'other', val: sql[i] }); i++; continue; }
      tokens.push({ type: 'word', val: sql.slice(i, j) });
      i = j;
    }
    return tokens;
  }

  function upperKeywords(tokens) {
    const out = tokens.map(t => Object.assign({}, t));
    const single = new Set(KEYWORDS.filter(k => !k.includes(' ')));
    for (let i = 0; i < out.length; i++) {
      if (out[i].type === 'word' && single.has(out[i].val.toUpperCase())) {
        out[i].val = out[i].val.toUpperCase();
        out[i].type = 'keyword';
      }
    }
    const multi = KEYWORDS.filter(k => k.includes(' ')).sort((a,b) => b.length - a.length);
    for (const kw of multi) {
      const parts = kw.split(' ');
      for (let i = 0; i <= out.length - parts.length; i++) {
        const slice = out.slice(i, i + parts.length * 2 - 1);
        let pi = 0, si = 0, match = true;
        while (pi < parts.length && si < slice.length) {
          if (slice[si].type === 'ws') { si++; continue; }
          if ((slice[si].type === 'word' || slice[si].type === 'keyword') &&
              slice[si].val.toUpperCase() === parts[pi]) {
            pi++; si++;
          } else { match = false; break; }
        }
        if (match && pi === parts.length) {
          out.splice(i, si, { type: 'keyword', val: kw });
        }
      }
    }
    return out;
  }

  function formatSQL(sql, tabSize) {
    const indent = ' '.repeat(tabSize);
    const tokens = upperKeywords(tokenize(sql));
    const clauseSet = new Set(CLAUSE_KW);
    let result = '';
    let depth = 0;
    let firstToken = true;

    function pad() { return indent.repeat(depth); }

    for (let i = 0; i < tokens.length; i++) {
      const t = tokens[i];
      if (t.type === 'ws') continue;

      if (t.type === 'keyword' && clauseSet.has(t.val)) {
        if (!firstToken) result += '\n';
        result += pad() + t.val + ' ';
        firstToken = false;
        continue;
      }
      if (t.val === '(') {
        result += '(';
        depth++;
        let ni = i + 1;
        while (ni < tokens.length && tokens[ni].type === 'ws') ni++;
        if (ni < tokens.length && tokens[ni].val === 'SELECT') {
          result += '\n' + pad();
        }
        firstToken = false;
        continue;
      }
      if (t.val === ')') {
        depth = Math.max(0, depth - 1);
        result = result.trimEnd();
        result += '\n' + pad() + ')';
        firstToken = false;
        continue;
      }
      if (t.val === ',') {
        result = result.trimEnd();
        result += ',\n' + pad();
        firstToken = false;
        continue;
      }
      if (t.val === ';') {
        result = result.trimEnd();
        result += ';\n';
        firstToken = false;
        continue;
      }
      result += t.val;
      if (t.type !== 'punct') result += ' ';
      firstToken = false;
    }

    return result
      .split('\n')
      .map(l => l.trimEnd())
      .join('\n')
      .replace(/\n{3,}/g, '\n\n')
      .trim();
  }

  function minifySQL(sql) {
    const tokens = upperKeywords(tokenize(sql));
    return tokens
      .filter(t => t.type !== 'ws')
      .map((t, i, arr) => {
        const prev = arr[i-1];
        const needSpace = prev &&
          !['punct'].includes(prev.type) && !['punct'].includes(t.type) &&
          !(prev.val === '(') && !(t.val === ')') &&
          !(t.val === ',') && !(t.val === ';');
        return (needSpace ? ' ' : '') + t.val;
      })
      .join('')
      .trim();
  }

  function escapeHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function highlightSQL(text) {
    const tokens = upperKeywords(tokenize(text));
    return tokens.map(t => {
      const v = escapeHtml(t.val);
      switch (t.type) {
        case 'keyword': return '<span class="kw">' + v + '</span>';
        case 'string':  return '<span class="str">' + v + '</span>';
        case 'number':  return '<span class="num">' + v + '</span>';
        case 'comment': return '<span class="cmt">' + v + '</span>';
        default: return v;
      }
    }).join('');
  }

  const inputEl   = document.getElementById('sql-input');
  const outputEl  = document.getElementById('sql-output');
  const formatBtn = document.getElementById('sql-format-btn');
  const minifyBtn = document.getElementById('sql-minify-btn');
  const clearBtn  = document.getElementById('sql-clear-btn');
  const copyBtn   = document.getElementById('sql-copy-btn');
  const hlChk     = document.getElementById('sql-highlight-chk');
  const tabSel    = document.getElementById('sql-tabsize-sel');
  const statusEl  = document.getElementById('sql-status');

  let lastFormatted = '';

  function renderOutput(text, highlight) {
    lastFormatted = text;
    if (highlight) {
      outputEl.innerHTML = highlightSQL(text);
    } else {
      outputEl.textContent = text;
    }
  }

  function setStatus(msg, ok) {
    statusEl.textContent = msg;
    statusEl.style.color = ok === false ? '#f87171' : '#4ade80';
  }

  formatBtn.addEventListener('click', () => {
    const sql = inputEl.value.trim();
    if (!sql) { setStatus('入力欄にSQLを貼り付けてください。', false); return; }
    const tab = parseInt(tabSel.value, 10);
    try {
      renderOutput(formatSQL(sql, tab), hlChk.checked);
      setStatus('整形完了しました。');
    } catch(e) {
      setStatus('整形中にエラーが発生しました。', false);
    }
  });

  minifyBtn.addEventListener('click', () => {
    const sql = inputEl.value.trim();
    if (!sql) { setStatus('入力欄にSQLを貼り付けてください。', false); return; }
    try {
      renderOutput(minifySQL(sql), false);
      setStatus('ミニファイ完了しました。');
    } catch(e) {
      setStatus('ミニファイ中にエラーが発生しました。', false);
    }
  });

  clearBtn.addEventListener('click', () => {
    inputEl.value = '';
    outputEl.textContent = '';
    lastFormatted = '';
    statusEl.textContent = '';
  });

  copyBtn.addEventListener('click', () => {
    if (!lastFormatted) { setStatus('コピーする内容がありません。', false); return; }
    navigator.clipboard.writeText(lastFormatted).then(() => {
      copyBtn.textContent = 'コピー済み!';
      setStatus('クリップボードにコピーしました。');
      setTimeout(() => { copyBtn.textContent = 'コピー'; }, 1800);
    }).catch(() => {
      setStatus('コピーに失敗しました。手動で選択してコピーしてください。', false);
    });
  });

  hlChk.addEventListener('change', () => {
    if (lastFormatted) renderOutput(lastFormatted, hlChk.checked);
  });

  inputEl.value = "select u.id,u.name,o.total from users u inner join orders o on u.id=o.user_id where o.total>100 and u.active=1 order by o.total desc limit 10;";
})();
</script>
