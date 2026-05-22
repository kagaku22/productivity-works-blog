---
title: "請求書ジェネレーター"
date: 2025-04-19
description: "無料の請求書作成ツール。品目・数量・単価を入力して税込み金額を自動計算、PDF印刷対応。会員登録不要、すべてブラウザで完結。インボイス制度対応。"
categories: ["無料ツール"]
tags: ["便利ツール", "無料ツール"]
slug: "invoice-generator"
ShowToc: false
cover:
  image: "/images/covers/invoice-generator-ja.png"
  alt: "請求書ジェネレーター"
---

ブラウザだけで完結する無料の請求書作成ツールです。品目・数量・単価を入力すると消費税（10%・8%軽減税率・0%）を自動計算し、そのままPDF保存・印刷が可能です。インボイス制度の登録番号にも対応しています。

<div id="ig-app">
<style>
/* ============================================================
BASE RESET & LAYOUT
============================================================ */
#ig-app *,
#ig-app *::before,
#ig-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#ig-app {
font-family: system-ui, "Hiragino Sans", "Yu Gothic UI", "Meiryo", sans-serif;
font-size: 14px;
color: #1e293b;
line-height: 1.6;
}

/* ============================================================
FORM CARD
============================================================ */
#ig-app .ig-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 20px 22px;
margin-bottom: 18px;
}
#ig-app .ig-card-title {
font-size: 13px;
font-weight: 700;
color: #475569;
text-transform: uppercase;
letter-spacing: .04em;
border-bottom: 1px solid #f1f5f9;
padding-bottom: 8px;
margin-bottom: 14px;
}

/* ============================================================
GRID & FIELDS
============================================================ */
#ig-app .ig-grid {
display: grid;
gap: 10px 14px;
}
#ig-app .ig-grid-2 { grid-template-columns: 1fr 1fr; }
#ig-app .ig-grid-3 { grid-template-columns: 1fr 1fr 1fr; }
#ig-app label.ig-label {
display: block;
font-size: 12px;
font-weight: 600;
color: #64748b;
margin-bottom: 3px;
}
#ig-app input[type="text"],
#ig-app input[type="date"],
#ig-app input[type="email"],
#ig-app input[type="tel"],
#ig-app input[type="number"],
#ig-app select,
#ig-app textarea {
width: 100%;
padding: 7px 10px;
border: 1px solid #cbd5e1;
border-radius: 6px;
font-size: 13px;
font-family: inherit;
color: #1e293b;
background: #f8fafc;
transition: border-color .15s, box-shadow .15s;
outline: none;
}
#ig-app input:focus,
#ig-app select:focus,
#ig-app textarea:focus {
border-color: #0284c7;
box-shadow: 0 0 0 3px rgba(2,132,199,.12);
background: #fff;
}
#ig-app textarea { resize: vertical; min-height: 70px; }

/* ============================================================
LINE ITEMS TABLE
============================================================ */
#ig-app .ig-items-wrap {
overflow-x: auto;
}
#ig-app table.ig-items {
width: 100%;
border-collapse: collapse;
min-width: 640px;
font-size: 13px;
}
#ig-app table.ig-items th {
background: #f1f5f9;
color: #475569;
font-weight: 700;
font-size: 12px;
text-align: center;
padding: 7px 8px;
border: 1px solid #e2e8f0;
white-space: nowrap;
}
#ig-app table.ig-items td {
padding: 5px 5px;
border: 1px solid #e2e8f0;
vertical-align: middle;
}
#ig-app table.ig-items td input,
#ig-app table.ig-items td select {
padding: 5px 7px;
font-size: 13px;
}
#ig-app table.ig-items td.ig-subtotal {
text-align: right;
font-weight: 600;
white-space: nowrap;
padding-right: 10px;
color: #0f172a;
}
#ig-app .ig-btn-del {
background: #fee2e2;
color: #dc2626;
border: 1px solid #fca5a5;
border-radius: 5px;
padding: 4px 8px;
cursor: pointer;
font-size: 12px;
font-weight: 700;
transition: background .15s;
}
#ig-app .ig-btn-del:hover { background: #fecaca; }
#ig-app .ig-btn-add {
background: #f0fdf4;
color: #16a34a;
border: 1px dashed #86efac;
border-radius: 6px;
padding: 7px 16px;
cursor: pointer;
font-size: 13px;
font-weight: 600;
margin-top: 10px;
transition: background .15s;
}
#ig-app .ig-btn-add:hover { background: #dcfce7; }

/* ============================================================
TOTALS
============================================================ */
#ig-app .ig-totals {
display: flex;
justify-content: flex-end;
}
#ig-app .ig-totals-table {
width: 100%;
max-width: 340px;
font-size: 13px;
}
#ig-app .ig-totals-table tr td {
padding: 5px 8px;
}
#ig-app .ig-totals-table tr td:last-child {
text-align: right;
font-weight: 600;
white-space: nowrap;
}
#ig-app .ig-totals-table .ig-total-grand td {
background: #0284c7;
color: #fff;
font-size: 15px;
font-weight: 700;
border-radius: 4px;
padding: 8px 10px;
}

/* ============================================================
ACTION BUTTONS
============================================================ */
#ig-app .ig-actions {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-top: 4px;
}
#ig-app .ig-btn-preview {
background: #0284c7;
color: #fff;
border: none;
border-radius: 7px;
padding: 10px 26px;
font-size: 14px;
font-weight: 700;
cursor: pointer;
font-family: inherit;
transition: background .15s;
}
#ig-app .ig-btn-preview:hover { background: #0369a1; }
#ig-app .ig-btn-print {
background: #f8fafc;
color: #334155;
border: 1px solid #cbd5e1;
border-radius: 7px;
padding: 10px 22px;
font-size: 14px;
font-weight: 600;
cursor: pointer;
font-family: inherit;
transition: background .15s;
}
#ig-app .ig-btn-print:hover { background: #e2e8f0; }

/* ============================================================
MODAL OVERLAY
============================================================ */
#ig-app .ig-modal-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(15,23,42,.55);
z-index: 9000;
overflow-y: auto;
padding: 24px 16px;
}
#ig-app .ig-modal-overlay.open { display: block; }
#ig-app .ig-modal-inner {
background: #fff;
max-width: 760px;
margin: 0 auto;
border-radius: 10px;
overflow: hidden;
box-shadow: 0 20px 60px rgba(0,0,0,.25);
}
#ig-app .ig-modal-header {
background: #0284c7;
color: #fff;
padding: 14px 20px;
display: flex;
justify-content: space-between;
align-items: center;
}
#ig-app .ig-modal-header h2 { font-size: 15px; font-weight: 700; }
#ig-app .ig-modal-close {
background: none;
border: none;
color: #fff;
font-size: 22px;
cursor: pointer;
line-height: 1;
font-weight: 700;
padding: 0 4px;
}
#ig-app .ig-modal-body { padding: 24px 28px; }

/* ============================================================
INVOICE PREVIEW
============================================================ */
#ig-app .ig-preview {
font-family: system-ui, "Hiragino Sans", "Yu Gothic UI", "Meiryo", sans-serif;
font-size: 13px;
color: #0f172a;
line-height: 1.65;
}
#ig-app .ig-preview-top {
display: flex;
justify-content: space-between;
align-items: flex-start;
margin-bottom: 24px;
}
#ig-app .ig-preview-title {
font-size: 28px;
font-weight: 900;
color: #0284c7;
letter-spacing: .02em;
}
#ig-app .ig-preview-issuer {
text-align: right;
font-size: 12px;
color: #334155;
}
#ig-app .ig-preview-issuer strong {
display: block;
font-size: 15px;
font-weight: 700;
color: #0f172a;
margin-bottom: 2px;
}
#ig-app .ig-preview-issuer .ig-reg-num {
display: inline-block;
margin-top: 4px;
background: #f0f9ff;
border: 1px solid #bae6fd;
border-radius: 4px;
padding: 2px 8px;
font-size: 11px;
color: #0369a1;
font-weight: 600;
}
#ig-app .ig-preview-bill-to {
margin-bottom: 20px;
}
#ig-app .ig-preview-bill-to .ig-bill-name {
font-size: 18px;
font-weight: 700;
border-bottom: 2px solid #0284c7;
display: inline-block;
padding-bottom: 2px;
margin-bottom: 4px;
}
#ig-app .ig-preview-meta {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 6px 20px;
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 6px;
padding: 12px 16px;
margin-bottom: 20px;
font-size: 12px;
}
#ig-app .ig-preview-meta .ig-meta-label { color: #64748b; font-weight: 600; }
#ig-app .ig-preview-meta .ig-meta-value { font-weight: 700; }
#ig-app table.ig-preview-items {
width: 100%;
border-collapse: collapse;
font-size: 12px;
margin-bottom: 16px;
}
#ig-app table.ig-preview-items th {
background: #0284c7;
color: #fff;
font-weight: 700;
padding: 7px 10px;
text-align: center;
white-space: nowrap;
}
#ig-app table.ig-preview-items th:first-child { text-align: left; }
#ig-app table.ig-preview-items td {
padding: 6px 10px;
border-bottom: 1px solid #e2e8f0;
vertical-align: middle;
}
#ig-app table.ig-preview-items tr:nth-child(even) td { background: #f8fafc; }
#ig-app table.ig-preview-items td:not(:first-child) { text-align: right; white-space: nowrap; }
#ig-app .ig-preview-totals {
display: flex;
justify-content: flex-end;
margin-bottom: 16px;
}
#ig-app .ig-preview-totals table {
font-size: 12px;
min-width: 260px;
}
#ig-app .ig-preview-totals td {
padding: 4px 10px;
}
#ig-app .ig-preview-totals td:last-child {
text-align: right;
font-weight: 600;
white-space: nowrap;
}
#ig-app .ig-preview-totals .ig-grand td {
background: #0284c7;
color: #fff;
font-size: 14px;
font-weight: 700;
padding: 8px 12px;
}
#ig-app .ig-preview-bank {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 6px;
padding: 10px 14px;
font-size: 12px;
margin-bottom: 14px;
white-space: pre-wrap;
}
#ig-app .ig-preview-bank-title {
font-weight: 700;
font-size: 12px;
color: #0284c7;
margin-bottom: 4px;
}
#ig-app .ig-preview-note {
font-size: 12px;
color: #475569;
background: #fffbeb;
border-left: 3px solid #fbbf24;
padding: 8px 12px;
border-radius: 0 6px 6px 0;
}

/* ============================================================
PRINT STYLES
============================================================ */
@media print {
#ig-app .ig-form-section,
#ig-app .ig-actions,
#ig-app .ig-modal-overlay,
#ig-app .ig-cta,
#ig-app .ig-crosslinks {
display: none !important;
}
#ig-app .ig-print-area {
display: block !important;
}
}
#ig-app .ig-print-area {
display: none;
}

/* ============================================================
RESPONSIVE
============================================================ */
@media (max-width: 600px) {
#ig-app .ig-grid-2,
#ig-app .ig-grid-3 {
grid-template-columns: 1fr;
}
#ig-app .ig-preview-top {
flex-direction: column;
gap: 12px;
}
#ig-app .ig-preview-issuer { text-align: left; }
#ig-app .ig-preview-meta {
grid-template-columns: 1fr;
}
}
</style>

<!-- ============================================================
FORM SECTION
============================================================ -->
<div class="ig-form-section">

<!-- 発行者情報 -->
<div class="ig-card">
<div class="ig-card-title">発行者情報</div>
<div class="ig-grid ig-grid-2">
<div>
<label class="ig-label" for="ig-issuer-name">会社名・屋号</label>
<input type="text" id="ig-issuer-name" placeholder="株式会社サンプル">
</div>
<div>
<label class="ig-label" for="ig-issuer-reg">登録番号（インボイス）</label>
<input type="text" id="ig-issuer-reg" placeholder="T1234567890123" maxlength="14">
</div>
<div>
<label class="ig-label" for="ig-issuer-addr">住所</label>
<input type="text" id="ig-issuer-addr" placeholder="東京都渋谷区〇〇 1-2-3">
</div>
<div>
<label class="ig-label" for="ig-issuer-email">メールアドレス</label>
<input type="email" id="ig-issuer-email" placeholder="info@example.com">
</div>
<div>
<label class="ig-label" for="ig-issuer-tel">電話番号</label>
<input type="tel" id="ig-issuer-tel" placeholder="03-0000-0000">
</div>
</div>
</div>

<!-- 請求先情報 -->
<div class="ig-card">
<div class="ig-card-title">請求先情報</div>
<div class="ig-grid ig-grid-2">
<div>
<label class="ig-label" for="ig-client-name">会社名</label>
<input type="text" id="ig-client-name" placeholder="株式会社クライアント">
</div>
<div>
<label class="ig-label" for="ig-client-person">担当者名</label>
<input type="text" id="ig-client-person" placeholder="山田 太郎">
</div>
<div style="grid-column: 1 / -1;">
<label class="ig-label" for="ig-client-addr">住所</label>
<input type="text" id="ig-client-addr" placeholder="東京都新宿区〇〇 4-5-6">
</div>
</div>
</div>

<!-- 請求書情報 -->
<div class="ig-card">
<div class="ig-card-title">請求書情報</div>
<div class="ig-grid ig-grid-3">
<div>
<label class="ig-label" for="ig-inv-num">請求書番号</label>
<input type="text" id="ig-inv-num">
</div>
<div>
<label class="ig-label" for="ig-inv-date">発行日</label>
<input type="date" id="ig-inv-date">
</div>
<div>
<label class="ig-label" for="ig-inv-due">支払期日</label>
<input type="date" id="ig-inv-due">
</div>
</div>
</div>

<!-- 品目 -->
<div class="ig-card">
<div class="ig-card-title">品目</div>
<div class="ig-items-wrap">
<table class="ig-items" id="ig-items-table">
<thead>
<tr>
<th style="min-width:180px;text-align:left;">品名・説明</th>
<th style="width:70px;">数量</th>
<th style="width:110px;">単価（円）</th>
<th style="width:100px;">税率</th>
<th style="width:110px;">小計（税抜）</th>
<th style="width:44px;"></th>
</tr>
</thead>
<tbody id="ig-items-body">
<!-- rows injected by JS -->
</tbody>
</table>
</div>
<button class="ig-btn-add" onclick="igAddRow()">＋ 品目を追加</button>
</div>

<!-- 合計 -->
<div class="ig-card">
<div class="ig-card-title">合計</div>
<div class="ig-totals">
<table class="ig-totals-table">
<tbody>
<tr>
<td>小計（税抜）</td>
<td id="ig-t-subtotal">¥0</td>
</tr>
<tr>
<td>10%対象額</td>
<td id="ig-t-base10">¥0</td>
</tr>
<tr>
<td>消費税（10%）</td>
<td id="ig-t-tax10">¥0</td>
</tr>
<tr>
<td>8%対象額（軽減税率）</td>
<td id="ig-t-base8">¥0</td>
</tr>
<tr>
<td>消費税（8%）</td>
<td id="ig-t-tax8">¥0</td>
</tr>
<tr class="ig-total-grand">
<td>合計（税込）</td>
<td id="ig-t-grand">¥0</td>
</tr>
</tbody>
</table>
</div>
<div style="margin-top:16px;">
<label class="ig-label" for="ig-bank">振込先情報</label>
<textarea id="ig-bank" rows="3" placeholder="銀行名：〇〇銀行 〇〇支店&#10;口座種別：普通&#10;口座番号：0000000&#10;口座名義：カ）サンプル"></textarea>
</div>
</div>

<!-- 備考 -->
<div class="ig-card">
<div class="ig-card-title">備考</div>
<textarea id="ig-note" rows="3" placeholder="お支払いにつきましては上記期日までにお振込みいただけますようお願い申し上げます。"></textarea>
</div>

<!-- アクション -->
<div class="ig-actions">
<button class="ig-btn-preview" onclick="igShowPreview()">プレビュー</button>
<button class="ig-btn-print" onclick="igPrint()">印刷 / PDF保存</button>
</div>

</div><!-- /ig-form-section -->

<!-- ============================================================
MODAL PREVIEW
============================================================ -->
<div class="ig-modal-overlay" id="ig-modal">
<div class="ig-modal-inner">
<div class="ig-modal-header">
<h2>請求書プレビュー</h2>
<button class="ig-modal-close" onclick="igCloseModal()" title="閉じる">&#x2715;</button>
</div>
<div class="ig-modal-body">
<div id="ig-preview-content" class="ig-preview"></div>
<div style="margin-top:18px;display:flex;gap:10px;flex-wrap:wrap;">
<button class="ig-btn-preview" onclick="igPrint()">印刷 / PDF保存</button>
<button class="ig-btn-print" onclick="igCloseModal()">閉じる</button>
</div>
</div>
</div>
</div>

<!-- ============================================================
PRINT AREA (hidden on screen)
============================================================ -->
<div class="ig-print-area" id="ig-print-area"></div>

<!-- ============================================================
JAVASCRIPT
============================================================ -->
<script>
(function(){
/* ---------- State ---------- */
var rows = [];
var rowId = 0;

/* ---------- Init ---------- */
function init(){
// Auto invoice number
var now = new Date();
var yyyymm = now.getFullYear().toString() +
String(now.getMonth()+1).padStart(2,'0');
var rand = String(Math.floor(Math.random()*900)+100);
document.getElementById('ig-inv-num').value = 'INV-' + yyyymm + '-' + rand;

// Dates
var today = now.toISOString().slice(0,10);
document.getElementById('ig-inv-date').value = today;
var due = new Date(now);
due.setMonth(due.getMonth()+1);
due.setDate(0); // last day of current month
document.getElementById('ig-inv-due').value = due.toISOString().slice(0,10);

// Default rows
addRow();
addRow();
}

/* ---------- Row management ---------- */
function addRow(){
var id = ++rowId;
rows.push({id:id});
renderRows();
}
window.igAddRow = addRow;

function deleteRow(id){
rows = rows.filter(function(r){ return r.id !== id; });
renderRows();
calcTotals();
}
window.igDeleteRow = deleteRow;

function renderRows(){
var tbody = document.getElementById('ig-items-body');
tbody.innerHTML = '';
rows.forEach(function(r){
var tr = document.createElement('tr');
tr.id = 'ig-row-' + r.id;
tr.innerHTML =
'<td><input type="text" placeholder="品名・説明" oninput="igCalcRow('+r.id+')" id="ig-name-'+r.id+'"></td>' +
'<td><input type="number" min="0" step="1" value="1" style="text-align:right;" oninput="igCalcRow('+r.id+')" id="ig-qty-'+r.id+'"></td>' +
'<td><input type="number" min="0" step="1" value="0" style="text-align:right;" oninput="igCalcRow('+r.id+')" id="ig-price-'+r.id+'"></td>' +
'<td><select oninput="igCalcRow('+r.id+')" id="ig-tax-'+r.id+'">' +
'<option value="10">10%</option>' +
'<option value="8">8%（軽減）</option>' +
'<option value="0">0%（非課税）</option>' +
'</select></td>' +
'<td class="ig-subtotal" id="ig-sub-'+r.id+'">¥0</td>' +
'<td style="text-align:center;"><button class="ig-btn-del" onclick="igDeleteRow('+r.id+')">削除</button></td>';
tbody.appendChild(tr);
});
}

function calcRow(id){
var qty = parseFloat(document.getElementById('ig-qty-'+id).value)||0;
var price = parseFloat(document.getElementById('ig-price-'+id).value)||0;
var sub = qty * price;
document.getElementById('ig-sub-'+id).textContent = fmtYen(sub);
calcTotals();
}
window.igCalcRow = calcRow;

/* ---------- Totals ---------- */
function calcTotals(){
var base10=0, base8=0, base0=0;
rows.forEach(function(r){
var qty = parseFloat((document.getElementById('ig-qty-'+r.id)||{}).value)||0;
var price = parseFloat((document.getElementById('ig-price-'+r.id)||{}).value)||0;
var tax = (document.getElementById('ig-tax-'+r.id)||{}).value||'10';
var sub = qty * price;
if(tax==='10') base10 += sub;
else if(tax==='8') base8 += sub;
else base0 += sub;
});
var tax10 = Math.floor(base10 * 0.10);
var tax8  = Math.floor(base8  * 0.08);
var subtotal = base10 + base8 + base0;
var grand = subtotal + tax10 + tax8;

document.getElementById('ig-t-subtotal').textContent = fmtYen(subtotal);
document.getElementById('ig-t-base10').textContent = fmtYen(base10);
document.getElementById('ig-t-tax10').textContent = fmtYen(tax10);
document.getElementById('ig-t-base8').textContent = fmtYen(base8);
document.getElementById('ig-t-tax8').textContent = fmtYen(tax8);
document.getElementById('ig-t-grand').textContent = fmtYen(grand);
return {base10:base10,base8:base8,base0:base0,tax10:tax10,tax8:tax8,subtotal:subtotal,grand:grand};
}

/* ---------- Format helpers ---------- */
function fmtYen(n){
return '¥' + Math.round(n).toLocaleString('ja-JP');
}
function fmtDate(s){
if(!s) return '';
var parts = s.split('-');
return parts[0]+'年'+parseInt(parts[1])+'月'+parseInt(parts[2])+'日';
}
function esc(s){
return (s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

/* ---------- Collect form data ---------- */
function collectData(){
var totals = calcTotals();
var itemsData = rows.map(function(r){
var qty = parseFloat((document.getElementById('ig-qty-'+r.id)||{}).value)||0;
var price = parseFloat((document.getElementById('ig-price-'+r.id)||{}).value)||0;
var tax = (document.getElementById('ig-tax-'+r.id)||{}).value||'10';
var name = (document.getElementById('ig-name-'+r.id)||{}).value||'';
var sub = qty * price;
return {name:name,qty:qty,price:price,tax:tax,sub:sub};
});
return {
issuerName:  document.getElementById('ig-issuer-name').value,
issuerReg:   document.getElementById('ig-issuer-reg').value,
issuerAddr:  document.getElementById('ig-issuer-addr').value,
issuerEmail: document.getElementById('ig-issuer-email').value,
issuerTel:   document.getElementById('ig-issuer-tel').value,
clientName:  document.getElementById('ig-client-name').value,
clientPerson:document.getElementById('ig-client-person').value,
clientAddr:  document.getElementById('ig-client-addr').value,
invNum:      document.getElementById('ig-inv-num').value,
invDate:     document.getElementById('ig-inv-date').value,
invDue:      document.getElementById('ig-inv-due').value,
bank:        document.getElementById('ig-bank').value,
note:        document.getElementById('ig-note').value,
items:       itemsData,
totals:      totals
};
}

/* ---------- Build preview HTML ---------- */
function buildPreviewHTML(d){
var regHtml = d.issuerReg
? '<div class="ig-reg-num">登録番号：'+esc(d.issuerReg)+'</div>'
: '';

var itemsRows = d.items.map(function(item){
var taxLabel = item.tax==='10' ? '10%' : item.tax==='8' ? '8%※' : '0%';
return '<tr>' +
'<td>'+esc(item.name)+'</td>' +
'<td style="text-align:right;">'+item.qty.toLocaleString('ja-JP')+'</td>' +
'<td style="text-align:right;">'+fmtYen(item.price)+'</td>' +
'<td style="text-align:center;">'+taxLabel+'</td>' +
'<td style="text-align:right;">'+fmtYen(item.sub)+'</td>' +
'</tr>';
}).join('');

var t = d.totals;
var bankHtml = d.bank
? '<div class="ig-preview-bank-title">振込先情報</div><div class="ig-preview-bank">'+esc(d.bank)+'</div>'
: '';
var noteHtml = d.note
? '<div class="ig-preview-note">備考：'+esc(d.note)+'</div>'
: '';

return '<div class="ig-preview">' +
'<div class="ig-preview-top">' +
'<div class="ig-preview-title">請求書</div>' +
'<div class="ig-preview-issuer">' +
'<strong>'+esc(d.issuerName||'（発行者名）')+'</strong>' +
(d.issuerAddr  ? '<div>'+esc(d.issuerAddr)+'</div>'  : '') +
(d.issuerTel   ? '<div>TEL：'+esc(d.issuerTel)+'</div>'   : '') +
(d.issuerEmail ? '<div>'+esc(d.issuerEmail)+'</div>' : '') +
regHtml +
'</div>' +
'</div>' +
'<div class="ig-preview-bill-to">' +
'<div class="ig-bill-name">'+esc(d.clientName||'（請求先）')+'&nbsp;御中</div>' +
(d.clientPerson ? '<div style="font-size:12px;color:#475569;">担当：'+esc(d.clientPerson)+'様</div>' : '') +
(d.clientAddr   ? '<div style="font-size:12px;color:#475569;">'+esc(d.clientAddr)+'</div>' : '') +
'</div>' +
'<div class="ig-preview-meta">' +
'<span class="ig-meta-label">請求書番号</span><span class="ig-meta-value">'+esc(d.invNum)+'</span>' +
'<span class="ig-meta-label">発行日</span><span class="ig-meta-value">'+fmtDate(d.invDate)+'</span>' +
'<span class="ig-meta-label">支払期日</span><span class="ig-meta-value">'+fmtDate(d.invDue)+'</span>' +
'<span class="ig-meta-label">ご請求金額（税込）</span><span class="ig-meta-value" style="color:#0284c7;font-size:15px;">'+fmtYen(t.grand)+'</span>' +
'</div>' +
'<table class="ig-preview-items">' +
'<thead><tr>' +
'<th>品名・説明</th>' +
'<th style="text-align:right;">数量</th>' +
'<th style="text-align:right;">単価</th>' +
'<th>税率</th>' +
'<th style="text-align:right;">小計（税抜）</th>' +
'</tr></thead>' +
'<tbody>'+itemsRows+'</tbody>' +
'</table>' +
'<div class="ig-preview-totals">' +
'<table>' +
'<tr><td>小計（税抜）</td><td>'+fmtYen(t.subtotal)+'</td></tr>' +
(t.base10>0 ? '<tr><td>10%対象額</td><td>'+fmtYen(t.base10)+'</td></tr><tr><td>消費税（10%）</td><td>'+fmtYen(t.tax10)+'</td></tr>' : '') +
(t.base8>0  ? '<tr><td>8%対象額（軽減税率）</td><td>'+fmtYen(t.base8)+'</td></tr><tr><td>消費税（8%）</td><td>'+fmtYen(t.tax8)+'</td></tr>' : '') +
'<tr class="ig-grand"><td>合計（税込）</td><td>'+fmtYen(t.grand)+'</td></tr>' +
'</table>' +
'</div>' +
bankHtml +
noteHtml +
(t.base8>0 ? '<div style="font-size:11px;color:#64748b;margin-top:8px;">※ 軽減税率（8%）対象</div>' : '') +
'</div>';
}

/* ---------- Preview modal ---------- */
window.igShowPreview = function(){
var d = collectData();
document.getElementById('ig-preview-content').innerHTML = buildPreviewHTML(d);
document.getElementById('ig-modal').classList.add('open');
document.body.style.overflow = 'hidden';
};
window.igCloseModal = function(){
document.getElementById('ig-modal').classList.remove('open');
document.body.style.overflow = '';
};
document.getElementById('ig-modal').addEventListener('click', function(e){
if(e.target === this) igCloseModal();
});

/* ---------- Print ---------- */
window.igPrint = function(){
var d = collectData();
var html = buildPreviewHTML(d);
var win = window.open('','_blank','width=820,height=1100');
win.document.write(
'<!DOCTYPE html><html lang="ja"><head><meta charset="utf-8"><title>請求書 - '+
esc(d.invNum)+'</title><style>'+
'body{font-family:system-ui,"Hiragino Sans","Yu Gothic UI","Meiryo",sans-serif;font-size:13px;color:#0f172a;padding:32px 40px;line-height:1.65;}'+
'.ig-preview-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:24px;}'+
'.ig-preview-title{font-size:28px;font-weight:900;color:#0284c7;}'+
'.ig-preview-issuer{text-align:right;font-size:12px;}'+
'.ig-preview-issuer strong{display:block;font-size:15px;font-weight:700;}'+
'.ig-reg-num{display:inline-block;margin-top:4px;border:1px solid #bae6fd;border-radius:4px;padding:2px 8px;font-size:11px;color:#0369a1;font-weight:600;}'+
'.ig-bill-name{font-size:18px;font-weight:700;border-bottom:2px solid #0284c7;display:inline-block;padding-bottom:2px;margin-bottom:4px;}'+
'.ig-preview-meta{display:grid;grid-template-columns:1fr 1fr;gap:6px 20px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:6px;padding:12px 16px;margin:16px 0;font-size:12px;}'+
'.ig-meta-label{color:#64748b;font-weight:600;}.ig-meta-value{font-weight:700;}'+
'table.ig-preview-items{width:100%;border-collapse:collapse;font-size:12px;margin-bottom:16px;}'+
'table.ig-preview-items th{background:#0284c7;color:#fff;font-weight:700;padding:7px 10px;text-align:center;}'+
'table.ig-preview-items th:first-child{text-align:left;}'+
'table.ig-preview-items td{padding:6px 10px;border-bottom:1px solid #e2e8f0;}'+
'table.ig-preview-items tr:nth-child(even) td{background:#f8fafc;}'+
'table.ig-preview-items td:not(:first-child){text-align:right;white-space:nowrap;}'+
'.ig-preview-totals{display:flex;justify-content:flex-end;margin-bottom:16px;}'+
'.ig-preview-totals table{font-size:12px;min-width:260px;}'+
'.ig-preview-totals td{padding:4px 10px;}'+
'.ig-preview-totals td:last-child{text-align:right;font-weight:600;white-space:nowrap;}'+
'.ig-grand td{background:#0284c7;color:#fff;font-size:14px;font-weight:700;padding:8px 12px;}'+
'.ig-preview-bank{background:#f8fafc;border:1px solid #e2e8f0;border-radius:6px;padding:10px 14px;font-size:12px;margin-bottom:14px;white-space:pre-wrap;}'+
'.ig-preview-bank-title{font-weight:700;font-size:12px;color:#0284c7;margin-bottom:4px;}'+
'.ig-preview-note{font-size:12px;color:#475569;background:#fffbeb;border-left:3px solid #fbbf24;padding:8px 12px;}'+
'@media print{@page{margin:15mm;}}'+
'</style></head><body>'+html+'</body></html>'
);
win.document.close();
win.focus();
setTimeout(function(){ win.print(); }, 400);
};

/* ---------- Bootstrap ---------- */
init();
})();
</script>

<!-- ============================================================
freee CTA
============================================================ -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">請求書の発行・管理をもっとラクに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書の自動作成・送付・入金管理まで一元化。インボイス制度にも完全対応。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

</div><!-- /#ig-app -->

---

> 年金をシミュレーション → [年金シミュレーター](/ja/tools/pension-simulator/)

> 手取り額を計算 → [手取り計算ツール](/ja/tools/salary-tedori-calculator/)

> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-planner/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [AI×確定申告 フリーランス完全自動化ガイド2026](/ja/posts/ai-kakuteishinkoku-freelance-2026/)
- [フリーランス確定申告 AIで経費仕訳を自動化する具体的手順](/ja/posts/freelance-kakuteishinkoku-ai-keihi-shiwake/)
- [フリーランスエンジニアの開業届と青色申告｜初年度にやるべき手続き全リスト](/ja/posts/freelance-engineer-kaigyou-aoiro-shinkoku/)
