---
title: "貯蓄目標シミュレーター｜目標額まで何ヶ月？無料計算ツール"
date: 2026-05-16
draft: false
slug: "chochiku-mokuhyo-simulator"
aliases:
  - /ja/tools/savings-goal-calculator/
description: "貯蓄目標シミュレーター。目標金額・現在の貯金額・毎月の積立額・想定利回りを入力して、目標達成までの期間を無料で計算できます。"
categories: ["無料ツール"]
tags: ["貯蓄", "シミュレーター", "家計管理", "資産形成", "計算ツール"]
author: "Productivity Works編集部"
ShowToc: false
ShowReadingTime: false
ShowWordCount: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/chochiku-mokuhyo-simulator.png"
  alt: "貯蓄目標シミュレーター"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 貯蓄目標シミュレーター

目標金額・現在の貯金額・毎月の積立額を入力して、**目標達成までの期間**を計算します。運用利回りを加味した場合の効果も一目でわかります。

<div id="cs-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI','Hiragino Sans',sans-serif;color:#1e293b;">

<div style="padding:24px;border:2px solid #7c3aed;border-radius:12px;background:#faf5ff;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">目標金額（万円）</label>
<input type="number" id="csGoal" min="1" max="100000" step="1" value="500" oninput="calcCS()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">現在の貯金額（万円）</label>
<input type="number" id="csCurrent" min="0" max="100000" step="1" value="50" oninput="calcCS()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:16px;">
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">毎月の積立額（万円）</label>
<input type="range" id="csMonthly" min="0.5" max="30" step="0.5" value="3" oninput="calcCS()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0.5万円</span><span id="csMonthlyVal" style="font-weight:bold;font-size:18px;color:#7c3aed;">3万円</span><span>30万円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">想定年利回り（%）</label>
<input type="range" id="csReturn" min="0" max="10" step="0.5" value="3" oninput="calcCS()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0%</span><span id="csReturnVal" style="font-weight:bold;font-size:18px;color:#7c3aed;">3.0%</span><span>10%</span></div>
</div>

<div style="margin-bottom:8px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">目的（参考）</label>
<select id="csPurpose" onchange="setPurpose()" style="width:100%;padding:10px;border:1px solid #cbd5e1;border-radius:8px;font-size:15px;">
<option value="custom">自由に設定</option>
<option value="emergency">緊急予備資金（生活費6ヶ月分）</option>
<option value="car">車の購入資金</option>
<option value="wedding">結婚資金</option>
<option value="education">教育資金</option>
<option value="house">住宅頭金</option>
<option value="retirement">老後資金2,000万円</option>
</select>
</div>

</div>

<!-- 結果 -->
<div id="csResults" style="margin-top:24px;padding:24px;border-radius:12px;background:#f5f3ff;border:1px solid #c4b5fd;">

<div style="text-align:center;margin-bottom:20px;">
<div style="font-size:14px;color:#64748b;">目標達成まで</div>
<div id="csTime" style="font-size:42px;font-weight:bold;color:#7c3aed;line-height:1.2;">11年 2ヶ月</div>
<div id="csDate" style="font-size:14px;color:#64748b;margin-top:4px;">達成予定: 2037年7月</div>
</div>

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;text-align:center;">
<div style="padding:16px;background:white;border-radius:8px;">
<div style="font-size:12px;color:#64748b;">積立総額</div>
<div id="csContributed" style="font-size:20px;font-weight:bold;color:#1e293b;">450万円</div>
</div>
<div style="padding:16px;background:white;border-radius:8px;">
<div style="font-size:12px;color:#64748b;">運用益</div>
<div id="csInterest" style="font-size:20px;font-weight:bold;color:#7c3aed;">50万円</div>
</div>
<div style="padding:16px;background:white;border-radius:8px;">
<div style="font-size:12px;color:#64748b;">最終残高</div>
<div id="csFinal" style="font-size:20px;font-weight:bold;color:#1e293b;">500万円</div>
</div>
</div>

<!-- プログレスバー -->
<div style="margin-top:20px;">
<div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:6px;">
<span>内訳</span>
<span id="csPctLabel">90% 積立 / 10% 運用益</span>
</div>
<div style="height:24px;background:#e2e8f0;border-radius:12px;overflow:hidden;display:flex;">
<div id="csBarCurrent" style="background:#94a3b8;height:100%;transition:width 0.3s;" title="現在の貯金"></div>
<div id="csBarContrib" style="background:#7c3aed;height:100%;transition:width 0.3s;" title="新規積立"></div>
<div id="csBarReturn" style="background:#a78bfa;height:100%;transition:width 0.3s;" title="運用益"></div>
</div>
<div style="display:flex;gap:16px;font-size:12px;color:#64748b;margin-top:6px;">
<span><span style="display:inline-block;width:10px;height:10px;background:#94a3b8;border-radius:2px;"></span> 現在の貯金</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#7c3aed;border-radius:2px;"></span> 新規積立</span>
<span><span style="display:inline-block;width:10px;height:10px;background:#a78bfa;border-radius:2px;"></span> 運用益</span>
</div>
</div>

<!-- 年次推移表 -->
<details style="margin-top:20px;">
<summary style="cursor:pointer;font-weight:bold;color:#7c3aed;font-size:15px;">年次推移を表示</summary>
<div style="overflow-x:auto;margin-top:12px;">
<table id="csTable" style="width:100%;border-collapse:collapse;font-size:14px;">
<thead>
<tr style="background:#7c3aed;color:white;">
<th style="padding:8px;text-align:left;">年</th>
<th style="padding:8px;text-align:right;">積立額</th>
<th style="padding:8px;text-align:right;">運用益</th>
<th style="padding:8px;text-align:right;">残高</th>
</tr>
</thead>
<tbody id="csTableBody"></tbody>
</table>
</div>
</details>

</div>

<!-- シナリオ比較 -->
<div style="margin-top:24px;padding:24px;border-radius:12px;background:#f8fafc;border:1px solid #e2e8f0;">
<h3 style="margin:0 0 16px 0;font-size:18px;">もっと早く達成するには？</h3>
<div id="csScenarios" style="display:grid;gap:8px;"></div>
</div>

<!-- 運用あり vs なし比較 -->
<div style="margin-top:24px;padding:24px;border-radius:12px;background:#fffbeb;border:1px solid #fde68a;">
<h3 style="margin:0 0 12px 0;font-size:18px;">運用ありvs貯金のみ</h3>
<div id="csComparison" style="display:grid;grid-template-columns:1fr 1fr;gap:12px;"></div>
</div>

</div>

<script>
function calcCS(){
  const goalMan=parseFloat(document.getElementById('csGoal').value)||0;
  const currentMan=parseFloat(document.getElementById('csCurrent').value)||0;
  const monthlyMan=parseFloat(document.getElementById('csMonthly').value)||0;
  const annualReturn=parseFloat(document.getElementById('csReturn').value)/100;
  const monthlyReturn=annualReturn/12;

  const goal=goalMan*10000;
  const current=currentMan*10000;
  const monthly=monthlyMan*10000;

  document.getElementById('csMonthlyVal').textContent=monthlyMan+'万円';
  document.getElementById('csReturnVal').textContent=(annualReturn*100).toFixed(1)+'%';

  if(goal<=current){
    document.getElementById('csTime').textContent='既に達成済み！';
    document.getElementById('csDate').textContent='現在の貯金が目標額を超えています。';
    document.getElementById('csContributed').textContent='0万円';
    document.getElementById('csInterest').textContent='0万円';
    document.getElementById('csFinal').textContent=currentMan+'万円';
    document.getElementById('csBarCurrent').style.width='100%';
    document.getElementById('csBarContrib').style.width='0%';
    document.getElementById('csBarReturn').style.width='0%';
    document.getElementById('csPctLabel').textContent='目標達成済み';
    document.getElementById('csTableBody').innerHTML='';
    document.getElementById('csScenarios').innerHTML='';
    document.getElementById('csComparison').innerHTML='';
    return;
  }

  if(monthly<=0){
    document.getElementById('csTime').textContent='積立額を設定してください';
    document.getElementById('csDate').textContent='毎月の積立額が必要です。';
    return;
  }

  const result=computeM(goal,current,monthly,monthlyReturn);
  const months=result.months;
  const years=Math.floor(months/12);
  const remMonths=months%12;

  let timeStr='';
  if(years>0) timeStr+=years+'年';
  if(remMonths>0) timeStr+=(years>0?' ':'')+remMonths+'ヶ月';
  if(months===0) timeStr='1ヶ月以内';
  if(months>600){timeStr='50年以上';document.getElementById('csDate').textContent='積立額または利回りを上げましょう。';}
  else{
    const td=new Date();
    td.setMonth(td.getMonth()+months);
    document.getElementById('csDate').textContent='達成予定: '+td.getFullYear()+'年'+(td.getMonth()+1)+'月';
  }
  document.getElementById('csTime').textContent=timeStr;

  const totalContributed=current+monthly*months;
  const interestEarned=result.finalBalance-totalContributed;
  const newContributions=monthly*months;

  document.getElementById('csContributed').textContent=Math.round(totalContributed/10000)+'万円';
  document.getElementById('csInterest').textContent=Math.max(0,Math.round(interestEarned/10000))+'万円';
  document.getElementById('csFinal').textContent=Math.round(result.finalBalance/10000)+'万円';

  const fb=result.finalBalance;
  const pC=((current/fb)*100).toFixed(1);
  const pN=((newContributions/fb)*100).toFixed(1);
  const pR=(((fb-totalContributed)/fb)*100).toFixed(1);
  document.getElementById('csBarCurrent').style.width=pC+'%';
  document.getElementById('csBarContrib').style.width=pN+'%';
  document.getElementById('csBarReturn').style.width=Math.max(0,pR)+'%';
  document.getElementById('csPctLabel').textContent=Math.round(parseFloat(pC)+parseFloat(pN))+'% 積立 / '+Math.max(0,Math.round(pR))+'% 運用益';

  // 年次推移表
  let tbody='';
  let balance=current;
  const totalYears=Math.ceil(months/12);
  for(let y=1;y<=Math.min(totalYears,40);y++){
    const mty=y===totalYears?(months%12||12):12;
    let yc=0,yr=0;
    for(let m=0;m<mty;m++){
      const ret=balance*monthlyReturn;
      yr+=ret;balance+=ret+monthly;yc+=monthly;
      if(balance>=goal){balance=Math.max(balance,goal);break;}
    }
    const bg=y%2===0?'#f5f3ff':'white';
    tbody+='<tr style="background:'+bg+'"><td style="padding:8px;">'+y+'年目</td><td style="padding:8px;text-align:right;">'+Math.round(yc/10000)+'万円</td><td style="padding:8px;text-align:right;color:#7c3aed;">'+Math.round(yr/10000)+'万円</td><td style="padding:8px;text-align:right;font-weight:bold;">'+Math.round(Math.min(balance,goal*1.1)/10000)+'万円</td></tr>';
    if(balance>=goal) break;
  }
  document.getElementById('csTableBody').innerHTML=tbody;

  // シナリオ比較
  const scenarios=[monthlyMan*1.5,monthlyMan*2,monthlyMan*3].filter(s=>s<=50);
  let sHTML='';
  scenarios.forEach(s=>{
    const r=computeM(goal,current,s*10000,monthlyReturn);
    const sy=Math.floor(r.months/12);
    const sm=r.months%12;
    let st='';
    if(sy>0)st+=sy+'年';
    if(sm>0)st+=(sy>0?' ':'')+sm+'ヶ月';
    const saved=months-r.months;
    sHTML+='<div style="display:flex;justify-content:space-between;align-items:center;padding:12px;background:white;border-radius:8px;border:1px solid #e2e8f0;">';
    sHTML+='<div><strong>月'+s+'万円</strong></div>';
    sHTML+='<div style="text-align:right;"><span style="font-weight:bold;">'+st+'</span>';
    if(saved>0)sHTML+=' <span style="color:#7c3aed;font-size:13px;">('+saved+'ヶ月短縮)</span>';
    sHTML+='</div></div>';
  });
  document.getElementById('csScenarios').innerHTML=sHTML;

  // 運用あり vs なし
  const noInvest=computeM(goal,current,monthly,0);
  const diffMonths=noInvest.months-months;
  let cHTML='';
  cHTML+='<div style="padding:16px;background:white;border-radius:8px;text-align:center;border:2px solid #7c3aed;"><div style="font-size:12px;color:#64748b;">運用あり（年利'+((annualReturn*100).toFixed(1))+'%）</div><div style="font-size:24px;font-weight:bold;color:#7c3aed;">'+timeStr+'</div></div>';
  const ny=Math.floor(noInvest.months/12);const nm=noInvest.months%12;
  let nt='';if(ny>0)nt+=ny+'年';if(nm>0)nt+=(ny>0?' ':'')+nm+'ヶ月';
  if(noInvest.months>600)nt='50年以上';
  cHTML+='<div style="padding:16px;background:white;border-radius:8px;text-align:center;border:1px solid #e2e8f0;"><div style="font-size:12px;color:#64748b;">貯金のみ（利回り0%）</div><div style="font-size:24px;font-weight:bold;color:#94a3b8;">'+nt+'</div>';
  if(diffMonths>0&&noInvest.months<=600)cHTML+='<div style="font-size:13px;color:#ef4444;margin-top:4px;">'+diffMonths+'ヶ月遅い</div>';
  cHTML+='</div>';
  document.getElementById('csComparison').innerHTML=cHTML;
}

function computeM(goal,current,monthly,monthlyReturn){
  let balance=current;let months=0;
  while(balance<goal&&months<600){balance+=balance*monthlyReturn;balance+=monthly;months++;}
  return{months:months,finalBalance:balance};
}

function setPurpose(){
  const p=document.getElementById('csPurpose').value;
  const presets={emergency:{goal:150,current:0,monthly:3,ret:0},car:{goal:300,current:50,monthly:5,ret:0},wedding:{goal:350,current:50,monthly:5,ret:0},education:{goal:1000,current:0,monthly:3,ret:3},house:{goal:1000,current:100,monthly:5,ret:3},retirement:{goal:2000,current:0,monthly:5,ret:5}};
  if(presets[p]){
    document.getElementById('csGoal').value=presets[p].goal;
    document.getElementById('csCurrent').value=presets[p].current;
    document.getElementById('csMonthly').value=presets[p].monthly;
    document.getElementById('csReturn').value=presets[p].ret;
    calcCS();
  }
}

calcCS();
</script>

---

## 使い方

1. **目標金額を入力** — 緊急予備資金、車、結婚、住宅頭金、老後資金など
2. **現在の貯金額を入力** — すでに貯めている額
3. **毎月の積立額を調整** — 毎月いくら貯金・投資するか
4. **想定利回りを設定** — 普通預金なら0%、投資信託なら3〜7%が目安

「目的」プルダウンから選択すると、一般的な金額がプリセットされます。

---

## 貯蓄目標の目安

| 目的 | 目標金額の目安 | 推奨期間 |
|---|---|---|
| 緊急予備資金 | 生活費3〜6ヶ月分（100〜200万円） | 6〜18ヶ月 |
| 車の購入 | 200〜400万円 | 1〜3年 |
| 結婚資金 | 300〜500万円 | 1〜3年 |
| 教育資金（1人分） | 500〜1,500万円 | 10〜18年 |
| 住宅頭金 | 500〜1,500万円 | 3〜10年 |
| 老後資金 | 1,500〜3,000万円 | 20〜35年 |

---

## 目標達成を早めるコツ

### 1. 先取り貯蓄を徹底する

給料日に自動振替で貯蓄口座に移す「先取り貯蓄」が最も確実です。残ったお金で生活する習慣をつけましょう。

### 2. 長期目標は「運用」を組み合わせる

5年以上の目標なら、新NISAやiDeCoを活用した投資信託での積立がおすすめです。年利3〜5%でも、複利効果で大きな差が出ます。

### 3. 固定費を見直す

携帯料金、保険料、サブスクリプションなど固定費を月1万円削減すれば、年間12万円が貯蓄に回ります。

### 4. 副業収入を丸ごと貯蓄に回す

本業の給料で生活し、副業収入は全額貯蓄に回すと、目標達成が大幅に早まります。

---

## 関連ツール

> 複利効果で資産がどう増えるか確認 → [複利計算シミュレーター](/ja/tools/fukuri-keisan/)
> 月収から理想の支出配分を計算 → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)
> 年収から手取りを計算 → [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)
> 新NISAの非課税効果を計算 → [NISAシミュレーター](/ja/tools/nisa-simulator/)
> 老後に必要な資金を計算 → [年金シミュレーター](/ja/tools/nenkin-simulator/)
> 子供の教育費総額を計算 → [教育費シミュレーター](/ja/tools/kyouikuhi-simulator/)

---

## 関連記事

- [老後2,000万円問題の対策](/ja/posts/rougo-2000man-taisaku/)
- [新NISA始め方](/ja/posts/shin-nisa-hajimekata-shoshinsha-2026/)
- [30代の保険見直しガイド](/ja/posts/30dai-hoken-minaoshi-guide/)
- [副業の始め方](/ja/posts/副業-始め方-初心者-2026/)

---

## Productivity Worksの無料ツール

当サイトの計算ツールはすべて**完全無料**、ブラウザ上で動作し、データは一切保存されません。

[全ツール一覧はこちら](/ja/tools/)

> 副業や投資で収入が増えてきたら、確定申告の準備も早めに始めましょう。<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freee会計</a>なら銀行口座・クレジットカードと連携して収支を自動記録し、確定申告書類もガイドに沿って作成できます。

*本記事にはアフィリエイトリンクが含まれています。読者の皆様に追加費用は発生しません。*
