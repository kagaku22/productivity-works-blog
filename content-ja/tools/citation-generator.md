---
title: "引用文献ジェネレーター"
description: "無料の引用文献作成ツール。APA・MLA・Chicago・Harvard形式の参考文献を自動生成。書籍・論文・Webサイト対応。レポート・論文作成に最適。"
slug: citation-generator
date: 2025-08-04
categories: ["無料ツール"]
tags: ["開発ツール", "ドキュメント", "無料ツール"]
ShowToc: false
cover:
  image: /images/covers/citation-generator-ja.png
  alt: "引用文献ジェネレーター - APA・MLA・Chicago・Harvard形式"
---

APA・MLA・Chicago・Harvard形式の参考文献を自動生成。書籍・雑誌論文・Webサイト・学会論文に対応。レポートや卒論の参考文献リストをかんたんに作成できます。

<div id="cg-app">

<style>
#cg-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Noto Sans JP", sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1e293b;
}
#cg-app * { box-sizing: border-box; }
#cg-app h2 {
font-size: 1.15rem;
font-weight: 700;
margin: 0 0 12px;
color: #0f172a;
}
#cg-app .cg-row {
display: flex;
gap: 12px;
flex-wrap: wrap;
margin-bottom: 14px;
}
#cg-app .cg-field {
display: flex;
flex-direction: column;
gap: 4px;
flex: 1;
min-width: 180px;
}
#cg-app .cg-field label {
font-size: 12px;
font-weight: 600;
color: #475569;
text-transform: uppercase;
letter-spacing: .03em;
}
#cg-app .cg-field input,
#cg-app .cg-field select {
padding: 8px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
color: #1e293b;
background: #fff;
outline: none;
transition: border-color .15s;
width: 100%;
}
#cg-app .cg-field input:focus,
#cg-app .cg-field select:focus {
border-color: #6366f1;
}
#cg-app .cg-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 20px 22px;
margin-bottom: 18px;
}
#cg-app .cg-author-row {
display: flex;
gap: 8px;
align-items: center;
margin-bottom: 8px;
}
#cg-app .cg-author-row input {
flex: 1;
padding: 8px 10px;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
font-size: 14px;
color: #1e293b;
outline: none;
transition: border-color .15s;
}
#cg-app .cg-author-row input:focus { border-color: #6366f1; }
#cg-app .cg-btn {
padding: 8px 16px;
border: none;
border-radius: 7px;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: background .15s, transform .1s;
}
#cg-app .cg-btn:active { transform: scale(.97); }
#cg-app .cg-btn-primary {
background: #6366f1;
color: #fff;
}
#cg-app .cg-btn-primary:hover { background: #4f46e5; }
#cg-app .cg-btn-secondary {
background: #e2e8f0;
color: #334155;
}
#cg-app .cg-btn-secondary:hover { background: #cbd5e1; }
#cg-app .cg-btn-danger {
background: #fee2e2;
color: #dc2626;
padding: 8px 10px;
}
#cg-app .cg-btn-danger:hover { background: #fecaca; }
#cg-app .cg-btn-sm {
padding: 5px 11px;
font-size: 12px;
}
#cg-app .cg-preview-box {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 9px;
padding: 16px 18px;
margin-bottom: 10px;
}
#cg-app .cg-preview-label {
font-size: 11px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .06em;
color: #94a3b8;
margin-bottom: 6px;
}
#cg-app .cg-preview-text {
font-size: 14px;
line-height: 1.7;
color: #1e293b;
white-space: pre-wrap;
word-break: break-word;
}
#cg-app .cg-intext {
font-size: 13px;
color: #64748b;
margin-top: 8px;
padding: 9px 12px;
background: #f1f5f9;
border-radius: 7px;
}
#cg-app .cg-intext strong { color: #0f172a; }
#cg-app .cg-copy-row {
display: flex;
gap: 8px;
flex-wrap: wrap;
margin-top: 10px;
}
#cg-app .cg-toast {
display: inline-block;
font-size: 12px;
color: #16a34a;
font-weight: 600;
opacity: 0;
transition: opacity .3s;
margin-left: 6px;
align-self: center;
}
#cg-app .cg-toast.show { opacity: 1; }
#cg-app .cg-bib-list {
list-style: none;
padding: 0;
margin: 0 0 12px;
}
#cg-app .cg-bib-item {
display: flex;
align-items: flex-start;
gap: 8px;
padding: 10px 0;
border-bottom: 1px solid #e2e8f0;
font-size: 13px;
line-height: 1.6;
color: #1e293b;
word-break: break-word;
}
#cg-app .cg-bib-item:last-child { border-bottom: none; }
#cg-app .cg-bib-num {
font-size: 11px;
font-weight: 700;
color: #94a3b8;
min-width: 22px;
padding-top: 2px;
}
#cg-app .cg-bib-text { flex: 1; }
#cg-app .cg-tabs {
display: flex;
gap: 4px;
margin-bottom: 16px;
border-bottom: 2px solid #e2e8f0;
}
#cg-app .cg-tab {
padding: 8px 16px;
font-size: 13px;
font-weight: 600;
color: #64748b;
border: none;
background: none;
cursor: pointer;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
border-radius: 6px 6px 0 0;
transition: color .15s;
}
#cg-app .cg-tab.active {
color: #6366f1;
border-bottom-color: #6366f1;
}
#cg-app .cg-tab:hover:not(.active) { color: #334155; }
#cg-app .cg-section { margin-bottom: 6px; }
#cg-app .cg-divider {
border: none;
border-top: 1.5px solid #e2e8f0;
margin: 18px 0;
}
#cg-app .cg-empty {
color: #94a3b8;
font-size: 13px;
text-align: center;
padding: 18px 0;
}
@media (max-width: 600px) {
#cg-app .cg-row { flex-direction: column; }
#cg-app .cg-field { min-width: 100%; }
}
</style>

<div class="cg-card">
<div class="cg-tabs">
<button class="cg-tab active" data-tab="generator">引用文献を作成</button>
<button class="cg-tab" data-tab="bibliography">参考文献リスト</button>
</div>

<!-- 作成タブ -->
<div id="cg-tab-generator">
<div class="cg-row">
<div class="cg-field">
<label>資料の種類</label>
<select id="cg-source-type">
<option value="book">書籍</option>
<option value="journal">雑誌論文</option>
<option value="website">Webサイト</option>
<option value="conference">学会論文</option>
</select>
</div>
<div class="cg-field">
<label>引用スタイル</label>
<select id="cg-style">
<option value="apa7">APA 第7版</option>
<option value="mla9">MLA 第9版</option>
<option value="chicago17">Chicago 第17版</option>
<option value="harvard">Harvard</option>
</select>
</div>
</div>

<!-- 著者 -->
<div class="cg-section">
<label style="font-size:12px;font-weight:600;color:#475569;text-transform:uppercase;letter-spacing:.03em;">著者</label>
<div id="cg-authors" style="margin-top:6px;"></div>
<button class="cg-btn cg-btn-secondary cg-btn-sm" id="cg-add-author" style="margin-top:6px;">+ 著者を追加</button>
</div>

<hr class="cg-divider">

<!-- 基本情報 -->
<div class="cg-row">
<div class="cg-field">
<label>タイトル</label>
<input type="text" id="cg-title" placeholder="論文・書籍のタイトル">
</div>
<div class="cg-field">
<label>出版年</label>
<input type="text" id="cg-year" placeholder="2024" maxlength="4" style="max-width:120px;">
</div>
</div>

<div class="cg-row">
<div class="cg-field" id="cg-field-publisher">
<label>出版社</label>
<input type="text" id="cg-publisher" placeholder="出版社名">
</div>
<div class="cg-field" id="cg-field-place">
<label>出版地</label>
<input type="text" id="cg-place" placeholder="東京">
</div>
</div>

<div class="cg-row" id="cg-row-journal">
<div class="cg-field">
<label>雑誌名</label>
<input type="text" id="cg-journal" placeholder="Nature, Science など">
</div>
<div class="cg-field" style="max-width:100px;">
<label>巻 (Volume)</label>
<input type="text" id="cg-volume" placeholder="12">
</div>
<div class="cg-field" style="max-width:100px;">
<label>号 (Issue)</label>
<input type="text" id="cg-issue" placeholder="3">
</div>
<div class="cg-field" style="max-width:130px;">
<label>ページ</label>
<input type="text" id="cg-pages" placeholder="45–67">
</div>
</div>

<div class="cg-row" id="cg-row-conference">
<div class="cg-field">
<label>学会名</label>
<input type="text" id="cg-conference" placeholder="Proceedings of ...">
</div>
<div class="cg-field">
<label>開催地</label>
<input type="text" id="cg-conf-location" placeholder="大阪">
</div>
</div>

<div class="cg-row">
<div class="cg-field">
<label>DOI</label>
<input type="text" id="cg-doi" placeholder="10.1000/xyz123">
</div>
<div class="cg-field" id="cg-field-url">
<label>URL</label>
<input type="text" id="cg-url" placeholder="https://example.com">
</div>
</div>

<div class="cg-row" id="cg-row-access">
<div class="cg-field">
<label>アクセス日</label>
<input type="text" id="cg-access-date" placeholder="2025年5月16日">
</div>
<div class="cg-field">
<label>サイト名</label>
<input type="text" id="cg-site-name" placeholder="NHK News Web">
</div>
</div>

<hr class="cg-divider">

<!-- プレビュー -->
<h2>引用文献プレビュー</h2>
<div class="cg-preview-box">
<div class="cg-preview-label">参考文献リスト</div>
<div class="cg-preview-text" id="cg-preview-ref">上のフィールドを入力すると引用文献が生成されます。</div>
</div>
<div class="cg-intext" id="cg-preview-intext" style="display:none;">
<strong>本文中引用：</strong> <span id="cg-intext-text"></span>
</div>

<div class="cg-copy-row">
<button class="cg-btn cg-btn-primary" id="cg-copy-ref">参考文献をコピー</button>
<button class="cg-btn cg-btn-secondary" id="cg-copy-intext">本文引用をコピー</button>
<button class="cg-btn cg-btn-secondary" id="cg-add-to-bib">リストに追加</button>
<span class="cg-toast" id="cg-toast"></span>
</div>
</div>

<!-- 参考文献リストタブ -->
<div id="cg-tab-bibliography" style="display:none;">
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;flex-wrap:wrap;gap:8px;">
<h2 style="margin:0;">参考文献リスト</h2>
<div style="display:flex;gap:8px;flex-wrap:wrap;">
<button class="cg-btn cg-btn-secondary cg-btn-sm" id="cg-sort-alpha">50音順に並べ替え</button>
<button class="cg-btn cg-btn-secondary cg-btn-sm" id="cg-export-txt">テキストで書き出し</button>
<button class="cg-btn cg-btn-danger cg-btn-sm" id="cg-clear-bib">すべて削除</button>
</div>
</div>
<ul class="cg-bib-list" id="cg-bib-list">
<li class="cg-empty" id="cg-bib-empty">まだ引用文献がありません。「リストに追加」で追加してください。</li>
</ul>
</div>

<div class="cg-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">研究費・学会費の管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、研究費用・書籍購入費の経費管理もクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>
</div>

<script>
(function() {
'use strict';

// ── State ──
var authors = [{ first: '', last: '' }];
var bibItems = [];

// ── DOM refs ──
var sourceTypeEl = document.getElementById('cg-source-type');
var styleEl = document.getElementById('cg-style');
var titleEl = document.getElementById('cg-title');
var yearEl = document.getElementById('cg-year');
var publisherEl = document.getElementById('cg-publisher');
var placeEl = document.getElementById('cg-place');
var journalEl = document.getElementById('cg-journal');
var volumeEl = document.getElementById('cg-volume');
var issueEl = document.getElementById('cg-issue');
var pagesEl = document.getElementById('cg-pages');
var doiEl = document.getElementById('cg-doi');
var urlEl = document.getElementById('cg-url');
var accessEl = document.getElementById('cg-access-date');
var siteNameEl = document.getElementById('cg-site-name');
var conferenceEl = document.getElementById('cg-conference');
var confLocEl = document.getElementById('cg-conf-location');
var authorsContainer = document.getElementById('cg-authors');
var previewRef = document.getElementById('cg-preview-ref');
var previewIntextEl = document.getElementById('cg-preview-intext');
var intextText = document.getElementById('cg-intext-text');
var toast = document.getElementById('cg-toast');
var bibList = document.getElementById('cg-bib-list');

// ── Helpers ──
function v(el) { return el ? el.value.trim() : ''; }
function italic(text) { return '_' + text + '_'; }

function formatAuthorsAPA(auths) {
if (!auths.length) return '';
return auths.map(function(a) {
var last = a.last || a.first || '著者不明';
var first = a.last ? a.first : '';
if (!first) return last;
var initials = first.split(/\s+/).map(function(n) { return n[0].toUpperCase() + '.'; }).join(' ');
return last + ', ' + initials;
}).join(', ');
}

function formatAuthorsMLA(auths) {
if (!auths.length) return '';
if (auths.length === 1) {
var a = auths[0];
return (a.last && a.first) ? a.last + ', ' + a.first : (a.last || a.first || '著者不明');
}
var first = auths[0];
var firstStr = (first.last && first.first) ? first.last + ', ' + first.first : (first.last || first.first || '著者不明');
if (auths.length === 2) {
var s = auths[1];
return firstStr + ', and ' + ((s.first ? s.first + ' ' : '') + (s.last || ''));
}
return firstStr + ', et al.';
}

function formatAuthorsChicago(auths) {
if (!auths.length) return '';
if (auths.length === 1) {
var a = auths[0];
return (a.last && a.first) ? a.last + ', ' + a.first : (a.last || a.first || '著者不明');
}
var first = auths[0];
var firstStr = (first.last && first.first) ? first.last + ', ' + first.first : (first.last || first.first || '著者不明');
var rest = auths.slice(1).map(function(a) { return (a.first ? a.first + ' ' : '') + (a.last || ''); });
return firstStr + ', and ' + rest.join(', and ');
}

function formatAuthorsHarvard(auths) {
if (!auths.length) return '';
return auths.map(function(a) {
var last = a.last || a.first || '著者不明';
var first = a.last ? a.first : '';
var initials = first ? first.split(/\s+/).map(function(n) { return n[0].toUpperCase() + '.'; }).join('') : '';
return last + (initials ? ', ' + initials : '');
}).join(', ');
}

function intextAPA(auths, year) {
var name = auths.length ? (auths[0].last || auths[0].first || '著者') : '著者';
var suffix = auths.length > 2 ? ' et al.' : (auths.length === 2 ? ' & ' + (auths[1].last || auths[1].first || '') : '');
return '(' + name + suffix + ', ' + (year || 'n.d.') + ')';
}
function intextMLA(auths) {
var name = auths.length ? (auths[0].last || auths[0].first || '著者') : '著者';
return '(' + name + ')';
}
function intextChicago(auths, year) {
var names = auths.slice(0, 3).map(function(a) { return a.last || a.first || '著者'; });
if (auths.length > 3) names.push('et al.');
return '(' + names.join(', ') + ' ' + (year || 'n.d.') + ')';
}
function intextHarvard(auths, year) {
var name = auths.length ? (auths[0].last || auths[0].first || '著者') : '著者';
var suffix = auths.length > 2 ? ' et al.' : (auths.length === 2 ? ' and ' + (auths[1].last || auths[1].first || '') : '');
return '(' + name + suffix + ', ' + (year || 'n.d.') + ')';
}

// ── Citation Builders ──
function buildAPA7(data) {
var a = formatAuthorsAPA(data.authors);
var yr = data.year ? '(' + data.year + ').' : '(n.d.).';
var doi = data.doi ? ' https://doi.org/' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') : '';
var url = !data.doi && data.url ? ' ' + data.url : '';
if (data.type === 'book') {
return (a ? a + ' ' : '') + yr + ' ' + italic(data.title || '無題') + '.' + (data.publisher ? ' ' + data.publisher + '.' : '') + doi + url;
}
if (data.type === 'journal') {
var vol = data.volume ? ', ' + italic(data.volume) : '';
var iss = data.issue ? '(' + data.issue + ')' : '';
var pg = data.pages ? ', ' + data.pages : '';
return (a ? a + ' ' : '') + yr + ' ' + (data.title || '無題') + '. ' + italic(data.journal || '雑誌名') + vol + iss + pg + '.' + doi + url;
}
if (data.type === 'website') {
var site = data.siteName ? data.siteName + '. ' : '';
var acc = data.accessDate ? ' Retrieved ' + data.accessDate + ', from' : '';
return (a ? a + ' ' : '') + yr + ' ' + italic(data.title || '無題') + '. ' + site + acc + (data.url ? ' ' + data.url : '');
}
if (data.type === 'conference') {
var pg2 = data.pages ? ', ' + data.pages : '';
return (a ? a + ' ' : '') + yr + ' ' + (data.title || '無題') + '. In ' + italic(data.conference || '学会名') + pg2 + '.' + doi + url;
}
return '';
}

function buildMLA9(data) {
var a = formatAuthorsMLA(data.authors);
if (data.type === 'book') {
return (a ? a + '. ' : '') + italic(data.title || '無題') + '. ' + (data.publisher || '') + ', ' + (data.year || 'n.d.') + '.';
}
if (data.type === 'journal') {
var vol = data.volume ? 'vol. ' + data.volume + ', ' : '';
var iss = data.issue ? 'no. ' + data.issue + ', ' : '';
var pg = data.pages ? 'pp. ' + data.pages + ', ' : '';
var doi = data.doi ? 'https://doi.org/' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') + '.' : (data.url ? data.url + '.' : '');
return (a ? a + '. ' : '') + '"' + (data.title || '無題') + '." ' + italic(data.journal || '雑誌名') + ', ' + vol + iss + (data.year || 'n.d.') + ', ' + pg + doi;
}
if (data.type === 'website') {
var acc = data.accessDate ? ' Accessed ' + data.accessDate + '.' : '';
return (a ? a + '. ' : '') + '"' + (data.title || '無題') + '." ' + (data.siteName ? italic(data.siteName) + ', ' : '') + (data.year || 'n.d.') + ', ' + (data.url || '') + '.' + acc;
}
if (data.type === 'conference') {
return (a ? a + '. ' : '') + '"' + (data.title || '無題') + '." ' + italic(data.conference || '学会名') + ', ' + (data.year || 'n.d.') + (data.pages ? ', pp. ' + data.pages : '') + '.';
}
return '';
}

function buildChicago17(data) {
var a = formatAuthorsChicago(data.authors);
if (data.type === 'book') {
return (a ? a + '. ' : '') + italic(data.title || '無題') + '. ' + (data.place ? data.place + ': ' : '') + (data.publisher || '') + ', ' + (data.year || 'n.d.') + '.';
}
if (data.type === 'journal') {
var vol = data.volume || '';
var iss = data.issue ? ', no. ' + data.issue : '';
var yr = data.year ? ' (' + data.year + ')' : '';
var pg = data.pages ? ': ' + data.pages : '';
var doi = data.doi ? ' https://doi.org/' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') : (data.url ? ' ' + data.url : '');
return (a ? a + '. ' : '') + '"' + (data.title || '無題') + '." ' + italic(data.journal || '雑誌名') + ' ' + vol + iss + yr + pg + '.' + doi;
}
if (data.type === 'website') {
var acc = data.accessDate ? ' Accessed ' + data.accessDate + '.' : '';
return (a ? a + '. ' : '') + '"' + (data.title || '無題') + '." ' + (data.siteName ? data.siteName + '. ' : '') + (data.year || 'n.d.') + '.' + (data.url ? ' ' + data.url + '.' : '') + acc;
}
if (data.type === 'conference') {
return (a ? a + '. ' : '') + '"' + (data.title || '無題') + '." Paper presented at ' + (data.conference || '学会名') + ', ' + (data.confLocation || '') + ', ' + (data.year || 'n.d.') + '.';
}
return '';
}

function buildHarvard(data) {
var a = formatAuthorsHarvard(data.authors);
var yr = data.year || 'n.d.';
if (data.type === 'book') {
return (a ? a + ' ' : '') + '(' + yr + ') ' + italic(data.title || '無題') + '. ' + (data.place ? data.place + ': ' : '') + (data.publisher || '') + '.';
}
if (data.type === 'journal') {
var vol = data.volume || '';
var iss = data.issue ? '(' + data.issue + ')' : '';
var pg = data.pages ? ', pp.' + data.pages : '';
var doi = data.doi ? ' doi:' + data.doi.replace(/^https?:\/\/doi\.org\//i,'') : (data.url ? ' Available at: ' + data.url : '');
return (a ? a + ' ' : '') + '(' + yr + ') "' + (data.title || '無題') + '", ' + italic(data.journal || '雑誌名') + ', ' + vol + iss + pg + '.' + doi;
}
if (data.type === 'website') {
var acc = data.accessDate ? ' [Accessed: ' + data.accessDate + ']' : '';
return (a ? a + ' ' : '') + '(' + yr + ') ' + italic(data.title || '無題') + '. ' + (data.siteName ? data.siteName + '.' : '') + (data.url ? ' Available at: ' + data.url + '.' : '') + acc;
}
if (data.type === 'conference') {
var pg2 = data.pages ? ', pp.' + data.pages : '';
return (a ? a + ' ' : '') + '(' + yr + ') "' + (data.title || '無題') + '", ' + italic(data.conference || '学会名') + pg2 + '.';
}
return '';
}

function getCitationData() {
return {
type: v(sourceTypeEl),
authors: authors.filter(function(a) { return a.first || a.last; }),
title: v(titleEl),
year: v(yearEl),
publisher: v(publisherEl),
place: v(placeEl),
journal: v(journalEl),
volume: v(volumeEl),
issue: v(issueEl),
pages: v(pagesEl),
doi: v(doiEl),
url: v(urlEl),
accessDate: v(accessEl),
siteName: v(siteNameEl),
conference: v(conferenceEl),
confLocation: v(confLocEl)
};
}

function buildCitation(data) {
var style = v(styleEl);
if (style === 'apa7') return buildAPA7(data);
if (style === 'mla9') return buildMLA9(data);
if (style === 'chicago17') return buildChicago17(data);
if (style === 'harvard') return buildHarvard(data);
return '';
}

function buildIntext(data) {
var style = v(styleEl);
var auths = data.authors;
if (style === 'apa7') return intextAPA(auths, data.year);
if (style === 'mla9') return intextMLA(auths);
if (style === 'chicago17') return intextChicago(auths, data.year);
if (style === 'harvard') return intextHarvard(auths, data.year);
return '';
}

function renderForDisplay(text) {
return text.replace(/_([^_]+)_/g, '<em>$1</em>');
}
function renderForCopy(text) {
return text.replace(/_([^_]+)_/g, '$1');
}

// ── Field visibility ──
function updateFieldVisibility() {
var type = v(sourceTypeEl);
var isJournal = type === 'journal';
var isWebsite = type === 'website';
var isConference = type === 'conference';
var isBook = type === 'book';

document.getElementById('cg-row-journal').style.display = (isJournal || isConference) ? 'flex' : 'none';
if (isConference) {
journalEl.closest('.cg-field').style.display = 'none';
} else {
journalEl.closest('.cg-field').style.display = '';
}
document.getElementById('cg-row-conference').style.display = isConference ? 'flex' : 'none';
document.getElementById('cg-row-access').style.display = isWebsite ? 'flex' : 'none';
document.getElementById('cg-field-url').style.display = isWebsite ? '' : 'flex';
document.getElementById('cg-field-publisher').style.display = (isBook || isConference || isJournal) ? '' : 'none';
document.getElementById('cg-field-place').style.display = isBook ? '' : 'none';
}

// ── Render authors ──
function escAttr(s) { return (s || '').replace(/"/g, '&quot;'); }

function renderAuthors() {
authorsContainer.innerHTML = '';
authors.forEach(function(a, i) {
var row = document.createElement('div');
row.className = 'cg-author-row';
row.innerHTML =
'<input type="text" placeholder="姓（ファミリーネーム）" value="' + escAttr(a.last) + '" data-i="' + i + '" data-field="last">' +
'<input type="text" placeholder="名（ファーストネーム）" value="' + escAttr(a.first) + '" data-i="' + i + '" data-field="first">' +
(authors.length > 1 ? '<button class="cg-btn cg-btn-danger cg-btn-sm cg-remove-author" data-i="' + i + '">✕</button>' : '');
authorsContainer.appendChild(row);
});
authorsContainer.querySelectorAll('input').forEach(function(inp) {
inp.addEventListener('input', function() {
authors[+this.dataset.i][this.dataset.field] = this.value;
updatePreview();
});
});
authorsContainer.querySelectorAll('.cg-remove-author').forEach(function(btn) {
btn.addEventListener('click', function() {
authors.splice(+this.dataset.i, 1);
renderAuthors();
updatePreview();
});
});
}

// ── Preview ──
function updatePreview() {
var data = getCitationData();
var ref = buildCitation(data);
var intext = buildIntext(data);
if (ref) {
previewRef.innerHTML = renderForDisplay(ref);
previewIntextEl.style.display = '';
intextText.textContent = renderForCopy(intext);
} else {
previewRef.textContent = '上のフィールドを入力すると引用文献が生成されます。';
previewIntextEl.style.display = 'none';
}
}

// ── Toast ──
var toastTimer;
function showToast(msg) {
toast.textContent = msg;
toast.classList.add('show');
clearTimeout(toastTimer);
toastTimer = setTimeout(function() { toast.classList.remove('show'); }, 2000);
}

// ── Copy ──
function copyText(text) {
if (navigator.clipboard) {
navigator.clipboard.writeText(text).catch(function() { fallbackCopy(text); });
} else { fallbackCopy(text); }
}
function fallbackCopy(text) {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
}

// ── Bibliography ──
function renderBib() {
if (!bibItems.length) {
bibList.innerHTML = '<li class="cg-empty">まだ引用文献がありません。「リストに追加」で追加してください。</li>';
return;
}
var html = '';
bibItems.forEach(function(item, i) {
html += '<li class="cg-bib-item"><span class="cg-bib-num">' + (i+1) + '.</span><span class="cg-bib-text">' + renderForDisplay(item) + '</span>' +
'<button class="cg-btn cg-btn-danger cg-btn-sm cg-remove-bib" data-i="' + i + '" style="flex-shrink:0;">✕</button></li>';
});
bibList.innerHTML = html;
bibList.querySelectorAll('.cg-remove-bib').forEach(function(btn) {
btn.addEventListener('click', function() {
bibItems.splice(+this.dataset.i, 1);
renderBib();
});
});
}

// ── Tabs ──
document.querySelectorAll('#cg-app .cg-tab').forEach(function(tab) {
tab.addEventListener('click', function() {
document.querySelectorAll('#cg-app .cg-tab').forEach(function(t) { t.classList.remove('active'); });
this.classList.add('active');
var name = this.dataset.tab;
document.getElementById('cg-tab-generator').style.display = name === 'generator' ? '' : 'none';
document.getElementById('cg-tab-bibliography').style.display = name === 'bibliography' ? '' : 'none';
});
});

// ── Event listeners ──
sourceTypeEl.addEventListener('change', function() { updateFieldVisibility(); updatePreview(); });
styleEl.addEventListener('change', updatePreview);
[titleEl, yearEl, publisherEl, placeEl, journalEl, volumeEl, issueEl, pagesEl, doiEl, urlEl, accessEl, siteNameEl, conferenceEl, confLocEl].forEach(function(el) {
if (el) el.addEventListener('input', updatePreview);
});

document.getElementById('cg-add-author').addEventListener('click', function() {
authors.push({ first: '', last: '' });
renderAuthors();
});

document.getElementById('cg-copy-ref').addEventListener('click', function() {
var data = getCitationData();
var ref = renderForCopy(buildCitation(data));
if (!ref) { showToast('コピーできる内容がありません'); return; }
copyText(ref);
showToast('コピーしました！');
});

document.getElementById('cg-copy-intext').addEventListener('click', function() {
var data = getCitationData();
var it = buildIntext(data);
if (!it) { showToast('コピーできる内容がありません'); return; }
copyText(it);
showToast('本文引用をコピーしました！');
});

document.getElementById('cg-add-to-bib').addEventListener('click', function() {
var data = getCitationData();
var ref = buildCitation(data);
if (!ref) { showToast('先に引用文献を生成してください'); return; }
bibItems.push(ref);
renderBib();
showToast('リストに追加しました！');
});

document.getElementById('cg-sort-alpha').addEventListener('click', function() {
bibItems.sort(function(a, b) { return renderForCopy(a).localeCompare(renderForCopy(b), 'ja'); });
renderBib();
showToast('並べ替え完了！');
});

document.getElementById('cg-export-txt').addEventListener('click', function() {
if (!bibItems.length) { showToast('参考文献リストが空です'); return; }
var text = bibItems.map(function(item, i) { return (i+1) + '. ' + renderForCopy(item); }).join('\n\n');
var blob = new Blob([text], { type: 'text/plain' });
var a = document.createElement('a');
a.href = URL.createObjectURL(blob);
a.download = 'bibliography.txt';
a.click();
URL.revokeObjectURL(a.href);
});

document.getElementById('cg-clear-bib').addEventListener('click', function() {
if (bibItems.length && confirm('参考文献リストをすべて削除しますか？')) {
bibItems = [];
renderBib();
}
});

// ── Init ──
renderAuthors();
updateFieldVisibility();
updatePreview();
})();
</script>

</div>

---

**関連ツール：**

- 文字数カウント → [文字数カウンター](/ja/tools/word-counter/)
- 読了時間を計算 → [読了時間計算ツール](/ja/tools/reading-time-calculator/)

---

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
