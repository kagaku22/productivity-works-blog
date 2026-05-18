---
title: "アスキーアートジェネレーター"
date: 2025-12-28
description: "無料のアスキーアート作成ツール。テキストを大きなASCIIアートバナーに変換。5種類のフォントスタイル対応、コピー機能付き、会員登録不要。"
categories: ["無料ツール"]
slug: "ascii-art-generator"
ShowToc: false
cover:
  image: "/images/covers/ascii-art-generator-ja.png"
  alt: "アスキーアートジェネレーター"
---

<div id="aa-app">
<style>
#aa-app *,#aa-app *::before,#aa-app *::after{box-sizing:border-box;margin:0;padding:0;}
#aa-app{font-family:'Helvetica Neue',Arial,'Hiragino Kaku Gothic ProN','Hiragino Sans',Meiryo,sans-serif;color:#1e293b;background:#f8fafc;border-radius:12px;padding:24px;max-width:860px;margin:0 auto;}
#aa-app h2{font-size:1.4rem;font-weight:700;color:#0f172a;margin-bottom:4px;}
#aa-app .aa-subtitle{font-size:0.88rem;color:#64748b;margin-bottom:20px;}
#aa-app .aa-section{margin-bottom:16px;}
#aa-app label.aa-label{display:block;font-size:0.82rem;font-weight:600;color:#475569;margin-bottom:6px;}
#aa-app textarea#aa-input{width:100%;padding:10px 12px;border:1.5px solid #cbd5e1;border-radius:8px;font-size:1rem;resize:vertical;min-height:64px;background:#fff;color:#1e293b;outline:none;transition:border-color .2s;}
#aa-app textarea#aa-input:focus{border-color:#3b82f6;}
#aa-app .aa-font-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:8px;}
#aa-app .aa-font-btn{padding:8px 10px;border:1.5px solid #cbd5e1;border-radius:8px;background:#fff;cursor:pointer;font-size:0.83rem;color:#334155;font-weight:500;text-align:center;transition:all .15s;}
#aa-app .aa-font-btn:hover{border-color:#3b82f6;background:#eff6ff;color:#1d4ed8;}
#aa-app .aa-font-btn.active{border-color:#2563eb;background:#dbeafe;color:#1e3a8a;font-weight:700;}
#aa-app .aa-options-row{display:flex;flex-wrap:wrap;gap:14px;align-items:flex-end;}
#aa-app .aa-opt-group{display:flex;flex-direction:column;gap:5px;}
#aa-app .aa-opt-group label{font-size:0.8rem;font-weight:600;color:#475569;}
#aa-app select.aa-select,#aa-app input.aa-text-input{padding:7px 10px;border:1.5px solid #cbd5e1;border-radius:7px;background:#fff;color:#1e293b;font-size:0.88rem;outline:none;}
#aa-app select.aa-select:focus,#aa-app input.aa-text-input:focus{border-color:#3b82f6;}
#aa-app input.aa-text-input{width:90px;}
#aa-app .aa-generate-btn{padding:10px 28px;background:#2563eb;color:#fff;border:none;border-radius:8px;font-size:0.95rem;font-weight:700;cursor:pointer;transition:background .2s;align-self:flex-end;}
#aa-app .aa-generate-btn:hover{background:#1d4ed8;}
#aa-app .aa-output-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;}
#aa-app .aa-output-meta{font-size:0.8rem;color:#64748b;}
#aa-app .aa-copy-btn{padding:6px 16px;background:#0f172a;color:#fff;border:none;border-radius:6px;font-size:0.82rem;font-weight:600;cursor:pointer;transition:background .2s;}
#aa-app .aa-copy-btn:hover{background:#1e293b;}
#aa-app .aa-copy-btn.copied{background:#16a34a;}
#aa-app pre#aa-output{background:#0f172a;color:#a3e635;border-radius:10px;padding:20px;overflow-x:auto;font-family:'Courier New',Courier,monospace;font-size:0.7rem;line-height:1.25;white-space:pre;min-height:80px;border:1.5px solid #1e293b;}
#aa-app .aa-empty-hint{color:#94a3b8;font-size:0.88rem;font-style:italic;}
@media(max-width:540px){
  #aa-app{padding:14px;}
  #aa-app pre#aa-output{font-size:0.55rem;}
}
</style>

<h2>アスキーアートジェネレーター</h2>
<p class="aa-subtitle">テキストを入力してスタイルを選ぶだけ。大きなASCIIアートバナーを瞬時に生成します。</p>

<div class="aa-section">
  <label class="aa-label" for="aa-input">テキスト入力（英数字・スペース対応）</label>
  <textarea id="aa-input" placeholder="例: HELLO" maxlength="30"></textarea>
</div>

<div class="aa-section">
  <label class="aa-label">フォントスタイル</label>
  <div class="aa-font-grid" id="aa-font-grid">
    <button class="aa-font-btn active" data-font="standard">スタンダード<br><span style="font-size:0.72rem;color:#64748b;">#文字ブロック</span></button>
    <button class="aa-font-btn" data-font="banner">バナー<br><span style="font-size:0.72rem;color:#64748b;">=と|の幅広</span></button>
    <button class="aa-font-btn" data-font="shadow">シャドウ<br><span style="font-size:0.72rem;color:#64748b;">/と_の影付き</span></button>
    <button class="aa-font-btn" data-font="thin">シン<br><span style="font-size:0.72rem;color:#64748b;">細線ミニマル</span></button>
    <button class="aa-font-btn" data-font="block">ブロック<br><span style="font-size:0.72rem;color:#64748b;">█ソリッド</span></button>
  </div>
</div>

<div class="aa-section">
  <div class="aa-options-row">
    <div class="aa-opt-group">
      <label>文字幅</label>
      <select class="aa-select" id="aa-width">
        <option value="1">狭い（×1）</option>
        <option value="2" selected>標準（×2）</option>
        <option value="3">広い（×3）</option>
      </select>
    </div>
    <div class="aa-opt-group">
      <label>カスタム塗り文字</label>
      <input class="aa-text-input" id="aa-fillchar" type="text" maxlength="3" placeholder="自動" />
    </div>
    <div class="aa-opt-group">
      <label>向き</label>
      <select class="aa-select" id="aa-orient">
        <option value="normal">横書き</option>
        <option value="flip">左右反転</option>
      </select>
    </div>
    <button class="aa-generate-btn" id="aa-gen-btn">生成する</button>
  </div>
</div>

<div class="aa-section">
  <div class="aa-output-header">
    <span class="aa-output-meta" id="aa-meta">出力: —</span>
    <button class="aa-copy-btn" id="aa-copy-btn">コピー</button>
  </div>
  <pre id="aa-output"><span class="aa-empty-hint">ここに生成されたASCIIアートが表示されます</span></pre>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

<script>
(function(){
"use strict";

// ── FONT DATA ──────────────────────────────────────────────────────────────
// Each glyph is an array of 6 strings (rows). Width determined by string length.
// Unsupported chars render as spaces.

var FONTS = {};

// ── STANDARD (# blocks) ──
FONTS.standard = {
  ' ': ['   ','   ','   ','   ','   ','   '],
  'A': [' ## ','#  #','####','#  #','#  #','    '],
  'B': ['### ','#  #','### ','#  #','### ','    '],
  'C': [' ###','#   ','#   ','#   ',' ###','    '],
  'D': ['### ','#  #','#  #','#  #','### ','    '],
  'E': ['####','#   ','### ','#   ','####','    '],
  'F': ['####','#   ','### ','#   ','#   ','    '],
  'G': [' ###','#   ','# ##','#  #',' ###','    '],
  'H': ['#  #','#  #','####','#  #','#  #','    '],
  'I': ['###',' # ',' # ',' # ','###','   '],
  'J': [' ##','  #','  #','# #',' # ','   '],
  'K': ['#  #','# # ','##  ','# # ','#  #','    '],
  'L': ['#   ','#   ','#   ','#   ','####','    '],
  'M': ['#   #','## ##','# # #','#   #','#   #','     '],
  'N': ['#  #','## #','# ##','#  #','#  #','    '],
  'O': [' ## ','#  #','#  #','#  #',' ## ','    '],
  'P': ['### ','#  #','### ','#   ','#   ','    '],
  'Q': [' ## ','#  #','#  #','# ##',' ###','    '],
  'R': ['### ','#  #','### ','# # ','#  #','    '],
  'S': [' ###','#   ',' ## ','   #','### ','    '],
  'T': ['###',' # ',' # ',' # ',' # ','   '],
  'U': ['#  #','#  #','#  #','#  #',' ## ','    '],
  'V': ['#  #','#  #','#  #',' ## ',' #  ','    '],
  'W': ['#   #','#   #','# # #','## ##','#   #','     '],
  'X': ['#  #',' ## ',' #  ',' ## ','#  #','    '],
  'Y': ['# #',' # ',' # ',' # ',' # ','   '],
  'Z': ['####','  # ',' #  ','#   ','####','    '],
  '0': [' ## ','#  #','# ##','## #','#  #',' ## '],
  '1': [' # ','## ',' # ',' # ','###','   '],
  '2': [' ## ','#  #','  # ',' #  ','####','    '],
  '3': ['### ','   #',' ## ','   #','### ','    '],
  '4': ['#  #','#  #','####','   #','   #','    '],
  '5': ['####','#   ','### ','   #','### ','    '],
  '6': [' ## ','#   ','### ','#  #',' ## ','    '],
  '7': ['####','  # ',' #  ',' #  ',' #  ','    '],
  '8': [' ## ','#  #',' ## ','#  #',' ## ','    '],
  '9': [' ## ','#  #',' ###','   #',' ## ','    '],
  '!': ['#','#','#',' ','#',' '],
  '?': [' ##','#  #','  # ',' #  ','    ',' #  '],
  '.': ['  ','  ','  ','  ',' #','  '],
  '-': ['   ','   ','###','   ','   ','   '],
  '_': ['   ','   ','   ','   ','####','    '],
};

// ── BANNER (=, | wide chars) ──
FONTS.banner = {
  ' ': ['     ','     ','     ','     ','     ','     '],
  'A': ['  =  ',' = = ','=====','=   =','=   =','     '],
  'B': ['==== ','=   =','==== ','=   =','==== ','     '],
  'C': [' ====','=    ','=    ','=    ',' ====','     '],
  'D': ['==== ','=   =','=   =','=   =','==== ','     '],
  'E': ['=====','=    ','==== ','=    ','=====','     '],
  'F': ['=====','=    ','==== ','=    ','=    ','     '],
  'G': [' ====','=    ','= ===','=   =','=====','     '],
  'H': ['=   =','=   =','=====','=   =','=   =','     '],
  'I': ['=====','  =  ','  =  ','  =  ','=====','     '],
  'J': ['  ===','   = ','   = ','=  = ',' ==  ','     '],
  'K': ['=   =','=  = ','===  ','=  = ','=   =','     '],
  'L': ['=    ','=    ','=    ','=    ','=====','     '],
  'M': ['=   =','== ==','= = =','=   =','=   =','     '],
  'N': ['=   =','==  =','= = =','=  ==','=   =','     '],
  'O': [' === ','=   =','=   =','=   =','=   =',' === '],
  'P': ['==== ','=   =','==== ','=    ','=    ','     '],
  'Q': [' === ','=   =','= = =','=  = ','=  ==','  =  '],
  'R': ['==== ','=   =','==== ','=  = ','=   =','     '],
  'S': [' ====','=    ',' === ','    =','====  ','     '],
  'T': ['=====','  =  ','  =  ','  =  ','  =  ','     '],
  'U': ['=   =','=   =','=   =','=   =','=====','     '],
  'V': ['=   =','=   =','=   =',' = = ','  =  ','     '],
  'W': ['=   =','=   =','= = =','== ==','=   =','     '],
  'X': ['=   =',' = = ','  =  ',' = = ','=   =','     '],
  'Y': ['=   =',' = = ','  =  ','  =  ','  =  ','     '],
  'Z': ['=====','   = ','  =  ',' =   ','=====','     '],
  '0': [' === ','=   =','= = =','=   =',' === ','     '],
  '1': ['  =  ',' ==  ','  =  ','  =  ','=====','     '],
  '2': [' === ','=   =','   = ',' ==  ','=====','     '],
  '3': ['=====','   = ',' === ','   = ','=====','     '],
  '4': ['=  = ','=  = ','=====','   = ','   = ','     '],
  '5': ['=====','=    ','==== ','    =','====  ','     '],
  '6': [' === ','=    ','==== ','=   =',' === ','     '],
  '7': ['=====','   = ','  =  ',' =   ','=    ','     '],
  '8': [' === ','=   =',' === ','=   =',' === ','     '],
  '9': [' === ','=   =',' ====','    =',' === ','     '],
  '!': ['=','=','=','=','  ','='],
  '?': [' === ','=   =','  =  ','     ','  =  ','     '],
  '.': ['  ','  ','  ','  ','= ','  '],
  '-': ['     ','     ','=====','     ','     ','     '],
  '_': ['     ','     ','     ','     ','=====','     '],
};

// ── SHADOW (/ and _ shadow style) ──
FONTS.shadow = {
  ' ': ['    ','    ','    ','    ','    ','    '],
  'A': ['  _  ',' /_\\ ','/ _ \\','/_/ \\_\\','    ','    '],
  'B': ['| __ )','| _ \\','| _) ','|____/','     ','     '],
  'C': [' ___',' / __|','| (__ ',' \\___|','     ','     '],
  'D': ['|  _ \\','| | | |','| |_| |','|____/ ','      ','      '],
  'E': ['| ___|','|___ \\','___) |','|____/ ','      ','      '],
  'F': ['| ___|','| _| ','|_|  ','     ','     ','     '],
  'G': [' ___ ','/ __|','\\__ \\','|___/','     ','     '],
  'H': ['| | | |','| |_| |','|  _  |','|_| |_|','       ','       '],
  'I': ['|_ _|',' | | ',' | | ','|___|','     ','     '],
  'J': ['_ | |','| | |','| |_| |','\\___/ ','      ','      '],
  'K': ['| |/ /','| \' / ','|  < ','| . \\','|_|\\_\\','      '],
  'L': ['| |    ','| |    ','| |___ ','|_____|','       ','       '],
  'M': ['| \\/ |','|      |','| |\\/| |','|_|  |_|','        ','        '],
  'N': ['| \\| |','| .` |','| |\\  |','|_| \\_|','       ','       '],
  'O': [' ___  ','/ _ \\ ','| (_) |',' \\___/ ','       ','       '],
  'P': ['| _ \\','|  _/','|_|  ','     ','     ','     '],
  'Q': [' ___  ','/ _ \\ ','| (_) |',' \\__\\_\\','   )_)','       '],
  'R': ['| _ \\','|   /','|_|_\\','     ','     ','     '],
  'S': ['/ __|','\\__ \\','|___/','     ','     ','     '],
  'T': ['|_   _|','  | |  ','  | |  ','  |_|  ','       ','       '],
  'U': ['| | | |','| |_| |','\\___/ ','      ','      ','      '],
  'V': ['\\  / ','\\  / ','\\\\/ ','    ','    ','    '],
  'W': ['\\ \\/ /','\\  / ',' \\/  ','     ','     ','     '],
  'X': ['\\  /','\\/ /','/ /\\','/_/ ','    ','    '],
  'Y': ['\\  / ',' \\/ ','  |  ','  |  ','     ','     '],
  'Z': ['__','/_/','  ','   ','   ','   '],
  '0': [' ___','/ _ \\','| | | |','| |_| |','\\___/ ','      '],
  '1': ['_ ','/ |','| |','|_|','   ','   '],
  '2': [' ___','|_  )','/ / ','/___|','     ','     '],
  '3': [' ___','|__ \\','__) |','|___/','     ','     '],
  '4': ['| || |','| || |','\\__  _|','   |_|','      ','      '],
  '5': ['| __|','|__ \\','|___/','     ','     ','     '],
  '6': [' ___','/ __|','\\__ \\','|___/','     ','     '],
  '7': [' ___','|__ /','/ / ','/_/  ','     ','     '],
  '8': [' ___ ','( _ )','/ _ \\','\\___/','     ','     '],
  '9': [' ___ ','/ _ \\','\\_, /','/_/  ','     ','     '],
  '!': ['_','!','|','!','  ','!'],
  '?': [' ___','|__ /','|_ \\','|__/','    ','/_/ '],
  '.': ['  ','  ','  ','  ','. ','  '],
  '-': ['   ','___','   ','   ','   ','   '],
  '_': ['   ','   ','   ','___','   ','   '],
};

// ── THIN (minimal line style) ──
FONTS.thin = {
  ' ': ['  ','  ','  ','  ','  ','  '],
  'A': [' /\\ ',' /  \\ ','/ /\\ \\','/_/  \\_\\','     ','     '],
  'B': ['|_  )','| ) / ','|___|','     ','     ','     '],
  'C': ['/ __|','| (__ ',' \\___|','      ','      ','      '],
  'D': ['|) ','||_','|__|','    ','    ','    '],
  'E': ['|_ ','|_ \\','|__|','    ','    ','    '],
  'F': ['|_ ','|_ ','|  ','   ','   ','   '],
  'G': ['.-.','|-|','`-|','   ','   ','   '],
  'H': ['| || |','|_  _|','  |_|  ','       ','       ','       '],
  'I': ['|','|','|','   ','   ','   '],
  'J': [' j',' j','`-\'','   ','   ','   '],
  'K': ['|/','|<','|\\','   ','   ','   '],
  'L': ['|  ','|  ','|__','   ','   ','   '],
  'M': ['|\\/|','|  |','|  |','    ','    ','    '],
  'N': ['|\\ |','| \\|','|  |','    ','    ','    '],
  'O': ['.-. ','| | ','`-\' ','    ','    ','    '],
  'P': ['|_) ','|  \\','|   ','    ','    ','    '],
  'Q': ['.-.','| |','`-\'','/ ','   ','   '],
  'R': ['|_) ','|_/ ','|   ','    ','    ','    '],
  'S': ['.-.','`-.','.-\'','   ','   ','   '],
  'T': ['_|_','  |','  |','   ','   ','   '],
  'U': ['| |','| |','`-\'','   ','   ','   '],
  'V': ['\\ /','\\/ ','   ','   ','   ','   '],
  'W': ['\\ /\\  /','\\   \\/','  \\  ','      ','      ','      '],
  'X': ['\\/','/\\','   ','   ','   ','   '],
  'Y': ['\\ /','\\/ ','|  ','   ','   ','   '],
  'Z': ['.-','  /','`-','   ','   ','   '],
  '0': ['.-.','| |','`-\'','   ','   ','   '],
  '1': ['|','|','   ','   ','   ','   '],
  '2': ['.-.','.-\'','`-\' ','    ','    ','    '],
  '3': ['.-.','.--|','`-\'','   ','   ','   '],
  '4': ['|\\ ','|_\\','  |','   ','   ','   '],
  '5': ['.-','`-.','.-\'','   ','   ','   '],
  '6': ['.-','\\.','`-\'','   ','   ','   '],
  '7': ['.-','  |','   ','   ','   ','   '],
  '8': ['.-.',')-(','`-\'','   ','   ','   '],
  '9': ['.-.','`-|','.-\'','   ','   ','   '],
  '!': ['|','|','  ','  ','  ','  '],
  '?': ['.-','  )','  ','  ','  ','  '],
  '.': [' ',' ',' ',' ','.','  '],
  '-': ['   ','---','   ','   ','   ','   '],
  '_': ['   ','   ','___','   ','   ','   '],
};

// ── BLOCK (█ solid blocks) ──
FONTS.block = {
  ' ': ['    ','    ','    ','    ','    ','    '],
  'A': [' ██ ','█  █','████','█  █','█  █','    '],
  'B': ['███ ','█  █','███ ','█  █','███ ','    '],
  'C': [' ███','█   ','█   ','█   ',' ███','    '],
  'D': ['███ ','█  █','█  █','█  █','███ ','    '],
  'E': ['████','█   ','███ ','█   ','████','    '],
  'F': ['████','█   ','███ ','█   ','█   ','    '],
  'G': [' ███','█   ','█ ██','█  █',' ███','    '],
  'H': ['█  █','█  █','████','█  █','█  █','    '],
  'I': ['███',' █ ',' █ ',' █ ','███','   '],
  'J': [' ██','  █','  █','█ █',' █ ','   '],
  'K': ['█  █','█ █ ','██  ','█ █ ','█  █','    '],
  'L': ['█   ','█   ','█   ','█   ','████','    '],
  'M': ['█   █','██ ██','█ █ █','█   █','█   █','     '],
  'N': ['█  █','██ █','█ ██','█  █','█  █','    '],
  'O': [' ██ ','█  █','█  █','█  █',' ██ ','    '],
  'P': ['███ ','█  █','███ ','█   ','█   ','    '],
  'Q': [' ██ ','█  █','█  █','█ ██',' ███','    '],
  'R': ['███ ','█  █','███ ','█ █ ','█  █','    '],
  'S': [' ███','█   ',' ██ ','   █','███ ','    '],
  'T': ['███',' █ ',' █ ',' █ ',' █ ','   '],
  'U': ['█  █','█  █','█  █','█  █',' ██ ','    '],
  'V': ['█  █','█  █','█  █',' ██ ',' █  ','    '],
  'W': ['█   █','█   █','█ █ █','██ ██','█   █','     '],
  'X': ['█  █',' ██ ',' █  ',' ██ ','█  █','    '],
  'Y': ['█ █',' █ ',' █ ',' █ ',' █ ','   '],
  'Z': ['████','  █ ',' █  ','█   ','████','    '],
  '0': [' ██ ','█  █','█ ██','██ █','█  █',' ██ '],
  '1': [' █ ','██ ',' █ ',' █ ','███','   '],
  '2': [' ██ ','█  █','  █ ',' █  ','████','    '],
  '3': ['███ ','   █',' ██ ','   █','███ ','    '],
  '4': ['█  █','█  █','████','   █','   █','    '],
  '5': ['████','█   ','███ ','   █','███ ','    '],
  '6': [' ██ ','█   ','███ ','█  █',' ██ ','    '],
  '7': ['████','  █ ',' █  ',' █  ',' █  ','    '],
  '8': [' ██ ','█  █',' ██ ','█  █',' ██ ','    '],
  '9': [' ██ ','█  █',' ███','   █',' ██ ','    '],
  '!': ['█','█','█',' ','█',' '],
  '?': [' ██','█  █','  █ ',' █  ','    ',' █  '],
  '.': ['  ','  ','  ','  ',' █','  '],
  '-': ['   ','   ','███','   ','   ','   '],
  '_': ['   ','   ','   ','   ','████','    '],
};

// ── RENDERING ──────────────────────────────────────────────────────────────

function getFont(name){ return FONTS[name] || FONTS.standard; }

function renderText(text, fontName, widthMul, fillChar, flip){
  var font = getFont(fontName);
  var chars = text.toUpperCase().split('');
  var ROWS = 6;
  var rows = [];
  for(var r=0;r<ROWS;r++) rows.push([]);

  chars.forEach(function(ch){
    var glyph = font[ch] || font[' '];
    if(!glyph){ glyph = font[' ']; }
    // Normalize to ROWS entries
    while(glyph.length < ROWS) glyph = glyph.concat(['']);
    var maxW = glyph.reduce(function(m,l){ return Math.max(m,l.length); },0);
    for(var r=0;r<ROWS;r++){
      var line = glyph[r] || '';
      // Pad to maxW
      while(line.length < maxW) line = line + ' ';
      // Apply fill char replacement
      if(fillChar && fillChar.trim()){
        var fc = fillChar.trim()[0];
        // Replace first non-space, non-special char pattern
        // We replace 'block' chars (#, =, █, |) with fillChar
        line = line.replace(/[#=█|]/g, fc);
      }
      // Apply width multiplier
      if(widthMul > 1){
        var expanded = '';
        for(var i=0;i<line.length;i++){
          for(var w=0;w<widthMul;w++) expanded += line[i];
        }
        line = expanded;
      }
      rows[r].push(line);
    }
  });

  // Join rows
  var result = rows.map(function(parts){ return parts.join(' '); }).join('\n');

  // Flip
  if(flip){
    result = result.split('\n').map(function(line){
      return line.split('').reverse().join('');
    }).join('\n');
  }

  return result;
}

// ── UI LOGIC ───────────────────────────────────────────────────────────────
var currentFont = 'standard';

function $(id){ return document.getElementById(id); }

// Font button selection
var fontBtns = document.querySelectorAll('#aa-font-grid .aa-font-btn');
fontBtns.forEach(function(btn){
  btn.addEventListener('click', function(){
    fontBtns.forEach(function(b){ b.classList.remove('active'); });
    btn.classList.add('active');
    currentFont = btn.getAttribute('data-font');
    generate();
  });
});

function generate(){
  var text = ($('aa-input').value || '').replace(/\n/g,' ').trim();
  if(!text){
    $('aa-output').innerHTML = '<span class="aa-empty-hint">ここに生成されたASCIIアートが表示されます</span>';
    $('aa-meta').textContent = '出力: —';
    return;
  }
  var widthMul = parseInt($('aa-width').value, 10) || 2;
  var fillChar = $('aa-fillchar').value;
  var flip = $('aa-orient').value === 'flip';
  var result = renderText(text, currentFont, widthMul, fillChar, flip);
  $('aa-output').textContent = result;
  // Meta
  var lines = result.split('\n');
  var maxW = lines.reduce(function(m,l){ return Math.max(m,l.length); }, 0);
  $('aa-meta').textContent = '出力: ' + lines.length + '行 × ' + maxW + '列';
}

$('aa-gen-btn').addEventListener('click', generate);
$('aa-input').addEventListener('keydown', function(e){
  if(e.key === 'Enter' && !e.shiftKey){ e.preventDefault(); generate(); }
});
$('aa-width').addEventListener('change', generate);
$('aa-orient').addEventListener('change', generate);
$('aa-fillchar').addEventListener('input', generate);

// Copy button
$('aa-copy-btn').addEventListener('click', function(){
  var text = $('aa-output').textContent;
  if(!text || text.includes('ここに生成')) return;
  var btn = $('aa-copy-btn');
  if(navigator.clipboard && window.isSecureContext){
    navigator.clipboard.writeText(text).then(function(){
      btn.textContent = 'コピー済み!';
      btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
    });
  } else {
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position='fixed';ta.style.opacity='0';
    document.body.appendChild(ta);
    ta.select();
    try{ document.execCommand('copy'); } catch(e){}
    document.body.removeChild(ta);
    btn.textContent = 'コピー済み!';
    btn.classList.add('copied');
    setTimeout(function(){ btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 1800);
  }
});

// Auto-generate on load with placeholder
$('aa-input').value = 'HELLO';
generate();

})();
</script>

</div>

---

> QRコードを作成 → [QRコードジェネレーター](/ja/tools/qr-code-generator/)
> ダミー画像を作成 → [プレースホルダー画像生成ツール](/ja/tools/placeholder-image/)
> Unicode文字を検索 → [Unicode文字マップ](/ja/tools/unicode-character-map/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
