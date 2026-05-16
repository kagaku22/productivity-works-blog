---
title: "関数電卓"
description: "無料のオンライン関数電卓。三角関数・対数・指数・階乗・定数（π, e）・メモリ機能対応。PC・スマートフォンで使えます。会員登録不要。"
slug: scientific-calculator
date: 2025-05-16
categories: ["無料ツール"]
ShowToc: false
cover:
  image: /images/covers/scientific-calculator-ja.png
  alt: "関数電卓"
---

<div id="sc-app">

<style>
#sc-app * { box-sizing: border-box; margin: 0; padding: 0; }
#sc-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 420px;
  margin: 0 auto;
  padding: 16px;
}
#sc-app .sc-calc-wrap {
  background: #1a1a2e;
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.3);
}
#sc-app .sc-display {
  background: #0f0f1a;
  border-radius: 10px;
  padding: 14px 16px;
  margin-bottom: 14px;
  min-height: 80px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-end;
  gap: 4px;
}
#sc-app .sc-expr {
  font-size: 13px;
  color: #8888aa;
  min-height: 18px;
  word-break: break-all;
  text-align: right;
  max-width: 100%;
  overflow-x: auto;
  white-space: nowrap;
}
#sc-app .sc-result {
  font-size: 28px;
  color: #e8e8ff;
  font-weight: 300;
  word-break: break-all;
  text-align: right;
  max-width: 100%;
  overflow-x: auto;
  white-space: nowrap;
}
#sc-app .sc-mode-row {
  display: flex;
  gap: 8px;
  margin-bottom: 12px;
  justify-content: flex-end;
}
#sc-app .sc-mode-btn {
  padding: 4px 12px;
  border-radius: 20px;
  border: 1.5px solid #4444aa;
  background: transparent;
  color: #8888cc;
  font-size: 12px;
  cursor: pointer;
  transition: all 0.15s;
}
#sc-app .sc-mode-btn.active {
  background: #4444aa;
  color: #fff;
}
#sc-app .sc-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 8px;
}
#sc-app .sc-btn {
  padding: 0;
  height: 46px;
  border-radius: 8px;
  border: none;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.1s;
  display: flex;
  align-items: center;
  justify-content: center;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}
#sc-app .sc-btn:active { transform: scale(0.93); }
#sc-app .sc-btn.num { background: #2a2a4a; color: #ddeeff; }
#sc-app .sc-btn.num:hover { background: #33336a; }
#sc-app .sc-btn.op { background: #1e3a5f; color: #7ec8e3; }
#sc-app .sc-btn.op:hover { background: #254e80; }
#sc-app .sc-btn.fn { background: #1a2a3a; color: #aaccee; font-size: 12px; }
#sc-app .sc-btn.fn:hover { background: #22384a; }
#sc-app .sc-btn.eq { background: #0066cc; color: #fff; font-size: 18px; }
#sc-app .sc-btn.eq:hover { background: #0077ee; }
#sc-app .sc-btn.ac { background: #c0392b; color: #fff; }
#sc-app .sc-btn.ac:hover { background: #e74c3c; }
#sc-app .sc-btn.cl { background: #7f3c3c; color: #ffcccc; }
#sc-app .sc-btn.cl:hover { background: #a04040; }
#sc-app .sc-btn.mem { background: #1a3a2a; color: #88ddaa; font-size: 12px; }
#sc-app .sc-btn.mem:hover { background: #224a36; }
#sc-app .sc-btn.const { background: #2a1a3a; color: #cc88ff; }
#sc-app .sc-btn.const:hover { background: #3a2a50; }
#sc-app .sc-history {
  margin-top: 20px;
  background: #0f0f1a;
  border-radius: 10px;
  padding: 12px 14px;
}
#sc-app .sc-history h3 {
  font-size: 13px;
  color: #6666aa;
  margin-bottom: 8px;
  font-weight: 500;
  letter-spacing: 0.04em;
}
#sc-app .sc-history-list {
  list-style: none;
  max-height: 180px;
  overflow-y: auto;
}
#sc-app .sc-history-list li {
  font-size: 13px;
  color: #8888bb;
  padding: 4px 0;
  border-bottom: 1px solid #1e1e30;
  display: flex;
  justify-content: space-between;
  gap: 8px;
  cursor: pointer;
  transition: color 0.1s;
}
#sc-app .sc-history-list li:last-child { border-bottom: none; }
#sc-app .sc-history-list li:hover { color: #ccccff; }
#sc-app .sc-history-list .hi-expr { color: #555588; }
#sc-app .sc-history-list .hi-val { color: #aaaadd; font-weight: 600; }
#sc-app .sc-crosslinks {
  margin-top: 20px;
  font-size: 13px;
  color: #6c757d;
  line-height: 1.7;
}
#sc-app .sc-crosslinks a { color: #0066cc; text-decoration: none; }
#sc-app .sc-crosslinks a:hover { text-decoration: underline; }
@media (max-width: 480px) {
  #sc-app .sc-btn { height: 42px; font-size: 13px; }
  #sc-app .sc-btn.fn { font-size: 11px; }
  #sc-app .sc-result { font-size: 22px; }
}
</style>

<div class="sc-calc-wrap">
  <div class="sc-display">
    <div class="sc-expr" id="sc-expr"></div>
    <div class="sc-result" id="sc-result">0</div>
  </div>
  <div class="sc-mode-row">
    <button class="sc-mode-btn active" id="sc-deg-btn" onclick="scSetMode('deg')">DEG</button>
    <button class="sc-mode-btn" id="sc-rad-btn" onclick="scSetMode('rad')">RAD</button>
  </div>
  <div class="sc-grid">
    <!-- Row 1: Memory -->
    <button class="sc-btn mem" onclick="scMem('mc')">MC</button>
    <button class="sc-btn mem" onclick="scMem('mr')">MR</button>
    <button class="sc-btn mem" onclick="scMem('mp')">M+</button>
    <button class="sc-btn mem" onclick="scMem('mm')">M−</button>
    <button class="sc-btn cl" onclick="scBack()">⌫</button>
    <!-- Row 2: Scientific -->
    <button class="sc-btn fn" onclick="scFn('sin')">sin</button>
    <button class="sc-btn fn" onclick="scFn('cos')">cos</button>
    <button class="sc-btn fn" onclick="scFn('tan')">tan</button>
    <button class="sc-btn fn" onclick="scFn('log')">log</button>
    <button class="sc-btn fn" onclick="scFn('ln')">ln</button>
    <!-- Row 3: Scientific -->
    <button class="sc-btn fn" onclick="scFn('asin')">asin</button>
    <button class="sc-btn fn" onclick="scFn('acos')">acos</button>
    <button class="sc-btn fn" onclick="scFn('atan')">atan</button>
    <button class="sc-btn fn" onclick="scFn('sqrt')">√</button>
    <button class="sc-btn fn" onclick="scFn('cbrt')">∛</button>
    <!-- Row 4: Power / special -->
    <button class="sc-btn fn" onclick="scFn('sq')">x²</button>
    <button class="sc-btn fn" onclick="scFn('cb')">x³</button>
    <button class="sc-btn fn" onclick="scFn('pow')">xʸ</button>
    <button class="sc-btn fn" onclick="scFn('inv')">1/x</button>
    <button class="sc-btn fn" onclick="scFn('exp')">eˣ</button>
    <!-- Row 5: Constants / factorial / parens -->
    <button class="sc-btn const" onclick="scConst('pi')">π</button>
    <button class="sc-btn const" onclick="scConst('e')">e</button>
    <button class="sc-btn fn" onclick="scFn('fact')">n!</button>
    <button class="sc-btn op" onclick="scOp('(')">(</button>
    <button class="sc-btn op" onclick="scOp(')')">)</button>
    <!-- Row 6: Numbers + ops -->
    <button class="sc-btn num" onclick="scNum('7')">7</button>
    <button class="sc-btn num" onclick="scNum('8')">8</button>
    <button class="sc-btn num" onclick="scNum('9')">9</button>
    <button class="sc-btn op" onclick="scOp('÷')">÷</button>
    <button class="sc-btn ac" onclick="scAC()">AC</button>
    <!-- Row 7 -->
    <button class="sc-btn num" onclick="scNum('4')">4</button>
    <button class="sc-btn num" onclick="scNum('5')">5</button>
    <button class="sc-btn num" onclick="scNum('6')">6</button>
    <button class="sc-btn op" onclick="scOp('×')">×</button>
    <button class="sc-btn op" onclick="scOp('%')">%</button>
    <!-- Row 8 -->
    <button class="sc-btn num" onclick="scNum('1')">1</button>
    <button class="sc-btn num" onclick="scNum('2')">2</button>
    <button class="sc-btn num" onclick="scNum('3')">3</button>
    <button class="sc-btn op" onclick="scOp('−')">−</button>
    <button class="sc-btn eq" onclick="scEq()" style="grid-row: span 2;">=</button>
    <!-- Row 9 -->
    <button class="sc-btn num" onclick="scNum('0')" style="grid-column: span 2;">0</button>
    <button class="sc-btn num" onclick="scNum('.')">.</button>
    <button class="sc-btn op" onclick="scOp('+')">+</button>
  </div>
</div>

<div class="sc-history">
  <h3>履歴（最新10件）</h3>
  <ul class="sc-history-list" id="sc-history-list">
    <li style="color:#444466;font-style:italic;">まだ計算がありません。</li>
  </ul>
</div>

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">経理計算もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、複雑な経理計算・確定申告もクラウドで自動化。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

<div class="sc-crosslinks">
  パーセント計算 → <a href="/ja/tools/percentage-calculator/">パーセント計算ツール</a><br>
  単位変換 → <a href="/ja/tools/unit-converter/">単位変換ツール</a>
</div>

</div>

<script>
(function() {
  'use strict';

  var SC = {
    expr: '',
    pendingFn: null,
    memory: 0,
    history: [],
    angleMode: 'deg',
    justEvaled: false,
    lastResult: '0'
  };

  function display() {
    document.getElementById('sc-expr').textContent = SC.expr;
    document.getElementById('sc-result').textContent = SC.lastResult;
  }

  function toRad(x) {
    return SC.angleMode === 'deg' ? x * Math.PI / 180 : x;
  }

  function fromRad(x) {
    return SC.angleMode === 'deg' ? x * 180 / Math.PI : x;
  }

  function fmtNum(n) {
    if (!isFinite(n)) return n.toString();
    var s = parseFloat(n.toPrecision(12)).toString();
    return s;
  }

  window.scSetMode = function(mode) {
    SC.angleMode = mode;
    document.getElementById('sc-deg-btn').classList.toggle('active', mode === 'deg');
    document.getElementById('sc-rad-btn').classList.toggle('active', mode === 'rad');
  };

  window.scNum = function(n) {
    if (SC.justEvaled && n !== '.') {
      SC.expr = '';
      SC.justEvaled = false;
    }
    SC.expr += n;
    SC.lastResult = SC.expr;
    display();
  };

  window.scOp = function(op) {
    SC.justEvaled = false;
    SC.expr += op;
    SC.lastResult = SC.expr;
    display();
  };

  window.scConst = function(c) {
    if (SC.justEvaled) { SC.expr = ''; SC.justEvaled = false; }
    if (c === 'pi') SC.expr += 'π';
    else SC.expr += 'e';
    SC.lastResult = fmtNum(c === 'pi' ? Math.PI : Math.E);
    display();
  };

  window.scFn = function(fn) {
    if (SC.justEvaled) { SC.justEvaled = false; }
    var cur = SC.expr;
    if (fn === 'sq') {
      SC.expr = '(' + (cur || '0') + ')^2';
      try { SC.lastResult = fmtNum(Math.pow(evalExprSC(cur || '0'), 2)); } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'cb') {
      SC.expr = '(' + (cur || '0') + ')^3';
      try { SC.lastResult = fmtNum(Math.pow(evalExprSC(cur || '0'), 3)); } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'pow') {
      SC.expr = (cur || '0') + '^';
      SC.lastResult = SC.expr;
    } else if (fn === 'inv') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(1 / v);
        SC.expr = '1/(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'fact') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(scFactorial(Math.round(v)));
        SC.expr = cur + '!';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'exp') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.exp(v));
        SC.expr = 'e^(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'sqrt') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.sqrt(v));
        SC.expr = '√(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'cbrt') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.cbrt(v));
        SC.expr = '∛(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'log') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.log10(v));
        SC.expr = 'log(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'ln') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.log(v));
        SC.expr = 'ln(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'sin') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.sin(toRad(v)));
        SC.expr = 'sin(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'cos') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.cos(toRad(v)));
        SC.expr = 'cos(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'tan') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(Math.tan(toRad(v)));
        SC.expr = 'tan(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'asin') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(fromRad(Math.asin(v)));
        SC.expr = 'asin(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'acos') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(fromRad(Math.acos(v)));
        SC.expr = 'acos(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    } else if (fn === 'atan') {
      try {
        var v = evalExprSC(cur || '0');
        SC.lastResult = fmtNum(fromRad(Math.atan(v)));
        SC.expr = 'atan(' + cur + ')';
      } catch(e) { SC.lastResult = 'エラー'; }
    }
    display();
  };

  function evalExprSC(raw) {
    var s = raw
      .replace(/\^/g, '**')
      .replace(/×/g, '*')
      .replace(/÷/g, '/')
      .replace(/−/g, '-')
      .replace(/π/g, '(' + Math.PI + ')')
      .replace(/e(?!\^)/g, '(' + Math.E + ')');
    return Function('"use strict"; return (' + s + ')')();
  }

  function scFactorial(n) {
    if (n < 0) return NaN;
    if (n > 170) return Infinity;
    var r = 1;
    for (var i = 2; i <= n; i++) r *= i;
    return r;
  }

  window.scEq = function() {
    if (!SC.expr) return;
    var raw = SC.expr;
    try {
      var result = evalExprSC(raw);
      var res = fmtNum(result);
      addHistory(raw, res);
      SC.expr = res;
      SC.lastResult = res;
      SC.justEvaled = true;
    } catch(e) {
      SC.lastResult = 'エラー';
    }
    display();
  };

  function addHistory(expr, val) {
    SC.history.unshift({ expr: expr, val: val });
    if (SC.history.length > 10) SC.history.pop();
    renderHistory();
  }

  function renderHistory() {
    var ul = document.getElementById('sc-history-list');
    if (!SC.history.length) {
      ul.innerHTML = '<li style="color:#444466;font-style:italic;">まだ計算がありません。</li>';
      return;
    }
    ul.innerHTML = SC.history.map(function(h) {
      return '<li onclick="scUseHistory(\'' + h.val.replace(/'/g, "\\'") + '\')">' +
        '<span class="hi-expr">' + escHtml(h.expr) + '</span>' +
        '<span class="hi-val">' + escHtml(h.val) + '</span>' +
        '</li>';
    }).join('');
  }

  function escHtml(s) {
    return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
  }

  window.scUseHistory = function(val) {
    SC.expr = val;
    SC.lastResult = val;
    SC.justEvaled = false;
    display();
  };

  window.scAC = function() {
    SC.expr = '';
    SC.lastResult = '0';
    SC.justEvaled = false;
    display();
  };

  window.scBack = function() {
    if (SC.justEvaled) { scAC(); return; }
    SC.expr = SC.expr.slice(0, -1);
    SC.lastResult = SC.expr || '0';
    display();
  };

  window.scMem = function(op) {
    if (op === 'mc') {
      SC.memory = 0;
    } else if (op === 'mr') {
      SC.expr = String(SC.memory);
      SC.lastResult = String(SC.memory);
      SC.justEvaled = false;
      display();
      return;
    } else if (op === 'mp') {
      try { SC.memory += parseFloat(SC.lastResult) || 0; } catch(e) {}
    } else if (op === 'mm') {
      try { SC.memory -= parseFloat(SC.lastResult) || 0; } catch(e) {}
    }
  };

  document.addEventListener('keydown', function(e) {
    var k = e.key;
    if (k >= '0' && k <= '9') scNum(k);
    else if (k === '.') scNum('.');
    else if (k === '+') scOp('+');
    else if (k === '-') scOp('−');
    else if (k === '*') scOp('×');
    else if (k === '/') { e.preventDefault(); scOp('÷'); }
    else if (k === '(') scOp('(');
    else if (k === ')') scOp(')');
    else if (k === '%') scOp('%');
    else if (k === 'Enter' || k === '=') scEq();
    else if (k === 'Backspace') scBack();
    else if (k === 'Escape') scAC();
  });

})();
</script>

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

</div>
