---
title: "複利計算シミュレーター｜積立投資の将来資産を自動計算【無料】"
date: 2025-06-23
draft: false
slug: "fukuri-keisan"
description: "毎月の積立額・想定利回り・投資期間を入力するだけで将来の資産額を自動計算。元本と運用益の内訳、NISA非課税との比較もわかる無料シミュレーター。"
author: "Productivity Works編集部"
categories:
  - "マネー・個人金融"
tags:
  - "複利"
  - "積立投資"
  - "計算ツール"
  - "NISA"
  - "資産形成"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/fukuri-keisan.png"
  alt: "複利計算シミュレーター｜積立投資の将来資産を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 複利計算シミュレーター

毎月の積立額・想定利回り・投資期間を入力して、**将来の資産額**を計算しましょう。

<div id="calc-app" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #1e40af;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">毎月の積立額（円）</label>
<input type="range" id="monthly" min="1000" max="300000" step="1000" value="30000" oninput="calcFK()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1,000円</span><span id="monthlyVal" style="font-weight:bold;font-size:18px;color:#1e40af;">30,000円</span><span>300,000円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">想定年利回り（%）</label>
<input type="range" id="rate" min="1" max="10" step="0.5" value="5" oninput="calcFK()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1%</span><span id="rateVal" style="font-weight:bold;font-size:18px;color:#1e40af;">5.0%</span><span>10%</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">投資期間（年）</label>
<input type="range" id="years" min="1" max="40" step="1" value="20" oninput="calcFK()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1年</span><span id="yearsVal" style="font-weight:bold;font-size:18px;color:#1e40af;">20年</span><span>40年</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">将来の資産総額</div>
<div id="totalAsset" style="font-size:36px;font-weight:bold;">0円</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">元本（積立総額）</div>
<div id="principal" style="font-size:16px;font-weight:bold;color:#0369a1;">0円</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">運用益（複利効果）</div>
<div id="profit" style="font-size:16px;font-weight:bold;color:#15803d;">0円</div>
</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#fef3c7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">NISA非課税の場合</div>
<div id="nisaNet" style="font-size:16px;font-weight:bold;color:#b45309;">0円</div>
<div style="font-size:11px;color:#92400e;">運用益に課税なし</div>
</div>
<div style="background:#fce7f3;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">特定口座（課税20.315%）</div>
<div id="taxedNet" style="font-size:16px;font-weight:bold;color:#be185d;">0円</div>
<div style="font-size:11px;color:#9d174d;" id="taxSaved">NISA節税額: 0円</div>
</div>
</div>

<h3 style="margin:20px 0 12px;font-size:16px;">年次推移表</h3>
<div style="overflow-x:auto;">
<table id="timeline" style="width:100%;border-collapse:collapse;font-size:13px;">
<thead><tr style="background:#1e3a5f;color:white;">
<th style="padding:6px 8px;text-align:center;">年</th>
<th style="padding:6px 8px;text-align:right;">元本</th>
<th style="padding:6px 8px;text-align:right;">資産総額</th>
<th style="padding:6px 8px;text-align:right;">運用益</th>
</tr></thead>
<tbody id="tbody"></tbody>
</table>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;margin-top:16px;">
<strong>前提条件：</strong>毎月末に積立、月次複利で計算。実際の投資リターンは市場環境によって変動します。過去の実績は将来の成果を保証するものではありません。
</div>

</div>

<script>
function calcFK(){
  var m=parseInt(document.getElementById('monthly').value);
  var r=parseFloat(document.getElementById('rate').value)/100;
  var y=parseInt(document.getElementById('years').value);
  var mr=r/12;
  var n=y*12;
  var fv=m*((Math.pow(1+mr,n)-1)/mr);
  var p=m*n;
  var g=fv-p;
  var tax=g*0.20315;
  document.getElementById('monthlyVal').textContent=m.toLocaleString()+'円';
  document.getElementById('rateVal').textContent=(r*100).toFixed(1)+'%';
  document.getElementById('yearsVal').textContent=y+'年';
  document.getElementById('totalAsset').textContent=Math.floor(fv).toLocaleString()+'円';
  document.getElementById('principal').textContent=p.toLocaleString()+'円';
  document.getElementById('profit').textContent=Math.floor(g).toLocaleString()+'円';
  document.getElementById('nisaNet').textContent=Math.floor(fv).toLocaleString()+'円';
  document.getElementById('taxedNet').textContent=Math.floor(fv-tax).toLocaleString()+'円';
  document.getElementById('taxSaved').textContent='NISA節税額: '+Math.floor(tax).toLocaleString()+'円';
  var tb=document.getElementById('tbody');
  tb.innerHTML='';
  var milestones=[1,3,5,10,15,20,25,30,35,40];
  for(var i=0;i<milestones.length;i++){
var yr=milestones[i];
if(yr>y)break;
var nm=yr*12;
var fvY=m*((Math.pow(1+mr,nm)-1)/mr);
var pY=m*nm;
var gY=fvY-pY;
var bg=i%2===0?'#f8fafc':'#ffffff';
tb.innerHTML+='<tr style="background:'+bg+'"><td style="padding:6px 8px;text-align:center;border-bottom:1px solid #e2e8f0;">'+yr+'年</td><td style="padding:6px 8px;text-align:right;border-bottom:1px solid #e2e8f0;">'+pY.toLocaleString()+'円</td><td style="padding:6px 8px;text-align:right;border-bottom:1px solid #e2e8f0;font-weight:bold;">'+Math.floor(fvY).toLocaleString()+'円</td><td style="padding:6px 8px;text-align:right;border-bottom:1px solid #e2e8f0;color:#15803d;">+'+Math.floor(gY).toLocaleString()+'円</td></tr>';
  }
}
calcFK();
</script>

---

## 複利効果のポイント

- **時間が最大の味方** — 同じ利回りでも、20年と30年では運用益に2倍以上の差が生まれます
- **毎月の積立額が重要** — 月1万円でも30年続ければ、年利5%で約830万円に成長します
- **NISAの非課税効果** — 運用益の20.315%が非課税になるため、長期投資ほどNISAの恩恵が大きくなります

---

## よくある質問

**Q: 年利5%は現実的ですか？**
全世界株式インデックス（MSCI ACWI）の過去20年の平均リターンは年率約7〜8%です。インフレと手数料を考慮すると、5%は保守的な見積もりです。

**Q: 複利と単利の違いは？**
単利は元本にのみ利息がつきますが、複利は「元本＋利息」に対して利息がつきます。長期になるほど複利の効果は指数関数的に大きくなります。

**Q: つみたてNISAとの関係は？**
新NISAのつみたて投資枠（年120万円）で購入した投資信託の運用益は非課税です。このシミュレーターで非課税の効果を確認できます。

---

> NISAを始めるなら、**<a href="https://hb.afl.rakuten.co.jp/hsc/41ab8a31.8f450617.41ab8a32.86e006c4/?link_type=hybrid_url&ut=eyJwYWdlIjoic2hvcCIsInR5cGUiOiJoeWJyaWRfdXJsIiwiY29sIjoxLCJjYXQiOiIxIiwiYmFuIjoiMTI0NjkzOSIsImFtcCI6ZmFsc2V9" target="_blank" rel="nofollow">楽天証券</a>**がおすすめ。つみたて投資枠でインデックスファンドを設定すれば、この複利効果を非課税で享受できます。

---

## 関連ツール

- [NISAシミュレーター](/ja/tools/nisa-simulator/) — 新NISAの非課税効果を計算
- [iDeCoシミュレーター](/ja/tools/ideco-simulator/) — iDeCoの節税額を年収別に計算
- [配当金シミュレーター](/ja/tools/haitoukin-simulator/) — 配当投資の年間収入を計算
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 年収から手取りを計算
- [家計簿シミュレーター](/ja/tools/kakeibo-generator/) — 月収から理想の支出配分を計算

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [新NISA始め方2026年版【初心者向け完全ガイド】口座開設から投資スタートまで](/ja/posts/shin-nisa-hajimekata-shoshinsha-2026/)
