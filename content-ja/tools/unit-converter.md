---
title: "単位変換ツール - 無料オンライン単位換算"
date: 2025-04-22
description: "長さ・重さ・温度・体積・面積・速度などの単位を即座に変換。メートル法・ヤードポンド法対応の無料オンライン単位変換ツール。"
categories: ["無料ツール"]
tags: ["単位変換", "換算", "メートル", "計算", "ツール"]
slug: "unit-converter"
aliases: ["/ja/tools/unit-converter/", "/ja/tools/unit-converter/"]
cover:
  image: "/images/covers/unit-converter-ja.png"
  alt: "単位変換ツール"
ShowToc: false
---

<div id="converter-app">

<style>
#converter-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 16px;
  color: #1e293b;
  box-sizing: border-box;
}
#converter-app * { box-sizing: border-box; }

/* タブ */
.cv-tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 20px;
}
.cv-tab {
  padding: 7px 14px;
  border: 2px solid #0891b2;
  border-radius: 20px;
  background: #fff;
  color: #0891b2;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.18s;
}
.cv-tab:hover { background: #e0f7fa; }
.cv-tab.active { background: #0891b2; color: #fff; }

/* メインカード */
.cv-card {
  background: #f0f9ff;
  border: 1px solid #bae6fd;
  border-radius: 14px;
  padding: 24px;
  margin-bottom: 20px;
}

/* 入力エリア */
.cv-row {
  display: flex;
  align-items: flex-end;
  gap: 10px;
  margin-bottom: 14px;
}
.cv-field {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.cv-field label {
  font-size: 12px;
  font-weight: 700;
  color: #0e7490;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.cv-field input[type="number"] {
  width: 100%;
  padding: 11px 14px;
  border: 2px solid #7dd3fc;
  border-radius: 8px;
  font-size: 20px;
  font-weight: 700;
  color: #0c4a6e;
  background: #fff;
  outline: none;
  transition: border-color 0.2s;
}
.cv-field input[type="number"]:focus { border-color: #0891b2; }
.cv-field select {
  width: 100%;
  padding: 9px 12px;
  border: 2px solid #7dd3fc;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  color: #0c4a6e;
  background: #fff;
  outline: none;
  cursor: pointer;
  transition: border-color 0.2s;
}
.cv-field select:focus { border-color: #0891b2; }

/* スワップボタン */
.cv-swap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  flex-shrink: 0;
}
.cv-swap button {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: 2px solid #0891b2;
  background: #fff;
  color: #0891b2;
  font-size: 20px;
  cursor: pointer;
  transition: all 0.18s;
  display: flex;
  align-items: center;
  justify-content: center;
}
.cv-swap button:hover { background: #0891b2; color: #fff; }

/* 結果 */
.cv-result-box {
  background: #fff;
  border: 2px solid #0891b2;
  border-radius: 10px;
  padding: 14px 18px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  flex-wrap: wrap;
}
.cv-result-value {
  font-size: 26px;
  font-weight: 800;
  color: #0891b2;
}
.cv-result-label {
  font-size: 13px;
  color: #64748b;
}
.cv-formula {
  font-size: 12px;
  color: #94a3b8;
  background: #f8fafc;
  border-radius: 6px;
  padding: 6px 10px;
  margin-top: 8px;
  font-family: monospace;
}

/* 早見表 */
.cv-quick-title {
  font-size: 14px;
  font-weight: 700;
  color: #0e7490;
  margin-bottom: 10px;
  margin-top: 4px;
}
.cv-quick-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 8px;
}
.cv-quick-item {
  background: #fff;
  border: 1px solid #bae6fd;
  border-radius: 8px;
  padding: 8px 12px;
  font-size: 12px;
  color: #334155;
  line-height: 1.5;
  cursor: pointer;
  transition: background 0.15s;
}
.cv-quick-item:hover { background: #e0f7fa; }
.cv-quick-item strong { color: #0891b2; display: block; }

/* 温度特別 */
.cv-temp-note {
  font-size: 12px;
  color: #64748b;
  margin-top: 6px;
  padding: 6px 10px;
  background: #fef9c3;
  border-radius: 6px;
}

@media (max-width: 520px) {
  .cv-row { flex-direction: column; }
  .cv-swap { flex-direction: row; justify-content: center; margin: 4px 0; }
  .cv-swap button { width: 40px; height: 40px; font-size: 18px; }
  .cv-result-value { font-size: 22px; }
  .cv-tab { font-size: 12px; padding: 6px 11px; }
}
</style>

<!-- タブ -->
<div class="cv-tabs" id="cvTabs">
  <button class="cv-tab active" data-cat="length">長さ</button>
  <button class="cv-tab" data-cat="weight">重さ</button>
  <button class="cv-tab" data-cat="temperature">温度</button>
  <button class="cv-tab" data-cat="volume">体積</button>
  <button class="cv-tab" data-cat="area">面積</button>
  <button class="cv-tab" data-cat="speed">速度</button>
  <button class="cv-tab" data-cat="time">時間</button>
  <button class="cv-tab" data-cat="data">データ</button>
</div>

<!-- 変換カード -->
<div class="cv-card">
  <div class="cv-row">
    <div class="cv-field">
      <label>変換元</label>
      <input type="number" id="cvInput" value="1" step="any" />
      <select id="cvFromUnit"></select>
    </div>
    <div class="cv-swap">
      <button id="cvSwapBtn" title="入れ替え">&#8646;</button>
    </div>
    <div class="cv-field">
      <label>変換先</label>
      <input type="number" id="cvOutput" step="any" readonly style="background:#f0f9ff;color:#0891b2;" />
      <select id="cvToUnit"></select>
    </div>
  </div>
  <div class="cv-result-box">
    <div>
      <div class="cv-result-label">変換結果</div>
      <div class="cv-result-value" id="cvResultText">---</div>
    </div>
    <div id="cvFormulaBox" class="cv-formula" style="text-align:right;"></div>
  </div>
  <div id="cvTempNote" class="cv-temp-note" style="display:none;">
    ※ 温度の変換は線形ではないため、オフセットを考慮した計算を行います。
  </div>
</div>

<!-- 早見表 -->
<div class="cv-card" style="background:#fff;">
  <div class="cv-quick-title" id="cvQuickTitle">よく使う換算早見表</div>
  <div class="cv-quick-grid" id="cvQuickGrid"></div>
</div>

<script>
(function() {
  // ===== 単位定義 =====
  // 各カテゴリの基準単位へのファクター (温度は別処理)
  const UNITS = {
    length: {
      label: '長さ',
      base: 'm',
      units: [
        { key: 'mm',   label: 'ミリメートル (mm)',  factor: 0.001 },
        { key: 'cm',   label: 'センチメートル (cm)', factor: 0.01 },
        { key: 'm',    label: 'メートル (m)',         factor: 1 },
        { key: 'km',   label: 'キロメートル (km)',    factor: 1000 },
        { key: 'sun',  label: '寸',                   factor: 0.030303 },
        { key: 'shaku',label: '尺',                   factor: 0.303030 },
        { key: 'ken',  label: '間',                   factor: 1.818182 },
        { key: 'ri',   label: '里',                   factor: 3927.272 },
        { key: 'inch', label: 'インチ (in)',           factor: 0.0254 },
        { key: 'ft',   label: 'フィート (ft)',         factor: 0.3048 },
        { key: 'yd',   label: 'ヤード (yd)',           factor: 0.9144 },
        { key: 'mi',   label: 'マイル (mi)',           factor: 1609.344 },
        { key: 'nmi',  label: '海里 (nmi)',            factor: 1852 },
      ],
      quick: [
        { from: 1, fu: 'm',    to: 'ft',   label: '1メートル = 約3.281フィート' },
        { from: 1, fu: 'km',   to: 'mi',   label: '1キロ = 約0.621マイル' },
        { from: 1, fu: 'inch', to: 'cm',   label: '1インチ = 2.54センチ' },
        { from: 1, fu: 'shaku',to: 'cm',   label: '1尺 = 約30.3センチ' },
        { from: 1, fu: 'ken',  to: 'm',    label: '1間 = 約1.818メートル' },
        { from: 1, fu: 'ri',   to: 'km',   label: '1里 = 約3.927キロ' },
        { from: 1, fu: 'mi',   to: 'km',   label: '1マイル = 約1.609キロ' },
        { from: 1, fu: 'ft',   to: 'cm',   label: '1フィート = 30.48センチ' },
      ]
    },
    weight: {
      label: '重さ',
      base: 'kg',
      units: [
        { key: 'mg',  label: 'ミリグラム (mg)',  factor: 0.000001 },
        { key: 'g',   label: 'グラム (g)',         factor: 0.001 },
        { key: 'kg',  label: 'キログラム (kg)',    factor: 1 },
        { key: 't',   label: 'トン (t)',           factor: 1000 },
        { key: 'mom', label: '匁 (もんめ)',        factor: 0.00375 },
        { key: 'kan', label: '貫 (かん)',          factor: 3.75 },
        { key: 'oz',  label: 'オンス (oz)',        factor: 0.0283495 },
        { key: 'lb',  label: 'ポンド (lb)',        factor: 0.453592 },
        { key: 'st',  label: 'ストーン (st)',      factor: 6.35029 },
      ],
      quick: [
        { from: 1, fu: 'kg',  to: 'lb',  label: '1キログラム = 約2.205ポンド' },
        { from: 1, fu: 'lb',  to: 'kg',  label: '1ポンド = 約0.454キログラム' },
        { from: 1, fu: 'oz',  to: 'g',   label: '1オンス = 約28.35グラム' },
        { from: 1, fu: 'kan', to: 'kg',  label: '1貫 = 3.75キログラム' },
        { from: 1, fu: 'mom', to: 'g',   label: '1匁 = 3.75グラム' },
        { from: 60, fu: 'kg', to: 'lb',  label: '60kg = 約132.3ポンド' },
      ]
    },
    temperature: {
      label: '温度',
      base: 'C',
      isTemp: true,
      units: [
        { key: 'C', label: '摂氏 (°C)' },
        { key: 'F', label: '華氏 (°F)' },
        { key: 'K', label: 'ケルビン (K)' },
      ],
      quick: [
        { from: 0,   fu: 'C', to: 'F', label: '0°C = 32°F (氷点)' },
        { from: 100, fu: 'C', to: 'F', label: '100°C = 212°F (沸点)' },
        { from: 37,  fu: 'C', to: 'F', label: '37°C = 98.6°F (体温)' },
        { from: 20,  fu: 'C', to: 'F', label: '20°C = 68°F (室温)' },
        { from: -40, fu: 'C', to: 'F', label: '-40°C = -40°F (同じ値)' },
        { from: 0,   fu: 'C', to: 'K', label: '0°C = 273.15K' },
      ]
    },
    volume: {
      label: '体積',
      base: 'L',
      units: [
        { key: 'mL',  label: 'ミリリットル (mL)',   factor: 0.001 },
        { key: 'cL',  label: 'センチリットル (cL)', factor: 0.01 },
        { key: 'dL',  label: 'デシリットル (dL)',   factor: 0.1 },
        { key: 'L',   label: 'リットル (L)',         factor: 1 },
        { key: 'kL',  label: 'キロリットル (kL)',   factor: 1000 },
        { key: 'm3',  label: '立方メートル (m³)',   factor: 1000 },
        { key: 'cm3', label: '立方センチ (cm³)',    factor: 0.001 },
        { key: 'tsp', label: 'ティースプーン (tsp)',factor: 0.004929 },
        { key: 'tbsp',label: 'テーブルスプーン',    factor: 0.014787 },
        { key: 'floz',label: '液量オンス (fl oz)',  factor: 0.029574 },
        { key: 'cup', label: 'カップ (米)',          factor: 0.236588 },
        { key: 'pt',  label: 'パイント (pt)',        factor: 0.473176 },
        { key: 'qt',  label: 'クォート (qt)',        factor: 0.946353 },
        { key: 'gal', label: 'ガロン (gal)',         factor: 3.785411 },
      ],
      quick: [
        { from: 1, fu: 'L',   to: 'gal',  label: '1リットル = 約0.264ガロン' },
        { from: 1, fu: 'gal', to: 'L',    label: '1ガロン = 約3.785リットル' },
        { from: 1, fu: 'cup', to: 'mL',   label: '1カップ = 約237mL' },
        { from: 1, fu: 'floz',to: 'mL',   label: '1液量オンス = 約29.6mL' },
        { from: 1, fu: 'pt',  to: 'mL',   label: '1パイント = 約473mL' },
      ]
    },
    area: {
      label: '面積',
      base: 'm2',
      units: [
        { key: 'mm2',  label: '平方ミリ (mm²)',     factor: 0.000001 },
        { key: 'cm2',  label: '平方センチ (cm²)',   factor: 0.0001 },
        { key: 'm2',   label: '平方メートル (m²)',  factor: 1 },
        { key: 'km2',  label: '平方キロ (km²)',     factor: 1000000 },
        { key: 'tsubo',label: '坪',                  factor: 3.305785 },
        { key: 'jo',   label: '畳',                  factor: 1.6528 },
        { key: 'tan',  label: '反',                  factor: 991.7355 },
        { key: 'cho',  label: '町',                  factor: 9917.355 },
        { key: 'acre', label: 'エーカー (acre)',     factor: 4046.856 },
        { key: 'ha',   label: 'ヘクタール (ha)',     factor: 10000 },
        { key: 'sqft', label: '平方フィート (ft²)', factor: 0.092903 },
        { key: 'sqyd', label: '平方ヤード (yd²)',   factor: 0.836127 },
        { key: 'sqmi', label: '平方マイル (mi²)',   factor: 2589988.1 },
      ],
      quick: [
        { from: 1,   fu: 'tsubo', to: 'm2',   label: '1坪 = 約3.306平方メートル' },
        { from: 1,   fu: 'jo',    to: 'm2',   label: '1畳 = 約1.653平方メートル' },
        { from: 1,   fu: 'tan',   to: 'm2',   label: '1反 = 約991.7平方メートル' },
        { from: 1,   fu: 'cho',   to: 'm2',   label: '1町 = 約9917平方メートル' },
        { from: 1,   fu: 'ha',    to: 'tsubo',label: '1ヘクタール = 約3025坪' },
        { from: 1,   fu: 'acre',  to: 'm2',   label: '1エーカー = 約4047平方メートル' },
        { from: 100, fu: 'm2',    to: 'tsubo',label: '100m² = 約30.25坪' },
        { from: 1,   fu: 'sqft',  to: 'm2',   label: '1平方フィート = 約0.093m²' },
      ]
    },
    speed: {
      label: '速度',
      base: 'mps',
      units: [
        { key: 'mps',  label: 'メートル毎秒 (m/s)',     factor: 1 },
        { key: 'kmph', label: 'キロメートル毎時 (km/h)', factor: 0.277778 },
        { key: 'mph',  label: 'マイル毎時 (mph)',         factor: 0.44704 },
        { key: 'knot', label: 'ノット (knot)',             factor: 0.514444 },
        { key: 'mach', label: 'マッハ (Mach)',             factor: 340.29 },
        { key: 'fps',  label: 'フィート毎秒 (ft/s)',      factor: 0.3048 },
      ],
      quick: [
        { from: 100, fu: 'kmph', to: 'mph',  label: '100km/h = 約62.1mph' },
        { from: 1,   fu: 'mach', to: 'kmph', label: '音速 = 約1225km/h' },
        { from: 1,   fu: 'knot', to: 'kmph', label: '1ノット = 約1.852km/h' },
        { from: 60,  fu: 'kmph', to: 'mps',  label: '60km/h = 約16.7m/s' },
      ]
    },
    time: {
      label: '時間',
      base: 's',
      units: [
        { key: 'ns',  label: 'ナノ秒 (ns)',    factor: 0.000000001 },
        { key: 'us',  label: 'マイクロ秒 (μs)',factor: 0.000001 },
        { key: 'ms',  label: 'ミリ秒 (ms)',    factor: 0.001 },
        { key: 's',   label: '秒 (s)',          factor: 1 },
        { key: 'min', label: '分 (min)',        factor: 60 },
        { key: 'hr',  label: '時間 (hr)',       factor: 3600 },
        { key: 'day', label: '日',              factor: 86400 },
        { key: 'wk',  label: '週',             factor: 604800 },
        { key: 'mo',  label: 'ヶ月 (30日)',    factor: 2592000 },
        { key: 'yr',  label: '年 (365日)',      factor: 31536000 },
      ],
      quick: [
        { from: 1,  fu: 'hr',  to: 'min', label: '1時間 = 60分' },
        { from: 1,  fu: 'day', to: 'hr',  label: '1日 = 24時間' },
        { from: 1,  fu: 'wk',  to: 'day', label: '1週間 = 7日' },
        { from: 1,  fu: 'yr',  to: 'day', label: '1年 = 365日' },
        { from: 1,  fu: 'mo',  to: 'day', label: '1ヶ月 = 30日' },
        { from: 90, fu: 'min', to: 'hr',  label: '90分 = 1.5時間' },
      ]
    },
    data: {
      label: 'データ',
      base: 'B',
      units: [
        { key: 'bit', label: 'ビット (bit)',         factor: 0.125 },
        { key: 'B',   label: 'バイト (B)',            factor: 1 },
        { key: 'KB',  label: 'キロバイト (KB)',       factor: 1024 },
        { key: 'MB',  label: 'メガバイト (MB)',       factor: 1048576 },
        { key: 'GB',  label: 'ギガバイト (GB)',       factor: 1073741824 },
        { key: 'TB',  label: 'テラバイト (TB)',       factor: 1099511627776 },
        { key: 'PB',  label: 'ペタバイト (PB)',       factor: 1.12589990684e15 },
        { key: 'Kbit',label: 'キロビット (Kbit)',     factor: 125 },
        { key: 'Mbit',label: 'メガビット (Mbit)',     factor: 125000 },
        { key: 'Gbit',label: 'ギガビット (Gbit)',     factor: 125000000 },
      ],
      quick: [
        { from: 1,    fu: 'GB', to: 'MB',  label: '1GB = 1024MB' },
        { from: 1,    fu: 'TB', to: 'GB',  label: '1TB = 1024GB' },
        { from: 1,    fu: 'MB', to: 'KB',  label: '1MB = 1024KB' },
        { from: 100,  fu: 'MB', to: 'GB',  label: '100MB = 約0.098GB' },
        { from: 1,    fu: 'Gbit',to: 'MB', label: '1Gbps = 125MB/s' },
      ]
    }
  };

  // 温度変換
  function convertTemp(val, from, to) {
    let celsius;
    if (from === 'C') celsius = val;
    else if (from === 'F') celsius = (val - 32) * 5/9;
    else if (from === 'K') celsius = val - 273.15;
    if (to === 'C') return celsius;
    if (to === 'F') return celsius * 9/5 + 32;
    if (to === 'K') return celsius + 273.15;
  }

  function tempFormula(from, to) {
    const f = {
      C_F: '°F = °C × 9/5 + 32',
      F_C: '°C = (°F - 32) × 5/9',
      C_K: 'K = °C + 273.15',
      K_C: '°C = K - 273.15',
      F_K: 'K = (°F - 32) × 5/9 + 273.15',
      K_F: '°F = (K - 273.15) × 9/5 + 32',
    };
    return f[from+'_'+to] || '';
  }

  // 汎用変換
  function convertValue(val, from, to, cat) {
    if (cat.isTemp) return convertTemp(val, from, to);
    const fu = cat.units.find(u => u.key === from);
    const tu = cat.units.find(u => u.key === to);
    if (!fu || !tu) return 0;
    return val * fu.factor / tu.factor;
  }

  function formatNum(n) {
    if (n === null || isNaN(n)) return '---';
    if (Math.abs(n) < 0.0001 && n !== 0) return n.toExponential(4);
    if (Math.abs(n) >= 1e10) return n.toExponential(4);
    // 有効桁数に応じて
    const s = parseFloat(n.toPrecision(7)).toString();
    return s;
  }

  function getFormula(val, from, to, cat) {
    if (cat.isTemp) return tempFormula(from, to);
    const fu = cat.units.find(u => u.key === from);
    const tu = cat.units.find(u => u.key === to);
    if (!fu || !tu || from === to) return '';
    const ratio = fu.factor / tu.factor;
    const ratioStr = parseFloat(ratio.toPrecision(6));
    return `1 ${from} = ${ratioStr} ${to}`;
  }

  // ===== UI =====
  let currentCat = 'length';

  const tabs     = document.querySelectorAll('.cv-tab');
  const inputEl  = document.getElementById('cvInput');
  const outputEl = document.getElementById('cvOutput');
  const fromSel  = document.getElementById('cvFromUnit');
  const toSel    = document.getElementById('cvToUnit');
  const resultEl = document.getElementById('cvResultText');
  const formulaEl= document.getElementById('cvFormulaBox');
  const quickGrid= document.getElementById('cvQuickGrid');
  const quickTitle=document.getElementById('cvQuickTitle');
  const swapBtn  = document.getElementById('cvSwapBtn');
  const tempNote = document.getElementById('cvTempNote');

  function buildSelects(cat) {
    const units = UNITS[cat].units;
    [fromSel, toSel].forEach((sel, idx) => {
      sel.innerHTML = '';
      units.forEach(u => {
        const opt = document.createElement('option');
        opt.value = u.key;
        opt.textContent = u.label;
        sel.appendChild(opt);
      });
      // デフォルト: from=0, to=1
      sel.selectedIndex = idx === 0 ? 0 : Math.min(1, units.length - 1);
    });
  }

  function buildQuick(cat) {
    const catDef = UNITS[cat];
    quickTitle.textContent = `${catDef.label}のよく使う換算早見表`;
    quickGrid.innerHTML = '';
    catDef.quick.forEach(q => {
      const item = document.createElement('div');
      item.className = 'cv-quick-item';
      const result = convertValue(q.from, q.fu, q.to, catDef);
      item.innerHTML = `<strong>${q.label}</strong><span style="color:#64748b;font-size:11px;">クリックで使用</span>`;
      item.addEventListener('click', () => {
        inputEl.value = q.from;
        fromSel.value = q.fu;
        toSel.value = q.to;
        doConvert();
      });
      quickGrid.appendChild(item);
    });
  }

  function doConvert() {
    const val = parseFloat(inputEl.value);
    const from = fromSel.value;
    const to   = toSel.value;
    const catDef = UNITS[currentCat];
    if (isNaN(val)) {
      outputEl.value = '';
      resultEl.textContent = '---';
      formulaEl.textContent = '';
      return;
    }
    const result = convertValue(val, from, to, catDef);
    const fromLabel = catDef.units.find(u => u.key === from)?.label || from;
    const toLabel   = catDef.units.find(u => u.key === to)?.label || to;
    outputEl.value = formatNum(result);
    resultEl.textContent = `${formatNum(val)} ${from} = ${formatNum(result)} ${to}`;
    formulaEl.textContent = getFormula(val, from, to, catDef);
    tempNote.style.display = catDef.isTemp ? 'block' : 'none';
  }

  function switchCat(cat) {
    currentCat = cat;
    tabs.forEach(t => t.classList.toggle('active', t.dataset.cat === cat));
    buildSelects(cat);
    buildQuick(cat);
    doConvert();
  }

  tabs.forEach(t => {
    t.addEventListener('click', () => switchCat(t.dataset.cat));
  });

  inputEl.addEventListener('input', doConvert);
  fromSel.addEventListener('change', doConvert);
  toSel.addEventListener('change', doConvert);

  swapBtn.addEventListener('click', () => {
    const tmp = fromSel.value;
    fromSel.value = toSel.value;
    toSel.value = tmp;
    const tmpVal = inputEl.value;
    inputEl.value = outputEl.value;
    doConvert();
  });

  // 初期化
  switchCat('length');
})();
</script>

</div>

---

## 単位変換ツールの使い方

### 簡単3ステップ

1. **カテゴリを選ぶ** — 長さ・重さ・温度・体積・面積・速度・時間・データから選択します。
2. **数値と単位を入力** — 変換元の数値を入力し、変換元・変換先の単位をドロップダウンから選びます。
3. **結果を確認** — リアルタイムで変換結果が表示されます。スワップボタン（⇆）で入出力を入れ替えられます。

### 機能のポイント

- **双方向変換** — スワップボタンで変換元と変換先を即座に入れ替えられます。
- **変換式の表示** — 計算の根拠となる変換式を確認できます。
- **早見表** — よく使う換算をワンクリックで即座に入力できます。
- **日本の伝統単位対応** — 尺・寸・間・里・匁・貫・坪・畳・反・町などの日本独自の単位に対応しています。

---

## よく使う単位換算

### 長さの換算

| 単位 | メートル換算 | 用途 |
|------|------------|------|
| 1インチ | 2.54 cm | 画面サイズ、身長(英米) |
| 1フィート | 30.48 cm | 身長、建築(英米) |
| 1マイル | 1.609 km | 道路距離(英米) |
| 1尺 | 約30.3 cm | 日本の伝統建築 |
| 1間 | 約1.818 m | 部屋の広さ |
| 1里 | 約3.927 km | 昔の道のり |

### 重さの換算

| 単位 | キログラム換算 | 用途 |
|------|-------------|------|
| 1ポンド (lb) | 約0.454 kg | 食品表示(英米) |
| 1オンス (oz) | 約28.35 g | 食品・金属 |
| 1貫 | 3.75 kg | 日本の伝統単位 |
| 1匁 | 3.75 g | 宝石・貴金属 |

### 面積の換算

| 単位 | 平方メートル換算 | 用途 |
|------|--------------|------|
| 1坪 | 約3.306 m² | 不動産 |
| 1畳 | 約1.653 m² | 部屋の広さ |
| 1反 | 約991.7 m² | 農地 |
| 1エーカー | 約4047 m² | 英米の農地・土地 |
| 1ヘクタール | 10,000 m² | 農地・公園 |

### 温度の換算

| 摂氏 (°C) | 華氏 (°F) | 場面 |
|-----------|----------|------|
| 0°C | 32°F | 氷点 |
| 20°C | 68°F | 室温 |
| 37°C | 98.6°F | 体温 |
| 100°C | 212°F | 沸点 |

---

## 関連ツール

> 割合・割引・変化率をすぐ計算 → [パーセント計算ツール](/ja/tools/percent-calculator/)

> BMIと適正体重をチェック → [BMI計算ツール](/ja/tools/bmi-calculator/)

> 時給と年収を相互変換 → [時給換算ツール](/ja/tools/jikyuu-kansan-calculator/)

---

**不動産の面積計算・海外取引の単位換算に**

不動産投資や海外ビジネスで必要な単位換算。経費管理もクラウド会計ソフト「freee」で効率化しませんか？

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">
freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">
