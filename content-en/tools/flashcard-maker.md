---
title: "Flashcard Maker"
date: 2025-05-16
description: "Free online flashcard maker. Create, study, and review flashcards with spaced repetition — supports import/export, no sign-up required."
categories: ["Free Tools"]
slug: "flashcard-maker"
ShowToc: false
cover:
  image: "/images/covers/flashcard-maker.png"
  alt: "Flashcard Maker"
---

<div id="fc-app">

<style>
/* ── Reset & base ─────────────────────────────────────────── */
#fc-app *,
#fc-app *::before,
#fc-app *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#fc-app {
  --slate-50:  #f8fafc;
  --slate-100: #f1f5f9;
  --slate-200: #e2e8f0;
  --slate-300: #cbd5e1;
  --slate-400: #94a3b8;
  --slate-500: #64748b;
  --slate-600: #475569;
  --slate-700: #334155;
  --slate-800: #1e293b;
  --slate-900: #0f172a;
  --accent:    #3b82f6;
  --accent-h:  #2563eb;
  --green:     #22c55e;
  --red:       #ef4444;
  --amber:     #f59e0b;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: var(--slate-800);
  background: var(--slate-50);
  border-radius: 12px;
  padding: 24px 20px;
  max-width: 760px;
  margin: 0 auto;
}

/* ── Tab nav ──────────────────────────────────────────────── */
#fc-app .fc-tabs {
  display: flex;
  gap: 4px;
  background: var(--slate-200);
  border-radius: 10px;
  padding: 4px;
  margin-bottom: 24px;
}

#fc-app .fc-tab {
  flex: 1;
  padding: 9px 6px;
  border: none;
  background: transparent;
  border-radius: 7px;
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--slate-500);
  cursor: pointer;
  transition: background .18s, color .18s;
}

#fc-app .fc-tab.active {
  background: #fff;
  color: var(--slate-800);
  box-shadow: 0 1px 4px rgba(0,0,0,.12);
}

/* ── Panels ───────────────────────────────────────────────── */
#fc-app .fc-panel { display: none; }
#fc-app .fc-panel.active { display: block; }

/* ── Section headings ─────────────────────────────────────── */
#fc-app h2 {
  font-size: 1.1rem;
  color: var(--slate-700);
  margin-bottom: 14px;
}

/* ── Form elements ────────────────────────────────────────── */
#fc-app label {
  display: block;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--slate-600);
  margin-bottom: 4px;
}

#fc-app input[type="text"],
#fc-app textarea {
  width: 100%;
  padding: 9px 12px;
  border: 1.5px solid var(--slate-300);
  border-radius: 8px;
  font-size: 0.95rem;
  color: var(--slate-800);
  background: #fff;
  outline: none;
  transition: border-color .15s;
  resize: vertical;
}

#fc-app input[type="text"]:focus,
#fc-app textarea:focus {
  border-color: var(--accent);
}

#fc-app .fc-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 12px;
}

@media (max-width: 500px) {
  #fc-app .fc-row { grid-template-columns: 1fr; }
}

/* ── Buttons ──────────────────────────────────────────────── */
#fc-app .btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 9px 18px;
  border: none;
  border-radius: 8px;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: background .15s, transform .1s;
}
#fc-app .btn:active { transform: scale(.97); }

#fc-app .btn-primary  { background: var(--accent);  color: #fff; }
#fc-app .btn-primary:hover { background: var(--accent-h); }

#fc-app .btn-success  { background: var(--green);   color: #fff; }
#fc-app .btn-success:hover { background: #16a34a; }

#fc-app .btn-danger   { background: var(--red);     color: #fff; }
#fc-app .btn-danger:hover { background: #dc2626; }

#fc-app .btn-ghost {
  background: var(--slate-100);
  color: var(--slate-700);
  border: 1.5px solid var(--slate-200);
}
#fc-app .btn-ghost:hover { background: var(--slate-200); }

#fc-app .btn-sm {
  padding: 5px 11px;
  font-size: 0.78rem;
}

#fc-app .btn-full { width: 100%; }

#fc-app .fc-btn-row {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 10px;
}

/* ── Card list ────────────────────────────────────────────── */
#fc-app .fc-card-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 20px;
  max-height: 340px;
  overflow-y: auto;
  padding-right: 2px;
}

#fc-app .fc-card-item {
  background: #fff;
  border: 1.5px solid var(--slate-200);
  border-radius: 9px;
  padding: 10px 12px;
  display: flex;
  align-items: flex-start;
  gap: 10px;
}

#fc-app .fc-card-item .fc-card-texts {
  flex: 1;
  min-width: 0;
}

#fc-app .fc-card-item .fc-front {
  font-weight: 600;
  font-size: 0.9rem;
  color: var(--slate-800);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#fc-app .fc-card-item .fc-back {
  font-size: 0.82rem;
  color: var(--slate-500);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#fc-app .fc-card-item .fc-card-actions {
  display: flex;
  gap: 6px;
  flex-shrink: 0;
}

#fc-app .fc-empty {
  text-align: center;
  color: var(--slate-400);
  font-size: 0.9rem;
  padding: 24px 0;
}

/* ── CSV import ───────────────────────────────────────────── */
#fc-app .fc-csv-box {
  margin-top: 20px;
  padding: 16px;
  background: var(--slate-100);
  border-radius: 10px;
  border: 1.5px dashed var(--slate-300);
}

#fc-app .fc-csv-box p {
  font-size: 0.8rem;
  color: var(--slate-500);
  margin-bottom: 8px;
}

#fc-app .fc-csv-box code {
  font-size: 0.78rem;
  background: var(--slate-200);
  padding: 1px 5px;
  border-radius: 4px;
}

/* ── Flip card ────────────────────────────────────────────── */
#fc-app .fc-study-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 14px;
  flex-wrap: wrap;
  gap: 8px;
}

#fc-app .fc-progress-bar {
  width: 100%;
  height: 6px;
  background: var(--slate-200);
  border-radius: 99px;
  margin-bottom: 20px;
  overflow: hidden;
}

#fc-app .fc-progress-fill {
  height: 100%;
  background: var(--accent);
  border-radius: 99px;
  transition: width .3s ease;
}

#fc-app .fc-flip-scene {
  perspective: 1000px;
  width: 100%;
  max-width: 560px;
  margin: 0 auto 24px;
  cursor: pointer;
  user-select: none;
}

#fc-app .fc-flip-card {
  position: relative;
  width: 100%;
  padding-bottom: 56%;
  transform-style: preserve-3d;
  transition: transform .5s cubic-bezier(.4,0,.2,1);
  border-radius: 14px;
}

#fc-app .fc-flip-card.flipped {
  transform: rotateY(180deg);
}

#fc-app .fc-flip-face {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  border-radius: 14px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 28px 24px;
  text-align: center;
  box-shadow: 0 4px 20px rgba(0,0,0,.10);
}

#fc-app .fc-flip-front {
  background: #fff;
  border: 2px solid var(--slate-200);
}

#fc-app .fc-flip-back {
  background: var(--slate-800);
  color: #fff;
  transform: rotateY(180deg);
}

#fc-app .fc-flip-label {
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--slate-400);
  margin-bottom: 12px;
}

#fc-app .fc-flip-back .fc-flip-label {
  color: var(--slate-400);
}

#fc-app .fc-flip-text {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 1.4;
  color: inherit;
}

#fc-app .fc-flip-hint {
  font-size: 0.75rem;
  color: var(--slate-400);
  margin-top: 10px;
}

#fc-app .fc-study-actions {
  display: flex;
  gap: 12px;
  justify-content: center;
  margin-top: 4px;
}

#fc-app .fc-study-actions .btn {
  flex: 1;
  max-width: 200px;
  padding: 13px;
  font-size: 0.95rem;
}

#fc-app .fc-study-complete {
  text-align: center;
  padding: 32px 16px;
}

#fc-app .fc-study-complete h2 {
  font-size: 1.6rem;
  margin-bottom: 8px;
}

#fc-app .fc-study-complete p {
  color: var(--slate-500);
  margin-bottom: 20px;
}

#fc-app .fc-summary-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-bottom: 20px;
}

#fc-app .fc-summary-card {
  background: #fff;
  border: 1.5px solid var(--slate-200);
  border-radius: 10px;
  padding: 14px 8px;
  text-align: center;
}

#fc-app .fc-summary-card .fc-num {
  font-size: 1.9rem;
  font-weight: 700;
  line-height: 1;
}

#fc-app .fc-summary-card .fc-lbl {
  font-size: 0.75rem;
  color: var(--slate-500);
  margin-top: 4px;
}

#fc-app .fc-summary-card.green .fc-num { color: var(--green); }
#fc-app .fc-summary-card.red   .fc-num { color: var(--red); }
#fc-app .fc-summary-card.blue  .fc-num { color: var(--accent); }

/* ── Stats panel ──────────────────────────────────────────── */
#fc-app .fc-stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
  margin-bottom: 24px;
}

@media (max-width: 400px) {
  #fc-app .fc-stats-grid { grid-template-columns: 1fr; }
}

#fc-app .fc-stat-box {
  background: #fff;
  border: 1.5px solid var(--slate-200);
  border-radius: 10px;
  padding: 16px;
  text-align: center;
}

#fc-app .fc-stat-box .fc-stat-num {
  font-size: 2.2rem;
  font-weight: 700;
  line-height: 1;
}

#fc-app .fc-stat-box .fc-stat-lbl {
  font-size: 0.78rem;
  color: var(--slate-500);
  margin-top: 4px;
}

#fc-app .fc-stat-box.green .fc-stat-num { color: var(--green); }
#fc-app .fc-stat-box.amber .fc-stat-num { color: var(--amber); }
#fc-app .fc-stat-box.blue  .fc-stat-num { color: var(--accent); }
#fc-app .fc-stat-box.slate .fc-stat-num { color: var(--slate-600); }

/* ── Manage panel ─────────────────────────────────────────── */
#fc-app .fc-manage-section {
  background: #fff;
  border: 1.5px solid var(--slate-200);
  border-radius: 10px;
  padding: 18px;
  margin-bottom: 16px;
}

#fc-app .fc-manage-section h3 {
  font-size: 0.95rem;
  color: var(--slate-700);
  margin-bottom: 12px;
}

#fc-app .fc-manage-section p {
  font-size: 0.83rem;
  color: var(--slate-500);
  margin-bottom: 10px;
}

/* ── Inline edit ──────────────────────────────────────────── */
#fc-app .fc-inline-edit {
  display: none;
  flex-direction: column;
  gap: 6px;
  margin-top: 8px;
}
#fc-app .fc-inline-edit.open { display: flex; }

/* ── Toast ────────────────────────────────────────────────── */
#fc-app .fc-toast {
  position: fixed;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: var(--slate-800);
  color: #fff;
  padding: 10px 22px;
  border-radius: 99px;
  font-size: 0.85rem;
  font-weight: 500;
  opacity: 0;
  pointer-events: none;
  transition: opacity .25s, transform .25s;
  z-index: 9999;
  white-space: nowrap;
}
#fc-app .fc-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

/* ── No-cards overlay ─────────────────────────────────────── */
#fc-app .fc-no-cards {
  text-align: center;
  padding: 48px 16px;
  color: var(--slate-400);
}
#fc-app .fc-no-cards p { margin-top: 8px; font-size: 0.9rem; }
</style>

<!-- ── Tab Navigation ───────────────────────────────────── -->
<div class="fc-tabs" role="tablist">
  <button class="fc-tab active" data-tab="create"  role="tab">Create</button>
  <button class="fc-tab"        data-tab="study"   role="tab">Study</button>
  <button class="fc-tab"        data-tab="stats"   role="tab">Stats</button>
  <button class="fc-tab"        data-tab="manage"  role="tab">Manage</button>
</div>

<!-- ══════════════════════════════════════════════════════════
     CREATE PANEL
════════════════════════════════════════════════════════════ -->
<div id="fc-panel-create" class="fc-panel active" role="tabpanel">

  <h2>Add a Card</h2>

  <div class="fc-row">
    <div>
      <label for="fc-front">Front (question)</label>
      <textarea id="fc-front" rows="3" placeholder="What is the capital of France?"></textarea>
    </div>
    <div>
      <label for="fc-back">Back (answer)</label>
      <textarea id="fc-back" rows="3" placeholder="Paris"></textarea>
    </div>
  </div>

  <div class="fc-btn-row">
    <button class="btn btn-primary" id="fc-add-btn">+ Add Card</button>
  </div>

  <!-- Card list -->
  <ul class="fc-card-list" id="fc-card-list">
    <!-- populated by JS -->
  </ul>

  <!-- CSV import -->
  <div class="fc-csv-box">
    <p>Bulk import via CSV — one card per line: <code>front,back</code></p>
    <textarea id="fc-csv-input" rows="4" placeholder="What is H2O?,Water&#10;Speed of light?,299,792,458 m/s"></textarea>
    <div class="fc-btn-row">
      <button class="btn btn-ghost btn-sm" id="fc-csv-import-btn">Import CSV</button>
    </div>
  </div>

</div>

<!-- ══════════════════════════════════════════════════════════
     STUDY PANEL
════════════════════════════════════════════════════════════ -->
<div id="fc-panel-study" class="fc-panel" role="tabpanel">

  <div id="fc-study-no-cards" class="fc-no-cards" style="display:none;">
    <strong>No cards yet!</strong>
    <p>Go to Create tab and add some cards first.</p>
  </div>

  <div id="fc-study-area" style="display:none;">

    <div class="fc-study-header">
      <span id="fc-study-counter" style="font-size:.85rem;color:var(--slate-500);font-weight:600;"></span>
      <button class="btn btn-ghost btn-sm" id="fc-shuffle-btn">Shuffle</button>
    </div>

    <div class="fc-progress-bar">
      <div class="fc-progress-fill" id="fc-progress-fill" style="width:0%"></div>
    </div>

    <!-- Flip card -->
    <div class="fc-flip-scene" id="fc-flip-scene" title="Click to flip">
      <div class="fc-flip-card" id="fc-flip-card">
        <div class="fc-flip-face fc-flip-front">
          <div class="fc-flip-label">Question</div>
          <div class="fc-flip-text" id="fc-flip-front-text"></div>
          <div class="fc-flip-hint">Click to reveal answer</div>
        </div>
        <div class="fc-flip-face fc-flip-back">
          <div class="fc-flip-label">Answer</div>
          <div class="fc-flip-text" id="fc-flip-back-text"></div>
        </div>
      </div>
    </div>

    <!-- Answer buttons (hidden until flipped) -->
    <div class="fc-study-actions" id="fc-answer-btns" style="display:none;">
      <button class="btn btn-danger"  id="fc-still-btn">Still Learning</button>
      <button class="btn btn-success" id="fc-know-btn">Know It</button>
    </div>

  </div>

  <!-- Session complete -->
  <div id="fc-study-complete" class="fc-study-complete" style="display:none;">
    <h2>Session Complete!</h2>
    <p>Here's how you did this round:</p>

    <div class="fc-summary-grid">
      <div class="fc-summary-card green">
        <div class="fc-num" id="fc-sum-know">0</div>
        <div class="fc-lbl">Knew It</div>
      </div>
      <div class="fc-summary-card red">
        <div class="fc-num" id="fc-sum-still">0</div>
        <div class="fc-lbl">Still Learning</div>
      </div>
      <div class="fc-summary-card blue">
        <div class="fc-num" id="fc-sum-total">0</div>
        <div class="fc-lbl">Reviewed</div>
      </div>
    </div>

    <div class="fc-btn-row" style="justify-content:center;">
      <button class="btn btn-primary" id="fc-restart-btn">Study Again</button>
      <button class="btn btn-ghost"   id="fc-review-still-btn">Review Struggling Cards</button>
    </div>
  </div>

</div>

<!-- ══════════════════════════════════════════════════════════
     STATS PANEL
════════════════════════════════════════════════════════════ -->
<div id="fc-panel-stats" class="fc-panel" role="tabpanel">

  <h2>Your Progress</h2>

  <div class="fc-stats-grid">
    <div class="fc-stat-box blue">
      <div class="fc-stat-num" id="st-total">0</div>
      <div class="fc-stat-lbl">Total Cards</div>
    </div>
    <div class="fc-stat-box green">
      <div class="fc-stat-num" id="st-mastered">0</div>
      <div class="fc-stat-lbl">Mastered</div>
    </div>
    <div class="fc-stat-box amber">
      <div class="fc-stat-num" id="st-learning">0</div>
      <div class="fc-stat-lbl">Still Learning</div>
    </div>
    <div class="fc-stat-box slate">
      <div class="fc-stat-num" id="st-streak">0</div>
      <div class="fc-stat-lbl">Current Streak</div>
    </div>
  </div>

  <div class="fc-stat-box" style="margin-bottom:16px;">
    <div style="font-size:.8rem;color:var(--slate-500);margin-bottom:8px;">Mastery Progress</div>
    <div class="fc-progress-bar" style="height:10px;margin-bottom:0;">
      <div class="fc-progress-fill" id="st-mastery-bar" style="width:0%;background:var(--green);"></div>
    </div>
    <div style="font-size:.75rem;color:var(--slate-400);margin-top:6px;" id="st-mastery-pct">0% mastered</div>
  </div>

  <button class="btn btn-ghost btn-sm" id="fc-reset-stats-btn">Reset All Stats</button>

</div>

<!-- ══════════════════════════════════════════════════════════
     MANAGE PANEL
════════════════════════════════════════════════════════════ -->
<div id="fc-panel-manage" class="fc-panel" role="tabpanel">

  <div class="fc-manage-section">
    <h3>Export Deck</h3>
    <p>Download all cards as a JSON file to back up or share your deck.</p>
    <button class="btn btn-primary btn-sm" id="fc-export-btn">Export JSON</button>
  </div>

  <div class="fc-manage-section">
    <h3>Import Deck</h3>
    <p>Load a previously exported JSON deck. Existing cards will be kept unless you clear first.</p>
    <input type="file" id="fc-import-file" accept=".json" style="display:none;">
    <button class="btn btn-ghost btn-sm" id="fc-import-btn">Choose JSON File</button>
  </div>

  <div class="fc-manage-section">
    <h3>Clear All Cards</h3>
    <p>Remove every card and reset stats. This cannot be undone.</p>
    <button class="btn btn-danger btn-sm" id="fc-clear-btn">Clear All</button>
  </div>

</div>

<!-- Toast -->
<div class="fc-toast" id="fc-toast"></div>

</div><!-- /#fc-app -->

<script>
(function () {
  'use strict';

  /* ── Storage keys ─────────────────────────────────────── */
  var STORE_KEY   = 'fc_deck_v1';
  var STATS_KEY   = 'fc_stats_v1';

  /* ── State ────────────────────────────────────────────── */
  var cards  = [];   // [{id, front, back, score, bucket}]
  var stats  = { streak: 0, sessions: 0, lastDate: '' };

  // study session state
  var studyQueue   = [];
  var studyIndex   = 0;
  var sessionKnow  = 0;
  var sessionStill = 0;
  var isFlipped    = false;

  /* ── Persistence ──────────────────────────────────────── */
  function save() {
    try { localStorage.setItem(STORE_KEY, JSON.stringify(cards)); } catch(e) {}
  }

  function saveStats() {
    try { localStorage.setItem(STATS_KEY, JSON.stringify(stats)); } catch(e) {}
  }

  function load() {
    try {
      var raw = localStorage.getItem(STORE_KEY);
      if (raw) cards = JSON.parse(raw);
    } catch(e) { cards = []; }
    try {
      var rs = localStorage.getItem(STATS_KEY);
      if (rs) stats = Object.assign(stats, JSON.parse(rs));
    } catch(e) {}
  }

  /* ── Utilities ────────────────────────────────────────── */
  function uid() {
    return Math.random().toString(36).slice(2) + Date.now().toString(36);
  }

  function toast(msg) {
    var el = document.getElementById('fc-toast');
    el.textContent = msg;
    el.classList.add('show');
    setTimeout(function () { el.classList.remove('show'); }, 2200);
  }

  function esc(str) {
    return String(str)
      .replace(/&/g,'&amp;')
      .replace(/</g,'&lt;')
      .replace(/>/g,'&gt;')
      .replace(/"/g,'&quot;');
  }

  /* ── Tab switching ────────────────────────────────────── */
  document.querySelectorAll('#fc-app .fc-tab').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var tab = btn.dataset.tab;
      document.querySelectorAll('#fc-app .fc-tab').forEach(function(b){ b.classList.remove('active'); });
      document.querySelectorAll('#fc-app .fc-panel').forEach(function(p){ p.classList.remove('active'); });
      btn.classList.add('active');
      document.getElementById('fc-panel-' + tab).classList.add('active');
      if (tab === 'study')  initStudy();
      if (tab === 'stats')  renderStats();
    });
  });

  /* ══════════════════════════════════════════════════════
     CREATE
  ════════════════════════════════════════════════════════ */
  function renderCardList() {
    var ul = document.getElementById('fc-card-list');
    if (!cards.length) {
      ul.innerHTML = '<li class="fc-empty">No cards yet. Add one above!</li>';
      return;
    }
    ul.innerHTML = cards.map(function(c, i) {
      return '<li class="fc-card-item" data-id="' + c.id + '">' +
        '<div class="fc-card-texts">' +
          '<div class="fc-front">' + esc(c.front) + '</div>' +
          '<div class="fc-back">'  + esc(c.back)  + '</div>' +
          '<div class="fc-inline-edit" id="edit-' + c.id + '">' +
            '<textarea class="edit-front" rows="2">' + esc(c.front) + '</textarea>' +
            '<textarea class="edit-back"  rows="2">' + esc(c.back)  + '</textarea>' +
            '<div class="fc-btn-row">' +
              '<button class="btn btn-primary btn-sm save-edit-btn" data-id="' + c.id + '">Save</button>' +
              '<button class="btn btn-ghost   btn-sm cancel-edit-btn" data-id="' + c.id + '">Cancel</button>' +
            '</div>' +
          '</div>' +
        '</div>' +
        '<div class="fc-card-actions">' +
          '<button class="btn btn-ghost btn-sm edit-btn" data-id="' + c.id + '">Edit</button>' +
          '<button class="btn btn-danger btn-sm del-btn"  data-id="' + c.id + '">Del</button>' +
        '</div>' +
      '</li>';
    }).join('');
  }

  document.getElementById('fc-add-btn').addEventListener('click', function() {
    var front = document.getElementById('fc-front').value.trim();
    var back  = document.getElementById('fc-back').value.trim();
    if (!front || !back) { toast('Please fill in both front and back.'); return; }
    cards.push({ id: uid(), front: front, back: back, score: 0, bucket: 0 });
    save();
    document.getElementById('fc-front').value = '';
    document.getElementById('fc-back').value  = '';
    renderCardList();
    toast('Card added!');
  });

  // Event delegation for card list buttons
  document.getElementById('fc-card-list').addEventListener('click', function(e) {
    var id = e.target.dataset.id;
    if (!id) return;

    if (e.target.classList.contains('del-btn')) {
      cards = cards.filter(function(c){ return c.id !== id; });
      save();
      renderCardList();
      toast('Card deleted.');
      return;
    }

    if (e.target.classList.contains('edit-btn')) {
      var box = document.getElementById('edit-' + id);
      if (box) box.classList.add('open');
      return;
    }

    if (e.target.classList.contains('cancel-edit-btn')) {
      var box2 = document.getElementById('edit-' + id);
      if (box2) box2.classList.remove('open');
      return;
    }

    if (e.target.classList.contains('save-edit-btn')) {
      var box3 = document.getElementById('edit-' + id);
      if (!box3) return;
      var nf = box3.querySelector('.edit-front').value.trim();
      var nb = box3.querySelector('.edit-back').value.trim();
      if (!nf || !nb) { toast('Front and back cannot be empty.'); return; }
      var card = cards.find(function(c){ return c.id === id; });
      if (card) { card.front = nf; card.back = nb; }
      save();
      renderCardList();
      toast('Card updated.');
    }
  });

  // CSV import
  document.getElementById('fc-csv-import-btn').addEventListener('click', function() {
    var raw  = document.getElementById('fc-csv-input').value.trim();
    if (!raw) { toast('Paste CSV content first.'); return; }
    var lines = raw.split('\n');
    var added = 0;
    lines.forEach(function(line) {
      line = line.trim();
      if (!line) return;
      // split only on first comma so back can contain commas
      var comma = line.indexOf(',');
      if (comma < 0) return;
      var front = line.slice(0, comma).trim();
      var back  = line.slice(comma + 1).trim();
      if (!front || !back) return;
      cards.push({ id: uid(), front: front, back: back, score: 0, bucket: 0 });
      added++;
    });
    if (!added) { toast('No valid rows found.'); return; }
    save();
    document.getElementById('fc-csv-input').value = '';
    renderCardList();
    toast(added + ' card(s) imported from CSV!');
  });

  /* ══════════════════════════════════════════════════════
     STUDY — spaced repetition (Leitner-lite)
     bucket 0 = new/struggling → weight 3
     bucket 1 = seen once     → weight 2
     bucket 2+ = known         → weight 1
  ════════════════════════════════════════════════════════ */
  function buildQueue(source) {
    var q = [];
    source.forEach(function(c) {
      var weight = c.bucket === 0 ? 3 : c.bucket === 1 ? 2 : 1;
      for (var i = 0; i < weight; i++) q.push(c);
    });
    // Fisher-Yates shuffle
    for (var i = q.length - 1; i > 0; i--) {
      var j = Math.floor(Math.random() * (i + 1));
      var tmp = q[i]; q[i] = q[j]; q[j] = tmp;
    }
    return q;
  }

  function initStudy(reviewStill) {
    var noCardsEl = document.getElementById('fc-study-no-cards');
    var studyArea = document.getElementById('fc-study-area');
    var completeEl = document.getElementById('fc-study-complete');

    if (!cards.length) {
      noCardsEl.style.display  = '';
      studyArea.style.display  = 'none';
      completeEl.style.display = 'none';
      return;
    }

    noCardsEl.style.display  = 'none';
    studyArea.style.display  = '';
    completeEl.style.display = 'none';

    var source = reviewStill
      ? cards.filter(function(c){ return c.bucket < 2; })
      : cards.slice();

    if (!source.length) source = cards.slice();

    studyQueue   = buildQueue(source);
    studyIndex   = 0;
    sessionKnow  = 0;
    sessionStill = 0;

    showCard();
  }

  function showCard() {
    var card = studyQueue[studyIndex];
    var completeEl = document.getElementById('fc-study-complete');
    var studyArea  = document.getElementById('fc-study-area');

    if (!card) {
      // session done
      endSession();
      return;
    }

    completeEl.style.display = 'none';
    studyArea.style.display  = '';

    document.getElementById('fc-flip-front-text').textContent = card.front;
    document.getElementById('fc-flip-back-text').textContent  = card.back;

    // reset flip
    var fc = document.getElementById('fc-flip-card');
    fc.classList.remove('flipped');
    isFlipped = false;
    document.getElementById('fc-answer-btns').style.display = 'none';

    // counter & progress
    var total = studyQueue.length;
    var done  = studyIndex;
    document.getElementById('fc-study-counter').textContent =
      'Card ' + (studyIndex + 1) + ' of ' + total;
    document.getElementById('fc-progress-fill').style.width =
      Math.round((done / total) * 100) + '%';
  }

  function endSession() {
    var studyArea  = document.getElementById('fc-study-area');
    var completeEl = document.getElementById('fc-study-complete');

    studyArea.style.display  = 'none';
    completeEl.style.display = '';

    document.getElementById('fc-sum-know').textContent  = sessionKnow;
    document.getElementById('fc-sum-still').textContent = sessionStill;
    document.getElementById('fc-sum-total').textContent = sessionKnow + sessionStill;

    // update streak
    var today = new Date().toISOString().slice(0,10);
    if (stats.lastDate === today) {
      // same day — no change
    } else if (stats.lastDate === getPrevDate(today)) {
      stats.streak++;
    } else {
      stats.streak = 1;
    }
    stats.lastDate = today;
    stats.sessions++;
    saveStats();
  }

  function getPrevDate(dateStr) {
    var d = new Date(dateStr);
    d.setDate(d.getDate() - 1);
    return d.toISOString().slice(0,10);
  }

  // Flip on click
  document.getElementById('fc-flip-scene').addEventListener('click', function() {
    if (isFlipped) return;
    isFlipped = true;
    document.getElementById('fc-flip-card').classList.add('flipped');
    document.getElementById('fc-answer-btns').style.display = 'flex';
  });

  document.getElementById('fc-know-btn').addEventListener('click', function() {
    var card = studyQueue[studyIndex];
    if (card) {
      var orig = cards.find(function(c){ return c.id === card.id; });
      if (orig) { orig.bucket = Math.min(orig.bucket + 1, 3); orig.score++; }
    }
    sessionKnow++;
    save();
    studyIndex++;
    showCard();
  });

  document.getElementById('fc-still-btn').addEventListener('click', function() {
    var card = studyQueue[studyIndex];
    if (card) {
      var orig = cards.find(function(c){ return c.id === card.id; });
      if (orig) { orig.bucket = 0; }
    }
    sessionStill++;
    save();
    studyIndex++;
    showCard();
  });

  document.getElementById('fc-shuffle-btn').addEventListener('click', function() {
    initStudy();
    toast('Deck shuffled!');
  });

  document.getElementById('fc-restart-btn').addEventListener('click', function() {
    initStudy();
  });

  document.getElementById('fc-review-still-btn').addEventListener('click', function() {
    initStudy(true);
  });

  /* ══════════════════════════════════════════════════════
     STATS
  ════════════════════════════════════════════════════════ */
  function renderStats() {
    var total    = cards.length;
    var mastered = cards.filter(function(c){ return c.bucket >= 2; }).length;
    var learning = cards.filter(function(c){ return c.bucket < 2; }).length;
    var pct      = total > 0 ? Math.round((mastered / total) * 100) : 0;

    document.getElementById('st-total').textContent    = total;
    document.getElementById('st-mastered').textContent = mastered;
    document.getElementById('st-learning').textContent = learning;
    document.getElementById('st-streak').textContent   = stats.streak;

    document.getElementById('st-mastery-bar').style.width = pct + '%';
    document.getElementById('st-mastery-pct').textContent = pct + '% mastered';
  }

  document.getElementById('fc-reset-stats-btn').addEventListener('click', function() {
    if (!confirm('Reset all stats and card progress?')) return;
    cards.forEach(function(c){ c.bucket = 0; c.score = 0; });
    stats = { streak: 0, sessions: 0, lastDate: '' };
    save();
    saveStats();
    renderStats();
    toast('Stats reset.');
  });

  /* ══════════════════════════════════════════════════════
     MANAGE — export / import / clear
  ════════════════════════════════════════════════════════ */
  document.getElementById('fc-export-btn').addEventListener('click', function() {
    if (!cards.length) { toast('No cards to export.'); return; }
    var json = JSON.stringify({ version: 1, cards: cards }, null, 2);
    var blob = new Blob([json], { type: 'application/json' });
    var url  = URL.createObjectURL(blob);
    var a    = document.createElement('a');
    a.href     = url;
    a.download = 'flashcards.json';
    a.click();
    URL.revokeObjectURL(url);
    toast('Deck exported!');
  });

  document.getElementById('fc-import-btn').addEventListener('click', function() {
    document.getElementById('fc-import-file').click();
  });

  document.getElementById('fc-import-file').addEventListener('change', function(e) {
    var file = e.target.files[0];
    if (!file) return;
    var reader = new FileReader();
    reader.onload = function(ev) {
      try {
        var data = JSON.parse(ev.target.result);
        var imported = Array.isArray(data.cards) ? data.cards : (Array.isArray(data) ? data : null);
        if (!imported) { toast('Invalid JSON format.'); return; }
        var added = 0;
        imported.forEach(function(c) {
          if (c.front && c.back) {
            cards.push({
              id:     uid(),
              front:  String(c.front),
              back:   String(c.back),
              score:  Number(c.score)  || 0,
              bucket: Number(c.bucket) || 0
            });
            added++;
          }
        });
        save();
        renderCardList();
        toast(added + ' card(s) imported!');
      } catch(err) {
        toast('Failed to parse JSON file.');
      }
    };
    reader.readAsText(file);
    e.target.value = '';
  });

  document.getElementById('fc-clear-btn').addEventListener('click', function() {
    if (!confirm('Delete ALL cards and stats? This cannot be undone.')) return;
    cards = [];
    stats = { streak: 0, sessions: 0, lastDate: '' };
    save();
    saveStats();
    renderCardList();
    renderStats();
    toast('All cards cleared.');
  });

  /* ── Init ─────────────────────────────────────────────── */
  load();
  renderCardList();

})();
</script>

---

> Test reading speed → [Reading Speed Calculator](/tools/reading-speed-calculator/)
> Focus with Pomodoro → [Pomodoro Timer](/tools/pomodoro-timer/)
> Test typing speed → [Typing Speed Test](/tools/typing-speed-test/)

## Related Articles

- [How to Use ChatGPT for Studying: The Complete Student Guide 2026](/posts/how-to-use-chatgpt-for-studying-guide-2026/)
- [Best AI Tools for Teachers & Educators 2026: Complete Guide](/posts/ai-tools-teachers-educators-2026/)
