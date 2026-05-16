---
title: "White Noise Generator - Focus & Sleep Sounds"
description: "Generate white, pink, and brown noise for focus, sleep, or relaxation. Free online ambient sound generator."
date: 2025-05-16
slug: "white-noise-generator"
categories: ["Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/white-noise-generator.png"
---

<div id="wn-app">

<style>
#wn-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  padding: 24px 16px;
  color: #1a1a2e;
}
#wn-app h2 {
  font-size: 1.4rem;
  margin: 0 0 6px;
  color: #1a1a2e;
}
#wn-app .wn-subtitle {
  font-size: 0.9rem;
  color: #666;
  margin: 0 0 28px;
}
#wn-app .wn-card {
  background: #f8f9ff;
  border: 1px solid #e0e4f0;
  border-radius: 16px;
  padding: 28px 24px;
  margin-bottom: 20px;
}
#wn-app .wn-noise-types {
  display: flex;
  gap: 10px;
  margin-bottom: 24px;
  flex-wrap: wrap;
}
#wn-app .wn-noise-btn {
  flex: 1;
  min-width: 90px;
  padding: 14px 8px;
  border: 2px solid #d0d6f0;
  border-radius: 12px;
  background: #fff;
  cursor: pointer;
  text-align: center;
  font-size: 0.85rem;
  font-weight: 600;
  color: #555;
  transition: all 0.2s ease;
  user-select: none;
}
#wn-app .wn-noise-btn:hover {
  border-color: #6c63ff;
  color: #6c63ff;
  background: #f0eeff;
}
#wn-app .wn-noise-btn.active {
  border-color: #6c63ff;
  background: #6c63ff;
  color: #fff;
}
#wn-app .wn-noise-btn .wn-icon {
  display: block;
  font-size: 1.6rem;
  margin-bottom: 4px;
}
#wn-app .wn-section-label {
  font-size: 0.78rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #888;
  margin-bottom: 10px;
}
#wn-app .wn-volume-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}
#wn-app .wn-volume-icon {
  font-size: 1.2rem;
  width: 24px;
  text-align: center;
  flex-shrink: 0;
}
#wn-app input[type="range"] {
  flex: 1;
  -webkit-appearance: none;
  appearance: none;
  height: 6px;
  border-radius: 3px;
  background: linear-gradient(to right, #6c63ff 0%, #6c63ff var(--vol-pct, 70%), #d0d6f0 var(--vol-pct, 70%), #d0d6f0 100%);
  outline: none;
  cursor: pointer;
}
#wn-app input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #6c63ff;
  box-shadow: 0 2px 6px rgba(108,99,255,0.4);
  cursor: pointer;
  transition: transform 0.15s;
}
#wn-app input[type="range"]::-webkit-slider-thumb:hover {
  transform: scale(1.15);
}
#wn-app .wn-vol-label {
  font-size: 0.85rem;
  font-weight: 700;
  color: #6c63ff;
  width: 36px;
  text-align: right;
  flex-shrink: 0;
}
#wn-app .wn-timer-row {
  display: flex;
  gap: 8px;
  margin-bottom: 28px;
  flex-wrap: wrap;
}
#wn-app .wn-timer-btn {
  padding: 8px 16px;
  border: 2px solid #d0d6f0;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 0.82rem;
  font-weight: 600;
  color: #666;
  transition: all 0.2s;
}
#wn-app .wn-timer-btn:hover {
  border-color: #6c63ff;
  color: #6c63ff;
}
#wn-app .wn-timer-btn.active {
  border-color: #6c63ff;
  background: #eeecff;
  color: #6c63ff;
}
#wn-app .wn-play-btn {
  display: block;
  width: 100%;
  padding: 18px;
  border: none;
  border-radius: 14px;
  background: linear-gradient(135deg, #6c63ff, #a78bfa);
  color: #fff;
  font-size: 1.1rem;
  font-weight: 700;
  cursor: pointer;
  letter-spacing: 0.02em;
  box-shadow: 0 4px 16px rgba(108,99,255,0.35);
  transition: all 0.2s;
}
#wn-app .wn-play-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 22px rgba(108,99,255,0.45);
}
#wn-app .wn-play-btn:active {
  transform: translateY(0);
}
#wn-app .wn-play-btn.playing {
  background: linear-gradient(135deg, #e53e3e, #fc8181);
  box-shadow: 0 4px 16px rgba(229,62,62,0.35);
}
#wn-app .wn-canvas-wrap {
  margin-bottom: 20px;
  border-radius: 12px;
  overflow: hidden;
  background: #1a1a2e;
}
#wn-app canvas {
  display: block;
  width: 100%;
  height: 80px;
}
#wn-app .wn-status {
  text-align: center;
  font-size: 0.88rem;
  color: #888;
  min-height: 1.4em;
  margin-top: 14px;
}
#wn-app .wn-status.active {
  color: #6c63ff;
  font-weight: 600;
}
#wn-app .wn-info {
  background: #fff;
  border: 1px solid #e0e4f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
}
#wn-app .wn-info h3 {
  font-size: 1rem;
  margin: 0 0 10px;
  color: #333;
}
#wn-app .wn-info p {
  font-size: 0.85rem;
  color: #555;
  margin: 0 0 8px;
  line-height: 1.6;
}
#wn-app .wn-info p:last-child { margin-bottom: 0; }
#wn-app .wn-related {
  background: #f0eeff;
  border-radius: 12px;
  padding: 18px 20px;
}
#wn-app .wn-related h3 {
  font-size: 0.9rem;
  font-weight: 700;
  color: #6c63ff;
  margin: 0 0 10px;
}
#wn-app .wn-related ul {
  margin: 0;
  padding: 0 0 0 18px;
}
#wn-app .wn-related li {
  font-size: 0.85rem;
  margin-bottom: 6px;
  color: #444;
}
#wn-app .wn-related a {
  color: #6c63ff;
  text-decoration: none;
  font-weight: 600;
}
#wn-app .wn-related a:hover { text-decoration: underline; }
</style>

<h2>White Noise Generator</h2>
<p class="wn-subtitle">Generate ambient sounds to boost focus, mask distractions, and improve sleep — all in your browser. No downloads needed.</p>

<div class="wn-card">
  <div class="wn-section-label">Noise Type</div>
  <div class="wn-noise-types">
    <button class="wn-noise-btn active" data-type="white" onclick="wnSelectType('white')">
      <span class="wn-icon">🌫</span>White
    </button>
    <button class="wn-noise-btn" data-type="pink" onclick="wnSelectType('pink')">
      <span class="wn-icon">🌸</span>Pink
    </button>
    <button class="wn-noise-btn" data-type="brown" onclick="wnSelectType('brown')">
      <span class="wn-icon">🌿</span>Brown
    </button>
  </div>

  <div class="wn-section-label">Volume</div>
  <div class="wn-volume-row">
    <span class="wn-volume-icon">🔈</span>
    <input type="range" id="wn-volume" min="0" max="100" value="70" oninput="wnSetVolume(this.value)">
    <span class="wn-vol-label" id="wn-vol-label">70%</span>
  </div>

  <div class="wn-section-label">Timer</div>
  <div class="wn-timer-row">
    <button class="wn-timer-btn active" data-min="0" onclick="wnSelectTimer(0)">Continuous</button>
    <button class="wn-timer-btn" data-min="15" onclick="wnSelectTimer(15)">15 min</button>
    <button class="wn-timer-btn" data-min="30" onclick="wnSelectTimer(30)">30 min</button>
    <button class="wn-timer-btn" data-min="60" onclick="wnSelectTimer(60)">60 min</button>
  </div>

  <div class="wn-canvas-wrap">
    <canvas id="wn-canvas" height="80"></canvas>
  </div>

  <button class="wn-play-btn" id="wn-play-btn" onclick="wnTogglePlay()">
    ▶ Start Playing
  </button>

  <div class="wn-status" id="wn-status">Select a noise type and press play</div>
</div>

<div class="wn-info">
  <h3>Which noise type should I choose?</h3>
  <p><strong>White Noise</strong> — Equal energy at all frequencies. Best for blocking office chatter, AC hum, or general distractions. Great for concentration tasks.</p>
  <p><strong>Pink Noise</strong> — Energy decreases with frequency (1/f). Sounds more natural and balanced. Research suggests it may improve memory consolidation during sleep.</p>
  <p><strong>Brown Noise</strong> — Heavier bass, similar to distant thunder or ocean surf. Many people find it deeply relaxing and ideal for sleep or meditation.</p>
</div>

<div class="wn-related">
  <h3>Related Free Tools</h3>
  <ul>
    <li><a href="/tools/pomodoro-timer/">Pomodoro Timer</a> — Pair focused work sessions with white noise</li>
    <li><a href="/tools/time-blocking-planner/">Time Blocking Planner</a> — Schedule deep-work blocks</li>
    <li><a href="/tools/distraction-blocker/">Focus Session Tracker</a> — Track distraction-free streaks</li>
  </ul>
</div>

<script>
(function() {
  var wnCtx = null;
  var wnSource = null;
  var wnGain = null;
  var wnPlaying = false;
  var wnType = 'white';
  var wnVolume = 0.7;
  var wnTimerMin = 0;
  var wnTimerTimeout = null;
  var wnAnimFrame = null;
  var wnAnalyser = null;
  var wnDataArr = null;

  var canvas = document.getElementById('wn-canvas');
  var canvasCtx = canvas.getContext('2d');
  canvas.width = canvas.offsetWidth || 600;

  function wnCreateBuffer(audioCtx, type) {
    var bufferSize = audioCtx.sampleRate * 2;
    var buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
    var data = buffer.getChannelData(0);
    if (type === 'white') {
      for (var i = 0; i < bufferSize; i++) {
        data[i] = Math.random() * 2 - 1;
      }
    } else if (type === 'pink') {
      var b0=0,b1=0,b2=0,b3=0,b4=0,b5=0,b6=0;
      for (var i = 0; i < bufferSize; i++) {
        var white = Math.random() * 2 - 1;
        b0 = 0.99886*b0 + white*0.0555179;
        b1 = 0.99332*b1 + white*0.0750759;
        b2 = 0.96900*b2 + white*0.1538520;
        b3 = 0.86650*b3 + white*0.3104856;
        b4 = 0.55000*b4 + white*0.5329522;
        b5 = -0.7616*b5 - white*0.0168980;
        data[i] = (b0+b1+b2+b3+b4+b5+b6 + white*0.5362) / 6;
        b6 = white * 0.115926;
      }
    } else if (type === 'brown') {
      var last = 0;
      for (var i = 0; i < bufferSize; i++) {
        var white = Math.random() * 2 - 1;
        data[i] = (last + 0.02 * white) / 1.02;
        last = data[i];
        data[i] *= 3.5;
      }
    }
    return buffer;
  }

  function wnStart() {
    wnCtx = new (window.AudioContext || window.webkitAudioContext)();
    wnAnalyser = wnCtx.createAnalyser();
    wnAnalyser.fftSize = 256;
    wnDataArr = new Uint8Array(wnAnalyser.frequencyBinCount);

    wnGain = wnCtx.createGain();
    wnGain.gain.value = wnVolume;

    var buffer = wnCreateBuffer(wnCtx, wnType);
    wnSource = wnCtx.createBufferSource();
    wnSource.buffer = buffer;
    wnSource.loop = true;
    wnSource.connect(wnGain);
    wnGain.connect(wnAnalyser);
    wnAnalyser.connect(wnCtx.destination);
    wnSource.start();

    wnPlaying = true;
    wnDrawWaveform();

    var btn = document.getElementById('wn-play-btn');
    btn.textContent = '\u23F9 Stop';
    btn.classList.add('playing');
    wnUpdateStatus();

    if (wnTimerMin > 0) {
      wnTimerTimeout = setTimeout(function() {
        wnStop();
        document.getElementById('wn-status').textContent = 'Timer ended. Great session!';
      }, wnTimerMin * 60 * 1000);
    }
  }

  function wnStop() {
    if (wnSource) { try { wnSource.stop(); } catch(e){} wnSource = null; }
    if (wnCtx) { wnCtx.close(); wnCtx = null; }
    if (wnTimerTimeout) { clearTimeout(wnTimerTimeout); wnTimerTimeout = null; }
    if (wnAnimFrame) { cancelAnimationFrame(wnAnimFrame); wnAnimFrame = null; }
    wnPlaying = false;
    wnGain = null;
    wnAnalyser = null;

    var btn = document.getElementById('wn-play-btn');
    btn.textContent = '\u25B6 Start Playing';
    btn.classList.remove('playing');
    document.getElementById('wn-status').textContent = 'Stopped';
    document.getElementById('wn-status').classList.remove('active');
    wnClearCanvas();
  }

  function wnClearCanvas() {
    var w = canvas.width, h = canvas.height;
    canvasCtx.fillStyle = '#1a1a2e';
    canvasCtx.fillRect(0, 0, w, h);
    canvasCtx.strokeStyle = 'rgba(108,99,255,0.2)';
    canvasCtx.lineWidth = 1;
    canvasCtx.beginPath();
    canvasCtx.moveTo(0, h/2);
    canvasCtx.lineTo(w, h/2);
    canvasCtx.stroke();
  }

  function wnDrawWaveform() {
    if (!wnPlaying || !wnAnalyser) return;
    wnAnimFrame = requestAnimationFrame(wnDrawWaveform);
    wnAnalyser.getByteTimeDomainData(wnDataArr);

    var w = canvas.width, h = canvas.height;
    canvasCtx.fillStyle = '#1a1a2e';
    canvasCtx.fillRect(0, 0, w, h);

    var grad = canvasCtx.createLinearGradient(0, 0, w, 0);
    if (wnType === 'white') {
      grad.addColorStop(0, '#a5b4fc');
      grad.addColorStop(0.5, '#818cf8');
      grad.addColorStop(1, '#6c63ff');
    } else if (wnType === 'pink') {
      grad.addColorStop(0, '#f9a8d4');
      grad.addColorStop(0.5, '#f472b6');
      grad.addColorStop(1, '#ec4899');
    } else {
      grad.addColorStop(0, '#6ee7b7');
      grad.addColorStop(0.5, '#34d399');
      grad.addColorStop(1, '#059669');
    }

    canvasCtx.lineWidth = 2.5;
    canvasCtx.strokeStyle = grad;
    canvasCtx.beginPath();

    var sliceWidth = w / wnDataArr.length;
    var x = 0;
    for (var i = 0; i < wnDataArr.length; i++) {
      var v = wnDataArr[i] / 128.0;
      var y = v * h / 2;
      if (i === 0) canvasCtx.moveTo(x, y);
      else canvasCtx.lineTo(x, y);
      x += sliceWidth;
    }
    canvasCtx.lineTo(w, h/2);
    canvasCtx.stroke();

    // glow
    canvasCtx.lineWidth = 6;
    canvasCtx.globalAlpha = 0.18;
    canvasCtx.strokeStyle = grad;
    canvasCtx.stroke();
    canvasCtx.globalAlpha = 1;
  }

  function wnUpdateStatus() {
    var el = document.getElementById('wn-status');
    var label = wnType.charAt(0).toUpperCase() + wnType.slice(1);
    var timer = wnTimerMin > 0 ? ' | Timer: ' + wnTimerMin + ' min' : ' | Continuous';
    el.textContent = 'Playing ' + label + ' Noise' + timer;
    el.classList.add('active');
  }

  window.wnTogglePlay = function() {
    if (wnPlaying) wnStop();
    else wnStart();
  };

  window.wnSelectType = function(type) {
    wnType = type;
    document.querySelectorAll('#wn-app .wn-noise-btn').forEach(function(b) {
      b.classList.toggle('active', b.dataset.type === type);
    });
    if (wnPlaying) { wnStop(); wnStart(); }
  };

  window.wnSetVolume = function(val) {
    wnVolume = val / 100;
    document.getElementById('wn-vol-label').textContent = val + '%';
    document.getElementById('wn-volume').style.setProperty('--vol-pct', val + '%');
    if (wnGain) wnGain.gain.setTargetAtTime(wnVolume, wnCtx.currentTime, 0.01);
  };

  window.wnSelectTimer = function(min) {
    wnTimerMin = min;
    document.querySelectorAll('#wn-app .wn-timer-btn').forEach(function(b) {
      b.classList.toggle('active', parseInt(b.dataset.min) === min);
    });
    if (wnPlaying) wnUpdateStatus();
  };

  // init canvas
  wnClearCanvas();

  // set initial volume gradient
  document.getElementById('wn-volume').style.setProperty('--vol-pct', '70%');
})();
</script>

</div>
