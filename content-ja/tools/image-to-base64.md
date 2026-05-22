---
title: "画像→Base64変換ツール — データURIコンバーター"
date: 2025-08-11
description: "画像をBase64データURIに即座に変換。PNG・JPG・GIF・SVG・WebPをドラッグ＆ドロップ。Base64文字列・データURI・CSS背景・HTMLタグとしてコピー。"
categories: ["無料ツール"]
tags: ["開発ツール", "コード変換", "無料ツール"]
slug: "image-to-base64"
ShowToc: false
cover:
  image: "/images/covers/image-to-base64-ja.png"
  alt: "画像→Base64変換ツール"
---

画像をBase64データURIにブラウザ上で即座に変換。アップロード不要・サーバー送信なし・完全プライベート。

<div id="i2b-app">
<style>
#i2b-app *,
#i2b-app *::before,
#i2b-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#i2b-app {
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
color: #1a1a2e;
max-width: 820px;
margin: 0 auto;
padding: 0 0 40px;
}
#i2b-drop-zone {
border: 2.5px dashed #7c3aed;
border-radius: 14px;
padding: 48px 24px;
text-align: center;
cursor: pointer;
background: #f5f3ff;
transition: background 0.2s, border-color 0.2s;
position: relative;
}
#i2b-drop-zone.i2b-dragover {
background: #ede9fe;
border-color: #5b21b6;
}
#i2b-drop-zone-icon {
font-size: 48px;
line-height: 1;
margin-bottom: 12px;
}
#i2b-drop-zone p {
color: #6d28d9;
font-size: 1.05rem;
font-weight: 500;
}
#i2b-drop-zone small {
display: block;
margin-top: 6px;
color: #8b5cf6;
font-size: 0.82rem;
}
#i2b-file-input {
position: absolute;
inset: 0;
opacity: 0;
cursor: pointer;
width: 100%;
height: 100%;
}
#i2b-warning {
display: none;
margin-top: 14px;
padding: 10px 16px;
background: #fef3c7;
border: 1px solid #f59e0b;
border-radius: 8px;
color: #92400e;
font-size: 0.88rem;
font-weight: 500;
}
#i2b-results {
display: none;
margin-top: 28px;
}
#i2b-preview-row {
display: flex;
align-items: flex-start;
gap: 24px;
margin-bottom: 22px;
flex-wrap: wrap;
}
#i2b-preview-img {
max-width: 200px;
max-height: 200px;
border-radius: 10px;
border: 1px solid #e5e7eb;
object-fit: contain;
background: repeating-conic-gradient(#e5e7eb 0% 25%, #fff 0% 50%) 0 0 / 16px 16px;
flex-shrink: 0;
}
#i2b-meta {
flex: 1;
min-width: 180px;
}
#i2b-meta h3 {
font-size: 1rem;
font-weight: 700;
color: #1a1a2e;
margin-bottom: 10px;
word-break: break-all;
}
.i2b-meta-row {
display: flex;
justify-content: space-between;
padding: 5px 0;
border-bottom: 1px solid #f3f4f6;
font-size: 0.875rem;
color: #374151;
}
.i2b-meta-row:last-child { border-bottom: none; }
.i2b-meta-label { color: #6b7280; font-weight: 500; }
.i2b-meta-value { font-weight: 600; color: #1a1a2e; }
.i2b-size-bigger { color: #dc2626; }
#i2b-outputs { display: flex; flex-direction: column; gap: 16px; }
.i2b-output-block {
background: #f9fafb;
border: 1px solid #e5e7eb;
border-radius: 10px;
overflow: hidden;
}
.i2b-output-header {
display: flex;
justify-content: space-between;
align-items: center;
padding: 10px 16px;
background: #f3f4f6;
border-bottom: 1px solid #e5e7eb;
}
.i2b-output-label {
font-size: 0.8rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.04em;
color: #6b7280;
}
.i2b-copy-btn {
display: inline-flex;
align-items: center;
gap: 5px;
padding: 4px 14px;
background: #7c3aed;
color: #fff;
border: none;
border-radius: 6px;
font-size: 0.8rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
white-space: nowrap;
font-family: inherit;
}
.i2b-copy-btn:hover { background: #6d28d9; }
.i2b-copy-btn.i2b-copied { background: #16a34a; }
.i2b-output-textarea {
width: 100%;
min-height: 80px;
max-height: 160px;
padding: 12px 16px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.78rem;
line-height: 1.5;
color: #374151;
background: transparent;
border: none;
resize: vertical;
outline: none;
word-break: break-all;
overflow-y: auto;
}
#i2b-reset-btn {
margin-top: 20px;
padding: 10px 24px;
background: transparent;
border: 2px solid #7c3aed;
color: #7c3aed;
border-radius: 8px;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, color 0.15s;
font-family: inherit;
}
#i2b-reset-btn:hover { background: #7c3aed; color: #fff; }
#i2b-freee-cta {
margin-top: 36px;
padding: 20px 24px;
background: linear-gradient(135deg, #e0f2fe 0%, #f0fdf4 100%);
border: 1px solid #bae6fd;
border-radius: 12px;
display: flex;
align-items: center;
gap: 16px;
flex-wrap: wrap;
}
#i2b-freee-cta-text { flex: 1; min-width: 200px; }
#i2b-freee-cta-text strong {
display: block;
font-size: 0.95rem;
color: #0c4a6e;
margin-bottom: 4px;
}
#i2b-freee-cta-text span {
font-size: 0.83rem;
color: #0369a1;
line-height: 1.5;
}
#i2b-freee-cta-btn {
display: inline-block;
padding: 9px 20px;
background: #0ea5e9;
color: #fff;
border-radius: 8px;
font-size: 0.875rem;
font-weight: 700;
text-decoration: none;
white-space: nowrap;
transition: background 0.15s;
}
#i2b-freee-cta-btn:hover { background: #0284c7; }
@media (max-width: 540px) {
#i2b-preview-row { flex-direction: column; }
#i2b-preview-img { max-width: 100%; }
.i2b-output-header { flex-direction: column; align-items: flex-start; gap: 8px; }
#i2b-freee-cta { flex-direction: column; }
}
</style>

<div id="i2b-drop-zone">
<input type="file" id="i2b-file-input" accept="image/png,image/jpeg,image/gif,image/svg+xml,image/webp">
<div id="i2b-drop-zone-icon">🖼</div>
<p>ここに画像をドラッグ＆ドロップ、またはクリックしてファイルを選択</p>
<small>対応形式：PNG・JPG・GIF・SVG・WebP &nbsp;·&nbsp; 推奨上限：2 MB</small>
</div>
<div id="i2b-warning"></div>

<div id="i2b-results">
<div id="i2b-preview-row">
<img id="i2b-preview-img" src="" alt="プレビュー">
<div id="i2b-meta">
<h3 id="i2b-filename"></h3>
<div class="i2b-meta-row"><span class="i2b-meta-label">MIMEタイプ</span><span class="i2b-meta-value" id="i2b-mime"></span></div>
<div class="i2b-meta-row"><span class="i2b-meta-label">元のサイズ</span><span class="i2b-meta-value" id="i2b-orig-size"></span></div>
<div class="i2b-meta-row"><span class="i2b-meta-label">Base64サイズ</span><span class="i2b-meta-value" id="i2b-b64-size"></span></div>
<div class="i2b-meta-row"><span class="i2b-meta-label">サイズ増加率</span><span class="i2b-meta-value i2b-size-bigger" id="i2b-size-ratio"></span></div>
</div>
</div>

<div id="i2b-outputs">
<div class="i2b-output-block">
<div class="i2b-output-header">
<span class="i2b-output-label">Base64文字列（プレフィックスなし）</span>
<button class="i2b-copy-btn" data-target="i2b-out-b64">コピー</button>
</div>
<textarea id="i2b-out-b64" class="i2b-output-textarea" readonly spellcheck="false"></textarea>
</div>

<div class="i2b-output-block">
<div class="i2b-output-header">
<span class="i2b-output-label">データURI</span>
<button class="i2b-copy-btn" data-target="i2b-out-uri">コピー</button>
</div>
<textarea id="i2b-out-uri" class="i2b-output-textarea" readonly spellcheck="false"></textarea>
</div>

<div class="i2b-output-block">
<div class="i2b-output-header">
<span class="i2b-output-label">CSS background-image</span>
<button class="i2b-copy-btn" data-target="i2b-out-css">コピー</button>
</div>
<textarea id="i2b-out-css" class="i2b-output-textarea" readonly spellcheck="false"></textarea>
</div>

<div class="i2b-output-block">
<div class="i2b-output-header">
<span class="i2b-output-label">HTML &lt;img&gt; タグ</span>
<button class="i2b-copy-btn" data-target="i2b-out-html">コピー</button>
</div>
<textarea id="i2b-out-html" class="i2b-output-textarea" readonly spellcheck="false"></textarea>
</div>
</div>

<button id="i2b-reset-btn">別の画像を変換する</button>
</div>

<script>
(function () {
var MAX_WARN_BYTES = 2 * 1024 * 1024; // 2 MB

var dropZone  = document.getElementById('i2b-drop-zone');
var fileInput = document.getElementById('i2b-file-input');
var warning   = document.getElementById('i2b-warning');
var results   = document.getElementById('i2b-results');
var resetBtn  = document.getElementById('i2b-reset-btn');

function fmtBytes(n) {
if (n < 1024) return n + ' B';
if (n < 1024 * 1024) return (n / 1024).toFixed(1) + ' KB';
return (n / (1024 * 1024)).toFixed(2) + ' MB';
}

function processFile(file) {
warning.style.display = 'none';
warning.textContent   = '';

var allowed = ['image/png','image/jpeg','image/gif','image/svg+xml','image/webp'];
if (!allowed.includes(file.type)) {
warning.textContent   = '対応していないファイル形式です：' + (file.type || '不明') + '。PNG・JPG・GIF・SVG・WebP を使用してください。';
warning.style.display = 'block';
return;
}

if (file.size > MAX_WARN_BYTES) {
warning.textContent   = '警告：ファイルサイズが ' + fmtBytes(file.size) + ' あります。Base64エンコード後は約 ' + fmtBytes(Math.ceil(file.size * 4 / 3)) + ' になります。大きなデータURIはブラウザのパフォーマンスに影響する場合があります。';
warning.style.display = 'block';
}

var reader = new FileReader();
reader.onload = function (e) {
var dataUri = e.target.result;
var b64     = dataUri.split(',')[1];
var mime    = file.type;

document.getElementById('i2b-preview-img').src = dataUri;
document.getElementById('i2b-filename').textContent  = file.name;
document.getElementById('i2b-mime').textContent      = mime;
document.getElementById('i2b-orig-size').textContent = fmtBytes(file.size);
document.getElementById('i2b-b64-size').textContent  = fmtBytes(b64.length);

var ratio = ((b64.length / file.size - 1) * 100).toFixed(1);
document.getElementById('i2b-size-ratio').textContent = '+' + ratio + '%';

document.getElementById('i2b-out-b64').value  = b64;
document.getElementById('i2b-out-uri').value  = dataUri;
document.getElementById('i2b-out-css').value  = 'background-image: url("' + dataUri + '");';
document.getElementById('i2b-out-html').value = '<img src="' + dataUri + '" alt="' + file.name.replace(/"/g, '&quot;') + '">';

dropZone.style.display = 'none';
results.style.display  = 'block';
};
reader.readAsDataURL(file);
}

// ドラッグ＆ドロップ
dropZone.addEventListener('dragover', function (e) {
e.preventDefault();
dropZone.classList.add('i2b-dragover');
});
dropZone.addEventListener('dragleave', function () {
dropZone.classList.remove('i2b-dragover');
});
dropZone.addEventListener('drop', function (e) {
e.preventDefault();
dropZone.classList.remove('i2b-dragover');
var file = e.dataTransfer.files[0];
if (file) processFile(file);
});

// ファイル選択
fileInput.addEventListener('change', function () {
if (fileInput.files[0]) processFile(fileInput.files[0]);
});

// コピーボタン
document.getElementById('i2b-outputs').addEventListener('click', function (e) {
var btn = e.target.closest('.i2b-copy-btn');
if (!btn) return;
var targetId = btn.getAttribute('data-target');
var textarea = document.getElementById(targetId);
if (!textarea) return;
navigator.clipboard.writeText(textarea.value).then(function () {
var orig = btn.textContent;
btn.textContent = 'コピーしました!';
btn.classList.add('i2b-copied');
setTimeout(function () {
btn.textContent = 'コピー';
btn.classList.remove('i2b-copied');
}, 2000);
}).catch(function () {
textarea.select();
document.execCommand('copy');
});
});

// リセット
resetBtn.addEventListener('click', function () {
fileInput.value        = '';
results.style.display  = 'none';
dropZone.style.display = '';
warning.style.display  = 'none';
warning.textContent    = '';
document.getElementById('i2b-preview-img').src = '';
['i2b-out-b64','i2b-out-uri','i2b-out-css','i2b-out-html'].forEach(function (id) {
document.getElementById(id).value = '';
});
});
})();
</script>
</div>

---

## 使い方

1. 上のエリアに画像をドラッグ＆ドロップするか、クリックしてファイルを選択します。
2. ツールはブラウザの **FileReader API** でファイルをローカル処理します。画像はどのサーバーにも送信されません。
3. 必要な形式の **コピー** ボタンをクリックして出力をコピーします。

## 出力形式の説明

| 形式 | 用途 |
|---|---|
| **Base64文字列** | API・データベース・JSONペイロード |
| **データURI** | `src` 属性の値としてそのまま使用 |
| **CSS background-image** | スタイルシートにそのまま貼り付け |
| **HTML `<img>` タグ** | HTMLにそのまま貼り付け |

## Base64エンコードが役立つ場面

画像をBase64データURIとして埋め込むと、外部リクエストなしで完結するHTMLファイルやメールテンプレートを作成できます。CSSの小さなアイコン、APIペイロード、オフライン対応Webアプリにも便利です。ただし、サイズが約 **33%増加** し、初期解析がやや遅くなるため、埋め込む画像は小さめ（目安：50 KB以下）に留めることをおすすめします。

## プライバシー

すべての変換処理は **ブラウザ内** で完結します。画像ファイルがデバイスの外に出ることは一切ありません。

---

**関連ツール：** [Base64エンコーダー / デコーダー](/ja/tools/base64-encoder/) · [画像リサイザー](/ja/tools/image-resizer/) · [プレースホルダー画像ジェネレーター](/ja/tools/placeholder-image/)

---

<div id="i2b-freee-cta">
<div id="i2b-freee-cta-text">
<strong>freee で経理・請求書をもっとスムーズに</strong>
<span>中小企業・フリーランス向けのクラウド会計ソフト。無料トライアルから始められます。</span>
</div>
<a id="i2b-freee-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener noreferrer">freee を試してみる</a>
</div>
