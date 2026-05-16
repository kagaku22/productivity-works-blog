---
title: "サブスク管理計算ツール｜月額サブスクの年間コストを見える化【無料】"
date: 2026-05-16
draft: false
slug: "subscription-cost-calculator"
aliases:
  - /ja/tools/subscription-tracker/
description: "Netflix、Spotify、Amazon Primeなど月額サブスクを一覧入力するだけで、年間コスト・1日あたりの金額・投資した場合の将来額を自動計算。無駄なサブスクを発見して節約しましょう。"
author: "Productivity Works編集部"
categories:
  - "無料ツール"
tags:
  - "サブスク"
  - "節約"
  - "家計管理"
  - "計算ツール"
  - "固定費"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "images/covers/subscription-cost-calculator.png"
  alt: "サブスク管理計算ツール｜月額サブスクの年間コストを見える化"
  relative: false
---

※本記事にはアフィリエイト広告が含まれています。

# サブスク管理計算ツール｜月額サブスクの年間コストを見える化

毎月当たり前のように引き落とされているサブスクリプション費用、合計いくらか把握できていますか？**使っているサービスにチェックを入れて金額を確認**するだけで、年間コスト・1日あたりの費用・もし投資に回した場合の将来額を自動で計算します。見えにくい固定費を「見える化」して、賢く節約しましょう。

<div id="sub-calc" style="max-width:720px;margin:0 auto;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI','Hiragino Sans',sans-serif;color:#1e293b;">

<!-- サブスクリスト -->
<div style="padding:24px;border:2px solid #e11d48;border-radius:12px;background:#fff1f2;margin-bottom:20px;">
<h2 style="margin:0 0 4px 0;font-size:18px;color:#e11d48;">サブスクリストを確認・編集</h2>
<p style="margin:0 0 20px 0;font-size:13px;color:#64748b;">チェックを入れたサービスが集計対象になります。金額・名前は直接編集できます。</p>

<!-- 動画・音楽 -->
<div style="margin-bottom:20px;">
<div style="font-size:13px;font-weight:bold;color:#e11d48;background:#ffe4e6;padding:4px 10px;border-radius:4px;margin-bottom:10px;display:inline-block;">動画・音楽</div>
<div id="rows-video"></div>
</div>

<!-- 仕事・生産性 -->
<div style="margin-bottom:20px;">
<div style="font-size:13px;font-weight:bold;color:#7c3aed;background:#ede9fe;padding:4px 10px;border-radius:4px;margin-bottom:10px;display:inline-block;">仕事・生産性</div>
<div id="rows-work"></div>
</div>

<!-- 健康・フィットネス -->
<div style="margin-bottom:20px;">
<div style="font-size:13px;font-weight:bold;color:#059669;background:#d1fae5;padding:4px 10px;border-radius:4px;margin-bottom:10px;display:inline-block;">健康・フィットネス</div>
<div id="rows-health"></div>
</div>

<!-- ニュース・学習 -->
<div style="margin-bottom:20px;">
<div style="font-size:13px;font-weight:bold;color:#d97706;background:#fef3c7;padding:4px 10px;border-radius:4px;margin-bottom:10px;display:inline-block;">ニュース・学習</div>
<div id="rows-news"></div>
</div>

<!-- その他 -->
<div style="margin-bottom:20px;">
<div style="font-size:13px;font-weight:bold;color:#0284c7;background:#e0f2fe;padding:4px 10px;border-radius:4px;margin-bottom:10px;display:inline-block;">その他</div>
<div id="rows-other"></div>
</div>

<!-- 追加ボタン -->
<button onclick="addCustomRow()" style="display:block;width:100%;padding:10px;background:white;border:2px dashed #e11d48;border-radius:8px;color:#e11d48;font-size:14px;font-weight:bold;cursor:pointer;">＋ サブスクを追加</button>
</div>

<!-- 結果パネル -->
<div id="sub-results" style="padding:24px;border:2px solid #e11d48;border-radius:12px;background:white;margin-bottom:20px;">

<div style="background:#e11d48;color:white;border-radius:10px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:13px;margin-bottom:4px;opacity:0.9;">月額合計</div>
<div id="res-monthly" style="font-size:42px;font-weight:bold;line-height:1.1;">0円</div>
<div style="font-size:13px;margin-top:6px;opacity:0.85;display:flex;justify-content:center;gap:24px;">
<span>年間: <strong id="res-yearly">0円</strong></span>
<span>1日あたり: <strong id="res-daily">0円</strong></span>
</div>
</div>

<!-- 投資シミュレーション -->
<div style="background:#fdf2f8;border:1px solid #fbcfe8;border-radius:10px;padding:18px;margin-bottom:16px;">
<div style="font-size:15px;font-weight:bold;color:#9d174d;margin-bottom:12px;">この金額を投資したら？ <span style="font-size:12px;font-weight:normal;color:#64748b;">（年利5%・年間コストを一括投資した場合）</span></div>
<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;text-align:center;">
<div style="background:white;border-radius:8px;padding:12px;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">5年後</div>
<div id="res-inv5" style="font-size:20px;font-weight:bold;color:#e11d48;">-</div>
</div>
<div style="background:white;border-radius:8px;padding:12px;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">10年後</div>
<div id="res-inv10" style="font-size:20px;font-weight:bold;color:#e11d48;">-</div>
</div>
<div style="background:white;border-radius:8px;padding:12px;">
<div style="font-size:12px;color:#64748b;margin-bottom:4px;">20年後</div>
<div id="res-inv20" style="font-size:20px;font-weight:bold;color:#e11d48;">-</div>
</div>
</div>
</div>

<!-- カテゴリ別内訳 -->
<div>
<div style="font-size:15px;font-weight:bold;color:#1e293b;margin-bottom:12px;">カテゴリ別内訳</div>
<div id="res-breakdown"></div>
</div>

</div>

</div>

<script>
(function(){

var categories = [
  {
    id: 'video',
    label: '動画・音楽',
    color: '#e11d48',
    items: [
      {name:'Netflix', cost:1490, checked:true},
      {name:'Spotify', cost:980, checked:true},
      {name:'YouTube Premium', cost:1280, checked:false},
      {name:'Disney+', cost:990, checked:false},
      {name:'Amazon Prime', cost:600, checked:true}
    ]
  },
  {
    id: 'work',
    label: '仕事・生産性',
    color: '#7c3aed',
    items: [
      {name:'Microsoft 365', cost:1490, checked:false},
      {name:'Google One', cost:250, checked:false},
      {name:'Notion', cost:0, checked:false},
      {name:'Dropbox', cost:1500, checked:false}
    ]
  },
  {
    id: 'health',
    label: '健康・フィットネス',
    color: '#059669',
    items: [
      {name:'ジム会費', cost:8000, checked:false},
      {name:'フィットネスアプリ', cost:980, checked:false}
    ]
  },
  {
    id: 'news',
    label: 'ニュース・学習',
    color: '#d97706',
    items: [
      {name:'新聞電子版', cost:1000, checked:false},
      {name:'オンライン講座', cost:2000, checked:false}
    ]
  },
  {
    id: 'other',
    label: 'その他',
    color: '#0284c7',
    items: []
  }
];

var customCount = 0;

function rowStyle(){
  return 'display:flex;align-items:center;padding:8px 0;border-bottom:1px solid #fecdd3;gap:8px;';
}

function renderRows(cat){
  var container = document.getElementById('rows-' + cat.id);
  if(!container) return;
  var html = '';
  for(var i=0;i<cat.items.length;i++){
    var item = cat.items[i];
    var ck = item.checked ? 'checked' : '';
    html += '<div style="'+rowStyle()+'">';
    html += '<input type="checkbox" '+ck+' data-cat="'+cat.id+'" data-idx="'+i+'" onchange="onCheck(this)" style="width:18px;height:18px;accent-color:#e11d48;flex-shrink:0;cursor:pointer;">';
    html += '<input type="text" value="'+escHtml(item.name)+'" data-cat="'+cat.id+'" data-idx="'+i+'" onchange="onNameChange(this)" style="flex:1;border:none;background:transparent;font-size:14px;color:#1e293b;min-width:0;padding:2px 4px;border-radius:4px;" onfocus="this.style.background=\'#fff\';this.style.border=\'1px solid #fda4af\';" onblur="this.style.background=\'transparent\';this.style.border=\'none\';">';
    html += '<input type="number" value="'+item.cost+'" min="0" data-cat="'+cat.id+'" data-idx="'+i+'" onchange="onCostChange(this)" style="width:90px;padding:4px 6px;border:1px solid #cbd5e1;border-radius:6px;font-size:14px;text-align:right;">';
    html += '<span style="font-size:13px;color:#64748b;flex-shrink:0;">円/月</span>';
    html += '<button onclick="removeRow(\''+cat.id+'\','+i+')" style="background:none;border:none;color:#94a3b8;font-size:18px;cursor:pointer;padding:0 4px;line-height:1;flex-shrink:0;" title="削除">×</button>';
    html += '</div>';
  }
  container.innerHTML = html;
}

function escHtml(s){
  return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function renderAll(){
  for(var i=0;i<categories.length;i++){
    renderRows(categories[i]);
  }
  calcResults();
}

function getCatById(id){
  for(var i=0;i<categories.length;i++){
    if(categories[i].id===id) return categories[i];
  }
  return null;
}

window.onCheck = function(el){
  var cat = getCatById(el.getAttribute('data-cat'));
  var idx = parseInt(el.getAttribute('data-idx'));
  cat.items[idx].checked = el.checked;
  calcResults();
};

window.onNameChange = function(el){
  var cat = getCatById(el.getAttribute('data-cat'));
  var idx = parseInt(el.getAttribute('data-idx'));
  cat.items[idx].name = el.value;
};

window.onCostChange = function(el){
  var cat = getCatById(el.getAttribute('data-cat'));
  var idx = parseInt(el.getAttribute('data-idx'));
  var v = parseInt(el.value);
  cat.items[idx].cost = isNaN(v)||v<0 ? 0 : v;
  calcResults();
};

window.removeRow = function(catId, idx){
  var cat = getCatById(catId);
  cat.items.splice(idx,1);
  renderRows(cat);
  calcResults();
};

window.addCustomRow = function(){
  customCount++;
  var cat = getCatById('other');
  cat.items.push({name:'カスタム'+customCount, cost:0, checked:true});
  renderRows(cat);
  calcResults();
};

function fmt(n){
  return Math.round(n).toLocaleString()+'円';
}

function calcResults(){
  var totalMonthly = 0;
  var catTotals = [];

  for(var i=0;i<categories.length;i++){
    var cat = categories[i];
    var catSum = 0;
    for(var j=0;j<cat.items.length;j++){
      if(cat.items[j].checked){
        catSum += cat.items[j].cost;
      }
    }
    catTotals.push({label:cat.label, color:cat.color, sum:catSum});
    totalMonthly += catSum;
  }

  var totalYearly = totalMonthly * 12;
  var totalDaily = totalMonthly / 30;

  document.getElementById('res-monthly').textContent = fmt(totalMonthly);
  document.getElementById('res-yearly').textContent = fmt(totalYearly);
  document.getElementById('res-daily').textContent = Math.round(totalDaily).toLocaleString()+'円';

  var rate = 0.05;
  document.getElementById('res-inv5').textContent  = totalYearly>0 ? fmt(totalYearly * Math.pow(1+rate, 5))  : '-';
  document.getElementById('res-inv10').textContent = totalYearly>0 ? fmt(totalYearly * Math.pow(1+rate,10)) : '-';
  document.getElementById('res-inv20').textContent = totalYearly>0 ? fmt(totalYearly * Math.pow(1+rate,20)) : '-';

  var bHtml = '';
  if(totalMonthly === 0){
    bHtml = '<div style="color:#94a3b8;font-size:14px;text-align:center;padding:12px 0;">チェックを入れたサービスがありません</div>';
  } else {
    for(var k=0;k<catTotals.length;k++){
      if(catTotals[k].sum===0) continue;
      var pct = Math.round(catTotals[k].sum / totalMonthly * 100);
      bHtml += '<div style="margin-bottom:10px;">';
      bHtml += '<div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:4px;">';
      bHtml += '<span style="font-weight:bold;color:'+catTotals[k].color+';">'+catTotals[k].label+'</span>';
      bHtml += '<span style="color:#1e293b;">'+catTotals[k].sum.toLocaleString()+'円/月 <span style="color:#94a3b8;">('+pct+'%)</span></span>';
      bHtml += '</div>';
      bHtml += '<div style="background:#f1f5f9;border-radius:4px;height:10px;overflow:hidden;">';
      bHtml += '<div style="background:'+catTotals[k].color+';height:100%;width:'+pct+'%;border-radius:4px;transition:width 0.4s;"></div>';
      bHtml += '</div>';
      bHtml += '</div>';
    }
  }
  document.getElementById('res-breakdown').innerHTML = bHtml;
}

renderAll();

})();
</script>

---

## サブスク節約のコツ

**1. まず「全部リストアップ」する**
クレジットカードの明細を3ヶ月分さかのぼり、定期引き落としをすべてリスト化しましょう。「使っていたのに気づかなかった」サブスクが1〜2件は見つかります。

**2. 「使用頻度」で仕分けする**
月1回以下しか使わないサービスは「解約候補」です。年額換算で考えると決断しやすくなります。Netflix（年間17,880円）を解約するだけで、スターバックスラテ約59杯分の節約になります。

**3. 複数サービスの重複を見つける**
動画サービスをNetflix・Disney+・Amazon Primeと3つ契約していませんか？「今月はNetflixだけ」と決めてローテーションするだけで固定費が下がります。

**4. 家族プラン・年払いを活用する**
Spotifyのファミリープランは最大6人で月額1,980円（1人あたり330円）。SpotifyやYouTube Premiumは年払いにすると約2ヶ月分お得になります。

**5. 無料トライアル終了日をカレンダーに入れる**
無料期間が終わった直後に課金が始まるパターンが最も多い落とし穴です。登録時に必ずカレンダーへ「解約確認日」を入力する習慣をつけましょう。

---

## 固定費を自動管理するならfreee会計

サブスクの引き落とし管理は、銀行口座・クレジットカードと自動連携できる会計ソフトを使うと格段に楽になります。

**[freee会計で固定費を自動管理する →](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP)**

口座明細を自動取得して支出を分類・グラフ化してくれるため、「いつのまにか増えたサブスク」を月次で把握できます。確定申告にも対応しているため、フリーランス・副業をしている方にも最適です。

---

## 関連ツール

月々の支出バランスを見直す → [家計簿シミュレーター](/ja/tools/kakeibo-generator/)

貯蓄目標を計算 → [貯蓄目標シミュレーター](/ja/tools/chochiku-mokuhyo-simulator/)

年収から手取りを計算 → [手取り計算シミュレーター](/ja/tools/salary-tedori-calculator/)

純資産を把握する → [資産管理シミュレーター](/ja/tools/shisan-simulator/)

---

## 関連記事

- [節約の始め方｜固定費を削るだけで月1万円浮かせる方法](/ja/posts/setsuyaku-hajimekata/)
- [クレジットカードおすすめ2026年版](/ja/posts/credit-card-osusume-2026/)
- [NISAとiDeCo、どっちを先に始めるべきか？](/ja/posts/nisa-ideco-docchi-saki/)
- [副業の始め方ガイド2026](/ja/posts/fukugyou-hajimekata-2026/)
