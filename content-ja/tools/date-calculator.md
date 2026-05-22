---
title: "日付計算ツール"
slug: "date-calculator"
description: "無料の日付計算ツール。2つの日付間の差、日付への日数加減算、営業日計算に対応。"
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
date: 2025-10-31
ShowToc: false
cover:
  image: "/images/covers/date-calculator-ja.png"
---

無料のオンライン日付計算ツールです。2つの日付の差を計算、日付への日数加減算、営業日カウントの3モードに対応しています。登録不要・広告なしで即座に利用できます。

<div id="dt-app">
<style>
#dt-app {
font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Yu Gothic", sans-serif;
max-width: 700px;
margin: 0 auto;
color: #1a1a2e;
}
#dt-app * {
box-sizing: border-box;
}
#dt-app .dt-tabs {
display: flex;
gap: 0;
border-bottom: 2px solid #e0e0e0;
margin-bottom: 24px;
}
#dt-app .dt-tab {
flex: 1;
padding: 12px 8px;
background: none;
border: none;
border-bottom: 3px solid transparent;
margin-bottom: -2px;
font-size: 14px;
font-weight: 700;
color: #777;
cursor: pointer;
transition: all 0.2s;
text-align: center;
}
#dt-app .dt-tab:hover {
color: #4f46e5;
background: #f5f3ff;
}
#dt-app .dt-tab.active {
color: #4f46e5;
border-bottom-color: #4f46e5;
background: none;
}
#dt-app .dt-panel {
display: none;
}
#dt-app .dt-panel.active {
display: block;
}
#dt-app .dt-card {
background: #f9f9ff;
border: 1px solid #e8e8f0;
border-radius: 12px;
padding: 24px;
margin-bottom: 20px;
}
#dt-app .dt-row {
display: flex;
gap: 16px;
flex-wrap: wrap;
margin-bottom: 16px;
align-items: flex-end;
}
#dt-app .dt-field {
display: flex;
flex-direction: column;
gap: 6px;
flex: 1;
min-width: 160px;
}
#dt-app .dt-field label {
font-size: 13px;
font-weight: 700;
color: #555;
}
#dt-app .dt-field input,
#dt-app .dt-field select {
padding: 10px 12px;
border: 1.5px solid #d0d0e0;
border-radius: 8px;
font-size: 15px;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.2s;
width: 100%;
}
#dt-app .dt-field input:focus,
#dt-app .dt-field select:focus {
border-color: #4f46e5;
}
#dt-app .dt-btn {
display: inline-block;
padding: 11px 28px;
background: #4f46e5;
color: #fff;
border: none;
border-radius: 8px;
font-size: 15px;
font-weight: 700;
cursor: pointer;
transition: background 0.2s;
}
#dt-app .dt-btn:hover {
background: #4338ca;
}
#dt-app .dt-result {
background: #fff;
border: 1.5px solid #4f46e5;
border-radius: 10px;
padding: 20px 24px;
margin-top: 16px;
display: none;
}
#dt-app .dt-result.show {
display: block;
}
#dt-app .dt-result-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
gap: 12px;
margin-bottom: 12px;
}
#dt-app .dt-result-item {
background: #f5f3ff;
border-radius: 8px;
padding: 14px 12px;
text-align: center;
}
#dt-app .dt-result-item .val {
font-size: 26px;
font-weight: 800;
color: #4f46e5;
line-height: 1.1;
}
#dt-app .dt-result-item .lbl {
font-size: 12px;
color: #666;
margin-top: 4px;
}
#dt-app .dt-result-main {
font-size: 16px;
font-weight: 700;
color: #1a1a2e;
margin-bottom: 8px;
}
#dt-app .dt-result-sub {
font-size: 14px;
color: #555;
line-height: 1.8;
}
#dt-app .dt-dow-badge {
display: inline-block;
background: #e0f2fe;
color: #0369a1;
border-radius: 6px;
padding: 3px 10px;
font-size: 13px;
font-weight: 700;
margin-left: 6px;
}
#dt-app .dt-error {
color: #dc2626;
font-size: 14px;
margin-top: 10px;
display: none;
}
#dt-app .dt-error.show {
display: block;
}
#dt-app .dt-op-toggle {
display: flex;
gap: 0;
border: 1.5px solid #d0d0e0;
border-radius: 8px;
overflow: hidden;
background: #fff;
}
#dt-app .dt-op-btn {
flex: 1;
padding: 10px;
background: none;
border: none;
font-size: 14px;
font-weight: 700;
color: #777;
cursor: pointer;
transition: all 0.2s;
}
#dt-app .dt-op-btn.active {
background: #4f46e5;
color: #fff;
}
#dt-app .dt-cta {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
border-radius: 12px;
padding: 24px;
margin-top: 32px;
color: #fff;
}
#dt-app .dt-cta h3 {
margin: 0 0 8px;
font-size: 18px;
font-weight: 800;
}
#dt-app .dt-cta p {
margin: 0 0 16px;
font-size: 14px;
opacity: 0.92;
line-height: 1.6;
}
#dt-app .dt-cta-btn {
display: inline-block;
padding: 11px 24px;
background: #fff;
color: #4f46e5;
border-radius: 8px;
font-size: 14px;
font-weight: 800;
text-decoration: none;
transition: opacity 0.2s;
}
#dt-app .dt-cta-btn:hover {
opacity: 0.9;
}
#dt-app .dt-related {
margin-top: 32px;
padding-top: 24px;
border-top: 1px solid #e0e0e0;
}
#dt-app .dt-related h3 {
font-size: 16px;
font-weight: 700;
margin: 0 0 14px;
color: #1a1a2e;
}
#dt-app .dt-related-links {
display: flex;
gap: 12px;
flex-wrap: wrap;
}
#dt-app .dt-related-link {
display: inline-block;
padding: 9px 18px;
background: #f5f3ff;
border: 1.5px solid #c7d2fe;
border-radius: 8px;
color: #4f46e5;
font-size: 14px;
font-weight: 700;
text-decoration: none;
transition: background 0.2s;
}
#dt-app .dt-related-link:hover {
background: #ede9fe;
}
#dt-app .dt-hint {
font-size: 13px;
color: #888;
margin-top: 10px;
}
@media (max-width: 500px) {
#dt-app .dt-tab { font-size: 12px; padding: 10px 4px; }
#dt-app .dt-result-item .val { font-size: 20px; }
#dt-app .dt-cta h3 { font-size: 16px; }
}
</style>

<!-- タブナビゲーション -->
<div class="dt-tabs">
<button class="dt-tab active" onclick="dtSwitchTab(0, this)">日付の差</button>
<button class="dt-tab" onclick="dtSwitchTab(1, this)">日数の加減算</button>
<button class="dt-tab" onclick="dtSwitchTab(2, this)">営業日計算</button>
</div>

<!-- パネル0: 日付の差 -->
<div class="dt-panel active" id="dt-panel-0">
<div class="dt-card">
<div class="dt-row">
<div class="dt-field">
<label>開始日</label>
<input type="date" id="dd-start" />
</div>
<div class="dt-field">
<label>終了日</label>
<input type="date" id="dd-end" />
</div>
</div>
<button class="dt-btn" onclick="dtCalcDiff()">差を計算する</button>
<div class="dt-error" id="dd-error">開始日と終了日を両方入力してください。</div>
</div>
<div class="dt-result" id="dd-result">
<div class="dt-result-main" id="dd-main"></div>
<div class="dt-result-grid" id="dd-grid"></div>
<div class="dt-result-sub" id="dd-sub"></div>
</div>
</div>

<!-- パネル1: 日数の加減算 -->
<div class="dt-panel" id="dt-panel-1">
<div class="dt-card">
<div class="dt-row">
<div class="dt-field">
<label>基準日</label>
<input type="date" id="as-date" />
</div>
</div>
<div class="dt-row">
<div class="dt-field" style="max-width:100px;">
<label>数値</label>
<input type="number" id="as-amount" value="30" min="0" max="9999" />
</div>
<div class="dt-field" style="max-width:160px;">
<label>単位</label>
<select id="as-unit">
<option value="days">日</option>
<option value="weeks">週</option>
<option value="months">ヶ月</option>
<option value="years">年</option>
</select>
</div>
<div class="dt-field" style="max-width:180px;">
<label>演算</label>
<div class="dt-op-toggle">
<button class="dt-op-btn active" id="as-add-btn" onclick="dtSetOp('add')">＋ 加算</button>
<button class="dt-op-btn" id="as-sub-btn" onclick="dtSetOp('sub')">－ 減算</button>
</div>
</div>
</div>
<button class="dt-btn" onclick="dtCalcAddSub()">日付を計算する</button>
<div class="dt-error" id="as-error">基準日と数値を入力してください。</div>
</div>
<div class="dt-result" id="as-result">
<div class="dt-result-main" id="as-main"></div>
<div class="dt-result-sub" id="as-sub"></div>
</div>
</div>

<!-- パネル2: 営業日計算 -->
<div class="dt-panel" id="dt-panel-2">
<div class="dt-card">
<div class="dt-row">
<div class="dt-field">
<label>開始日</label>
<input type="date" id="bd-start" />
</div>
<div class="dt-field">
<label>終了日</label>
<input type="date" id="bd-end" />
</div>
</div>
<p class="dt-hint">土曜日・日曜日を除外します。祝日は自動除外されません。</p>
<button class="dt-btn" onclick="dtCalcBiz()">営業日を計算する</button>
<div class="dt-error" id="bd-error">開始日と終了日を両方入力してください。</div>
</div>
<div class="dt-result" id="bd-result">
<div class="dt-result-main" id="bd-main"></div>
<div class="dt-result-grid" id="bd-grid"></div>
<div class="dt-result-sub" id="bd-sub"></div>
</div>
</div>

<!-- freee CTA -->
<div class="dt-cta">
<h3>請求書・経費管理をもっとラクに</h3>
<p>freee会計なら日付入力・締め日管理・営業日ベースの支払サイクル設定がすべて自動化。個人事業主から法人まで無料トライアルで試せます。</p>
<a class="dt-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener sponsored">freeeを無料で試す &rarr;</a>
</div>

<!-- 関連ツール -->
<div class="dt-related">
<h3>関連する無料ツール</h3>
<div class="dt-related-links">
<a class="dt-related-link" href="/ja/tools/age-calculator/">年齢計算ツール</a>
<a class="dt-related-link" href="/ja/tools/calendar-generator/">カレンダー生成ツール</a>
</div>
</div>

<script>
(function() {
var _op = 'add';
var DAYS_JA = ['日曜日','月曜日','火曜日','水曜日','木曜日','金曜日','土曜日'];
var DAYS_JA_SHORT = ['日','月','火','水','木','金','土'];

var today = new Date();
var todayStr = dtFmtISO(today);
document.getElementById('dd-start').value = todayStr;
document.getElementById('dd-end').value = todayStr;
document.getElementById('as-date').value = todayStr;
document.getElementById('bd-start').value = todayStr;
document.getElementById('bd-end').value = todayStr;

function dtFmtISO(d) {
var y = d.getFullYear();
var m = String(d.getMonth()+1).padStart(2,'0');
var day = String(d.getDate()).padStart(2,'0');
return y+'-'+m+'-'+day;
}

function dtFmtDisplay(d) {
return d.getFullYear()+'年'+(d.getMonth()+1)+'月'+d.getDate()+'日（'+DAYS_JA_SHORT[d.getDay()]+'）';
}

function dtParseDate(str) {
if (!str) return null;
var p = str.split('-');
if (p.length !== 3) return null;
return new Date(+p[0], +p[1]-1, +p[2]);
}

window.dtSwitchTab = function(idx, btn) {
var tabs = document.querySelectorAll('#dt-app .dt-tab');
var panels = document.querySelectorAll('#dt-app .dt-panel');
tabs.forEach(function(t){ t.classList.remove('active'); });
panels.forEach(function(p){ p.classList.remove('active'); });
btn.classList.add('active');
document.getElementById('dt-panel-'+idx).classList.add('active');
};

window.dtSetOp = function(op) {
_op = op;
document.getElementById('as-add-btn').classList.toggle('active', op==='add');
document.getElementById('as-sub-btn').classList.toggle('active', op==='sub');
};

window.dtCalcDiff = function() {
var err = document.getElementById('dd-error');
var res = document.getElementById('dd-result');
err.classList.remove('show');
res.classList.remove('show');

var s = dtParseDate(document.getElementById('dd-start').value);
var e = dtParseDate(document.getElementById('dd-end').value);
if (!s || !e) { err.classList.add('show'); return; }

var sign = 1;
if (e < s) { sign = -1; var tmp = s; s = e; e = tmp; }

var msPerDay = 86400000;
var totalDays = Math.round((e - s) / msPerDay);
var totalHours = totalDays * 24;
var totalWeeks = Math.floor(totalDays / 7);
var remDays = totalDays % 7;

var y = e.getFullYear() - s.getFullYear();
var mo = e.getMonth() - s.getMonth();
var da = e.getDate() - s.getDate();
if (da < 0) {
mo--;
var prev = new Date(e.getFullYear(), e.getMonth(), 0);
da += prev.getDate();
}
if (mo < 0) { y--; mo += 12; }

var s0 = dtParseDate(document.getElementById('dd-start').value);
var e0 = dtParseDate(document.getElementById('dd-end').value);

var warningHtml = sign < 0
? ' <span style="color:#dc2626;font-size:13px;">（終了日が開始日より前です）</span>'
: '';
document.getElementById('dd-main').innerHTML =
dtFmtDisplay(s0)+' ～ '+dtFmtDisplay(e0)+warningHtml;

var grid = document.getElementById('dd-grid');
grid.innerHTML = [
{v: y, l: '年'},
{v: mo, l: 'ヶ月'},
{v: da, l: '日（端数）'},
{v: totalDays, l: '合計日数'},
{v: totalWeeks+'週'+remDays+'日', l: '週換算'},
{v: totalHours.toLocaleString(), l: '合計時間（h）'}
].map(function(i){
return '<div class="dt-result-item"><div class="val">'+i.v+'</div><div class="lbl">'+i.l+'</div></div>';
}).join('');

document.getElementById('dd-sub').innerHTML =
'開始日：<strong>'+dtFmtDisplay(s0)+'</strong><br>'+
'終了日：<strong>'+dtFmtDisplay(e0)+'</strong>';

res.classList.add('show');
};

window.dtCalcAddSub = function() {
var err = document.getElementById('as-error');
var res = document.getElementById('as-result');
err.classList.remove('show');
res.classList.remove('show');

var base = dtParseDate(document.getElementById('as-date').value);
var amt = parseInt(document.getElementById('as-amount').value, 10);
var unit = document.getElementById('as-unit').value;
if (!base || isNaN(amt) || amt < 0) { err.classList.add('show'); return; }

var mul = _op === 'add' ? 1 : -1;
var result = new Date(base);
var unitLabels = {days:'日',weeks:'週間',months:'ヶ月',years:'年'};

if (unit === 'days') {
result.setDate(result.getDate() + mul * amt);
} else if (unit === 'weeks') {
result.setDate(result.getDate() + mul * amt * 7);
} else if (unit === 'months') {
result.setMonth(result.getMonth() + mul * amt);
} else if (unit === 'years') {
result.setFullYear(result.getFullYear() + mul * amt);
}

var opLabel = _op === 'add' ? '後' : '前';
document.getElementById('as-main').innerHTML =
dtFmtDisplay(base)+' の <span style="color:#4f46e5;">'+amt+unitLabels[unit]+opLabel+'</span>';
document.getElementById('as-sub').innerHTML =
'結果：<strong style="font-size:20px;">'+dtFmtDisplay(result)+'</strong>'+
'<span class="dt-dow-badge">'+DAYS_JA[result.getDay()]+'</span>';

res.classList.add('show');
};

window.dtCalcBiz = function() {
var err = document.getElementById('bd-error');
var res = document.getElementById('bd-result');
err.classList.remove('show');
res.classList.remove('show');

var s = dtParseDate(document.getElementById('bd-start').value);
var e = dtParseDate(document.getElementById('bd-end').value);
if (!s || !e) { err.classList.add('show'); return; }

var sign = 1;
if (e < s) { sign = -1; var tmp = s; s = e; e = tmp; }

var msPerDay = 86400000;
var totalDays = Math.round((e - s) / msPerDay) + 1;
var bizDays = 0, weekendDays = 0;
var cur = new Date(s);
for (var i = 0; i < totalDays; i++) {
var dow = cur.getDay();
if (dow === 0 || dow === 6) weekendDays++;
else bizDays++;
cur.setDate(cur.getDate() + 1);
}

var s0 = dtParseDate(document.getElementById('bd-start').value);
var e0 = dtParseDate(document.getElementById('bd-end').value);

document.getElementById('bd-main').innerHTML =
dtFmtDisplay(s0)+' ～ '+dtFmtDisplay(e0);

var grid = document.getElementById('bd-grid');
grid.innerHTML = [
{v: bizDays, l: '営業日数'},
{v: weekendDays, l: '土日数'},
{v: totalDays, l: '合計日数（含む）'}
].map(function(i){
return '<div class="dt-result-item"><div class="val">'+i.v+'</div><div class="lbl">'+i.l+'</div></div>';
}).join('');

var wks = Math.floor(bizDays / 5);
var rem = bizDays % 5;
document.getElementById('bd-sub').innerHTML =
'約 <strong>'+wks+'週間'+(rem ? rem+'日' : '')+'</strong> の営業時間に相当します。<br>'+
'<span style="font-size:13px;color:#888;">祝日は自動的には除外されません。必要な場合は手動で差し引いてください。</span>';

res.classList.add('show');
};
})();
</script>
</div>

## 使い方

**モード1 — 日付の差を計算：** 開始日と終了日を入力して「差を計算する」をクリックすると、年・月・日・合計日数・週数・時間数が表示されます。

**モード2 — 日数の加減算：** 基準日を選択し、数値と単位（日・週・ヶ月・年）を設定して加算または減算を選びます。結果の日付と曜日が即座に表示されます。

**モード3 — 営業日計算：** 2つの日付を入力すると、その期間に含まれる平日（月〜金）の日数をカウントします。土日は自動で除外されます。

### よくある質問

**日付の差はどのように計算されますか？**
カレンダー上の正確な差を使用します。年・月は暦上の位置で計算し、端数の日数はうるう年を含めて正確にカウントします。

**営業日計算で祝日は除外されますか？**
土曜日と日曜日は自動的に除外されますが、祝日は自動除外されません。祝日を除外したい場合は、計算結果から手動で差し引いてください。

**異なる年をまたぐ計算はできますか？**
はい。複数年にわたる期間、うるう年、月の日数の違いもすべて自動で処理します。

**曜日表示は何に使いますか？**
計算結果に曜日（例：月曜日）が表示されるため、会議や締め切りのスケジュール確認に役立ちます。

---

*関連ツール：[年齢計算ツール](/ja/tools/age-calculator/) · [カレンダー生成ツール](/ja/tools/calendar-generator/)*
