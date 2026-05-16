---
title: "料理単位変換ツール - キッチン計量換算計算機"
date: 2025-05-16
description: "カップ、大さじ、小さじ、ml、グラム、オンスなど料理の計量単位を相互変換。レシピのスケールアップ・ダウンにも対応。"
categories: ["無料ツール"]
slug: "cooking-unit-converter"
ShowToc: false
cover:
  image: "/images/covers/cooking-unit-converter.png"
  alt: "料理単位変換ツール"
---

<div id="cu-app">

<style>
#cu-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1a1a2e;
  line-height: 1.7;
}
#cu-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 1.8rem 0 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid #e85d26;
}
#cu-app .tabs {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}
#cu-app .tab-btn {
  padding: 0.55rem 1.1rem;
  border: 2px solid #e0e0e0;
  border-radius: 2rem;
  background: #fff;
  color: #555;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}
#cu-app .tab-btn.active,
#cu-app .tab-btn:hover {
  background: #e85d26;
  border-color: #e85d26;
  color: #fff;
}
#cu-app .panel {
  display: none;
  background: #fff;
  border: 1px solid #e8e8e8;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.06);
}
#cu-app .panel.active { display: block; }
#cu-app .converter-grid {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1rem;
  align-items: end;
  margin-bottom: 1rem;
}
#cu-app .swap-btn {
  background: #e85d26;
  color: #fff;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 0.2rem;
}
#cu-app .swap-btn:hover { background: #c94e1f; }
#cu-app label {
  display: block;
  font-size: 0.82rem;
  font-weight: 700;
  color: #666;
  margin-bottom: 0.3rem;
  letter-spacing: 0.02em;
}
#cu-app input[type="number"],
#cu-app select {
  width: 100%;
  padding: 0.65rem 0.8rem;
  border: 1.5px solid #ddd;
  border-radius: 8px;
  font-size: 1rem;
  background: #fafafa;
  box-sizing: border-box;
  transition: border-color 0.2s;
  font-family: inherit;
}
#cu-app input[type="number"]:focus,
#cu-app select:focus {
  outline: none;
  border-color: #e85d26;
  background: #fff;
}
#cu-app .result-box {
  background: linear-gradient(135deg, #fff3ee, #fff);
  border: 1.5px solid #e85d26;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  margin-top: 1rem;
  text-align: center;
}
#cu-app .result-box .result-value {
  font-size: 2rem;
  font-weight: 800;
  color: #e85d26;
}
#cu-app .result-box .result-label {
  font-size: 0.88rem;
  color: #888;
  margin-top: 0.2rem;
}
#cu-app .ingredient-row {
  display: flex;
  gap: 0.8rem;
  margin-bottom: 1rem;
  align-items: end;
  flex-wrap: wrap;
}
#cu-app .ingredient-row > div {
  flex: 1;
  min-width: 120px;
}
#cu-app .scaler-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1rem;
}
#cu-app .scaler-ingredients { margin-top: 1rem; }
#cu-app .scaler-ingredient-item {
  display: grid;
  grid-template-columns: 1fr 1fr auto;
  gap: 0.6rem;
  margin-bottom: 0.5rem;
  align-items: center;
}
#cu-app .scaler-ingredient-item input,
#cu-app .scaler-ingredient-item select {
  padding: 0.5rem 0.6rem;
  font-size: 0.9rem;
}
#cu-app .remove-btn {
  background: #ff5555;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 0.5rem 0.7rem;
  cursor: pointer;
  font-size: 0.85rem;
}
#cu-app .remove-btn:hover { background: #cc3333; }
#cu-app .add-btn {
  background: #e8f5e9;
  color: #2e7d32;
  border: 1.5px solid #a5d6a7;
  border-radius: 8px;
  padding: 0.5rem 1rem;
  cursor: pointer;
  font-size: 0.88rem;
  font-weight: 600;
  margin-right: 0.5rem;
  font-family: inherit;
}
#cu-app .add-btn:hover { background: #c8e6c9; }
#cu-app .calc-btn {
  background: #e85d26;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0.55rem 1.2rem;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: 700;
  font-family: inherit;
}
#cu-app .calc-btn:hover { background: #c94e1f; }
#cu-app .scaler-result {
  background: #f8f9fa;
  border-radius: 10px;
  padding: 1rem;
  margin-top: 1rem;
}
#cu-app .scaler-result table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.92rem;
}
#cu-app .scaler-result th {
  text-align: left;
  padding: 0.4rem 0.6rem;
  background: #e85d26;
  color: #fff;
  border-radius: 4px;
}
#cu-app .scaler-result td {
  padding: 0.4rem 0.6rem;
  border-bottom: 1px solid #eee;
}
#cu-app .scaler-result tr:last-child td { border-bottom: none; }
#cu-app .ref-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.87rem;
  margin-top: 0.5rem;
}
#cu-app .ref-table th {
  background: #1a1a2e;
  color: #fff;
  padding: 0.55rem 0.8rem;
  text-align: left;
}
#cu-app .ref-table td {
  padding: 0.5rem 0.8rem;
  border-bottom: 1px solid #eee;
}
#cu-app .ref-table tr:nth-child(even) td { background: #f9f9f9; }
#cu-app .tip-box {
  background: #fff3e0;
  border-left: 4px solid #e85d26;
  border-radius: 0 8px 8px 0;
  padding: 0.8rem 1rem;
  margin: 1rem 0;
  font-size: 0.87rem;
  color: #7b3d00;
}
#cu-app .freee-cta {
  background: linear-gradient(135deg, #e8f4fd, #eef7ff);
  border: 1px solid #90caf9;
  border-radius: 10px;
  padding: 1rem 1.2rem;
  margin-top: 2rem;
  font-size: 0.9rem;
}
#cu-app .freee-cta p { margin: 0; }
#cu-app .freee-cta a {
  color: #1565c0;
  font-weight: 700;
  text-decoration: none;
}
#cu-app .freee-cta a:hover { text-decoration: underline; }
@media (max-width: 600px) {
  #cu-app .converter-grid { grid-template-columns: 1fr; }
  #cu-app .swap-btn { margin: 0 auto; transform: rotate(90deg); }
  #cu-app .scaler-row { grid-template-columns: 1fr; }
  #cu-app .ref-table { font-size: 0.78rem; }
  #cu-app .ref-table th, #cu-app .ref-table td { padding: 0.4rem 0.5rem; }
}
</style>

<h2>料理単位変換ツール</h2>

<div class="tabs">
  <button class="tab-btn active" onclick="cuShowTab('volume')">容量</button>
  <button class="tab-btn" onclick="cuShowTab('weight')">重量</button>
  <button class="tab-btn" onclick="cuShowTab('jp')">日本の単位</button>
  <button class="tab-btn" onclick="cuShowTab('ingredient')">食材別換算</button>
  <button class="tab-btn" onclick="cuShowTab('scaler')">レシピスケール</button>
  <button class="tab-btn" onclick="cuShowTab('reference')">早見表</button>
</div>

<!-- 容量タブ -->
<div id="cu-tab-volume" class="panel active">
  <div class="converter-grid">
    <div>
      <label>数量</label>
      <input type="number" id="vol-amount" value="1" min="0" step="any" oninput="cuConvertVolume()">
    </div>
    <div style="display:flex;align-items:flex-end;padding-bottom:0.2rem;">
      <button class="swap-btn" onclick="cuSwapVolume()" title="単位を入れ替え">&#8644;</button>
    </div>
    <div>
      <label>換算結果</label>
      <input type="number" id="vol-result" value="" min="0" step="any" oninput="cuConvertVolumeReverse()">
    </div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1rem;">
    <div>
      <label>変換元の単位</label>
      <select id="vol-from" onchange="cuConvertVolume()">
        <option value="cup">カップ（米国）</option>
        <option value="tbsp">大さじ（tbsp）</option>
        <option value="tsp">小さじ（tsp）</option>
        <option value="ml">ミリリットル（ml/cc）</option>
        <option value="liter">リットル（L）</option>
        <option value="floz">液量オンス（fl oz）</option>
      </select>
    </div>
    <div>
      <label>変換先の単位</label>
      <select id="vol-to" onchange="cuConvertVolume()">
        <option value="cup">カップ（米国）</option>
        <option value="tbsp">大さじ（tbsp）</option>
        <option value="tsp">小さじ（tsp）</option>
        <option value="ml" selected>ミリリットル（ml/cc）</option>
        <option value="liter">リットル（L）</option>
        <option value="floz">液量オンス（fl oz）</option>
      </select>
    </div>
  </div>
  <div class="result-box" id="vol-result-box">
    <div class="result-value" id="vol-result-display">236.59 ml</div>
    <div class="result-label">1 カップ（米国）= 236.59 ml</div>
  </div>
  <div class="tip-box">
    ヒント：米国カップ1杯 = 大さじ16杯 = 小さじ48杯 = 約236.6ml = 8 fl oz
  </div>
</div>

<!-- 重量タブ -->
<div id="cu-tab-weight" class="panel">
  <div class="converter-grid">
    <div>
      <label>数量</label>
      <input type="number" id="wt-amount" value="1" min="0" step="any" oninput="cuConvertWeight()">
    </div>
    <div style="display:flex;align-items:flex-end;padding-bottom:0.2rem;">
      <button class="swap-btn" onclick="cuSwapWeight()" title="単位を入れ替え">&#8644;</button>
    </div>
    <div>
      <label>換算結果</label>
      <input type="number" id="wt-result" value="" min="0" step="any" oninput="cuConvertWeightReverse()">
    </div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1rem;">
    <div>
      <label>変換元の単位</label>
      <select id="wt-from" onchange="cuConvertWeight()">
        <option value="g">グラム（g）</option>
        <option value="kg">キログラム（kg）</option>
        <option value="oz">オンス（oz）</option>
        <option value="lb">ポンド（lb）</option>
      </select>
    </div>
    <div>
      <label>変換先の単位</label>
      <select id="wt-to" onchange="cuConvertWeight()">
        <option value="g">グラム（g）</option>
        <option value="kg">キログラム（kg）</option>
        <option value="oz" selected>オンス（oz）</option>
        <option value="lb">ポンド（lb）</option>
      </select>
    </div>
  </div>
  <div class="result-box" id="wt-result-box">
    <div class="result-value" id="wt-result-display">0.035 oz</div>
    <div class="result-label">1 グラム（g）= 0.035 オンス（oz）</div>
  </div>
  <div class="tip-box">
    ヒント：1 oz = 28.35 g ｜ 1 lb = 16 oz = 453.6 g ｜ 1 kg = 2.205 lb
  </div>
</div>

<!-- 日本の単位タブ -->
<div id="cu-tab-jp" class="panel">
  <p style="font-size:0.9rem;color:#555;margin-top:0;">日本特有の料理・計量単位（合・勺・升）を他の単位へ変換します。</p>
  <div class="converter-grid">
    <div>
      <label>数量</label>
      <input type="number" id="jp-amount" value="1" min="0" step="any" oninput="cuConvertJP()">
    </div>
    <div style="display:flex;align-items:flex-end;padding-bottom:0.2rem;">
      <button class="swap-btn" onclick="cuSwapJP()" title="単位を入れ替え">&#8644;</button>
    </div>
    <div>
      <label>換算結果</label>
      <input type="number" id="jp-result" value="" min="0" step="any" oninput="cuConvertJPReverse()">
    </div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1rem;">
    <div>
      <label>変換元の単位</label>
      <select id="jp-from" onchange="cuConvertJP()">
        <option value="go">合（ごう）</option>
        <option value="shaku">勺（しゃく）</option>
        <option value="sho">升（しょう）</option>
        <option value="tbsp_jp">大さじ</option>
        <option value="tsp_jp">小さじ</option>
        <option value="cc">cc（= ml）</option>
        <option value="ml_jp">ml</option>
        <option value="cup_jp">カップ（日本：200ml）</option>
      </select>
    </div>
    <div>
      <label>変換先の単位</label>
      <select id="jp-to" onchange="cuConvertJP()">
        <option value="go">合（ごう）</option>
        <option value="shaku">勺（しゃく）</option>
        <option value="sho">升（しょう）</option>
        <option value="tbsp_jp">大さじ</option>
        <option value="tsp_jp">小さじ</option>
        <option value="cc">cc（= ml）</option>
        <option value="ml_jp" selected>ml</option>
        <option value="cup_jp">カップ（日本：200ml）</option>
      </select>
    </div>
  </div>
  <div class="result-box" id="jp-result-box">
    <div class="result-value" id="jp-result-display">180 ml</div>
    <div class="result-label">1 合 = 180 ml</div>
  </div>
  <div class="tip-box">
    ヒント：1合 = 180ml ｜ 大さじ1 = 15ml ｜ 小さじ1 = 5ml ｜ 日本のカップ = 200ml（米国カップ≠日本カップ）
  </div>
  <div id="jp-all-conversions" style="margin-top:1rem;"></div>
</div>

<!-- 食材別換算タブ -->
<div id="cu-tab-ingredient" class="panel">
  <p style="font-size:0.9rem;color:#555;margin-top:0;">食材の密度を考慮して、容量と重量を相互変換します。</p>
  <div class="ingredient-row">
    <div>
      <label>食材</label>
      <select id="ing-type" onchange="cuConvertIngredient()">
        <option value="water">水</option>
        <option value="milk">牛乳</option>
        <option value="flour">薄力粉（小麦粉）</option>
        <option value="strong_flour">強力粉</option>
        <option value="sugar_white">上白糖（グラニュー糖）</option>
        <option value="sugar_brown">黒糖・三温糖（詰め込み）</option>
        <option value="sugar_powder">粉砂糖</option>
        <option value="butter">バター</option>
        <option value="oil">サラダ油・植物油</option>
        <option value="soy_sauce">醤油</option>
        <option value="miso">味噌</option>
        <option value="honey">はちみつ</option>
        <option value="rice">米（生）</option>
        <option value="salt">塩</option>
        <option value="katakuriko">片栗粉</option>
      </select>
    </div>
    <div>
      <label>数量</label>
      <input type="number" id="ing-amount" value="1" min="0" step="any" oninput="cuConvertIngredient()">
    </div>
    <div>
      <label>単位</label>
      <select id="ing-from" onchange="cuConvertIngredient()">
        <option value="cup_jp">カップ（日本 200ml）</option>
        <option value="tbsp_jp">大さじ（15ml）</option>
        <option value="tsp_jp">小さじ（5ml）</option>
        <option value="ml">ml / cc</option>
        <option value="go">合（180ml）</option>
        <option value="g">グラム（g）</option>
        <option value="oz">オンス（oz）</option>
      </select>
    </div>
  </div>
  <div class="result-box" id="ing-result-box">
    <div class="result-value" id="ing-result-display">--</div>
    <div class="result-label" id="ing-result-label">食材と数量を選択してください</div>
  </div>
  <div id="ing-all-conversions" style="margin-top:1rem;"></div>
</div>

<!-- レシピスケールタブ -->
<div id="cu-tab-scaler" class="panel">
  <p style="font-size:0.9rem;color:#555;margin-top:0;">レシピの人数に合わせて材料の分量を自動計算します。</p>
  <div class="scaler-row">
    <div>
      <label>元のレシピ人数</label>
      <input type="number" id="sc-original" value="4" min="0.1" step="any">
    </div>
    <div>
      <label>作りたい人数</label>
      <input type="number" id="sc-desired" value="6" min="0.1" step="any">
    </div>
  </div>
  <div class="scaler-ingredients" id="sc-ingredients">
    <label style="margin-bottom:0.5rem;display:block;">材料リスト</label>
    <div class="scaler-ingredient-item" id="sc-row-0">
      <input type="number" placeholder="分量" value="2" min="0" step="any">
      <select>
        <option value="カップ">カップ</option>
        <option value="大さじ">大さじ</option>
        <option value="小さじ">小さじ</option>
        <option value="合">合</option>
        <option value="ml">ml</option>
        <option value="g">g</option>
        <option value="個">個</option>
        <option value="枚">枚</option>
        <option value="本">本</option>
      </select>
      <button class="remove-btn" onclick="cuRemoveRow(this)">&#10005;</button>
    </div>
    <div class="scaler-ingredient-item" id="sc-row-1">
      <input type="number" placeholder="分量" value="3" min="0" step="any">
      <select>
        <option value="カップ">カップ</option>
        <option value="大さじ" selected>大さじ</option>
        <option value="小さじ">小さじ</option>
        <option value="合">合</option>
        <option value="ml">ml</option>
        <option value="g">g</option>
        <option value="個">個</option>
        <option value="枚">枚</option>
        <option value="本">本</option>
      </select>
      <button class="remove-btn" onclick="cuRemoveRow(this)">&#10005;</button>
    </div>
  </div>
  <div style="margin-top:0.8rem;">
    <button class="add-btn" onclick="cuAddRow()">+ 材料を追加</button>
    <button class="calc-btn" onclick="cuScaleRecipe()">計算する</button>
  </div>
  <div class="scaler-result" id="sc-result" style="display:none;">
    <table>
      <thead>
        <tr>
          <th>元の分量</th>
          <th>換算後の分量</th>
        </tr>
      </thead>
      <tbody id="sc-result-body"></tbody>
    </table>
    <div style="font-size:0.82rem;color:#888;margin-top:0.6rem;" id="sc-factor-label"></div>
  </div>
</div>

<!-- 早見表タブ -->
<div id="cu-tab-reference" class="panel">
  <h2>日本の料理単位早見表</h2>
  <table class="ref-table">
    <thead>
      <tr>
        <th>単位</th>
        <th>ml / cc</th>
        <th>大さじ</th>
        <th>小さじ</th>
        <th>合</th>
        <th>米国カップ</th>
      </tr>
    </thead>
    <tbody>
      <tr><td><strong>1合（180ml）</strong></td><td>180</td><td>12</td><td>36</td><td>1</td><td>0.76</td></tr>
      <tr><td><strong>1升（1800ml）</strong></td><td>1800</td><td>120</td><td>360</td><td>10</td><td>7.61</td></tr>
      <tr><td><strong>日本カップ1（200ml）</strong></td><td>200</td><td>13.3</td><td>40</td><td>1.11</td><td>0.85</td></tr>
      <tr><td><strong>大さじ1（15ml）</strong></td><td>15</td><td>1</td><td>3</td><td>0.083</td><td>0.063</td></tr>
      <tr><td><strong>小さじ1（5ml）</strong></td><td>5</td><td>0.333</td><td>1</td><td>0.028</td><td>0.021</td></tr>
      <tr><td><strong>米国カップ1（236.6ml）</strong></td><td>236.6</td><td>15.77</td><td>47.3</td><td>1.31</td><td>1</td></tr>
    </tbody>
  </table>

  <h2>食材1カップ（日本 200ml）あたりの重量</h2>
  <table class="ref-table">
    <thead>
      <tr>
        <th>食材</th>
        <th>グラム（g）</th>
        <th>大さじ1（g）</th>
        <th>小さじ1（g）</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>水・だし</td><td>200 g</td><td>15 g</td><td>5 g</td></tr>
      <tr><td>牛乳</td><td>206 g</td><td>15.5 g</td><td>5.2 g</td></tr>
      <tr><td>薄力粉</td><td>106 g</td><td>8 g</td><td>2.7 g</td></tr>
      <tr><td>強力粉</td><td>110 g</td><td>8.3 g</td><td>2.8 g</td></tr>
      <tr><td>上白糖</td><td>169 g</td><td>9 g</td><td>3 g</td></tr>
      <tr><td>塩</td><td>240 g</td><td>18 g</td><td>6 g</td></tr>
      <tr><td>醤油</td><td>230 g</td><td>18 g</td><td>6 g</td></tr>
      <tr><td>味噌</td><td>—</td><td>18 g</td><td>6 g</td></tr>
      <tr><td>バター</td><td>191 g</td><td>14.3 g</td><td>4.8 g</td></tr>
      <tr><td>サラダ油</td><td>184 g</td><td>13.8 g</td><td>4.6 g</td></tr>
      <tr><td>米（生）</td><td>158 g</td><td>—</td><td>—</td></tr>
      <tr><td>片栗粉</td><td>130 g</td><td>9 g</td><td>3 g</td></tr>
    </tbody>
  </table>

  <h2>重量早見表</h2>
  <table class="ref-table">
    <thead>
      <tr>
        <th>換算元</th>
        <th>グラム（g）</th>
        <th>kg</th>
        <th>オンス（oz）</th>
        <th>ポンド（lb）</th>
      </tr>
    </thead>
    <tbody>
      <tr><td><strong>1グラム</strong></td><td>1</td><td>0.001</td><td>0.035</td><td>0.0022</td></tr>
      <tr><td><strong>1キログラム</strong></td><td>1000</td><td>1</td><td>35.27</td><td>2.205</td></tr>
      <tr><td><strong>1オンス</strong></td><td>28.35</td><td>0.028</td><td>1</td><td>0.0625</td></tr>
      <tr><td><strong>1ポンド</strong></td><td>453.6</td><td>0.454</td><td>16</td><td>1</td></tr>
    </tbody>
  </table>
</div>

<div class="freee-cta">
  <p>家計管理を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で食費を自動管理</a></p>
</div>

<script>
(function() {
  // --- 容量換算（基準：ml）---
  var VOL_TO_ML = {
    cup: 236.5882,
    tbsp: 14.7868,
    tsp: 4.9289,
    ml: 1,
    liter: 1000,
    floz: 29.5735
  };
  var VOL_NAMES = {
    cup: 'カップ（米国）', tbsp: '大さじ', tsp: '小さじ',
    ml: 'ml', liter: 'リットル', floz: 'fl oz'
  };

  // --- 重量換算（基準：g）---
  var WT_TO_G = { g: 1, kg: 1000, oz: 28.3495, lb: 453.592 };
  var WT_NAMES = { g: 'グラム（g）', kg: 'kg', oz: 'オンス（oz）', lb: 'ポンド（lb）' };

  // --- 日本の単位（基準：ml）---
  var JP_TO_ML = {
    go: 180,
    shaku: 18,
    sho: 1800,
    tbsp_jp: 15,
    tsp_jp: 5,
    cc: 1,
    ml_jp: 1,
    cup_jp: 200
  };
  var JP_NAMES = {
    go: '合', shaku: '勺', sho: '升',
    tbsp_jp: '大さじ', tsp_jp: '小さじ',
    cc: 'cc', ml_jp: 'ml', cup_jp: 'カップ（日本 200ml）'
  };

  // --- 食材密度（g/ml）- 日本基準 ---
  var ING_DENSITY = {
    water: 1.0, milk: 1.03, flour: 0.53, strong_flour: 0.55,
    sugar_white: 0.845, sugar_brown: 0.930, sugar_powder: 0.507,
    butter: 0.955, oil: 0.920, soy_sauce: 1.15, miso: 1.10,
    honey: 1.436, rice: 0.79, salt: 1.20, katakuriko: 0.65
  };
  var ING_NAMES = {
    water: '水', milk: '牛乳', flour: '薄力粉', strong_flour: '強力粉',
    sugar_white: '上白糖', sugar_brown: '黒糖・三温糖', sugar_powder: '粉砂糖',
    butter: 'バター', oil: 'サラダ油', soy_sauce: '醤油', miso: '味噌',
    honey: 'はちみつ', rice: '米（生）', salt: '塩', katakuriko: '片栗粉'
  };
  var ING_VOL_TO_ML = {
    cup_jp: 200, tbsp_jp: 15, tsp_jp: 5, ml: 1, go: 180, g: null, oz: null
  };

  function cuFmt(n) {
    if (n === null || isNaN(n)) return '--';
    if (Math.abs(n) >= 1000) return parseFloat(n.toFixed(2)).toLocaleString();
    if (Math.abs(n) >= 10) return parseFloat(n.toFixed(2)).toString();
    if (Math.abs(n) >= 0.01) return parseFloat(n.toFixed(3)).toString();
    return parseFloat(n.toFixed(5)).toString();
  }

  window.cuShowTab = function(tab) {
    document.querySelectorAll('#cu-app .panel').forEach(function(p) { p.classList.remove('active'); });
    document.querySelectorAll('#cu-app .tab-btn').forEach(function(b) { b.classList.remove('active'); });
    document.getElementById('cu-tab-' + tab).classList.add('active');
    event.target.classList.add('active');
  };

  // 容量換算
  window.cuConvertVolume = function() {
    var amt = parseFloat(document.getElementById('vol-amount').value);
    var from = document.getElementById('vol-from').value;
    var to = document.getElementById('vol-to').value;
    if (isNaN(amt)) return;
    var ml = amt * VOL_TO_ML[from];
    var res = ml / VOL_TO_ML[to];
    document.getElementById('vol-result').value = cuFmt(res);
    document.getElementById('vol-result-display').textContent = cuFmt(res) + ' ' + VOL_NAMES[to];
    document.querySelector('#vol-result-box .result-label').textContent =
      cuFmt(amt) + ' ' + VOL_NAMES[from] + ' = ' + cuFmt(res) + ' ' + VOL_NAMES[to];
  };
  window.cuConvertVolumeReverse = function() {
    var amt = parseFloat(document.getElementById('vol-result').value);
    var from = document.getElementById('vol-from').value;
    var to = document.getElementById('vol-to').value;
    if (isNaN(amt)) return;
    var ml = amt * VOL_TO_ML[to];
    var res = ml / VOL_TO_ML[from];
    document.getElementById('vol-amount').value = cuFmt(res);
    document.getElementById('vol-result-display').textContent = cuFmt(amt) + ' ' + VOL_NAMES[to];
    document.querySelector('#vol-result-box .result-label').textContent =
      cuFmt(res) + ' ' + VOL_NAMES[from] + ' = ' + cuFmt(amt) + ' ' + VOL_NAMES[to];
  };
  window.cuSwapVolume = function() {
    var f = document.getElementById('vol-from');
    var t = document.getElementById('vol-to');
    var tmp = f.value; f.value = t.value; t.value = tmp;
    cuConvertVolume();
  };

  // 重量換算
  window.cuConvertWeight = function() {
    var amt = parseFloat(document.getElementById('wt-amount').value);
    var from = document.getElementById('wt-from').value;
    var to = document.getElementById('wt-to').value;
    if (isNaN(amt)) return;
    var g = amt * WT_TO_G[from];
    var res = g / WT_TO_G[to];
    document.getElementById('wt-result').value = cuFmt(res);
    document.getElementById('wt-result-display').textContent = cuFmt(res) + ' ' + WT_NAMES[to];
    document.querySelector('#wt-result-box .result-label').textContent =
      cuFmt(amt) + ' ' + WT_NAMES[from] + ' = ' + cuFmt(res) + ' ' + WT_NAMES[to];
  };
  window.cuConvertWeightReverse = function() {
    var amt = parseFloat(document.getElementById('wt-result').value);
    var from = document.getElementById('wt-from').value;
    var to = document.getElementById('wt-to').value;
    if (isNaN(amt)) return;
    var g = amt * WT_TO_G[to];
    var res = g / WT_TO_G[from];
    document.getElementById('wt-amount').value = cuFmt(res);
    document.getElementById('wt-result-display').textContent = cuFmt(amt) + ' ' + WT_NAMES[to];
    document.querySelector('#wt-result-box .result-label').textContent =
      cuFmt(res) + ' ' + WT_NAMES[from] + ' = ' + cuFmt(amt) + ' ' + WT_NAMES[to];
  };
  window.cuSwapWeight = function() {
    var f = document.getElementById('wt-from');
    var t = document.getElementById('wt-to');
    var tmp = f.value; f.value = t.value; t.value = tmp;
    cuConvertWeight();
  };

  // 日本単位換算
  window.cuConvertJP = function() {
    var amt = parseFloat(document.getElementById('jp-amount').value);
    var from = document.getElementById('jp-from').value;
    var to = document.getElementById('jp-to').value;
    if (isNaN(amt)) return;
    var ml = amt * JP_TO_ML[from];
    var res = ml / JP_TO_ML[to];
    document.getElementById('jp-result').value = cuFmt(res);
    document.getElementById('jp-result-display').textContent = cuFmt(res) + ' ' + JP_NAMES[to];
    document.querySelector('#jp-result-box .result-label').textContent =
      cuFmt(amt) + ' ' + JP_NAMES[from] + ' = ' + cuFmt(res) + ' ' + JP_NAMES[to];
    // All conversions
    var ml_val = amt * JP_TO_ML[from];
    var html = '<table class="ref-table" style="font-size:0.85rem;"><thead><tr><th>単位</th><th>換算値</th></tr></thead><tbody>';
    Object.keys(JP_TO_ML).forEach(function(unit) {
      html += '<tr><td>' + JP_NAMES[unit] + '</td><td>' + cuFmt(ml_val / JP_TO_ML[unit]) + ' ' + JP_NAMES[unit] + '</td></tr>';
    });
    html += '</tbody></table>';
    document.getElementById('jp-all-conversions').innerHTML = html;
  };
  window.cuConvertJPReverse = function() {
    var amt = parseFloat(document.getElementById('jp-result').value);
    var from = document.getElementById('jp-from').value;
    var to = document.getElementById('jp-to').value;
    if (isNaN(amt)) return;
    var ml = amt * JP_TO_ML[to];
    var res = ml / JP_TO_ML[from];
    document.getElementById('jp-amount').value = cuFmt(res);
    document.getElementById('jp-result-display').textContent = cuFmt(amt) + ' ' + JP_NAMES[to];
    document.querySelector('#jp-result-box .result-label').textContent =
      cuFmt(res) + ' ' + JP_NAMES[from] + ' = ' + cuFmt(amt) + ' ' + JP_NAMES[to];
  };
  window.cuSwapJP = function() {
    var f = document.getElementById('jp-from');
    var t = document.getElementById('jp-to');
    var tmp = f.value; f.value = t.value; t.value = tmp;
    cuConvertJP();
  };

  // 食材別換算
  window.cuConvertIngredient = function() {
    var ing = document.getElementById('ing-type').value;
    var amt = parseFloat(document.getElementById('ing-amount').value);
    var from = document.getElementById('ing-from').value;
    if (isNaN(amt)) return;
    var density = ING_DENSITY[ing];
    var grams, ml_val;
    if (from === 'g') {
      grams = amt;
      ml_val = grams / density;
    } else if (from === 'oz') {
      grams = amt * 28.3495;
      ml_val = grams / density;
    } else {
      ml_val = amt * ING_VOL_TO_ML[from];
      grams = ml_val * density;
    }
    var res = document.getElementById('ing-result-display');
    var lbl = document.getElementById('ing-result-label');
    if (from === 'g' || from === 'oz') {
      res.textContent = cuFmt(ml_val) + ' ml  /  ' + cuFmt(ml_val/15) + ' 大さじ';
      lbl.textContent = cuFmt(grams) + ' g の ' + ING_NAMES[ing];
    } else {
      res.textContent = cuFmt(grams) + ' g  /  ' + cuFmt(grams/28.3495) + ' oz';
      lbl.textContent = cuFmt(amt) + ' ' + (ING_VOL_TO_ML[from] === 200 ? 'カップ' : from === 'tbsp_jp' ? '大さじ' : from === 'tsp_jp' ? '小さじ' : from === 'go' ? '合' : from) + ' の ' + ING_NAMES[ing];
    }
    var html = '<table class="ref-table" style="font-size:0.85rem;"><thead><tr><th>単位</th><th>換算値</th></tr></thead><tbody>';
    html += '<tr><td>グラム（g）</td><td>' + cuFmt(grams) + ' g</td></tr>';
    html += '<tr><td>オンス（oz）</td><td>' + cuFmt(grams/28.3495) + ' oz</td></tr>';
    html += '<tr><td>ml / cc</td><td>' + cuFmt(ml_val) + ' ml</td></tr>';
    html += '<tr><td>大さじ</td><td>' + cuFmt(ml_val/15) + ' 大さじ</td></tr>';
    html += '<tr><td>小さじ</td><td>' + cuFmt(ml_val/5) + ' 小さじ</td></tr>';
    html += '<tr><td>カップ（日本 200ml）</td><td>' + cuFmt(ml_val/200) + ' カップ</td></tr>';
    html += '<tr><td>合（180ml）</td><td>' + cuFmt(ml_val/180) + ' 合</td></tr>';
    html += '<tr><td>米国カップ（236.6ml）</td><td>' + cuFmt(ml_val/236.5882) + ' cup</td></tr>';
    html += '</tbody></table>';
    document.getElementById('ing-all-conversions').innerHTML = html;
  };

  // レシピスケール
  var cuRowCount = 2;
  window.cuAddRow = function() {
    var container = document.getElementById('sc-ingredients');
    var div = document.createElement('div');
    div.className = 'scaler-ingredient-item';
    div.id = 'sc-row-' + cuRowCount;
    div.innerHTML = '<input type="number" placeholder="分量" value="1" min="0" step="any">' +
      '<select>' +
        '<option value="カップ">カップ</option>' +
        '<option value="大さじ">大さじ</option>' +
        '<option value="小さじ">小さじ</option>' +
        '<option value="合">合</option>' +
        '<option value="ml">ml</option>' +
        '<option value="g">g</option>' +
        '<option value="個">個</option>' +
        '<option value="枚">枚</option>' +
        '<option value="本">本</option>' +
      '</select>' +
      '<button class="remove-btn" onclick="cuRemoveRow(this)">&#10005;</button>';
    container.appendChild(div);
    cuRowCount++;
  };
  window.cuRemoveRow = function(btn) { btn.parentElement.remove(); };
  window.cuScaleRecipe = function() {
    var orig = parseFloat(document.getElementById('sc-original').value);
    var desired = parseFloat(document.getElementById('sc-desired').value);
    if (isNaN(orig) || isNaN(desired) || orig <= 0 || desired <= 0) return;
    var factor = desired / orig;
    var rows = document.querySelectorAll('#sc-ingredients .scaler-ingredient-item');
    var tbody = document.getElementById('sc-result-body');
    tbody.innerHTML = '';
    rows.forEach(function(row) {
      var amt = parseFloat(row.querySelector('input').value);
      var unit = row.querySelector('select').value;
      if (isNaN(amt)) return;
      var scaled = amt * factor;
      var tr = document.createElement('tr');
      tr.innerHTML = '<td>' + cuFmt(amt) + ' ' + unit + '</td><td><strong>' + cuFmt(scaled) + ' ' + unit + '</strong></td>';
      tbody.appendChild(tr);
    });
    document.getElementById('sc-factor-label').textContent =
      '倍率: x' + cuFmt(factor) + '（' + orig + '人前 → ' + desired + '人前）';
    document.getElementById('sc-result').style.display = 'block';
  };

  // 初期化
  cuConvertVolume();
  cuConvertWeight();
  cuConvertJP();
  cuConvertIngredient();
})();
</script>

</div>
