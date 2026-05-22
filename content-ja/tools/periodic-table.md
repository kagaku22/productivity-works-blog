---
title: "インタラクティブ周期表"
description: "無料のインタラクティブ周期表。全118元素をクリックして原子番号・質量・電子配置・性質を確認。カテゴリ別色分け・検索機能付き。化学の学習に最適。"
date: 2025-10-07
slug: periodic-table
categories: ["無料ツール"]
tags: ["テキストツール", "文字列処理", "無料ツール"]
ShowToc: false
cover:
  image: /images/covers/periodic-table-ja.png
  alt: "インタラクティブ周期表 - 全118元素"
---

<div id="pt-app">

<style>
#pt-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', sans-serif;
color: #1a1a1a;
max-width: 100%;
}
#pt-app * { box-sizing: border-box; }

#pt-app .pt-controls {
display: flex;
flex-wrap: wrap;
gap: 10px;
margin-bottom: 16px;
align-items: center;
}
#pt-app .pt-search {
flex: 1;
min-width: 180px;
padding: 8px 12px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 14px;
outline: none;
transition: border-color 0.2s;
}
#pt-app .pt-search:focus { border-color: #3b82f6; }
#pt-app .pt-filter {
padding: 8px 12px;
border: 1.5px solid #d1d5db;
border-radius: 8px;
font-size: 13px;
background: #fff;
cursor: pointer;
outline: none;
}
#pt-app .pt-clear {
padding: 8px 14px;
background: #6b7280;
color: #fff;
border: none;
border-radius: 8px;
font-size: 13px;
cursor: pointer;
}
#pt-app .pt-clear:hover { background: #4b5563; }

/* Legend */
#pt-app .pt-legend {
display: flex;
flex-wrap: wrap;
gap: 6px;
margin-bottom: 14px;
}
#pt-app .pt-legend-item {
display: flex;
align-items: center;
gap: 4px;
font-size: 11px;
color: #374151;
cursor: pointer;
padding: 2px 6px;
border-radius: 4px;
border: 1px solid transparent;
transition: border-color 0.15s;
}
#pt-app .pt-legend-item:hover { border-color: #9ca3af; }
#pt-app .pt-legend-swatch {
width: 12px; height: 12px;
border-radius: 3px;
flex-shrink: 0;
}

/* Table wrapper */
#pt-app .pt-wrapper {
overflow-x: auto;
-webkit-overflow-scrolling: touch;
padding-bottom: 8px;
}
#pt-app .pt-grid {
display: grid;
grid-template-columns: repeat(18, minmax(46px, 1fr));
grid-template-rows: repeat(9, 48px);
gap: 2px;
min-width: 860px;
}

/* Element cell */
#pt-app .el {
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
border-radius: 4px;
cursor: pointer;
padding: 2px;
transition: transform 0.1s, box-shadow 0.1s, opacity 0.2s;
border: 1px solid rgba(0,0,0,0.12);
position: relative;
user-select: none;
}
#pt-app .el:hover {
transform: scale(1.12);
box-shadow: 0 4px 12px rgba(0,0,0,0.22);
z-index: 5;
}
#pt-app .el.dimmed { opacity: 0.18; }
#pt-app .el.highlighted { opacity: 1; box-shadow: 0 0 0 2px #1d4ed8; }

#pt-app .el-num {
font-size: 8px;
color: rgba(0,0,0,0.55);
line-height: 1;
align-self: flex-start;
padding-left: 2px;
}
#pt-app .el-sym {
font-size: 16px;
font-weight: 700;
line-height: 1;
}
#pt-app .el-name {
font-size: 7px;
line-height: 1.1;
text-align: center;
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
width: 100%;
text-align: center;
}
#pt-app .el-mass {
font-size: 7px;
color: rgba(0,0,0,0.5);
line-height: 1;
}

/* Category colors */
#pt-app .cat-alkali       { background: #fca5a5; }
#pt-app .cat-alkaline     { background: #fdba74; }
#pt-app .cat-lanthanide   { background: #fde68a; }
#pt-app .cat-actinide     { background: #d9f99d; }
#pt-app .cat-transition   { background: #93c5fd; }
#pt-app .cat-post         { background: #6ee7b7; }
#pt-app .cat-metalloid    { background: #a5b4fc; }
#pt-app .cat-nonmetal     { background: #f9a8d4; }
#pt-app .cat-halogen      { background: #fb923c; color: #fff; }
#pt-app .cat-noble        { background: #c4b5fd; }
#pt-app .cat-unknown      { background: #d1d5db; }

/* Popup */
#pt-app .pt-popup-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(0,0,0,0.45);
z-index: 1000;
align-items: center;
justify-content: center;
}
#pt-app .pt-popup-overlay.open { display: flex; }
#pt-app .pt-popup {
background: #fff;
border-radius: 14px;
padding: 24px 28px;
max-width: 440px;
width: 90vw;
box-shadow: 0 20px 60px rgba(0,0,0,0.3);
position: relative;
animation: ptPopIn 0.18s ease;
}
@keyframes ptPopIn {
from { transform: scale(0.88); opacity: 0; }
to   { transform: scale(1); opacity: 1; }
}
#pt-app .pt-popup-close {
position: absolute;
top: 12px; right: 14px;
background: none;
border: none;
font-size: 22px;
cursor: pointer;
color: #6b7280;
line-height: 1;
}
#pt-app .pt-popup-close:hover { color: #1a1a1a; }
#pt-app .pt-popup-header {
display: flex;
align-items: center;
gap: 16px;
margin-bottom: 16px;
}
#pt-app .pt-popup-sym-box {
width: 72px; height: 72px;
border-radius: 10px;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
flex-shrink: 0;
}
#pt-app .pt-popup-sym {
font-size: 32px;
font-weight: 800;
line-height: 1;
}
#pt-app .pt-popup-num-small {
font-size: 12px;
color: rgba(0,0,0,0.5);
}
#pt-app .pt-popup-name {
font-size: 22px;
font-weight: 700;
margin: 0 0 4px;
}
#pt-app .pt-popup-cat {
font-size: 12px;
color: #6b7280;
}
#pt-app .pt-popup-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px 16px;
}
#pt-app .pt-popup-field label {
font-size: 11px;
color: #9ca3af;
display: block;
margin-bottom: 1px;
text-transform: uppercase;
letter-spacing: 0.04em;
}
#pt-app .pt-popup-field span {
font-size: 14px;
font-weight: 600;
color: #111;
}

#pt-app .pt-mobile-hint {
text-align: center;
font-size: 12px;
color: #9ca3af;
margin-top: 6px;
}

@media (max-width: 600px) {
#pt-app .pt-grid { min-width: 760px; }
#pt-app .el { border-radius: 3px; }
#pt-app .el-sym { font-size: 13px; }
}
</style>

<div class="pt-controls">
<input class="pt-search" id="ptSearch" type="text" placeholder="元素名または元素記号で検索…" autocomplete="off" />
<select class="pt-filter" id="ptFilter">
<option value="">すべてのカテゴリ</option>
<option value="alkali">アルカリ金属</option>
<option value="alkaline">アルカリ土類金属</option>
<option value="transition">遷移金属</option>
<option value="post">典型金属</option>
<option value="metalloid">半金属</option>
<option value="nonmetal">非金属</option>
<option value="halogen">ハロゲン</option>
<option value="noble">希ガス</option>
<option value="lanthanide">ランタノイド</option>
<option value="actinide">アクチノイド</option>
<option value="unknown">性質不明</option>
</select>
<button class="pt-clear" id="ptClear">クリア</button>
</div>

<div class="pt-legend" id="ptLegend"></div>

<div class="pt-wrapper">
<div class="pt-grid" id="ptGrid"></div>
</div>
<p class="pt-mobile-hint">← 横スクロールで全体を表示できます →</p>

<div class="pt-popup-overlay" id="ptOverlay">
<div class="pt-popup" id="ptPopup">
<button class="pt-popup-close" id="ptClose">×</button>
<div class="pt-popup-header">
<div class="pt-popup-sym-box" id="ppSymBox">
<span class="pt-popup-sym" id="ppSym"></span>
<span class="pt-popup-num-small" id="ppNumSmall"></span>
</div>
<div>
<p class="pt-popup-name" id="ppName"></p>
<p class="pt-popup-cat" id="ppCat"></p>
</div>
</div>
<div class="pt-popup-grid">
<div class="pt-popup-field"><label>原子番号</label><span id="ppNum"></span></div>
<div class="pt-popup-field"><label>原子量</label><span id="ppMass"></span></div>
<div class="pt-popup-field"><label>カテゴリ</label><span id="ppCatFull"></span></div>
<div class="pt-popup-field"><label>常温での状態</label><span id="ppState"></span></div>
<div class="pt-popup-field"><label>電子配置</label><span id="ppElec"></span></div>
<div class="pt-popup-field"><label>発見年</label><span id="ppDisc"></span></div>
<div class="pt-popup-field"><label>周期</label><span id="ppPeriod"></span></div>
<div class="pt-popup-field"><label>族</label><span id="ppGroup"></span></div>
</div>
</div>
</div>

<script>
(function() {
const ELEMENTS = [
[1,"H","水素",1.008,"nonmetal",1,1,"1s¹","気体","太古",1,1],
[2,"He","ヘリウム",4.003,"noble",1,18,"1s²","気体",1895,1,18],
[3,"Li","リチウム",6.941,"alkali",2,1,"[He] 2s¹","固体",1817,2,1],
[4,"Be","ベリリウム",9.012,"alkaline",2,2,"[He] 2s²","固体",1798,2,2],
[5,"B","ホウ素",10.81,"metalloid",2,13,"[He] 2s² 2p¹","固体","太古",2,13],
[6,"C","炭素",12.011,"nonmetal",2,14,"[He] 2s² 2p²","固体","太古",2,14],
[7,"N","窒素",14.007,"nonmetal",2,15,"[He] 2s² 2p³","気体",1772,2,15],
[8,"O","酸素",15.999,"nonmetal",2,16,"[He] 2s² 2p⁴","気体",1774,2,16],
[9,"F","フッ素",18.998,"halogen",2,17,"[He] 2s² 2p⁵","気体",1886,2,17],
[10,"Ne","ネオン",20.18,"noble",2,18,"[He] 2s² 2p⁶","気体",1898,2,18],
[11,"Na","ナトリウム",22.99,"alkali",3,1,"[Ne] 3s¹","固体",1807,3,1],
[12,"Mg","マグネシウム",24.305,"alkaline",3,2,"[Ne] 3s²","固体",1755,3,2],
[13,"Al","アルミニウム",26.982,"post",3,13,"[Ne] 3s² 3p¹","固体",1825,3,13],
[14,"Si","ケイ素",28.086,"metalloid",3,14,"[Ne] 3s² 3p²","固体",1824,3,14],
[15,"P","リン",30.974,"nonmetal",3,15,"[Ne] 3s² 3p³","固体",1669,3,15],
[16,"S","硫黄",32.065,"nonmetal",3,16,"[Ne] 3s² 3p⁴","固体","太古",3,16],
[17,"Cl","塩素",35.453,"halogen",3,17,"[Ne] 3s² 3p⁵","気体",1774,3,17],
[18,"Ar","アルゴン",39.948,"noble",3,18,"[Ne] 3s² 3p⁶","気体",1894,3,18],
[19,"K","カリウム",39.098,"alkali",4,1,"[Ar] 4s¹","固体",1807,4,1],
[20,"Ca","カルシウム",40.078,"alkaline",4,2,"[Ar] 4s²","固体",1808,4,2],
[21,"Sc","スカンジウム",44.956,"transition",4,3,"[Ar] 3d¹ 4s²","固体",1879,4,3],
[22,"Ti","チタン",47.867,"transition",4,4,"[Ar] 3d² 4s²","固体",1791,4,4],
[23,"V","バナジウム",50.942,"transition",4,5,"[Ar] 3d³ 4s²","固体",1801,4,5],
[24,"Cr","クロム",51.996,"transition",4,6,"[Ar] 3d⁵ 4s¹","固体",1797,4,6],
[25,"Mn","マンガン",54.938,"transition",4,7,"[Ar] 3d⁵ 4s²","固体",1774,4,7],
[26,"Fe","鉄",55.845,"transition",4,8,"[Ar] 3d⁶ 4s²","固体","太古",4,8],
[27,"Co","コバルト",58.933,"transition",4,9,"[Ar] 3d⁷ 4s²","固体",1735,4,9],
[28,"Ni","ニッケル",58.693,"transition",4,10,"[Ar] 3d⁸ 4s²","固体",1751,4,10],
[29,"Cu","銅",63.546,"transition",4,11,"[Ar] 3d¹⁰ 4s¹","固体","太古",4,11],
[30,"Zn","亜鉛",65.38,"transition",4,12,"[Ar] 3d¹⁰ 4s²","固体","太古",4,12],
[31,"Ga","ガリウム",69.723,"post",4,13,"[Ar] 3d¹⁰ 4s² 4p¹","固体",1875,4,13],
[32,"Ge","ゲルマニウム",72.63,"metalloid",4,14,"[Ar] 3d¹⁰ 4s² 4p²","固体",1886,4,14],
[33,"As","ヒ素",74.922,"metalloid",4,15,"[Ar] 3d¹⁰ 4s² 4p³","固体","太古",4,15],
[34,"Se","セレン",78.971,"nonmetal",4,16,"[Ar] 3d¹⁰ 4s² 4p⁴","固体",1817,4,16],
[35,"Br","臭素",79.904,"halogen",4,17,"[Ar] 3d¹⁰ 4s² 4p⁵","液体",1826,4,17],
[36,"Kr","クリプトン",83.798,"noble",4,18,"[Ar] 3d¹⁰ 4s² 4p⁶","気体",1898,4,18],
[37,"Rb","ルビジウム",85.468,"alkali",5,1,"[Kr] 5s¹","固体",1861,5,1],
[38,"Sr","ストロンチウム",87.62,"alkaline",5,2,"[Kr] 5s²","固体",1790,5,2],
[39,"Y","イットリウム",88.906,"transition",5,3,"[Kr] 4d¹ 5s²","固体",1794,5,3],
[40,"Zr","ジルコニウム",91.224,"transition",5,4,"[Kr] 4d² 5s²","固体",1789,5,4],
[41,"Nb","ニオブ",92.906,"transition",5,5,"[Kr] 4d⁴ 5s¹","固体",1801,5,5],
[42,"Mo","モリブデン",95.96,"transition",5,6,"[Kr] 4d⁵ 5s¹","固体",1781,5,6],
[43,"Tc","テクネチウム",98,"transition",5,7,"[Kr] 4d⁵ 5s²","固体",1937,5,7],
[44,"Ru","ルテニウム",101.07,"transition",5,8,"[Kr] 4d⁷ 5s¹","固体",1844,5,8],
[45,"Rh","ロジウム",102.906,"transition",5,9,"[Kr] 4d⁸ 5s¹","固体",1803,5,9],
[46,"Pd","パラジウム",106.42,"transition",5,10,"[Kr] 4d¹⁰","固体",1803,5,10],
[47,"Ag","銀",107.868,"transition",5,11,"[Kr] 4d¹⁰ 5s¹","固体","太古",5,11],
[48,"Cd","カドミウム",112.411,"transition",5,12,"[Kr] 4d¹⁰ 5s²","固体",1817,5,12],
[49,"In","インジウム",114.818,"post",5,13,"[Kr] 4d¹⁰ 5s² 5p¹","固体",1863,5,13],
[50,"Sn","スズ",118.71,"post",5,14,"[Kr] 4d¹⁰ 5s² 5p²","固体","太古",5,14],
[51,"Sb","アンチモン",121.76,"metalloid",5,15,"[Kr] 4d¹⁰ 5s² 5p³","固体","太古",5,15],
[52,"Te","テルル",127.6,"metalloid",5,16,"[Kr] 4d¹⁰ 5s² 5p⁴","固体",1782,5,16],
[53,"I","ヨウ素",126.904,"halogen",5,17,"[Kr] 4d¹⁰ 5s² 5p⁵","固体",1811,5,17],
[54,"Xe","キセノン",131.293,"noble",5,18,"[Kr] 4d¹⁰ 5s² 5p⁶","気体",1898,5,18],
[55,"Cs","セシウム",132.905,"alkali",6,1,"[Xe] 6s¹","固体",1860,6,1],
[56,"Ba","バリウム",137.327,"alkaline",6,2,"[Xe] 6s²","固体",1808,6,2],
[57,"La","ランタン",138.905,"lanthanide",8,4,"[Xe] 5d¹ 6s²","固体",1839,6,3],
[58,"Ce","セリウム",140.116,"lanthanide",8,5,"[Xe] 4f¹ 5d¹ 6s²","固体",1803,6,4],
[59,"Pr","プラセオジム",140.908,"lanthanide",8,6,"[Xe] 4f³ 6s²","固体",1885,6,5],
[60,"Nd","ネオジム",144.242,"lanthanide",8,7,"[Xe] 4f⁴ 6s²","固体",1885,6,6],
[61,"Pm","プロメチウム",145,"lanthanide",8,8,"[Xe] 4f⁵ 6s²","固体",1945,6,7],
[62,"Sm","サマリウム",150.36,"lanthanide",8,9,"[Xe] 4f⁶ 6s²","固体",1879,6,8],
[63,"Eu","ユウロピウム",151.964,"lanthanide",8,10,"[Xe] 4f⁷ 6s²","固体",1901,6,9],
[64,"Gd","ガドリニウム",157.25,"lanthanide",8,11,"[Xe] 4f⁷ 5d¹ 6s²","固体",1880,6,10],
[65,"Tb","テルビウム",158.925,"lanthanide",8,12,"[Xe] 4f⁹ 6s²","固体",1843,6,11],
[66,"Dy","ジスプロシウム",162.5,"lanthanide",8,13,"[Xe] 4f¹⁰ 6s²","固体",1886,6,12],
[67,"Ho","ホルミウム",164.93,"lanthanide",8,14,"[Xe] 4f¹¹ 6s²","固体",1867,6,13],
[68,"Er","エルビウム",167.259,"lanthanide",8,15,"[Xe] 4f¹² 6s²","固体",1842,6,14],
[69,"Tm","ツリウム",168.934,"lanthanide",8,16,"[Xe] 4f¹³ 6s²","固体",1879,6,15],
[70,"Yb","イッテルビウム",173.045,"lanthanide",8,17,"[Xe] 4f¹⁴ 6s²","固体",1878,6,16],
[71,"Lu","ルテチウム",174.967,"lanthanide",8,18,"[Xe] 4f¹⁴ 5d¹ 6s²","固体",1907,6,17],
[72,"Hf","ハフニウム",178.49,"transition",6,4,"[Xe] 4f¹⁴ 5d² 6s²","固体",1923,6,4],
[73,"Ta","タンタル",180.948,"transition",6,5,"[Xe] 4f¹⁴ 5d³ 6s²","固体",1802,6,5],
[74,"W","タングステン",183.84,"transition",6,6,"[Xe] 4f¹⁴ 5d⁴ 6s²","固体",1783,6,6],
[75,"Re","レニウム",186.207,"transition",6,7,"[Xe] 4f¹⁴ 5d⁵ 6s²","固体",1925,6,7],
[76,"Os","オスミウム",190.23,"transition",6,8,"[Xe] 4f¹⁴ 5d⁶ 6s²","固体",1803,6,8],
[77,"Ir","イリジウム",192.217,"transition",6,9,"[Xe] 4f¹⁴ 5d⁷ 6s²","固体",1803,6,9],
[78,"Pt","白金",195.084,"transition",6,10,"[Xe] 4f¹⁴ 5d⁹ 6s¹","固体","太古",6,10],
[79,"Au","金",196.967,"transition",6,11,"[Xe] 4f¹⁴ 5d¹⁰ 6s¹","固体","太古",6,11],
[80,"Hg","水銀",200.592,"transition",6,12,"[Xe] 4f¹⁴ 5d¹⁰ 6s²","液体","太古",6,12],
[81,"Tl","タリウム",204.383,"post",6,13,"[Xe] 4f¹⁴ 5d¹⁰ 6s² 6p¹","固体",1861,6,13],
[82,"Pb","鉛",207.2,"post",6,14,"[Xe] 4f¹⁴ 5d¹⁰ 6s² 6p²","固体","太古",6,14],
[83,"Bi","ビスマス",208.98,"post",6,15,"[Xe] 4f¹⁴ 5d¹⁰ 6s² 6p³","固体","太古",6,15],
[84,"Po","ポロニウム",209,"metalloid",6,16,"[Xe] 4f¹⁴ 5d¹⁰ 6s² 6p⁴","固体",1898,6,16],
[85,"At","アスタチン",210,"halogen",6,17,"[Xe] 4f¹⁴ 5d¹⁰ 6s² 6p⁵","固体",1940,6,17],
[86,"Rn","ラドン",222,"noble",6,18,"[Xe] 4f¹⁴ 5d¹⁰ 6s² 6p⁶","気体",1900,6,18],
[87,"Fr","フランシウム",223,"alkali",7,1,"[Rn] 7s¹","固体",1939,7,1],
[88,"Ra","ラジウム",226,"alkaline",7,2,"[Rn] 7s²","固体",1898,7,2],
[89,"Ac","アクチニウム",227,"actinide",9,4,"[Rn] 6d¹ 7s²","固体",1899,7,3],
[90,"Th","トリウム",232.038,"actinide",9,5,"[Rn] 6d² 7s²","固体",1829,7,4],
[91,"Pa","プロトアクチニウム",231.036,"actinide",9,6,"[Rn] 5f² 6d¹ 7s²","固体",1913,7,5],
[92,"U","ウラン",238.029,"actinide",9,7,"[Rn] 5f³ 6d¹ 7s²","固体",1789,7,6],
[93,"Np","ネプツニウム",237,"actinide",9,8,"[Rn] 5f⁴ 6d¹ 7s²","固体",1940,7,7],
[94,"Pu","プルトニウム",244,"actinide",9,9,"[Rn] 5f⁶ 7s²","固体",1940,7,8],
[95,"Am","アメリシウム",243,"actinide",9,10,"[Rn] 5f⁷ 7s²","固体",1944,7,9],
[96,"Cm","キュリウム",247,"actinide",9,11,"[Rn] 5f⁷ 6d¹ 7s²","固体",1944,7,10],
[97,"Bk","バークリウム",247,"actinide",9,12,"[Rn] 5f⁹ 7s²","固体",1949,7,11],
[98,"Cf","カリホルニウム",251,"actinide",9,13,"[Rn] 5f¹⁰ 7s²","固体",1950,7,12],
[99,"Es","アインスタイニウム",252,"actinide",9,14,"[Rn] 5f¹¹ 7s²","固体",1952,7,13],
[100,"Fm","フェルミウム",257,"actinide",9,15,"[Rn] 5f¹² 7s²","固体",1952,7,14],
[101,"Md","メンデレビウム",258,"actinide",9,16,"[Rn] 5f¹³ 7s²","固体",1955,7,15],
[102,"No","ノーベリウム",259,"actinide",9,17,"[Rn] 5f¹⁴ 7s²","固体",1958,7,16],
[103,"Lr","ローレンシウム",262,"actinide",9,18,"[Rn] 5f¹⁴ 7s² 7p¹","固体",1961,7,17],
[104,"Rf","ラザホージウム",267,"transition",7,4,"[Rn] 5f¹⁴ 6d² 7s²","固体",1964,7,4],
[105,"Db","ドブニウム",270,"transition",7,5,"[Rn] 5f¹⁴ 6d³ 7s²","固体",1968,7,5],
[106,"Sg","シーボーギウム",271,"transition",7,6,"[Rn] 5f¹⁴ 6d⁴ 7s²","固体",1974,7,6],
[107,"Bh","ボーリウム",270,"transition",7,7,"[Rn] 5f¹⁴ 6d⁵ 7s²","固体",1981,7,7],
[108,"Hs","ハッシウム",277,"transition",7,8,"[Rn] 5f¹⁴ 6d⁶ 7s²","固体",1984,7,8],
[109,"Mt","マイトネリウム",276,"unknown",7,9,"[Rn] 5f¹⁴ 6d⁷ 7s²","不明",1982,7,9],
[110,"Ds","ダームスタチウム",281,"unknown",7,10,"[Rn] 5f¹⁴ 6d⁸ 7s²","不明",1994,7,10],
[111,"Rg","レントゲニウム",280,"unknown",7,11,"[Rn] 5f¹⁴ 6d⁹ 7s²","不明",1994,7,11],
[112,"Cn","コペルニシウム",285,"transition",7,12,"[Rn] 5f¹⁴ 6d¹⁰ 7s²","気体",1996,7,12],
[113,"Nh","ニホニウム",284,"unknown",7,13,"[Rn] 5f¹⁴ 6d¹⁰ 7s² 7p¹","不明",2004,7,13],
[114,"Fl","フレロビウム",289,"unknown",7,14,"[Rn] 5f¹⁴ 6d¹⁰ 7s² 7p²","不明",1998,7,14],
[115,"Mc","モスコビウム",288,"unknown",7,15,"[Rn] 5f¹⁴ 6d¹⁰ 7s² 7p³","不明",2003,7,15],
[116,"Lv","リバモリウム",293,"unknown",7,16,"[Rn] 5f¹⁴ 6d¹⁰ 7s² 7p⁴","不明",2000,7,16],
[117,"Ts","テネシン",294,"halogen",7,17,"[Rn] 5f¹⁴ 6d¹⁰ 7s² 7p⁵","不明",2010,7,17],
[118,"Og","オガネソン",294,"noble",7,18,"[Rn] 5f¹⁴ 6d¹⁰ 7s² 7p⁶","不明",2006,7,18]
];

const CAT_META = {
alkali:     { label: "アルカリ金属",     cls: "cat-alkali" },
alkaline:   { label: "アルカリ土類金属", cls: "cat-alkaline" },
transition: { label: "遷移金属",         cls: "cat-transition" },
post:       { label: "典型金属",          cls: "cat-post" },
metalloid:  { label: "半金属",            cls: "cat-metalloid" },
nonmetal:   { label: "非金属",            cls: "cat-nonmetal" },
halogen:    { label: "ハロゲン",          cls: "cat-halogen" },
noble:      { label: "希ガス",            cls: "cat-noble" },
lanthanide: { label: "ランタノイド",      cls: "cat-lanthanide" },
actinide:   { label: "アクチノイド",      cls: "cat-actinide" },
unknown:    { label: "性質不明",          cls: "cat-unknown" }
};

const CAT_ORDER = ["alkali","alkaline","transition","post","metalloid","nonmetal","halogen","noble","lanthanide","actinide","unknown"];

// Build legend
const legendEl = document.getElementById('ptLegend');
CAT_ORDER.forEach(key => {
const m = CAT_META[key];
const item = document.createElement('div');
item.className = 'pt-legend-item';
item.dataset.cat = key;
const sw = document.createElement('span');
sw.className = 'pt-legend-swatch ' + m.cls;
const lbl = document.createElement('span');
lbl.textContent = m.label;
item.appendChild(sw);
item.appendChild(lbl);
item.addEventListener('click', () => {
const sel = document.getElementById('ptFilter');
sel.value = sel.value === key ? '' : key;
applyFilters();
});
legendEl.appendChild(item);
});

// Build grid
const grid = document.getElementById('ptGrid');
const posMap = {};
ELEMENTS.forEach(el => {
const key = el[5] + '_' + el[6];
posMap[key] = el;
});

for (let r = 1; r <= 9; r++) {
for (let c = 1; c <= 18; c++) {
const div = document.createElement('div');
div.style.gridRow = r;
div.style.gridColumn = c;

const key = r + '_' + c;
const el = posMap[key];

if (el) {
div.className = 'el ' + CAT_META[el[4]].cls;
div.dataset.num = el[0];
div.dataset.cat = el[4];
div.innerHTML = `
<span class="el-num">${el[0]}</span>
<span class="el-sym">${el[1]}</span>
<span class="el-name">${el[2]}</span>
<span class="el-mass">${el[3]}</span>
`;
div.addEventListener('click', () => openPopup(el));
} else {
if (r === 6 && c === 3) {
div.style.background = '#fde68a';
div.style.borderRadius = '4px';
div.style.border = '1px dashed #d97706';
div.style.display = 'flex';
div.style.alignItems = 'center';
div.style.justifyContent = 'center';
div.style.fontSize = '8px';
div.style.color = '#92400e';
div.style.fontWeight = '600';
div.textContent = '57-71';
} else if (r === 7 && c === 3) {
div.style.background = '#d9f99d';
div.style.borderRadius = '4px';
div.style.border = '1px dashed #65a30d';
div.style.display = 'flex';
div.style.alignItems = 'center';
div.style.justifyContent = 'center';
div.style.fontSize = '8px';
div.style.color = '#3f6212';
div.style.fontWeight = '600';
div.textContent = '89-103';
} else if (r === 8 && c === 1) {
div.style.gridColumn = '1 / 4';
div.style.display = 'flex';
div.style.alignItems = 'center';
div.style.justifyContent = 'flex-end';
div.style.paddingRight = '4px';
div.style.fontSize = '8px';
div.style.fontWeight = '700';
div.style.color = '#92400e';
div.textContent = 'ランタノイド →';
grid.appendChild(div);
continue;
} else if (r === 9 && c === 1) {
div.style.gridColumn = '1 / 4';
div.style.display = 'flex';
div.style.alignItems = 'center';
div.style.justifyContent = 'flex-end';
div.style.paddingRight = '4px';
div.style.fontSize = '8px';
div.style.fontWeight = '700';
div.style.color = '#3f6212';
div.textContent = 'アクチノイド →';
grid.appendChild(div);
continue;
} else if (r === 8 && (c === 2 || c === 3)) {
continue;
} else if (r === 9 && (c === 2 || c === 3)) {
continue;
}
}
grid.appendChild(div);
}
}

// Popup
function openPopup(el) {
const [num, sym, name, mass, cat, , , econfig, state, year, period, group] = el;
const m = CAT_META[cat];
document.getElementById('ppSym').textContent = sym;
document.getElementById('ppNumSmall').textContent = '#' + num;
document.getElementById('ppSymBox').className = 'pt-popup-sym-box ' + m.cls;
document.getElementById('ppName').textContent = name;
document.getElementById('ppCat').textContent = m.label;
document.getElementById('ppNum').textContent = num;
document.getElementById('ppMass').textContent = mass + ' u';
document.getElementById('ppCatFull').textContent = m.label;
document.getElementById('ppState').textContent = state;
document.getElementById('ppElec').textContent = econfig;
document.getElementById('ppDisc').textContent = year;
document.getElementById('ppPeriod').textContent = period + '周期';
document.getElementById('ppGroup').textContent = group + '族';
document.getElementById('ptOverlay').classList.add('open');
}

document.getElementById('ptClose').addEventListener('click', closePopup);
document.getElementById('ptOverlay').addEventListener('click', function(e) {
if (e.target === this) closePopup();
});
document.addEventListener('keydown', function(e) {
if (e.key === 'Escape') closePopup();
});
function closePopup() {
document.getElementById('ptOverlay').classList.remove('open');
}

// Filter / search
function applyFilters() {
const q = document.getElementById('ptSearch').value.toLowerCase().trim();
const cat = document.getElementById('ptFilter').value;

const allEls = document.querySelectorAll('#ptGrid .el');
allEls.forEach(div => {
const elNum = parseInt(div.dataset.num);
const elData = ELEMENTS.find(e => e[0] === elNum);
if (!elData) return;

const matchSearch = !q ||
elData[2].toLowerCase().includes(q) ||
elData[1].toLowerCase().includes(q);
const matchCat = !cat || elData[4] === cat;
const match = matchSearch && matchCat;

if (!q && !cat) {
div.classList.remove('dimmed', 'highlighted');
} else if (match) {
div.classList.remove('dimmed');
div.classList.add('highlighted');
} else {
div.classList.add('dimmed');
div.classList.remove('highlighted');
}
});
}

document.getElementById('ptSearch').addEventListener('input', applyFilters);
document.getElementById('ptFilter').addEventListener('change', applyFilters);
document.getElementById('ptClear').addEventListener('click', () => {
document.getElementById('ptSearch').value = '';
document.getElementById('ptFilter').value = '';
applyFilters();
});
})();
</script>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">研究費・実験材料費の管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、研究費用・材料費の経費管理もクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

</div>

---

**関連ツール:**
- 単位変換 → [単位変換ツール](/ja/tools/unit-converter/)
- 関数電卓 → [関数電卓](/ja/tools/scientific-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
