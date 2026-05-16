---
title: "手取り計算ツール - 額面から手取りを即計算"
date: 2025-05-16
description: "無料の手取り計算ツール。額面年収から所得税・住民税・社会保険料を差し引いた手取り額を即座に計算。月額・年額・ボーナス対応。"
categories: ["無料ツール"]
slug: "salary-calculator"
ShowToc: false
aliases:
  - "/ja/tools/salary-calculator/"
  - "/ja/tools/salary-tedori-calculator/"
cover:
  image: "/images/covers/salary-calculator-ja.png"
  alt: "手取り計算ツール"
---

※本ページにはアフィリエイト広告が含まれています。

**確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

<style>
#sc-app-ja,#sc-app-ja *,#sc-app-ja *::before,#sc-app-ja *::after{box-sizing:border-box}
#sc-app-ja{font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans','Yu Gothic UI','Segoe UI',Roboto,sans-serif;max-width:700px;margin:0 auto;color:#1e293b;padding:4px 0}
#sc-app-ja h2{font-size:1.05rem;font-weight:700;color:#0f172a;margin:0 0 16px}
#sc-app-ja .sc-card{background:#fff;border:1px solid #e2e8f0;border-radius:12px;padding:22px 24px;margin-bottom:18px;box-shadow:0 1px 4px rgba(0,0,0,.06)}
#sc-app-ja label{display:block;font-size:13px;font-weight:600;color:#475569;margin-bottom:6px;margin-top:14px}
#sc-app-ja label:first-child{margin-top:0}
#sc-app-ja input[type=number],#sc-app-ja input[type=range],#sc-app-ja select{font-family:inherit}
#sc-app-ja input[type=number],#sc-app-ja select{width:100%;padding:9px 12px;border:1.5px solid #cbd5e1;border-radius:8px;font-size:15px;color:#1e293b;background:#f8fafc;transition:border-color .2s;-webkit-appearance:none;appearance:none}
#sc-app-ja input[type=number]:focus,#sc-app-ja select:focus{outline:none;border-color:#3b82f6;background:#fff;box-shadow:0 0 0 3px rgba(59,130,246,.12)}
#sc-app-ja input[type=range]{width:100%;accent-color:#3b82f6;cursor:pointer;margin-top:4px}
#sc-app-ja .sc-row{display:grid;grid-template-columns:1fr 1fr;gap:16px}
@media(max-width:520px){#sc-app-ja .sc-row{grid-template-columns:1fr}}
#sc-app-ja .sc-range-val{display:inline-block;font-size:20px;font-weight:800;color:#1d4ed8}
#sc-app-ja .sc-btn{display:block;width:100%;margin-top:20px;padding:13px;background:linear-gradient(135deg,#1d4ed8 0%,#3b82f6 100%);color:#fff;font-size:15px;font-weight:700;border:none;border-radius:9px;cursor:pointer;transition:opacity .2s;letter-spacing:.02em}
#sc-app-ja .sc-btn:hover{opacity:.88}
#sc-app-ja .sc-hero{background:linear-gradient(135deg,#1d4ed8 0%,#3b82f6 100%);border-radius:12px;padding:28px 20px;color:#fff;text-align:center;margin-bottom:18px}
#sc-app-ja .sc-hero-label{font-size:13px;opacity:.85;margin-bottom:6px;letter-spacing:.04em;font-weight:500}
#sc-app-ja .sc-hero-amount{font-size:52px;font-weight:800;letter-spacing:-1px;line-height:1}
#sc-app-ja .sc-hero-sub{margin-top:16px;display:flex;justify-content:center;gap:22px;flex-wrap:wrap;font-size:14px;opacity:.92}
#sc-app-ja .sc-hero-sub span{font-weight:700}
#sc-app-ja .sc-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:18px}
@media(max-width:520px){#sc-app-ja .sc-stats{grid-template-columns:1fr 1fr}}
#sc-app-ja .sc-stat{border-radius:10px;padding:14px 10px;text-align:center}
#sc-app-ja .sc-stat-label{font-size:11px;font-weight:600;color:#64748b;text-transform:uppercase;letter-spacing:.3px;margin-bottom:4px}
#sc-app-ja .sc-stat-val{font-size:1.15rem;font-weight:800;color:#0f172a}
#sc-app-ja table{width:100%;border-collapse:collapse;font-size:14px}
#sc-app-ja th{background:#f1f5f9;text-align:left;padding:9px 12px;font-size:11px;font-weight:700;color:#64748b;letter-spacing:.3px}
#sc-app-ja th:not(:first-child){text-align:right}
#sc-app-ja td{padding:9px 12px;border-bottom:1px solid #f1f5f9;color:#334155}
#sc-app-ja td:not(:first-child){text-align:right;font-weight:600}
#sc-app-ja tr:last-child td{border-bottom:none}
#sc-app-ja tr.sc-subtotal td{font-weight:700;color:#dc2626;background:#fff1f2}
#sc-app-ja tr.sc-net td{font-weight:800;color:#15803d;background:#f0fdf4;font-size:15px}
#sc-app-ja .sc-chart-wrap{display:flex;align-items:center;gap:20px;flex-wrap:wrap}
#sc-app-ja canvas{flex-shrink:0}
#sc-app-ja .sc-legend{flex:1;min-width:180px}
#sc-app-ja .sc-legend-item{display:flex;align-items:center;gap:8px;margin-bottom:7px;font-size:13px;color:#334155}
#sc-app-ja .sc-legend-swatch{width:12px;height:12px;border-radius:3px;flex-shrink:0}
#sc-app-ja .sc-bar-wrap{display:flex;height:18px;border-radius:6px;overflow:hidden;margin:10px 0 8px}
#sc-app-ja .sc-bar-legend{display:flex;flex-wrap:wrap;gap:10px;font-size:12px;color:#475569}
#sc-app-ja .sc-dot{display:inline-block;width:10px;height:10px;border-radius:2px;margin-right:5px;vertical-align:middle}
#sc-app-ja .sc-note{font-size:12px;color:#94a3b8;line-height:1.65;margin-top:14px;border-left:3px solid #e2e8f0;padding-left:12px}
</style>

<div id="sc-app-ja">

<div class="sc-card">
  <h2>年収・条件を入力してください</h2>

  <label for="ja-gross-num">額面年収（円）</label>
  <input type="range" id="ja-gross-range" min="1000000" max="30000000" step="100000" value="5000000">
  <div style="margin:6px 0 4px"><span class="sc-range-val" id="ja-gross-display">500万円</span></div>
  <input type="number" id="ja-gross-num" min="1000000" max="100000000" step="100000" value="5000000" placeholder="例: 5000000">

  <div class="sc-row">
    <div>
      <label for="ja-bonus">ボーナス月数（月分）</label>
      <input type="number" id="ja-bonus" min="0" max="12" step="0.5" value="2" placeholder="例: 2">
    </div>
    <div>
      <label for="ja-age">年齢（社会保険区分）</label>
      <select id="ja-age">
        <option value="under40">40歳未満（介護保険なし）</option>
        <option value="over40">40〜64歳（介護保険あり）</option>
        <option value="over65">65歳以上</option>
      </select>
    </div>
  </div>

  <div class="sc-row">
    <div>
      <label for="ja-dependents">扶養家族人数</label>
      <select id="ja-dependents">
        <option value="0">0人（独身・扶養なし）</option>
        <option value="1">1人</option>
        <option value="2">2人</option>
        <option value="3">3人</option>
        <option value="4">4人以上</option>
      </select>
    </div>
    <div style="display:flex;align-items:flex-end">
      <button class="sc-btn" onclick="jaCalc()" style="margin-top:0">手取りを計算する</button>
    </div>
  </div>
</div>

<div class="sc-hero">
  <div class="sc-hero-label">手取り年収（概算）</div>
  <div class="sc-hero-amount" id="ja-h-net">—</div>
  <div class="sc-hero-sub">
    <div>月収手取り: <span id="ja-h-monthly">—</span></div>
    <div>賞与月手取り: <span id="ja-h-bonus">—</span></div>
  </div>
</div>

<div class="sc-stats">
  <div class="sc-stat" style="background:#f0fdf4;border:1px solid #86efac">
    <div class="sc-stat-label">手取り年収</div>
    <div class="sc-stat-val" style="color:#15803d" id="ja-s-net">—</div>
  </div>
  <div class="sc-stat" style="background:#fff1f2;border:1px solid #fca5a5">
    <div class="sc-stat-label">控除合計</div>
    <div class="sc-stat-val" style="color:#dc2626" id="ja-s-ded">—</div>
  </div>
  <div class="sc-stat" style="background:#fef3c7;border:1px solid #fde68a">
    <div class="sc-stat-label">実質負担率</div>
    <div class="sc-stat-val" style="color:#b45309" id="ja-s-rate">—</div>
  </div>
  <div class="sc-stat" style="background:#f0f9ff;border:1px solid #bae6fd">
    <div class="sc-stat-label">所得税</div>
    <div class="sc-stat-val" style="color:#0369a1" id="ja-s-income">—</div>
  </div>
  <div class="sc-stat" style="background:#faf5ff;border:1px solid #d8b4fe">
    <div class="sc-stat-label">住民税</div>
    <div class="sc-stat-val" style="color:#7c3aed" id="ja-s-resident">—</div>
  </div>
  <div class="sc-stat" style="background:#fff7ed;border:1px solid #fed7aa">
    <div class="sc-stat-label">社会保険料計</div>
    <div class="sc-stat-val" style="color:#c2410c" id="ja-s-si">—</div>
  </div>
</div>

<div class="sc-card">
  <h2>内訳一覧</h2>
  <div style="overflow-x:auto">
  <table>
    <thead>
      <tr>
        <th>項目</th>
        <th>年額</th>
        <th>月額（概算）</th>
      </tr>
    </thead>
    <tbody id="ja-tbody"></tbody>
  </table>
  </div>
  <div style="margin-top:18px">
    <div style="font-size:12px;font-weight:600;color:#94a3b8;margin-bottom:4px">年収の内訳</div>
    <div class="sc-bar-wrap" id="ja-barwrap"></div>
    <div class="sc-bar-legend" id="ja-barlegend"></div>
  </div>
</div>

<div class="sc-card">
  <h2>控除の内訳グラフ</h2>
  <div class="sc-chart-wrap">
    <canvas id="ja-pie" width="180" height="180"></canvas>
    <div class="sc-legend" id="ja-legend"></div>
  </div>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">確定申告・経費管理をもっとラクに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、手取り計算はもちろん、確定申告・経費精算までクラウドで一元管理。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<p class="sc-note">本ツールはあくまで目安の計算です。実際の手取り額は企業の給与規程・標準報酬月額の等級・各種控除・扶養控除の詳細等により異なります。正確な計算は給与明細や税理士にご確認ください。社会保険料率は協会けんぽ（東京・2024年度）を基準にしています。所得税は源泉徴収税額表の簡易計算を使用。住民税は前年所得ベースのため、転職初年度等は異なる場合があります。</p>

</div>

<script>
(function(){
// 給与所得控除（2024年）
function kyuyoKojo(gross){
  if(gross<=1625000)return550000;
  if(gross<=1800000)return gross*0.4-100000;
  if(gross<=3600000)return gross*0.3+80000;
  if(gross<=6600000)return gross*0.2+440000;
  if(gross<=8500000)return gross*0.1+1100000;
  return950000; // 上限
}

// 所得税の速算表（2024年・課税所得）
function incomeTax(taxable){
  if(taxable<=1950000) return taxable*0.05;
  if(taxable<=3300000) return taxable*0.10-97500;
  if(taxable<=6950000) return taxable*0.20-427500;
  if(taxable<=9000000) return taxable*0.23-636000;
  if(taxable<=18000000)return taxable*0.33-1536000;
  if(taxable<=40000000)return taxable*0.40-2796000;
  return taxable*0.45-4796000;
}

function fmtYen(n){
  n=Math.round(Math.max(0,n));
  if(n>=10000){
    return Math.round(n/10000).toLocaleString('ja-JP')+'万円';
  }
  return n.toLocaleString('ja-JP')+'円';
}
function fmtYenFull(n){
  return Math.round(Math.max(0,n)).toLocaleString('ja-JP')+'円';
}
function pct(n){return(n*100).toFixed(1)+'%'}
function g(id){return document.getElementById(id)}

function addRow2(tbody,label,annual,cls){
  var tr=document.createElement('tr');
  if(cls)tr.className=cls;
  [label,fmtYen(annual),fmtYen(annual/12)].forEach(function(v,i){
    var td=document.createElement('td');td.textContent=v;tr.appendChild(td);
  });
  tbody.appendChild(tr);
}

window.jaCalc=function(){
  var gross=Math.max(0,parseFloat(g('ja-gross-num').value)||0);
  var bonusMonths=Math.max(0,parseFloat(g('ja-bonus').value)||0);
  var ageGroup=g('ja-age').value;
  var dependents=parseInt(g('ja-dependents').value)||0;

  // 月給・ボーナスの分割
  // 年収 = 月給×12 + ボーナス(月給×bonusMonths)
  // gross = monthly * (12 + bonusMonths)
  var monthly = bonusMonths>0 ? gross/(12+bonusMonths) : gross/12;
  var bonusTotal = monthly * bonusMonths;

  // 社会保険料（協会けんぽ東京・2024年度）
  // 標準報酬月額に対して計算（簡易: 月給を標準報酬月額とする）
  var kenpoRate = ageGroup==='over40' ? 0.1182 : 0.0998; // 健康保険（介護含む）本人負担
  var nenkinRate = 0.183/2; // 厚生年金 本人負担9.15%
  // 厚生年金：標準報酬月額上限65万円
  var stdMonthly = Math.min(monthly, 650000);
  var kenpo = stdMonthly * kenpoRate;
  var nenkin = stdMonthly * nenkinRate;
  // 雇用保険：0.6%（一般）
  var koyo = gross * 0.006;
  // 社会保険料合計（年額）
  var siTotal = (kenpo + nenkin) * 12 + koyo;

  // 給与所得控除
  var kojo = kyuyoKojo(gross);
  // 給与所得
  var kyuyoShotoku = Math.max(0, gross - kojo);
  // 所得控除
  var kisoPct = 480000; // 基礎控除
  var fuyoKojo = dependents * 380000; // 扶養控除（一般）
  var allKojo = kisoPct + fuyoKojo + siTotal;
  // 課税所得（所得税）
  var taxableIncome = Math.max(0, kyuyoShotoku - allKojo);
  // 所得税
  var shotokuZei = Math.max(0, incomeTax(taxableIncome));
  // 復興特別所得税（2.1%）
  var fukkoZei = shotokuZei * 0.021;
  var shotokuZeiTotal = shotokuZei + fukkoZei;

  // 住民税（課税所得の10%、住民税控除は43万円）
  var juuminKisoPct = 430000;
  var juuminAllKojo = juuminKisoPct + fuyoKojo + siTotal;
  var juuminTaxable = Math.max(0, kyuyoShotoku - juuminAllKojo);
  var juuminZei = Math.max(0, juuminTaxable * 0.10 + 5000); // 均等割5000円加算

  // 手取り
  var totalDed = siTotal + shotokuZeiTotal + juuminZei;
  var net = Math.max(0, gross - totalDed);
  var effRate = totalDed / Math.max(1, gross);

  // ボーナス手取り概算（社保・所得税30%・住民税10%控除）
  var bonusNet = bonusTotal > 0 ? Math.max(0, bonusTotal * 0.72) : 0;

  // Hero
  g('ja-h-net').textContent = fmtYen(net);
  g('ja-h-monthly').textContent = fmtYen((net - bonusNet) / 12);
  g('ja-h-bonus').textContent = bonusMonths > 0 ? fmtYen(bonusNet / bonusMonths) : '—';

  // Stats
  g('ja-s-net').textContent = fmtYen(net);
  g('ja-s-ded').textContent = fmtYen(totalDed);
  g('ja-s-rate').textContent = pct(effRate);
  g('ja-s-income').textContent = fmtYen(shotokuZeiTotal);
  g('ja-s-resident').textContent = fmtYen(juuminZei);
  g('ja-s-si').textContent = fmtYen(siTotal);

  // Table
  var tbody = g('ja-tbody'); tbody.innerHTML = '';
  addRow2(tbody, '額面年収', gross, '');
  addRow2(tbody, '健康保険料（本人負担）', kenpo * 12, '');
  addRow2(tbody, '厚生年金保険料（本人負担）', nenkin * 12, '');
  addRow2(tbody, '雇用保険料', koyo, '');
  addRow2(tbody, '社会保険料 合計', siTotal, '');
  addRow2(tbody, '所得税（復興税込）', shotokuZeiTotal, '');
  addRow2(tbody, '住民税（概算）', juuminZei, '');
  addRow2(tbody, '控除合計', totalDed, 'sc-subtotal');
  addRow2(tbody, '手取り年収', net, 'sc-net');

  // Pie
  var COLS = ['#22c55e','#3b82f6','#a855f7','#f97316','#eab308','#06b6d4'];
  var items = [
    {label:'手取り',val:net,color:COLS[0]},
    {label:'健康保険',val:kenpo*12,color:COLS[1]},
    {label:'厚生年金',val:nenkin*12,color:COLS[2]},
    {label:'雇用保険',val:koyo,color:COLS[3]},
    {label:'所得税',val:shotokuZeiTotal,color:COLS[4]},
    {label:'住民税',val:juuminZei,color:COLS[5]}
  ].filter(function(x){return x.val>0.5});

  var canvas = g('ja-pie');
  var ctx = canvas.getContext('2d');
  ctx.clearRect(0,0,180,180);
  var tot = items.reduce(function(s,x){return s+x.val},0)||1;
  var ang = -Math.PI/2;
  items.forEach(function(item){
    var sl = (item.val/tot)*Math.PI*2;
    ctx.beginPath(); ctx.moveTo(90,90);
    ctx.arc(90,90,85,ang,ang+sl);
    ctx.closePath(); ctx.fillStyle=item.color; ctx.fill();
    ctx.strokeStyle='#fff'; ctx.lineWidth=2; ctx.stroke();
    ang += sl;
  });

  var legend = g('ja-legend'); legend.innerHTML = '';
  items.forEach(function(item){
    var p = ((item.val/Math.max(1,gross))*100).toFixed(1);
    legend.innerHTML += '<div class="sc-legend-item"><span class="sc-legend-swatch" style="background:'+item.color+'"></span><span><strong>'+item.label+'</strong> '+fmtYen(item.val)+' ('+p+'%)</span></div>';
  });

  var bw = g('ja-barwrap'), bl = g('ja-barlegend');
  bw.innerHTML = ''; bl.innerHTML = '';
  items.forEach(function(item){
    var d = document.createElement('div');
    d.style.width = ((item.val/Math.max(1,gross))*100).toFixed(2)+'%';
    d.style.background = item.color; bw.appendChild(d);
    bl.innerHTML += '<span><span class="sc-dot" style="background:'+item.color+'"></span>'+item.label+'</span>';
  });
};

// Range sync
var rng = g('ja-gross-range'), num = g('ja-gross-num'), disp = g('ja-gross-display');
rng.addEventListener('input', function(){
  num.value = rng.value;
  var man = Math.round(parseInt(rng.value)/10000);
  disp.textContent = man.toLocaleString('ja-JP')+'万円';
  jaCalc();
});
num.addEventListener('input', function(){
  var v = Math.min(100000000, Math.max(1000000, parseFloat(num.value)||5000000));
  rng.value = Math.min(v, 30000000);
  var man = Math.round(v/10000);
  disp.textContent = man.toLocaleString('ja-JP')+'万円';
  jaCalc();
});
g('ja-age').addEventListener('change', jaCalc);
g('ja-dependents').addEventListener('change', jaCalc);
['ja-bonus'].forEach(function(id){g(id).addEventListener('input', jaCalc);});
jaCalc();
})();
</script>
</div>

---

> 複利計算 → [複利計算ツール](/ja/tools/compound-interest-calculator/)

> 住宅ローン → [住宅ローン計算ツール](/ja/tools/mortgage-calculator/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [AIを使った副業の始め方完全ガイド【2026年版・月3万〜10万円を目指す】](/ja/posts/ai-副業-始め方/)
- [フリーランスエンジニア年収相場完全ガイド2026年版](/ja/posts/フリーランス-エンジニア-年収-相場/)
- [50代転職 AI活用準備ガイド2026 未経験からの完全ロードマップ](/ja/posts/50dai-tenshoku-ai-junbi-2026/)
