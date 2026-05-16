---
title: "IP Address Calculator - Subnet & CIDR Tools"
description: "Calculate IP subnets, network ranges, and CIDR notation. Free online IP address and subnet calculator."
date: 2025-05-16
slug: "ip-address-calculator"
categories: ["Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/ip-address-calculator.png"
---

<div id="ipc-app">
<style>
#ipc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
  line-height: 1.6;
}
#ipc-app h1 {
  font-size: 1.8rem;
  font-weight: 700;
  color: #0f3460;
  margin-bottom: 0.4rem;
}
#ipc-app .ipc-subtitle {
  color: #555;
  margin-bottom: 1.5rem;
  font-size: 0.97rem;
}
#ipc-app .ipc-card {
  background: #fff;
  border: 1px solid #d0d7e3;
  border-radius: 10px;
  padding: 1.4rem 1.6rem;
  margin-bottom: 1.4rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.06);
}
#ipc-app .ipc-card h2 {
  font-size: 1.05rem;
  font-weight: 600;
  color: #0f3460;
  margin: 0 0 1rem 0;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e8eaf6;
}
#ipc-app .ipc-input-row {
  display: flex;
  gap: 0.7rem;
  align-items: center;
  flex-wrap: wrap;
}
#ipc-app .ipc-input {
  flex: 1;
  min-width: 220px;
  padding: 0.65rem 1rem;
  font-size: 1rem;
  border: 2px solid #c5cfe0;
  border-radius: 7px;
  outline: none;
  transition: border-color 0.2s;
  font-family: monospace;
  background: #f8faff;
}
#ipc-app .ipc-input:focus {
  border-color: #3a7bd5;
  background: #fff;
}
#ipc-app .ipc-btn {
  padding: 0.65rem 1.5rem;
  background: #3a7bd5;
  color: #fff;
  border: none;
  border-radius: 7px;
  font-size: 0.97rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  white-space: nowrap;
}
#ipc-app .ipc-btn:hover {
  background: #2563b0;
}
#ipc-app .ipc-btn:active {
  transform: scale(0.98);
}
#ipc-app .ipc-btn-sm {
  padding: 0.4rem 0.9rem;
  font-size: 0.85rem;
  border-radius: 5px;
}
#ipc-app .ipc-examples {
  margin-top: 0.6rem;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}
#ipc-app .ipc-example-chip {
  background: #eef2fb;
  border: 1px solid #c5cfe0;
  border-radius: 20px;
  padding: 0.2rem 0.75rem;
  font-size: 0.82rem;
  cursor: pointer;
  font-family: monospace;
  color: #3a7bd5;
  transition: background 0.15s;
}
#ipc-app .ipc-example-chip:hover {
  background: #dce8fa;
}
#ipc-app .ipc-error {
  color: #c0392b;
  background: #fdf0ed;
  border: 1px solid #f5c6bb;
  border-radius: 7px;
  padding: 0.6rem 1rem;
  margin-top: 0.8rem;
  font-size: 0.92rem;
  display: none;
}
#ipc-app .ipc-results {
  display: none;
}
#ipc-app .ipc-badge-row {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}
#ipc-app .ipc-badge {
  border-radius: 20px;
  padding: 0.25rem 0.85rem;
  font-size: 0.82rem;
  font-weight: 600;
  letter-spacing: 0.02em;
}
#ipc-app .badge-class-a { background: #e3f2fd; color: #1565c0; border: 1px solid #90caf9; }
#ipc-app .badge-class-b { background: #e8f5e9; color: #2e7d32; border: 1px solid #a5d6a7; }
#ipc-app .badge-class-c { background: #fff3e0; color: #e65100; border: 1px solid #ffcc80; }
#ipc-app .badge-class-d { background: #fce4ec; color: #880e4f; border: 1px solid #f48fb1; }
#ipc-app .badge-class-e { background: #f3e5f5; color: #4a148c; border: 1px solid #ce93d8; }
#ipc-app .badge-private { background: #e8f5e9; color: #1b5e20; border: 1px solid #a5d6a7; }
#ipc-app .badge-public  { background: #e3f2fd; color: #0d47a1; border: 1px solid #90caf9; }
#ipc-app .ipc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 0.7rem;
  margin-bottom: 1rem;
}
#ipc-app .ipc-field {
  background: #f5f8ff;
  border: 1px solid #dde4f0;
  border-radius: 8px;
  padding: 0.65rem 0.9rem;
}
#ipc-app .ipc-field-label {
  font-size: 0.75rem;
  color: #7a8aaa;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin-bottom: 0.15rem;
  font-weight: 600;
}
#ipc-app .ipc-field-value {
  font-size: 1rem;
  font-weight: 700;
  color: #0f3460;
  font-family: monospace;
  word-break: break-all;
}
#ipc-app .ipc-field-sub {
  font-size: 0.75rem;
  color: #8899bb;
  margin-top: 0.1rem;
  font-family: monospace;
}
#ipc-app .ipc-section-title {
  font-size: 0.88rem;
  font-weight: 700;
  color: #556;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin: 0.8rem 0 0.4rem 0;
}
#ipc-app table.ipc-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.88rem;
}
#ipc-app table.ipc-table th {
  background: #eef2fb;
  color: #3a5080;
  font-weight: 700;
  padding: 0.45rem 0.7rem;
  text-align: left;
  border-bottom: 2px solid #c5cfe0;
}
#ipc-app table.ipc-table td {
  padding: 0.38rem 0.7rem;
  border-bottom: 1px solid #e8eaf6;
  font-family: monospace;
  color: #2a3a5a;
}
#ipc-app table.ipc-table tr:last-child td { border-bottom: none; }
#ipc-app table.ipc-table tr:hover td { background: #f5f8ff; }
#ipc-app .ipc-sub-form {
  display: flex;
  gap: 0.7rem;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 0.9rem;
}
#ipc-app .ipc-select {
  padding: 0.55rem 0.8rem;
  border: 2px solid #c5cfe0;
  border-radius: 7px;
  font-size: 0.92rem;
  background: #f8faff;
  color: #1a1a2e;
  outline: none;
}
#ipc-app .ipc-select:focus { border-color: #3a7bd5; }
#ipc-app .ipc-divider {
  border: none;
  border-top: 2px solid #e8eaf6;
  margin: 1rem 0;
}
#ipc-app .ipc-related {
  background: #f0f4ff;
  border: 1px solid #c5d3f0;
  border-radius: 9px;
  padding: 1rem 1.2rem;
  margin-top: 0.5rem;
}
#ipc-app .ipc-related h3 {
  font-size: 0.95rem;
  font-weight: 700;
  color: #3a5080;
  margin: 0 0 0.5rem 0;
}
#ipc-app .ipc-related ul {
  margin: 0;
  padding-left: 1.2rem;
}
#ipc-app .ipc-related li {
  margin-bottom: 0.25rem;
  font-size: 0.9rem;
}
#ipc-app .ipc-related a {
  color: #3a7bd5;
  text-decoration: none;
}
#ipc-app .ipc-related a:hover { text-decoration: underline; }
#ipc-app .ipc-highlight {
  background: #fffbea;
  border-left: 3px solid #f0b429;
  padding: 0.5rem 0.9rem;
  border-radius: 0 6px 6px 0;
  font-size: 0.88rem;
  color: #5c4b00;
  margin-top: 0.6rem;
}
@media (max-width: 600px) {
  #ipc-app .ipc-grid { grid-template-columns: 1fr; }
  #ipc-app .ipc-input-row { flex-direction: column; align-items: stretch; }
  #ipc-app .ipc-btn { width: 100%; }
}
</style>

<h1>IP Address Calculator</h1>
<p class="ipc-subtitle">Subnet, CIDR, and network analysis tools — instant results, no server required.</p>

<div class="ipc-card">
  <h2>IP / CIDR Input</h2>
  <div class="ipc-input-row">
    <input id="ipc-input" class="ipc-input" type="text" placeholder="e.g. 192.168.1.0/24" spellcheck="false" autocomplete="off" />
    <button class="ipc-btn" onclick="ipcCalculate()">Calculate</button>
    <button class="ipc-btn" style="background:#6c757d;" onclick="ipcReset()">Reset</button>
  </div>
  <div class="ipc-examples">
    <span>Try:</span>
    <span class="ipc-example-chip" onclick="ipcFill('192.168.1.0/24')">192.168.1.0/24</span>
    <span class="ipc-example-chip" onclick="ipcFill('10.0.0.0/8')">10.0.0.0/8</span>
    <span class="ipc-example-chip" onclick="ipcFill('172.16.0.0/12')">172.16.0.0/12</span>
    <span class="ipc-example-chip" onclick="ipcFill('203.0.113.50/28')">203.0.113.50/28</span>
    <span class="ipc-example-chip" onclick="ipcFill('100.64.0.0/10')">100.64.0.0/10</span>
  </div>
  <div id="ipc-error" class="ipc-error"></div>
</div>

<div id="ipc-results" class="ipc-results">

  <div class="ipc-card">
    <h2>Network Summary</h2>
    <div id="ipc-badges" class="ipc-badge-row"></div>
    <div class="ipc-grid" id="ipc-main-fields"></div>
  </div>

  <div class="ipc-card">
    <h2>Mask Details</h2>
    <div class="ipc-grid" id="ipc-mask-fields"></div>
  </div>

  <div class="ipc-card">
    <h2>Subnet Subdivision</h2>
    <p style="font-size:0.88rem;color:#556;margin:0 0 0.8rem 0;">Split the current network into smaller subnets by selecting a new prefix length.</p>
    <div class="ipc-sub-form">
      <label style="font-size:0.9rem;font-weight:600;color:#3a5080;">New prefix:</label>
      <select id="ipc-sub-select" class="ipc-select"></select>
      <button class="ipc-btn ipc-btn-sm" onclick="ipcSubdivide()">Subdivide</button>
    </div>
    <div id="ipc-sub-results"></div>
  </div>

  <div class="ipc-card">
    <h2>CIDR to Subnet Mask Reference Table</h2>
    <div style="overflow-x:auto;">
    <table class="ipc-table" id="ipc-ref-table">
      <thead>
        <tr>
          <th>CIDR</th>
          <th>Subnet Mask</th>
          <th>Wildcard Mask</th>
          <th>Total Hosts</th>
          <th>Usable Hosts</th>
        </tr>
      </thead>
      <tbody id="ipc-ref-body"></tbody>
    </table>
    </div>
  </div>

</div>

<div class="ipc-related">
  <h3>Related Tools</h3>
  <ul>
    <li><a href="/tools/binary-converter/">Binary / Hex / Decimal Converter</a></li>
    <li><a href="/tools/port-number-lookup/">Port Number Lookup</a></li>
    <li><a href="/tools/mac-address-lookup/">MAC Address Vendor Lookup</a></li>
    <li><a href="/tools/network-speed-calculator/">Network Speed & Bandwidth Calculator</a></li>
  </ul>
</div>

<script>
(function() {

  function ipcParseIP(str) {
    var parts = str.trim().split('.');
    if (parts.length !== 4) return null;
    var nums = parts.map(Number);
    if (nums.some(function(n) { return isNaN(n) || n < 0 || n > 255 || String(n) !== parts[nums.indexOf(n)]; })) return null;
    // re-map properly
    var ok = true;
    var out = parts.map(function(p) {
      var n = Number(p);
      if (isNaN(n) || n < 0 || n > 255) { ok = false; }
      return n;
    });
    return ok ? out : null;
  }

  function ipToInt(octets) {
    return ((octets[0] << 24) | (octets[1] << 16) | (octets[2] << 8) | octets[3]) >>> 0;
  }

  function intToIP(n) {
    n = n >>> 0;
    return [(n >>> 24) & 0xff, (n >>> 16) & 0xff, (n >>> 8) & 0xff, n & 0xff].join('.');
  }

  function intToBinary(n, bits) {
    bits = bits || 32;
    var s = (n >>> 0).toString(2);
    while (s.length < bits) s = '0' + s;
    return s.match(/.{1,8}/g).join('.');
  }

  function cidrToMask(prefix) {
    if (prefix === 0) return 0;
    return (0xFFFFFFFF << (32 - prefix)) >>> 0;
  }

  function getIPClass(firstOctet) {
    if (firstOctet < 128) return 'A';
    if (firstOctet < 192) return 'B';
    if (firstOctet < 224) return 'C';
    if (firstOctet < 240) return 'D';
    return 'E';
  }

  function isPrivate(octets) {
    var a = octets[0], b = octets[1];
    if (a === 10) return true;
    if (a === 172 && b >= 16 && b <= 31) return true;
    if (a === 192 && b === 168) return true;
    if (a === 127) return true;
    if (a === 169 && b === 254) return true;
    if (a === 100 && b >= 64 && b <= 127) return true; // CGNAT
    return false;
  }

  function formatNum(n) {
    return n.toLocaleString();
  }

  window.ipcFill = function(val) {
    document.getElementById('ipc-input').value = val;
    ipcCalculate();
  };

  window.ipcReset = function() {
    document.getElementById('ipc-input').value = '';
    document.getElementById('ipc-error').style.display = 'none';
    document.getElementById('ipc-results').style.display = 'none';
  };

  var currentPrefix = 24;
  var currentNetInt = 0;

  window.ipcCalculate = function() {
    var raw = document.getElementById('ipc-input').value.trim();
    var errEl = document.getElementById('ipc-error');
    errEl.style.display = 'none';

    var parts = raw.split('/');
    if (parts.length !== 2) {
      errEl.textContent = 'Please enter an IP address with CIDR prefix, e.g. 192.168.1.0/24';
      errEl.style.display = 'block';
      document.getElementById('ipc-results').style.display = 'none';
      return;
    }

    var octets = ipcParseIP(parts[0]);
    var prefix = parseInt(parts[1], 10);

    if (!octets) {
      errEl.textContent = 'Invalid IP address. Each octet must be 0-255.';
      errEl.style.display = 'block';
      document.getElementById('ipc-results').style.display = 'none';
      return;
    }
    if (isNaN(prefix) || prefix < 0 || prefix > 32) {
      errEl.textContent = 'Invalid prefix length. Must be 0-32.';
      errEl.style.display = 'block';
      document.getElementById('ipc-results').style.display = 'none';
      return;
    }

    var ipInt = ipToInt(octets);
    var maskInt = cidrToMask(prefix);
    var wildInt = (~maskInt) >>> 0;
    var netInt = (ipInt & maskInt) >>> 0;
    var bcastInt = (netInt | wildInt) >>> 0;
    var totalHosts = Math.pow(2, 32 - prefix);
    var usableHosts = prefix >= 31 ? (prefix === 32 ? 1 : 2) : totalHosts - 2;
    var firstHost = prefix >= 31 ? netInt : netInt + 1;
    var lastHost = prefix >= 31 ? bcastInt : bcastInt - 1;

    currentPrefix = prefix;
    currentNetInt = netInt;

    var ipClass = getIPClass(octets[0]);
    var priv = isPrivate(octets);

    // Badges
    var badgeRow = document.getElementById('ipc-badges');
    var classBadgeClass = 'badge-class-' + ipClass.toLowerCase();
    badgeRow.innerHTML =
      '<span class="ipc-badge ' + classBadgeClass + '">Class ' + ipClass + '</span>' +
      '<span class="ipc-badge ' + (priv ? 'badge-private' : 'badge-public') + '">' + (priv ? 'Private' : 'Public') + '</span>' +
      '<span class="ipc-badge" style="background:#e8eaf6;color:#3a3a6a;border:1px solid #b0b8d8;">/' + prefix + '</span>' +
      (octets[0] === 127 ? '<span class="ipc-badge" style="background:#fce4ec;color:#880e4f;border:1px solid #f48fb1;">Loopback</span>' : '') +
      (octets[0] === 169 && octets[1] === 254 ? '<span class="ipc-badge" style="background:#fff3e0;color:#e65100;border:1px solid #ffcc80;">Link-local</span>' : '') +
      (octets[0] === 100 && octets[1] >= 64 && octets[1] <= 127 ? '<span class="ipc-badge" style="background:#f3e5f5;color:#4a148c;border:1px solid #ce93d8;">CGNAT</span>' : '') +
      (ipClass === 'D' ? '<span class="ipc-badge" style="background:#fce4ec;color:#880e4f;border:1px solid #f48fb1;">Multicast</span>' : '') +
      (ipClass === 'E' ? '<span class="ipc-badge" style="background:#f3e5f5;color:#4a148c;border:1px solid #ce93d8;">Reserved</span>' : '');

    // Main fields
    var mainFields = document.getElementById('ipc-main-fields');
    mainFields.innerHTML = [
      { label: 'IP Address', value: intToIP(ipInt), sub: intToBinary(ipInt) },
      { label: 'Network Address', value: intToIP(netInt), sub: intToBinary(netInt) },
      { label: 'Broadcast Address', value: intToIP(bcastInt), sub: intToBinary(bcastInt) },
      { label: 'First Usable Host', value: intToIP(firstHost), sub: '' },
      { label: 'Last Usable Host', value: intToIP(lastHost), sub: '' },
      { label: 'Total Hosts', value: formatNum(totalHosts), sub: 'including network & broadcast' },
      { label: 'Usable Hosts', value: formatNum(usableHosts >= 0 ? usableHosts : 0), sub: 'assignable addresses' },
    ].map(function(f) {
      return '<div class="ipc-field"><div class="ipc-field-label">' + f.label + '</div>' +
        '<div class="ipc-field-value">' + f.value + '</div>' +
        (f.sub ? '<div class="ipc-field-sub">' + f.sub + '</div>' : '') + '</div>';
    }).join('');

    // Mask fields
    var maskFields = document.getElementById('ipc-mask-fields');
    maskFields.innerHTML = [
      { label: 'Subnet Mask', value: intToIP(maskInt), sub: intToBinary(maskInt) },
      { label: 'Wildcard Mask', value: intToIP(wildInt), sub: intToBinary(wildInt) },
      { label: 'CIDR Notation', value: '/' + prefix, sub: prefix + ' network bits, ' + (32 - prefix) + ' host bits' },
      { label: 'Integer (Network)', value: netInt.toString(), sub: '0x' + netInt.toString(16).toUpperCase().padStart(8, '0') },
    ].map(function(f) {
      return '<div class="ipc-field"><div class="ipc-field-label">' + f.label + '</div>' +
        '<div class="ipc-field-value">' + f.value + '</div>' +
        (f.sub ? '<div class="ipc-field-sub">' + f.sub + '</div>' : '') + '</div>';
    }).join('');

    // Subdivision select
    var sel = document.getElementById('ipc-sub-select');
    sel.innerHTML = '';
    for (var p = prefix + 1; p <= 30; p++) {
      var opt = document.createElement('option');
      opt.value = p;
      opt.textContent = '/' + p + ' (' + formatNum(Math.pow(2, 32 - p) - 2) + ' hosts each)';
      sel.appendChild(opt);
    }
    document.getElementById('ipc-sub-results').innerHTML = '';

    // Reference table
    buildRefTable(prefix);

    document.getElementById('ipc-results').style.display = 'block';
  };

  window.ipcSubdivide = function() {
    var newPrefix = parseInt(document.getElementById('ipc-sub-select').value, 10);
    var count = Math.pow(2, newPrefix - currentPrefix);
    var display = Math.min(count, 64);
    var subSize = Math.pow(2, 32 - newPrefix);
    var rows = [];
    for (var i = 0; i < display; i++) {
      var netI = (currentNetInt + i * subSize) >>> 0;
      var bcastI = (netI + subSize - 1) >>> 0;
      rows.push('<tr><td>#' + (i + 1) + '</td><td>' + intToIP(netI) + '/' + newPrefix + '</td><td>' + intToIP(netI) + '</td><td>' + intToIP(bcastI) + '</td><td>' + intToIP(netI + 1) + '</td><td>' + intToIP(bcastI - 1) + '</td><td>' + formatNum(subSize - 2) + '</td></tr>');
    }
    var extra = count > display ? '<p style="font-size:0.82rem;color:#888;margin:0.4rem 0 0 0;">Showing first ' + display + ' of ' + formatNum(count) + ' subnets.</p>' : '';
    document.getElementById('ipc-sub-results').innerHTML =
      '<div style="overflow-x:auto;"><table class="ipc-table"><thead><tr><th>#</th><th>Subnet</th><th>Network</th><th>Broadcast</th><th>First Host</th><th>Last Host</th><th>Usable Hosts</th></tr></thead><tbody>' +
      rows.join('') + '</tbody></table></div>' + extra;
  };

  function buildRefTable(highlight) {
    var body = document.getElementById('ipc-ref-body');
    var rows = [];
    for (var p = 8; p <= 30; p++) {
      var mask = cidrToMask(p);
      var wild = (~mask) >>> 0;
      var total = Math.pow(2, 32 - p);
      var usable = total - 2;
      var hl = (p === highlight) ? ' style="background:#fffbea;font-weight:700;"' : '';
      rows.push('<tr' + hl + '><td>/' + p + '</td><td>' + intToIP(mask) + '</td><td>' + intToIP(wild) + '</td><td>' + formatNum(total) + '</td><td>' + formatNum(usable) + '</td></tr>');
    }
    body.innerHTML = rows.join('');
  }

  // Initialize reference table on load
  buildRefTable(-1);

  // Allow Enter key
  document.getElementById('ipc-input').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') ipcCalculate();
  });

})();
</script>

</div>

---

## Related Tools

> [Api Request Builder](/tools/api-request-builder/)
> [Dns Record Guide](/tools/dns-record-guide/)
> [Http Status Codes](/tools/http-status-codes/)

