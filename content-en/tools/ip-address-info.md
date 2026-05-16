---
title: "IP Address Info — Subnet Calculator, IP Converter & Network Tools"
date: 2025-05-16
description: "Free IP address toolkit: subnet calculator, IPv4/decimal converter, private/public range checker, IP class identifier, WebRTC local IP detection, and connection info — no install needed."
categories: ["Free Tools"]
slug: "ip-address-info"
tags: ["ip address", "subnet calculator", "cidr", "ip converter", "network tools", "webrtc", "ipv4"]
cover:
  image: "/images/covers/ip-address-info.png"
  alt: "IP Address Info"
ShowToc: false
aliases:
  - "/tools/my-ip/"
  - "/tools/ip-lookup/"
---

Detect your local network info, calculate subnets, convert IPv4 to decimal, check IP classes, and validate addresses — all in your browser with no external requests.

<div id="ip-app">

<style>
#ip-app {
  font-family: system-ui, -apple-system, sans-serif;
  background: #0f172a;
  color: #e2e8f0;
  max-width: 900px;
  margin: 0 auto;
  padding: 1.5rem;
  border-radius: 14px;
}
#ip-app * { box-sizing: border-box; }

#ip-app h2 {
  font-size: 1.05rem;
  font-weight: 700;
  color: #22c55e;
  margin: 1.8rem 0 0.7rem;
  border-left: 4px solid #22c55e;
  padding-left: 0.65rem;
  letter-spacing: 0.02em;
}
#ip-app h2:first-of-type { margin-top: 0; }

#ip-app .ip-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 0.75rem;
  margin-bottom: 1rem;
}

#ip-app .ip-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 0.85rem 1rem;
}
#ip-app .ip-card .ip-label {
  font-size: 0.68rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
  margin-bottom: 0.3rem;
}
#ip-app .ip-card .ip-value {
  font-size: 1.1rem;
  font-weight: 700;
  color: #22c55e;
  word-break: break-all;
}
#ip-app .ip-card .ip-value.muted {
  color: #94a3b8;
  font-size: 0.9rem;
  font-weight: 500;
}

#ip-app .ip-badge {
  display: inline-block;
  padding: 0.2rem 0.6rem;
  border-radius: 99px;
  font-size: 0.72rem;
  font-weight: 600;
  margin-top: 0.2rem;
}
#ip-app .ip-badge.green { background: #14532d; color: #86efac; }
#ip-app .ip-badge.blue  { background: #1e3a5f; color: #93c5fd; }
#ip-app .ip-badge.amber { background: #451a03; color: #fcd34d; }
#ip-app .ip-badge.red   { background: #450a0a; color: #fca5a5; }

#ip-app .ip-section {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 1.2rem;
  margin-bottom: 1.2rem;
}

#ip-app label {
  display: block;
  font-size: 0.8rem;
  color: #94a3b8;
  margin-bottom: 0.3rem;
  margin-top: 0.8rem;
}
#ip-app label:first-child { margin-top: 0; }

#ip-app input[type="text"], #ip-app input[type="number"], #ip-app select {
  width: 100%;
  background: #0f172a;
  border: 1px solid #475569;
  border-radius: 8px;
  color: #e2e8f0;
  padding: 0.55rem 0.8rem;
  font-size: 0.95rem;
  outline: none;
  transition: border-color 0.2s;
}
#ip-app input[type="text"]:focus,
#ip-app input[type="number"]:focus,
#ip-app select:focus {
  border-color: #22c55e;
}
#ip-app input.error { border-color: #ef4444; }

#ip-app .ip-row {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}
#ip-app .ip-row > * { flex: 1; min-width: 140px; }

#ip-app button {
  background: #22c55e;
  color: #0f172a;
  border: none;
  border-radius: 8px;
  padding: 0.6rem 1.4rem;
  font-size: 0.9rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 0.9rem;
  transition: background 0.15s;
}
#ip-app button:hover { background: #16a34a; }

#ip-app .ip-result-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 1rem;
  font-size: 0.88rem;
}
#ip-app .ip-result-table td {
  padding: 0.5rem 0.75rem;
  border-bottom: 1px solid #1e293b;
}
#ip-app .ip-result-table td:first-child {
  color: #64748b;
  width: 50%;
  font-size: 0.8rem;
}
#ip-app .ip-result-table td:last-child {
  color: #22c55e;
  font-weight: 600;
  word-break: break-all;
}
#ip-app .ip-result-table tr:last-child td { border-bottom: none; }

#ip-app .ip-msg {
  font-size: 0.82rem;
  margin-top: 0.6rem;
  padding: 0.5rem 0.75rem;
  border-radius: 7px;
}
#ip-app .ip-msg.ok  { background: #14532d44; color: #86efac; border: 1px solid #14532d; }
#ip-app .ip-msg.err { background: #450a0a44; color: #fca5a5; border: 1px solid #450a0a; }
#ip-app .ip-msg.info { background: #1e3a5f44; color: #93c5fd; border: 1px solid #1e3a5f; }

#ip-app .webrtc-note {
  font-size: 0.78rem;
  color: #475569;
  margin-top: 0.4rem;
  line-height: 1.5;
}

#ip-app .ip-divider {
  border: none;
  border-top: 1px solid #334155;
  margin: 1.2rem 0;
}

#ip-app .subnet-vis {
  margin-top: 0.9rem;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 0.75rem 1rem;
}
#ip-app .subnet-vis .sv-bar {
  height: 18px;
  border-radius: 4px;
  background: linear-gradient(90deg, #22c55e 0%, #16a34a 100%);
  margin: 0.4rem 0;
  position: relative;
  overflow: hidden;
}
#ip-app .subnet-vis .sv-label {
  font-size: 0.72rem;
  color: #64748b;
}
#ip-app .subnet-vis .sv-count {
  font-size: 1rem;
  font-weight: 700;
  color: #22c55e;
}

@media (max-width: 520px) {
  #ip-app { padding: 1rem; }
  #ip-app .ip-row { flex-direction: column; }
}
</style>

<!-- ===== SECTION 1: LOCAL NETWORK & BROWSER INFO ===== -->
<h2>Your Connection & Browser Info</h2>
<div class="ip-grid" id="info-grid">
  <div class="ip-card"><div class="ip-label">Connection Type</div><div class="ip-value" id="conn-type">Detecting…</div></div>
  <div class="ip-card"><div class="ip-label">Effective Speed</div><div class="ip-value" id="conn-speed">—</div></div>
  <div class="ip-card"><div class="ip-label">Screen Resolution</div><div class="ip-value" id="screen-res">—</div></div>
  <div class="ip-card"><div class="ip-label">Color Depth</div><div class="ip-value" id="color-depth">—</div></div>
  <div class="ip-card"><div class="ip-label">Browser</div><div class="ip-value muted" id="browser-name">—</div></div>
  <div class="ip-card"><div class="ip-label">Platform / OS</div><div class="ip-value muted" id="os-name">—</div></div>
  <div class="ip-card"><div class="ip-label">Language</div><div class="ip-value" id="lang">—</div></div>
  <div class="ip-card"><div class="ip-label">Cookies Enabled</div><div class="ip-value" id="cookies">—</div></div>
</div>

<!-- ===== SECTION 2: WebRTC LOCAL IP ===== -->
<h2>Local IP Detection (WebRTC)</h2>
<div class="ip-section">
  <div id="webrtc-ips"><span style="color:#64748b;font-size:0.9rem;">Attempting WebRTC detection…</span></div>
  <p class="webrtc-note">WebRTC can reveal your local (LAN) IP addresses assigned by your router. This works in most modern browsers without any permissions. Results depend on your network configuration — VPN or firewall may suppress results.</p>
</div>

<!-- ===== SECTION 3: SUBNET CALCULATOR ===== -->
<h2>Subnet Calculator (CIDR)</h2>
<div class="ip-section">
  <div class="ip-row">
    <div>
      <label>IPv4 Address</label>
      <input type="text" id="sub-ip" placeholder="e.g. 192.168.1.50" maxlength="18">
    </div>
    <div>
      <label>CIDR Prefix Length</label>
      <input type="number" id="sub-cidr" placeholder="e.g. 24" min="0" max="32" value="24">
    </div>
  </div>
  <button onclick="calcSubnet()">Calculate Subnet</button>
  <div id="sub-msg"></div>
  <table class="ip-result-table" id="sub-table" style="display:none">
    <tbody>
      <tr><td>Network Address</td><td id="sub-network">—</td></tr>
      <tr><td>Subnet Mask</td><td id="sub-mask">—</td></tr>
      <tr><td>Broadcast Address</td><td id="sub-broadcast">—</td></tr>
      <tr><td>First Usable Host</td><td id="sub-first">—</td></tr>
      <tr><td>Last Usable Host</td><td id="sub-last">—</td></tr>
      <tr><td>Number of Hosts</td><td id="sub-hosts">—</td></tr>
      <tr><td>Total Addresses</td><td id="sub-total">—</td></tr>
      <tr><td>Wildcard Mask</td><td id="sub-wild">—</td></tr>
    </tbody>
  </table>
  <div id="sub-vis" class="subnet-vis" style="display:none">
    <div class="sv-label">Usable Host Capacity</div>
    <div class="sv-bar" id="sub-bar"></div>
    <div class="sv-count" id="sub-bar-label"></div>
  </div>
</div>

<!-- ===== SECTION 4: IP CLASS & RANGE CHECKER ===== -->
<h2>IP Class & Range Checker</h2>
<div class="ip-section">
  <label>IPv4 Address</label>
  <input type="text" id="cls-ip" placeholder="e.g. 10.0.0.1" maxlength="18">
  <button onclick="checkClass()">Check IP Class</button>
  <div id="cls-result"></div>
</div>

<!-- ===== SECTION 5: IPv4 ↔ DECIMAL CONVERTER ===== -->
<h2>IPv4 ↔ Decimal Converter</h2>
<div class="ip-section">
  <div class="ip-row">
    <div>
      <label>IPv4 Address</label>
      <input type="text" id="conv-ipv4" placeholder="e.g. 192.168.1.1" maxlength="18">
    </div>
    <div>
      <label>Decimal (32-bit)</label>
      <input type="text" id="conv-dec" placeholder="e.g. 3232235777">
    </div>
  </div>
  <div class="ip-row">
    <button onclick="ipToDecimal()">IPv4 → Decimal</button>
    <button onclick="decimalToIp()">Decimal → IPv4</button>
  </div>
  <div id="conv-msg"></div>
  <table class="ip-result-table" id="conv-table" style="display:none">
    <tbody>
      <tr><td>IPv4 Address</td><td id="conv-r-ipv4">—</td></tr>
      <tr><td>Decimal</td><td id="conv-r-dec">—</td></tr>
      <tr><td>Binary</td><td id="conv-r-bin">—</td></tr>
      <tr><td>Hexadecimal</td><td id="conv-r-hex">—</td></tr>
    </tbody>
  </table>
</div>

<!-- ===== SECTION 6: IPv4 VALIDATOR ===== -->
<h2>IPv4 Format Validator</h2>
<div class="ip-section">
  <label>IPv4 Address to Validate</label>
  <input type="text" id="val-ip" placeholder="e.g. 256.1.1.1" maxlength="18" oninput="validateIp()">
  <div id="val-msg"></div>
</div>

<script>
(function(){

/* ── UTILITIES ── */
function isValidIPv4(ip) {
  return /^(\d{1,3}\.){3}\d{1,3}$/.test(ip) &&
    ip.split('.').every(o => parseInt(o, 10) >= 0 && parseInt(o, 10) <= 255);
}
function ipToInt(ip) {
  return ip.split('.').reduce((acc, o) => (acc << 8) | parseInt(o, 10), 0) >>> 0;
}
function intToIp(n) {
  return [(n>>>24)&255,(n>>>16)&255,(n>>>8)&255,n&255].join('.');
}
function intToMask(prefix) {
  return prefix === 0 ? 0 : (0xFFFFFFFF << (32 - prefix)) >>> 0;
}
function msg(el, text, type) {
  el.innerHTML = `<div class="ip-msg ${type}">${text}</div>`;
}

/* ── SECTION 1: BROWSER & CONNECTION INFO ── */
function detectBrowser(ua) {
  if (/Edg\//.test(ua)) return 'Microsoft Edge';
  if (/OPR\/|Opera/.test(ua)) return 'Opera';
  if (/Firefox\//.test(ua)) return 'Firefox';
  if (/Chrome\//.test(ua) && !/Chromium/.test(ua)) return 'Chrome';
  if (/Chromium/.test(ua)) return 'Chromium';
  if (/Safari\//.test(ua) && !/Chrome/.test(ua)) return 'Safari';
  return 'Unknown Browser';
}
function detectOS(ua) {
  if (/Windows NT 10/.test(ua)) return 'Windows 10/11';
  if (/Windows NT/.test(ua)) return 'Windows';
  if (/Mac OS X/.test(ua)) return 'macOS';
  if (/Android/.test(ua)) return 'Android';
  if (/iPhone|iPad/.test(ua)) return 'iOS';
  if (/Linux/.test(ua)) return 'Linux';
  return 'Unknown OS';
}
(function loadInfo() {
  const conn = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
  document.getElementById('conn-type').textContent  = conn ? (conn.type || conn.effectiveType || 'Unknown') : 'Not available';
  document.getElementById('conn-speed').textContent = conn && conn.downlink ? conn.downlink + ' Mbps' : '—';
  document.getElementById('screen-res').textContent = screen.width + ' × ' + screen.height;
  document.getElementById('color-depth').textContent = screen.colorDepth + ' bit';
  document.getElementById('browser-name').textContent = detectBrowser(navigator.userAgent);
  document.getElementById('os-name').textContent = detectOS(navigator.userAgent);
  document.getElementById('lang').textContent = navigator.language || '—';
  document.getElementById('cookies').textContent = navigator.cookieEnabled ? 'Yes' : 'No';
})();

/* ── SECTION 2: WebRTC ── */
(function detectWebRTC() {
  const container = document.getElementById('webrtc-ips');
  const RTCPeer = window.RTCPeerConnection || window.mozRTCPeerConnection || window.webkitRTCPeerConnection;
  if (!RTCPeer) {
    container.innerHTML = '<div class="ip-msg err">WebRTC is not supported in this browser.</div>';
    return;
  }
  const ips = new Set();
  const pc = new RTCPeer({ iceServers: [] });
  pc.createDataChannel('');
  pc.createOffer().then(o => pc.setLocalDescription(o)).catch(() => {});
  const timer = setTimeout(() => { pc.close(); renderIPs(); }, 2500);
  pc.onicecandidate = (e) => {
    if (!e || !e.candidate || !e.candidate.candidate) { clearTimeout(timer); renderIPs(); pc.close(); return; }
    const m = e.candidate.candidate.match(/(\d+\.\d+\.\d+\.\d+)/);
    if (m) ips.add(m[1]);
  };
  function renderIPs() {
    if (ips.size === 0) {
      container.innerHTML = '<div class="ip-msg info">No local IPs detected. Your browser may block WebRTC, or you may be on a VPN.</div>';
    } else {
      let html = '<div style="display:flex;flex-wrap:wrap;gap:0.5rem;">';
      ips.forEach(ip => {
        const priv = isPrivateIP(ip);
        html += `<span class="ip-badge ${priv ? 'green' : 'amber'}">${ip} ${priv ? '(Private)' : '(Public)'}</span>`;
      });
      html += '</div>';
      container.innerHTML = html;
    }
  }
})();

function isPrivateIP(ip) {
  const n = ipToInt(ip);
  return (
    (n >= ipToInt('10.0.0.0')    && n <= ipToInt('10.255.255.255')) ||
    (n >= ipToInt('172.16.0.0')  && n <= ipToInt('172.31.255.255')) ||
    (n >= ipToInt('192.168.0.0') && n <= ipToInt('192.168.255.255')) ||
    (n >= ipToInt('127.0.0.0')   && n <= ipToInt('127.255.255.255'))
  );
}

/* ── SECTION 3: SUBNET CALCULATOR ── */
window.calcSubnet = function() {
  const ipVal   = document.getElementById('sub-ip').value.trim();
  const cidrVal = parseInt(document.getElementById('sub-cidr').value, 10);
  const msgEl   = document.getElementById('sub-msg');
  const tbl     = document.getElementById('sub-table');
  const vis     = document.getElementById('sub-vis');

  if (!isValidIPv4(ipVal)) { msg(msgEl, 'Invalid IPv4 address.', 'err'); tbl.style.display='none'; vis.style.display='none'; return; }
  if (isNaN(cidrVal) || cidrVal < 0 || cidrVal > 32) { msg(msgEl, 'CIDR prefix must be 0–32.', 'err'); tbl.style.display='none'; vis.style.display='none'; return; }
  msgEl.innerHTML = '';

  const maskInt   = intToMask(cidrVal);
  const ipInt     = ipToInt(ipVal);
  const netInt    = (ipInt & maskInt) >>> 0;
  const wildInt   = (~maskInt) >>> 0;
  const bcastInt  = (netInt | wildInt) >>> 0;
  const total     = Math.pow(2, 32 - cidrVal);
  const usable    = total <= 2 ? 0 : total - 2;

  document.getElementById('sub-network').textContent   = intToIp(netInt);
  document.getElementById('sub-mask').textContent      = intToIp(maskInt);
  document.getElementById('sub-broadcast').textContent = intToIp(bcastInt);
  document.getElementById('sub-first').textContent     = usable > 0 ? intToIp(netInt + 1) : 'N/A';
  document.getElementById('sub-last').textContent      = usable > 0 ? intToIp(bcastInt - 1) : 'N/A';
  document.getElementById('sub-hosts').textContent     = usable.toLocaleString();
  document.getElementById('sub-total').textContent     = total.toLocaleString();
  document.getElementById('sub-wild').textContent      = intToIp(wildInt);

  tbl.style.display = '';
  vis.style.display = '';
  const pct = Math.max(4, (cidrVal / 32) * 100);
  document.getElementById('sub-bar').style.width = pct + '%';
  document.getElementById('sub-bar-label').textContent = usable.toLocaleString() + ' usable hosts';
};

/* ── SECTION 4: IP CLASS & RANGE CHECKER ── */
window.checkClass = function() {
  const ipVal = document.getElementById('cls-ip').value.trim();
  const el    = document.getElementById('cls-result');
  if (!isValidIPv4(ipVal)) { msg(el, 'Invalid IPv4 address.', 'err'); return; }

  const first = parseInt(ipVal.split('.')[0], 10);
  let cls = '', range = '', purpose = '';
  if (first >= 1 && first <= 126)       { cls = 'A'; range = '1.0.0.0 – 126.255.255.255'; purpose = 'Large networks (default mask /8)'; }
  else if (first === 127)               { cls = 'Loopback'; range = '127.0.0.0 – 127.255.255.255'; purpose = 'Loopback / localhost'; }
  else if (first >= 128 && first <= 191){ cls = 'B'; range = '128.0.0.0 – 191.255.255.255'; purpose = 'Medium networks (default mask /16)'; }
  else if (first >= 192 && first <= 223){ cls = 'C'; range = '192.0.0.0 – 223.255.255.255'; purpose = 'Small networks (default mask /24)'; }
  else if (first >= 224 && first <= 239){ cls = 'D'; range = '224.0.0.0 – 239.255.255.255'; purpose = 'Multicast'; }
  else if (first >= 240 && first <= 255){ cls = 'E'; range = '240.0.0.0 – 255.255.255.255'; purpose = 'Reserved / Experimental'; }
  else                                  { cls = 'Unknown'; range = '—'; purpose = '—'; }

  const priv = isPrivateIP(ipVal);
  const privBadge = priv
    ? '<span class="ip-badge green">Private</span>'
    : '<span class="ip-badge amber">Public / Routable</span>';

  el.innerHTML = `
    <table class="ip-result-table" style="margin-top:0.8rem">
      <tbody>
        <tr><td>IP Class</td><td><strong>Class ${cls}</strong></td></tr>
        <tr><td>Class Range</td><td>${range}</td></tr>
        <tr><td>Typical Use</td><td>${purpose}</td></tr>
        <tr><td>Scope</td><td>${privBadge}</td></tr>
      </tbody>
    </table>`;
};

/* ── SECTION 5: IPv4 ↔ DECIMAL ── */
window.ipToDecimal = function() {
  const ipVal = document.getElementById('conv-ipv4').value.trim();
  const msgEl = document.getElementById('conv-msg');
  const tbl   = document.getElementById('conv-table');
  if (!isValidIPv4(ipVal)) { msg(msgEl, 'Invalid IPv4 address.', 'err'); tbl.style.display='none'; return; }
  msgEl.innerHTML = '';
  const n = ipToInt(ipVal);
  showConv(ipVal, n, tbl);
  document.getElementById('conv-dec').value = n;
};

window.decimalToIp = function() {
  const decVal = document.getElementById('conv-dec').value.trim();
  const msgEl  = document.getElementById('conv-msg');
  const tbl    = document.getElementById('conv-table');
  const n      = parseInt(decVal, 10);
  if (isNaN(n) || n < 0 || n > 4294967295) { msg(msgEl, 'Decimal must be 0 – 4,294,967,295.', 'err'); tbl.style.display='none'; return; }
  msgEl.innerHTML = '';
  const ip = intToIp(n);
  showConv(ip, n, tbl);
  document.getElementById('conv-ipv4').value = ip;
};

function showConv(ip, n, tbl) {
  document.getElementById('conv-r-ipv4').textContent = ip;
  document.getElementById('conv-r-dec').textContent  = n.toLocaleString();
  document.getElementById('conv-r-bin').textContent  = ip.split('.').map(o => parseInt(o,10).toString(2).padStart(8,'0')).join('.');
  document.getElementById('conv-r-hex').textContent  = '0x' + n.toString(16).toUpperCase().padStart(8,'0');
  tbl.style.display = '';
}

/* ── SECTION 6: VALIDATOR ── */
window.validateIp = function() {
  const ipVal = document.getElementById('val-ip').value.trim();
  const el    = document.getElementById('val-msg');
  if (!ipVal) { el.innerHTML = ''; return; }
  if (isValidIPv4(ipVal)) {
    const priv = isPrivateIP(ipVal);
    msg(el, `Valid IPv4 address. ${priv ? 'This is a private (RFC 1918) address.' : 'This is a public/routable address.'}`, 'ok');
  } else {
    const parts = ipVal.split('.');
    let hint = '';
    if (parts.length !== 4) hint = ' (needs exactly 4 octets separated by dots)';
    else if (parts.some(p => isNaN(parseInt(p,10)) || parseInt(p,10) < 0 || parseInt(p,10) > 255))
      hint = ' (each octet must be 0–255)';
    msg(el, 'Invalid IPv4 address' + hint + '.', 'err');
  }
};

})();
</script>

</div>

---

Related: Check your display details → [Screen Resolution Checker](/tools/screen-resolution/)
