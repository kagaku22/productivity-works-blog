---
title: "FX利益計算シミュレーター｜損益・税金・必要証拠金を自動計算【2026年版】"
date: 2026-05-14
draft: false
slug: "fx-profit-calculator"
description: "FX取引の損益を自動計算。通貨ペア・ロット数・売買価格を入力するだけで、利益額・税金・必要証拠金・実質レバレッジがわかる無料シミュレーター。"
author: "Productivity Works編集部"
categories:
  - "投資・資産運用"
tags:
  - "FX"
  - "シミュレーター"
  - "投資"
  - "計算ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/fx-profit-calculator.png"
  alt: "FX利益計算シミュレーター｜損益・税金・必要証拠金を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# FX利益計算シミュレーター【2026年版】

通貨ペア・ロット数・エントリー価格・決済価格を入力するだけで、**損益額**・**税金**・**必要証拠金**を自動計算します。

<div id="fx-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">通貨ペア</label>
<select id="pair" onchange="fxCalc()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;">
<option value="USDJPY" data-rate="155.00" data-pip="0.01" data-unit="1">USD/JPY（ドル円）</option>
<option value="EURJPY" data-rate="168.00" data-pip="0.01" data-unit="1">EUR/JPY（ユーロ円）</option>
<option value="GBPJPY" data-rate="196.00" data-pip="0.01" data-unit="1">GBP/JPY（ポンド円）</option>
<option value="AUDJPY" data-rate="100.00" data-pip="0.01" data-unit="1">AUD/JPY（豪ドル円）</option>
<option value="EURUSD" data-rate="1.0840" data-pip="0.0001" data-unit="155">EUR/USD（ユーロドル）</option>
</select>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">売買方向</label>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<button id="btnBuy" onclick="setDir('buy')" style="padding:12px;border:2px solid #2563eb;border-radius:8px;background:#2563eb;color:white;font-weight:bold;font-size:16px;cursor:pointer;">買い（ロング）</button>
<button id="btnSell" onclick="setDir('sell')" style="padding:12px;border:2px solid #cbd5e1;border-radius:8px;background:white;color:#475569;font-weight:bold;font-size:16px;cursor:pointer;">売り（ショート）</button>
</div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">取引数量（ロット） ※1ロット=10,000通貨</label>
<input type="range" id="lots" min="1" max="100" step="1" value="10" oninput="fxCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1ロット</span><span id="lotsVal" style="font-weight:bold;font-size:18px;color:#2563eb;">10ロット</span><span>100ロット</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:20px;">
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;">エントリー価格</label>
<input type="number" id="entryPrice" value="155.00" step="0.01" oninput="fxCalc()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;box-sizing:border-box;">
</div>
<div>
<label style="display:block;font-weight:bold;margin-bottom:6px;">決済価格</label>
<input type="number" id="exitPrice" value="156.00" step="0.01" oninput="fxCalc()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:6px;font-size:16px;box-sizing:border-box;">
</div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">スプレッド（pips）</label>
<input type="range" id="spread" min="0" max="5" step="0.1" value="0.2" oninput="fxCalc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0</span><span id="spreadVal" style="font-weight:bold;font-size:18px;color:#2563eb;">0.2 pips</span><span>5.0</span></div>
</div>

<div id="plBox" style="background:#16a34a;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">損益（税引前）</div>
<div id="plAmount" style="font-size:36px;font-weight:bold;">+100,000円</div>
<div style="font-size:13px;margin-top:4px;">獲得pips: <span id="plPips" style="font-weight:bold;">100.0 pips</span></div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">必要証拠金</div>
<div id="margin" style="font-size:14px;font-weight:bold;color:#0369a1;">620,000円</div>
</div>
<div style="background:#fef9c3;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">実質レバレッジ</div>
<div id="leverage" style="font-size:14px;font-weight:bold;color:#a16207;">25.0倍</div>
</div>
<div style="background:#fee2e2;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">利益にかかる税金</div>
<div id="taxAmount" style="font-size:14px;font-weight:bold;color:#dc2626;">20,315円</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">税引後の手取り</div>
<div id="netProfit" style="font-size:18px;font-weight:bold;color:#15803d;">79,685円</div>
</div>
<div style="background:#f3e8ff;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">証拠金利回り</div>
<div id="roi" style="font-size:18px;font-weight:bold;color:#7c3aed;">+16.1%</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>計算条件:</strong> レバレッジ25倍（国内FX上限）。税金は申告分離課税20.315%（所得税15.315%+住民税5%）。スワップポイント・ロスカット手数料は含みません。
</div>

</div>

<script>
var fxDir='buy';
function setDir(d){
  fxDir=d;
  document.getElementById('btnBuy').style.background=d==='buy'?'#2563eb':'white';
  document.getElementById('btnBuy').style.color=d==='buy'?'white':'#475569';
  document.getElementById('btnBuy').style.borderColor=d==='buy'?'#2563eb':'#cbd5e1';
  document.getElementById('btnSell').style.background=d==='sell'?'#dc2626':'white';
  document.getElementById('btnSell').style.color=d==='sell'?'white':'#475569';
  document.getElementById('btnSell').style.borderColor=d==='sell'?'#dc2626':'#cbd5e1';
  fxCalc();
}
function fxCalc(){
  var sel=document.getElementById('pair');
  var opt=sel.options[sel.selectedIndex];
  var pipSize=parseFloat(opt.getAttribute('data-pip'));
  var jpyPerPip=parseFloat(opt.getAttribute('data-unit'));
  var lots=parseInt(document.getElementById('lots').value);
  var entry=parseFloat(document.getElementById('entryPrice').value);
  var exit=parseFloat(document.getElementById('exitPrice').value);
  var spreadPips=parseFloat(document.getElementById('spread').value);
  if(isNaN(entry)||isNaN(exit)||entry<=0||exit<=0){return;}
  var units=lots*10000;
  var priceDiff=fxDir==='buy'?(exit-entry):(entry-exit);
  var pips=priceDiff/pipSize;
  var netPips=pips-spreadPips;
  var plJpy=netPips*pipSize*units*jpyPerPip;
  var plRound=Math.round(plJpy);
  var marginRate=entry*units/25;
  if(jpyPerPip>1){marginRate=entry*units*jpyPerPip/25;}else{marginRate=entry*units/25;}
  var marginJpy;
  if(sel.value.endsWith('JPY')){
    marginJpy=Math.ceil(entry*units/25);
  }else{
    marginJpy=Math.ceil(entry*units*jpyPerPip/25);
  }
  var lev=(entry*units*(sel.value.endsWith('JPY')?1:jpyPerPip))/marginJpy;
  var tax=plRound>0?Math.floor(plRound*0.20315):0;
  var netPl=plRound-tax;
  var roiPct=marginJpy>0?((plRound/marginJpy)*100):0;
  var plBox=document.getElementById('plBox');
  if(plRound>=0){
    plBox.style.background='#16a34a';
  }else{
    plBox.style.background='#dc2626';
  }
  document.getElementById('lotsVal').textContent=lots+'ロット';
  document.getElementById('spreadVal').textContent=spreadPips.toFixed(1)+' pips';
  document.getElementById('plAmount').textContent=(plRound>=0?'+':'')+plRound.toLocaleString()+'円';
  document.getElementById('plPips').textContent=(netPips>=0?'+':'')+netPips.toFixed(1)+' pips';
  document.getElementById('margin').textContent=marginJpy.toLocaleString()+'円';
  document.getElementById('leverage').textContent=lev.toFixed(1)+'倍';
  document.getElementById('taxAmount').textContent=tax.toLocaleString()+'円';
  document.getElementById('netProfit').textContent=(netPl>=0?'+':'')+netPl.toLocaleString()+'円';
  document.getElementById('roi').textContent=(roiPct>=0?'+':'')+roiPct.toFixed(1)+'%';
}
fxCalc();
</script>

---

## FXを始めるならどの口座？

シミュレーション結果を見て、FXに興味を持ちましたか？初心者におすすめのFX口座を紹介します。

### DMM FX — 初心者人気No.1

- **スプレッド**: USD/JPY 0.2銭（業界最狭水準）
- **最低取引単位**: 10,000通貨（1ロット）
- **特徴**: スマホアプリが使いやすい、24時間サポート、取引ツールが充実
- **口座開設**: 最短30分、スマホで本人確認完了

上のシミュレーターでスプレッド0.2 pipsに設定すると、DMM FXの実際のコストに近い計算ができます。

### GMOクリック証券 — 総合力No.1

- **スプレッド**: USD/JPY 0.2銭
- **最低取引単位**: 1,000通貨から可能
- **特徴**: FX以外の投資（株・CFD）もワンストップ

---

## FXの税金について知っておくべきこと

### 申告分離課税20.315%

FXの利益には**一律20.315%**の税金がかかります（所得税15.315% + 住民税5%）。給与所得とは別に計算されるため、副業の税率より有利な場合があります。

| 項目 | FX | 副業（雑所得） |
|------|-----|---------------|
| 税率 | 一律20.315% | 累進課税（5%〜45%） |
| 損益通算 | 他の先物取引と可能 | 原則不可 |
| 損失繰越 | 3年間繰越可能 | 不可 |

### 年間利益20万円以下の場合

給与所得者（会社員）でFX利益が年間20万円以下なら、確定申告は不要です（住民税の申告は必要）。

→ 詳しくは [副業の税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/) で確認

---

## FXのリスクと注意点

- **レバレッジのリスク**: 25倍のレバレッジは利益も損失も25倍。証拠金以上の損失が発生する可能性があります
- **ロスカット**: 証拠金維持率が一定水準を下回ると、自動的にポジションが決済されます
- **初心者は少額から**: まずは1〜2ロットで値動きに慣れることをおすすめします

---

## よくある質問

**Q. 1ロットでどれくらいの利益が出ますか？**
USD/JPYで1ロット（10,000通貨）の場合、1円動くと10,000円の損益です。10pips（0.1円）なら1,000円です。

**Q. 必要証拠金はいくらですか？**
USD/JPY 155円で1ロットの場合、155円 × 10,000通貨 ÷ 25（レバレッジ）= 62,000円です。上のシミュレーターで正確に計算できます。

**Q. FXと株、どちらが初心者向きですか？**
少額から始められるのはFX（数万円〜）。長期資産形成なら株・投資信託がおすすめです → [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/)

---

## 関連ツール・記事

- [つみたてNISAシミュレーター](/ja/tools/nisa-simulator/) — 長期投資の資産シミュレーション
- [複利計算シミュレーター](/ja/tools/fukuri-keisan/) — 複利効果を可視化
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 年収からの手取り計算
- [副業の税金計算シミュレーター](/ja/tools/fukugyou-tax-calculator/) — 確定申告の要否判定
