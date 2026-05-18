---
title: "CSSカーソル ギャラリー"
slug: "css-cursor-gallery"
date: 2025-11-19
description: "無料のCSSカーソルリファレンス。30種類以上のCSSカーソル値をホバーでプレビュー。CSSコードをワンクリックでコピー。"
categories: ["無料ツール"]
tags: ["CSS", "カーソル", "リファレンス", "Webデザイン", "フロントエンド"]
cover:
  image: "/images/covers/css-cursor-gallery-ja.png"
  alt: "CSSカーソル ギャラリー"
ShowToc: false
---

CSSの `cursor` プロパティで使える全カーソル値を一覧で確認。カードにホバーしてカーソルをプレビューし、ボタンをクリックしてCSSをコピーできます。検索・カテゴリーで絞り込みも可能。カスタムカーソルのCSS生成ツールも内蔵しています。

<div id="cu-app">
<style>
#cu-app *,#cu-app *::before,#cu-app *::after{box-sizing:border-box;margin:0;padding:0}
#cu-app{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans','Noto Sans JP',sans-serif;color:#1e293b;max-width:960px;margin:0 auto;padding:0 0 48px}
#cu-app h2{display:none}

/* ── controls ── */
#cu-controls{display:flex;flex-wrap:wrap;gap:10px;margin-bottom:20px;align-items:center}
#cu-search{flex:1;min-width:180px;padding:9px 14px;border:1.5px solid #cbd5e1;border-radius:8px;font-size:14px;outline:none;transition:border-color .2s}
#cu-search:focus{border-color:#6366f1}
#cu-cats{display:flex;flex-wrap:wrap;gap:6px}
.cu-cat{padding:6px 14px;border:1.5px solid #cbd5e1;border-radius:20px;background:#fff;font-size:13px;cursor:pointer;transition:all .15s}
.cu-cat:hover{border-color:#6366f1;color:#6366f1}
.cu-cat.active{background:#6366f1;border-color:#6366f1;color:#fff}

/* ── grid ── */
#cu-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(148px,1fr));gap:12px}
.cu-card{position:relative;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:8px;height:110px;border:1.5px solid #e2e8f0;border-radius:10px;background:#f8fafc;transition:border-color .15s,box-shadow .15s;user-select:none}
.cu-card:hover{border-color:#6366f1;box-shadow:0 2px 12px rgba(99,102,241,.15)}
.cu-icon{font-size:22px;pointer-events:none}
.cu-name{font-size:12px;font-weight:600;color:#475569;pointer-events:none}
.cu-copy-btn{padding:3px 10px;font-size:11px;border:1px solid #cbd5e1;border-radius:5px;background:#fff;color:#6366f1;cursor:pointer;transition:all .15s;pointer-events:auto}
.cu-copy-btn:hover{background:#6366f1;color:#fff;border-color:#6366f1}
.cu-copied{position:absolute;top:6px;right:8px;font-size:10px;color:#22c55e;font-weight:700;opacity:0;transition:opacity .3s}
.cu-copied.show{opacity:1}
.cu-no-results{grid-column:1/-1;text-align:center;padding:40px;color:#94a3b8;font-size:15px}

/* ── custom builder ── */
#cu-builder{margin-top:36px;border:1.5px solid #e2e8f0;border-radius:12px;overflow:hidden}
#cu-builder-header{background:#6366f1;color:#fff;padding:14px 20px;font-size:15px;font-weight:700;display:flex;align-items:center;gap:8px}
#cu-builder-body{padding:20px;display:grid;grid-template-columns:1fr 1fr;gap:20px}
@media(max-width:600px){#cu-builder-body{grid-template-columns:1fr}}
.cu-b-label{font-size:13px;font-weight:600;color:#475569;display:block;margin-bottom:5px}
.cu-b-input{width:100%;padding:8px 11px;border:1.5px solid #cbd5e1;border-radius:7px;font-size:13px;outline:none;transition:border-color .2s}
.cu-b-input:focus{border-color:#6366f1}
#cu-preview-area{display:flex;align-items:center;justify-content:center;height:120px;border:2px dashed #cbd5e1;border-radius:8px;font-size:13px;color:#94a3b8;transition:border-color .2s}
#cu-preview-area:hover{border-color:#6366f1}
#cu-output{background:#1e293b;color:#e2e8f0;border-radius:8px;padding:14px;font-family:'Fira Code',Consolas,monospace;font-size:12.5px;white-space:pre-wrap;word-break:break-all;min-height:60px;margin-top:0}
#cu-copy-output{margin-top:8px;padding:8px 16px;background:#6366f1;color:#fff;border:none;border-radius:7px;font-size:13px;font-weight:600;cursor:pointer;transition:background .15s}
#cu-copy-output:hover{background:#4f46e5}
#cu-upload-label{display:inline-flex;align-items:center;gap:6px;padding:8px 14px;background:#f1f5f9;border:1.5px dashed #cbd5e1;border-radius:7px;font-size:13px;cursor:pointer;transition:border-color .2s}
#cu-upload-label:hover{border-color:#6366f1}
#cu-file-input{display:none}
#cu-img-preview{max-width:64px;max-height:64px;margin-top:8px;border-radius:4px;display:none}

/* ── cross-links ── */
#cu-links{margin-top:32px;display:flex;flex-wrap:wrap;gap:10px}
.cu-link-card{flex:1;min-width:180px;padding:14px 18px;border:1.5px solid #e2e8f0;border-radius:10px;text-decoration:none;color:#1e293b;transition:border-color .15s,box-shadow .15s}
.cu-link-card:hover{border-color:#6366f1;box-shadow:0 2px 10px rgba(99,102,241,.12)}
.cu-link-card span{display:block;font-size:11px;color:#94a3b8;margin-bottom:3px}
.cu-link-card strong{font-size:14px;font-weight:700;color:#6366f1}

/* ── freee CTA ── */
#cu-freee-cta{margin-top:40px;background:linear-gradient(135deg,#e0f2fe 0%,#ede9fe 100%);border:1.5px solid #bae6fd;border-radius:12px;padding:24px 28px;display:flex;flex-wrap:wrap;align-items:center;gap:18px}
#cu-freee-cta .cu-freee-text{flex:1;min-width:200px}
#cu-freee-cta .cu-freee-text h3{font-size:16px;font-weight:700;color:#0369a1;margin-bottom:6px}
#cu-freee-cta .cu-freee-text p{font-size:13px;color:#475569;line-height:1.6}
#cu-freee-cta a.cu-freee-btn{display:inline-block;padding:11px 22px;background:#0ea5e9;color:#fff;border-radius:8px;font-size:14px;font-weight:700;text-decoration:none;white-space:nowrap;transition:background .15s}
#cu-freee-cta a.cu-freee-btn:hover{background:#0284c7}

/* ── A8 footer ── */
#cu-a8-footer{margin-top:16px;font-size:11px;color:#94a3b8;text-align:center;line-height:1.7}
#cu-a8-footer a{color:#94a3b8}
</style>

<!-- Controls -->
<div id="cu-controls">
  <input id="cu-search" type="search" placeholder="カーソル名で検索…" autocomplete="off">
  <div id="cu-cats">
    <button class="cu-cat active" data-cat="all">すべて</button>
    <button class="cu-cat" data-cat="general">基本</button>
    <button class="cu-cat" data-cat="links">リンク・状態</button>
    <button class="cu-cat" data-cat="selection">テキスト選択</button>
    <button class="cu-cat" data-cat="dnd">ドラッグ＆ドロップ</button>
    <button class="cu-cat" data-cat="resize">リサイズ</button>
    <button class="cu-cat" data-cat="zoom">ズーム</button>
  </div>
</div>

<!-- Card Grid -->
<div id="cu-grid"></div>

<!-- Custom Cursor Builder -->
<div id="cu-builder">
  <div id="cu-builder-header">&#9881; カスタムカーソル CSS ジェネレーター</div>
  <div id="cu-builder-body">
    <div>
      <label class="cu-b-label">カーソル画像をアップロード（PNG・ICO・SVG）</label>
      <label id="cu-upload-label" for="cu-file-input">&#128247; 画像を選択</label>
      <input id="cu-file-input" type="file" accept="image/png,image/x-icon,image/svg+xml,image/gif">
      <img id="cu-img-preview" alt="カーソルプレビュー">
      <br>
      <label class="cu-b-label" style="margin-top:14px">ホットスポット X（px）</label>
      <input id="cu-hx" class="cu-b-input" type="number" value="0" min="0" max="128">
      <label class="cu-b-label" style="margin-top:10px">ホットスポット Y（px）</label>
      <input id="cu-hy" class="cu-b-input" type="number" value="0" min="0" max="128">
      <label class="cu-b-label" style="margin-top:10px">フォールバックカーソル</label>
      <select id="cu-fallback" class="cu-b-input">
        <option value="auto">auto</option>
        <option value="default">default</option>
        <option value="pointer" selected>pointer</option>
        <option value="crosshair">crosshair</option>
        <option value="move">move</option>
        <option value="grab">grab</option>
        <option value="none">none</option>
      </select>
    </div>
    <div style="display:flex;flex-direction:column;gap:12px">
      <div>
        <label class="cu-b-label">プレビュー（ここにホバー）</label>
        <div id="cu-preview-area">ここにホバーしてカーソルを確認</div>
      </div>
      <div>
        <label class="cu-b-label">生成されたCSS</label>
        <div id="cu-output">/* 画像をアップロードするとCSSが生成されます */</div>
        <button id="cu-copy-output">CSSをコピー</button>
      </div>
    </div>
  </div>
</div>

<!-- Cross-links -->
<div id="cu-links">
  <a class="cu-link-card" href="/ja/tools/css-animation-generator/">
    <span>CSSアニメーション</span>
    <strong>CSSアニメーションジェネレーター</strong>
  </a>
  <a class="cu-link-card" href="/ja/tools/css-button-generator/">
    <span>CSSボタン</span>
    <strong>CSSボタンジェネレーター</strong>
  </a>
</div>

<!-- freee CTA -->
<div id="cu-freee-cta">
  <div class="cu-freee-text">
    <h3>フリーランス・個人事業主の方へ：会計をもっとラクに</h3>
    <p>Webデザイン・フロントエンド案件の請求書・経費管理は <strong>freee</strong> でまとめて自動化。確定申告もかんたんに。</p>
  </div>
  <a class="cu-freee-btn" href="https://px.a8.net/svt/ejp?a8mat=3Z2T6K+XXXXXXX+XXXX+XXXX" rel="nofollow noopener" target="_blank">freee を無料で試す</a>
</div>

<div id="cu-a8-footer">
  <p>※本ページにはアフィリエイト広告（A8.net）が含まれます。<a href="/ja/disclosure/">広告掲載ポリシー</a></p>
</div>

<script>
(function(){
'use strict';

const CURSORS = [
  // 基本
  {name:'auto',       cat:'general', icon:'🖱️'},
  {name:'default',    cat:'general', icon:'↖️'},
  {name:'none',       cat:'general', icon:'🚫'},
  // リンク・状態
  {name:'context-menu', cat:'links', icon:'📋'},
  {name:'help',         cat:'links', icon:'❓'},
  {name:'pointer',      cat:'links', icon:'👆'},
  {name:'progress',     cat:'links', icon:'⏳'},
  {name:'wait',         cat:'links', icon:'⌛'},
  // テキスト選択
  {name:'cell',          cat:'selection', icon:'⊞'},
  {name:'crosshair',     cat:'selection', icon:'✛'},
  {name:'text',          cat:'selection', icon:'I'},
  {name:'vertical-text', cat:'selection', icon:'⌶'},
  // ドラッグ＆ドロップ
  {name:'alias',       cat:'dnd', icon:'↗️'},
  {name:'copy',        cat:'dnd', icon:'📄'},
  {name:'move',        cat:'dnd', icon:'✥'},
  {name:'no-drop',     cat:'dnd', icon:'🚫'},
  {name:'not-allowed', cat:'dnd', icon:'⛔'},
  {name:'grab',        cat:'dnd', icon:'🖐'},
  {name:'grabbing',    cat:'dnd', icon:'✊'},
  {name:'all-scroll',  cat:'dnd', icon:'⊹'},
  // リサイズ
  {name:'col-resize',   cat:'resize', icon:'↔'},
  {name:'row-resize',   cat:'resize', icon:'↕'},
  {name:'n-resize',     cat:'resize', icon:'↑'},
  {name:'e-resize',     cat:'resize', icon:'→'},
  {name:'s-resize',     cat:'resize', icon:'↓'},
  {name:'w-resize',     cat:'resize', icon:'←'},
  {name:'ne-resize',    cat:'resize', icon:'↗'},
  {name:'nw-resize',    cat:'resize', icon:'↖'},
  {name:'se-resize',    cat:'resize', icon:'↘'},
  {name:'sw-resize',    cat:'resize', icon:'↙'},
  {name:'ew-resize',    cat:'resize', icon:'↔'},
  {name:'ns-resize',    cat:'resize', icon:'↕'},
  {name:'nesw-resize',  cat:'resize', icon:'↗↙'},
  {name:'nwse-resize',  cat:'resize', icon:'↖↘'},
  // ズーム
  {name:'zoom-in',  cat:'zoom', icon:'🔍'},
  {name:'zoom-out', cat:'zoom', icon:'🔎'},
];

let currentCat = 'all';
let searchTerm = '';

const grid = document.getElementById('cu-grid');
const searchEl = document.getElementById('cu-search');
const catBtns = document.querySelectorAll('.cu-cat');

function cssSnippet(name){ return `cursor: ${name};`; }

function renderGrid(){
  const q = searchTerm.toLowerCase();
  const filtered = CURSORS.filter(c =>
    (currentCat === 'all' || c.cat === currentCat) &&
    c.name.includes(q)
  );
  grid.innerHTML = '';
  if(!filtered.length){
    grid.innerHTML = '<div class="cu-no-results">該当するカーソルが見つかりません。</div>';
    return;
  }
  filtered.forEach(c => {
    const card = document.createElement('div');
    card.className = 'cu-card';
    card.style.cursor = c.name;
    card.innerHTML = `
      <span class="cu-icon">${c.icon}</span>
      <span class="cu-name">${c.name}</span>
      <button class="cu-copy-btn" data-name="${c.name}">CSSをコピー</button>
      <span class="cu-copied" id="cp-${c.name.replace(/[^a-z]/g,'-')}">コピー完了!</span>
    `;
    card.querySelector('.cu-copy-btn').addEventListener('click', e => {
      e.stopPropagation();
      const snippet = cssSnippet(c.name);
      navigator.clipboard.writeText(snippet).catch(()=>{
        const ta = document.createElement('textarea');
        ta.value = snippet; document.body.appendChild(ta);
        ta.select(); document.execCommand('copy');
        document.body.removeChild(ta);
      });
      const badge = card.querySelector('.cu-copied');
      badge.classList.add('show');
      setTimeout(()=>badge.classList.remove('show'), 1500);
    });
    grid.appendChild(card);
  });
}

catBtns.forEach(btn => {
  btn.addEventListener('click', ()=>{
    catBtns.forEach(b=>b.classList.remove('active'));
    btn.classList.add('active');
    currentCat = btn.dataset.cat;
    renderGrid();
  });
});

searchEl.addEventListener('input', ()=>{
  searchTerm = searchEl.value;
  renderGrid();
});

// ── カスタムカーソルビルダー ──
const fileInput   = document.getElementById('cu-file-input');
const imgPreview  = document.getElementById('cu-img-preview');
const hxInput     = document.getElementById('cu-hx');
const hyInput     = document.getElementById('cu-hy');
const fallback    = document.getElementById('cu-fallback');
const previewArea = document.getElementById('cu-preview-area');
const output      = document.getElementById('cu-output');
const copyOutput  = document.getElementById('cu-copy-output');
let dataUrl = null;

function updateBuilder(){
  if(!dataUrl) return;
  const hx = parseInt(hxInput.value)||0;
  const hy = parseInt(hyInput.value)||0;
  const fb = fallback.value;
  const css = `cursor: url('${dataUrl}') ${hx} ${hy}, ${fb};`;
  output.textContent = css;
  previewArea.style.cursor = `url('${dataUrl}') ${hx} ${hy}, ${fb}`;
}

fileInput.addEventListener('change', ()=>{
  const file = fileInput.files[0];
  if(!file) return;
  const reader = new FileReader();
  reader.onload = e => {
    dataUrl = e.target.result;
    imgPreview.src = dataUrl;
    imgPreview.style.display = 'block';
    updateBuilder();
  };
  reader.readAsDataURL(file);
});

[hxInput, hyInput, fallback].forEach(el => el.addEventListener('input', updateBuilder));

copyOutput.addEventListener('click', ()=>{
  const text = output.textContent;
  if(text.startsWith('/*')) return;
  navigator.clipboard.writeText(text).catch(()=>{
    const ta = document.createElement('textarea');
    ta.value = text; document.body.appendChild(ta);
    ta.select(); document.execCommand('copy');
    document.body.removeChild(ta);
  });
  copyOutput.textContent = 'コピー完了!';
  setTimeout(()=>{ copyOutput.textContent = 'CSSをコピー'; }, 1500);
});

renderGrid();
})();
</script>
</div>

## CSSカーソルの使い方

`cursor` プロパティは任意の要素に設定できます：

```css
/* キーワード指定 */
.btn { cursor: pointer; }

/* カスタム画像カーソル */
.custom { cursor: url('/cursors/my-cursor.png') 0 0, auto; }
```

カスタムカーソルは `url()` の後にホットスポット座標（クリック判定位置）を `x y` の順で指定し、最後にキーワード（`auto` や `pointer` など）をフォールバックとして書きます。

## ブラウザ対応

上記のすべてのキーワード値は Chrome・Firefox・Safari・Edge の最新版でサポートされています。カスタム URL カーソルは PNG・SVG・ICO 形式に対応しており、推奨最大サイズは **128×128 px** です。

---

**関連ツール：** [CSSアニメーションジェネレーター](/ja/tools/css-animation-generator/) &nbsp;|&nbsp; [CSSボタンジェネレーター](/ja/tools/css-button-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

