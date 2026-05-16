---
title: "Text Diff Checker"
date: 2025-05-16
description: "Free online text diff checker. Compare two texts side by side with color-coded additions, deletions, and changes."
categories: ["Free Tools"]
slug: "diff-checker"
ShowToc: false
cover:
  image: "/images/covers/diff-checker.png"
  alt: "Text Diff Checker"
---

<div id="dc-app">
<style>
#dc-app *,#dc-app *::before,#dc-app *::after{box-sizing:border-box;margin:0;padding:0}
#dc-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;color:#1e293b;max-width:900px;margin:0 auto;padding:16px}
#dc-app h2{font-size:1.1rem;font-weight:600;color:#334155;margin-bottom:10px}
#dc-app .dc-inputs{display:grid;grid-template-columns:1fr 1fr;gap:12px}
@media(max-width:600px){#dc-app .dc-inputs{grid-template-columns:1fr}}
#dc-app .dc-col label{display:block;font-size:13px;font-weight:600;color:#475569;margin-bottom:6px}
#dc-app textarea{width:100%;height:200px;padding:10px 12px;font-size:13px;font-family:monospace;border:1.5px solid #cbd5e1;border-radius:8px;resize:vertical;outline:none;line-height:1.6;background:#f8fafc;transition:border-color .2s}
#dc-app textarea:focus{border-color:#3b82f6;background:#fff}
#dc-app .dc-actions{display:flex;align-items:center;gap:10px;margin:14px 0}
#dc-app button{cursor:pointer;border:none;border-radius:7px;font-size:13px;font-weight:600;padding:9px 20px;transition:opacity .15s}
#dc-app button:hover{opacity:.85}
#dc-app .btn-primary{background:#3b82f6;color:#fff}
#dc-app .btn-secondary{background:#e2e8f0;color:#334155}
#dc-app .btn-copy{background:#10b981;color:#fff}
#dc-app .dc-stats{font-size:12px;color:#64748b;margin-left:auto;display:flex;gap:12px;flex-wrap:wrap}
#dc-app .dc-stats span{background:#f1f5f9;border-radius:5px;padding:4px 10px}
#dc-app .dc-result-wrap{border:1.5px solid #e2e8f0;border-radius:10px;overflow:hidden}
#dc-app .dc-result-header{background:#f8fafc;padding:10px 14px;font-size:12px;font-weight:600;color:#64748b;display:flex;gap:16px;border-bottom:1px solid #e2e8f0}
#dc-app .dc-result{padding:12px 14px;font-size:13px;font-family:monospace;line-height:1.8;white-space:pre-wrap;word-break:break-all;min-height:80px;max-height:420px;overflow-y:auto;background:#fff}
#dc-app .dc-added{background:#dcfce7;color:#166534;border-radius:3px;padding:0 2px}
#dc-app .dc-removed{background:#fee2e2;color:#991b1b;border-radius:3px;padding:0 2px;text-decoration:line-through}
#dc-app .dc-empty{color:#94a3b8;font-style:italic;font-family:sans-serif}
#dc-app .dc-legend{display:flex;gap:14px;font-size:12px;margin-top:10px}
#dc-app .dc-legend span{display:flex;align-items:center;gap:5px}
#dc-app .dc-legend .dot{width:12px;height:12px;border-radius:3px;display:inline-block}
#dc-app .dot-add{background:#dcfce7;border:1px solid #86efac}
#dc-app .dot-rem{background:#fee2e2;border:1px solid #fca5a5}
</style>

<div class="dc-inputs">
  <div class="dc-col">
    <label for="dc-text-a">Original Text</label>
    <textarea id="dc-text-a" placeholder="Paste original text here..."></textarea>
  </div>
  <div class="dc-col">
    <label for="dc-text-b">Modified Text</label>
    <textarea id="dc-text-b" placeholder="Paste modified text here..."></textarea>
  </div>
</div>

<div class="dc-actions">
  <button class="btn-primary" onclick="dcRun()">Compare</button>
  <button class="btn-secondary" onclick="dcSwap()">&#8646; Swap</button>
  <button class="btn-secondary" onclick="dcClear()">Clear</button>
  <div class="dc-stats" id="dc-stats"></div>
</div>

<div class="dc-result-wrap" id="dc-result-wrap" style="display:none">
  <div class="dc-result-header">
    <span>Diff Result</span>
    <span id="dc-result-meta"></span>
    <button class="btn-copy" style="margin-left:auto;padding:4px 14px;font-size:12px" onclick="dcCopy()">Copy</button>
  </div>
  <div class="dc-result" id="dc-result"></div>
</div>

<div class="dc-legend">
  <span><span class="dot dot-add"></span> Added</span>
  <span><span class="dot dot-rem"></span> Removed</span>
</div>

<script>
(function(){
  function lcsTokens(a, b) {
    var m = a.length, n = b.length;
    // Use flat array for DP to save memory
    var dp = new Uint16Array((m+1)*(n+1));
    for (var i = m-1; i >= 0; i--) {
      for (var j = n-1; j >= 0; j--) {
        if (a[i] === b[j]) {
          dp[i*(n+1)+j] = 1 + dp[(i+1)*(n+1)+(j+1)];
        } else {
          var x = dp[(i+1)*(n+1)+j], y = dp[i*(n+1)+(j+1)];
          dp[i*(n+1)+j] = x > y ? x : y;
        }
      }
    }
    // Backtrack
    var ops = [], i = 0, j = 0;
    while (i < m && j < n) {
      if (a[i] === b[j]) { ops.push({t:'=',v:a[i]}); i++; j++; }
      else if (dp[(i+1)*(n+1)+j] >= dp[i*(n+1)+(j+1)]) { ops.push({t:'-',v:a[i]}); i++; }
      else { ops.push({t:'+',v:b[j]}); j++; }
    }
    while (i < m) { ops.push({t:'-',v:a[i]}); i++; }
    while (j < n) { ops.push({t:'+',v:b[j]}); j++; }
    return ops;
  }

  function tokenize(text) {
    // Split into words + whitespace tokens
    return text.match(/\S+|\s+/g) || [];
  }

  window.dcRun = function() {
    var a = document.getElementById('dc-text-a').value;
    var b = document.getElementById('dc-text-b').value;
    var wrap = document.getElementById('dc-result-wrap');
    var out = document.getElementById('dc-result');
    var meta = document.getElementById('dc-result-meta');
    var statsEl = document.getElementById('dc-stats');

    if (!a && !b) {
      wrap.style.display = 'none';
      statsEl.innerHTML = '';
      return;
    }

    var tokA = tokenize(a);
    var tokB = tokenize(b);
    var ops = lcsTokens(tokA, tokB);

    var added = 0, removed = 0;
    var html = '';
    for (var i = 0; i < ops.length; i++) {
      var o = ops[i];
      var esc = o.v.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
      if (o.t === '=') { html += esc; }
      else if (o.t === '+') { html += '<span class="dc-added">'+esc+'</span>'; added++; }
      else { html += '<span class="dc-removed">'+esc+'</span>'; removed++; }
    }

    var linesA = a ? a.split('\n').length : 0;
    var linesB = b ? b.split('\n').length : 0;

    out.innerHTML = html || '<span class="dc-empty">No differences found.</span>';
    wrap.style.display = '';
    meta.textContent = added + ' added · ' + removed + ' removed';
    statsEl.innerHTML =
      '<span>A: ' + linesA + ' lines</span>' +
      '<span>B: ' + linesB + ' lines</span>' +
      '<span>+' + added + ' / -' + removed + '</span>';
  };

  window.dcSwap = function() {
    var a = document.getElementById('dc-text-a');
    var b = document.getElementById('dc-text-b');
    var tmp = a.value; a.value = b.value; b.value = tmp;
  };

  window.dcClear = function() {
    document.getElementById('dc-text-a').value = '';
    document.getElementById('dc-text-b').value = '';
    document.getElementById('dc-result-wrap').style.display = 'none';
    document.getElementById('dc-stats').innerHTML = '';
  };

  window.dcCopy = function() {
    var el = document.getElementById('dc-result');
    var text = el.innerText || el.textContent;
    navigator.clipboard.writeText(text).then(function(){
      var btn = event.target;
      var orig = btn.textContent;
      btn.textContent = 'Copied!';
      setTimeout(function(){ btn.textContent = orig; }, 1500);
    });
  };
})();
</script>

---

**Related tools:**

> Compare JSON → [JSON Diff Checker](/tools/json-diff/)

> Edit Markdown → [Markdown Editor](/tools/markdown-editor/)

</div>
