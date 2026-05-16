---
title: "Unit Converter - Free Online Measurement Converter"
date: 2025-05-16
description: "Convert between units of length, weight, temperature, volume, area, speed, and more. Fast, free, and accurate online unit converter."
categories: ["Free Tools"]
tags: ["unit converter", "measurement", "conversion", "calculator", "metric imperial"]
slug: "unit-converter"
aliases: ["/tools/unit-converter/", "/tools/unit-converter/"]
cover:
  image: "/images/covers/unit-converter.png"
  alt: "Unit Converter"
ShowToc: false
---

<div id="converter-app">

<style>
  #converter-app {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    max-width: 820px;
    margin: 0 auto;
    color: #1e293b;
  }

  /* Category Tabs */
  .uc-tabs {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 24px;
  }

  .uc-tab {
    padding: 8px 16px;
    border: 2px solid #e2e8f0;
    border-radius: 9999px;
    background: #fff;
    color: #64748b;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .uc-tab:hover {
    border-color: #0891b2;
    color: #0891b2;
  }

  .uc-tab.active {
    background: #0891b2;
    border-color: #0891b2;
    color: #fff;
  }

  /* Main Converter Card */
  .uc-card {
    background: #fff;
    border-radius: 16px;
    padding: 32px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.08), 0 4px 16px rgba(8,145,178,0.08);
    margin-bottom: 24px;
  }

  .uc-category-label {
    font-size: 13px;
    font-weight: 600;
    color: #0891b2;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-bottom: 20px;
  }

  /* Converter Row */
  .uc-converter-row {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 16px;
    align-items: end;
    margin-bottom: 20px;
  }

  .uc-field {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .uc-field label {
    font-size: 13px;
    font-weight: 600;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .uc-field select {
    padding: 10px 12px;
    border: 2px solid #e2e8f0;
    border-radius: 10px;
    font-size: 15px;
    color: #1e293b;
    background: #f8fafc;
    appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%2364748b' stroke-width='2'%3E%3Cpolyline points='6 9 12 15 18 9'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 10px center;
    padding-right: 36px;
    cursor: pointer;
    transition: border-color 0.2s;
  }

  .uc-field select:focus {
    outline: none;
    border-color: #0891b2;
    background-color: #fff;
  }

  .uc-field input[type="number"] {
    padding: 14px 16px;
    border: 2px solid #e2e8f0;
    border-radius: 10px;
    font-size: 22px;
    font-weight: 600;
    color: #1e293b;
    background: #f8fafc;
    width: 100%;
    box-sizing: border-box;
    transition: border-color 0.2s;
    -moz-appearance: textfield;
  }

  .uc-field input[type="number"]::-webkit-outer-spin-button,
  .uc-field input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
  }

  .uc-field input[type="number"]:focus {
    outline: none;
    border-color: #0891b2;
    background-color: #fff;
    box-shadow: 0 0 0 3px rgba(8,145,178,0.12);
  }

  .uc-field input[readonly] {
    background: #f0f9ff;
    border-color: #bae6fd;
    color: #0891b2;
    cursor: default;
  }

  /* Swap Button */
  .uc-swap-col {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
    padding-bottom: 4px;
  }

  .uc-swap-btn {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    border: 2px solid #0891b2;
    background: #fff;
    color: #0891b2;
    font-size: 20px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    flex-shrink: 0;
  }

  .uc-swap-btn:hover {
    background: #0891b2;
    color: #fff;
    transform: rotate(180deg);
  }

  /* Formula display */
  .uc-formula {
    background: #f0f9ff;
    border: 1px solid #bae6fd;
    border-radius: 10px;
    padding: 12px 16px;
    font-size: 13px;
    color: #0369a1;
    font-family: 'Courier New', monospace;
    min-height: 40px;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 4px;
    word-break: break-word;
  }

  .uc-formula strong {
    color: #0891b2;
  }

  /* Quick Reference Table */
  .uc-quick-ref {
    background: #fff;
    border-radius: 16px;
    padding: 28px 32px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.08), 0 4px 16px rgba(8,145,178,0.08);
    margin-bottom: 24px;
  }

  .uc-quick-ref h3 {
    margin: 0 0 16px 0;
    font-size: 16px;
    font-weight: 700;
    color: #1e293b;
  }

  .uc-ref-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 14px;
  }

  .uc-ref-table th {
    text-align: left;
    padding: 8px 12px;
    background: #f0f9ff;
    color: #0891b2;
    font-weight: 600;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .uc-ref-table th:first-child { border-radius: 8px 0 0 8px; }
  .uc-ref-table th:last-child  { border-radius: 0 8px 8px 0; }

  .uc-ref-table td {
    padding: 9px 12px;
    border-bottom: 1px solid #f1f5f9;
    color: #334155;
  }

  .uc-ref-table tr:last-child td {
    border-bottom: none;
  }

  .uc-ref-table tr:hover td {
    background: #f8fafc;
  }

  /* Data base toggle */
  .uc-base-toggle {
    display: flex;
    gap: 8px;
    margin-bottom: 16px;
    flex-wrap: wrap;
  }

  .uc-base-btn {
    padding: 6px 14px;
    border-radius: 8px;
    border: 2px solid #e2e8f0;
    background: #fff;
    color: #64748b;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
  }

  .uc-base-btn.active {
    background: #0891b2;
    border-color: #0891b2;
    color: #fff;
  }

  /* Responsive */
  @media (max-width: 600px) {
    .uc-card, .uc-quick-ref {
      padding: 20px 16px;
    }

    .uc-converter-row {
      grid-template-columns: 1fr;
      gap: 12px;
    }

    .uc-swap-col {
      flex-direction: row;
      justify-content: center;
      padding-bottom: 0;
    }

    .uc-swap-btn {
      transform: rotate(90deg);
    }

    .uc-swap-btn:hover {
      transform: rotate(270deg);
    }

    .uc-tabs {
      gap: 4px;
    }

    .uc-tab {
      padding: 6px 12px;
      font-size: 13px;
    }

    .uc-field input[type="number"] {
      font-size: 18px;
    }
  }
</style>

<!-- Tabs -->
<div class="uc-tabs" id="uc-tabs"></div>

<!-- Main Converter Card -->
<div class="uc-card">
  <div class="uc-category-label" id="uc-category-label">Length</div>

  <!-- Data base toggle (shown only for Data category) -->
  <div class="uc-base-toggle" id="uc-base-toggle" style="display:none;">
    <button class="uc-base-btn active" data-base="1000" onclick="ucSetBase(1000,this)">SI (1 KB = 1,000 B)</button>
    <button class="uc-base-btn" data-base="1024" onclick="ucSetBase(1024,this)">Binary (1 KiB = 1,024 B)</button>
  </div>

  <div class="uc-converter-row">
    <!-- Input -->
    <div class="uc-field">
      <label>From</label>
      <select id="uc-from-unit" onchange="ucConvert()"></select>
      <input type="number" id="uc-from-val" value="1" oninput="ucConvert()" placeholder="Enter value" />
    </div>

    <!-- Swap -->
    <div class="uc-swap-col">
      <button class="uc-swap-btn" onclick="ucSwap()" title="Swap units">&#8646;</button>
    </div>

    <!-- Output -->
    <div class="uc-field">
      <label>To</label>
      <select id="uc-to-unit" onchange="ucConvert()"></select>
      <input type="number" id="uc-to-val" readonly placeholder="Result" />
    </div>
  </div>

  <!-- Formula -->
  <div class="uc-formula" id="uc-formula">Enter a value to see the conversion formula.</div>
</div>

<!-- Quick Reference -->
<div class="uc-quick-ref">
  <h3 id="uc-ref-title">Common Length Conversions</h3>
  <table class="uc-ref-table">
    <thead>
      <tr>
        <th>From</th>
        <th>To</th>
        <th>Multiply by</th>
      </tr>
    </thead>
    <tbody id="uc-ref-body"></tbody>
  </table>
</div>

<script>
(function() {
  /* ===== UNIT DEFINITIONS ===== */
  /* Each unit has a factor to convert TO the base unit of that category */
  /* For temperature: special handling via functions */

  const CATEGORIES = [
    { id: 'length',      label: 'Length',       base: 'm' },
    { id: 'weight',      label: 'Weight',       base: 'kg' },
    { id: 'temperature', label: 'Temperature',  base: 'C' },
    { id: 'volume',      label: 'Volume',       base: 'L' },
    { id: 'area',        label: 'Area',         base: 'sqm' },
    { id: 'speed',       label: 'Speed',        base: 'ms' },
    { id: 'time',        label: 'Time',         base: 'sec' },
    { id: 'data',        label: 'Data',         base: 'byte' },
  ];

  const UNITS = {
    length: [
      { id: 'mm',   label: 'Millimeter (mm)',  factor: 0.001 },
      { id: 'cm',   label: 'Centimeter (cm)',  factor: 0.01 },
      { id: 'm',    label: 'Meter (m)',         factor: 1 },
      { id: 'km',   label: 'Kilometer (km)',    factor: 1000 },
      { id: 'in',   label: 'Inch (in)',         factor: 0.0254 },
      { id: 'ft',   label: 'Foot (ft)',         factor: 0.3048 },
      { id: 'yd',   label: 'Yard (yd)',         factor: 0.9144 },
      { id: 'mi',   label: 'Mile (mi)',         factor: 1609.344 },
    ],
    weight: [
      { id: 'mg',   label: 'Milligram (mg)',    factor: 0.000001 },
      { id: 'g',    label: 'Gram (g)',           factor: 0.001 },
      { id: 'kg',   label: 'Kilogram (kg)',      factor: 1 },
      { id: 'oz',   label: 'Ounce (oz)',         factor: 0.0283495 },
      { id: 'lb',   label: 'Pound (lb)',         factor: 0.453592 },
      { id: 'ton',  label: 'Metric Ton (t)',     factor: 1000 },
    ],
    temperature: [
      { id: 'C',  label: 'Celsius (°C)' },
      { id: 'F',  label: 'Fahrenheit (°F)' },
      { id: 'K',  label: 'Kelvin (K)' },
    ],
    volume: [
      { id: 'ml',    label: 'Milliliter (ml)',   factor: 0.001 },
      { id: 'L',     label: 'Liter (L)',          factor: 1 },
      { id: 'cup',   label: 'Cup (US)',           factor: 0.2365882 },
      { id: 'pt',    label: 'Pint (US)',          factor: 0.4731765 },
      { id: 'qt',    label: 'Quart (US)',         factor: 0.9463529 },
      { id: 'gal',   label: 'Gallon (US)',        factor: 3.785412 },
      { id: 'floz',  label: 'Fl Oz (US)',         factor: 0.0295735 },
    ],
    area: [
      { id: 'sqcm',  label: 'Sq Centimeter (cm²)', factor: 0.0001 },
      { id: 'sqm',   label: 'Sq Meter (m²)',        factor: 1 },
      { id: 'sqkm',  label: 'Sq Kilometer (km²)',   factor: 1e6 },
      { id: 'sqft',  label: 'Sq Foot (ft²)',        factor: 0.092903 },
      { id: 'sqyd',  label: 'Sq Yard (yd²)',        factor: 0.836127 },
      { id: 'acre',  label: 'Acre',                 factor: 4046.856 },
      { id: 'ha',    label: 'Hectare (ha)',          factor: 10000 },
    ],
    speed: [
      { id: 'ms',   label: 'Meter/sec (m/s)',    factor: 1 },
      { id: 'kmh',  label: 'Kilometer/h (km/h)', factor: 0.277778 },
      { id: 'mph',  label: 'Miles/h (mph)',       factor: 0.44704 },
      { id: 'kn',   label: 'Knot (kn)',           factor: 0.514444 },
    ],
    time: [
      { id: 'sec',   label: 'Second (s)',   factor: 1 },
      { id: 'min',   label: 'Minute (min)', factor: 60 },
      { id: 'hr',    label: 'Hour (hr)',    factor: 3600 },
      { id: 'day',   label: 'Day',          factor: 86400 },
      { id: 'week',  label: 'Week',         factor: 604800 },
    ],
    data: [
      { id: 'byte', label: 'Byte (B)',       si: 1,          bin: 1 },
      { id: 'kb',   label: 'Kilobyte (KB)',  si: 1e3,        bin: 1024 },
      { id: 'mb',   label: 'Megabyte (MB)',  si: 1e6,        bin: 1048576 },
      { id: 'gb',   label: 'Gigabyte (GB)',  si: 1e9,        bin: 1073741824 },
      { id: 'tb',   label: 'Terabyte (TB)',  si: 1e12,       bin: 1099511627776 },
    ],
  };

  /* Quick Reference rows per category */
  const QUICK_REF = {
    length: [
      ['1 inch', '2.54 cm',       '× 2.54'],
      ['1 foot', '30.48 cm',      '× 30.48'],
      ['1 mile', '1.609 km',      '× 1.60934'],
      ['1 yard', '0.9144 m',      '× 0.9144'],
      ['1 km',   '0.621 miles',   '× 0.62137'],
      ['1 m',    '3.281 feet',    '× 3.28084'],
    ],
    weight: [
      ['1 kg',   '2.205 lb',      '× 2.20462'],
      ['1 lb',   '453.6 g',       '× 453.592'],
      ['1 oz',   '28.35 g',       '× 28.3495'],
      ['1 ton',  '1,000 kg',      '× 1000'],
      ['1 lb',   '16 oz',         '× 16'],
    ],
    temperature: [
      ['0 °C',    '32 °F',         '(°C × 9/5) + 32'],
      ['100 °C',  '212 °F',        '(°C × 9/5) + 32'],
      ['0 °C',    '273.15 K',      '°C + 273.15'],
      ['98.6 °F', '37 °C',         '(°F − 32) × 5/9'],
      ['72 °F',   '22.2 °C',       '(°F − 32) × 5/9'],
    ],
    volume: [
      ['1 L',     '4.227 cups',    '× 4.22675'],
      ['1 gal',   '3.785 L',       '× 3.78541'],
      ['1 cup',   '236.6 ml',      '× 236.588'],
      ['1 pint',  '2 cups',        '× 2'],
      ['1 quart', '2 pints',       '× 2'],
      ['1 fl oz', '29.57 ml',      '× 29.5735'],
    ],
    area: [
      ['1 acre',    '4,047 m²',     '× 4046.86'],
      ['1 hectare', '10,000 m²',    '× 10000'],
      ['1 sq mile', '640 acres',    '× 640'],
      ['1 sq ft',   '0.0929 m²',   '× 0.092903'],
      ['1 sq km',   '100 ha',       '× 100'],
    ],
    speed: [
      ['1 m/s',   '3.6 km/h',      '× 3.6'],
      ['1 mph',   '1.609 km/h',    '× 1.60934'],
      ['1 knot',  '1.852 km/h',    '× 1.852'],
      ['60 mph',  '96.56 km/h',    '× 1.60934'],
      ['1 km/h',  '0.2778 m/s',   '× 0.27778'],
    ],
    time: [
      ['1 min',   '60 sec',        '× 60'],
      ['1 hour',  '3,600 sec',     '× 3600'],
      ['1 day',   '24 hours',      '× 24'],
      ['1 week',  '7 days',        '× 7'],
      ['1 week',  '168 hours',     '× 168'],
    ],
    data: [
      ['1 KB (SI)',  '1,000 B',       '× 1,000'],
      ['1 MB (SI)',  '1,000 KB',      '× 1,000'],
      ['1 GB (SI)',  '1,000 MB',      '× 1,000'],
      ['1 KiB',      '1,024 B',       '× 1,024'],
      ['1 MiB',      '1,024 KiB',    '× 1,024'],
      ['1 GiB',      '1,024 MiB',    '× 1,024'],
    ],
  };

  /* ===== STATE ===== */
  let currentCat = 'length';
  let dataBase = 1000; // SI by default

  /* ===== INIT ===== */
  function init() {
    buildTabs();
    selectCategory('length');
  }

  function buildTabs() {
    const container = document.getElementById('uc-tabs');
    CATEGORIES.forEach(cat => {
      const btn = document.createElement('button');
      btn.className = 'uc-tab' + (cat.id === 'length' ? ' active' : '');
      btn.textContent = cat.label;
      btn.addEventListener('click', () => selectCategory(cat.id));
      btn.id = 'tab-' + cat.id;
      container.appendChild(btn);
    });
  }

  function selectCategory(catId) {
    currentCat = catId;

    /* Update tabs */
    document.querySelectorAll('.uc-tab').forEach(t => t.classList.remove('active'));
    const activeTab = document.getElementById('tab-' + catId);
    if (activeTab) activeTab.classList.add('active');

    /* Update label */
    const cat = CATEGORIES.find(c => c.id === catId);
    document.getElementById('uc-category-label').textContent = cat.label;

    /* Show/hide data base toggle */
    document.getElementById('uc-base-toggle').style.display = catId === 'data' ? 'flex' : 'none';

    /* Populate selects */
    populateSelects(catId);

    /* Update quick ref */
    updateQuickRef(catId);

    /* Run conversion */
    ucConvert();
  }

  function populateSelects(catId) {
    const units = UNITS[catId];
    const fromSel = document.getElementById('uc-from-unit');
    const toSel   = document.getElementById('uc-to-unit');

    fromSel.innerHTML = '';
    toSel.innerHTML   = '';

    units.forEach((u, i) => {
      const opt1 = new Option(u.label, u.id);
      const opt2 = new Option(u.label, u.id);
      fromSel.appendChild(opt1);
      toSel.appendChild(opt2);
    });

    /* Default: first unit from, second unit to */
    fromSel.selectedIndex = 0;
    toSel.selectedIndex   = Math.min(1, units.length - 1);
  }

  function updateQuickRef(catId) {
    const cat = CATEGORIES.find(c => c.id === catId);
    document.getElementById('uc-ref-title').textContent = 'Common ' + cat.label + ' Conversions';
    const tbody = document.getElementById('uc-ref-body');
    tbody.innerHTML = '';
    (QUICK_REF[catId] || []).forEach(row => {
      const tr = document.createElement('tr');
      tr.innerHTML = row.map(cell => `<td>${cell}</td>`).join('');
      tbody.appendChild(tr);
    });
  }

  /* ===== CONVERSION LOGIC ===== */
  function toBase(value, unitId, catId) {
    if (catId === 'temperature') {
      if (unitId === 'C') return value;
      if (unitId === 'F') return (value - 32) * 5 / 9;
      if (unitId === 'K') return value - 273.15;
    }
    if (catId === 'data') {
      const u = UNITS.data.find(x => x.id === unitId);
      return value * (dataBase === 1024 ? u.bin : u.si);
    }
    const u = UNITS[catId].find(x => x.id === unitId);
    return value * u.factor;
  }

  function fromBase(baseValue, unitId, catId) {
    if (catId === 'temperature') {
      if (unitId === 'C') return baseValue;
      if (unitId === 'F') return baseValue * 9 / 5 + 32;
      if (unitId === 'K') return baseValue + 273.15;
    }
    if (catId === 'data') {
      const u = UNITS.data.find(x => x.id === unitId);
      return baseValue / (dataBase === 1024 ? u.bin : u.si);
    }
    const u = UNITS[catId].find(x => x.id === unitId);
    return baseValue / u.factor;
  }

  function buildFormula(value, fromId, toId, result, catId) {
    const fromUnit = UNITS[catId].find(x => x.id === fromId);
    const toUnit   = UNITS[catId].find(x => x.id === toId);
    const fromName = fromUnit ? fromUnit.label : fromId;
    const toName   = toUnit   ? toUnit.label   : toId;

    if (catId === 'temperature') {
      let expr = '';
      if (fromId === 'C' && toId === 'F') expr = `(${fmtNum(value)} × 9/5) + 32 = <strong>${fmtNum(result)} °F</strong>`;
      else if (fromId === 'F' && toId === 'C') expr = `(${fmtNum(value)} − 32) × 5/9 = <strong>${fmtNum(result)} °C</strong>`;
      else if (fromId === 'C' && toId === 'K') expr = `${fmtNum(value)} + 273.15 = <strong>${fmtNum(result)} K</strong>`;
      else if (fromId === 'K' && toId === 'C') expr = `${fmtNum(value)} − 273.15 = <strong>${fmtNum(result)} °C</strong>`;
      else if (fromId === 'F' && toId === 'K') expr = `(${fmtNum(value)} − 32) × 5/9 + 273.15 = <strong>${fmtNum(result)} K</strong>`;
      else if (fromId === 'K' && toId === 'F') expr = `(${fmtNum(value)} − 273.15) × 9/5 + 32 = <strong>${fmtNum(result)} °F</strong>`;
      else expr = `<strong>${fmtNum(result)}</strong>`;
      return expr;
    }

    if (fromId === toId) {
      return `Same unit — no conversion needed: <strong>${fmtNum(result)}</strong>`;
    }

    /* Calculate the direct multiplier for display */
    let multiplier;
    if (catId === 'data') {
      const fu = UNITS.data.find(x => x.id === fromId);
      const tu = UNITS.data.find(x => x.id === toId);
      const fromFactor = dataBase === 1024 ? fu.bin : fu.si;
      const toFactor   = dataBase === 1024 ? tu.bin : tu.si;
      multiplier = fromFactor / toFactor;
    } else {
      const fu = UNITS[catId].find(x => x.id === fromId);
      const tu = UNITS[catId].find(x => x.id === toId);
      multiplier = fu.factor / tu.factor;
    }

    return `${fmtNum(value)} × ${fmtFactor(multiplier)} = <strong>${fmtNum(result)}</strong>`;
  }

  function fmtNum(n) {
    if (n === null || n === undefined || isNaN(n)) return '—';
    if (Math.abs(n) >= 1e9 || (Math.abs(n) < 1e-4 && n !== 0)) {
      return n.toExponential(6);
    }
    /* Show up to 8 significant digits */
    const s = parseFloat(n.toPrecision(8)).toString();
    return s;
  }

  function fmtFactor(f) {
    if (Math.abs(f) >= 1e6 || (Math.abs(f) < 1e-4 && f !== 0)) {
      return f.toExponential(4);
    }
    return parseFloat(f.toPrecision(7)).toString();
  }

  /* ===== PUBLIC FUNCTIONS (called from HTML) ===== */
  window.ucConvert = function() {
    const fromId  = document.getElementById('uc-from-unit').value;
    const toId    = document.getElementById('uc-to-unit').value;
    const rawVal  = document.getElementById('uc-from-val').value;
    const value   = rawVal === '' ? null : parseFloat(rawVal);

    if (value === null || isNaN(value)) {
      document.getElementById('uc-to-val').value = '';
      document.getElementById('uc-formula').innerHTML = 'Enter a value to see the conversion formula.';
      return;
    }

    const base   = toBase(value, fromId, currentCat);
    const result = fromBase(base, toId, currentCat);

    document.getElementById('uc-to-val').value = fmtNum(result);
    document.getElementById('uc-formula').innerHTML = buildFormula(value, fromId, toId, result, currentCat);
  };

  window.ucSwap = function() {
    const fromSel = document.getElementById('uc-from-unit');
    const toSel   = document.getElementById('uc-to-unit');
    const fromVal = document.getElementById('uc-from-val');
    const toVal   = document.getElementById('uc-to-val');

    const tmpUnit = fromSel.value;
    fromSel.value = toSel.value;
    toSel.value   = tmpUnit;

    /* Swap values: result becomes new input */
    const toValNum = toVal.value;
    if (toValNum !== '' && !isNaN(parseFloat(toValNum))) {
      fromVal.value = toValNum;
    }

    ucConvert();
  };

  window.ucSetBase = function(base, btn) {
    dataBase = base;
    document.querySelectorAll('.uc-base-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    ucConvert();
  };

  /* ===== BOOT ===== */
  init();
})();
</script>

</div>

---

## How to Use This Unit Converter

1. **Select a category** using the tabs at the top — Length, Weight, Temperature, Volume, Area, Speed, Time, or Data.
2. **Choose your units** from the "From" and "To" dropdown menus.
3. **Type a value** in the left input field. The result appears instantly on the right.
4. **Swap the direction** at any time using the swap button between the two fields — the result becomes the new input.
5. **Read the formula** shown below the fields to understand exactly how the conversion is calculated.

For Data conversions, you can switch between **SI (decimal, base-1000)** used by storage manufacturers and **Binary (base-1024)** used by operating systems.

---

## Common Conversion References

| From | To | Multiply By |
|------|-----|------------|
| 1 inch | 2.54 centimeters | × 2.54 |
| 1 mile | 1.60934 kilometers | × 1.60934 |
| 1 kilogram | 2.20462 pounds | × 2.20462 |
| 1 liter | 0.264172 US gallons | × 0.264172 |
| 1 acre | 0.404686 hectares | × 0.404686 |
| 0 °C | 32 °F | (°C × 9/5) + 32 |
| 1 m/s | 3.6 km/h | × 3.6 |
| 1 GB (SI) | 1,000 MB | × 1,000 |

---

## Related Tools

> Calculate percentages instantly → [Percentage Calculator](/tools/percentage-calculator/)

> Check your BMI → [BMI Calculator](/tools/bmi-calculator/)

> Convert hourly and annual salary → [Hourly to Salary Calculator](/tools/hourly-to-salary-calculator/)
