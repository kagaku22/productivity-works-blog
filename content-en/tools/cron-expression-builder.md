---
title: "Cron Expression Builder"
date: 2025-05-16
description: "Free online cron expression builder. Create and validate cron schedules with a visual interface — see next run times and human-readable descriptions."
categories: ["Free Tools"]
slug: "cron-expression-builder"
ShowToc: false
cover:
  image: "/images/covers/cron-expression-builder.png"
  alt: "Cron Expression Builder"
---

<div id="cr-app">

<style>
#cr-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #e2e8f0;
}

#cr-app * {
  box-sizing: border-box;
}

#cr-app .cr-section {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 20px 24px;
  margin-bottom: 18px;
}

#cr-app .cr-section-title {
  font-size: 13px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #94a3b8;
  margin: 0 0 16px 0;
}

/* Presets */
#cr-app .cr-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

#cr-app .cr-preset-btn {
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 6px;
  color: #cbd5e1;
  padding: 6px 12px;
  font-size: 13px;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s, color 0.15s;
}

#cr-app .cr-preset-btn:hover {
  background: #334155;
  border-color: #64748b;
  color: #f1f5f9;
}

/* Expression display */
#cr-app .cr-expr-row {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}

#cr-app .cr-expr-label {
  font-size: 13px;
  color: #94a3b8;
  white-space: nowrap;
}

#cr-app .cr-expr-input {
  flex: 1;
  min-width: 200px;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 20px;
  font-weight: 700;
  background: #0f172a;
  border: 2px solid #334155;
  border-radius: 8px;
  color: #38bdf8;
  padding: 10px 16px;
  outline: none;
  transition: border-color 0.15s;
  letter-spacing: 0.05em;
}

#cr-app .cr-expr-input:focus {
  border-color: #38bdf8;
}

#cr-app .cr-expr-input.cr-invalid {
  border-color: #ef4444;
  color: #ef4444;
}

#cr-app .cr-copy-btn {
  background: #0369a1;
  border: none;
  border-radius: 6px;
  color: #f0f9ff;
  padding: 10px 18px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
}

#cr-app .cr-copy-btn:hover {
  background: #0284c7;
}

#cr-app .cr-copy-btn.cr-copied {
  background: #16a34a;
}

/* Error message */
#cr-app .cr-error {
  display: none;
  color: #f87171;
  font-size: 13px;
  margin-top: 8px;
  padding: 8px 12px;
  background: #450a0a;
  border: 1px solid #7f1d1d;
  border-radius: 6px;
}

#cr-app .cr-error.cr-visible {
  display: block;
}

/* Description */
#cr-app .cr-description {
  font-size: 16px;
  color: #a5f3fc;
  font-weight: 500;
  min-height: 24px;
}

/* Fields grid */
#cr-app .cr-fields-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 16px;
}

#cr-app .cr-field-card {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 14px 16px;
}

#cr-app .cr-field-name {
  font-size: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #7dd3fc;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

#cr-app .cr-field-range {
  font-weight: 400;
  font-size: 11px;
  color: #64748b;
  text-transform: none;
  letter-spacing: 0;
}

#cr-app .cr-field-mode {
  display: flex;
  gap: 4px;
  margin-bottom: 10px;
  flex-wrap: wrap;
}

#cr-app .cr-mode-btn {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 4px;
  color: #94a3b8;
  padding: 3px 9px;
  font-size: 11px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.12s, color 0.12s, border-color 0.12s;
}

#cr-app .cr-mode-btn:hover {
  background: #334155;
  color: #e2e8f0;
}

#cr-app .cr-mode-btn.cr-active {
  background: #0369a1;
  border-color: #0284c7;
  color: #f0f9ff;
}

#cr-app .cr-field-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
}

#cr-app .cr-select,
#cr-app .cr-input {
  background: #1e293b;
  border: 1px solid #475569;
  border-radius: 5px;
  color: #e2e8f0;
  padding: 5px 10px;
  font-size: 13px;
  outline: none;
  transition: border-color 0.12s;
}

#cr-app .cr-select:focus,
#cr-app .cr-input:focus {
  border-color: #38bdf8;
}

#cr-app .cr-input {
  width: 70px;
  text-align: center;
}

#cr-app .cr-input-wide {
  width: 140px;
  text-align: left;
}

#cr-app .cr-field-label {
  font-size: 12px;
  color: #64748b;
}

/* Field value preview */
#cr-app .cr-field-preview {
  margin-top: 8px;
  font-family: monospace;
  font-size: 13px;
  color: #38bdf8;
  background: #1e293b;
  border-radius: 4px;
  padding: 3px 8px;
  display: inline-block;
}

/* Next runs */
#cr-app .cr-runs-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 6px;
  list-style: none;
  margin: 0;
  padding: 0;
}

#cr-app .cr-run-item {
  background: #0f172a;
  border: 1px solid #1e293b;
  border-radius: 6px;
  padding: 7px 12px;
  font-size: 13px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 8px;
}

#cr-app .cr-run-index {
  color: #475569;
  font-size: 11px;
  min-width: 20px;
  font-weight: 700;
}

#cr-app .cr-run-time {
  font-family: monospace;
  color: #e2e8f0;
  flex: 1;
}

#cr-app .cr-run-rel {
  font-size: 11px;
  color: #64748b;
  white-space: nowrap;
}

/* Cross-links */
#cr-app .cr-links {
  margin-top: 10px;
  padding: 0;
}

#cr-app .cr-links li {
  list-style: none;
  margin-bottom: 6px;
  font-size: 14px;
  color: #94a3b8;
}

#cr-app .cr-links a {
  color: #38bdf8;
  text-decoration: none;
}

#cr-app .cr-links a:hover {
  text-decoration: underline;
}

@media (max-width: 600px) {
  #cr-app .cr-expr-input {
    font-size: 16px;
  }
  #cr-app .cr-fields-grid {
    grid-template-columns: 1fr;
  }
}
</style>

<!-- Presets -->
<div class="cr-section">
  <div class="cr-section-title">Common Presets</div>
  <div class="cr-presets" id="cr-presets"></div>
</div>

<!-- Expression -->
<div class="cr-section">
  <div class="cr-section-title">Cron Expression</div>
  <div class="cr-expr-row">
    <span class="cr-expr-label">Expression:</span>
    <input class="cr-expr-input" id="cr-expr-input" type="text" value="* * * * *" spellcheck="false" autocomplete="off" />
    <button class="cr-copy-btn" id="cr-copy-btn">Copy</button>
  </div>
  <div class="cr-error" id="cr-error"></div>
</div>

<!-- Description -->
<div class="cr-section">
  <div class="cr-section-title">Human-Readable Description</div>
  <div class="cr-description" id="cr-description">Every minute</div>
</div>

<!-- Visual Builder -->
<div class="cr-section">
  <div class="cr-section-title">Visual Builder</div>
  <div class="cr-fields-grid" id="cr-fields-grid"></div>
</div>

<!-- Next Runs -->
<div class="cr-section">
  <div class="cr-section-title">Next 10 Run Times</div>
  <ul class="cr-runs-list" id="cr-runs-list"></ul>
</div>

<!-- Cross-links -->
<div class="cr-section">
  <div class="cr-section-title">Related Tools</div>
  <ul class="cr-links">
    <li>Convert Unix timestamps &rarr; <a href="/tools/timestamp-converter/">Unix Timestamp Converter</a></li>
    <li>Generate Git commands &rarr; <a href="/tools/git-command-generator/">Git Command Generator</a></li>
    <li>Calculate file permissions &rarr; <a href="/tools/chmod-calculator/">Chmod Calculator</a></li>
  </ul>
</div>

<script>
(function () {
  "use strict";

  /* ── Field definitions ── */
  const FIELDS = [
    { id: "minute",  label: "Minute",       min: 0,  max: 59, extras: [] },
    { id: "hour",    label: "Hour",          min: 0,  max: 23, extras: [] },
    { id: "dom",     label: "Day of Month",  min: 1,  max: 31, extras: ["L", "W"] },
    { id: "month",   label: "Month",         min: 1,  max: 12, extras: [] },
    { id: "dow",     label: "Day of Week",   min: 0,  max: 6,  extras: [] },
  ];

  const MONTH_NAMES = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];
  const DOW_NAMES   = ["Sun","Mon","Tue","Wed","Thu","Fri","Sat"];

  /* Mode: every | specific | range | interval */
  const state = {
    minute: { mode: "every", specific: "0", rangeFrom: "0", rangeTo: "59", interval: "5", list: "0" },
    hour:   { mode: "every", specific: "0", rangeFrom: "0", rangeTo: "23", interval: "1", list: "0" },
    dom:    { mode: "every", specific: "1", rangeFrom: "1", rangeTo: "31", interval: "1", list: "1", special: "L" },
    month:  { mode: "every", specific: "1", rangeFrom: "1", rangeTo: "12", interval: "1", list: "1" },
    dow:    { mode: "every", specific: "0", rangeFrom: "0", rangeTo:  "6", interval: "1", list: "0" },
  };

  /* ── Presets ── */
  const PRESETS = [
    { label: "Every minute",        expr: "* * * * *" },
    { label: "Every 5 minutes",     expr: "*/5 * * * *" },
    { label: "Every 15 minutes",    expr: "*/15 * * * *" },
    { label: "Every hour",          expr: "0 * * * *" },
    { label: "Daily at midnight",   expr: "0 0 * * *" },
    { label: "Weekly Mon 9am",      expr: "0 9 * * 1" },
    { label: "Monthly 1st midnight",expr: "0 0 1 * *" },
    { label: "Every weekday 9am",   expr: "0 9 * * 1-5" },
    { label: "Every Sunday noon",   expr: "0 12 * * 0" },
  ];

  /* ── Utility ── */
  function clamp(v, min, max) { return Math.max(min, Math.min(max, v)); }

  function fieldValue(fid) {
    const f = FIELDS.find(x => x.id === fid);
    const s = state[fid];
    switch (s.mode) {
      case "every":    return "*";
      case "specific":
        if (fid === "dom" && (s.specific === "L" || s.specific === "W" || s.specific === "LW")) return s.specific;
        return s.specific;
      case "range":    return s.rangeFrom + "-" + s.rangeTo;
      case "interval": return "*/" + s.interval;
      case "list":     return s.list;
      default:         return "*";
    }
  }

  function buildExpr() {
    return ["minute","hour","dom","month","dow"].map(fieldValue).join(" ");
  }

  /* ── Parse expression back to state ── */
  function parseExpr(expr) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return false;
    const ids = ["minute","hour","dom","month","dow"];
    for (let i = 0; i < 5; i++) {
      const p = parts[i];
      const s = state[ids[i]];
      if (p === "*") {
        s.mode = "every";
      } else if (/^\*\/\d+$/.test(p)) {
        s.mode = "interval";
        s.interval = p.slice(2);
      } else if (/^\d+-\d+$/.test(p)) {
        s.mode = "range";
        const [a, b] = p.split("-");
        s.rangeFrom = a;
        s.rangeTo = b;
      } else if (/^[\d,]+$/.test(p)) {
        if (p.indexOf(",") === -1) {
          s.mode = "specific";
          s.specific = p;
        } else {
          s.mode = "list";
          s.list = p;
        }
      } else if (/^[LW]+$/.test(p) && ids[i] === "dom") {
        s.mode = "specific";
        s.specific = p;
      } else {
        // Complex: treat as list
        s.mode = "list";
        s.list = p;
      }
    }
    return true;
  }

  /* ── Validation ── */
  function validateExpr(expr) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return "Expression must have exactly 5 fields (minute hour dom month dow).";
    const ranges = [[0,59],[0,23],[1,31],[1,12],[0,6]];
    const names  = ["Minute","Hour","Day of Month","Month","Day of Week"];
    for (let i = 0; i < 5; i++) {
      const p = parts[i];
      const [lo, hi] = ranges[i];
      if (p === "*") continue;
      if (/^\*\/(\d+)$/.test(p)) {
        const n = parseInt(RegExp.$1);
        if (n < 1) return names[i] + ": interval must be >= 1.";
        if (n > hi) return names[i] + ": interval " + n + " exceeds max " + hi + ".";
        continue;
      }
      if (/^(\d+)-(\d+)$/.test(p)) {
        const a = parseInt(RegExp.$1), b = parseInt(RegExp.$2);
        if (a < lo || a > hi) return names[i] + ": range start " + a + " out of bounds [" + lo + "-" + hi + "].";
        if (b < lo || b > hi) return names[i] + ": range end " + b + " out of bounds [" + lo + "-" + hi + "].";
        if (a >= b) return names[i] + ": range start must be less than end.";
        continue;
      }
      if (i === 2 && /^[LW]+$/.test(p)) continue;
      if (/^[\d,]+$/.test(p)) {
        const vals = p.split(",").map(Number);
        for (const v of vals) {
          if (v < lo || v > hi) return names[i] + ": value " + v + " out of bounds [" + lo + "-" + hi + "].";
        }
        continue;
      }
      // allow step ranges like 1-5/2
      if (/^\d+-\d+\/\d+$/.test(p)) continue;
      return names[i] + ": unrecognized pattern \"" + p + "\".";
    }
    return null;
  }

  /* ── Human-readable description ── */
  function describe(expr) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return "Invalid expression";
    const [min, hr, dom, mon, dow] = parts;

    function descField(p, unit, names) {
      if (p === "*") return null;
      if (p.startsWith("*/")) return "every " + p.slice(2) + " " + unit + (p.slice(2) === "1" ? "" : "s");
      if (/^\d+-\d+$/.test(p)) {
        const [a,b] = p.split("-").map(Number);
        if (names) return names[a] + " through " + names[b];
        return unit + " " + a + " through " + b;
      }
      if (/^[\d,]+$/.test(p)) {
        const vals = p.split(",").map(Number);
        if (names) return vals.map(v => names[v]).join(", ");
        return "at " + unit + " " + vals.join(", ");
      }
      return p;
    }

    let parts2 = [];

    // Time part
    if (min === "*" && hr === "*") {
      parts2.push("every minute");
    } else if (min.startsWith("*/") && hr === "*") {
      parts2.push("every " + min.slice(2) + " minutes");
    } else if (hr.startsWith("*/") && min === "0") {
      parts2.push("every " + hr.slice(2) + " hours");
    } else if (hr.startsWith("*/")) {
      parts2.push("every " + hr.slice(2) + " hours at minute " + min);
    } else if (min === "*") {
      const h = parseInt(hr);
      if (!isNaN(h)) {
        const ampm = h < 12 ? "AM" : "PM";
        const h12 = h === 0 ? 12 : h > 12 ? h - 12 : h;
        parts2.push("every minute between " + h12 + ":00 " + ampm + " and " + h12 + ":59 " + ampm);
      } else {
        parts2.push("every minute of hour " + hr);
      }
    } else {
      const h = parseInt(hr), m = parseInt(min);
      if (!isNaN(h) && !isNaN(m)) {
        const ampm = h < 12 ? "AM" : "PM";
        const h12 = h === 0 ? 12 : h > 12 ? h - 12 : h;
        const mm = m < 10 ? "0" + m : "" + m;
        parts2.push("at " + h12 + ":" + mm + " " + ampm);
      } else {
        const md = descField(min, "minute", null);
        const hd = descField(hr, "hour", null);
        if (md) parts2.push(md);
        if (hd) parts2.push(hd);
      }
    }

    // Day of week
    if (dow !== "*") {
      if (dow === "1-5") parts2.push("on weekdays");
      else if (dow === "6-0" || dow === "0,6" || dow === "6,0") parts2.push("on weekends");
      else {
        const d = descField(dow, "day", DOW_NAMES);
        if (d) parts2.push("on " + d);
      }
    }

    // Day of month
    if (dom !== "*") {
      if (dom === "L") parts2.push("on the last day of the month");
      else if (dom === "LW") parts2.push("on the last weekday of the month");
      else {
        const d = descField(dom, "day", null);
        if (d) parts2.push("on day " + dom + " of the month");
      }
    }

    // Month
    if (mon !== "*") {
      const d = descField(mon, "month", MONTH_NAMES);
      if (d) parts2.push("in " + d);
    }

    if (parts2.length === 0) return "Every minute";
    return parts2.join(", ").replace(/^./, c => c.toUpperCase());
  }

  /* ── Next run times ── */
  function matchesField(val, p, lo) {
    if (p === "*") return true;
    if (p === "L") return true; // simplified
    if (p === "W") return true;
    if (p.startsWith("*/")) {
      const step = parseInt(p.slice(2));
      return (val - lo) % step === 0;
    }
    if (/^\d+-\d+$/.test(p)) {
      const [a, b] = p.split("-").map(Number);
      return val >= a && val <= b;
    }
    if (/^\d+-\d+\/\d+$/.test(p)) {
      const m = p.match(/^(\d+)-(\d+)\/(\d+)$/);
      const a = parseInt(m[1]), b = parseInt(m[2]), step = parseInt(m[3]);
      if (val < a || val > b) return false;
      return (val - a) % step === 0;
    }
    if (/^[\d,]+$/.test(p)) {
      return p.split(",").map(Number).includes(val);
    }
    return false;
  }

  function nextRuns(expr, count) {
    const parts = expr.trim().split(/\s+/);
    if (parts.length !== 5) return [];
    const [minP, hrP, domP, monP, dowP] = parts;

    const results = [];
    const now = new Date();
    // Start from the next minute
    let cur = new Date(now.getFullYear(), now.getMonth(), now.getDate(), now.getHours(), now.getMinutes() + 1, 0, 0);

    const MAX_ITER = 366 * 24 * 60 * 2; // 2 years of minutes
    let iter = 0;

    while (results.length < count && iter < MAX_ITER) {
      iter++;
      const mn = cur.getMinutes();
      const hr = cur.getHours();
      const dom = cur.getDate();
      const mon = cur.getMonth() + 1; // 1-12
      const dow = cur.getDay();       // 0-6

      if (
        matchesField(mon, monP, 1) &&
        matchesField(dom, domP, 1) &&
        matchesField(dow, dowP, 0) &&
        matchesField(hr,  hrP,  0) &&
        matchesField(mn,  minP, 0)
      ) {
        results.push(new Date(cur));
      }

      cur = new Date(cur.getTime() + 60000);
    }

    return results;
  }

  function relTime(d) {
    const diff = d - Date.now();
    const sec = Math.round(diff / 1000);
    if (sec < 60) return "in " + sec + "s";
    const min = Math.round(sec / 60);
    if (min < 60) return "in " + min + "m";
    const hr = Math.round(min / 60);
    if (hr < 24) return "in " + hr + "h";
    const day = Math.round(hr / 24);
    return "in " + day + "d";
  }

  function formatDate(d) {
    const pad = n => n < 10 ? "0" + n : "" + n;
    const days = ["Sun","Mon","Tue","Wed","Thu","Fri","Sat"];
    return days[d.getDay()] + " " +
      d.getFullYear() + "-" + pad(d.getMonth()+1) + "-" + pad(d.getDate()) +
      " " + pad(d.getHours()) + ":" + pad(d.getMinutes());
  }

  /* ── Render ── */
  function renderPresets() {
    const container = document.getElementById("cr-presets");
    container.innerHTML = "";
    PRESETS.forEach(p => {
      const btn = document.createElement("button");
      btn.className = "cr-preset-btn";
      btn.textContent = p.label;
      btn.addEventListener("click", () => {
        const input = document.getElementById("cr-expr-input");
        input.value = p.expr;
        onExprInput(p.expr);
      });
      container.appendChild(btn);
    });
  }

  function renderFields() {
    const grid = document.getElementById("cr-fields-grid");
    grid.innerHTML = "";

    FIELDS.forEach(f => {
      const s = state[f.id];
      const card = document.createElement("div");
      card.className = "cr-field-card";
      card.id = "cr-field-" + f.id;

      // Header
      const header = document.createElement("div");
      header.className = "cr-field-name";
      header.innerHTML = f.label + ' <span class="cr-field-range">' + f.min + '–' + f.max + '</span>';
      card.appendChild(header);

      // Mode buttons
      const modeRow = document.createElement("div");
      modeRow.className = "cr-field-mode";
      const modes = ["every","specific","range","interval","list"];
      modes.forEach(m => {
        const btn = document.createElement("button");
        btn.className = "cr-mode-btn" + (s.mode === m ? " cr-active" : "");
        btn.textContent = m.charAt(0).toUpperCase() + m.slice(1);
        btn.dataset.field = f.id;
        btn.dataset.mode = m;
        btn.addEventListener("click", () => {
          state[f.id].mode = m;
          renderFields();
          updateAll();
        });
        modeRow.appendChild(btn);
      });
      card.appendChild(modeRow);

      // Controls
      const controls = document.createElement("div");
      controls.className = "cr-field-controls";

      if (s.mode === "every") {
        const lbl = document.createElement("span");
        lbl.className = "cr-field-label";
        lbl.textContent = "Every " + f.label.toLowerCase();
        controls.appendChild(lbl);
      }

      if (s.mode === "specific") {
        if (f.extras && f.extras.length > 0) {
          // Show a select with numbers + special values
          const sel = document.createElement("select");
          sel.className = "cr-select";
          for (let v = f.min; v <= f.max; v++) {
            const o = document.createElement("option");
            o.value = v;
            o.textContent = formatFieldVal(f.id, v);
            if (String(v) === s.specific) o.selected = true;
            sel.appendChild(o);
          }
          f.extras.forEach(e => {
            const o = document.createElement("option");
            o.value = e;
            o.textContent = e;
            if (e === s.specific) o.selected = true;
            sel.appendChild(o);
          });
          sel.addEventListener("change", () => {
            state[f.id].specific = sel.value;
            updateAll();
          });
          controls.appendChild(sel);
        } else {
          const sel = document.createElement("select");
          sel.className = "cr-select";
          for (let v = f.min; v <= f.max; v++) {
            const o = document.createElement("option");
            o.value = v;
            o.textContent = formatFieldVal(f.id, v);
            if (String(v) === s.specific) o.selected = true;
            sel.appendChild(o);
          }
          sel.addEventListener("change", () => {
            state[f.id].specific = sel.value;
            updateAll();
          });
          controls.appendChild(sel);
        }
      }

      if (s.mode === "range") {
        const lblFrom = document.createElement("span");
        lblFrom.className = "cr-field-label";
        lblFrom.textContent = "From";
        controls.appendChild(lblFrom);

        const selFrom = document.createElement("select");
        selFrom.className = "cr-select";
        for (let v = f.min; v <= f.max; v++) {
          const o = document.createElement("option");
          o.value = v;
          o.textContent = formatFieldVal(f.id, v);
          if (String(v) === s.rangeFrom) o.selected = true;
          selFrom.appendChild(o);
        }
        selFrom.addEventListener("change", () => {
          state[f.id].rangeFrom = selFrom.value;
          updateAll();
        });
        controls.appendChild(selFrom);

        const lblTo = document.createElement("span");
        lblTo.className = "cr-field-label";
        lblTo.textContent = "to";
        controls.appendChild(lblTo);

        const selTo = document.createElement("select");
        selTo.className = "cr-select";
        for (let v = f.min; v <= f.max; v++) {
          const o = document.createElement("option");
          o.value = v;
          o.textContent = formatFieldVal(f.id, v);
          if (String(v) === s.rangeTo) o.selected = true;
          selTo.appendChild(o);
        }
        selTo.addEventListener("change", () => {
          state[f.id].rangeTo = selTo.value;
          updateAll();
        });
        controls.appendChild(selTo);
      }

      if (s.mode === "interval") {
        const lbl = document.createElement("span");
        lbl.className = "cr-field-label";
        lbl.textContent = "Every";
        controls.appendChild(lbl);

        const inp = document.createElement("input");
        inp.className = "cr-input";
        inp.type = "number";
        inp.min = 1;
        inp.max = f.max;
        inp.value = s.interval;
        inp.addEventListener("input", () => {
          state[f.id].interval = inp.value;
          updateAll();
        });
        controls.appendChild(inp);

        const lbl2 = document.createElement("span");
        lbl2.className = "cr-field-label";
        lbl2.textContent = f.label.toLowerCase() + "(s)";
        controls.appendChild(lbl2);
      }

      if (s.mode === "list") {
        const lbl = document.createElement("span");
        lbl.className = "cr-field-label";
        lbl.textContent = "Values (comma-separated):";
        controls.appendChild(lbl);

        const inp = document.createElement("input");
        inp.className = "cr-input cr-input-wide";
        inp.type = "text";
        inp.value = s.list;
        inp.placeholder = f.min + "," + (f.min+1);
        inp.addEventListener("input", () => {
          state[f.id].list = inp.value;
          updateAll();
        });
        controls.appendChild(inp);
      }

      card.appendChild(controls);

      // Preview
      const preview = document.createElement("div");
      preview.className = "cr-field-preview";
      preview.textContent = fieldValue(f.id);
      preview.id = "cr-preview-" + f.id;
      card.appendChild(preview);

      grid.appendChild(card);
    });
  }

  function formatFieldVal(fid, v) {
    if (fid === "month") return v + " – " + MONTH_NAMES[v-1];
    if (fid === "dow")   return v + " – " + DOW_NAMES[v];
    return String(v);
  }

  function updateAll() {
    const expr = buildExpr();
    const input = document.getElementById("cr-expr-input");
    input.value = expr;
    refreshOutput(expr);
    updatePreviews();
  }

  function updatePreviews() {
    FIELDS.forEach(f => {
      const el = document.getElementById("cr-preview-" + f.id);
      if (el) el.textContent = fieldValue(f.id);
    });
  }

  function refreshOutput(expr) {
    const errEl  = document.getElementById("cr-error");
    const descEl = document.getElementById("cr-description");
    const input  = document.getElementById("cr-expr-input");
    const runsList = document.getElementById("cr-runs-list");

    const err = validateExpr(expr);
    if (err) {
      errEl.textContent = err;
      errEl.classList.add("cr-visible");
      input.classList.add("cr-invalid");
      descEl.textContent = "—";
      runsList.innerHTML = "";
      return;
    }

    errEl.classList.remove("cr-visible");
    input.classList.remove("cr-invalid");
    descEl.textContent = describe(expr);

    // Next runs
    const runs = nextRuns(expr, 10);
    runsList.innerHTML = "";
    runs.forEach((d, i) => {
      const li = document.createElement("li");
      li.className = "cr-run-item";
      li.innerHTML =
        '<span class="cr-run-index">' + (i+1) + '</span>' +
        '<span class="cr-run-time">' + formatDate(d) + '</span>' +
        '<span class="cr-run-rel">' + relTime(d) + '</span>';
      runsList.appendChild(li);
    });

    if (runs.length === 0) {
      const li = document.createElement("li");
      li.className = "cr-run-item";
      li.innerHTML = '<span style="color:#64748b;">Could not compute next runs for this expression.</span>';
      runsList.appendChild(li);
    }
  }

  function onExprInput(expr) {
    const ok = parseExpr(expr);
    if (ok) {
      renderFields();
    }
    refreshOutput(expr);
  }

  /* ── Copy button ── */
  function initCopy() {
    const btn = document.getElementById("cr-copy-btn");
    btn.addEventListener("click", () => {
      const expr = document.getElementById("cr-expr-input").value;
      navigator.clipboard.writeText(expr).then(() => {
        btn.textContent = "Copied!";
        btn.classList.add("cr-copied");
        setTimeout(() => {
          btn.textContent = "Copy";
          btn.classList.remove("cr-copied");
        }, 1500);
      }).catch(() => {
        // Fallback
        const ta = document.createElement("textarea");
        ta.value = expr;
        ta.style.position = "fixed";
        ta.style.opacity = "0";
        document.body.appendChild(ta);
        ta.select();
        document.execCommand("copy");
        document.body.removeChild(ta);
        btn.textContent = "Copied!";
        btn.classList.add("cr-copied");
        setTimeout(() => {
          btn.textContent = "Copy";
          btn.classList.remove("cr-copied");
        }, 1500);
      });
    });
  }

  /* ── Expression input (bidirectional) ── */
  function initExprInput() {
    const input = document.getElementById("cr-expr-input");
    input.addEventListener("input", () => {
      onExprInput(input.value);
    });
    input.addEventListener("keydown", e => {
      if (e.key === "Enter") onExprInput(input.value);
    });
  }

  /* ── Init ── */
  function init() {
    renderPresets();
    renderFields();
    updateAll();
    initCopy();
    initExprInput();
  }

  if (document.readyState === "loading") {
    document.addEventListener("DOMContentLoaded", init);
  } else {
    init();
  }
})();
</script>

</div>

## Related Articles

- [How to Automate Tasks with AI Step by Step](/posts/how-to-automate-tasks-with-ai-step-by-step/)
