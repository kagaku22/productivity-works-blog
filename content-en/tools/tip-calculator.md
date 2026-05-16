---
title: "Tip Calculator - Free Bill & Gratuity Splitter Tool"
date: 2025-05-16
description: "Calculate tips instantly with quick percentage buttons, custom rates, and split-bill by people. Includes round up/down, currency selector, and visual bill breakdown."
categories: ["Free Tools"]
tags: ["tip calculator", "gratuity calculator", "split bill", "restaurant", "personal finance"]
slug: "tip-calculator"
aliases: ["/tools/gratuity-calculator/", "/tools/split-bill/"]
cover:
  image: "/images/covers/tip-calculator.png"
  alt: "Tip Calculator"
ShowToc: false
---

<div id="tip-app">

<style>
#tip-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1f2937;
}

#tip-app * {
  box-sizing: border-box;
}

.tip-card {
  background: #fff;
  border: 1.5px solid #fde68a;
  border-radius: 16px;
  padding: 28px 28px 24px;
  margin-bottom: 20px;
  box-shadow: 0 2px 12px rgba(217,119,6,0.08);
}

.tip-section-title {
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: .06em;
  color: #92400e;
  margin: 0 0 12px;
}

/* Input row */
.tip-input-row {
  display: flex;
  gap: 12px;
  align-items: center;
  flex-wrap: wrap;
}

.tip-currency-select {
  flex: 0 0 72px;
  padding: 10px 8px;
  border: 1.5px solid #fcd34d;
  border-radius: 10px;
  font-size: 18px;
  font-weight: 700;
  color: #92400e;
  background: #fffbeb;
  text-align: center;
  cursor: pointer;
  appearance: none;
}

.tip-amount-input {
  flex: 1 1 160px;
  padding: 10px 14px;
  border: 1.5px solid #fcd34d;
  border-radius: 10px;
  font-size: 24px;
  font-weight: 700;
  color: #1f2937;
  background: #fffbeb;
  width: 100%;
}

.tip-amount-input:focus,
.tip-currency-select:focus {
  outline: none;
  border-color: #d97706;
  box-shadow: 0 0 0 3px rgba(217,119,6,0.15);
}

/* Tip quick buttons */
.tip-quick-btns {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 12px;
}

.tip-pct-btn {
  flex: 1 1 60px;
  padding: 10px 4px;
  border: 1.5px solid #fcd34d;
  border-radius: 10px;
  background: #fffbeb;
  color: #92400e;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background .15s, border-color .15s, color .15s;
  text-align: center;
}

.tip-pct-btn:hover {
  background: #fef3c7;
  border-color: #d97706;
}

.tip-pct-btn.active {
  background: #d97706;
  border-color: #b45309;
  color: #fff;
}

/* Custom tip */
.tip-custom-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 4px;
}

.tip-custom-label {
  font-size: 14px;
  color: #6b7280;
  white-space: nowrap;
}

.tip-custom-input {
  width: 90px;
  padding: 8px 12px;
  border: 1.5px solid #fcd34d;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  color: #1f2937;
  background: #fffbeb;
}

.tip-custom-input:focus {
  outline: none;
  border-color: #d97706;
  box-shadow: 0 0 0 3px rgba(217,119,6,0.15);
}

/* Quality label */
.tip-quality-badge {
  display: inline-block;
  padding: 3px 12px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: .04em;
  margin-left: 8px;
  vertical-align: middle;
  transition: background .2s, color .2s;
}

/* People selector */
.tip-people-row {
  display: flex;
  align-items: center;
  gap: 14px;
}

.tip-people-btn {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  border: 1.5px solid #fcd34d;
  background: #fffbeb;
  color: #92400e;
  font-size: 22px;
  font-weight: 700;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  line-height: 1;
  transition: background .15s;
}

.tip-people-btn:hover {
  background: #fef3c7;
  border-color: #d97706;
}

.tip-people-num {
  font-size: 26px;
  font-weight: 800;
  color: #d97706;
  min-width: 32px;
  text-align: center;
}

.tip-people-label {
  font-size: 14px;
  color: #6b7280;
}

/* Results */
.tip-results-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 18px;
}

@media (max-width: 480px) {
  .tip-results-grid {
    grid-template-columns: 1fr;
  }
  .tip-amount-input {
    font-size: 20px;
  }
}

.tip-result-cell {
  background: #fffbeb;
  border: 1.5px solid #fde68a;
  border-radius: 12px;
  padding: 16px 18px;
  text-align: center;
}

.tip-result-cell.highlight {
  background: #d97706;
  border-color: #b45309;
}

.tip-result-cell .label {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: .05em;
  color: #92400e;
  margin-bottom: 6px;
}

.tip-result-cell.highlight .label {
  color: #fef3c7;
}

.tip-result-cell .amount {
  font-size: 26px;
  font-weight: 800;
  color: #1f2937;
  line-height: 1.1;
}

.tip-result-cell.highlight .amount {
  color: #fff;
}

.tip-result-cell .sub {
  font-size: 12px;
  color: #9ca3af;
  margin-top: 4px;
}

.tip-result-cell.highlight .sub {
  color: #fde68a;
}

/* Visual bar */
.tip-bar-wrap {
  margin: 4px 0 16px;
}

.tip-bar-labels {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  color: #6b7280;
  margin-bottom: 5px;
}

.tip-bar-track {
  width: 100%;
  height: 18px;
  background: #e5e7eb;
  border-radius: 9px;
  overflow: hidden;
  display: flex;
}

.tip-bar-bill {
  background: #6b7280;
  height: 100%;
  border-radius: 9px 0 0 9px;
  transition: width .3s;
}

.tip-bar-tip {
  background: #d97706;
  height: 100%;
  border-radius: 0 9px 9px 0;
  transition: width .3s;
}

/* Round buttons */
.tip-round-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.tip-round-btn {
  flex: 1 1 auto;
  padding: 9px 14px;
  border: 1.5px solid #fcd34d;
  border-radius: 9px;
  background: #fffbeb;
  color: #92400e;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background .15s, border-color .15s;
  text-align: center;
}

.tip-round-btn:hover {
  background: #fef3c7;
  border-color: #d97706;
}

.tip-reset-btn {
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 10px;
  background: #f3f4f6;
  color: #6b7280;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  margin-top: 4px;
  transition: background .15s;
}

.tip-reset-btn:hover {
  background: #e5e7eb;
}
</style>

<!-- Bill Amount -->
<div class="tip-card">
  <div class="tip-section-title">Bill Amount</div>
  <div class="tip-input-row">
    <select class="tip-currency-select" id="tip-currency">
      <option value="$">$</option>
      <option value="€">€</option>
      <option value="£">£</option>
      <option value="¥">¥</option>
    </select>
    <input class="tip-amount-input" type="number" id="tip-bill" placeholder="0.00" min="0" step="0.01" inputmode="decimal" />
  </div>
</div>

<!-- Tip Percentage -->
<div class="tip-card">
  <div class="tip-section-title">
    Tip Percentage
    <span class="tip-quality-badge" id="tip-quality-badge"></span>
  </div>
  <div class="tip-quick-btns">
    <button class="tip-pct-btn" data-pct="10">10%</button>
    <button class="tip-pct-btn" data-pct="15">15%</button>
    <button class="tip-pct-btn active" data-pct="18">18%</button>
    <button class="tip-pct-btn" data-pct="20">20%</button>
    <button class="tip-pct-btn" data-pct="25">25%</button>
  </div>
  <div class="tip-custom-row">
    <span class="tip-custom-label">Custom:</span>
    <input class="tip-custom-input" type="number" id="tip-custom-pct" placeholder="%" min="0" max="100" step="1" inputmode="numeric" />
    <span style="font-size:14px;color:#6b7280;">%</span>
  </div>
</div>

<!-- Split Bill -->
<div class="tip-card">
  <div class="tip-section-title">Split Between</div>
  <div class="tip-people-row">
    <button class="tip-people-btn" id="tip-minus">−</button>
    <div class="tip-people-num" id="tip-people-num">1</div>
    <button class="tip-people-btn" id="tip-plus">+</button>
    <span class="tip-people-label" id="tip-people-label">person</span>
  </div>
</div>

<!-- Results -->
<div class="tip-card">
  <div class="tip-section-title">Results</div>
  <div class="tip-results-grid">
    <div class="tip-result-cell">
      <div class="label">Tip Amount</div>
      <div class="amount" id="res-tip">—</div>
      <div class="sub" id="res-tip-pct">at 18%</div>
    </div>
    <div class="tip-result-cell">
      <div class="label">Total Bill</div>
      <div class="amount" id="res-total">—</div>
      <div class="sub">bill + tip</div>
    </div>
    <div class="tip-result-cell highlight" id="res-person-cell">
      <div class="label">Per Person</div>
      <div class="amount" id="res-person">—</div>
      <div class="sub" id="res-person-sub">1 person</div>
    </div>
    <div class="tip-result-cell">
      <div class="label">Tip Per Person</div>
      <div class="amount" id="res-tip-person">—</div>
      <div class="sub" id="res-tip-person-sub">1 person</div>
    </div>
  </div>

  <!-- Visual bar -->
  <div class="tip-bar-wrap">
    <div class="tip-bar-labels">
      <span id="bar-label-bill">Bill: —</span>
      <span id="bar-label-tip">Tip: —</span>
    </div>
    <div class="tip-bar-track">
      <div class="tip-bar-bill" id="bar-bill" style="width:100%"></div>
      <div class="tip-bar-tip" id="bar-tip" style="width:0%"></div>
    </div>
  </div>

  <!-- Round buttons -->
  <div class="tip-round-row">
    <button class="tip-round-btn" id="btn-round-up">Round Up Total ↑</button>
    <button class="tip-round-btn" id="btn-round-down">Round Down Total ↓</button>
  </div>
  <button class="tip-reset-btn" id="btn-reset">Reset</button>
</div>

<script>
(function() {
  'use strict';

  // State
  let bill = 0;
  let tipPct = 18;
  let people = 1;
  let currency = '$';

  // Elements
  const elBill    = document.getElementById('tip-bill');
  const elCur     = document.getElementById('tip-currency');
  const elCustom  = document.getElementById('tip-custom-pct');
  const elPeople  = document.getElementById('tip-people-num');
  const elPLabel  = document.getElementById('tip-people-label');
  const elQuality = document.getElementById('tip-quality-badge');

  const elResTip       = document.getElementById('res-tip');
  const elResTotal     = document.getElementById('res-total');
  const elResPerson    = document.getElementById('res-person');
  const elResTipPct    = document.getElementById('res-tip-pct');
  const elResPersonSub = document.getElementById('res-person-sub');
  const elResTipPerson = document.getElementById('res-tip-person');
  const elResTipPersonSub = document.getElementById('res-tip-person-sub');

  const barBill  = document.getElementById('bar-bill');
  const barTip   = document.getElementById('bar-tip');
  const lblBill  = document.getElementById('bar-label-bill');
  const lblTip   = document.getElementById('bar-label-tip');

  const pctBtns  = document.querySelectorAll('#tip-app .tip-pct-btn');

  function fmt(n) {
    if (currency === '¥') return currency + Math.round(n).toLocaleString();
    return currency + n.toFixed(2);
  }

  function qualityLabel(pct) {
    if (pct < 10)  return { text: '',          bg: 'transparent', color: 'transparent' };
    if (pct < 15)  return { text: 'Fair',      bg: '#fef9c3', color: '#854d0e' };
    if (pct < 20)  return { text: 'Good',      bg: '#d1fae5', color: '#065f46' };
    if (pct < 25)  return { text: 'Great',     bg: '#bfdbfe', color: '#1e3a8a' };
    return           { text: 'Excellent!',    bg: '#ede9fe', color: '#4c1d95' };
  }

  function calc(overrideBill) {
    const b = (overrideBill !== undefined) ? overrideBill : bill;
    const tipAmt   = b * tipPct / 100;
    const total    = b + tipAmt;
    const perPerson    = total / people;
    const tipPerPerson = tipAmt / people;

    elResTip.textContent       = fmt(tipAmt);
    elResTotal.textContent     = fmt(total);
    elResPerson.textContent    = fmt(perPerson);
    elResTipPerson.textContent = fmt(tipPerPerson);
    elResTipPct.textContent    = 'at ' + tipPct + '%';
    elResPersonSub.textContent = people === 1 ? '1 person' : people + ' people';
    elResTipPersonSub.textContent = people === 1 ? '1 person' : people + ' people';

    // Bar
    const billPct = total > 0 ? (b / total * 100) : 100;
    const tipBarPct = total > 0 ? (tipAmt / total * 100) : 0;
    barBill.style.width = billPct + '%';
    barTip.style.width  = tipBarPct + '%';
    lblBill.textContent = 'Bill: ' + fmt(b);
    lblTip.textContent  = 'Tip: ' + fmt(tipAmt);

    // Quality
    const q = qualityLabel(tipPct);
    elQuality.textContent   = q.text;
    elQuality.style.background = q.bg;
    elQuality.style.color      = q.color;
  }

  function setActivePct(pct) {
    tipPct = pct;
    pctBtns.forEach(b => {
      b.classList.toggle('active', parseInt(b.dataset.pct, 10) === pct);
    });
    elCustom.value = '';
    calc();
  }

  // Events — bill
  elBill.addEventListener('input', function() {
    bill = parseFloat(this.value) || 0;
    calc();
  });

  // Events — currency
  elCur.addEventListener('change', function() {
    currency = this.value;
    calc();
  });

  // Events — quick pct buttons
  pctBtns.forEach(btn => {
    btn.addEventListener('click', function() {
      setActivePct(parseInt(this.dataset.pct, 10));
    });
  });

  // Events — custom pct
  elCustom.addEventListener('input', function() {
    const v = parseFloat(this.value);
    if (!isNaN(v) && v >= 0) {
      tipPct = v;
      pctBtns.forEach(b => b.classList.remove('active'));
      calc();
    }
  });

  // Events — people
  document.getElementById('tip-minus').addEventListener('click', function() {
    if (people > 1) { people--; update(); }
  });
  document.getElementById('tip-plus').addEventListener('click', function() {
    if (people < 20) { people++; update(); }
  });

  function update() {
    elPeople.textContent = people;
    elPLabel.textContent = people === 1 ? 'person' : 'people';
    calc();
  }

  // Round up / down
  document.getElementById('btn-round-up').addEventListener('click', function() {
    if (bill <= 0) return;
    const tipAmt = bill * tipPct / 100;
    const total  = bill + tipAmt;
    const rounded = Math.ceil(total);
    const newTip  = rounded - bill;
    const newPct  = bill > 0 ? (newTip / bill * 100) : tipPct;
    tipPct = Math.round(newPct * 10) / 10;
    elCustom.value = tipPct;
    pctBtns.forEach(b => b.classList.remove('active'));
    calc(bill);
    // recalc with rounded total override approach
    elResTotal.textContent = fmt(rounded);
    elResTip.textContent   = fmt(newTip);
    elResPerson.textContent    = fmt(rounded / people);
    elResTipPerson.textContent = fmt(newTip / people);
    barBill.style.width = (bill / rounded * 100) + '%';
    barTip.style.width  = (newTip / rounded * 100) + '%';
    lblTip.textContent  = 'Tip: ' + fmt(newTip);
  });

  document.getElementById('btn-round-down').addEventListener('click', function() {
    if (bill <= 0) return;
    const tipAmt = bill * tipPct / 100;
    const total  = bill + tipAmt;
    const rounded = Math.floor(total);
    if (rounded <= bill) return;
    const newTip  = rounded - bill;
    const newPct  = bill > 0 ? (newTip / bill * 100) : tipPct;
    tipPct = Math.round(newPct * 10) / 10;
    elCustom.value = tipPct;
    pctBtns.forEach(b => b.classList.remove('active'));
    calc(bill);
    elResTotal.textContent = fmt(rounded);
    elResTip.textContent   = fmt(newTip);
    elResPerson.textContent    = fmt(rounded / people);
    elResTipPerson.textContent = fmt(newTip / people);
    barBill.style.width = (bill / rounded * 100) + '%';
    barTip.style.width  = (newTip / rounded * 100) + '%';
    lblTip.textContent  = 'Tip: ' + fmt(newTip);
  });

  // Reset
  document.getElementById('btn-reset').addEventListener('click', function() {
    bill = 0;
    tipPct = 18;
    people = 1;
    currency = '$';
    elBill.value = '';
    elCur.value = '$';
    elCustom.value = '';
    elPeople.textContent = '1';
    elPLabel.textContent = 'person';
    pctBtns.forEach(b => b.classList.toggle('active', b.dataset.pct === '18'));
    elResTip.textContent = '—';
    elResTotal.textContent = '—';
    elResPerson.textContent = '—';
    elResTipPerson.textContent = '—';
    elResTipPct.textContent = 'at 18%';
    elResPersonSub.textContent = '1 person';
    elResTipPersonSub.textContent = '1 person';
    barBill.style.width = '100%';
    barTip.style.width  = '0%';
    lblBill.textContent = 'Bill: —';
    lblTip.textContent  = 'Tip: —';
    elQuality.textContent = '';
    elQuality.style.background = 'transparent';
  });

  // Init
  calc();
})();
</script>

</div>

---

**How to use this tip calculator:** Enter your bill amount, choose a tip percentage (or type a custom one), then set how many people are splitting the bill. Use the round up/down buttons to land on a clean total, and switch currencies with the dropdown if you're traveling abroad.

**Tip guide:**
- **10%** — Minimal service or takeout
- **15%** — Standard / Fair
- **18%** — Good service (US restaurant default)
- **20%** — Great service
- **25%+** — Excellent / exceptional experience

Related: Calculate your budget with our [Loan Calculator](/tools/loan-calculator/)
