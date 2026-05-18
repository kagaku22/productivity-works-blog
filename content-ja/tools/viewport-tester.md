---
title: "ビューポートサイズテスター"
slug: "viewport-tester"
date: 2025-05-21
description: "無料のビューポートサイズテスター。ブラウザの表示領域サイズをリアルタイム表示し、レスポンシブブレイクポイントを確認。登録不要ですぐ使えます。"
categories: ["無料ツール"]
tags: ["ビューポート", "レスポンシブデザイン", "ブレイクポイント", "Web開発", "CSS"]
ShowToc: false
cover:
  image: /images/covers/viewport-tester-ja.png
  alt: "ビューポートサイズテスター — ブラウザの表示領域サイズとレスポンシブブレイクポイントをリアルタイム確認"
---

ブラウザの表示領域（ビューポート）サイズをリアルタイムで確認し、どのCSSブレイクポイントが適用されているかを即座に把握できます。デバイスプリセット一覧との比較機能付き。登録・インストール不要。

**関連ツール:** 画面解像度 → [画面解像度チェッカー](/ja/tools/screen-resolution/) | メディアクエリ → [CSSメディアクエリジェネレーター](/ja/tools/media-query-generator/)

---

<div id="vt-app">

<style>
#vt-app * {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#vt-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Yu Gothic", Meiryo, sans-serif;
  font-size: 15px;
  color: #1e293b;
  line-height: 1.6;
  max-width: 860px;
}
#vt-app h2 {
  font-size: 17px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 12px;
  padding-bottom: 6px;
  border-bottom: 2px solid #e2e8f0;
}
#vt-app .vt-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 22px;
  margin-bottom: 20px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#vt-app .vt-hero {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  background: linear-gradient(135deg, #0f172a 0%, #1e3a5f 100%);
  border-radius: 14px;
  padding: 28px 24px;
  margin-bottom: 20px;
  flex-wrap: wrap;
}
#vt-app .vt-big-dim {
  text-align: center;
}
#vt-app .vt-big-dim .vt-num {
  font-size: 52px;
  font-weight: 800;
  color: #38bdf8;
  letter-spacing: -2px;
  line-height: 1;
}
#vt-app .vt-big-dim .vt-label {
  font-size: 12px;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-top: 4px;
}
#vt-app .vt-sep {
  font-size: 36px;
  color: #475569;
  font-weight: 300;
  padding: 0 4px;
}
#vt-app .vt-bp-badge {
  background: #0284c7;
  color: #fff;
  font-size: 22px;
  font-weight: 800;
  border-radius: 10px;
  padding: 10px 22px;
  letter-spacing: 1px;
  text-align: center;
}
#vt-app .vt-bp-name {
  font-size: 11px;
  color: #bae6fd;
  margin-top: 4px;
  text-align: center;
  letter-spacing: 0.5px;
}
#vt-app .vt-meta-row {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  flex-wrap: wrap;
  margin-top: 10px;
}
#vt-app .vt-pill {
  background: rgba(255,255,255,0.08);
  border: 1px solid rgba(255,255,255,0.15);
  border-radius: 20px;
  padding: 4px 14px;
  font-size: 12px;
  color: #cbd5e1;
}
#vt-app .vt-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-bottom: 20px;
}
@media (max-width: 560px) {
  #vt-app .vt-grid { grid-template-columns: 1fr; }
}
#vt-app .vt-stat-card {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 14px 16px;
}
#vt-app .vt-stat-card .vt-stat-title {
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  color: #64748b;
  margin-bottom: 4px;
}
#vt-app .vt-stat-card .vt-stat-val {
  font-size: 17px;
  font-weight: 700;
  color: #0f172a;
  font-variant-numeric: tabular-nums;
}
#vt-app .vt-stat-card .vt-stat-sub {
  font-size: 12px;
  color: #94a3b8;
  margin-top: 2px;
}
/* Breakpoint bar */
#vt-app .vt-bpbar-wrap {
  margin-bottom: 20px;
}
#vt-app .vt-bpbar-track {
  position: relative;
  height: 36px;
  background: #e2e8f0;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 6px;
}
#vt-app .vt-bpbar-fill {
  position: absolute;
  left: 0; top: 0; bottom: 0;
  background: linear-gradient(90deg, #0284c7, #38bdf8);
  border-radius: 8px;
  transition: width 0.2s ease;
  min-width: 4px;
}
#vt-app .vt-bpbar-label {
  position: absolute;
  right: 8px; top: 0; bottom: 0;
  display: flex;
  align-items: center;
  font-size: 12px;
  font-weight: 600;
  color: #fff;
  text-shadow: 0 1px 2px rgba(0,0,0,0.3);
}
#vt-app .vt-bpbar-ticks {
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  color: #94a3b8;
  padding: 0 2px;
}
#vt-app .vt-bp-segments {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  margin-top: 10px;
}
#vt-app .vt-bp-seg {
  flex: 1;
  min-width: 60px;
  text-align: center;
  padding: 6px 4px;
  border-radius: 7px;
  border: 1.5px solid #e2e8f0;
  font-size: 12px;
  font-weight: 600;
  color: #64748b;
  background: #f8fafc;
  transition: all 0.15s;
}
#vt-app .vt-bp-seg.active {
  background: #0284c7;
  border-color: #0284c7;
  color: #fff;
  box-shadow: 0 2px 8px rgba(2,132,199,0.25);
}
#vt-app .vt-bp-seg .vt-seg-range {
  display: block;
  font-size: 10px;
  font-weight: 400;
  opacity: 0.8;
  margin-top: 2px;
}
/* Device presets table */
#vt-app .vt-preset-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
#vt-app .vt-preset-table th {
  text-align: left;
  padding: 8px 10px;
  background: #f1f5f9;
  color: #475569;
  font-size: 11px;
  letter-spacing: 0.4px;
  border-bottom: 1.5px solid #e2e8f0;
}
#vt-app .vt-preset-table td {
  padding: 9px 10px;
  border-bottom: 1px solid #f1f5f9;
  color: #334155;
}
#vt-app .vt-preset-table tr:last-child td {
  border-bottom: none;
}
#vt-app .vt-preset-table tr:hover td {
  background: #f8fafc;
}
#vt-app .vt-preset-table .vt-device-name {
  font-weight: 600;
  color: #0f172a;
}
#vt-app .vt-preset-table .vt-bp-chip {
  display: inline-block;
  padding: 2px 8px;
  border-radius: 10px;
  font-size: 11px;
  font-weight: 700;
  background: #e0f2fe;
  color: #0369a1;
}
/* Copy button */
#vt-app .vt-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}
#vt-app .vt-btn {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  padding: 10px 20px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: all 0.15s;
  font-family: inherit;
}
#vt-app .vt-btn-primary {
  background: #0284c7;
  color: #fff;
}
#vt-app .vt-btn-primary:hover {
  background: #0369a1;
}
#vt-app .vt-btn-secondary {
  background: #f1f5f9;
  color: #334155;
  border: 1.5px solid #e2e8f0;
}
#vt-app .vt-btn-secondary:hover {
  background: #e2e8f0;
}
#vt-app .vt-copy-msg {
  display: none;
  font-size: 13px;
  color: #16a34a;
  align-items: center;
  gap: 5px;
  padding: 10px 16px;
  background: #f0fdf4;
  border-radius: 8px;
  border: 1px solid #bbf7d0;
}
#vt-app .vt-copy-msg.show { display: flex; }
</style>

<!-- HERO: ライブ寸法表示 -->
<div class="vt-hero" id="vt-hero">
  <div class="vt-big-dim">
    <div class="vt-num" id="vt-width">—</div>
    <div class="vt-label">幅 (px)</div>
  </div>
  <div class="vt-sep">×</div>
  <div class="vt-big-dim">
    <div class="vt-num" id="vt-height">—</div>
    <div class="vt-label">高さ (px)</div>
  </div>
  <div>
    <div class="vt-bp-badge" id="vt-bp-badge">—</div>
    <div class="vt-bp-name" id="vt-bp-name">ブレイクポイント</div>
  </div>
  <div style="width:100%;">
    <div class="vt-meta-row">
      <span class="vt-pill" id="vt-orientation">—</span>
      <span class="vt-pill" id="vt-touch">—</span>
      <span class="vt-pill" id="vt-dpr">DPR —</span>
    </div>
  </div>
</div>

<!-- ブレイクポイントビジュアルバー -->
<div class="vt-card vt-bpbar-wrap">
  <h2>ブレイクポイントインジケーター</h2>
  <div class="vt-bpbar-track">
    <div class="vt-bpbar-fill" id="vt-bar-fill" style="width:50%;">
      <span class="vt-bpbar-label" id="vt-bar-label"></span>
    </div>
  </div>
  <div class="vt-bpbar-ticks">
    <span>0</span><span>640</span><span>768</span><span>1024</span><span>1280</span><span>1536+</span>
  </div>
  <div class="vt-bp-segments">
    <div class="vt-bp-seg" id="seg-xs">xs<span class="vt-seg-range">&lt;640px</span></div>
    <div class="vt-bp-seg" id="seg-sm">sm<span class="vt-seg-range">640–767</span></div>
    <div class="vt-bp-seg" id="seg-md">md<span class="vt-seg-range">768–1023</span></div>
    <div class="vt-bp-seg" id="seg-lg">lg<span class="vt-seg-range">1024–1279</span></div>
    <div class="vt-bp-seg" id="seg-xl">xl<span class="vt-seg-range">1280–1535</span></div>
    <div class="vt-bp-seg" id="seg-2xl">2xl<span class="vt-seg-range">1536px+</span></div>
  </div>
</div>

<!-- 詳細ステータスグリッド -->
<div class="vt-grid">
  <div class="vt-stat-card">
    <div class="vt-stat-title">window.innerWidth</div>
    <div class="vt-stat-val" id="stat-iw">—</div>
    <div class="vt-stat-sub">スクロールバーを含む表示幅</div>
  </div>
  <div class="vt-stat-card">
    <div class="vt-stat-title">window.innerHeight</div>
    <div class="vt-stat-val" id="stat-ih">—</div>
    <div class="vt-stat-sub">スクロールバーを含む表示高さ</div>
  </div>
  <div class="vt-stat-card">
    <div class="vt-stat-title">document.documentElement</div>
    <div class="vt-stat-val" id="stat-doc">— × —</div>
    <div class="vt-stat-sub">clientWidth × clientHeight</div>
  </div>
  <div class="vt-stat-card">
    <div class="vt-stat-title">screen.width × screen.height</div>
    <div class="vt-stat-val" id="stat-scr">—</div>
    <div class="vt-stat-sub">物理画面の解像度</div>
  </div>
  <div class="vt-stat-card">
    <div class="vt-stat-title">devicePixelRatio</div>
    <div class="vt-stat-val" id="stat-dpr">—</div>
    <div class="vt-stat-sub">CSS px と物理 px の比率</div>
  </div>
  <div class="vt-stat-card">
    <div class="vt-stat-title">向き（Orientation）</div>
    <div class="vt-stat-val" id="stat-orient">—</div>
    <div class="vt-stat-sub">縦向き / 横向き</div>
  </div>
</div>

<!-- アクションボタン -->
<div class="vt-actions">
  <button class="vt-btn vt-btn-primary" onclick="vtCopyAll()">
    <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
    情報をコピー
  </button>
  <div class="vt-copy-msg" id="vt-copy-msg">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
    クリップボードにコピーしました！
  </div>
</div>

<!-- デバイスプリセット一覧 -->
<div class="vt-card">
  <h2>主要デバイスのビューポート参考値</h2>
  <div style="overflow-x:auto;">
    <table class="vt-preset-table">
      <thead>
        <tr>
          <th>デバイス</th>
          <th>ビューポート (CSS px)</th>
          <th>Tailwind BP</th>
          <th>備考</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="vt-device-name">iPhone 15 Pro</td>
          <td>393 × 852</td>
          <td><span class="vt-bp-chip">xs</span></td>
          <td>縦向き、@3x</td>
        </tr>
        <tr>
          <td class="vt-device-name">iPhone 15 / 14</td>
          <td>390 × 844</td>
          <td><span class="vt-bp-chip">xs</span></td>
          <td>縦向き、@3x</td>
        </tr>
        <tr>
          <td class="vt-device-name">iPhone SE（第3世代）</td>
          <td>375 × 667</td>
          <td><span class="vt-bp-chip">xs</span></td>
          <td>縦向き、@2x</td>
        </tr>
        <tr>
          <td class="vt-device-name">iPad（第10世代）</td>
          <td>820 × 1180</td>
          <td><span class="vt-bp-chip">md</span></td>
          <td>縦向き、@2x</td>
        </tr>
        <tr>
          <td class="vt-device-name">iPad Pro 12.9"</td>
          <td>1024 × 1366</td>
          <td><span class="vt-bp-chip">lg</span></td>
          <td>縦向き、@2x</td>
        </tr>
        <tr>
          <td class="vt-device-name">Pixel 7</td>
          <td>412 × 915</td>
          <td><span class="vt-bp-chip">xs</span></td>
          <td>縦向き、@2.625x</td>
        </tr>
        <tr>
          <td class="vt-device-name">Galaxy S24</td>
          <td>360 × 780</td>
          <td><span class="vt-bp-chip">xs</span></td>
          <td>縦向き、@3x</td>
        </tr>
        <tr>
          <td class="vt-device-name">MacBook Air 13"</td>
          <td>1280 × 800</td>
          <td><span class="vt-bp-chip">xl</span></td>
          <td>Retina @2x</td>
        </tr>
        <tr>
          <td class="vt-device-name">MacBook Pro 14"</td>
          <td>1512 × 982</td>
          <td><span class="vt-bp-chip">xl</span></td>
          <td>Retina @2x</td>
        </tr>
        <tr>
          <td class="vt-device-name">MacBook Pro 16"</td>
          <td>1728 × 1117</td>
          <td><span class="vt-bp-chip">2xl</span></td>
          <td>Retina @2x</td>
        </tr>
        <tr>
          <td class="vt-device-name">デスクトップ 1080p</td>
          <td>1920 × 1080</td>
          <td><span class="vt-bp-chip">2xl</span></td>
          <td>@1x 標準</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<script>
(function() {
  var BP_BREAKS = [
    { id: 'xs',  name: 'xs (640px未満)',   min: 0,    max: 639  },
    { id: 'sm',  name: 'sm (640〜767px)',  min: 640,  max: 767  },
    { id: 'md',  name: 'md (768〜1023px)', min: 768,  max: 1023 },
    { id: 'lg',  name: 'lg (1024〜1279px)',min: 1024, max: 1279 },
    { id: 'xl',  name: 'xl (1280〜1535px)',min: 1280, max: 1535 },
    { id: '2xl', name: '2xl (1536px以上)', min: 1536, max: Infinity }
  ];

  var MAX_BAR_W = 1536;

  function getBP(w) {
    for (var i = BP_BREAKS.length - 1; i >= 0; i--) {
      if (w >= BP_BREAKS[i].min) return BP_BREAKS[i];
    }
    return BP_BREAKS[0];
  }

  function update() {
    var iw = window.innerWidth;
    var ih = window.innerHeight;
    var dw = document.documentElement.clientWidth;
    var dh = document.documentElement.clientHeight;
    var sw = screen.width;
    var sh = screen.height;
    var dpr = window.devicePixelRatio || 1;
    var isTouch = ('ontouchstart' in window) || navigator.maxTouchPoints > 0;
    var orient = iw >= ih ? '横向き (Landscape)' : '縦向き (Portrait)';
    var bp = getBP(iw);

    document.getElementById('vt-width').textContent = iw;
    document.getElementById('vt-height').textContent = ih;
    document.getElementById('vt-bp-badge').textContent = bp.id;
    document.getElementById('vt-bp-name').textContent = bp.name;
    document.getElementById('vt-orientation').textContent = orient;
    document.getElementById('vt-touch').textContent = isTouch ? 'タッチデバイス' : '非タッチデバイス';
    document.getElementById('vt-dpr').textContent = 'DPR ' + dpr.toFixed(2);

    var pct = Math.min(100, (iw / MAX_BAR_W) * 100);
    document.getElementById('vt-bar-fill').style.width = pct + '%';
    document.getElementById('vt-bar-label').textContent = iw + 'px';

    BP_BREAKS.forEach(function(b) {
      var el = document.getElementById('seg-' + b.id);
      if (el) el.classList.toggle('active', b.id === bp.id);
    });

    document.getElementById('stat-iw').textContent = iw + ' px';
    document.getElementById('stat-ih').textContent = ih + ' px';
    document.getElementById('stat-doc').textContent = dw + ' × ' + dh + ' px';
    document.getElementById('stat-scr').textContent = sw + ' × ' + sh + ' px';
    document.getElementById('stat-dpr').textContent = dpr.toFixed(3);
    document.getElementById('stat-orient').textContent = orient;
  }

  window.vtCopyAll = function() {
    var iw = window.innerWidth;
    var ih = window.innerHeight;
    var dw = document.documentElement.clientWidth;
    var dh = document.documentElement.clientHeight;
    var dpr = (window.devicePixelRatio || 1).toFixed(3);
    var isTouch = ('ontouchstart' in window) || navigator.maxTouchPoints > 0;
    var orient = iw >= ih ? '横向き (Landscape)' : '縦向き (Portrait)';
    var bp = getBP(iw);

    var text = [
      '=== ビューポート情報 ===',
      'ビューポート (innerWidth x innerHeight): ' + iw + ' x ' + ih + ' px',
      'ドキュメント (clientWidth x clientHeight): ' + dw + ' x ' + dh + ' px',
      '画面解像度: ' + screen.width + ' x ' + screen.height + ' px',
      'devicePixelRatio: ' + dpr,
      'Tailwind ブレイクポイント: ' + bp.id + ' (' + bp.name + ')',
      '向き: ' + orient,
      'タッチデバイス: ' + (isTouch ? 'はい' : 'いいえ'),
      '取得日時: ' + new Date().toISOString()
    ].join('\n');

    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() { vtShowCopied(); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text;
      ta.style.position = 'fixed';
      ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      vtShowCopied();
    }
  };

  window.vtShowCopied = function() {
    var msg = document.getElementById('vt-copy-msg');
    msg.classList.add('show');
    setTimeout(function() { msg.classList.remove('show'); }, 2500);
  };

  update();
  window.addEventListener('resize', update);
  if (window.screen && window.screen.orientation) {
    screen.orientation.addEventListener('change', update);
  }
})();
</script>

</div>

---

## 使い方

1. **上部の数値を確認** — ブラウザのウィンドウをリサイズするとリアルタイムで更新されます。
2. **ブレイクポイントバーをチェック** — 現在の幅がTailwind CSSのどのブレイクポイント（xs / sm / md / lg / xl / 2xl）に該当するかが一目でわかります。
3. **デバイスプリセット一覧で比較** — 実機でどのように表示されるかの参考として活用してください。
4. **「情報をコピー」ボタン** — バグ報告やデザイン確認のためにスナップショットをテキストでコピーできます。

## 各プロパティの意味

| プロパティ | 計測対象 |
|---|---|
| `window.innerWidth/Height` | スクロールバーを含む表示領域のサイズ |
| `clientWidth/Height` | スクロールバーを除いた表示領域（CSSメディアクエリと一致） |
| `screen.width/Height` | デバイスの物理画面解像度（ズームに影響されない） |
| `devicePixelRatio` | CSS 1px が物理何ピクセルに対応するか（Retinaは2以上） |

## Tailwind CSS ブレイクポイント一覧

| プレフィックス | 最小幅 | CSSルール |
|---|---|---|
| *(なし — xs)* | 0 px | デフォルトスタイル |
| `sm` | 640 px | `@media (min-width: 640px)` |
| `md` | 768 px | `@media (min-width: 768px)` |
| `lg` | 1024 px | `@media (min-width: 1024px)` |
| `xl` | 1280 px | `@media (min-width: 1280px)` |
| `2xl` | 1536 px | `@media (min-width: 1536px)` |

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">Web制作の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、開発ツール費用の経費精算もクラウドで一元管理。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---
> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

**関連ツール:** 画面解像度 → [画面解像度チェッカー](/ja/tools/screen-resolution/) | メディアクエリ → [CSSメディアクエリジェネレーター](/ja/tools/media-query-generator/)
