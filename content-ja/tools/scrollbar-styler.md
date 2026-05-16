---
title: "CSSスクロールバー スタイラー"
date: 2025-05-16
description: "無料のCSSスクロールバーカスタマイズツール。幅・色・角丸・ホバー効果をライブプレビューで設定し、WebKit/Firefox用CSSを即コピー。"
categories: ["無料ツール"]
slug: "scrollbar-styler"
ShowToc: false
cover:
  image: "/images/covers/scrollbar-styler-ja.png"
  alt: "CSSスクロールバー スタイラー"
---

<div id="sb-app" style="font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans','Yu Gothic UI','Segoe UI',Roboto,sans-serif;max-width:900px;margin:0 auto;">

<style>
#sb-app *,#sb-app *::before,#sb-app *::after{box-sizing:border-box;}
#sb-app h2{font-size:1.1rem;font-weight:700;margin:0 0 12px;color:#1e293b;}
#sb-app .sb-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:20px;}
@media(max-width:640px){#sb-app .sb-grid{grid-template-columns:1fr;}}
#sb-app .sb-panel{background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;padding:18px;}
#sb-app .sb-control{margin-bottom:14px;}
#sb-app .sb-control label{display:block;font-size:13px;font-weight:600;color:#475569;margin-bottom:5px;}
#sb-app .sb-control input[type=range]{width:100%;accent-color:#6366f1;}
#sb-app .sb-control input[type=color]{width:48px;height:32px;border:1px solid #cbd5e1;border-radius:6px;cursor:pointer;padding:2px;}
#sb-app .sb-color-row{display:flex;align-items:center;gap:10px;}
#sb-app .sb-color-row input[type=text]{flex:1;padding:6px 10px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;font-family:monospace;}
#sb-app .sb-select{width:100%;padding:7px 10px;border:1px solid #cbd5e1;border-radius:6px;font-size:13px;background:#fff;}
#sb-app .sb-val{font-size:12px;color:#6366f1;font-weight:700;margin-left:6px;}
#sb-app .sb-presets{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px;}
#sb-app .sb-preset-btn{padding:7px 15px;border:1.5px solid #cbd5e1;border-radius:20px;font-size:13px;font-weight:600;cursor:pointer;background:#fff;color:#334155;transition:all .18s;}
#sb-app .sb-preset-btn:hover{border-color:#6366f1;color:#6366f1;}
#sb-app .sb-preset-btn.active{background:#6366f1;color:#fff;border-color:#6366f1;}
#sb-app .sb-preview-wrap{margin-bottom:20px;}
#sb-app .sb-preview-box{height:180px;overflow-y:scroll;border:1px solid #e2e8f0;border-radius:10px;padding:16px;background:#fff;font-size:14px;color:#475569;line-height:1.7;}
#sb-app .sb-output-wrap{margin-bottom:20px;}
#sb-app .sb-tabs{display:flex;gap:0;margin-bottom:0;}
#sb-app .sb-tab{padding:8px 18px;font-size:13px;font-weight:600;cursor:pointer;border:1.5px solid #e2e8f0;border-bottom:none;border-radius:8px 8px 0 0;background:#f1f5f9;color:#64748b;transition:all .15s;}
#sb-app .sb-tab.active{background:#1e293b;color:#fff;border-color:#1e293b;}
#sb-app .sb-code-block{position:relative;background:#1e293b;border-radius:0 10px 10px 10px;padding:18px 16px;min-height:120px;overflow-x:auto;}
#sb-app .sb-code-block pre{margin:0;font-family:'Fira Code','Cascadia Code',monospace;font-size:13px;line-height:1.7;white-space:pre-wrap;color:#e2e8f0;}
#sb-app .sb-kw{color:#c084fc;}
#sb-app .sb-prop{color:#67e8f9;}
#sb-app .sb-val-c{color:#86efac;}
#sb-app .sb-copy-btn{position:absolute;top:10px;right:10px;padding:6px 14px;background:#6366f1;color:#fff;border:none;border-radius:6px;font-size:12px;font-weight:700;cursor:pointer;transition:background .15s;}
#sb-app .sb-copy-btn:hover{background:#4f46e5;}
#sb-app .sb-copy-btn.copied{background:#10b981;}
#sb-app .sb-scope-row{display:flex;align-items:center;gap:10px;margin-bottom:20px;padding:12px 16px;background:#fefce8;border:1px solid #fde68a;border-radius:8px;flex-wrap:wrap;}
#sb-app .sb-scope-row label{font-size:13px;font-weight:600;color:#92400e;margin:0;}
#sb-app .sb-scope-row input[type=text]{flex:1;min-width:120px;padding:6px 10px;border:1px solid #fcd34d;border-radius:6px;font-size:13px;font-family:monospace;background:#fff;}
#sb-app .sb-compat{margin-top:20px;padding:14px 18px;background:#f0fdf4;border:1px solid #bbf7d0;border-radius:10px;}
#sb-app .sb-compat h3{margin:0 0 8px;font-size:14px;font-weight:700;color:#166534;}
#sb-app .sb-compat table{width:100%;border-collapse:collapse;font-size:13px;}
#sb-app .sb-compat th{text-align:left;padding:4px 8px;color:#166534;font-weight:600;border-bottom:1px solid #bbf7d0;}
#sb-app .sb-compat td{padding:4px 8px;color:#374151;}
#sb-app .sb-compat .ok{color:#16a34a;font-weight:700;}
#sb-app .sb-compat .no{color:#dc2626;font-weight:700;}
#sb-app .sb-crosslinks{margin-top:24px;padding:14px 18px;background:#f8fafc;border:1px solid #e2e8f0;border-radius:10px;font-size:14px;}
#sb-app .sb-crosslinks p{margin:4px 0;}
#sb-app .sb-crosslinks a{color:#6366f1;text-decoration:none;font-weight:600;}
#sb-app .sb-crosslinks a:hover{text-decoration:underline;}
</style>

<!-- ヘッダー -->
<div style="margin-bottom:8px;">
  <h2 style="font-size:1.25rem;margin-bottom:4px;">CSSスクロールバー スタイラー</h2>
  <p style="font-size:14px;color:#64748b;margin:0 0 14px;">スクロールバーの幅・色・角丸・ホバー効果をカスタマイズして、即コピーできるCSSを生成します。</p>
</div>

<!-- プリセット -->
<div class="sb-presets" id="sb-presets">
  <button class="sb-preset-btn" data-preset="minimal" onclick="sbApplyPreset('minimal')">ミニマル</button>
  <button class="sb-preset-btn" data-preset="dark" onclick="sbApplyPreset('dark')">ダークモード</button>
  <button class="sb-preset-btn" data-preset="colorful" onclick="sbApplyPreset('colorful')">カラフル</button>
  <button class="sb-preset-btn" data-preset="rounded" onclick="sbApplyPreset('rounded')">丸型</button>
  <button class="sb-preset-btn" data-preset="hidden" onclick="sbApplyPreset('hidden')">非表示</button>
</div>

<div class="sb-grid">
  <!-- コントロール -->
  <div class="sb-panel">
    <h2>コントロール</h2>

    <div class="sb-control">
      <label>スクロールバー幅モード</label>
      <select class="sb-select" id="sb-width-mode" onchange="sbWidthModeChange()">
        <option value="auto">auto（デフォルト）</option>
        <option value="thin">thin（細め）</option>
        <option value="custom" selected>カスタム（px指定）</option>
      </select>
    </div>

    <div class="sb-control" id="sb-custom-width-wrap">
      <label>カスタム幅: <span class="sb-val" id="sb-width-val">10px</span></label>
      <input type="range" id="sb-width" min="2" max="32" value="10" oninput="sbUpdate()">
    </div>

    <div class="sb-control">
      <label>トラック色（背景）</label>
      <div class="sb-color-row">
        <input type="color" id="sb-track-color" value="#f1f5f9" oninput="sbSyncColor('sb-track-color','sb-track-color-hex')">
        <input type="text" id="sb-track-color-hex" value="#f1f5f9" oninput="sbSyncHex('sb-track-color','sb-track-color-hex')" maxlength="9">
      </div>
    </div>

    <div class="sb-control">
      <label>サム色（つまみ）</label>
      <div class="sb-color-row">
        <input type="color" id="sb-thumb-color" value="#94a3b8" oninput="sbSyncColor('sb-thumb-color','sb-thumb-color-hex')">
        <input type="text" id="sb-thumb-color-hex" value="#94a3b8" oninput="sbSyncHex('sb-thumb-color','sb-thumb-color-hex')" maxlength="9">
      </div>
    </div>

    <div class="sb-control">
      <label>サム ホバー色</label>
      <div class="sb-color-row">
        <input type="color" id="sb-thumb-hover-color" value="#6366f1" oninput="sbSyncColor('sb-thumb-hover-color','sb-thumb-hover-hex')">
        <input type="text" id="sb-thumb-hover-hex" value="#6366f1" oninput="sbSyncHex('sb-thumb-hover-color','sb-thumb-hover-hex')" maxlength="9">
      </div>
    </div>

    <div class="sb-control">
      <label>サム 角丸: <span class="sb-val" id="sb-thumb-radius-val">6px</span></label>
      <input type="range" id="sb-thumb-radius" min="0" max="50" value="6" oninput="sbUpdate()">
    </div>

    <div class="sb-control">
      <label>トラック 角丸: <span class="sb-val" id="sb-track-radius-val">0px</span></label>
      <input type="range" id="sb-track-radius" min="0" max="50" value="0" oninput="sbUpdate()">
    </div>
  </div>

  <!-- ライブプレビュー -->
  <div class="sb-panel">
    <h2>ライブプレビュー</h2>
    <div class="sb-preview-box" id="sb-preview">
      <p>スクロールしてカスタムスクロールバーを確認できます。左のコントロールで設定を変更すると、リアルタイムでプレビューに反映されます。</p>
      <p>幅・トラック色・サム色・ホバー色・角丸をそれぞれ細かく調整できます。プリセットを使えば素早くスタイルを適用可能です。</p>
      <p>「非表示」プリセットを選ぶと、スクロール機能を保ちつつスクロールバーを見えなくできます。</p>
      <p>生成したCSSは下のタブからコピーしてご利用ください。WebKit（Chrome・Safari・Edge）とFirefox両対応のCSSを出力します。</p>
      <p>セレクター指定で特定の要素だけに適用することも可能です。グローバルに適用する場合は <code>body</code> のままにしてください。</p>
    </div>
    <p style="font-size:12px;color:#94a3b8;margin:6px 0 0;">現在の設定がプレビューに反映されています。</p>
  </div>
</div>

<!-- 適用先セレクター -->
<div class="sb-scope-row">
  <label>適用先セレクター:</label>
  <input type="text" id="sb-scope" value="body" oninput="sbUpdate()" placeholder="例: body, .my-container, #sidebar">
  <span style="font-size:12px;color:#92400e;"><code>body</code> のままでグローバル適用。</span>
</div>

<!-- CSS出力 -->
<div class="sb-output-wrap">
  <div class="sb-tabs">
    <div class="sb-tab active" id="sb-tab-webkit" onclick="sbShowTab('webkit')">WebKit（Chrome/Safari/Edge）</div>
    <div class="sb-tab" id="sb-tab-firefox" onclick="sbShowTab('firefox')">Firefox</div>
    <div class="sb-tab" id="sb-tab-combined" onclick="sbShowTab('combined')">まとめてコピー</div>
  </div>
  <div class="sb-code-block">
    <pre id="sb-output"></pre>
    <button class="sb-copy-btn" id="sb-copy-btn" onclick="sbCopy()">CSSをコピー</button>
  </div>
</div>

<!-- ブラウザ互換性 -->
<div class="sb-compat">
  <h3>ブラウザ互換性</h3>
  <table>
    <thead>
      <tr>
        <th>プロパティ</th>
        <th>Chrome</th>
        <th>Firefox</th>
        <th>Safari</th>
        <th>Edge</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>::-webkit-scrollbar</code></td>
        <td class="ok">対応</td>
        <td class="no">非対応</td>
        <td class="ok">対応</td>
        <td class="ok">対応</td>
      </tr>
      <tr>
        <td><code>scrollbar-width</code></td>
        <td class="ok">121以降</td>
        <td class="ok">対応</td>
        <td class="ok">16以降</td>
        <td class="ok">121以降</td>
      </tr>
      <tr>
        <td><code>scrollbar-color</code></td>
        <td class="ok">121以降</td>
        <td class="ok">対応</td>
        <td class="ok">16以降</td>
        <td class="ok">121以降</td>
      </tr>
      <tr>
        <td>ホバー効果</td>
        <td class="ok">対応（WebKit）</td>
        <td class="no">非対応</td>
        <td class="ok">対応（WebKit）</td>
        <td class="ok">対応（WebKit）</td>
      </tr>
    </tbody>
  </table>
  <p style="margin:8px 0 0;font-size:12px;color:#374151;"><strong>ヒント:</strong>「まとめてコピー」タブで全ブラウザ対応のCSSを一括取得できます。Firefoxはホバー色の個別指定に非対応です。</p>
</div>

<!-- freee CTA -->
<div class="sb-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">Web制作の経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、デザインツール・サーバー費用の経費精算もクラウドで一元管理。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<!-- 関連ツール -->
<div class="sb-crosslinks">
  <p>ボタンをスタイル &rarr; <a href="/ja/tools/css-button-generator/">CSSボタンジェネレーター</a></p>
  <p>アニメーションをカスタマイズ &rarr; <a href="/ja/tools/css-animation-generator/">CSSアニメーションジェネレーター</a></p>
  <p>CSS変数 &rarr; <a href="/ja/tools/css-variables-generator/">CSS変数ジェネレーター</a></p>
</div>

<script>
(function(){
  var currentTab = 'webkit';

  var presets = {
    minimal: {
      widthMode:'thin', width:6,
      trackColor:'#f8fafc', thumbColor:'#cbd5e1', thumbHover:'#94a3b8',
      thumbRadius:2, trackRadius:0
    },
    dark: {
      widthMode:'custom', width:8,
      trackColor:'#1e293b', thumbColor:'#475569', thumbHover:'#94a3b8',
      thumbRadius:4, trackRadius:0
    },
    colorful: {
      widthMode:'custom', width:12,
      trackColor:'#fef3c7', thumbColor:'#f59e0b', thumbHover:'#d97706',
      thumbRadius:6, trackRadius:4
    },
    rounded: {
      widthMode:'custom', width:10,
      trackColor:'#f0fdf4', thumbColor:'#4ade80', thumbHover:'#16a34a',
      thumbRadius:50, trackRadius:50
    },
    hidden: {
      widthMode:'thin', width:0,
      trackColor:'transparent', thumbColor:'transparent', thumbHover:'transparent',
      thumbRadius:0, trackRadius:0
    }
  };

  function g(id){ return document.getElementById(id); }

  function sbApplyPreset(name){
    var p = presets[name];
    if(!p) return;
    g('sb-width-mode').value = p.widthMode;
    g('sb-width').value = p.width;
    g('sb-track-color').value = p.trackColor;
    g('sb-track-color-hex').value = p.trackColor;
    g('sb-thumb-color').value = p.thumbColor;
    g('sb-thumb-color-hex').value = p.thumbColor;
    g('sb-thumb-hover-color').value = p.thumbHover;
    g('sb-thumb-hover-hex').value = p.thumbHover;
    g('sb-thumb-radius').value = p.thumbRadius;
    g('sb-track-radius').value = p.trackRadius;
    sbWidthModeChange();
    document.querySelectorAll('#sb-app .sb-preset-btn').forEach(function(b){
      b.classList.toggle('active', b.dataset.preset === name);
    });
    sbUpdate();
  }

  function sbWidthModeChange(){
    var mode = g('sb-width-mode').value;
    var wrap = g('sb-custom-width-wrap');
    wrap.style.display = (mode === 'custom') ? '' : 'none';
    sbUpdate();
  }

  function sbSyncColor(colorId, hexId){
    g(hexId).value = g(colorId).value;
    sbUpdate();
  }

  function sbSyncHex(colorId, hexId){
    var val = g(hexId).value;
    if(/^#([0-9a-fA-F]{3}|[0-9a-fA-F]{6})$/.test(val)){
      g(colorId).value = val;
    }
    sbUpdate();
  }

  function getState(){
    var widthMode = g('sb-width-mode').value;
    var width = parseInt(g('sb-width').value);
    var trackColor = g('sb-track-color-hex').value || g('sb-track-color').value;
    var thumbColor = g('sb-thumb-color-hex').value || g('sb-thumb-color').value;
    var thumbHover = g('sb-thumb-hover-hex').value || g('sb-thumb-hover-color').value;
    var thumbRadius = parseInt(g('sb-thumb-radius').value);
    var trackRadius = parseInt(g('sb-track-radius').value);
    var scope = g('sb-scope').value.trim() || 'body';
    return {widthMode, width, trackColor, thumbColor, thumbHover, thumbRadius, trackRadius, scope};
  }

  function buildWebkit(s){
    var w = s.widthMode === 'custom' ? s.width + 'px' : s.widthMode === 'thin' ? '6px' : '16px';
    var lines = [];
    lines.push(s.scope + '::-webkit-scrollbar {');
    lines.push('  width: ' + w + ';');
    lines.push('}');
    lines.push(s.scope + '::-webkit-scrollbar-track {');
    lines.push('  background: ' + s.trackColor + ';');
    if(s.trackRadius > 0) lines.push('  border-radius: ' + s.trackRadius + 'px;');
    lines.push('}');
    lines.push(s.scope + '::-webkit-scrollbar-thumb {');
    lines.push('  background: ' + s.thumbColor + ';');
    if(s.thumbRadius > 0) lines.push('  border-radius: ' + s.thumbRadius + 'px;');
    lines.push('}');
    lines.push(s.scope + '::-webkit-scrollbar-thumb:hover {');
    lines.push('  background: ' + s.thumbHover + ';');
    lines.push('}');
    return lines.join('\n');
  }

  function buildFirefox(s){
    var ffWidth = s.widthMode === 'custom' ? (s.width <= 6 ? 'thin' : 'auto') : s.widthMode;
    if(s.trackColor === 'transparent' && s.thumbColor === 'transparent') ffWidth = 'none';
    var lines = [];
    lines.push(s.scope + ' {');
    lines.push('  scrollbar-width: ' + ffWidth + ';');
    lines.push('  scrollbar-color: ' + s.thumbColor + ' ' + s.trackColor + ';');
    lines.push('}');
    return lines.join('\n');
  }

  function buildCombined(s){
    return buildWebkit(s) + '\n\n/* Firefox */\n' + buildFirefox(s);
  }

  function syntaxHighlight(css){
    return css
      .replace(/(::-webkit-[\w-]+(?::[\w-]+)?|scrollbar-[\w-]+)/g, '<span class="sb-prop">$1</span>')
      .replace(/(\/\*[^*]*\*+(?:[^/*][^*]*\*+)*\/)/g, '<span style="color:#64748b;">$1</span>');
  }

  function escHtml(str){
    return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  function sbUpdate(){
    var s = getState();
    g('sb-width-val').textContent = s.width + 'px';
    g('sb-thumb-radius-val').textContent = s.thumbRadius + 'px';
    g('sb-track-radius-val').textContent = s.trackRadius + 'px';

    var styleEl = document.getElementById('sb-preview-style');
    if(!styleEl){
      styleEl = document.createElement('style');
      styleEl.id = 'sb-preview-style';
      document.head.appendChild(styleEl);
    }
    var pw = s.widthMode === 'custom' ? s.width + 'px' : s.widthMode === 'thin' ? '6px' : '16px';
    styleEl.textContent = [
      '#sb-preview::-webkit-scrollbar { width: ' + pw + '; }',
      '#sb-preview::-webkit-scrollbar-track { background: ' + s.trackColor + '; border-radius: ' + s.trackRadius + 'px; }',
      '#sb-preview::-webkit-scrollbar-thumb { background: ' + s.thumbColor + '; border-radius: ' + s.thumbRadius + 'px; }',
      '#sb-preview::-webkit-scrollbar-thumb:hover { background: ' + s.thumbHover + '; }',
      '#sb-preview { scrollbar-width: ' + (s.widthMode === 'thin' ? 'thin' : 'auto') + '; scrollbar-color: ' + s.thumbColor + ' ' + s.trackColor + '; }'
    ].join('\n');

    var code = currentTab === 'webkit' ? buildWebkit(s) : currentTab === 'firefox' ? buildFirefox(s) : buildCombined(s);
    g('sb-output').innerHTML = syntaxHighlight(escHtml(code));
    g('sb-output').dataset.raw = code;
  }

  function sbShowTab(tab){
    currentTab = tab;
    ['webkit','firefox','combined'].forEach(function(t){
      var el = g('sb-tab-' + t);
      if(el) el.classList.toggle('active', t === tab);
    });
    sbUpdate();
  }

  function sbCopy(){
    var raw = g('sb-output').dataset.raw || g('sb-output').textContent;
    navigator.clipboard.writeText(raw).then(function(){
      var btn = g('sb-copy-btn');
      btn.textContent = 'コピーしました!';
      btn.classList.add('copied');
      setTimeout(function(){ btn.textContent = 'CSSをコピー'; btn.classList.remove('copied'); }, 2000);
    });
  }

  window.sbApplyPreset = sbApplyPreset;
  window.sbWidthModeChange = sbWidthModeChange;
  window.sbSyncColor = sbSyncColor;
  window.sbSyncHex = sbSyncHex;
  window.sbShowTab = sbShowTab;
  window.sbCopy = sbCopy;
  window.sbUpdate = sbUpdate;

  sbWidthModeChange();
  sbUpdate();
})();
</script>

</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
