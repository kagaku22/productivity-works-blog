---
title: "Unix Timestamp Converter — Epoch Time Tool"
date: 2025-05-16
description: "Convert Unix timestamps to human-readable dates and vice versa. Live clock, multiple formats, milliseconds support, and timezone selection. Free, no sign-up."
categories: ["Free Tools"]
slug: "timestamp-converter"
ShowToc: false
aliases:
  - "/tools/timestamp-converter/"
  - "/tools/timestamp-converter/"
cover:
  image: "/images/covers/timestamp-converter.png"
  alt: "Unix Timestamp Converter"
---

**Convert Unix timestamps instantly** — paste an epoch value to see the human-readable date, or pick a date to get its timestamp. Live clock, multiple output formats, milliseconds support, and full timezone control.

<div id="ts-app">
<style>
  #ts-app *,
  #ts-app *::before,
  #ts-app *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #ts-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    font-size: 15px;
    line-height: 1.6;
    color: #1a1a2e;
    max-width: 800px;
  }
  #ts-app .ts-section {
    background: #f8f9ff;
    border: 1px solid #e0e4f0;
    border-radius: 10px;
    padding: 20px 24px;
    margin-bottom: 20px;
  }
  #ts-app .ts-section-title {
    font-size: 13px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: #6366f1;
    margin-bottom: 14px;
  }
  #ts-app .ts-live-clock {
    background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
    border-radius: 10px;
    padding: 20px 24px;
    margin-bottom: 20px;
    color: #fff;
  }
  #ts-app .ts-live-label {
    font-size: 12px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    opacity: 0.8;
    margin-bottom: 6px;
  }
  #ts-app .ts-live-value {
    font-size: 36px;
    font-weight: 700;
    font-variant-numeric: tabular-nums;
    letter-spacing: 0.02em;
    word-break: break-all;
  }
  #ts-app .ts-live-sub {
    font-size: 13px;
    opacity: 0.75;
    margin-top: 4px;
    font-variant-numeric: tabular-nums;
  }
  #ts-app .ts-controls-row {
    display: flex;
    gap: 10px;
    align-items: center;
    flex-wrap: wrap;
    margin-bottom: 16px;
  }
  #ts-app .ts-toggle-group {
    display: flex;
    border: 1px solid #c7d0ea;
    border-radius: 6px;
    overflow: hidden;
  }
  #ts-app .ts-toggle-btn {
    padding: 7px 16px;
    font-size: 13px;
    font-weight: 600;
    border: none;
    background: #fff;
    color: #555;
    cursor: pointer;
    transition: background 0.15s, color 0.15s;
  }
  #ts-app .ts-toggle-btn.active {
    background: #6366f1;
    color: #fff;
  }
  #ts-app .ts-toggle-btn:hover:not(.active) {
    background: #eef0ff;
  }
  #ts-app select,
  #ts-app input[type="text"],
  #ts-app input[type="number"],
  #ts-app input[type="datetime-local"] {
    padding: 8px 12px;
    font-size: 14px;
    border: 1px solid #c7d0ea;
    border-radius: 6px;
    background: #fff;
    color: #1a1a2e;
    outline: none;
    transition: border-color 0.15s;
  }
  #ts-app select:focus,
  #ts-app input[type="text"]:focus,
  #ts-app input[type="number"]:focus,
  #ts-app input[type="datetime-local"]:focus {
    border-color: #6366f1;
    box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
  }
  #ts-app .ts-input-row {
    display: flex;
    gap: 10px;
    align-items: center;
    flex-wrap: wrap;
    margin-bottom: 14px;
  }
  #ts-app .ts-input-wide {
    flex: 1;
    min-width: 200px;
    font-family: "SFMono-Regular", Consolas, monospace;
  }
  #ts-app .ts-btn {
    padding: 8px 18px;
    font-size: 14px;
    font-weight: 600;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    background: #6366f1;
    color: #fff;
    transition: background 0.15s, transform 0.1s;
    white-space: nowrap;
  }
  #ts-app .ts-btn:hover {
    background: #4f46e5;
  }
  #ts-app .ts-btn:active {
    transform: scale(0.97);
  }
  #ts-app .ts-btn-secondary {
    background: #fff;
    color: #6366f1;
    border: 1px solid #c7d0ea;
  }
  #ts-app .ts-btn-secondary:hover {
    background: #eef0ff;
  }
  #ts-app .ts-results {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  #ts-app .ts-result-row {
    display: flex;
    align-items: center;
    gap: 10px;
    background: #fff;
    border: 1px solid #e0e4f0;
    border-radius: 7px;
    padding: 10px 14px;
    flex-wrap: wrap;
  }
  #ts-app .ts-result-label {
    font-size: 12px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: #888;
    min-width: 110px;
    flex-shrink: 0;
  }
  #ts-app .ts-result-value {
    font-family: "SFMono-Regular", Consolas, monospace;
    font-size: 13.5px;
    color: #1a1a2e;
    flex: 1;
    word-break: break-all;
    min-width: 150px;
  }
  #ts-app .ts-copy-btn {
    padding: 4px 12px;
    font-size: 12px;
    font-weight: 600;
    border: 1px solid #c7d0ea;
    border-radius: 5px;
    background: #fff;
    color: #6366f1;
    cursor: pointer;
    transition: background 0.15s, color 0.15s;
    flex-shrink: 0;
  }
  #ts-app .ts-copy-btn:hover {
    background: #6366f1;
    color: #fff;
    border-color: #6366f1;
  }
  #ts-app .ts-copy-btn.copied {
    background: #10b981;
    color: #fff;
    border-color: #10b981;
  }
  #ts-app .ts-error {
    color: #ef4444;
    font-size: 13px;
    margin-top: 6px;
    min-height: 18px;
  }
  #ts-app .ts-ref-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13.5px;
  }
  #ts-app .ts-ref-table th {
    text-align: left;
    font-size: 12px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: #888;
    padding: 6px 10px;
    border-bottom: 1px solid #e0e4f0;
  }
  #ts-app .ts-ref-table td {
    padding: 9px 10px;
    border-bottom: 1px solid #f0f2fa;
    vertical-align: middle;
  }
  #ts-app .ts-ref-table tr:last-child td {
    border-bottom: none;
  }
  #ts-app .ts-ref-table .ts-mono {
    font-family: "SFMono-Regular", Consolas, monospace;
  }
  #ts-app .ts-ref-table .ts-ref-copy {
    padding: 3px 10px;
    font-size: 11px;
    font-weight: 600;
    border: 1px solid #c7d0ea;
    border-radius: 4px;
    background: #fff;
    color: #6366f1;
    cursor: pointer;
    transition: background 0.15s, color 0.15s;
  }
  #ts-app .ts-ref-table .ts-ref-copy:hover {
    background: #6366f1;
    color: #fff;
    border-color: #6366f1;
  }
  #ts-app .ts-divider {
    border: none;
    border-top: 1px solid #e0e4f0;
    margin: 6px 0 14px;
  }
  #ts-app .ts-tz-row {
    display: flex;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 14px;
  }
  #ts-app .ts-tz-label {
    font-size: 13px;
    font-weight: 600;
    color: #555;
    white-space: nowrap;
  }
  #ts-app select.ts-tz-select {
    min-width: 220px;
  }
  @media (max-width: 540px) {
    #ts-app .ts-live-value { font-size: 26px; }
    #ts-app .ts-result-label { min-width: 90px; }
    #ts-app .ts-ref-table { font-size: 12px; }
    #ts-app .ts-ref-table th, #ts-app .ts-ref-table td { padding: 7px 6px; }
  }
</style>

<!-- Live Clock -->
<div class="ts-live-clock">
  <div class="ts-live-label">Current Unix Timestamp</div>
  <div class="ts-live-value" id="ts-live-val">—</div>
  <div class="ts-live-sub" id="ts-live-sub">—</div>
</div>

<!-- Controls: unit + timezone -->
<div class="ts-section">
  <div class="ts-section-title">Global Settings</div>
  <div class="ts-controls-row">
    <span style="font-size:13px;font-weight:600;color:#555;">Unit:</span>
    <div class="ts-toggle-group">
      <button class="ts-toggle-btn active" id="ts-unit-sec" onclick="tsSetUnit('s')">Seconds</button>
      <button class="ts-toggle-btn" id="ts-unit-ms" onclick="tsSetUnit('ms')">Milliseconds</button>
    </div>
  </div>
  <div class="ts-tz-row">
    <span class="ts-tz-label">Timezone:</span>
    <select class="ts-tz-select" id="ts-tz-select" onchange="tsOnTzChange()"></select>
  </div>
</div>

<!-- Timestamp → Date -->
<div class="ts-section">
  <div class="ts-section-title">Timestamp to Date</div>
  <div class="ts-input-row">
    <input type="number" class="ts-input-wide" id="ts-ts-input" placeholder="Enter Unix timestamp (e.g. 1700000000)" oninput="tsConvertTs()" />
    <button class="ts-btn ts-btn-secondary" onclick="tsUseNow()">Use Now</button>
  </div>
  <div class="ts-error" id="ts-ts-error"></div>
  <div class="ts-results" id="ts-ts-results"></div>
</div>

<!-- Date → Timestamp -->
<div class="ts-section">
  <div class="ts-section-title">Date to Timestamp</div>
  <div class="ts-input-row">
    <input type="datetime-local" id="ts-dt-input" oninput="tsConvertDt()" />
    <button class="ts-btn ts-btn-secondary" onclick="tsDtUseNow()">Use Now</button>
  </div>
  <div class="ts-results" id="ts-dt-results"></div>
</div>

<!-- Common Reference Timestamps -->
<div class="ts-section">
  <div class="ts-section-title">Common Reference Timestamps</div>
  <table class="ts-ref-table">
    <thead>
      <tr>
        <th>Event</th>
        <th>Unix (seconds)</th>
        <th>Date (UTC)</th>
        <th></th>
      </tr>
    </thead>
    <tbody id="ts-ref-body"></tbody>
  </table>
</div>

<script>
(function() {
  "use strict";

  // ── State ────────────────────────────────────────────────
  var unit = "s"; // "s" | "ms"
  var tz = Intl.DateTimeFormat().resolvedOptions().timeZone;
  var liveTimer = null;

  // ── Timezone list ────────────────────────────────────────
  var commonTzList = [
    "UTC",
    "America/New_York","America/Chicago","America/Denver","America/Los_Angeles",
    "America/Sao_Paulo","America/Toronto","America/Vancouver",
    "Europe/London","Europe/Paris","Europe/Berlin","Europe/Moscow","Europe/Istanbul",
    "Asia/Dubai","Asia/Kolkata","Asia/Dhaka","Asia/Bangkok","Asia/Singapore",
    "Asia/Shanghai","Asia/Tokyo","Asia/Seoul",
    "Australia/Sydney","Pacific/Auckland","Pacific/Honolulu"
  ];

  function buildTzSelect() {
    var sel = document.getElementById("ts-tz-select");
    // Best effort: list Intl-supported timezones
    var allTz = [];
    try {
      if (Intl.supportedValuesOf) {
        allTz = Intl.supportedValuesOf("timeZone");
      }
    } catch(e) {}
    if (allTz.length === 0) allTz = commonTzList;
    // Deduplicate and sort
    var seen = {};
    var sorted = [];
    allTz.forEach(function(z) { if (!seen[z]) { seen[z]=1; sorted.push(z); } });
    sorted.sort();
    // Detect local
    var localTz = Intl.DateTimeFormat().resolvedOptions().timeZone;
    sel.innerHTML = "";
    sorted.forEach(function(z) {
      var opt = document.createElement("option");
      opt.value = z;
      opt.textContent = z;
      if (z === localTz) opt.selected = true;
      sel.appendChild(opt);
    });
    tz = sel.value;
  }

  function tsOnTzChange() {
    tz = document.getElementById("ts-tz-select").value;
    tsConvertTs();
    tsConvertDt();
    renderRef();
  }

  // ── Unit ─────────────────────────────────────────────────
  function tsSetUnit(u) {
    unit = u;
    document.getElementById("ts-unit-sec").classList.toggle("active", u === "s");
    document.getElementById("ts-unit-ms").classList.toggle("active", u === "ms");
    startLiveClock();
    tsConvertTs();
    tsConvertDt();
    renderRef();
  }
  window.tsSetUnit = tsSetUnit;
  window.tsOnTzChange = tsOnTzChange;

  // ── Live clock ───────────────────────────────────────────
  function startLiveClock() {
    if (liveTimer) clearInterval(liveTimer);
    tickClock();
    liveTimer = setInterval(tickClock, unit === "ms" ? 100 : 1000);
  }

  function tickClock() {
    var now = Date.now();
    var val = unit === "ms" ? now : Math.floor(now / 1000);
    document.getElementById("ts-live-val").textContent = val.toLocaleString("en-US");
    document.getElementById("ts-live-sub").textContent =
      formatInTz(new Date(now), tz, {
        weekday:"short", year:"numeric", month:"short",
        day:"numeric", hour:"2-digit", minute:"2-digit", second:"2-digit",
        timeZoneName:"short"
      });
  }

  // ── Helpers ──────────────────────────────────────────────
  function formatInTz(date, timezone, opts) {
    try {
      return date.toLocaleString("en-US", Object.assign({timeZone: timezone}, opts));
    } catch(e) {
      return date.toLocaleString("en-US", opts);
    }
  }

  function toIso8601(date, timezone) {
    // Approximate ISO 8601 with offset
    try {
      var fmt = new Intl.DateTimeFormat("sv-SE", {
        timeZone: timezone,
        year:"numeric", month:"2-digit", day:"2-digit",
        hour:"2-digit", minute:"2-digit", second:"2-digit"
      });
      var parts = {};
      fmt.formatToParts(date).forEach(function(p) { parts[p.type] = p.value; });
      var base = parts.year+"-"+parts.month+"-"+parts.day+"T"+
                 parts.hour+":"+parts.minute+":"+parts.second;
      // Offset
      var utcMs = date.getTime();
      var localMs = new Date(date.toLocaleString("en-US", {timeZone: timezone})).getTime();
      var diffMin = Math.round((localMs - new Date(date.toLocaleString("en-US", {timeZone: "UTC"})).getTime()) / 60000);
      var sign = diffMin >= 0 ? "+" : "-";
      var abs = Math.abs(diffMin);
      var hh = String(Math.floor(abs/60)).padStart(2,"0");
      var mm = String(abs%60).padStart(2,"0");
      return base + sign + hh + ":" + mm;
    } catch(e) {
      return date.toISOString();
    }
  }

  function toRfc2822(date) {
    // RFC 2822 is always in local or UTC
    var days = ["Sun","Mon","Tue","Wed","Thu","Fri","Sat"];
    var months = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];
    var d = new Date(date.toLocaleString("en-US", {timeZone: tz}));
    // We'll use UTC representation of the localized time
    try {
      var parts = {};
      new Intl.DateTimeFormat("en-US", {
        timeZone: tz,
        weekday:"short", day:"2-digit", month:"short", year:"numeric",
        hour:"2-digit", minute:"2-digit", second:"2-digit", hour12:false
      }).formatToParts(date).forEach(function(p){ parts[p.type] = p.value; });
      // offset
      var utcMs2 = Date.parse(date.toLocaleString("en-US", {timeZone:"UTC"}));
      var localMs2 = Date.parse(date.toLocaleString("en-US", {timeZone:tz}));
      var diffMin2 = Math.round((localMs2 - utcMs2) / 60000);
      var sign2 = diffMin2 >= 0 ? "+" : "-";
      var abs2 = Math.abs(diffMin2);
      var hh2 = String(Math.floor(abs2/60)).padStart(2,"0");
      var mm2 = String(abs2%60).padStart(2,"0");
      return (parts.weekday||"")+ ", "+(parts.day||"").replace(/\D/g,"")+" "+
             (parts.month||"")+" "+(parts.year||"")+" "+
             (parts.hour||"").replace(/\D/g,"").padStart(2,"0")+":"+
             (parts.minute||"").padStart(2,"0")+":"+
             (parts.second||"").padStart(2,"0")+" "+sign2+hh2+mm2;
    } catch(e) {
      return date.toString();
    }
  }

  function relativeTime(date) {
    var diffMs = Date.now() - date.getTime();
    var abs = Math.abs(diffMs);
    var suffix = diffMs >= 0 ? " ago" : " from now";
    if (abs < 5000)   return "just now";
    if (abs < 60000)  return Math.round(abs/1000)+" seconds"+suffix;
    if (abs < 3600000) return Math.round(abs/60000)+" minutes"+suffix;
    if (abs < 86400000) return Math.round(abs/3600000)+" hours"+suffix;
    if (abs < 2592000000) return Math.round(abs/86400000)+" days"+suffix;
    if (abs < 31536000000) return Math.round(abs/2592000000)+" months"+suffix;
    return Math.round(abs/31536000000)+" years"+suffix;
  }

  function tsToDate(val) {
    var n = parseFloat(val);
    if (isNaN(n)) return null;
    var ms = unit === "ms" ? n : n * 1000;
    return new Date(ms);
  }

  // ── Timestamp → Date ─────────────────────────────────────
  function tsConvertTs() {
    var raw = document.getElementById("ts-ts-input").value.trim();
    var errEl = document.getElementById("ts-ts-error");
    var resEl = document.getElementById("ts-ts-results");
    errEl.textContent = "";
    if (!raw) { resEl.innerHTML = ""; return; }
    var date = tsToDate(raw);
    if (!date || isNaN(date.getTime())) {
      errEl.textContent = "Invalid timestamp. Please enter a valid number.";
      resEl.innerHTML = "";
      return;
    }
    renderDateResults(resEl, date);
  }
  window.tsConvertTs = tsConvertTs;

  function renderDateResults(container, date) {
    var rows = [
      { label: "UTC",        value: date.toUTCString() },
      { label: "Local Time", value: formatInTz(date, tz, {
          weekday:"long", year:"numeric", month:"long", day:"numeric",
          hour:"2-digit", minute:"2-digit", second:"2-digit", timeZoneName:"short"
        })
      },
      { label: "ISO 8601",   value: toIso8601(date, tz) },
      { label: "RFC 2822",   value: toRfc2822(date) },
      { label: "Relative",   value: relativeTime(date) },
      { label: "Unix (sec)", value: String(Math.floor(date.getTime()/1000)) },
      { label: "Unix (ms)",  value: String(date.getTime()) }
    ];
    container.innerHTML = rows.map(function(r) {
      return '<div class="ts-result-row">' +
        '<span class="ts-result-label">'+r.label+'</span>' +
        '<span class="ts-result-value" id="tsrv-'+r.label.replace(/\s/g,"_")+'">'+escHtml(r.value)+'</span>' +
        '<button class="ts-copy-btn" onclick="tsCopy(this,\'tsrv-'+r.label.replace(/\s/g,"_")+'\')">Copy</button>' +
        '</div>';
    }).join("");
  }

  // ── Date → Timestamp ─────────────────────────────────────
  function tsConvertDt() {
    var raw = document.getElementById("ts-dt-input").value;
    var resEl = document.getElementById("ts-dt-results");
    if (!raw) { resEl.innerHTML = ""; return; }
    // datetime-local gives us local browser time; treat as chosen tz
    // We parse it as if it's in the selected timezone
    var date = parseDatetimeLocalAsTz(raw, tz);
    if (!date || isNaN(date.getTime())) { resEl.innerHTML = ""; return; }
    renderDateResults(resEl, date);
  }
  window.tsConvertDt = tsConvertDt;

  function parseDatetimeLocalAsTz(s, timezone) {
    // s = "YYYY-MM-DDTHH:mm"
    // We construct a date assuming s is wall-clock time in timezone
    if (!s) return null;
    var parts = s.match(/^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2})(?::(\d{2}))?$/);
    if (!parts) return null;
    var iso = parts[1]+"-"+parts[2]+"-"+parts[3]+"T"+(parts[4]||"00")+":"+(parts[5]||"00")+":"+(parts[6]||"00");
    // Use a trick: format a reference date in the timezone, find the offset
    // Simple approach: treat the input as UTC first, then adjust
    var naive = new Date(iso + "Z"); // UTC parse
    if (isNaN(naive.getTime())) return null;
    // Get what wall-clock time this UTC moment shows in the target tz
    try {
      var wallStr = naive.toLocaleString("sv-SE", {timeZone: timezone});
      // wallStr = "YYYY-MM-DD HH:mm:ss"
      var wallParts = wallStr.match(/(\d{4})-(\d{2})-(\d{2}) (\d{2}):(\d{2}):(\d{2})/);
      if (!wallParts) return naive;
      var wallMs = Date.UTC(+wallParts[1],+wallParts[2]-1,+wallParts[3],+wallParts[4],+wallParts[5],+wallParts[6]);
      var naiveMs = Date.UTC(+parts[1],+parts[2]-1,+parts[3],+parts[4],+parts[5],+(parts[6]||0));
      var offsetMs = naiveMs - wallMs; // tz offset
      return new Date(naive.getTime() + offsetMs);
    } catch(e) {
      return naive;
    }
  }

  // ── Use Now buttons ──────────────────────────────────────
  function tsUseNow() {
    var now = Date.now();
    var val = unit === "ms" ? now : Math.floor(now / 1000);
    document.getElementById("ts-ts-input").value = val;
    tsConvertTs();
  }
  window.tsUseNow = tsUseNow;

  function tsDtUseNow() {
    var now = new Date();
    // Format for datetime-local input (no seconds needed)
    var y = now.getFullYear();
    var mo = String(now.getMonth()+1).padStart(2,"0");
    var d  = String(now.getDate()).padStart(2,"0");
    var h  = String(now.getHours()).padStart(2,"0");
    var mi = String(now.getMinutes()).padStart(2,"0");
    document.getElementById("ts-dt-input").value = y+"-"+mo+"-"+d+"T"+h+":"+mi;
    tsConvertDt();
  }
  window.tsDtUseNow = tsDtUseNow;

  // ── Copy ─────────────────────────────────────────────────
  function tsCopy(btn, id) {
    var el = document.getElementById(id);
    if (!el) return;
    var text = el.textContent;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(function() { flashCopy(btn); });
    } else {
      var ta = document.createElement("textarea");
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand("copy");
      document.body.removeChild(ta);
      flashCopy(btn);
    }
  }
  window.tsCopy = tsCopy;

  function flashCopy(btn) {
    btn.textContent = "Copied!";
    btn.classList.add("copied");
    setTimeout(function() {
      btn.textContent = "Copy";
      btn.classList.remove("copied");
    }, 1500);
  }

  // ── Reference table ──────────────────────────────────────
  var refEvents = [
    { name: "Unix Epoch",         ts: 0 },
    { name: "Y2K (2000-01-01)",   ts: 946684800 },
    { name: "9/11 (2001-09-11)",  ts: 1000166400 },
    { name: "Unix 1 Billion",     ts: 1000000000 },
    { name: "Unix 1.5 Billion",   ts: 1500000000 },
    { name: "Unix 2 Billion",     ts: 2000000000 },
    { name: "2030-01-01",         ts: 1893456000 },
    { name: "Current Time",       ts: -1 /* live */ },
  ];

  function renderRef() {
    var body = document.getElementById("ts-ref-body");
    if (!body) return;
    body.innerHTML = refEvents.map(function(ev) {
      var secVal = ev.ts === -1 ? Math.floor(Date.now()/1000) : ev.ts;
      var msVal  = ev.ts === -1 ? Date.now() : ev.ts * 1000;
      var displayVal = unit === "ms" ? msVal : secVal;
      var date = new Date(secVal * 1000);
      var utcStr = date.toUTCString();
      var copyId = "tsref-"+ev.name.replace(/\W/g,"_");
      return '<tr>' +
        '<td>'+escHtml(ev.name)+'</td>' +
        '<td class="ts-mono" id="'+copyId+'">'+displayVal+'</td>' +
        '<td>'+escHtml(utcStr)+'</td>' +
        '<td><button class="ts-ref-copy" onclick="tsCopy(this,\''+copyId+'\')">Copy</button></td>' +
        '</tr>';
    }).join("");
  }

  function escHtml(s) {
    return String(s)
      .replace(/&/g,"&amp;")
      .replace(/</g,"&lt;")
      .replace(/>/g,"&gt;")
      .replace(/"/g,"&quot;");
  }

  // ── Init ─────────────────────────────────────────────────
  buildTzSelect();
  startLiveClock();
  renderRef();

})();
</script>
</div>

---

### How Unix Timestamps Work

A **Unix timestamp** (also called epoch time) counts the number of seconds — or milliseconds — elapsed since **January 1, 1970, 00:00:00 UTC**. It is the universal time standard in software: databases, APIs, log files, and programming languages all rely on it.

| Format | Example |
|--------|---------|
| Seconds (standard) | `1700000000` |
| Milliseconds (JavaScript) | `1700000000000` |
| ISO 8601 | `2023-11-14T22:13:20+00:00` |
| RFC 2822 | `Tue, 14 Nov 2023 22:13:20 +0000` |

**Tip:** If your timestamp has 13 digits it is in milliseconds. 10 digits means seconds. Toggle the unit selector above accordingly.

---

### Related Tools

> Convert timezones → [Timezone Converter](/tools/timezone-converter/)
> Generate cron expressions → [Cron Expression Generator](/tools/cron-generator/)
> Calculate age → [Age Calculator](/tools/age-calculator/)
