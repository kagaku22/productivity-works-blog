---
title: "Screen Info & Display Tester"
date: 2025-05-16
description: "Free screen info and display tester. Check screen resolution, viewport, device pixel ratio, color depth, orientation, refresh rate, touch support, browser and OS info. Run color bar, grayscale, and dead pixel tests."
categories: ["Free Tools"]
tags: ["Lifestyle", "Converter", "Free Tools"]
slug: "screen-recorder-info"
ShowToc: false
aliases: ["/tools/viewport-tester/", "/tools/screen-resolution/"]
cover:
  image: "/images/covers/screen-recorder-info.png"
  alt: "Screen Info & Display Tester"
---

<div id="si-app">
<style>
#si-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
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
padding: 8px 16px;
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
#si-app .si-btn.danger {
border-color: #fca5a5;
color: #dc2626;
background: #fff5f5;
}
#si-app .si-btn.danger:hover {
background: #fee2e2;
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
#si-app .si-overlay-label {
position: fixed;
bottom: 24px;
left: 50%;
transform: translateX(-50%);
background: rgba(0,0,0,0.7);
color: #fff;
padding: 8px 20px;
border-radius: 30px;
font-size: 14px;
font-weight: 600;
pointer-events: none;
z-index: 1000000;
}
#si-app .si-colorbar {
display: flex;
height: 80px;
border-radius: 8px;
overflow: hidden;
margin-top: 8px;
}
#si-app .si-colorbar div {
flex: 1;
}
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

<button class="si-refresh-btn" onclick="siRefresh()">&#8635; Refresh Info</button>

<div class="si-card">
<div class="si-section-title">Screen & Display</div>
<div class="si-grid" id="si-screen-grid">
<div class="si-row"><span class="si-label">Screen Resolution</span><span class="si-value" id="si-res">—</span></div>
<div class="si-row"><span class="si-label">Viewport Size</span><span class="si-value" id="si-vp">—</span></div>
<div class="si-row"><span class="si-label">Device Pixel Ratio</span><span class="si-value" id="si-dpr">—</span></div>
<div class="si-row"><span class="si-label">Color Depth</span><span class="si-value" id="si-cd">—</span></div>
<div class="si-row"><span class="si-label">Orientation</span><span class="si-value" id="si-ori">—</span></div>
<div class="si-row"><span class="si-label">Touch Support</span><span class="si-value" id="si-touch">—</span></div>
</div>
</div>

<div class="si-card">
<div class="si-section-title">Browser & System</div>
<div class="si-grid">
<div class="si-row"><span class="si-label">Browser</span><span class="si-value" id="si-browser">—</span></div>
<div class="si-row"><span class="si-label">Operating System</span><span class="si-value" id="si-os">—</span></div>
<div class="si-row"><span class="si-label">Language</span><span class="si-value" id="si-lang">—</span></div>
<div class="si-row"><span class="si-label">Online Status</span><span class="si-value" id="si-online">—</span></div>
<div class="si-row"><span class="si-label">Cookies Enabled</span><span class="si-value" id="si-cookie">—</span></div>
<div class="si-row"><span class="si-label">Hardware Threads</span><span class="si-value" id="si-hw">—</span></div>
</div>
</div>

<div class="si-card">
<div class="si-section-title">Refresh Rate Estimation</div>
<div id="si-fps-label" style="font-size:13px;color:#64748b;">Click "Measure" to estimate your display refresh rate using requestAnimationFrame.</div>
<div class="si-fps-bar" id="si-fps-bar" style="display:none;">
<div class="si-fps-track"><div class="si-fps-fill" id="si-fps-fill" style="width:0%"></div></div>
<span style="font-size:15px;font-weight:800;color:#0f172a;min-width:60px;" id="si-fps-val">— Hz</span>
</div>
<div class="si-btn-row" style="margin-top:10px;">
<button class="si-btn" onclick="siMeasureFPS()">Measure Refresh Rate</button>
</div>
</div>

<div class="si-card">
<div class="si-section-title">Display Test Patterns</div>
<p style="font-size:13px;color:#64748b;margin:0 0 10px;">Click any test to go full-screen. Click anywhere on screen to exit.</p>
<div class="si-colorbar" id="si-preview-colorbar">
<div style="background:#fff"></div>
<div style="background:#ff0000"></div>
<div style="background:#00ff00"></div>
<div style="background:#0000ff"></div>
<div style="background:#ffff00"></div>
<div style="background:#ff00ff"></div>
<div style="background:#00ffff"></div>
<div style="background:#000"></div>
</div>
<div class="si-gray" id="si-preview-gray"></div>
<div class="si-btn-row" style="margin-top:12px;">
<button class="si-btn" onclick="siRunTest('colorbars')">Color Bars</button>
<button class="si-btn" onclick="siRunTest('grayscale')">Grayscale Gradient</button>
<button class="si-btn" onclick="siRunTest('black')">Dead Pixel (Black)</button>
<button class="si-btn" onclick="siRunTest('white')">Dead Pixel (White)</button>
<button class="si-btn" onclick="siRunTest('red')">Dead Pixel (Red)</button>
<button class="si-btn" onclick="siRunTest('green')">Dead Pixel (Green)</button>
<button class="si-btn" onclick="siRunTest('blue')">Dead Pixel (Blue)</button>
</div>
</div>

<div class="si-overlay" id="si-overlay" onclick="siCloseTest()">
<div class="si-overlay-label" id="si-overlay-label">Click anywhere to exit</div>
</div>

<script>
(function(){
function siDetectBrowser(ua) {
if (/Edg\//.test(ua)) return 'Microsoft Edge';
if (/OPR\/|Opera/.test(ua)) return 'Opera';
if (/Firefox\//.test(ua)) return 'Firefox';
if (/SamsungBrowser/.test(ua)) return 'Samsung Internet';
if (/Chrome\//.test(ua)) return 'Chrome';
if (/Safari\//.test(ua)) return 'Safari';
return 'Unknown';
}

function siDetectOS(ua) {
if (/Windows NT 10/.test(ua)) return 'Windows 10/11';
if (/Windows NT/.test(ua)) return 'Windows';
if (/Mac OS X/.test(ua)) return 'macOS';
if (/iPhone/.test(ua)) return 'iOS (iPhone)';
if (/iPad/.test(ua)) return 'iPadOS';
if (/Android/.test(ua)) return 'Android';
if (/Linux/.test(ua)) return 'Linux';
return 'Unknown';
}

window.siRefresh = function() {
const ua = navigator.userAgent;
document.getElementById('si-res').textContent = screen.width + ' × ' + screen.height + ' px';
document.getElementById('si-vp').textContent = window.innerWidth + ' × ' + window.innerHeight + ' px';
const dpr = window.devicePixelRatio || 1;
const dprEl = document.getElementById('si-dpr');
dprEl.textContent = dpr.toFixed(2) + 'x';
dprEl.className = 'si-value' + (dpr >= 2 ? ' good' : '');
document.getElementById('si-cd').textContent = (screen.colorDepth || '—') + '-bit';
const ori = screen.orientation ? screen.orientation.type : (window.innerWidth > window.innerHeight ? 'landscape' : 'portrait');
document.getElementById('si-ori').textContent = ori.charAt(0).toUpperCase() + ori.slice(1).replace('-primary','').replace('-secondary',' (secondary)');
const touch = navigator.maxTouchPoints > 0;
const touchEl = document.getElementById('si-touch');
touchEl.textContent = touch ? 'Yes (' + navigator.maxTouchPoints + ' points)' : 'No';
touchEl.className = 'si-value' + (touch ? ' good' : '');
document.getElementById('si-browser').textContent = siDetectBrowser(ua);
document.getElementById('si-os').textContent = siDetectOS(ua);
document.getElementById('si-lang').textContent = navigator.language || '—';
const onlineEl = document.getElementById('si-online');
onlineEl.textContent = navigator.onLine ? 'Online' : 'Offline';
onlineEl.className = 'si-value' + (navigator.onLine ? ' good' : ' warn');
const cookieEl = document.getElementById('si-cookie');
cookieEl.textContent = navigator.cookieEnabled ? 'Yes' : 'No';
cookieEl.className = 'si-value' + (navigator.cookieEnabled ? ' good' : ' warn');
document.getElementById('si-hw').textContent = navigator.hardwareConcurrency ? navigator.hardwareConcurrency + ' cores' : '—';
};

window.siMeasureFPS = function() {
const label = document.getElementById('si-fps-label');
const bar = document.getElementById('si-fps-bar');
const fill = document.getElementById('si-fps-fill');
const val = document.getElementById('si-fps-val');
label.textContent = 'Measuring... (hold on ~1 second)';
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
label.textContent = 'Estimated refresh rate: ' + fps + ' Hz' + (fps >= 120 ? ' (high refresh!)' : fps >= 60 ? ' (standard)' : ' (low)');
}
}
requestAnimationFrame(measure);
};

const TEST_STYLES = {
colorbars: `
display:flex;width:100%;height:100%;
`,
grayscale: 'background:linear-gradient(to right,#000 0%,#fff 100%);',
black: 'background:#000;',
white: 'background:#fff;',
red: 'background:#f00;',
green: 'background:#0f0;',
blue: 'background:#00f;'
};

const TEST_LABELS = {
colorbars: 'Color Bars — Click anywhere to exit',
grayscale: 'Grayscale Gradient — Click anywhere to exit',
black: 'Dead Pixel Test (Black) — Look for bright pixels — Click to exit',
white: 'Dead Pixel Test (White) — Look for dark pixels — Click to exit',
red: 'Dead Pixel Test (Red) — Click to exit',
green: 'Dead Pixel Test (Green) — Click to exit',
blue: 'Dead Pixel Test (Blue) — Click to exit'
};

const COLOR_BARS = ['#fff','#ff0','#0ff','#0f0','#f0f','#f00','#00f','#000'];

window.siRunTest = function(type) {
const overlay = document.getElementById('si-overlay');
const labelEl = document.getElementById('si-overlay-label');
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
lbl.className = 'si-overlay-label';
lbl.textContent = TEST_LABELS[type] || 'Click to exit';
lbl.style.cssText = 'position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,0.7);color:#fff;padding:8px 20px;border-radius:30px;font-size:14px;font-weight:600;pointer-events:none;z-index:1000000;';
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
const ori = screen.orientation ? screen.orientation.type : (window.innerWidth > window.innerHeight ? 'landscape' : 'portrait');
document.getElementById('si-ori').textContent = ori.charAt(0).toUpperCase() + ori.slice(1).replace('-primary','').replace('-secondary',' (secondary)');
});

siRefresh();
})();
</script>
</div>

> Check resolution → [Screen Resolution](/tools/screen-resolution/)
