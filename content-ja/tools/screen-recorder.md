---
title: "画面録画ツール"
date: 2025-05-16
description: "無料の画面録画ツール。ブラウザだけで画面・カメラを録画してWebMでダウンロード。インストール不要、会員登録不要。"
categories: ["無料ツール"]
slug: "screen-recorder"
ShowToc: false
cover:
  image: "/images/covers/screen-recorder-ja.png"
  alt: "画面録画ツール"
---

<div id="sr-app">
<style>
#sr-app *,
#sr-app *::before,
#sr-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#sr-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  color: #1e293b;
  max-width: 720px;
  margin: 0 auto;
  padding: 16px 0;
}
#sr-app h2 {
  font-size: 20px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 16px;
}
#sr-app .sr-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
}
#sr-app .sr-section-title {
  font-size: 13px;
  font-weight: 600;
  color: #475569;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin-bottom: 12px;
}
#sr-app .sr-radio-group,
#sr-app .sr-toggle-group {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
#sr-app .sr-radio-label,
#sr-app .sr-toggle-label {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 14px;
  background: #fff;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
  color: #334155;
  transition: border-color 0.15s, background 0.15s, color 0.15s;
  user-select: none;
}
#sr-app .sr-radio-label:hover,
#sr-app .sr-toggle-label:hover {
  border-color: #94a3b8;
  background: #f1f5f9;
}
#sr-app .sr-radio-label input,
#sr-app .sr-toggle-label input {
  accent-color: #475569;
  width: 15px;
  height: 15px;
}
#sr-app .sr-radio-label.selected,
#sr-app .sr-toggle-label.active {
  background: #1e293b;
  border-color: #1e293b;
  color: #f8fafc;
}
#sr-app .sr-radio-label.selected input,
#sr-app .sr-toggle-label.active input {
  accent-color: #94a3b8;
}

/* Preview area */
#sr-app .sr-preview-area {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
#sr-app .sr-video-wrap {
  position: relative;
  background: #0f172a;
  border-radius: 10px;
  overflow: hidden;
  aspect-ratio: 16 / 9;
  display: flex;
  align-items: center;
  justify-content: center;
}
#sr-app .sr-video-placeholder {
  color: #475569;
  font-size: 14px;
  text-align: center;
  padding: 20px;
  line-height: 1.6;
}
#sr-app video {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: none;
}
#sr-app video.active {
  display: block;
}
#sr-app .sr-pip-wrap {
  position: absolute;
  bottom: 10px;
  right: 10px;
  width: 140px;
  height: 79px;
  border-radius: 6px;
  overflow: hidden;
  border: 2px solid #475569;
  background: #0f172a;
  display: none;
}
#sr-app .sr-pip-wrap video {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
#sr-app .sr-pip-wrap.active {
  display: block;
}

/* Recording indicator */
#sr-app .sr-rec-indicator {
  display: none;
  align-items: center;
  gap: 7px;
  position: absolute;
  top: 10px;
  left: 12px;
  background: rgba(15,23,42,0.72);
  padding: 4px 10px;
  border-radius: 20px;
}
#sr-app .sr-rec-indicator.visible {
  display: flex;
}
#sr-app .sr-rec-dot {
  width: 10px;
  height: 10px;
  background: #ef4444;
  border-radius: 50%;
  animation: srBlink 1s infinite;
}
#sr-app .sr-rec-indicator.paused .sr-rec-dot {
  animation: none;
  background: #f59e0b;
}
@keyframes srBlink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.25; }
}
#sr-app .sr-rec-time {
  font-size: 13px;
  font-weight: 700;
  color: #f8fafc;
  font-variant-numeric: tabular-nums;
  letter-spacing: 0.04em;
}

/* Controls */
#sr-app .sr-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: center;
}
#sr-app .sr-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s, opacity 0.15s, transform 0.1s;
}
#sr-app .sr-btn:active { transform: scale(0.97); }
#sr-app .sr-btn:disabled { opacity: 0.4; cursor: not-allowed; transform: none; }
#sr-app .sr-btn-primary {
  background: #1e293b;
  color: #f8fafc;
}
#sr-app .sr-btn-primary:hover:not(:disabled) { background: #0f172a; }
#sr-app .sr-btn-danger {
  background: #ef4444;
  color: #fff;
}
#sr-app .sr-btn-danger:hover:not(:disabled) { background: #dc2626; }
#sr-app .sr-btn-warning {
  background: #f59e0b;
  color: #fff;
}
#sr-app .sr-btn-warning:hover:not(:disabled) { background: #d97706; }
#sr-app .sr-btn-success {
  background: #10b981;
  color: #fff;
}
#sr-app .sr-btn-success:hover:not(:disabled) { background: #059669; }
#sr-app .sr-btn-outline {
  background: #fff;
  color: #334155;
  border: 1.5px solid #cbd5e1;
}
#sr-app .sr-btn-outline:hover:not(:disabled) { background: #f1f5f9; }

/* Error / notice */
#sr-app .sr-error {
  display: none;
  background: #fef2f2;
  border: 1.5px solid #fca5a5;
  border-radius: 8px;
  padding: 12px 16px;
  font-size: 13px;
  color: #b91c1c;
  line-height: 1.6;
}
#sr-app .sr-error.visible { display: block; }
#sr-app .sr-notice {
  display: none;
  background: #f0fdf4;
  border: 1.5px solid #86efac;
  border-radius: 8px;
  padding: 12px 16px;
  font-size: 13px;
  color: #166534;
  line-height: 1.6;
}
#sr-app .sr-notice.visible { display: block; }

/* Download section */
#sr-app .sr-download-wrap {
  display: none;
}
#sr-app .sr-download-wrap.visible { display: block; }

/* Responsive */
@media (max-width: 500px) {
  #sr-app .sr-radio-group,
  #sr-app .sr-toggle-group {
    flex-direction: column;
  }
  #sr-app .sr-pip-wrap {
    width: 100px;
    height: 56px;
  }
  #sr-app .sr-controls {
    flex-direction: column;
    align-items: stretch;
  }
  #sr-app .sr-btn {
    justify-content: center;
  }
}
</style>

<!-- Error banner -->
<div id="sr-error" class="sr-error"></div>
<div id="sr-notice" class="sr-notice"></div>

<!-- Settings card -->
<div class="sr-card" id="sr-settings-card">
  <div class="sr-section-title">録画モード</div>
  <div class="sr-radio-group" id="sr-mode-group">
    <label class="sr-radio-label selected" data-mode="screen">
      <input type="radio" name="sr-mode" value="screen" checked> 画面のみ
    </label>
    <label class="sr-radio-label" data-mode="camera">
      <input type="radio" name="sr-mode" value="camera"> カメラのみ
    </label>
    <label class="sr-radio-label" data-mode="screen-camera">
      <input type="radio" name="sr-mode" value="screen-camera"> 画面＋カメラ
    </label>
  </div>

  <div class="sr-section-title" style="margin-top:16px;">音声設定</div>
  <div class="sr-toggle-group">
    <label class="sr-toggle-label" id="sr-sys-audio-label">
      <input type="checkbox" id="sr-sys-audio"> システム音声
    </label>
    <label class="sr-toggle-label" id="sr-mic-label">
      <input type="checkbox" id="sr-mic"> マイク
    </label>
  </div>
</div>

<!-- Preview card -->
<div class="sr-card">
  <div class="sr-section-title">プレビュー</div>
  <div class="sr-preview-area">
    <div class="sr-video-wrap" id="sr-video-wrap">
      <div class="sr-video-placeholder" id="sr-placeholder">
        録画を開始すると<br>ここにプレビューが表示されます
      </div>
      <video id="sr-live-video" autoplay muted playsinline></video>
      <div class="sr-pip-wrap" id="sr-pip-wrap">
        <video id="sr-pip-video" autoplay muted playsinline></video>
      </div>
      <div class="sr-rec-indicator" id="sr-rec-indicator">
        <div class="sr-rec-dot"></div>
        <span class="sr-rec-time" id="sr-timer">00:00</span>
      </div>
    </div>
  </div>
</div>

<!-- Controls card -->
<div class="sr-card">
  <div class="sr-section-title">操作</div>
  <div class="sr-controls">
    <button class="sr-btn sr-btn-primary" id="sr-start-btn">録画開始</button>
    <button class="sr-btn sr-btn-warning" id="sr-pause-btn" disabled>一時停止</button>
    <button class="sr-btn sr-btn-danger" id="sr-stop-btn" disabled>停止</button>
  </div>
</div>

<!-- Download card -->
<div class="sr-card sr-download-wrap" id="sr-download-wrap">
  <div class="sr-section-title">録画データ</div>
  <div class="sr-video-wrap" style="margin-bottom:14px;">
    <video id="sr-playback-video" controls></video>
  </div>
  <div class="sr-controls">
    <button class="sr-btn sr-btn-success" id="sr-download-btn">WebMでダウンロード</button>
    <button class="sr-btn sr-btn-outline" id="sr-reset-btn">新しい録画を開始</button>
  </div>
</div>

<script>
(function () {
  'use strict';

  // --- State ---
  var state = {
    mode: 'screen',
    sysAudio: false,
    mic: false,
    recording: false,
    paused: false,
    screenStream: null,
    cameraStream: null,
    micStream: null,
    mediaRecorder: null,
    chunks: [],
    blobUrl: null,
    timerInterval: null,
    elapsed: 0,
  };

  // --- DOM refs ---
  var $ = function (id) { return document.getElementById(id); };
  var errorEl = $('sr-error');
  var noticeEl = $('sr-notice');
  var settingsCard = $('sr-settings-card');
  var modeGroup = $('sr-mode-group');
  var sysAudioCb = $('sr-sys-audio');
  var micCb = $('sr-mic');
  var sysAudioLabel = $('sr-sys-audio-label');
  var micLabel = $('sr-mic-label');
  var liveVideo = $('sr-live-video');
  var pipWrap = $('sr-pip-wrap');
  var pipVideo = $('sr-pip-video');
  var placeholder = $('sr-placeholder');
  var recIndicator = $('sr-rec-indicator');
  var timerEl = $('sr-timer');
  var startBtn = $('sr-start-btn');
  var pauseBtn = $('sr-pause-btn');
  var stopBtn = $('sr-stop-btn');
  var downloadWrap = $('sr-download-wrap');
  var playbackVideo = $('sr-playback-video');
  var downloadBtn = $('sr-download-btn');
  var resetBtn = $('sr-reset-btn');

  // --- Helper: show error ---
  function showError(msg) {
    errorEl.textContent = msg;
    errorEl.classList.add('visible');
    noticeEl.classList.remove('visible');
  }
  function clearError() {
    errorEl.classList.remove('visible');
    errorEl.textContent = '';
  }
  function showNotice(msg) {
    noticeEl.textContent = msg;
    noticeEl.classList.add('visible');
    errorEl.classList.remove('visible');
  }

  // --- Browser support check ---
  function isSupported() {
    return !!(navigator.mediaDevices && window.MediaRecorder);
  }

  // --- Mode radio styling ---
  modeGroup.addEventListener('change', function (e) {
    if (e.target.name === 'sr-mode') {
      state.mode = e.target.value;
      modeGroup.querySelectorAll('.sr-radio-label').forEach(function (l) {
        l.classList.toggle('selected', l.dataset.mode === state.mode);
      });
      // System audio only available for screen modes
      var hasScreen = state.mode !== 'camera';
      sysAudioLabel.style.opacity = hasScreen ? '1' : '0.4';
      sysAudioCb.disabled = !hasScreen;
      if (!hasScreen) {
        sysAudioCb.checked = false;
        sysAudioLabel.classList.remove('active');
        state.sysAudio = false;
      }
    }
  });

  // --- Audio toggles ---
  sysAudioCb.addEventListener('change', function () {
    state.sysAudio = sysAudioCb.checked;
    sysAudioLabel.classList.toggle('active', state.sysAudio);
  });
  micCb.addEventListener('change', function () {
    state.mic = micCb.checked;
    micLabel.classList.toggle('active', state.mic);
  });

  // --- Timer ---
  function formatTime(s) {
    var m = Math.floor(s / 60);
    var sec = s % 60;
    return (m < 10 ? '0' : '') + m + ':' + (sec < 10 ? '0' : '') + sec;
  }
  function startTimer() {
    state.elapsed = 0;
    timerEl.textContent = '00:00';
    state.timerInterval = setInterval(function () {
      if (!state.paused) {
        state.elapsed++;
        timerEl.textContent = formatTime(state.elapsed);
      }
    }, 1000);
  }
  function stopTimer() {
    clearInterval(state.timerInterval);
    state.timerInterval = null;
  }

  // --- Stop all streams ---
  function stopAllStreams() {
    if (state.screenStream) {
      state.screenStream.getTracks().forEach(function (t) { t.stop(); });
      state.screenStream = null;
    }
    if (state.cameraStream) {
      state.cameraStream.getTracks().forEach(function (t) { t.stop(); });
      state.cameraStream = null;
    }
    if (state.micStream) {
      state.micStream.getTracks().forEach(function (t) { t.stop(); });
      state.micStream = null;
    }
  }

  // --- Combine audio tracks ---
  function buildCombinedStream(videoTracks, audioTracks) {
    // Merge all tracks into one MediaStream
    var tracks = videoTracks.concat(audioTracks);
    return new MediaStream(tracks);
  }

  // --- Start recording ---
  startBtn.addEventListener('click', async function () {
    clearError();
    if (!isSupported()) {
      showError('お使いのブラウザはMediaRecorder APIに対応していません。最新のChrome / Firefox / Edgeをお試しください。');
      return;
    }

    startBtn.disabled = true;

    try {
      var videoTracks = [];
      var audioTracks = [];

      // Screen capture
      if (state.mode === 'screen' || state.mode === 'screen-camera') {
        var screenConstraints = { video: true, audio: state.sysAudio };
        state.screenStream = await navigator.mediaDevices.getDisplayMedia(screenConstraints);
        state.screenStream.getVideoTracks().forEach(function (t) { videoTracks.push(t); });
        if (state.sysAudio) {
          state.screenStream.getAudioTracks().forEach(function (t) { audioTracks.push(t); });
        }
        // Handle user stopping screen share via browser UI
        state.screenStream.getVideoTracks()[0].addEventListener('ended', function () {
          if (state.recording) {
            stopRecording();
          }
        });
      }

      // Camera capture
      if (state.mode === 'camera' || state.mode === 'screen-camera') {
        state.cameraStream = await navigator.mediaDevices.getUserMedia({ video: true, audio: false });
        if (state.mode === 'camera') {
          state.cameraStream.getVideoTracks().forEach(function (t) { videoTracks.push(t); });
        }
        // In screen+camera mode, show camera in PiP
        if (state.mode === 'screen-camera') {
          pipVideo.srcObject = state.cameraStream;
          pipWrap.classList.add('active');
        }
      }

      // Microphone
      if (state.mic) {
        state.micStream = await navigator.mediaDevices.getUserMedia({ audio: true, video: false });
        state.micStream.getAudioTracks().forEach(function (t) { audioTracks.push(t); });
      }

      if (videoTracks.length === 0) {
        showError('映像ソースを取得できませんでした。権限を確認してください。');
        stopAllStreams();
        startBtn.disabled = false;
        return;
      }

      var combinedStream = buildCombinedStream(videoTracks, audioTracks);

      // Show live preview
      liveVideo.srcObject = combinedStream;
      liveVideo.classList.add('active');
      placeholder.style.display = 'none';

      // Choose MIME type
      var mimeType = '';
      var candidates = ['video/webm;codecs=vp9,opus', 'video/webm;codecs=vp8,opus', 'video/webm'];
      for (var i = 0; i < candidates.length; i++) {
        if (MediaRecorder.isTypeSupported(candidates[i])) {
          mimeType = candidates[i];
          break;
        }
      }

      var options = mimeType ? { mimeType: mimeType } : {};
      state.mediaRecorder = new MediaRecorder(combinedStream, options);
      state.chunks = [];

      state.mediaRecorder.addEventListener('dataavailable', function (e) {
        if (e.data && e.data.size > 0) {
          state.chunks.push(e.data);
        }
      });

      state.mediaRecorder.addEventListener('stop', function () {
        var blob = new Blob(state.chunks, { type: mimeType || 'video/webm' });
        if (state.blobUrl) { URL.revokeObjectURL(state.blobUrl); }
        state.blobUrl = URL.createObjectURL(blob);
        playbackVideo.src = state.blobUrl;
        playbackVideo.classList.add('active');
        downloadWrap.classList.add('visible');
        downloadBtn.dataset.filename = 'recording-' + new Date().toISOString().replace(/[:.]/g, '-') + '.webm';
        downloadBtn.dataset.mime = mimeType || 'video/webm';
        showNotice('録画が完了しました。以下でプレビューとダウンロードができます。');
      });

      state.mediaRecorder.start(1000);
      state.recording = true;
      state.paused = false;

      // Update UI
      recIndicator.classList.add('visible');
      recIndicator.classList.remove('paused');
      pauseBtn.disabled = false;
      stopBtn.disabled = false;
      settingsCard.style.opacity = '0.5';
      settingsCard.style.pointerEvents = 'none';
      startTimer();

    } catch (err) {
      stopAllStreams();
      startBtn.disabled = false;
      if (err.name === 'NotAllowedError' || err.name === 'PermissionDeniedError') {
        showError('権限が拒否されました。ブラウザの設定で画面・カメラ・マイクへのアクセスを許可してください。');
      } else if (err.name === 'NotFoundError') {
        showError('カメラまたはマイクが見つかりませんでした。デバイスが接続されているか確認してください。');
      } else if (err.name === 'NotSupportedError') {
        showError('このブラウザでは選択した録画モードに対応していません。');
      } else {
        showError('エラーが発生しました: ' + (err.message || err.name));
      }
    }
  });

  // --- Pause / Resume ---
  pauseBtn.addEventListener('click', function () {
    if (!state.mediaRecorder) return;
    if (state.paused) {
      state.mediaRecorder.resume();
      state.paused = false;
      pauseBtn.textContent = '一時停止';
      recIndicator.classList.remove('paused');
    } else {
      state.mediaRecorder.pause();
      state.paused = true;
      pauseBtn.textContent = '再開';
      recIndicator.classList.add('paused');
    }
  });

  // --- Stop ---
  function stopRecording() {
    if (!state.mediaRecorder || !state.recording) return;
    state.mediaRecorder.stop();
    state.recording = false;
    state.paused = false;
    stopTimer();
    stopAllStreams();

    // Reset video preview
    liveVideo.srcObject = null;
    liveVideo.classList.remove('active');
    pipVideo.srcObject = null;
    pipWrap.classList.remove('active');
    placeholder.style.display = '';

    // UI
    recIndicator.classList.remove('visible');
    startBtn.disabled = false;
    pauseBtn.disabled = true;
    pauseBtn.textContent = '一時停止';
    stopBtn.disabled = true;
    settingsCard.style.opacity = '';
    settingsCard.style.pointerEvents = '';
  }

  stopBtn.addEventListener('click', stopRecording);

  // --- Download ---
  downloadBtn.addEventListener('click', function () {
    if (!state.blobUrl) return;
    var a = document.createElement('a');
    a.href = state.blobUrl;
    a.download = downloadBtn.dataset.filename || 'recording.webm';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  });

  // --- Reset ---
  resetBtn.addEventListener('click', function () {
    if (state.blobUrl) {
      URL.revokeObjectURL(state.blobUrl);
      state.blobUrl = null;
    }
    playbackVideo.src = '';
    playbackVideo.classList.remove('active');
    downloadWrap.classList.remove('visible');
    clearError();
    noticeEl.classList.remove('visible');
  });

  // --- Initial state: disable sysAudio when not in screen mode ---
  // (screen is default, so it starts enabled)
})();
</script>

<!-- freee CTA -->
<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

</div>

---

> ホワイトボードに描画 → [ホワイトボードお絵かきツール](/ja/tools/whiteboard-drawing/)
> ドット絵を作成 → [ドット絵エディター](/ja/tools/pixel-art-editor/)
> ダミー画像を作成 → [プレースホルダー画像生成ツール](/ja/tools/placeholder-image/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
