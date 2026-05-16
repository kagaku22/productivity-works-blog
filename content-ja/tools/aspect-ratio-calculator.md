---
title: "アスペクト比計算ツール – 無料オンライン"
date: 2025-05-16
description: "縦横比（アスペクト比）を簡単に計算。比率から寸法を自動算出、プリセット選択、リアルタイムプレビュー、対角線サイズ（cm/インチ）、PPI計算まで無料で利用できます。"
categories: ["無料ツール"]
slug: "aspect-ratio-calculator"
aliases: ["/ja/tools/ratio-calculator/", "/ja/tools/aspect-ratio/"]
ShowToc: false
cover:
  image: "/images/covers/aspect-ratio-calculator-ja.png"
  alt: "アスペクト比計算ツール"
---

<style>
#ar-app-ja *,#ar-app-ja *::before,#ar-app-ja *::after{box-sizing:border-box;margin:0;padding:0}
#ar-app-ja{
  font-family:-apple-system,BlinkMacSystemFont,"Hiragino Kaku Gothic ProN","Noto Sans JP",sans-serif;
  max-width:720px;color:#1e293b;
}
#ar-app-ja h2{font-size:1.05rem;font-weight:700;margin-bottom:.75rem;color:#0284c7}
#ar-app-ja .card{background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:1.25rem;margin-bottom:1.25rem}
#ar-app-ja label{display:block;font-size:.82rem;font-weight:600;color:#475569;margin-bottom:.3rem}
#ar-app-ja input[type=number]{
  width:100%;padding:.5rem .75rem;border:1.5px solid #cbd5e1;border-radius:8px;
  font-size:1rem;color:#1e293b;background:#fff;outline:none;
  transition:border-color .15s;
}
#ar-app-ja input[type=number]:focus{border-color:#0284c7}
#ar-app-ja .row{display:flex;gap:1rem;flex-wrap:wrap}
#ar-app-ja .col{flex:1;min-width:120px}
#ar-app-ja .ratio-badge{
  display:inline-block;background:#0284c7;color:#fff;
  font-size:1.4rem;font-weight:800;letter-spacing:.02em;
  padding:.35rem 1.1rem;border-radius:8px;margin-top:.6rem;
}
#ar-app-ja .ratio-exact{font-size:.8rem;color:#64748b;margin-top:.3rem}
#ar-app-ja .presets{display:flex;flex-wrap:wrap;gap:.5rem;margin-bottom:1rem}
#ar-app-ja .preset-btn{
  border:1.5px solid #0284c7;color:#0284c7;background:#fff;
  padding:.3rem .75rem;border-radius:20px;font-size:.82rem;font-weight:600;
  cursor:pointer;transition:background .15s,color .15s;
}
#ar-app-ja .preset-btn:hover,#ar-app-ja .preset-btn.active{background:#0284c7;color:#fff}
#ar-app-ja .lock-row{display:flex;align-items:center;gap:.6rem;margin-top:.5rem}
#ar-app-ja .lock-row input[type=checkbox]{width:1rem;height:1rem;accent-color:#0284c7;cursor:pointer}
#ar-app-ja .lock-row span{font-size:.82rem;color:#475569;font-weight:600}
#ar-app-ja #ar-preview-wrap-ja{
  display:flex;align-items:center;justify-content:center;
  background:#e0f2fe;border:1px solid #bae6fd;border-radius:10px;
  min-height:130px;padding:1rem;overflow:hidden;
}
#ar-app-ja #ar-rect-ja{
  background:#0284c7;border-radius:4px;
  display:flex;align-items:center;justify-content:center;
  color:#fff;font-size:.75rem;font-weight:700;letter-spacing:.03em;
  transition:width .25s,height .25s;min-width:24px;min-height:24px;
}
#ar-app-ja .result-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:.75rem;margin-top:.75rem}
#ar-app-ja .result-item{background:#fff;border:1px solid #e2e8f0;border-radius:8px;padding:.65rem .85rem}
#ar-app-ja .result-item .label{font-size:.72rem;color:#64748b;font-weight:600;text-transform:uppercase;letter-spacing:.04em}
#ar-app-ja .result-item .value{font-size:1.1rem;font-weight:700;color:#0284c7;margin-top:.15rem}
/* freee CTA */
#ar-app-ja .freee-cta{
  background:linear-gradient(135deg,#e0f2fe 0%,#f0fdf4 100%);
  border:1.5px solid #0284c7;border-radius:12px;
  padding:1.1rem 1.25rem;margin-top:.5rem;
  display:flex;align-items:center;gap:1rem;flex-wrap:wrap;
}
#ar-app-ja .freee-cta .cta-text{flex:1;min-width:180px}
#ar-app-ja .freee-cta .cta-text strong{display:block;font-size:.95rem;color:#0284c7;margin-bottom:.25rem}
#ar-app-ja .freee-cta .cta-text p{font-size:.8rem;color:#475569;line-height:1.5}
#ar-app-ja .freee-cta a.cta-btn{
  display:inline-block;background:#0284c7;color:#fff;
  padding:.5rem 1.2rem;border-radius:8px;font-weight:700;font-size:.85rem;
  text-decoration:none;white-space:nowrap;transition:background .15s;
}
#ar-app-ja .freee-cta a.cta-btn:hover{background:#0369a1}
</style>

<div id="ar-app-ja">

<!-- ① 比率の計算 -->
<div class="card">
  <h2>寸法からアスペクト比を計算</h2>
  <div class="row" style="margin-bottom:.75rem">
    <div class="col">
      <label for="arj-w">横幅（px）</label>
      <input type="number" id="arj-w" min="1" placeholder="例: 1920">
    </div>
    <div class="col">
      <label for="arj-h">縦幅（px）</label>
      <input type="number" id="arj-h" min="1" placeholder="例: 1080">
    </div>
  </div>
  <div><span class="ratio-badge" id="arj-ratio-badge">—</span></div>
  <div class="ratio-exact" id="arj-ratio-exact"></div>
  <div class="lock-row">
    <input type="checkbox" id="arj-lock">
    <span>比率を固定して片方の寸法から自動計算する</span>
  </div>
</div>

<!-- ② プリセット -->
<div class="card">
  <h2>よく使う比率プリセット</h2>
  <div class="presets" id="arj-presets">
    <button class="preset-btn" data-w="16" data-h="9">16:9</button>
    <button class="preset-btn" data-w="4" data-h="3">4:3</button>
    <button class="preset-btn" data-w="1" data-h="1">1:1</button>
    <button class="preset-btn" data-w="21" data-h="9">21:9</button>
    <button class="preset-btn" data-w="9" data-h="16">9:16</button>
    <button class="preset-btn" data-w="3" data-h="2">3:2</button>
    <button class="preset-btn" data-w="2" data-h="3">2:3</button>
  </div>

  <div id="arj-lock-inputs" style="display:none">
    <div class="row">
      <div class="col">
        <label for="arj-lw">横幅（px）</label>
        <input type="number" id="arj-lw" min="1" placeholder="横幅を入力">
      </div>
      <div class="col">
        <label for="arj-lh">縦幅（px）</label>
        <input type="number" id="arj-lh" min="1" placeholder="自動入力">
      </div>
    </div>
  </div>
</div>

<!-- ③ ビジュアルプレビュー -->
<div class="card">
  <h2>プレビュー</h2>
  <div id="ar-preview-wrap-ja">
    <div id="ar-rect-ja">?</div>
  </div>
</div>

<!-- ④ 対角線・PPI -->
<div class="card">
  <h2>対角線サイズ・PPI 計算</h2>
  <div class="row">
    <div class="col">
      <label for="arj-diag">画面の対角線サイズ（インチ）</label>
      <input type="number" id="arj-diag" min="0.1" step="0.1" placeholder="例: 27">
    </div>
  </div>
  <div class="result-grid">
    <div class="result-item"><div class="label">横幅（cm）</div><div class="value" id="arj-wcm">—</div></div>
    <div class="result-item"><div class="label">縦幅（cm）</div><div class="value" id="arj-hcm">—</div></div>
    <div class="result-item"><div class="label">横幅（インチ）</div><div class="value" id="arj-win">—</div></div>
    <div class="result-item"><div class="label">縦幅（インチ）</div><div class="value" id="arj-hin">—</div></div>
    <div class="result-item"><div class="label">PPI</div><div class="value" id="arj-ppi">—</div></div>
    <div class="result-item"><div class="label">対角線（cm）</div><div class="value" id="arj-diagcm">—</div></div>
  </div>
</div>

<!-- ⑤ freee CTA -->
<div class="freee-cta">
  <div class="cta-text">
    <strong>freee会計 — 確定申告・経費管理をかんたんに</strong>
    <p>フリーランス・個人事業主・中小企業に対応。領収書の自動読み取り、銀行連携、確定申告書の自動作成まで一括管理。</p>
  </div>
  <a class="cta-btn" href="https://www.freee.co.jp/" target="_blank" rel="noopener">無料で試してみる</a>
</div>

</div><!-- /#ar-app-ja -->

<script>
(function(){
  function gcd(a,b){return b===0?a:gcd(b,a%b);}
  function simplify(w,h){var g=gcd(Math.round(w),Math.round(h));return[Math.round(w)/g,Math.round(h)/g];}

  var lockedW=16,lockedH=9,lockOn=false;

  var elW=document.getElementById('arj-w');
  var elH=document.getElementById('arj-h');
  var elBadge=document.getElementById('arj-ratio-badge');
  var elExact=document.getElementById('arj-ratio-exact');
  var elLock=document.getElementById('arj-lock');
  var elLockInputs=document.getElementById('arj-lock-inputs');
  var elLW=document.getElementById('arj-lw');
  var elLH=document.getElementById('arj-lh');
  var elRect=document.getElementById('ar-rect-ja');
  var elDiag=document.getElementById('arj-diag');
  var elWcm=document.getElementById('arj-wcm');
  var elHcm=document.getElementById('arj-hcm');
  var elWin=document.getElementById('arj-win');
  var elHin=document.getElementById('arj-hin');
  var elPpi=document.getElementById('arj-ppi');
  var elDiagcm=document.getElementById('arj-diagcm');

  function updateRatioDisplay(w,h){
    if(!w||!h||w<=0||h<=0){elBadge.textContent='—';elExact.textContent='';updatePreview(0,0);return;}
    var s=simplify(w,h);
    elBadge.textContent=s[0]+':'+s[1];
    elExact.textContent='正確な比率: '+w+' : '+h+(s[0]!==w||s[1]!==h?' （'+w+'×'+h+'を簡約）':'');
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
    if(!d||d<=0){
      elWcm.textContent='—';elHcm.textContent='—';
      elWin.textContent='—';elHin.textContent='—';
      elPpi.textContent='—';elDiagcm.textContent='—';
      return;
    }
    var rw=w||lockedW, rh=h||lockedH;
    if(!rw||!rh)return;
    var diagRatio=Math.sqrt(rw*rw+rh*rh);
    var wIn=d*rw/diagRatio;
    var hIn=d*rh/diagRatio;
    elWin.textContent=wIn.toFixed(2)+' in';
    elHin.textContent=hIn.toFixed(2)+' in';
    elWcm.textContent=(wIn*2.54).toFixed(2)+' cm';
    elHcm.textContent=(hIn*2.54).toFixed(2)+' cm';
    elDiagcm.textContent=(d*2.54).toFixed(2)+' cm';
    if(w>0&&h>0){
      var ppi=Math.sqrt(w*w+h*h)/d;
      elPpi.textContent=Math.round(ppi)+' ppi';
    } else {
      elPpi.textContent='px寸法を入力';
    }
  }

  function onDimInput(){
    var w=parseFloat(elW.value);
    var h=parseFloat(elH.value);
    updateRatioDisplay(w,h);
  }
  elW.addEventListener('input',onDimInput);
  elH.addEventListener('input',onDimInput);

  elLock.addEventListener('change',function(){
    lockOn=this.checked;
    elLockInputs.style.display=lockOn?'block':'none';
    if(lockOn){
      var w=parseFloat(elW.value)||lockedW;
      var h=parseFloat(elH.value)||lockedH;
      var s=simplify(w,h);
      lockedW=s[0];lockedH=s[1];
      elLW.value='';elLH.value='';
    }
  });

  elLW.addEventListener('input',function(){
    var w=parseFloat(this.value);
    if(!w||w<=0){elLH.value='';return;}
    var h=Math.round(w*lockedH/lockedW);
    elLH.value=h;
    elW.value=w;elH.value=h;
    updatePreview(w,h);updateDiag();
  });
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

  document.getElementById('arj-presets').addEventListener('click',function(e){
    var btn=e.target.closest('.preset-btn');
    if(!btn)return;
    document.querySelectorAll('#ar-app-ja .preset-btn').forEach(function(b){b.classList.remove('active');});
    btn.classList.add('active');
    var pw=parseInt(btn.dataset.w);
    var ph=parseInt(btn.dataset.h);
    lockedW=pw;lockedH=ph;
    elW.value=pw;elH.value=ph;
    updateRatioDisplay(pw,ph);
    if(lockOn){elLW.value='';elLH.value='';}
  });

  elDiag.addEventListener('input',updateDiag);
})();
</script>
