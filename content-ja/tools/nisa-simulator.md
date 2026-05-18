---
title: "つみたてNISAシミュレーター｜将来の資産額を無料で計算"
date: 2025-05-07
draft: false
slug: "nisa-simulator"
description: "つみたてNISA・新NISAの運用シミュレーション。毎月の積立額と運用年数を入力するだけで、将来の資産額を自動計算。非課税メリットも表示します。"
author: "Productivity Works編集部"
categories:
  - "投資・資産運用"
tags:
  - "新NISA"
  - "シミュレーター"
  - "投資"
  - "資産運用"
  - "計算ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/nisa-simulator.png"
  alt: "つみたてNISAシミュレーター｜将来の資産額を無料で計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# つみたてNISA / 新NISA 資産シミュレーター

毎月の積立額・想定利回り・運用年数を入力するだけで、**将来の資産額**と**非課税メリット**を自動計算します。

<div id="nisa-simulator" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">毎月の積立額（円）</label>
<input type="range" id="monthly" min="1000" max="100000" step="1000" value="30000" oninput="calc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1,000円</span><span id="monthlyVal" style="font-weight:bold;font-size:18px;color:#2563eb;">30,000円</span><span>100,000円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">想定年利回り（%）</label>
<input type="range" id="rate" min="1" max="10" step="0.5" value="5" oninput="calc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1%</span><span id="rateVal" style="font-weight:bold;font-size:18px;color:#2563eb;">5.0%</span><span>10%</span></div>
</div>

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">運用年数</label>
<input type="range" id="years" min="1" max="30" step="1" value="20" oninput="calc()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>1年</span><span id="yearsVal" style="font-weight:bold;font-size:18px;color:#2563eb;">20年</span><span>30年</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">将来の資産額（税引前）</div>
<div id="totalAsset" style="font-size:36px;font-weight:bold;">12,331,010円</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:16px;">
<div style="background:#e0f2fe;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">元本合計</div>
<div id="principal" style="font-size:16px;font-weight:bold;color:#0369a1;">7,200,000円</div>
</div>
<div style="background:#dcfce7;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">運用益</div>
<div id="profit" style="font-size:16px;font-weight:bold;color:#15803d;">5,131,010円</div>
</div>
<div style="background:#fef9c3;border-radius:8px;padding:12px;text-align:center;">
<div style="font-size:12px;color:#64748b;">非課税メリット</div>
<div id="taxSaved" style="font-size:16px;font-weight:bold;color:#a16207;">1,041,878円</div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>計算条件:</strong> 毎月定額積立、年利複利計算。NISA非課税枠で運用した場合の節税額は運用益の20.315%。実際の投資成果は市場状況により変動します。
</div>

</div>

<script>
function calc(){
  var m=parseInt(document.getElementById('monthly').value);
  var r=parseFloat(document.getElementById('rate').value)/100;
  var y=parseInt(document.getElementById('years').value);
  var mr=r/12;
  var n=y*12;
  var fv=m*((Math.pow(1+mr,n)-1)/mr);
  var p=m*n;
  var g=fv-p;
  var tax=Math.floor(g*0.20315);
  document.getElementById('monthlyVal').textContent=m.toLocaleString()+'円';
  document.getElementById('rateVal').textContent=(r*100).toFixed(1)+'%';
  document.getElementById('yearsVal').textContent=y+'年';
  document.getElementById('totalAsset').textContent=Math.floor(fv).toLocaleString()+'円';
  document.getElementById('principal').textContent=p.toLocaleString()+'円';
  document.getElementById('profit').textContent=Math.floor(g).toLocaleString()+'円';
  document.getElementById('taxSaved').textContent=tax.toLocaleString()+'円';
}
calc();
</script>

---

## この結果から次のアクションへ

シミュレーション結果を見て、NISAを始めたくなりましたか？

- **証券口座をまだお持ちでない方** → [楽天証券で口座開設する](https://hb.afl.rakuten.co.jp/hsc/41ab8a31.8f450617.41ab8a32.86e006c4/?link_type=hybrid_url&ut=eyJwYWdlIjoic2hvcCIsInR5cGUiOiJoeWJyaWRfdXJsIiwiY29sIjoxLCJjYXQiOiIxIiwiYmFuIjoiMTI0NjkzOSIsImFtcCI6ZmFsc2V9)
- **SBI証券と楽天証券で迷っている方** → [SBI証券 vs 楽天証券 徹底比較2026](/ja/posts/sbi-rakuten-hikaku-2026/)
- **NISAの始め方を知りたい方** → [新NISA始め方 初心者向け完全ガイド](/ja/posts/shin-nisa-hajimekata-shoshinsha-2026/)
- **おすすめ銘柄を知りたい方** → [NISAおすすめ銘柄2026](/ja/posts/nisa-osusume-meigara-2026/)

---

## よくある質問

**Q. このシミュレーターの計算は正確ですか？**
月次複利計算に基づく理論値です。実際の投資では市場変動があるため、これはあくまで参考値です。

**Q. 年利5%は現実的ですか？**
S&P500の過去30年平均リターンは年約10%、全世界株式は年約7-8%です。手数料を引いて5-7%が保守的な想定です。

**Q. NISAの非課税枠はいくらまでですか？**
新NISAでは年間360万円（つみたて投資枠120万円 + 成長投資枠240万円）、生涯非課税保有限度額は1,800万円です。

---

## 関連ツール・記事

- [FIREシミュレーター](/ja/tools/fire-simulator/) — FIRE（経済的自立）までの年数を計算
- [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/) — iDeCoの節税額と将来受取額を計算
- [年金シミュレーター](/ja/tools/nenkin-simulator/) — 将来の年金受給額を確認
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 年収から手取りを計算
- [教育費シミュレーター](/ja/tools/kyouikuhi-simulator/) — 子供の教育費総額を自動計算
- [積立NISAは毎月いくら？平均と最適額](/ja/posts/積立nisa-毎月いくら-平均/)
- [NISAとiDeCo、どちらを先に始めるべき？](/ja/posts/nisa-ideco-docchi-saki/)
- [投資信託おすすめ2026年版](/ja/posts/toushishintaku-osusume-2026/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [NISAで運用しながらFXもできる？税金の仕組みを比較してわかりやすく解説](/ja/posts/nisa-fx-zeikin-hikaku/)
- [新NISA始め方2026年版【初心者向け完全ガイド】口座開設から投資スタートまで](/ja/posts/shin-nisa-hajimekata-shoshinsha-2026/)
- [新NISA おすすめ銘柄 初心者向け完全ガイド【2026年最新版】](/ja/posts/nisa-osusume-meigara-2026/)
