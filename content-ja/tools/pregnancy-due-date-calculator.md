---
title: "出産予定日計算ツール - 赤ちゃんの予定日を計算"
date: 2025-10-18
description: "最終月経日または受精日から出産予定日を計算。妊娠週数・トリメスター・重要な健診スケジュールも一目でわかります。"
categories: ["無料ツール"]
tags: ["計算ツール", "変換ツール", "無料ツール"]
slug: "pregnancy-due-date-calculator"
ShowToc: false
cover:
  image: "/images/covers/pregnancy-due-date-calculator.png"
  alt: "出産予定日計算ツール"
---

<div id="pdd-app">

<style>
#pdd-app {
font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Noto Sans JP', sans-serif;
max-width: 760px;
margin: 0 auto;
color: #2d2d2d;
line-height: 1.7;
}

#pdd-app h2 {
font-size: 1.4rem;
font-weight: 700;
color: #c2185b;
margin: 0 0 1rem 0;
}

#pdd-app h3 {
font-size: 1.05rem;
font-weight: 600;
margin: 0 0 0.75rem 0;
color: #2d2d2d;
}

#pdd-app .pdd-intro {
background: #fce4ec;
border-left: 4px solid #e91e63;
border-radius: 0 8px 8px 0;
padding: 1rem 1.25rem;
margin-bottom: 1.5rem;
font-size: 0.95rem;
color: #555;
}

#pdd-app .pdd-card {
background: #fff;
border: 1px solid #f0c0d0;
border-radius: 12px;
padding: 1.5rem;
margin-bottom: 1.5rem;
box-shadow: 0 2px 8px rgba(194,24,91,0.06);
}

#pdd-app .pdd-input-group {
margin-bottom: 1.25rem;
}

#pdd-app .pdd-input-group label {
display: block;
font-weight: 600;
margin-bottom: 0.4rem;
font-size: 0.9rem;
color: #444;
}

#pdd-app .pdd-input-group input[type="date"] {
width: 100%;
padding: 0.65rem 0.9rem;
border: 2px solid #f0c0d0;
border-radius: 8px;
font-size: 1rem;
color: #2d2d2d;
background: #fff;
box-sizing: border-box;
transition: border-color 0.2s;
outline: none;
}

#pdd-app .pdd-input-group input[type="date"]:focus {
border-color: #e91e63;
}

#pdd-app .pdd-hint {
font-size: 0.8rem;
color: #aaa;
margin-top: 0.3rem;
}

#pdd-app .pdd-divider {
display: flex;
align-items: center;
gap: 0.75rem;
margin: 1rem 0;
color: #aaa;
font-size: 0.85rem;
font-weight: 600;
}

#pdd-app .pdd-divider::before,
#pdd-app .pdd-divider::after {
content: '';
flex: 1;
height: 1px;
background: #f0c0d0;
}

#pdd-app .pdd-btn {
display: inline-block;
background: #e91e63;
color: #fff;
border: none;
border-radius: 8px;
padding: 0.75rem 2rem;
font-size: 1rem;
font-weight: 700;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
width: 100%;
margin-top: 0.5rem;
}

#pdd-app .pdd-btn:hover {
background: #c2185b;
transform: translateY(-1px);
}

#pdd-app .pdd-btn:active {
transform: translateY(0);
}

#pdd-app .pdd-result {
display: none;
}

#pdd-app .pdd-result.visible {
display: block;
}

#pdd-app .pdd-due-date-box {
background: linear-gradient(135deg, #e91e63 0%, #c2185b 100%);
color: #fff;
border-radius: 12px;
padding: 1.5rem;
text-align: center;
margin-bottom: 1.5rem;
}

#pdd-app .pdd-due-date-box .pdd-due-label {
font-size: 0.9rem;
opacity: 0.85;
margin-bottom: 0.4rem;
font-weight: 500;
}

#pdd-app .pdd-due-date-box .pdd-due-value {
font-size: 2rem;
font-weight: 800;
letter-spacing: 0.02em;
margin-bottom: 0.5rem;
}

#pdd-app .pdd-due-date-box .pdd-due-sub {
font-size: 0.9rem;
opacity: 0.85;
}

#pdd-app .pdd-stats-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 1rem;
margin-bottom: 1.5rem;
}

@media (max-width: 520px) {
#pdd-app .pdd-stats-grid {
grid-template-columns: 1fr 1fr;
}
}

#pdd-app .pdd-stat-box {
background: #fce4ec;
border-radius: 10px;
padding: 0.9rem 0.75rem;
text-align: center;
}

#pdd-app .pdd-stat-box .pdd-stat-label {
font-size: 0.72rem;
color: #888;
font-weight: 600;
margin-bottom: 0.3rem;
}

#pdd-app .pdd-stat-box .pdd-stat-value {
font-size: 1.4rem;
font-weight: 800;
color: #c2185b;
line-height: 1.1;
}

#pdd-app .pdd-stat-box .pdd-stat-unit {
font-size: 0.75rem;
color: #c2185b;
font-weight: 500;
}

#pdd-app .pdd-trimester-bar {
background: #fce4ec;
border-radius: 10px;
padding: 1rem 1.25rem;
margin-bottom: 1.5rem;
}

#pdd-app .pdd-trimester-bar h3 {
margin-bottom: 0.75rem;
font-size: 0.9rem;
color: #888;
}

#pdd-app .pdd-progress-wrap {
background: #f8bbd0;
border-radius: 999px;
height: 14px;
position: relative;
overflow: hidden;
margin-bottom: 0.4rem;
}

#pdd-app .pdd-progress-fill {
height: 100%;
background: linear-gradient(90deg, #e91e63, #c2185b);
border-radius: 999px;
transition: width 0.6s ease;
}

#pdd-app .pdd-trimester-labels {
display: flex;
justify-content: space-between;
font-size: 0.7rem;
color: #aaa;
font-weight: 500;
}

#pdd-app .pdd-trimester-badge {
display: inline-block;
background: #e91e63;
color: #fff;
border-radius: 999px;
padding: 0.2rem 0.9rem;
font-size: 0.82rem;
font-weight: 700;
margin-top: 0.6rem;
}

#pdd-app .pdd-milestones {
margin-bottom: 1.5rem;
}

#pdd-app .pdd-milestone-item {
display: flex;
align-items: flex-start;
gap: 0.9rem;
padding: 0.8rem 0;
border-bottom: 1px solid #fce4ec;
}

#pdd-app .pdd-milestone-item:last-child {
border-bottom: none;
}

#pdd-app .pdd-milestone-icon {
width: 36px;
height: 36px;
border-radius: 50%;
display: flex;
align-items: center;
justify-content: center;
font-size: 1rem;
flex-shrink: 0;
background: #fce4ec;
}

#pdd-app .pdd-milestone-icon.past {
background: #e0e0e0;
}

#pdd-app .pdd-milestone-icon.current {
background: #e91e63;
}

#pdd-app .pdd-milestone-body {
flex: 1;
}

#pdd-app .pdd-milestone-body .pdd-ms-header {
display: flex;
justify-content: space-between;
align-items: flex-start;
gap: 0.5rem;
margin-bottom: 0.2rem;
flex-wrap: wrap;
}

#pdd-app .pdd-milestone-body .pdd-ms-name {
font-weight: 700;
font-size: 0.9rem;
color: #2d2d2d;
}

#pdd-app .pdd-milestone-body .pdd-ms-date {
font-size: 0.78rem;
color: #e91e63;
font-weight: 600;
white-space: nowrap;
}

#pdd-app .pdd-milestone-body .pdd-ms-desc {
font-size: 0.82rem;
color: #777;
}

#pdd-app .pdd-dev-section {
margin-bottom: 1.5rem;
}

#pdd-app .pdd-dev-card {
background: #fff9fb;
border: 1px solid #f8bbd0;
border-radius: 10px;
padding: 1rem 1.1rem;
margin-bottom: 0.75rem;
}

#pdd-app .pdd-dev-card .pdd-dev-week {
font-weight: 800;
color: #e91e63;
font-size: 0.82rem;
margin-bottom: 0.2rem;
}

#pdd-app .pdd-dev-card .pdd-dev-title {
font-weight: 700;
font-size: 0.95rem;
margin-bottom: 0.25rem;
}

#pdd-app .pdd-dev-card .pdd-dev-desc {
font-size: 0.85rem;
color: #666;
}

#pdd-app .pdd-cta {
background: #fff3e0;
border: 1px solid #ffcc80;
border-radius: 10px;
padding: 1.1rem 1.25rem;
margin-top: 1.5rem;
font-size: 0.92rem;
color: #555;
}

#pdd-app .pdd-cta strong {
color: #e65100;
}

#pdd-app .pdd-cta a {
color: #e65100;
font-weight: 700;
}

#pdd-app .pdd-error {
display: none;
color: #c2185b;
background: #fce4ec;
border-radius: 8px;
padding: 0.65rem 1rem;
font-size: 0.88rem;
font-weight: 600;
margin-top: 0.5rem;
}

#pdd-app .pdd-error.visible {
display: block;
}
</style>

<div class="pdd-intro">
<strong>最終月経開始日</strong>または<strong>排卵（受精）日</strong>を入力するだけで、出産予定日・現在の妊娠週数・トリメスター・重要な健診スケジュールを自動計算します。ナーゲレ法則（最終月経日 + 280日）を使用します。
</div>

<div class="pdd-card">
<h2>出産予定日計算ツール</h2>

<div class="pdd-input-group">
<label for="pdd-lmp">最終月経開始日（LMP）</label>
<input type="date" id="pdd-lmp" />
<div class="pdd-hint">生理が始まった日を選択してください</div>
</div>

<div class="pdd-divider">または</div>

<div class="pdd-input-group">
<label for="pdd-conception">排卵日・受精日（わかる場合）</label>
<input type="date" id="pdd-conception" />
<div class="pdd-hint">排卵日から最終月経日（約14日前）を自動換算します</div>
</div>

<div class="pdd-error" id="pdd-error">最終月経開始日または排卵日を入力してください。</div>

<button class="pdd-btn" onclick="pddCalculate()">出産予定日を計算する</button>
</div>

<div class="pdd-result" id="pdd-result">

<div class="pdd-due-date-box">
<div class="pdd-due-label">出産予定日（EDD）</div>
<div class="pdd-due-value" id="pdd-edd-display"></div>
<div class="pdd-due-sub" id="pdd-days-remaining"></div>
</div>

<div class="pdd-stats-grid">
<div class="pdd-stat-box">
<div class="pdd-stat-label">現在の妊娠週数</div>
<div class="pdd-stat-value" id="pdd-week-num">—</div>
<div class="pdd-stat-unit">週</div>
</div>
<div class="pdd-stat-box">
<div class="pdd-stat-label">週内の日数</div>
<div class="pdd-stat-value" id="pdd-day-num">—</div>
<div class="pdd-stat-unit">日</div>
</div>
<div class="pdd-stat-box">
<div class="pdd-stat-label">トリメスター</div>
<div class="pdd-stat-value" id="pdd-trimester-num">—</div>
<div class="pdd-stat-unit">期</div>
</div>
</div>

<div class="pdd-card pdd-trimester-bar">
<h3>妊娠の進捗</h3>
<div class="pdd-progress-wrap">
<div class="pdd-progress-fill" id="pdd-progress-fill" style="width:0%"></div>
</div>
<div class="pdd-trimester-labels">
<span>1週</span>
<span>第1期（1〜13週）</span>
<span>第2期（14〜27週）</span>
<span>第3期（28週〜）</span>
<span>40週</span>
</div>
<div id="pdd-trimester-badge" class="pdd-trimester-badge"></div>
</div>

<div class="pdd-card pdd-milestones">
<h2>主要な健診・マイルストーン</h2>
<div id="pdd-milestones-list"></div>
</div>

<div class="pdd-card pdd-dev-section">
<h2>週別 赤ちゃんの発育ハイライト</h2>
<div class="pdd-dev-card">
<div class="pdd-dev-week">妊娠8〜10週</div>
<div class="pdd-dev-title">主要臓器が形成される時期</div>
<div class="pdd-dev-desc">胎芽から胎児へ移行します。小さな指や足の指が現れ始め、心拍数は約170回/分。顔立ちも少しずつはっきりしてきます。</div>
</div>
<div class="pdd-dev-card">
<div class="pdd-dev-week">妊娠18〜22週</div>
<div class="pdd-dev-title">胎動の始まりと形態異常スクリーニング</div>
<div class="pdd-dev-desc">初めて赤ちゃんの動き（胎動）を感じる方が多い時期です。妊娠20週前後の胎児超音波検査（形態スクリーニング）では、主要臓器の形態確認と性別確認ができます。</div>
</div>
<div class="pdd-dev-card">
<div class="pdd-dev-week">妊娠28〜32週</div>
<div class="pdd-dev-title">脳の急速な発達期</div>
<div class="pdd-dev-desc">脳に特徴的なしわが形成されます。目の開閉ができるようになり、肺も出産に向けて成熟を始めます。</div>
</div>
<div class="pdd-dev-card">
<div class="pdd-dev-week">妊娠37〜40週</div>
<div class="pdd-dev-title">正期産 — 出産準備完了</div>
<div class="pdd-dev-desc">37週以降は「正期産」となり、いつ出産してもよい時期です。体重増加が続き、免疫抗体の移行も進みます。</div>
</div>
</div>

</div>

> 出産費用の管理も簡単 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

<script>
(function () {
function formatDateJa(d) {
return d.getFullYear() + '年' + (d.getMonth() + 1) + '月' + d.getDate() + '日';
}

function addDays(date, days) {
var d = new Date(date.getTime());
d.setDate(d.getDate() + days);
return d;
}

function daysBetween(a, b) {
return Math.round((b.getTime() - a.getTime()) / 86400000);
}

function getTrimesterInfo(weeks) {
if (weeks <= 13) return { num: '1', label: '第1トリメスター（1〜13週）', color: '#e91e63' };
if (weeks <= 27) return { num: '2', label: '第2トリメスター（14〜27週）', color: '#ad1457' };
return { num: '3', label: '第3トリメスター（28〜40週）', color: '#880e4f' };
}

window.pddCalculate = function () {
var lmpInput = document.getElementById('pdd-lmp').value;
var conceptionInput = document.getElementById('pdd-conception').value;
var errorEl = document.getElementById('pdd-error');
var resultEl = document.getElementById('pdd-result');

errorEl.classList.remove('visible');

var lmpDate;

if (lmpInput) {
lmpDate = new Date(lmpInput + 'T12:00:00');
} else if (conceptionInput) {
var conceptionDate = new Date(conceptionInput + 'T12:00:00');
lmpDate = addDays(conceptionDate, -14);
} else {
errorEl.classList.add('visible');
resultEl.classList.remove('visible');
return;
}

var edd = addDays(lmpDate, 280);
var today = new Date();
today.setHours(12, 0, 0, 0);

var daysPregnant = daysBetween(lmpDate, today);
var weeksPregnant = Math.floor(daysPregnant / 7);
var dayInWeek = daysPregnant % 7;
var daysRemaining = daysBetween(today, edd);
var progressPct = Math.min(100, Math.max(0, (daysPregnant / 280) * 100));

var trimInfo = getTrimesterInfo(weeksPregnant);

document.getElementById('pdd-edd-display').textContent = formatDateJa(edd);

if (daysRemaining > 0) {
document.getElementById('pdd-days-remaining').textContent =
'出産予定日まで あと ' + daysRemaining + ' 日';
} else if (daysRemaining === 0) {
document.getElementById('pdd-days-remaining').textContent = '今日が出産予定日です。';
} else {
document.getElementById('pdd-days-remaining').textContent =
'出産予定日から ' + Math.abs(daysRemaining) + ' 日が経過しています';
}

document.getElementById('pdd-week-num').textContent =
daysPregnant >= 0 ? weeksPregnant : '—';
document.getElementById('pdd-day-num').textContent =
daysPregnant >= 0 ? dayInWeek : '—';
document.getElementById('pdd-trimester-num').textContent =
daysPregnant >= 0 ? trimInfo.num : '—';

document.getElementById('pdd-progress-fill').style.width = progressPct.toFixed(1) + '%';
var badge = document.getElementById('pdd-trimester-badge');
badge.textContent = trimInfo.label;
badge.style.background = trimInfo.color;

var milestones = [
{
week: 8,
icon: '🩺',
name: '初回妊婦健診',
desc: '妊娠確認・血液検査・問診。母子手帳の交付申請もこの時期に。'
},
{
week: 12,
icon: '📷',
name: '妊娠12週 NT検査（初期超音波）',
desc: '染色体異常スクリーニング。赤ちゃんの最初の鮮明な画像が確認できます。'
},
{
week: 20,
icon: '🔬',
name: '妊娠20週 形態スクリーニング',
desc: '主要臓器の形態・位置・発育を詳細確認。性別がわかることも多い時期です。'
},
{
week: 28,
icon: '🌟',
name: '妊娠28週 第3トリメスター開始',
desc: '妊娠糖尿病スクリーニング検査の時期。健診頻度が増えます。'
},
{
week: 37,
icon: '✅',
name: '正期産（37週）',
desc: 'この週以降はいつ出産しても「正期産」。赤ちゃんはいつでも誕生できる状態です。'
},
{
week: 40,
icon: '👶',
name: '出産予定日（40週）',
desc: 'ナーゲレ法則による予定日。実際には予定日ちょうどに生まれる赤ちゃんは約5%です。'
}
];

var listEl = document.getElementById('pdd-milestones-list');
listEl.innerHTML = '';

milestones.forEach(function (ms) {
var msDate = addDays(lmpDate, ms.week * 7);
var msDaysFromToday = daysBetween(today, msDate);
var isPast = msDaysFromToday < 0;
var isCurrent = Math.abs(weeksPregnant - ms.week) <= 1 && !isPast;

var iconClass = isPast ? 'past' : (isCurrent ? 'current' : '');
var whenStr = isPast
? '通過済み'
: (msDaysFromToday === 0
? '本日！'
: 'あと ' + msDaysFromToday + ' 日（' + formatDateJa(msDate) + '）');

var item = document.createElement('div');
item.className = 'pdd-milestone-item';
item.innerHTML =
'<div class="pdd-milestone-icon ' + iconClass + '">' + ms.icon + '</div>' +
'<div class="pdd-milestone-body">' +
'<div class="pdd-ms-header">' +
'<span class="pdd-ms-name">妊娠' + ms.week + '週 — ' + ms.name + '</span>' +
'<span class="pdd-ms-date">' + whenStr + '</span>' +
'</div>' +
'<div class="pdd-ms-desc">' + ms.desc + '</div>' +
'</div>';
listEl.appendChild(item);
});

resultEl.classList.add('visible');
resultEl.scrollIntoView({ behavior: 'smooth', block: 'start' });
};

document.getElementById('pdd-lmp').addEventListener('input', function () {
if (this.value) document.getElementById('pdd-conception').value = '';
});
document.getElementById('pdd-conception').addEventListener('input', function () {
if (this.value) document.getElementById('pdd-lmp').value = '';
});
})();
</script>

</div>

---

## 関連ツール

> 年齢計算 → [年齢計算ツール](/ja/tools/age-calculator/)
> 犬の年齢計算 → [犬の年齢計算ツール](/ja/tools/dog-age-calculator/)

