---
title: "Timezone Clock Dashboard"
date: 2025-05-16
description: "Free world clock dashboard. Display live clocks for multiple timezones. Add/remove cities, see time differences, day/night indicator, and 12/24 hour toggle."
categories: ["Free Tools"]
slug: "timezone-clock"
ShowToc: false
aliases: ["/tools/world-time/"]
cover:
  image: "/images/covers/timezone-clock.png"
  alt: "Timezone Clock Dashboard"
---

<div id="tzc-app">
<style>
#tzc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #1e293b;
  box-sizing: border-box;
}
#tzc-app *, #tzc-app *::before, #tzc-app *::after {
  box-sizing: border-box;
}
#tzc-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 12px 0;
  color: #0f172a;
}
#tzc-app .tzc-topbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 16px;
}
#tzc-app .tzc-toggle {
  display: flex;
  background: #f1f5f9;
  border-radius: 8px;
  padding: 3px;
  gap: 2px;
}
#tzc-app .tzc-toggle button {
  padding: 5px 14px;
  border: none;
  background: transparent;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#tzc-app .tzc-toggle button.active {
  background: #fff;
  color: #1e293b;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}
#tzc-app .tzc-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 14px;
}
#tzc-app .tzc-preset-btn {
  padding: 5px 12px;
  background: #e0f2fe;
  color: #0369a1;
  border: 1.5px solid #bae6fd;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#tzc-app .tzc-preset-btn:hover {
  background: #bae6fd;
}
#tzc-app .tzc-add-row {
  display: flex;
  gap: 8px;
  margin-bottom: 18px;
  flex-wrap: wrap;
}
#tzc-app .tzc-add-row select {
  flex: 1;
  min-width: 200px;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  color: #1e293b;
  background: #f8fafc;
}
#tzc-app .tzc-add-row button {
  padding: 9px 18px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#tzc-app .tzc-add-row button:hover {
  background: #4f46e5;
}
#tzc-app .tzc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
  gap: 14px;
}
#tzc-app .tzc-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 16px 16px 14px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
  position: relative;
  transition: border-color 0.2s;
}
#tzc-app .tzc-card.day-card {
  border-color: #fde68a;
  background: linear-gradient(135deg, #fffbeb 0%, #fef9c3 100%);
}
#tzc-app .tzc-card.night-card {
  border-color: #818cf8;
  background: linear-gradient(135deg, #eef2ff 0%, #e0e7ff 100%);
}
#tzc-app .tzc-card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}
#tzc-app .tzc-city-name {
  font-size: 14px;
  font-weight: 700;
  color: #0f172a;
}
#tzc-app .tzc-dn-icon {
  font-size: 18px;
  line-height: 1;
}
#tzc-app .tzc-time {
  font-size: 2rem;
  font-weight: 800;
  color: #1e293b;
  letter-spacing: -1px;
  line-height: 1.1;
  margin-bottom: 2px;
}
#tzc-app .tzc-date {
  font-size: 12px;
  color: #64748b;
  margin-bottom: 6px;
}
#tzc-app .tzc-diff {
  display: inline-block;
  font-size: 11px;
  font-weight: 600;
  padding: 2px 8px;
  border-radius: 20px;
  background: #f1f5f9;
  color: #475569;
}
#tzc-app .tzc-remove {
  position: absolute;
  top: 8px;
  right: 8px;
  width: 22px;
  height: 22px;
  background: #fee2e2;
  color: #dc2626;
  border: none;
  border-radius: 50%;
  font-size: 14px;
  line-height: 22px;
  text-align: center;
  cursor: pointer;
  display: none;
  font-weight: 700;
  padding: 0;
}
#tzc-app .tzc-card:hover .tzc-remove {
  display: block;
}
#tzc-app .tzc-local-note {
  font-size: 11px;
  color: #94a3b8;
  margin-top: 2px;
}
#tzc-app .tzc-empty {
  text-align: center;
  color: #94a3b8;
  padding: 30px 0;
  font-size: 14px;
}
@media (max-width: 480px) {
  #tzc-app .tzc-time { font-size: 1.6rem; }
  #tzc-app .tzc-grid { grid-template-columns: 1fr 1fr; }
}
</style>

<div class="tzc-topbar">
  <div class="tzc-toggle">
    <button id="tzc-btn-24" class="active" onclick="tzcSetFormat(24)">24h</button>
    <button id="tzc-btn-12" onclick="tzcSetFormat(12)">12h</button>
  </div>
  <span style="font-size:13px;color:#64748b;">Your local time is shown with a star</span>
</div>

<div style="margin-bottom:8px;font-size:13px;font-weight:600;color:#475569;">Popular cities:</div>
<div class="tzc-presets">
  <button class="tzc-preset-btn" onclick="tzcAddPreset('New York','America/New_York')">New York</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('London','Europe/London')">London</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('Tokyo','Asia/Tokyo')">Tokyo</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('Sydney','Australia/Sydney')">Sydney</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('Dubai','Asia/Dubai')">Dubai</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('Paris','Europe/Paris')">Paris</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('Singapore','Asia/Singapore')">Singapore</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('Los Angeles','America/Los_Angeles')">Los Angeles</button>
</div>

<div class="tzc-add-row">
  <select id="tzc-tz-select">
    <option value="">-- Select a timezone --</option>
  </select>
  <button onclick="tzcAddFromSelect()">+ Add Clock</button>
</div>

<div class="tzc-grid" id="tzc-grid">
  <div class="tzc-empty" id="tzc-empty">Add clocks using the presets or selector above.</div>
</div>

<script>
(function(){
  const TZC_ZONES = [
    ["Africa/Abidjan","Africa/Abidjan"],["Africa/Accra","Africa/Accra"],["Africa/Addis_Ababa","Africa/Addis Ababa"],
    ["Africa/Algiers","Africa/Algiers"],["Africa/Cairo","Africa/Cairo"],["Africa/Casablanca","Africa/Casablanca"],
    ["Africa/Johannesburg","Africa/Johannesburg"],["Africa/Lagos","Africa/Lagos"],["Africa/Nairobi","Africa/Nairobi"],
    ["America/Anchorage","America/Anchorage"],["America/Bogota","America/Bogota"],["America/Buenos_Aires","America/Buenos Aires"],
    ["America/Chicago","America/Chicago"],["America/Denver","America/Denver"],["America/Los_Angeles","America/Los Angeles"],
    ["America/Mexico_City","America/Mexico City"],["America/New_York","America/New York"],["America/Sao_Paulo","America/Sao Paulo"],
    ["America/Toronto","America/Toronto"],["America/Vancouver","America/Vancouver"],
    ["Asia/Bangkok","Asia/Bangkok"],["Asia/Colombo","Asia/Colombo"],["Asia/Dubai","Asia/Dubai"],
    ["Asia/Hong_Kong","Asia/Hong Kong"],["Asia/Jakarta","Asia/Jakarta"],["Asia/Karachi","Asia/Karachi"],
    ["Asia/Kolkata","Asia/Kolkata"],["Asia/Kuala_Lumpur","Asia/Kuala Lumpur"],["Asia/Manila","Asia/Manila"],
    ["Asia/Seoul","Asia/Seoul"],["Asia/Shanghai","Asia/Shanghai"],["Asia/Singapore","Asia/Singapore"],
    ["Asia/Taipei","Asia/Taipei"],["Asia/Tehran","Asia/Tehran"],["Asia/Tokyo","Asia/Tokyo"],
    ["Atlantic/Azores","Atlantic/Azores"],["Australia/Adelaide","Australia/Adelaide"],["Australia/Brisbane","Australia/Brisbane"],
    ["Australia/Melbourne","Australia/Melbourne"],["Australia/Perth","Australia/Perth"],["Australia/Sydney","Australia/Sydney"],
    ["Europe/Amsterdam","Europe/Amsterdam"],["Europe/Athens","Europe/Athens"],["Europe/Berlin","Europe/Berlin"],
    ["Europe/Brussels","Europe/Brussels"],["Europe/Budapest","Europe/Budapest"],["Europe/Copenhagen","Europe/Copenhagen"],
    ["Europe/Dublin","Europe/Dublin"],["Europe/Helsinki","Europe/Helsinki"],["Europe/Istanbul","Europe/Istanbul"],
    ["Europe/Lisbon","Europe/Lisbon"],["Europe/London","Europe/London"],["Europe/Madrid","Europe/Madrid"],
    ["Europe/Moscow","Europe/Moscow"],["Europe/Oslo","Europe/Oslo"],["Europe/Paris","Europe/Paris"],
    ["Europe/Prague","Europe/Prague"],["Europe/Rome","Europe/Rome"],["Europe/Stockholm","Europe/Stockholm"],
    ["Europe/Warsaw","Europe/Warsaw"],["Europe/Zurich","Europe/Zurich"],
    ["Pacific/Auckland","Pacific/Auckland"],["Pacific/Fiji","Pacific/Fiji"],["Pacific/Honolulu","Pacific/Honolulu"],
    ["Pacific/Midway","Pacific/Midway"],["UTC","UTC"]
  ];

  let tzcClocks = [];
  let tzcFormat = 24;
  let tzcTimer = null;
  const localTZ = Intl.DateTimeFormat().resolvedOptions().timeZone;

  // Populate select
  const sel = document.getElementById('tzc-tz-select');
  TZC_ZONES.forEach(([tz, label]) => {
    const opt = document.createElement('option');
    opt.value = tz;
    opt.textContent = label;
    sel.appendChild(opt);
  });

  window.tzcSetFormat = function(f) {
    tzcFormat = f;
    document.getElementById('tzc-btn-24').classList.toggle('active', f === 24);
    document.getElementById('tzc-btn-12').classList.toggle('active', f === 12);
    tzcRender();
  };

  window.tzcAddPreset = function(city, tz) {
    if (tzcClocks.find(c => c.tz === tz)) return;
    tzcClocks.push({city, tz});
    tzcRender();
  };

  window.tzcAddFromSelect = function() {
    const s = document.getElementById('tzc-tz-select');
    if (!s.value) return;
    const tz = s.value;
    const city = s.options[s.selectedIndex].text;
    if (tzcClocks.find(c => c.tz === tz)) return;
    tzcClocks.push({city, tz});
    s.value = '';
    tzcRender();
  };

  window.tzcRemove = function(tz) {
    tzcClocks = tzcClocks.filter(c => c.tz !== tz);
    tzcRender();
  };

  function tzcGetLocalOffset() {
    const now = new Date();
    return -now.getTimezoneOffset(); // minutes
  }

  function tzcGetZoneOffset(tz, now) {
    try {
      // Use Intl to get UTC offset for the zone
      const utcStr = new Intl.DateTimeFormat('en-US', {timeZone:'UTC', hour:'2-digit', minute:'2-digit', hour12:false}).format(now);
      const tzStr = new Intl.DateTimeFormat('en-US', {timeZone:tz, hour:'2-digit', minute:'2-digit', hour12:false}).format(now);
      const [uh,um] = utcStr.split(':').map(Number);
      const [th,tm] = tzStr.split(':').map(Number);
      return (th - uh) * 60 + (tm - um);
    } catch(e) { return 0; }
  }

  function tzcFormatDiff(diffMin) {
    if (diffMin === 0) return 'Same time as you';
    const sign = diffMin > 0 ? '+' : '-';
    const abs = Math.abs(diffMin);
    const h = Math.floor(abs / 60);
    const m = abs % 60;
    return sign + h + (m ? ':' + String(m).padStart(2,'0') : '') + 'h from you';
  }

  function tzcIsDay(hour) {
    return hour >= 6 && hour < 20;
  }

  function tzcRender() {
    const grid = document.getElementById('tzc-grid');
    const empty = document.getElementById('tzc-empty');
    if (tzcClocks.length === 0) {
      grid.innerHTML = '<div class="tzc-empty" id="tzc-empty">Add clocks using the presets or selector above.</div>';
      return;
    }
    const now = new Date();
    const localOffMin = tzcGetLocalOffset();

    grid.innerHTML = tzcClocks.map(({city, tz}) => {
      const isLocal = tz === localTZ;
      let timeStr, dateStr, hourNum;
      try {
        const opts12 = {timeZone:tz, hour:'numeric', minute:'2-digit', second:'2-digit', hour12:true};
        const opts24 = {timeZone:tz, hour:'2-digit', minute:'2-digit', second:'2-digit', hour12:false};
        timeStr = new Intl.DateTimeFormat('en-US', tzcFormat===12 ? opts12 : opts24).format(now);
        dateStr = new Intl.DateTimeFormat('en-US', {timeZone:tz, weekday:'short', month:'short', day:'numeric'}).format(now);
        const h = parseInt(new Intl.DateTimeFormat('en-US', {timeZone:tz, hour:'2-digit', hour12:false}).format(now));
        hourNum = h;
      } catch(e) {
        timeStr = '--:--';
        dateStr = '';
        hourNum = 12;
      }
      const day = tzcIsDay(hourNum);
      const dnIcon = day ? '☀️' : '🌙';
      const cardClass = day ? 'tzc-card day-card' : 'tzc-card night-card';
      const tzOff = tzcGetZoneOffset(tz, now);
      const diffMin = tzOff - localOffMin;
      const diffStr = isLocal ? '⭐ Your local time' : tzcFormatDiff(diffMin);

      return `<div class="${cardClass}">
        <button class="tzc-remove" onclick="tzcRemove('${tz.replace(/'/g,"\\'")}')">&#x2715;</button>
        <div class="tzc-card-header">
          <div class="tzc-city-name">${city}${isLocal ? ' ⭐' : ''}</div>
          <div class="tzc-dn-icon">${dnIcon}</div>
        </div>
        <div class="tzc-time">${timeStr}</div>
        <div class="tzc-date">${dateStr}</div>
        <div class="tzc-diff">${diffStr}</div>
      </div>`;
    }).join('');
  }

  function tzcTick() {
    tzcRender();
    tzcTimer = setTimeout(tzcTick, 1000 - (Date.now() % 1000));
  }

  // Start with local time + common presets
  tzcAddPreset('Your Local Time', localTZ);
  tzcAddPreset('New York', 'America/New_York');
  tzcAddPreset('London', 'Europe/London');
  tzcAddPreset('Tokyo', 'Asia/Tokyo');
  tzcTick();
})();
</script>
</div>

> Convert timezones → [Timezone Converter](/tools/timezone-converter/)

> World clock → [World Clock](/tools/world-clock/)
