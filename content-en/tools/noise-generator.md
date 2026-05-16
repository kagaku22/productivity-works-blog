---
title: "White Noise Generator"
date: 2025-05-16
description: "Free online white noise generator. Play white, pink, brown, and ambient noise to help you focus, relax, or sleep — powered by Web Audio API, no sign-up required."
categories: ["Free Tools"]
slug: "noise-generator"
ShowToc: false
cover:
  image: "/images/covers/noise-generator.png"
  alt: "White Noise Generator"
---

Block out distractions and create your ideal sound environment — mix white, pink, brown, and rain noise directly in your browser with no downloads or sign-ups required.

<div id="ng-app">

<style>
#ng-app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #e2e8f0;
  background: #0f172a;
  border-radius: 16px;
  padding: 28px 24px 32px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.45);
}

#ng-app * {
  box-sizing: border-box;
}

#ng-app h2 {
  margin: 0 0 4px;
  font-size: 1.25rem;
  font-weight: 700;
  color: #f8fafc;
  letter-spacing: -0.01em;
}

#ng-app .ng-subtitle {
  font-size: 0.82rem;
  color: #94a3b8;
  margin: 0 0 24px;
}

/* Canvas */
#ng-app canvas {
  display: block;
  width: 100%;
  height: 90px;
  background: #1e293b;
  border-radius: 10px;
  margin-bottom: 24px;
}

/* Channel cards */
#ng-app .ng-channels {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 24px;
}

@media (max-width: 480px) {
  #ng-app .ng-channels {
    grid-template-columns: 1fr;
  }
}

#ng-app .ng-channel {
  background: #1e293b;
  border: 1.5px solid #334155;
  border-radius: 12px;
  padding: 14px 16px;
  transition: border-color 0.2s;
}

#ng-app .ng-channel.ng-active {
  border-color: #38bdf8;
  background: #0c2a3f;
}

#ng-app .ng-channel-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
}

#ng-app .ng-channel-label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  color: #cbd5e1;
}

#ng-app .ng-channel-label .ng-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex-shrink: 0;
}

#ng-app .dot-white  { background: #f1f5f9; }
#ng-app .dot-pink   { background: #f472b6; }
#ng-app .dot-brown  { background: #a16207; }
#ng-app .dot-rain   { background: #38bdf8; }

/* Toggle switch */
#ng-app .ng-toggle {
  position: relative;
  width: 38px;
  height: 21px;
  flex-shrink: 0;
}

#ng-app .ng-toggle input {
  opacity: 0;
  width: 0;
  height: 0;
  position: absolute;
}

#ng-app .ng-toggle-track {
  position: absolute;
  inset: 0;
  background: #334155;
  border-radius: 21px;
  cursor: pointer;
  transition: background 0.2s;
}

#ng-app .ng-toggle input:checked + .ng-toggle-track {
  background: #0ea5e9;
}

#ng-app .ng-toggle-track::after {
  content: "";
  position: absolute;
  left: 3px;
  top: 3px;
  width: 15px;
  height: 15px;
  background: #fff;
  border-radius: 50%;
  transition: transform 0.2s;
}

#ng-app .ng-toggle input:checked + .ng-toggle-track::after {
  transform: translateX(17px);
}

/* Volume slider */
#ng-app .ng-slider-row {
  display: flex;
  align-items: center;
  gap: 8px;
}

#ng-app .ng-slider-row span {
  font-size: 0.75rem;
  color: #64748b;
  width: 28px;
  text-align: right;
  flex-shrink: 0;
}

#ng-app input[type="range"] {
  -webkit-appearance: none;
  appearance: none;
  flex: 1;
  height: 5px;
  background: #334155;
  border-radius: 5px;
  outline: none;
  cursor: pointer;
}

#ng-app input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #38bdf8;
  cursor: pointer;
  transition: background 0.2s;
}

#ng-app input[type="range"]::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #38bdf8;
  border: none;
  cursor: pointer;
}

#ng-app input[type="range"]:hover::-webkit-slider-thumb {
  background: #7dd3fc;
}

/* Master controls */
#ng-app .ng-master {
  background: #1e293b;
  border-radius: 12px;
  padding: 18px 20px;
}

#ng-app .ng-master-row {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 16px;
}

#ng-app .ng-master-label {
  font-size: 0.8rem;
  font-weight: 600;
  color: #94a3b8;
  width: 90px;
  flex-shrink: 0;
}

#ng-app .ng-controls-row {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  flex-wrap: wrap;
  margin-top: 4px;
}

/* Play button */
#ng-app #ng-play-btn {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  border: none;
  background: linear-gradient(135deg, #0ea5e9, #6366f1);
  color: #fff;
  font-size: 1.6rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  box-shadow: 0 4px 16px rgba(14,165,233,0.35);
  transition: transform 0.15s, box-shadow 0.15s;
  line-height: 1;
}

#ng-app #ng-play-btn:hover {
  transform: scale(1.06);
  box-shadow: 0 6px 22px rgba(14,165,233,0.5);
}

#ng-app #ng-play-btn:active {
  transform: scale(0.97);
}

/* Timer select */
#ng-app #ng-timer-select {
  background: #0f172a;
  border: 1.5px solid #334155;
  color: #cbd5e1;
  font-family: inherit;
  font-size: 0.82rem;
  border-radius: 8px;
  padding: 8px 10px;
  cursor: pointer;
  outline: none;
  transition: border-color 0.2s;
}

#ng-app #ng-timer-select:hover,
#ng-app #ng-timer-select:focus {
  border-color: #38bdf8;
}

#ng-app .ng-timer-display {
  font-size: 0.8rem;
  color: #38bdf8;
  font-variant-numeric: tabular-nums;
  min-width: 52px;
  text-align: center;
}

/* Status */
#ng-app .ng-status {
  text-align: center;
  font-size: 0.75rem;
  color: #475569;
  margin-top: 14px;
}
</style>

<canvas id="ng-canvas" width="640" height="90" aria-hidden="true"></canvas>

<div class="ng-channels">

  <!-- White noise -->
  <div class="ng-channel" id="ng-card-white">
    <div class="ng-channel-header">
      <span class="ng-channel-label">
        <span class="ng-dot dot-white"></span>White
      </span>
      <label class="ng-toggle" aria-label="Toggle white noise">
        <input type="checkbox" id="ng-toggle-white" data-channel="white">
        <span class="ng-toggle-track"></span>
      </label>
    </div>
    <div class="ng-slider-row">
      <input type="range" id="ng-vol-white" min="0" max="100" value="70" aria-label="White noise volume">
      <span id="ng-vol-white-display">70%</span>
    </div>
  </div>

  <!-- Pink noise -->
  <div class="ng-channel" id="ng-card-pink">
    <div class="ng-channel-header">
      <span class="ng-channel-label">
        <span class="ng-dot dot-pink"></span>Pink
      </span>
      <label class="ng-toggle" aria-label="Toggle pink noise">
        <input type="checkbox" id="ng-toggle-pink" data-channel="pink">
        <span class="ng-toggle-track"></span>
      </label>
    </div>
    <div class="ng-slider-row">
      <input type="range" id="ng-vol-pink" min="0" max="100" value="70" aria-label="Pink noise volume">
      <span id="ng-vol-pink-display">70%</span>
    </div>
  </div>

  <!-- Brown noise -->
  <div class="ng-channel" id="ng-card-brown">
    <div class="ng-channel-header">
      <span class="ng-channel-label">
        <span class="ng-dot dot-brown"></span>Brown
      </span>
      <label class="ng-toggle" aria-label="Toggle brown noise">
        <input type="checkbox" id="ng-toggle-brown" data-channel="brown">
        <span class="ng-toggle-track"></span>
      </label>
    </div>
    <div class="ng-slider-row">
      <input type="range" id="ng-vol-brown" min="0" max="100" value="70" aria-label="Brown noise volume">
      <span id="ng-vol-brown-display">70%</span>
    </div>
  </div>

  <!-- Rain -->
  <div class="ng-channel" id="ng-card-rain">
    <div class="ng-channel-header">
      <span class="ng-channel-label">
        <span class="ng-dot dot-rain"></span>Rain
      </span>
      <label class="ng-toggle" aria-label="Toggle rain noise">
        <input type="checkbox" id="ng-toggle-rain" data-channel="rain">
        <span class="ng-toggle-track"></span>
      </label>
    </div>
    <div class="ng-slider-row">
      <input type="range" id="ng-vol-rain" min="0" max="100" value="70" aria-label="Rain noise volume">
      <span id="ng-vol-rain-display">70%</span>
    </div>
  </div>

</div><!-- /.ng-channels -->

<div class="ng-master">
  <div class="ng-master-row">
    <span class="ng-master-label">Master vol</span>
    <input type="range" id="ng-master-vol" min="0" max="100" value="80" aria-label="Master volume">
    <span id="ng-master-vol-display">80%</span>
  </div>

  <div class="ng-controls-row">
    <button id="ng-play-btn" aria-label="Play / Pause" title="Play / Pause">&#9654;</button>

    <select id="ng-timer-select" aria-label="Auto-stop timer">
      <option value="0">No timer</option>
      <option value="900">15 min</option>
      <option value="1800">30 min</option>
      <option value="3600">60 min</option>
      <option value="7200">2 hr</option>
    </select>

    <span class="ng-timer-display" id="ng-timer-display" aria-live="polite"></span>
  </div>

  <p class="ng-status" id="ng-status">Press play to start</p>
</div>

<script>
(function () {
  "use strict";

  /* ── State ───────────────────────────────────────────────── */
  let audioCtx = null;
  let masterGain = null;
  let analyser = null;
  let isPlaying = false;
  let timerEnd = null;
  let timerInterval = null;
  let rafId = null;

  const channels = {
    white: { enabled: false, vol: 0.70, gainNode: null, processor: null },
    pink:  { enabled: false, vol: 0.70, gainNode: null, processor: null },
    brown: { enabled: false, vol: 0.70, gainNode: null, processor: null },
    rain:  { enabled: false, vol: 0.70, gainNode: null, processor: null, rainFilter: null, rainGain: null },
  };

  /* ── DOM refs ─────────────────────────────────────────────── */
  const playBtn        = document.getElementById("ng-play-btn");
  const masterVolEl    = document.getElementById("ng-master-vol");
  const masterVolDisp  = document.getElementById("ng-master-vol-display");
  const timerSel       = document.getElementById("ng-timer-select");
  const timerDisp      = document.getElementById("ng-timer-display");
  const statusEl       = document.getElementById("ng-status");
  const canvas         = document.getElementById("ng-canvas");
  const ctx2d          = canvas.getContext("2d");

  /* ── Audio init ───────────────────────────────────────────── */
  function initAudio() {
    if (audioCtx) return;
    audioCtx  = new (window.AudioContext || window.webkitAudioContext)();
    masterGain = audioCtx.createGain();
    masterGain.gain.value = parseInt(masterVolEl.value) / 100;
    analyser  = audioCtx.createAnalyser();
    analyser.fftSize = 2048;
    masterGain.connect(analyser);
    analyser.connect(audioCtx.destination);
  }

  /* ── Noise generators ────────────────────────────────────── */

  function createWhiteProcessor() {
    const proc = audioCtx.createScriptProcessor(4096, 0, 1);
    proc.onaudioprocess = function (e) {
      const out = e.outputBuffer.getChannelData(0);
      for (let i = 0; i < out.length; i++) {
        out[i] = Math.random() * 2 - 1;
      }
    };
    return proc;
  }

  // Voss-McCartney pink noise (16 octave bands)
  function createPinkProcessor() {
    const NUM_OCTAVES = 16;
    const vals = new Float32Array(NUM_OCTAVES);
    let runningSum = 0;
    let counter = 0;
    const proc = audioCtx.createScriptProcessor(4096, 0, 1);
    proc.onaudioprocess = function (e) {
      const out = e.outputBuffer.getChannelData(0);
      for (let i = 0; i < out.length; i++) {
        // determine which octave to update (trailing zeros of counter)
        let c = counter;
        for (let k = 0; k < NUM_OCTAVES; k++) {
          if ((c & 1) === 0) {
            runningSum -= vals[k];
            vals[k] = Math.random() * 2 - 1;
            runningSum += vals[k];
            break;
          }
          c >>= 1;
        }
        counter++;
        // white noise contribution + normalise
        out[i] = (runningSum + (Math.random() * 2 - 1)) / (NUM_OCTAVES + 1);
      }
    };
    return proc;
  }

  // Brown noise — leaky integrator of white noise
  function createBrownProcessor() {
    let lastOut = 0;
    const proc = audioCtx.createScriptProcessor(4096, 0, 1);
    proc.onaudioprocess = function (e) {
      const out = e.outputBuffer.getChannelData(0);
      for (let i = 0; i < out.length; i++) {
        const white = Math.random() * 2 - 1;
        lastOut = (lastOut + 0.02 * white) / 1.02;
        out[i] = lastOut * 3.5; // amplify to audible range
      }
    };
    return proc;
  }

  // Rain — white noise through a bandpass with slow random gain modulation
  function createRainProcessor() {
    // White noise source
    const proc = audioCtx.createScriptProcessor(4096, 0, 1);
    let phase = 0;
    proc.onaudioprocess = function (e) {
      const out = e.outputBuffer.getChannelData(0);
      for (let i = 0; i < out.length; i++) {
        out[i] = Math.random() * 2 - 1;
      }
    };

    // Bandpass around ~2 kHz to mimic rain frequency
    const bpf = audioCtx.createBiquadFilter();
    bpf.type = "bandpass";
    bpf.frequency.value = 2000;
    bpf.Q.value = 0.8;

    // Second bandpass layer for texture
    const bpf2 = audioCtx.createBiquadFilter();
    bpf2.type = "bandpass";
    bpf2.frequency.value = 800;
    bpf2.Q.value = 0.5;

    // Slow LFO for modulation (simulates gusts)
    const lfo = audioCtx.createOscillator();
    const lfoGain = audioCtx.createGain();
    lfo.frequency.value = 0.08 + Math.random() * 0.05;
    lfoGain.gain.value = 0.4;
    lfo.connect(lfoGain);

    const mixGain = audioCtx.createGain();
    mixGain.gain.value = 1;

    // proc -> bpf -> mixGain
    proc.connect(bpf);
    bpf.connect(mixGain);
    // proc -> bpf2 -> mixGain (blend two bands)
    proc.connect(bpf2);
    bpf2.connect(mixGain);

    lfoGain.connect(mixGain.gain);
    lfo.start();

    return { proc, mixGain, lfo, bpf, bpf2, lfoGain };
  }

  /* ── Start/stop individual channel ───────────────────────── */
  function startChannel(name) {
    const ch = channels[name];
    if (ch.processor) return; // already running

    const gainNode = audioCtx.createGain();
    gainNode.gain.value = ch.vol;
    gainNode.connect(masterGain);
    ch.gainNode = gainNode;

    if (name === "white") {
      const proc = createWhiteProcessor();
      proc.connect(gainNode);
      ch.processor = proc;
    } else if (name === "pink") {
      const proc = createPinkProcessor();
      proc.connect(gainNode);
      ch.processor = proc;
    } else if (name === "brown") {
      const proc = createBrownProcessor();
      proc.connect(gainNode);
      ch.processor = proc;
    } else if (name === "rain") {
      const rain = createRainProcessor();
      rain.mixGain.connect(gainNode);
      ch.processor = rain.proc;
      ch._rain = rain;
    }
  }

  function stopChannel(name) {
    const ch = channels[name];
    if (!ch.processor) return;
    try {
      ch.processor.disconnect();
      if (name === "rain" && ch._rain) {
        ch._rain.lfo.stop();
        ch._rain.bpf.disconnect();
        ch._rain.bpf2.disconnect();
        ch._rain.mixGain.disconnect();
        ch._rain.lfoGain.disconnect();
        ch._rain = null;
      }
    } catch (_) {}
    try { ch.gainNode.disconnect(); } catch (_) {}
    ch.processor = null;
    ch.gainNode  = null;
  }

  /* ── Play / Pause ─────────────────────────────────────────── */
  function startAll() {
    initAudio();
    if (audioCtx.state === "suspended") audioCtx.resume();
    Object.keys(channels).forEach(name => {
      if (channels[name].enabled) startChannel(name);
    });
    isPlaying = true;
    playBtn.innerHTML = "&#9646;&#9646;";
    statusEl.textContent = "Playing…";
    startViz();
    startTimer();
  }

  function stopAll() {
    Object.keys(channels).forEach(stopChannel);
    isPlaying = false;
    playBtn.innerHTML = "&#9654;";
    statusEl.textContent = "Paused";
    clearTimer();
    stopViz();
  }

  playBtn.addEventListener("click", function () {
    if (!isPlaying) {
      startAll();
    } else {
      stopAll();
    }
  });

  /* ── Channel toggles ─────────────────────────────────────── */
  ["white", "pink", "brown", "rain"].forEach(function (name) {
    const toggle = document.getElementById("ng-toggle-" + name);
    const card   = document.getElementById("ng-card-" + name);
    const volEl  = document.getElementById("ng-vol-" + name);
    const dispEl = document.getElementById("ng-vol-" + name + "-display");

    toggle.addEventListener("change", function () {
      channels[name].enabled = toggle.checked;
      card.classList.toggle("ng-active", toggle.checked);
      if (isPlaying) {
        if (toggle.checked) {
          startChannel(name);
        } else {
          stopChannel(name);
        }
      }
    });

    volEl.addEventListener("input", function () {
      const v = parseInt(volEl.value) / 100;
      channels[name].vol = v;
      dispEl.textContent = volEl.value + "%";
      if (channels[name].gainNode) {
        channels[name].gainNode.gain.setTargetAtTime(v, audioCtx.currentTime, 0.01);
      }
    });
  });

  /* ── Master volume ────────────────────────────────────────── */
  masterVolEl.addEventListener("input", function () {
    const v = parseInt(masterVolEl.value) / 100;
    masterVolDisp.textContent = masterVolEl.value + "%";
    if (masterGain) {
      masterGain.gain.setTargetAtTime(v, audioCtx.currentTime, 0.01);
    }
  });

  /* ── Timer ────────────────────────────────────────────────── */
  function startTimer() {
    clearTimer();
    const secs = parseInt(timerSel.value);
    if (secs === 0) { timerDisp.textContent = ""; return; }
    timerEnd = Date.now() + secs * 1000;
    timerInterval = setInterval(tickTimer, 1000);
    tickTimer();
  }

  function tickTimer() {
    if (!timerEnd) return;
    const remaining = Math.max(0, timerEnd - Date.now());
    if (remaining <= 0) {
      timerDisp.textContent = "00:00";
      stopAll();
      statusEl.textContent = "Timer ended";
      return;
    }
    const m = Math.floor(remaining / 60000);
    const s = Math.floor((remaining % 60000) / 1000);
    timerDisp.textContent = String(m).padStart(2, "0") + ":" + String(s).padStart(2, "0");
  }

  function clearTimer() {
    if (timerInterval) { clearInterval(timerInterval); timerInterval = null; }
    timerEnd = null;
    timerDisp.textContent = "";
  }

  timerSel.addEventListener("change", function () {
    if (isPlaying) startTimer();
  });

  /* ── Waveform visualisation ───────────────────────────────── */
  function startViz() {
    if (rafId) return;
    drawFrame();
  }

  function stopViz() {
    if (rafId) { cancelAnimationFrame(rafId); rafId = null; }
    // clear canvas
    ctx2d.fillStyle = "#1e293b";
    ctx2d.fillRect(0, 0, canvas.width, canvas.height);
  }

  function drawFrame() {
    rafId = requestAnimationFrame(drawFrame);
    if (!analyser) return;

    const bufLen = analyser.fftSize;
    const data   = new Float32Array(bufLen);
    analyser.getFloatTimeDomainData(data);

    const W = canvas.width;
    const H = canvas.height;

    ctx2d.fillStyle = "#1e293b";
    ctx2d.fillRect(0, 0, W, H);

    ctx2d.lineWidth   = 1.5;
    ctx2d.strokeStyle = "#38bdf8";
    ctx2d.shadowColor = "#38bdf8";
    ctx2d.shadowBlur  = 6;
    ctx2d.beginPath();

    const step = Math.ceil(bufLen / W);
    let x = 0;
    for (let i = 0; i < W; i++) {
      const sample = data[i * step] || 0;
      const y = (1 - (sample * 0.5 + 0.5)) * H;
      if (i === 0) ctx2d.moveTo(x, y);
      else         ctx2d.lineTo(x, y);
      x += 1;
    }
    ctx2d.stroke();
    ctx2d.shadowBlur = 0;
  }

  /* ── Initial canvas placeholder ──────────────────────────── */
  (function () {
    const W = canvas.width, H = canvas.height;
    ctx2d.fillStyle = "#1e293b";
    ctx2d.fillRect(0, 0, W, H);
    ctx2d.strokeStyle = "#334155";
    ctx2d.lineWidth = 1;
    ctx2d.beginPath();
    ctx2d.moveTo(0, H / 2);
    ctx2d.lineTo(W, H / 2);
    ctx2d.stroke();
  })();

})();
</script>

</div><!-- /#ng-app -->

---

> Focus with Pomodoro → [Pomodoro Timer](/tools/pomodoro-timer/)
> Test typing speed → [Typing Speed Test](/tools/typing-speed-test/)
> Generate lorem ipsum → [Lorem Ipsum Generator](/tools/lorem-ipsum-generator/)
