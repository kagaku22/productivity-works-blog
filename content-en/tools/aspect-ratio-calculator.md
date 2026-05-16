---
title: "Aspect Ratio Calculator – Free Online Tool"
date: 2025-05-16
description: "Calculate aspect ratios, lock dimensions, preview rectangles, compute diagonal sizes in cm/inches, and find PPI — all free, no sign-up."
categories: ["Free Tools"]
slug: "aspect-ratio-calculator"
aliases: ["/tools/ratio-calculator/", "/tools/aspect-ratio/"]
ShowToc: false
cover:
  image: "/images/covers/aspect-ratio-calculator.png"
  alt: "Aspect Ratio Calculator"
---

<style>
/* ── scope everything under #ar-app ── */
#ar-app *,#ar-app *::before,#ar-app *::after{box-sizing:border-box;margin:0;padding:0}
#ar-app{
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;
  max-width:720px;color:#1e293b;
}
#ar-app h2{font-size:1.1rem;font-weight:700;margin-bottom:.75rem;color:#0284c7}
#ar-app .card{background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:1.25rem;margin-bottom:1.25rem}
#ar-app label{display:block;font-size:.82rem;font-weight:600;color:#475569;margin-bottom:.3rem}
#ar-app input[type=number]{
  width:100%;padding:.5rem .75rem;border:1.5px solid #cbd5e1;border-radius:8px;
  font-size:1rem;color:#1e293b;background:#fff;outline:none;
  transition:border-color .15s;
}
#ar-app input[type=number]:focus{border-color:#0284c7}
#ar-app .row{display:flex;gap:1rem;flex-wrap:wrap}
#ar-app .col{flex:1;min-width:120px}
#ar-app .ratio-badge{
  display:inline-block;background:#0284c7;color:#fff;
  font-size:1.4rem;font-weight:800;letter-spacing:.02em;
  padding:.35rem 1.1rem;border-radius:8px;margin-top:.6rem;
}
#ar-app .ratio-exact{font-size:.8rem;color:#64748b;margin-top:.3rem}
/* presets */
#ar-app .presets{display:flex;flex-wrap:wrap;gap:.5rem;margin-bottom:1rem}
#ar-app .preset-btn{
  border:1.5px solid #0284c7;color:#0284c7;background:#fff;
  padding:.3rem .75rem;border-radius:20px;font-size:.82rem;font-weight:600;
  cursor:pointer;transition:background .15s,color .15s;
}
#ar-app .preset-btn:hover,#ar-app .preset-btn.active{background:#0284c7;color:#fff}
/* lock */
#ar-app .lock-row{display:flex;align-items:center;gap:.6rem;margin-top:.5rem}
#ar-app .lock-row input[type=checkbox]{width:1rem;height:1rem;accent-color:#0284c7;cursor:pointer}
#ar-app .lock-row span{font-size:.82rem;color:#475569;font-weight:600}
/* preview */
#ar-app #ar-preview-wrap{
  display:flex;align-items:center;justify-content:center;
  background:#e0f2fe;border:1px solid #bae6fd;border-radius:10px;
  min-height:130px;padding:1rem;overflow:hidden;
}
#ar-app #ar-rect{
  background:#0284c7;border-radius:4px;
  display:flex;align-items:center;justify-content:center;
  color:#fff;font-size:.75rem;font-weight:700;letter-spacing:.03em;
  transition:width .25s,height .25s;min-width:24px;min-height:24px;
}
/* diagonal / PPI */
#ar-app .result-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:.75rem;margin-top:.75rem}
#ar-app .result-item{background:#fff;border:1px solid #e2e8f0;border-radius:8px;padding:.65rem .85rem}
#ar-app .result-item .label{font-size:.72rem;color:#64748b;font-weight:600;text-transform:uppercase;letter-spacing:.04em}
#ar-app .result-item .value{font-size:1.1rem;font-weight:700;color:#0284c7;margin-top:.15rem}
</style>

<div id="ar-app">

<!-- ① RATIO INPUT -->
<div class="card">
  <h2>Ratio from Dimensions</h2>
  <div class="row" style="margin-bottom:.75rem">
    <div class="col">
      <label for="ar-w">Width (px)</label>
      <input type="number" id="ar-w" min="1" placeholder="e.g. 1920">
    </div>
    <div class="col">
      <label for="ar-h">Height (px)</label>
      <input type="number" id="ar-h" min="1" placeholder="e.g. 1080">
    </div>
  </div>
  <div id="ar-ratio-out"><span class="ratio-badge" id="ar-ratio-badge">—</span></div>
  <div class="ratio-exact" id="ar-ratio-exact"></div>
  <div class="lock-row">
    <input type="checkbox" id="ar-lock">
    <span>Lock ratio — enter one dimension to auto-fill the other</span>
  </div>
</div>

<!-- ② PRESETS -->
<div class="card">
  <h2>Common Ratio Presets</h2>
  <div class="presets" id="ar-presets">
    <button class="preset-btn" data-w="16" data-h="9">16:9</button>
    <button class="preset-btn" data-w="4" data-h="3">4:3</button>
    <button class="preset-btn" data-w="1" data-h="1">1:1</button>
    <button class="preset-btn" data-w="21" data-h="9">21:9</button>
    <button class="preset-btn" data-w="9" data-h="16">9:16</button>
    <button class="preset-btn" data-w="3" data-h="2">3:2</button>
    <button class="preset-btn" data-w="2" data-h="3">2:3</button>
  </div>

  <!-- locked dimension inputs shown when lock is on -->
  <div id="ar-lock-inputs" style="display:none">
    <div class="row">
      <div class="col">
        <label for="ar-lw">Width (px)</label>
        <input type="number" id="ar-lw" min="1" placeholder="enter width">
      </div>
      <div class="col">
        <label for="ar-lh">Height (px)</label>
        <input type="number" id="ar-lh" min="1" placeholder="auto-filled">
      </div>
    </div>
  </div>
</div>

<!-- ③ VISUAL PREVIEW -->
<div class="card">
  <h2>Visual Preview</h2>
  <div id="ar-preview-wrap">
    <div id="ar-rect">?</div>
  </div>
</div>

<!-- ④ DIAGONAL + PPI -->
<div class="card">
  <h2>Diagonal & PPI Calculator</h2>
  <div class="row">
    <div class="col">
      <label for="ar-diag">Screen diagonal (inches)</label>
      <input type="number" id="ar-diag" min="0.1" step="0.1" placeholder="e.g. 27">
    </div>
  </div>
  <div class="result-grid" id="ar-diag-results">
    <div class="result-item"><div class="label">Width (cm)</div><div class="value" id="ar-wcm">—</div></div>
    <div class="result-item"><div class="label">Height (cm)</div><div class="value" id="ar-hcm">—</div></div>
    <div class="result-item"><div class="label">Width (in)</div><div class="value" id="ar-win">—</div></div>
    <div class="result-item"><div class="label">Height (in)</div><div class="value" id="ar-hin">—</div></div>
    <div class="result-item"><div class="label">PPI</div><div class="value" id="ar-ppi">—</div></div>
    <div class="result-item"><div class="label">Diagonal (cm)</div><div class="value" id="ar-diagcm">—</div></div>
  </div>
</div>

</div><!-- /#ar-app -->

<script>
(function(){
  // ── helpers ──
  function gcd(a,b){return b===0?a:gcd(b,a%b);}
  function simplify(w,h){var g=gcd(Math.round(w),Math.round(h));return[Math.round(w)/g,Math.round(h)/g];}

  // state
  var lockedW=16,lockedH=9,lockOn=false;

  // elements
  var elW=document.getElementById('ar-w');
  var elH=document.getElementById('ar-h');
  var elBadge=document.getElementById('ar-ratio-badge');
  var elExact=document.getElementById('ar-ratio-exact');
  var elLock=document.getElementById('ar-lock');
  var elLockInputs=document.getElementById('ar-lock-inputs');
  var elLW=document.getElementById('ar-lw');
  var elLH=document.getElementById('ar-lh');
  var elRect=document.getElementById('ar-rect');
  var elDiag=document.getElementById('ar-diag');
  var elWcm=document.getElementById('ar-wcm');
  var elHcm=document.getElementById('ar-hcm');
  var elWin=document.getElementById('ar-win');
  var elHin=document.getElementById('ar-hin');
  var elPpi=document.getElementById('ar-ppi');
  var elDiagcm=document.getElementById('ar-diagcm');

  function updateRatioDisplay(w,h){
    if(!w||!h||w<=0||h<=0){elBadge.textContent='—';elExact.textContent='';updatePreview(0,0);return;}
    var s=simplify(w,h);
    elBadge.textContent=s[0]+':'+s[1];
    elExact.textContent='Exact ratio: '+w+' : '+h+(s[0]!==w||s[1]!==h?' (simplified from '+w+'×'+h+')':'');
    lockedW=s[0];lockedH=s[1];
    updatePreview(w,h);
    updateDiag();
  }

  function updatePreview(w,h){
    var maxW=280,maxH=140;
    if(!w||!h||w<=0||h<=0){elRect.style.width='60px';elRect.style.height='60px';elRect.textContent='?';return;}
    var ratio=w/h;
    var rw,rh;
    if(ratio>=maxW/maxH){rw=maxW;rh=Math.round(maxW/ratio);}
    else{rh=maxH;rw=Math.round(maxH*ratio);}
    rw=Math.max(rw,24);rh=Math.max(rh,24);
    elRect.style.width=rw+'px';elRect.style.height=rh+'px';
    elRect.textContent=w+'×'+h;
  }

  function updateDiag(){
    var d=parseFloat(elDiag.value);
    var w=parseFloat(elW.value)||0;
    var h=parseFloat(elH.value)||0;
    if(!d||d<=0){elWcm.textContent='—';elHcm.textContent='—';elWin.textContent='—';elHin.textContent='—';elPpi.textContent='—';elDiagcm.textContent='—';return;}
    // use locked ratio if dimensions empty
    var rw=w||lockedW, rh=h||lockedH;
    if(!rw||!rh){return;}
    // physical size from diagonal and ratio
    var diagRatio=Math.sqrt(rw*rw+rh*rh);
    var wIn=d*rw/diagRatio;
    var hIn=d*rh/diagRatio;
    elWin.textContent=wIn.toFixed(2)+' in';
    elHin.textContent=hIn.toFixed(2)+' in';
    elWcm.textContent=(wIn*2.54).toFixed(2)+' cm';
    elHcm.textContent=(hIn*2.54).toFixed(2)+' cm';
    elDiagcm.textContent=(d*2.54).toFixed(2)+' cm';
    // PPI requires pixel dimensions
    if(w>0&&h>0){
      var ppi=Math.sqrt(w*w+h*h)/d;
      elPpi.textContent=Math.round(ppi)+' ppi';
    } else {
      elPpi.textContent='Enter px dims';
    }
  }

  // ── ratio inputs ──
  function onDimInput(){
    var w=parseFloat(elW.value);
    var h=parseFloat(elH.value);
    updateRatioDisplay(w,h);
  }
  elW.addEventListener('input',onDimInput);
  elH.addEventListener('input',onDimInput);

  // ── lock checkbox ──
  elLock.addEventListener('change',function(){
    lockOn=this.checked;
    elLockInputs.style.display=lockOn?'block':'none';
    if(lockOn){
      // capture current ratio
      var w=parseFloat(elW.value)||lockedW;
      var h=parseFloat(elH.value)||lockedH;
      var s=simplify(w,h);
      lockedW=s[0];lockedH=s[1];
      elLW.value='';elLH.value='';
    }
  });

  // locked width → auto height
  elLW.addEventListener('input',function(){
    var w=parseFloat(this.value);
    if(!w||w<=0){elLH.value='';return;}
    var h=Math.round(w*lockedH/lockedW);
    elLH.value=h;
    // also populate main inputs for PPI/diag
    elW.value=w;elH.value=h;
    updatePreview(w,h);updateDiag();
  });
  // locked height → auto width
  elLH.addEventListener('input',function(){
    if(lockOn&&!elLW.value){
      var h=parseFloat(this.value);
      if(!h||h<=0){elLW.value='';return;}
      var w=Math.round(h*lockedW/lockedH);
      elLW.value=w;
      elW.value=w;elH.value=h;
      updatePreview(w,h);updateDiag();
    }
  });

  // ── preset buttons ──
  document.getElementById('ar-presets').addEventListener('click',function(e){
    var btn=e.target.closest('.preset-btn');
    if(!btn)return;
    document.querySelectorAll('#ar-app .preset-btn').forEach(function(b){b.classList.remove('active');});
    btn.classList.add('active');
    var pw=parseInt(btn.dataset.w);
    var ph=parseInt(btn.dataset.h);
    lockedW=pw;lockedH=ph;
    elW.value=pw;elH.value=ph;
    updateRatioDisplay(pw,ph);
    if(lockOn){elLW.value='';elLH.value='';}
  });

  // ── diagonal input ──
  elDiag.addEventListener('input',updateDiag);
})();
</script>

---

**Related:** Resize images to exact dimensions — [Image Resizer](/tools/image-resizer/)
