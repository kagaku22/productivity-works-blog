---
title: "Base64エンコーダー & デコーダー - 無料オンライン変換ツール"
date: 2025-05-16
description: "Base64文字列を即座にエンコード・デコード。テキスト・URL・ファイル対応。開発者向け無料オンラインBase64変換ツール。"
categories: ["無料ツール"]
tags: ["Base64", "エンコーダー", "デコーダー", "開発ツール", "エンコード"]
slug: "base64-encoder"
aliases: ["/ja/tools/base64-encoder/", "/ja/tools/base64-encoder/"]
cover:
  image: "/images/covers/base64-encoder-ja.png"
  alt: "Base64エンコーダー"
ShowToc: false
---

<div id="base64-app">

<style>
#base64-app {
  font-family: 'Segoe UI', 'Hiragino Sans', 'Yu Gothic UI', sans-serif;
  max-width: 820px;
  margin: 0 auto;
  padding: 16px;
  color: #e2e8f0;
}

#base64-app * {
  box-sizing: border-box;
}

.b64-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
}

.b64-label {
  font-size: 13px;
  font-weight: 600;
  color: #94a3b8;
  margin-bottom: 6px;
  letter-spacing: 0.04em;
}

.b64-textarea {
  width: 100%;
  min-height: 140px;
  background: #0f172a;
  border: 1.5px solid #334155;
  border-radius: 8px;
  padding: 12px;
  color: #e2e8f0;
  font-size: 14px;
  font-family: 'Courier New', 'Consolas', monospace;
  resize: vertical;
  outline: none;
  transition: border-color 0.2s;
  line-height: 1.6;
}

.b64-textarea:focus {
  border-color: #06b6d4;
}

.b64-textarea.error {
  border-color: #f87171;
}

.b64-char-count {
  font-size: 12px;
  color: #64748b;
  text-align: right;
  margin-top: 4px;
  min-height: 18px;
}

.b64-error-msg {
  font-size: 12px;
  color: #f87171;
  margin-top: 4px;
  min-height: 18px;
}

.b64-options-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  margin-bottom: 14px;
  padding: 12px 16px;
  background: #0f172a;
  border-radius: 8px;
  border: 1px solid #334155;
}

.b64-toggle-label {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-size: 13px;
  color: #94a3b8;
  user-select: none;
}

.b64-toggle-label input[type="checkbox"] {
  appearance: none;
  width: 36px;
  height: 20px;
  background: #334155;
  border-radius: 10px;
  position: relative;
  cursor: pointer;
  transition: background 0.2s;
  flex-shrink: 0;
}

.b64-toggle-label input[type="checkbox"]:checked {
  background: #06b6d4;
}

.b64-toggle-label input[type="checkbox"]::after {
  content: '';
  position: absolute;
  width: 14px;
  height: 14px;
  background: #fff;
  border-radius: 50%;
  top: 3px;
  left: 3px;
  transition: left 0.2s;
}

.b64-toggle-label input[type="checkbox"]:checked::after {
  left: 19px;
}

.b64-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 14px;
}

.b64-btn {
  padding: 9px 18px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.15s;
  display: inline-flex;
  align-items: center;
  gap: 6px;
}

.b64-btn:active {
  transform: scale(0.97);
}

.b64-btn-primary {
  background: #06b6d4;
  color: #0f172a;
}

.b64-btn-primary:hover {
  background: #22d3ee;
}

.b64-btn-secondary {
  background: #334155;
  color: #e2e8f0;
}

.b64-btn-secondary:hover {
  background: #475569;
}

.b64-btn-danger {
  background: #1e293b;
  color: #94a3b8;
  border: 1px solid #334155;
}

.b64-btn-danger:hover {
  background: #334155;
  color: #f87171;
}

.b64-btn-success {
  background: #059669;
  color: #fff;
}

.b64-swap-row {
  display: flex;
  justify-content: center;
  margin: 8px 0;
}

.b64-swap-btn {
  background: #1e293b;
  border: 1.5px solid #334155;
  color: #06b6d4;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 18px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.15s;
}

.b64-swap-btn:hover {
  background: #334155;
  transform: rotate(180deg);
}

.b64-copy-row {
  display: flex;
  justify-content: flex-end;
  gap: 8px;
  margin-top: 8px;
}

.b64-dropzone {
  border: 2px dashed #334155;
  border-radius: 10px;
  padding: 24px;
  text-align: center;
  color: #64748b;
  font-size: 13px;
  cursor: pointer;
  transition: all 0.2s;
  background: #0f172a;
  margin-top: 12px;
}

.b64-dropzone.dragover {
  border-color: #06b6d4;
  background: #0c1a2e;
  color: #06b6d4;
}

.b64-dropzone input[type="file"] {
  display: none;
}

.b64-dropzone-icon {
  font-size: 28px;
  margin-bottom: 6px;
}

.b64-section-title {
  font-size: 14px;
  font-weight: 700;
  color: #06b6d4;
  margin-bottom: 10px;
  padding-bottom: 6px;
  border-bottom: 1px solid #334155;
}

.b64-file-info {
  font-size: 12px;
  color: #22d3ee;
  margin-top: 8px;
  text-align: center;
}

.b64-uri-toggle {
  margin-top: 10px;
}

.b64-auto-badge {
  font-size: 11px;
  background: #06b6d4;
  color: #0f172a;
  padding: 2px 7px;
  border-radius: 4px;
  font-weight: 700;
  margin-left: 6px;
}

@media (max-width: 600px) {
  .b64-btn {
    padding: 8px 12px;
    font-size: 13px;
  }

  .b64-options-row {
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
  }
}
</style>

<!-- オプション行 -->
<div class="b64-card">
  <div class="b64-section-title">変換オプション</div>
  <div class="b64-options-row">
    <label class="b64-toggle-label">
      <input type="checkbox" id="b64-url-safe">
      URLセーフ Base64
    </label>
    <label class="b64-toggle-label">
      <input type="checkbox" id="b64-auto-detect" checked>
      自動検出モード
      <span class="b64-auto-badge">AUTO</span>
    </label>
    <label class="b64-toggle-label">
      <input type="checkbox" id="b64-data-uri">
      データURI出力
    </label>
  </div>
</div>

<!-- 入力エリア -->
<div class="b64-card">
  <div class="b64-section-title">入力</div>
  <div class="b64-label" id="b64-input-label">テキストまたは Base64 文字列を入力</div>
  <textarea class="b64-textarea" id="b64-input" placeholder="ここにテキストまたは Base64 文字列を入力してください..."></textarea>
  <div class="b64-char-count" id="b64-input-count">0 文字</div>

  <!-- ボタン行 -->
  <div class="b64-btn-row">
    <button class="b64-btn b64-btn-primary" id="b64-encode-btn">エンコード</button>
    <button class="b64-btn b64-btn-secondary" id="b64-decode-btn">デコード</button>
    <button class="b64-btn b64-btn-danger" id="b64-clear-btn">クリア</button>
  </div>
</div>

<!-- スワップ -->
<div class="b64-swap-row">
  <button class="b64-swap-btn" id="b64-swap-btn" title="入力と出力を入れ替え">&#8645;</button>
</div>

<!-- 出力エリア -->
<div class="b64-card">
  <div class="b64-section-title">出力</div>
  <div class="b64-label">変換結果</div>
  <textarea class="b64-textarea" id="b64-output" placeholder="変換結果がここに表示されます..." readonly></textarea>
  <div class="b64-char-count" id="b64-output-count">0 文字</div>
  <div class="b64-error-msg" id="b64-error"></div>
  <div class="b64-copy-row">
    <button class="b64-btn b64-btn-secondary" id="b64-copy-btn">コピー</button>
  </div>
</div>

<!-- ファイル→Base64 -->
<div class="b64-card">
  <div class="b64-section-title">ファイル → Base64 変換</div>
  <label class="b64-dropzone" id="b64-dropzone">
    <input type="file" id="b64-file-input">
    <div class="b64-dropzone-icon">&#128190;</div>
    <div>ファイルをドラッグ&ドロップ、またはクリックして選択</div>
    <div style="font-size:11px;margin-top:4px;color:#475569;">テキスト・画像・その他あらゆるファイルに対応</div>
  </label>
  <div class="b64-file-info" id="b64-file-info"></div>
</div>

<script>
(function () {
  'use strict';

  const inputEl   = document.getElementById('b64-input');
  const outputEl  = document.getElementById('b64-output');
  const inputCnt  = document.getElementById('b64-input-count');
  const outputCnt = document.getElementById('b64-output-count');
  const errorEl   = document.getElementById('b64-error');
  const encodeBtn = document.getElementById('b64-encode-btn');
  const decodeBtn = document.getElementById('b64-decode-btn');
  const clearBtn  = document.getElementById('b64-clear-btn');
  const swapBtn   = document.getElementById('b64-swap-btn');
  const copyBtn   = document.getElementById('b64-copy-btn');
  const urlSafe   = document.getElementById('b64-url-safe');
  const autoDetect= document.getElementById('b64-auto-detect');
  const dataUri   = document.getElementById('b64-data-uri');
  const fileInput = document.getElementById('b64-file-input');
  const dropzone  = document.getElementById('b64-dropzone');
  const fileInfo  = document.getElementById('b64-file-info');

  function countChars(str) {
    return [...str].length;
  }

  function updateCounts() {
    const ic = countChars(inputEl.value);
    const oc = countChars(outputEl.value);
    inputCnt.textContent  = ic.toLocaleString('ja-JP') + ' 文字';
    outputCnt.textContent = oc.toLocaleString('ja-JP') + ' 文字';
  }

  function clearError() {
    errorEl.textContent = '';
    outputEl.classList.remove('error');
  }

  function showError(msg) {
    errorEl.textContent = msg;
    outputEl.classList.add('error');
  }

  function toBase64(str) {
    try {
      const encoded = btoa(unescape(encodeURIComponent(str)));
      if (urlSafe.checked) {
        return encoded.replace(/\+/g, '-').replace(/\//g, '_').replace(/=+$/, '');
      }
      return encoded;
    } catch (e) {
      throw new Error('エンコードに失敗しました: ' + e.message);
    }
  }

  function fromBase64(str) {
    try {
      let s = str.trim();
      if (urlSafe.checked || /[-_]/.test(s)) {
        s = s.replace(/-/g, '+').replace(/_/g, '/');
        while (s.length % 4 !== 0) s += '=';
      }
      return decodeURIComponent(escape(atob(s)));
    } catch (e) {
      throw new Error('デコードに失敗しました。正しい Base64 文字列を入力してください。');
    }
  }

  function isLikelyBase64(str) {
    const s = str.trim().replace(/\s/g, '');
    if (s.length < 4) return false;
    const b64Regex = /^[A-Za-z0-9+/\-_]+=*$/;
    return b64Regex.test(s) && s.length % 4 === 0 || /^[A-Za-z0-9\-_]+$/.test(s);
  }

  function encode() {
    clearError();
    const input = inputEl.value;
    if (!input) {
      outputEl.value = '';
      updateCounts();
      return;
    }
    try {
      let result = toBase64(input);
      if (dataUri.checked) {
        result = 'data:text/plain;base64,' + result;
      }
      outputEl.value = result;
    } catch (e) {
      showError(e.message);
      outputEl.value = '';
    }
    updateCounts();
  }

  function decode() {
    clearError();
    const input = inputEl.value.trim();
    if (!input) {
      outputEl.value = '';
      updateCounts();
      return;
    }
    try {
      let src = input;
      if (/^data:[^;]+;base64,/i.test(src)) {
        src = src.replace(/^data:[^;]+;base64,/i, '');
      }
      const result = fromBase64(src);
      outputEl.value = result;
    } catch (e) {
      showError(e.message);
      outputEl.value = '';
    }
    updateCounts();
  }

  encodeBtn.addEventListener('click', encode);
  decodeBtn.addEventListener('click', decode);

  clearBtn.addEventListener('click', function () {
    inputEl.value  = '';
    outputEl.value = '';
    fileInfo.textContent = '';
    clearError();
    updateCounts();
  });

  swapBtn.addEventListener('click', function () {
    const tmp = inputEl.value;
    inputEl.value  = outputEl.value;
    outputEl.value = tmp;
    clearError();
    updateCounts();
  });

  copyBtn.addEventListener('click', function () {
    if (!outputEl.value) return;
    navigator.clipboard.writeText(outputEl.value).then(function () {
      const orig = copyBtn.textContent;
      copyBtn.textContent = 'コピーしました!';
      copyBtn.classList.add('b64-btn-success');
      copyBtn.classList.remove('b64-btn-secondary');
      setTimeout(function () {
        copyBtn.textContent = orig;
        copyBtn.classList.remove('b64-btn-success');
        copyBtn.classList.add('b64-btn-secondary');
      }, 1800);
    }).catch(function () {
      outputEl.select();
      document.execCommand('copy');
    });
  });

  inputEl.addEventListener('input', function () {
    updateCounts();
    if (autoDetect.checked && inputEl.value.trim()) {
      const val = inputEl.value.trim();
      const dataUriPattern = /^data:[^;]+;base64,/i;
      if (dataUriPattern.test(val) || isLikelyBase64(val)) {
        decode();
      } else {
        encode();
      }
    }
  });

  // ファイル読み込み共通処理
  function handleFile(file) {
    if (!file) return;
    const maxSize = 5 * 1024 * 1024; // 5MB
    if (file.size > maxSize) {
      fileInfo.textContent = 'エラー: ファイルサイズは 5MB 以下にしてください。';
      fileInfo.style.color = '#f87171';
      return;
    }
    const reader = new FileReader();
    reader.onload = function (e) {
      let b64 = e.target.result.split(',')[1];
      if (urlSafe.checked) {
        b64 = b64.replace(/\+/g, '-').replace(/\//g, '_').replace(/=+$/, '');
      }
      let result = b64;
      if (dataUri.checked) {
        result = e.target.result;
      }
      outputEl.value = result;
      inputEl.value  = '';
      fileInfo.textContent = 'ファイル: ' + file.name + ' (' + (file.size / 1024).toFixed(1) + ' KB) を変換しました。';
      fileInfo.style.color = '#22d3ee';
      clearError();
      updateCounts();
    };
    reader.readAsDataURL(file);
  }

  fileInput.addEventListener('change', function () {
    handleFile(fileInput.files[0]);
  });

  dropzone.addEventListener('dragover', function (e) {
    e.preventDefault();
    dropzone.classList.add('dragover');
  });

  dropzone.addEventListener('dragleave', function () {
    dropzone.classList.remove('dragover');
  });

  dropzone.addEventListener('drop', function (e) {
    e.preventDefault();
    dropzone.classList.remove('dragover');
    const file = e.dataTransfer.files[0];
    handleFile(file);
  });

  updateCounts();
})();
</script>

</div>

---

## Base64エンコードとは

Base64は、バイナリデータを印字可能なASCII文字列に変換するエンコード方式です。英数字と一部の記号（`+`、`/`、`=`）の64種類の文字のみを使用するため、メール本文・HTMLのデータURI・JSONペイロードなど、テキストしか扱えない場面でも安全にバイナリを埋め込めます。3バイトのデータを4文字に変換するため、データ量は約33%増加しますが、あらゆる環境で文字化けなく転送できる信頼性が最大のメリットです。

URLセーフBase64は標準版の `+` と `/` をそれぞれ `-` と `_` に置き換えたバリアントで、JWTトークンやクエリパラメータなど、URLに直接埋め込む用途で広く使われています。パディング文字 `=` も省略される場合が多く、本ツールの「URLセーフ」モードではこの形式に対応しています。

## よくある使用例

- **JWT（JSON Web Token）**: ヘッダーとペイロードをBase64URLエンコードして署名と連結し、認証情報を安全に伝送する
- **画像・フォントの埋め込み**: CSSやHTMLに `data:image/png;base64,...` 形式で画像を直接埋め込み、HTTP リクエスト数を削減する
- **メール添付ファイル**: MIME形式のメールでバイナリの添付ファイルをBase64に変換して本文に含める
- **APIのバイナリ転送**: REST APIのJSONボディにファイルやバイナリデータを含める際、Base64文字列として送信する
- **設定ファイル・シークレット管理**: KubernetesのSecretリソースなど、設定ファイル内にパスワードや証明書をBase64で格納する

## 関連ツール

> JSONデータを即座に整形・検証 → [JSONフォーマッター](/ja/tools/json-formatter/)

> 安全なパスワードを即座に生成 → [パスワード生成ツール](/ja/tools/password-generator/)

> 文字数・単語数をリアルタイムでカウント → [文字数カウンター](/ja/tools/moji-counter/)

---

**エンジニアの確定申告をもっと簡単に**

コーディングは得意でも、経理は苦手…。クラウド会計ソフト「freee」なら、銀行口座と自動連携して経費を自動分類。確定申告書の作成もガイドに沿うだけ。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">

## 関連記事

- [ChatGPT API初心者向け完全ガイド【2026年版・サンプルコード付き】](/ja/posts/chatgpt-api-使い方-初心者/)
