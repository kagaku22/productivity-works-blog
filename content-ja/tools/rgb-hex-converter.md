---
title: "RGB⇔HEXカラー変換ツール"
description: "RGBとHEX、HSLを瞬時に相互変換。カラーピッカー・ライブスライダー・大型プレビュースウォッチ・ワンクリックコピー・カラー履歴（localStorage）対応の無料オンラインカラーコンバーター。"
date: 2025-11-12
categories: ["無料ツール"]
slug: "rgb-hex-converter"
ShowToc: false
aliases:
  - "/ja/tools/rgb-hex-converter/"
  - "/ja/tools/color-converter/"
cover:
  image: "/images/covers/rgb-hex-converter-ja.png"
  alt: "RGB⇔HEXカラー変換ツール"
---

<div id="rhc-app">

<style>
#rhc-app *,#rhc-app *::before,#rhc-app *::after{box-sizing:border-box;margin:0;padding:0}
#rhc-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI','Hiragino Sans','Noto Sans JP',Roboto,sans-serif;color:#1a1a2e;--accent:#6c63ff;--radius:10px;--shadow:0 4px 24px rgba(0,0,0,.10)}
#rhc-app .rhc-wrap{max-width:760px;margin:0 auto;padding:0 0 48px}
#rhc-app .rhc-lead{font-size:.97rem;color:#555;margin-bottom:28px;line-height:1.7}

/* Layout */
#rhc-app .rhc-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:24px}
@media(max-width:600px){#rhc-app .rhc-grid{grid-template-columns:1fr}}

/* Panels */
#rhc-app .rhc-panel{background:#f7f7fc;border-radius:var(--radius);padding:20px}
#rhc-app .rhc-panel h3{font-size:.78rem;font-weight:700;color:#444;text-transform:uppercase;letter-spacing:.06em;margin-bottom:14px}

/* Color picker */
#rhc-app .rhc-picker-row{display:flex;align-items:center;gap:14px;margin-bottom:18px}
#rhc-app .rhc-color-input{width:72px;height:72px;border:3px solid #ddd;border-radius:10px;cursor:pointer;padding:2px;background:#fff}
#rhc-app .rhc-hex-input{flex:1;height:44px;padding:0 14px;border:2px solid #ddd;border-radius:8px;font-size:1rem;font-family:monospace;background:#fff;outline:none;transition:border-color .2s;text-transform:uppercase}
#rhc-app .rhc-hex-input:focus{border-color:var(--accent)}

/* Preview swatch */
#rhc-app .rhc-swatch{width:100%;height:120px;border-radius:var(--radius);margin-bottom:20px;transition:background .15s;border:1px solid rgba(0,0,0,.07);box-shadow:var(--shadow)}

/* Sliders */
#rhc-app .rhc-slider-group{display:flex;flex-direction:column;gap:12px}
#rhc-app .rhc-slider-row{display:grid;grid-template-columns:18px 1fr 52px;align-items:center;gap:10px}
#rhc-app .rhc-slider-label{font-size:.85rem;font-weight:700;color:#444;text-align:center}
#rhc-app .rhc-slider{-webkit-appearance:none;appearance:none;width:100%;height:8px;border-radius:4px;outline:none;cursor:pointer}
#rhc-app .rhc-slider::-webkit-slider-thumb{-webkit-appearance:none;appearance:none;width:20px;height:20px;border-radius:50%;background:#fff;border:2px solid #aaa;box-shadow:0 1px 4px rgba(0,0,0,.2);cursor:pointer}
#rhc-app .rhc-slider::-moz-range-thumb{width:20px;height:20px;border-radius:50%;background:#fff;border:2px solid #aaa;box-shadow:0 1px 4px rgba(0,0,0,.2);cursor:pointer}
#rhc-app .slider-r{background:linear-gradient(to right,#000,#ff0000)}
#rhc-app .slider-g{background:linear-gradient(to right,#000,#00ff00)}
#rhc-app .slider-b{background:linear-gradient(to right,#000,#0000ff)}
#rhc-app .rhc-num-input{width:52px;height:34px;border:2px solid #ddd;border-radius:6px;text-align:center;font-size:.88rem;font-weight:600;outline:none;transition:border-color .2s}
#rhc-app .rhc-num-input:focus{border-color:var(--accent)}

/* Output values */
#rhc-app .rhc-outputs{display:flex;flex-direction:column;gap:10px;margin-bottom:24px}
#rhc-app .rhc-output-row{display:flex;align-items:center;gap:10px;background:#fff;border:1.5px solid #e5e7eb;border-radius:8px;padding:10px 14px}
#rhc-app .rhc-output-label{font-size:.75rem;font-weight:700;color:#6c63ff;text-transform:uppercase;letter-spacing:.05em;min-width:38px}
#rhc-app .rhc-output-val{flex:1;font-family:monospace;font-size:.92rem;color:#1a1a2e;word-break:break-all}
#rhc-app .rhc-copy-btn{flex-shrink:0;padding:5px 12px;border:none;border-radius:6px;background:#6c63ff;color:#fff;font-size:.78rem;font-weight:700;cursor:pointer;transition:opacity .2s,transform .1s}
#rhc-app .rhc-copy-btn:hover{opacity:.85}
#rhc-app .rhc-copy-btn:active{transform:scale(.95)}
#rhc-app .rhc-copy-btn.copied{background:#22c55e}

/* HSL sliders panel */
#rhc-app .rhc-hsl-panel{background:#f7f7fc;border-radius:var(--radius);padding:20px;margin-bottom:24px}
#rhc-app .rhc-hsl-panel h3{font-size:.78rem;font-weight:700;color:#444;text-transform:uppercase;letter-spacing:.06em;margin-bottom:14px}
#rhc-app .rhc-hsl-group{display:flex;flex-direction:column;gap:12px}
#rhc-app .rhc-hsl-row{display:grid;grid-template-columns:22px 1fr 60px;align-items:center;gap:10px}
#rhc-app .rhc-hsl-label{font-size:.78rem;font-weight:700;color:#444;text-align:center}
#rhc-app .slider-h{background:linear-gradient(to right,#f00,#ff0,#0f0,#0ff,#00f,#f0f,#f00)}
#rhc-app .slider-s{background:linear-gradient(to right,#888,#f00)}
#rhc-app .slider-l{background:linear-gradient(to right,#000,#888,#fff)}
#rhc-app .rhc-hsl-val{font-size:.82rem;font-weight:600;color:#555;text-align:right}

/* Color history */
#rhc-app .rhc-history{margin-bottom:0}
#rhc-app .rhc-history h3{font-size:.78rem;font-weight:700;color:#444;text-transform:uppercase;letter-spacing:.06em;margin-bottom:12px}
#rhc-app .rhc-history-swatches{display:flex;flex-wrap:wrap;gap:8px}
#rhc-app .rhc-hist-swatch{width:42px;height:42px;border-radius:8px;cursor:pointer;border:2px solid #ddd;transition:transform .15s,border-color .15s;position:relative}
#rhc-app .rhc-hist-swatch:hover{transform:scale(1.12);border-color:#6c63ff}
#rhc-app .rhc-hist-swatch .rhc-hist-tip{display:none;position:absolute;bottom:calc(100% + 6px);left:50%;transform:translateX(-50%);background:#1a1a2e;color:#fff;font-size:.7rem;white-space:nowrap;padding:3px 7px;border-radius:5px;pointer-events:none;z-index:10}
#rhc-app .rhc-hist-swatch:hover .rhc-hist-tip{display:block}
#rhc-app .rhc-history-empty{font-size:.85rem;color:#999;font-style:italic}
</style>

<div class="rhc-wrap">
  <p class="rhc-lead">RGB・HEX・HSLをリアルタイムで相互変換できる無料ツールです。カラーピッカーで色を選ぶか、HEXコードを直接入力するか、スライダーをドラッグするだけで全ての値が即座に更新されます。コピーボタンでCSS用の値を一発コピー。</p>

  <!-- Swatch -->
  <div class="rhc-swatch" id="rhcSwatch"></div>

  <!-- Picker row + HEX input -->
  <div class="rhc-panel" style="margin-bottom:20px">
    <h3>カラー入力</h3>
    <div class="rhc-picker-row">
      <input type="color" class="rhc-color-input" id="rhcColorPick" value="#6c63ff" title="カラーピッカーを開く">
      <input type="text" class="rhc-hex-input" id="rhcHexInput" value="#6C63FF" maxlength="7" placeholder="#RRGGBB" spellcheck="false">
    </div>
  </div>

  <!-- RGB sliders + HSL sliders side by side on wide screens -->
  <div class="rhc-grid">
    <!-- RGB sliders -->
    <div class="rhc-panel">
      <h3>RGBスライダー</h3>
      <div class="rhc-slider-group">
        <div class="rhc-slider-row">
          <span class="rhc-slider-label" style="color:#ef4444">R</span>
          <input type="range" class="rhc-slider slider-r" id="rhcR" min="0" max="255" value="108">
          <input type="number" class="rhc-num-input" id="rhcRNum" min="0" max="255" value="108">
        </div>
        <div class="rhc-slider-row">
          <span class="rhc-slider-label" style="color:#22c55e">G</span>
          <input type="range" class="rhc-slider slider-g" id="rhcG" min="0" max="255" value="99">
          <input type="number" class="rhc-num-input" id="rhcGNum" min="0" max="255" value="99">
        </div>
        <div class="rhc-slider-row">
          <span class="rhc-slider-label" style="color:#3b82f6">B</span>
          <input type="range" class="rhc-slider slider-b" id="rhcB" min="0" max="255" value="255">
          <input type="number" class="rhc-num-input" id="rhcBNum" min="0" max="255" value="255">
        </div>
      </div>
    </div>

    <!-- HSL sliders -->
    <div class="rhc-panel">
      <h3>HSLスライダー</h3>
      <div class="rhc-hsl-group">
        <div class="rhc-hsl-row">
          <span class="rhc-hsl-label">H</span>
          <input type="range" class="rhc-slider slider-h" id="rhcH" min="0" max="360" value="243">
          <span class="rhc-hsl-val" id="rhcHVal">243°</span>
        </div>
        <div class="rhc-hsl-row">
          <span class="rhc-hsl-label">S</span>
          <input type="range" class="rhc-slider slider-s" id="rhcS" min="0" max="100" value="100">
          <span class="rhc-hsl-val" id="rhcSVal">100%</span>
        </div>
        <div class="rhc-hsl-row">
          <span class="rhc-hsl-label">L</span>
          <input type="range" class="rhc-slider slider-l" id="rhcL" min="0" max="100" value="70">
          <span class="rhc-hsl-val" id="rhcLVal">70%</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Output values -->
  <div class="rhc-outputs" id="rhcOutputs">
    <div class="rhc-output-row">
      <span class="rhc-output-label">HEX</span>
      <span class="rhc-output-val" id="rhcOutHex">#6C63FF</span>
      <button class="rhc-copy-btn" data-target="rhcOutHex">コピー</button>
    </div>
    <div class="rhc-output-row">
      <span class="rhc-output-label">RGB</span>
      <span class="rhc-output-val" id="rhcOutRgb">rgb(108, 99, 255)</span>
      <button class="rhc-copy-btn" data-target="rhcOutRgb">コピー</button>
    </div>
    <div class="rhc-output-row">
      <span class="rhc-output-label">HSL</span>
      <span class="rhc-output-val" id="rhcOutHsl">hsl(243, 100%, 70%)</span>
      <button class="rhc-copy-btn" data-target="rhcOutHsl">コピー</button>
    </div>
  </div>

  <!-- Color history -->
  <div class="rhc-panel rhc-history" style="margin-bottom:20px">
    <h3>カラー履歴（最新10件）</h3>
    <div class="rhc-history-swatches" id="rhcHistory">
      <span class="rhc-history-empty">まだ履歴がありません。色を選ぶと自動保存されます。</span>
    </div>
  </div>

  <!-- freee CTA -->
  <div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
    <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
    <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
    <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
  </div>
</div>

<script>
(function(){
  var HIST_KEY='rhc_history';
  var els={
    pick:document.getElementById('rhcColorPick'),
    hex:document.getElementById('rhcHexInput'),
    swatch:document.getElementById('rhcSwatch'),
    r:document.getElementById('rhcR'),rn:document.getElementById('rhcRNum'),
    g:document.getElementById('rhcG'),gn:document.getElementById('rhcGNum'),
    b:document.getElementById('rhcB'),bn:document.getElementById('rhcBNum'),
    hSlider:document.getElementById('rhcH'),hVal:document.getElementById('rhcHVal'),
    sSlider:document.getElementById('rhcS'),sVal:document.getElementById('rhcSVal'),
    lSlider:document.getElementById('rhcL'),lVal:document.getElementById('rhcLVal'),
    outHex:document.getElementById('rhcOutHex'),
    outRgb:document.getElementById('rhcOutRgb'),
    outHsl:document.getElementById('rhcOutHsl'),
    histBox:document.getElementById('rhcHistory')
  };

  /* ---- Math helpers ---- */
  function clamp(v,mn,mx){return Math.min(mx,Math.max(mn,v));}
  function toHex2(n){return ('0'+Math.round(clamp(n,0,255)).toString(16)).slice(-2).toUpperCase();}

  function rgbToHex(r,g,b){return '#'+toHex2(r)+toHex2(g)+toHex2(b);}

  function hexToRgb(hex){
    var h=hex.replace('#','');
    if(h.length===3)h=h[0]+h[0]+h[1]+h[1]+h[2]+h[2];
    if(h.length!==6)return null;
    var n=parseInt(h,16);
    if(isNaN(n))return null;
    return{r:(n>>16)&255,g:(n>>8)&255,b:n&255};
  }

  function rgbToHsl(r,g,b){
    r/=255;g/=255;b/=255;
    var mx=Math.max(r,g,b),mn=Math.min(r,g,b),d=mx-mn,h,s,l=(mx+mn)/2;
    if(d===0){h=s=0;}
    else{
      s=l>0.5?d/(2-mx-mn):d/(mx+mn);
      switch(mx){
        case r:h=((g-b)/d+(g<b?6:0))/6;break;
        case g:h=((b-r)/d+2)/6;break;
        default:h=((r-g)/d+4)/6;
      }
    }
    return{h:Math.round(h*360),s:Math.round(s*100),l:Math.round(l*100)};
  }

  function hslToRgb(h,s,l){
    s/=100;l/=100;h/=360;
    var r,g,b;
    if(s===0){r=g=b=l;}
    else{
      function hue2rgb(p,q,t){if(t<0)t+=1;if(t>1)t-=1;if(t<1/6)return p+(q-p)*6*t;if(t<1/2)return q;if(t<2/3)return p+(q-p)*(2/3-t)*6;return p;}
      var q=l<0.5?l*(1+s):l+s-l*s,p=2*l-q;
      r=hue2rgb(p,q,h+1/3);g=hue2rgb(p,q,h);b=hue2rgb(p,q,h-1/3);
    }
    return{r:Math.round(r*255),g:Math.round(g*255),b:Math.round(b*255)};
  }

  /* ---- State ---- */
  var state={r:108,g:99,b:255};

  function updateAll(rgb,source){
    state.r=clamp(Math.round(rgb.r),0,255);
    state.g=clamp(Math.round(rgb.g),0,255);
    state.b=clamp(Math.round(rgb.b),0,255);
    var hex=rgbToHex(state.r,state.g,state.b);
    var hsl=rgbToHsl(state.r,state.g,state.b);

    /* swatch */
    els.swatch.style.background=hex;

    /* picker */
    if(source!=='pick')els.pick.value=hex;

    /* hex input */
    if(source!=='hex')els.hex.value=hex;

    /* RGB sliders */
    if(source!=='rgb'){
      els.r.value=state.r;els.rn.value=state.r;
      els.g.value=state.g;els.gn.value=state.g;
      els.b.value=state.b;els.bn.value=state.b;
    }

    /* HSL sliders */
    if(source!=='hsl'){
      els.hSlider.value=hsl.h;els.sSlider.value=hsl.s;els.lSlider.value=hsl.l;
    }
    els.hVal.textContent=hsl.h+'°';
    els.sVal.textContent=hsl.s+'%';
    els.lVal.textContent=hsl.l+'%';

    /* outputs */
    els.outHex.textContent=hex;
    els.outRgb.textContent='rgb('+state.r+', '+state.g+', '+state.b+')';
    els.outHsl.textContent='hsl('+hsl.h+', '+hsl.s+'%, '+hsl.l+'%)';

    /* gradient for S slider */
    var sFrom='hsl('+hsl.h+',0%,'+hsl.l+'%)';
    var sTo='hsl('+hsl.h+',100%,'+hsl.l+'%)';
    els.sSlider.style.background='linear-gradient(to right,'+sFrom+','+sTo+')';
    var lFrom='hsl('+hsl.h+','+hsl.s+'%,0%)';
    var lMid='hsl('+hsl.h+','+hsl.s+'%,50%)';
    var lTo='hsl('+hsl.h+','+hsl.s+'%,100%)';
    els.lSlider.style.background='linear-gradient(to right,'+lFrom+','+lMid+','+lTo+')';
  }

  /* ---- Event listeners ---- */
  els.pick.addEventListener('input',function(){
    var rgb=hexToRgb(this.value);
    if(rgb)updateAll(rgb,'pick');
  });
  els.pick.addEventListener('change',function(){addHistory(rgbToHex(state.r,state.g,state.b));});

  els.hex.addEventListener('input',function(){
    var v=this.value.trim();
    if(!v.startsWith('#'))v='#'+v;
    var rgb=hexToRgb(v);
    if(rgb)updateAll(rgb,'hex');
  });
  els.hex.addEventListener('blur',function(){
    addHistory(rgbToHex(state.r,state.g,state.b));
    els.hex.value=rgbToHex(state.r,state.g,state.b);
  });
  els.hex.addEventListener('keydown',function(e){if(e.key==='Enter')this.blur();});

  function rgbSliderHandler(){
    updateAll({r:+els.r.value,g:+els.g.value,b:+els.b.value},'rgb');
  }
  function rgbNumHandler(){
    els.r.value=clamp(+els.rn.value,0,255);
    els.g.value=clamp(+els.gn.value,0,255);
    els.b.value=clamp(+els.bn.value,0,255);
    updateAll({r:+els.r.value,g:+els.g.value,b:+els.b.value},'rgb');
  }
  [els.r,els.g,els.b].forEach(function(sl){sl.addEventListener('input',rgbSliderHandler);sl.addEventListener('change',function(){addHistory(rgbToHex(state.r,state.g,state.b));});});
  [els.rn,els.gn,els.bn].forEach(function(n){n.addEventListener('input',rgbNumHandler);n.addEventListener('blur',function(){addHistory(rgbToHex(state.r,state.g,state.b));});});

  function hslSliderHandler(){
    var rgb=hslToRgb(+els.hSlider.value,+els.sSlider.value,+els.lSlider.value);
    updateAll(rgb,'hsl');
  }
  [els.hSlider,els.sSlider,els.lSlider].forEach(function(sl){sl.addEventListener('input',hslSliderHandler);sl.addEventListener('change',function(){addHistory(rgbToHex(state.r,state.g,state.b));});});

  /* ---- Copy buttons ---- */
  document.querySelectorAll('#rhc-app .rhc-copy-btn').forEach(function(btn){
    btn.addEventListener('click',function(){
      var txt=document.getElementById(btn.dataset.target).textContent;
      navigator.clipboard.writeText(txt).then(function(){
        btn.textContent='コピー完了';btn.classList.add('copied');
        setTimeout(function(){btn.textContent='コピー';btn.classList.remove('copied');},1500);
      }).catch(function(){
        var ta=document.createElement('textarea');ta.value=txt;document.body.appendChild(ta);ta.select();document.execCommand('copy');document.body.removeChild(ta);
        btn.textContent='コピー完了';btn.classList.add('copied');
        setTimeout(function(){btn.textContent='コピー';btn.classList.remove('copied');},1500);
      });
    });
  });

  /* ---- History ---- */
  function loadHistory(){
    try{return JSON.parse(localStorage.getItem(HIST_KEY)||'[]');}catch(e){return[];}
  }
  function saveHistory(arr){
    try{localStorage.setItem(HIST_KEY,JSON.stringify(arr));}catch(e){}
  }
  function addHistory(hex){
    var arr=loadHistory();
    arr=arr.filter(function(h){return h!==hex;});
    arr.unshift(hex);
    arr=arr.slice(0,10);
    saveHistory(arr);
    renderHistory(arr);
  }
  function renderHistory(arr){
    if(!arr||arr.length===0){
      els.histBox.innerHTML='<span class="rhc-history-empty">まだ履歴がありません。色を選ぶと自動保存されます。</span>';
      return;
    }
    els.histBox.innerHTML='';
    arr.forEach(function(hex){
      var div=document.createElement('div');
      div.className='rhc-hist-swatch';
      div.style.background=hex;
      div.title=hex;
      var tip=document.createElement('span');
      tip.className='rhc-hist-tip';
      tip.textContent=hex;
      div.appendChild(tip);
      div.addEventListener('click',function(){
        var rgb=hexToRgb(hex);
        if(rgb){updateAll(rgb,'');addHistory(hex);}
      });
      els.histBox.appendChild(div);
    });
  }

  /* ---- Init ---- */
  renderHistory(loadHistory());
  updateAll({r:108,g:99,b:255},'');
})();
</script>

</div>

---

### 関連ツール
> カラーパレット → [カラーパレット生成](/ja/tools/color-palette-generator/)
> コントラスト確認 → [コントラストチェッカー](/ja/tools/contrast-checker/)
> 色覚シミュレーション → [色覚シミュレーター](/ja/tools/color-blindness-simulator/)
---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
