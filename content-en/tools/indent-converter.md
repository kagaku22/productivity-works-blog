---
title: "Indent Converter"
date: 2025-05-16
description: "Free online indent converter. Re-indent code between 2-space, 4-space, and tab styles. Auto-detects current indentation, shows whitespace markers, cleans mixed indentation, and copies output instantly."
categories: ["Free Tools"]
slug: "indent-converter"
ShowToc: false
aliases: ["/tools/indent-converter/", "/tools/indent-converter/"]
cover:
  image: "/images/covers/indent-converter.png"
  alt: "Indent Converter"
---

Re-indent any code instantly — convert between 2-space, 4-space, and tab styles, fix mixed indentation, and preview whitespace markers before copying.

> Convert tabs → [Tab Converter](/tools/tab-converter/)

> Format HTML → [HTML Beautifier](/tools/html-beautifier/)

<div id="ic-app">
<style>
#ic-app *,#ic-app *::before,#ic-app *::after{box-sizing:border-box;margin:0;padding:0}
#ic-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;font-size:14px;color:#1e293b;background:#f8fafc;border:1px solid #e2e8f0;border-radius:12px;padding:20px;max-width:960px}
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
#ic-app .ic-btn.warn{background:#fef3c7;border-color:#fcd34d;color:#92400e}
#ic-app .ic-btn.warn:hover{background:#fde68a;border-color:#f59e0b}
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
#ic-app .ic-preview .ws-mixed{background:#fef2f2;color:#dc2626}
#ic-app .ic-stats{display:flex;gap:14px;flex-wrap:wrap;padding:10px 14px;background:#f1f5f9;border-radius:8px;margin-top:12px}
#ic-app .ic-stat{font-size:12px;color:#64748b}
#ic-app .ic-stat strong{color:#1e293b;font-weight:600}
#ic-app .ic-divider{border:none;border-top:1px solid #e2e8f0;margin:14px 0}
#ic-app .ic-copy-note{font-size:12px;color:#10b981;font-weight:600;display:none}
#ic-app .ic-upload-wrap{position:relative;display:inline-block}
#ic-app .ic-upload-wrap input[type=file]{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%}
#ic-app .ic-increase-decrease{display:flex;gap:4px}
</style>

<!-- Row 1: From style -->
<div class="ic-row">
  <span class="ic-label">From:</span>
  <div class="ic-btn-group" id="ic-from-group">
    <button class="ic-btn active" id="ic-from-auto" onclick="icSetFrom('auto')">Auto-detect</button>
    <button class="ic-btn" id="ic-from-2sp" onclick="icSetFrom('2sp')">2 Spaces</button>
    <button class="ic-btn" id="ic-from-4sp" onclick="icSetFrom('4sp')">4 Spaces</button>
    <button class="ic-btn" id="ic-from-tab" onclick="icSetFrom('tab')">Tabs</button>
  </div>
  <span class="ic-detect-badge" id="ic-detect-badge"><span class="dot"></span><span id="ic-detect-text">Paste code to detect</span></span>
</div>

<!-- Row 2: To style -->
<div class="ic-row">
  <span class="ic-label">To:</span>
  <div class="ic-btn-group">
    <button class="ic-btn" id="ic-to-2sp" onclick="icSetTo('2sp')">2 Spaces</button>
    <button class="ic-btn active" id="ic-to-4sp" onclick="icSetTo('4sp')">4 Spaces</button>
    <button class="ic-btn" id="ic-to-tab" onclick="icSetTo('tab')">Tabs</button>
  </div>
</div>

<!-- Row 3: Indent level shift -->
<div class="ic-row">
  <span class="ic-label">Indent shift:</span>
  <div class="ic-increase-decrease">
    <button class="ic-btn secondary" onclick="icShiftIndent(-1)">&#8722; Decrease</button>
    <button class="ic-btn secondary" onclick="icShiftIndent(1)">&#43; Increase</button>
  </div>
</div>

<!-- Row 4: Options -->
<div class="ic-row">
  <label class="ic-check-label"><input type="checkbox" id="ic-trim" onchange="icProcess()"> Trim trailing whitespace</label>
  <label class="ic-check-label"><input type="checkbox" id="ic-fix-mixed" onchange="icProcess()" checked> Fix mixed indentation</label>
  <label class="ic-check-label"><input type="checkbox" id="ic-show-ws" onchange="icProcess()" checked> Show whitespace markers</label>
</div>

<!-- Row 5: Actions -->
<div class="ic-row">
  <div class="ic-btn-group">
    <button class="ic-btn action" onclick="icProcess()">Convert</button>
    <button class="ic-btn secondary" onclick="icSwap()">Swap</button>
    <button class="ic-btn secondary" onclick="icClear()">Clear</button>
    <div class="ic-upload-wrap">
      <button class="ic-btn secondary">Upload File</button>
      <input type="file" accept="text/*" onchange="icUpload(event)">
    </div>
  </div>
</div>

<hr class="ic-divider">

<!-- Editor panels -->
<div class="ic-panels">
  <div>
    <div class="ic-panel-head">
      <span class="ic-panel-title">INPUT</span>
      <div class="ic-panel-actions">
        <button class="ic-btn secondary" style="padding:4px 10px;font-size:12px" onclick="icPaste()">Paste</button>
      </div>
    </div>
    <textarea id="ic-input" placeholder="Paste your code here..." oninput="icProcess()" spellcheck="false"></textarea>
  </div>
  <div>
    <div class="ic-panel-head">
      <span class="ic-panel-title">OUTPUT</span>
      <div class="ic-panel-actions">
        <button class="ic-btn secondary" style="padding:4px 10px;font-size:12px" onclick="icCopy()">Copy</button>
        <span class="ic-copy-note" id="ic-copy-note">Copied!</span>
      </div>
    </div>
    <div class="ic-preview" id="ic-output-preview" aria-live="polite"></div>
    <textarea id="ic-output-raw" style="display:none" readonly spellcheck="false"></textarea>
  </div>
</div>

<!-- Stats -->
<div class="ic-stats" id="ic-stats">
  <span class="ic-stat">Lines: <strong id="ic-stat-lines">0</strong></span>
  <span class="ic-stat">Input chars: <strong id="ic-stat-in">0</strong></span>
  <span class="ic-stat">Output chars: <strong id="ic-stat-out">0</strong></span>
  <span class="ic-stat">Tab-indented lines: <strong id="ic-stat-tabs">0</strong></span>
  <span class="ic-stat">Space-indented lines: <strong id="ic-stat-spaces">0</strong></span>
  <span class="ic-stat">Mixed lines: <strong id="ic-stat-mixed">0</strong></span>
</div>

<script>
(function(){
  var fromStyle = 'auto'; // auto|2sp|4sp|tab
  var toStyle = '4sp';    // 2sp|4sp|tab
  var shiftDelta = 0;     // cumulative indent shift

  /* ---- Detection ---- */
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
      // spaces
      var n = lead.length;
      if(n % 4 === 0) sp4Lines++;
      else if(n % 2 === 0) sp2Lines++;
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
      'unknown':'No indentation detected',
      '2sp':'Detected: 2-space',
      '4sp':'Detected: 4-space',
      'tab':'Detected: Tabs',
      'mixed':'Detected: Mixed (will fix)'
    };
    var classes = {'2sp':'detected-spaces-2','4sp':'detected-spaces-4','tab':'detected-tabs','mixed':'detected-mixed'};
    text.textContent = labels[style] || 'Paste code to detect';
    if(classes[style]) badge.classList.add(classes[style]);
  }

  /* ---- Conversion core ---- */
  function lineToUnified(line, srcStyle){
    // Resolve actual from-style
    var src = srcStyle === 'auto' ? detectStyle([line]) : srcStyle;
    if(src === 'unknown' || src === 'mixed') src = guessLineStyle(line);

    var m = line.match(/^(\s*)([\s\S]*)$/);
    if(!m) return {level:0, rest:line, raw:''};
    var lead = m[1];
    var rest = m[2];

    if(!lead) return {level:0, rest:rest, raw:''};

    // Normalise lead to spaces first
    var sp = lead.replace(/\t/g, '    '); // treat tab=4sp for measurement
    var unitSize = (src === '2sp') ? 2 : 4;
    var level = Math.round(sp.length / unitSize);
    return {level:level, rest:rest, raw:lead};
  }

  function guessLineStyle(line){
    var m = line.match(/^(\s+)/);
    if(!m) return '4sp';
    var lead = m[1];
    if(/\t/.test(lead)) return 'tab';
    if(lead.length % 4 === 0) return '4sp';
    return '2sp';
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
      // Separate leading whitespace from content
      var m = line.match(/^(\s*)([\s\S]*)$/);
      var lead = m[1];
      var rest = m[2];

      if(!lead){
        if(trim) rest = rest.replace(/[ \t]+$/, '');
        return rest;
      }

      // Fix mixed: normalise to spaces first
      var normalized = lead;
      if(fixMixed && /\t/.test(lead) && / /.test(lead)){
        normalized = lead.replace(/\t/g, '    ');
      }

      // Determine source unit
      var hasTabs = /\t/.test(normalized);
      var src = srcStyle === 'auto' ? detected : srcStyle;
      if(src === 'mixed' || src === 'unknown') src = hasTabs ? 'tab' : (normalized.length % 4 === 0 ? '4sp' : '2sp');

      // Measure level
      var level;
      if(hasTabs && src !== 'tab'){
        // expand tabs then measure
        var expanded = normalized.replace(/\t/g, (src==='2sp'?'  ':'    '));
        var unit = src==='2sp' ? 2 : 4;
        level = Math.floor(expanded.length / unit);
      } else if(!hasTabs && src === 'tab'){
        // treat every group of 4 spaces as 1 tab level
        level = Math.floor(normalized.length / 4);
      } else if(src === 'tab'){
        level = normalized.length; // count of tab chars
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

  /* ---- Whitespace preview ---- */
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

  /* ---- Stats ---- */
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

  /* ---- Main process ---- */
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
      document.getElementById('ic-detect-text').textContent = 'Paste code to detect';
    }
  }

  /* ---- UI setters ---- */
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
    document.getElementById('ic-detect-text').textContent = 'Paste code to detect';
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

  // Expose to inline handlers
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

**How it works:**

- **Auto-detect**: Scans leading whitespace across all lines to determine whether the file uses 2-space, 4-space, or tab indentation, and flags mixed files.
- **Re-indent**: Measures each line's indent level in the source style, then rebuilds it in the target style — preserving relative nesting depth exactly.
- **Indent shift**: Increases or decreases every line's nesting level by one step without changing style.
- **Mixed indentation cleanup**: Normalises lines that combine tabs and spaces before re-indenting, so no stray characters remain.
- **Whitespace markers**: Spaces show as `·` (purple), tabs show as `→` (amber) so you can verify the result at a glance.
