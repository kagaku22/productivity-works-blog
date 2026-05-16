---
title: "タイムゾーン会議プランナー"
date: 2025-05-16
description: "無料のタイムゾーン会議調整ツール。複数のタイムゾーンの参加者間で最適な会議時間を可視化。営業時間の重複をビジュアルタイムラインで表示。"
categories: ["無料ツール"]
tags: ["会議調整", "タイムゾーン", "世界時計", "スケジュール調整", "リモートワーク"]
slug: "meeting-planner"
cover:
  image: "/images/covers/meeting-planner-ja.png"
  alt: "タイムゾーン会議プランナー"
ShowToc: false
---

<div id="mp-app">

<style>
  #mp-app {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
    max-width: 860px;
    margin: 0 auto;
    padding: 16px;
    color: #1e1b4b;
  }

  #mp-app * { box-sizing: border-box; }

  #mp-app h2 {
    font-size: 1.05rem;
    font-weight: 700;
    margin: 0 0 10px;
    color: #1e1b4b;
  }

  #mp-app .mp-section {
    background: #f8f7ff;
    border: 1px solid #e0e7ff;
    border-radius: 10px;
    padding: 16px;
    margin-bottom: 16px;
  }

  #mp-app .mp-row {
    display: flex;
    gap: 8px;
    align-items: center;
    flex-wrap: wrap;
    margin-bottom: 8px;
  }

  #mp-app label {
    font-size: 0.82rem;
    font-weight: 600;
    color: #4b5563;
    white-space: nowrap;
  }

  #mp-app input[type="text"],
  #mp-app select {
    border: 1px solid #c7d2fe;
    border-radius: 6px;
    padding: 6px 10px;
    font-size: 0.85rem;
    background: #fff;
    color: #1e1b4b;
    outline: none;
  }

  #mp-app input[type="text"]:focus,
  #mp-app select:focus {
    border-color: #6366f1;
    box-shadow: 0 0 0 2px #e0e7ff;
  }

  #mp-app input[type="text"] { width: 140px; }
  #mp-app select { width: 260px; }

  #mp-app .mp-btn {
    background: #6366f1;
    color: #fff;
    border: none;
    border-radius: 6px;
    padding: 7px 14px;
    font-size: 0.82rem;
    font-weight: 600;
    cursor: pointer;
    white-space: nowrap;
  }

  #mp-app .mp-btn:hover { background: #4f46e5; }

  #mp-app .mp-btn-sm {
    background: transparent;
    color: #6366f1;
    border: 1px solid #6366f1;
    border-radius: 5px;
    padding: 3px 9px;
    font-size: 0.75rem;
    cursor: pointer;
    font-weight: 600;
  }

  #mp-app .mp-btn-sm:hover { background: #e0e7ff; }

  #mp-app .mp-btn-danger {
    background: transparent;
    color: #ef4444;
    border: 1px solid #fca5a5;
    border-radius: 5px;
    padding: 3px 9px;
    font-size: 0.75rem;
    cursor: pointer;
  }

  #mp-app .mp-btn-danger:hover { background: #fef2f2; }

  #mp-app .mp-presets {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 8px;
  }

  #mp-app .mp-preset-btn {
    background: #e0e7ff;
    color: #3730a3;
    border: none;
    border-radius: 5px;
    padding: 4px 10px;
    font-size: 0.75rem;
    cursor: pointer;
    font-weight: 600;
  }

  #mp-app .mp-preset-btn:hover { background: #c7d2fe; }

  #mp-app .mp-participant-list {
    display: flex;
    flex-direction: column;
    gap: 6px;
    margin-bottom: 10px;
  }

  #mp-app .mp-participant {
    display: flex;
    align-items: center;
    gap: 8px;
    background: #fff;
    border: 1px solid #e0e7ff;
    border-radius: 7px;
    padding: 7px 10px;
  }

  #mp-app .mp-color-dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  #mp-app .mp-p-name {
    font-size: 0.85rem;
    font-weight: 600;
    flex: 1;
  }

  #mp-app .mp-p-tz {
    font-size: 0.75rem;
    color: #6b7280;
    flex: 1;
  }

  #mp-app .mp-p-time {
    font-size: 0.78rem;
    color: #374151;
    font-family: monospace;
    min-width: 60px;
    text-align: right;
  }

  /* Timeline */
  #mp-app .mp-timeline-wrap {
    overflow-x: auto;
  }

  #mp-app .mp-timeline {
    min-width: 600px;
  }

  #mp-app .mp-tl-header {
    display: grid;
    grid-template-columns: 110px repeat(24, 1fr);
    margin-bottom: 2px;
  }

  #mp-app .mp-tl-hcell {
    font-size: 0.62rem;
    color: #9ca3af;
    text-align: center;
    padding: 1px 0;
  }

  #mp-app .mp-tl-row {
    display: grid;
    grid-template-columns: 110px repeat(24, 1fr);
    margin-bottom: 3px;
    align-items: center;
  }

  #mp-app .mp-tl-label {
    font-size: 0.72rem;
    font-weight: 600;
    color: #374151;
    padding-right: 6px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    line-height: 1.3;
  }

  #mp-app .mp-tl-label span {
    display: block;
    font-size: 0.62rem;
    font-weight: 400;
    color: #9ca3af;
  }

  #mp-app .mp-tl-cell {
    height: 28px;
    border-radius: 2px;
    cursor: pointer;
    position: relative;
    transition: filter 0.1s;
  }

  #mp-app .mp-tl-cell:hover { filter: brightness(0.88); }

  #mp-app .mp-tl-cell.cell-work    { background: #22c55e; }
  #mp-app .mp-tl-cell.cell-early   { background: #facc15; }
  #mp-app .mp-tl-cell.cell-night   { background: #6366f1; opacity: 0.25; }
  #mp-app .mp-tl-cell.cell-overlap { background: #10b981; border: 2px solid #059669; }
  #mp-app .mp-tl-cell.cell-selected { outline: 3px solid #f59e0b; outline-offset: -1px; }

  /* Overlap row */
  #mp-app .mp-tl-row.overlap-row .mp-tl-label {
    font-size: 0.7rem;
    color: #065f46;
    font-weight: 700;
  }

  #mp-app .mp-tl-row.overlap-row .mp-tl-cell.cell-overlap {
    height: 20px;
    border-radius: 3px;
  }

  #mp-app .mp-tl-row.overlap-row .mp-tl-cell.cell-no-overlap {
    background: #f3f4f6;
    height: 20px;
    border-radius: 3px;
  }

  /* Legend */
  #mp-app .mp-legend {
    display: flex;
    gap: 14px;
    flex-wrap: wrap;
    font-size: 0.75rem;
    color: #6b7280;
    margin-top: 10px;
  }

  #mp-app .mp-legend-item {
    display: flex;
    align-items: center;
    gap: 4px;
  }

  #mp-app .mp-legend-swatch {
    width: 14px;
    height: 14px;
    border-radius: 3px;
  }

  /* Suggestions */
  #mp-app .mp-suggestions {
    margin-top: 14px;
  }

  #mp-app .mp-suggestion-title {
    font-size: 0.85rem;
    font-weight: 700;
    color: #065f46;
    margin-bottom: 8px;
  }

  #mp-app .mp-suggestion-none {
    font-size: 0.82rem;
    color: #9ca3af;
    font-style: italic;
  }

  #mp-app .mp-slot {
    display: flex;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
    background: #ecfdf5;
    border: 1px solid #6ee7b7;
    border-radius: 7px;
    padding: 8px 12px;
    margin-bottom: 6px;
    font-size: 0.82rem;
  }

  #mp-app .mp-slot-utc {
    font-weight: 700;
    color: #065f46;
    white-space: nowrap;
  }

  #mp-app .mp-slot-times {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    flex: 1;
  }

  #mp-app .mp-slot-ptime {
    background: #fff;
    border: 1px solid #a7f3d0;
    border-radius: 5px;
    padding: 2px 8px;
    font-size: 0.78rem;
    white-space: nowrap;
  }

  /* Copy invite */
  #mp-app .mp-copy-wrap {
    margin-top: 14px;
  }

  #mp-app .mp-copy-area {
    width: 100%;
    border: 1px solid #c7d2fe;
    border-radius: 7px;
    padding: 10px;
    font-size: 0.8rem;
    font-family: monospace;
    background: #fff;
    color: #374151;
    resize: vertical;
    min-height: 80px;
  }

  #mp-app .mp-copy-row {
    display: flex;
    gap: 8px;
    align-items: center;
    margin-top: 6px;
    flex-wrap: wrap;
  }

  #mp-app .mp-copy-status {
    font-size: 0.78rem;
    color: #22c55e;
    display: none;
  }

  #mp-app .mp-tip {
    font-size: 0.78rem;
    color: #6b7280;
    margin-top: 6px;
    line-height: 1.5;
  }

  #mp-app .mp-no-p {
    font-size: 0.82rem;
    color: #9ca3af;
    font-style: italic;
    padding: 8px 0;
  }

  /* freee CTA */
  #mp-app .mp-freee-cta {
    background: #f0fdf4;
    border: 1px solid #bbf7d0;
    border-radius: 8px;
    padding: 14px 16px;
    font-size: 0.82rem;
    color: #166534;
    line-height: 1.6;
  }

  #mp-app .mp-freee-cta strong { color: #166534; }

  #mp-app .mp-freee-cta a {
    color: #15803d;
    font-weight: 700;
    text-decoration: underline;
  }

  @media (max-width: 540px) {
    #mp-app input[type="text"] { width: 110px; }
    #mp-app select { width: 200px; }
  }
</style>

<!-- Section 1: 参加者追加 -->
<div class="mp-section">
  <h2>参加者を追加</h2>

  <div class="mp-row">
    <label>名前：</label>
    <input type="text" id="mp-name" placeholder="例：田中さん" maxlength="24" />
    <label>タイムゾーン：</label>
    <select id="mp-tz"></select>
    <button class="mp-btn" id="mp-add-btn">+ 追加</button>
  </div>

  <div>
    <label style="font-size:0.78rem; color:#6b7280;">主要都市から選ぶ：</label>
    <div class="mp-presets" id="mp-presets"></div>
  </div>
</div>

<!-- Section 2: 参加者一覧 & タイムライン -->
<div class="mp-section">
  <h2>ビジュアルタイムライン <span style="font-weight:400; font-size:0.8rem; color:#6b7280;">— セルをクリックして会議時間を選択</span></h2>

  <div id="mp-participant-list" class="mp-participant-list">
    <div class="mp-no-p">参加者がいません。上から追加してください。</div>
  </div>

  <div class="mp-timeline-wrap">
    <div class="mp-timeline" id="mp-timeline"></div>
  </div>

  <div class="mp-legend">
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#10b981; border:2px solid #059669;"></div>
      <span>全員重複（9〜17時）</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#22c55e;"></div>
      <span>営業時間内（9〜17時）</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#facc15;"></div>
      <span>早朝・夕方（7〜9時 / 17〜20時）</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#6366f1; opacity:0.4;"></div>
      <span>夜間</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#f59e0b;"></div>
      <span>選択中のスロット</span>
    </div>
  </div>
</div>

<!-- Section 3: 最適な会議時間 -->
<div class="mp-section" id="mp-suggest-section">
  <h2>最適な会議時間</h2>
  <div class="mp-suggestions" id="mp-suggestions">
    <div class="mp-suggestion-none">参加者を追加すると候補時間が表示されます。</div>
  </div>
</div>

<!-- Section 4: 招待文コピー -->
<div class="mp-section" id="mp-invite-section">
  <h2>会議招待文を作成</h2>
  <div class="mp-tip">上のタイムラインまたは候補時間をクリックして選択すると、参加者全員向けの招待文が自動生成されます。</div>
  <div class="mp-copy-wrap">
    <textarea class="mp-copy-area" id="mp-invite-text" readonly placeholder="会議スロットを選択すると招待文が生成されます..."></textarea>
    <div class="mp-copy-row">
      <button class="mp-btn" id="mp-copy-btn">クリップボードにコピー</button>
      <span class="mp-copy-status" id="mp-copy-status">コピーしました！</span>
    </div>
  </div>
</div>

<script>
(function() {
  'use strict';

  const ZONES = [
    { value: 'UTC',                  label: 'UTC — 協定世界時', city: null },
    { value: 'America/Los_Angeles',  label: 'PST/PDT — ロサンゼルス / サンフランシスコ', city: 'ロサンゼルス' },
    { value: 'America/Denver',       label: 'MST/MDT — デンバー', city: null },
    { value: 'America/Chicago',      label: 'CST/CDT — シカゴ / ダラス', city: 'シカゴ' },
    { value: 'America/New_York',     label: 'EST/EDT — ニューヨーク / トロント', city: 'ニューヨーク' },
    { value: 'America/Sao_Paulo',    label: 'BRT — サンパウロ', city: 'サンパウロ' },
    { value: 'Europe/London',        label: 'GMT/BST — ロンドン', city: 'ロンドン' },
    { value: 'Europe/Paris',         label: 'CET/CEST — パリ / ベルリン', city: 'パリ' },
    { value: 'Europe/Helsinki',      label: 'EET/EEST — ヘルシンキ / キーウ', city: null },
    { value: 'Europe/Moscow',        label: 'MSK — モスクワ', city: 'モスクワ' },
    { value: 'Asia/Dubai',           label: 'GST — ドバイ', city: 'ドバイ' },
    { value: 'Asia/Karachi',         label: 'PKT — カラチ / イスラマバード', city: null },
    { value: 'Asia/Kolkata',         label: 'IST — ムンバイ / ニューデリー', city: 'ムンバイ' },
    { value: 'Asia/Dhaka',           label: 'BST — ダッカ', city: null },
    { value: 'Asia/Bangkok',         label: 'ICT — バンコク / ジャカルタ', city: 'バンコク' },
    { value: 'Asia/Singapore',       label: 'SGT — シンガポール / クアラルンプール', city: 'シンガポール' },
    { value: 'Asia/Shanghai',        label: 'CST — 北京 / 上海 / 台北', city: '北京' },
    { value: 'Asia/Tokyo',           label: 'JST — 東京 / 大阪', city: '東京' },
    { value: 'Asia/Seoul',           label: 'KST — ソウル', city: 'ソウル' },
    { value: 'Australia/Sydney',     label: 'AEST/AEDT — シドニー / メルボルン', city: 'シドニー' },
    { value: 'Pacific/Auckland',     label: 'NZST/NZDT — オークランド', city: 'オークランド' },
    { value: 'Pacific/Honolulu',     label: 'HST — ホノルル', city: 'ホノルル' },
  ];

  const COLORS = [
    '#6366f1','#f59e0b','#ef4444','#3b82f6','#8b5cf6',
    '#06b6d4','#ec4899','#14b8a6','#f97316','#84cc16'
  ];

  let participants = [];
  let selectedSlot = null;
  let clockTick = null;

  // --- タイムゾーン選択肢を構築 ---
  const tzSel = document.getElementById('mp-tz');
  ZONES.forEach(z => {
    const opt = document.createElement('option');
    opt.value = z.value;
    opt.textContent = z.label;
    tzSel.appendChild(opt);
  });
  // デフォルトをローカルTZに
  try {
    const local = Intl.DateTimeFormat().resolvedOptions().timeZone;
    if (ZONES.find(z => z.value === local)) tzSel.value = local;
    else tzSel.value = 'Asia/Tokyo';
  } catch(e) { tzSel.value = 'Asia/Tokyo'; }

  // --- 都市プリセット ---
  const presetsEl = document.getElementById('mp-presets');
  ZONES.filter(z => z.city).forEach(z => {
    const btn = document.createElement('button');
    btn.className = 'mp-preset-btn';
    btn.textContent = z.city;
    btn.addEventListener('click', () => {
      const nameEl = document.getElementById('mp-name');
      if (!nameEl.value.trim()) nameEl.value = z.city;
      tzSel.value = z.value;
    });
    presetsEl.appendChild(btn);
  });

  // --- 参加者追加 ---
  document.getElementById('mp-add-btn').addEventListener('click', addParticipant);
  document.getElementById('mp-name').addEventListener('keydown', e => {
    if (e.key === 'Enter') addParticipant();
  });

  function addParticipant() {
    const nameEl = document.getElementById('mp-name');
    const name = nameEl.value.trim() || tzSel.options[tzSel.selectedIndex].text.split('—')[1]?.trim().split('/')[0].trim() || '参加者';
    const tz = tzSel.value;
    if (participants.length >= 10) {
      alert('参加者は最大10名です。');
      return;
    }
    participants.push({
      id: Date.now(),
      name,
      tz,
      color: COLORS[participants.length % COLORS.length]
    });
    nameEl.value = '';
    render();
  }

  function removeParticipant(id) {
    participants = participants.filter(p => p.id !== id);
    selectedSlot = null;
    render();
  }

  // --- 時刻フォーマット ---
  function fmtTime(tz, date) {
    return date.toLocaleString('ja-JP', {
      timeZone: tz,
      hour: '2-digit',
      minute: '2-digit',
      hour12: false
    });
  }

  function fmtDateTime(tz, date) {
    return date.toLocaleString('ja-JP', {
      timeZone: tz,
      month: 'numeric',
      day: 'numeric',
      weekday: 'short',
      hour: '2-digit',
      minute: '2-digit',
      hour12: false
    });
  }

  function getLocalHour(tz, utcHour) {
    const now = new Date();
    now.setUTCHours(utcHour, 0, 0, 0);
    const hStr = now.toLocaleString('en-US', { timeZone: tz, hour: 'numeric', hour12: false });
    return parseInt(hStr);
  }

  function getShortLabel(tz) {
    const z = ZONES.find(z => z.value === tz);
    if (!z) return tz;
    return z.label.split('—')[0].trim();
  }

  function getLocationLabel(tz) {
    const z = ZONES.find(z => z.value === tz);
    if (!z) return '';
    const parts = z.label.split('—');
    return parts.slice(1).join('—').trim();
  }

  function cellClass(localH) {
    if (localH >= 9 && localH < 17) return 'cell-work';
    if ((localH >= 7 && localH < 9) || (localH >= 17 && localH < 20)) return 'cell-early';
    return 'cell-night';
  }

  // --- 描画 ---
  function render() {
    renderParticipantList();
    renderTimeline();
    renderSuggestions();
    renderInvite();
  }

  function renderParticipantList() {
    const el = document.getElementById('mp-participant-list');
    if (participants.length === 0) {
      el.innerHTML = '<div class="mp-no-p">参加者がいません。上から追加してください。</div>';
      return;
    }
    const now = new Date();
    el.innerHTML = participants.map(p => `
      <div class="mp-participant">
        <div class="mp-color-dot" style="background:${p.color};"></div>
        <div class="mp-p-name">${escHtml(p.name)}</div>
        <div class="mp-p-tz">${escHtml(getShortLabel(p.tz))} — ${escHtml(getLocationLabel(p.tz))}</div>
        <div class="mp-p-time" id="mp-ptime-${p.id}">${fmtTime(p.tz, now)}</div>
        <button class="mp-btn-danger" onclick="window._mpRemove(${p.id})">削除</button>
      </div>
    `).join('');
  }

  function renderTimeline() {
    const el = document.getElementById('mp-timeline');
    if (participants.length === 0) {
      el.innerHTML = '';
      return;
    }

    // 時間軸ヘッダー
    let html = '<div class="mp-tl-header"><div class="mp-tl-hcell"></div>';
    for (let h = 0; h < 24; h++) {
      html += `<div class="mp-tl-hcell">${String(h).padStart(2,'0')}</div>`;
    }
    html += '</div>';

    // 全員の営業時間重複を計算
    const overlapHours = [];
    for (let h = 0; h < 24; h++) {
      const allWork = participants.every(p => {
        const lh = getLocalHour(p.tz, h);
        return lh >= 9 && lh < 17;
      });
      overlapHours.push(allWork);
    }

    // 参加者ごとの行
    participants.forEach(p => {
      html += `<div class="mp-tl-row">`;
      html += `<div class="mp-tl-label">${escHtml(p.name)}<span>${escHtml(getShortLabel(p.tz))}</span></div>`;
      for (let h = 0; h < 24; h++) {
        const lh = getLocalHour(p.tz, h);
        let cls = overlapHours[h] ? 'cell-overlap' : cellClass(lh);
        if (selectedSlot === h) cls += ' cell-selected';
        const lhFmt = String(lh).padStart(2,'0') + ':00';
        html += `<div class="mp-tl-cell ${cls}" title="${escHtml(p.name)}: ${lhFmt}" data-hour="${h}" onclick="window._mpSelectSlot(${h})"></div>`;
      }
      html += '</div>';
    });

    // 重複まとめ行
    html += `<div class="mp-tl-row overlap-row">`;
    html += `<div class="mp-tl-label" style="color:#065f46;">全員重複<span>ベスト時間</span></div>`;
    for (let h = 0; h < 24; h++) {
      let cls = overlapHours[h] ? 'cell-overlap' : 'cell-no-overlap';
      if (selectedSlot === h) cls += ' cell-selected';
      html += `<div class="mp-tl-cell ${cls}" title="UTC ${String(h).padStart(2,'0')}:00${overlapHours[h] ? ' ✓ 全員営業時間内' : ''}" data-hour="${h}" onclick="window._mpSelectSlot(${h})"></div>`;
    }
    html += '</div>';

    el.innerHTML = html;
  }

  function renderSuggestions() {
    const el = document.getElementById('mp-suggestions');
    if (participants.length === 0) {
      el.innerHTML = '<div class="mp-suggestion-none">参加者を追加すると候補時間が表示されます。</div>';
      return;
    }

    // 全員9〜17時の重複
    const overlapHours = [];
    for (let h = 0; h < 24; h++) {
      const allWork = participants.every(p => {
        const lh = getLocalHour(p.tz, h);
        return lh >= 9 && lh < 17;
      });
      if (allWork) overlapHours.push(h);
    }

    // 緩和条件（7〜20時）
    const relaxedHours = [];
    if (overlapHours.length === 0) {
      for (let h = 0; h < 24; h++) {
        const allOk = participants.every(p => {
          const lh = getLocalHour(p.tz, h);
          return lh >= 7 && lh < 20;
        });
        if (allOk) relaxedHours.push(h);
      }
    }

    const hours = overlapHours.length > 0 ? overlapHours : relaxedHours;

    if (hours.length === 0) {
      el.innerHTML = `
        <div class="mp-suggestion-none">
          全参加者の営業時間が重複する時間帯が見つかりませんでした。<br>
          タイムゾーンの組み合わせを見直すか、非同期コミュニケーションをご検討ください。
        </div>`;
      return;
    }

    // 連続した時間帯をスロットにまとめる
    const slots = [];
    let start = hours[0], end = hours[0];
    for (let i = 1; i < hours.length; i++) {
      if (hours[i] === hours[i-1] + 1) {
        end = hours[i];
      } else {
        slots.push({ start, end });
        start = hours[i]; end = hours[i];
      }
    }
    slots.push({ start, end });

    const quality = overlapHours.length > 0
      ? `最適な重複時間帯（全員9〜17時） — ${hours.length}時間`
      : `拡張重複時間帯（7〜20時、一部早朝・夕方） — ${hours.length}時間`;

    let html = `<div class="mp-suggestion-title">${quality}</div>`;

    slots.forEach(slot => {
      const now = new Date();
      now.setUTCHours(slot.start, 0, 0, 0);
      const endDate = new Date(now);
      endDate.setUTCHours(slot.end + 1, 0, 0, 0);

      html += `<div class="mp-slot" onclick="window._mpSelectSlot(${slot.start})" style="cursor:pointer;">`;
      html += `<div class="mp-slot-utc">UTC ${String(slot.start).padStart(2,'0')}:00〜${String(slot.end+1).padStart(2,'0')}:00</div>`;
      html += `<div class="mp-slot-times">`;
      participants.forEach(p => {
        html += `<div class="mp-slot-ptime" style="border-color:${p.color};">
          <strong>${escHtml(p.name)}</strong>: ${fmtTime(p.tz, now)}〜${fmtTime(p.tz, endDate)}
        </div>`;
      });
      html += `</div></div>`;
    });

    el.innerHTML = html;
  }

  function renderInvite() {
    const el = document.getElementById('mp-invite-text');
    if (participants.length === 0 || selectedSlot === null) {
      el.value = '';
      return;
    }
    const h = selectedSlot;
    const now = new Date();
    now.setUTCHours(h, 0, 0, 0);
    const endDate = new Date(now);
    endDate.setUTCHours(h + 1, 0, 0, 0);

    let text = `会議のご案内\n`;
    text += `============\n`;
    text += `UTC: ${String(h).padStart(2,'0')}:00 〜 ${String(h+1).padStart(2,'0')}:00\n\n`;
    text += `参加者ごとの現地時間：\n`;
    participants.forEach(p => {
      text += `  ${p.name}（${getShortLabel(p.tz)}）: ${fmtDateTime(p.tz, now)}\n`;
    });
    text += `\nタイムゾーン会議プランナーで作成\nhttps://productivity.works/ja/tools/meeting-planner/`;
    el.value = text;
  }

  // --- 現在時刻の更新 ---
  function startClock() {
    if (clockTick) clearInterval(clockTick);
    clockTick = setInterval(() => {
      if (participants.length === 0) return;
      const now = new Date();
      participants.forEach(p => {
        const el = document.getElementById(`mp-ptime-${p.id}`);
        if (el) el.textContent = fmtTime(p.tz, now);
      });
    }, 10000);
  }

  // --- スロット選択 ---
  window._mpSelectSlot = function(h) {
    selectedSlot = (selectedSlot === h) ? null : h;
    renderTimeline();
    renderInvite();
  };

  window._mpRemove = function(id) {
    removeParticipant(id);
  };

  // --- コピー ---
  document.getElementById('mp-copy-btn').addEventListener('click', () => {
    const ta = document.getElementById('mp-invite-text');
    if (!ta.value) return;
    navigator.clipboard.writeText(ta.value).then(() => {
      const st = document.getElementById('mp-copy-status');
      st.style.display = 'inline';
      setTimeout(() => { st.style.display = 'none'; }, 2000);
    }).catch(() => {
      ta.select();
      document.execCommand('copy');
    });
  });

  function escHtml(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  // --- 初期化：ローカルTZの参加者を自動追加 ---
  (function init() {
    try {
      const local = Intl.DateTimeFormat().resolvedOptions().timeZone;
      const z = ZONES.find(z => z.value === local) || ZONES.find(z => z.value === 'Asia/Tokyo');
      if (z) {
        participants.push({
          id: Date.now(),
          name: z.city || '自分',
          tz: z.value,
          color: COLORS[0]
        });
      }
    } catch(e) {}
    render();
    startClock();
  })();
})();
</script>

</div>

---

**関連ツール：** [ワールドクロック](/ja/tools/world-clock/) | [タイムゾーン変換ツール](/ja/tools/timezone-converter/)

---

**海外取引の会計管理にはfreee**
海外クライアントや外国人メンバーとの取引がある方、freeeなら外貨取引・請求書発行も簡単に管理できます。
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>

<small>※本リンクはアフィリエイトリンクです。</small>
