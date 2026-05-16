---
title: "インデント変換ツール"
date: 2025-05-16
description: "コードのインデントをワンクリックで変換。2スペース・4スペース・タブを相互変換し、現在のインデントスタイルを自動検出。混在インデントの修正、空白文字のプレビュー表示、結果コピーに対応した無料オンラインツール。"
categories: ["無料ツール"]
slug: "indent-converter"
ShowToc: false
aliases: ["/ja/tools/reindent/", "/ja/tools/indent-fixer/"]
cover:
  image: "/images/covers/indent-converter-ja.png"
  alt: "インデント変換ツール"
---

コードのインデントスタイルを瞬時に変換。2スペース・4スペース・タブを自由に切り替え、混在インデントを修正し、空白文字をプレビューしながら結果をコピーできます。

> タブ変換 → [タブ⇔スペース変換](/ja/tools/tab-converter/)

> HTMLを整形 → [HTML整形ツール](/ja/tools/html-beautifier/)

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div id="ic-app">
<style>
#ic-app *,#ic-app *::before,#ic-app *::after{box-sizing:border-box;margin:0;padding:0}
#ic-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;font-size:14px;color:#1e293b;background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:20px;max-width:960px;margin-top:20px}
#ic-app .ic-row{display:flex;gap:12px;flex-wrap:wrap;align-items:center;margin-bottom:14px}
#ic-app .ic-label{font-weight:600;font-size:13px;color:#475569;white-space:nowrap;min-width:90px}
#ic-app .ic-btn-group{display:flex;gap:6px;flex-wrap:wrap}
#ic-app .ic-btn{padding:7px 14px;border-radius:7px;border:1.5px solid #cbd5e1;background:#fff;color:#334155;font-size:13px;font-weight:500;cursor:pointer;transition:all .15s}
#ic-app .ic-btn:hover{border-color:#6366f1;color:#6366f1}
#ic-app .ic-btn.active{background:#6366f1;border-color:#6366f1;color:#fff}
#ic-app .ic-btn.action{background:#6366f1;border-color:#6366f1;color:#fff;font-weight:600}
#ic-app .ic-btn.action:hover{background:#4f46e5;border-color:#4f46e5}
#ic-app .ic-btn.secondary{background:#f1f5f9;border-color:#cbd5e1;color:#475569}
#ic-app .ic-btn.secondary:hover{border-color:#6366f1;color:#6366f1;background:#f1f5f9}
#ic-app .ic-check-label{display:flex;align-items:center;gap:6px;font-size:13px;color:#475569;cursor:pointer;user-select:none}
#ic-app .ic-check-label input{accent-color:#6366f1;width:15px;height:15px;cursor:pointer}
#ic-app .ic-detect-badge{display:inline-flex;align-items:center;gap:6px;padding:5px 12px;background:#f1f5f9;border:1.5px solid #e2e8f0;border-radius:20px;font-size:12px;color:#475569;font-weight:600}
#ic-app .ic-detect-badge .dot{width:8px;height:8px;border-radius:50%;background:#94a3b8;display:inline-block}
#ic-app .ic-detect-badge.detected-spaces-2 .dot{background:#10b981}
#ic-app .ic-detect-badge.detected-spaces-4 .dot{background:#6366f1}
#ic-app .ic-detect-badge.detected-tabs .dot{background:#f59e0b}
#ic-app .ic-detect-badge.detected-mixed .dot{background:#ef4444}
#ic-app .ic-panels{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media(max-width:660px){#ic-app .ic-panels{grid-template-columns:1fr}}
#ic-app .ic-panel-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px}
#ic-app .ic-panel-title{font-weight:600;font-size:13px;color:#64748b;letter-spacing:.02em}
#ic-app .ic-panel-actions{display:flex;gap:6px;align-items:center}
#ic-app textarea{width:100%;height:300px;padding:10px 12px;border:1.5px solid #e2e8f0;border-radius:8px;font-family:"SFMono-Regular",Consolas,"Liberation Mono",Menlo,monospace;font-size:13px;line-height:1.6;color:#1e293b;background:#fff;resize:vertical;outline:none;transition:border-color .15s}
#ic-app textarea:focus{border-color:#6366f1}
#ic-app .ic-preview{width:100%;height:300px;padding:10px 12px;border:1.5px solid #e2e8f0;border-radius:8px;font-family:"SFMono-Regular",Consolas,"Liberation Mono",Menlo,monospace;font-size:13px;line-height:1.6;background:#fff;overflow:auto;white-space:pre;word-break:normal;tab-size:4}
#ic-app .ic-preview .ws-sp{color:#c4b5fd}
#ic-app .ic-preview .ws-tab{color:#f59e0b}
#ic-app .ic-stats{display:flex;gap:14px;flex-wrap:wrap;padding:10px 14px;background:#f1f5f9;border-radius:8px;margin-top:12px}
#ic-app .ic-stat{font-size:12px;color:#64748b}
#ic-app .ic-stat strong{color:#1e293b;font-weight:600}
#ic-app .ic-divider{border:none;border-top:1px solid #e2e8f0;margin:14px 0}
#ic-app .ic-copy-note{font-size:12px;color:#10b981;font-weight:600;display:none}
#ic-app .ic-upload-wrap{position:relative;display:inline-block}
#ic-app .ic-upload-wrap input[type=file]{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%}
#ic-app .ic-increase-decrease{display:flex;gap:4px}
</style>

<!-- 変換元スタイル -->
<div class="ic-row">
  <span class="ic-label">変換元：</span>
  <div class="ic-btn-group" id="ic-from-group">
    <button class="ic-btn active" id="ic-from-auto" onclick="icSetFrom('auto')">自動検出</button>
    <button class="ic-btn" id="ic-from-2sp" onclick="icSetFrom('2sp')">2スペース</button>
    <button class="ic-btn" id="ic-from-4sp" onclick="icSetFrom('4sp')">4スペース</button>
    <button class="ic-btn" id="ic-from-tab" onclick="icSetFrom('tab')">タブ</button>
  </div>
  <span class="ic-detect-badge" id="ic-detect-badge"><span class="dot"></span><span id="ic-detect-text">コードを貼り付けて検出</span></span>
</div>

<!-- 変換先スタイル -->
<div class="ic-row">
  <span class="ic-label">変換先：</span>
  <div class="ic-btn-group">
    <button class="ic-btn" id="ic-to-2sp" onclick="icSetTo('2sp')">2スペース</button>
    <button class="ic-btn active" id="ic-to-4sp" onclick="icSetTo('4sp')">4スペース</button>
    <button class="ic-btn" id="ic-to-tab" onclick="icSetTo('tab')">タブ</button>
  </div>
</div>

<!-- インデントレベル調整 -->
<div class="ic-row">
  <span class="ic-label">レベル調整：</span>
  <div class="ic-increase-decrease">
    <button class="ic-btn secondary" onclick="icShiftIndent(-1)">&#8722; 減らす</button>
    <button class="ic-btn secondary" onclick="icShiftIndent(1)">&#43; 増やす</button>
  </div>
</div>

<!-- オプション -->
<div class="ic-row">
  <label class="ic-check-label"><input type="checkbox" id="ic-trim" onchange="icProcess()"> 行末空白を除去</label>
  <label class="ic-check-label"><input type="checkbox" id="ic-fix-mixed" onchange="icProcess()" checked> 混在インデントを修正</label>
  <label class="ic-check-label"><input type="checkbox" id="ic-show-ws" onchange="icProcess()" checked> 空白文字を表示</label>
</div>

<!-- アクション -->
<div class="ic-row">
  <div class="ic-btn-group">
    <button class="ic-btn action" onclick="icProcess()">変換</button>
    <button class="ic-btn secondary" onclick="icSwap()">入出力を入替</button>
    <button class="ic-btn secondary" onclick="icClear()">クリア</button>
    <div class="ic-upload-wrap">
      <button class="ic-btn secondary">ファイルを開く</button>
      <input type="file" accept="text/*" onchange="icUpload(event)">
    </div>
  </div>
</div>

<hr class="ic-divider">

<!-- エディタパネル -->
<div class="ic-panels">
  <div>
    <div class="ic-panel-head">
      <span class="ic-panel-title">入力</span>
      <div class="ic-panel-actions">
        <button class="ic-btn secondary" style="padding:4px 10px;font-size:12px" onclick="icPaste()">貼り付け</button>
      </div>
    </div>
    <textarea id="ic-input" placeholder="コードをここに貼り付けてください..." oninput="icProcess()" spellcheck="false"></textarea>
  </div>
  <div>
    <div class="ic-panel-head">
      <span class="ic-panel-title">出力</span>
      <div class="ic-panel-actions">
        <button class="ic-btn secondary" style="padding:4px 10px;font-size:12px" onclick="icCopy()">コピー</button>
        <span class="ic-copy-note" id="ic-copy-note">コピーしました！</span>
      </div>
    </div>
    <div class="ic-preview" id="ic-output-preview" aria-live="polite"></div>
    <textarea id="ic-output-raw" style="display:none" readonly spellcheck="false"></textarea>
  </div>
</div>

<!-- 統計情報 -->
<div class="ic-stats" id="ic-stats">
  <span class="ic-stat">行数: <strong id="ic-stat-lines">0</strong></span>
  <span class="ic-stat">入力文字数: <strong id="ic-stat-in">0</strong></span>
  <span class="ic-stat">出力文字数: <strong id="ic-stat-out">0</strong></span>
  <span class="ic-stat">タブインデント行: <strong id="ic-stat-tabs">0</strong></span>
  <span class="ic-stat">スペースインデント行: <strong id="ic-stat-spaces">0</strong></span>
  <span class="ic-stat">混在行: <strong id="ic-stat-mixed">0</strong></span>
</div>

<script>
(function(){
  var fromStyle = 'auto';
  var toStyle = '4sp';
  var shiftDelta = 0;

  function detectStyle(lines){
    var tabLines=0, sp2Lines=0, sp4Lines=0, mixedLines=0;
    lines.forEach(function(l){
      var m = l.match(/^(\s+)/);
      if(!m) return;
      var lead = m[1];
      var hasTab = /\t/.test(lead);
      var hasSp = / /.test(lead);
      if(hasTab && hasSp){ mixedLines++; return; }
      if(hasTab){ tabLines++; return; }
      var n = lead.length;
      if(n % 4 === 0) sp4Lines++;
      else sp2Lines++;
    });
    var total = tabLines + sp2Lines + sp4Lines + mixedLines;
    if(total === 0) return 'unknown';
    if(mixedLines > total * 0.15) return 'mixed';
    if(tabLines > sp2Lines && tabLines > sp4Lines) return 'tab';
    if(sp4Lines >= sp2Lines) return '4sp';
    return '2sp';
  }

  function updateDetectBadge(style){
    var badge = document.getElementById('ic-detect-badge');
    var text = document.getElementById('ic-detect-text');
    badge.className = 'ic-detect-badge';
    var labels = {
      'unknown':'インデントなし',
      '2sp':'検出: 2スペース',
      '4sp':'検出: 4スペース',
      'tab':'検出: タブ',
      'mixed':'検出: 混在（修正します）'
    };
    var classes = {'2sp':'detected-spaces-2','4sp':'detected-spaces-4','tab':'detected-tabs','mixed':'detected-mixed'};
    text.textContent = labels[style] || 'コードを貼り付けて検出';
    if(classes[style]) badge.classList.add(classes[style]);
  }

  function buildIndent(level, style){
    if(level <= 0) return '';
    if(style === 'tab') return '\t'.repeat(level);
    var size = style === '2sp' ? 2 : 4;
    return ' '.repeat(size * level);
  }

  function convertLines(lines, srcStyle, dstStyle, fixMixed, trim, shift){
    var detected = detectStyle(lines);
    updateDetectBadge(detected);

    return lines.map(function(line){
      var m = line.match(/^(\s*)([\s\S]*)$/);
      var lead = m[1], rest = m[2];
      if(!lead){
        if(trim) rest = rest.replace(/[ \t]+$/, '');
        return rest;
      }
      var normalized = lead;
      if(fixMixed && /\t/.test(lead) && / /.test(lead)){
        normalized = lead.replace(/\t/g, '    ');
      }
      var hasTabs = /\t/.test(normalized);
      var src = srcStyle === 'auto' ? detected : srcStyle;
      if(src === 'mixed' || src === 'unknown') src = hasTabs ? 'tab' : (normalized.length % 4 === 0 ? '4sp' : '2sp');
      var level;
      if(hasTabs && src !== 'tab'){
        var expanded = normalized.replace(/\t/g, (src==='2sp'?'  ':'    '));
        var unit = src==='2sp' ? 2 : 4;
        level = Math.floor(expanded.length / unit);
      } else if(!hasTabs && src === 'tab'){
        level = Math.floor(normalized.length / 4);
      } else if(src === 'tab'){
        level = normalized.length;
      } else {
        var u = src==='2sp' ? 2 : 4;
        level = Math.floor(normalized.length / u);
      }
      level = Math.max(0, level + shift);
      var newLead = buildIndent(level, dstStyle);
      var out = newLead + rest;
      if(trim) out = out.replace(/[ \t]+$/, '');
      return out;
    });
  }

  function escHtml(s){
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function renderPreview(text, showWs, dstStyle){
    var el = document.getElementById('ic-output-preview');
    if(!showWs){ el.textContent = text; return; }
    var lines = text.split('\n');
    var html = lines.map(function(line){
      var m = line.match(/^(\s*)([\s\S]*)$/);
      var lead = m[1], rest = m[2];
      var leadHtml = '';
      if(dstStyle === 'tab'){
        leadHtml = escHtml(lead).replace(/\t/g,'<span class="ws-tab">\u2192   </span>');
      } else {
        leadHtml = escHtml(lead).replace(/ /g,'<span class="ws-sp">\u00b7</span>');
      }
      return leadHtml + escHtml(rest);
    }).join('\n');
    el.innerHTML = html;
  }

  function computeStats(lines){
    var tabs=0, spaces=0, mixed=0;
    lines.forEach(function(l){
      var m = l.match(/^(\s+)/);
      if(!m) return;
      var lead = m[1];
      var hasT = /\t/.test(lead), hasS = / /.test(lead);
      if(hasT && hasS) mixed++;
      else if(hasT) tabs++;
      else spaces++;
    });
    return {tabs:tabs, spaces:spaces, mixed:mixed};
  }

  function process(){
    var input = document.getElementById('ic-input').value;
    var trim = document.getElementById('ic-trim').checked;
    var fixMixed = document.getElementById('ic-fix-mixed').checked;
    var showWs = document.getElementById('ic-show-ws').checked;
    var lines = input.split('\n');
    var stats = computeStats(lines);
    var outLines = convertLines(lines, fromStyle, toStyle, fixMixed, trim, shiftDelta);
    var output = outLines.join('\n');
    document.getElementById('ic-output-raw').value = output;
    renderPreview(output, showWs, toStyle);
    document.getElementById('ic-stat-lines').textContent = lines.length;
    document.getElementById('ic-stat-in').textContent = input.length;
    document.getElementById('ic-stat-out').textContent = output.length;
    document.getElementById('ic-stat-tabs').textContent = stats.tabs;
    document.getElementById('ic-stat-spaces').textContent = stats.spaces;
    document.getElementById('ic-stat-mixed').textContent = stats.mixed;
    if(!input){
      updateDetectBadge('unknown');
      document.getElementById('ic-detect-text').textContent = 'コードを貼り付けて検出';
    }
  }

  function setFrom(s){
    fromStyle = s;
    ['auto','2sp','4sp','tab'].forEach(function(k){
      document.getElementById('ic-from-'+k).classList.toggle('active', k===s);
    });
    process();
  }

  function setTo(s){
    toStyle = s;
    ['2sp','4sp','tab'].forEach(function(k){
      document.getElementById('ic-to-'+k).classList.toggle('active', k===s);
    });
    process();
  }

  function shiftIndent(delta){
    shiftDelta += delta;
    process();
  }

  function swap(){
    var raw = document.getElementById('ic-output-raw').value;
    document.getElementById('ic-input').value = raw;
    shiftDelta = 0;
    process();
  }

  function clear(){
    document.getElementById('ic-input').value = '';
    document.getElementById('ic-output-raw').value = '';
    document.getElementById('ic-output-preview').textContent = '';
    shiftDelta = 0;
    ['ic-stat-lines','ic-stat-in','ic-stat-out','ic-stat-tabs','ic-stat-spaces','ic-stat-mixed'].forEach(function(id){
      document.getElementById(id).textContent = '0';
    });
    updateDetectBadge('unknown');
    document.getElementById('ic-detect-text').textContent = 'コードを貼り付けて検出';
  }

  function copy(){
    var val = document.getElementById('ic-output-raw').value;
    if(!val) return;
    if(navigator.clipboard && navigator.clipboard.writeText){
      navigator.clipboard.writeText(val).then(flashCopy);
    } else {
      var ta = document.createElement('textarea');
      ta.value = val; ta.style.position='fixed'; ta.style.opacity='0';
      document.body.appendChild(ta); ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      flashCopy();
    }
  }

  function flashCopy(){
    var note = document.getElementById('ic-copy-note');
    note.style.display='inline';
    setTimeout(function(){ note.style.display='none'; }, 1800);
  }

  function paste(){
    if(navigator.clipboard && navigator.clipboard.readText){
      navigator.clipboard.readText().then(function(t){
        document.getElementById('ic-input').value = t;
        shiftDelta = 0;
        process();
      });
    }
  }

  function upload(e){
    var file = e.target.files[0];
    if(!file) return;
    var reader = new FileReader();
    reader.onload = function(ev){
      document.getElementById('ic-input').value = ev.target.result;
      shiftDelta = 0;
      process();
    };
    reader.readAsText(file);
    e.target.value = '';
  }

  window.icSetFrom = setFrom;
  window.icSetTo = setTo;
  window.icShiftIndent = shiftIndent;
  window.icProcess = process;
  window.icSwap = swap;
  window.icClear = clear;
  window.icCopy = copy;
  window.icPaste = paste;
  window.icUpload = upload;

  process();
})();
</script>
</div>

---

**使い方：**

- **自動検出**：全行の先頭空白を分析し、2スペース・4スペース・タブ・混在のいずれかを判定します。
- **再インデント**：各行のインデント深さを元スタイルで測定し、変換先スタイルで再構築。相対的なネスト構造をそのまま保ちます。
- **レベル調整**：スタイルを変えずに全行のインデントを1段階増減します。
- **混在修正**：タブとスペースが混在した行を正規化してから変換します。
- **空白文字表示**：スペースは `·`（紫）、タブは `→`（琥珀）で表示し、変換結果を目視確認できます。

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
