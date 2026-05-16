---
title: "Timezone Converter - Free World Clock & Meeting Planner"
date: 2025-05-16
description: "Free online timezone converter with live world clock, date/time conversion, multi-timezone comparison, and meeting planner. Convert between 20+ major timezones instantly."
categories: ["Free Tools"]
tags: ["timezone", "world clock", "time converter", "meeting planner", "international time"]
slug: "timezone-converter"
aliases: ["/tools/time-zone-converter/", "/tools/world-clock/"]
cover:
  image: "/images/covers/timezone-converter.png"
  alt: "Timezone Converter"
ShowToc: false
---

<div id="tz-app">

<style>
  #tz-app {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
    max-width: 780px;
    margin: 0 auto;
    padding: 16px;
    color: #1e1b4b;
  }

  #tz-app * { box-sizing: border-box; }

  #tz-app h2 {
    font-size: 1.1rem;
    font-weight: 700;
    color: #4f46e5;
    margin: 0 0 12px;
    padding-bottom: 6px;
    border-bottom: 2px solid #e0e7ff;
  }

  /* Mode tabs */
  #tz-app .tz-tabs {
    display: flex;
    gap: 8px;
    margin-bottom: 24px;
    flex-wrap: wrap;
  }
  #tz-app .tz-tab {
    padding: 8px 20px;
    border: 2px solid #4f46e5;
    border-radius: 24px;
    background: transparent;
    color: #4f46e5;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
  }
  #tz-app .tz-tab.active {
    background: #4f46e5;
    color: #fff;
  }
  #tz-app .tz-tab:hover:not(.active) {
    background: #eef2ff;
  }

  /* Cards */
  #tz-app .tz-card {
    background: #fff;
    border: 1px solid #e0e7ff;
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 20px;
    box-shadow: 0 1px 4px rgba(79,70,229,0.07);
  }

  /* Live clock section */
  #tz-app .tz-live-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 12px;
  }
  @media (max-width: 500px) {
    #tz-app .tz-live-grid { grid-template-columns: 1fr; }
  }
  #tz-app .tz-clock-box {
    background: #f5f3ff;
    border-radius: 10px;
    padding: 16px;
    text-align: center;
  }
  #tz-app .tz-clock-label {
    font-size: 12px;
    font-weight: 600;
    color: #6d6fae;
    margin-bottom: 4px;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  #tz-app .tz-clock-time {
    font-size: 2rem;
    font-weight: 700;
    color: #4f46e5;
    font-variant-numeric: tabular-nums;
    letter-spacing: -0.02em;
  }
  #tz-app .tz-clock-date {
    font-size: 13px;
    color: #6b7280;
    margin-top: 2px;
  }

  /* Select */
  #tz-app select {
    width: 100%;
    padding: 9px 12px;
    border: 1.5px solid #c7d2fe;
    border-radius: 8px;
    font-size: 14px;
    color: #1e1b4b;
    background: #fff;
    cursor: pointer;
    outline: none;
    transition: border-color 0.2s;
    appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%234f46e5' stroke-width='2'%3E%3Cpolyline points='6 9 12 15 18 9'%3E%3C/polyline%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 10px center;
    padding-right: 36px;
  }
  #tz-app select:focus { border-color: #4f46e5; }

  #tz-app label {
    display: block;
    font-size: 12px;
    font-weight: 600;
    color: #6d6fae;
    margin-bottom: 4px;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  /* Converter row */
  #tz-app .tz-conv-row {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 12px;
    align-items: end;
    margin-bottom: 16px;
  }
  @media (max-width: 540px) {
    #tz-app .tz-conv-row {
      grid-template-columns: 1fr;
    }
    #tz-app .tz-swap-col { text-align: center; }
  }

  #tz-app .tz-swap-btn {
    background: #4f46e5;
    color: #fff;
    border: none;
    border-radius: 50%;
    width: 38px;
    height: 38px;
    font-size: 18px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.2s, transform 0.2s;
    flex-shrink: 0;
    margin: 0 auto;
  }
  #tz-app .tz-swap-btn:hover { background: #4338ca; transform: rotate(180deg); }

  #tz-app input[type="datetime-local"] {
    width: 100%;
    padding: 9px 12px;
    border: 1.5px solid #c7d2fe;
    border-radius: 8px;
    font-size: 14px;
    color: #1e1b4b;
    outline: none;
    transition: border-color 0.2s;
  }
  #tz-app input[type="datetime-local"]:focus { border-color: #4f46e5; }

  #tz-app .tz-result-box {
    background: #f5f3ff;
    border-radius: 10px;
    padding: 14px 16px;
    margin-top: 12px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  #tz-app .tz-result-label { font-size: 12px; color: #6d6fae; font-weight: 600; }
  #tz-app .tz-result-value { font-size: 1.3rem; font-weight: 700; color: #4f46e5; }
  #tz-app .tz-result-offset { font-size: 12px; color: #9ca3af; margin-top: 2px; }

  /* Multi-timezone comparison */
  #tz-app .tz-multi-add-row {
    display: flex;
    gap: 10px;
    align-items: flex-end;
    margin-bottom: 16px;
    flex-wrap: wrap;
  }
  #tz-app .tz-multi-add-row > div { flex: 1; min-width: 200px; }
  #tz-app .tz-add-btn {
    background: #4f46e5;
    color: #fff;
    border: none;
    border-radius: 8px;
    padding: 9px 18px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s;
    white-space: nowrap;
  }
  #tz-app .tz-add-btn:hover { background: #4338ca; }
  #tz-app .tz-add-btn:disabled { background: #c7d2fe; cursor: not-allowed; }

  #tz-app .tz-multi-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  #tz-app .tz-multi-item {
    background: #fff;
    border: 1.5px solid #e0e7ff;
    border-radius: 10px;
    padding: 12px 14px;
    display: flex;
    align-items: center;
    gap: 12px;
    flex-wrap: wrap;
  }
  #tz-app .tz-multi-item.is-day { border-color: #fbbf24; background: #fffbeb; }
  #tz-app .tz-multi-item.is-night { border-color: #818cf8; background: #f5f3ff; }
  #tz-app .tz-multi-name { font-weight: 600; font-size: 14px; flex: 1; min-width: 120px; }
  #tz-app .tz-multi-time { font-size: 1.4rem; font-weight: 700; color: #4f46e5; font-variant-numeric: tabular-nums; }
  #tz-app .tz-multi-date { font-size: 12px; color: #9ca3af; }
  #tz-app .tz-multi-badge {
    font-size: 11px;
    padding: 2px 8px;
    border-radius: 12px;
    font-weight: 600;
  }
  #tz-app .badge-day { background: #fef3c7; color: #92400e; }
  #tz-app .badge-night { background: #e0e7ff; color: #3730a3; }
  #tz-app .tz-remove-btn {
    background: none;
    border: none;
    color: #9ca3af;
    font-size: 18px;
    cursor: pointer;
    line-height: 1;
    padding: 0 4px;
    transition: color 0.2s;
  }
  #tz-app .tz-remove-btn:hover { color: #ef4444; }

  /* Timeline bar */
  #tz-app .tz-timeline {
    margin-top: 16px;
  }
  #tz-app .tz-tl-label {
    font-size: 11px;
    color: #9ca3af;
    margin-bottom: 6px;
    font-weight: 600;
    text-transform: uppercase;
  }
  #tz-app .tz-tl-row {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 6px;
  }
  #tz-app .tz-tl-name {
    font-size: 12px;
    width: 90px;
    flex-shrink: 0;
    color: #4b5563;
    font-weight: 500;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  #tz-app .tz-tl-bar-wrap {
    flex: 1;
    height: 20px;
    background: #1e1b4b;
    border-radius: 4px;
    position: relative;
    overflow: hidden;
  }
  #tz-app .tz-tl-day-seg {
    position: absolute;
    top: 0;
    height: 100%;
    background: #fbbf24;
    border-radius: 2px;
  }
  #tz-app .tz-tl-now-line {
    position: absolute;
    top: 0;
    height: 100%;
    width: 2px;
    background: #ef4444;
    border-radius: 1px;
  }
  #tz-app .tz-tl-hour {
    font-size: 11px;
    color: #9ca3af;
    width: 90px;
    flex-shrink: 0;
  }
  #tz-app .tz-tl-labels {
    display: flex;
    flex: 1;
    justify-content: space-between;
    font-size: 10px;
    color: #9ca3af;
    padding: 0 2px;
    margin-top: 2px;
  }

  /* Meeting planner */
  #tz-app .tz-meeting-grid {
    overflow-x: auto;
  }
  #tz-app .tz-meeting-table {
    width: 100%;
    border-collapse: collapse;
    min-width: 500px;
  }
  #tz-app .tz-meeting-table th {
    font-size: 11px;
    font-weight: 600;
    color: #6d6fae;
    text-align: center;
    padding: 4px 2px;
    border-bottom: 1px solid #e0e7ff;
  }
  #tz-app .tz-meeting-table td {
    width: 3.8%;
    height: 32px;
    text-align: center;
    font-size: 10px;
    border: 1px solid #f3f4f6;
  }
  #tz-app .tz-meeting-table .tz-row-label {
    font-size: 11px;
    font-weight: 600;
    color: #4b5563;
    text-align: left;
    padding: 4px 8px;
    white-space: nowrap;
    width: auto;
  }
  #tz-app .cell-night { background: #1e1b4b; }
  #tz-app .cell-day { background: #fef9c3; }
  #tz-app .cell-work { background: #6ee7b7; }
  #tz-app .cell-overlap { background: #4f46e5; }
  #tz-app .tz-legend {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    margin-top: 12px;
    font-size: 12px;
    color: #6b7280;
  }
  #tz-app .tz-legend-item { display: flex; align-items: center; gap: 6px; }
  #tz-app .tz-legend-dot {
    width: 14px;
    height: 14px;
    border-radius: 3px;
  }

  /* Sections */
  #tz-app .tz-section { display: none; }
  #tz-app .tz-section.active { display: block; }

  #tz-app .tz-field { margin-bottom: 14px; }
</style>

<!-- Mode Tabs -->
<div class="tz-tabs">
  <button class="tz-tab active" onclick="tzSetMode('converter')">Converter</button>
  <button class="tz-tab" onclick="tzSetMode('world-clock')">World Clock</button>
  <button class="tz-tab" onclick="tzSetMode('meeting')">Meeting Planner</button>
</div>

<!-- ===== CONVERTER MODE ===== -->
<div id="tz-section-converter" class="tz-section active">
  <div class="tz-card">
    <h2>Convert Date & Time</h2>
    <div class="tz-field">
      <label>Date & Time</label>
      <input type="datetime-local" id="tz-dt-input">
    </div>
    <div class="tz-conv-row">
      <div>
        <label>From Timezone</label>
        <select id="tz-from"></select>
      </div>
      <div class="tz-swap-col">
        <button class="tz-swap-btn" onclick="tzSwap()" title="Swap timezones">⇄</button>
      </div>
      <div>
        <label>To Timezone</label>
        <select id="tz-to"></select>
      </div>
    </div>
    <div class="tz-result-box" id="tz-conv-result">
      <div>
        <div class="tz-result-label">Converted Time</div>
        <div class="tz-result-value" id="tz-conv-value">—</div>
        <div class="tz-result-offset" id="tz-conv-offset"></div>
      </div>
    </div>
  </div>
</div>

<!-- ===== WORLD CLOCK MODE ===== -->
<div id="tz-section-world-clock" class="tz-section">
  <div class="tz-card">
    <h2>Live World Clock</h2>
    <div class="tz-live-grid" id="tz-live-primary">
      <div class="tz-clock-box">
        <div class="tz-clock-label" id="tz-live-from-label">—</div>
        <div class="tz-clock-time" id="tz-live-from-time">—</div>
        <div class="tz-clock-date" id="tz-live-from-date"></div>
      </div>
      <div class="tz-clock-box">
        <div class="tz-clock-label" id="tz-live-to-label">—</div>
        <div class="tz-clock-time" id="tz-live-to-time">—</div>
        <div class="tz-clock-date" id="tz-live-to-date"></div>
      </div>
    </div>
  </div>

  <div class="tz-card">
    <h2>Compare Multiple Timezones</h2>
    <div class="tz-multi-add-row">
      <div>
        <label>Add Timezone</label>
        <select id="tz-add-select"></select>
      </div>
      <button class="tz-add-btn" id="tz-add-btn" onclick="tzAddZone()">+ Add</button>
    </div>
    <div class="tz-multi-list" id="tz-multi-list"></div>
    <div class="tz-timeline" id="tz-timeline"></div>
  </div>
</div>

<!-- ===== MEETING PLANNER MODE ===== -->
<div id="tz-section-meeting" class="tz-section">
  <div class="tz-card">
    <h2>Meeting Planner — Business Hours Overlap</h2>
    <p style="font-size:13px;color:#6b7280;margin:0 0 16px;">Shows when 9am–5pm business hours overlap across your selected timezones. Add timezones in the World Clock tab first.</p>
    <div class="tz-meeting-grid">
      <table class="tz-meeting-table" id="tz-meeting-table"></table>
    </div>
    <div class="tz-legend">
      <div class="tz-legend-item"><div class="tz-legend-dot" style="background:#1e1b4b"></div>Night</div>
      <div class="tz-legend-item"><div class="tz-legend-dot" style="background:#fef9c3;border:1px solid #d1d5db"></div>Day (off-hours)</div>
      <div class="tz-legend-item"><div class="tz-legend-dot" style="background:#6ee7b7"></div>Business hours</div>
      <div class="tz-legend-item"><div class="tz-legend-dot" style="background:#4f46e5"></div>All overlap</div>
    </div>
  </div>
</div>

<script>
(function() {
  const ZONES = [
    { label: "UTC — Coordinated Universal Time",      value: "UTC" },
    { label: "EST — Eastern (New York)",               value: "America/New_York" },
    { label: "CST — Central (Chicago)",                value: "America/Chicago" },
    { label: "MST — Mountain (Denver)",                value: "America/Denver" },
    { label: "PST — Pacific (Los Angeles)",            value: "America/Los_Angeles" },
    { label: "AKT — Alaska",                           value: "America/Anchorage" },
    { label: "HST — Hawaii",                           value: "Pacific/Honolulu" },
    { label: "BRT — Brazil (São Paulo)",               value: "America/Sao_Paulo" },
    { label: "GMT — London",                           value: "Europe/London" },
    { label: "CET — Paris / Berlin",                   value: "Europe/Paris" },
    { label: "EET — Helsinki / Athens",                value: "Europe/Helsinki" },
    { label: "MSK — Moscow",                           value: "Europe/Moscow" },
    { label: "GST — Dubai",                            value: "Asia/Dubai" },
    { label: "IST — Mumbai / Delhi",                   value: "Asia/Kolkata" },
    { label: "BST — Dhaka",                            value: "Asia/Dhaka" },
    { label: "ICT — Bangkok",                          value: "Asia/Bangkok" },
    { label: "SGT — Singapore",                        value: "Asia/Singapore" },
    { label: "CST — Shanghai / Beijing",               value: "Asia/Shanghai" },
    { label: "KST — Seoul",                            value: "Asia/Seoul" },
    { label: "JST — Tokyo",                            value: "Asia/Tokyo" },
    { label: "AEST — Sydney",                          value: "Australia/Sydney" },
    { label: "NZST — Auckland",                        value: "Pacific/Auckland" },
  ];

  let activeMode = 'converter';
  let multiZones = []; // array of tz values
  let clockInterval = null;

  // Populate selects
  function populateSelect(id, defaultVal) {
    const el = document.getElementById(id);
    if (!el) return;
    el.innerHTML = '';
    ZONES.forEach(z => {
      const o = document.createElement('option');
      o.value = z.value;
      o.textContent = z.label;
      if (z.value === defaultVal) o.selected = true;
      el.appendChild(o);
    });
  }

  function init() {
    populateSelect('tz-from', 'UTC');
    populateSelect('tz-to', 'America/New_York');
    populateSelect('tz-add-select', 'Asia/Tokyo');

    // Set datetime input to now (local)
    const now = new Date();
    const local = new Date(now - now.getTimezoneOffset() * 60000);
    document.getElementById('tz-dt-input').value = local.toISOString().slice(0, 16);

    // Listeners
    document.getElementById('tz-dt-input').addEventListener('input', tzConvert);
    document.getElementById('tz-from').addEventListener('change', () => { tzConvert(); tzUpdateLive(); });
    document.getElementById('tz-to').addEventListener('change', () => { tzConvert(); tzUpdateLive(); });

    tzConvert();
    tzUpdateLive();
    startClock();
  }

  window.tzSetMode = function(mode) {
    activeMode = mode;
    document.querySelectorAll('#tz-app .tz-tab').forEach((t, i) => {
      t.classList.toggle('active', ['converter','world-clock','meeting'][i] === mode);
    });
    document.querySelectorAll('#tz-app .tz-section').forEach(s => s.classList.remove('active'));
    document.getElementById('tz-section-' + mode).classList.add('active');
    if (mode === 'meeting') tzRenderMeeting();
  };

  window.tzSwap = function() {
    const f = document.getElementById('tz-from');
    const t = document.getElementById('tz-to');
    const tmp = f.value;
    f.value = t.value;
    t.value = tmp;
    tzConvert();
    tzUpdateLive();
  };

  function tzConvert() {
    const dtVal = document.getElementById('tz-dt-input').value;
    const fromTz = document.getElementById('tz-from').value;
    const toTz = document.getElementById('tz-to').value;
    if (!dtVal) return;

    // Parse datetime-local as if it's in fromTz
    // Strategy: get the UTC ms by formatting a known UTC time in fromTz, then binary-search
    const [datePart, timePart] = dtVal.split('T');
    const [y, mo, d] = datePart.split('-').map(Number);
    const [h, mi] = timePart.split(':').map(Number);

    // Approximate: treat input as UTC first, then adjust
    const approxUTC = Date.UTC(y, mo - 1, d, h, mi);
    // Get offset of fromTz at that approximate UTC time
    const offsetMin = getTzOffsetMin(fromTz, approxUTC);
    const utcMs = approxUTC - offsetMin * 60000;

    const formatted = formatInTz(utcMs, toTz);
    const toOffset = getTzOffsetMin(toTz, utcMs);
    const fromOffset = getTzOffsetMin(fromTz, utcMs);
    const diffH = (toOffset - fromOffset) / 60;
    const sign = diffH >= 0 ? '+' : '';

    document.getElementById('tz-conv-value').textContent = formatted;
    document.getElementById('tz-conv-offset').textContent =
      'Offset difference: ' + sign + diffH.toFixed(1).replace('.0','') + ' hours';
  }

  function getTzOffsetMin(tz, utcMs) {
    // Compare UTC-formatted time with tz-formatted time to get offset
    const utcStr = new Date(utcMs).toLocaleString('en-US', { timeZone: 'UTC',
      year:'numeric', month:'2-digit', day:'2-digit',
      hour:'2-digit', minute:'2-digit', second:'2-digit', hour12: false });
    const tzStr = new Date(utcMs).toLocaleString('en-US', { timeZone: tz,
      year:'numeric', month:'2-digit', day:'2-digit',
      hour:'2-digit', minute:'2-digit', second:'2-digit', hour12: false });
    return (parseLocaleStr(tzStr) - parseLocaleStr(utcStr)) / 60000;
  }

  function parseLocaleStr(s) {
    // en-US format: "MM/DD/YYYY, HH:MM:SS"
    const m = s.match(/(\d+)\/(\d+)\/(\d+),?\s+(\d+):(\d+):(\d+)/);
    if (!m) return 0;
    return Date.UTC(+m[3], +m[1]-1, +m[2], +m[4], +m[5], +m[6]);
  }

  function formatInTz(utcMs, tz) {
    return new Date(utcMs).toLocaleString('en-US', {
      timeZone: tz,
      weekday: 'short',
      year: 'numeric', month: 'short', day: 'numeric',
      hour: '2-digit', minute: '2-digit',
      hour12: true
    });
  }

  function formatTimeOnly(utcMs, tz) {
    return new Date(utcMs).toLocaleTimeString('en-US', {
      timeZone: tz, hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false
    });
  }

  function formatDateOnly(utcMs, tz) {
    return new Date(utcMs).toLocaleDateString('en-US', {
      timeZone: tz, weekday: 'short', month: 'short', day: 'numeric'
    });
  }

  function tzUpdateLive() {
    const fromTz = document.getElementById('tz-from').value;
    const toTz = document.getElementById('tz-to').value;
    const fromLabel = ZONES.find(z => z.value === fromTz);
    const toLabel = ZONES.find(z => z.value === toTz);
    document.getElementById('tz-live-from-label').textContent = fromLabel ? fromLabel.label.split('—')[0].trim() : fromTz;
    document.getElementById('tz-live-to-label').textContent = toLabel ? toLabel.label.split('—')[0].trim() : toTz;
  }

  function tickClock() {
    const now = Date.now();
    const fromTz = document.getElementById('tz-from').value;
    const toTz = document.getElementById('tz-to').value;

    document.getElementById('tz-live-from-time').textContent = formatTimeOnly(now, fromTz);
    document.getElementById('tz-live-from-date').textContent = formatDateOnly(now, fromTz);
    document.getElementById('tz-live-to-time').textContent = formatTimeOnly(now, toTz);
    document.getElementById('tz-live-to-date').textContent = formatDateOnly(now, toTz);

    // Update multi-list
    const items = document.querySelectorAll('#tz-multi-list .tz-multi-item');
    items.forEach(item => {
      const tz = item.dataset.tz;
      const timeEl = item.querySelector('.tz-multi-time');
      const dateEl = item.querySelector('.tz-multi-date');
      if (timeEl) timeEl.textContent = formatTimeOnly(now, tz);
      if (dateEl) dateEl.textContent = formatDateOnly(now, tz);
      // day/night based on hour
      const hourStr = new Date(now).toLocaleString('en-US', { timeZone: tz, hour: 'numeric', hour12: false });
      const hour = parseInt(hourStr);
      const isDay = hour >= 6 && hour < 18;
      item.classList.toggle('is-day', isDay);
      item.classList.toggle('is-night', !isDay);
      const badge = item.querySelector('.tz-multi-badge');
      if (badge) {
        badge.textContent = isDay ? 'Day' : 'Night';
        badge.className = 'tz-multi-badge ' + (isDay ? 'badge-day' : 'badge-night');
      }
    });

    // Timeline
    renderTimeline(now);
  }

  function startClock() {
    tickClock();
    clockInterval = setInterval(tickClock, 1000);
  }

  window.tzAddZone = function() {
    if (multiZones.length >= 6) return;
    const tz = document.getElementById('tz-add-select').value;
    if (multiZones.includes(tz)) return;
    multiZones.push(tz);
    renderMultiList();
    document.getElementById('tz-add-btn').disabled = multiZones.length >= 6;
  };

  function tzRemoveZone(tz) {
    multiZones = multiZones.filter(z => z !== tz);
    renderMultiList();
    document.getElementById('tz-add-btn').disabled = multiZones.length >= 6;
    if (activeMode === 'meeting') tzRenderMeeting();
  }

  function renderMultiList() {
    const list = document.getElementById('tz-multi-list');
    const now = Date.now();
    list.innerHTML = '';
    multiZones.forEach(tz => {
      const z = ZONES.find(z => z.value === tz);
      const label = z ? z.label.split('—').slice(1).join('—').trim() : tz;
      const abbr = z ? z.label.split('—')[0].trim() : '';
      const hourStr = new Date(now).toLocaleString('en-US', { timeZone: tz, hour: 'numeric', hour12: false });
      const hour = parseInt(hourStr);
      const isDay = hour >= 6 && hour < 18;
      const item = document.createElement('div');
      item.className = 'tz-multi-item ' + (isDay ? 'is-day' : 'is-night');
      item.dataset.tz = tz;
      item.innerHTML = `
        <div class="tz-multi-name">${abbr}<br><span style="font-weight:400;font-size:12px;color:#6b7280">${label}</span></div>
        <div>
          <div class="tz-multi-time">${formatTimeOnly(now, tz)}</div>
          <div class="tz-multi-date">${formatDateOnly(now, tz)}</div>
        </div>
        <span class="tz-multi-badge ${isDay ? 'badge-day':'badge-night'}">${isDay?'Day':'Night'}</span>
        <button class="tz-remove-btn" onclick="tzRemoveZone('${tz}')">×</button>
      `;
      list.appendChild(item);
    });
    renderTimeline(now);
    if (activeMode === 'meeting') tzRenderMeeting();
  }

  function renderTimeline(now) {
    const container = document.getElementById('tz-timeline');
    if (multiZones.length === 0) { container.innerHTML = ''; return; }

    let html = '<div class="tz-tl-label">24-hour timeline (yellow = 6am–6pm day)</div>';
    multiZones.forEach(tz => {
      const z = ZONES.find(z => z.value === tz);
      const abbr = z ? z.label.split('—')[0].trim() : tz;
      // Current hour in this tz
      const hourStr = new Date(now).toLocaleString('en-US', { timeZone: tz, hour: 'numeric', minute:'numeric', hour12: false });
      const [hh, mm] = hourStr.split(':').map(Number);
      const currentFrac = (hh * 60 + (mm||0)) / (24 * 60);
      // Day segment: 6am to 6pm = 25% to 75%
      const dayLeft = (6 / 24) * 100;
      const dayWidth = (12 / 24) * 100;
      const nowLeft = currentFrac * 100;
      html += `<div class="tz-tl-row">
        <div class="tz-tl-name">${abbr}</div>
        <div class="tz-tl-bar-wrap">
          <div class="tz-tl-day-seg" style="left:${dayLeft}%;width:${dayWidth}%"></div>
          <div class="tz-tl-now-line" style="left:${nowLeft}%"></div>
        </div>
        <div class="tz-tl-hour">${String(hh).padStart(2,'0')}:${String(mm||0).padStart(2,'0')}</div>
      </div>`;
    });
    html += `<div class="tz-tl-row">
      <div class="tz-tl-hour"></div>
      <div class="tz-tl-labels" style="flex:1">
        <span>0</span><span>6</span><span>12</span><span>18</span><span>24</span>
      </div>
    </div>`;
    container.innerHTML = html;
  }

  window.tzRemoveZone = tzRemoveZone;

  function tzRenderMeeting() {
    const table = document.getElementById('tz-meeting-table');
    if (multiZones.length === 0) {
      table.innerHTML = '<tr><td style="padding:20px;color:#9ca3af;font-size:13px">Add timezones in the World Clock tab to see overlap.</td></tr>';
      return;
    }
    const now = Date.now();
    // Build header: hours 0-23
    let html = '<thead><tr><th class="tz-row-label">Timezone</th>';
    for (let h = 0; h < 24; h++) {
      html += `<th>${h}</th>`;
    }
    html += '</tr></thead><tbody>';

    // For each zone, determine which hours are business hours (9-17)
    const businessHours = multiZones.map(tz => {
      const arr = [];
      for (let h = 0; h < 24; h++) {
        // Find what hour in this tz corresponds to UTC hour h on today's date
        const testDate = new Date(now);
        testDate.setUTCHours(h, 0, 0, 0);
        const localHStr = testDate.toLocaleString('en-US', { timeZone: tz, hour: 'numeric', hour12: false });
        const localH = parseInt(localHStr);
        arr.push(localH);
      }
      return arr;
    });

    // Overlap: all zones have business hours (9 <= h < 17)
    const overlapHours = Array(24).fill(true).map((_, h) => {
      return multiZones.every((tz, zi) => {
        const localH = businessHours[zi][h];
        return localH >= 9 && localH < 17;
      });
    });

    multiZones.forEach((tz, zi) => {
      const z = ZONES.find(z => z.value === tz);
      const abbr = z ? z.label.split('—')[0].trim() : tz;
      const loc = z ? z.label.split('—').slice(1).join('—').trim() : '';
      html += `<tr><td class="tz-row-label">${abbr}<br><span style="font-weight:400;font-size:10px;color:#9ca3af">${loc}</span></td>`;
      for (let h = 0; h < 24; h++) {
        const localH = businessHours[zi][h];
        let cls = '';
        if (overlapHours[h]) cls = 'cell-overlap';
        else if (localH >= 9 && localH < 17) cls = 'cell-work';
        else if (localH >= 6 && localH < 18) cls = 'cell-day';
        else cls = 'cell-night';
        html += `<td class="${cls}" title="${localH}:00"></td>`;
      }
      html += '</tr>';
    });

    html += '</tbody>';
    table.innerHTML = html;
  }

  // Boot
  init();
})();
</script>

</div>

---

**Related:** Plan your productivity with our [Pomodoro Timer](/tools/pomodoro-timer/)
