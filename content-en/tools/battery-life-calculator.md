---
title: "Battery Life Calculator - Estimate Device Runtime"
description: "Estimate your device's battery life based on capacity, usage patterns, and power consumption. Free online battery duration calculator."
date: 2025-05-16
categories: ["Free Tools"]
slug: "battery-life-calculator"
ShowToc: false
cover:
  image: "/images/covers/battery-life-calculator.png"
---

<div id="bl-app">
<style>
#bl-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
  line-height: 1.6;
}
#bl-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 1.6rem 0 0.8rem;
  color: #16213e;
}
#bl-app h3 {
  font-size: 1.1rem;
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
  padding: 0.6rem 1rem;
  background: #f1f5f9;
  border: none;
  cursor: pointer;
  font-size: 0.9rem;
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
  text-transform: uppercase;
  letter-spacing: 0.03em;
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
#bl-app .result-item .label {
  font-size: 0.78rem;
  color: #64748b;
  text-transform: uppercase;
  font-weight: 600;
  letter-spacing: 0.03em;
}
#bl-app .result-item .value {
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
#bl-app .related-links {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-top: 0.6rem;
}
#bl-app .related-links a {
  color: #2563eb;
  text-decoration: none;
  font-size: 0.9rem;
  border: 1px solid #bfdbfe;
  border-radius: 6px;
  padding: 0.3rem 0.75rem;
  transition: background 0.15s;
}
#bl-app .related-links a:hover {
  background: #eff6ff;
}
#bl-app .section-divider {
  border: none;
  border-top: 2px solid #e2e8f0;
  margin: 1.6rem 0;
}
#bl-app .power-toggle {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 0.8rem;
}
#bl-app .power-toggle label {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  text-transform: none;
  letter-spacing: 0;
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

<h2>Battery Life Calculator</h2>
<p>Instantly estimate how long your device will run on a single charge — or find out what battery capacity you need for a target runtime. Works for smartphones, laptops, tablets, IoT sensors, drones, and more.</p>

<div class="tabs">
  <button class="tab-btn active" onclick="blSwitchTab('runtime')">Runtime Estimator</button>
  <button class="tab-btn" onclick="blSwitchTab('reverse')">Reverse: Capacity Needed</button>
  <button class="tab-btn" onclick="blSwitchTab('charging')">Charging Time</button>
</div>

<!-- ===== TAB: RUNTIME ===== -->
<div id="bl-tab-runtime">
  <div class="card card-blue">
    <h3>Device Presets</h3>
    <div class="presets">
      <button class="preset-btn" onclick="blApplyPreset('smartphone')">Smartphone</button>
      <button class="preset-btn" onclick="blApplyPreset('tablet')">Tablet</button>
      <button class="preset-btn" onclick="blApplyPreset('laptop')">Laptop</button>
      <button class="preset-btn" onclick="blApplyPreset('iot')">IoT Sensor</button>
      <button class="preset-btn" onclick="blApplyPreset('drone')">Drone</button>
      <button class="preset-btn" onclick="blApplyPreset('earbuds')">Earbuds</button>
      <button class="preset-btn" onclick="blApplyPreset('smartwatch')">Smartwatch</button>
      <button class="preset-btn" onclick="blApplyPreset('ebike')">E-Bike</button>
    </div>

    <h3>Battery Capacity</h3>
    <div class="field-row">
      <div>
        <label>Capacity (mAh)</label>
        <input type="number" id="bl-mah" value="4000" min="1" step="100">
      </div>
      <div>
        <label>Battery Voltage (V)</label>
        <input type="number" id="bl-voltage" value="3.7" min="0.1" step="0.1">
      </div>
    </div>

    <h3>Power Consumption</h3>
    <div class="power-toggle">
      <label><input type="radio" name="bl-power-mode" value="ma" checked onchange="blTogglePowerMode()"> Current draw (mA)</label>
      <label><input type="radio" name="bl-power-mode" value="w" onchange="blTogglePowerMode()"> Wattage (W)</label>
    </div>
    <div class="field-row">
      <div id="bl-ma-field">
        <label>Current Draw (mA)</label>
        <input type="number" id="bl-ma" value="150" min="0.1" step="10">
      </div>
      <div id="bl-w-field" style="display:none;">
        <label>Power (W)</label>
        <input type="number" id="bl-w" value="0.555" min="0.001" step="0.1">
      </div>
      <div></div>
    </div>

    <div class="slider-row">
      <label>Efficiency Factor: <strong id="bl-eff-label">85%</strong> <span class="badge">Real-world loss</span></label>
      <input type="range" id="bl-efficiency" min="70" max="95" value="85" step="1" oninput="document.getElementById('bl-eff-label').textContent=this.value+'%'">
      <div class="slider-labels"><span>70% (Poor)</span><span>80%</span><span>90%</span><span>95% (Ideal)</span></div>
    </div>

    <button class="calc-btn" onclick="blCalculateRuntime()">Calculate Runtime</button>
  </div>

  <div class="result-box" id="bl-result-runtime">
    <div class="result-main" id="bl-runtime-main">--</div>
    <div class="result-sub" id="bl-runtime-sub"></div>
    <div class="result-grid">
      <div class="result-item">
        <div class="label">Battery Energy</div>
        <div class="value" id="bl-res-wh">--</div>
      </div>
      <div class="result-item">
        <div class="label">Effective Power Draw</div>
        <div class="value" id="bl-res-draw">--</div>
      </div>
      <div class="result-item">
        <div class="label">Efficiency Applied</div>
        <div class="value" id="bl-res-eff">--</div>
      </div>
      <div class="result-item">
        <div class="label">Runtime (decimal)</div>
        <div class="value" id="bl-res-dec">--</div>
      </div>
    </div>
  </div>
</div>

<!-- ===== TAB: REVERSE ===== -->
<div id="bl-tab-reverse" style="display:none;">
  <div class="card card-green">
    <h3>Target Runtime</h3>
    <div class="field-row three">
      <div>
        <label>Hours needed</label>
        <input type="number" id="bl-target-h" value="8" min="0" step="1">
      </div>
      <div>
        <label>Minutes needed</label>
        <input type="number" id="bl-target-m" value="0" min="0" max="59" step="5">
      </div>
      <div>
        <label>Voltage (V)</label>
        <input type="number" id="bl-rev-voltage" value="3.7" min="0.1" step="0.1">
      </div>
    </div>
    <div class="field-row">
      <div>
        <label>Current Draw (mA)</label>
        <input type="number" id="bl-rev-ma" value="150" min="0.1" step="10">
      </div>
      <div>
        <label>Efficiency Factor (%)</label>
        <input type="number" id="bl-rev-eff" value="85" min="70" max="95" step="1">
      </div>
    </div>
    <button class="calc-btn" onclick="blCalculateReverse()">Calculate Needed Capacity</button>
  </div>

  <div class="result-box" id="bl-result-reverse">
    <div class="result-main" id="bl-rev-main">--</div>
    <div class="result-sub" id="bl-rev-sub"></div>
    <div class="result-grid">
      <div class="result-item">
        <div class="label">Minimum mAh</div>
        <div class="value" id="bl-rev-min">--</div>
      </div>
      <div class="result-item">
        <div class="label">Recommended (+20% buffer)</div>
        <div class="value" id="bl-rev-rec">--</div>
      </div>
      <div class="result-item">
        <div class="label">Energy Required (Wh)</div>
        <div class="value" id="bl-rev-wh">--</div>
      </div>
      <div class="result-item">
        <div class="label">Efficiency Factor</div>
        <div class="value" id="bl-rev-eff-res">--</div>
      </div>
    </div>
  </div>
</div>

<!-- ===== TAB: CHARGING ===== -->
<div id="bl-tab-charging" style="display:none;">
  <div class="card card-amber">
    <h3>Charging Time Estimator</h3>
    <div class="field-row">
      <div>
        <label>Battery Capacity (mAh)</label>
        <input type="number" id="bl-ch-mah" value="4000" min="1" step="100">
      </div>
      <div>
        <label>Charger Output (W)</label>
        <input type="number" id="bl-ch-w" value="20" min="0.5" step="1">
      </div>
    </div>
    <div class="field-row">
      <div>
        <label>Battery Voltage (V)</label>
        <input type="number" id="bl-ch-voltage" value="3.7" min="0.1" step="0.1">
      </div>
      <div>
        <label>Current charge level (%)</label>
        <input type="number" id="bl-ch-current" value="20" min="0" max="99" step="5">
      </div>
    </div>
    <div class="slider-row">
      <label>Charging Efficiency: <strong id="bl-ch-eff-label">90%</strong></label>
      <input type="range" id="bl-ch-efficiency" min="75" max="98" value="90" step="1" oninput="document.getElementById('bl-ch-eff-label').textContent=this.value+'%'">
      <div class="slider-labels"><span>75%</span><span>85%</span><span>95%</span><span>98%</span></div>
    </div>
    <button class="calc-btn" onclick="blCalculateCharging()">Calculate Charging Time</button>
  </div>

  <div class="result-box" id="bl-result-charging">
    <div class="result-main" id="bl-ch-main">--</div>
    <div class="result-sub" id="bl-ch-sub"></div>
    <div class="result-grid">
      <div class="result-item">
        <div class="label">To 80% (Fast Charge)</div>
        <div class="value" id="bl-ch-80">--</div>
      </div>
      <div class="result-item">
        <div class="label">To 100% (Full)</div>
        <div class="value" id="bl-ch-100">--</div>
      </div>
      <div class="result-item">
        <div class="label">Charge Rate (mA)</div>
        <div class="value" id="bl-ch-rate">--</div>
      </div>
      <div class="result-item">
        <div class="label">Energy to Add (Wh)</div>
        <div class="value" id="bl-ch-wh">--</div>
      </div>
    </div>
  </div>
</div>

<hr class="section-divider">

<h2>Tips for Extending Battery Life</h2>
<div class="card">
  <ul class="tips-list">
    <li><strong>Avoid full discharges.</strong> Lithium batteries last longer when kept between 20–80% charge. Deep cycling accelerates capacity loss.</li>
    <li><strong>Reduce screen brightness.</strong> The display is the single largest power consumer in most mobile devices — cutting brightness 30% can extend runtime 15–20%.</li>
    <li><strong>Disable background refresh.</strong> Apps syncing in the background can consume 10–25% of battery without you noticing. Enable it only for critical apps.</li>
    <li><strong>Mind the temperature.</strong> Batteries discharge faster in cold and degrade faster in heat. Ideal operating range is 15–25°C (59–77°F).</li>
    <li><strong>Use low-power or airplane mode.</strong> Radio transmitters (Wi-Fi, LTE, Bluetooth) are heavy consumers. Disable unused radios for a significant runtime boost.</li>
    <li><strong>Slow-charge when possible.</strong> Fast charging generates heat, which degrades battery cells over time. Overnight slow-charging extends overall battery lifespan.</li>
    <li><strong>Match charger to device.</strong> Using an underpowered or overpowered charger reduces efficiency and can stress cells. Always use the manufacturer-recommended output.</li>
    <li><strong>Store at 50% for long-term.</strong> If storing a device unused for weeks or months, keep it at around 50% charge in a cool, dry place.</li>
  </ul>
</div>

<h2>How Battery Life Is Calculated</h2>
<div class="card">
  <p>The core formula is straightforward:</p>
  <p><strong>Runtime (hours) = (Capacity in mAh × Efficiency) ÷ Current Draw (mA)</strong></p>
  <p>Or, using watt-hours:</p>
  <p><strong>Runtime (hours) = (Capacity in mAh × Voltage × Efficiency) ÷ Power (W) ÷ 1000</strong></p>
  <p>The <strong>efficiency factor</strong> accounts for real-world losses: heat generation in battery cells, voltage conversion losses in the device's power management IC, and the fact that batteries cannot fully discharge to rated capacity under load. A value of 85% is a good general estimate for lithium-ion cells; older or colder batteries may warrant 70–75%.</p>
</div>

<h2>Related Tools</h2>
<div class="related-links">
  <a href="/tools/watt-hour-calculator/">Watt-Hour Calculator</a>
  <a href="/tools/solar-panel-calculator/">Solar Panel Output Calculator</a>
  <a href="/tools/power-consumption-calculator/">Device Power Consumption Calculator</a>
  <a href="/tools/co2-footprint-calculator/">Electronics CO2 Footprint</a>
</div>

<script>
(function() {
  var presets = {
    smartphone:  { mah: 4500,  voltage: 3.7,  ma: 150,   label: "Smartphone (moderate use)" },
    tablet:      { mah: 8000,  voltage: 3.7,  ma: 280,   label: "Tablet (mixed use)" },
    laptop:      { mah: 50000, voltage: 3.6,  ma: 2200,  label: "Laptop (light workload)" },
    iot:         { mah: 2000,  voltage: 3.0,  ma: 5,     label: "IoT Sensor (sleep-cycle)" },
    drone:       { mah: 5200,  voltage: 11.1, ma: 15000, label: "Drone (hover)" },
    earbuds:     { mah: 55,    voltage: 3.7,  ma: 12,    label: "Wireless Earbuds" },
    smartwatch:  { mah: 300,   voltage: 3.7,  ma: 25,    label: "Smartwatch (always-on)" },
    ebike:       { mah: 13500, voltage: 36,   ma: 8000,  label: "E-Bike (assist mode)" }
  };

  window.blApplyPreset = function(key) {
    var p = presets[key];
    if (!p) return;
    document.getElementById('bl-mah').value = p.mah;
    document.getElementById('bl-voltage').value = p.voltage;
    document.getElementById('bl-ma').value = p.ma;
    // switch to mA mode
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
    if (hrs === 0) return min + ' min';
    if (min === 0) return hrs + ' hr';
    return hrs + ' hr ' + min + ' min';
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
    document.getElementById('bl-runtime-sub').textContent  = 'Estimated runtime under current settings';
    document.getElementById('bl-res-wh').textContent   = totalWh.toFixed(2) + ' Wh';
    document.getElementById('bl-res-draw').textContent = drawMa.toFixed(0) + ' mA / ' + (drawW * 1000).toFixed(0) + ' mW';
    document.getElementById('bl-res-eff').textContent  = (eff * 100).toFixed(0) + '%';
    document.getElementById('bl-res-dec').textContent  = runtime.toFixed(2) + ' hr';
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
    document.getElementById('bl-rev-main').textContent = Math.ceil(minMah).toLocaleString() + ' mAh minimum';
    document.getElementById('bl-rev-sub').textContent  = 'Battery capacity needed for ' + fmt(totalH) + ' of runtime';
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
    var hToFull      = (toFull  / (chargerW * eff));
    var hTo80        = (to80Wh  / (chargerW * eff));

    var box = document.getElementById('bl-result-charging');
    box.classList.add('visible');
    document.getElementById('bl-ch-main').textContent = fmt(hToFull) + ' to full';
    document.getElementById('bl-ch-sub').textContent  = 'Charging from ' + current + '% with a ' + chargerW + 'W charger';
    document.getElementById('bl-ch-80').textContent   = to80Frac > 0 ? fmt(hTo80) : 'Already above 80%';
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
