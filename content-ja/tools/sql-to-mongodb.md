---
title: "SQL→MongoDB変換ツール"
date: 2025-05-16
description: "無料のSQL→MongoDB変換ツール。SELECT、INSERT、UPDATE、DELETE文をMongoDBのfind()、insertOne()、updateOne()、deleteOne()構文に即座に変換。"
categories: ["無料ツール"]
slug: "sql-to-mongodb"
ShowToc: false
cover:
  image: "/images/covers/sql-to-mongodb-ja.png"
  alt: "SQL→MongoDB変換ツール"
---

<div id="stm-app">
  <style>
    #stm-app {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Yu Gothic UI", sans-serif;
      max-width: 900px;
      margin: 0 auto;
      color: #e2e8f0;
    }
    #stm-app .stm-layout {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    @media (max-width: 640px) {
      #stm-app .stm-layout { grid-template-columns: 1fr; }
    }
    #stm-app .stm-panel {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    #stm-app .stm-panel-label {
      font-size: 12px;
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: #94a3b8;
    }
    #stm-app textarea {
      width: 100%;
      height: 260px;
      padding: 14px 16px;
      font-size: 13.5px;
      font-family: "Fira Code", "Cascadia Code", "Consolas", "Menlo", monospace;
      line-height: 1.65;
      border: 1.5px solid #334155;
      border-radius: 10px;
      resize: vertical;
      box-sizing: border-box;
      background: #0f172a;
      color: #e2e8f0;
      outline: none;
      transition: border-color 0.2s;
    }
    #stm-app textarea:focus {
      border-color: #38bdf8;
    }
    #stm-app textarea::placeholder {
      color: #475569;
    }
    #stm-app textarea[readonly] {
      background: #0a1120;
      cursor: default;
      color: #7dd3fc;
    }
    #stm-app .stm-btn-row {
      display: flex;
      gap: 10px;
      justify-content: center;
      margin: 6px 0;
      flex-wrap: wrap;
    }
    #stm-app .stm-btn {
      padding: 10px 32px;
      font-size: 14px;
      font-weight: 600;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.15s, transform 0.1s;
    }
    #stm-app .stm-btn:active { transform: scale(0.97); }
    #stm-app .stm-btn-convert {
      background: linear-gradient(135deg, #0ea5e9, #6366f1);
      color: #fff;
    }
    #stm-app .stm-btn-convert:hover { background: linear-gradient(135deg, #38bdf8, #818cf8); }
    #stm-app .stm-btn-copy {
      background: #1e293b;
      color: #94a3b8;
      border: 1.5px solid #334155;
    }
    #stm-app .stm-btn-copy:hover { background: #334155; color: #e2e8f0; }
    #stm-app .stm-btn-clear {
      background: #1e293b;
      color: #94a3b8;
      border: 1.5px solid #334155;
    }
    #stm-app .stm-btn-clear:hover { background: #334155; color: #e2e8f0; }
    #stm-app .stm-error {
      background: #1e0a0a;
      border: 1.5px solid #7f1d1d;
      border-radius: 8px;
      color: #fca5a5;
      font-size: 13px;
      padding: 10px 14px;
      font-family: "Fira Code", monospace;
      display: none;
    }
    #stm-app .stm-examples {
      margin-top: 8px;
      border: 1.5px solid #1e293b;
      border-radius: 10px;
      overflow: hidden;
    }
    #stm-app .stm-examples-title {
      background: #1e293b;
      padding: 8px 14px;
      font-size: 12px;
      font-weight: 600;
      color: #64748b;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }
    #stm-app .stm-example-list {
      display: flex;
      flex-wrap: wrap;
      gap: 0;
    }
    #stm-app .stm-example-btn {
      background: none;
      border: none;
      border-right: 1px solid #1e293b;
      border-bottom: 1px solid #1e293b;
      color: #38bdf8;
      font-size: 12px;
      font-family: "Fira Code", monospace;
      padding: 7px 12px;
      cursor: pointer;
      text-align: left;
      transition: background 0.12s;
    }
    #stm-app .stm-example-btn:hover { background: #0f172a; color: #7dd3fc; }
    #stm-app .stm-copy-toast {
      display: none;
      font-size: 12px;
      color: #4ade80;
      text-align: center;
      margin-top: 4px;
    }
  </style>

  <div class="stm-layout">
    <div class="stm-panel">
      <div class="stm-panel-label">SQL 入力</div>
      <textarea id="stm-sql" placeholder="SELECT * FROM users WHERE age > 25"></textarea>
    </div>
    <div class="stm-panel">
      <div class="stm-panel-label">MongoDB 出力</div>
      <textarea id="stm-mongo" readonly placeholder="変換されたMongoDBクエリがここに表示されます..."></textarea>
    </div>
  </div>

  <div id="stm-error" class="stm-error"></div>
  <div class="stm-copy-toast" id="stm-copy-toast">コピーしました！</div>

  <div class="stm-btn-row">
    <button class="stm-btn stm-btn-convert" id="stm-convert-btn">変換する</button>
    <button class="stm-btn stm-btn-copy" id="stm-copy-btn">出力をコピー</button>
    <button class="stm-btn stm-btn-clear" id="stm-clear-btn">クリア</button>
  </div>

  <div class="stm-examples">
    <div class="stm-examples-title">サンプルSQL</div>
    <div class="stm-example-list">
      <button class="stm-example-btn" data-sql="SELECT * FROM users WHERE age > 25">SELECT * WHERE</button>
      <button class="stm-example-btn" data-sql="SELECT name, age FROM users">フィールド指定</button>
      <button class="stm-example-btn" data-sql="SELECT * FROM orders WHERE status = 'active' AND total > 100">WHERE AND</button>
      <button class="stm-example-btn" data-sql="SELECT * FROM users WHERE name LIKE '%john%'">LIKE</button>
      <button class="stm-example-btn" data-sql="SELECT * FROM products WHERE category IN ('books', 'music')">IN</button>
      <button class="stm-example-btn" data-sql="SELECT * FROM users ORDER BY age DESC LIMIT 10">ORDER + LIMIT</button>
      <button class="stm-example-btn" data-sql="INSERT INTO users (name, age, email) VALUES ('Tanaka', 30, 'tanaka@example.com')">INSERT</button>
      <button class="stm-example-btn" data-sql="UPDATE users SET age = 31, email = 'new@example.com' WHERE name = 'Tanaka'">UPDATE</button>
      <button class="stm-example-btn" data-sql="DELETE FROM users WHERE name = 'Tanaka'">DELETE</button>
    </div>
  </div>

  <script>
  (function() {
    var sqlEl    = document.getElementById('stm-sql');
    var mongoEl  = document.getElementById('stm-mongo');
    var errorEl  = document.getElementById('stm-error');
    var copyToast= document.getElementById('stm-copy-toast');
    var convertBtn = document.getElementById('stm-convert-btn');
    var copyBtn  = document.getElementById('stm-copy-btn');
    var clearBtn = document.getElementById('stm-clear-btn');

    function showError(msg) {
      errorEl.textContent = msg;
      errorEl.style.display = 'block';
      mongoEl.value = '';
    }
    function clearError() {
      errorEl.style.display = 'none';
    }

    function parseValue(v) {
      v = v.trim();
      if (/^'.*'$/.test(v)) return JSON.stringify(v.slice(1, -1));
      if (/^".*"$/.test(v)) return JSON.stringify(v.slice(1, -1));
      if (!isNaN(Number(v))) return v;
      if (v.toUpperCase() === 'NULL') return 'null';
      if (v.toUpperCase() === 'TRUE') return 'true';
      if (v.toUpperCase() === 'FALSE') return 'false';
      return JSON.stringify(v);
    }

    function parseWhere(where) {
      where = where.trim();
      if (!where) return '{}';
      var orParts = splitByKeyword(where, 'OR');
      if (orParts.length > 1) {
        var orClauses = orParts.map(function(p) { return parseAndClause(p.trim()); });
        return '{ $or: [ ' + orClauses.join(', ') + ' ] }';
      }
      return parseAndClause(where);
    }

    function parseAndClause(clause) {
      var parts = splitByKeyword(clause, 'AND');
      if (parts.length === 1) return parseSingleCondition(clause.trim());
      var conditions = parts.map(function(p) { return parseSingleCondition(p.trim()); });
      return '{ $and: [ ' + conditions.join(', ') + ' ] }';
    }

    function splitByKeyword(str, kw) {
      var parts = [];
      var inQuote = false;
      var qChar = '';
      var last = 0;
      for (var i = 0; i < str.length; i++) {
        var c = str[i];
        if (!inQuote && (c === "'" || c === '"')) { inQuote = true; qChar = c; continue; }
        if (inQuote && c === qChar) { inQuote = false; continue; }
        if (!inQuote) {
          var sub = str.slice(i).match(new RegExp('^' + kw + '\\b', 'i'));
          if (sub) {
            parts.push(str.slice(last, i));
            i += sub[0].length;
            last = i;
            i--;
          }
        }
      }
      parts.push(str.slice(last));
      return parts.filter(function(p) { return p.trim().length > 0; });
    }

    function parseSingleCondition(cond) {
      cond = cond.trim();

      var isNullM = cond.match(/^(\w+)\s+IS\s+NOT\s+NULL$/i);
      if (isNullM) return '{ ' + isNullM[1] + ': { $ne: null } }';
      var isNullM2 = cond.match(/^(\w+)\s+IS\s+NULL$/i);
      if (isNullM2) return '{ ' + isNullM2[1] + ': null }';

      var likeM = cond.match(/^(\w+)\s+(?:NOT\s+)?LIKE\s+('([^']*)'|"([^"]*)")/i);
      if (likeM) {
        var likeNot = /NOT\s+LIKE/i.test(cond);
        var pattern = (likeM[3] !== undefined ? likeM[3] : likeM[4]);
        var regexStr = pattern.replace(/%/g, '.*').replace(/_/g, '.');
        var mongoRegex = '/' + regexStr + '/i';
        if (likeNot) return '{ ' + likeM[1] + ': { $not: ' + mongoRegex + ' } }';
        return '{ ' + likeM[1] + ': { $regex: ' + mongoRegex + ' } }';
      }

      var inM = cond.match(/^(\w+)\s+(NOT\s+)?IN\s*\(([^)]+)\)/i);
      if (inM) {
        var inNot = !!inM[2];
        var vals = inM[3].split(',').map(function(v) { return parseValue(v.trim()); });
        if (inNot) return '{ ' + inM[1] + ': { $nin: [ ' + vals.join(', ') + ' ] } }';
        return '{ ' + inM[1] + ': { $in: [ ' + vals.join(', ') + ' ] } }';
      }

      var compM = cond.match(/^(\w+)\s*(!=|<>|<=|>=|<|>|=)\s*(.+)$/i);
      if (compM) {
        var field = compM[1];
        var op    = compM[2];
        var val   = parseValue(compM[3]);
        var opMap = { '=': null, '!=': '$ne', '<>': '$ne', '<': '$lt', '<=': '$lte', '>': '$gt', '>=': '$gte' };
        var mongoOp = opMap[op];
        if (mongoOp === null) return '{ ' + field + ': ' + val + ' }';
        return '{ ' + field + ': { ' + mongoOp + ': ' + val + ' } }';
      }

      return '{ /* 未対応: ' + cond + ' */ }';
    }

    function parseFields(fieldStr) {
      fieldStr = fieldStr.trim();
      if (fieldStr === '*') return null;
      var fields = fieldStr.split(',').map(function(f) { return f.trim().replace(/\s+AS\s+\w+/i, ''); });
      return '{ ' + fields.map(function(f) { return f + ': 1'; }).join(', ') + ' }';
    }

    function parseInsert(cols, vals) {
      var colArr = cols.split(',').map(function(c) { return c.trim(); });
      var valArr = splitValues(vals);
      var pairs = colArr.map(function(c, i) {
        return c + ': ' + parseValue(valArr[i] || 'null');
      });
      return '{ ' + pairs.join(', ') + ' }';
    }

    function splitValues(str) {
      var result = [];
      var cur = '';
      var depth = 0;
      var inQ = false;
      var qC = '';
      for (var i = 0; i < str.length; i++) {
        var c = str[i];
        if (!inQ && (c === "'" || c === '"')) { inQ = true; qC = c; cur += c; continue; }
        if (inQ && c === qC) { inQ = false; cur += c; continue; }
        if (!inQ && c === '(') { depth++; cur += c; continue; }
        if (!inQ && c === ')') { depth--; cur += c; continue; }
        if (!inQ && depth === 0 && c === ',') { result.push(cur.trim()); cur = ''; continue; }
        cur += c;
      }
      if (cur.trim()) result.push(cur.trim());
      return result;
    }

    function parseSet(setStr) {
      var pairs = splitValues(setStr);
      var obj = pairs.map(function(p) {
        var m = p.match(/^(\w+)\s*=\s*(.+)$/);
        if (!m) return '/* ' + p + ' */';
        return m[1] + ': ' + parseValue(m[2]);
      });
      return '{ ' + obj.join(', ') + ' }';
    }

    function convertSQL(sql) {
      sql = sql.trim().replace(/;$/, '').trim();

      var selM = sql.match(/^SELECT\s+([\s\S]+?)\s+FROM\s+(\w+)([\s\S]*)$/i);
      if (selM) {
        var fields   = selM[1].trim();
        var table    = selM[2].trim();
        var rest     = selM[3].trim();
        var whereStr = '';
        var orderStr = '';
        var limitStr = '';

        var limitM = rest.match(/\bLIMIT\s+(\d+)\b/i);
        if (limitM) { limitStr = limitM[1]; rest = rest.replace(limitM[0], '').trim(); }

        var orderM = rest.match(/\bORDER\s+BY\s+([\w\s,]+?)(?=\bLIMIT\b|$)/i);
        if (orderM) {
          var orderRaw = orderM[1].trim();
          rest = rest.replace(orderM[0], '').trim();
          var orderParts = orderRaw.split(',').map(function(o) {
            var om = o.trim().match(/^(\w+)(?:\s+(ASC|DESC))?$/i);
            if (!om) return '';
            var dir = (om[2] && om[2].toUpperCase() === 'DESC') ? -1 : 1;
            return om[1] + ': ' + dir;
          }).filter(Boolean);
          orderStr = '{ ' + orderParts.join(', ') + ' }';
        }

        var whereM = rest.match(/\bWHERE\s+([\s\S]+?)(?=\bORDER\s+BY\b|\bLIMIT\b|\bGROUP\s+BY\b|$)/i);
        if (whereM) whereStr = whereM[1].trim();

        var filter = whereStr ? parseWhere(whereStr) : '{}';
        var proj   = parseFields(fields);

        var query = 'db.' + table + '.find(' + filter;
        if (proj) query += ', ' + proj;
        query += ')';
        if (orderStr) query += '.sort(' + orderStr + ')';
        if (limitStr) query += '.limit(' + limitStr + ')';
        return query;
      }

      var insM = sql.match(/^INSERT\s+INTO\s+(\w+)\s*\(([^)]+)\)\s*VALUES\s*\(([^)]+)\)/i);
      if (insM) {
        var table = insM[1];
        var doc = parseInsert(insM[2], insM[3]);
        return 'db.' + table + '.insertOne(' + doc + ')';
      }

      var updM = sql.match(/^UPDATE\s+(\w+)\s+SET\s+([\s\S]+?)(?:\s+WHERE\s+([\s\S]+))?$/i);
      if (updM) {
        var table  = updM[1];
        var setStr = updM[2].trim();
        var whereStr2 = updM[3] ? updM[3].trim() : '';
        setStr = setStr.replace(/\s+WHERE\s+[\s\S]+$/i, '').trim();
        var filter2 = whereStr2 ? parseWhere(whereStr2) : '{}';
        var update  = '{ $set: ' + parseSet(setStr) + ' }';
        return 'db.' + table + '.updateOne(' + filter2 + ', ' + update + ')';
      }

      var delM = sql.match(/^DELETE\s+FROM\s+(\w+)(?:\s+WHERE\s+([\s\S]+))?$/i);
      if (delM) {
        var table    = delM[1];
        var whereStr3 = delM[2] ? delM[2].trim() : '';
        var filter3  = whereStr3 ? parseWhere(whereStr3) : '{}';
        return 'db.' + table + '.deleteOne(' + filter3 + ')';
      }

      throw new Error('未対応のSQL文です。SELECT、INSERT INTO、UPDATE、DELETE FROMに対応しています。');
    }

    convertBtn.addEventListener('click', function() {
      clearError();
      var sql = sqlEl.value.trim();
      if (!sql) { showError('SQLを入力してください。'); return; }
      try {
        mongoEl.value = convertSQL(sql);
      } catch (e) {
        showError('エラー: ' + e.message);
      }
    });

    sqlEl.addEventListener('keydown', function(e) {
      if ((e.ctrlKey || e.metaKey) && e.key === 'Enter') convertBtn.click();
    });

    copyBtn.addEventListener('click', function() {
      var text = mongoEl.value;
      if (!text) return;
      navigator.clipboard.writeText(text).then(function() {
        copyToast.style.display = 'block';
        setTimeout(function() { copyToast.style.display = 'none'; }, 1800);
      });
    });

    clearBtn.addEventListener('click', function() {
      sqlEl.value = '';
      mongoEl.value = '';
      clearError();
    });

    document.querySelectorAll('#stm-app .stm-example-btn').forEach(function(btn) {
      btn.addEventListener('click', function() {
        sqlEl.value = btn.getAttribute('data-sql');
        clearError();
        convertBtn.click();
      });
    });
  })();
  </script>
</div>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
