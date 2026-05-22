---
title: "CSS Scrollbar Styler"
date: 2025-05-16
description: "Free CSS scrollbar generator. Customize scrollbar width, colors, border-radius, and hover effects with live preview — copy WebKit and Firefox CSS."
categories: ["Free Tools"]
slug: "scrollbar-styler"
ShowToc: false
cover:
  image: "/images/covers/scrollbar-styler.png"
  alt: "CSS Scrollbar Styler"
---

<div id="sb-app" style="font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;max-width:900px;margin:0 auto;">

<style>
#sb-app *,#sb-app *::before,#sb-app *::after{box-sizing:border-box;}
#sb-app h2{font-size:1.1rem;font-weight:700;margin:0 0 12px;color:#1e293b !important;color-scheme:light;}
#sb-app .sb-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:20px;}
@media(max-width:640px){#sb-app .sb-grid{grid-template-columns:1fr;}}
#sb-app .sb-panel{background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;padding:18px;}
#sb-app .sb-control{margin-bottom:14px;}
#sb-app .sb-control label{display:block;font-size:13px;font-weight:600;color:#475569;margin-bottom:5px;}
#sb-app .sb-control input[type=range]{width:100%;accent-color:#6366f1;}
#sb-app .sb-control input[type=color]{width:48px;height:32px;border:1px solid #cbd5e1;border-radius:6px;cursor:pointer;padding:2px;}
#sb-app .sb-color-row{display:flex;align-items:center;gap:10px;}
#sb-app .sb-color-row input[type=text]{flex:1;padding:6px 10px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;font-family:monospace;}
#sb-app .sb-select{width:100%;padding:7px 10px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;background:#fff;}
#sb-app .sb-val{font-size:12px;color:#6366f1;font-weight:700;margin-left:6px;}
#sb-app .sb-presets{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px;}
#sb-app .sb-preset-btn{padding:7px 15px;border:1.5px solid #cbd5e1;border-radius:20px;font-size:13px;font-weight:600;cursor:pointer;background:#fff;color:#334155;transition:all .18s;}
#sb-app .sb-preset-btn:hover{border-color:#6366f1;color:#6366f1;}
#sb-app .sb-preset-btn.active{background:#6366f1;color:#fff;border-color:#6366f1;}
#sb-app .sb-preview-wrap{margin-bottom:20px;}
#sb-app .sb-preview-box{height:180px;overflow-y:scroll;border:1px solid #e2e8f0;border-radius:10px;padding:16px;background:#fff;font-size:14px;color:#475569;line-height:1.7;}
#sb-app .sb-output-wrap{margin-bottom:20px;}
#sb-app .sb-tabs{display:flex;gap:0;margin-bottom:0;}
#sb-app .sb-tab{padding:8px 18px;font-size:13px;font-weight:600;cursor:pointer;border:1.5px solid #e2e8f0;border-bottom:none;border-radius:8px 8px 0 0;background:#f1f5f9;color:#64748b;transition:all .15s;}
#sb-app .sb-tab.active{background:#1e293b;color:#fff;border-color:#1e293b !important;color-scheme:light;}
#sb-app .sb-code-block{position:relative;background:#1e293b;border-radius:0 10px 10px 10px;padding:18px 16px;min-height:120px;overflow-x:auto;}
#sb-app .sb-code-block pre{margin:0;font-family:'Fira Code','Cascadia Code',monospace;font-size:13px;line-height:1.7;white-space:pre-wrap;color:#e2e8f0;}
#sb-app .sb-kw{color:#c084fc;}
#sb-app .sb-prop{color:#67e8f9;}
#sb-app .sb-val-c{color:#86efac;}
#sb-app .sb-copy-btn{position:absolute;top:10px;right:10px;padding:6px 14px;background:#6366f1;color:#fff;border:none;border-radius:6px;font-size:12px;font-weight:700;cursor:pointer;transition:background .15s;}
#sb-app .sb-copy-btn:hover{background:#4f46e5;}
#sb-app .sb-copy-btn.copied{background:#10b981;}
#sb-app .sb-scope-row{display:flex;align-items:center;gap:10px;margin-bottom:20px;padding:12px 16px;background:#fefce8;border:1px solid #fde68a;border-radius:8px;}
#sb-app .sb-scope-row label{font-size:13px;font-weight:600;color:#92400e;margin:0;}
#sb-app .sb-scope-row input[type=text]{flex:1;padding:6px 10px;border:1px solid #fcd34d;border-radius:6px;font-size:13px;font-family:monospace;background:#fff;}
#sb-app .sb-compat{margin-top:20px;padding:14px 18px;background:#f0fdf4;border:1px solid #bbf7d0;border-radius:10px;}
#sb-app .sb-compat h3{margin:0 0 8px;font-size:14px;font-weight:700;color:#166534;}
#sb-app .sb-compat table{width:100%;border-collapse:collapse;font-size:13px;}
#sb-app .sb-compat th{text-align:left;padding:4px 8px;color:#166534;font-weight:600;border-bottom:1px solid #bbf7d0;}
#sb-app .sb-compat td{padding:4px 8px;color:#374151;}
#sb-app .sb-compat .ok{color:#16a34a;font-weight:700;}
#sb-app .sb-compat .partial{color:#d97706;font-weight:700;}
#sb-app .sb-compat .no{color:#dc2626;font-weight:700;}
#sb-app .sb-crosslinks{margin-top:24px;padding:14px 18px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;font-size:14px;}
#sb-app .sb-crosslinks p{margin:4px 0;}
#sb-app .sb-crosslinks a{color:#6366f1;text-decoration:none;font-weight:600;}
#sb-app .sb-crosslinks a:hover{text-decoration:underline;}
</style>

<!-- Presets -->
<div style="margin-bottom:8px;">
<h2 style="font-size:1.25rem;margin-bottom:4px;">CSS Scrollbar Styler</h2>
<p style="font-size:14px;color:#64748b;margin:0 0 14px;">Customize your scrollbar and copy ready-to-use CSS for WebKit and Firefox.</p>
</div>

<div class="sb-presets" id="sb-presets">
<button class="sb-preset-btn" data-preset="minimal" onclick="sbApplyPreset('minimal')">Minimal</button>
<button class="sb-preset-btn" data-preset="dark" onclick="sbApplyPreset('dark')">Dark Mode</button>
<button class="sb-preset-btn" data-preset="colorful" onclick="sbApplyPreset('colorful')">Colorful</button>
<button class="sb-preset-btn" data-preset="rounded" onclick="sbApplyPreset('rounded')">Rounded</button>
<button class="sb-preset-btn" data-preset="hidden" onclick="sbApplyPreset('hidden')">Hidden</button>
</div>

<div class="sb-grid">
<!-- Controls Panel -->
<div class="sb-panel">
<h2>Controls</h2>

<div class="sb-control">
<label>Scrollbar Width Mode</label>
<select class="sb-select" id="sb-width-mode" onchange="sbWidthModeChange()">
<option value="auto">auto (default)</option>
<option value="thin">thin</option>
<option value="custom" selected>custom (px)</option>
</select>
</div>

<div class="sb-control" id="sb-custom-width-wrap">
<label>Custom Width: <span class="sb-val" id="sb-width-val">10px</span></label>
<input type="range" id="sb-width" min="2" max="32" value="10" oninput="sbUpdate()">
</div>

<div class="sb-control">
<label>Track Color</label>
<div class="sb-color-row">
<input type="color" id="sb-track-color" value="#f1f5f9" oninput="sbSyncColor('sb-track-color','sb-track-color-hex')">
<input type="text" id="sb-track-color-hex" value="#f1f5f9" oninput="sbSyncHex('sb-track-color','sb-track-color-hex')" maxlength="9">
</div>
</div>

<div class="sb-control">
<label>Thumb Color</label>
<div class="sb-color-row">
<input type="color" id="sb-thumb-color" value="#94a3b8" oninput="sbSyncColor('sb-thumb-color','sb-thumb-color-hex')">
<input type="text" id="sb-thumb-color-hex" value="#94a3b8" oninput="sbSyncHex('sb-thumb-color','sb-thumb-color-hex')" maxlength="9">
</div>
</div>

<div class="sb-control">
<label>Thumb Hover Color</label>
<div class="sb-color-row">
<input type="color" id="sb-thumb-hover-color" value="#6366f1" oninput="sbSyncColor('sb-thumb-hover-color','sb-thumb-hover-hex')">
<input type="text" id="sb-thumb-hover-hex" value="#6366f1" oninput="sbSyncHex('sb-thumb-hover-color','sb-thumb-hover-hex')" maxlength="9">
</div>
</div>

<div class="sb-control">
<label>Thumb Border-Radius: <span class="sb-val" id="sb-thumb-radius-val">6px</span></label>
<input type="range" id="sb-thumb-radius" min="0" max="50" value="6" oninput="sbUpdate()">
</div>

<div class="sb-control">
<label>Track Border-Radius: <span class="sb-val" id="sb-track-radius-val">0px</span></label>
<input type="range" id="sb-track-radius" min="0" max="50" value="0" oninput="sbUpdate()">
</div>
</div>

<!-- Preview Panel -->
<div class="sb-panel">
<h2>Live Preview</h2>
<div class="sb-preview-box" id="sb-preview">
<p>Scroll me to see your custom scrollbar in action. This preview box contains enough content to make scrolling necessary so you can see exactly how your scrollbar looks.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation.</p>
<p>Customize width, colors, and border-radius with the controls on the left. Your changes update the preview in real time.</p>
<p>Copy the generated CSS for WebKit (Chrome, Safari, Edge) or Firefox using the tabs below.</p>
<p>Use presets for quick starting points — then fine-tune to match your design system.</p>
<p>Try the "Hidden" preset to remove scrollbars while keeping scroll functionality.</p>
</div>
<p style="font-size:12px;color:#94a3b8;margin:6px 0 0;">Preview reflects your current settings.</p>
</div>
</div>

<!-- Scope selector -->
<div class="sb-scope-row">
<label>Apply to element (CSS selector):</label>
<input type="text" id="sb-scope" value="body" oninput="sbUpdate()" placeholder="e.g. body, .my-container, #sidebar">
<span style="font-size:12px;color:#92400e;">Leave <code>body</code> for global styles.</span>
</div>

<!-- CSS Output -->
<div class="sb-output-wrap">
<div class="sb-tabs">
<div class="sb-tab active" id="sb-tab-webkit" onclick="sbShowTab('webkit')">WebKit (Chrome/Safari/Edge)</div>
<div class="sb-tab" id="sb-tab-firefox" onclick="sbShowTab('firefox')">Firefox</div>
<div class="sb-tab" id="sb-tab-combined" onclick="sbShowTab('combined')">Combined</div>
</div>
<div class="sb-code-block">
<pre id="sb-output"></pre>
<button class="sb-copy-btn" id="sb-copy-btn" onclick="sbCopy()">Copy CSS</button>
</div>
</div>

<!-- Browser Compatibility -->
<div class="sb-compat">
<h3>Browser Compatibility</h3>
<table>
<thead>
<tr>
<th>Property</th>
<th>Chrome</th>
<th>Firefox</th>
<th>Safari</th>
<th>Edge</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>::-webkit-scrollbar</code></td>
<td class="ok">Yes</td>
<td class="no">No</td>
<td class="ok">Yes</td>
<td class="ok">Yes</td>
</tr>
<tr>
<td><code>scrollbar-width</code></td>
<td class="ok">121+</td>
<td class="ok">Yes</td>
<td class="ok">16+</td>
<td class="ok">121+</td>
</tr>
<tr>
<td><code>scrollbar-color</code></td>
<td class="ok">121+</td>
<td class="ok">Yes</td>
<td class="ok">16+</td>
<td class="ok">121+</td>
</tr>
<tr>
<td>Hover effects</td>
<td class="ok">Yes (WebKit)</td>
<td class="no">Not supported</td>
<td class="ok">Yes (WebKit)</td>
<td class="ok">Yes (WebKit)</td>
</tr>
</tbody>
</table>
<p style="margin:8px 0 0;font-size:12px;color:#374151;"><strong>Tip:</strong> Use the Combined output to support all modern browsers. Firefox does not support per-element scrollbar hover colors.</p>
</div>

<!-- Cross-links -->
<div class="sb-crosslinks">
<p>Style buttons &rarr; <a href="/tools/css-button-generator/">CSS Button Generator</a></p>
<p>Customize animations &rarr; <a href="/tools/css-animation-generator/">CSS Animation Generator</a></p>
<p>CSS variables &rarr; <a href="/tools/css-variables-generator/">CSS Variables Generator</a></p>
</div>

<script>
(function(){
var currentTab = 'webkit';

var presets = {
minimal: {
widthMode:'thin', width:6,
trackColor:'#f8fafc', thumbColor:'#cbd5e1', thumbHover:'#94a3b8',
thumbRadius:2, trackRadius:0
},
dark: {
widthMode:'custom', width:8,
trackColor:'#1e293b', thumbColor:'#475569', thumbHover:'#94a3b8',
thumbRadius:4, trackRadius:0
},
colorful: {
widthMode:'custom', width:12,
trackColor:'#fef3c7', thumbColor:'#f59e0b', thumbHover:'#d97706',
thumbRadius:6, trackRadius:4
},
rounded: {
widthMode:'custom', width:10,
trackColor:'#f0fdf4', thumbColor:'#4ade80', thumbHover:'#16a34a',
thumbRadius:50, trackRadius:50
},
hidden: {
widthMode:'thin', width:0,
trackColor:'transparent', thumbColor:'transparent', thumbHover:'transparent',
thumbRadius:0, trackRadius:0
}
};

function g(id){ return document.getElementById(id); }

function sbApplyPreset(name){
var p = presets[name];
if(!p) return;
g('sb-width-mode').value = p.widthMode;
g('sb-width').value = p.width;
g('sb-track-color').value = p.trackColor;
g('sb-track-color-hex').value = p.trackColor;
g('sb-thumb-color').value = p.thumbColor;
g('sb-thumb-color-hex').value = p.thumbColor;
g('sb-thumb-hover-color').value = p.thumbHover;
g('sb-thumb-hover-hex').value = p.thumbHover;
g('sb-thumb-radius').value = p.thumbRadius;
g('sb-track-radius').value = p.trackRadius;
sbWidthModeChange();
document.querySelectorAll('#sb-app .sb-preset-btn').forEach(function(b){
b.classList.toggle('active', b.dataset.preset === name);
});
sbUpdate();
}

function sbWidthModeChange(){
var mode = g('sb-width-mode').value;
var wrap = g('sb-custom-width-wrap');
wrap.style.display = (mode === 'custom') ? '' : 'none';
sbUpdate();
}

function sbSyncColor(colorId, hexId){
g(hexId).value = g(colorId).value;
sbUpdate();
}

function sbSyncHex(colorId, hexId){
var val = g(hexId).value;
if(/^#([0-9a-fA-F]{3}|[0-9a-fA-F]{6})$/.test(val)){
g(colorId).value = val;
}
sbUpdate();
}

function getState(){
var widthMode = g('sb-width-mode').value;
var width = parseInt(g('sb-width').value);
var trackColor = g('sb-track-color-hex').value || g('sb-track-color').value;
var thumbColor = g('sb-thumb-color-hex').value || g('sb-thumb-color').value;
var thumbHover = g('sb-thumb-hover-hex').value || g('sb-thumb-hover-color').value;
var thumbRadius = parseInt(g('sb-thumb-radius').value);
var trackRadius = parseInt(g('sb-track-radius').value);
var scope = g('sb-scope').value.trim() || 'body';
return {widthMode, width, trackColor, thumbColor, thumbHover, thumbRadius, trackRadius, scope};
}

function buildWebkit(s){
var w = s.widthMode === 'custom' ? s.width + 'px' : s.widthMode === 'thin' ? '6px' : '16px';
var lines = [];
lines.push(s.scope + '::-webkit-scrollbar {');
lines.push('  width: ' + w + ';');
lines.push('}');
lines.push(s.scope + '::-webkit-scrollbar-track {');
lines.push('  background: ' + s.trackColor + ';');
if(s.trackRadius > 0) lines.push('  border-radius: ' + s.trackRadius + 'px;');
lines.push('}');
lines.push(s.scope + '::-webkit-scrollbar-thumb {');
lines.push('  background: ' + s.thumbColor + ';');
if(s.thumbRadius > 0) lines.push('  border-radius: ' + s.thumbRadius + 'px;');
lines.push('}');
lines.push(s.scope + '::-webkit-scrollbar-thumb:hover {');
lines.push('  background: ' + s.thumbHover + ';');
lines.push('}');
return lines.join('\n');
}

function buildFirefox(s){
var ffWidth = s.widthMode === 'custom' ? (s.width <= 6 ? 'thin' : 'auto') : s.widthMode;
if(s.trackColor === 'transparent' && s.thumbColor === 'transparent') ffWidth = 'none';
var lines = [];
lines.push(s.scope + ' {');
lines.push('  scrollbar-width: ' + ffWidth + ';');
lines.push('  scrollbar-color: ' + s.thumbColor + ' ' + s.trackColor + ';');
lines.push('}');
return lines.join('\n');
}

function buildCombined(s){
return buildWebkit(s) + '\n\n/* Firefox */\n' + buildFirefox(s);
}

function syntaxHighlight(css){
return css
.replace(/(::-webkit-[\w-]+(?::[\w-]+)?|scrollbar-[\w-]+)/g, '<span class="sb-prop">$1</span>')
.replace(/(#[0-9a-fA-F]{3,8}|transparent|none|thin|auto|body|[\w#.-]+(?:::[:\w-]+)?(?:\s+[:\w-]+)*\s*(?=\{))/g, function(m){
if(m.trim().endsWith('{')) return '<span class="sb-kw">' + m + '</span>';
return m;
})
.replace(/(\/\*[^*]*\*+(?:[^/*][^*]*\*+)*\/)/g, '<span style="color:#64748b;">$1</span>');
}

function sbUpdate(){
var s = getState();
g('sb-width-val').textContent = s.width + 'px';
g('sb-thumb-radius-val').textContent = s.thumbRadius + 'px';
g('sb-track-radius-val').textContent = s.trackRadius + 'px';

// Update preview scrollbar via injected style
var styleEl = document.getElementById('sb-preview-style');
if(!styleEl){
styleEl = document.createElement('style');
styleEl.id = 'sb-preview-style';
document.head.appendChild(styleEl);
}
var pw = s.widthMode === 'custom' ? s.width + 'px' : s.widthMode === 'thin' ? '6px' : '16px';
styleEl.textContent = [
'#sb-preview::-webkit-scrollbar { width: ' + pw + '; }',
'#sb-preview::-webkit-scrollbar-track { background: ' + s.trackColor + '; border-radius: ' + s.trackRadius + 'px; }',
'#sb-preview::-webkit-scrollbar-thumb { background: ' + s.thumbColor + '; border-radius: ' + s.thumbRadius + 'px; }',
'#sb-preview::-webkit-scrollbar-thumb:hover { background: ' + s.thumbHover + '; }',
'#sb-preview { scrollbar-width: ' + (s.widthMode === 'thin' ? 'thin' : 'auto') + '; scrollbar-color: ' + s.thumbColor + ' ' + s.trackColor + '; }'
].join('\n');

// Update code output
var code = currentTab === 'webkit' ? buildWebkit(s) : currentTab === 'firefox' ? buildFirefox(s) : buildCombined(s);
g('sb-output').innerHTML = syntaxHighlight(escHtml(code));
g('sb-output').dataset.raw = code;
}

function escHtml(str){
return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function sbShowTab(tab){
currentTab = tab;
['webkit','firefox','combined'].forEach(function(t){
var el = g('sb-tab-' + t);
if(el) el.classList.toggle('active', t === tab);
});
sbUpdate();
}

function sbCopy(){
var raw = g('sb-output').dataset.raw || g('sb-output').textContent;
navigator.clipboard.writeText(raw).then(function(){
var btn = g('sb-copy-btn');
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function(){ btn.textContent = 'Copy CSS'; btn.classList.remove('copied'); }, 2000);
});
}

// Expose to global for inline onclick handlers
window.sbApplyPreset = sbApplyPreset;
window.sbWidthModeChange = sbWidthModeChange;
window.sbSyncColor = sbSyncColor;
window.sbSyncHex = sbSyncHex;
window.sbShowTab = sbShowTab;
window.sbCopy = sbCopy;
window.sbUpdate = sbUpdate;

// Init
sbWidthModeChange();
sbUpdate();
})();
</script>

</div>
