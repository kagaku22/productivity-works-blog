---
title: "習慣トラッカー"
date: 2025-05-16
description: "無料の習慣トラッカー。毎日の習慣を記録・連続記録・達成率・ヒートマップで可視化。データはローカル保存、会員登録不要。"
categories: ["無料ツール"]
slug: "habit-tracker"
ShowToc: false
cover:
  image: "/images/covers/habit-tracker-ja.png"
  alt: "習慣トラッカー"
---

<div id="ht-app">
<style>
#ht-app {
  font-family: 'Hiragino Sans', 'Noto Sans JP', sans-serif;
  max-width: 860px;
  margin: 0 auto;
  color: #1e293b;
  font-size: 15px;
}
#ht-app *, #ht-app *::before, #ht-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

/* --- layout --- */
#ht-app .ht-section { margin-bottom: 28px; }
#ht-app .ht-card {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px 22px;
}
#ht-app h2.ht-h2 {
  font-size: 17px;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 14px;
  display: flex;
  align-items: center;
  gap: 8px;
}
#ht-app .ht-badge {
  font-size: 11px;
  font-weight: 700;
  background: #e2e8f0;
  color: #475569;
  border-radius: 20px;
  padding: 2px 9px;
}

/* --- add habit form --- */
#ht-add-form {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  align-items: flex-end;
}
#ht-add-form input[type="text"] {
  flex: 1 1 180px;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  color: #1e293b;
  outline: none;
  transition: border-color .2s;
}
#ht-add-form input[type="text"]:focus { border-color: #6366f1; }
#ht-add-form select {
  padding: 9px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  color: #1e293b;
  cursor: pointer;
  outline: none;
}
#ht-add-form .ht-color-row {
  display: flex;
  align-items: center;
  gap: 6px;
}
#ht-add-form label.ht-lbl { font-size: 13px; color: #64748b; white-space: nowrap; }
#ht-color-pick {
  width: 34px; height: 34px;
  border-radius: 8px;
  border: 1.5px solid #cbd5e1;
  cursor: pointer;
  padding: 2px;
  background: #fff;
}
#ht-add-form button.ht-btn-add {
  padding: 9px 20px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  white-space: nowrap;
  transition: background .2s;
}
#ht-add-form button.ht-btn-add:hover { background: #4f46e5; }

/* --- today list --- */
#ht-today-list { list-style: none; display: flex; flex-direction: column; gap: 10px; }
#ht-today-list li {
  display: flex;
  align-items: center;
  gap: 12px;
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 12px 14px;
  transition: box-shadow .15s;
}
#ht-today-list li:hover { box-shadow: 0 2px 8px rgba(0,0,0,.07); }
#ht-today-list li.ht-done { opacity: .65; }
#ht-today-list .ht-cb {
  width: 24px; height: 24px;
  border-radius: 6px;
  border: 2.5px solid #cbd5e1;
  appearance: none;
  cursor: pointer;
  position: relative;
  flex-shrink: 0;
  transition: background .15s, border-color .15s;
}
#ht-today-list .ht-cb:checked { border-color: transparent; }
#ht-today-list .ht-cb:checked::after {
  content: '';
  position: absolute;
  left: 5px; top: 2px;
  width: 8px; height: 12px;
  border: 2.5px solid #fff;
  border-top: none; border-left: none;
  transform: rotate(45deg);
}
#ht-today-list .ht-habit-dot {
  width: 12px; height: 12px;
  border-radius: 50%;
  flex-shrink: 0;
}
#ht-today-list .ht-habit-name { flex: 1; font-size: 15px; font-weight: 600; }
#ht-today-list .ht-habit-name.done-text { text-decoration: line-through; color: #94a3b8; }
#ht-today-list .ht-freq-tag {
  font-size: 11px;
  background: #f1f5f9;
  color: #64748b;
  border-radius: 5px;
  padding: 2px 7px;
}
#ht-today-list .ht-edit-btn, #ht-today-list .ht-del-btn {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 15px;
  padding: 2px 5px;
  border-radius: 5px;
  color: #94a3b8;
  transition: color .15s, background .15s;
}
#ht-today-list .ht-edit-btn:hover { color: #6366f1; background: #ede9fe; }
#ht-today-list .ht-del-btn:hover { color: #ef4444; background: #fee2e2; }
#ht-empty-msg { color: #94a3b8; font-size: 14px; text-align: center; padding: 20px 0; }

/* --- week grid --- */
#ht-week-wrap { overflow-x: auto; }
#ht-week-table { border-collapse: collapse; width: 100%; min-width: 420px; }
#ht-week-table th, #ht-week-table td {
  text-align: center;
  padding: 7px 6px;
  font-size: 13px;
}
#ht-week-table th { color: #64748b; font-weight: 600; border-bottom: 1px solid #e2e8f0; }
#ht-week-table td.ht-habit-col { text-align: left; font-weight: 600; white-space: nowrap; max-width: 140px; overflow: hidden; text-overflow: ellipsis; }
#ht-week-table td.ht-day-cell {
  width: 44px;
}
.ht-cell-inner {
  width: 28px; height: 28px;
  border-radius: 6px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  cursor: default;
}
.ht-cell-done { color: #fff; }
.ht-cell-miss { background: #f1f5f9; }
.ht-cell-today-border { outline: 2px solid #6366f1; outline-offset: 1px; }
.ht-cell-na { background: transparent; }

/* --- heatmap --- */
#ht-heatmap-wrap { overflow-x: auto; }
#ht-habit-select-row {
  display: flex; align-items: center; gap: 10px; margin-bottom: 12px; flex-wrap: wrap;
}
#ht-habit-select-row label { font-size: 13px; color: #64748b; }
#ht-hm-habit-sel {
  padding: 6px 10px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 13px;
  background: #fff;
  color: #1e293b;
  cursor: pointer;
  outline: none;
}
#ht-heatmap-grid {
  display: flex;
  flex-direction: column;
  gap: 3px;
}
.ht-hm-week-row { display: flex; gap: 3px; }
.ht-hm-cell {
  width: 14px; height: 14px;
  border-radius: 3px;
  position: relative;
  flex-shrink: 0;
}
.ht-hm-cell:hover::after {
  content: attr(data-tip);
  position: absolute;
  bottom: calc(100% + 5px);
  left: 50%;
  transform: translateX(-50%);
  background: #1e293b;
  color: #fff;
  font-size: 11px;
  white-space: nowrap;
  padding: 3px 7px;
  border-radius: 5px;
  pointer-events: none;
  z-index: 20;
}
.ht-hm-month-labels { display: flex; gap: 3px; margin-bottom: 3px; }
.ht-hm-month-lbl { font-size: 10px; color: #94a3b8; min-width: 14px; text-align: center; }
.ht-hm-legend { display: flex; align-items: center; gap: 4px; margin-top: 8px; font-size: 11px; color: #94a3b8; }
.ht-hm-legend-cell { width: 12px; height: 12px; border-radius: 3px; }

/* --- stats --- */
#ht-stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 12px;
}
.ht-stat-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  padding: 14px 16px;
  text-align: center;
}
.ht-stat-num { font-size: 28px; font-weight: 800; color: #6366f1; line-height: 1.1; }
.ht-stat-label { font-size: 12px; color: #64748b; margin-top: 4px; }

/* --- data controls --- */
#ht-data-row { display: flex; gap: 10px; flex-wrap: wrap; }
#ht-data-row button {
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  border: 1.5px solid #cbd5e1;
  background: #fff;
  color: #475569;
  transition: background .2s, border-color .2s;
}
#ht-data-row button:hover { background: #f1f5f9; border-color: #94a3b8; }
#ht-data-row button.danger { color: #ef4444; border-color: #fca5a5; }
#ht-data-row button.danger:hover { background: #fee2e2; border-color: #ef4444; }

/* --- edit modal --- */
#ht-modal-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(15,23,42,.45);
  z-index: 1000;
  align-items: center;
  justify-content: center;
}
#ht-modal-overlay.open { display: flex; }
#ht-modal {
  background: #fff;
  border-radius: 14px;
  padding: 26px 28px;
  width: 340px;
  max-width: 95vw;
  box-shadow: 0 10px 40px rgba(0,0,0,.2);
}
#ht-modal h3 { font-size: 16px; font-weight: 700; margin-bottom: 16px; }
#ht-modal .ht-modal-field { margin-bottom: 12px; }
#ht-modal label { font-size: 13px; color: #64748b; display: block; margin-bottom: 4px; }
#ht-modal input[type="text"], #ht-modal select {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid #cbd5e1;
  border-radius: 8px;
  font-size: 14px;
  color: #1e293b;
  outline: none;
}
#ht-modal input[type="text"]:focus, #ht-modal select:focus { border-color: #6366f1; }
#ht-modal .ht-modal-btns { display: flex; gap: 10px; margin-top: 18px; justify-content: flex-end; }
#ht-modal .ht-modal-btns button {
  padding: 9px 20px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  border: none;
}
#ht-modal-save { background: #6366f1; color: #fff; }
#ht-modal-save:hover { background: #4f46e5; }
#ht-modal-cancel { background: #f1f5f9; color: #475569; }
#ht-modal-cancel:hover { background: #e2e8f0; }

/* responsive */
@media (max-width: 520px) {
  #ht-app .ht-card { padding: 14px 12px; }
  #ht-stats-grid { grid-template-columns: 1fr 1fr; }
}
</style>

<!-- ===== ADD HABIT ===== -->
<div class="ht-section">
  <div class="ht-card">
    <h2 class="ht-h2">&#43; 習慣を追加</h2>
    <div id="ht-add-form">
      <input type="text" id="ht-name-input" placeholder="習慣名（例：ランニング）" maxlength="30" />
      <div class="ht-color-row">
        <label class="ht-lbl">色</label>
        <input type="color" id="ht-color-pick" value="#6366f1" />
      </div>
      <select id="ht-freq-sel">
        <option value="daily">毎日</option>
        <option value="weekday">平日のみ</option>
        <option value="custom">カスタム曜日</option>
      </select>
      <div id="ht-custom-days" style="display:none;gap:5px;flex-wrap:wrap;">
        <label style="font-size:13px;color:#64748b;align-self:center;">曜日:</label>
        <label class="ht-day-chk"><input type="checkbox" value="0">日</label>
        <label class="ht-day-chk"><input type="checkbox" value="1">月</label>
        <label class="ht-day-chk"><input type="checkbox" value="2">火</label>
        <label class="ht-day-chk"><input type="checkbox" value="3">水</label>
        <label class="ht-day-chk"><input type="checkbox" value="4">木</label>
        <label class="ht-day-chk"><input type="checkbox" value="5">金</label>
        <label class="ht-day-chk"><input type="checkbox" value="6">土</label>
      </div>
      <button class="ht-btn-add" onclick="htAddHabit()">追加</button>
    </div>
  </div>
</div>

<!-- ===== TODAY ===== -->
<div class="ht-section">
  <div class="ht-card">
    <h2 class="ht-h2">&#9989; 今日の習慣 <span class="ht-badge" id="ht-today-badge">0/0</span></h2>
    <ul id="ht-today-list"><li id="ht-empty-msg" style="list-style:none;padding:20px 0;text-align:center;color:#94a3b8;font-size:14px;">習慣をまだ登録していません</li></ul>
  </div>
</div>

<!-- ===== WEEK GRID ===== -->
<div class="ht-section">
  <div class="ht-card">
    <h2 class="ht-h2">&#128197; 週間グリッド</h2>
    <div id="ht-week-wrap"><p style="color:#94a3b8;font-size:14px;" id="ht-week-empty">習慣を追加すると表示されます</p></div>
  </div>
</div>

<!-- ===== HEATMAP ===== -->
<div class="ht-section">
  <div class="ht-card">
    <h2 class="ht-h2">&#128293; 月間ヒートマップ</h2>
    <div id="ht-habit-select-row">
      <label>習慣を選択:</label>
      <select id="ht-hm-habit-sel" onchange="htRenderHeatmap()"></select>
    </div>
    <div id="ht-heatmap-wrap">
      <p style="color:#94a3b8;font-size:14px;" id="ht-hm-empty">習慣を追加すると表示されます</p>
    </div>
  </div>
</div>

<!-- ===== STATS ===== -->
<div class="ht-section">
  <div class="ht-card">
    <h2 class="ht-h2">&#128200; 統計</h2>
    <div id="ht-stats-grid">
      <div class="ht-stat-card"><div class="ht-stat-num" id="ht-stat-streak">0</div><div class="ht-stat-label">現在の連続日数（日）</div></div>
      <div class="ht-stat-card"><div class="ht-stat-num" id="ht-stat-best">0</div><div class="ht-stat-label">最長連続記録（日）</div></div>
      <div class="ht-stat-card"><div class="ht-stat-num" id="ht-stat-rate">0%</div><div class="ht-stat-label">今月の達成率</div></div>
      <div class="ht-stat-card"><div class="ht-stat-num" id="ht-stat-total">0</div><div class="ht-stat-label">累計達成回数</div></div>
    </div>
    <p style="font-size:12px;color:#94a3b8;margin-top:10px;">※ 統計はヒートマップで選択中の習慣に対して計算されます</p>
  </div>
</div>

<!-- ===== DATA ===== -->
<div class="ht-section">
  <div class="ht-card">
    <h2 class="ht-h2">&#128190; データ管理</h2>
    <div id="ht-data-row">
      <button onclick="htExportJSON()">JSONで書き出し</button>
      <button onclick="document.getElementById('ht-import-file').click()">JSONを取り込む</button>
      <button class="danger" onclick="htClearAll()">全データ削除</button>
    </div>
    <input type="file" id="ht-import-file" accept=".json" style="display:none;" onchange="htImportJSON(event)" />
  </div>
</div>

<!-- ===== EDIT MODAL ===== -->
<div id="ht-modal-overlay">
  <div id="ht-modal">
    <h3>習慣を編集</h3>
    <div class="ht-modal-field">
      <label>習慣名</label>
      <input type="text" id="ht-edit-name" maxlength="30" />
    </div>
    <div class="ht-modal-field">
      <label>色</label>
      <input type="color" id="ht-edit-color" style="width:100%;height:38px;border:1.5px solid #cbd5e1;border-radius:8px;cursor:pointer;" />
    </div>
    <div class="ht-modal-field">
      <label>頻度</label>
      <select id="ht-edit-freq">
        <option value="daily">毎日</option>
        <option value="weekday">平日のみ</option>
        <option value="custom">カスタム曜日</option>
      </select>
    </div>
    <div id="ht-edit-custom-days" style="display:none;gap:5px;flex-wrap:wrap;margin-top:8px;">
      <label style="font-size:13px;color:#64748b;width:100%;margin-bottom:2px;">曜日を選択:</label>
      <label class="ht-eday-chk"><input type="checkbox" value="0">日</label>
      <label class="ht-eday-chk"><input type="checkbox" value="1">月</label>
      <label class="ht-eday-chk"><input type="checkbox" value="2">火</label>
      <label class="ht-eday-chk"><input type="checkbox" value="3">水</label>
      <label class="ht-eday-chk"><input type="checkbox" value="4">木</label>
      <label class="ht-eday-chk"><input type="checkbox" value="5">金</label>
      <label class="ht-eday-chk"><input type="checkbox" value="6">土</label>
    </div>
    <div class="ht-modal-btns">
      <button id="ht-modal-cancel" onclick="htCloseModal()">キャンセル</button>
      <button id="ht-modal-save" onclick="htSaveEdit()">保存</button>
    </div>
  </div>
</div>

<style>
#ht-add-form #ht-custom-days { display: none; }
#ht-add-form #ht-custom-days.show { display: flex; }
#ht-add-form .ht-day-chk, #ht-modal .ht-eday-chk {
  display: flex; align-items: center; gap: 3px;
  font-size: 13px; cursor: pointer;
  background: #f1f5f9; border: 1px solid #e2e8f0;
  border-radius: 5px; padding: 3px 8px;
  user-select: none;
}
#ht-add-form .ht-day-chk input, #ht-modal .ht-eday-chk input { display: none; }
#ht-modal #ht-edit-custom-days { display: none; }
#ht-modal #ht-edit-custom-days.show { display: flex; }
</style>

<script>
(function(){
'use strict';

var LS_KEY = 'ht_v1';
var state = { habits: [], logs: {} };
var editId = null;

// ===== STORAGE =====
function save() {
  try { localStorage.setItem(LS_KEY, JSON.stringify(state)); } catch(e){}
}
function load() {
  try {
    var d = localStorage.getItem(LS_KEY);
    if (d) state = JSON.parse(d);
    if (!state.habits) state.habits = [];
    if (!state.logs) state.logs = {};
  } catch(e){ state = { habits: [], logs: {} }; }
}

// ===== HELPERS =====
function uid() { return Date.now().toString(36) + Math.random().toString(36).slice(2,7); }
function todayStr() {
  var d = new Date();
  return d.getFullYear() + '-' + pad(d.getMonth()+1) + '-' + pad(d.getDate());
}
function pad(n){ return n < 10 ? '0'+n : ''+n; }
function dateStr(d) {
  return d.getFullYear() + '-' + pad(d.getMonth()+1) + '-' + pad(d.getDate());
}
function addDays(dateStr, n) {
  var d = new Date(dateStr + 'T00:00:00');
  d.setDate(d.getDate() + n);
  return dateStr(d);
}
function getDayOfWeek(ds) {
  return new Date(ds + 'T00:00:00').getDay(); // 0=Sun
}
function isScheduled(habit, ds) {
  var dow = getDayOfWeek(ds);
  if (habit.freq === 'daily') return true;
  if (habit.freq === 'weekday') return dow >= 1 && dow <= 5;
  if (habit.freq === 'custom') return habit.days && habit.days.indexOf(dow) !== -1;
  return true;
}
function isLogged(habitId, ds) {
  return !!(state.logs[habitId] && state.logs[habitId][ds]);
}
function freqLabel(h) {
  if (h.freq === 'daily') return '毎日';
  if (h.freq === 'weekday') return '平日';
  if (h.freq === 'custom') {
    var names = ['日','月','火','水','木','金','土'];
    return (h.days||[]).map(function(d){ return names[d]; }).join('・');
  }
  return '';
}

// ===== ADD =====
window.htAddHabit = function() {
  var name = document.getElementById('ht-name-input').value.trim();
  if (!name) { alert('習慣名を入力してください'); return; }
  var color = document.getElementById('ht-color-pick').value;
  var freq = document.getElementById('ht-freq-sel').value;
  var days = [];
  if (freq === 'custom') {
    document.querySelectorAll('#ht-custom-days input:checked').forEach(function(cb){ days.push(parseInt(cb.value)); });
    if (!days.length) { alert('曜日を1つ以上選んでください'); return; }
  }
  state.habits.push({ id: uid(), name: name, color: color, freq: freq, days: days });
  document.getElementById('ht-name-input').value = '';
  save();
  render();
};

// freq select toggle
document.getElementById('ht-freq-sel').addEventListener('change', function(){
  var cd = document.getElementById('ht-custom-days');
  if (this.value === 'custom') cd.classList.add('show');
  else cd.classList.remove('show');
});
document.getElementById('ht-edit-freq').addEventListener('change', function(){
  var cd = document.getElementById('ht-edit-custom-days');
  if (this.value === 'custom') cd.classList.add('show');
  else cd.classList.remove('show');
});

// ===== DELETE =====
window.htDeleteHabit = function(id) {
  if (!confirm('この習慣を削除しますか？ログも消えます。')) return;
  state.habits = state.habits.filter(function(h){ return h.id !== id; });
  delete state.logs[id];
  save();
  render();
};

// ===== EDIT MODAL =====
window.htOpenEdit = function(id) {
  editId = id;
  var h = state.habits.find(function(x){ return x.id === id; });
  if (!h) return;
  document.getElementById('ht-edit-name').value = h.name;
  document.getElementById('ht-edit-color').value = h.color;
  document.getElementById('ht-edit-freq').value = h.freq;
  var cd = document.getElementById('ht-edit-custom-days');
  if (h.freq === 'custom') cd.classList.add('show'); else cd.classList.remove('show');
  document.querySelectorAll('#ht-edit-custom-days input').forEach(function(cb){
    cb.checked = h.days && h.days.indexOf(parseInt(cb.value)) !== -1;
  });
  document.getElementById('ht-modal-overlay').classList.add('open');
};
window.htCloseModal = function() {
  document.getElementById('ht-modal-overlay').classList.remove('open');
  editId = null;
};
window.htSaveEdit = function() {
  if (!editId) return;
  var h = state.habits.find(function(x){ return x.id === editId; });
  if (!h) return;
  var name = document.getElementById('ht-edit-name').value.trim();
  if (!name) { alert('習慣名を入力してください'); return; }
  h.name = name;
  h.color = document.getElementById('ht-edit-color').value;
  h.freq = document.getElementById('ht-edit-freq').value;
  h.days = [];
  if (h.freq === 'custom') {
    document.querySelectorAll('#ht-edit-custom-days input:checked').forEach(function(cb){ h.days.push(parseInt(cb.value)); });
    if (!h.days.length) { alert('曜日を1つ以上選んでください'); return; }
  }
  save();
  htCloseModal();
  render();
};
document.getElementById('ht-modal-overlay').addEventListener('click', function(e){
  if (e.target === this) htCloseModal();
});

// ===== TOGGLE LOG =====
window.htToggleLog = function(habitId, ds, cb) {
  if (!state.logs[habitId]) state.logs[habitId] = {};
  if (cb.checked) state.logs[habitId][ds] = true;
  else delete state.logs[habitId][ds];
  save();
  renderToday();
  renderWeek();
  renderHeatmap();
  renderStats();
};

// ===== RENDER TODAY =====
function renderToday() {
  var today = todayStr();
  var dow = getDayOfWeek(today);
  var list = document.getElementById('ht-today-list');
  var habits = state.habits.filter(function(h){ return isScheduled(h, today); });
  var badge = document.getElementById('ht-today-badge');
  if (!habits.length) {
    list.innerHTML = '<li style="list-style:none;padding:20px 0;text-align:center;color:#94a3b8;font-size:14px;">今日スケジュールされた習慣はありません</li>';
    badge.textContent = '0/0';
    return;
  }
  var done = habits.filter(function(h){ return isLogged(h.id, today); }).length;
  badge.textContent = done + '/' + habits.length;
  list.innerHTML = habits.map(function(h){
    var checked = isLogged(h.id, today);
    return '<li class="'+(checked?'ht-done':'')+'">' +
      '<input type="checkbox" class="ht-cb" style="background:'+(checked?h.color:'#fff')+';" '+(checked?'checked':'')+
      ' onchange="htToggleLog(\''+h.id+'\',\''+today+'\',this)" />' +
      '<span class="ht-habit-dot" style="background:'+h.color+';"></span>' +
      '<span class="ht-habit-name'+(checked?' done-text':'')+'">'+esc(h.name)+'</span>' +
      '<span class="ht-freq-tag">'+freqLabel(h)+'</span>' +
      '<button class="ht-edit-btn" onclick="htOpenEdit(\''+h.id+'\')" title="編集">&#9998;</button>' +
      '<button class="ht-del-btn" onclick="htDeleteHabit(\''+h.id+'\')" title="削除">&#128465;</button>' +
      '</li>';
  }).join('');
}

// ===== RENDER WEEK =====
function renderWeek() {
  var wrap = document.getElementById('ht-week-wrap');
  if (!state.habits.length) {
    wrap.innerHTML = '<p style="color:#94a3b8;font-size:14px;">習慣を追加すると表示されます</p>';
    return;
  }
  var today = todayStr();
  var days = [];
  for (var i = 6; i >= 0; i--) { days.push(addDays(today, -i)); }
  var dowNames = ['日','月','火','水','木','金','土'];
  var header = '<tr><th style="text-align:left;">習慣</th>' +
    days.map(function(ds){
      var d = new Date(ds+'T00:00:00');
      var isToday = ds === today;
      return '<th style="'+(isToday?'color:#6366f1;font-weight:800;':'')+'">'+dowNames[d.getDay()]+'<br><span style="font-size:11px;font-weight:400;">'+pad(d.getMonth()+1)+'/'+pad(d.getDate())+'</span></th>';
    }).join('') + '</tr>';
  var rows = state.habits.map(function(h){
    var cells = days.map(function(ds){
      var sched = isScheduled(h, ds);
      var done = isLogged(h.id, ds);
      var isToday = ds === today;
      var inner = '';
      if (!sched) {
        inner = '<div class="ht-cell-inner ht-cell-na" style="opacity:.15;">—</div>';
      } else if (done) {
        inner = '<div class="ht-cell-inner ht-cell-done'+(isToday?' ht-cell-today-border':'')+'" style="background:'+h.color+';">&#10003;</div>';
      } else {
        inner = '<div class="ht-cell-inner ht-cell-miss'+(isToday?' ht-cell-today-border':'')+'" style="'+(isToday?'background:#ede9fe;':'')+'"></div>';
      }
      return '<td class="ht-day-cell">'+inner+'</td>';
    }).join('');
    return '<tr><td class="ht-habit-col"><span style="display:inline-block;width:9px;height:9px;border-radius:50%;background:'+h.color+';margin-right:6px;vertical-align:middle;"></span>'+esc(h.name)+'</td>'+cells+'</tr>';
  }).join('');
  wrap.innerHTML = '<table id="ht-week-table"><thead>'+header+'</thead><tbody>'+rows+'</tbody></table>';
}

// ===== RENDER HEATMAP =====
function renderHeatmapSelect() {
  var sel = document.getElementById('ht-hm-habit-sel');
  var prev = sel.value;
  sel.innerHTML = state.habits.map(function(h){
    return '<option value="'+h.id+'">'+esc(h.name)+'</option>';
  }).join('');
  if (prev && state.habits.find(function(x){ return x.id === prev; })) sel.value = prev;
}

window.htRenderHeatmap = function() { renderHeatmap(); renderStats(); };

function renderHeatmap() {
  var wrap = document.getElementById('ht-heatmap-wrap');
  var emEl = document.getElementById('ht-hm-empty');
  if (!state.habits.length) {
    if(emEl) emEl.style.display = '';
    wrap.innerHTML = '<p style="color:#94a3b8;font-size:14px;" id="ht-hm-empty">習慣を追加すると表示されます</p>';
    return;
  }
  var habitId = document.getElementById('ht-hm-habit-sel').value;
  var habit = state.habits.find(function(h){ return h.id === habitId; });
  if (!habit) habit = state.habits[0];

  // build 16 weeks (112 days) ending today
  var today = todayStr();
  var todayD = new Date(today + 'T00:00:00');
  var endDow = todayD.getDay(); // 0=Sun
  // end on Saturday of this week
  var endDate = new Date(todayD);
  endDate.setDate(endDate.getDate() + (6 - endDow));
  var startDate = new Date(endDate);
  startDate.setDate(startDate.getDate() - 16*7 + 1);

  // build weeks array
  var weeks = [];
  var cur = new Date(startDate);
  while (cur <= endDate) {
    var week = [];
    for (var d = 0; d < 7; d++) {
      var ds = dateStr(cur);
      week.push(ds);
      cur.setDate(cur.getDate() + 1);
    }
    weeks.push(week);
  }

  // month labels row
  var monthNames = ['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
  var monthLabels = weeks.map(function(w){
    var d = new Date(w[0]+'T00:00:00');
    return (d.getDate() <= 7) ? monthNames[d.getMonth()] : '';
  });

  // color scale (5 levels)
  function cellColor(ds) {
    var future = ds > today;
    var sched = isScheduled(habit, ds);
    var done = isLogged(habit.id, ds);
    if (future || !sched) return '#f1f5f9';
    if (!done) return '#e2e8f0';
    return habit.color;
  }

  var html = '<div class="ht-hm-month-labels">' +
    monthLabels.map(function(m){ return '<div class="ht-hm-month-lbl">'+m+'</div>'; }).join('') +
    '</div>';
  html += '<div class="ht-heatmap-grid" style="flex-direction:row;">';
  weeks.forEach(function(week, wi){
    html += '<div class="ht-hm-week-row" style="flex-direction:column;">';
    week.forEach(function(ds){
      var future = ds > today;
      var tip = ds + (future ? '' : (isLogged(habit.id, ds) ? ' ✓達成' : ' ✗未達成'));
      html += '<div class="ht-hm-cell" style="background:'+cellColor(ds)+';'+(ds===today?'outline:2px solid #6366f1;outline-offset:1px;':'')+'" data-tip="'+tip+'"></div>';
    });
    html += '</div>';
  });
  html += '</div>';
  html += '<div class="ht-hm-legend"><span>少</span><div class="ht-hm-legend-cell" style="background:#e2e8f0;"></div><div class="ht-hm-legend-cell" style="background:'+habit.color+';opacity:.4;"></div><div class="ht-hm-legend-cell" style="background:'+habit.color+';opacity:.7;"></div><div class="ht-hm-legend-cell" style="background:'+habit.color+';"></div><span>多</span></div>';

  wrap.innerHTML = html;
}

// ===== RENDER STATS =====
function renderStats() {
  var habitId = document.getElementById('ht-hm-habit-sel').value;
  var habit = state.habits.find(function(h){ return h.id === habitId; });
  if (!habit) {
    ['ht-stat-streak','ht-stat-best','ht-stat-rate','ht-stat-total'].forEach(function(id){
      document.getElementById(id).textContent = id==='ht-stat-rate'?'0%':'0';
    });
    return;
  }
  var today = todayStr();
  var logs = state.logs[habit.id] || {};

  // total
  var total = Object.keys(logs).length;

  // streak (current)
  var streak = 0;
  var cur = today;
  var limit = 0;
  while (limit++ < 400) {
    if (!isScheduled(habit, cur)) { cur = addDays(cur, -1); continue; }
    if (logs[cur]) { streak++; cur = addDays(cur, -1); }
    else break;
  }

  // best streak
  var allDates = [];
  var d0 = new Date(today+'T00:00:00');
  d0.setDate(d0.getDate() - 365);
  var dCur = new Date(d0);
  var dEnd = new Date(today+'T00:00:00');
  while (dCur <= dEnd) {
    allDates.push(dateStr(dCur));
    dCur.setDate(dCur.getDate()+1);
  }
  var best = 0, run = 0;
  allDates.forEach(function(ds){
    if (!isScheduled(habit, ds)) return;
    if (logs[ds]) { run++; if(run>best) best=run; }
    else run = 0;
  });

  // this month rate
  var now = new Date();
  var y = now.getFullYear(), m = now.getMonth();
  var daysInMonth = new Date(y, m+1, 0).getDate();
  var todayDate = now.getDate();
  var monthDone = 0, monthSched = 0;
  for (var dd = 1; dd <= Math.min(todayDate, daysInMonth); dd++) {
    var ds = y+'-'+pad(m+1)+'-'+pad(dd);
    if (isScheduled(habit, ds)) {
      monthSched++;
      if (logs[ds]) monthDone++;
    }
  }
  var rate = monthSched ? Math.round(monthDone/monthSched*100) : 0;

  document.getElementById('ht-stat-streak').textContent = streak;
  document.getElementById('ht-stat-best').textContent = best;
  document.getElementById('ht-stat-rate').textContent = rate + '%';
  document.getElementById('ht-stat-total').textContent = total;
}

// ===== DATA =====
window.htExportJSON = function() {
  var blob = new Blob([JSON.stringify(state, null, 2)], {type:'application/json'});
  var a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'habit-tracker-' + todayStr() + '.json';
  a.click();
};
window.htImportJSON = function(e) {
  var file = e.target.files[0];
  if (!file) return;
  var reader = new FileReader();
  reader.onload = function(ev){
    try {
      var d = JSON.parse(ev.target.result);
      if (!d.habits || !d.logs) throw new Error('形式が不正です');
      if (!confirm('現在のデータを上書きしてインポートしますか？')) return;
      state = d;
      save();
      render();
      alert('インポートしました');
    } catch(err) { alert('読み込みに失敗しました: ' + err.message); }
    e.target.value = '';
  };
  reader.readAsText(file);
};
window.htClearAll = function() {
  if (!confirm('全習慣・全ログを削除します。元に戻せません。よろしいですか？')) return;
  state = { habits: [], logs: {} };
  save();
  render();
};

// ===== ESCAPE =====
function esc(s){ var d=document.createElement('div');d.textContent=s;return d.innerHTML; }

// ===== FULL RENDER =====
function render() {
  renderHeatmapSelect();
  renderToday();
  renderWeek();
  renderHeatmap();
  renderStats();
}

// ===== INIT =====
load();
render();

})();
</script>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
  <p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
  <span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

---

> ポモドーロで集中 → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)
> フラッシュカードで学習 → [フラッシュカードメーカー](/ja/tools/flashcard-maker/)
> 家計を見直す → [50/30/20 家計バランス計算](/ja/tools/budget-calculator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。
</div>
