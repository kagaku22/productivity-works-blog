---
title: "予算プランナー | 無料月次予算計算ツール"
date: 2025-11-07
draft: false
slug: "budget-planner"
aliases:
  - /ja/tools/budget-planner/
description: "無料の予算プランナー計算ツール。月収を入力するだけで50/30/20ルールに基づく推奨支出配分を瞬時に表示します。"
author: "Productivity Works Editorial"
categories:
  - "無料ツール"
tags:
  - "予算"
  - "計算ツール"
  - "個人ファイナンス"
  - "貯蓄"
  - "ツール"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/budget-planner.png"
  alt: "予算プランナー | 無料月次予算計算ツール"
  relative: false
---

*本ページにはアフィリエイトリンクが含まれています。*

# 予算プランナー | 50/30/20ルール計算ツール

月の手取り収入を入力して、50/30/20予算ルールに基づく**推奨支出配分**を確認しましょう。

<div id="budget-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">月の手取り収入（円）</label>
<input type="range" id="monthlyPay" min="100000" max="1500000" step="10000" value="500000" oninput="calcBudget()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>10万円</span><span id="payVal" style="font-weight:bold;font-size:18px;color:#2563eb;">50万円</span><span>150万円</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">月間貯蓄目標（20%）</div>
<div id="savingsAmt" style="font-size:36px;font-weight:bold;">10万円</div>
<div style="font-size:13px;margin-top:4px;">年間貯蓄額: <span id="savingsYearly" style="font-weight:bold;">120万円</span></div>
</div>

<div style="margin-bottom:16px;">

<div style="display:flex;align-items:center;padding:12px 0;border-bottom:1px solid #e2e8f0;">
<div style="width:16px;height:16px;border-radius:50%;background:#ef4444;margin-right:12px;flex-shrink:0;"></div>
<div style="flex:1;"><strong>必需費（50%）</strong><br><span style="font-size:13px;color:#64748b;">家賃・住居費、食費、光熱費、保険、交通費</span></div>
<div style="font-weight:bold;font-size:18px;" id="needsAmt">25万円</div>
</div>

<div style="display:flex;align-items:center;padding:12px 0;border-bottom:1px solid #e2e8f0;">
<div style="width:16px;height:16px;border-radius:50%;background:#f59e0b;margin-right:12px;flex-shrink:0;"></div>
<div style="flex:1;"><strong>欲しいもの（30%）</strong><br><span style="font-size:13px;color:#64748b;">外食、娯楽、買い物、趣味</span></div>
<div style="font-weight:bold;font-size:18px;" id="wantsAmt">15万円</div>
</div>

<div style="display:flex;align-items:center;padding:12px 0;border-bottom:1px solid #e2e8f0;">
<div style="width:16px;height:16px;border-radius:50%;background:#2563eb;margin-right:12px;flex-shrink:0;"></div>
<div style="flex:1;"><strong>貯蓄・借金返済（20%）</strong><br><span style="font-size:13px;color:#64748b;">緊急資金、投資、借金返済</span></div>
<div style="font-weight:bold;font-size:18px;" id="saveAmt">10万円</div>
</div>

</div>

<div style="background:#dcfce7;border-radius:8px;padding:16px;margin-bottom:16px;">
<div style="font-size:13px;color:#15803d;margin-bottom:4px;"><strong>20%を投資した場合の試算（年利7%）：</strong></div>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<div style="text-align:center;"><div style="font-size:12px;color:#64748b;">10年後</div><div id="invest10" style="font-weight:bold;color:#15803d;font-size:16px;">173万円</div></div>
<div style="text-align:center;"><div style="font-size:12px;color:#64748b;">30年後</div><div id="invest30" style="font-weight:bold;color:#15803d;font-size:16px;">1,220万円</div></div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>50/30/20ルールとは：</strong>エリザベス・ウォーレン上院議員が広めたシンプルな家計管理法。税引き後収入の50%を必需費、30%を欲しいもの、20%を貯蓄・借金返済に充てます。
</div>

</div>

<script>
function calcBudget(){
  var pay=parseInt(document.getElementById('monthlyPay').value);
  var needs=Math.floor(pay*0.5);
  var wants=Math.floor(pay*0.3);
  var save=Math.floor(pay*0.2);

  // Investment projections at 7% annual return
  var mr=0.07/12;
  var fv10=save*((Math.pow(1+mr,120)-1)/mr);
  var fv30=save*((Math.pow(1+mr,360)-1)/mr);

  function fmtJPY(n){return Math.floor(n/10000)+'万'+(Math.floor(n%10000)>0?Math.floor(n%10000)+'円':'円');}
  function fmtJPYSimple(n){
if(n>=10000){return Math.floor(n/10000).toLocaleString('ja-JP')+'万円';}
return n.toLocaleString('ja-JP')+'円';
  }

  document.getElementById('payVal').textContent=Math.floor(pay/10000)+'万円';
  document.getElementById('savingsAmt').textContent=Math.floor(save/10000)+'万円';
  document.getElementById('savingsYearly').textContent=Math.floor(save*12/10000)+'万円';
  document.getElementById('needsAmt').textContent=Math.floor(needs/10000)+'万円';
  document.getElementById('wantsAmt').textContent=Math.floor(wants/10000)+'万円';
  document.getElementById('saveAmt').textContent=Math.floor(save/10000)+'万円';
  document.getElementById('invest10').textContent=Math.floor(fv10/10000).toLocaleString('ja-JP')+'万円';
  document.getElementById('invest30').textContent=Math.floor(fv30/10000).toLocaleString('ja-JP')+'万円';
}
calcBudget();
</script>

---

## 予算の使い方

### 必需費（50%）の内訳
| カテゴリ | 収入に占める目安 |
|----------|----------------|
| 住居費（家賃・ローン） | 25〜30% |
| 食費 | 10〜15% |
| 光熱費 | 3〜5% |
| 交通費 | 5〜10% |
| 保険料 | 3〜5% |

### 20%貯蓄の使い道
1. **まず緊急資金** — 3〜6ヶ月分の生活費を高利回り普通預金口座に
2. **NISAやiDeCoを活用** — 税制優遇メリットを最大限に活用する
3. **残りを投資** — 低コストのインデックスファンドで長期運用

---

## よくある質問

**Q: 20%貯蓄できない場合は？**
まずできる金額から始めましょう。5%でもゼロよりはるかに良いです。自動積立を設定し、毎月1%ずつ増やしていきましょう。

**Q: 借金返済は20%に含めますか？**
最低返済額は「必需費（50%）」に含めます。追加の繰り上げ返済分は20%に含めてください。

**Q: 必需費が50%を超えてしまう場合は？**
生活費の高い地域ではよくあることです。最大の出費（通常は住居費）を減らす方法を探すか、収入を増やすことを検討しましょう。

---

## 次のステップ

- **貯蓄を投資に回す** — 毎月1万円でも、年利7%で20年間投資すれば約630万円以上になります
- **高利率の借金を先に返す** — 借金返済計画を立てましょう
- **実際の手取りを確認** — 正確な数字で予算を立てることが重要です

---

## 関連ツール

- [緊急資金計算ツール](/ja/tools/emergency-fund-calculator/) — 必要な緊急資金額を計算
- [配当収入計算ツール](/ja/tools/dividend-income-calculator/) — 投資からの配当収入を試算
- [FIREシミュレーター](/ja/tools/fire-calculator/) — 早期退職までの年数を計算

---

> 資産管理を効率化 → [freee会計で家計を自動管理](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)

## 関連記事

- [家計簿アプリから卒業：収入が月10万円超えたらfreeeに切り替える理由](/ja/posts/kakeibo-freee-kirikae-fukugyou/)
- [30代の保険見直し完全ガイド｜無料相談で年間5万円節約できるケースも](/ja/posts/30dai-hoken-minaoshi-guide/)
- [独身に生命保険は必要？｜20代・30代が本当に必要な保障額をデータで解説【2026年版】](/ja/posts/dokushin-hoken-hitsuyou-20dai-30dai/)
