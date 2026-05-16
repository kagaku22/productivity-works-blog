---
title: "Aspect Ratio Crop Calculator - Free Online Crop Size Tool"
date: 2025-05-16
description: "Enter image dimensions, choose a target aspect ratio (16:9, 4:3, 1:1, 3:2, 21:9, or custom) and instantly see the exact crop dimensions with a visual overlay preview. Free, no upload needed."
categories: ["Free Tools"]
tags: ["aspect ratio", "crop calculator", "image crop", "16:9", "4:3", "photo crop", "free tool", "image tool"]
slug: "aspect-ratio-crop"
aliases: ["/tools/crop-calculator/"]
cover:
  image: "/images/covers/aspect-ratio-crop.png"
  alt: "Aspect Ratio Crop Calculator"
ShowToc: false
---

<div id="arc-app">

<style>
#arc-app {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: #0f0f13;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 24px;
  margin: 0 auto;
  max-width: 860px;
  box-sizing: border-box;
}
#arc-app * { box-sizing: border-box; }

#arc-app h2 {
  font-size: 1.05rem;
  font-weight: 600;
  color: #f1f5f9;
  margin: 0 0 18px;
  letter-spacing: 0.02em;
}

/* section labels */
.arc-label {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 8px;
  display: block;
}

/* input grid */
.arc-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 16px;
}

@media (max-width: 500px) {
  .arc-row { grid-template-columns: 1fr; }
}

.arc-field {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.arc-field label {
  font-size: 0.78rem;
  color: #94a3b8;
  font-weight: 600;
}

.arc-input {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 7px;
  color: #e2e8f0;
  font-size: 1rem;
  padding: 9px 12px;
  font-family: inherit;
  outline: none;
  transition: border-color 0.2s;
  width: 100%;
}
.arc-input:focus { border-color: #6366f1; }
.arc-input::placeholder { color: #4a5568; }

/* ratio button pills */
.arc-ratio-row {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

.arc-ratio-btn {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 20px;
  color: #94a3b8;
  font-size: 0.8rem;
  font-weight: 600;
  padding: 5px 14px;
  cursor: pointer;
  font-family: inherit;
  transition: all 0.15s;
  white-space: nowrap;
}
.arc-ratio-btn:hover { border-color: #6366f1; color: #a5b4fc; }
.arc-ratio-btn.arc-active { background: rgba(99,102,241,0.18); border-color: #6366f1; color: #a5b4fc; }

/* custom ratio inputs */
.arc-custom-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}
.arc-custom-row label { font-size: 0.78rem; color: #94a3b8; white-space: nowrap; }
.arc-custom-input {
  width: 68px;
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 7px;
  color: #e2e8f0;
  font-size: 0.95rem;
  padding: 7px 10px;
  font-family: inherit;
  outline: none;
  transition: border-color 0.2s;
  text-align: center;
}
.arc-custom-input:focus { border-color: #6366f1; }
.arc-sep { color: #64748b; font-size: 1rem; font-weight: 700; }

/* results */
.arc-results {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 10px;
  margin-bottom: 20px;
}
@media (max-width: 500px) { .arc-results { grid-template-columns: 1fr; } }

.arc-card {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  padding: 12px 14px;
}
.arc-card-label {
  font-size: 0.68rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 4px;
}
.arc-card-value {
  font-size: 1.1rem;
  font-weight: 700;
  color: #a5b4fc;
  font-family: 'Courier New', monospace;
}
.arc-card-unit {
  font-size: 0.72rem;
  color: #475569;
  margin-top: 2px;
}
.arc-card.arc-highlight { border-color: #6366f1; }
.arc-card.arc-highlight .arc-card-label { color: #6366f1; }

/* canvas preview */
.arc-preview-wrap {
  background: #1a1a24;
  border: 1px solid #2d2d3d;
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 16px;
}
.arc-preview-title {
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 12px;
}
#arc-canvas {
  display: block;
  margin: 0 auto;
  border-radius: 4px;
  max-width: 100%;
}

/* note */
.arc-note {
  font-size: 0.78rem;
  color: #4a5568;
  line-height: 1.6;
}
.arc-note strong { color: #64748b; }
</style>

<h2>Aspect Ratio Crop Calculator</h2>

<span class="arc-label">Original Image Size (pixels)</span>
<div class="arc-row">
  <div class="arc-field">
    <label for="arc-w">Width</label>
    <input class="arc-input" id="arc-w" type="number" min="1" placeholder="e.g. 1920" value="1920" />
  </div>
  <div class="arc-field">
    <label for="arc-h">Height</label>
    <input class="arc-input" id="arc-h" type="number" min="1" placeholder="e.g. 1080" value="1080" />
  </div>
</div>

<span class="arc-label">Target Aspect Ratio</span>
<div class="arc-ratio-row" id="arc-ratios">
  <button class="arc-ratio-btn" data-w="16" data-h="9">16:9</button>
  <button class="arc-ratio-btn" data-w="4" data-h="3">4:3</button>
  <button class="arc-ratio-btn" data-w="1" data-h="1">1:1</button>
  <button class="arc-ratio-btn" data-w="3" data-h="2">3:2</button>
  <button class="arc-ratio-btn" data-w="21" data-h="9">21:9</button>
  <button class="arc-ratio-btn" data-w="9" data-h="16">9:16</button>
  <button class="arc-ratio-btn" data-w="5" data-h="4">5:4</button>
  <button class="arc-ratio-btn arc-custom-trigger" data-custom="true">Custom</button>
</div>

<div class="arc-custom-row" id="arc-custom-row" style="display:none;">
  <label>Custom ratio:</label>
  <input class="arc-custom-input" id="arc-cw" type="number" min="1" value="3" />
  <span class="arc-sep">:</span>
  <input class="arc-custom-input" id="arc-ch" type="number" min="1" value="1" />
</div>

<div class="arc-results" id="arc-results">
  <div class="arc-card arc-highlight">
    <div class="arc-card-label">Crop Width</div>
    <div class="arc-card-value" id="arc-crop-w">—</div>
    <div class="arc-card-unit">pixels</div>
  </div>
  <div class="arc-card arc-highlight">
    <div class="arc-card-label">Crop Height</div>
    <div class="arc-card-value" id="arc-crop-h">—</div>
    <div class="arc-card-unit">pixels</div>
  </div>
  <div class="arc-card">
    <div class="arc-card-label">Crop Offset (center)</div>
    <div class="arc-card-value" id="arc-offset">—</div>
    <div class="arc-card-unit">x, y from top-left</div>
  </div>
  <div class="arc-card">
    <div class="arc-card-label">Cropped Away (W)</div>
    <div class="arc-card-value" id="arc-lost-w">—</div>
    <div class="arc-card-unit">pixels removed</div>
  </div>
  <div class="arc-card">
    <div class="arc-card-label">Cropped Away (H)</div>
    <div class="arc-card-value" id="arc-lost-h">—</div>
    <div class="arc-card-unit">pixels removed</div>
  </div>
  <div class="arc-card">
    <div class="arc-card-label">Pixels Kept</div>
    <div class="arc-card-value" id="arc-kept-pct">—</div>
    <div class="arc-card-unit">% of original</div>
  </div>
</div>

<div class="arc-preview-wrap">
  <div class="arc-preview-title">Visual Crop Preview</div>
  <canvas id="arc-canvas" width="560" height="320"></canvas>
</div>

<p class="arc-note" id="arc-note">Select a target ratio and enter image dimensions to calculate crop.</p>

<script>
(function(){
'use strict';

var state = {
  imgW: 1920,
  imgH: 1080,
  ratioW: null,
  ratioH: null,
  custom: false
};

var canvas = document.getElementById('arc-canvas');
var ctx = canvas.getContext('2d');

function gcd(a,b){ return b===0?a:gcd(b,a%b); }

function calculate(){
  var iw = state.imgW;
  var ih = state.imgH;
  var rw = state.ratioW;
  var rh = state.ratioH;

  if(!iw||!ih||!rw||!rh||iw<1||ih<1||rw<1||rh<1){
    setText('arc-crop-w','—');setText('arc-crop-h','—');
    setText('arc-offset','—');setText('arc-lost-w','—');
    setText('arc-lost-h','—');setText('arc-kept-pct','—');
    document.getElementById('arc-note').textContent='Select a target ratio and enter image dimensions to calculate crop.';
    drawBlank(); return;
  }

  /* Determine crop box: largest rectangle fitting ratio inside image */
  var cropW, cropH;
  /* Try fitting by width */
  cropW = iw;
  cropH = Math.round(iw * rh / rw);
  if(cropH > ih){
    /* Fit by height instead */
    cropH = ih;
    cropW = Math.round(ih * rw / rh);
  }

  var offsetX = Math.floor((iw - cropW) / 2);
  var offsetY = Math.floor((ih - cropH) / 2);
  var lostW = iw - cropW;
  var lostH = ih - cropH;
  var keptPct = ((cropW * cropH) / (iw * ih) * 100).toFixed(1);

  setText('arc-crop-w', cropW.toLocaleString());
  setText('arc-crop-h', cropH.toLocaleString());
  setText('arc-offset', offsetX.toLocaleString() + ', ' + offsetY.toLocaleString());
  setText('arc-lost-w', lostW > 0 ? lostW.toLocaleString() : '0');
  setText('arc-lost-h', lostH > 0 ? lostH.toLocaleString() : '0');
  setText('arc-kept-pct', keptPct + '%');

  var g = gcd(rw, rh);
  var rWs = rw/g; var rHs = rh/g;
  document.getElementById('arc-note').innerHTML =
    '<strong>Result:</strong> Crop to <strong>' + cropW.toLocaleString() + ' × ' + cropH.toLocaleString() +
    ' px</strong> (ratio ' + rWs + ':' + rHs + '), centered at offset (' + offsetX + ', ' + offsetY + '). ' +
    (lostW>0 ? lostW+'px removed from sides.' : '') +
    (lostH>0 ? (lostW>0?' ':'')+lostH+'px removed from top/bottom.' : '') +
    (lostW===0&&lostH===0?' No pixels removed — image already matches this ratio.':'');

  drawPreview(iw, ih, cropW, cropH, offsetX, offsetY);
}

function setText(id, val){
  document.getElementById(id).textContent = val;
}

function drawBlank(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle='#1a1a24';
  ctx.fillRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle='#2d2d3d';
  ctx.font='14px "Segoe UI",system-ui,sans-serif';
  ctx.textAlign='center';
  ctx.fillText('Preview will appear here', canvas.width/2, canvas.height/2);
}

function drawPreview(iw, ih, cw, ch, ox, oy){
  var canW = canvas.width;
  var canH = canvas.height;
  var pad = 20;

  /* Scale image to canvas */
  var scale = Math.min((canW - pad*2)/iw, (canH - pad*2)/ih);
  var dispW = Math.round(iw * scale);
  var dispH = Math.round(ih * scale);
  var imgX = Math.round((canW - dispW) / 2);
  var imgY = Math.round((canH - dispH) / 2);

  /* Crop rect in canvas coords */
  var cropX = imgX + Math.round(ox * scale);
  var cropY = imgY + Math.round(oy * scale);
  var cropW2 = Math.round(cw * scale);
  var cropH2 = Math.round(ch * scale);

  ctx.clearRect(0,0,canW,canH);

  /* Background */
  ctx.fillStyle = '#0f0f13';
  ctx.fillRect(0,0,canW,canH);

  /* Full image area (dimmed) */
  ctx.fillStyle = '#1e1e2e';
  ctx.strokeStyle = '#2d2d3d';
  ctx.lineWidth = 1;
  ctx.fillRect(imgX, imgY, dispW, dispH);
  ctx.strokeRect(imgX+0.5, imgY+0.5, dispW, dispH);

  /* Overlay outside crop — semi-transparent dark */
  ctx.fillStyle = 'rgba(0,0,0,0.52)';
  /* top */
  if(oy>0) ctx.fillRect(imgX, imgY, dispW, cropY-imgY);
  /* bottom */
  var botY = cropY + cropH2;
  if(botY < imgY+dispH) ctx.fillRect(imgX, botY, dispW, (imgY+dispH)-botY);
  /* left */
  if(ox>0) ctx.fillRect(imgX, cropY, cropX-imgX, cropH2);
  /* right */
  var rightX = cropX + cropW2;
  if(rightX < imgX+dispW) ctx.fillRect(rightX, cropY, (imgX+dispW)-rightX, cropH2);

  /* Crop rect border */
  ctx.strokeStyle = '#6366f1';
  ctx.lineWidth = 2;
  ctx.strokeRect(cropX+0.5, cropY+0.5, cropW2, cropH2);

  /* Crop rect fill (bright) */
  ctx.fillStyle = 'rgba(99,102,241,0.08)';
  ctx.fillRect(cropX, cropY, cropW2, cropH2);

  /* Corner markers */
  var mkLen = Math.min(14, cropW2*0.15, cropH2*0.15);
  ctx.strokeStyle = '#a5b4fc';
  ctx.lineWidth = 2.5;
  var corners = [[cropX,cropY],[cropX+cropW2,cropY],[cropX,cropY+cropH2],[cropX+cropW2,cropY+cropH2]];
  var dirs = [[1,1],[-1,1],[1,-1],[-1,-1]];
  for(var i=0;i<4;i++){
    var cx2=corners[i][0]; var cy2=corners[i][1];
    var dx=dirs[i][0]; var dy=dirs[i][1];
    ctx.beginPath(); ctx.moveTo(cx2,cy2); ctx.lineTo(cx2+dx*mkLen,cy2); ctx.stroke();
    ctx.beginPath(); ctx.moveTo(cx2,cy2); ctx.lineTo(cx2,cy2+dy*mkLen); ctx.stroke();
  }

  /* Labels */
  ctx.font = 'bold 11px "Segoe UI",system-ui,sans-serif';
  ctx.textAlign = 'center';
  ctx.fillStyle = '#6366f1';
  ctx.fillText(cw + ' \xd7 ' + ch + ' px', cropX + cropW2/2, cropY - 6 > imgY+4 ? cropY-6 : cropY+14);

  ctx.fillStyle = '#475569';
  ctx.font = '10px "Segoe UI",system-ui,sans-serif';
  ctx.fillText(iw + ' \xd7 ' + ih + ' (original)', imgX+dispW/2, imgY+dispH+13 < canH-4 ? imgY+dispH+13 : imgY+dispH-4);
}

function updateFromRatio(rw, rh, custom){
  state.ratioW = rw; state.ratioH = rh; state.custom = !!custom;
  document.getElementById('arc-custom-row').style.display = custom ? 'flex' : 'none';
  calculate();
}

/* Ratio buttons */
var btns = document.querySelectorAll('#arc-ratios .arc-ratio-btn');
btns.forEach(function(btn){
  btn.addEventListener('click', function(){
    btns.forEach(function(b){b.classList.remove('arc-active');}); btn.classList.add('arc-active');
    if(btn.getAttribute('data-custom')==='true'){
      updateFromRatio(
        parseFloat(document.getElementById('arc-cw').value)||3,
        parseFloat(document.getElementById('arc-ch').value)||1,
        true
      );
    } else {
      updateFromRatio(
        parseFloat(btn.getAttribute('data-w')),
        parseFloat(btn.getAttribute('data-h')),
        false
      );
    }
  });
});

/* Image size inputs */
document.getElementById('arc-w').addEventListener('input', function(){
  state.imgW = Math.max(1, parseFloat(this.value)||0);
  calculate();
});
document.getElementById('arc-h').addEventListener('input', function(){
  state.imgH = Math.max(1, parseFloat(this.value)||0);
  calculate();
});

/* Custom ratio inputs */
document.getElementById('arc-cw').addEventListener('input', function(){
  state.ratioW = Math.max(1, parseFloat(this.value)||1);
  if(state.custom) calculate();
});
document.getElementById('arc-ch').addEventListener('input', function(){
  state.ratioH = Math.max(1, parseFloat(this.value)||1);
  if(state.custom) calculate();
});

/* Default selection: 16:9 */
(function(){
  var def = document.querySelector('[data-w="16"][data-h="9"]');
  if(def){ def.classList.add('arc-active'); state.ratioW=16; state.ratioH=9; }
  calculate();
})();

drawBlank();

})();
</script>

</div>

---

## Related Tools

> Calculate aspect ratios → [Aspect Ratio Calculator](/tools/aspect-ratio-calculator/)

> Resize images in the browser → [Image Resizer](/tools/image-resizer/)

> Convert images to Base64 → [Image to Base64](/tools/image-to-base64/)
