---
title: "テキスト読み上げツール"
slug: "text-to-speech"
date: 2025-09-10
description: "無料のテキスト読み上げツール。ブラウザの音声合成APIでテキストを読み上げ。声・速度・ピッチ・言語を自由に設定。登録不要。"
categories: ["無料ツール"]
ShowToc: false
cover:
  image: "/images/covers/text-to-speech-ja.png"
  alt: "テキスト読み上げツール — ブラウザ内蔵の音声合成で声・速度・ピッチを自由設定"
---

<div id="sp-app-ja">

<style>
#sp-app-ja {
  font-family: "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  max-width: 780px;
  margin: 0 auto;
  color: #1a1a2e;
}
#sp-app-ja h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 0.5rem 0;
  color: #1a1a2e;
}
#sp-app-ja .sp-card {
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.06);
}
#sp-app-ja textarea#sp-text-ja {
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
  line-height: 1.8;
  color: #1a1a2e;
  background: #f8fafc;
}
#sp-app-ja textarea#sp-text-ja:focus {
  outline: none;
  border-color: #6366f1;
  background: #fff;
}
#sp-app-ja .sp-meta-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 0.45rem;
  font-size: 0.82rem;
  color: #64748b;
}
#sp-app-ja .sp-controls-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
@media (max-width: 560px) {
  #sp-app-ja .sp-controls-grid { grid-template-columns: 1fr; }
}
#sp-app-ja label.sp-label {
  display: block;
  font-size: 0.78rem;
  font-weight: 700;
  color: #475569;
  margin-bottom: 0.3rem;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#sp-app-ja select.sp-select {
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
#sp-app-ja select.sp-select:focus { outline: none; border-color: #6366f1; }
#sp-app-ja .sp-slider-wrap { display: flex; flex-direction: column; gap: 0.25rem; }
#sp-app-ja .sp-slider-row { display: flex; align-items: center; gap: 0.6rem; }
#sp-app-ja input[type="range"].sp-slider {
  flex: 1;
  -webkit-appearance: none;
  height: 4px;
  border-radius: 2px;
  background: #e2e8f0;
  cursor: pointer;
}
#sp-app-ja input[type="range"].sp-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #6366f1;
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(99,102,241,0.4);
}
#sp-app-ja input[type="range"].sp-slider::-moz-range-thumb {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #6366f1;
  border: none;
  cursor: pointer;
}
#sp-app-ja .sp-slider-val {
  font-size: 0.82rem;
  font-weight: 700;
  color: #6366f1;
  min-width: 2.5rem;
  text-align: right;
}
#sp-app-ja .sp-btn-row { display: flex; gap: 0.75rem; flex-wrap: wrap; }
#sp-app-ja button.sp-btn {
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
}
#sp-app-ja button.sp-btn:active { transform: scale(0.97); }
#sp-app-ja button.sp-btn:disabled { opacity: 0.45; cursor: not-allowed; }
#sp-app-ja button#sp-play-ja  { background: #6366f1; color: #fff; }
#sp-app-ja button#sp-play-ja:hover:not(:disabled)  { background: #4f46e5; }
#sp-app-ja button#sp-pause-ja { background: #f59e0b; color: #fff; }
#sp-app-ja button#sp-pause-ja:hover:not(:disabled) { background: #d97706; }
#sp-app-ja button#sp-stop-ja  { background: #ef4444; color: #fff; }
#sp-app-ja button#sp-stop-ja:hover:not(:disabled)  { background: #dc2626; }
#sp-app-ja .sp-status-bar {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.88rem;
  color: #64748b;
  padding: 0.5rem 0 0;
}
#sp-app-ja .sp-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #cbd5e1;
  flex-shrink: 0;
  transition: background 0.2s;
}
#sp-app-ja .sp-dot.playing { background: #22c55e; animation: sp-pulse-ja 1s infinite; }
#sp-app-ja .sp-dot.paused  { background: #f59e0b; }
#sp-app-ja .sp-dot.stopped { background: #ef4444; }
@keyframes sp-pulse-ja {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.4; }
}
#sp-app-ja .sp-highlight-box {
  background: #f0f4ff;
  border-left: 3px solid #6366f1;
  border-radius: 0 8px 8px 0;
  padding: 0.65rem 1rem;
  font-size: 0.9rem;
  color: #3730a3;
  min-height: 2.4rem;
  line-height: 1.8;
  word-break: break-all;
}
#sp-app-ja .sp-highlight-box .sp-word-current {
  background: #6366f1;
  color: #fff;
  border-radius: 3px;
  padding: 0 3px;
}
#sp-app-ja .sp-no-support {
  background: #fef9c3;
  border: 1px solid #fde047;
  border-radius: 8px;
  padding: 1rem 1.25rem;
  font-size: 0.9rem;
  color: #713f12;
}
/* freee CTA */
#sp-app-ja .sp-freee-cta {
  background: linear-gradient(135deg, #e8f5e9 0%, #f1f8e9 100%);
  border: 1.5px solid #a5d6a7;
  border-radius: 12px;
  padding: 1.25rem 1.5rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 1.25rem;
  flex-wrap: wrap;
}
#sp-app-ja .sp-freee-cta-text h3 {
  font-size: 1rem;
  font-weight: 700;
  color: #1b5e20;
  margin: 0 0 0.3rem 0;
}
#sp-app-ja .sp-freee-cta-text p {
  font-size: 0.88rem;
  color: #2e7d32;
  margin: 0;
  line-height: 1.5;
}
#sp-app-ja .sp-freee-cta-btn {
  display: inline-block;
  background: #00c853;
  color: #fff;
  font-weight: 700;
  font-size: 0.9rem;
  padding: 0.6rem 1.4rem;
  border-radius: 8px;
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0;
  transition: background 0.15s;
}
#sp-app-ja .sp-freee-cta-btn:hover { background: #00b248; }
/* A8 footer */
#sp-app-ja .sp-a8-footer {
  font-size: 0.75rem;
  color: #94a3b8;
  border-top: 1px solid #e2e8f0;
  padding-top: 0.75rem;
  margin-top: 0.5rem;
  line-height: 1.5;
}
</style>

<div class="sp-card">
  <h2>テキストを入力</h2>
  <textarea id="sp-text-ja" placeholder="読み上げたいテキストをここに貼り付けるか入力して、「再生」を押してください…">Web Speech APIを使うと、ブラウザが内蔵の音声合成でテキストを読み上げます。音声データはサーバーに送信されず、すべてデバイス上で処理されます。下の設定で声・速度・ピッチを自由にカスタマイズできます。</textarea>
  <div class="sp-meta-row">
    <span id="sp-char-count-ja">0 文字</span>
    <span id="sp-read-time-ja">約0分で読める</span>
  </div>
</div>

<div class="sp-card">
  <h2>声・言語の選択</h2>
  <div class="sp-controls-grid">
    <div>
      <label class="sp-label" for="sp-lang-filter-ja">言語フィルター</label>
      <select class="sp-select" id="sp-lang-filter-ja">
        <option value="">すべての言語</option>
      </select>
    </div>
    <div>
      <label class="sp-label" for="sp-voice-ja">音声</label>
      <select class="sp-select" id="sp-voice-ja">
        <option value="">音声を読み込み中…</option>
      </select>
    </div>
  </div>
</div>

<div class="sp-card">
  <h2>再生設定</h2>
  <div class="sp-controls-grid">
    <div class="sp-slider-wrap">
      <label class="sp-label" for="sp-rate-ja">速度</label>
      <div class="sp-slider-row">
        <input type="range" class="sp-slider" id="sp-rate-ja" min="0.5" max="2" step="0.05" value="1">
        <span class="sp-slider-val" id="sp-rate-val-ja">1.00x</span>
      </div>
    </div>
    <div class="sp-slider-wrap">
      <label class="sp-label" for="sp-pitch-ja">ピッチ</label>
      <div class="sp-slider-row">
        <input type="range" class="sp-slider" id="sp-pitch-ja" min="0.5" max="2" step="0.05" value="1">
        <span class="sp-slider-val" id="sp-pitch-val-ja">1.00</span>
      </div>
    </div>
    <div class="sp-slider-wrap">
      <label class="sp-label" for="sp-volume-ja">音量</label>
      <div class="sp-slider-row">
        <input type="range" class="sp-slider" id="sp-volume-ja" min="0" max="1" step="0.01" value="1">
        <span class="sp-slider-val" id="sp-volume-val-ja">100%</span>
      </div>
    </div>
  </div>
</div>

<div class="sp-card">
  <div class="sp-btn-row">
    <button class="sp-btn" id="sp-play-ja">&#9654; 再生</button>
    <button class="sp-btn" id="sp-pause-ja" disabled>&#9646;&#9646; 一時停止</button>
    <button class="sp-btn" id="sp-stop-ja" disabled>&#9632; 停止</button>
  </div>
  <div class="sp-status-bar">
    <div class="sp-dot" id="sp-dot-ja"></div>
    <span id="sp-status-text-ja">待機中</span>
  </div>
</div>

<div class="sp-card">
  <h2>読み上げ中の単語</h2>
  <div class="sp-highlight-box" id="sp-highlight-box-ja">
    <span style="color:#94a3b8;">再生中、読み上げられている部分がここにハイライト表示されます。</span>
  </div>
</div>

<div id="sp-no-support-ja" class="sp-no-support" style="display:none;">
  お使いのブラウザはWeb Speech APIに対応していません。Chrome、Edge、Safariなどの最新ブラウザをご利用ください。
</div>

<script>
(function () {
  'use strict';

  if (!('speechSynthesis' in window)) {
    document.getElementById('sp-no-support-ja').style.display = 'block';
    ['sp-play-ja','sp-pause-ja','sp-stop-ja'].forEach(function(id){ document.getElementById(id).disabled = true; });
    return;
  }

  var synth = window.speechSynthesis;
  var allVoices = [];
  var currentUtterance = null;
  var spState = 'stopped';

  var elText     = document.getElementById('sp-text-ja');
  var elLangFilter = document.getElementById('sp-lang-filter-ja');
  var elVoice    = document.getElementById('sp-voice-ja');
  var elRate     = document.getElementById('sp-rate-ja');
  var elPitch    = document.getElementById('sp-pitch-ja');
  var elVolume   = document.getElementById('sp-volume-ja');
  var elRateVal  = document.getElementById('sp-rate-val-ja');
  var elPitchVal = document.getElementById('sp-pitch-val-ja');
  var elVolVal   = document.getElementById('sp-volume-val-ja');
  var elPlay     = document.getElementById('sp-play-ja');
  var elPause    = document.getElementById('sp-pause-ja');
  var elStop     = document.getElementById('sp-stop-ja');
  var elDot      = document.getElementById('sp-dot-ja');
  var elStatus   = document.getElementById('sp-status-text-ja');
  var elHighlight= document.getElementById('sp-highlight-box-ja');
  var elCharCount= document.getElementById('sp-char-count-ja');
  var elReadTime = document.getElementById('sp-read-time-ja');

  function updateMeta() {
    var txt = elText.value;
    var chars = txt.length;
    elCharCount.textContent = chars.toLocaleString() + ' 文字';
    var words = txt.trim() === '' ? 0 : txt.trim().split(/\s+/).length;
    var mins = Math.max(1, Math.ceil(chars / 400));
    elReadTime.textContent = '約' + mins + '分で読める';
  }
  elText.addEventListener('input', updateMeta);
  updateMeta();

  elRate.addEventListener('input', function() { elRateVal.textContent = parseFloat(elRate.value).toFixed(2) + 'x'; });
  elPitch.addEventListener('input', function() { elPitchVal.textContent = parseFloat(elPitch.value).toFixed(2); });
  elVolume.addEventListener('input', function() { elVolVal.textContent = Math.round(parseFloat(elVolume.value) * 100) + '%'; });

  function populateLangFilter(voices) {
    var langs = [];
    voices.forEach(function(v) {
      if (langs.indexOf(v.lang) === -1) langs.push(v.lang);
    });
    langs.sort();
    elLangFilter.innerHTML = '<option value="">すべての言語</option>';
    langs.forEach(function(l) {
      var opt = document.createElement('option');
      opt.value = l;
      opt.textContent = l;
      if (l === 'ja-JP' || l === 'ja') opt.selected = true;
      elLangFilter.appendChild(opt);
    });
  }

  function populateVoices(filterLang) {
    var voices = filterLang
      ? allVoices.filter(function(v){ return v.lang === filterLang; })
      : allVoices;
    elVoice.innerHTML = '';
    if (voices.length === 0) {
      elVoice.innerHTML = '<option value="">この言語の音声はありません</option>';
      return;
    }
    voices.forEach(function(v) {
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
    var jaLang = elLangFilter.value;
    populateVoices(jaLang);
  }

  synth.onvoiceschanged = loadVoices;
  loadVoices();
  setTimeout(loadVoices, 500);

  elLangFilter.addEventListener('change', function() {
    populateVoices(elLangFilter.value);
  });

  function setUIState(state) {
    spState = state;
    elDot.className = 'sp-dot ' + state;
    if (state === 'playing') {
      elStatus.textContent = '再生中…';
      elPlay.disabled  = true;
      elPause.disabled = false;
      elStop.disabled  = false;
      elPause.innerHTML = '\u23ae\u23ae 一時停止';
    } else if (state === 'paused') {
      elStatus.textContent = '一時停止中';
      elPlay.disabled  = true;
      elPause.disabled = false;
      elStop.disabled  = false;
      elPause.innerHTML = '\u25b6 再開';
    } else {
      elStatus.textContent = '待機中';
      elPlay.disabled  = false;
      elPause.disabled = true;
      elStop.disabled  = true;
      elPause.innerHTML = '\u23ae\u23ae 一時停止';
      elHighlight.innerHTML = '<span style="color:#94a3b8;">再生中、読み上げられている部分がここにハイライト表示されます。</span>';
    }
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
    var span = elHighlight.querySelector('.sp-word-current');
    if (span) span.scrollIntoView({ block: 'nearest', behavior: 'smooth' });
  }

  function escHtml(str) {
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  elPlay.addEventListener('click', function() {
    var text = elText.value.trim();
    if (!text) { elStatus.textContent = 'テキストを入力してください。'; return; }

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
        elStatus.textContent = 'エラー: ' + e.error;
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

  elPause.addEventListener('click', function() {
    if (spState === 'playing') {
      synth.pause();
      setUIState('paused');
    } else if (spState === 'paused') {
      synth.resume();
      setUIState('playing');
    }
  });

  elStop.addEventListener('click', function() {
    synth.cancel();
    setUIState('stopped');
  });

  setUIState('stopped');
})();
</script>

</div>

---

## 使い方

1. テキストエリアに読み上げたいテキストを貼り付けるか入力します。
2. 言語フィルターで絞り込んだあと、使用する音声を選択します。
3. 速度・ピッチ・音量のスライダーで好みに合わせて調整します。
4. **「再生」ボタン**を押すと、読み上げが開始されます。読み上げ中の部分がリアルタイムでハイライトされます。
5. **「一時停止」**で途中停止、**「停止」**で完全にリセットできます。

## このツールについて

このツールはブラウザ内蔵の **Web Speech API（SpeechSynthesis）** を使用しています。音声データはサーバーには一切送信されず、すべてお使いのデバイス上で処理されます。利用できる音声はOSとブラウザによって異なります。

**対応ブラウザ：** Chrome、Edge、Safari、およびほとんどの最新ブラウザ。Firefoxは環境によって音声の選択肢が限られる場合があります。

---

<div id="sp-app-ja">
<div class="sp-freee-cta">
  <div class="sp-freee-cta-text">
    <h3>個人事業主・フリーランスの方へ：会計をもっとかんたんに</h3>
    <p>freee会計なら、確定申告・請求書・経費管理をまとめて自動化。面倒な帳簿作業から解放されます。</p>
  </div>
  <a class="sp-freee-cta-btn" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener sponsored">freeeを無料で試す</a>
</div>
</div>

## 関連ツール

- [読書時間計算ツール](/ja/tools/reading-time-calculator/) — テキストを読むのにかかる時間を計算
- [文字数カウンター](/ja/tools/word-counter/) — 文字数・単語数・文の数をカウント

---

<div id="sp-app-ja">
<div class="sp-a8-footer">
本ページはアフィリエイト広告（A8.net）を含む場合があります。掲載している商品・サービスの選定は編集部の判断によるものです。
</div>
</div>
