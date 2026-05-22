---
title: "色覚シミュレーター"
date: 2025-09-29
description: "無料の色覚シミュレーター。プロタノピア・デュータノピア・トリタノピアなど8種類の色覚特性で色がどう見えるかを確認。アクセシビリティ対策に。"
categories: ["無料ツール"]
tags: ["CSS", "Webデザイン", "無料ツール"]
slug: "color-blindness-simulator"
ShowToc: false
cover:
  image: "/images/covers/color-blindness-simulator-ja.png"
  alt: "色覚シミュレーター"
---

デザインや配色が色覚特性を持つ方にどう見えるか、8種類のシミュレーションで即確認。Webデザイン・UI・データビジュアライゼーションのアクセシビリティ改善に。

<div id="cb-app">

<style>
#cb-app {
font-family: system-ui, -apple-system, sans-serif;
max-width: 860px;
margin: 0 auto;
color: #1e293b;
}
#cb-app * { box-sizing: border-box; }

#cb-app h2 {
font-size: 1.15rem;
font-weight: 700;
margin: 28px 0 12px;
color: #0f172a;
border-left: 4px solid #6366f1;
padding-left: 10px;
}

#cb-app .cb-input-row {
display: flex;
flex-wrap: wrap;
gap: 10px;
align-items: center;
margin-bottom: 18px;
}

#cb-app .cb-color-entry {
display: flex;
align-items: center;
gap: 8px;
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
padding: 8px 12px;
}

#cb-app .cb-color-entry input[type="color"] {
width: 40px;
height: 36px;
border: none;
border-radius: 6px;
cursor: pointer;
padding: 0;
background: none;
}

#cb-app .cb-color-entry input[type="text"] {
width: 110px;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
padding: 6px 10px;
font-size: 0.9rem;
font-family: monospace;
color: #334155;
}

#cb-app .cb-color-entry input[type="text"]:focus {
outline: none;
border-color: #6366f1;
}

#cb-app .cb-remove-btn {
background: none;
border: none;
color: #94a3b8;
cursor: pointer;
font-size: 1.1rem;
padding: 2px 4px;
border-radius: 4px;
line-height: 1;
}
#cb-app .cb-remove-btn:hover { color: #ef4444; background: #fee2e2; }

#cb-app .cb-btn {
padding: 9px 18px;
border-radius: 8px;
border: none;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
}
#cb-app .cb-btn:active { transform: scale(0.97); }

#cb-app .cb-btn-primary {
background: #6366f1;
color: #fff;
}
#cb-app .cb-btn-primary:hover { background: #4f46e5; }

#cb-app .cb-btn-secondary {
background: #e0e7ff;
color: #4338ca;
}
#cb-app .cb-btn-secondary:hover { background: #c7d2fe; }

#cb-app .cb-btn-row {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 24px;
}

#cb-app .cb-results-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
gap: 20px;
margin-bottom: 32px;
}

#cb-app .cb-palette-block {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px;
}

#cb-app .cb-palette-label {
font-size: 0.8rem;
font-weight: 600;
color: #64748b;
margin-bottom: 10px;
text-transform: uppercase;
letter-spacing: 0.05em;
}

#cb-app .cb-swatches {
display: flex;
flex-wrap: wrap;
gap: 8px;
}

#cb-app .cb-swatch-item {
display: flex;
flex-direction: column;
align-items: center;
gap: 4px;
}

#cb-app .cb-swatch {
width: 56px;
height: 56px;
border-radius: 8px;
border: 1px solid rgba(0,0,0,0.1);
box-shadow: 0 1px 3px rgba(0,0,0,0.08);
}

#cb-app .cb-swatch-hex {
font-size: 0.7rem;
font-family: monospace;
color: #475569;
}

#cb-app .cb-type-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 6px;
}

#cb-app .cb-type-name {
font-size: 0.95rem;
font-weight: 700;
color: #1e293b;
}

#cb-app .cb-type-stat {
font-size: 0.78rem;
color: #64748b;
background: #e2e8f0;
border-radius: 99px;
padding: 2px 8px;
}

#cb-app .cb-type-desc {
font-size: 0.82rem;
color: #64748b;
margin-bottom: 10px;
}

#cb-app .cb-tips {
background: #f0fdf4;
border: 1.5px solid #bbf7d0;
border-radius: 10px;
padding: 16px 20px;
margin-top: 8px;
}

#cb-app .cb-tips h3 {
font-size: 1rem;
font-weight: 700;
color: #15803d;
margin: 0 0 10px;
}

#cb-app .cb-tips ul {
margin: 0;
padding-left: 20px;
color: #166534;
font-size: 0.88rem;
line-height: 1.8;
}

#cb-app .cb-stats-table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
margin-bottom: 12px;
}

#cb-app .cb-stats-table th {
background: #f1f5f9;
padding: 8px 12px;
text-align: left;
font-weight: 600;
color: #475569;
border-bottom: 2px solid #e2e8f0;
}

#cb-app .cb-stats-table td {
padding: 8px 12px;
border-bottom: 1px solid #f1f5f9;
color: #334155;
}

#cb-app .cb-stats-table tr:hover td { background: #f8fafc; }

#cb-app .cb-error {
color: #dc2626;
font-size: 0.85rem;
margin-top: 4px;
}

#cb-app .cb-notice {
background: #fefce8;
border: 1.5px solid #fde68a;
border-radius: 8px;
padding: 10px 14px;
font-size: 0.85rem;
color: #92400e;
margin-bottom: 16px;
}

@media (max-width: 600px) {
#cb-app .cb-results-grid { grid-template-columns: 1fr; }
#cb-app .cb-swatch { width: 44px; height: 44px; }
}
</style>

<h2>色を入力</h2>

<div id="cb-color-list"></div>

<div class="cb-btn-row">
<button class="cb-btn cb-btn-secondary" onclick="cbAddColor()">+ 色を追加（最大5色）</button>
<button class="cb-btn cb-btn-primary" onclick="cbSimulate()">シミュレーション実行</button>
<button class="cb-btn cb-btn-secondary" onclick="cbReset()">リセット</button>
</div>

<div id="cb-error" class="cb-error" style="display:none;"></div>

<h2>シミュレーション結果</h2>
<div class="cb-notice">色はVienot/Brettelアルゴリズムによる近似値です。医学的な診断基準ではなく、視覚的な参考としてご利用ください。</div>
<div id="cb-results" class="cb-results-grid"></div>

<h2>アクセシビリティのヒント</h2>
<div class="cb-tips">
<h3>色覚特性に配慮したデザインのポイント</h3>
<ul>
<li>色だけで情報を伝えない — ラベル・アイコン・パターンを併用する。</li>
<li>隣接する色のコントラスト比をWCAG AA基準（テキスト4.5:1以上）に保つ。</li>
<li>グラフやUIの主な区別に赤と緑の組み合わせだけを使わない。</li>
<li>データビジュアライゼーションにはOkabe-Ito・IBM Carbonなどのカラーブラインドフレンドリーパレットを使う。</li>
<li>色コードに加えてテクスチャやパターンをグラフに使用する。</li>
<li>色によって表現された情報には代替テキストを提供する。</li>
<li>実際にシミュレーターで確認してからリリースする習慣をつける。</li>
</ul>
</div>

<h2>色覚特性の統計</h2>
<table class="cb-stats-table">
<thead>
<tr>
<th>種類</th>
<th>説明</th>
<th>推定割合</th>
</tr>
</thead>
<tbody>
<tr><td>デュータノピア (Deuteranopia)</td><td>緑錐体なし（赤緑型）</td><td>男性の約1%</td></tr>
<tr><td>プロタノピア (Protanopia)</td><td>赤錐体なし（赤緑型）</td><td>男性の約1%</td></tr>
<tr><td>デュータノマリー (Deuteranomaly)</td><td>緑錐体がずれ（最多）</td><td>男性の約5%</td></tr>
<tr><td>プロタノマリー (Protanomaly)</td><td>赤錐体がずれ</td><td>男性の約1%</td></tr>
<tr><td>トリタノピア (Tritanopia)</td><td>青錐体なし（青黄型）</td><td>約0.003%</td></tr>
<tr><td>トリタノマリー (Tritanomaly)</td><td>青錐体がずれ</td><td>約0.01%</td></tr>
<tr><td>アクロマトプシア (Achromatopsia)</td><td>完全色盲</td><td>約0.003%</td></tr>
<tr><td>アクロマトマリー (Achromatomaly)</td><td>色覚が著しく低下</td><td>まれ</td></tr>
</tbody>
</table>
<p style="font-size:0.82rem;color:#64748b;">出典：Colour Blind Awareness。赤緑型はX染色体連鎖のため男性に多く、男性全体の約8%・女性の約0.5%が何らかの色覚特性を持つとされています。</p>

<script>
(function() {
const TYPES = [
{
id: 'original',
name: '元の色',
desc: '入力した色そのまま。',
stat: '—',
matrix: null
},
{
id: 'protanopia',
name: 'プロタノピア',
desc: '赤錐体なし。赤が暗く見え、赤と緑の区別が困難。',
stat: '男性の約1%',
matrix: [
0.152286, 1.052583, -0.204868,
0.114503, 0.786281,  0.099216,
-0.003882,-0.048116,  1.051998
]
},
{
id: 'deuteranopia',
name: 'デュータノピア',
desc: '緑錐体なし。赤緑色覚異常の中で最も一般的。',
stat: '男性の約1%',
matrix: [
0.367322, 0.860646, -0.227968,
0.280085, 0.672501,  0.047413,
-0.011820, 0.042940,  0.968881
]
},
{
id: 'tritanopia',
name: 'トリタノピア',
desc: '青錐体なし。青と黄色の区別が困難。',
stat: '約0.003%',
matrix: [
1.255528,-0.076749,-0.178779,
-0.078411, 0.930809, 0.147602,
0.004733, 0.691367, 0.303900
]
},
{
id: 'protanomaly',
name: 'プロタノマリー',
desc: '赤錐体がずれ。プロタノピアの軽症型。',
stat: '男性の約1%',
matrix: [
0.458064, 0.679578,-0.137642,
0.092785, 0.846313, 0.060902,
-0.007494,-0.016807, 1.024301
]
},
{
id: 'deuteranomaly',
name: 'デュータノマリー',
desc: '緑錐体がずれ。最も多く見られる色覚特性。',
stat: '男性の約5%',
matrix: [
0.547494, 0.607765,-0.155259,
0.181692, 0.781202, 0.037106,
-0.010410, 0.027275, 0.983135
]
},
{
id: 'tritanomaly',
name: 'トリタノマリー',
desc: '青錐体がずれ。軽度の青黄色覚異常。',
stat: '約0.01%',
matrix: [
1.017277,-0.006113,-0.011164,
-0.006561, 0.971381, 0.035180,
0.002183, 0.357817, 0.640000
]
},
{
id: 'achromatopsia',
name: 'アクロマトプシア',
desc: '完全色盲。明暗のみ知覚し、色の区別がない。',
stat: '約0.003%',
matrix: null
},
{
id: 'achromatomaly',
name: 'アクロマトマリー',
desc: '色覚が著しく低下。色の識別が大幅に制限される。',
stat: 'まれ',
matrix: null
}
];

function toLinear(c) {
const v = c / 255;
return v <= 0.04045 ? v / 12.92 : Math.pow((v + 0.055) / 1.055, 2.4);
}
function toSRGB(v) {
const c = v <= 0.0031308 ? 12.92 * v : 1.055 * Math.pow(v, 1/2.4) - 0.055;
return Math.min(255, Math.max(0, Math.round(c * 255)));
}
function applyMatrix(r, g, b, m) {
return [
m[0]*r + m[1]*g + m[2]*b,
m[3]*r + m[4]*g + m[5]*b,
m[6]*r + m[7]*g + m[8]*b
];
}
function hexToRgb(hex) {
hex = hex.replace(/^#/, '');
if (hex.length === 3) hex = hex.split('').map(c => c+c).join('');
const n = parseInt(hex, 16);
return [(n >> 16) & 255, (n >> 8) & 255, n & 255];
}
function rgbToHex(r, g, b) {
return '#' + [r, g, b].map(v => v.toString(16).padStart(2, '0')).join('');
}
function parseColorInput(val) {
val = val.trim();
if (/^#?[0-9a-fA-F]{3,6}$/.test(val)) {
val = val.startsWith('#') ? val : '#' + val;
if (val.length === 4) val = '#' + val[1]+val[1]+val[2]+val[2]+val[3]+val[3];
return val.toLowerCase();
}
const m = val.match(/rgb\s*\(\s*(\d+)\s*,\s*(\d+)\s*,\s*(\d+)\s*\)/i);
if (m) return rgbToHex(+m[1], +m[2], +m[3]);
return null;
}

function simulateColor(hexColor, typeId) {
const [r, g, b] = hexToRgb(hexColor);
if (typeId === 'original') return hexColor;
const lr = toLinear(r);
const lg = toLinear(g);
const lb = toLinear(b);
let or, og, ob;
if (typeId === 'achromatopsia') {
const lum = 0.2126 * lr + 0.7152 * lg + 0.0722 * lb;
or = og = ob = lum;
} else if (typeId === 'achromatomaly') {
const lum = 0.2126 * lr + 0.7152 * lg + 0.0722 * lb;
or = 0.618 * lum + 0.382 * lr;
og = 0.618 * lum + 0.382 * lg;
ob = 0.618 * lum + 0.382 * lb;
} else {
const t = TYPES.find(t => t.id === typeId);
if (!t || !t.matrix) return hexColor;
[or, og, ob] = applyMatrix(lr, lg, lb, t.matrix);
}
or = Math.min(1, Math.max(0, or));
og = Math.min(1, Math.max(0, og));
ob = Math.min(1, Math.max(0, ob));
return rgbToHex(toSRGB(or), toSRGB(og), toSRGB(ob));
}

let colors = ['#3b82f6'];

function renderInputs() {
const list = document.getElementById('cb-color-list');
list.innerHTML = '';
colors.forEach((c, i) => {
const row = document.createElement('div');
row.className = 'cb-input-row';
row.innerHTML = `
<div class="cb-color-entry">
<input type="color" value="${c}" id="cb-pick-${i}" oninput="cbPickChange(${i}, this.value)" />
<input type="text" value="${c}" id="cb-hex-${i}" placeholder="#rrggbb または rgb()" onchange="cbTextChange(${i}, this.value)" onkeyup="cbTextChange(${i}, this.value)" />
${colors.length > 1 ? `<button class="cb-remove-btn" onclick="cbRemove(${i})" title="削除">&#x2715;</button>` : ''}
</div>
`;
list.appendChild(row);
});
}

window.cbPickChange = function(i, val) {
colors[i] = val;
const txtEl = document.getElementById('cb-hex-' + i);
if (txtEl) txtEl.value = val;
};

window.cbTextChange = function(i, val) {
const parsed = parseColorInput(val);
if (parsed) {
colors[i] = parsed;
const pickEl = document.getElementById('cb-pick-' + i);
if (pickEl) pickEl.value = parsed;
}
};

window.cbAddColor = function() {
if (colors.length >= 5) return;
colors.push('#e11d48');
renderInputs();
};

window.cbRemove = function(i) {
colors.splice(i, 1);
renderInputs();
};

window.cbReset = function() {
colors = ['#3b82f6'];
renderInputs();
document.getElementById('cb-results').innerHTML = '';
document.getElementById('cb-error').style.display = 'none';
};

window.cbSimulate = function() {
const errEl = document.getElementById('cb-error');
errEl.style.display = 'none';
colors = colors.map((c, i) => {
const el = document.getElementById('cb-hex-' + i);
return el ? (parseColorInput(el.value) || c) : c;
});
const parsed = colors.map(c => parseColorInput(c));
const bad = parsed.findIndex(p => !p);
if (bad !== -1) {
errEl.textContent = `色 ${bad + 1} が有効なhexまたはrgb値ではありません。`;
errEl.style.display = 'block';
return;
}
const validColors = parsed;
const resultsEl = document.getElementById('cb-results');
resultsEl.innerHTML = '';
TYPES.forEach(type => {
const simColors = validColors.map(c => simulateColor(c, type.id));
const block = document.createElement('div');
block.className = 'cb-palette-block';
const header = document.createElement('div');
header.className = 'cb-type-header';
header.innerHTML = `
<span class="cb-type-name">${type.name}</span>
<span class="cb-type-stat">${type.stat}</span>
`;
block.appendChild(header);
const desc = document.createElement('div');
desc.className = 'cb-type-desc';
desc.textContent = type.desc;
block.appendChild(desc);
const swatches = document.createElement('div');
swatches.className = 'cb-swatches';
simColors.forEach((sc) => {
const item = document.createElement('div');
item.className = 'cb-swatch-item';
item.innerHTML = `
<div class="cb-swatch" style="background:${sc};" title="${sc}"></div>
<span class="cb-swatch-hex">${sc}</span>
`;
swatches.appendChild(item);
});
block.appendChild(swatches);
resultsEl.appendChild(block);
});
};

renderInputs();
cbSimulate();
})();
</script>

</div>

<div class="cb-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">アクセシブルなWeb制作の経費管理も</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、デザインツール・制作費用の経費精算もクラウドで一元管理。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

> コントラスト比を確認 → [カラーコントラストチェッカー](/ja/tools/color-contrast-checker/)

> 色を変換 → [カラーコンバーター](/ja/tools/color-converter/)

> パレットを生成 → [カラーパレットジェネレーター](/ja/tools/color-palette-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
