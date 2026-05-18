---
title: "フリーランス報酬計算ツール｜適正な時給・単価を自動計算【2026年版】"
date: 2025-05-25
draft: false
slug: "freelance-hoshu-calculator"
aliases:
  - /ja/tools/freelance-rate-calculator/
description: "目標年収・稼働時間・経費を入力するだけで、フリーランスの適正時給・日単価・必要売上を自動計算。職種別相場や年収別比較テーブルも掲載した無料ツール。"
author: "Productivity Works編集部"
categories:
  - "無料ツール"
tags:
  - "フリーランス"
  - "報酬計算"
  - "時給"
  - "単価"
  - "計算ツール"
  - "副業"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/freelance-hoshu-calculator.png"
  alt: "フリーランス報酬計算ツール｜適正な時給・単価を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# フリーランス報酬計算ツール【2026年版】

目標年収・稼働時間・経費を入力するだけで、**適正な時給単価**・**日単価**・**必要月間売上**を自動計算します。値下げ交渉に負けない「根拠ある単価」を把握しましょう。

<div id="fh-calc" style="max-width:680px;margin:0 auto;font-family:'Noto Sans JP',sans-serif;">

<div style="padding:24px;border:2px solid #0d9488;border-radius:12px;background:#f0fdfa;">

<h3 style="margin:0 0 16px;color:#0f766e;font-size:17px;">入力項目</h3>

<div style="margin-bottom:18px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">目標年収（万円）</label>
<div style="display:flex;align-items:center;gap:12px;">
<input type="number" id="targetNenshu" min="100" max="3000" step="10" value="500" oninput="calcFH()" style="width:120px;padding:8px 10px;border:2px solid #0d9488;border-radius:6px;font-size:18px;font-weight:bold;color:#0f766e;text-align:center;">
<span style="font-size:14px;color:#64748b;">万円</span>
</div>
</div>

<div style="margin-bottom:18px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">週の稼働時間（時間）</label>
<input type="range" id="weeklyHours" min="20" max="40" step="1" value="30" oninput="calcFH()" style="width:100%;accent-color:#0d9488;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>20h</span><span id="weeklyHoursVal" style="font-weight:bold;font-size:17px;color:#0d9488;">30時間/週</span><span>40h</span></div>
</div>

<div style="margin-bottom:18px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">年間稼働週数</label>
<input type="range" id="workWeeks" min="40" max="52" step="1" value="48" oninput="calcFH()" style="width:100%;accent-color:#0d9488;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>40週</span><span id="workWeeksVal" style="font-weight:bold;font-size:17px;color:#0d9488;">48週/年</span><span>52週</span></div>
</div>

<div style="margin-bottom:18px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">年間経費（万円）</label>
<div style="display:flex;align-items:center;gap:12px;">
<input type="number" id="annualExpense" min="0" max="500" step="5" value="50" oninput="calcFH()" style="width:120px;padding:8px 10px;border:2px solid #0d9488;border-radius:6px;font-size:18px;font-weight:bold;color:#0f766e;text-align:center;">
<span style="font-size:14px;color:#64748b;">万円（PC・通信費・書籍など）</span>
</div>
</div>

<div style="margin-bottom:18px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">税金・社会保険料率（%）</label>
<input type="range" id="taxRate" min="15" max="40" step="1" value="30" oninput="calcFH()" style="width:100%;accent-color:#0d9488;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>15%</span><span id="taxRateVal" style="font-weight:bold;font-size:17px;color:#0d9488;">30%</span><span>40%</span></div>
</div>

<div style="margin-bottom:4px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;font-size:14px;">利益マージン（%）</label>
<input type="range" id="marginRate" min="0" max="30" step="1" value="10" oninput="calcFH()" style="width:100%;accent-color:#0d9488;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span id="marginRateVal" style="font-weight:bold;font-size:17px;color:#0d9488;">10%</span><span>30%</span></div>
</div>

</div>

<!-- 主要結果 -->
<div id="fh-result-main" style="margin-top:20px;">
</div>

<!-- 内訳グリッド -->
<div id="fh-result-grid" style="margin-top:16px;display:grid;grid-template-columns:repeat(2,1fr);gap:12px;">
</div>

<!-- 売上内訳バー -->
<div id="fh-breakdown" style="margin-top:20px;padding:20px;border:2px solid #0d9488;border-radius:12px;background:#fff;">
<h3 style="margin:0 0 14px;color:#0f766e;font-size:16px;">手元に残る金額の内訳</h3>
<div id="fh-bar-labels" style="display:flex;justify-content:space-between;font-size:12px;color:#64748b;margin-bottom:4px;"></div>
<div id="fh-bar" style="display:flex;height:32px;border-radius:8px;overflow:hidden;"></div>
<div id="fh-bar-legend" style="display:flex;flex-wrap:wrap;gap:12px;margin-top:10px;font-size:13px;"></div>
</div>

<!-- 案件単価変換 -->
<div style="margin-top:20px;padding:20px;border:2px solid #0d9488;border-radius:12px;background:#fff;">
<h3 style="margin:0 0 14px;color:#0f766e;font-size:16px;">案件単価変換（推奨時給単価 × 稼働時間）</h3>
<div id="fh-project-rates" style="display:grid;grid-template-columns:repeat(2,1fr);gap:10px;"></div>
</div>

<!-- 年収別比較テーブル -->
<div style="margin-top:20px;padding:20px;border:2px solid #0d9488;border-radius:12px;background:#fff;">
<h3 style="margin:0 0 14px;color:#0f766e;font-size:16px;">年収別 単価比較テーブル（現在の稼働条件で試算）</h3>
<div style="overflow-x:auto;">
<table id="fh-table" style="width:100%;border-collapse:collapse;font-size:14px;min-width:360px;"></table>
</div>
</div>

</div>

<script>
function fmt(n){return Math.round(n).toLocaleString('ja-JP');}
function fmtMan(n){return (Math.round(n/1000)/10).toFixed(1);}

function calcFH(){
  var targetMan=parseFloat(document.getElementById('targetNenshu').value)||500;
  var weekH=parseInt(document.getElementById('weeklyHours').value);
  var weeks=parseInt(document.getElementById('workWeeks').value);
  var expenseMan=parseFloat(document.getElementById('annualExpense').value)||0;
  var taxPct=parseInt(document.getElementById('taxRate').value);
  var marginPct=parseInt(document.getElementById('marginRate').value);

  // ラベル更新
  document.getElementById('weeklyHoursVal').textContent=weekH+'時間/週';
  document.getElementById('workWeeksVal').textContent=weeks+'週/年';
  document.getElementById('taxRateVal').textContent=taxPct+'%';
  document.getElementById('marginRateVal').textContent=marginPct+'%';

  // 計算
  var totalHours=weekH*weeks;                     // 年間総稼働時間
  var targetYen=targetMan*10000;                  // 目標年収（円）
  var expenseYen=expenseMan*10000;                // 年間経費（円）
  var taxRate=taxPct/100;
  var marginRate=marginPct/100;

  // 必要年間売上 = (目標年収 + 経費) / (1 - 税率)
  var requiredSalesYen=(targetYen+expenseYen)/(1-taxRate);

  // 最低時給単価（マージンなし）
  var minHourlyRate=Math.ceil(requiredSalesYen/totalHours/10)*10;

  // 推奨時給単価（マージン込み）
  var recHourlyRate=Math.ceil(minHourlyRate/(1-marginRate)/10)*10;

  // 推奨ベースの必要年間売上
  var recAnnualSales=recHourlyRate*totalHours;

  // 月間売上
  var recMonthlySales=recAnnualSales/12;

  // 日単価・半日単価（8時間換算）
  var dayRate=recHourlyRate*8;
  var halfDayRate=recHourlyRate*4;

  // 内訳（推奨売上ベース）
  var taxAmt=recAnnualSales*taxRate;
  var marginAmt=recAnnualSales*marginRate;
  var tedoriAmt=recAnnualSales-taxAmt-expenseYen-marginAmt;

  // 主要結果描画
  var rhtml='<div style="padding:24px;border:2px solid #0d9488;border-radius:12px;background:#0d9488;color:#fff;text-align:center;">';
  rhtml+='<div style="font-size:13px;opacity:0.85;margin-bottom:4px;">最低時給単価</div>';
  rhtml+='<div style="font-size:28px;font-weight:bold;opacity:0.9;">'+fmt(minHourlyRate)+'<span style="font-size:16px;font-weight:normal;">円/時</span></div>';
  rhtml+='<div style="margin-top:12px;font-size:13px;opacity:0.85;">推奨時給単価（マージン'+marginPct+'%込み）</div>';
  rhtml+='<div style="font-size:42px;font-weight:bold;letter-spacing:-1px;">'+fmt(recHourlyRate)+'<span style="font-size:20px;font-weight:normal;">円/時</span></div>';
  rhtml+='</div>';
  document.getElementById('fh-result-main').innerHTML=rhtml;

  // グリッド
  var ghtml='';
  var cells=[
    {label:'必要年間売上',val:fmt(Math.round(recAnnualSales/10000))+'万円',bg:'#f0fdfa',tc:'#0f766e'},
    {label:'必要月間売上',val:fmt(Math.round(recMonthlySales/10000))+'万円',bg:'#f0fdfa',tc:'#0f766e'},
    {label:'日単価（8時間）',val:fmt(dayRate)+'円',bg:'#fef3c7',tc:'#b45309'},
    {label:'半日単価（4時間）',val:fmt(halfDayRate)+'円',bg:'#fef3c7',tc:'#b45309'},
  ];
  cells.forEach(function(c){
    ghtml+='<div style="background:'+c.bg+';border-radius:10px;padding:14px;text-align:center;">';
    ghtml+='<div style="font-size:12px;color:#64748b;margin-bottom:4px;">'+c.label+'</div>';
    ghtml+='<div style="font-size:20px;font-weight:bold;color:'+c.tc+';">'+c.val+'</div>';
    ghtml+='</div>';
  });
  document.getElementById('fh-result-grid').innerHTML=ghtml;

  // 内訳バー
  var total=recAnnualSales;
  var segs=[
    {label:'手取り',amt:Math.max(tedoriAmt,0),color:'#0d9488'},
    {label:'税金・社保',amt:taxAmt,color:'#f59e0b'},
    {label:'経費',amt:expenseYen,color:'#94a3b8'},
    {label:'マージン',amt:marginAmt,color:'#6366f1'},
  ];
  var barHtml='';
  var legendHtml='';
  var labelHtml='';
  segs.forEach(function(s){
    var pct=(s.amt/total*100).toFixed(1);
    if(parseFloat(pct)<=0)return;
    barHtml+='<div style="width:'+pct+'%;background:'+s.color+';"></div>';
    legendHtml+='<span><span style="display:inline-block;width:12px;height:12px;background:'+s.color+';border-radius:2px;vertical-align:middle;margin-right:4px;"></span>'+s.label+' '+fmt(Math.round(s.amt/10000))+'万円 ('+pct+'%)</span>';
  });
  document.getElementById('fh-bar').innerHTML=barHtml;
  document.getElementById('fh-bar-legend').innerHTML=legendHtml;
  document.getElementById('fh-bar-labels').innerHTML='<span>売上合計 '+fmt(Math.round(total/10000))+'万円/年</span>';

  // 案件単価変換
  var projectHours=[2,5,10,20,40];
  var projectLabels=['2時間案件','5時間案件','10時間案件','20時間案件','40時間（月1件）'];
  var prHtml='';
  projectHours.forEach(function(h,i){
    var rate=fmt(recHourlyRate*h);
    var bg=i%2===0?'#f0fdfa':'#fff';
    prHtml+='<div style="background:'+bg+';border:1px solid #ccfbf1;border-radius:8px;padding:12px;text-align:center;">';
    prHtml+='<div style="font-size:12px;color:#64748b;margin-bottom:4px;">'+projectLabels[i]+'</div>';
    prHtml+='<div style="font-size:18px;font-weight:bold;color:#0d9488;">'+rate+'<span style="font-size:12px;font-weight:normal;">円</span></div>';
    prHtml+='</div>';
  });
  document.getElementById('fh-project-rates').innerHTML=prHtml;

  // 年収別テーブル
  var nenshuList=[300,400,500,600,800,1000];
  var thtml='<thead><tr style="background:#0d9488;color:#fff;">';
  thtml+='<th style="padding:10px 8px;text-align:left;">目標年収</th>';
  thtml+='<th style="padding:10px 8px;text-align:right;">最低時給</th>';
  thtml+='<th style="padding:10px 8px;text-align:right;">推奨時給</th>';
  thtml+='<th style="padding:10px 8px;text-align:right;">日単価</th>';
  thtml+='</tr></thead><tbody>';
  nenshuList.forEach(function(n,i){
    var ty=n*10000;
    var rs=(ty+expenseYen)/(1-taxRate);
    var mh=Math.ceil(rs/totalHours/10)*10;
    var rh=Math.ceil(mh/(1-marginRate)/10)*10;
    var dr=rh*8;
    var bg=i%2===0?'#fff':'#f0fdfa';
    var bold=n===Math.round(targetMan/100)*100?'font-weight:bold;':'';
    var highlight=n===targetMan?'background:#ccfbf1;':('background:'+bg+';');
    thtml+='<tr style="'+highlight+bold+'">';
    thtml+='<td style="padding:9px 8px;">'+n+'万円'+(n===targetMan?' ✓':'')+'</td>';
    thtml+='<td style="padding:9px 8px;text-align:right;">'+fmt(mh)+'円</td>';
    thtml+='<td style="padding:9px 8px;text-align:right;color:#0d9488;font-weight:bold;">'+fmt(rh)+'円</td>';
    thtml+='<td style="padding:9px 8px;text-align:right;">'+fmt(dr)+'円</td>';
    thtml+='</tr>';
  });
  thtml+='</tbody>';
  document.getElementById('fh-table').innerHTML=thtml;
}

document.addEventListener('DOMContentLoaded',function(){calcFH();});
calcFH();
</script>

---

## フリーランスの適正単価の決め方

### 1. 「手取り目標」から逆算する

会社員と違い、フリーランスは**税金・社会保険料・経費**をすべて売上から負担します。目標年収500万円の場合、実際には700〜800万円規模の売上が必要なケースが多いです。上のツールで「必要年間売上」を確認し、そこから時給に落とし込むのが正攻法です。

### 2. 「最低単価」を死守する

値下げ交渉を受けた際、根拠なく応じると赤字になります。このツールで算出した**最低時給単価**は「これ以下では受けられない」ラインです。提案時は推奨単価を提示し、交渉余地として最低単価との差を保持しておきましょう。

### 3. 稼働時間に「ノンビラブル時間」を含めない

実際に請求できる稼働時間は、総稼働時間の70〜80%程度です。営業・事務・スキルアップの時間は収益を生みません。週30時間稼働でも請求できるのは実質20〜24時間、と考えて設定すると安全です。

---

## 職種別 フリーランス単価の相場

| 職種 | 時給相場 | 月単価（20日×8h） | 備考 |
|------|---------|-----------------|------|
| Webライター | 2,000〜5,000円 | 32〜80万円 | 専門領域・文字単価で大きく変動 |
| Webデザイナー | 3,000〜8,000円 | 48〜128万円 | UI/UXスキルで上振れ |
| エンジニア（Web） | 5,000〜15,000円 | 80〜240万円 | 言語・フレームワーク次第 |
| コンサルタント | 8,000〜30,000円 | 128〜480万円 | 業界経験・実績が直結 |
| 動画編集者 | 2,000〜6,000円 | 32〜96万円 | 案件単価は1本3〜10万円が多い |
| マーケター | 4,000〜12,000円 | 64〜192万円 | 広告運用・SEO等で差異 |

※上記は2026年時点の市場相場の目安です。スキル・実績・クライアントにより大きく異なります。

---

## 関連ツール

> 副業の税金を計算 → [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/)

> 手取り額を計算 → [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)

> 所得税を計算 → [所得税シミュレーター](/ja/tools/shotokuzei-simulator/)

> 家計を見直す → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)

> FIRE達成年数を計算 → [FIREシミュレーター](/ja/tools/fire-simulator/)

> 転職後の年収を比較 → [転職年収シミュレーター](/ja/tools/tenshoku-nenshu-simulator/)

---

## 関連記事

- [フリーランス確定申告のやり方と必要書類まとめ](/ja/posts/フリーランス-確定申告-やり方/)
- [開業届の出し方とメリット・デメリット](/ja/posts/kaigyo-todoke-kakikata-merit/)
- [フリーランスにおすすめの会計ソフト比較2026年版](/ja/posts/freelance-kaikei-soft-hikaku/)
- [副業から独立するタイミングの見極め方](/ja/posts/fukugyou-dokuritsu-timing/)
- [フリーランスが節税できる経費一覧【2026年】](/ja/posts/freelance-keihi-ichiran-2026/)

---

> フリーランスの経理なら**[freee会計（無料トライアルあり）](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)**

---

*本ツールの計算結果は概算です。実際の税額・社会保険料は個人の状況により異なります。正確な数値は税理士・社会保険労務士にご相談ください。*
