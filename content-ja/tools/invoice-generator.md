---
title: "無料請求書作成ツール｜インボイス対応・即時PDF出力【2025年版】"
date: 2025-05-16
draft: false
slug: "invoice-generator"
aliases:
  - "/ja/tools/invoice-maker/"
  - "/ja/tools/free-invoice/"
description: "無料で使えるオンライン請求書作成ツール。適格請求書（インボイス）制度対応。登録番号・税率区分（10%/8%）・消費税額を自動計算。明細入力・PDF保存まで会員登録不要。"
categories:
  - "無料ツール"
tags:
  - "請求書作成"
  - "インボイス"
  - "適格請求書"
  - "フリーランス"
  - "無料ツール"
  - "消費税計算"
author: "Productivity Works編集部"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: /images/covers/invoice-generator-ja.png
  alt: "無料請求書作成ツール｜インボイス対応・即時PDF出力"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 無料請求書作成ツール【インボイス対応】

送信元・送信先・明細を入力するだけで**プロ品質の請求書**を即作成。適格請求書（インボイス）制度に対応した**登録番号欄・税率区分（10%/8%）・消費税額の自動計算**を搭載。会員登録不要・完全無料。

<style>
#inv-app * { box-sizing: border-box; margin: 0; padding: 0; }
#inv-app {
  max-width: 860px;
  margin: 0 auto;
  font-family: 'Noto Sans JP', 'Hiragino Kaku Gothic ProN', 'Yu Gothic', sans-serif;
  color: #1e293b;
  font-size: 15px;
  line-height: 1.6;
}
#inv-app h2 {
  font-size: 17px;
  font-weight: 700;
  color: #1e40af;
  margin-bottom: 14px;
  padding-bottom: 6px;
  border-bottom: 2px solid #dbeafe;
}
#inv-app .inv-section {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 22px;
  margin-bottom: 20px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#inv-app .inv-grid-2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
#inv-app .inv-field {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
#inv-app label {
  font-size: 12px;
  font-weight: 700;
  color: #64748b;
  letter-spacing: 0.02em;
}
#inv-app input[type="text"],
#inv-app input[type="email"],
#inv-app input[type="number"],
#inv-app input[type="date"],
#inv-app select,
#inv-app textarea {
  border: 1px solid #cbd5e1;
  border-radius: 6px;
  padding: 8px 10px;
  font-size: 14px;
  color: #1e293b;
  background: #f8fafc;
  transition: border-color 0.15s;
  width: 100%;
  font-family: inherit;
}
#inv-app input:focus,
#inv-app select:focus,
#inv-app textarea:focus {
  outline: none;
  border-color: #1e40af;
  background: #fff;
}
#inv-app textarea { resize: vertical; min-height: 72px; }
#inv-app .inv-meta-row {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 14px;
}
#inv-app .invoice-badge {
  display: inline-block;
  background: #dbeafe;
  color: #1e40af;
  font-size: 11px;
  font-weight: 700;
  border-radius: 4px;
  padding: 2px 8px;
  margin-left: 8px;
  vertical-align: middle;
}
/* Tax rate section */
#inv-app .tax-rate-group {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 8px;
}
#inv-app .tax-rate-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  background: #f1f5f9;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  padding: 8px 14px;
  cursor: pointer;
  font-size: 14px;
  font-weight: 600;
  color: #475569;
  transition: all 0.15s;
  font-family: inherit;
}
#inv-app .tax-rate-btn.active {
  background: #eff6ff;
  border-color: #1e40af;
  color: #1e40af;
}
#inv-app .tax-rate-btn input[type="radio"] { accent-color: #1e40af; }
/* Line items */
#inv-app .line-items-header {
  display: grid;
  grid-template-columns: 3fr 1fr 1.3fr 1fr 1.3fr 36px;
  gap: 8px;
  padding: 0 0 6px;
  border-bottom: 1px solid #e2e8f0;
  margin-bottom: 8px;
}
#inv-app .line-items-header span {
  font-size: 11px;
  font-weight: 700;
  color: #64748b;
  letter-spacing: 0.02em;
}
#inv-app .line-item-row {
  display: grid;
  grid-template-columns: 3fr 1fr 1.3fr 1fr 1.3fr 36px;
  gap: 8px;
  margin-bottom: 8px;
  align-items: center;
}
#inv-app .line-item-row input,
#inv-app .line-item-row select { margin: 0; }
#inv-app .line-item-total {
  font-size: 14px;
  font-weight: 600;
  color: #1e40af;
  padding: 8px 10px;
  background: #eff6ff;
  border-radius: 6px;
  text-align: right;
}
#inv-app .btn-remove {
  background: none;
  border: 1px solid #fca5a5;
  border-radius: 6px;
  color: #dc2626;
  cursor: pointer;
  font-size: 16px;
  width: 34px;
  height: 34px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.15s;
}
#inv-app .btn-remove:hover { background: #fee2e2; }
#inv-app .btn-add {
  background: #eff6ff;
  border: 1px dashed #93c5fd;
  border-radius: 7px;
  color: #1e40af;
  cursor: pointer;
  font-size: 14px;
  font-weight: 700;
  padding: 9px 18px;
  margin-top: 6px;
  transition: background 0.15s;
  font-family: inherit;
}
#inv-app .btn-add:hover { background: #dbeafe; }
/* Totals */
#inv-app .totals-block {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 8px;
}
#inv-app .total-row {
  display: flex;
  gap: 16px;
  align-items: center;
  min-width: 300px;
  justify-content: space-between;
}
#inv-app .total-row span:first-child {
  font-size: 13px;
  color: #64748b;
  font-weight: 500;
}
#inv-app .total-row span.total-val {
  font-size: 15px;
  font-weight: 700;
  color: #1e293b;
  min-width: 110px;
  text-align: right;
}
#inv-app .total-row.grand {
  border-top: 2px solid #1e40af;
  padding-top: 8px;
  margin-top: 4px;
}
#inv-app .total-row.grand span.total-val {
  font-size: 20px;
  color: #1e40af;
}
/* Buttons */
#inv-app .btn-primary {
  background: #1e40af;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 12px 28px;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
  font-family: inherit;
}
#inv-app .btn-primary:hover { background: #1d3a9e; }
#inv-app .btn-secondary {
  background: #f1f5f9;
  color: #334155;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  padding: 12px 24px;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  font-family: inherit;
}
#inv-app .btn-secondary:hover { background: #e2e8f0; }
#inv-app .actions-bar {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}
/* Preview */
#inv-app .preview-wrapper {
  background: #f1f5f9;
  border-radius: 10px;
  padding: 24px;
  margin-top: 8px;
}
#inv-app .invoice-preview {
  background: #fff;
  border-radius: 8px;
  padding: 36px 40px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.10);
  max-width: 720px;
  margin: 0 auto;
}
#inv-app .inv-preview-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 28px;
  padding-bottom: 18px;
  border-bottom: 3px solid #1e40af;
}
#inv-app .inv-preview-title {
  font-size: 32px;
  font-weight: 800;
  color: #1e40af;
  letter-spacing: -1px;
}
#inv-app .inv-preview-title small {
  display: block;
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  letter-spacing: 0;
  margin-top: 2px;
}
#inv-app .inv-preview-from-name { font-size: 16px; font-weight: 700; color: #1e293b; }
#inv-app .inv-preview-from-detail { font-size: 12px; color: #64748b; margin-top: 2px; white-space: pre-line; }
#inv-app .inv-preview-meta { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; margin-bottom: 22px; }
#inv-app .inv-preview-to-label { font-size: 11px; font-weight: 700; color: #1e40af; margin-bottom: 4px; }
#inv-app .inv-preview-to-name { font-size: 15px; font-weight: 700; color: #1e293b; }
#inv-app .inv-preview-to-detail { font-size: 12px; color: #64748b; margin-top: 2px; white-space: pre-line; }
#inv-app .inv-preview-info-grid {
  background: #eff6ff;
  border-radius: 8px;
  padding: 12px 16px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}
#inv-app .inv-preview-info-item label {
  font-size: 10px;
  font-weight: 700;
  color: #1e40af;
  letter-spacing: 0.04em;
  display: block;
}
#inv-app .inv-preview-info-item span {
  font-size: 13px;
  font-weight: 600;
  color: #1e293b;
  display: block;
  margin-top: 1px;
}
#inv-app .inv-preview-table { width: 100%; border-collapse: collapse; margin-bottom: 20px; }
#inv-app .inv-preview-table th {
  background: #1e40af;
  color: #fff;
  font-size: 11px;
  font-weight: 700;
  padding: 8px 10px;
  text-align: left;
}
#inv-app .inv-preview-table th:not(:first-child) { text-align: right; }
#inv-app .inv-preview-table td { padding: 9px 10px; font-size: 13px; color: #334155; border-bottom: 1px solid #e2e8f0; }
#inv-app .inv-preview-table td:not(:first-child) { text-align: right; }
#inv-app .inv-preview-table tr:nth-child(even) td { background: #f8fafc; }
#inv-app .inv-preview-totals { display: flex; flex-direction: column; align-items: flex-end; gap: 5px; margin-bottom: 22px; }
#inv-app .inv-preview-total-row { display: flex; justify-content: space-between; min-width: 260px; font-size: 13px; color: #475569; }
#inv-app .inv-preview-total-row.grand-total { font-size: 18px; font-weight: 800; color: #1e40af; border-top: 2px solid #1e40af; padding-top: 8px; margin-top: 4px; }
#inv-app .inv-preview-notes { background: #f8fafc; border-left: 3px solid #1e40af; padding: 10px 14px; border-radius: 0 6px 6px 0; font-size: 12px; color: #475569; white-space: pre-line; }
#inv-app .inv-preview-notes-label { font-size: 10px; font-weight: 700; color: #1e40af; letter-spacing: 0.04em; margin-bottom: 4px; }
#inv-app .inv-preview-footer { text-align: center; font-size: 11px; color: #94a3b8; margin-top: 24px; padding-top: 12px; border-top: 1px solid #e2e8f0; }
/* Responsive */
@media (max-width: 640px) {
  #inv-app .inv-grid-2 { grid-template-columns: 1fr; }
  #inv-app .inv-meta-row { grid-template-columns: 1fr 1fr; }
  #inv-app .line-items-header { display: none; }
  #inv-app .line-item-row { grid-template-columns: 1fr 1fr; }
  #inv-app .line-item-row input:first-child { grid-column: 1 / -1; }
  #inv-app .invoice-preview { padding: 18px 14px; }
  #inv-app .inv-preview-header { flex-direction: column; gap: 12px; }
  #inv-app .inv-preview-meta { grid-template-columns: 1fr; }
}
/* Print */
@media print {
  body > *:not(#inv-app) { display: none !important; }
  #inv-app .no-print { display: none !important; }
  #inv-app .preview-wrapper { padding: 0; background: none; }
  #inv-app .invoice-preview { box-shadow: none; padding: 20px; }
  #inv-app { max-width: 100%; }
}
</style>

<div id="inv-app">

<!-- ===== フォーム ===== -->
<div class="no-print">

<div class="inv-section">
<h2>請求元（自分の情報）</h2>
<div class="inv-grid-2">
  <div class="inv-field">
    <label>氏名・屋号・会社名</label>
    <input type="text" id="inv-from-name" placeholder="山田 太郎 / 山田デザイン事務所" oninput="invRender()">
  </div>
  <div class="inv-field">
    <label>メールアドレス</label>
    <input type="email" id="inv-from-email" placeholder="taro@example.com" oninput="invRender()">
  </div>
  <div class="inv-field" style="grid-column:1/-1">
    <label>住所</label>
    <textarea id="inv-from-address" placeholder="〒150-0001 東京都渋谷区神宮前1-1-1" oninput="invRender()"></textarea>
  </div>
  <div class="inv-field" style="grid-column:1/-1">
    <label>適格請求書発行事業者 登録番号 <span class="invoice-badge">インボイス対応</span></label>
    <input type="text" id="inv-regnum" placeholder="T1234567890123（13桁）" oninput="invRender()">
  </div>
</div>
</div>

<div class="inv-section">
<h2>請求先（取引先の情報）</h2>
<div class="inv-grid-2">
  <div class="inv-field">
    <label>取引先名・会社名</label>
    <input type="text" id="inv-to-name" placeholder="株式会社クライアント 御中" oninput="invRender()">
  </div>
  <div class="inv-field">
    <label>取引先メールアドレス</label>
    <input type="email" id="inv-to-email" placeholder="client@example.co.jp" oninput="invRender()">
  </div>
  <div class="inv-field" style="grid-column:1/-1">
    <label>取引先住所</label>
    <textarea id="inv-to-address" placeholder="〒100-0001 東京都千代田区丸の内1-1-1" oninput="invRender()"></textarea>
  </div>
</div>
</div>

<div class="inv-section">
<h2>請求書情報</h2>
<div class="inv-meta-row">
  <div class="inv-field">
    <label>請求書番号</label>
    <input type="text" id="inv-number" oninput="invRender()">
  </div>
  <div class="inv-field">
    <label>通貨</label>
    <select id="inv-currency" onchange="invRender()">
      <option value="¥" selected>¥ 円（JPY）</option>
      <option value="$">$ USD</option>
      <option value="€">€ EUR</option>
      <option value="£">£ GBP</option>
    </select>
  </div>
  <div class="inv-field">
    <label>請求日</label>
    <input type="date" id="inv-date" oninput="invRender()">
  </div>
  <div class="inv-field">
    <label>支払期限</label>
    <input type="date" id="inv-due" oninput="invRender()">
  </div>
</div>
</div>

<div class="inv-section">
<h2>明細 <span class="invoice-badge">税率区分 10%/8% 対応</span></h2>
<div class="line-items-header">
  <span>品目・内容</span>
  <span>数量</span>
  <span>単価</span>
  <span>税率</span>
  <span>金額（税抜）</span>
  <span></span>
</div>
<div id="inv-lines"></div>
<button class="btn-add" onclick="invAddLine()">＋ 明細を追加</button>
</div>

<div class="inv-section">
<h2>合計・消費税・備考</h2>
<div style="display:flex;flex-wrap:wrap;gap:32px;justify-content:space-between;align-items:flex-start;">
  <div class="inv-field" style="flex:1;min-width:200px;">
    <label>備考・振込先・支払条件</label>
    <textarea id="inv-notes" placeholder="お振込先：〇〇銀行 〇〇支店 普通 1234567&#10;お振込期限：請求日より30日以内&#10;※振込手数料はご負担ください。" oninput="invRender()"></textarea>
  </div>
  <div class="totals-block">
    <div class="total-row">
      <span>小計（税抜）</span>
      <span class="total-val" id="inv-subtotal-display">—</span>
    </div>
    <div class="total-row">
      <span>消費税（10%）</span>
      <span class="total-val" id="inv-tax10-display">—</span>
    </div>
    <div class="total-row">
      <span>消費税（8%）</span>
      <span class="total-val" id="inv-tax8-display">—</span>
    </div>
    <div class="total-row">
      <span>消費税合計</span>
      <span class="total-val" id="inv-tax-total-display">—</span>
    </div>
    <div class="total-row grand">
      <span style="font-size:15px;font-weight:700;color:#1e40af;">請求合計（税込）</span>
      <span class="total-val" id="inv-grand-display" style="color:#1e40af;">—</span>
    </div>
  </div>
</div>
</div>

<div class="actions-bar" style="margin-bottom:28px;">
  <button class="btn-primary" onclick="invPrint()">&#128438; 印刷・PDFで保存</button>
  <button class="btn-secondary" onclick="invReset()">&#x21BA; リセット</button>
</div>

</div><!-- /no-print -->

<!-- ===== プレビュー ===== -->
<div class="preview-wrapper">
  <p style="font-size:12px;color:#64748b;margin-bottom:12px;font-weight:700;letter-spacing:0.04em;" class="no-print">リアルタイムプレビュー</p>
  <div class="invoice-preview" id="inv-preview-box">
    <!-- JS でレンダリング -->
  </div>
</div>

</div><!-- /#inv-app -->

<script>
(function() {
  var pad = function(n){ return String(n).padStart(2,'0'); };
  var today = new Date();
  var fmtDate = function(d){ return d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate()); };
  var due = new Date(today); due.setDate(due.getDate()+30);
  var invNum = 'INV-'+today.getFullYear()+pad(today.getMonth()+1)+pad(today.getDate())+'-'+Math.floor(Math.random()*900+100);

  document.getElementById('inv-number').value = invNum;
  document.getElementById('inv-date').value = fmtDate(today);
  document.getElementById('inv-due').value = fmtDate(due);

  // lines: each has desc, qty, price, taxRate (10 or 8)
  var lines = [{ desc:'', qty:1, price:0, taxRate:10 }];

  function escHtml(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }

  function fmtNum(n, sym) {
    if(sym === '¥') return Number(n).toLocaleString('ja-JP', {minimumFractionDigits:0, maximumFractionDigits:0});
    return Number(n).toLocaleString('en-US', {minimumFractionDigits:2, maximumFractionDigits:2});
  }

  function renderLines() {
    var container = document.getElementById('inv-lines');
    container.innerHTML = '';
    var sym = document.getElementById('inv-currency').value;
    lines.forEach(function(line, i) {
      var row = document.createElement('div');
      row.className = 'line-item-row';
      var subtotal = (parseFloat(line.qty)||0) * (parseFloat(line.price)||0);
      row.innerHTML =
        '<input type="text" placeholder="Webデザイン制作費（5月分）" value="'+escHtml(line.desc)+'" oninput="invLineUpdate('+i+',\'desc\',this.value)">' +
        '<input type="number" placeholder="1" value="'+line.qty+'" min="0" step="any" oninput="invLineUpdate('+i+',\'qty\',this.value)">' +
        '<input type="number" placeholder="0" value="'+line.price+'" min="0" step="any" oninput="invLineUpdate('+i+',\'price\',this.value)">' +
        '<select onchange="invLineUpdate('+i+',\'taxRate\',this.value)">' +
          '<option value="10"'+(line.taxRate==10?' selected':'')+'>10%</option>' +
          '<option value="8"'+(line.taxRate==8?' selected':'')+'>8%&#x2605;</option>' +
        '</select>' +
        '<div class="line-item-total">'+sym+fmtNum(subtotal,sym)+'</div>' +
        '<button class="btn-remove" onclick="invRemoveLine('+i+')" title="削除">&#215;</button>';
      container.appendChild(row);
    });
  }

  window.invLineUpdate = function(i, field, val) {
    lines[i][field] = (field==='taxRate') ? parseInt(val) : val;
    invRender();
  };
  window.invAddLine = function() {
    lines.push({ desc:'', qty:1, price:0, taxRate:10 });
    invRender();
  };
  window.invRemoveLine = function(i) {
    if(lines.length === 1) return;
    lines.splice(i,1);
    invRender();
  };

  function calcTotals() {
    var sub10=0, sub8=0;
    lines.forEach(function(l){
      var amt = (parseFloat(l.qty)||0)*(parseFloat(l.price)||0);
      if(parseInt(l.taxRate)===8) sub8+=amt; else sub10+=amt;
    });
    var tax10 = Math.floor(sub10*0.10);
    var tax8  = Math.floor(sub8*0.08);
    var subTotal = sub10+sub8;
    var taxTotal = tax10+tax8;
    var grand = subTotal+taxTotal;
    return { sub10:sub10, sub8:sub8, subTotal:subTotal, tax10:tax10, tax8:tax8, taxTotal:taxTotal, grand:grand };
  }

  window.invRender = function() {
    renderLines();
    var sym = document.getElementById('inv-currency').value;
    var t = calcTotals();
    document.getElementById('inv-subtotal-display').textContent = sym+fmtNum(t.subTotal,sym);
    document.getElementById('inv-tax10-display').textContent = sym+fmtNum(t.tax10,sym);
    document.getElementById('inv-tax8-display').textContent = sym+fmtNum(t.tax8,sym);
    document.getElementById('inv-tax-total-display').textContent = sym+fmtNum(t.taxTotal,sym);
    document.getElementById('inv-grand-display').textContent = sym+fmtNum(t.grand,sym);
    renderPreview(t, sym);
  };

  function renderPreview(t, sym) {
    var fromName = document.getElementById('inv-from-name').value || '氏名・会社名';
    var fromEmail = document.getElementById('inv-from-email').value;
    var fromAddr = document.getElementById('inv-from-address').value;
    var regNum = document.getElementById('inv-regnum').value;
    var toName = document.getElementById('inv-to-name').value || '取引先名';
    var toEmail = document.getElementById('inv-to-email').value;
    var toAddr = document.getElementById('inv-to-address').value;
    var invNo = document.getElementById('inv-number').value;
    var invDate = document.getElementById('inv-date').value;
    var invDue = document.getElementById('inv-due').value;
    var notes = document.getElementById('inv-notes').value;

    var fromParts = [fromEmail, fromAddr];
    if(regNum) fromParts.push('登録番号: '+regNum);
    var fromDetail = fromParts.filter(Boolean).join('\n');
    var toDetail = [toEmail, toAddr].filter(Boolean).join('\n');

    var tableRows = lines.map(function(l) {
      var qty = parseFloat(l.qty)||0;
      var price = parseFloat(l.price)||0;
      var subtotal = qty*price;
      var rate = parseInt(l.taxRate)===8 ? '8%★' : '10%';
      return '<tr>' +
        '<td>'+(escHtml(l.desc)||'<span style="color:#94a3b8;font-style:italic;">品目</span>')+'</td>' +
        '<td>'+qty+'</td>' +
        '<td>'+sym+fmtNum(price,sym)+'</td>' +
        '<td>'+rate+'</td>' +
        '<td>'+sym+fmtNum(subtotal,sym)+'</td>' +
        '</tr>';
    }).join('');

    var regNumHtml = regNum ? '<div style="font-size:11px;color:#64748b;margin-top:4px;">登録番号: '+escHtml(regNum)+'</div>' : '';
    var notesHtml = notes ? '<div class="inv-preview-notes-label">備考</div><div class="inv-preview-notes">'+escHtml(notes)+'</div>' : '';
    var tax8row = t.sub8>0
      ? '<div class="inv-preview-total-row"><span>消費税（8% 軽減税率）</span><span>'+sym+fmtNum(t.tax8,sym)+'</span></div>' : '';
    var tax10row = '<div class="inv-preview-total-row"><span>消費税（10%）</span><span>'+sym+fmtNum(t.tax10,sym)+'</span></div>';

    document.getElementById('inv-preview-box').innerHTML =
      '<div class="inv-preview-header">' +
        '<div>' +
          '<div class="inv-preview-title">請求書<small>INVOICE</small></div>' +
        '</div>' +
        '<div style="text-align:right">' +
          '<div class="inv-preview-from-name">'+escHtml(fromName)+'</div>' +
          '<div class="inv-preview-from-detail">'+escHtml(fromDetail)+'</div>' +
          regNumHtml +
        '</div>' +
      '</div>' +
      '<div class="inv-preview-meta">' +
        '<div>' +
          '<div class="inv-preview-to-label">請求先</div>' +
          '<div class="inv-preview-to-name">'+escHtml(toName)+'</div>' +
          '<div class="inv-preview-to-detail">'+escHtml(toDetail)+'</div>' +
        '</div>' +
        '<div>' +
          '<div class="inv-preview-info-grid">' +
            '<div class="inv-preview-info-item"><label>請求書番号</label><span>'+escHtml(invNo)+'</span></div>' +
            '<div class="inv-preview-info-item"><label>通貨</label><span>'+escHtml(sym)+'</span></div>' +
            '<div class="inv-preview-info-item"><label>請求日</label><span>'+escHtml(invDate)+'</span></div>' +
            '<div class="inv-preview-info-item"><label>支払期限</label><span>'+escHtml(invDue)+'</span></div>' +
          '</div>' +
        '</div>' +
      '</div>' +
      '<table class="inv-preview-table">' +
        '<thead><tr>' +
          '<th>品目・内容</th><th style="text-align:right">数量</th><th style="text-align:right">単価</th><th style="text-align:right">税率</th><th style="text-align:right">金額（税抜）</th>' +
        '</tr></thead>' +
        '<tbody>'+tableRows+'</tbody>' +
      '</table>' +
      '<div style="font-size:10px;color:#94a3b8;text-align:right;margin-bottom:10px;">★ 軽減税率対象</div>' +
      '<div class="inv-preview-totals">' +
        '<div class="inv-preview-total-row"><span>小計（税抜）</span><span>'+sym+fmtNum(t.subTotal,sym)+'</span></div>' +
        tax10row +
        tax8row +
        '<div class="inv-preview-total-row"><span>消費税合計</span><span>'+sym+fmtNum(t.taxTotal,sym)+'</span></div>' +
        '<div class="inv-preview-total-row grand-total"><span>合計（税込）</span><span>'+sym+fmtNum(t.grand,sym)+'</span></div>' +
      '</div>' +
      notesHtml +
      '<div class="inv-preview-footer">※本請求書は適格請求書（インボイス）として発行されています。</div>';
  }

  window.invPrint = function() { window.print(); };

  window.invReset = function() {
    ['inv-from-name','inv-from-email','inv-from-address','inv-regnum',
     'inv-to-name','inv-to-email','inv-to-address','inv-notes'].forEach(function(id){
      document.getElementById(id).value='';
    });
    document.getElementById('inv-currency').value='¥';
    var today2=new Date();
    var due2=new Date(today2); due2.setDate(due2.getDate()+30);
    document.getElementById('inv-number').value='INV-'+today2.getFullYear()+pad(today2.getMonth()+1)+pad(today2.getDate())+'-'+Math.floor(Math.random()*900+100);
    document.getElementById('inv-date').value=fmtDate(today2);
    document.getElementById('inv-due').value=fmtDate(due2);
    lines=[{desc:'',qty:1,price:0,taxRate:10}];
    invRender();
  };

  invRender();
})();
</script>

---

## 使い方

1. **請求元を入力** — 自分の氏名・屋号・住所・メール、そして適格請求書発行事業者の登録番号（T＋13桁）を入力します。
2. **請求先を入力** — 取引先の会社名・住所・メールアドレスを入力します。
3. **請求書情報を設定** — 請求書番号は自動生成されます。請求日・支払期限・通貨を必要に応じて変更してください。
4. **明細を追加** — 「＋ 明細を追加」で行を追加。品目・数量・単価を入力すると金額が自動計算されます。税率は10%/8%（軽減税率）を行ごとに選択できます。
5. **消費税を確認** — 10%・8%の税額が自動で分けて計算されます。インボイス制度の要件を満たします。
6. **備考・振込先を入力** — 振込先口座や支払条件を記載しましょう。
7. **印刷・PDF保存** — 「印刷・PDFで保存」ボタンをクリック。ブラウザの印刷ダイアログで「PDFに保存」を選択するとPDFが作成されます。

## インボイス制度（適格請求書）の記載要件

2023年10月から開始した**インボイス制度**に対応するため、請求書には以下の記載が必要です。

| 必要記載事項 | このツールでの入力欄 |
|---|---|
| 適格請求書発行事業者の氏名・名称 | 請求元「氏名・屋号・会社名」 |
| **登録番号（T＋13桁）** | 請求元「登録番号」欄 |
| 取引年月日 | 請求日 |
| 取引内容 | 明細「品目・内容」 |
| **税率ごとに区分した対価の額** | 明細「税率」（10%/8%） |
| **税率ごとの消費税額** | 合計欄（自動計算） |
| 書類交付を受ける事業者の氏名・名称 | 請求先「取引先名」 |

---

## 関連ツール

> フリーランスの適正時給を計算 → [フリーランス報酬計算ツール](/ja/tools/freelance-hoshu-calculator/)

> 支払いリンクやビジネスカードにQRコードを生成 → [QRコードジェネレーター](/ja/tools/qr-code-generator/)

> 副業・フリーランス収入の税金を計算 → [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/)

---

**請求書管理の自動化ならfreee**

請求書の作成・管理を効率化したい方に。freeeなら請求書の作成から入金管理まで一括で行えます。インボイス制度にも対応。

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
