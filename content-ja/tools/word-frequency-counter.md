---
title: "単語頻度カウンター"
date: 2025-05-16
description: "無料の単語頻度カウンター。テキストの頻出単語・フレーズ・N-gramを分析。ソート可能な表とワードクラウド表示、CSV書き出し対応。"
categories: ["無料ツール"]
slug: "word-frequency-counter"
ShowToc: false
cover:
  image: "/images/covers/word-frequency-counter-ja.png"
  alt: "単語頻度カウンター"
---

<div id="wf-app">
<style>
#wf-app {
  font-family: "Helvetica Neue", Arial, "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, sans-serif;
  max-width: 820px;
  margin: 0 auto;
  color: #1e293b;
}
#wf-app h2 {
  font-size: 1.15rem;
  font-weight: 700;
  color: #334155;
  margin: 1.5rem 0 0.5rem;
}
#wf-app textarea {
  width: 100%;
  height: 180px;
  padding: 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  line-height: 1.6;
  resize: vertical;
  background: #f8fafc;
  box-sizing: border-box;
  outline: none;
  transition: border-color 0.2s;
  color: #1e293b;
}
#wf-app textarea:focus {
  border-color: #64748b;
  background: #fff;
}
#wf-app .wf-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  align-items: flex-end;
  margin: 14px 0;
}
#wf-app .wf-ctrl-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
  font-size: 13px;
  color: #475569;
}
#wf-app .wf-ctrl-group label {
  font-weight: 600;
  font-size: 12px;
  color: #64748b;
}
#wf-app select,
#wf-app input[type="number"] {
  padding: 7px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 7px;
  font-size: 13px;
  background: #f8fafc;
  color: #1e293b;
  outline: none;
  cursor: pointer;
}
#wf-app select:focus,
#wf-app input[type="number"]:focus {
  border-color: #64748b;
}
#wf-app input[type="number"] {
  width: 72px;
}
#wf-app .wf-checkbox-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
#wf-app .wf-checkbox-group label {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: #475569;
  cursor: pointer;
  font-weight: normal;
}
#wf-app .wf-checkbox-group input[type="checkbox"] {
  width: 15px;
  height: 15px;
  cursor: pointer;
  accent-color: #475569;
}
#wf-app .wf-btn-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 6px;
}
#wf-app button {
  padding: 9px 20px;
  border: none;
  border-radius: 7px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  transition: opacity 0.15s;
}
#wf-app button:hover {
  opacity: 0.85;
}
#wf-app .btn-primary {
  background: #475569;
  color: #fff;
}
#wf-app .btn-secondary {
  background: #e2e8f0;
  color: #334155;
}
#wf-app .btn-export {
  background: #0f766e;
  color: #fff;
}
#wf-app .wf-stats-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  padding: 12px 16px;
  background: #f1f5f9;
  border-radius: 8px;
  margin: 14px 0 10px;
  font-size: 13px;
  color: #475569;
}
#wf-app .wf-stat {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}
#wf-app .wf-stat span:first-child {
  font-size: 11px;
  color: #94a3b8;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
#wf-app .wf-stat span:last-child {
  font-size: 18px;
  font-weight: 700;
  color: #334155;
}
#wf-app .wf-tabs {
  display: flex;
  gap: 0;
  margin: 18px 0 0;
  border-bottom: 2px solid #e2e8f0;
}
#wf-app .wf-tab {
  padding: 8px 18px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  color: #94a3b8;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.15s, border-color 0.15s;
  background: none;
  border-radius: 0;
}
#wf-app .wf-tab.active {
  color: #334155;
  border-bottom-color: #475569;
}
#wf-app .wf-tab-panel {
  display: none;
  margin-top: 14px;
}
#wf-app .wf-tab-panel.active {
  display: block;
}
#wf-app .wf-table-wrap {
  overflow-x: auto;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
}
#wf-app table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}
#wf-app thead th {
  background: #f1f5f9;
  padding: 9px 14px;
  text-align: left;
  font-weight: 700;
  color: #64748b;
  border-bottom: 1px solid #e2e8f0;
  cursor: pointer;
  user-select: none;
  white-space: nowrap;
}
#wf-app thead th:hover {
  background: #e2e8f0;
}
#wf-app thead th.sort-asc::after { content: " ▲"; font-size: 10px; }
#wf-app thead th.sort-desc::after { content: " ▼"; font-size: 10px; }
#wf-app tbody tr:nth-child(even) { background: #f8fafc; }
#wf-app tbody td {
  padding: 8px 14px;
  border-bottom: 1px solid #f1f5f9;
  color: #334155;
}
#wf-app .wf-bar-cell {
  min-width: 100px;
}
#wf-app .wf-bar-bg {
  background: #e2e8f0;
  border-radius: 4px;
  height: 8px;
  overflow: hidden;
}
#wf-app .wf-bar-fill {
  background: #475569;
  height: 8px;
  border-radius: 4px;
  transition: width 0.3s;
}
#wf-app canvas#wf-cloud {
  display: block;
  margin: 0 auto;
  border-radius: 10px;
  border: 1px solid #e2e8f0;
  background: #f8fafc;
  max-width: 100%;
}
#wf-app .wf-empty {
  text-align: center;
  color: #94a3b8;
  font-size: 14px;
  padding: 40px 0;
}
#wf-app .wf-stopwords-toggle {
  font-size: 12px;
  color: #94a3b8;
  cursor: pointer;
  text-decoration: underline;
  background: none;
  border: none;
  padding: 0;
  font-weight: normal;
}
#wf-app .wf-stopwords-area {
  display: none;
  margin-top: 8px;
}
#wf-app .wf-stopwords-area textarea {
  height: 70px;
  font-size: 12px;
}
@media (max-width: 600px) {
  #wf-app .wf-controls { flex-direction: column; }
  #wf-app .wf-stat span:last-child { font-size: 15px; }
  #wf-app .wf-tab { padding: 8px 10px; font-size: 12px; }
}
</style>

<h2>テキストを入力</h2>
<textarea id="wf-input" placeholder="ここにテキストを貼り付けてください…"></textarea>

<div class="wf-controls">
  <div class="wf-ctrl-group">
    <label>分析単位</label>
    <select id="wf-ngram">
      <option value="1">単語（1-gram）</option>
      <option value="2">フレーズ（2-gram）</option>
      <option value="3">3-gram</option>
    </select>
  </div>
  <div class="wf-ctrl-group">
    <label>最小出現回数</label>
    <input type="number" id="wf-mincount" value="1" min="1" max="999">
  </div>
  <div class="wf-ctrl-group">
    <label>表示件数上限</label>
    <input type="number" id="wf-topn" value="100" min="5" max="1000">
  </div>
  <div class="wf-ctrl-group">
    <label>オプション</label>
    <div class="wf-checkbox-group">
      <label><input type="checkbox" id="wf-ignore-case" checked> 大文字・小文字を区別しない</label>
      <label><input type="checkbox" id="wf-ignore-punct" checked> 記号・句読点を除外</label>
      <label><input type="checkbox" id="wf-ignore-nums"> 数字を除外</label>
      <label><input type="checkbox" id="wf-use-stopwords"> ストップワードを除外</label>
    </div>
  </div>
</div>

<div id="wf-stopwords-section" style="display:none;margin-bottom:10px;">
  <button class="wf-stopwords-toggle" id="wf-sw-toggle" onclick="wfToggleStopwords()">ストップワードを編集</button>
  <div class="wf-stopwords-area" id="wf-sw-area">
    <textarea id="wf-stopwords-input" placeholder="除外する単語をスペースまたは改行で区切って入力…">の は が を に で も と や から まで より て で し た だ な の に は が を も と や か</textarea>
  </div>
</div>

<div class="wf-btn-row">
  <button class="btn-primary" onclick="wfAnalyze()">分析する</button>
  <button class="btn-secondary" onclick="wfClear()">クリア</button>
  <button class="btn-export" onclick="wfExportCSV()" id="wf-export-btn" style="display:none;">CSVで書き出す</button>
</div>

<div id="wf-stats" class="wf-stats-bar" style="display:none;">
  <div class="wf-stat"><span>総文字数</span><span id="wf-s-chars">0</span></div>
  <div class="wf-stat"><span>総単語数</span><span id="wf-s-words">0</span></div>
  <div class="wf-stat"><span>ユニーク語</span><span id="wf-s-unique">0</span></div>
  <div class="wf-stat"><span>最頻出語</span><span id="wf-s-top">—</span></div>
</div>

<div id="wf-result" style="display:none;">
  <div class="wf-tabs">
    <button class="wf-tab active" onclick="wfShowTab('table', this)">表</button>
    <button class="wf-tab" onclick="wfShowTab('cloud', this)">ワードクラウド</button>
  </div>

  <div class="wf-tab-panel active" id="wf-panel-table">
    <div class="wf-table-wrap">
      <table id="wf-table">
        <thead>
          <tr>
            <th onclick="wfSort('rank')" id="wf-th-rank">順位</th>
            <th onclick="wfSort('word')" id="wf-th-word">単語 / フレーズ</th>
            <th onclick="wfSort('count')" id="wf-th-count" class="sort-desc">出現回数</th>
            <th onclick="wfSort('pct')" id="wf-th-pct">割合</th>
            <th>頻度バー</th>
          </tr>
        </thead>
        <tbody id="wf-tbody"></tbody>
      </table>
    </div>
  </div>

  <div class="wf-tab-panel" id="wf-panel-cloud">
    <canvas id="wf-cloud" width="780" height="420"></canvas>
  </div>
</div>

<div id="wf-empty" class="wf-empty" style="display:none;">
  一致する単語が見つかりませんでした。テキストを入力して再度お試しください。
</div>

<script>
(function(){
  var _data = [];
  var _sortKey = 'count';
  var _sortDir = -1;
  var _totalTokens = 0;

  // ストップワード表示切替
  window.wfToggleStopwords = function() {
    var area = document.getElementById('wf-sw-area');
    area.style.display = (area.style.display === 'block') ? 'none' : 'block';
  };

  // ストップワードチェックボックス連動
  document.getElementById('wf-use-stopwords').addEventListener('change', function(){
    document.getElementById('wf-stopwords-section').style.display = this.checked ? 'block' : 'none';
  });

  function tokenize(text, n, ignorePunct, ignoreNums, ignoreCase) {
    var t = text;
    if (ignoreCase) t = t.toLowerCase();
    if (ignorePunct) t = t.replace(/[!"#$%&'()*+,\-./:;<=>?@[\\\]^_`{|}~。、「」『』【】〔〕・…―〜！？（）［］｛｝""'']/g, ' ');
    if (ignoreNums) t = t.replace(/[0-9０-９]+/g, ' ');
    // split on whitespace
    var tokens = t.split(/\s+/).filter(function(w){ return w.length > 0; });
    if (n === 1) return tokens;
    var ngrams = [];
    for (var i = 0; i <= tokens.length - n; i++) {
      ngrams.push(tokens.slice(i, i + n).join(' '));
    }
    return ngrams;
  }

  function getStopwords() {
    var raw = document.getElementById('wf-stopwords-input').value;
    return raw.split(/[\s\n]+/).filter(function(w){ return w.length > 0; }).map(function(w){ return w.toLowerCase(); });
  }

  window.wfAnalyze = function() {
    var text = document.getElementById('wf-input').value;
    if (!text.trim()) {
      document.getElementById('wf-result').style.display = 'none';
      document.getElementById('wf-stats').style.display = 'none';
      document.getElementById('wf-export-btn').style.display = 'none';
      document.getElementById('wf-empty').style.display = 'block';
      return;
    }

    var n = parseInt(document.getElementById('wf-ngram').value);
    var minCount = parseInt(document.getElementById('wf-mincount').value) || 1;
    var topN = parseInt(document.getElementById('wf-topn').value) || 100;
    var ignoreCase = document.getElementById('wf-ignore-case').checked;
    var ignorePunct = document.getElementById('wf-ignore-punct').checked;
    var ignoreNums = document.getElementById('wf-ignore-nums').checked;
    var useStopwords = document.getElementById('wf-use-stopwords').checked;
    var stopwords = useStopwords ? getStopwords() : [];

    var tokens = tokenize(text, n, ignorePunct, ignoreNums, ignoreCase);
    _totalTokens = tokens.length;

    // filter stopwords
    if (stopwords.length > 0) {
      tokens = tokens.filter(function(t){
        return stopwords.indexOf(t.toLowerCase()) === -1;
      });
    }

    // count
    var freq = {};
    tokens.forEach(function(t){
      freq[t] = (freq[t] || 0) + 1;
    });

    // build data array
    var arr = Object.keys(freq).map(function(w, i){
      return { word: w, count: freq[w] };
    });

    // filter mincount
    arr = arr.filter(function(d){ return d.count >= minCount; });

    // sort by count desc
    arr.sort(function(a,b){ return b.count - a.count; });

    // top N
    arr = arr.slice(0, topN);

    // add rank & pct
    var maxCount = arr.length > 0 ? arr[0].count : 1;
    arr.forEach(function(d, i){
      d.rank = i + 1;
      d.pct = _totalTokens > 0 ? ((d.count / _totalTokens) * 100).toFixed(2) : '0.00';
      d.barPct = maxCount > 0 ? ((d.count / maxCount) * 100).toFixed(1) : 0;
    });

    _data = arr;
    _sortKey = 'count';
    _sortDir = -1;

    // update stats
    var charCount = text.length;
    var rawTokens = tokenize(text, 1, false, false, false);
    var uniqueCount = Object.keys(freq).length;
    var topWord = arr.length > 0 ? arr[0].word : '—';

    document.getElementById('wf-s-chars').textContent = charCount.toLocaleString();
    document.getElementById('wf-s-words').textContent = rawTokens.length.toLocaleString();
    document.getElementById('wf-s-unique').textContent = uniqueCount.toLocaleString();
    document.getElementById('wf-s-top').textContent = topWord;
    document.getElementById('wf-stats').style.display = 'flex';

    // reset sort headers
    ['rank','word','count','pct'].forEach(function(k){
      var el = document.getElementById('wf-th-'+k);
      if (el) { el.className = (k === 'count') ? 'sort-desc' : ''; }
    });

    if (arr.length === 0) {
      document.getElementById('wf-result').style.display = 'none';
      document.getElementById('wf-export-btn').style.display = 'none';
      document.getElementById('wf-empty').style.display = 'block';
    } else {
      document.getElementById('wf-empty').style.display = 'none';
      document.getElementById('wf-result').style.display = 'block';
      document.getElementById('wf-export-btn').style.display = 'inline-block';
      renderTable();
      renderCloud();
    }
  };

  function renderTable() {
    var tbody = document.getElementById('wf-tbody');
    var rows = _data.map(function(d){
      return '<tr>' +
        '<td>' + d.rank + '</td>' +
        '<td><strong>' + escHtml(d.word) + '</strong></td>' +
        '<td>' + d.count.toLocaleString() + '</td>' +
        '<td>' + d.pct + '%</td>' +
        '<td class="wf-bar-cell"><div class="wf-bar-bg"><div class="wf-bar-fill" style="width:' + d.barPct + '%"></div></div></td>' +
        '</tr>';
    });
    tbody.innerHTML = rows.join('');
  }

  window.wfSort = function(key) {
    if (_sortKey === key) {
      _sortDir *= -1;
    } else {
      _sortKey = key;
      _sortDir = (key === 'word') ? 1 : -1;
    }
    _data.sort(function(a, b){
      if (key === 'word') {
        return _sortDir * a.word.localeCompare(b.word);
      }
      return _sortDir * (a[key] - b[key]);
    });
    // re-rank
    _data.forEach(function(d, i){ d.rank = i + 1; });

    ['rank','word','count','pct'].forEach(function(k){
      var el = document.getElementById('wf-th-'+k);
      if (!el) return;
      el.className = '';
      if (k === _sortKey) {
        el.className = _sortDir > 0 ? 'sort-asc' : 'sort-desc';
      }
    });
    renderTable();
  };

  window.wfShowTab = function(tab, btn) {
    document.querySelectorAll('#wf-app .wf-tab').forEach(function(b){ b.classList.remove('active'); });
    document.querySelectorAll('#wf-app .wf-tab-panel').forEach(function(p){ p.classList.remove('active'); });
    btn.classList.add('active');
    document.getElementById('wf-panel-' + tab).classList.add('active');
    if (tab === 'cloud') renderCloud();
  };

  function renderCloud() {
    var canvas = document.getElementById('wf-cloud');
    var ctx = canvas.getContext('2d');
    var W = canvas.width;
    var H = canvas.height;
    ctx.clearRect(0, 0, W, H);
    ctx.fillStyle = '#f8fafc';
    ctx.fillRect(0, 0, W, H);

    if (_data.length === 0) return;

    var maxCount = _data[0].count;
    var slice = _data.slice(0, 80);
    var colors = ['#334155','#475569','#64748b','#7c3aed','#0f766e','#b45309','#be185d','#1d4ed8','#065f46','#92400e'];

    // Simple placement: try random, skip on collision
    var placed = [];
    var minFont = 11, maxFont = 64;

    function getFontSize(count) {
      return Math.round(minFont + (maxFont - minFont) * Math.pow(count / maxCount, 0.5));
    }

    function overlaps(x, y, w, h) {
      for (var i = 0; i < placed.length; i++) {
        var p = placed[i];
        if (x < p.x + p.w + 4 && x + w + 4 > p.x &&
            y < p.y + p.h + 4 && y + h + 4 > p.y) return true;
      }
      return false;
    }

    var cx = W / 2, cy = H / 2;
    var attempts = 120;

    slice.forEach(function(d, idx) {
      var fs = getFontSize(d.count);
      ctx.font = 'bold ' + fs + 'px "Helvetica Neue", Arial, sans-serif';
      var tw = ctx.measureText(d.word).width;
      var th = fs;
      var color = colors[idx % colors.length];
      var placed_flag = false;

      for (var a = 0; a < attempts; a++) {
        var angle = a * 2.399963; // golden angle
        var r = 6 * Math.sqrt(a);
        var px = cx + r * Math.cos(angle) - tw / 2;
        var py = cy + r * Math.sin(angle) - th / 2;

        if (px < 4 || py < 4 || px + tw > W - 4 || py + th > H - 4) continue;
        if (!overlaps(px, py, tw, th)) {
          ctx.fillStyle = color;
          ctx.fillText(d.word, px, py + th);
          placed.push({ x: px, y: py, w: tw, h: th });
          placed_flag = true;
          break;
        }
      }
    });
  }

  window.wfClear = function() {
    document.getElementById('wf-input').value = '';
    document.getElementById('wf-result').style.display = 'none';
    document.getElementById('wf-stats').style.display = 'none';
    document.getElementById('wf-export-btn').style.display = 'none';
    document.getElementById('wf-empty').style.display = 'none';
    _data = [];
  };

  window.wfExportCSV = function() {
    if (_data.length === 0) return;
    var rows = [['順位', '単語/フレーズ', '出現回数', '割合(%)']];
    _data.forEach(function(d){
      rows.push([d.rank, d.word, d.count, d.pct]);
    });
    var csv = rows.map(function(r){
      return r.map(function(cell){
        var s = String(cell);
        if (s.indexOf(',') > -1 || s.indexOf('"') > -1 || s.indexOf('\n') > -1) {
          s = '"' + s.replace(/"/g, '""') + '"';
        }
        return s;
      }).join(',');
    }).join('\n');

    var bom = '\uFEFF';
    var blob = new Blob([bom + csv], { type: 'text/csv;charset=utf-8;' });
    var url = URL.createObjectURL(blob);
    var a = document.createElement('a');
    a.href = url;
    a.download = 'word-frequency.csv';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
  };

  function escHtml(s) {
    return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
  }
})();
</script>
</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

---

> テキストを変換 → [テキスト変換ツール](/ja/tools/text-case-converter/)
> コード行数をカウント → [行数カウンター](/ja/tools/line-counter/)
> テキストの差分を確認 → [テキスト差分比較ツール](/ja/tools/text-diff-checker/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
