---
title: "IP Subnet Visualizer - Free CIDR Calculator & Subnet Tool"
date: 2025-05-16
description: "Visual CIDR subnet calculator. Enter IP/CIDR to see network address, broadcast, usable host range, and host count. Color-coded binary breakdown, subnet table, and address space canvas. Free, no install."
categories: ["Free Tools"]
tags: ["subnet calculator", "CIDR calculator", "IP subnet", "network address", "broadcast address", "subnet mask", "IPv4"]
slug: "ip-subnet-visualizer"
aliases: ["/tools/subnet-visualizer/", "/tools/cidr-calculator/"]
cover:
  image: "/images/covers/ip-subnet-visualizer.png"
  alt: "IP Subnet Visualizer"
ShowToc: false
---

<div id="isv-app">

<style>
#isv-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  max-width: 900px;
  margin: 0 auto;
  box-sizing: border-box;
}
#isv-app * { box-sizing: border-box; }

#isv-app h2 {
  color: #38bdf8;
  font-size: 1.05rem;
  margin: 0 0 14px;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

#isv-app .input-row {
  display: flex;
  gap: 10px;
  margin-bottom: 16px;
  flex-wrap: wrap;
  align-items: stretch;
}
#isv-app .cidr-input {
  flex: 1;
  min-width: 200px;
  background: #1e293b;
  border: 1.5px solid #334155;
  color: #e2e8f0;
  border-radius: 8px;
  padding: 11px 14px;
  font-size: 1.05rem;
  font-family: 'Courier New', monospace;
  transition: border-color 0.15s;
}
#isv-app .cidr-input:focus { outline: none; border-color: #38bdf8; }
#isv-app .cidr-input.error { border-color: #ef4444; }
#isv-app .calc-btn {
  background: #0284c7;
  border: none;
  color: #fff;
  border-radius: 8px;
  padding: 11px 22px;
  font-size: 0.95rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
}
#isv-app .calc-btn:hover { background: #0369a1; }
#isv-app .error-line {
  color: #ef4444;
  font-size: 0.83rem;
  margin: -10px 0 12px;
  min-height: 18px;
}

#isv-app .results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 10px;
  margin-bottom: 20px;
}
#isv-app .res-card {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 10px;
  padding: 13px 15px;
}
#isv-app .res-card .rc-label {
  font-size: 0.72rem;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.09em;
  font-weight: 600;
  margin-bottom: 5px;
}
#isv-app .res-card .rc-value {
  font-family: 'Courier New', monospace;
  font-size: 0.97rem;
  color: #38bdf8;
  word-break: break-all;
  min-height: 20px;
}
#isv-app .res-card .rc-value.green { color: #4ade80; }
#isv-app .res-card .rc-value.orange { color: #fb923c; }
#isv-app .res-card .rc-value.yellow { color: #facc15; }

#isv-app .binary-section {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 18px;
}
#isv-app .bin-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 9px;
  flex-wrap: wrap;
}
#isv-app .bin-row:last-child { margin-bottom: 0; }
#isv-app .bin-label {
  font-size: 0.75rem;
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  font-weight: 600;
  min-width: 100px;
}
#isv-app .bin-bits {
  display: flex;
  gap: 2px;
  flex-wrap: wrap;
  font-family: 'Courier New', monospace;
  font-size: 0.82rem;
}
#isv-app .bin-octet {
  display: flex;
  gap: 2px;
  margin-right: 6px;
}
#isv-app .bin-bit {
  width: 18px;
  height: 22px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 3px;
  font-weight: 700;
  font-size: 0.8rem;
}
#isv-app .bin-bit.net { background: #1d4ed8; color: #93c5fd; }
#isv-app .bin-bit.host { background: #166534; color: #86efac; }
#isv-app .bin-bit.zero { background: #1e3a5f; color: #93c5fd; opacity: 0.5; }
#isv-app .bin-legend {
  display: flex;
  gap: 16px;
  margin-top: 10px;
  flex-wrap: wrap;
}
#isv-app .bin-legend-item {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 0.78rem;
  color: #94a3b8;
}
#isv-app .bin-legend-swatch {
  width: 14px;
  height: 14px;
  border-radius: 3px;
}

#isv-app .canvas-section {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 18px;
}
#isv-app #isv-canvas {
  width: 100%;
  height: 48px;
  border-radius: 6px;
  display: block;
}
#isv-app .canvas-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.72rem;
  color: #64748b;
  margin-top: 5px;
  font-family: 'Courier New', monospace;
}

#isv-app .table-section {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 10px;
  padding: 16px;
  overflow-x: auto;
}
#isv-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.82rem;
  font-family: 'Courier New', monospace;
  min-width: 480px;
}
#isv-app thead th {
  color: #64748b;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  font-size: 0.72rem;
  font-weight: 600;
  padding: 7px 10px;
  text-align: left;
  border-bottom: 1px solid #334155;
}
#isv-app tbody td {
  padding: 6px 10px;
  color: #cbd5e1;
  border-bottom: 1px solid #1e293b;
  white-space: nowrap;
}
#isv-app tbody tr:last-child td { border-bottom: none; }
#isv-app tbody tr.current-row td {
  background: #0c2d4a;
  color: #38bdf8;
  font-weight: 700;
}
#isv-app tbody tr:hover td { background: #263448; }
#isv-app tbody td.hosts-col { color: #4ade80; }

#isv-app .placeholder {
  text-align: center;
  color: #475569;
  padding: 32px 0;
  font-size: 0.95rem;
}

@media (max-width: 560px) {
  #isv-app .results-grid { grid-template-columns: 1fr 1fr; }
  #isv-app .bin-label { min-width: 80px; }
}
</style>

<h2>IP Subnet Visualizer</h2>

<div class="input-row">
  <input class="cidr-input" id="isv-input" type="text" placeholder="e.g. 192.168.1.0/24 or 10.0.5.37/18"
    oninput="isvCalc()" autocomplete="off" spellcheck="false" value="">
  <button class="calc-btn" onclick="isvCalc()">Calculate</button>
</div>
<div class="error-line" id="isv-error"></div>

<div id="isv-results" style="display:none">

  <div class="results-grid" id="isv-cards"></div>

  <div class="binary-section">
    <h2>Binary Breakdown</h2>
    <div id="isv-bin-rows"></div>
    <div class="bin-legend">
      <div class="bin-legend-item">
        <div class="bin-legend-swatch" style="background:#1d4ed8;"></div>
        Network bits
      </div>
      <div class="bin-legend-item">
        <div class="bin-legend-swatch" style="background:#166534;"></div>
        Host bits
      </div>
    </div>
  </div>

  <div class="canvas-section">
    <h2>Address Space</h2>
    <canvas id="isv-canvas" height="48"></canvas>
    <div class="canvas-labels">
      <span id="isv-cv-start">0.0.0.0</span>
      <span style="color:#38bdf8;">&#9632; This subnet</span>
      <span id="isv-cv-end">255.255.255.255</span>
    </div>
  </div>

  <div class="table-section">
    <h2>Subnet Reference Table (/8 – /32)</h2>
    <table>
      <thead>
        <tr>
          <th>Prefix</th>
          <th>Subnet Mask</th>
          <th>Hosts</th>
          <th>Network Size</th>
        </tr>
      </thead>
      <tbody id="isv-tbl-body"></tbody>
    </table>
  </div>

</div>

<div class="placeholder" id="isv-placeholder">Enter an IP address with CIDR prefix (e.g. 192.168.1.0/24)</div>

<script>
(function() {
  function ipToNum(ip) {
    var parts = ip.split('.');
    if (parts.length !== 4) return null;
    var n = 0;
    for (var i = 0; i < 4; i++) {
      var p = parseInt(parts[i], 10);
      if (isNaN(p) || p < 0 || p > 255) return null;
      n = (n * 256) + p;
    }
    return n >>> 0;
  }

  function numToIp(n) {
    n = n >>> 0;
    return [(n >>> 24) & 255, (n >>> 16) & 255, (n >>> 8) & 255, n & 255].join('.');
  }

  function maskFromPrefix(prefix) {
    if (prefix === 0) return 0;
    return (0xFFFFFFFF << (32 - prefix)) >>> 0;
  }

  function numToHostCount(prefix) {
    if (prefix >= 32) return 1;
    if (prefix === 31) return 2;
    return Math.pow(2, 32 - prefix) - 2;
  }

  function formatHosts(n) {
    if (n <= 0) return n === 1 ? '1 (host route)' : '0';
    if (n >= 1000000) return (n / 1000000).toFixed(2) + 'M';
    if (n >= 1000) return n.toLocaleString();
    return n.toString();
  }

  function parseCIDR(val) {
    val = val.trim();
    var slash = val.indexOf('/');
    if (slash === -1) return null;
    var ipStr = val.slice(0, slash);
    var prefixStr = val.slice(slash + 1);
    var prefix = parseInt(prefixStr, 10);
    if (isNaN(prefix) || prefix < 0 || prefix > 32) return null;
    var ipNum = ipToNum(ipStr);
    if (ipNum === null) return null;
    return { ipNum: ipNum, prefix: prefix, ipStr: ipStr };
  }

  function renderBinaryRow(label, num, prefix, colorMode) {
    // colorMode: 'ip' shows net/host split, 'mask' shows all net bits, 'addr' flat color
    var bits = [];
    for (var i = 31; i >= 0; i--) {
      bits.push((num >>> i) & 1);
    }
    var octets = [];
    for (var o = 0; o < 4; o++) {
      var octetBits = bits.slice(o * 8, o * 8 + 8);
      var cells = octetBits.map(function(b, idx) {
        var bitPos = o * 8 + idx;
        var cls = 'bin-bit';
        if (colorMode === 'ip') {
          cls += bitPos < prefix ? ' net' : ' host';
        } else if (colorMode === 'mask') {
          cls += b === 1 ? ' net' : ' zero';
        } else {
          cls += b === 1 ? ' net' : ' zero';
        }
        return '<div class="' + cls + '">' + b + '</div>';
      }).join('');
      octets.push('<div class="bin-octet">' + cells + '</div>');
    }
    return '<div class="bin-row"><span class="bin-label">' + label + '</span><div class="bin-bits">' + octets.join('') + '</div></div>';
  }

  function renderCanvas(networkNum, broadcastNum) {
    var canvas = document.getElementById('isv-canvas');
    var W = canvas.offsetWidth || 800;
    canvas.width = W;
    canvas.height = 48;
    var ctx = canvas.getContext('2d');

    // Background gradient: full IPv4 space
    var grad = ctx.createLinearGradient(0, 0, W, 0);
    grad.addColorStop(0, '#0f2744');
    grad.addColorStop(1, '#1e3a5f');
    ctx.fillStyle = grad;
    ctx.roundRect ? ctx.roundRect(0, 0, W, 48, 6) : ctx.fillRect(0, 0, W, 48);
    ctx.fill();

    // Subnet block
    var total = 4294967295;
    var x1 = Math.floor((networkNum / total) * W);
    var x2 = Math.ceil((broadcastNum / total) * W);
    if (x2 - x1 < 2) x2 = x1 + 2;

    var subGrad = ctx.createLinearGradient(x1, 0, x2, 0);
    subGrad.addColorStop(0, '#0284c7');
    subGrad.addColorStop(1, '#38bdf8');
    ctx.fillStyle = subGrad;
    ctx.fillRect(x1, 6, x2 - x1, 36);

    // Border on subnet
    ctx.strokeStyle = '#7dd3fc';
    ctx.lineWidth = 1;
    ctx.strokeRect(x1, 6, x2 - x1, 36);

    document.getElementById('isv-cv-start').textContent = '0.0.0.0';
    document.getElementById('isv-cv-end').textContent = '255.255.255.255';
  }

  function renderTable(currentPrefix) {
    var body = document.getElementById('isv-tbl-body');
    var rows = [];
    for (var p = 8; p <= 32; p++) {
      var mask = maskFromPrefix(p);
      var hosts = numToHostCount(p);
      var size = Math.pow(2, 32 - p);
      var sizeStr = size >= 1000000 ? (size / 1000000).toFixed(0) + 'M' : size >= 1000 ? size.toLocaleString() : size.toString();
      var isCurrent = (p === currentPrefix);
      rows.push(
        '<tr class="' + (isCurrent ? 'current-row' : '') + '">' +
        '<td>/' + p + '</td>' +
        '<td>' + numToIp(mask) + '</td>' +
        '<td class="hosts-col">' + (hosts > 0 ? hosts.toLocaleString() : (p === 32 ? '1' : '0')) + '</td>' +
        '<td>' + sizeStr + ' addr</td>' +
        '</tr>'
      );
    }
    body.innerHTML = rows.join('');
    // Scroll current row into view
    var cur = body.querySelector('.current-row');
    if (cur) { setTimeout(function() { cur.scrollIntoView({ block: 'nearest' }); }, 50); }
  }

  window.isvCalc = function() {
    var val = document.getElementById('isv-input').value;
    var errEl = document.getElementById('isv-error');
    var inp = document.getElementById('isv-input');
    var resultsEl = document.getElementById('isv-results');
    var placeholderEl = document.getElementById('isv-placeholder');

    if (!val.trim()) {
      errEl.textContent = '';
      inp.classList.remove('error');
      resultsEl.style.display = 'none';
      placeholderEl.style.display = '';
      return;
    }

    var parsed = parseCIDR(val);
    if (!parsed) {
      errEl.textContent = 'Invalid CIDR notation. Use format: 192.168.1.0/24';
      inp.classList.add('error');
      resultsEl.style.display = 'none';
      placeholderEl.style.display = '';
      return;
    }
    errEl.textContent = '';
    inp.classList.remove('error');

    var prefix = parsed.prefix;
    var ipNum = parsed.ipNum;
    var mask = maskFromPrefix(prefix);
    var networkNum = (ipNum & mask) >>> 0;
    var broadcastNum = (networkNum | (~mask)) >>> 0;
    var firstHost = prefix < 31 ? ((networkNum + 1) >>> 0) : networkNum;
    var lastHost = prefix < 31 ? ((broadcastNum - 1) >>> 0) : broadcastNum;
    var hostCount = numToHostCount(prefix);
    var totalAddrs = Math.pow(2, 32 - prefix);

    // Cards
    var cards = [
      { label: 'IP Address', value: parsed.ipStr, cls: '' },
      { label: 'Network Address', value: numToIp(networkNum), cls: '' },
      { label: 'Broadcast', value: numToIp(broadcastNum), cls: 'orange' },
      { label: 'Subnet Mask', value: numToIp(mask), cls: '' },
      { label: 'First Host', value: prefix < 31 ? numToIp(firstHost) : 'N/A', cls: 'green' },
      { label: 'Last Host', value: prefix < 31 ? numToIp(lastHost) : 'N/A', cls: 'green' },
      { label: 'Usable Hosts', value: hostCount > 0 ? hostCount.toLocaleString() : (prefix === 32 ? '1' : '0'), cls: 'yellow' },
      { label: 'Total Addresses', value: totalAddrs.toLocaleString(), cls: '' },
    ];
    var cardsHtml = cards.map(function(c) {
      return '<div class="res-card"><div class="rc-label">' + c.label + '</div><div class="rc-value ' + c.cls + '">' + c.value + '</div></div>';
    }).join('');
    document.getElementById('isv-cards').innerHTML = cardsHtml;

    // Binary rows
    var binHtml = '';
    binHtml += renderBinaryRow('IP Address', ipNum, prefix, 'ip');
    binHtml += renderBinaryRow('Subnet Mask', mask, prefix, 'mask');
    binHtml += renderBinaryRow('Network Addr', networkNum, prefix, 'ip');
    binHtml += renderBinaryRow('Broadcast', broadcastNum, prefix, 'ip');
    document.getElementById('isv-bin-rows').innerHTML = binHtml;

    // Canvas
    renderCanvas(networkNum, broadcastNum);

    // Table
    renderTable(prefix);

    resultsEl.style.display = '';
    placeholderEl.style.display = 'none';
  };

  // Auto-calc on load if value preset
  window.addEventListener('load', function() {
    var inp = document.getElementById('isv-input');
    if (inp.value) isvCalc();
    // Redraw canvas on resize
    window.addEventListener('resize', function() {
      var val = document.getElementById('isv-input').value;
      if (val.trim()) isvCalc();
    });
  });
})();
</script>

</div>

---

> IP address info → [IP Address Info](/tools/ip-address-info/)
