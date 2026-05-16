---
title: "Fake Data Generator - Mock API Data"
date: 2025-05-16
description: "Free fake data generator. Generate realistic mock data for testing: names, emails, addresses, phone numbers, dates, UUIDs. Export as JSON, CSV, or SQL INSERT statements."
categories: ["Free Tools"]
slug: "fake-data-generator"
ShowToc: false
cover:
  image: "/images/covers/fake-data-generator.png"
  alt: "Fake Data Generator - Mock API Data"
---

<div id="fd-app">

<style>
#fd-app *,
#fd-app *::before,
#fd-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

#fd-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 14px;
  color: #1e293b;
  line-height: 1.5;
}

#fd-app h2 {
  font-size: 16px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 10px;
}

#fd-app .fd-row {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  margin-bottom: 14px;
}

#fd-app .fd-col {
  flex: 1 1 240px;
  min-width: 0;
}

#fd-app .fd-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 16px;
}

#fd-app .fd-label {
  display: block;
  font-size: 12px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 6px;
}

#fd-app .fd-input {
  width: 100%;
  padding: 7px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  color: #1e293b;
  background: #fff;
  outline: none;
  transition: border-color 0.15s;
}
#fd-app .fd-input:focus { border-color: #2563eb; }

#fd-app .fd-select {
  width: 100%;
  padding: 7px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  color: #1e293b;
  background: #fff;
  cursor: pointer;
  outline: none;
}
#fd-app .fd-select:focus { border-color: #2563eb; }

#fd-app .fd-fields-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
  gap: 8px;
}

#fd-app .fd-field-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 10px;
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  cursor: pointer;
  user-select: none;
  transition: border-color 0.15s, background 0.15s;
}
#fd-app .fd-field-item:hover { border-color: #93c5fd; background: #eff6ff; }
#fd-app .fd-field-item.active { border-color: #2563eb; background: #dbeafe; }

#fd-app .fd-field-item input[type="checkbox"] {
  width: 15px;
  height: 15px;
  accent-color: #2563eb;
  cursor: pointer;
  flex-shrink: 0;
}

#fd-app .fd-field-label {
  font-size: 13px;
  font-weight: 500;
  color: #334155;
  flex: 1;
}

#fd-app .fd-field-item.active .fd-field-label { color: #1d4ed8; font-weight: 600; }

#fd-app .fd-field-icon {
  font-size: 16px;
  flex-shrink: 0;
}

#fd-app .fd-custom-names {
  margin-top: 10px;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
}

#fd-app .fd-custom-name-input {
  padding: 5px 9px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 12px;
  width: 120px;
  color: #1e293b;
  background: #fff;
  outline: none;
}
#fd-app .fd-custom-name-input:focus { border-color: #2563eb; }

#fd-app .fd-toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 14px;
}

#fd-app .fd-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 8px 16px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  white-space: nowrap;
  line-height: 1;
}
#fd-app .fd-btn:active { transform: scale(0.97); }
#fd-app .fd-btn-primary  { background: #2563eb; color: #fff; }
#fd-app .fd-btn-primary:hover  { background: #1d4ed8; }
#fd-app .fd-btn-success  { background: #16a34a; color: #fff; }
#fd-app .fd-btn-success:hover  { background: #15803d; }
#fd-app .fd-btn-orange   { background: #d97706; color: #fff; }
#fd-app .fd-btn-orange:hover   { background: #b45309; }
#fd-app .fd-btn-purple   { background: #7c3aed; color: #fff; }
#fd-app .fd-btn-purple:hover   { background: #6d28d9; }
#fd-app .fd-btn-secondary { background: #e2e8f0; color: #334155; }
#fd-app .fd-btn-secondary:hover { background: #cbd5e1; }
#fd-app .fd-btn-sm {
  padding: 5px 10px;
  font-size: 12px;
}

#fd-app .fd-count-row {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

#fd-app .fd-count-input {
  width: 90px;
  padding: 7px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 700;
  color: #1e293b;
  background: #fff;
  outline: none;
  text-align: center;
}
#fd-app .fd-count-input:focus { border-color: #2563eb; }

#fd-app .fd-seed-row {
  display: flex;
  align-items: center;
  gap: 8px;
  flex-wrap: wrap;
}

#fd-app .fd-seed-toggle {
  display: flex;
  align-items: center;
  gap: 6px;
  cursor: pointer;
  font-size: 13px;
  color: #475569;
}

#fd-app .fd-seed-input {
  width: 110px;
  padding: 5px 9px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  color: #1e293b;
  background: #fff;
  outline: none;
}
#fd-app .fd-seed-input:focus { border-color: #2563eb; }
#fd-app .fd-seed-input:disabled { background: #f1f5f9; color: #94a3b8; }

#fd-app .fd-status {
  font-size: 13px;
  color: #475569;
  padding: 6px 12px;
  background: #f1f5f9;
  border-radius: 6px;
}

#fd-app .fd-status.ok   { background: #dcfce7; color: #15803d; }
#fd-app .fd-status.err  { background: #fee2e2; color: #dc2626; }
#fd-app .fd-status.info { background: #dbeafe; color: #1d4ed8; }

#fd-app .fd-preview-wrap {
  overflow-x: auto;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  background: #fff;
  margin-bottom: 14px;
}

#fd-app .fd-preview-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 12px;
  white-space: nowrap;
}

#fd-app .fd-preview-table th {
  background: #f1f5f9;
  padding: 8px 12px;
  text-align: left;
  font-weight: 700;
  color: #475569;
  border-bottom: 2px solid #e2e8f0;
  position: sticky;
  top: 0;
}

#fd-app .fd-preview-table td {
  padding: 7px 12px;
  color: #1e293b;
  border-bottom: 1px solid #f1f5f9;
  max-width: 180px;
  overflow: hidden;
  text-overflow: ellipsis;
}

#fd-app .fd-preview-table tr:last-child td { border-bottom: none; }
#fd-app .fd-preview-table tr:hover td { background: #f8fafc; }

#fd-app .fd-output-wrap {
  background: #0f172a;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 14px;
  position: relative;
  max-height: 360px;
  overflow-y: auto;
}

#fd-app .fd-output {
  font-family: "Fira Code", "Cascadia Code", "SF Mono", Consolas, monospace;
  font-size: 12px;
  color: #e2e8f0;
  white-space: pre;
  line-height: 1.6;
}

#fd-app .fd-copy-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 5px 12px;
  background: #334155;
  color: #cbd5e1;
  border: none;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#fd-app .fd-copy-btn:hover { background: #475569; }
#fd-app .fd-copy-btn.copied { background: #16a34a; color: #fff; }

#fd-app .fd-empty {
  text-align: center;
  padding: 40px 20px;
  color: #94a3b8;
  font-size: 13px;
}

#fd-app .fd-divider {
  border: none;
  border-top: 1.5px solid #e2e8f0;
  margin: 16px 0;
}

#fd-app .fd-format-tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 10px;
}

#fd-app .fd-tab {
  padding: 6px 14px;
  border: 1.5px solid #e2e8f0;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  background: #fff;
  color: #475569;
  transition: all 0.15s;
}
#fd-app .fd-tab.active { background: #2563eb; color: #fff; border-color: #2563eb; }
#fd-app .fd-tab:hover:not(.active) { border-color: #93c5fd; color: #1d4ed8; }

#fd-app .fd-sql-table-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
}

#fd-app .fd-sql-table-input {
  padding: 5px 9px;
  border: 1.5px solid #cbd5e1;
  border-radius: 6px;
  font-size: 13px;
  color: #1e293b;
  background: #fff;
  outline: none;
  width: 160px;
}
#fd-app .fd-sql-table-input:focus { border-color: #2563eb; }

#fd-app .fd-badge {
  display: inline-block;
  padding: 2px 8px;
  background: #dbeafe;
  color: #1d4ed8;
  border-radius: 99px;
  font-size: 11px;
  font-weight: 700;
}

@media (max-width: 600px) {
  #fd-app .fd-fields-grid {
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
  }
  #fd-app .fd-output-wrap { max-height: 240px; }
}
</style>

<!-- FIELD SELECTION -->
<div class="fd-card" style="margin-bottom:14px;">
  <h2>1. Select Fields</h2>
  <div class="fd-fields-grid" id="fdFieldsGrid"></div>
  <hr class="fd-divider">
  <div style="font-size:12px;color:#475569;margin-bottom:6px;font-weight:600;">Custom column names (optional — overrides defaults)</div>
  <div class="fd-custom-names" id="fdCustomNames">
    <span style="font-size:12px;color:#94a3b8;">Select fields above to set custom names.</span>
  </div>
</div>

<!-- CONFIG ROW -->
<div class="fd-row">
  <div class="fd-col fd-card">
    <h2>2. Record Count</h2>
    <div class="fd-count-row">
      <input type="number" id="fdCount" class="fd-count-input" value="10" min="1" max="1000">
      <span style="font-size:13px;color:#475569;">rows (max 1000)</span>
    </div>
    <input type="range" id="fdCountSlider" min="1" max="1000" value="10"
      style="width:100%;margin-top:10px;accent-color:#2563eb;">
  </div>
  <div class="fd-col fd-card">
    <h2>3. Reproducible Seed</h2>
    <div class="fd-seed-row">
      <label class="fd-seed-toggle">
        <input type="checkbox" id="fdSeedEnabled" style="accent-color:#2563eb;"> Use seed
      </label>
      <input type="number" id="fdSeedVal" class="fd-seed-input" value="42" disabled placeholder="e.g. 42">
    </div>
    <div style="font-size:12px;color:#64748b;margin-top:8px;">Same seed = same data every time.</div>
  </div>
  <div class="fd-col fd-card">
    <h2>4. Export Format</h2>
    <div class="fd-format-tabs" id="fdFormatTabs">
      <button class="fd-tab active" data-fmt="json">JSON</button>
      <button class="fd-tab" data-fmt="csv">CSV</button>
      <button class="fd-tab" data-fmt="sql">SQL</button>
    </div>
    <div id="fdSqlTableRow" class="fd-sql-table-row" style="display:none;">
      <span style="font-size:12px;color:#475569;">Table:</span>
      <input type="text" id="fdSqlTable" class="fd-sql-table-input" value="mock_data" placeholder="table name">
    </div>
  </div>
</div>

<!-- GENERATE TOOLBAR -->
<div class="fd-toolbar">
  <button class="fd-btn fd-btn-primary" id="fdBtnGenerate">&#9654; Generate</button>
  <button class="fd-btn fd-btn-secondary" id="fdBtnSelectAll">Check All</button>
  <button class="fd-btn fd-btn-secondary" id="fdBtnClearAll">Uncheck All</button>
  <div id="fdStatus" class="fd-status">Select fields and click Generate.</div>
</div>

<!-- PREVIEW TABLE -->
<div id="fdPreviewSection" style="display:none;">
  <h2 style="margin-bottom:8px;">Preview <span id="fdPreviewBadge" class="fd-badge"></span></h2>
  <div class="fd-preview-wrap" style="max-height:280px;overflow-y:auto;">
    <table class="fd-preview-table" id="fdPreviewTable">
      <thead id="fdPreviewHead"></thead>
      <tbody id="fdPreviewBody"></tbody>
    </table>
  </div>
</div>

<!-- OUTPUT -->
<div id="fdOutputSection" style="display:none;margin-top:14px;">
  <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;flex-wrap:wrap;gap:8px;">
    <h2>Output</h2>
    <div style="display:flex;gap:8px;">
      <button class="fd-btn fd-btn-success fd-btn-sm" id="fdBtnDownload">&#8659; Download</button>
    </div>
  </div>
  <div class="fd-output-wrap">
    <button class="fd-copy-btn" id="fdBtnCopy">Copy</button>
    <pre class="fd-output" id="fdOutput"></pre>
  </div>
</div>

<script>
(function() {
  // ── FIELD DEFINITIONS ──────────────────────────────────────────────────────
  var FIELDS = [
    { id: "name",     label: "Full Name",    icon: "&#128100;" },
    { id: "email",    label: "Email",         icon: "&#9993;" },
    { id: "phone",    label: "Phone",         icon: "&#128222;" },
    { id: "address",  label: "Address",       icon: "&#127968;" },
    { id: "company",  label: "Company",       icon: "&#127970;" },
    { id: "date",     label: "Date",          icon: "&#128197;" },
    { id: "uuid",     label: "UUID",          icon: "&#128273;" },
    { id: "number",   label: "Number",        icon: "&#128290;" },
    { id: "boolean",  label: "Boolean",       icon: "&#9989;" },
    { id: "lorem",    label: "Lorem Text",    icon: "&#128218;" },
  ];

  var selectedFields = ["name", "email", "phone", "uuid"];
  var customNames = {};
  var currentFmt = "json";
  var generatedData = [];

  // ── SEEDED RNG ─────────────────────────────────────────────────────────────
  function mulberry32(seed) {
    return function() {
      seed |= 0; seed = seed + 0x6D2B79F5 | 0;
      var t = Math.imul(seed ^ seed >>> 15, 1 | seed);
      t = t + Math.imul(t ^ t >>> 7, 61 | t) ^ t;
      return ((t ^ t >>> 14) >>> 0) / 4294967296;
    };
  }

  var rnd = Math.random;

  function rand() { return rnd(); }
  function randInt(min, max) { return Math.floor(rand() * (max - min + 1)) + min; }
  function pick(arr) { return arr[Math.floor(rand() * arr.length)]; }

  // ── DATA POOLS ─────────────────────────────────────────────────────────────
  var FIRST = ["James","Mary","John","Patricia","Robert","Jennifer","Michael","Linda",
    "William","Barbara","David","Susan","Richard","Jessica","Joseph","Sarah",
    "Thomas","Karen","Charles","Lisa","Christopher","Nancy","Daniel","Betty",
    "Matthew","Margaret","Anthony","Sandra","Mark","Ashley","Donald","Dorothy",
    "Steven","Kimberly","Paul","Emily","Andrew","Donna","Joshua","Michelle"];
  var LAST = ["Smith","Johnson","Williams","Brown","Jones","Garcia","Miller","Davis",
    "Wilson","Taylor","Anderson","Thomas","Jackson","White","Harris","Martin",
    "Thompson","Young","Lee","Perez","Clark","Lewis","Robinson","Walker",
    "Hall","Allen","King","Wright","Scott","Green","Baker","Adams","Nelson",
    "Carter","Mitchell","Roberts","Turner","Campbell","Parker","Evans"];
  var DOMAINS = ["gmail.com","yahoo.com","outlook.com","example.com","icloud.com",
    "proton.me","hotmail.com","company.io","work.org","mail.net"];
  var STREETS = ["Oak St","Maple Ave","Cedar Rd","Pine Blvd","Elm Dr","Washington St",
    "Lincoln Ave","Park Rd","Lake Dr","Hill Blvd","River Rd","Valley Ave",
    "Forest Ln","Sunset Blvd","Sunrise Dr","Main St","Broadway","First Ave"];
  var CITIES = ["New York","Los Angeles","Chicago","Houston","Phoenix","Philadelphia",
    "San Antonio","San Diego","Dallas","San Jose","Austin","Jacksonville",
    "Seattle","Denver","Nashville","Boston","Portland","Las Vegas","Memphis"];
  var STATES = ["NY","CA","IL","TX","AZ","PA","FL","OH","MI","WA","CO","TN","MA","OR","NV"];
  var COMPANIES = ["Acme Corp","Globex","Initech","Umbrella Ltd","Stark Industries",
    "Wayne Enterprises","Oscorp","Vandelay Industries","Dunder Mifflin",
    "Bluth Company","Sterling Cooper","Pied Piper","Hooli","Aviato",
    "Weyland Corp","Blue Sun Corp","Rekall Inc","OmniCorp","Massive Dynamic"];
  var LOREM_WORDS = ["lorem","ipsum","dolor","sit","amet","consectetur","adipiscing",
    "elit","sed","do","eiusmod","tempor","incididunt","ut","labore","et","dolore",
    "magna","aliqua","enim","ad","minim","veniam","quis","nostrud","exercitation",
    "ullamco","laboris","nisi","aliquip","ex","ea","commodo","consequat","duis",
    "aute","irure","in","reprehenderit","voluptate","velit","esse","cillum","fugiat",
    "nulla","pariatur","excepteur","sint","occaecat","cupidatat","non","proident",
    "sunt","culpa","qui","officia","deserunt","mollit","anim","id","est","laborum"];

  function genFirst() { return pick(FIRST); }
  function genLast()  { return pick(LAST); }
  function genName()  { return genFirst() + " " + genLast(); }
  function genEmail() {
    var f = genFirst().toLowerCase();
    var l = genLast().toLowerCase();
    var sep = pick([".", "_", ""]);
    return f + sep + l + randInt(1, 99) + "@" + pick(DOMAINS);
  }
  function genPhone() {
    return "(" + randInt(200,999) + ") " + randInt(200,999) + "-" + randInt(1000,9999);
  }
  function genAddress() {
    return randInt(1, 9999) + " " + pick(STREETS) + ", " + pick(CITIES) + ", " + pick(STATES) + " " + String(randInt(10000,99999));
  }
  function genCompany() { return pick(COMPANIES); }
  function genDate() {
    var y = randInt(1970, 2025);
    var m = String(randInt(1,12)).padStart(2,"0");
    var d = String(randInt(1,28)).padStart(2,"0");
    return y + "-" + m + "-" + d;
  }
  function genUUID() {
    function s4() {
      return Math.floor((1 + rand()) * 0x10000).toString(16).substring(1);
    }
    return s4()+s4()+"-"+s4()+"-4"+s4().substring(1)+"-"+
      (["8","9","a","b"][Math.floor(rand()*4)])+s4().substring(1)+"-"+s4()+s4()+s4();
  }
  function genNumber() { return randInt(1, 100000); }
  function genBoolean() { return rand() < 0.5; }
  function genLorem() {
    var words = [];
    var len = randInt(8, 20);
    for (var i = 0; i < len; i++) words.push(pick(LOREM_WORDS));
    words[0] = words[0].charAt(0).toUpperCase() + words[0].slice(1);
    return words.join(" ") + ".";
  }

  function genField(id) {
    switch(id) {
      case "name":    return genName();
      case "email":   return genEmail();
      case "phone":   return genPhone();
      case "address": return genAddress();
      case "company": return genCompany();
      case "date":    return genDate();
      case "uuid":    return genUUID();
      case "number":  return genNumber();
      case "boolean": return genBoolean();
      case "lorem":   return genLorem();
      default:        return "";
    }
  }

  function colName(fid) {
    return (customNames[fid] && customNames[fid].trim()) ? customNames[fid].trim() : fid;
  }

  // ── BUILD FIELD GRID ───────────────────────────────────────────────────────
  var grid = document.getElementById("fdFieldsGrid");
  FIELDS.forEach(function(f) {
    var item = document.createElement("div");
    item.className = "fd-field-item" + (selectedFields.indexOf(f.id) >= 0 ? " active" : "");
    item.dataset.fid = f.id;
    item.innerHTML =
      '<input type="checkbox" id="fdCb_'+f.id+'"' + (selectedFields.indexOf(f.id)>=0?' checked':'')+'>'+
      '<span class="fd-field-icon">'+f.icon+'</span>'+
      '<span class="fd-field-label">'+f.label+'</span>';
    item.addEventListener("click", function(e) {
      if (e.target.tagName === "INPUT") return;
      var cb = item.querySelector("input");
      cb.checked = !cb.checked;
      toggleField(f.id, cb.checked);
    });
    item.querySelector("input").addEventListener("change", function(e) {
      toggleField(f.id, e.target.checked);
    });
    grid.appendChild(item);
  });

  function toggleField(fid, on) {
    var item = grid.querySelector('[data-fid="'+fid+'"]');
    if (on) {
      if (selectedFields.indexOf(fid) < 0) selectedFields.push(fid);
      item.classList.add("active");
    } else {
      selectedFields = selectedFields.filter(function(x){return x!==fid;});
      item.classList.remove("active");
      delete customNames[fid];
    }
    renderCustomNames();
  }

  // ── CUSTOM NAMES ───────────────────────────────────────────────────────────
  function renderCustomNames() {
    var wrap = document.getElementById("fdCustomNames");
    wrap.innerHTML = "";
    if (selectedFields.length === 0) {
      wrap.innerHTML = '<span style="font-size:12px;color:#94a3b8;">Select fields above to set custom names.</span>';
      return;
    }
    selectedFields.forEach(function(fid) {
      var f = FIELDS.find(function(x){return x.id===fid;});
      var row = document.createElement("div");
      row.style.cssText = "display:flex;align-items:center;gap:4px;";
      row.innerHTML =
        '<span style="font-size:11px;color:#64748b;font-weight:600;">'+f.label+':</span>'+
        '<input type="text" class="fd-custom-name-input" placeholder="'+fid+'" data-fid="'+fid+'" value="'+(customNames[fid]||'')+'">';
      row.querySelector("input").addEventListener("input", function(e) {
        customNames[fid] = e.target.value;
      });
      wrap.appendChild(row);
    });
  }
  renderCustomNames();

  // ── COUNT & SLIDER ─────────────────────────────────────────────────────────
  var countInput  = document.getElementById("fdCount");
  var countSlider = document.getElementById("fdCountSlider");
  countInput.addEventListener("input", function() {
    var v = Math.max(1, Math.min(1000, parseInt(countInput.value)||1));
    countSlider.value = v;
  });
  countSlider.addEventListener("input", function() {
    countInput.value = countSlider.value;
  });

  // ── SEED ───────────────────────────────────────────────────────────────────
  var seedEnabled = document.getElementById("fdSeedEnabled");
  var seedVal     = document.getElementById("fdSeedVal");
  seedEnabled.addEventListener("change", function() {
    seedVal.disabled = !seedEnabled.checked;
  });

  // ── FORMAT TABS ────────────────────────────────────────────────────────────
  document.getElementById("fdFormatTabs").addEventListener("click", function(e) {
    var tab = e.target.closest(".fd-tab");
    if (!tab) return;
    currentFmt = tab.dataset.fmt;
    document.querySelectorAll("#fd-app .fd-tab").forEach(function(t){t.classList.remove("active");});
    tab.classList.add("active");
    document.getElementById("fdSqlTableRow").style.display = currentFmt === "sql" ? "flex" : "none";
    if (generatedData.length > 0) renderOutput();
  });

  // ── SELECT/CLEAR ALL ───────────────────────────────────────────────────────
  document.getElementById("fdBtnSelectAll").addEventListener("click", function() {
    FIELDS.forEach(function(f) { toggleField(f.id, true); });
    grid.querySelectorAll("input[type=checkbox]").forEach(function(cb){cb.checked=true;});
    renderCustomNames();
  });
  document.getElementById("fdBtnClearAll").addEventListener("click", function() {
    FIELDS.forEach(function(f) { toggleField(f.id, false); });
    grid.querySelectorAll("input[type=checkbox]").forEach(function(cb){cb.checked=false;});
    selectedFields = [];
    customNames = {};
    renderCustomNames();
  });

  // ── GENERATE ───────────────────────────────────────────────────────────────
  document.getElementById("fdBtnGenerate").addEventListener("click", function() {
    var status = document.getElementById("fdStatus");

    if (selectedFields.length === 0) {
      status.className = "fd-status err";
      status.textContent = "Please select at least one field.";
      return;
    }

    var count = Math.max(1, Math.min(1000, parseInt(countInput.value)||10));
    countInput.value = count;
    countSlider.value = count;

    // set RNG
    if (seedEnabled.checked) {
      var s = parseInt(seedVal.value) || 42;
      rnd = mulberry32(s);
    } else {
      rnd = Math.random;
    }

    generatedData = [];
    for (var i = 0; i < count; i++) {
      var row = {};
      selectedFields.forEach(function(fid) {
        row[colName(fid)] = genField(fid);
      });
      generatedData.push(row);
    }

    status.className = "fd-status ok";
    status.textContent = "Generated " + count + " records with " + selectedFields.length + " field(s).";

    renderPreview();
    renderOutput();

    document.getElementById("fdPreviewSection").style.display = "block";
    document.getElementById("fdOutputSection").style.display = "block";
  });

  // ── PREVIEW TABLE ──────────────────────────────────────────────────────────
  function renderPreview() {
    var head = document.getElementById("fdPreviewHead");
    var body = document.getElementById("fdPreviewBody");
    document.getElementById("fdPreviewBadge").textContent = generatedData.length + " rows";
    var cols = selectedFields.map(colName);

    head.innerHTML = "<tr>" + cols.map(function(c){return "<th>"+escHtml(c)+"</th>";}).join("") + "</tr>";
    var preview = generatedData.slice(0, 20);
    body.innerHTML = preview.map(function(row) {
      return "<tr>" + cols.map(function(c){
        return "<td>" + escHtml(String(row[c])) + "</td>";
      }).join("") + "</tr>";
    }).join("");
  }

  // ── OUTPUT ─────────────────────────────────────────────────────────────────
  function renderOutput() {
    var out = document.getElementById("fdOutput");
    out.textContent = buildOutput();
  }

  function buildOutput() {
    if (currentFmt === "json") return buildJSON();
    if (currentFmt === "csv")  return buildCSV();
    if (currentFmt === "sql")  return buildSQL();
    return "";
  }

  function buildJSON() {
    return JSON.stringify(generatedData, null, 2);
  }

  function buildCSV() {
    var cols = selectedFields.map(colName);
    var lines = [cols.map(csvEsc).join(",")];
    generatedData.forEach(function(row) {
      lines.push(cols.map(function(c){ return csvEsc(row[c]); }).join(","));
    });
    return lines.join("\n");
  }

  function buildSQL() {
    var table = (document.getElementById("fdSqlTable").value.trim() || "mock_data");
    var cols = selectedFields.map(colName);
    var header = "INSERT INTO `" + table + "` (`" + cols.join("`, `") + "`) VALUES";
    var rows = generatedData.map(function(row) {
      var vals = cols.map(function(c) {
        var v = row[c];
        if (typeof v === "boolean") return v ? "TRUE" : "FALSE";
        if (typeof v === "number") return v;
        return "'" + String(v).replace(/'/g, "''") + "'";
      });
      return "  (" + vals.join(", ") + ")";
    });
    return header + "\n" + rows.join(",\n") + ";";
  }

  function csvEsc(v) {
    var s = String(v);
    if (s.includes(",") || s.includes('"') || s.includes("\n")) {
      return '"' + s.replace(/"/g,'""') + '"';
    }
    return s;
  }

  function escHtml(s) {
    return s.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;");
  }

  // ── COPY ───────────────────────────────────────────────────────────────────
  document.getElementById("fdBtnCopy").addEventListener("click", function() {
    var btn = document.getElementById("fdBtnCopy");
    var text = document.getElementById("fdOutput").textContent;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text).then(function() {
        btn.textContent = "Copied!";
        btn.classList.add("copied");
        setTimeout(function(){ btn.textContent="Copy"; btn.classList.remove("copied"); }, 1800);
      });
    } else {
      var ta = document.createElement("textarea");
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand("copy");
      document.body.removeChild(ta);
      btn.textContent = "Copied!";
      btn.classList.add("copied");
      setTimeout(function(){ btn.textContent="Copy"; btn.classList.remove("copied"); }, 1800);
    }
  });

  // ── DOWNLOAD ───────────────────────────────────────────────────────────────
  document.getElementById("fdBtnDownload").addEventListener("click", function() {
    var text = buildOutput();
    var ext  = currentFmt === "json" ? "json" : currentFmt === "csv" ? "csv" : "sql";
    var mime = currentFmt === "json" ? "application/json"
             : currentFmt === "csv"  ? "text/csv"
             : "text/plain";
    var blob = new Blob([text], {type: mime});
    var url  = URL.createObjectURL(blob);
    var a    = document.createElement("a");
    a.href     = url;
    a.download = "mock-data." + ext;
    a.click();
    URL.revokeObjectURL(url);
  });

})();
</script>

</div>

---

> Format generated JSON output: [JSON Formatter](/tools/json-formatter/)

> Generate placeholder text: [Lorem Ipsum Generator](/tools/lorem-ipsum-generator/)

> Convert your CSV data: [CSV to JSON](/tools/csv-to-json/)
