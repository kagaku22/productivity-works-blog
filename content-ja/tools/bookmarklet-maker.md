---
title: "ブックマークレット作成ツール"
description: "無料のブックマークレット作成ツール。JavaScriptコードをブックマークレットURLに変換。圧縮・エンコード・テスト機能付き。すぐ使えるサンプル付き。"
slug: bookmarklet-maker
date: 2025-07-12
categories: ["無料ツール"]
cover:
  image: /images/covers/bookmarklet-maker-ja.png
  alt: "ブックマークレット作成ツール — JavaScriptをブックマークレットURLに変換"
ShowToc: false
---

**ブックマークレット**とは、どのWebページでもJavaScriptを実行できるブックマークです。以下にJSコードを貼り付けて「変換」をクリック、ブックマークバーにドラッグするだけで即使えます — 拡張機能不要。

<div id="bm-app">
<style>
#bm-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1a1a2e;
}
#bm-app * { box-sizing: border-box; }
#bm-app h2 {
font-size: 1.15rem;
font-weight: 700;
margin: 1.6rem 0 0.5rem;
color: #0f3460;
border-left: 4px solid #e94560;
padding-left: 0.6rem;
}
#bm-app .bm-section {
background: #f8f9fc;
border: 1px solid #dde3f0;
border-radius: 10px;
padding: 1.2rem 1.4rem;
margin-bottom: 1.2rem;
}
#bm-app label {
display: block;
font-weight: 600;
font-size: 0.85rem;
margin-bottom: 0.35rem;
color: #333;
}
#bm-app textarea {
width: 100%;
min-height: 180px;
font-family: 'Courier New', Courier, monospace;
font-size: 0.88rem;
line-height: 1.55;
padding: 0.8rem 1rem;
border: 1.5px solid #c8d0e0;
border-radius: 7px;
background: #fff;
color: #1a1a2e;
resize: vertical;
transition: border-color 0.2s;
}
#bm-app textarea:focus {
outline: none;
border-color: #0f3460;
}
#bm-app .bm-options {
display: flex;
flex-wrap: wrap;
gap: 1rem;
align-items: center;
margin-top: 0.8rem;
}
#bm-app .bm-check {
display: flex;
align-items: center;
gap: 0.4rem;
font-size: 0.88rem;
cursor: pointer;
user-select: none;
}
#bm-app .bm-check input { cursor: pointer; width: 16px; height: 16px; }
#bm-app .bm-btn-row {
display: flex;
flex-wrap: wrap;
gap: 0.6rem;
margin-top: 1rem;
}
#bm-app .bm-btn {
padding: 0.55rem 1.2rem;
border: none;
border-radius: 6px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: opacity 0.15s, transform 0.1s;
}
#bm-app .bm-btn:hover { opacity: 0.88; transform: translateY(-1px); }
#bm-app .bm-btn:active { transform: translateY(0); }
#bm-app .bm-btn-primary { background: #e94560; color: #fff; }
#bm-app .bm-btn-secondary { background: #0f3460; color: #fff; }
#bm-app .bm-btn-ghost {
background: transparent;
color: #0f3460;
border: 1.5px solid #0f3460;
}
#bm-app .bm-btn-sm {
padding: 0.35rem 0.75rem;
font-size: 0.8rem;
}
#bm-app .bm-output-wrap {
position: relative;
margin-top: 0.5rem;
}
#bm-app .bm-output {
width: 100%;
min-height: 80px;
font-family: 'Courier New', Courier, monospace;
font-size: 0.82rem;
line-height: 1.5;
padding: 0.75rem 3.5rem 0.75rem 1rem;
border: 1.5px solid #c8d0e0;
border-radius: 7px;
background: #fff;
color: #1a1a2e;
word-break: break-all;
white-space: pre-wrap;
resize: vertical;
}
#bm-app .bm-copy-btn {
position: absolute;
top: 0.5rem;
right: 0.5rem;
padding: 0.3rem 0.6rem;
font-size: 0.75rem;
font-weight: 600;
background: #0f3460;
color: #fff;
border: none;
border-radius: 5px;
cursor: pointer;
transition: opacity 0.15s;
}
#bm-app .bm-copy-btn:hover { opacity: 0.8; }
#bm-app .bm-stats {
display: flex;
gap: 1.5rem;
margin-top: 0.5rem;
font-size: 0.8rem;
color: #666;
}
#bm-app .bm-stats span strong { color: #0f3460; }
#bm-app .bm-drag-box {
margin-top: 0.8rem;
padding: 0.9rem 1.2rem;
background: #eaf0ff;
border: 2px dashed #7fa7e0;
border-radius: 8px;
font-size: 0.88rem;
color: #2a4a7f;
text-align: center;
}
#bm-app .bm-drag-link {
display: inline-block;
margin-top: 0.5rem;
padding: 0.4rem 1rem;
background: #fff;
border: 1.5px solid #7fa7e0;
border-radius: 5px;
font-weight: 700;
color: #0f3460;
text-decoration: none;
cursor: grab;
}
#bm-app .bm-drag-link:hover { background: #ddeaff; }
#bm-app .bm-presets {
display: flex;
flex-wrap: wrap;
gap: 0.5rem;
margin-top: 0.3rem;
}
#bm-app .bm-preset-btn {
padding: 0.38rem 0.85rem;
background: #fff;
border: 1.5px solid #c8d0e0;
border-radius: 20px;
font-size: 0.82rem;
cursor: pointer;
transition: border-color 0.15s, background 0.15s;
color: #333;
}
#bm-app .bm-preset-btn:hover {
border-color: #e94560;
background: #fff0f3;
color: #e94560;
}
#bm-app .bm-alert {
padding: 0.65rem 1rem;
border-radius: 6px;
font-size: 0.85rem;
margin-top: 0.6rem;
display: none;
}
#bm-app .bm-alert.error { background: #fff0f0; border: 1px solid #ffbaba; color: #c00; }
#bm-app .bm-alert.success { background: #f0fff4; border: 1px solid #a0d9b0; color: #1a7a3a; }
#bm-app .bm-divider { border: none; border-top: 1px solid #dde3f0; margin: 1.5rem 0; }
#bm-app .bm-cta {
background: linear-gradient(135deg, #0f3460 0%, #16213e 100%);
color: #fff;
border-radius: 10px;
padding: 1.3rem 1.6rem;
margin: 1.5rem 0;
display: flex;
align-items: center;
gap: 1.2rem;
flex-wrap: wrap;
}
#bm-app .bm-cta-text { flex: 1; min-width: 200px; }
#bm-app .bm-cta-text strong { display: block; font-size: 1rem; margin-bottom: 0.3rem; }
#bm-app .bm-cta-text span { font-size: 0.85rem; opacity: 0.88; }
#bm-app .bm-cta-btn {
display: inline-block;
padding: 0.6rem 1.4rem;
background: #e94560;
color: #fff;
border-radius: 6px;
font-weight: 700;
font-size: 0.9rem;
text-decoration: none;
white-space: nowrap;
transition: opacity 0.15s;
}
#bm-app .bm-cta-btn:hover { opacity: 0.85; }
#bm-app .bm-crosslinks {
background: #f0f4ff;
border-radius: 8px;
padding: 1rem 1.2rem;
font-size: 0.88rem;
}
#bm-app .bm-crosslinks a {
color: #0f3460;
text-decoration: underline;
margin-right: 1rem;
}
#bm-app .bm-footer-af {
font-size: 0.75rem;
color: #999;
margin-top: 0.5rem;
text-align: right;
}
</style>

<div class="bm-section">
<h2>JavaScriptコード</h2>
<label for="bm-code">JavaScriptをここに貼り付けてください</label>
<textarea id="bm-code" placeholder="// 例：トップへスクロール&#10;window.scrollTo({top: 0, behavior: 'smooth'});"></textarea>
<div class="bm-options">
<label class="bm-check">
<input type="checkbox" id="bm-minify" checked>
圧縮（コメント・空白を除去）
</label>
<label class="bm-check">
<input type="checkbox" id="bm-encode" checked>
URIエンコード
</label>
<label class="bm-check">
<input type="checkbox" id="bm-wrap-iife" checked>
IIFEでラップ（void function(){...}()）
</label>
</div>
<div class="bm-btn-row">
<button class="bm-btn bm-btn-primary" id="bm-convert-btn">ブックマークレットに変換</button>
<button class="bm-btn bm-btn-ghost" id="bm-clear-btn">クリア</button>
<button class="bm-btn bm-btn-secondary" id="bm-test-btn">コンソールでテスト</button>
</div>
<div class="bm-alert" id="bm-alert"></div>
</div>

<div class="bm-section">
<h2>ブックマークレット出力</h2>
<div class="bm-output-wrap">
<textarea class="bm-output" id="bm-result" readonly placeholder="ブックマークレットのURLがここに表示されます..."></textarea>
<button class="bm-copy-btn" id="bm-copy-btn">コピー</button>
</div>
<div class="bm-stats">
<span>文字数: <strong id="bm-char-count">0</strong></span>
<span>サイズ: <strong id="bm-size">0 B</strong></span>
<span>状態: <strong id="bm-status">—</strong></span>
</div>
<div class="bm-drag-box" id="bm-drag-box" style="display:none;">
<div>このボタンをブックマークバーにドラッグしてください：</div>
<a class="bm-drag-link" id="bm-drag-link" href="#">ブックマークレット</a>
<div style="margin-top:0.5rem;font-size:0.8rem;color:#5a7aaf;">（ブックマークバーを表示: Ctrl+Shift+B / Cmd+Shift+B）</div>
</div>
</div>

<div class="bm-section">
<h2>すぐ使えるサンプル</h2>
<div class="bm-presets" id="bm-presets">
<button class="bm-preset-btn" data-preset="highlight-links">リンクを強調表示</button>
<button class="bm-preset-btn" data-preset="dark-mode">ダークモード切替</button>
<button class="bm-preset-btn" data-preset="font-size">文字サイズ変更</button>
<button class="bm-preset-btn" data-preset="print-page">ページを印刷</button>
<button class="bm-preset-btn" data-preset="scroll-top">トップへスクロール</button>
<button class="bm-preset-btn" data-preset="word-count">文字数カウント</button>
<button class="bm-preset-btn" data-preset="copy-url">URL＋タイトルをコピー</button>
</div>
</div>

<hr class="bm-divider">

<!-- freee CTA (AF: a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) -->
<div class="bm-cta">
<div class="bm-cta-text">
<strong>業務効率化なら freee会計</strong>
<span>請求書・経費精算・確定申告をまるごと自動化。ブックマークレットで毎日の作業を時短するように、バックオフィスも自動化しましょう。</span>
</div>
<a class="bm-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="nofollow noopener">無料で試してみる</a>
</div>

<div class="bm-crosslinks">
<strong>関連ツール：</strong>
<a href="/ja/tools/code-minifier/">コード圧縮ツール</a>
<a href="/ja/tools/url-encoder/">URLエンコードツール</a>
</div>
<div class="bm-footer-af">※ freeeへのリンクはアフィリエイトリンクです。</div>

<script>
(function () {
'use strict';

var PRESETS = {
'highlight-links': {
name: 'リンクを強調表示',
code: [
'// ページ上の全リンクにカラーアウトラインを付ける',
'var links = document.querySelectorAll("a");',
'var colors = ["#e94560","#0f3460","#f5a623","#2ecc71","#9b59b6"];',
'links.forEach(function(el, i) {',
'  el.style.outline = "3px solid " + colors[i % colors.length];',
'  el.style.outlineOffset = "2px";',
'});',
'alert(links.length + " 件のリンクを強調表示しました。");'
].join('\n')
},
'dark-mode': {
name: 'ダークモード切替',
code: [
'// どのサイトでもダークモードオーバーレイを切り替える',
'var id = "__bm_dark__";',
'var existing = document.getElementById(id);',
'if (existing) {',
'  existing.remove();',
'} else {',
'  var s = document.createElement("style");',
'  s.id = id;',
'  s.textContent = "html{filter:invert(1) hue-rotate(180deg)!important} img,video,canvas{filter:invert(1) hue-rotate(180deg)!important}";',
'  document.head.appendChild(s);',
'}'
].join('\n')
},
'font-size': {
name: '文字サイズ変更',
code: [
'// フォントサイズを 100% → 120% → 140% → 100% と切り替える',
'var sizes = ["100%","120%","140%"];',
'var cur = document.documentElement.style.fontSize || "100%";',
'var idx = sizes.indexOf(cur);',
'var next = sizes[(idx + 1) % sizes.length];',
'document.documentElement.style.fontSize = next;'
].join('\n')
},
'print-page': {
name: 'ページを印刷',
code: '// 現在のページを印刷する\nwindow.print();'
},
'scroll-top': {
name: 'トップへスクロール',
code: [
'// ページのトップへスムーズにスクロールする',
'window.scrollTo({ top: 0, behavior: "smooth" });'
].join('\n')
},
'word-count': {
name: '文字数カウント',
code: [
'// ページの表示テキストの単語数をカウントする',
'var text = document.body.innerText || document.body.textContent || "";',
'var words = text.trim().split(/\\s+/).filter(function(w){ return w.length > 0; });',
'alert("このページの単語数: " + words.length + " 語");'
].join('\n')
},
'copy-url': {
name: 'URL＋タイトルをコピー',
code: [
'// ページタイトルとURLをクリップボードにコピーする',
'var txt = document.title + "\\n" + location.href;',
'navigator.clipboard.writeText(txt).then(function(){',
'  alert("コピーしました！\\n" + txt);',
'}).catch(function(){',
'  prompt("コピーしてください:", txt);',
'});'
].join('\n')
}
};

function minifyJS(code) {
code = code.replace(/(?<![:'"])\/\/[^\n]*/g, '');
code = code.replace(/\/\*[\s\S]*?\*\//g, '');
code = code.replace(/\s+/g, ' ').trim();
code = code.replace(/\s*([{};,=+\-*\/<>!&|?:])\s*/g, '$1');
return code;
}

function buildBookmarklet(rawCode, doMinify, doEncode, doIife) {
var code = rawCode.trim();
if (!code) return null;
if (doMinify) { code = minifyJS(code); }
if (doIife) { code = 'void function(){' + code + '}()'; }
if (doEncode) { return 'javascript:' + encodeURIComponent(code); }
return 'javascript:' + code;
}

function byteSize(str) { return new Blob([str]).size; }

function formatBytes(n) {
if (n < 1024) return n + ' B';
return (n / 1024).toFixed(1) + ' KB';
}

function showAlert(msg, type) {
var el = document.getElementById('bm-alert');
el.textContent = msg;
el.className = 'bm-alert ' + type;
el.style.display = 'block';
setTimeout(function () { el.style.display = 'none'; }, 4000);
}

function updateStats(url) {
var chars = url ? url.length : 0;
var bytes = url ? byteSize(url) : 0;
document.getElementById('bm-char-count').textContent = chars.toLocaleString();
document.getElementById('bm-size').textContent = formatBytes(bytes);
}

function convert() {
var code = document.getElementById('bm-code').value;
if (!code.trim()) {
showAlert('JavaScriptコードを入力してください。', 'error');
return;
}
var doMinify = document.getElementById('bm-minify').checked;
var doEncode = document.getElementById('bm-encode').checked;
var doIife = document.getElementById('bm-wrap-iife').checked;
try {
var url = buildBookmarklet(code, doMinify, doEncode, doIife);
if (!url) { showAlert('変換に失敗しました。', 'error'); return; }
document.getElementById('bm-result').value = url;
updateStats(url);
document.getElementById('bm-status').textContent = '完成';
var dragBox = document.getElementById('bm-drag-box');
var dragLink = document.getElementById('bm-drag-link');
dragLink.href = url;
dragBox.style.display = 'block';
showAlert('変換完了！ブックマークバーにドラッグするか、コピーしてください。', 'success');
} catch (e) {
showAlert('エラー: ' + e.message, 'error');
}
}

function copyResult() {
var val = document.getElementById('bm-result').value;
if (!val) { showAlert('先に変換してください。', 'error'); return; }
navigator.clipboard.writeText(val).then(function () {
var btn = document.getElementById('bm-copy-btn');
btn.textContent = 'コピー済み！';
setTimeout(function () { btn.textContent = 'コピー'; }, 2000);
}).catch(function () {
document.getElementById('bm-result').select();
document.execCommand('copy');
});
}

function testBookmarklet() {
var code = document.getElementById('bm-code').value.trim();
if (!code) { showAlert('テストするJavaScriptを入力してください。', 'error'); return; }
try {
var fn = new Function(code);
fn();
} catch (e) {
showAlert('実行エラー: ' + e.message, 'error');
}
}

function loadPreset(key) {
var p = PRESETS[key];
if (!p) return;
document.getElementById('bm-code').value = p.code;
document.getElementById('bm-status').textContent = '—';
document.getElementById('bm-result').value = '';
document.getElementById('bm-drag-box').style.display = 'none';
updateStats('');
}

document.getElementById('bm-convert-btn').addEventListener('click', convert);
document.getElementById('bm-copy-btn').addEventListener('click', copyResult);
document.getElementById('bm-test-btn').addEventListener('click', testBookmarklet);
document.getElementById('bm-clear-btn').addEventListener('click', function () {
document.getElementById('bm-code').value = '';
document.getElementById('bm-result').value = '';
document.getElementById('bm-drag-box').style.display = 'none';
document.getElementById('bm-status').textContent = '—';
updateStats('');
});
document.getElementById('bm-presets').addEventListener('click', function (e) {
if (e.target.classList.contains('bm-preset-btn')) {
loadPreset(e.target.dataset.preset);
}
});
document.getElementById('bm-code').addEventListener('input', function () {
var url = document.getElementById('bm-result').value;
if (url) updateStats(url);
});

loadPreset('scroll-top');
}());
</script>
</div>

## ブックマークレットの使い方

1. 上のコード欄にJavaScriptを貼り付けます（またはサンプルを選択）。
2. **「変換」をクリック** — コードが `javascript:` URIに変換されます。
3. 生成されたボタンをブラウザのブックマークバーに**ドラッグ**します。
4. 任意のページを開いてブックマークをクリック — スクリプトが即座に実行されます。

## 活用のヒント

- **圧縮**でコメントと空白を削除し、URLを短くできます。
- **IIFEラップ**でページのグローバルスコープを汚染せずに済みます。
- **URIエンコード**はスペース・引用符・アンパサンドなど特殊文字に必須です。
- ブラウザのブックマークレットURL上限はおよそ2KB。スクリプトは簡潔に。
- テスト時は `alert()` や `console.log()` で出力を確認しましょう。

## 関連ツール

- [コード圧縮ツール](/ja/tools/code-minifier/) — JS・CSS・HTMLを圧縮します。
- [URLエンコードツール](/ja/tools/url-encoder/) — URLコンポーネントを手動でエンコード／デコードします。
