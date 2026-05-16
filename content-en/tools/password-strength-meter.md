---
title: "Password Strength Meter"
date: 2025-05-16
description: "Free password strength checker. Analyze password security with entropy calculation, crack time estimate, and detailed feedback. All processing done locally in your browser."
categories: ["Free Tools"]
slug: "password-strength-meter"
ShowToc: false
cover:
  image: "/images/covers/password-strength-meter.png"
  alt: "Password Strength Meter"
---

Check how strong your password really is — entropy, estimated crack time, pattern detection, and improvement suggestions. All analysis runs locally in your browser; nothing is ever transmitted.

<div id="pm-app">

<style>
#pm-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
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
#pm-app #pm-input {
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
#pm-app #pm-input:focus { border-color: #3b82f6; }
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
#pm-app .pm-lvl-0 { width: 5%;  background: #ef4444; }
#pm-app .pm-lvl-1 { width: 25%; background: #f97316; }
#pm-app .pm-lvl-2 { width: 50%; background: #eab308; }
#pm-app .pm-lvl-3 { width: 75%; background: #22c55e; }
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

<!-- Input -->
<div class="pm-section">
  <h3 class="pm-section-title">Enter Password</h3>
  <div class="pm-input-wrap">
    <input type="password" id="pm-input" autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false" placeholder="Type or paste a password…" oninput="pmAnalyze()">
    <button class="pm-toggle-vis" onclick="pmToggleVis()" id="pm-vis-btn" title="Show / Hide">&#128065;</button>
  </div>
  <div id="pm-common-warning" class="pm-common-warning">&#9888; This is one of the most commonly used passwords — avoid it!</div>
  <p class="pm-privacy">&#128274; All analysis is done locally. Your password never leaves your device.</p>

  <!-- Strength bar -->
  <div class="pm-bar-wrap">
    <div class="pm-bar-track"><div class="pm-bar-fill" id="pm-bar"></div></div>
    <div class="pm-bar-label" id="pm-bar-label">—</div>
  </div>
</div>

<!-- Stats -->
<div class="pm-section">
  <h3 class="pm-section-title">Analysis</h3>
  <div class="pm-stats">
    <div class="pm-stat">
      <div class="pm-stat-label">Length</div>
      <div class="pm-stat-value" id="pm-stat-length">—</div>
    </div>
    <div class="pm-stat">
      <div class="pm-stat-label">Charset Size</div>
      <div class="pm-stat-value" id="pm-stat-charset">—</div>
    </div>
    <div class="pm-stat">
      <div class="pm-stat-label">Entropy</div>
      <div class="pm-stat-value" id="pm-stat-entropy">—</div>
    </div>
    <div class="pm-stat">
      <div class="pm-stat-label">Crack Time (10B/s)</div>
      <div class="pm-stat-value" id="pm-stat-crack">—</div>
    </div>
  </div>
</div>

<!-- Checks -->
<div class="pm-section">
  <h3 class="pm-section-title">Checks</h3>
  <ul class="pm-checks" id="pm-checks-list"></ul>
</div>

<!-- Suggestions -->
<div class="pm-section">
  <h3 class="pm-section-title">Suggestions</h3>
  <ul class="pm-suggestions" id="pm-suggestions-list"></ul>
</div>

<script>
(function() {
  'use strict';

  var _visible = false;

  // Top-100 common passwords
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

  function pmToggleVis() {
    _visible = !_visible;
    var inp = document.getElementById('pm-input');
    inp.type = _visible ? 'text' : 'password';
    document.getElementById('pm-vis-btn').innerHTML = _visible ? '&#128584;' : '&#128065;';
  }
  window.pmToggleVis = pmToggleVis;

  function hasUpper(s)   { return /[A-Z]/.test(s); }
  function hasLower(s)   { return /[a-z]/.test(s); }
  function hasDigit(s)   { return /[0-9]/.test(s); }
  function hasSpecial(s) { return /[^A-Za-z0-9]/.test(s); }
  function hasRepeat(s)  { return /(.)\1{2,}/.test(s); }
  function hasSeq(s){
    var seqs = ['0123456789','9876543210','abcdefghijklmnopqrstuvwxyz',
                'zyxwvutsrqponmlkjihgfedcba','qwertyuiop','poiuytrewq',
                'asdfghjkl','lkjhgfdsa','zxcvbnm'];
    var sl = s.toLowerCase();
    for (var i = 0; i < seqs.length; i++) {
      for (var j = 0; j <= seqs[i].length - 3; j++) {
        if (sl.indexOf(seqs[i].slice(j, j+3)) !== -1) return true;
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
    // 10 billion guesses per second
    var guesses = Math.pow(2, entropy) / 2;
    var seconds = guesses / 1e10;
    if (seconds < 1)          return 'Instant';
    if (seconds < 60)         return Math.round(seconds) + ' seconds';
    if (seconds < 3600)       return Math.round(seconds/60) + ' minutes';
    if (seconds < 86400)      return Math.round(seconds/3600) + ' hours';
    if (seconds < 2592000)    return Math.round(seconds/86400) + ' days';
    if (seconds < 31536000)   return Math.round(seconds/2592000) + ' months';
    if (seconds < 3.154e9)    return Math.round(seconds/31536000) + ' years';
    if (seconds < 3.154e12)   return Math.round(seconds/3.154e9).toLocaleString() + ' thousand years';
    if (seconds < 3.154e15)   return 'Millions of years';
    return 'Billions of years';
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

  var LEVEL_LABELS = ['Very Weak','Weak','Fair','Strong','Very Strong'];

  function pmAnalyze() {
    var pwd = document.getElementById('pm-input').value;
    var entropy = calcEntropy(pwd);
    var cs = pwd.length ? charsetSize(pwd) : 0;
    var level = getLevel(entropy, pwd);
    var isCommon = isCommonPassword(pwd);

    // Bar
    var bar = document.getElementById('pm-bar');
    var barLabel = document.getElementById('pm-bar-label');
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

    // Stats
    document.getElementById('pm-stat-length').textContent  = pwd.length ? pwd.length + ' chars' : '—';
    document.getElementById('pm-stat-charset').textContent = cs ? cs + ' chars' : '—';
    document.getElementById('pm-stat-entropy').textContent = pwd.length ? entropy + ' bits' : '—';
    document.getElementById('pm-stat-crack').textContent   = pwd.length ? crackTime(entropy) : '—';

    // Common password warning
    document.getElementById('pm-common-warning').style.display = isCommon ? 'block' : 'none';

    // Checks
    var checks = [
      { label: 'At least 8 characters',    pass: pwd.length >= 8,  warn: false },
      { label: 'At least 12 characters',   pass: pwd.length >= 12, warn: false },
      { label: 'At least 16 characters',   pass: pwd.length >= 16, warn: false },
      { label: 'Contains uppercase (A-Z)', pass: hasUpper(pwd),    warn: false },
      { label: 'Contains lowercase (a-z)', pass: hasLower(pwd),    warn: false },
      { label: 'Contains digits (0-9)',    pass: hasDigit(pwd),    warn: false },
      { label: 'Contains special characters', pass: hasSpecial(pwd), warn: false },
      { label: 'No repeated characters (aaa…)', pass: !hasRepeat(pwd), warn: true },
      { label: 'No sequential patterns (abc, 123…)', pass: !hasSeq(pwd), warn: true },
      { label: 'No common words (password, admin…)', pass: !hasCommonWord(pwd), warn: true },
      { label: 'Not a top-100 common password', pass: !isCommon, warn: true }
    ];
    var list = document.getElementById('pm-checks-list');
    list.innerHTML = '';
    checks.forEach(function(c) {
      var li = document.createElement('li');
      var cls = c.pass ? 'pm-check-pass' : (c.warn ? 'pm-check-warn' : 'pm-check-fail');
      li.className = 'pm-check-item ' + cls;
      li.innerHTML = '<span class="pm-check-icon">' + (c.pass ? '&#10003;' : (c.warn ? '!' : '&#10007;')) + '</span>' + c.label;
      list.appendChild(li);
    });

    // Suggestions
    var sug = [];
    if (!pwd.length) {
      sug.push('Enter a password above to see suggestions.');
    } else {
      if (pwd.length < 12)    sug.push('Increase length to at least 12 characters.');
      if (pwd.length < 16)    sug.push('Aim for 16+ characters for maximum security.');
      if (!hasUpper(pwd))     sug.push('Add uppercase letters (A-Z).');
      if (!hasLower(pwd))     sug.push('Add lowercase letters (a-z).');
      if (!hasDigit(pwd))     sug.push('Add digits (0-9).');
      if (!hasSpecial(pwd))   sug.push('Add special characters (e.g. !@#$%^&*).');
      if (hasRepeat(pwd))     sug.push('Avoid repeating the same character three or more times.');
      if (hasSeq(pwd))        sug.push('Avoid sequential patterns like "abc" or "123".');
      if (hasCommonWord(pwd)) sug.push('Remove common words like "password" or "admin".');
      if (isCommon)           sug.push('This is in the top-100 most common passwords — choose something unique.');
    }
    var sugList = document.getElementById('pm-suggestions-list');
    sugList.innerHTML = '';
    if (!pwd.length || sug.length === 0) {
      var li = document.createElement('li');
      li.className = 'pm-no-suggestions';
      li.textContent = pwd.length ? 'Looks great! No suggestions.' : 'Enter a password to get suggestions.';
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
  window.pmAnalyze = pmAnalyze;

  pmAnalyze();
})();
</script>

</div>

---

## How It Works

All analysis runs entirely in your browser using plain JavaScript — no data is ever sent to a server.

**Entropy** (measured in bits) quantifies how unpredictable a password is. The formula is `length × log₂(charset size)`. A 20-character password using all four character types (upper, lower, digit, symbol) produces roughly 131 bits of entropy — effectively uncrackable by brute force with current hardware.

**Crack Time** is estimated at 10 billion guesses per second, representing a well-resourced offline attack. Online attacks are far slower due to rate limiting.

### Strength Levels

| Level | Entropy | Typical Scenario |
|---|---|---|
| Very Weak | < 28 bits | Short or common password |
| Weak | 28–39 bits | Dictionary word + small variation |
| Fair | 40–59 bits | Mixed types, moderate length |
| Strong | 60–79 bits | Long mixed-type password |
| Very Strong | 80+ bits | Full character set, 16+ characters |

### Tips

- Use 16+ characters for everyday accounts; 24+ for critical ones.
- Enable all character types to maximise entropy.
- Avoid real words, names, dates, and keyboard patterns.
- Use a password manager — never reuse passwords across sites.
- Consider a passphrase (e.g. `correct-horse-battery-staple`) for passwords you must memorise.

---

> Generate a new password → [Password Generator](/tools/password-generator/)

> Create and verify hashes → [Hash Generator](/tools/hash-generator/)

## Related Articles

- [Best Password Managers 2026: Secure Every Account for $3/Month](/posts/best-password-managers-2026/)
