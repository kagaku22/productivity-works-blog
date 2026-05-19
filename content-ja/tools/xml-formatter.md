---
title: "XML整形・バリデーションツール"
description: "無料のXML整形ツール。XMLの整形・圧縮・構文検証・JSON変換をブラウザで完結。シンタックスハイライト・ツリー表示対応。会員登録不要。"
date: 2025-08-09
slug: xml-formatter
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/xml-formatter-ja.png
  alt: "XML整形・バリデーションツール - 無料オンラインツール"
---

<div id="xf-app">

<style>
#xf-app *,#xf-app *::before,#xf-app *::after{box-sizing:border-box;margin:0;padding:0}
#xf-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Hiragino Sans","Yu Gothic UI",sans-serif;font-size:15px;color:#1e293b;line-height:1.6}
#xf-app .xf-toolbar{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:10px;align-items:center}
#xf-app .xf-btn{display:inline-flex;align-items:center;gap:5px;padding:7px 14px;border:none;border-radius:6px;font-size:13px;font-weight:600;cursor:pointer;transition:background .15s,transform .1s;white-space:nowrap}
#xf-app .xf-btn:active{transform:scale(.97)}
#xf-app .xf-btn-primary{background:#2563eb;color:#fff}
#xf-app .xf-btn-primary:hover{background:#1d4ed8}
#xf-app .xf-btn-secondary{background:#f1f5f9;color:#334155;border:1px solid #cbd5e1}
#xf-app .xf-btn-secondary:hover{background:#e2e8f0}
#xf-app .xf-btn-success{background:#16a34a;color:#fff}
#xf-app .xf-btn-success:hover{background:#15803d}
#xf-app .xf-btn-warning{background:#d97706;color:#fff}
#xf-app .xf-btn-warning:hover{background:#b45309}
#xf-app .xf-btn-info{background:#0891b2;color:#fff}
#xf-app .xf-btn-info:hover{background:#0e7490}
#xf-app .xf-btn-danger{background:#dc2626;color:#fff}
#xf-app .xf-btn-danger:hover{background:#b91c1c}
#xf-app .xf-select{padding:7px 10px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;background:#fff;color:#334155;cursor:pointer}
#xf-app .xf-panels{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px}
@media(max-width:700px){#xf-app .xf-panels{grid-template-columns:1fr}}
#xf-app .xf-panel{display:flex;flex-direction:column;gap:6px}
#xf-app .xf-panel-label{font-size:12px;font-weight:700;color:#64748b;text-transform:uppercase;letter-spacing:.05em}
#xf-app .xf-editor-wrap{position:relative;border:1.5px solid #cbd5e1;border-radius:8px;overflow:hidden;background:#fafafa}
#xf-app .xf-editor-wrap.xf-error-border{border-color:#ef4444}
#xf-app .xf-editor-wrap.xf-ok-border{border-color:#22c55e}
#xf-app .xf-with-lines{display:flex}
#xf-app .xf-line-nums{width:36px;min-width:36px;background:#f1f5f9;color:#94a3b8;font-family:"JetBrains Mono","Fira Code","Cascadia Code",monospace;font-size:12px;line-height:1.6;padding:10px 0;text-align:right;padding-right:6px;user-select:none;overflow:hidden;border-right:1px solid #e2e8f0}
#xf-app .xf-line-nums span{display:block}
#xf-app .xf-textarea{width:100%;min-height:280px;padding:10px 12px;border:none;background:transparent;font-family:"JetBrains Mono","Fira Code","Cascadia Code",monospace;font-size:13px;line-height:1.6;color:#1e293b;resize:vertical;outline:none}
#xf-app .xf-output-pre{width:100%;min-height:280px;padding:10px 12px;font-family:"JetBrains Mono","Fira Code","Cascadia Code",monospace;font-size:13px;line-height:1.6;overflow:auto;white-space:pre;background:transparent}
#xf-app .xf-status{display:flex;align-items:center;gap:8px;padding:9px 14px;border-radius:8px;font-size:13px;font-weight:600;min-height:40px}
#xf-app .xf-status.xf-idle{background:#f8fafc;color:#64748b;border:1px solid #e2e8f0}
#xf-app .xf-status.xf-ok{background:#f0fdf4;color:#16a34a;border:1px solid #bbf7d0}
#xf-app .xf-status.xf-err{background:#fef2f2;color:#dc2626;border:1px solid #fecaca}
#xf-app .xf-status-dot{width:8px;height:8px;border-radius:50%;background:currentColor;flex-shrink:0}
#xf-app .xf-tab-bar{display:flex;gap:4px;margin-bottom:8px}
#xf-app .xf-tab{padding:6px 14px;border-radius:6px 6px 0 0;border:1.5px solid #e2e8f0;border-bottom:none;font-size:13px;font-weight:600;cursor:pointer;background:#f8fafc;color:#64748b;transition:background .15s}
#xf-app .xf-tab.xf-tab-active{background:#fff;color:#2563eb;border-color:#2563eb;border-bottom:2px solid #fff}
#xf-app .xf-tab-content{display:none}
#xf-app .xf-tab-content.xf-tab-visible{display:block}
#xf-app .xf-tree{padding:10px 12px;min-height:200px;font-family:"JetBrains Mono","Fira Code",monospace;font-size:12.5px;line-height:1.7;overflow:auto}
#xf-app .xf-tree-node{cursor:pointer;user-select:none}
#xf-app .xf-tree-node:hover{background:#f0f9ff;border-radius:3px}
#xf-app .xf-tree-toggle{display:inline-block;width:14px;text-align:center;color:#94a3b8;font-size:10px}
#xf-app .xf-tree-children{margin-left:18px}
#xf-app .xf-tree-tag{color:#2563eb;font-weight:600}
#xf-app .xf-tree-attr{color:#7c3aed}
#xf-app .xf-tree-text{color:#374151}
#xf-app .xf-tree-comment{color:#6b7280;font-style:italic}
#xf-app .xf-hl-tag{color:#1d4ed8;font-weight:600}
#xf-app .xf-hl-attr{color:#7c3aed}
#xf-app .xf-hl-val{color:#15803d}
#xf-app .xf-hl-cdata{color:#b45309}
#xf-app .xf-hl-comment{color:#6b7280;font-style:italic}
#xf-app .xf-hl-pi{color:#0e7490}
#xf-app .xf-hl-text{color:#374151}
#xf-app .xf-copy-tip{font-size:12px;color:#16a34a;font-weight:600;opacity:0;transition:opacity .3s}
#xf-app .xf-copy-tip.xf-show{opacity:1}
#xf-app .xf-related{margin-top:20px;padding:14px 16px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:8px;font-size:13px}
#xf-app .xf-related p{margin:0 0 6px;font-weight:600;color:#475569}
#xf-app .xf-related a{color:#2563eb;text-decoration:none;margin-right:12px}
#xf-app .xf-related a:hover{text-decoration:underline}
#xf-app .xf-freee-cta{margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px}
</style>

<div class="xf-toolbar">
<button class="xf-btn xf-btn-primary" id="xf-btn-format">&#9654; 整形</button>
<button class="xf-btn xf-btn-secondary" id="xf-btn-minify">&#9646;&#9646; 圧縮</button>
<button class="xf-btn xf-btn-success" id="xf-btn-validate">&#10003; 検証</button>
<button class="xf-btn xf-btn-info" id="xf-btn-to-json">&#123;&#125; JSON変換</button>
<select class="xf-select" id="xf-indent">
<option value="2">スペース2</option>
<option value="4" selected>スペース4</option>
<option value="tab">タブ</option>
</select>
<button class="xf-btn xf-btn-secondary" id="xf-btn-sample">&#128196; サンプル</button>
<button class="xf-btn xf-btn-danger" id="xf-btn-clear">&#215; クリア</button>
<button class="xf-btn xf-btn-secondary" id="xf-btn-copy-in">&#128203; 入力をコピー</button>
</div>

<div id="xf-status" class="xf-status xf-idle"><span class="xf-status-dot"></span><span id="xf-status-msg">XMLを貼り付けて「整形」または「検証」をクリックしてください。</span></div>

<div class="xf-panels" style="margin-top:10px">
<div class="xf-panel">
<div class="xf-panel-label">入力XML</div>
<div class="xf-editor-wrap" id="xf-in-wrap">
<div class="xf-with-lines">
<div class="xf-line-nums" id="xf-line-nums"></div>
<textarea class="xf-textarea" id="xf-input" spellcheck="false" placeholder="XMLをここに貼り付けてください..."></textarea>
</div>
</div>
</div>
<div class="xf-panel">
<div class="xf-panel-label" style="display:flex;justify-content:space-between;align-items:center">
<span id="xf-out-label">出力</span>
<span class="xf-copy-tip" id="xf-copy-tip">コピーしました！</span>
</div>
<div class="xf-tab-bar">
<div class="xf-tab xf-tab-active" data-tab="formatted">整形済み</div>
<div class="xf-tab" data-tab="tree">ツリー表示</div>
<div class="xf-tab" data-tab="json">JSON</div>
</div>
<div class="xf-editor-wrap" id="xf-out-wrap">
<div class="xf-tab-content xf-tab-visible" id="xf-tab-formatted">
<pre class="xf-output-pre" id="xf-output"></pre>
</div>
<div class="xf-tab-content" id="xf-tab-tree">
<div class="xf-tree" id="xf-tree-view"></div>
</div>
<div class="xf-tab-content" id="xf-tab-json">
<pre class="xf-output-pre" id="xf-json-output"></pre>
</div>
</div>
<button class="xf-btn xf-btn-secondary" id="xf-btn-copy-out" style="align-self:flex-start;margin-top:4px">&#128203; 出力をコピー</button>
</div>
</div>

<div class="xf-freee-cta">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">開発チームの会計管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、SaaS利用料・サーバー費用の経費管理もクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div class="xf-related">
<p>関連ツール</p>
JSONを整形 &rarr; <a href="/ja/tools/json-formatter/">JSON整形ツール</a>
&nbsp;|&nbsp; CSV &harr; JSON変換 &rarr; <a href="/ja/tools/csv-to-json/">CSV⇔JSON変換ツール</a>
&nbsp;|&nbsp; SQLを整形 &rarr; <a href="/ja/tools/sql-formatter/">SQLフォーマッター</a>
</div>

<script>
(function(){
'use strict';

// ── DOM refs ──────────────────────────────────────────────────────────────
var inp       = document.getElementById('xf-input');
var outPre    = document.getElementById('xf-output');
var jsonOut   = document.getElementById('xf-json-output');
var treeView  = document.getElementById('xf-tree-view');
var statusEl  = document.getElementById('xf-status');
var statusMsg = document.getElementById('xf-status-msg');
var inWrap    = document.getElementById('xf-in-wrap');
var outWrap   = document.getElementById('xf-out-wrap');
var lineNums  = document.getElementById('xf-line-nums');
var copyTip   = document.getElementById('xf-copy-tip');
var indentSel = document.getElementById('xf-indent');

var tabs      = document.querySelectorAll('#xf-app .xf-tab');
var tabPanes  = {
formatted: document.getElementById('xf-tab-formatted'),
tree:      document.getElementById('xf-tab-tree'),
json:      document.getElementById('xf-tab-json')
};
var activeTab = 'formatted';

// ── Helpers ───────────────────────────────────────────────────────────────
function getIndent() {
var v = indentSel.value;
if (v === 'tab') return '\t';
return ' '.repeat(parseInt(v, 10));
}

function setStatus(type, msg) {
statusEl.className = 'xf-status xf-' + type;
statusMsg.textContent = msg;
inWrap.className  = 'xf-editor-wrap' + (type === 'err' ? ' xf-error-border' : type === 'ok' ? ' xf-ok-border' : '');
outWrap.className = 'xf-editor-wrap' + (type === 'err' ? ' xf-error-border' : type === 'ok' ? ' xf-ok-border' : '');
}

function updateLineNums() {
var lines = inp.value.split('\n').length;
var html = '';
for (var i = 1; i <= lines; i++) html += '<span>' + i + '</span>';
lineNums.innerHTML = html;
}

inp.addEventListener('input', updateLineNums);
updateLineNums();

// ── XML Parser (browser DOMParser) ────────────────────────────────────────
function parseXML(src) {
var parser = new DOMParser();
var doc = parser.parseFromString(src, 'application/xml');
var err = doc.querySelector('parsererror');
if (err) {
var msg = err.textContent.replace(/\s+/g, ' ').trim();
var lineMatch = msg.match(/line[:\s]+(\d+)/i) || msg.match(/(\d+)/);
var lineInfo = lineMatch ? '（' + lineMatch[1] + '行目付近）' : '';
throw new Error(msg.slice(0, 120) + lineInfo);
}
return doc;
}

// ── Formatter ─────────────────────────────────────────────────────────────
function escapeHtml(s) {
return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function formatNode(node, indent, level) {
var ind = indent.repeat(level);

if (node.nodeType === 8) {
return ind + '<span class="xf-hl-comment">&lt;!--' + escapeHtml(node.nodeValue) + '--&gt;</span>';
}
if (node.nodeType === 7) {
return ind + '<span class="xf-hl-pi">&lt;?' + escapeHtml(node.nodeName) + ' ' + escapeHtml(node.nodeValue) + '?&gt;</span>';
}
if (node.nodeType === 4) {
return ind + '<span class="xf-hl-cdata">&lt;![CDATA[' + escapeHtml(node.nodeValue) + ']]&gt;</span>';
}
if (node.nodeType === 3) {
var t = node.nodeValue.trim();
if (!t) return null;
return ind + '<span class="xf-hl-text">' + escapeHtml(t) + '</span>';
}
if (node.nodeType === 9) {
var parts = [];
node.childNodes.forEach(function(c){ var r = formatNode(c, indent, 0); if(r) parts.push(r); });
return parts.join('\n');
}

var tagName = escapeHtml(node.nodeName);
var attrStr = '';
if (node.attributes) {
for (var i = 0; i < node.attributes.length; i++) {
var a = node.attributes[i];
attrStr += ' <span class="xf-hl-attr">' + escapeHtml(a.name) + '</span>=<span class="xf-hl-val">"' + escapeHtml(a.value) + '"</span>';
}
}

var children = [];
node.childNodes.forEach(function(c){ var r = formatNode(c, indent, level + 1); if(r !== null) children.push(r); });

var open = ind + '&lt;<span class="xf-hl-tag">' + tagName + '</span>' + attrStr;

if (children.length === 0) {
return open + ' /&gt;';
}

if (children.length === 1 && node.childNodes.length === 1 && node.firstChild.nodeType === 3) {
return open + '&gt;' +
'<span class="xf-hl-text">' + escapeHtml(node.firstChild.nodeValue.trim()) + '</span>' +
'&lt;/<span class="xf-hl-tag">' + tagName + '</span>&gt;';
}

return open + '&gt;\n' + children.join('\n') + '\n' + ind + '&lt;/<span class="xf-hl-tag">' + tagName + '</span>&gt;';
}

// ── Minifier ──────────────────────────────────────────────────────────────
function minifyXML(src) {
return src
.replace(/>\s+</g, '><')
.replace(/\s+/g, ' ')
.replace(/> </g, '><')
.trim();
}

// ── XML → JSON ────────────────────────────────────────────────────────────
function xmlNodeToJSON(node) {
if (node.nodeType === 3 || node.nodeType === 4) {
var t = node.nodeValue.trim();
return t ? t : null;
}
if (node.nodeType !== 1) return null;

var obj = {};
if (node.attributes && node.attributes.length > 0) {
obj['@attributes'] = {};
for (var i = 0; i < node.attributes.length; i++) {
obj['@attributes'][node.attributes[i].name] = node.attributes[i].value;
}
}
var textContent = '';
node.childNodes.forEach(function(child) {
if (child.nodeType === 3 || child.nodeType === 4) {
textContent += child.nodeValue.trim();
} else if (child.nodeType === 1) {
var childJSON = xmlNodeToJSON(child);
var name = child.nodeName;
if (obj[name] !== undefined) {
if (!Array.isArray(obj[name])) obj[name] = [obj[name]];
obj[name].push(childJSON);
} else {
obj[name] = childJSON;
}
}
});
if (textContent) obj['#text'] = textContent;
return obj;
}

function xmlDocToJSON(doc) {
var root = doc.documentElement;
var result = {};
result[root.nodeName] = xmlNodeToJSON(root);
return JSON.stringify(result, null, 2);
}

// ── Tree View ─────────────────────────────────────────────────────────────
function buildTreeHTML(node, level) {
if (node.nodeType === 8) {
return '<div class="xf-tree-node" style="padding-left:' + (level*14) + 'px"><span class="xf-tree-comment">&lt;!--' + escapeHtml(node.nodeValue.trim()) + '--&gt;</span></div>';
}
if (node.nodeType === 3) {
var t = node.nodeValue.trim();
if (!t) return '';
return '<div style="padding-left:' + (level*14) + 'px"><span class="xf-tree-text">"' + escapeHtml(t) + '"</span></div>';
}
if (node.nodeType !== 1) return '';

var tag = node.nodeName;
var attrParts = [];
if (node.attributes) {
for (var i = 0; i < node.attributes.length; i++) {
var a = node.attributes[i];
attrParts.push('<span class="xf-tree-attr"> ' + escapeHtml(a.name) + '=</span><span class="xf-hl-val">"' + escapeHtml(a.value) + '"</span>');
}
}

var hasChildren = false;
node.childNodes.forEach(function(c){
if (c.nodeType === 1 || (c.nodeType === 3 && c.nodeValue.trim())) hasChildren = true;
});

var id = 'xf-t-' + Math.random().toString(36).slice(2);
var toggle = hasChildren ? '<span class="xf-tree-toggle" onclick="var e=document.getElementById(\'' + id + '\');e.style.display=e.style.display===\'none\'?\'block\':\'none\';">&#9660;</span>' : '<span class="xf-tree-toggle"></span>';
var header = '<div class="xf-tree-node" style="padding-left:' + (level*14) + 'px">' + toggle +
'&lt;<span class="xf-tree-tag">' + escapeHtml(tag) + '</span>' + attrParts.join('') + '&gt;</div>';

if (!hasChildren) {
return '<div style="padding-left:' + (level*14) + 'px"><span class="xf-tree-toggle"></span>&lt;<span class="xf-tree-tag">' + escapeHtml(tag) + '</span>' + attrParts.join('') + ' /&gt;</div>';
}

var childHTML = '';
node.childNodes.forEach(function(c){ childHTML += buildTreeHTML(c, level + 1); });
return header + '<div id="' + id + '">' + childHTML + '</div>';
}

// ── Tab switching ─────────────────────────────────────────────────────────
tabs.forEach(function(tab) {
tab.addEventListener('click', function() {
tabs.forEach(function(t){ t.classList.remove('xf-tab-active'); });
Object.values(tabPanes).forEach(function(p){ p.classList.remove('xf-tab-visible'); });
tab.classList.add('xf-tab-active');
activeTab = tab.dataset.tab;
tabPanes[activeTab].classList.add('xf-tab-visible');
});
});

// ── Core actions ──────────────────────────────────────────────────────────
function doFormat() {
var src = inp.value.trim();
if (!src) { setStatus('idle', 'XMLを貼り付けて「整形」をクリックしてください。'); return; }
try {
var doc = parseXML(src);
var indent = getIndent();
var highlighted = formatNode(doc, indent, 0);
outPre.innerHTML = highlighted;
setStatus('ok', 'XMLの整形が完了しました。');
treeView.innerHTML = buildTreeHTML(doc.documentElement, 0);
try { jsonOut.textContent = xmlDocToJSON(doc); } catch(e){}
} catch(e) {
outPre.innerHTML = '';
setStatus('err', 'パースエラー: ' + e.message);
}
}

function doMinify() {
var src = inp.value.trim();
if (!src) { setStatus('idle', 'XMLを貼り付けて「圧縮」をクリックしてください。'); return; }
try {
parseXML(src);
outPre.innerHTML = escapeHtml(minifyXML(src));
setStatus('ok', 'XMLの圧縮が完了しました。');
} catch(e) {
setStatus('err', 'パースエラー: ' + e.message);
}
}

function doValidate() {
var src = inp.value.trim();
if (!src) { setStatus('idle', 'XMLを貼り付けて「検証」をクリックしてください。'); return; }
try {
var doc = parseXML(src);
var elCount = doc.getElementsByTagName('*').length;
setStatus('ok', '有効なXMLです。要素数: ' + elCount + '個。');
} catch(e) {
setStatus('err', '無効なXML: ' + e.message);
}
}

function doToJSON() {
var src = inp.value.trim();
if (!src) { setStatus('idle', 'XMLを貼り付けて「JSON変換」をクリックしてください。'); return; }
try {
var doc = parseXML(src);
var json = xmlDocToJSON(doc);
jsonOut.textContent = json;
tabs.forEach(function(t){ t.classList.remove('xf-tab-active'); });
Object.values(tabPanes).forEach(function(p){ p.classList.remove('xf-tab-visible'); });
document.querySelector('[data-tab="json"]').classList.add('xf-tab-active');
tabPanes['json'].classList.add('xf-tab-visible');
activeTab = 'json';
setStatus('ok', 'JSONへの変換が完了しました。');
} catch(e) {
setStatus('err', 'パースエラー: ' + e.message);
}
}

// ── Copy ──────────────────────────────────────────────────────────────────
function copyText(text) {
if (navigator.clipboard) {
navigator.clipboard.writeText(text).then(showCopied);
} else {
var ta = document.createElement('textarea');
ta.value = text;
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
showCopied();
}
}

function showCopied() {
copyTip.classList.add('xf-show');
setTimeout(function(){ copyTip.classList.remove('xf-show'); }, 1800);
}

document.getElementById('xf-btn-copy-in').addEventListener('click', function(){ copyText(inp.value); });
document.getElementById('xf-btn-copy-out').addEventListener('click', function(){
var txt = '';
if (activeTab === 'formatted') txt = outPre.innerText || outPre.textContent;
else if (activeTab === 'json') txt = jsonOut.textContent;
else txt = treeView.innerText || treeView.textContent;
copyText(txt);
});

// ── Sample XML ────────────────────────────────────────────────────────────
var SAMPLE_XML = '<?xml version="1.0" encoding="UTF-8"?>\n<bookstore>\n  <book category="fiction">\n    <title lang="ja">吾輩は猫である</title>\n    <author>夏目漱石</author>\n    <year>1905</year>\n    <price currency="JPY">880</price>\n  </book>\n  <book category="technology">\n    <title lang="ja">プログラマー脳</title>\n    <author>フェリエンヌ・ヘルマンス</author>\n    <year>2023</year>\n    <price currency="JPY">2860</price>\n  </book>\n  <!-- 書籍データはここに追加できます -->\n  <metadata>\n    <lastUpdated>2026-05-16</lastUpdated>\n    <totalBooks>2</totalBooks>\n  </metadata>\n</bookstore>';

document.getElementById('xf-btn-sample').addEventListener('click', function(){
inp.value = SAMPLE_XML;
updateLineNums();
setStatus('idle', 'サンプルXMLを読み込みました。「整形」をクリックして整形してください。');
});

document.getElementById('xf-btn-clear').addEventListener('click', function(){
inp.value = '';
outPre.innerHTML = '';
jsonOut.textContent = '';
treeView.innerHTML = '';
updateLineNums();
setStatus('idle', 'クリアしました。XMLを貼り付けて操作してください。');
inWrap.className = 'xf-editor-wrap';
outWrap.className = 'xf-editor-wrap';
});

// ── Button bindings ───────────────────────────────────────────────────────
document.getElementById('xf-btn-format').addEventListener('click', doFormat);
document.getElementById('xf-btn-minify').addEventListener('click', doMinify);
document.getElementById('xf-btn-validate').addEventListener('click', doValidate);
document.getElementById('xf-btn-to-json').addEventListener('click', doToJSON);

// ── Keyboard shortcut: Ctrl+Enter = Format ────────────────────────────────
inp.addEventListener('keydown', function(e){
if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') { e.preventDefault(); doFormat(); }
});

})();
</script>

</div>

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
