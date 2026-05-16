---
title: "CSS Flexboxプレイグラウンド"
date: 2025-05-16
description: "無料のCSS Flexboxプレイグラウンド。全プロパティをビジュアルで実験。ライブプレビュー・CSSコードコピー対応。"
categories: ["無料ツール"]
slug: "flexbox-playground"
ShowToc: false
cover:
  image: "/images/covers/flexbox-playground-ja.png"
  alt: "CSS Flexboxプレイグラウンド"
---

<div id="fb-app">
<style>
  #fb-app *, #fb-app *::before, #fb-app *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #fb-app {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", Roboto, sans-serif;
    font-size: 14px;
    color: #1a1a2e;
    background: #f8f9ff;
    border-radius: 12px;
    padding: 24px;
    max-width: 100%;
    overflow: hidden;
  }
  #fb-app h2.fb-title {
    font-size: 1.4rem;
    font-weight: 700;
    margin-bottom: 4px;
    color: #1a1a2e;
  }
  #fb-app p.fb-subtitle {
    color: #666;
    margin-bottom: 20px;
    font-size: 0.9rem;
  }
  #fb-app .fb-layout {
    display: grid;
    grid-template-columns: 300px 1fr;
    gap: 20px;
    align-items: start;
  }
  @media (max-width: 768px) {
    #fb-app .fb-layout {
      grid-template-columns: 1fr;
    }
  }
  #fb-app .fb-panel {
    background: #fff;
    border: 1.5px solid #dde1ff;
    border-radius: 10px;
    overflow: hidden;
  }
  #fb-app .fb-panel-header {
    background: linear-gradient(90deg, #4f46e5 0%, #7c3aed 100%);
    color: #fff;
    font-weight: 700;
    font-size: 0.85rem;
    padding: 9px 14px;
    letter-spacing: 0.03em;
  }
  #fb-app .fb-panel-body {
    padding: 14px;
  }
  #fb-app .fb-control-group {
    margin-bottom: 12px;
  }
  #fb-app .fb-control-group:last-child {
    margin-bottom: 0;
  }
  #fb-app .fb-label {
    display: block;
    font-size: 0.78rem;
    font-weight: 600;
    color: #4f46e5;
    margin-bottom: 4px;
    font-family: "Courier New", monospace;
  }
  #fb-app select.fb-select,
  #fb-app input.fb-input {
    width: 100%;
    padding: 6px 10px;
    border: 1.5px solid #c7d2fe;
    border-radius: 7px;
    font-size: 0.85rem;
    color: #1a1a2e;
    background: #f5f7ff;
    appearance: none;
    -webkit-appearance: none;
    cursor: pointer;
    outline: none;
    transition: border-color 0.15s;
  }
  #fb-app select.fb-select:focus,
  #fb-app input.fb-input:focus {
    border-color: #4f46e5;
    background: #fff;
  }
  #fb-app input[type="range"].fb-range {
    width: 100%;
    accent-color: #4f46e5;
    cursor: pointer;
  }
  #fb-app .fb-range-row {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  #fb-app .fb-range-val {
    min-width: 38px;
    font-size: 0.82rem;
    font-weight: 700;
    color: #4f46e5;
    text-align: right;
  }
  #fb-app .fb-section-title {
    font-size: 0.72rem;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: #7c3aed;
    border-bottom: 1.5px solid #ede9fe;
    padding-bottom: 4px;
    margin-bottom: 10px;
    margin-top: 14px;
  }
  #fb-app .fb-section-title:first-child {
    margin-top: 0;
  }
  #fb-app .fb-item-count-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 14px;
  }
  #fb-app .fb-count-btn {
    width: 28px;
    height: 28px;
    border-radius: 50%;
    border: 2px solid #4f46e5;
    background: #fff;
    color: #4f46e5;
    font-size: 1.1rem;
    font-weight: 700;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 1;
    transition: all 0.15s;
  }
  #fb-app .fb-count-btn:hover {
    background: #4f46e5;
    color: #fff;
  }
  #fb-app .fb-count-display {
    font-size: 0.9rem;
    font-weight: 700;
    min-width: 70px;
    color: #1a1a2e;
  }
  #fb-app .fb-item-tabs {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    margin-bottom: 12px;
  }
  #fb-app .fb-item-tab {
    padding: 4px 10px;
    border-radius: 5px;
    border: 1.5px solid #c7d2fe;
    background: #f5f7ff;
    font-size: 0.78rem;
    font-weight: 600;
    cursor: pointer;
    color: #4f46e5;
    transition: all 0.15s;
  }
  #fb-app .fb-item-tab.active {
    background: #4f46e5;
    color: #fff;
    border-color: #4f46e5;
  }
  #fb-app .fb-item-tab:hover:not(.active) {
    background: #ede9fe;
  }
  #fb-app .fb-right {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  #fb-app .fb-preview-wrap {
    background: #fff;
    border: 1.5px solid #dde1ff;
    border-radius: 10px;
    overflow: hidden;
  }
  #fb-app .fb-preview-header {
    background: linear-gradient(90deg, #4f46e5 0%, #7c3aed 100%);
    color: #fff;
    font-weight: 700;
    font-size: 0.85rem;
    padding: 9px 14px;
  }
  #fb-app .fb-preview-container {
    padding: 20px;
    background: #f0f4ff;
    min-height: 220px;
    position: relative;
  }
  #fb-app .fb-preview-inner {
    background: #e8eeff;
    border: 2px dashed #a5b4fc;
    border-radius: 8px;
    min-height: 180px;
    padding: 8px;
    width: 100%;
    overflow: auto;
  }
  #fb-app .fb-flex-container {
    width: 100%;
    min-height: 160px;
  }
  #fb-app .fb-flex-item {
    min-width: 40px;
    min-height: 50px;
    border-radius: 7px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 1rem;
    color: #fff;
    text-shadow: 0 1px 3px rgba(0,0,0,0.25);
    cursor: pointer;
    transition: box-shadow 0.15s, outline 0.15s;
  }
  #fb-app .fb-flex-item.selected-item {
    outline: 3px solid #1a1a2e;
    outline-offset: 2px;
  }
  #fb-app .fb-code-wrap {
    background: #fff;
    border: 1.5px solid #dde1ff;
    border-radius: 10px;
    overflow: hidden;
  }
  #fb-app .fb-code-header {
    background: linear-gradient(90deg, #4f46e5 0%, #7c3aed 100%);
    color: #fff;
    font-weight: 700;
    font-size: 0.85rem;
    padding: 9px 14px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  #fb-app .fb-copy-btn {
    background: rgba(255,255,255,0.2);
    border: 1.5px solid rgba(255,255,255,0.5);
    color: #fff;
    border-radius: 6px;
    padding: 3px 12px;
    font-size: 0.78rem;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.15s;
  }
  #fb-app .fb-copy-btn:hover {
    background: rgba(255,255,255,0.35);
  }
  #fb-app .fb-copy-btn.copied {
    background: #10b981;
    border-color: #10b981;
  }
  #fb-app pre.fb-code {
    margin: 0;
    padding: 14px 16px;
    background: #1e1b4b;
    color: #c4b5fd;
    font-family: "Courier New", Courier, monospace;
    font-size: 0.82rem;
    line-height: 1.6;
    overflow-x: auto;
    white-space: pre;
  }
  #fb-app pre.fb-code .fb-prop { color: #a5f3fc; }
  #fb-app pre.fb-code .fb-val  { color: #fde68a; }
  #fb-app pre.fb-code .fb-sel  { color: #86efac; }
  #fb-app pre.fb-code .fb-brace{ color: #f0abfc; }
</style>

<h2 class="fb-title">CSS Flexbox プレイグラウンド</h2>
<p class="fb-subtitle">すべてのFlexboxプロパティをビジュアルで実験できます。アイテムをクリックして個別プロパティを調整。生成CSSはそのままコピー可能。</p>

<div class="fb-layout">
  <!-- 左: コントロール -->
  <div>
    <!-- アイテム数 -->
    <div class="fb-panel" style="margin-bottom:16px;">
      <div class="fb-panel-header">アイテム数</div>
      <div class="fb-panel-body">
        <div class="fb-item-count-row">
          <button class="fb-count-btn" id="fb-remove-item">&#8722;</button>
          <span class="fb-count-display" id="fb-item-count-label">3 個</span>
          <button class="fb-count-btn" id="fb-add-item">&#43;</button>
        </div>
        <div class="fb-item-tabs" id="fb-item-tabs"></div>
      </div>
    </div>

    <!-- コンテナプロパティ -->
    <div class="fb-panel" style="margin-bottom:16px;">
      <div class="fb-panel-header">コンテナのプロパティ</div>
      <div class="fb-panel-body">
        <p class="fb-section-title">flex-direction</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-flex-direction">
            <option value="row">row — 横方向</option>
            <option value="row-reverse">row-reverse — 横逆</option>
            <option value="column">column — 縦方向</option>
            <option value="column-reverse">column-reverse — 縦逆</option>
          </select>
        </div>
        <p class="fb-section-title">flex-wrap</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-flex-wrap">
            <option value="nowrap">nowrap — 折り返しなし</option>
            <option value="wrap">wrap — 折り返しあり</option>
            <option value="wrap-reverse">wrap-reverse — 逆折り返し</option>
          </select>
        </div>
        <p class="fb-section-title">justify-content</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-justify-content">
            <option value="flex-start">flex-start — 先頭寄せ</option>
            <option value="flex-end">flex-end — 末尾寄せ</option>
            <option value="center">center — 中央</option>
            <option value="space-between">space-between</option>
            <option value="space-around">space-around</option>
            <option value="space-evenly">space-evenly</option>
          </select>
        </div>
        <p class="fb-section-title">align-items</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-align-items">
            <option value="stretch">stretch — 引き伸ばし</option>
            <option value="flex-start">flex-start</option>
            <option value="flex-end">flex-end</option>
            <option value="center">center — 中央</option>
            <option value="baseline">baseline</option>
          </select>
        </div>
        <p class="fb-section-title">align-content</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-align-content">
            <option value="normal">normal</option>
            <option value="flex-start">flex-start</option>
            <option value="flex-end">flex-end</option>
            <option value="center">center</option>
            <option value="space-between">space-between</option>
            <option value="space-around">space-around</option>
            <option value="space-evenly">space-evenly</option>
            <option value="stretch">stretch</option>
          </select>
        </div>
        <p class="fb-section-title">gap（間隔）</p>
        <div class="fb-control-group">
          <div class="fb-range-row">
            <input type="range" class="fb-range" id="fb-gap" min="0" max="40" value="8" step="2">
            <span class="fb-range-val" id="fb-gap-val">8px</span>
          </div>
        </div>
      </div>
    </div>

    <!-- アイテムプロパティ -->
    <div class="fb-panel">
      <div class="fb-panel-header">アイテムのプロパティ <span id="fb-item-label" style="opacity:0.75;font-weight:400;">（アイテム1）</span></div>
      <div class="fb-panel-body">
        <p class="fb-section-title">order（順序）</p>
        <div class="fb-control-group">
          <div class="fb-range-row">
            <input type="range" class="fb-range" id="fb-order" min="-5" max="10" value="0" step="1">
            <span class="fb-range-val" id="fb-order-val">0</span>
          </div>
        </div>
        <p class="fb-section-title">flex-grow（拡大）</p>
        <div class="fb-control-group">
          <div class="fb-range-row">
            <input type="range" class="fb-range" id="fb-flex-grow" min="0" max="10" value="0" step="1">
            <span class="fb-range-val" id="fb-flex-grow-val">0</span>
          </div>
        </div>
        <p class="fb-section-title">flex-shrink（縮小）</p>
        <div class="fb-control-group">
          <div class="fb-range-row">
            <input type="range" class="fb-range" id="fb-flex-shrink" min="0" max="10" value="1" step="1">
            <span class="fb-range-val" id="fb-flex-shrink-val">1</span>
          </div>
        </div>
        <p class="fb-section-title">flex-basis（基本サイズ）</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-flex-basis">
            <option value="auto">auto</option>
            <option value="0">0</option>
            <option value="50px">50px</option>
            <option value="80px">80px</option>
            <option value="100px">100px</option>
            <option value="120px">120px</option>
            <option value="150px">150px</option>
            <option value="200px">200px</option>
            <option value="25%">25%</option>
            <option value="33%">33%</option>
            <option value="50%">50%</option>
          </select>
        </div>
        <p class="fb-section-title">align-self（個別揃え）</p>
        <div class="fb-control-group">
          <select class="fb-select" id="fb-align-self">
            <option value="auto">auto</option>
            <option value="flex-start">flex-start</option>
            <option value="flex-end">flex-end</option>
            <option value="center">center</option>
            <option value="baseline">baseline</option>
            <option value="stretch">stretch</option>
          </select>
        </div>
      </div>
    </div>
  </div>

  <!-- 右: プレビュー + コード -->
  <div class="fb-right">
    <div class="fb-preview-wrap">
      <div class="fb-preview-header">ライブプレビュー</div>
      <div class="fb-preview-container">
        <div class="fb-preview-inner">
          <div class="fb-flex-container" id="fb-flex-container"></div>
        </div>
      </div>
    </div>

    <div class="fb-code-wrap">
      <div class="fb-code-header">
        <span>生成CSS</span>
        <button class="fb-copy-btn" id="fb-copy-btn">CSSをコピー</button>
      </div>
      <pre class="fb-code" id="fb-code-output"></pre>
    </div>
  </div>
</div>

<script>
(function() {
  var COLORS = [
    '#4f46e5','#7c3aed','#db2777','#ea580c','#16a34a',
    '#0891b2','#b45309','#dc2626','#6d28d9','#0284c7',
    '#059669','#c026d3'
  ];
  var MAX_ITEMS = 12;
  var MIN_ITEMS = 1;

  var state = {
    itemCount: 3,
    selectedItem: 0,
    container: {
      flexDirection: 'row',
      flexWrap: 'nowrap',
      justifyContent: 'flex-start',
      alignItems: 'stretch',
      alignContent: 'normal',
      gap: 8
    },
    items: []
  };

  function makeDefaultItem() {
    return { order: 0, flexGrow: 0, flexShrink: 1, flexBasis: 'auto', alignSelf: 'auto' };
  }
  for (var i = 0; i < MAX_ITEMS; i++) state.items.push(makeDefaultItem());

  var g = function(id) { return document.getElementById(id); };
  var fdEl  = g('fb-flex-direction');
  var fwEl  = g('fb-flex-wrap');
  var jcEl  = g('fb-justify-content');
  var aiEl  = g('fb-align-items');
  var acEl  = g('fb-align-content');
  var gapEl = g('fb-gap');
  var gapVal= g('fb-gap-val');
  var ordEl = g('fb-order');
  var ordVal= g('fb-order-val');
  var fgEl  = g('fb-flex-grow');
  var fgVal = g('fb-flex-grow-val');
  var fsEl  = g('fb-flex-shrink');
  var fsVal = g('fb-flex-shrink-val');
  var fbEl  = g('fb-flex-basis');
  var asEl  = g('fb-align-self');
  var container = g('fb-flex-container');
  var codeOut = g('fb-code-output');
  var tabsEl = g('fb-item-tabs');
  var countLabel = g('fb-item-count-label');
  var itemLabel = g('fb-item-label');
  var copyBtn = g('fb-copy-btn');

  function renderTabs() {
    tabsEl.innerHTML = '';
    for (var i = 0; i < state.itemCount; i++) {
      (function(idx) {
        var btn = document.createElement('button');
        btn.className = 'fb-item-tab' + (idx === state.selectedItem ? ' active' : '');
        btn.textContent = 'アイテム' + (idx + 1);
        btn.style.borderColor = COLORS[idx];
        if (idx === state.selectedItem) btn.style.background = COLORS[idx];
        btn.addEventListener('click', function() {
          state.selectedItem = idx;
          loadItemControls();
          renderTabs();
          renderPreview();
        });
        tabsEl.appendChild(btn);
      })(i);
    }
    countLabel.textContent = state.itemCount + ' 個';
    itemLabel.textContent = '（アイテム' + (state.selectedItem + 1) + '）';
  }

  function loadItemControls() {
    var it = state.items[state.selectedItem];
    ordEl.value = it.order;    ordVal.textContent = it.order;
    fgEl.value  = it.flexGrow; fgVal.textContent  = it.flexGrow;
    fsEl.value  = it.flexShrink; fsVal.textContent = it.flexShrink;
    fbEl.value  = it.flexBasis;
    asEl.value  = it.alignSelf;
    itemLabel.textContent = '（アイテム' + (state.selectedItem + 1) + '）';
  }

  function renderPreview() {
    var c = state.container;
    container.style.display = 'flex';
    container.style.flexDirection = c.flexDirection;
    container.style.flexWrap = c.flexWrap;
    container.style.justifyContent = c.justifyContent;
    container.style.alignItems = c.alignItems;
    container.style.alignContent = c.alignContent;
    container.style.gap = c.gap + 'px';

    while (container.children.length > state.itemCount) {
      container.removeChild(container.lastChild);
    }
    for (var i = 0; i < state.itemCount; i++) {
      var el = container.children[i];
      if (!el) {
        el = document.createElement('div');
        el.className = 'fb-flex-item';
        container.appendChild(el);
      }
      var it = state.items[i];
      el.style.order = it.order;
      el.style.flexGrow = it.flexGrow;
      el.style.flexShrink = it.flexShrink;
      el.style.flexBasis = it.flexBasis;
      el.style.alignSelf = it.alignSelf;
      el.style.background = COLORS[i];
      el.textContent = i + 1;
      el.className = 'fb-flex-item' + (i === state.selectedItem ? ' selected-item' : '');
      (function(idx) {
        el.onclick = function() {
          state.selectedItem = idx;
          loadItemControls();
          renderTabs();
          renderPreview();
        };
      })(i);
    }
    renderCode();
  }

  function renderCode() {
    var c = state.container;
    var lines = [];
    lines.push('<span class="fb-sel">.container</span> <span class="fb-brace">{</span>');
    lines.push('  <span class="fb-prop">display</span>: <span class="fb-val">flex</span>;');
    if (c.flexDirection !== 'row')
      lines.push('  <span class="fb-prop">flex-direction</span>: <span class="fb-val">' + c.flexDirection + '</span>;');
    if (c.flexWrap !== 'nowrap')
      lines.push('  <span class="fb-prop">flex-wrap</span>: <span class="fb-val">' + c.flexWrap + '</span>;');
    if (c.justifyContent !== 'flex-start')
      lines.push('  <span class="fb-prop">justify-content</span>: <span class="fb-val">' + c.justifyContent + '</span>;');
    if (c.alignItems !== 'stretch')
      lines.push('  <span class="fb-prop">align-items</span>: <span class="fb-val">' + c.alignItems + '</span>;');
    if (c.alignContent !== 'normal')
      lines.push('  <span class="fb-prop">align-content</span>: <span class="fb-val">' + c.alignContent + '</span>;');
    if (c.gap > 0)
      lines.push('  <span class="fb-prop">gap</span>: <span class="fb-val">' + c.gap + 'px</span>;');
    lines.push('<span class="fb-brace">}</span>');

    for (var i = 0; i < state.itemCount; i++) {
      var it = state.items[i];
      var itemLines = [];
      if (it.order !== 0)          itemLines.push('  <span class="fb-prop">order</span>: <span class="fb-val">' + it.order + '</span>;');
      if (it.flexGrow !== 0)       itemLines.push('  <span class="fb-prop">flex-grow</span>: <span class="fb-val">' + it.flexGrow + '</span>;');
      if (it.flexShrink !== 1)     itemLines.push('  <span class="fb-prop">flex-shrink</span>: <span class="fb-val">' + it.flexShrink + '</span>;');
      if (it.flexBasis !== 'auto') itemLines.push('  <span class="fb-prop">flex-basis</span>: <span class="fb-val">' + it.flexBasis + '</span>;');
      if (it.alignSelf !== 'auto') itemLines.push('  <span class="fb-prop">align-self</span>: <span class="fb-val">' + it.alignSelf + '</span>;');
      if (itemLines.length > 0) {
        lines.push('');
        lines.push('<span class="fb-sel">.item-' + (i+1) + '</span> <span class="fb-brace">{</span>');
        lines = lines.concat(itemLines);
        lines.push('<span class="fb-brace">}</span>');
      }
    }
    codeOut.innerHTML = lines.join('\n');
  }

  function getPlainCSS() {
    var c = state.container;
    var out = '.container {\n  display: flex;\n';
    if (c.flexDirection !== 'row')      out += '  flex-direction: ' + c.flexDirection + ';\n';
    if (c.flexWrap !== 'nowrap')        out += '  flex-wrap: ' + c.flexWrap + ';\n';
    if (c.justifyContent !== 'flex-start') out += '  justify-content: ' + c.justifyContent + ';\n';
    if (c.alignItems !== 'stretch')     out += '  align-items: ' + c.alignItems + ';\n';
    if (c.alignContent !== 'normal')    out += '  align-content: ' + c.alignContent + ';\n';
    if (c.gap > 0)                      out += '  gap: ' + c.gap + 'px;\n';
    out += '}\n';
    for (var i = 0; i < state.itemCount; i++) {
      var it = state.items[i];
      var props = '';
      if (it.order !== 0)          props += '  order: ' + it.order + ';\n';
      if (it.flexGrow !== 0)       props += '  flex-grow: ' + it.flexGrow + ';\n';
      if (it.flexShrink !== 1)     props += '  flex-shrink: ' + it.flexShrink + ';\n';
      if (it.flexBasis !== 'auto') props += '  flex-basis: ' + it.flexBasis + ';\n';
      if (it.alignSelf !== 'auto') props += '  align-self: ' + it.alignSelf + ';\n';
      if (props) out += '\n.item-' + (i+1) + ' {\n' + props + '}\n';
    }
    return out;
  }

  fdEl.addEventListener('change', function() { state.container.flexDirection = this.value.split('（')[0]; renderPreview(); });
  fwEl.addEventListener('change', function() { state.container.flexWrap = this.value.split('（')[0]; renderPreview(); });
  jcEl.addEventListener('change', function() { state.container.justifyContent = this.value.split('（')[0]; renderPreview(); });
  aiEl.addEventListener('change', function() { state.container.alignItems = this.value.split('（')[0]; renderPreview(); });
  acEl.addEventListener('change', function() { state.container.alignContent = this.value; renderPreview(); });
  gapEl.addEventListener('input', function() {
    state.container.gap = parseInt(this.value);
    gapVal.textContent = this.value + 'px';
    renderPreview();
  });

  ordEl.addEventListener('input', function() {
    state.items[state.selectedItem].order = parseInt(this.value);
    ordVal.textContent = this.value;
    renderPreview();
  });
  fgEl.addEventListener('input', function() {
    state.items[state.selectedItem].flexGrow = parseInt(this.value);
    fgVal.textContent = this.value;
    renderPreview();
  });
  fsEl.addEventListener('input', function() {
    state.items[state.selectedItem].flexShrink = parseInt(this.value);
    fsVal.textContent = this.value;
    renderPreview();
  });
  fbEl.addEventListener('change', function() {
    state.items[state.selectedItem].flexBasis = this.value;
    renderPreview();
  });
  asEl.addEventListener('change', function() {
    state.items[state.selectedItem].alignSelf = this.value;
    renderPreview();
  });

  g('fb-add-item').addEventListener('click', function() {
    if (state.itemCount < MAX_ITEMS) {
      state.itemCount++;
      renderTabs();
      renderPreview();
    }
  });
  g('fb-remove-item').addEventListener('click', function() {
    if (state.itemCount > MIN_ITEMS) {
      state.itemCount--;
      if (state.selectedItem >= state.itemCount) {
        state.selectedItem = state.itemCount - 1;
        loadItemControls();
      }
      renderTabs();
      renderPreview();
    }
  });

  copyBtn.addEventListener('click', function() {
    var txt = getPlainCSS();
    if (navigator.clipboard) {
      navigator.clipboard.writeText(txt).then(function() {
        copyBtn.textContent = 'コピー完了!';
        copyBtn.classList.add('copied');
        setTimeout(function() { copyBtn.textContent = 'CSSをコピー'; copyBtn.classList.remove('copied'); }, 1800);
      });
    } else {
      var ta = document.createElement('textarea');
      ta.value = txt;
      ta.style.position = 'fixed'; ta.style.opacity = '0';
      document.body.appendChild(ta);
      ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      copyBtn.textContent = 'コピー完了!';
      copyBtn.classList.add('copied');
      setTimeout(function() { copyBtn.textContent = 'CSSをコピー'; copyBtn.classList.remove('copied'); }, 1800);
    }
  });

  renderTabs();
  loadItemControls();
  renderPreview();

  // Fix: read actual option values (strip Japanese annotations)
  fdEl.addEventListener('change', function() {
    state.container.flexDirection = this.value;
    renderPreview();
  });
  fwEl.addEventListener('change', function() {
    state.container.flexWrap = this.value;
    renderPreview();
  });
  jcEl.addEventListener('change', function() {
    state.container.justifyContent = this.value;
    renderPreview();
  });
  aiEl.addEventListener('change', function() {
    state.container.alignItems = this.value;
    renderPreview();
  });
})();
</script>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

> clip-path作成 → [CSS clip-pathメーカー](/ja/tools/css-clip-path/)

> CSS詳細度 → [CSS詳細度計算](/ja/tools/css-specificity-calculator/)

<div class="fb-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>
