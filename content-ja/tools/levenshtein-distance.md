---
title: "レーベンシュタイン距離計算ツール"
date: 2025-07-28
description: "無料の編集距離（レーベンシュタイン距離）計算ツール。2つの文字列間の編集距離を計算。挿入・削除・置換の操作をステップバイステップで表示。"
categories: ["無料ツール"]
slug: "levenshtein-distance"
ShowToc: false
cover:
  image: "/images/covers/levenshtein-distance-ja.png"
  alt: "レーベンシュタイン距離計算ツール"
---

2つの文字列を入力するだけで編集距離を即時計算。挿入・削除・置換の操作手順をステップごとに表示し、DPテーブルの可視化やバッチ比較にも対応。すべてブラウザ内で完結します。

<div id="ld-app">
<style>
#ld-app *,
#ld-app *::before,
#ld-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#ld-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.6;
}
#ld-app .ld-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 18px 20px;
  margin-bottom: 16px;
}
#ld-app .ld-row {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}
#ld-app .ld-col {
  flex: 1;
  min-width: 180px;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
#ld-app label.ld-label {
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#ld-app input.ld-input {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 15px;
  font-family: "SF Mono", "Fira Code", Consolas, monospace;
  color: #1e293b;
  background: #fff;
  outline: none;
  transition: border-color 0.15s, box-shadow 0.15s;
}
#ld-app input.ld-input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#ld-app .ld-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
}
#ld-app .ld-btn {
  padding: 7px 16px;
  border-radius: 7px;
  border: 1.5px solid #cbd5e1;
  background: #f8fafc;
  color: #334155;
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
}
#ld-app .ld-btn:hover {
  background: #f1f5f9;
  border-color: #94a3b8;
}
#ld-app .ld-btn-primary {
  background: #6366f1;
  border-color: #6366f1;
  color: #fff;
  font-weight: 600;
}
#ld-app .ld-btn-primary:hover {
  background: #4f46e5;
  border-color: #4f46e5;
}
#ld-app label.ld-check {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 13px;
  color: #475569;
  cursor: pointer;
  user-select: none;
}
#ld-app label.ld-check input[type="checkbox"] {
  width: 15px;
  height: 15px;
  accent-color: #6366f1;
  cursor: pointer;
}
#ld-app .ld-result-banner {
  display: none;
  gap: 20px;
  flex-wrap: wrap;
  background: linear-gradient(135deg, #eef2ff 0%, #f0fdf4 100%);
  border: 1.5px solid #c7d2fe;
  border-radius: 10px;
  padding: 16px 20px;
  margin-bottom: 16px;
}
#ld-app .ld-result-banner.show { display: flex; }
#ld-app .ld-stat {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  min-width: 80px;
}
#ld-app .ld-stat-num {
  font-size: 28px;
  font-weight: 700;
  color: #4f46e5;
  line-height: 1;
}
#ld-app .ld-stat-label {
  font-size: 11px;
  color: #64748b;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.03em;
  text-align: center;
}
#ld-app .ld-sim-bar-wrap {
  margin-top: 8px;
  background: #e2e8f0;
  border-radius: 99px;
  height: 8px;
  overflow: hidden;
}
#ld-app .ld-sim-bar {
  height: 100%;
  border-radius: 99px;
  background: linear-gradient(90deg, #6366f1, #22c55e);
  transition: width 0.4s ease;
  width: 0%;
}
#ld-app .ld-section-title {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 10px;
}
#ld-app .ld-steps {
  display: none;
  flex-direction: column;
  gap: 6px;
  max-height: 280px;
  overflow-y: auto;
  padding-right: 4px;
}
#ld-app .ld-steps.show { display: flex; }
#ld-app .ld-step {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  padding: 8px 12px;
  border-radius: 7px;
  border-left: 4px solid transparent;
  background: #f8fafc;
  font-size: 13px;
}
#ld-app .ld-step.ins { border-left-color: #22c55e; background: #f0fdf4; }
#ld-app .ld-step.del { border-left-color: #ef4444; background: #fef2f2; }
#ld-app .ld-step.sub { border-left-color: #f59e0b; background: #fffbeb; }
#ld-app .ld-step.eq  { border-left-color: #cbd5e1; }
#ld-app .ld-step-icon { font-weight: 700; font-size: 14px; min-width: 18px; }
#ld-app .ld-step-text { color: #334155; line-height: 1.5; }
#ld-app .ld-step-text code {
  font-family: "SF Mono", "Fira Code", Consolas, monospace;
  background: rgba(0,0,0,0.06);
  padding: 1px 5px;
  border-radius: 4px;
  font-size: 12px;
}
#ld-app .ld-matrix-wrap {
  display: none;
  overflow-x: auto;
  margin-top: 4px;
}
#ld-app .ld-matrix-wrap.show { display: block; }
#ld-app .ld-matrix-table {
  border-collapse: collapse;
  font-family: "SF Mono", "Fira Code", Consolas, monospace;
  font-size: 12px;
}
#ld-app .ld-matrix-table th,
#ld-app .ld-matrix-table td {
  width: 32px;
  height: 32px;
  text-align: center;
  vertical-align: middle;
  border: 1px solid #e2e8f0;
}
#ld-app .ld-matrix-table th {
  background: #f1f5f9;
  color: #64748b;
  font-weight: 700;
  font-size: 11px;
}
#ld-app .ld-matrix-table td {
  background: #fff;
  color: #1e293b;
}
#ld-app .ld-matrix-table td.ld-path {
  background: #eef2ff;
  color: #4f46e5;
  font-weight: 700;
}
#ld-app .ld-matrix-table td.ld-path-end {
  background: #6366f1;
  color: #fff;
  font-weight: 700;
}
#ld-app .ld-batch-area {
  width: 100%;
  min-height: 100px;
  padding: 10px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-family: "SF Mono", "Fira Code", Consolas, monospace;
  font-size: 13px;
  resize: vertical;
  outline: none;
  color: #1e293b;
  background: #fff;
  transition: border-color 0.15s, box-shadow 0.15s;
}
#ld-app .ld-batch-area:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
#ld-app .ld-batch-results {
  display: none;
  flex-direction: column;
  gap: 6px;
  margin-top: 10px;
}
#ld-app .ld-batch-results.show { display: flex; }
#ld-app .ld-batch-row {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 8px 12px;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 7px;
  font-size: 13px;
  flex-wrap: wrap;
}
#ld-app .ld-batch-pair {
  font-family: "SF Mono", "Fira Code", Consolas, monospace;
  color: #475569;
  flex: 1;
  min-width: 120px;
}
#ld-app .ld-batch-dist {
  font-weight: 700;
  color: #4f46e5;
  min-width: 90px;
  text-align: right;
}
#ld-app .ld-batch-sim {
  color: #16a34a;
  font-weight: 600;
  min-width: 70px;
  text-align: right;
}
#ld-app .ld-tab-row {
  display: flex;
  gap: 4px;
  margin-bottom: 14px;
  border-bottom: 2px solid #e2e8f0;
}
#ld-app .ld-tab {
  padding: 8px 16px;
  font-size: 13px;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  border: none;
  background: none;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
}
#ld-app .ld-tab.active {
  color: #6366f1;
  border-bottom-color: #6366f1;
}
#ld-app .ld-tab-panel { display: none; }
#ld-app .ld-tab-panel.active { display: block; }
#ld-app .ld-hint {
  font-size: 12px;
  color: #94a3b8;
  margin-top: 5px;
}
#ld-app .ld-empty {
  color: #94a3b8;
  font-size: 13px;
  text-align: center;
  padding: 20px 0;
}
#ld-app .ld-error {
  color: #dc2626;
  font-size: 13px;
  padding: 8px 12px;
  background: #fef2f2;
  border-radius: 7px;
  border: 1px solid #fecaca;
}
</style>

<!-- タブナビゲーション -->
<div class="ld-tab-row">
  <button class="ld-tab active" data-tab="single">1ペア比較</button>
  <button class="ld-tab" data-tab="batch">バッチ比較</button>
</div>

<!-- ===== 1ペア比較タブ ===== -->
<div class="ld-tab-panel active" id="ld-tab-single">

  <div class="ld-card">
    <div class="ld-row" style="margin-bottom:14px;">
      <div class="ld-col">
        <label class="ld-label" for="ld-str1">文字列 A</label>
        <input class="ld-input" id="ld-str1" type="text" placeholder="例：kitten" autocomplete="off" spellcheck="false">
      </div>
      <div class="ld-col">
        <label class="ld-label" for="ld-str2">文字列 B</label>
        <input class="ld-input" id="ld-str2" type="text" placeholder="例：sitting" autocomplete="off" spellcheck="false">
      </div>
    </div>
    <div class="ld-toolbar">
      <button class="ld-btn ld-btn-primary" id="ld-calc-btn">計算する</button>
      <button class="ld-btn" id="ld-swap-btn">&#8646; 入れ替え</button>
      <button class="ld-btn" id="ld-clear-btn">クリア</button>
      <label class="ld-check">
        <input type="checkbox" id="ld-case-toggle"> 大文字/小文字を区別する
      </label>
      <label class="ld-check">
        <input type="checkbox" id="ld-matrix-toggle"> DPテーブルを表示
      </label>
    </div>
  </div>

  <!-- 結果バナー -->
  <div class="ld-result-banner" id="ld-banner">
    <div class="ld-stat">
      <span class="ld-stat-num" id="ld-dist-num">—</span>
      <span class="ld-stat-label">編集距離</span>
    </div>
    <div class="ld-stat">
      <span class="ld-stat-num" id="ld-sim-num">—</span>
      <span class="ld-stat-label">類似度</span>
    </div>
    <div class="ld-stat">
      <span class="ld-stat-num" id="ld-ins-num" style="color:#16a34a;">0</span>
      <span class="ld-stat-label">挿入</span>
    </div>
    <div class="ld-stat">
      <span class="ld-stat-num" id="ld-del-num" style="color:#dc2626;">0</span>
      <span class="ld-stat-label">削除</span>
    </div>
    <div class="ld-stat">
      <span class="ld-stat-num" id="ld-sub-num" style="color:#d97706;">0</span>
      <span class="ld-stat-label">置換</span>
    </div>
    <div style="flex:1;min-width:140px;display:flex;flex-direction:column;justify-content:center;">
      <div style="font-size:11px;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:0.04em;margin-bottom:5px;">類似度</div>
      <div class="ld-sim-bar-wrap"><div class="ld-sim-bar" id="ld-sim-bar"></div></div>
    </div>
  </div>

  <!-- ステップ説明 -->
  <div class="ld-card" id="ld-steps-card" style="display:none;">
    <div class="ld-section-title">編集操作のステップバイステップ</div>
    <div class="ld-steps show" id="ld-steps"></div>
  </div>

  <!-- DPテーブル -->
  <div class="ld-card" id="ld-matrix-card" style="display:none;">
    <div class="ld-section-title">動的計画法テーブル <span style="font-size:11px;font-weight:400;color:#94a3b8;">（ハイライト = 最適経路）</span></div>
    <div class="ld-matrix-wrap show" id="ld-matrix"></div>
  </div>

</div>

<!-- ===== バッチ比較タブ ===== -->
<div class="ld-tab-panel" id="ld-tab-batch">
  <div class="ld-card">
    <div class="ld-section-title" style="margin-bottom:8px;">バッチ比較</div>
    <p class="ld-hint" style="margin-bottom:10px;">1行に1ペア、カンマ区切りで入力してください：<code style="font-family:monospace;background:#f1f5f9;padding:1px 5px;border-radius:3px;">文字列1,文字列2</code></p>
    <textarea class="ld-batch-area" id="ld-batch-input" placeholder="kitten,sitting&#10;sunday,saturday&#10;hello,hallo&#10;東京,東宝"></textarea>
    <div style="margin-top:10px;display:flex;gap:8px;flex-wrap:wrap;">
      <button class="ld-btn ld-btn-primary" id="ld-batch-btn">すべて比較</button>
      <button class="ld-btn" id="ld-batch-clear-btn">クリア</button>
      <label class="ld-check">
        <input type="checkbox" id="ld-batch-case"> 大文字/小文字を区別する
      </label>
    </div>
    <div class="ld-batch-results" id="ld-batch-results"></div>
  </div>
</div>

<script>
(function () {
  'use strict';

  /* ── コア：レーベンシュタイン距離 ── */
  function buildMatrix(a, b) {
    var m = a.length, n = b.length;
    var dp = [];
    for (var i = 0; i <= m; i++) {
      dp[i] = [];
      for (var j = 0; j <= n; j++) {
        if (i === 0) { dp[i][j] = j; }
        else if (j === 0) { dp[i][j] = i; }
        else if (a[i - 1] === b[j - 1]) { dp[i][j] = dp[i - 1][j - 1]; }
        else { dp[i][j] = 1 + Math.min(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1]); }
      }
    }
    return dp;
  }

  function traceback(dp, a, b) {
    var ops = [];
    var i = a.length, j = b.length;
    while (i > 0 || j > 0) {
      if (i > 0 && j > 0 && a[i - 1] === b[j - 1]) {
        ops.unshift({ type: 'eq', ch: a[i - 1] });
        i--; j--;
      } else if (j > 0 && (i === 0 || dp[i][j - 1] <= dp[i - 1][j] && dp[i][j - 1] <= dp[i - 1][j - 1])) {
        ops.unshift({ type: 'ins', ch: b[j - 1], pos: j - 1 });
        j--;
      } else if (i > 0 && (j === 0 || dp[i - 1][j] <= dp[i][j - 1] && dp[i - 1][j] <= dp[i - 1][j - 1])) {
        ops.unshift({ type: 'del', ch: a[i - 1], pos: i - 1 });
        i--;
      } else {
        ops.unshift({ type: 'sub', from: a[i - 1], to: b[j - 1] });
        i--; j--;
      }
    }
    return ops;
  }

  function levenshtein(a, b) {
    var dp = buildMatrix(a, b);
    var dist = dp[a.length][b.length];
    var ops = traceback(dp, a, b);
    var ins = 0, del = 0, sub = 0;
    for (var k = 0; k < ops.length; k++) {
      if (ops[k].type === 'ins') ins++;
      else if (ops[k].type === 'del') del++;
      else if (ops[k].type === 'sub') sub++;
    }
    var maxLen = Math.max(a.length, b.length);
    var sim = maxLen === 0 ? 100 : Math.round((1 - dist / maxLen) * 100);
    return { dist: dist, sim: sim, ins: ins, del: del, sub: sub, ops: ops, dp: dp };
  }

  /* ── 文字列エスケープ ── */
  function esc(s) {
    return s.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
  }

  /* ── ステップ描画 ── */
  function renderSteps(ops) {
    if (ops.length === 0) return '<p class="ld-empty">2つの文字列は同一です。操作は不要です。</p>';
    var html = '';
    var step = 0;
    for (var k = 0; k < ops.length; k++) {
      var op = ops[k];
      if (op.type === 'eq') {
        html += '<div class="ld-step eq"><span class="ld-step-icon" style="color:#94a3b8;">=</span><span class="ld-step-text"><code>' + esc(op.ch) + '</code> はそのまま保持</span></div>';
      } else if (op.type === 'ins') {
        step++;
        html += '<div class="ld-step ins"><span class="ld-step-icon" style="color:#16a34a;">+</span><span class="ld-step-text"><strong>ステップ ' + step + '：</strong><code>' + esc(op.ch) + '</code> を挿入</span></div>';
      } else if (op.type === 'del') {
        step++;
        html += '<div class="ld-step del"><span class="ld-step-icon" style="color:#dc2626;">−</span><span class="ld-step-text"><strong>ステップ ' + step + '：</strong><code>' + esc(op.ch) + '</code> を削除</span></div>';
      } else if (op.type === 'sub') {
        step++;
        html += '<div class="ld-step sub"><span class="ld-step-icon" style="color:#d97706;">~</span><span class="ld-step-text"><strong>ステップ ' + step + '：</strong><code>' + esc(op.from) + '</code> → <code>' + esc(op.to) + '</code> に置換</span></div>';
      }
    }
    return html;
  }

  /* ── DPテーブル描画 ── */
  function renderMatrix(dp, a, b) {
    var pathSet = {};
    var i = a.length, j = b.length;
    pathSet[i + ',' + j] = true;
    while (i > 0 || j > 0) {
      if (i > 0 && j > 0 && a[i - 1] === b[j - 1]) { i--; j--; }
      else if (j > 0 && (i === 0 || dp[i][j - 1] <= dp[i - 1][j] && dp[i][j - 1] <= dp[i - 1][j - 1])) { j--; }
      else if (i > 0 && (j === 0 || dp[i - 1][j] <= dp[i][j - 1] && dp[i - 1][j] <= dp[i - 1][j - 1])) { i--; }
      else { i--; j--; }
      pathSet[i + ',' + j] = true;
    }
    var html = '<table class="ld-matrix-table"><thead><tr><th></th><th style="background:#e0e7ff;color:#4f46e5;">ε</th>';
    for (var jj = 0; jj < b.length; jj++) {
      html += '<th style="background:#e0e7ff;color:#4f46e5;">' + esc(b[jj]) + '</th>';
    }
    html += '</tr></thead><tbody>';
    for (var ii = 0; ii <= a.length; ii++) {
      html += '<tr>';
      if (ii === 0) html += '<th style="background:#e0e7ff;color:#4f46e5;">ε</th>';
      else html += '<th style="background:#e0e7ff;color:#4f46e5;">' + esc(a[ii - 1]) + '</th>';
      for (var jj2 = 0; jj2 <= b.length; jj2++) {
        var key = ii + ',' + jj2;
        var isEnd = (ii === a.length && jj2 === b.length);
        var cls = isEnd ? 'ld-path-end' : (pathSet[key] ? 'ld-path' : '');
        html += '<td class="' + cls + '">' + dp[ii][jj2] + '</td>';
      }
      html += '</tr>';
    }
    html += '</tbody></table>';
    return html;
  }

  /* ── 1ペア計算 ── */
  function calculate() {
    var rawA = document.getElementById('ld-str1').value;
    var rawB = document.getElementById('ld-str2').value;
    var caseSensitive = document.getElementById('ld-case-toggle').checked;
    var a = caseSensitive ? rawA : rawA.toLowerCase();
    var b = caseSensitive ? rawB : rawB.toLowerCase();

    var result = levenshtein(a, b);

    var banner = document.getElementById('ld-banner');
    banner.classList.add('show');
    document.getElementById('ld-dist-num').textContent = result.dist;
    document.getElementById('ld-sim-num').textContent = result.sim + '%';
    document.getElementById('ld-ins-num').textContent = result.ins;
    document.getElementById('ld-del-num').textContent = result.del;
    document.getElementById('ld-sub-num').textContent = result.sub;
    document.getElementById('ld-sim-bar').style.width = result.sim + '%';

    var stepsCard = document.getElementById('ld-steps-card');
    stepsCard.style.display = 'block';
    document.getElementById('ld-steps').innerHTML = renderSteps(result.ops);

    var showMatrix = document.getElementById('ld-matrix-toggle').checked;
    var matrixCard = document.getElementById('ld-matrix-card');
    if (showMatrix && a.length <= 20 && b.length <= 20) {
      matrixCard.style.display = 'block';
      document.getElementById('ld-matrix').innerHTML = renderMatrix(result.dp, a, b);
    } else if (showMatrix && (a.length > 20 || b.length > 20)) {
      matrixCard.style.display = 'block';
      document.getElementById('ld-matrix').innerHTML = '<p class="ld-hint" style="color:#f59e0b;">DPテーブルは20文字以内の文字列のみ表示できます。</p>';
    } else {
      matrixCard.style.display = 'none';
    }
  }

  /* ── バッチ計算 ── */
  function calculateBatch() {
    var raw = document.getElementById('ld-batch-input').value.trim();
    var caseSensitive = document.getElementById('ld-batch-case').checked;
    var resultsEl = document.getElementById('ld-batch-results');
    if (!raw) {
      resultsEl.innerHTML = '';
      resultsEl.classList.remove('show');
      return;
    }
    var lines = raw.split('\n');
    var html = '';
    var hasResult = false;
    for (var i = 0; i < lines.length; i++) {
      var line = lines[i].trim();
      if (!line) continue;
      var parts = line.split(',');
      if (parts.length < 2) {
        html += '<div class="ld-error">' + (i + 1) + '行目：形式が正しくありません。「文字列1,文字列2」の形式で入力してください。</div>';
        continue;
      }
      var rawA = parts[0].trim();
      var rawB = parts.slice(1).join(',').trim();
      var a = caseSensitive ? rawA : rawA.toLowerCase();
      var b = caseSensitive ? rawB : rawB.toLowerCase();
      var r = levenshtein(a, b);
      hasResult = true;
      html += '<div class="ld-batch-row">'
        + '<span class="ld-batch-pair">' + esc(rawA) + ' ↔ ' + esc(rawB) + '</span>'
        + '<span class="ld-batch-dist">距離：' + r.dist + '</span>'
        + '<span class="ld-batch-sim">' + r.sim + '% 類似</span>'
        + '<span style="font-size:12px;color:#64748b;">挿入+' + r.ins + ' 削除−' + r.del + ' 置換~' + r.sub + '</span>'
        + '</div>';
    }
    if (!hasResult && !html) {
      resultsEl.innerHTML = '';
      resultsEl.classList.remove('show');
      return;
    }
    resultsEl.innerHTML = html;
    resultsEl.classList.add('show');
  }

  /* ── タブ切り替え ── */
  document.querySelectorAll('#ld-app .ld-tab').forEach(function (tab) {
    tab.addEventListener('click', function () {
      document.querySelectorAll('#ld-app .ld-tab').forEach(function (t) { t.classList.remove('active'); });
      document.querySelectorAll('#ld-app .ld-tab-panel').forEach(function (p) { p.classList.remove('active'); });
      tab.classList.add('active');
      document.getElementById('ld-tab-' + tab.dataset.tab).classList.add('active');
    });
  });

  /* ── イベントリスナー ── */
  document.getElementById('ld-calc-btn').addEventListener('click', calculate);

  document.getElementById('ld-swap-btn').addEventListener('click', function () {
    var a = document.getElementById('ld-str1');
    var b = document.getElementById('ld-str2');
    var tmp = a.value;
    a.value = b.value;
    b.value = tmp;
  });

  document.getElementById('ld-clear-btn').addEventListener('click', function () {
    document.getElementById('ld-str1').value = '';
    document.getElementById('ld-str2').value = '';
    document.getElementById('ld-banner').classList.remove('show');
    document.getElementById('ld-steps-card').style.display = 'none';
    document.getElementById('ld-matrix-card').style.display = 'none';
  });

  document.getElementById('ld-matrix-toggle').addEventListener('change', function () {
    if (document.getElementById('ld-banner').classList.contains('show')) calculate();
  });

  var debounceTimer;
  function maybeAutoRun() {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(function () {
      if (document.getElementById('ld-str1').value || document.getElementById('ld-str2').value) {
        calculate();
      }
    }, 400);
  }
  document.getElementById('ld-str1').addEventListener('input', maybeAutoRun);
  document.getElementById('ld-str2').addEventListener('input', maybeAutoRun);

  document.getElementById('ld-batch-btn').addEventListener('click', calculateBatch);
  document.getElementById('ld-batch-clear-btn').addEventListener('click', function () {
    document.getElementById('ld-batch-input').value = '';
    var r = document.getElementById('ld-batch-results');
    r.innerHTML = '';
    r.classList.remove('show');
  });

  /* サンプルを事前入力 */
  document.getElementById('ld-str1').value = 'kitten';
  document.getElementById('ld-str2').value = 'sitting';
  calculate();
})();
</script>
</div>

---

<div class="df-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">開発・研究ツールの経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、ソフトウェア・サーバー費用の経費精算もクラウドで一元管理。確定申告もスムーズに。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:8px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

## レーベンシュタイン距離とは？

**レーベンシュタイン距離**（編集距離）とは、ある文字列を別の文字列に変換するために必要な**挿入・削除・置換**の最小操作回数です。1965年にロシアの数学者ウラジーミル・レーベンシュタインが考案しました。

有名な例：**"kitten"** を **"sitting"** に変換するには3回の操作が必要 → 編集距離 **3**

| 操作 | 例 | コスト |
|---|---|---|
| 置換 | k → s（kitten → sitten） | 1 |
| 置換 | e → i（sitten → sittin） | 1 |
| 挿入 | sittin → sitting | 1 |

**類似度（%）** は `(1 − 距離 / max(len_A, len_B)) × 100` で計算します。

---

## 動的計画法による計算の仕組み

サイズ `(m+1) × (n+1)` の行列を構築します（`m`, `n` は各文字列の長さ）。各セル `dp[i][j]` は「文字列Aの最初の`i`文字」と「文字列Bの最初の`j`文字」の間の最小編集距離を保持します。

漸化式：

- `A[i] == B[j]` の場合：`dp[i][j] = dp[i-1][j-1]`（コストなし）
- それ以外：`dp[i][j] = 1 + min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1])`（置換・削除・挿入）

`dp[m][n]` からトレースバックすることで、具体的な操作手順を復元します。

---

## 主な活用例

| 分野 | 活用方法 |
|---|---|
| スペルチェッカー | 辞書内の最近傍単語を特定 |
| DNA配列解析 | 遺伝子配列の類似度を計測 |
| あいまい検索 | 検索結果を類似度でランク付け |
| 盗用検出 | ほぼ同一の文章を発見 |
| データ統合 | 重複レコードの名寄せ |
| 自動補正 | ユーザーの意図した単語を推定 |
| 自然言語処理 | テキスト類似度の特徴量として利用 |

---

## 使い方・ヒント

- **大文字/小文字の区別** — デフォルトは区別なし。コード識別子やパスワード比較時は有効化してください。
- **DPテーブル表示** — 「DPテーブルを表示」を有効にすると、動的計画法の行列と最適経路（ハイライト）を確認できます。20文字以内の文字列のみ対応。
- **バッチ比較** — `文字列1,文字列2` の形式で複数ペアをまとめて比較できます。しきい値の検証などに便利です。
- **入れ替え** — AとBを一発で入れ替えます。レーベンシュタイン距離は対称なので `d(A,B) == d(B,A)` です。
- **日本語対応** — ひらがな・カタカナ・漢字も1文字単位で計算します。

---

> テキストを行単位で比較する → [テキスト差分比較ツール](/ja/tools/text-diff-checker/)

> 文字数・単語数をカウントする → [文字数カウンター](/ja/tools/moji-counter/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
