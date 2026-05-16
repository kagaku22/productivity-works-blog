---
title: "タイムゾーン時計"
date: 2025-05-16
description: "無料のワールドクロックダッシュボード。複数タイムゾーンのリアルタイム時計を表示。都市の追加・削除、時差表示、昼夜インジケーター、12/24時間切り替え対応。"
categories: ["無料ツール"]
slug: "timezone-clock"
ShowToc: false
aliases: ["/ja/tools/world-time/"]
cover:
  image: "/images/covers/timezone-clock-ja.png"
  alt: "タイムゾーン時計ダッシュボード"
---

<div id="tzc-app">
<style>
#tzc-app {
  font-family: 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', -apple-system, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  color: #1e293b;
  box-sizing: border-box;
}
#tzc-app *, #tzc-app *::before, #tzc-app *::after {
  box-sizing: border-box;
}
#tzc-app h2 {
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 12px 0;
  color: #0f172a;
}
#tzc-app .tzc-topbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  align-items: center;
  margin-bottom: 16px;
}
#tzc-app .tzc-toggle {
  display: flex;
  background: #f1f5f9;
  border-radius: 8px;
  padding: 3px;
  gap: 2px;
}
#tzc-app .tzc-toggle button {
  padding: 5px 14px;
  border: none;
  background: transparent;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  color: #64748b;
  cursor: pointer;
  transition: background 0.15s, color 0.15s;
}
#tzc-app .tzc-toggle button.active {
  background: #fff;
  color: #1e293b;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}
#tzc-app .tzc-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 14px;
}
#tzc-app .tzc-preset-btn {
  padding: 5px 12px;
  background: #e0f2fe;
  color: #0369a1;
  border: 1.5px solid #bae6fd;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.15s;
}
#tzc-app .tzc-preset-btn:hover {
  background: #bae6fd;
}
#tzc-app .tzc-add-row {
  display: flex;
  gap: 8px;
  margin-bottom: 18px;
  flex-wrap: wrap;
}
#tzc-app .tzc-add-row select {
  flex: 1;
  min-width: 200px;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  color: #1e293b;
  background: #f8fafc;
}
#tzc-app .tzc-add-row button {
  padding: 9px 18px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.15s;
}
#tzc-app .tzc-add-row button:hover {
  background: #4f46e5;
}
#tzc-app .tzc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
  gap: 14px;
}
#tzc-app .tzc-card {
  background: #fff;
  border: 1.5px solid #e2e8f0;
  border-radius: 12px;
  padding: 16px 16px 14px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
  position: relative;
  transition: border-color 0.2s;
}
#tzc-app .tzc-card.day-card {
  border-color: #fde68a;
  background: linear-gradient(135deg, #fffbeb 0%, #fef9c3 100%);
}
#tzc-app .tzc-card.night-card {
  border-color: #818cf8;
  background: linear-gradient(135deg, #eef2ff 0%, #e0e7ff 100%);
}
#tzc-app .tzc-card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 8px;
}
#tzc-app .tzc-city-name {
  font-size: 14px;
  font-weight: 700;
  color: #0f172a;
}
#tzc-app .tzc-dn-icon {
  font-size: 18px;
  line-height: 1;
}
#tzc-app .tzc-time {
  font-size: 2rem;
  font-weight: 800;
  color: #1e293b;
  letter-spacing: -1px;
  line-height: 1.1;
  margin-bottom: 2px;
}
#tzc-app .tzc-date {
  font-size: 12px;
  color: #64748b;
  margin-bottom: 6px;
}
#tzc-app .tzc-diff {
  display: inline-block;
  font-size: 11px;
  font-weight: 600;
  padding: 2px 8px;
  border-radius: 20px;
  background: #f1f5f9;
  color: #475569;
}
#tzc-app .tzc-remove {
  position: absolute;
  top: 8px;
  right: 8px;
  width: 22px;
  height: 22px;
  background: #fee2e2;
  color: #dc2626;
  border: none;
  border-radius: 50%;
  font-size: 14px;
  line-height: 22px;
  text-align: center;
  cursor: pointer;
  display: none;
  font-weight: 700;
  padding: 0;
}
#tzc-app .tzc-card:hover .tzc-remove {
  display: block;
}
#tzc-app .tzc-empty {
  text-align: center;
  color: #94a3b8;
  padding: 30px 0;
  font-size: 14px;
}
@media (max-width: 480px) {
  #tzc-app .tzc-time { font-size: 1.6rem; }
  #tzc-app .tzc-grid { grid-template-columns: 1fr 1fr; }
}
</style>

<div class="tzc-topbar">
  <div class="tzc-toggle">
    <button id="tzc-btn-24" class="active" onclick="tzcSetFormat(24)">24時間</button>
    <button id="tzc-btn-12" onclick="tzcSetFormat(12)">12時間</button>
  </div>
  <span style="font-size:13px;color:#64748b;">あなたの現地時間には ⭐ が表示されます</span>
</div>

<div style="margin-bottom:8px;font-size:13px;font-weight:600;color:#475569;">主要都市を追加：</div>
<div class="tzc-presets">
  <button class="tzc-preset-btn" onclick="tzcAddPreset('ニューヨーク','America/New_York')">ニューヨーク</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('ロンドン','Europe/London')">ロンドン</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('東京','Asia/Tokyo')">東京</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('シドニー','Australia/Sydney')">シドニー</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('ドバイ','Asia/Dubai')">ドバイ</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('パリ','Europe/Paris')">パリ</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('シンガポール','Asia/Singapore')">シンガポール</button>
  <button class="tzc-preset-btn" onclick="tzcAddPreset('ロサンゼルス','America/Los_Angeles')">ロサンゼルス</button>
</div>

<div class="tzc-add-row">
  <select id="tzc-tz-select">
    <option value="">-- タイムゾーンを選択 --</option>
  </select>
  <button onclick="tzcAddFromSelect()">+ 追加</button>
</div>

<div class="tzc-grid" id="tzc-grid">
  <div class="tzc-empty" id="tzc-empty">上のプリセットまたはセレクターから時計を追加してください。</div>
</div>

<script>
(function(){
  const TZC_ZONES = [
    ["Africa/Cairo","アフリカ/カイロ"],["Africa/Johannesburg","アフリカ/ヨハネスブルク"],["Africa/Lagos","アフリカ/ラゴス"],
    ["Africa/Nairobi","アフリカ/ナイロビ"],["America/Anchorage","アメリカ/アンカレッジ"],["America/Bogota","アメリカ/ボゴタ"],
    ["America/Buenos_Aires","アメリカ/ブエノスアイレス"],["America/Chicago","アメリカ/シカゴ"],["America/Denver","アメリカ/デンバー"],
    ["America/Los_Angeles","アメリカ/ロサンゼルス"],["America/Mexico_City","アメリカ/メキシコシティ"],
    ["America/New_York","アメリカ/ニューヨーク"],["America/Sao_Paulo","アメリカ/サンパウロ"],
    ["America/Toronto","アメリカ/トロント"],["America/Vancouver","アメリカ/バンクーバー"],
    ["Asia/Bangkok","アジア/バンコク"],["Asia/Dubai","アジア/ドバイ"],["Asia/Hong_Kong","アジア/香港"],
    ["Asia/Jakarta","アジア/ジャカルタ"],["Asia/Karachi","アジア/カラチ"],["Asia/Kolkata","アジア/コルカタ"],
    ["Asia/Kuala_Lumpur","アジア/クアラルンプール"],["Asia/Manila","アジア/マニラ"],["Asia/Seoul","アジア/ソウル"],
    ["Asia/Shanghai","アジア/上海"],["Asia/Singapore","アジア/シンガポール"],["Asia/Taipei","アジア/台北"],
    ["Asia/Tehran","アジア/テヘラン"],["Asia/Tokyo","アジア/東京"],
    ["Australia/Adelaide","オーストラリア/アデレード"],["Australia/Brisbane","オーストラリア/ブリスベン"],
    ["Australia/Melbourne","オーストラリア/メルボルン"],["Australia/Perth","オーストラリア/パース"],
    ["Australia/Sydney","オーストラリア/シドニー"],
    ["Europe/Amsterdam","ヨーロッパ/アムステルダム"],["Europe/Athens","ヨーロッパ/アテネ"],
    ["Europe/Berlin","ヨーロッパ/ベルリン"],["Europe/Dublin","ヨーロッパ/ダブリン"],
    ["Europe/Helsinki","ヨーロッパ/ヘルシンキ"],["Europe/Istanbul","ヨーロッパ/イスタンブール"],
    ["Europe/London","ヨーロッパ/ロンドン"],["Europe/Madrid","ヨーロッパ/マドリード"],
    ["Europe/Moscow","ヨーロッパ/モスクワ"],["Europe/Paris","ヨーロッパ/パリ"],
    ["Europe/Rome","ヨーロッパ/ローマ"],["Europe/Zurich","ヨーロッパ/チューリッヒ"],
    ["Pacific/Auckland","太平洋/オークランド"],["Pacific/Honolulu","太平洋/ホノルル"],["UTC","UTC"]
  ];

  let tzcClocks = [];
  let tzcFormat = 24;
  let tzcTimer = null;
  const localTZ = Intl.DateTimeFormat().resolvedOptions().timeZone;

  const sel = document.getElementById('tzc-tz-select');
  TZC_ZONES.forEach(([tz, label]) => {
    const opt = document.createElement('option');
    opt.value = tz;
    opt.textContent = label;
    sel.appendChild(opt);
  });

  window.tzcSetFormat = function(f) {
    tzcFormat = f;
    document.getElementById('tzc-btn-24').classList.toggle('active', f === 24);
    document.getElementById('tzc-btn-12').classList.toggle('active', f === 12);
    tzcRender();
  };

  window.tzcAddPreset = function(city, tz) {
    if (tzcClocks.find(c => c.tz === tz)) return;
    tzcClocks.push({city, tz});
    tzcRender();
  };

  window.tzcAddFromSelect = function() {
    const s = document.getElementById('tzc-tz-select');
    if (!s.value) return;
    const tz = s.value;
    const city = s.options[s.selectedIndex].text;
    if (tzcClocks.find(c => c.tz === tz)) return;
    tzcClocks.push({city, tz});
    s.value = '';
    tzcRender();
  };

  window.tzcRemove = function(tz) {
    tzcClocks = tzcClocks.filter(c => c.tz !== tz);
    tzcRender();
  };

  function tzcGetLocalOffset() {
    const now = new Date();
    return -now.getTimezoneOffset();
  }

  function tzcGetZoneOffset(tz, now) {
    try {
      const utcStr = new Intl.DateTimeFormat('en-US', {timeZone:'UTC', hour:'2-digit', minute:'2-digit', hour12:false}).format(now);
      const tzStr = new Intl.DateTimeFormat('en-US', {timeZone:tz, hour:'2-digit', minute:'2-digit', hour12:false}).format(now);
      const [uh,um] = utcStr.split(':').map(Number);
      const [th,tm] = tzStr.split(':').map(Number);
      return (th - uh) * 60 + (tm - um);
    } catch(e) { return 0; }
  }

  function tzcFormatDiff(diffMin) {
    if (diffMin === 0) return 'あなたと同じ時間';
    const sign = diffMin > 0 ? '+' : '-';
    const abs = Math.abs(diffMin);
    const h = Math.floor(abs / 60);
    const m = abs % 60;
    return 'あなたより' + sign + h + (m ? ':' + String(m).padStart(2,'0') : '') + '時間';
  }

  function tzcIsDay(hour) {
    return hour >= 6 && hour < 20;
  }

  function tzcRender() {
    const grid = document.getElementById('tzc-grid');
    if (tzcClocks.length === 0) {
      grid.innerHTML = '<div class="tzc-empty">上のプリセットまたはセレクターから時計を追加してください。</div>';
      return;
    }
    const now = new Date();
    const localOffMin = tzcGetLocalOffset();

    grid.innerHTML = tzcClocks.map(({city, tz}) => {
      const isLocal = tz === localTZ;
      let timeStr, dateStr, hourNum;
      try {
        const opts12 = {timeZone:tz, hour:'numeric', minute:'2-digit', second:'2-digit', hour12:true};
        const opts24 = {timeZone:tz, hour:'2-digit', minute:'2-digit', second:'2-digit', hour12:false};
        timeStr = new Intl.DateTimeFormat('ja-JP', tzcFormat===12 ? opts12 : opts24).format(now);
        dateStr = new Intl.DateTimeFormat('ja-JP', {timeZone:tz, weekday:'short', month:'long', day:'numeric'}).format(now);
        const h = parseInt(new Intl.DateTimeFormat('en-US', {timeZone:tz, hour:'2-digit', hour12:false}).format(now));
        hourNum = h;
      } catch(e) {
        timeStr = '--:--';
        dateStr = '';
        hourNum = 12;
      }
      const day = tzcIsDay(hourNum);
      const dnIcon = day ? '☀️' : '🌙';
      const cardClass = day ? 'tzc-card day-card' : 'tzc-card night-card';
      const tzOff = tzcGetZoneOffset(tz, now);
      const diffMin = tzOff - localOffMin;
      const diffStr = isLocal ? '⭐ 現地時間' : tzcFormatDiff(diffMin);

      return `<div class="${cardClass}">
        <button class="tzc-remove" onclick="tzcRemove('${tz.replace(/'/g,"\\'")}')">&#x2715;</button>
        <div class="tzc-card-header">
          <div class="tzc-city-name">${city}${isLocal ? ' ⭐' : ''}</div>
          <div class="tzc-dn-icon">${dnIcon}</div>
        </div>
        <div class="tzc-time">${timeStr}</div>
        <div class="tzc-date">${dateStr}</div>
        <div class="tzc-diff">${diffStr}</div>
      </div>`;
    }).join('');
  }

  function tzcTick() {
    tzcRender();
    tzcTimer = setTimeout(tzcTick, 1000 - (Date.now() % 1000));
  }

  tzcAddPreset('現地時間', localTZ);
  tzcAddPreset('ニューヨーク', 'America/New_York');
  tzcAddPreset('ロンドン', 'Europe/London');
  tzcAddPreset('東京', 'Asia/Tokyo');
  tzcTick();
})();
</script>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

> タイムゾーン変換 → [タイムゾーン変換ツール](/ja/tools/timezone-converter/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。
