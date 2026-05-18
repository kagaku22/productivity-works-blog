---
title: "電話番号フォーマッター - 電話番号の書式変換＆検証"
date: 2025-11-29
description: "電話番号を国際形式・国内形式・E.164形式に変換。各国の電話番号を検証し、一括フォーマットにも対応。"
categories: ["無料ツール"]
slug: "phone-formatter"
ShowToc: false
cover:
  image: "/images/covers/phone-formatter.png"
  alt: "電話番号フォーマッター"
---

<div id="pf-app">

<style>
#pf-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Yu Gothic", Meiryo, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1a1a2e;
}
#pf-app h2 {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 2rem 0 1rem;
  color: #0f3460;
  border-left: 4px solid #e94560;
  padding-left: 0.75rem;
}
#pf-app .pf-card {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 10px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
#pf-app label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #444;
  margin-bottom: 0.4rem;
}
#pf-app input[type="text"],
#pf-app select,
#pf-app textarea {
  width: 100%;
  padding: 0.65rem 0.9rem;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
  box-sizing: border-box;
  transition: border-color 0.2s;
}
#pf-app input[type="text"]:focus,
#pf-app select:focus,
#pf-app textarea:focus {
  outline: none;
  border-color: #0f3460;
}
#pf-app textarea {
  min-height: 130px;
  resize: vertical;
  font-family: monospace;
  font-size: 0.9rem;
}
#pf-app .pf-row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
#pf-app .pf-row > * {
  flex: 1;
  min-width: 220px;
}
#pf-app .pf-btn {
  display: inline-block;
  background: #0f3460;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 0.65rem 1.4rem;
  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  margin-top: 0.5rem;
}
#pf-app .pf-btn:hover {
  background: #e94560;
}
#pf-app .pf-btn-secondary {
  background: #6c757d;
}
#pf-app .pf-btn-secondary:hover {
  background: #495057;
}
#pf-app .pf-result-grid {
  display: grid;
  grid-template-columns: 170px 1fr;
  gap: 0.5rem 1rem;
  align-items: center;
  margin-top: 1rem;
}
#pf-app .pf-result-label {
  font-size: 0.8rem;
  font-weight: 700;
  color: #666;
  letter-spacing: 0.02em;
}
#pf-app .pf-result-value {
  background: #f4f6fb;
  border: 1px solid #dde3f0;
  border-radius: 5px;
  padding: 0.45rem 0.75rem;
  font-family: monospace;
  font-size: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  min-height: 2.2rem;
  word-break: break-all;
}
#pf-app .pf-copy-btn {
  background: none;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 2px 8px;
  font-size: 0.75rem;
  cursor: pointer;
  color: #555;
  white-space: nowrap;
  margin-left: auto;
  transition: background 0.15s;
  font-family: sans-serif;
}
#pf-app .pf-copy-btn:hover {
  background: #e0e7ff;
}
#pf-app .pf-badge {
  display: inline-block;
  padding: 3px 10px;
  border-radius: 12px;
  font-size: 0.78rem;
  font-weight: 700;
}
#pf-app .pf-badge-valid {
  background: #d4edda;
  color: #155724;
}
#pf-app .pf-badge-invalid {
  background: #f8d7da;
  color: #721c24;
}
#pf-app .pf-badge-warn {
  background: #fff3cd;
  color: #856404;
}
#pf-app .pf-validation-box {
  margin-top: 1rem;
  padding: 0.75rem 1rem;
  border-radius: 6px;
  font-size: 0.9rem;
}
#pf-app .pf-validation-box.valid {
  background: #d4edda;
  border: 1px solid #c3e6cb;
  color: #155724;
}
#pf-app .pf-validation-box.invalid {
  background: #f8d7da;
  border: 1px solid #f5c6cb;
  color: #721c24;
}
#pf-app .pf-validation-box.warn {
  background: #fff3cd;
  border: 1px solid #ffeeba;
  color: #856404;
}
#pf-app .bulk-output {
  margin-top: 1rem;
}
#pf-app .bulk-output-line {
  font-family: monospace;
  font-size: 0.88rem;
  padding: 0.3rem 0.5rem;
  border-bottom: 1px solid #f0f0f0;
  display: flex;
  gap: 0.75rem;
  align-items: center;
  flex-wrap: wrap;
}
#pf-app .bulk-output-line:nth-child(even) {
  background: #f9f9f9;
}
#pf-app .pf-ref-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.87rem;
}
#pf-app .pf-ref-table th {
  background: #0f3460;
  color: #fff;
  padding: 0.5rem 0.75rem;
  text-align: left;
}
#pf-app .pf-ref-table td {
  padding: 0.45rem 0.75rem;
  border-bottom: 1px solid #eee;
}
#pf-app .pf-ref-table tr:nth-child(even) td {
  background: #f7f9fc;
}
#pf-app .pf-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid #e0e0e0;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}
#pf-app .pf-tab {
  padding: 0.55rem 1.1rem;
  cursor: pointer;
  font-weight: 600;
  font-size: 0.88rem;
  color: #666;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
  background: none;
  border-top: none;
  border-left: none;
  border-right: none;
}
#pf-app .pf-tab.active {
  color: #0f3460;
  border-bottom-color: #e94560;
}
#pf-app .pf-tab-panel {
  display: none;
}
#pf-app .pf-tab-panel.active {
  display: block;
}
#pf-app .pf-jp-info {
  background: #eef3ff;
  border: 1px solid #c5d5f7;
  border-radius: 8px;
  padding: 1rem 1.25rem;
  font-size: 0.88rem;
  margin-bottom: 1rem;
  line-height: 1.7;
}
#pf-app .pf-jp-info strong {
  color: #0f3460;
}
#pf-app .pf-cta {
  background: linear-gradient(135deg, #f0f7ff 0%, #e8f4fd 100%);
  border: 1px solid #b8d9f5;
  border-radius: 8px;
  padding: 1rem 1.25rem;
  margin-top: 2rem;
  font-size: 0.92rem;
}
#pf-app .pf-cta a {
  color: #0f3460;
  font-weight: 700;
  text-decoration: none;
}
#pf-app .pf-cta a:hover {
  color: #e94560;
  text-decoration: underline;
}
@media (max-width: 600px) {
  #pf-app .pf-result-grid {
    grid-template-columns: 1fr;
  }
  #pf-app .pf-result-label {
    margin-top: 0.5rem;
  }
}
</style>

<h2>電話番号フォーマッター＆バリデーター</h2>

<div class="pf-tabs">
  <button class="pf-tab active" onclick="pfSwitchTab('single')">1件変換</button>
  <button class="pf-tab" onclick="pfSwitchTab('bulk')">一括変換</button>
  <button class="pf-tab" onclick="pfSwitchTab('jpref')">日本番号ガイド</button>
  <button class="pf-tab" onclick="pfSwitchTab('ref')">国番号一覧</button>
</div>

<!-- SINGLE FORMATTER TAB -->
<div id="pf-tab-single" class="pf-tab-panel active">
  <div class="pf-card">
    <div class="pf-row">
      <div>
        <label for="pf-input">電話番号を入力</label>
        <input type="text" id="pf-input" placeholder="例: 03-1234-5678 / 090-9876-5432 / +81 3 1234 5678" oninput="pfFormat()" />
      </div>
      <div>
        <label for="pf-country">国を選択</label>
        <select id="pf-country" onchange="pfFormat()">
          <option value="JP" selected>日本 (+81)</option>
          <option value="US">アメリカ (+1)</option>
          <option value="CA">カナダ (+1)</option>
          <option value="GB">イギリス (+44)</option>
          <option value="DE">ドイツ (+49)</option>
          <option value="FR">フランス (+33)</option>
          <option value="AU">オーストラリア (+61)</option>
          <option value="KR">韓国 (+82)</option>
          <option value="CN">中国 (+86)</option>
          <option value="IN">インド (+91)</option>
          <option value="BR">ブラジル (+55)</option>
          <option value="MX">メキシコ (+52)</option>
          <option value="IT">イタリア (+39)</option>
          <option value="ES">スペイン (+34)</option>
          <option value="NL">オランダ (+31)</option>
          <option value="SG">シンガポール (+65)</option>
          <option value="HK">香港 (+852)</option>
          <option value="TW">台湾 (+886)</option>
          <option value="NZ">ニュージーランド (+64)</option>
          <option value="ZA">南アフリカ (+27)</option>
        </select>
      </div>
    </div>
    <div id="pf-validation-box" class="pf-validation-box warn" style="display:none;"></div>
    <div id="pf-result-grid" class="pf-result-grid" style="display:none;">
      <span class="pf-result-label">国際形式</span>
      <span class="pf-result-value"><span id="val-intl"></span><button class="pf-copy-btn" onclick="pfCopy('val-intl')">コピー</button></span>
      <span class="pf-result-label">国内形式</span>
      <span class="pf-result-value"><span id="val-natl"></span><button class="pf-copy-btn" onclick="pfCopy('val-natl')">コピー</button></span>
      <span class="pf-result-label">E.164</span>
      <span class="pf-result-value"><span id="val-e164"></span><button class="pf-copy-btn" onclick="pfCopy('val-e164')">コピー</button></span>
      <span class="pf-result-label">RFC 3966</span>
      <span class="pf-result-value"><span id="val-rfc"></span><button class="pf-copy-btn" onclick="pfCopy('val-rfc')">コピー</button></span>
      <span class="pf-result-label">数字のみ</span>
      <span class="pf-result-value"><span id="val-raw"></span><button class="pf-copy-btn" onclick="pfCopy('val-raw')">コピー</button></span>
    </div>
  </div>
</div>

<!-- BULK FORMATTER TAB -->
<div id="pf-tab-bulk" class="pf-tab-panel">
  <div class="pf-card">
    <label for="pf-bulk-country">国を選択（全番号共通）</label>
    <select id="pf-bulk-country" style="margin-bottom:1rem;">
      <option value="JP" selected>日本 (+81)</option>
      <option value="US">アメリカ (+1)</option>
      <option value="CA">カナダ (+1)</option>
      <option value="GB">イギリス (+44)</option>
      <option value="DE">ドイツ (+49)</option>
      <option value="FR">フランス (+33)</option>
      <option value="AU">オーストラリア (+61)</option>
      <option value="KR">韓国 (+82)</option>
      <option value="CN">中国 (+86)</option>
      <option value="IN">インド (+91)</option>
      <option value="BR">ブラジル (+55)</option>
      <option value="MX">メキシコ (+52)</option>
      <option value="IT">イタリア (+39)</option>
      <option value="ES">スペイン (+34)</option>
      <option value="NL">オランダ (+31)</option>
      <option value="SG">シンガポール (+65)</option>
      <option value="HK">香港 (+852)</option>
      <option value="TW">台湾 (+886)</option>
      <option value="NZ">ニュージーランド (+64)</option>
      <option value="ZA">南アフリカ (+27)</option>
    </select>
    <label for="pf-bulk-input">電話番号を1行1件で貼り付け</label>
    <textarea id="pf-bulk-input" placeholder="03-1234-5678&#10;090-9876-5432&#10;0120-123-456&#10;+81312345678&#10;075-234-5678"></textarea>
    <div style="display:flex;gap:0.75rem;flex-wrap:wrap;">
      <button class="pf-btn" onclick="pfBulkFormat()">一括変換</button>
      <button class="pf-btn pf-btn-secondary" onclick="pfBulkClear()">クリア</button>
      <button class="pf-btn pf-btn-secondary" onclick="pfBulkCopyAll()">結果をコピー</button>
    </div>
    <div id="pf-bulk-output" class="bulk-output"></div>
  </div>
</div>

<!-- JAPAN NUMBER GUIDE TAB -->
<div id="pf-tab-jpref" class="pf-tab-panel">
  <div class="pf-card">
    <h2 style="margin-top:0;">日本の電話番号体系ガイド</h2>
    <div class="pf-jp-info">
      日本の電話番号は市外局番＋市内局番＋加入者番号で構成され、国内では先頭に<strong>0</strong>（市外局番の一部）を付けます。国際発信時は<strong>+81</strong>を付け、先頭の0を除きます。
    </div>
    <table class="pf-ref-table">
      <thead>
        <tr>
          <th>種別</th>
          <th>番号帯</th>
          <th>桁数（0含む）</th>
          <th>国内形式例</th>
          <th>国際形式例</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><strong>固定（東京・大阪）</strong></td>
          <td>03-xxxx / 06-xxxx</td>
          <td>10桁</td>
          <td>03-1234-5678</td>
          <td>+81-3-1234-5678</td>
        </tr>
        <tr>
          <td><strong>固定（地方 3桁局番）</strong></td>
          <td>0AB-xxxx-xxxx</td>
          <td>10桁</td>
          <td>045-123-4567</td>
          <td>+81-45-123-4567</td>
        </tr>
        <tr>
          <td><strong>固定（地方 4桁局番）</strong></td>
          <td>0ABC-xx-xxxx</td>
          <td>10桁</td>
          <td>0120-12-3456（例外）</td>
          <td>+81-120-12-3456</td>
        </tr>
        <tr>
          <td><strong>携帯（docomo/au/SB）</strong></td>
          <td>090 / 080 / 070</td>
          <td>11桁</td>
          <td>090-1234-5678</td>
          <td>+81-90-1234-5678</td>
        </tr>
        <tr>
          <td><strong>IP電話</strong></td>
          <td>050-xxxx-xxxx</td>
          <td>11桁</td>
          <td>050-1234-5678</td>
          <td>+81-50-1234-5678</td>
        </tr>
        <tr>
          <td><strong>フリーダイヤル</strong></td>
          <td>0120 / 0800</td>
          <td>11桁</td>
          <td>0120-123-456</td>
          <td>+81-120-123-456</td>
        </tr>
        <tr>
          <td><strong>ナビダイヤル</strong></td>
          <td>0570-xxx-xxx</td>
          <td>10桁</td>
          <td>0570-123-456</td>
          <td>+81-570-123-456</td>
        </tr>
        <tr>
          <td><strong>緊急・特番</strong></td>
          <td>110 / 119 / 117等</td>
          <td>3桁</td>
          <td>110</td>
          <td>（国内専用）</td>
        </tr>
      </tbody>
    </table>
    <p style="margin-top:1rem;font-size:0.85rem;color:#666;">※ E.164形式では+81の後に0を除いた番号を続けます（例: +819012345678）。RFC 3966形式は <code>tel:+81-90-1234-5678</code> のように記述します。</p>
  </div>
</div>

<!-- COUNTRY CODE REFERENCE TAB -->
<div id="pf-tab-ref" class="pf-tab-panel">
  <div class="pf-card">
    <p style="margin-top:0;color:#555;font-size:0.9rem;">主要国の国番号・市外局番プレフィックス・桁数の一覧です。</p>
    <table class="pf-ref-table">
      <thead>
        <tr>
          <th>国名</th>
          <th>国番号</th>
          <th>局番プレフィックス</th>
          <th>加入者番号桁数</th>
          <th>例</th>
        </tr>
      </thead>
      <tbody id="pf-ref-body"></tbody>
    </table>
  </div>
</div>

<script>
(function() {

  const COUNTRIES = {
    JP: { name: "日本",           code: "81",  trunk: "0",  digits: [9,10,11],    fmt: pfFmtJP,  example: "+81 3-1234-5678" },
    US: { name: "アメリカ",       code: "1",   trunk: "1",  digits: [10],         fmt: pfFmtUS,  example: "+1 212-555-0100" },
    CA: { name: "カナダ",         code: "1",   trunk: "1",  digits: [10],         fmt: pfFmtUS,  example: "+1 416-555-0100" },
    GB: { name: "イギリス",       code: "44",  trunk: "0",  digits: [9,10],       fmt: pfFmtGB,  example: "+44 20 7946 0958" },
    DE: { name: "ドイツ",         code: "49",  trunk: "0",  digits: [3,4,5,6,7,8,9,10,11], fmt: pfFmtDE, example: "+49 30 12345678" },
    FR: { name: "フランス",       code: "33",  trunk: "0",  digits: [9],          fmt: pfFmtFR,  example: "+33 1 23 45 67 89" },
    AU: { name: "オーストラリア", code: "61",  trunk: "0",  digits: [9],          fmt: pfFmtAU,  example: "+61 2 1234 5678" },
    KR: { name: "韓国",           code: "82",  trunk: "0",  digits: [9,10],       fmt: pfFmtKR,  example: "+82 2-1234-5678" },
    CN: { name: "中国",           code: "86",  trunk: "0",  digits: [11],         fmt: pfFmtCN,  example: "+86 138 0013 8000" },
    IN: { name: "インド",         code: "91",  trunk: "0",  digits: [10],         fmt: pfFmtIN,  example: "+91 98765 43210" },
    BR: { name: "ブラジル",       code: "55",  trunk: "0",  digits: [10,11],      fmt: pfFmtBR,  example: "+55 11 91234-5678" },
    MX: { name: "メキシコ",       code: "52",  trunk: "0",  digits: [10],         fmt: pfFmtMX,  example: "+52 55 1234 5678" },
    IT: { name: "イタリア",       code: "39",  trunk: "0",  digits: [6,7,8,9,10], fmt: pfFmtIT,  example: "+39 06 1234 5678" },
    ES: { name: "スペイン",       code: "34",  trunk: "",   digits: [9],          fmt: pfFmtES,  example: "+34 91 123 45 67" },
    NL: { name: "オランダ",       code: "31",  trunk: "0",  digits: [9],          fmt: pfFmtNL,  example: "+31 20 123 4567" },
    SG: { name: "シンガポール",   code: "65",  trunk: "",   digits: [8],          fmt: pfFmtSG,  example: "+65 6123 4567" },
    HK: { name: "香港",           code: "852", trunk: "",   digits: [8],          fmt: pfFmtHK,  example: "+852 2123 4567" },
    TW: { name: "台湾",           code: "886", trunk: "0",  digits: [8,9],        fmt: pfFmtTW,  example: "+886 2 1234 5678" },
    NZ: { name: "ニュージーランド", code: "64", trunk: "0", digits: [8,9],        fmt: pfFmtNZ,  example: "+64 9-123 4567" },
    ZA: { name: "南アフリカ",     code: "27",  trunk: "0",  digits: [9],          fmt: pfFmtZA,  example: "+27 11 123 4567" },
  };

  function digits(s) { return s.replace(/\D/g, ''); }

  function normalize(raw, key) {
    const c = COUNTRIES[key];
    let d = digits(raw);
    if (d.startsWith(c.code)) d = d.slice(c.code.length);
    if (c.trunk && d.startsWith(c.trunk)) d = d.slice(c.trunk.length);
    return d;
  }

  function pfFmtJP(sub) {
    if (sub.length === 10) {
      if (/^[789]0/.test(sub) || sub.startsWith('50')) {
        return { intl: `+81 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`, natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}` };
      }
      if (sub.startsWith('120') || sub.startsWith('800') || sub.startsWith('570')) {
        return { intl: `+81 ${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`, natl: `0${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}` };
      }
      return { intl: `+81 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`, natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}` };
    }
    if (sub.length === 9) {
      if (sub.startsWith('3') || sub.startsWith('6')) {
        return { intl: `+81 ${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}`, natl: `0${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}` };
      }
      return { intl: `+81 ${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`, natl: `0${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}` };
    }
    if (sub.length === 8) {
      return { intl: `+81 ${sub.slice(0,4)}-${sub.slice(4)}`, natl: `0${sub.slice(0,4)}-${sub.slice(4)}` };
    }
    return null;
  }
  function pfFmtUS(sub) {
    if (sub.length !== 10) return null;
    return { intl: `+1 ${sub.slice(0,3)}-${sub.slice(3,6)}-${sub.slice(6)}`, natl: `(${sub.slice(0,3)}) ${sub.slice(3,6)}-${sub.slice(6)}` };
  }
  function pfFmtGB(sub) {
    if (sub.length === 10) return { intl: `+44 ${sub.slice(0,2)} ${sub.slice(2,6)} ${sub.slice(6)}`, natl: `0${sub.slice(0,2)} ${sub.slice(2,6)} ${sub.slice(6)}` };
    if (sub.length === 9) return { intl: `+44 ${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}`, natl: `0${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}` };
    return null;
  }
  function pfFmtDE(sub) {
    if (sub.length < 3) return null;
    return { intl: `+49 ${sub.slice(0,3)} ${sub.slice(3)}`, natl: `0${sub.slice(0,3)} ${sub.slice(3)}` };
  }
  function pfFmtFR(sub) {
    if (sub.length !== 9) return null;
    const p = sub.slice(1).match(/.{1,2}/g).join(' ');
    return { intl: `+33 ${sub[0]} ${p}`, natl: `0${sub[0]} ${p}` };
  }
  function pfFmtAU(sub) {
    if (sub.length === 9) return { intl: `+61 ${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}`, natl: `0${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}` };
    return null;
  }
  function pfFmtKR(sub) {
    if (sub.length === 10) return { intl: `+82 ${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}`, natl: `0${sub.slice(0,2)}-${sub.slice(2,6)}-${sub.slice(6)}` };
    if (sub.length === 9) return { intl: `+82 ${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}`, natl: `0${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}` };
    return null;
  }
  function pfFmtCN(sub) {
    if (sub.length === 11) return { intl: `+86 ${sub.slice(0,3)} ${sub.slice(3,7)} ${sub.slice(7)}`, natl: `0${sub.slice(0,3)} ${sub.slice(3,7)} ${sub.slice(7)}` };
    return null;
  }
  function pfFmtIN(sub) {
    if (sub.length === 10) return { intl: `+91 ${sub.slice(0,5)} ${sub.slice(5)}`, natl: `0${sub.slice(0,5)} ${sub.slice(5)}` };
    return null;
  }
  function pfFmtBR(sub) {
    if (sub.length === 11) return { intl: `+55 ${sub.slice(0,2)} ${sub.slice(2,7)}-${sub.slice(7)}`, natl: `(0${sub.slice(0,2)}) ${sub.slice(2,7)}-${sub.slice(7)}` };
    if (sub.length === 10) return { intl: `+55 ${sub.slice(0,2)} ${sub.slice(2,6)}-${sub.slice(6)}`, natl: `(0${sub.slice(0,2)}) ${sub.slice(2,6)}-${sub.slice(6)}` };
    return null;
  }
  function pfFmtMX(sub) {
    if (sub.length === 10) return { intl: `+52 ${sub.slice(0,2)} ${sub.slice(2,6)} ${sub.slice(6)}`, natl: `(${sub.slice(0,2)}) ${sub.slice(2,6)} ${sub.slice(6)}` };
    return null;
  }
  function pfFmtIT(sub) {
    return { intl: `+39 0${sub.slice(0,2)} ${sub.slice(2)}`, natl: `0${sub.slice(0,2)} ${sub.slice(2)}` };
  }
  function pfFmtES(sub) {
    if (sub.length === 9) return { intl: `+34 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5,7)} ${sub.slice(7)}`, natl: `${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5,7)} ${sub.slice(7)}` };
    return null;
  }
  function pfFmtNL(sub) {
    if (sub.length === 9) return { intl: `+31 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`, natl: `0${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}` };
    return null;
  }
  function pfFmtSG(sub) {
    if (sub.length === 8) return { intl: `+65 ${sub.slice(0,4)} ${sub.slice(4)}`, natl: `${sub.slice(0,4)} ${sub.slice(4)}` };
    return null;
  }
  function pfFmtHK(sub) {
    if (sub.length === 8) return { intl: `+852 ${sub.slice(0,4)} ${sub.slice(4)}`, natl: `${sub.slice(0,4)} ${sub.slice(4)}` };
    return null;
  }
  function pfFmtTW(sub) {
    if (sub.length === 9) return { intl: `+886 ${sub[0]} ${sub.slice(1,5)} ${sub.slice(5)}`, natl: `0${sub[0]}-${sub.slice(1,5)}-${sub.slice(5)}` };
    if (sub.length === 8) return { intl: `+886 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`, natl: `0${sub.slice(0,2)}-${sub.slice(2,5)}-${sub.slice(5)}` };
    return null;
  }
  function pfFmtNZ(sub) {
    if (sub.length === 9) return { intl: `+64 ${sub[0]}-${sub.slice(1,4)} ${sub.slice(4)}`, natl: `0${sub[0]}-${sub.slice(1,4)} ${sub.slice(4)}` };
    if (sub.length === 8) return { intl: `+64 ${sub.slice(0,2)}-${sub.slice(2,5)} ${sub.slice(5)}`, natl: `0${sub.slice(0,2)}-${sub.slice(2,5)} ${sub.slice(5)}` };
    return null;
  }
  function pfFmtZA(sub) {
    if (sub.length === 9) return { intl: `+27 ${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}`, natl: `0${sub.slice(0,2)} ${sub.slice(2,5)} ${sub.slice(5)}` };
    return null;
  }

  function toE164(code, sub) { return `+${code}${sub}`; }
  function toRFC3966(code, sub) { return `tel:+${code}-${sub.match(/.{1,4}/g).join('-')}`; }

  function validate(sub, key) {
    const c = COUNTRIES[key];
    if (!sub || sub.length === 0) return { ok: false, msg: "電話番号を入力してください。" };
    if (!/^\d+$/.test(sub)) return { ok: false, msg: "番号に数字以外の文字が含まれています。" };
    if (c.digits.includes(sub.length)) {
      return { ok: true, msg: `${c.name}の有効な桁数です（加入者番号 ${sub.length} 桁）。` };
    }
    return { ok: 'warn', msg: `桁数 ${sub.length} は${c.name}では一般的ではありません（想定: ${c.digits.join(' または ')} 桁）。特殊番号の場合は問題ありません。` };
  }

  window.pfFormat = function() {
    const raw = document.getElementById('pf-input').value.trim();
    const key = document.getElementById('pf-country').value;
    const c = COUNTRIES[key];
    const validBox = document.getElementById('pf-validation-box');
    const grid = document.getElementById('pf-result-grid');

    if (!raw) { validBox.style.display = 'none'; grid.style.display = 'none'; return; }

    const sub = normalize(raw, key);
    const v = validate(sub, key);
    validBox.style.display = 'block';
    validBox.className = 'pf-validation-box ' + (v.ok === true ? 'valid' : v.ok === 'warn' ? 'warn' : 'invalid');
    validBox.textContent = v.msg;

    if (v.ok === false) { grid.style.display = 'none'; return; }

    const formatted = c.fmt(sub);
    const e164 = toE164(c.code, sub);
    const rfc = toRFC3966(c.code, sub);

    grid.style.display = 'grid';
    document.getElementById('val-intl').textContent = formatted ? formatted.intl : e164;
    document.getElementById('val-natl').textContent = formatted ? formatted.natl : `0${sub}`;
    document.getElementById('val-e164').textContent = e164;
    document.getElementById('val-rfc').textContent = rfc;
    document.getElementById('val-raw').textContent = sub;
  };

  window.pfCopy = function(id) {
    const text = document.getElementById(id).textContent;
    navigator.clipboard.writeText(text).then(() => {
      const btn = document.getElementById(id).nextElementSibling;
      const orig = btn.textContent;
      btn.textContent = 'コピー済';
      setTimeout(() => { btn.textContent = orig; }, 1500);
    });
  };

  window.pfSwitchTab = function(tab) {
    const tabs = ['single','bulk','jpref','ref'];
    document.querySelectorAll('#pf-app .pf-tab').forEach((t,i) => {
      t.classList.toggle('active', tabs[i] === tab);
    });
    document.querySelectorAll('#pf-app .pf-tab-panel').forEach(p => p.classList.remove('active'));
    document.getElementById('pf-tab-' + tab).classList.add('active');
  };

  window.pfBulkFormat = function() {
    const lines = document.getElementById('pf-bulk-input').value.split('\n').filter(l => l.trim());
    const key = document.getElementById('pf-bulk-country').value;
    const c = COUNTRIES[key];
    const out = document.getElementById('pf-bulk-output');
    if (!lines.length) { out.innerHTML = ''; return; }

    let html = '';
    lines.forEach(line => {
      const raw = line.trim();
      if (!raw) return;
      const sub = normalize(raw, key);
      const v = validate(sub, key);
      const formatted = (v.ok !== false) ? c.fmt(sub) : null;
      const e164 = (v.ok !== false) ? toE164(c.code, sub) : '—';
      const badge = v.ok === true
        ? '<span class="pf-badge pf-badge-valid">有効</span>'
        : v.ok === 'warn'
          ? '<span class="pf-badge pf-badge-warn">注意</span>'
          : '<span class="pf-badge pf-badge-invalid">無効</span>';
      html += `<div class="bulk-output-line">
        ${badge}
        <span style="color:#888;min-width:150px;">${raw}</span>
        <span>→</span>
        <span>${formatted ? formatted.intl : '—'}</span>
        <span style="color:#888;">${e164}</span>
      </div>`;
    });
    out.innerHTML = html;
  };

  window.pfBulkClear = function() {
    document.getElementById('pf-bulk-input').value = '';
    document.getElementById('pf-bulk-output').innerHTML = '';
  };

  window.pfBulkCopyAll = function() {
    const lines = document.querySelectorAll('#pf-bulk-output .bulk-output-line');
    const text = Array.from(lines).map(l => {
      const spans = l.querySelectorAll('span');
      return spans[2] ? spans[2].textContent.trim() : '';
    }).filter(Boolean).join('\n');
    navigator.clipboard.writeText(text).then(() => alert('結果をクリップボードにコピーしました！'));
  };

  function buildRefTable() {
    const tbody = document.getElementById('pf-ref-body');
    let html = '';
    Object.entries(COUNTRIES).forEach(([key, c]) => {
      const trunk = c.trunk || '（なし）';
      const digStr = c.digits.join(', ') + ' 桁';
      html += `<tr>
        <td><strong>${c.name}</strong> (${key})</td>
        <td>+${c.code}</td>
        <td>${trunk}</td>
        <td>${digStr}</td>
        <td style="font-family:monospace;font-size:0.82rem;">${c.example}</td>
      </tr>`;
    });
    tbody.innerHTML = html;
  }

  buildRefTable();
})();
</script>

---

<div class="pf-cta">

顧客管理を効率化 → <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow" target="_blank">freee会計で取引先情報を一元管理</a>

</div>

</div>
