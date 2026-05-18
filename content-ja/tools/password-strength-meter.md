---
title: "パスワード強度チェッカー"
date: 2025-07-15
description: "無料のパスワード強度診断ツール。エントロピー計算・解読時間推定・詳細フィードバック。すべてブラウザ内で処理、サーバー送信なし。"
categories: ["無料ツール"]
slug: "password-strength-meter"
ShowToc: false
cover:
  image: "/images/covers/password-strength-meter-ja.png"
  alt: "パスワード強度チェッカー"
---

パスワードの安全性をリアルタイムで診断。エントロピー・解読時間・パターン検出・改善提案まで、すべてブラウザ内で処理されます。入力内容はサーバーに一切送信されません。

<div id="pm-app">

<style>
#pm-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, "Segoe UI", sans-serif;
  max-width: 680px;
  margin: 0 auto;
  color: #1e293b;
}
#pm-app * { box-sizing: border-box; }

#pm-app .pm-section {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 24px;
  margin-bottom: 16px;
}

#pm-app h3.pm-section-title {
  margin: 0 0 14px 0;
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: #64748b;
}

/* Input row */
#pm-app .pm-input-wrap {
  position: relative;
  display: flex;
  align-items: center;
}
#pm-app #pm-input-ja {
  width: 100%;
  padding: 13px 46px 13px 14px;
  font-size: 16px;
  font-family: "Courier New", Courier, monospace;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  outline: none;
  color: #0f172a;
  background: #fff;
  transition: border-color 0.15s;
}
#pm-app #pm-input-ja:focus { border-color: #3b82f6; }
#pm-app .pm-toggle-vis {
  position: absolute;
  right: 12px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  color: #64748b;
  font-size: 18px;
  line-height: 1;
  user-select: none;
}
#pm-app .pm-toggle-vis:hover { color: #1e293b; }

/* Strength bar */
#pm-app .pm-bar-wrap {
  margin-top: 14px;
}
#pm-app .pm-bar-track {
  height: 8px;
  background: #e2e8f0;
  border-radius: 99px;
  overflow: hidden;
  margin-bottom: 6px;
}
#pm-app .pm-bar-fill {
  height: 100%;
  border-radius: 99px;
  transition: width 0.3s ease, background 0.3s ease;
  width: 0%;
  background: #e2e8f0;
}
#pm-app .pm-bar-label {
  font-size: 14px;
  font-weight: 700;
  color: #475569;
}

/* Strength levels */
#pm-app .pm-lvl-0 { width: 5%;   background: #ef4444; }
#pm-app .pm-lvl-1 { width: 25%;  background: #f97316; }
#pm-app .pm-lvl-2 { width: 50%;  background: #eab308; }
#pm-app .pm-lvl-3 { width: 75%;  background: #22c55e; }
#pm-app .pm-lvl-4 { width: 100%; background: #16a34a; }

#pm-app .pm-label-0 { color: #ef4444; }
#pm-app .pm-label-1 { color: #f97316; }
#pm-app .pm-label-2 { color: #ca8a04; }
#pm-app .pm-label-3 { color: #16a34a; }
#pm-app .pm-label-4 { color: #15803d; }

/* Stats grid */
#pm-app .pm-stats {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-top: 14px;
}
#pm-app .pm-stat {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  padding: 10px 14px;
}
#pm-app .pm-stat-label {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #94a3b8;
  margin-bottom: 2px;
}
#pm-app .pm-stat-value {
  font-size: 15px;
  font-weight: 700;
  color: #0f172a;
}

/* Checks list */
#pm-app .pm-checks {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
#pm-app .pm-check-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: #475569;
}
#pm-app .pm-check-icon {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 11px;
  flex-shrink: 0;
  font-weight: 700;
}
#pm-app .pm-check-pass .pm-check-icon { background: #dcfce7; color: #16a34a; }
#pm-app .pm-check-fail .pm-check-icon { background: #fee2e2; color: #dc2626; }
#pm-app .pm-check-warn .pm-check-icon { background: #fef9c3; color: #ca8a04; }

/* Suggestions */
#pm-app .pm-suggestions {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 5px;
}
#pm-app .pm-suggestion {
  font-size: 13px;
  color: #475569;
  padding: 6px 10px;
  background: #fff7ed;
  border-left: 3px solid #f97316;
  border-radius: 0 6px 6px 0;
}
#pm-app .pm-no-suggestions {
  font-size: 13px;
  color: #16a34a;
  font-weight: 600;
}

/* Common password warning */
#pm-app .pm-common-warning {
  display: none;
  padding: 10px 14px;
  background: #fef2f2;
  border: 1px solid #fecaca;
  border-radius: 8px;
  font-size: 13px;
  color: #b91c1c;
  font-weight: 600;
  margin-top: 8px;
}

/* Privacy note */
#pm-app .pm-privacy {
  font-size: 11px;
  color: #94a3b8;
  text-align: center;
  margin-top: 4px;
}

@media (max-width: 480px) {
  #pm-app .pm-stats { grid-template-columns: 1fr; }
  #pm-app .pm-section { padding: 16px; }
}
</style>

<!-- 入力 -->
<div class="pm-section">
  <h3 class="pm-section-title">パスワードを入力</h3>
  <div class="pm-input-wrap">
    <input type="password" id="pm-input-ja" autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false" placeholder="パスワードを入力または貼り付け…" oninput="pmjaAnalyze()">
    <button class="pm-toggle-vis" onclick="pmjaToggleVis()" id="pm-vis-btn-ja" title="表示 / 非表示">&#128065;</button>
  </div>
  <div id="pm-common-warning-ja" class="pm-common-warning">&#9888; このパスワードはよく使われるパスワードランキング上位100件に含まれています。使用しないことを強くおすすめします。</div>
  <p class="pm-privacy">&#128274; すべての解析はブラウザ内で完結。入力内容はサーバーに一切送信されません。</p>

  <!-- 強度バー -->
  <div class="pm-bar-wrap">
    <div class="pm-bar-track"><div class="pm-bar-fill" id="pm-bar-ja"></div></div>
    <div class="pm-bar-label" id="pm-bar-label-ja">—</div>
  </div>
</div>

<!-- 分析結果 -->
<div class="pm-section">
  <h3 class="pm-section-title">解析結果</h3>
  <div class="pm-stats">
    <div class="pm-stat">
      <div class="pm-stat-label">文字数</div>
      <div class="pm-stat-value" id="pm-stat-length-ja">—</div>
    </div>
    <div class="pm-stat">
      <div class="pm-stat-label">文字セットサイズ</div>
      <div class="pm-stat-value" id="pm-stat-charset-ja">—</div>
    </div>
    <div class="pm-stat">
      <div class="pm-stat-label">エントロピー</div>
      <div class="pm-stat-value" id="pm-stat-entropy-ja">—</div>
    </div>
    <div class="pm-stat">
      <div class="pm-stat-label">推定解読時間（100億回/秒）</div>
      <div class="pm-stat-value" id="pm-stat-crack-ja">—</div>
    </div>
  </div>
</div>

<!-- チェック項目 -->
<div class="pm-section">
  <h3 class="pm-section-title">チェック項目</h3>
  <ul class="pm-checks" id="pm-checks-list-ja"></ul>
</div>

<!-- 改善提案 -->
<div class="pm-section">
  <h3 class="pm-section-title">改善提案</h3>
  <ul class="pm-suggestions" id="pm-suggestions-list-ja"></ul>
</div>

<script>
(function() {
  'use strict';

  var _visible = false;

  var COMMON_PASSWORDS = [
    '123456','password','123456789','12345678','12345','1234567','1234567890',
    'qwerty','abc123','111111','123123','admin','letmein','welcome','monkey',
    '1234','sunshine','princess','dragon','master','666666','123321','654321',
    'superman','iloveyou','trustno1','password1','password123','batman','shadow',
    'michael','football','baseball','soccer','hockey','liverpool','chelsea',
    'arsenal','andrew','thomas','jordan','harley','ranger','dakota','cookie',
    'cheese','banana','mustang','hunter','purple','thunder','orange','coffee',
    'george','access','hello','letmein','qwerty123','1q2w3e','zxcvbn','asdfgh',
    'qazwsx','1qaz2wsx','password!','pass@123','p@ssword','p@ss123','root',
    'toor','admin123','test','guest','user','login','default','changeme',
    'abc1234','pass1234','qwerty1','123qwe','asdf1234','abcdef','123abc',
    'pass','passw0rd','p4ssword','pa$$word','secret','manager','system',
    'website','online','service','support','security','network','internet',
    'linux','windows','apple','google','amazon','twitter','facebook','instagram'
  ];

  function pmjaToggleVis() {
    _visible = !_visible;
    var inp = document.getElementById('pm-input-ja');
    inp.type = _visible ? 'text' : 'password';
    document.getElementById('pm-vis-btn-ja').innerHTML = _visible ? '&#128584;' : '&#128065;';
  }
  window.pmjaToggleVis = pmjaToggleVis;

  function hasUpper(s)   { return /[A-Z]/.test(s); }
  function hasLower(s)   { return /[a-z]/.test(s); }
  function hasDigit(s)   { return /[0-9]/.test(s); }
  function hasSpecial(s) { return /[^A-Za-z0-9]/.test(s); }
  function hasRepeat(s)  { return /(.)\1{2,}/.test(s); }
  function hasSeq(s) {
    var seqs = ['0123456789','9876543210','abcdefghijklmnopqrstuvwxyz',
                'zyxwvutsrqponmlkjihgfedcba','qwertyuiop','poiuytrewq',
                'asdfghjkl','lkjhgfdsa','zxcvbnm'];
    var sl = s.toLowerCase();
    for (var i = 0; i < seqs.length; i++) {
      for (var j = 0; j <= seqs[i].length - 3; j++) {
        if (sl.indexOf(seqs[i].slice(j, j + 3)) !== -1) return true;
      }
    }
    return false;
  }
  function hasCommonWord(s) {
    var sl = s.toLowerCase();
    var words = ['password','pass','admin','login','user','test','welcome','hello',
                 'abc','qwerty','letmein','monkey','dragon','master','shadow'];
    for (var i = 0; i < words.length; i++) {
      if (sl.indexOf(words[i]) !== -1) return true;
    }
    return false;
  }
  function isCommonPassword(s) {
    return COMMON_PASSWORDS.indexOf(s.toLowerCase()) !== -1;
  }

  function charsetSize(s) {
    var size = 0;
    if (hasLower(s))   size += 26;
    if (hasUpper(s))   size += 26;
    if (hasDigit(s))   size += 10;
    if (hasSpecial(s)) size += 33;
    return size || 26;
  }

  function calcEntropy(s) {
    if (!s.length) return 0;
    var cs = charsetSize(s);
    return Math.round(s.length * Math.log2(cs) * 10) / 10;
  }

  function crackTime(entropy) {
    var guesses = Math.pow(2, entropy) / 2;
    var seconds = guesses / 1e10;
    if (seconds < 1)           return '即座に解読可能';
    if (seconds < 60)          return Math.round(seconds) + '秒';
    if (seconds < 3600)        return Math.round(seconds / 60) + '分';
    if (seconds < 86400)       return Math.round(seconds / 3600) + '時間';
    if (seconds < 2592000)     return Math.round(seconds / 86400) + '日';
    if (seconds < 31536000)    return Math.round(seconds / 2592000) + 'ヶ月';
    if (seconds < 3.154e9)     return Math.round(seconds / 31536000) + '年';
    if (seconds < 3.154e12)    return Math.round(seconds / 3.154e9).toLocaleString() + '千年';
    if (seconds < 3.154e15)    return '数百万年';
    return '数十億年以上';
  }

  function getLevel(entropy, pwd) {
    if (!pwd.length) return -1;
    if (isCommonPassword(pwd)) return 0;
    if (entropy < 28)  return 0;
    if (entropy < 40)  return 1;
    if (entropy < 60)  return 2;
    if (entropy < 80)  return 3;
    return 4;
  }

  var LEVEL_LABELS = ['非常に脆弱','脆弱','普通','強い','非常に強い'];

  function pmjaAnalyze() {
    var pwd = document.getElementById('pm-input-ja').value;
    var entropy = calcEntropy(pwd);
    var cs = pwd.length ? charsetSize(pwd) : 0;
    var level = getLevel(entropy, pwd);
    var isCommon = isCommonPassword(pwd);

    // バー
    var bar = document.getElementById('pm-bar-ja');
    var barLabel = document.getElementById('pm-bar-label-ja');
    bar.className = 'pm-bar-fill';
    if (!pwd.length) {
      bar.style.width = '0%';
      barLabel.textContent = '—';
      barLabel.className = 'pm-bar-label';
    } else {
      bar.classList.add('pm-lvl-' + level);
      barLabel.textContent = LEVEL_LABELS[level];
      barLabel.className = 'pm-bar-label pm-label-' + level;
    }

    // 統計
    document.getElementById('pm-stat-length-ja').textContent  = pwd.length ? pwd.length + '文字' : '—';
    document.getElementById('pm-stat-charset-ja').textContent = cs ? cs + '種類' : '—';
    document.getElementById('pm-stat-entropy-ja').textContent = pwd.length ? entropy + ' bits' : '—';
    document.getElementById('pm-stat-crack-ja').textContent   = pwd.length ? crackTime(entropy) : '—';

    // よく使われるパスワード警告
    document.getElementById('pm-common-warning-ja').style.display = isCommon ? 'block' : 'none';

    // チェック
    var checks = [
      { label: '8文字以上',                     pass: pwd.length >= 8,      warn: false },
      { label: '12文字以上',                    pass: pwd.length >= 12,     warn: false },
      { label: '16文字以上',                    pass: pwd.length >= 16,     warn: false },
      { label: '大文字を含む (A-Z)',             pass: hasUpper(pwd),        warn: false },
      { label: '小文字を含む (a-z)',             pass: hasLower(pwd),        warn: false },
      { label: '数字を含む (0-9)',               pass: hasDigit(pwd),        warn: false },
      { label: '記号を含む (!@#$…)',             pass: hasSpecial(pwd),      warn: false },
      { label: '同じ文字の連続がない (aaa…)',    pass: !hasRepeat(pwd),      warn: true  },
      { label: '連続した並びがない (abc, 123…)', pass: !hasSeq(pwd),         warn: true  },
      { label: '一般的な単語を含まない',          pass: !hasCommonWord(pwd),  warn: true  },
      { label: 'よく使われるパスワードでない',    pass: !isCommon,            warn: true  }
    ];
    var list = document.getElementById('pm-checks-list-ja');
    list.innerHTML = '';
    checks.forEach(function(c) {
      var li = document.createElement('li');
      var cls = c.pass ? 'pm-check-pass' : (c.warn ? 'pm-check-warn' : 'pm-check-fail');
      li.className = 'pm-check-item ' + cls;
      li.innerHTML = '<span class="pm-check-icon">' + (c.pass ? '&#10003;' : (c.warn ? '!' : '&#10007;')) + '</span>' + c.label;
      list.appendChild(li);
    });

    // 改善提案
    var sug = [];
    if (!pwd.length) {
      sug.push('パスワードを入力すると提案が表示されます。');
    } else {
      if (pwd.length < 12)    sug.push('少なくとも12文字以上にしましょう。');
      if (pwd.length < 16)    sug.push('重要なアカウントには16文字以上を推奨します。');
      if (!hasUpper(pwd))     sug.push('大文字（A-Z）を追加しましょう。');
      if (!hasLower(pwd))     sug.push('小文字（a-z）を追加しましょう。');
      if (!hasDigit(pwd))     sug.push('数字（0-9）を追加しましょう。');
      if (!hasSpecial(pwd))   sug.push('記号（例: !@#$%^&*）を追加するとエントロピーが大幅に向上します。');
      if (hasRepeat(pwd))     sug.push('同じ文字を3回以上連続して使用しないようにしましょう。');
      if (hasSeq(pwd))        sug.push('「abc」「123」などの連続した文字列を避けましょう。');
      if (hasCommonWord(pwd)) sug.push('「password」「admin」などの一般的な単語を含まないようにしましょう。');
      if (isCommon)           sug.push('このパスワードはよく使われるリストに含まれています。まったく異なるものを選んでください。');
    }
    var sugList = document.getElementById('pm-suggestions-list-ja');
    sugList.innerHTML = '';
    if (!pwd.length || sug.length === 0) {
      var li = document.createElement('li');
      li.className = 'pm-no-suggestions';
      li.textContent = pwd.length ? '問題ありません！改善提案はありません。' : 'パスワードを入力してください。';
      sugList.appendChild(li);
    } else {
      sug.forEach(function(s) {
        var li = document.createElement('li');
        li.className = 'pm-suggestion';
        li.textContent = s;
        sugList.appendChild(li);
      });
    }
  }
  window.pmjaAnalyze = pmjaAnalyze;

  pmjaAnalyze();
})();
</script>

</div>

<div class="pw-freee-cta" style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">セキュリティ管理に必要な経費も一元管理</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、セキュリティツールのサブスク費用も経費として簡単に記録・管理。無料トライアル実施中。</span>
  <a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

## パスワードの仕組みと安全性

すべての解析はブラウザ内のJavaScriptで完結しています。入力したパスワードはサーバーに送信されません。

**エントロピー**（ビット単位）はパスワードの予測困難さを表します。計算式は `文字数 × log₂(文字セットサイズ)` です。大文字・小文字・数字・記号すべてを含む20文字のパスワードは約131ビットのエントロピーを持ち、現在のコンピュータでは事実上解読不可能です。

**推定解読時間**は毎秒100億回（10B/s）の総当たり攻撃を前提に計算しています。オンライン攻撃はレート制限により実際にはさらに遅くなります。

### 強度レベルの目安

| レベル | エントロピー | 典型的なパスワード例 |
|---|---|---|
| 非常に脆弱 | 28ビット未満 | 短いパスワード・よく使われるパスワード |
| 脆弱 | 28〜39ビット | 辞書にある単語＋小さな変更 |
| 普通 | 40〜59ビット | 複数の文字種・中程度の長さ |
| 強い | 60〜79ビット | 長くて複数の文字種を含む |
| 非常に強い | 80ビット以上 | 全文字種＋16文字以上 |

### 安全なパスワードのヒント

- 一般的なアカウントは16文字以上、重要なアカウントは24文字以上を推奨します。
- 全文字種（大文字・小文字・数字・記号）を使用するとエントロピーが最大になります。
- 実在する単語・名前・日付・キーボードパターンは避けましょう。
- パスワードマネージャーを使って、サイトごとに異なるパスワードを管理しましょう。
- 暗記が必要なパスワードには、パスフレーズ（例: `sakura-tsuki-yama-kaze`）が有効です。

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

---

> 新しいパスワードを生成 → [パスワード生成ツール](/ja/tools/password-generator/)

> ハッシュを生成・検証 → [ハッシュ生成ツール](/ja/tools/hash-generator/)
