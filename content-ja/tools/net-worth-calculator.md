---
title: "純資産計算機 | あなたの財務状況を把握する"
date: 2025-04-09
draft: false
slug: "net-worth-calculator"
description: "無料の純資産計算機。資産と負債を入力して純資産・負債資産比率を即座に算出。年齢別の日本平均と比較できます。"
categories: ["無料ツール"]
tags: ["純資産計算機", "純資産", "個人ファイナンス", "財務健全性", "計算機", "資産", "負債"]
author: "Productivity Works Editorial"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/net-worth-calculator.png"
  alt: "純資産計算機"
  relative: false
---

*本ページにはアフィリエイトリンクが含まれます。*

# 純資産計算機

資産と負債を入力して、**純資産**を即座に計算し、財務状況を確認しましょう。

<div id="nw-calc" style="max-width:760px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b !important;color-scheme:light;">

<!-- 資産セクション -->
<div style="padding:24px;border:2px solid #059669;border-radius:12px;background:#f0fdf4;margin-bottom:20px;">

<h2 style="margin:0 0 20px 0;font-size:20px;color:#059669;">資産</h2>

<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">現金・預金</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">普通預金（給与口座）</label><input type="number" id="aCash" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">定期預金・貯蓄口座</label><input type="number" id="aSavings" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">緊急資金</label><input type="number" id="aEmergency" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">投資</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">iDeCo（個人型確定拠出年金）</label><input type="number" id="a401k" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">NISA口座</label><input type="number" id="aIRA" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">特定口座・一般口座（株・投信）</label><input type="number" id="aBrokerage" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">暗号資産（仮想通貨）</label><input type="number" id="aCrypto" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="margin-bottom:16px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">不動産</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">自宅の時価</label><input type="number" id="aHome" min="0" step="100000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">その他不動産</label><input type="number" id="aRealEstate" min="0" step="100000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="margin-bottom:20px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:12px;">その他の資産</div>
<div style="display:grid;gap:10px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">自動車・バイク</label><input type="number" id="aVehicles" min="0" step="50000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">貴重品（宝飾品・美術品・コレクション）</label><input type="number" id="aValuables" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">事業（会社）の持分</label><input type="number" id="aBusiness" min="0" step="100000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #a7f3d0;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>
</div>

<div style="padding:16px;background:#059669;border-radius:8px;display:flex;justify-content:space-between;align-items:center;">
<span style="color:white;font-weight:bold;font-size:16px;">資産合計</span>
<span id="totalAssets" style="color:white;font-weight:bold;font-size:24px;">¥0</span>
</div>

</div>

<!-- 負債セクション -->
<div style="padding:24px;border:2px solid #dc2626;border-radius:12px;background:#fef2f2;margin-bottom:20px;">

<h2 style="margin:0 0 20px 0;font-size:20px;color:#dc2626;">負債</h2>

<div style="display:grid;gap:10px;margin-bottom:20px;">
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">住宅ローン残高</label><input type="number" id="lMortgage" min="0" step="100000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">教育ローン・奨学金</label><input type="number" id="lStudent" min="0" step="50000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">自動車ローン</label><input type="number" id="lAuto" min="0" step="50000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">クレジットカード残高</label><input type="number" id="lCredit" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;min-width:14px;">¥</span>
<div style="flex:1;"><label style="display:block;font-size:13px;color:#64748b;margin-bottom:4px;">その他の借入</label><input type="number" id="lOther" min="0" step="10000" value="0" oninput="calcNW()" style="width:100%;padding:9px 12px;border:1px solid #fca5a5;border-radius:8px;font-size:15px;box-sizing:border-box;"></div>
</div>
</div>

<div style="padding:16px;background:#dc2626;border-radius:8px;display:flex;justify-content:space-between;align-items:center;">
<span style="color:white;font-weight:bold;font-size:16px;">負債合計</span>
<span id="totalLiabilities" style="color:white;font-weight:bold;font-size:24px;">¥0</span>
</div>

</div>

<!-- 結果パネル -->
<div id="nwResults" style="padding:28px;border-radius:12px;background:#eef2ff;border:2px solid #4f46e5;margin-bottom:20px;">

<div style="text-align:center;margin-bottom:24px;">
<div style="font-size:14px;color:#64748b;text-transform:uppercase;letter-spacing:0.08em;margin-bottom:6px;">あなたの純資産</div>
<div id="netWorthDisplay" style="font-size:52px;font-weight:bold;color:#4f46e5;line-height:1.1;">¥0</div>
<div id="debtRatioDisplay" style="font-size:14px;color:#64748b;margin-top:8px;">負債資産比率: —</div>
</div>

<!-- 資産配分バー -->
<div style="margin-bottom:20px;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:8px;">資産配分</div>
<div id="assetBar" style="height:28px;border-radius:8px;overflow:hidden;display:flex;background:#e2e8f0;">
<div id="barCash" style="background:#059669;height:100%;transition:width 0.3s;" title="現金・預金"></div>
<div id="barInvest" style="background:#10b981;height:100%;transition:width 0.3s;" title="投資"></div>
<div id="barProperty" style="background:#34d399;height:100%;transition:width 0.3s;" title="不動産"></div>
<div id="barOther" style="background:#6ee7b7;height:100%;transition:width 0.3s;" title="その他"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#059669;border-radius:2px;margin-right:4px;"></span>現金・預金 <span id="pctCash" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#10b981;border-radius:2px;margin-right:4px;"></span>投資 <span id="pctInvest" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#34d399;border-radius:2px;margin-right:4px;"></span>不動産 <span id="pctProperty" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#6ee7b7;border-radius:2px;margin-right:4px;"></span>その他 <span id="pctOther" style="font-weight:bold;">0%</span></span>
</div>
</div>

<!-- 負債内訳バー -->
<div id="liabBreakdownWrap" style="display:none;">
<div style="font-weight:bold;font-size:13px;color:#64748b;text-transform:uppercase;letter-spacing:0.05em;margin-bottom:8px;">負債の内訳</div>
<div id="liabBar" style="height:28px;border-radius:8px;overflow:hidden;display:flex;background:#e2e8f0;">
<div id="lbarMortgage" style="background:#dc2626;height:100%;transition:width 0.3s;" title="住宅ローン"></div>
<div id="lbarStudent" style="background:#ef4444;height:100%;transition:width 0.3s;" title="教育ローン"></div>
<div id="lbarAuto" style="background:#f87171;height:100%;transition:width 0.3s;" title="自動車ローン"></div>
<div id="lbarCredit" style="background:#fca5a5;height:100%;transition:width 0.3s;" title="クレジットカード"></div>
<div id="lbarOther" style="background:#fecaca;height:100%;transition:width 0.3s;" title="その他"></div>
</div>
<div style="display:flex;flex-wrap:wrap;gap:12px;font-size:12px;color:#64748b;margin-top:8px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#dc2626;border-radius:2px;margin-right:4px;"></span>住宅ローン <span id="lpctMortgage" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#ef4444;border-radius:2px;margin-right:4px;"></span>教育ローン <span id="lpctStudent" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#f87171;border-radius:2px;margin-right:4px;"></span>自動車ローン <span id="lpctAuto" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#fca5a5;border-radius:2px;margin-right:4px;"></span>クレカ <span id="lpctCredit" style="font-weight:bold;">0%</span></span>
<span><span style="display:inline-block;width:10px;height:10px;background:#fecaca;border-radius:2px;margin-right:4px;"></span>その他 <span id="lpctOther" style="font-weight:bold;">0%</span></span>
</div>
</div>

</div>

<!-- 比較セクション -->
<div style="padding:24px;border-radius:12px;background:#f8fafc;border:1px solid #e2e8f0;margin-bottom:20px;">

<h3 style="margin:0 0 16px 0;font-size:18px;color:#1e293b !important;color-scheme:light;">平均と比べてどうか？</h3>
<p style="font-size:13px;color:#64748b;margin:0 0 16px 0;">日本の年齢層別・世帯純資産の中央値の目安（金融広報中央委員会データを参考）。</p>

<div style="overflow-x:auto;">
<table id="benchmarkTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#4f46e5;color:white;">
<th style="padding:10px 14px;text-align:left;border-radius:0;">年齢層</th>
<th style="padding:10px 14px;text-align:right;">純資産中央値（目安）</th>
<th style="padding:10px 14px;text-align:center;">あなたの位置</th>
</tr>
</thead>
<tbody id="benchmarkBody"></tbody>
</table>
</div>

<div style="margin-top:12px;font-size:12px;color:#64748b;">年齢層を選択すると、平均との比較が表示されます。</div>

<div style="margin-top:16px;">
<label style="display:block;font-size:13px;font-weight:bold;color:#64748b;margin-bottom:6px;">あなたの年齢層</label>
<select id="ageGroup" onchange="calcNW()" style="padding:9px 12px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;background:white;">
<option value="">— 年齢層を選択 —</option>
<option value="0">35歳未満</option>
<option value="1">35〜44歳</option>
<option value="2">45〜54歳</option>
<option value="3">55〜64歳</option>
<option value="4">65〜74歳</option>
<option value="5">75歳以上</option>
</select>
</div>

</div>

<!-- 目標トラッカー -->
<div style="padding:24px;border-radius:12px;background:#f8fafc;border:1px solid #e2e8f0;margin-bottom:8px;">

<h3 style="margin:0 0 16px 0;font-size:18px;color:#1e293b !important;color-scheme:light;">目標トラッカー</h3>

<div style="margin-bottom:16px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">純資産の目標額（円）</label>
<div style="display:flex;align-items:center;gap:8px;">
<span style="font-size:16px;color:#64748b;">¥</span>
<input type="number" id="nwGoal" min="0" step="1000000" value="100000000" oninput="calcNW()" style="flex:1;padding:9px 12px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;box-sizing:border-box;">
</div>
</div>

<div style="margin-bottom:10px;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;margin-bottom:6px;">
<span>目標への進捗</span>
<span id="goalPctLabel" style="font-weight:bold;color:#4f46e5;">0%</span>
</div>
<div style="height:20px;background:#e2e8f0;border-radius:10px;overflow:hidden;">
<div id="goalBar" style="height:100%;background:#4f46e5;border-radius:10px;transition:width 0.4s;width:0%;"></div>
</div>
</div>

<div id="goalMessage" style="font-size:14px;color:#4f46e5;font-weight:bold;margin-top:8px;">目標の0%に達しています。</div>

</div>

</div>

<script>
var NW_BENCHMARKS=[
  {label:'35歳未満',median:2200000},
  {label:'35\u301044\u6b73',median:6500000},
  {label:'45\u301054\u6b73',median:9000000},
  {label:'55\u301064\u6b73',median:14000000},
  {label:'65\u301074\u6b73',median:18000000},
  {label:'75\u6b73\u4ee5\u4e0a',median:16000000}
];

function v(id){return parseFloat(document.getElementById(id).value)||0;}

function fmt(n){
  var abs=Math.abs(n);
  var s='\u00a5'+abs.toLocaleString('ja-JP',{minimumFractionDigits:0,maximumFractionDigits:0});
  return n<0?'-'+s:s;
}

function pct(part,total){
  if(total<=0) return 0;
  return Math.round((part/total)*100);
}

function calcNW(){
  var cash=v('aCash')+v('aSavings')+v('aEmergency');
  var invest=v('a401k')+v('aIRA')+v('aBrokerage')+v('aCrypto');
  var property=v('aHome')+v('aRealEstate');
  var other=v('aVehicles')+v('aValuables')+v('aBusiness');
  var totalAssets=cash+invest+property+other;

  var lMortgage=v('lMortgage');
  var lStudent=v('lStudent');
  var lAuto=v('lAuto');
  var lCredit=v('lCredit');
  var lOther=v('lOther');
  var totalLiabilities=lMortgage+lStudent+lAuto+lCredit+lOther;

  var netWorth=totalAssets-totalLiabilities;

  document.getElementById('totalAssets').textContent=fmt(totalAssets);
  document.getElementById('totalLiabilities').textContent=fmt(totalLiabilities);

  var nwEl=document.getElementById('netWorthDisplay');
  nwEl.textContent=fmt(netWorth);
  nwEl.style.color=netWorth>=0?'#4f46e5':'#dc2626';

  var dtaEl=document.getElementById('debtRatioDisplay');
  if(totalAssets>0){
var dta=((totalLiabilities/totalAssets)*100).toFixed(1);
dtaEl.textContent='\u8ca0\u50b5\u8cc7\u7523\u6bd4\u7387: '+dta+'%';
  } else {
dtaEl.textContent='\u8ca0\u50b5\u8cc7\u7523\u6bd4\u7387: \u2014';
  }

  var pCash=pct(cash,totalAssets);
  var pInvest=pct(invest,totalAssets);
  var pProperty=pct(property,totalAssets);
  var pOther=pct(other,totalAssets);
  var remainder=totalAssets>0?Math.max(0,100-pCash-pInvest-pProperty-pOther):0;
  pOther+=remainder;

  document.getElementById('barCash').style.width=pCash+'%';
  document.getElementById('barInvest').style.width=pInvest+'%';
  document.getElementById('barProperty').style.width=pProperty+'%';
  document.getElementById('barOther').style.width=pOther+'%';
  document.getElementById('pctCash').textContent=pCash+'%';
  document.getElementById('pctInvest').textContent=pInvest+'%';
  document.getElementById('pctProperty').textContent=pProperty+'%';
  document.getElementById('pctOther').textContent=pOther+'%';

  var liabWrap=document.getElementById('liabBreakdownWrap');
  if(totalLiabilities>0){
liabWrap.style.display='block';
var lpM=pct(lMortgage,totalLiabilities);
var lpS=pct(lStudent,totalLiabilities);
var lpA=pct(lAuto,totalLiabilities);
var lpC=pct(lCredit,totalLiabilities);
var lpO=pct(lOther,totalLiabilities);
var lRemainder=Math.max(0,100-lpM-lpS-lpA-lpC-lpO);
lpO+=lRemainder;
document.getElementById('lbarMortgage').style.width=lpM+'%';
document.getElementById('lbarStudent').style.width=lpS+'%';
document.getElementById('lbarAuto').style.width=lpA+'%';
document.getElementById('lbarCredit').style.width=lpC+'%';
document.getElementById('lbarOther').style.width=lpO+'%';
document.getElementById('lpctMortgage').textContent=lpM+'%';
document.getElementById('lpctStudent').textContent=lpS+'%';
document.getElementById('lpctAuto').textContent=lpA+'%';
document.getElementById('lpctCredit').textContent=lpC+'%';
document.getElementById('lpctOther').textContent=lpO+'%';
  } else {
liabWrap.style.display='none';
  }

  var ageIdx=document.getElementById('ageGroup').value;
  var tbody='';
  NW_BENCHMARKS.forEach(function(b,i){
var isSelected=(ageIdx!==''&&parseInt(ageIdx)===i);
var bg=isSelected?'#eef2ff':(i%2===0?'white':'#f8fafc');
var border=isSelected?'2px solid #4f46e5':'1px solid transparent';
var position='';
if(isSelected){
if(netWorth>=b.median){
var abovePct=Math.round(((netWorth-b.median)/b.median)*100);
position='<span style="color:#059669;font-weight:bold;">\u4e2d\u592e\u5024\u4ee5\u4e0a (+'+abovePct+'%)</span>';
} else {
var belowPct=Math.round(((b.median-netWorth)/b.median)*100);
position='<span style="color:#dc2626;font-weight:bold;">\u4e2d\u592e\u5024\u672a\u6e80 (-'+belowPct+'%)</span>';
}
} else {
position='<span style="color:#94a3b8;">\u2014</span>';
}
tbody+='<tr style="background:'+bg+';border:'+border+';">';
tbody+='<td style="padding:10px 14px;font-weight:'+(isSelected?'bold':'normal')+';">'+b.label+'</td>';
tbody+='<td style="padding:10px 14px;text-align:right;">\u00a5'+b.median.toLocaleString('ja-JP')+'</td>';
tbody+='<td style="padding:10px 14px;text-align:center;">'+position+'</td>';
tbody+='</tr>';
  });
  document.getElementById('benchmarkBody').innerHTML=tbody;

  var goal=v('nwGoal');
  var goalPct=goal>0?Math.min(100,Math.max(0,Math.round((netWorth/goal)*100))):0;
  document.getElementById('goalBar').style.width=goalPct+'%';
  document.getElementById('goalPctLabel').textContent=goalPct+'%';
  var goalMsg=document.getElementById('goalMessage');
  if(netWorth<=0){
goalMsg.textContent='\u8ca0\u50b5\u3092\u8fd4\u6e08\u3057\u3001\u8cc7\u7523\u3092\u5897\u3084\u3057\u3066\u76ee\u6a19\u306b\u5411\u304b\u3063\u3066\u524d\u9032\u3057\u307e\u3057\u3087\u3046\u3002';
goalMsg.style.color='#dc2626';
  } else if(goalPct>=100){
goalMsg.textContent='\u304a\u3081\u3067\u3068\u3046\u3054\u3056\u3044\u307e\u3059\u2014\u7d14\u8cc7\u7523\u306e\u76ee\u6a19\u3092\u9054\u6210\u3057\u307e\u3057\u305f\uff01';
goalMsg.style.color='#059669';
  } else {
var remaining=goal-netWorth;
goalMsg.textContent='\u76ee\u6a19\u306e'+goalPct+'%\u306b\u9054\u3057\u3066\u3044\u307e\u3059\u3002\u6b8b\u308a '+fmt(remaining)+'\u3002';
goalMsg.style.color='#4f46e5';
  }
}

calcNW();
</script>

---

## 使い方

1. **資産を入力** — 預金・投資口座・不動産・その他の資産を現在の時価で入力してください。
2. **負債を入力** — 住宅ローン・教育ローン・自動車ローン・クレジットカード残高をすべて入力してください。
3. **年齢層を選択** — 日本の平均値と自分の純資産を比較できます。
4. **目標を設定** — 目標純資産額を入力して進捗を確認しましょう。

入力と同時に計算結果が更新されます。データはブラウザ外に送信されません。

---

## 純資産とは？なぜ重要か？

純資産は個人ファイナンスで最も重要な指標です。**資産（持っているもの）から負債（借りているもの）を引いた金額**がそれです。プラスなら資産が借金を上回り、マイナスなら（特に若い世代に多い）借金が資産を超えていることを意味します。定期的にこの数字を追うことが、本当の意味で資産形成できているかを測る最善の方法です。

---

## 純資産を増やす方法

### 1. 収入を増やす

余分な収入をすべて貯蓄・投資に回せば、純資産は着実に増えます。昇給交渉・スキルアップ・副業などを検討しましょう。

### 2. 支出を減らす

無駄なサブスクリプションを解約し、高金利の借金を借り換え、「欲しいもの」と「必要なもの」を区別しましょう。

### 3. 高金利の負債を返済する

クレジットカードの高金利（年15〜20%超）は純資産を急速に削ります。投資より先に高金利の借金を返すことを優先してください。

### 4. 継続的に投資する

iDeCo・NISA・インデックスファンドへの積み立てを自動化し、複利の力を長期間にわたって活用しましょう。

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

---

## 関連ツール

> 家計簿プランナー → [家計簿プランナーツール](/ja/tools/budget-planner/)
> 緊急資金計算 → [緊急資金計算ツール](/ja/tools/emergency-fund-calculator/)
> 支出トラッカー → [支出トラッカーツール](/ja/tools/expense-tracker/)

