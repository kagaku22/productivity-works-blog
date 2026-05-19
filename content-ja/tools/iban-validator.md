---
title: "IBAN検証ツール - 国際銀行口座番号チェッカー"
date: 2025-11-18
description: "IBANの形式とチェックサムを無料で検証。全国対応。銀行コード・支店コード・口座番号を抽出。"
categories: ["無料ツール"]
slug: "iban-validator"
ShowToc: false
cover:
  image: "/images/covers/iban-validator.png"
  alt: "IBAN検証ツール"
---

<div id="iban-app">

<style>
#iban-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic UI", Meiryo, sans-serif;
max-width: 760px;
margin: 0 auto;
color: #1a1a2e;
}
#iban-app * { box-sizing: border-box; }
#iban-app h2 {
font-size: 1.2rem;
font-weight: 700;
color: #1a1a2e;
margin: 1.5rem 0 0.75rem;
}
#iban-app .iban-input-group {
display: flex;
gap: 0.5rem;
margin-bottom: 1rem;
}
#iban-app #iban-input {
flex: 1;
padding: 0.75rem 1rem;
font-size: 1.1rem;
font-family: "Courier New", Courier, monospace;
border: 2px solid #cbd5e1;
border-radius: 8px;
outline: none;
letter-spacing: 0.05em;
transition: border-color 0.2s;
text-transform: uppercase;
}
#iban-app #iban-input:focus { border-color: #3b82f6; }
#iban-app #iban-input.valid { border-color: #22c55e; }
#iban-app #iban-input.invalid { border-color: #ef4444; }
#iban-app .btn {
padding: 0.75rem 1.25rem;
font-size: 0.95rem;
font-weight: 600;
border: none;
border-radius: 8px;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
white-space: nowrap;
}
#iban-app .btn:active { transform: scale(0.97); }
#iban-app .btn-primary {
background: #3b82f6;
color: #fff;
}
#iban-app .btn-primary:hover { background: #2563eb; }
#iban-app .btn-clear {
background: #f1f5f9;
color: #64748b;
}
#iban-app .btn-clear:hover { background: #e2e8f0; }
#iban-app .result-box {
border-radius: 10px;
padding: 1.25rem 1.5rem;
margin-bottom: 1rem;
display: none;
}
#iban-app .result-box.visible { display: block; }
#iban-app .result-valid {
background: #f0fdf4;
border: 2px solid #22c55e;
}
#iban-app .result-invalid {
background: #fef2f2;
border: 2px solid #ef4444;
}
#iban-app .result-status {
font-size: 1.1rem;
font-weight: 700;
margin-bottom: 0.4rem;
}
#iban-app .result-valid .result-status { color: #16a34a; }
#iban-app .result-invalid .result-status { color: #dc2626; }
#iban-app .result-msg {
font-size: 0.93rem;
color: #475569;
line-height: 1.6;
}
#iban-app .details-grid {
display: none;
grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
gap: 0.75rem;
margin-top: 1.25rem;
}
#iban-app .details-grid.visible { display: grid; }
#iban-app .detail-card {
background: #f8fafc;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 0.75rem 1rem;
}
#iban-app .detail-label {
font-size: 0.72rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.05em;
color: #94a3b8;
margin-bottom: 0.25rem;
}
#iban-app .detail-value {
font-size: 0.97rem;
font-weight: 600;
color: #1e293b;
word-break: break-all;
}
#iban-app .detail-value.mono {
font-family: "Courier New", Courier, monospace;
font-size: 0.92rem;
}
#iban-app .country-flag { font-size: 1.3rem; margin-right: 0.3rem; }
#iban-app .examples-section { margin-top: 1.5rem; }
#iban-app .examples-label {
font-size: 0.83rem;
color: #64748b;
margin-bottom: 0.5rem;
}
#iban-app .example-chips {
display: flex;
flex-wrap: wrap;
gap: 0.4rem;
}
#iban-app .chip {
padding: 0.3rem 0.75rem;
background: #eff6ff;
border: 1px solid #bfdbfe;
border-radius: 999px;
font-size: 0.8rem;
font-family: "Courier New", Courier, monospace;
color: #1d4ed8;
cursor: pointer;
transition: background 0.15s;
}
#iban-app .chip:hover { background: #dbeafe; }
#iban-app table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
margin-top: 0.5rem;
}
#iban-app thead th {
background: #f1f5f9;
padding: 0.55rem 0.8rem;
text-align: left;
font-weight: 600;
color: #475569;
border-bottom: 2px solid #e2e8f0;
}
#iban-app tbody td {
padding: 0.5rem 0.8rem;
border-bottom: 1px solid #f1f5f9;
color: #334155;
}
#iban-app tbody tr:hover td { background: #f8fafc; }
#iban-app .cta-box {
margin-top: 2rem;
padding: 1.25rem 1.5rem;
background: linear-gradient(135deg, #eff6ff 0%, #f0fdf4 100%);
border: 1px solid #bfdbfe;
border-radius: 10px;
font-size: 0.93rem;
color: #1e3a5f;
line-height: 1.7;
}
#iban-app .cta-box strong {
display: block;
font-size: 1rem;
margin-bottom: 0.4rem;
color: #1d4ed8;
}
#iban-app .cta-box a {
color: #2563eb;
font-weight: 600;
}
@media (max-width: 520px) {
#iban-app .iban-input-group { flex-direction: column; }
#iban-app .btn { width: 100%; }
}
</style>

<h2>IBAN番号を入力してください</h2>

<div class="iban-input-group">
<input
id="iban-input"
type="text"
placeholder="例: DE89 3704 0044 0532 0130 00"
maxlength="42"
autocomplete="off"
spellcheck="false"
/>
<button class="btn btn-primary" onclick="ibanValidate()">検証する</button>
<button class="btn btn-clear" onclick="ibanClear()">クリア</button>
</div>

<div id="iban-result" class="result-box"></div>

<div id="iban-details" class="details-grid"></div>

<div class="examples-section">
<div class="examples-label">サンプルで試す:</div>
<div class="example-chips">
<span class="chip" onclick="ibanSetExample('DE89370400440532013000')">DE（ドイツ）</span>
<span class="chip" onclick="ibanSetExample('GB29NWBK60161331926819')">GB（イギリス）</span>
<span class="chip" onclick="ibanSetExample('FR7630006000011234567890189')">FR（フランス）</span>
<span class="chip" onclick="ibanSetExample('ES9121000418450200051332')">ES（スペイン）</span>
<span class="chip" onclick="ibanSetExample('IT60X0542811101000000123456')">IT（イタリア）</span>
<span class="chip" onclick="ibanSetExample('NL91ABNA0417164300')">NL（オランダ）</span>
<span class="chip" onclick="ibanSetExample('BE68539007547034')">BE（ベルギー）</span>
<span class="chip" onclick="ibanSetExample('AT611904300234573201')">AT（オーストリア）</span>
<span class="chip" onclick="ibanSetExample('CH9300762011623852957')">CH（スイス）</span>
<span class="chip" onclick="ibanSetExample('IE29AIBK93115212345678')">IE（アイルランド）</span>
<span class="chip" onclick="ibanSetExample('DE00370400440532013000')">無効チェックサム</span>
</div>
</div>

<h2>国別IBANの桁数一覧</h2>

<table>
<thead>
<tr>
<th>国旗</th>
<th>国名</th>
<th>コード</th>
<th>桁数</th>
<th>フォーマット</th>
</tr>
</thead>
<tbody id="iban-country-table"></tbody>
</table>

<div class="cta-box">
<strong>海外送金・外貨取引の管理を効率化しませんか？</strong>
IBANを使った国際送金の記帳・為替差損益の自動計算は freee会計 が便利です。<br>
> 海外送金の管理を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee会計で外貨取引を自動管理</a>
</div>

<script>
(function() {
const COUNTRIES = [
{ code: "AD", name: "アンドラ",           flag: "🇦🇩", length: 24, format: "ADkk BBBB SSSS CCCC CCCC CCCC",  bankLen: 4, branchLen: 4 },
{ code: "AT", name: "オーストリア",        flag: "🇦🇹", length: 20, format: "ATkk BBBB BCCC CCCC CCCC",        bankLen: 5, branchLen: 0 },
{ code: "BE", name: "ベルギー",            flag: "🇧🇪", length: 16, format: "BEkk BBBC CCCC CCXX",             bankLen: 3, branchLen: 0 },
{ code: "CH", name: "スイス",              flag: "🇨🇭", length: 21, format: "CHkk BBBB BCCC CCCC CCCC C",      bankLen: 5, branchLen: 0 },
{ code: "CY", name: "キプロス",            flag: "🇨🇾", length: 28, format: "CYkk BBBS SSSS CCCC CCCC CCCC CCCC", bankLen: 3, branchLen: 5 },
{ code: "CZ", name: "チェコ",              flag: "🇨🇿", length: 24, format: "CZkk BBBB SSSS SSCC CCCC CCCC",   bankLen: 4, branchLen: 6 },
{ code: "DE", name: "ドイツ",              flag: "🇩🇪", length: 22, format: "DEkk BBBB BBBB CCCC CCCC CC",     bankLen: 8, branchLen: 0 },
{ code: "DK", name: "デンマーク",          flag: "🇩🇰", length: 18, format: "DKkk BBBB CCCC CCCC CC",          bankLen: 4, branchLen: 0 },
{ code: "EE", name: "エストニア",          flag: "🇪🇪", length: 20, format: "EEkk BBSS CCCC CCCC CCCK",        bankLen: 2, branchLen: 2 },
{ code: "ES", name: "スペイン",            flag: "🇪🇸", length: 24, format: "ESkk BBBB SSSS KKCC CCCC CCCC",   bankLen: 4, branchLen: 4 },
{ code: "FI", name: "フィンランド",        flag: "🇫🇮", length: 18, format: "FIkk BBBB BBCC CCCC CK",          bankLen: 6, branchLen: 0 },
{ code: "FR", name: "フランス",            flag: "🇫🇷", length: 27, format: "FRkk BBBB BSSS SSCC CCCC CCCC CKK", bankLen: 5, branchLen: 5 },
{ code: "GB", name: "イギリス",            flag: "🇬🇧", length: 22, format: "GBkk BBBB SSSS SSCC CCCC CC",     bankLen: 4, branchLen: 6 },
{ code: "GR", name: "ギリシャ",            flag: "🇬🇷", length: 27, format: "GRkk BBBS SSSC CCCC CCCC CCCC CCC", bankLen: 3, branchLen: 4 },
{ code: "HR", name: "クロアチア",          flag: "🇭🇷", length: 21, format: "HRkk BBBB BBBC CCCC CCCC C",      bankLen: 7, branchLen: 0 },
{ code: "HU", name: "ハンガリー",          flag: "🇭🇺", length: 28, format: "HUkk BBBS SSSK CCCC CCCC CCCC CCCK", bankLen: 3, branchLen: 4 },
{ code: "IE", name: "アイルランド",        flag: "🇮🇪", length: 22, format: "IEkk AAAA BBBB BBCC CCCC CC",     bankLen: 4, branchLen: 6 },
{ code: "IT", name: "イタリア",            flag: "🇮🇹", length: 27, format: "ITkk KBBB BBSS SSSC CCCC CCCC CCC", bankLen: 5, branchLen: 5 },
{ code: "LT", name: "リトアニア",          flag: "🇱🇹", length: 20, format: "LTkk BBBB BCCC CCCC CCCC",        bankLen: 5, branchLen: 0 },
{ code: "LU", name: "ルクセンブルク",      flag: "🇱🇺", length: 20, format: "LUkk BBBС CCCC CCCC CCCC",        bankLen: 3, branchLen: 0 },
{ code: "LV", name: "ラトビア",            flag: "🇱🇻", length: 21, format: "LVkk BBBB CCCC CCCC CCCC C",      bankLen: 4, branchLen: 0 },
{ code: "MT", name: "マルタ",              flag: "🇲🇹", length: 31, format: "MTkk BBBB SSSS SCCC CCCC CCCC CCCC CCC", bankLen: 4, branchLen: 5 },
{ code: "NL", name: "オランダ",            flag: "🇳🇱", length: 18, format: "NLkk BBBB CCCC CCCC CC",          bankLen: 4, branchLen: 0 },
{ code: "NO", name: "ノルウェー",          flag: "🇳🇴", length: 15, format: "NOkk BBBB CCCC CCK",              bankLen: 4, branchLen: 0 },
{ code: "PL", name: "ポーランド",          flag: "🇵🇱", length: 28, format: "PLkk BBBS SSSK CCCC CCCC CCCC CCCC", bankLen: 3, branchLen: 4 },
{ code: "PT", name: "ポルトガル",          flag: "🇵🇹", length: 25, format: "PTkk BBBB SSSS CCCC CCCC CCCK K",  bankLen: 4, branchLen: 4 },
{ code: "RO", name: "ルーマニア",          flag: "🇷🇴", length: 24, format: "ROkk BBBB CCCC CCCC CCCC CCCC",   bankLen: 4, branchLen: 0 },
{ code: "SE", name: "スウェーデン",        flag: "🇸🇪", length: 24, format: "SEkk BBBC CCCC CCCC CCCC CCCK",   bankLen: 3, branchLen: 0 },
{ code: "SI", name: "スロベニア",          flag: "🇸🇮", length: 19, format: "SIkk BBSS SCCC CCCC CKK",         bankLen: 2, branchLen: 3 },
{ code: "SK", name: "スロバキア",          flag: "🇸🇰", length: 24, format: "SKkk BBBB SSSS SSCC CCCC CCCC",   bankLen: 4, branchLen: 6 },
];

function buildTable() {
const tbody = document.getElementById("iban-country-table");
COUNTRIES.forEach(c => {
const tr = document.createElement("tr");
tr.innerHTML = `<td>${c.flag}</td><td>${c.name}</td><td><code>${c.code}</code></td><td>${c.length}桁</td><td style="font-family:monospace;font-size:0.78rem;">${c.format}</td>`;
tbody.appendChild(tr);
});
}

function getCountry(code) {
return COUNTRIES.find(c => c.code === code.toUpperCase()) || null;
}

function mod97(iban) {
const rearranged = iban.slice(4) + iban.slice(0, 4);
const numeric = rearranged.split("").map(ch => {
const code = ch.charCodeAt(0);
return code >= 65 && code <= 90 ? String(code - 55) : ch;
}).join("");
let remainder = 0;
for (let i = 0; i < numeric.length; i++) {
remainder = (remainder * 10 + parseInt(numeric[i], 10)) % 97;
}
return remainder;
}

function formatIban(raw) {
return raw.replace(/(.{4})/g, "$1 ").trim();
}

function extractDetails(iban, country) {
const bban = iban.slice(4);
const bankCode = country ? bban.slice(0, country.bankLen) : "";
const branchCode = country && country.branchLen > 0 ? bban.slice(country.bankLen, country.bankLen + country.branchLen) : "";
const accountStart = country ? country.bankLen + country.branchLen : 4;
const accountNum = bban.slice(accountStart);
return { bankCode, branchCode, accountNum };
}

window.ibanValidate = function() {
const raw = document.getElementById("iban-input").value.replace(/\s+/g, "").toUpperCase();
const input = document.getElementById("iban-input");
const resultBox = document.getElementById("iban-result");
const detailsGrid = document.getElementById("iban-details");

if (!raw) {
resultBox.className = "result-box result-invalid visible";
resultBox.innerHTML = `<div class="result-status">&#10007; 入力がありません</div><div class="result-msg">IBAN番号を入力してから「検証する」を押してください。</div>`;
input.className = "invalid";
detailsGrid.className = "details-grid";
return;
}

if (!/^[A-Z]{2}[0-9]{2}[A-Z0-9]+$/.test(raw)) {
resultBox.className = "result-box result-invalid visible";
resultBox.innerHTML = `<div class="result-status">&#10007; フォーマットエラー</div><div class="result-msg">IBANは2文字の国コード、2桁のチェックデジット、英数字で構成されます。入力内容を確認してください。</div>`;
input.className = "invalid";
detailsGrid.className = "details-grid";
return;
}

const countryCode = raw.slice(0, 2);
const checkDigits = raw.slice(2, 4);
const country = getCountry(countryCode);

if (country && raw.length !== country.length) {
resultBox.className = "result-box result-invalid visible";
resultBox.innerHTML = `<div class="result-status">&#10007; 桁数エラー</div><div class="result-msg">${country.flag} ${country.name}のIBANは正確に${country.length}桁必要です。入力は${raw.length}桁です。</div>`;
input.className = "invalid";
detailsGrid.className = "details-grid";
return;
}

const remainder = mod97(raw);
if (remainder !== 1) {
resultBox.className = "result-box result-invalid visible";
resultBox.innerHTML = `<div class="result-status">&#10007; チェックサムエラー</div><div class="result-msg">MOD 97検算に失敗しました（結果: ${remainder}、期待値: 1）。入力ミスまたはチェックデジットの誤りが考えられます。</div>`;
input.className = "invalid";
detailsGrid.className = "details-grid";
return;
}

// Valid
input.className = "valid";
const flagHtml = country ? `<span class="country-flag">${country.flag}</span>` : "";
const countryName = country ? country.name : "不明な国";
resultBox.className = "result-box result-valid visible";
resultBox.innerHTML = `<div class="result-status">&#10003; 有効なIBANです</div><div class="result-msg">${flagHtml}${countryName} &mdash; チェックサム検証済み（MOD 97 = 1）。フォーマット済み: <strong style="font-family:monospace">${formatIban(raw)}</strong></div>`;

const { bankCode, branchCode, accountNum } = extractDetails(raw, country);

const cards = [
{ label: "国", value: `${country ? country.flag + " " : ""}${countryName}` },
{ label: "国コード", value: countryCode, mono: true },
{ label: "チェックデジット", value: checkDigits, mono: true },
{ label: "IBAN（整形済み）", value: formatIban(raw), mono: true },
{ label: "BBAN", value: raw.slice(4), mono: true },
];
if (bankCode) cards.push({ label: "銀行コード", value: bankCode, mono: true });
if (branchCode) cards.push({ label: "支店コード", value: branchCode, mono: true });
if (accountNum) cards.push({ label: "口座番号部分", value: accountNum, mono: true });
if (country) cards.push({ label: "IBAN桁数", value: `${country.length}桁` });

detailsGrid.innerHTML = cards.map(c =>
`<div class="detail-card"><div class="detail-label">${c.label}</div><div class="detail-value${c.mono ? " mono" : ""}">${c.value}</div></div>`
).join("");
detailsGrid.className = "details-grid visible";
};

window.ibanClear = function() {
const input = document.getElementById("iban-input");
input.value = "";
input.className = "";
document.getElementById("iban-result").className = "result-box";
document.getElementById("iban-details").className = "details-grid";
input.focus();
};

window.ibanSetExample = function(val) {
const input = document.getElementById("iban-input");
input.value = val;
input.className = "";
ibanValidate();
};

document.getElementById("iban-input").addEventListener("input", function() {
const raw = this.value.replace(/\s+/g, "").toUpperCase();
const formatted = raw.replace(/(.{4})(?=.)/g, "$1 ");
if (this.value !== formatted) this.value = formatted;
this.className = "";
document.getElementById("iban-result").className = "result-box";
document.getElementById("iban-details").className = "details-grid";
});

document.getElementById("iban-input").addEventListener("keydown", function(e) {
if (e.key === "Enter") ibanValidate();
});

buildTable();
})();
</script>

</div>
