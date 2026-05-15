---
title: "住宅ローンシミュレーター｜月々返済額・総返済額を自動計算【2026年版】"
date: 2026-05-16
draft: false
slug: "jutaku-loan-simulator"
description: "住宅ローンの月々返済額・総返済額・利息総額を自動計算。借入額・金利・返済期間を入力するだけ。元利均等・元金均等の比較、繰上返済シミュレーションも対応。"
author: "Productivity Works編集部"
categories:
  - "マネー・個人金融"
tags:
  - "住宅ローン"
  - "シミュレーション"
  - "不動産"
  - "計算ツール"
  - "返済額"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/jutaku-loan-simulator.png"
  alt: "住宅ローンシミュレーター｜月々返済額・総返済額を自動計算"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# 住宅ローンシミュレーター【2026年版】

借入額・金利・返済期間を入力するだけで、**月々の返済額**・**総返済額**・**利息総額**を自動計算します。元利均等返済と元金均等返済の比較もできます。

<div id="loan-calc" style="max-width:680px;margin:0 auto;font-family:'Noto Sans JP',sans-serif;">

<div style="padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">借入額（万円）</label>
<input type="range" id="principal" min="500" max="10000" step="100" value="3500" oninput="calcLoan()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>500万</span><span id="principalVal" style="font-weight:bold;font-size:18px;color:#2563eb;">3,500万円</span><span>1億円</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">金利（年利 %）</label>
<input type="range" id="rate" min="0.1" max="3.0" step="0.05" value="0.65" oninput="calcLoan()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>0.1%</span><span id="rateVal" style="font-weight:bold;font-size:18px;color:#2563eb;">0.65%</span><span>3.0%</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">返済期間（年）</label>
<input type="range" id="years" min="5" max="40" step="1" value="35" oninput="calcLoan()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>5年</span><span id="yearsVal" style="font-weight:bold;font-size:18px;color:#2563eb;">35年</span><span>40年</span></div>
</div>

<div style="margin-bottom:20px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">返済方式</label>
<div style="display:flex;gap:16px;">
<label style="cursor:pointer;"><input type="radio" name="method" value="equal_payment" checked onchange="calcLoan()"> 元利均等返済</label>
<label style="cursor:pointer;"><input type="radio" name="method" value="equal_principal" onchange="calcLoan()"> 元金均等返済</label>
</div>
<div style="font-size:12px;color:#64748b;margin-top:4px;">元利均等：毎月同額返済　/　元金均等：元金を均等返済（初期負担大・総利息少）</div>
</div>

<div id="result" style="margin-top:24px;padding:20px;background:#fff;border-radius:8px;border:1px solid #e2e8f0;"></div>

</div>

<div id="chart-section" style="margin-top:24px;padding:24px;border:2px solid #10b981;border-radius:12px;background:#f0fdf4;">
<h3 style="margin:0 0 16px;color:#166534;font-size:16px;">返済推移グラフ</h3>
<canvas id="loanChart" width="640" height="300" style="width:100%;height:auto;"></canvas>
</div>

<div style="margin-top:24px;padding:24px;border:2px solid #f59e0b;border-radius:12px;background:#fffbeb;">
<h3 style="margin:0 0 12px;color:#92400e;font-size:16px;">金利別 月々返済額の比較（借入額 <span id="compareLabel">3,500万円</span>・35年）</h3>
<div id="rateCompare"></div>
</div>

</div>

<script>
function fmt(n){return n.toLocaleString('ja-JP');}

function calcLoan(){
  var P=+document.getElementById('principal').value;
  var r=+document.getElementById('rate').value;
  var Y=+document.getElementById('years').value;
  var method=document.querySelector('input[name="method"]:checked').value;

  document.getElementById('principalVal').textContent=fmt(P)+'万円';
  document.getElementById('rateVal').textContent=r.toFixed(2)+'%';
  document.getElementById('yearsVal').textContent=Y+'年';

  var Pyen=P*10000;
  var mr=r/100/12;
  var n=Y*12;
  var monthly,totalPay,totalInterest;
  var balances=[],interests=[],principals=[];

  if(method==='equal_payment'){
    if(mr===0){monthly=Pyen/n;}
    else{monthly=Pyen*mr*Math.pow(1+mr,n)/(Math.pow(1+mr,n)-1);}
    totalPay=monthly*n;
    totalInterest=totalPay-Pyen;
    var bal=Pyen;
    for(var y=0;y<=Y;y++){
      balances.push(Math.round(bal/10000));
      if(y<Y){
        var yInt=0,yPrin=0;
        for(var m=0;m<12;m++){
          var intPart=bal*mr;
          var prinPart=monthly-intPart;
          yInt+=intPart;yPrin+=prinPart;bal-=prinPart;
        }
        interests.push(Math.round(yInt/10000));
        principals.push(Math.round(yPrin/10000));
      }
    }
  }else{
    var prinPerMonth=Pyen/n;
    totalPay=0;totalInterest=0;
    var bal=Pyen;
    var firstMonth=prinPerMonth+bal*mr;
    for(var y=0;y<=Y;y++){
      balances.push(Math.round(bal/10000));
      if(y<Y){
        var yInt=0,yPrin=0;
        for(var m=0;m<12;m++){
          var intPart=bal*mr;
          var pay=prinPerMonth+intPart;
          totalPay+=pay;totalInterest+=intPart;
          yPrin+=prinPerMonth;yInt+=intPart;bal-=prinPerMonth;
        }
        interests.push(Math.round(yInt/10000));
        principals.push(Math.round(yPrin/10000));
      }
    }
    if(method==='equal_payment'){monthly=monthly;}
    else{monthly=firstMonth;}
  }

  if(method==='equal_payment'){
    totalPay=monthly*n;totalInterest=totalPay-Pyen;
  }

  var html='<div style="text-align:center;margin-bottom:16px;">';
  html+='<div style="font-size:14px;color:#64748b;">月々の返済額'+(method==='equal_principal'?'（初月）':'')+'</div>';
  html+='<div style="font-size:36px;font-weight:bold;color:#2563eb;">'+fmt(Math.round(monthly))+'<span style="font-size:16px;">円</span></div>';
  html+='</div>';
  html+='<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;text-align:center;">';
  html+='<div style="padding:12px;background:#f1f5f9;border-radius:8px;"><div style="font-size:12px;color:#64748b;">借入額</div><div style="font-size:18px;font-weight:bold;">'+fmt(P)+'<span style="font-size:12px;">万円</span></div></div>';
  html+='<div style="padding:12px;background:#fef2f2;border-radius:8px;"><div style="font-size:12px;color:#64748b;">利息総額</div><div style="font-size:18px;font-weight:bold;color:#dc2626;">'+fmt(Math.round(totalInterest/10000))+'<span style="font-size:12px;">万円</span></div></div>';
  html+='<div style="padding:12px;background:#eff6ff;border-radius:8px;"><div style="font-size:12px;color:#64748b;">総返済額</div><div style="font-size:18px;font-weight:bold;color:#1e40af;">'+fmt(Math.round(totalPay/10000))+'<span style="font-size:12px;">万円</span></div></div>';
  html+='</div>';

  if(method==='equal_principal'){
    var lastMonth=prinPerMonth+prinPerMonth*mr;
    html+='<div style="margin-top:12px;text-align:center;font-size:13px;color:#64748b;">最終月の返済額: <strong>'+fmt(Math.round(lastMonth))+'円</strong></div>';
  }

  document.getElementById('result').innerHTML=html;

  drawChart(balances,interests,principals,Y);
  drawRateCompare(P,Y);
}

function drawChart(balances,interests,principals,Y){
  var c=document.getElementById('loanChart');
  var ctx=c.getContext('2d');
  var W=c.width,H=c.height;
  ctx.clearRect(0,0,W,H);

  var maxBal=Math.max.apply(null,balances);
  if(maxBal===0)maxBal=1;
  var pad={t:20,r:20,b:40,l:60};
  var cw=W-pad.l-pad.r,ch=H-pad.t-pad.b;

  ctx.strokeStyle='#e2e8f0';ctx.lineWidth=1;
  for(var i=0;i<=4;i++){
    var y=pad.t+ch*(1-i/4);
    ctx.beginPath();ctx.moveTo(pad.l,y);ctx.lineTo(W-pad.r,y);ctx.stroke();
    ctx.fillStyle='#94a3b8';ctx.font='11px sans-serif';ctx.textAlign='right';
    ctx.fillText(fmt(Math.round(maxBal*i/4))+'万',pad.l-6,y+4);
  }

  ctx.beginPath();ctx.strokeStyle='#2563eb';ctx.lineWidth=2.5;
  for(var i=0;i<=Y;i++){
    var x=pad.l+cw*i/Y,y=pad.t+ch*(1-balances[i]/maxBal);
    if(i===0)ctx.moveTo(x,y);else ctx.lineTo(x,y);
  }
  ctx.stroke();

  ctx.fillStyle='rgba(37,99,235,0.1)';
  ctx.beginPath();
  ctx.moveTo(pad.l,pad.t+ch);
  for(var i=0;i<=Y;i++){
    var x=pad.l+cw*i/Y,y=pad.t+ch*(1-balances[i]/maxBal);
    ctx.lineTo(x,y);
  }
  ctx.lineTo(pad.l+cw,pad.t+ch);ctx.closePath();ctx.fill();

  ctx.fillStyle='#64748b';ctx.font='11px sans-serif';ctx.textAlign='center';
  var step=Y<=10?1:Y<=20?5:Y<=35?5:10;
  for(var i=0;i<=Y;i+=step){
    var x=pad.l+cw*i/Y;
    ctx.fillText(i+'年',x,H-pad.b+20);
  }
  if(Y%step!==0){ctx.fillText(Y+'年',pad.l+cw,H-pad.b+20);}

  ctx.fillStyle='#2563eb';ctx.font='bold 12px sans-serif';ctx.textAlign='left';
  ctx.fillText('残高推移',pad.l,pad.t-6);
}

function drawRateCompare(P,Y){
  var rates=[0.4,0.65,1.0,1.5,2.0];
  var Pyen=P*10000;var n=Y*12;
  var html='<table style="width:100%;border-collapse:collapse;font-size:14px;">';
  html+='<tr style="border-bottom:2px solid #92400e;"><th style="text-align:left;padding:6px;">金利</th><th style="text-align:right;padding:6px;">月々返済</th><th style="text-align:right;padding:6px;">総返済額</th><th style="text-align:right;padding:6px;">利息総額</th></tr>';
  for(var i=0;i<rates.length;i++){
    var mr=rates[i]/100/12;
    var m=Pyen*mr*Math.pow(1+mr,n)/(Math.pow(1+mr,n)-1);
    var total=m*n;var interest=total-Pyen;
    var bg=i%2===0?'#fff':'#fef3c7';
    html+='<tr style="background:'+bg+';"><td style="padding:6px;font-weight:bold;">'+rates[i].toFixed(2)+'%</td>';
    html+='<td style="padding:6px;text-align:right;">'+fmt(Math.round(m))+'円</td>';
    html+='<td style="padding:6px;text-align:right;">'+fmt(Math.round(total/10000))+'万円</td>';
    html+='<td style="padding:6px;text-align:right;color:#dc2626;">'+fmt(Math.round(interest/10000))+'万円</td></tr>';
  }
  html+='</table>';
  document.getElementById('rateCompare').innerHTML=html;
  document.getElementById('compareLabel').textContent=fmt(P)+'万円';
}

document.addEventListener('DOMContentLoaded',function(){calcLoan();});
calcLoan();
</script>

---

## 住宅ローンの基礎知識

### 元利均等返済と元金均等返済の違い

**元利均等返済**は毎月の返済額が一定のため、家計の計画が立てやすいのが特徴です。ただし、返済初期は利息の割合が大きく、元金がなかなか減りません。

**元金均等返済**は毎月の元金返済額が一定で、残高の減少に伴い利息も減るため、総返済額は元利均等より少なくなります。ただし初期の返済負担が大きくなります。

### 変動金利と固定金利

2026年現在、変動金利型の住宅ローンは年0.3%〜0.7%程度と歴史的な低水準です。一方、全期間固定型（フラット35など）は年1.5%〜2.0%前後です。

変動金利は金利上昇リスクがありますが、固定金利との差額分を繰上返済に回すことで、実質的なリスクヘッジが可能です。

### 住宅ローン控除（減税）

住宅ローン控除は、年末の住宅ローン残高の0.7%が所得税・住民税から控除される制度です。新築の場合は最長13年間適用されます。上限は借入限度額（省エネ性能等により2,000万〜5,000万円）に基づきます。

---

> 不動産投資に興味がある方は「[RENOSYの利回りは本当？評判・口コミを徹底検証](/ja/posts/renosy-rimawari-hyoban-kensho-2026/)」もご覧ください。投資用ワンルームマンションの実質利回りをデータで分析しています。

> 確定申告が必要になったら、会計ソフト[freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)なら住宅ローン控除の申告もガイドに沿って進められます。

---

**関連記事**
- [会社員が始めるRENOSY不動産投資入門](/ja/posts/kaishain-fudousan-toushi-renosy/)
- [副業税金計算ツール](/ja/tools/fukugyou-tax-calculator/)
- [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)
- [iDeCo節税シミュレーター](/ja/tools/ideco-simulator/)
