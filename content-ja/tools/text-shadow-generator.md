---
title: "CSSテキストシャドウ ジェネレーター"
slug: "text-shadow-generator"
date: 2025-05-16
description: "無料のCSSテキストシャドウジェネレーター。複数シャドウ・プリセット・ライブプレビューでtext-shadowを生成しCSS即コピー。"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/text-shadow-generator-ja.png
  alt: "CSSテキストシャドウジェネレーター – 複数レイヤーとプリセットでライブプレビュー"
---

`text-shadow` CSSを即座に生成。複数のシャドウレイヤーを追加し、プリセットから選択、リアルタイムでプレビューしてワンクリックでCSSをコピーできます。

---

<div id="ts-app">
<style>
#ts-app *,#ts-app *::before,#ts-app *::after{box-sizing:border-box;margin:0;padding:0}
#ts-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans','Yu Gothic UI',Roboto,sans-serif;font-size:14px;color:#1e293b;max-width:860px}
#ts-app h2{font-size:15px;font-weight:700;margin-bottom:10px;color:#0f172a}
#ts-app .ts-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px}
@media(max-width:640px){#ts-app .ts-grid{grid-template-columns:1fr}}
#ts-app .ts-panel{background:#f8fafc;border:1.5px solid #e2e8f0;border-radius:10px;padding:16px}
#ts-app .ts-preview-wrap{background:#1e293b;border-radius:10px;padding:30px 20px;text-align:center;min-height:140px;display:flex;align-items:center;justify-content:center;margin-bottom:16px;overflow:hidden;position:relative}
#ts-app #ts-preview-text{font-weight:700;white-space:nowrap;transition:text-shadow .15s,color .15s,font-size .15s}
#ts-app .ts-ctrl-row{display:flex;align-items:center;gap:8px;margin-bottom:10px;flex-wrap:wrap}
#ts-app .ts-ctrl-row label{min-width:90px;font-size:13px;color:#475569}
#ts-app input[type=range]{flex:1;min-width:80px;accent-color:#6366f1}
#ts-app input[type=color]{width:36px;height:28px;border:1.5px solid #cbd5e1;border-radius:5px;cursor:pointer;padding:1px}
#ts-app input[type=text]{border:1.5px solid #cbd5e1;border-radius:6px;padding:5px 8px;font-size:13px;width:100%;background:#fff}
#ts-app select{border:1.5px solid #cbd5e1;border-radius:6px;padding:5px 8px;font-size:13px;background:#fff;cursor:pointer}
#ts-app .ts-val{min-width:36px;text-align:right;font-size:12px;color:#64748b}
#ts-app .ts-btn{display:inline-flex;align-items:center;gap:6px;padding:8px 16px;border-radius:7px;font-size:13px;font-weight:600;border:none;cursor:pointer;transition:opacity .15s}
#ts-app .ts-btn-primary{background:#6366f1;color:#fff}
#ts-app .ts-btn-primary:hover{opacity:.88}
#ts-app .ts-btn-sm{padding:5px 11px;font-size:12px;background:#fff;border:1.5px solid #cbd5e1;color:#374151;border-radius:6px}
#ts-app .ts-btn-sm:hover{background:#f1f5f9}
#ts-app .ts-btn-danger{background:#fff;border:1.5px solid #fca5a5;color:#dc2626;padding:5px 10px;font-size:12px;border-radius:6px}
#ts-app .ts-btn-danger:hover{background:#fef2f2}
#ts-app .ts-layers{display:flex;flex-direction:column;gap:8px;margin-bottom:12px}
#ts-app .ts-layer-card{background:#fff;border:1.5px solid #e2e8f0;border-radius:8px;padding:12px}
#ts-app .ts-layer-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
#ts-app .ts-layer-title{font-size:13px;font-weight:600;color:#334155}
#ts-app .ts-presets{display:flex;flex-wrap:wrap;gap:7px;margin-bottom:14px}
#ts-app .ts-preset-btn{padding:6px 13px;border-radius:20px;border:1.5px solid #cbd5e1;background:#fff;font-size:12px;font-weight:600;cursor:pointer;transition:border-color .15s,background .15s}
#ts-app .ts-preset-btn:hover{border-color:#6366f1;background:#eef2ff}
#ts-app .ts-code-wrap{position:relative;background:#0f172a;border-radius:8px;padding:14px 14px 14px 14px;margin-top:4px}
#ts-app .ts-code{color:#7dd3fc;font-family:'Courier New',monospace;font-size:12.5px;word-break:break-all;white-space:pre-wrap;line-height:1.6}
#ts-app .ts-copy-btn{position:absolute;top:10px;right:10px;padding:5px 12px;background:#6366f1;color:#fff;border:none;border-radius:6px;font-size:12px;font-weight:600;cursor:pointer}
#ts-app .ts-copy-btn:hover{background:#4f46e5}
#ts-app .ts-copy-btn.copied{background:#10b981}
#ts-app .ts-preview-controls{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:14px;align-items:center}
#ts-app .ts-preview-controls label{font-size:13px;color:#475569}
#ts-app .ts-sep{border:none;border-top:1.5px solid #e2e8f0;margin:14px 0}
#ts-app .ts-add-row{display:flex;gap:8px;flex-wrap:wrap;align-items:center}
</style>

<!-- ライブプレビュー -->
<div class="ts-panel" style="margin-bottom:16px">
  <h2>ライブプレビュー</h2>
  <div class="ts-preview-wrap" id="ts-preview-bg">
    <span id="ts-preview-text">テキスト シャドウ</span>
  </div>
  <div class="ts-preview-controls">
    <label>テキスト：</label>
    <input type="text" id="ts-input-text" value="テキスト シャドウ" style="width:180px">
    <label>文字色：</label>
    <input type="color" id="ts-input-textcolor" value="#ffffff">
    <label>サイズ：</label>
    <input type="range" id="ts-input-fontsize" min="16" max="96" value="48" style="width:100px">
    <span class="ts-val" id="ts-fontsize-val">48px</span>
    <label>背景：</label>
    <input type="color" id="ts-input-bg" value="#1e293b">
  </div>
</div>

<!-- プリセット -->
<div class="ts-panel" style="margin-bottom:16px">
  <h2>プリセット</h2>
  <div class="ts-presets" id="ts-presets"></div>
</div>

<!-- レイヤー + CSS出力 -->
<div class="ts-grid">
  <div class="ts-panel">
    <h2>シャドウレイヤー</h2>
    <div class="ts-layers" id="ts-layers"></div>
    <div class="ts-add-row">
      <button class="ts-btn ts-btn-primary" onclick="tsAddLayer()">＋ レイヤーを追加</button>
    </div>
  </div>
  <div class="ts-panel">
    <h2>生成されたCSS</h2>
    <div class="ts-code-wrap">
      <pre class="ts-code" id="ts-css-out"></pre>
      <button class="ts-copy-btn" id="ts-copy-btn" onclick="tsCopy()">コピー</button>
    </div>
  </div>
</div>

<script>
(function(){
  var layers=[];
  var lid=0;

  var PRESETS=[
    {name:"ネオングロー",layers:[
      {h:0,v:0,b:4,c:"#ff00ff",a:1},
      {h:0,v:0,b:16,c:"#ff00ff",a:.8},
      {h:0,v:0,b:32,c:"#ff00ff",a:.4}
    ],bg:"#0a0a1a",tc:"#ff00ff",fs:48},
    {name:"エンボス",layers:[
      {h:-2,v:-2,b:4,c:"#ffffff",a:.9},
      {h:2,v:2,b:4,c:"#000000",a:.4}
    ],bg:"#c0c8d8",tc:"#c0c8d8",fs:48},
    {name:"レトロ",layers:[
      {h:3,v:3,b:0,c:"#f97316",a:1},
      {h:6,v:6,b:0,c:"#ef4444",a:1}
    ],bg:"#fef9c3",tc:"#1e293b",fs:48},
    {name:"ファイア",layers:[
      {h:0,v:-4,b:8,c:"#fbbf24",a:1},
      {h:0,v:-8,b:16,c:"#f97316",a:.9},
      {h:0,v:-16,b:24,c:"#ef4444",a:.6},
      {h:0,v:-24,b:32,c:"#dc2626",a:.3}
    ],bg:"#18181b",tc:"#fef9c3",fs:48},
    {name:"3D",layers:[
      {h:1,v:1,b:0,c:"#475569",a:1},
      {h:2,v:2,b:0,c:"#64748b",a:1},
      {h:3,v:3,b:0,c:"#94a3b8",a:1},
      {h:4,v:4,b:0,c:"#cbd5e1",a:1}
    ],bg:"#1e293b",tc:"#f8fafc",fs:48},
    {name:"アウトライン",layers:[
      {h:1,v:0,b:0,c:"#000000",a:1},
      {h:-1,v:0,b:0,c:"#000000",a:1},
      {h:0,v:1,b:0,c:"#000000",a:1},
      {h:0,v:-1,b:0,c:"#000000",a:1}
    ],bg:"#f8fafc",tc:"#6366f1",fs:48}
  ];

  function hexToRgba(hex,a){
    var r=parseInt(hex.slice(1,3),16),g=parseInt(hex.slice(3,5),16),b=parseInt(hex.slice(5,7),16);
    return a<1?'rgba('+r+','+g+','+b+','+a+')':'rgb('+r+','+g+','+b+')';
  }

  function makeCss(){
    if(!layers.length)return'text-shadow: none;';
    var parts=layers.map(function(l){
      return l.h+'px '+l.v+'px '+l.b+'px '+hexToRgba(l.c,l.a);
    });
    return'text-shadow:\n  '+parts.join(',\n  ')+';';
  }

  function applyPreview(){
    var text=document.getElementById('ts-input-text').value||'テキスト シャドウ';
    var tc=document.getElementById('ts-input-textcolor').value;
    var fs=document.getElementById('ts-input-fontsize').value;
    var bg=document.getElementById('ts-input-bg').value;
    document.getElementById('ts-fontsize-val').textContent=fs+'px';
    var el=document.getElementById('ts-preview-text');
    el.textContent=text;
    el.style.color=tc;
    el.style.fontSize=fs+'px';
    el.style.textShadow=layers.map(function(l){
      return l.h+'px '+l.v+'px '+l.b+'px '+hexToRgba(l.c,l.a);
    }).join(', ')||'none';
    document.getElementById('ts-preview-bg').style.background=bg;
    document.getElementById('ts-css-out').textContent=makeCss();
  }

  function renderLayers(){
    var cont=document.getElementById('ts-layers');
    cont.innerHTML='';
    if(!layers.length){
      cont.innerHTML='<p style="color:#94a3b8;font-size:13px;text-align:center;padding:16px 0;">レイヤーがありません。追加またはプリセットを選択してください。</p>';
      return;
    }
    layers.forEach(function(l,i){
      var d=document.createElement('div');
      d.className='ts-layer-card';
      d.innerHTML='<div class="ts-layer-header"><span class="ts-layer-title">レイヤー '+(i+1)+'</span><button class="ts-btn ts-btn-danger" onclick="tsRemoveLayer('+l.id+')">削除</button></div>'+
        '<div class="ts-ctrl-row"><label>水平オフセット</label><input type="range" min="-50" max="50" value="'+l.h+'" oninput="tsLayerChange('+l.id+',\'h\',this.value);document.getElementById(\'ts-h-val-'+l.id+'\').textContent=this.value+\'px\'"><span class="ts-val" id="ts-h-val-'+l.id+'">'+l.h+'px</span></div>'+
        '<div class="ts-ctrl-row"><label>垂直オフセット</label><input type="range" min="-50" max="50" value="'+l.v+'" oninput="tsLayerChange('+l.id+',\'v\',this.value);document.getElementById(\'ts-v-val-'+l.id+'\').textContent=this.value+\'px\'"><span class="ts-val" id="ts-v-val-'+l.id+'">'+l.v+'px</span></div>'+
        '<div class="ts-ctrl-row"><label>ぼかし半径</label><input type="range" min="0" max="60" value="'+l.b+'" oninput="tsLayerChange('+l.id+',\'b\',this.value);document.getElementById(\'ts-b-val-'+l.id+'\').textContent=this.value+\'px\'"><span class="ts-val" id="ts-b-val-'+l.id+'">'+l.b+'px</span></div>'+
        '<div class="ts-ctrl-row"><label>カラー</label><input type="color" value="'+l.c+'" oninput="tsLayerChange('+l.id+',\'c\',this.value)"></div>'+
        '<div class="ts-ctrl-row"><label>不透明度</label><input type="range" min="0" max="1" step="0.01" value="'+l.a+'" oninput="tsLayerChange('+l.id+',\'a\',parseFloat(this.value));document.getElementById(\'ts-a-val-'+l.id+'\').textContent=parseFloat(this.value).toFixed(2)"><span class="ts-val" id="ts-a-val-'+l.id+'">'+l.a.toFixed(2)+'</span></div>';
      cont.appendChild(d);
    });
  }

  window.tsAddLayer=function(){
    layers.push({id:lid++,h:2,v:2,b:4,c:'#000000',a:0.5});
    renderLayers();applyPreview();
  };

  window.tsRemoveLayer=function(id){
    layers=layers.filter(function(l){return l.id!==id;});
    renderLayers();applyPreview();
  };

  window.tsLayerChange=function(id,prop,val){
    var l=layers.find(function(x){return x.id===id;});
    if(l){l[prop]=prop==='h'||prop==='v'||prop==='b'?parseInt(val,10):val;}
    applyPreview();
  };

  window.tsCopy=function(){
    var txt=makeCss();
    if(navigator.clipboard){navigator.clipboard.writeText(txt);}else{var ta=document.createElement('textarea');ta.value=txt;document.body.appendChild(ta);ta.select();document.execCommand('copy');document.body.removeChild(ta);}
    var btn=document.getElementById('ts-copy-btn');
    btn.textContent='コピー済！';btn.classList.add('copied');
    setTimeout(function(){btn.textContent='コピー';btn.classList.remove('copied');},1800);
  };

  // プリセットボタン描画
  var pb=document.getElementById('ts-presets');
  PRESETS.forEach(function(p){
    var b=document.createElement('button');
    b.className='ts-preset-btn';b.textContent=p.name;
    b.onclick=function(){
      layers=p.layers.map(function(l){return Object.assign({id:lid++},l);});
      document.getElementById('ts-input-bg').value=p.bg;
      document.getElementById('ts-input-textcolor').value=p.tc;
      document.getElementById('ts-input-fontsize').value=p.fs;
      document.getElementById('ts-fontsize-val').textContent=p.fs+'px';
      renderLayers();applyPreview();
    };
    pb.appendChild(b);
  });

  // プレビューコントロール
  ['ts-input-text','ts-input-textcolor','ts-input-fontsize','ts-input-bg'].forEach(function(id){
    document.getElementById(id).addEventListener('input',applyPreview);
  });

  // 初期表示：ネオングロー
  (function(){
    var p=PRESETS[0];
    layers=p.layers.map(function(l){return Object.assign({id:lid++},l);});
    document.getElementById('ts-input-bg').value=p.bg;
    document.getElementById('ts-input-textcolor').value=p.tc;
    document.getElementById('ts-input-fontsize').value=p.fs;
    document.getElementById('ts-fontsize-val').textContent=p.fs+'px';
    renderLayers();applyPreview();
  })();
})();
</script>
</div>

---

## 使い方

1. **レイヤーを追加** — 「レイヤーを追加」をクリックするか、プリセットを選択して即座にシャドウレイヤーを読み込みます。
2. **各レイヤーを調整** — 水平・垂直オフセット、ぼかし半径、カラー、不透明度のスライダーを操作します。
3. **プレビューをカスタマイズ** — プレビューテキスト・文字色・フォントサイズ・背景色を変更できます。
4. **CSSをコピー** — 「コピー」をクリックして `text-shadow` ルールをスタイルシートに貼り付けます。

## プリセット一覧

| プリセット | 効果 |
|---|---|
| ネオングロー | 同じ色相に拡大するぼかしを重ねた発光エフェクト |
| エンボス | 明暗のシャドウで浮き彫り・くぼみ感を表現 |
| レトロ | ハードに積み重なるシャドウでヴィンテージ印刷風に |
| ファイア | 黄色から深紅へのグラデーションで炎を表現 |
| 3D | 段差状のソリッドシャドウで立体感を演出 |
| アウトライン | 4方向の1pxシャドウでテキストのふち取りを実現 |

## CSS `text-shadow` の書式

```css
text-shadow: 水平 垂直 ぼかし カラー, /* レイヤー1 */
             水平 垂直 ぼかし カラー; /* レイヤー2 */
```

- **水平オフセット** — 正の値で右方向、負の値で左方向
- **垂直オフセット** — 正の値で下方向、負の値で上方向
- **ぼかし半径** — 大きいほど滑らか（0はシャープなシャドウ）
- **カラー** — `rgba()` も使用可能。透明度を指定してシャドウを重ねるのがコツ

複数のシャドウはカンマで区切り、前から後ろの順で重なります。

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">Web制作の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、デザインツール費用の経費精算もクラウドで一元管理。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

---

## 関連ツール

- [ボックスシャドウ ジェネレーター](/ja/tools/box-shadow-generator/) — 要素・カードの `box-shadow` CSSを生成
- [テキストグラデーション ジェネレーター](/ja/tools/text-gradient-generator/) — `background-clip` を使ったテキストグラデーションをライブプレビューで生成
