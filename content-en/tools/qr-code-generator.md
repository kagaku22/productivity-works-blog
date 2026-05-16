---
title: "QR Code Generator - Free Online Tool"
date: 2025-05-16
description: "Generate QR codes instantly for URLs, text, email, phone, and WiFi. Free online QR code maker with custom colors and PNG download. No sign-up required."
categories: ["Free Tools"]
tags: ["QR code", "QR generator", "QR maker", "URL QR code", "WiFi QR code", "free tool"]
slug: "qr-code-generator"
aliases: ["/tools/qr-generator/", "/tools/qr-maker/"]
cover:
  image: "/images/covers/qr-code-generator.png"
  alt: "QR Code Generator"
ShowToc: false
---

<div id="qr-app">

<style>
#qr-app {
  font-family: ui-sans-serif, system-ui, -apple-system, sans-serif;
  color: #e2e8f0;
  max-width: 860px;
  margin: 0 auto;
  padding: 0;
}
#qr-app * { box-sizing: border-box; }

.qr-header {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
  border: 1px solid #1e3a5f;
  border-radius: 16px;
  padding: 28px 32px 24px;
  margin-bottom: 20px;
  text-align: center;
}
.qr-header h2 {
  margin: 0 0 6px;
  font-size: 1.6rem;
  font-weight: 700;
  color: #f1f5f9;
}
.qr-header p {
  margin: 0;
  color: #94a3b8;
  font-size: 0.95rem;
}

.qr-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 20px;
}
.qr-preset-btn {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #cbd5e1;
  cursor: pointer;
  font-size: 13px;
  padding: 7px 14px;
  transition: background 0.15s, border-color 0.15s, color 0.15s;
  display: flex;
  align-items: center;
  gap: 6px;
}
.qr-preset-btn:hover, .qr-preset-btn.active {
  background: #3b82f6;
  border-color: #3b82f6;
  color: #fff;
}

.qr-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 24px;
  margin-bottom: 16px;
}
.qr-label {
  font-size: 13px;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 10px;
}
.qr-input {
  width: 100%;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #f1f5f9;
  font-size: 15px;
  padding: 12px 14px;
  outline: none;
  transition: border-color 0.15s;
  resize: vertical;
}
.qr-input:focus { border-color: #3b82f6; }
.qr-input::placeholder { color: #475569; }

.qr-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin-bottom: 16px;
}
@media (max-width: 540px) {
  .qr-row { grid-template-columns: 1fr; }
}

.qr-select {
  width: 100%;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 8px;
  color: #f1f5f9;
  font-size: 14px;
  padding: 10px 12px;
  outline: none;
  cursor: pointer;
}
.qr-select:focus { border-color: #3b82f6; }

.qr-color-row {
  display: flex;
  align-items: center;
  gap: 10px;
}
.qr-color-input {
  width: 42px;
  height: 38px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  padding: 2px;
  background: #0f172a;
}
.qr-color-hex {
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 6px;
  color: #f1f5f9;
  font-size: 13px;
  padding: 8px 10px;
  width: 100px;
  outline: none;
  font-family: monospace;
}
.qr-color-hex:focus { border-color: #3b82f6; }

.qr-canvas-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  background: #0f172a;
  border-radius: 12px;
  padding: 28px;
  margin-bottom: 16px;
  min-height: 260px;
  border: 1px solid #1e3a5f;
}
#qr-canvas {
  image-rendering: pixelated;
  border-radius: 4px;
  max-width: 100%;
}

.qr-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.qr-btn {
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
  font-weight: 600;
  padding: 11px 22px;
  transition: opacity 0.15s, transform 0.1s;
  display: flex;
  align-items: center;
  gap: 7px;
}
.qr-btn:active { transform: scale(0.97); }
.qr-btn-primary {
  background: #3b82f6;
  color: #fff;
}
.qr-btn-primary:hover { background: #2563eb; }
.qr-btn-secondary {
  background: #1e293b;
  border: 1px solid #334155;
  color: #cbd5e1;
}
.qr-btn-secondary:hover { background: #334155; }
.qr-btn-success {
  background: #10b981;
  color: #fff;
}
.qr-btn-success:hover { background: #059669; }

.qr-status {
  font-size: 13px;
  color: #64748b;
  margin-top: 12px;
  min-height: 20px;
  transition: color 0.2s;
}
.qr-status.ok { color: #10b981; }
.qr-status.err { color: #ef4444; }

.qr-char-count {
  font-size: 12px;
  color: #64748b;
  text-align: right;
  margin-top: 6px;
}
.qr-char-count.warn { color: #f59e0b; }
.qr-char-count.bad { color: #ef4444; }

.qr-wifi-fields { display: none; }
.qr-wifi-fields.show { display: block; }
.qr-wifi-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-top: 12px;
}
@media (max-width: 540px) { .qr-wifi-row { grid-template-columns: 1fr; } }

.qr-tip {
  background: #0f172a;
  border-left: 3px solid #3b82f6;
  border-radius: 0 8px 8px 0;
  padding: 12px 16px;
  font-size: 13px;
  color: #94a3b8;
  margin-top: 20px;
  line-height: 1.6;
}
.qr-tip strong { color: #e2e8f0; }
</style>

<div class="qr-header">
  <h2>QR Code Generator</h2>
  <p>Create QR codes for URLs, text, email, phone, and WiFi — free, instant, no sign-up</p>
</div>

<div class="qr-presets">
  <button class="qr-preset-btn active" data-preset="url" onclick="qrSetPreset('url',this)">&#127760; URL</button>
  <button class="qr-preset-btn" data-preset="text" onclick="qrSetPreset('text',this)">&#128196; Text</button>
  <button class="qr-preset-btn" data-preset="email" onclick="qrSetPreset('email',this)">&#9993; Email</button>
  <button class="qr-preset-btn" data-preset="phone" onclick="qrSetPreset('phone',this)">&#128222; Phone</button>
  <button class="qr-preset-btn" data-preset="wifi" onclick="qrSetPreset('wifi',this)">&#128246; WiFi</button>
</div>

<div class="qr-card">
  <div class="qr-label">Content</div>
  <textarea id="qr-text" class="qr-input" rows="3" placeholder="Enter URL or text…" oninput="qrOnInput()">https://productivity.works</textarea>
  <div class="qr-char-count" id="qr-char-count">27 / 500 characters</div>

  <div class="qr-wifi-fields" id="qr-wifi-fields">
    <div class="qr-wifi-row">
      <div>
        <div class="qr-label" style="margin-top:12px">Network Name (SSID)</div>
        <input type="text" id="qr-wifi-ssid" class="qr-input" placeholder="MyNetwork" oninput="qrBuildWifi()">
      </div>
      <div>
        <div class="qr-label" style="margin-top:12px">Password</div>
        <input type="text" id="qr-wifi-pass" class="qr-input" placeholder="password123" oninput="qrBuildWifi()">
      </div>
    </div>
    <div style="margin-top:10px">
      <div class="qr-label">Security</div>
      <select id="qr-wifi-sec" class="qr-select" onchange="qrBuildWifi()">
        <option value="WPA">WPA/WPA2</option>
        <option value="WEP">WEP</option>
        <option value="nopass">None</option>
      </select>
    </div>
  </div>
</div>

<div class="qr-row">
  <div class="qr-card" style="margin-bottom:0">
    <div class="qr-label">Size</div>
    <select id="qr-size" class="qr-select" onchange="qrRender()">
      <option value="200">Small (200px)</option>
      <option value="300" selected>Medium (300px)</option>
      <option value="400">Large (400px)</option>
    </select>
  </div>
  <div class="qr-card" style="margin-bottom:0">
    <div class="qr-label">Error Correction</div>
    <select id="qr-ecl" class="qr-select" onchange="qrRender()">
      <option value="L">L — 7% recovery</option>
      <option value="M" selected>M — 15% recovery</option>
      <option value="Q">Q — 25% recovery</option>
      <option value="H">H — 30% recovery</option>
    </select>
  </div>
</div>

<div class="qr-row" style="margin-top:16px">
  <div class="qr-card" style="margin-bottom:0">
    <div class="qr-label">Foreground Color</div>
    <div class="qr-color-row">
      <input type="color" id="qr-fg-color" class="qr-color-input" value="#1a1a2e" oninput="qrSyncColor('fg')">
      <input type="text" id="qr-fg-hex" class="qr-color-hex" value="#1a1a2e" oninput="qrHexChange('fg')" maxlength="7">
    </div>
  </div>
  <div class="qr-card" style="margin-bottom:0">
    <div class="qr-label">Background Color</div>
    <div class="qr-color-row">
      <input type="color" id="qr-bg-color" class="qr-color-input" value="#ffffff" oninput="qrSyncColor('bg')">
      <input type="text" id="qr-bg-hex" class="qr-color-hex" value="#ffffff" oninput="qrHexChange('bg')" maxlength="7">
    </div>
  </div>
</div>

<div class="qr-canvas-wrap">
  <canvas id="qr-canvas" width="300" height="300"></canvas>
</div>

<div class="qr-actions">
  <button class="qr-btn qr-btn-primary" onclick="qrDownload()">&#8615; Download PNG</button>
  <button class="qr-btn qr-btn-success" onclick="qrCopyClipboard()">&#128203; Copy to Clipboard</button>
  <button class="qr-btn qr-btn-secondary" onclick="qrReset()">&#10006; Reset</button>
</div>
<div class="qr-status" id="qr-status"></div>

<div class="qr-tip">
  <strong>Tips:</strong> Use <strong>Error Correction H</strong> if you plan to add a logo over the QR code.
  For URLs, keep them short for best scan reliability. QR codes are generated entirely in your browser — no data is sent to any server.
</div>

</div><!-- #qr-app -->

---

Related: Encode data with our [Base64 Encoder](/tools/base64-encoder/)

<script>
(function(){
'use strict';

/* ============================================================
   Minimal QR Code encoder — pure vanilla JS
   Supports: Byte mode, EC levels L/M/Q/H, versions 1–10
   ============================================================ */

// ---- GF(256) arithmetic ----
const GF_EXP = new Uint8Array(512);
const GF_LOG = new Uint8Array(256);
(function initGF(){
  let x = 1;
  for(let i=0;i<255;i++){
    GF_EXP[i] = x;
    GF_LOG[x] = i;
    x = x << 1;
    if(x & 0x100) x ^= 0x11d;
  }
  for(let i=255;i<512;i++) GF_EXP[i] = GF_EXP[i-255];
})();

function gfMul(a,b){
  if(a===0||b===0) return 0;
  return GF_EXP[(GF_LOG[a]+GF_LOG[b])%255];
}
function gfPow(x,p){ return GF_EXP[(GF_LOG[x]*p)%255]; }

function rsGeneratorPoly(nsym){
  let g=[1];
  for(let i=0;i<nsym;i++){
    const factor=[1, gfPow(2,i)];
    const ng=new Array(g.length+factor.length-1).fill(0);
    for(let j=0;j<g.length;j++)
      for(let k=0;k<factor.length;k++)
        ng[j+k]^=gfMul(g[j],factor[k]);
    g=ng;
  }
  return g;
}

function rsEncode(data, nsym){
  const gen=rsGeneratorPoly(nsym);
  const msg=data.concat(new Array(nsym).fill(0));
  for(let i=0;i<data.length;i++){
    const coef=msg[i];
    if(coef!==0)
      for(let j=0;j<gen.length;j++)
        msg[i+j]^=gfMul(gen[j],coef);
  }
  return msg.slice(data.length);
}

// ---- QR version / capacity tables ----
// [version] => { totalBytes, ecBlocks: [{count, dataBytes}], ecPerBlock }
// EC level index: 0=L,1=M,2=Q,3=H
const QR_EC = {
  L:0, M:1, Q:2, H:3
};

// Simplified capacity & EC table for versions 1-10
// Format: [dcw, ecPerBlock, [b1count, b1data, b2count, b2data]]
const QR_TABLE = [
//ver  L:[dcw,ecPB,[g1c,g1d,g2c,g2d]]  M:...  Q:...  H:...
  null,
  { L:[19,7,[1,19,0,0]],  M:[16,10,[1,16,0,0]],  Q:[13,13,[1,13,0,0]],  H:[9,17,[1,9,0,0]]  }, // v1
  { L:[34,10,[1,34,0,0]], M:[28,16,[1,28,0,0]],  Q:[22,22,[1,22,0,0]],  H:[16,28,[1,16,0,0]] }, // v2
  { L:[55,15,[1,55,0,0]], M:[44,26,[1,44,0,0]],  Q:[34,18,[2,17,0,0]],  H:[26,22,[2,13,0,0]] }, // v3
  { L:[80,20,[1,80,0,0]], M:[64,18,[2,32,0,0]],  Q:[48,26,[2,24,0,0]],  H:[36,16,[4,9,0,0]]  }, // v4
  { L:[108,26,[1,108,0,0]],M:[86,24,[2,43,0,0]], Q:[62,18,[2,15,2,16]], H:[46,22,[2,11,2,12]]}, // v5
  { L:[136,18,[2,68,0,0]], M:[108,16,[4,27,0,0]],Q:[76,24,[4,19,0,0]],  H:[60,28,[4,15,0,0]] }, // v6
  { L:[156,20,[2,78,0,0]], M:[124,18,[4,31,0,0]],Q:[88,18,[2,14,4,15]], H:[66,26,[4,13,1,14]]}, // v7
  { L:[194,24,[2,97,0,0]], M:[154,22,[2,38,2,39]],Q:[110,22,[4,18,2,19]],H:[86,26,[4,14,2,15]]},// v8
  { L:[232,30,[2,116,0,0]],M:[182,22,[3,36,2,37]],Q:[132,20,[4,16,4,17]],H:[100,24,[4,12,4,13]]},//v9
  { L:[274,18,[2,68,2,69]],M:[216,26,[4,43,1,44]],Q:[154,24,[6,19,2,20]],H:[122,28,[6,15,2,16]]},//v10
];

// Max data bytes per version per EC level
function getMaxBytes(ver, ecl){
  const t=QR_TABLE[ver][ecl];
  return t[0];
}

function chooseVersion(byteLen, ecl){
  for(let v=1;v<=10;v++){
    const max=getMaxBytes(v,ecl);
    // byte mode overhead: 4 bits mode + 8 bits length = 12 bits + 4 terminator = 2 bytes overhead
    if(byteLen+2 <= max) return v;
  }
  return null;
}

// ---- Encode data codewords ----
function encodeData(text, ver, ecl){
  const bytes=[];
  for(let i=0;i<text.length;i++){
    const c=text.charCodeAt(i);
    if(c>0x7FF){
      // 3-byte UTF-8
      bytes.push(0xE0|(c>>12), 0x80|((c>>6)&0x3F), 0x80|(c&0x3F));
    } else if(c>0x7F){
      // 2-byte UTF-8
      bytes.push(0xC0|(c>>6), 0x80|(c&0x3F));
    } else {
      bytes.push(c);
    }
  }
  const t=QR_TABLE[ver][ecl];
  const totalDC=t[0];
  // Build bit stream
  const bits=[];
  function pushBits(val,len){
    for(let i=len-1;i>=0;i--) bits.push((val>>i)&1);
  }
  pushBits(0b0100,4); // byte mode
  pushBits(bytes.length, ver<10?8:16);
  for(let i=0;i<bytes.length;i++) pushBits(bytes[i],8);
  // terminator
  let term=Math.min(4, totalDC*8-bits.length);
  for(let i=0;i<term;i++) bits.push(0);
  // pad to byte boundary
  while(bits.length%8) bits.push(0);
  // pad codewords
  const padWords=[0xEC,0x11];
  let pi=0;
  const codewords=[];
  for(let i=0;i<bits.length;i+=8){
    let b=0;
    for(let j=0;j<8;j++) b=(b<<1)|(bits[i+j]||0);
    codewords.push(b);
  }
  while(codewords.length<totalDC) codewords.push(padWords[pi++%2]);
  return {bytes, codewords};
}

// ---- Interleave blocks and append EC ----
function buildFinalMessage(codewords, ver, ecl){
  const t=QR_TABLE[ver][ecl];
  const ecPerBlock=t[1];
  const [g1c,g1d,g2c,g2d]=t[2];

  const blocks=[];
  let ptr=0;
  for(let i=0;i<g1c;i++){
    blocks.push(codewords.slice(ptr,ptr+g1d)); ptr+=g1d;
  }
  for(let i=0;i<g2c;i++){
    blocks.push(codewords.slice(ptr,ptr+g2d)); ptr+=g2d;
  }

  // Interleave data
  const data=[];
  const maxData=Math.max(g1d,g2d);
  for(let i=0;i<maxData;i++)
    for(let b=0;b<blocks.length;b++)
      if(i<blocks[b].length) data.push(blocks[b][i]);

  // EC codewords per block
  const ecBlocks=blocks.map(b=>rsEncode(Array.from(b),ecPerBlock));
  const ec=[];
  for(let i=0;i<ecPerBlock;i++)
    for(let b=0;b<ecBlocks.length;b++)
      ec.push(ecBlocks[b][i]);

  return data.concat(ec);
}

// ---- QR matrix building ----
const QR_SIZE = v => v*4+17;

function makeMatrix(size){
  return Array.from({length:size},()=>new Array(size).fill(null));
}

function placeFinderPattern(m,r,c){
  for(let i=0;i<7;i++)
    for(let j=0;j<7;j++){
      const onBorder=(i===0||i===6||j===0||j===6);
      const onInner=(i>=2&&i<=4&&j>=2&&j<=4);
      m[r+i][c+j]=(onBorder||onInner)?1:0;
    }
}

function placeSeparators(m,size){
  for(let i=0;i<8;i++){
    if(m[i][7]===null) m[i][7]=0;
    if(m[7][i]===null) m[7][i]=0;
    if(m[i][size-8]===null) m[i][size-8]=0;
    if(m[7][size-8+i]===null) m[7][size-8+i]=0;
    if(m[size-8][i]===null) m[size-8][i]=0;
    if(m[size-i-1][7]===null) m[size-i-1][7]=0;
  }
}

function placeTimingPatterns(m,size){
  for(let i=8;i<size-8;i++){
    if(m[6][i]===null) m[6][i]=(i%2===0)?1:0;
    if(m[i][6]===null) m[i][6]=(i%2===0)?1:0;
  }
}

function placeDarkModule(m,ver){
  m[4*ver+9][8]=1;
}

// Alignment pattern centers for versions 1-10
const ALIGN_CENTERS = [
  [],[],[6,18],[6,22],[6,26],[6,30],[6,34],
  [6,22,38],[6,24,42],[6,28,46],[6,32,50]
];

function placeAlignmentPatterns(m,ver){
  const centers=ALIGN_CENTERS[ver];
  for(let r=0;r<centers.length;r++){
    for(let c=0;c<centers.length;c++){
      const row=centers[r], col=centers[c];
      if(m[row][col]!==null) continue;
      for(let i=-2;i<=2;i++)
        for(let j=-2;j<=2;j++){
          const v=(i===-2||i===2||j===-2||j===2)?1:(i===0&&j===0)?1:0;
          m[row+i][col+j]=v;
        }
    }
  }
}

// Format info strings (pre-computed for mask patterns 0-7, EC levels L/M/Q/H)
// Format: 15-bit string after BCH and masking with 101010000010010
const FORMAT_INFO = {
  L: [0x77C4,0x72F3,0x7DAA,0x789D,0x662F,0x6318,0x6C41,0x6976],
  M: [0x5412,0x5125,0x5E7C,0x5B4B,0x45F9,0x40CE,0x4F97,0x4AA0],
  Q: [0x355F,0x3068,0x3F31,0x3A06,0x24B4,0x2183,0x2EDA,0x2BED],
  H: [0x1689,0x13BE,0x1CE7,0x19D0,0x0762,0x0255,0x0D0C,0x083B]
};

function placeFormatInfo(m,size,ecl,mask){
  const fmt=FORMAT_INFO[ecl][mask];
  const bits=[];
  for(let i=14;i>=0;i--) bits.push((fmt>>i)&1);
  // Around top-left finder
  const pos=[0,1,2,3,4,5,7,8,size-7,size-6,size-5,size-4,size-3,size-2,size-1];
  for(let i=0;i<6;i++) m[8][pos[i]]=bits[i];
  m[8][7]=bits[6]; m[8][8]=bits[7]; m[7][8]=bits[8];
  for(let i=9;i<15;i++) m[14-i][8]=bits[i];
  // Vertical strip
  for(let i=0;i<8;i++) m[i<6?i:i+1][8]=bits[i];
  // Right & bottom
  for(let i=0;i<8;i++) m[8][size-8+i]=bits[7+i];
  for(let i=0;i<7;i++) m[size-7+i][8]=bits[i];
}

// ---- Data placement ----
function placeData(m,size,data){
  // Build bit stream
  const bits=[];
  for(let i=0;i<data.length;i++){
    for(let j=7;j>=0;j--) bits.push((data[i]>>j)&1);
  }
  let bi=0;
  let up=true;
  for(let col=size-1;col>=0;col-=2){
    if(col===6) col--; // skip timing column
    for(let row=up?size-1:0;up?row>=0:row<size;up?row--:row++){
      for(let dc=0;dc<2;dc++){
        const c=col-dc;
        if(m[row][c]===null){
          m[row][c]=(bi<bits.length)?bits[bi++]:0;
        }
      }
    }
    up=!up;
  }
}

// ---- Masking ----
const MASK_FN = [
  (r,c)=>(r+c)%2===0,
  (r,c)=>r%2===0,
  (r,c)=>c%3===0,
  (r,c)=>(r+c)%3===0,
  (r,c)=>(Math.floor(r/2)+Math.floor(c/3))%2===0,
  (r,c)=>(r*c)%2+(r*c)%3===0,
  (r,c)=>((r*c)%2+(r*c)%3)%2===0,
  (r,c)=>((r+c)%2+(r*c)%3)%2===0,
];

function applyMask(m,size,mask){
  const fn=MASK_FN[mask];
  for(let r=0;r<size;r++)
    for(let c=0;c<size;c++)
      if(m[r][c]===0||m[r][c]===1)
        if(fn(r,c)) m[r][c]^=1;
  return m;
}

// Evaluate penalty (simplified — we just pick mask 0 after testing all 8)
function penaltyScore(m,size){
  let score=0;
  // N1: runs of 5+
  for(let r=0;r<size;r++){
    let run=1;
    for(let c=1;c<size;c++){
      if(m[r][c]===m[r][c-1]) run++;
      else{ if(run>=5) score+=3+(run-5); run=1; }
    }
    if(run>=5) score+=3+(run-5);
  }
  for(let c=0;c<size;c++){
    let run=1;
    for(let r=1;r<size;r++){
      if(m[r][c]===m[r-1][c]) run++;
      else{ if(run>=5) score+=3+(run-5); run=1; }
    }
    if(run>=5) score+=3+(run-5);
  }
  // N2: 2x2 blocks
  for(let r=0;r<size-1;r++)
    for(let c=0;c<size-1;c++)
      if(m[r][c]===m[r][c+1]&&m[r][c]===m[r+1][c]&&m[r][c]===m[r+1][c+1])
        score+=3;
  // N4: dark ratio
  let dark=0;
  for(let r=0;r<size;r++) for(let c=0;c<size;c++) if(m[r][c]) dark++;
  const ratio=dark/(size*size);
  score+=Math.abs(Math.round(ratio*20)-10)*10;
  return score;
}

function buildQR(text, ecl){
  // Convert to UTF-8 bytes
  const enc=new TextEncoder().encode(text);
  const byteLen=enc.length;
  const ver=chooseVersion(byteLen,ecl);
  if(!ver) return null;
  const {codewords}=encodeData(text,ver,ecl);
  const finalMsg=buildFinalMessage(codewords,ver,ecl);
  const size=QR_SIZE(ver);

  let bestMask=0, bestScore=Infinity, bestMatrix=null;
  for(let mask=0;mask<8;mask++){
    const m=makeMatrix(size);
    placeFinderPattern(m,0,0);
    placeFinderPattern(m,0,size-7);
    placeFinderPattern(m,size-7,0);
    placeSeparators(m,size);
    placeTimingPatterns(m,size);
    if(ver>=2) placeAlignmentPatterns(m,ver);
    placeDarkModule(m,ver);
    // Reserve format areas
    for(let i=0;i<9;i++){
      if(m[8][i]===null) m[8][i]=0;
      if(m[i][8]===null) m[i][8]=0;
    }
    for(let i=0;i<8;i++){
      if(m[8][size-8+i]===null) m[8][size-8+i]=0;
      if(m[size-8+i][8]===null) m[size-8+i][8]=0;
    }
    placeData(m,size,[...finalMsg]);
    applyMask(m,size,mask);
    placeFormatInfo(m,size,ecl,mask);
    const score=penaltyScore(m,size);
    if(score<bestScore){ bestScore=score; bestMask=mask; bestMatrix=m.map(r=>[...r]); }
  }
  return {matrix:bestMatrix,size,ver};
}

// ---- Rendering ----
function renderQR(matrix,size,canvasSize,fg,bg){
  const canvas=document.getElementById('qr-canvas');
  canvas.width=canvasSize;
  canvas.height=canvasSize;
  const ctx=canvas.getContext('2d');
  ctx.fillStyle=bg;
  ctx.fillRect(0,0,canvasSize,canvasSize);
  const quiet=4;
  const cellSize=(canvasSize)/(size+quiet*2);
  ctx.fillStyle=fg;
  for(let r=0;r<size;r++){
    for(let c=0;c<size;c++){
      if(matrix[r][c]){
        ctx.fillRect(
          Math.round((c+quiet)*cellSize),
          Math.round((r+quiet)*cellSize),
          Math.ceil(cellSize),
          Math.ceil(cellSize)
        );
      }
    }
  }
}

// ---- UI Logic ----
let currentPreset='url';

const PRESETS={
  url:  {placeholder:'https://example.com', prefix:'', hint:'Enter any URL'},
  text: {placeholder:'Hello, World!', prefix:'', hint:'Enter any text'},
  email:{placeholder:'user@example.com', prefix:'mailto:', hint:'Enter email address'},
  phone:{placeholder:'+1234567890', prefix:'tel:', hint:'Enter phone number with country code'},
  wifi: {placeholder:'', prefix:'', hint:'Fill in WiFi network details below'},
};

function qrSetPreset(preset, btn){
  currentPreset=preset;
  document.querySelectorAll('#qr-app .qr-preset-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const p=PRESETS[preset];
  const ta=document.getElementById('qr-text');
  const wf=document.getElementById('qr-wifi-fields');
  if(preset==='wifi'){
    ta.placeholder='(WiFi string will be generated automatically)';
    ta.readOnly=true;
    wf.classList.add('show');
    qrBuildWifi();
  } else {
    ta.readOnly=false;
    ta.placeholder=p.placeholder;
    wf.classList.remove('show');
    if(p.prefix && !ta.value.startsWith(p.prefix)){
      ta.value=p.prefix;
    }
    qrOnInput();
  }
}

function qrBuildWifi(){
  const ssid=document.getElementById('qr-wifi-ssid').value;
  const pass=document.getElementById('qr-wifi-pass').value;
  const sec=document.getElementById('qr-wifi-sec').value;
  const str=`WIFI:T:${sec};S:${ssid};P:${pass};;`;
  document.getElementById('qr-text').value=str;
  qrOnInput();
}

function qrOnInput(){
  const text=document.getElementById('qr-text').value;
  const len=new TextEncoder().encode(text).length;
  const cc=document.getElementById('qr-char-count');
  cc.textContent=`${len} / 500 bytes`;
  cc.className='qr-char-count'+(len>500?' bad':len>350?' warn':'');
  qrRender();
}

function qrRender(){
  const text=document.getElementById('qr-text').value.trim();
  const ecl=document.getElementById('qr-ecl').value;
  const canvasSize=parseInt(document.getElementById('qr-size').value);
  const fg=document.getElementById('qr-fg-hex').value||'#000000';
  const bg=document.getElementById('qr-bg-hex').value||'#ffffff';
  const status=document.getElementById('qr-status');

  if(!text){
    const canvas=document.getElementById('qr-canvas');
    const ctx=canvas.getContext('2d');
    canvas.width=canvasSize; canvas.height=canvasSize;
    ctx.fillStyle='#0f172a'; ctx.fillRect(0,0,canvasSize,canvasSize);
    status.textContent=''; status.className='qr-status';
    return;
  }

  try{
    const result=buildQR(text,ecl);
    if(!result){
      status.textContent='Text too long for QR version 1-10. Please shorten.';
      status.className='qr-status err';
      return;
    }
    renderQR(result.matrix,result.size,canvasSize,fg,bg);
    status.textContent=`QR version ${result.ver} generated (${result.size}x${result.size} modules).`;
    status.className='qr-status ok';
  } catch(e){
    status.textContent='Error generating QR code: '+e.message;
    status.className='qr-status err';
  }
}

function qrDownload(){
  const canvas=document.getElementById('qr-canvas');
  const link=document.createElement('a');
  link.download='qr-code.png';
  link.href=canvas.toDataURL('image/png');
  link.click();
}

async function qrCopyClipboard(){
  const canvas=document.getElementById('qr-canvas');
  const status=document.getElementById('qr-status');
  try{
    canvas.toBlob(async blob=>{
      await navigator.clipboard.write([new ClipboardItem({'image/png':blob})]);
      status.textContent='QR code copied to clipboard!';
      status.className='qr-status ok';
      setTimeout(()=>{ status.className='qr-status'; },2500);
    });
  } catch(e){
    status.textContent='Copy failed — use Download instead.';
    status.className='qr-status err';
  }
}

function qrSyncColor(which){
  const color=document.getElementById('qr-'+which+'-color').value;
  document.getElementById('qr-'+which+'-hex').value=color;
  qrRender();
}

function qrHexChange(which){
  const hex=document.getElementById('qr-'+which+'-hex').value;
  if(/^#[0-9A-Fa-f]{6}$/.test(hex)){
    document.getElementById('qr-'+which+'-color').value=hex;
    qrRender();
  }
}

function qrReset(){
  document.getElementById('qr-text').value='https://productivity.works';
  document.getElementById('qr-text').readOnly=false;
  document.getElementById('qr-wifi-fields').classList.remove('show');
  document.getElementById('qr-ecl').value='M';
  document.getElementById('qr-size').value='300';
  document.getElementById('qr-fg-color').value='#1a1a2e';
  document.getElementById('qr-fg-hex').value='#1a1a2e';
  document.getElementById('qr-bg-color').value='#ffffff';
  document.getElementById('qr-bg-hex').value='#ffffff';
  currentPreset='url';
  document.querySelectorAll('#qr-app .qr-preset-btn').forEach((b,i)=>b.classList.toggle('active',i===0));
  qrOnInput();
}

// Init
qrRender();

})();
</script>

---

## Related Tools

> Resize images for your QR code marketing materials → [Image Resizer](/tools/image-resizer/)

> Generate a random number for giveaways or lotteries → [Random Number Generator](/tools/random-number-generator/)

> Pick the perfect colors for your QR code design → [Color Picker](/tools/color-picker/)
