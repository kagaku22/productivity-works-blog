---
title: "借金返済シミュレーター｜雪だるま式vs高金利優先を比較【無料】"
date: 2026-05-16
draft: false
slug: "shakkin-hensai-simulator"
description: "複数の借金の返済計画を自動計算。雪だるま式（少額優先）と高金利優先（利息節約）を比較して、最速で借金ゼロになるプランを見つけましょう。無料シミュレーター。"
author: "Productivity Works編集部"
categories:
  - "マネー・個人金融"
tags:
  - "借金返済"
  - "シミュレーター"
  - "リボ払い"
  - "カードローン"
  - "債務整理"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/shakkin-hensai-simulator.png"
  alt: "借金返済シミュレーター｜雪だるま式vs高金利優先を比較"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 借金返済シミュレーター

借入先ごとの残高・金利・月々の返済額を入力して、**最短で完済する返済プラン**を見つけましょう。

<div id="dp-calc" style="max-width:720px;margin:0 auto;">

<div style="padding:24px;border:2px solid #dc2626;border-radius:12px;background:#fef2f2;">

<h3 style="margin:0 0 16px;color:#991b1b;font-size:16px;">借入一覧</h3>

<div id="debtList"></div>

<button onclick="addDebt()" style="margin-top:12px;padding:8px 20px;background:#dc2626;color:#fff;border:none;border-radius:8px;font-size:14px;cursor:pointer;">＋ 借入を追加</button>

<div style="margin-top:20px;padding-top:16px;border-top:1px solid #fca5a5;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">追加返済額（月額）</label>
<input type="range" id="extraPay" min="0" max="100000" step="1000" value="10000" oninput="calcDP()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0円</span><span id="extraVal" style="font-weight:bold;font-size:18px;color:#059669;">10,000円</span><span>100,000円</span></div>
<div style="font-size:12px;color:#64748b;margin-top:4px;">※最低返済額に上乗せして返済する金額</div>
</div>

</div>

<div id="dpResult" style="margin-top:24px;"></div>

<div style="margin-top:24px;padding:24px;border:2px solid #7c3aed;border-radius:12px;background:#faf5ff;">
<h3 style="margin:0 0 16px;color:#6d28d9;font-size:16px;">返済推移グラフ</h3>
<canvas id="dpChart" width="680" height="280" style="width:100%;height:auto;"></canvas>
</div>

</div>

<script>
var debts=[];
var debtId=0;

function addDebt(name,bal,rate,minPay){
  debts.push({id:debtId++,name:name||'借入'+(debts.length+1),balance:bal||500000,rate:rate||15,minPay:minPay||15000});
  renderDebts();
  calcDP();
}

function removeDebt(id){
  debts=debts.filter(function(d){return d.id!==id;});
  renderDebts();
  calcDP();
}

function updateDebt(id,field,val){
  for(var i=0;i<debts.length;i++){
    if(debts[i].id===id){debts[i][field]=field==='name'?val:+val;break;}
  }
  calcDP();
}

function renderDebts(){
  var html='';
  for(var i=0;i<debts.length;i++){
    var d=debts[i];
    html+='<div style="padding:12px;margin-bottom:8px;background:#fff;border-radius:8px;border:1px solid #fca5a5;">';
    html+='<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">';
    html+='<input type="text" value="'+d.name+'" onchange="updateDebt('+d.id+',\'name\',this.value)" style="border:none;font-weight:bold;font-size:14px;color:#991b1b;width:60%;outline:none;">';
    html+='<button onclick="removeDebt('+d.id+')" style="background:none;border:none;color:#ef4444;cursor:pointer;font-size:18px;">×</button>';
    html+='</div>';
    html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;">';
    html+='<div><label style="display:block;font-size:11px;color:#64748b;">残高（円）</label><input type="number" value="'+d.balance+'" onchange="updateDebt('+d.id+',\'balance\',this.value)" style="width:100%;padding:6px;border:1px solid #cbd5e1;border-radius:4px;font-size:13px;"></div>';
    html+='<div><label style="display:block;font-size:11px;color:#64748b;">年利（%）</label><input type="number" value="'+d.rate+'" step="0.1" onchange="updateDebt('+d.id+',\'rate\',this.value)" style="width:100%;padding:6px;border:1px solid #cbd5e1;border-radius:4px;font-size:13px;"></div>';
    html+='<div><label style="display:block;font-size:11px;color:#64748b;">月々返済額（円）</label><input type="number" value="'+d.minPay+'" onchange="updateDebt('+d.id+',\'minPay\',this.value)" style="width:100%;padding:6px;border:1px solid #cbd5e1;border-radius:4px;font-size:13px;"></div>';
    html+='</div></div>';
  }
  document.getElementById('debtList').innerHTML=html;
}

function fmt(n){return Math.round(n).toLocaleString();}

function simulate(sortFn,extra){
  var ds=debts.map(function(d){return{name:d.name,balance:d.balance,rate:d.rate,minPay:d.minPay};});
  var totalPaid=0,months=0,history=[getTotalBal(ds)];
  var maxMonths=600;
  while(getTotalBal(ds)>0&&months<maxMonths){
    months++;
    ds.sort(sortFn);
    var leftover=extra;
    for(var i=0;i<ds.length;i++){
      if(ds[i].balance<=0)continue;
      var interest=ds[i].balance*(ds[i].rate/100/12);
      ds[i].balance+=interest;
      var pay=Math.min(ds[i].balance,ds[i].minPay);
      ds[i].balance-=pay;
      totalPaid+=pay;
    }
    for(var i=0;i<ds.length;i++){
      if(ds[i].balance<=0||leftover<=0)continue;
      var ep=Math.min(ds[i].balance,leftover);
      ds[i].balance-=ep;
      leftover-=ep;
      totalPaid+=ep;
    }
    history.push(getTotalBal(ds));
  }
  return{months:months,totalPaid:totalPaid,history:history};
}

function getTotalBal(ds){
  var t=0;for(var i=0;i<ds.length;i++)t+=Math.max(0,ds[i].balance);return t;
}

function calcDP(){
  if(debts.length===0)return;
  var extra=+document.getElementById('extraPay').value;
  document.getElementById('extraVal').textContent=fmt(extra)+'円';

  var totalBal=0,totalMin=0;
  for(var i=0;i<debts.length;i++){totalBal+=debts[i].balance;totalMin+=debts[i].minPay;}

  var snowball=simulate(function(a,b){return a.balance-b.balance;},extra);
  var avalanche=simulate(function(a,b){return b.rate-a.rate;},extra);
  var noExtra=simulate(function(a,b){return b.rate-a.rate;},0);

  var snowInt=snowball.totalPaid-totalBal;
  var avaInt=avalanche.totalPaid-totalBal;
  var noExInt=noExtra.totalPaid-totalBal;
  var best=avaInt<=snowInt?'avalanche':'snowball';
  var saved=Math.max(0,noExInt-Math.min(snowInt,avaInt));

  var html='<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;">';

  var sBorder=best==='snowball'?'2px solid #059669':'1px solid #e2e8f0';
  var sBadge=best==='snowball'?'<span style="background:#dcfce7;color:#166534;font-size:11px;font-weight:700;padding:2px 8px;border-radius:4px;margin-left:8px;">最適</span>':'';
  html+='<div style="padding:20px;border-radius:12px;border:'+sBorder+';background:#fff;">';
  html+='<div style="font-size:14px;font-weight:bold;color:#dc2626;margin-bottom:12px;">雪だるま式'+sBadge+'</div>';
  html+='<div style="font-size:12px;color:#64748b;">少額の借入から優先返済</div>';
  html+='<div style="font-size:28px;font-weight:bold;margin:8px 0;">'+snowball.months+'<span style="font-size:14px;">ヶ月</span></div>';
  html+='<div style="font-size:13px;color:#64748b;">支払利息合計: <strong>'+fmt(snowInt)+'円</strong></div>';
  html+='<div style="font-size:13px;color:#64748b;">総返済額: '+fmt(snowball.totalPaid)+'円</div>';
  html+='</div>';

  var aBorder=best==='avalanche'?'2px solid #059669':'1px solid #e2e8f0';
  var aBadge=best==='avalanche'?'<span style="background:#dcfce7;color:#166534;font-size:11px;font-weight:700;padding:2px 8px;border-radius:4px;margin-left:8px;">最適</span>':'';
  html+='<div style="padding:20px;border-radius:12px;border:'+aBorder+';background:#fff;">';
  html+='<div style="font-size:14px;font-weight:bold;color:#7c3aed;margin-bottom:12px;">高金利優先'+aBadge+'</div>';
  html+='<div style="font-size:12px;color:#64748b;">金利が高い借入から優先返済</div>';
  html+='<div style="font-size:28px;font-weight:bold;margin:8px 0;">'+avalanche.months+'<span style="font-size:14px;">ヶ月</span></div>';
  html+='<div style="font-size:13px;color:#64748b;">支払利息合計: <strong>'+fmt(avaInt)+'円</strong></div>';
  html+='<div style="font-size:13px;color:#64748b;">総返済額: '+fmt(avalanche.totalPaid)+'円</div>';
  html+='</div>';
  html+='</div>';

  if(saved>0){
    html+='<div style="margin-top:16px;padding:16px;background:#f0fdf4;border-radius:8px;text-align:center;">';
    html+='<div style="font-size:13px;color:#64748b;">毎月'+fmt(extra)+'円の追加返済で</div>';
    html+='<div style="font-size:24px;font-weight:bold;color:#059669;">'+fmt(saved)+'円の利息を節約</div>';
    html+='<div style="font-size:13px;color:#64748b;">完済が'+(noExtra.months-Math.min(snowball.months,avalanche.months))+'ヶ月早くなります</div>';
    html+='</div>';
  }

  document.getElementById('dpResult').innerHTML=html;
  drawDPChart(snowball,avalanche,noExtra);
}

function drawDPChart(snow,ava,noEx){
  var c=document.getElementById('dpChart');
  var ctx=c.getContext('2d');
  var W=c.width,H=c.height;
  ctx.clearRect(0,0,W,H);

  var maxM=Math.max(snow.months,ava.months,noEx.months,12);
  maxM=Math.ceil(maxM*1.1);
  var maxVal=Math.max(snow.history[0],1);
  var pad={t:20,r:20,b:45,l:80};
  var cw=W-pad.l-pad.r,ch=H-pad.t-pad.b;

  ctx.strokeStyle='#e2e8f0';ctx.lineWidth=1;
  for(var i=0;i<=4;i++){
    var y=pad.t+ch*(1-i/4);
    ctx.beginPath();ctx.moveTo(pad.l,y);ctx.lineTo(W-pad.r,y);ctx.stroke();
    ctx.fillStyle='#94a3b8';ctx.font='11px sans-serif';ctx.textAlign='right';
    ctx.fillText(fmt(maxVal*i/4)+'円',pad.l-6,y+4);
  }

  function drawLine(hist,color,dash){
    ctx.beginPath();ctx.strokeStyle=color;ctx.lineWidth=2;ctx.setLineDash(dash||[]);
    for(var m=0;m<hist.length&&m<=maxM;m++){
      var x=pad.l+cw*m/maxM,y=pad.t+ch*(1-hist[m]/maxVal);
      if(m===0)ctx.moveTo(x,y);else ctx.lineTo(x,y);
    }
    ctx.stroke();ctx.setLineDash([]);
  }

  drawLine(noEx.history,'#94a3b8',[4,4]);
  drawLine(snow.history,'#dc2626',[]);
  drawLine(ava.history,'#7c3aed',[]);

  var lx=pad.l+10,ly=pad.t+12;
  [[' 雪だるま式','#dc2626'],[' 高金利優先','#7c3aed'],[' 最低返済のみ','#94a3b8']].forEach(function(item,i){
    ctx.fillStyle=item[1];ctx.fillRect(lx,ly+i*16,12,3);
    ctx.fillStyle='#334155';ctx.font='11px sans-serif';ctx.textAlign='left';
    ctx.fillText(item[0],lx+16,ly+i*16+5);
  });

  ctx.fillStyle='#64748b';ctx.font='11px sans-serif';ctx.textAlign='center';
  var step=maxM<=12?1:maxM<=24?3:maxM<=48?6:12;
  for(var m=0;m<=maxM;m+=step){
    ctx.fillText(m+'月',pad.l+cw*m/maxM,H-pad.b+20);
  }
}

addDebt('リボ払い',500000,15,15000);
addDebt('カードローン',800000,8,20000);
addDebt('消費者金融',200000,18,10000);
</script>

---

## 雪だるま式 vs 高金利優先：どちらを選ぶ？

| 方法 | 仕組み | おすすめの人 |
|---|---|---|
| **雪だるま式** | 残高が少ない借入から優先返済 | 小さな成功体験でモチベーションを保ちたい人 |
| **高金利優先** | 金利が高い借入から優先返済 | 利息を最小化して合理的に返済したい人 |

**高金利優先**が数学的には最適（支払利息が最小）。ただし**雪だるま式**は借入件数が早く減るため、心理的な達成感を得やすいメリットがあります。

### 追加返済の仕組み

どちらの方法でも、すべての借入に最低返済額を支払った上で、余剰資金を優先度の高い借入に集中投入します。1件完済すると、その分の返済額が次の借入に「雪だるま」のように加算されていきます。

### 早く完済するコツ

1. **追加返済額を増やす** — 月5,000円の上乗せでも返済期間と利息に大きな差が出ます
2. **臨時収入を活用** — ボーナス・還付金・副業収入を返済に回す
3. **金利交渉をする** — カードローンは金利引き下げの交渉が可能な場合があります
4. **新規借入を止める** — リボ払いの新規利用を停止し、残高を減らすことに集中

---

## よくある質問

**Q: リボ払いの金利は何%ですか？**
一般的なリボ払いの金利は年15〜18%です。カードローンは年3〜15%、消費者金融は年15〜18%が目安です。

**Q: 過払い金は計算に含まれますか？**
このシミュレーターは将来の返済計画のみを計算します。過払い金（2010年以前の年20%超の借入）については専門家に相談してください。

**Q: 繰上返済の手数料は？**
カードローンや消費者金融は繰上返済手数料が無料の場合がほとんどです。住宅ローンは別途手数料がかかる場合があるため、契約書を確認してください。

---

> 借金返済と並行して家計管理を始めましょう。**[freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)**なら収支の可視化から確定申告まで一元管理。副業で返済を加速したいフリーランスの方にもおすすめです。

---

## 関連ツール

- [家計簿シミュレーター](/ja/tools/kakeibo-generator/) — 月収から理想の支出配分を計算
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/) — 年収から手取りを計算
- [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/) — 副業収入の税金を計算
- [複利計算シミュレーター](/ja/tools/fukuri-keisan/) — 完済後の積立投資をシミュレーション
- [住宅ローンシミュレーター](/ja/tools/jutaku-loan-simulator/) — 住宅ローンの返済計画を計算
