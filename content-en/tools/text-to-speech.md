---
title: "Text to Speech"
date: 2025-05-16
description: "Free online text-to-speech tool. Convert text to audio using your browser's built-in voices. Adjust speed, pitch, and volume. No sign-up required."
categories: ["Free Tools"]
slug: "text-to-speech"
ShowToc: false
cover:
  image: "/images/covers/text-to-speech.png"
  alt: "Text to Speech"
---

<div id="ts-app">

<style>
#ts-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  color: #1a1a2e;
}
#ts-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 0.6rem 0;
  color: #1e293b;
}
#ts-app .ts-card {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
#ts-app textarea#ts-text {
  width: 100%;
  min-height: 160px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  font-size: 1rem;
  font-family: inherit;
  resize: vertical;
  box-sizing: border-box;
  transition: border-color 0.2s;
  line-height: 1.65;
  color: #1a1a2e;
  background: #f8fafc;
}
#ts-app textarea#ts-text:focus {
  outline: none;
  border-color: #6366f1;
  background: #fff;
}
#ts-app .ts-meta-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.4rem;
  font-size: 0.82rem;
  color: #64748b;
}
#ts-app .ts-controls-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 560px) {
  #ts-app .ts-controls-grid { grid-template-columns: 1fr; }
}
#ts-app label.ts-label {
  display: block;
  font-size: 0.78rem;
  font-weight: 700;
  color: #475569;
  margin-bottom: 0.3rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
#ts-app select.ts-select {
  width: 100%;
  padding: 0.5rem 2rem 0.5rem 0.75rem;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 0.92rem;
  font-family: inherit;
  background: #f8fafc;
  color: #1a1a2e;
  cursor: pointer;
  appearance: none;
  -webkit-appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2364748b' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 0.75rem center;
}
#ts-app select.ts-select:focus {
  outline: none;
  border-color: #6366f1;
}
#ts-app .ts-slider-wrap {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}
#ts-app .ts-slider-row {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}
#ts-app input[type="range"].ts-slider {
  flex: 1;
  -webkit-appearance: none;
  appearance: none;
  height: 4px;
  border-radius: 2px;
  background: #e2e8f0;
  cursor: pointer;
}
#ts-app input[type="range"].ts-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 17px;
  height: 17px;
  border-radius: 50%;
  background: #6366f1;
  cursor: pointer;
  box-shadow: 0 1px 4px rgba(99,102,241,0.45);
}
#ts-app input[type="range"].ts-slider::-moz-range-thumb {
  width: 17px;
  height: 17px;
  border-radius: 50%;
  background: #6366f1;
  border: none;
  cursor: pointer;
}
#ts-app .ts-slider-val {
  font-size: 0.82rem;
  font-weight: 700;
  color: #6366f1;
  min-width: 3rem;
  text-align: right;
}
#ts-app .ts-btn-row {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  align-items: center;
}
#ts-app button.ts-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.6rem 1.4rem;
  border: none;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 700;
  font-family: inherit;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s, opacity 0.15s;
  white-space: nowrap;
}
#ts-app button.ts-btn:active { transform: scale(0.96); }
#ts-app button.ts-btn:disabled { opacity: 0.4; cursor: not-allowed; }
#ts-app button#ts-play   { background: #6366f1; color: #fff; }
#ts-app button#ts-play:hover:not(:disabled)   { background: #4f46e5; }
#ts-app button#ts-pause  { background: #f59e0b; color: #fff; }
#ts-app button#ts-pause:hover:not(:disabled)  { background: #d97706; }
#ts-app button#ts-stop   { background: #ef4444; color: #fff; }
#ts-app button#ts-stop:hover:not(:disabled)   { background: #dc2626; }
#ts-app .ts-status-bar {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.88rem;
  color: #64748b;
  padding: 0.55rem 0 0;
}
#ts-app .ts-dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  background: #cbd5e1;
  flex-shrink: 0;
  transition: background 0.2s;
}
#ts-app .ts-dot.playing { background: #22c55e; animation: ts-pulse 1s infinite; }
#ts-app .ts-dot.paused  { background: #f59e0b; }
#ts-app .ts-dot.stopped { background: #ef4444; }
@keyframes ts-pulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.35; }
}
#ts-app .ts-highlight-box {
  background: #f0f4ff;
  border-left: 3px solid #6366f1;
  border-radius: 0 8px 8px 0;
  padding: 0.7rem 1rem;
  font-size: 0.9rem;
  color: #3730a3;
  min-height: 2.6rem;
  line-height: 1.65;
  word-break: break-word;
  overflow-y: auto;
  max-height: 180px;
}
#ts-app .ts-highlight-box .ts-word-current {
  background: #6366f1;
  color: #fff;
  border-radius: 3px;
  padding: 1px 4px;
}
#ts-app .ts-no-support {
  background: #fef9c3;
  border: 1px solid #fde047;
  border-radius: 8px;
  padding: 1rem 1.25rem;
  font-size: 0.9rem;
  color: #713f12;
  margin-bottom: 1rem;
}
</style>

<!-- Text input -->
<div class="ts-card">
  <h2>Enter Your Text</h2>
  <textarea id="ts-text" placeholder="Paste or type any text here and press Play to hear it read aloud...">The Web Speech API lets browsers convert text to speech entirely on-device, with no data sent to any server. Try adjusting the voice, speed, pitch, and volume below to find the combination that works best for you.</textarea>
  <div class="ts-meta-row">
    <span id="ts-char-count">0 characters</span>
    <span id="ts-read-time">~0 min read</span>
  </div>
</div>

<!-- Voice selector -->
<div class="ts-card">
  <h2>Voice &amp; Language</h2>
  <div class="ts-controls-grid">
    <div>
      <label class="ts-label" for="ts-lang-filter">Filter by Language</label>
      <select class="ts-select" id="ts-lang-filter">
        <option value="">All Languages</option>
      </select>
    </div>
    <div>
      <label class="ts-label" for="ts-voice">Voice</label>
      <select class="ts-select" id="ts-voice">
        <option value="">Loading voices&hellip;</option>
      </select>
    </div>
  </div>
</div>

<!-- Playback settings -->
<div class="ts-card">
  <h2>Playback Settings</h2>
  <div class="ts-controls-grid">
    <div class="ts-slider-wrap">
      <label class="ts-label" for="ts-rate">Speed</label>
      <div class="ts-slider-row">
        <input type="range" class="ts-slider" id="ts-rate" min="0.5" max="2" step="0.05" value="1">
        <span class="ts-slider-val" id="ts-rate-val">1.00x</span>
      </div>
    </div>
    <div class="ts-slider-wrap">
      <label class="ts-label" for="ts-pitch">Pitch</label>
      <div class="ts-slider-row">
        <input type="range" class="ts-slider" id="ts-pitch" min="0.5" max="2" step="0.05" value="1">
        <span class="ts-slider-val" id="ts-pitch-val">1.00</span>
      </div>
    </div>
    <div class="ts-slider-wrap">
      <label class="ts-label" for="ts-volume">Volume</label>
      <div class="ts-slider-row">
        <input type="range" class="ts-slider" id="ts-volume" min="0" max="1" step="0.01" value="1">
        <span class="ts-slider-val" id="ts-volume-val">100%</span>
      </div>
    </div>
  </div>
</div>

<!-- Controls -->
<div class="ts-card">
  <div class="ts-btn-row">
    <button class="ts-btn" id="ts-play">&#9654; Play</button>
    <button class="ts-btn" id="ts-pause" disabled>&#9646;&#9646; Pause</button>
    <button class="ts-btn" id="ts-stop" disabled>&#9632; Stop</button>
  </div>
  <div class="ts-status-bar">
    <div class="ts-dot" id="ts-dot"></div>
    <span id="ts-status-text">Ready</span>
  </div>
</div>

<!-- Word highlight -->
<div class="ts-card">
  <h2>Current Word</h2>
  <div class="ts-highlight-box" id="ts-highlight-box">
    <span style="color:#94a3b8;">Spoken words will appear highlighted here during playback.</span>
  </div>
</div>

<!-- No support notice -->
<div id="ts-no-support" class="ts-no-support" style="display:none;">
  Your browser does not support the Web Speech API. Please use a modern browser such as Chrome, Edge, or Safari.
</div>

<script>
(function () {
  'use strict';

  if (!('speechSynthesis' in window)) {
    document.getElementById('ts-no-support').style.display = 'block';
    ['ts-play','ts-pause','ts-stop'].forEach(function(id){
      var el = document.getElementById(id);
      if (el) el.disabled = true;
    });
    return;
  }

  var synth   = window.speechSynthesis;
  var allVoices = [];
  var currentUtt = null;
  var tsState = 'stopped'; // 'stopped' | 'playing' | 'paused'

  var elText      = document.getElementById('ts-text');
  var elLangFilter= document.getElementById('ts-lang-filter');
  var elVoice     = document.getElementById('ts-voice');
  var elRate      = document.getElementById('ts-rate');
  var elPitch     = document.getElementById('ts-pitch');
  var elVolume    = document.getElementById('ts-volume');
  var elRateVal   = document.getElementById('ts-rate-val');
  var elPitchVal  = document.getElementById('ts-pitch-val');
  var elVolVal    = document.getElementById('ts-volume-val');
  var elPlay      = document.getElementById('ts-play');
  var elPause     = document.getElementById('ts-pause');
  var elStop      = document.getElementById('ts-stop');
  var elDot       = document.getElementById('ts-dot');
  var elStatus    = document.getElementById('ts-status-text');
  var elHighlight = document.getElementById('ts-highlight-box');
  var elCharCount = document.getElementById('ts-char-count');
  var elReadTime  = document.getElementById('ts-read-time');

  // --- Character / read-time counters ---
  function updateMeta() {
    var txt   = elText.value;
    var chars = txt.length;
    elCharCount.textContent = chars.toLocaleString() + ' character' + (chars === 1 ? '' : 's');
    var words = txt.trim() === '' ? 0 : txt.trim().split(/\s+/).length;
    var mins  = Math.max(1, Math.ceil(words / 200));
    elReadTime.textContent = '~' + mins + ' min read';
  }
  elText.addEventListener('input', updateMeta);
  updateMeta();

  // --- Slider display ---
  elRate.addEventListener('input', function () {
    elRateVal.textContent = parseFloat(elRate.value).toFixed(2) + 'x';
  });
  elPitch.addEventListener('input', function () {
    elPitchVal.textContent = parseFloat(elPitch.value).toFixed(2);
  });
  elVolume.addEventListener('input', function () {
    elVolVal.textContent = Math.round(parseFloat(elVolume.value) * 100) + '%';
  });

  // --- Voice loading ---
  function populateLangFilter(voices) {
    var langs = [];
    voices.forEach(function (v) {
      if (langs.indexOf(v.lang) === -1) langs.push(v.lang);
    });
    langs.sort();
    elLangFilter.innerHTML = '<option value="">All Languages</option>';
    langs.forEach(function (l) {
      var opt = document.createElement('option');
      opt.value = l;
      opt.textContent = l;
      elLangFilter.appendChild(opt);
    });
  }

  function populateVoices(filterLang) {
    var voices = filterLang
      ? allVoices.filter(function (v) { return v.lang === filterLang; })
      : allVoices;
    elVoice.innerHTML = '';
    if (voices.length === 0) {
      elVoice.innerHTML = '<option value="">No voices for this language</option>';
      return;
    }
    voices.forEach(function (v) {
      var opt = document.createElement('option');
      opt.value = v.name;
      opt.textContent = v.name + ' (' + v.lang + ')' + (v.default ? ' \u2605' : '');
      elVoice.appendChild(opt);
    });
  }

  function loadVoices() {
    var voices = synth.getVoices();
    if (voices.length === 0) return;
    allVoices = voices;
    populateLangFilter(voices);
    populateVoices(elLangFilter.value);
  }

  synth.onvoiceschanged = loadVoices;
  loadVoices();
  setTimeout(loadVoices, 600);

  elLangFilter.addEventListener('change', function () {
    populateVoices(elLangFilter.value);
  });

  // --- UI state ---
  function setUIState(state) {
    tsState = state;
    elDot.className = 'ts-dot ' + state;
    if (state === 'playing') {
      elStatus.textContent    = 'Playing\u2026';
      elPlay.disabled         = true;
      elPause.disabled        = false;
      elStop.disabled         = false;
      elPause.innerHTML       = '\u23ae\u23ae Pause';
    } else if (state === 'paused') {
      elStatus.textContent    = 'Paused';
      elPlay.disabled         = true;
      elPause.disabled        = false;
      elStop.disabled         = false;
      elPause.innerHTML       = '\u25b6 Resume';
    } else {
      elStatus.textContent    = 'Ready';
      elPlay.disabled         = false;
      elPause.disabled        = true;
      elStop.disabled         = true;
      elPause.innerHTML       = '\u23ae\u23ae Pause';
      elHighlight.innerHTML   = '<span style="color:#94a3b8;">Spoken words will appear highlighted here during playback.</span>';
    }
  }

  // --- Word highlighting ---
  function escHtml(str) {
    return str
      .replace(/&/g, '&amp;')
      .replace(/</g, '&lt;')
      .replace(/>/g, '&gt;');
  }

  function highlightWord(charIndex, charLength) {
    var full   = elText.value;
    var before = full.substring(0, charIndex);
    var word   = full.substring(charIndex, charIndex + charLength);
    var after  = full.substring(charIndex + charLength);
    elHighlight.innerHTML =
      escHtml(before) +
      '<span class="ts-word-current">' + escHtml(word) + '</span>' +
      escHtml(after);
    var span = elHighlight.querySelector('.ts-word-current');
    if (span) span.scrollIntoView({ block: 'nearest', behavior: 'smooth' });
  }

  // --- Play ---
  elPlay.addEventListener('click', function () {
    var text = elText.value.trim();
    if (!text) {
      elStatus.textContent = 'Please enter some text first.';
      return;
    }

    synth.cancel();
    currentUtt = new SpeechSynthesisUtterance(text);

    var selectedName = elVoice.value;
    var voice = allVoices.find(function (v) { return v.name === selectedName; });
    if (voice) currentUtt.voice = voice;

    currentUtt.rate   = parseFloat(elRate.value);
    currentUtt.pitch  = parseFloat(elPitch.value);
    currentUtt.volume = parseFloat(elVolume.value);

    currentUtt.onstart = function ()  { setUIState('playing'); };
    currentUtt.onend   = function ()  { setUIState('stopped'); };
    currentUtt.onerror = function (e) {
      if (e.error !== 'interrupted') {
        elStatus.textContent = 'Error: ' + e.error;
        setUIState('stopped');
      }
    };
    currentUtt.onboundary = function (e) {
      if (e.name === 'word') {
        highlightWord(e.charIndex, e.charLength || 1);
      }
    };

    synth.speak(currentUtt);
    setUIState('playing');
  });

  // --- Pause / Resume ---
  elPause.addEventListener('click', function () {
    if (tsState === 'playing') {
      synth.pause();
      setUIState('paused');
    } else if (tsState === 'paused') {
      synth.resume();
      setUIState('playing');
    }
  });

  // --- Stop ---
  elStop.addEventListener('click', function () {
    synth.cancel();
    setUIState('stopped');
  });

  // Init
  setUIState('stopped');
}());
</script>

</div>

---

## How to Use

1. **Paste or type** your text into the text area above.
2. **Choose a voice** — use the language filter to narrow down voices available in your browser.
3. **Adjust speed, pitch, and volume** using the sliders (speed: 0.5x–2x).
4. **Press Play** and watch the current word highlight in real time.
5. **Pause** to temporarily stop, or **Stop** to cancel playback entirely.

## About This Tool

This tool uses your browser's built-in **Web Speech API** (`speechSynthesis`). No audio is sent to any server — everything happens locally on your device. Available voices depend on your operating system and browser.

**Browser support:** Chrome, Edge, Safari, and most modern browsers. Firefox has limited voice selection on some platforms.

> Count characters → [Character Counter](/tools/character-counter/)

> Translate Morse → [Morse Code Translator](/tools/morse-code/)
