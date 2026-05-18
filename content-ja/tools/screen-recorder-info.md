---
title: "画面情報＆ディスプレイテスト"
date: 2025-12-20
description: "無料の画面情報＆ディスプレイテストツール。画面解像度・ビューポート・デバイスピクセル比・色深度・向き・リフレッシュレート・タッチ対応・ブラウザ・OS情報を表示。カラーバー・グレースケール・ドット抜けテスト対応。"
categories: ["無料ツール"]
slug: "screen-recorder-info"
ShowToc: false
aliases: ["/ja/tools/viewport-tester/"]
cover:
  image: "/images/covers/screen-recorder-info-ja.png"
  alt: "画面情報＆ディスプレイテスト"
---

<div id="si-app">
<style>
#si-app {
  font-family: 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', -apple-system, sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
  box-sizing: border-box;
}
#si-app *, #si-app *::before, #si-app *::after {
  box-sizing: border-box;
}
#si-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 12px 0;
  color: #0f172a;
}
#si-app .si-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#si-app .si-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px 16px;
}
#si-app .si-row {
  display: flex;
  flex-direction: column;
  gap: 2px;
}
#si-app .si-label {
  font-size: 11px;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#si-app .si-value {
  font-size: 15px;
  font-weight: 700;
  color: #0f172a;
  word-break: break-all;
}
#si-app .si-value.good { color: #059669; }
#si-app .si-value.warn { color: #d97706; }
#si-app .si-section-title {
  font-size: 13px;
  font-weight: 700;
  color: #475569;
  margin-bottom: 12px;
  padding-bottom: 6px;
  border-bottom: 1.5px solid #f1f5f9;
}
#si-app .si-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 4px;
}
#si-app .si-btn {
  padding: 8px 14px;
  border: 1.5px solid #cbd5e1;
  background: #f8fafc;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  color: #334155;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
}
#si-app .si-btn:hover {
  background: #e0f2fe;
  border-color: #7dd3fc;
  color: #0369a1;
}
#si-app .si-refresh-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 7px 14px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  margin-bottom: 14px;
  transition: background 0.15s;
}
#si-app .si-refresh-btn:hover { background: #4f46e5; }
#si-app .si-fps-bar {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 8px;
}
#si-app .si-fps-track {
  flex: 1;
  height: 8px;
  background: #e2e8f0;
  border-radius: 4px;
  overflow: hidden;
}
#si-app .si-fps-fill {
  height: 100%;
  background: #22c55e;
  border-radius: 4px;
  transition: width 0.5s;
}
#si-app .si-overlay {
  display: none;
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  z-index: 999999;
  cursor: pointer;
}
#si-app .si-colorbar {
  display: flex;
  height: 80px;
  border-radius: 8px;
  overflow: hidden;
  margin-top: 8px;
}
#si-app .si-colorbar div { flex: 1; }
#si-app .si-gray {
  height: 40px;
  border-radius: 8px;
  margin-top: 8px;
  background: linear-gradient(to right, #000 0%, #fff 100%);
}
@media (max-width: 480px) {
  #si-app .si-grid { grid-template-columns: 1fr; }
}
</style>

<button class="si-refresh-btn" onclick="siRefresh()">&#8635; 情報を更新</button>

<div class="si-card">
  <div class="si-section-title">画面・ディスプレイ情報</div>
  <div class="si-grid">
    <div class="si-row"><span class="si-label">画面解像度</span><span class="si-value" id="si-res">—</span></div>
    <div class="si-row"><span class="si-label">ビューポートサイズ</span><span class="si-value" id="si-vp">—</span></div>
    <div class="si-row"><span class="si-label">デバイスピクセル比</span><span class="si-value" id="si-dpr">—</span></div>
    <div class="si-row"><span class="si-label">色深度</span><span class="si-value" id="si-cd">—</span></div>
    <div class="si-row"><span class="si-label">向き（オリエンテーション）</span><span class="si-value" id="si-ori">—</span></div>
    <div class="si-row"><span class="si-label">タッチ対応</span><span class="si-value" id="si-touch">—</span></div>
  </div>
</div>

<div class="si-card">
  <div class="si-section-title">ブラウザ・システム情報</div>
  <div class="si-grid">
    <div class="si-row"><span class="si-label">ブラウザ</span><span class="si-value" id="si-browser">—</span></div>
    <div class="si-row"><span class="si-label">OS</span><span class="si-value" id="si-os">—</span></div>
    <div class="si-row"><span class="si-label">言語</span><span class="si-value" id="si-lang">—</span></div>
    <div class="si-row"><span class="si-label">オンライン状態</span><span class="si-value" id="si-online">—</span></div>
    <div class="si-row"><span class="si-label">Cookie有効</span><span class="si-value" id="si-cookie">—</span></div>
    <div class="si-row"><span class="si-label">ハードウェアスレッド数</span><span class="si-value" id="si-hw">—</span></div>
  </div>
</div>

<div class="si-card">
  <div class="si-section-title">リフレッシュレート測定</div>
  <div id="si-fps-label" style="font-size:13px;color:#64748b;">「測定開始」をクリックするとrequestAnimationFrameを使ってディスプレイのリフレッシュレートを推定します。</div>
  <div class="si-fps-bar" id="si-fps-bar" style="display:none;">
    <div class="si-fps-track"><div class="si-fps-fill" id="si-fps-fill" style="width:0%"></div></div>
    <span style="font-size:15px;font-weight:800;color:#0f172a;min-width:60px;" id="si-fps-val">— Hz</span>
  </div>
  <div class="si-btn-row" style="margin-top:10px;">
    <button class="si-btn" onclick="siMeasureFPS()">リフレッシュレートを測定</button>
  </div>
</div>

<div class="si-card">
  <div class="si-section-title">ディスプレイテストパターン</div>
  <p style="font-size:13px;color:#64748b;margin:0 0 10px;">テストをクリックするとフルスクリーンで表示されます。画面をクリックすると終了します。</p>
  <div class="si-colorbar">
    <div style="background:#fff"></div>
    <div style="background:#ff0000"></div>
    <div style="background:#00ff00"></div>
    <div style="background:#0000ff"></div>
    <div style="background:#ffff00"></div>
    <div style="background:#ff00ff"></div>
    <div style="background:#00ffff"></div>
    <div style="background:#000"></div>
  </div>
  <div class="si-gray"></div>
  <div class="si-btn-row" style="margin-top:12px;">
    <button class="si-btn" onclick="siRunTest('colorbars')">カラーバー</button>
    <button class="si-btn" onclick="siRunTest('grayscale')">グレースケール</button>
    <button class="si-btn" onclick="siRunTest('black')">ドット抜け（黒）</button>
    <button class="si-btn" onclick="siRunTest('white')">ドット抜け（白）</button>
    <button class="si-btn" onclick="siRunTest('red')">ドット抜け（赤）</button>
    <button class="si-btn" onclick="siRunTest('green')">ドット抜け（緑）</button>
    <button class="si-btn" onclick="siRunTest('blue')">ドット抜け（青）</button>
  </div>
</div>

<div class="si-overlay" id="si-overlay" onclick="siCloseTest()"></div>

<script>
(function(){
  function siDetectBrowser(ua) {
    if (/Edg\//.test(ua)) return 'Microsoft Edge';
    if (/OPR\/|Opera/.test(ua)) return 'Opera';
    if (/Firefox\//.test(ua)) return 'Firefox';
    if (/SamsungBrowser/.test(ua)) return 'Samsung Internet';
    if (/Chrome\//.test(ua)) return 'Chrome';
    if (/Safari\//.test(ua)) return 'Safari';
    return '不明';
  }

  function siDetectOS(ua) {
    if (/Windows NT 10/.test(ua)) return 'Windows 10/11';
    if (/Windows NT/.test(ua)) return 'Windows';
    if (/Mac OS X/.test(ua)) return 'macOS';
    if (/iPhone/.test(ua)) return 'iOS (iPhone)';
    if (/iPad/.test(ua)) return 'iPadOS';
    if (/Android/.test(ua)) return 'Android';
    if (/Linux/.test(ua)) return 'Linux';
    return '不明';
  }

  window.siRefresh = function() {
    const ua = navigator.userAgent;
    document.getElementById('si-res').textContent = screen.width + ' × ' + screen.height + ' px';
    document.getElementById('si-vp').textContent = window.innerWidth + ' × ' + window.innerHeight + ' px';
    const dpr = window.devicePixelRatio || 1;
    const dprEl = document.getElementById('si-dpr');
    dprEl.textContent = dpr.toFixed(2) + 'x';
    dprEl.className = 'si-value' + (dpr >= 2 ? ' good' : '');
    document.getElementById('si-cd').textContent = (screen.colorDepth || '—') + 'ビット';
    const oriRaw = screen.orientation ? screen.orientation.type : (window.innerWidth > window.innerHeight ? 'landscape' : 'portrait');
    const oriMap = {'landscape-primary':'横向き','landscape-secondary':'横向き（反転）','portrait-primary':'縦向き','portrait-secondary':'縦向き（反転）','landscape':'横向き','portrait':'縦向き'};
    document.getElementById('si-ori').textContent = oriMap[oriRaw] || oriRaw;
    const touch = navigator.maxTouchPoints > 0;
    const touchEl = document.getElementById('si-touch');
    touchEl.textContent = touch ? '対応 (' + navigator.maxTouchPoints + 'ポイント)' : '非対応';
    touchEl.className = 'si-value' + (touch ? ' good' : '');
    document.getElementById('si-browser').textContent = siDetectBrowser(ua);
    document.getElementById('si-os').textContent = siDetectOS(ua);
    document.getElementById('si-lang').textContent = navigator.language || '—';
    const onlineEl = document.getElementById('si-online');
    onlineEl.textContent = navigator.onLine ? 'オンライン' : 'オフライン';
    onlineEl.className = 'si-value' + (navigator.onLine ? ' good' : ' warn');
    const cookieEl = document.getElementById('si-cookie');
    cookieEl.textContent = navigator.cookieEnabled ? '有効' : '無効';
    cookieEl.className = 'si-value' + (navigator.cookieEnabled ? ' good' : ' warn');
    document.getElementById('si-hw').textContent = navigator.hardwareConcurrency ? navigator.hardwareConcurrency + 'コア' : '—';
  };

  window.siMeasureFPS = function() {
    const label = document.getElementById('si-fps-label');
    const bar = document.getElementById('si-fps-bar');
    const fill = document.getElementById('si-fps-fill');
    const val = document.getElementById('si-fps-val');
    label.textContent = '測定中... 約1秒お待ちください';
    bar.style.display = 'flex';
    fill.style.width = '0%';
    val.textContent = '...';

    let frames = 0;
    let start = null;
    const DURATION = 1000;

    function measure(ts) {
      if (!start) start = ts;
      frames++;
      const elapsed = ts - start;
      if (elapsed < DURATION) {
        requestAnimationFrame(measure);
      } else {
        const fps = Math.round(frames / (elapsed / 1000));
        const pct = Math.min(100, (fps / 144) * 100);
        fill.style.width = pct + '%';
        fill.style.background = fps >= 100 ? '#6366f1' : fps >= 60 ? '#22c55e' : fps >= 30 ? '#f59e0b' : '#ef4444';
        val.textContent = fps + ' Hz';
        label.textContent = '推定リフレッシュレート：' + fps + ' Hz' + (fps >= 120 ? '（高リフレッシュレート）' : fps >= 60 ? '（標準）' : '（低い）');
      }
    }
    requestAnimationFrame(measure);
  };

  const COLOR_BARS = ['#fff','#ff0','#0ff','#0f0','#f0f','#f00','#00f','#000'];
  const TEST_LABELS = {
    colorbars: 'カラーバー — クリックして終了',
    grayscale: 'グレースケール — クリックして終了',
    black: 'ドット抜けテスト（黒）— 明るいピクセルを探してください — クリックして終了',
    white: 'ドット抜けテスト（白）— 暗いピクセルを探してください — クリックして終了',
    red: 'ドット抜けテスト（赤）— クリックして終了',
    green: 'ドット抜けテスト（緑）— クリックして終了',
    blue: 'ドット抜けテスト（青）— クリックして終了'
  };

  window.siRunTest = function(type) {
    const overlay = document.getElementById('si-overlay');
    overlay.innerHTML = '';
    overlay.style.cssText = 'display:block;position:fixed;top:0;left:0;right:0;bottom:0;z-index:999999;cursor:pointer;';

    if (type === 'colorbars') {
      overlay.style.display = 'flex';
      COLOR_BARS.forEach(c => {
        const d = document.createElement('div');
        d.style.cssText = 'flex:1;height:100%;background:' + c;
        overlay.appendChild(d);
      });
    } else if (type === 'grayscale') {
      overlay.style.background = 'linear-gradient(to right,#000 0%,#fff 100%)';
    } else {
      const colors = {black:'#000',white:'#fff',red:'#f00',green:'#0f0',blue:'#00f'};
      overlay.style.background = colors[type] || '#000';
    }

    const lbl = document.createElement('div');
    lbl.textContent = TEST_LABELS[type] || 'クリックして終了';
    lbl.style.cssText = 'position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,0.7);color:#fff;padding:8px 20px;border-radius:30px;font-size:14px;font-weight:600;pointer-events:none;z-index:1000000;white-space:nowrap;';
    overlay.appendChild(lbl);
  };

  window.siCloseTest = function() {
    const overlay = document.getElementById('si-overlay');
    overlay.style.display = 'none';
    overlay.innerHTML = '';
    overlay.style.background = '';
  };

  window.addEventListener('resize', function() {
    document.getElementById('si-vp').textContent = window.innerWidth + ' × ' + window.innerHeight + ' px';
    const oriRaw = screen.orientation ? screen.orientation.type : (window.innerWidth > window.innerHeight ? 'landscape' : 'portrait');
    const oriMap = {'landscape-primary':'横向き','landscape-secondary':'横向き（反転）','portrait-primary':'縦向き','portrait-secondary':'縦向き（反転）','landscape':'横向き','portrait':'縦向き'};
    document.getElementById('si-ori').textContent = oriMap[oriRaw] || oriRaw;
  });

  siRefresh();
})();
</script>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

> 画面解像度 → [画面解像度ツール](/ja/tools/screen-resolution/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
