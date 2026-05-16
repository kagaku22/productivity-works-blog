---
title: "Text to Speech"
slug: "text-to-speech"
date: 2025-05-16
description: "Free text to speech tool. Listen to any text read aloud using your browser's built-in speech synthesis — choose voice, speed, pitch, and language."
categories: ["Free Tools"]
ShowToc: false
cover:
  image: "/images/covers/text-to-speech.png"
  alt: "Text to Speech tool — browser-based speech synthesis with voice, speed, and pitch controls"
---

<div id="sp-app">

<style>
#sp-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
}
#sp-app h2 {
  font-size: 1.15rem;
  font-weight: 600;
  margin: 0 0 0.5rem 0;
  color: #1a1a2e;
}
#sp-app .sp-card {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
#sp-app textarea#sp-text {
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
  line-height: 1.6;
  color: #1a1a2e;
  background: #f8fafc;
}
#sp-app textarea#sp-text:focus {
  outline: none;
  border-color: #6366f1;
  background: #fff;
}
#sp-app .sp-meta-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.45rem;
  font-size: 0.82rem;
  color: #64748b;
}
#sp-app .sp-controls-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 560px) {
  #sp-app .sp-controls-grid { grid-template-columns: 1fr; }
}
#sp-app label.sp-label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: #475569;
  margin-bottom: 0.3rem;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#sp-app select.sp-select {
  width: 100%;
  padding: 0.5rem 0.75rem;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 0.92rem;
  font-family: inherit;
  background: #f8fafc;
  color: #1a1a2e;
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2364748b' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 0.75rem center;
  padding-right: 2rem;
}
#sp-app select.sp-select:focus {
  outline: none;
  border-color: #6366f1;
}
#sp-app .sp-slider-wrap {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}
#sp-app .sp-slider-row {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}
#sp-app input[type="range"].sp-slider {
  flex: 1;
  -webkit-appearance: none;
  height: 4px;
  border-radius: 2px;
  background: #e2e8f0;
  cursor: pointer;
}
#sp-app input[type="range"].sp-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #6366f1;
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(99,102,241,0.4);
}
#sp-app input[type="range"].sp-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #6366f1;
  border: none;
  cursor: pointer;
}
#sp-app .sp-slider-val {
  font-size: 0.82rem;
  font-weight: 600;
  color: #6366f1;
  min-width: 2.5rem;
  text-align: right;
}
#sp-app .sp-btn-row {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}
#sp-app button.sp-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.6rem 1.4rem;
  border: none;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 600;
  font-family: inherit;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s, opacity 0.15s;
}
#sp-app button.sp-btn:active { transform: scale(0.97); }
#sp-app button.sp-btn:disabled { opacity: 0.45; cursor: not-allowed; }
#sp-app button#sp-play  { background: #6366f1; color: #fff; }
#sp-app button#sp-play:hover:not(:disabled)  { background: #4f46e5; }
#sp-app button#sp-pause { background: #f59e0b; color: #fff; }
#sp-app button#sp-pause:hover:not(:disabled) { background: #d97706; }
#sp-app button#sp-stop  { background: #ef4444; color: #fff; }
#sp-app button#sp-stop:hover:not(:disabled)  { background: #dc2626; }
#sp-app .sp-status-bar {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.88rem;
  color: #64748b;
  padding: 0.5rem 0 0;
}
#sp-app .sp-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #cbd5e1;
  flex-shrink: 0;
  transition: background 0.2s;
}
#sp-app .sp-dot.playing { background: #22c55e; animation: sp-pulse 1s infinite; }
#sp-app .sp-dot.paused  { background: #f59e0b; }
#sp-app .sp-dot.stopped { background: #ef4444; }
@keyframes sp-pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.4; }
}
#sp-app .sp-highlight-box {
  background: #f0f4ff;
  border-left: 3px solid #6366f1;
  border-radius: 0 8px 8px 0;
  padding: 0.65rem 1rem;
  font-size: 0.9rem;
  color: #3730a3;
  min-height: 2.4rem;
  line-height: 1.5;
  word-break: break-word;
}
#sp-app .sp-highlight-box .sp-word-current {
  background: #6366f1;
  color: #fff;
  border-radius: 3px;
  padding: 0 3px;
}
#sp-app .sp-no-support {
  background: #fef9c3;
  border: 1px solid #fde047;
  border-radius: 8px;
  padding: 1rem 1.25rem;
  font-size: 0.9rem;
  color: #713f12;
}
</style>

<div class="sp-card">
  <h2>Enter Your Text</h2>
  <textarea id="sp-text" placeholder="Paste or type any text here and press Play to hear it read aloud...">The Web Speech API lets browsers convert text to speech entirely on-device, with no data sent to any server. Try adjusting the voice, speed, and pitch below to find the combination that works best for you.</textarea>
  <div class="sp-meta-row">
    <span id="sp-char-count">0 characters</span>
    <span id="sp-read-time">~0 min read</span>
  </div>
</div>

<div class="sp-card">
  <h2>Voice &amp; Language</h2>
  <div class="sp-controls-grid">
    <div>
      <label class="sp-label" for="sp-lang-filter">Filter by Language</label>
      <select class="sp-select" id="sp-lang-filter">
        <option value="">All Languages</option>
      </select>
    </div>
    <div>
      <label class="sp-label" for="sp-voice">Voice</label>
      <select class="sp-select" id="sp-voice">
        <option value="">Loading voices…</option>
      </select>
    </div>
  </div>
</div>

<div class="sp-card">
  <h2>Playback Settings</h2>
  <div class="sp-controls-grid">
    <div class="sp-slider-wrap">
      <label class="sp-label" for="sp-rate">Speed</label>
      <div class="sp-slider-row">
        <input type="range" class="sp-slider" id="sp-rate" min="0.5" max="2" step="0.05" value="1">
        <span class="sp-slider-val" id="sp-rate-val">1.00x</span>
      </div>
    </div>
    <div class="sp-slider-wrap">
      <label class="sp-label" for="sp-pitch">Pitch</label>
      <div class="sp-slider-row">
        <input type="range" class="sp-slider" id="sp-pitch" min="0.5" max="2" step="0.05" value="1">
        <span class="sp-slider-val" id="sp-pitch-val">1.00</span>
      </div>
    </div>
    <div class="sp-slider-wrap">
      <label class="sp-label" for="sp-volume">Volume</label>
      <div class="sp-slider-row">
        <input type="range" class="sp-slider" id="sp-volume" min="0" max="1" step="0.01" value="1">
        <span class="sp-slider-val" id="sp-volume-val">100%</span>
      </div>
    </div>
  </div>
</div>

<div class="sp-card">
  <div class="sp-btn-row">
    <button class="sp-btn" id="sp-play">&#9654; Play</button>
    <button class="sp-btn" id="sp-pause" disabled>&#9646;&#9646; Pause</button>
    <button class="sp-btn" id="sp-stop" disabled>&#9632; Stop</button>
  </div>
  <div class="sp-status-bar">
    <div class="sp-dot" id="sp-dot"></div>
    <span id="sp-status-text">Ready</span>
  </div>
</div>

<div class="sp-card">
  <h2>Current Word</h2>
  <div class="sp-highlight-box" id="sp-highlight-box">
    <span style="color:#94a3b8;">Spoken words will appear highlighted here during playback.</span>
  </div>
</div>

<div id="sp-no-support" class="sp-no-support" style="display:none;">
  Your browser does not support the Web Speech API. Please use a modern browser such as Chrome, Edge, or Safari.
</div>

<script>
(function () {
  'use strict';

  if (!('speechSynthesis' in window)) {
    document.getElementById('sp-no-support').style.display = 'block';
    ['sp-play','sp-pause','sp-stop'].forEach(function(id){ document.getElementById(id).disabled = true; });
    return;
  }

  var synth = window.speechSynthesis;
  var allVoices = [];
  var currentUtterance = null;
  var spState = 'stopped'; // 'stopped' | 'playing' | 'paused'

  var elText     = document.getElementById('sp-text');
  var elLangFilter = document.getElementById('sp-lang-filter');
  var elVoice    = document.getElementById('sp-voice');
  var elRate     = document.getElementById('sp-rate');
  var elPitch    = document.getElementById('sp-pitch');
  var elVolume   = document.getElementById('sp-volume');
  var elRateVal  = document.getElementById('sp-rate-val');
  var elPitchVal = document.getElementById('sp-pitch-val');
  var elVolVal   = document.getElementById('sp-volume-val');
  var elPlay     = document.getElementById('sp-play');
  var elPause    = document.getElementById('sp-pause');
  var elStop     = document.getElementById('sp-stop');
  var elDot      = document.getElementById('sp-dot');
  var elStatus   = document.getElementById('sp-status-text');
  var elHighlight= document.getElementById('sp-highlight-box');
  var elCharCount= document.getElementById('sp-char-count');
  var elReadTime = document.getElementById('sp-read-time');

  // --- Meta counters ---
  function updateMeta() {
    var txt = elText.value;
    var chars = txt.length;
    elCharCount.textContent = chars.toLocaleString() + ' character' + (chars === 1 ? '' : 's');
    var words = txt.trim() === '' ? 0 : txt.trim().split(/\s+/).length;
    var mins = Math.ceil(words / 200);
    elReadTime.textContent = '~' + mins + ' min read';
  }
  elText.addEventListener('input', updateMeta);
  updateMeta();

  // --- Slider display ---
  elRate.addEventListener('input', function() { elRateVal.textContent = parseFloat(elRate.value).toFixed(2) + 'x'; });
  elPitch.addEventListener('input', function() { elPitchVal.textContent = parseFloat(elPitch.value).toFixed(2); });
  elVolume.addEventListener('input', function() { elVolVal.textContent = Math.round(parseFloat(elVolume.value) * 100) + '%'; });

  // --- Voice loading ---
  function populateLangFilter(voices) {
    var langs = [];
    voices.forEach(function(v) {
      var code = v.lang;
      if (langs.indexOf(code) === -1) langs.push(code);
    });
    langs.sort();
    elLangFilter.innerHTML = '<option value="">All Languages</option>';
    langs.forEach(function(l) {
      var opt = document.createElement('option');
      opt.value = l;
      opt.textContent = l;
      elLangFilter.appendChild(opt);
    });
  }

  function populateVoices(filterLang) {
    var voices = filterLang
      ? allVoices.filter(function(v){ return v.lang === filterLang; })
      : allVoices;
    elVoice.innerHTML = '';
    if (voices.length === 0) {
      elVoice.innerHTML = '<option value="">No voices for this language</option>';
      return;
    }
    voices.forEach(function(v, i) {
      var opt = document.createElement('option');
      opt.value = v.name;
      opt.textContent = v.name + ' (' + v.lang + ')' + (v.default ? ' ★' : '');
      elVoice.appendChild(opt);
    });
  }

  function loadVoices() {
    var voices = synth.getVoices();
    if (voices.length === 0) return;
    allVoices = voices;
    populateLangFilter(voices);
    populateVoices('');
  }

  synth.onvoiceschanged = loadVoices;
  loadVoices();
  setTimeout(loadVoices, 500);

  elLangFilter.addEventListener('change', function() {
    populateVoices(elLangFilter.value);
  });

  // --- State UI ---
  function setUIState(state) {
    spState = state;
    elDot.className = 'sp-dot ' + state;
    if (state === 'playing') {
      elStatus.textContent = 'Playing…';
      elPlay.disabled  = true;
      elPause.disabled = false;
      elStop.disabled  = false;
      elPause.textContent = '\u23ae\u23ae Pause';
    } else if (state === 'paused') {
      elStatus.textContent = 'Paused';
      elPlay.disabled  = true;
      elPause.disabled = false;
      elStop.disabled  = false;
      elPause.textContent = '\u25b6 Resume';
    } else {
      elStatus.textContent = 'Ready';
      elPlay.disabled  = false;
      elPause.disabled = true;
      elStop.disabled  = true;
      elPause.textContent = '\u23ae\u23ae Pause';
      elHighlight.innerHTML = '<span style="color:#94a3b8;">Spoken words will appear highlighted here during playback.</span>';
    }
  }

  // --- Word highlighting ---
  var textWords = [];
  function buildWordList(text) {
    textWords = text.split(/(\s+)/);
  }

  function highlightWord(charIndex, charLength) {
    var fullText = elText.value;
    var before = fullText.substring(0, charIndex);
    var word   = fullText.substring(charIndex, charIndex + charLength);
    var after  = fullText.substring(charIndex + charLength);
    elHighlight.innerHTML =
      escHtml(before) +
      '<span class="sp-word-current">' + escHtml(word) + '</span>' +
      escHtml(after);
    // Scroll the highlight box to show current word
    var span = elHighlight.querySelector('.sp-word-current');
    if (span) span.scrollIntoView({ block: 'nearest', behavior: 'smooth' });
  }

  function escHtml(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  // --- Play ---
  elPlay.addEventListener('click', function() {
    var text = elText.value.trim();
    if (!text) { elStatus.textContent = 'Please enter some text first.'; return; }

    synth.cancel();
    currentUtterance = new SpeechSynthesisUtterance(text);

    var selectedVoiceName = elVoice.value;
    var voice = allVoices.find(function(v){ return v.name === selectedVoiceName; });
    if (voice) currentUtterance.voice = voice;

    currentUtterance.rate   = parseFloat(elRate.value);
    currentUtterance.pitch  = parseFloat(elPitch.value);
    currentUtterance.volume = parseFloat(elVolume.value);

    currentUtterance.onstart = function() { setUIState('playing'); };
    currentUtterance.onend   = function() { setUIState('stopped'); };
    currentUtterance.onerror = function(e) {
      if (e.error !== 'interrupted') {
        elStatus.textContent = 'Error: ' + e.error;
        setUIState('stopped');
      }
    };
    currentUtterance.onboundary = function(e) {
      if (e.name === 'word') {
        highlightWord(e.charIndex, e.charLength || 1);
      }
    };

    synth.speak(currentUtterance);
    setUIState('playing');
  });

  // --- Pause / Resume ---
  elPause.addEventListener('click', function() {
    if (spState === 'playing') {
      synth.pause();
      setUIState('paused');
    } else if (spState === 'paused') {
      synth.resume();
      setUIState('playing');
    }
  });

  // --- Stop ---
  elStop.addEventListener('click', function() {
    synth.cancel();
    setUIState('stopped');
  });

  // Init
  setUIState('stopped');
})();
</script>

</div>

---

## How to Use

1. **Paste or type** your text into the text area above.
2. **Choose a voice** — use the language filter to narrow down voices available in your browser.
3. **Adjust speed, pitch, and volume** using the sliders.
4. **Press Play** and watch the current word highlight in real time.
5. **Pause or Stop** at any time.

## About This Tool

This tool uses your browser's built-in **Web Speech API** (`SpeechSynthesis`). No audio is sent to any server — everything happens locally on your device. Available voices depend on your operating system and browser.

**Browser support:** Chrome, Edge, Safari, and most modern browsers. Firefox has limited voice selection on some platforms.

## Related Tools

- [Reading Time Calculator](/tools/reading-time-calculator/) — estimate how long it takes to read any text
- [Word Counter](/tools/word-counter/) — count words, characters, sentences, and paragraphs
