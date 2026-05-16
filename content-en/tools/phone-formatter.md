---
title: "Phone Number Formatter - Format & Validate Phone Numbers"
date: 2025-05-16
description: "Format phone numbers for any country. Convert between international, national, and E.164 formats. Validate phone number structure."
categories: ["Free Tools"]
slug: "phone-formatter"
ShowToc: false
cover:
  image: "/images/covers/phone-formatter.png"
  alt: "Phone Number Formatter"
---

<div id="pf-app">

<style>
#pf-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}
#pf-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 2rem 0 1rem;
  color: #0f3460;
  border-left: 4px solid #e94560;
  padding-left: 0.75rem;
}
#pf-app .pf-card {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 10px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
#pf-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #444;
  margin-bottom: 0.4rem;
}
#pf-app input[type="text"],
#pf-app select,
#pf-app textarea {
  width: 100%;
  padding: 0.65rem 0.9rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
  box-sizing: border-box;
  transition: border-color 0.2s;
}
#pf-app input[type="text"]:focus,
#pf-app select:focus,
#pf-app textarea:focus {
  outline: none;
  border-color: #0f3460;
}
#pf-app textarea {
  min-height: 120px;
  resize: vertical;
  font-family: monospace;
  font-size: 0.9rem;
}
#pf-app .pf-row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
#pf-app .pf-row > * {
  flex: 1;
  min-width: 220px;
}
#pf-app .pf-btn {
  display: inline-block;
  background: #0f3460;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 0.65rem 1.4rem;
  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  margin-top: 0.5rem;
}
#pf-app .pf-btn:hover {
  background: #e94560;
}
#pf-app .pf-btn-secondary {
  background: #6c757d;
}
#pf-app .pf-btn-secondary:hover {
  background: #495057;
}
#pf-app .pf-result-grid {
  display: grid;
  grid-template-columns: 160px 1fr;
  gap: 0.5rem 1rem;
  align-items: center;
  margin-top: 1rem;
}
#pf-app .pf-result-label {
  font-size: 0.8rem;
  font-weight: 700;
  color: #666;
  text-transform: uppercase;
  letter-spacing: 0.03em;
}
#pf-app .pf-result-value {
  background: #f4f6fb;
  border: 1px solid #dde3f0;
  border-radius: 5px;
  padding: 0.45rem 0.75rem;
  font-family: monospace;
  font-size: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  min-height: 2.2rem;
  word-break: break-all;
}
#pf-app .pf-copy-btn {
  background: none;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 2px 8px;
  font-size: 0.75rem;
  cursor: pointer;
  color: #555;
  white-space: nowrap;
  margin-left: auto;
  transition: background 0.15s;
}
#pf-app .pf-copy-btn:hover {
  background: #e0e7ff;
}
#pf-app .pf-badge {
  display: inline-block;
  padding: 3px 10px;
  border-radius: 12px;
  font-size: 0.78rem;
  font-weight: 700;
}
#pf-app .pf-badge-valid {
  background: #d4edda;
  color: #155724;
}
#pf-app .pf-badge-invalid {
  background: #f8d7da;
  color: #721c24;
}
#pf-app .pf-badge-warn {
  background: #fff3cd;
  color: #856404;
}
#pf-app .pf-validation-box {
  margin-top: 1rem;
  padding: 0.75rem 1rem;
  border-radius: 6px;
  font-size: 0.9rem;
}
#pf-app .pf-validation-box.valid {
  background: #d4edda;
  border: 1px solid #c3e6cb;
  color: #155724;
}
#pf-app .pf-validation-box.invalid {
  background: #f8d7da;
  border: 1px solid #f5c6cb;
  color: #721c24;
}
#pf-app .pf-validation-box.warn {
  background: #fff3cd;
  border: 1px solid #ffeeba;
  color: #856404;
}
#pf-app .bulk-output {
  margin-top: 1rem;
}
#pf-app .bulk-output-line {
  font-family: monospace;
  font-size: 0.88rem;
  padding: 0.3rem 0.5rem;
  border-bottom: 1px solid #f0f0f0;
  display: flex;
  gap: 0.75rem;
  align-items: center;
  flex-wrap: wrap;
}
#pf-app .bulk-output-line:nth-child(even) {
  background: #f9f9f9;
}
#pf-app .pf-ref-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#pf-app .pf-ref-table th {
  background: #0f3460;
  color: #fff;
  padding: 0.5rem 0.75rem;
  text-align: left;
}
#pf-app .pf-ref-table td {
  padding: 0.45rem 0.75rem;
  border-bottom: 1px solid #eee;
}
#pf-app .pf-ref-table tr:nth-child(even) td {
  background: #f7f9fc;
}
#pf-app .pf-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e0e0e0;
  margin-bottom: 1.5rem;
}
#pf-app .pf-tab {
  padding: 0.55rem 1.2rem;
  cursor: pointer;
  font-weight: 600;
  font-size: 0.9rem;
  color: #666;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
  background: none;
  border-top: none;
  border-left: none;
  border-right: none;
}
#pf-app .pf-tab.active {
  color: #0f3460;
  border-bottom-color: #e94560;
}
#pf-app .pf-tab-panel {
  display: none;
}
#pf-app .pf-tab-panel.active {
  display: block;
}
#pf-app .pf-related {
  background: #f7f9fc;
  border: 1px solid #dde3f0;
  border-radius: 8px;
  padding: 1rem 1.25rem;
  margin-top: 2rem;
  font-size: 0.9rem;
}
#pf-app .pf-related a {
  color: #0f3460;
  text-decoration: none;
  font-weight: 600;
}
#pf-app .pf-related a:hover {
  color: #e94560;
  text-decoration: underline;
}
#pf-app .pf-related ul {
  margin: 0.5rem 0 0;
  padding-left: 1.25rem;
}
#pf-app .pf-related li {
  margin-bottom: 0.35rem;
}
@media (max-width: 600px) {
  #pf-app .pf-result-grid {
    grid-template-columns: 1fr;
  }
  #pf-app .pf-result-label {
    margin-top: 0.5rem;
  }
}
</style>

<h2>Phone Number Formatter & Validator</h2>

<div class="pf-tabs">
  <button class="pf-tab active" onclick="pfSwitchTab('single')">Single Number</button>
  <button class="pf-tab" onclick="pfSwitchTab('bulk')">Bulk Formatter</button>
  <button class="pf-tab" onclick="pfSwitchTab('ref')">Country Code Reference</button>
</div>

<!-- SINGLE FORMATTER TAB -->
<div id="pf-tab-single" class="pf-tab-panel active">
  <div class="pf-card">
    <div class="pf-row">
      <div>
        <label for="pf-input">Phone Number</label>
        <input type="text" id="pf-input" placeholder="e.g. 03-1234-5678 or +1 555 123 4567" oninput="pfFormat()" />
      </div>
      <div>
        <label for="pf-country">Country</label>
        <select id="pf-country" onchange="pfFormat()">
          <option value="US">United States (+1)</option>
          <option value="CA">Canada (+1)</option>
          <option value="GB">United Kingdom (+44)</option>
          <option value="JP" selected>Japan (+81)</option>
          <option value="DE">Germany (+49)</option>
          <option value="FR">France (+33)</option>
          <option value="AU">Australia (+61)</option>
          <option value="KR">South Korea (+82)</option>
          <option value="CN">China (+86)</option>
          <option value="IN">India (+91)</option>
          <option value="BR">Brazil (+55)</option>
          <option value="MX">Mexico (+52)</option>
          <option value="IT">Italy (+39)</option>
          <option value="ES">Spain (+34)</option>
          <option value="NL">Netherlands (+31)</option>
          <option value="SG">Singapore (+65)</option>
          <option value="HK">Hong Kong (+852)</option>
          <option value="TW">Taiwan (+886)</option>
          <option value="NZ">New Zealand (+64)</option>
          <option value="ZA">South Africa (+27)</option>
        </select>
      </div>
    </div>
    <div id="pf-validation-box" class="pf-validation-box warn" style="display:none;"></div>
    <div id="pf-result-grid" class="pf-result-grid" style="display:none;">
      <span class="pf-result-label">International</span>
      <span class="pf-result-value" id="res-intl"><span id="val-intl"></span><button class="pf-copy-btn" onclick="pfCopy('val-intl')">Copy</button></span>
      <span class="pf-result-label">National</span>
      <span class="pf-result-value" id="res-natl"><span id="val-natl"></span><button class="pf-copy-btn" onclick="pfCopy('val-natl')">Copy</button></span>
      <span class="pf-result-label">E.164</span>
      <span class="pf-result-value" id="res-e164"><span id="val-e164"></span><button class="pf-copy-btn" onclick="pfCopy('val-e164')">Copy</button></span>
      <span class="pf-result-label">RFC 3966</span>
      <span class="pf-result-value" id="res-rfc"><span id="val-rfc"></span><button class="pf-copy-btn" onclick="pfCopy('val-rfc')">Copy</button></span>
      <span class="pf-result-label">Digits Only</span>
      <span class="pf-result-value" id="res-raw"><span id="val-raw"></span><button class="pf-copy-btn" onclick="pfCopy('val-raw')">Copy</button></span>
    </div>
  </div>
</div>

<!-- BULK FORMATTER TAB -->
<div id="pf-tab-bulk" class="pf-tab-panel">
  <div class="pf-card">
    <label for="pf-bulk-country">Country for all numbers</label>
    <select id="pf-bulk-country" style="margin-bottom:1rem;">
      <option value="US">United States (+1)</option>
      <option value="CA">Canada (+1)</option>
      <option value="GB">United Kingdom (+44)</option>
      <option value="JP" selected>Japan (+81)</option>
      <option value="DE">Germany (+49)</option>
      <option value="FR">France (+33)</option>
      <option value="AU">Australia (+61)</option>
      <option value="KR">South Korea (+82)</option>
      <option value="CN">China (+86)</option>
      <option value="IN">India (+91)</option>
      <option value="BR">Brazil (+55)</option>
      <option value="MX">Mexico (+52)</option>
      <option value="IT">Italy (+39)</option>
      <option value="ES">Spain (+34)</option>
      <option value="NL">Netherlands (+31)</option>
      <option value="SG">Singapore (+65)</option>
      <option value="HK">Hong Kong (+852)</option>
      <option value="TW">Taiwan (+886)</option>
      <option value="NZ">New Zealand (+64)</option>
      <option value="ZA">South Africa (+27)</option>
    </select>
    <label for="pf-bulk-input">Paste phone numbers (one per line)</label>
    <textarea id="pf-bulk-input" placeholder="03-1234-5678&#10;090-9876-5432&#10;0120-123-456&#10;+81 3 1234 5678"></textarea>
    <div style="display:flex;gap:0.75rem;flex-wrap:wrap;">
      <button class="pf-btn" onclick="pfBulkFormat()">Format All</button>
      <button class="pf-btn pf-btn-secondary" onclick="pfBulkClear()">Clear</button>
      <button class="pf-btn pf-btn-secondary" onclick="pfBulkCopyAll()">Copy Results</button>
    </div>
    <div id="pf-bulk-output" class="bulk-output"></div>
  </div>
</div>

<!-- COUNTRY CODE REFERENCE TAB -->
<div id="pf-tab-ref" class="pf-tab-panel">
  <div class="pf-card">
    <p style="margin-top:0;color:#555;font-size:0.9rem;">Country dial codes, trunk prefixes, and typical number lengths for reference.</p>
    <table class="pf-ref-table">
      <thead>
        <tr>
          <th>Country</th>
          <th>Dial Code</th>
          <th>Trunk Prefix</th>
          <th>Subscriber Digits</th>
          <th>Example</th>
        </tr>
      </thead>
      <tbody id="pf-ref-body"></tbody>
    </table>
  </div>
</div>

<script>
(function() {

  // Country metadata
  const COUNTRIES = {
    US: { name: "United States",    code: "1",   trunk: "1",  digits: [10],         fmt: (n) => pfFmtUS(n),   example: "+1 212-555-0100" },
    CA: { name: "Canada",           code: "1",   trunk: "1",  digits: [10],         fmt: (n) => pfFmtUS(n),   example: "+1 416-555-0100" },
    GB: { name: "United Kingdom",   code: "44",  trunk: "0",  digits: [9,10],       fmt: (n) => pfFmtGB(n),   example: "+44 20 7946 0958" },
    JP: { name: "Japan",            code: "81",  trunk: "0",  digits: [9,10,11],    fmt: (n) => pfFmtJP(n),   example: "+81 3-1234-5678" },
    DE: { name: "Germany",          code: "49",  trunk: "0",  digits: [3,4,5,6,7,8,9,10,11], fmt: (n) => pfFmtDE(n), example: "+49 30 12345678" },
    FR: { name: "France",           code: "33",  trunk: "0",  digits: [9],          fmt: (n) => pfFmtFR(n),   example: "+33 1 23 45 67 89" },
    AU: { name: "Australia",        code: "61",  trunk: "0",  digits: [9],          fmt: (n) => pfFmtAU(n),   example: "+61 2 1234 5678" },
    KR: { name: "South Korea",      code: "82",  trunk: "0",  digits: [9,10],       fmt: (n) => pfFmtKR(n),   example: "+82 2-1234-5678" },
    CN: { name: "China",            code: "86",  trunk: "0",  digits: [11],         fmt: (n) => pfFmtCN(n),   example: "+86 138 0013 8000" },
    IN: { name: "India",            code: "91",  trunk: "0",  digits: [10],         fmt: (n) => pfFmtIN(n),   example: "+91 98765 43210" },
    BR: { name: "Brazil",           code: "55",  trunk: "0",  digits: [10,11],      fmt: (n) => pfFmtBR(n),   example: "+55 11 91234-5678" },
    MX: { name: "Mexico",           code: "52",  trunk: "0",  digits: [10],         fmt: (n) => pfFmtMX(n),   example: "+52 55 1234 5678" },
    IT: { name: "Italy",            code: "39",  trunk: "0",  digits: [6,7,8,9,10], fmt: (n) => pfFmtIT(n),  example: "+39 06 1234 5678" },
    ES: { name: "Spain",            code: "34",  trunk: "",   digits: [9],          fmt: (n) => pfFmtES(n),   example: "+34 91 123 45 67" },
    NL: { name: "Netherlands",      code: "31",  trunk: "0",  digits: [9],          fmt: (n) => pfFmtNL(n),   example: "+31 20 123 4567" },
    SG: { name: "Singapore",        code: "65",  trunk: "",   digits: [8],          fmt: (n) => pfFmtSG(n),   example: "+65 6123 4567" },
    HK: { name: "Hong Kong",        code: "852", trunk: "",   digits: [8],          fmt: (n) => pfFmtHK(n),   example: "+852 2123 4567" },
    TW: { name: "Taiwan",           code: "886", trunk: "0",  digits: [8,9],        fmt: (n) => pfFmtTW(n),   example: "+886 2 1234 5678" },
    NZ: { name: "New Zealand",      code: "64",  trunk: "0",  digits: [8,9],        fmt: (n) => pfFmtNZ(n),   example: "+64 9-123 4567" },
    ZA: { name: "South Africa",     code: "27",  trunk: "0",  digits: [9],          fmt: (n) => pfFmtZA(n),   example: "+27 11 123 4567" },
  };

  // Strip everything except digits
  function digits(s) {
    return s.replace(/\D/g, '');
  }

  // Normalize input: remove country code if present, strip leading trunk
  function normalize(raw, countryKey) {
    const c = COUNTRIES[countryKey];
    let d = digits(raw);
    // Remove leading country code
    if (d.startsWith(c.code)) {
      d = d.slice(c.code.length);
    }
    // Remove leading trunk prefix
    if (c.trunk && d.startsWith(c.trunk)) {
      d = d.slice(c.trunk.length);
    }
    return d;
  }

  // --- Country-specific formatters ---
  // Return { intl, natl } where intl includes +code and natl uses local trunk

  function pfFmtUS(sub) {
    // 10 digits: (NXX) NXX-XXXX
    if (sub.length !== 10) return null;
    return {
      intl: `+1 ${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`,
      natl: `(${sub.slice(0,3)}) ${sub.slice(3,6)}-${sub.slice(6)}`
    };
  }

  function pfFmtGB(sub) {
    // 10 digits common
    if (sub.length === 10) {
      return {
        intl: `+44 ${sub.slice(0,2)} ${sub.slice(2,6)} ${sub.slice(6)}`,
        natl: `0${sub.slice(0,2)} ${sub.slice(2,6)} ${sub.slice(6)}`
      };
    }
    if (sub.length === 9) {
      return {
        intl: `+44 ${sub.slice(0,1)} ${sub.slice(1,5)} ${sub.slice(5)}`,
        natl: `0${sub.slice(0,1)} ${sub.slice(1,5)} ${sub.slice(5)}`
      };
    }
    return null;
  }

  function pfFmtJP(sub) {
    // Mobile: 090/080/070 + 8 digits = 11 digits sub (after removing leading 0, 10 digits)
    // Fixed Tokyo: 3 + 8 = 9 digits sub (03 -> 3)
    // Freephone: 120/0120 -> sub starts with 120, 9 digits
    if (sub.length === 10) {
      // Mobile: 90/80/70 + XXXX + XXXX
      if (/^[789]0/.test(sub)) {
        return {
          intl: `+81 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`,
          natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`
        };
      }
      // IP phone 50: 50-XXXX-XXXX
      if (sub.startsWith('50')) {
        return {
          intl: `+81 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`,
          natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`
        };
      }
      // Freephone 120/800: 120-XXX-XXX
      if (sub.startsWith('120') || sub.startsWith('800')) {
        return {
          intl: `+81 ${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`,
          natl: `0${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`
        };
      }
      // Generic 10-digit
      return {
        intl: `+81 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`,
        natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`
      };
    }
    if (sub.length === 9) {
      // Tokyo/Osaka area 2-digit area code: 3/6 + 4+4
      if (sub.startsWith('3') || sub.startsWith('6')) {
        return {
          intl: `+81 ${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}`,
          natl: `0${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}`
        };
      }
      // 3-digit area code + 6 digits
      return {
        intl: `+81 ${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`,
        natl: `0${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`
      };
    }
    if (sub.length === 8) {
      // 4-digit area code small cities
      return {
        intl: `+81 ${sub.slice(0,4)}-${sub.slice(4)}`,
        natl: `0${sub.slice(0,4)}-${sub.slice(4)}`
      };
    }
    return null;
  }

  function pfFmtDE(sub) {
    if (sub.length < 3) return null;
    // Generic grouping: area + subscriber
    return {
      intl: `+49 ${sub.slice(0,3)} ${sub.slice(3)}`,
      natl: `0${sub.slice(0,3)} ${sub.slice(3)}`
    };
  }

  function pfFmtFR(sub) {
    if (sub.length !== 9) return null;
    const groups = sub.match(/.{1,2}/g).join(' ');
    return {
      intl: `+33 ${sub[0]} ${sub.slice(1).match(/.{1,2}/g).join(' ')}`,
      natl: `0${sub[0]} ${sub.slice(1).match(/.{1,2}/g).join(' ')}`
    };
  }

  function pfFmtAU(sub) {
    if (sub.length === 9) {
      return {
        intl: `+61 ${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}`,
        natl: `0${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}`
      };
    }
    return null;
  }

  function pfFmtKR(sub) {
    if (sub.length === 9) {
      return {
        intl: `+82 ${sub.slice(0,1)}-${sub.slice(1,5)}-${sub.slice(5)}`,
        natl: `0${sub.slice(0,1)}-${sub.slice(1,5)}-${sub.slice(5)}`
      };
    }
    if (sub.length === 10) {
      return {
        intl: `+82 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`,
        natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`
      };
    }
    return null;
  }

  function pfFmtCN(sub) {
    if (sub.length === 11) {
      return {
        intl: `+86 ${sub.slice(0,3)} ${sub.slice(3,7)} ${sub.slice(7)}`,
        natl: `0${sub.slice(0,3)} ${sub.slice(3,7)} ${sub.slice(7)}`
      };
    }
    return null;
  }

  function pfFmtIN(sub) {
    if (sub.length === 10) {
      return {
        intl: `+91 ${sub.slice(0,5)} ${sub.slice(5)}`,
        natl: `0${sub.slice(0,5)} ${sub.slice(5)}`
      };
    }
    return null;
  }

  function pfFmtBR(sub) {
    if (sub.length === 11) {
      return {
        intl: `+55 ${sub.slice(0,2)} ${sub.slice(2,7)}-${sub.slice(7)}`,
        natl: `(0${sub.slice(0,2)}) ${sub.slice(2,7)}-${sub.slice(7)}`
      };
    }
    if (sub.length === 10) {
      return {
        intl: `+55 ${sub.slice(0,2)} ${sub.slice(2,6)}-${sub.slice(6)}`,
        natl: `(0${sub.slice(0,2)}) ${sub.slice(2,6)}-${sub.slice(6)}`
      };
    }
    return null;
  }

  function pfFmtMX(sub) {
    if (sub.length === 10) {
      return {
        intl: `+52 ${sub.slice(0,2)} ${sub.slice(2,6)} ${sub.slice(6)}`,
        natl: `(${sub.slice(0,2)}) ${sub.slice(2,6)} ${sub.slice(6)}`
      };
    }
    return null;
  }

  function pfFmtIT(sub) {
    return {
      intl: `+39 0${sub.slice(0,2)} ${sub.slice(2)}`,
      natl: `0${sub.slice(0,2)} ${sub.slice(2)}`
    };
  }

  function pfFmtES(sub) {
    if (sub.length === 9) {
      return {
        intl: `+34 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5,7)} ${sub.slice(7)}`,
        natl: `${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5,7)} ${sub.slice(7)}`
      };
    }
    return null;
  }

  function pfFmtNL(sub) {
    if (sub.length === 9) {
      return {
        intl: `+31 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`,
        natl: `0${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`
      };
    }
    return null;
  }

  function pfFmtSG(sub) {
    if (sub.length === 8) {
      return {
        intl: `+65 ${sub.slice(0,4)} ${sub.slice(4)}`,
        natl: `${sub.slice(0,4)} ${sub.slice(4)}`
      };
    }
    return null;
  }

  function pfFmtHK(sub) {
    if (sub.length === 8) {
      return {
        intl: `+852 ${sub.slice(0,4)} ${sub.slice(4)}`,
        natl: `${sub.slice(0,4)} ${sub.slice(4)}`
      };
    }
    return null;
  }

  function pfFmtTW(sub) {
    if (sub.length === 9) {
      return {
        intl: `+886 ${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}`,
        natl: `0${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}`
      };
    }
    if (sub.length === 8) {
      return {
        intl: `+886 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`,
        natl: `0${sub.slice(0,2)}-${sub.slice(2,5)}-${sub.slice(5)}`
      };
    }
    return null;
  }

  function pfFmtNZ(sub) {
    if (sub.length === 9) {
      return {
        intl: `+64 ${sub[0]}-${sub.slice(1,4)} ${sub.slice(4)}`,
        natl: `0${sub[0]}-${sub.slice(1,4)} ${sub.slice(4)}`
      };
    }
    if (sub.length === 8) {
      return {
        intl: `+64 ${sub.slice(0,2)}-${sub.slice(2,5)} ${sub.slice(5)}`,
        natl: `0${sub.slice(0,2)}-${sub.slice(2,5)} ${sub.slice(5)}`
      };
    }
    return null;
  }

  function pfFmtZA(sub) {
    if (sub.length === 9) {
      return {
        intl: `+27 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`,
        natl: `0${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`
      };
    }
    return null;
  }

  // Build E.164: +{code}{subscriber_digits}
  function toE164(code, sub) {
    return `+${code}${sub}`;
  }

  // Build RFC 3966 tel URI with hyphens
  function toRFC3966(code, sub) {
    return `tel:+${code}-${sub.match(/.{1,4}/g).join('-')}`;
  }

  // Validate
  function validate(sub, countryKey) {
    const c = COUNTRIES[countryKey];
    if (!sub || sub.length === 0) return { ok: false, msg: "Enter a phone number." };
    if (!/^\d+$/.test(sub)) return { ok: false, msg: "Subscriber part contains non-digit characters." };
    if (c.digits.includes(sub.length)) {
      return { ok: true, msg: `Valid length (${sub.length} subscriber digits) for ${c.name}.` };
    }
    const expected = c.digits.join(' or ');
    return { ok: 'warn', msg: `Length ${sub.length} is unexpected for ${c.name} (expected ${expected} subscriber digits). May still be valid for special numbers.` };
  }

  window.pfFormat = function() {
    const raw = document.getElementById('pf-input').value.trim();
    const countryKey = document.getElementById('pf-country').value;
    const c = COUNTRIES[countryKey];

    const validBox = document.getElementById('pf-validation-box');
    const grid = document.getElementById('pf-result-grid');

    if (!raw) {
      validBox.style.display = 'none';
      grid.style.display = 'none';
      return;
    }

    const sub = normalize(raw, countryKey);
    const v = validate(sub, countryKey);

    validBox.style.display = 'block';
    validBox.className = 'pf-validation-box ' + (v.ok === true ? 'valid' : v.ok === 'warn' ? 'warn' : 'invalid');
    validBox.textContent = v.msg;

    if (v.ok === false) {
      grid.style.display = 'none';
      return;
    }

    const formatted = c.fmt(sub);
    const e164 = toE164(c.code, sub);
    const rfc = toRFC3966(c.code, sub);

    grid.style.display = 'grid';
    document.getElementById('val-intl').textContent = formatted ? formatted.intl : e164;
    document.getElementById('val-natl').textContent = formatted ? formatted.natl : `0${sub}`;
    document.getElementById('val-e164').textContent = e164;
    document.getElementById('val-rfc').textContent = rfc;
    document.getElementById('val-raw').textContent = sub;
  };

  window.pfCopy = function(id) {
    const text = document.getElementById(id).textContent;
    navigator.clipboard.writeText(text).then(() => {
      const btn = document.getElementById(id).nextElementSibling;
      const orig = btn.textContent;
      btn.textContent = 'Copied!';
      setTimeout(() => { btn.textContent = orig; }, 1500);
    });
  };

  window.pfSwitchTab = function(tab) {
    document.querySelectorAll('#pf-app .pf-tab').forEach((t,i) => {
      t.classList.toggle('active', ['single','bulk','ref'][i] === tab);
    });
    document.querySelectorAll('#pf-app .pf-tab-panel').forEach(p => p.classList.remove('active'));
    document.getElementById('pf-tab-' + tab).classList.add('active');
  };

  window.pfBulkFormat = function() {
    const lines = document.getElementById('pf-bulk-input').value.split('\n').filter(l => l.trim());
    const countryKey = document.getElementById('pf-bulk-country').value;
    const c = COUNTRIES[countryKey];
    const out = document.getElementById('pf-bulk-output');

    if (!lines.length) { out.innerHTML = ''; return; }

    let html = '';
    lines.forEach(line => {
      const raw = line.trim();
      if (!raw) return;
      const sub = normalize(raw, countryKey);
      const v = validate(sub, countryKey);
      const formatted = (v.ok !== false) ? c.fmt(sub) : null;
      const e164 = (v.ok !== false) ? toE164(c.code, sub) : '—';
      const badge = v.ok === true
        ? '<span class="pf-badge pf-badge-valid">Valid</span>'
        : v.ok === 'warn'
          ? '<span class="pf-badge pf-badge-warn">Warn</span>'
          : '<span class="pf-badge pf-badge-invalid">Invalid</span>';
      html += `<div class="bulk-output-line">
        ${badge}
        <span style="color:#888;min-width:140px;">${raw}</span>
        <span>→</span>
        <span>${formatted ? formatted.intl : '—'}</span>
        <span style="color:#888;">${e164}</span>
      </div>`;
    });
    out.innerHTML = html;
  };

  window.pfBulkClear = function() {
    document.getElementById('pf-bulk-input').value = '';
    document.getElementById('pf-bulk-output').innerHTML = '';
  };

  window.pfBulkCopyAll = function() {
    const lines = document.querySelectorAll('#pf-bulk-output .bulk-output-line');
    const text = Array.from(lines).map(l => {
      const spans = l.querySelectorAll('span');
      return spans[2] ? spans[2].textContent.trim() : '';
    }).filter(Boolean).join('\n');
    navigator.clipboard.writeText(text).then(() => alert('Results copied to clipboard!'));
  };

  // Build reference table
  function buildRefTable() {
    const tbody = document.getElementById('pf-ref-body');
    let html = '';
    Object.entries(COUNTRIES).forEach(([key, c]) => {
      const trunk = c.trunk || '(none)';
      const digStr = c.digits.join(', ') + ' digits';
      html += `<tr>
        <td><strong>${c.name}</strong> (${key})</td>
        <td>+${c.code}</td>
        <td>${trunk}</td>
        <td>${digStr}</td>
        <td style="font-family:monospace;font-size:0.83rem;">${c.example}</td>
      </tr>`;
    });
    tbody.innerHTML = html;
  }

  buildRefTable();

})();
</script>

---

**Related tools:**

- [Time Zone Converter](/tools/timezone-converter/) — Convert times across world time zones instantly
- [Unit Converter](/tools/unit-converter/) — Length, weight, temperature, and more
- [Currency Converter](/tools/currency-converter/) — Live exchange rates for 150+ currencies
- [QR Code Generator](/tools/qr-generator/) — Create QR codes for URLs, text, and contact info

</div>
