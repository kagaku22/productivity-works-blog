---
title: "IPアドレス情報ツール — サブネット計算・IPv4変換・ネットワーク診断"
date: 2025-05-16
description: "無料IPアドレスツール：サブネット計算（CIDR）・IPv4/10進数変換・プライベート/パブリック判定・IPクラス識別・WebRTCローカルIP検出・接続情報表示。インストール不要。"
categories: ["無料ツール"]
slug: "ip-address-info"
tags: ["IPアドレス", "サブネット計算", "CIDR", "IPv4変換", "ネットワークツール", "WebRTC", "プライベートIP"]
cover:
  image: "/images/covers/ip-address-info-ja.png"
  alt: "IPアドレス情報ツール"
ShowToc: false
aliases:
  - "/ja/tools/my-ip/"
  - "/ja/tools/ip-lookup/"
---

ローカルネットワーク情報の検出・サブネット計算・IPv4の10進数変換・IPクラス判定・アドレス検証をブラウザ上で完結。外部へのリクエスト不要です。

<div id="ip-app">

<style>
#ip-app {
  font-family: system-ui, -apple-system, "Hiragino Kaku Gothic ProN", "Noto Sans JP", sans-serif;
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
#ip-app input[type="number"]:focus {
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
#ip-app .ip-msg.ok   { background: #14532d44; color: #86efac; border: 1px solid #14532d; }
#ip-app .ip-msg.err  { background: #450a0a44; color: #fca5a5; border: 1px solid #450a0a; }
#ip-app .ip-msg.info { background: #1e3a5f44; color: #93c5fd; border: 1px solid #1e3a5f; }

#ip-app .webrtc-note {
  font-size: 0.78rem;
  color: #475569;
  margin-top: 0.4rem;
  line-height: 1.6;
}

#ip-app .subnet-vis {
  margin-top: 0.9rem;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  padding: 0.75rem 1rem;
}
#ip-app .subnet-vis .sv-bar-wrap {
  background: #334155;
  border-radius: 4px;
  height: 18px;
  margin: 0.4rem 0;
  overflow: hidden;
}
#ip-app .subnet-vis .sv-bar {
  height: 18px;
  border-radius: 4px;
  background: linear-gradient(90deg, #22c55e 0%, #16a34a 100%);
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

/* freee CTA */
#ip-app .freee-cta {
  background: linear-gradient(135deg, #1e293b 0%, #0f2027 100%);
  border: 1px solid #22c55e44;
  border-radius: 12px;
  padding: 1.2rem 1.4rem;
  margin-top: 1.8rem;
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  flex-wrap: wrap;
}
#ip-app .freee-cta .fc-icon {
  font-size: 2rem;
  line-height: 1;
  flex-shrink: 0;
}
#ip-app .freee-cta .fc-body { flex: 1; min-width: 200px; }
#ip-app .freee-cta .fc-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: #e2e8f0;
  margin-bottom: 0.3rem;
}
#ip-app .freee-cta .fc-desc {
  font-size: 0.8rem;
  color: #94a3b8;
  line-height: 1.5;
  margin-bottom: 0.7rem;
}
#ip-app .freee-cta a {
  display: inline-block;
  background: #22c55e;
  color: #0f172a;
  font-size: 0.85rem;
  font-weight: 700;
  padding: 0.45rem 1.1rem;
  border-radius: 7px;
  text-decoration: none;
  transition: background 0.15s;
}
#ip-app .freee-cta a:hover { background: #16a34a; }

@media (max-width: 520px) {
  #ip-app { padding: 1rem; }
  #ip-app .ip-row { flex-direction: column; }
}
</style>

<!-- ===== SECTION 1: ブラウザ・接続情報 ===== -->
<h2>接続・ブラウザ情報</h2>
<div class="ip-grid" id="info-grid">
  <div class="ip-card"><div class="ip-label">接続タイプ</div><div class="ip-value" id="conn-type">検出中…</div></div>
  <div class="ip-card"><div class="ip-label">実効速度</div><div class="ip-value" id="conn-speed">—</div></div>
  <div class="ip-card"><div class="ip-label">画面解像度</div><div class="ip-value" id="screen-res">—</div></div>
  <div class="ip-card"><div class="ip-label">色深度</div><div class="ip-value" id="color-depth">—</div></div>
  <div class="ip-card"><div class="ip-label">ブラウザ</div><div class="ip-value muted" id="browser-name">—</div></div>
  <div class="ip-card"><div class="ip-label">OS / プラットフォーム</div><div class="ip-value muted" id="os-name">—</div></div>
  <div class="ip-card"><div class="ip-label">言語設定</div><div class="ip-value" id="lang">—</div></div>
  <div class="ip-card"><div class="ip-label">Cookie 有効</div><div class="ip-value" id="cookies">—</div></div>
</div>

<!-- ===== SECTION 2: WebRTC ローカルIP ===== -->
<h2>ローカルIP検出（WebRTC）</h2>
<div class="ip-section">
  <div id="webrtc-ips"><span style="color:#64748b;font-size:0.9rem;">WebRTC でローカルIPを検出しています…</span></div>
  <p class="webrtc-note">WebRTC を使用して、ルーターが割り当てたローカル（LAN）IPアドレスを取得します。外部サーバーへのアクセスは不要で、ほとんどのモダンブラウザで動作します。VPN使用時やファイアウォール環境では検出されない場合があります。</p>
</div>

<!-- ===== SECTION 3: サブネット計算 ===== -->
<h2>サブネット計算（CIDR）</h2>
<div class="ip-section">
  <div class="ip-row">
    <div>
      <label>IPv4 アドレス</label>
      <input type="text" id="sub-ip" placeholder="例: 192.168.1.50" maxlength="18">
    </div>
    <div>
      <label>プレフィックス長（CIDR）</label>
      <input type="number" id="sub-cidr" placeholder="例: 24" min="0" max="32" value="24">
    </div>
  </div>
  <button onclick="calcSubnet()">サブネットを計算</button>
  <div id="sub-msg"></div>
  <table class="ip-result-table" id="sub-table" style="display:none">
    <tbody>
      <tr><td>ネットワークアドレス</td><td id="sub-network">—</td></tr>
      <tr><td>サブネットマスク</td><td id="sub-mask">—</td></tr>
      <tr><td>ブロードキャストアドレス</td><td id="sub-broadcast">—</td></tr>
      <tr><td>最初のホストアドレス</td><td id="sub-first">—</td></tr>
      <tr><td>最後のホストアドレス</td><td id="sub-last">—</td></tr>
      <tr><td>使用可能ホスト数</td><td id="sub-hosts">—</td></tr>
      <tr><td>総アドレス数</td><td id="sub-total">—</td></tr>
      <tr><td>ワイルドカードマスク</td><td id="sub-wild">—</td></tr>
    </tbody>
  </table>
  <div id="sub-vis" class="subnet-vis" style="display:none">
    <div class="sv-label">使用可能ホスト容量</div>
    <div class="sv-bar-wrap"><div class="sv-bar" id="sub-bar" style="width:4%"></div></div>
    <div class="sv-count" id="sub-bar-label"></div>
  </div>
</div>

<!-- ===== SECTION 4: IPクラス・範囲判定 ===== -->
<h2>IPクラス・範囲判定</h2>
<div class="ip-section">
  <label>IPv4 アドレス</label>
  <input type="text" id="cls-ip" placeholder="例: 10.0.0.1" maxlength="18">
  <button onclick="checkClass()">IPクラスを判定</button>
  <div id="cls-result"></div>
</div>

<!-- ===== SECTION 5: IPv4 ↔ 10進数変換 ===== -->
<h2>IPv4 ↔ 10進数（32bit）変換</h2>
<div class="ip-section">
  <div class="ip-row">
    <div>
      <label>IPv4 アドレス</label>
      <input type="text" id="conv-ipv4" placeholder="例: 192.168.1.1" maxlength="18">
    </div>
    <div>
      <label>10進数（32ビット）</label>
      <input type="text" id="conv-dec" placeholder="例: 3232235777">
    </div>
  </div>
  <div class="ip-row">
    <button onclick="ipToDecimal()">IPv4 → 10進数</button>
    <button onclick="decimalToIp()">10進数 → IPv4</button>
  </div>
  <div id="conv-msg"></div>
  <table class="ip-result-table" id="conv-table" style="display:none">
    <tbody>
      <tr><td>IPv4 アドレス</td><td id="conv-r-ipv4">—</td></tr>
      <tr><td>10進数</td><td id="conv-r-dec">—</td></tr>
      <tr><td>2進数（バイナリ）</td><td id="conv-r-bin">—</td></tr>
      <tr><td>16進数（Hex）</td><td id="conv-r-hex">—</td></tr>
    </tbody>
  </table>
</div>

<!-- ===== SECTION 6: IPv4 バリデーター ===== -->
<h2>IPv4 アドレス形式チェック</h2>
<div class="ip-section">
  <label>確認したい IPv4 アドレス</label>
  <input type="text" id="val-ip" placeholder="例: 256.1.1.1" maxlength="18" oninput="validateIp()">
  <div id="val-msg"></div>
</div>

<!-- ===== freee CTA ===== -->
<div class="freee-cta">
  <div class="fc-icon">💼</div>
  <div class="fc-body">
    <div class="fc-title">freee 会計 — 個人事業主・フリーランスの帳簿をAIで自動化</div>
    <div class="fc-desc">銀行・クレカ明細を自動取込。確定申告書類をワンクリック作成。ITエンジニア・フリーランスに選ばれるクラウド会計ソフト。</div>
    <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener sponsored">freee を無料で試す</a>
  </div>
</div>

<script>
(function(){

/* ── ユーティリティ ── */
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

/* ── ブラウザ・接続情報 ── */
function detectBrowser(ua) {
  if (/Edg\//.test(ua)) return 'Microsoft Edge';
  if (/OPR\/|Opera/.test(ua)) return 'Opera';
  if (/Firefox\//.test(ua)) return 'Firefox';
  if (/Chrome\//.test(ua) && !/Chromium/.test(ua)) return 'Chrome';
  if (/Chromium/.test(ua)) return 'Chromium';
  if (/Safari\//.test(ua) && !/Chrome/.test(ua)) return 'Safari';
  return '不明なブラウザ';
}
function detectOS(ua) {
  if (/Windows NT 10/.test(ua)) return 'Windows 10/11';
  if (/Windows NT/.test(ua)) return 'Windows';
  if (/Mac OS X/.test(ua)) return 'macOS';
  if (/Android/.test(ua)) return 'Android';
  if (/iPhone|iPad/.test(ua)) return 'iOS';
  if (/Linux/.test(ua)) return 'Linux';
  return '不明なOS';
}
(function loadInfo() {
  const conn = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
  document.getElementById('conn-type').textContent  = conn ? (conn.type || conn.effectiveType || '不明') : '取得不可';
  document.getElementById('conn-speed').textContent = conn && conn.downlink ? conn.downlink + ' Mbps' : '—';
  document.getElementById('screen-res').textContent = screen.width + ' × ' + screen.height;
  document.getElementById('color-depth').textContent = screen.colorDepth + ' ビット';
  document.getElementById('browser-name').textContent = detectBrowser(navigator.userAgent);
  document.getElementById('os-name').textContent = detectOS(navigator.userAgent);
  document.getElementById('lang').textContent = navigator.language || '—';
  document.getElementById('cookies').textContent = navigator.cookieEnabled ? '有効' : '無効';
})();

/* ── WebRTC ローカルIP ── */
(function detectWebRTC() {
  const container = document.getElementById('webrtc-ips');
  const RTCPeer = window.RTCPeerConnection || window.mozRTCPeerConnection || window.webkitRTCPeerConnection;
  if (!RTCPeer) {
    container.innerHTML = '<div class="ip-msg err">このブラウザは WebRTC に対応していません。</div>';
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
      container.innerHTML = '<div class="ip-msg info">ローカルIPが検出されませんでした。VPN接続中またはブラウザの設定によりブロックされている可能性があります。</div>';
    } else {
      let html = '<div style="display:flex;flex-wrap:wrap;gap:0.5rem;">';
      ips.forEach(ip => {
        const priv = isPrivateIP(ip);
        html += `<span class="ip-badge ${priv ? 'green' : 'amber'}">${ip} ${priv ? '（プライベート）' : '（パブリック）'}</span>`;
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

/* ── サブネット計算 ── */
window.calcSubnet = function() {
  const ipVal   = document.getElementById('sub-ip').value.trim();
  const cidrVal = parseInt(document.getElementById('sub-cidr').value, 10);
  const msgEl   = document.getElementById('sub-msg');
  const tbl     = document.getElementById('sub-table');
  const vis     = document.getElementById('sub-vis');

  if (!isValidIPv4(ipVal)) { msg(msgEl, '有効なIPv4アドレスを入力してください。', 'err'); tbl.style.display='none'; vis.style.display='none'; return; }
  if (isNaN(cidrVal) || cidrVal < 0 || cidrVal > 32) { msg(msgEl, 'プレフィックス長は 0〜32 の整数で入力してください。', 'err'); tbl.style.display='none'; vis.style.display='none'; return; }
  msgEl.innerHTML = '';

  const maskInt  = intToMask(cidrVal);
  const ipInt    = ipToInt(ipVal);
  const netInt   = (ipInt & maskInt) >>> 0;
  const wildInt  = (~maskInt) >>> 0;
  const bcastInt = (netInt | wildInt) >>> 0;
  const total    = Math.pow(2, 32 - cidrVal);
  const usable   = total <= 2 ? 0 : total - 2;

  document.getElementById('sub-network').textContent   = intToIp(netInt);
  document.getElementById('sub-mask').textContent      = intToIp(maskInt);
  document.getElementById('sub-broadcast').textContent = intToIp(bcastInt);
  document.getElementById('sub-first').textContent     = usable > 0 ? intToIp(netInt + 1) : 'なし';
  document.getElementById('sub-last').textContent      = usable > 0 ? intToIp(bcastInt - 1) : 'なし';
  document.getElementById('sub-hosts').textContent     = usable.toLocaleString('ja-JP') + ' 台';
  document.getElementById('sub-total').textContent     = total.toLocaleString('ja-JP') + ' アドレス';
  document.getElementById('sub-wild').textContent      = intToIp(wildInt);

  tbl.style.display = '';
  vis.style.display = '';
  const pct = Math.max(4, (cidrVal / 32) * 100);
  document.getElementById('sub-bar').style.width = pct + '%';
  document.getElementById('sub-bar-label').textContent = '使用可能: ' + usable.toLocaleString('ja-JP') + ' ホスト';
};

/* ── IPクラス・範囲判定 ── */
window.checkClass = function() {
  const ipVal = document.getElementById('cls-ip').value.trim();
  const el    = document.getElementById('cls-result');
  if (!isValidIPv4(ipVal)) { msg(el, '有効なIPv4アドレスを入力してください。', 'err'); return; }

  const first = parseInt(ipVal.split('.')[0], 10);
  let cls = '', range = '', purpose = '';
  if (first >= 1 && first <= 126)        { cls = 'A'; range = '1.0.0.0 – 126.255.255.255'; purpose = '大規模ネットワーク（デフォルトマスク /8）'; }
  else if (first === 127)                { cls = 'ループバック'; range = '127.0.0.0 – 127.255.255.255'; purpose = 'ループバック / localhost'; }
  else if (first >= 128 && first <= 191) { cls = 'B'; range = '128.0.0.0 – 191.255.255.255'; purpose = '中規模ネットワーク（デフォルトマスク /16）'; }
  else if (first >= 192 && first <= 223) { cls = 'C'; range = '192.0.0.0 – 223.255.255.255'; purpose = '小規模ネットワーク（デフォルトマスク /24）'; }
  else if (first >= 224 && first <= 239) { cls = 'D'; range = '224.0.0.0 – 239.255.255.255'; purpose = 'マルチキャスト'; }
  else if (first >= 240 && first <= 255) { cls = 'E'; range = '240.0.0.0 – 255.255.255.255'; purpose = '予約済み / 実験的'; }
  else                                   { cls = '不明'; range = '—'; purpose = '—'; }

  const priv = isPrivateIP(ipVal);
  const privBadge = priv
    ? '<span class="ip-badge green">プライベート（RFC 1918）</span>'
    : '<span class="ip-badge amber">パブリック / グローバル</span>';

  el.innerHTML = `
    <table class="ip-result-table" style="margin-top:0.8rem">
      <tbody>
        <tr><td>IPクラス</td><td><strong>クラス ${cls}</strong></td></tr>
        <tr><td>クラス範囲</td><td>${range}</td></tr>
        <tr><td>主な用途</td><td>${purpose}</td></tr>
        <tr><td>スコープ</td><td>${privBadge}</td></tr>
      </tbody>
    </table>`;
};

/* ── IPv4 ↔ 10進数変換 ── */
window.ipToDecimal = function() {
  const ipVal = document.getElementById('conv-ipv4').value.trim();
  const msgEl = document.getElementById('conv-msg');
  const tbl   = document.getElementById('conv-table');
  if (!isValidIPv4(ipVal)) { msg(msgEl, '有効なIPv4アドレスを入力してください。', 'err'); tbl.style.display='none'; return; }
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
  if (isNaN(n) || n < 0 || n > 4294967295) { msg(msgEl, '10進数は 0 〜 4,294,967,295 の範囲で入力してください。', 'err'); tbl.style.display='none'; return; }
  msgEl.innerHTML = '';
  const ip = intToIp(n);
  showConv(ip, n, tbl);
  document.getElementById('conv-ipv4').value = ip;
};

function showConv(ip, n, tbl) {
  document.getElementById('conv-r-ipv4').textContent = ip;
  document.getElementById('conv-r-dec').textContent  = n.toLocaleString('ja-JP');
  document.getElementById('conv-r-bin').textContent  = ip.split('.').map(o => parseInt(o,10).toString(2).padStart(8,'0')).join('.');
  document.getElementById('conv-r-hex').textContent  = '0x' + n.toString(16).toUpperCase().padStart(8,'0');
  tbl.style.display = '';
}

/* ── IPv4 バリデーター ── */
window.validateIp = function() {
  const ipVal = document.getElementById('val-ip').value.trim();
  const el    = document.getElementById('val-msg');
  if (!ipVal) { el.innerHTML = ''; return; }
  if (isValidIPv4(ipVal)) {
    const priv = isPrivateIP(ipVal);
    msg(el, `有効な IPv4 アドレスです。${priv ? 'このアドレスはプライベート（RFC 1918）アドレスです。' : 'このアドレスはパブリック（グローバルルーティング可能）アドレスです。'}`, 'ok');
  } else {
    const parts = ipVal.split('.');
    let hint = '';
    if (parts.length !== 4) hint = '（ドット区切りで4つのオクテットが必要です）';
    else if (parts.some(p => isNaN(parseInt(p,10)) || parseInt(p,10) < 0 || parseInt(p,10) > 255))
      hint = '（各オクテットは 0〜255 の整数である必要があります）';
    msg(el, '無効な IPv4 アドレスです' + hint + '。', 'err');
  }
};

})();
</script>

</div>
