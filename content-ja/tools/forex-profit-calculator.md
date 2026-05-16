---
title: "FX損益計算ツール | 無料FXトレードシミュレーター"
date: 2026-05-14
draft: false
slug: "forex-profit-calculator"
description: "FXトレードの損益を瞬時に計算。通貨ペア・ロット数・価格を入力するだけで損益額・必要証拠金・実効レバレッジを表示します。"
author: "Productivity Works"
categories:
  - "無料ツール"
tags:
  - "FX"
  - "計算ツール"
  - "トレード"
  - "投資ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/forex-profit-calculator.png"
  alt: "FX損益計算ツール | 無料FXトレードシミュレーター"
  relative: false
---

# FX損益計算ツール

取引の詳細を入力すると、**損益額**・**必要証拠金**・**ROI** を瞬時に計算します。

<div id="fx-calc-en" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">通貨ペア</label>
<select id="pairEn" onchange="fxCalcEn()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="EURUSD" data-pip="0.0001" data-pipval="10">EUR/USD</option>
<option value="GBPUSD" data-pip="0.0001" data-pipval="10">GBP/USD</option>
<option value="USDJPY" data-pip="0.01" data-pipval="6.45">USD/JPY</option>
<option value="AUDUSD" data-pip="0.0001" data-pipval="10">AUD/USD</option>
<option value="USDCAD" data-pip="0.0001" data-pipval="7.35">USD/CAD</option>
</select>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">ポジション</label>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<button id="btnBuyEn" onclick="setDirEn('buy')" style="padding:12px;border:2px solid #2563eb;border-radius:8px;background:#2563eb;color:white;font-weight:bold;font-size:16px;cursor:pointer;">買い（ロング）</button>
<button id="btnSellEn" onclick="setDirEn('sell')" style="padding:12px;border:2px solid #cbd5e1;border-radius:8px;background:white;color:#475569;font-weight:bold;font-size:16px;cursor:pointer;">売り（ショート）</button>
</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">ロット数（1標準ロット = 100,000通貨単位）</label>
<input type="range" id="lotsEn" min="0.01" max="10" step="0.01" value="1" oninput="fxCalcEn()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0.01</span><span id="lotsValEn" style="font-weight:bold;font-size:18px;color:#2563eb;">1.00 ロット</span><span>10.00</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:20px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;">エントリー価格</label>
<input type="number" id="entryPriceEn" value="1.0840" step="0.0001" oninput="fxCalcEn()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;box-sizing:border-box;">
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;">決済価格</label>
<input type="number" id="exitPriceEn" value="1.0940" step="0.0001" oninput="fxCalcEn()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;box-sizing:border-box;">
</div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">スプレッド（pips）</label>
<input type="range" id="spreadEn" min="0" max="5" step="0.1" value="1.0" oninput="fxCalcEn()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0</span><span id="spreadValEn" style="font-weight:bold;font-size:18px;color:#2563eb;">1.0 pips</span><span>5.0</span></div>
</div>

<div id="plBoxEn" style="background:#16a34a;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">損益</div>
<div id="plAmountEn" style="font-size:36px;font-weight:bold;">+$900.00</div>
<div style="font-size:13px;margin-top:4px;">正味pips: <span id="plPipsEn" style="font-weight:bold;">+90.0</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">必要証拠金</div>
<div id="marginEn" style="font-size:14px;font-weight:bold;color:#0369a1;">$2,168</div>
</div>
<div style="background:#fef9c3;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">レバレッジ</div>
<div id="leverageEn" style="font-size:14px;font-weight:bold;color:#a16207;">50:1</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">ROI</div>
<div id="roiEn" style="font-size:14px;font-weight:bold;color:#15803d;">+41.5%</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>注意：</strong> 計算はレバレッジ50:1（米国標準）を使用。Pip値は概算です。実際の結果はブローカーによって異なります。スワップ・ロールオーバー費用は含みません。
</div>

</div>

<script>
var fxDirEn='buy';
function setDirEn(d){
  fxDirEn=d;
  document.getElementById('btnBuyEn').style.background=d==='buy'?'#2563eb':'white';
  document.getElementById('btnBuyEn').style.color=d==='buy'?'white':'#475569';
  document.getElementById('btnBuyEn').style.borderColor=d==='buy'?'#2563eb':'#cbd5e1';
  document.getElementById('btnSellEn').style.background=d==='sell'?'#dc2626':'white';
  document.getElementById('btnSellEn').style.color=d==='sell'?'white':'#475569';
  document.getElementById('btnSellEn').style.borderColor=d==='sell'?'#dc2626':'#cbd5e1';
  fxCalcEn();
}
function fxCalcEn(){
  var sel=document.getElementById('pairEn');
  var opt=sel.options[sel.selectedIndex];
  var pipSize=parseFloat(opt.getAttribute('data-pip'));
  var pipValPer=parseFloat(opt.getAttribute('data-pipval'));
  var lots=parseFloat(document.getElementById('lotsEn').value);
  var entry=parseFloat(document.getElementById('entryPriceEn').value);
  var exit=parseFloat(document.getElementById('exitPriceEn').value);
  var spreadPips=parseFloat(document.getElementById('spreadEn').value);
  if(isNaN(entry)||isNaN(exit)||entry<=0||exit<=0){return;}
  var priceDiff=fxDirEn==='buy'?(exit-entry):(entry-exit);
  var pips=priceDiff/pipSize;
  var netPips=pips-spreadPips;
  var pl=netPips*pipValPer*lots;
  var plRound=Math.round(pl*100)/100;
  var notional=entry*100000*lots;
  var marginReq=Math.ceil(notional/50);
  var lev=notional/marginReq;
  var roiPct=marginReq>0?((plRound/marginReq)*100):0;
  var plBox=document.getElementById('plBoxEn');
  plBox.style.background=plRound>=0?'#16a34a':'#dc2626';
  document.getElementById('lotsValEn').textContent=lots.toFixed(2)+' ロット';
  document.getElementById('spreadValEn').textContent=spreadPips.toFixed(1)+' pips';
  document.getElementById('plAmountEn').textContent=(plRound>=0?'+':'')+plRound.toLocaleString('en-US',{style:'currency',currency:'USD'});
  document.getElementById('plPipsEn').textContent=(netPips>=0?'+':'')+netPips.toFixed(1);
  document.getElementById('marginEn').textContent='$'+marginReq.toLocaleString();
  document.getElementById('leverageEn').textContent=Math.round(lev)+':1';
  document.getElementById('roiEn').textContent=(roiPct>=0?'+':'')+roiPct.toFixed(1)+'%';
}
fxCalcEn();
</script>

---

## FX損益の計算方法

FX損益の基本計算式：

**損益 = （価格変動pips数）×（Pip値）×（ロット数）－ スプレッドコスト**

| 通貨ペア | Pipサイズ | Pip値（1標準ロット） |
|----------|-----------|---------------------|
| EUR/USD | 0.0001 | $10 |
| GBP/USD | 0.0001 | $10 |
| USD/JPY | 0.01 | 約$6.45 |
| AUD/USD | 0.0001 | $10 |

---

## リスク管理のポイント

1. **1回の取引でリスクにさらすのは口座残高の1〜2%以内**
2. **必ずストップロスを設定**して最大損失を限定する
3. **初心者はマイクロロット（0.01）から始める**
4. **レバレッジが高いほどリスクも高い** — 経験を積むまでは低レバレッジで
5. **トレード日誌をつけて**パフォーマンスを記録・改善する

---

## よくある質問

**Q: Pipとは何ですか？**
Pipとは通貨ペアの最小価格変動単位です。EUR/USDでは0.0001（小数点第4位）、USD/JPYでは0.01（小数点第2位）です。

**Q: FX取引を始めるにはどれくらいの資金が必要ですか？**
マイクロ口座（0.01ロット）なら$50〜100程度から始められます。ただし、適切なリスク管理のためには$500〜1,000が推奨されます。

**Q: 標準ロットとミニロットの違いは？**
標準ロットは100,000通貨単位、ミニロットは10,000通貨単位、マイクロロットは1,000通貨単位です。

---

## 関連ツール

- [複利計算ツール](/tools/compound-interest-calculator/) — 長期投資の成長シミュレーション
- [ローン返済計算ツール](/tools/loan-repayment-calculator/) — 借入返済計画
- [予算プランナー](/tools/budget-planner/) — 月次予算の最適化

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)
