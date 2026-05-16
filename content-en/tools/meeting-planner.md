---
title: "Timezone Meeting Planner"
date: 2025-05-16
description: "Free timezone meeting planner. Find the best meeting time across multiple time zones. Visual timeline shows business hours overlap for all participants."
categories: ["Free Tools"]
tags: ["meeting planner", "timezone", "world clock", "time zones", "schedule meeting"]
slug: "meeting-planner"
cover:
  image: "/images/covers/meeting-planner.png"
  alt: "Timezone Meeting Planner"
ShowToc: false
---

<div id="mp-app">

<style>
  #mp-app {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
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
  #mp-app select { width: 240px; }

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

  #mp-app .mp-tl-cell.cell-work   { background: #22c55e; }
  #mp-app .mp-tl-cell.cell-early  { background: #facc15; }
  #mp-app .mp-tl-cell.cell-night  { background: #6366f1; opacity: 0.25; }
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

  @media (max-width: 540px) {
    #mp-app input[type="text"] { width: 110px; }
    #mp-app select { width: 200px; }
  }
</style>

<!-- Section 1: Add Participants -->
<div class="mp-section">
  <h2>Add Participants</h2>

  <div class="mp-row">
    <label>Name:</label>
    <input type="text" id="mp-name" placeholder="e.g. Alice" maxlength="24" />
    <label>Timezone:</label>
    <select id="mp-tz"></select>
    <button class="mp-btn" id="mp-add-btn">+ Add</button>
  </div>

  <div>
    <label style="font-size:0.78rem; color:#6b7280;">Quick add city:</label>
    <div class="mp-presets" id="mp-presets"></div>
  </div>
</div>

<!-- Section 2: Participants & Timeline -->
<div class="mp-section">
  <h2>Visual Timeline <span style="font-weight:400; font-size:0.8rem; color:#6b7280;">— click any cell to select a meeting slot</span></h2>

  <div id="mp-participant-list" class="mp-participant-list">
    <div class="mp-no-p">No participants yet. Add someone above.</div>
  </div>

  <div class="mp-timeline-wrap">
    <div class="mp-timeline" id="mp-timeline"></div>
  </div>

  <div class="mp-legend">
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#10b981; border:2px solid #059669;"></div>
      <span>Best overlap (all 9–17)</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#22c55e;"></div>
      <span>Business hours (9–17)</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#facc15;"></div>
      <span>Early/Late (7–9 or 17–20)</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#6366f1; opacity:0.4;"></div>
      <span>Night</span>
    </div>
    <div class="mp-legend-item">
      <div class="mp-legend-swatch" style="background:#f59e0b;"></div>
      <span>Selected slot</span>
    </div>
  </div>
</div>

<!-- Section 3: Best Meeting Times -->
<div class="mp-section" id="mp-suggest-section">
  <h2>Best Meeting Times</h2>
  <div class="mp-suggestions" id="mp-suggestions">
    <div class="mp-suggestion-none">Add participants to see suggestions.</div>
  </div>
</div>

<!-- Section 4: Copy Invite -->
<div class="mp-section" id="mp-invite-section">
  <h2>Copy Meeting Invite</h2>
  <div class="mp-tip">Select a slot above or choose a time, then copy the invite text for all participants.</div>
  <div class="mp-copy-wrap">
    <textarea class="mp-copy-area" id="mp-invite-text" readonly placeholder="Select a meeting slot above to generate invite text..."></textarea>
    <div class="mp-copy-row">
      <button class="mp-btn" id="mp-copy-btn">Copy to Clipboard</button>
      <span class="mp-copy-status" id="mp-copy-status">Copied!</span>
    </div>
  </div>
</div>

<script>
(function() {
  'use strict';

  const ZONES = [
    { value: 'UTC',                  label: 'UTC — Coordinated Universal Time', city: null },
    { value: 'America/Los_Angeles',  label: 'PST/PDT — Los Angeles / San Francisco', city: 'Los Angeles' },
    { value: 'America/Denver',       label: 'MST/MDT — Denver / Salt Lake City', city: null },
    { value: 'America/Chicago',      label: 'CST/CDT — Chicago / Dallas', city: 'Chicago' },
    { value: 'America/New_York',     label: 'EST/EDT — New York / Toronto', city: 'New York' },
    { value: 'America/Sao_Paulo',    label: 'BRT — São Paulo / Rio de Janeiro', city: 'São Paulo' },
    { value: 'Europe/London',        label: 'GMT/BST — London', city: 'London' },
    { value: 'Europe/Paris',         label: 'CET/CEST — Paris / Berlin / Rome', city: 'Paris' },
    { value: 'Europe/Helsinki',      label: 'EET/EEST — Helsinki / Kyiv', city: null },
    { value: 'Europe/Moscow',        label: 'MSK — Moscow', city: 'Moscow' },
    { value: 'Asia/Dubai',           label: 'GST — Dubai / Abu Dhabi', city: 'Dubai' },
    { value: 'Asia/Karachi',         label: 'PKT — Karachi / Islamabad', city: null },
    { value: 'Asia/Kolkata',         label: 'IST — Mumbai / New Delhi', city: 'Mumbai' },
    { value: 'Asia/Dhaka',           label: 'BST — Dhaka', city: null },
    { value: 'Asia/Bangkok',         label: 'ICT — Bangkok / Jakarta', city: 'Bangkok' },
    { value: 'Asia/Singapore',       label: 'SGT — Singapore / Kuala Lumpur', city: 'Singapore' },
    { value: 'Asia/Shanghai',        label: 'CST — Beijing / Shanghai / Taipei', city: 'Beijing' },
    { value: 'Asia/Tokyo',           label: 'JST — Tokyo / Osaka', city: 'Tokyo' },
    { value: 'Asia/Seoul',           label: 'KST — Seoul', city: 'Seoul' },
    { value: 'Australia/Sydney',     label: 'AEST/AEDT — Sydney / Melbourne', city: 'Sydney' },
    { value: 'Pacific/Auckland',     label: 'NZST/NZDT — Auckland', city: 'Auckland' },
    { value: 'Pacific/Honolulu',     label: 'HST — Honolulu', city: 'Honolulu' },
  ];

  const COLORS = [
    '#6366f1','#f59e0b','#ef4444','#3b82f6','#8b5cf6',
    '#06b6d4','#ec4899','#14b8a6','#f97316','#84cc16'
  ];

  let participants = [];
  let selectedSlot = null;
  let clockTick = null;

  // --- Build timezone select ---
  const tzSel = document.getElementById('mp-tz');
  ZONES.forEach(z => {
    const opt = document.createElement('option');
    opt.value = z.value;
    opt.textContent = z.label;
    tzSel.appendChild(opt);
  });
  // Default to local timezone if possible
  try {
    const local = Intl.DateTimeFormat().resolvedOptions().timeZone;
    if (ZONES.find(z => z.value === local)) tzSel.value = local;
  } catch(e) {}

  // --- Build city presets ---
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

  // --- Add participant ---
  document.getElementById('mp-add-btn').addEventListener('click', addParticipant);
  document.getElementById('mp-name').addEventListener('keydown', e => {
    if (e.key === 'Enter') addParticipant();
  });

  function addParticipant() {
    const nameEl = document.getElementById('mp-name');
    const name = nameEl.value.trim() || tzSel.options[tzSel.selectedIndex].text.split('—')[1]?.trim() || 'Participant';
    const tz = tzSel.value;
    if (participants.length >= 10) {
      alert('Maximum 10 participants.');
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

  // --- Format local time ---
  function fmtTime(tz, date) {
    return date.toLocaleString('en-US', {
      timeZone: tz,
      hour: '2-digit',
      minute: '2-digit',
      hour12: false
    });
  }

  function fmtDateTime(tz, date) {
    return date.toLocaleString('en-US', {
      timeZone: tz,
      weekday: 'short',
      month: 'short',
      day: 'numeric',
      hour: '2-digit',
      minute: '2-digit',
      hour12: true
    });
  }

  function getLocalHour(tz, utcHour) {
    // Get what hour it is in `tz` when UTC is `utcHour` today
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

  // --- Render ---
  function render() {
    renderParticipantList();
    renderTimeline();
    renderSuggestions();
    renderInvite();
  }

  function renderParticipantList() {
    const el = document.getElementById('mp-participant-list');
    if (participants.length === 0) {
      el.innerHTML = '<div class="mp-no-p">No participants yet. Add someone above.</div>';
      return;
    }
    const now = new Date();
    el.innerHTML = participants.map(p => `
      <div class="mp-participant">
        <div class="mp-color-dot" style="background:${p.color};"></div>
        <div class="mp-p-name">${escHtml(p.name)}</div>
        <div class="mp-p-tz">${escHtml(getShortLabel(p.tz))} — ${escHtml(getLocationLabel(p.tz))}</div>
        <div class="mp-p-time" id="mp-ptime-${p.id}">${fmtTime(p.tz, now)}</div>
        <button class="mp-btn-danger" onclick="window._mpRemove(${p.id})">Remove</button>
      </div>
    `).join('');
  }

  function renderTimeline() {
    const el = document.getElementById('mp-timeline');
    if (participants.length === 0) {
      el.innerHTML = '';
      return;
    }

    // Hour labels row
    let html = '<div class="mp-tl-header"><div class="mp-tl-hcell"></div>';
    for (let h = 0; h < 24; h++) {
      html += `<div class="mp-tl-hcell">${String(h).padStart(2,'0')}</div>`;
    }
    html += '</div>';

    // Compute overlap hours (all participants in business hours)
    const overlapHours = [];
    for (let h = 0; h < 24; h++) {
      const allWork = participants.every(p => {
        const lh = getLocalHour(p.tz, h);
        return lh >= 9 && lh < 17;
      });
      overlapHours.push(allWork);
    }

    // Per-participant rows
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

    // Overlap summary row
    html += `<div class="mp-tl-row overlap-row">`;
    html += `<div class="mp-tl-label" style="color:#065f46;">All overlap<span>best times</span></div>`;
    for (let h = 0; h < 24; h++) {
      let cls = overlapHours[h] ? 'cell-overlap' : 'cell-no-overlap';
      if (selectedSlot === h) cls += ' cell-selected';
      html += `<div class="mp-tl-cell ${cls}" title="UTC ${String(h).padStart(2,'0')}:00${overlapHours[h] ? ' ✓ All in business hours' : ''}" data-hour="${h}" onclick="window._mpSelectSlot(${h})"></div>`;
    }
    html += '</div>';

    el.innerHTML = html;
  }

  function renderSuggestions() {
    const el = document.getElementById('mp-suggestions');
    if (participants.length === 0) {
      el.innerHTML = '<div class="mp-suggestion-none">Add participants to see suggestions.</div>';
      return;
    }

    // Find overlap hours
    const overlapHours = [];
    for (let h = 0; h < 24; h++) {
      const allWork = participants.every(p => {
        const lh = getLocalHour(p.tz, h);
        return lh >= 9 && lh < 17;
      });
      if (allWork) overlapHours.push(h);
    }

    // Find relaxed overlap (all 7-20)
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
          No overlapping business hours found across all participants.<br>
          Consider scheduling across fewer time zones or using asynchronous communication.
        </div>`;
      return;
    }

    // Group consecutive hours into slots
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

    const quality = overlapHours.length > 0 ? 'Best overlap (all within 9–17)' : 'Extended overlap (7–20, early/late for some)';

    let html = `<div class="mp-suggestion-title">${quality} — ${hours.length} hour${hours.length>1?'s':''}</div>`;

    slots.forEach(slot => {
      const now = new Date();
      now.setUTCHours(slot.start, 0, 0, 0);
      const endDate = new Date(now);
      endDate.setUTCHours(slot.end + 1, 0, 0, 0);

      html += `<div class="mp-slot" onclick="window._mpSelectSlot(${slot.start})" style="cursor:pointer;">`;
      html += `<div class="mp-slot-utc">UTC ${String(slot.start).padStart(2,'0')}:00–${String(slot.end+1).padStart(2,'0')}:00</div>`;
      html += `<div class="mp-slot-times">`;
      participants.forEach(p => {
        html += `<div class="mp-slot-ptime" style="border-color:${p.color};">
          <strong>${escHtml(p.name)}</strong>: ${fmtTime(p.tz, now)}–${fmtTime(p.tz, endDate)}
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

    let text = `Meeting Invitation\n`;
    text += `==================\n`;
    text += `UTC: ${String(h).padStart(2,'0')}:00 – ${String(h+1).padStart(2,'0')}:00\n\n`;
    text += `Local times for participants:\n`;
    participants.forEach(p => {
      text += `  ${p.name} (${getShortLabel(p.tz)}): ${fmtDateTime(p.tz, now)}\n`;
    });
    text += `\nGenerated by Timezone Meeting Planner\nhttps://productivity.works/tools/meeting-planner/`;
    el.value = text;
  }

  // --- Clock tick ---
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

  // --- Slot selection ---
  window._mpSelectSlot = function(h) {
    selectedSlot = (selectedSlot === h) ? null : h;
    renderTimeline();
    renderInvite();
  };

  window._mpRemove = function(id) {
    removeParticipant(id);
  };

  // --- Copy ---
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

  // --- Init: add a default participant ---
  (function init() {
    try {
      const local = Intl.DateTimeFormat().resolvedOptions().timeZone;
      const z = ZONES.find(z => z.value === local);
      if (z) {
        participants.push({
          id: Date.now(),
          name: z.city || z.label.split('—')[1]?.trim().split(' / ')[0] || 'You',
          tz: local,
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

**Related Tools:** [World Clock](/tools/world-clock/) | [Timezone Converter](/tools/timezone-converter/)
