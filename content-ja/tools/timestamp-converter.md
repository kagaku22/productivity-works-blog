---
title: "Unixタイムスタンプ変換ツール — エポック時間"
date: 2025-05-16
description: "Unixタイムスタンプを日時に変換、またはその逆。ライブクロック・複数フォーマット・ミリ秒対応・タイムゾーン選択。無料・登録不要。"
categories: ["無料ツール"]
slug: "timestamp-converter"
ShowToc: false
aliases:
  - "/ja/tools/unix-timestamp/"
  - "/ja/tools/epoch-converter/"
cover:
  image: "/images/covers/timestamp-converter-ja.png"
  alt: "Unixタイムスタンプ変換ツール"
---

**Unixタイムスタンプを瞬時に変換** — エポック値を貼り付けると人間が読める日時を表示。日時を入力するとタイムスタンプに変換。ライブクロック・複数フォーマット・ミリ秒対応・タイムゾーン選択付き。

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
    font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo,
                 -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    font-size: 15px;
    line-height: 1.7;
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
    font-size: 12px;
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
    letter-spacing: 0.06em;
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
    font-family: inherit;
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
    font-family: inherit;
  }
  #ts-app .ts-btn:hover { background: #4f46e5; }
  #ts-app .ts-btn:active { transform: scale(0.97); }
  #ts-app .ts-btn-secondary {
    background: #fff;
    color: #6366f1;
    border: 1px solid #c7d0ea;
  }
  #ts-app .ts-btn-secondary:hover { background: #eef0ff; }
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
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: #888;
    min-width: 120px;
    flex-shrink: 0;
  }
  #ts-app .ts-result-value {
    font-family: "SFMono-Regular", Consolas, monospace;
    font-size: 13px;
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
    font-family: inherit;
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
    font-size: 11px;
    font-weight: 700;
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
  #ts-app .ts-ref-table tr:last-child td { border-bottom: none; }
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
    font-family: inherit;
  }
  #ts-app .ts-ref-table .ts-ref-copy:hover {
    background: #6366f1;
    color: #fff;
    border-color: #6366f1;
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
  #ts-app select.ts-tz-select { min-width: 220px; }
  #ts-app .ts-freee-cta {
    background: #fff7ed;
    border: 1px solid #fed7aa;
    border-radius: 10px;
    padding: 18px 22px;
    margin-top: 24px;
  }
  #ts-app .ts-freee-cta-title {
    font-size: 14px;
    font-weight: 700;
    color: #c2410c;
    margin-bottom: 6px;
  }
  #ts-app .ts-freee-cta p {
    font-size: 13px;
    color: #7c3a1e;
    margin-bottom: 10px;
  }
  #ts-app .ts-freee-btn {
    display: inline-block;
    padding: 9px 22px;
    background: #f97316;
    color: #fff;
    font-weight: 700;
    font-size: 14px;
    border-radius: 6px;
    text-decoration: none;
    transition: background 0.15s;
  }
  #ts-app .ts-freee-btn:hover { background: #ea6c00; }
  @media (max-width: 540px) {
    #ts-app .ts-live-value { font-size: 26px; }
    #ts-app .ts-result-label { min-width: 100px; }
    #ts-app .ts-ref-table { font-size: 12px; }
    #ts-app .ts-ref-table th, #ts-app .ts-ref-table td { padding: 7px 6px; }
  }
</style>

<!-- ライブクロック -->
<div class="ts-live-clock">
  <div class="ts-live-label">現在のUnixタイムスタンプ（自動更新）</div>
  <div class="ts-live-value" id="ts-live-val">—</div>
  <div class="ts-live-sub" id="ts-live-sub">—</div>
</div>

<!-- グローバル設定 -->
<div class="ts-section">
  <div class="ts-section-title">共通設定</div>
  <div class="ts-controls-row">
    <span style="font-size:13px;font-weight:600;color:#555;">単位：</span>
    <div class="ts-toggle-group">
      <button class="ts-toggle-btn active" id="ts-unit-sec" onclick="tsSetUnit('s')">秒（seconds）</button>
      <button class="ts-toggle-btn" id="ts-unit-ms" onclick="tsSetUnit('ms')">ミリ秒（ms）</button>
    </div>
  </div>
  <div class="ts-tz-row">
    <span class="ts-tz-label">タイムゾーン：</span>
    <select class="ts-tz-select" id="ts-tz-select" onchange="tsOnTzChange()"></select>
  </div>
</div>

<!-- タイムスタンプ → 日時 -->
<div class="ts-section">
  <div class="ts-section-title">タイムスタンプ → 日時に変換</div>
  <div class="ts-input-row">
    <input type="number" class="ts-input-wide" id="ts-ts-input"
      placeholder="タイムスタンプを入力（例：1700000000）" oninput="tsConvertTs()" />
    <button class="ts-btn ts-btn-secondary" onclick="tsUseNow()">現在時刻を使用</button>
  </div>
  <div class="ts-error" id="ts-ts-error"></div>
  <div class="ts-results" id="ts-ts-results"></div>
</div>

<!-- 日時 → タイムスタンプ -->
<div class="ts-section">
  <div class="ts-section-title">日時 → タイムスタンプに変換</div>
  <div class="ts-input-row">
    <input type="datetime-local" id="ts-dt-input" oninput="tsConvertDt()" />
    <button class="ts-btn ts-btn-secondary" onclick="tsDtUseNow()">現在時刻を使用</button>
  </div>
  <div class="ts-results" id="ts-dt-results"></div>
</div>

<!-- よく使うタイムスタンプ -->
<div class="ts-section">
  <div class="ts-section-title">よく使うタイムスタンプ（参照用）</div>
  <table class="ts-ref-table">
    <thead>
      <tr>
        <th>イベント</th>
        <th>Unix（秒）</th>
        <th>日時（UTC）</th>
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
  var unit = "s";
  var tz = Intl.DateTimeFormat().resolvedOptions().timeZone;
  var liveTimer = null;

  // ── ラベル（日本語） ─────────────────────────────────────
  var LABELS = {
    utc:      "UTC",
    local:    "現地時刻",
    iso:      "ISO 8601",
    rfc:      "RFC 2822",
    relative: "相対時間",
    unixSec:  "Unix（秒）",
    unixMs:   "Unix（ミリ秒）"
  };

  // ── タイムゾーンリスト ───────────────────────────────────
  var commonTzList = [
    "UTC",
    "Asia/Tokyo","Asia/Seoul","Asia/Shanghai","Asia/Singapore","Asia/Bangkok",
    "Asia/Kolkata","Asia/Dubai","Asia/Dhaka",
    "Europe/London","Europe/Paris","Europe/Berlin","Europe/Moscow","Europe/Istanbul",
    "America/New_York","America/Chicago","America/Denver","America/Los_Angeles",
    "America/Sao_Paulo","America/Toronto","America/Vancouver",
    "Australia/Sydney","Pacific/Auckland","Pacific/Honolulu"
  ];

  function buildTzSelect() {
    var sel = document.getElementById("ts-tz-select");
    var allTz = [];
    try {
      if (Intl.supportedValuesOf) allTz = Intl.supportedValuesOf("timeZone");
    } catch(e) {}
    if (allTz.length === 0) allTz = commonTzList;
    var seen = {}, sorted = [];
    allTz.forEach(function(z) { if (!seen[z]) { seen[z]=1; sorted.push(z); } });
    sorted.sort();
    var localTz = Intl.DateTimeFormat().resolvedOptions().timeZone;
    sel.innerHTML = "";
    sorted.forEach(function(z) {
      var opt = document.createElement("option");
      opt.value = z; opt.textContent = z;
      if (z === localTz) opt.selected = true;
      sel.appendChild(opt);
    });
    tz = sel.value;
  }

  function tsOnTzChange() {
    tz = document.getElementById("ts-tz-select").value;
    tsConvertTs(); tsConvertDt(); renderRef();
  }
  window.tsOnTzChange = tsOnTzChange;

  // ── 単位切り替え ─────────────────────────────────────────
  function tsSetUnit(u) {
    unit = u;
    document.getElementById("ts-unit-sec").classList.toggle("active", u === "s");
    document.getElementById("ts-unit-ms").classList.toggle("active", u === "ms");
    startLiveClock();
    tsConvertTs(); tsConvertDt(); renderRef();
  }
  window.tsSetUnit = tsSetUnit;

  // ── ライブクロック ───────────────────────────────────────
  function startLiveClock() {
    if (liveTimer) clearInterval(liveTimer);
    tickClock();
    liveTimer = setInterval(tickClock, unit === "ms" ? 100 : 1000);
  }

  function tickClock() {
    var now = Date.now();
    var val = unit === "ms" ? now : Math.floor(now / 1000);
    document.getElementById("ts-live-val").textContent = val.toLocaleString("ja-JP");
    document.getElementById("ts-live-sub").textContent =
      formatInTz(new Date(now), tz, {
        year:"numeric", month:"2-digit", day:"2-digit",
        hour:"2-digit", minute:"2-digit", second:"2-digit",
        timeZoneName:"short"
      });
  }

  // ── ユーティリティ ───────────────────────────────────────
  function formatInTz(date, timezone, opts) {
    try {
      return date.toLocaleString("ja-JP", Object.assign({timeZone: timezone}, opts));
    } catch(e) {
      return date.toLocaleString("ja-JP", opts);
    }
  }

  function toIso8601(date, timezone) {
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
      var utcMs = Date.parse(date.toLocaleString("en-US", {timeZone:"UTC"}));
      var localMs = Date.parse(date.toLocaleString("en-US", {timeZone:timezone}));
      var diffMin = Math.round((localMs - utcMs) / 60000);
      var sign = diffMin >= 0 ? "+" : "-";
      var abs = Math.abs(diffMin);
      var hh = String(Math.floor(abs/60)).padStart(2,"0");
      var mm = String(abs%60).padStart(2,"0");
      return base + sign + hh + ":" + mm;
    } catch(e) { return date.toISOString(); }
  }

  function toRfc2822(date) {
    try {
      var parts = {};
      new Intl.DateTimeFormat("en-US", {
        timeZone: tz,
        weekday:"short", day:"2-digit", month:"short", year:"numeric",
        hour:"2-digit", minute:"2-digit", second:"2-digit", hour12:false
      }).formatToParts(date).forEach(function(p){ parts[p.type] = p.value; });
      var utcMs2 = Date.parse(date.toLocaleString("en-US", {timeZone:"UTC"}));
      var localMs2 = Date.parse(date.toLocaleString("en-US", {timeZone:tz}));
      var diffMin2 = Math.round((localMs2 - utcMs2) / 60000);
      var sign2 = diffMin2 >= 0 ? "+" : "-";
      var abs2 = Math.abs(diffMin2);
      var hh2 = String(Math.floor(abs2/60)).padStart(2,"0");
      var mm2 = String(abs2%60).padStart(2,"0");
      return (parts.weekday||"")+", "+(parts.day||"").replace(/\D/g,"")+" "+
             (parts.month||"")+" "+(parts.year||"")+" "+
             (parts.hour||"").replace(/\D/g,"").padStart(2,"0")+":"+
             (parts.minute||"").padStart(2,"0")+":"+
             (parts.second||"").padStart(2,"0")+" "+sign2+hh2+mm2;
    } catch(e) { return date.toString(); }
  }

  function relativeTime(date) {
    var diffMs = Date.now() - date.getTime();
    var abs = Math.abs(diffMs);
    var suffix = diffMs >= 0 ? "前" : "後";
    if (abs < 5000)    return "たった今";
    if (abs < 60000)   return Math.round(abs/1000)+"秒"+suffix;
    if (abs < 3600000) return Math.round(abs/60000)+"分"+suffix;
    if (abs < 86400000) return Math.round(abs/3600000)+"時間"+suffix;
    if (abs < 2592000000) return Math.round(abs/86400000)+"日"+suffix;
    if (abs < 31536000000) return Math.round(abs/2592000000)+"ヶ月"+suffix;
    return Math.round(abs/31536000000)+"年"+suffix;
  }

  function tsToDate(val) {
    var n = parseFloat(val);
    if (isNaN(n)) return null;
    return new Date(unit === "ms" ? n : n * 1000);
  }

  // ── タイムスタンプ → 日時 ────────────────────────────────
  function tsConvertTs() {
    var raw = document.getElementById("ts-ts-input").value.trim();
    var errEl = document.getElementById("ts-ts-error");
    var resEl = document.getElementById("ts-ts-results");
    errEl.textContent = "";
    if (!raw) { resEl.innerHTML = ""; return; }
    var date = tsToDate(raw);
    if (!date || isNaN(date.getTime())) {
      errEl.textContent = "無効なタイムスタンプです。数値を入力してください。";
      resEl.innerHTML = ""; return;
    }
    renderDateResults(resEl, date);
  }
  window.tsConvertTs = tsConvertTs;

  function renderDateResults(container, date) {
    var rows = [
      { label: LABELS.utc,     value: date.toUTCString() },
      { label: LABELS.local,   value: formatInTz(date, tz, {
          year:"numeric", month:"long", day:"numeric", weekday:"long",
          hour:"2-digit", minute:"2-digit", second:"2-digit", timeZoneName:"short"
        })
      },
      { label: LABELS.iso,     value: toIso8601(date, tz) },
      { label: LABELS.rfc,     value: toRfc2822(date) },
      { label: LABELS.relative, value: relativeTime(date) },
      { label: LABELS.unixSec, value: String(Math.floor(date.getTime()/1000)) },
      { label: LABELS.unixMs,  value: String(date.getTime()) }
    ];
    container.innerHTML = rows.map(function(r) {
      var id = "tsrv-ja-"+r.label.replace(/[^\w]/g,"_");
      return '<div class="ts-result-row">' +
        '<span class="ts-result-label">'+r.label+'</span>' +
        '<span class="ts-result-value" id="'+id+'">'+escHtml(r.value)+'</span>' +
        '<button class="ts-copy-btn" onclick="tsCopy(this,\''+id+'\')">コピー</button>' +
        '</div>';
    }).join("");
  }

  // ── 日時 → タイムスタンプ ────────────────────────────────
  function tsConvertDt() {
    var raw = document.getElementById("ts-dt-input").value;
    var resEl = document.getElementById("ts-dt-results");
    if (!raw) { resEl.innerHTML = ""; return; }
    var date = parseDatetimeLocalAsTz(raw, tz);
    if (!date || isNaN(date.getTime())) { resEl.innerHTML = ""; return; }
    renderDateResults(resEl, date);
  }
  window.tsConvertDt = tsConvertDt;

  function parseDatetimeLocalAsTz(s, timezone) {
    if (!s) return null;
    var parts = s.match(/^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2})(?::(\d{2}))?$/);
    if (!parts) return null;
    var iso = parts[1]+"-"+parts[2]+"-"+parts[3]+"T"+(parts[4]||"00")+":"+(parts[5]||"00")+":"+(parts[6]||"00");
    var naive = new Date(iso + "Z");
    if (isNaN(naive.getTime())) return null;
    try {
      var wallStr = naive.toLocaleString("sv-SE", {timeZone: timezone});
      var wParts = wallStr.match(/(\d{4})-(\d{2})-(\d{2}) (\d{2}):(\d{2}):(\d{2})/);
      if (!wParts) return naive;
      var wallMs = Date.UTC(+wParts[1],+wParts[2]-1,+wParts[3],+wParts[4],+wParts[5],+wParts[6]);
      var naiveMs = Date.UTC(+parts[1],+parts[2]-1,+parts[3],+parts[4],+parts[5],+(parts[6]||0));
      return new Date(naive.getTime() + (naiveMs - wallMs));
    } catch(e) { return naive; }
  }

  // ── 現在時刻ボタン ───────────────────────────────────────
  function tsUseNow() {
    var now = Date.now();
    document.getElementById("ts-ts-input").value = unit === "ms" ? now : Math.floor(now/1000);
    tsConvertTs();
  }
  window.tsUseNow = tsUseNow;

  function tsDtUseNow() {
    var now = new Date();
    var y  = now.getFullYear();
    var mo = String(now.getMonth()+1).padStart(2,"0");
    var d  = String(now.getDate()).padStart(2,"0");
    var h  = String(now.getHours()).padStart(2,"0");
    var mi = String(now.getMinutes()).padStart(2,"0");
    document.getElementById("ts-dt-input").value = y+"-"+mo+"-"+d+"T"+h+":"+mi;
    tsConvertDt();
  }
  window.tsDtUseNow = tsDtUseNow;

  // ── コピー ───────────────────────────────────────────────
  function tsCopy(btn, id) {
    var el = document.getElementById(id);
    if (!el) return;
    var text = el.textContent;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(function() { flashCopy(btn); });
    } else {
      var ta = document.createElement("textarea");
      ta.value = text;
      document.body.appendChild(ta); ta.select();
      document.execCommand("copy"); document.body.removeChild(ta);
      flashCopy(btn);
    }
  }
  window.tsCopy = tsCopy;

  function flashCopy(btn) {
    var orig = btn.textContent;
    btn.textContent = "コピー済み！";
    btn.classList.add("copied");
    setTimeout(function() { btn.textContent = orig; btn.classList.remove("copied"); }, 1500);
  }

  // ── 参照テーブル ─────────────────────────────────────────
  var refEvents = [
    { name: "Unixエポック（基準点）",      ts: 0 },
    { name: "Y2K（2000年1月1日）",         ts: 946684800 },
    { name: "9.11テロ（2001年9月11日）",   ts: 1000166400 },
    { name: "Unix 10億秒",                 ts: 1000000000 },
    { name: "Unix 15億秒",                 ts: 1500000000 },
    { name: "Unix 20億秒",                 ts: 2000000000 },
    { name: "2030年1月1日",                ts: 1893456000 },
    { name: "現在時刻",                    ts: -1 },
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
      var copyId = "tsref-ja-"+ev.name.replace(/[^\w]/g,"_");
      return '<tr>'+
        '<td>'+escHtml(ev.name)+'</td>'+
        '<td class="ts-mono" id="'+copyId+'">'+displayVal+'</td>'+
        '<td>'+escHtml(utcStr)+'</td>'+
        '<td><button class="ts-ref-copy" onclick="tsCopy(this,\''+copyId+'\')">コピー</button></td>'+
        '</tr>';
    }).join("");
  }

  function escHtml(s) {
    return String(s)
      .replace(/&/g,"&amp;").replace(/</g,"&lt;")
      .replace(/>/g,"&gt;").replace(/"/g,"&quot;");
  }

  // ── 初期化 ───────────────────────────────────────────────
  buildTzSelect();
  startLiveClock();
  renderRef();

})();
</script>

<!-- freee CTA -->
<div class="ts-freee-cta">
  <div class="ts-freee-cta-title">freeeで会計・請求書をもっとラクに</div>
  <p>タイムスタンプの確認だけでなく、日々の会計処理・請求書発行・給与計算も自動化しませんか？freeeならタイムログ・経費精算・確定申告まで一括管理できます。</p>
  <a class="ts-freee-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">freeeを無料で試す</a>
</div>
</div>

---

### Unixタイムスタンプとは？

**Unixタイムスタンプ**（エポック時間）は、**1970年1月1日 00:00:00 UTC** から経過した秒数（またはミリ秒数）です。データベース・API・ログファイル・プログラミング言語で広く使われる共通の時間表現です。

| フォーマット | 例 |
|---|---|
| 秒（標準） | `1700000000` |
| ミリ秒（JavaScript等） | `1700000000000` |
| ISO 8601 | `2023-11-15T07:13:20+09:00` |
| RFC 2822 | `Wed, 15 Nov 2023 07:13:20 +0900` |

**ヒント：** 13桁ならミリ秒、10桁なら秒です。上の単位セレクターで切り替えてください。

---

### 関連ツール

> タイムゾーンを変換 → [タイムゾーン変換ツール](/ja/tools/timezone-converter/)
> Cron式を生成 → [Cron式ジェネレーター](/ja/tools/cron-generator/)
> 年齢を計算 → [年齢計算ツール](/ja/tools/age-calculator/)
