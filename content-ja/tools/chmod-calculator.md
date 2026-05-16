---
title: "Chmod計算ツール — Unixパーミッション設定"
date: 2025-05-16
description: "無料のchmod計算ツール。ビジュアルパーミッションエディタで8進数・シンボリック表記を即座に確認。ファイル権限のプリセット付き。chmodコマンドをワンクリックコピー。"
categories: ["無料ツール"]
slug: "chmod-calculator"
ShowToc: false
aliases:
  - "/ja/tools/chmod-calculator/"
  - "/ja/tools/chmod-calculator/"
cover:
  image: "/images/covers/chmod-calculator-ja.png"
  alt: "Chmod計算ツール"
---

<style>
#chmod-app-ja *,
#chmod-app-ja *::before,
#chmod-app-ja *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#chmod-app-ja {
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, "Liberation Mono", monospace;
  background: #0f172a;
  color: #e2e8f0;
  border-radius: 12px;
  padding: 28px;
  max-width: 860px;
  margin: 0 auto;
}

#chmod-app-ja h2 {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #84cc16;
  margin-bottom: 20px;
  letter-spacing: -0.02em;
}

#chmod-app-ja .chj-section-label {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.7rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 10px;
}

/* Presets */
#chmod-app-ja .chj-presets {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 24px;
}

#chmod-app-ja .chj-preset-btn {
  background: #1e293b;
  border: 1px solid #334155;
  color: #94a3b8;
  border-radius: 6px;
  padding: 6px 14px;
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, monospace;
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.15s;
}

#chmod-app-ja .chj-preset-btn:hover {
  background: #334155;
  color: #e2e8f0;
  border-color: #84cc16;
}

#chmod-app-ja .chj-preset-btn span {
  font-weight: 700;
  color: #84cc16;
}

/* Numeric input */
#chmod-app-ja .chj-numeric-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}

#chmod-app-ja .chj-numeric-input {
  background: #1e293b;
  border: 1px solid #334155;
  color: #84cc16;
  border-radius: 8px;
  padding: 10px 16px;
  font-family: ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, monospace;
  font-size: 1.8rem;
  font-weight: 700;
  width: 120px;
  text-align: center;
  outline: none;
  transition: border-color 0.15s;
  letter-spacing: 0.1em;
}

#chmod-app-ja .chj-numeric-input:focus {
  border-color: #84cc16;
}

#chmod-app-ja .chj-numeric-hint {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.78rem;
  color: #64748b;
}

/* Permission grid */
#chmod-app-ja .chj-grid-wrapper {
  overflow-x: auto;
  margin-bottom: 24px;
}

#chmod-app-ja .chj-grid {
  width: 100%;
  border-collapse: collapse;
  min-width: 380px;
}

#chmod-app-ja .chj-grid th {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.72rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
  padding: 8px 12px;
  text-align: center;
  border-bottom: 1px solid #1e293b;
}

#chmod-app-ja .chj-grid th.chj-th-owner {
  text-align: left;
  color: #94a3b8;
}

#chmod-app-ja .chj-grid td {
  padding: 10px 12px;
  text-align: center;
  border-bottom: 1px solid #1e293b;
}

#chmod-app-ja .chj-grid td.chj-td-label {
  text-align: left;
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.88rem;
  font-weight: 600;
  color: #e2e8f0;
  padding-left: 4px;
}

#chmod-app-ja .chj-grid tr:last-child td {
  border-bottom: none;
}

#chmod-app-ja .chj-grid tr:hover td {
  background: #1e293b22;
}

/* Checkbox custom */
#chmod-app-ja .chj-cb-wrap {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

#chmod-app-ja .chj-cb-wrap input[type="checkbox"] {
  display: none;
}

#chmod-app-ja .chj-cb-box {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  border: 2px solid #334155;
  background: #1e293b;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.15s;
  font-size: 0.9rem;
  color: transparent;
  user-select: none;
}

#chmod-app-ja .chj-cb-wrap input:checked + .chj-cb-box {
  background: #84cc16;
  border-color: #84cc16;
  color: #0f172a;
}

#chmod-app-ja .chj-cb-wrap:hover .chj-cb-box {
  border-color: #84cc16;
}

/* Row color accents */
#chmod-app-ja .chj-row-owner td.chj-td-label { color: #38bdf8; }
#chmod-app-ja .chj-row-group  td.chj-td-label { color: #a78bfa; }
#chmod-app-ja .chj-row-others td.chj-td-label { color: #f97316; }

/* Special permissions */
#chmod-app-ja .chj-special-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 24px;
}

#chmod-app-ja .chj-special-item {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}

#chmod-app-ja .chj-special-item input[type="checkbox"] {
  display: none;
}

#chmod-app-ja .chj-special-box {
  width: 26px;
  height: 26px;
  border-radius: 5px;
  border: 2px solid #334155;
  background: #1e293b;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.15s;
  font-size: 0.8rem;
  color: transparent;
}

#chmod-app-ja .chj-special-item input:checked + .chj-special-box {
  background: #f59e0b;
  border-color: #f59e0b;
  color: #0f172a;
}

#chmod-app-ja .chj-special-item:hover .chj-special-box {
  border-color: #f59e0b;
}

#chmod-app-ja .chj-special-name {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.83rem;
  color: #94a3b8;
}

/* Output cards */
#chmod-app-ja .chj-outputs {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 12px;
  margin-bottom: 24px;
}

#chmod-app-ja .chj-output-card {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 14px 16px;
}

#chmod-app-ja .chj-output-card .chj-output-label {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.68rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #64748b;
  margin-bottom: 6px;
}

#chmod-app-ja .chj-output-card .chj-output-value {
  font-size: 1.1rem;
  font-weight: 700;
  color: #84cc16;
  word-break: break-all;
}

/* Copy button */
#chmod-app-ja .chj-copy-row {
  display: flex;
  align-items: center;
  gap: 12px;
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 12px 16px;
  margin-bottom: 28px;
}

#chmod-app-ja .chj-copy-cmd {
  flex: 1;
  font-size: 1rem;
  color: #e2e8f0;
  font-weight: 600;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#chmod-app-ja .chj-copy-btn {
  background: #84cc16;
  border: none;
  border-radius: 6px;
  color: #0f172a;
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.8rem;
  font-weight: 700;
  padding: 7px 16px;
  cursor: pointer;
  transition: background 0.15s;
  white-space: nowrap;
  flex-shrink: 0;
}

#chmod-app-ja .chj-copy-btn:hover {
  background: #a3e635;
}

#chmod-app-ja .chj-copy-btn.copied {
  background: #22c55e;
}

/* Explanation */
#chmod-app-ja .chj-explain {
  background: #1e293b;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 20px;
}

#chmod-app-ja .chj-explain h3 {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.95rem;
  font-weight: 700;
  color: #e2e8f0;
  margin-bottom: 14px;
}

#chmod-app-ja .chj-explain-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}

#chmod-app-ja .chj-explain-item {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

#chmod-app-ja .chj-explain-item .chj-ei-title {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.78rem;
  font-weight: 700;
  color: #84cc16;
}

#chmod-app-ja .chj-explain-item .chj-ei-desc {
  font-family: "Noto Sans JP", ui-sans-serif, system-ui, sans-serif;
  font-size: 0.78rem;
  color: #94a3b8;
  line-height: 1.55;
}

/* Symbolic breakdown */
#chmod-app-ja .chj-sym-breakdown {
  display: flex;
  gap: 0;
  font-size: 1.3rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
  flex-wrap: wrap;
}

#chmod-app-ja .chj-sym-part {
  padding: 4px 8px;
  border-radius: 4px;
}

#chmod-app-ja .chj-sym-owner  { color: #38bdf8; background: #0c2340; }
#chmod-app-ja .chj-sym-group  { color: #a78bfa; background: #1a0c40; }
#chmod-app-ja .chj-sym-others { color: #f97316; background: #3d1500; }

/* Responsive */
@media (max-width: 600px) {
  #chmod-app-ja {
    padding: 18px 14px;
  }
  #chmod-app-ja .chj-numeric-input {
    font-size: 1.4rem;
    width: 100px;
  }
  #chmod-app-ja .chj-sym-breakdown {
    font-size: 1rem;
  }
}
</style>

<div id="chmod-app-ja">

<h2>Chmod パーミッション計算ツール</h2>

<div class="chj-section-label">クイックプリセット</div>
<div class="chj-presets">
  <button class="chj-preset-btn" onclick="chjApplyPreset(644)"><span>644</span> — ファイル</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(755)"><span>755</span> — ディレクトリ</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(600)"><span>600</span> — プライベート</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(777)"><span>777</span> — 全員アクセス</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(444)"><span>444</span> — 読み取り専用</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(700)"><span>700</span> — オーナーのみ</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(664)"><span>664</span> — グループ書込</button>
  <button class="chj-preset-btn" onclick="chjApplyPreset(640)"><span>640</span> — グループ読取</button>
</div>

<div class="chj-section-label">8進数の値</div>
<div class="chj-numeric-row">
  <input class="chj-numeric-input" id="chj-octal-input" type="text" maxlength="4" value="755"
    oninput="chjFromOctal(this.value)" placeholder="755" />
  <span class="chj-numeric-hint">8進数（000〜777）を直接入力<br>またはグリッドで選択</span>
</div>

<div class="chj-section-label">パーミッション グリッド</div>
<div class="chj-grid-wrapper">
  <table class="chj-grid">
    <thead>
      <tr>
        <th class="chj-th-owner">対象</th>
        <th>読取 (r)</th>
        <th>書込 (w)</th>
        <th>実行 (x)</th>
        <th>8進数</th>
      </tr>
    </thead>
    <tbody>
      <tr class="chj-row-owner">
        <td class="chj-td-label">オーナー (u)</td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-ur" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-uw" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-ux" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td id="chj-uval" style="color:#38bdf8;font-weight:700;">7</td>
      </tr>
      <tr class="chj-row-group">
        <td class="chj-td-label">グループ (g)</td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-gr" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-gw" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-gx" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td id="chj-gval" style="color:#a78bfa;font-weight:700;">5</td>
      </tr>
      <tr class="chj-row-others">
        <td class="chj-td-label">その他 (o)</td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-or" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-ow" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td><label class="chj-cb-wrap"><input type="checkbox" id="chj-ox" onchange="chjUpdate()"><span class="chj-cb-box">✓</span></label></td>
        <td id="chj-oval" style="color:#f97316;font-weight:700;">5</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="chj-section-label">特殊パーミッション</div>
<div class="chj-special-row">
  <label class="chj-special-item">
    <input type="checkbox" id="chj-setuid" onchange="chjUpdate()">
    <span class="chj-special-box">✓</span>
    <span class="chj-special-name">setuid — オーナー権限で実行</span>
  </label>
  <label class="chj-special-item">
    <input type="checkbox" id="chj-setgid" onchange="chjUpdate()">
    <span class="chj-special-box">✓</span>
    <span class="chj-special-name">setgid — グループ権限で実行</span>
  </label>
  <label class="chj-special-item">
    <input type="checkbox" id="chj-sticky" onchange="chjUpdate()">
    <span class="chj-special-box">✓</span>
    <span class="chj-special-name">スティッキービット — 削除制限</span>
  </label>
</div>

<div class="chj-section-label">結果</div>
<div class="chj-outputs">
  <div class="chj-output-card">
    <div class="chj-output-label">8進数（数値表記）</div>
    <div class="chj-output-value" id="chj-out-octal">755</div>
  </div>
  <div class="chj-output-card">
    <div class="chj-output-label">シンボリック表記</div>
    <div class="chj-sym-breakdown" id="chj-out-sym-parts">
      <span class="chj-sym-part chj-sym-owner">rwx</span><span class="chj-sym-part chj-sym-group">r-x</span><span class="chj-sym-part chj-sym-others">r-x</span>
    </div>
    <div class="chj-output-value" style="font-size:0.85rem;color:#64748b;" id="chj-out-sym-full">rwxr-xr-x</div>
  </div>
</div>

<div class="chj-copy-row">
  <span class="chj-copy-cmd" id="chj-cmd-text">chmod 755 filename</span>
  <button class="chj-copy-btn" id="chj-copy-btn" onclick="chjCopyCmd()">コピー</button>
</div>

<div class="chj-explain">
  <h3>パーミッションの意味</h3>
  <div class="chj-explain-grid">
    <div class="chj-explain-item">
      <span class="chj-ei-title">読取 (r) = 4</span>
      <span class="chj-ei-desc">ファイル：内容を閲覧できる。<br>ディレクトリ：一覧表示（ls）できる。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">書込 (w) = 2</span>
      <span class="chj-ei-desc">ファイル：変更・削除できる。<br>ディレクトリ：ファイルの作成・削除ができる。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">実行 (x) = 1</span>
      <span class="chj-ei-desc">ファイル：プログラムとして実行できる。<br>ディレクトリ：移動（cd）できる。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">オーナー (u)</span>
      <span class="chj-ei-desc">ファイルを所有するユーザー。通常は作成者。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">グループ (g)</span>
      <span class="chj-ei-desc">ファイルに関連付けられたグループのメンバー。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">その他 (o)</span>
      <span class="chj-ei-desc">オーナー・グループ以外の全ユーザー。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">setuid (4000)</span>
      <span class="chj-ei-desc">オーナーの権限で実行される。実行ビットに「s」が表示される。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">setgid (2000)</span>
      <span class="chj-ei-desc">グループ権限で実行。ディレクトリ内の新ファイルがグループを継承。</span>
    </div>
    <div class="chj-explain-item">
      <span class="chj-ei-title">スティッキービット (1000)</span>
      <span class="chj-ei-desc">ファイルのオーナーのみ削除可能。/tmp ディレクトリ等で使用。</span>
    </div>
  </div>
</div>

</div>

<script>
(function() {
  function chjGetBits() {
    return {
      ur: document.getElementById('chj-ur').checked,
      uw: document.getElementById('chj-uw').checked,
      ux: document.getElementById('chj-ux').checked,
      gr: document.getElementById('chj-gr').checked,
      gw: document.getElementById('chj-gw').checked,
      gx: document.getElementById('chj-gx').checked,
      or: document.getElementById('chj-or').checked,
      ow: document.getElementById('chj-ow').checked,
      ox: document.getElementById('chj-ox').checked,
      setuid: document.getElementById('chj-setuid').checked,
      setgid: document.getElementById('chj-setgid').checked,
      sticky: document.getElementById('chj-sticky').checked
    };
  }

  function chjBitsToOctal(b) {
    var u = (b.ur ? 4 : 0) + (b.uw ? 2 : 0) + (b.ux ? 1 : 0);
    var g = (b.gr ? 4 : 0) + (b.gw ? 2 : 0) + (b.gx ? 1 : 0);
    var o = (b.or ? 4 : 0) + (b.ow ? 2 : 0) + (b.ox ? 1 : 0);
    var s = (b.setuid ? 4 : 0) + (b.setgid ? 2 : 0) + (b.sticky ? 1 : 0);
    return { u: u, g: g, o: o, s: s };
  }

  function chjBitsToSymbol(b) {
    function bit(r, w, x, special, sChar) {
      return (r ? 'r' : '-') + (w ? 'w' : '-') + (special ? (x ? sChar : sChar.toUpperCase()) : (x ? 'x' : '-'));
    }
    var uSym = bit(b.ur, b.uw, b.ux, b.setuid, 's');
    var gSym = bit(b.gr, b.gw, b.gx, b.setgid, 's');
    var oSym = bit(b.or, b.ow, b.ox, b.sticky, 't');
    return { u: uSym, g: gSym, o: oSym };
  }

  window.chjUpdate = function() {
    var b = chjGetBits();
    var oct = chjBitsToOctal(b);
    var sym = chjBitsToSymbol(b);

    document.getElementById('chj-uval').textContent = oct.u;
    document.getElementById('chj-gval').textContent = oct.g;
    document.getElementById('chj-oval').textContent = oct.o;

    var octalStr;
    if (oct.s > 0) {
      octalStr = oct.s + '' + oct.u + '' + oct.g + '' + oct.o;
    } else {
      octalStr = oct.u + '' + oct.g + '' + oct.o;
    }

    document.getElementById('chj-out-octal').textContent = octalStr;
    document.getElementById('chj-out-sym-parts').innerHTML =
      '<span class="chj-sym-part chj-sym-owner">' + sym.u + '</span>' +
      '<span class="chj-sym-part chj-sym-group">' + sym.g + '</span>' +
      '<span class="chj-sym-part chj-sym-others">' + sym.o + '</span>';
    document.getElementById('chj-out-sym-full').textContent = sym.u + sym.g + sym.o;
    document.getElementById('chj-cmd-text').textContent = 'chmod ' + octalStr + ' filename';
    document.getElementById('chj-octal-input').value = octalStr;

    var btn = document.getElementById('chj-copy-btn');
    btn.textContent = 'コピー';
    btn.classList.remove('copied');
  };

  window.chjFromOctal = function(val) {
    val = val.replace(/[^0-7]/g, '');
    if (val.length < 3 || val.length > 4) return;

    var digits;
    var special = 0;
    if (val.length === 4) {
      special = parseInt(val[0], 8);
      digits = [parseInt(val[1], 8), parseInt(val[2], 8), parseInt(val[3], 8)];
    } else {
      digits = [parseInt(val[0], 8), parseInt(val[1], 8), parseInt(val[2], 8)];
    }

    function setRow(d, prefix) {
      document.getElementById('chj-' + prefix + 'r').checked = !!(d & 4);
      document.getElementById('chj-' + prefix + 'w').checked = !!(d & 2);
      document.getElementById('chj-' + prefix + 'x').checked = !!(d & 1);
    }

    setRow(digits[0], 'u');
    setRow(digits[1], 'g');
    setRow(digits[2], 'o');
    document.getElementById('chj-setuid').checked = !!(special & 4);
    document.getElementById('chj-setgid').checked = !!(special & 2);
    document.getElementById('chj-sticky').checked = !!(special & 1);

    chjUpdate();
  };

  window.chjApplyPreset = function(val) {
    chjFromOctal(String(val));
    document.getElementById('chj-octal-input').value = String(val);
  };

  window.chjCopyCmd = function() {
    var cmd = document.getElementById('chj-cmd-text').textContent;
    navigator.clipboard.writeText(cmd).then(function() {
      var btn = document.getElementById('chj-copy-btn');
      btn.textContent = 'コピーしました!';
      btn.classList.add('copied');
      setTimeout(function() {
        btn.textContent = 'コピー';
        btn.classList.remove('copied');
      }, 2000);
    }).catch(function() {
      var ta = document.createElement('textarea');
      ta.value = cmd;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      var btn = document.getElementById('chj-copy-btn');
      btn.textContent = 'コピーしました!';
      btn.classList.add('copied');
      setTimeout(function() {
        btn.textContent = 'コピー';
        btn.classList.remove('copied');
      }, 2000);
    });
  };

  // Initialize to 755
  chjApplyPreset(755);
})();
</script>

---

### 関連ツール

> Cron式を生成 → [Cron式ジェネレーター](/ja/tools/cron-generator/)

> .htaccessを生成 → [.htaccessジェネレーター](/ja/tools/htaccess-generator/)

> SQLを整形 → [SQLフォーマッター](/ja/tools/sql-formatter/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
