---
title: "バッテリー持続時間計算ツール - デバイスの稼働時間を推定"
description: "デバイスのバッテリー持続時間を容量・使用パターン・消費電力から計算。無料オンラインバッテリー寿命計算ツール。"
date: 2026-01-09
categories: ["無料ツール"]
slug: "battery-life-calculator"
ShowToc: false
cover:
  image: "/images/covers/battery-life-calculator.png"
---

<div id="bl-app">
<style>
#bl-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic", "Meiryo", sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
  line-height: 1.7;
}
#bl-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 1.6rem 0 0.8rem;
  color: #16213e;
}
#bl-app h3 {
  font-size: 1.05rem;
  font-weight: 600;
  margin: 1.2rem 0 0.5rem;
  color: #0f3460;
}
#bl-app .card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.4rem 1.6rem;
  margin-bottom: 1.2rem;
}
#bl-app .card-blue {
  background: #eff6ff;
  border-color: #bfdbfe;
}
#bl-app .card-green {
  background: #f0fdf4;
  border-color: #bbf7d0;
}
#bl-app .card-amber {
  background: #fffbeb;
  border-color: #fde68a;
}
#bl-app .tabs {
  display: flex;
  gap: 0;
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid #cbd5e1;
  margin-bottom: 1.2rem;
}
#bl-app .tab-btn {
  flex: 1;
  padding: 0.6rem 0.8rem;
  background: #f1f5f9;
  border: none;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 500;
  color: #475569;
  transition: background 0.15s, color 0.15s;
}
#bl-app .tab-btn.active {
  background: #2563eb;
  color: #fff;
}
#bl-app .tab-btn:hover:not(.active) {
  background: #e2e8f0;
}
#bl-app .field-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 0.8rem;
}
#bl-app .field-row.three {
  grid-template-columns: 1fr 1fr 1fr;
}
@media (max-width: 540px) {
  #bl-app .field-row,
  #bl-app .field-row.three {
    grid-template-columns: 1fr;
  }
}
#bl-app label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #374151;
  margin-bottom: 0.3rem;
}
#bl-app input[type="number"],
#bl-app select {
  width: 100%;
  padding: 0.5rem 0.7rem;
  border: 1px solid #cbd5e1;
  border-radius: 7px;
  font-size: 1rem;
  background: #fff;
  color: #1a1a2e;
  box-sizing: border-box;
  transition: border-color 0.15s;
}
#bl-app input[type="number"]:focus,
#bl-app select:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37,99,235,0.12);
}
#bl-app .slider-row {
  margin-bottom: 0.8rem;
}
#bl-app input[type="range"] {
  width: 100%;
  accent-color: #2563eb;
  margin-top: 0.3rem;
}
#bl-app .slider-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.78rem;
  color: #64748b;
  margin-top: 0.1rem;
}
#bl-app .presets {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
#bl-app .preset-btn {
  padding: 0.35rem 0.85rem;
  border: 1px solid #93c5fd;
  border-radius: 20px;
  background: #eff6ff;
  color: #1d4ed8;
  font-size: 0.82rem;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.15s;
}
#bl-app .preset-btn:hover {
  background: #dbeafe;
}
#bl-app .calc-btn {
  display: inline-block;
  padding: 0.65rem 2rem;
  background: #2563eb;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
  margin-top: 0.4rem;
}
#bl-app .calc-btn:hover {
  background: #1d4ed8;
}
#bl-app .result-box {
  background: #fff;
  border: 2px solid #2563eb;
  border-radius: 12px;
  padding: 1.2rem 1.4rem;
  margin-top: 1rem;
  display: none;
}
#bl-app .result-box.visible {
  display: block;
}
#bl-app .result-main {
  font-size: 2rem;
  font-weight: 800;
  color: #2563eb;
  margin-bottom: 0.3rem;
}
#bl-app .result-sub {
  color: #475569;
  font-size: 0.95rem;
}
#bl-app .result-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.8rem;
  margin-top: 0.8rem;
}
#bl-app .result-item {
  background: #f1f5f9;
  border-radius: 8px;
  padding: 0.7rem 1rem;
}
#bl-app .result-item .lbl {
  font-size: 0.78rem;
  color: #64748b;
  font-weight: 600;
}
#bl-app .result-item .val {
  font-size: 1.1rem;
  font-weight: 700;
  color: #1e293b;
  margin-top: 0.1rem;
}
#bl-app .tips-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
#bl-app .tips-list li {
  padding: 0.45rem 0 0.45rem 1.6rem;
  position: relative;
  font-size: 0.95rem;
  border-bottom: 1px solid #e2e8f0;
}
#bl-app .tips-list li:last-child {
  border-bottom: none;
}
#bl-app .tips-list li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: #16a34a;
  font-weight: 700;
}
#bl-app .cta-box {
  background: #fef3c7;
  border: 1px solid #fbbf24;
  border-radius: 10px;
  padding: 1rem 1.4rem;
  margin-top: 1.6rem;
  font-size: 0.95rem;
}
#bl-app .cta-box a {
  color: #b45309;
  font-weight: 600;
}
#bl-app .section-divider {
  border: none;
  border-top: 2px solid #e2e8f0;
  margin: 1.6rem 0;
}
#bl-app .power-toggle {
  display: flex;
  gap: 0.8rem;
  margin-bottom: 0.8rem;
}
#bl-app .power-toggle label {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
}
#bl-app .badge {
  display: inline-block;
  background: #dcfce7;
  color: #15803d;
  font-size: 0.75rem;
  font-weight: 700;
  padding: 0.15rem 0.5rem;
  border-radius: 10px;
  vertical-align: middle;
  margin-left: 0.3rem;
}
</style>

<h2>バッテリー持続時間計算ツール</h2>
<p>スマートフォン・ノートPC・タブレット・IoTセンサー・ドローンなど、あらゆるデバイスのバッテリー稼働時間を即座に試算できます。必要な電池容量の逆算や充電時間の見積もりにも対応しています。</p>

<div class="tabs">
  <button class="tab-btn active" onclick="blSwitchTab('runtime')">稼働時間を計算</button>
  <button class="tab-btn" onclick="blSwitchTab('reverse')">必要容量を逆算</button>
  <button class="tab-btn" onclick="blSwitchTab('charging')">充電時間を計算</button>
</div>

<!-- ===== TAB: 稼働時間 ===== -->
<div id="bl-tab-runtime">
  <div class="card card-blue">
    <h3>デバイスプリセット</h3>
    <div class="presets">
      <button class="preset-btn" onclick="blApplyPreset('smartphone')">スマートフォン</button>
      <button class="preset-btn" onclick="blApplyPreset('tablet')">タブレット</button>
      <button class="preset-btn" onclick="blApplyPreset('laptop')">ノートPC</button>
      <button class="preset-btn" onclick="blApplyPreset('iot')">IoTセンサー</button>
      <button class="preset-btn" onclick="blApplyPreset('drone')">ドローン</button>
      <button class="preset-btn" onclick="blApplyPreset('earbuds')">ワイヤレスイヤホン</button>
      <button class="preset-btn" onclick="blApplyPreset('smartwatch')">スマートウォッチ</button>
      <button class="preset-btn" onclick="blApplyPreset('ebike')">電動アシスト自転車</button>
    </div>

    <h3>バッテリー容量</h3>
    <div class="field-row">
      <div>
        <label>容量（mAh）</label>
        <input type="number" id="bl-mah" value="4000" min="1" step="100">
      </div>
      <div>
        <label>バッテリー電圧（V）</label>
        <input type="number" id="bl-voltage" value="3.7" min="0.1" step="0.1">
      </div>
    </div>

    <h3>消費電力</h3>
    <div class="power-toggle">
      <label><input type="radio" name="bl-power-mode" value="ma" checked onchange="blTogglePowerMode()"> 電流（mA）で入力</label>
      <label><input type="radio" name="bl-power-mode" value="w" onchange="blTogglePowerMode()"> ワット数（W）で入力</label>
    </div>
    <div class="field-row">
      <div id="bl-ma-field">
        <label>消費電流（mA）</label>
        <input type="number" id="bl-ma" value="150" min="0.1" step="10">
      </div>
      <div id="bl-w-field" style="display:none;">
        <label>消費電力（W）</label>
        <input type="number" id="bl-w" value="0.555" min="0.001" step="0.1">
      </div>
      <div></div>
    </div>

    <div class="slider-row">
      <label>効率係数: <strong id="bl-eff-label">85%</strong> <span class="badge">実使用ロスを考慮</span></label>
      <input type="range" id="bl-efficiency" min="70" max="95" value="85" step="1" oninput="document.getElementById('bl-eff-label').textContent=this.value+'%'">
      <div class="slider-labels"><span>70%（劣化）</span><span>80%</span><span>90%</span><span>95%（理想）</span></div>
    </div>

    <button class="calc-btn" onclick="blCalculateRuntime()">稼働時間を計算する</button>
  </div>

  <div class="result-box" id="bl-result-runtime">
    <div class="result-main" id="bl-runtime-main">--</div>
    <div class="result-sub" id="bl-runtime-sub"></div>
    <div class="result-grid">
      <div class="result-item">
        <div class="lbl">バッテリーエネルギー</div>
        <div class="val" id="bl-res-wh">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">実効消費電力</div>
        <div class="val" id="bl-res-draw">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">適用効率</div>
        <div class="val" id="bl-res-eff">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">稼働時間（小数）</div>
        <div class="val" id="bl-res-dec">--</div>
      </div>
    </div>
  </div>
</div>

<!-- ===== TAB: 必要容量 ===== -->
<div id="bl-tab-reverse" style="display:none;">
  <div class="card card-green">
    <h3>目標稼働時間の設定</h3>
    <div class="field-row three">
      <div>
        <label>目標時間（時間）</label>
        <input type="number" id="bl-target-h" value="8" min="0" step="1">
      </div>
      <div>
        <label>目標時間（分）</label>
        <input type="number" id="bl-target-m" value="0" min="0" max="59" step="5">
      </div>
      <div>
        <label>電圧（V）</label>
        <input type="number" id="bl-rev-voltage" value="3.7" min="0.1" step="0.1">
      </div>
    </div>
    <div class="field-row">
      <div>
        <label>消費電流（mA）</label>
        <input type="number" id="bl-rev-ma" value="150" min="0.1" step="10">
      </div>
      <div>
        <label>効率係数（%）</label>
        <input type="number" id="bl-rev-eff" value="85" min="70" max="95" step="1">
      </div>
    </div>
    <button class="calc-btn" onclick="blCalculateReverse()">必要容量を計算する</button>
  </div>

  <div class="result-box" id="bl-result-reverse">
    <div class="result-main" id="bl-rev-main">--</div>
    <div class="result-sub" id="bl-rev-sub"></div>
    <div class="result-grid">
      <div class="result-item">
        <div class="lbl">最低限必要な容量</div>
        <div class="val" id="bl-rev-min">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">推奨容量（+20%バッファ）</div>
        <div class="val" id="bl-rev-rec">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">必要エネルギー（Wh）</div>
        <div class="val" id="bl-rev-wh">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">適用効率</div>
        <div class="val" id="bl-rev-eff-res">--</div>
      </div>
    </div>
  </div>
</div>

<!-- ===== TAB: 充電時間 ===== -->
<div id="bl-tab-charging" style="display:none;">
  <div class="card card-amber">
    <h3>充電時間シミュレーター</h3>
    <div class="field-row">
      <div>
        <label>バッテリー容量（mAh）</label>
        <input type="number" id="bl-ch-mah" value="4000" min="1" step="100">
      </div>
      <div>
        <label>充電器出力（W）</label>
        <input type="number" id="bl-ch-w" value="20" min="0.5" step="1">
      </div>
    </div>
    <div class="field-row">
      <div>
        <label>バッテリー電圧（V）</label>
        <input type="number" id="bl-ch-voltage" value="3.7" min="0.1" step="0.1">
      </div>
      <div>
        <label>現在の残量（%）</label>
        <input type="number" id="bl-ch-current" value="20" min="0" max="99" step="5">
      </div>
    </div>
    <div class="slider-row">
      <label>充電効率: <strong id="bl-ch-eff-label">90%</strong></label>
      <input type="range" id="bl-ch-efficiency" min="75" max="98" value="90" step="1" oninput="document.getElementById('bl-ch-eff-label').textContent=this.value+'%'">
      <div class="slider-labels"><span>75%</span><span>85%</span><span>95%</span><span>98%</span></div>
    </div>
    <button class="calc-btn" onclick="blCalculateCharging()">充電時間を計算する</button>
  </div>

  <div class="result-box" id="bl-result-charging">
    <div class="result-main" id="bl-ch-main">--</div>
    <div class="result-sub" id="bl-ch-sub"></div>
    <div class="result-grid">
      <div class="result-item">
        <div class="lbl">80%まで（急速充電目安）</div>
        <div class="val" id="bl-ch-80">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">100%まで（満充電）</div>
        <div class="val" id="bl-ch-100">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">充電レート（mA）</div>
        <div class="val" id="bl-ch-rate">--</div>
      </div>
      <div class="result-item">
        <div class="lbl">投入エネルギー（Wh）</div>
        <div class="val" id="bl-ch-wh">--</div>
      </div>
    </div>
  </div>
</div>

<hr class="section-divider">

<h2>バッテリーを長持ちさせるコツ</h2>
<div class="card">
  <ul class="tips-list">
    <li><strong>完全放電を避ける。</strong>リチウムイオン電池は残量20〜80%の範囲で使うと寿命が延びます。0%まで使い切ることを繰り返すと劣化が加速します。</li>
    <li><strong>画面輝度を下げる。</strong>ディスプレイはモバイル機器で最大の電力消費源です。輝度を30%下げるだけで稼働時間が15〜20%改善する場合があります。</li>
    <li><strong>バックグラウンドアプリの更新を制限する。</strong>アプリが裏で常時同期していると、気づかないうちに10〜25%のバッテリーを消費します。</li>
    <li><strong>温度管理に気をつける。</strong>低温では放電が早まり、高温では劣化が加速します。理想的な使用温度は15〜25℃です。</li>
    <li><strong>省電力モードや機内モードを活用する。</strong>Wi-Fi・LTE・Bluetoothの無線送受信は電力消費が大きいです。不要な無線はオフに。</li>
    <li><strong>できるだけ低速充電を選ぶ。</strong>急速充電は熱を発生させ、長期的にバッテリーセルを傷めます。余裕があるときは普通充電が長寿命につながります。</li>
    <li><strong>充電器は適切な出力のものを使う。</strong>推奨外の充電器は効率を下げ、セルにストレスを与えます。メーカー推奨の出力を守りましょう。</li>
    <li><strong>長期保管は残量50%で。</strong>数週間以上使わない場合は、残量50%前後にしてから涼しい場所に保管してください。</li>
  </ul>
</div>

<h2>計算方法について</h2>
<div class="card">
  <p>基本的な計算式は次のとおりです：</p>
  <p><strong>稼働時間（時間）＝ 容量（mAh）× 効率 ÷ 消費電流（mA）</strong></p>
  <p>ワット時で計算する場合：</p>
  <p><strong>稼働時間（時間）＝ 容量（mAh）× 電圧（V）× 効率 ÷ 消費電力（W）÷ 1000</strong></p>
  <p><strong>効率係数</strong>は、バッテリーセルの発熱損失、電源管理ICでの変換ロス、負荷がかかった状態では定格容量まで完全に使えないといった実使用上の損失を考慮した補正値です。リチウムイオン電池の一般的な目安は85%。劣化したバッテリーや低温環境では70〜75%程度を見込んでください。</p>
</div>

<hr class="section-divider">

<div class="cta-box">

IT機器の経費管理を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で固定資産を自動管理</a>

</div>

<script>
(function() {
  var presets = {
    smartphone:  { mah: 4500,  voltage: 3.7,  ma: 150,   label: "スマートフォン（標準使用）" },
    tablet:      { mah: 8000,  voltage: 3.7,  ma: 280,   label: "タブレット（混合使用）" },
    laptop:      { mah: 50000, voltage: 3.6,  ma: 2200,  label: "ノートPC（軽作業）" },
    iot:         { mah: 2000,  voltage: 3.0,  ma: 5,     label: "IoTセンサー（スリープサイクル）" },
    drone:       { mah: 5200,  voltage: 11.1, ma: 15000, label: "ドローン（ホバリング）" },
    earbuds:     { mah: 55,    voltage: 3.7,  ma: 12,    label: "ワイヤレスイヤホン" },
    smartwatch:  { mah: 300,   voltage: 3.7,  ma: 25,    label: "スマートウォッチ（常時表示）" },
    ebike:       { mah: 13500, voltage: 36,   ma: 8000,  label: "電動アシスト自転車（アシストモード）" }
  };

  window.blApplyPreset = function(key) {
    var p = presets[key];
    if (!p) return;
    document.getElementById('bl-mah').value = p.mah;
    document.getElementById('bl-voltage').value = p.voltage;
    document.getElementById('bl-ma').value = p.ma;
    document.querySelector('input[name="bl-power-mode"][value="ma"]').checked = true;
    blTogglePowerMode();
  };

  window.blTogglePowerMode = function() {
    var mode = document.querySelector('input[name="bl-power-mode"]:checked').value;
    document.getElementById('bl-ma-field').style.display = mode === 'ma' ? '' : 'none';
    document.getElementById('bl-w-field').style.display  = mode === 'w'  ? '' : 'none';
  };

  function fmt(h) {
    var hrs = Math.floor(h);
    var min = Math.round((h - hrs) * 60);
    if (min === 60) { hrs++; min = 0; }
    if (hrs === 0) return min + '分';
    if (min === 0) return hrs + '時間';
    return hrs + '時間' + min + '分';
  }

  window.blCalculateRuntime = function() {
    var mah  = parseFloat(document.getElementById('bl-mah').value);
    var v    = parseFloat(document.getElementById('bl-voltage').value);
    var eff  = parseFloat(document.getElementById('bl-efficiency').value) / 100;
    var mode = document.querySelector('input[name="bl-power-mode"]:checked').value;
    var drawW;
    if (mode === 'ma') {
      var ma = parseFloat(document.getElementById('bl-ma').value);
      drawW  = ma * v / 1000;
    } else {
      drawW = parseFloat(document.getElementById('bl-w').value);
    }
    if (!mah || !v || !drawW || drawW <= 0) return;

    var totalWh  = mah * v / 1000;
    var effWh    = totalWh * eff;
    var runtime  = effWh / drawW;
    var drawMa   = drawW / v * 1000;

    var box = document.getElementById('bl-result-runtime');
    box.classList.add('visible');
    document.getElementById('bl-runtime-main').textContent = fmt(runtime);
    document.getElementById('bl-runtime-sub').textContent  = '現在の設定における推定稼働時間';
    document.getElementById('bl-res-wh').textContent   = totalWh.toFixed(2) + ' Wh';
    document.getElementById('bl-res-draw').textContent = drawMa.toFixed(0) + ' mA / ' + (drawW * 1000).toFixed(0) + ' mW';
    document.getElementById('bl-res-eff').textContent  = (eff * 100).toFixed(0) + '%';
    document.getElementById('bl-res-dec').textContent  = runtime.toFixed(2) + ' 時間';
  };

  window.blCalculateReverse = function() {
    var h    = parseFloat(document.getElementById('bl-target-h').value) || 0;
    var m    = parseFloat(document.getElementById('bl-target-m').value) || 0;
    var v    = parseFloat(document.getElementById('bl-rev-voltage').value);
    var ma   = parseFloat(document.getElementById('bl-rev-ma').value);
    var eff  = parseFloat(document.getElementById('bl-rev-eff').value) / 100;
    var totalH = h + m / 60;
    if (!totalH || !v || !ma || !eff) return;

    var minMah = (ma * totalH) / eff;
    var recMah = minMah * 1.2;
    var wh     = minMah * v / 1000;

    var box = document.getElementById('bl-result-reverse');
    box.classList.add('visible');
    document.getElementById('bl-rev-main').textContent = Math.ceil(minMah).toLocaleString() + ' mAh 以上必要';
    document.getElementById('bl-rev-sub').textContent  = fmt(totalH) + 'の稼働に必要なバッテリー容量';
    document.getElementById('bl-rev-min').textContent  = Math.ceil(minMah).toLocaleString() + ' mAh';
    document.getElementById('bl-rev-rec').textContent  = Math.ceil(recMah).toLocaleString() + ' mAh';
    document.getElementById('bl-rev-wh').textContent   = wh.toFixed(2) + ' Wh';
    document.getElementById('bl-rev-eff-res').textContent = (eff * 100).toFixed(0) + '%';
  };

  window.blCalculateCharging = function() {
    var mah      = parseFloat(document.getElementById('bl-ch-mah').value);
    var chargerW = parseFloat(document.getElementById('bl-ch-w').value);
    var v        = parseFloat(document.getElementById('bl-ch-voltage').value);
    var current  = parseFloat(document.getElementById('bl-ch-current').value) || 0;
    var eff      = parseFloat(document.getElementById('bl-ch-efficiency').value) / 100;
    if (!mah || !chargerW || !v) return;

    var chargerMa    = chargerW * 1000 / v * eff;
    var emptyWh      = mah * v / 1000;
    var remainFrac   = current / 100;
    var toFull       = emptyWh * (1 - remainFrac);
    var to80Frac     = Math.max(0, 0.8 - remainFrac);
    var to80Wh       = emptyWh * to80Frac;
    var hToFull      = toFull  / (chargerW * eff);
    var hTo80        = to80Wh  / (chargerW * eff);

    var box = document.getElementById('bl-result-charging');
    box.classList.add('visible');
    document.getElementById('bl-ch-main').textContent = fmt(hToFull) + 'で満充電';
    document.getElementById('bl-ch-sub').textContent  = current + '%から' + chargerW + 'Wの充電器で充電した場合';
    document.getElementById('bl-ch-80').textContent   = to80Frac > 0 ? fmt(hTo80) : 'すでに80%以上';
    document.getElementById('bl-ch-100').textContent  = fmt(hToFull);
    document.getElementById('bl-ch-rate').textContent = Math.round(chargerMa).toLocaleString() + ' mA';
    document.getElementById('bl-ch-wh').textContent   = toFull.toFixed(2) + ' Wh';
  };

  window.blSwitchTab = function(tab) {
    ['runtime','reverse','charging'].forEach(function(t) {
      document.getElementById('bl-tab-' + t).style.display = t === tab ? '' : 'none';
    });
    document.querySelectorAll('#bl-app .tab-btn').forEach(function(btn, i) {
      btn.classList.toggle('active', ['runtime','reverse','charging'][i] === tab);
    });
  };
})();
</script>
</div>
